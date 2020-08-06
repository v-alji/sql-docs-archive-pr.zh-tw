---
title: 重新組織與重建索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.indexproperties.fragmentation.f1
- sql12.swb.index.reorg.f1
- sql12.swb.index.rebuild.f1
helpviewer_keywords:
- large object defragmenting
- indexes [SQL Server], reorganizing
- index reorganization [SQL Server]
- reorganizing indexes
- defragmenting large object data types
- index fragmentation [SQL Server]
- index rebuilding [SQL Server]
- rebuilding indexes
- indexes [SQL Server], rebuilding
- defragmenting indexes
- nonclustered indexes [SQL Server], defragmenting
- fragmentation [SQL Server]
- index defragmenting [SQL Server]
- LOB data [SQL Server], defragmenting
- clustered indexes, defragmenting
ms.assetid: a28c684a-c4e9-4b24-a7ae-e248808b31e9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7c00f2128bb4c54064511ffff9e8929c9faf4d59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707553"
---
# <a name="reorganize-and-rebuild-indexes"></a><span data-ttu-id="ebf8c-102">重新組織與重建索引</span><span class="sxs-lookup"><span data-stu-id="ebf8c-102">Reorganize and Rebuild Indexes</span></span>
  <span data-ttu-id="ebf8c-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中重新組織或重建片段索引。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-103">This topic describes how to reorganize or rebuild a fragmented index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ebf8c-104">只要對基礎資料進行插入、更新或刪除作業， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 就會自動維護索引。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-104">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] automatically maintains indexes whenever insert, update, or delete operations are made to the underlying data.</span></span> <span data-ttu-id="ebf8c-105">過一段時間後，這些修改就可能使索引中的資訊變成散佈於資料庫中 (片段)。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-105">Over time these modifications can cause the information in the index to become scattered in the database (fragmented).</span></span> <span data-ttu-id="ebf8c-106">當根據索引鍵值的邏輯順序頁面，與資料檔中的實體順序不相符時，就會有片段產生。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-106">Fragmentation exists when indexes have pages in which the logical ordering, based on the key value, does not match the physical ordering inside the data file.</span></span> <span data-ttu-id="ebf8c-107">片段化嚴重的索引可能會造成查詢效能降低並使應用程式回應變慢。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-107">Heavily fragmented indexes can degrade query performance and cause your application to respond slowly.</span></span>  
  
 <span data-ttu-id="ebf8c-108">您可以重新組織或重建索引以修復索引片段。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-108">You can remedy index fragmentation by reorganizing or rebuilding an index.</span></span> <span data-ttu-id="ebf8c-109">對於在資料分割配置上建立的資料分割索引，您可以在完整的索引或在索引的單一資料分割上使用這些方法。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-109">For partitioned indexes built on a partition scheme, you can use either of these methods on a complete index or a single partition of an index.</span></span> <span data-ttu-id="ebf8c-110">重建索引會卸除和重新建立索引。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-110">Rebuilding an index drops and re-creates the index.</span></span> <span data-ttu-id="ebf8c-111">這會移除片段；根據指定的或現有的填滿因數設定壓縮頁面來收回磁碟空間，以及重新排序連續頁面中的索引資料列。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-111">This removes fragmentation, reclaims disk space by compacting the pages based on the specified or existing fill factor setting, and reorders the index rows in contiguous pages.</span></span> <span data-ttu-id="ebf8c-112">當指定 ALL 時，會在單一交易中卸除和重建資料表的所有索引。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-112">When ALL is specified, all indexes on the table are dropped and rebuilt in a single transaction.</span></span> <span data-ttu-id="ebf8c-113">重新組織索引所用的系統資源最少。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-113">Reorganizing an index uses minimal system resources.</span></span> <span data-ttu-id="ebf8c-114">它會實際重新排序分葉層級的頁面，使它們由左至右符合分葉節點的邏輯順序，以重新組織資料表和檢視表之叢集和非叢集索引的分葉層級。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-114">It defragments the leaf level of clustered and nonclustered indexes on tables and views by physically reordering the leaf-level pages to match the logical, left to right, order of the leaf nodes.</span></span> <span data-ttu-id="ebf8c-115">重新組織也會壓縮索引頁面。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-115">Reorganizing also compacts the index pages.</span></span> <span data-ttu-id="ebf8c-116">壓縮是以現有填滿因數值為基礎。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-116">Compaction is based on the existing fill factor value.</span></span>  
  
 <span data-ttu-id="ebf8c-117">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="ebf8c-117">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ebf8c-118">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="ebf8c-118">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ebf8c-119">偵測片段</span><span class="sxs-lookup"><span data-stu-id="ebf8c-119">Detecting Fragmentation</span></span>](#Fragmentation)  
  
     [<span data-ttu-id="ebf8c-120">限制事項</span><span class="sxs-lookup"><span data-stu-id="ebf8c-120">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ebf8c-121">安全性</span><span class="sxs-lookup"><span data-stu-id="ebf8c-121">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ebf8c-122">**使用下列方法檢查索引的片段：**</span><span class="sxs-lookup"><span data-stu-id="ebf8c-122">**To check the fragmentation of an index, using:**</span></span>  
  
     [<span data-ttu-id="ebf8c-123">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ebf8c-123">SQL Server Management Studio</span></span>](#SSMSProcedureFrag)  
  
     [<span data-ttu-id="ebf8c-124">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ebf8c-124">Transact-SQL</span></span>](#TsqlProcedureFrag)  
  
-   <span data-ttu-id="ebf8c-125">**使用下列方法重新組織或重建索引：**</span><span class="sxs-lookup"><span data-stu-id="ebf8c-125">**To reorganize or rebuild an index, using:**</span></span>  
  
     [<span data-ttu-id="ebf8c-126">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ebf8c-126">SQL Server Management Studio</span></span>](#SSMSProcedureReorg)  
  
     [<span data-ttu-id="ebf8c-127">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ebf8c-127">Transact-SQL</span></span>](#TsqlProcedureReorg)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ebf8c-128">開始之前</span><span class="sxs-lookup"><span data-stu-id="ebf8c-128">Before You Begin</span></span>  
  
###  <a name="detecting-fragmentation"></a><a name="Fragmentation"></a><span data-ttu-id="ebf8c-129">偵測片段</span><span class="sxs-lookup"><span data-stu-id="ebf8c-129">Detecting Fragmentation</span></span>  
 <span data-ttu-id="ebf8c-130">決定使用重組方法的第一步是分析索引以決定片段的程度。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-130">The first step in deciding which defragmentation method to use is to analyze the index to determine the degree of fragmentation.</span></span> <span data-ttu-id="ebf8c-131">透過使用系統函數 [sys.dm_db_index_physical_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql)，您就可以在特定的索引中、在資料表或索引檢視表上的所有索引、在資料庫中的所有索引或在所有資料庫的所有索引中偵測片段。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-131">By using the system function [sys.dm_db_index_physical_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql), you can detect fragmentation in a specific index, all indexes on a table or indexed view, all indexes in a database, or all indexes in all databases.</span></span> <span data-ttu-id="ebf8c-132">對於資料分割索引而言， **sys.dm_db_index_physical_stats** 也為每個資料分割提供片段資訊。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-132">For partitioned indexes, **sys.dm_db_index_physical_stats** also provides fragmentation information for each partition.</span></span>  
  
 <span data-ttu-id="ebf8c-133">**sys.dm_db_index_physical_stats** 函數傳回的結果集包含下列資料行。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-133">The result set returned by the **sys.dm_db_index_physical_stats** function includes the following columns.</span></span>  
  
|<span data-ttu-id="ebf8c-134">資料行</span><span class="sxs-lookup"><span data-stu-id="ebf8c-134">Column</span></span>|<span data-ttu-id="ebf8c-135">描述</span><span class="sxs-lookup"><span data-stu-id="ebf8c-135">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ebf8c-136">**avg_fragmentation_in_percent**</span><span class="sxs-lookup"><span data-stu-id="ebf8c-136">**avg_fragmentation_in_percent**</span></span>|<span data-ttu-id="ebf8c-137">邏輯片段的百分比 (索引中失序的頁面)。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-137">The percent of logical fragmentation (out-of-order pages in the index).</span></span>|  
|<span data-ttu-id="ebf8c-138">**fragment_count**</span><span class="sxs-lookup"><span data-stu-id="ebf8c-138">**fragment_count**</span></span>|<span data-ttu-id="ebf8c-139">在索引中的片段數目 (實體上為連續的分葉頁面)。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-139">The number of fragments (physically consecutive leaf pages) in the index.</span></span>|  
|<span data-ttu-id="ebf8c-140">**avg_fragment_size_in_pages**</span><span class="sxs-lookup"><span data-stu-id="ebf8c-140">**avg_fragment_size_in_pages**</span></span>|<span data-ttu-id="ebf8c-141">在索引中一個片段的頁面平均數目。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-141">Average number of pages in one fragment in an index.</span></span>|  
  
 <span data-ttu-id="ebf8c-142">在了解片段的程度後，請使用下表來決定修正片段最好的方法。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-142">After the degree of fragmentation is known, use the following table to determine the best method to correct the fragmentation.</span></span>  
  
|<span data-ttu-id="ebf8c-143">**avg_fragmentation_in_percent** 值</span><span class="sxs-lookup"><span data-stu-id="ebf8c-143">**avg_fragmentation_in_percent** value</span></span>|<span data-ttu-id="ebf8c-144">修正的陳述式</span><span class="sxs-lookup"><span data-stu-id="ebf8c-144">Corrective statement</span></span>|  
|-----------------------------------------------|--------------------------|  
|<span data-ttu-id="ebf8c-145">> 5% 和 \< = 30%</span><span class="sxs-lookup"><span data-stu-id="ebf8c-145">> 5% and \< = 30%</span></span>|<span data-ttu-id="ebf8c-146">ALTER INDEX REORGANIZE</span><span class="sxs-lookup"><span data-stu-id="ebf8c-146">ALTER INDEX REORGANIZE</span></span>|  
|<span data-ttu-id="ebf8c-147">> 30%</span><span class="sxs-lookup"><span data-stu-id="ebf8c-147">> 30%</span></span>|<span data-ttu-id="ebf8c-148">ALTER INDEX REBUILD WITH (ONLINE = ON) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="ebf8c-148">ALTER INDEX REBUILD WITH (ONLINE = ON) <sup>1</sup></span></span>|

<span data-ttu-id="ebf8c-149"><sup>1</sup> 重建索引可於線上或離線執行。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-149"><sup>1</sup> Rebuilding an index can be executed online or offline.</span></span> <span data-ttu-id="ebf8c-150">重新組織索引則一律在線上執行。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-150">Reorganizing an index is always executed online.</span></span> <span data-ttu-id="ebf8c-151">若要達到與重新組織選項相似的可用性，您應該在線上重建索引。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-151">To achieve availability similar to the reorganize option, you should rebuild indexes online.</span></span>  
  
> [!TIP]
> <span data-ttu-id="ebf8c-152">這些值提供概略的方針，讓您可判斷應該在 `ALTER INDEX REORGANIZE` 和 `ALTER INDEX REBUILD` 之間切換的時間點。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-152">These values provide a rough guideline for determining the point at which you should switch between `ALTER INDEX REORGANIZE` and `ALTER INDEX REBUILD`.</span></span> <span data-ttu-id="ebf8c-153">不過，實際的值可能隨各種狀況而異。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-153">However, the actual values may vary from case to case.</span></span> <span data-ttu-id="ebf8c-154">請務必嘗試不同的值，以判斷適合您環境的最佳臨界值。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-154">It is important that you experiment to determine the best threshold for your environment.</span></span> <span data-ttu-id="ebf8c-155">例如，如果指定的索引主要用於掃描作業，則移除片段可以改善這些作業的效能。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-155">For example, if a given index is used mainly for scan operations, removing fragmentation can improve performance of these operations.</span></span> <span data-ttu-id="ebf8c-156">對於主要用於搜尋作業的索引而言，效能優勢較不明顯。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-156">The performance benefit is less noticeable for indexes that are used primarily for seek operations.</span></span> <span data-ttu-id="ebf8c-157">同樣地，移除堆積中的片段 (沒有叢集索引的資料表) 對於非叢集索引掃描作業特別有用，但對查閱作業則幾乎沒有作用。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-157">Similarly, removing fragmentation in a heap (a table with no clustered index) is especially useful for nonclustered index scan operations, but has little effect in lookup operations.</span></span>

<span data-ttu-id="ebf8c-158">您通常不應該使用上述任何命令來處理片段層級過低 (低於 5%) 的情況，因為重組或重建索引的成本遠遠超過移除如此少量片段所獲得的好處。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-158">Very low levels of fragmentation (less than 5 percent) should typically not be addressed by either of these commands, because the benefit from removing such a small amount of fragmentation is almost always vastly outweighed by the cost of reorganizing or rebuilding the index.</span></span> 

> [!NOTE]
> <span data-ttu-id="ebf8c-159">重建或重新組織小型索引通常不會減少片段。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-159">Rebuilding or reorganizing small indexes often does not reduce fragmentation.</span></span> <span data-ttu-id="ebf8c-160">小型索引的頁面有時候會儲存在混合範圍上，</span><span class="sxs-lookup"><span data-stu-id="ebf8c-160">The pages of small indexes are sometimes stored on mixed extents.</span></span> <span data-ttu-id="ebf8c-161">混合範圍最多可由八個物件所共用，所以當重新組織或重建索引之後，小型索引中的片段可能不會減少。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-161">Mixed extents are shared by up to eight objects, so the fragmentation in a small index might not be reduced after reorganizing or rebuilding it.</span></span>

### <a name="index-defragmentation-considerations"></a><span data-ttu-id="ebf8c-162">索引磁碟重組考量</span><span class="sxs-lookup"><span data-stu-id="ebf8c-162">Index defragmentation considerations</span></span>
<span data-ttu-id="ebf8c-163">在某些情況下，如果非叢集索引記錄中所包含的實體或邏輯識別碼需要變更，則重建叢集索引將會自動重建任何參考叢集索引鍵的非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-163">Under certain conditions, rebuilding a clustered index will automatically rebuild any nonclustered index that reference the clustering key, if the physical or logical identifiers contained in the nonclustered index records needs to change.</span></span>

<span data-ttu-id="ebf8c-164">強制在資料表上自動重建所有非叢集索引的案例：</span><span class="sxs-lookup"><span data-stu-id="ebf8c-164">Scenarios that force all nonclustered indexes to be automatically rebuilt on a table:</span></span>

-  <span data-ttu-id="ebf8c-165">在資料表上建立叢集索引</span><span class="sxs-lookup"><span data-stu-id="ebf8c-165">Creating a clustered index on a table</span></span>
-  <span data-ttu-id="ebf8c-166">移除叢集索引，使資料表儲存為堆積</span><span class="sxs-lookup"><span data-stu-id="ebf8c-166">Removing a clustered index, causing the table to be stored as a heap</span></span>
-  <span data-ttu-id="ebf8c-167">變更叢集索引鍵以包含或排除資料行</span><span class="sxs-lookup"><span data-stu-id="ebf8c-167">Changing the clustering key to include or exclude columns</span></span>

<span data-ttu-id="ebf8c-168">不需要在資料表上自動重建所有非叢集索引的案例：</span><span class="sxs-lookup"><span data-stu-id="ebf8c-168">Scenarios that do not require all nonclustered indexes to be automatically rebuilt on a table:</span></span>

-  <span data-ttu-id="ebf8c-169">重建唯一的叢集索引</span><span class="sxs-lookup"><span data-stu-id="ebf8c-169">Rebuilding a unique clustered index</span></span>
-  <span data-ttu-id="ebf8c-170">重建非唯一的叢集索引</span><span class="sxs-lookup"><span data-stu-id="ebf8c-170">Rebuilding a non-unique clustered index</span></span>
-  <span data-ttu-id="ebf8c-171">變更索引結構描述，例如將資料分割結構描述套用至叢集索引，或將叢集索引移至不同的檔案群組</span><span class="sxs-lookup"><span data-stu-id="ebf8c-171">Changing the index schema, such as applying a partitioning scheme to a clustered index or moving the clustered index to a different filegroup</span></span>
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ebf8c-172">限制事項</span><span class="sxs-lookup"><span data-stu-id="ebf8c-172">Limitations and Restrictions</span></span>  
  
<span data-ttu-id="ebf8c-173">超過 128 個範圍的索引將以兩個不同的階段重建：邏輯和實體。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-173">Indexes with more than 128 extents are rebuilt in two separate phases: logical and physical.</span></span> <span data-ttu-id="ebf8c-174">在邏輯階段中，索引所使用的現有配置單位將以取消配置標示，並複製和排序資料列，然後移到所建立的新配置單位以儲存重建索引。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-174">In the logical phase, the existing allocation units used by the index are marked for deallocation, the data rows are copied and sorted, then moved to new allocation units created to store the rebuilt index.</span></span> <span data-ttu-id="ebf8c-175">在實體階段中，會將先前標示為取消配置的配置單位，在背景以短暫的交易實際卸除，而且不需要許多鎖定。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-175">In the physical phase, the allocation units previously marked for deallocation are physically dropped in short transactions that happen in the background, and do not require many locks.</span></span> <span data-ttu-id="ebf8c-176">如需範圍的詳細資訊，請參閱[分頁與範圍架構指南](https://docs.microsoft.com/sql/relational-databases/pages-and-extents-architecture-guide)。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-176">For more information about extents, refer to the [Pages and Extents Architecture Guide](https://docs.microsoft.com/sql/relational-databases/pages-and-extents-architecture-guide).</span></span>

<span data-ttu-id="ebf8c-177">`ALTER INDEX REORGANIZE` 陳述式需要包含索引的資料檔案具有可用的空間，因為作業只能配置在相同檔案上的暫存工作頁面，而不是檔案群組內的其他檔案。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-177">The `ALTER INDEX REORGANIZE` statement requires the data file containing the index to have space available, because the operation can only allocate temporary work pages on the same file, not another file within the filegroup.</span></span> <span data-ttu-id="ebf8c-178">因此，雖然檔案群組可能有可用的分頁，但是使用者仍然可能會出現錯誤 1105：`Could not allocate space for object '###' in database '###' because the '###' filegroup is full. Create disk space by deleting unneeded files, dropping objects in the filegroup, adding additional files to the filegroup, or setting autogrowth on for existing files in the filegroup.`</span><span class="sxs-lookup"><span data-stu-id="ebf8c-178">So although the filegroup might have free pages available, the user can still encounter error 1105: `Could not allocate space for object '###' in database '###' because the '###' filegroup is full. Create disk space by deleting unneeded files, dropping objects in the filegroup, adding additional files to the filegroup, or setting autogrowth on for existing files in the filegroup.`</span></span>

<span data-ttu-id="ebf8c-179">您可以對包含超過 1,000 個分割區的資料表，建立及重建未校正的索引，但並不建議這麼做。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-179">Creating and rebuilding non-aligned indexes on a table with more than 1,000 partitions is possible, but is not recommended.</span></span> <span data-ttu-id="ebf8c-180">此做法可能會導致在作業期間效能降低或耗用過多記憶體。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-180">Doing so may cause degraded performance or excessive memory consumption during these operations.</span></span>

<span data-ttu-id="ebf8c-181">如果索引所在的檔案群組離線或設為唯讀，便無法重新組織或重建索引。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-181">An index cannot be reorganized or rebuilt if the filegroup in which it is located is offline or set to read-only.</span></span> <span data-ttu-id="ebf8c-182">當指定 `ALL` 關鍵字，且有一或多個索引在離線或唯讀檔案群組中時，陳述式會失敗。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-182">When the keyword `ALL` is specified and one or more indexes are in an offline or read-only filegroup, the statement fails.</span></span>
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ebf8c-183">Security</span><span class="sxs-lookup"><span data-stu-id="ebf8c-183">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ebf8c-184">權限</span><span class="sxs-lookup"><span data-stu-id="ebf8c-184">Permissions</span></span>  
 <span data-ttu-id="ebf8c-185">必須具備資料表或檢視的 `ALTER` 權限。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-185">Requires `ALTER` permission on the table or view.</span></span> <span data-ttu-id="ebf8c-186">使用者必須是 **系統管理員** 固定伺服器角色的成員，或是 **db_ddladmin** 和 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-186">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedureFrag"></a> <span data-ttu-id="ebf8c-187">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ebf8c-187">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-check-the-fragmentation-of-an-index"></a><span data-ttu-id="ebf8c-188">若要檢查索引的片段</span><span class="sxs-lookup"><span data-stu-id="ebf8c-188">To check the fragmentation of an index</span></span>  
  
1.  <span data-ttu-id="ebf8c-189">在 [物件總管] 中，展開包含您要檢查其索引片段之資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-189">In Object Explorer, Expand the database that contains the table on which you want to check an index's fragmentation.</span></span>  
  
2.  <span data-ttu-id="ebf8c-190">展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-190">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="ebf8c-191">展開要檢查其索引片段的資料表。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-191">Expand the table on which you want to check an index's fragmentation.</span></span>  
  
4.  <span data-ttu-id="ebf8c-192">展開 **[索引]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-192">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="ebf8c-193">以滑鼠右鍵按一下要檢查其片段的索引，然後選取 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-193">Right-click the index of which you want to check the fragmentation and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="ebf8c-194">在 **[選取頁面]** 底下，選取 **[片段]** 。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-194">Under **Select a page**, select **Fragmentation**.</span></span>  
  
     <span data-ttu-id="ebf8c-195">**[片段]** 頁面上提供下列資訊：</span><span class="sxs-lookup"><span data-stu-id="ebf8c-195">The following information is available on the **Fragmentation** page:</span></span>  
  
     <span data-ttu-id="ebf8c-196">**頁面飽和度**</span><span class="sxs-lookup"><span data-stu-id="ebf8c-196">**Page fullness**</span></span>  
     <span data-ttu-id="ebf8c-197">指出索引頁面的平均飽和度，以百分比表示。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-197">Indicates average fullness of the index pages, as a percentage.</span></span> <span data-ttu-id="ebf8c-198">100% 表示索引頁面完全飽和。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-198">100% means the index pages are completely full.</span></span> <span data-ttu-id="ebf8c-199">50% 表示平均每個索引頁面為半飽和。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-199">50% means that, on average, each index page is half full.</span></span>  
  
     <span data-ttu-id="ebf8c-200">**片段總計**</span><span class="sxs-lookup"><span data-stu-id="ebf8c-200">**Total fragmentation**</span></span>  
     <span data-ttu-id="ebf8c-201">邏輯片段百分比。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-201">The logical fragmentation percentage.</span></span> <span data-ttu-id="ebf8c-202">這指出索引中未依順序儲存的頁數。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-202">This indicates the number of pages in an index that are not stored in order.</span></span>  
  
     <span data-ttu-id="ebf8c-203">**平均資料列大小**</span><span class="sxs-lookup"><span data-stu-id="ebf8c-203">**Average row size**</span></span>  
     <span data-ttu-id="ebf8c-204">分葉層級資料列的平均大小。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-204">The average size of a leaf level row.</span></span>  
  
     <span data-ttu-id="ebf8c-205">**Depth**</span><span class="sxs-lookup"><span data-stu-id="ebf8c-205">**Depth**</span></span>  
     <span data-ttu-id="ebf8c-206">索引中的層級數目，包括分葉層級。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-206">The number of levels in the index, including the leaf level.</span></span>  
  
     <span data-ttu-id="ebf8c-207">**轉送的記錄**</span><span class="sxs-lookup"><span data-stu-id="ebf8c-207">**Forwarded records**</span></span>  
     <span data-ttu-id="ebf8c-208">在堆積中，有指向另一個資料位置之轉送指標的記錄數目。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-208">The number of records in a heap that have forward pointers to another data location.</span></span> <span data-ttu-id="ebf8c-209">(此狀態發生於更新期間，原始位置的空間不足以儲存新資料列時)。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-209">(This state occurs during an update, when there is not enough room to store the new row in the original location.)</span></span>  
  
     <span data-ttu-id="ebf8c-210">**準刪除列**</span><span class="sxs-lookup"><span data-stu-id="ebf8c-210">**Ghost rows**</span></span>  
     <span data-ttu-id="ebf8c-211">標示為刪除但尚未移除的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-211">The number of rows that are marked as deleted but not yet removed.</span></span> <span data-ttu-id="ebf8c-212">這些資料列將由清除執行緒在伺服器不忙碌時移除。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-212">These rows will be removed by a clean-up thread, when the server is not busy.</span></span> <span data-ttu-id="ebf8c-213">這個值不包含因未處理的快照集隔離交易而保留的資料列。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-213">This value does not include rows that are being retained due to an outstanding snapshot isolation transaction.</span></span>  
  
     <span data-ttu-id="ebf8c-214">**索引類型**</span><span class="sxs-lookup"><span data-stu-id="ebf8c-214">**Index type**</span></span>  
     <span data-ttu-id="ebf8c-215">索引的類型。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-215">The type of index.</span></span> <span data-ttu-id="ebf8c-216">可能的值為 **[叢集索引]** 、 **[非叢集索引]** 以及 **[主要 XML]** 。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-216">Possible values are **Clustered index**, **Nonclustered index**, and **Primary XML**.</span></span> <span data-ttu-id="ebf8c-217">資料表也可以儲存為堆積 (無索引)，但是無法開啟此 [索引屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-217">Tables can also be stored as a heap (without indexes), but then this Index Properties page cannot be opened.</span></span>  
  
     <span data-ttu-id="ebf8c-218">**分葉層級資料列**</span><span class="sxs-lookup"><span data-stu-id="ebf8c-218">**Leaf-level rows**</span></span>  
     <span data-ttu-id="ebf8c-219">分葉層級資料列的數目。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-219">The number of leaf level rows.</span></span>  
  
     <span data-ttu-id="ebf8c-220">**資料列大小上限**</span><span class="sxs-lookup"><span data-stu-id="ebf8c-220">**Maximum row size**</span></span>  
     <span data-ttu-id="ebf8c-221">分葉層級資料列大小上限。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-221">The maximum leaf-level row size.</span></span>  
  
     <span data-ttu-id="ebf8c-222">**資料列大小下限**</span><span class="sxs-lookup"><span data-stu-id="ebf8c-222">**Minimum row size**</span></span>  
     <span data-ttu-id="ebf8c-223">最小分葉層級資料列大小。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-223">The minimum leaf-level row size.</span></span>  
  
     <span data-ttu-id="ebf8c-224">**頁面**</span><span class="sxs-lookup"><span data-stu-id="ebf8c-224">**Pages**</span></span>  
     <span data-ttu-id="ebf8c-225">資料頁的總數。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-225">The total number of data pages.</span></span>  
  
     <span data-ttu-id="ebf8c-226">**分割區識別碼**</span><span class="sxs-lookup"><span data-stu-id="ebf8c-226">**Partition ID**</span></span>  
     <span data-ttu-id="ebf8c-227">包含索引之 B 型樹狀目錄的資料分割識別碼。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-227">The partition ID of the b-tree containing the index.</span></span>  
  
     <span data-ttu-id="ebf8c-228">**版本準刪除列**</span><span class="sxs-lookup"><span data-stu-id="ebf8c-228">**Version ghost rows**</span></span>  
     <span data-ttu-id="ebf8c-229">因為未處理的快照集隔離交易而保留的準刪除記錄數目。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-229">The number of ghost records that are being retained due to an outstanding snapshot isolation transaction.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedureFrag"></a> <span data-ttu-id="ebf8c-230">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ebf8c-230">Using Transact-SQL</span></span>  
  
#### <a name="to-check-the-fragmentation-of-an-index"></a><span data-ttu-id="ebf8c-231">若要檢查索引的片段</span><span class="sxs-lookup"><span data-stu-id="ebf8c-231">To check the fragmentation of an index</span></span>  
  
1.  <span data-ttu-id="ebf8c-232">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-232">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ebf8c-233">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-233">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ebf8c-234">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-234">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Find the average fragmentation percentage of all indexes  
    -- in the HumanResources.Employee table.   
    SELECT a.index_id, name, avg_fragmentation_in_percent  
    FROM sys.dm_db_index_physical_stats (DB_ID(N'AdventureWorks2012'), OBJECT_ID(N'HumanResources.Employee'), NULL, NULL, NULL) AS a  
        JOIN sys.indexes AS b ON a.object_id = b.object_id AND a.index_id = b.index_id;   
    GO  
    ```  
  
     <span data-ttu-id="ebf8c-235">上面的陳述式可能會傳回與下例類似的結果集。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-235">The statement above might return a result set similar to the following.</span></span>  
  
    ```  
    index_id    name                                                  avg_fragmentation_in_percent  
    ----------- ----------------------------------------------------- ----------------------------  
    1           PK_Employee_BusinessEntityID                          0  
    2           IX_Employee_OrganizationalNode                        0  
    3           IX_Employee_OrganizationalLevel_OrganizationalNode    0  
    5           AK_Employee_LoginID                                   66.6666666666667  
    6           AK_Employee_NationalIDNumber                          50  
    7           AK_Employee_rowguid                                   0  
  
    (6 row(s) affected)  
    ```  
  
 <span data-ttu-id="ebf8c-236">如需詳細資訊，請參閱 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-236">For more information, see  [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedureReorg"></a> <span data-ttu-id="ebf8c-237">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ebf8c-237">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-reorganize-or-rebuild-an-index"></a><span data-ttu-id="ebf8c-238">若要重新組織或重建索引</span><span class="sxs-lookup"><span data-stu-id="ebf8c-238">To reorganize or rebuild an index</span></span>  
  
1.  <span data-ttu-id="ebf8c-239">在 [物件總管] 中，展開包含您要重新組織其索引之資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-239">In Object Explorer, Expand the database that contains the table on which you want to reorganize an index.</span></span>  
  
2.  <span data-ttu-id="ebf8c-240">展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-240">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="ebf8c-241">展開您要重新組織其索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-241">Expand the table on which you want to reorganize an index.</span></span>  
  
4.  <span data-ttu-id="ebf8c-242">展開 **[索引]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-242">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="ebf8c-243">以滑鼠右鍵按一下您要重新組織的索引，然後選取 **[重新組織]** 。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-243">Right-click the index you want to reorganize and select **Reorganize**.</span></span>  
  
6.  <span data-ttu-id="ebf8c-244">在 **[重新組織索引]** 對話方塊中，確認 **[要重新組織的索引]** 方格中有正確索引，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-244">In the **Reorganize Indexes** dialog box, verify that the correct index is in the **Indexes to be reorganized** grid and click **OK**.</span></span>  
  
7.  <span data-ttu-id="ebf8c-245">選取 **[壓縮大型物件資料行資料]** 核取方塊，可指定一併壓縮包含大型物件 (LOB) 資料的所有頁面。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-245">Select the **Compact large object column data** check box to specify that all pages that contain large object (LOB) data are also compacted.</span></span>  
  
8.  <span data-ttu-id="ebf8c-246">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-246">Click **OK.**</span></span>  
  
#### <a name="to-reorganize-all-indexes-in-a-table"></a><span data-ttu-id="ebf8c-247">若要重新組織資料表中的所有索引</span><span class="sxs-lookup"><span data-stu-id="ebf8c-247">To reorganize all indexes in a table</span></span>  
  
1.  <span data-ttu-id="ebf8c-248">在 [物件總管] 中，展開包含您要重新組織其索引之資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-248">In Object Explorer, Expand the database that contains the table on which you want to reorganize the indexes.</span></span>  
  
2.  <span data-ttu-id="ebf8c-249">展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-249">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="ebf8c-250">展開您要重新組織其索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-250">Expand the table on which you want to reorganize the indexes.</span></span>  
  
4.  <span data-ttu-id="ebf8c-251">以滑鼠右鍵按一下 **[索引]** 資料夾，並選取 **[全部重新組織]** 。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-251">Right-click the **Indexes** folder and select **Reorganize All**.</span></span>  
  
5.  <span data-ttu-id="ebf8c-252">在 **[重新組織索引]** 對話方塊中，確認 **[要重新組織的索引]** 方格中有正確索引。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-252">In the **Reorganize Indexes** dialog box, verify that the correct indexes are in the **Indexes to be reorganized**.</span></span> <span data-ttu-id="ebf8c-253">若要從 **[要重新組織的索引]** 方格中移除索引，請選取索引，然後按下 DELETE 鍵。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-253">To remove an index from the **Indexes to be reorganized** grid, select the index and then press the Delete key.</span></span>  
  
6.  <span data-ttu-id="ebf8c-254">選取 **[壓縮大型物件資料行資料]** 核取方塊，可指定一併壓縮包含大型物件 (LOB) 資料的所有頁面。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-254">Select the **Compact large object column data** check box to specify that all pages that contain large object (LOB) data are also compacted.</span></span>  
  
7.  <span data-ttu-id="ebf8c-255">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-255">Click **OK.**</span></span>  
  
#### <a name="to-rebuild-an-index"></a><span data-ttu-id="ebf8c-256">若要重建索引</span><span class="sxs-lookup"><span data-stu-id="ebf8c-256">To rebuild an index</span></span>  
  
1.  <span data-ttu-id="ebf8c-257">在 [物件總管] 中，展開包含您要重新組織其索引之資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-257">In Object Explorer, Expand the database that contains the table on which you want to reorganize an index.</span></span>  
  
2.  <span data-ttu-id="ebf8c-258">展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-258">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="ebf8c-259">展開您要重新組織其索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-259">Expand the table on which you want to reorganize an index.</span></span>  
  
4.  <span data-ttu-id="ebf8c-260">展開 **[索引]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-260">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="ebf8c-261">以滑鼠右鍵按一下您要重新組織的索引，然後選取 **[重新組織]** 。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-261">Right-click the index you want to reorganize and select **Reorganize**.</span></span>  
  
6.  <span data-ttu-id="ebf8c-262">在 **[重建索引]** 對話方塊中，確認 **[要重建的索引]** 方格中有正確索引，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-262">In the **Rebuild Indexes** dialog box, verify that the correct index is in the **Indexes to be rebuilt** grid and click **OK**.</span></span>  
  
7.  <span data-ttu-id="ebf8c-263">選取 **[壓縮大型物件資料行資料]** 核取方塊，可指定一併壓縮包含大型物件 (LOB) 資料的所有頁面。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-263">Select the **Compact large object column data** check box to specify that all pages that contain large object (LOB) data are also compacted.</span></span>  
  
8.  <span data-ttu-id="ebf8c-264">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-264">Click **OK.**</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedureReorg"></a> <span data-ttu-id="ebf8c-265">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ebf8c-265">Using Transact-SQL</span></span>  
  
#### <a name="to-reorganize-a-defragmented-index"></a><span data-ttu-id="ebf8c-266">若要重新組織重組的索引</span><span class="sxs-lookup"><span data-stu-id="ebf8c-266">To reorganize a defragmented index</span></span>  
  
1.  <span data-ttu-id="ebf8c-267">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-267">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ebf8c-268">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-268">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ebf8c-269">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-269">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- Reorganize the IX_Employee_OrganizationalLevel_OrganizationalNode index on the HumanResources.Employee table.   
  
    ALTER INDEX IX_Employee_OrganizationalLevel_OrganizationalNode ON HumanResources.Employee  
    REORGANIZE ;   
    GO  
    ```  
  
#### <a name="to-reorganize-all-indexes-in-a-table"></a><span data-ttu-id="ebf8c-270">若要重新組織資料表中的所有索引</span><span class="sxs-lookup"><span data-stu-id="ebf8c-270">To reorganize all indexes in a table</span></span>  
  
1.  <span data-ttu-id="ebf8c-271">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-271">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ebf8c-272">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-272">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ebf8c-273">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-273">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- Reorganize all indexes on the HumanResources.Employee table.  
    ALTER INDEX ALL ON HumanResources.Employee  
    REORGANIZE ;   
    GO  
    ```  
  
#### <a name="to-rebuild-a-defragmented-index"></a><span data-ttu-id="ebf8c-274">若要重建重組的索引</span><span class="sxs-lookup"><span data-stu-id="ebf8c-274">To rebuild a defragmented index</span></span>  
  
1.  <span data-ttu-id="ebf8c-275">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-275">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ebf8c-276">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-276">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ebf8c-277">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-277">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ebf8c-278">此範例會在 `Employee` 資料表上重建單一索引。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-278">The example rebuilds a single index on the `Employee` table.</span></span>  
  
     [!code-sql[IndexDDL#AlterIndex1](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex1)]  
  
#### <a name="to-rebuild-all-indexes-in-a-table"></a><span data-ttu-id="ebf8c-279">若要重建資料表中全部的索引</span><span class="sxs-lookup"><span data-stu-id="ebf8c-279">To rebuild all indexes in a table</span></span>  
  
1.  <span data-ttu-id="ebf8c-280">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-280">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ebf8c-281">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-281">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ebf8c-282">將下列範例複製並貼入查詢視窗中。此範例會指定關鍵字 `ALL`。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-282">Copy and paste the following example into the query The example specifies the keyword `ALL`.</span></span> <span data-ttu-id="ebf8c-283">這會重建與資料表相關聯的所有索引。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-283">This rebuilds all indexes associated with the table.</span></span> <span data-ttu-id="ebf8c-284">指定三個選項。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-284">Three options are specified.</span></span>  
  
     [!code-sql[IndexDDL#AlterIndex2](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex2)]  
  
 <span data-ttu-id="ebf8c-285">如需詳細資訊，請參閱 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ebf8c-285">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebf8c-286">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebf8c-286">See Also</span></span>  
 [<span data-ttu-id="ebf8c-287">Microsoft SQL Server 2000 索引重組最佳作法</span><span class="sxs-lookup"><span data-stu-id="ebf8c-287">Microsoft SQL Server 2000 Index Defragmentation Best Practices</span></span>](https://technet.microsoft.com/library/cc966523.aspx)  
  
  
