---
title: 指定軸間隔 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ae46712d-a5bf-44c0-9929-e30ccc1e7e33
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 70b64b824933753a8482360f193ca4ccf71e8d52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585014"
---
# <a name="specify-an-axis-interval-report-builder-and-ssrs"></a><span data-ttu-id="580db-102">指定軸間隔 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="580db-102">Specify an Axis Interval (Report Builder and SSRS)</span></span>
  <span data-ttu-id="580db-103">軸間隔定義軸上的標籤數及隨附的刻度。</span><span class="sxs-lookup"><span data-stu-id="580db-103">The axis interval defines the number of labels and accompanying tick marks on an axis.</span></span> <span data-ttu-id="580db-104">在值軸上，軸間隔會為圖表上的資料點提供一致的量值；</span><span class="sxs-lookup"><span data-stu-id="580db-104">On the value axis, axis intervals provide a consistent measure of the data points on the chart.</span></span> <span data-ttu-id="580db-105">不過，在類別目錄軸上，這項功能則可能導致類別目錄無法顯示軸標籤。</span><span class="sxs-lookup"><span data-stu-id="580db-105">However, on the category axis, this functionality can cause categories to appear without axis labels.</span></span> <span data-ttu-id="580db-106">您可以在軸 Interval 屬性中指定所需間隔數。</span><span class="sxs-lookup"><span data-stu-id="580db-106">You can specify the number of intervals you want in the axis Interval property.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="580db-107">會根據結果集中的資料，在執行階段計算間隔數。</span><span class="sxs-lookup"><span data-stu-id="580db-107">calculates the number of intervals at run time, based on the data in the result set.</span></span> <span data-ttu-id="580db-108">如需如何計算軸間隔的詳細資訊，請參閱[格式化圖表上的軸標籤 &#40;報表產生器及 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="580db-108">For more information about how axis intervals are calculated, see [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="580db-109">此主題並不適用於類別目錄軸上的日期或時間值。</span><span class="sxs-lookup"><span data-stu-id="580db-109">This topic is not applicable for date or time values on the category axis.</span></span> <span data-ttu-id="580db-110">根據預設，`DateTime` 值會顯示為天。</span><span class="sxs-lookup"><span data-stu-id="580db-110">Be default, `DateTime` values appear as days.</span></span> <span data-ttu-id="580db-111">若要指定其他的日期或時間間隔 (例如月份或時間間隔)，則必須設定軸標籤的格式，並將軸設定為顯示 `DateTime` 類型 (而非 `String` 類型) 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="580db-111">To specify a different date or time interval, such as a month or time interval, you must format the axis labels and set the axis to display instances of `DateTime` types instead of `String` types.</span></span> <span data-ttu-id="580db-112">此外，也必須設定 Interval 屬性。</span><span class="sxs-lookup"><span data-stu-id="580db-112">In addition, you must set the Interval property.</span></span> <span data-ttu-id="580db-113">如需詳細資訊，請參閱[將軸標籤格式化成日期或貨幣 &#40;報表產生器及 SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="580db-113">For more information, see [Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="580db-114">此主題並不適用於圓形圖、環圈圖、漏斗圖或金字塔圖，因為這些圖表並沒有軸。</span><span class="sxs-lookup"><span data-stu-id="580db-114">This topic does not apply to pie, doughnut, funnel or pyramid charts, which do not have axes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="580db-115">類別目錄軸通常是水平軸或 X 軸。</span><span class="sxs-lookup"><span data-stu-id="580db-115">The category axis is usually the horizontal or x-axis.</span></span> <span data-ttu-id="580db-116">不過，如果是長條圖，類別目錄軸會是垂直軸或 Y 軸。</span><span class="sxs-lookup"><span data-stu-id="580db-116">However, for bar charts, the category axis is the vertical or y-axis.</span></span>  
  
 <span data-ttu-id="580db-117">指定不同軸間隔的圖表範例可從範例報表取得。</span><span class="sxs-lookup"><span data-stu-id="580db-117">An example of a chart specifying different axis intervals is available as a sample report.</span></span> <span data-ttu-id="580db-118">如需下載這個範例報表及其他項目的詳細資訊，請參閱 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][報表產生器與報表設計師範例報表](https://go.microsoft.com/fwlink/?LinkId=198283)：</span><span class="sxs-lookup"><span data-stu-id="580db-118">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-show-all-category-labels-on-the-x-axis"></a><span data-ttu-id="580db-119">若要在 X 軸上顯示所有類別目錄標籤</span><span class="sxs-lookup"><span data-stu-id="580db-119">To show all category labels on the x-axis</span></span>  
  
1.  <span data-ttu-id="580db-120">以滑鼠右鍵按一下類別目錄軸，然後按一下 **[軸屬性]**。</span><span class="sxs-lookup"><span data-stu-id="580db-120">Right-click the category axis and click **Axis Properties**.</span></span> <span data-ttu-id="580db-121">**[軸屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="580db-121">The **Axis Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="580db-122">在 [**軸選項**] 中，將設定 `Interval` 為**1**。</span><span class="sxs-lookup"><span data-stu-id="580db-122">In **Axis Options**, set `Interval` to **1**.</span></span> <span data-ttu-id="580db-123">每個類別目錄群組標籤隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="580db-123">Every category group label is displayed.</span></span> <span data-ttu-id="580db-124">如果想要在 X 軸上每隔一個類別目錄群組標籤進行顯示，請輸入 **2**。</span><span class="sxs-lookup"><span data-stu-id="580db-124">If you want to show every other category group label on the x-axis, type **2**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="580db-125">在設定軸間隔後，所有的自動標籤都會停用。</span><span class="sxs-lookup"><span data-stu-id="580db-125">When an axis interval is set, all automatic labeling is disabled.</span></span> <span data-ttu-id="580db-126">如果指定軸間隔的值，則可能會遭遇非預期的標籤行為，依類別目錄軸上有多少類別目錄而定。</span><span class="sxs-lookup"><span data-stu-id="580db-126">If you specify a value for the axis interval, you may experience unpredictable labeling behavior depending on how many categories are on the category axis.</span></span>  
  
### <a name="to-enable-a-variable-interval-calculation-on-an-axis"></a><span data-ttu-id="580db-127">在軸上啟用可變間隔計算</span><span class="sxs-lookup"><span data-stu-id="580db-127">To enable a variable interval calculation on an axis</span></span>  
  
1.  <span data-ttu-id="580db-128">以滑鼠右鍵按一下要變更的圖表軸，然後按一下 **[軸屬性]**。</span><span class="sxs-lookup"><span data-stu-id="580db-128">Right-click the chart axis that you want to change, and then click **Axis Properties**.</span></span> <span data-ttu-id="580db-129">**[軸屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="580db-129">The **Axis Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="580db-130">在 [**軸選項**] 中，設定 `Interval` 為 [**自動**]。圖表會顯示可沿著軸容納的最佳類別目錄標籤數目。</span><span class="sxs-lookup"><span data-stu-id="580db-130">In **Axis Options**, set `Interval` to **Auto**. The chart will display the optimal number of category labels that can fit along the axis.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="580db-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="580db-131">See Also</span></span>  
 <span data-ttu-id="580db-132">[將圖表格式化 &#40;報表產生器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="580db-132">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="580db-133">[格式化圖表上的資料點 &#40;報表產生器和 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="580db-133">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="580db-134">[在資料區域中排序資料 &#40;報表產生器和 SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="580db-134">[Sort Data in a Data Region &#40;Report Builder and SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="580db-135">[軸屬性對話方塊、軸選項 &#40;報表產生器和 SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="580db-135">[Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="580db-136">[指定報表產生器和 SSRS 的對數刻度 &#40;&#41;](specify-a-logarithmic-scale-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="580db-136">[Specify a Logarithmic Scale &#40;Report Builder and SSRS&#41;](specify-a-logarithmic-scale-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="580db-137">繪製副座標軸上的資料 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="580db-137">Plot Data on a Secondary Axis &#40;Report Builder and SSRS&#41;</span></span>](plot-data-on-a-secondary-axis-report-builder-and-ssrs.md)  
  
  
