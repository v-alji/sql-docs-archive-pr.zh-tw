---
title: 使用叢集資料行存放區索引 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 5af6b91c-724f-45ac-aff1-7555014914f4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: afc7da4e28ef7f32ca4a2b4ea762e5a5af442471
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585536"
---
# <a name="using-clustered-columnstore-indexes"></a><span data-ttu-id="d15aa-102">使用叢集資料行存放區索引</span><span class="sxs-lookup"><span data-stu-id="d15aa-102">Using Clustered Columnstore Indexes</span></span>
  <span data-ttu-id="d15aa-103">在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中使用叢集資料行存放區索引的工作。</span><span class="sxs-lookup"><span data-stu-id="d15aa-103">Tasks for using clustered columnstore indexes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>

 <span data-ttu-id="d15aa-104">如需資料行存放區索引的概觀，請參閱＜ [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d15aa-104">For an overview of columnstore indexes, see [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md).</span></span>

 <span data-ttu-id="d15aa-105">如需有關叢集資料行存放區索引的詳細資訊，請參閱＜ [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d15aa-105">For information about clustered columnstore indexes, see [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md).</span></span>

## <a name="contents"></a><span data-ttu-id="d15aa-106">目錄</span><span class="sxs-lookup"><span data-stu-id="d15aa-106">Contents</span></span>

-   [<span data-ttu-id="d15aa-107">建立叢集資料行存放區索引</span><span class="sxs-lookup"><span data-stu-id="d15aa-107">Create a Clustered Columnstore Index</span></span>](#create)

-   [<span data-ttu-id="d15aa-108">卸除叢集資料行存放區索引</span><span class="sxs-lookup"><span data-stu-id="d15aa-108">Drop a Clustered Columnstore Index</span></span>](#drop)

-   [<span data-ttu-id="d15aa-109">將資料載入叢集資料行存放區索引</span><span class="sxs-lookup"><span data-stu-id="d15aa-109">Load Data into a Clustered Columnstore Index</span></span>](#load)

-   [<span data-ttu-id="d15aa-110">變更叢集資料行存放區索引中的資料</span><span class="sxs-lookup"><span data-stu-id="d15aa-110">Change Data in a Clustered Columnstore Index</span></span>](#change)

-   [<span data-ttu-id="d15aa-111">重建叢集資料行存放區索引</span><span class="sxs-lookup"><span data-stu-id="d15aa-111">Rebuild a Clustered Columnstore Index</span></span>](#rebuild)

-   [<span data-ttu-id="d15aa-112">重新組織叢集資料行存放區索引</span><span class="sxs-lookup"><span data-stu-id="d15aa-112">Reorganize a Clustered Columnstore Index</span></span>](#reorganize)

##  <a name="create-a-clustered-columnstore-index"></a><a name="create"></a><span data-ttu-id="d15aa-113">建立叢集資料行存放區索引</span><span class="sxs-lookup"><span data-stu-id="d15aa-113">Create a Clustered Columnstore Index</span></span>
 <span data-ttu-id="d15aa-114">若要建立叢集資料行存放區索引，請先建立 rowstore 資料表做為堆積或叢集索引，然後使用 Create 叢集資料行存放區[索引 &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)語句，將資料表轉換成叢集資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="d15aa-114">To create a clustered columnstore index, first create a rowstore table as a heap or clustered index, and then use the [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql) statement to convert the table to a clustered columnstore index.</span></span> <span data-ttu-id="d15aa-115">如果您要讓叢集資料行存放區索引使用與叢集索引相同的名稱，請使用 DROP_EXISTING 選項。</span><span class="sxs-lookup"><span data-stu-id="d15aa-115">If you want the clustered columnstore index to have the same name as the clustered index, use the DROP_EXISTING option.</span></span>

 <span data-ttu-id="d15aa-116">此範例會建立資料表做為堆積，然後將它轉換成名為 cci_Simple 的叢集資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="d15aa-116">This example creates a table as a heap and then converts it to a clustered columnstore index named cci_Simple.</span></span> <span data-ttu-id="d15aa-117">這會將整個資料表的儲存體從資料列存放區變更為資料行存放區。</span><span class="sxs-lookup"><span data-stu-id="d15aa-117">This changes the storage for the entire table from rowstore to columnstore.</span></span>

```
CREATE TABLE T1(
    ProductKey [int] NOT NULL, 
    OrderDateKey [int] NOT NULL, 
    DueDateKey [int] NOT NULL, 
    ShipDateKey [int] NOT NULL);
GO
CREATE CLUSTERED COLUMNSTORE INDEX cci_T1 ON T1;
GO
```

 <span data-ttu-id="d15aa-118">如需更多範例，請參閱 CREATE 叢集資料行存放區[索引 &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)中的範例一節。</span><span class="sxs-lookup"><span data-stu-id="d15aa-118">For more examples, see the Examples section in [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql).</span></span>

##  <a name="drop-a-clustered-columnstore-index"></a><a name="drop"></a><span data-ttu-id="d15aa-119">卸載叢集資料行存放區索引</span><span class="sxs-lookup"><span data-stu-id="d15aa-119">Drop a Clustered Columnstore Index</span></span>
 <span data-ttu-id="d15aa-120">使用[DROP INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/drop-index-transact-sql)語句來卸載叢集資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="d15aa-120">Use the [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql) statement to drop a clustered columnstore index.</span></span> <span data-ttu-id="d15aa-121">此作業將卸除索引並將資料行存放區資料表轉換成資料列存放區堆積。</span><span class="sxs-lookup"><span data-stu-id="d15aa-121">This operation will drop the index and convert the columnstore table to a rowstore heap.</span></span>

##  <a name="load-data-into-a-clustered-columnstore-index"></a><a name="load"></a><span data-ttu-id="d15aa-122">將資料載入叢集資料行存放區索引</span><span class="sxs-lookup"><span data-stu-id="d15aa-122">Load Data into a Clustered Columnstore Index</span></span>
 <span data-ttu-id="d15aa-123">您可以利用任何一種標準的載入方法，將資料加入至現有的叢集資料行存放區索引中。</span><span class="sxs-lookup"><span data-stu-id="d15aa-123">You can add data to an existing clustered columnstore index by using any of the standard loading methods.</span></span>  <span data-ttu-id="d15aa-124">例如，bcp 大量載入工具、Integration Services 和 INSERT .。。選取 [所有] 可將資料載入叢集資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="d15aa-124">For example, the bcp bulk loading tool, Integration Services, and INSERT ... SELECT can all load data into a clustered columnstore index.</span></span>

 <span data-ttu-id="d15aa-125">叢集資料行存放區索引會運用差異存放區防止資料行存放區中出現資料行區段的片段。</span><span class="sxs-lookup"><span data-stu-id="d15aa-125">Clustered columnstore indexes leverage the deltastore in order to prevent fragmentation of column segments in the columnstore.</span></span>

### <a name="loading-into-a-partitioned-table"></a><span data-ttu-id="d15aa-126">載入至資料分割資料表</span><span class="sxs-lookup"><span data-stu-id="d15aa-126">Loading into a partitioned table</span></span>
 <span data-ttu-id="d15aa-127">對於分割資料， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會先將每個資料列指派至一個分割區，然後在分割區內對資料執行資料行存放區作業。</span><span class="sxs-lookup"><span data-stu-id="d15aa-127">For partitioned data, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] first assigns each row to a partition, and then performs columnstore operations on the data within the partition.</span></span> <span data-ttu-id="d15aa-128">每個分割區都有自己的資料列群組以及至少一個差異存放區。</span><span class="sxs-lookup"><span data-stu-id="d15aa-128">Each partition has its own rowgroups and at least one deltastore.</span></span>

### <a name="deltastore-loading-scenarios"></a><span data-ttu-id="d15aa-129">差異存放區載入案例</span><span class="sxs-lookup"><span data-stu-id="d15aa-129">Deltastore loading scenarios</span></span>
 <span data-ttu-id="d15aa-130">資料列會在差異存放區中累積，直到資料列數達到一個資料列群組允許的資料列數上限。</span><span class="sxs-lookup"><span data-stu-id="d15aa-130">Rows accumulate in the deltastore until the number of rows is the maximum number of rows allowed for a rowgroup.</span></span> <span data-ttu-id="d15aa-131">當差異存放區包含每個資料列群組的最大資料列數目時，會將資料列群組 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 標示為「已關閉」。</span><span class="sxs-lookup"><span data-stu-id="d15aa-131">When the deltastore contains the maximum number of rows per rowgroup, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] marks the rowgroup as "CLOSED".</span></span> <span data-ttu-id="d15aa-132">背景進程（稱為「元組」）會尋找關閉的資料列群組，並移入資料行存放區，其中資料列群組會壓縮成資料行區段，而資料行區段則儲存在資料行存放區中。</span><span class="sxs-lookup"><span data-stu-id="d15aa-132">A background process, called the "tuple-mover", finds the CLOSED rowgroup and moves into the columnstore, where the rowgroup is compressed into column segments and the column segments are stored in the columnstore.</span></span>

 <span data-ttu-id="d15aa-133">每一個叢集資料行存放區索引可以有多個差異存放區。</span><span class="sxs-lookup"><span data-stu-id="d15aa-133">For each clustered columnstore index there can be multiple deltastores.</span></span>

-   <span data-ttu-id="d15aa-134">如果差異存放區已鎖定， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 將嘗試鎖定另一個差異存放區。</span><span class="sxs-lookup"><span data-stu-id="d15aa-134">If a deltastore is locked, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will try to obtain a lock on a different deltastore.</span></span> <span data-ttu-id="d15aa-135">如果沒有可用的差異存放區， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 將建立新的差異存放區。</span><span class="sxs-lookup"><span data-stu-id="d15aa-135">If there are no deltastores available, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will create a new deltastore.</span></span>

-   <span data-ttu-id="d15aa-136">若是資料分割資料表，每個分割區可以有一個或多個差異存放區。</span><span class="sxs-lookup"><span data-stu-id="d15aa-136">For a partitioned table, there can be one or more deltastores for each partition.</span></span>

 <span data-ttu-id="d15aa-137">下列案例僅適用於叢集資料行存放區索引，將描述載入的資料列何時會直接進入資料行存放區，或何時會進入差異存放區。</span><span class="sxs-lookup"><span data-stu-id="d15aa-137">For clustered columnstore indexes only, the following scenarios describe when loaded rows go directly to the columnstore or when they go to the deltastore.</span></span>

 <span data-ttu-id="d15aa-138">在範例中，每個資料列群組可以有 102,400-1,048,576 個資料列。</span><span class="sxs-lookup"><span data-stu-id="d15aa-138">In the example, each rowgroup can have 102,400-1,048,576 rows per rowgroup.</span></span>

|<span data-ttu-id="d15aa-139">大量載入的資料列</span><span class="sxs-lookup"><span data-stu-id="d15aa-139">Rows to Bulk Load</span></span>|<span data-ttu-id="d15aa-140">加入至資料行存放區的資料列</span><span class="sxs-lookup"><span data-stu-id="d15aa-140">Rows Added to the Columnstore</span></span>|<span data-ttu-id="d15aa-141">加入至差異存放區的資料列</span><span class="sxs-lookup"><span data-stu-id="d15aa-141">Rows Added to the Deltastore</span></span>|
|-----------------------|-----------------------------------|----------------------------------|
|<span data-ttu-id="d15aa-142">102,000</span><span class="sxs-lookup"><span data-stu-id="d15aa-142">102,000</span></span>|<span data-ttu-id="d15aa-143">0</span><span class="sxs-lookup"><span data-stu-id="d15aa-143">0</span></span>|<span data-ttu-id="d15aa-144">102,000</span><span class="sxs-lookup"><span data-stu-id="d15aa-144">102,000</span></span>|
|<span data-ttu-id="d15aa-145">145,000</span><span class="sxs-lookup"><span data-stu-id="d15aa-145">145,000</span></span>|<span data-ttu-id="d15aa-146">145,000</span><span class="sxs-lookup"><span data-stu-id="d15aa-146">145,000</span></span><br /><br /> <span data-ttu-id="d15aa-147">資料列群組大小：145,000</span><span class="sxs-lookup"><span data-stu-id="d15aa-147">Rowgroup size: 145,000</span></span>|<span data-ttu-id="d15aa-148">0</span><span class="sxs-lookup"><span data-stu-id="d15aa-148">0</span></span>|
|<span data-ttu-id="d15aa-149">1,048,577</span><span class="sxs-lookup"><span data-stu-id="d15aa-149">1,048,577</span></span>|<span data-ttu-id="d15aa-150">1,048,576</span><span class="sxs-lookup"><span data-stu-id="d15aa-150">1,048,576</span></span><br /><br /> <span data-ttu-id="d15aa-151">資料列群組大小：1,048,576。</span><span class="sxs-lookup"><span data-stu-id="d15aa-151">Rowgroup size: 1,048,576.</span></span>|<span data-ttu-id="d15aa-152">1</span><span class="sxs-lookup"><span data-stu-id="d15aa-152">1</span></span>|
|<span data-ttu-id="d15aa-153">2,252,152</span><span class="sxs-lookup"><span data-stu-id="d15aa-153">2,252,152</span></span>|<span data-ttu-id="d15aa-154">2,252,152</span><span class="sxs-lookup"><span data-stu-id="d15aa-154">2,252,152</span></span><br /><br /> <span data-ttu-id="d15aa-155">資料列群組大小：1,048,576、1,048,576、155,000。</span><span class="sxs-lookup"><span data-stu-id="d15aa-155">Rowgroup sizes: 1,048,576, 1,048,576, 155,000.</span></span>|<span data-ttu-id="d15aa-156">0</span><span class="sxs-lookup"><span data-stu-id="d15aa-156">0</span></span>|

 <span data-ttu-id="d15aa-157">下列範例顯示將 1,048,577 個資料列載入分割區的結果。</span><span class="sxs-lookup"><span data-stu-id="d15aa-157">The following example shows the results of loading 1,048,577 rows into a partition.</span></span> <span data-ttu-id="d15aa-158">結果顯示，資料行存放區中有一個 COMPRESSED 資料列群組 (壓縮的資料行區段)，而差異存放區中有 1 個資料列。</span><span class="sxs-lookup"><span data-stu-id="d15aa-158">The results show that one COMPRESSED rowgroup in the columnstore (as compressed column segments), and 1 row in the deltastore.</span></span>

```sql
SELECT * FROM sys.column_store_row_groups;
```

 <span data-ttu-id="d15aa-159">![批次載入的資料列群組與差異存放區](../../2014/database-engine/media/sql-server-pdw-columnstore-batchload.gif "批次載入的資料列群組與差異存放區")</span><span class="sxs-lookup"><span data-stu-id="d15aa-159">![Rowgroup and deltastore for a batch load](../../2014/database-engine/media/sql-server-pdw-columnstore-batchload.gif "Rowgroup and deltastore for a batch load")</span></span>



##  <a name="change-data-in-a-clustered-columnstore-index"></a><a name="change"></a><span data-ttu-id="d15aa-160">變更叢集資料行存放區索引中的資料</span><span class="sxs-lookup"><span data-stu-id="d15aa-160">Change Data in a Clustered Columnstore Index</span></span>
 <span data-ttu-id="d15aa-161">叢集資料行存放區索引支援插入、更新及刪除 DML 作業。</span><span class="sxs-lookup"><span data-stu-id="d15aa-161">Clustered columnstore indexes support insert, update, and delete DML operations.</span></span>

 <span data-ttu-id="d15aa-162">使用[insert &#40;transact-sql&#41;](/sql/t-sql/statements/insert-transact-sql)插入資料列。</span><span class="sxs-lookup"><span data-stu-id="d15aa-162">Use [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) to insert a row.</span></span> <span data-ttu-id="d15aa-163">資料列會加入至差異存放區。</span><span class="sxs-lookup"><span data-stu-id="d15aa-163">The row will be added to the deltastore.</span></span>

 <span data-ttu-id="d15aa-164">使用 [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) 刪除資料列。</span><span class="sxs-lookup"><span data-stu-id="d15aa-164">Use [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) to delete a row.</span></span>

-   <span data-ttu-id="d15aa-165">如果資料列位於資料行存放區中，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會將該資料列標示為邏輯刪除，但不會回收該資料列的實體儲存體，直到重建索引為止。</span><span class="sxs-lookup"><span data-stu-id="d15aa-165">If the row is in the columnstore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] marks the row as logically deleted but does not reclaim the physical storage for the row until the index is rebuilt.</span></span>

-   <span data-ttu-id="d15aa-166">如果資料列位於差異存放區中，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會以邏輯方式實際刪除該資料列。</span><span class="sxs-lookup"><span data-stu-id="d15aa-166">If the row is in the deltastore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] logically and physically deletes the row.</span></span>

 <span data-ttu-id="d15aa-167">使用 [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) 更新資料列。</span><span class="sxs-lookup"><span data-stu-id="d15aa-167">Use [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) to update a row.</span></span>

-   <span data-ttu-id="d15aa-168">如果資料列位於資料行存放區中，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會將該資料列標示為邏輯刪除，然後將更新的資料列插入差異存放區中。</span><span class="sxs-lookup"><span data-stu-id="d15aa-168">If the row is in the columnstore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] marks the row as logically deleted, and then inserts the updated row into the deltastore.</span></span>

-   <span data-ttu-id="d15aa-169">如果資料列位於差異存放區中，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會更新差異存放區中的該資料列。</span><span class="sxs-lookup"><span data-stu-id="d15aa-169">If the row is in the deltastore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] updates the row in the deltastore.</span></span>

##  <a name="rebuild-a-clustered-columnstore-index"></a><a name="rebuild"></a><span data-ttu-id="d15aa-170">重建叢集資料行存放區索引</span><span class="sxs-lookup"><span data-stu-id="d15aa-170">Rebuild a Clustered Columnstore Index</span></span>
 <span data-ttu-id="d15aa-171">使用 CREATE 叢集資料行存放區[索引 &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)或[ALTER INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/alter-index-transact-sql)來執行現有叢集資料行存放區索引的完整重建。</span><span class="sxs-lookup"><span data-stu-id="d15aa-171">Use [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql) or [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) to perform a full rebuild of an existing clustered columnstore index.</span></span> <span data-ttu-id="d15aa-172">此外，您可以使用 ALTER INDEX .。。REBUILD 以重建特定的分割區。</span><span class="sxs-lookup"><span data-stu-id="d15aa-172">Additionally, you can use ALTER INDEX ... REBUILD to rebuild a specific partition.</span></span>

### <a name="rebuild-process"></a><span data-ttu-id="d15aa-173">重建程序</span><span class="sxs-lookup"><span data-stu-id="d15aa-173">Rebuild Process</span></span>
 <span data-ttu-id="d15aa-174">為了重建叢集資料行存放區索引，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會進行以下作業：</span><span class="sxs-lookup"><span data-stu-id="d15aa-174">To rebuild a clustered columnstore index, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>

-   <span data-ttu-id="d15aa-175">在進行重建時，取得資料表或分割區上的獨佔鎖定。</span><span class="sxs-lookup"><span data-stu-id="d15aa-175">Acquires an exclusive lock on the table or partition while the rebuild occurs.</span></span>  <span data-ttu-id="d15aa-176">在重建期間，資料處於「離線」狀態而且無法使用。</span><span class="sxs-lookup"><span data-stu-id="d15aa-176">The data is "offline" and unavailable during the rebuild.</span></span>

-   <span data-ttu-id="d15aa-177">藉由實際刪除已經以邏輯方式從資料表刪除的資料列，以重組資料行存放區，而已刪除的位元組會在實體媒體上回收。</span><span class="sxs-lookup"><span data-stu-id="d15aa-177">Defragments the columnstore by physically deleting rows that have been logically deleted from the table; the deleted bytes are reclaimed on the physical media.</span></span>

-   <span data-ttu-id="d15aa-178">在重建索引之前，合併差異存放區中的資料列存放區資料與資料行存放區中的資料。</span><span class="sxs-lookup"><span data-stu-id="d15aa-178">Merges the rowstore data in the deltastore with the data in the columnstore before it rebuilds the index.</span></span> <span data-ttu-id="d15aa-179">重建完成時，所有資料都會以資料行存放區格式儲存，且差異存放區會是空的。</span><span class="sxs-lookup"><span data-stu-id="d15aa-179">When the rebuild is finished, all data is stored in columnstore format, and the deltastore is empty.</span></span>

-   <span data-ttu-id="d15aa-180">將所有資料重新壓縮到資料行存放區。</span><span class="sxs-lookup"><span data-stu-id="d15aa-180">Re-compresses all data into the columnstore.</span></span> <span data-ttu-id="d15aa-181">當重建進行時，有兩個資料行存放區索引複本存在。</span><span class="sxs-lookup"><span data-stu-id="d15aa-181">Two copies of the columnstore index exist while the rebuild is taking place.</span></span> <span data-ttu-id="d15aa-182">當重建完成時， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會刪除原始資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="d15aa-182">When the rebuild is finished, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] deletes the original columnstore index.</span></span>

### <a name="recommendations-for-rebuilding-a-clustered-columnstore-index"></a><span data-ttu-id="d15aa-183">重建叢集資料行存放區索引的建議</span><span class="sxs-lookup"><span data-stu-id="d15aa-183">Recommendations for Rebuilding a Clustered Columnstore Index</span></span>
 <span data-ttu-id="d15aa-184">重建叢集資料行存放區索引對於移除片段以及將所有資料列移入資料行存放區而言相當實用。</span><span class="sxs-lookup"><span data-stu-id="d15aa-184">Rebuilding a clustered columnstore index is useful for removing fragmentation, and for moving all rows into the columnstore.</span></span> <span data-ttu-id="d15aa-185">以下是我們的建議：</span><span class="sxs-lookup"><span data-stu-id="d15aa-185">We have the following recommendations:</span></span>

-   <span data-ttu-id="d15aa-186">重建分割區，而非整份資料表。</span><span class="sxs-lookup"><span data-stu-id="d15aa-186">Rebuild a partition instead of the entire table.</span></span>

    1.  <span data-ttu-id="d15aa-187">如果索引很大，重建整個資料表將花上很長的時間，而且需要足夠的磁碟空間來存放重建期間額外的索引副本。</span><span class="sxs-lookup"><span data-stu-id="d15aa-187">Rebuilding the entire table takes a long time if the index is large, and it requires enough disk space to store an additional copy of the index during the rebuild.</span></span> <span data-ttu-id="d15aa-188">通常只需要重建最近使用的分割區。</span><span class="sxs-lookup"><span data-stu-id="d15aa-188">Usually it is only necessary to rebuild the most recently used partition.</span></span>

    2.  <span data-ttu-id="d15aa-189">對於資料分割資料表，您不需要重建整個資料行存放區索引，因為片段可能只會出現在最近修改過的分割區中。</span><span class="sxs-lookup"><span data-stu-id="d15aa-189">For partitioned tables, you do not need to rebuild the entire columnstore index because fragmentation is likely to occur in only the partitions that have been modified recently.</span></span> <span data-ttu-id="d15aa-190">事實資料表和大型維度資料表通常會進行分割區，以便在資料表區塊上執行備份和管理作業。</span><span class="sxs-lookup"><span data-stu-id="d15aa-190">Fact tables and large dimension tables are usually partitioned in order to perform backup and management operations on chunks of the table.</span></span>

-   <span data-ttu-id="d15aa-191">在繁重的 DML 作業之後重建分割區。</span><span class="sxs-lookup"><span data-stu-id="d15aa-191">Rebuild a partition after heavy DML operations.</span></span>

     <span data-ttu-id="d15aa-192">重建分割區將會重組分割區並減少磁碟儲存體。</span><span class="sxs-lookup"><span data-stu-id="d15aa-192">Rebuilding a partition will defragment the partition and reduce disk storage.</span></span> <span data-ttu-id="d15aa-193">重建將會刪除資料行存放區中所有標示為刪除的資料列，並且將所有資料列從差異存放區移至資料行存放區。</span><span class="sxs-lookup"><span data-stu-id="d15aa-193">Rebuilding will delete all rows from the columnstore that are marked for deletion, and it will move all rows from the deltastore into the columnstore.</span></span>

-   <span data-ttu-id="d15aa-194">載入資料後重建分割區。</span><span class="sxs-lookup"><span data-stu-id="d15aa-194">Rebuild a partition after loading data.</span></span>

     <span data-ttu-id="d15aa-195">如此可確保所有資料都儲存在資料行存放區中。</span><span class="sxs-lookup"><span data-stu-id="d15aa-195">This ensures all data is stored in the columnstore.</span></span> <span data-ttu-id="d15aa-196">如果同時進行多項載入，每個分割區最後可能會有多個差異存放區。</span><span class="sxs-lookup"><span data-stu-id="d15aa-196">If multiple loads occur at the same time, each partition could end up having multiple deltastores.</span></span> <span data-ttu-id="d15aa-197">重建會將所有差異存放區資料列移至資料行存放區。</span><span class="sxs-lookup"><span data-stu-id="d15aa-197">Rebuilding will move all deltastore rows into the columnstore.</span></span>

##  <a name="reorganize-a-clustered-columnstore-index"></a><a name="reorganize"></a><span data-ttu-id="d15aa-198">重新組織叢集資料行存放區索引</span><span class="sxs-lookup"><span data-stu-id="d15aa-198">Reorganize a Clustered Columnstore Index</span></span>
 <span data-ttu-id="d15aa-199">重新組織叢集資料行存放區索引會將所有 CLOSED 資料列群組移到資料行存放區中。</span><span class="sxs-lookup"><span data-stu-id="d15aa-199">Reorganizing a clustered columnstore index moves all CLOSED rowgroups into the columnstore.</span></span> <span data-ttu-id="d15aa-200">若要執行重新組織，請使用[ALTER INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/alter-index-transact-sql)搭配 [重新組織] 選項。</span><span class="sxs-lookup"><span data-stu-id="d15aa-200">To perform a reorganize, use [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)with the REORGANIZE option.</span></span>

 <span data-ttu-id="d15aa-201">不需要進行重新組織，也能將 CLOSED 資料列群組移到資料行存放區中。</span><span class="sxs-lookup"><span data-stu-id="d15aa-201">Reorganizing is not required in order to move CLOSED rowgroups into the columnstore.</span></span> <span data-ttu-id="d15aa-202">Tuple 移動處理序最後會找到所有 CLOSED 資料列群組並加以移動。</span><span class="sxs-lookup"><span data-stu-id="d15aa-202">The tuple-mover process will eventually find all CLOSED rowgroups and move them.</span></span> <span data-ttu-id="d15aa-203">不過，Tuple 移動是單一執行緒，而且移動資料列群組的速度對於您的工作負載可能不夠快。</span><span class="sxs-lookup"><span data-stu-id="d15aa-203">However, the tuple-mover is single-threaded and might not move rowgroups fast enough for your workload.</span></span>

### <a name="recommendations-for-reorganizing"></a><span data-ttu-id="d15aa-204">對重新組織的建議</span><span class="sxs-lookup"><span data-stu-id="d15aa-204">Recommendations for Reorganizing</span></span>
 <span data-ttu-id="d15aa-205">重新組織叢集資料行存放區索引的時機：</span><span class="sxs-lookup"><span data-stu-id="d15aa-205">When to reorganize a clustered columnstore index:</span></span>

-   <span data-ttu-id="d15aa-206">在一次或多次資料載入後重新組織叢集資料行存放區索引，以便盡快獲得查詢效能的優勢。</span><span class="sxs-lookup"><span data-stu-id="d15aa-206">Reorganize a clustered columnstore index after one or more data loads to achieve query performance benefits as quickly as possible.</span></span> <span data-ttu-id="d15aa-207">進行重新組織一開始會需要額外的 CPU 資源來壓縮資料，這可能會拖慢整體系統效能。</span><span class="sxs-lookup"><span data-stu-id="d15aa-207">Reorganizing will initially require additional CPU resources to compress the data, which could slow overall system performance.</span></span> <span data-ttu-id="d15aa-208">不過，只要資料壓縮完成，查詢效能就能獲得改善。</span><span class="sxs-lookup"><span data-stu-id="d15aa-208">However, as soon as the data is compressed, query performance can improve.</span></span>


