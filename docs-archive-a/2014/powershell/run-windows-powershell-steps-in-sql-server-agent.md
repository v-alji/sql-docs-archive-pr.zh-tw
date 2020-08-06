---
title: 在 SQL Server Agent 中執行 Windows PowerShell 步驟 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: f25f7549-c9b3-4618-85f2-c9a08adbe0e3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8c100e2eaf1f9b706087bd991fbc268540c29a46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595146"
---
# <a name="run-windows-powershell-steps-in-sql-server-agent"></a><span data-ttu-id="85a5a-102">在 SQL Server Agent 中執行 Windows PowerShell 步驟</span><span class="sxs-lookup"><span data-stu-id="85a5a-102">Run Windows PowerShell Steps in SQL Server Agent</span></span>
  <span data-ttu-id="85a5a-103">使用 SQL Server Agent 在排定的時間執行 SQL Server PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="85a5a-103">Use SQL Server Agent to run SQL Server PowerShell scripts at schedule times.</span></span>  
  
1.  <span data-ttu-id="85a5a-104">**開始之前：**  [限制事項](#LimitationsRestrictions)</span><span class="sxs-lookup"><span data-stu-id="85a5a-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions)</span></span>  
  
2.  <span data-ttu-id="85a5a-105">**若要從 SQL Server Agent 執行 PowerShell，請使用：** [PowerShell 作業步驟](#PShellJob)、[命令提示字元作業步驟](#CmdExecJob)</span><span class="sxs-lookup"><span data-stu-id="85a5a-105">**To run PowerShell from SQL Server Agent, using:**  [PowerShell Job Step](#PShellJob), [Command Prompt Job Step](#CmdExecJob)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="85a5a-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="85a5a-106">Before You Begin</span></span>  
 <span data-ttu-id="85a5a-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 作業步驟有幾種類型。</span><span class="sxs-lookup"><span data-stu-id="85a5a-107">There are several types of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent job steps.</span></span> <span data-ttu-id="85a5a-108">每一種類型都與實作特定環境的子系統相關，例如複寫代理程式或命令提示字元環境。</span><span class="sxs-lookup"><span data-stu-id="85a5a-108">Each type is associated with a subsystem that implements a specific environment, such as a replication agent or command prompt environment.</span></span> <span data-ttu-id="85a5a-109">您可以編寫 Windows PowerShell 指令碼，然後使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 在排程時間執行的作業內包含這些指令碼，或是用來回應 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 事件。</span><span class="sxs-lookup"><span data-stu-id="85a5a-109">You can code Windows PowerShell scripts, and then use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent to include the scripts in jobs that run at scheduled times or in response to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] events.</span></span> <span data-ttu-id="85a5a-110">Windows PowerShell 指令碼可透過使用命令提示字元作業步驟或 PowerShell 作業步驟加以執行。</span><span class="sxs-lookup"><span data-stu-id="85a5a-110">Windows PowerShell scripts can be run using either a command prompt job step or a PowerShell job step.</span></span>  
  
1.  <span data-ttu-id="85a5a-111">使用 PowerShell 作業步驟讓 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 子系統執行 `sqlps` 公用程式，此公用程式會啟動 PowerShell 2.0 並匯入 `sqlps` 模組。</span><span class="sxs-lookup"><span data-stu-id="85a5a-111">Use a PowerShell job step to have the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent subsystem run the `sqlps` utility, which launches PowerShell 2.0 and imports the `sqlps` module.</span></span>  
  
2.  <span data-ttu-id="85a5a-112">使用命令提示字元作業步驟執行 PowerShell.exe，並指定匯入 `sqlps` 模組的指令碼。</span><span class="sxs-lookup"><span data-stu-id="85a5a-112">Use a command prompt job step to run PowerShell.exe, and specify a script that imports the `sqlps` module.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="85a5a-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="85a5a-113">Limitations and Restrictions</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="85a5a-114">搭配 `sqlps` 模組執行 PowerShell 的每項 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 作業步驟，都會啟動大約耗用 20 MB 記憶體的處理序。</span><span class="sxs-lookup"><span data-stu-id="85a5a-114">Each [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent job step that runs PowerShell with the `sqlps` module launches a process which consumes approximately 20 MB of memory.</span></span> <span data-ttu-id="85a5a-115">執行大量的並行 Windows PowerShell 作業步驟可能會對效能造成負面影響。</span><span class="sxs-lookup"><span data-stu-id="85a5a-115">Running large numbers of concurrent Windows PowerShell job steps can adversely impact performance.</span></span>  
  
##  <a name="create-a-powershell-job-step"></a><a name="PShellJob"></a><span data-ttu-id="85a5a-116">建立 PowerShell 作業步驟</span><span class="sxs-lookup"><span data-stu-id="85a5a-116">Create a PowerShell Job Step</span></span>  
 <span data-ttu-id="85a5a-117">**建立 PowerShell 作業步驟**</span><span class="sxs-lookup"><span data-stu-id="85a5a-117">**To create a PowerShell job step**</span></span>  
  
1.  <span data-ttu-id="85a5a-118">展開 **SQL Server Agent**，建立新作業或以滑鼠右鍵按一下現有作業，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85a5a-118">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="85a5a-119">如需建立作業的詳細資訊，請參閱＜ [建立作業](../ssms/agent/create-jobs.md)＞。</span><span class="sxs-lookup"><span data-stu-id="85a5a-119">For more information about creating a job, see [Creating Jobs](../ssms/agent/create-jobs.md).</span></span>  
  
2.  <span data-ttu-id="85a5a-120">在 **[作業屬性]** 方塊中，按一下 **[步驟]** 頁面，然後按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="85a5a-120">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
3.  <span data-ttu-id="85a5a-121">在 **[新增作業步驟]** 對話方塊中，輸入一個作業 **步驟名稱**。</span><span class="sxs-lookup"><span data-stu-id="85a5a-121">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
4.  <span data-ttu-id="85a5a-122">在 **[類型]** 清單中，按一下 **[PowerShell]**。</span><span class="sxs-lookup"><span data-stu-id="85a5a-122">In the **Type** list, click **PowerShell**.</span></span>  
  
5.  <span data-ttu-id="85a5a-123">在 **[執行身分]** 清單中，選取具有作業將會使用之認證的 Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="85a5a-123">In the **Run as** list, select the proxy account with the credentials that the job will use.</span></span>  
  
6.  <span data-ttu-id="85a5a-124">在 **[命令]** 方塊中，輸入將為作業步驟執行的 PowerShell 指令碼語法。</span><span class="sxs-lookup"><span data-stu-id="85a5a-124">In the **Command** box, enter the PowerShell script syntax that will be executed for the job step.</span></span> <span data-ttu-id="85a5a-125">或者，請按一下 **[開啟舊檔]** ，然後選取包含指令碼語法的檔案。</span><span class="sxs-lookup"><span data-stu-id="85a5a-125">Alternately, click **Open** and select a file containing the script syntax.</span></span>  
  
7.  <span data-ttu-id="85a5a-126">按一下 **[進階]** 頁面，設定下列作業步驟選項：作業步驟成功或失敗時要採取什麼動作、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 應該嘗試執行作業步驟多少次，以及應該多久重試一次。</span><span class="sxs-lookup"><span data-stu-id="85a5a-126">Click the **Advanced** page to set the following job step options: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent should try to execute the job step, and how often retry attempts should be made.</span></span>  
  
##  <a name="create-a-command-prompt-job-step"></a><a name="CmdExecJob"></a><span data-ttu-id="85a5a-127">建立命令提示字元作業步驟</span><span class="sxs-lookup"><span data-stu-id="85a5a-127">Create a Command Prompt Job Step</span></span>  
 <span data-ttu-id="85a5a-128">**建立 CmdExec 作業步驟**</span><span class="sxs-lookup"><span data-stu-id="85a5a-128">**To create a CmdExec job step**</span></span>  
  
1.  <span data-ttu-id="85a5a-129">展開 **SQL Server Agent**，建立新作業或以滑鼠右鍵按一下現有作業，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85a5a-129">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="85a5a-130">如需建立作業的詳細資訊，請參閱＜ [建立作業](../ssms/agent/create-jobs.md)＞。</span><span class="sxs-lookup"><span data-stu-id="85a5a-130">For more information about creating a job, see [Creating Jobs](../ssms/agent/create-jobs.md).</span></span>  
  
2.  <span data-ttu-id="85a5a-131">在 **[作業屬性]** 方塊中，按一下 **[步驟]** 頁面，然後按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="85a5a-131">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
3.  <span data-ttu-id="85a5a-132">在 **[新增作業步驟]** 對話方塊中，輸入一個作業 **步驟名稱**。</span><span class="sxs-lookup"><span data-stu-id="85a5a-132">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
4.  <span data-ttu-id="85a5a-133">在 [類型]\*\*\*\* 清單中，選擇 [作業系統 (CmdExec)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85a5a-133">In the **Type** list, choose **Operating system (CmdExec)**.</span></span>  
  
5.  <span data-ttu-id="85a5a-134">在 **[執行身分]** 清單中，選取具有作業將會使用之認證的 Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="85a5a-134">In **Run as** list, select the proxy account with the credentials that the job will use.</span></span> <span data-ttu-id="85a5a-135">根據預設，CmdExec 作業步驟會以 SQL Server Agent 服務帳戶的身分執行。</span><span class="sxs-lookup"><span data-stu-id="85a5a-135">By default, CmdExec job steps run under the context of the SQL Server Agent service account.</span></span>  
  
6.  <span data-ttu-id="85a5a-136">在 **[成功命令的處理序結束碼]** 方塊中，輸入介於 0 到 999999 之間的值。</span><span class="sxs-lookup"><span data-stu-id="85a5a-136">In the **Process exit code of a successful command** box, enter a value from 0 to 999999.</span></span>  
  
7.  <span data-ttu-id="85a5a-137">在 **[命令]** 方塊中，輸入內含指定執行 PowerShell 指令碼之參數的 powershell.exe。</span><span class="sxs-lookup"><span data-stu-id="85a5a-137">In the **Command** box, enter powershell.exe with parameters specifying the PowerShell script to be run.</span></span>  
  
8.  <span data-ttu-id="85a5a-138">按一下 **[進階]** 頁面設定作業步驟選項，例如：作業步驟成功或失敗時要採取什麼動作、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 應該嘗試執行作業步驟多少次，以及可供 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 寫入作業步驟輸出的檔案。</span><span class="sxs-lookup"><span data-stu-id="85a5a-138">Click the **Advanced** page to set job step options, such as: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent should try to execute the job step, and the file where [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent can write the job step output.</span></span> <span data-ttu-id="85a5a-139">只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，可以將作業步驟輸出寫入作業系統檔案。</span><span class="sxs-lookup"><span data-stu-id="85a5a-139">Only members of the **sysadmin** fixed server role can write job step output to an operating system file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85a5a-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85a5a-140">See Also</span></span>  
 [<span data-ttu-id="85a5a-141">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="85a5a-141">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
  
  
