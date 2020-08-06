---
title: 貝氏貝氏機率分類模型查詢範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- naive bayes model [Analysis Services]
- naive bayes algorithms [Analysis Services]
- content queries [DMX]
ms.assetid: e642bd7d-5afa-4dfb-8cca-4f84aadf61b0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9694826bf2f74daef7b6d024e51e31d4ee448671
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687361"
---
# <a name="naive-bayes-model-query-examples"></a><span data-ttu-id="7f223-102">貝式機率分類模型查詢範例</span><span class="sxs-lookup"><span data-stu-id="7f223-102">Naive Bayes Model Query Examples</span></span>
  <span data-ttu-id="7f223-103">當您針對資料採礦模型建立查詢時，可以建立內容查詢來提供有關分析期間所發現之模式的詳細資料，或是建立預測查詢來使用模型中的模式，為新的資料進行預測。</span><span class="sxs-lookup"><span data-stu-id="7f223-103">When you create a query against a data mining model, you can create either a content query, which provides details about the patterns discovered in analysis, or you can create a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="7f223-104">您也可以針對資料採礦結構描述資料列集使用查詢，藉以擷取有關模型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7f223-104">You can also retrieve metadata about the model by using a query against the data mining schema rowset.</span></span> <span data-ttu-id="7f223-105">本節說明如何針對以 Microsoft 貝氏機率分類演算法為基礎的模型來建立這些查詢。</span><span class="sxs-lookup"><span data-stu-id="7f223-105">This section explains how to create these queries for models that are based on the Microsoft Naive Bayes algorithm.</span></span>  
  
 <span data-ttu-id="7f223-106">**內容查詢**</span><span class="sxs-lookup"><span data-stu-id="7f223-106">**Content Queries**</span></span>  
  
 [<span data-ttu-id="7f223-107">使用 DMX 取得模型中繼資料</span><span class="sxs-lookup"><span data-stu-id="7f223-107">Getting model metadata by using DMX</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="7f223-108">擷取定型資料的摘要</span><span class="sxs-lookup"><span data-stu-id="7f223-108">Retrieving a summary of training data</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="7f223-109">尋找有關屬性的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="7f223-109">Finding more information about attributes</span></span>](#bkmk_Query3)  
  
 [<span data-ttu-id="7f223-110">使用系統預存程式</span><span class="sxs-lookup"><span data-stu-id="7f223-110">Using system stored procedures</span></span>](#bkmk_Query4)  
  
 <span data-ttu-id="7f223-111">**預測查詢**</span><span class="sxs-lookup"><span data-stu-id="7f223-111">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="7f223-112">使用單一查詢預測結果</span><span class="sxs-lookup"><span data-stu-id="7f223-112">Predicting outcomes using a singleton query</span></span>](#bkmk_Query5)  
  
 [<span data-ttu-id="7f223-113">取得含有機率和支援值的預測</span><span class="sxs-lookup"><span data-stu-id="7f223-113">Getting predictions with probability and support values</span></span>](#bkmk_Query6)  
  
 [<span data-ttu-id="7f223-114">預測關聯</span><span class="sxs-lookup"><span data-stu-id="7f223-114">Predicting associations</span></span>](#bkmk_Query7)  
  
## <a name="finding-information-about-a-naive-bayes-model"></a><span data-ttu-id="7f223-115">尋找有關貝式機率分類模型的資訊</span><span class="sxs-lookup"><span data-stu-id="7f223-115">Finding Information about a Naive Bayes Model</span></span>  
 <span data-ttu-id="7f223-116">貝氏機率分類模型的模型內容會提供定型資料中，有關值分佈的彙總資訊。</span><span class="sxs-lookup"><span data-stu-id="7f223-116">The model content of a Naive Bayes model provides aggregated information about the distribution of values in the training data.</span></span> <span data-ttu-id="7f223-117">您也可以針對資料採礦結構描述資料列集建立查詢，藉以擷取有關模型之中繼資料的資訊。</span><span class="sxs-lookup"><span data-stu-id="7f223-117">You can also retrieve information about the metadata of the model by creating queries against the data mining schema rowsets.</span></span>  
  
###  <a name="sample-query-1-getting-model-metadata-by-using-dmx"></a><a name="bkmk_Query1"></a> <span data-ttu-id="7f223-118">範例查詢 1：使用 DMX 取得模型中繼資料</span><span class="sxs-lookup"><span data-stu-id="7f223-118">Sample Query 1: Getting Model Metadata by Using DMX</span></span>  
 <span data-ttu-id="7f223-119">您可以查詢資料採礦結構描述資料列集來尋找模型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7f223-119">By querying the data mining schema rowset, you can find metadata for the model.</span></span> <span data-ttu-id="7f223-120">這可能包括建立模型的時間、上次處理模型的時間、模型所依據之採礦結構的名稱，以及用來當做可預測屬性之資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="7f223-120">This might include when the model was created, when the model was last processed, the name of the mining structure that the model is based on, and the name of the columns used as the predictable attribute.</span></span> <span data-ttu-id="7f223-121">您也可以傳回建立此模型時所使用的參數。</span><span class="sxs-lookup"><span data-stu-id="7f223-121">You can also return the parameters that were used when the model was created.</span></span>  
  
```  
SELECT MODEL_CATALOG, MODEL_NAME, DATE_CREATED, LAST_PROCESSED,  
SERVICE_NAME, PREDICTION_ENTITY, FILTER  
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_NaiveBayes_Filtered'  
```  
  
 <span data-ttu-id="7f223-122">範例結果：</span><span class="sxs-lookup"><span data-stu-id="7f223-122">Sample results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7f223-123">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7f223-123">MODEL_CATALOG</span></span>|<span data-ttu-id="7f223-124">AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="7f223-124">AdventureWorks</span></span>|  
|<span data-ttu-id="7f223-125">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="7f223-125">MODEL_NAME</span></span>|<span data-ttu-id="7f223-126">TM_NaiveBayes_Filtered</span><span class="sxs-lookup"><span data-stu-id="7f223-126">TM_NaiveBayes_Filtered</span></span>|  
|<span data-ttu-id="7f223-127">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="7f223-127">DATE_CREATED</span></span>|<span data-ttu-id="7f223-128">3/1/2008 19:15</span><span class="sxs-lookup"><span data-stu-id="7f223-128">3/1/2008 19:15</span></span>|  
|<span data-ttu-id="7f223-129">LAST_PROCESSED</span><span class="sxs-lookup"><span data-stu-id="7f223-129">LAST_PROCESSED</span></span>|<span data-ttu-id="7f223-130">3/2/2008 20:00</span><span class="sxs-lookup"><span data-stu-id="7f223-130">3/2/2008 20:00</span></span>|  
|<span data-ttu-id="7f223-131">SERVICE_NAME</span><span class="sxs-lookup"><span data-stu-id="7f223-131">SERVICE_NAME</span></span>|<span data-ttu-id="7f223-132">Microsoft_Naive_Bayes</span><span class="sxs-lookup"><span data-stu-id="7f223-132">Microsoft_Naive_Bayes</span></span>|  
|<span data-ttu-id="7f223-133">PREDICTION_ENTITY</span><span class="sxs-lookup"><span data-stu-id="7f223-133">PREDICTION_ENTITY</span></span>|<span data-ttu-id="7f223-134">Bike Buyer,Yearly Income</span><span class="sxs-lookup"><span data-stu-id="7f223-134">Bike Buyer,Yearly Income</span></span>|  
|<span data-ttu-id="7f223-135">FILTER</span><span class="sxs-lookup"><span data-stu-id="7f223-135">FILTER</span></span>|<span data-ttu-id="7f223-136">[Region] = 'Europe' OR [Region] = 'North America'</span><span class="sxs-lookup"><span data-stu-id="7f223-136">[Region] = 'Europe' OR [Region] = 'North America'</span></span>|  
  
 <span data-ttu-id="7f223-137">用於此範例的模型是以您在 [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)中建立的貝氏機率分類模型為基礎，但是透過加入另一個可預測屬性，並將篩選套用到定型資料來修改。</span><span class="sxs-lookup"><span data-stu-id="7f223-137">The model used for this example is based on the Naive Bayes model you create in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md), but was modified by adding a second predictable attribute and applying a filter to the training data.</span></span>  
  
###  <a name="sample-query-2-retrieving-a-summary-of-training-data"></a><a name="bkmk_Query2"></a> <span data-ttu-id="7f223-138">範例查詢 2：擷取定型資料的摘要</span><span class="sxs-lookup"><span data-stu-id="7f223-138">Sample Query 2: Retrieving a Summary of Training Data</span></span>  
 <span data-ttu-id="7f223-139">在貝氏機率分類模型中，臨界統計資料節點會儲存定型資料中，有關值分佈的彙總資訊。</span><span class="sxs-lookup"><span data-stu-id="7f223-139">In a Naive Bayes model, the marginal statistics node stores aggregated information about the distribution of values in the training data.</span></span> <span data-ttu-id="7f223-140">此摘要相當方便，而且您不必根據定型資料建立 SQL 查詢，就可以找到相同的資訊。</span><span class="sxs-lookup"><span data-stu-id="7f223-140">This summary is convenient and saves you from having to create SQL queries against the training data to find the same information.</span></span>  
  
 <span data-ttu-id="7f223-141">下列範例使用 DMX 內容查詢從節點 (NODE_TYPE = 24) 擷取資料。</span><span class="sxs-lookup"><span data-stu-id="7f223-141">The following example uses a DMX content query to retrieve the data from the node (NODE_TYPE = 24).</span></span> <span data-ttu-id="7f223-142">由於統計資料儲存在巢狀資料表中，因此，FLATTENED 關鍵字的用途是讓結果更容易檢視。</span><span class="sxs-lookup"><span data-stu-id="7f223-142">Because the statistics are stored in a nested table, the FLATTENED keyword is used to make the results easier to view.</span></span>  
  
```  
SELECT FLATTENED MODEL_NAME,  
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, [SUPPORT], [PROBABILITY], VALUETYPE FROM NODE_DISTRIBUTION) AS t  
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 26  
```  
  
> [!NOTE]  
>  <span data-ttu-id="7f223-143">您必須將 SUPPORT 和 PROBABILITY 資料行的名稱括在括號中，以便與相同名稱的「多維度運算式」(MDX) 保留關鍵字區別。</span><span class="sxs-lookup"><span data-stu-id="7f223-143">You must enclose the name of the columns, SUPPORT and PROBABILITY, in brackets to distinguish them from the Multidimensional Expressions (MDX) reserved keywords of the same names.</span></span>  
  
 <span data-ttu-id="7f223-144">部分結果：</span><span class="sxs-lookup"><span data-stu-id="7f223-144">Partial results:</span></span>  
  
|<span data-ttu-id="7f223-145">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="7f223-145">MODEL_NAME</span></span>|<span data-ttu-id="7f223-146">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="7f223-146">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="7f223-147">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="7f223-147">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="7f223-148">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="7f223-148">t.SUPPORT</span></span>|<span data-ttu-id="7f223-149">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="7f223-149">t.PROBABILITY</span></span>|<span data-ttu-id="7f223-150">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="7f223-150">t.VALUETYPE</span></span>|  
|-----------------|-----------------------|------------------------|---------------|-------------------|-----------------|  
|<span data-ttu-id="7f223-151">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="7f223-151">TM_NaiveBayes</span></span>|<span data-ttu-id="7f223-152">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="7f223-152">Bike Buyer</span></span>|<span data-ttu-id="7f223-153">Missing</span><span class="sxs-lookup"><span data-stu-id="7f223-153">Missing</span></span>|<span data-ttu-id="7f223-154">0</span><span class="sxs-lookup"><span data-stu-id="7f223-154">0</span></span>|<span data-ttu-id="7f223-155">0</span><span class="sxs-lookup"><span data-stu-id="7f223-155">0</span></span>|<span data-ttu-id="7f223-156">1</span><span class="sxs-lookup"><span data-stu-id="7f223-156">1</span></span>|  
|<span data-ttu-id="7f223-157">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="7f223-157">TM_NaiveBayes</span></span>|<span data-ttu-id="7f223-158">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="7f223-158">Bike Buyer</span></span>|<span data-ttu-id="7f223-159">0</span><span class="sxs-lookup"><span data-stu-id="7f223-159">0</span></span>|<span data-ttu-id="7f223-160">8869</span><span class="sxs-lookup"><span data-stu-id="7f223-160">8869</span></span>|<span data-ttu-id="7f223-161">0.507263784</span><span class="sxs-lookup"><span data-stu-id="7f223-161">0.507263784</span></span>|<span data-ttu-id="7f223-162">4</span><span class="sxs-lookup"><span data-stu-id="7f223-162">4</span></span>|  
|<span data-ttu-id="7f223-163">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="7f223-163">TM_NaiveBayes</span></span>|<span data-ttu-id="7f223-164">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="7f223-164">Bike Buyer</span></span>|<span data-ttu-id="7f223-165">1</span><span class="sxs-lookup"><span data-stu-id="7f223-165">1</span></span>|<span data-ttu-id="7f223-166">8615</span><span class="sxs-lookup"><span data-stu-id="7f223-166">8615</span></span>|<span data-ttu-id="7f223-167">0.492736216</span><span class="sxs-lookup"><span data-stu-id="7f223-167">0.492736216</span></span>|<span data-ttu-id="7f223-168">4</span><span class="sxs-lookup"><span data-stu-id="7f223-168">4</span></span>|  
|<span data-ttu-id="7f223-169">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="7f223-169">TM_NaiveBayes</span></span>|<span data-ttu-id="7f223-170">性別</span><span class="sxs-lookup"><span data-stu-id="7f223-170">Gender</span></span>|<span data-ttu-id="7f223-171">Missing</span><span class="sxs-lookup"><span data-stu-id="7f223-171">Missing</span></span>|<span data-ttu-id="7f223-172">0</span><span class="sxs-lookup"><span data-stu-id="7f223-172">0</span></span>|<span data-ttu-id="7f223-173">0</span><span class="sxs-lookup"><span data-stu-id="7f223-173">0</span></span>|<span data-ttu-id="7f223-174">1</span><span class="sxs-lookup"><span data-stu-id="7f223-174">1</span></span>|  
|<span data-ttu-id="7f223-175">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="7f223-175">TM_NaiveBayes</span></span>|<span data-ttu-id="7f223-176">性別</span><span class="sxs-lookup"><span data-stu-id="7f223-176">Gender</span></span>|<span data-ttu-id="7f223-177">F</span><span class="sxs-lookup"><span data-stu-id="7f223-177">F</span></span>|<span data-ttu-id="7f223-178">8656</span><span class="sxs-lookup"><span data-stu-id="7f223-178">8656</span></span>|<span data-ttu-id="7f223-179">0.495081217</span><span class="sxs-lookup"><span data-stu-id="7f223-179">0.495081217</span></span>|<span data-ttu-id="7f223-180">4</span><span class="sxs-lookup"><span data-stu-id="7f223-180">4</span></span>|  
|<span data-ttu-id="7f223-181">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="7f223-181">TM_NaiveBayes</span></span>|<span data-ttu-id="7f223-182">性別</span><span class="sxs-lookup"><span data-stu-id="7f223-182">Gender</span></span>|<span data-ttu-id="7f223-183">M</span><span class="sxs-lookup"><span data-stu-id="7f223-183">M</span></span>|<span data-ttu-id="7f223-184">8828</span><span class="sxs-lookup"><span data-stu-id="7f223-184">8828</span></span>|<span data-ttu-id="7f223-185">0.504918783</span><span class="sxs-lookup"><span data-stu-id="7f223-185">0.504918783</span></span>|<span data-ttu-id="7f223-186">4</span><span class="sxs-lookup"><span data-stu-id="7f223-186">4</span></span>|  
  
 <span data-ttu-id="7f223-187">例如，這些結果告訴您每個離散值 (VALUETYPE = 4) 的定型案例數目，以及針對遺漏值 (VALUETYPE = 1) 調整的計算機率。</span><span class="sxs-lookup"><span data-stu-id="7f223-187">For example, these results tell you the number of training cases for each discrete value (VALUETYPE = 4), together with the computed probability, adjusted for missing values (VALUETYPE = 1).</span></span>  
  
 <span data-ttu-id="7f223-188">如需貝氏機率分類模型之 NODE_DISTRIBUTION 資料表中所提供值的定義，請參閱 [貝氏機率分類模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="7f223-188">For a definition of the values provided in the NODE_DISTRIBUTION table in a Naive Bayes model, see [Mining Model Content for Naive Bayes Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md).</span></span> <span data-ttu-id="7f223-189">如需支援與機率計算如何受到遺漏值影響的詳細資訊，請參閱[遺漏值 &#40;Analysis Services - 資料採礦&#41;](missing-values-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="7f223-189">For more information about how support and probability calculations are affected by missing values, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
###  <a name="sample-query-3-finding-more-information-about-attributes"></a><a name="bkmk_Query3"></a> <span data-ttu-id="7f223-190">範例查詢 3：尋找有關屬性的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="7f223-190">Sample Query 3: Finding More Information about Attributes</span></span>  
 <span data-ttu-id="7f223-191">貝氏機率分類模型通常包含不同屬性之間關聯性的複雜資訊，檢視這些關聯性最簡單的方式就是使用 [Microsoft 貝氏機率分類檢視器](browse-a-model-using-the-microsoft-naive-bayes-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="7f223-191">Because a Naive Bayes model often contains complex information about the relationships among different attributes, the easiest way to view these relationships is to use the [Microsoft Naive Bayes Viewer](browse-a-model-using-the-microsoft-naive-bayes-viewer.md).</span></span> <span data-ttu-id="7f223-192">不過，您可以建立 DMX 查詢來傳回資料。</span><span class="sxs-lookup"><span data-stu-id="7f223-192">However, you can create DMX queries to return the data.</span></span>  
  
 <span data-ttu-id="7f223-193">下列範例顯示如何從模型傳回有關特定屬性 `Region`的資訊。</span><span class="sxs-lookup"><span data-stu-id="7f223-193">The following example shows how to return information from the model about a particular attribute, `Region`.</span></span>  
  
```  
SELECT NODE_TYPE, NODE_CAPTION,   
NODE_PROBABILITY, NODE_SUPPORT, MSOLAP_NODE_SCORE  
FROM TM_NaiveBayes.CONTENT  
WHERE ATTRIBUTE_NAME = 'Region'  
```  
  
 <span data-ttu-id="7f223-194">此查詢會傳回兩種類型的節點：代表輸入屬性 (NODE_TYPE = 10) 的節點，以及屬性 (NODE_TYPE = 11) 每個值的節點。</span><span class="sxs-lookup"><span data-stu-id="7f223-194">This query returns two types of nodes: the node that represents the input attribute (NODE_TYPE = 10), and nodes for each value of the attribute (NODE_TYPE = 11).</span></span> <span data-ttu-id="7f223-195">節點標題 (而非節點名稱) 用於識別節點，因為標題會同時顯示屬性名稱和屬性值。</span><span class="sxs-lookup"><span data-stu-id="7f223-195">The node caption is used to identify the node, rather than the node name, because the caption shows both the attribute name and attribute value.</span></span>  
  
|<span data-ttu-id="7f223-196">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="7f223-196">NODE_TYPE</span></span>|<span data-ttu-id="7f223-197">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="7f223-197">NODE_CAPTION</span></span>|<span data-ttu-id="7f223-198">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="7f223-198">NODE_PROBABILITY</span></span>|<span data-ttu-id="7f223-199">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="7f223-199">NODE_SUPPORT</span></span>|<span data-ttu-id="7f223-200">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="7f223-200">MSOLAP_NODE_SCORE</span></span>|<span data-ttu-id="7f223-201">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="7f223-201">NODE_TYPE</span></span>|  
|----------------|-------------------|-----------------------|-------------------|-------------------------|----------------|  
|<span data-ttu-id="7f223-202">10</span><span class="sxs-lookup"><span data-stu-id="7f223-202">10</span></span>|<span data-ttu-id="7f223-203">Bike Buyer -> Region</span><span class="sxs-lookup"><span data-stu-id="7f223-203">Bike Buyer -> Region</span></span>|<span data-ttu-id="7f223-204">1</span><span class="sxs-lookup"><span data-stu-id="7f223-204">1</span></span>|<span data-ttu-id="7f223-205">17484</span><span class="sxs-lookup"><span data-stu-id="7f223-205">17484</span></span>|<span data-ttu-id="7f223-206">84.51555875</span><span class="sxs-lookup"><span data-stu-id="7f223-206">84.51555875</span></span>|<span data-ttu-id="7f223-207">10</span><span class="sxs-lookup"><span data-stu-id="7f223-207">10</span></span>|  
|<span data-ttu-id="7f223-208">11</span><span class="sxs-lookup"><span data-stu-id="7f223-208">11</span></span>|<span data-ttu-id="7f223-209">Bike Buyer -> Region = Missing</span><span class="sxs-lookup"><span data-stu-id="7f223-209">Bike Buyer -> Region = Missing</span></span>|<span data-ttu-id="7f223-210">0</span><span class="sxs-lookup"><span data-stu-id="7f223-210">0</span></span>|<span data-ttu-id="7f223-211">0</span><span class="sxs-lookup"><span data-stu-id="7f223-211">0</span></span>|<span data-ttu-id="7f223-212">0</span><span class="sxs-lookup"><span data-stu-id="7f223-212">0</span></span>|<span data-ttu-id="7f223-213">11</span><span class="sxs-lookup"><span data-stu-id="7f223-213">11</span></span>|  
|<span data-ttu-id="7f223-214">11</span><span class="sxs-lookup"><span data-stu-id="7f223-214">11</span></span>|<span data-ttu-id="7f223-215">Bike Buyer -> Region = North America</span><span class="sxs-lookup"><span data-stu-id="7f223-215">Bike Buyer -> Region = North America</span></span>|<span data-ttu-id="7f223-216">0.508236102</span><span class="sxs-lookup"><span data-stu-id="7f223-216">0.508236102</span></span>|<span data-ttu-id="7f223-217">8886</span><span class="sxs-lookup"><span data-stu-id="7f223-217">8886</span></span>|<span data-ttu-id="7f223-218">0</span><span class="sxs-lookup"><span data-stu-id="7f223-218">0</span></span>|<span data-ttu-id="7f223-219">11</span><span class="sxs-lookup"><span data-stu-id="7f223-219">11</span></span>|  
|<span data-ttu-id="7f223-220">11</span><span class="sxs-lookup"><span data-stu-id="7f223-220">11</span></span>|<span data-ttu-id="7f223-221">Bike Buyer -> Region = Pacific</span><span class="sxs-lookup"><span data-stu-id="7f223-221">Bike Buyer -> Region = Pacific</span></span>|<span data-ttu-id="7f223-222">0.193891558</span><span class="sxs-lookup"><span data-stu-id="7f223-222">0.193891558</span></span>|<span data-ttu-id="7f223-223">3390</span><span class="sxs-lookup"><span data-stu-id="7f223-223">3390</span></span>|<span data-ttu-id="7f223-224">0</span><span class="sxs-lookup"><span data-stu-id="7f223-224">0</span></span>|<span data-ttu-id="7f223-225">11</span><span class="sxs-lookup"><span data-stu-id="7f223-225">11</span></span>|  
|<span data-ttu-id="7f223-226">11</span><span class="sxs-lookup"><span data-stu-id="7f223-226">11</span></span>|<span data-ttu-id="7f223-227">Bike Buyer -> Region = Europe</span><span class="sxs-lookup"><span data-stu-id="7f223-227">Bike Buyer -> Region = Europe</span></span>|<span data-ttu-id="7f223-228">0.29787234</span><span class="sxs-lookup"><span data-stu-id="7f223-228">0.29787234</span></span>|<span data-ttu-id="7f223-229">5208</span><span class="sxs-lookup"><span data-stu-id="7f223-229">5208</span></span>|<span data-ttu-id="7f223-230">0</span><span class="sxs-lookup"><span data-stu-id="7f223-230">0</span></span>|<span data-ttu-id="7f223-231">11</span><span class="sxs-lookup"><span data-stu-id="7f223-231">11</span></span>|  
  
 <span data-ttu-id="7f223-232">儲存在節點中的某些資料行與您可以從臨界統計資料節點中取得的資料行相同，例如，節點機率分數與節點支援值。</span><span class="sxs-lookup"><span data-stu-id="7f223-232">Some of the columns stored in the nodes are the same that you can get from the marginal statistics nodes, such as the node probability score and the node support values.</span></span> <span data-ttu-id="7f223-233">不過，MSOLAP_NODE_SCORE 是僅針對輸入屬性節點提供的特別值，表示此屬性在模型中的相對重要性。</span><span class="sxs-lookup"><span data-stu-id="7f223-233">However, the MSOLAP_NODE_SCORE is a special value provided only for the input attribute nodes, and indicates the relative importance of this attribute in the model.</span></span> <span data-ttu-id="7f223-234">您可以在檢視器的 [相依性網路] 窗格中看到很多相同的資訊，但是，此檢視器不提供分數。</span><span class="sxs-lookup"><span data-stu-id="7f223-234">You can see much the same information in the Dependency Network pane of the viewer; however, the viewer does not provide scores.</span></span>  
  
 <span data-ttu-id="7f223-235">下列查詢會傳回所有屬性在模型中的重要性分數：</span><span class="sxs-lookup"><span data-stu-id="7f223-235">The following query returns the importance scores of all attributes in the model:</span></span>  
  
```  
SELECT NODE_CAPTION, MSOLAP_NODE_SCORE  
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 10  
ORDER BY MSOLAP_NODE_SCORE DESC  
```  
  
 <span data-ttu-id="7f223-236">範例結果：</span><span class="sxs-lookup"><span data-stu-id="7f223-236">Sample results:</span></span>  
  
|<span data-ttu-id="7f223-237">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="7f223-237">NODE_CAPTION</span></span>|<span data-ttu-id="7f223-238">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="7f223-238">MSOLAP_NODE_SCORE</span></span>|  
|-------------------|-------------------------|  
|<span data-ttu-id="7f223-239">Bike Buyer -> Total Children</span><span class="sxs-lookup"><span data-stu-id="7f223-239">Bike Buyer -> Total Children</span></span>|<span data-ttu-id="7f223-240">181.3654836</span><span class="sxs-lookup"><span data-stu-id="7f223-240">181.3654836</span></span>|  
|<span data-ttu-id="7f223-241">Bike Buyer -> Commute Distance</span><span class="sxs-lookup"><span data-stu-id="7f223-241">Bike Buyer -> Commute Distance</span></span>|<span data-ttu-id="7f223-242">179.8419482</span><span class="sxs-lookup"><span data-stu-id="7f223-242">179.8419482</span></span>|  
|<span data-ttu-id="7f223-243">Bike Buyer -> English Education</span><span class="sxs-lookup"><span data-stu-id="7f223-243">Bike Buyer -> English Education</span></span>|<span data-ttu-id="7f223-244">156.9841928</span><span class="sxs-lookup"><span data-stu-id="7f223-244">156.9841928</span></span>|  
|<span data-ttu-id="7f223-245">Bike Buyer -> Number Children At Home</span><span class="sxs-lookup"><span data-stu-id="7f223-245">Bike Buyer -> Number Children At Home</span></span>|<span data-ttu-id="7f223-246">111.8122599</span><span class="sxs-lookup"><span data-stu-id="7f223-246">111.8122599</span></span>|  
|<span data-ttu-id="7f223-247">Bike Buyer -> Region</span><span class="sxs-lookup"><span data-stu-id="7f223-247">Bike Buyer -> Region</span></span>|<span data-ttu-id="7f223-248">84.51555875</span><span class="sxs-lookup"><span data-stu-id="7f223-248">84.51555875</span></span>|  
|<span data-ttu-id="7f223-249">Bike Buyer -> Marital Status</span><span class="sxs-lookup"><span data-stu-id="7f223-249">Bike Buyer -> Marital Status</span></span>|<span data-ttu-id="7f223-250">23.13297354</span><span class="sxs-lookup"><span data-stu-id="7f223-250">23.13297354</span></span>|  
|<span data-ttu-id="7f223-251">Bike Buyer -> English Occupation</span><span class="sxs-lookup"><span data-stu-id="7f223-251">Bike Buyer -> English Occupation</span></span>|<span data-ttu-id="7f223-252">2.832069191</span><span class="sxs-lookup"><span data-stu-id="7f223-252">2.832069191</span></span>|  
  
 <span data-ttu-id="7f223-253">透過在 [Microsoft 一般內容樹狀檢視器](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)中瀏覽模型內容，您將會更為了解哪些統計資料可能是有趣的。</span><span class="sxs-lookup"><span data-stu-id="7f223-253">By browsing the model content in the [Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md), you will get a better idea of what statistics might be interesting.</span></span> <span data-ttu-id="7f223-254">此處會示範一些簡單的案例；您可能需要更常執行多個查詢，或在用戶端上儲存結果並進行處理。</span><span class="sxs-lookup"><span data-stu-id="7f223-254">Some simple examples were demonstrated here; more often you may need to execute multiple queries or store the results and process them on the client.</span></span>  
  
###  <a name="sample-query-4-using-system-stored-procedures"></a><a name="bkmk_Query4"></a> <span data-ttu-id="7f223-255">範例查詢 4：使用系統預存程序</span><span class="sxs-lookup"><span data-stu-id="7f223-255">Sample Query 4: Using System Stored Procedures</span></span>  
 <span data-ttu-id="7f223-256">除了撰寫您自己的內容查詢之外，您也可以使用某些 Analysis Services 系統預存程序瀏覽結果。</span><span class="sxs-lookup"><span data-stu-id="7f223-256">In addition to writing your own content queries, you can use some Analysis Services system stored procedures to explore the results.</span></span> <span data-ttu-id="7f223-257">若要使用系統預存程序，在預存程序名稱開頭加上 CALL 關鍵字：</span><span class="sxs-lookup"><span data-stu-id="7f223-257">To use a system stored procedure, prefix the stored procedure name with the CALL keyword:</span></span>  
  
```  
CALL GetPredictableAttributes ('TM_NaiveBayes')  
```  
  
 <span data-ttu-id="7f223-258">部分結果：</span><span class="sxs-lookup"><span data-stu-id="7f223-258">Partial results:</span></span>  
  
|<span data-ttu-id="7f223-259">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="7f223-259">ATTRIBUTE_NAME</span></span>|<span data-ttu-id="7f223-260">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="7f223-260">NODE_UNIQUE_NAME</span></span>|  
|---------------------|------------------------|  
|<span data-ttu-id="7f223-261">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="7f223-261">Bike Buyer</span></span>|<span data-ttu-id="7f223-262">100000001</span><span class="sxs-lookup"><span data-stu-id="7f223-262">100000001</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="7f223-263">這些系統預存程序供 Analysis Services 伺服器與用戶端之間的內部通訊使用，而只是為了方便而在開發和測試採礦模型時使用。</span><span class="sxs-lookup"><span data-stu-id="7f223-263">These system stored procedures are for internal communication between the Analysis Services server and the client and should only be used for convenience when developing and testing mining models.</span></span> <span data-ttu-id="7f223-264">當您為實際系統建立查詢時，應該一律使用 DMX 撰寫您自己的查詢。</span><span class="sxs-lookup"><span data-stu-id="7f223-264">When you create queries for a production system, you should always write your own queries by using DMX.</span></span>  
  
 <span data-ttu-id="7f223-265">如需 Analysis Services 系統預存程序的詳細資訊，請參閱[資料採礦預存程序 &#40;Analysis Services - 資料採礦&#41;](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining)。</span><span class="sxs-lookup"><span data-stu-id="7f223-265">For more information about Analysis Services system stored procedures, see [Data Mining Stored Procedures &#40;Analysis Services - Data Mining&#41;](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining).</span></span>  
  
## <a name="using-a-naive-bayes-model-to-make-predictions"></a><span data-ttu-id="7f223-266">使用貝式機率分類模型進行預測</span><span class="sxs-lookup"><span data-stu-id="7f223-266">Using a Naive Bayes Model to Make Predictions</span></span>  
 <span data-ttu-id="7f223-267">Microsoft 貝氏機率分類演算法用於預測的頻率通常比用於瀏覽輸入屬性和可預測屬性之間關聯性的頻率低。</span><span class="sxs-lookup"><span data-stu-id="7f223-267">The Microsoft Naive Bayes algorithm is typically used less for prediction than it is for exploration of relationships among the input and predictable attributes.</span></span> <span data-ttu-id="7f223-268">不過，此模型支援同時針對預測和關聯使用預測函數。</span><span class="sxs-lookup"><span data-stu-id="7f223-268">However, the model supports the use of prediction functions for both prediction and association.</span></span>  
  
###  <a name="sample-query-5-predicting-outcomes-using-a-singleton-query"></a><a name="bkmk_Query5"></a> <span data-ttu-id="7f223-269">範例查詢 5：使用單一查詢預測結果</span><span class="sxs-lookup"><span data-stu-id="7f223-269">Sample Query 5: Predicting Outcomes using a Singleton Query</span></span>  
 <span data-ttu-id="7f223-270">下列查詢使用單一查詢提供新的值，並根據模型預測具備這些特徵的客戶是否可能購買自行車。</span><span class="sxs-lookup"><span data-stu-id="7f223-270">The following query uses a singleton query to provide a new value and predict, based on the model, whether a customer with these characteristics is likely to buy a bike.</span></span> <span data-ttu-id="7f223-271">在迴歸模型上建立單一查詢最簡單的方式是使用 **[單一查詢輸入]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7f223-271">The easiest way to create a singleton query on a regression model is by using the **Singleton Query Input** dialog box.</span></span> <span data-ttu-id="7f223-272">例如，您可以選取 `TM_NaiveBayes` 模型、選擇 **[單一查詢]**，然後從 `[Commute Distance]` 和 `Gender`的下拉式清單選取值來建立下列 DMX 查詢。</span><span class="sxs-lookup"><span data-stu-id="7f223-272">For example, you can build the following DMX query by selecting the `TM_NaiveBayes` model, choosing **Singleton Query**, and selecting values from the dropdown lists for `[Commute Distance]` and `Gender`.</span></span>  
  
```  
SELECT  
  Predict([TM_NaiveBayes].[Bike Buyer])  
FROM  
  [TM_NaiveBayes]  
NATURAL PREDICTION JOIN  
(SELECT '5-10 Miles' AS [Commute Distance],  
  'F' AS [Gender]) AS t  
```  
  
 <span data-ttu-id="7f223-273">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="7f223-273">Example results:</span></span>  
  
|<span data-ttu-id="7f223-274">運算是</span><span class="sxs-lookup"><span data-stu-id="7f223-274">Expression</span></span>|  
|----------------|  
|<span data-ttu-id="7f223-275">0</span><span class="sxs-lookup"><span data-stu-id="7f223-275">0</span></span>|  
  
 <span data-ttu-id="7f223-276">預測函數會傳回最可能的值，在此範例中為 0，也就是說，此類型的客戶不太可能購買自行車。</span><span class="sxs-lookup"><span data-stu-id="7f223-276">The prediction function returns the most likely value, in this case, 0, which means this type of customer is unlikely to purchase a bike.</span></span>  
  
###  <a name="sample-query-6-getting-predictions-with-probability-and-support-values"></a><a name="bkmk_Query6"></a><span data-ttu-id="7f223-277">範例查詢6：取得具有機率和支援值的預測</span><span class="sxs-lookup"><span data-stu-id="7f223-277">Sample Query 6: Getting Predictions with Probability and Support Values</span></span>  
 <span data-ttu-id="7f223-278">除了預測結果之外，您通常還想要知道預測的可能性。</span><span class="sxs-lookup"><span data-stu-id="7f223-278">In addition to predicting an outcome, you often want to know how strong the prediction is.</span></span> <span data-ttu-id="7f223-279">下列查詢使用與先前範例相同的單一查詢，但是加入預測函數 ([PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx)) 來傳回包含支援預測之統計資料的巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="7f223-279">The following query uses the same singleton query as the previous example, but adds the prediction function, [PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx), to return a nested table that contains statistics in support of the prediction.</span></span>  
  
```  
SELECT  
  Predict([TM_NaiveBayes].[Bike Buyer]),  
  PredictHistogram([TM_NaiveBayes].[Bike Buyer])  
FROM  
  [TM_NaiveBayes]  
NATURAL PREDICTION JOIN  
(SELECT '5-10 Miles' AS [Commute Distance],  
  'F' AS [Gender]) AS t  
```  
  
 <span data-ttu-id="7f223-280">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="7f223-280">Example results:</span></span>  
  
|<span data-ttu-id="7f223-281">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="7f223-281">Bike Buyer</span></span>|<span data-ttu-id="7f223-282">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="7f223-282">$SUPPORT</span></span>|<span data-ttu-id="7f223-283">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="7f223-283">$PROBABILITY</span></span>|<span data-ttu-id="7f223-284">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="7f223-284">$ADJUSTEDPROBABILITY</span></span>|<span data-ttu-id="7f223-285">$VARIANCE</span><span class="sxs-lookup"><span data-stu-id="7f223-285">$VARIANCE</span></span>|<span data-ttu-id="7f223-286">$STDEV</span><span class="sxs-lookup"><span data-stu-id="7f223-286">$STDEV</span></span>|  
|----------------|--------------|------------------|--------------------------|---------------|------------|  
|<span data-ttu-id="7f223-287">0</span><span class="sxs-lookup"><span data-stu-id="7f223-287">0</span></span>|<span data-ttu-id="7f223-288">10161.5714</span><span class="sxs-lookup"><span data-stu-id="7f223-288">10161.5714</span></span>|<span data-ttu-id="7f223-289">0.581192599</span><span class="sxs-lookup"><span data-stu-id="7f223-289">0.581192599</span></span>|<span data-ttu-id="7f223-290">0.010530981</span><span class="sxs-lookup"><span data-stu-id="7f223-290">0.010530981</span></span>|<span data-ttu-id="7f223-291">0</span><span class="sxs-lookup"><span data-stu-id="7f223-291">0</span></span>|<span data-ttu-id="7f223-292">0</span><span class="sxs-lookup"><span data-stu-id="7f223-292">0</span></span>|  
|<span data-ttu-id="7f223-293">1</span><span class="sxs-lookup"><span data-stu-id="7f223-293">1</span></span>|<span data-ttu-id="7f223-294">7321.428768</span><span class="sxs-lookup"><span data-stu-id="7f223-294">7321.428768</span></span>|<span data-ttu-id="7f223-295">0.418750215</span><span class="sxs-lookup"><span data-stu-id="7f223-295">0.418750215</span></span>|<span data-ttu-id="7f223-296">0.008945684</span><span class="sxs-lookup"><span data-stu-id="7f223-296">0.008945684</span></span>|<span data-ttu-id="7f223-297">0</span><span class="sxs-lookup"><span data-stu-id="7f223-297">0</span></span>|<span data-ttu-id="7f223-298">0</span><span class="sxs-lookup"><span data-stu-id="7f223-298">0</span></span>|  
||<span data-ttu-id="7f223-299">0.999828444</span><span class="sxs-lookup"><span data-stu-id="7f223-299">0.999828444</span></span>|<span data-ttu-id="7f223-300">5.72E-05</span><span class="sxs-lookup"><span data-stu-id="7f223-300">5.72E-05</span></span>|<span data-ttu-id="7f223-301">5.72E-05</span><span class="sxs-lookup"><span data-stu-id="7f223-301">5.72E-05</span></span>|<span data-ttu-id="7f223-302">0</span><span class="sxs-lookup"><span data-stu-id="7f223-302">0</span></span>|<span data-ttu-id="7f223-303">0</span><span class="sxs-lookup"><span data-stu-id="7f223-303">0</span></span>|  
  
 <span data-ttu-id="7f223-304">資料表中的最後一個資料列會顯示支援與機率針對遺漏值所做的調整。</span><span class="sxs-lookup"><span data-stu-id="7f223-304">The final row in the table shows the adjustments to support and probability for the missing value.</span></span> <span data-ttu-id="7f223-305">變異數和標準差永遠為 0，因為貝氏機率分類模型無法製作連續值的模型。</span><span class="sxs-lookup"><span data-stu-id="7f223-305">Variance and standard deviation values are always 0, because Naive Bayes models cannot model continuous values.</span></span>  
  
###  <a name="sample-query-7-predicting-associations"></a><a name="bkmk_Query7"></a><span data-ttu-id="7f223-306">範例查詢7：預測關聯</span><span class="sxs-lookup"><span data-stu-id="7f223-306">Sample Query 7: Predicting Associations</span></span>  
 <span data-ttu-id="7f223-307">如果採礦結構包含巢狀資料表與當做索引鍵的可預測屬性，Microsoft 貝氏機率分類演算法可以用於關聯分析。</span><span class="sxs-lookup"><span data-stu-id="7f223-307">The Microsoft Naive Bayes algorithm can be used for association analysis, if the mining structure contains a nested table with the predictable attribute as the key.</span></span> <span data-ttu-id="7f223-308">例如，您可以使用在資料採礦教學課程之[第 3 課：建立購物籃狀況 &#40;中繼資料採礦教學課程&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md) 中所建立的採礦結構來建立貝氏機率分類模型。</span><span class="sxs-lookup"><span data-stu-id="7f223-308">For example, you could build a Naive Bayes model by using the mining structure created in [Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md) of the data mining tutorial.</span></span> <span data-ttu-id="7f223-309">此範例中所使用的模型會遭到修改，以便在案例資料表中加入有關收入和客戶地區的資訊。</span><span class="sxs-lookup"><span data-stu-id="7f223-309">The model used in this example was modified to add information about income and customer region in the case table.</span></span>  
  
 <span data-ttu-id="7f223-310">下列查詢範例顯示的單一查詢會預測與購買產品 `'Road Tire Tube'`相關的產品。</span><span class="sxs-lookup"><span data-stu-id="7f223-310">The following query example shows a singleton query that predicts products that are related to purchases of the product, `'Road Tire Tube'`.</span></span> <span data-ttu-id="7f223-311">您可以使用這項資訊提供產品建議給特定類型的客戶。</span><span class="sxs-lookup"><span data-stu-id="7f223-311">You might use this information to recommend products to a specific type of customer.</span></span>  
  
```  
SELECT   PredictAssociation([Association].[v Assoc Seq Line Items])  
FROM [Association_NB]  
NATURAL PREDICTION JOIN  
(SELECT 'High' AS [Income Group],  
  'Europe' AS [Region],  
  (SELECT 'Road Tire Tube' AS [Model])   
AS [v Assoc Seq Line Items])   
AS t  
```  
  
 <span data-ttu-id="7f223-312">部分結果：</span><span class="sxs-lookup"><span data-stu-id="7f223-312">Partial results:</span></span>  
  
|<span data-ttu-id="7f223-313">模型</span><span class="sxs-lookup"><span data-stu-id="7f223-313">Model</span></span>|  
|-----------|  
|<span data-ttu-id="7f223-314">Women's Mountain Shorts</span><span class="sxs-lookup"><span data-stu-id="7f223-314">Women's Mountain Shorts</span></span>|  
|<span data-ttu-id="7f223-315">Water Bottle</span><span class="sxs-lookup"><span data-stu-id="7f223-315">Water Bottle</span></span>|  
|<span data-ttu-id="7f223-316">Touring-3000</span><span class="sxs-lookup"><span data-stu-id="7f223-316">Touring-3000</span></span>|  
|<span data-ttu-id="7f223-317">Touring-2000</span><span class="sxs-lookup"><span data-stu-id="7f223-317">Touring-2000</span></span>|  
|<span data-ttu-id="7f223-318">Touring-1000</span><span class="sxs-lookup"><span data-stu-id="7f223-318">Touring-1000</span></span>|  
  
## <a name="function-list"></a><span data-ttu-id="7f223-319">函數清單</span><span class="sxs-lookup"><span data-stu-id="7f223-319">Function List</span></span>  
 <span data-ttu-id="7f223-320">所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 演算法都支援一組常用的函數。</span><span class="sxs-lookup"><span data-stu-id="7f223-320">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="7f223-321">不過， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 貝氏機率分類演算法支援下表所列出的其他函數。</span><span class="sxs-lookup"><span data-stu-id="7f223-321">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm supports the additional functions that are listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7f223-322">預測函數</span><span class="sxs-lookup"><span data-stu-id="7f223-322">Prediction Function</span></span>|<span data-ttu-id="7f223-323">使用量</span><span class="sxs-lookup"><span data-stu-id="7f223-323">Usage</span></span>|  
|[<span data-ttu-id="7f223-324">IsDescendant &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="7f223-324">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="7f223-325">確定某個節點是否為模型中另一個節點的子系。</span><span class="sxs-lookup"><span data-stu-id="7f223-325">Determines whether one node is a child of another node in the model.</span></span>|  
|[<span data-ttu-id="7f223-326">Predict &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="7f223-326">Predict &#40;DMX&#41;</span></span>](/sql/dmx/predict-dmx)|<span data-ttu-id="7f223-327">傳回指定之資料行的一個或一組預測值。</span><span class="sxs-lookup"><span data-stu-id="7f223-327">Returns a predicted value, or set of values, for a specified column.</span></span>|  
|[<span data-ttu-id="7f223-328">PredictAdjustedProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="7f223-328">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="7f223-329">傳回加權機率。</span><span class="sxs-lookup"><span data-stu-id="7f223-329">Returns the weighted probability.</span></span>|  
|[<span data-ttu-id="7f223-330">PredictAssociation &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="7f223-330">PredictAssociation &#40;DMX&#41;</span></span>](/sql/dmx/predictassociation-dmx)|<span data-ttu-id="7f223-331">預測關聯資料集的成員資格。</span><span class="sxs-lookup"><span data-stu-id="7f223-331">Predicts membership in an associative dataset.</span></span>|  
|[<span data-ttu-id="7f223-332">PredictNodeId &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="7f223-332">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="7f223-333">傳回每個案例的 Node_ID。</span><span class="sxs-lookup"><span data-stu-id="7f223-333">Returns the Node_ID for each case.</span></span>|  
|[<span data-ttu-id="7f223-334">PredictProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="7f223-334">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="7f223-335">傳回預測值的機率。</span><span class="sxs-lookup"><span data-stu-id="7f223-335">Returns probability for the predicted value.</span></span>|  
|[<span data-ttu-id="7f223-336">PredictSupport &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="7f223-336">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="7f223-337">傳回指定狀態的支援值。</span><span class="sxs-lookup"><span data-stu-id="7f223-337">Returns the support value for a specified state.</span></span>|  
  
 <span data-ttu-id="7f223-338">若要查看特定函數的語法，請參閱[資料採礦延伸模組 &#40;DMX&#41; 函數參考](/sql/dmx/data-mining-extensions-dmx-function-reference)。</span><span class="sxs-lookup"><span data-stu-id="7f223-338">To see  the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f223-339">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f223-339">See Also</span></span>  
 <span data-ttu-id="7f223-340">[Microsoft 貝氏貝氏機率分類演算法技術參考](microsoft-naive-bayes-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="7f223-340">[Microsoft Naive Bayes Algorithm Technical Reference](microsoft-naive-bayes-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="7f223-341">[Microsoft 貝氏貝氏機率分類演算法](microsoft-naive-bayes-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="7f223-341">[Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md) </span></span>  
 [<span data-ttu-id="7f223-342">貝氏機率分類模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="7f223-342">Mining Model Content for Naive Bayes Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)  
  
  
