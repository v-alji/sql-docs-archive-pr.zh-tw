---
title: 變更圖例項目的文字 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9e82fa34-17ed-494f-b25d-03dcc353a21f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0d0bb721aa0ff03a5211065111c98605cd86e971
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599367"
---
# <a name="change-the-text-of-a-legend-item-report-builder-and-ssrs"></a><span data-ttu-id="e3770-102">變更圖例項目的文字 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="e3770-102">Change the Text of a Legend Item (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e3770-103">將欄位放在圖表的 [值] 區域中時，系統會自動產生包含此欄位名稱的圖例項目。</span><span class="sxs-lookup"><span data-stu-id="e3770-103">When a field is placed in the Values area of the chart, a legend item is automatically generated that contains the name of this field.</span></span> <span data-ttu-id="e3770-104">每個圖例項目都會連接到報表上的個別數列，但是形狀圖例外 (其圖例會連接到個別資料點而非個別數列)。</span><span class="sxs-lookup"><span data-stu-id="e3770-104">Every legend item is connected to an individual series on the chart, with the exception of shape charts, where the legend is connected to individual data points instead of individual series.</span></span>  
  
 <span data-ttu-id="e3770-105">在形狀圖上，您可以變更圖例項目的文字，以顯示有關個別資料點的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e3770-105">On shape charts, you can change the text of a legend item to show more information about the individual data points.</span></span> <span data-ttu-id="e3770-106">例如，如果您要將資料點的值顯示為圖例中的百分比，可以使用關鍵字 (如 `#PERCENT`)。</span><span class="sxs-lookup"><span data-stu-id="e3770-106">For example, if you want to show the values of the data points as percentages in the legend, you can use a keyword such as `#PERCENT`.</span></span> <span data-ttu-id="e3770-107">您可以配合關鍵字附加 .NET Framework 格式化程式碼來套用數值和日期格式。</span><span class="sxs-lookup"><span data-stu-id="e3770-107">You can append .NET Framework format codes in conjunction with keywords to apply numeric and date formats.</span></span> <span data-ttu-id="e3770-108">如需關鍵字的詳細資訊，請參閱[格式化圖表上的資料點 &#40;報表產生器及 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e3770-108">For more information about keywords, see [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="e3770-109">![鮮明的圖表](../media/sharpchart.png "鮮明的圖表")</span><span class="sxs-lookup"><span data-stu-id="e3770-109">![Sharp Chart](../media/sharpchart.png "Sharp Chart")</span></span>  
  
 <span data-ttu-id="e3770-110">在非形狀圖上，您可以變更圖例項目的文字。</span><span class="sxs-lookup"><span data-stu-id="e3770-110">On non-shape charts, you can change the text of a legend item.</span></span> <span data-ttu-id="e3770-111">例如，如果您的數列名稱為 "Series1"，您可能想要變更為其他敘述性的文字，例如 "Sales for 2008"。</span><span class="sxs-lookup"><span data-stu-id="e3770-111">For example, if your series name is "Series1", you may want to change the text to something more descriptive like "Sales for 2008".</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-modify-the-text-that-appears-in-the-legend-on-a-shape-chart"></a><span data-ttu-id="e3770-112">在形狀圖上修改出現在圖例中的文字</span><span class="sxs-lookup"><span data-stu-id="e3770-112">To modify the text that appears in the legend on a Shape chart</span></span>  
  
1.  <span data-ttu-id="e3770-113">以滑鼠右鍵按一下數列，或以滑鼠右鍵按一下 [值]  區域中的欄位，然後選取 [數列屬性]  。</span><span class="sxs-lookup"><span data-stu-id="e3770-113">Right-click on a series, or right-click on a field in the **Values** area, and select **Series Properties**.</span></span>  
  
2.  <span data-ttu-id="e3770-114">按一下 [圖例]  ，然後在 [自訂圖例文字]  方塊中鍵入關鍵字。</span><span class="sxs-lookup"><span data-stu-id="e3770-114">Click **Legend** and in the **Custom legend text** box, type a keyword.</span></span>  
  
 <span data-ttu-id="e3770-115">下表提供用於 [自訂圖例文字]  屬性之圖表特定關鍵字的範例。</span><span class="sxs-lookup"><span data-stu-id="e3770-115">The following table provides examples of chart-specific keywords to use for the **Custom Legend Text** property.</span></span> <span data-ttu-id="e3770-116">如需關鍵字的詳細資訊，請參閱[格式化圖表上的資料點 &#40;報表產生器及 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e3770-116">For more information about keywords, see [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
|<span data-ttu-id="e3770-117">關鍵字</span><span class="sxs-lookup"><span data-stu-id="e3770-117">Keyword</span></span>|<span data-ttu-id="e3770-118">描述</span><span class="sxs-lookup"><span data-stu-id="e3770-118">Description</span></span>|<span data-ttu-id="e3770-119">在圖例中顯示為文字的範例</span><span class="sxs-lookup"><span data-stu-id="e3770-119">Example of what appears as text in the legend</span></span>|  
|-------------|-----------------|---------------------------------------------------|  
|`#PERCENT{P1}`|<span data-ttu-id="e3770-120">將總值的百分比顯示為一個小數位數。</span><span class="sxs-lookup"><span data-stu-id="e3770-120">Displays the percentage of the total value to one decimal place.</span></span>|<span data-ttu-id="e3770-121">85.0%</span><span class="sxs-lookup"><span data-stu-id="e3770-121">85.0%</span></span>|  
|`#VALY`|<span data-ttu-id="e3770-122">顯示資料欄位的實際數值。</span><span class="sxs-lookup"><span data-stu-id="e3770-122">Displays the actual numeric value of the data field.</span></span>|<span data-ttu-id="e3770-123">17000</span><span class="sxs-lookup"><span data-stu-id="e3770-123">17000</span></span>|  
|`#VALY{C2}`|<span data-ttu-id="e3770-124">將資料欄位的實際數值顯示為兩個小數位數的貨幣。</span><span class="sxs-lookup"><span data-stu-id="e3770-124">Displays the actual numeric value of the data field as a currency to two decimal places.</span></span>|<span data-ttu-id="e3770-125">$17000.00</span><span class="sxs-lookup"><span data-stu-id="e3770-125">$17000.00</span></span>|  
|`#AXISLABEL (#PERCENT{P0})`|<span data-ttu-id="e3770-126">顯示類別目錄欄位的文字表示法，後面接著每個類別目錄顯示在圖表上的百分比。</span><span class="sxs-lookup"><span data-stu-id="e3770-126">Displays the text representation of the category field, followed by the percentage that each category displays on the chart.</span></span>|<span data-ttu-id="e3770-127">Michael Blythe (85%)</span><span class="sxs-lookup"><span data-stu-id="e3770-127">Michael Blythe (85%)</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="e3770-128">在 [數列群組]  區域中沒有指定任何欄位時，只能在執行階段評估 #AXISLABEL 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="e3770-128">The #AXISLABEL keyword can only be evaluated at run time when there is not a field specified in the **Series Groups** area.</span></span>  
  
### <a name="to-modify-the-text-that-appears-in-the-legend-on-a-non-shape-chart"></a><span data-ttu-id="e3770-129">在非形狀圖上修改出現在圖例中的文字</span><span class="sxs-lookup"><span data-stu-id="e3770-129">To modify the text that appears in the legend on a non-Shape chart</span></span>  
  
1.  <span data-ttu-id="e3770-130">以滑鼠右鍵按一下數列，或以滑鼠右鍵按一下 [值]  區域中的欄位，然後選取 [數列屬性]  。</span><span class="sxs-lookup"><span data-stu-id="e3770-130">Right-click on a series, or right-click on a field in the **Values** area, and select **Series Properties**.</span></span>  
  
2.  <span data-ttu-id="e3770-131">按一下 [圖例]  ，然後在 [自訂圖例文字]  方塊中鍵入圖例標籤。</span><span class="sxs-lookup"><span data-stu-id="e3770-131">Click **Legend** and in the **Custom legend text** box, type a legend label.</span></span> <span data-ttu-id="e3770-132">數列會隨著您的文字更新。</span><span class="sxs-lookup"><span data-stu-id="e3770-132">The series is updated with your text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3770-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3770-133">See Also</span></span>  
 <span data-ttu-id="e3770-134">[在圖表上格式化圖例 &#40;報表產生器及 SSRS&#41;](chart-legend-formatting-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="e3770-134">[Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;](chart-legend-formatting-report-builder.md) </span></span>  
 <span data-ttu-id="e3770-135">[設定圖表上數列色彩的格式 &#40;報表產生器及 SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e3770-135">[Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e3770-136">隱藏圖表上的圖例項目 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e3770-136">Hide Legend Items on the Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-legend-hide-items-report-builder.md)  
  
  
