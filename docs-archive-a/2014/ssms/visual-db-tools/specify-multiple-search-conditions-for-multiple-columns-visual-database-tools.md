---
title: 為多個資料行指定多個搜尋條件 (Visual Database Tools) |Microsoft Docs
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
ms.assetid: 06617729-0d0b-4da2-9890-b7e2f5cdbc7b
author: stevestein
ms.author: sstein
ms.openlocfilehash: ccf08a98d39d4ab808b7c2df794164b341be363a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593740"
---
# <a name="specify-multiple-search-conditions-for-multiple-columns-visual-database-tools"></a><span data-ttu-id="02962-102">指定多重資料行的多重搜尋條件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="02962-102">Specify Multiple Search Conditions for Multiple Columns (Visual Database Tools)</span></span>
  <span data-ttu-id="02962-103">藉由包含幾個資料行做為搜尋條件的一部分，可以擴展或縮小查詢的範圍。</span><span class="sxs-lookup"><span data-stu-id="02962-103">You can expand or narrow the scope of your query by including several data columns as part of your search condition.</span></span> <span data-ttu-id="02962-104">例如，您可能要：</span><span class="sxs-lookup"><span data-stu-id="02962-104">For example, you might want to:</span></span>  
  
-   <span data-ttu-id="02962-105">搜尋在公司工作超過五年或維持特定工作的員工。</span><span class="sxs-lookup"><span data-stu-id="02962-105">Search for employees who either have worked more than five years at the company or who hold certain jobs.</span></span>  
  
-   <span data-ttu-id="02962-106">搜尋由特定發行者所發行有關烹飪的書籍。</span><span class="sxs-lookup"><span data-stu-id="02962-106">Search for a book that is both published by a specific publisher and pertains to cooking.</span></span>  
  
 <span data-ttu-id="02962-107">若要建立搜尋兩個 (或多個) 資料行中值的查詢，可以指定 OR 條件。</span><span class="sxs-lookup"><span data-stu-id="02962-107">To create a query that searches for values in either of two (or more) columns, you specify an OR condition.</span></span> <span data-ttu-id="02962-108">若要建立必須符合兩個 (或多個) 資料行中所有條件的查詢，可以指定 AND 條件。</span><span class="sxs-lookup"><span data-stu-id="02962-108">To create a query that must meet all conditions in two (or more) columns, you specify an AND condition.</span></span>  
  
## <a name="specifying-an-or-condition"></a><span data-ttu-id="02962-109">指定 OR 條件</span><span class="sxs-lookup"><span data-stu-id="02962-109">Specifying an OR Condition</span></span>  
 <span data-ttu-id="02962-110">若要建立使用 OR 連結的多重條件，請將個別條件放在 [準則] 窗格中的不同資料行。</span><span class="sxs-lookup"><span data-stu-id="02962-110">To create multiple conditions linked with OR, you put each separate condition in a different column of the Criteria pane.</span></span>  
  
#### <a name="to-specify-an-or-condition-for-two-different-columns"></a><span data-ttu-id="02962-111">若要指定兩個不同資料行的 OR 條件</span><span class="sxs-lookup"><span data-stu-id="02962-111">To specify an OR condition for two different columns</span></span>  
  
1.  <span data-ttu-id="02962-112">在 [準則窗格](visual-database-tools.md)中，新增想要搜尋的資料行。</span><span class="sxs-lookup"><span data-stu-id="02962-112">In the [Criteria Pane](visual-database-tools.md), add the columns you want to search.</span></span>  
  
2.  <span data-ttu-id="02962-113">在想要搜尋的第一個資料行的 [篩選條件]  資料行中，指定第一個條件。</span><span class="sxs-lookup"><span data-stu-id="02962-113">In the **Filter** column for the first column to search, specify the first condition.</span></span>  
  
3.  <span data-ttu-id="02962-114">在要搜尋的第二個資料行之 [或...]  資料行中，指定第二個條件，請將 [篩選條件]  資料行保留空白。</span><span class="sxs-lookup"><span data-stu-id="02962-114">In the **Or...** column for the second data column to search, specify the second condition, leaving the **Filter** column blank.</span></span>  
  
     <span data-ttu-id="02962-115">[查詢和檢視表設計工具] 會建立包含 OR 條件的 WHERE 子句，如下所示：</span><span class="sxs-lookup"><span data-stu-id="02962-115">The Query and View Designer creates a WHERE clause that contains an OR condition such as the following:</span></span>  
  
    ```  
    SELECT job_lvl, hire_date  
    FROM employee  
    WHERE (job_lvl >= 200) OR   
      (hire_date < '01/01/1998')  
    ```  
  
4.  <span data-ttu-id="02962-116">對想要加入的每個額外條件重複步驟 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="02962-116">Repeat Steps 2 and 3 for each additional condition you want to add.</span></span> <span data-ttu-id="02962-117">為每個新增的條件使用不同的 [或...]  資料行。</span><span class="sxs-lookup"><span data-stu-id="02962-117">Use a different **Or...** column for each new condition.</span></span>  
  
## <a name="specifying-an-and-condition"></a><span data-ttu-id="02962-118">指定 AND 條件</span><span class="sxs-lookup"><span data-stu-id="02962-118">Specifying an AND Condition</span></span>  
 <span data-ttu-id="02962-119">若要搜尋使用 AND 連結條件的不同資料行，請將所有條件放入方格的 [篩選條件]  資料行。</span><span class="sxs-lookup"><span data-stu-id="02962-119">To search different data columns using conditions linked with AND, you put all the conditions in the **Filter** column of the grid.</span></span>  
  
#### <a name="to-specify-an-and-condition-for-two-different-columns"></a><span data-ttu-id="02962-120">若要指定兩個不同資料行的 AND 條件</span><span class="sxs-lookup"><span data-stu-id="02962-120">To specify an AND condition for two different columns</span></span>  
  
1.  <span data-ttu-id="02962-121">在 [準則窗格](visual-database-tools.md)中，新增想要搜尋的資料行。</span><span class="sxs-lookup"><span data-stu-id="02962-121">In the [Criteria Pane](visual-database-tools.md), add the columns you want to search.</span></span>  
  
2.  <span data-ttu-id="02962-122">在想要搜尋的第一個資料行的 [篩選條件]  資料行中，指定第一個條件。</span><span class="sxs-lookup"><span data-stu-id="02962-122">In the **Filter** column for the first data column to search, specify the first condition.</span></span>  
  
3.  <span data-ttu-id="02962-123">在第二個資料行的 [篩選條件]  資料行中，指定第二個條件。</span><span class="sxs-lookup"><span data-stu-id="02962-123">In the **Filter** column for the second data column, specify the second condition.</span></span>  
  
     <span data-ttu-id="02962-124">查詢與檢視設計工具會建立 WHERE 子句，其中包含 AND 條件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="02962-124">The Query and View Designer creates a WHERE clause that contains an AND condition such as the following:</span></span>  
  
    ```  
    SELECT pub_id, title  
    FROM titles  
    WHERE (pub_id = '0877') AND (title LIKE '%Cook%')  
    ```  
  
4.  <span data-ttu-id="02962-125">對想要加入的每個額外條件重複步驟 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="02962-125">Repeat Steps 2 and 3 for each additional condition you want to add.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02962-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02962-126">See Also</span></span>  
 <span data-ttu-id="02962-127">[當和具有優先順序 &#40;Visual Database Tools&#41;時合併條件](combine-conditions-when-and-has-precedence-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="02962-127">[Combine Conditions When AND Has Precedence &#40;Visual Database Tools&#41;](combine-conditions-when-and-has-precedence-visual-database-tools.md) </span></span>  
 <span data-ttu-id="02962-128">[當或具有 &#40;Visual Database Tools&#41;的優先順序時合併條件](combine-conditions-when-or-has-precedence-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="02962-128">[Combine Conditions When OR Has Precedence &#40;Visual Database Tools&#41;](combine-conditions-when-or-has-precedence-visual-database-tools.md) </span></span>  
 <span data-ttu-id="02962-129">[在 [準則] 窗格中合併搜尋條件的慣例 &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span><span class="sxs-lookup"><span data-stu-id="02962-129">[Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span></span>  
 [<span data-ttu-id="02962-130">指定搜尋準則 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="02962-130">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
