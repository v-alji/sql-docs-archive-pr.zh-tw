---
title: MSSQLSERVER_4186 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 4186 (Database Engine error)
ms.assetid: 1ae88554-f291-45bc-a186-6f41d9cd0fca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 525c1c3bd6e631044b8bc7f17b2c2a01aeb1ef8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585468"
---
# <a name="mssqlserver_4186"></a><span data-ttu-id="41737-102">MSSQLSERVER_4186</span><span class="sxs-lookup"><span data-stu-id="41737-102">MSSQLSERVER_4186</span></span>
    
## <a name="details"></a><span data-ttu-id="41737-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="41737-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="41737-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="41737-104">Product Name</span></span>|<span data-ttu-id="41737-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="41737-105">SQL Server</span></span>|  
|<span data-ttu-id="41737-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="41737-106">Event ID</span></span>|<span data-ttu-id="41737-107">4186</span><span class="sxs-lookup"><span data-stu-id="41737-107">4186</span></span>|  
|<span data-ttu-id="41737-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="41737-108">Event Source</span></span>|<span data-ttu-id="41737-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="41737-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="41737-110">元件</span><span class="sxs-lookup"><span data-stu-id="41737-110">Component</span></span>|<span data-ttu-id="41737-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="41737-111">SQLEngine</span></span>|  
|<span data-ttu-id="41737-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="41737-112">Symbolic Name</span></span>||  
|<span data-ttu-id="41737-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="41737-113">Message Text</span></span>|<span data-ttu-id="41737-114">OUTPUT 子句中無法參考資料行 '%ls.%.\*ls'，因為此資料行定義包含子查詢，或者參考了執行使用者或系統資料存取的函數。</span><span class="sxs-lookup"><span data-stu-id="41737-114">Column '%ls.%.\*ls' cannot be referenced in the OUTPUT clause because the column definition contains a subquery or references a function that performs user or system data access.</span></span> <span data-ttu-id="41737-115">函數如果不是結構描述繫結，根據預設會假設為要執行資料存取。</span><span class="sxs-lookup"><span data-stu-id="41737-115">A function is assumed by default to perform data access if it is not schemabound.</span></span> <span data-ttu-id="41737-116">請考慮從資料行定義中移除子查詢或函數，或者從 OUTPUT 子句中移除資料行。</span><span class="sxs-lookup"><span data-stu-id="41737-116">Consider removing the subquery or function from the column definition or removing the column from the OUTPUT clause.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="41737-117">說明</span><span class="sxs-lookup"><span data-stu-id="41737-117">Explanation</span></span>  
 <span data-ttu-id="41737-118">若要避免不具決定性的行為，當檢視表或嵌入資料表值函式中的資料行是由下列其中一種方法所定義時，OUTPUT 子句便不得參考該資料行：</span><span class="sxs-lookup"><span data-stu-id="41737-118">To prevent nondeterministic behavior, the OUTPUT clause cannot reference a column from a view or inline table-valued function when that column is defined by one of the following methods:</span></span>  
  
-   <span data-ttu-id="41737-119">子查詢。</span><span class="sxs-lookup"><span data-stu-id="41737-119">A subquery.</span></span>  
  
-   <span data-ttu-id="41737-120">執行使用者或系統資料存取的使用者定義函數，或假設會執行這類存取的使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="41737-120">A user-defined function that performs user or system data access, or is assumed to perform such access.</span></span>  
  
-   <span data-ttu-id="41737-121">包含使用者定義函數的計算資料行，而該函數會在其定義中執行使用者或系統資料存取。</span><span class="sxs-lookup"><span data-stu-id="41737-121">A computed column that contains a user-defined function that performs user or system data access in its definition.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="41737-122">範例</span><span class="sxs-lookup"><span data-stu-id="41737-122">Examples</span></span>  
 <span data-ttu-id="41737-123">**由子查詢所定義的檢視表資料行**</span><span class="sxs-lookup"><span data-stu-id="41737-123">**View Column Defined by a Subquery**</span></span>  
  
 <span data-ttu-id="41737-124">下列範例會建立在選取清單中使用子查詢來定義資料行 `State` 的檢視表。</span><span class="sxs-lookup"><span data-stu-id="41737-124">The following example creates a view that uses a subquery in the select list to define the column `State`.</span></span> <span data-ttu-id="41737-125">然後，UPDATE 陳述式會參考 OUTPUT 子句中的 `State` 資料行，並且由於選取清單中的子查詢而失敗。</span><span class="sxs-lookup"><span data-stu-id="41737-125">An UPDATE statement then references the `State` column in the OUTPUT clause and fails because ob the subquery in the select list.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE VIEW dbo.V1  
AS  
    SELECT City,  
-- subquery to return the State name  
           (SELECT Name FROM Person.StateProvince AS sp   
            WHERE sp.StateProvinceID = a.StateProvinceID) AS State  
    FROM Person.Address AS a;  
GO  
--Reference the State column in the OUTPUT clause of an UPDATE statement  
UPDATE dbo.V1   
SET City = City + 'Test'   
OUTPUT deleted.City, deleted.State, inserted.City, inserted.State  
WHERE State = 'Texas';  
GO  
```  
  
 <span data-ttu-id="41737-126">**由函式所定義的檢視表資料行**</span><span class="sxs-lookup"><span data-stu-id="41737-126">**View Column Defined by a Function**</span></span>  
  
 <span data-ttu-id="41737-127">下列範例會建立在選取清單中使用資料存取純量函式 `dbo.ufnGetStock` 來定義資料行 `CurrentInventory` 的檢視表。</span><span class="sxs-lookup"><span data-stu-id="41737-127">The following example creates a view that uses the data accessing, scalar function `dbo.ufnGetStock` in the select list to define the column `CurrentInventory`.</span></span> <span data-ttu-id="41737-128">然後，UPDATE 陳述式會參考 OUTPUT 子句中的 `CurrentInventory` 資料行。</span><span class="sxs-lookup"><span data-stu-id="41737-128">An UPDATE statement then references the `CurrentInventory` column in the OUTPUT clause .</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE VIEW Production.ReorderLevels  
AS  
    SELECT ProductID, ProductModelID, ReorderPoint,  
           dbo.ufnGetStock(ProductID) AS CurrentInventory  
    FROM Production.Product;  
GO  
  
UPDATE Production.ReorderLevels  
SET ReorderPoint += CurrentInventory  
OUTPUT deleted.ReorderPoint, deleted.CurrentInventory,  
       inserted.ReorderPoint, inserted.CurrentInventory  
WHERE ProductModelID BETWEEN 75 and 80;  
```  
  
## <a name="user-action"></a><span data-ttu-id="41737-129">使用者動作</span><span class="sxs-lookup"><span data-stu-id="41737-129">User Action</span></span>  
 <span data-ttu-id="41737-130">您可以使用下列其中一種方法來更正錯誤 4186：</span><span class="sxs-lookup"><span data-stu-id="41737-130">Error 4186 can be corrected in one of the following ways:</span></span>  
  
-   <span data-ttu-id="41737-131">使用聯結 (而非子查詢) 來定義檢視表或函數中的資料行。</span><span class="sxs-lookup"><span data-stu-id="41737-131">Use joins instead of subqueries to define the column in the view or function.</span></span> <span data-ttu-id="41737-132">例如，您可以依照下列方式重新撰寫檢視表 `dbo.V1`。</span><span class="sxs-lookup"><span data-stu-id="41737-132">For example, you can rewrite the view `dbo.V1` as follows.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE VIEW dbo.V1  
    AS  
        SELECT City, sp.Name AS State  
        FROM Person.Address AS a   
        JOIN Person.StateProvince AS sp   
        ON sp.StateProvinceID = a.StateProvinceID;  
    ```  
  
-   <span data-ttu-id="41737-133">檢查使用者定義函數的定義。</span><span class="sxs-lookup"><span data-stu-id="41737-133">Examine the definition of the user-defined function.</span></span> <span data-ttu-id="41737-134">如果此函數沒有執行使用者或系統資料存取，請將函數更改為包含 WITH SCHEMABINDING 子句。</span><span class="sxs-lookup"><span data-stu-id="41737-134">If the function does not perform user or system data access, alter the function to include the WITH SCHEMABINDING clause.</span></span>  
  
-   <span data-ttu-id="41737-135">從 OUTPUT 子句中移除資料行。</span><span class="sxs-lookup"><span data-stu-id="41737-135">Remove the column from the OUTPUT clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41737-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41737-136">See Also</span></span>  
 [<span data-ttu-id="41737-137">OUTPUT 子句 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="41737-137">OUTPUT Clause &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/output-clause-transact-sql)  
  
  
