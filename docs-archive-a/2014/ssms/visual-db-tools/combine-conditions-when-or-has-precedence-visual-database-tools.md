---
title: 在 OR 具有優先權時結合條件 (Visual Database Tools) | Microsoft Docs
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
- OR operator
ms.assetid: b30f5ac9-25e7-4163-80ed-44e4bccb455d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8be0d2f783c28662eb01f6bf191dc24d339534f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686707"
---
# <a name="combine-conditions-when-or-has-precedence-visual-database-tools"></a><span data-ttu-id="41b5b-102">在 OR 具有優先權時結合條件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="41b5b-102">Combine Conditions When OR Has Precedence (Visual Database Tools)</span></span>
  <span data-ttu-id="41b5b-103">若要使用 OR 來連結條件，並使其優先權超越使用 AND 連結的條件，則必須在每個 OR 條件中重複 AND 條件。</span><span class="sxs-lookup"><span data-stu-id="41b5b-103">To link conditions with OR and give them precedence over conditions linked with AND, you must repeat the AND condition for each OR condition.</span></span>  
  
 <span data-ttu-id="41b5b-104">例如，假設您想要尋找已經在公司工作超過五年，而且在低階工作或已退休的員工。</span><span class="sxs-lookup"><span data-stu-id="41b5b-104">For example, imagine that you want to find all employees who have been with the company more than five years and have lower-level jobs or are retired.</span></span> <span data-ttu-id="41b5b-105">這一查詢需要三個條件，其中一個條件連結至兩個具有 AND 的其他條件：</span><span class="sxs-lookup"><span data-stu-id="41b5b-105">This query requires three conditions, a single condition linked to two additional conditions with AND:</span></span>  
  
-   <span data-ttu-id="41b5b-106">雇用日期在五年之前的員工，以及</span><span class="sxs-lookup"><span data-stu-id="41b5b-106">Employees with a hire date earlier than five years ago, and</span></span>  
  
-   <span data-ttu-id="41b5b-107">工作層級為 100 或其狀態為 "R" (已退休) 的員工。</span><span class="sxs-lookup"><span data-stu-id="41b5b-107">Employees with a job level of 100 or whose status is "R" (for retired).</span></span>  
  
 <span data-ttu-id="41b5b-108">下列程序說明如何在 [準則] 窗格中建立這種查詢。</span><span class="sxs-lookup"><span data-stu-id="41b5b-108">The following procedure illustrates how to create this type of query in the Criteria pane.</span></span>  
  
### <a name="to-combine-conditions-when-or-has-precedence"></a><span data-ttu-id="41b5b-109">若要在 OR 具有優先權時結合條件</span><span class="sxs-lookup"><span data-stu-id="41b5b-109">To combine conditions when OR has precedence</span></span>  
  
1.  <span data-ttu-id="41b5b-110">在 [準則窗格](visual-database-tools.md)中，新增想要搜尋的資料行。</span><span class="sxs-lookup"><span data-stu-id="41b5b-110">In the [Criteria pane](visual-database-tools.md), add the data columns you want to search.</span></span> <span data-ttu-id="41b5b-111">若要搜尋使用由 AND 所連結的兩個或多個條件之相同資料行，就必須針對想要搜尋的每個值，將資料行名稱加入方格中。</span><span class="sxs-lookup"><span data-stu-id="41b5b-111">If you want to search the same column using two or more conditions linked with AND, you must add the data column name to the grid once for each value you want to search.</span></span>  
  
2.  <span data-ttu-id="41b5b-112">在 [篩選條件]  方格資料行中輸入第一個條件，在另一個 [或...]  資料行中輸入第二個 (及後續其他的) 條件，即可建立使用 OR 連結的條件。</span><span class="sxs-lookup"><span data-stu-id="41b5b-112">Create the conditions to be linked with OR by entering the first one into the **Filter** grid column and the second (and subsequent ones) into separate **Or...** columns.</span></span> <span data-ttu-id="41b5b-113">例如，若要使用 OR 連結搜尋 `job_lvl` 和 `status` 資料行的條件，請在 `job_lvl` 的 [篩選條件] 資料行輸入 `= 100`，在 `status` 的 [或...] 資料行輸入 `= 'R'`。</span><span class="sxs-lookup"><span data-stu-id="41b5b-113">For example, to link conditions with OR that search the `job_lvl` and `status` columns, enter `= 100` in the **Filter** column for `job_lvl` and `= 'R'` in the **Or...** column for `status`.</span></span>  
  
     <span data-ttu-id="41b5b-114">輸入上述方格中的值，會在 [SQL] 窗格的陳述式中產生下列 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="41b5b-114">Entering these values in the grid produces the following WHERE clause in the statement in the SQL pane:</span></span>  
  
    ```  
    WHERE (job_lvl = 100) OR (status = 'R')  
    ```  
  
3.  <span data-ttu-id="41b5b-115">藉由輸入每個 OR 條件的 AND 條件，即可建立此條件。</span><span class="sxs-lookup"><span data-stu-id="41b5b-115">Create the AND condition by entering it once for each OR condition.</span></span> <span data-ttu-id="41b5b-116">將每個項目放入相同的方格資料行中，做為它所對應的 OR 條件。</span><span class="sxs-lookup"><span data-stu-id="41b5b-116">Place each entry in the same grid column as the OR condition it corresponds to.</span></span> <span data-ttu-id="41b5b-117">例如，若要新增搜尋 `hire_date` 資料行並套用至這兩個 OR 條件的 AND 條件，請在 [準則] 資料行和 [或...] 資料行中輸入 `< '1/1/91'`。</span><span class="sxs-lookup"><span data-stu-id="41b5b-117">For example, to add an AND condition that searches the `hire_date` column and applies to both OR conditions, enter `< '1/1/91'` in both the Criteria column and the **Or...** column.</span></span>  
  
     <span data-ttu-id="41b5b-118">輸入上述方格中的值，會在 [SQL] 窗格的陳述式中產生下列 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="41b5b-118">Entering these values in the grid produces the following WHERE clause in the statement in the SQL pane:</span></span>  
  
    ```  
    WHERE (job_lvl = 100) AND   
      (hire_date < '01/01/91' ) OR  
      (status = 'R') AND   
      (hire_date < '01/01/91' )  
    ```  
  
    > [!TIP]  
    >  <span data-ttu-id="41b5b-119">您可以藉由新增 AND 條件，然後使用 [編輯]  功能表的 [剪下]  和 [貼上]  命令來重複此條件，即可在其他 OR 條件中重複此條件。</span><span class="sxs-lookup"><span data-stu-id="41b5b-119">You can repeat an AND condition by adding it once, and then using the **Cut** and **Paste** commands from the **Edit** menu to repeat it for other OR conditions.</span></span>  
  
 <span data-ttu-id="41b5b-120">查詢和檢視表設計師所建立的 WHERE 子句相當於下列 WHERE 子句，其中使用括號來指定 OR 的優先權高於 AND：</span><span class="sxs-lookup"><span data-stu-id="41b5b-120">The WHERE clause created by the Query and View Designer is equivalent to the following WHERE clause, which uses parentheses to specify the precedence of OR over AND:</span></span>  
  
```  
WHERE (job_lvl = 100 OR status = 'R') AND  
   (hire_date < '01/01/91')  
```  
  
> [!NOTE]  
>  <span data-ttu-id="41b5b-121">如果您使用緊接在 [SQL 窗格](sql-pane-visual-database-tools.md)之上的格式輸入搜尋條件，然後變更 [圖表] 或 [準則] 窗格中的查詢，則查詢和檢視表設計工具會重新建立 SQL 陳述式，以便讓格式與明確散發給兩個 OR 條件的 AND 條件相符。</span><span class="sxs-lookup"><span data-stu-id="41b5b-121">If you enter the search conditions in the format shown immediately above in the [SQL Pane](sql-pane-visual-database-tools.md), but then make a change to the query in the Diagram or Criteria panes, the Query and View Designer recreates the SQL statement to match the form with the AND condition explicitly distributed to both OR conditions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41b5b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41b5b-122">See Also</span></span>  
 <span data-ttu-id="41b5b-123">[在 [準則] 窗格中合併搜尋條件的慣例 &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span><span class="sxs-lookup"><span data-stu-id="41b5b-123">[Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span></span>  
 [<span data-ttu-id="41b5b-124">指定搜尋準則 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="41b5b-124">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
