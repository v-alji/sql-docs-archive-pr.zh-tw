---
title: 建立更新查詢 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- tables [SQL Server], updating
- queries [SQL Server], types
- Update query
- updating tables
ms.assetid: 178b7b75-8078-4e61-b2a8-4719b9d8033d
author: stevestein
ms.author: sstein
ms.openlocfilehash: bbea575d544875dba73de923474cc11bbcb46a9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596991"
---
# <a name="create-update-queries-visual-database-tools"></a><span data-ttu-id="5a156-102">建立更新查詢 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="5a156-102">Create Update Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="5a156-103">您可以使用更新查詢，在一次作業中變更多個資料列的內容。</span><span class="sxs-lookup"><span data-stu-id="5a156-103">You can change the contents of multiple rows in one operation by using an Update query.</span></span> <span data-ttu-id="5a156-104">例如，在 `titles` 資料表中，您可以使用更新查詢，將特定發行者所有書籍的價格增加 10%。</span><span class="sxs-lookup"><span data-stu-id="5a156-104">For example, in a `titles` table you can use an Update query to add 10% to the price of all books for a particular publisher.</span></span>  
  
 <span data-ttu-id="5a156-105">在建立更新查詢時，您指定：</span><span class="sxs-lookup"><span data-stu-id="5a156-105">When you create an Update query, you specify:</span></span>  
  
-   <span data-ttu-id="5a156-106">要更新的資料表。</span><span class="sxs-lookup"><span data-stu-id="5a156-106">The table to update.</span></span>  
  
-   <span data-ttu-id="5a156-107">要更新內容的資料行。</span><span class="sxs-lookup"><span data-stu-id="5a156-107">The columns whose contents you want to update.</span></span>  
  
-   <span data-ttu-id="5a156-108">用來更新個別資料行的值或運算式。</span><span class="sxs-lookup"><span data-stu-id="5a156-108">The value or expression to use to update the individual columns.</span></span>  
  
-   <span data-ttu-id="5a156-109">定義要更新資料列的搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="5a156-109">Search conditions to define the rows you want to update.</span></span>  
  
 <span data-ttu-id="5a156-110">例如，下列查詢會更新 `titles` 資料表，將一個發行者所有書籍的價格增加 10%：</span><span class="sxs-lookup"><span data-stu-id="5a156-110">For example, the following query updates the `titles` table by adding 10% to the price of all titles for one publisher:</span></span>  
  
```  
UPDATE titles  
SET price = price * 1.1  
WHERE (pub_id = '0766')  
```  
  
> [!CAUTION]  
>  <span data-ttu-id="5a156-111">更新查詢執行的動作無法恢復。</span><span class="sxs-lookup"><span data-stu-id="5a156-111">You cannot undo the action of executing an Update query.</span></span> <span data-ttu-id="5a156-112">為安全起見，在執行查詢前請先備份資料。</span><span class="sxs-lookup"><span data-stu-id="5a156-112">As a precaution, back up your data before executing the query.</span></span>  
  
### <a name="to-create-an-update-query"></a><span data-ttu-id="5a156-113">若要建立更新查詢</span><span class="sxs-lookup"><span data-stu-id="5a156-113">To create an Update query</span></span>  
  
1.  <span data-ttu-id="5a156-114">將要更新的資料表加入至 [圖表] 窗格。</span><span class="sxs-lookup"><span data-stu-id="5a156-114">Add the table you want to update to the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="5a156-115">從 [查詢設計工具]  功能表中，指向 [變更類型]  ，然後按一下 [更新]  。</span><span class="sxs-lookup"><span data-stu-id="5a156-115">From the **Query Designer** menu point to **Change Type**, and then click **Update**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5a156-116">在啟動更新查詢時，如果 [圖表] 窗格中顯示一個以上的資料表，查詢和檢視表設計工具會顯示[選擇插入值的目標資料表對話方塊](visual-database-tools.md)，以詢問要更新的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="5a156-116">If more than one table is displayed in the Diagram pane when you start the Update query, the Query and View Designer displays the [Choose Target Table for Insert Values Dialog Box](visual-database-tools.md) to prompt you for the name of the table to update.</span></span>  
  
3.  <span data-ttu-id="5a156-117">在 [圖表] 窗格中，按一下要提供新值之各資料行的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5a156-117">In the Diagram pane, click the check box for each column for which you want to supply new values.</span></span> <span data-ttu-id="5a156-118">這些資料行將顯示在 [準則] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="5a156-118">Those columns will show in the Criteria pane.</span></span> <span data-ttu-id="5a156-119">只有加入查詢中的資料行才會更新。</span><span class="sxs-lookup"><span data-stu-id="5a156-119">Columns will be updated only if you add them to the query.</span></span>  
  
4.  <span data-ttu-id="5a156-120">在 [準則] 窗格的 [新值]  資料行中，輸入資料行的更新值。</span><span class="sxs-lookup"><span data-stu-id="5a156-120">In the **New Value** column of the Criteria pane, enter the update value for the column.</span></span> <span data-ttu-id="5a156-121">您可輸入常值、資料行名稱或運算式。</span><span class="sxs-lookup"><span data-stu-id="5a156-121">You can enter literal values, column names, or expressions.</span></span> <span data-ttu-id="5a156-122">該值必須符合 (或相容於) 正在更新之資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="5a156-122">The value must match (or be compatible with) the data type of the column you are updating.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="5a156-123">[查詢和檢視設計師] 不會檢查值是否符合所更新資料行的長度。</span><span class="sxs-lookup"><span data-stu-id="5a156-123">The Query and View Designer cannot check that a value fits within the length of the column you are updating.</span></span> <span data-ttu-id="5a156-124">如果提供的值太長，它可能會無預警地被截斷。</span><span class="sxs-lookup"><span data-stu-id="5a156-124">If you provide a value that is too long, it might be truncated without warning.</span></span> <span data-ttu-id="5a156-125">例如，如果 `name` 資料行的長度是 20 個字元，但是您指定 25 個字元的更新值，則最後 5 個字元可能會被截斷。</span><span class="sxs-lookup"><span data-stu-id="5a156-125">For example, if a `name` column is 20 characters long but you specify an update value of 25 characters, the last 5 characters might be truncated.</span></span>  
  
5.  <span data-ttu-id="5a156-126">在 [篩選條件]  資料行中輸入搜尋條件，以定義要更新的資料列。</span><span class="sxs-lookup"><span data-stu-id="5a156-126">Define the rows to update by entering search conditions in the **Filter** column.</span></span> <span data-ttu-id="5a156-127">如需詳細資訊，請參閱[指定搜尋準則 &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="5a156-127">For details, see [Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md).</span></span>  
  
     <span data-ttu-id="5a156-128">如果不指定搜尋條件，則指定資料表中的所有資料列會更新。</span><span class="sxs-lookup"><span data-stu-id="5a156-128">If you do not specify a search condition, all rows in the specified table will be updated.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5a156-129">在資料行加入至 [準則] 窗格以做為搜尋條件時，[查詢和檢視設計師] 也會將其加入至要更新的資料行清單中。</span><span class="sxs-lookup"><span data-stu-id="5a156-129">When you add a column to the Criteria pane for use in a search condition, the Query and View Designer also adds it to the list of columns to be updated.</span></span> <span data-ttu-id="5a156-130">如果想使用資料行做為搜尋條件但不想更新它，請在代表資料表或資料表值物件的矩形中，清除資料行名稱旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5a156-130">If you want to use a column for a search condition but not update it, clear the check box next to the column name in the rectangle representing the table or table-valued object.</span></span>  
  
 <span data-ttu-id="5a156-131">當執行更新查詢時， [結果窗格](results-pane-visual-database-tools.md)不會報告結果。</span><span class="sxs-lookup"><span data-stu-id="5a156-131">When you execute an Update query, no results are reported in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="5a156-132">而是出現訊息指出已經變更了多少資料列。</span><span class="sxs-lookup"><span data-stu-id="5a156-132">Instead, a message appears indicating how many rows were changed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a156-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a156-133">See Also</span></span>  
 <span data-ttu-id="5a156-134">[支援的查詢類型 &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="5a156-134">[Supported Query Types &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md) </span></span>  
 <span data-ttu-id="5a156-135">[設計查詢和觀看 how to 主題 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="5a156-135">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="5a156-136">使用查詢執行基本作業 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="5a156-136">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
