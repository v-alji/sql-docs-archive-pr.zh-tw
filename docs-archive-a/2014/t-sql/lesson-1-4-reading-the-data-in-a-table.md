---
title: 讀取資料表中的資料 (教學課程) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- reading data in a table
ms.assetid: 532232c9-3d41-45cd-9150-de67a1cbfcf5
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4bdaaeeddf8f35792c536624abfe6ff11b2dbd2e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597480"
---
# <a name="reading-the-data-in-a-table-tutorial"></a><span data-ttu-id="9e143-102">讀取資料表的資料 (教學課程)</span><span class="sxs-lookup"><span data-stu-id="9e143-102">Reading the Data in a Table (Tutorial)</span></span>
  <span data-ttu-id="9e143-103">使用 SELECT 陳述式來讀取資料表的資料。</span><span class="sxs-lookup"><span data-stu-id="9e143-103">Use the SELECT statement to read the data in a table.</span></span> <span data-ttu-id="9e143-104">[!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式中最重要的其中一個陳述式就是 SELECT 陳述式，而其中有很多的語法變化。</span><span class="sxs-lookup"><span data-stu-id="9e143-104">The SELECT statement is one of the most important [!INCLUDE[tsql](../includes/tsql-md.md)] statements, and there are many variations in the syntax.</span></span> <span data-ttu-id="9e143-105">在本教學課程中，您將使用五種簡單的變化樣式。</span><span class="sxs-lookup"><span data-stu-id="9e143-105">For this tutorial, you will work with five simple versions.</span></span>  
  
### <a name="to-read-the-data-in-a-table"></a><span data-ttu-id="9e143-106">讀取資料表的資料</span><span class="sxs-lookup"><span data-stu-id="9e143-106">To read the data in a table</span></span>  
  
1.  <span data-ttu-id="9e143-107">輸入並執行下列陳述式，以讀取 `Products` 資料表的資料。</span><span class="sxs-lookup"><span data-stu-id="9e143-107">Type and execute the following statements to read the data in the `Products` table.</span></span>  
  
    ```  
    -- The basic syntax for reading data from a single table  
    SELECT ProductID, ProductName, Price, ProductDescription  
        FROM dbo.Products  
    GO  
  
    ```  
  
2.  <span data-ttu-id="9e143-108">您可以使用星號，選取資料表中的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="9e143-108">You can use an asterisk to select all the columns in the table.</span></span> <span data-ttu-id="9e143-109">這個方法常在隨選查詢中使用。</span><span class="sxs-lookup"><span data-stu-id="9e143-109">This is often used in ad hoc queries.</span></span> <span data-ttu-id="9e143-110">您應該在固定程式碼中提供資料行清單，使陳述式會傳回預期的資料行，即使以後加入新資料行還是一樣。</span><span class="sxs-lookup"><span data-stu-id="9e143-110">You should provide the column list in you permanent code so that the statement will return the predicted columns, even if a new column is added to the table later.</span></span>  
  
    ```  
    -- Returns all columns in the table  
    -- Does not use the optional schema, dbo  
    SELECT * FROM Products  
    GO  
  
    ```  
  
3.  <span data-ttu-id="9e143-111">您可以省略不要傳回的資料行。</span><span class="sxs-lookup"><span data-stu-id="9e143-111">You can omit columns that you do not want to return.</span></span> <span data-ttu-id="9e143-112">而且會以資料行所列出的順序來傳回資料行。</span><span class="sxs-lookup"><span data-stu-id="9e143-112">The columns will be returned in the order that they are listed.</span></span>  
  
    ```  
    -- Returns only two of the columns from the table  
    SELECT ProductName, Price  
        FROM dbo.Products  
    GO  
  
    ```  
  
4.  <span data-ttu-id="9e143-113">使用 `WHERE` 子句，限制要傳回給使用者的資料列。</span><span class="sxs-lookup"><span data-stu-id="9e143-113">Use a `WHERE` clause to limit the rows that are returned to the user.</span></span>  
  
    ```  
    -- Returns only two of the records in the table  
    SELECT ProductID, ProductName, Price, ProductDescription  
        FROM dbo.Products  
        WHERE ProductID < 60  
    GO  
  
    ```  
  
5.  <span data-ttu-id="9e143-114">您可以處理資料行中所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="9e143-114">You can work with the values in the columns as they are returned.</span></span> <span data-ttu-id="9e143-115">下列範例會在 `Price` 資料行上進行數學運算。</span><span class="sxs-lookup"><span data-stu-id="9e143-115">The following example performs a mathematical operation on the `Price` column.</span></span> <span data-ttu-id="9e143-116">除非使用 `AS` 關鍵字提供名稱，否則以這種方式變更的資料行將不會有名稱。</span><span class="sxs-lookup"><span data-stu-id="9e143-116">Columns that have been changed in this way will not have a name unless you provide one by using the `AS` keyword.</span></span>  
  
    ```  
    -- Returns ProductName and the Price including a 7% tax  
    -- Provides the name CustomerPays for the calculated column  
    SELECT ProductName, Price * 1.07 AS CustomerPays  
        FROM dbo.Products  
    GO  
    ```  
  
## <a name="functions-that-are-useful-in-a-select-statement"></a><span data-ttu-id="9e143-117">函數對 SELECT 陳述式相當有用</span><span class="sxs-lookup"><span data-stu-id="9e143-117">Functions That Are Useful in a SELECT Statement</span></span>  
 <span data-ttu-id="9e143-118">如需有關某些可在 SELECT 陳述式中用來處理資料之函數的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="9e143-118">For information about some functions that you can use to work with data in SELECT statements, see the following topics:</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="9e143-119">字串函數 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9e143-119">String Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/string-functions-transact-sql)|[<span data-ttu-id="9e143-120">日期和時間資料類型與函數 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9e143-120">Date and Time Data Types and Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|  
|[<span data-ttu-id="9e143-121">數學函數 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9e143-121">Mathematical Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/mathematical-functions-transact-sql)|[<span data-ttu-id="9e143-122">Text 和 Image 函數 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9e143-122">Text and Image Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/text-and-image-functions-textptr-transact-sql)|  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="9e143-123">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="9e143-123">Next Task in Lesson</span></span>  
 [<span data-ttu-id="9e143-124">摘要：建立資料庫物件</span><span class="sxs-lookup"><span data-stu-id="9e143-124">Summary: Creating Database Objects</span></span>](lesson-1-5-summary-creating-database-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="9e143-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e143-125">See Also</span></span>  
 [<span data-ttu-id="9e143-126">SELECT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9e143-126">SELECT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/select-transact-sql)  
  
  
