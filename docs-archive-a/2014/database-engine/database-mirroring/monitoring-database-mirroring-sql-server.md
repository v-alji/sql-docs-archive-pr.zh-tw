---
title: 監視資料庫鏡像 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- monitoring [SQL Server], database mirroring
- database mirroring [SQL Server], monitoring
ms.assetid: a7b1b9b0-7c19-4acc-9de3-3a7c5e70694d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 92179abd47df2ee40b48be8eade7ea3e7b9267af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701863"
---
# <a name="monitoring-database-mirroring-sql-server"></a><span data-ttu-id="cc27c-102">監視資料庫鏡像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cc27c-102">Monitoring Database Mirroring (SQL Server)</span></span>
  <span data-ttu-id="cc27c-103">本節介紹「資料庫鏡像監視器」和 **sp_dbmmonitor** 系統預存程序、說明資料庫鏡像監視功能 (包括 [資料庫鏡像監視器作業] ) 的運作方式，以及摘要說明您可以監視的資料庫鏡像工作階段相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cc27c-103">This section introduces Database Mirroring Monitor and the **sp_dbmmonitor** system stored procedures, explains how database mirroring monitoring works (including the **Database Mirroring Monitor Job)**, and summarizes the information that you can monitor about database mirroring sessions.</span></span> <span data-ttu-id="cc27c-104">另外，本節還會介紹如何為一組預先定義的資料庫鏡像事件定義警告臨界值，以及如何在任何資料庫鏡像事件上設定警示。</span><span class="sxs-lookup"><span data-stu-id="cc27c-104">Additionally, this section introduces how to define warning thresholds for a set of predefined database mirroring events and how to set up alerts on any database mirroring event.</span></span>  
  
 <span data-ttu-id="cc27c-105">您可以在鏡像工作階段期間監視鏡像資料庫，以便確認資料流程是否正常。</span><span class="sxs-lookup"><span data-stu-id="cc27c-105">You can monitor a mirrored database during a mirroring session to verify whether and how well data is flowing.</span></span> <span data-ttu-id="cc27c-106">若要針對伺服器執行個體上的一個或多個鏡像資料庫設定並管理監視作業，您可以使用「資料庫鏡像監視器」或 **sp_dbmmonitor** 系統預存程序。</span><span class="sxs-lookup"><span data-stu-id="cc27c-106">To set up and manage monitoring for one or more of the mirrored databases on a server instance, you can use either Database Mirroring Monitor or the **sp_dbmmonitor** system stored procedures.</span></span>  
  
 <span data-ttu-id="cc27c-107">資料庫鏡像監視作業 **[資料庫鏡像監視器作業]** 是在背景中獨立運作，不受 [資料庫鏡像監視器] 影響。</span><span class="sxs-lookup"><span data-stu-id="cc27c-107">A database mirroring monitoring job, **Database Mirroring Monitor Job**, operates in the background, independently of Database Mirroring Monitor.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cc27c-108">Agent 會按一定的間隔呼叫 **[資料庫鏡像監視器作業]** ，預設為每分鐘一次，而這項作業則呼叫更新鏡像狀態的預存程序。</span><span class="sxs-lookup"><span data-stu-id="cc27c-108">Agent calls **Database Mirroring Monitor Job** at regular intervals, the default is once a minute, and the job calls a stored procedure that updates mirroring status.</span></span> <span data-ttu-id="cc27c-109">如果您使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來啟動鏡像工作階段，便會自動建立 **[資料庫鏡像監視器作業]** 。</span><span class="sxs-lookup"><span data-stu-id="cc27c-109">If you use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to start a mirroring session, **Database Mirroring Monitor Job** is created automatically.</span></span> <span data-ttu-id="cc27c-110">不過，如果您只使用 ALTER DATABASE *<資料庫名稱>* SET PARTNER 來啟動鏡像，則必須執行預存程序才能建立作業。</span><span class="sxs-lookup"><span data-stu-id="cc27c-110">However, if you only use ALTER DATABASE *<database_name>* SET PARTNER to start mirroring, you must create the job by running a stored procedure.</span></span>  
  
 <span data-ttu-id="cc27c-111">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="cc27c-111">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="cc27c-112">監視鏡像狀態</span><span class="sxs-lookup"><span data-stu-id="cc27c-112">Monitoring Mirroring Status</span></span>](#MonitoringStatus)  
  
-   [<span data-ttu-id="cc27c-113">與鏡像資料庫相關的其他資訊來源</span><span class="sxs-lookup"><span data-stu-id="cc27c-113">Additional Sources of Information About a Mirrored Database</span></span>](#AdditionalSources)  
  
-   [<span data-ttu-id="cc27c-114">相關工作</span><span class="sxs-lookup"><span data-stu-id="cc27c-114">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="monitoring-mirroring-status"></a><a name="MonitoringStatus"></a> <span data-ttu-id="cc27c-115">監視鏡像狀態</span><span class="sxs-lookup"><span data-stu-id="cc27c-115">Monitoring Mirroring Status</span></span>  
 <span data-ttu-id="cc27c-116">若要針對伺服器執行個體上的一個或多個鏡像資料庫設定並管理監視作業，您可以使用 [資料庫鏡像監視器] 或 **dbmmonitor** 系統預存程序。</span><span class="sxs-lookup"><span data-stu-id="cc27c-116">To set up and manage monitoring for one or more of the mirrored databases on a server instance, you can use either Database Mirroring Monitor or the **dbmmonitor** system stored procedures.</span></span> <span data-ttu-id="cc27c-117">您可以在鏡像工作階段期間監視鏡像資料庫，以便確認資料流程是否正常。</span><span class="sxs-lookup"><span data-stu-id="cc27c-117">You can monitor a mirrored database during a mirroring session to verify whether and how well data is flowing.</span></span>  
  
 <span data-ttu-id="cc27c-118">更明確地說，監視鏡像資料庫可讓您：</span><span class="sxs-lookup"><span data-stu-id="cc27c-118">Specifically, monitoring a mirrored database enables you to:</span></span>  
  
-   <span data-ttu-id="cc27c-119">確認鏡像是否正常運作。</span><span class="sxs-lookup"><span data-stu-id="cc27c-119">Verify that mirroring is functioning.</span></span>  
  
     <span data-ttu-id="cc27c-120">基本狀態包括了解兩個伺服器執行個體是否已啟用、伺服器是否已連接以及是否已將記錄從主體移至鏡像。</span><span class="sxs-lookup"><span data-stu-id="cc27c-120">Basic status includes knowing if the two server instances are up, that the servers are connected, and that the log is being moved from the principal to the mirror.</span></span>  
  
-   <span data-ttu-id="cc27c-121">判斷鏡像資料庫是否與主體資料庫保持同步。</span><span class="sxs-lookup"><span data-stu-id="cc27c-121">Determine whether the mirror database is keeping up with the principal database.</span></span>  
  
     <span data-ttu-id="cc27c-122">在高效能模式下，主體伺服器可能會開發未傳送記錄檔記錄的積存，而這些記錄仍需從主體伺服器傳送至鏡像伺服器。</span><span class="sxs-lookup"><span data-stu-id="cc27c-122">During high-performance mode, a principal server can develop a backlog of unsent log records that still need to be sent from the principal server to the mirror server.</span></span> <span data-ttu-id="cc27c-123">此外，在任何作業模式下，鏡像伺服器可能會開發未還原記錄檔記錄的積存，而且雖然這些記錄已經寫入記錄檔，不過仍需在鏡像資料庫上還原。</span><span class="sxs-lookup"><span data-stu-id="cc27c-123">Furthermore, in any operating mode, the mirror server can develop a backlog of unrestored log records that have been written to the log file but still need to be restored on the mirror database.</span></span>  
  
-   <span data-ttu-id="cc27c-124">判斷在高效能模式下主體伺服器執行個體成為無法使用時，有多少資料遺失。</span><span class="sxs-lookup"><span data-stu-id="cc27c-124">Determine how much data was lost when the principal server instance becomes unavailable during high-performance mode.</span></span>  
  
     <span data-ttu-id="cc27c-125">您可以透過查看未傳送的交易記錄量 (如果有的話) 以及在主體上認可遺失交易的時間間隔，藉以判斷資料遺失。</span><span class="sxs-lookup"><span data-stu-id="cc27c-125">You can determine data loss by looking at the amount of unsent transaction log (if any) and the time interval in which the lost transactions were committed at the principal.</span></span>  
  
-   <span data-ttu-id="cc27c-126">比較目前的效能與過去的效能。</span><span class="sxs-lookup"><span data-stu-id="cc27c-126">Compare current performance with past performance.</span></span>  
  
     <span data-ttu-id="cc27c-127">發生問題時，資料庫管理員可以檢視鏡像效能的記錄，以便有效了解目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="cc27c-127">When problems are occurring, a database administrator can view a history of the mirroring performance to help in understanding the current state.</span></span> <span data-ttu-id="cc27c-128">查看記錄可讓使用者偵測效能的趨勢，並識別效能問題的模式 (例如，網路速度變慢或輸入記錄的命令數目很大的當日時間)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-128">Looking at the history can allow the user to detect trends in performance, identify patterns of performance problems (such as times of day when the network is slow or the number of commands entering the log is very large).</span></span>  
  
-   <span data-ttu-id="cc27c-129">疑難排解鏡像夥伴之間減少資料流程的原因。</span><span class="sxs-lookup"><span data-stu-id="cc27c-129">Troubleshoot the cause of reduced data flow between mirroring partners.</span></span>  
  
-   <span data-ttu-id="cc27c-130">設定關鍵效能標準的警告臨界值。</span><span class="sxs-lookup"><span data-stu-id="cc27c-130">Set warning thresholds on key performance metrics.</span></span>  
  
     <span data-ttu-id="cc27c-131">如果新的狀態資料列含有超過臨界值的值，就會傳送參考用事件至 Windows 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="cc27c-131">If a new status row contains a value that exceeds a threshold, an informational event is sent to the Windows event log.</span></span> <span data-ttu-id="cc27c-132">然後，系統管理員就可以根據這些事件，手動設定警示。</span><span class="sxs-lookup"><span data-stu-id="cc27c-132">A system administrator can then manually configure alerts based on these events.</span></span> <span data-ttu-id="cc27c-133">如需詳細資訊，請參閱 [使用鏡像效能標準的警告臨界值與警示 &#40;SQL Server&#41;](use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-133">For more information, see [Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;](use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md).</span></span>  
  
###  <a name="tools-for-monitoring-database-mirroring-status"></a><a name="tools_for_monitoring_dbm_status"></a> <span data-ttu-id="cc27c-134">監視資料庫鏡像狀態的工具</span><span class="sxs-lookup"><span data-stu-id="cc27c-134">Tools for Monitoring Database Mirroring Status</span></span>  
 <span data-ttu-id="cc27c-135">您可以使用「資料庫鏡像監視器」或 **sp_dbmmonitorresults** 系統預存程序來監視鏡像狀態。</span><span class="sxs-lookup"><span data-stu-id="cc27c-135">Mirroring status can be monitored using either Database Mirroring Monitor or the **sp_dbmmonitorresults** system stored procedure.</span></span> <span data-ttu-id="cc27c-136">系統管理員 (亦即 **系統管理員** 固定伺服器角色的成員) 和系統管理員在 **msdb** 資料庫之 **dbm_monitor** 固定資料庫角色中加入的使用者，都可以使用這些工具來監視本機伺服器執行個體上任何鏡像資料庫的資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="cc27c-136">These tools can be used to monitor database mirroring on any mirrored database on the local server instance by both System administrators, that is, members of the **sysadmin** fixed server role, and user who have been added to the **dbm_monitor** fixed database role in the **msdb** database by a system administrator.</span></span> <span data-ttu-id="cc27c-137">使用任何一項工具時，系統管理員也可以手動重新整理鏡像狀態。</span><span class="sxs-lookup"><span data-stu-id="cc27c-137">When using either tool, a system administrator can also manually refresh mirroring status.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cc27c-138">系統管理員還可以設定並檢視關鍵效能標準的警告臨界值。</span><span class="sxs-lookup"><span data-stu-id="cc27c-138">System administrators can also configure and view warning thresholds for key performance metrics.</span></span> <span data-ttu-id="cc27c-139">如需詳細資訊，請參閱 [使用鏡像效能標準的警告臨界值與警示 &#40;SQL Server&#41;](use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-139">For more information, see [Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;](use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md).</span></span>  
  
-   <span data-ttu-id="cc27c-140">資料庫鏡像監視器</span><span class="sxs-lookup"><span data-stu-id="cc27c-140">Database Mirroring Monitor</span></span>  
  
     <span data-ttu-id="cc27c-141">[資料庫鏡像監視器] 是一個圖形化使用者介面工具，可讓系統管理員檢視並更新狀態，以及設定許多關鍵效能標準的警告臨界值。</span><span class="sxs-lookup"><span data-stu-id="cc27c-141">Database Mirroring Monitor is a graphical user interface tool that enables system administrators to view and update status and to configure warning thresholds on several key performance metrics.</span></span> <span data-ttu-id="cc27c-142">此外， **dbm_monitor** 固定資料庫角色的成員也可以使用「資料庫鏡像監視器」來檢視鏡像狀態資料表的最新資料列，不過他們無法更新狀態資料表。</span><span class="sxs-lookup"><span data-stu-id="cc27c-142">Database Mirroring Monitor can also be used by members of the **dbm_monitor** fixed database role to view the most recent row of the mirroring status table, though they cannot update the status table.</span></span>  
  
     <span data-ttu-id="cc27c-143">監視器會將選取的資料庫的狀態 (包括效能標準) 顯示在 **[狀態]** 索引標籤頁面上。</span><span class="sxs-lookup"><span data-stu-id="cc27c-143">The monitor displays the status, including performance metrics, for a selected database on the **Status** tabbed page.</span></span> <span data-ttu-id="cc27c-144">此頁面的內容來自於主體伺服器執行個體和鏡像伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="cc27c-144">The content of this page comes from both the principal and mirror server instances.</span></span> <span data-ttu-id="cc27c-145">透過與主體和鏡像伺服器執行個體的個別連接蒐集狀態時，會以非同步方式填滿頁面。</span><span class="sxs-lookup"><span data-stu-id="cc27c-145">The page is filled asynchronously as status is gathered through separate connections to the principal and mirror server instances.</span></span> <span data-ttu-id="cc27c-146">此監視器會嘗試以 30 秒的間隔更新狀態資料表。</span><span class="sxs-lookup"><span data-stu-id="cc27c-146">The monitor tries to update the status table at 30-second intervals.</span></span> <span data-ttu-id="cc27c-147">只有當資料表在 15 秒內尚未更新過，而且使用者是 **sysadmin** 固定伺服器角色的成員時，更新才會成功。</span><span class="sxs-lookup"><span data-stu-id="cc27c-147">The update succeeds only if the table has not been updated within 15 seconds and the user is a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="cc27c-148">如需 **[狀態]** 頁面上所報告資訊的摘要，請參閱本主題稍後的＜ [資料庫鏡像監視器顯示的狀態](#perf_metrics_of_dbm_monitor)＞。</span><span class="sxs-lookup"><span data-stu-id="cc27c-148">For a summary of the information reported on the **Status** page, see [Status Displayed by the Database Mirroring Monitor](#perf_metrics_of_dbm_monitor), later in this topic.</span></span>  
  
     <span data-ttu-id="cc27c-149">如需 [資料庫鏡像監視器] 介面的簡介，請參閱＜ [Database Mirroring Monitor Overview](database-mirroring-monitor-overview.md)＞。</span><span class="sxs-lookup"><span data-stu-id="cc27c-149">For an introduction to the Database Mirroring Monitor interface, see [Database Mirroring Monitor Overview](database-mirroring-monitor-overview.md).</span></span> <span data-ttu-id="cc27c-150">如需啟動「資料庫鏡像監視器」的資訊，請參閱 [啟動資料庫鏡像監視器 &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-150">For information on launching Database Mirroring Monitor, see [Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="cc27c-151">系統預存程序</span><span class="sxs-lookup"><span data-stu-id="cc27c-151">System stored procedures</span></span>  
  
     <span data-ttu-id="cc27c-152">您也可以執行 **sp_dbmmonitorresults** 系統預存程序來擷取或更新目前狀態。</span><span class="sxs-lookup"><span data-stu-id="cc27c-152">You can also retrieve or update the current status by running the **sp_dbmmonitorresults** system stored procedure.</span></span> <span data-ttu-id="cc27c-153">其他 dbmmonitor 預存程序則可讓您設定監視、變更監視參數、檢視目前的更新週期以及卸除伺服器執行個體上的監視作業。</span><span class="sxs-lookup"><span data-stu-id="cc27c-153">Other dbmmonitor stored procedures enable you to set up monitoring, change monitoring parameters, view the current update period, and drop monitoring on the server instance.</span></span>  
  
     <span data-ttu-id="cc27c-154">下表介紹不需依賴 [資料庫鏡像監視器]，即可獨立用於管理並使用資料庫鏡像監視作業的預存程序。</span><span class="sxs-lookup"><span data-stu-id="cc27c-154">The following table introduces the stored procedures for managing and using database mirroring monitoring independently of the Database Mirroring Monitor.</span></span>  
  
    |<span data-ttu-id="cc27c-155">程序</span><span class="sxs-lookup"><span data-stu-id="cc27c-155">Procedure</span></span>|<span data-ttu-id="cc27c-156">描述</span><span class="sxs-lookup"><span data-stu-id="cc27c-156">Description</span></span>|  
    |---------------|-----------------|  
    |[<span data-ttu-id="cc27c-157">sp_dbmmonitoraddmonitoring</span><span class="sxs-lookup"><span data-stu-id="cc27c-157">sp_dbmmonitoraddmonitoring</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitoraddmonitoring-transact-sql)|<span data-ttu-id="cc27c-158">建立一項作業，以便定期更新伺服器執行個體上每個鏡像資料庫的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="cc27c-158">Creates a job that periodically updates the status information for every mirrored database on the server instance.</span></span>|  
    |[<span data-ttu-id="cc27c-159">sp_dbmmonitorchangemonitoring</span><span class="sxs-lookup"><span data-stu-id="cc27c-159">sp_dbmmonitorchangemonitoring</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql)|<span data-ttu-id="cc27c-160">變更資料庫鏡像監視參數的值。</span><span class="sxs-lookup"><span data-stu-id="cc27c-160">Changes the value of a database mirroring monitoring parameter.</span></span>|  
    |[<span data-ttu-id="cc27c-161">sp_dbmmonitorhelpmonitoring</span><span class="sxs-lookup"><span data-stu-id="cc27c-161">sp_dbmmonitorhelpmonitoring</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql)|<span data-ttu-id="cc27c-162">傳回目前的更新週期。</span><span class="sxs-lookup"><span data-stu-id="cc27c-162">Returns the current update period.</span></span>|  
    |[<span data-ttu-id="cc27c-163">sp_dbmmonitorresults</span><span class="sxs-lookup"><span data-stu-id="cc27c-163">sp_dbmmonitorresults</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql)|<span data-ttu-id="cc27c-164">傳回監視資料庫的狀態資料列，並且讓您選擇是否要讓此程序事先取得最新狀態。</span><span class="sxs-lookup"><span data-stu-id="cc27c-164">Returns status rows for a monitored database and allows you to choose whether the procedure obtains the latest status beforehand.</span></span>|  
    |[<span data-ttu-id="cc27c-165">sp_dbmmonitordropmonitoring</span><span class="sxs-lookup"><span data-stu-id="cc27c-165">sp_dbmmonitordropmonitoring</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql)|<span data-ttu-id="cc27c-166">停止並刪除伺服器執行個體上所有資料庫的鏡像監視器作業。</span><span class="sxs-lookup"><span data-stu-id="cc27c-166">Stops and deletes the mirroring monitor job for all the databases on the server instance.</span></span>|  
  
     <span data-ttu-id="cc27c-167">**dbmmonitor** 系統預存程序可當做 [資料庫鏡像監視器] 的輔助使用。</span><span class="sxs-lookup"><span data-stu-id="cc27c-167">The **dbmmonitor** system stored procedures can be used as an adjunct to the Database Mirroring Monitor.</span></span> <span data-ttu-id="cc27c-168">例如，即使監視作業是使用 **sp_dbmmonitoraddmonitoring**設定的，您還是可以使用「資料庫鏡像監視器」來檢視狀態。</span><span class="sxs-lookup"><span data-stu-id="cc27c-168">For example, even if monitoring was configured using **sp_dbmmonitoraddmonitoring**, Database Mirroring Monitor can be used to view the status.</span></span>  
  
### <a name="how-monitoring-works"></a><span data-ttu-id="cc27c-169">監視的運作方式</span><span class="sxs-lookup"><span data-stu-id="cc27c-169">How Monitoring Works</span></span>  
 <span data-ttu-id="cc27c-170">本節將介紹資料庫鏡像狀態資料表、資料庫鏡像監視器作業和監視器、使用者如何監視資料庫鏡像狀態，以及如何卸除監視作業。</span><span class="sxs-lookup"><span data-stu-id="cc27c-170">This section introduces the database mirroring status table, database mirroring monitor job and the monitor, how users can monitor database mirroring status, and how the monitoring job can be dropped.</span></span>  
  
#### <a name="database-mirroring-status-table"></a><span data-ttu-id="cc27c-171">資料庫鏡像狀態資料表</span><span class="sxs-lookup"><span data-stu-id="cc27c-171">Database Mirroring Status Table</span></span>  
 <span data-ttu-id="cc27c-172">資料庫鏡像狀態會儲存在 **msdb** 資料庫之內部且未記載的資料庫鏡像狀態資料表中。</span><span class="sxs-lookup"><span data-stu-id="cc27c-172">Database mirroring status is stored in an internal, undocumented database mirroring status table in the **msdb** database.</span></span> <span data-ttu-id="cc27c-173">首次在伺服器執行個體上更新鏡像狀態時，就會自動建立此狀態資料表。</span><span class="sxs-lookup"><span data-stu-id="cc27c-173">This status table is automatically created the first time the mirroring status is updated on the server instance.</span></span>  
  
 <span data-ttu-id="cc27c-174">系統管理員可以自動或手動更新狀態資料表，而且最小更新間隔為 15 秒。</span><span class="sxs-lookup"><span data-stu-id="cc27c-174">The status table may be updated either automatically or manually by a system administrator, with a minimum update interval of 15 seconds.</span></span> <span data-ttu-id="cc27c-175">15 秒的下限可防止伺服器執行個體因狀態要求而超過負載。</span><span class="sxs-lookup"><span data-stu-id="cc27c-175">The 15 second minimum prevents server instances from being overloaded with status requests.</span></span>  
  
 <span data-ttu-id="cc27c-176">此狀態資料表會自動由 [資料庫鏡像監視器] 和資料庫鏡像監視器作業更新 (如果有執行的話)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-176">The status table is updated automatically by both Database Mirroring Monitor and the database mirroring monitor job, if running.</span></span> <span data-ttu-id="cc27c-177">[資料庫鏡像監視器作業] 預設會每分鐘更新資料表一次 (系統管理員可以指定介於 1 至 120 分鐘的更新週期)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-177">**Database Mirroring Monitor Job** updates the table once a minute by default (a system administrator can specify an update period of 1 to 120 minutes).</span></span> <span data-ttu-id="cc27c-178">不過，[資料庫鏡像監視器] 則會每隔 30 秒自動更新資料表。</span><span class="sxs-lookup"><span data-stu-id="cc27c-178">Database Mirroring Monitor, in contrast, updates the table automatically every 30 seconds.</span></span> <span data-ttu-id="cc27c-179">進行這些更新作業時，[資料庫鏡像監視器作業]  和「資料庫鏡像監視器」都會呼叫 **sp_dbmmonitorupdate**。</span><span class="sxs-lookup"><span data-stu-id="cc27c-179">For these updates, **Database Mirroring Monitor Job** and Database Mirroring Monitor call **sp_dbmmonitorupdate**.</span></span>  
  
 <span data-ttu-id="cc27c-180">**sp_dbmmonitorupdate** 初次執行時，會建立 **資料庫鏡像狀態** 資料表，並在 **msdb** 資料庫中建立 **dbm_monitor** 固定資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="cc27c-180">The first time **sp_dbmmonitorupdate** runs, it creates the **database mirroring status** table and the **dbm_monitor** fixed database role in the **msdb** database.</span></span> <span data-ttu-id="cc27c-181">**sp_dbmmonitorupdate** 通常會針對伺服器執行個體上每個鏡像資料庫的狀態資料表插入新資料列，以更新鏡像狀態；如需詳細資訊，請參閱本主題稍後的＜資料庫鏡像狀態資料表＞。</span><span class="sxs-lookup"><span data-stu-id="cc27c-181">**sp_dbmmonitorupdate** usually updates the mirroring status by inserting a new row into the status table for every mirrored database on the server instance; for more information, see "Database Mirroring Status Table," later in this topic.</span></span> <span data-ttu-id="cc27c-182">這個程序也會評估新資料列中的效能標準，並截斷晚於目前保留期限 (預設為 7 天) 的資料列。</span><span class="sxs-lookup"><span data-stu-id="cc27c-182">This procedure also evaluates the performance metrics in the new rows and truncates rows older than the current retention period (the default is 7 days).</span></span> <span data-ttu-id="cc27c-183">如需詳細資訊，請參閱 [sp_dbmmonitorupdate &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorupdate-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-183">For more information, see [sp_dbmmonitorupdate &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorupdate-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cc27c-184">除非「資料庫鏡像監視器」目前正由**系統管理員**固定伺服器角色的成員使用，否則只有當 **[資料庫鏡像監視器作業]** 存在且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 執行時，才會自動更新狀態資料表。</span><span class="sxs-lookup"><span data-stu-id="cc27c-184">Unless Database Mirroring Monitor is currently being used by a member of the **sysadmin** fixed server role, the status table is automatically updated only if the **Database Mirroring Monitor Job** exists and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is running.</span></span>  
  
#### <a name="database-mirroring-monitor-job"></a><span data-ttu-id="cc27c-185">資料庫鏡像監視器作業</span><span class="sxs-lookup"><span data-stu-id="cc27c-185">Database Mirroring Monitor Job</span></span>  
 <span data-ttu-id="cc27c-186">資料庫鏡像監視作業 **[資料庫鏡像監視器作業]** 是獨立於 [資料庫鏡像監視器] 運作的。</span><span class="sxs-lookup"><span data-stu-id="cc27c-186">The database mirroring monitoring job, **Database Mirroring Monitor Job**, operates independently of Database Mirroring Monitor.</span></span> <span data-ttu-id="cc27c-187">只有當**是用來啟動鏡像工作階段時，才會自動建立** [資料庫鏡像監視器作業] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cc27c-187">**Database Mirroring Monitor Job** is created automatically only if [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is used to start a mirroring session.</span></span> <span data-ttu-id="cc27c-188">如果一律使用 ALTER DATABASE *資料庫名稱* SET PARTNER 命令來啟動鏡像，則只有當系統管理員執行 **sp_dbmmonitoraddmonitoring** 預存程序時，此作業才會存在。</span><span class="sxs-lookup"><span data-stu-id="cc27c-188">If ALTER DATABASE *database_name* SET PARTNER commands are always used to start mirroring, the job exists only if the system administrator runs the **sp_dbmmonitoraddmonitoring** stored procedure.</span></span>  
  
 <span data-ttu-id="cc27c-189">建立 **[資料庫鏡像監視器作業]** 之後，假設 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 正在執行，則預設會每分鐘呼叫此作業一次。</span><span class="sxs-lookup"><span data-stu-id="cc27c-189">After **Database Mirroring Monitor Job** is created, assuming that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is running, the job is called once a minute, by default.</span></span> <span data-ttu-id="cc27c-190">然後，此作業就會呼叫 **sp_dbmmonitorupdate** 系統預存程序。</span><span class="sxs-lookup"><span data-stu-id="cc27c-190">The job then calls the **sp_dbmmonitorupdate** system stored procedure.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cc27c-191">Agent 預設會每分鐘呼叫 [資料庫鏡像監視器作業]  一次，而且此作業會呼叫 **sp_dbmmonitorupdate** 來更新狀態資料表。</span><span class="sxs-lookup"><span data-stu-id="cc27c-191">Agent calls **Database Mirroring Monitor Job** once a minute, by default, and the job calls **sp_dbmmonitorupdate** to update the status table.</span></span> <span data-ttu-id="cc27c-192">系統管理員可以使用 **sp_dbmmonitorchangemonitoring** 系統預存程序來變更更新週期，而且可以使用 **sp_dbmmonitorchangemonitoring** 系統預存程序來檢視目前的更新週期。</span><span class="sxs-lookup"><span data-stu-id="cc27c-192">System administrators can change the update period by using the **sp_dbmmonitorchangemonitoring** system stored procedure, and they can view the current update period by using the **sp_dbmmonitorchangemonitoring** system stored procedure.</span></span> <span data-ttu-id="cc27c-193">如需詳細資訊，請參閱 [sp_dbmmonitoraddmonitoring &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbmmonitoraddmonitoring-transact-sql) 和 [sp_dbmmonitorchangemonitoring &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-193">For more information, see [sp_dbmmonitoraddmonitoring &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbmmonitoraddmonitoring-transact-sql) and [sp_dbmmonitorchangemonitoring &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql).</span></span>  
  
#### <a name="monitoring-database-mirroring-status-by-system-administrators"></a><span data-ttu-id="cc27c-194">監視資料庫鏡像狀態 (系統管理員)</span><span class="sxs-lookup"><span data-stu-id="cc27c-194">Monitoring Database Mirroring Status (by System Administrators)</span></span>  
 <span data-ttu-id="cc27c-195">**sysadmin** 固定伺服器角色的成員可以檢視並更新狀態資料表。</span><span class="sxs-lookup"><span data-stu-id="cc27c-195">Members of the **sysadmin** fixed server role can view and update the status table</span></span>  
  
-   <span data-ttu-id="cc27c-196">使用資料庫鏡像監視器</span><span class="sxs-lookup"><span data-stu-id="cc27c-196">Using Database Mirroring Monitor</span></span>  
  
     <span data-ttu-id="cc27c-197">使用 [資料庫鏡像監視器] 時，系統管理員就可以手動重新整理 **[狀態]** 頁面、巡覽樹狀目錄或 **[記錄]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="cc27c-197">When using Database Mirroring Monitor, a system administrator can manually refresh the **Status** page, navigation tree, or **History** page.</span></span> <span data-ttu-id="cc27c-198">而且，除非已經在前 15 秒內更新過，否則它也會更新狀態資料表。</span><span class="sxs-lookup"><span data-stu-id="cc27c-198">This also updates the status table, unless it has already been updated within the previous 15 seconds.</span></span>  
  
     <span data-ttu-id="cc27c-199">若要檢視指定伺服器執行個體上的鏡像狀態記錄，系統管理員也可以按一下伺服器執行個體的 [記錄]  按鈕 (在 [狀態]  頁面上)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-199">To view the history of mirroring status on a given server instance, the system administrator can also click the **History** button for a server instance (on the **Status** page).</span></span> <span data-ttu-id="cc27c-200">然後，記錄就會顯示在 **[資料庫鏡像記錄]** 對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="cc27c-200">The history is displayed in the **Database Mirroring History** dialog box.</span></span> <span data-ttu-id="cc27c-201">系統管理員可以在此對話方塊中檢視伺服器執行個體之狀態資料表中的某些或所有資料列。</span><span class="sxs-lookup"><span data-stu-id="cc27c-201">There, the system administrator can view some or all of the rows in the status table of the server instance.</span></span>  
  
     <span data-ttu-id="cc27c-202">如需 **[狀態]** 頁面標準的詳細資訊，請參閱本主題稍後的「資料庫鏡像監視器顯示的效能標準」。</span><span class="sxs-lookup"><span data-stu-id="cc27c-202">For information about the **Status** page metrics, see Performance Metrics Displayed by the "Database Mirroring Monitor," later in this topic.</span></span>  
  
-   <span data-ttu-id="cc27c-203">使用 **sp_dbmmonitorresults**</span><span class="sxs-lookup"><span data-stu-id="cc27c-203">Using **sp_dbmmonitorresults**</span></span>  
  
     <span data-ttu-id="cc27c-204">系統管理員可以使用 **sp_dbmmonitorresults** 系統預存程序來檢視並選擇性地更新狀態資料表 (如果在前 15 秒內未更新過的話)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-204">System administrators can use the **sp_dbmmonitorresults** system stored procedure to view and, optionally, to update the status table, if it has not been updated within the previous 15 seconds.</span></span> <span data-ttu-id="cc27c-205">此程序會呼叫 **sp_dbmmonitorupdate** 程序並根據程序呼叫中要求的數量，傳回一個或多個記錄資料列。</span><span class="sxs-lookup"><span data-stu-id="cc27c-205">This procedure calls the **sp_dbmmonitorupdate** procedure and returns one or more history rows, depending on the amount requested in the procedure call.</span></span> <span data-ttu-id="cc27c-206">如需結果集中狀態的資訊，請參閱 [sp_dbmmonitorresults &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-206">For information about the status in its results set, see [sp_dbmmonitorresults &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql).</span></span>  
  
#### <a name="monitoring-database-mirroring-status-by-dbm_monitor-members"></a><span data-ttu-id="cc27c-207">監視資料庫鏡像狀態 (dbm_monitor 成員)</span><span class="sxs-lookup"><span data-stu-id="cc27c-207">Monitoring Database Mirroring Status (by dbm_monitor Members)</span></span>  
 <span data-ttu-id="cc27c-208">如上所述，首次執行 **sp_dbmmonitorupdate** 時，它會在 **msdb** 資料庫中建立 **dbm_monitor** 固定資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="cc27c-208">As mentioned, the first time **sp_dbmmonitorupdate** runs, it creates the **dbm_monitor** fixed database role in the **msdb** database.</span></span> <span data-ttu-id="cc27c-209">**dbm_monitor** 固定資料庫角色的成員可以使用「資料庫鏡像監視器」或 **sp_dbmmonitorresults** 預存程序，檢視現有的鏡像狀態。</span><span class="sxs-lookup"><span data-stu-id="cc27c-209">Members of the **dbm_monitor** fixed database role can view the existing mirroring status by using either Database Mirroring Monitor or the **sp_dbmmonitorresults** stored procedure.</span></span> <span data-ttu-id="cc27c-210">但是這些使用者無法更新狀態資料表。</span><span class="sxs-lookup"><span data-stu-id="cc27c-210">But these users cannot update the status table.</span></span> <span data-ttu-id="cc27c-211">若要瞭解顯示狀態的存在時間，使用者可以在 [**狀態**] 頁面上查看 [主體記錄檔 (中的時間\*\* ***\<time>***) **和 [**鏡像記錄] (***\<time>***) \*\*標籤。</span><span class="sxs-lookup"><span data-stu-id="cc27c-211">To learn the age of the displayed status a user can look at the times in the **Principal log (***\<time>***)** and **Mirror log (***\<time>***)** labels on the **Status** page.</span></span>  
  
 <span data-ttu-id="cc27c-212">**dbm_monitor** 固定資料庫角色的成員會仰賴 [資料庫鏡像監視器作業]  來定期更新狀態資料表。</span><span class="sxs-lookup"><span data-stu-id="cc27c-212">Members of the **dbm_monitor** fixed database role depend on the **Database Mirroring Monitor Job** to update the status table at regular intervals.</span></span> <span data-ttu-id="cc27c-213">如果此作業不存在或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 已停止，狀態就會逐漸成為過時，而且不再反映鏡像工作階段的組態。</span><span class="sxs-lookup"><span data-stu-id="cc27c-213">If the job does not exist or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is stopped, the status becomes increasingly stale and may no longer reflect the configuration of the mirroring session.</span></span> <span data-ttu-id="cc27c-214">例如，在容錯移轉之後，夥伴可能看起來像是共用相同的角色 (主體或鏡像)，或者目前的主體伺服器可能會顯示為鏡像，而目前的鏡像伺服器則顯示為主體。</span><span class="sxs-lookup"><span data-stu-id="cc27c-214">For example, after a failover, the partners might appear to share the same role-principal or mirror, or the current principal server might be shown as the mirror, while the current mirror server is shown as the principal.</span></span>  
  
#### <a name="dropping-the-database-mirroring-monitor-job"></a><span data-ttu-id="cc27c-215">卸除資料庫鏡像監視器作業</span><span class="sxs-lookup"><span data-stu-id="cc27c-215">Dropping the Database Mirroring Monitor Job</span></span>  
 <span data-ttu-id="cc27c-216">資料庫鏡像監視器作業 **[資料庫鏡像監視器作業]** 會維持到卸除為止。</span><span class="sxs-lookup"><span data-stu-id="cc27c-216">The database mirroring monitor job, **Database Mirroring Monitor Job**, remains until it is dropped.</span></span> <span data-ttu-id="cc27c-217">此監視作業必須由系統管理員管理。</span><span class="sxs-lookup"><span data-stu-id="cc27c-217">The monitoring job must be managed by the system administrator.</span></span> <span data-ttu-id="cc27c-218">若要卸除 [資料庫鏡像監視器作業] ，請使用 **sp_dbmmonitordropmonitoring**。</span><span class="sxs-lookup"><span data-stu-id="cc27c-218">To drop **Database Mirroring Monitor Job**, use **sp_dbmmonitordropmonitoring**.</span></span> <span data-ttu-id="cc27c-219">如需詳細資訊，請參閱 [sp_dbmmonitordropmonitoring &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-219">For more information, see [sp_dbmmonitordropmonitoring &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql).</span></span>  
  
###  <a name="status-displayed-by-the-database-mirroring-monitor"></a><a name="perf_metrics_of_dbm_monitor"></a> <span data-ttu-id="cc27c-220">資料庫鏡像監視器顯示的狀態</span><span class="sxs-lookup"><span data-stu-id="cc27c-220">Status Displayed by the Database Mirroring Monitor</span></span>  
 <span data-ttu-id="cc27c-221">[資料庫鏡像監視器] 的 **[狀態]** 頁面會描述夥伴，還有鏡像工作階段的狀態。</span><span class="sxs-lookup"><span data-stu-id="cc27c-221">The **Status** page of the Database Mirroring Monitor describes the partners, and also the state of the mirroring session.</span></span> <span data-ttu-id="cc27c-222">狀態會包括效能標準，如交易記錄狀態和其他資訊，目的是要在工作階段沒有同步時，協助您估計目前完成容錯移轉所需的時間以及遺失資料的可能性。</span><span class="sxs-lookup"><span data-stu-id="cc27c-222">The status includes performance metrics such as the state of the transaction log and other information that is intended to help currently estimate the time required to complete a failover and the potential of data loss, if the session is not synchronized.</span></span> <span data-ttu-id="cc27c-223">此外， **[狀態]** 頁面還會顯示鏡像工作階段的一般狀態和相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cc27c-223">In addition, the **Status** page displays status and information about the mirroring session in general.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cc27c-224">如需「資料庫鏡像監視器」和 [狀態]  頁面的簡介，請參閱本主題稍早的 [監視資料庫鏡像狀態的工具](#tools_for_monitoring_dbm_status)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-224">For an introduction to the Database Mirroring Monitor and **Status** page, see [Tools for Monitoring Database Mirroring Status](#tools_for_monitoring_dbm_status), earlier in this topic.</span></span>  
  
 <span data-ttu-id="cc27c-225">針對這其中每一項提供的資料都摘要在下列章節中。</span><span class="sxs-lookup"><span data-stu-id="cc27c-225">The information provided for each of these is summarized in the following sections.</span></span>  
  
#### <a name="partners"></a><span data-ttu-id="cc27c-226">合作夥伴</span><span class="sxs-lookup"><span data-stu-id="cc27c-226">Partners</span></span>  
 <span data-ttu-id="cc27c-227">**[狀態]** 頁面會顯示每個夥伴的下列資訊：</span><span class="sxs-lookup"><span data-stu-id="cc27c-227">The **Status** page displays the following information for each of the partners:</span></span>  
  
-   <span data-ttu-id="cc27c-228">伺服器執行個體</span><span class="sxs-lookup"><span data-stu-id="cc27c-228">Server instance</span></span>  
  
     <span data-ttu-id="cc27c-229">其狀態顯示在 **[狀態]** 資料列中的伺服器執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="cc27c-229">Name of the server instance whose status is displayed in the **Status** row.</span></span>  
  
-   <span data-ttu-id="cc27c-230">目前的角色</span><span class="sxs-lookup"><span data-stu-id="cc27c-230">Current role</span></span>  
  
     <span data-ttu-id="cc27c-231">伺服器執行個體的目前角色。</span><span class="sxs-lookup"><span data-stu-id="cc27c-231">Current role of the server instance.</span></span> <span data-ttu-id="cc27c-232">可能的狀態為：</span><span class="sxs-lookup"><span data-stu-id="cc27c-232">The possible states are:</span></span>  
  
    -   <span data-ttu-id="cc27c-233">主體</span><span class="sxs-lookup"><span data-stu-id="cc27c-233">Principal</span></span>  
  
    -   <span data-ttu-id="cc27c-234">鏡像</span><span class="sxs-lookup"><span data-stu-id="cc27c-234">Mirror</span></span>  
  
-   <span data-ttu-id="cc27c-235">鏡像狀態</span><span class="sxs-lookup"><span data-stu-id="cc27c-235">Mirroring state</span></span>  
  
     <span data-ttu-id="cc27c-236">可能的狀態為：</span><span class="sxs-lookup"><span data-stu-id="cc27c-236">The possible states are:</span></span>  
  
    -   <span data-ttu-id="cc27c-237">Unknown</span><span class="sxs-lookup"><span data-stu-id="cc27c-237">Unknown</span></span>  
  
    -   <span data-ttu-id="cc27c-238">正在同步處理</span><span class="sxs-lookup"><span data-stu-id="cc27c-238">Synchronizing</span></span>  
  
    -   <span data-ttu-id="cc27c-239">已同步處理</span><span class="sxs-lookup"><span data-stu-id="cc27c-239">Synchronized</span></span>  
  
    -   <span data-ttu-id="cc27c-240">暫止</span><span class="sxs-lookup"><span data-stu-id="cc27c-240">Suspended</span></span>  
  
    -   <span data-ttu-id="cc27c-241">已中斷連接</span><span class="sxs-lookup"><span data-stu-id="cc27c-241">Disconnected</span></span>  
  
-   <span data-ttu-id="cc27c-242">見證連接</span><span class="sxs-lookup"><span data-stu-id="cc27c-242">Witness connection</span></span>  
  
     <span data-ttu-id="cc27c-243">見證的連接狀態。</span><span class="sxs-lookup"><span data-stu-id="cc27c-243">Connection status of the witness.</span></span> <span data-ttu-id="cc27c-244">可能的狀態為：</span><span class="sxs-lookup"><span data-stu-id="cc27c-244">The possible states are:</span></span>  
  
    -   <span data-ttu-id="cc27c-245">Unknown</span><span class="sxs-lookup"><span data-stu-id="cc27c-245">Unknown</span></span>  
  
    -   <span data-ttu-id="cc27c-246">連線</span><span class="sxs-lookup"><span data-stu-id="cc27c-246">Connected</span></span>  
  
    -   <span data-ttu-id="cc27c-247">已中斷連接</span><span class="sxs-lookup"><span data-stu-id="cc27c-247">Disconnected.</span></span>  
  
#### <a name="log-on-the-principal-server"></a><span data-ttu-id="cc27c-248">主體伺服器上的記錄</span><span class="sxs-lookup"><span data-stu-id="cc27c-248">Log on the Principal Server</span></span>  
 <span data-ttu-id="cc27c-249">**[狀態]** 頁面會根據指定的時間，顯示下列有關主體伺服器之記錄狀態的資訊：</span><span class="sxs-lookup"><span data-stu-id="cc27c-249">The **Status** page displays the following information about the status of the log on the principal server as of the indicated time:</span></span>  
  
-   <span data-ttu-id="cc27c-250">未傳送的記錄</span><span class="sxs-lookup"><span data-stu-id="cc27c-250">Unsent log</span></span>  
  
     <span data-ttu-id="cc27c-251">在傳送佇列中等候的記錄量 (以 KB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-251">The amount of log waiting in the send queue in kilobytes (KB).</span></span>  
  
-   <span data-ttu-id="cc27c-252">最舊尚未傳送的交易</span><span class="sxs-lookup"><span data-stu-id="cc27c-252">Oldest unsent transaction</span></span>  
  
     <span data-ttu-id="cc27c-253">傳送佇列中最舊尚未傳送之交易的存在時間。</span><span class="sxs-lookup"><span data-stu-id="cc27c-253">Age of the oldest unsent transaction in the send queue.</span></span> <span data-ttu-id="cc27c-254">這項交易的存在時間會指出尚未傳送到鏡像伺服器執行個體的交易分鐘數。</span><span class="sxs-lookup"><span data-stu-id="cc27c-254">The age of this transaction indicates how many minutes of transactions have not yet been sent to the mirror server instance.</span></span> <span data-ttu-id="cc27c-255">這個值有助於從時間方面來測量資料遺失的可能性。</span><span class="sxs-lookup"><span data-stu-id="cc27c-255">This value helps measure the potential for data loss in terms of time.</span></span>  
  
-   <span data-ttu-id="cc27c-256">傳送記錄的時間 (估計)</span><span class="sxs-lookup"><span data-stu-id="cc27c-256">Time to send log (estimated)</span></span>  
  
     <span data-ttu-id="cc27c-257">根據目前的傳送速率，主體伺服器執行個體將目前位於傳送佇列中的記錄傳送至鏡像伺服器執行個體所需的估計分鐘數。</span><span class="sxs-lookup"><span data-stu-id="cc27c-257">Estimated number of minutes the principal server instance requires to send the log that is currently in the send queue to the mirror server instance based on the current send rate.</span></span> <span data-ttu-id="cc27c-258">傳送記錄的實際時間將會受到內送交易的速率影響，所以可能會有很大的差異。</span><span class="sxs-lookup"><span data-stu-id="cc27c-258">The actual time to send the log will be affected by the rate of incoming transactions, which can vary significantly.</span></span> <span data-ttu-id="cc27c-259">不過，在概略估計手動容錯移轉所需的時間時，[傳送記錄的時間 (估計)]  值非常有用。</span><span class="sxs-lookup"><span data-stu-id="cc27c-259">However, the **Time to send log (estimated)** value can be useful for roughly estimating the time required for a manual failover.</span></span>  
  
-   <span data-ttu-id="cc27c-260">目前的傳送速率</span><span class="sxs-lookup"><span data-stu-id="cc27c-260">Current send rate</span></span>  
  
     <span data-ttu-id="cc27c-261">將交易傳送至鏡像伺服器執行個體的速率 (以每秒 KB 數為單位)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-261">Rate at which transactions are being sent to the mirror server instance in KB per second.</span></span>  
  
-   <span data-ttu-id="cc27c-262">新交易的目前速率</span><span class="sxs-lookup"><span data-stu-id="cc27c-262">Current rate of new transactions</span></span>  
  
     <span data-ttu-id="cc27c-263">將內送交易輸入到主體記錄中的速率 (以每秒 KB 數為單位)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-263">Rate at which incoming transactions are being entered into the principal's log in KB per second.</span></span> <span data-ttu-id="cc27c-264">若要判斷鏡像是落後、超前，還是趕上進度，請將這個值與 **[傳送記錄的時間 (估計)]** 值加以比較。</span><span class="sxs-lookup"><span data-stu-id="cc27c-264">To determine whether mirroring is falling behind, staying up, or catching up, compare this value to the **Estimated time to send log** value.</span></span>  
  
#### <a name="log-on-the-mirror-server"></a><span data-ttu-id="cc27c-265">鏡像伺服器上的記錄</span><span class="sxs-lookup"><span data-stu-id="cc27c-265">Log on the Mirror Server</span></span>  
 <span data-ttu-id="cc27c-266">**[狀態]** 頁面會根據指定的時間，顯示下列有關鏡像伺服器之記錄狀態的資訊：</span><span class="sxs-lookup"><span data-stu-id="cc27c-266">The **Status** page displays the following information about the status of the log on the mirror server as of the indicated time:</span></span>  
  
-   <span data-ttu-id="cc27c-267">未還原的記錄</span><span class="sxs-lookup"><span data-stu-id="cc27c-267">Unrestored log</span></span>  
  
     <span data-ttu-id="cc27c-268">在重做佇列中等候的記錄量 (以 KB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-268">The amount of log waiting in the redo queue in KB.</span></span>  
  
-   <span data-ttu-id="cc27c-269">還原記錄的時間 (估計)</span><span class="sxs-lookup"><span data-stu-id="cc27c-269">Time to restore log (estimated)</span></span>  
  
     <span data-ttu-id="cc27c-270">將目前在重做佇列中的記錄套用至鏡像資料庫所需的大約分鐘數。</span><span class="sxs-lookup"><span data-stu-id="cc27c-270">Approximate number of minutes required for the log currently in the redo queue to be applied to the mirror database.</span></span>  
  
-   <span data-ttu-id="cc27c-271">目前的還原速率</span><span class="sxs-lookup"><span data-stu-id="cc27c-271">Current restore rate</span></span>  
  
     <span data-ttu-id="cc27c-272">將交易還原到鏡像資料庫中的速率 (以每秒 KB 數為單位)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-272">Rate at which transactions are being restored into the mirror database (in KB per second).</span></span>  
  
#### <a name="mirroring-session"></a><span data-ttu-id="cc27c-273">鏡像工作階段</span><span class="sxs-lookup"><span data-stu-id="cc27c-273">Mirroring Session</span></span>  
 <span data-ttu-id="cc27c-274">此外， **[狀態]** 頁面還會顯示下列與鏡像工作階段相關的資訊：</span><span class="sxs-lookup"><span data-stu-id="cc27c-274">In addition, the **Status** page displays the following information about the mirroring session:</span></span>  
  
-   <span data-ttu-id="cc27c-275">鏡像認可負擔</span><span class="sxs-lookup"><span data-stu-id="cc27c-275">Mirroring commit overhead</span></span>  
  
     <span data-ttu-id="cc27c-276">每筆交易的平均延遲時間 (以毫秒為單位) (僅適用於高安全性模式)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-276">Average delay per transaction in milliseconds (relevant only in high-safety mode).</span></span> <span data-ttu-id="cc27c-277">這項延遲是當主體伺服器執行個體等待鏡像伺服器執行個體將交易記錄寫入重做佇列中時所產生的負擔量。</span><span class="sxs-lookup"><span data-stu-id="cc27c-277">This delay is the amount of overhead incurred while the principal server instance waits for the mirror server instance to write the transaction's log record into the redo queue.</span></span>  
  
-   <span data-ttu-id="cc27c-278">傳送與還原所有目前記錄的時間 (估計)</span><span class="sxs-lookup"><span data-stu-id="cc27c-278">Time to send and restore all current log (estimated)</span></span>  
  
     <span data-ttu-id="cc27c-279">傳送主體上已經認可的所有未傳送記錄並還原目前位於重做佇列中的所有記錄所需的估計時間。</span><span class="sxs-lookup"><span data-stu-id="cc27c-279">Estimated time needed to send all of the unsent log that has been committed at the principal and to restore all of the log currently in the redo queue.</span></span> <span data-ttu-id="cc27c-280">此估計時間可能會比 [傳送記錄的時間 (估計)]  和 [還原記錄的時間 (估計)]  欄位值的總和要少，因為傳送和還原可以平行運作。</span><span class="sxs-lookup"><span data-stu-id="cc27c-280">This estimate may be less than the sum of the values of the **Time to send log (estimated)** and **Time to restore log (estimated)** fields, because sending and restoring can operate in parallel.</span></span>  
  
-   <span data-ttu-id="cc27c-281">見證位址</span><span class="sxs-lookup"><span data-stu-id="cc27c-281">Witness address</span></span>  
  
     <span data-ttu-id="cc27c-282">見證伺服器執行個體的網路位址。</span><span class="sxs-lookup"><span data-stu-id="cc27c-282">Network address of the witness server instance.</span></span> <span data-ttu-id="cc27c-283">如需此位址格式的資訊，請參閱[指定伺服器網路位址 &#40;資料庫鏡像&#41;](specify-a-server-network-address-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-283">For information about the format of this address, see [Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md).</span></span>  
  
-   <span data-ttu-id="cc27c-284">作業模式</span><span class="sxs-lookup"><span data-stu-id="cc27c-284">Operating mode</span></span>  
  
     <span data-ttu-id="cc27c-285">資料庫鏡像工作階段的作業模式：</span><span class="sxs-lookup"><span data-stu-id="cc27c-285">The operating mode of the database mirroring session:</span></span>  
  
    -   <span data-ttu-id="cc27c-286">高效能 (非同步)</span><span class="sxs-lookup"><span data-stu-id="cc27c-286">High performance (asynchronous)</span></span>  
  
    -   <span data-ttu-id="cc27c-287">不具有自動容錯移轉的高安全性 (同步)</span><span class="sxs-lookup"><span data-stu-id="cc27c-287">High safety without automatic failover (synchronous)</span></span>  
  
    -   <span data-ttu-id="cc27c-288">具有自動容錯移轉的高安全性 (同步)</span><span class="sxs-lookup"><span data-stu-id="cc27c-288">High safety with automatic failover (synchronous)</span></span>  
  
##  <a name="additional-sources-of-information-about-a-mirrored-database"></a><a name="AdditionalSources"></a> <span data-ttu-id="cc27c-289">與鏡像資料庫相關的其他資訊來源</span><span class="sxs-lookup"><span data-stu-id="cc27c-289">Additional Sources of Information About a Mirrored Database</span></span>  
 <span data-ttu-id="cc27c-290">除了使用 [資料庫鏡像監視器] 和 dbmmonitor 預存程序來監視鏡像資料庫並設定監視效能變數的警示以外， [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 還提供目錄檢視、效能計數器及資料庫鏡像事件通知。</span><span class="sxs-lookup"><span data-stu-id="cc27c-290">In addition to using the Database Mirroring Monitor and dbmmonitor stored procedures to monitor a mirrored database and set up alerts on monitored performance variables, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] provides catalog views, performance counters, and event notifications for database mirroring.</span></span>  
  
 <span data-ttu-id="cc27c-291">**本節內容：**</span><span class="sxs-lookup"><span data-stu-id="cc27c-291">**In This Section:**</span></span>  
  
-   [<span data-ttu-id="cc27c-292">資料庫鏡像中繼資料</span><span class="sxs-lookup"><span data-stu-id="cc27c-292">Database Mirroring Metadata</span></span>](#DbmMetadata)  
  
-   [<span data-ttu-id="cc27c-293">資料庫鏡像效能計數器</span><span class="sxs-lookup"><span data-stu-id="cc27c-293">Database Mirroring Performance Counters</span></span>](#DbmPerfCounters)  
  
-   [<span data-ttu-id="cc27c-294">資料庫鏡像事件通知</span><span class="sxs-lookup"><span data-stu-id="cc27c-294">Database Mirroring Event Notifications</span></span>](#DbmEventNotif)  
  
###  <a name="database-mirroring-metadata"></a><a name="DbmMetadata"></a> <span data-ttu-id="cc27c-295">資料庫鏡像中繼資料</span><span class="sxs-lookup"><span data-stu-id="cc27c-295">Database Mirroring Metadata</span></span>  
 <span data-ttu-id="cc27c-296">每個資料庫鏡像工作階段都會在中繼資料中描述，並可透過下列目錄或動態管理檢視公開此中繼資料：</span><span class="sxs-lookup"><span data-stu-id="cc27c-296">Each database mirroring session is described in metadata that is exposed through the following catalog or dynamic management views:</span></span>  
  
-   <span data-ttu-id="cc27c-297">**sys.database_mirroring**</span><span class="sxs-lookup"><span data-stu-id="cc27c-297">**sys.database_mirroring**</span></span>  
  
     <span data-ttu-id="cc27c-298">這個檢視會顯示伺服器執行個體中，每個鏡像資料庫的資料庫鏡像中繼資料。</span><span class="sxs-lookup"><span data-stu-id="cc27c-298">This view displays the database mirroring metadata for each mirrored database in a server instance.</span></span> <span data-ttu-id="cc27c-299">如需詳細資訊，請參閱 [sys.database_mirroring &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-299">For more information, see [sys.database_mirroring &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql).</span></span>  
  
-   <span data-ttu-id="cc27c-300">**sys.database_mirroring_endpoints**</span><span class="sxs-lookup"><span data-stu-id="cc27c-300">**sys.database_mirroring_endpoints**</span></span>  
  
     <span data-ttu-id="cc27c-301">**Sys.database_mirroring_endpoints** 目錄檢視會顯示伺服器執行個體之資料庫鏡像端點的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cc27c-301">The **sys.database_mirroring_endpoints** catalog view displays information about the database mirroring endpoint of the server instance.</span></span> <span data-ttu-id="cc27c-302">如需詳細資訊，請參閱 [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-302">For more information, see [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql).</span></span>  
  
-   <span data-ttu-id="cc27c-303">**sys.database_mirroring_witnesses**</span><span class="sxs-lookup"><span data-stu-id="cc27c-303">**sys.database_mirroring_witnesses**</span></span>  
  
     <span data-ttu-id="cc27c-304">這個目錄檢視會針對伺服器執行個體是見證的每一個工作階段，顯示其資料庫鏡像中繼資料。</span><span class="sxs-lookup"><span data-stu-id="cc27c-304">This catalog view displays the database mirroring metadata for each session in which a server instance is the witness.</span></span> <span data-ttu-id="cc27c-305">如需詳細資訊，請參閱 [sys.database_mirroring_witnesses &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-305">For more information, see [sys.database_mirroring_witnesses &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses).</span></span>  
  
-   <span data-ttu-id="cc27c-306">**sys.dm_db_mirroring_connections**</span><span class="sxs-lookup"><span data-stu-id="cc27c-306">**sys.dm_db_mirroring_connections**</span></span>  
  
     <span data-ttu-id="cc27c-307">此動態管理檢視會針對每一個資料庫鏡像網路連接，傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="cc27c-307">This dynamic management view returns a row for each database mirroring network connection.</span></span>  
  
     <span data-ttu-id="cc27c-308">如需詳細資訊，請參閱 [sys.dm_db_mirroring_connections &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-connections)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-308">For more information, see [sys.dm_db_mirroring_connections &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-connections).</span></span>  
  
###  <a name="database-mirroring-performance-counters"></a><a name="DbmPerfCounters"></a> <span data-ttu-id="cc27c-309">資料庫鏡像效能計數器</span><span class="sxs-lookup"><span data-stu-id="cc27c-309">Database Mirroring Performance Counters</span></span>  
 <span data-ttu-id="cc27c-310">效能計數器可讓您監視資料庫鏡像效能。</span><span class="sxs-lookup"><span data-stu-id="cc27c-310">Performance counters let you monitor database mirroring performance.</span></span> <span data-ttu-id="cc27c-311">例如，您可以檢查 **[Transaction Delay]** 計數器，以查看資料庫鏡像是否影響主體伺服器的效能；您可以檢查 **[Redo Queue]** 與 **[Log Send Queue]** 計數器，以查看鏡像資料庫是否跟得上主體資料庫。</span><span class="sxs-lookup"><span data-stu-id="cc27c-311">For example, you can examine the **Transaction Delay** counter to see if database mirroring is impacting performance on the principal server, you can examine the **Redo Queue** and **Log Send Queue** counters to see how well the mirror database is keeping up with the principal database.</span></span> <span data-ttu-id="cc27c-312">您可以檢查 [Log Bytes Sent/sec]  計數器，以監視每秒傳送的記錄量。</span><span class="sxs-lookup"><span data-stu-id="cc27c-312">You can examine the **Log Bytes Sent/sec** counter to monitor the amount of log sent per second.</span></span>  
  
 <span data-ttu-id="cc27c-313">在每個夥伴的「效能監視器」中，都可在資料庫鏡像效能物件 (**SQLServer:Database Mirroring**) 中使用效能計數器。</span><span class="sxs-lookup"><span data-stu-id="cc27c-313">In Performance Monitor on either partner, performance counters are available in the database mirroring performance object (**SQLServer:Database Mirroring**).</span></span> <span data-ttu-id="cc27c-314">如需詳細資訊，請參閱 [SQL Server 的 Database Mirroring 物件](../../relational-databases/performance-monitor/sql-server-database-mirroring-object.md)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-314">For more information, see [SQL Server, Database Mirroring Object](../../relational-databases/performance-monitor/sql-server-database-mirroring-object.md).</span></span>  
  
 <span data-ttu-id="cc27c-315">**若要啟動效能監視器**</span><span class="sxs-lookup"><span data-stu-id="cc27c-315">**To start the performance monitor**</span></span>  
  
-   [<span data-ttu-id="cc27c-316">啟動系統監視器 &#40;Windows&#41;</span><span class="sxs-lookup"><span data-stu-id="cc27c-316">Start System Monitor &#40;Windows&#41;</span></span>](../../relational-databases/performance/start-system-monitor-windows.md)  
  
###  <a name="database-mirroring-event-notifications"></a><a name="DbmEventNotif"></a> <span data-ttu-id="cc27c-317">資料庫鏡像事件通知</span><span class="sxs-lookup"><span data-stu-id="cc27c-317">Database Mirroring Event Notifications</span></span>  
 <span data-ttu-id="cc27c-318">事件通知是特殊的資料庫物件類型。</span><span class="sxs-lookup"><span data-stu-id="cc27c-318">Event notifications are a special kind of database object.</span></span> <span data-ttu-id="cc27c-319">事件通知是為了回應各種 Transact-SQL 資料定義語言 (DDL) 陳述式和 SQL 追蹤事件而執行，並將伺服器和資料庫事件的相關資訊傳送給 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="cc27c-319">Event notifications execute in response to a variety of Transact-SQL data definition language (DDL) statements and SQL Trace events and send information about server and database events to a [!INCLUDE[ssSB](../../includes/sssb-md.md)] service.</span></span>  
  
 <span data-ttu-id="cc27c-320">下列事件可用於資料庫鏡像：</span><span class="sxs-lookup"><span data-stu-id="cc27c-320">The following events are available for database mirroring:</span></span>  
  
-   <span data-ttu-id="cc27c-321">**Database Mirroring State Change** 事件類別</span><span class="sxs-lookup"><span data-stu-id="cc27c-321">**Database Mirroring State Change** event class</span></span>  
  
     <span data-ttu-id="cc27c-322">這表示鏡像資料庫之鏡像狀態變更的時間。</span><span class="sxs-lookup"><span data-stu-id="cc27c-322">This indicates when the mirroring state of a mirrored database changes.</span></span> <span data-ttu-id="cc27c-323">如需詳細資訊，請參閱 [Database Mirroring State Change Event Class](../../relational-databases/event-classes/database-mirroring-state-change-event-class.md)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-323">For more information, see [Database Mirroring State Change Event Class](../../relational-databases/event-classes/database-mirroring-state-change-event-class.md).</span></span>  
  
-   <span data-ttu-id="cc27c-324">**Audit Database Mirroring Login** 事件類別</span><span class="sxs-lookup"><span data-stu-id="cc27c-324">**Audit Database Mirroring Login** event class</span></span>  
  
     <span data-ttu-id="cc27c-325">這會報告與資料庫鏡像傳輸安全性相關的稽核訊息。</span><span class="sxs-lookup"><span data-stu-id="cc27c-325">This reports audit messages related to database mirroring transport security.</span></span> <span data-ttu-id="cc27c-326">如需詳細資訊，請參閱 [Audit Database Mirroring Login Event Class](../../relational-databases/event-classes/audit-database-mirroring-login-event-class.md)。</span><span class="sxs-lookup"><span data-stu-id="cc27c-326">For more information, see [Audit Database Mirroring Login Event Class](../../relational-databases/event-classes/audit-database-mirroring-login-event-class.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="cc27c-327">相關工作</span><span class="sxs-lookup"><span data-stu-id="cc27c-327">Related Tasks</span></span>  
  
-   [<span data-ttu-id="cc27c-328">使用鏡像效能標準的警告臨界值與警示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cc27c-328">Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;</span></span>](use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
-   [<span data-ttu-id="cc27c-329">啟動資料庫鏡像監視器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="cc27c-329">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="cc27c-330">檢視鏡像資料庫的狀態 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="cc27c-330">View the State of a Mirrored Database &#40;SQL Server Management Studio&#41;</span></span>](view-the-state-of-a-mirrored-database-sql-server-management-studio.md)  
  
 <span data-ttu-id="cc27c-331">**預存程序**</span><span class="sxs-lookup"><span data-stu-id="cc27c-331">**Stored procedures**</span></span>  
  
-   [<span data-ttu-id="cc27c-332">sp_dbmmonitoraddmonitoring &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc27c-332">sp_dbmmonitoraddmonitoring &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitoraddmonitoring-transact-sql)  
  
-   [<span data-ttu-id="cc27c-333">sp_dbmmonitorchangealert &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc27c-333">sp_dbmmonitorchangealert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql)  
  
-   [<span data-ttu-id="cc27c-334">sp_dbmmonitorchangemonitoring &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc27c-334">sp_dbmmonitorchangemonitoring &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql)  
  
-   [<span data-ttu-id="cc27c-335">sp_dbmmonitordropalert &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc27c-335">sp_dbmmonitordropalert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitordropalert-transact-sql)  
  
-   [<span data-ttu-id="cc27c-336">sp_dbmmonitordropmonitoring &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc27c-336">sp_dbmmonitordropmonitoring &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql)  
  
-   [<span data-ttu-id="cc27c-337">sp_dbmmonitorhelpalert &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc27c-337">sp_dbmmonitorhelpalert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorhelpalert-transact-sql)  
  
-   [<span data-ttu-id="cc27c-338">sp_dbmmonitorhelpmonitoring &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc27c-338">sp_dbmmonitorhelpmonitoring &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql)  
  
-   [<span data-ttu-id="cc27c-339">sp_dbmmonitorresults &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc27c-339">sp_dbmmonitorresults &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql)  
  
-   [<span data-ttu-id="cc27c-340">sp_dbmmonitorupdate &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc27c-340">sp_dbmmonitorupdate &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorupdate-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="cc27c-341">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc27c-341">See Also</span></span>  
 <span data-ttu-id="cc27c-342">[資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cc27c-342">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="cc27c-343">伺服器事件的 WMI 提供者概念</span><span class="sxs-lookup"><span data-stu-id="cc27c-343">WMI Provider for Server Events Concepts</span></span>](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)  
  
  
