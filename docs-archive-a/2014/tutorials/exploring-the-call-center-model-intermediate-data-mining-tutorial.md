---
title: 流覽撥打電話中心模型 (元資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9095212c-9068-4dd8-85ce-17a467adeabb
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2aceec298ba78e29988571293f8422ab9e55aa97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703557"
---
# <a name="exploring-the-call-center-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="eb0e0-102">探索撥接中心模型 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="eb0e0-102">Exploring the Call Center Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="eb0e0-103">現在您已經建立了探勘模型，您可以使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 所提供的下列工具深入了解您的資料。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-103">Now that you have built the exploratory model, you can use it to learn more about your data by using the following tools provided in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="eb0e0-104">[Microsoft 類神經網路查看](#bkmk_NNviewer)器 **：** 您可以在資料採礦設計師的 [**採礦模型檢視器**] 索引標籤中使用此檢視器，其設計目的是要協助您試驗資料中的互動。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-104">[Microsoft Neural Network Viewer](#bkmk_NNviewer) **:** This viewer is available in the **Mining Model Viewer** tab of Data Mining Designer, and is designed to help you experiment with interactions in the data.</span></span>  
  
-   <span data-ttu-id="eb0e0-105">[Microsoft 一般內容樹狀檢視器](#bkmk_genviewer) **：** 這個標準檢視器可提供在產生模型時，演算法發現的模式和統計資料的深入詳細資料。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-105">[Microsoft Generic Content Tree Viewer](#bkmk_genviewer) **:** This standard viewer provides in-depth detail about the patterns and statistics discovered by the algorithm when it generated the model.</span></span>  
  
##  <a name="microsoft-neural-network-viewer"></a><a name="bkmk_NNviewer"></a><span data-ttu-id="eb0e0-106">Microsoft 類神經網路檢視器</span><span class="sxs-lookup"><span data-stu-id="eb0e0-106">Microsoft Neural Network Viewer</span></span>  
 <span data-ttu-id="eb0e0-107">檢視器有三個窗格-**輸入**、**輸出**和**變數**。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-107">The viewer has three panes - **Input**, **Output**, and **Variables**.</span></span>  
  
 <span data-ttu-id="eb0e0-108">藉由使用 [**輸出**] 窗格，您可以為可預測的屬性或相依變數選取不同的值。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-108">By using the **Output** pane, you can select different values for the predictable attribute, or dependent variable.</span></span> <span data-ttu-id="eb0e0-109">如果您的模型包含多個可預測的屬性，您可以從 [**輸出屬性**] 清單中選取屬性。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-109">If your model contains multiple predictable attributes, you can select the attribute from the **Output Attribute** list.</span></span>  
  
 <span data-ttu-id="eb0e0-110">[**變數**] 窗格會比較您在參與屬性或變數方面所選擇的兩個結果。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-110">The **Variables** pane compares the two outcomes that you chose in terms of contributing attributes, or variables.</span></span> <span data-ttu-id="eb0e0-111">彩色列以視覺方式表示變數影響目標結果的強度。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-111">The colored bars visually represent how strongly the variable affects the target outcomes.</span></span> <span data-ttu-id="eb0e0-112">您也可以檢視變數的增益分數。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-112">You can also view lift scores for the variables.</span></span> <span data-ttu-id="eb0e0-113">增益分數會根據您所使用的採礦模型類型而有不同的計算方式，但在使用此屬性進行預測時，通常會告訴您模型的增進部分。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-113">A lift score is calculated differently depending on which mining model type you are using, but generally tells you the improvement in the model when using this attribute for prediction.</span></span>  
  
 <span data-ttu-id="eb0e0-114">[**輸入**] 窗格可讓您將影響因素加入至模型，以嘗試各種假設情況。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-114">The **Input** pane lets you add influencers to the model to try out various what-if scenarios.</span></span>  
  
### <a name="using-the-output-pane"></a><span data-ttu-id="eb0e0-115">使用輸出窗格</span><span class="sxs-lookup"><span data-stu-id="eb0e0-115">Using the Output Pane</span></span>  
 <span data-ttu-id="eb0e0-116">在此初始模型中，您可能有興趣想要查看各種因數如何影響服務等級。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-116">In this initial model, you are interested in seeing how various factors affect the grade of service.</span></span> <span data-ttu-id="eb0e0-117">若要這樣做，您可以從輸出屬性清單中選取 [服務等級]，然後從 [**值 1** ] 和 [**值 2**] 的下拉式清單中選取範圍，藉以比較不同層級的服務。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-117">To do this, you can select Service Grade from the list of output attributes, and then compare different levels of service by selecting ranges from the dropdown lists for **Value 1** and **Value 2**.</span></span>  
  
##### <a name="to-compare-lowest-and-highest-service-grades"></a><span data-ttu-id="eb0e0-118">若要比較最低和最高的服務等級</span><span class="sxs-lookup"><span data-stu-id="eb0e0-118">To compare lowest and highest service grades</span></span>  
  
1.  <span data-ttu-id="eb0e0-119">針對 [**值 1**]，選取具有最低值的範圍。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-119">For **Value 1**, select the range with the lowest values.</span></span> <span data-ttu-id="eb0e0-120">例如，範圍 0-0-0.7 表示最低的放棄率，因此是最佳的服務等級。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-120">For example, the range 0-0-0.7 represents the lowest abandon rates, and therefore the best level of service.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb0e0-121">在此範圍中的實際值可能會隨著您設定模型的方式而有所不同。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-121">The exact values in this range may vary depending on how you configured the model.</span></span>  
  
2.  <span data-ttu-id="eb0e0-122">在 [**值 2**] 中，選取最高值的範圍。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-122">For **Value 2**, select the range with the highest values.</span></span> <span data-ttu-id="eb0e0-123">例如，值為 >= 0.12 的範圍代表最高的放棄率，因此是最差的服務等級。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-123">For example, the range with the value >=0.12 represents the highest abandon rates, and therefore the worst service grade.</span></span> <span data-ttu-id="eb0e0-124">換句話說，在此排班期間打電話的客戶之中，有 12% 的客戶在與服務人員通話前，就會掛斷電話。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-124">In other words, 12% of the customers who phoned during this shift hung up before speaking to a representative.</span></span>  
  
     <span data-ttu-id="eb0e0-125">[**變數**] 窗格的內容會更新，以比較構成結果值的屬性。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-125">The contents of the **Variables** pane are updated to compare attributes that contribute to the outcome values.</span></span> <span data-ttu-id="eb0e0-126">因此，左側資料行會顯示與最佳服務等級相關聯的屬性，而右側資料行則顯示與最差服務等級相關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-126">Therefore, the left column shows you the attributes that are associated with the best grade of service, and the right column shows you the attributes associated with the worst grade of service.</span></span>  
  
### <a name="using-the-variables-pane"></a><span data-ttu-id="eb0e0-127">使用變數窗格</span><span class="sxs-lookup"><span data-stu-id="eb0e0-127">Using the Variables Pane</span></span>  
 <span data-ttu-id="eb0e0-128">在此模型中，它會顯示 `Average Time Per Issue` 為重要因素。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-128">In this model, it appears that `Average Time Per Issue` is an important factor.</span></span> <span data-ttu-id="eb0e0-129">此變數表示回應通話所需的平均時間，無論通話類型為何。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-129">This variable indicates the average time that it takes for a call to be answered, regardless of call type.</span></span>  
  
##### <a name="to-view-and-copy-probability-and-lift-scores-for-an-attribute"></a><span data-ttu-id="eb0e0-130">若要檢視與複製屬性的機率和增益分數</span><span class="sxs-lookup"><span data-stu-id="eb0e0-130">To view and copy probability and lift scores for an attribute</span></span>  
  
1.  <span data-ttu-id="eb0e0-131">在 [**變數**] 窗格中，將滑鼠游標暫留在第一個資料列的彩色橫條上。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-131">In the **Variables** pane, pause the mouse over the colored bar in the first row.</span></span>  
  
     <span data-ttu-id="eb0e0-132">這個彩色的橫條會顯示您 `Average Time Per Issue` 對服務等級的貢獻程度。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-132">This colored bar shows you how strongly `Average Time Per Issue` contributes toward the service grade.</span></span> <span data-ttu-id="eb0e0-133">工具提示會針對變數和目標結果的每個組合，顯示整體分數、機率，以及增益分數。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-133">The tooltip shows an overall score, probabilities, and lift scores for each combination of a variable and a target outcome.</span></span>  
  
2.  <span data-ttu-id="eb0e0-134">在 [**變數**] 窗格中，以滑鼠右鍵按一下任何彩色橫條，然後選取 [**複製**]。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-134">In the **Variables** pane, right-click any colored bar and select **Copy**.</span></span>  
  
3.  <span data-ttu-id="eb0e0-135">在 Excel 工作表中，以滑鼠右鍵按一下任何資料格，然後選取 [**貼**上]。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-135">In an Excel worksheet, right-click any cell and select **Paste**.</span></span>  
  
     <span data-ttu-id="eb0e0-136">此報表就會貼上為 HTML 表格，並僅顯示每列的分數。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-136">The report is pasted as an HTML table, and shows only the scores for each bar.</span></span>  
  
4.  <span data-ttu-id="eb0e0-137">在不同的 Excel 工作表中，以滑鼠右鍵按一下任何資料格，然後選取 [**貼上特殊**]。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-137">In a different Excel worksheet, right-click any cell and select **Paste Special**.</span></span>  
  
     <span data-ttu-id="eb0e0-138">此報表會以文字格式貼上，並包含下節所描述的相關統計資料。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-138">The report is pasted as text format, and includes the related statistics described in the next section.</span></span>  
  
### <a name="using-the-input-pane"></a><span data-ttu-id="eb0e0-139">使用輸入窗格</span><span class="sxs-lookup"><span data-stu-id="eb0e0-139">Using the Input Pane</span></span>  
 <span data-ttu-id="eb0e0-140">假設您有興趣查看特定因數的效果，例如排班或操作員數目。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-140">Suppose that you are interested in looking at the effect of a particular factor, such as the shift, or number of operators.</span></span> <span data-ttu-id="eb0e0-141">您可以使用 [**輸入**] 窗格來選取特定變數，[**變數**] 窗格會自動更新，以比較先前選取的兩個群組（指定的變數）。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-141">You can select a particular variable by using the **Input** pane, and the **Variables** pane is automatically updated to compare the two previously selected groups given the specified variable.</span></span>  
  
##### <a name="to-review-the-effect-on-service-grade-by-changing-input-attributes"></a><span data-ttu-id="eb0e0-142">若要變更輸入屬性來檢閱對於服務等級的效果</span><span class="sxs-lookup"><span data-stu-id="eb0e0-142">To review the effect on service grade by changing input attributes</span></span>  
  
1.  <span data-ttu-id="eb0e0-143">在 [**輸入**] 窗格中，針對 [**屬性**] 選取 [移位]。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-143">In the **Input** pane, for **attribute**, select Shift.</span></span>  
  
2.  <span data-ttu-id="eb0e0-144">針對 [**值**]，選取 [ **AM**]。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-144">For **Value**, select **AM**.</span></span>  
  
     <span data-ttu-id="eb0e0-145">[**變數**] 窗格會更新，以顯示當位移為**AM**時，對模型的影響。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-145">The **Variables** pane updates to show the impact on the model when the shift is **AM**.</span></span> <span data-ttu-id="eb0e0-146">所有其他選項都維持不變，您仍在比較最低和最高的服務等級。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-146">All other selections remain the same - you are still comparing the lowest and highest service grades.</span></span>  
  
3.  <span data-ttu-id="eb0e0-147">針對 [**值**]，選取 [ **PM1**]。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-147">For **Value**, select **PM1**.</span></span>  
  
     <span data-ttu-id="eb0e0-148">[**變數**] 窗格會更新，以顯示當移位變更時，對模型的影響。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-148">The **Variables** pane updates to show the impact on the model when the shift changes.</span></span>  
  
4.  <span data-ttu-id="eb0e0-149">在 [**輸入**] 窗格中，按一下 [**屬性**] 底下的下一個空白資料列，然後選取 [呼叫]。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-149">In the **Input** pane, click the next blank row under **Attribute**, and select Calls.</span></span> <span data-ttu-id="eb0e0-150">針對 [**值**]，選取表示最大呼叫次數的範圍。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-150">For **Value**, select the range that indicates the greatest number of calls.</span></span>  
  
     <span data-ttu-id="eb0e0-151">新的輸入條件就會加入至清單中。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-151">A new input condition is added to the list.</span></span> <span data-ttu-id="eb0e0-152">[**變數**] 窗格會更新，以顯示呼叫量最高時，對特定排班之模型的影響。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-152">The **Variables** pane updates to show the impact on the model for a particular shift when the call volume is highest.</span></span>  
  
5.  <span data-ttu-id="eb0e0-153">繼續變更 [排班] 和 [通話] 的值，以尋找排班、通話量，以及服務等級之間任何有趣的相互關聯。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-153">Continue to change the values for Shift and Calls to find any interesting correlations between shift, call volume, and service grade.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eb0e0-154">若要清除 [**輸入**] 窗格，讓您可以使用不同的屬性，請按一下 [重新整理**檢視器內容]**。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-154">To clear the **Input** pane so that you can use different attributes, click **Refresh viewer content**.</span></span>  
  
### <a name="interpreting-the-statistics-provided-in-the-viewer"></a><span data-ttu-id="eb0e0-155">解譯檢視器中所提供的統計資料</span><span class="sxs-lookup"><span data-stu-id="eb0e0-155">Interpreting the Statistics Provided in the Viewer</span></span>  
 <span data-ttu-id="eb0e0-156">較長的等待時間是一項代表高放棄率的準確預測指標，同時也意味著較差的服務等級。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-156">Longer waiting times are a strong predictor of a high abandon rate, meaning a poor service grade.</span></span> <span data-ttu-id="eb0e0-157">這似乎是一個明顯的結論，不過，採礦模型會提供您一些額外的統計資料以協助您解譯這些趨勢。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-157">This may seem an obvious conclusion; however, the mining model provides you with some additional statistical data to help you interpret these trends.</span></span>  
  
-   <span data-ttu-id="eb0e0-158">**分數**：指出此變數在結果之間群集辨識之整體重要性的值。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-158">**Score**: Value that indicates the overall importance of this variable for discriminating between outcomes.</span></span> <span data-ttu-id="eb0e0-159">分數越高，表示變數對於結果的效果越強。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-159">The higher the score, the stronger the effect the variable has on the outcome.</span></span>  
  
-   <span data-ttu-id="eb0e0-160">**值1的**機率：百分比，表示此結果的這個值的機率。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-160">**Probability of value 1**: Percentage that represents the probability of this value for this outcome.</span></span>  
  
-   <span data-ttu-id="eb0e0-161">**值2的**機率：百分比，表示此結果的這個值的機率。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-161">**Probability of value 2**: Percentage that represents the probability of this value for this outcome.</span></span>  
  
-   <span data-ttu-id="eb0e0-162">**值 1**的增益和**值2的**增益：表示使用這個特定變數來預測值1和值2結果之影響的分數。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-162">**Lift for Value 1** and **Lift for Value 2**: Scores that represents the impact of using this particular variable for predicting the Value 1 and Value 2 outcomes.</span></span> <span data-ttu-id="eb0e0-163">分數越高，表示變數越能預測結果。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-163">The higher the score, the better the variable is at predicting the outcomes.</span></span>  
  
 <span data-ttu-id="eb0e0-164">下表包含最重要之影響因數的一些範例值。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-164">The following table contains some example values for the top influencers.</span></span> <span data-ttu-id="eb0e0-165">例如，**值 1**的機率為60.6%，而**值 2**的機率為8.30%，表示當每個問題的平均時間介於44-70 分鐘的範圍內時，60.6% 的案例就會在最高服務等級的轉移中 (值 1) ，而8.30% 的案例則是在較差的服務等級 (值 2) 的轉移中。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-165">For example, the **Probability of value 1** is 60.6% and **Probability of value 2** is 8.30%, meaning that when the Average Time Per Issue was in the range of 44-70 minutes, 60.6% of cases were in the shift with the highest service grades (Value 1), and 8.30% of cases were in the shift with the worse service grades (Value 2).</span></span>  
  
 <span data-ttu-id="eb0e0-166">從這個資訊中，您可以得到一些結論。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-166">From this information, you can draw some conclusions.</span></span> <span data-ttu-id="eb0e0-167">較短的通話回應時間 (範圍是 44-70) 對於較佳的服務等級 (範圍是 0.00-0.07) 有強大的影響。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-167">Shorter call response time (the range of 44-70) strongly influences better service grade (the range 0.00-0.07).</span></span> <span data-ttu-id="eb0e0-168">此分數 (92.35) 表示這個變數非常重要。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-168">The score (92.35) tells you that this variable is very important.</span></span>  
  
 <span data-ttu-id="eb0e0-169">不過，當您向下查看影響的因數清單時，可以看到一些其他的因數，以及比較不容易理解也比較難解譯的效果。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-169">However, as you look down the list of contributing factors, you see some other factors with effects that are more subtle and more difficult to interpret.</span></span> <span data-ttu-id="eb0e0-170">例如，排班似乎會影響服務，但是增益分數和相對機率卻指出排班不是主要的因數。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-170">For example, shift appears to influence service, but the lift scores and the relative probabilities indicate that shift is not a major factor.</span></span>  
  
|<span data-ttu-id="eb0e0-171">屬性</span><span class="sxs-lookup"><span data-stu-id="eb0e0-171">Attribute</span></span>|<span data-ttu-id="eb0e0-172">值</span><span class="sxs-lookup"><span data-stu-id="eb0e0-172">Value</span></span>|<span data-ttu-id="eb0e0-173">優先 \< 0.07</span><span class="sxs-lookup"><span data-stu-id="eb0e0-173">Favors \< 0.07</span></span>|<span data-ttu-id="eb0e0-174">優先 >= 0.12</span><span class="sxs-lookup"><span data-stu-id="eb0e0-174">Favors >= 0.12</span></span>|  
|---------------|-----------|--------------------|----------------------|  
|<span data-ttu-id="eb0e0-175">每個問題的平均時間</span><span class="sxs-lookup"><span data-stu-id="eb0e0-175">Average Time Per Issue</span></span>|<span data-ttu-id="eb0e0-176">89.087-120.000</span><span class="sxs-lookup"><span data-stu-id="eb0e0-176">89.087 - 120.000</span></span>||<span data-ttu-id="eb0e0-177">分數：100</span><span class="sxs-lookup"><span data-stu-id="eb0e0-177">Score:  100</span></span><br /><br /> <span data-ttu-id="eb0e0-178">Value1 的機率：4.45%</span><span class="sxs-lookup"><span data-stu-id="eb0e0-178">Probability of Value1: 4.45 %</span></span><br /><br /> <span data-ttu-id="eb0e0-179">Value2 的機率：51.94%</span><span class="sxs-lookup"><span data-stu-id="eb0e0-179">Probability of Value2: 51.94 %</span></span><br /><br /> <span data-ttu-id="eb0e0-180">Value1 的增益：0.19</span><span class="sxs-lookup"><span data-stu-id="eb0e0-180">Lift for Value1: 0.19</span></span><br /><br /> <span data-ttu-id="eb0e0-181">Value2 的增益：1.94</span><span class="sxs-lookup"><span data-stu-id="eb0e0-181">Lift for Value2: 1.94</span></span>|  
|<span data-ttu-id="eb0e0-182">每個問題的平均時間</span><span class="sxs-lookup"><span data-stu-id="eb0e0-182">Average Time Per Issue</span></span>|<span data-ttu-id="eb0e0-183">44.000-70.597</span><span class="sxs-lookup"><span data-stu-id="eb0e0-183">44.000 - 70.597</span></span>|<span data-ttu-id="eb0e0-184">分數：92.35</span><span class="sxs-lookup"><span data-stu-id="eb0e0-184">Score: 92.35</span></span><br /><br /> <span data-ttu-id="eb0e0-185">值 1 的機率：60.06 %</span><span class="sxs-lookup"><span data-stu-id="eb0e0-185">Probability of Value1: 60.06 %</span></span><br /><br /> <span data-ttu-id="eb0e0-186">值 2 的機率：8.30 %</span><span class="sxs-lookup"><span data-stu-id="eb0e0-186">Probability of Value2: 8.30 %</span></span><br /><br /> <span data-ttu-id="eb0e0-187">值 1 的增益：2.61</span><span class="sxs-lookup"><span data-stu-id="eb0e0-187">Lift for Value1: 2.61</span></span><br /><br /> <span data-ttu-id="eb0e0-188">值 2 的增益：0.31</span><span class="sxs-lookup"><span data-stu-id="eb0e0-188">Lift for Value2: 0.31</span></span>||  
  
 [<span data-ttu-id="eb0e0-189">回到頁首</span><span class="sxs-lookup"><span data-stu-id="eb0e0-189">Back to Top</span></span>](#bkmk_NNviewer)  
  
##  <a name="microsoft-generic-content-tree-viewer"></a><a name="bkmk_genviewer"></a><span data-ttu-id="eb0e0-190">Microsoft 一般內容樹狀檢視器</span><span class="sxs-lookup"><span data-stu-id="eb0e0-190">Microsoft Generic Content Tree Viewer</span></span>  
 <span data-ttu-id="eb0e0-191">此檢視器可用於在處理模型時，檢視由演算法所建立的更詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-191">This viewer can be used to view even more detailed information created by the algorithm when the model is processed.</span></span> <span data-ttu-id="eb0e0-192">**MicrosoftGeneric 內容樹狀檢視器**會以一系列節點來表示「採礦模型」，其中每個節點都代表學習到有關定型資料的知識。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-192">The **MicrosoftGeneric Content Tree Viewer** represents the mining model as a series of nodes, wherein each node represents learned knowledge about the training data.</span></span> <span data-ttu-id="eb0e0-193">此檢視器可以搭配所有模型使用，但是節點的內容會隨著模型類型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-193">This viewer can be used with all models, but the contents of the nodes are different depending in the model type.</span></span>  
  
 <span data-ttu-id="eb0e0-194">在類神經網路模型或羅吉斯迴歸模型中，您可能會發現 `marginal statistics node` 特別實用。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-194">For neural network models or logistic regression models, you might find the `marginal statistics node` particularly useful.</span></span> <span data-ttu-id="eb0e0-195">此節點包含關於資料中值分佈的衍生統計資料。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-195">This node contains derived statistics about the distribution of values in your data.</span></span> <span data-ttu-id="eb0e0-196">如果您想要得到資料的摘要，但是不想撰寫許多 T-SQL 查詢，此資訊就非常有幫助。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-196">This information can be useful if you want to get a summary of the data without having to write many T-SQL queries.</span></span> <span data-ttu-id="eb0e0-197">在前一個主題中分類收納值的圖表便是衍生自臨界統計資料節點。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-197">The chart of binning values in the previous topic was derived from the marginal statistics node.</span></span>  
  
#### <a name="to-obtain-a-summary-of-data-values-from-the-mining-model"></a><span data-ttu-id="eb0e0-198">若要從採礦模型取得資料值的摘要</span><span class="sxs-lookup"><span data-stu-id="eb0e0-198">To obtain a summary of data values from the mining model</span></span>  
  
1.  <span data-ttu-id="eb0e0-199">在 [資料採礦設計師] 的 [**採礦模型檢視器**] 索引標籤中，選取 \<mining model name> 。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-199">In Data Mining Designer, in the **Mining Model Viewer** tab, select \<mining model name>.</span></span>  
  
2.  <span data-ttu-id="eb0e0-200">從 [**檢視器]** 清單中，選取 [ **Microsoft 一般內容樹狀檢視器]**。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-200">From the **Viewer** list, select **Microsoft Generic Content Tree Viewer**.</span></span>  
  
     <span data-ttu-id="eb0e0-201">採礦模型的檢視會重新整理，在左窗格中顯示節點階層，並在右窗格中顯示 HTML 表格。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-201">The view of the mining model refreshes to show a node hierarchy in the left-hand pane and an HTML table in the right-hand pane.</span></span>  
  
3.  <span data-ttu-id="eb0e0-202">在 [**節點標題**] 窗格中，按一下名稱為10000000000000000的節點。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-202">In the **Node Caption** pane, click the node that has the name 10000000000000000.</span></span>  
  
     <span data-ttu-id="eb0e0-203">模型中任何最頂部的節點永遠是模型根節點。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-203">The topmost node in any model is always the model root node.</span></span> <span data-ttu-id="eb0e0-204">在類神經網路或羅吉斯迴歸模型中，位於該節點正下方的節點是臨界統計資料節點。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-204">In a neural network or logistic regression model, the node immediately under that is the marginal statistics node.</span></span>  
  
4.  <span data-ttu-id="eb0e0-205">在 [**節點詳細資料**] 窗格中，向下 NODE_DISTRIBUTION，直到您找到資料列為止。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-205">In the **Node Details** pane, scroll down until you find the row, NODE_DISTRIBUTION.</span></span>  
  
5.  <span data-ttu-id="eb0e0-206">向下捲動到 NODE_DISTRIBUTION 資料表以檢視如類神經網路演算法所計算的值分佈。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-206">Scroll down through the NODE_DISTRIBUTION table to view the distribution of values as calculated by the neural network algorithm.</span></span>  
  
 <span data-ttu-id="eb0e0-207">若要在報表中使用這個資料，您可以選取然後複製特定資料列的資訊，或者也可以使用下列資料採礦延伸模組 (DMX) 查詢來擷取節點的完整內容。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-207">To use this data in a report, you could select and then copy the information for specific rows, or you can use the following Data Mining Extensions (DMX) query to extract the complete contents of the node.</span></span>  
  
```  
SELECT *   
FROM [Call Center EQ4].CONTENT  
WHERE NODE_NAME = '10000000000000000'  
```  
  
 <span data-ttu-id="eb0e0-208">您也可以使用 NODE_DISTRIBUTION 資料表中的節點階層與詳細資料來周遊類神經網路中的個別路徑，並檢視隱藏層的統計資料。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-208">You can also use the node hierarchy and the details in the NODE_DISTRIBUTION table to traverse individual paths in the neural network and view statistics from the hidden layer.</span></span> <span data-ttu-id="eb0e0-209">如需詳細資訊，請參閱類[神經網路模型查詢範例](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="eb0e0-209">For more information, see [Neural Network Model Query Examples](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md).</span></span>  
  
 [<span data-ttu-id="eb0e0-210">回到頁首</span><span class="sxs-lookup"><span data-stu-id="eb0e0-210">Back to Top</span></span>](#bkmk_NNviewer)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="eb0e0-211">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="eb0e0-211">Next Task in Lesson</span></span>  
 [<span data-ttu-id="eb0e0-212">&#40;元資料採礦教學課程中，將羅吉斯回歸模型加入至撥中心結構&#41;</span><span class="sxs-lookup"><span data-stu-id="eb0e0-212">Adding a Logistic Regression Model to the Call Center Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/add-logistic-regression-model-to-call-center-intermediate-data-mining.md)  
  
## <a name="see-also"></a><span data-ttu-id="eb0e0-213">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb0e0-213">See Also</span></span>  
 <span data-ttu-id="eb0e0-214">[類神經網路模型的採礦模型內容 &#40;Analysis Services 資料採礦&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="eb0e0-214">[Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="eb0e0-215">[類神經網路模型查詢範例](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="eb0e0-215">[Neural Network Model Query Examples](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md) </span></span>  
 <span data-ttu-id="eb0e0-216">[Microsoft 類神經網路演算法技術參考](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="eb0e0-216">[Microsoft Neural Network Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="eb0e0-217">變更採礦模型中的資料行離散化</span><span class="sxs-lookup"><span data-stu-id="eb0e0-217">Change the Discretization of a Column in a Mining Model</span></span>](../../2014/analysis-services/data-mining/change-the-discretization-of-a-column-in-a-mining-model.md)  
  
  
