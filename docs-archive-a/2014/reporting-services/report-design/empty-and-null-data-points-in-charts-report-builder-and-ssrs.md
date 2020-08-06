---
title: 圖表中的空白和 Null 資料點 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: faddd29d-4cc1-4c2c-8e29-d3d9918fe22a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3f0826a202969b432e53b3c57ddfe80680ba99e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686825"
---
# <a name="empty-and-null-data-points-in-charts-report-builder-and-ssrs"></a><span data-ttu-id="713ea-102">圖表中的空白和 Null 資料點 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="713ea-102">Empty and Null Data Points in Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="713ea-103">如果您要在圖表中顯示包含空白或 Null 值的欄位，圖表外觀可能不如您預期。</span><span class="sxs-lookup"><span data-stu-id="713ea-103">If you are displaying fields with empty or null values in your chart, the chart may not look as you expect.</span></span> <span data-ttu-id="713ea-104">圖表會根據指定的圖表類型，以不同的方式處理空白值：</span><span class="sxs-lookup"><span data-stu-id="713ea-104">Charts process empty values differently depending on the specified chart type:</span></span>  
  
-   <span data-ttu-id="713ea-105">如果圖表類型是線性圖表類型 (橫條圖、直條圖、散佈圖、折線圖、區域圖、範圍圖)，則空白值會在圖表中顯示為空格或「間距」。</span><span class="sxs-lookup"><span data-stu-id="713ea-105">If the chart type is a linear chart type (bar, column, scatter, line, area, range), empty values are displayed as empty spaces or "gaps" in the chart.</span></span> <span data-ttu-id="713ea-106">如果想要指出空點，必須加入空點預留位置。</span><span class="sxs-lookup"><span data-stu-id="713ea-106">If you want to indicate empty points, you must add empty point placeholders.</span></span> <span data-ttu-id="713ea-107">如需詳細資訊，請參閱[將空點加入圖表 &#40;報表產生器和 SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="713ea-107">For more information, see [Add Empty Points to the Chart &#40;Report Builder and SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="713ea-108">如果圖表類型是連續的線性圖表類型 (區域圖、橫條圖、直條圖、折線圖、散佈圖)，則空白的資料點會加入到圖表以維持數列的連續性。</span><span class="sxs-lookup"><span data-stu-id="713ea-108">If the chart type is a contiguous, linear chart type (area, bar, column, line, scatter), empty data points are added to the chart to maintain continuity in the series.</span></span>  
  
-   <span data-ttu-id="713ea-109">如果圖表類型是非線性圖表類型 (極座標圖、圓形圖、環圈圖、漏斗圖或金字塔圖)，則圖表會省略空白值的顯示。</span><span class="sxs-lookup"><span data-stu-id="713ea-109">If the chart type is a nonlinear chart type (polar, pie, doughnut, funnel or pyramid), empty values are omitted from display on the chart.</span></span>  
  
-   <span data-ttu-id="713ea-110">形狀圖圖表類型中會省略 Null 值。</span><span class="sxs-lookup"><span data-stu-id="713ea-110">In shape chart types, null values are omitted.</span></span>  
  
 <span data-ttu-id="713ea-111">具有空資料點的圖表範例可從範例報表取得。</span><span class="sxs-lookup"><span data-stu-id="713ea-111">An example of a chart with empty data points is available as a sample report.</span></span> <span data-ttu-id="713ea-112">如需下載這個範例報表及其他項目的詳細資訊，請參閱 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][報表產生器與報表設計師範例報表](https://go.microsoft.com/fwlink/?LinkId=198283)：</span><span class="sxs-lookup"><span data-stu-id="713ea-112">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="removing-empty-or-null-values"></a><span data-ttu-id="713ea-113">移除空白或 Null 值</span><span class="sxs-lookup"><span data-stu-id="713ea-113">Removing Empty or Null Values</span></span>  
 <span data-ttu-id="713ea-114">若要避免重要資料不易辨認，請考慮從資料集移除空白值。</span><span class="sxs-lookup"><span data-stu-id="713ea-114">To avoid obscuring important data, consider removing empty values from your dataset.</span></span> <span data-ttu-id="713ea-115">若要篩選 Null 值，可以在查詢中使用 NOT IS NULL 子句。</span><span class="sxs-lookup"><span data-stu-id="713ea-115">To filter nulls, you can use the NOT IS NULL clause in your query.</span></span> <span data-ttu-id="713ea-116">或者也可以加入篩選運算式，指定您只要顯示不等於零的值。</span><span class="sxs-lookup"><span data-stu-id="713ea-116">Alternatively, you can add a filtering expression that specifies that you only want to display values not equal to zero.</span></span> <span data-ttu-id="713ea-117">如需詳細資訊，請參閱 [加入資料集篩選、資料區篩選和群組篩選 &#40;報表產生器及 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="713ea-117">For more information, see [Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md).</span></span>  
  
## <a name="fields-with-no-values-in-a-chart"></a><span data-ttu-id="713ea-118">圖表中沒有值的欄位</span><span class="sxs-lookup"><span data-stu-id="713ea-118">Fields with No Values in a Chart</span></span>  
 <span data-ttu-id="713ea-119">如果在傳回的資料集中欄位未包含任何值，則圖表會顯示沒有資料點的空白圖表，但會加入數列名稱 (通常為欄位名稱) 做為圖例項目。</span><span class="sxs-lookup"><span data-stu-id="713ea-119">If a field does not contain any values in the returned dataset, the chart displays an empty chart with no data points, but the series name (typically the field name) is added as a legend item.</span></span>  
  
 <span data-ttu-id="713ea-120">這項行為與傳回資料集中有零個資料列的情況不同，後者可能會發生在當報表已進行參數化，而選取的值傳回空白結果集時。</span><span class="sxs-lookup"><span data-stu-id="713ea-120">This behavior differs from the case where there are zero rows of data in the returned dataset, which can occur when the report is parameterized and the selected value returns an empty result set.</span></span> <span data-ttu-id="713ea-121">如果資料集查詢傳回零個資料列，則系統會在執行階段會顯示訊息，指出沒有可以顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="713ea-121">If your dataset query returns zero rows of data, a message is displayed at run time to indicate that no data can be shown.</span></span> <span data-ttu-id="713ea-122">您可以在 [屬性]  窗格中修改報表的 NoDataMessage 標題，以自訂這個訊息。</span><span class="sxs-lookup"><span data-stu-id="713ea-122">You can customize this message by modifying the NoDataMessage caption for the report in the **Properties** pane.</span></span> <span data-ttu-id="713ea-123">如需詳細資訊，請參閱 [報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="713ea-123">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="713ea-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="713ea-124">See Also</span></span>  
 <span data-ttu-id="713ea-125">[圖表 &#40;報表產生器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="713ea-125">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="713ea-126">[將圖表格式化 &#40;報表產生器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="713ea-126">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="713ea-127">[將圖表新增至報表 &#40;報表產生器和 SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="713ea-127">[Add a Chart to a Report &#40;Report Builder and SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="713ea-128">疑難排解圖表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="713ea-128">Troubleshoot Charts &#40;Report Builder and SSRS&#41;</span></span>](troubleshoot-charts-report-builder-and-ssrs.md)  
  
  
