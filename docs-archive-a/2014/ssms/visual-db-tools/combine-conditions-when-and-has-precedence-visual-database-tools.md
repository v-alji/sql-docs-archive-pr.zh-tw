---
title: 在 AND 具有優先權時結合條件 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], combining
- precedence [SQL Server], Criteria pane
- search criteria [SQL Server], combining conditions
- combining search conditions
- AND, Criteria pane
ms.assetid: 450eb2eb-6ea3-405b-8dd2-1ff926c016e7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 917d5381bc83083ee1fa3c07375945c0908da521
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686710"
---
# <a name="combine-conditions-when-and-has-precedence-visual-database-tools"></a><span data-ttu-id="ca7b1-102">在 AND 具有優先權時結合條件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ca7b1-102">Combine Conditions When AND Has Precedence (Visual Database Tools)</span></span>
  <span data-ttu-id="ca7b1-103">若要使用 AND 結合條件，請將資料行加入至查詢兩次，每一個條件一次。</span><span class="sxs-lookup"><span data-stu-id="ca7b1-103">To combine conditions with AND, you add the column to the query twice--once for each condition.</span></span> <span data-ttu-id="ca7b1-104">若要使用 OR 結合條件，請將第一個條件放入 [篩選條件] 資料行，其他條件則放入 [或...]  資料行。</span><span class="sxs-lookup"><span data-stu-id="ca7b1-104">To combine conditions with OR, you put the first one in the Filter column and additional conditions into an **Or...** column.</span></span>  
  
 <span data-ttu-id="ca7b1-105">例如，假設要尋找公司中已經擔任低階工作超過五年的員工，或不論其雇用日期負責中階工作的員工。</span><span class="sxs-lookup"><span data-stu-id="ca7b1-105">For example, imagine that you want to find either employees who have been with the company for more than five years in lower-level jobs or employees with middle-level jobs regardless of their hire date.</span></span> <span data-ttu-id="ca7b1-106">此一查詢需要三個條件，其中兩個以 AND 連結：</span><span class="sxs-lookup"><span data-stu-id="ca7b1-106">This query requires three conditions, two of them linked with AND:</span></span>  
  
-   <span data-ttu-id="ca7b1-107">雇用日期早於五年前且工作層級為 100 的員工。</span><span class="sxs-lookup"><span data-stu-id="ca7b1-107">Employees with a hire date earlier than five years ago AND with a job level of 100.</span></span>  
  
     <span data-ttu-id="ca7b1-108">-或-</span><span class="sxs-lookup"><span data-stu-id="ca7b1-108">-or-</span></span>  
  
-   <span data-ttu-id="ca7b1-109">工作層級為 200 的員工。</span><span class="sxs-lookup"><span data-stu-id="ca7b1-109">Employees with a job level of 200.</span></span>  
  
### <a name="to-combine-conditions-when-and-has-precedence"></a><span data-ttu-id="ca7b1-110">若要在 AND 具有優先權時結合條件</span><span class="sxs-lookup"><span data-stu-id="ca7b1-110">To combine conditions when AND has precedence</span></span>  
  
1.  <span data-ttu-id="ca7b1-111">在 [準則窗格](visual-database-tools.md)中，新增想要搜尋的資料行。</span><span class="sxs-lookup"><span data-stu-id="ca7b1-111">In the [Criteria pane](visual-database-tools.md), add the data columns you want to search.</span></span> <span data-ttu-id="ca7b1-112">若要搜尋使用由 AND 所連結的兩個或多個條件之相同資料行，就必須針對想要搜尋的每個值，將資料行名稱加入方格中。</span><span class="sxs-lookup"><span data-stu-id="ca7b1-112">If you want to search the same column using two or more conditions linked with AND, you must add the data column name to the grid once for each value you want to search.</span></span>  
  
2.  <span data-ttu-id="ca7b1-113">在 [篩選條件]  資料行，輸入想要使用 AND 連結的所有條件。</span><span class="sxs-lookup"><span data-stu-id="ca7b1-113">In the **Filter** column, enter all the conditions that you want to link with AND.</span></span> <span data-ttu-id="ca7b1-114">例如，若要以 AND 連結搜尋 `hire_date` 和 `job_lvl` 資料行的條件，請在 [篩選條件] 資料行分別輸入值 `< '1/1/91'` 和 `= 100`。</span><span class="sxs-lookup"><span data-stu-id="ca7b1-114">For example, to link conditions with AND that search the `hire_date` and `job_lvl` columns, enter the values `< '1/1/91'` and `= 100`, respectively, in the Filter column.</span></span>  
  
     <span data-ttu-id="ca7b1-115">這些方格項目會在 [SQL 窗格](sql-pane-visual-database-tools.md)的陳述式中產生下列 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="ca7b1-115">These grid entries produce the following WHERE clause in the statement in the [SQL Pane](sql-pane-visual-database-tools.md):</span></span>  
  
    ```  
    WHERE (hire_date < '01/01/91') AND  
      (job_lvl = 100)  
    ```  
  
3.  <span data-ttu-id="ca7b1-116">在 [或...]  方格資料行中，輸入想要使用 OR 連結的條件。</span><span class="sxs-lookup"><span data-stu-id="ca7b1-116">In the **Or...** grid column, enter conditions that you want to link with OR.</span></span> <span data-ttu-id="ca7b1-117">例如，若要新增搜尋 `job_lvl` 資料行中其他值的條件，請在 [或...]  資料行中輸入其他值，例如 `= 200`。</span><span class="sxs-lookup"><span data-stu-id="ca7b1-117">For example, to add a condition that searches for another value in the `job_lvl` column, enter an additional value in the **Or...** column, such as `= 200`.</span></span>  
  
     <span data-ttu-id="ca7b1-118">在 [或...]  資料行中新增一個值，就會在 SQL 窗格中將另一個條件新增至陳述式中的 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="ca7b1-118">Adding a value in the **Or...** column adds another condition to the WHERE clause in the statement in the SQL pane:</span></span>  
  
    ```  
    WHERE (hire_date < '01/01/91' ) AND  
      (job_lvl = 100) OR   
      (job_lvl = 200)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ca7b1-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca7b1-119">See Also</span></span>  
 <span data-ttu-id="ca7b1-120">[當或具有 &#40;Visual Database Tools&#41;的優先順序時合併條件](combine-conditions-when-or-has-precedence-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ca7b1-120">[Combine Conditions When OR Has Precedence &#40;Visual Database Tools&#41;](combine-conditions-when-or-has-precedence-visual-database-tools.md) </span></span>  
 <span data-ttu-id="ca7b1-121">[在 [準則] 窗格中合併搜尋條件的慣例 &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ca7b1-121">[Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span></span>  
 <span data-ttu-id="ca7b1-122">[&#40;Visual Database Tools 輸入搜尋值的規則&#41;](rules-for-entering-search-values-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ca7b1-122">[Rules for Entering Search Values &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="ca7b1-123">指定搜尋準則 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="ca7b1-123">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
