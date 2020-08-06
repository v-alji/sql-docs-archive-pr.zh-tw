---
title: 使用 SQL Server Profiler 分析鎖死 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- process nodes [SQL Server Profiler]
- Profiler [SQL Server Profiler], deadlocks
- deadlocks [SQL Server], identifying cause
- resource nodes [SQL Server Profiler]
- graphs [SQL Server Profiler]
- SQL Server Profiler, deadlocks
- events [SQL Server], deadlocks
- edges [SQL Server Profiler]
ms.assetid: 72d6718f-501b-4ea6-b344-c0e653f19561
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3414cda74d75dbacf10ed98b6fc6d50da2feaa18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686613"
---
# <a name="analyze-deadlocks-with-sql-server-profiler"></a><span data-ttu-id="f06d4-102">使用 SQL Server Profiler 分析死結</span><span class="sxs-lookup"><span data-stu-id="f06d4-102">Analyze Deadlocks with SQL Server Profiler</span></span>
  <span data-ttu-id="f06d4-103">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 可識別死結的原因。</span><span class="sxs-lookup"><span data-stu-id="f06d4-103">Use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to identify the cause of a deadlock.</span></span> <span data-ttu-id="f06d4-104">SQL Server 中有兩個或兩個以上的執行緒 (或處理序)，因為某些資源集而產生循環相依性時，就會發生死結。</span><span class="sxs-lookup"><span data-stu-id="f06d4-104">A deadlock occurs when there is a cyclic dependency between two or more threads, or processes, for some set of resources within SQL Server.</span></span> <span data-ttu-id="f06d4-105">利用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，您可以建立一個用來記錄、重新執行和顯示死結事件的追蹤，以便進行分析。</span><span class="sxs-lookup"><span data-stu-id="f06d4-105">Using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can create a trace that records, replays, and displays deadlock events for analysis.</span></span>  
  
 <span data-ttu-id="f06d4-106">若要追蹤死結事件，請將 **Deadlock graph** 事件類別加入追蹤。</span><span class="sxs-lookup"><span data-stu-id="f06d4-106">To trace deadlock events, add the **Deadlock graph** event class to a trace.</span></span> <span data-ttu-id="f06d4-107">此事件類別會用死結相關處理序和物件的 XML 資料來擴展追蹤中的 **TextData** 資料行。</span><span class="sxs-lookup"><span data-stu-id="f06d4-107">This event class populates the **TextData** data column in the trace with XML data about the process and objects that are involved in the deadlock.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="f06d4-108">可將 XML 文件擷取至死結 XML (.xdl) 檔案，您稍後可在 SQL Server Management Studio 中檢視該檔案。</span><span class="sxs-lookup"><span data-stu-id="f06d4-108">can extract the XML document to a deadlock XML (.xdl) file which you can view later in SQL Server Management Studio.</span></span> <span data-ttu-id="f06d4-109">您可以設定 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ，將 **Deadlock graph** 事件擷取到單一檔案 (其中包含所有的 **Deadlock graph** 事件)，或將各個事件擷取到不同的檔案。</span><span class="sxs-lookup"><span data-stu-id="f06d4-109">You can configure [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to extract **Deadlock graph** events to a single file that contains all **Deadlock graph** events, or to separate files.</span></span> <span data-ttu-id="f06d4-110">這種擷取可以利用下列任一方法來完成：</span><span class="sxs-lookup"><span data-stu-id="f06d4-110">This extraction can be done in any of the following ways:</span></span>  
  
-   <span data-ttu-id="f06d4-111">在追蹤組態時，使用 [事件擷取設定]  索引標籤。請注意，您需在 [事件選取範圍]  索引標籤上選取 **Deadlock graph** 事件，這個索引標籤才會出現。</span><span class="sxs-lookup"><span data-stu-id="f06d4-111">At trace configuration time, using the **Events Extraction Settings** tab. Note that this tab does not appear until you select the **Deadlock graph** event on the **Events Selection** tab.</span></span>  
  
-   <span data-ttu-id="f06d4-112">使用 [檔案]  功能表上的 [擷取 SQL Server 事件]  選項。</span><span class="sxs-lookup"><span data-stu-id="f06d4-112">Using the **Extract SQL Server Events** option on the **File** menu.</span></span>  
  
-   <span data-ttu-id="f06d4-113">您也可以用滑鼠右鍵按一下特定事件，然後選擇 [擷取事件資料]  ，以擷取並儲存個別事件。</span><span class="sxs-lookup"><span data-stu-id="f06d4-113">Individual events can also be extracted and saved by right-clicking a specific event and choosing **Extract Event Data**.</span></span>  
  
## <a name="deadlock-graphs"></a><span data-ttu-id="f06d4-114">死結圖形</span><span class="sxs-lookup"><span data-stu-id="f06d4-114">Deadlock Graphs</span></span>  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="f06d4-115">和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 使用死結等待圖形 (deadlock wait-for graph) 來描述死結。</span><span class="sxs-lookup"><span data-stu-id="f06d4-115">and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] use a deadlock wait-for graph to describe a deadlock.</span></span> <span data-ttu-id="f06d4-116">死結等待圖形包含處理序節點、資源節點，以及代表處理序與資源之間關聯性的邊緣。</span><span class="sxs-lookup"><span data-stu-id="f06d4-116">The deadlock wait-for graph contains process nodes, resource nodes, and edges representing the relationships between the processes and the resources.</span></span> <span data-ttu-id="f06d4-117">等待圖形的元件定義如下表所示：</span><span class="sxs-lookup"><span data-stu-id="f06d4-117">The components of wait-for graphs are defined in the following table:</span></span>  
  
 <span data-ttu-id="f06d4-118">處理序節點</span><span class="sxs-lookup"><span data-stu-id="f06d4-118">Process node</span></span>  
 <span data-ttu-id="f06d4-119">執行工作的執行緒；例如，INSERT、UPDATE 或 DELETE。</span><span class="sxs-lookup"><span data-stu-id="f06d4-119">A thread that performs a task; for example, INSERT, UPDATE, or DELETE.</span></span>  
  
 <span data-ttu-id="f06d4-120">資源節點</span><span class="sxs-lookup"><span data-stu-id="f06d4-120">Resource node</span></span>  
 <span data-ttu-id="f06d4-121">資料庫物件；例如，資料表、索引或資料列。</span><span class="sxs-lookup"><span data-stu-id="f06d4-121">A database object; for example, a table, index, or row.</span></span>  
  
 <span data-ttu-id="f06d4-122">Edge</span><span class="sxs-lookup"><span data-stu-id="f06d4-122">Edge</span></span>  
 <span data-ttu-id="f06d4-123">處理序與資源之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="f06d4-123">A relationship between a process and a resource.</span></span> <span data-ttu-id="f06d4-124">當處理序等待資源時，會發生 `request` 邊緣；</span><span class="sxs-lookup"><span data-stu-id="f06d4-124">A `request` edge occurs when a process waits for a resource.</span></span> <span data-ttu-id="f06d4-125">當資源等待處理序時，則會發生 `owner` 邊緣。</span><span class="sxs-lookup"><span data-stu-id="f06d4-125">An `owner` edge occurs when a resource waits for a process.</span></span> <span data-ttu-id="f06d4-126">邊緣描述中也會納入鎖定模式，</span><span class="sxs-lookup"><span data-stu-id="f06d4-126">The lock mode is included in the edge description.</span></span> <span data-ttu-id="f06d4-127">例如，**模式：X**。</span><span class="sxs-lookup"><span data-stu-id="f06d4-127">For example, **Mode: X**.</span></span>  
  
## <a name="deadlock-process-node"></a><span data-ttu-id="f06d4-128">死結處理序節點</span><span class="sxs-lookup"><span data-stu-id="f06d4-128">Deadlock Process Node</span></span>  
 <span data-ttu-id="f06d4-129">在等待圖形中，處理序節點包含處理序的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f06d4-129">In a wait-for graph, the process node contains information about the process.</span></span> <span data-ttu-id="f06d4-130">下表說明處理序的元件。</span><span class="sxs-lookup"><span data-stu-id="f06d4-130">The following table explains the components of a process.</span></span>  
  
|<span data-ttu-id="f06d4-131">元件</span><span class="sxs-lookup"><span data-stu-id="f06d4-131">Component</span></span>|<span data-ttu-id="f06d4-132">定義</span><span class="sxs-lookup"><span data-stu-id="f06d4-132">Definition</span></span>|  
|---------------|----------------|  
|<span data-ttu-id="f06d4-133">伺服器處理序識別碼</span><span class="sxs-lookup"><span data-stu-id="f06d4-133">Server process Id</span></span>|<span data-ttu-id="f06d4-134">伺服器處理序識別碼 (SPID)，伺服器指派給擁有鎖定之處理序的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f06d4-134">Server process identifier (SPID), a server assigned identifier for the process owning the lock.</span></span>|  
|<span data-ttu-id="f06d4-135">伺服器批次識別碼</span><span class="sxs-lookup"><span data-stu-id="f06d4-135">Server batch Id</span></span>|<span data-ttu-id="f06d4-136">伺服器批次識別碼 (SBID)。</span><span class="sxs-lookup"><span data-stu-id="f06d4-136">Server batch identifier (SBID).</span></span>|  
|<span data-ttu-id="f06d4-137">執行內容識別碼</span><span class="sxs-lookup"><span data-stu-id="f06d4-137">Execution context Id</span></span>|<span data-ttu-id="f06d4-138">執行內容識別碼 (ECID)。</span><span class="sxs-lookup"><span data-stu-id="f06d4-138">Execution context identifier (ECID).</span></span> <span data-ttu-id="f06d4-139">給定執行緒並和特定 SPID 關聯的執行內容識別碼。</span><span class="sxs-lookup"><span data-stu-id="f06d4-139">The execution context ID of a given thread associated with a specific SPID.</span></span><br /><br /> <span data-ttu-id="f06d4-140">ECID = {0, 1, 2, 3, ... *n*}，其中 0 一律代表主要或父執行緒，{1, 2, 3, ... *n*} 代表子執行緒。</span><span class="sxs-lookup"><span data-stu-id="f06d4-140">ECID = {0,1,2,3, *...n*}, where 0 always represents the main or parent thread, and {1,2,3, *...n*} represent the subthreads.</span></span>|  
|<span data-ttu-id="f06d4-141">死結優先權</span><span class="sxs-lookup"><span data-stu-id="f06d4-141">Deadlock priority</span></span>|<span data-ttu-id="f06d4-142">處理序的死結優先權。</span><span class="sxs-lookup"><span data-stu-id="f06d4-142">Deadlock priority for the process.</span></span> <span data-ttu-id="f06d4-143">如需可能值的詳細資訊，請參閱 [SET DEADLOCK_PRIORITY &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-deadlock-priority-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f06d4-143">For more information about possible values, see [SET DEADLOCK_PRIORITY &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-deadlock-priority-transact-sql).</span></span>|  
|<span data-ttu-id="f06d4-144">使用的記錄</span><span class="sxs-lookup"><span data-stu-id="f06d4-144">Log Used</span></span>|<span data-ttu-id="f06d4-145">處理序已使用的記錄檔空間量。</span><span class="sxs-lookup"><span data-stu-id="f06d4-145">Amount of log space used by the process.</span></span>|  
|<span data-ttu-id="f06d4-146">擁有者識別碼</span><span class="sxs-lookup"><span data-stu-id="f06d4-146">Owner Id</span></span>|<span data-ttu-id="f06d4-147">正在使用交易且目前正在等待鎖定之處理序的交易識別碼。</span><span class="sxs-lookup"><span data-stu-id="f06d4-147">Transaction ID for the processes which are using transactions and currently waiting on a lock.</span></span>|  
|<span data-ttu-id="f06d4-148">交易描述項</span><span class="sxs-lookup"><span data-stu-id="f06d4-148">Transaction descriptor</span></span>|<span data-ttu-id="f06d4-149">說明交易狀態之交易描述項的指標。</span><span class="sxs-lookup"><span data-stu-id="f06d4-149">Pointer to the transaction descriptor that describes the state of the transaction.</span></span>|  
|<span data-ttu-id="f06d4-150">輸入緩衝區</span><span class="sxs-lookup"><span data-stu-id="f06d4-150">Input buffer</span></span>|<span data-ttu-id="f06d4-151">目前處理序的輸入緩衝區，定義事件類型和正在執行的陳述式。</span><span class="sxs-lookup"><span data-stu-id="f06d4-151">Input buffer of the current process, defines the type of event and the statement being executed.</span></span> <span data-ttu-id="f06d4-152">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="f06d4-152">Possible values include:</span></span><br /><br /> <span data-ttu-id="f06d4-153">**語言**</span><span class="sxs-lookup"><span data-stu-id="f06d4-153">**Language**</span></span><br /><br /> <span data-ttu-id="f06d4-154">**RPC**</span><span class="sxs-lookup"><span data-stu-id="f06d4-154">**RPC**</span></span><br /><br /> <span data-ttu-id="f06d4-155">**None**</span><span class="sxs-lookup"><span data-stu-id="f06d4-155">**None**</span></span>|  
|<span data-ttu-id="f06d4-156">引數</span><span class="sxs-lookup"><span data-stu-id="f06d4-156">Statement</span></span>|<span data-ttu-id="f06d4-157">陳述式的類型。</span><span class="sxs-lookup"><span data-stu-id="f06d4-157">Type of statement.</span></span> <span data-ttu-id="f06d4-158">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="f06d4-158">Possible values are:</span></span><br /><br /> <span data-ttu-id="f06d4-159">**NOP**</span><span class="sxs-lookup"><span data-stu-id="f06d4-159">**NOP**</span></span><br /><br /> <span data-ttu-id="f06d4-160">**SELECT**</span><span class="sxs-lookup"><span data-stu-id="f06d4-160">**SELECT**</span></span><br /><br /> <span data-ttu-id="f06d4-161">**UPDATE**</span><span class="sxs-lookup"><span data-stu-id="f06d4-161">**UPDATE**</span></span><br /><br /> <span data-ttu-id="f06d4-162">**INSERT**</span><span class="sxs-lookup"><span data-stu-id="f06d4-162">**INSERT**</span></span><br /><br /> <span data-ttu-id="f06d4-163">**DELETE**</span><span class="sxs-lookup"><span data-stu-id="f06d4-163">**DELETE**</span></span><br /><br /> <span data-ttu-id="f06d4-164">**Unknown**</span><span class="sxs-lookup"><span data-stu-id="f06d4-164">**Unknown**</span></span>|  
  
## <a name="deadlock-resource-node"></a><span data-ttu-id="f06d4-165">死結資源節點</span><span class="sxs-lookup"><span data-stu-id="f06d4-165">Deadlock Resource Node</span></span>  
 <span data-ttu-id="f06d4-166">在死結中，有兩個處理序正在互相等待彼此所保留的資源。</span><span class="sxs-lookup"><span data-stu-id="f06d4-166">In a deadlock, two processes are each waiting for a resource held by the other process.</span></span> <span data-ttu-id="f06d4-167">在死結圖形中，資源會顯示為資源節點。</span><span class="sxs-lookup"><span data-stu-id="f06d4-167">In a deadlock graph, the resources are displayed as resource nodes.</span></span>  
  
  
