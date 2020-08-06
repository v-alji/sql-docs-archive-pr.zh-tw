---
title: 建立 ActiveX Script 指令碼作業步驟 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- ActiveX scripting jobs [SQL Server]
- job steps [Analysis Services]
ms.assetid: e6c46c6b-2d61-4571-bc8e-a831cd6e6302
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6604ba75af7acdd5bd2521433e8310c74150ce8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686757"
---
# <a name="create-an-activex-script-job-step"></a><span data-ttu-id="acac3-102">Create an ActiveX Script Job Step</span><span class="sxs-lookup"><span data-stu-id="acac3-102">Create an ActiveX Script Job Step</span></span>
  <span data-ttu-id="acac3-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、或 SQL Server 管理物件，在中建立和定義執行 ActiveX script 的 Agent 作業步驟 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="acac3-103">This topic describes how to create and define a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that executes an ActiveX script by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
-   <span data-ttu-id="acac3-104">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="acac3-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="acac3-105">限制事項</span><span class="sxs-lookup"><span data-stu-id="acac3-105">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="acac3-106">安全性</span><span class="sxs-lookup"><span data-stu-id="acac3-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="acac3-107">**若要使用下列項目建立 Transact-SQL 作業步驟：**</span><span class="sxs-lookup"><span data-stu-id="acac3-107">**To create a Transact-SQL job step, using:**</span></span>  
  
     [<span data-ttu-id="acac3-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="acac3-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="acac3-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="acac3-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="acac3-110">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="acac3-110">SQL Server Management Objects</span></span>](#SMO)  
  
## <a name="before-you-begin"></a><span data-ttu-id="acac3-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="acac3-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="acac3-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="acac3-112">Limitations and Restrictions</span></span>  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="acac3-113">Security</span><span class="sxs-lookup"><span data-stu-id="acac3-113">Security</span></span>  
 <span data-ttu-id="acac3-114">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="acac3-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="acac3-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="acac3-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-activex-script-job-step"></a><span data-ttu-id="acac3-116">若要建立 ActiveX 指令碼作業步驟</span><span class="sxs-lookup"><span data-stu-id="acac3-116">To create an ActiveX Script job step</span></span>  
  
1.  <span data-ttu-id="acac3-117">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="acac3-117">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="acac3-118">展開 **SQL Server Agent**，建立新作業或以滑鼠右鍵按一下現有作業，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="acac3-118">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="acac3-119">如需建立作業的詳細資訊，請參閱＜ [建立作業](create-jobs.md)＞。</span><span class="sxs-lookup"><span data-stu-id="acac3-119">For more information on creating a job, see [Creating Jobs](create-jobs.md).</span></span>  
  
3.  <span data-ttu-id="acac3-120">在 **[作業屬性]** 方塊中，按一下 **[步驟]** 頁面，然後按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="acac3-120">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="acac3-121">在 **[新增作業步驟]** 對話方塊中，輸入一個作業 **步驟名稱**。</span><span class="sxs-lookup"><span data-stu-id="acac3-121">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="acac3-122">在 **[類型]** 清單中，按一下 **[ActiveX Script]**。</span><span class="sxs-lookup"><span data-stu-id="acac3-122">In the **Type** list, click **ActiveX Script**.</span></span>  
  
6.  <span data-ttu-id="acac3-123">在 **[執行身分]** 清單中，選取具有作業將會使用之認證的 Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="acac3-123">In the **Run as** list, select the proxy account with the credentials that the job will use.</span></span>  
  
7.  <span data-ttu-id="acac3-124">選取當初撰寫指令碼所用的 **[語言]** 。</span><span class="sxs-lookup"><span data-stu-id="acac3-124">Select the **Language** in which the script was written.</span></span> <span data-ttu-id="acac3-125">或者，按一下 **[其他]** ，然後輸入將用來撰寫指令碼的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX 指令碼語言的名稱。</span><span class="sxs-lookup"><span data-stu-id="acac3-125">Alternatively, click **Other** and then enter the name of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX scripting language in which the script will be written.</span></span>  
  
8.  <span data-ttu-id="acac3-126">在 **[命令]** 方塊中，輸入將為作業步驟執行的指令碼語法。</span><span class="sxs-lookup"><span data-stu-id="acac3-126">In the **Command** box, enter the script syntax that will be executed for the job step.</span></span> <span data-ttu-id="acac3-127">或者，請按一下 **[開啟舊檔]** ，然後選取包含指令碼語法的檔案。</span><span class="sxs-lookup"><span data-stu-id="acac3-127">Alternately, click **Open** and select a file containing the script syntax.</span></span>  
  
9. <span data-ttu-id="acac3-128">按一下 **[進階]** 頁面，設定下列作業步驟選項：作業步驟成功或失敗時要採取什麼動作、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 應該嘗試執行作業步驟多少次，以及應該多久重試一次。</span><span class="sxs-lookup"><span data-stu-id="acac3-128">Click the **Advanced** page to set the following job step options: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should try to execute the job step, and how often retry attempts should be made.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="acac3-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="acac3-129">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-activex-script-job-step"></a><span data-ttu-id="acac3-130">若要建立 ActiveX 指令碼作業步驟</span><span class="sxs-lookup"><span data-stu-id="acac3-130">To create an ActiveX Script job step</span></span>  
  
1.  <span data-ttu-id="acac3-131">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="acac3-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="acac3-132">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="acac3-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="acac3-133">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="acac3-133">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- create an ActiveX Script job step written in VBScript that creates a restore point  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Create a restore point',  
        @subsystem = N'ACTIVESCRIPTING',  
        @command = N'Const RESTORE_POINT = 20  
  
    strComputer = "."  
    Set objWMIService = GetObject("winmgmts:" _  
        & "{impersonationLevel=impersonate}!\\" & strComputer & "\root\default")  
  
    Set objItem = objWMIService.Get("SystemRestore")  
    errResults = objItem.Restore(RESTORE_POINT)',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="acac3-134">如需詳細資訊，請參閱[sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="acac3-134">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="acac3-135">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="acac3-135">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="acac3-136">**若要建立 ActiveX 指令碼作業步驟**</span><span class="sxs-lookup"><span data-stu-id="acac3-136">**To create an ActiveX Script job step**</span></span>  
  
 <span data-ttu-id="acac3-137">透過所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，使用 `JobStep` 類別。</span><span class="sxs-lookup"><span data-stu-id="acac3-137">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
