---
title: 在矩陣和圖表上顯示相同的資料 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1262f283-9fc2-4bc1-9c79-457f7642abc7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7746ce1f06d4dcc67c51ddc40714f19a3ff83d51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704917"
---
# <a name="display-the-same-data-on-a-matrix-and-a-chart-report-builder"></a><span data-ttu-id="50d02-102">在矩陣和圖表上顯示相同的資料 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="50d02-102">Display the Same Data on a Matrix and a Chart (Report Builder)</span></span>
  <span data-ttu-id="50d02-103">當您想要在矩陣和圖表中顯示相同的資料時，必須針對兩個資料區設定屬性來指定相同的資料集，也必須針對篩選、群組、排序和資料設定相同的運算式。</span><span class="sxs-lookup"><span data-stu-id="50d02-103">When you want to show the same data in a matrix and a chart, you must set properties on both data regions to specify the same dataset, and also the same expressions for filters, groups, sorts, and data.</span></span>  
  
 <span data-ttu-id="50d02-104">資料 (報表資料集) 的兩個資料區都有相同的上階，因此您可以將互動式排序按鈕加入到矩陣中，讓使用者在按一下該按鈕時，可同時針對矩陣和圖表變更排序次序。</span><span class="sxs-lookup"><span data-stu-id="50d02-104">Because both data regions will have the same ancestor for data (the report dataset), you can add an interactive sort button to the matrix that, when the user clicks it, changes the sort order for both the matrix and the chart.</span></span> <span data-ttu-id="50d02-105">如需詳細資訊，請參閱 [將互動式排序加入至資料表或矩陣 &#40;報表產生器及 SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md)(將互動式排序加入資料表或矩陣 (報表產生器及 SSRS))。</span><span class="sxs-lookup"><span data-stu-id="50d02-105">For more information, see [Add Interactive Sort to a Table or Matrix &#40;Report Builder and SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="50d02-106">若要使用矩陣資料行群組值做為圖表的圖例，您必須在圖表上指定數列資料的色彩，然後使用相同的色彩做為矩陣資料格中，顯示群組值之文字方塊的背景填滿色彩。</span><span class="sxs-lookup"><span data-stu-id="50d02-106">To use the matrix column group values as a legend for the chart, you must specify the colors for the series data on the chart, and then use the same colors as the fill colors for the background of the text boxes in the matrix cell that displays the group values.</span></span> <span data-ttu-id="50d02-107">如需詳細資訊，請參閱[跨多個形狀圖指定一致的色彩 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="50d02-107">For more information, see [Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="50d02-108">如果您的群組定義有太多群組值，您的群組在執行階段可能有點混亂。</span><span class="sxs-lookup"><span data-stu-id="50d02-108">At run-time, your report may appear cluttered if there are too many group values for your group definitions.</span></span> <span data-ttu-id="50d02-109">您可能需要篩選值、結合群組，或調整圖表的臨界值來為您結合群組。</span><span class="sxs-lookup"><span data-stu-id="50d02-109">You might need to filter values, combine groups, or adjust the threshold for the chart to combine groups for you.</span></span> <span data-ttu-id="50d02-110">如需詳細資訊，請參閱 [將多個資料區連結至相同的資料集 &#40;報表產生器及 SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="50d02-110">For more information, see [Linking Multiple Data Regions to the Same Dataset &#40;Report Builder and SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md)</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-matrix-and-chart-to-display-the-same-data"></a><span data-ttu-id="50d02-111">若要加入矩陣和圖表來顯示相同的資料</span><span class="sxs-lookup"><span data-stu-id="50d02-111">To add a matrix and chart to display the same data</span></span>  
  
1.  <span data-ttu-id="50d02-112">在設計檢視中，開啟報表。</span><span class="sxs-lookup"><span data-stu-id="50d02-112">Open a report in design view.</span></span>  
  
2.  <span data-ttu-id="50d02-113">在 **[插入]** 索引標籤的 **[資料區域]** 群組中，按一下 **[矩陣]** ，然後按一下報表主體或報表主體中的矩形。</span><span class="sxs-lookup"><span data-stu-id="50d02-113">From the **Insert** tab, in the **Data Regions** group, click **Matrix**, and then click the report body or in a rectangle in the report body.</span></span> <span data-ttu-id="50d02-114">如此矩陣就會加入至報表。</span><span class="sxs-lookup"><span data-stu-id="50d02-114">A matrix is added to the report.</span></span>  
  
3.  <span data-ttu-id="50d02-115">在 **[插入]** 索引標籤的 **[資料區域]** 群組中，按一下 **[圖表]** ，然後選取圖表類型。</span><span class="sxs-lookup"><span data-stu-id="50d02-115">From the **Insert** tab, in the **Data Regions** group, click **Chart**, and then select the chart type.</span></span> <span data-ttu-id="50d02-116">如此圖表就會加入至報表。</span><span class="sxs-lookup"><span data-stu-id="50d02-116">A chart is added to the report.</span></span>  
  
4.  <span data-ttu-id="50d02-117">(選擇性) 在 [插入]  索引標籤的 [報表項目]  群組中，按一下 [矩形]  ，然後按一下報表。</span><span class="sxs-lookup"><span data-stu-id="50d02-117">(Optional) From the **Insert** tab, in the **Report Items** group, click **Rectangle**, and then click the report.</span></span> <span data-ttu-id="50d02-118">如此矩形就會加入至報表。</span><span class="sxs-lookup"><span data-stu-id="50d02-118">A rectangle is added to the report.</span></span> <span data-ttu-id="50d02-119">將步驟 2 和 3 的矩陣與圖表拖曳至矩形中。</span><span class="sxs-lookup"><span data-stu-id="50d02-119">Drag the matrix and chart from steps 2 and 3 into the rectangle.</span></span>  
  
     <span data-ttu-id="50d02-120">透過將多個資料區域放在矩形容器中，您可以協助控制檢視報表時，矩陣和圖表的呈現方式。</span><span class="sxs-lookup"><span data-stu-id="50d02-120">By placing multiple data regions in the rectangle container, you help control how the matrix and chart render when you view the report.</span></span>  
  
     <span data-ttu-id="50d02-121">在接下來的幾個步驟中，您將選擇相同的資料集欄位以便顯示在矩陣和圖表中。</span><span class="sxs-lookup"><span data-stu-id="50d02-121">In the next few steps, you will choose the same dataset field to display in the matrix and to display in the chart.</span></span>  
  
5.  <span data-ttu-id="50d02-122">將數值資料集欄位從 [報表資料] 窗格拖曳到矩陣的 [資料] 資料格中。</span><span class="sxs-lookup"><span data-stu-id="50d02-122">From the Report Data pane, drag a numeric dataset field to the Data cell in the matrix.</span></span>  
  
     <span data-ttu-id="50d02-123">依預設，彙總函式 Sum 用於計算群組值。</span><span class="sxs-lookup"><span data-stu-id="50d02-123">By default, the aggregate function Sum is used for calculating the group value.</span></span> <span data-ttu-id="50d02-124">如果您變更矩陣中的彙總函式，也必須變更圖表中的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="50d02-124">If you change the aggregate function in the matrix, you must change in the chart also.</span></span>  
  
6.  <span data-ttu-id="50d02-125">在矩陣中，以滑鼠右鍵按一下包含資料的資料格，再按一下 [文字方塊屬性]  ，然後按一下 [數字]  。</span><span class="sxs-lookup"><span data-stu-id="50d02-125">In the matrix, right-click the cell with data, click **Text Box Properties**, and then click **Number**.</span></span> <span data-ttu-id="50d02-126">為資料集欄位值選擇適當的格式。</span><span class="sxs-lookup"><span data-stu-id="50d02-126">Choose an appropriate format for the dataset field value.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="50d02-127">將您在步驟 3 所選擇的相同資料集欄位拖曳到圖表上的 **[值]** 區域。</span><span class="sxs-lookup"><span data-stu-id="50d02-127">Drag the same dataset field you chose in step 3 to the **Values** area on the chart.</span></span>  
  
9. <span data-ttu-id="50d02-128">在圖表中，以滑鼠右鍵按一下 Y 軸，按一下 [軸屬性]  ，然後按一下 [數字]  。</span><span class="sxs-lookup"><span data-stu-id="50d02-128">In the chart, right-click the Y axis, click **Axis Properties**, and then click **Number**.</span></span> <span data-ttu-id="50d02-129">為您在步驟 4 中選擇的資料選擇相同的格式。</span><span class="sxs-lookup"><span data-stu-id="50d02-129">Choose the same format for the data that you chose in step 4.</span></span>  
  
10. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="50d02-130">在接下來的幾個步驟中，您會將矩陣資料列群組和圖表數列群組設定為相同的運算式，同時也設定圖表數列群組的排序次序。</span><span class="sxs-lookup"><span data-stu-id="50d02-130">In the next few steps, you will set the matrix row group and the chart series group to the same expression, and also set the sort order for the chart series group.</span></span>  
  
11. <span data-ttu-id="50d02-131">從 [報表資料] 窗格中，將您要依矩陣資料列分組的資料集欄位拖曳到 [資料列群組] 窗格。</span><span class="sxs-lookup"><span data-stu-id="50d02-131">From the Report Data pane, drag the dataset field that you want to group by for matrix rows to the Row Groups pane.</span></span>  
  
     <span data-ttu-id="50d02-132">根據預設，矩陣資料列群組會加入與群組運算式相同的排序運算式。</span><span class="sxs-lookup"><span data-stu-id="50d02-132">By default, the matrix row group adds a sort expression that is the same as the group expression.</span></span>  
  
12. <span data-ttu-id="50d02-133">將您在步驟 9 中所使用的相同資料集欄位拖曳到圖表的 **[數列群組]** 區域。</span><span class="sxs-lookup"><span data-stu-id="50d02-133">Drag the same dataset field that you used in step 9 to the **Series Groups** area for the chart.</span></span>  
  
13. <span data-ttu-id="50d02-134">以滑鼠右鍵按一下 [數列群組]  區域中的群組，然後按一下 [數列群組屬性]  。</span><span class="sxs-lookup"><span data-stu-id="50d02-134">Right-click the group in the **Series Groups** area, and then click **Series Group Properties**.</span></span>  
  
14. <span data-ttu-id="50d02-135">按一下 **[排序]** 。</span><span class="sxs-lookup"><span data-stu-id="50d02-135">Click **Sorting**.</span></span>  
  
15. <span data-ttu-id="50d02-136">按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="50d02-136">Click **Add**.</span></span> <span data-ttu-id="50d02-137">新的資料列會出現在排序運算式方格中。</span><span class="sxs-lookup"><span data-stu-id="50d02-137">A new row appears in the sort expressions grid.</span></span>  
  
16. <span data-ttu-id="50d02-138">在 [排序依據]  的下拉式清單中，選擇您在步驟 9 中選為分組依據的資料集欄位。</span><span class="sxs-lookup"><span data-stu-id="50d02-138">In **Sort by**, from the drop-down list, choose the dataset field that you chose to group by in step 9.</span></span>  
  
17. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="50d02-139">在接下來的幾個步驟中，您會將矩陣資料行群組和圖表類別目錄群組設定為相同的運算式，同時也設定圖表類別目錄群組的排序次序。</span><span class="sxs-lookup"><span data-stu-id="50d02-139">In the next few steps, you will set the matrix column group and the chart category group to the same expression, and also set the sort order for the chart category group.</span></span>  
  
18. <span data-ttu-id="50d02-140">從 [報表資料] 窗格中，將您要依矩陣資料行分組的資料集欄位拖曳到 [資料行群組] 窗格。</span><span class="sxs-lookup"><span data-stu-id="50d02-140">From the Report Data pane, drag the dataset field that you want to group by for matrix columns to the Column Groups pane.</span></span>  
  
     <span data-ttu-id="50d02-141">根據預設，矩陣資料行群組會加入與群組運算式相同的排序運算式。</span><span class="sxs-lookup"><span data-stu-id="50d02-141">By default, the matrix column group adds a sort expression that is the same as the group expression.</span></span>  
  
19. <span data-ttu-id="50d02-142">將您在步驟 16 中所使用的相同資料集欄位拖曳到圖表的 **[類別目錄群組]** 區域。</span><span class="sxs-lookup"><span data-stu-id="50d02-142">Drag the same dataset field that you used in step 16 to the **Category Groups** area for the chart.</span></span>  
  
20. <span data-ttu-id="50d02-143">以滑鼠右鍵按一下 [類別目錄群組]  區域中的群組，然後按一下 [類別目錄群組屬性]  。</span><span class="sxs-lookup"><span data-stu-id="50d02-143">Right-click the group in the **CategoryGroups** area, and then click **Category Group Properties**.</span></span>  
  
21. <span data-ttu-id="50d02-144">按一下 **[排序]** 。</span><span class="sxs-lookup"><span data-stu-id="50d02-144">Click **Sorting**.</span></span>  
  
22. <span data-ttu-id="50d02-145">按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="50d02-145">Click **Add**.</span></span> <span data-ttu-id="50d02-146">新的資料列會出現在排序運算式方格中。</span><span class="sxs-lookup"><span data-stu-id="50d02-146">A new row appears in the sort expressions grid.</span></span>  
  
23. <span data-ttu-id="50d02-147">在 [排序依據]  的下拉式清單中，選擇您在步驟 16 中選為分組依據的資料集欄位。</span><span class="sxs-lookup"><span data-stu-id="50d02-147">In **Sort by**, from the drop-down list, choose the dataset field that you chose to group by in step 16.</span></span>  
  
24. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
25. <span data-ttu-id="50d02-148">預覽結果。</span><span class="sxs-lookup"><span data-stu-id="50d02-148">Preview the result.</span></span> <span data-ttu-id="50d02-149">矩陣資料列和資料行群組會顯示與圖表數列和類別目錄群組相同的資料。</span><span class="sxs-lookup"><span data-stu-id="50d02-149">The matrix row and column groups display the same data as the chart series and category groups.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50d02-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50d02-150">See Also</span></span>  
 <span data-ttu-id="50d02-151">[將多個資料區連結至相同的資料集 &#40;報表產生器及 SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="50d02-151">[Linking Multiple Data Regions to the Same Dataset &#40;Report Builder and SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="50d02-152">[新增資料集篩選、資料區篩選和群組篩選 &#40;報表產生器及 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="50d02-152">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="50d02-153">[列出 &#40;報表產生器和 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="50d02-153">[Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="50d02-154">圖表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="50d02-154">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
