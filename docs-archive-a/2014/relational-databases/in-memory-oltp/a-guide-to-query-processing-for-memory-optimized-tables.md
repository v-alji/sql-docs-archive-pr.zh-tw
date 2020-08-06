---
title: 記憶體最佳化資料表的查詢處理指南 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 065296fe-6711-4837-965e-252ef6c13a0f
author: rothja
ms.author: jroth
ms.openlocfilehash: 93489e5dea295964826005e081bcffe889cb7586
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598876"
---
# <a name="a-guide-to-query-processing-for-memory-optimized-tables"></a><span data-ttu-id="1ae8f-102">記憶體最佳化資料表的查詢處理指南</span><span class="sxs-lookup"><span data-stu-id="1ae8f-102">A Guide to Query Processing for Memory-Optimized Tables</span></span>
  <span data-ttu-id="1ae8f-103">記憶體中 OLTP 推出記憶體最佳化資料表以及 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中的原生編譯預存程序。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-103">In-Memory OLTP introduces memory-optimized tables and natively compiled stored procedures in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1ae8f-104">本文針對記憶體最佳化資料表和原生編譯的預存程序提供查詢處理的概觀。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-104">This article gives an overview of query processing for both memory-optimized tables and natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="1ae8f-105">本文件說明如何編譯和執行記憶體最佳化資料表上的查詢，包含：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-105">The document explains how queries on memory-optimized tables are compiled and executed, including:</span></span>  
  
-   <span data-ttu-id="1ae8f-106">對於磁碟基礎的資料表， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的查詢處理管線。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-106">The query processing pipeline in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for disk-based tables.</span></span>  
  
-   <span data-ttu-id="1ae8f-107">查詢最佳化；統計資料在記憶體最佳化資料表上的角色，以及對不正確的查詢計劃進行疑難排解的方針。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-107">Query optimization; the role of statistics on memory-optimized tables as well as guidelines for troubleshooting bad query plans.</span></span>  
  
-   <span data-ttu-id="1ae8f-108">使用解譯的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 以存取記憶體最佳化資料表。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-108">The use of interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] to access memory-optimized tables.</span></span>  
  
-   <span data-ttu-id="1ae8f-109">有關記憶體最佳化資料表存取之查詢最佳化的考量。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-109">Considerations about query optimization for memory-optimized table access.</span></span>  
  
-   <span data-ttu-id="1ae8f-110">原生編譯預存程序編譯和處理。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-110">Natively compiled stored procedure compilation and processing.</span></span>  
  
-   <span data-ttu-id="1ae8f-111">最佳化工具用於估計成本的統計資料。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-111">Statistics that are used for cost estimation by the optimizer.</span></span>  
  
-   <span data-ttu-id="1ae8f-112">修正不正確查詢計劃的方式。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-112">Ways to fix bad query plans.</span></span>  
  
## <a name="example-query"></a><span data-ttu-id="1ae8f-113">範例查詢</span><span class="sxs-lookup"><span data-stu-id="1ae8f-113">Example Query</span></span>  
 <span data-ttu-id="1ae8f-114">下列範例將用來說明本文中所討論的查詢處理概念。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-114">The following example will be used to illustrate the query processing concepts discussed in this article.</span></span>  
  
 <span data-ttu-id="1ae8f-115">我們假設兩個資料表 Customer 和 Order。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-115">We consider two tables, Customer and Order.</span></span> <span data-ttu-id="1ae8f-116">下列 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 指令碼包含這兩個資料表與相關聯索引的定義 (以磁碟為基礎 (傳統) 的格式)：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-116">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] script contains the definitions for these two tables and associated indexes, in their (traditional) disk-based form:</span></span>  
  
```sql  
CREATE TABLE dbo.[Customer] (  
  CustomerID nchar (5) NOT NULL PRIMARY KEY,  
  ContactName nvarchar (30) NOT NULL   
)  
GO  
  
CREATE TABLE dbo.[Order] (  
  OrderID int NOT NULL PRIMARY KEY,  
  CustomerID nchar (5) NOT NULL,  
  OrderDate date NOT NULL  
)  
GO  
CREATE INDEX IX_CustomerID ON dbo.[Order](CustomerID)  
GO  
CREATE INDEX IX_OrderDate ON dbo.[Order](OrderDate)  
GO  
```  
  
 <span data-ttu-id="1ae8f-117">為了建構本文中所顯示的查詢計劃，這兩個資料表中已填入 Northwind 範例資料庫中的範例資料，您可以從 [Northwind and pubs Sample Databases for SQL Server 2000](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)(SQL Server 2000 的 Northwind 和 pubs 範例資料庫) 下載該資料庫。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-117">For constructing the query plans shown in this article, the two tables were populated with sample data from the Northwind sample database, which you can download from [Northwind and pubs Sample Databases for SQL Server 2000](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>  
  
 <span data-ttu-id="1ae8f-118">請看下列查詢，其中聯結了 Customer 和 Order 這兩個資料表，並且會傳回訂單識別碼和相關聯的客戶資訊：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-118">Consider the following query, which joins the tables Customer and Order and returns the ID of the order and the associated customer information:</span></span>  
  
```sql  
SELECT o.OrderID, c.* FROM dbo.[Customer] c INNER JOIN dbo.[Order] o ON c.CustomerID = o.CustomerID  
```  
  
 <span data-ttu-id="1ae8f-119">執行計畫大致如下面的 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 所示</span><span class="sxs-lookup"><span data-stu-id="1ae8f-119">The estimated execution plan as displayed by [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] is as follows</span></span>  
  
 <span data-ttu-id="1ae8f-120">![聯結磁碟為基礎資料表的查詢計劃。](../../database-engine/media/hekaton-query-plan-1.gif "聯結磁碟為基礎資料表的查詢計劃。")</span><span class="sxs-lookup"><span data-stu-id="1ae8f-120">![Query plan for join of disk-based tables.](../../database-engine/media/hekaton-query-plan-1.gif "Query plan for join of disk-based tables.")</span></span>  
<span data-ttu-id="1ae8f-121">聯結磁碟為基礎資料表的查詢計劃。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-121">Query plan for join of disk-based tables.</span></span>  
  
 <span data-ttu-id="1ae8f-122">關於這個查詢計劃：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-122">About this query plan:</span></span>  
  
-   <span data-ttu-id="1ae8f-123">Customer 資料表中的資料列是從叢集索引擷取，這是主要資料結構且擁有完整的資料表資料。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-123">The rows from the Customer table are retrieved from the clustered index, which is the primary data structure and has the full table data.</span></span>  
  
-   <span data-ttu-id="1ae8f-124">來自 Order 資料表的資料，使用 CustomerID 資料行上的非叢集索引擷取得來。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-124">Data from the Order table is retrieved using the nonclustered index on the CustomerID column.</span></span> <span data-ttu-id="1ae8f-125">這個索引同時包含用於聯結的 CustomerID 資料行，以及傳回給使用者的主索引鍵資料行 OrderID。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-125">This index contains both the CustomerID column, which is used for the join, and the primary key column OrderID, which is returned to the user.</span></span> <span data-ttu-id="1ae8f-126">從 Orders 資料表傳回其他資料行會需要查閱 Order 資料表的叢集索引。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-126">Returning additional columns from the Order table would require lookups in the clustered index for the Order table.</span></span>  
  
-   <span data-ttu-id="1ae8f-127">邏輯運算子 `Inner Join` 是由實體運算子 `Merge Join` 所實作。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-127">The logical operator `Inner Join` is implemented by the physical operator `Merge Join`.</span></span> <span data-ttu-id="1ae8f-128">其他實體聯結類型包括 `Nested Loops` 和 `Hash Join`。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-128">The other physical join types are `Nested Loops` and `Hash Join`.</span></span> <span data-ttu-id="1ae8f-129">`Merge Join` 運算子會利用兩個索引都會在聯結資料行 CustomerID 上排序的情況。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-129">The `Merge Join` operator takes advantage of the fact that both indexes are sorted on the join column CustomerID.</span></span>  
  
 <span data-ttu-id="1ae8f-130">請考慮與這個查詢稍微不同的做法，傳回 Order 資料表的所有資料列，而不只是 OrderID：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-130">Consider a slight variation on this query, which returns all rows from the Order table, not only OrderID:</span></span>  
  
```sql  
SELECT o.*, c.* FROM dbo.[Customer] c INNER JOIN dbo.[Order] o ON c.CustomerID = o.CustomerID  
```  
  
 <span data-ttu-id="1ae8f-131">這個查詢的計畫大致如下：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-131">The estimated plan for this query is:</span></span>  
  
 <span data-ttu-id="1ae8f-132">![磁碟為基礎資料表的雜湊聯結查詢計劃。](../../database-engine/media/hekaton-query-plan-2.gif "磁碟為基礎資料表的雜湊聯結查詢計劃。")</span><span class="sxs-lookup"><span data-stu-id="1ae8f-132">![Query plan for a hash join of disk-based tables.](../../database-engine/media/hekaton-query-plan-2.gif "Query plan for a hash join of disk-based tables.")</span></span>  
<span data-ttu-id="1ae8f-133">磁碟為基礎資料表的雜湊聯結查詢計劃。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-133">Query plan for a hash join of disk-based tables.</span></span>  
  
 <span data-ttu-id="1ae8f-134">在這個查詢中，Orders 資料表的資料列是使用叢集索引擷取。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-134">In this query, rows from the Order table are retrieved using the clustered index.</span></span> <span data-ttu-id="1ae8f-135">`Hash Match` 實體運算子現在用於 `Inner Join`。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-135">The `Hash Match` physical operator is now used for the `Inner Join`.</span></span> <span data-ttu-id="1ae8f-136">Order 上的叢集索引不會在 CustomerID 上排序，因此 `Merge Join` 會需要排序運算子，而這樣就會影響效能。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-136">The clustered index on Order is not sorted on CustomerID, and so a `Merge Join` would require a sort operator, which would affect performance.</span></span> <span data-ttu-id="1ae8f-137">請記下與上一個範例中 `Hash Match` 運算子成本 (46%) 相較的 `Merge Join` 運算子相對成本 (75%)。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-137">Note the relative cost of the `Hash Match` operator (75%) compared with the cost of the `Merge Join` operator in the previous example (46%).</span></span> <span data-ttu-id="1ae8f-138">最佳化工具原本也會在上一個範例中考慮 `Hash Match` 運算子，但結果卻是 `Merge Join` 運算子提供更佳效能的結果。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-138">The optimizer would have considered the `Hash Match` operator also in the previous example, but concluded that the `Merge Join` operator gave better performance.</span></span>  
  
## <a name="ssnoversion-query-processing-for-disk-based-tables"></a>[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="1ae8f-139">磁碟資料表的查詢處理</span><span class="sxs-lookup"><span data-stu-id="1ae8f-139">Query Processing for Disk-Based Tables</span></span>  
 <span data-ttu-id="1ae8f-140">下圖概述 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中隨選查詢的查詢處理流程：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-140">The following diagram outlines the query processing flow in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for ad hoc queries:</span></span>  
  
 <span data-ttu-id="1ae8f-141">![SQL Server 查詢處理管線。](../../database-engine/media/hekaton-query-plan-3.gif "SQL Server 查詢處理管線。")</span><span class="sxs-lookup"><span data-stu-id="1ae8f-141">![SQL Server query processing pipeline.](../../database-engine/media/hekaton-query-plan-3.gif "SQL Server query processing pipeline.")</span></span>  
<span data-ttu-id="1ae8f-142">SQL Server 查詢處理管線。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-142">SQL Server query processing pipeline.</span></span>  
  
 <span data-ttu-id="1ae8f-143">在此情節中：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-143">In this scenario:</span></span>  
  
1.  <span data-ttu-id="1ae8f-144">使用者會發出查詢。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-144">The user issues a query.</span></span>  
  
2.  <span data-ttu-id="1ae8f-145">剖析器和 Algebrizer 會利用根據使用者所提交 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 文字的邏輯運算子建構查詢樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-145">The parser and algebrizer construct a query tree with logical operators based on the [!INCLUDE[tsql](../../../includes/tsql-md.md)] text submitted by the user.</span></span>  
  
3.  <span data-ttu-id="1ae8f-146">最佳化工具會建立包含實體運算子 (例如，巢狀迴圈聯結) 的最佳化查詢計劃。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-146">The optimizer creates an optimized query plan containing physical operators (for example, nested-loops join).</span></span> <span data-ttu-id="1ae8f-147">在最佳化之後，計畫可能會儲存到計畫快取中。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-147">After optimization, the plan may be stored in the plan cache.</span></span> <span data-ttu-id="1ae8f-148">如果計畫快取中已包含這個查詢的計畫，則會略過這個步驟。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-148">This step is bypassed if the plan cache already contains a plan for this query.</span></span>  
  
4.  <span data-ttu-id="1ae8f-149">查詢執行引擎會處理查詢計劃的解譯。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-149">The query execution engine processes an interpretation of the query plan.</span></span>  
  
5.  <span data-ttu-id="1ae8f-150">對於每個索引搜尋、索引掃描和資料表掃描運算子，執行引擎都會向 Access Methods 的個別索引和資料表結構要求資料列。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-150">For each index seek, index scan, and table scan operator, the execution engine requests rows from the respective index and table structures from Access Methods.</span></span>  
  
6.  <span data-ttu-id="1ae8f-151">Access Methods 會從緩衝集區中的索引和資料頁面擷取資料列，並且視需要將頁面從磁碟載入至緩衝集區。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-151">Access Methods retrieves the rows from the index and data pages in the buffer pool and loads pages from disk into the buffer pool as needed.</span></span>  
  
 <span data-ttu-id="1ae8f-152">在第一個範例查詢中，執行引擎會從 Access Methods 要求 Customer 上叢集索引中的資料列，以及 Order 上非叢集索引中的資料列。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-152">For the first example query, the execution engine requests rows in the clustered index on Customer and the nonclustered index on Order from Access Methods.</span></span> <span data-ttu-id="1ae8f-153">Access Methods 會周遊 B 型樹狀目錄索引結構，擷取所要求的資料列。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-153">Access Methods traverses the B-tree index structures to retrieve the requested rows.</span></span> <span data-ttu-id="1ae8f-154">在這種情況下，當計畫需要完整索引掃描時，就會擷取所有資料列。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-154">In this case all rows are retrieved as the plan calls for full index scans.</span></span>  
  
## <a name="interpreted-tsql-access-to-memory-optimized-tables"></a><span data-ttu-id="1ae8f-155">對記憶體最佳化資料表進行解譯的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 存取</span><span class="sxs-lookup"><span data-stu-id="1ae8f-155">Interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] Access to Memory-Optimized Tables</span></span>  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="1ae8f-156">隨選批次和預存程序，也稱為解譯的 [!INCLUDE[tsql](../../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-156">ad hoc batches and stored procedures are also referred to as interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="1ae8f-157">解譯是指查詢計劃是由查詢計劃中每個運算子的查詢執行引擎所解譯。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-157">Interpreted refers to the fact that the query plan is interpreted by the query execution engine for each operator in the query plan.</span></span> <span data-ttu-id="1ae8f-158">執行引擎會讀取運算子及其參數，並執行作業。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-158">The execution engine reads the operator and its parameters and performs the operation.</span></span>  
  
 <span data-ttu-id="1ae8f-159">解譯的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 可用來存取記憶體最佳化和磁碟為基礎的資料表。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-159">Interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] can be used to access both memory-optimized and disk-based tables.</span></span> <span data-ttu-id="1ae8f-160">下圖說明對記憶體最佳化資料表進行解譯的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 存取之查詢處理：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-160">The following figure illustrates query processing for interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] access to memory-optimized tables:</span></span>  
  
 <span data-ttu-id="1ae8f-161">![用於解譯之 tsql 的查詢處理管線。](../../database-engine/media/hekaton-query-plan-4.gif "用於解譯 TSQL 的查詢處理管道。")</span><span class="sxs-lookup"><span data-stu-id="1ae8f-161">![Query processing pipeline for interpreted tsql.](../../database-engine/media/hekaton-query-plan-4.gif "Query processing pipeline for interpreted tsql.")</span></span>  
<span data-ttu-id="1ae8f-162">對記憶體最佳化資料表進行解譯的 Transact-SQL 存取之查詢處理管線。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-162">Query processing pipeline for interpreted Transact-SQL access to memory-optimized tables.</span></span>  
  
 <span data-ttu-id="1ae8f-163">如圖中所示，查詢處理管線大致保持不變：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-163">As illustrated by the figure, the query processing pipeline remains mostly unchanged:</span></span>  
  
-   <span data-ttu-id="1ae8f-164">剖析器和 Algebrizer 會建構查詢樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-164">The parser and algebrizer construct the query tree.</span></span>  
  
-   <span data-ttu-id="1ae8f-165">最佳化工具會建立執行計畫。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-165">The optimizer creates the execution plan.</span></span>  
  
-   <span data-ttu-id="1ae8f-166">查詢執行引擎會解譯執行計畫。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-166">The query execution engine interprets the execution plan.</span></span>  
  
 <span data-ttu-id="1ae8f-167">與傳統查詢處理管線的主要差異 (圖 2) 在於，記憶體最佳化資料表的資料列不是使用 Access Methods 從緩衝集區擷取，資料列反而是透過記憶體中 OLTP 引擎從記憶體中的資料結構擷取。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-167">The main difference with the traditional query processing pipeline (figure 2) is that rows for memory-optimized tables are not retrieved from the buffer pool using Access Methods.</span></span> <span data-ttu-id="1ae8f-168">資料列是透過記憶體中 OLTP 引擎從記憶體中的資料結構擷取。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-168">Instead, rows are retrieved from the in-memory data structures through the In-Memory OLTP engine.</span></span> <span data-ttu-id="1ae8f-169">資料結構的差異造成最佳化工具在某些情況下挑選不同的計畫，如下面範例所示。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-169">Differences in data structures cause the optimizer to pick different plans in some cases, as illustrated by the following example.</span></span>  
  
 <span data-ttu-id="1ae8f-170">下列 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 指令碼包含 Order 和 Customer 資料表的記憶體最佳化版本 (使用雜湊索引)：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-170">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] script contains memory-optimized versions of the Order and Customer tables, using hash indexes:</span></span>  
  
```sql  
CREATE TABLE dbo.[Customer] (  
  CustomerID nchar (5) NOT NULL PRIMARY KEY NONCLUSTERED,  
  ContactName nvarchar (30) NOT NULL   
) WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
CREATE TABLE dbo.[Order] (  
  OrderID int NOT NULL PRIMARY KEY NONCLUSTERED,  
  CustomerID nchar (5) NOT NULL INDEX IX_CustomerID HASH(CustomerID) WITH (BUCKET_COUNT=100000),  
  OrderDate date NOT NULL INDEX IX_OrderDate HASH(OrderDate) WITH (BUCKET_COUNT=100000)  
) WITH (MEMORY_OPTIMIZED=ON)  
GO  
```  
  
 <span data-ttu-id="1ae8f-171">請考慮在記憶體最佳化的資料表上執行相同的查詢：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-171">Consider the same query executed on memory-optimized tables:</span></span>  
  
```sql  
SELECT o.OrderID, c.* FROM dbo.[Customer] c INNER JOIN dbo.[Order] o ON c.CustomerID = o.CustomerID  
```  
  
 <span data-ttu-id="1ae8f-172">估計的計畫如下所示：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-172">The estimated plan is as follows:</span></span>  
  
 <span data-ttu-id="1ae8f-173">![聯結記憶體最佳化資料表的查詢計劃。](../../database-engine/media/hekaton-query-plan-5.gif "聯結記憶體最佳化資料表的查詢計劃。")</span><span class="sxs-lookup"><span data-stu-id="1ae8f-173">![Query plan for join of memory optimized tables.](../../database-engine/media/hekaton-query-plan-5.gif "Query plan for join of memory optimized tables.")</span></span>  
<span data-ttu-id="1ae8f-174">聯結記憶體最佳化資料表的查詢計劃。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-174">Query plan for join of memory-optimized tables.</span></span>  
  
 <span data-ttu-id="1ae8f-175">請觀察與磁碟為基礎的資料表 (圖 1) 上相同查詢的下列差異：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-175">Observe the following differences with the plan for the same query on disk-based tables (figure 1):</span></span>  
  
-   <span data-ttu-id="1ae8f-176">這個計畫針對 Customer 資料表適用的資料表掃描，而非叢集索引掃描：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-176">This plan contains a table scan rather than a clustered index scan for the table Customer:</span></span>  
  
    -   <span data-ttu-id="1ae8f-177">資料表定義不包含叢集索引。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-177">The definition of the table does not contain a clustered index.</span></span>  
  
    -   <span data-ttu-id="1ae8f-178">記憶體最佳化資料表不支援叢集索引。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-178">Clustered indexes are not supported with memory-optimized tables.</span></span> <span data-ttu-id="1ae8f-179">不過，每個記憶體最佳化的資料表都必須至少有一個非叢集索引，而且記憶體最佳化資料表上的所有索引均可有效率地存取資料表中的所有資料行，不必將資料行儲存於索引中，或參考叢集的索引。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-179">Instead, every memory-optimized table must have at least one nonclustered index and all indexes on memory-optimized tables can efficiently access all columns in the table without having to store them in the index or refer to a clustered index.</span></span>  
  
-   <span data-ttu-id="1ae8f-180">這個計畫包含 `Hash Match`，而不是 `Merge Join`。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-180">This plan contains a `Hash Match` rather than a `Merge Join`.</span></span> <span data-ttu-id="1ae8f-181">Order 和 Customer 資料表上的索引是雜湊索引，因此未進行排序。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-181">The indexes on both the Order and the Customer table are hash indexes, and are thus not ordered.</span></span> <span data-ttu-id="1ae8f-182">`Merge Join` 會需要排序運算子，而這樣會降低效能。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-182">A `Merge Join` would require sort operators that would decrease performance.</span></span>  
  
## <a name="natively-compiled-stored-procedures"></a><span data-ttu-id="1ae8f-183">原生編譯的預存程序</span><span class="sxs-lookup"><span data-stu-id="1ae8f-183">Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="1ae8f-184">原生編譯的預存程序是編譯成機器碼的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 預存程序，而不是由查詢執行引擎所解譯。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-184">Natively compiled stored procedures are [!INCLUDE[tsql](../../../includes/tsql-md.md)] stored procedures compiled to machine code, rather than interpreted by the query execution engine.</span></span> <span data-ttu-id="1ae8f-185">下列指令碼會建立執行範例查詢的原生編譯預存程序 (從「範例查詢」區段)。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-185">The following script creates a natively compiled stored procedure that runs the example query (from the Example Query section).</span></span>  
  
```sql  
CREATE PROCEDURE usp_SampleJoin  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
  LANGUAGE = 'english')  
  
  SELECT o.OrderID, c.CustomerID, c.ContactName   
FROM dbo.[Order] o INNER JOIN dbo.[Customer] c   
  ON c.CustomerID = o.CustomerID  
  
END  
```  
  
 <span data-ttu-id="1ae8f-186">原生編譯的預存程序會在建立時編譯，而解譯的預存程序則是在第一次執行時編譯</span><span class="sxs-lookup"><span data-stu-id="1ae8f-186">Natively compiled stored procedures are compiled at create time, whereas interpreted stored procedures are compiled at first execution time.</span></span> <span data-ttu-id="1ae8f-187">(編譯的一部分，尤其是指剖析和 Algebrization，會在建立時發生。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-187">(A portion of the compilation, particularly parsing and algebrization, take place at create.</span></span> <span data-ttu-id="1ae8f-188">不過，對於解譯的預存程序，查詢計劃的最佳化是在第一次執行時進行)。重新編譯邏輯也很類似。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-188">However, for interpreted stored procedures, optimization of the query plans takes place at first execution.) The recompilation logic is similar.</span></span> <span data-ttu-id="1ae8f-189">如果伺服器重新啟動，原生編譯的預存程序就會在第一次執行程序時重新編譯。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-189">Natively compiled stored procedures are recompiled on first execution of the procedure if the server is restarted.</span></span> <span data-ttu-id="1ae8f-190">如果計畫已不在計畫快取中，解譯的預存程序就會重新編譯。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-190">Interpreted stored procedures are recompiled if the plan is no longer in the plan cache.</span></span> <span data-ttu-id="1ae8f-191">下表摘要說明原生編譯的預存程序及解譯的預存程序之編譯和重新編譯案例：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-191">The following table summarizes compilation and recompilation cases for both natively compiled and interpreted stored procedures:</span></span>  
  
||<span data-ttu-id="1ae8f-192">原生編譯</span><span class="sxs-lookup"><span data-stu-id="1ae8f-192">Natively compiled</span></span>|<span data-ttu-id="1ae8f-193">對記憶體最佳化資料表進行解譯的</span><span class="sxs-lookup"><span data-stu-id="1ae8f-193">Interpreted</span></span>|  
|-|-----------------------|-----------------|  
|<span data-ttu-id="1ae8f-194">初始編譯</span><span class="sxs-lookup"><span data-stu-id="1ae8f-194">Initial compilation</span></span>|<span data-ttu-id="1ae8f-195">建立時。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-195">At create time.</span></span>|<span data-ttu-id="1ae8f-196">第一次執行時。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-196">At first execution.</span></span>|  
|<span data-ttu-id="1ae8f-197">自動重新編譯</span><span class="sxs-lookup"><span data-stu-id="1ae8f-197">Automatic recompilation</span></span>|<span data-ttu-id="1ae8f-198">在資料庫或伺服器重新啟動之後，第一次執行程序時。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-198">Upon first execution of the procedure after a database or server restart.</span></span>|<span data-ttu-id="1ae8f-199">伺服器重新啟動時。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-199">On server restart.</span></span> <span data-ttu-id="1ae8f-200">或者，從計畫快取收回，通常是依據結構描述或統計資料變更，或是記憶體壓力。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-200">Or, eviction from the plan cache, usually based on schema or stats changes, or memory pressure.</span></span>|  
|<span data-ttu-id="1ae8f-201">手動重新編譯</span><span class="sxs-lookup"><span data-stu-id="1ae8f-201">Manual recompilation</span></span>|<span data-ttu-id="1ae8f-202">不支援。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-202">Not supported.</span></span> <span data-ttu-id="1ae8f-203">解決方法是卸除並重新建立預存程序。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-203">The workaround is to drop and recreate the stored procedure.</span></span>|<span data-ttu-id="1ae8f-204">使用 `sp_recompile`。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-204">Use `sp_recompile`.</span></span> <span data-ttu-id="1ae8f-205">您可以從快取手動收回計畫，例如透過 DBCC FREEPROCCACHE。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-205">You can manually evict the plan from the cache, for example through DBCC FREEPROCCACHE.</span></span> <span data-ttu-id="1ae8f-206">您也可以建立預存程序 WITH RECOMPILE，而該預存程序將在每次執行時重新編譯。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-206">You can also create the stored procedure WITH RECOMPILE and the stored procedure will be recompiled at every execution.</span></span>|  
  
### <a name="compilation-and-query-processing"></a><span data-ttu-id="1ae8f-207">編譯和查詢處理</span><span class="sxs-lookup"><span data-stu-id="1ae8f-207">Compilation and Query Processing</span></span>  
 <span data-ttu-id="1ae8f-208">下圖說明原生編譯預存程序的編譯程序：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-208">The following diagram illustrates the compilation process for natively compiled stored procedures:</span></span>  
  
 <span data-ttu-id="1ae8f-209">![預存程序的原生編譯。](../../database-engine/media/hekaton-query-plan-6.gif "預存程序的原生編譯。")</span><span class="sxs-lookup"><span data-stu-id="1ae8f-209">![Native compilation of stored procedures.](../../database-engine/media/hekaton-query-plan-6.gif "Native compilation of stored procedures.")</span></span>  
<span data-ttu-id="1ae8f-210">預存程序的原生編譯。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-210">Native compilation of stored procedures.</span></span>  
  
 <span data-ttu-id="1ae8f-211">這個程序描述為：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-211">The process is described as,</span></span>  
  
1.  <span data-ttu-id="1ae8f-212">使用者對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 發出 `CREATE PROCEDURE` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-212">The user issues a `CREATE PROCEDURE` statement to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="1ae8f-213">剖析器和 Algebrizer 會為程序建立處理流程，以及為預存程序中的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查詢建立樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-213">The parser and algebrizer create the processing flow for the procedure, as well as query trees for the [!INCLUDE[tsql](../../../includes/tsql-md.md)] queries in the stored procedure.</span></span>  
  
3.  <span data-ttu-id="1ae8f-214">最佳化工具會為預存程序中的所有查詢建立最佳化的查詢執行計畫。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-214">The optimizer creates optimized query execution plans for all the queries in the stored procedure.</span></span>  
  
4.  <span data-ttu-id="1ae8f-215">記憶體中 OLTP 編譯器會採用具有內嵌最佳化查詢計劃的處理流程，並產生包含執行預存程序之機器碼的 DLL。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-215">The In-Memory OLTP compiler takes the processing flow with the embedded optimized query plans and generates a DLL that contains the machine code for executing the stored procedure.</span></span>  
  
5.  <span data-ttu-id="1ae8f-216">產生的 DLL 會載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-216">The generated DLL is loaded into memory.</span></span>  
  
 <span data-ttu-id="1ae8f-217">原生編譯預存程序的引動過程會轉譯為在 DLL 中呼叫函數。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-217">Invocation of a natively compiled stored procedure translates to calling a function in the DLL.</span></span>  
  
 <span data-ttu-id="1ae8f-218">![執行原生編譯預存程序。](../../database-engine/media/hekaton-query-plan-7.gif "執行原生編譯預存程序。")</span><span class="sxs-lookup"><span data-stu-id="1ae8f-218">![Execution of natively compiled stored procedures.](../../database-engine/media/hekaton-query-plan-7.gif "Execution of natively compiled stored procedures.")</span></span>  
<span data-ttu-id="1ae8f-219">執行原生編譯預存程序。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-219">Execution of natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="1ae8f-220">原生編譯預存程序的引動過程描述如下：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-220">Invocation of a natively compiled stored procedure is described as follows:</span></span>  
  
1.  <span data-ttu-id="1ae8f-221">使用者發出 `EXEC` *usp_myproc*語句。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-221">The user issues an `EXEC`*usp_myproc* statement.</span></span>  
  
2.  <span data-ttu-id="1ae8f-222">剖析器會擷取名稱和預存程序參數。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-222">The parser extracts the name and stored procedure parameters.</span></span>  
  
     <span data-ttu-id="1ae8f-223">如果陳述式已備妥，例如使用 `sp_prep_exec`，則剖析器不需要在執行時擷取程序名稱和參數。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-223">If the statement was prepared, for example using `sp_prep_exec`, the parser does not need to extract the procedure name and parameters at execution time.</span></span>  
  
3.  <span data-ttu-id="1ae8f-224">記憶體中 OLTP 執行階段會尋找預存程序的 DLL 進入點。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-224">The In-Memory OLTP runtime locates the DLL entry point for the stored procedure.</span></span>  
  
4.  <span data-ttu-id="1ae8f-225">然後會執行 DLL 中的機器碼，再將其結果傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-225">The machine code in the DLL is executed and the results of are returned to the client.</span></span>  
  
 <span data-ttu-id="1ae8f-226">**參數探測**</span><span class="sxs-lookup"><span data-stu-id="1ae8f-226">**Parameter sniffing**</span></span>  
  
 <span data-ttu-id="1ae8f-227">與在建立時編譯的原生編譯預存程序相反，解譯的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 預存程序會在第一次執行時編譯。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-227">Interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] stored procedures are compiled at first execution, in contrast to natively compiled stored procedures, which are compiled at create time.</span></span> <span data-ttu-id="1ae8f-228">在引動過程中編譯解譯的預存程序時，最佳化工具會在產生執行計畫時使用提供給這個引動過程的參數值。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-228">When interpreted stored procedures are compiled at invocation, the values of the parameters supplied for this invocation are used by the optimizer when generating the execution plan.</span></span> <span data-ttu-id="1ae8f-229">在編譯期間使用參數的動作，就稱為參數探測。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-229">This use of parameters during compilation is called parameter sniffing.</span></span>  
  
 <span data-ttu-id="1ae8f-230">參數探測不會用於編譯原生編譯的預存程序。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-230">Parameter sniffing is not used for compiling natively compiled stored procedures.</span></span> <span data-ttu-id="1ae8f-231">預存程序的所有參數都會視為具有 UNKNOWN 值。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-231">All parameters to the stored procedure are considered to have UNKNOWN values.</span></span> <span data-ttu-id="1ae8f-232">與解譯的預存程序相同，原生編譯的預存程序也支援 `OPTIMIZE FOR` 提示。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-232">Like interpreted stored procedures, natively compiled stored procedures also support the `OPTIMIZE FOR` hint.</span></span> <span data-ttu-id="1ae8f-233">如需詳細資訊，請參閱[查詢提示 &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query)。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-233">For more information, see [Query Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query).</span></span>  
  
### <a name="retrieving-a-query-execution-plan-for-natively-compiled-stored-procedures"></a><span data-ttu-id="1ae8f-234">擷取原生編譯預存程序的查詢執行計畫</span><span class="sxs-lookup"><span data-stu-id="1ae8f-234">Retrieving a Query Execution Plan for Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="1ae8f-235">原生編譯預存程序的查詢執行計畫，可以使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中的 [Estimated Execution Plan (估計的執行計畫)] 或 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 中的 SHOWPLAN_XML 選項加以擷取。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-235">The query execution plan for a natively compiled stored procedure can be retrieved using **Estimated Execution Plan** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], or using the SHOWPLAN_XML option in [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="1ae8f-236">例如：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-236">For example:</span></span>  
  
```sql  
SET SHOWPLAN_XML ON  
GO  
EXEC dbo.usp_myproc  
GO  
SET SHOWPLAN_XML OFF  
GO  
```  
  
 <span data-ttu-id="1ae8f-237">查詢最佳化工具所產生的執行計畫包含查詢運算子做為節點的樹狀結構，以及樹狀結構的分葉。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-237">The execution plan generated by the query optimizer consists of a tree with query operators on the nodes and leaves of the tree.</span></span> <span data-ttu-id="1ae8f-238">樹狀結構的結構決定運算子之間的互動 (資料列從一個運算子到另一個運算子的流程)。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-238">The structure of the tree determines the interaction (the flow of rows from one operator to another) between the operators.</span></span> <span data-ttu-id="1ae8f-239">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]的圖形檢視中，流程是由右至左。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-239">In the graphical view of [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], the flow is from right to left.</span></span> <span data-ttu-id="1ae8f-240">例如，圖 1 中的查詢計劃包含兩個索引掃描運算子，這兩個運算子會提供資料列給合併聯結運算子。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-240">For example, the query plan in figure 1 contains two index scan operators, which supplies rows to a merge join operator.</span></span> <span data-ttu-id="1ae8f-241">合併聯結運算子會將資料列提供給選取運算子。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-241">The merge join operator supplies rows to a select operator.</span></span> <span data-ttu-id="1ae8f-242">最後，選取運算子會將資料列傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-242">The select operator, finally, returns the rows to the client.</span></span>  
  
### <a name="query-operators-in-natively-compiled-stored-procedures"></a><span data-ttu-id="1ae8f-243">原生編譯預存程序中的查詢運算子</span><span class="sxs-lookup"><span data-stu-id="1ae8f-243">Query Operators in Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="1ae8f-244">下表摘要說明原生編譯預存程序內部支援的查詢運算子：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-244">The following table summarizes the query operators supported inside natively compiled stored procedures:</span></span>  
  
|<span data-ttu-id="1ae8f-245">運算子</span><span class="sxs-lookup"><span data-stu-id="1ae8f-245">Operator</span></span>|<span data-ttu-id="1ae8f-246">範例查詢</span><span class="sxs-lookup"><span data-stu-id="1ae8f-246">Sample query</span></span>|  
|--------------|------------------|  
|<span data-ttu-id="1ae8f-247">SELECT</span><span class="sxs-lookup"><span data-stu-id="1ae8f-247">SELECT</span></span>|`SELECT OrderID FROM dbo.[Order]`|  
|<span data-ttu-id="1ae8f-248">Insert</span><span class="sxs-lookup"><span data-stu-id="1ae8f-248">INSERT</span></span>|`INSERT dbo.Customer VALUES ('abc', 'def')`|  
|<span data-ttu-id="1ae8f-249">UPDATE</span><span class="sxs-lookup"><span data-stu-id="1ae8f-249">UPDATE</span></span>|`UPDATE dbo.Customer SET ContactName='ghi' WHERE CustomerID='abc'`|  
|<span data-ttu-id="1ae8f-250">刪除</span><span class="sxs-lookup"><span data-stu-id="1ae8f-250">DELETE</span></span>|`DELETE dbo.Customer WHERE CustomerID='abc'`|  
|<span data-ttu-id="1ae8f-251">Compute Scalar</span><span class="sxs-lookup"><span data-stu-id="1ae8f-251">Compute Scalar</span></span>|<span data-ttu-id="1ae8f-252">這個運算子同時用於內建函數和類型轉換。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-252">This operator is used both for intrinsic functions and type conversions.</span></span> <span data-ttu-id="1ae8f-253">並非所有函數和類型轉換都可在原生編譯預存程序內部受到支援。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-253">Not all functions and type conversions are supported inside natively compiled stored procedures.</span></span><br /><br /> `SELECT OrderID+1 FROM dbo.[Order]`|  
|<span data-ttu-id="1ae8f-254">Nested Loops Join</span><span class="sxs-lookup"><span data-stu-id="1ae8f-254">Nested Loops Join</span></span>|<span data-ttu-id="1ae8f-255">巢狀迴圈是原生編譯預存程序中唯一支援的聯結運算子。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-255">Nested Loops is the only join operator supported in natively compiled stored procedures.</span></span> <span data-ttu-id="1ae8f-256">即使做為解譯 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 執行的相同查詢計劃包含雜湊或合併聯結，所有包含聯結的計畫還是都會使用 Nested Loops 運算子。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-256">All plans that contain joins will use the Nested Loops operator, even if the plan for same query executed as interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] contains a hash or merge join.</span></span><br /><br /> `SELECT o.OrderID, c.CustomerID`  <br /> `FROM dbo.[Order] o INNER JOIN dbo.[Customer] c`|  
|<span data-ttu-id="1ae8f-257">Sort</span><span class="sxs-lookup"><span data-stu-id="1ae8f-257">Sort</span></span>|`SELECT ContactName FROM dbo.Customer`  <br /> `ORDER BY ContactName`|  
|<span data-ttu-id="1ae8f-258">頂端</span><span class="sxs-lookup"><span data-stu-id="1ae8f-258">Top</span></span>|`SELECT TOP 10 ContactName FROM dbo.Customer`|  
|<span data-ttu-id="1ae8f-259">Top-sort</span><span class="sxs-lookup"><span data-stu-id="1ae8f-259">Top-sort</span></span>|<span data-ttu-id="1ae8f-260">`TOP` 運算式 (要傳回的資料列數目) 不得超過 8,000 個資料列。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-260">The `TOP` expression (the number of rows to be returned) cannot exceed 8,000 rows.</span></span> <span data-ttu-id="1ae8f-261">如果查詢中也有聯結和彙總運算子，則數目會更少。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-261">Fewer if there are also join and aggregation operators in the query.</span></span> <span data-ttu-id="1ae8f-262">與基底資料表的資料列數相比，聯結和彙總運算子通常會減少要排序的資料列數。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-262">Joins and aggregation do typically reduce the number of rows to be sorted, compared with the row count of the base tables.</span></span><br /><br /> `SELECT TOP 10 ContactName FROM dbo.Customer`  <br /> `ORDER BY ContactName`|  
|<span data-ttu-id="1ae8f-263">Stream Aggregate</span><span class="sxs-lookup"><span data-stu-id="1ae8f-263">Stream Aggregate</span></span>|<span data-ttu-id="1ae8f-264">請注意，Hash Match 運算子不支援彙總。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-264">Note that the Hash Match operator is not supported for aggregation.</span></span> <span data-ttu-id="1ae8f-265">因此，即使解譯的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 中相同查詢的計畫使用 Hash Match 運算子，原生編譯預存程序中的所有彙總仍會使用 Stream Aggregate 運算子。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-265">Therefore, all aggregation in natively compiled stored procedures uses the Stream Aggregate operator, even if the plan for the same query in interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] uses the Hash Match operator.</span></span><br /><br /> `SELECT count(CustomerID) FROM dbo.Customer`|  
  
## <a name="column-statistics-and-joins"></a><span data-ttu-id="1ae8f-266">資料行統計資料和聯結</span><span class="sxs-lookup"><span data-stu-id="1ae8f-266">Column Statistics and Joins</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="1ae8f-267">會在索引鍵資料行中維護值的統計資料，以協助估計特定作業的成本，例如索引掃描或索引搜尋。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-267">maintains statistics on values in index key columns to help estimate the cost of certain operations, such as index scan and index seeks.</span></span> <span data-ttu-id="1ae8f-268">(如果您明確建立非索引之索引鍵資料行的統計資料，或如果查詢最佳化工具為了回應包含述詞的查詢而建立它們，則 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 也會建立這些統計資料。)成本估計的主要標準是單一運算子所處理的資料列數</span><span class="sxs-lookup"><span data-stu-id="1ae8f-268">( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] also creates statistics on non-index key columns if you explicitly create them or if the query optimizer creates them in response to a query with a predicate.) The main metric in cost estimation is the number of rows processed by a single operator.</span></span> <span data-ttu-id="1ae8f-269">請注意，對於磁碟基礎的資料表，特定運算子所存取的頁面數目在成本估計中佔有相當大的比例。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-269">Note that for disk-based tables, the number of pages accessed by a particular operator is significant in cost estimation.</span></span> <span data-ttu-id="1ae8f-270">但是，由於頁面數對於記憶體最佳化資料表而言並不重要 (一律為零)，因此這裡的討論將著重在資料列計數。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-270">However, as page count is not important for memory-optimized tables (it is always zero), this discussion focuses on row count.</span></span> <span data-ttu-id="1ae8f-271">估計時間是從計劃中的索引搜尋和掃描運算子開始算起，然後延伸以納入其他運算子，像是聯結運算子。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-271">The estimation starts with the index seek and scan operators in the plan, and is then extended to include the other operators, like the join operator.</span></span> <span data-ttu-id="1ae8f-272">聯結運算子所要處理的估計資料列數是以基礎索引、搜尋和掃描運算子的估計為依據。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-272">The estimated number of rows to be processed by a join operator is based on the estimation for the underlying index, seek, and scan operators.</span></span> <span data-ttu-id="1ae8f-273">若要對記憶體最佳化資料表進行解譯的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 存取，您可以觀察實際執行計畫，了解計畫中運算子的估計資料列計數和實際資料列計數之間的差異。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-273">For interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] access to memory-optimized tables, you can observe the actual execution plan to see the difference between the estimated and actual row counts for the operators in the plan.</span></span>  
  
 <span data-ttu-id="1ae8f-274">在圖 1 的範例中，</span><span class="sxs-lookup"><span data-stu-id="1ae8f-274">For the example in figure 1,</span></span>  
  
-   <span data-ttu-id="1ae8f-275">Customer 上叢集索引掃描的資料列估計為 91；實際為 91。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-275">The clustered index scan on Customer has estimated 91; actual 91.</span></span>  
  
-   <span data-ttu-id="1ae8f-276">CustomerID 上非叢集索引掃描的資料列估計為 830；實際為 830。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-276">The nonclustered index scan on CustomerID has estimated 830; actual 830.</span></span>  
  
-   <span data-ttu-id="1ae8f-277">Merge Join 運算子的資料列估計為 815；實際為 830。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-277">The Merge Join operator has estimated 815; actual 830.</span></span>  
  
 <span data-ttu-id="1ae8f-278">索引掃描的估計是正確的。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-278">The estimates for the index scans are accurate.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="1ae8f-279">會維護磁碟資料表的資料列計數。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-279">maintains the row count for disk-based tables.</span></span> <span data-ttu-id="1ae8f-280">完整資料表和索引掃描的估計永遠正確，而聯結的估計也一樣相當正確。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-280">Estimates for full table and index scans are always accurate.</span></span> <span data-ttu-id="1ae8f-281">聯結的估計同樣相當正確。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-281">The estimate for the join is fairly accurate, too.</span></span>  
  
 <span data-ttu-id="1ae8f-282">如果這些估計改變，不同計畫替代方式的成本考量也會改變。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-282">If these estimates change, the cost considerations for different plan alternatives change as well.</span></span> <span data-ttu-id="1ae8f-283">例如，如果聯結其中一端的估計資料列計數為 1，或只有少數資料列，則使用巢狀迴圈聯結成本較低。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-283">For example, if one of the sides of the join has an estimated row count of 1 or just a few rows, using a nested loops joins is less expensive.</span></span>  
  
 <span data-ttu-id="1ae8f-284">以下是查詢的計畫：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-284">The following is the plan for the query:</span></span>  
  
```  
SELECT o.OrderID, c.* FROM dbo.[Customer] c INNER JOIN dbo.[Order] o ON c.CustomerID = o.CustomerID  
```  
  
 <span data-ttu-id="1ae8f-285">只保留 Customer 資料表中的一個資料列，並刪除其餘全部資料列時：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-285">After deleting all rows but one in the table Customer:</span></span>  
  
 <span data-ttu-id="1ae8f-286">![資料行統計資料和聯結。](../../database-engine/media/hekaton-query-plan-9.gif "資料行統計資料和聯結。")</span><span class="sxs-lookup"><span data-stu-id="1ae8f-286">![Column statistics and joins.](../../database-engine/media/hekaton-query-plan-9.gif "Column statistics and joins.")</span></span>  
  
 <span data-ttu-id="1ae8f-287">關於這個查詢計畫：</span><span class="sxs-lookup"><span data-stu-id="1ae8f-287">Regarding this query plan:</span></span>  
  
-   <span data-ttu-id="1ae8f-288">Hash Match 已取代為 Nested Loops 實體聯結運算子。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-288">The Hash Match has been replaced with a Nested Loops physical join operator.</span></span>  
  
-   <span data-ttu-id="1ae8f-289">對 IX_CustomerID 的完整索引掃描已取代為索引搜尋。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-289">The full index scan on IX_CustomerID has been replaced with an index seek.</span></span> <span data-ttu-id="1ae8f-290">這樣的結果會是掃描 5 個資料列，而不是完整索引掃描所需的 830 個資料列。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-290">This resulted in scanning 5 rows, instead of the 830 rows required for the full index scan.</span></span>  
  
### <a name="statistics-and-cardinality-for-memory-optimized-tables"></a><span data-ttu-id="1ae8f-291">記憶體最佳化資料表的統計資料和基數</span><span class="sxs-lookup"><span data-stu-id="1ae8f-291">Statistics and Cardinality for Memory-Optimized Tables</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="1ae8f-292">會維護記憶體最佳化資料表的資料行層級統計資料。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-292">maintains column-level statistics for memory-optimized tables.</span></span> <span data-ttu-id="1ae8f-293">此外，它也會維護資料表的實際資料列計數。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-293">In addition, it maintains the actual row count of the table.</span></span> <span data-ttu-id="1ae8f-294">但和磁碟資料表不同，記憶體最佳化資料表的統計資料不會自動更新。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-294">However, in contrast to disk-based tables, the statistics for memory-optimized tables are not automatically updated.</span></span> <span data-ttu-id="1ae8f-295">因此，統計資料在資料表中進行過重大變更之後，需要手動更新。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-295">Therefore, statistics need to be manually updated after significant changes in the tables.</span></span> <span data-ttu-id="1ae8f-296">如需詳細資訊，請參閱 [記憶體最佳化資料表的統計資料](memory-optimized-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="1ae8f-296">For more information, see [Statistics for Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ae8f-297">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ae8f-297">See Also</span></span>  
 [<span data-ttu-id="1ae8f-298">記憶體最佳化資料表</span><span class="sxs-lookup"><span data-stu-id="1ae8f-298">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
