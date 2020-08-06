---
title: 建立子查詢 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], subqueries
- nested queries
- subqueries [SQL Server], SQL pane
ms.assetid: 34f6b9b4-ca3a-4a4f-9594-36e513f1c547
author: stevestein
ms.author: sstein
ms.openlocfilehash: 540228839b9734992be008b5d4fb7d717176832e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596994"
---
# <a name="create-subqueries-visual-database-tools"></a><span data-ttu-id="a037b-102">建立子查詢 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="a037b-102">Create Subqueries (Visual Database Tools)</span></span>
  <span data-ttu-id="a037b-103">可以使用某個查詢的結果做為另一個查詢的輸入。</span><span class="sxs-lookup"><span data-stu-id="a037b-103">You can use the results of one query as the input for another.</span></span> <span data-ttu-id="a037b-104">子查詢的結果可以用來做為使用 IN( ) 函數、EXISTS 運算子或 FROM 子句的陳述式。</span><span class="sxs-lookup"><span data-stu-id="a037b-104">You can use the results of a subquery as a statement that uses the IN( ) function, the EXISTS operator, or the FROM clause.</span></span>  
  
 <span data-ttu-id="a037b-105">您可以在 [SQL] 窗格中直接輸入子查詢，也可以複製查詢，再貼入至另一個子查詢中，以建立子查詢。</span><span class="sxs-lookup"><span data-stu-id="a037b-105">You can create a subquery by entering it directly into the SQL pane or by copying a query and pasting it into another.</span></span>  
  
### <a name="to-define-a-subquery-in-the-sql-pane"></a><span data-ttu-id="a037b-106">若要在 SQL 窗格中定義子查詢</span><span class="sxs-lookup"><span data-stu-id="a037b-106">To define a subquery in the SQL pane</span></span>  
  
1.  <span data-ttu-id="a037b-107">建立主查詢。</span><span class="sxs-lookup"><span data-stu-id="a037b-107">Create the primary query.</span></span>  
  
2.  <span data-ttu-id="a037b-108">在 [SQL] 窗格中選取 SQL 陳述式，然後使用 [複製]  將查詢移至 [剪貼簿]。</span><span class="sxs-lookup"><span data-stu-id="a037b-108">In the SQL pane, select the SQL statement, and then use **Copy** to move the query to the Clipboard.</span></span>  
  
3.  <span data-ttu-id="a037b-109">起始新的查詢，然後使用 [貼上]  將第一個查詢移至新查詢的 WHERE 或 FROM 子句。</span><span class="sxs-lookup"><span data-stu-id="a037b-109">Start the new query, and then use **Paste** to move the first query into the new query's WHERE or FROM clause.</span></span>  
  
     <span data-ttu-id="a037b-110">例如，假設您有兩個資料表 `products` 和 `suppliers`，並且想建立顯示 Sweden 供應商的所有產品的查詢。</span><span class="sxs-lookup"><span data-stu-id="a037b-110">For example, imagine you have two tables, `products` and `suppliers`, and you want to create a query showing all products for suppliers in Sweden.</span></span> <span data-ttu-id="a037b-111">請先在 `suppliers` 資料表建立第一個查詢，以找出所有的 Swedish 供應商：</span><span class="sxs-lookup"><span data-stu-id="a037b-111">Create the first query on the `suppliers` table to find all Swedish suppliers:</span></span>  
  
    ```  
    SELECT supplier_id  
    FROM supplier  
    WHERE (country = 'Sweden')  
    ```  
  
     <span data-ttu-id="a037b-112">使用 [複製] 指令將此查詢移至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="a037b-112">Use the Copy command to move this query to the Clipboard.</span></span> <span data-ttu-id="a037b-113">建立使用 `products` 資料表的第二個查詢，以列出所需的產品資訊：</span><span class="sxs-lookup"><span data-stu-id="a037b-113">Create the second query using the `products` table, listing the information you need about products:</span></span>  
  
    ```  
    SELECT product_id, supplier_id, product_name  
    FROM products  
    ```  
  
     <span data-ttu-id="a037b-114">在 [SQL] 窗格中，將 WHERE 子句加入至第二個查詢，然後從剪貼簿貼入第一個查詢。</span><span class="sxs-lookup"><span data-stu-id="a037b-114">In the SQL pane, add a WHERE clause to the second query, then paste the first query from the Clipboard.</span></span> <span data-ttu-id="a037b-115">在第一個查詢加上括號，使其最終結果如下所示：</span><span class="sxs-lookup"><span data-stu-id="a037b-115">Place parentheses around the first query, so that the end result looks like this:</span></span>  
  
    ```  
    SELECT product_id, supplier_id, product_name  
    FROM products  
    WHERE supplier_id IN  
       (SELECT supplier_id  
      FROM supplier  
      WHERE (country = 'Sweden'))  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a037b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a037b-116">See Also</span></span>  
 <span data-ttu-id="a037b-117">[支援的查詢類型 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="a037b-117">[Supported Query Types &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="a037b-118">指定搜尋準則 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="a037b-118">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
