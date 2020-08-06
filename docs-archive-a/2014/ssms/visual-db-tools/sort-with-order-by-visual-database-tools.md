---
title: 使用 ORDER BY 排序 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- ORDER BY clause [Visual Database Tools]
ms.assetid: 459f5640-8058-4c24-97e7-7bbd6168bc39
author: stevestein
ms.author: sstein
ms.openlocfilehash: 93bdb9ed01c7935c5b9dae543804fca758a9262d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705817"
---
# <a name="sort-with-order-by-visual-database-tools"></a><span data-ttu-id="4fe53-102">使用 ORDER BY 排序 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="4fe53-102">Sort with ORDER BY (Visual Database Tools)</span></span>
  <span data-ttu-id="4fe53-103">您可以使用 ORDER BY 子句，藉此根據傳回資料列中的一或多個資料行，排序查詢結果。</span><span class="sxs-lookup"><span data-stu-id="4fe53-103">You can sort query results by one or more of the columns in the returned rows by using an ORDER BY clause.</span></span> <span data-ttu-id="4fe53-104">您可以在 [準則細節] 窗格中選擇選項，定義 ORDER BY 子句。</span><span class="sxs-lookup"><span data-stu-id="4fe53-104">You can define an ORDER BY clause by choosing options in the Criteria Details pane.</span></span>  
  
### <a name="to-sort-a-query-using-an-order-by-clause"></a><span data-ttu-id="4fe53-105">若要使用 ORDER BY 子句排序查詢</span><span class="sxs-lookup"><span data-stu-id="4fe53-105">To sort a query using an ORDER BY clause</span></span>  
  
1.  <span data-ttu-id="4fe53-106">開啟查詢或建立新查詢。</span><span class="sxs-lookup"><span data-stu-id="4fe53-106">Open a query or create a new one.</span></span>  
  
2.  <span data-ttu-id="4fe53-107">在[準則窗格](visual-database-tools.md)中，針對對應到您要用來排序查詢結果之資料行的資料列，按一下 [排序類型]  。</span><span class="sxs-lookup"><span data-stu-id="4fe53-107">In the [Criteria Pane](visual-database-tools.md), click the **Sort Type** column for the row corresponding to the column that you want to use to sort your query results.</span></span>  
  
3.  <span data-ttu-id="4fe53-108">從下拉式清單選擇 [遞增]  或 [遞減]  。</span><span class="sxs-lookup"><span data-stu-id="4fe53-108">Choose *Ascending* or *Descending* from the drop-down list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4fe53-109">清除資料行的 [排序類型]  項目時，會從 ORDER BY 子句移除該資料行。</span><span class="sxs-lookup"><span data-stu-id="4fe53-109">Clearing the **Sort Type** entry for a column removes that column from the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="4fe53-110">請注意，使用 [準則] 窗格時，查詢的 UNION 子句會變更，以符合您最近的動作。</span><span class="sxs-lookup"><span data-stu-id="4fe53-110">Notice that as you work in the Criteria pane, your query's UNION clause changes to match your most recent actions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4fe53-111">使用多個資料行排序結果時，可使用 [排序次序]  欄位指定資料行相互之間搜尋的順序。</span><span class="sxs-lookup"><span data-stu-id="4fe53-111">When sorting results by more than one column, specify the order in which columns are searched relative to each other by using the **Sort Order** column.</span></span> <span data-ttu-id="4fe53-112">如需詳細資訊，請參閱**如何：對查詢中的多個資料行進行排序**。</span><span class="sxs-lookup"><span data-stu-id="4fe53-112">For more information, see **How to: Sort Multiple Columns in Queries**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fe53-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fe53-113">See Also</span></span>  
 <span data-ttu-id="4fe53-114">[排序和分組查詢結果 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="4fe53-114">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="4fe53-115">[&#40;Visual Database Tools&#41;匯總查詢結果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="4fe53-115">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="4fe53-116">設計查詢和檢視使用說明主題 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="4fe53-116">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
