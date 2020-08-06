---
title: 建立 SQL Server Agent 主要作業 | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], master jobs
- jobs [SQL Server Agent], creating
- master SQL Server Agent job [SQL Server]
ms.assetid: c12ab23f-d7ee-43a5-8cd2-0a9121292bcd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8a6503caec3f153878e360ee29ce09a5c099ade5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700564"
---
# <a name="create-a-sql-server-agent-master-job"></a><span data-ttu-id="0dc9e-102">建立 SQL Server Agent 主要作業</span><span class="sxs-lookup"><span data-stu-id="0dc9e-102">Create a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="0dc9e-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或，在中建立主要代理程式作業 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-103">This topic describes how to create a master [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0dc9e-104">開始之前</span><span class="sxs-lookup"><span data-stu-id="0dc9e-104">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0dc9e-105">限制事項</span><span class="sxs-lookup"><span data-stu-id="0dc9e-105">Limitations and Restrictions</span></span>  
 <span data-ttu-id="0dc9e-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 主要作業的變更必須傳播至所有相關的目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-106">Changes to master [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs must be propagated to all involved target servers.</span></span> <span data-ttu-id="0dc9e-107">因為目標伺服器最初並未下載作業，直到指定這些目標後才下載，所以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 建議您先完成特定作業的所有作業步驟和作業排程，再指定任何目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-107">Because target servers do not initially download a job until those targets are specified, [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommends that you complete all job steps and job schedules for a particular job before you specify any target servers.</span></span> <span data-ttu-id="0dc9e-108">否則，您必須執行 **sp_post_msx_operation** 預存程序或使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]修改作業，手動要求目標伺服器重新下載已修改的作業。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-108">Otherwise, you must manual request that the target servers download the modified job again, either by executing the **sp_post_msx_operation** stored procedure or modifying the job using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="0dc9e-109">如需詳細資訊，請參閱[sp_post_msx_operation &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql)或[修改作業](modify-a-job.md)。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-109">For more information, see [sp_post_msx_operation &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql) or [Modify a Job](modify-a-job.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0dc9e-110">Security</span><span class="sxs-lookup"><span data-stu-id="0dc9e-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0dc9e-111">權限</span><span class="sxs-lookup"><span data-stu-id="0dc9e-111">Permissions</span></span>  
 <span data-ttu-id="0dc9e-112">具有與 Proxy 相關聯之步驟的散發式作業，而該 Proxy 是在目標伺服器上的 Proxy 帳戶內容下執行 。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-112">Distributed jobs that have steps which are associated with a proxy run under the context of the proxy account on the target server.</span></span> <span data-ttu-id="0dc9e-113">請確保符合以下條件，否則與 Proxy 相關聯之作業步驟將不會從主要伺服器下載至目標：</span><span class="sxs-lookup"><span data-stu-id="0dc9e-113">Make sure that the following conditions are met or job steps that are associated with a proxy will not be downloaded from the master server to the target:</span></span>  
  
-   <span data-ttu-id="0dc9e-114">登錄子機碼**\ HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server \\ < *instance_name*> \sql Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) 設定為 1 (true) 。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-114">The registry subkey **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<*instance_name*>\SQL Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) is set to 1 (true).</span></span> <span data-ttu-id="0dc9e-115">依預設，這個子機碼設為 0 (False)。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-115">By default, this subkey is set to 0 (false).</span></span>  
  
-   <span data-ttu-id="0dc9e-116">存在於目標伺服器上的 Proxy 帳戶，而該帳戶名稱與執行作業步驟之主要伺服器上的 Proxy 帳戶名稱相同。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-116">A proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
 <span data-ttu-id="0dc9e-117">如果使用 Proxy 帳戶的作業步驟在從主要伺服器下載 Proxy 帳戶至目標伺服器時失敗，您可以在 **msdb** 資料庫的 **sysdownloadlist** 資料表中，檢查 **error_message** 資料行，以了解下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="0dc9e-117">If job steps that use proxy accounts fail when downloading them from the master server to the target server, you can check the **error_message** column in the **sysdownloadlist** table in the **msdb** database for the following error messages:</span></span>  
  
-   <span data-ttu-id="0dc9e-118">「作業步驟需要 Proxy 帳戶，不過目標伺服器上已停用 Proxy 比對。」</span><span class="sxs-lookup"><span data-stu-id="0dc9e-118">"The job step requires a proxy account, however proxy matching is disabled on the target server."</span></span> <span data-ttu-id="0dc9e-119">若要解決這個錯誤，請將 **AllowDownloadedJobsToMatchProxyName** 登錄子機碼設為 1。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-119">To resolve this error, set the **AllowDownloadedJobsToMatchProxyName** registry subkey to 1.</span></span>  
  
-   <span data-ttu-id="0dc9e-120">「找不到 Proxy。」</span><span class="sxs-lookup"><span data-stu-id="0dc9e-120">"Proxy not found."</span></span> <span data-ttu-id="0dc9e-121">若要解決這個錯誤，請確定目標伺服器上有 Proxy 帳戶，且帳戶名稱與執行該作業步驟的主要伺服器 Proxy 帳戶相同。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-121">To resolve this error, make sure a proxy account exists on the target server that has the same name as the master server proxy account under which the job step runs.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0dc9e-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0dc9e-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-master-sql-server-agent-job"></a><span data-ttu-id="0dc9e-123">若要建立 SQL Server Agent 的主要作業</span><span class="sxs-lookup"><span data-stu-id="0dc9e-123">To create a master SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="0dc9e-124">在 **[物件總管]** 中，按一下加號展開要建立 SQL Server Agent 作業的伺服器。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-124">In the **Object Explorer**, click the plus sign to expand the server where you want to create a SQL Server Agent job.</span></span>  
  
2.  <span data-ttu-id="0dc9e-125">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-125">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="0dc9e-126">以滑鼠右鍵按一下 [作業]\*\*\*\* 資料夾，然後選取 [新增作業...]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-126">Right-click the **Jobs** folder and select **New Job...**.</span></span>  
  
4.  <span data-ttu-id="0dc9e-127">在 **[新增作業]** 對話方塊的 **[一般]** 頁面中，修改作業的一般屬性。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-127">In the **New Job** dialog box, on the **General** page, modify the general properties of the job.</span></span> <span data-ttu-id="0dc9e-128">如需有關此頁面上可用選項的詳細資訊，請參閱[作業屬性和新增作業 &#40;一般頁面&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="0dc9e-128">For more information on the available options on this page, see [Job Properties and New Job &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)</span></span>  
  
5.  <span data-ttu-id="0dc9e-129">在 **[步驟]** 頁面上，組織作業步驟。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-129">On the **Steps** page, organize the job steps.</span></span> <span data-ttu-id="0dc9e-130">如需有關此頁面上可用選項的詳細資訊，請參閱[作業屬性：新增作業 &#40;步驟頁面&#41;](job-properties-new-job-steps-page.md)</span><span class="sxs-lookup"><span data-stu-id="0dc9e-130">For more information on the available options on this page, see [Job Properties:New Job &#40;Steps Page&#41;](job-properties-new-job-steps-page.md)</span></span>  
  
6.  <span data-ttu-id="0dc9e-131">在 **[排程]** 頁面上，組織作業的排程。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-131">On the **Schedules** page, organize schedules for the job.</span></span> <span data-ttu-id="0dc9e-132">如需有關此頁面上可用選項的詳細資訊，請參閱[作業屬性：新增作業 &#40;排程頁面&#41;](job-properties-new-job-schedules-page.md)</span><span class="sxs-lookup"><span data-stu-id="0dc9e-132">For more information on the available options on this page, see [Job Properties: New Job &#40;Schedules Page&#41;](job-properties-new-job-schedules-page.md)</span></span>  
  
7.  <span data-ttu-id="0dc9e-133">在 **[警示]** 頁面上，組織作業的警示。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-133">On the **Alerts** page, organize the alerts for the job.</span></span> <span data-ttu-id="0dc9e-134">如需有關此頁面上可用選項的詳細資訊，請參閱[作業屬性：新增作業 &#40;警示頁面&#41;](job-properties-new-job-alerts-page.md)</span><span class="sxs-lookup"><span data-stu-id="0dc9e-134">For more information on the available options on this page, see [Job Properties: New Job &#40;Alerts Page&#41;](job-properties-new-job-alerts-page.md)</span></span>  
  
8.  <span data-ttu-id="0dc9e-135">在 [通知]\*\*\*\* 頁面上設定當作業完成時，[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-135">On the **Notifications** page, set actions for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to perform when the job completes.</span></span> <span data-ttu-id="0dc9e-136">如需有關此頁面上可用選項的詳細資訊，請參閱[作業屬性：新增作業 &#40;通知頁面&#41;](job-properties-new-job-notifications-page.md)。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-136">For more information on the available options on this page, see [Job Properties: New Job &#40;Notifications Page&#41;](job-properties-new-job-notifications-page.md).</span></span>  
  
9. <span data-ttu-id="0dc9e-137">在 **[目標]** 頁面上，管理作業的目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-137">On the **Targets** page, manage the target servers for the job.</span></span> <span data-ttu-id="0dc9e-138">如需有關此頁面上可用選項的詳細資訊，請參閱[工作屬性：新增作業 &#40;目標頁面&#41;](job-properties-new-job-targets-page.md)。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-138">For more information on the available options on this page, see [Job Properties: New Job &#40;Targets Page&#41;](job-properties-new-job-targets-page.md).</span></span>  
  
10. <span data-ttu-id="0dc9e-139">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-139">When finished, click **OK**.</span></span>  
  

  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0dc9e-140">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0dc9e-140">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-master-sql-server-agent-job"></a><span data-ttu-id="0dc9e-141">若要建立 SQL Server Agent 的主要作業</span><span class="sxs-lookup"><span data-stu-id="0dc9e-141">To create a master SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="0dc9e-142">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-142">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0dc9e-143">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-143">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0dc9e-144">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="0dc9e-144">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb ;  
    GO  
    -- Adds a new job executed by the SQLServerAgent service called 'Weekly Sales Data Backup'  
    EXEC dbo.sp_add_job  
        @job_name = N'Weekly Sales Data Backup' ;  
    GO  
    -- Adds a step (operation) to the 'Weekly Sales Data Backup' job.  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    -- Creates a schedule called RunOnce  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
    USE msdb ;  
    GO  
    -- Sets the 'RunOnce' schedule to the "Weekly Sales Data Backup' Job  
    EXEC sp_attach_schedule  
       @job_name = N'Weekly Sales Data Backup',  
       @schedule_name = N'RunOnce';  
    GO  
    -- assigns the multiserver job Weekly Sales Backups to the server SEATTLE2  
    -- assumes that SEATTLE2 is registered as a target server for the current instance.  
    EXEC dbo.sp_add_jobserver  
        @job_name = N'Weekly Sales Data Backups',  
        @server_name = N'SEATTLE2' ;  
    GO  
    ```  
  
 <span data-ttu-id="0dc9e-145">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="0dc9e-145">For more information, see:</span></span>  
  
-   [<span data-ttu-id="0dc9e-146">sp_add_job &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0dc9e-146">sp_add_job &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
  
-   [<span data-ttu-id="0dc9e-147">sp_add_jobstep &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0dc9e-147">sp_add_jobstep &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [<span data-ttu-id="0dc9e-148">sp_add_schedule &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0dc9e-148">sp_add_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)  
  
-   [<span data-ttu-id="0dc9e-149">sp_attach_schedule &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0dc9e-149">sp_attach_schedule &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
-   [<span data-ttu-id="0dc9e-150">sp_add_jobserver &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="0dc9e-150">sp_add_jobserver &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)  
  

  
  
