---
title: 在圓形圖外部顯示資料點標籤 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 959b7574-cf43-470b-b592-4944d8a9948f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dd4f38f24d2729acacfa3520635b93d8af2e9433
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704929"
---
# <a name="display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs"></a><span data-ttu-id="3b848-102">在圓形圖外部顯示資料點標籤 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="3b848-102">Display Data Point Labels Outside a Pie Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="3b848-103">在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中，圓形圖標籤經過最佳化，只會顯示在幾個資料扇形區上。</span><span class="sxs-lookup"><span data-stu-id="3b848-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], pie chart labeling is optimized to display labels on only several slices of data.</span></span> <span data-ttu-id="3b848-104">如果圓形圖包含的扇形區過多，標籤可能會重疊。</span><span class="sxs-lookup"><span data-stu-id="3b848-104">Labels may overlap if the pie chart contains too many slices.</span></span> <span data-ttu-id="3b848-105">其中一種解決方法是將標籤顯示在圓形圖外部，這樣可能可以為較長的資料標籤創造更多空間。</span><span class="sxs-lookup"><span data-stu-id="3b848-105">One solution is to display the labels outside the pie chart, which may create more room for longer data labels.</span></span> <span data-ttu-id="3b848-106">如果您發現標籤仍會重疊，則可以透過啟用 3D 來建立更多的標籤空間。</span><span class="sxs-lookup"><span data-stu-id="3b848-106">If you find that your labels still overlap, you can create more space for them by enabling 3D.</span></span> <span data-ttu-id="3b848-107">如此可以縮減圓形圖的直徑，而在圖表外部建立更多空間。</span><span class="sxs-lookup"><span data-stu-id="3b848-107">This reduces the diameter of the pie chart, creating more space around the chart.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-data-point-labels-inside-a-pie-chart"></a><span data-ttu-id="3b848-108">在圓形圖內部顯示資料點標籤</span><span class="sxs-lookup"><span data-stu-id="3b848-108">To display data point labels inside a pie chart</span></span>  
  
1.  <span data-ttu-id="3b848-109">將圓形圖加入到報表中。</span><span class="sxs-lookup"><span data-stu-id="3b848-109">Add a pie chart to your report.</span></span> <span data-ttu-id="3b848-110">如需詳細資訊，請參閱[將圖表加入至報表 &#40;報表產生器及 SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="3b848-110">For more information, see [Add a Chart to a Report &#40;Report Builder and SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="3b848-111">在設計介面上以滑鼠右鍵按一下圖表，然後選取 [顯示資料標籤]  。</span><span class="sxs-lookup"><span data-stu-id="3b848-111">On the design surface, right-click on the chart and select **Show Data Labels**.</span></span>  
  
### <a name="to-display-data-point-labels-outside-a-pie-chart"></a><span data-ttu-id="3b848-112">在圓形圖外部顯示資料點標籤</span><span class="sxs-lookup"><span data-stu-id="3b848-112">To display data point labels outside a pie chart</span></span>  
  
1.  <span data-ttu-id="3b848-113">建立圓形圖和顯示資料標籤。</span><span class="sxs-lookup"><span data-stu-id="3b848-113">Create a pie chart and display the data labels.</span></span>  
  
2.  <span data-ttu-id="3b848-114">開啟 [屬性] 窗格。</span><span class="sxs-lookup"><span data-stu-id="3b848-114">Open the Properties pane.</span></span>  
  
3.  <span data-ttu-id="3b848-115">在設計介面上，按一下圓形圖本身，可在 [屬性] 窗格中顯示 [類別目錄]  屬性。</span><span class="sxs-lookup"><span data-stu-id="3b848-115">On the design surface, click on the pie itself to display the **Category** properties in the Properties pane.</span></span>  
  
4.  <span data-ttu-id="3b848-116">展開 **CustomAttributes** 節點。</span><span class="sxs-lookup"><span data-stu-id="3b848-116">Expand the **CustomAttributes** node.</span></span> <span data-ttu-id="3b848-117">圓形圖的屬性清單隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="3b848-117">A list of attributes for the pie chart is displayed.</span></span>  
  
5.  <span data-ttu-id="3b848-118">將 **PieLabelStyle** 屬性設定為 **Outside**。</span><span class="sxs-lookup"><span data-stu-id="3b848-118">Set the **PieLabelStyle** property to **Outside**.</span></span>  
  
6.  <span data-ttu-id="3b848-119">將 `PieLineColor` 屬性設定為**黑色**。</span><span class="sxs-lookup"><span data-stu-id="3b848-119">Set the `PieLineColor` property to **Black**.</span></span> <span data-ttu-id="3b848-120">PieLineColor 屬性定義每個資料點標籤的註標線。</span><span class="sxs-lookup"><span data-stu-id="3b848-120">The PieLineColor property defines callout lines for each data point label.</span></span>  
  
### <a name="to-prevent-overlapping-labels-displayed-outside-a-pie-chart"></a><span data-ttu-id="3b848-121">若要防止在圓形圖外部顯示重疊的標籤</span><span class="sxs-lookup"><span data-stu-id="3b848-121">To prevent overlapping labels displayed outside a pie chart</span></span>  
  
1.  <span data-ttu-id="3b848-122">建立具有外部標籤的圓形圖。</span><span class="sxs-lookup"><span data-stu-id="3b848-122">Create a pie chart with external labels.</span></span>  
  
2.  <span data-ttu-id="3b848-123">在設計介面上以滑鼠右鍵按一下圓形圖外部 (但位於圖表框線內)，然後選取 [圖表區域屬性]  。[圖表區域屬性]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="3b848-123">On the design surface, right-click outside the pie chart but inside the chart borders and select **Chart Area Properties**.The **Chart AreaProperties** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="3b848-124">在 [3D 選項]  索引標籤上，選取 [啟用 3D]  。</span><span class="sxs-lookup"><span data-stu-id="3b848-124">On the **3D Options** tab, select **Enable 3D**.</span></span>  
  
4.  <span data-ttu-id="3b848-125">如果希望圖表的標籤有更多的空間，但仍然以二維方式呈現，請將 [旋轉]  和 [傾斜]  屬性設定為 **0**。</span><span class="sxs-lookup"><span data-stu-id="3b848-125">If you want the chart to have more room for labels but still appear two-dimensional, set the **Rotation** and **Inclination** properties to **0**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b848-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b848-126">See Also</span></span>  
 <span data-ttu-id="3b848-127">[圓形圖 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3b848-127">[Pie Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3b848-128">[收集圓形圖上的小配量 &#40;報表產生器及 SSRS&#41;](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3b848-128">[Collect Small Slices on a Pie Chart &#40;Report Builder and SSRS&#41;](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="3b848-129">在圓形圖上顯示百分比值 &#40;報表產生器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3b848-129">Display Percentage Values on a Pie Chart &#40;Report Builder and SSRS&#41;</span></span>](display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  
