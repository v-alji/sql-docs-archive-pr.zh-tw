---
title: 監視和針對使用量進行記憶體疑難排解 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 7a458b9c-3423-4e24-823d-99573544c877
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5805ed06ad78040dbdf6c8557e5f548ad57f618b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709438"
---
# <a name="monitor-and-troubleshoot-memory-usage"></a><span data-ttu-id="cc014-102">監視與疑難排解記憶體使用量</span><span class="sxs-lookup"><span data-stu-id="cc014-102">Monitor and Troubleshoot Memory Usage</span></span>
  [!INCLUDE[hek_1](../../includes/hek-1-md.md)] <span data-ttu-id="cc014-103">耗用記憶體的模式與磁碟資料表不同。</span><span class="sxs-lookup"><span data-stu-id="cc014-103">consumes memory in different patterns than disk-based tables.</span></span> <span data-ttu-id="cc014-104">您可以使用針對記憶體和記憶體回收子系統提供的 DMV 或效能計數器，監視資料庫中記憶體最佳化資料表和索引所配置和使用的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="cc014-104">You can monitor the amount of memory allocated and used by memory-optimized tables and indexes in your database using the DMVs or performance counters provided for memory and the garbage collection subsystem.</span></span>  <span data-ttu-id="cc014-105">如此就能讓您同時深入查看系統和資料庫層級，並且讓您防止因記憶體耗盡而發生問題。</span><span class="sxs-lookup"><span data-stu-id="cc014-105">This gives you visibility at both the system and database level and lets you prevent problems due to memory exhaustion.</span></span>

 <span data-ttu-id="cc014-106">本主題將涵蓋監視您的 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="cc014-106">This topic covers monitoring your [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] memory usage.</span></span>


##  <a name="create-a-sample-database-with-memory-optimized-tables"></a><a name="bkmk_CreateDB"></a> <span data-ttu-id="cc014-107">建立含有記憶體最佳化資料表的範例資料庫</span><span class="sxs-lookup"><span data-stu-id="cc014-107">Create a sample database with memory-optimized tables</span></span>
 <span data-ttu-id="cc014-108">如果您的資料庫已包含記憶體最佳化資料表，則可略過本節。</span><span class="sxs-lookup"><span data-stu-id="cc014-108">You can skip this section if you already have a database with memory-optimized tables.</span></span>

 <span data-ttu-id="cc014-109">下列步驟將建立有三個記憶體最佳化資料表的資料庫，方便您在本主題其餘部分中使用。</span><span class="sxs-lookup"><span data-stu-id="cc014-109">The following steps create a database with three memory-optimized tables that you can use in the remainder of this topic.</span></span> <span data-ttu-id="cc014-110">在此範例中，我們將資料庫對應至資源集區，以便控制記憶體最佳化資料表可以取用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="cc014-110">In the example, we mapped the database to a resource pool so that we can control how much memory can be taken by memory-optimized tables.</span></span>

1.  <span data-ttu-id="cc014-111">啟動 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cc014-111">Launch [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>

2.  <span data-ttu-id="cc014-112">按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="cc014-112">Click **New Query**.</span></span>

3.  <span data-ttu-id="cc014-113">將此程式碼貼入新查詢視窗，並執行每一個區段。</span><span class="sxs-lookup"><span data-stu-id="cc014-113">Paste this code into the new query window and execute each section.</span></span>

    ```
    -- create a database to be used
    CREATE DATABASE IMOLTP_DB
    GO

    ALTER DATABASE IMOLTP_DB ADD FILEGROUP IMOLTP_DB_xtp_fg CONTAINS MEMORY_OPTIMIZED_DATA
    ALTER DATABASE IMOLTP_DB ADD FILE( NAME = 'IMOLTP_DB_xtp' , FILENAME = 'C:\Data\IMOLTP_DB_xtp') TO FILEGROUP IMOLTP_DB_xtp_fg;
    GO

    USE IMOLTP_DB
    GO

    -- create the resoure pool
    CREATE RESOURCE POOL PoolIMOLTP WITH (MAX_MEMORY_PERCENT = 60);
    ALTER RESOURCE GOVERNOR RECONFIGURE;
    GO

    -- bind the database to a resource pool
    EXEC sp_xtp_bind_db_resource_pool 'IMOLTP_DB', 'PoolIMOLTP'

    -- you can query the binding using the catalog view as described here
    SELECT d.database_id
         , d.name
         , d.resource_pool_id
    FROM sys.databases d
    GO

    -- take database offline/online to finalize the binding to the resource pool
    USE master
    GO

    ALTER DATABASE IMOLTP_DB SET OFFLINE
    GO
    ALTER DATABASE IMOLTP_DB SET ONLINE
    GO

    -- create some tables
    USE IMOLTP_DB
    GO

    -- create table t1
    CREATE TABLE dbo.t1 (
           c1 int NOT NULL CONSTRAINT [pk_t1_c1] PRIMARY KEY NONCLUSTERED
         , c2 char(40) NOT NULL
         , c3 char(8000) NOT NULL
         ) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)
    GO

    -- load t1 150K rows
    DECLARE @i int = 0
    BEGIN TRAN
    WHILE (@i <= 150000)
       BEGIN
          INSERT t1 VALUES (@i, 'a', replicate ('b', 8000))
          SET @i += 1;
       END
    Commit
    GO

    -- Create another table, t2
    CREATE TABLE dbo.t2 (
           c1 int NOT NULL CONSTRAINT [pk_t2_c1] PRIMARY KEY NONCLUSTERED
         , c2 char(40) NOT NULL
         , c3 char(8000) NOT NULL
         ) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)
    GO

    -- Create another table, t3 
    CREATE TABLE dbo.t3 (
           c1 int NOT NULL CONSTRAINT [pk_t3_c1] PRIMARY KEY NONCLUSTERED HASH (c1) WITH (BUCKET_COUNT = 1000000)
         , c2 char(40) NOT NULL
         , c3 char(8000) NOT NULL
         ) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)
    GO
    ```

##  <a name="monitoring-memory-usage"></a><span data-ttu-id="cc014-114">監視記憶體使用狀況</span><span class="sxs-lookup"><span data-stu-id="cc014-114">Monitoring Memory Usage</span></span>

###  <a name="using-ssmanstudiofull"></a><span data-ttu-id="cc014-115">使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc014-115">Using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]</span></span>
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="cc014-116">隨附內建的標準報表，可用來監視記憶體中資料表耗用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="cc014-116">ships with built-in standard reports to monitor the memory consumed by in-memory tables.</span></span> <span data-ttu-id="cc014-117">您可以使用 [物件總管] 存取這些報表。</span><span class="sxs-lookup"><span data-stu-id="cc014-117">You can access these reports using Object Explorer.</span></span> <span data-ttu-id="cc014-118">您也可以使用物件總管監視個別記憶體最佳化資料表耗用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="cc014-118">You can also use the object explorer to monitor memory consumed by individual memory-optimized tables.</span></span>

#### <a name="consumption-at-the-database-level"></a><span data-ttu-id="cc014-119">資料庫層級的耗用量</span><span class="sxs-lookup"><span data-stu-id="cc014-119">Consumption at the database level</span></span>
 <span data-ttu-id="cc014-120">您可以監視資料庫層級的記憶體使用量，如下所述。</span><span class="sxs-lookup"><span data-stu-id="cc014-120">You can monitor memory use at the database level as follows.</span></span>

1.  <span data-ttu-id="cc014-121">啟動 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 並連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="cc014-121">Launch [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and connect to a server.</span></span>

2.  <span data-ttu-id="cc014-122">在 [物件總管] 中，以滑鼠右鍵按一下要產生報表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="cc014-122">In Object Explorer, right-click the database you want reports on.</span></span>

3.  <span data-ttu-id="cc014-123">在操作功能表中，依序選取 [報表] -> [標準報表] -> [記憶體最佳化物件的記憶體使用量]</span><span class="sxs-lookup"><span data-stu-id="cc014-123">In the context menu select, **Reports** -> **Standard Reports** -> **Memory Usage By Memory Optimized Objects**</span></span>

 <span data-ttu-id="cc014-124">![HK_MM_SSMS](../../database-engine/media/hk-mm-ssms-stdrpt-memuse.gif "HK_MM_SSMS")</span><span class="sxs-lookup"><span data-stu-id="cc014-124">![HK_MM_SSMS](../../database-engine/media/hk-mm-ssms-stdrpt-memuse.gif "HK_MM_SSMS")</span></span>

 <span data-ttu-id="cc014-125">此報表會顯示上面所建立資料庫的記憶體耗用量。</span><span class="sxs-lookup"><span data-stu-id="cc014-125">This report shows memory consumption by the database we created above.</span></span>

 <span data-ttu-id="cc014-126">![HK_MM_SSMS](../../database-engine/media/hk-mm-ssms-stdrpt-memuserpt.gif "HK_MM_SSMS")</span><span class="sxs-lookup"><span data-stu-id="cc014-126">![HK_MM_SSMS](../../database-engine/media/hk-mm-ssms-stdrpt-memuserpt.gif "HK_MM_SSMS")</span></span>

###  <a name="using-dmvs"></a><span data-ttu-id="cc014-127">使用 DMVs</span><span class="sxs-lookup"><span data-stu-id="cc014-127">Using DMVs</span></span>
 <span data-ttu-id="cc014-128">有許多 DMV 可用來監視記憶體最佳化資料表、索引、系統物件及執行階段結構所耗用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="cc014-128">There are a number of DMVs available to monitor memory consumed by memory-optimized tables, indexes, system objects, and by run-time structures.</span></span>

#### <a name="memory-consumption-by-memory-optimized-tables-and-indexes"></a><span data-ttu-id="cc014-129">記憶體最佳化資料表和索引的記憶體耗用量</span><span class="sxs-lookup"><span data-stu-id="cc014-129">Memory consumption by memory-optimized tables and indexes</span></span>
 <span data-ttu-id="cc014-130">您可以藉由查詢 `sys.dm_db_xtp_table_memory_stats` 找到所有使用者資料表、索引和系統物件的記憶體耗用量，如此處所示。</span><span class="sxs-lookup"><span data-stu-id="cc014-130">You can find memory consumption for all user tables, indexes, and system objects by querying `sys.dm_db_xtp_table_memory_stats` as shown here.</span></span>

```sql
SELECT object_name(object_id) AS Name
     , *
   FROM sys.dm_db_xtp_table_memory_stats
```

 <span data-ttu-id="cc014-131">**範例輸出**</span><span class="sxs-lookup"><span data-stu-id="cc014-131">**Sample Output**</span></span>

```
Name       object_id   memory_allocated_for_table_kb memory_used_by_table_kb memory_allocated_for_indexes_kb memory_used_by_indexes_kb
---------- ----------- ----------------------------- ----------------------- ------------------------------- -------------------------
t3         629577281   0                             0                       128                             0
t1         565577053   1372928                       1200008                 7872                            1942
t2         597577167   0                             0                       128                             0
NULL       -6          0                             0                       2                               2
NULL       -5          0                             0                       24                              24
NULL       -4          0                             0                       2                               2
NULL       -3          0                             0                       2                               2
NULL       -2          192                           25                      16                              16
```

 <span data-ttu-id="cc014-132">如需詳細資訊，請參閱[sys. dm_db_xtp_table_memory_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql?view=sql-server-2016)。</span><span class="sxs-lookup"><span data-stu-id="cc014-132">For more information, see [sys.dm_db_xtp_table_memory_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql?view=sql-server-2016).</span></span>

#### <a name="memory-consumption-by-internal-system-structures"></a><span data-ttu-id="cc014-133">內部系統結構的記憶體耗用量</span><span class="sxs-lookup"><span data-stu-id="cc014-133">Memory consumption by internal system structures</span></span>
 <span data-ttu-id="cc014-134">系統物件也會耗用記憶體，這些系統物件包括交易式結構、資料和差異檔案的緩衝區、記憶體回收結構等。</span><span class="sxs-lookup"><span data-stu-id="cc014-134">Memory is also consumed by system objects, such as, transactional structures, buffers for data and delta files, garbage collection structures, and more.</span></span> <span data-ttu-id="cc014-135">您可以藉由查詢 `sys.dm_xtp_system_memory_consumers` 找到這些系統物件所使用的記憶體，如此處所示。</span><span class="sxs-lookup"><span data-stu-id="cc014-135">You can find the memory used for these system objects by querying `sys.dm_xtp_system_memory_consumers` as shown here.</span></span>

```sql
SELECT memory_consumer_desc
     , allocated_bytes/1024 AS allocated_bytes_kb
     , used_bytes/1024 AS used_bytes_kb
     , allocation_count
   FROM sys.dm_xtp_system_memory_consumers
```

 <span data-ttu-id="cc014-136">**範例輸出**</span><span class="sxs-lookup"><span data-stu-id="cc014-136">**Sample Output**</span></span>

```
memory_consumer_ desc allocated_bytes_kb   used_bytes_kb        allocation_count
------------------------- -------------------- -------------------- ----------------
VARHEAP                   0                    0                    0
VARHEAP                   384                  0                    0
DBG_GC_OUTSTANDING_T      64                   64                   910
ACTIVE_TX_MAP_LOOKAS      0                    0                    0
RECOVERY_TABLE_CACHE      0                    0                    0
RECENTLY_USED_ROWS_L      192                  192                  261
RANGE_CURSOR_LOOKSID      0                    0                    0
HASH_CURSOR_LOOKASID      128                  128                  455
SAVEPOINT_LOOKASIDE       0                    0                    0
PARTIAL_INSERT_SET_L      192                  192                  351
CONSTRAINT_SET_LOOKA      192                  192                  646
SAVEPOINT_SET_LOOKAS      0                    0                    0
WRITE_SET_LOOKASIDE       192                  192                  183
SCAN_SET_LOOKASIDE        64                   64                   31
READ_SET_LOOKASIDE        0                    0                    0
TRANSACTION_LOOKASID      448                  448                  156
PGPOOL:256K               768                  768                  3
PGPOOL: 64K               0                    0                    0
PGPOOL:  4K               0                    0                    0
```

 <span data-ttu-id="cc014-137">如需詳細資訊，請參閱 [sys.dm_xtp_system_memory_consumers &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cc014-137">For more information see [sys.dm_xtp_system_memory_consumers &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql).</span></span>


#### <a name="memory-consumption-at-run-time-when-accessing-memory-optimized-tables"></a><span data-ttu-id="cc014-138">存取記憶體最佳化資料表時的執行階段記憶體耗用量</span><span class="sxs-lookup"><span data-stu-id="cc014-138">Memory consumption at run-time when accessing memory-optimized tables</span></span>
 <span data-ttu-id="cc014-139">您可以使用下列查詢判斷執行階段結構 (例如程序快取) 所耗用的記憶體：執行此查詢可取得執行階段結構 (例如程序快取) 所使用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="cc014-139">You can determine the memory consumed by run time structures, such as the procedure cache with the following query: run this query to get the memory used by run-time structures such as for the procedure cache.</span></span> <span data-ttu-id="cc014-140">所有執行階段結構都會加上 XTP 標記。</span><span class="sxs-lookup"><span data-stu-id="cc014-140">All run-time structures are tagged with XTP.</span></span>

```sql
SELECT memory_object_address
     , pages_in_bytes
     , bytes_used
     , type
   FROM sys.dm_os_memory_objects WHERE type LIKE '%xtp%'
```

 <span data-ttu-id="cc014-141">**範例輸出**</span><span class="sxs-lookup"><span data-stu-id="cc014-141">**Sample Output**</span></span>

```
memory_object_address pages_ in_bytes bytes_used type
--------------------- ------------------- ---------- ----
0x00000001F1EA8040    507904              NULL       MEMOBJ_XTPDB
0x00000001F1EAA040    68337664            NULL       MEMOBJ_XTPDB
0x00000001FD67A040    16384               NULL       MEMOBJ_XTPPROCCACHE
0x00000001FD68C040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD284040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD302040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD382040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD402040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD482040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD502040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001FD67E040    16384               NULL       MEMOBJ_XTPPROCPARTITIONEDHEAP
0x00000001F813C040    8192                NULL       MEMOBJ_XTPBLOCKALLOC
0x00000001F813E040    16842752            NULL       MEMOBJ_XTPBLOCKALLOC
```

 <span data-ttu-id="cc014-142">如需詳細資訊，請參閱[dm_os_memory_objects (transact-sql) ](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cc014-142">For more information, see [sys.dm_os_memory_objects (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql).</span></span>

#### <a name="memory-consumed-by-hek_2-engine-across-the-instance"></a><span data-ttu-id="cc014-143">[!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 引擎跨執行個體所耗用的記憶體</span><span class="sxs-lookup"><span data-stu-id="cc014-143">Memory consumed by [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] engine across the instance</span></span>
 <span data-ttu-id="cc014-144">管理配置給 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 引擎和記憶體最佳化物件之記憶體的方式，與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中其他任何記憶體取用者的管理方式相同。</span><span class="sxs-lookup"><span data-stu-id="cc014-144">Memory allocated to the [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] engine and the memory-optimized objects is managed the same way as any other memory consumer within a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="cc014-145">MEMORYCLERK_XTP 類型的 Clerk 會考量所有配置給 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 引擎的記憶體。</span><span class="sxs-lookup"><span data-stu-id="cc014-145">The clerks of type MEMORYCLERK_XTP accounts for all the memory allocated to [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] engine.</span></span> <span data-ttu-id="cc014-146">使用下列查詢可找出 [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] 引擎所使用的所有記憶體。</span><span class="sxs-lookup"><span data-stu-id="cc014-146">Use the following query to find all the memory used by the [!INCLUDE[hek_2](../../../includes/hek-2-md.md)] engine.</span></span>

```sql
-- this DMV accounts for all memory used by the hek_2 engine
SELECT type
     , name
     , memory_node_id
     , pages_kb/1024 AS pages_MB 
   FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'
```

 <span data-ttu-id="cc014-147">此範例輸出顯示，在配置的總記憶體中，18 MB 為系統層級記憶體耗用量，1358 MB 則配置給資料庫識別碼 5。</span><span class="sxs-lookup"><span data-stu-id="cc014-147">The sample output shows that the total memory allocated is 18 MB system-level memory consumption and 1358MB allocated to database id of 5.</span></span> <span data-ttu-id="cc014-148">由於此資料庫對應至專用資源集區，因此該記憶體會佔用資源集區。</span><span class="sxs-lookup"><span data-stu-id="cc014-148">Since this database is mapped to a dedicated resource pool, this memory is accounted for in that resource pool.</span></span>

 <span data-ttu-id="cc014-149">**範例輸出**</span><span class="sxs-lookup"><span data-stu-id="cc014-149">**Sample Output**</span></span>

```
type                 name       memory_node_id pages_MB
-------------------- ---------- -------------- --------------------
MEMORYCLERK_XTP      Default    0              18
MEMORYCLERK_XTP      DB_ID_5    0              1358
MEMORYCLERK_XTP      Default    64             0
```

 <span data-ttu-id="cc014-150">如需詳細資訊，請參閱[dm_os_memory_clerks (transact-sql) ](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cc014-150">For more information, see [sys.dm_os_memory_clerks (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql).</span></span>

##   <a name="managing-memory-consumed-by-memory-optimized-objects"></a><span data-ttu-id="cc014-151">管理記憶體最佳化物件耗用的記憶體</span><span class="sxs-lookup"><span data-stu-id="cc014-151">Managing memory consumed by memory-optimized objects</span></span>
 <span data-ttu-id="cc014-152">您可以藉由將記憶體最佳化資料表繫結至具名資源集區的方式，控制資料表耗用的總記憶體，如 [將包含記憶體最佳化資料表的資料庫繫結至資源集區](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)主題中所述。</span><span class="sxs-lookup"><span data-stu-id="cc014-152">You can control the total memory consumed by memory-optimized tables by binding it to a named resource pool as described in the topic [Bind a Database with Memory-Optimized Tables to a Resource Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md).</span></span>

##  <a name="troubleshooting-memory-issues"></a><span data-ttu-id="cc014-153">進行記憶體問題疑難排解</span><span class="sxs-lookup"><span data-stu-id="cc014-153">Troubleshooting Memory Issues</span></span>
 <span data-ttu-id="cc014-154">對記憶體問題進行疑難排解是包含三個步驟的程序：</span><span class="sxs-lookup"><span data-stu-id="cc014-154">Troubleshooting memory issues is a three step process:</span></span>

1.  <span data-ttu-id="cc014-155">識別資料庫或執行個體中物件所耗用的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="cc014-155">Identify how much memory is being consumed by the objects in your database or instance.</span></span> <span data-ttu-id="cc014-156">您可以使用可供記憶體最佳化資料表使用的各種不同監視工具，如前文所述。</span><span class="sxs-lookup"><span data-stu-id="cc014-156">You can use a rich set of monitoring tools available for memory-optimized tables as described earlier.</span></span>  <span data-ttu-id="cc014-157">例如， `sys.dm_db_xtp_table_memory_stats` 或 `sys.dm_os_memory_clerks`這兩種 DMV。</span><span class="sxs-lookup"><span data-stu-id="cc014-157">For example the DMVs `sys.dm_db_xtp_table_memory_stats` or `sys.dm_os_memory_clerks`.</span></span>

2.  <span data-ttu-id="cc014-158">判斷記憶體耗用量增加的情況，以及您所剩的預留空間。</span><span class="sxs-lookup"><span data-stu-id="cc014-158">Determine how memory consumption is growing and how much head room you have left.</span></span> <span data-ttu-id="cc014-159">透過定期監視記憶體耗用量，就可以得知記憶體使用量成長的情況。</span><span class="sxs-lookup"><span data-stu-id="cc014-159">By monitoring the memory consumption periodically, you can know how the memory use is growing.</span></span> <span data-ttu-id="cc014-160">例如，如果您已將資料庫對應至具名資源集區，就可以監視效能計數器 Used Memory (KB)，查看記憶體使用量成長的情況。</span><span class="sxs-lookup"><span data-stu-id="cc014-160">For example, if you have mapped the database to a named resource pool, you can monitor the performance counter Used Memory (KB) to see how memory usage is growing.</span></span>

3.  <span data-ttu-id="cc014-161">採取動作消除可能發生的記憶體問題。</span><span class="sxs-lookup"><span data-stu-id="cc014-161">Take action to mitigate the potential memory issues.</span></span> <span data-ttu-id="cc014-162">如需詳細資訊，請參閱[解決記憶體不足問題](resolve-out-of-memory-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="cc014-162">For more information, see [Resolve Out Of Memory Issues](resolve-out-of-memory-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cc014-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc014-163">See Also</span></span>
 <span data-ttu-id="cc014-164">將[具有記憶體優化資料表的資料庫系結至資源集](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)區[變更 MIN_MEMORY_PERCENT 並 MAX_MEMORY_PERCENT 在現有集區上](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool)</span><span class="sxs-lookup"><span data-stu-id="cc014-164">[Bind a Database with Memory-Optimized Tables to a Resource Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) [Change MIN_MEMORY_PERCENT and MAX_MEMORY_PERCENT on an existing pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool)</span></span>


