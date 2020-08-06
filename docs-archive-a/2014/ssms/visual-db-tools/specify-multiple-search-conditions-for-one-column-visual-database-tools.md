---
title: 針對一個資料行指定多個搜尋條件 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], multiple conditions
- multiple search conditions
- search conditions [SQL Server], multiple
- OR operator
- AND, Criteria pane
ms.assetid: 2c006e36-56b1-4992-89b4-c6c0b19808f3
author: stevestein
ms.author: sstein
ms.openlocfilehash: a07322120bd3b3f543e6f54fa50cdf75aa32be59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595355"
---
# <a name="specify-multiple-search-conditions-for-one-column-visual-database-tools"></a><span data-ttu-id="8912b-102">指定單一資料行的多重搜尋條件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8912b-102">Specify Multiple Search Conditions for One Column (Visual Database Tools)</span></span>
  <span data-ttu-id="8912b-103">在一些執行個體中，可能要套用許多搜尋條件至相同的資料行。</span><span class="sxs-lookup"><span data-stu-id="8912b-103">In some instances, you might want to apply a number of search conditions to the same data column.</span></span> <span data-ttu-id="8912b-104">例如，您可能要：</span><span class="sxs-lookup"><span data-stu-id="8912b-104">For example, you might want to:</span></span>  
  
-   <span data-ttu-id="8912b-105">搜尋 `employee` 資料表中幾個不同的名稱，或在不同薪資範圍的員工。</span><span class="sxs-lookup"><span data-stu-id="8912b-105">Search for several different names in an `employee` table or for employees who are in different salary ranges.</span></span> <span data-ttu-id="8912b-106">這種搜尋需要 OR 條件。</span><span class="sxs-lookup"><span data-stu-id="8912b-106">This type of search requires an OR condition.</span></span>  
  
-   <span data-ttu-id="8912b-107">搜尋以文字 "The" 為開頭並包含文字 "Cook" 的書名。</span><span class="sxs-lookup"><span data-stu-id="8912b-107">Search for a book title that both starts with the word "The" and contains the word "Cook."</span></span> <span data-ttu-id="8912b-108">這種搜尋需要 AND 條件。</span><span class="sxs-lookup"><span data-stu-id="8912b-108">This type of search requires an AND condition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8912b-109">此主題的資訊適用於查詢的 WHERE 和 HAVING 子句中的搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="8912b-109">The information in this topic applies to search conditions in both the WHERE and HAVING clauses of a query.</span></span> <span data-ttu-id="8912b-110">本範例集中在建立 WHERE 子句，但上述原則仍可套用至兩種搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="8912b-110">The examples focus on creating WHERE clauses, but the principles apply to both types of search conditions.</span></span>  
  
 <span data-ttu-id="8912b-111">若要搜尋同一資料行的其他值，可以指定 OR 條件。</span><span class="sxs-lookup"><span data-stu-id="8912b-111">To search for alternative values in the same data column, you specify an OR condition.</span></span> <span data-ttu-id="8912b-112">若要搜尋符合幾個條件的值，可以指定 AND 條件。</span><span class="sxs-lookup"><span data-stu-id="8912b-112">To search for values that meet several conditions, you specify an AND condition.</span></span>  
  
## <a name="specifying-an-or-condition"></a><span data-ttu-id="8912b-113">指定 OR 條件</span><span class="sxs-lookup"><span data-stu-id="8912b-113">Specifying an OR Condition</span></span>  
 <span data-ttu-id="8912b-114">使用 OR 條件可讓您指定搜尋資料行中的幾個其他值。</span><span class="sxs-lookup"><span data-stu-id="8912b-114">Using an OR condition enables you to specify several alternative values to search for in a column.</span></span> <span data-ttu-id="8912b-115">這一選項會擴展搜尋的範圍，並可傳回比搜尋單一值還多的資料列。</span><span class="sxs-lookup"><span data-stu-id="8912b-115">This option expands the scope of the search and can return more rows than searching for a single value.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="8912b-116">您可以經常改用 IN 運算子來搜尋同一資料行中的多重值。</span><span class="sxs-lookup"><span data-stu-id="8912b-116">You can often use the IN operator instead to search for multiple values in the same data column.</span></span>  
  
#### <a name="to-specify-an-or-condition"></a><span data-ttu-id="8912b-117">若要指定 OR 條件</span><span class="sxs-lookup"><span data-stu-id="8912b-117">To specify an OR condition</span></span>  
  
1.  <span data-ttu-id="8912b-118">在[準則窗格](visual-database-tools.md)中，新增要搜尋的資料行。</span><span class="sxs-lookup"><span data-stu-id="8912b-118">In the [Criteria Pane](visual-database-tools.md), add the column to search.</span></span>  
  
2.  <span data-ttu-id="8912b-119">在剛新增的資料行的 [篩選條件]  資料行中，指定第一個條件。</span><span class="sxs-lookup"><span data-stu-id="8912b-119">In the **Filter** column for the data column you just added, specify the first condition.</span></span>  
  
3.  <span data-ttu-id="8912b-120">在相同資料行的 [**或...** ] 資料行中，指定第二個條件。</span><span class="sxs-lookup"><span data-stu-id="8912b-120">In the **Or...** column for the same data column, specify the second condition.</span></span>  
  
 <span data-ttu-id="8912b-121">[查詢和檢視表設計工具] 會建立包含 OR 條件的 WHERE 子句，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8912b-121">The Query and View Designer creates a WHERE clause that contains an OR condition such as the following:</span></span>  
  
```  
SELECT fname, lname  
FROM employees  
WHERE (salary < 30000) OR (salary > 100000)  
```  
  
## <a name="specifying-an-and-condition"></a><span data-ttu-id="8912b-122">指定 AND 條件</span><span class="sxs-lookup"><span data-stu-id="8912b-122">Specifying an AND Condition</span></span>  
 <span data-ttu-id="8912b-123">使用 AND 條件可讓指定資料行中的值必須符合包含在結果集中資料列兩個 (或更多) 的條件。</span><span class="sxs-lookup"><span data-stu-id="8912b-123">Using an AND condition enables you to specify that values in a column must meet two (or more) conditions for the row to be included in the result set.</span></span> <span data-ttu-id="8912b-124">這一選項會縮小搜尋的範圍，通常傳回的資料列比搜尋單一值還少。</span><span class="sxs-lookup"><span data-stu-id="8912b-124">This option narrows the scope of the search and usually returns fewer rows than searching for a single value.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="8912b-125">如果您在搜尋某範圍的值，可改用 BETWEEN 運算子以 AND 連結兩個條件。</span><span class="sxs-lookup"><span data-stu-id="8912b-125">If you are searching for a range of values, you can use the BETWEEN operator instead of linking two conditions with AND.</span></span>  
  
#### <a name="to-specify-an-and-condition"></a><span data-ttu-id="8912b-126">若要指定 AND 條件</span><span class="sxs-lookup"><span data-stu-id="8912b-126">To specify an AND condition</span></span>  
  
1.  <span data-ttu-id="8912b-127">在 [準則] 窗格中，加入要搜尋的資料行。</span><span class="sxs-lookup"><span data-stu-id="8912b-127">In the Criteria pane, add the column to search.</span></span>  
  
2.  <span data-ttu-id="8912b-128">在剛新增的資料行的 [篩選條件]  資料行中，指定第一個條件。</span><span class="sxs-lookup"><span data-stu-id="8912b-128">In the **Filter** column for the data column you just added, specify the first condition.</span></span>  
  
3.  <span data-ttu-id="8912b-129">再將相同的資料行加入 [準則] 窗格，將它放在方格的空資料列中。</span><span class="sxs-lookup"><span data-stu-id="8912b-129">Add the same data column to the Criteria pane again, placing it in an empty row of the grid.</span></span>  
  
4.  <span data-ttu-id="8912b-130">在資料行的第二個執行個體的 [篩選條件]  欄位中，指定第二個條件。</span><span class="sxs-lookup"><span data-stu-id="8912b-130">In the **Filter** column for the second instance of the data column, specify the second condition.</span></span>  
  
 <span data-ttu-id="8912b-131">查詢設計工具會建立 WHERE 子句，其中包含 AND 條件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8912b-131">The Query Designer creates a WHERE clause that contains an AND condition such as the following:</span></span>  
  
```  
SELECT title_id, title  
FROM titles  
WHERE (title LIKE '%Cook%') AND   
  (title LIKE '%Recipe%')  
```  
  
## <a name="see-also"></a><span data-ttu-id="8912b-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8912b-132">See Also</span></span>  
 <span data-ttu-id="8912b-133">[在 [準則] 窗格中合併搜尋條件的慣例 &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span><span class="sxs-lookup"><span data-stu-id="8912b-133">[Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span></span>  
 [<span data-ttu-id="8912b-134">指定搜尋準則 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="8912b-134">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
