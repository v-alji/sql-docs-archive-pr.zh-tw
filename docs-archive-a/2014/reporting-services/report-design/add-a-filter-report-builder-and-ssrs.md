---
title: 新增篩選 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 10ae54e7-0e8a-4dff-995d-05516c51d076
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 61a5444c437027d92a9f054e74cbcac6af5cc776
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710190"
---
# <a name="add-a-filter-report-builder-and-ssrs"></a><span data-ttu-id="1ac5b-102">加入篩選 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="1ac5b-102">Add a Filter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1ac5b-103">當您想要針對計算或顯示包含或排除特定值時，請將篩選加入至資料集、資料區或群組。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-103">Add a filter to a dataset, data region, or group when you want to include or exclude specific values for calculations or display.</span></span> <span data-ttu-id="1ac5b-104">篩選會在執行階段先套用至資料集、套用至資料區，然後套用至群組 (按照群組階層的由上而下順序)。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-104">Filters are applied at run time first on the dataset, and then on the data region, and then on the group, in top-down order for group hierarchies.</span></span> <span data-ttu-id="1ac5b-105">在資料表、矩陣或清單中，系統會針對資料列群組、資料行群組和相鄰群組獨立套用篩選。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-105">In a table, matrix, or list, filters for row groups, column groups, and adjacent groups are applied independently.</span></span> <span data-ttu-id="1ac5b-106">在圖表中，系統會針對類別目錄群組和數列群組獨立套用篩選。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-106">In a chart, filters for category groups and series groups are applied independently.</span></span>  
  
 <span data-ttu-id="1ac5b-107">若要加入篩選，您必須指定一或多個篩選方程式。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-107">To add a filter, you must specify one or more filter equations.</span></span> <span data-ttu-id="1ac5b-108">篩選方程式包含一個識別您想要篩選之資料的運算式、一個運算子和一個要比較的值。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-108">A filter equation consists of an expression that identifies the data that you want to filter, an operator, and the value to compare to.</span></span> <span data-ttu-id="1ac5b-109">篩選資料和值的資料類型必須相符。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-109">The data types of the filtered data and the value must match.</span></span> <span data-ttu-id="1ac5b-110">不支援針對資料集或資料區的彙總值進行篩選。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-110">Filtering on aggregate values for a dataset or data region is not supported.</span></span>  
  
 <span data-ttu-id="1ac5b-111">若要篩選圖表中的資料點，您可以針對類別目錄群組或數列群組設定篩選。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-111">To filter data points in a chart, you can set a filter on a category group or a series group.</span></span> <span data-ttu-id="1ac5b-112">依預設，圖表會使用內建函數 Sum，將屬於相同群組的值彙總成數列中的個別資料點。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-112">By default, the chart uses the built-in function Sum to aggregate values that belong to the same group into an individual data point in the series.</span></span> <span data-ttu-id="1ac5b-113">如果您變更數列的彙總函式，就必須變更篩選運算式中的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-113">If you change the aggregate function of a series, you must change the aggregate function in the filter expression.</span></span>  
  
 <span data-ttu-id="1ac5b-114">如需篩選內嵌和共用資料集的詳細資訊，請參閱[將篩選新增至資料集 &#40;報表產生器及 SSRS&#41;](../report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-114">For more information about filtering embedded and shared datasets, see [Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;](../report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-a-filter-on-a-data-region"></a><span data-ttu-id="1ac5b-115">若要設定資料區的篩選</span><span class="sxs-lookup"><span data-stu-id="1ac5b-115">To set a filter on a data region</span></span>  
  
1.  <span data-ttu-id="1ac5b-116">在 **[設計]** 檢視中，開啟報表。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-116">Open a report in **Design** view.</span></span>  
  
2.  <span data-ttu-id="1ac5b-117">選取設計介面上的資料區，然後以滑鼠右鍵按一下 [ _\<data region>_ **屬性**]。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-117">Select the data region on the design surface, and then right-click _\<data region>_**Properties**.</span></span> <span data-ttu-id="1ac5b-118">若為量測計，請選取 **[量測計面板屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-118">For a gauge, select **Gauge Panel Properties**.</span></span> <span data-ttu-id="1ac5b-119">[ _\<data region>_ **屬性**] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-119">The _\<data region>_**Properties** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1ac5b-120">在 Tablix 資料區上，以滑鼠右鍵按一下邊角資料格或是資料列或資料行控制代碼，然後按一下 [Tablix 屬性]  。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-120">On a Tablix data region, right-click the corner cell or a row or column handle, and then click **Tablix Properties**.</span></span>  
  
3.  <span data-ttu-id="1ac5b-121">按一下 **[篩選]** 。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-121">Click **Filters**.</span></span> <span data-ttu-id="1ac5b-122">這樣就會顯示目前的篩選方程式清單。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-122">This displays the current list of filter equations.</span></span> <span data-ttu-id="1ac5b-123">根據預設，此清單是空的。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-123">By default, the list is empty.</span></span>  
  
4.  <span data-ttu-id="1ac5b-124">按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-124">Click **Add**.</span></span> <span data-ttu-id="1ac5b-125">新的空白篩選方程式隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-125">A new blank filter equation appears.</span></span>  
  
5.  <span data-ttu-id="1ac5b-126">在 **[運算式]** 中，針對要篩選的欄位輸入或選取運算式。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-126">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="1ac5b-127">若要編輯運算式，請按一下運算式 (*fx*) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-127">To edit the expression, click the expression (*fx*) button.</span></span>  
  
6.  <span data-ttu-id="1ac5b-128">在下拉式方塊中，選取符合您在步驟 5 中建立之運算式資料類型的資料類型。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-128">From the drop-down box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
7.  <span data-ttu-id="1ac5b-129">在 **[運算子]** 方塊中，選取您想要篩選用來比較 **[運算式]** 方塊和 **[值]** 方塊中值的運算子。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-129">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="1ac5b-130">您所選擇的運算子會決定下一個步驟所使用的值數目。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-130">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
8.  <span data-ttu-id="1ac5b-131">在 **[值]** 方塊中，輸入您想要篩選在評估 **[運算式]** 中的值時，所針對的運算式或值。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-131">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="1ac5b-132">如需篩選方程式的範例，請參閱[篩選方程式範例 &#40;報表產生器及 SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-132">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-set-a-filter-on-a-tablix-row-or-column-group"></a><span data-ttu-id="1ac5b-133">設定 Tablix 資料列或資料行群組的篩選</span><span class="sxs-lookup"><span data-stu-id="1ac5b-133">To set a filter on a Tablix row or column group</span></span>  
  
1.  <span data-ttu-id="1ac5b-134">在 **[設計]** 檢視中，開啟報表。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-134">Open a report in **Design** view.</span></span>  
  
2.  <span data-ttu-id="1ac5b-135">以滑鼠右鍵按一下設計介面上的資料表、矩陣或清單資料區域，即可加以選取。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-135">Right-click the table, matrix, or list data region on the design surface to select it.</span></span> <span data-ttu-id="1ac5b-136">[群組] 窗格會顯示選定項目的群組。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-136">The Grouping pane displays the groups for the selected item.</span></span>  
  
3.  <span data-ttu-id="1ac5b-137">在 [群組] 窗格中，以滑鼠右鍵按一下群組，然後按一下 [編輯群組]  。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-137">In the Grouping pane, right-click the group, and then click **Edit Group**.</span></span> <span data-ttu-id="1ac5b-138">**[Tablix 群組]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-138">The **Tablix Group** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="1ac5b-139">按一下 **[篩選]** 。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-139">Click **Filters**.</span></span> <span data-ttu-id="1ac5b-140">這樣就會顯示目前的篩選方程式清單。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-140">This displays the current list of filter equations.</span></span> <span data-ttu-id="1ac5b-141">根據預設，此清單是空的。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-141">By default, the list is empty.</span></span>  
  
5.  <span data-ttu-id="1ac5b-142">按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-142">Click **Add**.</span></span> <span data-ttu-id="1ac5b-143">新的空白篩選方程式隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-143">A new blank filter equation appears.</span></span>  
  
6.  <span data-ttu-id="1ac5b-144">在 **[運算式]** 中，針對要篩選的欄位輸入或選取運算式。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-144">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="1ac5b-145">若要編輯運算式，請按一下運算式 (*fx*) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-145">To edit the expression, click the expression (*fx*) button.</span></span>  
  
7.  <span data-ttu-id="1ac5b-146">在下拉式方塊中，選取符合您在步驟 5 中建立之運算式資料類型的資料類型。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-146">From the drop-down box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
8.  <span data-ttu-id="1ac5b-147">在 **[運算子]** 方塊中，選取您想要篩選用來比較 **[運算式]** 方塊和 **[值]** 方塊中值的運算子。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-147">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="1ac5b-148">您所選擇的運算子會決定下一個步驟所使用的值數目。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-148">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
9. <span data-ttu-id="1ac5b-149">在 **[值]** 方塊中，輸入您想要篩選在評估 **[運算式]** 中的值時，所針對的運算式或值。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-149">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="1ac5b-150">如需篩選方程式的範例，請參閱[篩選方程式範例 &#40;報表產生器及 SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-150">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-set-a-filter-on-a-chart-category-group"></a><span data-ttu-id="1ac5b-151">設定圖表類別目錄群組的篩選</span><span class="sxs-lookup"><span data-stu-id="1ac5b-151">To set a filter on a Chart category group</span></span>  
  
1.  <span data-ttu-id="1ac5b-152">在 **[設計]** 檢視中，開啟報表。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-152">Open a report in **Design** view.</span></span>  
  
2.  <span data-ttu-id="1ac5b-153">在設計介面上，按兩下圖表，即可開啟資料、數列和類別目錄欄位放置區。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-153">On the design surface, click the chart twice to bring up data, series and category field drop zones.</span></span>  
  
3.  <span data-ttu-id="1ac5b-154">以滑鼠右鍵按一下類別目錄欄位放置區所包含的欄位，然後選取 [類別目錄群組屬性]  。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-154">Right-click on a field contained in the category field drop zone and select **Category Group Properties**.</span></span>  
  
4.  <span data-ttu-id="1ac5b-155">按一下 **[篩選]** 。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-155">Click **Filters**.</span></span> <span data-ttu-id="1ac5b-156">這樣就會顯示目前的篩選方程式清單。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-156">This displays the current list of filter equations.</span></span> <span data-ttu-id="1ac5b-157">根據預設，此清單是空的。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-157">By default, the list is empty.</span></span>  
  
5.  <span data-ttu-id="1ac5b-158">按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-158">Click **Add**.</span></span> <span data-ttu-id="1ac5b-159">新的空白篩選方程式隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-159">A new blank filter equation appears.</span></span>  
  
6.  <span data-ttu-id="1ac5b-160">在 **[運算式]** 中，針對要篩選的欄位輸入或選取運算式。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-160">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="1ac5b-161">若要編輯運算式，請按一下運算式 (*fx*) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-161">To edit the expression, click the expression (*fx*) button.</span></span>  
  
7.  <span data-ttu-id="1ac5b-162">在下拉式方塊中，選取符合您在步驟 5 中建立之運算式資料類型的資料類型。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-162">From the drop-down box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
8.  <span data-ttu-id="1ac5b-163">在 **[運算子]** 方塊中，選取您想要篩選用來比較 **[運算式]** 方塊和 **[值]** 方塊中值的運算子。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-163">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="1ac5b-164">您所選擇的運算子會決定下一個步驟所使用的值數目。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-164">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
9. <span data-ttu-id="1ac5b-165">在 **[值]** 方塊中，輸入您想要篩選在評估 **[運算式]** 中的值時，所針對的運算式或值。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-165">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="1ac5b-166">如需篩選方程式的範例，請參閱[篩選方程式範例 &#40;報表產生器及 SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-166">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-set-a-filter-on-a-chart-series-group"></a><span data-ttu-id="1ac5b-167">設定圖表數列群組的篩選</span><span class="sxs-lookup"><span data-stu-id="1ac5b-167">To set a filter on a Chart series group</span></span>  
  
1.  <span data-ttu-id="1ac5b-168">在 **[設計]** 檢視中，開啟報表。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-168">Open a report in **Design** view.</span></span>  
  
2.  <span data-ttu-id="1ac5b-169">在設計介面上，按兩下圖表，即可開啟資料、數列和類別目錄欄位放置區。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-169">On the design surface, click the chart twice to bring up data, series and category field drop zones.</span></span>  
  
3.  <span data-ttu-id="1ac5b-170">以滑鼠右鍵按一下數列欄位放置區所包含的欄位，然後選取 [數列群組屬性]  。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-170">Right-click on a field contained in the series field drop zone and select **Series Group Properties**.</span></span>  
  
4.  <span data-ttu-id="1ac5b-171">按一下 **[篩選]** 。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-171">Click **Filters**.</span></span> <span data-ttu-id="1ac5b-172">這樣就會顯示目前的篩選方程式清單。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-172">This displays the current list of filter equations.</span></span> <span data-ttu-id="1ac5b-173">根據預設，此清單是空的。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-173">By default, the list is empty.</span></span>  
  
5.  <span data-ttu-id="1ac5b-174">按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-174">Click **Add**.</span></span> <span data-ttu-id="1ac5b-175">新的空白篩選方程式隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-175">A new blank filter equation appears.</span></span>  
  
6.  <span data-ttu-id="1ac5b-176">在 **[運算式]** 中，針對要篩選的欄位輸入或選取運算式。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-176">In **Expression**, type or select the expression for the field to filter.</span></span> <span data-ttu-id="1ac5b-177">若要編輯運算式，請按一下運算式 (*fx*) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-177">To edit the expression, click the expression (*fx*) button.</span></span>  
  
7.  <span data-ttu-id="1ac5b-178">在下拉式方塊中，選取符合您在步驟 5 中建立之運算式資料類型的資料類型。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-178">From the drop-down box, select the data type that matches the type of data in the expression you created in step 5.</span></span>  
  
8.  <span data-ttu-id="1ac5b-179">在 **[運算子]** 方塊中，選取您想要篩選用來比較 **[運算式]** 方塊和 **[值]** 方塊中值的運算子。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-179">In the **Operator** box, select the operator that you want the filter to use to compare the values in the **Expression** box and the **Value** box.</span></span> <span data-ttu-id="1ac5b-180">您所選擇的運算子會決定下一個步驟所使用的值數目。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-180">The operator you choose determines the number of values that are used from the next step.</span></span>  
  
9. <span data-ttu-id="1ac5b-181">在 **[值]** 方塊中，輸入您想要篩選在評估 **[運算式]** 中的值時，所針對的運算式或值。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-181">In the **Value** box, type the expression or value against which you want the filter to evaluate the value in **Expression**.</span></span>  
  
     <span data-ttu-id="1ac5b-182">如需篩選方程式的範例，請參閱[篩選方程式範例 &#40;報表產生器及 SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1ac5b-182">For examples of filter equations, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md).</span></span>  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1ac5b-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ac5b-183">See Also</span></span>  
 <span data-ttu-id="1ac5b-184">[新增資料集篩選、資料區篩選和群組篩選 &#40;報表產生器及 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="1ac5b-184">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="1ac5b-185">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1ac5b-185">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1ac5b-186">[量測計 &#40;報表產生器及 SSRS&#41;](gauges-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1ac5b-186">[Gauges &#40;Report Builder and SSRS&#41;](gauges-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1ac5b-187">[列出 &#40;報表產生器和 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1ac5b-187">[Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1ac5b-188">圖表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ac5b-188">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
