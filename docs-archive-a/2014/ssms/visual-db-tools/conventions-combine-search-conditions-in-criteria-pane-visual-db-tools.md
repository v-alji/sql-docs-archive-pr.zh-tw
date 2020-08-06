---
title: 在 [準則] 窗格中合併搜尋條件的慣例 (Visual Database Tools) |Microsoft Docs
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
- multiple OR clauses
- combining search conditions
- OR operator
- AND, Criteria pane
- multiple AND clauses
ms.assetid: d4859be5-ff5b-48b2-a101-ad40c6dbcc68
author: stevestein
ms.author: sstein
ms.openlocfilehash: 684521baa87d5325366a0e18296cd35342a0e947
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686709"
---
# <a name="conventions-for-combining-search-conditions-in-the-criteria-pane-visual-database-tools"></a><span data-ttu-id="6bd94-102">在條件窗格中合併搜尋條件的慣例 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6bd94-102">Conventions for Combining Search Conditions in the Criteria Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="6bd94-103">您可以建立使用任意多個 AND 和 OR 運算子連結，包含任何搜尋條件的查詢。</span><span class="sxs-lookup"><span data-stu-id="6bd94-103">You can create queries that include any number of search conditions, linked with any number of AND and OR operators.</span></span> <span data-ttu-id="6bd94-104">查詢中如有使用 AND 與 OR 子句組合比較複雜，因此建議能夠先了解這類查詢在您執行時的解譯方式，以及這類查詢在 [[準則窗格]](visual-database-tools.md) 及 [SQL 窗格](sql-pane-visual-database-tools.md)中的表示方式。</span><span class="sxs-lookup"><span data-stu-id="6bd94-104">A query with a combination of AND and OR clauses can become complex, so it is helpful to understand how such a query is interpreted when you execute it, and how such a query is represented in the [Criteria Pane](visual-database-tools.md) and [SQL Pane](sql-pane-visual-database-tools.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6bd94-105">如需只包含 AND 或 OR 運算子之搜尋條件的詳細資料，請參閱[指定單一資料行的多重搜尋條件 &#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-one-column-visual-database-tools.md) 及[指定多重資料行的多重搜尋條件 &#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-multiple-columns-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="6bd94-105">For details about search conditions that contain only one AND or OR operator, see [Specify Multiple Search Conditions for One Column &#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-one-column-visual-database-tools.md) and [Specify Multiple Search Conditions for Multiple Columns &#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-multiple-columns-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="6bd94-106">您可以在下面找到的資訊：</span><span class="sxs-lookup"><span data-stu-id="6bd94-106">Below you will find information about:</span></span>  
  
-   <span data-ttu-id="6bd94-107">同時包含 AND 和 OR 運算子的查詢中運算子的優先順序。</span><span class="sxs-lookup"><span data-stu-id="6bd94-107">The precedence of AND and OR in queries that contain both.</span></span>  
  
-   <span data-ttu-id="6bd94-108">AND 和 OR 子句裡各種條件相互的邏輯關係。</span><span class="sxs-lookup"><span data-stu-id="6bd94-108">How the conditions in AND and OR clauses relate logically to one another.</span></span>  
  
-   <span data-ttu-id="6bd94-109">查詢和檢視設計工具在 [準則窗格] 中表示包含 AND 和 OR 的查詢的方式。</span><span class="sxs-lookup"><span data-stu-id="6bd94-109">How the Query and View Designer represents in the Criteria Pane queries that contain both AND and OR.</span></span>  
  
 <span data-ttu-id="6bd94-110">為了協助您了解下列的討論，試想您正在使用包含資料行 `employee` 、 `hire_date`和 `job_lvl`的 `status`資料表。</span><span class="sxs-lookup"><span data-stu-id="6bd94-110">To help you understand the discussion below, imagine that you are working with an `employee` table containing the columns `hire_date`, `job_lvl`, and `status`.</span></span> <span data-ttu-id="6bd94-111">範例假設您必須知道某個員工在公司的年資 (員工的雇用日期)、員工負責的工作類型 (工作階層) 以及員工的狀態 (例如已退休) 等資訊。</span><span class="sxs-lookup"><span data-stu-id="6bd94-111">The examples assume that you need to know information such as how long an employee has worked with the company (that is, what the employee's hire date is), what type of job the employee performs (what the job level is), and the employee's status (for example, retired).</span></span>  
  
## <a name="precedence-of-and-and-or"></a><span data-ttu-id="6bd94-112">AND 和 OR 的優先順序</span><span class="sxs-lookup"><span data-stu-id="6bd94-112">Precedence of AND and OR</span></span>  
 <span data-ttu-id="6bd94-113">執行查詢時，查詢會先評估以 AND 連結的子句，然後再評估以 OR 連結的子句。</span><span class="sxs-lookup"><span data-stu-id="6bd94-113">When a query is executed, it evaluates first the clauses linked with AND, and then those linked with OR.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6bd94-114">NOT 運算子的優先順序高於 AND 和 OR。</span><span class="sxs-lookup"><span data-stu-id="6bd94-114">The NOT operator takes precedence over both AND and OR.</span></span>  
  
 <span data-ttu-id="6bd94-115">例如，要尋找在公司擔任低階層工作，年資在五年以上的員工；或者擔任中階層工作，不論雇用日期為何的員工，可以依照以下範例建構一個 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="6bd94-115">For example, to find either employees who have been with the company for more than five years in lower-level jobs or employees with middle-level jobs without regard for their hire date, you can construct a WHERE clause such as the following:</span></span>  
  
```  
WHERE   
   hire_date < '01/01/95' AND   
   job_lvl = 100 OR  
   job_lvl = 200  
  
```  
  
 <span data-ttu-id="6bd94-116">若要覆寫預設的 AND 先於 OR 的優先順序，可以在 SQL 窗格中利用括號括住特定的條件。</span><span class="sxs-lookup"><span data-stu-id="6bd94-116">To override the default precedence of AND over OR, you can put parentheses around specific conditions in the SQL pane.</span></span> <span data-ttu-id="6bd94-117">括號裡的條件一定會先評估。</span><span class="sxs-lookup"><span data-stu-id="6bd94-117">Conditions in parentheses are always evaluated first.</span></span> <span data-ttu-id="6bd94-118">例如，要尋找在公司擔任低階層或中階層工作且滿五年的員工，可以建構如下的 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="6bd94-118">For example, to find all employees who have been with the company more than five years in either lower or middle-level jobs, you can construct a WHERE clause such as the following:</span></span>  
  
```  
WHERE   
   hire_date < '01/01/95' AND   
   (job_lvl = 100 OR job_lvl = 200)  
```  
  
> [!TIP]  
>  <span data-ttu-id="6bd94-119">為了保持明確，AND 和 OR 合併使用時，建議您加上括號，不要依賴預設的優先順序。</span><span class="sxs-lookup"><span data-stu-id="6bd94-119">It is recommended that, for clarity, you always include parentheses when combining AND and OR clauses instead of relying on the default precedence.</span></span>  
  
## <a name="how-and-works-with-multiple-or-clauses"></a><span data-ttu-id="6bd94-120">AND 和多個 OR 子句配合的方式</span><span class="sxs-lookup"><span data-stu-id="6bd94-120">How AND Works with Multiple OR Clauses</span></span>  
 <span data-ttu-id="6bd94-121">了解 AND 和 OR 子句合併使用時的關聯方式，可幫助您建構及了解查詢和檢視設計工具中複雜的查詢。</span><span class="sxs-lookup"><span data-stu-id="6bd94-121">Understanding how AND and OR clauses are related when combined can help you construct and understand complex queries in the Query and View Designer.</span></span>  
  
 <span data-ttu-id="6bd94-122">如果使用 AND 連結多個條件，以 AND 連結的第一組條件套用於第二組裡的所有條件。</span><span class="sxs-lookup"><span data-stu-id="6bd94-122">If you link multiple conditions using AND, the first set of conditions linked with AND applies to all the conditions in the second set.</span></span> <span data-ttu-id="6bd94-123">換句話說，使用 AND 和其他條件連結的條件會分配至第二組裡的所有條件。</span><span class="sxs-lookup"><span data-stu-id="6bd94-123">In other words, a condition linked with AND to another condition is distributed to all the conditions in the second set.</span></span> <span data-ttu-id="6bd94-124">例如，以下圖說顯示的是連結至一組 OR 條件的 AND 條件：</span><span class="sxs-lookup"><span data-stu-id="6bd94-124">For example, the following schematic representation shows an AND condition linked to a set of OR conditions:</span></span>  
  
```  
A AND (B OR C)  
```  
  
 <span data-ttu-id="6bd94-125">以上式子在邏輯上等於下面的式子，顯示 AND 條件是如何分散至第二組條件的：</span><span class="sxs-lookup"><span data-stu-id="6bd94-125">The representation above is logically equivalent to the following schematic representation, which shows how the AND condition is distributed to the second set of conditions:</span></span>  
  
```  
(A AND B) OR (A AND C)  
```  
  
 <span data-ttu-id="6bd94-126">此分散原則會影響使用查詢和檢視設計工具的方式。</span><span class="sxs-lookup"><span data-stu-id="6bd94-126">This distributive principle affects how you use the Query and View Designer.</span></span> <span data-ttu-id="6bd94-127">例如，想像一下您要尋找已經在公司擔任低階層或中階層工作且滿五年的員工。</span><span class="sxs-lookup"><span data-stu-id="6bd94-127">For example, imagine that you are looking for all employees who have been with the company more than five years in either lower or middle-level jobs.</span></span> <span data-ttu-id="6bd94-128">在 [SQL 窗格] 的陳述式中輸入以下的 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="6bd94-128">You enter the following WHERE clause into the statement in the SQL pane:</span></span>  
  
```  
WHERE (hire_date < '01/01/95' ) AND   
   (job_lvl = 100 OR job_lvl = 200)  
```  
  
 <span data-ttu-id="6bd94-129">以 AND 連結的子句會套用至以 OR 連結的兩個子句。</span><span class="sxs-lookup"><span data-stu-id="6bd94-129">The clause linked with AND applies to both clauses linked with OR.</span></span> <span data-ttu-id="6bd94-130">明確表示這種情形的方法是在 OR 子句裡的每一個條件重複一次 AND 條件。</span><span class="sxs-lookup"><span data-stu-id="6bd94-130">An explicit way to express this is to repeat the AND condition once for each condition in the OR clause.</span></span> <span data-ttu-id="6bd94-131">以下的陳述式比前面的陳述式更明確 (也更長)，但是在邏輯上相等：</span><span class="sxs-lookup"><span data-stu-id="6bd94-131">The following statement is more explicit (and longer) than the previous statement, but is logically equivalent to it:</span></span>  
  
```  
WHERE    (hire_date < '01/01/95' ) AND  
  (job_lvl = 100) OR   
  (hire_date < '01/01/95' ) AND   
  (job_lvl = 200)  
```  
  
 <span data-ttu-id="6bd94-132">不論有多少個個別的條件，將 AND 子句分散至連結的 OR 子句的原則都適用。</span><span class="sxs-lookup"><span data-stu-id="6bd94-132">The principle of distributing AND clauses to linked OR clauses applies no matter how many individual conditions are involved.</span></span> <span data-ttu-id="6bd94-133">例如，想像您要尋找在公司任職已滿五年或已退休的高階層或中階層員工。</span><span class="sxs-lookup"><span data-stu-id="6bd94-133">For example, imagine that you want to find higher or middle-level employees who have been with the company more than five years or are retired.</span></span> <span data-ttu-id="6bd94-134">WHERE 子句看起來應該像是這樣：</span><span class="sxs-lookup"><span data-stu-id="6bd94-134">The WHERE clause might look like this:</span></span>  
  
```  
WHERE   
   (job_lvl = 200 OR job_lvl = 300) AND  
   (hire_date < '01/01/95' ) OR (status = 'R')  
```  
  
 <span data-ttu-id="6bd94-135">分散了使用 AND 連結的條件以後，WHERE 子句看起來就像這樣：</span><span class="sxs-lookup"><span data-stu-id="6bd94-135">After the conditions linked with AND have been distributed, the WHERE clause will look like this:</span></span>  
  
```  
WHERE   
   (job_lvl = 200 AND hire_date < '01/01/95' ) OR  
   (job_lvl = 200 AND status = 'R') OR  
   (job_lvl = 300 AND hire_date < '01/01/95' ) OR  
   (job_lvl = 300 AND status = 'R')   
```  
  
## <a name="how-multiple-and-and-or-clauses-are-represented-in-the-criteria-pane"></a><span data-ttu-id="6bd94-136">多個 AND 和 OR 子句在準則窗格中表示的方式</span><span class="sxs-lookup"><span data-stu-id="6bd94-136">How Multiple AND and OR Clauses Are Represented in the Criteria Pane</span></span>  
 <span data-ttu-id="6bd94-137">查詢和檢視設計工具會在 [準則窗格](visual-database-tools.md)中表示您的搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="6bd94-137">The Query and View Designer represents your search conditions in the [Criteria Pane](visual-database-tools.md).</span></span> <span data-ttu-id="6bd94-138">然而，如果以 AND 和 OR 連結多個子句，[準則窗格] 中呈現的可能就不是您所預料的結果。</span><span class="sxs-lookup"><span data-stu-id="6bd94-138">However, in some cases that involve multiple clauses linked with AND and OR, the representation in the Criteria Pane might not be what you expect.</span></span> <span data-ttu-id="6bd94-139">此外，若您在 [準則窗格] 或 [圖表窗格](diagram-pane-visual-database-tools.md)中修改查詢，您可能會發現您的 SQL 陳述式已經變更，與您所輸入的不同。</span><span class="sxs-lookup"><span data-stu-id="6bd94-139">In addition, if you modify your query in the Criteria Pane or [Diagram Pane](diagram-pane-visual-database-tools.md), you might find that your SQL statement has been changed from what you entered.</span></span>  
  
 <span data-ttu-id="6bd94-140">一般而言，這些規則指示了 AND 和 OR 子句在 [準則窗格] 中顯示的方式：</span><span class="sxs-lookup"><span data-stu-id="6bd94-140">In general, these rules dictate how AND and OR clauses appear in the Criteria Pane:</span></span>  
  
-   <span data-ttu-id="6bd94-141">所有使用 AND 連結的條件都會顯示在 [篩選]  格線欄或同一個 [或...]  資料欄中。</span><span class="sxs-lookup"><span data-stu-id="6bd94-141">All conditions linked with AND appear in the **Filter** grid column or in the same **Or...** column.</span></span>  
  
-   <span data-ttu-id="6bd94-142">所有使用 OR 連結的條件都會顯示在不同的 [或...]  資料欄中。</span><span class="sxs-lookup"><span data-stu-id="6bd94-142">All conditions linked with OR appear in separate **Or...** columns.</span></span>  
  
-   <span data-ttu-id="6bd94-143">如果 AND 和 OR 子句合併的邏輯結果是 AND 分散至數個 OR 子句，[準則窗格] 會以需要的次數重複 AND 子句，以明確表示這一點。</span><span class="sxs-lookup"><span data-stu-id="6bd94-143">If the logical result of a combination of AND and OR clauses is that the AND is distributed into several OR clauses, the Criteria Pane represents this explicitly by repeating the AND clause as many times as necessary.</span></span>  
  
 <span data-ttu-id="6bd94-144">例如，您可以在 [SQL 窗格] 中建立如下的搜尋條件，利用 AND 連結的兩個子句優先於使用 OR 連結的第三個子句：</span><span class="sxs-lookup"><span data-stu-id="6bd94-144">For example, in the SQL pane you might create a search condition such as the following, in which two clauses linked with AND take precedence over a third one linked with OR:</span></span>  
  
```  
WHERE (hire_date < '01/01/95' ) AND   
  (job_lvl = 100) OR   
  (status = 'R')  
```  
  
 <span data-ttu-id="6bd94-145">查詢和檢視設計工具會在 [準則窗格] 中如下顯示此 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="6bd94-145">The Query and View Designer represents this WHERE clause in the Criteria Pane as follows:</span></span>  
  
 <span data-ttu-id="6bd94-146">![準則窗格中的 OR 子句優先順序](../../database-engine/media//vs-criteriapane1.gif "準則窗格中的 OR 子句優先順序")</span><span class="sxs-lookup"><span data-stu-id="6bd94-146">![OR clause precedence in the Criteria Pane](../../database-engine/media//vs-criteriapane1.gif "OR clause precedence in the Criteria Pane")</span></span>  
  
 <span data-ttu-id="6bd94-147">但是，如果連結的 OR 子句優先於 AND 子句，將會為每一個 OR 子句重複 AND 子句。</span><span class="sxs-lookup"><span data-stu-id="6bd94-147">However, if the linked OR clauses take precedence over an AND clause, the AND clause is repeated for each OR clause.</span></span> <span data-ttu-id="6bd94-148">這會使得 AND 子句分散至每一個 OR 子句。</span><span class="sxs-lookup"><span data-stu-id="6bd94-148">This causes the AND clause to be distributed to each OR clause.</span></span> <span data-ttu-id="6bd94-149">例如，您可以在 [SQL 窗格] 中建立如下所示的 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="6bd94-149">For example, in the SQL pane you might create a WHERE clause such as the following:</span></span>  
  
```  
WHERE (hire_date < '01/01/95' ) AND   
  ( (job_lvl = 100) OR   
  (status = 'R') )  
```  
  
 <span data-ttu-id="6bd94-150">查詢和檢視設計工具會在 [準則窗格] 中如下顯示此 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="6bd94-150">The Query and View Designer represents this WHERE clause in the Criteria Pane as follows:</span></span>  
  
 <span data-ttu-id="6bd94-151">![準則窗格中的多個 AND 和 OR 子句](../../database-engine/media//vs-criteriapane2.gif "準則窗格中的多個 AND 和 OR 子句")</span><span class="sxs-lookup"><span data-stu-id="6bd94-151">![Multiple AND and OR clauses in the Criteria Pane](../../database-engine/media//vs-criteriapane2.gif "Multiple AND and OR clauses in the Criteria Pane")</span></span>  
  
 <span data-ttu-id="6bd94-152">如果連結的 OR 子句只牽涉到一個資料行，查詢和檢視設計工具可以將整個 OR 子句放入方格的單一資料格內，避免重複 AND 子句的必要。</span><span class="sxs-lookup"><span data-stu-id="6bd94-152">If the linked OR clauses involve only one data column, the Query and View Designer can place the entire OR clause into a single cell of the grid, avoiding the need to repeat the AND clause.</span></span> <span data-ttu-id="6bd94-153">例如，您可以在 [SQL 窗格] 中建立如下所示的 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="6bd94-153">For example, in the SQL pane you might create a WHERE clause such as the following:</span></span>  
  
```  
WHERE (hire_date < '01/01/95' ) AND   
  ((status = 'R') OR (status = 'A'))  
```  
  
 <span data-ttu-id="6bd94-154">查詢和檢視設計工具會在 [準則窗格] 中如下顯示此 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="6bd94-154">The Query and View Designer represents this WHERE clause in the Criteria Pane as follows:</span></span>  
  
 <span data-ttu-id="6bd94-155">![準則窗格中定義的連結 OR 子句](../../database-engine/media//vs-criteriapane3.gif "準則窗格中定義的連結 OR 子句")</span><span class="sxs-lookup"><span data-stu-id="6bd94-155">![Linked OR clauses defined in the Criteria Pane](../../database-engine/media//vs-criteriapane3.gif "Linked OR clauses defined in the Criteria Pane")</span></span>  
  
 <span data-ttu-id="6bd94-156">如果您變更查詢 (例如變更 [準則窗格] 中的其中一個值)，查詢和檢視設計工具會在 [SQL 窗格] 中重建 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6bd94-156">If you make a change to the query (such as changing one of the values in the Criteria Pane), the Query and View Designer recreates the SQL statement in the SQL pane.</span></span> <span data-ttu-id="6bd94-157">重建的 SQL 陳述式和 [準則窗格] 中顯示的內容類似，而不是和原始陳述式類似。</span><span class="sxs-lookup"><span data-stu-id="6bd94-157">The recreated SQL statement will resemble the Criteria Pane display rather than your original statement.</span></span> <span data-ttu-id="6bd94-158">例如，[準則窗格] 中如果包含了分散式 AND 子句，[SQL 窗格] 中產生的陳述式將會以明確的分散式 AND 子句重建。</span><span class="sxs-lookup"><span data-stu-id="6bd94-158">For example, if the Criteria Pane contains distributed AND clauses, the resulting statement in the SQL pane will be recreated with explicit distributed AND clauses.</span></span> <span data-ttu-id="6bd94-159">如需詳細資訊，請參閱此主題中的＜AND 和多個 OR 子句配合的方式＞。</span><span class="sxs-lookup"><span data-stu-id="6bd94-159">For details, see "How AND Works with Multiple OR Clauses" earlier in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bd94-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bd94-160">See Also</span></span>  
 [<span data-ttu-id="6bd94-161">指定搜尋準則 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="6bd94-161">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
