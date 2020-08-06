---
title: Microsoft 貝氏貝氏機率分類演算法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Bayesian classifiers
- algorithms [data mining]
- predictive modeling [Analysis Services]
- classification algorithms [Analysis Services]
- naive bayes algorithms [Analysis Services]
ms.assetid: 3b53e011-3b1a-4cd1-bdc2-456768ba31b5
author: minewiskan
ms.author: owend
ms.openlocfilehash: f38ba263f4bba9ec09e2f195c3ed16ec8b3a1229
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686530"
---
# <a name="microsoft-naive-bayes-algorithm"></a><span data-ttu-id="5a8a4-102">Microsoft Naive Bayes Algorithm</span><span class="sxs-lookup"><span data-stu-id="5a8a4-102">Microsoft Naive Bayes Algorithm</span></span>
  <span data-ttu-id="5a8a4-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]貝氏貝氏機率分類演算法是以貝氏機率分類 ' 定理為基礎的分類演算法，並由提供以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 用於預測模型。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm is a classification algorithm based on Bayes' theorems, and provided by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] for use in predictive modeling.</span></span> <span data-ttu-id="5a8a4-104">貝氏 (Naïve Bayes) 名稱中的 naïve 一字源自此演算法使用 Bayesian 技術但卻沒有考量可能存在的相依性。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-104">The word naïve in the name Naïve Bayes derives from the fact that the algorithm uses Bayesian techniques but does not take into account dependencies that may exist.</span></span>

 <span data-ttu-id="5a8a4-105">此演算法比其他 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 演算法更少計算，因此對於快速產生採礦模型來探索輸入資料行和可預測資料行之間的關聯性很有用。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-105">This algorithm is less computationally intense than other [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, and therefore is useful for quickly generating mining models to discover relationships between input columns and predictable columns.</span></span> <span data-ttu-id="5a8a4-106">您可以使用此演算法來執行資料的初始瀏覽，然後您可以套用其結果，以其他更多計算和更精確的演算法來建立其他採礦模型。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-106">You can use this algorithm to do initial exploration of data, and then later you can apply the results to create additional mining models with other algorithms that are more computationally intense and more accurate.</span></span>

## <a name="example"></a><span data-ttu-id="5a8a4-107">範例</span><span class="sxs-lookup"><span data-stu-id="5a8a4-107">Example</span></span>
 <span data-ttu-id="5a8a4-108">做為一項正在進行的促銷策略，Adventure Works Cycle 公司的行銷部門決定郵寄廣告傳單來鎖定目標潛在客戶。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-108">As an ongoing promotional strategy, the marketing department for the Adventure Works Cycle company has decided to target potential customers by mailing out fliers.</span></span> <span data-ttu-id="5a8a4-109">為了減少成本，他們想要將廣告傳單只寄給那些有可能回應的客戶。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-109">To reduce costs, they want to send fliers only to those customers who are likely to respond.</span></span> <span data-ttu-id="5a8a4-110">公司會將有關人口統計資料和舊郵件的回應等資訊儲存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-110">The company stores information in a database about demographics and response to a previous mailing.</span></span> <span data-ttu-id="5a8a4-111">他們想要使用此資料來了解人口統計資料 (例如年齡和地點) 如何協助預測促銷的回應，藉由將潛在客戶與具有類似特性而且過去曾向公司購買產品的客戶做比較。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-111">They want to use this data to see how demographics such as age and location can help predict response to a promotion, by comparing potential customers to customers who have similar characteristics and who have purchased from the company in the past.</span></span> <span data-ttu-id="5a8a4-112">尤其，他們想要看看那些有購買腳踏車和沒有購買腳踏車的客戶之間的差異。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-112">Specifically, they want to see the differences between those customers who bought a bicycle and those customers who did not.</span></span>

 <span data-ttu-id="5a8a4-113">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 貝氏機率分類演算法，行銷部門可以快速預測特定客戶設定檔的結果，因此可以判斷哪些客戶最有可能對廣告傳單做出回應。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-113">By using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm, the marketing department can quickly predict an outcome for a particular customer profile, and can therefore determine which customers are most likely to respond to the fliers.</span></span> <span data-ttu-id="5a8a4-114">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 中的 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]貝氏機率分類檢視器，他們還可以利用視覺化方式來調查哪些輸入資料行促成廣告傳單的正面回應。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-114">By using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], they can also visually investigate specifically which input columns contribute to positive responses to fliers.</span></span>

## <a name="how-the-algorithm-works"></a><span data-ttu-id="5a8a4-115">演算法的運作方式</span><span class="sxs-lookup"><span data-stu-id="5a8a4-115">How the Algorithm Works</span></span>
 <span data-ttu-id="5a8a4-116">在提供了可預測資料行的每一個可能狀態之後， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 貝氏機率分類演算法可計算出每一個輸入資料行的每一個狀態的機率。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-116">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm calculates the probability of every state of each input column, given each possible state of the predictable column.</span></span>

 <span data-ttu-id="5a8a4-117">若要了解其運作方式，請在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 中使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 貝氏機率分類檢視器 (如下圖所示)，以視覺方式瀏覽此演算法如何分配狀態。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-117">To understand how this works, use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] (as shown in the following graphic) to visually explore how the algorithm distributes states.</span></span>

 <span data-ttu-id="5a8a4-118">![狀態的貝氏機率分類分佈](../media/naive-bayes.gif "狀態的貝氏機率分類分佈")</span><span class="sxs-lookup"><span data-stu-id="5a8a4-118">![Naive bayes distribution of states](../media/naive-bayes.gif "Naive bayes distribution of states")</span></span>

 <span data-ttu-id="5a8a4-119">提供了可預測資料行的每一個狀態之後， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 貝氏機率分類檢視器會在這裡列出資料集內的每一個輸入資料行，並顯示如何分配每一個資料行的狀態。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-119">Here, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer lists each input column in the dataset, and shows how the states of each column are distributed, given each state of the predictable column.</span></span>

 <span data-ttu-id="5a8a4-120">您會使用這個模型檢視來識別在區分可預測資料行的狀態時，非常重要的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-120">You would use this view of the model to identify the input columns that are important for differentiating between states of the predictable column.</span></span>

 <span data-ttu-id="5a8a4-121">例如，這裡顯示的 [通勤距離] 資料列中，購買者與非購買者的輸入值分佈明顯不同。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-121">For example, in the row for Commute Distance shown here, the distribution of input values is visibly different for buyers vs. non-buyers.</span></span> <span data-ttu-id="5a8a4-122">這告訴我們，Commute Distance = 0-1 miles 輸入可能是預測指標。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-122">What this tells you is that the input, Commute Distance = 0-1 miles, is a potential predictor.</span></span>

 <span data-ttu-id="5a8a4-123">該檢視器也提供了分佈的值，好讓您可以看到，對於通勤距離為一至二英里的客戶，其購買自行車的機率是 0.387，而不購買自行車的機率則是 0.287。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-123">The viewer also provides values for the distributions, so you can see that for customers who commute from one to two miles to work, the probability of them buying a bike is 0.387, and the probability that they will not buy a bike is 0.287.</span></span> <span data-ttu-id="5a8a4-124">在此範例中，此演算法會使用從客戶特性衍生的數值資訊 (例如通勤距離) 來預測客戶是否會購買自行車。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-124">In this example, the algorithm uses the numeric information, derived from customer characteristics (such as commute distance), to predict whether a customer will buy a bike.</span></span>

 <span data-ttu-id="5a8a4-125">如需使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 貝氏機率分類檢視器的詳細資訊，請參閱 [使用 Microsoft 貝氏機率分類檢視器瀏覽模型](browse-a-model-using-the-microsoft-naive-bayes-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-125">For more information about using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer, see [Browse a Model Using the Microsoft Naive Bayes Viewer](browse-a-model-using-the-microsoft-naive-bayes-viewer.md).</span></span>

## <a name="data-required-for-naive-bayes-models"></a><span data-ttu-id="5a8a4-126">貝氏機率分類模型所需的資料</span><span class="sxs-lookup"><span data-stu-id="5a8a4-126">Data Required for Naive Bayes Models</span></span>
 <span data-ttu-id="5a8a4-127">當您準備資料以供貝氏機率分類模型定型使用時，應該要了解特定演算法的需求，包括所需的資料量及資料的使用方式等。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-127">When you prepare data for use in training a Naive Bayes model, you should understand the requirements for the algorithm, including how much data is needed, and how the data is used.</span></span>

 <span data-ttu-id="5a8a4-128">貝氏機率分類模型的需求如下：</span><span class="sxs-lookup"><span data-stu-id="5a8a4-128">The requirements for a Naive Bayes model are as follows:</span></span>

-   <span data-ttu-id="5a8a4-129">**單一索引鍵資料行** ：每個模型都必須包含一個能唯一識別每一筆記錄的數值或文字資料行。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-129">**A single key column** Each model must contain one numeric or text column that uniquely identifies each record.</span></span> <span data-ttu-id="5a8a4-130">不允許複合的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-130">Compound keys are not allowed.</span></span>

-   <span data-ttu-id="5a8a4-131">**輸入資料行**在貝氏貝氏機率分類模型中，所有資料行都必須是離散或離散化資料行。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-131">**Input columns** In a Naive Bayes model, all columns must be either discrete or discretized columns.</span></span> <span data-ttu-id="5a8a4-132">如需分隔資料行的相關資訊，請參閱[離散化方法 &#40;資料採礦&#41;](discretization-methods-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-132">For information about discretizing columns, see [Discretization Methods &#40;Data Mining&#41;](discretization-methods-data-mining.md).</span></span>

     <span data-ttu-id="5a8a4-133">對貝氏機率分類模型而言，確保輸入屬性彼此無關也很重要。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-133">For a Naive Bayes model, it is also important to ensure that the input attributes are independent of each other.</span></span> <span data-ttu-id="5a8a4-134">當您使用此模型進行預測時，這一點格外重要。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-134">This is particularly important when you use the model for prediction.</span></span>

     <span data-ttu-id="5a8a4-135">原因在於，如果您使用已緊密相關的兩個資料行，則會導致這些資料行的影響倍增，從而遮蓋影響結果的其他因素。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-135">The reason is that, if you use two columns of data that are already closely related, the effect would be to multiply the influence of those columns, which can obscure other factors that influence the outcome.</span></span>

     <span data-ttu-id="5a8a4-136">相反地，當您瀏覽模型或資料集來辨識輸入之間的關聯性時，此演算法能夠識別變數之間關聯的功能會很有用。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-136">Conversely, the ability of the algorithm to identify correlations among variables is useful when you are exploring a model or dataset, to identify relationships among inputs.</span></span>

-   <span data-ttu-id="5a8a4-137">**至少有一個可預期的資料行** ：可預期的屬性必須包含離散或離散化的值。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-137">**At least one predictable column** The predictable attribute must contain discrete or discretized values.</span></span>

     <span data-ttu-id="5a8a4-138">可預期資料行的值可視為輸入。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-138">The values of the predictable column can be treated as inputs.</span></span> <span data-ttu-id="5a8a4-139">當您瀏覽新的資料集來尋找資料行之間的關聯性時，這個作法很有用。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-139">This practice can be useful when you are exploring a new dataset, to find relationships among the columns.</span></span>

## <a name="viewing-the-model"></a><span data-ttu-id="5a8a4-140">檢視模型</span><span class="sxs-lookup"><span data-stu-id="5a8a4-140">Viewing the Model</span></span>
 <span data-ttu-id="5a8a4-141">若要瀏覽此模型，您可以使用 **[Microsoft 貝氏機率分類檢視器]**。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-141">To explore the model, you can use the **Microsoft Naive Bayes Viewer**.</span></span> <span data-ttu-id="5a8a4-142">檢視器會顯示輸入屬性與可預測屬性間的關聯。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-142">The viewer shows you how the input attributes relate to the predictable attribute.</span></span> <span data-ttu-id="5a8a4-143">檢視器也會針對每個群集提供詳細的設定檔、區分各個群集的屬性清單以及整個訓練資料集的特性。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-143">The viewer also provides a detailed profile of each cluster, a list of the attributes that distinguish each cluster from the others, and the characteristics of the entire training data set.</span></span> <span data-ttu-id="5a8a4-144">如需詳細資訊，請參閱 [使用 Microsoft 貝氏機率分類檢視器瀏覽模型](browse-a-model-using-the-microsoft-naive-bayes-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-144">For more information, see [Browse a Model Using the Microsoft Naive Bayes Viewer](browse-a-model-using-the-microsoft-naive-bayes-viewer.md).</span></span>

 <span data-ttu-id="5a8a4-145">如果您想要知道更多詳細資訊，您可以在 [Microsoft 一般內容樹狀檢視器 &#40;資料採礦&#41;](../microsoft-generic-content-tree-viewer-data-mining.md) 中瀏覽此模型。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-145">If you want to know more detail, you can browse the model in the [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span> <span data-ttu-id="5a8a4-146">如需此模型所儲存之資訊類型的詳細資訊，請參閱 [貝氏機率分類模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-146">For more information about the type of information stored in the model, see [Mining Model Content for Naive Bayes Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md).</span></span>

## <a name="making-predictions"></a><span data-ttu-id="5a8a4-147">進行預測</span><span class="sxs-lookup"><span data-stu-id="5a8a4-147">Making Predictions</span></span>
 <span data-ttu-id="5a8a4-148">在此模型已培訓之後，結果會儲存成一組模式，供您瀏覽或用來做出預測。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-148">After the model has been trained, the results are stored as a set of patterns, which you can explore or use to make predictions.</span></span>

 <span data-ttu-id="5a8a4-149">您可以建立查詢來傳回新資料與可預測屬性的關聯方式，或者擷取描述有關群集的描述性統計資料。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-149">You can create queries to return predictions about how new data relates to the predictable attribute, or you can retrieve statistics that describe the correlations found by the model.</span></span>

 <span data-ttu-id="5a8a4-150">如需如何針對資料採礦模型建立查詢的資訊，請參閱 [資料採礦查詢](data-mining-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-150">For information about how to create queries against a data mining model, see [Data Mining Queries](data-mining-queries.md).</span></span> <span data-ttu-id="5a8a4-151">如需如何以貝氏機率分類模型使用查詢的範例，請參閱 [貝式機率分類模型查詢範例](naive-bayes-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-151">For examples of how to use queries with a Naive Bayes model, see [Naive Bayes Model Query Examples](naive-bayes-model-query-examples.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="5a8a4-152">備註</span><span class="sxs-lookup"><span data-stu-id="5a8a4-152">Remarks</span></span>

-   <span data-ttu-id="5a8a4-153">支援使用預測模型標記語言 (PMML) 來建立採礦模型。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-153">Supports the use of Predictive Model Markup Language (PMML) to create mining models.</span></span>

-   <span data-ttu-id="5a8a4-154">支援鑽研。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-154">Supports drillthrough.</span></span>

-   <span data-ttu-id="5a8a4-155">不支援建立資料採礦維度。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-155">Does not support the creation of data mining dimensions.</span></span>

-   <span data-ttu-id="5a8a4-156">支援 OLAP 採礦模型的使用。</span><span class="sxs-lookup"><span data-stu-id="5a8a4-156">Supports the use of OLAP mining models.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a8a4-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a8a4-157">See Also</span></span>
 <span data-ttu-id="5a8a4-158">[資料採礦演算法 &#40;Analysis Services 資料採礦&#41;](data-mining-algorithms-analysis-services-data-mining.md) [特徵選取 &#40;資料採礦&#41;](feature-selection-data-mining.md) [貝氏貝氏機率分類模型查詢範例](naive-bayes-model-query-examples.md)[貝氏貝氏機率分類模型的採礦模型內容 &#40;Analysis Services-資料採礦&#41;](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md) [Microsoft 貝氏貝氏機率分類演算法技術參考](microsoft-naive-bayes-algorithm-technical-reference.md)</span><span class="sxs-lookup"><span data-stu-id="5a8a4-158">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) [Feature Selection &#40;Data Mining&#41;](feature-selection-data-mining.md) [Naive Bayes Model Query Examples](naive-bayes-model-query-examples.md) [Mining Model Content for Naive Bayes Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md) [Microsoft Naive Bayes Algorithm Technical Reference](microsoft-naive-bayes-algorithm-technical-reference.md)</span></span>


