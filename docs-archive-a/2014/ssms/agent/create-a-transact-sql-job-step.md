---
title: 建立 Transact-SQL 作業步驟 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL job step
- job steps [Transact-SQL]
- SQL Server Agent jobs, Transact-SQL step
ms.assetid: 69c571a7-debe-4063-9d38-e4b6a1e8e84c
author: stevestein
ms.author: sstein
ms.openlocfilehash: b83ee944d2ca5c10ff1b77f3e6e6da6054b5c99a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705890"
---
# <a name="create-a-transact-sql-job-step"></a><span data-ttu-id="5fa94-102">Create a Transact-SQL Job Step</span><span class="sxs-lookup"><span data-stu-id="5fa94-102">Create a Transact-SQL Job Step</span></span>
  <span data-ttu-id="5fa94-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、或 SQL Server 管理物件，在中建立執行腳本的 Agent 作業步驟 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5fa94-103">This topic describes how to create a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step that executes [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="5fa94-104">這些作業步驟指令碼可呼叫預存程序及擴充預存程序。</span><span class="sxs-lookup"><span data-stu-id="5fa94-104">These job step scripts may call stored procedures and extended stored procedures.</span></span> <span data-ttu-id="5fa94-105">單一 [!INCLUDE[tsql](../../includes/tsql-md.md)] 作業步驟可包含多個批次和內嵌 GO 命令。</span><span class="sxs-lookup"><span data-stu-id="5fa94-105">A single [!INCLUDE[tsql](../../includes/tsql-md.md)] job step can contain multiple batches and embedded GO commands.</span></span> <span data-ttu-id="5fa94-106">如需建立作業的詳細資訊，請參閱＜ [建立作業](create-jobs.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5fa94-106">For more information on creating a job, see [Creating Jobs](create-jobs.md).</span></span>  
  
 <span data-ttu-id="5fa94-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="5fa94-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5fa94-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="5fa94-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5fa94-109">安全性</span><span class="sxs-lookup"><span data-stu-id="5fa94-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5fa94-110">**若要使用下列項目建立 Transact-SQL 作業步驟：**</span><span class="sxs-lookup"><span data-stu-id="5fa94-110">**To create a Transact-SQL job step, using:**</span></span>  
  
     [<span data-ttu-id="5fa94-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5fa94-111">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="5fa94-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5fa94-112">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="5fa94-113">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="5fa94-113">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5fa94-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="5fa94-114">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5fa94-115">Security</span><span class="sxs-lookup"><span data-stu-id="5fa94-115">Security</span></span>  
 <span data-ttu-id="5fa94-116">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5fa94-116">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="5fa94-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5fa94-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-transact-sql-job-step"></a><span data-ttu-id="5fa94-118">若要建立 Transact-SQL 作業步驟</span><span class="sxs-lookup"><span data-stu-id="5fa94-118">To create a Transact-SQL job step</span></span>  
  
1.  <span data-ttu-id="5fa94-119">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="5fa94-119">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="5fa94-120">展開 **SQL Server Agent**，建立新作業或以滑鼠右鍵按一下現有作業，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5fa94-120">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="5fa94-121">在 **[作業屬性]** 方塊中，按一下 **[步驟]** 頁面，然後按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="5fa94-121">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="5fa94-122">在 **[新增作業步驟]** 對話方塊中，輸入一個作業 **步驟名稱**。</span><span class="sxs-lookup"><span data-stu-id="5fa94-122">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="5fa94-123">在 [類型]\*\*\*\* 清單中，按一下 [Transact-SQL 指令碼 (TSQL)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5fa94-123">In the **Type** list, click **Transact-SQL Script (TSQL)**.</span></span>  
  
6.  <span data-ttu-id="5fa94-124">在 **[命令]** 方塊中，輸入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令批次，或按一下 **[開啟舊檔]** 來選取要作為命令使用的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 檔。</span><span class="sxs-lookup"><span data-stu-id="5fa94-124">In the **Command** box, type the [!INCLUDE[tsql](../../includes/tsql-md.md)] command batches, or click **Open** to select a [!INCLUDE[tsql](../../includes/tsql-md.md)] file to use as the command.</span></span>  
  
7.  <span data-ttu-id="5fa94-125">按一下 **[剖析]** 來檢查語法。</span><span class="sxs-lookup"><span data-stu-id="5fa94-125">Click **Parse** to check your syntax.</span></span>  
  
8.  <span data-ttu-id="5fa94-126">當語法正確時，會顯示「剖析成功」的訊息。</span><span class="sxs-lookup"><span data-stu-id="5fa94-126">The message "Parse succeeded" is displayed when your syntax is correct.</span></span> <span data-ttu-id="5fa94-127">如果出現錯誤訊息，請修正語法後再繼續。</span><span class="sxs-lookup"><span data-stu-id="5fa94-127">If an error is found, correct the syntax before continuing.</span></span>  
  
9. <span data-ttu-id="5fa94-128">按一下 **[進階]** 頁面來設定作業步驟選項，例如：作業步驟成功或失敗時要採取的動作、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 應嘗試執行作業步驟的次數，以及可供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 寫入作業步驟輸出的檔案或資料表。</span><span class="sxs-lookup"><span data-stu-id="5fa94-128">Click the **Advanced** page to set job step options, such as: what action to take if the job step succeeds or fails, how many times [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should try to execute the job step, and the file or table where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can write the job step output.</span></span> <span data-ttu-id="5fa94-129">只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，可以將作業步驟輸出寫入作業系統檔案。</span><span class="sxs-lookup"><span data-stu-id="5fa94-129">Only members of the **sysadmin** fixed server role can write job step output to an operating system file.</span></span> <span data-ttu-id="5fa94-130">所有 SQL Server Agent 使用者都可以將輸出記錄到資料表中。</span><span class="sxs-lookup"><span data-stu-id="5fa94-130">All SQL Server Agent users can log output to a table.</span></span>  
  
10. <span data-ttu-id="5fa94-131">如果您是 **系統管理員 (sysadmin)** 固定伺服器角色的成員，而您想以不同的 SQL 登入執行這個作業步驟，請從 **[指定執行時的身分]** 清單中選取 SQL 登入。</span><span class="sxs-lookup"><span data-stu-id="5fa94-131">If you are a member of the **sysadmin** fixed server role and you want to run this job step as a different SQL login, select the SQL login from the **Run as user** list.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="5fa94-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5fa94-132">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-transact-sql-job-step"></a><span data-ttu-id="5fa94-133">若要建立 Transact-SQL 作業步驟</span><span class="sxs-lookup"><span data-stu-id="5fa94-133">To create a Transact-SQL job step</span></span>  
  
1.  <span data-ttu-id="5fa94-134">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5fa94-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5fa94-135">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="5fa94-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5fa94-136">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="5fa94-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- creates a job step that uses Transact-SQL  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="5fa94-137">如需詳細資訊，請參閱[sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5fa94-137">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="5fa94-138">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="5fa94-138">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="5fa94-139">**若要建立 Transact-SQL 作業步驟**</span><span class="sxs-lookup"><span data-stu-id="5fa94-139">**To create a Transact-SQL job step**</span></span>  
  
 <span data-ttu-id="5fa94-140">透過所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，使用 `JobStep` 類別。</span><span class="sxs-lookup"><span data-stu-id="5fa94-140">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
