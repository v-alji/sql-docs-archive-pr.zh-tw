---
title: 設定量測計的貼齊間隔 (報表產生器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0ece7297-6e2f-47fb-835d-b9e9cce53fe2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bdc2a621c4406791838d97e93f47cd32fa9d5f94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703781"
---
# <a name="set-a-snapping-interval-on-a-gauge-report-builder-and-ssrs"></a><span data-ttu-id="c004e-102">設定量測計的貼齊間隔 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="c004e-102">Set a Snapping Interval on a Gauge (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c004e-103">貼齊間隔會定義捨入值的倍數。</span><span class="sxs-lookup"><span data-stu-id="c004e-103">A snapping interval defines the multiple to which values are rounded.</span></span> <span data-ttu-id="c004e-104">根據預設，量測計將指向您在資料窗格中指定之欄位的確切值。</span><span class="sxs-lookup"><span data-stu-id="c004e-104">By default, the gauge will point to the exact value of the field you have specified in the data pane.</span></span> <span data-ttu-id="c004e-105">不過，您可能會想要向上或向下捨入確切值，以便讓指標貼齊預設的間隔。</span><span class="sxs-lookup"><span data-stu-id="c004e-105">However, you may want to round the exact value up or down so that the pointer will snap to a preset interval.</span></span> <span data-ttu-id="c004e-106">例如，如果量測計的值為 34.2，而且您將貼齊間隔指定為 5，則量測計指標將會指向 35。</span><span class="sxs-lookup"><span data-stu-id="c004e-106">For example, if the value on your gauge is 34.2 and you specify a snapping interval of 5, the gauge pointer will point to 35.</span></span> <span data-ttu-id="c004e-107">如果量測計的值為 31.2，而且您將貼齊間隔指定為 5，則量測計指標將會指向 30。</span><span class="sxs-lookup"><span data-stu-id="c004e-107">If the value on your gauge is 31.2 and you specify a snapping interval of 5, the gauge pointer will point to 30.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-a-snapping-interval-on-a-gauge"></a><span data-ttu-id="c004e-108">設定量測計的貼齊間隔</span><span class="sxs-lookup"><span data-stu-id="c004e-108">To set a snapping interval on a gauge</span></span>  
  
1.  <span data-ttu-id="c004e-109">按一下量測計數字的任何位置，以便反白顯示標尺。</span><span class="sxs-lookup"><span data-stu-id="c004e-109">Click anywhere on the numbers of the gauge to highlight the scale.</span></span>  
  
2.  <span data-ttu-id="c004e-110">開啟 [屬性] 窗格。</span><span class="sxs-lookup"><span data-stu-id="c004e-110">Open the Properties pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c004e-111">如果看不到 [屬性] 窗格，請按一下 [**視圖**] 索引標籤，然後選取 [**屬性**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c004e-111">If you do not see the Properties pane, click the **View** tab and then select the **Properties** checkbox.</span></span>  
  
3.  <span data-ttu-id="c004e-112">在 [**指標**] 屬性中，按一下 [ ( ... ) ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c004e-112">In the **Pointers** property, click the (...) button.</span></span> <span data-ttu-id="c004e-113">指標集合編輯器隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="c004e-113">The Pointer Collection Editor opens.</span></span>  
  
4.  <span data-ttu-id="c004e-114">將**SnappingEnabled**屬性設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="c004e-114">Set the **SnappingEnabled** property to `True`.</span></span>  
  
5.  <span data-ttu-id="c004e-115">將**SnappingInterval**設定為代表貼齊間隔的值。</span><span class="sxs-lookup"><span data-stu-id="c004e-115">Set the **SnappingInterval** to a value that represents the snapping interval.</span></span> <span data-ttu-id="c004e-116">此指標將貼齊您已指定之值的最接近捨入倍數。</span><span class="sxs-lookup"><span data-stu-id="c004e-116">The pointer will be snapped to the nearest round multiple of the value that you have specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c004e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c004e-117">See Also</span></span>  
 <span data-ttu-id="c004e-118">[格式化量測計上的尺規 &#40;報表產生器和 SSRS&#41;](report-design/formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c004e-118">[Formatting Scales on a Gauge &#40;Report Builder and SSRS&#41;](report-design/formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c004e-119">[格式化量測計上的指標 &#40;報表產生器和 SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c004e-119">[Formatting Pointers on a Gauge &#40;Report Builder and SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c004e-120">量測計 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c004e-120">Gauges &#40;Report Builder and SSRS&#41;</span></span>](report-design/gauges-report-builder-and-ssrs.md)  
  
  
