---
title: 示範：記憶體內部 OLTP 的效能改善 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c6def45d-d2d4-4d24-8068-fab4cd94d8cc
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4858e4c35263ab3dd1d9fdcf55a2b136dd8eeaf2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595982"
---
# <a name="demonstration-performance-improvement-of-in-memory-oltp"></a><span data-ttu-id="75db1-102">示範：記憶體內部 OLTP 的效能改善</span><span class="sxs-lookup"><span data-stu-id="75db1-102">Demonstration: Performance Improvement of In-Memory OLTP</span></span>
  <span data-ttu-id="75db1-103">此範例說明使用記憶體中 OLTP 時的效能改進，方法是比較對記憶體最佳化和傳統以磁碟為基礎的資料表執行相同的 Transact-SQL 查詢時，兩者的回應時間有何差異。</span><span class="sxs-lookup"><span data-stu-id="75db1-103">This example shows performance improvements when using In-Memory OLTP by comparing differences in response times when running an identical Transact-SQL query against memory-optimized and traditional disk-based tables.</span></span> <span data-ttu-id="75db1-104">此外也會建立原生編譯的預存程序 (根據相同的查詢)，然後執行以示範您通常在使用原生編譯的預存程序來查詢記憶體最佳化資料表時，可獲得最佳的回應時間。</span><span class="sxs-lookup"><span data-stu-id="75db1-104">Additionally, a natively-compiled stored procedure is also created (based on the same query) and then run to demonstrate that you typically get the best response times when querying a memory-optimized table with a natively-compiled stored procedure.</span></span> <span data-ttu-id="75db1-105">此範例僅顯示在記憶體最佳化資料表中存取資料時的其中一個效能改進層面；即執行插入時的資料存取效率。</span><span class="sxs-lookup"><span data-stu-id="75db1-105">This sample only shows one aspect of performance improvements when accessing data in memory-optimized tables; data access efficiency when performing inserts.</span></span> <span data-ttu-id="75db1-106">此範例為單一執行緒且未利用記憶體中 OLTP 的並行優點。</span><span class="sxs-lookup"><span data-stu-id="75db1-106">This sample is single-threaded and does not take advantage of the concurrency benefits of In-Memory OLTP.</span></span> <span data-ttu-id="75db1-107">工作負載若是使用並行作業，將會有更高幅度的效能提升。</span><span class="sxs-lookup"><span data-stu-id="75db1-107">A workload that uses concurrency will see a greater performance gain.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75db1-108">另一個示範記憶體最佳化資料表的範例可從 [SQL Server 2014 記憶體中 OLTP 範例](https://msftdbprodsamples.codeplex.com/releases/view/114491)取得。</span><span class="sxs-lookup"><span data-stu-id="75db1-108">Another sample demonstrating memory-optimized tables is available at [SQL Server 2014 In-Memory OLTP Sample](https://msftdbprodsamples.codeplex.com/releases/view/114491).</span></span>  
  
 <span data-ttu-id="75db1-109">若要完成此範例，您將執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="75db1-109">To complete this sample you will perform the following:</span></span>  
  
1.  <span data-ttu-id="75db1-110">建立名為 **imoltp** 的資料庫，並變更其檔案詳細資料，以便將它設定為使用記憶體中 OLTP。</span><span class="sxs-lookup"><span data-stu-id="75db1-110">Create a database named **imoltp** and alter its file details to set it up for using In-Memory OLTP.</span></span>  
  
2.  <span data-ttu-id="75db1-111">建立範例的資料庫物件：三個資料表和原生編譯的預存程序。</span><span class="sxs-lookup"><span data-stu-id="75db1-111">Create the database objects for our sample: three tables and a natively-compiled stored procedure.</span></span>  
  
3.  <span data-ttu-id="75db1-112">執行不同的查詢，並顯示每個查詢的回應時間。</span><span class="sxs-lookup"><span data-stu-id="75db1-112">Run the different queries and display the response times for each query.</span></span>  
  
 <span data-ttu-id="75db1-113">若要設定範例的 **imoltp** 資料庫，請先建立空的資料夾 **c:\imoltp_data**，然後執行下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="75db1-113">To setup the **imoltp** database for our example, first create an empty folder: **c:\imoltp_data**, and then run the following code:</span></span>  
  
```sql  
USE master  
GO  
  
-- Create a new database.  
CREATE DATABASE imoltp  
GO  
  
-- Prepare the database for In-Memory OLTP by  
-- adding a memory-optimized filegroup to the database.  
ALTER DATABASE imoltp ADD FILEGROUP imoltp_file_group  
    CONTAINS MEMORY_OPTIMIZED_DATA;  
  
-- Add a file (to hold the memory-optimized data) to the new filegroup.  
ALTER DATABASE imoltp ADD FILE (name='imoltp_file', filename='c:\imoltp_data\imoltp_file')  
    TO FILEGROUP imoltp_file_group;  
GO  
  
```  
  
 <span data-ttu-id="75db1-114">接下來，執行下列程式碼以建立以磁碟為基礎的資料表、兩個 (2) 記憶體最佳化資料表，和將用來示範不同資料存取方法的原生編譯預存程序：</span><span class="sxs-lookup"><span data-stu-id="75db1-114">Next, run the following code to create the disk-based table, two (2) memory-optimized tables, and the natively-compiled stored procedure that will be used to demonstrate the different data access methods:</span></span>  
  
```sql  
USE imoltp  
GO  
  
-- If the tables or stored procedure already exist, drop them to start clean.  
IF EXISTS (SELECT NAME FROM sys.objects WHERE NAME = 'DiskBasedTable')  
   DROP TABLE [dbo].[DiskBasedTable]  
GO  
  
IF EXISTS (SELECT NAME FROM sys.objects WHERE NAME = 'InMemTable')  
   DROP TABLE [dbo].[InMemTable]  
GO  
  
IF EXISTS (SELECT NAME FROM sys.objects  WHERE NAME = 'InMemTable2')  
   DROP TABLE [dbo].[InMemTable2]  
GO  
  
IF EXISTS (SELECT NAME FROM sys.objects  WHERE NAME = 'usp_InsertData')  
   DROP PROCEDURE [dbo].[usp_InsertData]  
GO  
  
-- Create a traditional disk-based table.  
CREATE TABLE [dbo].[DiskBasedTable] (  
  c1 INT NOT NULL PRIMARY KEY,  
  c2 NCHAR(48) NOT NULL  
)  
GO  
  
-- Create a memory-optimized table.  
CREATE TABLE [dbo].[InMemTable] (  
  c1 INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000),  
  c2 NCHAR(48) NOT NULL  
) WITH (MEMORY_OPTIMIZED=ON, DURABILITY = SCHEMA_AND_DATA);  
GO  
  
-- Create a 2nd memory-optimized table.  
CREATE TABLE [dbo].[InMemTable2] (  
  c1 INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000),  
  c2 NCHAR(48) NOT NULL  
) WITH (MEMORY_OPTIMIZED=ON, DURABILITY = SCHEMA_AND_DATA);  
GO  
  
-- Create a natively-compiled stored procedure.  
CREATE PROCEDURE [dbo].[usp_InsertData]   
  @rowcount INT,  
  @c NCHAR(48)  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
  AS   
  BEGIN ATOMIC   
  WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
  DECLARE @i INT = 1;  
  WHILE @i <= @rowcount  
  BEGIN  
    INSERT INTO [dbo].[inMemTable2](c1,c2) VALUES (@i, @c);  
    SET @i += 1;  
  END  
END  
GO  
  
```  
  
 <span data-ttu-id="75db1-115">設定完成後，我們即可執行查詢，以顯示回應時間來比較資料存取方法的效能。</span><span class="sxs-lookup"><span data-stu-id="75db1-115">The setup is complete and we are ready to execute the queries that will display the response times comparing the performance between the data access methods.</span></span>  
  
 <span data-ttu-id="75db1-116">若要完成範例，請執行下列程式碼多次。</span><span class="sxs-lookup"><span data-stu-id="75db1-116">To complete the example run the following code multiple times.</span></span> <span data-ttu-id="75db1-117">請忽略第一次執行的結果，因為此結果受到初始記憶體配置的負面影響。</span><span class="sxs-lookup"><span data-stu-id="75db1-117">Ignore the results from the first run which is negatively affected by initial memory allocation.</span></span>  
  
```sql  
SET STATISTICS TIME OFF;  
SET NOCOUNT ON;  
  
-- Delete data from all tables to reset the example.  
DELETE FROM [dbo].[DiskBasedTable]   
    WHERE [c1]>0  
GO  
DELETE FROM [dbo].[inMemTable]   
    WHERE [c1]>0  
GO  
DELETE FROM [dbo].[InMemTable2]   
    WHERE [c1]>0  
GO  
  
-- Declare parameters for the test queries.  
DECLARE @i INT = 1;  
DECLARE @rowcount INT = 100000;  
DECLARE @c NCHAR(48) = N'12345678901234567890123456789012345678';  
DECLARE @timems INT;  
DECLARE @starttime datetime2 = sysdatetime();  
  
-- Disk-based table queried with interpreted Transact-SQL.  
BEGIN TRAN  
  WHILE @I <= @rowcount  
  BEGIN  
    INSERT INTO [dbo].[DiskBasedTable](c1,c2) VALUES (@i, @c);  
    SET @i += 1;  
  END  
COMMIT  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT CAST(@timems AS VARCHAR(10)) + ' ms (disk-based table with interpreted Transact-SQL).';  
  
-- Memory-optimized table queried with interpreted Transact-SQL.  
SET @i = 1;  
SET @starttime = sysdatetime();  
  
BEGIN TRAN  
  WHILE @i <= @rowcount  
    BEGIN  
      INSERT INTO [dbo].[InMemTable](c1,c2) VALUES (@i, @c);  
      SET @i += 1;  
    END  
COMMIT  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT CAST(@timems AS VARCHAR(10)) + ' ms (memory-optimized table with interpreted Transact-SQL).';  
  
-- Memory-optimized table queried with a natively-compiled stored procedure.  
SET @starttime = sysdatetime();  
  
EXEC usp_InsertData @rowcount, @c;  
  
SET @timems = datediff(ms, @starttime, sysdatetime());  
SELECT CAST(@timems AS VARCHAR(10)) + ' ms (memory-optimized table with natively-compiled stored procedure).';  
  
```  
  
 <span data-ttu-id="75db1-118">預期的結果會提供實際的回應時間，顯示使用記憶體最佳化資料表和原生編譯的預存程序，為何通常在回應時間上都可優於針對傳統以磁碟為基礎的資料表執行相同的工作負載。</span><span class="sxs-lookup"><span data-stu-id="75db1-118">The expected results provide actual response times showing how using memory-optimized tables and natively-compiled stored procedures typically provides consistently faster response times than the same workloads running against traditional disk-based tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75db1-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75db1-119">See Also</span></span>  
 <span data-ttu-id="75db1-120">[示範記憶體內部 OLTP 的 AdventureWorks 擴充功能](../../database-engine/extensions-to-adventureworks-to-demonstrate-in-memory-oltp.md) </span><span class="sxs-lookup"><span data-stu-id="75db1-120">[Extensions to AdventureWorks to Demonstrate In-Memory OLTP](../../database-engine/extensions-to-adventureworks-to-demonstrate-in-memory-oltp.md) </span></span>  
 <span data-ttu-id="75db1-121">[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](in-memory-oltp-in-memory-optimization.md) </span><span class="sxs-lookup"><span data-stu-id="75db1-121">[In-Memory OLTP &#40;In-Memory Optimization&#41;](in-memory-oltp-in-memory-optimization.md) </span></span>  
 <span data-ttu-id="75db1-122">[記憶體優化資料表](memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="75db1-122">[Memory-Optimized Tables](memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="75db1-123">[原生編譯的預存程序](natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="75db1-123">[Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md) </span></span>  
 <span data-ttu-id="75db1-124">[使用記憶體最佳化資料表的需求](requirements-for-using-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="75db1-124">[Requirements for Using Memory-Optimized Tables](requirements-for-using-memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="75db1-125">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="75db1-125">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="75db1-126">[ALTER DATABASE 檔案及檔案群組選項 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) </span><span class="sxs-lookup"><span data-stu-id="75db1-126">[ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) </span></span>  
 [<span data-ttu-id="75db1-127">建立程式和記憶體優化資料表</span><span class="sxs-lookup"><span data-stu-id="75db1-127">CREATE PROCEDURE and Memory-Optimized Tables</span></span>](/sql/t-sql/statements/create-procedure-transact-sql)  
  
  
