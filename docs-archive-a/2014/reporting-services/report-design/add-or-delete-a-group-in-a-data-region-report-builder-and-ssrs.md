---
title: 在資料區中新增或刪除群組 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4de53c3c-c6fc-49ce-b692-3609fc0b3ec5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c355ca87db578d47181935e1ca6bc48e75bf8b8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703878"
---
# <a name="add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs"></a><span data-ttu-id="947af-102">在資料區中加入或刪除群組 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="947af-102">Add or Delete a Group in a Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="947af-103">當您想要針對顯示和計算，依特定值或特定一組運算式組織資料時，將群組加入至資料區。</span><span class="sxs-lookup"><span data-stu-id="947af-103">Add a group to a data region when you want to organize data by a specific value or set of expressions, for display and calculations.</span></span> <span data-ttu-id="947af-104">每個群組都有一個名稱和一個運算式，識別資料集中的哪個資料屬於群組。</span><span class="sxs-lookup"><span data-stu-id="947af-104">A group has a name and an expression that identifies which data from a dataset belongs to the group.</span></span> <span data-ttu-id="947af-105">如需群組的詳細資訊，請參閱 [了解群組 &#40;報表產生器及 SSRS&#41;](understanding-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="947af-105">For more information about groups, see [Understanding Groups &#40;Report Builder and SSRS&#41;](understanding-groups-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="947af-106">在 Tablix 資料區中，按一下資料表、矩陣或清單來顯示 [群組] 窗格。</span><span class="sxs-lookup"><span data-stu-id="947af-106">In a tablix data region, click in the table, matrix, or list to display the Grouping pane.</span></span> <span data-ttu-id="947af-107">將資料集欄位拖曳到 [資料列群組] 和 [資料行群組] 窗格以建立父群組或子群組。</span><span class="sxs-lookup"><span data-stu-id="947af-107">Drag dataset fields to the Row Group and Column Group pane to create parent or child groups.</span></span> <span data-ttu-id="947af-108">以滑鼠右鍵按一下現有的群組即可加入相鄰的群組。</span><span class="sxs-lookup"><span data-stu-id="947af-108">Right-click an existing group to add an adjacent group.</span></span> <span data-ttu-id="947af-109">根據定義，詳細資料群組是最內部的群組，而且僅能當做子群組加入。</span><span class="sxs-lookup"><span data-stu-id="947af-109">By definition, the details group is the innermost group and can only be added as a child group.</span></span> <span data-ttu-id="947af-110">以滑鼠右鍵按一下現有的群組即可刪除該群組。</span><span class="sxs-lookup"><span data-stu-id="947af-110">Right-click an existing group to delete it.</span></span> <span data-ttu-id="947af-111">系統會為您自動加入用於顯示群組值的資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="947af-111">Rows and columns on which to display group values are automatically added for you.</span></span> <span data-ttu-id="947af-112">如需詳細資訊，請參閱 [資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="947af-112">For more information, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="947af-113">在 [圖表] 資料區域中，按一下圖表來顯示放置區。</span><span class="sxs-lookup"><span data-stu-id="947af-113">In a Chart data region, click in the chart to display the drop-zones.</span></span> <span data-ttu-id="947af-114">將資料集欄位拖曳到類別目錄和數列放置區，藉以建立群組。</span><span class="sxs-lookup"><span data-stu-id="947af-114">Create groups by dragging dataset fields to the category and series drop zones.</span></span> <span data-ttu-id="947af-115">若要加入巢狀群組，將多個欄位加入至放置區。</span><span class="sxs-lookup"><span data-stu-id="947af-115">To add nested groups, add multiple fields to the drop-zone.</span></span>  
  
 <span data-ttu-id="947af-116">依預設，在量測計中不會定義群組。</span><span class="sxs-lookup"><span data-stu-id="947af-116">Groups are not defined in a gauge by default.</span></span> <span data-ttu-id="947af-117">量測計的預設行為是將指定之欄位中的所有值彙總為量測計上顯示的一個值。</span><span class="sxs-lookup"><span data-stu-id="947af-117">The default behavior for the gauge is to aggregate all values in the specified field into one value that is displayed on the gauge.</span></span> <span data-ttu-id="947af-118">如需詳細資訊，請參閱 [量測計 &#40;報表產生器及 SSRS&#41;](gauges-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="947af-118">For more information, see [Gauges &#40;Report Builder and SSRS&#41;](gauges-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-parent-or-child-row-or-column-group-to-a-tablix-data-region"></a><span data-ttu-id="947af-119">若要將父或子資料列或資料行群組加入到 Tablix 資料區</span><span class="sxs-lookup"><span data-stu-id="947af-119">To add a parent or child row or column group to a tablix data region</span></span>  
  
1.  <span data-ttu-id="947af-120">將欄位從 **[報表資料]** 窗格拖曳到 **[資料列群組]** 窗格或 **[資料行群組]** 窗格。</span><span class="sxs-lookup"><span data-stu-id="947af-120">Drag a field from the **Report Data** pane to the **Row Groups** pane or the **Column Groups** pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="947af-121">如果沒有看到 [群組] 窗格，請按一下 [檢視] 索引標籤上的 [群組]  。</span><span class="sxs-lookup"><span data-stu-id="947af-121">If you do not see the Grouping pane, on the View tab, click **Grouping**.</span></span>  
  
2.  <span data-ttu-id="947af-122">使用導覽列將欄位放在群組階層之上或之下，以便將群組當做父群組或子群組放到現有的群組中。</span><span class="sxs-lookup"><span data-stu-id="947af-122">Drop the field above or below the group hierarchy using the guide bar to place the group as a parent group or a child group to an existing group.</span></span>  
  
     <span data-ttu-id="947af-123">此群組會使用預設名稱、群組運算式以及以欄位名稱為基礎的排序運算式加入。</span><span class="sxs-lookup"><span data-stu-id="947af-123">The group is added with a default name, group expression, and sort expression that is based on the field name.</span></span>  
  
### <a name="to-add-an-adjacent-row-or-column-group-to-a-tablix-data-region"></a><span data-ttu-id="947af-124">若要將相鄰的資料列或資料行群組加入到 Tablix 資料區</span><span class="sxs-lookup"><span data-stu-id="947af-124">To add an adjacent row or column group to a tablix data region</span></span>  
  
1.  <span data-ttu-id="947af-125">在 [群組] 窗格中，以滑鼠右鍵按一下與您想要加入之群組對等的群組。</span><span class="sxs-lookup"><span data-stu-id="947af-125">In the Grouping pane, right-click a group that is a peer to the group that you want to add.</span></span> <span data-ttu-id="947af-126">按一下 **[加入群組]** ，然後按一下 **[前方相鄰]** 或 **[後方相鄰]** 來指定要加入群組的位置。</span><span class="sxs-lookup"><span data-stu-id="947af-126">Click **Add Group**, and then click **Adjacent Before** or **Adjacent After** to specify where to add the group.</span></span> <span data-ttu-id="947af-127">**[Tablix 群組]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="947af-127">The **Tablix Group** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="947af-128">在 **[名稱]** 中，輸入群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="947af-128">In **Name**, type a name for the group.</span></span>  
  
3.  <span data-ttu-id="947af-129">在 [群組運算式]  中鍵入運算式，或按一下運算式按鈕 (**fx**) 建立運算式。</span><span class="sxs-lookup"><span data-stu-id="947af-129">In **Group expression**, type an expression or click the expression button (**fx**) to create an expression.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="947af-130">此時會將新群組加入到 [群組] 窗格中，並將在其中顯示群組值的資料列或資料行加入到設計介面的 Tablix 資料區中。</span><span class="sxs-lookup"><span data-stu-id="947af-130">A new group is added to the Grouping pane and a row or column on which to display group values is added to the tablix data region on the design surface.</span></span>  
  
### <a name="to-add-a-details-group-to-a-tablix-data-region"></a><span data-ttu-id="947af-131">將詳細資料群組加入到 Tablix 資料區域</span><span class="sxs-lookup"><span data-stu-id="947af-131">To add a details group to a tablix data region</span></span>  
  
1.  <span data-ttu-id="947af-132">在 [群組] 窗格中，以滑鼠右鍵按一下屬於最內部子群組的群組，而不是 [詳細資料]  群組。</span><span class="sxs-lookup"><span data-stu-id="947af-132">In the Grouping pane, right-click a group that is the innermost child group, but not the **Details** group.</span></span> <span data-ttu-id="947af-133">按一下 **[加入群組]** ，然後按一下 **[子群組]** 。</span><span class="sxs-lookup"><span data-stu-id="947af-133">Click **Add Group**, and then click **Child Group**.</span></span> <span data-ttu-id="947af-134">**[Tablix 群組]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="947af-134">The **Tablix Group** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="947af-135">在 **[群組運算式]** 中，將運算式保留空白。</span><span class="sxs-lookup"><span data-stu-id="947af-135">In **Group expression**, leave the expression blank.</span></span> <span data-ttu-id="947af-136">詳細資料群組沒有運算式。</span><span class="sxs-lookup"><span data-stu-id="947af-136">A details group has no expression.</span></span>  
  
3.  <span data-ttu-id="947af-137">選取 **[顯示詳細資料]** 。</span><span class="sxs-lookup"><span data-stu-id="947af-137">Select **Show detail data**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="947af-138">此時新的詳細資料群組會當做子群組加入到 [群組] 窗格中，而且您在步驟 1 中選取之群組的資料列控制代碼會顯示詳細資料群組圖示。</span><span class="sxs-lookup"><span data-stu-id="947af-138">A new details group is added as a child group in the Grouping pane, and the row handle for the group you selected in step 1 displays the details group icon.</span></span> <span data-ttu-id="947af-139">如需控制代碼的詳細資訊，請參閱 [Tablix 資料區資料格、資料列及資料行 &#40;報表產生器及 SSRS&#41;](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="947af-139">For more information about handles, see [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-edit-a-row-or-column-group-in-a-tablix-data-region"></a><span data-ttu-id="947af-140">若要在 Tablix 資料區中編輯資料列或資料行群組</span><span class="sxs-lookup"><span data-stu-id="947af-140">To edit a row or column group in a tablix data region</span></span>  
  
1.  <span data-ttu-id="947af-141">在報表設計介面上，按一下 Tablix 資料區中的任意位置來選取它。</span><span class="sxs-lookup"><span data-stu-id="947af-141">On the report design surface, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="947af-142">[群組] 窗格會顯示資料列和資料行群組。</span><span class="sxs-lookup"><span data-stu-id="947af-142">The Grouping pane displays the row and column groups.</span></span>  
  
2.  <span data-ttu-id="947af-143">以滑鼠右鍵按一下群組，然後按一下 [群組屬性]  。</span><span class="sxs-lookup"><span data-stu-id="947af-143">Right-click the group, and then click **Group Properties**.</span></span>  
  
3.  <span data-ttu-id="947af-144">在 **[名稱]** 中，輸入群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="947af-144">In **Name**, type the name of the group.</span></span>  
  
4.  <span data-ttu-id="947af-145">在 [群組運算式]  中鍵入或選取簡單運算式，或是按一下 [運算式]\(**fx**) 按鈕來建立群組運算式。</span><span class="sxs-lookup"><span data-stu-id="947af-145">In **Group expressions**, type or select a simple expression, or click the Expression (**fx**) button to create a group expression.</span></span>  
  
5.  <span data-ttu-id="947af-146">按一下 **[加入]** 來建立其他運算式。</span><span class="sxs-lookup"><span data-stu-id="947af-146">Click **Add** to create additional expressions.</span></span> <span data-ttu-id="947af-147">您指定的所有運算式都會使用邏輯 AND 結合在一起以指定此群組的資料。</span><span class="sxs-lookup"><span data-stu-id="947af-147">All expressions you specify are combined using a logical AND to specify data for this group.</span></span>  
  
6.  <span data-ttu-id="947af-148">(選擇性) 按一下 [分頁符號]  來設定分頁符號選項。</span><span class="sxs-lookup"><span data-stu-id="947af-148">(Optional) Click **Page Breaks** to set page break options.</span></span>  
  
7.  <span data-ttu-id="947af-149">(選擇性) 按一下 [排序]  來選取或鍵入運算式，以指定群組中值的排序次序。</span><span class="sxs-lookup"><span data-stu-id="947af-149">(Optional) Click **Sorting** to select or type expressions that specify the sort order for values in the group.</span></span>  
  
8.  <span data-ttu-id="947af-150">(選擇性) 按一下 [可見度]  來選取項目的可見度選項。</span><span class="sxs-lookup"><span data-stu-id="947af-150">(Optional) Click **Visibility** to select the visibility options for the item.</span></span>  
  
9. <span data-ttu-id="947af-151">(選擇性) 按一下 [篩選]  來設定此群組的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="947af-151">(Optional) Click **Filters** to set filters for this group.</span></span>  
  
10. <span data-ttu-id="947af-152">(選擇性) 按一下 [變數]  來定義此群組範圍內、可從任何子群組存取的變數。</span><span class="sxs-lookup"><span data-stu-id="947af-152">(Optional) Click **Variables** to define variables scoped to this group and accessible from any child groups.</span></span>  
  
11. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-group-from-a-tablix-data-region"></a><span data-ttu-id="947af-153">若要從 Tablix 資料區刪除群組</span><span class="sxs-lookup"><span data-stu-id="947af-153">To delete a group from a tablix data region</span></span>  
  
1.  <span data-ttu-id="947af-154">在 [群組] 窗格中，以滑鼠右鍵按一下群組，然後按一下 [刪除群組]  。</span><span class="sxs-lookup"><span data-stu-id="947af-154">In the Grouping pane, right-click the group, and then click **Delete Group**.</span></span>  
  
2.  <span data-ttu-id="947af-155">在 **[刪除群組]** 對話方塊中，選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="947af-155">In the **Delete Group** dialog box, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="947af-156">**刪除群組及相關資料列和資料行** ：選擇此選項來刪除群組定義與顯示群組資料的所有相關資料列。</span><span class="sxs-lookup"><span data-stu-id="947af-156">**Delete group and related rows and columns** Choose this option to delete the group definition and all related rows that display group data.</span></span> <span data-ttu-id="947af-157">對於詳細資料群組而言，如果相同的資料列同時屬於詳細資料與群組資料，則只會刪除詳細資料資料列。</span><span class="sxs-lookup"><span data-stu-id="947af-157">For the details group, if the same row belongs to both detail and group data, only the detail data rows are deleted.</span></span>  
  
    -   <span data-ttu-id="947af-158">**只刪除群組** ：選擇此選項，讓 Tablix 資料區的結構保持相同，並僅刪除群組定義。</span><span class="sxs-lookup"><span data-stu-id="947af-158">**Delete group only** Choose this option to keep the structure of the tablix data region the same and delete only the group definition.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-details-group-from-a-tablix-data-region"></a><span data-ttu-id="947af-159">若要從 Tablix 資料區刪除詳細資料群組</span><span class="sxs-lookup"><span data-stu-id="947af-159">To delete a details group from a tablix data region</span></span>  
  
1.  <span data-ttu-id="947af-160">在 [群組] 窗格中，以滑鼠右鍵按一下詳細資料群組，然後按一下 [刪除群組]  。</span><span class="sxs-lookup"><span data-stu-id="947af-160">In the Grouping pane, right-click the details group, and then click **Delete Group**.</span></span>  
  
2.  <span data-ttu-id="947af-161">在 **[刪除群組]** 對話方塊中，選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="947af-161">In the **Delete Group** dialog box, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="947af-162">**刪除群組及相關資料列和資料行** ：選擇此選項來刪除群組定義與顯示群組資料的所有相關資料列。</span><span class="sxs-lookup"><span data-stu-id="947af-162">**Delete group and related rows and columns** Choose this option to delete the group definition and all related rows that display group data.</span></span> <span data-ttu-id="947af-163">對於詳細資料群組而言，如果相同的資料列同時屬於詳細資料與群組資料，則只會刪除詳細資料資料列。</span><span class="sxs-lookup"><span data-stu-id="947af-163">For the details group, if the same row belongs to both detail and group data, only the detail data rows are deleted.</span></span>  
  
    -   <span data-ttu-id="947af-164">**只刪除群組** ：選擇此選項，讓 Tablix 資料區的結構保持相同，並僅刪除群組定義。</span><span class="sxs-lookup"><span data-stu-id="947af-164">**Delete group only** Choose this option to keep the structure of the tablix data region the same and delete only the group definition.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="947af-165">已刪除詳細資料群組。</span><span class="sxs-lookup"><span data-stu-id="947af-165">The details group is deleted.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="947af-166">確認移除詳細資料資料列之後，每個資料格中的運算式都會在適當時指定彙總運算式。</span><span class="sxs-lookup"><span data-stu-id="947af-166">Verify that after you remove a details row, the expression in each cell specifies an aggregate expression where appropriate.</span></span> <span data-ttu-id="947af-167">如有必要，編輯運算式以指定所需的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="947af-167">If necessary, edit the expression to specify aggregate functions as needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="947af-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="947af-168">See Also</span></span>  
 <span data-ttu-id="947af-169">[報表和群組變數集合參考 &#40;報表產生器及 SSRS&#41;](built-in-collections-report-and-group-variables-references-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="947af-169">[Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;](built-in-collections-report-and-group-variables-references-report-builder.md) </span></span>  
 <span data-ttu-id="947af-170">[群組運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="947af-170">[Group Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="947af-171">[篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="947af-171">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="947af-172">[Tablix 資料區 &#40;報表產生器及 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="947af-172">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="947af-173">[資料表 &#40;報表產生器及 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="947af-173">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="947af-174">[矩陣 &#40;報表產生器及 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="947af-174">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="947af-175">[清單 &#40;報表產生器及 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="947af-175">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="947af-176">資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="947af-176">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
