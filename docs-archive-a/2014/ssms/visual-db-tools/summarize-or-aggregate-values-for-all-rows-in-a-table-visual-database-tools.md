---
title: 摘要或匯總資料表中所有資料列的值 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing query results
- aggregate functions [SQL Server], summarizing query results
ms.assetid: f5af876e-f937-4110-ba09-07999c35a699
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5c4d80c8ab2b811b8e796f0a37b2180a2866c332
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704626"
---
# <a name="summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools"></a><span data-ttu-id="23e7d-102">摘要或彙總資料表中所有資料列的值 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="23e7d-102">Summarize or Aggregate Values for All Rows in a Table (Visual Database Tools)</span></span>
  <span data-ttu-id="23e7d-103">使用彙總函式 (Aggregate Function) 可以在資料表中建立所有值的摘要。</span><span class="sxs-lookup"><span data-stu-id="23e7d-103">Using an aggregate function, you can create a summary for all the values in a table.</span></span> <span data-ttu-id="23e7d-104">例如，您可以建立如下所示的查詢，以顯示在 `titles` 資料表中所有書籍的總價格：</span><span class="sxs-lookup"><span data-stu-id="23e7d-104">For example, you can create a query such as the following to display the total price for all books in the `titles` table:</span></span>  
  
```  
SELECT SUM(price)  
FROM titles  
```  
  
 <span data-ttu-id="23e7d-105">您可以對多個資料行使用彙總函式，在相同查詢中建立多個彙總。</span><span class="sxs-lookup"><span data-stu-id="23e7d-105">You can create multiple aggregations in the same query by using aggregate functions with more than one column.</span></span> <span data-ttu-id="23e7d-106">例如，您可以建立計算 `price` 資料行總計和 `discount` 資料行平均的查詢。</span><span class="sxs-lookup"><span data-stu-id="23e7d-106">For example, you can create a query that calculates the total of the `price` column and the average of the `discount` column.</span></span>  
  
 <span data-ttu-id="23e7d-107">在相同查詢中，您也可以使用不同的方法彙總相同的資料行 (例如加總、計數和平均)。</span><span class="sxs-lookup"><span data-stu-id="23e7d-107">You can also aggregate the same column in different ways (such as totaling, counting, and averaging) in the same query.</span></span> <span data-ttu-id="23e7d-108">例如，下列查詢會平均並加總 `price` 資料表的 `titles` 資料行：</span><span class="sxs-lookup"><span data-stu-id="23e7d-108">For example, the following query averages and summarizes the `price` column from the `titles` table:</span></span>  
  
```  
SELECT AVG(price), SUM(price)  
FROM titles  
```  
  
 <span data-ttu-id="23e7d-109">如果加入搜尋條件，您可以彙總符合條件的資料列子集。</span><span class="sxs-lookup"><span data-stu-id="23e7d-109">If you add a search condition, you can aggregate the subset of rows that meet that condition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="23e7d-110">您可以計算資料表中的所有資料列，或計算符合指定條件的資料列。</span><span class="sxs-lookup"><span data-stu-id="23e7d-110">You can also count all the rows in the table or the ones that meet a specific condition.</span></span> <span data-ttu-id="23e7d-111">如需詳細資訊，請參閱[計算資料表中的資料列 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="23e7d-111">For details, see [Count Rows in a Table &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="23e7d-112">在建立資料表中所有資料列的單一彙總值時，只顯示彙總值本身。</span><span class="sxs-lookup"><span data-stu-id="23e7d-112">When you create a single aggregation value for all rows in a table, you display only the aggregate values themselves.</span></span> <span data-ttu-id="23e7d-113">例如，如果加總 `price` 資料表的 `titles` 資料行值，將不會顯示個別的書名、出版者名稱等等。</span><span class="sxs-lookup"><span data-stu-id="23e7d-113">For example, if you are totaling the value of the `price` column of the `titles` table, you would not also display individual titles, publisher names, and so on.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="23e7d-114">如果進行小計，也就是建立群組，可以顯示每個群組的資料行值。</span><span class="sxs-lookup"><span data-stu-id="23e7d-114">If you are subtotaling - that is, creating groups - you can display column values for each group.</span></span> <span data-ttu-id="23e7d-115">如需詳細資訊，請參閱[群組查詢結果中的資料列 &#40;Visual Database Tools&#41;](group-rows-in-query-results-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="23e7d-115">For details, see [Group Rows in Query Results &#40;Visual Database Tools&#41;](group-rows-in-query-results-visual-database-tools.md).</span></span>  
  
### <a name="to-aggregate-values-for-all-rows"></a><span data-ttu-id="23e7d-116">若要彙總所有資料列的值</span><span class="sxs-lookup"><span data-stu-id="23e7d-116">To aggregate values for all rows</span></span>  
  
1.  <span data-ttu-id="23e7d-117">請確定您要彙總的資料表已經出現在 [圖表] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="23e7d-117">Be sure the table you want to aggregate is already present in the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="23e7d-118">在 [圖表] 窗格的背景上按一下滑鼠右鍵，然後從快速鍵功能表中選擇 [群組依據]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23e7d-118">Right-click the background of the Diagram pane, then choose **Group By** from the shortcut menu.</span></span> <span data-ttu-id="23e7d-119">[查詢和視圖設計](query-and-view-designer-tools-visual-database-tools.md)工具會將 [**群組依據**] 資料行加入至 [準則] 窗格中的方格。</span><span class="sxs-lookup"><span data-stu-id="23e7d-119">The [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) adds a **Group By** column to the grid in the Criteria pane.</span></span>  
  
3.  <span data-ttu-id="23e7d-120">將您想彙總的資料行加入至 [準則] 窗格。</span><span class="sxs-lookup"><span data-stu-id="23e7d-120">Add the column you want to aggregate to the Criteria pane.</span></span> <span data-ttu-id="23e7d-121">務必標記資料行以進行輸出。</span><span class="sxs-lookup"><span data-stu-id="23e7d-121">Be sure that the column is marked for output.</span></span>  
  
     <span data-ttu-id="23e7d-122">[查詢和檢視表設計工具] 會自動將資料行別名指派給您要加總的資料行。</span><span class="sxs-lookup"><span data-stu-id="23e7d-122">The Query and View Designer automatically assigns a column alias to the column you are summarizing.</span></span> <span data-ttu-id="23e7d-123">您可以使用較有意義的別名取代這個別名。</span><span class="sxs-lookup"><span data-stu-id="23e7d-123">You can replace this alias with a more meaningful one.</span></span> <span data-ttu-id="23e7d-124">如需詳細資訊，請參閱[建立資料行別名 &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="23e7d-124">For details, see [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
4.  <span data-ttu-id="23e7d-125">在 [群組依據]\*\*\*\* 方格資料行中，選取適當的彙總函式，例如：[Sum]\*\*\*\*、[Avg]\*\*\*\*、[Min]\*\*\*\*、[Max]\*\*\*\*、[Count]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23e7d-125">In the **Group By** grid column, select the appropriate aggregate function, such as: **Sum**, **Avg**, **Min**, **Max**, **Count**.</span></span> <span data-ttu-id="23e7d-126">如果只要彙總結果集中的唯一資料列，請選擇含有 DISTINCT 選項的彙總函式，例如 [Min Distinct]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23e7d-126">If you want to aggregate only unique rows in the result set, choose an aggregate function with the DISTINCT options, such as **Min Distinct**.</span></span> <span data-ttu-id="23e7d-127">不要選擇 [Group By]\*\*\*\*、[Expression]\*\*\*\* 或 [Where]\*\*\*\*，因為這些選項不適用於彙總所有資料列。</span><span class="sxs-lookup"><span data-stu-id="23e7d-127">Do not choose **Group By**, **Expression**, or **Where**, because those options do not apply when you are aggregating all rows.</span></span>  
  
     <span data-ttu-id="23e7d-128">查詢和檢視表設計工具會使用指定的彙總函式，取代 [SQL 窗格](sql-pane-visual-database-tools.md)中陳述式的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="23e7d-128">The Query and View Designer replaces the column name in the statement in the [SQL pane](sql-pane-visual-database-tools.md) with the aggregate function that you specify.</span></span> <span data-ttu-id="23e7d-129">例如，SQL 陳述式將如下所示：</span><span class="sxs-lookup"><span data-stu-id="23e7d-129">For example, the SQL statement might look like this:</span></span>  
  
    ```  
    SELECT SUM(price)  
    FROM titles  
    ```  
  
5.  <span data-ttu-id="23e7d-130">若要在查詢中建立一個以上的彙總，請重複步驟 3 和 4。</span><span class="sxs-lookup"><span data-stu-id="23e7d-130">If you want to create more than one aggregation in the query, repeat steps 3 and 4.</span></span>  
  
     <span data-ttu-id="23e7d-131">當其他資料行新增至查詢輸出清單或排序依據清單時，查詢和檢視表設計工具會自動將 [群組依據]\*\*\*\* 一詞填入至方格的 [群組依據] 資料行\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23e7d-131">When you add another column to the query output list or order by list, the Query and View Designer automatically fills the term **Group By** into the **Group By** column of the grid.</span></span> <span data-ttu-id="23e7d-132">選取適當的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="23e7d-132">Select the appropriate aggregate function.</span></span>  
  
6.  <span data-ttu-id="23e7d-133">加入搜尋條件 (如果有)，以指定要加總的資料列子集。</span><span class="sxs-lookup"><span data-stu-id="23e7d-133">Add search conditions, if any, to specify the subset of rows you want to summarize.</span></span>  
  
 <span data-ttu-id="23e7d-134">在執行查詢時，[結果] 窗格會顯示指定的彙總。</span><span class="sxs-lookup"><span data-stu-id="23e7d-134">When you execute the query, the Results pane displays the aggregations that you specified.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="23e7d-135">[查詢和檢視表設計工具] 會在 [SQL] 窗格中將彙總函式保持為 SQL 陳述式的一部分，直到明確關閉 [群組依據] 模式為止。</span><span class="sxs-lookup"><span data-stu-id="23e7d-135">The Query and View Designer maintains aggregate functions as part of the SQL statement in the SQL pane until you explicitly turn off Group By mode.</span></span> <span data-ttu-id="23e7d-136">因此，如果您變更查詢類型，或變更在 [圖表] 窗格中顯示的資料表或資料表值物件，以便修改查詢，則結果查詢可能會包含無效的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="23e7d-136">Therefore, if you modify your query by changing its type or by changing which tables or table-valued objects are present in the Diagram pane, the resulting query might include invalid aggregate functions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23e7d-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23e7d-137">See Also</span></span>  
 <span data-ttu-id="23e7d-138">[排序和分組查詢結果 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="23e7d-138">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="23e7d-139">摘要查詢結果 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="23e7d-139">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
  
  
