---
title: 將 3D 效果新增至圖表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ab9625d8-6557-4a4d-8123-eefa7c066ff5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f4fcd90452e32b760bc446ac5d085ed00520a2f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599375"
---
# <a name="add-3d-effects-to-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="8455c-102">將 3D 效果加入至圖表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="8455c-102">Add 3D Effects to a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8455c-103">三維 (3D) 效果可用來針對圖表提供深度及增加視覺效果。</span><span class="sxs-lookup"><span data-stu-id="8455c-103">Three-dimensional (3D) effects can be used to provide depth and add visual impact to your chart.</span></span> <span data-ttu-id="8455c-104">例如，若要強調分裂式圓形圖的特殊扇區，則可以旋轉及變更圖表的檢視方塊，讓使用者能首先注意該扇區。</span><span class="sxs-lookup"><span data-stu-id="8455c-104">For example, if you want to emphasize a particular slice of an exploded pie chart, you can rotate and change the perspective of the chart so that people notice that slice first.</span></span> <span data-ttu-id="8455c-105">將 3D 效果套用至圖表時，所有的漸層色彩和影線樣式都會停用。</span><span class="sxs-lookup"><span data-stu-id="8455c-105">When 3D effects are applied to your chart, all gradient colors and hatching styles are disabled.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-apply-3d-effects-to-a-range-area-line-scatter-or-polar-chart"></a><span data-ttu-id="8455c-106">將 3D 效果套用到範圍圖、區域圖、折線圖、散佈圖或極座標圖</span><span class="sxs-lookup"><span data-stu-id="8455c-106">To apply 3D effects to a Range, Area, Line, Scatter or Polar chart</span></span>  
  
1.  <span data-ttu-id="8455c-107">以滑鼠右鍵按一下圖表區域內的任何位置，然後選取 [3D 效果]  。</span><span class="sxs-lookup"><span data-stu-id="8455c-107">Right-click anywhere inside the chart area and select **3D Effects**.</span></span> <span data-ttu-id="8455c-108">[圖表區域屬性]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="8455c-108">The **Chart Area Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="8455c-109">在 [3D 選項]  中，選取 [啟用 3D]  選項。</span><span class="sxs-lookup"><span data-stu-id="8455c-109">In **3D Options**, select the **Enable 3D** option.</span></span>  
  
3.  <span data-ttu-id="8455c-110">(選擇性) 在 [3D 選項]  中，可以設定多種與 3D 角度及場景選項相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="8455c-110">(Optional) In **3D Options**, you can set a variety of properties relating to 3D angles and scene options.</span></span> <span data-ttu-id="8455c-111">如需這些屬性的詳細資訊，請參閱 [圖表中的 3D、浮凸和其他效果 &#40;報表產生器及 SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="8455c-111">For more information about these properties, see [3D, Bevel, and Other Effects in a Chart &#40;Report Builder and SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md).</span></span>  
  
4.  <span data-ttu-id="8455c-112">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="8455c-112">Click **OK**.</span></span>  
  
### <a name="to-apply-3d-effects-to-a-funnel-chart"></a><span data-ttu-id="8455c-113">將 3D 效果套用到漏斗圖</span><span class="sxs-lookup"><span data-stu-id="8455c-113">To apply 3D effects to a Funnel chart</span></span>  
  
1.  <span data-ttu-id="8455c-114">以滑鼠右鍵按一下圖表區域內的任何位置，然後選取 [3D 效果]  。</span><span class="sxs-lookup"><span data-stu-id="8455c-114">Right-click anywhere inside the chart area and select **3D Effects**.</span></span> <span data-ttu-id="8455c-115">[圖表區域屬性]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="8455c-115">The **Chart Area Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="8455c-116">在 [3D 選項]  中，選取 [啟用 3D]  選項。</span><span class="sxs-lookup"><span data-stu-id="8455c-116">In **3D Options**, select the **Enable 3D** option.</span></span> <span data-ttu-id="8455c-117">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="8455c-117">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="8455c-118">(選擇性) 若要自訂漏斗圖的視覺外觀，可以移至 [屬性] 窗格，然後變更漏斗圖特定的屬性。</span><span class="sxs-lookup"><span data-stu-id="8455c-118">(Optional) To customize the funnel chart visual appearance, you can go to the Properties pane and change properties specific to the funnel chart.</span></span>  
  
    1.  <span data-ttu-id="8455c-119">開啟 [屬性] 窗格。</span><span class="sxs-lookup"><span data-stu-id="8455c-119">Open the Properties pane.</span></span>  
  
    2.  <span data-ttu-id="8455c-120">在設計介面上按一下漏斗的任何位置。</span><span class="sxs-lookup"><span data-stu-id="8455c-120">On the design surface, click anywhere on the funnel.</span></span> <span data-ttu-id="8455c-121">漏斗圖數列的屬性會顯示在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="8455c-121">The properties for the series of the funnel chart are displayed in the Properties pane.</span></span>  
  
    3.  <span data-ttu-id="8455c-122">在 [一般]  區段中，展開 [CustomAttributes]  節點。</span><span class="sxs-lookup"><span data-stu-id="8455c-122">In the **General** section, expand the **CustomAttributes** node.</span></span>  
  
    4.  <span data-ttu-id="8455c-123">針對 [Funnel3DDrawingStyle]  屬性，選取漏斗是要顯示為圓形或方形。</span><span class="sxs-lookup"><span data-stu-id="8455c-123">For the **Funnel3DDrawingStyle** property, select whether the funnel will be shown with as circular or square.</span></span>  
  
    5.  <span data-ttu-id="8455c-124">為 [Funnel3DRotationAngle]  屬性設定介於 -10 和 10 之間的值。</span><span class="sxs-lookup"><span data-stu-id="8455c-124">For the **Funnel3DRotationAngle** property, set a value between -10 and 10.</span></span> <span data-ttu-id="8455c-125">這會決定在 3D 漏斗圖上顯示的傾斜度。</span><span class="sxs-lookup"><span data-stu-id="8455c-125">This will determine the degree of tilt that will be displayed on the 3D funnel chart.</span></span>  
  
### <a name="to-apply-3d-effects-to-a-pie-chart"></a><span data-ttu-id="8455c-126">將 3D 效果套用到圓形圖</span><span class="sxs-lookup"><span data-stu-id="8455c-126">To apply 3D effects to a Pie chart</span></span>  
  
1.  <span data-ttu-id="8455c-127">以滑鼠右鍵按一下圖表區域內的任何位置，然後選取 [3D 效果]。</span><span class="sxs-lookup"><span data-stu-id="8455c-127">Right-click anywhere inside the chart area and select 3D Effects.</span></span> <span data-ttu-id="8455c-128">[圖表區域屬性]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="8455c-128">The **Chart Area Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="8455c-129">在 [3D 選項]  中，選取 [啟用 3D]  選項。</span><span class="sxs-lookup"><span data-stu-id="8455c-129">In **3D Options**, select the **Enable 3D** option.</span></span> <span data-ttu-id="8455c-130">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="8455c-130">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="8455c-131">(選擇性) 在 [旋轉]  中鍵入整數值，代表圓形圖的水平旋轉。</span><span class="sxs-lookup"><span data-stu-id="8455c-131">(Optional) In **Rotation**, type an integer value that represents the horizontal rotation of the pie chart.</span></span>  
  
4.  <span data-ttu-id="8455c-132">(選擇性) 在 [傾斜]  中鍵入整數值，代表圓形圖的垂直傾斜旋轉。</span><span class="sxs-lookup"><span data-stu-id="8455c-132">(Optional) In **Inclination**, type an integer value that represents the vertical tilt rotation of the pie chart.</span></span>  
  
5.  <span data-ttu-id="8455c-133">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="8455c-133">Click **OK**.</span></span>  
  
### <a name="to-apply-3d-effects-to-a-bar-or-column-chart"></a><span data-ttu-id="8455c-134">將 3D 效果套用到橫條圖或直條圖</span><span class="sxs-lookup"><span data-stu-id="8455c-134">To apply 3D effects to a Bar or Column chart</span></span>  
  
1.  <span data-ttu-id="8455c-135">以滑鼠右鍵按一下圖表區域內的任何位置，然後選取 [3D 效果]  。</span><span class="sxs-lookup"><span data-stu-id="8455c-135">Right-click anywhere inside the chart area and select **3D Effects**.</span></span> <span data-ttu-id="8455c-136">[圖表區域屬性]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="8455c-136">The **Chart Area Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="8455c-137">選取 [啟用 3D]  選項。</span><span class="sxs-lookup"><span data-stu-id="8455c-137">Select the **Enable 3D** option.</span></span> <span data-ttu-id="8455c-138">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="8455c-138">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="8455c-139">(選擇性) 選取 [啟用數列群集]  選項。</span><span class="sxs-lookup"><span data-stu-id="8455c-139">(Optional) Select the **Enable series clustering** option.</span></span> <span data-ttu-id="8455c-140">如果圖表包含多個橫條圖或直條圖數列，則這個選項會將數列顯示為群集。</span><span class="sxs-lookup"><span data-stu-id="8455c-140">If your chart contains multiple bar or column chart series, this option will display the series as clustered.</span></span> <span data-ttu-id="8455c-141">依預設，多個橫條或直條數列會並列顯示。</span><span class="sxs-lookup"><span data-stu-id="8455c-141">By default, multiple bar or column series are shown side-by-side.</span></span>  
  
4.  <span data-ttu-id="8455c-142">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="8455c-142">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="8455c-143">(選擇性) 若要對橫條圖或直條圖加入圓柱效果，請依照下列步驟執行：</span><span class="sxs-lookup"><span data-stu-id="8455c-143">(Optional) To add cylinder effects to a bar or column chart, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="8455c-144">開啟 [屬性] 窗格。</span><span class="sxs-lookup"><span data-stu-id="8455c-144">Open the Properties pane.</span></span>  
  
    2.  <span data-ttu-id="8455c-145">在設計介面上按一下數列中的任何橫條。</span><span class="sxs-lookup"><span data-stu-id="8455c-145">On the design surface, click any of the bars in the series.</span></span> <span data-ttu-id="8455c-146">數列的屬性會顯示在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="8455c-146">The properties for the series are displayed in the Properties pane.</span></span>  
  
    3.  <span data-ttu-id="8455c-147">在 [一般]  區段中，展開 [CustomAttributes]  節點。</span><span class="sxs-lookup"><span data-stu-id="8455c-147">In the **General** section, expand the **CustomAttributes** node.</span></span>  
  
    4.  <span data-ttu-id="8455c-148">為 [DrawingStyle]  屬性指定 [圓柱]  值。</span><span class="sxs-lookup"><span data-stu-id="8455c-148">For the **DrawingStyle** property, specify the **Cylinder** value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8455c-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8455c-149">See Also</span></span>  
 <span data-ttu-id="8455c-150">[圖表中的 3D、浮凸和其他效果 &#40;報表產生器及 SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="8455c-150">[3D, Bevel, and Other Effects in a Chart &#40;Report Builder and SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md) </span></span>  
 <span data-ttu-id="8455c-151">[格式化圖表 &#40;報表產生器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8455c-151">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="8455c-152">圖表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8455c-152">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
