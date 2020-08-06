---
title: 流覽預測模型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- forecasting [data mining]
- mining models, viewing
- mining model, time series
- time series [data mining]
ms.assetid: ad35a528-1949-4048-8678-3b9760c1c88c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7d0b188c4ed6fba9bc5b1082725b17c99081c1b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593115"
---
# <a name="browsing-a-forecasting-model"></a><span data-ttu-id="e3f1d-102">瀏覽預測模型</span><span class="sxs-lookup"><span data-stu-id="e3f1d-102">Browsing a Forecasting Model</span></span>
  <span data-ttu-id="e3f1d-103">當您使用 **[流覽]** 來開啟預測模型時，該模型會顯示在互動式檢視器中，類似于中的時間序列模型檢視器 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-103">When you open a forecasting model using **Browse**, the model is displayed in an interactive viewer, similar to the time series model viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="e3f1d-104">此檢視器可協助您探索趨勢、比較序列、建立預測，以及取得有關模型和基礎資料的資訊。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-104">The viewer helps you explore trends, compare series, create predictions, and get information about the model and the underlying data.</span></span>  
  
##  <a name="explore-the-model"></a><a name="bkmk_Top"></a><span data-ttu-id="e3f1d-105">探索模型</span><span class="sxs-lookup"><span data-stu-id="e3f1d-105">Explore the Model</span></span>  
 <span data-ttu-id="e3f1d-106">適用于預測模型的**流覽**檢視器提供了圖表視圖，它會顯示一段時間的趨勢，並可讓您建立預測和模型視圖，將時間序列表示為決策樹或迴歸樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-106">The **Browse** viewer for forecasting models provides a chart view, which shows the trends over time and lets you create predictions, and a model view, which represents the time series as a decision tree or a regression tree.</span></span>  
  
-   [<span data-ttu-id="e3f1d-107">圖表檢視</span><span class="sxs-lookup"><span data-stu-id="e3f1d-107">Chart view</span></span>](#bkmk_charts)  
  
-   <span data-ttu-id="e3f1d-108">[[模型] 檢視](#bkmk_Model)</span><span class="sxs-lookup"><span data-stu-id="e3f1d-108">[Model view](#bkmk_Model)</span></span>  
  
 <span data-ttu-id="e3f1d-109">若要試驗預測模型，您可以使用範例資料活頁簿之 [預測] 索引標籤上的範例資料，並使用 [預測] Wizard 建立時間序列模型 &#40;[**資料採礦**] 功能區中的 [[適用于 Excel 的資料採礦增益集]&#41;](forecast-wizard-data-mining-add-ins-for-excel.md) ，或在 [**分析**] 功能區中[預測適用于 excel&#41;的 &#40;資料表分析工具](forecast-table-analysis-tools-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-109">To experiment with a forecasting model, you can use the sample data on the Forecast tab of the sample data workbook, and build a time series model using the [Forecast Wizard &#40;Data Mining Add-ins for Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md) in the **Data Mining** ribbon, or [Forecast &#40;Table Analysis Tools for Excel&#41;](forecast-table-analysis-tools-for-excel.md) in the **Analyze** ribbon.</span></span>  
  
###  <a name="chart"></a><a name="bkmk_charts"></a><span data-ttu-id="e3f1d-110">圖</span><span class="sxs-lookup"><span data-stu-id="e3f1d-110">Chart</span></span>  
 <span data-ttu-id="e3f1d-111">[**圖表**] 索引標籤會顯示一段時間內資料數列的趨勢，以及預測的值。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-111">The **Chart** tab displays the trend in your data series over time, together with the predicted values.</span></span> <span data-ttu-id="e3f1d-112">圖表的垂直軸代表序列的值，而水平軸代表時間。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-112">The vertical axis of the chart represents the values of the series, and the horizontal axis represents time.</span></span>  
  
##### <a name="explore-the-forecasting-chart"></a><span data-ttu-id="e3f1d-113">探索預測圖表</span><span class="sxs-lookup"><span data-stu-id="e3f1d-113">Explore the forecasting chart</span></span>  
  
1.  <span data-ttu-id="e3f1d-114">此模型包含多個時間序列，不過為了簡化圖表，您可以顯示一個序列，或只顯示幾個相關序列。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-114">This model contains multiple time series, but to simplify the chart, you can display a single series, or just a few related series.</span></span>  
  
     <span data-ttu-id="e3f1d-115">![預測模型中的歷程記錄預測](media/dm13-forecast-chart-historicpredictions.gif "預測模型中的歷程記錄預測")</span><span class="sxs-lookup"><span data-stu-id="e3f1d-115">![historical predictions in the forecasting model](media/dm13-forecast-chart-historicpredictions.gif "historical predictions in the forecasting model")</span></span>  
  
     <span data-ttu-id="e3f1d-116">使用核取方塊只選取北美洲的銷售量預測。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-116">Use the check boxes to select the forecast for just North America, and just for sales Amount.</span></span>  
  
2.  <span data-ttu-id="e3f1d-117">按一下 [**預測步驟**] 並輸入新的值，以控制您想要在圖表中看到多少未來時間值。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-117">Click **Prediction Steps** and type a new value to control how many future time values you want to see in the chart.</span></span>  
  
     <span data-ttu-id="e3f1d-118">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-118">The default is 5.</span></span>  
  
3.  <span data-ttu-id="e3f1d-119">按一下 [歷程記錄] 或 [未來] 這一行中的任何一點，以查看該時間點的確切值（顯示在 [**挖掘圖例**] 中）。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-119">Click any point in the line, either historical or future, to see the exact values for that point in time, displayed in the **Mining Legend**.</span></span>  
  
4.  <span data-ttu-id="e3f1d-120">圖表會顯示記錄資料和未來的資料。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-120">The chart displays both historical and future data.</span></span> <span data-ttu-id="e3f1d-121">注意套用陰影效果背景的虛線。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-121">Note the dotted line, with a shaded background.</span></span> <span data-ttu-id="e3f1d-122">這些值是根據模型的未來預測。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-122">These values are the future predictions, based on the model.</span></span>  
  
     <span data-ttu-id="e3f1d-123">圖表左側顯示用來建立模型的記錄資料。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-123">The historical data (which you used to build the model) is shown in the left side of the chart.</span></span>  
  
5.  <span data-ttu-id="e3f1d-124">選取 [**顯示歷史預測**] 選項，以瞭解時間序列的穩定性。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-124">Select the **Show historic predictions** option to get a sense for the stability of the time series.</span></span>  
  
     <span data-ttu-id="e3f1d-125">![模型中單一數列的預測](media/dm13-forecast-chart-singleseries.gif "模型中單一數列的預測")</span><span class="sxs-lookup"><span data-stu-id="e3f1d-125">![forecasts for a single series in the model](media/dm13-forecast-chart-singleseries.gif "forecasts for a single series in the model")</span></span>  
  
     <span data-ttu-id="e3f1d-126">記錄預測是根據該點的序列所預測的值，會與實際記錄值進行比較。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-126">Historical predictions are values predicted based on the series to that point, which are compared to actual historical values.</span></span> <span data-ttu-id="e3f1d-127">如果虛線 (預測值) 與實心線條 (實際值) 相差很多，表示序列的第一部分可能無法正確地預測稍後的值。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-127">If the dotted line (with the predicted values) is far apart from the solid line (the actual values), it means the first part of the series perhaps does not accurately predict the later values.</span></span> <span data-ttu-id="e3f1d-128">您可能需要更多資料，這也可能只是指出循環的變動性。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-128">You might need more data, or it might simply be an indicator of volatility in the cycle.</span></span>  
  
6.  <span data-ttu-id="e3f1d-129">選取 [**顯示偏差**] 選項，以在圖表中顯示誤差線。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-129">Select the **Show Deviations** option to display error bars in the chart.</span></span>  
  
     <span data-ttu-id="e3f1d-130">誤差線可讓您以視覺化方式評估預測的變化性。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-130">The error bars let you visually assess the variability of the predictions.</span></span> <span data-ttu-id="e3f1d-131">預測的品質視您的來源資料而有所不同，但是隨著您增加預測步驟的數目，您應該會看到偏差穩定地增加。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-131">The quality of predictions varies depending on your source data, but as you increase the number of prediction steps, you should see the deviations steadily increase.</span></span>  
  
 <span data-ttu-id="e3f1d-132">**提示**</span><span class="sxs-lookup"><span data-stu-id="e3f1d-132">**Tips**</span></span>  
  
-   <span data-ttu-id="e3f1d-133">若要切換 [**挖掘圖例**] 的顯示，請以滑鼠右鍵按一下圖表中的任一點。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-133">To toggle display of the **Mining Legend**, right-click any point in the chart.</span></span>  
  
     <span data-ttu-id="e3f1d-134">您可以按一下圖表，在圖表上拖曳時間選取範圍，然後再按一下圖表在選取的範圍上放大，以檢視特定的時間範圍。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-134">You can view a specific time range by clicking the chart, dragging a time selection across the chart, and then clicking again to zoom in on the selected range.</span></span>  
  
-   <span data-ttu-id="e3f1d-135">若要取得目前圖表的複本，請按一下 [**複製到 excel**]，然後按一下 excel 中的工作表。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-135">To get a copy of the current chart, click **Copy to Excel**, then click a worksheet in Excel.</span></span> <span data-ttu-id="e3f1d-136">即會使用您已設定的所有選項 (包括圖例) 將圖表插入工作表。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-136">A graphic is inserted in the sheet using all the options you had set, including a legend.</span></span>  
  
     <span data-ttu-id="e3f1d-137">不過，此圖形是靜態的，因此您無法編輯圖例或查看基礎資料。如果您需要更互動式的圖表視圖，請使用[Visio viewer](viewing-data-mining-models-in-visio-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-137">However, this graphic is static so you cannot edit the legend or view the underlying data; if you need a more interactive chart view, use the [Visio viewers](viewing-data-mining-models-in-visio-data-mining-add-ins.md).</span></span>  
  
-   <span data-ttu-id="e3f1d-138">按一下檢視器功能表列中的 [ **Abs** ]，在絕對與相對曲線之間切換。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-138">Click **Abs** in the viewer menu bar to toggle between absolute and relative curves.</span></span>  
  
     <span data-ttu-id="e3f1d-139">如果圖表包含多個模型，但每一個模型的資料比例差異很大，則此選項會很有用。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-139">This option is useful if your chart contains multiple models, but the scale of the data for each model is very different.</span></span>  
  
     <span data-ttu-id="e3f1d-140">例如，如果太平洋地區商店是新開的商店但銷售量很低，此時若使用絕對值，顯示太平洋地區銷售量的線條可能會很扁平，而難以查看實際變更，至於其他模型則以較為正常的比例顯示。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-140">For example, if the Pacific region stores were new and sales were low, and if absolute values are used, the line showing Pacific sales might appear flat, making it difficult to see actual changes, whereas the other models would be displayed at a more normal scale.</span></span>  
  
     <span data-ttu-id="e3f1d-141">藉由將檢視切換為使用相對值，您可以標準化不同模型的比例，並將差異顯示為變動百分比。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-141">By switching the view to use relative values, you can normalize the scale of different models, and display differences as a percent of change.</span></span> <span data-ttu-id="e3f1d-142">當變動與每個模型相關時，則可以在相同的圖表中顯示，而不會大幅失真。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-142">When change is relative to each model, they can be displayed in the same graph without significant distortion.</span></span>  
  
 [<span data-ttu-id="e3f1d-143">探索模型</span><span class="sxs-lookup"><span data-stu-id="e3f1d-143">Explore the Model</span></span>](#bkmk_Top)  
  
###  <a name="model"></a><a name="bkmk_Model"></a><span data-ttu-id="e3f1d-144">模組</span><span class="sxs-lookup"><span data-stu-id="e3f1d-144">Model</span></span>  
 <span data-ttu-id="e3f1d-145">預測模型也可以決策樹來表示，如果序列大部分呈線性，則可以迴歸模型來表示。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-145">A forecasting model can also be represented as a decision tree, or, if the series is mostly linear, a regression model.</span></span>  
  
 <span data-ttu-id="e3f1d-146">例如，在此模型中，根據特定條件迴歸公式含有差異，因此會將樹狀結構分成兩個分支，每個分支使用不同的迴歸公式。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-146">For example, in this model, there is a difference in the regression formula based on a certain condition, so the tree splits into two branches, each with a different regression formula.</span></span>  
  
 <span data-ttu-id="e3f1d-147">![在預測模型中篩選單一數列](media/dm13-forecast-model-northamerica.gif "在預測模型中篩選單一數列")</span><span class="sxs-lookup"><span data-stu-id="e3f1d-147">![Filter single series in the forecasting model](media/dm13-forecast-model-northamerica.gif "Filter single series in the forecasting model")</span></span>  
  
##### <a name="explore-the-forecasting-model-as-a-tree"></a><span data-ttu-id="e3f1d-148">探索樹狀結構的預測模型</span><span class="sxs-lookup"><span data-stu-id="e3f1d-148">Explore the forecasting model as a tree</span></span>  
  
1.  <span data-ttu-id="e3f1d-149">按一下 [**樹狀**] 下拉式清單，然後選擇要顯示的模型。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-149">Click the **Tree** dropdown list and choose a model to display.</span></span>  
  
     <span data-ttu-id="e3f1d-150">每個可預測的屬性會顯示不同的樹狀結構或迴歸節點。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-150">A separate tree or regression node is displayed for each predictable attribute.</span></span> <span data-ttu-id="e3f1d-151">例如，如果您的資料包含歐洲、北美洲和太平洋地區的銷售量，則會有三個模型，每個模型各代表一個資料數列。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-151">For example, if your data contains sales for Europe, North America, and the Pacific, there would three different models, one for each data series.</span></span>  
  
2.  <span data-ttu-id="e3f1d-152">拖曳 [**顯示層級**] 滑杆以篩選出較低層級的樹狀結構，並將焦點放在最重要的分割上。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-152">Drag the **Show Level** slider to filter out lower levels of the tree, and focus on the most important splits.</span></span>  
  
3.  <span data-ttu-id="e3f1d-153">按一下每個節點，即可在 [**挖掘圖例**] 中查看一些描述性統計資料。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-153">Click each node to view some descriptive statistics in the **Mining Legend**.</span></span>  
  
     <span data-ttu-id="e3f1d-154">當您將滑鼠暫停在某個節點上方時，[工具提示] 也會顯示相同的統計資料，以及描述該節點的完整公式。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-154">As you pause over a node with the mouse, a ToolTip also displays the same statistics, as well as the full formula describing that node.</span></span>  
  
4.  <span data-ttu-id="e3f1d-155">如果您想要複製 [**挖掘圖例**] 中的資訊，請以滑鼠右鍵按一下 [**挖掘圖例**]，選取 [**複製**]，然後在您的 Excel 工作表內按一下。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-155">If you want to copy the information in the **Mining Legend**, right-click the **Mining Legend**, select **Copy**, and click inside your Excel worksheet.</span></span> <span data-ttu-id="e3f1d-156">[**複製到 Excel** ] 選項會複製圖形，而不是統計資料。</span><span class="sxs-lookup"><span data-stu-id="e3f1d-156">The **Copy to Excel** option copies the graph, not the statistics.</span></span>  
  
 [<span data-ttu-id="e3f1d-157">探索模型</span><span class="sxs-lookup"><span data-stu-id="e3f1d-157">Explore the Model</span></span>](#bkmk_Top)  
  
## <a name="see-also"></a><span data-ttu-id="e3f1d-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3f1d-158">See Also</span></span>  
 [<span data-ttu-id="e3f1d-159">在 Excel 中流覽模型 &#40;SQL Server 資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="e3f1d-159">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
