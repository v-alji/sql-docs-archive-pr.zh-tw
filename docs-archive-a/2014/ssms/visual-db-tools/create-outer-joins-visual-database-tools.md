---
title: 建立外部聯結 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- outer joins
- joins [SQL Server], outer
ms.assetid: 18de47b1-f936-427d-b852-fe6d20334f71
author: stevestein
ms.author: sstein
ms.openlocfilehash: f02c0be049e2e75e1a657bb3c027d20430d562cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708889"
---
# <a name="create-outer-joins-visual-database-tools"></a><span data-ttu-id="b0fe6-102">建立外部聯結 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b0fe6-102">Create Outer Joins (Visual Database Tools)</span></span>
  <span data-ttu-id="b0fe6-103">在預設狀況下， [查詢和檢視表設計工具](visual-database-tools.md) 會在資料表之間建立內部聯結 (Inner Join)。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-103">By default, the [Query and View Designer](visual-database-tools.md) creates an inner join between tables.</span></span> <span data-ttu-id="b0fe6-104">內部聯結將刪除不符合其他資料表之資料列的資料列。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-104">Inner joins eliminate the rows that do not match with a row from the other table.</span></span> <span data-ttu-id="b0fe6-105">然而，外部聯結則至少傳回 FROM 子句提到的一個資料表或檢視，只要這些資料列符合任何 WHERE 或 HAVING 搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-105">Outer joins, however, return all rows from at least one of the tables or views mentioned in the FROM clause, as long as those rows meet any WHERE or HAVING search conditions.</span></span> <span data-ttu-id="b0fe6-106">若要在不具有符合聯結資料表中資料的結果集中包含資料列，就可以建立外部聯結。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-106">If you want to include data rows in the result set that do not have a match in the joined table, you can create an outer join.</span></span>  
  
 <span data-ttu-id="b0fe6-107">在建立外部聯結時，資料表在 SQL 陳述式中出現的順序 (如 SQL 窗格所反映) 非常重要。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-107">When you create an outer join, the order in which tables appear in the SQL statement (as reflected in the SQL pane) is significant.</span></span> <span data-ttu-id="b0fe6-108">您加入的第一個資料表會成為「左」資料表，第二個資料表會成為「右」資料表</span><span class="sxs-lookup"><span data-stu-id="b0fe6-108">The first table you add becomes the "left" table and the second table becomes the "right" table.</span></span> <span data-ttu-id="b0fe6-109">(資料表出現在 [圖表窗格](diagram-pane-visual-database-tools.md) 的實際順序並不重要)。在指定左或右外部聯結時，是指這些資料表加入查詢時的順序，以及它們出現在 [SQL 窗格](sql-pane-visual-database-tools.md)的 SQL 陳述式中的順序。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-109">(The actual order in which the tables appear in the [Diagram pane](diagram-pane-visual-database-tools.md) is not significant.) When you specify a left or right outer join, you are referring to the order in which the tables were added to the query and to the order in which they appear in the SQL statement in the [SQL pane](sql-pane-visual-database-tools.md).</span></span>  
  
### <a name="to-create-an-outer-join"></a><span data-ttu-id="b0fe6-110">若要建立外部聯結</span><span class="sxs-lookup"><span data-stu-id="b0fe6-110">To create an outer join</span></span>  
  
1.  <span data-ttu-id="b0fe6-111">自動或手動建立聯結。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-111">Create the join, either automatically or manually.</span></span> <span data-ttu-id="b0fe6-112">如需詳細資訊，請參閱[自動聯結資料表 &#40;Visual Database Tools&#41;](join-tables-automatically-visual-database-tools.md) 或[手動聯結資料表 &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-112">For details, see [Join Tables Automatically &#40;Visual Database Tools&#41;](join-tables-automatically-visual-database-tools.md) or [Join Tables Manually &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md).</span></span>  
  
2.  <span data-ttu-id="b0fe6-113">選取 [圖表] 窗格中的聯結線 (Join Line)，然後從 [查詢設計工具] 功能表選擇 [選取 \<tablename> 中所有的資料列]，以選取包含您要併入其額外資料列之資料表的命令。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-113">Select the join line in the Diagram pane, and then from the **Query Designer** menu, choose **Select All Rows from \<tablename>**, selecting the command that includes the table whose extra rows you want to include.</span></span>  
  
    -   <span data-ttu-id="b0fe6-114">選擇第一個資料表以建立左外部聯結。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-114">Choose the first table to create a left outer join.</span></span>  
  
    -   <span data-ttu-id="b0fe6-115">選擇第二個資料表以建立右外部聯結。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-115">Choose the second table to create a right outer join.</span></span>  
  
    -   <span data-ttu-id="b0fe6-116">選擇兩個資料表以建立完整外部聯結 (Full Outer Join)。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-116">Choose both tables to create a full outer join.</span></span>  
  
 <span data-ttu-id="b0fe6-117">在指定外部聯結時，查詢和檢視設計師會修改聯結線以指出外部聯結。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-117">When you specify an outer join, the Query and View Designer modifies the join line to indicate an outer join.</span></span>  
  
 <span data-ttu-id="b0fe6-118">此外，查詢和檢視設計師會修改 [SQL] 窗格中的 SQL 陳述式，以反映聯結類型的變更，如下列陳述式所示：</span><span class="sxs-lookup"><span data-stu-id="b0fe6-118">In addition, the Query and View Designer modifies the SQL statement in the SQL pane to reflect the change in join type, as shown in the following statement:</span></span>  
  
```  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee LEFT OUTER JOIN jobs ON   
    employee.job_id = jobs.job_id  
```  
  
 <span data-ttu-id="b0fe6-119">因為外部聯結包含不符的資料列，因此可以用它來尋找違反外部索引鍵條件約束的資料列。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-119">Because an outer join includes unmatched rows, you can use it to find rows that violate foreign key constraints.</span></span> <span data-ttu-id="b0fe6-120">若要如此，可以建立外部聯結，然後加入搜尋條件，以尋找最右方的資料表中主索引鍵資料行為 null 的資料列。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-120">To do so, you create an outer join and then add a search condition to find rows in which the primary key column of the rightmost table is null.</span></span> <span data-ttu-id="b0fe6-121">例如，下列外部聯結會找出 `employee` 資料表中在 `jobs` 資料表沒有對應資料列的資料列：</span><span class="sxs-lookup"><span data-stu-id="b0fe6-121">For example, the following outer join finds rows in the `employee` table that do not have corresponding rows in the `jobs` table:</span></span>  
  
```  
SELECT employee.emp_id, employee.job_id  
FROM employee LEFT OUTER JOIN jobs   
   ON employee.job_id = jobs.job_id  
WHERE (jobs.job_id IS NULL)  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0fe6-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0fe6-122">See Also</span></span>  
 <span data-ttu-id="b0fe6-123">[使用 Join 查詢 &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b0fe6-123">[Query with Joins &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="b0fe6-124">聯結對話方塊 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b0fe6-124">Join Dialog Box &#40;Visual Database Tools&#41;</span></span>](join-dialog-box-visual-database-tools.md)  
  
  
