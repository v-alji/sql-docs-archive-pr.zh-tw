---
title: 索引 DDL 作業的磁碟空間需求 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- disk space [SQL Server], indexes
- index disk space [SQL Server]
- space [SQL Server], indexes
- indexes [SQL Server], disk space requirements
- temporary disk space [SQL Server]
ms.assetid: 35930826-c870-44c1-a966-a6a4638f62ef
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4ac25fc1555d6b6cfd8ee97b50d261cf5788f587
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606310"
---
# <a name="disk-space-requirements-for-index-ddl-operations"></a><span data-ttu-id="722b9-102">Disk Space Requirements for Index DDL Operations</span><span class="sxs-lookup"><span data-stu-id="722b9-102">Disk Space Requirements for Index DDL Operations</span></span>
  <span data-ttu-id="722b9-103">當您建立、重建或卸除索引時，磁碟空間是一個重要的考量。</span><span class="sxs-lookup"><span data-stu-id="722b9-103">Disk space is an important consideration when you create, rebuild, or drop indexes.</span></span> <span data-ttu-id="722b9-104">不足的磁碟空間會降低效能，甚至導致索引作業失敗。</span><span class="sxs-lookup"><span data-stu-id="722b9-104">Inadequate disk space can degrade performance or even cause the index operation to fail.</span></span> <span data-ttu-id="722b9-105">此主題提供了一般資訊，可協助您判斷索引資料定義語言 (DDL) 作業所需的磁碟空間數量。</span><span class="sxs-lookup"><span data-stu-id="722b9-105">This topic provides general information that can help you determine the amount of disk space required for index data definition language (DDL) operations.</span></span>  
  
## <a name="index-operations-that-require-no-additional-disk-space"></a><span data-ttu-id="722b9-106">不需要額外磁碟空間的索引作業</span><span class="sxs-lookup"><span data-stu-id="722b9-106">Index Operations That Require No Additional Disk Space</span></span>  
 <span data-ttu-id="722b9-107">下列是不需要額外磁碟空間的索引作業：</span><span class="sxs-lookup"><span data-stu-id="722b9-107">The following index operations require no additional disk space:</span></span>  
  
-   <span data-ttu-id="722b9-108">ALTER INDEX REORGANIZE，但是需要記錄檔空間。</span><span class="sxs-lookup"><span data-stu-id="722b9-108">ALTER INDEX REORGANIZE; however, log space is required.</span></span>  
  
-   <span data-ttu-id="722b9-109">DROP INDEX，卸除非叢集索引時。</span><span class="sxs-lookup"><span data-stu-id="722b9-109">DROP INDEX when you are dropping a nonclustered index.</span></span>  
  
-   <span data-ttu-id="722b9-110">DROP INDEX，離線卸除叢集索引，而不指定 MOVE TO 子句且非叢集索引不存在時。</span><span class="sxs-lookup"><span data-stu-id="722b9-110">DROP INDEX when you are dropping a clustered index offline without specifying the MOVE TO clause and nonclustered indexes do not exist.</span></span>  
  
-   <span data-ttu-id="722b9-111">CREATE TABLE (PRIMARY KEY 或 UNIQUE 條件約束)</span><span class="sxs-lookup"><span data-stu-id="722b9-111">CREATE TABLE (PRIMARY KEY or UNIQUE constraints)</span></span>  
  
## <a name="index-operations-that-require-additional-disk-space"></a><span data-ttu-id="722b9-112">需要額外磁碟空間的索引作業</span><span class="sxs-lookup"><span data-stu-id="722b9-112">Index Operations That Require Additional Disk Space</span></span>  
 <span data-ttu-id="722b9-113">所有其他索引 DDL 作業在作業期間都需要使用額外的磁碟空間，並需要永久磁碟空間來儲存新的索引結構。</span><span class="sxs-lookup"><span data-stu-id="722b9-113">All other index DDL operations require additional temporary disk space to use during the operation, and permanent disk space to store the new index structure or structures.</span></span>  
  
 <span data-ttu-id="722b9-114">當建立新的索引結構時，舊 (來源) 和新 (目標) 結構在適當的檔案和檔案群組中需要用到磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="722b9-114">When a new index structure is created, disk space for both the old (source) and new (target) structures is required in their appropriate files and filegroups.</span></span> <span data-ttu-id="722b9-115">舊結構要到索引建立交易認可時才會取消配置。</span><span class="sxs-lookup"><span data-stu-id="722b9-115">The old structure is not deallocated until the index creation transaction commits.</span></span>  
  
 <span data-ttu-id="722b9-116">下列索引 DDL 作業會建立新的索引結構，並需要額外的磁碟空間：</span><span class="sxs-lookup"><span data-stu-id="722b9-116">The following index DDL operations create new index structures and require additional disk space:</span></span>  
  
-   <span data-ttu-id="722b9-117">CREATE INDEX</span><span class="sxs-lookup"><span data-stu-id="722b9-117">CREATE INDEX</span></span>  
  
-   <span data-ttu-id="722b9-118">CREATE INDEX WITH DROP_EXISTING</span><span class="sxs-lookup"><span data-stu-id="722b9-118">CREATE INDEX WITH DROP_EXISTING</span></span>  
  
-   <span data-ttu-id="722b9-119">ALTER INDEX REBUILD</span><span class="sxs-lookup"><span data-stu-id="722b9-119">ALTER INDEX REBUILD</span></span>  
  
-   <span data-ttu-id="722b9-120">ALTER TABLE ADD CONSTRAINT (PRIMARY KEY 或 UNIQUE)</span><span class="sxs-lookup"><span data-stu-id="722b9-120">ALTER TABLE ADD CONSTRAINT (PRIMARY KEY or UNIQUE)</span></span>  
  
-   <span data-ttu-id="722b9-121">ALTER TABLE DROP CONSTRAINT (PRIMARY KEY 或 UNIQUE) (當條件約束是以叢集索引為基礎時)</span><span class="sxs-lookup"><span data-stu-id="722b9-121">ALTER TABLE DROP CONSTRAINT (PRIMARY KEY or UNIQUE) when the constraint is based on a clustered index</span></span>  
  
-   <span data-ttu-id="722b9-122">DROP INDEX MOVE TO (僅適用於叢集索引)。</span><span class="sxs-lookup"><span data-stu-id="722b9-122">DROP INDEX MOVE TO (Applies only to clustered indexes.)</span></span>  
  
## <a name="temporary-disk-space-for-sorting"></a><span data-ttu-id="722b9-123">用於排序的暫存磁碟空間</span><span class="sxs-lookup"><span data-stu-id="722b9-123">Temporary Disk Space for Sorting</span></span>  
 <span data-ttu-id="722b9-124">除了來源和目標結構需要磁碟空間之外，排序時也需要暫存磁碟空間，除非查詢最佳化工具找到不需要排序的執行計畫。</span><span class="sxs-lookup"><span data-stu-id="722b9-124">Besides the disk space required for the source and target structures, temporary disk space is required for sorting, unless the query optimizer finds an execution plan that does not require sorting.</span></span>  
  
 <span data-ttu-id="722b9-125">如果需要排序，一次只會對一個新索引進行排序。</span><span class="sxs-lookup"><span data-stu-id="722b9-125">If sorting is required, sorting occurs one new index at a time.</span></span> <span data-ttu-id="722b9-126">例如，當您在單一陳述式內重建叢集索引和相關聯的非叢集索引時，會逐一排序索引。</span><span class="sxs-lookup"><span data-stu-id="722b9-126">For example, when you rebuild a clustered index and associated nonclustered indexes within a single statement, the indexes are sorted one after the other.</span></span> <span data-ttu-id="722b9-127">因此，排序所需的額外暫存磁碟空間必須和作業中最大的索引一樣大。</span><span class="sxs-lookup"><span data-stu-id="722b9-127">Therefore, the additional temporary disk space that is required for sorting only has to be as large as the largest index in the operation.</span></span> <span data-ttu-id="722b9-128">這幾乎都是叢集索引。</span><span class="sxs-lookup"><span data-stu-id="722b9-128">This is almost always the clustered index.</span></span>  
  
 <span data-ttu-id="722b9-129">如果 SORT_IN_TEMPDB 選項設為 ON，則最大的索引必須符合 **tempdb**。</span><span class="sxs-lookup"><span data-stu-id="722b9-129">If the SORT_IN_TEMPDB option is set to ON, the largest index must fit into **tempdb**.</span></span> <span data-ttu-id="722b9-130">雖然此選項會增加建立索引所使用的暫存磁碟空間數量，但只要 **tempdb** 所在的磁碟集與使用者資料庫不同，就可減少建立索引所需的時間。</span><span class="sxs-lookup"><span data-stu-id="722b9-130">Although this option increases the amount of temporary disk space that is used to create an index, it may reduce the time that is required to create an index when **tempdb** is on a set of disks different from the user database.</span></span>  
  
 <span data-ttu-id="722b9-131">如果 SORT_IN_TEMPDB 設為 OFF (預設值)，則每個索引 (包括資料分割索引) 會在其目的地磁碟空間中排序；而且只需要建立新索引結構的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="722b9-131">If SORT_IN_TEMPDB is set to OFF (the default) each index, including partitioned indexes, is sorted in its destination disk space; and only the disk space for the new index structures is required.</span></span>  
  
 <span data-ttu-id="722b9-132">如需計算磁碟空間的範例，請參閱＜ [Index Disk Space Example](index-disk-space-example.md)＞。</span><span class="sxs-lookup"><span data-stu-id="722b9-132">For an example of calculating disk space, see [Index Disk Space Example](index-disk-space-example.md).</span></span>  
  
## <a name="temporary-disk-space-for-online-index-operations"></a><span data-ttu-id="722b9-133">線上索引作業的暫存磁碟空間</span><span class="sxs-lookup"><span data-stu-id="722b9-133">Temporary Disk Space for Online Index Operations</span></span>  
 <span data-ttu-id="722b9-134">在線上執行索引作業時，需要額外的暫存磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="722b9-134">When you perform index operations online, additional temporary disk space is required.</span></span>  
  
 <span data-ttu-id="722b9-135">如果在線上建立、重建或卸除叢集索引，會建立暫存非叢集索引，以便將舊書籤對應至新書籤。</span><span class="sxs-lookup"><span data-stu-id="722b9-135">If a clustered index is created, rebuilt, or dropped online, a temporary nonclustered index is created to map old bookmarks to new bookmarks.</span></span> <span data-ttu-id="722b9-136">如果 SORT_IN_TEMPDB 選項設為 ON，則會在 **tempdb**中建立此暫存索引。</span><span class="sxs-lookup"><span data-stu-id="722b9-136">If the SORT_IN_TEMPDB option is set to ON, this temporary index is created in **tempdb**.</span></span> <span data-ttu-id="722b9-137">如果 SORT_IN_TEMPDB 設為 OFF，會使用與目標索引相同的檔案群組或資料分割結構描述。</span><span class="sxs-lookup"><span data-stu-id="722b9-137">If SORT_IN_TEMPDB is set to OFF, the same filegroup or partition scheme as the target index is used.</span></span> <span data-ttu-id="722b9-138">暫存對應索引為資料表中的每個資料列都包含一筆記錄，而且其內容結合了舊的和新的書籤資料行，包括唯一識別碼和記錄識別碼，並只包括用於這兩個書籤中之所有資料行的單一副本。</span><span class="sxs-lookup"><span data-stu-id="722b9-138">The temporary mapping index contains one record for each row in the table, and its contents is the union of the old and new bookmark columns, including uniqueifiers and record identifiers and including only a single copy of any column used in both bookmarks.</span></span> <span data-ttu-id="722b9-139">如需線上索引作業的詳細資訊，請參閱 [線上執行索引作業](perform-index-operations-online.md)。</span><span class="sxs-lookup"><span data-stu-id="722b9-139">For more information about online index operations, see [Perform Index Operations Online](perform-index-operations-online.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="722b9-140">無法對 DROP INDEX 陳述式設定 SORT_IN_TEMPDB 選項。</span><span class="sxs-lookup"><span data-stu-id="722b9-140">The SORT_IN_TEMPDB option cannot be set for DROP INDEX statements.</span></span> <span data-ttu-id="722b9-141">永遠會在與目標索引相同的檔案群組或資料分割結構描述中，建立暫存對應索引。</span><span class="sxs-lookup"><span data-stu-id="722b9-141">The temporary mapping index is always created in the same filegroup or partition scheme as the target index.</span></span>  
  
 <span data-ttu-id="722b9-142">線上索引作業會使用資料列版本設定來隔離索引作業與其他交易所進行的修改影響。</span><span class="sxs-lookup"><span data-stu-id="722b9-142">Online index operations use row versioning to isolate the index operation from the effects of modifications made by other transactions.</span></span> <span data-ttu-id="722b9-143">這樣可避免在已讀取的資料列上要求共用鎖定。</span><span class="sxs-lookup"><span data-stu-id="722b9-143">This avoids the need for requesting share locks on rows that have been read.</span></span> <span data-ttu-id="722b9-144">線上索引作業期間進行的並行使用者更新和刪除作業，將需要一些空間在 **tempdb**中產生版本記錄。</span><span class="sxs-lookup"><span data-stu-id="722b9-144">Concurrent user update and delete operations during online index operations require space for version records in **tempdb**.</span></span> <span data-ttu-id="722b9-145">如需詳細資訊，請參閱 [線上執行索引作業](perform-index-operations-online.md) 。</span><span class="sxs-lookup"><span data-stu-id="722b9-145">For more information, see [Perform Index Operations Online](perform-index-operations-online.md) .</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="722b9-146">相關工作</span><span class="sxs-lookup"><span data-stu-id="722b9-146">Related Tasks</span></span>  
 [<span data-ttu-id="722b9-147">索引磁碟空間範例</span><span class="sxs-lookup"><span data-stu-id="722b9-147">Index Disk Space Example</span></span>](index-disk-space-example.md)  
  
 [<span data-ttu-id="722b9-148">索引作業的交易記錄磁碟空間</span><span class="sxs-lookup"><span data-stu-id="722b9-148">Transaction Log Disk Space for Index Operations</span></span>](transaction-log-disk-space-for-index-operations.md)  
  
 [<span data-ttu-id="722b9-149">估計資料表的大小</span><span class="sxs-lookup"><span data-stu-id="722b9-149">Estimate the Size of a Table</span></span>](../databases/estimate-the-size-of-a-table.md)  
  
 [<span data-ttu-id="722b9-150">估計叢集索引的大小</span><span class="sxs-lookup"><span data-stu-id="722b9-150">Estimate the Size of a Clustered Index</span></span>](../databases/estimate-the-size-of-a-clustered-index.md)  
  
 [<span data-ttu-id="722b9-151">估計非叢集索引的大小</span><span class="sxs-lookup"><span data-stu-id="722b9-151">Estimate the Size of a Nonclustered Index</span></span>](../databases/estimate-the-size-of-a-nonclustered-index.md)  
  
 [<span data-ttu-id="722b9-152">估計堆積的大小</span><span class="sxs-lookup"><span data-stu-id="722b9-152">Estimate the Size of a Heap</span></span>](../databases/estimate-the-size-of-a-heap.md)  
  
## <a name="related-content"></a><span data-ttu-id="722b9-153">相關內容</span><span class="sxs-lookup"><span data-stu-id="722b9-153">Related Content</span></span>  
 [<span data-ttu-id="722b9-154">CREATE INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="722b9-154">CREATE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
 [<span data-ttu-id="722b9-155">ALTER INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="722b9-155">ALTER INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-index-transact-sql)  
  
 [<span data-ttu-id="722b9-156">DROP INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="722b9-156">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
 [<span data-ttu-id="722b9-157">指定索引的填滿因素</span><span class="sxs-lookup"><span data-stu-id="722b9-157">Specify Fill Factor for an Index</span></span>](specify-fill-factor-for-an-index.md)  
  
 [<span data-ttu-id="722b9-158">重新組織與重建索引</span><span class="sxs-lookup"><span data-stu-id="722b9-158">Reorganize and Rebuild Indexes</span></span>](indexes.md)  
  
  
