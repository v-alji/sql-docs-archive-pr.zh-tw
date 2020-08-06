---
title: 摘要查詢結果 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing query results
- queries [SQL Server], results
- aggregate queries [SQL Server]
ms.assetid: c9e15350-ed57-4d95-814d-815fbebfd86b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 08713be2d4439e520df07ec5efd6cb761a78a994
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704621"
---
# <a name="summarize-query-results-visual-database-tools"></a><span data-ttu-id="80975-102">摘要查詢結果 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="80975-102">Summarize Query Results (Visual Database Tools)</span></span>
  <span data-ttu-id="80975-103">當您建立彙總查詢時，可以套用某些邏輯原則。</span><span class="sxs-lookup"><span data-stu-id="80975-103">When you create aggregate queries, certain logical principles apply.</span></span> <span data-ttu-id="80975-104">例如，您無法顯示摘要查詢中的個別資料列內容。</span><span class="sxs-lookup"><span data-stu-id="80975-104">For example, you cannot display the contents of individual rows in a summary query.</span></span> <span data-ttu-id="80975-105">查詢和檢視設計工具可協助您依據 [圖表窗格](visual-database-tools.md) 與 [準則窗格](criteria-pane-visual-database-tools.md) 的運作模式來符合這些原則。</span><span class="sxs-lookup"><span data-stu-id="80975-105">The Query and View Designer helps you comply with these principles in the way the [Diagram pane](visual-database-tools.md) and [Criteria pane](criteria-pane-visual-database-tools.md) behave.</span></span>  
  
 <span data-ttu-id="80975-106">暸解彙總查詢和查詢和檢視設計工具的作業方式後，您就可以用邏輯方式來建立正確的彙總查詢。</span><span class="sxs-lookup"><span data-stu-id="80975-106">By understanding the principles of aggregate queries and the Query and View Designer's behavior, you can create logically correct aggregate queries.</span></span> <span data-ttu-id="80975-107">使用彙總查詢的最重要的原則就是只能產生摘要資訊。</span><span class="sxs-lookup"><span data-stu-id="80975-107">The overriding principle is that aggregate queries can result only in summary information.</span></span> <span data-ttu-id="80975-108">因此，其他的原則即說明可用來參考彙總查詢個別資料欄的其他方法。</span><span class="sxs-lookup"><span data-stu-id="80975-108">Thus, most of the principles that follow describe the ways that you can reference individual data columns within an aggregate query.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="80975-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="80975-109">In This Section</span></span>  
 [<span data-ttu-id="80975-110">在彙總查詢中使用資料行 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="80975-110">Work with Columns in Aggregate Queries &#40;Visual Database Tools&#41;</span></span>](work-with-columns-in-aggregate-queries-visual-database-tools.md)  
 <span data-ttu-id="80975-111">說明使用 GROUP BY、WHERE 和 HAVING 子句分組與摘要的概念。</span><span class="sxs-lookup"><span data-stu-id="80975-111">Describes concepts about grouping and summarizing columns with the GROUP BY, WHERE, and HAVING clauses.</span></span>  
  
 [<span data-ttu-id="80975-112">計算資料表中的資料列 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="80975-112">Count Rows in a Table &#40;Visual Database Tools&#41;</span></span>](count-rows-in-a-table-visual-database-tools.md)  
 <span data-ttu-id="80975-113">提供計算資料表中之資料列數目，或資料表中符合一組準則之資料列數目的步驟。</span><span class="sxs-lookup"><span data-stu-id="80975-113">Provides steps for counting the number of rows in a table or the number of rows in a table that meet a set of criteria.</span></span>  
  
 [<span data-ttu-id="80975-114">摘要或彙總資料表中所有資料列的值 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="80975-114">Summarize or Aggregate Values for All Rows in a Table &#40;Visual Database Tools&#41;</span></span>](summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools.md)  
 <span data-ttu-id="80975-115">提供摘要所有資料列而不是一組群組資料列的步驟。</span><span class="sxs-lookup"><span data-stu-id="80975-115">Provides steps for summarizing all rows rather than for a set of grouped rows.</span></span>  
  
 [<span data-ttu-id="80975-116">使用自訂運算式摘要或彙總值 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="80975-116">Summarize or Aggregate Values Using Custom Expressions &#40;Visual Database Tools&#41;</span></span>](summarize-or-aggregate-values-using-custom-expressions-visual-database-tools.md)  
 <span data-ttu-id="80975-117">提供使用運算式，而不是使用預先定義子句執行摘要或彙總的步驟。</span><span class="sxs-lookup"><span data-stu-id="80975-117">Provides steps for using expressions to summarize or aggregate rather than using the predefined clauses.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="80975-118">相關章節</span><span class="sxs-lookup"><span data-stu-id="80975-118">Related Sections</span></span>  
 [<span data-ttu-id="80975-119">設計查詢和檢視使用說明主題 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="80975-119">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
 <span data-ttu-id="80975-120">提供主題連結，內容包含如何使用查詢和檢視設計師。</span><span class="sxs-lookup"><span data-stu-id="80975-120">Provides links to topics covering how to use the Query and View Designer.</span></span>  
  
  
