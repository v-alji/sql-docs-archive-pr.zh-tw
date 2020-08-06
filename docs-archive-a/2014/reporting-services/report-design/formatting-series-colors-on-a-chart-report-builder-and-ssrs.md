---
title: 設定圖表上數列色彩的格式 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10245"
- "10252"
- sql12.rtp.rptdesigner.serieslabelproperties.borders.f1
- sql12.rtp.rptdesigner.seriesproperties.borders.f1
ms.assetid: fe541501-cac5-47b1-b95f-c410db789190
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f0e4f526e32ba38b94c5707c1ce3acc3cd073626
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686804"
---
# <a name="formatting-series-colors-on-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="628ba-102">設定圖表上數列色彩的格式 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="628ba-102">Formatting Series Colors on a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="628ba-103">Reporting Services 為圖表提供數個內建的調色盤，或者您也可以定義自訂的調色盤。</span><span class="sxs-lookup"><span data-stu-id="628ba-103">Reporting Services provides several built-in palettes for charts, or you can define a custom palette.</span></span> <span data-ttu-id="628ba-104">根據預設，圖表會使用內建的**BrightPastel**色調色板來填滿每個數列。</span><span class="sxs-lookup"><span data-stu-id="628ba-104">By default, charts use the built-in **BrightPastel** color palette to fill each series.</span></span> <span data-ttu-id="628ba-105">這些色彩也會出現在圖例中。</span><span class="sxs-lookup"><span data-stu-id="628ba-105">These colors also appear in the legend.</span></span> <span data-ttu-id="628ba-106">在圖表中加入多個序列時，圖表會以調色盤定義色彩的順序為序列指派色彩。</span><span class="sxs-lookup"><span data-stu-id="628ba-106">When multiple series are added to the chart, the chart assigns the series a color in the order that the colors have been defined in the palette.</span></span>  
  
 <span data-ttu-id="628ba-107">如果序列的數目超過調色盤中的色彩數，則圖表會重覆使用色彩，因此兩個序列可能會擁有相同的色彩。</span><span class="sxs-lookup"><span data-stu-id="628ba-107">If there are a greater number of series than there are colors in the palette, the chart will begin reusing colors, and two series may have the same color.</span></span> <span data-ttu-id="628ba-108">如果您所使用的是形狀圖，就會經常發生這種情形，其中會為每個資料點指派調色盤的一個色彩。</span><span class="sxs-lookup"><span data-stu-id="628ba-108">This frequently occurs if you are using a Shape chart, where each data point is assigned a color from the palette.</span></span> <span data-ttu-id="628ba-109">為了避免混淆，請至少使用與圖表上的序列一樣多的色彩來定義自訂調色盤。</span><span class="sxs-lookup"><span data-stu-id="628ba-109">To avoid confusion, define a custom palette with at least the same number of colors as you have series on your chart.</span></span>  
  
 <span data-ttu-id="628ba-110">您可以選取新的調色盤，或從 [屬性] 窗格定義自訂調色盤。</span><span class="sxs-lookup"><span data-stu-id="628ba-110">You can select a new palette or define a custom palette from the Properties pane.</span></span> <span data-ttu-id="628ba-111">如需詳細資訊，請參閱[使用調色盤定義圖表的色彩 &#40;報表產生器及 SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="628ba-111">For more information, see [Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="using-built-in-palettes"></a><span data-ttu-id="628ba-112">使用內建調色盤</span><span class="sxs-lookup"><span data-stu-id="628ba-112">Using Built-In Palettes</span></span>  
 <span data-ttu-id="628ba-113">Reporting Services 提供預先定義的內建調色盤清單，可用來為圖表上的序列定義色彩集。</span><span class="sxs-lookup"><span data-stu-id="628ba-113">Reporting Services provides a list of predefined, built-in palettes that you can use to define a color set for series on your chart.</span></span> <span data-ttu-id="628ba-114">所有內建調色盤都包含 10 到 16 個色彩值。</span><span class="sxs-lookup"><span data-stu-id="628ba-114">All built-in palettes contain between 10 and 16 color values.</span></span> <span data-ttu-id="628ba-115">您不能擴充內建調色盤來加入其他色彩，所以如果需要超過 16 種色彩，就必須定義自訂的調色盤。</span><span class="sxs-lookup"><span data-stu-id="628ba-115">You cannot extend the built-in palette to include more colors, so if you need more than 16 colors, you must define a custom palette.</span></span>  
  
 <span data-ttu-id="628ba-116">如果您要列印報表，請考慮使用 [灰階]  調色盤。</span><span class="sxs-lookup"><span data-stu-id="628ba-116">If you are printing a report, consider using the **Greyscale** palette.</span></span> <span data-ttu-id="628ba-117">這個調色盤會使用黑白色彩來表示圖表中的每個序列。</span><span class="sxs-lookup"><span data-stu-id="628ba-117">This palette uses shades of black and white to represent each series in a chart.</span></span>  
  
 <span data-ttu-id="628ba-118">在舊版的 Reporting Services 中是使用名為「預設」的調色盤做為預設的圖表調色盤。</span><span class="sxs-lookup"><span data-stu-id="628ba-118">The palette named Default was used as the default chart palette in earlier versions of Reporting Services.</span></span> <span data-ttu-id="628ba-119">這個調色盤仍維持相同名稱以求一致性。</span><span class="sxs-lookup"><span data-stu-id="628ba-119">It has been maintained with the same name for consistency.</span></span> <span data-ttu-id="628ba-120">圖表將使用 [預設] 調色盤進行無接縫的升級，但在升級之後，您可以考慮加以變更。</span><span class="sxs-lookup"><span data-stu-id="628ba-120">Charts will upgrade seamlessly using the Default palette, but after upgrading, you might consider changing it.</span></span>  
  
## <a name="using-custom-palettes"></a><span data-ttu-id="628ba-121">使用自訂調色盤</span><span class="sxs-lookup"><span data-stu-id="628ba-121">Using Custom Palettes</span></span>  
 <span data-ttu-id="628ba-122">如果要將自己的色彩套用至圖表，請使用自訂調色盤。</span><span class="sxs-lookup"><span data-stu-id="628ba-122">If you want to apply your own colors to the chart, use a custom palette.</span></span> <span data-ttu-id="628ba-123">自訂調色盤可讓您將依照要在圖表上顯示色彩的順序，加入自己的色彩。</span><span class="sxs-lookup"><span data-stu-id="628ba-123">A custom palette let you add your own colors in the order you want them to appear on the chart.</span></span> <span data-ttu-id="628ba-124">如果在設計階段時還不知道圖表中的序列數，則自訂調色盤特別有用。</span><span class="sxs-lookup"><span data-stu-id="628ba-124">A custom palette is especially helpful if the number of series in your chart is unknown at design time.</span></span> <span data-ttu-id="628ba-125">如需詳細資訊，請參閱[使用調色盤定義圖表的色彩 &#40;報表產生器及 SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="628ba-125">For more information, see [Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md).</span></span>  
  
## <a name="using-a-color-fill-on-each-series"></a><span data-ttu-id="628ba-126">在每個序列上使用色彩填滿</span><span class="sxs-lookup"><span data-stu-id="628ba-126">Using a Color Fill on Each Series</span></span>  
 <span data-ttu-id="628ba-127">您也可以針對圖表上的每個序列指定色彩，在圖表上定義自己的色彩。</span><span class="sxs-lookup"><span data-stu-id="628ba-127">You can also define your own colors on the chart by specifying a color for each series on the chart.</span></span> <span data-ttu-id="628ba-128">若要進行這項作業，請開啟 [數列屬性] 對話方塊，然後設定 [填滿] 的 [色彩] 屬性。</span><span class="sxs-lookup"><span data-stu-id="628ba-128">To do this, open the **Series Properties** dialog box and set the **Color** property for **Fill**.</span></span> <span data-ttu-id="628ba-129">這個方法會覆寫所有定義的調色盤。</span><span class="sxs-lookup"><span data-stu-id="628ba-129">This approach will override all defined palettes.</span></span> <span data-ttu-id="628ba-130">一般來說，最好使用自訂調色盤來定義自己的色彩，因為可能要到處理報表之後，才會知道資料集中的序列數。</span><span class="sxs-lookup"><span data-stu-id="628ba-130">Generally, it is better to use a custom palette to define your own colors because the number of series in your dataset may not be known until report processing.</span></span>  
  
 <span data-ttu-id="628ba-131">當您想要根據運算式有條件地設定序列的色彩時，這個方法最適用。</span><span class="sxs-lookup"><span data-stu-id="628ba-131">This approach is best suited when you want to conditionally set the color of the series based on an expression.</span></span>  <span data-ttu-id="628ba-132">如需詳細資訊，請參閱 [格式化圖表上的資料點 &#40;報表產生器及 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="628ba-132">For more information, see [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="628ba-133">本節內容</span><span class="sxs-lookup"><span data-stu-id="628ba-133">In This Section</span></span>  
 [<span data-ttu-id="628ba-134">跨多個形狀圖指定一致的色彩 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="628ba-134">Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
 <span data-ttu-id="628ba-135">[使用調色盤定義圖表的色彩 &#40;報表產生器及 SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="628ba-135">[Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md))</span></span>  
  
 [<span data-ttu-id="628ba-136">加入帶狀線來強調圖表資料 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="628ba-136">Highlight Chart Data by Adding Strip Lines &#40;Report Builder and SSRS&#41;</span></span>](highlight-chart-data-by-adding-strip-lines-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a><span data-ttu-id="628ba-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="628ba-137">See Also</span></span>  
 <span data-ttu-id="628ba-138">[格式化圖表 &#40;報表產生器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="628ba-138">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="628ba-139">[將斜面、浮凸與紋理樣式加入至圖表 &#40;報表產生器及 SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="628ba-139">[Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md) </span></span>  
 <span data-ttu-id="628ba-140">[圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="628ba-140">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="628ba-141">在圖表上格式化圖例 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="628ba-141">Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-legend-formatting-report-builder.md)  
  
  
