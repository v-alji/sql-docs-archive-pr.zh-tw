---
title: 極座標圖 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c9402d8f-202a-4cdf-949e-50f5b1d2b885
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b8c4dd9394fab3e076c4a714375954a616e081f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686773"
---
# <a name="polar-charts-report-builder-and-ssrs"></a><span data-ttu-id="eba3e-102">極座標圖 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="eba3e-102">Polar Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="eba3e-103">極座標圖是在 360 度的圓形上，依據類別目錄群組，將數列顯示為一組點。</span><span class="sxs-lookup"><span data-stu-id="eba3e-103">A polar chart displays a series as a set of points that are grouped by category on a 360-degree circle.</span></span> <span data-ttu-id="eba3e-104">這些值是以點的長度 (從圓心開始測量) 表示。</span><span class="sxs-lookup"><span data-stu-id="eba3e-104">Values are represented by the length of the point as measured from the center of the circle.</span></span> <span data-ttu-id="eba3e-105">從圓心到點的距離越遠，其值越大。</span><span class="sxs-lookup"><span data-stu-id="eba3e-105">The farther the point is from the center, the greater its value.</span></span> <span data-ttu-id="eba3e-106">類別目錄標籤會顯示在圖表的周長上。</span><span class="sxs-lookup"><span data-stu-id="eba3e-106">Category labels are displayed on the perimeter of the chart.</span></span> <span data-ttu-id="eba3e-107">如需如何將資料新增至極座標圖的詳細資訊，請參閱 [圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="eba3e-107">For more information on how to add data to a polar chart, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="eba3e-108">變化</span><span class="sxs-lookup"><span data-stu-id="eba3e-108">Variations</span></span>  
  
-   <span data-ttu-id="eba3e-109">**雷達圖**：</span><span class="sxs-lookup"><span data-stu-id="eba3e-109">**Radar chart**.</span></span> <span data-ttu-id="eba3e-110">雷達圖會將數列顯示為弧線或區域。</span><span class="sxs-lookup"><span data-stu-id="eba3e-110">A radar chart displays a series as a circular line or area.</span></span> <span data-ttu-id="eba3e-111">雷達圖不像極座標圖，不會根據極座標顯示資料。</span><span class="sxs-lookup"><span data-stu-id="eba3e-111">Unlike the polar chart, the radar chart does not display data in terms of polar coordinates.</span></span>  
  
## <a name="data-considerations-for-polar-charts"></a><span data-ttu-id="eba3e-112">極座標圖的資料考量</span><span class="sxs-lookup"><span data-stu-id="eba3e-112">Data Considerations for Polar Charts</span></span>  
  
-   <span data-ttu-id="eba3e-113">雷達圖適用於比較多個類別目錄資料的數列。</span><span class="sxs-lookup"><span data-stu-id="eba3e-113">The radar chart is useful for comparisons between multiple series of category data.</span></span>  
  
-   <span data-ttu-id="eba3e-114">極座標圖通常用於圖形的極線資料，其中每個資料點都是由角度和距離來決定。</span><span class="sxs-lookup"><span data-stu-id="eba3e-114">Polar charts are most commonly used to graph polar data, where each data point is determined by an angle and a distance.</span></span>  
  
-   <span data-ttu-id="eba3e-115">極座標圖無法與相同圖表區域中的其他任何圖表類型結合。</span><span class="sxs-lookup"><span data-stu-id="eba3e-115">Polar charts cannot be combined with any other chart type in the same chart area.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eba3e-116">範例</span><span class="sxs-lookup"><span data-stu-id="eba3e-116">Example</span></span>  
 <span data-ttu-id="eba3e-117">下列範例顯示如何使用雷達圖。</span><span class="sxs-lookup"><span data-stu-id="eba3e-117">The following example shows how a radar chart can be used.</span></span> <span data-ttu-id="eba3e-118">下表提供圖表的範例資料。</span><span class="sxs-lookup"><span data-stu-id="eba3e-118">The table below provides sample data for the chart.</span></span>  
  
|<span data-ttu-id="eba3e-119">名稱</span><span class="sxs-lookup"><span data-stu-id="eba3e-119">Name</span></span>|<span data-ttu-id="eba3e-120">Sales</span><span class="sxs-lookup"><span data-stu-id="eba3e-120">Sales</span></span>|  
|----------|-----------|  
|<span data-ttu-id="eba3e-121">灌木</span><span class="sxs-lookup"><span data-stu-id="eba3e-121">Shrubs</span></span>|<span data-ttu-id="eba3e-122">61</span><span class="sxs-lookup"><span data-stu-id="eba3e-122">61</span></span>|  
|<span data-ttu-id="eba3e-123">種子</span><span class="sxs-lookup"><span data-stu-id="eba3e-123">Seeds</span></span>|<span data-ttu-id="eba3e-124">78</span><span class="sxs-lookup"><span data-stu-id="eba3e-124">78</span></span>|  
|<span data-ttu-id="eba3e-125">燈泡</span><span class="sxs-lookup"><span data-stu-id="eba3e-125">Bulbs</span></span>|<span data-ttu-id="eba3e-126">60</span><span class="sxs-lookup"><span data-stu-id="eba3e-126">60</span></span>|  
|<span data-ttu-id="eba3e-127">樹木</span><span class="sxs-lookup"><span data-stu-id="eba3e-127">Trees</span></span>|<span data-ttu-id="eba3e-128">38</span><span class="sxs-lookup"><span data-stu-id="eba3e-128">38</span></span>|  
|<span data-ttu-id="eba3e-129">花朵</span><span class="sxs-lookup"><span data-stu-id="eba3e-129">Flowers</span></span>|<span data-ttu-id="eba3e-130">81</span><span class="sxs-lookup"><span data-stu-id="eba3e-130">81</span></span>|  
  
 <span data-ttu-id="eba3e-131">在此範例中，[名稱] 欄位放置在 [類別目錄群組] 區域中。</span><span class="sxs-lookup"><span data-stu-id="eba3e-131">In this example, the Name field is placed in the Category Groups area.</span></span> <span data-ttu-id="eba3e-132">[銷售量] 欄位放置在 [值] 區域中。</span><span class="sxs-lookup"><span data-stu-id="eba3e-132">The Sales field is placed in the Values area.</span></span> <span data-ttu-id="eba3e-133">當您放置 [銷售量] 欄位時，系統會自動彙總圖表的 [銷售量] 欄位。</span><span class="sxs-lookup"><span data-stu-id="eba3e-133">The Sales field is automatically aggregated for the chart when you drop it.</span></span> <span data-ttu-id="eba3e-134">雷達圖會根據 [銷售量] 欄位中的值個數，計算放置標籤的位置，例如，[銷售量] 欄位中包含 5 個值，因此會將標籤放置在圓形上 5 個等距離點的位置。</span><span class="sxs-lookup"><span data-stu-id="eba3e-134">The radar chart calculates where to place the labels based on the number of values in the Sales field, which contains five values and places labels at five equidistant points on a circle.</span></span> <span data-ttu-id="eba3e-135">如果 [銷售量] 欄位包含 3 個值，則會將標籤放置在圓形上 3 個等距離點的位置。</span><span class="sxs-lookup"><span data-stu-id="eba3e-135">If the Sales field contained three values, the labels would be placed at three equidistant points on a circle.</span></span>  
  
 <span data-ttu-id="eba3e-136">下圖根據呈現的資料，顯示雷達圖的範例。</span><span class="sxs-lookup"><span data-stu-id="eba3e-136">The following illustration shows an example of a radar chart based on the data presented.</span></span>  
  
 <span data-ttu-id="eba3e-137">![雷達圖](../media/rs-radarchart.gif "雷達圖")</span><span class="sxs-lookup"><span data-stu-id="eba3e-137">![Radar chart](../media/rs-radarchart.gif "Radar chart")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eba3e-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eba3e-138">See Also</span></span>  
 <span data-ttu-id="eba3e-139">[圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="eba3e-139">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="eba3e-140">[格式化圖表 &#40;報表產生器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="eba3e-140">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="eba3e-141">[圖表類型 &#40;報表產生器及 SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="eba3e-141">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="eba3e-142">[折線圖 &#40;報表產生器及 SSRS&#41;](line-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="eba3e-142">[Line Charts &#40;Report Builder and SSRS&#41;](line-charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="eba3e-143">圖表中的空白和 Null 資料點 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="eba3e-143">Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;</span></span>](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)  
  
  
