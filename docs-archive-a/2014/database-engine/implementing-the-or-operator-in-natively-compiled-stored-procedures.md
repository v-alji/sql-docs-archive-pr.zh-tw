---
title: 在原生編譯的預存程式中執行 OR 運算子 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f2528e74-2b1c-48cb-861b-c4e57b51ac35
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7ed762e062cbc6831eb46784ef71fc7889850676
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703282"
---
# <a name="implementing-the-or-operator-in-natively-compiled-stored-procedures"></a><span data-ttu-id="97c36-102">在原生編譯的預存程序中實作 OR 運算子</span><span class="sxs-lookup"><span data-stu-id="97c36-102">Implementing the OR Operator in Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="97c36-103">原生編譯預存程序內部的查詢述詞中不支援 OR 運算子。</span><span class="sxs-lookup"><span data-stu-id="97c36-103">OR operators are not supported in query predicates in natively compiled stored procedures.</span></span> <span data-ttu-id="97c36-104">由於原生編譯預存程序內部的查詢述詞中也不支援 NOT 運算子，所以無法透過單獨使用同等的邏輯運算子來模擬 OR 運算子的效果。</span><span class="sxs-lookup"><span data-stu-id="97c36-104">Because NOT operators are also not supported in query predicates in natively compiled stored procedures, the effects of OR operators cannot be simulated through the use of equivalent logical operators alone.</span></span> <span data-ttu-id="97c36-105">不過，OR 運算子的效果可透過記憶體最佳化資料表變數加以模擬。</span><span class="sxs-lookup"><span data-stu-id="97c36-105">However, the effects of an OR operator may be simulated with memory-optimized table variables.</span></span>  
  
## <a name="or-operator-in-where-clause"></a><span data-ttu-id="97c36-106">WHERE 子句中的 OR 運算子</span><span class="sxs-lookup"><span data-stu-id="97c36-106">OR Operator in WHERE Clause</span></span>  
 <span data-ttu-id="97c36-107">如果您在 WHERE 子句中有 OR 運算子，您可以使用下列方法模擬其行為：</span><span class="sxs-lookup"><span data-stu-id="97c36-107">If you have an OR operator in a WHERE clause, you can use the following approach to simulate its behavior:</span></span>  
  
1.  <span data-ttu-id="97c36-108">使用適當的結構描述建立記憶體最佳化資料表變數。</span><span class="sxs-lookup"><span data-stu-id="97c36-108">Create a memory-optimized table variable with the appropriate schema.</span></span> <span data-ttu-id="97c36-109">這需要預先定義的記憶體最佳化資料表類型。</span><span class="sxs-lookup"><span data-stu-id="97c36-109">This requires a predefined memory-optimized table type.</span></span>  
  
2.  <span data-ttu-id="97c36-110">從最上層 OR 運算子開始，根據 OR 運算子所聯結的述詞將 WHERE 子句分成兩部分。</span><span class="sxs-lookup"><span data-stu-id="97c36-110">Starting with the top level OR operator, separate the WHERE clause into two parts according to the predicates joined by the OR operator.</span></span> <span data-ttu-id="97c36-111">如果您在 WHERE 子句中有一個以上的 OR 運算子，您可能必須多次執行這項處理。</span><span class="sxs-lookup"><span data-stu-id="97c36-111">If you have more than one OR operator in a WHERE clause, you may need to do this more than once.</span></span> <span data-ttu-id="97c36-112">重複這個步驟，直到沒有留下任何 OR 運算子為止。</span><span class="sxs-lookup"><span data-stu-id="97c36-112">Repeat this step until no OR operators remain.</span></span> <span data-ttu-id="97c36-113">例如，如果您有以下述詞：</span><span class="sxs-lookup"><span data-stu-id="97c36-113">For example, if you have the following predicate:</span></span>  
  
    ```  
    pred1 OR (pred2 AND (pred3 OR pred4)) OR (pred5 AND pred6)  
    ```  
  
     <span data-ttu-id="97c36-114">在這個步驟之後，您應該有下列述詞：</span><span class="sxs-lookup"><span data-stu-id="97c36-114">After this step, you should have the following predicates:</span></span>  
  
    ```  
    pred1  
    pred5 AND pred6  
    pred2 AND pred3  
    pred2 AND pred4  
    ```  
  
3.  <span data-ttu-id="97c36-115">使用步驟 2 中找到之兩個部分的每一部分當做述詞來執行查詢。</span><span class="sxs-lookup"><span data-stu-id="97c36-115">Execute a query with each of the two parts found in Step 2 as the predicate.</span></span> <span data-ttu-id="97c36-116">將每個查詢的結果插入步驟 1 所建立的記憶體最佳化資料表變數中。</span><span class="sxs-lookup"><span data-stu-id="97c36-116">Insert the result for each query into the memory-optimized table variable created in Step 1.</span></span>  
  
4.  <span data-ttu-id="97c36-117">必要時，從記憶體最佳化資料表變數中移除重複項。</span><span class="sxs-lookup"><span data-stu-id="97c36-117">If necessary, remove duplicates from the memory-optimized table variable.</span></span>  
  
5.  <span data-ttu-id="97c36-118">使用記憶體最佳化資料表變數的內容當做查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="97c36-118">Use the content of the memory-optimized table variable as the result from the query.</span></span>  
  
 <span data-ttu-id="97c36-119">下列範例使用 AdventureWorks2012 資料庫中為 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 更新的資料表。</span><span class="sxs-lookup"><span data-stu-id="97c36-119">The following sample uses tables from the AdventureWorks2012 database that were updated for [!INCLUDE[hek_2](../includes/hek-2-md.md)].</span></span> <span data-ttu-id="97c36-120">若要下載此範例的檔，請移至[AdventureWorks 資料庫-2012、2008R2 和 2008](https://msftdbprodsamples.codeplex.com/releases/view/93587)。</span><span class="sxs-lookup"><span data-stu-id="97c36-120">To download the files for this sample, goto [AdventureWorks Databases - 2012, 2008R2 and 2008](https://msftdbprodsamples.codeplex.com/releases/view/93587).</span></span> <span data-ttu-id="97c36-121">若要將程式 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 代碼範例套用至 AdventureWorks2012，請移至[SQL Server 2014 記憶體內部 OLTP 範例](https://msftdbprodsamples.codeplex.com/releases/view/114491)。</span><span class="sxs-lookup"><span data-stu-id="97c36-121">To apply [!INCLUDE[hek_2](../includes/hek-2-md.md)] code sample to AdventureWorks2012, go to [SQL Server 2014 In-Memory OLTP Sample](https://msftdbprodsamples.codeplex.com/releases/view/114491).</span></span>  
  
 <span data-ttu-id="97c36-122">將下列預存程序加入至資料庫。</span><span class="sxs-lookup"><span data-stu-id="97c36-122">Add the following stored procedure to the database.</span></span> <span data-ttu-id="97c36-123">我們將會轉換這個預存程序來使用原生編譯。</span><span class="sxs-lookup"><span data-stu-id="97c36-123">We will convert this stored procedure to use native compilation.</span></span>  
  
```  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesOrderDetail_ondisk  
  @SalesOrderId int = 0, @SalesOrderDetailId int = 0,   
  @CarrierTrackingNumber nvarchar(25) = N'', @ProductId int = 0,   
  @minUnitPrice money = 0, @maxUnitPrice money = 0  
AS BEGIN  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_ondisk s  
  WHERE  s.SalesOrderId = @SalesOrderId  
      OR s.SalesOrderDetailId = @SalesOrderDetailId  
      OR s.CarrierTrackingNumber = @CarrierTrackingNumber  
      OR s.ProductID = @ProductId  
      OR (s.UnitPrice > @minUnitPrice AND s.UnitPrice < @maxUnitPrice)  
END  
GO  
```  
  
 <span data-ttu-id="97c36-124">在轉換後，資料表和預存程序的結構描述如下所示：</span><span class="sxs-lookup"><span data-stu-id="97c36-124">After conversion, the table and stored procedure schema is as follows,</span></span>  
  
```  
CREATE TYPE Sales.fuzzySearchSalesOrderDetailType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  ModifiedDate datetime2(7) not null  
  INDEX ix_fuzzySearchSalesOrderDetailType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE TYPE Sales.fuzzySearchSalesOrderDetailTempType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  recordcount int not null  
  INDEX ix_fuzzySearchSalesOrderDetailTempType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesOrderDetail_inmem  
  @SalesOrderId int = 0, @SalesOrderDetailId int = 0,   
  @CarrierTrackingNumber nvarchar(25) = N'', @ProductId int = 0,   
  @minUnitPrice money = 0, @maxUnitPrice money = 0  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'ENGLISH')  
  
  DECLARE @retValue Sales.fuzzySearchSalesOrderDetailType  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.SalesOrderId = @SalesOrderId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.SalesOrderDetailId = @SalesOrderDetailId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.CarrierTrackingNumber COLLATE Latin1_General_BIN2 = @CarrierTrackingNumber COLLATE Latin1_General_BIN2   
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE s.ProductID = @ProductId  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, ModifiedDate)  
  SELECT SalesOrderId, SalesOrderDetailId, ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  WHERE (s.UnitPrice > @minUnitPrice AND s.UnitPrice < @maxUnitPrice)  
  
  -- After the above statements, there will be duplicates inside @retValue  
  -- Delete the duplicates from @retValue  
  DECLARE @duplicates Sales.fuzzySearchSalesOrderDetailTempType  
  
  INSERT INTO @duplicates (SalesOrderId, SalesOrderDetailId, recordcount)   
  SELECT SalesOrderId, SalesOrderDetailId, COUNT(*) AS recordCount  
  FROM @retValue  
  GROUP BY SalesOrderId, SalesOrderDetailId  
  
  -- Now we have one row per pair  
  -- clear and rebuild the result set  
  DELETE FROM @retValue  
  
  INSERT INTO @retValue  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN @duplicates d ON s.SalesOrderId = d.SalesOrderId AND s.SalesOrderDetailId = d.SalesOrderDetailId  
  
  -- After this every pair of (SalesOrderId, SalesOrderDetailId) in @retValue should be unique.  
  SELECT SalesorderId, SalesOrderDetailId, ModifiedDate FROM @retValue  
END  
GO  
```  
  
## <a name="or-operator-in-join-condition"></a><span data-ttu-id="97c36-125">JOIN 條件中的 OR 運算子</span><span class="sxs-lookup"><span data-stu-id="97c36-125">OR Operator in JOIN Condition</span></span>  
 <span data-ttu-id="97c36-126">如果您在 SELECT 陳述式的 JOIN 條件中有 OR 運算子，您可以使用下列方法模擬其行為。</span><span class="sxs-lookup"><span data-stu-id="97c36-126">If you have an OR operator in a JOIN condition of a SELECT statement, you may use the following approach to simulate its behavior.</span></span> <span data-ttu-id="97c36-127">如果您在 JOIN 條件中有多個 OR 運算子，或者您在 OR 運算子中有多個 JOIN 條件，您可能必須多次執行這項處理。</span><span class="sxs-lookup"><span data-stu-id="97c36-127">If you have more than one OR operator in a JOIN condition or you have multiple JOIN condition with OR operators, you may need to do this more than once.</span></span>  
  
 <span data-ttu-id="97c36-128">如果您有 OUTER JOIN 條件，您可以將這個因應措施與 OUTER JOIN 條件的因應措施結合在一起。</span><span class="sxs-lookup"><span data-stu-id="97c36-128">If you have OUTER JOIN conditions, you may combine this workaround with the workaround for OUTER JOIN conditions.</span></span>  
  
1.  <span data-ttu-id="97c36-129">使用適當的結構描述建立記憶體最佳化資料表變數。</span><span class="sxs-lookup"><span data-stu-id="97c36-129">Create a memory-optimized table variable with the appropriate schema.</span></span> <span data-ttu-id="97c36-130">這需要預先定義的記憶體最佳化資料表類型。</span><span class="sxs-lookup"><span data-stu-id="97c36-130">This requires a predefined memory-optimized table type.</span></span>  
  
2.  <span data-ttu-id="97c36-131">根據 OR 運算子所聯結的述詞，將 JOIN 條件中的述詞分成兩部分。</span><span class="sxs-lookup"><span data-stu-id="97c36-131">Separate the predicate in the JOIN condition into two parts according to the predicates joined by the OR operator.</span></span> <span data-ttu-id="97c36-132">如果您有多個 JOIN 條件，您可能必須針對每個 JOIN 條件進行這項處理，然後建立一組結果片段的組合。</span><span class="sxs-lookup"><span data-stu-id="97c36-132">If you have multiple JOIN conditions, you may need to do this for each JOIN condition and then create a set of combinations of the resulting fragments.</span></span> <span data-ttu-id="97c36-133">例如，如果您有三個 JOIN 條件，每個 JOIN 條件中都有一個 OR 運算子，您可能會有 2x2x2=8 個述詞。</span><span class="sxs-lookup"><span data-stu-id="97c36-133">For example, if you have three JOIN conditions with one OR operator in each JOIN condition, you may have 2x2x2=8 predicates.</span></span>  
  
3.  <span data-ttu-id="97c36-134">針對步驟 2 所產生的每個述詞建立一個查詢，將其結果插入步驟 1 所建立的記憶體最佳化資料表變數中。</span><span class="sxs-lookup"><span data-stu-id="97c36-134">For each predicate produced by Step 2, create a query that will insert its result into the memory-optimized table variable created in Step 1.</span></span>  
  
4.  <span data-ttu-id="97c36-135">必要時，從記憶體最佳化資料表變數中移除重複項。</span><span class="sxs-lookup"><span data-stu-id="97c36-135">If necessary, remove duplicates from the memory-optimized table variable.</span></span>  
  
5.  <span data-ttu-id="97c36-136">使用記憶體最佳化資料表變數的內容當做查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="97c36-136">Use the content of the memory-optimized table variable as the result from the query.</span></span>  
  
 <span data-ttu-id="97c36-137">下列範例使用 AdventureWorks2012 資料庫中為 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 更新的資料表。</span><span class="sxs-lookup"><span data-stu-id="97c36-137">The following sample uses tables from the AdventureWorks2012 database that were updated for [!INCLUDE[hek_2](../includes/hek-2-md.md)].</span></span> <span data-ttu-id="97c36-138">若要下載此範例的檔，請移至[AdventureWorks 資料庫-2012、2008R2 和 2008](https://msftdbprodsamples.codeplex.com/releases/view/93587)。</span><span class="sxs-lookup"><span data-stu-id="97c36-138">To download the files for this sample, goto [AdventureWorks Databases - 2012, 2008R2 and 2008](https://msftdbprodsamples.codeplex.com/releases/view/93587).</span></span> <span data-ttu-id="97c36-139">若要將程式 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 代碼範例套用至 AdventureWorks2012，請移至[SQL Server 2014 記憶體內部 OLTP 範例](https://msftdbprodsamples.codeplex.com/releases/view/114491)。</span><span class="sxs-lookup"><span data-stu-id="97c36-139">To apply [!INCLUDE[hek_2](../includes/hek-2-md.md)] code sample to AdventureWorks2012, go to [SQL Server 2014 In-Memory OLTP Sample](https://msftdbprodsamples.codeplex.com/releases/view/114491).</span></span>  
  
 <span data-ttu-id="97c36-140">將下列預存程序加入至資料庫。</span><span class="sxs-lookup"><span data-stu-id="97c36-140">Add the following stored procedure to the database.</span></span> <span data-ttu-id="97c36-141">我們將會轉換這個預存程序來使用原生編譯。</span><span class="sxs-lookup"><span data-stu-id="97c36-141">We will convert this stored procedure to use native compilation.</span></span> <span data-ttu-id="97c36-142">此範例使用 INNER JOIN 條件。</span><span class="sxs-lookup"><span data-stu-id="97c36-142">This sample uses INNER JOIN conditions.</span></span>  
  
```  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesSpecialOffers_ondisk  
  @SpecialOfferId int  
AS BEGIN  
  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_ondisk s  
  JOIN Sales.SpecialOffer_onDisk offer   
    ON s.SpecialOfferID = offer.SpecialOfferID   
    OR s.ProductID IN (SELECT ProductId FROM Sales.SpecialOfferProduct sop WHERE sop.SpecialOfferID = @SpecialOfferId)  
END  
```  
  
 <span data-ttu-id="97c36-143">在轉換後，資料表和預存程序的結構描述如下所示：</span><span class="sxs-lookup"><span data-stu-id="97c36-143">After conversion, the table and stored procedure schema is as follows,</span></span>  
  
```  
CREATE TYPE Sales.fuzzySearchSalesSpecialOffers_Type AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  SpecialOfferId int not null,  
  ModifiedDate datetime2(7) not null  
  INDEX ix_fuzzySearchSalesSpecialOffers_Type NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE TYPE Sales.fuzzySearchSalesSpecialOffers_TempType AS TABLE  
(  
  SalesOrderId int not null,  
  SalesOrderDetailId int not null,  
  SpecialOfferId int not null,  
  recordcount int null  
  INDEX ix_fuzzySearchSalesSpecialOffers_TempType NONCLUSTERED (SalesOrderId, SalesOrderDetailId)  
) WITH (MEMORY_OPTIMIZED = ON)  
GO  
  
CREATE PROCEDURE Sales.usp_fuzzySearchSalesSpecialOffers_inmem  
  @SpecialOfferId int  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'ENGLISH')  
  
  DECLARE @retValue Sales.FuzzySearchSalesSpecialOffers_Type  
  
  -- Find all special offers matching the conditions  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, SpecialOfferid, ModifiedDate)  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN Sales.SpecialOffer_inmem offer   
    ON s.SpecialOfferID = offer.SpecialOfferID  
  
  INSERT INTO @retValue (SalesOrderId, SalesOrderDetailId, SpecialOfferid, ModifiedDate)  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN Sales.SpecialOfferProduct_inmem sop   
    ON sop.SpecialOfferId = @SpecialOfferId AND s.ProductID = sop.ProductId  
  
  -- Now we need to remove the duplicates from @matchingSpecialOffers  
  DECLARE @duplicates Sales.fuzzySearchSalesSpecialOffers_TempType  
  
  INSERT INTO @duplicates (SalesOrderId, SalesOrderDetailId, SpecialOfferid, recordcount)  
  SELECT SalesOrderId, SalesOrderDetailId, SpecialOfferId, COUNT(*)   
  FROM @retValue  
  GROUP BY SalesOrderId, SalesOrderDetailId, SpecialOfferId  
  
  -- now there should be no duplicates within @duplicate  
  -- use @duplicate for join.  
  SELECT s.SalesOrderId, s.SalesOrderDetailId, s.SpecialOfferID, s.ModifiedDate  
  FROM Sales.SalesOrderDetail_inmem s  
  JOIN @duplicates offer   
    ON    s.SalesOrderId = offer.SalesOrderId   
      AND s.SalesOrderDetailId = offer.SalesOrderDetailID   
      AND s.SpecialOfferId = offer.SpecialOfferId  
END  
GO  
```  
  
## <a name="side-effects"></a><span data-ttu-id="97c36-144">副作用</span><span class="sxs-lookup"><span data-stu-id="97c36-144">Side Effects</span></span>  
 <span data-ttu-id="97c36-145">如果您在 WHERE 子句或 JOIN 條件中有多個 OR 運算子，模擬此行為所必須執行的查詢數目可能會以指數方式遞增。</span><span class="sxs-lookup"><span data-stu-id="97c36-145">If you have more than one OR operator in the WHERE clause or JOIN condition, the number of queries you need to execute to simulate the behavior may increase exponentially.</span></span> <span data-ttu-id="97c36-146">這樣可能會降低查詢效能，也可能會增加記憶體使用量，因為必須使用記憶體最佳化資料表變數。</span><span class="sxs-lookup"><span data-stu-id="97c36-146">This may slow down query performance and may increase memory usage due to the need to use memory-optimized table variables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97c36-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97c36-147">See Also</span></span>  
 [<span data-ttu-id="97c36-148">原生編譯預存程序的移轉問題</span><span class="sxs-lookup"><span data-stu-id="97c36-148">Migration Issues for Natively Compiled Stored Procedures</span></span>](../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)  
  
