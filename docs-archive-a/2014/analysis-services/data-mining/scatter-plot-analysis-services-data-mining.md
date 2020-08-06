---
title: 散佈圖 (Analysis Services-資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- charts [Analysis Services]
- mining models [Analysis Services], validating
- scatter charts
- regression algorithms [Analysis Services]
ms.assetid: 166812ec-fd1c-47c8-88db-d5041142be91
author: minewiskan
ms.author: owend
ms.openlocfilehash: b584be18618e6b046a27e40d0707609c3e02c45c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607152"
---
# <a name="scatter-plot-analysis-services---data-mining"></a><span data-ttu-id="b0e56-102">散佈圖 (Analysis Services - 資料採礦)</span><span class="sxs-lookup"><span data-stu-id="b0e56-102">Scatter Plot (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="b0e56-103">*「散佈圖」* (Scatter Plot) 會針對此模型所預測的值來繪製資料中的實際值。</span><span class="sxs-lookup"><span data-stu-id="b0e56-103">A *scatter plot* graphs the actual values in your data against the values predicted by the model.</span></span> <span data-ttu-id="b0e56-104">散佈圖會沿著 X 軸顯示實際值，並沿著 Y 軸顯示預測值。</span><span class="sxs-lookup"><span data-stu-id="b0e56-104">The scatter plot displays the actual values along the X-axis, and displays the predicted values along the Y-axis.</span></span> <span data-ttu-id="b0e56-105">散佈圖也會顯示一條線來說明完美預測，也就是預測值完全符合實際值的情況。</span><span class="sxs-lookup"><span data-stu-id="b0e56-105">It also displays a line that illustrates the perfect prediction, where the predicted value exactly matches the actual value.</span></span> <span data-ttu-id="b0e56-106">這條理想 45 度線上之點的距離會指示預測執行的成果好壞。</span><span class="sxs-lookup"><span data-stu-id="b0e56-106">The distance of a point from this ideal 45-degree angle line indicates how well or how poorly the prediction performed.</span></span>

## <a name="understanding-the-scatter-plot"></a><span data-ttu-id="b0e56-107">了解散佈圖</span><span class="sxs-lookup"><span data-stu-id="b0e56-107">Understanding the Scatter Plot</span></span>
 <span data-ttu-id="b0e56-108">假設行銷部門中的模型是根據促銷電子郵件中傳送之連結的點選次數來預測每天的銷售。</span><span class="sxs-lookup"><span data-stu-id="b0e56-108">Consider a model in which the marketing department predicts daily sales based on the number of clicks on a link sent in a promotional e-mail.</span></span> <span data-ttu-id="b0e56-109">由於點選次數和銷售數量都是連續的數值，所以您可以將點選次數繪製為獨立變數，並將銷售繪製為相依變數。</span><span class="sxs-lookup"><span data-stu-id="b0e56-109">Because both the number of clicks and the amount of sales are continuous numeric values, you can graph the number of clicks as the independent variable and the sales as the dependent variable.</span></span> <span data-ttu-id="b0e56-110">當您這樣做時，直線會顯示預期的線性關係，而該線周圍散佈的點則會顯示預期值與實際值的差異。</span><span class="sxs-lookup"><span data-stu-id="b0e56-110">When you do so, the straight line shows the expected linear relationship, and the points scattered around that line show how the actual data diverges from the expected.</span></span> <span data-ttu-id="b0e56-111">這項分析可大致告訴您，某一組結果如何與特定輸入產生相互關聯性，以及與理想模型之間的變異有多大。</span><span class="sxs-lookup"><span data-stu-id="b0e56-111">This analysis tells you at a glance how closely a set of results is correlated with a particular input, and how much variation there is from the ideal model</span></span>

## <a name="interpreting-the-results"></a><span data-ttu-id="b0e56-112">解譯結果</span><span class="sxs-lookup"><span data-stu-id="b0e56-112">Interpreting the Results</span></span>
 <span data-ttu-id="b0e56-113">下圖顯示針對剛剛描述的案例所建立的散佈圖範例。</span><span class="sxs-lookup"><span data-stu-id="b0e56-113">The following diagram shows an example of a scatter plot, created for the scenario just described.</span></span>

 <span data-ttu-id="b0e56-114">![線性迴歸散佈圖的範例](../media/scatterplot-callctr.gif "線性迴歸散佈圖的範例")</span><span class="sxs-lookup"><span data-stu-id="b0e56-114">![example of a scatter plot for linear regression](../media/scatterplot-callctr.gif "example of a scatter plot for linear regression")</span></span>

 <span data-ttu-id="b0e56-115">您可以將滑鼠暫停在散佈於此線周圍的任何點上，以檢視工具提示內的預測值和實際值。</span><span class="sxs-lookup"><span data-stu-id="b0e56-115">You can pause the mouse on any point scattered around the line to view the predicted and actual values in a tooltip.</span></span> <span data-ttu-id="b0e56-116">散佈圖沒有 **[採礦圖例]** ；但是，該圖本身會包含一個圖例來顯示與此模型有關的分數。</span><span class="sxs-lookup"><span data-stu-id="b0e56-116">There is no **Mining Legend** for a scatter plot; however, the chart itself contains a legend that displays the score associated with the model.</span></span> <span data-ttu-id="b0e56-117">如需解譯分數的詳細資訊，請參閱[線性迴歸模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="b0e56-117">For more information about interpreting the score, see [Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md).</span></span>

 <span data-ttu-id="b0e56-118">您可以將圖表的視覺表示法複製到剪貼簿，但不是基礎資料或公式。</span><span class="sxs-lookup"><span data-stu-id="b0e56-118">You can copy the visual representation of the chart to the Clipboard, but not the underlying data or the formula.</span></span> <span data-ttu-id="b0e56-119">如果您想要檢視這條線的迴歸公式，您可以針對此模型建立內容查詢。</span><span class="sxs-lookup"><span data-stu-id="b0e56-119">If you want to view the regression formula for the line, you can create a content query against the model.</span></span> <span data-ttu-id="b0e56-120">如需詳細資訊，請參閱 [線性迴歸模型查詢範例](linear-regression-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="b0e56-120">For more information, see [Linear Regression Model Query Examples](linear-regression-model-query-examples.md).</span></span>

## <a name="restrictions-on-scatter-plots"></a><span data-ttu-id="b0e56-121">散佈圖的限制</span><span class="sxs-lookup"><span data-stu-id="b0e56-121">Restrictions on Scatter Plots</span></span>
 <span data-ttu-id="b0e56-122">只有當您在 **[輸入選擇]** 索引標籤上選擇的模型包含連續可預測屬性時，才會建立散佈圖。</span><span class="sxs-lookup"><span data-stu-id="b0e56-122">A scatter plot can only be created if the model that you choose on the **Input Selection** tab contains a continuous predictable attribute.</span></span> <span data-ttu-id="b0e56-123">您不必進行任何其他選擇；散佈圖圖表類型會自動顯示在以模型和屬性類型為根據的 **[增益圖]** 索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="b0e56-123">You do not have to make any additional selections; the scatter plot chart type is automatically displayed in the **Lift Chart** tab based on model and attribute type.</span></span>

 <span data-ttu-id="b0e56-124">雖然時間序列模型會預測連續數字，但是您無法使用散佈圖來測量時間序列模型的精確度。</span><span class="sxs-lookup"><span data-stu-id="b0e56-124">Although time series models predict continuous numbers, you cannot measure the accuracy of a time series model by using a scatter plot.</span></span> <span data-ttu-id="b0e56-125">您可以使用其他方法，例如保留歷程記錄資料的一部分。</span><span class="sxs-lookup"><span data-stu-id="b0e56-125">There are other methods that you can use, such as reserving a portion of the historical data.</span></span> <span data-ttu-id="b0e56-126">如需詳細資訊，請參閱[時間序列模型查詢範例](time-series-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="b0e56-126">For more information, see [Time Series Model Query Examples](time-series-model-query-examples.md).</span></span>

## <a name="related-content"></a><span data-ttu-id="b0e56-127">相關內容</span><span class="sxs-lookup"><span data-stu-id="b0e56-127">Related Content</span></span>
 <span data-ttu-id="b0e56-128">下列主題包含有關如何建立及使用散佈圖與相關精確度圖表的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="b0e56-128">The following topics contain more information about how you can build and use scatter plots and related accuracy charts.</span></span>

|<span data-ttu-id="b0e56-129">主題</span><span class="sxs-lookup"><span data-stu-id="b0e56-129">Topics</span></span>|<span data-ttu-id="b0e56-130">連結</span><span class="sxs-lookup"><span data-stu-id="b0e56-130">Links</span></span>|
|------------|-----------|
|<span data-ttu-id="b0e56-131">提供如何為此目標郵寄模型建立增益圖的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="b0e56-131">Provides a walkthrough of how to create a lift chart for the Targeted Mailing model.</span></span>|[<span data-ttu-id="b0e56-132">資料採礦基本教學課程</span><span class="sxs-lookup"><span data-stu-id="b0e56-132">Basic Data Mining Tutorial</span></span>](../../tutorials/basic-data-mining-tutorial.md)<br /><br /> [<span data-ttu-id="b0e56-133">使用增益圖測試精確度 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="b0e56-133">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)|
|<span data-ttu-id="b0e56-134">說明相關的圖表類型。</span><span class="sxs-lookup"><span data-stu-id="b0e56-134">Explains related chart types.</span></span>|[<span data-ttu-id="b0e56-135">增益圖 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="b0e56-135">Lift Chart &#40;Analysis Services - Data Mining&#41;</span></span>](lift-chart-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="b0e56-136">收益圖 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="b0e56-136">Profit Chart &#40;Analysis Services - Data Mining&#41;</span></span>](profit-chart-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="b0e56-137">分類矩陣 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="b0e56-137">Classification Matrix &#40;Analysis Services - Data Mining&#41;</span></span>](classification-matrix-analysis-services-data-mining.md)|
|<span data-ttu-id="b0e56-138">描述採礦模型和採礦結構的交叉驗證用法。</span><span class="sxs-lookup"><span data-stu-id="b0e56-138">Describes uses of cross-validation for mining models and mining structures.</span></span>|[<span data-ttu-id="b0e56-139">交叉驗證 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="b0e56-139">Cross-Validation &#40;Analysis Services - Data Mining&#41;</span></span>](cross-validation-analysis-services-data-mining.md)|
|<span data-ttu-id="b0e56-140">描述建立增益圖及其他精確度圖表的步驟。</span><span class="sxs-lookup"><span data-stu-id="b0e56-140">Describes steps for creating lift charts and other accuracy charts.</span></span>|[<span data-ttu-id="b0e56-141">測試及驗證工作與操作方法 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="b0e56-141">Testing and Validation Tasks and How-tos &#40;Data Mining&#41;</span></span>](testing-and-validation-tasks-and-how-tos-data-mining.md)|

## <a name="see-also"></a><span data-ttu-id="b0e56-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0e56-142">See Also</span></span>
 [<span data-ttu-id="b0e56-143">測試及驗證 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="b0e56-143">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)


