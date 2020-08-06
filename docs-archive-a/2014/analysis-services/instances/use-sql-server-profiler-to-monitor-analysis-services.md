---
title: 使用 SQL Server Profiler 來監視 Analysis Services |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- performance [Analysis Services], SQL Server Profiler
- Profiler [SQL Server Profiler], Analysis Services
ms.assetid: 8b77dafc-4584-4e93-8ad7-299304391bfd
author: minewiskan
ms.author: owend
ms.openlocfilehash: e144c1d858670f8a46b164ffc9885e6e082c4b0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592963"
---
# <a name="use-sql-server-profiler-to-monitor-analysis-services"></a><span data-ttu-id="e35e4-102">Use SQL Server Profiler to Monitor Analysis Services</span><span class="sxs-lookup"><span data-stu-id="e35e4-102">Use SQL Server Profiler to Monitor Analysis Services</span></span>
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="e35e4-103">會追蹤引擎處理事件 (例如批次或交易的開始) 和擷取關於這些事件的資料，如此可讓您監視伺服器和資料庫活動 (例如，使用者查詢或登入活動)。</span><span class="sxs-lookup"><span data-stu-id="e35e4-103">tracks engine process events, such as the start of a batch or a transaction, and it captures data about those events, thus enabling you to monitor server and database activity (for example, user queries or login activity).</span></span> <span data-ttu-id="e35e4-104">您可將 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 資料擷取至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表或檔案供稍後進行分析，也可以在相同或其他 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上重新執行擷取的事件以查看確實發生的狀況。</span><span class="sxs-lookup"><span data-stu-id="e35e4-104">You can capture [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] data to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or a file for later analysis, and you can also replay the events captured on the same or another [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance to see exactly what happened.</span></span> <span data-ttu-id="e35e4-105">您可以即時或逐步重新執行事件。</span><span class="sxs-lookup"><span data-stu-id="e35e4-105">You can replay events in real time or on a step-by-step basis.</span></span> <span data-ttu-id="e35e4-106">在相同電腦上執行追蹤事件以及 Performance 計數器也很有用。</span><span class="sxs-lookup"><span data-stu-id="e35e4-106">It is also very useful to run the trace events along with the Performance counters on the same machine.</span></span> <span data-ttu-id="e35e4-107">Profiler 可以依據時間建立這兩者的相互關聯，並沿著時間軸線將它們一起顯示。</span><span class="sxs-lookup"><span data-stu-id="e35e4-107">The profiler can correlate these two based on time and display them together along a single timeline.</span></span> <span data-ttu-id="e35e4-108">Performance 計數器提供的是彙總檢視，而追蹤事件則會提供詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e35e4-108">Trace events will give you more details while Performance counters give you an aggregate view.</span></span> <span data-ttu-id="e35e4-109">如需如何建立和執行追蹤的相關資訊，請參閱 [建立 Profiler 追蹤以重新執行 &#40;Analysis Services&#41;](create-profiler-traces-for-replay-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e35e4-109">For information about how to create and run traces, see [Create Profiler Traces for Replay &#40;Analysis Services&#41;](create-profiler-traces-for-replay-analysis-services.md).</span></span>  
  
 <span data-ttu-id="e35e4-110">下表描述此章節的主題。</span><span class="sxs-lookup"><span data-stu-id="e35e4-110">The following table describes the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e35e4-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="e35e4-111">In This Section</span></span>  
  
|<span data-ttu-id="e35e4-112">主題</span><span class="sxs-lookup"><span data-stu-id="e35e4-112">Topic</span></span>|<span data-ttu-id="e35e4-113">描述</span><span class="sxs-lookup"><span data-stu-id="e35e4-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e35e4-114">使用 SQL Server Profiler 監視 Analysis Services 簡介</span><span class="sxs-lookup"><span data-stu-id="e35e4-114">Introduction to Monitoring Analysis Services with SQL Server Profiler</span></span>](introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)|<span data-ttu-id="e35e4-115">描述如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 來監視 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="e35e4-115">Describes how to use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to monitor an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>|  
|[<span data-ttu-id="e35e4-116">建立 Profiler 追蹤以重新執行 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e35e4-116">Create Profiler Traces for Replay &#40;Analysis Services&#41;</span></span>](create-profiler-traces-for-replay-analysis-services.md)|<span data-ttu-id="e35e4-117">描述使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]建立重新執行之追蹤的需求。</span><span class="sxs-lookup"><span data-stu-id="e35e4-117">Describes the requirements for creating a trace for replay by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="e35e4-118">Analysis Services 追蹤事件</span><span class="sxs-lookup"><span data-stu-id="e35e4-118">Analysis Services Trace Events</span></span>](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)|<span data-ttu-id="e35e4-119">描述 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 事件類別。</span><span class="sxs-lookup"><span data-stu-id="e35e4-119">Describes [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] event classes.</span></span> <span data-ttu-id="e35e4-120">這些事件類別會對應到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 產生的動作，並用於追蹤重新執行。</span><span class="sxs-lookup"><span data-stu-id="e35e4-120">These event classes map to actions generated by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and are used for trace replays.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e35e4-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e35e4-121">See Also</span></span>  
 [<span data-ttu-id="e35e4-122">Monitor an Analysis Services Instance</span><span class="sxs-lookup"><span data-stu-id="e35e4-122">Monitor an Analysis Services Instance</span></span>](monitor-an-analysis-services-instance.md)  
  
  
