---
title: 在數列上顯示工具提示 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4c9606ff-e1c3-4cf7-a4e7-bb16f1a9e8ab
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9113ec843b3b9255f380b17ee1ab6b360fa1f60d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599347"
---
# <a name="show-tooltips-on-a-series-report-builder-and-ssrs"></a><span data-ttu-id="3be04-102">在數列上顯示工具提示 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="3be04-102">Show ToolTips on a Series (Report Builder and SSRS)</span></span>
  <span data-ttu-id="3be04-103">您可以將工具提示加入到圖表數列上的每個資料點，以便在使用者將滑鼠指標停留在已轉譯之報表中的資料點時，顯示與資料點相關的資訊，例如，群組名稱、資料點的值，或相對於數列總數之資料點的百分比。</span><span class="sxs-lookup"><span data-stu-id="3be04-103">You can add a ToolTip to each data point on the series of a chart to display information related to the data point, such as the group name, the value of the data point, or the percentage of the data point relative to the series total when users hover over the data point in a rendered report.</span></span>  
  
 <span data-ttu-id="3be04-104">您無法將工具提示加入到導出數列。</span><span class="sxs-lookup"><span data-stu-id="3be04-104">You cannot add a ToolTip to a calculated series.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-a-tooltip-on-each-data-point"></a><span data-ttu-id="3be04-105">在每個資料點上指定工具提示</span><span class="sxs-lookup"><span data-stu-id="3be04-105">To specify a ToolTip on each data point</span></span>  
  
1.  <span data-ttu-id="3be04-106">以滑鼠右鍵按一下數列，或以滑鼠右鍵按一下 [值]\*\*\*\* 區域中的欄位，然後按一下 [數列屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3be04-106">Right-click on the series or right-click on the field in the **Values** area, and click **Series Properties**.</span></span>  
  
2.  <span data-ttu-id="3be04-107">按一下 **[數列資料]** ，然後針對 **[工具提示]** 屬性，輸入字串或運算式。</span><span class="sxs-lookup"><span data-stu-id="3be04-107">Click **Series Data** and, for the **ToolTip** property, type in a string or expression.</span></span> <span data-ttu-id="3be04-108">您可以使用任何圖表專用的關鍵字來表示圖表上的其他元素。</span><span class="sxs-lookup"><span data-stu-id="3be04-108">You can use any chart-specific keyword to represent another element on the chart.</span></span> <span data-ttu-id="3be04-109">如需詳細資訊，請參閱 [格式化圖表上的資料點 &#40;報表產生器及 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="3be04-109">For more information, see [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3be04-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3be04-110">See Also</span></span>  
 <span data-ttu-id="3be04-111">[格式化圖表上的資料點 &#40;報表產生器和 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3be04-111">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3be04-112">[將圖例專案的文字變更 &#40;報表產生器及 SSRS&#41;](chart-legend-change-item-text-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="3be04-112">[Change the Text of a Legend Item &#40;Report Builder and SSRS&#41;](chart-legend-change-item-text-report-builder.md) </span></span>  
 <span data-ttu-id="3be04-113">[格式化圖表上的數列色彩 &#40;報表產生器和 SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3be04-113">[Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="3be04-114">在報表上新增鑽研動作 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3be04-114">Add a Drillthrough Action on a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-drillthrough-action-on-a-report-report-builder-and-ssrs.md)  
  
  
