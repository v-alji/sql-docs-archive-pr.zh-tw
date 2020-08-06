---
title: 新增刻度斷層至圖表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 84d66436-ed62-4967-bbbd-b457593ee787
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1c081debd1e0a84158615edebdb6b84705c10e5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703857"
---
# <a name="add-scale-breaks-to-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="35a8d-102">將刻度斷層加入至圖表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="35a8d-102">Add Scale Breaks to a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="35a8d-103">刻度斷層是在圖表繪圖區上繪製的一道區域線，代表在值軸高低值之間的延續性有斷層 (通常是垂直軸或 Y 軸)。</span><span class="sxs-lookup"><span data-stu-id="35a8d-103">A scale break is a stripe drawn across the plotting area of a chart to denote a break in continuity between the high and low values on a value axis (usually the vertical, or y-axis).</span></span> <span data-ttu-id="35a8d-104">使用刻度斷層可在相同的圖表區域中顯示兩個相異的範圍。</span><span class="sxs-lookup"><span data-stu-id="35a8d-104">Use a scale break to display two distinct ranges in the same chart area.</span></span>  
  
 <span data-ttu-id="35a8d-105">![具有刻度斷層的圖表](../media/rs-multipledatarangeschart-scalebreak.gif "具有刻度斷層的圖表")</span><span class="sxs-lookup"><span data-stu-id="35a8d-105">![Chart with scale break](../media/rs-multipledatarangeschart-scalebreak.gif "Chart with scale break")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="35a8d-106">您無法指定刻度斷層在圖表上的放置位置。</span><span class="sxs-lookup"><span data-stu-id="35a8d-106">You cannot specify where to place a scale break on your chart.</span></span> <span data-ttu-id="35a8d-107">圖表會根據資料集中的值，自行計算資料範圍之間是否有足夠的分隔，以在執行階段於值軸 (Y 軸) 上繪製刻度斷層。</span><span class="sxs-lookup"><span data-stu-id="35a8d-107">The chart uses its own calculations based on the values in your dataset to determine whether there is sufficient separation between data ranges to draw a scale break on the value axis (y-axis) at run time.</span></span>  
  
 <span data-ttu-id="35a8d-108">具有刻度斷層的圖表範例可從範例報表取得。</span><span class="sxs-lookup"><span data-stu-id="35a8d-108">An example of a chart with scale breaks is available as a sample report.</span></span> <span data-ttu-id="35a8d-109">如需下載這個範例報表及其他項目的詳細資訊，請參閱 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][報表產生器與報表設計師範例報表](https://go.microsoft.com/fwlink/?LinkId=198283)：</span><span class="sxs-lookup"><span data-stu-id="35a8d-109">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-enable-scale-breaks-on-the-chart"></a><span data-ttu-id="35a8d-110">若要在圖表上啟用刻度斷層</span><span class="sxs-lookup"><span data-stu-id="35a8d-110">To enable scale breaks on the chart</span></span>  
  
1.  <span data-ttu-id="35a8d-111">以滑鼠右鍵按一下垂直軸，然後按一下 [軸屬性]  。</span><span class="sxs-lookup"><span data-stu-id="35a8d-111">Right-click the vertical axis and then click **Axis Properties**.</span></span> <span data-ttu-id="35a8d-112">[垂直軸屬性]  對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="35a8d-112">The **VerticalAxis Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="35a8d-113">選取 [啟用刻度斷層]  核取方塊。</span><span class="sxs-lookup"><span data-stu-id="35a8d-113">Select the **Enable scale breaks** check box.</span></span>  
  
### <a name="to-change-the-style-of-the-scale-break"></a><span data-ttu-id="35a8d-114">變更刻度斷層的樣式</span><span class="sxs-lookup"><span data-stu-id="35a8d-114">To change the style of the scale break</span></span>  
  
1.  <span data-ttu-id="35a8d-115">開啟 [屬性] 窗格。</span><span class="sxs-lookup"><span data-stu-id="35a8d-115">Open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="35a8d-116">以滑鼠右鍵在設計介面上按一下圖表的 Y 軸。</span><span class="sxs-lookup"><span data-stu-id="35a8d-116">On the design surface, right-click on the y-axis of the chart.</span></span> <span data-ttu-id="35a8d-117">Y 軸物件的屬性 (依預設名為「圖表軸」) 會顯示在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="35a8d-117">The properties for the y-axis object (named Chart Axis by default) are displayed in the Properties pane.</span></span>  
  
3.  <span data-ttu-id="35a8d-118">在 [刻度]  區段中，展開 ScaleBreakStyle 屬性。</span><span class="sxs-lookup"><span data-stu-id="35a8d-118">In the **Scale** section, expand the ScaleBreakStyle property.</span></span>  
  
4.  <span data-ttu-id="35a8d-119">變更 ScaleBreakStyle 屬性的值，例如 BreakLineType 和 Spacing。</span><span class="sxs-lookup"><span data-stu-id="35a8d-119">Change the values for ScaleBreakStyle properties, such as BreakLineType and Spacing.</span></span> <span data-ttu-id="35a8d-120">如需刻度中斷線屬性的詳細資訊，請參閱[將包含多個資料範圍的數列顯示在圖表上 &#40;報表產生器及 SSRS&#41;](displaying-a-series-with-multiple-data-ranges-on-a-chart.md)。</span><span class="sxs-lookup"><span data-stu-id="35a8d-120">For more information about scale break properties, see [Displaying a Series with Multiple Data Ranges on a Chart &#40;Report Builder and SSRS&#41;](displaying-a-series-with-multiple-data-ranges-on-a-chart.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35a8d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35a8d-121">See Also</span></span>  
 <span data-ttu-id="35a8d-122">[圖表 &#40;報表產生器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="35a8d-122">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="35a8d-123">[將圖表格式化 &#40;報表產生器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="35a8d-123">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="35a8d-124">軸屬性對話方塊，軸選項 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="35a8d-124">Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;</span></span>](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md)  
  
  
