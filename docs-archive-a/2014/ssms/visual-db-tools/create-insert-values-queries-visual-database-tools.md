---
title: 建立插入值查詢 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting values
- queries [SQL Server], types
- adding values
- row additions [SQL Server], Insert Values query
- inserting rows
- Insert Values query
- adding rows
- table values [SQL Server]
ms.assetid: 2d4b2f6d-cc09-434b-8a0e-ccce40628064
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2fc71b0148ee8a7e92c517fe75b56c329b3c88f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699112"
---
# <a name="create-insert-values-queries-visual-database-tools"></a><span data-ttu-id="bf87a-102">建立插入值查詢 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="bf87a-102">Create Insert Values Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="bf87a-103">您可使用 [插入值] 查詢在目前的資料表中建立新資料列。</span><span class="sxs-lookup"><span data-stu-id="bf87a-103">You can create a new row in the current table using an Insert Values query.</span></span> <span data-ttu-id="bf87a-104">當建立 [插入值] 查詢時，您指定：</span><span class="sxs-lookup"><span data-stu-id="bf87a-104">When you create an Insert Values query, you specify:</span></span>  
  
-   <span data-ttu-id="bf87a-105">要加入資料列的資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="bf87a-105">The database table to add the row to.</span></span>  
  
-   <span data-ttu-id="bf87a-106">要加入內容的資料行。</span><span class="sxs-lookup"><span data-stu-id="bf87a-106">The columns whose contents you want to add.</span></span>  
  
-   <span data-ttu-id="bf87a-107">用來插入至個別資料行的值或運算式。</span><span class="sxs-lookup"><span data-stu-id="bf87a-107">The value or expression to insert into the individual columns.</span></span>  
  
 <span data-ttu-id="bf87a-108">例如，下列查詢會將資料列加入至 `titles` 資料表，同時指定標題，類型，發行者和價格的值：</span><span class="sxs-lookup"><span data-stu-id="bf87a-108">For example, the following query adds a row to the `titles` table, specifying values for the title, type, publisher, and price:</span></span>  
  
```  
INSERT INTO titles  
         (title_id, title, type, pub_id, price)  
VALUES   ('BU9876', 'Creating Web Pages', 'business', '1389', '29.99')  
```  
  
 <span data-ttu-id="bf87a-109">當建立 [插入值] 查詢時，[準則] 窗格會變更以反映插入新資料列僅只使用的選項：資料行名稱與要插入的值。</span><span class="sxs-lookup"><span data-stu-id="bf87a-109">When you create an Insert Values query, the Criteria pane changes to reflect the only options available for inserting a new row: the column name and the value to insert.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="bf87a-110">[插入值] 查詢執行的動作無法恢復。</span><span class="sxs-lookup"><span data-stu-id="bf87a-110">You cannot undo the action of executing an Insert Values query.</span></span> <span data-ttu-id="bf87a-111">為安全起見，在執行查詢前請先備份資料。</span><span class="sxs-lookup"><span data-stu-id="bf87a-111">As a precaution, back up your data before executing the query.</span></span>  
  
### <a name="to-create-an-insert-values-query"></a><span data-ttu-id="bf87a-112">若要建立 [插入值] 查詢</span><span class="sxs-lookup"><span data-stu-id="bf87a-112">To create an Insert Values query</span></span>  
  
1.  <span data-ttu-id="bf87a-113">將要更新的資料表加入至 [圖表] 窗格。</span><span class="sxs-lookup"><span data-stu-id="bf87a-113">Add the table you want to update to the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="bf87a-114">在 [查詢設計工具]  功能表中指向 [變更類型]  ，然後按一下 [插入值]  。</span><span class="sxs-lookup"><span data-stu-id="bf87a-114">From the **Query Designer** menu point to **Change Type**, and then click **Insert Values**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bf87a-115">當啟動 [插入值] 查詢時，[圖表] 窗格中若顯示一個以上之資料表，[查詢和檢視表設計工具] 會顯示[選擇插入值的目標資料表對話方塊](visual-database-tools.md)，詢問要更新的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="bf87a-115">If more than one table is displayed in the Diagram pane when you start the Insert Values query, the Query and View Designer displays the [Choose Target Table for Insert Values Dialog Box](visual-database-tools.md) to prompt you for the name of the table to update.</span></span>  
  
3.  <span data-ttu-id="bf87a-116">在 [圖表] 窗格中，按一下要提供新值之各資料行的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="bf87a-116">In the Diagram pane, click the check box for each column for which you want to supply new values.</span></span> <span data-ttu-id="bf87a-117">這些資料行將顯示在 [準則] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="bf87a-117">Those columns will show in the Criteria pane.</span></span> <span data-ttu-id="bf87a-118">只有加入查詢中的資料行才會更新。</span><span class="sxs-lookup"><span data-stu-id="bf87a-118">Columns will be updated only if you add them to the query.</span></span>  
  
4.  <span data-ttu-id="bf87a-119">在 [準則] 窗格之 [新值]  資料行中，輸入資料行的新值。</span><span class="sxs-lookup"><span data-stu-id="bf87a-119">In the **New Value** column of the Criteria pane, enter the new value for the column.</span></span> <span data-ttu-id="bf87a-120">您可輸入常值、資料行名稱或運算式。</span><span class="sxs-lookup"><span data-stu-id="bf87a-120">You can enter literal values, column names, or expressions.</span></span> <span data-ttu-id="bf87a-121">該值必須符合 (或相容於) 正在更新之資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="bf87a-121">The value must match (or be compatible with) the data type of the column you are updating.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="bf87a-122">查詢和檢視設計師不會檢查值是否符合要插入之資料行的長度。</span><span class="sxs-lookup"><span data-stu-id="bf87a-122">The Query and View Designer cannot check that a value fits within the length of the column you are inserting.</span></span> <span data-ttu-id="bf87a-123">如果提供的值太長，它可能會無預警地被截斷。</span><span class="sxs-lookup"><span data-stu-id="bf87a-123">If you provide a value that is too long, it might be truncated without warning.</span></span> <span data-ttu-id="bf87a-124">例如，如果 `name` 資料行的長度是 20 個字元，但是您指定了 25 個字元的插入值，最後 5 個字元可能會被截斷。</span><span class="sxs-lookup"><span data-stu-id="bf87a-124">For example, if a `name` column is 20 characters long but you specify an insert value of 25 characters, the last 5 characters might be truncated.</span></span>  
  
 <span data-ttu-id="bf87a-125">當執行 [插入值] 查詢時， [結果窗格](results-pane-visual-database-tools.md)不會報告結果。</span><span class="sxs-lookup"><span data-stu-id="bf87a-125">When you execute an Insert Values query, no results are reported in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="bf87a-126">而是出現訊息指出已經變更了多少資料列。</span><span class="sxs-lookup"><span data-stu-id="bf87a-126">Instead, a message appears indicating how many rows were changed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf87a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf87a-127">See Also</span></span>  
 <span data-ttu-id="bf87a-128">[支援的查詢類型 &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="bf87a-128">[Supported Query Types &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md) </span></span>  
 <span data-ttu-id="bf87a-129">[設計查詢和觀看 how to 主題 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="bf87a-129">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="bf87a-130">使用查詢執行基本作業 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="bf87a-130">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
