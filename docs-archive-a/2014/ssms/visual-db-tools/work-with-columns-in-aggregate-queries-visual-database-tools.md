---
title: 在彙總查詢中使用資料行 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- HAVING clause, query summary results
- GROUP BY clause, query summary results
- aggregate queries [SQL Server]
- WHERE clause, query summary results
ms.assetid: 1b82681f-3d4f-4b9a-bb1d-2060e44f2577
author: stevestein
ms.author: sstein
ms.openlocfilehash: 880f7529cebd7f51951e62952e3b5f13190f99b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686663"
---
# <a name="work-with-columns-in-aggregate-queries-visual-database-tools"></a><span data-ttu-id="9b69e-102">在彙總查詢中使用資料行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9b69e-102">Work with Columns in Aggregate Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="9b69e-103">當您建立彙總查詢時， [查詢和檢視表設計工具](visual-database-tools.md) 會做出特定假設，以便建構有效的查詢。</span><span class="sxs-lookup"><span data-stu-id="9b69e-103">When you create aggregate queries the [Query and View Designer](visual-database-tools.md) makes certain assumptions so that it can construct a valid query.</span></span> <span data-ttu-id="9b69e-104">例如，如果您要建立彙總查詢並標記某資料行進行輸出，查詢和檢視設計師會自動將該資料行變成 GROUP BY 子句的一部分，如此一來您便不會不慎在摘要中顯示個別資料列的內容。</span><span class="sxs-lookup"><span data-stu-id="9b69e-104">For example, if you are creating an aggregate query and mark a data column for output, the Query and View Designer automatically makes the column part of the GROUP BY clause so that you do not inadvertently attempt to display the contents of an individual row in a summary.</span></span>  
  
## <a name="using-group-by"></a><span data-ttu-id="9b69e-105">使用群組依據</span><span class="sxs-lookup"><span data-stu-id="9b69e-105">Using Group By</span></span>  
 <span data-ttu-id="9b69e-106">查詢和檢視設計師根據下列規則使用資料行：</span><span class="sxs-lookup"><span data-stu-id="9b69e-106">The Query and View Designer uses the following guidelines for working with columns:</span></span>  
  
-   <span data-ttu-id="9b69e-107">當您選擇 [群組依據] 選項或新增彙總函式至查詢時，所有標記為輸出或做為排序的資料行將自動新增至 GROUP BY 子句。</span><span class="sxs-lookup"><span data-stu-id="9b69e-107">When you choose the Group By option or add an aggregate function to a query, all columns marked for output or used for sorting are automatically added to the GROUP BY clause.</span></span> <span data-ttu-id="9b69e-108">如果資料行已經是彙總函式的一部分，則不會新增至 GROUP BY 子句。</span><span class="sxs-lookup"><span data-stu-id="9b69e-108">Columns are not automatically added to the GROUP BY clause if they are already part of an aggregate function.</span></span>  
  
     <span data-ttu-id="9b69e-109">如果您不想要特定資料行變成 GROUP BY 子句的一部分，必須在 [準則] 窗格的 [群組依據] 資料行中選取不同的選項來進行手動變更。</span><span class="sxs-lookup"><span data-stu-id="9b69e-109">If you do not want a particular column to be part of the GROUP BY clause, you must manually change it by selecting a different option in the Group By column of the Criteria pane.</span></span> <span data-ttu-id="9b69e-110">但查詢和檢視設計師無法阻止您選擇造成查詢無法執行的選項。</span><span class="sxs-lookup"><span data-stu-id="9b69e-110">However, the Query and View Designer will not prevent you from choosing an option that can result in a query that will not run.</span></span>  
  
-   <span data-ttu-id="9b69e-111">如果您手動新增查詢輸出資料行至 [準則] 或 [SQL] 窗格中的彙總函式，查詢和檢視設計師不會自動移除查詢的其他輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="9b69e-111">If you manually add a query output column to an aggregate function in either the Criteria or SQL pane, the Query and View Designer does not automatically remove other output columns from the query.</span></span> <span data-ttu-id="9b69e-112">因此您必須移除查詢輸出中的其他資料行，或將它們變成 GROUP BY 子句或彙總函式的一部分。</span><span class="sxs-lookup"><span data-stu-id="9b69e-112">Therefore, you must remove the remaining columns from the query output or make them part of the GROUP BY clause or of an aggregate function.</span></span>  
  
 <span data-ttu-id="9b69e-113">當您將搜尋條件輸入 [準則] 窗格的 [篩選條件] 資料行時，查詢和檢視設計師將遵守下列規則：</span><span class="sxs-lookup"><span data-stu-id="9b69e-113">When you enter a search condition into the Filter column of the Criteria pane, the Query and View Designer follows these rules:</span></span>  
  
-   <span data-ttu-id="9b69e-114">如果方格的 [群組依據]  資料行並未顯示 (因為您尚未指定彙總查詢)，則將搜尋條件放入 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="9b69e-114">If the **Group By** column of the grid is not displayed (because you have not yet specified an aggregate query), the search condition is placed into the WHERE clause.</span></span>  
  
-   <span data-ttu-id="9b69e-115">如果您已在彙總查詢中並已選取 [群組依據]  資料行中的 [Where]  選項，則將搜尋條件放入 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="9b69e-115">If you are already in an aggregate query and have selected the option **Where** in the **Group By** column, the search condition is placed into the WHERE clause.</span></span>  
  
-   <span data-ttu-id="9b69e-116">如果 [群組依據]  資料行中含有任何 [Where]  以外的值，則將搜尋條件放入 HAVING 子句。</span><span class="sxs-lookup"><span data-stu-id="9b69e-116">If the **Group By** column contains any value other than **Where**, the search condition is placed in the HAVING clause.</span></span>  
  
## <a name="using-the-having-and-where-clauses"></a><span data-ttu-id="9b69e-117">使用 HAVING 和 WHERE 子句</span><span class="sxs-lookup"><span data-stu-id="9b69e-117">Using the HAVING and WHERE Clauses</span></span>  
 <span data-ttu-id="9b69e-118">以下原則說明如何在搜尋條件中參考彙總查詢中的資料行。</span><span class="sxs-lookup"><span data-stu-id="9b69e-118">The following principles describe how you can reference columns in an aggregate query in search conditions.</span></span> <span data-ttu-id="9b69e-119">通常，您可以使用搜尋條件中的資料行來篩選應進行摘要的資料列 (WHERE 子句)，或決定最後輸出 (HAVING 子句) 中出現的群組結果。</span><span class="sxs-lookup"><span data-stu-id="9b69e-119">In general, you can use a column in a search condition to filter the rows that should be summarized (a WHERE clause) or to determine which grouped results appear in the final output (a HAVING clause).</span></span>  
  
-   <span data-ttu-id="9b69e-120">WHERE 或 HAVING 子句中可出現個別資料欄，視該資料欄在查詢中其他地方的使用情形而定。</span><span class="sxs-lookup"><span data-stu-id="9b69e-120">Individual data columns can appear in either the WHERE or HAVING clause, depending on how they are used elsewhere in the query.</span></span>  
  
-   <span data-ttu-id="9b69e-121">WHERE 子句可用來選取要進行摘要和群組化的資料列子集，因此可在完成群組化前套用之。</span><span class="sxs-lookup"><span data-stu-id="9b69e-121">WHERE clauses are used to select a subset of rows for summarizing and grouping and are thus applied before any grouping is done.</span></span> <span data-ttu-id="9b69e-122">因此，您可以在 WHERE 子句中使用資料欄，即使該資料欄並非 GROUP BY 子句的一部分或者並不在彙總函式中。</span><span class="sxs-lookup"><span data-stu-id="9b69e-122">Therefore, you can use a data column in a WHERE clause even if it is not part of the GROUP BY clause or contained in an aggregate function.</span></span> <span data-ttu-id="9b69e-123">例如，下列陳述式選取價錢超過 $10.00 和平均價格的所有書名：</span><span class="sxs-lookup"><span data-stu-id="9b69e-123">For example, the following statement selects all titles that cost more than $10.00 and averages the price:</span></span>  
  
    ```  
    SELECT AVG(price)  
    FROM titles  
    WHERE price > 10  
    ```  
  
-   <span data-ttu-id="9b69e-124">如果您建立的搜尋條件中使用了 GROUP BY 子句或彙總函式所用的資料行，搜尋條件可 WHERE 子句或 HAVING 子句的形式出現；您可以在建立搜尋條件時決定其中一項。</span><span class="sxs-lookup"><span data-stu-id="9b69e-124">If you create a search condition that involves a column also used in a GROUP BY clause or aggregate function, the search condition can appear as either a WHERE clause or a HAVING clause - you can decide which when you create the condition.</span></span> <span data-ttu-id="9b69e-125">例如，下列陳述式建立針對每個發行者建立書名的平均價格，然後針對發行者顯示平均價格超過 $10.00 的平均價格：</span><span class="sxs-lookup"><span data-stu-id="9b69e-125">For example, the following statement creates an average price for the titles for each publisher, then displays the average for the publishers in which the average price is greater than $10.00:</span></span>  
  
    ```  
    SELECT pub_id, AVG(price)  
    FROM titles  
    GROUP BY pub_id  
    HAVING (AVG(price) > 10)  
    ```  
  
-   <span data-ttu-id="9b69e-126">如果您在搜尋條件中使用彙總函式，搜尋條件將使用到摘要而且必須是 HAVING 子句的一部分。</span><span class="sxs-lookup"><span data-stu-id="9b69e-126">If you use an aggregate function in a search condition, the condition involves a summary and must therefore be part of the HAVING clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b69e-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b69e-127">See Also</span></span>  
 <span data-ttu-id="9b69e-128">[&#40;Visual Database Tools&#41;匯總查詢結果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9b69e-128">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="9b69e-129">排序及分組查詢結果 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="9b69e-129">Sort and Group Query Results &#40;Visual Database Tools&#41;</span></span>](sort-and-group-query-results-visual-database-tools.md)  
  
  
