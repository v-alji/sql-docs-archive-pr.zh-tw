---
title: 重新執行追蹤 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, replaying traces
- Run to Cursor option
- Toggle Breakpoint option
- traces [SQL Server], replaying
- replaying traces
- playback engine [SQL Server Profiler]
- events [SQL Server], replaying traces
- Profiler [SQL Server Profiler], replaying traces
ms.assetid: da958d3c-7f3e-44c9-aecc-8a9493bea7c0
author: stevestein
ms.author: sstein
ms.openlocfilehash: c485317d1343958f9c430b73d858130097d44d75
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705729"
---
# <a name="replay-traces"></a><span data-ttu-id="d1c26-102">重新執行追蹤</span><span class="sxs-lookup"><span data-stu-id="d1c26-102">Replay Traces</span></span>
  <span data-ttu-id="d1c26-103">重新執行是重現追蹤中已擷取之活動的能力。</span><span class="sxs-lookup"><span data-stu-id="d1c26-103">Replay is the ability to reproduce activity that has been captured in a trace.</span></span> <span data-ttu-id="d1c26-104">建立或編輯追蹤時，您可以將追蹤儲存至檔案，稍後重新執行它。</span><span class="sxs-lookup"><span data-stu-id="d1c26-104">When you create or edit a trace, you can save the trace to a file and replay it later.</span></span> <span data-ttu-id="d1c26-105">您可以使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ，從單一電腦重新執行追蹤活動。</span><span class="sxs-lookup"><span data-stu-id="d1c26-105">You can use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to replay trace activity from a single computer.</span></span> <span data-ttu-id="d1c26-106">如果是大型工作負載，請使用 Distributed Replay Utility，從多部電腦重新執行追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="d1c26-106">For large workloads, use the Distributed Replay Utility to replay trace data from multiple computers.</span></span>  
  
 <span data-ttu-id="d1c26-107">本節描述如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]的重新執行功能。</span><span class="sxs-lookup"><span data-stu-id="d1c26-107">This section describes how to use the replay features of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="d1c26-108">如需有關 Distributed Replay Utility 的詳細資訊，請參閱 [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md)。</span><span class="sxs-lookup"><span data-stu-id="d1c26-108">For more information about the Distributed Replay Utility, see [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md).</span></span>  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="d1c26-109">具有多執行緒播放引擎的功能，可以模擬使用者連線及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證。</span><span class="sxs-lookup"><span data-stu-id="d1c26-109">features a multithreaded playback engine that can simulate user connections and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="d1c26-110">重新執行在排解應用程式或處理序的疑難問題時很有用。</span><span class="sxs-lookup"><span data-stu-id="d1c26-110">Replay is useful to troubleshoot an application or process problem.</span></span> <span data-ttu-id="d1c26-111">當您找出問題並實作更正後，可以對已更正的應用程式或處理序，執行先前發現潛在問題的追蹤。</span><span class="sxs-lookup"><span data-stu-id="d1c26-111">When you have identified the problem and implemented corrections, run the trace that found the potential problem against the corrected application or process.</span></span> <span data-ttu-id="d1c26-112">然後，重新執行原始追蹤並比較結果。</span><span class="sxs-lookup"><span data-stu-id="d1c26-112">Then, replay the original trace and compare results.</span></span>  
  
 <span data-ttu-id="d1c26-113">追蹤重新執行支援以 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] [重新執行] 功能表上的 [切換中斷點] 和 [執行至資料指標處] 選項來進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="d1c26-113">Trace replay supports debugging by using the **Toggle Breakpoint** and the **Run to Cursor** options on the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Replay** menu.</span></span> <span data-ttu-id="d1c26-114">這些選項尤其能改善長指令碼的分析，因為可以將追蹤的重新執行分為數個短的區段，再以累加的方式進行分析。</span><span class="sxs-lookup"><span data-stu-id="d1c26-114">These options especially improve the analysis of long scripts because they can break the replay of the trace into short segments so they can be analyzed incrementally.</span></span>  
  
 <span data-ttu-id="d1c26-115">如需有關重新執行追蹤時所需之權限的詳細資訊，請參閱 [執行 SQL Server Profiler 所需的權限](permissions-required-to-run-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="d1c26-115">For information about the permissions required to replay traces, see [Permissions Required to Run SQL Server Profiler](permissions-required-to-run-sql-server-profiler.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d1c26-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="d1c26-116">In This Section</span></span>  
  
|<span data-ttu-id="d1c26-117">主題</span><span class="sxs-lookup"><span data-stu-id="d1c26-117">Topic</span></span>|<span data-ttu-id="d1c26-118">描述</span><span class="sxs-lookup"><span data-stu-id="d1c26-118">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d1c26-119">重新執行需求</span><span class="sxs-lookup"><span data-stu-id="d1c26-119">Replay Requirements</span></span>](replay-requirements.md)|<span data-ttu-id="d1c26-120">描述追蹤定義中必須包含哪些事件，才可以用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]重新執行。</span><span class="sxs-lookup"><span data-stu-id="d1c26-120">Describes the events that must be included in a trace definition so that it can be replayed with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="d1c26-121">重新執行選項 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="d1c26-121">Replay Options &#40;SQL Server Profiler&#41;</span></span>](replay-options-sql-server-profiler.md)|<span data-ttu-id="d1c26-122">描述您可以在 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 的 [重新執行組態] 對話方塊中設定的選項。</span><span class="sxs-lookup"><span data-stu-id="d1c26-122">Describes the options you can set in the **Replay Configuration** dialog box of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="d1c26-123">重新執行追蹤的考量 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="d1c26-123">Considerations for Replaying Traces &#40;SQL Server Profiler&#41;</span></span>](considerations-for-replaying-traces-sql-server-profiler.md)|<span data-ttu-id="d1c26-124">描述不能以 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 重新執行的追蹤事件，以及重新執行追蹤對伺服器效能的影響。</span><span class="sxs-lookup"><span data-stu-id="d1c26-124">Describes trace events that can not be replayed with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and the effects on server performance of replaying traces.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1c26-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1c26-125">See Also</span></span>  
 [<span data-ttu-id="d1c26-126">SQL Server Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="d1c26-126">SQL Server Distributed Replay</span></span>](../distributed-replay/sql-server-distributed-replay.md)  
  
  
