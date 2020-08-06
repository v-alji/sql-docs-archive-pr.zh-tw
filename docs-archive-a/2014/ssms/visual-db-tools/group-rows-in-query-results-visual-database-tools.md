---
title: 將查詢結果中的資料列分組 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing table subsets
- grouping rows
- grouping query results
ms.assetid: b07082d5-4d55-4903-9af9-4c470554c6d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 52de25c86425d95f5917d89c8a3f4fec8939fb16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596983"
---
# <a name="group-rows-in-query-results-visual-database-tools"></a><span data-ttu-id="e9a12-102">群組查詢結果中的資料列 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e9a12-102">Group Rows in Query Results (Visual Database Tools)</span></span>
  <span data-ttu-id="e9a12-103">如果您要建立小計，或顯示資料表子集的其他摘要資訊，請使用彙總查詢 (Aggregate Query) 建立群組。</span><span class="sxs-lookup"><span data-stu-id="e9a12-103">If you want to create subtotals or show other summary information for subsets of a table, you create groups using an aggregate query.</span></span> <span data-ttu-id="e9a12-104">每個群組都會針對資料表中具有相同值的所有資料列摘要資料。</span><span class="sxs-lookup"><span data-stu-id="e9a12-104">Each group summarizes the data for all the rows in the table that have the same value.</span></span>  
  
 <span data-ttu-id="e9a12-105">例如，您可能想查看 `titles` 資料表中某本書的平均價格，但是想依照簽發者顯示結果。</span><span class="sxs-lookup"><span data-stu-id="e9a12-105">For example, you might want to see the average price of a book in the `titles` table, but break the results down by publisher.</span></span> <span data-ttu-id="e9a12-106">若要這麼做，請依照簽發者將查詢分組 (例如， `pub_id`)。</span><span class="sxs-lookup"><span data-stu-id="e9a12-106">To do so, you group the query by publisher (for example, `pub_id`).</span></span> <span data-ttu-id="e9a12-107">結果查詢輸出可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="e9a12-107">The resulting query output might look like this:</span></span>  
  
 <span data-ttu-id="e9a12-108">![查詢結果：依發行者分組的平均價格](../../database-engine/media//dv3w9e1.gif "查詢結果：依發行者分組的平均價格")</span><span class="sxs-lookup"><span data-stu-id="e9a12-108">![Query results: average price grouped by publisher](../../database-engine/media//dv3w9e1.gif "Query results: average price grouped by publisher")</span></span>  
  
 <span data-ttu-id="e9a12-109">將資料分組時，您只能顯示摘要或分組的資料，例如：</span><span class="sxs-lookup"><span data-stu-id="e9a12-109">When you group data, you can display only summary or grouped data, such as:</span></span>  
  
-   <span data-ttu-id="e9a12-110">分組資料行 (出現在 GROUP BY 子句中的資料行) 的值。</span><span class="sxs-lookup"><span data-stu-id="e9a12-110">The values of the grouped columns (those that appear in the GROUP BY clause).</span></span> <span data-ttu-id="e9a12-111">在上述範例中， `pub_id` 就是分組資料行。</span><span class="sxs-lookup"><span data-stu-id="e9a12-111">In the example above, `pub_id` is the grouped column.</span></span>  
  
-   <span data-ttu-id="e9a12-112">SUM( ) 及 AVG( ) 之類彙總函式所產生的值。</span><span class="sxs-lookup"><span data-stu-id="e9a12-112">Values produced by aggregate functions such as SUM( ) and AVG( ).</span></span> <span data-ttu-id="e9a12-113">在上列的範例中，第二個資料行是使用 AVG( ) 函數及 `price` 資料行所產生的。</span><span class="sxs-lookup"><span data-stu-id="e9a12-113">In the example above, the second column is produced by using the AVG( ) function with the `price` column.</span></span>  
  
 <span data-ttu-id="e9a12-114">您不能顯示個別資料列的值。</span><span class="sxs-lookup"><span data-stu-id="e9a12-114">You cannot display values from individual rows.</span></span> <span data-ttu-id="e9a12-115">例如，如果您只依照簽發者分組，就不能在查詢中顯示個別標題。</span><span class="sxs-lookup"><span data-stu-id="e9a12-115">For example, if you group only by publisher, you cannot also display individual titles in the query.</span></span> <span data-ttu-id="e9a12-116">因此，如果您將資料行新增至查詢輸出， [查詢和檢視表設計工具](visual-database-tools.md) 就會自動將這些資料行新增至 [SQL 窗格](sql-pane-visual-database-tools.md)中的陳述式 GROUP BY 子句。</span><span class="sxs-lookup"><span data-stu-id="e9a12-116">Therefore, if you add columns to the query output, the [Query and View Designer](visual-database-tools.md) automatically adds them to the GROUP BY clause of the statement in the [SQL pane](sql-pane-visual-database-tools.md).</span></span> <span data-ttu-id="e9a12-117">如果您要改為彙總資料行，您可以針對該資料行指定彙總函式。</span><span class="sxs-lookup"><span data-stu-id="e9a12-117">If you want a column to be aggregated instead, you can specify an aggregate function for that column.</span></span>  
  
 <span data-ttu-id="e9a12-118">如果您依照一個以上的資料行分組，查詢中的每個群組便會顯示所有群組資料行的彙總值。</span><span class="sxs-lookup"><span data-stu-id="e9a12-118">If you group by more than one column, each group in the query shows the aggregate values for all grouping columns.</span></span>  
  
 <span data-ttu-id="e9a12-119">例如，下列針對 `titles` 執行的查詢同時依照簽發者 (`pub_id`) 以及書籍類型 (`type`) 進行分組。</span><span class="sxs-lookup"><span data-stu-id="e9a12-119">For example, the following query against the `titles` table groups by publisher (`pub_id`) and also by book type (`type`).</span></span> <span data-ttu-id="e9a12-120">查詢結果將依照簽發者的順序排列，並顯示簽發者出版的每一種不同書籍類型的摘要資訊：</span><span class="sxs-lookup"><span data-stu-id="e9a12-120">The query results are ordered by publisher and show summary information for each different type of book that the publisher produces:</span></span>  
  
```  
SELECT pub_id, type, SUM(price) Total_price  
FROM titles  
GROUP BY pub_id, type  
```  
  
 <span data-ttu-id="e9a12-121">產生的輸出將如下所示：</span><span class="sxs-lookup"><span data-stu-id="e9a12-121">The resulting output might look like this:</span></span>  
  
 <span data-ttu-id="e9a12-122">![查詢結果：依發行者和類型分組的價格](../../database-engine/media//dv3w9e2.gif "查詢結果：依發行者和類型分組的價格")</span><span class="sxs-lookup"><span data-stu-id="e9a12-122">![Query results: price grouped by publisher and type](../../database-engine/media//dv3w9e2.gif "Query results: price grouped by publisher and type")</span></span>  
  
### <a name="to-group-rows"></a><span data-ttu-id="e9a12-123">若要將資料列分組</span><span class="sxs-lookup"><span data-stu-id="e9a12-123">To group rows</span></span>  
  
1.  <span data-ttu-id="e9a12-124">將您要摘要的資料表加入至 [圖表] 窗格，以便開始進行查詢。</span><span class="sxs-lookup"><span data-stu-id="e9a12-124">Start the query by adding the tables you want to summarize to the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="e9a12-125">在 [圖表] 窗格的背景上按一下滑鼠右鍵，然後從快速鍵功能表中選擇 [新增群組依據]  。</span><span class="sxs-lookup"><span data-stu-id="e9a12-125">Right-click the background of the Diagram pane, then choose **Add Group By** from the shortcut menu.</span></span> <span data-ttu-id="e9a12-126">查詢和檢視表設計工具會將 [群組依據]  資料行新增至 [準則] 窗格的方格中。</span><span class="sxs-lookup"><span data-stu-id="e9a12-126">The Query and View Designer adds a **Group By** column to the grid in the Criteria pane.</span></span>  
  
3.  <span data-ttu-id="e9a12-127">將您想分組的一或多個資料行加入至 [準則] 窗格。</span><span class="sxs-lookup"><span data-stu-id="e9a12-127">Add the column or columns you want to group to the Criteria pane.</span></span> <span data-ttu-id="e9a12-128">如果您想讓資料行出現在查詢輸出中，務必選取 [輸出]  資料行進行輸出。</span><span class="sxs-lookup"><span data-stu-id="e9a12-128">If you want the column to appear in the query output, be sure that the **Output** column is selected for output.</span></span>  
  
     <span data-ttu-id="e9a12-129">查詢和檢視設計師會將 GROUP BY 子句加入至 [SQL] 窗格的陳述式中。</span><span class="sxs-lookup"><span data-stu-id="e9a12-129">The Query and View Designer adds a GROUP BY clause to the statement in the SQL pane.</span></span> <span data-ttu-id="e9a12-130">例如，SQL 陳述式將如下所示：</span><span class="sxs-lookup"><span data-stu-id="e9a12-130">For example, the SQL statement might look like this:</span></span>  
  
    ```  
    SELECT pub_id  
    FROM titles  
    GROUP BY pub_id  
    ```  
  
4.  <span data-ttu-id="e9a12-131">將您想彙總的一或多個資料行加入至 [準則] 窗格。</span><span class="sxs-lookup"><span data-stu-id="e9a12-131">Add the column or columns you want to aggregate to the Criteria pane.</span></span> <span data-ttu-id="e9a12-132">務必標記資料行以進行輸出。</span><span class="sxs-lookup"><span data-stu-id="e9a12-132">Be sure that the column is marked for output.</span></span>  
  
5.  <span data-ttu-id="e9a12-133">在要彙總資料行的 [群組依據]  方格資料格中，選取適當的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="e9a12-133">In the **Group By** grid cell for the column that is going to be aggregated, select the appropriate aggregate function.</span></span>  
  
     <span data-ttu-id="e9a12-134">[查詢和檢視表設計工具] 會自動將資料行別名指派給您要加總的資料行。</span><span class="sxs-lookup"><span data-stu-id="e9a12-134">The Query and View Designer automatically assigns a column alias to the column you are summarizing.</span></span> <span data-ttu-id="e9a12-135">您可以使用較有意義的別名取代這個自動產生的別名。</span><span class="sxs-lookup"><span data-stu-id="e9a12-135">You can replace this automatically generated alias with a more meaningful one.</span></span> <span data-ttu-id="e9a12-136">如需詳細資訊，請參閱[建立資料行別名 &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="e9a12-136">For more details, see [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
     <span data-ttu-id="e9a12-137">![將資料行別名新增至查詢結果集](../../database-engine/media//dv3w9e3.gif "將資料行別名新增至查詢結果集")</span><span class="sxs-lookup"><span data-stu-id="e9a12-137">![Adding a column alias to the query result set](../../database-engine/media//dv3w9e3.gif "Adding a column alias to the query result set")</span></span>  
  
     <span data-ttu-id="e9a12-138">[SQL]  窗格中的對應陳述式將如下所示：</span><span class="sxs-lookup"><span data-stu-id="e9a12-138">The corresponding statement in the **SQL** pane might look like this:</span></span>  
  
    ```  
    SELECT   pub_id, SUM(price) AS Totalprice  
    FROM     titles  
    GROUP BY pub_id  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e9a12-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9a12-139">See Also</span></span>  
 [<span data-ttu-id="e9a12-140">排序及分組查詢結果 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="e9a12-140">Sort and Group Query Results &#40;Visual Database Tools&#41;</span></span>](sort-and-group-query-results-visual-database-tools.md)  
  
  
