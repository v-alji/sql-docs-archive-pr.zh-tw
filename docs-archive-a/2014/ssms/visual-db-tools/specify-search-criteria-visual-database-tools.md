---
title: 指定搜尋準則 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Query Designer [SQL Server], Criteria pane
- queries [Visual Database Tools]
- criteria for search conditions
- search conditions [SQL Server], search criteria
- View Designer, Criteria pane
- row return limitations [SQL Server]
- Criteria pane
- restricting rows returned
- search criteria [SQL Server]
- Visual Database Tools [SQL Server], queries
- limiting rows returned
ms.assetid: 25fb4e31-6dbf-4cf6-8e47-0dd0998c836c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 258aceb348ed3bcd7d4d19201a0169b53b54d711
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595352"
---
# <a name="specify-search-criteria-visual-database-tools"></a><span data-ttu-id="236f4-102">指定搜尋準則 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="236f4-102">Specify Search Criteria (Visual Database Tools)</span></span>
  <span data-ttu-id="236f4-103">您可以使用搜尋準則來限制查詢所傳回的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="236f4-103">You can use search criteria to restrict the number of rows returned by a query.</span></span>  
  
 <span data-ttu-id="236f4-104">如需建立搜尋準則的特殊步驟的詳細資訊，請參閱下表所列的主題。</span><span class="sxs-lookup"><span data-stu-id="236f4-104">For details about the particular steps to creating search criteria, refer to the topics listed in the following table.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="236f4-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="236f4-105">In This Section</span></span>  
 [<span data-ttu-id="236f4-106">輸入搜尋值的規則 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="236f4-106">Rules for Entering Search Values &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
 <span data-ttu-id="236f4-107">說明如何輸入文字、數字、日期或邏輯值。</span><span class="sxs-lookup"><span data-stu-id="236f4-107">Explains how to enter text, numbers, dates, or logical values.</span></span>  
  
 [<span data-ttu-id="236f4-108">在條件窗格中合併搜尋條件的慣例 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="236f4-108">Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;</span></span>](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md)  
 <span data-ttu-id="236f4-109">說明使用 AND 和 OR 運算子的概念。</span><span class="sxs-lookup"><span data-stu-id="236f4-109">Explains the concepts behind using the AND and OR operators.</span></span>  
  
 [<span data-ttu-id="236f4-110">指定搜尋條件 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="236f4-110">Specify Search Conditions &#40;Visual Database Tools&#41;</span></span>](specify-search-conditions-visual-database-tools.md)  
 <span data-ttu-id="236f4-111">說明選擇搜尋準則以取得所要資料的基本概念。</span><span class="sxs-lookup"><span data-stu-id="236f4-111">Explains the basics of choosing search criteria to get just the data you want.</span></span>  
  
 [<span data-ttu-id="236f4-112">指定單一資料行的多重搜尋條件 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="236f4-112">Specify Multiple Search Conditions for One Column &#40;Visual Database Tools&#41;</span></span>](specify-multiple-search-conditions-for-one-column-visual-database-tools.md)  
 <span data-ttu-id="236f4-113">說明如何在同一資料行中建立多重搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="236f4-113">Explains how to create multiple search conditions to the same data column.</span></span>  
  
 [<span data-ttu-id="236f4-114">指定多重資料行的多重搜尋條件 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="236f4-114">Specify Multiple Search Conditions for Multiple Columns &#40;Visual Database Tools&#41;</span></span>](specify-multiple-search-conditions-for-multiple-columns-visual-database-tools.md)  
 <span data-ttu-id="236f4-115">說明如何在查詢搜尋條件中包含數個資料行。</span><span class="sxs-lookup"><span data-stu-id="236f4-115">Explains how to include several data columns as part of the search condition for a query.</span></span>  
  
 [<span data-ttu-id="236f4-116">在查詢中指定 TOP 子句 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="236f4-116">Specify the TOP Clause in Queries &#40;Visual Database Tools&#41;</span></span>](specify-the-top-clause-in-queries-visual-database-tools.md)  
 <span data-ttu-id="236f4-117">說明如何只傳回特定數目或百分比的資料列。</span><span class="sxs-lookup"><span data-stu-id="236f4-117">Explains how to have only a given number or percentage of rows returned.</span></span>  
  
 [<span data-ttu-id="236f4-118">在相同查詢中使用 HAVING 和 WHERE 子句 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="236f4-118">Use HAVING and WHERE Clauses in the Same Query &#40;Visual Database Tools&#41;</span></span>](use-having-and-where-clauses-in-the-same-query-visual-database-tools.md)  
 <span data-ttu-id="236f4-119">說明在查詢中同時使用這些子句的方法及原因。</span><span class="sxs-lookup"><span data-stu-id="236f4-119">Explains how and why to use both of these clauses in a query.</span></span>  
  
 [<span data-ttu-id="236f4-120">選取不符合某值的資料列 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="236f4-120">Select Rows That Do Not Match a Value &#40;Visual Database Tools&#41;</span></span>](select-rows-that-do-not-match-a-value-visual-database-tools.md)  
 <span data-ttu-id="236f4-121">說明如何在特定資料行的數值未符合您在查詢陳述式中所提供的數值時，傳回所有的資料列。</span><span class="sxs-lookup"><span data-stu-id="236f4-121">Explains how to return all rows where the value of a give column does not match the value you provide in the query statement.</span></span>  
  
 [<span data-ttu-id="236f4-122">包含或排除資料列 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="236f4-122">Include or Exclude Rows &#40;Visual Database Tools&#41;</span></span>](include-or-exclude-rows-visual-database-tools.md)  
 <span data-ttu-id="236f4-123">說明在查詢中所使用之子句和運算子的基本概念。</span><span class="sxs-lookup"><span data-stu-id="236f4-123">Explains the concepts behind clauses and operators used in queries.</span></span>  
  
 [<span data-ttu-id="236f4-124">排除重複的資料列 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="236f4-124">Exclude Duplicate Rows &#40;Visual Database Tools&#41;</span></span>](exclude-duplicate-rows-visual-database-tools.md)  
 <span data-ttu-id="236f4-125">說明如何利用選取查詢來篩選重複的資料列。</span><span class="sxs-lookup"><span data-stu-id="236f4-125">Explains how to filter duplicate rows out of Select queries.</span></span>  
  
 [<span data-ttu-id="236f4-126">在 AND 具有優先權時結合條件 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="236f4-126">Combine Conditions When AND Has Precedence &#40;Visual Database Tools&#41;</span></span>](combine-conditions-when-and-has-precedence-visual-database-tools.md)  
 <span data-ttu-id="236f4-127">說明使用 AND 運算子來篩選查詢結果的原因及方法。</span><span class="sxs-lookup"><span data-stu-id="236f4-127">Explains why and how to use the AND operator to filter query results.</span></span>  
  
 [<span data-ttu-id="236f4-128">在 OR 具有優先權時結合條件 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="236f4-128">Combine Conditions When OR Has Precedence &#40;Visual Database Tools&#41;</span></span>](combine-conditions-when-or-has-precedence-visual-database-tools.md)  
 <span data-ttu-id="236f4-129">說明使用 OR 運算子來篩選查詢結果的原因及方法。</span><span class="sxs-lookup"><span data-stu-id="236f4-129">Explains why and how to use the OR operator to filter query results.</span></span>  
  
 [<span data-ttu-id="236f4-130">建立子查詢 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="236f4-130">Create Subqueries &#40;Visual Database Tools&#41;</span></span>](create-subqueries-visual-database-tools.md)  
 <span data-ttu-id="236f4-131">說明如何建立子查詢或巢狀查詢。</span><span class="sxs-lookup"><span data-stu-id="236f4-131">Explains how to create subqueries, or nested queries.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="236f4-132">相關章節</span><span class="sxs-lookup"><span data-stu-id="236f4-132">Related Sections</span></span>  
 [<span data-ttu-id="236f4-133">使用查詢執行基本作業 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="236f4-133">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
 <span data-ttu-id="236f4-134">提供最常見查詢工作之主題及步驟的連結。</span><span class="sxs-lookup"><span data-stu-id="236f4-134">Provides links to topics with steps for the most common querying tasks.</span></span>  
  
 [<span data-ttu-id="236f4-135">查詢的類型 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="236f4-135">Types of Queries &#40;Visual Database Tools&#41;</span></span>](types-of-queries-visual-database-tools.md)  
 <span data-ttu-id="236f4-136">提供可說明所支援查詢類型之主題的連結。</span><span class="sxs-lookup"><span data-stu-id="236f4-136">Provides links to topics explaining the supported query types.</span></span>  
  
 [<span data-ttu-id="236f4-137">排序及分組查詢結果 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="236f4-137">Sort and Group Query Results &#40;Visual Database Tools&#41;</span></span>](sort-and-group-query-results-visual-database-tools.md)  
 <span data-ttu-id="236f4-138">提供排序和分組查詢結果之主題及步驟的連結。</span><span class="sxs-lookup"><span data-stu-id="236f4-138">Provides links to topics with steps for sorting and grouping the results of a query.</span></span>  
  
 [<span data-ttu-id="236f4-139">摘要查詢結果 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="236f4-139">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
 <span data-ttu-id="236f4-140">提供彙總包含 NULL 和非數值資料列結果之主題及步驟的連結。</span><span class="sxs-lookup"><span data-stu-id="236f4-140">Provides links to topics with steps for summarizing results, including NULL and Nonnumeric columns.</span></span>  
  
 [<span data-ttu-id="236f4-141">設計查詢和檢視使用說明主題 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="236f4-141">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
 <span data-ttu-id="236f4-142">提供使用 [查詢和檢視表設計工具] 進行查詢及檢視時可執行工作之主題及章節的連結。</span><span class="sxs-lookup"><span data-stu-id="236f4-142">Provides links to topics and sections covering work you can do in queries and views using the Query and View Designer.</span></span>  
  
  
