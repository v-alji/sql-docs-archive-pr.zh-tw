---
title: 判斷雜湊索引的正確值區計數 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6d1ac280-87db-4bd8-ad43-54353647d8b5
author: stevestein
ms.author: sstein
ms.openlocfilehash: e0579a98e3302b6944f68ca449d3e7cda0ecc01d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593555"
---
# <a name="determining-the-correct-bucket-count-for-hash-indexes"></a><span data-ttu-id="975dd-102">判斷雜湊索引的正確值區計數</span><span class="sxs-lookup"><span data-stu-id="975dd-102">Determining the Correct Bucket Count for Hash Indexes</span></span>
  <span data-ttu-id="975dd-103">您必須在建立記憶體最佳化資料表時，指定 `BUCKET_COUNT` 參數的值。</span><span class="sxs-lookup"><span data-stu-id="975dd-103">You must specify a value for the `BUCKET_COUNT` parameter when you create the memory-optimized table.</span></span> <span data-ttu-id="975dd-104">本主題將針對判斷適合 `BUCKET_COUNT` 參數的值提出建議。</span><span class="sxs-lookup"><span data-stu-id="975dd-104">This topic makes recommendations for determining the appropriate value for the `BUCKET_COUNT` parameter.</span></span> <span data-ttu-id="975dd-105">如果您無法判斷正確的值區計數，請改用非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="975dd-105">If you cannot determine the correct bucket count, use a nonclustered index instead.</span></span>  <span data-ttu-id="975dd-106">不正確的 `BUCKET_COUNT` 值 (尤其是過低的值) 可能會對工作負載的效能以及資料庫的復原時間造成嚴重影響。</span><span class="sxs-lookup"><span data-stu-id="975dd-106">An incorrect `BUCKET_COUNT` value, especially one that is too low, can significantly impact workload performance, as well as recovery time of the database.</span></span> <span data-ttu-id="975dd-107">最好是高估值區計數。</span><span class="sxs-lookup"><span data-stu-id="975dd-107">It is better to overestimate the bucket count.</span></span>  
  
 <span data-ttu-id="975dd-108">重複的索引鍵可能會因為雜湊索引而降低效能，因為索引鍵會雜湊到相同的貯體，使得貯體的鏈結增加。</span><span class="sxs-lookup"><span data-stu-id="975dd-108">Duplicate index keys can decrease performance with a hash index because the keys are hashed to the same bucket, causing that bucket's chain to increase.</span></span>  
  
 <span data-ttu-id="975dd-109">如需有關非叢集雜湊索引的詳細資訊，請參閱＜ [Hash Indexes](hash-indexes.md) ＞和＜ [Guidelines for Using Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md)＞。</span><span class="sxs-lookup"><span data-stu-id="975dd-109">For more information about nonclustered hash indexes, see [Hash Indexes](hash-indexes.md) and [Guidelines for Using Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="975dd-110">針對記憶體最佳化的資料表上的每個雜湊索引配置一個雜湊表。</span><span class="sxs-lookup"><span data-stu-id="975dd-110">One hash table is allocated for each hash index on a memory-optimized table.</span></span> <span data-ttu-id="975dd-111">配置給索引的雜湊表大小是由 `BUCKET_COUNT` [CREATE TABLE &#40;transact-sql&#41;](/sql/t-sql/statements/create-table-transact-sql)或[CREATE TYPE &#40;transact-sql&#41;](/sql/t-sql/statements/create-type-transact-sql)中的參數所指定。</span><span class="sxs-lookup"><span data-stu-id="975dd-111">The size of the hash table allocated for an index is specified by the `BUCKET_COUNT` parameter in [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) or [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).</span></span> <span data-ttu-id="975dd-112">值區計數會於內部四捨五入進位至下一個二的乘冪。</span><span class="sxs-lookup"><span data-stu-id="975dd-112">The bucket count will internally be rounded up to the next power of two.</span></span> <span data-ttu-id="975dd-113">例如，指定值區計數 300,000 將產生實際值區計數 524,288。</span><span class="sxs-lookup"><span data-stu-id="975dd-113">For example, specifying a bucket count of 300,000 will result in an actual bucket count of 524,288.</span></span>  
  
 <span data-ttu-id="975dd-114">如需有關貯體計數的文章和視訊的連結，請參閱 [如何判斷雜湊索引的正確貯體計數 (記憶體內 OLTP)](https://www.mssqltips.com/sqlservertip/3104/determine-bucketcount-for-hash-indexes-for-sql-server-memory-optimized-tables/)。</span><span class="sxs-lookup"><span data-stu-id="975dd-114">For links to an article and video on bucket count, see [How to determine the right bucket count for hash indexes (In-Memory OLTP)](https://www.mssqltips.com/sqlservertip/3104/determine-bucketcount-for-hash-indexes-for-sql-server-memory-optimized-tables/).</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="975dd-115">建議</span><span class="sxs-lookup"><span data-stu-id="975dd-115">Recommendations</span></span>  
 <span data-ttu-id="975dd-116">在大部分情況下，值區計數應該介於索引鍵中相異值數目的 1 到 2 倍之間。</span><span class="sxs-lookup"><span data-stu-id="975dd-116">In most cases the bucket count should be between 1 and 2 times the number of distinct values in the index key.</span></span> <span data-ttu-id="975dd-117">如果索引鍵包含許多重複的值，平均每個索引鍵值都有超過 10 個資料列，則改用非叢集索引</span><span class="sxs-lookup"><span data-stu-id="975dd-117">If the index key contains a lot of duplicate values, on average there are more than 10 rows for each index key value, use a nonclustered index instead</span></span>  
  
 <span data-ttu-id="975dd-118">您不一定能夠預測某個特定索引鍵可能擁有或將會擁有多少個值。</span><span class="sxs-lookup"><span data-stu-id="975dd-118">You may not always be able to predict how many values a particular index key may have or will have.</span></span> <span data-ttu-id="975dd-119">如果 `BUCKET_COUNT` 值在索引鍵值實際數目的 5 倍以內，則效能應該是可以接受的。</span><span class="sxs-lookup"><span data-stu-id="975dd-119">Performance should be acceptable if the `BUCKET_COUNT` value is within 5 times of the actual number of key values.</span></span>  
  
 <span data-ttu-id="975dd-120">若要判斷現有資料中的唯一索引鍵數目，請使用類似下列範例的查詢：</span><span class="sxs-lookup"><span data-stu-id="975dd-120">To determine the number of unique index keys in existing data, use queries similar to the following examples:</span></span>  
  
### <a name="primary-key-and-unique-indexes"></a><span data-ttu-id="975dd-121">主索引鍵和唯一索引</span><span class="sxs-lookup"><span data-stu-id="975dd-121">Primary Key and Unique Indexes</span></span>  
 <span data-ttu-id="975dd-122">由於主索引鍵的索引是唯一的，因此索引鍵中的相異值數目會對應資料表中資料列的數目。</span><span class="sxs-lookup"><span data-stu-id="975dd-122">Because the primary key index is unique, the number of distinct values in the key corresponds to the number of rows in the table.</span></span> <span data-ttu-id="975dd-123">針對 AdventureWorks 資料庫的 Sales.SalesOrderDetail 資料表中 (SalesOrderID, SalesOrderDetailID) 上的主索引鍵，發出下列查詢來計算相異主索引鍵值的數目，該數目對應資料表中資料列的數目：</span><span class="sxs-lookup"><span data-stu-id="975dd-123">For an example primary key on (SalesOrderID, SalesOrderDetailID) in the table Sales.SalesOrderDetail in the AdventureWorks database, issue the following query to calculate the number of distinct primary key values, which corresponds to the number of rows in the table:</span></span>  
  
```sql  
SELECT COUNT(*) AS [row count]   
FROM Sales.SalesOrderDetail  
```  
  
 <span data-ttu-id="975dd-124">此查詢會顯示資料列計數 121,317。</span><span class="sxs-lookup"><span data-stu-id="975dd-124">This query shows a row count of 121,317.</span></span> <span data-ttu-id="975dd-125">如果資料列計數不會大幅變更，請使用值區計數 240,000。</span><span class="sxs-lookup"><span data-stu-id="975dd-125">Use a bucket count of 240,000 if the row count will not change significantly.</span></span> <span data-ttu-id="975dd-126">如果資料表中的銷售訂單數目預計會變成四倍，請使用值區計數 480,000。</span><span class="sxs-lookup"><span data-stu-id="975dd-126">Use a bucket count of 480,000 if the number of sales orders in the table is expected to quadruple.</span></span>  
  
### <a name="non-unique-indexes"></a><span data-ttu-id="975dd-127">非唯一索引</span><span class="sxs-lookup"><span data-stu-id="975dd-127">Non-Unique Indexes</span></span>  
 <span data-ttu-id="975dd-128">對於其他索引，例如 (SpecialOfferID, ProductID) 上的多重資料行索引，發出下列查詢來判斷唯一索引鍵值的數目：</span><span class="sxs-lookup"><span data-stu-id="975dd-128">For other indexes, for example a multi-column index on (SpecialOfferID, ProductID), issue the following query to determine the number of unique index key values:</span></span>  
  
```sql  
SELECT COUNT(*) AS [SpecialOfferID_ProductID index key count]  
FROM   
   (SELECT DISTINCT SpecialOfferID, ProductID   
    FROM Sales.SalesOrderDetail) t  
```  
  
 <span data-ttu-id="975dd-129">此查詢會針對 (SpecialOfferID, ProductID) 傳回索引鍵計數 484，表示應該使用非叢集索引而不是非叢集雜湊索引。</span><span class="sxs-lookup"><span data-stu-id="975dd-129">This query returns an index key count for (SpecialOfferID, ProductID) of 484, indicating a that a nonclustered index should be used instead of a nonclustered hash index.</span></span>  
  
### <a name="determining-the-number-of-duplicates"></a><span data-ttu-id="975dd-130">判斷重複數目</span><span class="sxs-lookup"><span data-stu-id="975dd-130">Determining the Number of Duplicates</span></span>  
 <span data-ttu-id="975dd-131">若要判斷索引鍵值的重複值平均數目，請將資料列總數除以唯一索引鍵數目。</span><span class="sxs-lookup"><span data-stu-id="975dd-131">To determine the average number of duplicate values for an index key value, divide the total number of rows by the number of unique index keys.</span></span>  
  
 <span data-ttu-id="975dd-132">針對 (SpecialOfferID, ProductID) 上的範例索引，此運算為 121317 / 484 = 251。</span><span class="sxs-lookup"><span data-stu-id="975dd-132">For the example index on (SpecialOfferID, ProductID), this leads to 121317 / 484 = 251.</span></span> <span data-ttu-id="975dd-133">這表示索引鍵值的平均為 251，因此應該是非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="975dd-133">This means index key values have an average of 251, and thus this should be a nonclustered index.</span></span>  
  
## <a name="troubleshooting-the-bucket-count"></a><span data-ttu-id="975dd-134">對值區計數進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="975dd-134">Troubleshooting the Bucket Count</span></span>  
 <span data-ttu-id="975dd-135">若要對記憶體優化資料表中的值區計數問題進行疑難排解，請使用[dm_db_xtp_hash_index_stats sys.databases &#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-hash-index-stats-transact-sql)來取得有關空值區和資料列鏈長度的統計資料。</span><span class="sxs-lookup"><span data-stu-id="975dd-135">To troubleshoot bucket count issues in memory-optimized tables, use [sys.dm_db_xtp_hash_index_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-hash-index-stats-transact-sql) to obtain statistics about the empty buckets and the length of row chains.</span></span> <span data-ttu-id="975dd-136">下列查詢可用來取得目前資料庫中所有雜湊索引的相關統計資料。</span><span class="sxs-lookup"><span data-stu-id="975dd-136">The following query can be used to obtain statistics about all the hash indexes in the current database.</span></span> <span data-ttu-id="975dd-137">如果資料庫中有大型資料表，則查詢可能需要幾分鐘才能完成。</span><span class="sxs-lookup"><span data-stu-id="975dd-137">The query can take several minutes to run if there are large tables in the database.</span></span>  
  
```sql  
SELECT   
   object_name(hs.object_id) AS 'object name',   
   i.name as 'index name',   
   hs.total_bucket_count,  
   hs.empty_bucket_count,  
   floor((cast(empty_bucket_count as float)/total_bucket_count) * 100) AS 'empty_bucket_percent',  
   hs.avg_chain_length,   
   hs.max_chain_length  
FROM sys.dm_db_xtp_hash_index_stats AS hs   
   JOIN sys.indexes AS i   
   ON hs.object_id=i.object_id AND hs.index_id=i.index_id  
```  
  
 <span data-ttu-id="975dd-138">雜湊索引健全狀況的兩個重要指標為：</span><span class="sxs-lookup"><span data-stu-id="975dd-138">The two key indicators of hash index health are:</span></span>  
  
 <span data-ttu-id="975dd-139">*empty_bucket_percent*</span><span class="sxs-lookup"><span data-stu-id="975dd-139">*empty_bucket_percent*</span></span>  
 <span data-ttu-id="975dd-140">*empty_bucket_percent* 指出雜湊索引中的空白貯體數目。</span><span class="sxs-lookup"><span data-stu-id="975dd-140">*empty_bucket_percent* indicates the number of empty buckets in the hash index.</span></span>  
  
 <span data-ttu-id="975dd-141">如果 *empty_bucket_percent* 小於 10%，表示這個值區計數可能太低。</span><span class="sxs-lookup"><span data-stu-id="975dd-141">If *empty_bucket_percent* is less than 10 percent, the bucket count is likely to be too low.</span></span> <span data-ttu-id="975dd-142">理想的 *empty_bucket_percent* 應該是 33% 或更高。</span><span class="sxs-lookup"><span data-stu-id="975dd-142">Ideally, the *empty_bucket_percent* should be 33 percent or greater.</span></span> <span data-ttu-id="975dd-143">若值區計數與索引鍵值相符，則約 1/3 的貯體數目為空白，原因是雜湊散發。</span><span class="sxs-lookup"><span data-stu-id="975dd-143">If the bucket count matches the number of index key values, about 1/3 of the buckets is empty, due to hash distribution.</span></span>  
  
 <span data-ttu-id="975dd-144">*avg_chain_length*</span><span class="sxs-lookup"><span data-stu-id="975dd-144">*avg_chain_length*</span></span>  
 <span data-ttu-id="975dd-145">*avg_chain_length* 指出雜湊值區中資料列鏈結的平均長度。</span><span class="sxs-lookup"><span data-stu-id="975dd-145">*avg_chain_length* indicates the average length of the row chains in the hash buckets.</span></span>  
  
 <span data-ttu-id="975dd-146">如果 *avg_chain_length* 大於 10，且 *empty_bucket_percent* 大於 10%，則可能有許多重複的索引鍵值，那麼非叢集索引會較為理想。</span><span class="sxs-lookup"><span data-stu-id="975dd-146">If *avg_chain_length* is greater than 10 and *empty_bucket_percent* is greater than 10 percent, there likely are many duplicate index key values and a nonclustered index would be more appropriate.</span></span> <span data-ttu-id="975dd-147">理想的平均鏈結長度為 1。</span><span class="sxs-lookup"><span data-stu-id="975dd-147">An average chain length of 1 is ideal.</span></span>  
  
 <span data-ttu-id="975dd-148">影響鏈結長度的因素有兩個：</span><span class="sxs-lookup"><span data-stu-id="975dd-148">There are two factors that impact the chain length:</span></span>  
  
1.  <span data-ttu-id="975dd-149">重複項目；所有重複的資料列屬於雜湊索引中的同一個鏈結。</span><span class="sxs-lookup"><span data-stu-id="975dd-149">Duplicates; all duplicate rows are part of the same chain in the hash index.</span></span>  
  
2.  <span data-ttu-id="975dd-150">多個索引鍵值對應到相同貯體。</span><span class="sxs-lookup"><span data-stu-id="975dd-150">Multiple key values map to the same bucket.</span></span> <span data-ttu-id="975dd-151">值區計數越低，就會有越多的貯體擁有對應的多個值。</span><span class="sxs-lookup"><span data-stu-id="975dd-151">The lower the bucket count, the more buckets that will have multiple values mapped to them.</span></span>  
  
 <span data-ttu-id="975dd-152">以下列資料表和指令碼為例，將範例資料列插入資料表中：</span><span class="sxs-lookup"><span data-stu-id="975dd-152">As an example, consider the following table and script to insert sample rows in the table:</span></span>  
  
```sql  
CREATE TABLE [Sales].[SalesOrderHeader_test]  
(  
   [SalesOrderID] [uniqueidentifier] NOT NULL DEFAULT (newid()),  
   [OrderSequence] int NOT NULL,  
   [OrderDate] [datetime2](7) NOT NULL,  
   [Status] [tinyint] NOT NULL,  
  
PRIMARY KEY NONCLUSTERED HASH ([SalesOrderID]) WITH ( BUCKET_COUNT = 262144 ),  
INDEX IX_OrderSequence HASH (OrderSequence) WITH ( BUCKET_COUNT = 20000),  
INDEX IX_Status HASH ([Status]) WITH ( BUCKET_COUNT = 8),  
INDEX IX_OrderDate NONCLUSTERED ([OrderDate] ASC),  
)WITH ( MEMORY_OPTIMIZED = ON , DURABILITY = SCHEMA_AND_DATA )  
GO  
  
DECLARE @i int = 0  
BEGIN TRAN  
WHILE @i < 262144  
BEGIN  
   INSERT Sales.SalesOrderHeader_test (OrderSequence, OrderDate, [Status]) VALUES (@i, sysdatetime(), @i % 8)  
   SET @i += 1  
END  
COMMIT  
GO  
```  
  
 <span data-ttu-id="975dd-153">此指令碼會在資料表中插入 262,144 個資料列。</span><span class="sxs-lookup"><span data-stu-id="975dd-153">The script inserts 262,144 rows in the table.</span></span> <span data-ttu-id="975dd-154">它會在主索引鍵索引和 IX_OrderSequence 中插入唯一值。</span><span class="sxs-lookup"><span data-stu-id="975dd-154">It inserts unique values in the primary key index and in IX_OrderSequence.</span></span> <span data-ttu-id="975dd-155">它會在索引 IX_Status 中插入大量重複的值：指令碼只會產生 8 個相異值。</span><span class="sxs-lookup"><span data-stu-id="975dd-155">It inserts a lot of duplicate values in the index IX_Status: the script only generates 8 distinct values.</span></span>  
  
 <span data-ttu-id="975dd-156">BUCKET_COUNT 疑難排解查詢的輸出如下：</span><span class="sxs-lookup"><span data-stu-id="975dd-156">The output of the BUCKET_COUNT troubleshooting query is as follows:</span></span>  
  
|<span data-ttu-id="975dd-157">索引名稱</span><span class="sxs-lookup"><span data-stu-id="975dd-157">index name</span></span>|<span data-ttu-id="975dd-158">total_bucket_count</span><span class="sxs-lookup"><span data-stu-id="975dd-158">total_bucket_count</span></span>|<span data-ttu-id="975dd-159">empty_bucket_count</span><span class="sxs-lookup"><span data-stu-id="975dd-159">empty_bucket_count</span></span>|<span data-ttu-id="975dd-160">empty_bucket_percent</span><span class="sxs-lookup"><span data-stu-id="975dd-160">empty_bucket_percent</span></span>|<span data-ttu-id="975dd-161">avg_chain_length</span><span class="sxs-lookup"><span data-stu-id="975dd-161">avg_chain_length</span></span>|<span data-ttu-id="975dd-162">max_chain_length</span><span class="sxs-lookup"><span data-stu-id="975dd-162">max_chain_length</span></span>|  
|----------------|--------------------------|--------------------------|----------------------------|------------------------|------------------------|  
|<span data-ttu-id="975dd-163">IX_Status</span><span class="sxs-lookup"><span data-stu-id="975dd-163">IX_Status</span></span>|<span data-ttu-id="975dd-164">8</span><span class="sxs-lookup"><span data-stu-id="975dd-164">8</span></span>|<span data-ttu-id="975dd-165">4</span><span class="sxs-lookup"><span data-stu-id="975dd-165">4</span></span>|<span data-ttu-id="975dd-166">50</span><span class="sxs-lookup"><span data-stu-id="975dd-166">50</span></span>|<span data-ttu-id="975dd-167">65536</span><span class="sxs-lookup"><span data-stu-id="975dd-167">65536</span></span>|<span data-ttu-id="975dd-168">65536</span><span class="sxs-lookup"><span data-stu-id="975dd-168">65536</span></span>|  
|<span data-ttu-id="975dd-169">IX_OrderSequence</span><span class="sxs-lookup"><span data-stu-id="975dd-169">IX_OrderSequence</span></span>|<span data-ttu-id="975dd-170">32768</span><span class="sxs-lookup"><span data-stu-id="975dd-170">32768</span></span>|<span data-ttu-id="975dd-171">13</span><span class="sxs-lookup"><span data-stu-id="975dd-171">13</span></span>|<span data-ttu-id="975dd-172">0</span><span class="sxs-lookup"><span data-stu-id="975dd-172">0</span></span>|<span data-ttu-id="975dd-173">8</span><span class="sxs-lookup"><span data-stu-id="975dd-173">8</span></span>|<span data-ttu-id="975dd-174">26</span><span class="sxs-lookup"><span data-stu-id="975dd-174">26</span></span>|  
|<span data-ttu-id="975dd-175">PK_SalesOrd_B14003C3F8FB3364</span><span class="sxs-lookup"><span data-stu-id="975dd-175">PK_SalesOrd_B14003C3F8FB3364</span></span>|<span data-ttu-id="975dd-176">262144</span><span class="sxs-lookup"><span data-stu-id="975dd-176">262144</span></span>|<span data-ttu-id="975dd-177">96319</span><span class="sxs-lookup"><span data-stu-id="975dd-177">96319</span></span>|<span data-ttu-id="975dd-178">36</span><span class="sxs-lookup"><span data-stu-id="975dd-178">36</span></span>|<span data-ttu-id="975dd-179">1</span><span class="sxs-lookup"><span data-stu-id="975dd-179">1</span></span>|<span data-ttu-id="975dd-180">8</span><span class="sxs-lookup"><span data-stu-id="975dd-180">8</span></span>|  
  
 <span data-ttu-id="975dd-181">請考慮此資料表上的三個雜湊索引：</span><span class="sxs-lookup"><span data-stu-id="975dd-181">Consider the three hash indexes on this table:</span></span>  
  
-   <span data-ttu-id="975dd-182">IX_Status：有 50% 的貯體是空的，這是理想的狀況。</span><span class="sxs-lookup"><span data-stu-id="975dd-182">IX_Status: 50 percent of the buckets are empty, which is good.</span></span> <span data-ttu-id="975dd-183">不過，平均鏈結長度非常高 (65,536)。</span><span class="sxs-lookup"><span data-stu-id="975dd-183">However, the average chain length is very high (65,536).</span></span> <span data-ttu-id="975dd-184">這表示有大量重複的值。</span><span class="sxs-lookup"><span data-stu-id="975dd-184">This indicates a large number of duplicate values.</span></span> <span data-ttu-id="975dd-185">因此，這種情況不適合使用非叢集雜湊索引。</span><span class="sxs-lookup"><span data-stu-id="975dd-185">Therefore, using a nonclustered hash index is not appropriate in this case.</span></span> <span data-ttu-id="975dd-186">應該改用非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="975dd-186">A nonclustered index should be used instead.</span></span>  
  
-   <span data-ttu-id="975dd-187">IX_OrderSequence：有 0% 的貯體是空的，這個數字過低。</span><span class="sxs-lookup"><span data-stu-id="975dd-187">IX_OrderSequence: 0 percent of the buckets are empty, which is too low.</span></span> <span data-ttu-id="975dd-188">此外，平均鏈結長度為 8。</span><span class="sxs-lookup"><span data-stu-id="975dd-188">In addition, the average chain length is 8.</span></span> <span data-ttu-id="975dd-189">由於這個索引中的值是唯一的，因此這表示平均有 8 個值對應到每個貯體。</span><span class="sxs-lookup"><span data-stu-id="975dd-189">As the values in this index are unique, this means on average 8 values are mapped to each bucket.</span></span> <span data-ttu-id="975dd-190">值區計數應該增加。</span><span class="sxs-lookup"><span data-stu-id="975dd-190">The bucket count should be increased.</span></span> <span data-ttu-id="975dd-191">由於索引鍵擁有 262,144 個唯一值，因此值區計數至少應該為 262,144。</span><span class="sxs-lookup"><span data-stu-id="975dd-191">As the index key has 262,144 unique values, the bucket count should be at least 262,144.</span></span> <span data-ttu-id="975dd-192">如果預期未來會有所成長，則這個數字應該更高。</span><span class="sxs-lookup"><span data-stu-id="975dd-192">If future growth is expected, the number should be higher.</span></span>  
  
-   <span data-ttu-id="975dd-193">主鍵索引 (PK__SalesOrder ... ) ：36% 的值區是空的，這是很好的。</span><span class="sxs-lookup"><span data-stu-id="975dd-193">Primary key index (PK__SalesOrder...): 36 percent of the buckets are empty, which is good.</span></span> <span data-ttu-id="975dd-194">另外，平均鏈結長度為 1，這也很理想。</span><span class="sxs-lookup"><span data-stu-id="975dd-194">In addition the average chain length is 1, which is also good.</span></span> <span data-ttu-id="975dd-195">不需要變更。</span><span class="sxs-lookup"><span data-stu-id="975dd-195">No change needed.</span></span>  
  
 <span data-ttu-id="975dd-196">如需對記憶體最佳化雜湊索引的問題進行疑難排解的詳細資訊，請參閱＜ [Troubleshooting Common Performance Problems with Memory-Optimized Hash Indexes](../../2014/database-engine/troubleshooting-common-performance-problems-with-memory-optimized-hash-indexes.md)＞。</span><span class="sxs-lookup"><span data-stu-id="975dd-196">For more information on troubleshooting issues with your memory-optimized hash indexes, see [Troubleshooting Common Performance Problems with Memory-Optimized Hash Indexes](../../2014/database-engine/troubleshooting-common-performance-problems-with-memory-optimized-hash-indexes.md).</span></span>  
  
## <a name="detailed-considerations-for-further-optimization"></a><span data-ttu-id="975dd-197">進一步最佳化的詳細考量</span><span class="sxs-lookup"><span data-stu-id="975dd-197">Detailed Considerations for Further Optimization</span></span>  
 <span data-ttu-id="975dd-198">本節將概述最佳化值區計數的進一步考量。</span><span class="sxs-lookup"><span data-stu-id="975dd-198">This section outlines further considerations for optimizing the bucket count.</span></span>  
  
 <span data-ttu-id="975dd-199">若要達成雜湊索引的最佳效能，請平衡配置給雜湊表的記憶體數量以及索引鍵中的相異值數目。</span><span class="sxs-lookup"><span data-stu-id="975dd-199">To achieve the best performance for hash indexes, balance the amount of memory allocated to the hash table and the number of distinct values in the index key.</span></span> <span data-ttu-id="975dd-200">點查閱的效能和資料表掃描之間也有平衡點：</span><span class="sxs-lookup"><span data-stu-id="975dd-200">There is also a balance between the performance of point lookups and table scans:</span></span>  
  
-   <span data-ttu-id="975dd-201">值區計數的值越高，索引中就會有越多空的貯體。</span><span class="sxs-lookup"><span data-stu-id="975dd-201">The higher the bucket count value, the more empty buckets there will be in the index.</span></span> <span data-ttu-id="975dd-202">這樣會影響記憶體使用量 (每個貯體 8 個位元組) 和資料表掃描的效能，因為資料表掃描的過程中會掃描每個貯體。</span><span class="sxs-lookup"><span data-stu-id="975dd-202">This has an impact on memory usage (8 bytes per bucket) and the performance of table scans, as each bucket is scanned as part of a table scan.</span></span>  
  
-   <span data-ttu-id="975dd-203">值區計數越小，指派給單一貯體的值越多。</span><span class="sxs-lookup"><span data-stu-id="975dd-203">The lower the bucket count, the more values are assigned to a single bucket.</span></span> <span data-ttu-id="975dd-204">這樣會降低點查閱和插入的效能，因為 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 可能需要周遊單一貯體中的數個值，以尋找搜尋述詞所指定的值。</span><span class="sxs-lookup"><span data-stu-id="975dd-204">This decreases performance for point lookups and inserts, because [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] may need to traverse several values in a single bucket to find the value specified by the search predicate.</span></span>  
  
 <span data-ttu-id="975dd-205">如果值區計數明顯低於唯一索引鍵數目，則將會有許多值對應至每個貯體。</span><span class="sxs-lookup"><span data-stu-id="975dd-205">If the bucket count is significantly lower than the number of unique index keys, many values will map to each bucket.</span></span> <span data-ttu-id="975dd-206">這樣會降低大部分 DML 作業的效能，特別是點查閱 (個別索引鍵的查閱) 和插入作業。</span><span class="sxs-lookup"><span data-stu-id="975dd-206">This degrades performance of most DML operations, particularly point lookups (lookups of individual index keys) and insert operations.</span></span> <span data-ttu-id="975dd-207">例如，在 WHERE 子句中比對索引鍵資料行的等號比較述詞，您可能會發現 SELECT 查詢以及 UPDATE 與 DELETE 作業的效能不佳。</span><span class="sxs-lookup"><span data-stu-id="975dd-207">For example, you may see poor performance of SELECT queries and, UPDATE and DELETE operations with equality predicates matching the index key columns in the WHERE clause.</span></span> <span data-ttu-id="975dd-208">值區計數過低也會影響資料庫的復原時間，因為索引會在資料庫啟動時重新建立。</span><span class="sxs-lookup"><span data-stu-id="975dd-208">A low bucket count will also affect the recovery time of the database, as the indexes are recreated on database startup.</span></span>  
  
### <a name="duplicate-index-key-values"></a><span data-ttu-id="975dd-209">重複的索引鍵值</span><span class="sxs-lookup"><span data-stu-id="975dd-209">Duplicate Index Key Values</span></span>  
 <span data-ttu-id="975dd-210">重複值可能會加重雜湊衝突的效能影響。</span><span class="sxs-lookup"><span data-stu-id="975dd-210">Duplicate values can increase the performance impact of hash collisions.</span></span> <span data-ttu-id="975dd-211">如果每個索引鍵的重複數目不高，通常不會造成問題。</span><span class="sxs-lookup"><span data-stu-id="975dd-211">This is usually not a problem if each index key has a low number of duplicates.</span></span> <span data-ttu-id="975dd-212">不過，如果資料表中唯一索引鍵的數目和資料列數目之間的差異擴大，就有可能會產生問題。</span><span class="sxs-lookup"><span data-stu-id="975dd-212">But this can be a problem if the discrepancy between the number of unique index keys and the number of rows in the tables becomes very large.</span></span>  
  
 <span data-ttu-id="975dd-213">具有相同索引鍵的所有資料列將會進入相同的重複鏈結。</span><span class="sxs-lookup"><span data-stu-id="975dd-213">All rows with the same index key will go into the same duplicate chain.</span></span> <span data-ttu-id="975dd-214">如果同一個貯體中因為雜湊衝突而有多個索引鍵，索引掃描器就一定要先掃描整個重複鏈結找出第一個值，才能找到對應第二個值的第一個資料列。</span><span class="sxs-lookup"><span data-stu-id="975dd-214">If multiple index keys are in the same bucket due to a hash collision, index scanners always need to scan the full duplicate chain for the first value before they can locate the first row corresponding to the second value.</span></span> <span data-ttu-id="975dd-215">重複索引鍵也會使記憶體回收更難找出資料列。</span><span class="sxs-lookup"><span data-stu-id="975dd-215">Duplicate keys also make it more difficult for garbage collection to locate the row.</span></span> <span data-ttu-id="975dd-216">比方說，如果索引鍵具 1000 個重複項目，當其中一個資料列遭刪除時，記憶體回收行程就必須掃描 1000 個重複項目的鏈結，才能取消資料列與索引間的連結。</span><span class="sxs-lookup"><span data-stu-id="975dd-216">For example, if there are 1,000 duplicates for any key and one of the rows is deleted, the garbage collector needs to scan the chain of 1,000 duplicates to unlink the row from the index.</span></span> <span data-ttu-id="975dd-217">即使找出刪除的查詢使用較有效率的索引 (主索引鍵索引) 尋找資料列，但因為記憶體回收行程需要取消每個索引的連結，也會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="975dd-217">This is true even if the query that found the delete used a more efficient index (a primary key index) to locate the row, because the garbage collector needs to unlink from every index</span></span>  
  
 <span data-ttu-id="975dd-218">若是雜湊索引，有兩種方式可減少重複的索引鍵值產生的工作：</span><span class="sxs-lookup"><span data-stu-id="975dd-218">For hash indexes, there are two ways to reduce the work caused by duplicate index key values:</span></span>  
  
-   <span data-ttu-id="975dd-219">改用非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="975dd-219">Use a nonclustered index instead.</span></span> <span data-ttu-id="975dd-220">您可以藉由加入資料行至索引鍵來減少重複，不需要變更任何應用程式。</span><span class="sxs-lookup"><span data-stu-id="975dd-220">You can decrease the duplicates by adding columns to the index key without requiring any changes to the application.</span></span>  
  
-   <span data-ttu-id="975dd-221">指定非常高的索引值區計數。</span><span class="sxs-lookup"><span data-stu-id="975dd-221">Specify a very high bucket count for the index.</span></span> <span data-ttu-id="975dd-222">例如，唯一索引鍵數目的 20 到 100 倍。</span><span class="sxs-lookup"><span data-stu-id="975dd-222">For example, 20-to-100 times the number of unique index keys.</span></span> <span data-ttu-id="975dd-223">這樣一來就會減少雜湊衝突。</span><span class="sxs-lookup"><span data-stu-id="975dd-223">This will reduce hash collisions.</span></span>  
  
### <a name="small-tables"></a><span data-ttu-id="975dd-224">小型資料表</span><span class="sxs-lookup"><span data-stu-id="975dd-224">Small Tables</span></span>  
 <span data-ttu-id="975dd-225">對於較小的資料表而言，記憶體使用量通常不是問題，因為與資料庫整體大小相較之下，索引的大小會很小。</span><span class="sxs-lookup"><span data-stu-id="975dd-225">For smaller tables, memory utilization is usually not a concern, as the size of the index will be small compared to the overall size of the database.</span></span>  
  
 <span data-ttu-id="975dd-226">現在您必須根據想要的效能類型做出選擇：</span><span class="sxs-lookup"><span data-stu-id="975dd-226">You must now make a choice based on the kind of performance you want:</span></span>  
  
-   <span data-ttu-id="975dd-227">如果索引上相當倚賴效能的作業主要是點查閱和 (或) 插入作業，則適合使用較高的值區計數，如此可降低雜湊衝突的可能性。</span><span class="sxs-lookup"><span data-stu-id="975dd-227">If the performance-critical operations on the index are predominantly point lookups and/or insert operations, a higher bucket count would be appropriate to reduce the likelihood of hash collisions.</span></span> <span data-ttu-id="975dd-228">最理想的選擇會是資料列數目的三倍以上。</span><span class="sxs-lookup"><span data-stu-id="975dd-228">Three times the number of rows or even more would be the best option.</span></span>  
  
-   <span data-ttu-id="975dd-229">如果完整索引掃描是主要倚賴效能的作業，請使用接近索引鍵值實際數目的值區計數。</span><span class="sxs-lookup"><span data-stu-id="975dd-229">If full index scans are the predominant performance-critical operations, use a bucket count that is close to the actual number of index key values.</span></span>  
  
### <a name="big-tables"></a><span data-ttu-id="975dd-230">大型資料表</span><span class="sxs-lookup"><span data-stu-id="975dd-230">Big Tables</span></span>  
 <span data-ttu-id="975dd-231">對於大型資料表而言，記憶體使用量可能成為問題。</span><span class="sxs-lookup"><span data-stu-id="975dd-231">For large tables, memory utilization could become a concern.</span></span> <span data-ttu-id="975dd-232">例如，具有4個雜湊索引的250000000資料列資料表，每個都有一個值區計數為1000000000，而雜湊表的額外負荷為4個索引 \* 1000000000 值區 \* 8 個位元組 = 32 gb 的記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="975dd-232">For example, with a 250 million row table that has 4 hash indexes, each with a bucket count of one billion, the overhead for the hash tables is 4 indexes \* 1 billion buckets \* 8 bytes = 32 gigabytes of memory utilization.</span></span> <span data-ttu-id="975dd-233">如果針對每個索引選擇的值區計數為 2500 萬，則雜湊表的總負擔將會是 8 GB。</span><span class="sxs-lookup"><span data-stu-id="975dd-233">When choosing a bucket count of 250 million for each of the indexes, the total overhead for the hash tables will be 8 gigabytes.</span></span> <span data-ttu-id="975dd-234">請注意，這是除了8個位元組的記憶體使用量以外，每個索引都會新增至每個個別的資料列，在此案例中為 8 gb (4 索引 \* 8 個位元組250000000個數據 \* 列) 。</span><span class="sxs-lookup"><span data-stu-id="975dd-234">Note that this is in addition to the 8 bytes of memory usage each index adds to each individual row, which is 8 gigabytes in this scenario (4 indexes \* 8 bytes \* 250 million rows).</span></span>  
  
 <span data-ttu-id="975dd-235">完整資料表掃描通常不在 OLTP 工作負載的關鍵效能路徑中。</span><span class="sxs-lookup"><span data-stu-id="975dd-235">Full table scans are not usually in the performance-critical path for OLTP workloads.</span></span> <span data-ttu-id="975dd-236">因此，選擇會介於記憶體使用量與點查閱和插入作業的效能之間：</span><span class="sxs-lookup"><span data-stu-id="975dd-236">Therefore, the choice is between memory utilization versus performance of point lookup and insert operations:</span></span>  
  
-   <span data-ttu-id="975dd-237">如果記憶體使用量會是問題，請選擇接近索引鍵值數目的值區計數。</span><span class="sxs-lookup"><span data-stu-id="975dd-237">If memory utilization is a concern, choose a bucket count close to the number of index key values.</span></span> <span data-ttu-id="975dd-238">值區計數不應該大幅低於索引鍵值數目，因為這樣會影響大部分 DML 作業，以及影響在伺服器重新啟動後復原資料庫所需的時間。</span><span class="sxs-lookup"><span data-stu-id="975dd-238">The bucket count should not be significantly lower than the number of index key values, as this impacts most DML operations as well the time it takes to recover the database after server restart.</span></span>  
  
-   <span data-ttu-id="975dd-239">對點查閱的效能進行最佳化時，適合使用較高的值區計數，最好是唯一索引值數目的兩倍甚至三倍。</span><span class="sxs-lookup"><span data-stu-id="975dd-239">When optimizing the performance for point lookups, a higher bucket count of two or even three times the number of unique index values would be appropriate.</span></span> <span data-ttu-id="975dd-240">值區計數越高，表示記憶體使用量越高，而且完整索引掃描所需的時間也會越長。</span><span class="sxs-lookup"><span data-stu-id="975dd-240">A higher bucket count would mean an increased memory utilization and an increase in the time required for a full index scan.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="975dd-241">另請參閱</span><span class="sxs-lookup"><span data-stu-id="975dd-241">See Also</span></span>  
 [<span data-ttu-id="975dd-242">記憶體最佳化資料表上的索引</span><span class="sxs-lookup"><span data-stu-id="975dd-242">Indexes on Memory-Optimized Tables</span></span>](../../2014/database-engine/indexes-on-memory-optimized-tables.md)  
  
  
