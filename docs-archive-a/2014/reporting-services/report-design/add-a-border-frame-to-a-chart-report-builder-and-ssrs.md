---
title: 將邊框新增至圖表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ca0c5040-40bb-4cb7-bc2b-5bcbe73858bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4c91d3de00caa4eab6ed1894042b2214b7dcf4b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707166"
---
# <a name="add-a-border-frame-to-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="a7d39-102">將邊框加入至圖表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="a7d39-102">Add a Border Frame to a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a7d39-103">若要為圖表提供一個更吸引人的外觀，請考慮在圖表的周圍使用邊框。</span><span class="sxs-lookup"><span data-stu-id="a7d39-103">To give a chart more visual impact, consider using a border frame around the outside of the chart.</span></span> <span data-ttu-id="a7d39-104">您可以使用 **[圖表屬性]** 對話方塊或 [屬性] 窗格來選取邊框。</span><span class="sxs-lookup"><span data-stu-id="a7d39-104">You can select a border frame by using the **Chart Properties** dialog box or by using the Properties pane.</span></span> <span data-ttu-id="a7d39-105">圖表邊框無法套用到其他任何資料區。</span><span class="sxs-lookup"><span data-stu-id="a7d39-105">The chart border frames cannot be applied to any other data region.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-apply-a-border-to-a-chart"></a><span data-ttu-id="a7d39-106">將框線套用到圖表</span><span class="sxs-lookup"><span data-stu-id="a7d39-106">To apply a border to a chart</span></span>  
  
1.  <span data-ttu-id="a7d39-107">以滑鼠右鍵按一下圖表的任何位置，並選取 [圖表屬性]  。</span><span class="sxs-lookup"><span data-stu-id="a7d39-107">Right-click anywhere on the chart and select **Chart Properties**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a7d39-108">如果您沒有看到 [圖表屬性]  ，請指向捷徑功能表上的 [圖表]  ，並選取 [圖表屬性]  。</span><span class="sxs-lookup"><span data-stu-id="a7d39-108">If you do not see the **Chart Properties**, point to **Chart** on the shortcut menu and select **Chart Properties**.</span></span>  
  
2.  <span data-ttu-id="a7d39-109">選取 **[框線]** ，然後按一下要套用到圖表的框線類型。</span><span class="sxs-lookup"><span data-stu-id="a7d39-109">Select **Border**, and click the type of border to apply to the chart.</span></span>  
  
3.  <span data-ttu-id="a7d39-110">(選擇性) 選取一個值，或輸入代表框線樣式的運算式。</span><span class="sxs-lookup"><span data-stu-id="a7d39-110">(Optional) Select a value or type an expression that represents the style of the border.</span></span>  
  
4.  <span data-ttu-id="a7d39-111">(選擇性) 指定將會繪製在圖表周圍當做框線的線條色彩。</span><span class="sxs-lookup"><span data-stu-id="a7d39-111">(Optional) Specify the color of the line that will be drawn around the chart as the border.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a7d39-112">**[線條色彩]** 清單包含常見的色彩。</span><span class="sxs-lookup"><span data-stu-id="a7d39-112">The **Line color** list contains common colors.</span></span> <span data-ttu-id="a7d39-113">如果您想要從更多色彩的清單中選取，請按一下清單中的 [更多色彩]  ，或是按一下清單旁邊的運算式 (**fx**) 按鈕，叫出 [運算式]  編輯器。</span><span class="sxs-lookup"><span data-stu-id="a7d39-113">If you want to select from a list of more colors, click **More colors** in the list or click the expression (**fx**) button next to the list to bring up the **Expression** editor.</span></span>  
  
5.  <span data-ttu-id="a7d39-114">(選擇性) 指定框線的寬度。</span><span class="sxs-lookup"><span data-stu-id="a7d39-114">(Optional) Specify the width of the border.</span></span> <span data-ttu-id="a7d39-115">有效值介於 0.25pt 和 20pt 之間。</span><span class="sxs-lookup"><span data-stu-id="a7d39-115">Valid values are between 0.25pt and 20pt.</span></span> <span data-ttu-id="a7d39-116">為了得到最佳視覺效果，請考慮將框線的大小維持在 1 與 3pt 之間。</span><span class="sxs-lookup"><span data-stu-id="a7d39-116">Consider keeping the size of your border to between 1 and 3pt for the best visual effect.</span></span>  
  
6.  <span data-ttu-id="a7d39-117">(選擇性) 如果您的報表包含白色以外的背景色彩，請考慮定義相同色彩的頁面色彩。</span><span class="sxs-lookup"><span data-stu-id="a7d39-117">(Optional) If your report contains a background color other than white, consider defining a page color that is the same color.</span></span> <span data-ttu-id="a7d39-118">頁面色彩就是框線外面的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="a7d39-118">The page color is the background color outside of the border line.</span></span>  
  
7.  <span data-ttu-id="a7d39-119">(選擇性) 如果您選擇框架類型，請為框架指定樣式和色彩。</span><span class="sxs-lookup"><span data-stu-id="a7d39-119">(Optional) If you choose a Frame type, specify a style and color for the frame.</span></span> <span data-ttu-id="a7d39-120">**[框架填滿色彩]** 清單包含常見的色彩。</span><span class="sxs-lookup"><span data-stu-id="a7d39-120">The **Frame fill color** list contains common colors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7d39-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7d39-121">See Also</span></span>  
 <span data-ttu-id="a7d39-122">[圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a7d39-122">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a7d39-123">[格式化圖表 &#40;報表產生器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a7d39-123">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a7d39-124">將斜面、浮凸與紋理樣式新增至圖表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a7d39-124">Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-effects-add-bevel-emboss-or-texture-report-builder.md)  
  
  
