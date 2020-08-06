---
title: 估計記憶體最佳化資料表的記憶體需求 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 5c5cc1fc-1fdf-4562-9443-272ad9ab5ba8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5c5218a96d3650cbae22501ab2794b1b553996b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706505"
---
# <a name="estimate-memory-requirements-for-memory-optimized-tables"></a><span data-ttu-id="8b6bc-102">估計記憶體最佳化資料表的記憶體需求</span><span class="sxs-lookup"><span data-stu-id="8b6bc-102">Estimate Memory Requirements for Memory-Optimized Tables</span></span>
  <span data-ttu-id="8b6bc-103">不論您是建立新的 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 記憶體優化資料表，或是將現有的磁片資料表遷移至記憶體優化資料表，都一定要有合理的估計值來滿足每個資料表的記憶體需求，讓您可以使用足夠的記憶體來布建伺服器。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-103">Whether you are creating a new [!INCLUDE[hek_2](../../includes/hek-2-md.md)] memory-optimized table or migrating an existing disk-based table to a memory-optimized table, it is important to have a reasonable estimate of each table's memory needs so you can provision the server with sufficient memory.</span></span> <span data-ttu-id="8b6bc-104">本節描述如何估計保存記憶體最佳化資料表的資料所需的記憶體數目。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-104">This section describes how to estimate the amount of memory that you need to hold data for a memory-optimized table.</span></span>  
  
 <span data-ttu-id="8b6bc-105">如果您想從磁碟資料表移轉至記憶體最佳化資料表，請在進行本主題之前，先參閱 [判斷是否應將資料表或預存程序匯出至記憶體中 OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md) 主題，以取得最適合移轉之資料表的指引。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-105">If you are contemplating migrating from disk-based tables to memory-optimized tables, before you proceed in this topic, see the topic [Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md) for guidance on which tables are best to migrate.</span></span> <span data-ttu-id="8b6bc-106">[移轉至 In-Memory OLTP](migrating-to-in-memory-oltp.md) 底下的所有主題，提供從磁碟資料表移轉至記憶體最佳化資料表的指引。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-106">All the topics under [Migrating to In-Memory OLTP](migrating-to-in-memory-oltp.md) provide guidance on migrating from disk-based to memory-optimized tables.</span></span>  
  
## <a name="sections-in-this-topic"></a><span data-ttu-id="8b6bc-107">本主題的章節</span><span class="sxs-lookup"><span data-stu-id="8b6bc-107">Sections in this topic</span></span>  
  
-   [<span data-ttu-id="8b6bc-108">記憶體最佳化資料表範例</span><span class="sxs-lookup"><span data-stu-id="8b6bc-108">Example memory-optimized table</span></span>](#bkmk_ExampleTable)  
  
-   [<span data-ttu-id="8b6bc-109">配置給資料表的記憶體</span><span class="sxs-lookup"><span data-stu-id="8b6bc-109">Memory for the table</span></span>](#bkmk_MemoryForTable)  
  
-   [<span data-ttu-id="8b6bc-110">配置給索引的記憶體</span><span class="sxs-lookup"><span data-stu-id="8b6bc-110">Memory for indexes</span></span>](#bkmk_IndexMeemory)  
  
-   [<span data-ttu-id="8b6bc-111">配置給資料列版本設定的記憶體</span><span class="sxs-lookup"><span data-stu-id="8b6bc-111">Memory for row versioning</span></span>](#bkmk_MemoryForRowVersions)  
  
-   [<span data-ttu-id="8b6bc-112">配置給資料表變數的記憶體</span><span class="sxs-lookup"><span data-stu-id="8b6bc-112">Memory for table variables</span></span>](#bkmk_TableVariables)  
  
-   [<span data-ttu-id="8b6bc-113">配置給成長的記憶體</span><span class="sxs-lookup"><span data-stu-id="8b6bc-113">Memory for growth</span></span>](#bkmk_MemoryForGrowth)  
  
##  <a name="example-memory-optimized-table"></a><a name="bkmk_ExampleTable"></a> <span data-ttu-id="8b6bc-114">記憶體最佳化資料表範例</span><span class="sxs-lookup"><span data-stu-id="8b6bc-114">Example memory-optimized table</span></span>  
 <span data-ttu-id="8b6bc-115">請考慮下列記憶體最佳化資料表結構描述：</span><span class="sxs-lookup"><span data-stu-id="8b6bc-115">Consider the following memory-optimized table schema:</span></span>  
  
```sql  
  
CREATE TABLE t_hk (  
col1 int NOT NULL PRIMARY KEY NONCLUSTERED,  
col2 int NOT NULL INDEX t1c2_index   
     HASH WITH (bucket_count = 5000000),  
col3 int NOT NULL INDEX t1c3_index   
     HASH WITH (bucket_count = 5000000),  
col4 int NOT NULL INDEX t1c4_index   
     HASH WITH (bucket_count = 5000000),  
col5 int NOT NULL INDEX t1c5_index NONCLUSTERED,  
col6 char (50) NOT NULL,  
col7 char (50) NOT NULL,   
col8 char (30) NOT NULL,   
col9 char (50) NOT NULL  
     WITH (memory_optimized = on)  
GO  
  
```  
  
 <span data-ttu-id="8b6bc-116">我們將透過此結構描述，來判斷此記憶體最佳化資料所需的最小記憶體。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-116">Using this schema we will determine the minimum memory needed for this memory-optimized table.</span></span>  
  
##  <a name="memory-for-the-table"></a><a name="bkmk_MemoryForTable"></a> <span data-ttu-id="8b6bc-117">配置給資料表的記憶體</span><span class="sxs-lookup"><span data-stu-id="8b6bc-117">Memory for the table</span></span>  
 <span data-ttu-id="8b6bc-118">記憶體最佳化資料表資料列包含三個部分：</span><span class="sxs-lookup"><span data-stu-id="8b6bc-118">A memory-optimized table row is comprised of three parts:</span></span>  
  
-   <span data-ttu-id="8b6bc-119">**時間戳記** </span><span class="sxs-lookup"><span data-stu-id="8b6bc-119">**Timestamps** </span></span>  
    <span data-ttu-id="8b6bc-120">資料列標頭/時間戳記 = 24 個位元組。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-120">Row header/timestamps = 24 bytes.</span></span>  
  
-   <span data-ttu-id="8b6bc-121">**索引指標** </span><span class="sxs-lookup"><span data-stu-id="8b6bc-121">**Index pointers** </span></span>  
    <span data-ttu-id="8b6bc-122">針對資料表中的每個雜湊索引，每個資料列具有 8 位元組位址指標，指向索引的下一個資料列。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-122">For each hash index in the table, each row has an 8-byte address pointer to the next row in the index.</span></span>  <span data-ttu-id="8b6bc-123">由於有 4 個索引，因此每個資料列都會配置 32 個位元組給索引指標 (每個索引有 8 位元組指標)。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-123">Since there are 4 indexes, each row will allocate 32 bytes for index pointers (an 8 byte pointer for each index).</span></span>  
  
-   <span data-ttu-id="8b6bc-124">**資料** </span><span class="sxs-lookup"><span data-stu-id="8b6bc-124">**Data** </span></span>  
    <span data-ttu-id="8b6bc-125">資料列的資料部分大小是由每個資料行的類型大小總和來判斷。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-125">The size of the data portion of the row is determined by summing the type size for each data column.</span></span>  <span data-ttu-id="8b6bc-126">在資料表中，我們有五個 4 位元組整數、三個 50 位元組字元資料行，以及一個 30 位元組字元資料行。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-126">In our table we have five 4-byte integers, three 50-byte character columns, and one 30-byte character column.</span></span>  <span data-ttu-id="8b6bc-127">因此，每個資料列的資料部分為 4 + 4 + 4 + 4 + 4 + 50 + 50 + 30 + 50 (或 200) 個位元組。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-127">Therefore the data portion of each row is 4 + 4 + 4 + 4 + 4 + 50 + 50 + 30 + 50 or 200 bytes.</span></span>  
  
 <span data-ttu-id="8b6bc-128">以下是記憶體最佳化資料表中 5,000,000 (5 百萬) 個資料列的大小計算。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-128">The following is a size computation for 5,000,000 (5 million) rows in a memory-optimized table.</span></span> <span data-ttu-id="8b6bc-129">資料列所使用的記憶體總數估計如下：</span><span class="sxs-lookup"><span data-stu-id="8b6bc-129">The total memory used by data rows is estimated as follows:</span></span>  
  
 <span data-ttu-id="8b6bc-130">**配置給資料表資料列的記憶體**</span><span class="sxs-lookup"><span data-stu-id="8b6bc-130">**Memory for the table's rows**</span></span>  
  
 <span data-ttu-id="8b6bc-131">從上述計算得知，記憶體最佳化資料表的每個資料列大小為 24 + 32 + 200 (或 256) 個位元組。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-131">From the above calculations, the size of each row in the memory-optimized table is 24 + 32 + 200, or 256 bytes.</span></span>  <span data-ttu-id="8b6bc-132">由於我們有 5 百萬個資料列，因此資料表會耗用 5,000,000 \* 256 (或 1,280,000,000) 個位元組，大約是 1.28 GB。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-132">Since we have 5 million rows, the table will consume 5,000,000 \* 256 bytes, or 1,280,000,000 bytes - approximately 1.28 GB.</span></span>  
  
##  <a name="memory-for-indexes"></a><a name="bkmk_IndexMeemory"></a> <span data-ttu-id="8b6bc-133">配置給索引的記憶體</span><span class="sxs-lookup"><span data-stu-id="8b6bc-133">Memory for indexes</span></span>  
 <span data-ttu-id="8b6bc-134">**配置給每個雜湊索引的記憶體**</span><span class="sxs-lookup"><span data-stu-id="8b6bc-134">**Memory for each hash index**</span></span>  
  
 <span data-ttu-id="8b6bc-135">每個雜湊索引是 8 位元組位址指標的雜湊陣列。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-135">Each hash index is a hash array of 8-byte address pointers.</span></span>  <span data-ttu-id="8b6bc-136">陣列的大小是由該索引的唯一索引值數目來判斷；例如，t1c2_index 的陣列大小可以從唯一的 Col2 值數目開始。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-136">The size of the array is best determined by the number of unique index values for that index - e.g., the number of unique Col2 values is a good starting point for the array size for the t1c2_index.</span></span> <span data-ttu-id="8b6bc-137">雜湊陣列太大會浪費記憶體。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-137">A hash array that is too big wastes memory.</span></span>  <span data-ttu-id="8b6bc-138">雜湊陣列太小會降低效能，因為雜湊處理至相同索引的索引值會引起太多衝突。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-138">A hash array that is too small slows performance since there will be too many collisions by index values that hash to the same index.</span></span>  
  
 <span data-ttu-id="8b6bc-139">雜湊索引的等式查閱速度很快，例如：</span><span class="sxs-lookup"><span data-stu-id="8b6bc-139">Hash indexes achieve very fast equality lookups such as:</span></span>  
  
```sql  
  
SELECT * FROM t_hk  
   WHERE Col2 = 3  
  
```  
  
 <span data-ttu-id="8b6bc-140">非叢集索引的範圍查閱更快，例如：</span><span class="sxs-lookup"><span data-stu-id="8b6bc-140">Nonclustered indexes are faster for range lookups such as:</span></span>  
  
```sql  
  
SELECT * FROM t_hk  
   WHERE Col2 >= 3  
  
```  
  
 <span data-ttu-id="8b6bc-141">如果您想移轉磁碟資料表，您可以使用下列程式碼來判斷 index t1c2_index 的唯一值數目。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-141">If you are migrating a disk-based table you can use the following to determine the number of unique values for the index t1c2_index.</span></span>  
  
```sql  
  
SELECT COUNT(DISTINCT [Col2])  
  FROM t_hk  
  
```  
  
 <span data-ttu-id="8b6bc-142">如果您想建立新的資料表，則需要估計陣列大小，或在部署前從測試收集資料。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-142">If you are creating a new table, you'll need to estimate the array size or gather data from your testing prior to deployment.</span></span>  
  
 <span data-ttu-id="8b6bc-143">如需雜湊索引在 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 記憶體最佳化資料表中運作方式的相關資訊，請參閱 [雜湊索引](../../database-engine/hash-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-143">For information on how hash indexes work in [!INCLUDE[hek_2](../../includes/hek-2-md.md)] memory-optimized tables, see [Hash Indexes](../../database-engine/hash-indexes.md).</span></span>  
  
 <span data-ttu-id="8b6bc-144">**注意：** 您無法即時變更雜湊索引陣列大小。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-144">**Note:** You cannot change the hash index array size on the fly.</span></span> <span data-ttu-id="8b6bc-145">若要變更雜湊索引陣列大小，您必須卸除資料表、變更 bucket_count 值，然後重新建立資料表。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-145">To change the hash index array size you must drop the table, change the bucket_count value and recreate the table.</span></span>  
  
 <span data-ttu-id="8b6bc-146">**設定雜湊索引陣列大小**</span><span class="sxs-lookup"><span data-stu-id="8b6bc-146">**Setting the hash index array size**</span></span>  
  
 <span data-ttu-id="8b6bc-147">雜湊陣列大小是由 `(bucket_count= <value>)` 設定，其中 \<value> 是大於零的整數值。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-147">The hash array size is set by `(bucket_count= <value>)` where \<value> is an integer value greater than zero.</span></span> <span data-ttu-id="8b6bc-148">如果 \<value> 不是 2 的乘冪，實際的 bucket_count 會無條件進位到下一個最接近的 2 的乘冪。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-148">If \<value> is not a power of 2, the actual bucket_count is rounded up to the next closest power of 2.</span></span>  <span data-ttu-id="8b6bc-149">在我們的範例資料表中， (bucket_count = 5000000) ，因為5000000不是2的乘冪，所以實際的值區計數會無條件舍入至 8388608 (2<sup>23</sup>) 。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-149">In our example table, (bucket_count = 5000000), since 5,000,000 is not a power of 2, the actual bucket count rounds up to 8,388,608 (2<sup>23</sup>).</span></span>  <span data-ttu-id="8b6bc-150">計算雜湊陣列所需的記憶體時，您必須使用此數值，而不是 5,000,000。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-150">You must use this number, not 5,000,000 when calculating memory needed by the hash array.</span></span>  
  
 <span data-ttu-id="8b6bc-151">因此在此範例中，每個雜湊陣列所需的記憶體為：</span><span class="sxs-lookup"><span data-stu-id="8b6bc-151">Thus, in our example, the memory needed for each hash array is:</span></span>  
  
 <span data-ttu-id="8b6bc-152">8388608 \* 8 = 2<sup>23</sup> \* 8 = 2<sup>23</sup> \* 2<sup>3</sup> = 2<sup>26</sup> = 67108864 或大約 64 MB。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-152">8,388,608 \* 8 = 2<sup>23</sup> \* 8 = 2<sup>23</sup> \* 2<sup>3</sup> = 2<sup>26</sup> = 67,108,864 or approximately 64 MB.</span></span>  
  
 <span data-ttu-id="8b6bc-153">由於我們有三個雜湊索引，因此雜湊索引所需的記憶體為 3 \* 64MB = 192MB。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-153">Since we have three hash indexes, the memory needed for the hash indexes is 3 \* 64MB = 192MB.</span></span>  
  
 <span data-ttu-id="8b6bc-154">**非叢集索引的記憶體**</span><span class="sxs-lookup"><span data-stu-id="8b6bc-154">**Memory for nonclustered indexes**</span></span>  
  
 <span data-ttu-id="8b6bc-155">非叢集索引會以 BTree 實作，其內部節點包含索引值，以及指向後續節點的指標。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-155">Nonclustered indexes are implemented as BTrees with the inner nodes containing the index value and pointers to subsequent nodes.</span></span>  <span data-ttu-id="8b6bc-156">分葉節點包含索引值，以及一個指向記憶體中資料表資料列的指標。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-156">Leaf nodes contain the index value and a pointer to the table row in memory.</span></span>  
  
 <span data-ttu-id="8b6bc-157">不同於雜湊索引，非叢集索引沒有固定的貯體大小。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-157">Unlike hash indexes, nonclustered indexes do not have a fixed bucket size.</span></span> <span data-ttu-id="8b6bc-158">此索引會隨資料動態成長和壓縮。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-158">The index grows and shrinks dynamically with the data.</span></span>  
  
 <span data-ttu-id="8b6bc-159">非叢集索引所需的記憶體，計算方式如下：</span><span class="sxs-lookup"><span data-stu-id="8b6bc-159">Memory needed by nonclustered indexes can be computed as follows:</span></span>  
  
-   <span data-ttu-id="8b6bc-160">**配置給非分葉節點的記憶體** </span><span class="sxs-lookup"><span data-stu-id="8b6bc-160">**Memory allocated to non-leaf nodes** </span></span>  
    <span data-ttu-id="8b6bc-161">在一般組態中，配置給非分葉節點的記憶體只佔索引所使用之整體記憶體的很小比例。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-161">For a typical configuration, the memory allocated to non-leaf nodes is a small percentage of the overall memory taken by the index.</span></span> <span data-ttu-id="8b6bc-162">因為很小，所以可以放心忽略。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-162">This is so small it can safely be ignored.</span></span>  
  
-   <span data-ttu-id="8b6bc-163">**配置給分葉節點的記憶體** </span><span class="sxs-lookup"><span data-stu-id="8b6bc-163">**Memory for leaf nodes** </span></span>  
    <span data-ttu-id="8b6bc-164">分葉節點中對於資料表內的每個唯一索引鍵都有一個資料列，指向該唯一索引鍵的資料列。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-164">The leaf nodes have one row for each unique key in the table that points to the data rows with that unique key.</span></span>  <span data-ttu-id="8b6bc-165">如果相同索引鍵有多個資料列 (亦即有非唯一的非叢集索引)，則索引分葉節點中只有一個資料列會指向其中一個資料列，而其他資料列會彼此連結。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-165">If you have multiple rows with the same key (i.e., you have a non-unique nonclustered index), there is only one row in the index leaf node that points to one of the rows with the other rows linked to each other.</span></span>  <span data-ttu-id="8b6bc-166">因此，所需的總記憶體大約是：</span><span class="sxs-lookup"><span data-stu-id="8b6bc-166">Thus, the total memory required can be approximated by:</span></span>   
    <span data-ttu-id="8b6bc-167">memoryForNonClusteredIndex = (pointerSize + sum(keyColumnDataTypeSizes)) \* rowsWithUniqueKeys</span><span class="sxs-lookup"><span data-stu-id="8b6bc-167">memoryForNonClusteredIndex = (pointerSize + sum(keyColumnDataTypeSizes)) \* rowsWithUniqueKeys</span></span>  
  
 <span data-ttu-id="8b6bc-168">非叢集索引最適合用於範圍查閱，如下列查詢所示：</span><span class="sxs-lookup"><span data-stu-id="8b6bc-168">Nonclustered indexes are best when used for range lookups, as exemplified by the following query:</span></span>  
  
```sql  
  
SELECT * FROM t_hk  
   WHERE c2 > 5  
```  
  
##  <a name="memory-for-row-versioning"></a><a name="bkmk_MemoryForRowVersions"></a> <span data-ttu-id="8b6bc-169">配置給資料列版本設定的記憶體</span><span class="sxs-lookup"><span data-stu-id="8b6bc-169">Memory for row versioning</span></span>  
 <span data-ttu-id="8b6bc-170">更新或刪除資料列時，記憶體中 OLTP 會使用開放式並行存取來避免鎖定。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-170">To avoid locks, In-Memory OLTP uses optimistic concurrency when updating or deleting rows.</span></span> <span data-ttu-id="8b6bc-171">這表示當更新資料列時，會建立該資料列的其他版本。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-171">This means that when a row is updated, an additional version of the row is created.</span></span> <span data-ttu-id="8b6bc-172">在可能使用舊版本的所有交易完成執行之前，系統會保留舊版本可用。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-172">The system keeps the previous versions available until all transactions that could possibly use the version have finished execution.</span></span> <span data-ttu-id="8b6bc-173">刪除資料列時，系統會以類似更新的方式來執行，並保留版本可用，直到不再需要為止。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-173">When a row is deleted, the system acts in a similar way to an update, keeping the version available until it is no longer necessary.</span></span> <span data-ttu-id="8b6bc-174">讀取和插入並不會建立額外的資料列版本資料。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-174">Reads and inserts do not create additional row versions.</span></span>  
  
 <span data-ttu-id="8b6bc-175">由於等待記憶體回收循環釋放記憶體時，記憶體中可能會有許多其他的資料列，因此您必須有足夠的記憶體來容納這些其他的資料列。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-175">Because there may be a number of additional rows in memory at any time waiting for the garbage collection cycle to release their memory, you must have sufficient memory to accommodate these additional rows.</span></span>  
  
 <span data-ttu-id="8b6bc-176">您可以計算每秒更新和刪除的最大資料列數目，然後乘以最久的交易所需的秒數 (至少為 1)，來估計其他資料列的數目。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-176">The number of additional rows can be estimated by computing the peak number of row updates and deletions per second, then multiplying that by the number of seconds the longest transaction takes (minimum of 1).</span></span>  
  
 <span data-ttu-id="8b6bc-177">該值接著會乘以資料列大小，以取得設定資料列版本設定所需的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-177">That value is then multiplied by the row size to get the number of bytes you need for row versioning.</span></span>  
  
 `rowVersions = durationOfLongestTransactionInSeconds * peakNumberOfRowUpdatesOrDeletesPerSecond`  
  
 <span data-ttu-id="8b6bc-178">接著會將過時資料列數目乘以記憶體優化資料表資料列的大小，來估計過時資料列的記憶體需求 (查看) 上[表的記憶體](#bkmk_MemoryForTable)。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-178">Memory needs for stale rows is then estimated by multiplying the number of stale rows by the size of a memory-optimized table row (see [Memory for the table](#bkmk_MemoryForTable) above).</span></span>  
  
 `memoryForRowVersions = rowVersions * rowSize`  
  
##  <a name="memory-for-table-variables"></a><a name="bkmk_TableVariables"></a> <span data-ttu-id="8b6bc-179">配置給資料表變數的記憶體</span><span class="sxs-lookup"><span data-stu-id="8b6bc-179">Memory for table variables</span></span>  
 <span data-ttu-id="8b6bc-180">資料表變數所使用的記憶體只會在資料表變數超出範圍時釋出。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-180">Memory used for a table variable is released only when the table variable goes out of scope.</span></span> <span data-ttu-id="8b6bc-181">從資料表變數中刪除的資料列 (包括隨更新刪除的資料列) 則不受記憶體回收限制。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-181">Deleted rows, including rows deleted as part of an update, from a table variable are not subject to garbage collection.</span></span> <span data-ttu-id="8b6bc-182">在資料表變數離開範圍之前，不會釋出記憶體。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-182">No memory is released until the table variable exits scope.</span></span>  
  
 <span data-ttu-id="8b6bc-183">在大型 SQL 批次中定義的資料表變數 (與程序範圍相反) 會在許多交易中使用，且可能會耗用大量的記憶體。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-183">Table variables defined in a large SQL batch, as opposed to a procedure scope, which are used in many transactions, can consume a lot of memory.</span></span> <span data-ttu-id="8b6bc-184">由於它們不會進行記憶體回收，因此資料表變數中已刪除的資料列可能會耗用大量記憶體並降低效能，因為讀取作業需要掃描已刪除的資料列。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-184">Because they are not garbage collected, deleted rows in a table variable can consume a lot memory and degrade performance since read operations need to scan past the deleted rows.</span></span>  
  
##  <a name="memory-for-growth"></a><a name="bkmk_MemoryForGrowth"></a> <span data-ttu-id="8b6bc-185">配置給成長的記憶體</span><span class="sxs-lookup"><span data-stu-id="8b6bc-185">Memory for growth</span></span>  
 <span data-ttu-id="8b6bc-186">上述計算依資料表的現狀來估計資料表的記憶體需求。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-186">The above calculations estimate your memory needs for the table as it currently exists.</span></span> <span data-ttu-id="8b6bc-187">除了此記憶體之外，您還需要估計資料表的成長，並提供足夠的記憶體來容納該成長幅度。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-187">In addition to this memory, you need to estimate the growth of the table and provide sufficient memory to accommodate that growth.</span></span>  <span data-ttu-id="8b6bc-188">例如，如果您預期會成長 10%，則需要將上述結果乘以 1.1，以取得資料表所需的總記憶體。</span><span class="sxs-lookup"><span data-stu-id="8b6bc-188">For example, if you anticipate 10% growth then you need to multiple the results from above by 1.1 to get the total memory needed for your table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b6bc-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b6bc-189">See Also</span></span>  
 [<span data-ttu-id="8b6bc-190">移轉至 In-Memory OLTP</span><span class="sxs-lookup"><span data-stu-id="8b6bc-190">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
