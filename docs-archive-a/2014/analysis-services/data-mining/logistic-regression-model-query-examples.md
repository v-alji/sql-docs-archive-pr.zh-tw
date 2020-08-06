---
title: 羅吉斯回歸模型查詢範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- content queries [DMX]
ms.assetid: 7c8e13a3-5c67-46c2-abfa-4881e6ef9c62
author: minewiskan
ms.author: owend
ms.openlocfilehash: d432d38794e65e8b8bea69608479e330649ee395
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584849"
---
# <a name="logistic-regression-model-query-examples"></a><span data-ttu-id="6861d-102">羅吉斯迴歸模型查詢範例</span><span class="sxs-lookup"><span data-stu-id="6861d-102">Logistic Regression Model Query Examples</span></span>
  <span data-ttu-id="6861d-103">當您針對資料採礦模型建立查詢時，可以建立內容查詢來提供有關分析期間所發現之模式的詳細資料，也可以建立預測查詢來使用模型中的模式，透過新的資料進行預測。</span><span class="sxs-lookup"><span data-stu-id="6861d-103">When you create a query against a data mining model, you can create a content query, which provides details about the patterns discovered in analysis, or you can create a prediction query, which uses the patterns in the model to make predictions using new data.</span></span>  
  
 <span data-ttu-id="6861d-104">本節說明如何針對以 Microsoft 羅吉斯迴歸演算法為基礎的模型建立查詢。</span><span class="sxs-lookup"><span data-stu-id="6861d-104">This section explains how to create queries for models that are based on the Microsoft Logistic Regression algorithm.</span></span>  
  
 <span data-ttu-id="6861d-105">**內容查詢**</span><span class="sxs-lookup"><span data-stu-id="6861d-105">**Content Queries**</span></span>  
  
 [<span data-ttu-id="6861d-106">使用資料採礦結構描述資料列集擷取模型參數</span><span class="sxs-lookup"><span data-stu-id="6861d-106">Retrieving Model Parameters by Using the Data Mining Schema Rowset</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="6861d-107">使用 DMX 尋找有關模型的其他詳細資料</span><span class="sxs-lookup"><span data-stu-id="6861d-107">Finding Additional Detail about the Model by Using DMX</span></span>](#bkmk_Query2)  
  
 <span data-ttu-id="6861d-108">**預測查詢**</span><span class="sxs-lookup"><span data-stu-id="6861d-108">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="6861d-109">針對連續值進行預測</span><span class="sxs-lookup"><span data-stu-id="6861d-109">Making Predictions for a Continuous Value</span></span>](#bkmk_Query3)  
  
 [<span data-ttu-id="6861d-110">針對離散值進行預測</span><span class="sxs-lookup"><span data-stu-id="6861d-110">Making Predictions for a Discrete Value</span></span>](#bkmk_Query4)  
  
##  <a name="getting-information-about-the-logistic-regression-model"></a><a name="bkmk_top"></a><span data-ttu-id="6861d-111">取得羅吉斯回歸模型的相關資訊</span><span class="sxs-lookup"><span data-stu-id="6861d-111">Getting Information about the Logistic Regression Model</span></span>  
 <span data-ttu-id="6861d-112">羅吉斯迴歸模型是使用 Microsoft 類神經網路演算法搭配一組特殊的參數所建立。因此，羅吉斯迴歸模型所擁有的部分資訊與類神經網路模型相同，但是較不複雜。</span><span class="sxs-lookup"><span data-stu-id="6861d-112">Logistic regression models are created by using the Microsoft Neural Network algorithm with a special set of parameters; therefore, a logistic regression model has some of the same information as a neural networks model, but is less complex.</span></span> <span data-ttu-id="6861d-113">若要了解模型內容的結構，以及哪一種節點類型會儲存那一種資訊，請參閱 [羅吉斯迴歸模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-logistic-regression-models.md)。</span><span class="sxs-lookup"><span data-stu-id="6861d-113">To understand the structure of the model content, and which node types store what kind of information, see [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).</span></span>  
  
 <span data-ttu-id="6861d-114">若要依照查詢案例進行，您可以建立羅吉斯迴歸模型，如＜中繼資料採礦教學課程＞的下節所述： [第五課：建立類神經網路和羅吉斯迴歸模型 &#40;中繼資料採礦教學課程&#41;](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="6861d-114">To follow along in the query scenarios, you can create a logistic regression model as described in the following section of the Intermediate Data Mining Tutorial: [Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md).</span></span>  
  
 <span data-ttu-id="6861d-115">您也可以使用 [資料採礦基本教學課程](../../tutorials/basic-data-mining-tutorial.md)的採礦結構：目標郵寄。</span><span class="sxs-lookup"><span data-stu-id="6861d-115">You can also use the mining structure, Targeted Mailing, from the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span>  
  
```  
ALTER MINING STRUCTURE [Targeted Mailing]  
ADD MINING MODEL [TM_Logistic Regression]  
([Customer Key],  
[Age],  
[Bike Buyer] PREDICT,  
[Yearly Income] PREDICT,  
[Commute Distance],  
[English Education],  
Gender,  
[House Owner Flag],  
[Marital Status],  
[Number Cars Owned],  
[Number Children At Home],  
[Region],  
[Total Children]  
)  
USING Microsoft_Logistic_Regression  
```  
  
###  <a name="sample-query-1-retrieving-model-parameters-by-using-the-data-mining-schema-rowset"></a><a name="bkmk_Query1"></a><span data-ttu-id="6861d-116">範例查詢1：使用資料採礦架構資料列集來抓取模型參數</span><span class="sxs-lookup"><span data-stu-id="6861d-116">Sample Query 1: Retrieving Model Parameters by Using the Data Mining Schema Rowset</span></span>  
 <span data-ttu-id="6861d-117">您可以藉由查詢資料採礦結構描述資料列集來尋找有關此模型的中繼資料，例如此模型建立的時間、上次處理此模型的時間、此模型所根據的採礦結構名稱，以及用來當做可預測屬性的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="6861d-117">By querying the data mining schema rowset, you can find metadata about the model, such as when it was created, when the model was last processed, the name of the mining structure that the model is based on, and the name of the column used as the predictable attribute.</span></span> <span data-ttu-id="6861d-118">下列範例會傳回第一次建立模型時所使用的參數，以及模型的名稱、類型與建立模型的日期。</span><span class="sxs-lookup"><span data-stu-id="6861d-118">The following example returns the parameters that were used when the model was first created, together with the name and type of the model, and the date that it was created.</span></span>  
  
```  
SELECT MODEL_NAME, SERVICE_NAME, DATE_CREATED, MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Call Center_LR'  
```  
  
 <span data-ttu-id="6861d-119">範例結果：</span><span class="sxs-lookup"><span data-stu-id="6861d-119">Sample results:</span></span>  
  
|<span data-ttu-id="6861d-120">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="6861d-120">MODEL_NAME</span></span>|<span data-ttu-id="6861d-121">SERVICE_NAME</span><span class="sxs-lookup"><span data-stu-id="6861d-121">SERVICE_NAME</span></span>|<span data-ttu-id="6861d-122">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6861d-122">DATE_CREATED</span></span>|<span data-ttu-id="6861d-123">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6861d-123">MINING_PARAMETERS</span></span>|  
|-----------------|-------------------|-------------------|------------------------|  
|<span data-ttu-id="6861d-124">Call Center_LR</span><span class="sxs-lookup"><span data-stu-id="6861d-124">Call Center_LR</span></span>|<span data-ttu-id="6861d-125">Microsoft_Logistic_Regression</span><span class="sxs-lookup"><span data-stu-id="6861d-125">Microsoft_Logistic_Regression</span></span>|<span data-ttu-id="6861d-126">04/07/2009 20:38:33</span><span class="sxs-lookup"><span data-stu-id="6861d-126">04/07/2009 20:38:33</span></span>|<span data-ttu-id="6861d-127">HOLDOUT_PERCENTAGE=30, HOLDOUT_SEED=1, MAXIMUM_INPUT_ATTRIBUTES=255, MAXIMUM_OUTPUT_ATTRIBUTES=255, MAXIMUM_STATES=100, SAMPLE_SIZE=10000</span><span class="sxs-lookup"><span data-stu-id="6861d-127">HOLDOUT_PERCENTAGE=30, HOLDOUT_SEED=1, MAXIMUM_INPUT_ATTRIBUTES=255, MAXIMUM_OUTPUT_ATTRIBUTES=255, MAXIMUM_STATES=100, SAMPLE_SIZE=10000</span></span>|  
  
###  <a name="sample-query-2-finding-additional-detail-about-the-model-by-using-dmx"></a><a name="bkmk_Query2"></a><span data-ttu-id="6861d-128">範例查詢2：使用 DMX 尋找有關模型的其他詳細資料</span><span class="sxs-lookup"><span data-stu-id="6861d-128">Sample Query 2: Finding Additional Detail about the Model by Using DMX</span></span>  
 <span data-ttu-id="6861d-129">下列查詢會傳回有關羅吉斯迴歸模型的一些基本資訊。</span><span class="sxs-lookup"><span data-stu-id="6861d-129">The following query returns some basic information about the logistic regression model.</span></span> <span data-ttu-id="6861d-130">羅吉斯迴歸模型在許多方面類似於類神經網路模型，包括存在一個描述當做輸入使用之值的臨界統計資料節點 (NODE_TYPE = 24)。</span><span class="sxs-lookup"><span data-stu-id="6861d-130">A logistic regression model is similar to a neural network model in many ways, including the presence of a marginal statistic node (NODE_TYPE = 24) that describes the values used as inputs.</span></span> <span data-ttu-id="6861d-131">這個範例查詢會使用目標郵寄模型，並且從巢狀資料表 NODE_DISTRIBUTION 中擷取所有輸入的值，藉以取得這些值。</span><span class="sxs-lookup"><span data-stu-id="6861d-131">This example query uses the Targeted Mailing model, and gets the values of all the inputs by retrieving them from the nested table, NODE_DISTRIBUTION.</span></span>  
  
```  
SELECT FLATTENED NODE_DISTRIBUTION AS t  
FROM [TM_Logistic Regression].CONTENT   
```  
  
 <span data-ttu-id="6861d-132">部分結果：</span><span class="sxs-lookup"><span data-stu-id="6861d-132">Partial results:</span></span>  
  
|<span data-ttu-id="6861d-133">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="6861d-133">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="6861d-134">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="6861d-134">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="6861d-135">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="6861d-135">t.SUPPORT</span></span>|<span data-ttu-id="6861d-136">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="6861d-136">t.PROBABILITY</span></span>|<span data-ttu-id="6861d-137">t.VARIANCE</span><span class="sxs-lookup"><span data-stu-id="6861d-137">t.VARIANCE</span></span>|<span data-ttu-id="6861d-138">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="6861d-138">t.VALUETYPE</span></span>|  
|-----------------------|------------------------|---------------|-------------------|----------------|-----------------|  
|<span data-ttu-id="6861d-139">年齡</span><span class="sxs-lookup"><span data-stu-id="6861d-139">Age</span></span>|<span data-ttu-id="6861d-140">Missing</span><span class="sxs-lookup"><span data-stu-id="6861d-140">Missing</span></span>|<span data-ttu-id="6861d-141">0</span><span class="sxs-lookup"><span data-stu-id="6861d-141">0</span></span>|<span data-ttu-id="6861d-142">0</span><span class="sxs-lookup"><span data-stu-id="6861d-142">0</span></span>|<span data-ttu-id="6861d-143">0</span><span class="sxs-lookup"><span data-stu-id="6861d-143">0</span></span>|<span data-ttu-id="6861d-144">1</span><span class="sxs-lookup"><span data-stu-id="6861d-144">1</span></span>|  
|<span data-ttu-id="6861d-145">年齡</span><span class="sxs-lookup"><span data-stu-id="6861d-145">Age</span></span>|<span data-ttu-id="6861d-146">45.43491192</span><span class="sxs-lookup"><span data-stu-id="6861d-146">45.43491192</span></span>|<span data-ttu-id="6861d-147">17484</span><span class="sxs-lookup"><span data-stu-id="6861d-147">17484</span></span>|<span data-ttu-id="6861d-148">1</span><span class="sxs-lookup"><span data-stu-id="6861d-148">1</span></span>|<span data-ttu-id="6861d-149">126.9544114</span><span class="sxs-lookup"><span data-stu-id="6861d-149">126.9544114</span></span>|<span data-ttu-id="6861d-150">3</span><span class="sxs-lookup"><span data-stu-id="6861d-150">3</span></span>|  
|<span data-ttu-id="6861d-151">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="6861d-151">Bike Buyer</span></span>|<span data-ttu-id="6861d-152">Missing</span><span class="sxs-lookup"><span data-stu-id="6861d-152">Missing</span></span>|<span data-ttu-id="6861d-153">0</span><span class="sxs-lookup"><span data-stu-id="6861d-153">0</span></span>|<span data-ttu-id="6861d-154">0</span><span class="sxs-lookup"><span data-stu-id="6861d-154">0</span></span>|<span data-ttu-id="6861d-155">0</span><span class="sxs-lookup"><span data-stu-id="6861d-155">0</span></span>|<span data-ttu-id="6861d-156">1</span><span class="sxs-lookup"><span data-stu-id="6861d-156">1</span></span>|  
|<span data-ttu-id="6861d-157">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="6861d-157">Bike Buyer</span></span>|<span data-ttu-id="6861d-158">0</span><span class="sxs-lookup"><span data-stu-id="6861d-158">0</span></span>|<span data-ttu-id="6861d-159">8869</span><span class="sxs-lookup"><span data-stu-id="6861d-159">8869</span></span>|<span data-ttu-id="6861d-160">0.507263784</span><span class="sxs-lookup"><span data-stu-id="6861d-160">0.507263784</span></span>|<span data-ttu-id="6861d-161">0</span><span class="sxs-lookup"><span data-stu-id="6861d-161">0</span></span>|<span data-ttu-id="6861d-162">4</span><span class="sxs-lookup"><span data-stu-id="6861d-162">4</span></span>|  
|<span data-ttu-id="6861d-163">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="6861d-163">Bike Buyer</span></span>|<span data-ttu-id="6861d-164">1</span><span class="sxs-lookup"><span data-stu-id="6861d-164">1</span></span>|<span data-ttu-id="6861d-165">8615</span><span class="sxs-lookup"><span data-stu-id="6861d-165">8615</span></span>|<span data-ttu-id="6861d-166">0.492736216</span><span class="sxs-lookup"><span data-stu-id="6861d-166">0.492736216</span></span>|<span data-ttu-id="6861d-167">0</span><span class="sxs-lookup"><span data-stu-id="6861d-167">0</span></span>|<span data-ttu-id="6861d-168">4</span><span class="sxs-lookup"><span data-stu-id="6861d-168">4</span></span>|  
|<span data-ttu-id="6861d-169">Commute Distance</span><span class="sxs-lookup"><span data-stu-id="6861d-169">Commute Distance</span></span>|<span data-ttu-id="6861d-170">Missing</span><span class="sxs-lookup"><span data-stu-id="6861d-170">Missing</span></span>|<span data-ttu-id="6861d-171">0</span><span class="sxs-lookup"><span data-stu-id="6861d-171">0</span></span>|<span data-ttu-id="6861d-172">0</span><span class="sxs-lookup"><span data-stu-id="6861d-172">0</span></span>|<span data-ttu-id="6861d-173">0</span><span class="sxs-lookup"><span data-stu-id="6861d-173">0</span></span>|<span data-ttu-id="6861d-174">1</span><span class="sxs-lookup"><span data-stu-id="6861d-174">1</span></span>|  
|<span data-ttu-id="6861d-175">Commute Distance</span><span class="sxs-lookup"><span data-stu-id="6861d-175">Commute Distance</span></span>|<span data-ttu-id="6861d-176">5-10 英哩</span><span class="sxs-lookup"><span data-stu-id="6861d-176">5-10 Miles</span></span>|<span data-ttu-id="6861d-177">3033</span><span class="sxs-lookup"><span data-stu-id="6861d-177">3033</span></span>|<span data-ttu-id="6861d-178">0.173472889</span><span class="sxs-lookup"><span data-stu-id="6861d-178">0.173472889</span></span>|<span data-ttu-id="6861d-179">0</span><span class="sxs-lookup"><span data-stu-id="6861d-179">0</span></span>|<span data-ttu-id="6861d-180">4</span><span class="sxs-lookup"><span data-stu-id="6861d-180">4</span></span>|  
  
 <span data-ttu-id="6861d-181">實際查詢會傳回更多資料列，但是，這個範例說明關於輸入所提供之資訊的類型。</span><span class="sxs-lookup"><span data-stu-id="6861d-181">The actual query returns many more rows; however, this sample illustrates the type of information that is provided about the inputs.</span></span> <span data-ttu-id="6861d-182">若為離散輸入，每個可能值都會列在資料表中。</span><span class="sxs-lookup"><span data-stu-id="6861d-182">For discrete inputs, each possible value is listed in the table.</span></span> <span data-ttu-id="6861d-183">若為連續值輸入 (例如 Age)，就無法列出完整清單，因此輸入會離散化為平均值。</span><span class="sxs-lookup"><span data-stu-id="6861d-183">For continuous-value inputs such as Age, a complete listing is impossible, so the input is discretized as a mean.</span></span> <span data-ttu-id="6861d-184">如需如何使用臨界統計資料節點中資訊的詳細資訊，請參閱 [羅吉斯迴歸模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-logistic-regression-models.md)。</span><span class="sxs-lookup"><span data-stu-id="6861d-184">For more information about how to use the information in the marginal statistics node, see [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6861d-185">這些結果已經過扁平化，讓檢視更為容易，但是如果您的提供者支援階層式資料列集，則可以在單一資料行中傳回巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="6861d-185">The results have been flattened for easier viewing, but you can return the nested table in a single column if your provider supports hierarchical rowsets.</span></span>  
  
## <a name="prediction-queries-on-a-logistic-regression-model"></a><span data-ttu-id="6861d-186">羅吉斯迴歸模型的預測查詢</span><span class="sxs-lookup"><span data-stu-id="6861d-186">Prediction Queries on a Logistic Regression Model</span></span>  
 <span data-ttu-id="6861d-187">您可以搭配各種採礦模型使用 [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx) 函數來提供新的資料給模型，並且根據新的值進行預測。</span><span class="sxs-lookup"><span data-stu-id="6861d-187">You can use the [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx) function with every kind of mining model to provide new data to the model and make predictions based on the new values.</span></span> <span data-ttu-id="6861d-188">您也可以使用這些函數傳回關於預測的其他資訊，例如，預測正確的機率。</span><span class="sxs-lookup"><span data-stu-id="6861d-188">You can also use functions to return additional information about the prediction, such as the probability that a prediction is correct.</span></span> <span data-ttu-id="6861d-189">本節也針對羅吉斯迴歸模型，提供一些預測查詢的範例。</span><span class="sxs-lookup"><span data-stu-id="6861d-189">This section provides some examples of prediction queries on a logistic regression model.</span></span>  
  
###  <a name="sample-query-3-making-predictions-for-a-continuous-value"></a><a name="bkmk_Query3"></a><span data-ttu-id="6861d-190">範例查詢3：針對連續值進行預測</span><span class="sxs-lookup"><span data-stu-id="6861d-190">Sample Query 3: Making Predictions for a Continuous Value</span></span>  
 <span data-ttu-id="6861d-191">由於羅吉斯迴歸支援將連續屬性同時用於輸入和預測，因此，在資料中建立與各種因數相互關聯的模型相當容易。</span><span class="sxs-lookup"><span data-stu-id="6861d-191">Because logistic regression supports the use of continuous attributes for both input and prediction, it is easy to create models that correlate various factors in your data.</span></span> <span data-ttu-id="6861d-192">您可以使用預測查詢來探索這些因數之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="6861d-192">You can use prediction queries to explore the relationship among these factors.</span></span>  
  
 <span data-ttu-id="6861d-193">下列查詢範例是以中繼教學課程中的撥接中心模型為基礎，並且建立單一查詢，以便預測星期五上午排班的服務等級。</span><span class="sxs-lookup"><span data-stu-id="6861d-193">The following query sample is based on the Call Center model, from the Intermediate Tutorial, and creates a singleton query that predicts service grade for the Friday AM shift.</span></span> <span data-ttu-id="6861d-194">[PredictHistogram (DMX)](/sql/dmx/predicthistogram-dmx) 函數會傳回一個巢狀資料表，其中提供與了解預測值之有效性相關的統計資料。</span><span class="sxs-lookup"><span data-stu-id="6861d-194">The [PredictHistogram (DMX)](/sql/dmx/predicthistogram-dmx) function returns a nested table that provides statistics relevant to understanding the validity of the predicted value.</span></span>  
  
```  
SELECT  
  Predict([Call Center_LR].[Service Grade]) as Predicted ServiceGrade,  
  PredictHistogram([Call Center_LR].[Service Grade]) as [Results],  
FROM  
  [Call Center_LR]  
NATURAL PREDICTION JOIN  
(SELECT 'Friday' AS [Day Of Week],  
  'AM' AS [Shift]) AS t  
```  
  
 <span data-ttu-id="6861d-195">範例結果：</span><span class="sxs-lookup"><span data-stu-id="6861d-195">Sample results:</span></span>  
  
 <span data-ttu-id="6861d-196">**預測的服務等級**：0.102601830123659</span><span class="sxs-lookup"><span data-stu-id="6861d-196">**Predicted Service Grade**: 0.102601830123659</span></span>  
  
 <span data-ttu-id="6861d-197">**結果**</span><span class="sxs-lookup"><span data-stu-id="6861d-197">**Results**</span></span>  
  
|<span data-ttu-id="6861d-198">服務等級</span><span class="sxs-lookup"><span data-stu-id="6861d-198">Service Grade</span></span>|<span data-ttu-id="6861d-199">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="6861d-199">$SUPPORT</span></span>|<span data-ttu-id="6861d-200">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="6861d-200">$PROBABILITY</span></span>|<span data-ttu-id="6861d-201">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="6861d-201">$ADJUSTEDPROBABILITY</span></span>|<span data-ttu-id="6861d-202">$VARIANCE</span><span class="sxs-lookup"><span data-stu-id="6861d-202">$VARIANCE</span></span>|<span data-ttu-id="6861d-203">$STDEV</span><span class="sxs-lookup"><span data-stu-id="6861d-203">$STDEV</span></span>|  
|-------------------|--------------|------------------|--------------------------|---------------|------------|  
|<span data-ttu-id="6861d-204">0.102601830123659</span><span class="sxs-lookup"><span data-stu-id="6861d-204">0.102601830123659</span></span>|<span data-ttu-id="6861d-205">83.0232558139535</span><span class="sxs-lookup"><span data-stu-id="6861d-205">83.0232558139535</span></span>|<span data-ttu-id="6861d-206">0.988372093023256</span><span class="sxs-lookup"><span data-stu-id="6861d-206">0.988372093023256</span></span>|<span data-ttu-id="6861d-207">0</span><span class="sxs-lookup"><span data-stu-id="6861d-207">0</span></span>|<span data-ttu-id="6861d-208">0.00120552660600087</span><span class="sxs-lookup"><span data-stu-id="6861d-208">0.00120552660600087</span></span>|<span data-ttu-id="6861d-209">0.034720694203902</span><span class="sxs-lookup"><span data-stu-id="6861d-209">0.034720694203902</span></span>|  
||<span data-ttu-id="6861d-210">0.976744186046512</span><span class="sxs-lookup"><span data-stu-id="6861d-210">0.976744186046512</span></span>|<span data-ttu-id="6861d-211">0.0116279069767442</span><span class="sxs-lookup"><span data-stu-id="6861d-211">0.0116279069767442</span></span>|<span data-ttu-id="6861d-212">0.0116279069767442</span><span class="sxs-lookup"><span data-stu-id="6861d-212">0.0116279069767442</span></span>|<span data-ttu-id="6861d-213">0</span><span class="sxs-lookup"><span data-stu-id="6861d-213">0</span></span>|<span data-ttu-id="6861d-214">0</span><span class="sxs-lookup"><span data-stu-id="6861d-214">0</span></span>|  
  
 <span data-ttu-id="6861d-215">如需巢狀 NODE_DISTRIBUTION 資料表之機率、支援及標準差值的詳細資訊，請參閱 [羅吉斯迴歸模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-logistic-regression-models.md)。</span><span class="sxs-lookup"><span data-stu-id="6861d-215">For more information about the probability, support, and standard deviation values in the nested NODE_DISTRIBUTION table, see [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).</span></span>  
  
###  <a name="sample-query-4-making-predictions-for-a-discrete-value"></a><a name="bkmk_Query4"></a><span data-ttu-id="6861d-216">範例查詢4：針對離散值進行預測</span><span class="sxs-lookup"><span data-stu-id="6861d-216">Sample Query 4: Making Predictions for a Discrete Value</span></span>  
 <span data-ttu-id="6861d-217">羅吉斯迴歸通常用於您要分析提供二進位結果之因數的案例中。</span><span class="sxs-lookup"><span data-stu-id="6861d-217">Logistic regression is typically used in scenarios where you want to analyze the factors that contribute to a binary outcome.</span></span> <span data-ttu-id="6861d-218">雖然教學課程中所使用的模型會預測連續值 **ServiceGrade**，不過在實際案例中，您可能會想要設定模型來預測服務等級是否符合某個離散化目標值。</span><span class="sxs-lookup"><span data-stu-id="6861d-218">Although the model used in the tutorial predicts a continuous value, **ServiceGrade**, in a real-life scenario you might want to set up the model to predict whether service grade met some discretized target value.</span></span> <span data-ttu-id="6861d-219">或者，您可能會先使用連續值來輸出預測，然後再將預測的結果分組成 **良好**、 **普通**或 **差**。</span><span class="sxs-lookup"><span data-stu-id="6861d-219">Alternatively, you could output the predictions using a continuous value but later group the predicted outcomes into **Good**, **Fair**, or **Poor**.</span></span>  
  
 <span data-ttu-id="6861d-220">下列範例說明如何變更可預測屬性的分組方式。</span><span class="sxs-lookup"><span data-stu-id="6861d-220">The following sample illustrates how to change the way that the predictable attribute is grouped.</span></span> <span data-ttu-id="6861d-221">若要這樣做，您可以建立採礦結構的複本，然後變更目標資料行的離散化方法，讓這些值成為分組值而非連續值。</span><span class="sxs-lookup"><span data-stu-id="6861d-221">To do this, you create a copy of the mining structure and then change the discretization method of the target column so that the values are grouped rather than continuous.</span></span>  
  
 <span data-ttu-id="6861d-222">下列程序描述如何變更撥接中心資料內 Service Grade 值的分組方式。</span><span class="sxs-lookup"><span data-stu-id="6861d-222">The following procedure describes how to change the grouping of Service Grade values in the Call Center data.</span></span>  
  
##### <a name="to-create-a-discretized-version-of-the-call-center-mining-structure-and-models"></a><span data-ttu-id="6861d-223">建立離散化版本的客服中心採礦結構和模型</span><span class="sxs-lookup"><span data-stu-id="6861d-223">To create a discretized version of the Call Center mining structure and models</span></span>  
  
1.  <span data-ttu-id="6861d-224">在的 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 方案總管中，展開 [**採礦結構**]。</span><span class="sxs-lookup"><span data-stu-id="6861d-224">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Solution Explorer, expand **Mining Structures**.</span></span>  
  
2.  <span data-ttu-id="6861d-225">以滑鼠右鍵按一下 Call Center.dmm，然後選取 [複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6861d-225">Right-click Call Center.dmm and select **Copy**.</span></span>  
  
3.  <span data-ttu-id="6861d-226">以滑鼠右鍵按一下 [採礦結構]\*\*\*\* 並選取 [貼上]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6861d-226">Right click **Mining Structures** and select **Paste**.</span></span> <span data-ttu-id="6861d-227">如此就會加入名為「話務中心 1」的新採礦結構。</span><span class="sxs-lookup"><span data-stu-id="6861d-227">A new mining structure iss added, named Call Center 1.</span></span>  
  
4.  <span data-ttu-id="6861d-228">以滑鼠右鍵按一下新的採礦結構並選取 [重新命名]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6861d-228">Right-click the new mining structure and select **Rename**.</span></span> <span data-ttu-id="6861d-229">輸入新的名稱： **話務中心離散化**。</span><span class="sxs-lookup"><span data-stu-id="6861d-229">Type the new name, **Call Center Discretized**.</span></span>  
  
5.  <span data-ttu-id="6861d-230">按兩下新採礦結構，以在設計師中開啟。</span><span class="sxs-lookup"><span data-stu-id="6861d-230">Double-click the new mining structure to open it in the designer.</span></span> <span data-ttu-id="6861d-231">請注意，所有的採礦模型都已進行複製，而且都具有延伸模組 1。</span><span class="sxs-lookup"><span data-stu-id="6861d-231">Notice that the mining models have all been copied as well, and all have the extension 1.</span></span> <span data-ttu-id="6861d-232">請暫時保留這些名稱。</span><span class="sxs-lookup"><span data-stu-id="6861d-232">Leave the names as is for now.</span></span>  
  
6.  <span data-ttu-id="6861d-233">在 [採礦結構]\*\*\*\* 索引標籤中，以滑鼠右鍵按一下 Service Grade 的資料行，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6861d-233">In the **Mining Structure** tab, right-click the column for Service Grade, and select **Properties**.</span></span>  
  
7.  <span data-ttu-id="6861d-234">將 `Content` 屬性從 [**連續**] 變更為 [**離散**化]。</span><span class="sxs-lookup"><span data-stu-id="6861d-234">Change the `Content` property from **Continuous** to **Discretized**.</span></span> <span data-ttu-id="6861d-235">將 `DiscretizationMethod` 屬性變更為 [**群集**]。</span><span class="sxs-lookup"><span data-stu-id="6861d-235">Change the `DiscretizationMethod` property to **Clusters**.</span></span> <span data-ttu-id="6861d-236">針對 DiscretizationBucketCount 輸入 **3**。</span><span class="sxs-lookup"><span data-stu-id="6861d-236">For Discretization BucketCount, type **3**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6861d-237">這些參數只用來說明此程序，並不一定會產生有效的模型。</span><span class="sxs-lookup"><span data-stu-id="6861d-237">These parameters are just used for illustrating the process, and do not necessarily produce a valid model,</span></span>  
  
8.  <span data-ttu-id="6861d-238">在 [採礦模型]\*\*\*\* 功能表中，選取 [處理採礦結構和所有模型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6861d-238">From the **Mining Model** menu, select **Process structure and all models**.</span></span>  
  
 <span data-ttu-id="6861d-239">下列範例查詢是以這個離散化模型為基礎，並且預測一週內指定之日期的服務等級，以及每個預測結果的機率。</span><span class="sxs-lookup"><span data-stu-id="6861d-239">The following sample query is based on this discretized model, and predicts the service grade for the specified day of the week, together with the probabilities for each predicted outcome.</span></span>  
  
```  
SELECT  
  (PredictHistogram([Call Center_LR 1].[Service Grade])) as [Predictions]  
FROM  
  [Call Center_LR 1]  
NATURAL PREDICTION JOIN  
(SELECT 'Saturday' AS [Day Of Week]) AS t    
```  
  
 <span data-ttu-id="6861d-240">預期的結果：</span><span class="sxs-lookup"><span data-stu-id="6861d-240">Expected results:</span></span>  
  
 <span data-ttu-id="6861d-241">**預測**</span><span class="sxs-lookup"><span data-stu-id="6861d-241">**Predictions**</span></span>  
  
|<span data-ttu-id="6861d-242">服務等級</span><span class="sxs-lookup"><span data-stu-id="6861d-242">Service Grade</span></span>|<span data-ttu-id="6861d-243">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="6861d-243">$SUPPORT</span></span>|<span data-ttu-id="6861d-244">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="6861d-244">$PROBABILITY</span></span>|<span data-ttu-id="6861d-245">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="6861d-245">$ADJUSTEDPROBABILITY</span></span>|<span data-ttu-id="6861d-246">$VARIANCE</span><span class="sxs-lookup"><span data-stu-id="6861d-246">$VARIANCE</span></span>|<span data-ttu-id="6861d-247">$STDEV</span><span class="sxs-lookup"><span data-stu-id="6861d-247">$STDEV</span></span>|  
|-------------------|--------------|------------------|--------------------------|---------------|------------|  
|<span data-ttu-id="6861d-248">0.10872718383125</span><span class="sxs-lookup"><span data-stu-id="6861d-248">0.10872718383125</span></span>|<span data-ttu-id="6861d-249">35.7246504770641</span><span class="sxs-lookup"><span data-stu-id="6861d-249">35.7246504770641</span></span>|<span data-ttu-id="6861d-250">0.425293458060287</span><span class="sxs-lookup"><span data-stu-id="6861d-250">0.425293458060287</span></span>|<span data-ttu-id="6861d-251">0.0170168360030293</span><span class="sxs-lookup"><span data-stu-id="6861d-251">0.0170168360030293</span></span>|<span data-ttu-id="6861d-252">0</span><span class="sxs-lookup"><span data-stu-id="6861d-252">0</span></span>|<span data-ttu-id="6861d-253">0</span><span class="sxs-lookup"><span data-stu-id="6861d-253">0</span></span>|  
|<span data-ttu-id="6861d-254">0.05855769230625</span><span class="sxs-lookup"><span data-stu-id="6861d-254">0.05855769230625</span></span>|<span data-ttu-id="6861d-255">31.7098880800703</span><span class="sxs-lookup"><span data-stu-id="6861d-255">31.7098880800703</span></span>|<span data-ttu-id="6861d-256">0.377498667619885</span><span class="sxs-lookup"><span data-stu-id="6861d-256">0.377498667619885</span></span>|<span data-ttu-id="6861d-257">0.020882020060454</span><span class="sxs-lookup"><span data-stu-id="6861d-257">0.020882020060454</span></span>|<span data-ttu-id="6861d-258">0</span><span class="sxs-lookup"><span data-stu-id="6861d-258">0</span></span>|<span data-ttu-id="6861d-259">0</span><span class="sxs-lookup"><span data-stu-id="6861d-259">0</span></span>|  
|<span data-ttu-id="6861d-260">0.170169491525</span><span class="sxs-lookup"><span data-stu-id="6861d-260">0.170169491525</span></span>|<span data-ttu-id="6861d-261">15.6109159883202</span><span class="sxs-lookup"><span data-stu-id="6861d-261">15.6109159883202</span></span>|<span data-ttu-id="6861d-262">0.185844237956192</span><span class="sxs-lookup"><span data-stu-id="6861d-262">0.185844237956192</span></span>|<span data-ttu-id="6861d-263">0.0661386571386049</span><span class="sxs-lookup"><span data-stu-id="6861d-263">0.0661386571386049</span></span>|<span data-ttu-id="6861d-264">0</span><span class="sxs-lookup"><span data-stu-id="6861d-264">0</span></span>|<span data-ttu-id="6861d-265">0</span><span class="sxs-lookup"><span data-stu-id="6861d-265">0</span></span>|  
||<span data-ttu-id="6861d-266">0.954545454545455</span><span class="sxs-lookup"><span data-stu-id="6861d-266">0.954545454545455</span></span>|<span data-ttu-id="6861d-267">0.0113636363636364</span><span class="sxs-lookup"><span data-stu-id="6861d-267">0.0113636363636364</span></span>|<span data-ttu-id="6861d-268">0.0113636363636364</span><span class="sxs-lookup"><span data-stu-id="6861d-268">0.0113636363636364</span></span>|<span data-ttu-id="6861d-269">0</span><span class="sxs-lookup"><span data-stu-id="6861d-269">0</span></span>|<span data-ttu-id="6861d-270">0</span><span class="sxs-lookup"><span data-stu-id="6861d-270">0</span></span>|  
  
 <span data-ttu-id="6861d-271">請注意，預測的結果已經依照指定的方式分組成三個類別。不過，這些分組是以資料中實際值的群集為基礎，而非您可能設定為商務目標的二進位值。</span><span class="sxs-lookup"><span data-stu-id="6861d-271">Note that the predicted outcomes have been grouped into three categories as specified; however, these groupings are based on the clustering of actual values in the data, not arbitrary values that you might set as business goals.</span></span>  
  
## <a name="list-of-prediction-functions"></a><span data-ttu-id="6861d-272">預測函數的清單</span><span class="sxs-lookup"><span data-stu-id="6861d-272">List of Prediction Functions</span></span>  
 <span data-ttu-id="6861d-273">所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 演算法都支援一組常用的函數。</span><span class="sxs-lookup"><span data-stu-id="6861d-273">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="6861d-274">不過， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 羅吉斯迴歸演算法支援下表所列出的其他函數。</span><span class="sxs-lookup"><span data-stu-id="6861d-274">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm supports the additional functions listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6861d-275">預測函數</span><span class="sxs-lookup"><span data-stu-id="6861d-275">Prediction Function</span></span>|<span data-ttu-id="6861d-276">使用量</span><span class="sxs-lookup"><span data-stu-id="6861d-276">Usage</span></span>|  
|[<span data-ttu-id="6861d-277">IsDescendant &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6861d-277">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="6861d-278">確定某個節點是否為模型中另一個節點的子系。</span><span class="sxs-lookup"><span data-stu-id="6861d-278">Determines whether one node is a child of another node in the model.</span></span>|  
|[<span data-ttu-id="6861d-279">PredictAdjustedProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6861d-279">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="6861d-280">傳回指定狀態的已調整機率。</span><span class="sxs-lookup"><span data-stu-id="6861d-280">Returns the adjusted probability of a specified state.</span></span>|  
|[<span data-ttu-id="6861d-281">PredictHistogram &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6861d-281">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="6861d-282">傳回指定之資料行的一個或一組預測值。</span><span class="sxs-lookup"><span data-stu-id="6861d-282">Returns a predicted value, or set of values, for a specified column.</span></span>|  
|[<span data-ttu-id="6861d-283">PredictProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6861d-283">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="6861d-284">傳回指定狀態的機率。</span><span class="sxs-lookup"><span data-stu-id="6861d-284">Returns the probability for a specified state.</span></span>|  
|[<span data-ttu-id="6861d-285">PredictStdev &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6861d-285">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="6861d-286">傳回預測值的標準差。</span><span class="sxs-lookup"><span data-stu-id="6861d-286">Returns standard deviation for the predicted value.</span></span>|  
|[<span data-ttu-id="6861d-287">PredictSupport &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6861d-287">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="6861d-288">傳回指定狀態的支援值。</span><span class="sxs-lookup"><span data-stu-id="6861d-288">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="6861d-289">PredictVariance &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6861d-289">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="6861d-290">傳回指定之資料行的變異數。</span><span class="sxs-lookup"><span data-stu-id="6861d-290">Returns the variance of a specified column.</span></span>|  
  
 <span data-ttu-id="6861d-291">如需所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 演算法通用函數的清單，請參閱[一般預測函數 &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx)。</span><span class="sxs-lookup"><span data-stu-id="6861d-291">For a list of the functions that are common to all [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, see [General Prediction Functions &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).</span></span> <span data-ttu-id="6861d-292">如需特定函數的語法，請參閱[資料採礦延伸模組 &#40;DMX&#41; 函數參考](/sql/dmx/data-mining-extensions-dmx-function-reference)。</span><span class="sxs-lookup"><span data-stu-id="6861d-292">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6861d-293">若是類神經網路與羅吉斯迴歸模型， [PredictSupport &#40;DMX&#41;](/sql/dmx/predictsupport-dmx) 函數會傳回代表整個模型之定型集大小的單一值。</span><span class="sxs-lookup"><span data-stu-id="6861d-293">For neural network and logistic regression models, the [PredictSupport &#40;DMX&#41;](/sql/dmx/predictsupport-dmx) function returns a single value that represents the size of the training set for the entire model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6861d-294">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6861d-294">See Also</span></span>  
 <span data-ttu-id="6861d-295">[資料採礦查詢](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="6861d-295">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="6861d-296">[Microsoft 羅吉斯回歸演算法](microsoft-logistic-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="6861d-296">[Microsoft Logistic Regression Algorithm](microsoft-logistic-regression-algorithm.md) </span></span>  
 <span data-ttu-id="6861d-297">[Microsoft 羅吉斯回歸演算法技術參考](microsoft-logistic-regression-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="6861d-297">[Microsoft Logistic Regression Algorithm Technical Reference](microsoft-logistic-regression-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="6861d-298">[羅吉斯回歸模型的採礦模型內容 &#40;Analysis Services 資料採礦&#41;](mining-model-content-for-logistic-regression-models.md) </span><span class="sxs-lookup"><span data-stu-id="6861d-298">[Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md) </span></span>  
 [<span data-ttu-id="6861d-299">第五課：建立類神經網路和羅吉斯迴歸模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="6861d-299">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
  
