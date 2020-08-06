---
title: 軸屬性對話方塊、軸選項 (報表產生器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.axisproperties.axisoptions.f1
- "10138"
ms.assetid: b276e210-7a12-48ae-971b-7dabae51df11
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a94c4de6487d111417ef7ad3cee53a4172b5d275
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595818"
---
# <a name="axis-properties-dialog-box-axis-options-report-builder-and-ssrs"></a><span data-ttu-id="7e714-102">軸屬性對話方塊、軸選項 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="7e714-102">Axis Properties Dialog Box, Axis Options (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7e714-103">選取 [**水準**] 或 [**垂直軸屬性**] 對話方塊上的 [**軸選項**]，即可定義圖表中指定之軸的外觀。</span><span class="sxs-lookup"><span data-stu-id="7e714-103">Select **Axis Options** on the **Horizontal** or **VerticalAxis Properties** dialog box to define the appearance of the specified axis of the chart.</span></span> <span data-ttu-id="7e714-104">在舊版 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]中，圖表預設會顯示 X 軸上的所有標籤。</span><span class="sxs-lookup"><span data-stu-id="7e714-104">In previous versions of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], the chart displayed all labels on the x-axis by default.</span></span> <span data-ttu-id="7e714-105">不過，在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2008 中，圖表會略過標籤，以便產生較清晰的圖表影像並避免標籤互相衝突。</span><span class="sxs-lookup"><span data-stu-id="7e714-105">However, in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2008, the chart skips labels in order to produce a cleaner image on the chart and avoid labeling collisions.</span></span> <span data-ttu-id="7e714-106">如需詳細資訊，請參閱[格式化圖表上的軸標籤 &#40;報表產生器及 SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7e714-106">For more information, see [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="7e714-107">選項</span><span class="sxs-lookup"><span data-stu-id="7e714-107">Options</span></span>  
 <span data-ttu-id="7e714-108">**啟用刻度斷層**</span><span class="sxs-lookup"><span data-stu-id="7e714-108">**Enable scale breaks**</span></span>  
 <span data-ttu-id="7e714-109">選擇此選項讓圖表在必要時，繪製刻度斷層。</span><span class="sxs-lookup"><span data-stu-id="7e714-109">Select this option to enable the chart to draw a scale breaks when it is deemed necessary.</span></span> <span data-ttu-id="7e714-110">啟用此選項時，圖表會先自動計算資料集的高低點之間是否有足夠的差距，然後才繪製刻度斷層。</span><span class="sxs-lookup"><span data-stu-id="7e714-110">When this option is enabled, the chart will automatically calculate whether there is sufficient difference between the high and low points in the dataset to draw a scale break.</span></span>  
  
 <span data-ttu-id="7e714-111">**相反方向**</span><span class="sxs-lookup"><span data-stu-id="7e714-111">**Reverse direction**</span></span>  
 <span data-ttu-id="7e714-112">選取這個選項來反轉圖表的方向。</span><span class="sxs-lookup"><span data-stu-id="7e714-112">Select this option to reverse the direction of the chart.</span></span> <span data-ttu-id="7e714-113">例如，依預設，直條圖會在圖表左側顯示 Y 軸，而類別目錄由左至右顯示。</span><span class="sxs-lookup"><span data-stu-id="7e714-113">For example, by default, a column chart displays the y-axis on the left side of the chart and categories from left to right.</span></span> <span data-ttu-id="7e714-114">選取此選項時，圖表會在圖表右側顯示 Y 軸，而類別目錄由右至左顯示。</span><span class="sxs-lookup"><span data-stu-id="7e714-114">When this option is selected, the chart displays the y-axis on the right side of the chart and categories from right to left.</span></span>  
  
 <span data-ttu-id="7e714-115">**使用交錯式色彩**</span><span class="sxs-lookup"><span data-stu-id="7e714-115">**Use interlacing color**</span></span>  
 <span data-ttu-id="7e714-116">選取此選項可將帶狀線加入至圖表，然後選取色彩或輸入運算式。</span><span class="sxs-lookup"><span data-stu-id="7e714-116">Select this option to add strip lines to the chart, and then select a color or type an expression.</span></span> <span data-ttu-id="7e714-117">帶狀線是圖表區域上有陰影的曲線，可以在格線之間提供明暗交錯之區域的效果。</span><span class="sxs-lookup"><span data-stu-id="7e714-117">Strip lines are shaded bands on the chart area that give the effect of alternating light and dark areas between gridlines.</span></span> <span data-ttu-id="7e714-118">這些帶狀線非常適合在軸上強調重複的圖樣。</span><span class="sxs-lookup"><span data-stu-id="7e714-118">These strip lines are useful for highlighting repeating patterns on an axis.</span></span>  
  
 <span data-ttu-id="7e714-119">**永遠包含零**</span><span class="sxs-lookup"><span data-stu-id="7e714-119">**Always include zero**</span></span>  
 <span data-ttu-id="7e714-120">選取此選項即可在軸刻度上永遠包含零。</span><span class="sxs-lookup"><span data-stu-id="7e714-120">Select this option to always include zero on the axis scale.</span></span> <span data-ttu-id="7e714-121">如果未啟用此選項，圖表將不會在軸上標示零值。</span><span class="sxs-lookup"><span data-stu-id="7e714-121">If this option is not enabled, the chart will not label the zero value on the axis.</span></span> <span data-ttu-id="7e714-122">當資料集包含負值或零值時，包含零值相當實用。</span><span class="sxs-lookup"><span data-stu-id="7e714-122">Including zero values is useful when the dataset includes negative or zero values.</span></span>  
  
 <span data-ttu-id="7e714-123">**純量軸**</span><span class="sxs-lookup"><span data-stu-id="7e714-123">**Scalar axis**</span></span>  
 <span data-ttu-id="7e714-124">選取此選項即可在連續的刻度上顯示一組軸值。</span><span class="sxs-lookup"><span data-stu-id="7e714-124">Select this option to display a set of axis values on a continuous scale.</span></span> <span data-ttu-id="7e714-125">例如，如果資料集包含 1 月、3 月和 11 月的資料，非純量軸只會顯示這些月份，而純量軸則會顯示一年的所有月份。</span><span class="sxs-lookup"><span data-stu-id="7e714-125">For example, if the dataset contains data for January, March, and November, a non-scalar axis displays only those months, whereas a scalar axis displays all of the months in the year.</span></span>  
  
 <span data-ttu-id="7e714-126">**使用對數刻度**</span><span class="sxs-lookup"><span data-stu-id="7e714-126">**Use logarithmic scale**</span></span>  
 <span data-ttu-id="7e714-127">選取此選項可以表示軸刻度是對數。</span><span class="sxs-lookup"><span data-stu-id="7e714-127">Select this option to indicate that the axis scale is logarithmic.</span></span> <span data-ttu-id="7e714-128">只有在軸包含正數值時，Y 軸上才會提供這個選項。</span><span class="sxs-lookup"><span data-stu-id="7e714-128">This option is available only on the y-axis if the axis contains positive numeric values.</span></span>  
  
 <span data-ttu-id="7e714-129">在此方塊中，輸入在軸設定為使用對數刻度時所要使用的對數基底。</span><span class="sxs-lookup"><span data-stu-id="7e714-129">In the box, type the logarithmic base to use when the axis is set to use a logarithmic scale.</span></span> <span data-ttu-id="7e714-130">根據預設，圖表會針對軸的對數刻度，使用基底 10。</span><span class="sxs-lookup"><span data-stu-id="7e714-130">By default, the chart uses a base of 10 for the logarithmic scale of an axis.</span></span> <span data-ttu-id="7e714-131">只有在軸為數值時，Y 軸上才會提供這個選項。</span><span class="sxs-lookup"><span data-stu-id="7e714-131">This option is available only on the y-axis if the axis is numeric.</span></span>  
  
 <span data-ttu-id="7e714-132">**最低**</span><span class="sxs-lookup"><span data-stu-id="7e714-132">**Minimum**</span></span>  
 <span data-ttu-id="7e714-133">輸入運算式或值當做 X 軸的最小值。</span><span class="sxs-lookup"><span data-stu-id="7e714-133">Type an expression or a value for the minimum value for the x-axis.</span></span> <span data-ttu-id="7e714-134">如果忽略此值，則最小值由資料集所傳回的資料決定。</span><span class="sxs-lookup"><span data-stu-id="7e714-134">If omitted, the minimum value is determined by the data returned by the dataset.</span></span>  
  
 <span data-ttu-id="7e714-135">**最大值**</span><span class="sxs-lookup"><span data-stu-id="7e714-135">**Maximum**</span></span>  
 <span data-ttu-id="7e714-136">輸入運算式或值當做 X 軸的最大值。</span><span class="sxs-lookup"><span data-stu-id="7e714-136">Type an expression or a value for the maximum value for the x-axis.</span></span> <span data-ttu-id="7e714-137">如果忽略此值，則最大值由資料集所傳回的資料決定。</span><span class="sxs-lookup"><span data-stu-id="7e714-137">If omitted, the maximum value is determined by the data returned by the dataset.</span></span>  
  
 <span data-ttu-id="7e714-138">**間隔**</span><span class="sxs-lookup"><span data-stu-id="7e714-138">**Interval**</span></span>  
 <span data-ttu-id="7e714-139">針對軸標籤之間的間隔輸入運算式或值。</span><span class="sxs-lookup"><span data-stu-id="7e714-139">Type an expression or value for the interval between axis labels.</span></span> <span data-ttu-id="7e714-140">例如，輸入 1，即可顯示軸上的每個類別目錄標籤。</span><span class="sxs-lookup"><span data-stu-id="7e714-140">For example, type 1 to display each category label on the axis.</span></span> <span data-ttu-id="7e714-141">輸入 2，即可每隔一個類別目錄標籤進行顯示。</span><span class="sxs-lookup"><span data-stu-id="7e714-141">Type 2 to display every other category label.</span></span> <span data-ttu-id="7e714-142">如果忽略此值，系統就會自動根據資料集的值計算標籤。</span><span class="sxs-lookup"><span data-stu-id="7e714-142">If omitted, the labels are calculated automatically based on the values in the dataset.</span></span>  
  
 <span data-ttu-id="7e714-143">**間隔類型**</span><span class="sxs-lookup"><span data-stu-id="7e714-143">**Interval type**</span></span>  
 <span data-ttu-id="7e714-144">輸入運算式或值當做指定之間隔的間隔類型。</span><span class="sxs-lookup"><span data-stu-id="7e714-144">Type an expression or a value for the interval type of the interval specified.</span></span> <span data-ttu-id="7e714-145">例如，如果您希望間隔為兩天，您要將間隔指定為 [2]\*\*\*\*，並將間隔類型指定為 [天]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7e714-145">For example, if you want the interval to be two days, you will specify **2** for interval and **Days** for interval type.</span></span>  
  
 <span data-ttu-id="7e714-146">**側邊界**</span><span class="sxs-lookup"><span data-stu-id="7e714-146">**Side margins**</span></span>  
 <span data-ttu-id="7e714-147">輸入運算式或選取值，即可在圖表元素和圖表側邊之間加入或移除邊界。</span><span class="sxs-lookup"><span data-stu-id="7e714-147">Type an expression or select a value to add or remove a margin between the chart elements and the sides of the chart.</span></span> <span data-ttu-id="7e714-148">如果此選項設定為 [自動]\*\*\*\*，則會加入側邊界。</span><span class="sxs-lookup"><span data-stu-id="7e714-148">If this option is set to **Auto**, a side margins are added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e714-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e714-149">See Also</span></span>  
 <span data-ttu-id="7e714-150">[格式化圖表上的軸標籤 &#40;報表產生器和 SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7e714-150">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7e714-151">[圖表 &#40;報表產生器和 SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7e714-151">[Charts &#40;Report Builder and SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7e714-152">[格式化圖表上的數列色彩 &#40;報表產生器和 SSRS&#41;](report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7e714-152">[Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7e714-153">[指定報表產生器和 SSRS &#40;的軸間隔&#41;](report-design/specify-an-axis-interval-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7e714-153">[Specify an Axis Interval &#40;Report Builder and SSRS&#41;](report-design/specify-an-axis-interval-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7e714-154">[將軸標籤格式化為日期或貨幣 &#40;報表產生器和 SSRS&#41;](report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7e714-154">[Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7e714-155">[在次要軸上繪製資料 &#40;報表產生器和 SSRS&#41;](report-design/plot-data-on-a-secondary-axis-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7e714-155">[Plot Data on a Secondary Axis &#40;Report Builder and SSRS&#41;](report-design/plot-data-on-a-secondary-axis-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7e714-156">[走勢圖和資料橫條 &#40;報表產生器和 SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7e714-156">[Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7e714-157">加入或移除圖表中的邊界 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7e714-157">Add or Remove Margins from a Chart &#40;Report Builder and SSRS&#41;</span></span>](report-design/add-or-remove-margins-from-a-chart-report-builder-and-ssrs.md)  
  
  
