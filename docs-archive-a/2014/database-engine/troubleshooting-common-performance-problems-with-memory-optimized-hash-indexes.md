---
title: 針對記憶體優化雜湊索引的常見效能問題進行疑難排解 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 1954a997-7585-4713-81fd-76d429b8d095
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3cef98571edd7736bc45ba8caf17451007a74cf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687141"
---
# <a name="troubleshooting-common-performance-problems-with-memory-optimized-hash-indexes"></a><span data-ttu-id="49133-102">疑難排解記憶體最佳化雜湊索引的常見效能問題</span><span class="sxs-lookup"><span data-stu-id="49133-102">Troubleshooting Common Performance Problems with Memory-Optimized Hash Indexes</span></span>
  <span data-ttu-id="49133-103">本主題將焦點放在疑難排解以及解決與雜湊索引相關的常見問題。</span><span class="sxs-lookup"><span data-stu-id="49133-103">This topic will focus on troubleshooting and working around common issues with hash indexes.</span></span>  
  
## <a name="search-requires-a-subset-of-hash-index-key-columns"></a><span data-ttu-id="49133-104">搜尋需要雜湊索引鍵資料行的子集</span><span class="sxs-lookup"><span data-stu-id="49133-104">Search Requires a Subset of Hash Index Key Columns</span></span>  
 <span data-ttu-id="49133-105">**問題：** 雜湊索引需要所有索引鍵資料行的值，才能計算雜湊值，並在雜湊表中找出對應的資料列。</span><span class="sxs-lookup"><span data-stu-id="49133-105">**Issue:** Hash indexes require values for all index key columns in order to compute the hash value, and locate the corresponding rows in the hash table.</span></span> <span data-ttu-id="49133-106">因此，如果查詢只包含 WHERE 子句中索引鍵子集的等號比較述詞，則 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 無法使用索引搜尋找出對應 WHERE 子句中述詞的資料列。</span><span class="sxs-lookup"><span data-stu-id="49133-106">Therefore, if a query includes equality predicates for only a subset of the index keys in the WHERE clause, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cannot use an index seek to locate the rows corresponding to the predicates in the WHERE clause.</span></span>  
  
 <span data-ttu-id="49133-107">相反地，只要索引鍵資料行是索引中的前置資料行，像是磁碟非叢集索引和記憶體最佳化非叢集索引這類已排序索引就可支援在這些資料行的子集上進行索引搜尋。</span><span class="sxs-lookup"><span data-stu-id="49133-107">In contrast, ordered indexes like the disk-based nonclustered indexes and the memory-optimized nonclustered indexes support index seek on a subset of the index key columns, as long as they are the leading columns in the index.</span></span>  
  
 <span data-ttu-id="49133-108">**徵兆：** 這會導致效能降低，因為 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 需要執行完整資料表掃描，而不是索引搜尋，這通常是較快速的作業。</span><span class="sxs-lookup"><span data-stu-id="49133-108">**Symptom:** This results in a performance degradation, as [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] needs to execute full table scans rather than an index seek, which is typically a faster operation.</span></span>  
  
 <span data-ttu-id="49133-109">**如何進行疑難排解：** 除了效能降低之外，查詢計劃的檢查會顯示掃描，而不是索引搜尋。</span><span class="sxs-lookup"><span data-stu-id="49133-109">**How to troubleshoot:** Besides the performance degradation, inspection of the query plans will show a scan instead of an index seek.</span></span> <span data-ttu-id="49133-110">如果查詢相當簡單，則查詢文字和索引定義的檢查也會指出搜尋需要索引鍵資料行的子集。</span><span class="sxs-lookup"><span data-stu-id="49133-110">If the query is fairly simple, inspection of the query text and index definition will also show whether the search requires a subset of the index key columns.</span></span>  
  
 <span data-ttu-id="49133-111">請考慮下列資料表和查詢：</span><span class="sxs-lookup"><span data-stu-id="49133-111">Consider the following table and query:</span></span>  
  
```sql  
CREATE TABLE [dbo].[od]  
(  
     o_id INT NOT NULL,  
     od_id INT NOT NULL,  
     p_id INT NOT NULL,  
     CONSTRAINT PK_od PRIMARY KEY NONCLUSTERED HASH (o_id, od_id) WITH (BUCKET_COUNT = 10000)  
)  
WITH (MEMORY_OPTIMIZED = ON)  
  
 SELECT p_id  
 FROM dbo.od  
 WHERE o_id=1  
```  
  
 <span data-ttu-id="49133-112">資料表的兩個資料行 (o_id、od_id) 上有雜湊索引，而查詢在 (o_id) 上有等號比較述詞。</span><span class="sxs-lookup"><span data-stu-id="49133-112">The table has a hash index on the two columns (o_id, od_id), while the query has an equality predicate on (o_id).</span></span> <span data-ttu-id="49133-113">由於查詢只會在索引鍵資料行的子集上擁有等號比較述詞，因此 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 無法使用 PK_od 執行索引搜尋作業，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 必須改為轉換成完整索引掃描。</span><span class="sxs-lookup"><span data-stu-id="49133-113">As the query has equality predicates on only a subset of the index key columns, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cannot perform an index seek operation using PK_od; instead, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] has to revert to a full index scan.</span></span>  
  
 <span data-ttu-id="49133-114">因應措施 **：** 有一些可能的因應措施。</span><span class="sxs-lookup"><span data-stu-id="49133-114">**Workarounds:** There are a number of possible workarounds.</span></span> <span data-ttu-id="49133-115">例如：</span><span class="sxs-lookup"><span data-stu-id="49133-115">For example:</span></span>  
  
-   <span data-ttu-id="49133-116">重建索引做為非叢集類型，而不是非叢集雜湊。</span><span class="sxs-lookup"><span data-stu-id="49133-116">Recreate the index as type nonclustered instead of nonclustered hash.</span></span> <span data-ttu-id="49133-117">記憶體最佳化非叢集索引已經過排序，因此 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 可以在前置索引鍵資料行上執行索引搜尋。</span><span class="sxs-lookup"><span data-stu-id="49133-117">The memory-optimized nonclustered index is ordered, and thus [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] can perform an index seek on the leading index key columns.</span></span> <span data-ttu-id="49133-118">範例產生的主索引鍵定義會是 `constraint PK_od primary key nonclustered`。</span><span class="sxs-lookup"><span data-stu-id="49133-118">The resulting primary key definition for the example would be `constraint PK_od primary key nonclustered`.</span></span>  
  
-   <span data-ttu-id="49133-119">變更目前的索引鍵以符合 WHERE 子句中的資料行。</span><span class="sxs-lookup"><span data-stu-id="49133-119">Change the current index key to match the columns in the WHERE clause.</span></span>  
  
-   <span data-ttu-id="49133-120">加入與查詢的 WHERE 子句中資料行相符的新雜湊索引。</span><span class="sxs-lookup"><span data-stu-id="49133-120">Add a new hash index that matches with the columns in the WHERE clause of the query.</span></span> <span data-ttu-id="49133-121">在此範例中，產生的資料表定義如下：</span><span class="sxs-lookup"><span data-stu-id="49133-121">In the example, the resulting table definition would look at follows:</span></span>  
  
    ```sql  
    CREATE TABLE dbo.od  
     ( o_id INT NOT NULL,  
     od_id INT NOT NULL,  
     p_id INT NOT NULL,  
  
     CONSTRAINT PK_od PRIMARY KEY   
     NONCLUSTERED HASH (o_id,od_id) WITH (BUCKET_COUNT=10000),  
  
     INDEX ix_o_id NONCLUSTERED HASH (o_id) WITH (BUCKET_COUNT=10000)  
  
     ) WITH (MEMORY_OPTIMIZED=ON)  
    ```  
  
 <span data-ttu-id="49133-122">請注意，如果某個索引鍵值具有大量重複的資料列，則記憶體最佳化雜湊索引不會以最佳方式執行：在範例中，如果資料行 o_id 的唯一值數目比資料表中資料列的數目少許多，則在 (o_id) 上加入索引並不是最好的方式，較佳的解決方法是將索引 PK_od 的類型從雜湊變更為非叢集。</span><span class="sxs-lookup"><span data-stu-id="49133-122">Note that a memory-optimized hash index does not perform optimally if there are a lot of duplicate rows for a given index key value: in the example, if the number of unique values for the column o_id is much smaller than the number of rows in the table, it would not be optimal to add an index on (o_id); instead, changing the type of the index PK_od from hash to nonclustered would be the better solution.</span></span> <span data-ttu-id="49133-123">如需詳細資訊，請參閱＜ [Determining the Correct Bucket Count for Hash Indexes](../relational-databases/indexes/indexes.md)＞。</span><span class="sxs-lookup"><span data-stu-id="49133-123">For more information, see [Determining the Correct Bucket Count for Hash Indexes](../relational-databases/indexes/indexes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49133-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49133-124">See Also</span></span>  
 [<span data-ttu-id="49133-125">記憶體最佳化資料表上的索引</span><span class="sxs-lookup"><span data-stu-id="49133-125">Indexes on Memory-Optimized Tables</span></span>](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
  
