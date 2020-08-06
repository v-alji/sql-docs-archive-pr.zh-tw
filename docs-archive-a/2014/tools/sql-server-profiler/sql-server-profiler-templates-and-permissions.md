---
title: SQL Server Profiler 範本和權限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], about SQL Server Profiler
- SQL Server Profiler, about SQL Server Profiler
ms.assetid: 6d00378a-5d74-463b-9ed6-a2685306a9d2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8f3e3bc180db4e59def5af7eae39d8f177c93268
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592413"
---
# <a name="sql-server-profiler-templates-and-permissions"></a><span data-ttu-id="d6701-102">SQL Server Profiler 範本和權限</span><span class="sxs-lookup"><span data-stu-id="d6701-102">SQL Server Profiler Templates and Permissions</span></span>
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="d6701-103">顯示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如何在內部解析查詢。</span><span class="sxs-lookup"><span data-stu-id="d6701-103">shows how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resolves queries internally.</span></span> <span data-ttu-id="d6701-104">這可讓系統管理員確切地查看哪些 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式或「多維度運算式」已提交給伺服器，以及伺服器如何存取資料庫或 Cube，以傳回結果集。</span><span class="sxs-lookup"><span data-stu-id="d6701-104">This allows administrators to see exactly what [!INCLUDE[tsql](../../includes/tsql-md.md)] statements or Multi-Dimensional Expressions are submitted to the server and how the server accesses the database or cube to return result sets.</span></span>  
  
 <span data-ttu-id="d6701-105">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d6701-105">Using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can do the following:</span></span>  
  
-   <span data-ttu-id="d6701-106">建立根據可重複使用範本的追蹤</span><span class="sxs-lookup"><span data-stu-id="d6701-106">Create a trace that is based on a reusable template</span></span>  
  
-   <span data-ttu-id="d6701-107">在追蹤執行時監視追蹤結果</span><span class="sxs-lookup"><span data-stu-id="d6701-107">Watch the trace results as the trace runs</span></span>  
  
-   <span data-ttu-id="d6701-108">將追蹤結果儲存在資料表</span><span class="sxs-lookup"><span data-stu-id="d6701-108">Store the trace results in a table</span></span>  
  
-   <span data-ttu-id="d6701-109">視需要啟動、停止、暫停和修改追蹤結果</span><span class="sxs-lookup"><span data-stu-id="d6701-109">Start, stop, pause, and modify the trace results as necessary</span></span>  
  
-   <span data-ttu-id="d6701-110">重新執行追蹤結果</span><span class="sxs-lookup"><span data-stu-id="d6701-110">Replay the trace results</span></span>  
  
 <span data-ttu-id="d6701-111">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 時，只需監視您有興趣的事件。</span><span class="sxs-lookup"><span data-stu-id="d6701-111">Use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to monitor only the events in which you are interested.</span></span> <span data-ttu-id="d6701-112">如果追蹤變得太大，您可以根據所要的資訊加以篩選，以便只收集事件資料的子集。</span><span class="sxs-lookup"><span data-stu-id="d6701-112">If traces are becoming too large, you can filter them based on the information you want, so that only a subset of the event data is collected.</span></span> <span data-ttu-id="d6701-113">監視太多事件會增加伺服器與監視處理序的負擔，且會使得追蹤檔案或追蹤資料表增長過大，尤其是需要花費長時間的監視處理序更是如此。</span><span class="sxs-lookup"><span data-stu-id="d6701-113">Monitoring too many events adds overhead to the server and the monitoring process, and can cause the trace file or trace table to grow very large, especially when the monitoring process takes place over a long period of time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d6701-114">大於 1GB 的追蹤資料行值會傳回錯誤，並在追蹤輸出中截斷。</span><span class="sxs-lookup"><span data-stu-id="d6701-114">Trace column values greater than 1 GB return an error and are truncated in the trace output.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d6701-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="d6701-115">In This Section</span></span>  
  
|<span data-ttu-id="d6701-116">主題</span><span class="sxs-lookup"><span data-stu-id="d6701-116">Topic</span></span>|<span data-ttu-id="d6701-117">描述</span><span class="sxs-lookup"><span data-stu-id="d6701-117">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d6701-118">SQL Server Profiler 範本</span><span class="sxs-lookup"><span data-stu-id="d6701-118">SQL Server Profiler Templates</span></span>](sql-server-profiler-templates.md)|<span data-ttu-id="d6701-119">包含 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]隨附之預先定義追蹤範本的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d6701-119">Contains information about the predefined trace templates that ship with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="d6701-120">執行 SQL Server Profiler 所需的權限</span><span class="sxs-lookup"><span data-stu-id="d6701-120">Permissions Required to Run SQL Server Profiler</span></span>](permissions-required-to-run-sql-server-profiler.md)|<span data-ttu-id="d6701-121">包含執行 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]所需權限的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d6701-121">Contains information about the permissions that are required to run [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="d6701-122">儲存追蹤及追蹤範本</span><span class="sxs-lookup"><span data-stu-id="d6701-122">Save Traces and Trace Templates</span></span>](save-traces-and-trace-templates.md)|<span data-ttu-id="d6701-123">包含儲存追蹤輸出以及將追蹤定義儲存到範本的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d6701-123">Contains information about saving trace output and about saving trace definitions into a template.</span></span>|  
|[<span data-ttu-id="d6701-124">修改追蹤範本</span><span class="sxs-lookup"><span data-stu-id="d6701-124">Modify Trace Templates</span></span>](modify-trace-templates.md)|<span data-ttu-id="d6701-125">包含使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 或使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]修改追蹤範本的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d6701-125">Contains information about modifying trace templates by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>|  
|[<span data-ttu-id="d6701-126">啟動追蹤</span><span class="sxs-lookup"><span data-stu-id="d6701-126">Start a Trace</span></span>](start-a-trace.md)|<span data-ttu-id="d6701-127">包含當啟動、暫停或停止追蹤時所發生情況的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d6701-127">Contains information about what happens when you start, pause, or stop a trace.</span></span>|  
|[<span data-ttu-id="d6701-128">使追蹤與 Windows 效能記錄資料相互關聯</span><span class="sxs-lookup"><span data-stu-id="d6701-128">Correlate a Trace with Windows Performance Log Data</span></span>](correlate-a-trace-with-windows-performance-log-data.md)|<span data-ttu-id="d6701-129">包含使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler，讓 Windows 效能記錄資料與追蹤產生關聯的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d6701-129">Contains information about correlating Windows performance log data with a trace by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler.</span></span>|  
|[<span data-ttu-id="d6701-130">使用 SQL Server Profiler 檢視和分析追蹤</span><span class="sxs-lookup"><span data-stu-id="d6701-130">View and Analyze Traces with SQL Server Profiler</span></span>](view-and-analyze-traces-with-sql-server-profiler.md)|<span data-ttu-id="d6701-131">包含使用追蹤來進行資料的疑難排解、在追蹤中顯示物件名稱，以及在追蹤中尋找事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d6701-131">Contains information about using traces to troubleshoot data, displaying object names in a trace, and finding events in a trace.</span></span>|  
|[<span data-ttu-id="d6701-132">使用 SQL Server Profiler 分析死結</span><span class="sxs-lookup"><span data-stu-id="d6701-132">Analyze Deadlocks with SQL Server Profiler</span></span>](analyze-deadlocks-with-sql-server-profiler.md)|<span data-ttu-id="d6701-133">包含使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 來識別死結原因的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d6701-133">Contains information about using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to identify the cause of a deadlock.</span></span>|  
|[<span data-ttu-id="d6701-134">在 SQL Server Profiler 中使用 SHOWPLAN 結果分析查詢</span><span class="sxs-lookup"><span data-stu-id="d6701-134">Analyze Queries with SHOWPLAN Results in SQL Server Profiler</span></span>](analyze-queries-with-showplan-results-in-sql-server-profiler.md)|<span data-ttu-id="d6701-135">包含使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 來收集並顯示顯示計畫與顯示計畫統計結果的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d6701-135">Contains information about using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to collect and display Showplan and Showplan Statistics results.</span></span>|  
|[<span data-ttu-id="d6701-136">使用 SQL Server Profiler 篩選追蹤</span><span class="sxs-lookup"><span data-stu-id="d6701-136">Filter Traces with SQL Server Profiler</span></span>](filter-traces-with-sql-server-profiler.md)|<span data-ttu-id="d6701-137">包含使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]對資料行設定篩選，用來篩選追蹤輸出的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d6701-137">Contains information about setting filters on data columns to filter trace output by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="d6701-138">重新執行追蹤</span><span class="sxs-lookup"><span data-stu-id="d6701-138">Replay Traces</span></span>](replay-traces.md)|<span data-ttu-id="d6701-139">包含說明重新執行追蹤的意義，以及重新執行追蹤的必要條件等之相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d6701-139">Contains information that explains what replaying a trace means and what is required to replay a trace.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6701-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6701-140">See Also</span></span>  
 <span data-ttu-id="d6701-141">[[SQL Server Profiler]](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="d6701-141">[SQL Server Profiler](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="d6701-142">啟動 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="d6701-142">Start SQL Server Profiler</span></span>](start-sql-server-profiler.md)  
  
  
