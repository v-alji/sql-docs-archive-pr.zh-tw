---
title: 互動式排序 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 00cafed5-1a3c-4ce0-a1fb-ff1e2613f495
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 92f8a63ebd3d16c84dc12bb4a08549efa91e949a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707102"
---
# <a name="interactive-sort-report-builder-and-ssrs"></a><span data-ttu-id="f7f07-102">互動式排序 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f7f07-102">Interactive Sort (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f7f07-103">您可以加入互動式排序按鈕，讓使用者在資料表中切換資料列的遞增和遞減順序，或在矩陣中切換資料列及資料行的遞增和遞減順序。</span><span class="sxs-lookup"><span data-stu-id="f7f07-103">You can add interactive sort buttons to enable a user to toggle between ascending and descending order for rows in a table or for rows and columns in a matrix.</span></span> <span data-ttu-id="f7f07-104">互動式排序的常見用法為，將排序按鈕加入到每個資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="f7f07-104">The most common use of interactive sort is to add a sort button to every column header.</span></span> <span data-ttu-id="f7f07-105">接著，使用者可以選擇排序所依據的資料行。</span><span class="sxs-lookup"><span data-stu-id="f7f07-105">The user can then choose which column to sort by.</span></span>  
  
 <span data-ttu-id="f7f07-106">不過，您可以將互動式排序按鈕加入到任何文字方塊，而不只是資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="f7f07-106">However, you can add an interactive sort button to any text box, not just column headers.</span></span> <span data-ttu-id="f7f07-107">例如，對於資料列群組外之資料列中的文字方塊，您可以針對父群組資料列或資料行、子群組資料列或資料行，或詳細資料列或資料行指定排序。</span><span class="sxs-lookup"><span data-stu-id="f7f07-107">For example, for a text box in a row outside a row group, you can specify a sort for the parent group rows or columns, for child group rows or columns, or for the detail rows or columns.</span></span> <span data-ttu-id="f7f07-108">也可以將欄位結合成一個單一的群組運算式，然後依多個欄位進行排序。</span><span class="sxs-lookup"><span data-stu-id="f7f07-108">You can also combine fields into a single group expression, and then sort by multiple fields.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="f7f07-109">當您加入互動式排序時，必須指定下列項目：</span><span class="sxs-lookup"><span data-stu-id="f7f07-109">When you add an interactive sort, you must specify the following items:</span></span>  
  
-   <span data-ttu-id="f7f07-110">**要排序的項目：** 資料列或資料行？</span><span class="sxs-lookup"><span data-stu-id="f7f07-110">**What to sort:** Rows or columns?</span></span>  
  
-   <span data-ttu-id="f7f07-111">**排序的依據：** 顯示在資料表資料行中的欄位？</span><span class="sxs-lookup"><span data-stu-id="f7f07-111">**What to sort by:** A field that is displayed in a table column?</span></span> <span data-ttu-id="f7f07-112">未顯示的欄位？</span><span class="sxs-lookup"><span data-stu-id="f7f07-112">A field that is not displayed?</span></span>  
  
-   <span data-ttu-id="f7f07-113">**要排序的內容：** 例如，您可以針對下列項目進行排序：與資料列群組相關聯的資料列、與資料行群組相關聯的資料行、詳細資料列、父群組內的子群組，或是父群組和子群組一起。</span><span class="sxs-lookup"><span data-stu-id="f7f07-113">**What context to sort in:** For example, you can sort on rows associated with row groups; columns associated with column groups; detail rows; child groups within a parent group; or parent and child group together.</span></span>  
  
-   <span data-ttu-id="f7f07-114">**要加入排序按鈕的文字方塊：** 在資料行標頭或群組資料列標頭？</span><span class="sxs-lookup"><span data-stu-id="f7f07-114">**Which text box to add the sort button to:** In the column header or in the group row header?</span></span>  
  
-   <span data-ttu-id="f7f07-115">**是否要同步處理多個資料區的排序：** 您可以設計一份報表，讓使用者切換排序次序時，也排序具有相同上階的其他資料區。</span><span class="sxs-lookup"><span data-stu-id="f7f07-115">**Whether to synchronize the sort for multiple data regions:** You can design a report so that when the user toggles the sort order, other data regions with the same ancestor also sort.</span></span>  
  
 <span data-ttu-id="f7f07-116">如需逐步指示，請參閱 [將互動式排序加入至資料表或矩陣 &#40;報表產生器及 SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md)(將互動式排序加入資料表或矩陣 (報表產生器及 SSRS))。</span><span class="sxs-lookup"><span data-stu-id="f7f07-116">For step-by-step instructions, see [Add Interactive Sort to a Table or Matrix &#40;Report Builder and SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="f7f07-117">下表摘要說明您可以使用互動式排序按鈕達到的效果。</span><span class="sxs-lookup"><span data-stu-id="f7f07-117">The following table summarizes the effects you can achieve by using interactive sort buttons.</span></span>  
  
|<span data-ttu-id="f7f07-118">動作</span><span class="sxs-lookup"><span data-stu-id="f7f07-118">Action</span></span>|<span data-ttu-id="f7f07-119">要排序的項目</span><span class="sxs-lookup"><span data-stu-id="f7f07-119">What to sort</span></span>|<span data-ttu-id="f7f07-120">要加入排序按鈕的位置</span><span class="sxs-lookup"><span data-stu-id="f7f07-120">Where to add the sort button</span></span>|<span data-ttu-id="f7f07-121">排序依據的項目</span><span class="sxs-lookup"><span data-stu-id="f7f07-121">What to sort on</span></span>|<span data-ttu-id="f7f07-122">排序範圍</span><span class="sxs-lookup"><span data-stu-id="f7f07-122">Sort scope</span></span>|  
|------------|------------------|----------------------------------|---------------------|----------------|  
|<span data-ttu-id="f7f07-123">排序沒有群組之資料表的詳細資料列</span><span class="sxs-lookup"><span data-stu-id="f7f07-123">Sort detail rows for a table with no groups</span></span>|<span data-ttu-id="f7f07-124">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f7f07-124">Details</span></span>|<span data-ttu-id="f7f07-125">資料行標頭</span><span class="sxs-lookup"><span data-stu-id="f7f07-125">Column header</span></span>|<span data-ttu-id="f7f07-126">繫結至此資料行的資料集欄位</span><span class="sxs-lookup"><span data-stu-id="f7f07-126">Dataset field bound to this column</span></span>|<span data-ttu-id="f7f07-127">資料區域</span><span class="sxs-lookup"><span data-stu-id="f7f07-127">Data region</span></span>|  
|<span data-ttu-id="f7f07-128">排序矩陣的最上層群組執行個體</span><span class="sxs-lookup"><span data-stu-id="f7f07-128">Sort top-level group instances for a matrix</span></span>|<span data-ttu-id="f7f07-129">群組</span><span class="sxs-lookup"><span data-stu-id="f7f07-129">Groups</span></span>|<span data-ttu-id="f7f07-130">資料行標頭</span><span class="sxs-lookup"><span data-stu-id="f7f07-130">Column header</span></span>|<span data-ttu-id="f7f07-131">父群組的群組運算式</span><span class="sxs-lookup"><span data-stu-id="f7f07-131">Group expression for parent group</span></span>|<span data-ttu-id="f7f07-132">資料區域</span><span class="sxs-lookup"><span data-stu-id="f7f07-132">Data region</span></span>|  
|<span data-ttu-id="f7f07-133">排序資料表中子群組的詳細資料列</span><span class="sxs-lookup"><span data-stu-id="f7f07-133">Sort detail rows for a child group in a table</span></span>|<span data-ttu-id="f7f07-134">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f7f07-134">Details</span></span>|<span data-ttu-id="f7f07-135">子群組標題資料列</span><span class="sxs-lookup"><span data-stu-id="f7f07-135">Child group header row</span></span>|<span data-ttu-id="f7f07-136">排序依據的資料集欄位</span><span class="sxs-lookup"><span data-stu-id="f7f07-136">Dataset field to sort by</span></span>|<span data-ttu-id="f7f07-137">子群組</span><span class="sxs-lookup"><span data-stu-id="f7f07-137">Child group</span></span>|  
|<span data-ttu-id="f7f07-138">排序資料表中多個資料列群組和詳細資料列的資料列</span><span class="sxs-lookup"><span data-stu-id="f7f07-138">Sort rows for multiple row groups and detail rows in a table</span></span>|<span data-ttu-id="f7f07-139">群組，但是您必須重新定義群組運算式</span><span class="sxs-lookup"><span data-stu-id="f7f07-139">Groups, but you must redefine the group expression</span></span>|<span data-ttu-id="f7f07-140">資料行標頭</span><span class="sxs-lookup"><span data-stu-id="f7f07-140">Column header</span></span>|<span data-ttu-id="f7f07-141">排序依據之資料集欄位的彙總</span><span class="sxs-lookup"><span data-stu-id="f7f07-141">Aggregate of dataset field to sort by</span></span>|<span data-ttu-id="f7f07-142">資料區域</span><span class="sxs-lookup"><span data-stu-id="f7f07-142">Data region</span></span>|  
|<span data-ttu-id="f7f07-143">同步處理多個資料區域的排序次序</span><span class="sxs-lookup"><span data-stu-id="f7f07-143">Synchronize the sort order for multiple data regions</span></span>|<span data-ttu-id="f7f07-144">群組</span><span class="sxs-lookup"><span data-stu-id="f7f07-144">Groups</span></span>|<span data-ttu-id="f7f07-145">通常是資料行標頭</span><span class="sxs-lookup"><span data-stu-id="f7f07-145">Typically, column header</span></span>|<span data-ttu-id="f7f07-146">群組運算式</span><span class="sxs-lookup"><span data-stu-id="f7f07-146">Group expression</span></span>|<span data-ttu-id="f7f07-147">資料集</span><span class="sxs-lookup"><span data-stu-id="f7f07-147">Dataset</span></span>|  
  
 <span data-ttu-id="f7f07-148">報表處理器會在套用所有資料區域和群組排序運算式之後，套用互動式排序。</span><span class="sxs-lookup"><span data-stu-id="f7f07-148">The report processor applies interactive sort after all data region and group sort expressions are applied.</span></span> <span data-ttu-id="f7f07-149">如需詳細資訊，請參閱 [篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)(將互動式排序加入資料表或矩陣 (報表產生器及 SSRS))。</span><span class="sxs-lookup"><span data-stu-id="f7f07-149">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
## <a name="adding-interactive-sort-for-multiple-groups"></a><span data-ttu-id="f7f07-150">加入多個群組的互動式排序</span><span class="sxs-lookup"><span data-stu-id="f7f07-150">Adding Interactive Sort for Multiple Groups</span></span>  
 <span data-ttu-id="f7f07-151">在每個以單一資料集欄位為基礎之巢狀資料列群組的資料表中，您可以加入互動式排序按鈕，排序父群組值、子群組值或詳細資料列。</span><span class="sxs-lookup"><span data-stu-id="f7f07-151">In a table with nested row groups each based on a single dataset field, you can add an interactive sort button that sorts parent group values, child group values, or detail rows.</span></span> <span data-ttu-id="f7f07-152">不過，您可能想要讓使用者能夠同時依父群組值和子群組值排序資料表，而不必按滑鼠多次。</span><span class="sxs-lookup"><span data-stu-id="f7f07-152">However, you might want to provide the user with the ability to sort the table by both the parent and child group values without having to click multiple times.</span></span>  
  
 <span data-ttu-id="f7f07-153">若要這樣做，您必須重新設計資料表，以便針對結合多個欄位的運算式分組。</span><span class="sxs-lookup"><span data-stu-id="f7f07-153">To do this, you must redesign the table to group on an expression that combines multiple fields.</span></span> <span data-ttu-id="f7f07-154">例如，對於包含存貨計數的資料集，如果原始資料表先依大小，然後依色彩分組，您可以利用結合大小和色彩的群組運算式指定單一群組。</span><span class="sxs-lookup"><span data-stu-id="f7f07-154">For example, for a dataset with inventory counts, if the original table grouped by size and then by color, you can specify a single group with a group expression that is a combination of size and color.</span></span> <span data-ttu-id="f7f07-155">如需詳細資訊，請參閱 [將互動式排序加入至資料表或矩陣 &#40;報表產生器及 SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md)(將互動式排序加入資料表或矩陣 (報表產生器及 SSRS))。</span><span class="sxs-lookup"><span data-stu-id="f7f07-155">For more information, see [Add Interactive Sort to a Table or Matrix &#40;Report Builder and SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7f07-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7f07-156">See Also</span></span>  
 <span data-ttu-id="f7f07-157">[在資料區中排序資料 &#40;報表產生器及 SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f7f07-157">[Sort Data in a Data Region &#40;Report Builder and SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f7f07-158">[篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f7f07-158">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f7f07-159">將互動式排序加入至資料表或矩陣 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f7f07-159">Add Interactive Sort to a Table or Matrix &#40;Report Builder and SSRS&#41;</span></span>](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md)  
  
  
