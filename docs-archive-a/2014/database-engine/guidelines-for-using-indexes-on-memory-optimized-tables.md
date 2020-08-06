---
title: 在記憶體優化資料表上使用索引的指導方針 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- hash indexes
ms.assetid: 16ef63a4-367a-46ac-917d-9eebc81ab29b
author: stevestein
ms.author: sstein
ms.openlocfilehash: f00d643088634c918eb626917eae64a001ce3678
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701563"
---
# <a name="guidelines-for-using-indexes-on-memory-optimized-tables"></a><span data-ttu-id="a6c82-102">使用記憶體最佳化資料表索引的方針</span><span class="sxs-lookup"><span data-stu-id="a6c82-102">Guidelines for Using Indexes on Memory-Optimized Tables</span></span>
  <span data-ttu-id="a6c82-103">索引是用來有效率地存取 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="a6c82-103">Indexes are used for efficiently accessing data in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tables.</span></span> <span data-ttu-id="a6c82-104">指定正確的索引可以大幅提高查詢效能。</span><span class="sxs-lookup"><span data-stu-id="a6c82-104">Specifying the right indexes can dramatically improve query performance.</span></span> <span data-ttu-id="a6c82-105">假設有以下的查詢範例：</span><span class="sxs-lookup"><span data-stu-id="a6c82-105">Consider, for example, the query:</span></span>  
  
```sql  
SELECT c1, c2 FROM t WHERE c1 = 1;  
```  
  
 <span data-ttu-id="a6c82-106">如果 c1 資料行上沒有索引，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 將必須掃描整個資料表 t，然後篩選滿足 c1=1 條件的資料列。</span><span class="sxs-lookup"><span data-stu-id="a6c82-106">If there is no index on column c1, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will need to scan the entire table t, and then filter on the rows that satisfy the condition c1=1.</span></span> <span data-ttu-id="a6c82-107">不過，如果資料行 c1 上有索引，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 可以直接搜尋 1 的值並擷取資料列。</span><span class="sxs-lookup"><span data-stu-id="a6c82-107">However, if t has an index on column c1, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] can seek directly on the value 1 and retrieve the rows.</span></span>  
  
 <span data-ttu-id="a6c82-108">當搜尋具有特定值或值範圍的記錄來找出資料表中的一個或多個資料行時，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 可以使用這些資料行上的索引來快速尋找對應的記錄。</span><span class="sxs-lookup"><span data-stu-id="a6c82-108">When searching for records that have a specific value, or range of values, for one or more columns in the table, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] can use an index on those columns to quickly locate the corresponding records.</span></span> <span data-ttu-id="a6c82-109">以磁碟為基礎的資料表及記憶體最佳化的資料表都受益於索引。</span><span class="sxs-lookup"><span data-stu-id="a6c82-109">Both disk-based and memory-optimized tables benefit from indexes.</span></span> <span data-ttu-id="a6c82-110">但是，當使用記憶體最佳化資料表時，必須考量索引架構之間的一些差異。</span><span class="sxs-lookup"><span data-stu-id="a6c82-110">There are, however, certain differences between index structures that need to be considered when using memory-optimized tables.</span></span> <span data-ttu-id="a6c82-111">記憶體優化資料表上的 (索引稱為記憶體優化的索引。 ) 部分主要差異如下：</span><span class="sxs-lookup"><span data-stu-id="a6c82-111">(Indexes on memory-optimized tables are referred to as memory-optimized indexes.) Some of the key differences are:</span></span>  
  
-   <span data-ttu-id="a6c82-112">記憶體優化的索引必須使用[CREATE TABLE &#40;transact-sql&#41;](/sql/t-sql/statements/create-table-transact-sql)來建立。</span><span class="sxs-lookup"><span data-stu-id="a6c82-112">Memory-optimized indexes must be created with [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).</span></span> <span data-ttu-id="a6c82-113">以磁碟為基礎的索引可以使用 `CREATE TABLE` 和 `CREATE INDEX` 建立。</span><span class="sxs-lookup"><span data-stu-id="a6c82-113">Disk-based indexes can be created with `CREATE TABLE` and `CREATE INDEX`.</span></span>  
  
-   <span data-ttu-id="a6c82-114">記憶體最佳化的索引只存在於記憶體中。</span><span class="sxs-lookup"><span data-stu-id="a6c82-114">Memory-optimized indexes exist only in memory.</span></span> <span data-ttu-id="a6c82-115">索引結構不會保存到磁碟，且索引作業不會記錄在交易記錄中。</span><span class="sxs-lookup"><span data-stu-id="a6c82-115">Index structures are not persisted to disk and index operations are not logged in the transaction log.</span></span> <span data-ttu-id="a6c82-116">在記憶體中建立記憶體最佳化的資料表時 (在 CREATE TABLE 期間及資料庫啟動期間)，便會建立索引結構。</span><span class="sxs-lookup"><span data-stu-id="a6c82-116">The index structure is created when the memory-optimized table is created in memory, both during CREATE TABLE and during database startup.</span></span>  
  
-   <span data-ttu-id="a6c82-117">記憶體最佳化的索引本質上為涵蓋。</span><span class="sxs-lookup"><span data-stu-id="a6c82-117">Memory-optimized indexes are inherently covering.</span></span> <span data-ttu-id="a6c82-118">涵蓋表示所有資料行幾乎都包含在索引中，且記憶體最佳化資料表不需要書籤查閱。</span><span class="sxs-lookup"><span data-stu-id="a6c82-118">Covering means that all columns are virtually included in the index and bookmark lookups are not needed for memory-optimized tables.</span></span> <span data-ttu-id="a6c82-119">記憶體最佳化的索引只會包含指向資料表資料結構中實際資料列的記憶體指標，而不是主索引鍵的參考。</span><span class="sxs-lookup"><span data-stu-id="a6c82-119">Rather than a reference to the primary key, memory-optimized indexes simply contain a memory pointer to the actual row in the table data structure.</span></span>  
  
-   <span data-ttu-id="a6c82-120">片段和填滿因數不適用於記憶體最佳化索引。</span><span class="sxs-lookup"><span data-stu-id="a6c82-120">Fragmentation and fillfactor do not apply to memory-optimized indexes.</span></span> <span data-ttu-id="a6c82-121">在以磁碟為基礎的索引中，片段指的是未按順序寫入磁碟的 B 型樹狀目錄中的頁面。</span><span class="sxs-lookup"><span data-stu-id="a6c82-121">In disk-based indexes, fragmentation refers to pages in the B-tree being written to disk out-of-order.</span></span> <span data-ttu-id="a6c82-122">記憶體最佳化的索引不會寫入磁碟或從磁碟讀取。</span><span class="sxs-lookup"><span data-stu-id="a6c82-122">Memory-optimized indexes are not written to or read from disk.</span></span> <span data-ttu-id="a6c82-123">以磁碟為基礎的 B 型樹狀目錄索引中的填滿因數指的是實體頁面結構填滿實際資料的程度。</span><span class="sxs-lookup"><span data-stu-id="a6c82-123">Fillfactor in disk-based B-tree indexes refers to the degree to which the physical page structures are filled with actual data.</span></span> <span data-ttu-id="a6c82-124">記憶體最佳化的索引結構沒有固定大小的頁面。</span><span class="sxs-lookup"><span data-stu-id="a6c82-124">The memory-optimized index structures do not have fixed-size pages.</span></span>  
  
 <span data-ttu-id="a6c82-125">記憶體最佳化索引有兩種類型︰</span><span class="sxs-lookup"><span data-stu-id="a6c82-125">There are two types of memory-optimized indexes:</span></span>  
  
-   <span data-ttu-id="a6c82-126">非叢集雜湊索引，適用於點查閱。</span><span class="sxs-lookup"><span data-stu-id="a6c82-126">Nonclustered hash indexes, which are made for point lookups.</span></span> <span data-ttu-id="a6c82-127">如需有關雜湊索引的詳細資訊，請參閱[雜湊索引](hash-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="a6c82-127">For more information about hash indexes, see [Hash Indexes](hash-indexes.md).</span></span>  
  
-   <span data-ttu-id="a6c82-128">非叢集索引，適用於範圍掃描和依序掃描。</span><span class="sxs-lookup"><span data-stu-id="a6c82-128">Nonclustered indexes, which are made for range scans and ordered scans.</span></span>  
  
 <span data-ttu-id="a6c82-129">有了雜湊索引，便會透過記憶體中的雜湊表來存取資料。</span><span class="sxs-lookup"><span data-stu-id="a6c82-129">With a hash index, data is accessed through an in-memory hash table.</span></span> <span data-ttu-id="a6c82-130">雜湊索引沒有頁面，而且一定有固定的大小。</span><span class="sxs-lookup"><span data-stu-id="a6c82-130">Hash indexes do not have pages and are always of a fixed size.</span></span> <span data-ttu-id="a6c82-131">不過，雜湊索引可以有空的雜湊值區，這樣會造成有限的空間浪費。</span><span class="sxs-lookup"><span data-stu-id="a6c82-131">However, a hash index can have empty hash buckets, which result in limited wasted space.</span></span> <span data-ttu-id="a6c82-132">使用雜湊索引從查詢傳回的值，不會進行排序。</span><span class="sxs-lookup"><span data-stu-id="a6c82-132">The values returned from a query using a hash index are not sorted.</span></span> <span data-ttu-id="a6c82-133">雜湊索引已為相等述詞進行索引搜尋最佳化，同時支援完整的索引掃描。</span><span class="sxs-lookup"><span data-stu-id="a6c82-133">Hash indexes are optimized for index seeks on equality predicates and also support full index scans.</span></span>  
  
 <span data-ttu-id="a6c82-134">非叢集索引 (不是雜湊索引) 支援雜湊索引所支援的所有項目，而且還可在不等述詞 (例如大於或小於，以及排序順序) 上進行搜尋作業。</span><span class="sxs-lookup"><span data-stu-id="a6c82-134">Nonclustered indexes (not hash indexes) support everything that hash indexes supports plus seek operations on inequality predicates such as greater than or less than, as well as sort order.</span></span> <span data-ttu-id="a6c82-135">您可以根據索引建立時的指定順序進行資料列擷取。</span><span class="sxs-lookup"><span data-stu-id="a6c82-135">Rows can be retrieved according to the order specified with index creation.</span></span> <span data-ttu-id="a6c82-136">如果索引的排序次序符合特定查詢所需的排序次序 (例如，索引鍵符合 ORDER BY 子句)，在查詢執行期間就不需要排序資料列。</span><span class="sxs-lookup"><span data-stu-id="a6c82-136">If the sort order of the index matches the sort order required for a particular query, for example if the index key matches the ORDER BY clause, there is no need to sort the rows as part of query execution.</span></span> <span data-ttu-id="a6c82-137">記憶體最佳化的非叢集索引是單向索引，因此進行資料列擷取時，不支援與索引排序次序反向的排序次序。</span><span class="sxs-lookup"><span data-stu-id="a6c82-137">Memory-optimized nonclustered indexes are unidirectional; they do not support retrieving rows in a sort order that is the reverse of the sort order of the index.</span></span> <span data-ttu-id="a6c82-138">例如，若將索引指定為 (c1 ASC)，您就無法以反向順序 (c1 DESC) 掃描索引。</span><span class="sxs-lookup"><span data-stu-id="a6c82-138">For example, for an index specified as (c1 ASC), it is not possible to scan the index in reverse order, as (c1 DESC).</span></span>  
  
 <span data-ttu-id="a6c82-139">每個索引都會耗用記憶體。</span><span class="sxs-lookup"><span data-stu-id="a6c82-139">Each index consumes memory.</span></span> <span data-ttu-id="a6c82-140">雜湊索引會耗用固定數量的記憶體，也就是值區計數的函數。</span><span class="sxs-lookup"><span data-stu-id="a6c82-140">Hash indexes consume a fixed amount of memory, which is a function of the bucket count.</span></span> <span data-ttu-id="a6c82-141">對於非叢集索引，記憶體耗用量是資料列計數和索引鍵資料行大小的函式，並視工作負載之不同，還有一些額外的負擔。</span><span class="sxs-lookup"><span data-stu-id="a6c82-141">For nonclustered indexes, memory consumption is a function of the row count and the size of the index key columns, with some additional overhead depending on the workload.</span></span> <span data-ttu-id="a6c82-142">進行記憶體最佳化索引的記憶體，是除了用以儲存記憶體最佳化資料表中資料列的記憶體之外，額外的個別記憶體。</span><span class="sxs-lookup"><span data-stu-id="a6c82-142">Memory for memory-optimized indexes is in addition to and separate from the memory used to store rows in memory-optimized tables.</span></span>  
  
 <span data-ttu-id="a6c82-143">重複的鍵值一律會共用相同的雜湊值區。</span><span class="sxs-lookup"><span data-stu-id="a6c82-143">Duplicate key values always share the same hash bucket.</span></span> <span data-ttu-id="a6c82-144">如果雜湊索引包含許多重複的鍵值，所產生的長雜湊鏈結將危害到效能。</span><span class="sxs-lookup"><span data-stu-id="a6c82-144">If a hash index contains many duplicate key values, the resulting long hash chains will harm performance.</span></span> <span data-ttu-id="a6c82-145">在這個案例中，發生在任何雜湊索引中的雜湊衝突將進一步降低效能。</span><span class="sxs-lookup"><span data-stu-id="a6c82-145">Hash collisions, which occur in any hash index, will further reduce performance in this scenario.</span></span> <span data-ttu-id="a6c82-146">基於這個理由，如果唯一索引鍵的數目至少100倍小於資料列計數，您可以將值區計數縮小 (至少八倍唯一索引鍵的數目，藉此降低雜湊衝突的風險。如需) 的詳細資訊，請參閱[判斷雜湊索引的正確](../../2014/database-engine/determining-the-correct-bucket-count-for-hash-indexes.md)值區計數，或者您可以使用非叢集索引來完全消除雜湊衝突。</span><span class="sxs-lookup"><span data-stu-id="a6c82-146">For that reason, if the number of unique index keys is at least 100 times smaller than the row count, you can reduce the risk of hash collisions by making the bucket count much larger (at least eight times the number of unique index keys; see [Determining the Correct Bucket Count for Hash Indexes](../../2014/database-engine/determining-the-correct-bucket-count-for-hash-indexes.md) for more information) or you can eliminate hash collisions entirely by using a nonclustered index.</span></span>  
  
## <a name="determining-which-indexes-to-use-for-a-memory-optimized-table"></a><span data-ttu-id="a6c82-147">判斷哪些索引要用於記憶體最佳化的資料表</span><span class="sxs-lookup"><span data-stu-id="a6c82-147">Determining Which Indexes to Use for a Memory-Optimized Table</span></span>  
 <span data-ttu-id="a6c82-148">每個記憶體最佳化資料表至少必須有一個索引。</span><span class="sxs-lookup"><span data-stu-id="a6c82-148">Each memory-optimized table must have at least one index.</span></span> <span data-ttu-id="a6c82-149">請注意，每個 PRIMARY KEY 條件約束都會隱含地建立索引。</span><span class="sxs-lookup"><span data-stu-id="a6c82-149">Note that each PRIMARY KEY constraint implicitly creates an index.</span></span> <span data-ttu-id="a6c82-150">因此，如果資料表有主索引鍵，就表示它有索引。</span><span class="sxs-lookup"><span data-stu-id="a6c82-150">Therefore, if a table has a primary key, it has an index.</span></span> <span data-ttu-id="a6c82-151">持久的記憶體最佳化的資料表需要主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="a6c82-151">A primary key is a requirement for a durable memory-optimized table.</span></span>  
  
 <span data-ttu-id="a6c82-152">查詢記憶體最佳化資料表時，雜湊索引在述詞子句只包含相等述詞時的效能更佳。</span><span class="sxs-lookup"><span data-stu-id="a6c82-152">When querying a memory-optimized table, hash indexes perform better when the predicate clause contains only equality predicates.</span></span> <span data-ttu-id="a6c82-153">述詞必須包含雜湊索引鍵中的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="a6c82-153">The predicate must include all columns in the hash index key.</span></span> <span data-ttu-id="a6c82-154">若是不相等的述詞，雜湊索引會還原至掃描。</span><span class="sxs-lookup"><span data-stu-id="a6c82-154">A hash index will revert to a scan given an inequality predicate.</span></span>  
  
 <span data-ttu-id="a6c82-155">記憶體最佳化資料表中的資料行，可以是雜湊索引和非叢集索引的一部分。</span><span class="sxs-lookup"><span data-stu-id="a6c82-155">A column in a memory-optimized table can be part of both a hash index and a nonclustered index.</span></span>  
  
 <span data-ttu-id="a6c82-156">利用不相等述詞查詢記憶體最佳化資料表時，非叢集索引的效能比非叢集雜湊索引的效能好。</span><span class="sxs-lookup"><span data-stu-id="a6c82-156">When querying a memory-optimized table with inequality predicates, nonclustered indexes will perform better than nonclustered hash indexes.</span></span>  
  
 <span data-ttu-id="a6c82-157">雜湊索引需要索引鍵 (進行雜湊) 以在索引中尋找。</span><span class="sxs-lookup"><span data-stu-id="a6c82-157">The hash index requires a key (to hash) to seek into the index.</span></span> <span data-ttu-id="a6c82-158">如果索引鍵包含兩個資料行，而您只提供了第一個資料行，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 不會有完整的索引鍵可進行雜湊。</span><span class="sxs-lookup"><span data-stu-id="a6c82-158">If an index key consists of two columns and you only provide the first column, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] does not have a complete key to hash.</span></span> <span data-ttu-id="a6c82-159">如此會導致索引掃描查詢計劃。</span><span class="sxs-lookup"><span data-stu-id="a6c82-159">This will result in an index scan query plan.</span></span> <span data-ttu-id="a6c82-160">使用方法會決定應對哪些資料行編製索引。</span><span class="sxs-lookup"><span data-stu-id="a6c82-160">Usage determines which columns should be indexed.</span></span>  
  
 <span data-ttu-id="a6c82-161">非叢集索引的資料行若有許多資料列具有相同的值 (索引鍵資料行有許多重複的值)，效能可能會因為更新、插入及刪除而降低。</span><span class="sxs-lookup"><span data-stu-id="a6c82-161">When a column in a nonclustered index has the same value in many rows (index key columns have a lot of duplicate values), performance can degrade for updates, inserts, and deletions.</span></span>  <span data-ttu-id="a6c82-162">在此情況下，改善效能的其中一種方法就是在非叢集索引中加入其他資料行。</span><span class="sxs-lookup"><span data-stu-id="a6c82-162">One way to improve performance in this situation is to add another column to the nonclustered index.</span></span>  
  
### <a name="operations-on-memory-optimized-and-disk-based-indexes"></a><span data-ttu-id="a6c82-163">針對記憶體最佳化的索引以及以磁碟為基礎的索引所執行的作業。</span><span class="sxs-lookup"><span data-stu-id="a6c82-163">Operations on memory-optimized and disk-based indexes.</span></span>  
  
|<span data-ttu-id="a6c82-164">作業</span><span class="sxs-lookup"><span data-stu-id="a6c82-164">Operation</span></span>|<span data-ttu-id="a6c82-165">記憶體最佳化、非叢集雜湊、索引</span><span class="sxs-lookup"><span data-stu-id="a6c82-165">Memory-optimized, nonclustered hash, index</span></span>|<span data-ttu-id="a6c82-166">記憶體最佳化的非叢集索引</span><span class="sxs-lookup"><span data-stu-id="a6c82-166">Memory-optimized nonclustered index</span></span>|<span data-ttu-id="a6c82-167">磁碟型索引</span><span class="sxs-lookup"><span data-stu-id="a6c82-167">Disk-based index</span></span>|  
|---------------|-------------------------------------------------|------------------------------------------|-----------------------|  
|<span data-ttu-id="a6c82-168">索引掃描，擷取所有資料表資料列。</span><span class="sxs-lookup"><span data-stu-id="a6c82-168">Index Scan, retrieve all table rows.</span></span>|<span data-ttu-id="a6c82-169">是</span><span class="sxs-lookup"><span data-stu-id="a6c82-169">Yes</span></span>|<span data-ttu-id="a6c82-170">是</span><span class="sxs-lookup"><span data-stu-id="a6c82-170">Yes</span></span>|<span data-ttu-id="a6c82-171">是</span><span class="sxs-lookup"><span data-stu-id="a6c82-171">Yes</span></span>|  
|<span data-ttu-id="a6c82-172">等號比較述詞 (=) 的索引搜尋。</span><span class="sxs-lookup"><span data-stu-id="a6c82-172">Index seek on equality predicate(s) (=).</span></span>|<span data-ttu-id="a6c82-173">是</span><span class="sxs-lookup"><span data-stu-id="a6c82-173">Yes</span></span><br /><br /> <span data-ttu-id="a6c82-174">(需要完整金鑰。)</span><span class="sxs-lookup"><span data-stu-id="a6c82-174">(Full key required.)</span></span>|<span data-ttu-id="a6c82-175">是 <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a6c82-175">Yes <sup>1</sup></span></span>|<span data-ttu-id="a6c82-176">是</span><span class="sxs-lookup"><span data-stu-id="a6c82-176">Yes</span></span>|  
|<span data-ttu-id="a6c82-177">不等號比較述詞的索引搜尋 ( # A0、<、 \<=, > =、) 之間。</span><span class="sxs-lookup"><span data-stu-id="a6c82-177">Index seek on inequality predicates (>, <, \<=, >=, BETWEEN).</span></span>|<span data-ttu-id="a6c82-178">否 (產生索引掃描)</span><span class="sxs-lookup"><span data-stu-id="a6c82-178">No (results in an index scan)</span></span>|<span data-ttu-id="a6c82-179">是 <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a6c82-179">Yes <sup>1</sup></span></span>|<span data-ttu-id="a6c82-180">是</span><span class="sxs-lookup"><span data-stu-id="a6c82-180">Yes</span></span>|  
|<span data-ttu-id="a6c82-181">依照排序次序擷取符合索引定義的資料列。</span><span class="sxs-lookup"><span data-stu-id="a6c82-181">Retrieve rows in a sort-order matching the index definition.</span></span>|<span data-ttu-id="a6c82-182">否</span><span class="sxs-lookup"><span data-stu-id="a6c82-182">No</span></span>|<span data-ttu-id="a6c82-183">是</span><span class="sxs-lookup"><span data-stu-id="a6c82-183">Yes</span></span>|<span data-ttu-id="a6c82-184">是</span><span class="sxs-lookup"><span data-stu-id="a6c82-184">Yes</span></span>|  
|<span data-ttu-id="a6c82-185">依照排序次序擷取符合相反索引定義的資料列。</span><span class="sxs-lookup"><span data-stu-id="a6c82-185">Retrieve rows in a sort-order matching the reverse of the index definition.</span></span>|<span data-ttu-id="a6c82-186">否</span><span class="sxs-lookup"><span data-stu-id="a6c82-186">No</span></span>|<span data-ttu-id="a6c82-187">否</span><span class="sxs-lookup"><span data-stu-id="a6c82-187">No</span></span>|<span data-ttu-id="a6c82-188">是</span><span class="sxs-lookup"><span data-stu-id="a6c82-188">Yes</span></span>|  
  
 <span data-ttu-id="a6c82-189">在表格中，「是」表示索引可以適當地為要求提供服務，「否」則表示無法順利使用索引來滿足要求。</span><span class="sxs-lookup"><span data-stu-id="a6c82-189">In the table, Yes means that the index can adequately service the request and No means that the index cannot be used successfully to satisfy the request.</span></span>  
  
 <span data-ttu-id="a6c82-190"><sup>1</sup>若是非叢集記憶體優化索引，則不需要使用完整索引鍵來執行索引搜尋。</span><span class="sxs-lookup"><span data-stu-id="a6c82-190"><sup>1</sup> For a nonclustered memory-optimized index, the full key is not required to perform an index seek.</span></span> <span data-ttu-id="a6c82-191">即使索引鍵有資料行順序，如果資料行的值出現在遺漏的資料行之後，仍會發生掃描。</span><span class="sxs-lookup"><span data-stu-id="a6c82-191">Although, given the column order of the index key, a scan will occur if a value for a column comes after a missing column.</span></span>  
  
## <a name="index-count"></a><span data-ttu-id="a6c82-192">索引計數</span><span class="sxs-lookup"><span data-stu-id="a6c82-192">Index Count</span></span>  
 <span data-ttu-id="a6c82-193">記憶體最佳化的資料表最多可以有 8 個索引，包括使用主索引鍵建立的索引。</span><span class="sxs-lookup"><span data-stu-id="a6c82-193">A memory-optimized table can have up to 8 indexes, including the index created with the primary key.</span></span>  
  
 <span data-ttu-id="a6c82-194">有關記憶體最佳化的資料表上建立的索引數目，請考慮以下事項：</span><span class="sxs-lookup"><span data-stu-id="a6c82-194">Regarding the number of indexes created on a memory-optimized table, consider the following:</span></span>  
  
-   <span data-ttu-id="a6c82-195">當您建立資料表時，指定您需要的索引。</span><span class="sxs-lookup"><span data-stu-id="a6c82-195">Specify the indexes you need when you create the table.</span></span> <span data-ttu-id="a6c82-196">在建立記憶體最佳化的資料表之後，您就無法為此資料表建立索引。</span><span class="sxs-lookup"><span data-stu-id="a6c82-196">You cannot create an index for a memory-optimized table after the table is created.</span></span> <span data-ttu-id="a6c82-197">如果您想要在記憶體最佳化的資料表中加入索引，請卸除該資料表並重新建立。</span><span class="sxs-lookup"><span data-stu-id="a6c82-197">If you want to add an index to a memory-optimized table, drop and recreate that table.</span></span>  
  
-   <span data-ttu-id="a6c82-198">請勿建立您很少使用的索引：</span><span class="sxs-lookup"><span data-stu-id="a6c82-198">Do not create an index that you rarely use:</span></span>  
  
     <span data-ttu-id="a6c82-199">如果資料表上的索引都經常使用，記憶體回收的效果最好。</span><span class="sxs-lookup"><span data-stu-id="a6c82-199">Garbage collection works best if all indexes on the table are frequently used.</span></span> <span data-ttu-id="a6c82-200">很少使用的索引可能會造成記憶體回收系統對舊的資料列版本無法達到最佳執行效果。</span><span class="sxs-lookup"><span data-stu-id="a6c82-200">Rarely-used indexes may cause the garbage collection system to not perform optimally for old row versions.</span></span>  
  
## <a name="creating-a-memory-optimized-index-code-samples"></a><span data-ttu-id="a6c82-201">建立記憶體最佳化索引：程式碼範例</span><span class="sxs-lookup"><span data-stu-id="a6c82-201">Creating a Memory-Optimized Index: Code Samples</span></span>  
 <span data-ttu-id="a6c82-202">資料行層級雜湊索引：</span><span class="sxs-lookup"><span data-stu-id="a6c82-202">Column level hash index:</span></span>  
  
```sql  
CREATE TABLE t1   
   (c1 INT NOT NULL INDEX idx HASH WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 <span data-ttu-id="a6c82-203">資料表層級雜湊索引：</span><span class="sxs-lookup"><span data-stu-id="a6c82-203">Table level hash index:</span></span>  
  
```sql  
CREATE TABLE t1_1   
   (c1 INT NOT NULL,   
   INDEX IDX HASH (c1) WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 <span data-ttu-id="a6c82-204">資料行層級主索引鍵雜湊索引：</span><span class="sxs-lookup"><span data-stu-id="a6c82-204">Column level primary key hash index:</span></span>  
  
```sql  
CREATE TABLE t2   
   (c1 INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 <span data-ttu-id="a6c82-205">資料表層級主索引鍵雜湊索引：</span><span class="sxs-lookup"><span data-stu-id="a6c82-205">Table level primary key hash index:</span></span>  
  
```sql  
CREATE TABLE t2_2   
   (c1 INT NOT NULL,   
   PRIMARY KEY NONCLUSTERED HASH (c1) WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 <span data-ttu-id="a6c82-206">資料行層級非叢集索引：</span><span class="sxs-lookup"><span data-stu-id="a6c82-206">Column level nonclustered index:</span></span>  
  
```sql  
CREATE TABLE t3   
   (c1 INT NOT NULL INDEX ID)   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 <span data-ttu-id="a6c82-207">資料表層級非叢集索引：</span><span class="sxs-lookup"><span data-stu-id="a6c82-207">Table level nonclustered  index:</span></span>  
  
```sql  
CREATE TABLE t3_3   
   (c1 INT NOT NULL,   
   INDEX IDX NONCLUSTERED (c1))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 <span data-ttu-id="a6c82-208">資料行層級主索引鍵非叢集索引：</span><span class="sxs-lookup"><span data-stu-id="a6c82-208">Column level primary key nonclustered  index:</span></span>  
  
```sql  
CREATE TABLE t4   
   (c1 INT NOT NULL PRIMARY KEY NONCLUSTERED)   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 <span data-ttu-id="a6c82-209">資料表層級主索引鍵非叢集索引：</span><span class="sxs-lookup"><span data-stu-id="a6c82-209">Table level primary key nonclustered index:</span></span>  
  
```sql  
CREATE TABLE t4_4   
   (c1 INT NOT NULL,   
   PRIMARY KEY NONCLUSTERED (c1))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 <span data-ttu-id="a6c82-210">定義資料行之後所定義的多資料行索引：</span><span class="sxs-lookup"><span data-stu-id="a6c82-210">Multicolumn index defined after columns are defined:</span></span>  
  
```sql  
create table t (  
       a int not null constraint ta primary key nonclustered,  
       b int not null,  
       c int not null,  
       d int not null,  
       index idx_t_b_c_d nonclustered (b, c asc, d desc)  
) with (memory_optimized = on, durability = SCHEMA_AND_DATA)  
go  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6c82-211">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6c82-211">See Also</span></span>  
 <span data-ttu-id="a6c82-212">[記憶體優化資料表上的索引](../relational-databases/in-memory-oltp/memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="a6c82-212">[Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="a6c82-213">[判斷雜湊索引的正確值區計數](../../2014/database-engine/determining-the-correct-bucket-count-for-hash-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="a6c82-213">[Determining the Correct Bucket Count for Hash Indexes](../../2014/database-engine/determining-the-correct-bucket-count-for-hash-indexes.md) </span></span>  
 [<span data-ttu-id="a6c82-214">雜湊索引</span><span class="sxs-lookup"><span data-stu-id="a6c82-214">Hash Indexes</span></span>](hash-indexes.md)  
  
  
