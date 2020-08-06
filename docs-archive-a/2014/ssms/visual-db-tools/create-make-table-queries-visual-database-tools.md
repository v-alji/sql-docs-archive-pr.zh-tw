---
title: 建立製成資料表查詢 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], types
- table creation [SQL Server], Make Table query
- inserting tables
- Make Table query
- adding tables
ms.assetid: 4493cffa-7b2d-4c24-8ef0-d49329198972
author: stevestein
ms.author: sstein
ms.openlocfilehash: 91c4a3bf45935053789d6e884b1af5b338b4c7c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699115"
---
# <a name="create-make-table-queries-visual-database-tools"></a><span data-ttu-id="db0f5-102">建立製成資料表查詢 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="db0f5-102">Create Make Table Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="db0f5-103">您可以使用製成資料表查詢 (Make Table Query)，將資料列複製到新的資料表中；這種方法非常適合用來建立要使用的資料子集，或是將資料表的內容從其中一個資料庫複製到另一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="db0f5-103">You can copy rows into a new table using a Make Table query, which is useful for creating subsets of data to work with or copying the contents of a table from one database to another.</span></span> <span data-ttu-id="db0f5-104">製成資料表查詢與插入結果查詢相似，但前者會建立用來複製資料列的新資料表。</span><span class="sxs-lookup"><span data-stu-id="db0f5-104">A Make Table query is similar to an Insert Results query but creates a new table to copy rows into.</span></span>  
  
 <span data-ttu-id="db0f5-105">建立製成資料表查詢時，請指定：</span><span class="sxs-lookup"><span data-stu-id="db0f5-105">When you create a Make Table query, you specify:</span></span>  
  
-   <span data-ttu-id="db0f5-106">新資料庫資料表 (目的資料表) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="db0f5-106">The name of the new database table (the destination table).</span></span>  
  
-   <span data-ttu-id="db0f5-107">從中複製資料列的一或多個資料表 (來源資料表)。</span><span class="sxs-lookup"><span data-stu-id="db0f5-107">The table or tables to copy rows from (the source table).</span></span> <span data-ttu-id="db0f5-108">您可以從單一資料表或聯結資料表複製資料列。</span><span class="sxs-lookup"><span data-stu-id="db0f5-108">You can copy from a single table or from joined tables.</span></span>  
  
-   <span data-ttu-id="db0f5-109">要從中複製內容的來源資料表資料行。</span><span class="sxs-lookup"><span data-stu-id="db0f5-109">The columns in the source table whose contents you want to copy.</span></span>  
  
-   <span data-ttu-id="db0f5-110">排序次序 (若要以特定次序複製資料列)。</span><span class="sxs-lookup"><span data-stu-id="db0f5-110">Sort order, if you want to copy the rows in a particular order.</span></span>  
  
-   <span data-ttu-id="db0f5-111">搜尋條件，用來定義要複製的資料列。</span><span class="sxs-lookup"><span data-stu-id="db0f5-111">Search conditions to define the rows you want to copy.</span></span>  
  
-   <span data-ttu-id="db0f5-112">[群組依據] 選項 (如果只要複製摘要資訊)。</span><span class="sxs-lookup"><span data-stu-id="db0f5-112">Group By options, if you want to copy only summary information.</span></span>  
  
 <span data-ttu-id="db0f5-113">例如，下列查詢會建立名為 `uk`_`customers` 的新資料表，並將 `customers` 資料表中的資訊複製到新資料表中：</span><span class="sxs-lookup"><span data-stu-id="db0f5-113">For example, the following query creates a new table called `uk`_`customers` and copies information from the `customers` table to it:</span></span>  
  
```  
SELECT *   
INTO uk_customers  
FROM customers  
WHERE country = 'UK'  
```  
  
 <span data-ttu-id="db0f5-114">若要順利使用製成資料表查詢：</span><span class="sxs-lookup"><span data-stu-id="db0f5-114">In order to use a Make Table query successfully:</span></span>  
  
-   <span data-ttu-id="db0f5-115">資料庫必須支援 SELECT...INTO 語法。</span><span class="sxs-lookup"><span data-stu-id="db0f5-115">Your database must support the SELECT...INTO syntax.</span></span>  
  
-   <span data-ttu-id="db0f5-116">必須擁有在目標資料庫中建立資料表的使用權限。</span><span class="sxs-lookup"><span data-stu-id="db0f5-116">You must have permission to create a table in the target database.</span></span>  
  
### <a name="to-create-a-make-table-query"></a><span data-ttu-id="db0f5-117">若要建立製成資料表查詢</span><span class="sxs-lookup"><span data-stu-id="db0f5-117">To create a Make Table query</span></span>  
  
1.  <span data-ttu-id="db0f5-118">將一或多個來源資料表加入至 [圖表] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="db0f5-118">Add the source table or tables to the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="db0f5-119">從 [查詢設計工具]  功能表中，指向 [變更類型]  ，然後按一下 [製成資料表]  。</span><span class="sxs-lookup"><span data-stu-id="db0f5-119">From the **Query Designer** menu, point to **Change Type**, and then click **Make Table**.</span></span>  
  
3.  <span data-ttu-id="db0f5-120">在 [製成資料表]  對話方塊中，輸入目的資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="db0f5-120">In the **Make Table** dialog box, type the name of the destination table.</span></span> <span data-ttu-id="db0f5-121">查詢和檢視設計師並不會檢查名稱是否存在，或您是否具有建立資料表的權限。</span><span class="sxs-lookup"><span data-stu-id="db0f5-121">The Query and View Designer does not check whether the name is already in use or whether you have permission to create the table.</span></span>  
  
     <span data-ttu-id="db0f5-122">若要在其他資料庫中建立目的資料表，請指定完整的資料表名稱，包括目標資料庫名稱、擁有人 (如有需要) 和資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="db0f5-122">To create a destination table in another database, specify a fully qualified table name including the name of the target database, the owner (if required), and the name of the table.</span></span>  
  
4.  <span data-ttu-id="db0f5-123">指定並將要複製的資料行加入至查詢中。</span><span class="sxs-lookup"><span data-stu-id="db0f5-123">Specify the columns to copy by adding them to the query.</span></span> <span data-ttu-id="db0f5-124">如需詳細資訊，請參閱[將資料行新增至查詢 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="db0f5-124">For details, see [Add Columns to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span> <span data-ttu-id="db0f5-125">只有加入查詢中的資料行才會複製。</span><span class="sxs-lookup"><span data-stu-id="db0f5-125">Columns will be copied only if you add them to the query.</span></span> <span data-ttu-id="db0f5-126">若要複製整個資料列，請選擇 [ \*\* \* (所有\*\*資料行]) 。</span><span class="sxs-lookup"><span data-stu-id="db0f5-126">To copy entire rows, choose **\* (All Columns)**.</span></span>  
  
     <span data-ttu-id="db0f5-127">查詢和檢視表設計工具會將您選擇的資料行新增至 [準則] 窗格的 [資料行]  資料行。</span><span class="sxs-lookup"><span data-stu-id="db0f5-127">The Query and View Designer adds the columns you choose to the **Column** column of the Criteria pane.</span></span>  
  
5.  <span data-ttu-id="db0f5-128">若要以特定次序複製資料列，請指定排序次序。</span><span class="sxs-lookup"><span data-stu-id="db0f5-128">If you want to copy rows in a particular order, specify a sort order.</span></span> <span data-ttu-id="db0f5-129">如需詳細資訊，請參閱 **排序和群組查詢結果**。</span><span class="sxs-lookup"><span data-stu-id="db0f5-129">For details, see **Sorting and Grouping Query Results**.</span></span>  
  
6.  <span data-ttu-id="db0f5-130">輸入搜尋條件以指定要複製的資料列。</span><span class="sxs-lookup"><span data-stu-id="db0f5-130">Specify the rows to copy by entering search conditions.</span></span> <span data-ttu-id="db0f5-131">如需詳細資訊，請參閱[指定搜尋準則 &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="db0f5-131">For details, see [Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md).</span></span>  
  
     <span data-ttu-id="db0f5-132">如果沒有指定搜尋條件，便會將來源資料表的所有資料列複製到目的資料表中。</span><span class="sxs-lookup"><span data-stu-id="db0f5-132">If you do not specify a search condition, all rows from the source table will be copied to the destination table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="db0f5-133">當將要搜尋的資料行加入至 [準則] 窗格時，[查詢和檢視設計師] 也會將它加入至要複製的資料行清單中。</span><span class="sxs-lookup"><span data-stu-id="db0f5-133">When you add a column to search to the Criteria pane, the Query and View Designer also adds it to the list of columns to copy.</span></span> <span data-ttu-id="db0f5-134">如果想使用某一資料行進行搜尋但不想複製它，請在代表資料表或表格化物件 (Table-Structured Object) 的矩形中，清除資料行名稱旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="db0f5-134">If you want to use a column for searching but not copy it, clear the check box next to the column name in the rectangle representing the table or table-structured object.</span></span>  
  
7.  <span data-ttu-id="db0f5-135">若要複製摘要資訊，請指定 [群組依據] 選項。</span><span class="sxs-lookup"><span data-stu-id="db0f5-135">If you want to copy summary information, specify Group By options.</span></span> <span data-ttu-id="db0f5-136">如需詳細資訊，請參閱[摘要查詢結果 &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="db0f5-136">For details, see [Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="db0f5-137">執行製成資料表查詢時， [結果窗格](results-pane-visual-database-tools.md)不會報告結果。</span><span class="sxs-lookup"><span data-stu-id="db0f5-137">When you execute a Make Table query, no results are reported in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="db0f5-138">而是出現訊息指出已經複製了多少資料列。</span><span class="sxs-lookup"><span data-stu-id="db0f5-138">Instead, a message appears indicating how many rows were copied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db0f5-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db0f5-139">See Also</span></span>  
 <span data-ttu-id="db0f5-140">[設計查詢和觀看 how to 主題 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="db0f5-140">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="db0f5-141">查詢的類型 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="db0f5-141">Types of Queries &#40;Visual Database Tools&#41;</span></span>](types-of-queries-visual-database-tools.md)  
  
  
