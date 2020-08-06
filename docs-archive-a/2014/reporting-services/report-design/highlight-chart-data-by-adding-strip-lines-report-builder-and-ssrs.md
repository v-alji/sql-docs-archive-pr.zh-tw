---
title: 新增帶狀線來強調圖表資料 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: addd6137-4b6e-4e88-a7e8-9600fcd1ccce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01b0bb41a71daf9ac558ce8d8bb84480426870c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592441"
---
# <a name="highlight-chart-data-by-adding-strip-lines-report-builder-and-ssrs"></a><span data-ttu-id="79599-102">加入帶狀線來強調圖表資料 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="79599-102">Highlight Chart Data by Adding Strip Lines (Report Builder and SSRS)</span></span>
  <span data-ttu-id="79599-103">帶狀線 (或稱寬帶) 是水平或垂直的範圍，這些範圍會以規則或自訂的間隔來繪製圖表背景的陰影。</span><span class="sxs-lookup"><span data-stu-id="79599-103">Strip lines, or strips, are horizontal or vertical ranges that shade the background of the chart in regular or custom intervals.</span></span> <span data-ttu-id="79599-104">您可以使用區域線：</span><span class="sxs-lookup"><span data-stu-id="79599-104">You can use strip lines to:</span></span>  
  
-   <span data-ttu-id="79599-105">改善可讀性以在圖表上尋找個別值。</span><span class="sxs-lookup"><span data-stu-id="79599-105">Improve readability for looking up individual values on the chart.</span></span> <span data-ttu-id="79599-106">以固定間隔指定區域線，這有助於在讀取圖表時區隔資料點。</span><span class="sxs-lookup"><span data-stu-id="79599-106">Specify strip lines at regular intervals to help separate data points when reading the chart.</span></span>  
  
-   <span data-ttu-id="79599-107">反白顯示以固定間隔發生的日期。</span><span class="sxs-lookup"><span data-stu-id="79599-107">Highlight dates that occur at regular intervals.</span></span> <span data-ttu-id="79599-108">例如，您可以在銷售報表中使用區域線來識別週末資料點。</span><span class="sxs-lookup"><span data-stu-id="79599-108">For example, in a sales report you might use strip lines to identify weekend data points.</span></span>  
  
-   <span data-ttu-id="79599-109">反白顯示特定的關鍵範圍。</span><span class="sxs-lookup"><span data-stu-id="79599-109">Highlight a specific key range.</span></span> <span data-ttu-id="79599-110">續前例，您可以使用一個區域線來反白顯示 $80 和 $100 之間的最高銷售範圍。</span><span class="sxs-lookup"><span data-stu-id="79599-110">Using the previous example, you can use one strip line to highlight the highest range of sales that is between $80-100.</span></span>  
  
 <span data-ttu-id="79599-111">區域線不適用於「形狀」或「極座標」圖表類型。</span><span class="sxs-lookup"><span data-stu-id="79599-111">Strip lines are not applicable to Shape or Polar chart types.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-interlaced-strip-lines-at-regular-intervals-on-a-chart"></a><span data-ttu-id="79599-112">在圖表上以固定間隔顯示交錯的帶狀線</span><span class="sxs-lookup"><span data-stu-id="79599-112">To display interlaced strip lines at regular intervals on a chart</span></span>  
  
1.  <span data-ttu-id="79599-113">若要顯示水平帶狀線，請以滑鼠右鍵按一下垂直圖表軸，然後按一下 [垂直軸屬性]  。</span><span class="sxs-lookup"><span data-stu-id="79599-113">To show horizontal strip lines, right-click the vertical chart axis and click **VerticalAxis Properties**.</span></span>  
  
     <span data-ttu-id="79599-114">若要顯示垂直帶狀線，請以滑鼠右鍵按一下水平圖表軸，然後按一下 [水平軸屬性]  。</span><span class="sxs-lookup"><span data-stu-id="79599-114">To show vertical strip lines, right-click the horizontal chart axis and click **Horizontal Axis Properties**.</span></span>  
  
2.  <span data-ttu-id="79599-115">選取 [使用交錯式]  選項。</span><span class="sxs-lookup"><span data-stu-id="79599-115">Select the **Use interlacing** option.</span></span> <span data-ttu-id="79599-116">灰色帶狀線會出現在圖表上。</span><span class="sxs-lookup"><span data-stu-id="79599-116">Grey strip lines will appear on your chart.</span></span>  
  
3.  <span data-ttu-id="79599-117">(選擇性) 使用相鄰的 [色彩]  下拉式清單來指定帶狀線的色彩。</span><span class="sxs-lookup"><span data-stu-id="79599-117">(Optional) Specify a color for the strip lines using the adjacent **Color** drop-down list.</span></span>  
  
### <a name="to-display-interlaced-strip-lines-at-custom-intervals-on-a-chart"></a><span data-ttu-id="79599-118">在圖表上以自訂間隔顯示交錯的帶狀線</span><span class="sxs-lookup"><span data-stu-id="79599-118">To display interlaced strip lines at custom intervals on a chart</span></span>  
  
1.  <span data-ttu-id="79599-119">若要顯示水平帶狀線，請以滑鼠右鍵按一下垂直圖表軸，然後按一下 [垂直軸屬性]  。</span><span class="sxs-lookup"><span data-stu-id="79599-119">To show horizontal strip lines, right-click the vertical chart axis and click **VerticalAxis Properties**.</span></span>  
  
     <span data-ttu-id="79599-120">若要顯示垂直帶狀線，請以滑鼠右鍵按一下水平圖表軸，然後按一下 [水平軸屬性]  。</span><span class="sxs-lookup"><span data-stu-id="79599-120">To show vertical strip lines, right-click the horizontal chart axis and click **Horizontal Axis Properties**.</span></span>  
  
     <span data-ttu-id="79599-121">軸屬性會在 [屬性] 視窗中顯示。</span><span class="sxs-lookup"><span data-stu-id="79599-121">The axis properties are displayed in the Properties window.</span></span>  
  
2.  <span data-ttu-id="79599-122">在 [屬性] 窗格的 [外觀]  區段中，針對 StripLines 屬性按一下 [編輯集合] 按鈕 (…) 來開啟 [ChartStripLine 集合編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="79599-122">In the **Appearance** section of the Properties pane, for the StripLines property, click the Edit Collection (...) button to open the **ChartStripLine Collection Editor**.</span></span>  
  
3.  <span data-ttu-id="79599-123">按一下 [新增]  ，將新的帶狀線新增集合。</span><span class="sxs-lookup"><span data-stu-id="79599-123">Click **Add** to add a new strip line to the collection.</span></span>  
  
4.  <span data-ttu-id="79599-124">按一下 [StripWidth] 來指定帶狀線的寬度，在報表上是以英吋表示。</span><span class="sxs-lookup"><span data-stu-id="79599-124">Click StripWidth to specify the width of the strip line, measured in inches on the report.</span></span> <span data-ttu-id="79599-125">如果要反白顯示日期或時間，請按一下 [StripWidthType] 並選取時間間隔。</span><span class="sxs-lookup"><span data-stu-id="79599-125">If you are highlighting dates or times, click StripWidthType and select a time interval.</span></span>  
  
5.  <span data-ttu-id="79599-126">輸入 Interval 的值或運算式，以指定帶狀線重複的頻率。</span><span class="sxs-lookup"><span data-stu-id="79599-126">Type a value or expression for the Interval to specify how often the strip line will repeat.</span></span>  <span data-ttu-id="79599-127">例如，如果指定的間隔為 10，而區域線寬度為 5，則區域線會在 0 到 5、15 到 20、30 到 35 的值位置顯示，以此類推。</span><span class="sxs-lookup"><span data-stu-id="79599-127">For example, if you specify an interval of 10, and your strip line width is 5, strip lines will display at values of 0 to 5, 15 to 20, 30 to 35, and so on.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="79599-128">根據預設，Interval 是設為 [自動]，代表圖表不會計算自訂帶狀線的間隔。</span><span class="sxs-lookup"><span data-stu-id="79599-128">By default, Interval is set to Auto, which means the chart will not calculate an interval for custom strip lines.</span></span> <span data-ttu-id="79599-129">只有在有設定間隔值時，圖表才會計算區域線的間隔。</span><span class="sxs-lookup"><span data-stu-id="79599-129">The chart only calculates intervals for strip lines if an interval value is set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79599-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79599-130">See Also</span></span>  
 <span data-ttu-id="79599-131">[格式化圖表上的軸標籤 &#40;報表產生器及 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="79599-131">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="79599-132">[格式化圖表 &#40;報表產生器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="79599-132">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="79599-133">將移動平均加入至圖表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="79599-133">Add a Moving Average to a Chart &#40;Report Builder and SSRS&#41;</span></span>](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)  
  
  
