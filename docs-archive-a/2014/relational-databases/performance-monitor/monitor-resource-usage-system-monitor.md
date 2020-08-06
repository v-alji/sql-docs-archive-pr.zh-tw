---
title: 監視資源使用狀況 (系統監視器) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server], resource usage
- System Monitor [SQL Server], about Windows System Monitor
- resource usage monitoring [SQL Server]
- System Monitor [SQL Server]
- counters [SQL Server], resource usage subjects
- performance counters [SQL Server], resource usage subjects
- Windows System Monitor [SQL Server], about Windows System Monitor
- monitoring [SQL Server], server resource usage
- monitoring resource usage [SQL Server]
- Windows System Monitor [SQL Server]
- database monitoring [SQL Server], resource usage
- database performance [SQL Server], resource usage
- tuning databases [SQL Server], resource usage
- server performance [SQL Server], resource usage
ms.assetid: f2993a28-0b81-46f2-aec0-6877fe990387
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d691091a41e3161c733902824bf439b6788cc4f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606246"
---
# <a name="monitor-resource-usage-system-monitor"></a><span data-ttu-id="ff777-102">監視資源使用狀況 (系統監視器)</span><span class="sxs-lookup"><span data-stu-id="ff777-102">Monitor Resource Usage (System Monitor)</span></span>
  <span data-ttu-id="ff777-103">如果您正在執行 Microsoft Windows 伺服器作業系統，請使用系統監視器圖形工具，測量 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的效能。</span><span class="sxs-lookup"><span data-stu-id="ff777-103">If you are running Microsoft Windows server operating system, use the System Monitor graphical tool to measure the performance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ff777-104">您可以檢視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件、效能計數器及其他物件 (如處理器、記憶體、快取、執行緒和處理序) 的行為。</span><span class="sxs-lookup"><span data-stu-id="ff777-104">You can view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects, performance counters, and the behavior of other objects, such as processors, memory, cache, threads, and processes.</span></span> <span data-ttu-id="ff777-105">這些物件每一個都有一組關聯的計數器，可測量裝置的使用狀況 (Usage)、佇列長度 (Queue Length)、延遲 (Delay) 和產能 (Throughput) 及內部壅塞的其他指示器。</span><span class="sxs-lookup"><span data-stu-id="ff777-105">Each of these objects has an associated set of counters that measure device usage, queue lengths, delays, and other indicators of throughput and internal congestion.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ff777-106">在 Windows NT 4.0 之後，系統監視器已取代效能監視器。</span><span class="sxs-lookup"><span data-stu-id="ff777-106">System Monitor replaced Performance Monitor after Windows NT 4.0.</span></span>  
  
## <a name="benefits-of-system-monitor"></a><span data-ttu-id="ff777-107">系統監視器的優點</span><span class="sxs-lookup"><span data-stu-id="ff777-107">Benefits of System Monitor</span></span>  
 <span data-ttu-id="ff777-108">系統監視器可同時監視 Windows 作業系統與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 計數器，有助於判斷 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 與 Windows 的效能之間是否有任何關聯。</span><span class="sxs-lookup"><span data-stu-id="ff777-108">System Monitor can be useful to monitor Windows operating system and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] counters at the same time to determine any correlation between the performance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows.</span></span> <span data-ttu-id="ff777-109">例如，同時監視 Windows 磁碟輸入/輸出 (I/O) 計數器與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 緩衝區管理員計數器，可顯示整個系統的運作方式。</span><span class="sxs-lookup"><span data-stu-id="ff777-109">For example, monitoring the Windows disk input/output (I/O) counters and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Buffer Manager counters at the same time can reveal the behavior of the entire system.</span></span>  
  
 <span data-ttu-id="ff777-110">您可利用系統監視器取得有關目前 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 活動與效能的統計資料。</span><span class="sxs-lookup"><span data-stu-id="ff777-110">System Monitor allows you to obtain statistics on current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] activity and performance.</span></span> <span data-ttu-id="ff777-111">使用系統監視器可以：</span><span class="sxs-lookup"><span data-stu-id="ff777-111">Using System Monitor, you can:</span></span>  
  
-   <span data-ttu-id="ff777-112">同時從任意多台電腦中檢視資料。</span><span class="sxs-lookup"><span data-stu-id="ff777-112">View data simultaneously from any number of computers.</span></span>  
  
-   <span data-ttu-id="ff777-113">檢視與變更圖表以反映目前的活動，並顯示計數器數值，其更新頻率是使用者自訂的。</span><span class="sxs-lookup"><span data-stu-id="ff777-113">View and change charts to reflect current activity, and show counter values that are updated at a frequency that the user defines.</span></span>  
  
-   <span data-ttu-id="ff777-114">從圖表、記錄檔、警示記錄檔和報表中將資料匯出至試算表或資料庫應用程式內，以便作進一步的處理與列印。</span><span class="sxs-lookup"><span data-stu-id="ff777-114">Export data from charts, logs, alert logs, and reports to spreadsheet or database applications for further manipulation and printing.</span></span>  
  
-   <span data-ttu-id="ff777-115">加入系統警示，將事件列在警示記錄檔，並且可以發出網路警示來通知您。</span><span class="sxs-lookup"><span data-stu-id="ff777-115">Add system alerts that list an event in the alert log and can notify you by issuing a network alert.</span></span>  
  
-   <span data-ttu-id="ff777-116">當計數器數值首次或每次超過或低於某個使用者自訂的數值時，就執行預先定義的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ff777-116">Run a predefined application the first time or every time a counter value goes over or under a user-defined value.</span></span>  
  
-   <span data-ttu-id="ff777-117">建立記錄檔，裡面包含不同電腦之各種物件的相關資料。</span><span class="sxs-lookup"><span data-stu-id="ff777-117">Create log files that contain data about various objects from different computers.</span></span>  
  
-   <span data-ttu-id="ff777-118">將其他現存記錄檔的資料附加到某個檔案的選取區段內，以構成長期的封存。</span><span class="sxs-lookup"><span data-stu-id="ff777-118">Append to one file selected sections from other existing log files to form a long-term archive.</span></span>  
  
-   <span data-ttu-id="ff777-119">檢視目前的活動報告，或使用現有的記錄檔來建立報告。</span><span class="sxs-lookup"><span data-stu-id="ff777-119">View current-activity reports, or create reports from existing log files.</span></span>  
  
-   <span data-ttu-id="ff777-120">儲存個別的圖表、警示、記錄檔、報告設定，或整個工作空間設定，以便重複使用。</span><span class="sxs-lookup"><span data-stu-id="ff777-120">Save individual chart, alert, log, or report settings, or the entire workspace setup for reuse.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ff777-121">在 Windows NT 4.0 之後，「系統監視器」已取代「效能監視器」。</span><span class="sxs-lookup"><span data-stu-id="ff777-121">System Monitor replaced the Performance Monitor after Windows NT 4.0.</span></span> <span data-ttu-id="ff777-122">您可以使用系統監視器或效能監視器進行這些工作。</span><span class="sxs-lookup"><span data-stu-id="ff777-122">You can use either the System Monitor or Performance Monitor to do these tasks.</span></span>  
  
## <a name="system-monitor-performance"></a><span data-ttu-id="ff777-123">系統監視器效能</span><span class="sxs-lookup"><span data-stu-id="ff777-123">System Monitor Performance</span></span>  
 <span data-ttu-id="ff777-124">當您監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 與 Microsoft Windows 作業系統，以研究效能相關的問題時，一開始可集中於三個主要領域上：</span><span class="sxs-lookup"><span data-stu-id="ff777-124">When you monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the Microsoft Windows operating system to investigate performance-related issues, concentrate your initial efforts in three main areas:</span></span>  
  
-   <span data-ttu-id="ff777-125">磁碟活動</span><span class="sxs-lookup"><span data-stu-id="ff777-125">Disk activity</span></span>  
  
-   <span data-ttu-id="ff777-126">處理器使用率</span><span class="sxs-lookup"><span data-stu-id="ff777-126">Processor utilization</span></span>  
  
-   <span data-ttu-id="ff777-127">記憶體使用量</span><span class="sxs-lookup"><span data-stu-id="ff777-127">Memory usage</span></span>  
  
 <span data-ttu-id="ff777-128">監視正在執行系統監視器的電腦，可能會稍微影響電腦的效能；</span><span class="sxs-lookup"><span data-stu-id="ff777-128">Monitoring a computer on which System Monitor is running can affect computer performance slightly.</span></span> <span data-ttu-id="ff777-129">因此，您可將「系統監視器」資料記錄到另一個磁碟 (或電腦)，以減少對受監視電腦的影響，或從遠端電腦執行「系統監視器」。</span><span class="sxs-lookup"><span data-stu-id="ff777-129">Therefore, either log the System Monitor data to another disk (or computer) so that it reduces the effect on the computer being monitored, or run System Monitor from a remote computer.</span></span> <span data-ttu-id="ff777-130">請只監視有興趣的計數器。</span><span class="sxs-lookup"><span data-stu-id="ff777-130">Monitor only the counters in which you are interested.</span></span> <span data-ttu-id="ff777-131">如果您監視太多計數器，系統會將資源使用狀況負擔加入監視處理序，並且會影響正在監視的電腦之效能。</span><span class="sxs-lookup"><span data-stu-id="ff777-131">If you monitor too many counters, resource usage overhead is added to the monitoring process and affects the performance of the computer that is being monitored.</span></span>  
  
## <a name="system-monitor-tasks"></a><span data-ttu-id="ff777-132">系統監視器工作</span><span class="sxs-lookup"><span data-stu-id="ff777-132">System Monitor Tasks</span></span>  
  
|<span data-ttu-id="ff777-133">工作描述</span><span class="sxs-lookup"><span data-stu-id="ff777-133">Task Description</span></span>|<span data-ttu-id="ff777-134">主題</span><span class="sxs-lookup"><span data-stu-id="ff777-134">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="ff777-135">描述使用系統監視器的時機，並討論使用系統監視器時的效能負擔。</span><span class="sxs-lookup"><span data-stu-id="ff777-135">Describes when to use System Monitor and discusses performance overhead when you use System Monitor.</span></span>|[<span data-ttu-id="ff777-136">執行系統監視器</span><span class="sxs-lookup"><span data-stu-id="ff777-136">Run System Monitor</span></span>](run-system-monitor.md)|  
|<span data-ttu-id="ff777-137">描述如何監視磁碟計數器以判定磁碟活動與其 SQL Server 元件所產生之 I/O 數量。</span><span class="sxs-lookup"><span data-stu-id="ff777-137">Describes how to monitor disk counters to determine disk activity and the amount of I/O generated by their SQL Server components.</span></span>|[<span data-ttu-id="ff777-138">監視磁碟使用量</span><span class="sxs-lookup"><span data-stu-id="ff777-138">Monitor Disk Usage</span></span>](monitor-disk-usage.md)|  
|<span data-ttu-id="ff777-139">描述如何監視 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體，以判定 CPU 使用率是否在正常範圍內。</span><span class="sxs-lookup"><span data-stu-id="ff777-139">Describes how to monitor an instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to determine whether CPU usage rates are within normal ranges.</span></span>|[<span data-ttu-id="ff777-140">監視 CPU 使用量</span><span class="sxs-lookup"><span data-stu-id="ff777-140">Monitor CPU Usage</span></span>](monitor-cpu-usage.md)|  
|<span data-ttu-id="ff777-141">描述如何監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體，以確認記憶體使用量在正常範圍內。</span><span class="sxs-lookup"><span data-stu-id="ff777-141">Describes how to monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to confirm that memory usage is within typical ranges.</span></span>|[<span data-ttu-id="ff777-142">監視記憶體使用量</span><span class="sxs-lookup"><span data-stu-id="ff777-142">Monitor Memory Usage</span></span>](monitor-memory-usage.md)|  
|<span data-ttu-id="ff777-143">描述如何建立警示，讓它在達到系統監視器計數器的臨界值時引發。</span><span class="sxs-lookup"><span data-stu-id="ff777-143">Describes how to create an alert that is raised when a threshold value for a System Monitor counter has been reached.</span></span>|[<span data-ttu-id="ff777-144">建立 SQL Server 資料庫警示</span><span class="sxs-lookup"><span data-stu-id="ff777-144">Create a SQL Server Database Alert</span></span>](create-a-sql-server-database-alert.md)|  
|<span data-ttu-id="ff777-145">描述如何建立圖表、警示、記錄與報表，以監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ff777-145">Describes how to you create charts, alerts, logs, and reports to monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|[<span data-ttu-id="ff777-146">建立圖表、警示、記錄和報表</span><span class="sxs-lookup"><span data-stu-id="ff777-146">Create Charts, Alerts, Logs, and Reports</span></span>](create-charts-alerts-logs-and-reports.md)|  
|<span data-ttu-id="ff777-147">列出系統監視器用以監視電腦中正在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體之活動的物件與計數器。</span><span class="sxs-lookup"><span data-stu-id="ff777-147">Lists objects and counters that System Monitor uses to monitor activity in computers running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|[<span data-ttu-id="ff777-148">使用 SQL Server 物件</span><span class="sxs-lookup"><span data-stu-id="ff777-148">Use SQL Server Objects</span></span>](use-sql-server-objects.md)|  
|<span data-ttu-id="ff777-149">列出系統監視器用以監視記憶體中 OLTP 活動的物件與計數器。</span><span class="sxs-lookup"><span data-stu-id="ff777-149">Lists objects and counters that System Monitor uses to monitor In-Memory OLTP activity.</span></span>|[<span data-ttu-id="ff777-150">XTP &#40;記憶體內部 OLTP&#41; 效能計數器</span><span class="sxs-lookup"><span data-stu-id="ff777-150">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)|  
  
  
