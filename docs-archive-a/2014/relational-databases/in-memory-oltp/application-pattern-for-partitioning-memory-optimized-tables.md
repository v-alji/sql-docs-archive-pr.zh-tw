---
title: 分割記憶體最佳化資料表的應用程式模式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 3f867763-a8e6-413a-b015-20e9672cc4d1
author: rothja
ms.author: jroth
ms.openlocfilehash: d2633cdf1b631a1d9209adf26f4773e27c4c44c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592010"
---
# <a name="application-pattern-for-partitioning-memory-optimized-tables"></a><span data-ttu-id="1bbcd-102">分割記憶體最佳化資料表的應用程式模式</span><span class="sxs-lookup"><span data-stu-id="1bbcd-102">Application Pattern for Partitioning Memory-Optimized Tables</span></span>
  [!INCLUDE[hek_2](../../includes/hek-2-md.md)] <span data-ttu-id="1bbcd-103">支援的模式如下：將有限的使用中資料數量保留在記憶體最佳化資料表中，而比較不常存取的資料則在磁碟中處理。</span><span class="sxs-lookup"><span data-stu-id="1bbcd-103">supports a pattern where a limited amount of active data is kept in a memory-optimized table, while less-frequently accessed data is processed on disk.</span></span> <span data-ttu-id="1bbcd-104">這種情況一般都是根據 `datetime` 索引鍵儲存資料。</span><span class="sxs-lookup"><span data-stu-id="1bbcd-104">Typically, this would be a scenario where data is stored based on a `datetime` key.</span></span>  
  
 <span data-ttu-id="1bbcd-105">您可以藉由使用通用的結構描述維護分割區資料表和記憶體最佳化資料表的方式，利用記憶體最佳化資料表模擬分割區資料表。</span><span class="sxs-lookup"><span data-stu-id="1bbcd-105">You can emulate partitioned tables with memory-optimized tables by maintaining a partitioned table and a memory-optimized table with a common schema.</span></span> <span data-ttu-id="1bbcd-106">目前的資料會插入記憶體最佳化資料表中並進行更新，而較不常存取的資料會在傳統的分割區資料表中維護。</span><span class="sxs-lookup"><span data-stu-id="1bbcd-106">Current data would be inserted and updated in the memory-optimized table, while less-frequently accessed data would be maintained in the traditional partitioned table.</span></span>  
  
 <span data-ttu-id="1bbcd-107">了解使用中資料在記憶體最佳化資料表中的應用程式，可使用原生方式編譯預存程序以存取資料。</span><span class="sxs-lookup"><span data-stu-id="1bbcd-107">An application that knows that the active data is in a memory-optimized table can use natively compiled stored procedures to access the data.</span></span> <span data-ttu-id="1bbcd-108">對於需要存取整個資料範圍，或可能不知道哪個資料表保有相關資料的作業，都會使用解譯的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 結合記憶體最佳化的資料表與分割資料表。</span><span class="sxs-lookup"><span data-stu-id="1bbcd-108">Operations that need to access the entire span of data, or which may not know which table holds relevant data, use interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] to join the memory-optimized table with the partitioned table.</span></span>  
  
 <span data-ttu-id="1bbcd-109">此分割區切換描述如下：</span><span class="sxs-lookup"><span data-stu-id="1bbcd-109">This partition switch is described as follows:</span></span>  
  
-   <span data-ttu-id="1bbcd-110">從記憶體中 OLTP 資料表將資料插入暫存資料表中，可能是使用截止日期。</span><span class="sxs-lookup"><span data-stu-id="1bbcd-110">Insert data from the In-Memory OLTP table into a staging table, possibly using a cutoff date.</span></span>  
  
-   <span data-ttu-id="1bbcd-111">從記憶體最佳化資料表刪除相同的資料。</span><span class="sxs-lookup"><span data-stu-id="1bbcd-111">Delete the same data from the memory-optimized table.</span></span>  
  
-   <span data-ttu-id="1bbcd-112">在暫存資料表中交換。</span><span class="sxs-lookup"><span data-stu-id="1bbcd-112">Swap in the staging table.</span></span>  
  
-   <span data-ttu-id="1bbcd-113">加入使用中分割區。</span><span class="sxs-lookup"><span data-stu-id="1bbcd-113">Add the active partition.</span></span>  
  
 <span data-ttu-id="1bbcd-114">![分割區切換。](../../database-engine/media/hekaton-partitioned-tables.gif "分割區切換。")</span><span class="sxs-lookup"><span data-stu-id="1bbcd-114">![Partition switch.](../../database-engine/media/hekaton-partitioned-tables.gif "Partition switch.")</span></span>  
<span data-ttu-id="1bbcd-115">使用中資料維護</span><span class="sxs-lookup"><span data-stu-id="1bbcd-115">Active Data Maintenance</span></span>  
  
 <span data-ttu-id="1bbcd-116">從刪除使用中訂單開始的動作必須在維護期間完成，以免在刪除資料以及在暫存資料表中切換之間會遺失查詢資料。</span><span class="sxs-lookup"><span data-stu-id="1bbcd-116">The actions starting with Deleting ActiveOrders need to be done during a maintenance window to avoid queries missing data during the time between deleting data and switching in the staging table.</span></span>  
  
 <span data-ttu-id="1bbcd-117">如需相關範例，請參閱 [應用程式層級資料分割](application-level-partitioning.md)。</span><span class="sxs-lookup"><span data-stu-id="1bbcd-117">For a related sample, see [Application-Level Partitioning](application-level-partitioning.md).</span></span>  
  
## <a name="code-sample"></a><span data-ttu-id="1bbcd-118">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="1bbcd-118">Code Sample</span></span>  
 <span data-ttu-id="1bbcd-119">下列範例示範如何使用具有分割磁碟型資料表之記憶體最佳化的資料表。</span><span class="sxs-lookup"><span data-stu-id="1bbcd-119">The following sample shows how to use a memory-optimized table with a partitioned disk-based table.</span></span> <span data-ttu-id="1bbcd-120">經常使用的資料會儲存在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="1bbcd-120">Frequently-used data is stored in memory.</span></span> <span data-ttu-id="1bbcd-121">如果要將資料儲存到磁碟，請建立新的磁碟分割區，並將資料複製到分割資料表。</span><span class="sxs-lookup"><span data-stu-id="1bbcd-121">To save the data to disk, create a new partition and copy the data to the partitioned table.</span></span>  
  
 <span data-ttu-id="1bbcd-122">此範例的第一個部分會建立資料庫和必要的物件。</span><span class="sxs-lookup"><span data-stu-id="1bbcd-122">The first part of this sample creates the database and necessary objects.</span></span> <span data-ttu-id="1bbcd-123">第二部分會示範如何將資料從記憶體最佳化的資料表，移至分割資料表。</span><span class="sxs-lookup"><span data-stu-id="1bbcd-123">The second part of the sample shows how to move data from a memory-optimized table into a partitioned table.</span></span>  
  
```sql  
CREATE DATABASE partitionsample;  
GO  
  
-- enable for In-Memory OLTP - change file path as needed  
ALTER DATABASE partitionsample ADD FILEGROUP partitionsample_mod CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE partitionsample ADD FILE( NAME = 'partitionsample_mod' , FILENAME = 'c:\data\partitionsample_mod') TO FILEGROUP partitionsample_mod;  
GO  
  
USE partitionsample;  
GO  
  
-- frequently used portion of the SalesOrders - memory-optimized  
  
CREATE TABLE dbo.SalesOrders_hot (  
   so_id INT IDENTITY PRIMARY KEY NONCLUSTERED,  
   cust_id INT NOT NULL,  
   so_date DATETIME2 NOT NULL INDEX ix_date NONCLUSTERED,  
   so_total MONEY NOT NULL,  
   INDEX ix_date_total NONCLUSTERED (so_date desc, so_total desc)  
) WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
-- cold portion of the SalesOrders - partitioned disk-based table  
CREATE PARTITION FUNCTION [ByDatePF](datetime2) AS RANGE RIGHT   
   FOR VALUES();  
GO  
  
CREATE PARTITION SCHEME [ByDateRange]   
   AS PARTITION [ByDatePF]   
   ALL TO ([PRIMARY]);  
GO  
  
CREATE TABLE dbo.SalesOrders_cold (  
   so_id INT NOT NULL,  
   cust_id INT NOT NULL,  
   so_date DATETIME2 NOT NULL,  
   so_total MONEY NOT NULL,  
   CONSTRAINT PK_SalesOrders_cold PRIMARY KEY (so_id, so_date),  
   INDEX ix_date_total NONCLUSTERED (so_date desc, so_total desc)  
) ON [ByDateRange](so_date)  
GO  
  
-- table for temporary partitions  
CREATE TABLE dbo.SalesOrders_cold_staging (  
   so_id INT NOT NULL,  
   cust_id INT NOT NULL,  
   so_date datetime2 NOT NULL,  
   so_total MONEY NOT NULL,  
   CONSTRAINT PK_SalesOrders_cold_staging PRIMARY KEY (so_id, so_date),  
   INDEX ix_date_total NONCLUSTERED (so_date desc, so_total desc),  
   CONSTRAINT CHK_SalesOrders_cold_staging CHECK (so_date >= '1900-01-01')  
)  
GO  
  
-- aggregate view of the hot and cold data  
CREATE VIEW dbo.SalesOrders  
AS SELECT so_id,  
   cust_id,  
   so_date,  
   so_total,  
   1 AS 'is_hot'  
   FROM dbo.SalesOrders_hot  
   UNION ALL  
   SELECT so_id,  
          cust_id,  
          so_date,  
          so_total,  
          0 AS 'is_hot'  
          FROM dbo.SalesOrders_cold;  
GO  
  
-- move all sales orders up to the split date to cold storage  
CREATE PROCEDURE dbo.usp_SalesOrdersOffloadToCold @splitdate datetime2  
   AS  
   BEGIN  
      BEGIN TRANSACTION;  
      -- create new heap based on the hot data to be moved to cold storage  
      INSERT INTO dbo.SalesOrders_cold_staging WITH( TABLOCKX)  
      SELECT so_id , cust_id , so_date , so_total  
         FROM dbo.SalesOrders_hot WITH ( serializable)  
         WHERE so_date <= @splitdate;  
  
      -- remove moved data  
      DELETE FROM dbo.SalesOrders_hot WITH( SERIALIZABLE)  
         WHERE so_date <= @splitdate;  
  
      -- update partition function, and switch in new partition  
      ALTER PARTITION SCHEME [ByDateRange] NEXT USED [PRIMARY];  
  
      DECLARE @p INT = ( SELECT MAX( partition_number) FROM sys.partitions WHERE object_id = OBJECT_ID( 'dbo.SalesOrders_cold'));  
      EXEC sp_executesql N'alter table dbo.SalesOrders_cold_staging  
         SWITCH TO dbo.SalesOrders_cold partition @i' , N'@i int' , @i = @p;  
  
      ALTER PARTITION FUNCTION [ByDatePF]()  
      SPLIT RANGE( @splitdate);  
  
      -- modify constraint on staging table to align with new partition  
      ALTER TABLE dbo.SalesOrders_cold_staging DROP CONSTRAINT CHK_SalesOrders_cold_staging;  
  
      DECLARE @s nvarchar( 100) = CONVERT( nvarchar( 100) , @splitdate , 121);  
      DECLARE @sql nvarchar( 1000) = N'alter table dbo.SalesOrders_cold_staging   
         add constraint CHK_SalesOrders_cold_staging check (so_date > ''' + @s + ''')';  
      PRINT @sql;  
      EXEC sp_executesql @sql;  
  
      COMMIT;  
END;  
GO  
  
-- insert sample values in the hot table  
INSERT INTO dbo.SalesOrders_hot VALUES(1,SYSDATETIME(), 1);   
GO  
  
INSERT INTO dbo.SalesOrders_hot VALUES(1, SYSDATETIME(), 1);  
GO  
  
INSERT INTO dbo.SalesOrders_hot VALUES(1, SYSDATETIME(), 1);  
GO  
  
-- verify contents of the table  
SELECT *  FROM dbo.SalesOrders;  
GO  
  
-- offload all sales orders to date to cold storage  
DECLARE  @t datetime2 = SYSDATETIME();  
EXEC dbo.usp_SalesOrdersOffloadToCold @t;  
  
-- verify contents of the tables  
SELECT * FROM dbo.SalesOrders;  
GO  
  
-- verify partitions  
SELECT OBJECT_NAME( object_id) , * FROM sys.dm_db_partition_stats ps  
   WHERE object_id = OBJECT_ID( 'dbo.SalesOrders_cold');  
  
-- insert more rows in the hot table  
INSERT INTO dbo.SalesOrders_hot VALUES(2, SYSDATETIME(), 1);  
GO  
  
INSERT INTO dbo.SalesOrders_hot VALUES(2, SYSDATETIME(), 1);  
GO  
  
INSERT INTO dbo.SalesOrders_hot VALUES(2, SYSDATETIME(), 1);  
GO  
  
-- verify contents of the tables  
SELECT * FROM dbo.SalesOrders;  
GO  
  
-- offload all sales orders to date to cold storage  
DECLARE @t datetime2 = SYSDATETIME();  
EXEC dbo.usp_SalesOrdersOffloadToCold @t;  
  
-- verify contents of the tables  
SELECT * FROM dbo.SalesOrders;  
GO  
  
-- verify partitions  
SELECT OBJECT_NAME( object_id) , partition_number , row_count  FROM sys.dm_db_partition_stats ps  
  WHERE object_id = OBJECT_ID( 'dbo.SalesOrders_cold') AND index_id = 1;  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bbcd-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bbcd-124">See Also</span></span>  
 [<span data-ttu-id="1bbcd-125">記憶體最佳化資料表</span><span class="sxs-lookup"><span data-stu-id="1bbcd-125">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
