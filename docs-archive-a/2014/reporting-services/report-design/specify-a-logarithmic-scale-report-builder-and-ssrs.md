---
title: 指定對數刻度 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f3092c1c-b128-433d-9a95-983508b2a8d4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2cc422a6f95a420445dc604d08a23e8f8e65c95d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585015"
---
# <a name="specify-a-logarithmic-scale-report-builder-and-ssrs"></a><span data-ttu-id="23476-102">指定對數刻度 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="23476-102">Specify a Logarithmic Scale (Report Builder and SSRS)</span></span>
  <span data-ttu-id="23476-103">如果您的資料在對數上成比例，您可能會想要考慮在圖表上使用對數刻度。</span><span class="sxs-lookup"><span data-stu-id="23476-103">If you have data that is logarithmically proportional, you may want to consider using a logarithmic scale on the chart.</span></span> <span data-ttu-id="23476-104">這樣可以讓您的資料更容易管理，而有助於改善圖表的外觀。</span><span class="sxs-lookup"><span data-stu-id="23476-104">This helps improve the appearance of the chart by making your data more manageable.</span></span> <span data-ttu-id="23476-105">大部分的對數刻度都使用 10 當做基底。</span><span class="sxs-lookup"><span data-stu-id="23476-105">Most logarithmic scales use a base of 10.</span></span>  
  
 <span data-ttu-id="23476-106">此功能僅能在值軸上使用。</span><span class="sxs-lookup"><span data-stu-id="23476-106">This feature is only available on the value axis.</span></span> <span data-ttu-id="23476-107">值軸通常是圖表的垂直軸 (或 Y 軸)，</span><span class="sxs-lookup"><span data-stu-id="23476-107">The value axis is usually the vertical, or y-axis.</span></span> <span data-ttu-id="23476-108">而在長條圖中，則為水平軸 (即 X 軸)。</span><span class="sxs-lookup"><span data-stu-id="23476-108">On bar charts, however, it is the horizontal, or x-axis.</span></span>  
  
 <span data-ttu-id="23476-109">如果您的軸為對數，系統就會以對數的方式縮放與該軸相關的其他所有屬性。</span><span class="sxs-lookup"><span data-stu-id="23476-109">If your axis is logarithmic, all other properties relating to the axis will be scaled logarithmically.</span></span> <span data-ttu-id="23476-110">例如，如果您在軸上指定基底為 10 的對數刻度，將軸間隔設定為 2 就會產生將間隔範圍 10 自乘至 2 的乘冪或 100。</span><span class="sxs-lookup"><span data-stu-id="23476-110">For example, if you specify a base-10 logarithmic scale on your axis, setting an axis interval of 2 will generate intervals in magnitudes of 10 to the power of 2, or 100.</span></span> <span data-ttu-id="23476-111">這表示，您的軸值將讀取 1、100 或 10000 而非 1、10、100、1000 或 10000 的預設結果。</span><span class="sxs-lookup"><span data-stu-id="23476-111">This means your axis values will read 1, 100, 10000, instead of the default result of 1, 10, 100, 1000, 10000.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-a-logarithmic-scale"></a><span data-ttu-id="23476-112">若要指定對數刻度</span><span class="sxs-lookup"><span data-stu-id="23476-112">To specify a logarithmic scale</span></span>  
  
1.  <span data-ttu-id="23476-113">以滑鼠右鍵按一下圖表的 Y 軸，然後按一下 [垂直軸屬性]  。</span><span class="sxs-lookup"><span data-stu-id="23476-113">Right-click the y-axis of your chart, and click **VerticalAxis Properties**.</span></span> <span data-ttu-id="23476-114">[垂直軸屬性]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="23476-114">The **VerticalAxis Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="23476-115">在 [軸選項]  中，選取 [使用對數刻度]  。</span><span class="sxs-lookup"><span data-stu-id="23476-115">In **Axis Options**, select **Uselogarithmic scale**.</span></span>  
  
3.  <span data-ttu-id="23476-116">在 [對數底數]  文字方塊中，為對數底數鍵入正值。</span><span class="sxs-lookup"><span data-stu-id="23476-116">In the **Logbase** text box, type a positive value for the logarithmic base.</span></span> <span data-ttu-id="23476-117">如果沒有指定任何值，對數基底預設為 10。</span><span class="sxs-lookup"><span data-stu-id="23476-117">If no value is specified, the logarithmic base defaults to 10.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23476-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23476-118">See Also</span></span>  
 <span data-ttu-id="23476-119">[格式化圖表上的軸標籤 &#40;報表產生器及 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="23476-119">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="23476-120">[格式化圖表 &#40;報表產生器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="23476-120">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="23476-121">[將軸標籤格式化成日期或貨幣 &#40;報表產生器及 SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="23476-121">[Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="23476-122">圖表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="23476-122">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
