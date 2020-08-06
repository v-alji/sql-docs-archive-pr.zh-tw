---
title: 建立插入結果查詢 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], types
- result sets [SQL Server], queries
- results [SQL Server], query
- Insert Results query
- queries [SQL Server], results
ms.assetid: 8770d630-09cc-47ec-a0e9-e9de2d7bbc89
author: stevestein
ms.author: sstein
ms.openlocfilehash: 02643c2cf3295debe740a696941f8730d4417254
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699118"
---
# <a name="create-insert-results-queries-visual-database-tools"></a><span data-ttu-id="db31e-102">建立插入結果查詢 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="db31e-102">Create Insert Results Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="db31e-103">您可以使用插入結果查詢，將某個資料表的資料列複製到另一個資料表，或者在資料表中複製資料列。</span><span class="sxs-lookup"><span data-stu-id="db31e-103">You can copy rows from one table to another or within a table using an Insert Results query.</span></span> <span data-ttu-id="db31e-104">例如，在 `titles` 資料表中，您可以使用插入結果查詢，將關於某個簽發者所有標題的資訊，複製到可供該簽發者使用的第二份資料表。</span><span class="sxs-lookup"><span data-stu-id="db31e-104">For example, in a `titles` table, you can use an Insert Results query to copy information about all the titles for one publisher to a second table that you can make available to that publisher.</span></span> <span data-ttu-id="db31e-105">插入結果查詢與製成資料表查詢 (Make Table Query) 類似，但是可以將資料列複製到現有的資料表中。</span><span class="sxs-lookup"><span data-stu-id="db31e-105">An Insert Results query is similar to Make Table Queries, but copies rows into an existing table.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="db31e-106">您也可以使用剪貼的方式將某個資料表的資料列複製到另一個資料表。</span><span class="sxs-lookup"><span data-stu-id="db31e-106">You can also copy rows from one table to another using cut and paste.</span></span> <span data-ttu-id="db31e-107">針對每個資料表建立一項查詢，並執行查詢。</span><span class="sxs-lookup"><span data-stu-id="db31e-107">Create a query for each table and run the queries.</span></span> <span data-ttu-id="db31e-108">從其中一個結果方格，將需要的資料列複製到另一個結果方格。</span><span class="sxs-lookup"><span data-stu-id="db31e-108">Copy the rows you want from one results grid to the other.</span></span>  
  
 <span data-ttu-id="db31e-109">在建立插入結果查詢時，您指定：</span><span class="sxs-lookup"><span data-stu-id="db31e-109">When you create an Insert Results query, you specify:</span></span>  
  
-   <span data-ttu-id="db31e-110">將資料列複製到其中的資料庫資料表 (目的資料表)。</span><span class="sxs-lookup"><span data-stu-id="db31e-110">The database table to copy rows to (the destination table).</span></span>  
  
-   <span data-ttu-id="db31e-111">從中複製資料列的一或多個資料表 (來源資料表)。</span><span class="sxs-lookup"><span data-stu-id="db31e-111">The table or tables to copy rows from (the source table).</span></span> <span data-ttu-id="db31e-112">這一或多個來源資料表會成為子查詢 (Subquery) 的一部份。</span><span class="sxs-lookup"><span data-stu-id="db31e-112">The source table or tables become part of a subquery.</span></span> <span data-ttu-id="db31e-113">如果您是在資料表中進行複製，來源資料表便與目的資料表相同。</span><span class="sxs-lookup"><span data-stu-id="db31e-113">If you are copying within a table, the source table is the same as the destination table.</span></span>  
  
-   <span data-ttu-id="db31e-114">要從中複製內容的來源資料表資料行。</span><span class="sxs-lookup"><span data-stu-id="db31e-114">The columns in the source table whose contents you want to copy.</span></span>  
  
-   <span data-ttu-id="db31e-115">將資料複製到其中的目標資料表目標資料行。</span><span class="sxs-lookup"><span data-stu-id="db31e-115">The target columns in the destination table to copy the data to.</span></span>  
  
-   <span data-ttu-id="db31e-116">搜尋條件，用來定義要複製的資料列。</span><span class="sxs-lookup"><span data-stu-id="db31e-116">Search conditions to define the rows you want to copy.</span></span>  
  
-   <span data-ttu-id="db31e-117">排序次序 (若要以特定次序複製資料列)。</span><span class="sxs-lookup"><span data-stu-id="db31e-117">Sort order, if you want to copy the rows in a particular order.</span></span>  
  
-   <span data-ttu-id="db31e-118">[群組依據] 選項 (如果只要複製摘要資訊)。</span><span class="sxs-lookup"><span data-stu-id="db31e-118">Group By options, if you want to copy only summary information.</span></span>  
  
 <span data-ttu-id="db31e-119">例如，下列查詢會將 `titles` 資料表的標題資訊複製到名稱為 `archivetitles`的封存資料表中。</span><span class="sxs-lookup"><span data-stu-id="db31e-119">For example, the following query copies title information from the `titles` table to an archive table called `archivetitles`.</span></span> <span data-ttu-id="db31e-120">此查詢會複製特定簽發者所屬全部標題的四個資料行內容：</span><span class="sxs-lookup"><span data-stu-id="db31e-120">The query copies the contents of four columns for all titles belonging to a particular publisher:</span></span>  
  
```  
INSERT INTO archivetitles   
   (title_id, title, type, pub_id)  
SELECT title_id, title, type, pub_id  
FROM titles  
WHERE (pub_id = '0766')  
```  
  
> [!NOTE]  
>  <span data-ttu-id="db31e-121">若要將值插入至新資料行，請使用插入值查詢 (Insert Value Query)。</span><span class="sxs-lookup"><span data-stu-id="db31e-121">To insert values into a new row, use an Insert Values query.</span></span>  
  
 <span data-ttu-id="db31e-122">您可以複製資料列中選取資料行的內容或所有資料行的內容。</span><span class="sxs-lookup"><span data-stu-id="db31e-122">You can copy the contents of selected columns or of all columns in a row.</span></span> <span data-ttu-id="db31e-123">不論是哪種情況，您複製的資料都必須與複製的目標資料列資料行相容。</span><span class="sxs-lookup"><span data-stu-id="db31e-123">In either case, the data you are copying must be compatible with the columns in the rows you are copying to.</span></span> <span data-ttu-id="db31e-124">例如，若要複製 `price`之類資料行的內容，複製的目標資料列資料行就必須接受含小數位數的數字資料。</span><span class="sxs-lookup"><span data-stu-id="db31e-124">For example, if you copy the contents of a column such as `price`, the column in the row you are copying to must accept numeric data with decimal places.</span></span> <span data-ttu-id="db31e-125">如果您要複製整個資料列，目的資料表與來源資料表的相對應欄位必須相容。</span><span class="sxs-lookup"><span data-stu-id="db31e-125">If you are copying an entire row, the destination table must have compatible columns in the same physical position as the source table.</span></span>  
  
 <span data-ttu-id="db31e-126">建立插入結果查詢時，[準則] 窗格將會變更，以反映可以用來複製資料的選項。</span><span class="sxs-lookup"><span data-stu-id="db31e-126">When you create an Insert Results query, the Criteria pane changes to reflect options available for copying data.</span></span> <span data-ttu-id="db31e-127">窗格中會加入一個 [附加] 欄位，供您指定複製資料的目標資料行。</span><span class="sxs-lookup"><span data-stu-id="db31e-127">An Append column is added to allow you to specify the columns into which data should be copied.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="db31e-128">插入結果查詢執行的動作無法恢復。</span><span class="sxs-lookup"><span data-stu-id="db31e-128">You cannot undo the action of executing an Insert Results query.</span></span> <span data-ttu-id="db31e-129">為安全起見，在執行查詢前請先備份資料。</span><span class="sxs-lookup"><span data-stu-id="db31e-129">As a precaution, back up your data before executing the query.</span></span>  
  
### <a name="to-create-an-insert-results-query"></a><span data-ttu-id="db31e-130">若要建立插入結果查詢</span><span class="sxs-lookup"><span data-stu-id="db31e-130">To create an Insert Results query</span></span>  
  
1.  <span data-ttu-id="db31e-131">建立新查詢，並加入您要從中複製資料列的資料表 (來源資料表)。</span><span class="sxs-lookup"><span data-stu-id="db31e-131">Create a new query and add the table from which you want to copy rows (the source table).</span></span> <span data-ttu-id="db31e-132">如果您是在資料表中複製資料列，您可以加入來源資料表做為目的資料表。</span><span class="sxs-lookup"><span data-stu-id="db31e-132">If you are copying rows within a table, you can add the source table as a destination table.</span></span>  
  
2.  <span data-ttu-id="db31e-133">在 [ **查詢設計工具** ] 功能表中指向 [ **變更類型**]，再按 [ **插入結果**]。</span><span class="sxs-lookup"><span data-stu-id="db31e-133">From the **Query Designer** menu, point to **Change Type**, and then click **Insert Results**.</span></span>  
  
3.  <span data-ttu-id="db31e-134">在 [選擇插入結果的目標資料表對話方塊](visual-database-tools.md)中，選取將資料列複製到其中的資料表 (目的資料表)。</span><span class="sxs-lookup"><span data-stu-id="db31e-134">In the [Choose Target Table for Insert Results Dialog Box](visual-database-tools.md), select the table to copy rows to (the destination table).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="db31e-135">[查詢和檢視設計師] 無法預先判斷您可以更新哪些資料表和檢視。</span><span class="sxs-lookup"><span data-stu-id="db31e-135">The Query and View Designer cannot determine in advance which tables and views you can update.</span></span> <span data-ttu-id="db31e-136">因此，[從查詢選擇要插入的資料表]  對話方塊的 [資料表名稱]  清單會顯示正在查詢之資料連接中的所有可用資料表和檢視，甚至包括您無法將資料列複製到其中的資料表和檢視。</span><span class="sxs-lookup"><span data-stu-id="db31e-136">Therefore, the **Table Name** list in the **Choose Table for Insert From Query** dialog box shows all available tables and views in the data connection you are querying, even those that you might not be able to copy rows to.</span></span>  
  
4.  <span data-ttu-id="db31e-137">在表示資料表或資料表值物件的矩形中，選擇您想複製內容的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="db31e-137">In the rectangle representing the table or table-valued object, choose the names of the columns whose contents you want to copy.</span></span> <span data-ttu-id="db31e-138">若要複製整個資料列，請選擇 [ \*\* \* (所有\*\*資料行]) 。</span><span class="sxs-lookup"><span data-stu-id="db31e-138">To copy entire rows, choose **\* (All Columns)**.</span></span>  
  
     <span data-ttu-id="db31e-139">查詢和檢視表設計工具會將您選擇的資料行新增至 [準則] 窗格的 [資料行]  欄位中。</span><span class="sxs-lookup"><span data-stu-id="db31e-139">The Query and View Designer adds the columns you choose to the **Column** column of the Criteriapane.</span></span>  
  
5.  <span data-ttu-id="db31e-140">在 [準則] 窗格的 [附加]  欄位中，在目的資料表中，為您要複製的每個資料行選取目標資料行。</span><span class="sxs-lookup"><span data-stu-id="db31e-140">In the **Append** column of the Criteria pane, select a target column in the destination table for each column you are copying.</span></span> <span data-ttu-id="db31e-141">如果您要複製整個資料列，請選擇\*tablename。 \* \*</span><span class="sxs-lookup"><span data-stu-id="db31e-141">Choose *tablename.\** if you are copying entire rows.</span></span> <span data-ttu-id="db31e-142">目的資料表的資料行必須與來源資料表的資料行具有相同 (或相容) 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="db31e-142">The columns in the destination table must have the same (or compatible) data types as the columns in the source table.</span></span>  
  
6.  <span data-ttu-id="db31e-143">若要以特定次序複製資料列，請指定排序次序。</span><span class="sxs-lookup"><span data-stu-id="db31e-143">If you want to copy rows in a particular order, specify a sort order.</span></span> <span data-ttu-id="db31e-144">如需詳細資訊，請參閱[排序及分組查詢結果 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="db31e-144">For details, see [Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md).</span></span>  
  
7.  <span data-ttu-id="db31e-145">在 [篩選條件]  欄位中輸入搜尋條件，以指定要複製的資料列。</span><span class="sxs-lookup"><span data-stu-id="db31e-145">Specify the rows to copy by entering search conditions in the **Filter** column.</span></span> <span data-ttu-id="db31e-146">如需詳細資訊，請參閱[指定搜尋準則 &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="db31e-146">For details, see [Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md).</span></span>  
  
     <span data-ttu-id="db31e-147">如果沒有指定搜尋條件，便會將來源資料表的所有資料列複製到目的資料表中。</span><span class="sxs-lookup"><span data-stu-id="db31e-147">If you do not specify a search condition, all rows from the source table will be copied to the destination table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="db31e-148">當將要搜尋的資料行加入至 [準則] 窗格時，[查詢和檢視設計師] 也會將它加入至要複製的資料行清單中。</span><span class="sxs-lookup"><span data-stu-id="db31e-148">When you add a column to search to the Criteria pane, the Query and View Designer also adds it to the list of columns to copy.</span></span> <span data-ttu-id="db31e-149">如果想使用某一資料行進行搜尋但不想複製它，請在代表資料表或資料表值物件的矩形中，清除資料行名稱旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="db31e-149">If you want to use a column for searching but not copy it, clear the check box next to the column name in the rectangle representing the table or table-valued object.</span></span>  
  
8.  <span data-ttu-id="db31e-150">若要複製摘要資訊，請指定 [群組依據] 選項。</span><span class="sxs-lookup"><span data-stu-id="db31e-150">If you want to copy summary information, specify Group By options.</span></span> <span data-ttu-id="db31e-151">如需詳細資訊，請參閱[摘要查詢結果 &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="db31e-151">For details, see [Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="db31e-152">在執行插入結果查詢時， [結果窗格](results-pane-visual-database-tools.md)中不會報告結果，</span><span class="sxs-lookup"><span data-stu-id="db31e-152">When you execute an Insert Results query, no results are reported in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="db31e-153">而是出現訊息指出已經複製了多少資料列。</span><span class="sxs-lookup"><span data-stu-id="db31e-153">Instead, a message appears indicating how many rows were copied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db31e-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db31e-154">See Also</span></span>  
 <span data-ttu-id="db31e-155">[&#40;Visual Database Tools&#41;的查詢類型](types-of-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="db31e-155">[Types of Queries &#40;Visual Database Tools&#41;](types-of-queries-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="db31e-156">設計查詢和檢視使用說明主題 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="db31e-156">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
