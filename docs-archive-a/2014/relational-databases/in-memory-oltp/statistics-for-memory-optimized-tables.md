---
title: 記憶體最佳化資料表的統計資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e644766d-1d1c-43d7-83ff-8ccfe4f3af9f
author: rothja
ms.author: jroth
ms.openlocfilehash: 0ae09d76c2642e23c56afcdd5ae4e1e468ef5883
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708354"
---
# <a name="statistics-for-memory-optimized-tables"></a><span data-ttu-id="32ef4-102">記憶體最佳化資料表的統計資料</span><span class="sxs-lookup"><span data-stu-id="32ef4-102">Statistics for Memory-Optimized Tables</span></span>
  <span data-ttu-id="32ef4-103">查詢最佳化工具會使用有關資料行的統計資料來建立可改善查詢效能的查詢計劃。</span><span class="sxs-lookup"><span data-stu-id="32ef4-103">The query optimizer uses statistics about columns to create query plans that improve query performance.</span></span> <span data-ttu-id="32ef4-104">統計資料是從資料庫中的資料表收集，並且儲存在資料庫中繼資料內。</span><span class="sxs-lookup"><span data-stu-id="32ef4-104">Statistics are collected from the tables in the database and stored in the database metadata.</span></span>  
  
 <span data-ttu-id="32ef4-105">統計資料是自動建立的，但也可以手動建立。</span><span class="sxs-lookup"><span data-stu-id="32ef4-105">Statistics are created automatically, but can also be created manually.</span></span> <span data-ttu-id="32ef4-106">例如，建立索引時就會自動建立索引鍵資料行的統計資料。</span><span class="sxs-lookup"><span data-stu-id="32ef4-106">For example, statistics are created automatically for index key columns when the index is created.</span></span> <span data-ttu-id="32ef4-107">如需有關建立統計資料的詳細資訊，請參閱 [統計資料](../statistics/statistics.md)。</span><span class="sxs-lookup"><span data-stu-id="32ef4-107">For more information about creating statistics see [Statistics](../statistics/statistics.md).</span></span>  
  
 <span data-ttu-id="32ef4-108">資料表資料通常會隨資料列插入、更新和刪除而變更。</span><span class="sxs-lookup"><span data-stu-id="32ef4-108">Table data typically changes over time as rows are inserted, updated, and deleted.</span></span> <span data-ttu-id="32ef4-109">這表示，統計資料需要定期更新。</span><span class="sxs-lookup"><span data-stu-id="32ef4-109">This means statistics need to be updated periodically.</span></span> <span data-ttu-id="32ef4-110">根據預設，以磁碟為基礎的資料表上的統計資料會在最佳化工具判斷統計資料可能過期時自動更新。</span><span class="sxs-lookup"><span data-stu-id="32ef4-110">By default, statistics on disk-based tables are updated automatically when the optimizer determines they might be out of date.</span></span>  
  
 <span data-ttu-id="32ef4-111">根據預設，記憶體最佳化資料表上的統計資料不會更新。</span><span class="sxs-lookup"><span data-stu-id="32ef4-111">Statistics on memory-optimized tables are not updated by default.</span></span> <span data-ttu-id="32ef4-112">您需要手動更新這些統計資料。</span><span class="sxs-lookup"><span data-stu-id="32ef4-112">Instead, you need to update them manually.</span></span> <span data-ttu-id="32ef4-113">針對個別資料行、索引或資料表，請使用[UPDATE STATISTICS &#40;transact-sql&#41;](/sql/t-sql/statements/update-statistics-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="32ef4-113">Use [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql) for individual columns, indexes, or tables.</span></span> <span data-ttu-id="32ef4-114">使用[sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)來更新資料庫中所有使用者和內部資料表的統計資料。</span><span class="sxs-lookup"><span data-stu-id="32ef4-114">Use [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql) to update statistics for all user and internal tables in the database.</span></span>  
  
 <span data-ttu-id="32ef4-115">當您使用[CREATE statistics &#40;transact-sql&#41;](/sql/t-sql/statements/create-statistics-transact-sql)或[UPDATE statistics &#40;transact-sql&#41;](/sql/t-sql/statements/update-statistics-transact-sql)時，您必須指定 `NORECOMPUTE` 來停用記憶體優化資料表的自動統計資料更新。</span><span class="sxs-lookup"><span data-stu-id="32ef4-115">When using [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql) or [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql), you must specify `NORECOMPUTE` to disable automatic statistics update for memory-optimized tables.</span></span> <span data-ttu-id="32ef4-116">對於以磁片為基礎的資料表，只有在上次[sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)之後修改資料表時， [sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)才會更新統計資料。</span><span class="sxs-lookup"><span data-stu-id="32ef4-116">For disk based tables, [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql) only updates statistics if the table has been modified since the last [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql).</span></span> <span data-ttu-id="32ef4-117">對於記憶體優化資料表， [sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)一律會產生更新的統計資料。</span><span class="sxs-lookup"><span data-stu-id="32ef4-117">For memory-optimized tables, [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql) always generates updated statistics.</span></span> <span data-ttu-id="32ef4-118">[sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)是記憶體優化資料表的理想選項;否則，您必須知道哪些資料表有重大變更，才能個別更新統計資料。</span><span class="sxs-lookup"><span data-stu-id="32ef4-118">[sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql) is a good option for memory-optimized tables; otherwise you need to know which tables have significant changes so you can update statistics individually.</span></span>  
  
 <span data-ttu-id="32ef4-119">可以藉由取樣資料或執行完整掃描來產生統計資料。</span><span class="sxs-lookup"><span data-stu-id="32ef4-119">Statistics can either be generated by either sampling the data or performing a full scan.</span></span> <span data-ttu-id="32ef4-120">取樣的統計資料只會使用資料表資料的取樣來估計資料分佈情形。</span><span class="sxs-lookup"><span data-stu-id="32ef4-120">Sampled statistics only use a sample of the table data to estimate the data distribution.</span></span> <span data-ttu-id="32ef4-121">完整掃描的統計資料會掃描整個資料表來判斷資料分佈情形。</span><span class="sxs-lookup"><span data-stu-id="32ef4-121">Fullscan statistics scan the entire table to determine the data distribution.</span></span> <span data-ttu-id="32ef4-122">完整掃描的統計資料通常更正確，但要花較多的時間來計算。</span><span class="sxs-lookup"><span data-stu-id="32ef4-122">Fullscan statistics are usually more accurate but take longer to compute.</span></span> <span data-ttu-id="32ef4-123">取樣的統計資料收集速度較快。</span><span class="sxs-lookup"><span data-stu-id="32ef4-123">Sampled statistics can be collected faster.</span></span>  
  
 <span data-ttu-id="32ef4-124">以磁碟為基礎的資料表預設為使用取樣的統計資料。</span><span class="sxs-lookup"><span data-stu-id="32ef4-124">Disk-based tables use sampled statistics by default.</span></span> <span data-ttu-id="32ef4-125">記憶體最佳化資料表只支援完整掃描統計資料。</span><span class="sxs-lookup"><span data-stu-id="32ef4-125">Memory-optimized tables only support fullscan statistics.</span></span> <span data-ttu-id="32ef4-126">使用[CREATE statistics &#40;transact-sql&#41;](/sql/t-sql/statements/create-statistics-transact-sql)或[&#40;TRANSACT-SQL&#41;更新統計資料](/sql/t-sql/statements/update-statistics-transact-sql)時，您必須指定 `FULLSCAN` 記憶體優化資料表的選項。</span><span class="sxs-lookup"><span data-stu-id="32ef4-126">When using [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql) or [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql), you must specify the `FULLSCAN` option for memory-optimized tables.</span></span>  
  
 <span data-ttu-id="32ef4-127">記憶體最佳化資料表上統計資料的額外考量：</span><span class="sxs-lookup"><span data-stu-id="32ef4-127">Additional considerations for statistics on memory-optimized tables:</span></span>  
  
-   <span data-ttu-id="32ef4-128">記憶體最佳化資料表上的索引會隨資料表建立。</span><span class="sxs-lookup"><span data-stu-id="32ef4-128">Indexes on memory-optimized tables are created with the table.</span></span> <span data-ttu-id="32ef4-129">索引鍵資料行上的統計資料會在資料表為空白時建立。</span><span class="sxs-lookup"><span data-stu-id="32ef4-129">The statistics on the index key columns are created when the table is empty.</span></span> <span data-ttu-id="32ef4-130">因此，這些統計資料需要在資料載入資料表後更新。</span><span class="sxs-lookup"><span data-stu-id="32ef4-130">Therefore, these statistics need to be updated after data is loaded into the table.</span></span>  
  
-   <span data-ttu-id="32ef4-131">若是原生編譯預存程序，程序中查詢的執行計畫會在編譯程序時最佳化。</span><span class="sxs-lookup"><span data-stu-id="32ef4-131">For natively compiled stored procedures, execution plans for queries in the procedure are optimized when the procedure is compiled.</span></span> <span data-ttu-id="32ef4-132">這種情況只會在建立程序及伺服器重新啟動時發生，而不會在統計資料更新時發生。</span><span class="sxs-lookup"><span data-stu-id="32ef4-132">This happens only when the procedure is created and when the server restarts, not when statistics are updated.</span></span> <span data-ttu-id="32ef4-133">因此，資料表需要包含代表性的資料集，且統計資料需要處於最新狀態，才能建立程序 </span><span class="sxs-lookup"><span data-stu-id="32ef4-133">Therefore, the tables need to contain a representative set of data and statistics need to be up-to-date before the procedures are created.</span></span> <span data-ttu-id="32ef4-134">(如果讓資料庫離線後再次上線，或有任何伺服器重新啟動，則原生編譯的預存程序會重新編譯)。</span><span class="sxs-lookup"><span data-stu-id="32ef4-134">(Natively compiled stored procedures are recompiled if the database is taken offline and brought back online, or if there is a server restart.)</span></span>  
  
## <a name="guidelines-for-statistics-when-deploying-memory-optimized-tables"></a><span data-ttu-id="32ef4-135">部署記憶體最佳化資料表時統計資料的方針</span><span class="sxs-lookup"><span data-stu-id="32ef4-135">Guidelines for Statistics When Deploying Memory-Optimized Tables</span></span>  
 <span data-ttu-id="32ef4-136">為確保查詢最佳化工具建立查詢計劃時擁有最新的統計資料，請利用下列五個步驟部署記憶體最佳化資料表：</span><span class="sxs-lookup"><span data-stu-id="32ef4-136">To ensure that the query optimizer has up-to-date statistics when creating query plans, deploy memory-optimized tables using these five steps:</span></span>  
  
1.  <span data-ttu-id="32ef4-137">建立資料表及索引。</span><span class="sxs-lookup"><span data-stu-id="32ef4-137">Create tables and indexes.</span></span> <span data-ttu-id="32ef4-138">索引是在 `CREATE TABLE` 陳述式中以內嵌方式指定。</span><span class="sxs-lookup"><span data-stu-id="32ef4-138">Indexes are specified inline in the `CREATE TABLE` statements.</span></span>  
  
2.  <span data-ttu-id="32ef4-139">將資料載入資料表中。</span><span class="sxs-lookup"><span data-stu-id="32ef4-139">Load data into the tables.</span></span>  
  
3.  <span data-ttu-id="32ef4-140">更新資料表上的統計資料。</span><span class="sxs-lookup"><span data-stu-id="32ef4-140">Update statistics on the tables.</span></span>  
  
4.  <span data-ttu-id="32ef4-141">建立存取資料表的預存程序。</span><span class="sxs-lookup"><span data-stu-id="32ef4-141">Create stored procedures that access the tables.</span></span>  
  
5.  <span data-ttu-id="32ef4-142">執行工作負載，其中包含混合原生編譯和解譯的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 預存程序以及特定批次。</span><span class="sxs-lookup"><span data-stu-id="32ef4-142">Run the workload, which can contain a mix of natively compiled and interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] stored procedures, as well as ad hoc batches.</span></span>  
  
 <span data-ttu-id="32ef4-143">在您載入資料並更新統計資料後建立原生編譯預存程序，可確保最佳化工具能夠提供統計資料給記憶體最佳化資料表。</span><span class="sxs-lookup"><span data-stu-id="32ef4-143">Creating natively compiled stored procedures after you load the data and update the statistics ensures that the optimizer has statistics available for the memory-optimized tables.</span></span> <span data-ttu-id="32ef4-144">這樣將可確保編譯程序時，查詢計劃能夠保持效率。</span><span class="sxs-lookup"><span data-stu-id="32ef4-144">This will ensure efficient query plans when the procedure is compiled.</span></span>  
  
## <a name="guidelines-for-maintaining-statistics-on-memory-optimized-tables"></a><span data-ttu-id="32ef4-145">維護記憶體最佳化資料表上統計資料的方針</span><span class="sxs-lookup"><span data-stu-id="32ef4-145">Guidelines for Maintaining Statistics on Memory-Optimized Tables</span></span>  
 <span data-ttu-id="32ef4-146">為了讓統計資料保持最新狀態，請定期更新記憶體最佳化資料表上的統計資料。</span><span class="sxs-lookup"><span data-stu-id="32ef4-146">To keep statistics up-to-date, regularly update the statistics on memory-optimized tables.</span></span>  
  
 <span data-ttu-id="32ef4-147">如果資料經常變更，則應經常更新統計資料。</span><span class="sxs-lookup"><span data-stu-id="32ef4-147">If data changes frequently, you should update statistics frequently.</span></span> <span data-ttu-id="32ef4-148">例如，在批次更新後更新資料表統計資料。</span><span class="sxs-lookup"><span data-stu-id="32ef4-148">For example, update table statistics after a batch update.</span></span> <span data-ttu-id="32ef4-149">在您更新統計資料後，卸除並重新建立原生編譯預存程序，讓程序能夠利用更新的統計資料。</span><span class="sxs-lookup"><span data-stu-id="32ef4-149">After you update statistics, drop and recreate natively compiled stored procedures so they can benefit from the updated statistics.</span></span>  
  
 <span data-ttu-id="32ef4-150">.</span><span class="sxs-lookup"><span data-stu-id="32ef4-150">.</span></span>  
  
 <span data-ttu-id="32ef4-151">不要在尖峰工作負載期間更新統計資料。</span><span class="sxs-lookup"><span data-stu-id="32ef4-151">Do not update statistics during peak workload.</span></span>  
  
 <span data-ttu-id="32ef4-152">若要更新統計資料：</span><span class="sxs-lookup"><span data-stu-id="32ef4-152">To update statistics:</span></span>  
  
-   <span data-ttu-id="32ef4-153">用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來建立具有[更新統計](../maintenance-plans/update-statistics-task-maintenance-plan.md)資料[工作的維護計畫](../maintenance-plans/create-a-maintenance-plan.md)</span><span class="sxs-lookup"><span data-stu-id="32ef4-153">Use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to [Create a Maintenance Plan](../maintenance-plans/create-a-maintenance-plan.md) with an [Update Statistic Task](../maintenance-plans/update-statistics-task-maintenance-plan.md)</span></span>  
  
-   <span data-ttu-id="32ef4-154">或是透過 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 指令碼更新統計資料，如下列所討論。</span><span class="sxs-lookup"><span data-stu-id="32ef4-154">Or, update statistics through a [!INCLUDE[tsql](../../../includes/tsql-md.md)] script, as discussed below.</span></span>  
  
 <span data-ttu-id="32ef4-155">若要更新單一記憶體優化資料表的統計資料 (*myschema*。</span><span class="sxs-lookup"><span data-stu-id="32ef4-155">To update the statistics for a single memory-optimized table (*myschema*.</span></span> <span data-ttu-id="32ef4-156">*Mytable*) ，請執行下列腳本：</span><span class="sxs-lookup"><span data-stu-id="32ef4-156">*Mytable*), run the following script:</span></span>  
  
```  
UPDATE STATISTICS myschema.Mytable WITH FULLSCAN, NORECOMPUTE  
```  
  
 <span data-ttu-id="32ef4-157">若要更新目前資料庫中所有記憶體最佳化資料表的統計資料，請執行下列指令碼：</span><span class="sxs-lookup"><span data-stu-id="32ef4-157">To update statistics for all memory-optimized tables in the current database, run the following script:</span></span>  
  
```sql  
DECLARE @sql NVARCHAR(MAX) = N''  
  
SELECT @sql += N'  
   UPDATE STATISTICS ' + quotename(schema_name(schema_id)) + N'.' + quotename(name) + N' WITH FULLSCAN, NORECOMPUTE'  
FROM sys.tables WHERE is_memory_optimized=1  
  
EXEC sp_executesql @sql  
```  
  
 <span data-ttu-id="32ef4-158">若要更新資料庫中所有資料表的統計資料，請執行[sp_updatestats &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="32ef4-158">To update statistics for all tables in the database, run [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql).</span></span>  
  
 <span data-ttu-id="32ef4-159">下列範例會報告記憶體最佳化資料表的統計資料上次更新時間。</span><span class="sxs-lookup"><span data-stu-id="32ef4-159">The following sample reports when the statistics on memory-optimized tables were last updated.</span></span> <span data-ttu-id="32ef4-160">這項資訊可協助您決定是否需要更新統計資料。</span><span class="sxs-lookup"><span data-stu-id="32ef4-160">This information can help you decide if you need to update the statistics.</span></span>  
  
```sql  
select t.object_id, t.name, sp.last_updated as 'stats_last_updated'  
from sys.tables t join sys.stats s on t.object_id=s.object_id cross apply sys.dm_db_stats_properties(t.object_id, s.stats_id) sp  
where t.is_memory_optimized=1  
```  
  
## <a name="see-also"></a><span data-ttu-id="32ef4-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32ef4-161">See Also</span></span>  
 [<span data-ttu-id="32ef4-162">記憶體最佳化資料表</span><span class="sxs-lookup"><span data-stu-id="32ef4-162">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
