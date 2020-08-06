---
title: 將空點加入至圖表 (報表產生器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2b056119-439f-494f-83cf-ee0c05dc6487
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 53d891c58210bcd51cd4e49f2f9a691a7729c884
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706217"
---
# <a name="add-empty-points-to-the-chart-report-builder-and-ssrs"></a><span data-ttu-id="01e88-102">將空白點加入圖表中 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="01e88-102">Add Empty Points to the Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="01e88-103">Null 值會顯示在圖表上，當做數列內資料點之間的空格或間距。</span><span class="sxs-lookup"><span data-stu-id="01e88-103">Null values are shown on the chart as empty spaces or gaps between data points in a series.</span></span> <span data-ttu-id="01e88-104">空點是指可以插入由 Null 值所建立之空格內的資料點。</span><span class="sxs-lookup"><span data-stu-id="01e88-104">Empty points are data points that can be inserted in the empty space created by null values.</span></span>  
  
 <span data-ttu-id="01e88-105">根據預設，空點的計算方式是求得包含某個值之上一個和下一個資料點的平均值。</span><span class="sxs-lookup"><span data-stu-id="01e88-105">By default, empty points are calculated by taking the average of the previous and next data points that contain a value.</span></span> <span data-ttu-id="01e88-106">您可以變更這個值，好讓所有空白點都在零的地方插入。</span><span class="sxs-lookup"><span data-stu-id="01e88-106">You can change this so that all empty points are inserted at zero.</span></span>  
  
 <span data-ttu-id="01e88-107">如需詳細資訊，請參閱[圖表中的空白和 Null 資料點 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="01e88-107">For more information, see [Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-empty-points-on-a-chart"></a><span data-ttu-id="01e88-108">在圖表上指定空白點</span><span class="sxs-lookup"><span data-stu-id="01e88-108">To specify empty points on a chart</span></span>  
  
1.  <span data-ttu-id="01e88-109">開啟 [屬性] 窗格。</span><span class="sxs-lookup"><span data-stu-id="01e88-109">Open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="01e88-110">在設計介面上，以滑鼠右鍵按一下包含 Null 值的數列。</span><span class="sxs-lookup"><span data-stu-id="01e88-110">On the design surface, right-click the series that contains null values.</span></span> <span data-ttu-id="01e88-111">數列的屬性會顯示在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="01e88-111">The properties for the series are displayed in the Properties pane.</span></span>  
  
3.  <span data-ttu-id="01e88-112">展開 **[EmptyPoint]** 節點。</span><span class="sxs-lookup"><span data-stu-id="01e88-112">Expand the **EmptyPoint** node.</span></span>  
  
4.  <span data-ttu-id="01e88-113">為 Color 屬性選取色彩值。</span><span class="sxs-lookup"><span data-stu-id="01e88-113">Select a color value for the Color property.</span></span>  
  
5.  <span data-ttu-id="01e88-114">在 **[EmptyPoint]** 節點中，展開 [標記] 節點。</span><span class="sxs-lookup"><span data-stu-id="01e88-114">In the **EmptyPoint** node, expand the Marker node.</span></span>  
  
6.  <span data-ttu-id="01e88-115">為 MarkerType 屬性選取標記類型。</span><span class="sxs-lookup"><span data-stu-id="01e88-115">Select a marker type for the MarkerType property.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="01e88-116">您必須選取一個標記類型，以便將空點加入至橫條圖、直條圖或散佈圖。</span><span class="sxs-lookup"><span data-stu-id="01e88-116">You must select a marker type to add empty points to a bar, column or scatter chart.</span></span> <span data-ttu-id="01e88-117">但如果是區域圖、折線圖和雷達圖，則選取標記類型為選擇性的動作，因為該圖表會填入空白的空格或間距，而不需要指定標記。</span><span class="sxs-lookup"><span data-stu-id="01e88-117">However, for area, line and radar charts, selecting a marker type is optional because the chart fills in the empty space or gap without requiring a marker to be specified.</span></span>  
  
7.  <span data-ttu-id="01e88-118">設定空點的值。</span><span class="sxs-lookup"><span data-stu-id="01e88-118">Set the value of the empty point.</span></span>  
  
    1.  <span data-ttu-id="01e88-119">在 [屬性] 窗格中，展開 **[CustomAttributes]** 節點。</span><span class="sxs-lookup"><span data-stu-id="01e88-119">In the Properties pane, expand the **CustomAttributes** node.</span></span>  
  
    2.  <span data-ttu-id="01e88-120">設定 EmptyPointValue 屬性。</span><span class="sxs-lookup"><span data-stu-id="01e88-120">Set the EmptyPointValue property.</span></span> <span data-ttu-id="01e88-121">若要在上一個和下一個資料點的平均值處插入空點，請選取 **Average**。</span><span class="sxs-lookup"><span data-stu-id="01e88-121">To insert empty points at an average of the previous and next data points, select **Average**.</span></span> <span data-ttu-id="01e88-122">若要在零處插入空點，請選取 **Zero**。</span><span class="sxs-lookup"><span data-stu-id="01e88-122">To insert empty points at zero, select **Zero**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e88-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01e88-123">See Also</span></span>  
 <span data-ttu-id="01e88-124">[新增資料集篩選、資料區篩選和群組篩選 &#40;報表產生器及 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="01e88-124">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="01e88-125">[圖表類型 &#40;報表產生器及 SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="01e88-125">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="01e88-126">[新增刻度斷層至圖表 &#40;報表產生器及 SSRS&#41;](add-scale-breaks-to-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="01e88-126">[Add Scale Breaks to a Chart &#40;Report Builder and SSRS&#41;](add-scale-breaks-to-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="01e88-127">圖表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="01e88-127">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
