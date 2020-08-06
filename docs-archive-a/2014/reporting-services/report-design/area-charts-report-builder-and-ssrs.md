---
title: 區域圖 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 245b236d-1d55-4744-b752-80bd133502aa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f401efa0abd5eac8ab39e511bc6b16a4f381ebdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702474"
---
# <a name="area-charts-report-builder-and-ssrs"></a><span data-ttu-id="7beed-102">區域圖 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="7beed-102">Area Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7beed-103">區域圖會將數列顯示成一組用線條連接的點，線條下會有一個全部填滿的區域。</span><span class="sxs-lookup"><span data-stu-id="7beed-103">An area chart displays a series as a set of points connected by a line, with all the area filled in below the line.</span></span> <span data-ttu-id="7beed-104">如需如何將資料加入區域圖的詳細資訊，請參閱 [圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7beed-104">For more information on how to add data to an area chart, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="7beed-105">下圖顯示堆疊區域圖的範例。</span><span class="sxs-lookup"><span data-stu-id="7beed-105">The following illustration shows an example of a stacked area chart.</span></span> <span data-ttu-id="7beed-106">此資料非常適合在堆疊區域圖上顯示，因為此圖表可以顯示所有數列的總計，以及每個數列對於總計所佔據的比例。</span><span class="sxs-lookup"><span data-stu-id="7beed-106">The data is well suited for display on a stacked area chart because the chart can display totals for all series as well as the proportion that each series contributes to the total.</span></span>  
  
 <span data-ttu-id="7beed-107">![區域圖](../media/areachart.gif "區域圖")</span><span class="sxs-lookup"><span data-stu-id="7beed-107">![Area chart](../media/areachart.gif "Area chart")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="7beed-108">變化</span><span class="sxs-lookup"><span data-stu-id="7beed-108">Variations</span></span>  
  
-   <span data-ttu-id="7beed-109">**堆疊區域**：</span><span class="sxs-lookup"><span data-stu-id="7beed-109">**Stacked area**.</span></span> <span data-ttu-id="7beed-110">將多個數列垂直堆疊的區域圖。</span><span class="sxs-lookup"><span data-stu-id="7beed-110">An area chart where multiple series are stacked vertically.</span></span> <span data-ttu-id="7beed-111">如果您的圖表中只有一個數列，堆疊區域圖的顯示將與區域圖相同。</span><span class="sxs-lookup"><span data-stu-id="7beed-111">If there is only one series in your chart, the stacked area chart will display the same as an area chart.</span></span>  
  
-   <span data-ttu-id="7beed-112">**百分比堆疊區域**：</span><span class="sxs-lookup"><span data-stu-id="7beed-112">**Percent stacked area**.</span></span> <span data-ttu-id="7beed-113">將多個數列垂直堆疊以便符合整個圖表區域的區域圖。</span><span class="sxs-lookup"><span data-stu-id="7beed-113">An area chart where multiple series are stacked vertically to fit the entire chart area.</span></span> <span data-ttu-id="7beed-114">如果您的圖表中只有一個數列，堆疊區域圖的顯示將與區域圖相同。</span><span class="sxs-lookup"><span data-stu-id="7beed-114">If there is only one series in your chart, the stacked area chart will display the same as an area chart.</span></span>  
  
-   <span data-ttu-id="7beed-115">**平滑區域圖**：</span><span class="sxs-lookup"><span data-stu-id="7beed-115">**Smooth area**.</span></span> <span data-ttu-id="7beed-116">一種區域圖，其中的資料點是以平滑線相連，而非以一般線條相連。</span><span class="sxs-lookup"><span data-stu-id="7beed-116">An area chart where the data points are connected by a smooth line instead of a regular line.</span></span> <span data-ttu-id="7beed-117">當您比較注重顯示趨勢，而非顯示各個資料點的值時，請使用平滑區域圖，而非區域圖。</span><span class="sxs-lookup"><span data-stu-id="7beed-117">Use a smooth area chart instead of an area chart when you are more concerned with displaying trends than with displaying the values of individual data points.</span></span>  
  
## <a name="data-considerations-for-area-charts"></a><span data-ttu-id="7beed-118">區域圖的資料考量</span><span class="sxs-lookup"><span data-stu-id="7beed-118">Data Considerations for Area Charts</span></span>  
  
-   <span data-ttu-id="7beed-119">除了折線圖之外，區域圖是連續顯示資料的唯一圖表類型。</span><span class="sxs-lookup"><span data-stu-id="7beed-119">Along with the line chart, the area chart is the only chart type that displays data contiguously.</span></span> <span data-ttu-id="7beed-120">因此，區域圖通常用於表示發生超過一段連續時間的資料。</span><span class="sxs-lookup"><span data-stu-id="7beed-120">For this reason, an area chart is commonly used to represent data that occurs over a continuous period of time.</span></span>  
  
-   <span data-ttu-id="7beed-121">百分比堆疊區域圖適用於顯示發生超過一段時間的成比例資料。</span><span class="sxs-lookup"><span data-stu-id="7beed-121">A percent stacked area chart is useful for showing proportional data that occurs over time.</span></span>  
  
-   <span data-ttu-id="7beed-122">如果只有一個數列，堆疊區域圖的外觀將與區域圖相同。</span><span class="sxs-lookup"><span data-stu-id="7beed-122">If there is only one series, a stacked area chart will be drawn as an area chart.</span></span>  
  
-   <span data-ttu-id="7beed-123">在一般區域圖中，如果多個數列的值相似，這些區域可能會重疊，而遮蓋到重要資料點的值。</span><span class="sxs-lookup"><span data-stu-id="7beed-123">In a plain area chart, if the values in multiple series are similar, the areas may overlap, obscuring important data point values.</span></span> <span data-ttu-id="7beed-124">您可以將圖表類型變更為堆疊區域圖 (其設計為顯示區域圖的多個數列) 來解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="7beed-124">You can resolve this issue by changing the chart type to a stacked area chart, which is designed to show multiple series on an area chart.</span></span>  
  
-   <span data-ttu-id="7beed-125">如果您的堆疊區域圖包含間隙，您的資料集可能包含空值，這些值在堆疊區域圖上會顯示為空的區段。</span><span class="sxs-lookup"><span data-stu-id="7beed-125">If your stacked area chart contains gaps, it is possible that your dataset includes empty values, which will be shown as a vacant section on a stacked area chart.</span></span> <span data-ttu-id="7beed-126">如果您的資料集包含空值，請考慮在圖表上插入空的點。</span><span class="sxs-lookup"><span data-stu-id="7beed-126">If your dataset includes empty values, consider inserting empty points on the chart.</span></span> <span data-ttu-id="7beed-127">加入空的點將會在圖表上，以不同的色彩填滿空的區域來表示 Null 或零值。</span><span class="sxs-lookup"><span data-stu-id="7beed-127">Adding empty points will fill in the empty areas on the chart with a different color to indicate null or zero values.</span></span> <span data-ttu-id="7beed-128">如需詳細資訊，請參閱[將空點加入圖表 &#40;報表產生器和 SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7beed-128">For more information, see [Add Empty Points to the Chart &#40;Report Builder and SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="7beed-129">區域圖類型在行為上非常類似於直條圖與折線圖。</span><span class="sxs-lookup"><span data-stu-id="7beed-129">Area chart types are very similar to column and line charts in behavior.</span></span> <span data-ttu-id="7beed-130">如果您要在多個數列間進行比較，請考慮改用直條圖。</span><span class="sxs-lookup"><span data-stu-id="7beed-130">If you are making a comparison between multiple series, consider using a column chart instead.</span></span> <span data-ttu-id="7beed-131">如果您要分析一段時間的趨勢，則考慮使用折線圖。</span><span class="sxs-lookup"><span data-stu-id="7beed-131">If you are analyzing trends over a period of time, consider using a line chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7beed-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7beed-132">See Also</span></span>  
 <span data-ttu-id="7beed-133">[圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7beed-133">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7beed-134">[圖表類型 &#40;報表產生器及 SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7beed-134">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7beed-135">[折線圖 &#40;報表產生器及 SSRS&#41;](line-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7beed-135">[Line Charts &#40;Report Builder and SSRS&#41;](line-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7beed-136">[變更圖表類型 &#40;報表產生器及 SSRS&#41;](change-a-chart-type-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7beed-136">[Change a Chart Type &#40;Report Builder and SSRS&#41;](change-a-chart-type-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7beed-137">圖表中的空白和 Null 資料點 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7beed-137">Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;</span></span>](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)  
  
  
