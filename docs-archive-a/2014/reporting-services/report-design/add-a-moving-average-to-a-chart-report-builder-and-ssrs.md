---
title: 將移動平均新增至圖表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 166cf9c1-0750-4866-8381-542e4fbfe65a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9bc16d0cb45a3240148f931009a836c231b442b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585042"
---
# <a name="add-a-moving-average-to-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="d6a50-102">將移動平均加入至圖表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="d6a50-102">Add a Moving Average to a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d6a50-103">移動平均是數列中資料的平均，是根據定義的一段時間而計算。</span><span class="sxs-lookup"><span data-stu-id="d6a50-103">A moving average is an average of the data in your series, calculated over a defined period of time.</span></span> <span data-ttu-id="d6a50-104">您可以在圖表上顯示移動平均以識別明顯的趨勢。</span><span class="sxs-lookup"><span data-stu-id="d6a50-104">The moving average can be shown on the chart to identify significant trends.</span></span>  
  
 <span data-ttu-id="d6a50-105">「移動平均」公式是技術分析中最常使用的價格指標。</span><span class="sxs-lookup"><span data-stu-id="d6a50-105">The Moving Average formula is the most popular price indicator used in technical analyses.</span></span> <span data-ttu-id="d6a50-106">您也可以從圖表上的數列衍生許多其他公式 (包括平均、中間值和標準差等)。</span><span class="sxs-lookup"><span data-stu-id="d6a50-106">Many other formulas, including mean, median and standard deviation, can also be derived from a series on the chart.</span></span> <span data-ttu-id="d6a50-107">在指定移動平均時，每個公式都可能有一或多個必須指定的參數。</span><span class="sxs-lookup"><span data-stu-id="d6a50-107">When specifying a moving average, each formula may have one or more parameters that must be specified.</span></span>  
  
 <span data-ttu-id="d6a50-108">以設計模式加入移動平均公式時，所加入的線數列只是視覺化的預留位置。</span><span class="sxs-lookup"><span data-stu-id="d6a50-108">When a moving average formula is added in Design mode, the line series that is added is only a visual placeholder.</span></span> <span data-ttu-id="d6a50-109">圖表會在報表處理期間計算每個公式的資料點。</span><span class="sxs-lookup"><span data-stu-id="d6a50-109">The chart will calculate the data points of each formula during report processing.</span></span>  
  
 <span data-ttu-id="d6a50-110">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中不提供趨勢線的內建支援。</span><span class="sxs-lookup"><span data-stu-id="d6a50-110">Built-in support for trend lines is not available in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-calculated-moving-average-to-a-series-on-the-chart"></a><span data-ttu-id="d6a50-111">將導出的移動平均加入至圖表上的數列</span><span class="sxs-lookup"><span data-stu-id="d6a50-111">To add a calculated moving average to a series on the chart</span></span>  
  
1.  <span data-ttu-id="d6a50-112">以滑鼠右鍵按一下 **[值]** 區域中的欄位，然後按一下 **[加入導出數列]**。</span><span class="sxs-lookup"><span data-stu-id="d6a50-112">Right-click on a field in the **Values** area and click **Add Calculated Series**.</span></span> <span data-ttu-id="d6a50-113">**[導出數列屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d6a50-113">The **Calculated Series Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="d6a50-114">從 **[公式]** 下拉式清單中，選取 **[移動平均]** 選項。</span><span class="sxs-lookup"><span data-stu-id="d6a50-114">Select the **Moving average** option from the **Formula** drop-down list.</span></span>  
  
3.  <span data-ttu-id="d6a50-115">為代表移動平均週期的 **[週期]** 指定整數值。</span><span class="sxs-lookup"><span data-stu-id="d6a50-115">Specify an integer value for the **Period** that represents the period of the moving average.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d6a50-116">週期是用來計算移動平均的天數。</span><span class="sxs-lookup"><span data-stu-id="d6a50-116">The period is the number of days used to calculate a moving average.</span></span> <span data-ttu-id="d6a50-117">如果沒有在 X 軸上指定日期/時間值，則週期會由用來計算移動平均的資料點數目代表。</span><span class="sxs-lookup"><span data-stu-id="d6a50-117">If date/time values are not specified on the x-axis, the period is represented by the number of data points used to calculate a moving average.</span></span> <span data-ttu-id="d6a50-118">如果只有一個資料點，則移動平均公式不會進行計算。</span><span class="sxs-lookup"><span data-stu-id="d6a50-118">If there is only one data point, the moving average formula does not calculate.</span></span> <span data-ttu-id="d6a50-119">移動平均會從第二個點開始計算。</span><span class="sxs-lookup"><span data-stu-id="d6a50-119">The moving average is calculated starting at the second point.</span></span> <span data-ttu-id="d6a50-120">如果指定 **[從第一個點開始]** 選項，則移動平均會從圖表的第一個點開始。</span><span class="sxs-lookup"><span data-stu-id="d6a50-120">If you specify the **Start from first point** option, the chart will start the moving average at the first point.</span></span> <span data-ttu-id="d6a50-121">如果只有一個資料點，則導出的移動平均中的點會與原始數列中的第一個點相同。</span><span class="sxs-lookup"><span data-stu-id="d6a50-121">If there is only one data point, the point in the calculated moving average will be identical to the first point in your original series.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6a50-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6a50-122">See Also</span></span>  
 <span data-ttu-id="d6a50-123">[將圖表格式化 &#40;報表產生器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d6a50-123">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d6a50-124">[圖表 &#40;報表產生器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d6a50-124">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="d6a50-125">將空點加入至圖表 &#40;報表產生器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d6a50-125">Add Empty Points to the Chart &#40;Report Builder and SSRS&#41;</span></span>](add-empty-points-to-a-chart-report-builder-and-ssrs.md)  
  
  
