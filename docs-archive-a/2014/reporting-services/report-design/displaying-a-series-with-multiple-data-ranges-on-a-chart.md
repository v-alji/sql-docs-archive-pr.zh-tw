---
title: 在圖表上顯示具有多個資料範圍的數列 (報表產生器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 45da3d39-278e-4760-a4b3-9932c9547cf2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dfe378f3fb5aa50ddf02f95b2b4be04dd1ae6ac5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592443"
---
# <a name="displaying-a-series-with-multiple-data-ranges-on-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="34042-102">將包含多個資料範圍的數列顯示在圖表上 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="34042-102">Displaying a Series with Multiple Data Ranges on a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="34042-103">圖表將會使用數列的最小值和最大值來計算軸刻度。</span><span class="sxs-lookup"><span data-stu-id="34042-103">Chart will use the minimum and maximum values of a series to calculate the axis scale.</span></span> <span data-ttu-id="34042-104">當圖表上的數列包含一個以上的資料範圍時，資料點可能會變得模糊，而圖表上只能清楚看到幾個資料點。</span><span class="sxs-lookup"><span data-stu-id="34042-104">When a series on your chart contains more than one range of data, the data points can become obscured, and only a few data points to be seen easily on the chart.</span></span> <span data-ttu-id="34042-105">例如，假設您的報表顯示 30 天的期間內每天的銷售總額。</span><span class="sxs-lookup"><span data-stu-id="34042-105">For example, suppose a report displays daily sales totals over a period of 30 days.</span></span>  
  
 <span data-ttu-id="34042-106">![具有多個資料範圍的圖表](../media/rs-multipledatarangeschart.gif "具有多個資料範圍的圖表")</span><span class="sxs-lookup"><span data-stu-id="34042-106">![Chart with multiple data ranges](../media/rs-multipledatarangeschart.gif "Chart with multiple data ranges")</span></span>  
  
 <span data-ttu-id="34042-107">在這個月的大多數時間，銷售量都是在 10 和 40 之間。</span><span class="sxs-lookup"><span data-stu-id="34042-107">For most of the month, the sales are between 10 and 40.</span></span> <span data-ttu-id="34042-108">但是，有一個禮拜的促銷活動造成四月初的銷售量激增。</span><span class="sxs-lookup"><span data-stu-id="34042-108">However, a one-week sales marketing campaign has caused a sudden sales increase at the beginning of April.</span></span> <span data-ttu-id="34042-109">這樣的銷售資料變更會產生資料點的不平均分配，因此會降低圖表的整體可讀性。</span><span class="sxs-lookup"><span data-stu-id="34042-109">This change in sales data produces an uneven distribution of data points that reduces the overall readability of the chart.</span></span>  
  
 <span data-ttu-id="34042-110">有幾種不同的方式可提升可讀性：</span><span class="sxs-lookup"><span data-stu-id="34042-110">There are different ways to improve readability:</span></span>  
  
-   <span data-ttu-id="34042-111">**啟用刻度斷層**：</span><span class="sxs-lookup"><span data-stu-id="34042-111">**Enable scale breaks**.</span></span> <span data-ttu-id="34042-112">如果您的資料形成兩組或多組資料範圍，請使用刻度斷層來移除範圍之間的間隙。</span><span class="sxs-lookup"><span data-stu-id="34042-112">If your data forms two or more sets of data ranges, use a scale break to remove the gap between the ranges.</span></span> <span data-ttu-id="34042-113">刻度斷層是在繪圖區上繪製的一道區域線，代表數列中高低值之間的斷層。</span><span class="sxs-lookup"><span data-stu-id="34042-113">A scale break is a stripe drawn across the plotting area to denote a break between the high and low values of a series.</span></span>  
  
-   <span data-ttu-id="34042-114">**篩選掉不必要的值**：</span><span class="sxs-lookup"><span data-stu-id="34042-114">**Filter out unnecessary values**.</span></span> <span data-ttu-id="34042-115">如果您的資料點蓋住了圖表上所要顯示的重要資料範圍，請使用報表篩選移除不要的點。</span><span class="sxs-lookup"><span data-stu-id="34042-115">If you have data points that are obscuring the important data range to be displayed on the chart, remove the unwanted points using a report filter.</span></span> <span data-ttu-id="34042-116">如需如何在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中將篩選新增至圖表的詳細資訊，請參閱[新增資料集篩選、資料區篩選和群組篩選 &#40;報表產生器及 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="34042-116">For information on how to add a filter to the chart in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md).</span></span>  
  
-   <span data-ttu-id="34042-117">**將每一個資料範圍繪製成個別數列來進行多個數列的比較**：</span><span class="sxs-lookup"><span data-stu-id="34042-117">**Plot each data range as a separate series for multiple series comparison**.</span></span> <span data-ttu-id="34042-118">如果您的資料範圍超過兩個以上，請考慮將資料範圍分割成個別的數列。</span><span class="sxs-lookup"><span data-stu-id="34042-118">If you have more than two data ranges, consider separating the data ranges into separate series.</span></span> <span data-ttu-id="34042-119">如需詳細資訊，請參閱 [圖表上的多個數列 &#40;報表產生器及 SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md)：</span><span class="sxs-lookup"><span data-stu-id="34042-119">For more information, see [Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="displaying-multiple-data-ranges-using-scale-breaks"></a><span data-ttu-id="34042-120">使用刻度斷層顯示多個資料範圍</span><span class="sxs-lookup"><span data-stu-id="34042-120">Displaying Multiple Data Ranges Using Scale Breaks</span></span>  
 <span data-ttu-id="34042-121">當您啟用刻度斷層時，圖表會計算要將線條繪製到圖表上的何處。</span><span class="sxs-lookup"><span data-stu-id="34042-121">When you enable a scale break, the chart calculates where to draw a line across the chart.</span></span> <span data-ttu-id="34042-122">範圍之間必須有足夠的分隔位置，才能繪製刻度斷層。</span><span class="sxs-lookup"><span data-stu-id="34042-122">You must have sufficient separation between ranges to draw a scale break.</span></span> <span data-ttu-id="34042-123">根據預設，只有當至少圖表百分之 25 的資料範圍之間有分隔時，才可以加入刻度斷層。</span><span class="sxs-lookup"><span data-stu-id="34042-123">By default, a scale break can be added only if there is a separation between the data ranges of at least 25% of the chart.</span></span>  
  
 <span data-ttu-id="34042-124">![具有刻度斷層的圖表](../media/rs-multipledatarangeschart-scalebreak.gif "具有刻度斷層的圖表")</span><span class="sxs-lookup"><span data-stu-id="34042-124">![Chart with scale break](../media/rs-multipledatarangeschart-scalebreak.gif "Chart with scale break")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="34042-125">您無法指定刻度斷層在圖表上的放置位置。</span><span class="sxs-lookup"><span data-stu-id="34042-125">You cannot specify where to place a scale break on a chart.</span></span> <span data-ttu-id="34042-126">但是，您可以修改刻度斷層的計算方式，本主題稍後會加以描述。</span><span class="sxs-lookup"><span data-stu-id="34042-126">You can, however, modify how the scale break is calculated, described later in this topic.</span></span>  
  
 <span data-ttu-id="34042-127">如果您啟用刻度斷層，但是它並未出現，而且資料範圍之間確實有足夠的距離，此時您可以將 CollapsibleSpaceThreshold 屬性設定為小於 25 的值。</span><span class="sxs-lookup"><span data-stu-id="34042-127">If you enable a scale break but it does not appear, even though there is sufficient distance between the data ranges, you can set the CollapsibleSpaceThreshold property to a value less than 25.</span></span> <span data-ttu-id="34042-128">CollapsibleSpaceThreshold 會指定資料範圍之間所需之可摺疊空間的百分比。</span><span class="sxs-lookup"><span data-stu-id="34042-128">The CollapsibleSpaceThreshold specifies the percent of collapsible space required between the data ranges.</span></span> <span data-ttu-id="34042-129">如需詳細資訊，請參閱[將刻度斷層新增至圖表 &#40;報表產生器及 SSRS&#41;](add-scale-breaks-to-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="34042-129">For more information, see [Add Scale Breaks to a Chart &#40;Report Builder and SSRS&#41;](add-scale-breaks-to-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="34042-130">圖表最多可支援每個圖表五個刻度斷層；但是，顯示一個以上的刻度斷層可能會造成圖表無法讀取。</span><span class="sxs-lookup"><span data-stu-id="34042-130">Charts support up to five scale breaks per chart; however, displaying more than one scale break can cause the chart to become unreadable.</span></span> <span data-ttu-id="34042-131">如果您的資料範圍超過兩個以上，請考慮使用另一個方法來顯示這些資料。</span><span class="sxs-lookup"><span data-stu-id="34042-131">If you have more than two data ranges, consider using a different method for displaying this data.</span></span> <span data-ttu-id="34042-132">如需詳細資訊，請參閱 [圖表上的多個數列 &#40;報表產生器及 SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md)：</span><span class="sxs-lookup"><span data-stu-id="34042-132">For more information, see [Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
## <a name="unsupported-scale-break-scenarios"></a><span data-ttu-id="34042-133">不支援的刻度斷層案例</span><span class="sxs-lookup"><span data-stu-id="34042-133">Unsupported Scale Break Scenarios</span></span>  
 <span data-ttu-id="34042-134">下列圖表案例不支援刻度斷層：</span><span class="sxs-lookup"><span data-stu-id="34042-134">Scale breaks are not supported in the following chart scenarios:</span></span>  
  
-   <span data-ttu-id="34042-135">圖表具有立體功能。</span><span class="sxs-lookup"><span data-stu-id="34042-135">The chart is 3-D enabled.</span></span>  
  
-   <span data-ttu-id="34042-136">指定了對數值軸。</span><span class="sxs-lookup"><span data-stu-id="34042-136">A logarithmic value axis has been specified.</span></span>  
  
-   <span data-ttu-id="34042-137">已經明確設定值軸的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="34042-137">The value axis minimum or maximum has been explicitly set.</span></span>  
  
-   <span data-ttu-id="34042-138">圖表類型為極座標圖、雷達圖、圓形圖、環圈圖、漏斗圖、金字塔圖或任何堆疊圖表。</span><span class="sxs-lookup"><span data-stu-id="34042-138">The chart type is polar, radar, pie, doughnut, funnel, pyramid, or any stacked chart.</span></span>  
  
 <span data-ttu-id="34042-139">具有刻度斷層的圖表範例可從範例報表取得。</span><span class="sxs-lookup"><span data-stu-id="34042-139">An example of chart with scale breaks is available as a sample report.</span></span> <span data-ttu-id="34042-140">如需下載這個範例報表及其他項目的詳細資訊，請參閱 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][報表產生器與報表設計師範例報表](https://go.microsoft.com/fwlink/?LinkId=198283)：</span><span class="sxs-lookup"><span data-stu-id="34042-140">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34042-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34042-141">See Also</span></span>  
 <span data-ttu-id="34042-142">[圖表上的多個數列 &#40;報表產生器和 SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="34042-142">[Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="34042-143">[將圖表格式化 &#40;報表產生器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="34042-143">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="34042-144">[圖表中的3D、斜面和其他效果 &#40;報表產生器和 SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="34042-144">[3D, Bevel, and Other Effects in a Chart &#40;Report Builder and SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md) </span></span>  
 <span data-ttu-id="34042-145">[圖表 &#40;報表產生器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="34042-145">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="34042-146">[軸屬性對話方塊、軸選項 &#40;報表產生器和 SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="34042-146">[Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="34042-147">收集圓形圖上的小配量 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="34042-147">Collect Small Slices on a Pie Chart &#40;Report Builder and SSRS&#41;</span></span>](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  
