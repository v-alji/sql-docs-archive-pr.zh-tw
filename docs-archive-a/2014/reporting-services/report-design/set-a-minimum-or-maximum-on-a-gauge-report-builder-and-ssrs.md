---
title: 設定最小值或最大值為量測計 （報表產生器及 SSRS） |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b4c260c0-5a88-4f30-8977-eb5cc78fc146
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 344122dbff647a8c35b838ecce637602f202864b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592440"
---
# <a name="set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs"></a><span data-ttu-id="703c0-102">設定量測計的最小值或最大值 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="703c0-102">Set a Minimum or Maximum on a Gauge (Report Builder and SSRS)</span></span>
  <span data-ttu-id="703c0-103">與定義多個群組的圖表不同的是，量測計只會顯示一個值。</span><span class="sxs-lookup"><span data-stu-id="703c0-103">Unlike the chart, where multiple groups are defined, the gauge only shows one value.</span></span> <span data-ttu-id="703c0-104">由於報表產生器和報表設計師會判斷您嘗試在量測計上顯示之單一值的內容或相對重要性，所以您必須定義標尺的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="703c0-104">Since Report Builder and Report Designer determine the context or relative significance of the one value that you are trying to show on the gauge, you must define the minimum and maximum of the scale.</span></span> <span data-ttu-id="703c0-105">例如，如果您的資料值為介於 0 和 10 之間的排名，就會想要將最小值設定為 0 而將最大值設定為 10。</span><span class="sxs-lookup"><span data-stu-id="703c0-105">For example, if your data values are rankings between 0 and 10, you will want to set the minimum to 0 and maximum to 10.</span></span> <span data-ttu-id="703c0-106">系統會根據您針對最小值和最大值指定的值，自動計算間隔數字。</span><span class="sxs-lookup"><span data-stu-id="703c0-106">The interval numbers are calculated automatically based on the values specified for the minimum and maximum.</span></span> <span data-ttu-id="703c0-107">根據預設，最小值和最大值會設定為 0 和 100，但這是您應該變更的任意值。</span><span class="sxs-lookup"><span data-stu-id="703c0-107">By default, the minimum and maximum are set to 0 and 100, but this is an arbitrary value that you should change.</span></span> <span data-ttu-id="703c0-108">應用程式不會將您的值計算成百分比。</span><span class="sxs-lookup"><span data-stu-id="703c0-108">The application does not calculate your value as a percentage.</span></span>  
  
 <span data-ttu-id="703c0-109">如果值的範圍很大 (例如從 0 到 10000)，請考慮使用乘數來減少量測計上零的數目。</span><span class="sxs-lookup"><span data-stu-id="703c0-109">If the range of your values is large, for example from 0 to 10000, consider using a multiplier to reduce the number of zeroes on the gauge.</span></span> <span data-ttu-id="703c0-110">此乘數只會減少量測計上數字的標尺，而非值本身。</span><span class="sxs-lookup"><span data-stu-id="703c0-110">The multiplier will only reduce the scale of the numbers on the gauge, not the value itself.</span></span>  
  
 <span data-ttu-id="703c0-111">您可以使用運算式來設定 [最小值]  和 [最大值]  選項的值。</span><span class="sxs-lookup"><span data-stu-id="703c0-111">You can use expressions to set the values of the **Minimum** and **Maximum** options.</span></span> <span data-ttu-id="703c0-112">如需詳細資訊，請參閱[運算式 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="703c0-112">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-the-minimum-and-maximum-on-the-gauge"></a><span data-ttu-id="703c0-113">設定量測計的最小值和最大值</span><span class="sxs-lookup"><span data-stu-id="703c0-113">To set the minimum and maximum on the gauge</span></span>  
  
1.  <span data-ttu-id="703c0-114">以滑鼠右鍵按一下標尺，然後選取 [標尺屬性]  。</span><span class="sxs-lookup"><span data-stu-id="703c0-114">Right-click on the scale and select **Scale Properties**.</span></span> <span data-ttu-id="703c0-115">[標尺屬性]  對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="703c0-115">The **Scale Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="703c0-116">在 [一般]  中，指定 [最小值]  的值。</span><span class="sxs-lookup"><span data-stu-id="703c0-116">In **General**, specify a value for **Minimum**.</span></span> <span data-ttu-id="703c0-117">根據預設，這個值為 0。</span><span class="sxs-lookup"><span data-stu-id="703c0-117">By default, this value is 0.</span></span> <span data-ttu-id="703c0-118">您可以選擇按一下 [運算式]  \(*fx*) 按鈕來編輯設定選項值的運算式。</span><span class="sxs-lookup"><span data-stu-id="703c0-118">Optionally, click the **Expression** (*fx*) button to edit the expression that sets the value of the option.</span></span>  
  
3.  <span data-ttu-id="703c0-119">指定 [最大值]  的值。</span><span class="sxs-lookup"><span data-stu-id="703c0-119">Specify a value for **Maximum**.</span></span> <span data-ttu-id="703c0-120">根據預設，此值為 100。</span><span class="sxs-lookup"><span data-stu-id="703c0-120">By default, this value is 100.</span></span> <span data-ttu-id="703c0-121">您可以選擇按一下 [運算式]  \(*fx*) 按鈕來編輯設定選項值的運算式。</span><span class="sxs-lookup"><span data-stu-id="703c0-121">Optionally, click the **Expression** (*fx*) button to edit the expression that sets the value of the option.</span></span>  
  
4.  <span data-ttu-id="703c0-122">(選擇性) 如果最小值和最大值的值很大，請指定 [標尺標籤乘數]  選項的值。</span><span class="sxs-lookup"><span data-stu-id="703c0-122">(Optional) If the values for your minimum and maximum are large, specify a value for the **Multiply scale labels by** option.</span></span> <span data-ttu-id="703c0-123">若要指定減少標尺的乘數，請使用十進位數字。</span><span class="sxs-lookup"><span data-stu-id="703c0-123">To specify a multiplier that reduces your scale, use a decimal number.</span></span> <span data-ttu-id="703c0-124">例如，如果您的標尺為從 0 到 1000，就可以指定乘數值 0.01 來減少標尺，以便顯示成 0 到 10。</span><span class="sxs-lookup"><span data-stu-id="703c0-124">For example, if you have a scale from 0 to 1000, you can specify a multiplier value of 0.01 to reduce the scale to read 0 to 10.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="703c0-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="703c0-125">See Also</span></span>  
 <span data-ttu-id="703c0-126">[格式化量測計上的標尺 &#40;報表產生器及 SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="703c0-126">[Formatting Scales on a Gauge &#40;Report Builder and SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="703c0-127">[格式化量測計上的指標 &#40;報表產生器及 SSRS&#41;](formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="703c0-127">[Formatting Pointers on a Gauge &#40;Report Builder and SSRS&#41;](formatting-pointers-on-a-gauge-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="703c0-128">量測計 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="703c0-128">Gauges &#40;Report Builder and SSRS&#41;</span></span>](gauges-report-builder-and-ssrs.md)  
  
  
