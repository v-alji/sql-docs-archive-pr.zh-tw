---
title: 折線圖 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 194e6679-890d-4a3e-a756-130d32ef7e29
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 44e7a011186e66e6b8bdc8b5dd31939c883e320b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707089"
---
# <a name="line-charts-report-builder-and-ssrs"></a><span data-ttu-id="52e84-102">折線圖 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="52e84-102">Line Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="52e84-103">折線圖會將數列顯示成一組由單一線條連接的點。</span><span class="sxs-lookup"><span data-stu-id="52e84-103">A line chart displays a series as a set of points connected by a single line.</span></span> <span data-ttu-id="52e84-104">因此，折線圖用於表示發生超過一段連續時間的大量資料。</span><span class="sxs-lookup"><span data-stu-id="52e84-104">Line charts are used to representing large amounts of data that occur over a continuous period of time.</span></span> <span data-ttu-id="52e84-105">如需如何將資料加入折線圖的詳細資訊，請參閱 [圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="52e84-105">For more information about how to add data to a line chart, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="52e84-106">下圖顯示的是包含三個數列的折線圖。</span><span class="sxs-lookup"><span data-stu-id="52e84-106">The following illustration shows a line chart that contains three series.</span></span>  
  
 <span data-ttu-id="52e84-107">![折線圖](../media/rs-linechart.gif "折線圖")</span><span class="sxs-lookup"><span data-stu-id="52e84-107">![Line chart](../media/rs-linechart.gif "Line chart")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="52e84-108">變化</span><span class="sxs-lookup"><span data-stu-id="52e84-108">Variations</span></span>  
  
-   <span data-ttu-id="52e84-109">**平滑線圖**：</span><span class="sxs-lookup"><span data-stu-id="52e84-109">**Smooth line**.</span></span> <span data-ttu-id="52e84-110">使用曲線而非一般線條的折線圖。</span><span class="sxs-lookup"><span data-stu-id="52e84-110">A line chart that uses a curved line instead of a regular line.</span></span>  
  
-   <span data-ttu-id="52e84-111">**梯線圖**：</span><span class="sxs-lookup"><span data-stu-id="52e84-111">**Stepped line**.</span></span> <span data-ttu-id="52e84-112">使用梯線而非一般線條的折線圖。</span><span class="sxs-lookup"><span data-stu-id="52e84-112">A line chart that uses a stepped line instead of a regular line.</span></span> <span data-ttu-id="52e84-113">梯線圖會使用類似梯子或樓梯的階梯線條來連接每個點。</span><span class="sxs-lookup"><span data-stu-id="52e84-113">The stepped line connects points by using a line that makes it look like steps on a ladder or staircase.</span></span>  
  
-   <span data-ttu-id="52e84-114">**走勢圖**：</span><span class="sxs-lookup"><span data-stu-id="52e84-114">**Sparkline charts**.</span></span> <span data-ttu-id="52e84-115">折線圖的變數，只在資料表或矩陣的資料格中顯示線條數列。</span><span class="sxs-lookup"><span data-stu-id="52e84-115">Variations of the line chart that show only the line series in the cell of a table or matrix.</span></span> <span data-ttu-id="52e84-116">如需詳細資訊，請參閱 [走勢圖和資料橫條 &#40;報表產生器及 SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="52e84-116">For more information, see [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
## <a name="data-considerations-for-line-charts"></a><span data-ttu-id="52e84-117">折線圖的資料考量</span><span class="sxs-lookup"><span data-stu-id="52e84-117">Data Considerations for Line Charts</span></span>  
  
-   <span data-ttu-id="52e84-118">為增進預設折線圖的視覺效果，請考慮將數列框線的寬度變更為 3，並增加一個單位的陰影位移。</span><span class="sxs-lookup"><span data-stu-id="52e84-118">To improve the visual impact of the default line chart, consider changing the width of the series border to 3, and adding a shadow offset of 1.</span></span> <span data-ttu-id="52e84-119">這樣就會建立線條較粗的折線圖。</span><span class="sxs-lookup"><span data-stu-id="52e84-119">This will create a much bolder line chart.</span></span> <span data-ttu-id="52e84-120">如果您將圖表類型從折線圖變更為其他類型，您需要將這些屬性還原為其原始值。</span><span class="sxs-lookup"><span data-stu-id="52e84-120">You will need to revert these properties to their original values if you change the chart type from Line to another type.</span></span>  
  
-   <span data-ttu-id="52e84-121">如果您的資料集包含空值，折線圖將會以預留位置線條的形式加入空點，才能維持圖表的連續性。</span><span class="sxs-lookup"><span data-stu-id="52e84-121">If your dataset includes empty values, the line chart will add empty points, in the form of placeholder lines, in order to maintain continuity on the chart.</span></span> <span data-ttu-id="52e84-122">如果您不想看到這些線條，請考慮使用非連續的圖表類型 (例如，橫條圖或直條圖) 來顯示資料集。</span><span class="sxs-lookup"><span data-stu-id="52e84-122">If you would rather not see these lines, consider displaying your dataset using a non-contiguous chart type such as a bar or column chart.</span></span>  
  
-   <span data-ttu-id="52e84-123">折線圖至少需要兩個點才能繪製一條線。</span><span class="sxs-lookup"><span data-stu-id="52e84-123">A line chart requires at least two points to draw a line.</span></span>  <span data-ttu-id="52e84-124">如果您的資料集只有一個資料點，折線圖將會顯示為單一資料點標記。</span><span class="sxs-lookup"><span data-stu-id="52e84-124">If your dataset has only one data point, the line chart will display as a single data point marker.</span></span>  
  
-   <span data-ttu-id="52e84-125">繪製為線條的數列在圖表區域中將不會佔用太多空間。</span><span class="sxs-lookup"><span data-stu-id="52e84-125">A series that is drawn as a line will not take up much space within a chart area.</span></span>  <span data-ttu-id="52e84-126">因此，折線圖通常會與其他圖表類型組合，例如，直條圖。</span><span class="sxs-lookup"><span data-stu-id="52e84-126">For this reason, line charts are frequently combined with other chart types such as column charts.</span></span> <span data-ttu-id="52e84-127">不過，折線圖無法與橫條圖、極座標圖、圓形圖或形狀圖等圖表類型組合在一起。</span><span class="sxs-lookup"><span data-stu-id="52e84-127">However, you cannot combine a line chart with bar, polar, pie or shape chart types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52e84-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52e84-128">See Also</span></span>  
 <span data-ttu-id="52e84-129">[橫條圖 &#40;報表產生器及 SSRS&#41;](bar-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="52e84-129">[Bar Charts &#40;Report Builder and SSRS&#41;](bar-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="52e84-130">[直條圖 &#40;報表產生器及 SSRS&#41;](column-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="52e84-130">[Column Charts &#40;Report Builder and SSRS&#41;](column-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="52e84-131">[圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="52e84-131">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="52e84-132">[圖表類型 &#40;報表產生器及 SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="52e84-132">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="52e84-133">[區域圖 &#40;報表產生器及 SSRS&#41;](area-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="52e84-133">[Area Charts &#40;Report Builder and SSRS&#41;](area-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="52e84-134">[圖表中的空白和 Null 資料點 &#40;報表產生器及 SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="52e84-134">[Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="52e84-135">圖表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="52e84-135">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
