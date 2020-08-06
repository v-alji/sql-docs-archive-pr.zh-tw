---
title: 在圓形圖上顯示百分比值 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eb905fc1-5235-4773-a27e-b07be9318be5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2dee9017d34f2751b790b2e4928571160b597f1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595736"
---
# <a name="display-percentage-values-on-a-pie-chart-report-builder-and-ssrs"></a><span data-ttu-id="22e4f-102">在圓形圖上顯示百分比值 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="22e4f-102">Display Percentage Values on a Pie Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="22e4f-103">根據預設，圖例中會顯示類別目錄來識別每個值。</span><span class="sxs-lookup"><span data-stu-id="22e4f-103">By default, categories are shown in the legend to identify each value.</span></span> <span data-ttu-id="22e4f-104">如果您已使用類別目錄標籤做為圓形圖的標籤，則可能會想在圖例中顯示百分比。</span><span class="sxs-lookup"><span data-stu-id="22e4f-104">If you have labeled the pie chart using category labels, you may want show percentages in the legend.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-percentage-values-as-labels-on-a-pie-chart"></a><span data-ttu-id="22e4f-105">將百分比值顯示為圓形圖的標籤</span><span class="sxs-lookup"><span data-stu-id="22e4f-105">To display percentage values as labels on a pie chart</span></span>  
  
1.  <span data-ttu-id="22e4f-106">將圓形圖加入到報表中。</span><span class="sxs-lookup"><span data-stu-id="22e4f-106">Add a pie chart to your report.</span></span> <span data-ttu-id="22e4f-107">如需詳細資訊，請參閱[將圖表加入至報表 &#40;報表產生器及 SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="22e4f-107">For more information, see [Add a Chart to a Report &#40;Report Builder and SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="22e4f-108">在設計介面上，以滑鼠右鍵按一下圓形圖，然後選取 [顯示資料標籤]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="22e4f-108">On the design surface, right-click on the pie and select **Show Data Labels**.</span></span> <span data-ttu-id="22e4f-109">資料標籤會顯示在圓形圖的每個扇區內。</span><span class="sxs-lookup"><span data-stu-id="22e4f-109">The data labels should appear within each slice on the pie chart.</span></span>  
  
3.  <span data-ttu-id="22e4f-110">在設計介面上，以滑鼠右鍵按一下標籤，然後選取 [數列標籤屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="22e4f-110">On the design surface, right-click on the labels and select **Series Label Properties**.</span></span> <span data-ttu-id="22e4f-111">[數列標籤屬性]\*\*\*\* 對話方塊便會出現。</span><span class="sxs-lookup"><span data-stu-id="22e4f-111">The **Series Label Properties** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="22e4f-112">`#PERCENT`針對 [**標籤資料**] 選項輸入。</span><span class="sxs-lookup"><span data-stu-id="22e4f-112">Type `#PERCENT` for the **Label data** option.</span></span>  
  
5.  <span data-ttu-id="22e4f-113">(選擇性) 若要指定標籤所顯示的小數位數，請輸入 "#PERCENT{P*n*}"，其中 *n* 是要顯示的小數位數。</span><span class="sxs-lookup"><span data-stu-id="22e4f-113">(Optional) To specify how many decimal places the label shows, type "#PERCENT{P*n*}" where *n* is the number of decimal places to display.</span></span> <span data-ttu-id="22e4f-114">例如，如果不要顯示任何小數位數，請輸入 "#PERCENT{P0}"。</span><span class="sxs-lookup"><span data-stu-id="22e4f-114">For example, to display no decimal places, type "#PERCENT{P0}".</span></span>  
  
### <a name="to-display-percentage-values-in-the-legend-of-a-pie-chart"></a><span data-ttu-id="22e4f-115">若要在圓形圖的圖例中顯示百分比值</span><span class="sxs-lookup"><span data-stu-id="22e4f-115">To display percentage values in the legend of a pie chart</span></span>  
  
1.  <span data-ttu-id="22e4f-116">在設計介面上，以滑鼠右鍵按一下圓形圖，然後選取 [數列屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="22e4f-116">On the design surface, right-click on the pie chart and select **Series Properties**.</span></span> <span data-ttu-id="22e4f-117">[數列屬性]\*\*\*\* 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="22e4f-117">The **Series Properties** dialog box displays.</span></span>  
  
2.  <span data-ttu-id="22e4f-118">在 [**圖例**] 中， `#PERCENT` 針對 [**自訂圖例文字**] 屬性輸入。</span><span class="sxs-lookup"><span data-stu-id="22e4f-118">In **Legend**, type `#PERCENT` for the **Custom legend text** property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22e4f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22e4f-119">See Also</span></span>  
 <span data-ttu-id="22e4f-120">[圓形圖 &#40;報表產生器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="22e4f-120">[Pie Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="22e4f-121">[在圖表上格式化圖例 &#40;報表產生器和 SSRS&#41;](chart-legend-formatting-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="22e4f-121">[Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;](chart-legend-formatting-report-builder.md) </span></span>  
 <span data-ttu-id="22e4f-122">[在圓形圖外部顯示資料點標籤 &#40;報表產生器和 SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="22e4f-122">[Display Data Point Labels Outside a Pie Chart &#40;Report Builder and SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="22e4f-123">收集圓形圖上的小配量 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="22e4f-123">Collect Small Slices on a Pie Chart &#40;Report Builder and SSRS&#41;</span></span>](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  
