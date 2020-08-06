---
title: SQL Server Profiler-重新執行設定 (基本重新執行選項) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.generaloptions.f1
helpviewer_keywords:
- Replay Configuration dialog box
ms.assetid: 85a1dec6-9bbc-477a-86c5-b463db9ebb31
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cbf433c3108294909d91f7860136c0755b39b46f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705366"
---
# <a name="sql-server-profiler---replay-configuration-basic-replay-options"></a><span data-ttu-id="debe9-102">SQL Server Profiler - 重新執行組態 (基本重新執行選項)</span><span class="sxs-lookup"><span data-stu-id="debe9-102">SQL Server Profiler - Replay Configuration (Basic Replay Options)</span></span>
  <span data-ttu-id="debe9-103">在 **[重新執行組態]** 對話方塊中，使用 **[基本重新執行選項]** 頁面來指定如何重新執行追蹤檔案或資料表。</span><span class="sxs-lookup"><span data-stu-id="debe9-103">In the **Replay Configuration** dialog box, use the **Basic Replay Options** page to specify how to replay a trace file or table.</span></span>  
  
 <span data-ttu-id="debe9-104">若要檢視這個視窗，請使用 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 開啟包含用以重新執行的適當事件之追蹤檔案或資料表。</span><span class="sxs-lookup"><span data-stu-id="debe9-104">To view this window, use [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] to open a trace file or table that contains the appropriate events for replay.</span></span> <span data-ttu-id="debe9-105">如需詳細資訊，請參閱 [Replay Requirements](../tools/sql-server-profiler/replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="debe9-105">For more information, see [Replay Requirements](../tools/sql-server-profiler/replay-requirements.md).</span></span> <span data-ttu-id="debe9-106">在追蹤檔案或資料表開啟期間，請在 **[重新執行]** 功能表上按一下 **[啟動]**，然後連接到想要重新執行追蹤的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="debe9-106">While the trace file or table is open, on the **Replay** menu, click **Start**, and then connect to the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] where you want to replay the trace.</span></span>  
  
## <a name="options"></a><span data-ttu-id="debe9-107">選項</span><span class="sxs-lookup"><span data-stu-id="debe9-107">Options</span></span>  
 <span data-ttu-id="debe9-108">**重新執行伺服器**</span><span class="sxs-lookup"><span data-stu-id="debe9-108">**Replay server**</span></span>  
 <span data-ttu-id="debe9-109">顯示要連接以重新執行的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="debe9-109">Displays the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to connect to for the replay.</span></span>  
  
 <span data-ttu-id="debe9-110">**變更 .。。**</span><span class="sxs-lookup"><span data-stu-id="debe9-110">**Change...**</span></span>  
 <span data-ttu-id="debe9-111">啟動 [連接到伺服器]\*\*\*\* 對話方塊，以連接到另一部伺服器。</span><span class="sxs-lookup"><span data-stu-id="debe9-111">Launches the **Connect to Server** dialog box to connect to another server.</span></span>  
  
 <span data-ttu-id="debe9-112">**儲存至檔案**</span><span class="sxs-lookup"><span data-stu-id="debe9-112">**Save to file**</span></span>  
 <span data-ttu-id="debe9-113">將重新執行結果儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="debe9-113">Save the replay results to a file.</span></span> [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] <span data-ttu-id="debe9-114">會顯示標準檔案對話方塊，您可以在此指定檔案的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="debe9-114">displays the standard file dialog, where you can specify the location to save the file.</span></span>  
  
 <span data-ttu-id="debe9-115">**儲存至資料表**</span><span class="sxs-lookup"><span data-stu-id="debe9-115">**Save to table**</span></span>  
 <span data-ttu-id="debe9-116">將重新執行結果儲存至資料表。</span><span class="sxs-lookup"><span data-stu-id="debe9-116">Save the replay results to a table.</span></span> [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] <span data-ttu-id="debe9-117">會顯示資料表選取項目對話方塊，您可以在此指定資料表的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="debe9-117">displays the table selection dialog, where you can specify the location to save the table.</span></span>  
  
 <span data-ttu-id="debe9-118">**重新執行執行緒的數目**</span><span class="sxs-lookup"><span data-stu-id="debe9-118">**Number of replay threads**</span></span>  
 <span data-ttu-id="debe9-119">指定要同時使用的重新執行執行緒的數目。</span><span class="sxs-lookup"><span data-stu-id="debe9-119">Specify the number of replay threads to use concurrently.</span></span> <span data-ttu-id="debe9-120">較高的數目會在重新執行期間消耗較多資源，但是重新執行速度較快而且更並行。</span><span class="sxs-lookup"><span data-stu-id="debe9-120">A higher number consumes more resources during replay, but replay is faster and more concurrent.</span></span>  
  
 <span data-ttu-id="debe9-121">**依照追蹤的順序重新執行事件**</span><span class="sxs-lookup"><span data-stu-id="debe9-121">**Replay events in the order they were traced**</span></span>  
 <span data-ttu-id="debe9-122">循序重新執行事件。</span><span class="sxs-lookup"><span data-stu-id="debe9-122">Replay events sequentially.</span></span> <span data-ttu-id="debe9-123">如果您正在重新執行追蹤以偵錯，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="debe9-123">Use this option if you are replaying a trace for debugging.</span></span>  
  
 <span data-ttu-id="debe9-124">**使用多執行緒重新執行事件**</span><span class="sxs-lookup"><span data-stu-id="debe9-124">**Replay events using multiple threads**</span></span>  
 <span data-ttu-id="debe9-125">並行重新執行事件。</span><span class="sxs-lookup"><span data-stu-id="debe9-125">Replay events concurrently.</span></span> <span data-ttu-id="debe9-126">此選項比循序重新執行事件還快，但是會停用偵錯。</span><span class="sxs-lookup"><span data-stu-id="debe9-126">This option is faster than replaying events sequentially, but disables debugging.</span></span> <span data-ttu-id="debe9-127">事件會依其系統處理序識別碼 (SPID) 來排序。</span><span class="sxs-lookup"><span data-stu-id="debe9-127">The events are ordered within their system process identifiers (SPID).</span></span>  
  
 <span data-ttu-id="debe9-128">**顯示重新執行結果**</span><span class="sxs-lookup"><span data-stu-id="debe9-128">**Display replay results**</span></span>  
 <span data-ttu-id="debe9-129">在 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]中顯示重新執行結果。</span><span class="sxs-lookup"><span data-stu-id="debe9-129">Display replay results in [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="debe9-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="debe9-130">See Also</span></span>  
 <span data-ttu-id="debe9-131">[重新執行追蹤資料表 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="debe9-131">[Replay a Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="debe9-132">[重新執行追蹤檔案 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="debe9-132">[Replay a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="debe9-133">重新執行追蹤</span><span class="sxs-lookup"><span data-stu-id="debe9-133">Replay Traces</span></span>](../tools/sql-server-profiler/replay-traces.md)  
  
  
