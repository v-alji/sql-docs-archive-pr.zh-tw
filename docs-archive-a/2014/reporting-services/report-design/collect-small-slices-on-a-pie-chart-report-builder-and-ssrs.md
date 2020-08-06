---
title: 收集圓形圖上的小配量 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 21c2b8cb-b9ca-4bc0-bf49-50ba432562f6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2302217843864115847aeb544d1c64727b8ad3a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596502"
---
# <a name="collect-small-slices-on-a-pie-chart-report-builder-and-ssrs"></a><span data-ttu-id="8167f-102">收集圓形圖上的小配量 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="8167f-102">Collect Small Slices on a Pie Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8167f-103">當圓形圖顯示太多資料點時，看起來會很雜亂。</span><span class="sxs-lookup"><span data-stu-id="8167f-103">When pie charts display too many points of data, they begin to look cluttered.</span></span> <span data-ttu-id="8167f-104">若要解決這個問題，您可以將落在特定值以下的所有資料顯示為圓形圖上的一個扇區。</span><span class="sxs-lookup"><span data-stu-id="8167f-104">To resolve this issue, you can show all data that falls beneath a certain value as one slice on the pie chart.</span></span>  
  
 <span data-ttu-id="8167f-105">若要將小扇區收集成一個扇區，請先決定收集小扇區的臨界值是以圓形圖的百分比或是以固定值表示。</span><span class="sxs-lookup"><span data-stu-id="8167f-105">To collect small slices into one slice, first decide whether your threshold for collecting small slices is measured as a percentage of the pie chart or as a fixed value.</span></span> <span data-ttu-id="8167f-106">然後設定 CollectedThreshold 和 CollectedThresholdUsePercent 屬性。將 CollectedThreshold 屬性設定為圖表百分比 (值必須落在這個值以下才會被收集)，或是集合的實際臨界值資料值。</span><span class="sxs-lookup"><span data-stu-id="8167f-106">Then set the CollectedThreshold and CollectedThresholdUsePercent properties.Set the CollectedThreshold property to either the percentage of the chart that a value must fall below to be collected, or the actual threshold data value for collection.</span></span> <span data-ttu-id="8167f-107">將 CollectedThresholdUsePercent 屬性設定為 `True` ，以使用百分比或 `False` 使用實際值。</span><span class="sxs-lookup"><span data-stu-id="8167f-107">Set the CollectedThresholdUsePercent property to `True` to use a percentage or `False` to use an actual value.</span></span>  
  
 <span data-ttu-id="8167f-108">您也可以將小扇區收集成第二個圓形圖，此圖會成為第一個圓形圖的收集扇區的註標。</span><span class="sxs-lookup"><span data-stu-id="8167f-108">You can also collect small slices into a second pie chart that is called out from a collected slice of the first pie chart.</span></span> <span data-ttu-id="8167f-109">第二個圓形圖會繪製在原始圓形圖的右方。</span><span class="sxs-lookup"><span data-stu-id="8167f-109">The second pie chart is drawn to the right of the original pie chart.</span></span>  
  
 <span data-ttu-id="8167f-110">您不能將漏斗圖或金字塔圖的扇區結合成一個扇區。</span><span class="sxs-lookup"><span data-stu-id="8167f-110">You cannot combine slices of funnel or pyramid charts into one slice.</span></span>  
  
 <span data-ttu-id="8167f-111">此圖表的範例可從範例報表取得。</span><span class="sxs-lookup"><span data-stu-id="8167f-111">An example of this chart is available as a sample report.</span></span> <span data-ttu-id="8167f-112">如需下載這個範例報表及其他項目的詳細資訊，請參閱 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][報表產生器與報表設計師範例報表](https://go.microsoft.com/fwlink/?LinkId=198283)：</span><span class="sxs-lookup"><span data-stu-id="8167f-112">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
### <a name="to-collect-small-slices-into-a-single-slice-on-a-pie-chart"></a><span data-ttu-id="8167f-113">將小配量收集成圓形圖上的單一配量</span><span class="sxs-lookup"><span data-stu-id="8167f-113">To collect small slices into a single slice on a pie chart</span></span>  
  
1.  <span data-ttu-id="8167f-114">開啟 [屬性] 窗格。</span><span class="sxs-lookup"><span data-stu-id="8167f-114">Open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="8167f-115">在設計介面上按一下圓形圖的任何配量。</span><span class="sxs-lookup"><span data-stu-id="8167f-115">On the design surface, click on any slice of the pie chart.</span></span> <span data-ttu-id="8167f-116">數列的屬性會顯示在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="8167f-116">The properties for the series are displayed in the Properties pane.</span></span>  
  
3.  <span data-ttu-id="8167f-117">在 [一般] \*\*\*\* 區段中，展開 [CustomAttributes] \*\*\*\* 節點。</span><span class="sxs-lookup"><span data-stu-id="8167f-117">In the **General** section, expand the **CustomAttributes** node.</span></span>  
  
4.  <span data-ttu-id="8167f-118">將 CollectedStyle 屬性設定為 **SingleSlice**。</span><span class="sxs-lookup"><span data-stu-id="8167f-118">Set the CollectedStyle property to **SingleSlice**.</span></span>  
  
5.  <span data-ttu-id="8167f-119">設定收集的臨界值及臨界值類型。</span><span class="sxs-lookup"><span data-stu-id="8167f-119">Set the collected threshold value and type of threshold.</span></span> <span data-ttu-id="8167f-120">下列範例是設定收集臨界值的常見方式。</span><span class="sxs-lookup"><span data-stu-id="8167f-120">The following examples are common ways of setting collected thresholds.</span></span>  
  
    -   <span data-ttu-id="8167f-121">**依百分比。**</span><span class="sxs-lookup"><span data-stu-id="8167f-121">**By percentage.**</span></span> <span data-ttu-id="8167f-122">例如，將圓形圖上少於 10% 的任何扇區收集成單一扇區：</span><span class="sxs-lookup"><span data-stu-id="8167f-122">For example, to collect any slice on your pie chart that is less than 10% into a single slice:</span></span>  
  
         <span data-ttu-id="8167f-123">將 CollectedThresholdUsePercent 屬性設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="8167f-123">Set the CollectedThresholdUsePercent property to `True`.</span></span>  
  
         <span data-ttu-id="8167f-124">將 CollectedThreshold 屬性設定為 **10**。</span><span class="sxs-lookup"><span data-stu-id="8167f-124">Set the CollectedThreshold property to **10**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="8167f-125">如果您將 CollectedStyle 設定為**SingleSlice**，CollectedThreshold 為大於**100**的值，而 CollectedThresholdUsePercent 是 `True` ，則圖表會擲回例外狀況，因為它無法計算百分比。</span><span class="sxs-lookup"><span data-stu-id="8167f-125">If you set CollectedStyle to **SingleSlice**, CollectedThreshold to a value greater than **100**, and CollectedThresholdUsePercent is `True`, the chart will throw an exception because it cannot calculate a percentage.</span></span> <span data-ttu-id="8167f-126">若要解決此問題，請將 CollectedThreshold 設定為小於 **100** 的值。</span><span class="sxs-lookup"><span data-stu-id="8167f-126">To resolve this issue, set the CollectedThreshold to a value less than **100**.</span></span>  
  
    -   <span data-ttu-id="8167f-127">**依資料值。**</span><span class="sxs-lookup"><span data-stu-id="8167f-127">**By data value.**</span></span> <span data-ttu-id="8167f-128">例如，將圓形圖上小於 5000 的任何扇區收集成單一扇區：</span><span class="sxs-lookup"><span data-stu-id="8167f-128">For example, to collect any slice on your pie chart that is less than 5000 into a single slice:</span></span>  
  
         <span data-ttu-id="8167f-129">將 CollectedThresholdUsePercent 屬性設定為 `False` 。</span><span class="sxs-lookup"><span data-stu-id="8167f-129">Set the CollectedThresholdUsePercent property to `False`.</span></span>  
  
         <span data-ttu-id="8167f-130">將 CollectedThreshold 屬性設定為 **5000**。</span><span class="sxs-lookup"><span data-stu-id="8167f-130">Set the CollectedThreshold property to **5000**.</span></span>  
  
6.  <span data-ttu-id="8167f-131">將 CollectedLabel 屬性設為字串，代表會在收集的扇形區上顯示的文字標籤。</span><span class="sxs-lookup"><span data-stu-id="8167f-131">Set the CollectedLabel property to a string that represents the text label that will be shown on the collected slice.</span></span>  
  
7.  <span data-ttu-id="8167f-132">(選擇性) 設定 CollectedSliceExploded、CollectedColor、CollectedLegendText 和 CollectedToolTip 屬性。</span><span class="sxs-lookup"><span data-stu-id="8167f-132">(Optional) Set the CollectedSliceExploded, CollectedColor, CollectedLegendText and CollectedToolTip properties.</span></span> <span data-ttu-id="8167f-133">這些屬性會變更單一扇區的外觀、色彩、標籤文字、圖例文字及工具提示層面。</span><span class="sxs-lookup"><span data-stu-id="8167f-133">These properties change the appearance, color, label text, legend text and tooltip aspects of the single slice.</span></span>  
  
### <a name="to-collect-small-slices-into-a-secondary-callout-pie-chart"></a><span data-ttu-id="8167f-134">將小扇區收集成次要的註標圓形圖</span><span class="sxs-lookup"><span data-stu-id="8167f-134">To collect small slices into a secondary, callout pie chart</span></span>  
  
1.  <span data-ttu-id="8167f-135">請遵循上述步驟 1 - 3。</span><span class="sxs-lookup"><span data-stu-id="8167f-135">Follow Steps 1-3 from above.</span></span>  
  
2.  <span data-ttu-id="8167f-136">將 CollectedStyle 屬性設定為 **CollectedPie**。</span><span class="sxs-lookup"><span data-stu-id="8167f-136">Set the CollectedStyle property to **CollectedPie**.</span></span>  
  
3.  <span data-ttu-id="8167f-137">將 CollectedThresholdproperty 設為一個代表臨界值的值，達到該值時小扇形區會收集為一個扇形區。</span><span class="sxs-lookup"><span data-stu-id="8167f-137">Set the CollectedThresholdproperty to a value that represents the threshold at which small slices will be collected into one slice.</span></span> <span data-ttu-id="8167f-138">當 CollectedStyle 屬性設定為**CollectedPie**時，CollectedThresholdUsePercentproperty 一律會設定為 `True` ，而收集到的閾值一律會以百分比測量。</span><span class="sxs-lookup"><span data-stu-id="8167f-138">When the CollectedStyle property is set to **CollectedPie**, the CollectedThresholdUsePercentproperty is always set to `True`, and the collected threshold is always measured in percent.</span></span>  
  
4.  <span data-ttu-id="8167f-139">(選擇性) 設定 CollectedColor、CollectedLabel、CollectedLegendText 和 CollectedToolTip 屬性。</span><span class="sxs-lookup"><span data-stu-id="8167f-139">(Optional) Set the CollectedColor, CollectedLabel, CollectedLegendText and CollectedToolTip properties.</span></span> <span data-ttu-id="8167f-140">所有其他名為 "Collected" 的屬性都不適用於收集的圓形圖。</span><span class="sxs-lookup"><span data-stu-id="8167f-140">All other properties named "Collected" do not apply to the collected pie.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8167f-141">次要的圓形圖會根據資料中的小扇區而計算，所以只會顯示在預覽中，</span><span class="sxs-lookup"><span data-stu-id="8167f-141">The secondary pie chart is calculated based on the small slices in your data so it will only appear in Preview.</span></span> <span data-ttu-id="8167f-142">而不會出現在設計介面上。</span><span class="sxs-lookup"><span data-stu-id="8167f-142">It does not appear on the design surface.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8167f-143">您無法格式化次要圓形圖。</span><span class="sxs-lookup"><span data-stu-id="8167f-143">You cannot format the secondary pie chart.</span></span> <span data-ttu-id="8167f-144">因為這個緣故，所以我們強烈建議您在收集圓形圖扇區時使用第一種方法。</span><span class="sxs-lookup"><span data-stu-id="8167f-144">For this reason, it is strongly recommended to use the first approach when collecting pie slices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8167f-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8167f-145">See Also</span></span>  
 <span data-ttu-id="8167f-146">[圓形圖 &#40;報表產生器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8167f-146">[Pie Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8167f-147">[格式化圖表上的資料點 &#40;報表產生器和 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8167f-147">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8167f-148">[在圓形圖外部顯示資料點標籤 &#40;報表產生器和 SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8167f-148">[Display Data Point Labels Outside a Pie Chart &#40;Report Builder and SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8167f-149">[在圓形圖上顯示百分比值 &#40;報表產生器和 SSRS&#41;](display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8167f-149">[Display Percentage Values on a Pie Chart &#40;Report Builder and SSRS&#41;](display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="8167f-150">將 3D 效果新增至圖表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8167f-150">Add 3D Effects to a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-effects-add-3d-effects-report-builder.md)  
  
  
