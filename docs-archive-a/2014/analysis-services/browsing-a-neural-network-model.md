---
title: 流覽類神經網路模型 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- mining model, neural network
- neural networks
- dependency network
ms.assetid: e4224cb7-115b-4889-ac07-03f096fb55fc
author: minewiskan
ms.author: owend
ms.openlocfilehash: ab2673d5b1881f74c2bc146b084d2efc7b06d69b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593107"
---
# <a name="browsing-a-neural-network-model"></a><span data-ttu-id="cf90c-102">瀏覽類神經網路模型</span><span class="sxs-lookup"><span data-stu-id="cf90c-102">Browsing a Neural Network Model</span></span>
  <span data-ttu-id="cf90c-103">當您使用 [瀏覽]\*\*\*\* 開啟類神經網路或羅吉斯迴歸模型時，該模型會在類似於 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 類神經網路檢視器的互動式檢視器中顯示。</span><span class="sxs-lookup"><span data-stu-id="cf90c-103">When you open a neural network or logistic regression model using **Browse**, the model is displayed in an interactive viewer, similar to the neural network model viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="cf90c-104">此檢視器可協助您探索相互關聯，以及取得有關模型和基礎資料之模式的資訊。</span><span class="sxs-lookup"><span data-stu-id="cf90c-104">The viewer helps you explore correlations, and get information about the patterns in the model and the underlying data.</span></span>

##  <a name="explore-the-model"></a><a name="BKMK_Tabs"></a><span data-ttu-id="cf90c-105">探索模型</span><span class="sxs-lookup"><span data-stu-id="cf90c-105">Explore the Model</span></span>
 <span data-ttu-id="cf90c-106">以 [!INCLUDE[msCoName](../includes/msconame-md.md)] 類神經網路或羅吉斯迴歸演算法為基礎的模型很相似，因為它們都會將資料分析成已知輸入與輸出之間的一組連接。</span><span class="sxs-lookup"><span data-stu-id="cf90c-106">Models that are based on [!INCLUDE[msCoName](../includes/msconame-md.md)] Neural Network or Logistic Regression algorithms are similar in that they analyze data as a set of connections among known inputs and outputs.</span></span> <span data-ttu-id="cf90c-107">[瀏覽]\*\*\*\* 檢視器可協助您使用下列控制項來探索這些連接：</span><span class="sxs-lookup"><span data-stu-id="cf90c-107">The **Browse** viewer helps you to explore those connections, using the following controls:</span></span>

-   [<span data-ttu-id="cf90c-108">變數</span><span class="sxs-lookup"><span data-stu-id="cf90c-108">Variables</span></span>](#BKMK_Variables)

-   [<span data-ttu-id="cf90c-109">輸入</span><span class="sxs-lookup"><span data-stu-id="cf90c-109">Inputs</span></span>](#BKMK_Inputs)

-   [<span data-ttu-id="cf90c-110">輸出</span><span class="sxs-lookup"><span data-stu-id="cf90c-110">Outputs</span></span>](#BKMK_Outputs)

 <span data-ttu-id="cf90c-111">如果您想要試驗這個檢視器，可以使用[分類精靈 &#40;適用於 Excel 的資料採礦增益集&#41;](classify-wizard-data-mining-add-ins-for-excel.md) 精靈來建立模型，並且使用 [演算法參數]\*\*\*\* 對話方塊中的 [進階]\*\*\*\* 選項，將演算法變更為 Microsoft 羅吉斯迴歸。</span><span class="sxs-lookup"><span data-stu-id="cf90c-111">If you want to experiment with this viewer, you can create a model using the [Classify Wizard &#40;Data Mining Add-ins for Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md) wizard, and use the **Advanced** option to change the algorithm to Microsoft Logistic Regression in the **Algorithm Parameters** dialog box.</span></span>

###  <a name="variables"></a><a name="BKMK_Variables"></a><span data-ttu-id="cf90c-112">變數</span><span class="sxs-lookup"><span data-stu-id="cf90c-112">Variables</span></span>
 <span data-ttu-id="cf90c-113">[變數]\*\*\*\* 窗格會按照輸入變數作用於模型的順序，顯示這些變數的清單。</span><span class="sxs-lookup"><span data-stu-id="cf90c-113">The **Variables** pane displays a list of input variables in order of their effect on the model.</span></span> <span data-ttu-id="cf90c-114">您可以使用 [輸入]\*\*\*\* 和 [輸出]\*\*\*\* 控制項來篩選模型，並影響顯示的變數及其順序。</span><span class="sxs-lookup"><span data-stu-id="cf90c-114">You use the **Input** and **Output** controls to filter the model, affecting the variables that are displayed, as well as their order.</span></span>

 <span data-ttu-id="cf90c-115">在判斷客戶比較可能屬於自行車購買者類別目錄或非購買者類別目錄時，您可以使用此檢視器來探索最重要的因數。</span><span class="sxs-lookup"><span data-stu-id="cf90c-115">Using this viewer, you can explore the factors that are most important in determining whether a customer more likely belongs to the bike buyer category or the non-buyer category.</span></span>

 <span data-ttu-id="cf90c-116">![測試對選取屬性結果的影響](media/dm13-neuralnet-agebuyer1.gif "測試對選取屬性結果的影響")</span><span class="sxs-lookup"><span data-stu-id="cf90c-116">![Testing effect on outcome of selected attributes](media/dm13-neuralnet-agebuyer1.gif "Testing effect on outcome of selected attributes")</span></span>

##### <a name="explore-variables"></a><span data-ttu-id="cf90c-117">探索變數</span><span class="sxs-lookup"><span data-stu-id="cf90c-117">Explore variables</span></span>

1.  <span data-ttu-id="cf90c-118">在指定目前篩選的情況下，[變數]\*\*\*\* 窗格一開始會按照最重要屬性的順序排序。</span><span class="sxs-lookup"><span data-stu-id="cf90c-118">Initially, the **Variables** pane is sorted in order of the most important attributes, given the current filters.</span></span> <span data-ttu-id="cf90c-119">垂直線的長度表示因數的強度。</span><span class="sxs-lookup"><span data-stu-id="cf90c-119">The length of the bar indicates the strength of the factor.</span></span>

     <span data-ttu-id="cf90c-120">在此範例中，您可以看見收入是最具影響力的因數，其次是地區。</span><span class="sxs-lookup"><span data-stu-id="cf90c-120">In the example, you can see that income is the most influential factor, followed by region.</span></span> <span data-ttu-id="cf90c-121">另一方面，擁有許多部車和多個小孩的客戶不太可能會購買自行車。</span><span class="sxs-lookup"><span data-stu-id="cf90c-121">On the other hand, customers with many cars and many children are highly unlikely to buy a bike.</span></span>

2.  <span data-ttu-id="cf90c-122">在 [變數]\*\*\*\* 窗格中，按一下 [屬性]\*\*\*\* 的資料行標題。</span><span class="sxs-lookup"><span data-stu-id="cf90c-122">In the **Variables** pane, click the column heading for **Attribute**.</span></span>

     <span data-ttu-id="cf90c-123">透過針對屬性排序，您就可以查看針對每個輸入資料行建立的分類收納。</span><span class="sxs-lookup"><span data-stu-id="cf90c-123">By sorting on attribute, you can see the bins that were created for each of the input columns.</span></span> <span data-ttu-id="cf90c-124">具有離散值的資料行 (例如職業) 會按照常值「分類收納」\*\* (Bin)。</span><span class="sxs-lookup"><span data-stu-id="cf90c-124">Columns with discrete values, such as occupation, are *binned* by the literal values.</span></span>

3.  <span data-ttu-id="cf90c-125">請注意針對 [年齡]\*\*\*\* 和 [收入]\*\*\*\* 找到的值範圍。</span><span class="sxs-lookup"><span data-stu-id="cf90c-125">Notice the ranges of values that were found for **Age** and **Income**.</span></span>

     <span data-ttu-id="cf90c-126">如果任何輸入資料行是數字 (亦即，整個資料行都是連續數值資料類型)，這些數字就會儲存或分類收納成離散範圍。</span><span class="sxs-lookup"><span data-stu-id="cf90c-126">If any of your input columns are numbers (that is, the entire column of data is a continuous numeric data type), the numbers are bucketed, or binned, into discrete ranges.</span></span>

     <span data-ttu-id="cf90c-127">就 Income 而言，此資料行已經細分為群組，例如 78.4-154.06 (代表最高收入範圍)。</span><span class="sxs-lookup"><span data-stu-id="cf90c-127">For Income, the column has been subdivided into groupings such as 78.4-154.06 (for the uppermost income range).</span></span>

     <span data-ttu-id="cf90c-128">![排序以檢視變數分類收納的方式](media/dm13-nn-bucketing-variables.gif "排序以檢視變數分類收納的方式")</span><span class="sxs-lookup"><span data-stu-id="cf90c-128">![sort to view how variables were binned](media/dm13-nn-bucketing-variables.gif "sort to view how variables were binned")</span></span>

     <span data-ttu-id="cf90c-129">如果您想要不同的群組，就應該使用[重定標籤 &#40;SQL Server 資料採礦增益集&#41;](relabel-sql-server-data-mining-add-ins.md) 工具或 Excel 函數來建立新的收入類別目錄，然後再建立模型。</span><span class="sxs-lookup"><span data-stu-id="cf90c-129">If you want different groupings, you should use the [Relabel &#40;SQL Server Data Mining Add-ins&#41;](relabel-sql-server-data-mining-add-ins.md) tool, or Excel functions, to create new income categories before building the model.</span></span>

4.  <span data-ttu-id="cf90c-130">按一下 [喜好 Yes]\*\*\*\*，將圖形還原成預設檢視。</span><span class="sxs-lookup"><span data-stu-id="cf90c-130">Click **Favors Yes** to restore the graph to the default view.</span></span>

     <span data-ttu-id="cf90c-131">根據預設，此檢視會按照第一個結果值的 [喜好]\*\*\*\* 值來排序。</span><span class="sxs-lookup"><span data-stu-id="cf90c-131">By default, the view is sorted by the value of **Favors** for the first outcome value.</span></span> <span data-ttu-id="cf90c-132">您可以針對 [輸出]\*\*\*\* 中的 [值 1]\*\*\*\* 和 [值 2]\*\*\*\* 選擇新的值，藉以變更指派給第一個和第二個資料行的結果。</span><span class="sxs-lookup"><span data-stu-id="cf90c-132">You can change which outcomes are assigned to the first and second columns by choosing a new value for **Value 1** and **Value 2** in **Output**.</span></span>

5.  <span data-ttu-id="cf90c-133">將滑鼠游標暫時放在圖表中最頂端的彩色列上。</span><span class="sxs-lookup"><span data-stu-id="cf90c-133">Pause the mouse over the topmost colored bar in the chart.</span></span>

     <span data-ttu-id="cf90c-134">工具提示隨即出現，其中包含「重要性」\*\* 分數、一對「機率」\*\* 分數，以及一對「增益」\*\* 值。</span><span class="sxs-lookup"><span data-stu-id="cf90c-134">A ToolTip appears that includes an *importance* score, a pair of *probability* scores, and a pair of *lift* values.</span></span>

    -   <span data-ttu-id="cf90c-135">**重要性**的計算範圍是整個資料集，而且可在指定所有輸入的情況下，識別與目標結果最相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="cf90c-135">**Importance** is calculated across the entire dataset, and identifies the attribute that, given all inputs, is most correlated with the target outcome.</span></span> <span data-ttu-id="cf90c-136">此檢視器會按照重要性分數排序圖表中的值。</span><span class="sxs-lookup"><span data-stu-id="cf90c-136">The viewer sorts the values in the chart by the importance scores.</span></span>

    -   <span data-ttu-id="cf90c-137">**機率**的計算範圍是整個資料集內，目標結果的每組屬性值配對。</span><span class="sxs-lookup"><span data-stu-id="cf90c-137">**Probability** is calculated for each set of attribute-value pairs, for the target outcomes, across the entire data set.</span></span>

    -   <span data-ttu-id="cf90c-138">**增益**會告知您這個特定屬性值配對在促成不同結果方面的有用程度。</span><span class="sxs-lookup"><span data-stu-id="cf90c-138">**Lift** tells you how useful this particular attribute-value pair is for promoting one outcome or another.</span></span>

     <span data-ttu-id="cf90c-139">注意：不論您將滑鼠游標放在哪個資料行上方，工具提示都會包含相同的資訊。</span><span class="sxs-lookup"><span data-stu-id="cf90c-139">Note: The ToolTip contains the same information no matter whether you position the mouse over one column or the other.</span></span>

 [<span data-ttu-id="cf90c-140">回到頁首</span><span class="sxs-lookup"><span data-stu-id="cf90c-140">Back To Top</span></span>](#BKMK_Tabs)

###  <a name="inputs"></a><a name="BKMK_Inputs"></a><span data-ttu-id="cf90c-141">輸入</span><span class="sxs-lookup"><span data-stu-id="cf90c-141">Inputs</span></span>
 <span data-ttu-id="cf90c-142">[輸入]\*\*\*\* 窗格可讓您選擇一組輸入並且套用該組輸入當成模型的篩選，以便根據定型資料，查看這些選擇對於結果的影響</span><span class="sxs-lookup"><span data-stu-id="cf90c-142">The **Inputs** pane lets you choose a set of inputs and apply that as a filter to the model, which lets you see the influence of those choices on the outcome, based on the training data</span></span>

##### <a name="explore-inputs"></a><span data-ttu-id="cf90c-143">探索輸入</span><span class="sxs-lookup"><span data-stu-id="cf90c-143">Explore inputs</span></span>

1.  <span data-ttu-id="cf90c-144">假設您想要鎖定特定群組，並且查看最能影響該群組之購買行為的因數。</span><span class="sxs-lookup"><span data-stu-id="cf90c-144">Suppose you want to target a particular group, and see the factors that most influence purchasing in that group.</span></span>

     <span data-ttu-id="cf90c-145">在 [**輸入**] 窗格中，按一下 [屬性] 底下的資料 **\<All>** 格，然後選取 [ \*\* \*\*\*\*年齡\*\*]。</span><span class="sxs-lookup"><span data-stu-id="cf90c-145">In the **Input** pane, click the **\<All>** cell under **Attribute**, and select **Age**.</span></span>

     <span data-ttu-id="cf90c-146">針對 [值]\*\*\*\*，選取最年輕的年齡類別目錄。</span><span class="sxs-lookup"><span data-stu-id="cf90c-146">For **Value**, select the youngest age category.</span></span>

2.  <span data-ttu-id="cf90c-147">請注意，即使您針對特定的年齡群組篩選，太平洋地區還是會顯示在清單頂端附近。</span><span class="sxs-lookup"><span data-stu-id="cf90c-147">Notice that even when you filter on a particular age group, the Pacific region comes to near the top of the list.</span></span> <span data-ttu-id="cf90c-148">這是因為太平洋地區的客戶購買自行車的可能性高於其他地區的客戶。</span><span class="sxs-lookup"><span data-stu-id="cf90c-148">This is because customers in the Pacific region are far more likely to buy a bike than customers in other regions.</span></span>

     <span data-ttu-id="cf90c-149">由於地區是您無法影響的條件，因此，若要從考量中移除此變數並查看其他因數，您可以再次變更輸入。</span><span class="sxs-lookup"><span data-stu-id="cf90c-149">Since region is not something you can influence, to remove this variable from consideration and see other factors, you can change the inputs again.</span></span>

     <span data-ttu-id="cf90c-150">在 [輸入]\*\*\*\* 窗格中，按一下 [年齡]\*\*\*\* 底下的空白資料格，然後選取 [區域]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cf90c-150">In the **Input** pane, click the empty cell under **Age**, and select **Region**.</span></span>

     <span data-ttu-id="cf90c-151">針對 [值]\*\*\*\*，選取 [歐洲]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cf90c-151">For **Value**, select **Europe**.</span></span>

3.  <span data-ttu-id="cf90c-152">繼續加入輸入篩選，將焦點放在特別感興趣的群組上。</span><span class="sxs-lookup"><span data-stu-id="cf90c-152">Continue adding input filters to focus on a group of particular interest.</span></span>

     <span data-ttu-id="cf90c-153">例如，針對輸入屬性，新增 [性別]\*\*\*\*，並且選取 [女性]\*\*\*\* 作為值。</span><span class="sxs-lookup"><span data-stu-id="cf90c-153">For example, for the input attribute, add **Gender**, and select **Female** as the value.</span></span>

     <span data-ttu-id="cf90c-154">![測試對選取屬性結果的影響](media/dm13-neuralnet-agebuyer2.gif "測試對選取屬性結果的影響")</span><span class="sxs-lookup"><span data-stu-id="cf90c-154">![Testing effect on outcome of selected attributes](media/dm13-neuralnet-agebuyer2.gif "Testing effect on outcome of selected attributes")</span></span>

     <span data-ttu-id="cf90c-155">請注意變數的清單如何變更。</span><span class="sxs-lookup"><span data-stu-id="cf90c-155">Notice how the list of variables changes.</span></span> <span data-ttu-id="cf90c-156">現在，[收入]\*\*\*\* 是預測目標結果的最重要變數。</span><span class="sxs-lookup"><span data-stu-id="cf90c-156">Now **Income** is the variable that is most important in predicting the target outcome.</span></span>

     <span data-ttu-id="cf90c-157">您套用輸入篩選的順序不會影響結果。</span><span class="sxs-lookup"><span data-stu-id="cf90c-157">The order in which you apply the input filters does not affect the results.</span></span>

 [<span data-ttu-id="cf90c-158">回到頁首</span><span class="sxs-lookup"><span data-stu-id="cf90c-158">Back To Top</span></span>](#BKMK_Tabs)

###  <a name="outputs"></a><a name="BKMK_Outputs"></a><span data-ttu-id="cf90c-159">產出</span><span class="sxs-lookup"><span data-stu-id="cf90c-159">Outputs</span></span>
 <span data-ttu-id="cf90c-160">在 [輸出]\*\*\*\* 窗格中，您可以選擇自己感興趣的結果。</span><span class="sxs-lookup"><span data-stu-id="cf90c-160">In the **Outputs** pane, you can choose the outcome that you are interested in.</span></span> <span data-ttu-id="cf90c-161">類神經網路可讓您指定任意數目的結果資料行，不過，加入更多輸出會增加模型的複雜度，而且可能需要更長的處理時間。</span><span class="sxs-lookup"><span data-stu-id="cf90c-161">Neural networks let you specify as many outcome columns as you like, although adding more outputs adds to the complexity of the model and may require a much longer time to process.</span></span>

 <span data-ttu-id="cf90c-162">若要比較兩個輸出，您必須將這些輸出指定為 [預測]\*\*\*\* 或 [僅預測]\*\*\*\* 資料行。</span><span class="sxs-lookup"><span data-stu-id="cf90c-162">To compare two outputs, they must have been designated as **Predict** or **Predict Only** columns.</span></span>

##### <a name="explore-outputs"></a><span data-ttu-id="cf90c-163">探索輸出</span><span class="sxs-lookup"><span data-stu-id="cf90c-163">Explore outputs</span></span>

1.  <span data-ttu-id="cf90c-164">使用 [輸出屬性]\*\*\*\* 清單來選取屬性。</span><span class="sxs-lookup"><span data-stu-id="cf90c-164">Use the **Output Attribute** list to select an attribute.</span></span>

2.  <span data-ttu-id="cf90c-165">從 [值 1] 和 [值 2] 清單中選取兩個結果。</span><span class="sxs-lookup"><span data-stu-id="cf90c-165">Select two outcomes from the Value 1 and Value 2 lists.</span></span> <span data-ttu-id="cf90c-166">輸出屬性的這兩個狀態將會在 **[變數]** 窗格中做比較。</span><span class="sxs-lookup"><span data-stu-id="cf90c-166">These two states of the output attribute will be compared in the **Variables** pane.</span></span>

 [<span data-ttu-id="cf90c-167">回到頁首</span><span class="sxs-lookup"><span data-stu-id="cf90c-167">Back To Top</span></span>](#BKMK_Tabs)

## <a name="more-about-neural-network-models"></a><span data-ttu-id="cf90c-168">進一步了解類神經網路模型</span><span class="sxs-lookup"><span data-stu-id="cf90c-168">More About Neural Network Models</span></span>
 <span data-ttu-id="cf90c-169">此檢視器中的資訊是使用這個模型類型特有的預存程序，從伺服器中擷取而來：System.Microsoft.AnalysisServices.System.DataMining.NeuralNet.GetAttributeScores。</span><span class="sxs-lookup"><span data-stu-id="cf90c-169">The information in the viewer is retrieved from the server using a stored procedure specific to this model type: System.Microsoft.AnalysisServices.System.DataMining.NeuralNet.GetAttributeScores.</span></span>

 <span data-ttu-id="cf90c-170">如果您想要使用增益集來建立具有多個可預測屬性的模型，請使用 [進階]\*\*\*\* 模型選項。</span><span class="sxs-lookup"><span data-stu-id="cf90c-170">If you want to create a model with multiple predictable attributes using the add-ins, use the **Advanced** modeling options.</span></span>

 <span data-ttu-id="cf90c-171">如需詳細資訊，請參閱[建立採礦結構 &#40;SQL Server 資料採礦增益集&#41;](create-mining-structure-sql-server-data-mining-add-ins.md) 和[將模型加入結構 &#40;適用於 Excel 的資料採礦增益集&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="cf90c-171">For more information, see [Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;](create-mining-structure-sql-server-data-mining-add-ins.md) and [Add Model to Structure &#40;Data Mining Add-ins for Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cf90c-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf90c-172">See Also</span></span>
 [<span data-ttu-id="cf90c-173">在 Excel 中流覽模型 &#40;SQL Server 資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="cf90c-173">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)


