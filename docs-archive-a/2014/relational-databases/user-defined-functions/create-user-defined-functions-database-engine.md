---
title: 建立使用者定義函式 (Database Engine) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SCHEMABINDING clause
- schema-bound functions [SQL Server]
- user-defined functions [SQL Server], creating
- CREATE FUNCTION statement
- valid statements [SQL Server]
ms.assetid: f0d5dd10-73fd-4e05-9177-07f56552bdf7
author: rothja
ms.author: jroth
ms.openlocfilehash: 790fa1b969f933890e050311173fcde3f12c37ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606112"
---
# <a name="create-user-defined-functions-database-engine"></a><span data-ttu-id="1d3d3-102">建立使用者定義函數 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="1d3d3-102">Create User-defined Functions (Database Engine)</span></span>
  <span data-ttu-id="1d3d3-103">本主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中建立使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-103">This topic describes how to create a user-defined function in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1d3d3-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="1d3d3-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1d3d3-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="1d3d3-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1d3d3-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="1d3d3-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1d3d3-107">安全性</span><span class="sxs-lookup"><span data-stu-id="1d3d3-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1d3d3-108">**若要建立使用者定義函數：**</span><span class="sxs-lookup"><span data-stu-id="1d3d3-108">**To create a user-defined function:**</span></span>  
  
     [<span data-ttu-id="1d3d3-109">建立純量函數</span><span class="sxs-lookup"><span data-stu-id="1d3d3-109">Create a Scalar Function</span></span>](#Scalar)  
  
     [<span data-ttu-id="1d3d3-110">建立資料表值函式</span><span class="sxs-lookup"><span data-stu-id="1d3d3-110">Create a Table-valued Function</span></span>](#TVF)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1d3d3-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="1d3d3-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1d3d3-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="1d3d3-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="1d3d3-113">使用者定義函數不能用來執行修改資料庫狀態的動作。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-113">User-defined functions cannot be used to perform actions that modify the database state.</span></span>  
  
-   <span data-ttu-id="1d3d3-114">使用者定義函數不得包含具有資料表當做其目標的 OUTPUT INTO 子句。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-114">User-defined functions cannot contain an OUTPUT INTO clause that has a table as its target.</span></span>  
  
-   <span data-ttu-id="1d3d3-115">使用者定義函數無法傳回多個結果集。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-115">User-defined functions can not return multiple result sets.</span></span> <span data-ttu-id="1d3d3-116">如果您需要傳回多個結果集，請使用預存程序。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-116">Use a stored procedure if you need to return multiple result sets.</span></span>  
  
-   <span data-ttu-id="1d3d3-117">使用者定義函數中限制錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-117">Error handling is restricted in a user-defined function.</span></span> <span data-ttu-id="1d3d3-118">UDF 不支援 [嘗試 ...]CATCH @ERROR 或 RAISERROR。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-118">A UDF does not support TRY...CATCH, @ERROR or RAISERROR.</span></span>  
  
-   <span data-ttu-id="1d3d3-119">使用者定義函數無法呼叫預存程序，但是可以呼叫擴充預存程序。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-119">User-defined functions cannot call a stored procedure, but can call an extended stored procedure.</span></span>  
  
-   <span data-ttu-id="1d3d3-120">使用者定義函數無法利用動態 SQL 或暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-120">User-defined functions cannot make use of dynamic SQL or temp tables.</span></span> <span data-ttu-id="1d3d3-121">允許使用資料表變數。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-121">Table variables are allowed.</span></span>  
  
-   <span data-ttu-id="1d3d3-122">使用者定義函數中不允許使用 SET 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-122">SET statements are not allowed in a user-defined function.</span></span>  
  
-   <span data-ttu-id="1d3d3-123">不允許使用 FOR XML 子句</span><span class="sxs-lookup"><span data-stu-id="1d3d3-123">The FOR XML clause is not allowed</span></span>  
  
-   <span data-ttu-id="1d3d3-124">使用者定義函數可以具有巢狀結構；也就是說，某個使用者定義函數可以呼叫另一個使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-124">User-defined functions can be nested; that is, one user-defined function can call another.</span></span> <span data-ttu-id="1d3d3-125">被呼叫的函數開始執行時，巢狀層級會遞增；被呼叫的函數完成執行時，巢狀層級會遞減。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-125">The nesting level is incremented when the called function starts execution, and decremented when the called function finishes execution.</span></span> <span data-ttu-id="1d3d3-126">使用者定義函數所建立的巢狀結構最多可以有 32 個層級。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-126">User-defined functions can be nested up to 32 levels.</span></span> <span data-ttu-id="1d3d3-127">超過巢狀層級上限會導致整個呼叫函數鏈結失敗。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-127">Exceeding the maximum levels of nesting causes the whole calling function chain to fail.</span></span> <span data-ttu-id="1d3d3-128">依照 32 個層級巢狀限制，Transact-SQL 使用者定義函數之 Managed 程式碼的任何參考都算是一個層級。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-128">Any reference to managed code from a Transact-SQL user-defined function counts as one level against the 32-level nesting limit.</span></span> <span data-ttu-id="1d3d3-129">從 Managed 程式碼內叫用的方法，不列入這項限制。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-129">Methods invoked from within managed code do not count against this limit.</span></span>  
  
-   <span data-ttu-id="1d3d3-130">下列 Service Broker 陳述式不能併入 Transact-SQL 使用者定義函數的定義中：</span><span class="sxs-lookup"><span data-stu-id="1d3d3-130">The following Service Broker statements cannot be included in the definition of a Transact-SQL user-defined function:</span></span>  
  
    -   <span data-ttu-id="1d3d3-131">BEGIN DIALOG CONVERSATION</span><span class="sxs-lookup"><span data-stu-id="1d3d3-131">BEGIN DIALOG CONVERSATION</span></span>  
  
    -   <span data-ttu-id="1d3d3-132">END CONVERSATION</span><span class="sxs-lookup"><span data-stu-id="1d3d3-132">END CONVERSATION</span></span>  
  
    -   <span data-ttu-id="1d3d3-133">GET CONVERSATION GROUP</span><span class="sxs-lookup"><span data-stu-id="1d3d3-133">GET CONVERSATION GROUP</span></span>  
  
    -   <span data-ttu-id="1d3d3-134">MOVE CONVERSATION</span><span class="sxs-lookup"><span data-stu-id="1d3d3-134">MOVE CONVERSATION</span></span>  
  
    -   <span data-ttu-id="1d3d3-135">RECEIVE</span><span class="sxs-lookup"><span data-stu-id="1d3d3-135">RECEIVE</span></span>  
  
    -   <span data-ttu-id="1d3d3-136">SEND</span><span class="sxs-lookup"><span data-stu-id="1d3d3-136">SEND</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1d3d3-137">Security</span><span class="sxs-lookup"><span data-stu-id="1d3d3-137">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1d3d3-138">權限</span><span class="sxs-lookup"><span data-stu-id="1d3d3-138">Permissions</span></span>  
 <span data-ttu-id="1d3d3-139">需要資料庫中的 CREATE FUNCTION 權限，以及此函數建立所在之結構描述上的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-139">Requires CREATE FUNCTION permission in the database and ALTER permission on the schema in which the function is being created.</span></span> <span data-ttu-id="1d3d3-140">如果此函數指定使用者定義型別，則需要該型別的 EXECUTE 權限。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-140">If the function specifies a user-defined type, requires EXECUTE permission on the type.</span></span>  
  
##  <a name="scalar-functions"></a><a name="Scalar"></a><span data-ttu-id="1d3d3-141">純量函數</span><span class="sxs-lookup"><span data-stu-id="1d3d3-141">Scalar Functions</span></span>  
 <span data-ttu-id="1d3d3-142">下列範例會在 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 資料庫中建立多重陳述式純量函數。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-142">The following example creates a multistatement scalar function in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="1d3d3-143">這個函數使用了一個輸入值 `ProductID`，並傳回單一資料值，也就是指定產品的彙總存貨量。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-143">The function takes one input value, a `ProductID`, and returns a single data value, the aggregated quantity of the specified product in inventory.</span></span>  
  
```  
IF OBJECT_ID (N'dbo.ufnGetInventoryStock', N'FN') IS NOT NULL  
    DROP FUNCTION ufnGetInventoryStock;  
GO  
CREATE FUNCTION dbo.ufnGetInventoryStock(@ProductID int)  
RETURNS int   
AS   
-- Returns the stock level for the product.  
BEGIN  
    DECLARE @ret int;  
    SELECT @ret = SUM(p.Quantity)   
    FROM Production.ProductInventory p   
    WHERE p.ProductID = @ProductID   
        AND p.LocationID = '6';  
     IF (@ret IS NULL)   
        SET @ret = 0;  
    RETURN @ret;  
END;  
GO  
  
```  
  
 <span data-ttu-id="1d3d3-144">以下範例會使用 `ufnGetInventoryStock` 函數來傳回 `ProductModelID` 介於 75 和 80 之間的產品目前的存貨量。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-144">The following example uses the `ufnGetInventoryStock` function to return the current inventory quantity for products that have a `ProductModelID` between 75 and 80.</span></span>  
  
```  
SELECT ProductModelID, Name, dbo.ufnGetInventoryStock(ProductID)AS CurrentSupply  
FROM Production.Product  
WHERE ProductModelID BETWEEN 75 and 80;  
  
```  
  
##  <a name="table-valued-functions"></a><a name="TVF"></a><span data-ttu-id="1d3d3-145">資料表值函式</span><span class="sxs-lookup"><span data-stu-id="1d3d3-145">Table-Valued Functions</span></span>  
 <span data-ttu-id="1d3d3-146">下列範例會在 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 資料庫中建立內嵌資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-146">The following example creates an inline table-valued function in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="1d3d3-147">這個函數使用了一個輸入參數，也就是客戶 (商店) 識別碼，並傳回 `ProductID`和 `Name`資料行，以及從年初至今將每項產品銷售給商店的彙總銷售額 `YTD Total` 。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-147">The function takes one input parameter, a customer (store) ID, and returns the columns `ProductID`, `Name`, and the aggregate of year-to-date sales as `YTD Total` for each product sold to the store.</span></span>  
  
```  
IF OBJECT_ID (N'Sales.ufn_SalesByStore', N'IF') IS NOT NULL  
    DROP FUNCTION Sales.ufn_SalesByStore;  
GO  
CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
    FROM Production.Product AS P   
    JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
    JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
    JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
    WHERE C.StoreID = @storeid  
    GROUP BY P.ProductID, P.Name  
);  
  
```  
  
 <span data-ttu-id="1d3d3-148">下例會叫用這個函數並指定客戶識別碼 602。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-148">The following example invokes the function and specifies customer ID 602.</span></span>  
  
```  
SELECT * FROM Sales.ufn_SalesByStore (602);  
  
```  
  
 <span data-ttu-id="1d3d3-149">下列範例會在 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 資料庫中建立資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-149">The following example creates a table-valued function in the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="1d3d3-150">這個函數使用單一輸入參數 `EmployeeID` ，並傳回一份清單，列出這位指定員工的所有直接或間接下屬。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-150">The function takes a single input parameter, an `EmployeeID` and returns a list of all the employees who report to the specified employee directly or indirectly.</span></span> <span data-ttu-id="1d3d3-151">然後叫用此函數並指定員工識別碼 109。</span><span class="sxs-lookup"><span data-stu-id="1d3d3-151">The function is then invoked specifying employee ID 109.</span></span>  
  
```  
IF OBJECT_ID (N'dbo.ufn_FindReports', N'TF') IS NOT NULL  
    DROP FUNCTION dbo.ufn_FindReports;  
GO  
CREATE FUNCTION dbo.ufn_FindReports (@InEmpID INTEGER)  
RETURNS @retFindReports TABLE   
(  
    EmployeeID int primary key NOT NULL,  
    FirstName nvarchar(255) NOT NULL,  
    LastName nvarchar(255) NOT NULL,  
    JobTitle nvarchar(50) NOT NULL,  
    RecursionLevel int NOT NULL  
)  
--Returns a result set that lists all the employees who report to the   
--specific employee directly or indirectly.*/  
AS  
BEGIN  
WITH EMP_cte(EmployeeID, OrganizationNode, FirstName, LastName, JobTitle, RecursionLevel) -- CTE name and columns  
    AS (  
        SELECT e.BusinessEntityID, e.OrganizationNode, p.FirstName, p.LastName, e.JobTitle, 0 -- Get the initial list of Employees for Manager n  
        FROM HumanResources.Employee e   
INNER JOIN Person.Person p   
ON p.BusinessEntityID = e.BusinessEntityID  
        WHERE e.BusinessEntityID = @InEmpID  
        UNION ALL  
        SELECT e.BusinessEntityID, e.OrganizationNode, p.FirstName, p.LastName, e.JobTitle, RecursionLevel + 1 -- Join recursive member to anchor  
        FROM HumanResources.Employee e   
            INNER JOIN EMP_cte  
            ON e.OrganizationNode.GetAncestor(1) = EMP_cte.OrganizationNode  
INNER JOIN Person.Person p   
ON p.BusinessEntityID = e.BusinessEntityID  
        )  
-- copy the required columns to the result of the function   
   INSERT @retFindReports  
   SELECT EmployeeID, FirstName, LastName, JobTitle, RecursionLevel  
   FROM EMP_cte   
   RETURN  
END;  
GO  
-- Example invocation  
SELECT EmployeeID, FirstName, LastName, JobTitle, RecursionLevel  
FROM dbo.ufn_FindReports(1);  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d3d3-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d3d3-152">See Also</span></span>  
 <span data-ttu-id="1d3d3-153">[使用者定義函數](user-defined-functions.md) </span><span class="sxs-lookup"><span data-stu-id="1d3d3-153">[User-Defined Functions](user-defined-functions.md) </span></span>  
 [<span data-ttu-id="1d3d3-154">CREATE FUNCTION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1d3d3-154">CREATE FUNCTION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-function-transact-sql)  
  
  
