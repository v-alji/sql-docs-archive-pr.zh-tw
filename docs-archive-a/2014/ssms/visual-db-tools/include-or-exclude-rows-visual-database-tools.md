---
title: 包含或排除資料列 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- search criteria [SQL Server], WHERE clause
- included rows
- search conditions [SQL Server], HAVING clause
- search criteria [SQL Server], including rows
- row excluded in search [SQL Server]
- search criteria [SQL Server], HAVING clause
- search conditions [SQL Server], WHERE clause
- row included in search [SQL Server]
- excluding rows
ms.assetid: ba4e1202-31a2-444d-8365-c68a530ef223
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7b2d31c51296fa73a503e59a14adb60d79a61178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596967"
---
# <a name="include-or-exclude-rows-visual-database-tools"></a><span data-ttu-id="5359a-102">包含或排除資料列 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="5359a-102">Include or Exclude Rows (Visual Database Tools)</span></span>
  <span data-ttu-id="5359a-103">若要限制 SELECT 查詢傳回的資料列數目，您可以建立搜尋條件或篩選條件。</span><span class="sxs-lookup"><span data-stu-id="5359a-103">To restrict the number of rows a SELECT query should return, you create search conditions or filter criteria.</span></span> <span data-ttu-id="5359a-104">在 SQL 中，搜尋條件出現在陳述式中的 WHERE 子句，或如果您要建立彙總查詢，查詢條件則位於 HAVING 子句中。</span><span class="sxs-lookup"><span data-stu-id="5359a-104">In SQL, search conditions appear in the WHERE clause of the statement, or if you are creating an aggregate query, in the HAVING clause.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5359a-105">您也可以使用搜尋條件來指出受到 UPDATE、Insert Results、Insert Values、DELETE 或製成資料表查詢影響的資料列。</span><span class="sxs-lookup"><span data-stu-id="5359a-105">You can also use search conditions to indicate which rows are affected by an Update, Insert Results, Insert Values, Delete, or Make Table query.</span></span>  
  
 <span data-ttu-id="5359a-106">執行查詢時， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會檢查並將搜尋條件套用到您正在搜尋之資料表中的每個資料列。</span><span class="sxs-lookup"><span data-stu-id="5359a-106">When the query runs, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] examines and applies the search condition to each row in the tables you are searching.</span></span> <span data-ttu-id="5359a-107">如果符合搜尋條件，該資料列將包含在查詢中。</span><span class="sxs-lookup"><span data-stu-id="5359a-107">If the row meets the condition, it is included in the query.</span></span> <span data-ttu-id="5359a-108">例如，要在特定區域中尋找所有員工的搜尋條件可以是：</span><span class="sxs-lookup"><span data-stu-id="5359a-108">For example, a search condition that would find all the employees in a particular region might be:</span></span>  
  
```  
region = 'UK'  
```  
  
 <span data-ttu-id="5359a-109">若要建立將資料列包含在結果的準則，您可以使用多重搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="5359a-109">To establish the criteria for including a row in a result, you can use multiple search conditions.</span></span> <span data-ttu-id="5359a-110">例如，下列搜尋準則含有兩個搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="5359a-110">For example, the following search criterion consists of two search conditions.</span></span> <span data-ttu-id="5359a-111">如果資料列同時符合這兩個條件，查詢才會將該資料列包含在結果集中。</span><span class="sxs-lookup"><span data-stu-id="5359a-111">The query includes a row in the result set only if that row satisfies both of the conditions.</span></span>  
  
```  
region = 'UK' AND product_line = 'Housewares'  
```  
  
 <span data-ttu-id="5359a-112">您可以使用 AND 或 OR 來結合這些條件。</span><span class="sxs-lookup"><span data-stu-id="5359a-112">You can combine these conditions with AND or OR.</span></span> <span data-ttu-id="5359a-113">上面的範例即使用 AND。</span><span class="sxs-lookup"><span data-stu-id="5359a-113">The previous example uses AND.</span></span> <span data-ttu-id="5359a-114">相反的，下面的搜尋準則則是使用 OR。</span><span class="sxs-lookup"><span data-stu-id="5359a-114">In contrast, the following criterion uses OR.</span></span> <span data-ttu-id="5359a-115">結果集將包含符合其中一個或同時符合兩個搜尋條件的所有資料列：</span><span class="sxs-lookup"><span data-stu-id="5359a-115">The result set will include any row that satisfies either or both of the search conditions:</span></span>  
  
```  
region = 'UK' OR product_line = 'Housewares'  
```  
  
 <span data-ttu-id="5359a-116">您甚至可以在單一資料行中結合搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="5359a-116">You can even combine search conditions on a single column.</span></span> <span data-ttu-id="5359a-117">例如，以下準則即結合了區域資料行的兩個條件：</span><span class="sxs-lookup"><span data-stu-id="5359a-117">For example, the following criterion combines two conditions on the region column:</span></span>  
  
```  
region = 'UK' OR region = 'US'  
```  
  
 <span data-ttu-id="5359a-118">如需結合搜尋條件的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="5359a-118">For details about combining search conditions, see the following topics:</span></span>  
  
-   [<span data-ttu-id="5359a-119">在條件窗格中合併搜尋條件的慣例 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="5359a-119">Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;</span></span>](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md)  
  
-   [<span data-ttu-id="5359a-120">指定單一資料行的多重搜尋條件 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="5359a-120">Specify Multiple Search Conditions for One Column &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
-   [<span data-ttu-id="5359a-121">指定多重資料行的多重搜尋條件 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="5359a-121">Specify Multiple Search Conditions for Multiple Columns &#40;Visual Database Tools&#41;</span></span>](specify-multiple-search-conditions-for-multiple-columns-visual-database-tools.md)  
  
-   [<span data-ttu-id="5359a-122">在 AND 具有優先權時結合條件 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="5359a-122">Combine Conditions When AND Has Precedence &#40;Visual Database Tools&#41;</span></span>](combine-conditions-when-and-has-precedence-visual-database-tools.md)  
  
-   [<span data-ttu-id="5359a-123">在 OR 具有優先權時結合條件 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="5359a-123">Combine Conditions When OR Has Precedence &#40;Visual Database Tools&#41;</span></span>](combine-conditions-when-or-has-precedence-visual-database-tools.md)  
  
## <a name="examples"></a><span data-ttu-id="5359a-124">範例</span><span class="sxs-lookup"><span data-stu-id="5359a-124">Examples</span></span>  
 <span data-ttu-id="5359a-125">此處是使用不同運算子和資料列準則之查詢的一些範例：</span><span class="sxs-lookup"><span data-stu-id="5359a-125">Here are some examples of queries using various operators and row criteria:</span></span>  
  
-   <span data-ttu-id="5359a-126">**常值** ，單一文字、數字、日期或邏輯值。</span><span class="sxs-lookup"><span data-stu-id="5359a-126">**Literal** A single text, numeric, date, or logical value.</span></span> <span data-ttu-id="5359a-127">下例即使用常值搜尋所有資料列，尋找位於英國的員工：</span><span class="sxs-lookup"><span data-stu-id="5359a-127">The following example uses a literal to find all rows for employees in the United Kingdom:</span></span>  
  
    ```  
    WHERE region = 'UK'  
    ```  
  
-   <span data-ttu-id="5359a-128">**資料行參考** ：將某一資料行中的值與另一個資料行中的值進行比較。</span><span class="sxs-lookup"><span data-stu-id="5359a-128">**Column reference** Compares the values in one column with the values in another.</span></span> <span data-ttu-id="5359a-129">下例即搜尋 `products` 資料表中的所有資料列，其中生產成本的值低於貨運成本：</span><span class="sxs-lookup"><span data-stu-id="5359a-129">The following example searches a `products` table for all rows in which the value of the production cost is lower than the shipping cost:</span></span>  
  
    ```  
    WHERE prod_cost < ship_cost  
    ```  
  
-   <span data-ttu-id="5359a-130">**函數** ：函數的參考，資料庫後端可解析該函數以計算搜尋的值。</span><span class="sxs-lookup"><span data-stu-id="5359a-130">**Function** A reference to a function that the database back-end can resolve to calculate a value for the search.</span></span> <span data-ttu-id="5359a-131">函數可以是資料庫伺服器所定義的函數，或傳回純量值的使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="5359a-131">The function can be a function defined by the database server or a user-defined function that returns a scalar value.</span></span> <span data-ttu-id="5359a-132">下列範例即搜尋今天所發出的訂單 (GETDATE( ) 函數將傳回目前日期)：</span><span class="sxs-lookup"><span data-stu-id="5359a-132">The following example searches for orders placed today (the GETDATE( ) function returns the current date):</span></span>  
  
    ```  
    WHERE order_date = GETDATE()  
    ```  
  
-   <span data-ttu-id="5359a-133">**NULL** ，下列範例將在 `authors` 資料表中搜尋檔案中出現其名字的所有作者：</span><span class="sxs-lookup"><span data-stu-id="5359a-133">**NULL** The following example searches an `authors` table for all authors who have a first name on file:</span></span>  
  
    ```  
    WHERE au_fname IS NOT NULL  
    ```  
  
-   <span data-ttu-id="5359a-134">**計算** ：計算的結果可能是常值、資料行參考或其他運算式。</span><span class="sxs-lookup"><span data-stu-id="5359a-134">**Calculation** The result of a calculation that can involve literals, column references, or other expressions.</span></span> <span data-ttu-id="5359a-135">下列範例中即在 `products` 資料表中搜尋所有資料列，其中尋找零售價格是生產價格的兩倍：</span><span class="sxs-lookup"><span data-stu-id="5359a-135">The following example searches a `products` table to find all rows in which the retail sales price is more than twice the production cost:</span></span>  
  
    ```  
    WHERE sales_price > (prod_cost * 2)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5359a-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5359a-136">See Also</span></span>  
 <span data-ttu-id="5359a-137">[設計查詢和觀看 how to 主題 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="5359a-137">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="5359a-138">[&#40;Visual Database Tools 指定搜尋準則&#41;](specify-search-criteria-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="5359a-138">[Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="5359a-139">使用參數查詢 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="5359a-139">Query with Parameters &#40;Visual Database Tools&#41;</span></span>](query-with-parameters-visual-database-tools.md)  
  
  
