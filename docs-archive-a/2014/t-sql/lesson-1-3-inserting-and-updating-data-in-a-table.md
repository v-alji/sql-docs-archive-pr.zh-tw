---
title: 在資料表中插入及更新資料 (教學課程) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- inserting and updating data
ms.assetid: 514dc87a-b829-43b5-8fc8-1a400a260284
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0646019f166e1c2cc126a4cc7d2ed8f27a7bd2f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597479"
---
# <a name="inserting-and-updating-data-in-a-table-tutorial"></a><span data-ttu-id="c6d8f-102">在資料表中插入及更新資料 (教學課程)</span><span class="sxs-lookup"><span data-stu-id="c6d8f-102">Inserting and Updating Data in a Table (Tutorial)</span></span>
  <span data-ttu-id="c6d8f-103">既然您現在建立好 **Products** 資料表，就可以準備使用 INSERT 陳述式，將資料插入資料表。</span><span class="sxs-lookup"><span data-stu-id="c6d8f-103">Now that you have created the **Products** table, you are ready to insert data into the table by using the INSERT statement.</span></span> <span data-ttu-id="c6d8f-104">在插入資料後，您將使用 UPDATE 陳述式來變更資料列的內容。</span><span class="sxs-lookup"><span data-stu-id="c6d8f-104">After the data is inserted, you will change the content of a row by using an UPDATE statement.</span></span> <span data-ttu-id="c6d8f-105">您將使用 UPDATE 陳述式的 WHERE 子句，限制對單一資料列進行更新。</span><span class="sxs-lookup"><span data-stu-id="c6d8f-105">You will use the WHERE clause of the UPDATE statement to restrict the update to a single row.</span></span> <span data-ttu-id="c6d8f-106">接下來所述的四個陳述式將輸入下面資料。</span><span class="sxs-lookup"><span data-stu-id="c6d8f-106">The four statements will enter the following data.</span></span>  
  
|<span data-ttu-id="c6d8f-107">ProductID</span><span class="sxs-lookup"><span data-stu-id="c6d8f-107">ProductID</span></span>|<span data-ttu-id="c6d8f-108">ProductName</span><span class="sxs-lookup"><span data-stu-id="c6d8f-108">ProductName</span></span>|<span data-ttu-id="c6d8f-109">價格</span><span class="sxs-lookup"><span data-stu-id="c6d8f-109">Price</span></span>|<span data-ttu-id="c6d8f-110">ProductDescription</span><span class="sxs-lookup"><span data-stu-id="c6d8f-110">ProductDescription</span></span>|  
|---------------|-----------------|-----------|------------------------|  
|<span data-ttu-id="c6d8f-111">1</span><span class="sxs-lookup"><span data-stu-id="c6d8f-111">1</span></span>|<span data-ttu-id="c6d8f-112">Clamp</span><span class="sxs-lookup"><span data-stu-id="c6d8f-112">Clamp</span></span>|<span data-ttu-id="c6d8f-113">12.48</span><span class="sxs-lookup"><span data-stu-id="c6d8f-113">12.48</span></span>|<span data-ttu-id="c6d8f-114">Workbench clamp</span><span class="sxs-lookup"><span data-stu-id="c6d8f-114">Workbench clamp</span></span>|  
|<span data-ttu-id="c6d8f-115">50</span><span class="sxs-lookup"><span data-stu-id="c6d8f-115">50</span></span>|<span data-ttu-id="c6d8f-116">Screwdriver</span><span class="sxs-lookup"><span data-stu-id="c6d8f-116">Screwdriver</span></span>|<span data-ttu-id="c6d8f-117">3.17</span><span class="sxs-lookup"><span data-stu-id="c6d8f-117">3.17</span></span>|<span data-ttu-id="c6d8f-118">Flat head</span><span class="sxs-lookup"><span data-stu-id="c6d8f-118">Flat head</span></span>|  
|<span data-ttu-id="c6d8f-119">75</span><span class="sxs-lookup"><span data-stu-id="c6d8f-119">75</span></span>|<span data-ttu-id="c6d8f-120">Tire Bar</span><span class="sxs-lookup"><span data-stu-id="c6d8f-120">Tire Bar</span></span>||<span data-ttu-id="c6d8f-121">Tool for changing tires.</span><span class="sxs-lookup"><span data-stu-id="c6d8f-121">Tool for changing tires.</span></span>|  
|<span data-ttu-id="c6d8f-122">3000</span><span class="sxs-lookup"><span data-stu-id="c6d8f-122">3000</span></span>|<span data-ttu-id="c6d8f-123">3mm Bracket</span><span class="sxs-lookup"><span data-stu-id="c6d8f-123">3mm Bracket</span></span>|<span data-ttu-id="c6d8f-124">.52</span><span class="sxs-lookup"><span data-stu-id="c6d8f-124">.52</span></span>||  
  
 <span data-ttu-id="c6d8f-125">基本語法包括：INSERT、資料表、資料行清單、VALUES 以及要插入的值清單。</span><span class="sxs-lookup"><span data-stu-id="c6d8f-125">The basic syntax is: INSERT, table name, column list, VALUES, and then a list of the values to be inserted.</span></span> <span data-ttu-id="c6d8f-126">程式行前面的兩個連字號表示該程式行是註解，而編譯器會忽略這行文字。</span><span class="sxs-lookup"><span data-stu-id="c6d8f-126">The two hyphens in front of a line indicate that the line is a comment and the text will be ignored by the compiler.</span></span> <span data-ttu-id="c6d8f-127">在本案例中，註解說明所允許的語法變化。</span><span class="sxs-lookup"><span data-stu-id="c6d8f-127">In this case, the comment describes a permissible variation of the syntax.</span></span>  
  
### <a name="to-insert-data-into-a-table"></a><span data-ttu-id="c6d8f-128">將資料插入資料表</span><span class="sxs-lookup"><span data-stu-id="c6d8f-128">To insert data into a table</span></span>  
  
1.  <span data-ttu-id="c6d8f-129">執行下列陳述式，將資料列插入上一項工作中建立的 `Products` 資料表。</span><span class="sxs-lookup"><span data-stu-id="c6d8f-129">Execute the following statement to insert a row into the `Products` table that was created in the previous task.</span></span> <span data-ttu-id="c6d8f-130">以下是基本語法。</span><span class="sxs-lookup"><span data-stu-id="c6d8f-130">This is the basic syntax.</span></span>  
  
    ```  
    -- Standard syntax  
    INSERT dbo.Products (ProductID, ProductName, Price, ProductDescription)  
        VALUES (1, 'Clamp', 12.48, 'Workbench clamp')  
    GO  
  
    ```  
  
2.  <span data-ttu-id="c6d8f-131">下列陳述式示範如何可以在透過切換欄位清單 (括號內) 和值清單內 `ProductID` 和 `ProductName` 的位置所提供的參數中變更順序。</span><span class="sxs-lookup"><span data-stu-id="c6d8f-131">The following statement shows how you can change the order in which the parameters are provided by switching the placement of the `ProductID` and `ProductName` in both the field list (in parentheses) and in the values list.</span></span>  
  
    ```  
    -- Changing the order of the columns  
    INSERT dbo.Products (ProductName, ProductID, Price, ProductDescription)  
        VALUES ('Screwdriver', 50, 3.17, 'Flat head')  
    GO  
  
    ```  
  
3.  <span data-ttu-id="c6d8f-132">下列陳述式示範只要依照正確的順序列出值，就可以省略資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="c6d8f-132">The following statement demonstrates that the names of the columns are optional, as long as the values are listed in the correct order.</span></span> <span data-ttu-id="c6d8f-133">這是常見的語法，但不建議您使用，因為其他使用者可能會很難了解您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c6d8f-133">This syntax is common but is not recommended because it might be harder for others to understand your code.</span></span> <span data-ttu-id="c6d8f-134">`NULL` 已針對 `Price` 資料行指定，這是因為此產品的價格不明。</span><span class="sxs-lookup"><span data-stu-id="c6d8f-134">`NULL` is specified for the `Price` column because the price for this product is not yet known.</span></span>  
  
    ```  
    -- Skipping the column list, but keeping the values in order  
    INSERT dbo.Products  
        VALUES (75, 'Tire Bar', NULL, 'Tool for changing tires.')  
    GO  
  
    ```  
  
4.  <span data-ttu-id="c6d8f-135">只要是在預設的結構描述中存取及變更資料表，就可以省略結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="c6d8f-135">The schema name is optional as long as you are accessing and changing a table in your default schema.</span></span> <span data-ttu-id="c6d8f-136">因為 `ProductDescription` 資料行可以接受 Null 值及無值，所以在陳述式中便可以完全省略 `ProductDescription` 資料行名稱和值。</span><span class="sxs-lookup"><span data-stu-id="c6d8f-136">Because the `ProductDescription` column allows null values and no value is being provided, the `ProductDescription` column name and value can be dropped from the statement completely.</span></span>  
  
    ```  
    -- Dropping the optional dbo and dropping the ProductDescription column  
    INSERT Products (ProductID, ProductName, Price)  
        VALUES (3000, '3mm Bracket', .52)  
    GO  
    ```  
  
### <a name="to-update-the-products-table"></a><span data-ttu-id="c6d8f-137">更新 Products 資料表</span><span class="sxs-lookup"><span data-stu-id="c6d8f-137">To update the products table</span></span>  
  
1.  <span data-ttu-id="c6d8f-138">輸入並執行下列 `UPDATE` 陳述式，將第二個產品的 `ProductName` 從 `Screwdriver`變更為 `Flat Head Screwdriver`。</span><span class="sxs-lookup"><span data-stu-id="c6d8f-138">Type and execute the following `UPDATE` statement to change the `ProductName` of the second product from `Screwdriver`, to `Flat Head Screwdriver`.</span></span>  
  
    ```  
    UPDATE dbo.Products  
        SET ProductName = 'Flat Head Screwdriver'  
        WHERE ProductID = 50  
    GO  
    ```  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="c6d8f-139">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="c6d8f-139">Next Task in Lesson</span></span>  
 [<span data-ttu-id="c6d8f-140">讀取資料表的資料 &#40;教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="c6d8f-140">Reading the Data in a Table &#40;Tutorial&#41;</span></span>](lesson-1-4-reading-the-data-in-a-table.md)  
  
## <a name="see-also"></a><span data-ttu-id="c6d8f-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6d8f-141">See Also</span></span>  
 <span data-ttu-id="c6d8f-142">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c6d8f-142">[INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) </span></span>  
 [<span data-ttu-id="c6d8f-143">UPDATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c6d8f-143">UPDATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/update-transact-sql)  
  
  
