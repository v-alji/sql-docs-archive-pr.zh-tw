---
title: " (中繼資料採礦教學課程) 探索預測模型 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0a00f409-050f-4b92-9763-ba31a6aa3052
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 86bd6371a8d32c53c68351aaff36a317f7433ef0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704474"
---
# <a name="exploring-the-forecasting-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="bb560-102">探索預測模型 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="bb560-102">Exploring the Forecasting Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="bb560-103">現在您已建立預測採礦模型，您可以使用資料採礦設計師的 [**採礦模型檢視器**] 索引標籤來探索結果。</span><span class="sxs-lookup"><span data-stu-id="bb560-103">Now that you have built the forecasting mining model, you can explore the results by using the **Mining Model Viewer** tab of Data Mining Designer.</span></span> <span data-ttu-id="bb560-104">[!INCLUDE[msCoName](../includes/msconame-md.md)]時間序列檢視器包含兩個索引標籤： [**圖表**] 和 [**模型**]。</span><span class="sxs-lookup"><span data-stu-id="bb560-104">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series Viewer contains two tabs: **Charts** and **Model**.</span></span>  
  
 <span data-ttu-id="bb560-105">此外，您可以對所有模型使用 Microsoft 一般內容樹狀檢視器。</span><span class="sxs-lookup"><span data-stu-id="bb560-105">Additionally, you can use the Microsoft Generic Tree Viewer with all models.</span></span> <span data-ttu-id="bb560-106">每個檢視針對時間序列模型中的資訊呈現略為不同的面貌。</span><span class="sxs-lookup"><span data-stu-id="bb560-106">Each view presents a slightly different picture of the information in the time series model.</span></span>  
  
-   [<span data-ttu-id="bb560-107">圖表索引標籤</span><span class="sxs-lookup"><span data-stu-id="bb560-107">Charts Tab</span></span>](#bkmk_Charts)  
  
-   [<span data-ttu-id="bb560-108">模型索引標籤</span><span class="sxs-lookup"><span data-stu-id="bb560-108">Model Tab</span></span>](#bkmk_Model)  
  
-   [<span data-ttu-id="bb560-109">Microsoft 一般內容樹狀檢視器</span><span class="sxs-lookup"><span data-stu-id="bb560-109">Microsoft Generic Content Viewer</span></span>](#bkmk_Content)  
  
##  <a name="charts-tab"></a><a name="bkmk_Charts"></a><span data-ttu-id="bb560-110">圖表索引標籤</span><span class="sxs-lookup"><span data-stu-id="bb560-110">Charts Tab</span></span>  
 <span data-ttu-id="bb560-111">時間序列檢視器的 [**圖表**] 索引標籤 [!INCLUDE[msCoName](../includes/msconame-md.md)] 會以圖形方式顯示每個數列，包括歷程記錄資料和預測。</span><span class="sxs-lookup"><span data-stu-id="bb560-111">The **Charts** tab of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series Viewer graphically shows you each of the series, including historical data and predictions.</span></span> <span data-ttu-id="bb560-112">時間序列圖形中的每個線條代表由產品、區域和可預測屬性構成的唯一組合。</span><span class="sxs-lookup"><span data-stu-id="bb560-112">Each line in the time series graph represents a unique combination of product, region, and predictable attribute.</span></span>  
  
 <span data-ttu-id="bb560-113">檢視器右側的圖例會根據下拉式清單中的選取項目列出時間序列。</span><span class="sxs-lookup"><span data-stu-id="bb560-113">The legend on the right side of the viewer lists the time series that available, based on the selections in the drop-down list.</span></span> <span data-ttu-id="bb560-114">您可以選取和清除圖例中的核取方塊，來控制圖形中所顯示的時間序列。</span><span class="sxs-lookup"><span data-stu-id="bb560-114">You can select and clear the check boxes in the legend to control which time series displays in the graph.</span></span>  
  
 <span data-ttu-id="bb560-115">您也可以變更顯示選項，例如各時間序列所用的色彩，或值是否顯示在圖表中的資料點。</span><span class="sxs-lookup"><span data-stu-id="bb560-115">You can also change the display options, such as the colors used for each time series, or whether values are displayed at points in the chart.</span></span>  
  
#### <a name="to-select-a-time-series"></a><span data-ttu-id="bb560-116">若要選取時間序列</span><span class="sxs-lookup"><span data-stu-id="bb560-116">To select a time series</span></span>  
  
1.  <span data-ttu-id="bb560-117">如果看不到，請按一下 [**採礦模型檢視器**] 索引標籤的 [**圖表**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="bb560-117">Click the **Charts** tab of the **Mining Model Viewer** tab, if it is not visible.</span></span>  
  
2.  <span data-ttu-id="bb560-118">按一下圖表檢視右側的下拉式清單，選取所有核取方塊。</span><span class="sxs-lookup"><span data-stu-id="bb560-118">Click the drop-down list to the right of the chart view, and select all the check boxes.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="bb560-119">圖表現在應包含 24 個不同的序列線條。</span><span class="sxs-lookup"><span data-stu-id="bb560-119">The chart should now contain 24 different series lines.</span></span>  
  
3.  <span data-ttu-id="bb560-120">在圖表右側的核取方塊中，清除所有有關 [金額] 的方塊，以便暫時隱藏以金額為基礎的所有序列線條。</span><span class="sxs-lookup"><span data-stu-id="bb560-120">In the check boxes to the right of the chart, clear the boxes to temporarily hide the lines for all series that are based on Amount.</span></span>  
  
     <span data-ttu-id="bb560-121">接著，清除與 R750 和 R250 自行車有關的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="bb560-121">Now, clear the check boxes related to the R750 and R250 bicycles.</span></span>  
  
     <span data-ttu-id="bb560-122">此圖表現在只包含下列六個序列線條，方便您比較 M200 和 T1000 自行車的趨勢。</span><span class="sxs-lookup"><span data-stu-id="bb560-122">The chart now contains just the following six series lines, so that can you more easily compare trends for the M200 and T1000 bicycles.</span></span>  
  
    -   <span data-ttu-id="bb560-123">**M200 Europe: Quantity**</span><span class="sxs-lookup"><span data-stu-id="bb560-123">**M200 Europe: Quantity**</span></span>  
  
    -   <span data-ttu-id="bb560-124">**M200 North America: Quantity**</span><span class="sxs-lookup"><span data-stu-id="bb560-124">**M200 North America: Quantity**</span></span>  
  
    -   <span data-ttu-id="bb560-125">**M200 Pacific: Quantity**</span><span class="sxs-lookup"><span data-stu-id="bb560-125">**M200 Pacific: Quantity**</span></span>  
  
    -   <span data-ttu-id="bb560-126">**T1000 Europe: Quantity**</span><span class="sxs-lookup"><span data-stu-id="bb560-126">**T1000 Europe: Quantity**</span></span>  
  
    -   <span data-ttu-id="bb560-127">**T1000 North America: Quantity**</span><span class="sxs-lookup"><span data-stu-id="bb560-127">**T1000 North America: Quantity**</span></span>  
  
    -   <span data-ttu-id="bb560-128">**T1000 Pacific: Quantity**</span><span class="sxs-lookup"><span data-stu-id="bb560-128">**T1000 Pacific: Quantity**</span></span>  
  
 <span data-ttu-id="bb560-129">![序列預測 M200 與 T1000 數量](../../2014/tutorials/media/6series-defaultforecasting.gif "序列預測 M200 與 T1000 數量")</span><span class="sxs-lookup"><span data-stu-id="bb560-129">![Series predicting M200 and T1000 quantity](../../2014/tutorials/media/6series-defaultforecasting.gif "Series predicting M200 and T1000 quantity")</span></span>  
  
 <span data-ttu-id="bb560-130">此檢視器中顯示的圖表會包含歷程記錄資料和預測的資料。</span><span class="sxs-lookup"><span data-stu-id="bb560-130">The chart that is displayed in this viewer includes both historical and predicted data.</span></span> <span data-ttu-id="bb560-131">預測的資料會加上陰影，以便和歷程記錄資料有所區別。</span><span class="sxs-lookup"><span data-stu-id="bb560-131">Predicted data is shaded to differentiate it from historical data.</span></span> <span data-ttu-id="bb560-132">若要更輕鬆地比較不同序列，您也可以變更圖表中各線條的色彩。</span><span class="sxs-lookup"><span data-stu-id="bb560-132">To make it easier to compare different series, you can also change the colors associated with each line in the graph.</span></span> <span data-ttu-id="bb560-133">如需詳細資訊，請參閱 [變更資料採礦檢視器中使用的色彩](../../2014/analysis-services/data-mining/change-the-colors-used-in-the-data-mining-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="bb560-133">For more information, see [Change the Colors Used in the Data Mining Viewer](../../2014/analysis-services/data-mining/change-the-colors-used-in-the-data-mining-viewer.md).</span></span>  
  
 <span data-ttu-id="bb560-134">從趨勢線，可以看到所有區域的總銷售量整體都在增加，且每 12 個月會有一個出現在 12 月的高峰。</span><span class="sxs-lookup"><span data-stu-id="bb560-134">From the trend lines, you can see that total sales for all regions are generally increasing, with a peak every 12 months in December.</span></span> <span data-ttu-id="bb560-135">此外，您還可以從圖表中看出 T1000 自行車資料的開始時間，比其他產品序列資料晚的多。</span><span class="sxs-lookup"><span data-stu-id="bb560-135">From the chart, you can also see that the data for the T1000 bicycle starts much later than the data for the other product series.</span></span> <span data-ttu-id="bb560-136">因為它是新產品，但此序列是以較少的資料為基礎，因此預測可能不準確。</span><span class="sxs-lookup"><span data-stu-id="bb560-136">That is because it is a newer product, but because this series is based on much less data, the predictions might not be as accurate.</span></span>  
  
 <span data-ttu-id="bb560-137">根據預設，每個時間序列 (以點線表示) 顯示五個預測步驟。</span><span class="sxs-lookup"><span data-stu-id="bb560-137">By default, five prediction steps are shown for each time series, displayed as dotted lines.</span></span> <span data-ttu-id="bb560-138">您可以變更這個值，檢視更多或更少的預測。</span><span class="sxs-lookup"><span data-stu-id="bb560-138">You can change this value to view more or fewer predictions.</span></span> <span data-ttu-id="bb560-139">您也可以在圖表中加入誤差線，以圖形方式檢視預測的標準差。</span><span class="sxs-lookup"><span data-stu-id="bb560-139">You can also graphically view the standard deviation for the predictions by adding error bars to the chart.</span></span>  
  
#### <a name="to-change-prediction-and-display-options-in-the-chart-view"></a><span data-ttu-id="bb560-140">變更圖表檢視中的預測和顯示選項</span><span class="sxs-lookup"><span data-stu-id="bb560-140">To change prediction and display options in the Chart view</span></span>  
  
1.  <span data-ttu-id="bb560-141">請嘗試逐漸變更**預測步驟**的值，將它從**5**增加為**10**，然後再轉換回**6**。</span><span class="sxs-lookup"><span data-stu-id="bb560-141">Try changing the value for **Prediction Steps** gradually, increasing it from **5** to **10**, and then back to **6**.</span></span>  
  
     <span data-ttu-id="bb560-142">當歷程記錄資料中有大幅波動時，其波動通常會隨著預測數目增加而重複或甚至幅度加大。</span><span class="sxs-lookup"><span data-stu-id="bb560-142">When the historical data has large fluctuations, the fluctuations tend to be repeated or even amplified as you increase the number of predictions.</span></span> <span data-ttu-id="bb560-143">這時您可能需要探究歷程記錄資料中暴增的原因，然後決定是要接受這些結果、尋求來源資料中的某種更正，還是在模型中套用某種平滑效果。</span><span class="sxs-lookup"><span data-stu-id="bb560-143">You probably need to do some research at this point, to understand the cause of the big increase in the historical data and then decide whether to accept these results, seek some kind of correction in the source data, or apply some kind of smoothing in the model.</span></span>  
  
2.  <span data-ttu-id="bb560-144">選取 [**顯示偏差**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="bb560-144">Select the **Show Deviations** check box.</span></span>  
  
     <span data-ttu-id="bb560-145">此選項會顯示每個預測值的預估錯誤。</span><span class="sxs-lookup"><span data-stu-id="bb560-145">This option displays the estimated error for each predicted value.</span></span>  
  
3.  <span data-ttu-id="bb560-146">請注意 X 軸的小數位數。</span><span class="sxs-lookup"><span data-stu-id="bb560-146">Note the scale of the X-axis.</span></span> <span data-ttu-id="bb560-147">歷程記錄和預測資料的變更永遠是以百分比表示，但實際值會自動調整，以便將所有值放在圖形上。</span><span class="sxs-lookup"><span data-stu-id="bb560-147">The changes over both historical and predicted data are always expressed as a percentage, but the actual values are adjusted automatically to fit all values onto the graph.</span></span> <span data-ttu-id="bb560-148">因此，在比較模型時需要特別小心，不要只依賴視覺項目。</span><span class="sxs-lookup"><span data-stu-id="bb560-148">Therefore you need to be careful when comparing models to not rely on visuals alone.</span></span> <span data-ttu-id="bb560-149">若要取得確切的值，或預測的增加百分比和值，請將滑鼠停留在虛線或實線，或按一下線條以查看 [**挖掘圖例**] 中的值。</span><span class="sxs-lookup"><span data-stu-id="bb560-149">To get the exact value, or the percentage increase and value for predictions, pause the mouse over the dotted line or solid lines, or click the lines to view the values in the **Mining Legend**.</span></span>  
  
     <span data-ttu-id="bb560-150">**提示**：如果看不到 [**挖掘圖例**]，請切換至 [**模型**視圖]，以滑鼠右鍵按一下任何節點，然後選取 [**顯示圖例**]。</span><span class="sxs-lookup"><span data-stu-id="bb560-150">**Tip**: If the **Mining Legend** is not visible, switch to **Model** view, right-click any node, and select **Show Legend**.</span></span>  
  
 <span data-ttu-id="bb560-151">檢視這些趨勢後，您關切某些序列缺少資料，想知道是否可根據模型或地區計算平均銷售量，取得更可靠的預測。</span><span class="sxs-lookup"><span data-stu-id="bb560-151">From looking at these trends, you are concerned about the lack of data for some of the series, and wonder if you might get more reliable predictions by averaging sales by model, or perhaps averaging sales by region.</span></span> <span data-ttu-id="bb560-152">稍後在本教學課程中將探索此方法。</span><span class="sxs-lookup"><span data-stu-id="bb560-152">You will explore this approach in a later lesson in this tutorial.</span></span>  
  
 [<span data-ttu-id="bb560-153">回到頁首</span><span class="sxs-lookup"><span data-stu-id="bb560-153">Back to Top</span></span>](#bkmk_Charts)  
  
##  <a name="model-tab"></a><a name="bkmk_Model"></a><span data-ttu-id="bb560-154">模型索引標籤</span><span class="sxs-lookup"><span data-stu-id="bb560-154">Model Tab</span></span>  
 <span data-ttu-id="bb560-155">[資料採礦設計師] 中的時間序列檢視器的 [**模型**] 索引標籤 [!INCLUDE[msCoName](../includes/msconame-md.md)] 可讓您以樹狀結構圖表的形式來查看預測模型。</span><span class="sxs-lookup"><span data-stu-id="bb560-155">The **Model** tab of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series Viewer in Data Mining Designer lets you view the forecasting model in the form of a tree graph.</span></span>  
  
 <span data-ttu-id="bb560-156">首先，請注意，因為資料針對三個不同區域 (Europe、North America 和 Pacific) 中多個產品線 (T1000 等等) 的銷售描述兩個不同的量值 (Amount 和 Quantity)，所以建立的模型實際上包含 24 個不同的樹狀目錄，每個樹狀目錄代表不同區域、產品和可預測屬性之組合的銷售模式模型。</span><span class="sxs-lookup"><span data-stu-id="bb560-156">First, notice that because your data describes two different measures (Amount and Quantity) for sales of multiple product lines (T1000, etc.) in three different regions (Europe, North America, and Pacific), the model that you built actually contains 24 different trees, each tree representing a model of the sales patterns for a different combination of region, product, and predictable attribute.</span></span>  
  
 <span data-ttu-id="bb560-157">您可以從 [**模型**] 索引標籤上的 [**樹狀**] 下拉式清單中選取數列，以選擇您想要查看的產品線、地區和銷售度量的組合。</span><span class="sxs-lookup"><span data-stu-id="bb560-157">You can choose which combination of product line, region, and sales metric you want to view by selecting a series from the **Tree** dropdown list on the **Model** tab.</span></span>  
  
 <span data-ttu-id="bb560-158">從樹狀檢視的模型中可學到什麼？</span><span class="sxs-lookup"><span data-stu-id="bb560-158">So what can you learn from viewing the model as a tree?</span></span> <span data-ttu-id="bb560-159">例如，讓我們比較兩個模型，一個在樹狀結構中有數個層級，另一個則具有單一節點。</span><span class="sxs-lookup"><span data-stu-id="bb560-159">As an example, let's compare two models, one that has several levels in the tree, and one that has a single node.</span></span>  
  
-   <span data-ttu-id="bb560-160">當樹狀圖形包含單一節點時，這表示模型中的趨勢在一段時間後通常是同質性的。</span><span class="sxs-lookup"><span data-stu-id="bb560-160">When a tree graph contains a single node, it means the trend found in the model is mostly homogenous over time.</span></span> <span data-ttu-id="bb560-161">您可以使用這個單一節點標記為 [**全部**]，以查看描述輸入變數與結果之間關聯性的公式。</span><span class="sxs-lookup"><span data-stu-id="bb560-161">You can use this single node, labeled **All**, to view the formula that describes the relationship between the input variables and the outcome.</span></span>  
  
-   <span data-ttu-id="bb560-162">當時間序列的樹狀圖形有多個分支時，這表示偵測到的時間序列太複雜，無法以單一方程式表示。</span><span class="sxs-lookup"><span data-stu-id="bb560-162">When a tree graph for a time series has multiple branches, it means the time series that was detected is too complex to be represented as a single equation.</span></span> <span data-ttu-id="bb560-163">相反地，樹狀圖表可能包含多個分支，每個分支都標示了導致樹狀結構*分割*的條件。</span><span class="sxs-lookup"><span data-stu-id="bb560-163">Instead, the tree graph might contain multiple branches, each branch labeled with the conditions that caused the tree to *split*.</span></span> <span data-ttu-id="bb560-164">當樹狀目錄分割時，每個分支表示不同的時間區段，其中的趨勢可用單一方程式描述。</span><span class="sxs-lookup"><span data-stu-id="bb560-164">When the tree splits, each branch represents a different segment of time, inside which the trend can be described as a single equation.</span></span>  
  
     <span data-ttu-id="bb560-165">例如，如果您查看圖表圖形，並在9月底開始看到銷售量突然跳躍，並繼續進行年末的假日，您可以切換至**模型**視圖，以查看趨勢變更的確切日期。</span><span class="sxs-lookup"><span data-stu-id="bb560-165">For example, if you look at the chart graph and see a sudden jump in sales volume starting sometime in September and continuing through a year-end holiday, you can switch to the **Model** view to see the exact date where the trend changed.</span></span> <span data-ttu-id="bb560-166">樹狀結構中代表「9月前」和「9月之後」的分支會包含不同的公式：一個公式會以數學方式描述分割的銷售趨勢，另一個公式則描述「年9月」假期的銷售趨勢。</span><span class="sxs-lookup"><span data-stu-id="bb560-166">The branches in the tree that represent "before September" and "after September" would contain different formulas: one formula that mathematically describes the sales trends up to the split, and another formula that describes sales trends for September through the year-end holiday.</span></span>  
  
#### <a name="to-explore-the-decision-tree-for-a-time-series-model"></a><span data-ttu-id="bb560-167">瀏覽時間序列模型的決策樹</span><span class="sxs-lookup"><span data-stu-id="bb560-167">To explore the decision tree for a time series model</span></span>  
  
1.  <span data-ttu-id="bb560-168">在檢視器的 [**模型**] 索引標籤上的 [**樹狀**] 清單中，選取 [ **T1000 歐洲：金額**] 數列。</span><span class="sxs-lookup"><span data-stu-id="bb560-168">In the **Tree** list on the **Model** tab of the viewer, select the **T1000 Europe: Amount** series.</span></span>  
  
     <span data-ttu-id="bb560-169">按一下標示為 [**全部**] 的節點。</span><span class="sxs-lookup"><span data-stu-id="bb560-169">Click the node labeled **All**.</span></span>  
  
     <span data-ttu-id="bb560-170">針對 [ **All** ] 節點，所顯示的工具提示會包含整個數列中的案例數目，以及衍生自資料分析的時間序列方程式等資訊。</span><span class="sxs-lookup"><span data-stu-id="bb560-170">For an **All** node, the ToolTip that appears includes information such as, the number of cases in the entire series, and time series equations derived from analysis of the data.</span></span>  
  
2.  <span data-ttu-id="bb560-171">如果看不到 [**挖掘圖例**]，請以滑鼠右鍵按一下節點，然後選取 [**顯示圖例**]。</span><span class="sxs-lookup"><span data-stu-id="bb560-171">If the **Mining Legend** is not visible, right-click the node and select **Show Legend**.</span></span>  
  
     <span data-ttu-id="bb560-172">[**挖掘圖例**] 提供工具提示中的相同資訊。</span><span class="sxs-lookup"><span data-stu-id="bb560-172">The **Mining Legend** provides much the same information that is in the Tooltip.</span></span> <span data-ttu-id="bb560-173">如果有任何離散的獨立變數，您也會看到顯示變數分佈在節點中的長條圖。</span><span class="sxs-lookup"><span data-stu-id="bb560-173">If any of your independent variables are discrete, you will also see a histogram that shows the distribution of variables in the node.</span></span>  
  
3.  <span data-ttu-id="bb560-174">現在選取另一個要檢視的時間序列。</span><span class="sxs-lookup"><span data-stu-id="bb560-174">Now select a different time series to view.</span></span> <span data-ttu-id="bb560-175">在檢視器的 [**模型**] 索引標籤上，使用**樹狀**清單，選取 [ **M200 北美洲：數量**] 數列。</span><span class="sxs-lookup"><span data-stu-id="bb560-175">Using the **Tree** list on the **Model** tab of the viewer, select the **M200 North America: Amount** series.</span></span>  
  
     <span data-ttu-id="bb560-176">樹狀結構圖形現在包含 [ **All** ] 節點和兩個子節點。</span><span class="sxs-lookup"><span data-stu-id="bb560-176">The tree graph now contains an **All** node and two child nodes.</span></span> <span data-ttu-id="bb560-177">您可以透過查看子節點上的標籤，了解趨勢線在哪個時間點變更。</span><span class="sxs-lookup"><span data-stu-id="bb560-177">By looking at the labels on the child nodes, you can understand at what point the trend line changed.</span></span>  
  
     <span data-ttu-id="bb560-178">針對每個子節點，[**挖掘圖例**] 中的描述也會包含樹狀結構之每個分支中的案例計數。</span><span class="sxs-lookup"><span data-stu-id="bb560-178">For each child node, the description in the **Mining Legend** also includes the count of cases in each branch of the tree.</span></span>  
  
 <span data-ttu-id="bb560-179">下列清單說明樹狀檢視器的一些其他功能：</span><span class="sxs-lookup"><span data-stu-id="bb560-179">The following list describes some additional features in the tree viewer:</span></span>  
  
-   <span data-ttu-id="bb560-180">您可以使用 [**背景**] 控制項來變更圖表中所表示的變數。</span><span class="sxs-lookup"><span data-stu-id="bb560-180">You can change the variable that is represented in the chart by using the **Background** control.</span></span> <span data-ttu-id="bb560-181">根據預設，較暗的節點會包含更多案例，因為**背景**的值會設定為 [擴展 **]。**</span><span class="sxs-lookup"><span data-stu-id="bb560-181">By default, nodes that are darker contain more cases, because the value of **Background** is set to **Population**.</span></span> <span data-ttu-id="bb560-182">若只要查看節點中有多少案例，請將滑鼠停留在節點上，並查看顯示的工具提示，或按一下節點，並在 [**節點圖例**] 視窗中查看數位。</span><span class="sxs-lookup"><span data-stu-id="bb560-182">To see just how many cases there are in a node, pause the mouse over a node and view the ToolTip that appears, or click the node and view the numbers in the **Node Legend** window.</span></span>  
  
-   <span data-ttu-id="bb560-183">也可以在工具提示中或透過按一下節點來檢視節點的迴歸公式。</span><span class="sxs-lookup"><span data-stu-id="bb560-183">The regression formula for the node can also be viewed in the ToolTip, or by clicking the node.</span></span> <span data-ttu-id="bb560-184">如果您建立了混合模型，則會看到兩個公式，一個用於 ARTXP (在分葉節點中)，另一個用於 ARIMA (在樹狀目錄的根節點中)。</span><span class="sxs-lookup"><span data-stu-id="bb560-184">If you have created a mixed model, you can see two formulas, one for ARTXP (in the leaf nodes) and one for ARIMA (in the root node of the tree).</span></span>  
  
-   <span data-ttu-id="bb560-185">小菱形用於表示連續數字的節點。</span><span class="sxs-lookup"><span data-stu-id="bb560-185">The little diamonds are used in nodes that represent continuous numbers.</span></span> <span data-ttu-id="bb560-186">菱形所在的橫線上會顯示屬性的範圍。</span><span class="sxs-lookup"><span data-stu-id="bb560-186">The range of the attributes is shown in the bar on which the diamond rests.</span></span> <span data-ttu-id="bb560-187">菱形會在節點的平均值置中，而菱形的寬度代表在該節點的屬性變異數。</span><span class="sxs-lookup"><span data-stu-id="bb560-187">The diamond is centered on the mean for the node, and the width of the diamond represents the variance of the attribute at that node.</span></span>  
  
 [<span data-ttu-id="bb560-188">回到頁首</span><span class="sxs-lookup"><span data-stu-id="bb560-188">Back to Top</span></span>](#bkmk_Charts)  
  
##  <a name="optional-generic-content-tree-viewer"></a><a name="bkmk_Content"></a> <span data-ttu-id="bb560-189">(選擇性) 一般內容樹狀檢視器</span><span class="sxs-lookup"><span data-stu-id="bb560-189">(Optional) Generic Content Tree Viewer</span></span>  
 <span data-ttu-id="bb560-190">除了時間序列的自訂檢視器之外， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 還提供**MicrosoftGeneric 內容樹狀檢視器**，以用於所有資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="bb560-190">In addition to the custom viewer for time series, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides the **MicrosoftGeneric Content Tree Viewer** for use with all data mining models.</span></span> <span data-ttu-id="bb560-191">此檢視器具備一些優點：</span><span class="sxs-lookup"><span data-stu-id="bb560-191">This viewer provides some advantages:</span></span>  
  
-   <span data-ttu-id="bb560-192">**Microsoft 時間序列檢視器**：此視圖會合並這兩種演算法的結果。</span><span class="sxs-lookup"><span data-stu-id="bb560-192">**Microsoft Time Series Viewer**: This view merges the results of the two algorithms.</span></span> <span data-ttu-id="bb560-193">雖然您可以分別檢視每個序列，但無法判斷各演算法結果如何結合。</span><span class="sxs-lookup"><span data-stu-id="bb560-193">Although you can view each series separately, you cannot determine how the results of each algorithm were combined.</span></span> <span data-ttu-id="bb560-194">此外，在此檢視中，工具提示和採礦圖例只顯示最重要的統計資料。</span><span class="sxs-lookup"><span data-stu-id="bb560-194">Also, in this view, the Tooltips and Mining Legend show only the most important statistics.</span></span>  
  
-   <span data-ttu-id="bb560-195">**一般內容樹狀檢視器**：可讓您一次流覽和查看模型中使用的所有資料數列，如果您已建立混合模型，ARIMA 和 ARTXP 樹狀目錄都會顯示在相同的圖形中。</span><span class="sxs-lookup"><span data-stu-id="bb560-195">**Generic Content Tree Viewer**: Lets you browse and view all of the data series that were used in the model at one time, and if you have created a mixed model, both the ARIMA and ARTXP trees are displayed in the same graph.</span></span>  
  
     <span data-ttu-id="bb560-196">您可以使用此檢視器取得兩個演算法的所有統計資料，以及值分佈。</span><span class="sxs-lookup"><span data-stu-id="bb560-196">You can use this viewer to get all the statistics from both algorithms, as well as distributions of the values.</span></span>  
  
     <span data-ttu-id="bb560-197">建議想要深入了解 ARIMA 和 ARTXP 分析的資料採礦專家使用者採用。</span><span class="sxs-lookup"><span data-stu-id="bb560-197">Recommended for expert users of data mining who want to know more about the ARIMA and ARTXP analyses.</span></span>  
  
#### <a name="to-view-details-for-a-particular-data-series-in-the-generic-content-viewer"></a><span data-ttu-id="bb560-198">在一般內容樹狀檢視器中檢視特定資料序列的詳細資料</span><span class="sxs-lookup"><span data-stu-id="bb560-198">To view details for a particular data series in the generic content viewer</span></span>  
  
1.  <span data-ttu-id="bb560-199">在 [**採礦模型檢視器**] 索引標籤中，從 [**檢視器**] 下拉式清單中選取 [ **Microsoft 一般內容樹狀檢視器**]。</span><span class="sxs-lookup"><span data-stu-id="bb560-199">In the **Mining Model Viewer** tab, select **Microsoft Generic Content Tree Viewer** from the **Viewer** drop-down list.</span></span>  
  
2.  <span data-ttu-id="bb560-200">在 [**節點標題**] 窗格中，按一下最上層 ([所有) ] 節點。</span><span class="sxs-lookup"><span data-stu-id="bb560-200">In the **Node Caption** pane, click the topmost (All) node.</span></span>  
  
3.  <span data-ttu-id="bb560-201">在 [**節點詳細資料**] 窗格中，查看 ATTRIBUTE_NAME 的值。</span><span class="sxs-lookup"><span data-stu-id="bb560-201">In the **Node Details** pane, view the value for ATTRIBUTE_NAME.</span></span>  
  
     <span data-ttu-id="bb560-202">這個值顯示這個節點包含哪一個序列或產品與區域組合。</span><span class="sxs-lookup"><span data-stu-id="bb560-202">This value shows you which series, or combination of product and region, is contained in this node.</span></span> <span data-ttu-id="bb560-203">在 AdventureWorks 範例中，最頂端的節點屬於 M200 Europe 序列。</span><span class="sxs-lookup"><span data-stu-id="bb560-203">In the AdventureWorks example, the topmost node is for the M200 Europe series.</span></span>  
  
4.  <span data-ttu-id="bb560-204">在 [**節點標題**] 窗格中，找出具有子節點的第一個節點。</span><span class="sxs-lookup"><span data-stu-id="bb560-204">In the **Node Caption** pane, locate the first node that has child nodes.</span></span>  
  
     <span data-ttu-id="bb560-205">如果數列節點具有子系，則 Microsoft 時間序列檢視器的 [**模型**] 索引標籤上所顯示的樹狀檢視也會有分支結構。</span><span class="sxs-lookup"><span data-stu-id="bb560-205">If a series node has children, the tree view that appears on the **Model** tab of the Microsoft Time Series Viewer will also have a branching structure.</span></span>  
  
5.  <span data-ttu-id="bb560-206">展開該節點，並按一下其中一個子節點。</span><span class="sxs-lookup"><span data-stu-id="bb560-206">Expand the node and click one of the child nodes.</span></span>  
  
     <span data-ttu-id="bb560-207">結構描述的 NODE_DESCRIPTION 資料行包含造成樹狀結構分岔的條件。</span><span class="sxs-lookup"><span data-stu-id="bb560-207">The NODE_DESCRIPTION column of the schema contains the condition that caused the tree to split.</span></span>  
  
6.  <span data-ttu-id="bb560-208">在 [**節點標題**] 窗格中，按一下最上層的 ARIMA 節點，然後展開節點，直到所有子節點都可見為止。</span><span class="sxs-lookup"><span data-stu-id="bb560-208">In the **Node Caption** pane, click the topmost ARIMA node, and expand the node until all child nodes are visible.</span></span>  
  
7.  <span data-ttu-id="bb560-209">在 [**節點詳細資料**] 窗格中，查看 ATTRIBUTE_NAME 的值。</span><span class="sxs-lookup"><span data-stu-id="bb560-209">In the **Node Details** pane, view the value for ATTRIBUTE_NAME.</span></span>  
  
     <span data-ttu-id="bb560-210">這個值會告訴您這個節點包含哪一個時間序列。</span><span class="sxs-lookup"><span data-stu-id="bb560-210">This value tells you which time series is contained in this node.</span></span> <span data-ttu-id="bb560-211">ARIMA 區段中最頂端的節點應該符合 (All) 區段中最頂端的節點。</span><span class="sxs-lookup"><span data-stu-id="bb560-211">The topmost node in the ARIMA section should match the topmost node in the (All) section.</span></span> <span data-ttu-id="bb560-212">在 AdventureWorks 範例中，這個節點包含 M200 Europe 序列的 ARIMA 分析。</span><span class="sxs-lookup"><span data-stu-id="bb560-212">In the AdventureWorks example, this node contains the ARIMA analysis for the series, M200 Europe.</span></span>  
  
 <span data-ttu-id="bb560-213">如需詳細資訊，請參閱[時間序列模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="bb560-213">For more information, see [Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md).</span></span>  
  
 [<span data-ttu-id="bb560-214">回到頁首</span><span class="sxs-lookup"><span data-stu-id="bb560-214">Back to Top</span></span>](#bkmk_Charts)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="bb560-215">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="bb560-215">Next Task in Lesson</span></span>  
 [<span data-ttu-id="bb560-216">&#40;中繼資料採礦教學課程建立時間序列預測&#41;</span><span class="sxs-lookup"><span data-stu-id="bb560-216">Creating Time Series Predictions &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="bb560-217">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb560-217">See Also</span></span>  
 <span data-ttu-id="bb560-218">[時間序列模型查詢範例](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="bb560-218">[Time Series Model Query Examples](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span></span>  
 [<span data-ttu-id="bb560-219">Microsoft 時間序列演算法技術參考</span><span class="sxs-lookup"><span data-stu-id="bb560-219">Microsoft Time Series Algorithm Technical Reference</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
