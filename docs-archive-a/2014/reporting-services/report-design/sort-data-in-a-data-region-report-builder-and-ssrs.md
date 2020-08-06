---
title: 在資料區中排序資料 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2fcb9be2-1daa-4c92-ad00-5f63cdf39f70
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bc1fb458066bb942a490b08c0faad876dd3d5438
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707058"
---
# <a name="sort-data-in-a-data-region-report-builder-and-ssrs"></a><span data-ttu-id="ebdd6-102">在資料區中排序資料 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="ebdd6-102">Sort Data in a Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ebdd6-103">若要在資料區域中變更報表第一次執行時資料的排序次序，您必須針對資料區域或群組設定排序運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-103">To change the sort order of data in a data region when a report first runs, you must set the sort expression on the data region or group.</span></span> <span data-ttu-id="ebdd6-104">根據預設，群組的排序運算式會自動設定為與群組運算式相同的值。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-104">By default, the sort expression for a group is automatically set to the same value as the group expression.</span></span>  
  
-   <span data-ttu-id="ebdd6-105">在 Tablix 資料區域中，設定資料區域或每個群組 (包括詳細資料群組) 的排序運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-105">In a tablix data region, set the sort expression for the data region or for each group, including the details group.</span></span> <span data-ttu-id="ebdd6-106">如果您在 Tablix 資料區域中只有一個詳細資料群組，您可以在查詢中、資料區域上，或詳細資料群組上，定義排序運算式，而且它們都有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-106">If you have only one details group in a tablix data region, you can define a sort expression in the query, on the data region, or on the details group and they all have the same effect.</span></span>  
  
-   <span data-ttu-id="ebdd6-107">在圖表資料區域中，設定 [類別目錄] 和 [數列] 群組的排序運算式來控制每個群組的排序次序。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-107">In a chart data region, set the sort expression for the Category and Series groups to control the sort order for each group.</span></span> <span data-ttu-id="ebdd6-108">在圖表圖例中，色彩的次序取決於 [類別目錄] 群組中資料點的排序運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-108">The order for colors in a chart legend is determined by the sort expression for the data points in the Category group.</span></span>  
  
-   <span data-ttu-id="ebdd6-109">在量測計資料區域中，您通常不需要排序資料，因為量測計會顯示一個相對於範圍的單一值。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-109">In a gauge data region, you do not typically need to sort data because the gauge displays a single value relative to a range.</span></span> <span data-ttu-id="ebdd6-110">如果您需要排序量測計中的資料，則必須先定義一個群組，然後設定該群組的排序運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-110">If you do need sort data in a gauge, you must first define a group, and then set the sort expression for the group.</span></span>  
  
 <span data-ttu-id="ebdd6-111">如需詳細資訊，請參閱 [篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)(將互動式排序加入資料表或矩陣 (報表產生器及 SSRS))。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-111">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="ebdd6-112">若是 Tablix 資料區域，您也可以將互動式排序按鈕加入到資料行標頭的頂端，以提供使用者變更群組或詳細資料列之排序次序的能力。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-112">For a tablix data region, you can also add an interactive sort button to the top of a column header to provide the user with the ability to change the sort order of groups or detail rows.</span></span> <span data-ttu-id="ebdd6-113">如需詳細資訊，請參閱[互動式排序 &#40;報表產生器及 SSRS&#41;](interactive-sort-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-113">For more information, see [Interactive Sort &#40;Report Builder and SSRS&#41;](interactive-sort-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-sort-data-in-a-tablix-data-region"></a><span data-ttu-id="ebdd6-114">在 Tablix 資料區域中排序資料</span><span class="sxs-lookup"><span data-stu-id="ebdd6-114">To sort data in a Tablix data region</span></span>  
  
1.  <span data-ttu-id="ebdd6-115">以滑鼠右鍵按一下設計介面上的資料列控制代碼，然後按一下 [Tablix 屬性]  。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-115">On the design surface, right-click a row handle, and then click **Tablix Properties**.</span></span>  
  
2.  <span data-ttu-id="ebdd6-116">按一下 **[排序]** 。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-116">Click **Sorting**.</span></span>  
  
3.  <span data-ttu-id="ebdd6-117">針對每個排序運算式，請依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="ebdd6-117">For each sort expression, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="ebdd6-118">按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-118">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="ebdd6-119">輸入或選取排序資料所依據的運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-119">Type or select an expression by which to sort the data.</span></span>  
  
    3.  <span data-ttu-id="ebdd6-120">從 **Order** 資料行下拉式清單中，選擇每個運算式的排序方向。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-120">From the **Order** column drop-down list, choose the sort direction for each expression.</span></span> <span data-ttu-id="ebdd6-121">**A-Z** 會以遞增順序排序運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-121">**A-Z** sorts the expression in ascending order.</span></span> <span data-ttu-id="ebdd6-122">**Z-A** 會以遞減順序排序運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-122">**Z-A** sorts the expression in descending order.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-sort-values-in-a-group-including-the-details-group-for-a-tablix"></a><span data-ttu-id="ebdd6-123">針對 Tablix 排序群組 (包括詳細資料群組) 中的值</span><span class="sxs-lookup"><span data-stu-id="ebdd6-123">To sort values in a group, including the details group, for a Tablix</span></span>  
  
1.  <span data-ttu-id="ebdd6-124">在設計介面上，按一下 Tablix 資料區域來選取它。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-124">On the design surface, click in the tablix data region to select it.</span></span> <span data-ttu-id="ebdd6-125">[群組] 窗格會顯示 Tablix 資料區域的資料列群組和資料行群組。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-125">The Grouping pane displays the row groups and column groups for the Tablix data region.</span></span>  
  
2.  <span data-ttu-id="ebdd6-126">在 [資料列群組] 窗格中，以滑鼠右鍵按一下群組名稱，然後按一下 [編輯群組]  。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-126">In the Row Groups pane, right-click the group name, and then click **Edit Group**.</span></span>  
  
3.  <span data-ttu-id="ebdd6-127">在 **[Tablix 群組]** 對話方塊中，按一下 **[排序]** 。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-127">In the **Tablix Group** dialog box, click **Sort**.</span></span>  
  
4.  <span data-ttu-id="ebdd6-128">針對每個排序運算式，請依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="ebdd6-128">For each sort expression, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="ebdd6-129">按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-129">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="ebdd6-130">輸入或選取排序資料所依據的運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-130">Type or select an expression by which to sort the data.</span></span>  
  
    3.  <span data-ttu-id="ebdd6-131">從 **Order** 資料行下拉式清單中，選擇每個運算式的排序方向。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-131">From the **Order** column drop-down list, choose the sort direction for each expression.</span></span> <span data-ttu-id="ebdd6-132">**A-Z** 會以遞增順序排序運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-132">**A-Z** sorts the expression in ascending order.</span></span> <span data-ttu-id="ebdd6-133">**Z-A** 會以遞減順序排序運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-133">**Z-A** sorts the expression in descending order.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-sort-x-axis-labels-in-alphabetical-order-on-a-chart"></a><span data-ttu-id="ebdd6-134">在圖表上按照字母順序排序 x 軸標籤</span><span class="sxs-lookup"><span data-stu-id="ebdd6-134">To sort x-axis labels in alphabetical order on a chart</span></span>  
  
1.  <span data-ttu-id="ebdd6-135">在 [類別目錄欄位] 放置區中的欄位上按一下滑鼠右鍵，然後按一下 [類別目錄群組屬性]  。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-135">Right-click a field in the Category Field drop-zone and click **Category GroupProperties**.</span></span>  
  
2.  <span data-ttu-id="ebdd6-136">在 **[類別目錄群組屬性]** 對話方塊中，按一下 **[排序]** 。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-136">In the **Category Group Properties** dialog box, click **Sorting**.</span></span>  
  
3.  <span data-ttu-id="ebdd6-137">針對每個排序運算式，請依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="ebdd6-137">For each sort expression, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="ebdd6-138">按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-138">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="ebdd6-139">選取符合您群組欄位的運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-139">Select the expression that matches your grouping field.</span></span> <span data-ttu-id="ebdd6-140">您可以按一下 **[群組]** 來驗證群組欄位的運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-140">You can verify the expression for the grouping field by clicking **Grouping**.</span></span>  
  
    3.  <span data-ttu-id="ebdd6-141">從 **Order** 資料行下拉式清單中，選擇每個運算式的排序方向。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-141">From the **Order** column drop-down list, choose the sort direction for each expression.</span></span> <span data-ttu-id="ebdd6-142">[A-Z]  會以字母的遞增順序排序運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-142">**A-Z** sorts the expression in ascending alphabetical order.</span></span> <span data-ttu-id="ebdd6-143">[Z-A]  會以字母的遞減順序排序運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-143">**Z-A** sorts the expression in descending alphabetical order.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-sort-the-data-points-in-ascending-or-descending-order-on-a-chart"></a><span data-ttu-id="ebdd6-144">在圖表上，以遞增或遞減的順序排序資料點</span><span class="sxs-lookup"><span data-stu-id="ebdd6-144">To sort the data points in ascending or descending order on a chart</span></span>  
  
1.  <span data-ttu-id="ebdd6-145">在 [類別目錄欄位] 放置區中的欄位上按一下滑鼠右鍵，然後按一下 [類別目錄群組屬性]  。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-145">Right-click a field in the Category Field drop zone and click **Category GroupProperties**.</span></span>  
  
2.  <span data-ttu-id="ebdd6-146">在 **[類別目錄群組屬性]** 對話方塊中，按一下 **[排序]** 。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-146">In the **Category Group Properties** dialog box, click **Sorting**.</span></span>  
  
3.  <span data-ttu-id="ebdd6-147">針對每個排序運算式，請依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="ebdd6-147">For each sort expression, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="ebdd6-148">按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-148">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="ebdd6-149">選取符合您資料欄位的運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-149">Select the expression that matches your data field.</span></span> <span data-ttu-id="ebdd6-150">在大部分的情況下，這是彙總值，例如 `=Sum(Fields!Quantity.Value)`。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-150">In most cases, this is an aggregated value, such as `=Sum(Fields!Quantity.Value)`.</span></span>  
  
    3.  <span data-ttu-id="ebdd6-151">從 **Order** 資料行下拉式清單中，選擇每個運算式的排序方向。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-151">From the **Order** column drop-down list, choose the sort direction for each expression.</span></span> <span data-ttu-id="ebdd6-152">**A-Z** 會以遞增順序排序運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-152">**A-Z** sorts the expression in ascending order.</span></span> <span data-ttu-id="ebdd6-153">**Z-A** 會以遞減順序排序運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-153">**Z-A** sorts the expression in descending order.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-sort-data-in-ascending-or-descending-order-for-display-on-a-gauge"></a><span data-ttu-id="ebdd6-154">在量測計上，以遞增或遞減的順序排序要顯示的資料</span><span class="sxs-lookup"><span data-stu-id="ebdd6-154">To sort data in ascending or descending order for display on a gauge</span></span>  
  
1.  <span data-ttu-id="ebdd6-155">以滑鼠右鍵按一下量測計，然後按一下 [新增資料群組]  。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-155">Right-click the gauge and click **Add Data Group**.</span></span>  
  
2.  <span data-ttu-id="ebdd6-156">必要時，在 [量測計面板群組屬性]  對話方塊中，按一下 [一般]  。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-156">In the **Gauge Panel GroupProperties** dialog box, click **General** if necessary.</span></span>  
  
3.  <span data-ttu-id="ebdd6-157">在 **[群組運算式]** 中，按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-157">In **Group expressions**, click **Add**.</span></span>  
  
4.  <span data-ttu-id="ebdd6-158">在 **[群組對象]** 中，輸入或選取用來分組資料的運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-158">In **Group on**, type or select an expression by which to group the data.</span></span>  
  
5.  <span data-ttu-id="ebdd6-159">重複步驟 3 和 4，直到加入您要使用的所有群組運算式為止。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-159">Repeat steps 3 and 4 until you have added all the group expressions you want to use.</span></span>  
  
6.  <span data-ttu-id="ebdd6-160">按一下 **[排序]** 。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-160">Click **Sorting**.</span></span>  
  
7.  <span data-ttu-id="ebdd6-161">針對每個排序運算式，請依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="ebdd6-161">For each sort expression, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="ebdd6-162">按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-162">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="ebdd6-163">選取符合您群組欄位的運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-163">Select the expression that matches your grouping field.</span></span> <span data-ttu-id="ebdd6-164">您可以按一下 **[群組]** 來驗證群組欄位的運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-164">You can verify the expression for the grouping field by clicking **Grouping**.</span></span>  
  
    3.  <span data-ttu-id="ebdd6-165">從 **Order** 資料行下拉式清單中，選擇每個運算式的排序方向。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-165">From the **Order** column drop-down list, choose the sort direction for each expression.</span></span> <span data-ttu-id="ebdd6-166">**A-Z** 會以遞增順序排序運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-166">**A-Z** sorts the expression in ascending order.</span></span> <span data-ttu-id="ebdd6-167">**Z-A** 會以遞減順序排序運算式。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-167">**Z-A** sorts the expression in descending order.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="ebdd6-168">如需如何在量測計中群組資料的詳細資訊，請參閱[量測計 &#40;報表產生器及 SSRS&#41;](gauges-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ebdd6-168">For more information about how data is grouped in a gauge, see [Gauges &#40;Report Builder and SSRS&#41;](gauges-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebdd6-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebdd6-169">See Also</span></span>  
 <span data-ttu-id="ebdd6-170">[對話方塊、窗格和嚮導的報表產生器說明](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="ebdd6-170">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="ebdd6-171">[圖表 &#40;報表產生器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ebdd6-171">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ebdd6-172">[格式化圖表上的軸標籤 &#40;報表產生器和 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ebdd6-172">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ebdd6-173">跨多個形狀圖指定一致的色彩 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ebdd6-173">Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;</span></span>](shape-charts-report-builder-and-ssrs.md)  
  
  
