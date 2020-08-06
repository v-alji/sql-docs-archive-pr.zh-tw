---
title: 隱藏圖表上的圖例項目 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 92256240-0cd5-4be4-8904-d1e3b93cb6b3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 20444432f580ffaf1c5f4de1320b06319f973a01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599360"
---
# <a name="hide-legend-items-on-the-chart-report-builder-and-ssrs"></a><span data-ttu-id="516d1-102">隱藏圖表上的圖例項目 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="516d1-102">Hide Legend Items on the Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="516d1-103">根據預設，加入到非形狀圖中的任何數列都會當做圖例中的項目加入。</span><span class="sxs-lookup"><span data-stu-id="516d1-103">By default, any series added to a non-Shape chart will be added as an item in the legend.</span></span> <span data-ttu-id="516d1-104">至於圓形圖、環圈圖、漏斗圖與金字塔圖，加入到圖表中的任何數列則會在圖例中加入個別的資料點。</span><span class="sxs-lookup"><span data-stu-id="516d1-104">For pie, doughnut, funnel, and pyramid charts, any series added to the chart will add individual data points in the legend.</span></span>  
  
 <span data-ttu-id="516d1-105">您可以隱藏圖例上的任何項目。</span><span class="sxs-lookup"><span data-stu-id="516d1-105">You can hide any item on the legend.</span></span> <span data-ttu-id="516d1-106">當您隱藏圖例項目時，該項目仍然會出現在圖表中。</span><span class="sxs-lookup"><span data-stu-id="516d1-106">When you hide a legend item, it will still appear in the chart.</span></span> <span data-ttu-id="516d1-107">當您不要顯示加入至圖表中之數列的詳細資訊時，此功能相當實用。</span><span class="sxs-lookup"><span data-stu-id="516d1-107">This is useful in situations where you do not want to show more information for a series that is added to the chart.</span></span> <span data-ttu-id="516d1-108">例如，如果您已經加入導出數列，例如圖表的移動平均，您可能想要在圖例中隱藏這個項目，只顯示原始數列的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="516d1-108">For example, if you have added a calculated series like a moving average to the chart, you may want to hide this entry in the legend so that more information is only shown for the original series.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-hide-an-item-from-display-in-the-legend"></a><span data-ttu-id="516d1-109">隱藏圖例中顯示的項目</span><span class="sxs-lookup"><span data-stu-id="516d1-109">To hide an item from display in the legend</span></span>  
  
1.  <span data-ttu-id="516d1-110">以滑鼠右鍵按一下您要隱藏的數列，然後選取 [數列屬性]  。</span><span class="sxs-lookup"><span data-stu-id="516d1-110">Right-click on the series you want to hide and select **Series Properties**.</span></span>  
  
2.  <span data-ttu-id="516d1-111">按一下 **[圖例]** 。</span><span class="sxs-lookup"><span data-stu-id="516d1-111">Click **Legend**.</span></span> <span data-ttu-id="516d1-112">選取 **[不要在圖例中顯示此數列]** 選項。</span><span class="sxs-lookup"><span data-stu-id="516d1-112">Select the **Do not show this series in a legend** option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="516d1-113">您無法針對一個群組而不在其他群組中隱藏數列。</span><span class="sxs-lookup"><span data-stu-id="516d1-113">You cannot hide a series for one group and not for the others.</span></span> <span data-ttu-id="516d1-114">如果您已經將欄位加入到 **[數列群組]** 區域，將會隱藏屬於此群組的所有數列。</span><span class="sxs-lookup"><span data-stu-id="516d1-114">If you have added a field to the **Series Groups** area, all series belonging to this group will be hidden.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="516d1-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="516d1-115">See Also</span></span>  
 <span data-ttu-id="516d1-116">[在圖表上格式化圖例 &#40;報表產生器及 SSRS&#41;](chart-legend-formatting-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="516d1-116">[Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;](chart-legend-formatting-report-builder.md) </span></span>  
 <span data-ttu-id="516d1-117">[格式化圖表上的資料點 &#40;報表產生器和 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="516d1-117">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="516d1-118">[變更圖例項目的文字 &#40;報表產生器及 SSRS&#41;](chart-legend-change-item-text-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="516d1-118">[Change the Text of a Legend Item &#40;Report Builder and SSRS&#41;](chart-legend-change-item-text-report-builder.md) </span></span>  
 <span data-ttu-id="516d1-119">[將移動平均新增至圖表 &#40;報表產生器及 SSRS&#41;](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="516d1-119">[Add a Moving Average to a Chart &#40;Report Builder and SSRS&#41;](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="516d1-120">圖例屬性對話方塊、一般 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="516d1-120">Legend Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../legend-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
