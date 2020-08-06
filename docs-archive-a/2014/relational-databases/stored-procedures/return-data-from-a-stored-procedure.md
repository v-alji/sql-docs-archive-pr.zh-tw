---
title: 從預存程序傳回資料 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], returning data
- returning data from stored procedure
ms.assetid: 7a428ffe-cd87-4f42-b3f1-d26aa8312bf7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 472ca5cf27f7e7ea2b18daa961c19faadcf2251f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607355"
---
# <a name="return-data-from-a-stored-procedure"></a><span data-ttu-id="5c0ce-102">從預存程序傳回資料</span><span class="sxs-lookup"><span data-stu-id="5c0ce-102">Return Data from a Stored Procedure</span></span>
  <span data-ttu-id="5c0ce-103">將結果集或資料從程序傳回至呼叫端程式的方式有兩種：輸出參數和傳回碼。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-103">There are two ways of returning result sets or data from a procedure to a calling program: output parameters and return codes.</span></span> <span data-ttu-id="5c0ce-104">本主題提供有關這兩種方法的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-104">This topic provides information on both approaches.</span></span>  
  
## <a name="returning-data-using-an-output-parameter"></a><span data-ttu-id="5c0ce-105">使用輸出參數傳回資料</span><span class="sxs-lookup"><span data-stu-id="5c0ce-105">Returning Data Using an Output Parameter</span></span>  
 <span data-ttu-id="5c0ce-106">如果在程序定義中為參數指定 OUTPUT 關鍵字，程序就可以在結束時將參數目前的值傳回至呼叫端程式。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-106">If you specify the OUTPUT keyword for a parameter in the procedure definition, the procedure can return the current value of the parameter to the calling program when the procedure exits.</span></span> <span data-ttu-id="5c0ce-107">若要將參數值儲存在可供呼叫端程式使用的變數中，呼叫端程式在執行程序時必須使用 OUTPUT 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-107">To save the value of the parameter in a variable that can be used in the calling program, the calling program must use the OUTPUT keyword when executing the procedure.</span></span> <span data-ttu-id="5c0ce-108">如需何種資料類型可做為輸出參數的詳細資訊，請參閱 [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-108">For more information about what data types can be used as output parameters, see [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql).</span></span>  
  
### <a name="examples-of-output-parameter"></a><span data-ttu-id="5c0ce-109">輸出參數範例</span><span class="sxs-lookup"><span data-stu-id="5c0ce-109">Examples of Output Parameter</span></span>  
 <span data-ttu-id="5c0ce-110">下列範例示範的程序有一個輸入參數和一個輸出參數。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-110">The following example shows a procedure with an input and an output parameter.</span></span> <span data-ttu-id="5c0ce-111">`@SalesPerson` 參數會接收呼叫端程式所指定的輸入值。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-111">The `@SalesPerson` parameter would receive an input value specified by the calling program.</span></span> <span data-ttu-id="5c0ce-112">SELECT 陳述式使用傳入輸入參數的值，來取得正確的 `SalesYTD` 值。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-112">The SELECT statement uses the value passed into the input parameter to obtain the correct `SalesYTD` value.</span></span> <span data-ttu-id="5c0ce-113">SELECT 陳述式也會將值指派給 `@SalesYTD` 輸出參數，以便在程序結束時，將值傳回給呼叫端程式。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-113">The SELECT statement also assigns the value to the `@SalesYTD` output parameter, which returns the value to the calling program when the procedure exits.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID('Sales.uspGetEmployeeSalesYTD', 'P') IS NOT NULL  
    DROP PROCEDURE Sales.uspGetEmployeeSalesYTD;  
GO  
CREATE PROCEDURE Sales.uspGetEmployeeSalesYTD  
@SalesPerson nvarchar(50),  
@SalesYTD money OUTPUT  
AS    
  
    SET NOCOUNT ON;  
    SELECT @SalesYTD = SalesYTD  
    FROM Sales.SalesPerson AS sp  
    JOIN HumanResources.vEmployee AS e ON e.BusinessEntityID = sp.BusinessEntityID  
    WHERE LastName = @SalesPerson;  
RETURN  
GO  
  
```  
  
 <span data-ttu-id="5c0ce-114">下列範例會呼叫第一個範例中所建立的程序，並將被呼叫程序所傳回的輸出值儲存至呼叫端程式的區域變數 `@SalesYTD` 。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-114">The following example calls the procedure created in the first example and saves the output value returned from the called procedure in the `@SalesYTD` variable, which is local to the calling program.</span></span>  
  
```  
-- Declare the variable to receive the output value of the procedure.  
DECLARE @SalesYTDBySalesPerson money;  
-- Execute the procedure specifying a last name for the input parameter  
-- and saving the output value in the variable @SalesYTDBySalesPerson  
EXECUTE Sales.uspGetEmployeeSalesYTD  
    N'Blythe', @SalesYTD = @SalesYTDBySalesPerson OUTPUT;  
-- Display the value returned by the procedure.  
PRINT 'Year-to-date sales for this employee is ' +   
    convert(varchar(10),@SalesYTDBySalesPerson);  
GO  
  
```  
  
 <span data-ttu-id="5c0ce-115">執行程序時，也可以對 OUTPUT 參數指定輸入值。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-115">Input values can also be specified for OUTPUT parameters when the procedure is executed.</span></span> <span data-ttu-id="5c0ce-116">這可讓程序接收來自呼叫端程式的值，變更值或對值執行作業，然後將新值傳回給呼叫端程式。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-116">This allows the procedure to receive a value from the calling program, change or perform operations with the value, and then return the new value to the calling program.</span></span> <span data-ttu-id="5c0ce-117">在上述範例中，在程式呼叫 `@SalesYTDBySalesPerson` 程序之前，可先指派 `Sales.uspGetEmployeeSalesYTD` 變數的值。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-117">In the previous example, the `@SalesYTDBySalesPerson` variable can be assigned a value before the program calls the `Sales.uspGetEmployeeSalesYTD` procedure.</span></span> <span data-ttu-id="5c0ce-118">EXECUTE 陳述式就會將 `@SalesYTDBySalesPerson` 變數值傳入 `@SalesYTD` OUTPUT 參數。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-118">The execute statement would pass the `@SalesYTDBySalesPerson` variable value into the `@SalesYTD` OUTPUT parameter.</span></span> <span data-ttu-id="5c0ce-119">然後在程序主體中，此值可用於產生新值的計算。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-119">Then in the procedure body, the value could be used for calculations that generate a new value.</span></span> <span data-ttu-id="5c0ce-120">程序結束時，新值可透過 OUTPUT 參數從程序傳回，更新 `@SalesYTDBySalesPerson` 變數中的值。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-120">The new value would be passed back out of the procedure through the OUTPUT parameter, updating the value in the `@SalesYTDBySalesPerson` variable when the procedure exits.</span></span> <span data-ttu-id="5c0ce-121">這通常稱為「以傳址方式傳遞的能力」。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-121">This is often referred to as "pass-by-reference capability."</span></span>  
  
 <span data-ttu-id="5c0ce-122">呼叫程序時，如果您對參數指定 OUTPUT，但該參數在程序定義中並未使用 OUTPUT 來定義，則會出現錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-122">If you specify OUTPUT for a parameter when you call a procedure and that parameter is not defined by using OUTPUT in the procedure definition, you get an error message.</span></span> <span data-ttu-id="5c0ce-123">不過，您可以用輸出參數來執行程序，但在執行程序時不指定 OUTPUT。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-123">However, you can execute a procedure with output parameters and not specify OUTPUT when executing the procedure.</span></span> <span data-ttu-id="5c0ce-124">這樣不會傳回錯誤，但您不能在呼叫程式中使用輸出值。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-124">No error is returned, but you cannot use the output value in the calling program.</span></span>  
  
### <a name="using-the-cursor-data-type-in-output-parameters"></a><span data-ttu-id="5c0ce-125">在 OUTPUT 參數中使用 Cursor 資料類型</span><span class="sxs-lookup"><span data-stu-id="5c0ce-125">Using the Cursor Data Type in OUTPUT Parameters</span></span>  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)]<span data-ttu-id="5c0ce-126">程式只能使用 `cursor` 輸出參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-126">procedures can use the `cursor` data type only for OUTPUT parameters.</span></span> <span data-ttu-id="5c0ce-127">如果為 `cursor` 參數指定了資料類型，則必須在程序定義中指定該參數的不同和輸出關鍵字。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-127">If the `cursor` data type is specified for a parameter, both the VARYING and OUTPUT keywords must be specified for that parameter in the procedure definition.</span></span> <span data-ttu-id="5c0ce-128">參數可以指定為僅 OUTPUT，但如果在參數宣告中指定了不同的關鍵字，則資料類型必須是 `cursor` ，而且也必須指定 OUTPUT 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-128">A parameter can be specified as only OUTPUT but if the VARYING keyword is specified in the parameter declaration, the data type must be `cursor` and the OUTPUT keyword must also be specified.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5c0ce-129">`cursor` 資料類型不可透過 OLE DB、ODBC、ADO 以及 DB-Library 之類的資料庫 API 繫結至應用程式變數。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-129">The `cursor` data type cannot be bound to application variables through the database APIs such as OLE DB, ODBC, ADO, and DB-Library.</span></span> <span data-ttu-id="5c0ce-130">因為必須先繫結 OUTPUT 參數，然後應用程式才能執行程序，所以不能從資料庫 API 呼叫具有 `cursor` OUTPUT 參數的程序。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-130">Because OUTPUT parameters must be bound before an application can execute a procedure, procedures with `cursor` OUTPUT parameters cannot be called from the database APIs.</span></span> <span data-ttu-id="5c0ce-131">只有當 `cursor` OUTPUT 變數指定給 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 本機 `cursor` 變數時，才可以從 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 批次、程序或觸發程序呼叫這些程序。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-131">These procedures can be called from [!INCLUDE[tsql](../../../includes/tsql-md.md)] batches, procedures, or triggers only when the `cursor` OUTPUT variable is assigned to a [!INCLUDE[tsql](../../../includes/tsql-md.md)] local `cursor` variable.</span></span>  
  
### <a name="rules-for-cursor-output-parameters"></a><span data-ttu-id="5c0ce-132">Cursor 輸出參數的規則</span><span class="sxs-lookup"><span data-stu-id="5c0ce-132">Rules for Cursor Output Parameters</span></span>  
 <span data-ttu-id="5c0ce-133">以下規則是有關程序執行時的 `cursor` 輸出參數：</span><span class="sxs-lookup"><span data-stu-id="5c0ce-133">The following rules pertain to `cursor` output parameters when the procedure is executed:</span></span>  
  
-   <span data-ttu-id="5c0ce-134">順向資料指標的結果集之中只會傳回程序執行結束時，位於或超過資料指標所在位置的資料列，例如：</span><span class="sxs-lookup"><span data-stu-id="5c0ce-134">For a forward-only cursor, the rows returned in the cursor's result set are only those rows at and beyond the position of the cursor at the conclusion of the procedure execution, for example:</span></span>  
  
    -   <span data-ttu-id="5c0ce-135">一個無法捲動的資料指標在 RS 結果集 (有 100 個資料列) 的程序中開啟。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-135">A nonscrollable cursor is opened in a procedure on a result set named RS of 100 rows.</span></span>  
  
    -   <span data-ttu-id="5c0ce-136">此程序擷取 RS 結果集的前 5 個資料列。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-136">The procedure fetches the first 5 rows of result set RS.</span></span>  
  
    -   <span data-ttu-id="5c0ce-137">此程序傳回呼叫者。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-137">The procedure returns to its caller.</span></span>  
  
    -   <span data-ttu-id="5c0ce-138">傳回呼叫者的 RS 結果集是由 RS 的第 6 到第 100 個資料列所構成，而呼叫者中的資料指標位於 RS 的第一個資料列之前。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-138">The result set RS returned to the caller consists of rows from 6 through 100 of RS, and the cursor in the caller is positioned before the first row of RS.</span></span>  
  
-   <span data-ttu-id="5c0ce-139">如果順向資料指標在程序結束時位於第一個資料列之前，整個結果集都會傳回至呼叫的批次、程序或觸發程序。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-139">For a forward-only cursor, if the cursor is positioned before the first row when the procedure exits, the entire result set is returned to the calling batch, procedure, or trigger.</span></span> <span data-ttu-id="5c0ce-140">傳回時，資料指標的位置會設定在第一個資料列之前。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-140">When returned, the cursor position is set before the first row.</span></span>  
  
-   <span data-ttu-id="5c0ce-141">如果順向資料指標在程序結束時位於最後一個資料列之後，便會將空的結果集傳回至呼叫的批次、程序或觸發程序。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-141">For a forward-only cursor, if the cursor is positioned beyond the end of the last row when the procedure exits, an empty result set is returned to the calling batch, procedure, or trigger.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5c0ce-142">空的結果集與 Null 值是不同的。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-142">An empty result set is not the same as a null value.</span></span>  
  
-   <span data-ttu-id="5c0ce-143">如果是可捲動的資料指標，結果集之中的所有資料列都會在程序結束時傳回至呼叫的批次、程序或觸發程序。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-143">For a scrollable cursor, all the rows in the result set are returned to the calling batch, procedure, or trigger when the procedure exits.</span></span> <span data-ttu-id="5c0ce-144">傳回時，資料指標會留在程序中執行最後一次擷取的位置。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-144">When returned, the cursor position is left at the position of the last fetch executed in the procedure.</span></span>  
  
-   <span data-ttu-id="5c0ce-145">任何類型的資料指標關閉時，都會將 Null 值傳回至呼叫的批次、程序或觸發程序。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-145">For any type of cursor, if the cursor is closed, then a null value is passed back to the calling batch, procedure, or trigger.</span></span> <span data-ttu-id="5c0ce-146">如果將資料指標指派給某個參數但該資料指標從未開啟時，也會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-146">This will also be the case if a cursor is assigned to a parameter, but that cursor is never opened.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5c0ce-147">關閉的狀態只在傳回時有影響。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-147">The closed state matters only at return time.</span></span> <span data-ttu-id="5c0ce-148">舉例來說，在程序執行到一半時關閉資料指標，之後又開啟，然後將該資料指標的結果集傳回至呼叫的批次、程序或觸發程序，這些都是有效的。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-148">For example, it is valid to close a cursor part of the way through the procedure, to open it again later in the procedure, and return that cursor's result set to the calling batch, procedure, or trigger.</span></span>  
  
### <a name="examples-of-cursor-output-parameters"></a><span data-ttu-id="5c0ce-149">Cursor 輸出參數的範例</span><span class="sxs-lookup"><span data-stu-id="5c0ce-149">Examples of Cursor Output Parameters</span></span>  
 <span data-ttu-id="5c0ce-150">在下列範例中，會建立 `@currency` `cursor` 使用資料類型指定輸出參數 _ 的程式 `cursor` 。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-150">In the following example, a procedure is created that specified an output parameter, `@currency`_`cursor` using the `cursor` data type.</span></span> <span data-ttu-id="5c0ce-151">然後在批次中呼叫程序。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-151">The procedure is then called in a batch.</span></span>  
  
 <span data-ttu-id="5c0ce-152">首先，建立在 Currency 資料表上宣告並隨後開啟資料指標的程序。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-152">First, create the procedure that declares and then opens a cursor on the Currency table.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'dbo.uspCurrencyCursor', 'P' ) IS NOT NULL  
    DROP PROCEDURE dbo.uspCurrencyCursor;  
GO  
CREATE PROCEDURE dbo.uspCurrencyCursor   
    @CurrencyCursor CURSOR VARYING OUTPUT  
AS  
    SET NOCOUNT ON;  
    SET @CurrencyCursor = CURSOR  
    FORWARD_ONLY STATIC FOR  
      SELECT CurrencyCode, Name  
      FROM Sales.Currency;  
    OPEN @CurrencyCursor;  
GO  
  
```  
  
 <span data-ttu-id="5c0ce-153">接下來，執行一個宣告區域資料指標變數的批次、執行此程序將資料指標指派給區域變數，再從資料指標擷取資料列。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-153">Next, execute a batch that declares a local cursor variable, executes the procedure to assign the cursor to the local variable, and then fetches the rows from the cursor.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @MyCursor CURSOR;  
EXEC dbo.uspCurrencyCursor @CurrencyCursor = @MyCursor OUTPUT;  
WHILE (@@FETCH_STATUS = 0)  
BEGIN;  
     FETCH NEXT FROM @MyCursor;  
END;  
CLOSE @MyCursor;  
DEALLOCATE @MyCursor;  
GO  
  
```  
  
## <a name="returning-data-using-a-return-code"></a><span data-ttu-id="5c0ce-154">使用傳回碼傳回資料</span><span class="sxs-lookup"><span data-stu-id="5c0ce-154">Returning Data Using a Return Code</span></span>  
 <span data-ttu-id="5c0ce-155">程序可以傳回稱為傳回碼的整數值，以指出程序的執行狀態。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-155">A procedure can return an integer value called a return code to indicate the execution status of a procedure.</span></span> <span data-ttu-id="5c0ce-156">若要為程序指定傳回碼，請使用 RETURN 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-156">You specify the return code for a procedure using the RETURN statement.</span></span> <span data-ttu-id="5c0ce-157">就像使用 OUTPUT 參數一樣，若要在呼叫端程式中使用傳回碼，您必須在執行程序時將傳回碼儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-157">As with OUTPUT parameters, you must save the return code in a variable when the procedure is executed in order to use the return code value in the calling program.</span></span> <span data-ttu-id="5c0ce-158">例如，資料類型的指派變數 `@result` `int` 是用來儲存程式的傳回碼 `my_proc` ，例如：</span><span class="sxs-lookup"><span data-stu-id="5c0ce-158">For example, the assignment variable `@result` of data type `int` is used to store the return code from the procedure `my_proc`, such as:</span></span>  
  
```  
DECLARE @result int;  
EXECUTE @result = my_proc;  
```  
  
 <span data-ttu-id="5c0ce-159">傳回碼常用於程序的流程控制區塊中，以設定每個可能錯誤狀況的傳回碼值。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-159">Return codes are commonly used in control-of-flow blocks within procedures to set the return code value for each possible error situation.</span></span> <span data-ttu-id="5c0ce-160">您可以在 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式之後使用 @@ERROR，來偵測陳述式執行過程中是否曾發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-160">You can use the @@ERROR function after a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement to detect whether an error occurred during the execution of the statement.</span></span>  
  
### <a name="examples-of-return-codes"></a><span data-ttu-id="5c0ce-161">傳回碼的範例</span><span class="sxs-lookup"><span data-stu-id="5c0ce-161">Examples of Return Codes</span></span>  
 <span data-ttu-id="5c0ce-162">下列範例顯示具有可為各種錯誤設定特別傳回碼值之錯誤處理的 `usp_GetSalesYTD` 程序。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-162">The following example shows the `usp_GetSalesYTD` procedure with error handling that sets special return code values for various errors.</span></span> <span data-ttu-id="5c0ce-163">下表顯示由程序指派給每個可能錯誤的整數值，以及每個值對應的意義。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-163">The following table shows the integer value that is assigned by the procedure to each possible error, and the corresponding meaning for each value.</span></span>  
  
|<span data-ttu-id="5c0ce-164">傳回碼值</span><span class="sxs-lookup"><span data-stu-id="5c0ce-164">Return code value</span></span>|<span data-ttu-id="5c0ce-165">意義</span><span class="sxs-lookup"><span data-stu-id="5c0ce-165">Meaning</span></span>|  
|-----------------------|-------------|  
|<span data-ttu-id="5c0ce-166">0</span><span class="sxs-lookup"><span data-stu-id="5c0ce-166">0</span></span>|<span data-ttu-id="5c0ce-167">成功執行。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-167">Successful execution.</span></span>|  
|<span data-ttu-id="5c0ce-168">1</span><span class="sxs-lookup"><span data-stu-id="5c0ce-168">1</span></span>|<span data-ttu-id="5c0ce-169">未指定必要的參數值。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-169">Required parameter value is not specified.</span></span>|  
|<span data-ttu-id="5c0ce-170">2</span><span class="sxs-lookup"><span data-stu-id="5c0ce-170">2</span></span>|<span data-ttu-id="5c0ce-171">指定的參數值無效。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-171">Specified parameter value is not valid.</span></span>|  
|<span data-ttu-id="5c0ce-172">3</span><span class="sxs-lookup"><span data-stu-id="5c0ce-172">3</span></span>|<span data-ttu-id="5c0ce-173">取得銷售值時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-173">Error has occurred getting sales value.</span></span>|  
|<span data-ttu-id="5c0ce-174">4</span><span class="sxs-lookup"><span data-stu-id="5c0ce-174">4</span></span>|<span data-ttu-id="5c0ce-175">銷售人員有 NULL 銷售值。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-175">NULL sales value found for the salesperson.</span></span>|  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID('Sales.usp_GetSalesYTD', 'P') IS NOT NULL  
    DROP PROCEDURE Sales.usp_GetSalesYTD;  
GO  
CREATE PROCEDURE Sales.usp_GetSalesYTD  
@SalesPerson nvarchar(50) = NULL,  -- NULL default value  
@SalesYTD money = NULL OUTPUT  
AS    
  
-- Validate the @SalesPerson parameter.  
IF @SalesPerson IS NULL  
   BEGIN  
       PRINT 'ERROR: You must specify a last name for the sales person.'  
       RETURN(1)  
   END  
ELSE  
   BEGIN  
   -- Make sure the value is valid.  
   IF (SELECT COUNT(*) FROM HumanResources.vEmployee  
          WHERE LastName = @SalesPerson) = 0  
      RETURN(2)  
   END  
-- Get the sales for the specified name and   
-- assign it to the output parameter.  
SELECT @SalesYTD = SalesYTD   
FROM Sales.SalesPerson AS sp  
JOIN HumanResources.vEmployee AS e ON e.BusinessEntityID = sp.BusinessEntityID  
WHERE LastName = @SalesPerson;  
-- Check for SQL Server errors.  
IF @@ERROR <> 0   
   BEGIN  
      RETURN(3)  
   END  
ELSE  
   BEGIN  
   -- Check to see if the ytd_sales value is NULL.  
     IF @SalesYTD IS NULL  
       RETURN(4)   
     ELSE  
      -- SUCCESS!!  
        RETURN(0)  
   END  
-- Run the stored procedure without specifying an input value.  
EXEC Sales.usp_GetSalesYTD;  
GO  
-- Run the stored procedure with an input value.  
DECLARE @SalesYTDForSalesPerson money, @ret_code int;  
-- Execute the procedure specifying a last name for the input parameter  
-- and saving the output value in the variable @SalesYTD  
EXECUTE Sales.usp_GetSalesYTD  
    N'Blythe', @SalesYTD = @SalesYTDForSalesPerson OUTPUT;  
PRINT N'Year-to-date sales for this employee is ' +  
    CONVERT(varchar(10), @SalesYTDForSalesPerson);  
  
```  
  
 <span data-ttu-id="5c0ce-176">下列範例會建立程式以處理從 `usp_GetSalesYTD` 程序傳回的傳回碼。</span><span class="sxs-lookup"><span data-stu-id="5c0ce-176">The following example creates a program to handle the return codes that are returned from the `usp_GetSalesYTD` procedure.</span></span>  
  
```  
-- Declare the variables to receive the output value and return code   
-- of the procedure.  
DECLARE @SalesYTDForSalesPerson money, @ret_code int;  
  
-- Execute the procedure with a title_id value  
-- and save the output value and return code in variables.  
EXECUTE @ret_code = Sales.usp_GetSalesYTD  
    N'Blythe', @SalesYTD = @SalesYTDForSalesPerson OUTPUT;  
--  Check the return codes.  
IF @ret_code = 0  
BEGIN  
   PRINT 'Procedure executed successfully'  
   -- Display the value returned by the procedure.  
   PRINT 'Year-to-date sales for this employee is ' + CONVERT(varchar(10),@SalesYTDForSalesPerson)  
END  
ELSE IF @ret_code = 1  
   PRINT 'ERROR: You must specify a last name for the sales person.'  
ELSE IF @ret_code = 2   
   PRINT 'EERROR: You must enter a valid last name for the sales person.'  
ELSE IF @ret_code = 3  
   PRINT 'ERROR: An error occurred getting sales value.'  
ELSE IF @ret_code = 4  
   PRINT 'ERROR: No sales recorded for this employee.'     
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c0ce-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c0ce-177">See Also</span></span>  
 <span data-ttu-id="5c0ce-178">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5c0ce-178">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span></span>  
 <span data-ttu-id="5c0ce-179">[PRINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/print-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5c0ce-179">[PRINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/print-transact-sql) </span></span>  
 <span data-ttu-id="5c0ce-180">[SET @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/set-local-variable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5c0ce-180">[SET @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/set-local-variable-transact-sql) </span></span>  
 <span data-ttu-id="5c0ce-181">[資料指標](../cursors.md) </span><span class="sxs-lookup"><span data-stu-id="5c0ce-181">[Cursors](../cursors.md) </span></span>  
 <span data-ttu-id="5c0ce-182">[RETURN &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/return-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5c0ce-182">[RETURN &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/return-transact-sql) </span></span>  
 [<span data-ttu-id="5c0ce-183">@@ERROR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5c0ce-183">@@ERROR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/error-transact-sql)  
  
  
