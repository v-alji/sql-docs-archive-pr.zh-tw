---
title: 建立 CmdExec 作業步驟 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CmdExec jobs
ms.assetid: b48da5b4-6fe7-4eb7-bade-dc7d697c6d5c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 48c557b8ea4228d27b73d361c50aac62232d1e00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595359"
---
# <a name="create-a-cmdexec-job-step"></a><span data-ttu-id="d0496-102">建立 CmdExec 作業步驟</span><span class="sxs-lookup"><span data-stu-id="d0496-102">Create a CmdExec Job Step</span></span>
  <span data-ttu-id="d0496-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或 SQL Server 管理物件，在中建立和定義 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用可執行程式或作業系統命令的 Agent 作業步驟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d0496-103">This topic describes how to create and define a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that uses an executable program or operating system command by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="d0496-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="d0496-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d0496-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="d0496-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d0496-106">安全性</span><span class="sxs-lookup"><span data-stu-id="d0496-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d0496-107">**若要使用下列項目建立 CmdExec 作業步驟：**</span><span class="sxs-lookup"><span data-stu-id="d0496-107">**To create a CmdExec job step, using:**</span></span>  
  
     [<span data-ttu-id="d0496-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d0496-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="d0496-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d0496-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="d0496-110">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="d0496-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d0496-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="d0496-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d0496-112">Security</span><span class="sxs-lookup"><span data-stu-id="d0496-112">Security</span></span>  
 <span data-ttu-id="d0496-113">根據預設，只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員可以建立 CmdExec 作業步驟。</span><span class="sxs-lookup"><span data-stu-id="d0496-113">By default, only members of the **sysadmin** fixed server role can create CmdExec job steps.</span></span> <span data-ttu-id="d0496-114">這些作業步驟會以 SQL Server Agent 服務帳戶的身分執行，除非 **系統管理員 (sysadmin)** 使用者建立 Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="d0496-114">These job steps run under the context of the SQL Server Agent service account unless the **sysadmin** user creates a proxy account.</span></span> <span data-ttu-id="d0496-115">如果使用者不是 **系統管理員 (sysadmin)** 角色的成員，則必須能夠存取 CmdExec Proxy 帳戶，才能建立 CmdExec 作業步驟。</span><span class="sxs-lookup"><span data-stu-id="d0496-115">Users who are not members of the **sysadmin** role can create CmdExec job steps if they have access to a CmdExec proxy account.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d0496-116">權限</span><span class="sxs-lookup"><span data-stu-id="d0496-116">Permissions</span></span>  
 <span data-ttu-id="d0496-117">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d0496-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="d0496-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d0496-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-cmdexec-job-step"></a><span data-ttu-id="d0496-119">建立 CmdExec 作業步驟</span><span class="sxs-lookup"><span data-stu-id="d0496-119">To create a CmdExec job step</span></span>  
  
1.  <span data-ttu-id="d0496-120">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="d0496-120">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="d0496-121">展開 **SQL Server Agent**，建立新作業或以滑鼠右鍵按一下現有作業，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0496-121">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="d0496-122">在 **[作業屬性]** 方塊中，按一下 **[步驟]** 頁面，然後按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="d0496-122">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="d0496-123">在 **[新增作業步驟]** 對話方塊中，輸入一個作業 **步驟名稱**。</span><span class="sxs-lookup"><span data-stu-id="d0496-123">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="d0496-124">在 [類型]\*\*\*\* 清單中，選擇 [作業系統 (CmdExec)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d0496-124">In the **Type** list, choose **Operating system (CmdExec)**.</span></span>  
  
6.  <span data-ttu-id="d0496-125">在 **[執行身分]** 清單中，選取具有作業將會使用之認證的 Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="d0496-125">In **Run as** list, select the proxy account with the credentials that the job will use.</span></span> <span data-ttu-id="d0496-126">根據預設，CmdExec 作業步驟會以 SQL Server Agent 服務帳戶的身分執行。</span><span class="sxs-lookup"><span data-stu-id="d0496-126">By default, CmdExec job steps run under the context of the SQL Server Agent service account.</span></span>  
  
7.  <span data-ttu-id="d0496-127">在 **[成功命令的處理序結束碼]** 方塊中，輸入介於 0 到 999999 之間的值。</span><span class="sxs-lookup"><span data-stu-id="d0496-127">In the **Process exit code of a successful command** box, enter a value from 0 to 999999.</span></span>  
  
8.  <span data-ttu-id="d0496-128">\*\*\*\* 在 [命令]方塊中，輸入作業系統命令或可執行的程式。</span><span class="sxs-lookup"><span data-stu-id="d0496-128">In the **Command** box, enter the operating system command or executable program.</span></span> <span data-ttu-id="d0496-129">如需範例，請參閱＜使用 Transact-SQL＞。</span><span class="sxs-lookup"><span data-stu-id="d0496-129">See "Using Transact T-SQL for an example.</span></span>  
  
9. <span data-ttu-id="d0496-130">按一下 **[進階]** 頁面設定作業步驟選項，例如：作業步驟成功或失敗時要採取什麼動作、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 應該嘗試執行作業步驟多少次，以及可供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 寫入作業步驟輸出的檔案。</span><span class="sxs-lookup"><span data-stu-id="d0496-130">Click the **Advanced** page to set job step options, such as: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should try to execute the job step, and the file where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can write the job step output.</span></span> <span data-ttu-id="d0496-131">只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，可以將作業步驟輸出寫入作業系統檔案。</span><span class="sxs-lookup"><span data-stu-id="d0496-131">Only members of the **sysadmin** fixed server role can write job step output to an operating system file.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="d0496-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d0496-132">Using Transact-SQL</span></span>  
  
### <a name="to-create-a-cmdexec-job-step"></a><span data-ttu-id="d0496-133">建立 CmdExec 作業步驟</span><span class="sxs-lookup"><span data-stu-id="d0496-133">To create a CmdExec job step</span></span>  
  
1.  <span data-ttu-id="d0496-134">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d0496-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d0496-135">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="d0496-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d0496-136">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="d0496-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- creates a job step that uses CmdExec  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'CMDEXEC',  
        @command = C:\clickme_scripts\SQL11\PostBOLReorg GetHsX.exe',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="d0496-137">如需詳細資訊，請參閱[sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="d0496-137">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="d0496-138">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="d0496-138">Using SQL Server Management Objects</span></span>  

### <a name="to-create-a-cmdexec-job-step"></a><span data-ttu-id="d0496-139">建立 CmdExec 作業步驟</span><span class="sxs-lookup"><span data-stu-id="d0496-139">To create a CmdExec job step</span></span>
  
 <span data-ttu-id="d0496-140">透過所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，使用 `JobStep` 類別。</span><span class="sxs-lookup"><span data-stu-id="d0496-140">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
