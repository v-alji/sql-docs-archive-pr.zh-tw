---
title: 在圖表中放置標籤 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5db74e0b-8be8-4b47-b386-faab56dffa9b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e90cbf04e0282454658e6324f0ba6600a99cb718
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686770"
---
# <a name="position-labels-in-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="c874e-102">在圖表中放置標籤 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="c874e-102">Position Labels in a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c874e-103">因為每種圖表類型都有不同的形狀，所以資料點標籤會放置於最佳位置，避免影響圖表。</span><span class="sxs-lookup"><span data-stu-id="c874e-103">Because each chart type has a different shape, data point labels are placed in an optimal location so as not to interfere on the chart.</span></span> <span data-ttu-id="c874e-104">標籤的預設位置會因圖表類型而不同：</span><span class="sxs-lookup"><span data-stu-id="c874e-104">The default position of the labels depends varies with the chart type:</span></span>  
  
-   <span data-ttu-id="c874e-105">在堆疊圖表上，標籤只能放置於數列內部。</span><span class="sxs-lookup"><span data-stu-id="c874e-105">On stacked charts, labels can only be positioned inside the series.</span></span>  
  
-   <span data-ttu-id="c874e-106">在漏斗圖或金字塔圖上，標籤會位於直條外部。</span><span class="sxs-lookup"><span data-stu-id="c874e-106">On funnel or pyramid charts, labels are placed on the outside in a column.</span></span>  
  
-   <span data-ttu-id="c874e-107">在圓形圖上，標籤會位於圓形圖上的個別配量內部。</span><span class="sxs-lookup"><span data-stu-id="c874e-107">On pie charts, labels are placed inside the individual slices on a pie chart.</span></span>  
  
-   <span data-ttu-id="c874e-108">在橫條圖上，標籤會位於代表資料點的橫條外部。</span><span class="sxs-lookup"><span data-stu-id="c874e-108">On bar charts, labels are placed outside of the bars that represent data points.</span></span>  
  
-   <span data-ttu-id="c874e-109">在極座標圖上，標籤會位於代表資料點的圓形區域外部。</span><span class="sxs-lookup"><span data-stu-id="c874e-109">On polar charts, labels are placed outside of the circular area that represents data points.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-position-of-point-labels-in-a-pie-chart"></a><span data-ttu-id="c874e-110">若要變更點標籤在圓形圖內的位置</span><span class="sxs-lookup"><span data-stu-id="c874e-110">To change the position of point labels in a Pie chart</span></span>  
  
1.  <span data-ttu-id="c874e-111">建立圓形圖。</span><span class="sxs-lookup"><span data-stu-id="c874e-111">Create a pie chart.</span></span>  
  
2.  <span data-ttu-id="c874e-112">在設計介面上，以滑鼠右鍵按一下圖表，然後選取 [顯示資料標籤]  。</span><span class="sxs-lookup"><span data-stu-id="c874e-112">On the design surface, right-click the chart and select **Show Data Labels**.</span></span>  
  
3.  <span data-ttu-id="c874e-113">開啟 [屬性] 窗格。</span><span class="sxs-lookup"><span data-stu-id="c874e-113">Open the Properties pane.</span></span> <span data-ttu-id="c874e-114">在 [檢視]  索引標籤上，按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="c874e-114">On the **View** tab, click **Properties**.</span></span>  
  
4.  <span data-ttu-id="c874e-115">在設計介面上，按一下圖表。</span><span class="sxs-lookup"><span data-stu-id="c874e-115">On the design surface, click the chart.</span></span> <span data-ttu-id="c874e-116">圖表的屬性會顯示在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="c874e-116">The properties for the chart are displayed in the Properties pane.</span></span>  
  
5.  <span data-ttu-id="c874e-117">在 [一般]  區段中，展開 [CustomAttributes]  節點。</span><span class="sxs-lookup"><span data-stu-id="c874e-117">In the **General** section, expand the **CustomAttributes** node.</span></span> <span data-ttu-id="c874e-118">圓形圖的屬性清單隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="c874e-118">A list of attributes for the pie chart is displayed.</span></span>  
  
6.  <span data-ttu-id="c874e-119">選取 PieLabelStyle 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="c874e-119">Select a value for the PieLabelStyle property.</span></span>  
  
### <a name="to-change-the-position-of-point-labels-in-a-funnel-or-pyramid-chart"></a><span data-ttu-id="c874e-120">變更點標籤在漏斗圖或金字塔圖內的位置</span><span class="sxs-lookup"><span data-stu-id="c874e-120">To change the position of point labels in a Funnel or Pyramid chart</span></span>  
  
1.  <span data-ttu-id="c874e-121">建立漏斗圖或金字塔圖。</span><span class="sxs-lookup"><span data-stu-id="c874e-121">Create a funnel or pyramid chart.</span></span>  
  
2.  <span data-ttu-id="c874e-122">在設計介面上，以滑鼠右鍵按一下圖表，然後選取 [顯示資料標籤]  。</span><span class="sxs-lookup"><span data-stu-id="c874e-122">On the design surface, right-click the chart and select **Show Data Labels**.</span></span>  
  
3.  <span data-ttu-id="c874e-123">開啟 [屬性] 窗格。</span><span class="sxs-lookup"><span data-stu-id="c874e-123">Open the Properties pane.</span></span> <span data-ttu-id="c874e-124">在 [檢視]  索引標籤上，按一下 [屬性] </span><span class="sxs-lookup"><span data-stu-id="c874e-124">On the **View** tab, click **Properties**</span></span>  
  
4.  <span data-ttu-id="c874e-125">在設計介面上，按一下圖表。</span><span class="sxs-lookup"><span data-stu-id="c874e-125">On the design surface, click the chart.</span></span> <span data-ttu-id="c874e-126">圖表的屬性會顯示在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="c874e-126">The properties for the chart are displayed in the Properties pane.</span></span>  
  
5.  <span data-ttu-id="c874e-127">在 [一般]  區段中，展開 [CustomAttributes]  節點。</span><span class="sxs-lookup"><span data-stu-id="c874e-127">In the **General** section, expand the **CustomAttributes** node.</span></span> <span data-ttu-id="c874e-128">漏斗圖的屬性清單隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="c874e-128">A list of attributes for the funnel chart is displayed.</span></span>  
  
6.  <span data-ttu-id="c874e-129">若為漏斗圖，請選取 FunnelLabelStyle 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="c874e-129">For a funnel chart, select a value for the FunnelLabelStyle property.</span></span> <span data-ttu-id="c874e-130">若為金字塔圖，請選取 PyramidLabelStyle 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="c874e-130">For a pyramid chart, select a value for the PyramidLabelStyle property.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c874e-131">當這個屬性設定為 `OutsideInColumn` 值時，標籤就會繪製在垂直直條中。</span><span class="sxs-lookup"><span data-stu-id="c874e-131">When this property is set to a value `OutsideInColumn`, the labels are drawn in a vertical column.</span></span> <span data-ttu-id="c874e-132">您無法變更直條的位置。</span><span class="sxs-lookup"><span data-stu-id="c874e-132">There is no way to change the position of the column.</span></span>  
  
### <a name="to-change-the-position-of-point-labels-in-a-bar-chart"></a><span data-ttu-id="c874e-133">若要變更點標籤在橫條圖內的位置</span><span class="sxs-lookup"><span data-stu-id="c874e-133">To change the position of point labels in a Bar chart</span></span>  
  
1.  <span data-ttu-id="c874e-134">建立橫條圖。</span><span class="sxs-lookup"><span data-stu-id="c874e-134">Create a bar chart.</span></span>  
  
2.  <span data-ttu-id="c874e-135">在設計介面上，以滑鼠右鍵按一下圖表，然後選取 [顯示資料標籤]  。</span><span class="sxs-lookup"><span data-stu-id="c874e-135">On the design surface, right-click the chart and select **Show Data Labels**.</span></span>  
  
3.  <span data-ttu-id="c874e-136">開啟 [屬性] 窗格。</span><span class="sxs-lookup"><span data-stu-id="c874e-136">Open the Properties pane.</span></span> <span data-ttu-id="c874e-137">在 [檢視]  索引標籤上，按一下 [屬性] </span><span class="sxs-lookup"><span data-stu-id="c874e-137">On the **View** tab, click **Properties**</span></span>  
  
4.  <span data-ttu-id="c874e-138">在設計介面上，按一下圖表。</span><span class="sxs-lookup"><span data-stu-id="c874e-138">On the design surface, click the chart.</span></span> <span data-ttu-id="c874e-139">圖表的屬性會顯示在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="c874e-139">The properties for the chart are displayed in the Properties pane.</span></span>  
  
5.  <span data-ttu-id="c874e-140">在 [一般]  區段中，展開 [CustomAttributes]  節點。</span><span class="sxs-lookup"><span data-stu-id="c874e-140">In the **General** section, expand the **CustomAttributes** node.</span></span> <span data-ttu-id="c874e-141">橫條圖的屬性清單隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="c874e-141">A list of attributes for the bar chart is displayed.</span></span>  
  
6.  <span data-ttu-id="c874e-142">選取 BarLabelStyle 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="c874e-142">Select a value for the BarLabelStyle property.</span></span>  
  
 <span data-ttu-id="c874e-143">當橫條標籤樣式設定為 `Outside` 時，只要圖表區域能夠容納，標籤就會位於橫條外部。</span><span class="sxs-lookup"><span data-stu-id="c874e-143">When the bar label style is set to `Outside`, the labels will be placed outside of the bar, as long as it fits in the chart area.</span></span> <span data-ttu-id="c874e-144">如果標籤無法位於橫條外部，但位於圖表區域內部，此標籤就會位於橫條內部最接近橫條結尾的位置。</span><span class="sxs-lookup"><span data-stu-id="c874e-144">If the label cannot be placed outside of the bar but inside of the chart area, the label is placed inside the bar at the position closest to the end of the bar.</span></span>  
  
### <a name="to-change-the-position-of-point-labels-in-an-area-column-line-or-scatter-chart"></a><span data-ttu-id="c874e-145">變更點標籤在區域圖、直條圖、折線圖或散佈圖內的位置</span><span class="sxs-lookup"><span data-stu-id="c874e-145">To change the position of point labels in an Area, Column, Line or Scatter chart</span></span>  
  
1.  <span data-ttu-id="c874e-146">建立區域圖、直條圖、折線圖或散佈圖。</span><span class="sxs-lookup"><span data-stu-id="c874e-146">Create an Area, Column, Line or Scatter chart.</span></span>  
  
2.  <span data-ttu-id="c874e-147">在設計介面上，以滑鼠右鍵按一下圖表，然後選取 [顯示資料標籤]  。</span><span class="sxs-lookup"><span data-stu-id="c874e-147">On the design surface, right-click the chart and select **Show Data Labels**.</span></span>  
  
3.  <span data-ttu-id="c874e-148">開啟 [屬性] 窗格。</span><span class="sxs-lookup"><span data-stu-id="c874e-148">Open the Properties pane.</span></span> <span data-ttu-id="c874e-149">在 [檢視]  索引標籤上，按一下 [屬性] </span><span class="sxs-lookup"><span data-stu-id="c874e-149">On the **View** tab, click **Properties**</span></span>  
  
4.  <span data-ttu-id="c874e-150">在設計介面上，按一下數列。</span><span class="sxs-lookup"><span data-stu-id="c874e-150">On the design surface, click the series.</span></span> <span data-ttu-id="c874e-151">數列的屬性會顯示在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="c874e-151">The properties for the series are displayed in the Properties pane.</span></span>  
  
5.  <span data-ttu-id="c874e-152">在 [資料]  區段中，展開 [DataPoint]  節點，然後展開 [Label]  節點。</span><span class="sxs-lookup"><span data-stu-id="c874e-152">In the **Data** section, expand the **DataPoint** node, then expand the **Label**node.</span></span>  
  
6.  <span data-ttu-id="c874e-153">選取 Position 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="c874e-153">Select a value for the Position property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c874e-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c874e-154">See Also</span></span>  
 <span data-ttu-id="c874e-155">[圓形圖 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c874e-155">[Pie Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c874e-156">[橫條圖 &#40;報表產生器及 SSRS&#41;](bar-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c874e-156">[Bar Charts &#40;Report Builder and SSRS&#41;](bar-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c874e-157">[格式化圖表上的軸標籤 &#40;報表產生器及 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c874e-157">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c874e-158">[將軸標籤格式化成日期或貨幣 &#40;報表產生器及 SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c874e-158">[Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c874e-159">[在圓形圖外部顯示資料點標籤 &#40;報表產生器及 SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c874e-159">[Display Data Point Labels Outside a Pie Chart &#40;Report Builder and SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c874e-160">格式化圖表上的資料點 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c874e-160">Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)  
  
  
