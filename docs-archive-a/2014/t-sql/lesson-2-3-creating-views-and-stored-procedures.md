---
title: 建立檢視和預存程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- creating views and stored procedures
ms.assetid: 53a0426d-07d8-4b7c-aa21-22632753bad8
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 76f6ecec446536191e8be4b05547ba5fd44c9d8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686671"
---
# <a name="creating-views-and-stored-procedures"></a><span data-ttu-id="cb56f-102">建立檢視和預存程序</span><span class="sxs-lookup"><span data-stu-id="cb56f-102">Creating Views and Stored Procedures</span></span>
  <span data-ttu-id="cb56f-103">既然 Mary 現在能存取 **TestData** 資料庫，您或許想要建立一些資料庫物件，如檢視和預存程序，然後授與 Mary 存取這些物件。</span><span class="sxs-lookup"><span data-stu-id="cb56f-103">Now that Mary can access the **TestData** database, you may want to create some database objects, such as a view and a stored procedure, and then grant Mary access to them.</span></span> <span data-ttu-id="cb56f-104">檢視是預存的 SELECT 陳述式，而預存程序是一個或多個批次執行的 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="cb56f-104">A view is a stored SELECT statement, and a stored procedure is one or more [!INCLUDE[tsql](../includes/tsql-md.md)] statements that execute as a batch.</span></span>  
  
 <span data-ttu-id="cb56f-105">檢視的查詢方式就跟資料表一樣，而且不接受參數。</span><span class="sxs-lookup"><span data-stu-id="cb56f-105">Views are queried like tables and do not accept parameters.</span></span> <span data-ttu-id="cb56f-106">預存程序就比檢視還要複雜。</span><span class="sxs-lookup"><span data-stu-id="cb56f-106">Stored procedures are more complex than views.</span></span> <span data-ttu-id="cb56f-107">預存程序能有輸出和輸入參數，而且還能包含控制程式碼流程的陳述式，如 IF 和 WHILE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="cb56f-107">Stored procedures can have both input and output parameters and can contain statements to control the flow of the code, such as IF and WHILE statements.</span></span> <span data-ttu-id="cb56f-108">對於所有在資料庫中的重複動作，使用預存程序是一個不錯的程式設計方法。</span><span class="sxs-lookup"><span data-stu-id="cb56f-108">It is good programming practice to use stored procedures for all repetitive actions in the database.</span></span>  
  
 <span data-ttu-id="cb56f-109">例如，您將使用 CREATE VIEW 建立檢視，其中只選取 **Products** 資料表中的兩個資料行。</span><span class="sxs-lookup"><span data-stu-id="cb56f-109">For this example, you will use CREATE VIEW to create a view that selects only two of the columns in the **Products** table.</span></span> <span data-ttu-id="cb56f-110">接著，您將使用 CREATE PROCEDURE 建立預存程序，其中接受 price 參數並只傳回成本小於指定參數值的產品。</span><span class="sxs-lookup"><span data-stu-id="cb56f-110">Then, you will use CREATE PROCEDURE to create a stored procedure that accepts a price parameter and returns only those products that cost less than the specified parameter value.</span></span>  
  
### <a name="to-create-a-view"></a><span data-ttu-id="cb56f-111">建立檢視</span><span class="sxs-lookup"><span data-stu-id="cb56f-111">To create a view</span></span>  
  
1.  <span data-ttu-id="cb56f-112">執行下列陳述式建立簡單的檢視，其中會執行 SELECT 陳述式並將產品名稱及價格傳回給使用者。</span><span class="sxs-lookup"><span data-stu-id="cb56f-112">Execute the following statement to create a very simple view that executes a select statement, and returns the names and prices of our products to the user.</span></span>  
  
    ```  
    CREATE VIEW vw_Names  
       AS  
       SELECT ProductName, Price FROM Products;  
    GO  
  
    ```  
  
### <a name="test-the-view"></a><span data-ttu-id="cb56f-113">測試檢視</span><span class="sxs-lookup"><span data-stu-id="cb56f-113">Test the view</span></span>  
  
1.  <span data-ttu-id="cb56f-114">檢視的處理方式和資料表一樣。</span><span class="sxs-lookup"><span data-stu-id="cb56f-114">Views are treated just like tables.</span></span> <span data-ttu-id="cb56f-115">使用 `SELECT` 陳述式存取檢視。</span><span class="sxs-lookup"><span data-stu-id="cb56f-115">Use a `SELECT` statement to access a view.</span></span>  
  
    ```  
    SELECT * FROM vw_Names;  
    GO  
  
    ```  
  
### <a name="to-create-a-stored-procedure"></a><span data-ttu-id="cb56f-116">若要建立預存程序</span><span class="sxs-lookup"><span data-stu-id="cb56f-116">To create a stored procedure</span></span>  
  
1.  <span data-ttu-id="cb56f-117">下列陳述式會建立預存程序名稱 `pr_Names`，接受資料類型為 `@VarPrice` 的輸入參數 (名稱是 `money`)。</span><span class="sxs-lookup"><span data-stu-id="cb56f-117">The following statement creates a stored procedure name `pr_Names`, accepts an input parameter named `@VarPrice` of data type `money`.</span></span> <span data-ttu-id="cb56f-118">預存程序會列印與輸出參數串連的 `Products less than` 陳述式，而這個輸出參數會從 `money` 資料類型變更為 `varchar(10)` 字元資料類型。</span><span class="sxs-lookup"><span data-stu-id="cb56f-118">The stored procedure prints the statement `Products less than` concatenated with the input parameter that is changed from the `money` data type into a `varchar(10)` character data type.</span></span> <span data-ttu-id="cb56f-119">然後，預存程序會執行檢視上的 `SELECT` 陳述式，將輸出參數當做 `WHERE` 子句的一部分進行傳遞。</span><span class="sxs-lookup"><span data-stu-id="cb56f-119">Then, the procedure executes a `SELECT` statement on the view, passing the input parameter as part of the `WHERE` clause.</span></span> <span data-ttu-id="cb56f-120">這樣會傳回成本小於輸出參數值的所有產品。</span><span class="sxs-lookup"><span data-stu-id="cb56f-120">This returns all products that cost less than the input parameter value.</span></span>  
  
    ```  
    CREATE PROCEDURE pr_Names @VarPrice money  
       AS  
       BEGIN  
          -- The print statement returns text to the user  
          PRINT 'Products less than ' + CAST(@VarPrice AS varchar(10));  
          -- A second statement starts here  
          SELECT ProductName, Price FROM vw_Names  
                WHERE Price < @varPrice;  
       END  
    GO  
  
    ```  
  
### <a name="test-the-stored-procedure"></a><span data-ttu-id="cb56f-121">測試預存程序</span><span class="sxs-lookup"><span data-stu-id="cb56f-121">Test the stored procedure</span></span>  
  
1.  <span data-ttu-id="cb56f-122">若要測試預存程序，請輸入並執行下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="cb56f-122">To test the stored procedure, type and execute the following statement.</span></span> <span data-ttu-id="cb56f-123">這個程序應該傳回兩個成本小於 `Products` 的產品名稱，這兩個產品是在第 1 課輸入 `10.00`資料表而來的。</span><span class="sxs-lookup"><span data-stu-id="cb56f-123">The procedure should return the names of the two products entered into the `Products` table in Lesson 1 with a price that is less than `10.00`.</span></span>  
  
    ```  
    EXECUTE pr_Names 10.00;  
    GO  
  
    ```  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="cb56f-124">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="cb56f-124">Next Task in Lesson</span></span>  
 [<span data-ttu-id="cb56f-125">授與資料庫物件的存取權</span><span class="sxs-lookup"><span data-stu-id="cb56f-125">Granting Access to a Database Object</span></span>](lesson-2-4-granting-access-to-a-database-object.md)  
  
## <a name="see-also"></a><span data-ttu-id="cb56f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb56f-126">See Also</span></span>  
 <span data-ttu-id="cb56f-127">[CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cb56f-127">[CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) </span></span>  
 [<span data-ttu-id="cb56f-128">CREATE PROCEDURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cb56f-128">CREATE PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-procedure-transact-sql)  
  
  
