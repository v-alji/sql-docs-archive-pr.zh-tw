---
title: Microsoft 類神經網路演算法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- training neural networks
- output neurons [Analysis Services]
- algorithms [data mining]
- neural network algorithms [Analysis Services]
- neurons [Analysis Services]
- classification algorithms [Analysis Services]
- neural networks
- multilayer perceptron network of neurons [Analysis Services]
- hidden neurons
- Back-Propagated Delta Rule network
- input neurons [Analysis Services]
- regression algorithms [Analysis Services]
ms.assetid: 61eb4861-8a6a-4214-a4b8-1dd278ad7a68
author: minewiskan
ms.author: owend
ms.openlocfilehash: 389df77299bbf357e1b8b0f0695f03a74420f786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584842"
---
# <a name="microsoft-neural-network-algorithm"></a><span data-ttu-id="0ed25-102">Microsoft Neural Network Algorithm</span><span class="sxs-lookup"><span data-stu-id="0ed25-102">Microsoft Neural Network Algorithm</span></span>
  <span data-ttu-id="0ed25-103">在中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，類 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 神經網路演算法會將輸入屬性的每個可能狀態與可預測屬性的每個可能狀態結合，並使用定型資料來電腦率。</span><span class="sxs-lookup"><span data-stu-id="0ed25-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm combines each possible state of the input attribute with each possible state of the predictable attribute, and uses the training data to calculate probabilities.</span></span> <span data-ttu-id="0ed25-104">稍後您可以使用這些機率來進行分類或迴歸，依據輸入屬性預測該預測屬性的結果。</span><span class="sxs-lookup"><span data-stu-id="0ed25-104">You can later use these probabilities for classification or regression, and to predict an outcome of the predicted attribute, based on the input attributes.</span></span>  
  
 <span data-ttu-id="0ed25-105">以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 類神經網路演算法建構的採礦模型可包含多個網路，視用於輸入和預測的資料行數目或只用於預測的資料行數目而定。</span><span class="sxs-lookup"><span data-stu-id="0ed25-105">A mining model that is constructed with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm can contain multiple networks, depending on the number of columns that are used for both input and prediction, or that are used only for prediction.</span></span> <span data-ttu-id="0ed25-106">單一採礦模型包含的網路數目，視採礦模型使用的輸入資料行和可預測資料行所包含的狀態數目而定。</span><span class="sxs-lookup"><span data-stu-id="0ed25-106">The number of networks that a single mining model contains depends on the number of states that are contained by the input columns and predictable columns that the mining model uses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ed25-107">範例</span><span class="sxs-lookup"><span data-stu-id="0ed25-107">Example</span></span>  
 <span data-ttu-id="0ed25-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 類神經網路演算法在分析複雜輸入資料 (例如來自製造程序或商業程序的資料) 或商務問題 (有大量培訓資料可用但很難使用其他演算法來衍生規則) 時很有用。</span><span class="sxs-lookup"><span data-stu-id="0ed25-108">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm is useful for analyzing complex input data, such as from a manufacturing or commercial process, or business problems for which a significant quantity of training data is available but for which rules cannot be easily derived by using other algorithms.</span></span>  
  
 <span data-ttu-id="0ed25-109">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 類神經網路演算法的建議狀況包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="0ed25-109">Suggested scenarios for using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm include the following:</span></span>  
  
-   <span data-ttu-id="0ed25-110">行銷和促銷分析，例如衡量直接郵寄促銷廣告或電台廣告活動的績效。</span><span class="sxs-lookup"><span data-stu-id="0ed25-110">Marketing and promotion analysis, such as measuring the success of a direct mail promotion or a radio advertising campaign.</span></span>  
  
-   <span data-ttu-id="0ed25-111">從記錄資料中預測股價移動、貨幣波動或其他高流動性財務資訊。</span><span class="sxs-lookup"><span data-stu-id="0ed25-111">Predicting stock movement, currency fluctuation, or other highly fluid financial information from historical data.</span></span>  
  
-   <span data-ttu-id="0ed25-112">分析製造和產業流程。</span><span class="sxs-lookup"><span data-stu-id="0ed25-112">Analyzing manufacturing and industrial processes.</span></span>  
  
-   <span data-ttu-id="0ed25-113">文字採礦</span><span class="sxs-lookup"><span data-stu-id="0ed25-113">Text mining.</span></span>  
  
-   <span data-ttu-id="0ed25-114">任何分析許多輸入以及較少輸出之間複雜關聯性的預測模型。</span><span class="sxs-lookup"><span data-stu-id="0ed25-114">Any prediction model that analyzes complex relationships between many inputs and relatively fewer outputs.</span></span>  
  
## <a name="how-the-algorithm-works"></a><span data-ttu-id="0ed25-115">演算法的運作方式</span><span class="sxs-lookup"><span data-stu-id="0ed25-115">How the Algorithm Works</span></span>  
 <span data-ttu-id="0ed25-116">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 類神經網路演算法會建立最多由三層神經所組成的網路。</span><span class="sxs-lookup"><span data-stu-id="0ed25-116">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm creates a network that is composed of up to three layers of neurons.</span></span> <span data-ttu-id="0ed25-117">這 3 層分別是輸入層、選擇性隱藏層和輸出層。</span><span class="sxs-lookup"><span data-stu-id="0ed25-117">These layers are an input layer, an optional hidden layer, and an output layer.</span></span>  
  
 <span data-ttu-id="0ed25-118">**輸入層：** 輸入神經會定義資料採礦模型的所有輸入屬性值及其機率。</span><span class="sxs-lookup"><span data-stu-id="0ed25-118">**Input layer:** Input neurons define all the input attribute values for the data mining model, and their probabilities.</span></span>  
  
 <span data-ttu-id="0ed25-119">**隱藏層：** 隱藏神經會接收來自輸入神經的輸入，並將輸出提供給輸出神經。</span><span class="sxs-lookup"><span data-stu-id="0ed25-119">**Hidden layer:** Hidden neurons receive inputs from input neurons and provide outputs to output neurons.</span></span> <span data-ttu-id="0ed25-120">隱藏層是為輸入的各種機率指派加權之處。</span><span class="sxs-lookup"><span data-stu-id="0ed25-120">The hidden layer is where the various probabilities of the inputs are assigned weights.</span></span> <span data-ttu-id="0ed25-121">加權會對隱藏神經描述特定輸入的相關性或重要性。</span><span class="sxs-lookup"><span data-stu-id="0ed25-121">A weight describes the relevance or importance of a particular input to the hidden neuron.</span></span> <span data-ttu-id="0ed25-122">指派給輸入的加權越大，該輸入之值的重要性就越大。</span><span class="sxs-lookup"><span data-stu-id="0ed25-122">The greater the weight that is assigned to an input, the more important the value of that input is.</span></span> <span data-ttu-id="0ed25-123">加權可以是負數，這表示輸入可以禁止而非喜好特定結果。</span><span class="sxs-lookup"><span data-stu-id="0ed25-123">Weights can be negative, which means that the input can inhibit, rather than favor, a specific result.</span></span>  
  
 <span data-ttu-id="0ed25-124">**輸出層：** 輸出神經代表資料採礦模型的可預測屬性值。</span><span class="sxs-lookup"><span data-stu-id="0ed25-124">**Output layer:** Output neurons represent predictable attribute values for the data mining model.</span></span>  
  
 <span data-ttu-id="0ed25-125">如需輸入、隱藏和輸出層之建構和計分方式的詳細說明，請參閱 [Microsoft 類神經網路演算法技術參考](microsoft-neural-network-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="0ed25-125">For a detailed explanation of how the input, hidden, and output layers are constructed and scored, see [Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md).</span></span>  
  
## <a name="data-required-for-neural-network-models"></a><span data-ttu-id="0ed25-126">類神經網路模型所需的資料</span><span class="sxs-lookup"><span data-stu-id="0ed25-126">Data Required for Neural Network Models</span></span>  
 <span data-ttu-id="0ed25-127">類神經網路模型必須包含一個索引鍵資料行、一或多個輸入資料行，以及一或多個可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="0ed25-127">A neural network model must contain a key column, one or more input columns, and one or more predictable columns.</span></span>  
  
 <span data-ttu-id="0ed25-128">您為 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 類神經網路演算法所提供參數指定的值，對使用該演算法的資料採礦模型會有很大的影響。</span><span class="sxs-lookup"><span data-stu-id="0ed25-128">Data mining models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm are heavily influenced by the values that you specify for the parameters that are available to the algorithm.</span></span> <span data-ttu-id="0ed25-129">這些參數定義資料取樣的方式、如何散發或預測每個資料行所散發的資料，以及何時會叫用功能選擇來限制用於最終模型中的值。</span><span class="sxs-lookup"><span data-stu-id="0ed25-129">The parameters define how data is sampled, how data is distributed or expected to be distributed in each column, and when feature selection is invoked to limit the values that are used in the final model.</span></span>  
  
 <span data-ttu-id="0ed25-130">如需設定參數以自訂模型行為的詳細資訊，請參閱 [Microsoft 類神經網路演算法技術參考](microsoft-neural-network-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="0ed25-130">For more information about setting parameters to customize model behavior, see [Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md).</span></span>  
  
## <a name="viewing-a-neural-network-model"></a><span data-ttu-id="0ed25-131">檢視類神經網路模型</span><span class="sxs-lookup"><span data-stu-id="0ed25-131">Viewing a Neural Network Model</span></span>  
 <span data-ttu-id="0ed25-132">若要使用資料並查看模型如何在輸入與輸出之間產生關聯，可以使用 **Microsoft 類神經網路檢視器**。</span><span class="sxs-lookup"><span data-stu-id="0ed25-132">To work with the data and see how the model correlates inputs with outputs, you can use the **Microsoft Neural Network Viewer**.</span></span> <span data-ttu-id="0ed25-133">您可以利用這個自訂的檢視器來篩選輸入屬性及其值，並查看示範這些屬性和值如何影響輸出的圖表。</span><span class="sxs-lookup"><span data-stu-id="0ed25-133">With this custom viewer, you can filter on input attributes and their values, and see graphs that show how they affect the outputs.</span></span> <span data-ttu-id="0ed25-134">檢視器中的工具提示會顯示與每個成對輸入和輸出值相關聯的機率與增益。</span><span class="sxs-lookup"><span data-stu-id="0ed25-134">The tooltips in the viewer show you the probability and lift associated with each pair of input and output values.</span></span> <span data-ttu-id="0ed25-135">如需詳細資訊，請參閱 [使用 Microsoft 類神經網路檢視器瀏覽模型](browse-a-model-using-the-microsoft-neural-network-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="0ed25-135">For more information, see [Browse a Model Using the Microsoft Neural Network Viewer](browse-a-model-using-the-microsoft-neural-network-viewer.md).</span></span>  
  
 <span data-ttu-id="0ed25-136">瀏覽模型結構最簡單的方式就是使用 **Microsoft 一般內容樹狀檢視器**。</span><span class="sxs-lookup"><span data-stu-id="0ed25-136">The easiest way to explore the structure of the model is to use the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="0ed25-137">您可以檢視此模型所建立的輸入、輸出和網路，並可按一下任一節點加以展開，然後查看與輸入、輸出或隱藏層節點相關的統計資料。</span><span class="sxs-lookup"><span data-stu-id="0ed25-137">You can view the inputs, outputs, and networks created by the model, and click on any node to expand it and see statistics related to the input, output, or hidden layer nodes.</span></span> <span data-ttu-id="0ed25-138">如需詳細資訊，請參閱 [使用 Microsoft 一般內容樹狀檢視器瀏覽模型](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="0ed25-138">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span></span>  
  
## <a name="creating-predictions"></a><span data-ttu-id="0ed25-139">建立預測</span><span class="sxs-lookup"><span data-stu-id="0ed25-139">Creating Predictions</span></span>  
 <span data-ttu-id="0ed25-140">當模型經過處理之後，您就可以使用網路和每個節點內儲存的加權來進行預測。</span><span class="sxs-lookup"><span data-stu-id="0ed25-140">After the model has been processed, you can use the network and the weights stored within each node to make predictions.</span></span> <span data-ttu-id="0ed25-141">類神經網路模型支援迴歸、關聯和分類分析，因此每個預測的意義都可能不同。</span><span class="sxs-lookup"><span data-stu-id="0ed25-141">A neural network model supports regression, association, and classification analysis, Therefore, the meaning of each prediction might be different.</span></span> <span data-ttu-id="0ed25-142">您也可以查詢模型本身，以檢視找到的關聯性並擷取相關的統計資料。</span><span class="sxs-lookup"><span data-stu-id="0ed25-142">You can also query the model itself, to review the correlations that were found and retrieve related statistics.</span></span> <span data-ttu-id="0ed25-143">如需如何針對類神經網路模型建立查詢的範例，請參閱 [類神經網路模型查詢範例](neural-network-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="0ed25-143">For examples of how to create queries against a neural network model, see [Neural Network Model Query Examples](neural-network-model-query-examples.md).</span></span>  
  
 <span data-ttu-id="0ed25-144">如需如何在資料採礦模型上建立查詢的一般資訊，請參閱 [資料採礦查詢](data-mining-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="0ed25-144">For general information about how to create a query on a data mining model, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ed25-145">備註</span><span class="sxs-lookup"><span data-stu-id="0ed25-145">Remarks</span></span>  
  
-   <span data-ttu-id="0ed25-146">不支援鑽研或資料採礦維度。</span><span class="sxs-lookup"><span data-stu-id="0ed25-146">Does not support drillthrough or data mining dimensions.</span></span> <span data-ttu-id="0ed25-147">這是因為採礦模型中的節點結構不一定會直接對應至基礎資料。</span><span class="sxs-lookup"><span data-stu-id="0ed25-147">This is because the structure of the nodes in the mining model does not necessarily correspond directly to the underlying data.</span></span>  
  
-   <span data-ttu-id="0ed25-148">不支援使用預測模型標記語言 (PMML) 格式來建立模型。</span><span class="sxs-lookup"><span data-stu-id="0ed25-148">Does not support the creation of models in Predictive Model Markup Language (PMML) format.</span></span>  
  
-   <span data-ttu-id="0ed25-149">支援 OLAP 採礦模型的使用。</span><span class="sxs-lookup"><span data-stu-id="0ed25-149">Supports the use of OLAP mining models.</span></span>  
  
-   <span data-ttu-id="0ed25-150">不支援建立資料採礦維度。</span><span class="sxs-lookup"><span data-stu-id="0ed25-150">Does not support the creation of data mining dimensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ed25-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ed25-151">See Also</span></span>  
 <span data-ttu-id="0ed25-152">[Microsoft 類神經網路演算法技術參考](microsoft-neural-network-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0ed25-152">[Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="0ed25-153">[類神經網路模型的採礦模型內容 &#40;Analysis Services 資料採礦&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="0ed25-153">[Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="0ed25-154">[類神經網路模型查詢範例](neural-network-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="0ed25-154">[Neural Network Model Query Examples](neural-network-model-query-examples.md) </span></span>  
 [<span data-ttu-id="0ed25-155">Microsoft 羅吉斯迴歸演算法</span><span class="sxs-lookup"><span data-stu-id="0ed25-155">Microsoft Logistic Regression Algorithm</span></span>](microsoft-logistic-regression-algorithm.md)  
  
  
