---
title: 在相同查詢中使用 HAVING 和 WHERE 子句 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- search criteria [SQL Server], WHERE clause
- search conditions [SQL Server], HAVING clause
- row excluded in search [SQL Server]
- search criteria [SQL Server], HAVING clause
- HAVING clause, search criteria
- search conditions [SQL Server], WHERE clause
- WHERE clause, search criteria
- excluding rows
ms.assetid: 1e07cf56-b4b7-4c49-8ddd-c276812a7148
author: stevestein
ms.author: sstein
ms.openlocfilehash: 20f6b471a60bf225ee61bdbbf0ecec30f21a92cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687409"
---
# <a name="use-having-and-where-clauses-in-the-same-query-visual-database-tools"></a><span data-ttu-id="4a56f-102">在相同查詢中使用 HAVING 和 WHERE 子句 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="4a56f-102">Use HAVING and WHERE Clauses in the Same Query (Visual Database Tools)</span></span>
  <span data-ttu-id="4a56f-103">在某些情況下，將條件套用到整個群組 (使用 HAVING 子句) 之前，您可能會想排除群組中的個別資料列 (使用 WHERE 子句)。</span><span class="sxs-lookup"><span data-stu-id="4a56f-103">In some instances, you might want to exclude individual rows from groups (using a WHERE clause) before applying a condition to groups as a whole (using a HAVING clause).</span></span>  
  
 <span data-ttu-id="4a56f-104">HAVING 子句類似 WHERE 子句，但是只適用於整個群組 (也就是在結果集中表示群組的資料列)，而 WHERE 子句則適用於個別資料列。</span><span class="sxs-lookup"><span data-stu-id="4a56f-104">A HAVING clause is like a WHERE clause, but applies only to groups as a whole (that is, to the rows in the result set representing groups), whereas the WHERE clause applies to individual rows.</span></span> <span data-ttu-id="4a56f-105">查詢可以同時包含 WHERE 子句和 HAVING 子句。</span><span class="sxs-lookup"><span data-stu-id="4a56f-105">A query can contain both a WHERE clause and a HAVING clause.</span></span> <span data-ttu-id="4a56f-106">在此情況下：</span><span class="sxs-lookup"><span data-stu-id="4a56f-106">In that case:</span></span>  
  
-   <span data-ttu-id="4a56f-107">WHERE 子句會先套用到 [圖表] 窗格的資料表或資料表值物件的個別資料列。</span><span class="sxs-lookup"><span data-stu-id="4a56f-107">The WHERE clause is applied first to the individual rows in the tables or table-valued objects in the Diagram pane.</span></span> <span data-ttu-id="4a56f-108">只有符合 WHERE 子句條件的資料列才會被分組。</span><span class="sxs-lookup"><span data-stu-id="4a56f-108">Only the rows that meet the conditions in the WHERE clause are grouped.</span></span>  
  
-   <span data-ttu-id="4a56f-109">然後 HAVING 子句會套用到結果集的資料列。</span><span class="sxs-lookup"><span data-stu-id="4a56f-109">The HAVING clause is then applied to the rows in the result set.</span></span> <span data-ttu-id="4a56f-110">只有符合 HAVING 條件的群組才會出現在查詢輸出中。</span><span class="sxs-lookup"><span data-stu-id="4a56f-110">Only the groups that meet the HAVING conditions appear in the query output.</span></span> <span data-ttu-id="4a56f-111">您只能將 HAVING 子句套用到也出現在 GROUP BY 子句或彙總函式的資料行。</span><span class="sxs-lookup"><span data-stu-id="4a56f-111">You can apply a HAVING clause only to columns that also appear in the GROUP BY clause or in an aggregate function.</span></span>  
  
 <span data-ttu-id="4a56f-112">例如，想像您將 `titles` 和 `publishers` 資料表加以聯結，建立能顯示不同出版商平均書價的查詢。</span><span class="sxs-lookup"><span data-stu-id="4a56f-112">For example, imagine that you are joining the `titles` and `publishers` tables to create a query showing the average book price for a set of publishers.</span></span> <span data-ttu-id="4a56f-113">您只想看到某一群特定出版商的平均價格，也許是加州的出版商。</span><span class="sxs-lookup"><span data-stu-id="4a56f-113">You want to see the average price for only a specific set of publishers - perhaps only the publishers in the state of California.</span></span> <span data-ttu-id="4a56f-114">甚至，您只想看平均價格超過 $10.00 的出版商。</span><span class="sxs-lookup"><span data-stu-id="4a56f-114">And even then, you want to see the average price only if it is over $10.00.</span></span>  
  
 <span data-ttu-id="4a56f-115">您可以加入 WHERE 子句以建立第一個條件，忽略任何不在加州的出版商，然後才計算平均價格。</span><span class="sxs-lookup"><span data-stu-id="4a56f-115">You can establish the first condition by including a WHERE clause, which discards any publishers that are not in California, before calculating average prices.</span></span> <span data-ttu-id="4a56f-116">第二個條件需要 HAVING 子句，因為條件是以資料的分組和摘要結果為基礎。</span><span class="sxs-lookup"><span data-stu-id="4a56f-116">The second condition requires a HAVING clause, because the condition is based on the results of grouping and summarizing the data.</span></span> <span data-ttu-id="4a56f-117">產生的 SQL 陳述式將如下所示：</span><span class="sxs-lookup"><span data-stu-id="4a56f-117">The resulting SQL statement might look like this:</span></span>  
  
```  
SELECT titles.pub_id, AVG(titles.price)  
FROM titles INNER JOIN publishers  
   ON titles.pub_id = publishers.pub_id  
WHERE publishers.state = 'CA'  
GROUP BY titles.pub_id  
HAVING AVG(price) > 10  
```  
  
 <span data-ttu-id="4a56f-118">您可以在 [準則] 窗格中同時建立 HAVING 和 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="4a56f-118">You can create both HAVING and WHERE clauses in the Criteria pane.</span></span> <span data-ttu-id="4a56f-119">依照預設，如果您為資料行指定搜尋條件，條件會成為 HAVING 子句的一部分。</span><span class="sxs-lookup"><span data-stu-id="4a56f-119">By default, if you specify a search condition for a column, the condition becomes part of the HAVING clause.</span></span> <span data-ttu-id="4a56f-120">然而，您可以將條件變更為 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="4a56f-120">However, you can change the condition to be a WHERE clause.</span></span>  
  
 <span data-ttu-id="4a56f-121">您可以建立需要相同資料行的 WHERE 子句和 HAVING 子句。</span><span class="sxs-lookup"><span data-stu-id="4a56f-121">You can create a WHERE clause and HAVING clause involving the same column.</span></span> <span data-ttu-id="4a56f-122">若要這樣做，您必須加入兩次資料行到 [準則] 窗格，然後指定一個準則做為 HAVING 子句的一部分，另外一個準則做為 WHERE 子句的一部分。</span><span class="sxs-lookup"><span data-stu-id="4a56f-122">To do so, you must add the column twice to the Criteria pane, then specify one instance as part of the HAVING clause and the other instance as part of the WHERE clause.</span></span>  
  
### <a name="to-specify-a-where-condition-in-an-aggregate-query"></a><span data-ttu-id="4a56f-123">若要在彙總查詢指定 WHERE 條件</span><span class="sxs-lookup"><span data-stu-id="4a56f-123">To specify a WHERE condition in an aggregate query</span></span>  
  
1.  <span data-ttu-id="4a56f-124">為您的查詢指定群組。</span><span class="sxs-lookup"><span data-stu-id="4a56f-124">Specify the groups for your query.</span></span> <span data-ttu-id="4a56f-125">如需詳細資訊，請參閱[群組查詢結果中的資料列 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="4a56f-125">For details, see [Group Rows in Query Results &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
2.  <span data-ttu-id="4a56f-126">如果沒有出現在 [準則] 窗格中，加入您想要組成 WHERE 條件的資料行。</span><span class="sxs-lookup"><span data-stu-id="4a56f-126">If it is not already in the Criteria pane, add the column on which you want to base the WHERE condition.</span></span>  
  
3.  <span data-ttu-id="4a56f-127">除非資料的資料行是 GROUP BY 子句的一部分，或包含在彙總函式中，否則清除 [輸出]  資料行。</span><span class="sxs-lookup"><span data-stu-id="4a56f-127">Clear the **Output** column unless the data column is part of the GROUP BY clause or included in an aggregate function.</span></span>  
  
4.  <span data-ttu-id="4a56f-128">在 [篩選條件]  資料行中，指定 WHERE 條件。</span><span class="sxs-lookup"><span data-stu-id="4a56f-128">In the **Filter** column, specify the WHERE condition.</span></span> <span data-ttu-id="4a56f-129">[查詢和檢視設計師] 會將條件加入到 SQL 陳述式的 HAVING 子句。</span><span class="sxs-lookup"><span data-stu-id="4a56f-129">The Query and View Designer adds the condition to the HAVING clause of the SQL statement.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4a56f-130">在這個程序中所顯示的查詢範例聯結了兩個資料表， `titles` 和 `publishers`。</span><span class="sxs-lookup"><span data-stu-id="4a56f-130">The query shown in the example for this procedure joins two tables, `titles` and `publishers`.</span></span>  
  
     <span data-ttu-id="4a56f-131">這個時候，在查詢中 SQL 陳述式包含一個 HAVING 子句：</span><span class="sxs-lookup"><span data-stu-id="4a56f-131">At this point in the query, the SQL statement contains a HAVING clause:</span></span>  
  
    ```  
    SELECT titles.pub_id, AVG(titles.price)  
    FROM titles INNER JOIN publishers   
       ON titles.pub_id = publishers.pub_id  
    GROUP BY titles.pub_id  
    HAVING publishers.state = 'CA'  
    ```  
  
5.  <span data-ttu-id="4a56f-132">在 [群組依據]  資料行中，從群組和摘要選項清單中選擇 [Where]  。</span><span class="sxs-lookup"><span data-stu-id="4a56f-132">In the **Group By** column, select **Where** from the list of group and summary options.</span></span> <span data-ttu-id="4a56f-133">[查詢和檢視設計師] 移除 SQL 陳述式中的 HAVING 子句條件，然後加入到 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="4a56f-133">The Query and View Designer removes the condition from the HAVING clause in the SQL statement and adds it to the WHERE clause.</span></span>  
  
     <span data-ttu-id="4a56f-134">SQL 陳述式變更為包含了 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="4a56f-134">The SQL statement changes to include a WHERE clause instead:</span></span>  
  
    ```  
    SELECT titles.pub_id, AVG(titles.price)  
    FROM titles INNER JOIN publishers   
       ON titles.pub_id = publishers.pub_id  
    WHERE publishers.state = 'CA'  
    GROUP BY titles.pub_id  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4a56f-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a56f-135">See Also</span></span>  
 <span data-ttu-id="4a56f-136">[排序和分組查詢結果 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="4a56f-136">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="4a56f-137">摘要查詢結果 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="4a56f-137">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
  
  
