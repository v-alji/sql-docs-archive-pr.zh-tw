---
title: 記憶體內部 OLTP 記憶體回收 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 940140a7-4785-46fc-8bf4-151435dccd3c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 23997d3664fb48902d2be08bbb22d2189c832298
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707562"
---
# <a name="in-memory-oltp-garbage-collection"></a><span data-ttu-id="f55a4-102">記憶體中的 OLTP 記憶體回收</span><span class="sxs-lookup"><span data-stu-id="f55a4-102">In-Memory OLTP Garbage Collection</span></span>
  <span data-ttu-id="f55a4-103">如果某個不再使用的交易刪除資料列，則該資料列視為過時。</span><span class="sxs-lookup"><span data-stu-id="f55a4-103">A data row is considered stale if it was deleted by a transaction that is no longer active.</span></span> <span data-ttu-id="f55a4-104">過時的資料列適合進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="f55a4-104">A stale row is eligible for garbage collection.</span></span> <span data-ttu-id="f55a4-105">以下是 [!INCLUDE[hek_2](../../includes/hek-2-md.md)]之記憶體回收的特性：</span><span class="sxs-lookup"><span data-stu-id="f55a4-105">The following are characteristics of garbage collection in [!INCLUDE[hek_2](../../includes/hek-2-md.md)]:</span></span>  
  
-   <span data-ttu-id="f55a4-106">非鎖定。</span><span class="sxs-lookup"><span data-stu-id="f55a4-106">Non-blocking.</span></span> <span data-ttu-id="f55a4-107">記憶體回收會隨著時間散發，藉此將對工作負載的影響降到最低。</span><span class="sxs-lookup"><span data-stu-id="f55a4-107">Garbage collection is distributed over time with minimal impact on the workload.</span></span>  
  
-   <span data-ttu-id="f55a4-108">合作式。</span><span class="sxs-lookup"><span data-stu-id="f55a4-108">Cooperative.</span></span> <span data-ttu-id="f55a4-109">使用者交易會參與記憶體回收與主要記憶體回收執行緒。</span><span class="sxs-lookup"><span data-stu-id="f55a4-109">User transactions participate in garbage collection with main garbage-collection thread.</span></span>  
  
-   <span data-ttu-id="f55a4-110">高效率。</span><span class="sxs-lookup"><span data-stu-id="f55a4-110">Efficient.</span></span> <span data-ttu-id="f55a4-111">使用者交易針對所使用之存取路徑 (索引) 中的過時資料列，會取消其連結。</span><span class="sxs-lookup"><span data-stu-id="f55a4-111">User transactions delink stale rows in the access path (the index) being used.</span></span> <span data-ttu-id="f55a4-112">這會減少最後移除資料列時所需進行的工作。</span><span class="sxs-lookup"><span data-stu-id="f55a4-112">This reduces the work required when the row is finally removed.</span></span>  
  
-   <span data-ttu-id="f55a4-113">主動回應。</span><span class="sxs-lookup"><span data-stu-id="f55a4-113">Responsive.</span></span> <span data-ttu-id="f55a4-114">記憶體不足的壓力會導致記憶體回收變得積極。</span><span class="sxs-lookup"><span data-stu-id="f55a4-114">Memory pressure leads to aggressive garbage collection.</span></span>  
  
-   <span data-ttu-id="f55a4-115">可擴充。</span><span class="sxs-lookup"><span data-stu-id="f55a4-115">Scalable.</span></span> <span data-ttu-id="f55a4-116">認可後，使用者交易會執行一部分的記憶體回收工作。</span><span class="sxs-lookup"><span data-stu-id="f55a4-116">After commit, user transactions do part of the work of garbage collection.</span></span> <span data-ttu-id="f55a4-117">交易活動越多，就有越多交易取消過時資料列的連結。</span><span class="sxs-lookup"><span data-stu-id="f55a4-117">The more transaction activity, the more the transactions delink stale rows.</span></span>  
  
 <span data-ttu-id="f55a4-118">記憶體回收是由主要記憶體回收執行緒所控制。</span><span class="sxs-lookup"><span data-stu-id="f55a4-118">Garbage collection is controlled by the main garbage collection thread.</span></span> <span data-ttu-id="f55a4-119">主要記憶體回收執行緒會每分鐘執行一次，或在認可的交易數目超出內部臨界值時執行。</span><span class="sxs-lookup"><span data-stu-id="f55a4-119">The main garbage collection thread runs every minute, or when the number of committed transactions exceeds an internal threshold.</span></span> <span data-ttu-id="f55a4-120">記憶體回收行程的工作是：</span><span class="sxs-lookup"><span data-stu-id="f55a4-120">The task of the garbage collector is to:</span></span>  
  
-   <span data-ttu-id="f55a4-121">識別已刪除或更新一組資料列並在最舊的使用中交易之前認可的交易。</span><span class="sxs-lookup"><span data-stu-id="f55a4-121">Identify transactions that have deleted or updated a set of rows and have committed before the oldest active transaction.</span></span>  
  
-   <span data-ttu-id="f55a4-122">識別這些舊交易所建立的資料列版本。</span><span class="sxs-lookup"><span data-stu-id="f55a4-122">Identity row versions created by these old transactions.</span></span>  
  
-   <span data-ttu-id="f55a4-123">將這些舊資料列分組為一個或多個單位，每個單位包含 16 個資料列。</span><span class="sxs-lookup"><span data-stu-id="f55a4-123">Group old rows into one or more units of 16 rows each.</span></span> <span data-ttu-id="f55a4-124">這樣做的目的在於將記憶體回收行程的工作分散到較小的單位。</span><span class="sxs-lookup"><span data-stu-id="f55a4-124">This is done to distribute the work of the garbage collector into smaller units.</span></span>  
  
-   <span data-ttu-id="f55a4-125">將這些工作單位逐一移至每個排程器的記憶體回收佇列中。</span><span class="sxs-lookup"><span data-stu-id="f55a4-125">Move these work units into the garbage collection queue, one for each scheduler.</span></span> <span data-ttu-id="f55a4-126">如需詳細資料，請參閱下列記憶體回收行程 DMV：[sys.dm_xtp_gc_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-stats-transact-sql)、[sys.dm_db_xtp_gc_cycle_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-gc-cycle-stats-transact-sql) 及 [sys.dm_xtp_gc_queue_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f55a4-126">Refer to the garbage collector DMVs for the details: [sys.dm_xtp_gc_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-stats-transact-sql), [sys.dm_db_xtp_gc_cycle_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-gc-cycle-stats-transact-sql), and [sys.dm_xtp_gc_queue_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql).</span></span>  
  
 <span data-ttu-id="f55a4-127">使用者交易在認可之後，會識別與其執行所在之排程器相關聯的所有佇列項目，然後釋出記憶體。</span><span class="sxs-lookup"><span data-stu-id="f55a4-127">After a user transaction commits, it identifies all queued items associated with the scheduler it ran on and then releases the memory.</span></span> <span data-ttu-id="f55a4-128">如果排程器上的記憶體回收佇列是空的，則它會搜尋目前 NUMA 節點中所有非空白的佇列。</span><span class="sxs-lookup"><span data-stu-id="f55a4-128">If the garbage collection queue on the scheduler is empty, it searches for any non-empty queue in the current NUMA node.</span></span> <span data-ttu-id="f55a4-129">如果發現交易活動較少且有記憶體不足的壓力，則主要記憶體回收執行緒可從任何佇列進行資料列的記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="f55a4-129">If there is low transactional activity and there is memory pressure, the main garbage-collection thread can access garbage collect rows from any queue.</span></span> <span data-ttu-id="f55a4-130">例如，如果刪除大量資料列之後沒有交易活動，而且沒有記憶體不足的壓力，則在交易活動繼續或發生記憶體不足的壓力之前，將不會對已刪除的資料列進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="f55a4-130">If there is no transactional activity after (for example) deleting a large number of rows and there is no memory pressure, the deleted rows will not be garbage collected until the transactional activity resumes or there is memory pressure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f55a4-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f55a4-131">See Also</span></span>  
 [<span data-ttu-id="f55a4-132">為記憶體內部 OLTP 管理記憶體</span><span class="sxs-lookup"><span data-stu-id="f55a4-132">Managing Memory for In-Memory OLTP</span></span>](../../database-engine/managing-memory-for-in-memory-oltp.md)  
  
  
