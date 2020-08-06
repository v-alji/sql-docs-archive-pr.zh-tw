---
title: 使用自訂表格達式摘要或匯總值 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing query results
- custom expressions to aggregate values [SQL Server]
ms.assetid: 34130ac1-0106-4766-b324-acb0b7bb6f6e
author: stevestein
ms.author: sstein
ms.openlocfilehash: b9f03f82842178a68c8a3d04ebc1bd738c0ab0b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704622"
---
# <a name="summarize-or-aggregate-values-using-custom-expressions-visual-database-tools"></a><span data-ttu-id="1adf7-102">使用自訂運算式摘要或彙總值 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="1adf7-102">Summarize or Aggregate Values Using Custom Expressions (Visual Database Tools)</span></span>
  <span data-ttu-id="1adf7-103">除了使用彙總函式彙總資料以外，您也可以建立自訂運算式產生彙總值。</span><span class="sxs-lookup"><span data-stu-id="1adf7-103">In addition to using aggregate functions to aggregate data, you can create custom expressions to produce aggregate values.</span></span> <span data-ttu-id="1adf7-104">您可以使用自訂運算式取代彙總查詢中任何位置的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="1adf7-104">You can use custom expressions in place of aggregate functions anywhere in an aggregate query.</span></span>  
  
 <span data-ttu-id="1adf7-105">例如，在 `titles` 資料表中，您可能想要建立查詢，以同時顯示平均價格與折扣後的平均價格。</span><span class="sxs-lookup"><span data-stu-id="1adf7-105">For example, in the `titles` table you might want to create a query that shows not just the average price, but what the average price would be if it were discounted.</span></span>  
  
 <span data-ttu-id="1adf7-106">不可包含只計算資料表中個別資料列的運算式；運算式必須以彙總值做為基礎，因為在計算運算式時只有彙總值可以使用。</span><span class="sxs-lookup"><span data-stu-id="1adf7-106">You cannot include an expression that is based on calculations involving only individual rows in the table; the expression must be based on an aggregate value, because only the aggregate values are available at the time the expression is calculated.</span></span>  
  
### <a name="to-specify-a-custom-expression-for-a-summary-value"></a><span data-ttu-id="1adf7-107">若要指定摘要值的自訂運算式</span><span class="sxs-lookup"><span data-stu-id="1adf7-107">To specify a custom expression for a summary value</span></span>  
  
1.  <span data-ttu-id="1adf7-108">為您的查詢指定群組。</span><span class="sxs-lookup"><span data-stu-id="1adf7-108">Specify the groups for your query.</span></span> <span data-ttu-id="1adf7-109">如需詳細資訊，請參閱[群組查詢結果中的資料列 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="1adf7-109">For details, see [Group Rows in Query Results &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
2.  <span data-ttu-id="1adf7-110">移至 [準則] 窗格的空白資料列，然後在 [資料行]  資料行輸入運算式。</span><span class="sxs-lookup"><span data-stu-id="1adf7-110">Move to a blank row of the Criteria pane, and then type the expression in the **Columns** column.</span></span>  
  
     <span data-ttu-id="1adf7-111">[查詢和檢視表設計工具](query-and-view-designer-tools-visual-database-tools.md)會自動指派資料行別名給運算式，以便在查詢輸出中建立有用的資料行標題。</span><span class="sxs-lookup"><span data-stu-id="1adf7-111">The [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) automatically assigns a column alias to the expression to create a useful column heading in query output.</span></span> <span data-ttu-id="1adf7-112">如需詳細資訊，請參閱[建立資料行別名 &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="1adf7-112">For more details, see [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
3.  <span data-ttu-id="1adf7-113">在運算式的 [群組依據]  資料行中，選取 [Expression]  。</span><span class="sxs-lookup"><span data-stu-id="1adf7-113">In the **Group By** column for the expression, select **Expression**.</span></span>  
  
4.  <span data-ttu-id="1adf7-114">執行查詢。</span><span class="sxs-lookup"><span data-stu-id="1adf7-114">Run the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1adf7-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1adf7-115">See Also</span></span>  
 <span data-ttu-id="1adf7-116">[排序和分組查詢結果 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="1adf7-116">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="1adf7-117">摘要查詢結果 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="1adf7-117">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
  
  
