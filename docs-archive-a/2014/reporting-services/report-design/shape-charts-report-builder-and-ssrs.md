---
title: 形狀圖 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4b8404c1-aa89-4350-8bd6-203bc0446ee4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c8940f23c0c2b1fdabadec62de4c214c98d60b1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596488"
---
# <a name="shape-charts-report-builder-and-ssrs"></a><span data-ttu-id="88235-102">形狀圖 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="88235-102">Shape Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="88235-103">形狀圖會將值資料顯示為整體所佔的百分比。</span><span class="sxs-lookup"><span data-stu-id="88235-103">A shape chart displays value data as percentages of a whole.</span></span> <span data-ttu-id="88235-104">形狀圖通常用於顯示集合中不同值之間成比例的比較。</span><span class="sxs-lookup"><span data-stu-id="88235-104">Shape charts are typically used to show proportional comparisons between different values in a set.</span></span> <span data-ttu-id="88235-105">類別目錄是以個別的形狀區段表示。</span><span class="sxs-lookup"><span data-stu-id="88235-105">Categories are represented by individual segments of the shape.</span></span> <span data-ttu-id="88235-106">區段的大小取決於值。</span><span class="sxs-lookup"><span data-stu-id="88235-106">The size of the segment is determined by the value.</span></span> <span data-ttu-id="88235-107">形狀圖在用途上類似於圓形圖，差別在於後者排序類別目錄時是從最大到最小。</span><span class="sxs-lookup"><span data-stu-id="88235-107">Shape charts are similar in use to pie charts, except that they order categories from largest to smallest.</span></span>  
  
 <span data-ttu-id="88235-108">漏斗圖會將值顯示為逐漸減少的比例。</span><span class="sxs-lookup"><span data-stu-id="88235-108">A funnel chart displays values as progressively decreasing proportions.</span></span> <span data-ttu-id="88235-109">區域的大小取決於所有值總計中所佔百分比的數列值。</span><span class="sxs-lookup"><span data-stu-id="88235-109">The size of the area is determined by the series value as a percentage of the total of all values.</span></span> <span data-ttu-id="88235-110">例如，您可能會使用漏斗圖來顯示網站訪客的趨勢。</span><span class="sxs-lookup"><span data-stu-id="88235-110">For example, you might use a funnel chart to display Web site visitor trends.</span></span> <span data-ttu-id="88235-111">漏斗圖在頂端可能會顯示一個寬廣的區域，表示訪客點擊首頁的次數，而其他區域在比例上會比較小。</span><span class="sxs-lookup"><span data-stu-id="88235-111">It is likely that the funnel chart will display a wide area at the top, indicating visitor page hits to the homepage, and the other areas will be proportionally smaller.</span></span> <span data-ttu-id="88235-112">如需如何將資料加入漏斗圖中的詳細資訊，請參閱 [圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="88235-112">For more information about how to add data to a funnel chart, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="88235-113">下圖顯示漏斗圖的範例。</span><span class="sxs-lookup"><span data-stu-id="88235-113">The following illustration shows an example of a funnel chart.</span></span>  
  
 <span data-ttu-id="88235-114">![漏斗圖](../media/rs-funnelchart.gif "漏斗圖")</span><span class="sxs-lookup"><span data-stu-id="88235-114">![Funnel chart](../media/rs-funnelchart.gif "Funnel chart")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="88235-115">變化</span><span class="sxs-lookup"><span data-stu-id="88235-115">Variations</span></span>  
  
-   <span data-ttu-id="88235-116">**金字塔圖**：</span><span class="sxs-lookup"><span data-stu-id="88235-116">**Pyramid**.</span></span> <span data-ttu-id="88235-117">金字塔圖會顯示成比例的資料，讓圖表看起來像金字塔一樣。</span><span class="sxs-lookup"><span data-stu-id="88235-117">A pyramid chart displays proportional data so that the chart looks like a pyramid.</span></span>  
  
## <a name="data-considerations-for-shape-charts"></a><span data-ttu-id="88235-118">形狀圖的資料考量</span><span class="sxs-lookup"><span data-stu-id="88235-118">Data Considerations for Shape Charts</span></span>  
  
-   <span data-ttu-id="88235-119">形狀圖因為其視覺效果而在報表上相當普遍。</span><span class="sxs-lookup"><span data-stu-id="88235-119">Shape charts are popular in reports because of their visual impact.</span></span> <span data-ttu-id="88235-120">不過，形狀圖是非常簡化的圖表類型，在表示資料時可能不是最適合。</span><span class="sxs-lookup"><span data-stu-id="88235-120">However, shape charts are a very simplified chart type that may not best represent your data.</span></span> <span data-ttu-id="88235-121">只有在資料已彙整為七個資料點 (含) 以下後，才考慮使用形狀圖。</span><span class="sxs-lookup"><span data-stu-id="88235-121">Consider using a shape chart only once the data has been aggregated to seven data points or less.</span></span> <span data-ttu-id="88235-122">一般而言，使用形狀圖只能在每個資料區域顯示一個類別目錄。</span><span class="sxs-lookup"><span data-stu-id="88235-122">In general, use the shape chart to display only one category per data region.</span></span>  
  
-   <span data-ttu-id="88235-123">形狀圖會將每個資料群組顯示為圖表的個別區段。</span><span class="sxs-lookup"><span data-stu-id="88235-123">Shape charts display each data group as a separate segment of the chart.</span></span> <span data-ttu-id="88235-124">您至少必須加入一個資料欄位和一個類別目錄欄位。</span><span class="sxs-lookup"><span data-stu-id="88235-124">You must add at least one data field and one category field.</span></span> <span data-ttu-id="88235-125">如果將一個以上的資料欄位加入到形狀圖中，形狀圖將會在相同的圖表中同時顯示兩個資料欄位。</span><span class="sxs-lookup"><span data-stu-id="88235-125">If more than one data field is added to a shape chart, the shape chart will display both data fields in the same chart.</span></span>  
  
-   <span data-ttu-id="88235-126">形狀圖在按照排序順序顯示成比例的百分比時最有效。</span><span class="sxs-lookup"><span data-stu-id="88235-126">Shape charts are most effective for showing proportional percentages in sorted order.</span></span> <span data-ttu-id="88235-127">不過，為了維持一致性，圖表預設不會排序資料集中的值。</span><span class="sxs-lookup"><span data-stu-id="88235-127">However, in order to maintain consistency, the chart does not sort the values in your dataset by default.</span></span> <span data-ttu-id="88235-128">若要最精確地將資料表示成漏斗圖或金字塔圖，請考慮從最高至最低排序值。</span><span class="sxs-lookup"><span data-stu-id="88235-128">Consider ordering your values from highest to lowest to most accurately represent your data as a funnel or a pyramid.</span></span> <span data-ttu-id="88235-129">如需詳細資訊，請參閱 [篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)(將互動式排序加入資料表或矩陣 (報表產生器及 SSRS))。</span><span class="sxs-lookup"><span data-stu-id="88235-129">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="88235-130">計算比例時，Null、空值、負值與零值沒有效用。</span><span class="sxs-lookup"><span data-stu-id="88235-130">Null, empty, negative and zero values have no effect when calculating ratios.</span></span> <span data-ttu-id="88235-131">因此，這些值不會顯示在形狀圖上。</span><span class="sxs-lookup"><span data-stu-id="88235-131">For this reason, these values are not shown on a shape chart.</span></span> <span data-ttu-id="88235-132">如果您要在圖表上，以視覺方式表示這些值的類型，請將圖表類型變更為形狀圖之外的其他類型。</span><span class="sxs-lookup"><span data-stu-id="88235-132">If you want to visually indicate these types of values on your chart, change the chart type to be something other than a shape chart.</span></span> <span data-ttu-id="88235-133">如需如何將空點加入非形狀圖的詳細資訊，請參閱[將空點加入圖表 &#40;報表產生器和 SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="88235-133">For more information about how to add empty points to a non-shape chart, see [Add Empty Points to the Chart &#40;Report Builder and SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="88235-134">如果您要在形狀圖上使用自訂調色盤定義自己的色彩，請確認您的調色盤上有足夠的色彩，才能以其獨特的色彩反白顯示每個資料點。</span><span class="sxs-lookup"><span data-stu-id="88235-134">If you are defining your own colors on a shape chart using a custom palette, be sure that you have enough colors in your palette to highlight each data point with its own unique color.</span></span> <span data-ttu-id="88235-135">如需詳細資訊，請參閱 [設定圖表上數列色彩的格式 &#40;報表產生器及 SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="88235-135">For more information, see [Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="88235-136">形狀圖不像其他所有的圖表類型，它會在其圖例中顯示個別的資料點，而不會顯示個別的數列。</span><span class="sxs-lookup"><span data-stu-id="88235-136">Unlike all other chart types, a shape chart will display individual data points, and not individual series, in its legend.</span></span>  
  
-   <span data-ttu-id="88235-137">漏斗圖會忽略值和類別目錄軸的設定。</span><span class="sxs-lookup"><span data-stu-id="88235-137">Settings for the value and category axis are ignored for funnel charts.</span></span> <span data-ttu-id="88235-138">如果您有多個類別目錄或序列群組，則群組標籤會在圖表圖例中顯示。</span><span class="sxs-lookup"><span data-stu-id="88235-138">If you have multiple category or series groups, the group labels are displayed in the chart legend.</span></span>  
  
-   <span data-ttu-id="88235-139">形狀圖類型無法與相同圖表區域中的其他任何圖表類型結合。</span><span class="sxs-lookup"><span data-stu-id="88235-139">Shape chart types cannot be combined with any other chart type in the same chart area.</span></span> <span data-ttu-id="88235-140">如果您必須顯示形狀圖顯示之資料以及其他圖表類型顯示之資料間的比較，您必須加入另一個圖表區域。</span><span class="sxs-lookup"><span data-stu-id="88235-140">If you have to show comparisons between data displayed on a shape chart, and data displayed on another chart type, you will need to add a second chart area.</span></span>  
  
-   <span data-ttu-id="88235-141">加入立體效果會顯著改善形狀圖類型的整體外觀。</span><span class="sxs-lookup"><span data-stu-id="88235-141">Adding 3-D effects significantly improves the overall appearance of a shape chart type.</span></span>  
  
-   <span data-ttu-id="88235-142">您可以在圓形圖和環圈圖上套用其他繪製樣式來增加視覺效果。</span><span class="sxs-lookup"><span data-stu-id="88235-142">You can apply additional drawing styles to pie and doughnut charts for increased visual impact.</span></span> <span data-ttu-id="88235-143">如需詳細資訊，請參閱[格式化圖表上的數列色彩 &#40;報表產生器及 SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="88235-143">See [Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88235-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88235-144">See Also</span></span>  
 <span data-ttu-id="88235-145">[圖表 &#40;報表產生器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="88235-145">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="88235-146">[將圖表格式化 &#40;報表產生器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="88235-146">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="88235-147">[圖表中的空白和 Null 資料點 &#40;報表產生器和 SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="88235-147">[Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="88235-148">圓形圖 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="88235-148">Pie Charts &#40;Report Builder and SSRS&#41;</span></span>](pie-charts-report-builder-and-ssrs.md)  
  
  
