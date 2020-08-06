---
title: 直條圖 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ae8c138b-e356-4ad8-862c-a4a8d0c04149
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b6ebada49e65d44a2294228a3840bf4951140812
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710194"
---
# <a name="column-charts-report-builder-and-ssrs"></a><span data-ttu-id="692ab-102">Column Charts (Report Builder and SSRS)</span><span class="sxs-lookup"><span data-stu-id="692ab-102">Column Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="692ab-103">直條圖是依據類別目錄群組，將數列顯示為一組垂直線。</span><span class="sxs-lookup"><span data-stu-id="692ab-103">A column chart displays a series as a set of vertical bars that are grouped by category.</span></span> <span data-ttu-id="692ab-104">直條圖適合顯示一段時間的資料變更，或圖解項目之間的比較。</span><span class="sxs-lookup"><span data-stu-id="692ab-104">Column charts are useful for showing data changes over a period of time or for illustrating comparisons among items.</span></span> <span data-ttu-id="692ab-105">一般直條圖與橫條圖相當有關聯，後者會將數列顯示為一組水平橫條，而範圍直條圖則會將數列顯示為一組垂直線，其中包含各種起點與終點。</span><span class="sxs-lookup"><span data-stu-id="692ab-105">The plain column chart is closely related to the bar chart, which displays series as sets of horizontal bars, and the range column chart, which displays series as sets of vertical bars with varying beginning and end points.</span></span> <span data-ttu-id="692ab-106">如需詳細資訊，請參閱 [橫條圖 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md) 和 [範圍圖表 &#40;報表產生器及 SSRS&#41;](range-charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="692ab-106">For more information, see [Bar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) and [Range Charts &#40;Report Builder and SSRS&#41;](range-charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="692ab-107">直條圖非常適合這個資料，因為全部三個數列都共用一個共同的時間週期，以便進行有效的比較。</span><span class="sxs-lookup"><span data-stu-id="692ab-107">The column chart is well suited for this data because all three series share a common time period, allowing for valid comparisons to be made.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations-of-a-column-chart"></a><span data-ttu-id="692ab-108">直條圖的變化</span><span class="sxs-lookup"><span data-stu-id="692ab-108">Variations of a Column Chart</span></span>  
  
-   <span data-ttu-id="692ab-109">**堆疊**：</span><span class="sxs-lookup"><span data-stu-id="692ab-109">**Stacked**.</span></span> <span data-ttu-id="692ab-110">將多個數列垂直堆疊的直條圖。</span><span class="sxs-lookup"><span data-stu-id="692ab-110">A column chart where multiple series are stacked vertically.</span></span> <span data-ttu-id="692ab-111">如果您的圖表中只有一個數列，堆疊直條圖的顯示將與直條圖相同。</span><span class="sxs-lookup"><span data-stu-id="692ab-111">If there is only one series in your chart, the stacked column chart will display the same as a column chart.</span></span>  
  
-   <span data-ttu-id="692ab-112">**百分之百堆疊**：</span><span class="sxs-lookup"><span data-stu-id="692ab-112">**Percent stacked**.</span></span> <span data-ttu-id="692ab-113">將多個數列垂直堆疊以便百分之百符合圖表區域的直條圖。</span><span class="sxs-lookup"><span data-stu-id="692ab-113">A column chart where multiple series are stacked vertically to fit 100% of the chart area.</span></span> <span data-ttu-id="692ab-114">如果您的圖表中只有一個數列，所有直條圖都會百分之百符合圖表區域。</span><span class="sxs-lookup"><span data-stu-id="692ab-114">If there is only one series in your chart, all the column bars will fit to 100% of the chart area.</span></span>  
  
-   <span data-ttu-id="692ab-115">**立體群組**：</span><span class="sxs-lookup"><span data-stu-id="692ab-115">**3D clustered**.</span></span> <span data-ttu-id="692ab-116">以立體圖表的個別資料列顯示各個數列的直條圖。</span><span class="sxs-lookup"><span data-stu-id="692ab-116">A column chart that shows individual series in separate rows on a 3D chart.</span></span>  
  
-   <span data-ttu-id="692ab-117">**立體圓柱圖**：</span><span class="sxs-lookup"><span data-stu-id="692ab-117">**3D cylinder**.</span></span> <span data-ttu-id="692ab-118">其直條形狀類似立體圖表圓柱的直條圖。</span><span class="sxs-lookup"><span data-stu-id="692ab-118">A column chart whose bars are shaped like cylinders on a 3D chart.</span></span>  
  
-   <span data-ttu-id="692ab-119">`Histogram`.</span><span class="sxs-lookup"><span data-stu-id="692ab-119">`Histogram`.</span></span> <span data-ttu-id="692ab-120">圖表會執行計算，讓其直條以常態分佈排列的直條圖。</span><span class="sxs-lookup"><span data-stu-id="692ab-120">A column chart which the chart calculates so that its bars are arranged in a normal distribution.</span></span>  
  
-   <span data-ttu-id="692ab-121">`Pareto`.</span><span class="sxs-lookup"><span data-stu-id="692ab-121">`Pareto`.</span></span> <span data-ttu-id="692ab-122">其直條從高而低排列的直條圖。</span><span class="sxs-lookup"><span data-stu-id="692ab-122">A column chart whose bars are arranged from highest to lowest.</span></span>  
  
## <a name="data-considerations-for-a-column-chart"></a><span data-ttu-id="692ab-123">直條圖的資料考量</span><span class="sxs-lookup"><span data-stu-id="692ab-123">Data Considerations for a Column Chart</span></span>  
  
-   <span data-ttu-id="692ab-124">橫條圖與直條圖通常用於顯示群組之間的比較。</span><span class="sxs-lookup"><span data-stu-id="692ab-124">Bar and column charts are most commonly used to show comparisons between groups.</span></span> <span data-ttu-id="692ab-125">如果在圖表上出現三個以上的數列，請考慮使用堆疊橫條圖或直條圖。</span><span class="sxs-lookup"><span data-stu-id="692ab-125">If more than three series are present on the chart, consider using a stacked bar or column chart.</span></span> <span data-ttu-id="692ab-126">如果在圖表上有多個數列，您也可以將堆疊橫條圖或直條圖收集到多個群組中。</span><span class="sxs-lookup"><span data-stu-id="692ab-126">You can also collect stacked bar or column charts into multiple groups if you have several series on your chart.</span></span> <span data-ttu-id="692ab-127">如需詳細資訊，請參閱[橫條圖 &#40;報表產生器和 SSRS&#41;](charts-report-builder-and-ssrs.md)和*直條圖*。</span><span class="sxs-lookup"><span data-stu-id="692ab-127">For more information, see [Bar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) and *Column Charts*.</span></span>  
  
-   <span data-ttu-id="692ab-128">在直條圖中，用於水平顯示類別目錄軸標籤的空間較少。</span><span class="sxs-lookup"><span data-stu-id="692ab-128">In a column chart, you have less space for category axis labels to display horizontally.</span></span> <span data-ttu-id="692ab-129">如果您的類別目錄標籤比較長，請考慮使用橫條圖，或變更標籤的旋轉角度。</span><span class="sxs-lookup"><span data-stu-id="692ab-129">If you have longer category labels, consider using a bar chart or changing the rotation angle of the label.</span></span>  
  
-   <span data-ttu-id="692ab-130">您可以在直條圖的個別直條上加入特殊的繪製樣式來增加其視覺效果。</span><span class="sxs-lookup"><span data-stu-id="692ab-130">You can add special drawing styles to the individual bars on a column chart to increase its visual impact.</span></span> <span data-ttu-id="692ab-131">繪製樣式包括楔形、浮凸、圓柱及深淺。</span><span class="sxs-lookup"><span data-stu-id="692ab-131">Drawing styles include wedge, emboss, cylinder and light-to-dark.</span></span> <span data-ttu-id="692ab-132">這些效果的設計可以改善平面圖表的外觀。</span><span class="sxs-lookup"><span data-stu-id="692ab-132">These effects are designed to improve the appearance of your 2D chart.</span></span> <span data-ttu-id="692ab-133">如果要使用立體圖表，您仍然可以套用繪製樣式，但是可能不會有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="692ab-133">If you are using a 3D chart, the drawing styles will still be applied, but may not have the same effect.</span></span> <span data-ttu-id="692ab-134">如需如何將繪製樣式加入橫條圖的詳細資訊，請參閱 [將斜面、浮凸與紋理樣式加入至圖表 &#40;報表產生器及 SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="692ab-134">For more information about how to add a drawing style to a bar chart, see [Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md).</span></span>  
  
-   <span data-ttu-id="692ab-135">直條圖的特點是，可以將您的圖表顯示為長條圖或帕累托圖。</span><span class="sxs-lookup"><span data-stu-id="692ab-135">Unique to column charts is the ability to show your chart as a histogram or Pareto chart.</span></span> <span data-ttu-id="692ab-136">若要這麼做，請將屬性視窗中的 ShowColumnAs 屬性設定為 `Histogram` 或 `Pareto` `true` 。</span><span class="sxs-lookup"><span data-stu-id="692ab-136">To do so, set the ShowColumnAs property to `Histogram` or `Pareto` in the Properties window to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="692ab-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="692ab-137">See Also</span></span>  
 <span data-ttu-id="692ab-138">[圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="692ab-138">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="692ab-139">[圖表類型 &#40;報表產生器及 SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="692ab-139">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="692ab-140">[橫條圖 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="692ab-140">[Bar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="692ab-141">[範圍圖表 &#40;報表產生器及 SSRS&#41;](range-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="692ab-141">[Range Charts &#40;Report Builder and SSRS&#41;](range-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="692ab-142">[教學課程：將橫條圖新增至報表 &#40;報表產生器&#41;](../tutorial-add-a-bar-chart-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="692ab-142">[Tutorial: Add a Bar Chart to Your Report &#40;Report Builder&#41;](../tutorial-add-a-bar-chart-to-your-report-report-builder.md) </span></span>  
 [<span data-ttu-id="692ab-143">圖表中的空白和 Null 資料點 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="692ab-143">Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;</span></span>](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)  
  
  
