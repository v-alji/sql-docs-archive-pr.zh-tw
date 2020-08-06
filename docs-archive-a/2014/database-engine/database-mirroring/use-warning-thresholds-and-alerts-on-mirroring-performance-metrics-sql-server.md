---
title: 使用鏡像效能標準的警告臨界值和警示 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- monitoring database mirroring [SQL Server]
- thresholds [SQL Server]
- database mirroring [SQL Server], managing in SQL Server Management Studio
- alerts [SQL Server], database mirroring
- database mirroring [SQL Server], monitoring
- warnings [database mirroring]
ms.assetid: 8cdd1515-0bd7-4f8c-a7fc-a33b575e20f6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 908b234143bc7e2140fe1c98d85ba150ea69b28d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594675"
---
# <a name="use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server"></a><span data-ttu-id="fbb45-102">使用鏡像效能標準的警告臨界值與警示 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="fbb45-102">Use Warning Thresholds and Alerts on Mirroring Performance Metrics (SQL Server)</span></span>
  <span data-ttu-id="fbb45-103">此主題包含可針對資料庫鏡像設定和管理警告臨界值之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fbb45-103">This topic contains information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events for which warning thresholds can be configured and managed for database mirroring.</span></span> <span data-ttu-id="fbb45-104">您可以使用「資料庫鏡像監視器」或 **sp_dbmmonitorchangealert**、 **sp_dbmmonitorhelpalert**及 **sp_dbmmonitordropalert** 預存程序。</span><span class="sxs-lookup"><span data-stu-id="fbb45-104">You can use the  Database Mirroring Monitor or the **sp_dbmmonitorchangealert**, **sp_dbmmonitorhelpalert**, and **sp_dbmmonitordropalert** stored procedures.</span></span> <span data-ttu-id="fbb45-105">此主題也包含設定資料庫鏡像事件之警示的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fbb45-105">This topic also contains information about configuring alerts on database mirroring events.</span></span>  
  
 <span data-ttu-id="fbb45-106">建立鏡像資料庫的監視作業後，系統管理員就可以設定許多項關鍵效能標準的警告臨界值。</span><span class="sxs-lookup"><span data-stu-id="fbb45-106">After monitoring is established for a mirrored database, a system administrator can configure warning thresholds on several key performance metrics.</span></span> <span data-ttu-id="fbb45-107">此外，管理員還可以設定這些和其他資料庫鏡像事件的警示。</span><span class="sxs-lookup"><span data-stu-id="fbb45-107">Also, an administrator can configure alerts on these and other database mirroring events.</span></span>  
  
 <span data-ttu-id="fbb45-108">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="fbb45-108">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="fbb45-109">效能標準和警告臨界值</span><span class="sxs-lookup"><span data-stu-id="fbb45-109">Performance Metrics and Warning Thresholds</span></span>](#PerfMetricsAndWarningThresholds)  
  
-   [<span data-ttu-id="fbb45-110">設定和管理警告臨界值</span><span class="sxs-lookup"><span data-stu-id="fbb45-110">Setting Up and Managing Warning Thresholds</span></span>](#SetUpManageWarningThresholds)  
  
-   [<span data-ttu-id="fbb45-111">針對鏡像資料庫使用警示</span><span class="sxs-lookup"><span data-stu-id="fbb45-111">Using Alerts for a Mirrored Database</span></span>](#UseAlerts)  
  
-   [<span data-ttu-id="fbb45-112">相關工作</span><span class="sxs-lookup"><span data-stu-id="fbb45-112">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="performance-metrics-and-warning-thresholds"></a><a name="PerfMetricsAndWarningThresholds"></a> <span data-ttu-id="fbb45-113">效能標準和警告臨界值</span><span class="sxs-lookup"><span data-stu-id="fbb45-113">Performance Metrics and Warning Thresholds</span></span>  
 <span data-ttu-id="fbb45-114">下表將列出可設定警告的效能標準、描述對應的警告臨界值，並列出對應的 [資料庫鏡像監視器] 標籤。</span><span class="sxs-lookup"><span data-stu-id="fbb45-114">The following table lists the performance metrics for which warnings can be configured, describes the corresponding warning threshold, and lists the corresponding Database Mirroring Monitor label.</span></span>  
  
|<span data-ttu-id="fbb45-115">效能標準</span><span class="sxs-lookup"><span data-stu-id="fbb45-115">Performance metric</span></span>|<span data-ttu-id="fbb45-116">警告臨界值</span><span class="sxs-lookup"><span data-stu-id="fbb45-116">Warning threshold</span></span>|<span data-ttu-id="fbb45-117">資料庫鏡像監視器標籤</span><span class="sxs-lookup"><span data-stu-id="fbb45-117">Database Mirroring Monitor label</span></span>|  
|------------------------|-----------------------|--------------------------------------|  
|<span data-ttu-id="fbb45-118">未傳送的記錄</span><span class="sxs-lookup"><span data-stu-id="fbb45-118">Unsent log</span></span>|<span data-ttu-id="fbb45-119">指定會在主體伺服器執行個體上產生警告之未傳送記錄的 KB 數。</span><span class="sxs-lookup"><span data-stu-id="fbb45-119">Specifies how many kilobytes (KB) of unsent log generate a warning on the principal server instance.</span></span> <span data-ttu-id="fbb45-120">這個警告有助於從 KB 方面測量資料遺失的可能性，而且尤其與高效能模式相關。</span><span class="sxs-lookup"><span data-stu-id="fbb45-120">This warning helps measure the potential for data loss in terms of KB and is especially relevant for high-performance mode.</span></span> <span data-ttu-id="fbb45-121">但是，當鏡像因為夥伴中斷連接而暫停或暫止時，這個警告也會與高安全性模式有關。</span><span class="sxs-lookup"><span data-stu-id="fbb45-121">However, the warning is also relevant for high-safety mode when mirroring is paused or suspended because the partners become disconnected.</span></span>|<span data-ttu-id="fbb45-122">**如果未傳送的記錄超過臨界值，即發出警告**</span><span class="sxs-lookup"><span data-stu-id="fbb45-122">**Warn if the unsent log exceeds the threshold**</span></span>|  
|<span data-ttu-id="fbb45-123">未還原的記錄</span><span class="sxs-lookup"><span data-stu-id="fbb45-123">Unrestored log</span></span>|<span data-ttu-id="fbb45-124">指定會在鏡像伺服器執行個體上產生警告之未還原記錄的 KB 數。</span><span class="sxs-lookup"><span data-stu-id="fbb45-124">Specifies how many KB of unrestored log generate a warning on the mirror server instance.</span></span> <span data-ttu-id="fbb45-125">這個警告有助於測量容錯移轉時間。</span><span class="sxs-lookup"><span data-stu-id="fbb45-125">This warning helps measure failover time.</span></span> <span data-ttu-id="fbb45-126">*容錯移轉時間* 主要包含先前的鏡像伺服器向前復原其重做佇列中剩餘之所有記錄所需的時間，再加上一段很短的額外時間。</span><span class="sxs-lookup"><span data-stu-id="fbb45-126">*Failover time* consists mainly of the time that the former mirror server requires to roll forward any log remaining in its redo queue, plus a short additional time.</span></span><br /><br /> <span data-ttu-id="fbb45-127">注意:如果是自動容錯移轉，則系統發現錯誤的時間與容錯移轉時間無關。</span><span class="sxs-lookup"><span data-stu-id="fbb45-127">Note: For an automatic failover, the time for the system to notice the error is independent of the failover time.</span></span><br /><br /> <span data-ttu-id="fbb45-128">如需詳細資訊，請參閱 [預估角色切換期間的服務中斷時間 &#40;資料庫鏡像&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md)的程序交換。</span><span class="sxs-lookup"><span data-stu-id="fbb45-128">For more information, see [Estimate the Interruption of Service During Role Switching &#40;Database Mirroring&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md).</span></span>|<span data-ttu-id="fbb45-129">**如果未還原的記錄超過臨界值，即發出警告**</span><span class="sxs-lookup"><span data-stu-id="fbb45-129">**Warn if the unrestored log exceeds the threshold**</span></span>|  
|<span data-ttu-id="fbb45-130">最舊尚未傳送的交易</span><span class="sxs-lookup"><span data-stu-id="fbb45-130">Oldest unsent transaction</span></span>|<span data-ttu-id="fbb45-131">指定在主體伺服器執行個體上產生警告之前，傳送佇列中可以累積的交易分鐘數。</span><span class="sxs-lookup"><span data-stu-id="fbb45-131">Specifies the number of minutes worth of transactions that can accumulate in the send queue before a warning is generated on the principal server instance.</span></span> <span data-ttu-id="fbb45-132">這個警告有助於從時間方面測量資料遺失的可能性，而且尤其與高效能模式相關。</span><span class="sxs-lookup"><span data-stu-id="fbb45-132">This warning helps measure the potential for data loss in terms of time and is especially relevant for high-performance mode.</span></span> <span data-ttu-id="fbb45-133">但是，當鏡像因為夥伴中斷連接而暫停或暫止時，這個警告也會與高安全性模式有關。</span><span class="sxs-lookup"><span data-stu-id="fbb45-133">However, the warning is also relevant for high-safety mode when mirroring is paused or suspended because the partners become disconnected.</span></span>|<span data-ttu-id="fbb45-134">**如果最舊未傳送交易的時間超過臨界值，即發出警告**</span><span class="sxs-lookup"><span data-stu-id="fbb45-134">**Warn if the age of the oldest unsent transaction exceeds the threshold**</span></span>|  
|<span data-ttu-id="fbb45-135">鏡像認可負擔</span><span class="sxs-lookup"><span data-stu-id="fbb45-135">Mirror commit overhead</span></span>|<span data-ttu-id="fbb45-136">指定在主體伺服器上產生警告之前所容許之每項交易的平均延遲毫秒數。</span><span class="sxs-lookup"><span data-stu-id="fbb45-136">Specifies the number of milliseconds of average delay per transaction that are tolerated before a warning is generated on the principal server.</span></span> <span data-ttu-id="fbb45-137">這項延遲是當主體伺服器執行個體等待鏡像伺服器執行個體將交易記錄寫入重做佇列中時所產生的負擔量。</span><span class="sxs-lookup"><span data-stu-id="fbb45-137">This delay is the amount of overhead incurred while the principal server instance waits for the mirror server instance to write the transaction's log record into the redo queue.</span></span> <span data-ttu-id="fbb45-138">只有在高安全性模式中才會顯出這個值的重要性。</span><span class="sxs-lookup"><span data-stu-id="fbb45-138">This value is relevant only in high-safety mode.</span></span>|<span data-ttu-id="fbb45-139">**如果鏡像認可負擔超過臨界值，即發出警告**</span><span class="sxs-lookup"><span data-stu-id="fbb45-139">**Warn if the mirror commit overhead exceeds the threshold**</span></span>|  
  
 <span data-ttu-id="fbb45-140">系統管理員可以針對其中一項效能標準，在鏡像資料庫上指定臨界值。</span><span class="sxs-lookup"><span data-stu-id="fbb45-140">For any one of these performance metrics, a system administrator can specify a threshold on a mirrored database.</span></span> <span data-ttu-id="fbb45-141">如需詳細資訊，請參閱本主題後面的 [設定和管理警告臨界值](#SetUpManageWarningThresholds)。</span><span class="sxs-lookup"><span data-stu-id="fbb45-141">For more information, see [Setting Up and Managing Warning Thresholds](#SetUpManageWarningThresholds), later in this topic.</span></span>  
  
##  <a name="setting-up-and-managing-warning-thresholds"></a><a name="SetUpManageWarningThresholds"></a> <span data-ttu-id="fbb45-142">設定和管理警告臨界值</span><span class="sxs-lookup"><span data-stu-id="fbb45-142">Setting Up and Managing Warning Thresholds</span></span>  
 <span data-ttu-id="fbb45-143">系統管理員可以設定關鍵鏡像效能標準的一或多個警告臨界值。</span><span class="sxs-lookup"><span data-stu-id="fbb45-143">A system administrator can configure one or more warning thresholds for the key mirroring performance metrics.</span></span> <span data-ttu-id="fbb45-144">我們建議您在兩個夥伴上設定指定警告的臨界值，以便確保資料庫在容錯移轉時，警告仍會保持不變。</span><span class="sxs-lookup"><span data-stu-id="fbb45-144">We recommend setting a threshold for a given warning on both partners to make sure that the warning persists if the database fails over.</span></span> <span data-ttu-id="fbb45-145">每個夥伴上的適當臨界值會根據該夥伴系統的效能功能而定。</span><span class="sxs-lookup"><span data-stu-id="fbb45-145">The appropriate threshold on each partner depends on the performance capabilities of that partner's system.</span></span>  
  
 <span data-ttu-id="fbb45-146">您可以使用下列任何一項方式來設定並管理警告臨界值：</span><span class="sxs-lookup"><span data-stu-id="fbb45-146">Warning thresholds can be configured and managed by using either of the following:</span></span>  
  
-   <span data-ttu-id="fbb45-147">資料庫鏡像監視器</span><span class="sxs-lookup"><span data-stu-id="fbb45-147">Database Mirroring Monitor</span></span>  
  
     <span data-ttu-id="fbb45-148">在 [資料庫鏡像監視器] 中，管理員可以選取 **[警告]** 索引標籤頁面，藉以同時檢視位於主體和鏡像伺服器執行個體之選取資料庫的目前警告組態。</span><span class="sxs-lookup"><span data-stu-id="fbb45-148">In Database Mirroring Monitor, the administrator can view the current configuration of warnings for a selected database at both the principal and mirror server instances at the same time by selecting the **Warnings** tabbed page.</span></span> <span data-ttu-id="fbb45-149">在該頁面中，管理員可以開啟 **[設定警告臨界值]** 對話方塊，以便啟用和設定一或多個警告臨界值。</span><span class="sxs-lookup"><span data-stu-id="fbb45-149">From there, the administrator can open the **Set Warning Thresholds** dialog box to enable and configure one or more warning thresholds.</span></span>  
  
     <span data-ttu-id="fbb45-150">如需 [資料庫鏡像監視器] 介面的簡介，請參閱＜ [Database Mirroring Monitor Overview](database-mirroring-monitor-overview.md)＞。</span><span class="sxs-lookup"><span data-stu-id="fbb45-150">For an introduction to the Database Mirroring Monitor interface, see [Database Mirroring Monitor Overview](database-mirroring-monitor-overview.md).</span></span> <span data-ttu-id="fbb45-151">如需啟動「資料庫鏡像監視器」的相關資訊，請參閱 [啟動資料庫鏡像監視器 &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="fbb45-151">For information about launching Database Mirroring Monitor, see [Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="fbb45-152">系統預存程序</span><span class="sxs-lookup"><span data-stu-id="fbb45-152">System stored procedures</span></span>  
  
     <span data-ttu-id="fbb45-153">下列系統預存程序集可讓管理員一次設定並管理一個夥伴之鏡像資料庫的警告臨界值。</span><span class="sxs-lookup"><span data-stu-id="fbb45-153">The following set of system stored procedures enable an administrator to set up and manage warning thresholds on mirrored databases of one partner at a time.</span></span>  
  
    |<span data-ttu-id="fbb45-154">程序</span><span class="sxs-lookup"><span data-stu-id="fbb45-154">Procedure</span></span>|<span data-ttu-id="fbb45-155">描述</span><span class="sxs-lookup"><span data-stu-id="fbb45-155">Description</span></span>|  
    |---------------|-----------------|  
    |[<span data-ttu-id="fbb45-156">sp_dbmmonitorchangealert &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fbb45-156">sp_dbmmonitorchangealert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql)|<span data-ttu-id="fbb45-157">加入或變更指定之鏡像效能標準的警告臨界值。</span><span class="sxs-lookup"><span data-stu-id="fbb45-157">Adds or changes warning threshold for a specified mirroring performance metric.</span></span>|  
    |[<span data-ttu-id="fbb45-158">sp_dbmmonitorhelpalert &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fbb45-158">sp_dbmmonitorhelpalert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorhelpalert-transact-sql)|<span data-ttu-id="fbb45-159">傳回有關其中一個或所有關鍵資料庫鏡像監視器效能標準之警告臨界值的資訊。</span><span class="sxs-lookup"><span data-stu-id="fbb45-159">Returns information about warning thresholds on one or all of several key database mirroring monitor performance metrics.</span></span>|  
    |[<span data-ttu-id="fbb45-160">sp_dbmmonitordropalert &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fbb45-160">sp_dbmmonitordropalert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitordropalert-transact-sql)|<span data-ttu-id="fbb45-161">卸除指定效能標準的警告。</span><span class="sxs-lookup"><span data-stu-id="fbb45-161">Drops the warning for a specified performance metric.</span></span>|  
  
## <a name="performance-threshold-events-sent-to-the-windows-event-log"></a><span data-ttu-id="fbb45-162">傳送至 Windows 事件記錄檔的效能臨界值事件</span><span class="sxs-lookup"><span data-stu-id="fbb45-162">Performance-Threshold Events Sent to the Windows Event Log</span></span>  
 <span data-ttu-id="fbb45-163">如果已經定義效能標準的警告臨界值，當狀態資料表更新後，就會根據臨界值評估最新的值。</span><span class="sxs-lookup"><span data-stu-id="fbb45-163">If warning thresholdis defined for a performance metric, when the status table is updated, the latest value is evaluated against the threshold.</span></span> <span data-ttu-id="fbb45-164">如果已達到臨界值，更新程式**sp_dbmmonitorupdate**會產生資訊事件（此為度量的*效能臨界值事件*），並將事件寫入 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="fbb45-164">If the threshold has been reached, the update procedure, **sp_dbmmonitorupdate**, generates an informational event-a *performance-threshold event*- for the metric and writes the event to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows event log.</span></span> <span data-ttu-id="fbb45-165">下表將列出效能臨界值事件的事件識別碼。</span><span class="sxs-lookup"><span data-stu-id="fbb45-165">The following table lists the event IDs of the performance-threshold events.</span></span>  
  
|<span data-ttu-id="fbb45-166">效能標準</span><span class="sxs-lookup"><span data-stu-id="fbb45-166">Performance metric</span></span>|<span data-ttu-id="fbb45-167">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="fbb45-167">Event ID</span></span>|  
|------------------------|--------------|  
|<span data-ttu-id="fbb45-168">未傳送的記錄</span><span class="sxs-lookup"><span data-stu-id="fbb45-168">Unsent log</span></span>|<span data-ttu-id="fbb45-169">32042</span><span class="sxs-lookup"><span data-stu-id="fbb45-169">32042</span></span>|  
|<span data-ttu-id="fbb45-170">未還原的記錄</span><span class="sxs-lookup"><span data-stu-id="fbb45-170">Unrestored log</span></span>|<span data-ttu-id="fbb45-171">32043</span><span class="sxs-lookup"><span data-stu-id="fbb45-171">32043</span></span>|  
|<span data-ttu-id="fbb45-172">最舊尚未傳送的交易</span><span class="sxs-lookup"><span data-stu-id="fbb45-172">Oldest unsent transaction</span></span>|<span data-ttu-id="fbb45-173">32040</span><span class="sxs-lookup"><span data-stu-id="fbb45-173">32040</span></span>|  
|<span data-ttu-id="fbb45-174">鏡像認可負擔</span><span class="sxs-lookup"><span data-stu-id="fbb45-174">Mirror commit overhead</span></span>|<span data-ttu-id="fbb45-175">32044</span><span class="sxs-lookup"><span data-stu-id="fbb45-175">32044</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="fbb45-176">管理員可以定義其中一或多個事件的警示。</span><span class="sxs-lookup"><span data-stu-id="fbb45-176">An administrator can define alerts on any one or more of these events.</span></span> <span data-ttu-id="fbb45-177">如需詳細資訊，請參閱本主題後面的 [針對鏡像資料庫使用警示](#UseAlerts)</span><span class="sxs-lookup"><span data-stu-id="fbb45-177">For more information, see [Using Alerts for a Mirrored Database](#UseAlerts), later in this</span></span>  
>   
>  <span data-ttu-id="fbb45-178">。</span><span class="sxs-lookup"><span data-stu-id="fbb45-178">topic.</span></span>  
  
##  <a name="using-alerts-for-a-mirrored-database"></a><a name="UseAlerts"></a><span data-ttu-id="fbb45-179">針對鏡像資料庫使用警示</span><span class="sxs-lookup"><span data-stu-id="fbb45-179">Using Alerts for a Mirrored Database</span></span>  
 <span data-ttu-id="fbb45-180">監視鏡像資料庫最重要的部分就是設定重大資料庫鏡像事件的警示。</span><span class="sxs-lookup"><span data-stu-id="fbb45-180">An important part of monitoring a mirrored database is configuring alerts on significant database mirro events.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fbb45-181">會產生下列資料庫鏡像事件類型：</span><span class="sxs-lookup"><span data-stu-id="fbb45-181">generates the following types of database mirroring events:</span></span>  
  
-   <span data-ttu-id="fbb45-182">效能臨界值事件</span><span class="sxs-lookup"><span data-stu-id="fbb45-182">Performance threshold events</span></span>  
  
     <span data-ttu-id="fbb45-183">如需詳細資訊，請參閱本主題前面的「傳送至 Windows 事件記錄檔的效能臨界值事件」。</span><span class="sxs-lookup"><span data-stu-id="fbb45-183">For more information, see "Performance-Threshold Events Sent to the Windows Event Log" earlier in this topic.</span></span>  
  
-   <span data-ttu-id="fbb45-184">狀態變更事件</span><span class="sxs-lookup"><span data-stu-id="fbb45-184">State-change events</span></span>  
  
     <span data-ttu-id="fbb45-185">這些是資料庫鏡像工作階段的內部狀態發生變更時產生的 Windows Management Instrumentation (WMI) 事件。</span><span class="sxs-lookup"><span data-stu-id="fbb45-185">These are Windows Management Instrumentation (WMI) events that are generated when changes occur in the internal state of a database mirroring session.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fbb45-186">如需詳細資訊，請參閱 [伺服器事件的 WMI 提供者概念](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="fbb45-186">For more information, see [WMI Provider for Server Events Concepts](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md).</span></span>  
  
 <span data-ttu-id="fbb45-187">系統管理員可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 或其他應用程式 (例如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Operations Manager)，設定這些事件的警示。</span><span class="sxs-lookup"><span data-stu-id="fbb45-187">A system administrator can configure alerts on these by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent or other applications, such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Operations Manager.</span></span>  
  
 <span data-ttu-id="fbb45-188">定義資料庫鏡像事件的警示後，我們建議您在兩個夥伴伺服器執行個體上都定義警告臨界值和警示。</span><span class="sxs-lookup"><span data-stu-id="fbb45-188">When you define alerts on database mirroring events, we recommend that you define warning thresholds and alerts at both partner server instances.</span></span> <span data-ttu-id="fbb45-189">雖然個別事件會在主體伺服器或鏡像伺服器上產生，不過每一個夥伴都可以隨時執行任何一個角色。</span><span class="sxs-lookup"><span data-stu-id="fbb45-189">Individual events are generated at either the principal server or the mirror server, but each partner can perform either role at any time.</span></span> <span data-ttu-id="fbb45-190">若要確保在容錯移轉之後警示會繼續運作，您必須在兩個夥伴上都定義該警示。</span><span class="sxs-lookup"><span data-stu-id="fbb45-190">To make sure that an alert continues to operate after a failover, the alert must be defined at both partners.</span></span>  
  
 <span data-ttu-id="fbb45-191">如需詳細資訊，請參閱此 [SQL Server 網站](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)上關於資料庫鏡像事件之警示的白皮書。</span><span class="sxs-lookup"><span data-stu-id="fbb45-191">For more information, see the white paper about alerting on database mirroring events at this [SQL Server Web site](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md).</span></span> <span data-ttu-id="fbb45-192">這份白皮書包含如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent、資料庫鏡像 WMI 事件及範例指令碼來設定警示的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="fbb45-192">This white paper contains information about how to configure alerts using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, the database mirroring WMI events, and sample scripts.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fbb45-193">我們強烈建議您針對所有鏡像工作階段，將資料庫設定為傳送任何狀態變更事件的警示。</span><span class="sxs-lookup"><span data-stu-id="fbb45-193">For all mirroring sessions, we strongly recommend that you configure the database to send an alert on any state-change events.</span></span> <span data-ttu-id="fbb45-194">除非狀態變更預期為手動組態變更的結果，否則就表示發生了可能會危害資料的事件。</span><span class="sxs-lookup"><span data-stu-id="fbb45-194">Unless a state change is expected as the result of a manual configuration change, something has occurred that could compromise your data.</span></span> <span data-ttu-id="fbb45-195">若要有效保護資料，請識別並修正非預期狀態變更的原因。</span><span class="sxs-lookup"><span data-stu-id="fbb45-195">To help protect your data, identify and fix the cause of an unexpected state change.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="fbb45-196">相關工作</span><span class="sxs-lookup"><span data-stu-id="fbb45-196">Related Tasks</span></span>  
 <span data-ttu-id="fbb45-197">**若要使用 SQL Server Management Studio 建立警示**</span><span class="sxs-lookup"><span data-stu-id="fbb45-197">**To create an alert using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="fbb45-198">使用錯誤號碼建立警示</span><span class="sxs-lookup"><span data-stu-id="fbb45-198">Create an Alert Using an Error Number</span></span>](../../ssms/agent/create-an-alert-using-an-error-number.md)  
  
-   [<span data-ttu-id="fbb45-199">建立 WMI 事件警示</span><span class="sxs-lookup"><span data-stu-id="fbb45-199">Create a WMI Event Alert</span></span>](../../ssms/agent/create-a-wmi-event-alert.md)  
  
 <span data-ttu-id="fbb45-200">**若要監控資料庫鏡像**</span><span class="sxs-lookup"><span data-stu-id="fbb45-200">**To monitor database mirroring**</span></span>  
  
-   [<span data-ttu-id="fbb45-201">啟動資料庫鏡像監視器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="fbb45-201">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="fbb45-202">sp_dbmmonitoraddmonitoring &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fbb45-202">sp_dbmmonitoraddmonitoring &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitoraddmonitoring-transact-sql)  
  
-   [<span data-ttu-id="fbb45-203">sp_dbmmonitorchangealert &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fbb45-203">sp_dbmmonitorchangealert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql)  
  
-   [<span data-ttu-id="fbb45-204">sp_dbmmonitorchangemonitoring &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fbb45-204">sp_dbmmonitorchangemonitoring &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql)  
  
-   [<span data-ttu-id="fbb45-205">sp_dbmmonitordropalert &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fbb45-205">sp_dbmmonitordropalert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitordropalert-transact-sql)  
  
-   [<span data-ttu-id="fbb45-206">sp_dbmmonitordropmonitoring &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fbb45-206">sp_dbmmonitordropmonitoring &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql)  
  
-   [<span data-ttu-id="fbb45-207">sp_dbmmonitorhelpalert &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fbb45-207">sp_dbmmonitorhelpalert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorhelpalert-transact-sql)  
  
-   [<span data-ttu-id="fbb45-208">sp_dbmmonitorhelpmonitoring &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fbb45-208">sp_dbmmonitorhelpmonitoring &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql)  
  
-   [<span data-ttu-id="fbb45-209">sp_dbmmonitorresults &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fbb45-209">sp_dbmmonitorresults &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql)  
  
-   [<span data-ttu-id="fbb45-210">sp_dbmmonitorupdate &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fbb45-210">sp_dbmmonitorupdate &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dbmmonitorupdate-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="fbb45-211">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbb45-211">See Also</span></span>  
 <span data-ttu-id="fbb45-212">[資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fbb45-212">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="fbb45-213">監視資料庫鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fbb45-213">Monitoring Database Mirroring &#40;SQL Server&#41;</span></span>](monitoring-database-mirroring-sql-server.md)  
  
  
