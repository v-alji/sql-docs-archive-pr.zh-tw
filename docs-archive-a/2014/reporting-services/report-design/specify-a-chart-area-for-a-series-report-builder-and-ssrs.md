---
title: 為數列指定圖表區域 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10157"
- sql12.rtp.rptdesigner.chartareaproperties.alignment.f1
ms.assetid: dc3c365b-c263-402a-bf6f-c2a7081db073
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 483bc6d2fa4aa079c95e9dbd03e18c71d7b13abf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585017"
---
# <a name="specify-a-chart-area-for-a-series-report-builder-and-ssrs"></a><span data-ttu-id="6e6e4-102">為數列指定圖表區域 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="6e6e4-102">Specify a Chart Area for a Series (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6e6e4-103">此圖表是最上層的容器，其中包含外框、圖表標題和圖例。</span><span class="sxs-lookup"><span data-stu-id="6e6e4-103">The chart is the top-level container that includes the outer border, the chart title, and the legend.</span></span> <span data-ttu-id="6e6e4-104">依預設，圖表包含一個預設的圖表區域。</span><span class="sxs-lookup"><span data-stu-id="6e6e4-104">By default, the chart contains one default chart area.</span></span> <span data-ttu-id="6e6e4-105">在圖表介面上看不到圖表區域，但是您可以將圖表區域視為僅包含軸標籤、軸標題，以及一或多個數列之繪圖區的容器。</span><span class="sxs-lookup"><span data-stu-id="6e6e4-105">The chart area is not visible on the chart surface, but you can think of the chart area as a container that encompasses only the axis labels, the axis title and the plotting area of one or more series.</span></span> <span data-ttu-id="6e6e4-106">下圖顯示單一圖表內圖表區域的概念。</span><span class="sxs-lookup"><span data-stu-id="6e6e4-106">The following illustration shows the concept of chart areas within a single chart.</span></span>  
  
 <span data-ttu-id="6e6e4-107">![顯示圖表區域的圖表](../media/chartareasdiagram.gif "顯示圖表區域的圖表")</span><span class="sxs-lookup"><span data-stu-id="6e6e4-107">![Shows a diagram of a chart area](../media/chartareasdiagram.gif "Shows a diagram of a chart area")</span></span>  
  
 <span data-ttu-id="6e6e4-108">依預設，所有數列都會加入到預設的圖表區域中。</span><span class="sxs-lookup"><span data-stu-id="6e6e4-108">By default, all series are added to the default chart area.</span></span> <span data-ttu-id="6e6e4-109">使用區域圖、直條圖、折線圖和散佈圖時，這些數列的任何組合都可以顯示在相同的圖表區域中。</span><span class="sxs-lookup"><span data-stu-id="6e6e4-109">When using area, column, line, and scatter charts, any combination of these series can be displayed on the same chart area.</span></span> <span data-ttu-id="6e6e4-110">如果您在相同的圖表區域中有數個數列，則會降低圖表的可讀性。</span><span class="sxs-lookup"><span data-stu-id="6e6e4-110">If you have several series in the same chart area, the readability of the chart is reduced.</span></span> <span data-ttu-id="6e6e4-111">您可能想要將圖表類型分為數個圖表區域。</span><span class="sxs-lookup"><span data-stu-id="6e6e4-111">You may want to separate the chart types into multiple chart areas.</span></span> <span data-ttu-id="6e6e4-112">使用多個圖表區域將會增加可讀性，讓比較更為容易。</span><span class="sxs-lookup"><span data-stu-id="6e6e4-112">Using multiple chart areas will increase readability for easier comparisons.</span></span> <span data-ttu-id="6e6e4-113">例如，價格-數量股票圖通常有不同範圍的值，但是可以在相同一段時間的價格和數量資料之間進行比較。</span><span class="sxs-lookup"><span data-stu-id="6e6e4-113">For example, price-volume stock charts often have different ranges of values, but comparisons can be made between the price and volume data over the same period of time.</span></span>  
  
 <span data-ttu-id="6e6e4-114">長條圖、極座標圖或形狀圖數列僅能與相同圖表區域中相同圖表類型的數列結合。</span><span class="sxs-lookup"><span data-stu-id="6e6e4-114">The bar, polar, or shape series can only be combined with series of the same chart types in the same chart area.</span></span> <span data-ttu-id="6e6e4-115">如果您使用的是極座標圖或形狀圖，請考慮將個別的圖表資料區域用於您要顯示的每個欄位。</span><span class="sxs-lookup"><span data-stu-id="6e6e4-115">If you are using a Polar or Shape chart, consider using a separate chart data region for each field that you wish to show.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-associate-a-series-with-a-new-chart-area"></a><span data-ttu-id="6e6e4-116">讓數列與新圖表區域產生關聯</span><span class="sxs-lookup"><span data-stu-id="6e6e4-116">To associate a series with a new chart area</span></span>  
  
1.  <span data-ttu-id="6e6e4-117">以滑鼠右鍵按一下圖表的任何位置，然後選取 [新增新的圖表區域]  。</span><span class="sxs-lookup"><span data-stu-id="6e6e4-117">Right-click anywhere on the chart and select **Add New Chart Area**.</span></span> <span data-ttu-id="6e6e4-118">新的空白圖表區域就會出現在圖表上。</span><span class="sxs-lookup"><span data-stu-id="6e6e4-118">A new, blank chart area appears on the chart.</span></span>  
  
2.  <span data-ttu-id="6e6e4-119">以滑鼠右鍵按一下圖表上的數列，或者在 [圖表資料] 窗格以滑鼠右鍵按一下適當區域中的資料欄位，然後按一下 [數列屬性]  。</span><span class="sxs-lookup"><span data-stu-id="6e6e4-119">Right-click the series on the chart or right-click a series or data field in the appropriate area in the Chart Data pane, and then click **Series Properties**.</span></span>  
  
3.  <span data-ttu-id="6e6e4-120">在 **[軸和圖表區域]** 中，選取您要數列顯示在其中的圖表區域。</span><span class="sxs-lookup"><span data-stu-id="6e6e4-120">In **Axes and Chart Areas**, select the chart area that you want the series to be shown in.</span></span>  
  
4.  <span data-ttu-id="6e6e4-121">(選擇性) 垂直對齊圖表區域。</span><span class="sxs-lookup"><span data-stu-id="6e6e4-121">(Optional) Align the chart areas vertically.</span></span> <span data-ttu-id="6e6e4-122">若要這樣做，以滑鼠右鍵按一下圖表，然後選取 [圖表區域屬性]  。</span><span class="sxs-lookup"><span data-stu-id="6e6e4-122">To do this, right-click the chart and select **Chart Area Properties**.</span></span> <span data-ttu-id="6e6e4-123">在 **[對齊]** 中，選取您要與所選圖表區域對齊的另一個圖表區域。</span><span class="sxs-lookup"><span data-stu-id="6e6e4-123">In **Alignment**, select another chart area that you want to align the selected chart area with.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e6e4-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e6e4-124">See Also</span></span>  
 <span data-ttu-id="6e6e4-125">[圖表上的多個數列 &#40;報表產生器及 SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6e6e4-125">[Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6e6e4-126">[格式化圖表上的資料點 &#40;報表產生器和 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6e6e4-126">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6e6e4-127">[使用調色盤定義圖表的色彩 &#40;報表產生器及 SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6e6e4-127">[Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6e6e4-128">[極座標圖 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6e6e4-128">[Polar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6e6e4-129">[形狀圖 &#40;報表產生器及 SSRS&#41;](shape-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6e6e4-129">[Shape Charts &#40;Report Builder and SSRS&#41;](shape-charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6e6e4-130">圓形圖 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6e6e4-130">Pie Charts &#40;Report Builder and SSRS&#41;</span></span>](pie-charts-report-builder-and-ssrs.md)  
  
  
