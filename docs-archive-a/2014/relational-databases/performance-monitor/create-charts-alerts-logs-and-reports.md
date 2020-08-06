---
title: 建立圖表、警示、記錄和報表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- System Monitor [SQL Server], charts and reports
- charts [SQL Server]
- reports [SQL Server]
- reports [SQL Server], creating
- Windows System Monitor [SQL Server], charts and reports
- logs [SQL Server], System Monitor
- System Monitor [SQL Server], logs
- Windows System Monitor [SQL Server], logs
ms.assetid: c9162b37-e5dc-43d1-a3aa-1e9ebc69fecc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3a0c95c3f483a8af3e3e68d9c5c7d3caf44350d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707410"
---
# <a name="create-charts-alerts-logs-and-reports"></a><span data-ttu-id="f9fac-102">建立圖表、警示、記錄和報表</span><span class="sxs-lookup"><span data-stu-id="f9fac-102">Create Charts, Alerts, Logs, and Reports</span></span>
  <span data-ttu-id="f9fac-103">「系統監視器」可讓您建立圖表、警示、記錄和報表，以監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f9fac-103">System Monitor lets you create charts, alerts, logs, and reports to monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="charts"></a><span data-ttu-id="f9fac-104">圖表</span><span class="sxs-lookup"><span data-stu-id="f9fac-104">Charts</span></span>  
 <span data-ttu-id="f9fac-105">圖表可以監視所選取物件和計數器目前的效能；例如 CPU 使用量或磁碟 I/O。</span><span class="sxs-lookup"><span data-stu-id="f9fac-105">Charts can monitor the current performance of selected objects and counters; for example, the CPU usage or disk I/O.</span></span> <span data-ttu-id="f9fac-106">您可以在圖表中加入各種不同的系統監視器物件和計數器組合。</span><span class="sxs-lookup"><span data-stu-id="f9fac-106">You can add to a chart various combinations of System Monitor objects and counters.</span></span> <span data-ttu-id="f9fac-107">也可將 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 物件和計數器加入圖表。</span><span class="sxs-lookup"><span data-stu-id="f9fac-107">You also can add [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows objects and counters to a chart.</span></span>  
  
 <span data-ttu-id="f9fac-108">每個圖表都代表欲監視之資訊的子集合。</span><span class="sxs-lookup"><span data-stu-id="f9fac-108">Each chart represents a subset of information you want to monitor.</span></span> <span data-ttu-id="f9fac-109">例如一個圖表可追蹤記憶體使用狀況統計資料，第二個圖表可追蹤磁碟 I/O 統計資料。</span><span class="sxs-lookup"><span data-stu-id="f9fac-109">For example, one chart can track memory usage statistics and a second chart can track disk I/O statistics.</span></span>  
  
 <span data-ttu-id="f9fac-110">使用圖表有助於下列工作：</span><span class="sxs-lookup"><span data-stu-id="f9fac-110">Using a chart can be useful for the following tasks:</span></span>  
  
-   <span data-ttu-id="f9fac-111">研究為何某個電腦或應用程式很慢或沒有效率。</span><span class="sxs-lookup"><span data-stu-id="f9fac-111">Investigating why a computer or application is slow or inefficient.</span></span>  
  
-   <span data-ttu-id="f9fac-112">持續監視系統來找出間歇性的效能問題。</span><span class="sxs-lookup"><span data-stu-id="f9fac-112">Continually monitoring systems to find intermittent performance problems.</span></span>  
  
-   <span data-ttu-id="f9fac-113">找出為何需要增加容量的原因。</span><span class="sxs-lookup"><span data-stu-id="f9fac-113">Discovering why you need to increase capacity.</span></span>  
  
-   <span data-ttu-id="f9fac-114">將趨勢顯示成線條圖。</span><span class="sxs-lookup"><span data-stu-id="f9fac-114">Displaying a trend as a line chart.</span></span>  
  
-   <span data-ttu-id="f9fac-115">將比較資料顯示成分佈圖表。</span><span class="sxs-lookup"><span data-stu-id="f9fac-115">Displaying a comparison as a histogram chart.</span></span>  
  
 <span data-ttu-id="f9fac-116">圖表對於短期、即時地監視本地或遠端的電腦很有用，例如若要監視事件發生時的狀況。</span><span class="sxs-lookup"><span data-stu-id="f9fac-116">Charts are useful for short-term, real-time monitoring of a local or remote computer (for example, when you want to monitor an event as it occurs).</span></span>  
  
## <a name="alerts"></a><span data-ttu-id="f9fac-117">警示</span><span class="sxs-lookup"><span data-stu-id="f9fac-117">Alerts</span></span>  
 <span data-ttu-id="f9fac-118">使用警示，可讓「系統監視器」追蹤特定事件，並依要求在發生事件時進行通知。</span><span class="sxs-lookup"><span data-stu-id="f9fac-118">Using alerts, System Monitor tracks specific events and notifies you of these events as requested.</span></span> <span data-ttu-id="f9fac-119">警示記錄檔可在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，監視所選取計數器和物件執行個體的目前效能。</span><span class="sxs-lookup"><span data-stu-id="f9fac-119">An alert log can monitor the current performance of selected counters and instances for objects in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f9fac-120">如果計數器超出給定值，記錄檔便會記錄事件的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="f9fac-120">When a counter exceeds a given value, the log records the date and time of the event.</span></span> <span data-ttu-id="f9fac-121">事件也可以產生網路警示。</span><span class="sxs-lookup"><span data-stu-id="f9fac-121">An event can also generate a network alert.</span></span> <span data-ttu-id="f9fac-122">您可以在事件第一次發生或每次發生時，指定要執行的程式。</span><span class="sxs-lookup"><span data-stu-id="f9fac-122">You can have a specified program run the first time or every time an event occurs.</span></span> <span data-ttu-id="f9fac-123">例如，警示可以傳送網路訊息給所有系統管理員，告知 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的磁碟空間不足。</span><span class="sxs-lookup"><span data-stu-id="f9fac-123">For example, an alert can send a network message to all system administrators that the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is getting low on disk space.</span></span>  
  
## <a name="logs"></a><span data-ttu-id="f9fac-124">記錄</span><span class="sxs-lookup"><span data-stu-id="f9fac-124">Logs</span></span>  
 <span data-ttu-id="f9fac-125">記錄檔可讓您記錄選定物件和電腦的目前活動資訊，以供日後檢視與分析。</span><span class="sxs-lookup"><span data-stu-id="f9fac-125">Logs allow you to record information on the current activity of selected objects and computers for later viewing and analysis.</span></span> <span data-ttu-id="f9fac-126">您可將多個系統的資料收集到一個記錄檔內。</span><span class="sxs-lookup"><span data-stu-id="f9fac-126">You can collect data from multiple systems into a single log file.</span></span> <span data-ttu-id="f9fac-127">例如，您可以建立不同的記錄檔來累積各種電腦上選取物件的效能資訊，以供日後分析。</span><span class="sxs-lookup"><span data-stu-id="f9fac-127">For example, you can create different logs to accumulate information about the performance of selected objects on various computers for future analysis.</span></span> <span data-ttu-id="f9fac-128">您可將這些選取資料存到一個檔名底下，當您想要建立相似資訊的另一個記錄檔以進行比較時，就可重複使用它們。</span><span class="sxs-lookup"><span data-stu-id="f9fac-128">You can save these selections under a file name and reuse them when you want to create another log of similar information for comparison.</span></span>  
  
 <span data-ttu-id="f9fac-129">記錄檔提供許多資訊，可用於疑難排解或規劃上。</span><span class="sxs-lookup"><span data-stu-id="f9fac-129">Log files provide a wealth of information for troubleshooting or planning.</span></span> <span data-ttu-id="f9fac-130">目前活動的圖表、警示與報表可提供立即的回應，而記錄檔則可讓您長期追蹤計數器。</span><span class="sxs-lookup"><span data-stu-id="f9fac-130">Whereas charts, alerts, and reports on current activity provide instant feedback, log files enable you to track counters over a long period of time.</span></span> <span data-ttu-id="f9fac-131">因此，您可以更詳盡地檢查資訊，並記錄系統的效能。</span><span class="sxs-lookup"><span data-stu-id="f9fac-131">Thus, you can examine information more thoroughly and document system performance.</span></span>  
  
## <a name="reports"></a><span data-ttu-id="f9fac-132">報表</span><span class="sxs-lookup"><span data-stu-id="f9fac-132">Reports</span></span>  
 <span data-ttu-id="f9fac-133">報表可讓您顯示經常變動的計數器值以及所選取物件的執行個體值。</span><span class="sxs-lookup"><span data-stu-id="f9fac-133">Reports allow you to display constantly changing counter and instance values for selected objects.</span></span> <span data-ttu-id="f9fac-134">這些值出現在每個執行個體的資料行中。</span><span class="sxs-lookup"><span data-stu-id="f9fac-134">Values appear in columns for each instance.</span></span> <span data-ttu-id="f9fac-135">您可以調整報表的間隔，列印快照集，以及匯出資料。</span><span class="sxs-lookup"><span data-stu-id="f9fac-135">You can adjust report intervals, print snapshots, and export data.</span></span> <span data-ttu-id="f9fac-136">當您需要顯示原始數字時，請使用報表。</span><span class="sxs-lookup"><span data-stu-id="f9fac-136">Use reports when you need to display the raw numbers.</span></span>  
  
 <span data-ttu-id="f9fac-137">如需建立圖表、警示、記錄檔和報表的詳細資訊，以及 Windows 物件和計數器的詳細資訊，請參閱 Windows 文件集。</span><span class="sxs-lookup"><span data-stu-id="f9fac-137">For more information about creating charts, alerts, logs, and reports, or about Windows objects and counters, see the Windows documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9fac-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9fac-138">See Also</span></span>  
 [<span data-ttu-id="f9fac-139">監視資源使用狀況 &#40;System Monitor&#41;</span><span class="sxs-lookup"><span data-stu-id="f9fac-139">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
