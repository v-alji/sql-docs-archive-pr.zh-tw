---
title: 記憶體最佳化資料表的還原與復原 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 294975b7-e7d1-491b-b66a-fdb1100d2acc
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5e702798ea68745a038407fb65af7726a5c5d50e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598375"
---
# <a name="restore-and-recovery-of-memory-optimized-tables"></a><span data-ttu-id="57e90-102">記憶體最佳化資料表的還原與復原</span><span class="sxs-lookup"><span data-stu-id="57e90-102">Restore and Recovery of Memory-Optimized Tables</span></span>
  <span data-ttu-id="57e90-103">復原或還原使用記憶體最佳化資料表之資料庫的基本機制，與僅使用磁碟資料表的資料庫類似。</span><span class="sxs-lookup"><span data-stu-id="57e90-103">The basic mechanism to recover or restore a database with memory-optimized tables is similar to databases with only disk-based tables.</span></span> <span data-ttu-id="57e90-104">但是與磁碟資料表不同之處在於，記憶體最佳化資料表必須載入記憶體中，資料庫才能供使用者存取。</span><span class="sxs-lookup"><span data-stu-id="57e90-104">But unlike disk-based tables, memory-optimized tables must be loaded into memory before database is available for user access.</span></span> <span data-ttu-id="57e90-105">這會在資料庫復原中加入一個新步驟。</span><span class="sxs-lookup"><span data-stu-id="57e90-105">This adds a new step in the database recovery.</span></span> <span data-ttu-id="57e90-106">資料庫復原中修改的步驟變更如下：</span><span class="sxs-lookup"><span data-stu-id="57e90-106">The modified steps in database recovery are changed as follows:</span></span>

 <span data-ttu-id="57e90-107">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 重新啟動時，每個資料庫都會經歷包括三個階段的復原階段：</span><span class="sxs-lookup"><span data-stu-id="57e90-107">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restarts, each database goes through a recovery phase that consists of the following three phases:</span></span>

1.  <span data-ttu-id="57e90-108">分析階段。</span><span class="sxs-lookup"><span data-stu-id="57e90-108">The analysis phase.</span></span> <span data-ttu-id="57e90-109">在這個階段中，使用中交易記錄上會進行一個行程，用以偵測認可和未認可的交易。</span><span class="sxs-lookup"><span data-stu-id="57e90-109">During this phase, a pass is made on the active transaction logs to detect committed and uncommitted transactions.</span></span> <span data-ttu-id="57e90-110">記憶體中 OLTP 引擎會識別要載入的檢查點，並預先載入其系統資料表記錄項目。</span><span class="sxs-lookup"><span data-stu-id="57e90-110">The In-Memory OLTP engine identifies the checkpoint to load and preloads its system table log entries.</span></span> <span data-ttu-id="57e90-111">另外還會處理一些檔案配置記錄檔記錄。</span><span class="sxs-lookup"><span data-stu-id="57e90-111">It will also process some file allocation log records.</span></span>

2.  <span data-ttu-id="57e90-112">重做階段。</span><span class="sxs-lookup"><span data-stu-id="57e90-112">The redo phase.</span></span> <span data-ttu-id="57e90-113">這個階段會在磁碟資料表和記憶體最佳化資料表上同時執行。</span><span class="sxs-lookup"><span data-stu-id="57e90-113">This phase is run concurrently on both disk-based and memory-optimized tables.</span></span>

     <span data-ttu-id="57e90-114">對於磁碟資料表，資料庫會移至目前的時間點，並取得未認可交易所採用的鎖定。</span><span class="sxs-lookup"><span data-stu-id="57e90-114">For disk-based tables, the database is moved to the current point in time and acquires locks taken by uncommitted transactions.</span></span>

     <span data-ttu-id="57e90-115">對於記憶體最佳化資料表，資料檔案和差異檔案組中的資料會載入記憶體中，然後根據上一個持久性檢查點更新使用中交易記錄的資料。</span><span class="sxs-lookup"><span data-stu-id="57e90-115">For memory-optimized tables, data from the data and delta file pairs are loaded into memory and then update the data with the active transaction log based on the last durable checkpoint.</span></span>

     <span data-ttu-id="57e90-116">上述在磁碟和記憶體最佳化資料表上的作業完成時，資料庫就可供存取。</span><span class="sxs-lookup"><span data-stu-id="57e90-116">When the above operations on disk-based and memory-optimized tables are complete, the database is available for access.</span></span>

3.  <span data-ttu-id="57e90-117">恢復階段。</span><span class="sxs-lookup"><span data-stu-id="57e90-117">The undo phase.</span></span> <span data-ttu-id="57e90-118">在這個階段中，未認可的交易會回復。</span><span class="sxs-lookup"><span data-stu-id="57e90-118">In this phase, the uncommitted transactions are rolled back.</span></span>

 <span data-ttu-id="57e90-119">將記憶體最佳化資料表載入記憶體中可能會影響復原時間目標 (RTO) 的效能。</span><span class="sxs-lookup"><span data-stu-id="57e90-119">Loading memory-optimized tables into memory can affect performance of the recovery time objective (RTO).</span></span> <span data-ttu-id="57e90-120">為了改善從資料和差異檔案載入記憶體最佳化資料的時間，記憶體中 OLTP 引擎會平行載入資料/差異檔案，如下所示：</span><span class="sxs-lookup"><span data-stu-id="57e90-120">To improve the load time of memory-optimized data from data and delta files, the In-Memory OLTP engine loads the data/delta files in parallel as follows:</span></span>

-   <span data-ttu-id="57e90-121">建立差異對應篩選。</span><span class="sxs-lookup"><span data-stu-id="57e90-121">Creating a Delta Map Filter.</span></span> <span data-ttu-id="57e90-122">差異檔案會儲存已刪除資料列的參考。</span><span class="sxs-lookup"><span data-stu-id="57e90-122">Delta files store references to the deleted rows.</span></span> <span data-ttu-id="57e90-123">每個容器會有一個執行緒讀取差異檔案，並建立差異對應篩選</span><span class="sxs-lookup"><span data-stu-id="57e90-123">One thread per container reads the delta files and creates a delta map filter.</span></span> <span data-ttu-id="57e90-124">(記憶體最佳化資料檔案群組可包含一個或多個容器)。</span><span class="sxs-lookup"><span data-stu-id="57e90-124">(A memory optimized data filegroup can have one or more containers.)</span></span>

-   <span data-ttu-id="57e90-125">將資料檔案做為資料流。</span><span class="sxs-lookup"><span data-stu-id="57e90-125">Streaming the data files.</span></span>  <span data-ttu-id="57e90-126">一旦建立差異對應篩選，就會使用與邏輯 CPU 數目相等的執行緒數目讀取資料檔案。</span><span class="sxs-lookup"><span data-stu-id="57e90-126">Once the delta-map filter is created, data files are read using as many threads as there are logical CPUs.</span></span> <span data-ttu-id="57e90-127">每個讀取資料檔案的執行緒都會讀取資料列、檢查相關聯的差異對應，並且只有在資料列未標示為已刪除時，才會將該資料列插入資料表。</span><span class="sxs-lookup"><span data-stu-id="57e90-127">Each thread reading the data file reads the data rows, checks the associated delta map and only inserts the row into table if this row has not been marked deleted.</span></span> <span data-ttu-id="57e90-128">在下述情況下，復原的這個部分可能繫於 CPU。</span><span class="sxs-lookup"><span data-stu-id="57e90-128">This part of recovery can be CPU bound in some cases as noted below.</span></span>

 <span data-ttu-id="57e90-129">![記憶體優化資料表。](../../database-engine/media/memory-optimized-tables.gif "記憶體最佳化資料表。")</span><span class="sxs-lookup"><span data-stu-id="57e90-129">![Memory-optimized tables.](../../database-engine/media/memory-optimized-tables.gif "Memory-optimized tables.")</span></span>

 <span data-ttu-id="57e90-130">記憶體最佳化資料表通常能夠以 I/O 速度載入記憶體中，但是在某些情況下將資料列載入記憶體中的速度會變慢。</span><span class="sxs-lookup"><span data-stu-id="57e90-130">Memory-optimized tables can generally be loaded into memory at the speed of I/O but there are cases when loading data rows into memory will be slower.</span></span> <span data-ttu-id="57e90-131">這些特定情況包括：</span><span class="sxs-lookup"><span data-stu-id="57e90-131">Specific cases are:</span></span>

-   <span data-ttu-id="57e90-132">雜湊索引的值區計數過低可能會導致過多衝突，造成插入資料列的速度變慢。</span><span class="sxs-lookup"><span data-stu-id="57e90-132">Low bucket count for hash index can lead to excessive collision causing data row inserts to be slower.</span></span> <span data-ttu-id="57e90-133">這種情況通常會導致整體 CPU 使用量變得非常高，尤其是接近復原結束時。</span><span class="sxs-lookup"><span data-stu-id="57e90-133">This generally results in very high CPU utilization throughout, and especially towards the end of recovery.</span></span> <span data-ttu-id="57e90-134">如果您已正確設定雜湊索引，它應該不會影響復原時間。</span><span class="sxs-lookup"><span data-stu-id="57e90-134">If you configured the hash index correctly, it should not impact the recovery time.</span></span>

-   <span data-ttu-id="57e90-135">具有一個或多個非叢集索引的大型記憶體最佳化資料表，它與值區計數大小已於建立時調整的雜湊索引不同，非叢集索引會動態成長，造成 CPU 使用量增加。</span><span class="sxs-lookup"><span data-stu-id="57e90-135">Large memory-optimized tables with one or more nonclustered indexes, unlike a hash index whose bucket count is sized at create time, the nonclustered indexes grow dynamically, resulting in high CPU utilization.</span></span>

## <a name="restoring-a-database-with-memory-optimized-tables"></a><span data-ttu-id="57e90-136">還原含有記憶體最佳化資料表的資料庫</span><span class="sxs-lookup"><span data-stu-id="57e90-136">Restoring a Database with Memory-optimized tables</span></span>
 <span data-ttu-id="57e90-137">您知道伺服器上有足夠的記憶體可還原資料庫，但資料庫所需記憶體的需求會佔用現有資源集區的一部分。</span><span class="sxs-lookup"><span data-stu-id="57e90-137">You know that you have sufficient memory on the server to restore a database, but there's a requirement  that the memory needed by the database is accounted for as part of an existing Resource Pool.</span></span>  <span data-ttu-id="57e90-138">您知道您無法在資料庫存在之前建立資源集區的繫結，因此您會執行使用 WITH NORECOVERY 還原。</span><span class="sxs-lookup"><span data-stu-id="57e90-138">You know that you cannot create the binding to the resource pool before the database exists, so you perform the restore WITH NORECOVERY.</span></span>  <span data-ttu-id="57e90-139">這會造成資料庫磁碟映像的還原和資料庫的建立，但因為資料庫尚未連線，所以不會用到記憶體內部 OLTP 記憶體。</span><span class="sxs-lookup"><span data-stu-id="57e90-139">This causes the disk image of the database to be restored and the database to be created, but no In-Memory OLTP memory is consumed because the database is not brought online.</span></span>

 <span data-ttu-id="57e90-140">到目前為止，您可以建立資源集區與資料庫的繫結，然後使用 WITH RECOVERY 還原將已還原的資料庫連線。</span><span class="sxs-lookup"><span data-stu-id="57e90-140">At this point, you can create the Resource Pool to Database binding, and then use RESTORE WITH RECOVERY to bring the restored database online.</span></span>  <span data-ttu-id="57e90-141">由於是在資料庫連線之前發生繫結，因此會適當地佔用記憶體內部 OLTP 記憶體耗用量。</span><span class="sxs-lookup"><span data-stu-id="57e90-141">Since the binding is in place before the database is brought online, its In-Memory OLTP memory consumption is properly accounted for.</span></span> <span data-ttu-id="57e90-142">這只需要還原一次資料庫即可。</span><span class="sxs-lookup"><span data-stu-id="57e90-142">This requires restoring the database only once.</span></span> <span data-ttu-id="57e90-143">第一個 RESTORE 命令是參考用的命令，只會讀取備份標頭，而最後一個命令會在無需實際還原任何位元的情況下觸發復原。</span><span class="sxs-lookup"><span data-stu-id="57e90-143">The first RESTORE command is an informational command that only reads the backup header, and the last command simply triggers recovery without actually restoring any bits.</span></span>

## <a name="see-also"></a><span data-ttu-id="57e90-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57e90-144">See Also</span></span>
 [<span data-ttu-id="57e90-145">備份、還原及復原記憶體最佳化資料表</span><span class="sxs-lookup"><span data-stu-id="57e90-145">Backup, Restore, and Recovery of Memory-Optimized Tables</span></span>](memory-optimized-tables.md)


