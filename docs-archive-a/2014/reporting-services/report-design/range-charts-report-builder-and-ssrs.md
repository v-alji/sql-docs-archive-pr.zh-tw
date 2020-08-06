---
title: 範圍圖表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 48e351d3-ac5b-4eda-a4bd-32a0de206a30
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 76a9723bc55030da59d22c945a40ce4418b84ab3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702450"
---
# <a name="range-charts-report-builder-and-ssrs"></a><span data-ttu-id="76818-102">範圍圖表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="76818-102">Range Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="76818-103">範圍圖表類型會顯示一組資料點，每個點都是由相同類別的多個值所定義。</span><span class="sxs-lookup"><span data-stu-id="76818-103">A range chart type displays a set of data points that are each defined by multiple values for the same category.</span></span> <span data-ttu-id="76818-104">這些值會以值軸所測量的標記高度來表示。</span><span class="sxs-lookup"><span data-stu-id="76818-104">Values are represented by the height of the marker as measured by the value axis.</span></span> <span data-ttu-id="76818-105">類別標籤會顯示在類別軸上。</span><span class="sxs-lookup"><span data-stu-id="76818-105">Category labels are displayed on the category axis.</span></span> <span data-ttu-id="76818-106">一般範圍圖表會針對每個資料點，填滿上界值和下界值之間的區域。</span><span class="sxs-lookup"><span data-stu-id="76818-106">The plain range chart fills in the area between the top and bottom value for each data point.</span></span>  
  
 <span data-ttu-id="76818-107">下圖顯示的是包含三個數列的一般範圍圖表。</span><span class="sxs-lookup"><span data-stu-id="76818-107">The following illustration shows a plain range chart with three series.</span></span>  
  
 <span data-ttu-id="76818-108">![範圍圖](../media/rs-rangechart.gif "範圍圖")</span><span class="sxs-lookup"><span data-stu-id="76818-108">![Range chart](../media/rs-rangechart.gif "Range chart")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="76818-109">變化</span><span class="sxs-lookup"><span data-stu-id="76818-109">Variations</span></span>  
  
-   <span data-ttu-id="76818-110">**平滑範圍圖表**：</span><span class="sxs-lookup"><span data-stu-id="76818-110">**Smooth range**.</span></span> <span data-ttu-id="76818-111">平滑範圍圖表會顯示曲線而不是直線。</span><span class="sxs-lookup"><span data-stu-id="76818-111">A smooth range chart displays curved lines rather than straight.</span></span>  
  
-   <span data-ttu-id="76818-112">**資料行範圍**：</span><span class="sxs-lookup"><span data-stu-id="76818-112">**Column range**.</span></span> <span data-ttu-id="76818-113">資料行範圍圖表會使用資料行 (而非區域) 來顯示範圍。</span><span class="sxs-lookup"><span data-stu-id="76818-113">A column range chart uses columns instead of areas to display the ranges.</span></span>  
  
-   <span data-ttu-id="76818-114">**橫條範圍**：</span><span class="sxs-lookup"><span data-stu-id="76818-114">**Bar range**.</span></span> <span data-ttu-id="76818-115">橫條範圍圖表會使用橫條 (而非區域) 來顯示範圍。</span><span class="sxs-lookup"><span data-stu-id="76818-115">A bar range chart uses bars instead of areas to display the ranges.</span></span>  
  
## <a name="data-considerations-for-range-charts"></a><span data-ttu-id="76818-116">範圍圖表的資料考量</span><span class="sxs-lookup"><span data-stu-id="76818-116">Data Considerations for Range Charts</span></span>  
  
-   <span data-ttu-id="76818-117">範圍圖表類型的每個資料點都需要兩個值。</span><span class="sxs-lookup"><span data-stu-id="76818-117">Range chart types require two values per data point.</span></span> <span data-ttu-id="76818-118">這些值會與定義每個資料點範圍的最高值和最低值相對應。</span><span class="sxs-lookup"><span data-stu-id="76818-118">These values correspond with a high value and a low value that defines the range for each data point.</span></span>  
  
-   <span data-ttu-id="76818-119">只有在上界值永遠高於下界值時，範圍圖表才適用於分析。</span><span class="sxs-lookup"><span data-stu-id="76818-119">Range charts are useful for analysis only if the top values are always higher than the bottom values.</span></span> <span data-ttu-id="76818-120">否則，請考慮使用折線圖。</span><span class="sxs-lookup"><span data-stu-id="76818-120">If this is not the case, consider using a line chart.</span></span> <span data-ttu-id="76818-121">如果最高值低於最低值，範圍圖表將會顯示這些值之間之差異的絕對值。</span><span class="sxs-lookup"><span data-stu-id="76818-121">If the high value is lower the low value, the range chart will display the absolute value of the difference between these values.</span></span>  
  
-   <span data-ttu-id="76818-122">如果只有指定一個值，範圍圖表將會當做一般區域圖表顯示，其中每個資料點都有一個值。</span><span class="sxs-lookup"><span data-stu-id="76818-122">If only one value is specified, the range chart will display as if it were a regular area chart, with one value per data point.</span></span>  
  
-   <span data-ttu-id="76818-123">範圍圖表通常用於圖形資料，其中資料集中包含每個類別目錄群組的最小值與最大值。</span><span class="sxs-lookup"><span data-stu-id="76818-123">Range charts are often used to graph data that contains minimum and maximum values for each category group in the dataset.</span></span>  
  
-   <span data-ttu-id="76818-124">在範圍圖表上，不支援顯示每個資料點的標記。</span><span class="sxs-lookup"><span data-stu-id="76818-124">Displaying markers on each data point is not supported on the range chart.</span></span>  
  
-   <span data-ttu-id="76818-125">如果在多個數列中的值相似，這些數列將會重疊，就像一般範圍圖表中的區域圖表一樣。</span><span class="sxs-lookup"><span data-stu-id="76818-125">Like the area chart, in a plain range chart, if the values in multiple series are similar, the series will overlap.</span></span> <span data-ttu-id="76818-126">在此狀況下，您可能會想要使用資料行範圍圖表或橫條範圍圖表，而非一般範圍圖表。</span><span class="sxs-lookup"><span data-stu-id="76818-126">In this scenario, you may want to use a column range or bar range chart instead of a plain range chart.</span></span>  
  
-   <span data-ttu-id="76818-127">甘特圖可以使用範圍橫條圖建立。</span><span class="sxs-lookup"><span data-stu-id="76818-127">Gantt charts can be created using a range bar chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76818-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76818-128">See Also</span></span>  
 <span data-ttu-id="76818-129">[圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="76818-129">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="76818-130">[圖表類型 &#40;報表產生器及 SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="76818-130">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="76818-131">格式化圖表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="76818-131">Formatting a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-a-chart-report-builder-and-ssrs.md)  
  
  
