---
title: 將圖表格式化 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10214"
- sql12.rtp.rptdesigner.calculatedseriesproperties.fill.f1
- sql12.rtp.rptdesigner.serieslabelproperties.fill.f1
- sql12.rtp.rptdesigner.legendproperties.fill.f1
- "10149"
- sql12.rtp.rptdesigner.seriesproperties.shadow.f1
- sql12.rtp.rptdesigner.seriesproperties.markers.f1
- "10255"
- sql12.rtp.rptdesigner.charttitleproperties.fill.f1
- "10154"
- "10170"
- "10173"
- sql12.rtp.rptdesigner.seriesproperties.fill.f1
- "10169"
- "10158"
- sql12.rtp.rptdesigner.chartareaproperties.fill.f1
- sql12.rtp.rptdesigner.charttitleproperties.shadow.f1
- "10246"
- "10150"
- sql12.rtp.rptdesigner.calculatedseriesproperties.borders.f1
- sql12.rtp.rptdesigner.chartproperties.fill.f1
- "10159"
- sql12.rtp.rptdesigner.majorgridlineproperties.gridlineoptions.f1
- "10160"
- sql12.rtp.rptdesigner.serieslabelproperties.font.f1
- "10182"
- "10163"
- "10164"
- "10253"
- "10216"
- "10171"
- "10257"
- sql12.rtp.rptdesigner.chartareaproperties.border.f1
- sql12.rtp.rptdesigner.calculatedseriesproperties.shadow.f1
- sql12.rtp.rptdesigner.chartproperties.border.f1
- sql12.rtp.rptdesigner.minorgridlineproperties.gridlineoptions.f1
- sql12.rtp.rptdesigner.chartareaproperties.shadow.f1
- sql12.rtp.rptdesigner.charttitleproperties.borders.f1
- sql12.rtp.rptdesigner.charttitleproperties.font.f1
- "10247"
ms.assetid: d3984300-c766-42f8-b7c4-863123d67c99
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af164d4db9b6439f0634d113652b95939827b0f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594386"
---
# <a name="formatting-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="f6687-102">格式化圖表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f6687-102">Formatting a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f6687-103">在定義了圖表的資料且資料也以所要的方式顯示之後，您就可以加入格式設定，以改善整體外觀並強調關鍵的資料點。</span><span class="sxs-lookup"><span data-stu-id="f6687-103">After you have defined the data for your chart and it is appearing the way you want, you can add formatting to improve the overall appearance and highlight key data points.</span></span> <span data-ttu-id="f6687-104">您可以從 [屬性] 對話方塊修改最常見的格式設定選項，當您以滑鼠右鍵按一下圖表元素以顯示其快速鍵功能表時，此對話方塊就會顯示。</span><span class="sxs-lookup"><span data-stu-id="f6687-104">The most common formatting options can be modified from the Properties dialog box that are found when you right-click a chart element to display its shortcut menu.</span></span> <span data-ttu-id="f6687-105">每個圖表元素都有它自己的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f6687-105">Each chart element has its own dialog box.</span></span> <span data-ttu-id="f6687-106">如需圖表元素的詳細資訊，請參閱 [圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f6687-106">For more information about chart elements, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="f6687-107">所有與圖表相關的屬性都位在 [屬性] 窗格中，但其中許多屬性也可以從對話方塊進行設定。</span><span class="sxs-lookup"><span data-stu-id="f6687-107">All properties that relate to the chart are located in the Properties pane, but many of these properties can also be set from a dialog box.</span></span> <span data-ttu-id="f6687-108">如果要格式化數列，可以使用自訂屬性 (attribute) 來指定數列特定的屬性 (property)，您只能在 [屬性]\(property) 窗格的 **CustomAttributes** 屬性類別目錄中才能找到這些自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="f6687-108">If you are formatting the series, you can specify series-specific properties using custom attributes, which can only be found in the **CustomAttributes** category of properties, located in the Properties pane.</span></span>  
  
 <span data-ttu-id="f6687-109">若要使用最少的步驟有效地進行圖表的格式化，請變更預設的框線樣式、調色盤和繪製樣式。</span><span class="sxs-lookup"><span data-stu-id="f6687-109">To effectively format the chart using a minimal number of steps, change the default border style, palette and drawing style.</span></span> <span data-ttu-id="f6687-110">這三個功能會在圖表上產生最多的可見變更。</span><span class="sxs-lookup"><span data-stu-id="f6687-110">These three features produce the largest visible change on the chart.</span></span> <span data-ttu-id="f6687-111">繪製樣式只適用於圓形圖、環圈圖、橫條圖和直條圖。</span><span class="sxs-lookup"><span data-stu-id="f6687-111">Drawing styles are only applicable to pie, doughnut, bar and column charts.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a><span data-ttu-id="f6687-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="f6687-112">In This Section</span></span>  
 [<span data-ttu-id="f6687-113">設定圖表上數列色彩的格式 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f6687-113">Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)  
 <span data-ttu-id="f6687-114">討論如何使用調色盤定義顏色、如何定義自己的調色盤，以及如何根據運算式定義顏色。</span><span class="sxs-lookup"><span data-stu-id="f6687-114">Discusses how colors are defined using a palette, how you can define your own color palette, and how to define colors based on an expression.</span></span>  
  
 [<span data-ttu-id="f6687-115">格式化圖表上的軸標籤 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f6687-115">Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)  
 <span data-ttu-id="f6687-116">討論如何顯示格線、刻度及標題，以及如何格式化軸刻度上的數字和日期。</span><span class="sxs-lookup"><span data-stu-id="f6687-116">Discusses how to display gridlines, tick marks, and titles, and how to format numbers and dates on the axis scale.</span></span>  
  
 [<span data-ttu-id="f6687-117">在圖表上格式化圖例 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f6687-117">Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-legend-formatting-report-builder.md)  
 <span data-ttu-id="f6687-118">討論如何重新排列及格式化圖表圖例中的項目。</span><span class="sxs-lookup"><span data-stu-id="f6687-118">Discusses how to re-order and format items in the chart legend.</span></span>  
  
 [<span data-ttu-id="f6687-119">格式化圖表上的資料點 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f6687-119">Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)  
 <span data-ttu-id="f6687-120">討論如何針對圖表上的每個數列放置資料點標籤及格式化資料點標記。</span><span class="sxs-lookup"><span data-stu-id="f6687-120">Discusses how to position data point labels and format data point markers for every series on the chart.</span></span>  
  
 [<span data-ttu-id="f6687-121">圖表中的 3D、浮凸和其他效果 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f6687-121">3D, Bevel, and Other Effects in a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-effects-3d-bevel-and-other-report-builder.md)  
 <span data-ttu-id="f6687-122">討論可套用到圖表的各種 3D 效果。</span><span class="sxs-lookup"><span data-stu-id="f6687-122">Discusses various 3D effects that you can apply to a chart.</span></span>  
  
 [<span data-ttu-id="f6687-123">將邊框加入至圖表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f6687-123">Add a Border Frame to a Chart &#40;Report Builder and SSRS&#41;</span></span>](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md)  
 <span data-ttu-id="f6687-124">說明如何將邊框加入至圖表。</span><span class="sxs-lookup"><span data-stu-id="f6687-124">Explains how to add a border frame to a chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6687-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6687-125">See Also</span></span>  
 <span data-ttu-id="f6687-126">[圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f6687-126">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f6687-127">[將邊框新增至圖表 &#40;報表產生器及 SSRS&#41;](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f6687-127">[Add a Border Frame to a Chart &#40;Report Builder and SSRS&#41;](add-a-border-frame-to-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f6687-128">[使用調色盤定義圖表的色彩 &#40;報表產生器及 SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f6687-128">[Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f6687-129">將斜面、浮凸與紋理樣式新增至圖表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f6687-129">Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-effects-add-bevel-emboss-or-texture-report-builder.md)  
  
  
