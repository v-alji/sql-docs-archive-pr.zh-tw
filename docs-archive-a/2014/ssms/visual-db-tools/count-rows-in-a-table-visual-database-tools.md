---
title: 計算資料表中的資料列 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- totals [SQL Server], row counts
- row counts [SQL Server]
- column values [SQL Server]
- number of rows
- number of values
- counting rows
ms.assetid: dda4296a-1d16-4e77-8d6f-e295f6dd4e87
author: stevestein
ms.author: sstein
ms.openlocfilehash: f6dca92fb955b776f56d9b51f28b1a486b89f18f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700513"
---
# <a name="count-rows-in-a-table-visual-database-tools"></a><span data-ttu-id="e16c9-102">計算資料表中的資料列 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e16c9-102">Count Rows in a Table (Visual Database Tools)</span></span>
  <span data-ttu-id="e16c9-103">您可以計算資料表中的資料列，以判斷：</span><span class="sxs-lookup"><span data-stu-id="e16c9-103">You can count rows in a table to determine:</span></span>  
  
-   <span data-ttu-id="e16c9-104">在資料表中的資料列總數，例如，在 `titles` 資料表中所有書籍的計數。</span><span class="sxs-lookup"><span data-stu-id="e16c9-104">The total number of rows in a table, for example, a count of all the books in a `titles` table.</span></span>  
  
-   <span data-ttu-id="e16c9-105">符合特定條件的資料表資料列數目，例如，在 `titles` 資料表中某簽發者的書籍數目。</span><span class="sxs-lookup"><span data-stu-id="e16c9-105">The number of rows in a table that meet a specific condition, for example, the number of books by one publisher in a `titles` table.</span></span>  
  
-   <span data-ttu-id="e16c9-106">特定資料行中的值數目。</span><span class="sxs-lookup"><span data-stu-id="e16c9-106">The number of values in a particular column.</span></span>  
  
 <span data-ttu-id="e16c9-107">在計算資料行中的值時，null 不包含在計數中。</span><span class="sxs-lookup"><span data-stu-id="e16c9-107">When you count values in a column, nulls are not included in the count.</span></span> <span data-ttu-id="e16c9-108">例如，您可能會計算 `titles` 資料表中 `advance` 資料行有值的書籍數目。</span><span class="sxs-lookup"><span data-stu-id="e16c9-108">For example, you might count the number of books in a `titles` table that have values in the `advance` column.</span></span> <span data-ttu-id="e16c9-109">依照預設，計數包含所有的值，而不只是唯一的值。</span><span class="sxs-lookup"><span data-stu-id="e16c9-109">By default, the count includes all values, not just unique values.</span></span>  
  
 <span data-ttu-id="e16c9-110">所有三種類型計數的程序都相互類似。</span><span class="sxs-lookup"><span data-stu-id="e16c9-110">The procedures for all three types of counts are similar.</span></span>  
  
### <a name="to-count-all-the-rows-in-a-table"></a><span data-ttu-id="e16c9-111">若要計算資料表中的所有資料列</span><span class="sxs-lookup"><span data-stu-id="e16c9-111">To count all the rows in a table</span></span>  
  
1.  <span data-ttu-id="e16c9-112">請確定您要摘要的資料表已經出現在 [圖表] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="e16c9-112">Be sure the table you want to summarize is already present in the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="e16c9-113">在 [圖表] 窗格的背景上按一下滑鼠右鍵，然後從快速鍵功能表中選擇 [新增群組依據]  。</span><span class="sxs-lookup"><span data-stu-id="e16c9-113">Right-click the background of the Diagram pane, then choose **Add Group By** from the shortcut menu.</span></span> <span data-ttu-id="e16c9-114">[查詢和檢視表設計工具](visual-database-tools.md)會將 [群組依據]  資料行新增至 [準則] 窗格的方格中。</span><span class="sxs-lookup"><span data-stu-id="e16c9-114">The [Query and View Designer](visual-database-tools.md) adds a **Group By** column to the grid in the Criteria pane.</span></span>  
  
3.  <span data-ttu-id="e16c9-115">在代表資料表或資料表值物件的矩形中，選取 [ \*\* \* () 的所有資料行\*\*。</span><span class="sxs-lookup"><span data-stu-id="e16c9-115">Select **\* (All Columns)** in the rectangle representing the table or table-valued object.</span></span>  
  
     <span data-ttu-id="e16c9-116">查詢和檢視表設計工具會自動將 [計數]  一詞填入至 [準則] 窗格的 [群組依據]  資料行，並且將資料行別名指定至您所摘要的資料行。</span><span class="sxs-lookup"><span data-stu-id="e16c9-116">The Query and View Designer automatically fills the term **Count** into the **Group By** column in the Criteria pane and assigns a column alias to the column you are summarizing.</span></span> <span data-ttu-id="e16c9-117">您可以使用較有意義的別名取代這個自動產生的別名。</span><span class="sxs-lookup"><span data-stu-id="e16c9-117">You can replace this automatically generated alias with a more meaningful one.</span></span> <span data-ttu-id="e16c9-118">如需詳細資訊，請參閱[建立資料行別名 &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="e16c9-118">For more details, see [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
4.  <span data-ttu-id="e16c9-119">執行查詢。</span><span class="sxs-lookup"><span data-stu-id="e16c9-119">Run the query.</span></span>  
  
### <a name="to-count-all-the-rows-that-meet-a-condition"></a><span data-ttu-id="e16c9-120">若要計算符合條件的所有資料列</span><span class="sxs-lookup"><span data-stu-id="e16c9-120">To count all the rows that meet a condition</span></span>  
  
1.  <span data-ttu-id="e16c9-121">請確定您要摘要的資料表已經出現在 [圖表] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="e16c9-121">Be sure the table you want to summarize is already present in the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="e16c9-122">在 [圖表] 窗格的背景上按一下滑鼠右鍵，然後從快速鍵功能表中選擇 [新增群組依據]  。</span><span class="sxs-lookup"><span data-stu-id="e16c9-122">Right-click the background of the Diagram pane, then choose **Add Group By** from the shortcut menu.</span></span> <span data-ttu-id="e16c9-123">查詢和檢視表設計工具會將 [群組依據]  資料行新增至 [準則] 窗格的方格中。</span><span class="sxs-lookup"><span data-stu-id="e16c9-123">The Query and View Designer adds a **Group By** column to the grid in the Criteria pane.</span></span>  
  
3.  <span data-ttu-id="e16c9-124">在代表資料表或資料表結構化物件的矩形中，選取 [ \*\* \* (所有資料行) \*\* 。</span><span class="sxs-lookup"><span data-stu-id="e16c9-124">Select **\*(All Columns)** in the rectangle representing the table or table-structured object.</span></span>  
  
     <span data-ttu-id="e16c9-125">查詢和檢視表設計工具會自動將 [計數]  一詞填入至 [準則] 窗格的 [群組依據]  資料行，並且將資料行別名指定至您所摘要的資料行。</span><span class="sxs-lookup"><span data-stu-id="e16c9-125">The Query and View Designer automatically fills the term **Count** into the **Group By** column in the Criteria pane and assigns a column alias to the column you are summarizing.</span></span> <span data-ttu-id="e16c9-126">若要在查詢輸出中建立更有用的資料行標題，請參閱[建立資料行別名 &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="e16c9-126">To create a more useful column heading in query output, see [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
4.  <span data-ttu-id="e16c9-127">新增要搜尋的資料行，然後清除 [輸出]  資料行中的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e16c9-127">Add the data column that you want to search, and then clear the check box in the **Output** column.</span></span>  
  
     <span data-ttu-id="e16c9-128">查詢和檢視表設計工具會自動將 [群組依據]  一詞填入至方格的 [群組依據]  資料行中。</span><span class="sxs-lookup"><span data-stu-id="e16c9-128">The Query and View Designer automatically fills the term **Group By** into the **Group By** column of the grid.</span></span>  
  
5.  <span data-ttu-id="e16c9-129">將 [群組依據]  資料行中的 [群組依據]  變更為 [Where]  。</span><span class="sxs-lookup"><span data-stu-id="e16c9-129">Change **Group By** in the **Group By** column to **Where**.</span></span>  
  
6.  <span data-ttu-id="e16c9-130">在想要搜尋資料行的 [過濾]  資料行中，輸入搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="e16c9-130">In the **Filter** column for the data column to search, enter the search condition.</span></span>  
  
7.  <span data-ttu-id="e16c9-131">執行查詢。</span><span class="sxs-lookup"><span data-stu-id="e16c9-131">Run the query.</span></span>  
  
### <a name="to-count-the-values-in-a-column"></a><span data-ttu-id="e16c9-132">若要計算資料行中的值</span><span class="sxs-lookup"><span data-stu-id="e16c9-132">To count the values in a column</span></span>  
  
1.  <span data-ttu-id="e16c9-133">請確定您要摘要的資料表已經出現在 [圖表] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="e16c9-133">Be sure the table you want to summarize is already present in the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="e16c9-134">在 [圖表] 窗格的背景上按一下滑鼠右鍵，然後從快速鍵功能表中選擇 [新增群組依據]  。</span><span class="sxs-lookup"><span data-stu-id="e16c9-134">Right-click the background of the Diagram pane, then choose **Add Group By** from the shortcut menu.</span></span> <span data-ttu-id="e16c9-135">查詢和檢視表設計工具會將 [群組依據]  資料行新增至 [準則] 窗格的方格中。</span><span class="sxs-lookup"><span data-stu-id="e16c9-135">The Query and View Designer adds a **Group By** column to the grid in the Criteria pane.</span></span>  
  
3.  <span data-ttu-id="e16c9-136">將您要計算的資料行加入至 [準則] 窗格。</span><span class="sxs-lookup"><span data-stu-id="e16c9-136">Add the column that you want to count to the Criteria pane.</span></span>  
  
     <span data-ttu-id="e16c9-137">查詢和檢視表設計工具會自動將 [群組依據]  一詞填入至方格的 [群組依據]  資料行中。</span><span class="sxs-lookup"><span data-stu-id="e16c9-137">The Query and View Designer automatically fills the term **Group By** into the **Group By** column of the grid.</span></span>  
  
4.  <span data-ttu-id="e16c9-138">將 [群組依據]  資料行中的 [群組依據]  變更為 [計數]  。</span><span class="sxs-lookup"><span data-stu-id="e16c9-138">Change **Group By** in the **Group By** column to **Count**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e16c9-139">若只要計算唯一的值，則選擇 [Count Distinct]  。</span><span class="sxs-lookup"><span data-stu-id="e16c9-139">To count only unique values, choose **Count Distinct**.</span></span>  
  
5.  <span data-ttu-id="e16c9-140">執行查詢。</span><span class="sxs-lookup"><span data-stu-id="e16c9-140">Run the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e16c9-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e16c9-141">See Also</span></span>  
 <span data-ttu-id="e16c9-142">[排序和分組查詢結果 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="e16c9-142">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="e16c9-143">摘要查詢結果 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="e16c9-143">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
  
  
