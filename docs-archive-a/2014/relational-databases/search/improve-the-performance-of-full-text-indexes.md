---
title: 改善全文檢索索引的效能 | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- performance [SQL Server], full-text search
- full-text queries [SQL Server], performance
- crawls [full-text search]
- full-text indexes [SQL Server], performance
- full-text search [SQL Server], performance
- batches [SQL Server], full-text search
ms.assetid: ef39ef1f-f0b7-4582-8e9c-31d4bd0ad35d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 51b5913e9c3ce65faa5a1fddc5846cc7c94d149f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702637"
---
# <a name="improve-the-performance-of-full-text-indexes"></a><span data-ttu-id="b4bf9-102">改善全文檢索索引的效能</span><span class="sxs-lookup"><span data-stu-id="b4bf9-102">Improve the Performance of Full-Text Indexes</span></span>
  <span data-ttu-id="b4bf9-103">全文檢索索引與全文檢索查詢的效能會受硬體資源的影響，例如記憶體、磁碟速度、CPU 速度與電腦架構。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-103">Performance for full-text indexing and full-text queries is influenced by hardware resources, such as memory, disk speed, CPU speed, and machine architecture.</span></span>  
  
##  <a name="common-causes-of-performance-issues"></a><a name="causes"></a><span data-ttu-id="b4bf9-104">效能問題的常見原因</span><span class="sxs-lookup"><span data-stu-id="b4bf9-104">Common Causes of Performance Issues</span></span>  
 <span data-ttu-id="b4bf9-105">全文檢索索引效能降低的主要原因即為硬體資源的限制：</span><span class="sxs-lookup"><span data-stu-id="b4bf9-105">The main cause for reduced full-text indexing performance is hardware-resource limits:</span></span>  
  
-   <span data-ttu-id="b4bf9-106">如果篩選背景程式主機處理序 (fdhost.exe) 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序 (sqlservr.exe) 的 CPU 使用率接近 100%，表示 CPU 就是瓶頸。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-106">If CPU usage by the filter daemon host process (fdhost.exe) or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process (sqlservr.exe) is close to 100 percent, the CPU is the bottleneck.</span></span>  
  
-   <span data-ttu-id="b4bf9-107">如果平均磁碟等候佇列長度超過磁碟讀寫頭數目的兩倍，表示磁碟有瓶頸。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-107">If the average disk-waiting queue length is more than two times the number of disk heads, there is a bottleneck on the disk.</span></span> <span data-ttu-id="b4bf9-108">主要的解決方式是建立和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫檔案和記錄分開的全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-108">The primary workaround is to create full-text catalogs that are separate from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database files and logs.</span></span> <span data-ttu-id="b4bf9-109">請將記錄、資料庫檔案和全文檢索目錄放在不同的磁碟上。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-109">Put the logs, database files, and full-text catalogs on separate disks.</span></span> <span data-ttu-id="b4bf9-110">購買較快速的磁碟以及使用 RAID 也有助於改善索引效能。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-110">Buying faster disks and using RAID can also help improve indexing performance.</span></span>  
  
-   <span data-ttu-id="b4bf9-111">如果實體記憶體 (3 GB 的限制) 不足，表示記憶體可能是瓶頸。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-111">If there is a shortage of physical memory (3-GB limit), memory might be the bottleneck.</span></span> <span data-ttu-id="b4bf9-112">實體記憶體限制可能會在所有系統上發生，而且在 32 位元系統上，虛擬記憶體不足的壓力可能會降低全文檢索索引的速度。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-112">Physical memory limitations are possible on all systems, and on 32-bit systems, virtual memory pressure can slow down full-text indexing.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b4bf9-113">從 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]開始，全文檢索引擎就可以使用 AWE 記憶體，因為全文檢索引擎屬於 sqlservr.exe 的一部分。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-113">Beginning in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the Full-Text Engine can use AWE memory because the Full-Text Engine is part of the sqlservr.exe.</span></span>  
  
 <span data-ttu-id="b4bf9-114">如果系統沒有任何硬體瓶頸，全文檢索搜尋的索引效能大多取決於下列條件：</span><span class="sxs-lookup"><span data-stu-id="b4bf9-114">If the system has no hardware bottlenecks, the indexing performance of full-text search mostly depends on the following:</span></span>  
  
-   <span data-ttu-id="b4bf9-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 建立全文檢索批次所花的時間。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-115">How long it takes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to create full-text batches.</span></span>  
  
-   <span data-ttu-id="b4bf9-116">篩選背景程式可以取用這些批次的速度。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-116">How quickly the filter daemon can consume those batches.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4bf9-117">與完整母體擴展不同，累加、手動和自動變更追蹤母體擴展並非設計來最大化硬體資源以達到更快的速度。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-117">Unlike full population, incremental, manual, and auto change tracking population are not designed to maximize hardware resources to achieve faster speed.</span></span> <span data-ttu-id="b4bf9-118">因此，這些微調建議可能無法增強全文檢索索引的效能。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-118">Therefore, these tuning suggestions may not enhance performance for full-text indexing.</span></span>  
  
 <span data-ttu-id="b4bf9-119">完成母體擴展後會觸發最後的合併程序，將索引片段合併成一個主要的全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-119">When a population has completed, a final merge process is triggered that merges the index fragments together into one master full-text index.</span></span> <span data-ttu-id="b4bf9-120">如此可提升查詢的效能，因為只需要查詢一個主索引而不需查詢數個索引片段，而且可使用較佳的計分系統來排定關聯順序。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-120">This results in improved query performance since only the master index needs to be queried rather than a number of index fragments, and better scoring statistics may be used for relevance ranking.</span></span> <span data-ttu-id="b4bf9-121">請注意，主要合併過程可能需要密集的磁碟 I/O，因為合併索引片段時必須讀寫大量的資料，但是不會阻止傳入的查詢。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-121">Note that the master merge can be I/O intensive, because large amounts of data must be written and read when index fragments are merged, though it does not block incoming queries.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b4bf9-122">主要合併大量資料可能會建立長時間執行的交易，並在檢查點期間延遲截斷交易記錄。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-122">Master merging a large amount of data can create a long running transaction, delaying truncation of the transaction log during checkpoint.</span></span> <span data-ttu-id="b4bf9-123">在此情況下，交易記錄可能會在完整復原模式下明顯成長。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-123">In this case, under the full recovery model, the transaction log might grow significantly.</span></span> <span data-ttu-id="b4bf9-124">最佳作法是確認您的異動記錄包含足夠的空間，可供長時間執行的異動使用，然後在使用完整復原模式的資料庫中，辨識大型全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-124">As a best practice, before reorganizing a large full-text index in a database that uses the full recovery model, ensure that your transaction log contains sufficient space for a long-running transaction.</span></span> <span data-ttu-id="b4bf9-125">如需詳細資訊，請參閱 [管理交易記錄檔的大小](../logs/manage-the-size-of-the-transaction-log-file.md)。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-125">For more information, see [Manage the Size of the Transaction Log File](../logs/manage-the-size-of-the-transaction-log-file.md).</span></span>  
  
  
  
##  <a name="tuning-the-performance-of-full-text-indexes"></a><a name="tuning"></a><span data-ttu-id="b4bf9-126">微調全文檢索索引的效能</span><span class="sxs-lookup"><span data-stu-id="b4bf9-126">Tuning the Performance of Full-Text Indexes</span></span>  
 <span data-ttu-id="b4bf9-127">若要將全文檢索索引的效能發揮至極限，請實作下列最佳作法：</span><span class="sxs-lookup"><span data-stu-id="b4bf9-127">To maximize the performance of your full-text indexes, implement the following best practices:</span></span>  
  
-   <span data-ttu-id="b4bf9-128">若要使用所有處理器或核心來達到最大值，請將[sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)' `max full-text crawl ranges` ' 設定為系統上的 cpu 數目。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-128">To use all processors or cores to the maximum, set [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)'`max full-text crawl ranges`' to the number of CPUs on the system.</span></span> <span data-ttu-id="b4bf9-129">此組態選項的相關資訊，請參閱 [全文檢索搜耙最大範圍伺服器組態選項](../../database-engine/configure-windows/max-full-text-crawl-range-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-129">For information about this configuration option, see [max full-text crawl range Server Configuration Option](../../database-engine/configure-windows/max-full-text-crawl-range-server-configuration-option.md).</span></span>  
  
-   <span data-ttu-id="b4bf9-130">請確定基底資料表具有叢集索引。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-130">Make sure that the base table has a clustered index.</span></span> <span data-ttu-id="b4bf9-131">對叢集索引的第一個資料行使用整數資料類型。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-131">Use an integer data type for the first column of the clustered index.</span></span> <span data-ttu-id="b4bf9-132">避免在叢集索引的第一個資料行使用 GUID。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-132">Avoid using GUIDs in the first column of the clustered index.</span></span> <span data-ttu-id="b4bf9-133">叢集索引的多重範圍母體擴展可能會產生最高的母體擴展速度。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-133">A multi-range population on a clustered index can produce the highest population speed.</span></span> <span data-ttu-id="b4bf9-134">我們建議當做全文檢索索引鍵的資料行應該是整數資料類型。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-134">We recommend that the column serving as the full-text key be an integer data type.</span></span>  
  
-   <span data-ttu-id="b4bf9-135">請使用 [UPDATE STATISTICS](/sql/t-sql/statements/update-statistics-transact-sql) 陳述式來更新基底資料表的統計資料。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-135">Update the statistics of the base table by using the [UPDATE STATISTICS](/sql/t-sql/statements/update-statistics-transact-sql) statement.</span></span> <span data-ttu-id="b4bf9-136">更重要的是，請更新叢集索引上的統計資料或完整母體擴展的全文檢索索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-136">More important, update the statistics on the clustered index or the full-text key for a full population.</span></span> <span data-ttu-id="b4bf9-137">這有助於多重範圍母體擴展在資料表上產生良好的資料分割。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-137">This helps a multi-range population to generate good partitions on the table.</span></span>  
  
-   <span data-ttu-id="b4bf9-138">如果您想要改善累加母體擴展的效能，請在 `timestamp` 資料行上建立次要索引。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-138">Build a secondary index on a `timestamp` column if you want to improve the performance of incremental population.</span></span>  
  
-   <span data-ttu-id="b4bf9-139">在大型的多重 CPU 電腦上執行完整母體擴展之前，我們建議您設定 `max server memory` 值來暫時限制緩衝集區的大小，以便保留足夠的記憶體供 fdhost.exe 處理序和作業系統使用。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-139">Before you perform a full population on a large multi-CPU computer, we recommend that you temporarily limit the size of the buffer pool by setting the `max server memory` value to leave enough memory for the fdhost.exe process and operating system use.</span></span> <span data-ttu-id="b4bf9-140">如需詳細資訊，請參閱本主題稍後的＜估計篩選背景程式主機處理序 (fdhost.exe) 的記憶體需求＞一節。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-140">For more information, see "Estimating the Memory Requirements of the Filter Daemon Host Process (fdhost.exe)," later in this topic.</span></span>  
  
  
  
##  <a name="troubleshooting-the-performance-of-full-populations"></a><a name="full"></a><span data-ttu-id="b4bf9-141">針對完整擴展的效能進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="b4bf9-141">Troubleshooting the Performance of Full Populations</span></span>  
 <span data-ttu-id="b4bf9-142">若要診斷效能問題，請查看全文檢索搜耙記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-142">To diagnose performance problems, look at the full-text crawl logs.</span></span> <span data-ttu-id="b4bf9-143">如需搜耙記錄檔的相關資訊，請參閱 [擴展全文檢索索引](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-143">For information about crawl logs, see [Populate Full-Text Indexes](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="b4bf9-144">如果您對於完整母體擴展的效能不滿意，建議您遵循下列疑難排解順序進行。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-144">It is recommended that the following order of troubleshooting be followed if the performance of full populations is not satisfactory.</span></span>  
  
### <a name="physical-memory-usage"></a><span data-ttu-id="b4bf9-145">實體記憶體使用量</span><span class="sxs-lookup"><span data-stu-id="b4bf9-145">Physical Memory Usage</span></span>  
 <span data-ttu-id="b4bf9-146">在全文檢索母體擴展期間，fdhost.exe 或 sqlservr.exe 可能會造成記憶體不足或用完記憶體。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-146">During a full-text population, it is possible for fdhost.exe or sqlservr.exe to run low on memory or to run out of memory.</span></span> <span data-ttu-id="b4bf9-147">如果全文檢索搜耙記錄檔顯示 fdhost.exe 經常重新啟動或者傳回錯誤碼 8007008，就表示其中一個處理序用完記憶體。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-147">If the full-text crawl log shows that fdhost.exe is being restarted often or that error code 8007008 is being returned it means one of these processes is running out of memory.</span></span> <span data-ttu-id="b4bf9-148">如果 fdhost.exe 正在產生傾印 (尤其是在大型的多重 CPU 電腦上)，它可能會用完記憶體。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-148">If fdhost.exe is producing dumps, particularly on large, multi-CPU computers, it might be running out of memory.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4bf9-149">請參閱 [sys.dm_fts_memory_buffers &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql)，以取得全文檢索搜耙所使用的記憶體緩衝區的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-149">To obtain information about memory buffers used by a full-text crawl, see [sys.dm_fts_memory_buffers &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql).</span></span>  
  
 <span data-ttu-id="b4bf9-150">可能的原因如下：</span><span class="sxs-lookup"><span data-stu-id="b4bf9-150">The possible causes are as follows:</span></span>  
  
-   <span data-ttu-id="b4bf9-151">如果完整母體擴展期間可用的實體記憶體數量為零，表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 緩衝集區可能耗用了系統上的大部分實體記憶體。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-151">If amount of physical memory that is available during a full population is zero, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] buffer pool might be consuming most of the physical memory on the system.</span></span>  
  
     <span data-ttu-id="b4bf9-152">sqlservr.exe 處理序嘗試擷取緩衝集區的所有可用記憶體，最多至已設定的最大伺服器記憶體。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-152">The sqlservr.exe process tries to grab all available memory for the buffer pool, up to the configured maximum server memory.</span></span> <span data-ttu-id="b4bf9-153">如果 `max server memory` 配置太大，fdhost.exe 處理序可能會發生記憶體不足以及無法配置共用記憶體的狀況。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-153">If the `max server memory` allocation is too large, out-of-memory conditions and failure to allocate shared memory can occur for the fdhost.exe process.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b4bf9-154">在多重 CPU 電腦上進行全文檢索母體擴展期間，fdhost.exe 或 sqlservr.exe 之間可能會發生競爭緩衝集區記憶體的情況。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-154">During a full-text population on a multi-CPU computer, contention for the buffer pool memory can occur between fdhost.exe or sqlservr.exe.</span></span> <span data-ttu-id="b4bf9-155">所產生的共用記憶體不足會導致批次重試、記憶體壓力以及 fdhost.exe 處理序的傾印。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-155">The resulting lack of shared memory causes batch retries, memory thrashing, and dumps by the fdhost.exe process.</span></span>  
  
     <span data-ttu-id="b4bf9-156">您可以透過適當地設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 緩衝集區的 `max server memory` 值，解決此問題。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-156">You can solve this problem by setting the `max server memory` value of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] buffer pool appropriately.</span></span> <span data-ttu-id="b4bf9-157">如需詳細資訊，請參閱本主題稍後的＜估計篩選背景程式主機處理序 (fdhost.exe) 的記憶體需求＞一節。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-157">For more information, see "Estimating the Memory Requirements of the Filter Daemon Host Process (fdhost.exe)," later in this topic.</span></span> <span data-ttu-id="b4bf9-158">減少全文檢索索引所使用的批次大小可能也會有所幫助。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-158">Reducing the batch size used for full-text indexing may also help.</span></span>  
  
-   <span data-ttu-id="b4bf9-159">分頁問題</span><span class="sxs-lookup"><span data-stu-id="b4bf9-159">A paging issue</span></span>  
  
     <span data-ttu-id="b4bf9-160">分頁檔大小不足 (例如，在具有成長受限之小型分頁檔的系統上) 可能也會導致 fdhost.exe 或 sqlservr.exe 用完記憶體。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-160">Insufficient page-file size, such as on a system that has a small page file with restricted growth, can also cause the fdhost.exe or sqlservr.exe to run out of memory.</span></span>  
  
     <span data-ttu-id="b4bf9-161">如果搜耙記錄檔並未指出任何記憶體相關的失敗，可能是由於過度分頁而導致效能降低。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-161">If the crawl logs do not indicate any memory-related failures, it is likely that performance is slow due to excessive paging.</span></span>  
  
  
  
### <a name="estimating-the-memory-requirements-of-the-filter-daemon-host-process-fdhostexe"></a><span data-ttu-id="b4bf9-162">估計篩選背景程式主機處理序 (fdhost.exe) 的記憶體需求</span><span class="sxs-lookup"><span data-stu-id="b4bf9-162">Estimating the Memory Requirements of the Filter Daemon Host Process (fdhost.exe)</span></span>  
 <span data-ttu-id="b4bf9-163">fdhost.exe 處理序進行母體擴展所需的記憶體數量主要取決於它所使用的全文檢索搜耙範圍數目、內部共用記憶體 (ISM) 的大小，以及 ISM 執行個體的數目上限。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-163">The amount of memory required by the fdhost.exe process for a population depends mainly on the number of full-text crawl ranges it uses, the size of inbound shared memory (ISM), and the maximum number of ISM instances.</span></span>  
  
 <span data-ttu-id="b4bf9-164">您可以使用下列公式來概略估計篩選背景程式主機所耗用的記憶體數量 (以位元組為單位)：</span><span class="sxs-lookup"><span data-stu-id="b4bf9-164">The amount of memory (in bytes) consumed by the filter daemon host can be roughly estimated by using the following formula:</span></span>  
  
 <span data-ttu-id="b4bf9-165">*number_of_crawl_ranges* \`ism_size '*max_outstanding_isms* \* 2</span><span class="sxs-lookup"><span data-stu-id="b4bf9-165">*number_of_crawl_ranges* \`ism_size\`*max_outstanding_isms*\* 2</span></span>  
  
 <span data-ttu-id="b4bf9-166">上述公式中變數的預設值如下所示：</span><span class="sxs-lookup"><span data-stu-id="b4bf9-166">The default values of the variables in the preceding formula are as follows:</span></span>  
  
|<span data-ttu-id="b4bf9-167">**變數**</span><span class="sxs-lookup"><span data-stu-id="b4bf9-167">**Variable**</span></span>|<span data-ttu-id="b4bf9-168">**預設值**</span><span class="sxs-lookup"><span data-stu-id="b4bf9-168">**Default value**</span></span>|  
|------------------|-----------------------|  
|<span data-ttu-id="b4bf9-169">*number_of_crawl_ranges*</span><span class="sxs-lookup"><span data-stu-id="b4bf9-169">*number_of_crawl_ranges*</span></span>|<span data-ttu-id="b4bf9-170">CPU 數目</span><span class="sxs-lookup"><span data-stu-id="b4bf9-170">The number of CPUs</span></span>|  
|<span data-ttu-id="b4bf9-171">*ism_size*</span><span class="sxs-lookup"><span data-stu-id="b4bf9-171">*ism_size*</span></span>|<span data-ttu-id="b4bf9-172">1 MB (適用於 x86 電腦)</span><span class="sxs-lookup"><span data-stu-id="b4bf9-172">1 MB for x86 computers</span></span><br /><br /> <span data-ttu-id="b4bf9-173">4 MB、8 MB 或 16MB (適用於 x64 電腦，端視實體記憶體總數而定)</span><span class="sxs-lookup"><span data-stu-id="b4bf9-173">4 MB, 8 MB, or 16MB for x64 computers, depending on the total physical memory</span></span>|  
|<span data-ttu-id="b4bf9-174">*max_outstanding_isms*</span><span class="sxs-lookup"><span data-stu-id="b4bf9-174">*max_outstanding_isms*</span></span>|<span data-ttu-id="b4bf9-175">25 (適用於 x86 電腦)</span><span class="sxs-lookup"><span data-stu-id="b4bf9-175">25 for x86 computers</span></span><br /><br /> <span data-ttu-id="b4bf9-176">5 (適用於 x64 電腦)</span><span class="sxs-lookup"><span data-stu-id="b4bf9-176">5 for x64 computers</span></span>|  
  
 <span data-ttu-id="b4bf9-177">下表將列出有關如何估計 fdhost.exe 記憶體需求的指導方針。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-177">The following table presents guidelines about how to estimate the memory requirements of fdhost.exe.</span></span> <span data-ttu-id="b4bf9-178">此表中的公式會使用下列值：</span><span class="sxs-lookup"><span data-stu-id="b4bf9-178">The formulas in this table use the following values:</span></span>  
  
-   <span data-ttu-id="b4bf9-179">*F*，這是 fdhost.exe 所需記憶體的估計 (以 MB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-179">*F*, which is an estimate of memory needed by fdhost.exe (in MB).</span></span>  
  
-   <span data-ttu-id="b4bf9-180">*T*，這是系統上可用的實體記憶體總計 (以 MB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-180">*T*, which is the total physical memory available on the system (in MB).</span></span>  
  
-   <span data-ttu-id="b4bf9-181">*M*，這是最佳 `max server memory` 設定。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-181">*M*, which is the optimal `max server memory` setting.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b4bf9-182">如需公式的基本資訊，請參閱下方的<sup>1</sup>、 <sup>2</sup>和<sup>3</sup>。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-182">For essential information about the formulas, see <sup>1</sup>, <sup>2</sup>, and <sup>3</sup>, below.</span></span>  
  
|<span data-ttu-id="b4bf9-183">平台</span><span class="sxs-lookup"><span data-stu-id="b4bf9-183">Platform</span></span>|<span data-ttu-id="b4bf9-184">估計 fdhost.exe 記憶體需求（MB）-*F*<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b4bf9-184">Estimating fdhost.exe memory requirements in MB-*F*<sup>1</sup></span></span>|<span data-ttu-id="b4bf9-185">計算最大伺服器記憶體的公式-*M*<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="b4bf9-185">Formula for calculating max server memory-*M*<sup>2</sup></span></span>|  
|--------------|---------------------------------------------------------------------|---------------------------------------------------------------|  
|<span data-ttu-id="b4bf9-186">x86</span><span class="sxs-lookup"><span data-stu-id="b4bf9-186">x86</span></span>|<span data-ttu-id="b4bf9-187">_F_ **=** **&#42;** 50_的爬網範圍數目_</span><span class="sxs-lookup"><span data-stu-id="b4bf9-187">_F_ **=** _Number of crawl ranges_ **&#42;** 50</span></span>|<span data-ttu-id="b4bf9-188">_M_ **= 最小 (** _T_ **，** 2000 **) *`F`* - -** 500</span><span class="sxs-lookup"><span data-stu-id="b4bf9-188">_M_ **=minimum(** _T_ **,** 2000 **)-*`F`*-** 500</span></span>|  
|<span data-ttu-id="b4bf9-189">x64</span><span class="sxs-lookup"><span data-stu-id="b4bf9-189">x64</span></span>|<span data-ttu-id="b4bf9-190">_F_ **=** _爬網範圍數_ **&#42;** 10 **&#42;** 8</span><span class="sxs-lookup"><span data-stu-id="b4bf9-190">_F_ **=** _Number of crawl ranges_ **&#42;** 10 **&#42;** 8</span></span>|<span data-ttu-id="b4bf9-191">_M_ **=** _T_ **-** _F_ **-** 500</span><span class="sxs-lookup"><span data-stu-id="b4bf9-191">_M_ **=** _T_ **-** _F_ **-** 500</span></span>|  
  
 <span data-ttu-id="b4bf9-192"><sup>1</sup>如果有多個完整擴展正在進行中，請分別計算每個的 fdhost.exe 記憶體需求，例如*F1*、 *F2*等。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-192"><sup>1</sup> If multiple full populations are in progress, calculate the fdhost.exe memory requirements of each separately, as *F1*, *F2*, and so forth.</span></span> <span data-ttu-id="b4bf9-193">然後將 *M* 計算為 _T_ **-** sigma **(** _F_i **)** 。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-193">Then calculate *M* as _T_**-** sigma **(**_F_i **)**.</span></span>  
  
 <span data-ttu-id="b4bf9-194"><sup>2</sup> 500 MB 是系統中其他進程所需記憶體的估計。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-194"><sup>2</sup> 500 MB is an estimate of the memory required by other processes in the system.</span></span> <span data-ttu-id="b4bf9-195">如果系統正在進行其他工作，請據此增加這個值。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-195">If the system is doing additional work, increase this value accordingly.</span></span>  
  
 <span data-ttu-id="b4bf9-196"><sup>3</sup> 。x64 平臺的*ism_size*假設為 8 MB。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-196"><sup>3</sup> .*ism_size* is assumed to be 8 MB for x64 platforms.</span></span>  
  
 <span data-ttu-id="b4bf9-197">**範例：估計 fdhost.exe 的記憶體需求**</span><span class="sxs-lookup"><span data-stu-id="b4bf9-197">**Example: Estimating the Memory Requirements of fdhost.exe**</span></span>  
  
 <span data-ttu-id="b4bf9-198">這個範例適用於具有 8GM RAM 和 4 個雙核心處理器的 AMD64 電腦。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-198">This example is for an AMD64 computer that has 8GM of RAM and 4 dual core processors.</span></span> <span data-ttu-id="b4bf9-199">第一個計算會估計 fdhost.exe 所需的記憶體-*F*。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-199">The first calculation estimates of memory needed by fdhost.exe-*F*.</span></span> <span data-ttu-id="b4bf9-200">搜耙範圍的數目是 `8`。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-200">The number of crawl ranges is `8`.</span></span>  
  
 `F = 8*10*8=640`  
  
 <span data-ttu-id="b4bf9-201">下一個計算會取得 M 的最佳值 `max server memory` - \* \*。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-201">The next calculation obtains the optimal value for `max server memory`-*M*.</span></span> <span data-ttu-id="b4bf9-202">此系統上可用的實體記憶體總計（以 MB 為*單位）為* *t* `8192` 。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-202">*T*he total physical memory available on this system in MB-*T*-is `8192`.</span></span>  
  
 `M = 8192-640-500=7052`  
  
 <span data-ttu-id="b4bf9-203">**範例：設定最大伺服器記憶體**</span><span class="sxs-lookup"><span data-stu-id="b4bf9-203">**Example: Setting max server memory**</span></span>  
  
 <span data-ttu-id="b4bf9-204">這個範例會使用[sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)並[重新](/sql/t-sql/language-elements/reconfigure-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] 設定語句，將設 `max server memory` 為上述範例中為*M*計算的值， `7052` 如下所示：</span><span class="sxs-lookup"><span data-stu-id="b4bf9-204">This example uses the [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) and [RECONFIGURE](/sql/t-sql/language-elements/reconfigure-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statements to set `max server memory` to the value calculated for *M* in the preceding example, `7052`:</span></span>  
  
```  
USE master;  
GO  
EXEC sp_configure 'max server memory', 7052;  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="b4bf9-205">**設定最大伺服器記憶體組態選項**</span><span class="sxs-lookup"><span data-stu-id="b4bf9-205">**To set the max server memory configuration option**</span></span>  
  
-   [<span data-ttu-id="b4bf9-206">伺服器記憶體伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="b4bf9-206">Server Memory Server Configuration Options</span></span>](../../database-engine/configure-windows/server-memory-server-configuration-options.md)  
  
  
  
### <a name="factors-that-can-reduce-cpu-consumption"></a><span data-ttu-id="b4bf9-207">可能會降低 CPU 耗用率的因素</span><span class="sxs-lookup"><span data-stu-id="b4bf9-207">Factors that Can Reduce CPU Consumption</span></span>  
 <span data-ttu-id="b4bf9-208">當平均 CPU 耗用率大約低 30% 時，我們會預期完整母體擴展的效能並非最佳化。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-208">We expect that the performance of full populations is not optimal when the average CPU consumption is lower than about 30 percent.</span></span> <span data-ttu-id="b4bf9-209">本節將討論影響 CPU 耗用率的某些因素。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-209">This section discusses some factors that affect CPU consumption.</span></span>  
  
-   <span data-ttu-id="b4bf9-210">等候分頁的時間很高</span><span class="sxs-lookup"><span data-stu-id="b4bf9-210">High wait for pages</span></span>  
  
     <span data-ttu-id="b4bf9-211">若要了解分頁等候時間是否很高，請執行下列 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="b4bf9-211">To find out whether a page wait time is high, execute the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    Execute SELECT TOP 10 * FROM sys.dm_os_wait_stats ORDER BY wait_time_ms DESC;  
    ```  
  
     <span data-ttu-id="b4bf9-212">下表將說明在此重要的等候類型。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-212">The following table describes the wait types of interest here.</span></span>  
  
    |<span data-ttu-id="b4bf9-213">等候類型</span><span class="sxs-lookup"><span data-stu-id="b4bf9-213">Wait type</span></span>|<span data-ttu-id="b4bf9-214">描述</span><span class="sxs-lookup"><span data-stu-id="b4bf9-214">Description</span></span>|<span data-ttu-id="b4bf9-215">可能的解決方案</span><span class="sxs-lookup"><span data-stu-id="b4bf9-215">Possible resolution</span></span>|  
    |---------------|-----------------|-------------------------|  
    |<span data-ttu-id="b4bf9-216">PAGEIO_LATCH_SH (_EX 或 _UP)</span><span class="sxs-lookup"><span data-stu-id="b4bf9-216">PAGEIO_LATCH_SH (_EX or _UP)</span></span>|<span data-ttu-id="b4bf9-217">這可能表示 IO 瓶頸，而在此情況下，您通常也會看見很高的平均磁碟佇列長度。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-217">This could indicate an IO bottleneck, in which case you would typically also see a high average disk-queue length.</span></span>|<span data-ttu-id="b4bf9-218">將全文檢索索引移至不同磁碟上的不同檔案群組可能有助於減少 IO 瓶頸。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-218">Moving the full-text index to a different filegroup on a different disk could help reduce the IO bottleneck.</span></span>|  
    |<span data-ttu-id="b4bf9-219">PAGELATCH_EX (或 _UP)</span><span class="sxs-lookup"><span data-stu-id="b4bf9-219">PAGELATCH_EX (or _UP)</span></span>|<span data-ttu-id="b4bf9-220">這可能表示嘗試寫入相同資料庫檔案的執行緒之間存在大量競爭的情況。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-220">This could indicate a lot of contention among threads that are trying to write to the same database file.</span></span>|<span data-ttu-id="b4bf9-221">將檔案加入至全文檢索索引所在的檔案群組可能有助於減少這類競爭的情況。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-221">Adding files to the filegroup on which the fulltext index resides could help alleviate such contention.</span></span>|  
  
     <span data-ttu-id="b4bf9-222">如需詳細資訊，請參閱 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-222">For more information, see [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql).</span></span>  
  
-   <span data-ttu-id="b4bf9-223">掃描基底資料表的效率不足</span><span class="sxs-lookup"><span data-stu-id="b4bf9-223">Inefficiencies in scanning the base table</span></span>  
  
     <span data-ttu-id="b4bf9-224">完整母體擴展會掃描基底資料表來產生批次。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-224">A full population scans the base table to produce batches.</span></span> <span data-ttu-id="b4bf9-225">在下列狀況中，這種資料表掃描作業可能會沒有效率：</span><span class="sxs-lookup"><span data-stu-id="b4bf9-225">This table scanning could be inefficient in the following scenarios:</span></span>  
  
    -   <span data-ttu-id="b4bf9-226">如果基底資料表中正在進行全文檢索索引之資料列外資料行的百分比很高，掃描基底資料表來產生批次的作業可能就是瓶頸。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-226">If the base table has a high percentage of out-of-row columns that are being full-text indexed, scanning the base table to produce batches might be the bottleneck.</span></span> <span data-ttu-id="b4bf9-227">在此情況下，使用 `varchar(max)` 或 `nvarchar(max)` 來移動較少的同資料列資料可能會有用。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-227">In this case, moving the smaller data in-row using `varchar(max)` or `nvarchar(max)` might help.</span></span>  
  
    -   <span data-ttu-id="b4bf9-228">如果基底資料表嚴重片段化，掃描可能就沒有效率。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-228">If the base table is very fragmented, scanning might be inefficient.</span></span> <span data-ttu-id="b4bf9-229">如需計算資料列外資料和索引片段的相關資訊，請參閱 [sys.dm_db_partition_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql) 和 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-229">For information about computing out-of-row data and index fragmentation, see [sys.dm_db_partition_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql) and [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql).</span></span>  
  
         <span data-ttu-id="b4bf9-230">若要減少片段，您可以重新組織或重建叢集索引。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-230">To reduce fragmentation, you can reorganize or rebuild the clustered index.</span></span> <span data-ttu-id="b4bf9-231">如需詳細資訊，請參閱 [重新組織與重建索引](../indexes/reorganize-and-rebuild-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-231">For more information, see [Reorganize and Rebuild Indexes](../indexes/reorganize-and-rebuild-indexes.md).</span></span>  
  
  
  
##  <a name="troubleshooting-slow-indexing-performance-due-to-filters"></a><a name="filters"></a><span data-ttu-id="b4bf9-232">針對緩慢的索引編制效能疑難排解，因為篩選準則</span><span class="sxs-lookup"><span data-stu-id="b4bf9-232">Troubleshooting Slow Indexing Performance Due to Filters</span></span>  
 <span data-ttu-id="b4bf9-233">擴展全文檢索索引時，全文檢索引擎會使用兩種篩選：多執行緒與單一執行緒。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-233">When populating a full-text index, the Full-Text Engine uses two types of filters: multithreaded and single-threaded.</span></span> <span data-ttu-id="b4bf9-234">某些文件 (例如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word 文件) 是使用多執行緒篩選進行篩選。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-234">Some documents, such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word documents, are filtered using a multithreaded filter.</span></span> <span data-ttu-id="b4bf9-235">其他文件 (例如 Adobe Acrobat Portable Document Format (PDF) 文件) 則是使用單一執行緒篩選進行篩選。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-235">Other documents, such as Adobe Acrobat Portable Document Format (PDF) documents, are filtered using a single-threaded filter.</span></span>  
  
 <span data-ttu-id="b4bf9-236">基於安全性理由，篩選是由篩選背景程式主機處理序載入。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-236">For security reasons, filters are loaded by filter daemon host processes.</span></span> <span data-ttu-id="b4bf9-237">伺服器執行個體會針對所有多執行緒篩選使用多執行緒處理序，而針對所有單一執行緒篩選使用單一執行緒處理序。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-237">A server instance uses a multithreaded process for all multithreaded filters and a single-threaded process for all single-threaded filters.</span></span> <span data-ttu-id="b4bf9-238">當使用多執行緒篩選的文件包含使用單一執行緒篩選的內嵌文件時，全文檢索引擎就會針對內嵌文件啟動單一執行緒處理序。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-238">When a document that uses a multithreaded filter contains an embedded document that uses a single-threaded filter, the Full-Text Engine launches a single-threaded process for the embedded document.</span></span> <span data-ttu-id="b4bf9-239">例如，如果遇到包含 PDF 文件的 Word 文件，全文檢索引擎就會針對 Word 內容啟動多執行緒處理序，而針對 PDF 內容啟動單一執行緒處理序。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-239">For example, on encountering a Word document that contains a PDF document, the Full-Text Engine uses the multithreaded process for the Word content and launches a single-threaded process for the PDF content.</span></span> <span data-ttu-id="b4bf9-240">不過，單一執行緒篩選在此環境下可能無法正常運作，而且可能會使篩選處理序不穩定。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-240">A single-threaded filter might not work well in this environment, however, and could destabilize the filtering process.</span></span> <span data-ttu-id="b4bf9-241">在經常會有這類內嵌的特定情況下，不穩定可能會導致篩選處理序損毀。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-241">In certain circumstances where such embedding is common, destabilization might lead to filtering-process crashes.</span></span> <span data-ttu-id="b4bf9-242">發生這個狀況時，全文檢索引擎就會將任何失敗的文件 (例如，包含內嵌 PDF 內容的 Word 文件) 重新路由傳送至單一執行緒篩選處理序。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-242">When this occurs, the Full-Text Engine re-routes any failed document (for example, a Word document that contains embedded PDF content) to the single-threaded filtering process.</span></span> <span data-ttu-id="b4bf9-243">如果經常發生重新路由傳送的狀況，則會導致全文檢索索引處理序的效能降低。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-243">If re-routing occurs frequently, it results in performance degradation of the full-text indexing process.</span></span>  
  
 <span data-ttu-id="b4bf9-244">若要解決這個問題，請將容器文件 (在此範例中是 Word) 的篩選標示成單一執行緒篩選。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-244">To work around this problem, mark the filter for the container document (Word in this case) as a single-threaded filter.</span></span> <span data-ttu-id="b4bf9-245">您可以變更篩選登錄值，以便將給定的篩選標示成單一執行緒篩選。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-245">You can change the filter registry value to mark a given filter as a single-threaded filter.</span></span> <span data-ttu-id="b4bf9-246">若要將篩選標示為單一執行緒篩選，您必須將篩選的**ThreadingModel**登錄值設定為 `Apartment Threaded` 。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-246">To mark a filter as a single-threaded filter, you need to set the **ThreadingModel** registry value for the filter to `Apartment Threaded`.</span></span> <span data-ttu-id="b4bf9-247">如需有關單一執行緒 Apartment 的詳細資訊，請參閱 [Understanding and Using COM Threading Models](https://go.microsoft.com/fwlink/?LinkId=209159)(了解與使用 COM 執行緒模型) 技術白皮書。</span><span class="sxs-lookup"><span data-stu-id="b4bf9-247">For information about single-threaded apartments, see the white paper [Understanding and Using COM Threading Models](https://go.microsoft.com/fwlink/?LinkId=209159).</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="b4bf9-248">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4bf9-248">See Also</span></span>  
 <span data-ttu-id="b4bf9-249">[伺服器記憶體伺服器組態選項](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span><span class="sxs-lookup"><span data-stu-id="b4bf9-249">[Server Memory Server Configuration Options](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span></span>  
 <span data-ttu-id="b4bf9-250">[全文檢索搜耙最大範圍伺服器組態選項](../../database-engine/configure-windows/max-full-text-crawl-range-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="b4bf9-250">[max full-text crawl range Server Configuration Option](../../database-engine/configure-windows/max-full-text-crawl-range-server-configuration-option.md) </span></span>  
 <span data-ttu-id="b4bf9-251">[擴展全文檢索索引](populate-full-text-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="b4bf9-251">[Populate Full-Text Indexes](populate-full-text-indexes.md) </span></span>  
 <span data-ttu-id="b4bf9-252">[建立及管理全文檢索索引](create-and-manage-full-text-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="b4bf9-252">[Create and Manage Full-Text Indexes](create-and-manage-full-text-indexes.md) </span></span>  
 <span data-ttu-id="b4bf9-253">[sys.dm_fts_memory_buffers &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b4bf9-253">[sys.dm_fts_memory_buffers &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql) </span></span>  
 <span data-ttu-id="b4bf9-254">[sys.dm_fts_memory_pools &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-pools-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b4bf9-254">[sys.dm_fts_memory_pools &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-pools-transact-sql) </span></span>  
 [<span data-ttu-id="b4bf9-255">疑難排解全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="b4bf9-255">Troubleshoot Full-Text Indexing</span></span>](troubleshoot-full-text-indexing.md)  
  
  
