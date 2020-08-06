---
title: 股票圖 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f75ca11e-b7f5-4ac0-ba17-fe6f82742dad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a0f8c9c7dbc750bdb477f2ea1d96aa03f7ad022f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585006"
---
# <a name="stock-charts-report-builder-and-ssrs"></a><span data-ttu-id="19066-102">股票圖 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="19066-102">Stock Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="19066-103">股票圖是特別針對每個資料點最多使用四個值的財務或科學資料而設計的。</span><span class="sxs-lookup"><span data-stu-id="19066-103">A stock chart is specifically designed for financial or scientific data that uses up to four values per data point.</span></span> <span data-ttu-id="19066-104">這些值會讓用於繪製財務股票資料的最高值、最低值、開盤值與收盤值排成一列。</span><span class="sxs-lookup"><span data-stu-id="19066-104">These values align with the high, low, open and close values that are used to plot financial stock data.</span></span> <span data-ttu-id="19066-105">此圖表類型會使用標記 (通常是線條或三角形) 來顯示開盤值與收盤值。</span><span class="sxs-lookup"><span data-stu-id="19066-105">This chart type displays opening and closing values by using markers, which are typically lines or triangles.</span></span> <span data-ttu-id="19066-106">在下列範例中，開盤值以左方的標記顯示，而收盤值以右方的標記顯示。</span><span class="sxs-lookup"><span data-stu-id="19066-106">In the following example, the opening values are shown by the markers on the left, and the closing values are shown by the markers on the right.</span></span>  
  
 <span data-ttu-id="19066-107">![股票圖](../media/rs-stockchart.gif "股票圖")</span><span class="sxs-lookup"><span data-stu-id="19066-107">![Stock chart](../media/rs-stockchart.gif "Stock chart")</span></span>  
  
 <span data-ttu-id="19066-108">股票圖表的例子可從範例 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 報表產生器報表取得。</span><span class="sxs-lookup"><span data-stu-id="19066-108">An example of a stock chart is available as a sample [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] Report Builder report.</span></span> <span data-ttu-id="19066-109">如需下載這個範例報表及其他項目的詳細資訊，請參閱 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)][報表產生器與報表設計師範例報表](https://go.microsoft.com/fwlink/?LinkId=198283)：</span><span class="sxs-lookup"><span data-stu-id="19066-109">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="19066-110">變化</span><span class="sxs-lookup"><span data-stu-id="19066-110">Variations</span></span>  
  
-   <span data-ttu-id="19066-111">**K 線圖**：</span><span class="sxs-lookup"><span data-stu-id="19066-111">**Candlestick**.</span></span> <span data-ttu-id="19066-112">K 線圖是一種特殊形式的股票圖，其中的方塊用於顯示開盤值與收盤值之間的範圍。</span><span class="sxs-lookup"><span data-stu-id="19066-112">The candlestick chart is a specialized form of the stock chart, wherein boxes are used to show the range between the open and close values.</span></span> <span data-ttu-id="19066-113">K 線圖就像股票圖一樣，最多可以在每個資料點顯示四個值。</span><span class="sxs-lookup"><span data-stu-id="19066-113">Like the stock chart, the candlestick chart can display up to four values per data point.</span></span>  
  
## <a name="data-considerations-for-stock-charts"></a><span data-ttu-id="19066-114">股票圖的資料考量</span><span class="sxs-lookup"><span data-stu-id="19066-114">Data Considerations for Stock Charts</span></span>  
  
-   <span data-ttu-id="19066-115">顯示多個股票資料點 (例如，年股價趨勢) 時，很難區分每個資料點的每個開盤值、收盤值、最高值與最低值。</span><span class="sxs-lookup"><span data-stu-id="19066-115">When presenting many stock data points, such as annual stock price trend, it is difficult to distinguish each open, close, high and low value of each data point.</span></span> <span data-ttu-id="19066-116">在此狀況下，請考慮使用折線圖而非股票圖。</span><span class="sxs-lookup"><span data-stu-id="19066-116">In this scenario, consider using a line chart instead of a stock chart.</span></span>  
  
-   <span data-ttu-id="19066-117">產生軸標籤時，標記通常會從零開始。</span><span class="sxs-lookup"><span data-stu-id="19066-117">When axis labels are generated, labeling usually begins at zero.</span></span>  <span data-ttu-id="19066-118">一般而言，股價的變動程度與其他資料集的變動程度不同。</span><span class="sxs-lookup"><span data-stu-id="19066-118">In general, stock prices do not fluctuate to the same degree as other data sets.</span></span> <span data-ttu-id="19066-119">因此，您可能想要停用從零開始的軸標籤，才能得到較佳的資料檢視。</span><span class="sxs-lookup"><span data-stu-id="19066-119">For this reason, you may want to disable the axis labels from starting at zero, in order to get a better view of your data.</span></span> <span data-ttu-id="19066-120">若要這樣做，請在 **[軸屬性]** 對話方塊或 [屬性] 視窗中，將 **IncludeZero** 設定為 **false** 。</span><span class="sxs-lookup"><span data-stu-id="19066-120">To do this, set **IncludeZero** to **false** in the **Axis Properties** dialog box or the Properties window.</span></span> <span data-ttu-id="19066-121">如需圖表如何產生軸標籤的詳細資訊，請參閱[格式化圖表上的軸標籤 &#40;報表產生器及 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="19066-121">For more information about how the chart generates axis labels, see [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="19066-122">提供許多計算公式搭配股票圖使用，包括「價格指標」、「相對強弱指標 (Relative Strength Index)」、MACD 等等。</span><span class="sxs-lookup"><span data-stu-id="19066-122">provides many calculated formulas for use with stock charts, including Price Indicator, Relative Strength Index, MACD and more.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19066-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19066-123">See Also</span></span>  
 <span data-ttu-id="19066-124">[&#40;報表產生器和 SSRS 的範圍圖表&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="19066-124">[Range Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="19066-125">[圖表 &#40;報表產生器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="19066-125">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="19066-126">[將圖表格式化 &#40;報表產生器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="19066-126">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="19066-127">軸屬性對話方塊，軸選項 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="19066-127">Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;</span></span>](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md)  
  
  
