---
title: 記憶體優化資料表變數 |Microsoft Docs
ms.custom: ''
ms.date: 07/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: bd102e95-53e2-4da6-9b8b-0e4f02d286d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: bec720c53c257240ee92274a6391ebc3f17faa25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596881"
---
# <a name="memory-optimized-table-variables"></a><span data-ttu-id="446a5-102">記憶體最佳化資料表變數</span><span class="sxs-lookup"><span data-stu-id="446a5-102">Memory-Optimized Table Variables</span></span>
  <span data-ttu-id="446a5-103">除了記憶體最佳化資料表 (提供高效率的資料存取) 和原生編譯預存程序 (提供高效率的查詢處理和商務邏輯執行) 之外，[!INCLUDE[hek_2](../includes/hek-2-md.md)] 還導入了第三種物件：記憶體最佳化資料表類型。</span><span class="sxs-lookup"><span data-stu-id="446a5-103">In addition to memory-optimized tables (for efficient data access) and natively compiled stored procedures (for efficient query processing and business logic execution) [!INCLUDE[hek_2](../includes/hek-2-md.md)] introduces a third kind of object: the memory-optimized table type.</span></span> <span data-ttu-id="446a5-104">使用記憶體最佳化資料表類型建立的資料表變數，就是記憶體最佳化資料表變數。</span><span class="sxs-lookup"><span data-stu-id="446a5-104">A table variable created using a memory-optimized table type is a memory-optimized table variable.</span></span>  
  
 <span data-ttu-id="446a5-105">與磁碟資料表變數相較之下，記憶體最佳化資料表變數提供了下列幾項優點：</span><span class="sxs-lookup"><span data-stu-id="446a5-105">Memory-optimized table variables offer the following advantages when compared to disk-based table variables:</span></span>  
  
-   <span data-ttu-id="446a5-106">變數只儲存在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="446a5-106">The variables are only stored in memory.</span></span> <span data-ttu-id="446a5-107">資料存取將更有效率，因為記憶體最佳化資料表類型使用的記憶體最佳化演算法和資料結構，與記憶體最佳化資料表所使用的相同，特別是在原生編譯預存程序中使用變數時。</span><span class="sxs-lookup"><span data-stu-id="446a5-107">Data access is more efficient because memory-optimized table type use the same memory-optimized algorithm and data structures used for memory-optimized tables, especially when the variables are used in natively compiled stored procedures.</span></span>  
  
-   <span data-ttu-id="446a5-108">有了記憶體最佳化資料表變數，就不會使用 tempdb。</span><span class="sxs-lookup"><span data-stu-id="446a5-108">With memory-optimized table variables, there is no tempdb utilization.</span></span> <span data-ttu-id="446a5-109">資料表變數不會儲存在 tempdb 中，而且不會使用 tempdb 中的任何資源。</span><span class="sxs-lookup"><span data-stu-id="446a5-109">Table variables are not stored in tempdb and do not use any resources in tempdb.</span></span>  
  
 <span data-ttu-id="446a5-110">記憶體最佳化資料表變數的一般使用案例包括：</span><span class="sxs-lookup"><span data-stu-id="446a5-110">The typical usage scenarios for memory-optimized table variables are:</span></span>  
  
-   <span data-ttu-id="446a5-111">根據原生編譯預存程序中的多個查詢儲存中繼結果並建立單一結果集。</span><span class="sxs-lookup"><span data-stu-id="446a5-111">Storing intermediate results and creating single result sets based on multiple queries in natively compiled stored procedures.</span></span>  
  
-   <span data-ttu-id="446a5-112">將資料表值參數傳遞至原生編譯預存程序和解譯的預存程序中。</span><span class="sxs-lookup"><span data-stu-id="446a5-112">Passing table-valued parameters into natively compiled stored procedures and interpreted stored procedures.</span></span>  
  
-   <span data-ttu-id="446a5-113">取代磁碟資料表變數，以及在某些情況下取代預存程序的本機 #temp 資料表。</span><span class="sxs-lookup"><span data-stu-id="446a5-113">Replacing disk-based table variables, and in some cases #temp tables that are local to a stored procedure.</span></span> <span data-ttu-id="446a5-114">如果系統中有大量 tempdb 競爭，這就會特別有用。</span><span class="sxs-lookup"><span data-stu-id="446a5-114">This is particularly useful if there is a lot of tempdb contention in the system.</span></span>  
  
-   <span data-ttu-id="446a5-115">資料表變數可用來模擬以原生方式編譯之預存程序中的資料指標，這樣可協助您在以原生方式編譯的預存程序中避開介面區限制。</span><span class="sxs-lookup"><span data-stu-id="446a5-115">Table variables can be used to simulate cursors in natively compiled stored procedures, which can help you work around surface area limitations in natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="446a5-116">就像記憶體最佳化資料表一樣， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會為每個記憶體最佳化資料表類型產生 DLL</span><span class="sxs-lookup"><span data-stu-id="446a5-116">Like memory-optimized tables, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] generates a DLL for each memory-optimized table type.</span></span> <span data-ttu-id="446a5-117">當建立記憶體優化資料表類型時，會叫用 (編譯，而不是在用來建立記憶體優化資料表變數時叫用。 ) 此 DLL 包含用來存取索引和從資料表變數中抓取資料的函數。</span><span class="sxs-lookup"><span data-stu-id="446a5-117">(Compilation is invoked when the memory-optimized table type is created and not when used to create memory-optimized table variables.) This DLL includes the functions for accessing indexes and retrieving data from the table variables.</span></span> <span data-ttu-id="446a5-118">根據資料表類型宣告記憶體最佳化資料表變數時，會在使用者工作階段中建立對應至資料表類型之資料表和索引結構的執行個體。</span><span class="sxs-lookup"><span data-stu-id="446a5-118">When a memory-optimized table variable is declared based on the table type, an instance of the table and index structures corresponding to the table type is created in the user session.</span></span> <span data-ttu-id="446a5-119">接著就可以透過與磁碟資料表變數相同的方式使用資料表變數。</span><span class="sxs-lookup"><span data-stu-id="446a5-119">The table variable can then be used in the same way as disk-based table variables.</span></span> <span data-ttu-id="446a5-120">您可以在資料表變數中插入、更新及刪除資料列，也可以在 [!INCLUDE[tsql](../includes/tsql-md.md)] 查詢中使用變數。</span><span class="sxs-lookup"><span data-stu-id="446a5-120">You can insert, update, and delete rows in the table variable, and you can use the variables in [!INCLUDE[tsql](../includes/tsql-md.md)] queries.</span></span> <span data-ttu-id="446a5-121">您也可以將變數當做資料表值參數 (TVP) 傳遞至以原生方式編譯和解譯的預存程序中。</span><span class="sxs-lookup"><span data-stu-id="446a5-121">You can also pass the variables into natively compiled and interpreted stored procedures, as table-valued parameters (TVP).</span></span>  
  
 <span data-ttu-id="446a5-122">下列範例顯示 AdventureWorks 型記憶體內部 OLTP 範例中的記憶體優化資料表類型 ([SQL Server 2014 記憶體內部 Oltp 範例](https://msftdbprodsamples.codeplex.com/releases/view/114491)) 。</span><span class="sxs-lookup"><span data-stu-id="446a5-122">The following sample shows a memory-optimized table type from the AdventureWorks-based In-Memory OLTP sample ([SQL Server 2014 In-Memory OLTP Sample](https://msftdbprodsamples.codeplex.com/releases/view/114491)).</span></span>  
  
```sql
CREATE TYPE Sales.SalesOrderDetailType_inmem
   AS TABLE
(
   OrderQty         smallint   NOT NULL,
   ProductID        int        NOT NULL,

   SpecialOfferID   int        NOT NULL
      INDEX  IX_SpecialOfferID  NONCLUSTERED,

   LocalID          int        NOT NULL,

   INDEX IX_ProductID HASH (ProductID)
      WITH ( BUCKET_COUNT = 8 )
)
WITH ( MEMORY_OPTIMIZED = ON );
```  
  
 <span data-ttu-id="446a5-123">此範例顯示，記憶體最佳化資料表類型的語法類似於磁碟資料表類型，但是有下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="446a5-123">The sample shows that the syntax of memory-optimized table types is similar to disk-based table types, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="446a5-124">`MEMORY_OPTIMIZED=ON` 指出資料表類型為記憶體最佳化。</span><span class="sxs-lookup"><span data-stu-id="446a5-124">`MEMORY_OPTIMIZED=ON` indicates that the table type is memory-optimized.</span></span>  
  
-   <span data-ttu-id="446a5-125">類型必須至少有一個索引。</span><span class="sxs-lookup"><span data-stu-id="446a5-125">The type must have at least one index.</span></span> <span data-ttu-id="446a5-126">就像在記憶體最佳化資料表中，您可以使用雜湊和非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="446a5-126">As with memory-optimized tables, you can use hash and nonclustered indexes.</span></span>  
  
     <span data-ttu-id="446a5-127">若是雜湊索引，值區計數應該約為預期的唯一索引鍵數目的一倍到兩倍。</span><span class="sxs-lookup"><span data-stu-id="446a5-127">For a hash index, the bucket count should be about one to two times the number of expected unique index keys.</span></span> <span data-ttu-id="446a5-128">如需詳細資訊，請參閱＜ [Determining the Correct Bucket Count for Hash Indexes](../relational-databases/indexes/indexes.md)＞。</span><span class="sxs-lookup"><span data-stu-id="446a5-128">For more information, see [Determining the Correct Bucket Count for Hash Indexes](../relational-databases/indexes/indexes.md).</span></span>  
  
-   <span data-ttu-id="446a5-129">對於記憶體最佳化資料表的資料類型和條件約束限制也適用於記憶體最佳化資料表類型。</span><span class="sxs-lookup"><span data-stu-id="446a5-129">The data type and constraint restrictions on memory-optimized tables also apply to memory-optimized table types.</span></span> <span data-ttu-id="446a5-130">例如，[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 支援預設條件約束，但是不支援檢查條件約束。</span><span class="sxs-lookup"><span data-stu-id="446a5-130">For example, in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] default constraints are supported, but check constraints are not.</span></span>  
  
 <span data-ttu-id="446a5-131">就像記憶體最佳化資料表，記憶體最佳化資料表變數</span><span class="sxs-lookup"><span data-stu-id="446a5-131">Like memory-optimized tables, memory-optimized table variables,</span></span>  
  
-   <span data-ttu-id="446a5-132">不支援平行計畫。</span><span class="sxs-lookup"><span data-stu-id="446a5-132">Do not support parallel plans.</span></span>  
  
-   <span data-ttu-id="446a5-133">必須納入記憶體中，且不使用磁碟資源。</span><span class="sxs-lookup"><span data-stu-id="446a5-133">Must fit in memory and do not use disk resources.</span></span>  
  
 <span data-ttu-id="446a5-134">磁碟資料表變數存在於 tempdb 中。</span><span class="sxs-lookup"><span data-stu-id="446a5-134">Disk-based table variables exist in tempdb.</span></span> <span data-ttu-id="446a5-135">記憶體最佳化資料表變數存在使用者資料庫中 (但是不會耗用儲存體，也不會復原)。</span><span class="sxs-lookup"><span data-stu-id="446a5-135">Memory-optimized table variables exist in the user database (but they do not consume storage and are not recovered).</span></span>  
  
 <span data-ttu-id="446a5-136">您無法使用內嵌語法建立記憶體最佳化資料表變數。</span><span class="sxs-lookup"><span data-stu-id="446a5-136">You cannot create a memory-optimized table variable using in-line syntax.</span></span> <span data-ttu-id="446a5-137">與磁碟資料表變數不同的是，您必須先建立類型。</span><span class="sxs-lookup"><span data-stu-id="446a5-137">Unlike disk-based table variables, you must create a type first.</span></span>  
  
## <a name="table-valued-parameters"></a><span data-ttu-id="446a5-138">資料表值參數</span><span class="sxs-lookup"><span data-stu-id="446a5-138">Table-Valued Parameters</span></span>  
 <span data-ttu-id="446a5-139">下列範例指令碼示範如何將資料表變數宣告為記憶體最佳化資料表類型 `Sales.SalesOrderDetailType_inmem`、將三個資料列插入變數中，以及將變數當做 TVP 傳遞至 `Sales.usp_InsertSalesOrder_inmem` 中。</span><span class="sxs-lookup"><span data-stu-id="446a5-139">The following sample script shows the declaration of a table variable as the memory-optimized table type `Sales.SalesOrderDetailType_inmem`, the insert of three rows into the variable, and passing the variable as a TVP into `Sales.usp_InsertSalesOrder_inmem`.</span></span>  
  
```sql  
DECLARE @od Sales.SalesOrderDetailType_inmem,  
  @SalesOrderID uniqueidentifier,  
  @DueDate datetime2 = SYSDATETIME()  
  
INSERT @od (LocalID, ProductID, OrderQty, SpecialOfferID) VALUES  
  (1, 888, 2, 1),  
  (2, 450, 13, 1),  
  (3, 841, 1, 1)  
  
EXEC Sales.usp_InsertSalesOrder_inmem  
  @SalesOrderID = @SalesOrderID,  
  @DueDate = @DueDate,  
 @OnlineOrderFlag = 1,  
  @SalesOrderDetails = @od  
```  
  
 <span data-ttu-id="446a5-140">記憶體最佳化資料表類型可以做為預存程序資料表值參數 (TVP) 的類型使用，並且可以供用戶端參考，與磁碟資料表類型和 TVP 完全相同。</span><span class="sxs-lookup"><span data-stu-id="446a5-140">Memory-optimized table types can be used as the type for stored procedure table-valued parameters (TVPs) and can be referenced by clients exactly the same as disk-based table types and TVPs.</span></span> <span data-ttu-id="446a5-141">因此，採用記憶體最佳化 TVP 之預存程序和原生方式編譯之預存程序的引動過程，與採用磁碟 TVP 之解譯預存程序的引動過程完全相同。</span><span class="sxs-lookup"><span data-stu-id="446a5-141">Therefore, the invocation of stored procedures with memory-optimized TVPs, and natively compiled stored procedures works exactly the same as the invocation of interpreted stored procedures with disk-based TVPs.</span></span>  
  
## <a name="temp-table-replacement"></a><span data-ttu-id="446a5-142">取代 #temp 資料表</span><span class="sxs-lookup"><span data-stu-id="446a5-142">#temp Table Replacement</span></span>  
 <span data-ttu-id="446a5-143">下列範例將示範記憶體最佳化資料表類型和資料表變數，做為預存程序之本機 #temp 資料表的替代方式。</span><span class="sxs-lookup"><span data-stu-id="446a5-143">The following sample shows memory-optimized table types and table variables as a replacement for #temp tables that are local to a stored procedure.</span></span>  
  
```sql  
-- Using SQL procedure and temp table  
CREATE TABLE #tempTable (c INT NOT NULL PRIMARY KEY NONCLUSTERED)  
  
CREATE PROCEDURE sqlProc  
AS  
BEGIN  
  TRUNCATE TABLE #tempTable  
  
  INSERT #tempTable VALUES (1)  
  INSERT #tempTable VALUES (2)  
  INSERT #tempTable VALUES (3)  
  SELECT * FROM #tempTable  
END  
GO  
  
-- Using natively compiled stored procedure and table variable  
CREATE TYPE TT AS TABLE (c INT NOT NULL PRIMARY KEY NONCLUSTERED)  
GO  
  
CREATE PROCEDURE NCSPProc  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
  DECLARE @tableVariable TT  
  INSERT @tableVariable VALUES (1)  
  INSERT @tableVariable VALUES (2)  
  INSERT @tableVariable VALUES (3)  
  SELECT c FROM @tableVariable  
END  
GO  
```  
  
## <a name="creating-a-single-result-set"></a><span data-ttu-id="446a5-144">建立單一結果集</span><span class="sxs-lookup"><span data-stu-id="446a5-144">Creating a Single Result Set</span></span>  
 <span data-ttu-id="446a5-145">下列範例將示範如何根據原生編譯預存程序中的多個查詢儲存中繼結果並建立單一結果集。</span><span class="sxs-lookup"><span data-stu-id="446a5-145">The following sample shows how to store intermediate results and create single result sets based on multiple queries in natively compiled stored procedures.</span></span> <span data-ttu-id="446a5-146">此範例將計算聯集 `SELECT c1 FROM dbo.t1 UNION SELECT c1 FROM dbo.t2`。</span><span class="sxs-lookup"><span data-stu-id="446a5-146">The sample is computing the union `SELECT c1 FROM dbo.t1 UNION SELECT c1 FROM dbo.t2`.</span></span>  
  
```sql  
CREATE DATABASE hk  
GO  
ALTER DATABASE hk ADD FILEGROUP hk_mod CONTAINS MEMORY_OPTIMIZED_DATA  
ALTER DATABASE hk ADD FILE( NAME = 'hk_mod' , FILENAME = 'c:\data\hk_mod') TO FILEGROUP hk_mod;  
  
USE hk  
GO  
  
CREATE TYPE tab1 AS TABLE (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON)  
  
CREATE TABLE dbo.t1 (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
CREATE TABLE dbo.t2 (c1 INT NOT NULL, INDEX idx NONCLUSTERED(c1)) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
  
INSERT INTO dbo.t1 VALUES (1), (2)  
INSERT INTO dbo.t2 VALUES (3), (4)  
GO  
  
CREATE PROCEDURE dbo.p1  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
  AS  
  BEGIN ATOMIC WITH ( TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english' )  
  
    DECLARE @t dbo.tab1  
    INSERT @t (c1)  
    SELECT c1 FROM dbo.t1;  
  
    INSERT @t (c1)  
    SELECT c1 FROM dbo.t2;  
  
    SELECT c1 FROM @t;  
  END  
GO  
  
EXEC dbo.p1  
GO  
```  
  
## <a name="memory-consumption-for-table-variables"></a><span data-ttu-id="446a5-147">資料表變數的記憶體耗用量</span><span class="sxs-lookup"><span data-stu-id="446a5-147">Memory Consumption for Table Variables</span></span>  
 <span data-ttu-id="446a5-148">資料表變數的記憶體耗用量類似於記憶體最佳化的資料表，但有非叢集索引的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="446a5-148">Memory consumption for table variables is similar to memory-optimized tables, with the exception of nonclustered indexes.</span></span> <span data-ttu-id="446a5-149">如果您將大量資料列插入含有非叢集索引的記憶體最佳化資料表變數中，而且如果索引鍵很大，這些資料表變數將會使用不成比例的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="446a5-149">If you insert a lot of rows into memory-optimized table variables with nonclustered indexes and if the index keys are large, these table variables will use a disproportionate amount of memory.</span></span> <span data-ttu-id="446a5-150">對於在資料表中插入相同數目的資料列而言，大型資料表變數上的非叢集索引比單一非叢集索引在比例上需要更多記憶體 (索引頁中需要更多記憶體)。</span><span class="sxs-lookup"><span data-stu-id="446a5-150">Nonclustered indexes on large table variables require proportionately more memory than a nonclustered index would require for the same number of rows inserted into a table (more memory in the index pages).</span></span>  
  
 <span data-ttu-id="446a5-151">資料表變數的記憶體來自資料庫的資源管理員資源集區。</span><span class="sxs-lookup"><span data-stu-id="446a5-151">Memory for table variables comes from the database's Resource Governor resource pool.</span></span>  
  
 <span data-ttu-id="446a5-152">與記憶體最佳化的資料表不同，當資料表變數脫離範圍時，會釋出資料表變數所耗用的記憶體 (包括已刪除的資料列)。</span><span class="sxs-lookup"><span data-stu-id="446a5-152">Unlike memory-optimized tables, the memory consumed (including deleted rows) by table variables is freed when the table variable goes out of scope.</span></span>  
  
 <span data-ttu-id="446a5-153">屬於資料庫的單一 PGPOOL 記憶體取用者時，才會計算記憶體。</span><span class="sxs-lookup"><span data-stu-id="446a5-153">Memory is accounted for as part of the single PGPOOL memory consumer of the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="446a5-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="446a5-154">See Also</span></span>  
 [<span data-ttu-id="446a5-155">記憶體內部 OLTP 的 Transact-SQL 支援</span><span class="sxs-lookup"><span data-stu-id="446a5-155">Transact-SQL Support for In-Memory OLTP</span></span>](../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)  
  
  
