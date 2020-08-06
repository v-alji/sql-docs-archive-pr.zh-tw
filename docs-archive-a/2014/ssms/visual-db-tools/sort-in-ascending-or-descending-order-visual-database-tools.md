---
title: 以遞增或遞減順序排序 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- descending sorts
- ascending sorts
ms.assetid: d61cc55b-9ee8-4ecf-a32f-6459ae43910b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 67b5e6b00f62cfc297cc5930bc8cf3a41314a2f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605984"
---
# <a name="sort-in-ascending-or-descending-order-visual-database-tools"></a><span data-ttu-id="ab218-102">以遞增或遞減順序排序 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ab218-102">Sort in Ascending or Descending Order (Visual Database Tools)</span></span>
  <span data-ttu-id="ab218-103">您可以使用 `ASC` 或 `DESC` 關鍵字搭配 `ORDER BY` 子句，針對結果集中一個或多個資料行，將查詢結果按照遞增或遞減排序。</span><span class="sxs-lookup"><span data-stu-id="ab218-103">You can sort query results in ascending or descending order on one or more of the columns in the result set by using the `ASC` or `DESC` keywords with the `ORDER BY` clause.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab218-104">排序次序一部份取決於資料行的定序序列。</span><span class="sxs-lookup"><span data-stu-id="ab218-104">The sort order is determined in part by the column's collation sequence.</span></span> <span data-ttu-id="ab218-105">您可以在 [定序對話方塊](visual-database-tools.md)中變更定序序列。</span><span class="sxs-lookup"><span data-stu-id="ab218-105">You can change the collation sequence in the [Collation Dialog Box](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="ab218-106">以下程序假設您已經在查詢和檢視設計工具中使用 ORDER BY 子句排序一個或多個資料行開啟查詢。</span><span class="sxs-lookup"><span data-stu-id="ab218-106">The following procedure assumes that you have a query open in Query and View Designer that uses the ORDER BY clause to sort one or more columns.</span></span>  
  
### <a name="to-specify-or-change-the-order-in-which-results-are-sorted"></a><span data-ttu-id="ab218-107">指定或變更已經排序結果的順序</span><span class="sxs-lookup"><span data-stu-id="ab218-107">To specify or change the order in which results are sorted</span></span>  
  
1.  <span data-ttu-id="ab218-108">在 [準則窗格](criteria-pane-visual-database-tools.md) 中，對要重新排序的資料行按一下 [排序類型]  欄位。</span><span class="sxs-lookup"><span data-stu-id="ab218-108">In the [Criteria pane](criteria-pane-visual-database-tools.md), click the **Sort Type** field for the column that you want to reorder.</span></span>  
  
2.  <span data-ttu-id="ab218-109">選擇 [遞增]  或 [遞減]  以指定資料行的排序順序。</span><span class="sxs-lookup"><span data-stu-id="ab218-109">Choose **Ascending** or **Descending** to specify the sort order for the column.</span></span>  
  
 <span data-ttu-id="ab218-110">請注意，使用 [準則] 窗格時，查詢的 UNION 子句會變更，以符合您最近的動作。</span><span class="sxs-lookup"><span data-stu-id="ab218-110">Notice that as you work in the Criteria pane, your query's UNION clause changes to match your most recent actions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab218-111">使用多個資料行排序結果時，可使用 [排序次序] 欄位指定資料行相互之間搜尋的順序。</span><span class="sxs-lookup"><span data-stu-id="ab218-111">When sorting results by more than one column, specify the order in which columns are searched relative to each other by using the Sort Order column.</span></span> <span data-ttu-id="ab218-112">如需詳細資訊，請參閱[排序查詢中的多個資料行 &#40;Visual Database Tools&#41;](sort-multiple-columns-in-queries-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="ab218-112">For more information, see [Sort Multiple Columns in Queries &#40;Visual Database Tools&#41;](sort-multiple-columns-in-queries-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab218-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab218-113">See Also</span></span>  
 <span data-ttu-id="ab218-114">[排序和分組查詢結果 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ab218-114">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="ab218-115">[&#40;Visual Database Tools&#41;匯總查詢結果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ab218-115">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="ab218-116">設計查詢和檢視使用說明主題 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="ab218-116">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
