---
title: 將斜面、浮凸與紋理樣式新增至圖表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 737cfc80-b39e-497c-817b-b46693deb58f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 92c5d4af47b7889b9ba5ec421706848f8822075b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599372"
---
# <a name="add-bevel-emboss-and-texture-styles-to-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="95027-102">將斜面、浮凸與紋理樣式加入至圖表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="95027-102">Add Bevel, Emboss, and Texture Styles to a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="95027-103">使用某些圖表類型時，您可以指定繪製效果來增加圖表的視覺效果。</span><span class="sxs-lookup"><span data-stu-id="95027-103">When using certain chart types, you can specify a drawing effect to increase the visual impact of your chart.</span></span> <span data-ttu-id="95027-104">這些繪製效果僅適用於圖表的數列。</span><span class="sxs-lookup"><span data-stu-id="95027-104">These drawing effects are only applied to the series of your chart.</span></span> <span data-ttu-id="95027-105">它們對於其他任何圖表元素沒有影響。</span><span class="sxs-lookup"><span data-stu-id="95027-105">They have no effect on any other chart element.</span></span>  
  
 <span data-ttu-id="95027-106">當您使用圓形圖或環圈圖的任何變數時，您可以指定類似於可以套用到影像之斜面或浮凸效果的柔邊或凹面繪製樣式。</span><span class="sxs-lookup"><span data-stu-id="95027-106">When you are using any variant of a pie or doughnut chart, you can specify a soft edge or concave drawing style, similar to bevel or emboss effects that can be applied to an image.</span></span>  
  
 <span data-ttu-id="95027-107">當您使用橫條圖或直條圖的任何變數時，則可以將紋理樣式 (例如，圓柱、楔形和深淺) 套用到個別的橫條圖或直條圖。</span><span class="sxs-lookup"><span data-stu-id="95027-107">When you are using any variant of a bar or column chart, you can apply texture styles, such as cylinder, wedge, and light-to-dark, to the individual bars or columns.</span></span>  
  
 <span data-ttu-id="95027-108">除了這些繪製樣式之外，您也可以在許多圖表元素中加入框線和陰影，以提供深度的幻影。</span><span class="sxs-lookup"><span data-stu-id="95027-108">In addition to these drawing styles, you can add borders and shadows to many chart elements to give the illusion of depth.</span></span> <span data-ttu-id="95027-109">如需其他格式化圖表方式的詳細資訊，請參閱 [格式化圖表 &#40;報表產生器及 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="95027-109">For more information on other ways to format the chart, see [Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-bevel-or-emboss-styles-to-a-pie-or-doughnut-chart"></a><span data-ttu-id="95027-110">若要將斜面或浮凸樣式加入至圓形圖或環圈圖</span><span class="sxs-lookup"><span data-stu-id="95027-110">To add bevel or emboss styles to a pie or doughnut chart</span></span>  
  
1.  <span data-ttu-id="95027-111">在 **[檢視]** 索引標籤上，選取 **[屬性]** 來開啟 [屬性] 窗格。</span><span class="sxs-lookup"><span data-stu-id="95027-111">On the **View** tab, select **Properties** to open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="95027-112">選取您要增強的圓形圖或環圈圖。</span><span class="sxs-lookup"><span data-stu-id="95027-112">Select the pie or doughnut chart that you want to enhance.</span></span> <span data-ttu-id="95027-113">在圖表 (而非整個圖表) 中選取一個資料欄位。</span><span class="sxs-lookup"><span data-stu-id="95027-113">Select a data field in the chart, not the entire chart.</span></span>  
  
3.  <span data-ttu-id="95027-114">在 [屬性] 窗格中，展開 **[CustomAttributes]** 節點。</span><span class="sxs-lookup"><span data-stu-id="95027-114">In the Properties pane, expand the **CustomAttributes** node.</span></span>  
  
4.  <span data-ttu-id="95027-115">為 PieDrawingStyle 從下拉式清單中選取一種樣式。</span><span class="sxs-lookup"><span data-stu-id="95027-115">For PieDrawingStyle, select a style from the drop-down list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95027-116">在相同的圖表上，您無法同時擁有 3D 與斜面或浮凸樣式。</span><span class="sxs-lookup"><span data-stu-id="95027-116">You can't have 3D and bevel or emboss styles on the same chart.</span></span> <span data-ttu-id="95027-117">如果您已經啟用圖表的 3D 樣式，將無法看到 PieDrawingStyle 屬性。</span><span class="sxs-lookup"><span data-stu-id="95027-117">If you have enabled 3D for the chart, you will not see the PieDrawingStyle property.</span></span>  
  
 <span data-ttu-id="95027-118">![具有凹面繪製樣式的圓形圖](../media/rs-piedrawingeffects-concave.gif "具有凹面繪製樣式的圓形圖")</span><span class="sxs-lookup"><span data-stu-id="95027-118">![Pie chart with concave drawing style](../media/rs-piedrawingeffects-concave.gif "Pie chart with concave drawing style")</span></span>  
  
### <a name="to-add-texture-styles-to-a-bar-or-column-chart"></a><span data-ttu-id="95027-119">若要將紋理樣式加入至橫條圖或直條圖</span><span class="sxs-lookup"><span data-stu-id="95027-119">To add texture styles to a bar or column chart</span></span>  
  
1.  <span data-ttu-id="95027-120">選取您要增強的橫條圖或直條圖。</span><span class="sxs-lookup"><span data-stu-id="95027-120">Select the bar or column chart that you want to enhance.</span></span> <span data-ttu-id="95027-121">在圖表 (而非整個圖表) 中選取一個資料欄位。</span><span class="sxs-lookup"><span data-stu-id="95027-121">Select a data field in the chart, not the entire chart.</span></span>  
  
2.  <span data-ttu-id="95027-122">開啟 [屬性] 窗格。</span><span class="sxs-lookup"><span data-stu-id="95027-122">Open the Properties pane.</span></span>  
  
3.  <span data-ttu-id="95027-123">展開 **CustomAttributes** 節點。</span><span class="sxs-lookup"><span data-stu-id="95027-123">Expand the **CustomAttributes** node.</span></span>  
  
4.  <span data-ttu-id="95027-124">為 DrawingStyle 從下拉式清單中選取一種樣式。</span><span class="sxs-lookup"><span data-stu-id="95027-124">For DrawingStyle, select a style from the drop-down list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95027-125">在相同的圖表上，您無法同時擁有 3D 與斜面或浮凸樣式。</span><span class="sxs-lookup"><span data-stu-id="95027-125">You can't have 3D and bevel or emboss styles on the same chart.</span></span> <span data-ttu-id="95027-126">如果您已經啟用圖表的 3D 樣式，將無法看到 PieDrawingStyle 屬性。</span><span class="sxs-lookup"><span data-stu-id="95027-126">If you have enabled 3D for the chart, you will not see the PieDrawingStyle property.</span></span>  
  
 <span data-ttu-id="95027-127">![具有 LightToDark 繪製效果的橫條圖](../media/rs-bardrawingeffects-lighttodark.gif "具有 LightToDark 繪製效果的橫條圖")</span><span class="sxs-lookup"><span data-stu-id="95027-127">![Bar chart with LightToDark drawing effect](../media/rs-bardrawingeffects-lighttodark.gif "Bar chart with LightToDark drawing effect")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95027-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95027-128">See Also</span></span>  
 <span data-ttu-id="95027-129">[橫條圖 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="95027-129">[Bar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="95027-130">[直條圖 &#40;報表產生器及 SSRS&#41;](column-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="95027-130">[Column Charts &#40;Report Builder and SSRS&#41;](column-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="95027-131">[圓形圖 &#40;報表產生器及 SSRS&#41;](pie-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="95027-131">[Pie Charts &#40;Report Builder and SSRS&#41;](pie-charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="95027-132">格式化圖表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="95027-132">Formatting a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-a-chart-report-builder-and-ssrs.md)  
  
  
