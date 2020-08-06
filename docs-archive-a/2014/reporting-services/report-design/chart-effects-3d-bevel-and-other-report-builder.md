---
title: 圖表中的 3D、斜面和其他效果 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10156"
ms.assetid: 18ef2119-2931-43ae-9078-f39b460462dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f505a0226d1c95a1c0c7c3caffde2be60f407b43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599376"
---
# <a name="3d-bevel-and-other-effects-in-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="0dbef-102">圖表中的 3D、浮凸和其他效果 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="0dbef-102">3D, Bevel, and Other Effects in a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="0dbef-103">三維 (3D) 效果可用來針對圖表提供深度及增加視覺效果。</span><span class="sxs-lookup"><span data-stu-id="0dbef-103">Three-dimensional (3D) effects can be used to provide depth and add visual impact to your chart.</span></span> <span data-ttu-id="0dbef-104">例如，若要強調分裂式圓形圖的特殊扇區，則可以旋轉及變更圖表的檢視方塊，讓使用者能首先注意該扇區。</span><span class="sxs-lookup"><span data-stu-id="0dbef-104">For example, if you want to emphasize a particular slice of an exploded pie chart, you can rotate and change the perspective of the chart so that people notice that slice first.</span></span> <span data-ttu-id="0dbef-105">將 3D 效果套用至圖表時，所有的漸層色彩和影線樣式都會停用。</span><span class="sxs-lookup"><span data-stu-id="0dbef-105">When 3D effects are applied to your chart, all gradient colors and hatching styles are disabled.</span></span>  
  
 <span data-ttu-id="0dbef-106">您可以將三維效果套用至個別的圖表，也可以同時在相同報表上顯示二維和三維圖表。</span><span class="sxs-lookup"><span data-stu-id="0dbef-106">Three-dimensional effects can be applied to individual charts, and it is possible to display both two-dimensional and three-dimensional charts on the same report.</span></span>  
  
 <span data-ttu-id="0dbef-107">您可以針對所有的圖表類型選取 [圖表區域屬性]  對話方塊中的 [啟用 3D]  ，以對圖表區域新增三維效果。</span><span class="sxs-lookup"><span data-stu-id="0dbef-107">For all chart types, you can add three-dimensional effects to a chart area in the **Chart Area Properties** dialog box by selecting **Enable 3D**.</span></span> <span data-ttu-id="0dbef-108">如需詳細資訊，請參閱 [將 3D 效果加入至圖表 &#40;報表產生器及 SSRS&#41;](chart-effects-add-3d-effects-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="0dbef-108">For more information, see [Add 3D Effects to a Chart &#40;Report Builder and SSRS&#41;](chart-effects-add-3d-effects-report-builder.md).</span></span>  
  
 <span data-ttu-id="0dbef-109">另一種對圖表加入視覺效果的方式是在直條圖、橫條圖、圓形圖及環圈圖中加入按鈕形、浮凸和材質樣式。</span><span class="sxs-lookup"><span data-stu-id="0dbef-109">Another way to add visual impact to charts is by adding bevel, emboss and texture styles in bar, column, pie and doughnut charts.</span></span> <span data-ttu-id="0dbef-110">如需詳細資訊，請參閱[將斜面、浮凸與紋理樣式加入圖表 &#40;報表產生器及 SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="0dbef-110">For more information, see [Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="coordinate-based-three-dimensional-charts"></a><span data-ttu-id="0dbef-111">以座標為基礎的三維圖表</span><span class="sxs-lookup"><span data-stu-id="0dbef-111">Coordinate-Based Three-Dimensional Charts</span></span>  
 <span data-ttu-id="0dbef-112">三維效果在使用以座標為基礎的圖表類型 (直條圖、橫條圖、區域圖、點圖、折線圖和範圍圖) 時，會以第三個軸 (也稱為 Z 軸) 來顯示圖表。</span><span class="sxs-lookup"><span data-stu-id="0dbef-112">When working with coordinate-based chart types (Column, Bar, Area, Point, Line and Range), three-dimensional effects display the chart with a third axis, known as the "z-axis".</span></span> <span data-ttu-id="0dbef-113">在引進這第三個軸後，您就可以對圖表套用各種視覺增強功能。</span><span class="sxs-lookup"><span data-stu-id="0dbef-113">The introduction of this third axis allows you to apply a variety of visual enhancements to your chart.</span></span>  
  
### <a name="changing-the-white-space-in-a-3d-chart"></a><span data-ttu-id="0dbef-114">變更 3D 圖表中的空白</span><span class="sxs-lookup"><span data-stu-id="0dbef-114">Changing the White Space in a 3D Chart</span></span>  
 <span data-ttu-id="0dbef-115">以三維模式顯示圖表區域時，每個數列都會沿著圖表的 Z 軸以個別的資料列顯示。</span><span class="sxs-lookup"><span data-stu-id="0dbef-115">When you display a chart area in three-dimensional mode, each series is shown in a separate row along the z-axis of the chart.</span></span> <span data-ttu-id="0dbef-116">若要變更每個數列之間的空白量，請變更 [3D 效果] 對話方塊中的 **[點間隙深度]** 屬性來修改圖表的點間隙深度。</span><span class="sxs-lookup"><span data-stu-id="0dbef-116">To change the amount of space between each series, modify the chart's point gap depth by changing the **Point Gap Depth** property in the 3D Effects dialog box.</span></span>  
  
### <a name="changing-the-projection-of-a-3d-chart"></a><span data-ttu-id="0dbef-117">變更 3D 圖表的投射</span><span class="sxs-lookup"><span data-stu-id="0dbef-117">Changing the Projection of a 3D Chart</span></span>  
 <span data-ttu-id="0dbef-118">3D 投射有兩種類型：傾斜和遠近景深。</span><span class="sxs-lookup"><span data-stu-id="0dbef-118">There are two types of 3D projections: oblique and perspective.</span></span> <span data-ttu-id="0dbef-119">圖表的傾斜投射會對二維圖表加入深度維度。</span><span class="sxs-lookup"><span data-stu-id="0dbef-119">An oblique projection to the chart adds a depth dimension to a two-dimensional chart.</span></span> <span data-ttu-id="0dbef-120">Z 軸會從與水平及垂直軸相等的角度繪製，水平及垂直軸則彼此垂直，與二維圖表中一樣。</span><span class="sxs-lookup"><span data-stu-id="0dbef-120">The z-axis is drawn at equal angles from the horizontal and vertical axes, which remain perpendicular to each other just as in a two-dimensional chart.</span></span>  
  
 <span data-ttu-id="0dbef-121">遠近景深投射轉換圖表的方式則是估計檢視平面並重新繪製圖表，使其好像是從該點進行檢視一般。</span><span class="sxs-lookup"><span data-stu-id="0dbef-121">Perspective projection transforms the chart by estimating a view plane and re-drawing the chart as if it were being viewed from that point.</span></span> <span data-ttu-id="0dbef-122">**[旋轉]** 值會將檢視從 0 度的「地平面」垂直提升到頭頂的 90 度。</span><span class="sxs-lookup"><span data-stu-id="0dbef-122">The **Rotation** value shifts the view vertically from "ground level" at 0 to overhead at 90.</span></span> <span data-ttu-id="0dbef-123">**[傾斜]** 值則會將檢視角度轉至左方或右方。</span><span class="sxs-lookup"><span data-stu-id="0dbef-123">The **Inclination** value shifts the viewing angle to the left or right.</span></span> <span data-ttu-id="0dbef-124">0 值與圖表的二維檢視相同。</span><span class="sxs-lookup"><span data-stu-id="0dbef-124">A value of 0 is equivalent to a two-dimensional view of the chart.</span></span> <span data-ttu-id="0dbef-125">**[遠近景深]** 值定義在顯示投射時使用的扭曲百分比。</span><span class="sxs-lookup"><span data-stu-id="0dbef-125">The **Perspective** value defines the percentage of distortion that will be used when displaying the projection.</span></span> <span data-ttu-id="0dbef-126">這種投射類型會維持圖表的比例，但圖表的外觀會扭曲，所以使用較低的遠近景深比較有效。</span><span class="sxs-lookup"><span data-stu-id="0dbef-126">This type of projection maintains the proportions of your chart, but the chart's appearance becomes distorted, so it is most effective to use a lower degree of perspective.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0dbef-127">傾斜和遠近景深投射是不同的投射類型，所以不能同時用於相同的圖表。</span><span class="sxs-lookup"><span data-stu-id="0dbef-127">The oblique and perspective projections are separate types of projections, so they cannot be used together on the same chart.</span></span>  
  
### <a name="clustering-data"></a><span data-ttu-id="0dbef-128">群集資料</span><span class="sxs-lookup"><span data-stu-id="0dbef-128">Clustering Data</span></span>  
 <span data-ttu-id="0dbef-129">在 2D 圖表中，多個資料數列會並列顯示。</span><span class="sxs-lookup"><span data-stu-id="0dbef-129">In 2D charts, multiple series of data appear side-by-side.</span></span> <span data-ttu-id="0dbef-130">群集則會在 3D 圖表的個別資料列上顯示個別數列。</span><span class="sxs-lookup"><span data-stu-id="0dbef-130">Clustering shows individual series in separate rows on a 3D chart.</span></span> <span data-ttu-id="0dbef-131">例如，如果圖表包含三個資料點數列，則群集會沿著 Z 軸以個別的資料列顯示這三個數列。</span><span class="sxs-lookup"><span data-stu-id="0dbef-131">For example, if you have a chart that contains three series of data points, clustering will display each of the three series on a separate row along the z-axis.</span></span> <span data-ttu-id="0dbef-132">依預設，以 3D 顯示的所有圖表類型都會進行群集。</span><span class="sxs-lookup"><span data-stu-id="0dbef-132">By default, all chart types shown in 3D are clustered.</span></span>  
  
 <span data-ttu-id="0dbef-133">橫條圖和直條圖都可以停用群集。</span><span class="sxs-lookup"><span data-stu-id="0dbef-133">Clustering can be disabled for bar and column charts.</span></span> <span data-ttu-id="0dbef-134">當群集停用時，多個橫條和直條數列會並排顯示於單一資料列。</span><span class="sxs-lookup"><span data-stu-id="0dbef-134">When clustering is disabled, multiple bar and column series are displayed side-by-side in one row.</span></span>  
  
## <a name="shape-based-three-dimensional-charts"></a><span data-ttu-id="0dbef-135">以形狀為基礎的三維圖表</span><span class="sxs-lookup"><span data-stu-id="0dbef-135">Shape-Based Three-Dimensional Charts</span></span>  
 <span data-ttu-id="0dbef-136">以形狀為基礎的圖表類型 (圓形圖、環圈圖、漏斗圖、金字塔圖) 可用的三維效果較少。</span><span class="sxs-lookup"><span data-stu-id="0dbef-136">Shape-based chart types (Pie, Doughnut, Funnel, Pyramid) have fewer three-dimensional effects available.</span></span> <span data-ttu-id="0dbef-137">在使用以形狀為基礎的圖表類型時，只能變更旋轉及傾斜值。</span><span class="sxs-lookup"><span data-stu-id="0dbef-137">When working with shape-based chart types, you can change the rotation and inclination values only.</span></span>  
  
## <a name="rotations"></a><span data-ttu-id="0dbef-138">旋轉</span><span class="sxs-lookup"><span data-stu-id="0dbef-138">Rotations</span></span>  
 <span data-ttu-id="0dbef-139">可以將圖表從 -90 度水平及垂直旋轉至 90 度。</span><span class="sxs-lookup"><span data-stu-id="0dbef-139">Charts can be rotated horizontally and vertically from -90 to 90 degrees.</span></span> <span data-ttu-id="0dbef-140">正值的水平角度會沿著 X 軸逆時針旋轉圖表，正值的垂直角度則會沿 Y 軸順時針旋轉圖表。</span><span class="sxs-lookup"><span data-stu-id="0dbef-140">A positive horizontal angle will rotate the chart counter-clockwise around the x-axis, while a positive vertical angle will rotate the chart clockwise around the y-axis.</span></span>  
  
## <a name="highlighting-3d-effects"></a><span data-ttu-id="0dbef-141">反白顯示 3D 效果</span><span class="sxs-lookup"><span data-stu-id="0dbef-141">Highlighting 3D Effects</span></span>  
 <span data-ttu-id="0dbef-142">您可以透過 **[陰影]** 屬性來反白顯示 3D 圖表的樣式，這個屬性會在您選取圖表區域時顯示在 [屬性] 窗格的 [Area3DStyle] 下方。</span><span class="sxs-lookup"><span data-stu-id="0dbef-142">You can add highlighting styles to a 3D chart via the **Shading** property, which appears under Area3DStyle in the Properties pane when the chart area is selected.</span></span> <span data-ttu-id="0dbef-143">簡單的光源樣式會對圖表區域項目套用相同的色調。</span><span class="sxs-lookup"><span data-stu-id="0dbef-143">A simple lighting style applies the same hue to the chart area elements.</span></span> <span data-ttu-id="0dbef-144">真實感的樣式會根據指定的光源角度而變更圖表區域項目的色調。</span><span class="sxs-lookup"><span data-stu-id="0dbef-144">A realistic style changes the hues of the chart area elements depending on a specified lighting angle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dbef-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0dbef-145">See Also</span></span>  
 <span data-ttu-id="0dbef-146">[格式化圖表上的軸標籤 &#40;報表產生器及 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0dbef-146">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0dbef-147">[格式化圖表 &#40;報表產生器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0dbef-147">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="0dbef-148">將 3D 效果新增至圖表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0dbef-148">Add 3D Effects to a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-effects-add-3d-effects-report-builder.md)  
  
  
