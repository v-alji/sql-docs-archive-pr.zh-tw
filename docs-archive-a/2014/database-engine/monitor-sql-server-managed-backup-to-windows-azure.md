---
title: 監視 SQL Server 受控備份至 Azure |Microsoft Docs
description: 本文說明的工具可讓您使用 SQL Server 受控備份至 Azure 來判斷備份的整體健全狀況，並找出錯誤。
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: cfb9e431-7d4c-457c-b090-6f2528b2f315
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: baec99e63c70befde0cfce76e42dd6202ebc0bad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599671"
---
# <a name="monitor-sql-server-managed-backup-to-azure"></a><span data-ttu-id="5ae3c-103">監視 SQL Server Managed Backup 到 Azure</span><span class="sxs-lookup"><span data-stu-id="5ae3c-103">Monitor SQL Server Managed Backup to Azure</span></span>
  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="5ae3c-104">有內建的測量工具，可用於找出備份程序中的問題和錯誤，並在可能時施以更正動作加以矯正。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-104">has built-in measures to identify problems and errors during backup processes and remedy with corrective action when possible.</span></span>  <span data-ttu-id="5ae3c-105">不過有某些狀況需要使用者介入。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-105">However there are certain situations where user intervention is required.</span></span> <span data-ttu-id="5ae3c-106">本主題描述可用於判斷備份之整體健康情況的工具，並找出需要處理的所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-106">This topic describes the tools that you can use to determine the overall health status of backups, and identify any errors that need to be addressed.</span></span>  
  
## <a name="overview-of-ss_smartbackup-built-in-debugging"></a><span data-ttu-id="5ae3c-107">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]內建偵錯概觀</span><span class="sxs-lookup"><span data-stu-id="5ae3c-107">Overview of [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Built-in Debugging</span></span>  
 <span data-ttu-id="5ae3c-108">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]會定期檢閱排程的備份，並嘗試重新排程所有失敗的備份。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-108">The [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] periodically reviews scheduled backups and attempts to reschedule any failed backups.</span></span> <span data-ttu-id="5ae3c-109">它會定期輪詢儲存體帳戶，找出記錄檔鏈結中，影響資料庫復原能力的中斷點，然後據此排程新的備份。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-109">It polls the storage account periodically to identify breaks in log chains affecting recoverability of the database, and schedules new backups accordingly.</span></span> <span data-ttu-id="5ae3c-110">它也會將 Azure 節流原則納入考慮，並具有可管理多個資料庫備份的機制。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-110">It also takes into account Azure throttling policies, and has mechanisms in place to manage multiple database backups.</span></span> [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="5ae3c-111">會使用擴充事件追蹤所有的活動。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-111">uses extended events to track all activity.</span></span> <span data-ttu-id="5ae3c-112">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]代理程式所使用的擴充事件通道包含管理、作業、分析和偵錯。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-112">The Extended Event channels used by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] agent include, Admin, Operational, Analytical, and Debug.</span></span> <span data-ttu-id="5ae3c-113">屬於管理類別的事件通常和錯誤有關，而且需要使用者的介入，並且預設為啟動。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-113">Events that fall under the Admin category usually are related to errors and require user intervention and are enabled by default.</span></span> <span data-ttu-id="5ae3c-114">分析事件也預設為開啟，不過通常和需要使用者介入的錯誤無關。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-114">Analytical events are also turned on by default, but usually are not related to errors that require user intervention.</span></span> <span data-ttu-id="5ae3c-115">作業事件通常做為參考用。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-115">Operation events are typically informational.</span></span> <span data-ttu-id="5ae3c-116">例如，「操作事件」包括排程備份、成功完成備份等。Debug 是最詳細的資訊，可在內部用 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 來判斷問題，並在必要時加以更正。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-116">For example, operational events include scheduling a backup, a successful completion of backup, etc. The Debug is the most verbose and is used internally by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] to determine issues and correct them if required.</span></span>  
  
### <a name="configure-monitoring-parameters-for-ss_smartbackup"></a><span data-ttu-id="5ae3c-117">設定[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]的監視參數</span><span class="sxs-lookup"><span data-stu-id="5ae3c-117">Configure Monitoring Parameters for [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]</span></span>  
 <span data-ttu-id="5ae3c-118">**Smart_admin sp_set_parameter**系統預存程式可讓您指定監視設定。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-118">The **smart_admin.sp_set_parameter** system stored procedure allows you to specify monitoring settings.</span></span> <span data-ttu-id="5ae3c-119">下列章節將逐步討論啟用擴充事件的程序，以及啟用錯誤和警告的電子郵件通知。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-119">The following sections walks through the process of enabling Extended Events,  and enabling email notification for errors and warnings.</span></span>  
  
 <span data-ttu-id="5ae3c-120">**Smart_admin. fn_get_parameter**函數可用來取得特定參數或所有已設定參數的目前設定。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-120">The **smart_admin.fn_get_parameter** function can be used to get the current setting for a specific parameter or all configured parameters.</span></span> <span data-ttu-id="5ae3c-121">如果從未設定過參數，該函數不會傳回任何值。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-121">If the parameters have never been configured, the function does not return any values.</span></span>  
  
1.  <span data-ttu-id="5ae3c-122">連接到 [!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-122">Connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5ae3c-123">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-123">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5ae3c-124">將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-124">Copy and paste the following example into the query window and then click **Execute**.</span></span> <span data-ttu-id="5ae3c-125">這樣會傳回擴充事件的現有組態，以及電子郵件通知。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-125">This will return the current configuration for Extended Events, and e-mail notifications.</span></span>  
  
```sql
Use msdb  
Go  
SELECT * FROM smart_admin.fn_get_parameter (NULL)  
GO  
```  
  
 <span data-ttu-id="5ae3c-126">如需詳細資訊，請參閱[smart_admin。 fn_get_parameter &#40;transact-sql&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-parameter-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="5ae3c-126">For more information, see [smart_admin.fn_get_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-parameter-transact-sql)</span></span>  
  
### <a name="extended-events-for-monitoring"></a><span data-ttu-id="5ae3c-127">監視的擴充事件</span><span class="sxs-lookup"><span data-stu-id="5ae3c-127">Extended Events for Monitoring</span></span>  
 <span data-ttu-id="5ae3c-128">管理、作業和分析事件預設為啟動。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-128">By default, Admin, Operational and Analytical events are turned on.</span></span> <span data-ttu-id="5ae3c-129">在確認需要人工介入解決問題的錯誤時，管理事件是極為重要且實用的方法。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-129">Admin events are most critical, useful when identifying errors that require manual intervention to solve the problem.</span></span> <span data-ttu-id="5ae3c-130">您可能會想要開啟作業和偵錯事件，但請注意，這些事件十分冗長，可能需要篩選。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-130">You may want to turn on the operational and debug events but consider that these events are verbose and may require some filtering.</span></span> <span data-ttu-id="5ae3c-131">下列程序描述如何監視透過擴充事件所記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-131">The following procedures describe how to monitor events logged through Extended Events.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5ae3c-132">不同於 SQL 引擎的擴充事件，[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]不支援擴充事件工作階段的概念。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-132">Unlike Extended Events for SQL Engine, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] does not support Extended Event session concepts.</span></span> <span data-ttu-id="5ae3c-133">系統預存程序和函式可用於和擴充事件進行互動。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-133">System stored procedures and functions are the tools used to interact with extended events.</span></span> <span data-ttu-id="5ae3c-134">您也可以從記錄檔目錄檢視擴充事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-134">You can also view the extended event log from the log directory.</span></span>  
  
##### <a name="to-configure-and-view-extended-events"></a><span data-ttu-id="5ae3c-135">設定和檢視擴充事件</span><span class="sxs-lookup"><span data-stu-id="5ae3c-135">To Configure and View Extended Events</span></span>  
  
1.  <span data-ttu-id="5ae3c-136">透過執行下列查詢來檢視可用的擴充事件通道及其目前狀態：</span><span class="sxs-lookup"><span data-stu-id="5ae3c-136">To view available Extended Event channels and their current status by running the following query:</span></span>  
  
    ```sql
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     <span data-ttu-id="5ae3c-137">不論是否可設定，以及目前是否已啟用，此查詢的輸出會顯示 event_name。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-137">The output from this query will display the event_name, whether it is configurable or not, and whether it is currently enabled.</span></span>  <span data-ttu-id="5ae3c-138">如需詳細資訊，請參閱[smart_admin. fn_get_current_xevent_settings &#40;transact-sql&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-current-xevent-settings-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-138">For more information, see [smart_admin.fn_get_current_xevent_settings &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-get-current-xevent-settings-transact-sql).</span></span>  
  
2.  <span data-ttu-id="5ae3c-139">若要啟用偵錯事件，請執行下列查詢：</span><span class="sxs-lookup"><span data-stu-id="5ae3c-139">To enable debug events, run the following query:</span></span>  
  
    ```sql
    --  to enable debug events  
    Use msdb;  
    GO 
    EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
    ```  
  
     <span data-ttu-id="5ae3c-140">如需預存程式的詳細資訊，請參閱[smart_admin。 sp_set_parameter &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-set-parameter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-140">For more information about the stored procedure, see [smart_admin.sp_set_parameter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-set-parameter-transact-sql).</span></span>  
  
3.  <span data-ttu-id="5ae3c-141">若要檢視紀錄的事件，請執行下列查詢：</span><span class="sxs-lookup"><span data-stu-id="5ae3c-141">To view the logged events run the following query:</span></span>  
  
    ```sql
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;
    ```  
  
    ```sql
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'
    ```  
  
### <a name="aggregated-error-countshealth-status"></a><span data-ttu-id="5ae3c-142">彙總錯誤計數/健康情況</span><span class="sxs-lookup"><span data-stu-id="5ae3c-142">Aggregated Error Counts/Health Status</span></span>  
 <span data-ttu-id="5ae3c-143">**Smart_admin fn_get_health_status**函式會傳回每個分類的匯總錯誤計數資料表，可用來監視的健全狀況狀態 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-143">The **smart_admin.fn_get_health_status** function returns a table of aggregated error counts for each category that can be used to monitor the health status of [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)].</span></span> <span data-ttu-id="5ae3c-144">系統也使用相同的功能設定本主題稍後所述的電子郵件通知機制。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-144">This same function is also used by the system configured e-mail notification mechanism described later in this topic.</span></span>   
<span data-ttu-id="5ae3c-145">這些彙總計算可用來監視系統健全狀況。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-145">These aggregated counts can be used to monitor system health.</span></span> <span data-ttu-id="5ae3c-146">例如，如果 number_ of_retention_loops 資料行在 30 分鐘內為 0，則保留管理可能需要耗費長時間運作，或甚至運作不正確。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-146">For example, if the number_ of_retention_loops column is 0 in 30 minutes, it is possible that retention management is taking long time or even not working correctly.</span></span> <span data-ttu-id="5ae3c-147">非零的錯誤資料行可能表示出現問題，應檢查擴充事件記錄來發現此問題。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-147">Non-zero error columns may indicate problems and Extended Events logs should be checked to discover the problem.</span></span> <span data-ttu-id="5ae3c-148">或者，呼叫**smart_admin. sp_get_backup_diagnostics**預存程式來尋找錯誤的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-148">Alternatively, call **smart_admin.sp_get_backup_diagnostics** stored procedure to find the details of the error.</span></span>  
  
### <a name="using-agent-notification-for-assessing-backup-status-and-health"></a><span data-ttu-id="5ae3c-149">使用代理程式通知以評估備份狀態和健全狀況</span><span class="sxs-lookup"><span data-stu-id="5ae3c-149">Using Agent Notification for Assessing Backup Status and Health</span></span>  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="5ae3c-150">包含使用 SQL Server 原則式管理原則的通知機制。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-150">includes a notification mechanism that is based on SQL Server policy based management policies.</span></span>  
  
 <span data-ttu-id="5ae3c-151">**必要條件：**</span><span class="sxs-lookup"><span data-stu-id="5ae3c-151">**Prerequisites:**</span></span>  
  
-   <span data-ttu-id="5ae3c-152">需要 Database Mail 使用這項功能。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-152">Database Mail is required to use this functionality.</span></span> <span data-ttu-id="5ae3c-153">如需有關如何為 SQL Server 的實例啟用 DB Mail 的詳細資訊，請參閱[設定 Database Mail](../relational-databases/database-mail/configure-database-mail.md)。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-153">For more information, about how to enable DB Mail for the instance of SQL Server, see [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md).</span></span>  
  
-   <span data-ttu-id="5ae3c-154">SQL Server Agent 警示系統的屬性應設定為使用 Database Mail。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-154">SQL Server Agent Alert System properties should be set to use Database Mail.</span></span>  
  
 <span data-ttu-id="5ae3c-155">**通知架構：**</span><span class="sxs-lookup"><span data-stu-id="5ae3c-155">**Notification Architecture:**</span></span>  
  
-   <span data-ttu-id="5ae3c-156">以**原則為基礎的管理：** 設定兩個原則來監視備份健全狀況：**智慧型管理系統健全狀況原則**，以及**智慧型管理使用者動作健全狀況原則**。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-156">**Policy Based Management:** Two policies are set to monitor backup health: **Smart Admin System Health Policy**, and the **Smart Admin User Action Health Policy**.</span></span> <span data-ttu-id="5ae3c-157">智慧型管理系統健全狀況原則會評估嚴重的錯誤，例如缺少或無效的 SQL 認證以及連接錯誤，並且回報系統的健全狀況。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-157">The Smart Admin System Health Policy evaluates critical errors like lack of or invalid SQL Credentials, connectivity errors and reports the health of the system.</span></span> <span data-ttu-id="5ae3c-158">這些通常需要手動的動作才能修正基礎的問題。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-158">These typically require a manual action to correct the underlying issue.</span></span> <span data-ttu-id="5ae3c-159">智慧管理使用者動作健全狀況原則會評估警告訊息，例如損毀的備份等等。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-159">The Smart Admin User Action Health Policy evaluates warnings such as corrupted backups, and such.</span></span>  <span data-ttu-id="5ae3c-160">這些可能不需要任何動作，只是事件的警告訊息。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-160">These may not require any action but just a warning of an event.</span></span> <span data-ttu-id="5ae3c-161">依照預期，這類問題會由[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]代理程式自動處理。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-161">It is expected that such issues will be automatically taken care of by [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] agent.</span></span>  
  
-   <span data-ttu-id="5ae3c-162">**SQL Server Agent**作業：使用具有三個作業步驟的 SQL Server Agent 作業來執行通知。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-162">**SQL Server Agent** Job: The notification is performed using a SQL Server Agent job that has three job steps.</span></span> <span data-ttu-id="5ae3c-163">在第一個作業步驟中，它會偵測[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]是否為資料庫或執行個體進行設定。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-163">In the first job step it detects to see whether [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is configured for a database or instance.</span></span> <span data-ttu-id="5ae3c-164">當其偵測到已有啟用及設定[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]時，會執行第二個步驟：透過評估 SQL Server 原則式管理原則，執行 PowerShell 指令程式評估健康狀態。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-164">If it finds [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] enabled and configured, it executes the second step: executes a PowerShell cmdlet that assess the health status by evaluating the SQL Server policy based management policies.</span></span> <span data-ttu-id="5ae3c-165">若是偵測到錯誤或警告便，其會失敗，然後觸發第三個步驟︰傳送隨附此錯誤/警告報表的電子郵件通知。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-165">If it finds either an error or warning, it fails which then triggers the third step: The third step sends out an e-mail notification with the error/warning report.</span></span>  <span data-ttu-id="5ae3c-166">但是此 SQL Server Agent 預設為不啟用。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-166">However this SQL Server Agent job is not enabled by default.</span></span> <span data-ttu-id="5ae3c-167">若要啟用電子郵件通知工作，請使用**smart_admin. sp_set_backup_parameter**系統預存程式。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-167">To enable the e-mail notification job, use the **smart_admin.sp_set_backup_parameter** system stored procedure.</span></span>  <span data-ttu-id="5ae3c-168">下列程序將更詳細說明這些步驟：</span><span class="sxs-lookup"><span data-stu-id="5ae3c-168">The following procedure describes the steps in more detail:</span></span>  
  
##### <a name="enabling-email-notification"></a><span data-ttu-id="5ae3c-169">啟用電子郵件通知</span><span class="sxs-lookup"><span data-stu-id="5ae3c-169">Enabling Email Notification</span></span>  
  
1.  <span data-ttu-id="5ae3c-170">如果尚未設定 Database Mail，請使用[設定 Database Mail](../relational-databases/database-mail/configure-database-mail.md)中所述的步驟。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-170">If Database Mail is not already configured, use the steps described in [Configure Database Mail](../relational-databases/database-mail/configure-database-mail.md).</span></span>  
  
2.  <span data-ttu-id="5ae3c-171">將資料庫設定為 SQL Server 警示系統的郵件系統：以滑鼠右鍵按一下**SQL Server Agent**，選取 [**警示系統**]，勾選 [**啟用郵件設定檔**] 方塊，選取 [ **Database Mail**作為**郵件系統**]，然後選取先前建立的郵件設定檔。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-171">Set database as the Mail System for SQL Server Alert System: Right Click on **SQL Server Agent**, select **Alert System**, check the **Enable mail profile** box, Select **Database Mail** as the **Mail System**, and select a previously created Mail profile.</span></span>  
  
3.  <span data-ttu-id="5ae3c-172">在查詢視窗中執行下列查詢，並提供您希望通知送達的電子郵件地址：</span><span class="sxs-lookup"><span data-stu-id="5ae3c-172">Run the following query in a query window and provide the e-mail address where you want the notification to be sent to:</span></span>  
  
    ```sql
    Use msdb  
    Go  
    EXEC smart_admin.sp_set_parameter @parameter_name = 'SSMBackup2WANotificationEmailIds', @parameter_value = '<email address>'
    ```  
  
     <span data-ttu-id="5ae3c-173">當備份有錯誤或問題時，這會建立用來蒐集健康情況及傳送通知的 SQL Server Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-173">This creates a SQL Server Agent job that is used to gather health status and send notifications when there is an error or an issue with backups.</span></span>  
  
 <span data-ttu-id="5ae3c-174">下列是啟用 DB 郵件和透過 SQL Server Agent 作業設定電子郵件通知的範例指令碼</span><span class="sxs-lookup"><span data-stu-id="5ae3c-174">Following is a sample script  to enable DB Mail and set up the e-mail notification through SQL Server Agent Job</span></span>  
  
```sql
-- Prereq: Make sure that SQL Server service runs in a service account that has  
--  access to SMTP Server   
-- set SQL Server service account as domain account   
  
EXEC sp_configure 'show advanced', 1  
RECONFIGURE  
GO  
  
-- Enable DBMail  
EXEC sp_configure 'Database Mail XPs',1  
GO  
RECONFIGURE  
GO  
  
-- Configure DBMail  
DECLARE @emailid NVARCHAR(255)  
-- Note: change this email to your own email id  
SET @emailid = N'emailalias@mycompany.com'  
  
DECLARE @smtpserver NVARCHAR(255)  
SET @smtpserver = N'smtphost.domainname.com'  
  
DECLARE @mailprofile NVARCHAR(255)  
SET @mailprofile = N'my_profile'  
  
EXEC msdb.dbo.sysmail_add_account_sp @account_name=N'myaccount',  
                @email_address = @emailid,  
                @replyto_address = @emailid,  
                @mailserver_name = @smtpserver,  
                @use_default_credentials = 1  
  
EXEC msdb.dbo.sysmail_add_profile_sp @profile_name=@mailprofile  
EXEC msdb.dbo.sysmail_add_profileaccount_sp @profile_name=@mailprofile, @account_name=N'myaccount', @sequence_number=1  
  
-- Set SQL Agent to use DBMail profile  
EXEC msdb.dbo.sp_set_sqlagent_properties @databasemail_profile = @mailprofile  
  
-- Configure Notifications   
EXEC msdb.smart_admin.sp_set_parameter  
@parameter_name = 'SSMBackup2WANotificationEmailIds',  
@parameter_value = @emailid  
  
-- To test is you are receiving notifications  
-- delete few backup files from your storage container, Wait for 15 minutes & see if you get any email notification
```  
  
### <a name="using-powershell-to-setup-custom-health-monitoring"></a><span data-ttu-id="5ae3c-175">使用 PowerShell 設定自訂健全狀況監視</span><span class="sxs-lookup"><span data-stu-id="5ae3c-175">Using PowerShell to Setup Custom Health Monitoring</span></span>  
 <span data-ttu-id="5ae3c-176">**Set-sqlsmartadmin** Cmdlet 可以用來建立自訂健全狀況監視。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-176">The **Test-SqlSmartAdmin** cmdlet can be used to create custom health monitoring.</span></span> <span data-ttu-id="5ae3c-177">例如，前一節所述的通知選項可在執行個體層級設定。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-177">For example, the notification option described in the previous section can be configured at the instance level.</span></span>  <span data-ttu-id="5ae3c-178">如果您將多個 SQL Server 執行個體設定為使用[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]，即可使用 PowerShell 指令程式建立指令碼，以收集所有執行個體之備份的狀態及健全狀態。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-178">If you have several instances of SQL Server configured to use [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)], the PowerShell cmdlet can be used to create scripts in gather the status and health of backups for all the instances.</span></span>  
  
 <span data-ttu-id="5ae3c-179">**Set-sqlsmartadmin 指令程式**會評估 SQL Server 以原則為基礎的管理原則所傳回的錯誤和警告，並報告已匯總的狀態。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-179">The **Test-SqlSmartAdmin** cmdlet assesses the errors and warnings returned by the SQL Server Policy Based Management policies and reports out a rolled up status.</span></span>  <span data-ttu-id="5ae3c-180">根據預設，此指令程式使用系統原則。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-180">By default this cmdlet uses the system policies.</span></span> <span data-ttu-id="5ae3c-181">若要包含所有自訂原則，請使用 `-AllowUserPolicies` 參數。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-181">To include any custom policy use the `-AllowUserPolicies` parameter.</span></span>  
  
 <span data-ttu-id="5ae3c-182">下面是 PowerShell 指令碼的範例，它會根據系統原則和所有建立的使用者原則，傳回錯誤和警告報告：</span><span class="sxs-lookup"><span data-stu-id="5ae3c-182">Following is a sample PowerShell script that returns a report of errors and warnings based on the system policies and any user policies created:</span></span>  
  
```powershell
$policyResults = Get-SqlSmartAdmin | Test-SqlSmartAdmin -AllowUserPolicies  
$policyResults.PolicyEvaluationDetails | Select Name, Category, Expression, Result, Exception | fl
```  
  
 <span data-ttu-id="5ae3c-183">下列腳本會傳回預設實例 () 之錯誤和警告的詳細報告 `\SQL\COMPUTER\DEFAULT` ：</span><span class="sxs-lookup"><span data-stu-id="5ae3c-183">The following script returns a detailed report of the errors and warnings for the default instance (`\SQL\COMPUTER\DEFAULT`):</span></span>  
  
```powershell
(Get-SqlSmartAdmin ).EnumHealthStatus()  
```  
  
### <a name="objects-in-msdb-database"></a><span data-ttu-id="5ae3c-184">MSDB 資料庫中的物件</span><span class="sxs-lookup"><span data-stu-id="5ae3c-184">Objects in MSDB database</span></span>  
 <span data-ttu-id="5ae3c-185">系統會安裝實作此功能的物件。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-185">There are objects that are installed to implement the functionality.</span></span> <span data-ttu-id="5ae3c-186">這些物件會保留給內部使用。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-186">These objects are reserved for internal use.</span></span> <span data-ttu-id="5ae3c-187">不過，有一個系統資料表對於監視備份狀態很實用：smart_backup_files。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-187">However, there is one system table that can be useful in monitoring the backup status: smart_backup_files.</span></span> <span data-ttu-id="5ae3c-188">與監視相關的大部分資訊（例如備份類型、資料庫名稱、第一個和最後一個 lsn、備份到期日）都會透過系統函數[smart_admin 公開。 fn_available_backups &#40;transact-sql&#41;](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-188">Most of the Information   stored in this table relevant to monitoring like the type of backup, database name, first and last lsn, backup expiry dates are exposed through the system function [smart_admin.fn_available_backups &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/managed-backup-fn-available-backups-transact-sql).</span></span> <span data-ttu-id="5ae3c-189">但是，使用此函數則無法使用 smart_backup_files 資料表中的狀態資料行 (可指示備份檔案的狀態)。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-189">However the status column in the smart_backup_files table which indicates the status of the backup file is not available using the function.</span></span> <span data-ttu-id="5ae3c-190">以下是您可以從系統資料表中擷取部分資訊 (包括狀態) 的範例查詢：</span><span class="sxs-lookup"><span data-stu-id="5ae3c-190">Following is a sample query you can use to retrieve the some information including the status from the system table:</span></span>  
  
```sql
USE msdb  
GO  
SELECT  
 database_name AS [Database Name] ,backup_path AS [Backup Destination and File]  
,[Backup Type] =  
CASE backup_type  
WHEN 1 THEN 'FULL'  
WHEN 2 THEN 'LOG'  
END  
,[Backup Status] =  
CASE [status]  
WHEN 'A' THEN 'Available'  
WHEN 'B' THEN 'Copy In Progress'  
WHEN 'C' THEN 'Corrupted'  
WHEN 'D' THEN 'Deleted'  
WHEN 'F' THEN 'Copy Failed'  
WHEN 'U' THEN 'Unknown'  
END  
,first_lsn AS [First LSN]  
,last_lsn AS [Last LSN]  
,backup_start_date AS [Backup Start Time]  
,backup_finish_date AS [Backup Completion Time]  
,expiration_date AS [Backup Expiry Date/Time]  
FROM  
smart_backup_files;
```  
  
 <span data-ttu-id="5ae3c-191">下面是傳回之不同狀態的詳細說明：</span><span class="sxs-lookup"><span data-stu-id="5ae3c-191">Following is a detailed explanation of the different status returned:</span></span>  
  
-   <span data-ttu-id="5ae3c-192">**可用-A：** 這是一般的備份檔案。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-192">**Available - A:** This is a normal backup file.</span></span> <span data-ttu-id="5ae3c-193">備份已完成，也已確認它可在 Azure 儲存體中使用。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-193">The backup has been completed, and also verified that it is available in the Azure storage.</span></span>  
  
-   <span data-ttu-id="5ae3c-194">**複製進行中-B：** 此狀態特別適用于可用性群組資料庫。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-194">**Copy in Progress -B:** This status is specifically for Availability Group databases.</span></span> <span data-ttu-id="5ae3c-195">如果[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]在備份記錄鏈結中偵測到中斷，它會先嘗試識別可能在備份鏈結中造成中斷的備份。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-195">If [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] detects a break in the backup log chain, it will first attempt identify the  backup that might have caused the break in backup chain.</span></span> <span data-ttu-id="5ae3c-196">在尋找備份檔案時，它會嘗試將檔案複製到 Azure 儲存體。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-196">On finding the backup file it attempts to copy the file to Azure storage.</span></span> <span data-ttu-id="5ae3c-197">當複製作業正在進行時，它將會顯示這個狀態。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-197">When the copying process is in progress it will display this status.</span></span>  
  
-   <span data-ttu-id="5ae3c-198">**複製失敗-F：** 類似于複製進行中，這是可用性群組資料庫的特定。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-198">**Copy Failed - F:** Similar to Copy In Progress, this is specific t Availability Group databases.</span></span> <span data-ttu-id="5ae3c-199">如果複製程序失敗，狀態會標示成 F。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-199">If the copy process fails, the status is marked as F.</span></span>  
  
-   <span data-ttu-id="5ae3c-200">**損毀-C：** 如果 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 無法藉由執行還原 HEADER_ONLY 命令來驗證儲存體中的備份檔案，即使在多次嘗試之後，它也會將此檔案標示為已損毀。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-200">**Corrupted - C:** If [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] is unable to verify the backup file in the storage by performing a RESTORE HEADER_ONLY command even after multiple attempts, it marks this file as corrupted.</span></span> [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]<span data-ttu-id="5ae3c-201">會排程備份，以確保損毀的檔案不會導致備份鏈結中斷。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-201">will schedule a backup to ensure that the corrupted file does not result in a break of the backup chain.</span></span>  
  
-   <span data-ttu-id="5ae3c-202">**已刪除-D：** 在 Azure 儲存體中找不到對應的檔案。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-202">**Deleted - D:** The corresponding file cannot be found in the Azure storage.</span></span> <span data-ttu-id="5ae3c-203">如果已刪除的檔案造成備份鏈結中斷，[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]將會排程備份。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-203">[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] will schedule a backup if the deleted file results in a break in the backup chain.</span></span>  
  
-   <span data-ttu-id="5ae3c-204">**未知-U：** 此狀態表示尚未 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] 能夠驗證 Azure 儲存體中的檔案是否存在及其屬性。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-204">**Unknown - U:** This status indicated that [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] has not yet been able to verify file existence and its properties in the Azure storage.</span></span> <span data-ttu-id="5ae3c-205">下次執行此程序時 (大約每隔 15 分鐘執行一次)，將會更新此狀態。</span><span class="sxs-lookup"><span data-stu-id="5ae3c-205">The next time the process runs, which is approximately every 15 minutes, this status will be updated.</span></span>  
