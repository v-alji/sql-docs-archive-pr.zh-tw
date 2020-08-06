---
title: 設定量測計上範圍的格式 (報表產生器及 SSRS)| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ffdec8ca-3e95-41cd-850b-9e8c83be4b49
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 29574c58eef6f18d685b48dd8d695a5fc42c3e6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686809"
---
# <a name="formatting-ranges-on-a-gauge-report-builder-and-ssrs"></a><span data-ttu-id="02a1e-102">設定量測計上範圍的格式 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="02a1e-102">Formatting Ranges on a Gauge (Report Builder and SSRS)</span></span>
  <span data-ttu-id="02a1e-103">量測計範圍是量測計標尺上的一個區域，表示值在量測計上的重要子區段。</span><span class="sxs-lookup"><span data-stu-id="02a1e-103">A gauge range is a zone or area on the gauge scale that indicates an important subsection of values on the gauge.</span></span> <span data-ttu-id="02a1e-104">您可以使用量測計範圍，以視覺化的方式表示指標值靠近特定值範圍的時間。</span><span class="sxs-lookup"><span data-stu-id="02a1e-104">Using a gauge range, you can visually indicate when the pointer value has gone into a certain span of values.</span></span> <span data-ttu-id="02a1e-105">範圍是由開始值和結束值所定義。</span><span class="sxs-lookup"><span data-stu-id="02a1e-105">Ranges are defined by a start value and an end value.</span></span>  
  
 <span data-ttu-id="02a1e-106">您也可以使用範圍來定義量測計的不同區段。</span><span class="sxs-lookup"><span data-stu-id="02a1e-106">You can also use ranges to define different sections of a gauge.</span></span> <span data-ttu-id="02a1e-107">例如，在值範圍為 0 到 10 的量測計上，您可以定義一個值範圍為 0 到 3 的紅色範圍、一個值範圍為 4 到 7 的黃色範圍，以及一個值範圍為 8 到 10 的綠色範圍。</span><span class="sxs-lookup"><span data-stu-id="02a1e-107">For example, on a gauge with values from 0 to 10, you can define a red range that has a value from 0 to 3, a yellow range that has a value from 4 to 7 and a green range that has a value from 8 to 10.</span></span> <span data-ttu-id="02a1e-108">如果您所指定的開始值大於您所指定的結束值，這些值就會交換，讓開始值變成結束值，而結束值變成開始值。</span><span class="sxs-lookup"><span data-stu-id="02a1e-108">If the start value that you specified is greater than the end value that you specified, the values are swapped so that the start value is the end value and the end value is the start value.</span></span>  
  
 <span data-ttu-id="02a1e-109">您可以使用在標尺上放置指標的相同方式來放置範圍。</span><span class="sxs-lookup"><span data-stu-id="02a1e-109">You can position the range in the same way that you position pointers on a scale.</span></span> <span data-ttu-id="02a1e-110">**[位置]** 和 **[距標尺距離]** 屬性會決定範圍的位置。</span><span class="sxs-lookup"><span data-stu-id="02a1e-110">The **Position** and **Distance from scale** properties determine the position of the range.</span></span> <span data-ttu-id="02a1e-111">如需詳細資訊，請參閱 [量測計 &#40;報表產生器及 SSRS&#41;](gauges-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="02a1e-111">For more information, see [Gauges &#40;Report Builder and SSRS&#41;](gauges-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="02a1e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02a1e-112">See Also</span></span>  
 <span data-ttu-id="02a1e-113">[格式化量測計上的標尺 &#40;報表產生器及 SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="02a1e-113">[Formatting Scales on a Gauge &#40;Report Builder and SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="02a1e-114">[格式化量測計上的指標 &#40;報表產生器及 SSRS&#41;](formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="02a1e-114">[Formatting Pointers on a Gauge &#40;Report Builder and SSRS&#41;](formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="02a1e-115">[設定量測計的最小值或最大值 &#40;報表產生器及 SSRS&#41;](set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="02a1e-115">[Set a Minimum or Maximum on a Gauge &#40;Report Builder and SSRS&#41;](set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="02a1e-116">[教學課程：將 KPI 新增至報表 &#40;報表產生器&#41;](../tutorial-adding-a-kpi-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="02a1e-116">[Tutorial: Adding a KPI to Your Report &#40;Report Builder&#41;](../tutorial-adding-a-kpi-to-your-report-report-builder.md) </span></span>  
 [<span data-ttu-id="02a1e-117">量測計 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="02a1e-117">Gauges &#40;Report Builder and SSRS&#41;</span></span>](gauges-report-builder-and-ssrs.md)  
  
  
