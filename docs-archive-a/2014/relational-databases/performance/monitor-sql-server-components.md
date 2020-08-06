---
title: 監視 SQL Server 元件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: e8f1b16b-ea40-4e12-886c-967ebda4e6e4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: baefe9aa1848bc3347a9a5a87c2ab81c382a6717
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594021"
---
# <a name="monitor-sql-server-components"></a><span data-ttu-id="f84f6-102">監視 SQL Server 元件</span><span class="sxs-lookup"><span data-stu-id="f84f6-102">Monitor SQL Server Components</span></span>
  <span data-ttu-id="f84f6-103">因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是在動態環境下提供服務，所以監視很重要。</span><span class="sxs-lookup"><span data-stu-id="f84f6-103">Monitoring is important because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides a service in a dynamic environment.</span></span> <span data-ttu-id="f84f6-104">應用程式中的資料會變更。</span><span class="sxs-lookup"><span data-stu-id="f84f6-104">The data in the application changes.</span></span> <span data-ttu-id="f84f6-105">使用者需要的存取類型會變更。</span><span class="sxs-lookup"><span data-stu-id="f84f6-105">The type of access that users require changes.</span></span> <span data-ttu-id="f84f6-106">使用者的連接方式會變更。</span><span class="sxs-lookup"><span data-stu-id="f84f6-106">The way that users connect changes.</span></span> <span data-ttu-id="f84f6-107">甚至存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的應用程式類型也可能變更，但 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會自動管理系統層級的資源，例如記憶體和磁碟空間，以便將系統層級的密集手動微調需求降到最低。</span><span class="sxs-lookup"><span data-stu-id="f84f6-107">The types of applications accessing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] may even change, but [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] automatically manages system-level resources, such as memory and disk space, to minimize the need for extensive system-level manual tuning.</span></span> <span data-ttu-id="f84f6-108">監視可讓管理員識別效能趨勢，以決定是否需要變更。</span><span class="sxs-lookup"><span data-stu-id="f84f6-108">Monitoring lets administrators identify performance trends to determine if changes are necessary.</span></span>  
  
 <span data-ttu-id="f84f6-109">若要有效監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的任何元件：</span><span class="sxs-lookup"><span data-stu-id="f84f6-109">To monitor any component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectively:</span></span>  
  
1.  <span data-ttu-id="f84f6-110">決定您的監視目標。</span><span class="sxs-lookup"><span data-stu-id="f84f6-110">Determine your monitoring goals.</span></span>  
  
2.  <span data-ttu-id="f84f6-111">選取適當的工具。</span><span class="sxs-lookup"><span data-stu-id="f84f6-111">Select the appropriate tool.</span></span>  
  
3.  <span data-ttu-id="f84f6-112">識別要監視的元件。</span><span class="sxs-lookup"><span data-stu-id="f84f6-112">Identify components to monitor.</span></span>  
  
4.  <span data-ttu-id="f84f6-113">選取這些元件的標準。</span><span class="sxs-lookup"><span data-stu-id="f84f6-113">Select metrics for those components.</span></span>  
  
5.  <span data-ttu-id="f84f6-114">監視伺服器。</span><span class="sxs-lookup"><span data-stu-id="f84f6-114">Monitor the server.</span></span>  
  
6.  <span data-ttu-id="f84f6-115">分析資料。</span><span class="sxs-lookup"><span data-stu-id="f84f6-115">Analyze the data.</span></span>  
  
 <span data-ttu-id="f84f6-116">以下依次討論這些步驟。</span><span class="sxs-lookup"><span data-stu-id="f84f6-116">These steps are discussed in turn below.</span></span>  
  
## <a name="determine-your-monitoring-goals"></a><span data-ttu-id="f84f6-117">決定您的監視目標</span><span class="sxs-lookup"><span data-stu-id="f84f6-117">Determine Your Monitoring Goals</span></span>  
 <span data-ttu-id="f84f6-118">若要有效監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，您應該具體描述您的監視理由。</span><span class="sxs-lookup"><span data-stu-id="f84f6-118">To monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectively you should clearly identify your reason for monitoring.</span></span> <span data-ttu-id="f84f6-119">可以包括下列理由：</span><span class="sxs-lookup"><span data-stu-id="f84f6-119">Reasons can include the following:</span></span>  
  
-   <span data-ttu-id="f84f6-120">建立效能基準線。</span><span class="sxs-lookup"><span data-stu-id="f84f6-120">Establish a baseline for performance.</span></span>  
  
-   <span data-ttu-id="f84f6-121">識別效能變更趨勢。</span><span class="sxs-lookup"><span data-stu-id="f84f6-121">Identify performance changes over time.</span></span>  
  
-   <span data-ttu-id="f84f6-122">診斷特定效能問題。</span><span class="sxs-lookup"><span data-stu-id="f84f6-122">Diagnose specific performance problems.</span></span>  
  
-   <span data-ttu-id="f84f6-123">識別要最佳化的元件或處理序。</span><span class="sxs-lookup"><span data-stu-id="f84f6-123">Identify components or processes to optimize.</span></span>  
  
-   <span data-ttu-id="f84f6-124">比較不同用戶端應用程式在效能上的影響。</span><span class="sxs-lookup"><span data-stu-id="f84f6-124">Compare the effect of different client applications on performance.</span></span>  
  
-   <span data-ttu-id="f84f6-125">稽核使用者活動。</span><span class="sxs-lookup"><span data-stu-id="f84f6-125">Audit user activity.</span></span>  
  
-   <span data-ttu-id="f84f6-126">以不同的負載來測試伺服器。</span><span class="sxs-lookup"><span data-stu-id="f84f6-126">Test a server under different loads.</span></span>  
  
-   <span data-ttu-id="f84f6-127">測試資料庫架構。</span><span class="sxs-lookup"><span data-stu-id="f84f6-127">Test database architecture.</span></span>  
  
-   <span data-ttu-id="f84f6-128">測試維護排程。</span><span class="sxs-lookup"><span data-stu-id="f84f6-128">Test maintenance schedules.</span></span>  
  
-   <span data-ttu-id="f84f6-129">測試備份與還原計畫。</span><span class="sxs-lookup"><span data-stu-id="f84f6-129">Test backup and restore plans.</span></span>  
  
-   <span data-ttu-id="f84f6-130">決定修改硬體組態的時間。</span><span class="sxs-lookup"><span data-stu-id="f84f6-130">Determining when to modify your hardware configuration.</span></span>  
  
## <a name="select-the-appropriate-tool"></a><span data-ttu-id="f84f6-131">選取適當的工具</span><span class="sxs-lookup"><span data-stu-id="f84f6-131">Select the Appropriate Tool</span></span>  
 <span data-ttu-id="f84f6-132">決定監視的原因之後，您應該針對該監視類型選取適當的工具。</span><span class="sxs-lookup"><span data-stu-id="f84f6-132">After determining why you are monitoring, you should select the appropriate tools for that type of monitoring.</span></span> <span data-ttu-id="f84f6-133">Windows 作業系統和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會提供完整的工具集合，可在交易密集的環境中監視伺服器。</span><span class="sxs-lookup"><span data-stu-id="f84f6-133">The Windows operating system and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provide a complete set of tools to monitor servers in transaction-intensive environments.</span></span> <span data-ttu-id="f84f6-134">這些工具可清楚地呈現 SQL Server Database Engine 執行個體或 SQL Server Analysis Services 執行個體的狀況。</span><span class="sxs-lookup"><span data-stu-id="f84f6-134">These tools clearly reveal the condition of an instance of the SQL Server Database Engine or an instance of SQL Server Analysis Services.</span></span>  
  
 <span data-ttu-id="f84f6-135">Windows 會提供下列工具來監視伺服器上執行的應用程式：</span><span class="sxs-lookup"><span data-stu-id="f84f6-135">Windows provides the following tools for monitoring applications that are running on a server:</span></span>  
  
-   <span data-ttu-id="f84f6-136">系統監視器，可讓您收集和檢視記憶體、磁碟及處理器用量等活動的即時資料</span><span class="sxs-lookup"><span data-stu-id="f84f6-136">System Monitor, which lets you collect and view real-time data about activities such as memory, disk, and processor usage</span></span>  
  
-   <span data-ttu-id="f84f6-137">效能記錄與警示</span><span class="sxs-lookup"><span data-stu-id="f84f6-137">Performance logs and alerts</span></span>  
  
-   <span data-ttu-id="f84f6-138">工作管理員</span><span class="sxs-lookup"><span data-stu-id="f84f6-138">Task Manager</span></span>  
  
 <span data-ttu-id="f84f6-139">如需有關 Windows Server 或 Windows 工具的詳細資訊，請參閱 Windows 文件集。</span><span class="sxs-lookup"><span data-stu-id="f84f6-139">For more information about Windows Server or Windows tools, see the Windows documentation.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f84f6-140">可提供下列工具來監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的元件：</span><span class="sxs-lookup"><span data-stu-id="f84f6-140">provides the following tools for monitoring components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="f84f6-141">SQL 追蹤</span><span class="sxs-lookup"><span data-stu-id="f84f6-141">SQL Trace</span></span>  
  
-   [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]  
  
-   <span data-ttu-id="f84f6-142">Distributed Replay Utility</span><span class="sxs-lookup"><span data-stu-id="f84f6-142">Distributed Replay Utility</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="f84f6-143">活動監視器</span><span class="sxs-lookup"><span data-stu-id="f84f6-143">Activity Monitor</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="f84f6-144">圖形化顯示計畫</span><span class="sxs-lookup"><span data-stu-id="f84f6-144">Graphical Showplan</span></span>  
  
-   <span data-ttu-id="f84f6-145">預存程序</span><span class="sxs-lookup"><span data-stu-id="f84f6-145">Stored procedures</span></span>  
  
-   <span data-ttu-id="f84f6-146">Database Console Commands (DBCC)</span><span class="sxs-lookup"><span data-stu-id="f84f6-146">Database Console Commands (DBCC)</span></span>  
  
-   <span data-ttu-id="f84f6-147">內建函式</span><span class="sxs-lookup"><span data-stu-id="f84f6-147">Built-in functions</span></span>  
  
-   <span data-ttu-id="f84f6-148">追蹤旗標</span><span class="sxs-lookup"><span data-stu-id="f84f6-148">Trace flags</span></span>  
  
 <span data-ttu-id="f84f6-149">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 監視工具的詳細資訊，請參閱 [效能監視及微調工具](performance-monitoring-and-tuning-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="f84f6-149">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] monitoring tools, see [Performance Monitoring and Tuning Tools](performance-monitoring-and-tuning-tools.md).</span></span>  
  
## <a name="identify-the-components-to-monitor"></a><span data-ttu-id="f84f6-150">識別要監視的元件</span><span class="sxs-lookup"><span data-stu-id="f84f6-150">Identify the Components to Monitor</span></span>  
 <span data-ttu-id="f84f6-151">監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的第三個步驟是識別您監視的元件。</span><span class="sxs-lookup"><span data-stu-id="f84f6-151">The third step to monitoring an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is to identify the components that you monitor.</span></span> <span data-ttu-id="f84f6-152">例如，如果使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 來追蹤伺服器，您可以定義追蹤來收集特定事件的資料。</span><span class="sxs-lookup"><span data-stu-id="f84f6-152">For example, if you are using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to trace a server you can define the trace to collect data about specific events.</span></span> <span data-ttu-id="f84f6-153">您也可以排除不符合情況的事件。</span><span class="sxs-lookup"><span data-stu-id="f84f6-153">You can also exclude events that do not apply to your situation.</span></span>  
  
## <a name="select-metrics-for-monitored-components"></a><span data-ttu-id="f84f6-154">選取受監視元件的標準</span><span class="sxs-lookup"><span data-stu-id="f84f6-154">Select Metrics for Monitored Components</span></span>  
 <span data-ttu-id="f84f6-155">識別要監視的元件之後，請決定您監視的元件標準。</span><span class="sxs-lookup"><span data-stu-id="f84f6-155">After identifying the components to monitor, determine the metrics for components you monitor.</span></span> <span data-ttu-id="f84f6-156">例如，選取要納入追蹤的事件之後，您可以選擇只包含事件的特定資料。</span><span class="sxs-lookup"><span data-stu-id="f84f6-156">For example, after selecting the events to include in a trace, you can choose to include only specific data about the events.</span></span> <span data-ttu-id="f84f6-157">將追蹤限制在與追蹤相關的資料上，可以將執行追蹤所需的系統資源減到最小。</span><span class="sxs-lookup"><span data-stu-id="f84f6-157">Limiting the trace to data that is relevant to the trace minimizes the system resources required to perform the tracing.</span></span>  
  
## <a name="monitor-the-server"></a><span data-ttu-id="f84f6-158">監視伺服器</span><span class="sxs-lookup"><span data-stu-id="f84f6-158">Monitor the Server</span></span>  
 <span data-ttu-id="f84f6-159">若要監視伺服器，請執行您已設定來蒐集資料的監視工具。</span><span class="sxs-lookup"><span data-stu-id="f84f6-159">To monitor the server, run the monitoring tool that you have configured to gather data.</span></span> <span data-ttu-id="f84f6-160">例如，定義追蹤之後，您可以執行追蹤來蒐集伺服器中所引發的事件之相關資料。</span><span class="sxs-lookup"><span data-stu-id="f84f6-160">For example, after a trace is defined, you can run the trace to gather data about events raised in the server.</span></span>  
  
## <a name="analyze-the-data"></a><span data-ttu-id="f84f6-161">分析資料</span><span class="sxs-lookup"><span data-stu-id="f84f6-161">Analyze the Data</span></span>  
 <span data-ttu-id="f84f6-162">完成追蹤之後，請分析資料，以查看是否已達到您的監視目標。</span><span class="sxs-lookup"><span data-stu-id="f84f6-162">After the trace has finished, analyze the data to see if you have achieved your monitoring goal.</span></span> <span data-ttu-id="f84f6-163">如果尚未達成，請修改您用來監視伺服器的元件或標準。</span><span class="sxs-lookup"><span data-stu-id="f84f6-163">If you have not, modify the components or metrics that you used to monitor the server.</span></span>  
  
 <span data-ttu-id="f84f6-164">以下概略說明擷取與使用事件資料的程序。</span><span class="sxs-lookup"><span data-stu-id="f84f6-164">The following outlines the process for capturing event data and putting it to use.</span></span>  
  
1.  <span data-ttu-id="f84f6-165">套用篩選來限制要收集的事件資料。</span><span class="sxs-lookup"><span data-stu-id="f84f6-165">Apply filters to limit the event data collected.</span></span>  
  
     <span data-ttu-id="f84f6-166">限制事件資料可讓系統把焦點放在監視案例相關的事件上。</span><span class="sxs-lookup"><span data-stu-id="f84f6-166">Limiting the event data allows for the system to focus on the events pertinent to the monitoring scenario.</span></span> <span data-ttu-id="f84f6-167">例如，若您要監視慢速查詢，可以使用篩選來限制只監視應用程式對特定資料庫執行超過三十秒以上的查詢。</span><span class="sxs-lookup"><span data-stu-id="f84f6-167">For example, if you want to monitor slow queries, you can use a filter to monitor only those queries issued by the application that take more than 30 seconds to run against a particular database.</span></span> <span data-ttu-id="f84f6-168">如需詳細資訊，請參閱[設定追蹤篩選 &#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md) 和[篩選追蹤中的事件 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="f84f6-168">For more information, see [Set a Trace Filter &#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md) and [Filter Events in a Trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md).</span></span>  
  
2.  <span data-ttu-id="f84f6-169">監視 (擷取) 事件。</span><span class="sxs-lookup"><span data-stu-id="f84f6-169">Monitor (capture) events.</span></span>  
  
     <span data-ttu-id="f84f6-170">一旦啟用後，使用中的監視會從指定的應用程式、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體或作業系統中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="f84f6-170">As soon as it is enabled, active monitoring captures data from the specified application, instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or operating system.</span></span> <span data-ttu-id="f84f6-171">例如，使用「系統監視器」監視磁碟活動時，監視會擷取磁碟讀寫動作等事件資料，並顯示在螢幕上。</span><span class="sxs-lookup"><span data-stu-id="f84f6-171">For example, when disk activity is monitored using System Monitor, monitoring captures event data, such as disk reads and writes, and displays it on the screen.</span></span> <span data-ttu-id="f84f6-172">如需詳細資訊，請參閱[監視資源使用狀況 &#40;系統監視器&#41;](../performance-monitor/monitor-resource-usage-system-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="f84f6-172">For more information, see [Monitor Resource Usage &#40;System Monitor&#41;](../performance-monitor/monitor-resource-usage-system-monitor.md).</span></span>  
  
3.  <span data-ttu-id="f84f6-173">儲存擷取的事件資料。</span><span class="sxs-lookup"><span data-stu-id="f84f6-173">Save captured event data.</span></span>  
  
     <span data-ttu-id="f84f6-174">儲存擷取的事件資料可讓您稍後分析，或甚至使用 Distributed Replay Utility 或 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]來重新執行。</span><span class="sxs-lookup"><span data-stu-id="f84f6-174">Saving captured event data lets you analyze it later or even replay it using the Distributed Replay Utility or [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="f84f6-175">您可將擷取的事件資料儲存到檔案，而檔案可以重新載入到原先建立該檔案的工具中，以進行分析。</span><span class="sxs-lookup"><span data-stu-id="f84f6-175">Captured event data is saved to a file that can be loaded back into the tool that originally created it for analysis.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="f84f6-176">允許將事件資料儲存到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="f84f6-176">permits event data to be saved to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="f84f6-177">在建立效能基準時，儲存擷取的事件資料就很重要。</span><span class="sxs-lookup"><span data-stu-id="f84f6-177">Saving captured event data is important when you are creating a performance baseline.</span></span> <span data-ttu-id="f84f6-178">效能基準資料會儲存起來，並在比較最近擷取的事件資料時使用，以判斷效能是否為最佳化。</span><span class="sxs-lookup"><span data-stu-id="f84f6-178">The performance baseline data is saved and used, when comparing recently captured event data, to determine whether performance is optimal.</span></span> <span data-ttu-id="f84f6-179">如需詳細資訊，請參閱 [SQL Server Profiler 範本和權限](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="f84f6-179">For more information, see [SQL Server Profiler Templates and Permissions](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md).</span></span>  
  
4.  <span data-ttu-id="f84f6-180">建立包含指定設定的追蹤範本來擷取事件。</span><span class="sxs-lookup"><span data-stu-id="f84f6-180">Create trace templates that contain the settings specified to capture the events.</span></span>  
  
     <span data-ttu-id="f84f6-181">追蹤範本中包含事件本身、事件資料和用來擷取資料的篩選等相關規格。</span><span class="sxs-lookup"><span data-stu-id="f84f6-181">Trace templates include specifications about the events themselves, event data, and filters that are used to capture data.</span></span> <span data-ttu-id="f84f6-182">這些範本稍後可以用來監視特定的事件組合，而不需重新定義事件、事件資料與篩選。</span><span class="sxs-lookup"><span data-stu-id="f84f6-182">These templates can be used to monitor a specific set of events later without redefining the events, event data, and filters.</span></span> <span data-ttu-id="f84f6-183">例如，如果您要時常監視死結的數目與陷入死結的使用者數目，您可以建立一個定義這些事件、事件資料與事件篩選的範本、儲存範本，然後在下次要監視死結時重新套用此篩選。</span><span class="sxs-lookup"><span data-stu-id="f84f6-183">For example, if you want to frequently monitor the number of deadlocks, and the users involved in those deadlocks, you can create a template defining those events, event data, and event filters; save the template; and reapply the filter the next time that you want to monitor deadlocks.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="f84f6-184">會針對這個目的使用追蹤範本。</span><span class="sxs-lookup"><span data-stu-id="f84f6-184">uses trace templates for this purpose.</span></span> <span data-ttu-id="f84f6-185">如需詳細資訊，請參閱[設定追蹤定義預設值 &#40;SQL Server Profiler & #41;](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md) 和[建立追蹤範本 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="f84f6-185">For more information, see [Set Trace Definition Defaults &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md) and [Create a Trace Template &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md).</span></span>  
  
5.  <span data-ttu-id="f84f6-186">分析擷取的事件資料。</span><span class="sxs-lookup"><span data-stu-id="f84f6-186">Analyze captured event data.</span></span>  
  
     <span data-ttu-id="f84f6-187">為了進行分析，擷取的事件資料會載入擷取資料的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="f84f6-187">To be analyzed, the captured event data is loaded into the application that captured the data.</span></span> <span data-ttu-id="f84f6-188">例如，從 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 擷取的追縱可以重新載入 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 中，以供檢視與分析。</span><span class="sxs-lookup"><span data-stu-id="f84f6-188">For example, a captured trace from [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] can be reloaded into [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] for viewing and analysis.</span></span> <span data-ttu-id="f84f6-189">如需詳細資訊，請參閱 [使用 SQL Server Profiler 檢視和分析追蹤](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="f84f6-189">For more information, see [View and Analyze Traces with SQL Server Profiler](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md).</span></span>  
  
     <span data-ttu-id="f84f6-190">分析事件資料涉及判斷發生何事與發生的原因。</span><span class="sxs-lookup"><span data-stu-id="f84f6-190">Analyzing event data involves determining what is occurring and why.</span></span> <span data-ttu-id="f84f6-191">這項資訊可讓您利用 Transact-SQL 陳述式或預存程序等 (視執行的分析類型而定)，執行變更以改善效能，例如增加更多記憶體、變更索引、修正程式碼問題。</span><span class="sxs-lookup"><span data-stu-id="f84f6-191">This information lets you make changes that can improve performance, such as adding more memory, changing indexes, correcting coding problems with Transact-SQL statements or stored procedures, and so on, depending on the type of analysis performed.</span></span> <span data-ttu-id="f84f6-192">例如，您可以使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor 來分析從 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 擷取的追蹤，並根據結果提供索引建議。</span><span class="sxs-lookup"><span data-stu-id="f84f6-192">For example, you can use the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor to analyze a captured trace from [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and make index recommendations based on the results.</span></span>  
  
6.  <span data-ttu-id="f84f6-193">重新執行擷取的事件資料。</span><span class="sxs-lookup"><span data-stu-id="f84f6-193">Replay captured event data.</span></span>  
  
     <span data-ttu-id="f84f6-194">事件重新執行可讓您仿造原先擷取資料的資料庫環境來建立測試副本，然後模擬原本發生在實際系統的狀況來重複執行擷取的事件。</span><span class="sxs-lookup"><span data-stu-id="f84f6-194">Event replay lets you establish a test copy of the database environment from which the data was captured, and then repeat the captured events as they occurred originally on the real system.</span></span> <span data-ttu-id="f84f6-195">只有 Distributed Replay Utility 或 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="f84f6-195">This capability is only available with the Distributed Replay Utility or [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="f84f6-196">您可以使用原本的發生速度、盡量加快 (用以驅策系統) 或甚至一次一個步驟來重新執行這些事件，以便在發生每個事件之後分析系統。</span><span class="sxs-lookup"><span data-stu-id="f84f6-196">You can replay the events at the same speed as they originally occurred, as fast as possible (to stress the system), or more likely, one step at a time (to analyze the system after each event has occurred).</span></span> <span data-ttu-id="f84f6-197">藉由在測試環境下分析確實的事件，可以避免損害實際系統。</span><span class="sxs-lookup"><span data-stu-id="f84f6-197">By analyzing the exact events in a test environment, you can prevent harm to the production system.</span></span> <span data-ttu-id="f84f6-198">如需詳細資訊，請參閱 [重新執行追蹤](../../tools/sql-server-profiler/replay-traces.md)。</span><span class="sxs-lookup"><span data-stu-id="f84f6-198">For more information, see [Replay Traces](../../tools/sql-server-profiler/replay-traces.md).</span></span>  
  
  
