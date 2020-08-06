---
title: 使用資料表值參數 (Database Engine) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- DECLARE
- CREATE TYPE
helpviewer_keywords:
- table-valued parameters
- table-valued parameters, about table-valued parameters
- parameters [SQL Server], table-valued
- TVP See table-valued parameters
ms.assetid: 5e95a382-1e01-4c74-81f5-055612c2ad99
author: stevestein
ms.author: sstein
ms.openlocfilehash: fa7013fddc6b2ce12ad9ad0f9fcb511d93915e05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595863"
---
# <a name="use-table-valued-parameters-database-engine"></a><span data-ttu-id="ce2fb-102">使用資料表值參數 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="ce2fb-102">Use Table-Valued Parameters (Database Engine)</span></span>
  <span data-ttu-id="ce2fb-103">資料表值參數是藉由使用使用者定義的資料表類型來進行宣告。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-103">Table-valued parameters are declared by using user-defined table types.</span></span> <span data-ttu-id="ce2fb-104">您可以使用資料表值參數，將多個資料列傳送到 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式或常式 (如預存程序或函數)，而不需要建立暫存資料表或許多參數。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-104">You can use table-valued parameters to send multiple rows of data to a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or a routine, such as a stored procedure or function, without creating a temporary table or many parameters.</span></span>  
  
 <span data-ttu-id="ce2fb-105">資料表值參數就像是 OLE DB 和 ODBC 中的參數陣列，但是提供了更多的彈性，而且與 [!INCLUDE[tsql](../../includes/tsql-md.md)]更緊密整合在一起。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-105">Table-valued parameters are like parameter arrays in OLE DB and ODBC, but offer more flexibility and closer integration with [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ce2fb-106">資料表值參數也會因為能夠參與以集合為基礎的作業而獲益。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-106">Table-valued parameters also have the benefit of being able to participate in set-based operations.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="ce2fb-107">會以傳址方式將資料表值參數傳遞給常式，以免產生輸入資料的複本。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-107">passes table-valued parameters to routines by reference to avoid making a copy of the input data.</span></span> <span data-ttu-id="ce2fb-108">您可以使用資料表值參數來建立及執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 常式，然後從 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼 (任何 Managed 語言中的 Managed 和原生用戶端) 呼叫這些常式。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-108">You can create and execute [!INCLUDE[tsql](../../includes/tsql-md.md)] routines with table-valued parameters, and call them from [!INCLUDE[tsql](../../includes/tsql-md.md)] code, managed and native clients in any managed language.</span></span>  
  
 <span data-ttu-id="ce2fb-109">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="ce2fb-109">**In This Topic:**</span></span>  
  
 [<span data-ttu-id="ce2fb-110">優點</span><span class="sxs-lookup"><span data-stu-id="ce2fb-110">Benefits</span></span>](#Benefits)  
  
 [<span data-ttu-id="ce2fb-111">限制</span><span class="sxs-lookup"><span data-stu-id="ce2fb-111">Restrictions</span></span>](#Restrictions)  
  
 [<span data-ttu-id="ce2fb-112">資料表值參數與BULK INSERT 作業的比較</span><span class="sxs-lookup"><span data-stu-id="ce2fb-112">Table-Valued Parameters vs. BULK INSERT Operations</span></span>](#BulkInsert)  
  
 [<span data-ttu-id="ce2fb-113">範例</span><span class="sxs-lookup"><span data-stu-id="ce2fb-113">Example</span></span>](#Example)  
  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="ce2fb-114">優點</span><span class="sxs-lookup"><span data-stu-id="ce2fb-114">Benefits</span></span>  
 <span data-ttu-id="ce2fb-115">資料表值參數的範圍為預存程序、函數或動態 [!INCLUDE[tsql](../../includes/tsql-md.md)] 文字，與其他參數一模一樣。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-115">A table-valued parameter is scoped to the stored procedure, function, or dynamic [!INCLUDE[tsql](../../includes/tsql-md.md)] text, exactly like other parameters.</span></span> <span data-ttu-id="ce2fb-116">同樣地，資料表類型之變數的範圍與使用 DECLARE 陳述式建立的其他任何區域變數一樣。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-116">Similarly, a variable of table type has scope like any other local variable that is created by using a DECLARE statement.</span></span> <span data-ttu-id="ce2fb-117">您可以在動態 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式內宣告資料表值變數，並將這些變數當做資料表值參數傳遞給預存程序和函數。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-117">You can declare table-valued variables within dynamic [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and pass these variables as table-valued parameters to stored procedures and functions.</span></span>  
  
 <span data-ttu-id="ce2fb-118">資料表值參數提供更大的彈性，而且在某些情況下，其效能優於暫存資料表或是傳遞參數清單的其他方法。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-118">Table-valued parameters offer more flexibility and in some cases better performance than temporary tables or other ways to pass a list of parameters.</span></span> <span data-ttu-id="ce2fb-119">資料表值參數提供下列好處：</span><span class="sxs-lookup"><span data-stu-id="ce2fb-119">Table-valued parameters offer the following benefits:</span></span>  
  
-   <span data-ttu-id="ce2fb-120">不需要從用戶端鎖定初始資料母體。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-120">Do not acquire locks for the initial population of data from a client.</span></span>  
  
-   <span data-ttu-id="ce2fb-121">提供簡單的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-121">Provide a simple programming model.</span></span>  
  
-   <span data-ttu-id="ce2fb-122">可讓您將複雜的商務邏輯併入單一常式內。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-122">Enable you to include complex business logic in a single routine.</span></span>  
  
-   <span data-ttu-id="ce2fb-123">減少與伺服器之間的往返次數。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-123">Reduce round trips to the server.</span></span>  
  
-   <span data-ttu-id="ce2fb-124">可以有一個不同基數的資料表結構。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-124">Can have a table structure of different cardinality.</span></span>  
  
-   <span data-ttu-id="ce2fb-125">具有強型別。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-125">Are strongly typed.</span></span>  
  
-   <span data-ttu-id="ce2fb-126">可讓用戶端指定排序次序和唯一索引鍵。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-126">Enable the client to specify sort order and unique keys.</span></span>  
  
-   <span data-ttu-id="ce2fb-127">在預存程序中使用時，會像暫存資料表一樣被快取。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-127">Are cached like a temp table when used in a stored procedure.</span></span> <span data-ttu-id="ce2fb-128">從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]開始，也會為參數化查詢快取資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-128">Starting with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], table-valued parameters are also cached for parameterized queries.</span></span>  
  
##  <a name="restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ce2fb-129">限制</span><span class="sxs-lookup"><span data-stu-id="ce2fb-129">Restrictions</span></span>  
 <span data-ttu-id="ce2fb-130">資料表值參數有下列限制：</span><span class="sxs-lookup"><span data-stu-id="ce2fb-130">Table-valued parameters have the following restrictions:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ce2fb-131">不會維護資料表值參數之資料行上的統計資料。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-131">does not maintain statistics on columns of table-valued parameters.</span></span>  
  
-   <span data-ttu-id="ce2fb-132">資料表值參數必須當做輸入 READONLY 參數傳遞給 [!INCLUDE[tsql](../../includes/tsql-md.md)] 常式。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-132">Table-valued parameters must be passed as input READONLY parameters to [!INCLUDE[tsql](../../includes/tsql-md.md)] routines.</span></span> <span data-ttu-id="ce2fb-133">您不能在常式主體內針對資料表值參數執行 DML 作業，例如 UPDATE、DELETE 或 INSERT。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-133">You cannot perform DML operations such as UPDATE, DELETE, or INSERT on a table-valued parameter in the body of a routine.</span></span>  
  
-   <span data-ttu-id="ce2fb-134">您不能使用資料表值參數當做 SELECT INTO 或 INSERT EXEC 陳述式的目標。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-134">You cannot use a table-valued parameter as target of a SELECT INTO or INSERT EXEC statement.</span></span> <span data-ttu-id="ce2fb-135">資料表值參數可以在 SELECT INTO 的 FROM 子句中或是 INSERT EXEC 字串或預存程序內。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-135">A table-valued parameter can be in the FROM clause of SELECT INTO or in the INSERT EXEC string or stored procedure.</span></span>  
  
##  <a name="table-valued-parameters-vs-bulk-insert-operations"></a><a name="BulkInsert"></a><span data-ttu-id="ce2fb-136">資料表值參數與 BULK INSERT 作業的比較</span><span class="sxs-lookup"><span data-stu-id="ce2fb-136">Table-Valued Parameters vs. BULK INSERT Operations</span></span>  
 <span data-ttu-id="ce2fb-137">使用資料表值參數可以和使用以集合為基礎之變數的其他方式相比較；但是，對於大型資料集而言，使用資料表值參數通常可以更快速。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-137">Using table-valued parameters is comparable to other ways of using set-based variables; however, using table-valued parameters frequently can be faster for large data sets.</span></span> <span data-ttu-id="ce2fb-138">與大量作業 (其啟動成本高於資料表值參數) 相較之下，當插入 1000 個以下的資料列時，資料表值參數會有很不錯的執行效能。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-138">Compared to bulk operations that have a greater startup cost than table-valued parameters, table-valued parameters perform well for inserting less than 1000 rows.</span></span>  
  
 <span data-ttu-id="ce2fb-139">重複使用的資料表值參數會因為暫存資料表快取而獲益。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-139">Table-valued parameters that are reused benefit from temporary table caching.</span></span> <span data-ttu-id="ce2fb-140">這種資料表快取提供了比同等的 BULK INSERT 作業更好的延展性。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-140">This table caching enables better scalability than equivalent BULK INSERT operations.</span></span> <span data-ttu-id="ce2fb-141">藉由使用小型資料列插入作業，可能會因為使用參數清單或批次處理的陳述式 (而非 BULK INSERT 作業或資料表值參數) 而有效能上的小獲益。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-141">By using small row-insert operations a small performance benefit might be gained by using parameter lists or batched statements instead of BULK INSERT operations or table-valued parameters.</span></span> <span data-ttu-id="ce2fb-142">但是，這些方法的便利性不如程式，而且當資料列增加時，效能會快速降低。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-142">However, these methods are less convenient to program, and performance decreases quickly as rows increase.</span></span>  
  
 <span data-ttu-id="ce2fb-143">資料表值參數的執行效能等於或優於同等的參數陣列實作。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-143">Table-valued parameters perform equally well or better than an equivalent parameter array implementation.</span></span>  
  
##  <a name="example"></a><a name="Example"></a> <span data-ttu-id="ce2fb-144">範例</span><span class="sxs-lookup"><span data-stu-id="ce2fb-144">Example</span></span>  
 <span data-ttu-id="ce2fb-145">下列範例使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 並示範如何建立資料表值參數類型、宣告變數來參考它、填入參數清單，然後將值傳遞給預存程序。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-145">The following example uses [!INCLUDE[tsql](../../includes/tsql-md.md)] and shows you how to create a table-valued parameter type, declare a variable to reference it, fill the parameter list, and then pass the values to a stored procedure.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
  
/* Create a table type. */  
CREATE TYPE LocationTableType AS TABLE   
( LocationName VARCHAR(50)  
, CostRate INT );  
GO  
  
/* Create a procedure to receive data for the table-valued parameter. */  
CREATE PROCEDURE dbo. usp_InsertProductionLocation  
    @TVP LocationTableType READONLY  
    AS   
    SET NOCOUNT ON  
    INSERT INTO AdventureWorks2012.Production.Location  
           (Name  
           ,CostRate  
           ,Availability  
           ,ModifiedDate)  
        SELECT *, 0, GETDATE()  
        FROM  @TVP;  
        GO  
  
/* Declare a variable that references the type. */  
DECLARE @LocationTVP AS LocationTableType;  
  
/* Add data to the table variable. */  
INSERT INTO @LocationTVP (LocationName, CostRate)  
    SELECT Name, 0.00  
    FROM AdventureWorks2012.Person.StateProvince;  
  
/* Pass the table variable data to a stored procedure. */  
EXEC usp_InsertProductionLocation @LocationTVP;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce2fb-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce2fb-146">See Also</span></span>  
 <span data-ttu-id="ce2fb-147">[CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ce2fb-147">[CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql) </span></span>  
 <span data-ttu-id="ce2fb-148">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ce2fb-148">[DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql) </span></span>  
 <span data-ttu-id="ce2fb-149">[&#40;Transact-sql&#41;的 sys.databases 類型](/sql/relational-databases/system-catalog-views/sys-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ce2fb-149">[sys.types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-types-transact-sql) </span></span>  
 <span data-ttu-id="ce2fb-150">[&#40;Transact-sql&#41;的 sys.databases 參數](/sql/relational-databases/system-catalog-views/sys-parameters-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ce2fb-150">[sys.parameters &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-parameters-transact-sql) </span></span>  
 <span data-ttu-id="ce2fb-151">[parameter_type_usages &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-parameter-type-usages-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ce2fb-151">[sys.parameter_type_usages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-parameter-type-usages-transact-sql) </span></span>  
 <span data-ttu-id="ce2fb-152">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ce2fb-152">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span></span>  
 [<span data-ttu-id="ce2fb-153">CREATE FUNCTION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ce2fb-153">CREATE FUNCTION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-function-transact-sql)  
  
  
