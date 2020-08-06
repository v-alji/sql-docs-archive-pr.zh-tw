---
title: 指定參數 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- parameters [SQL Server], stored procedures
- stored procedures [SQL Server], parameters
- output parameters [SQL Server]
- input parameters [SQL Server]
ms.assetid: 902314fe-5f9c-4d0d-a0b7-27e67c9c70ec
author: stevestein
ms.author: sstein
ms.openlocfilehash: d93a04281839c4db26cbab16ac166af3cdb7c9a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607354"
---
# <a name="specify-parameters"></a><span data-ttu-id="17bd2-102">指定參數</span><span class="sxs-lookup"><span data-stu-id="17bd2-102">Specify Parameters</span></span>
  <span data-ttu-id="17bd2-103">藉由指定程序參數，呼叫端程式就能夠將值傳入程序的主體。</span><span class="sxs-lookup"><span data-stu-id="17bd2-103">By specifying procedure parameters, calling programs are able to pass values into the body of the procedure.</span></span> <span data-ttu-id="17bd2-104">這些值在程序執行期間可用於各種用途。</span><span class="sxs-lookup"><span data-stu-id="17bd2-104">Those values can be used for a variety of purposes during procedure execution.</span></span> <span data-ttu-id="17bd2-105">如果程序參數標示為 OUTPUT 參數，程序參數也可以將值傳回給呼叫端程式。</span><span class="sxs-lookup"><span data-stu-id="17bd2-105">Procedure parameters can also return values to the calling program if the parameter is marked as an OUTPUT parameter.</span></span>  
  
 <span data-ttu-id="17bd2-106">程序最多可以有 2100 個參數，每個參數各被指派名稱、資料類型和方向。</span><span class="sxs-lookup"><span data-stu-id="17bd2-106">A procedure can have a maximum of 2100 parameters; each assigned a name, data type, and direction.</span></span> <span data-ttu-id="17bd2-107">您可以選擇性指派預設值給參數。</span><span class="sxs-lookup"><span data-stu-id="17bd2-107">Optionally, parameters can be assigned default values.</span></span>  
  
 <span data-ttu-id="17bd2-108">下節提供有關傳遞值至參數，以及在程序呼叫期間如何使用每個參數屬性的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="17bd2-108">The following section provides information about passing values into parameters and about how each of the parameter attributes is used during a procedure call.</span></span>  
  
## <a name="passing-values-into-parameters"></a><span data-ttu-id="17bd2-109">將值傳遞至參數</span><span class="sxs-lookup"><span data-stu-id="17bd2-109">Passing Values into Parameters</span></span>  
 <span data-ttu-id="17bd2-110">以程序呼叫提供的參數值必須是常數或變數，函數名稱不可做為參數值。</span><span class="sxs-lookup"><span data-stu-id="17bd2-110">The parameter values supplied with a procedure call must be constants or a variable; a function name cannot be used as a parameter value.</span></span> <span data-ttu-id="17bd2-111">變數可以是使用者定義的變數或系統變數，如 \@\@spid。</span><span class="sxs-lookup"><span data-stu-id="17bd2-111">Variables can be user-defined or system variables such as \@\@spid.</span></span>  
  
 <span data-ttu-id="17bd2-112">下列範例示範傳遞參數值至 `uspGetWhereUsedProductID`程序。</span><span class="sxs-lookup"><span data-stu-id="17bd2-112">The following examples demonstrate passing parameter values to the procedure `uspGetWhereUsedProductID`.</span></span> <span data-ttu-id="17bd2-113">這些範例說明如何以常數和變數方式傳遞參數，以及如何使用變數傳遞函數值。</span><span class="sxs-lookup"><span data-stu-id="17bd2-113">They illustrate how to pass parameters as constants and variables and also how to use a variable to pass the value of a function.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
-- Passing values as constants.  
EXEC dbo.uspGetWhereUsedProductID 819, '20050225';  
GO  
-- Passing values as variables.  
DECLARE @ProductID int, @CheckDate datetime;  
SET @ProductID = 819;  
SET @CheckDate = '20050225';  
EXEC dbo.uspGetWhereUsedProductID @ProductID, @CheckDate;  
GO  
-- Try to use a function as a parameter value.  
-- This produces an error message.  
EXEC dbo.uspGetWhereUsedProductID 819, GETDATE();  
GO  
-- Passing the function value as a variable.  
DECLARE @CheckDate datetime;  
SET @CheckDate = GETDATE();  
EXEC dbo.uspGetWhereUsedProductID 819, @CheckDate;  
GO  
```  
  
## <a name="specifying-parameter-names"></a><span data-ttu-id="17bd2-114">指定參數名稱</span><span class="sxs-lookup"><span data-stu-id="17bd2-114">Specifying Parameter Names</span></span>  
 <span data-ttu-id="17bd2-115">建立程序及宣告參數名稱時，參數名稱必須以一個 \@ 字元開始，而且在程序範圍中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="17bd2-115">When creating a procedure and declaring a parameter name, the parameter name must begin with a single \@ character and must be unique in the scope of the procedure.</span></span>  
  
 <span data-ttu-id="17bd2-116">明確為參數命名以及在程序呼叫中指定適當值給每個參數，就能以任何順序提供參數。</span><span class="sxs-lookup"><span data-stu-id="17bd2-116">Explicitly naming the parameters and assigning the appropriate values to each parameter in a procedure call allows the parameters to be supplied in any order.</span></span> <span data-ttu-id="17bd2-117">例如，如果 **my_proc** 程序預期有三個參數，名稱分別為 **\@first**、 **\@second** 和 **\@third**，您可以將傳遞給程序的值指派給參數名稱，例如：`EXECUTE my_proc @second = 2, @first = 1, @third = 3;`</span><span class="sxs-lookup"><span data-stu-id="17bd2-117">For example, if the procedure **my_proc** expects three parameters named **\@first**, **\@second**, and **\@third**, the values passed to the procedure can be assigned to the parameter names, such as: `EXECUTE my_proc @second = 2, @first = 1, @third = 3;`</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17bd2-118">如果以 **\@parameter =** _value_ 形式提供一個參數值，則所有後續的參數就必須按照此方式來提供。</span><span class="sxs-lookup"><span data-stu-id="17bd2-118">If one parameter value is supplied in the form **\@parameter =**_value_, all subsequent parameters must be supplied in this manner.</span></span> <span data-ttu-id="17bd2-119">如果不是以 **\@parameter =** _value_ 形式傳遞參數值，則提供值的順序就必須與 CREATE PROCEDURE 陳述式中列出參數的順序一樣 (由左到右)。</span><span class="sxs-lookup"><span data-stu-id="17bd2-119">If the parameter values are not passed in the form **\@parameter =**_value_, the values must be supplied in the identical order (left to right) as the parameters are listed in the CREATE PROCEDURE statement.</span></span>  
> 
> [!WARNING]
>  <span data-ttu-id="17bd2-120">任何以 **\@parameter =** _value_ 形式傳遞的參數若有拼字錯誤，就會讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 產生錯誤，並導致程序無法執行。</span><span class="sxs-lookup"><span data-stu-id="17bd2-120">Any parameter passed in the form **\@parameter =**_value_ with the parameter misspelled, will cause [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to generate an error and prevent procedure execution.</span></span>  
  
## <a name="specifying-parameter-data-types"></a><span data-ttu-id="17bd2-121">指定參數資料類型</span><span class="sxs-lookup"><span data-stu-id="17bd2-121">Specifying Parameter Data Types</span></span>  
 <span data-ttu-id="17bd2-122">在 CREATE PROCEDURE 陳述式中宣告時，參數必須定義一種資料類型。</span><span class="sxs-lookup"><span data-stu-id="17bd2-122">Parameters must be defined with a data type when they are declared in a CREATE PROCEDURE statement.</span></span> <span data-ttu-id="17bd2-123">參數的資料類型將決定在呼叫程序時參數可接受的值類型和範圍。</span><span class="sxs-lookup"><span data-stu-id="17bd2-123">The data type of a parameter determines the type and range of values that are accepted for the parameter when the procedure is called.</span></span> <span data-ttu-id="17bd2-124">例如，若將參數定義為 `tinyint` 資料類型，在傳遞數值至該參數時，只能接受 0 到 255 範圍內的數值。</span><span class="sxs-lookup"><span data-stu-id="17bd2-124">For example, if you define a parameter with a `tinyint` data type, only numeric values ranging from 0 to 255 are accepted when passed into that parameter.</span></span> <span data-ttu-id="17bd2-125">執行程序時，如果值與資料類型不相容的話，就會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="17bd2-125">An error is returned if a procedure is executed with a value incompatible with the data type.</span></span>  
  
## <a name="specifying-parameter-default-values"></a><span data-ttu-id="17bd2-126">指定參數預設值</span><span class="sxs-lookup"><span data-stu-id="17bd2-126">Specifying Parameter Default Values</span></span>  
 <span data-ttu-id="17bd2-127">如果在宣告時，已指定參數的預設值，此參數視為選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="17bd2-127">A parameter is considered optional if the parameter has a default value specified when it is declared.</span></span> <span data-ttu-id="17bd2-128">在程序呼叫中，不需要提供值給選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="17bd2-128">It is not necessary to provide a value for an optional parameter in a procedure call.</span></span>  
  
 <span data-ttu-id="17bd2-129">在下列情況下會使用參數的預設值：</span><span class="sxs-lookup"><span data-stu-id="17bd2-129">The default value of a parameter is used when:</span></span>  
  
-   <span data-ttu-id="17bd2-130">在程序呼叫中未指定參數值。</span><span class="sxs-lookup"><span data-stu-id="17bd2-130">No value for the parameter is specified in the procedure call.</span></span>  
  
-   <span data-ttu-id="17bd2-131">程序呼叫中指定 DEFAULT 關鍵字做為值。</span><span class="sxs-lookup"><span data-stu-id="17bd2-131">The DEFAULT keyword is specified as the value in the procedure call.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17bd2-132">如果預設值是包含內嵌空白或標點的字串，或是以數字開頭 (例如 6xxx)，就必須將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="17bd2-132">If the default value is a character string that contains embedded blanks or punctuation, or if it starts with a number (for example, 6xxx), it must be enclosed in single, straight quotation marks.</span></span>  
  
 <span data-ttu-id="17bd2-133">如果無法指定適當的數值做為參數的預設值，您可以指定 NULL 做為預設值。</span><span class="sxs-lookup"><span data-stu-id="17bd2-133">If no value can be specified appropriately as a default for the parameter, specify NULL as the default.</span></span> <span data-ttu-id="17bd2-134">在沒有參數值的狀況下執行程序時，最好讓程序傳回自訂的訊息</span><span class="sxs-lookup"><span data-stu-id="17bd2-134">It is a good idea to have the procedure return a customized message if the procedure is executed without a value for the parameter.</span></span>  
  
 <span data-ttu-id="17bd2-135">下列範例使用一個輸入參數 `usp_GetSalesYTD` 來建立 `@SalesPerson`程序。</span><span class="sxs-lookup"><span data-stu-id="17bd2-135">The following example creates the `usp_GetSalesYTD` procedure with one input parameter, `@SalesPerson`.</span></span> <span data-ttu-id="17bd2-136">NULL 做為預設值指派給參數，並用於錯誤處理陳述式，以便在未指定值給 `@SalesPerson` 參數而執行程序時，傳回自訂錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="17bd2-136">NULL is assigned as the default value for the parameter and is used in error handling statements to return a custom error message for cases when the procedure is executed without a value for the `@SalesPerson` parameter.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID('Sales.uspGetSalesYTD', 'P') IS NOT NULL  
    DROP PROCEDURE Sales.uspGetSalesYTD;  
GO  
CREATE PROCEDURE Sales.uspGetSalesYTD  
@SalesPerson nvarchar(50) = NULL  -- NULL default value  
AS   
    SET NOCOUNT ON;   
  
-- Validate the @SalesPerson parameter.  
IF @SalesPerson IS NULL  
BEGIN  
   PRINT 'ERROR: You must specify the last name of the sales person.'  
   RETURN  
END  
-- Get the sales for the specified sales person and   
-- assign it to the output parameter.  
SELECT SalesYTD  
FROM Sales.SalesPerson AS sp  
JOIN HumanResources.vEmployee AS e ON e.BusinessEntityID = sp.BusinessEntityID  
WHERE LastName = @SalesPerson;  
RETURN  
GO  
  
```  
  
 <span data-ttu-id="17bd2-137">下列範例執行此程序。</span><span class="sxs-lookup"><span data-stu-id="17bd2-137">The following example executes the procedure.</span></span> <span data-ttu-id="17bd2-138">第一個陳述式會在不指定輸入值的情況下執行程序。</span><span class="sxs-lookup"><span data-stu-id="17bd2-138">The first statement executes the procedure without specifying an input value.</span></span> <span data-ttu-id="17bd2-139">這將造成程序中的錯誤處理陳述式傳回自訂錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="17bd2-139">This causes the error handling statements in the procedure to return the custom error message.</span></span> <span data-ttu-id="17bd2-140">第二個陳述式則提供輸入值並傳回預期的結果集。</span><span class="sxs-lookup"><span data-stu-id="17bd2-140">The second statement supplies an input value and returns the expected result set.</span></span>  
  
```  
-- Run the procedure without specifying an input value.  
EXEC Sales.usp_GetSalesYTD;  
GO  
-- Run the procedure with an input value.  
EXEC Sales.usp_GetSalesYTD N'Blythe';  
GO  
```  
  
 <span data-ttu-id="17bd2-141">雖然可以省略已提供預設值的參數，但只能截斷參數清單。</span><span class="sxs-lookup"><span data-stu-id="17bd2-141">Although parameters for which defaults have been supplied can be omitted, the list of parameters can only be truncated.</span></span> <span data-ttu-id="17bd2-142">例如，如果程序有五個參數，第四個和第五個參數可以省略。</span><span class="sxs-lookup"><span data-stu-id="17bd2-142">For example, if a procedure has five parameters, both the fourth and the fifth parameters can be omitted.</span></span> <span data-ttu-id="17bd2-143">但除非是以 **\@parameter =** _value_ 形式提供參數，否則只要包含第五個參數，就不能省略第四個參數。</span><span class="sxs-lookup"><span data-stu-id="17bd2-143">However the fourth parameter cannot be skipped as long as the fifth parameter is included, unless the parameters are supplied in the form **\@parameter =**_value_.</span></span>  
  
## <a name="specifying-parameter-direction"></a><span data-ttu-id="17bd2-144">指定參數方向</span><span class="sxs-lookup"><span data-stu-id="17bd2-144">Specifying Parameter Direction</span></span>  
 <span data-ttu-id="17bd2-145">參數的方向可以是輸入或輸出，前者指將值傳入程序的主體，後者則指程序傳回值給呼叫端程式。</span><span class="sxs-lookup"><span data-stu-id="17bd2-145">The direction of a parameter is either input, a value is passed into the body of the procedure, or output, the procedure returns a value to the calling program.</span></span> <span data-ttu-id="17bd2-146">預設是輸入參數。</span><span class="sxs-lookup"><span data-stu-id="17bd2-146">The default is an input parameter.</span></span>  
  
 <span data-ttu-id="17bd2-147">若要指定輸出參數，必須在 CREATE PROCEDURE 陳述式的參數定義中指定 OUTPUT 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="17bd2-147">To specify an output parameter, the OUTPUT keyword must be specified in the definition of the parameter in the CREATE PROCEDURE statement.</span></span> <span data-ttu-id="17bd2-148">程序結束時，會將輸出參數目前的值傳回給呼叫端程式。</span><span class="sxs-lookup"><span data-stu-id="17bd2-148">The procedure returns the current value of the output parameter to the calling program when the procedure exits.</span></span> <span data-ttu-id="17bd2-149">呼叫端程式在執行程序時，也必須使用 OUTPUT 關鍵字，才能將參數值儲存在變數中，供呼叫端程式使用。</span><span class="sxs-lookup"><span data-stu-id="17bd2-149">The calling program must also use the OUTPUT keyword when executing the procedure to save the parameter's value in a variable that can be used in the calling program.</span></span>  
  
 <span data-ttu-id="17bd2-150">下列範例建立 `Production.usp`_`GetList` 程序，傳回價格不超過指定金額的產品清單。</span><span class="sxs-lookup"><span data-stu-id="17bd2-150">The following example creates the `Production.usp`_`GetList` procedure, which returns a list of products that have prices that do not exceed a specified amount.</span></span> <span data-ttu-id="17bd2-151">此範例顯示使用多個 SELECT 陳述式和多個 OUTPUT 參數。</span><span class="sxs-lookup"><span data-stu-id="17bd2-151">The example shows using multiple SELECT statements and multiple OUTPUT parameters.</span></span> <span data-ttu-id="17bd2-152">OUTPUT 參數可以讓外部程序、批次或一個以上的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式在程序執行過程中存取某一值集。</span><span class="sxs-lookup"><span data-stu-id="17bd2-152">OUTPUT parameters allow an external procedure, a batch, or more than one [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to access a value set during the procedure execution.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'Production.uspGetList', 'P' ) IS NOT NULL   
    DROP PROCEDURE Production.uspGetList;  
GO  
CREATE PROCEDURE Production.uspGetList @Product varchar(40)   
    , @MaxPrice money   
    , @ComparePrice money OUTPUT  
    , @ListPrice money OUT  
AS  
    SET NOCOUNT ON;  
    SELECT p.[Name] AS Product, p.ListPrice AS 'List Price'  
    FROM Production.Product AS p  
    JOIN Production.ProductSubcategory AS s   
      ON p.ProductSubcategoryID = s.ProductSubcategoryID  
    WHERE s.[Name] LIKE @Product AND p.ListPrice < @MaxPrice;  
-- Populate the output variable @ListPprice.  
SET @ListPrice = (SELECT MAX(p.ListPrice)  
        FROM Production.Product AS p  
        JOIN  Production.ProductSubcategory AS s   
          ON p.ProductSubcategoryID = s.ProductSubcategoryID  
        WHERE s.[Name] LIKE @Product AND p.ListPrice < @MaxPrice);  
-- Populate the output variable @compareprice.  
SET @ComparePrice = @MaxPrice;  
GO  
  
```  
  
 <span data-ttu-id="17bd2-153">執行 `usp_GetList` 以傳回成本低於 $700 的 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] 產品 (自行車) 清單。</span><span class="sxs-lookup"><span data-stu-id="17bd2-153">Execute `usp_GetList` to return a list of [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] products (Bikes) that cost less than $700.</span></span> <span data-ttu-id="17bd2-154">OUTPUT 參數 **\@cost** 和 **\@compareprices** 會搭配流程控制語言使用，以便在 [訊息] 視窗中傳回訊息。</span><span class="sxs-lookup"><span data-stu-id="17bd2-154">The OUTPUT parameters **\@cost** and **\@compareprices** are used with control-of-flow language to return a message in the **Messages** window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17bd2-155">在建立程序過程以及在使用變數過程中，必須定義 OUTPUT 變數。</span><span class="sxs-lookup"><span data-stu-id="17bd2-155">The OUTPUT variable must be defined during the procedure creation and also during the use of the variable.</span></span> <span data-ttu-id="17bd2-156">參數名稱和變數名稱不一定要相符。</span><span class="sxs-lookup"><span data-stu-id="17bd2-156">The parameter name and variable name do not have to match.</span></span> <span data-ttu-id="17bd2-157">但是，資料類型和參數定位必須相符 (除非使用 **\@listprice=** _variable_)。</span><span class="sxs-lookup"><span data-stu-id="17bd2-157">However, the data type and parameter positioning must match (unless **\@listprice=** _variable_ is used).</span></span>  
  
```  
DECLARE @ComparePrice money, @Cost money ;  
EXECUTE Production.uspGetList '%Bikes%', 700,   
    @ComparePrice OUT,   
    @Cost OUTPUT  
IF @Cost <= @ComparePrice   
BEGIN  
    PRINT 'These products can be purchased for less than   
    $'+RTRIM(CAST(@ComparePrice AS varchar(20)))+'.'  
END  
ELSE  
    PRINT 'The prices for all products in this category exceed   
    $'+ RTRIM(CAST(@ComparePrice AS varchar(20)))+'.';  
  
```  
  
 <span data-ttu-id="17bd2-158">部分結果集如下：</span><span class="sxs-lookup"><span data-stu-id="17bd2-158">Here is the partial result set:</span></span>  
  
```  
Product                                            List Price  
-------------------------------------------------- ------------------  
Road-750 Black, 58                                 539.99  
Mountain-500 Silver, 40                            564.99  
Mountain-500 Silver, 42                            564.99  
...  
Road-750 Black, 48                                 539.99  
Road-750 Black, 52                                 539.99  
  
(14 row(s) affected)  
  
These items can be purchased for less than $700.00.  
```  
  
## <a name="see-also"></a><span data-ttu-id="17bd2-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17bd2-159">See Also</span></span>  
 [<span data-ttu-id="17bd2-160">CREATE PROCEDURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="17bd2-160">CREATE PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-procedure-transact-sql)  
  
  
