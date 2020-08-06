---
title: 設定作業步驟成功或失敗的流程 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, action flow logic
- successful jobs [SQL Server]
- failed jobs [SQL Server]
- jobs [SQL Server Agent], action flow logic
ms.assetid: 23041ccf-8a07-41d3-85b9-c449a54b7e1e
author: stevestein
ms.author: sstein
ms.openlocfilehash: fddc5820676cb231b6f0cd5f7151e24d8eceaefa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710094"
---
# <a name="set-job-step-success-or-failure-flow"></a><span data-ttu-id="8956c-102">設定作業步驟成功或失敗的流程</span><span class="sxs-lookup"><span data-stu-id="8956c-102">Set Job Step Success or Failure Flow</span></span>
  <span data-ttu-id="8956c-103">建立 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業時，您可以指定在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 作業執行期間發生失敗時，應採取什麼動作。</span><span class="sxs-lookup"><span data-stu-id="8956c-103">When creating [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs, you can specify what action [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should take if a failure occurs during job execution.</span></span> <span data-ttu-id="8956c-104">決定每個作業步驟成功或失敗時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 應採取的動作。</span><span class="sxs-lookup"><span data-stu-id="8956c-104">Determine the action that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should take upon the success or failure of each job step.</span></span> <span data-ttu-id="8956c-105">接著，依照下列程序使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 來設定作業步驟動作流程。</span><span class="sxs-lookup"><span data-stu-id="8956c-105">Then use the following procedure to configure the job step action flow logic by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
-   <span data-ttu-id="8956c-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="8956c-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8956c-107">安全性</span><span class="sxs-lookup"><span data-stu-id="8956c-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8956c-108">**若要使用下列項目，設定作業步驟成功或失敗的流程：**</span><span class="sxs-lookup"><span data-stu-id="8956c-108">**To set job step success or failure flow, using:**</span></span>  
  
     [<span data-ttu-id="8956c-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8956c-109">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="8956c-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8956c-110">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="8956c-111">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="8956c-111">SQL Server Management Objects</span></span>](#SMO)  
  
## <a name="before-you-begin"></a><span data-ttu-id="8956c-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="8956c-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8956c-113">Security</span><span class="sxs-lookup"><span data-stu-id="8956c-113">Security</span></span>  
 <span data-ttu-id="8956c-114">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8956c-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="8956c-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8956c-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-job-step-success-or-failure-flow"></a><span data-ttu-id="8956c-116">若要設定作業步驟成功或失敗的流程</span><span class="sxs-lookup"><span data-stu-id="8956c-116">To set job step success or failure flow</span></span>  
  
1.  <span data-ttu-id="8956c-117">在 **[物件總管]** 中，展開 **[SQL Server Agent]**，然後展開 **[作業]**。</span><span class="sxs-lookup"><span data-stu-id="8956c-117">In **Object Explorer**, expand **SQL Server Agent**, and then expand **Jobs**.</span></span>  
  
2.  <span data-ttu-id="8956c-118">以滑鼠右鍵按一下要刪除的作業，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8956c-118">Right-click the job you want to edit, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="8956c-119">按一下 **[步驟]** 頁面，再按一下步驟，然後按一下 **[編輯]**。</span><span class="sxs-lookup"><span data-stu-id="8956c-119">Select the **Steps** page, click a step, and then click **Edit**.</span></span>  
  
4.  <span data-ttu-id="8956c-120">在 **[作業步驟屬性]** 對話方塊中，選取 **[進階]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="8956c-120">In the **Job Step Properties** dialog box, select the **Advanced** page.</span></span>  
  
5.  <span data-ttu-id="8956c-121">在 [成功時的動作]\*\*\*\* 清單中，按一下作業步驟順利完成時要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="8956c-121">In the **On success action**list, click the action to perform if the job step completes successfully.</span></span>  
  
6.  <span data-ttu-id="8956c-122">在 **[重試次數]** 方塊中，輸入介於 0 到 9999 間的值，此值是當發生作業步驟失敗前應該重試的次數。</span><span class="sxs-lookup"><span data-stu-id="8956c-122">In the **Retry attempts** box, enter the number of times from 0 through 9999 that the job step should be repeated before it is considered to have failed.</span></span> <span data-ttu-id="8956c-123">如果在 [重試次數]\*\*\*\* 方塊中指定大於 0 的值，請在 [重試間隔 (分鐘)]\*\*\*\* 方塊內輸入 1 至 9999 間的分鐘數，此值為作業步驟在重試前所應等待的時間。</span><span class="sxs-lookup"><span data-stu-id="8956c-123">If you entered a value greater than 0 in the **Retry attempts** box, enter in the **Retry interval (minutes)** box the number of minutes from 1 through 9999 that must pass before the job step is retried.</span></span>  
  
7.  <span data-ttu-id="8956c-124">在 **[當動作失敗時]** 清單中，按一下當作業步驟失敗時要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="8956c-124">In the **On failure action** list, click the action to perform if the job step fails.</span></span>  
  
8.  <span data-ttu-id="8956c-125">如果作業是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼，您可以從下列選項中選擇：</span><span class="sxs-lookup"><span data-stu-id="8956c-125">If the job is a [!INCLUDE[tsql](../../includes/tsql-md.md)] script, you can choose from the following options:</span></span>  
  
    -   <span data-ttu-id="8956c-126">在 **[輸出檔]** 方塊中，輸入要寫入指令碼輸出的輸出檔名稱。</span><span class="sxs-lookup"><span data-stu-id="8956c-126">In the **Output file** box, enter the name of an output file to which the script output will be written.</span></span> <span data-ttu-id="8956c-127">根據預設，每次執行作業步驟時都會覆寫此檔案。</span><span class="sxs-lookup"><span data-stu-id="8956c-127">By default the file is overwritten each time the job step executes.</span></span> <span data-ttu-id="8956c-128">如果您不想要覆寫輸出檔，請選取 **[將輸出附加至現有檔案]**。</span><span class="sxs-lookup"><span data-stu-id="8956c-128">If you do not want the output file overwritten, check **Append output to existing file**.</span></span>  
  
    -   <span data-ttu-id="8956c-129">若要將作業步驟記錄至資料庫資料表，請選取 **[記錄至資料表]** 。</span><span class="sxs-lookup"><span data-stu-id="8956c-129">Check **Log to table** if you want to log the job step to a database table.</span></span> <span data-ttu-id="8956c-130">根據預設，每次執行作業步驟時都會覆寫此資料表內容。</span><span class="sxs-lookup"><span data-stu-id="8956c-130">By default the table contents are overwritten each time the job step executes.</span></span> <span data-ttu-id="8956c-131">如果您不想要覆寫資料表內容，請選取 **[將輸出附加至資料表的現有項目]**。</span><span class="sxs-lookup"><span data-stu-id="8956c-131">If you do not want the table contents overwritten, check **Append output to existing entry in table**.</span></span> <span data-ttu-id="8956c-132">作業步驟執行之後，您可以按一下 **[檢視]** 以檢視這個資料表的內容。</span><span class="sxs-lookup"><span data-stu-id="8956c-132">After the job step executes, you can view the contents of this table by clicking **View**.</span></span>  
  
    -   <span data-ttu-id="8956c-133">如果您希望步驟的記錄中包含輸出，請選取 **[包含步驟輸出於記錄中]** 。</span><span class="sxs-lookup"><span data-stu-id="8956c-133">Check **Include step output in history** if you want the output included in the step's history.</span></span> <span data-ttu-id="8956c-134">只有無錯誤時，才會顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="8956c-134">Output will only be shown if there were no errors.</span></span> <span data-ttu-id="8956c-135">另外，輸出可能被截斷。</span><span class="sxs-lookup"><span data-stu-id="8956c-135">Also, output may be truncated.</span></span>  
  
9. <span data-ttu-id="8956c-136">若 **[指定執行時的身分]** 清單可用，請選取具有作業將會使用之認證的 Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="8956c-136">If the **Run as user** list is available, select the proxy account with the credentials that the job will use.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="8956c-137">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8956c-137">Using Transact-SQL</span></span>  
  
#### <a name="to-set-job-step-success-or-failure-flow"></a><span data-ttu-id="8956c-138">若要設定作業步驟成功或失敗的流程</span><span class="sxs-lookup"><span data-stu-id="8956c-138">To set job step success or failure flow</span></span>  
  
1.  <span data-ttu-id="8956c-139">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8956c-139">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8956c-140">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="8956c-140">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8956c-141">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="8956c-141">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @on_success_action = 1;  
    GO  
    ```  
  
 <span data-ttu-id="8956c-142">如需詳細資訊，請參閱[sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8956c-142">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="8956c-143">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="8956c-143">Using SQL Server Management Objects</span></span>  

### <a name="to-set-job-step-success-or-failure-flow"></a><span data-ttu-id="8956c-144">若要設定作業步驟成功或失敗的流程</span><span class="sxs-lookup"><span data-stu-id="8956c-144">To set job step success or failure flow</span></span>
  
 <span data-ttu-id="8956c-145">透過所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，使用 `JobStep` 類別。</span><span class="sxs-lookup"><span data-stu-id="8956c-145">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="8956c-146">如需詳細資訊，請參閱 [SQL Server 管理物件 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="8956c-146">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
