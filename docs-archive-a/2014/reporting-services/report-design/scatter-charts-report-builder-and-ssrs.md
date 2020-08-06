---
title: 散佈圖 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2520ae24-0609-4890-807d-3267018aba8e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 93f9b31089eb8399c7fdfd201d3c799608f2e91e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702453"
---
# <a name="scatter-charts-report-builder-and-ssrs"></a><span data-ttu-id="3ed0c-102">散佈圖 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="3ed0c-102">Scatter Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="3ed0c-103">散佈圖會將數列顯示成一組點。</span><span class="sxs-lookup"><span data-stu-id="3ed0c-103">A scatter chart displays a series as a set of points.</span></span> <span data-ttu-id="3ed0c-104">這些值會以點在圖表上的位置來表示。</span><span class="sxs-lookup"><span data-stu-id="3ed0c-104">Values are represented by the position of the points on the chart.</span></span> <span data-ttu-id="3ed0c-105">類別目錄會由圖表上不同的標記來表示。</span><span class="sxs-lookup"><span data-stu-id="3ed0c-105">Categories are represented by different markers on the chart.</span></span> <span data-ttu-id="3ed0c-106">散佈圖通常用來比較跨越類別目錄的彙總資料。</span><span class="sxs-lookup"><span data-stu-id="3ed0c-106">Scatter charts are typically used to compare aggregated data across categories.</span></span> <span data-ttu-id="3ed0c-107">如需如何將資料新增至散佈圖的詳細資訊，請參閱 [圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="3ed0c-107">For more information on how to add data to a scatter chart, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md)</span></span>  
  
 <span data-ttu-id="3ed0c-108">下圖顯示散佈圖的範例。</span><span class="sxs-lookup"><span data-stu-id="3ed0c-108">The following illustration shows an example of a scatter chart.</span></span>  
  
 <span data-ttu-id="3ed0c-109">![散佈圖](../media/rs-scatterchart.gif "散佈圖")</span><span class="sxs-lookup"><span data-stu-id="3ed0c-109">![Scatter chart](../media/rs-scatterchart.gif "Scatter chart")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="3ed0c-110">變化</span><span class="sxs-lookup"><span data-stu-id="3ed0c-110">Variations</span></span>  
  
-   <span data-ttu-id="3ed0c-111">**泡泡圖。**</span><span class="sxs-lookup"><span data-stu-id="3ed0c-111">**Bubble.**</span></span> <span data-ttu-id="3ed0c-112">泡泡圖會根據泡泡的大小，顯示資料點的兩個值之間的差異。</span><span class="sxs-lookup"><span data-stu-id="3ed0c-112">Bubble charts display the difference between two values of a data point based on the size of the bubble.</span></span> <span data-ttu-id="3ed0c-113">較大的泡泡，也就是兩個值之間較大的差異。</span><span class="sxs-lookup"><span data-stu-id="3ed0c-113">The larger the bubble, the larger the difference between the two values.</span></span>  
  
-   <span data-ttu-id="3ed0c-114">**立體泡泡圖**。</span><span class="sxs-lookup"><span data-stu-id="3ed0c-114">**3-D Bubble**.</span></span> <span data-ttu-id="3ed0c-115">泡泡圖以立體方式顯示。</span><span class="sxs-lookup"><span data-stu-id="3ed0c-115">A bubble chart displayed in 3-D.</span></span>  
  
## <a name="data-considerations-for-a-scatter-chart"></a><span data-ttu-id="3ed0c-116">散佈圖的資料考量</span><span class="sxs-lookup"><span data-stu-id="3ed0c-116">Data Considerations for a Scatter Chart</span></span>  
  
-   <span data-ttu-id="3ed0c-117">散佈圖通常用於顯示與比較數值，例如，科學、統計與工程資料。</span><span class="sxs-lookup"><span data-stu-id="3ed0c-117">Scatter charts are commonly used for displaying and comparing numeric values, such as scientific, statistical, and engineering data.</span></span>  
  
-   <span data-ttu-id="3ed0c-118">當您想要在不管時間的情況下比較大量資料點時，請使用散佈圖。</span><span class="sxs-lookup"><span data-stu-id="3ed0c-118">Use the scatter chart when you want to compare large numbers of data points without regard to time.</span></span> <span data-ttu-id="3ed0c-119">您在散佈圖中包含越多資料，您就可以達到越好的比較結果。</span><span class="sxs-lookup"><span data-stu-id="3ed0c-119">The more data that you include in a scatter chart, the better the comparisons that you can make.</span></span>  
  
-   <span data-ttu-id="3ed0c-120">泡泡圖的每個資料點都需要兩個值 (頂端和底部)。</span><span class="sxs-lookup"><span data-stu-id="3ed0c-120">The bubble chart requires two values (top and bottom) per data point.</span></span>  
  
-   <span data-ttu-id="3ed0c-121">散佈圖適合處理值的分佈與資料點的群集。</span><span class="sxs-lookup"><span data-stu-id="3ed0c-121">Scatter charts are ideal for handling the distribution of values and clusters of data points.</span></span> <span data-ttu-id="3ed0c-122">如果您的資料集包含許多點 (例如，數千個點)，則這是最佳的圖表類型。</span><span class="sxs-lookup"><span data-stu-id="3ed0c-122">This is the best chart type if your dataset contains many points (for example, several thousand points).</span></span> <span data-ttu-id="3ed0c-123">在點圖上顯示多個數列會擾亂視覺，應該予以避免。</span><span class="sxs-lookup"><span data-stu-id="3ed0c-123">Displaying multiple series on a point chart is visually distracting and should be avoided.</span></span> <span data-ttu-id="3ed0c-124">在此狀況下，請考慮使用折線圖。</span><span class="sxs-lookup"><span data-stu-id="3ed0c-124">In this scenario, consider using a line chart.</span></span>  
  
-   <span data-ttu-id="3ed0c-125">根據預設，散佈圖會將資料點顯示為圓形。</span><span class="sxs-lookup"><span data-stu-id="3ed0c-125">By default, scatter charts display data points as circles.</span></span> <span data-ttu-id="3ed0c-126">如果您在散佈圖上有多個數列，請考慮將每個點的標記形狀變更為正方形、三角形、菱形或其他形狀。</span><span class="sxs-lookup"><span data-stu-id="3ed0c-126">If you have multiple series on a scatter chart, consider changing the marker shape of each point to be square, triangle, diamond, or another shape.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ed0c-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ed0c-127">See Also</span></span>  
 <span data-ttu-id="3ed0c-128">[圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3ed0c-128">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3ed0c-129">[圖表類型 &#40;報表產生器及 SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3ed0c-129">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3ed0c-130">[格式化圖表 &#40;報表產生器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3ed0c-130">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="3ed0c-131">折線圖 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3ed0c-131">Line Charts &#40;Report Builder and SSRS&#41;</span></span>](line-charts-report-builder-and-ssrs.md)  
  
  
