---
title: 類神經網路模型查詢範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- neural network algorithms [Analysis Services]
- content queries [DMX]
- neural network model [Analysis Services]
ms.assetid: 81b06183-620f-4e0c-bc10-532e6a1f0829
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7154ce0ad66346634225734fe829c36e7bf3ad58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703466"
---
# <a name="neural-network-model-query-examples"></a><span data-ttu-id="a1fbf-102">類神經網路模型查詢範例</span><span class="sxs-lookup"><span data-stu-id="a1fbf-102">Neural Network Model Query Examples</span></span>
  <span data-ttu-id="a1fbf-103">當您針對資料採礦模型建立查詢時，可以建立內容查詢來提供有關分析期間所發現之模式的詳細資料，或是建立預測查詢來使用模型中的模式，為新的資料進行預測。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-103">When you create a query against a data mining model, you can create a content query, which provides details about the patterns discovered in analysis, or a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="a1fbf-104">例如，類神經網路模型的內容查詢可以擷取模型中繼資料，例如，隱藏層的數目。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-104">For example, a content query for a neural network model might retrieve model metadata such as the number of hidden layers.</span></span> <span data-ttu-id="a1fbf-105">或者，預測查詢可以根據輸入建議分類，並選擇性地提供每個分類的機率。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-105">Alternatively, a prediction query might suggest classifications based on an input and optionally provide probabilities for each classification.</span></span>  
  
 <span data-ttu-id="a1fbf-106">本節說明如何針對以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 類神經網路演算法為基礎的模型來建立查詢。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-106">This section explains how to create queries for models that are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm.</span></span>  
  
 <span data-ttu-id="a1fbf-107">**內容查詢**</span><span class="sxs-lookup"><span data-stu-id="a1fbf-107">**Content queries**</span></span>  
  
 [<span data-ttu-id="a1fbf-108">使用 DMX 取得模型中繼資料</span><span class="sxs-lookup"><span data-stu-id="a1fbf-108">Getting Model Metadata by Using DMX</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="a1fbf-109">從結構描述資料列集擷取模型中繼資料</span><span class="sxs-lookup"><span data-stu-id="a1fbf-109">Retrieving Model Metadata from the Schema Rowset</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="a1fbf-110">擷取模型的輸入屬性</span><span class="sxs-lookup"><span data-stu-id="a1fbf-110">Retrieving the Input Attributes for the Model</span></span>](#bkmk_Query3)  
  
 [<span data-ttu-id="a1fbf-111">從隱藏層擷取加權</span><span class="sxs-lookup"><span data-stu-id="a1fbf-111">Retrieving Weights from the Hidden Layer</span></span>](#bkmk_Query4)  
  
 <span data-ttu-id="a1fbf-112">**預測查詢**</span><span class="sxs-lookup"><span data-stu-id="a1fbf-112">**Prediction queries**</span></span>  
  
 [<span data-ttu-id="a1fbf-113">建立單一預測</span><span class="sxs-lookup"><span data-stu-id="a1fbf-113">Creating a Singleton Prediction</span></span>](#bkmk_Query5)  
  
## <a name="finding-information-about-a-neural-network-model"></a><span data-ttu-id="a1fbf-114">尋找有關類神經網路模型的資訊</span><span class="sxs-lookup"><span data-stu-id="a1fbf-114">Finding Information about a Neural Network Model</span></span>  
 <span data-ttu-id="a1fbf-115">所有的採礦模型都會公開演算法根據標準化結構描述所學習的內容，也就是採礦模型結構描述資料列集。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-115">All mining models expose the content learned by the algorithm according to a standardized schema, the mining model schema rowset.</span></span> <span data-ttu-id="a1fbf-116">此資訊提供關於模型的詳細資料，而且包含基本中繼資料、分析期間所發現的結構，以及處理時所使用的參數。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-116">This information provides details about the model and includes the basic metadata, structures discovered in analysis, and parameters that are used when processing.</span></span> <span data-ttu-id="a1fbf-117">您可以藉由使用資料採礦延伸模組 (DMX) 陳述式來針對模型內容建立查詢。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-117">You can create queries against the model content by using Data Mining Extension (DMX) statements.</span></span>  
  
###  <a name="sample-query-1-getting-model-metadata-by-using-dmx"></a><a name="bkmk_Query1"></a> <span data-ttu-id="a1fbf-118">範例查詢 1：使用 DMX 取得模型中繼資料</span><span class="sxs-lookup"><span data-stu-id="a1fbf-118">Sample Query 1: Getting Model Metadata by Using DMX</span></span>  
 <span data-ttu-id="a1fbf-119">下列查詢會傳回使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 類神經網路演算法建立之模型的相關基本中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-119">The following query returns some basic metadata about a model that was built by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm.</span></span> <span data-ttu-id="a1fbf-120">在類神經網路模型中，模型的父節點僅包含模型的名稱、模型儲存位置所在資料庫的名稱，以及子節點的數目。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-120">In a neural network model, the parent node of the model contains only the name of the model, the name of the database where the model is stored, and the number of child nodes.</span></span> <span data-ttu-id="a1fbf-121">不過，臨界統計資料節點 (NODE_TYPE = 24) 會提供關於模型中使用之輸入資料行的這個基本中繼資料，以及一些衍生的統計資料。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-121">However, the marginal statistics node (NODE_TYPE = 24) provides both this basic metadata and some derived statistics about the input columns used in the model.</span></span>  
  
 <span data-ttu-id="a1fbf-122">下列範例查詢是以您在＜ [中繼資料採礦教學課程](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)＞中建立的採礦模型為基礎，名稱為 `Call Center Default NN`。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-122">The following sample query is based on the mining model that you create in the [Intermediate Data Mining Tutorial](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md), named `Call Center Default NN`.</span></span> <span data-ttu-id="a1fbf-123">此模型使用來自撥接中心的資料，探索人員雇用以及電話通數、訂單數與問題數之間可能的關聯。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-123">The model uses data from a call center to explore possible correlations between staffing and the number of calls, orders, and issues.</span></span> <span data-ttu-id="a1fbf-124">DMX 陳述式會從類神經網路模型的臨界統計資料節點擷取資料。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-124">The DMX statement retrieves data from the marginal statistics node of the neural network model.</span></span> <span data-ttu-id="a1fbf-125">此查詢包含 FLATTENED 關鍵字，因為感興趣的輸入屬性統計資料會儲存在 NODE_DISTRIBUTION 巢狀資料表中。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-125">The query includes the FLATTENED keyword, because the input attribute statistics of interest are stored in a nested table, NODE_DISTRIBUTION.</span></span> <span data-ttu-id="a1fbf-126">不過，如果您的查詢提供者支援階段式資料列集，您就不需要使用 FLATTENED 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-126">However, if your query provider supports hierarchical rowsets you do not need to use the FLATTENED keyword.</span></span>  
  
```  
SELECT FLATTENED MODEL_CATALOG, MODEL_NAME,   
(    SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE,  
     [SUPPORT], [PROBABILITY], VALUETYPE   
     FROM NODE_DISTRIBUTION  
) AS t  
FROM [Call Center Default NN].CONTENT  
WHERE NODE_TYPE = 24  
```  
  
> [!NOTE]  
>  <span data-ttu-id="a1fbf-127">您必須將巢狀資料表資料行 `[SUPPORT]` 和 `[PROBABILITY]` 的名稱括在括弧內，以便與同名的保留關鍵字區別。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-127">You must enclose the name of the nested table columns `[SUPPORT]` and `[PROBABILITY]` in brackets to distinguish them from the reserved keywords of the same name.</span></span>  
  
 <span data-ttu-id="a1fbf-128">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="a1fbf-128">Example results:</span></span>  
  
|<span data-ttu-id="a1fbf-129">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a1fbf-129">MODEL_CATALOG</span></span>|<span data-ttu-id="a1fbf-130">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="a1fbf-130">MODEL_NAME</span></span>|<span data-ttu-id="a1fbf-131">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1fbf-131">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="a1fbf-132">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="a1fbf-132">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="a1fbf-133">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="a1fbf-133">t.SUPPORT</span></span>|<span data-ttu-id="a1fbf-134">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="a1fbf-134">t.PROBABILITY</span></span>|<span data-ttu-id="a1fbf-135">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="a1fbf-135">t.VALUETYPE</span></span>|  
|--------------------|-----------------|-----------------------|------------------------|---------------|-------------------|-----------------|  
|<span data-ttu-id="a1fbf-136">Adventure Works DW Multidimensional 2012</span><span class="sxs-lookup"><span data-stu-id="a1fbf-136">Adventure Works DW Multidimensional 2012</span></span>|<span data-ttu-id="a1fbf-137">撥接中心 NN</span><span class="sxs-lookup"><span data-stu-id="a1fbf-137">Call Center NN</span></span>|<span data-ttu-id="a1fbf-138">每個問題的平均時間</span><span class="sxs-lookup"><span data-stu-id="a1fbf-138">Average Time Per Issue</span></span>|<span data-ttu-id="a1fbf-139">Missing</span><span class="sxs-lookup"><span data-stu-id="a1fbf-139">Missing</span></span>|<span data-ttu-id="a1fbf-140">0</span><span class="sxs-lookup"><span data-stu-id="a1fbf-140">0</span></span>|<span data-ttu-id="a1fbf-141">0</span><span class="sxs-lookup"><span data-stu-id="a1fbf-141">0</span></span>|<span data-ttu-id="a1fbf-142">1</span><span class="sxs-lookup"><span data-stu-id="a1fbf-142">1</span></span>|  
|<span data-ttu-id="a1fbf-143">Adventure Works DW Multidimensional 2012</span><span class="sxs-lookup"><span data-stu-id="a1fbf-143">Adventure Works DW Multidimensional 2012</span></span>|<span data-ttu-id="a1fbf-144">撥接中心 NN</span><span class="sxs-lookup"><span data-stu-id="a1fbf-144">Call Center NN</span></span>|<span data-ttu-id="a1fbf-145">每個問題的平均時間</span><span class="sxs-lookup"><span data-stu-id="a1fbf-145">Average Time Per Issue</span></span>|<span data-ttu-id="a1fbf-146">< 64.7094100096</span><span class="sxs-lookup"><span data-stu-id="a1fbf-146">< 64.7094100096</span></span>|<span data-ttu-id="a1fbf-147">11</span><span class="sxs-lookup"><span data-stu-id="a1fbf-147">11</span></span>|<span data-ttu-id="a1fbf-148">0.407407407</span><span class="sxs-lookup"><span data-stu-id="a1fbf-148">0.407407407</span></span>|<span data-ttu-id="a1fbf-149">5</span><span class="sxs-lookup"><span data-stu-id="a1fbf-149">5</span></span>|  
  
 <span data-ttu-id="a1fbf-150">如需結構描述資料列集中的資料行在類神經網路模型環境中代表的定義，請參閱 [類神經網路模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-150">For a definition of what the columns in the schema rowset mean in the context of a neural network model, see [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md).</span></span>  
  
###  <a name="sample-query-2-retrieving-model-metadata-from-the-schema-rowset"></a><a name="bkmk_Query2"></a><span data-ttu-id="a1fbf-151">範例查詢2：從架構資料列集抓取模型中繼資料</span><span class="sxs-lookup"><span data-stu-id="a1fbf-151">Sample Query 2: Retrieving Model Metadata from the Schema Rowset</span></span>  
 <span data-ttu-id="a1fbf-152">您可以藉由查詢資料採礦結構描述資料列集，找到與 DMX 內容查詢所傳回的相同資訊。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-152">You can find the same information that is returned in a DMX content query by querying the data mining schema rowset.</span></span> <span data-ttu-id="a1fbf-153">不過，結構描述資料列集會提供某些額外的資料行。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-153">However, the schema rowset provides some additional columns.</span></span> <span data-ttu-id="a1fbf-154">下列範例查詢會傳回建立模型的日期、修改日期以及上次處理模型的日期。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-154">The following sample query returns the date that the model was created, the date it was modified, and the date that the model was last processed.</span></span> <span data-ttu-id="a1fbf-155">此查詢也會傳回不易從模型內容取得的可預測資料行，以及建立模型所使用的參數。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-155">The query also returns the predictable columns, which are not easily available from the model content, and the parameters that were used to build the model.</span></span> <span data-ttu-id="a1fbf-156">這項資訊對於記錄模型可能相當實用。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-156">This information can be useful for documenting the model.</span></span>  
  
```  
SELECT MODEL_NAME, DATE_CREATED, LAST_PROCESSED, PREDICTION_ENTITY, MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Call Center Default NN'  
```  
  
 <span data-ttu-id="a1fbf-157">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="a1fbf-157">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a1fbf-158">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="a1fbf-158">MODEL_NAME</span></span>|<span data-ttu-id="a1fbf-159">撥接中心預設 NN</span><span class="sxs-lookup"><span data-stu-id="a1fbf-159">Call Center Default NN</span></span>|  
|<span data-ttu-id="a1fbf-160">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="a1fbf-160">DATE_CREATED</span></span>|<span data-ttu-id="a1fbf-161">1/10/2008 5:07:38 PM</span><span class="sxs-lookup"><span data-stu-id="a1fbf-161">1/10/2008 5:07:38 PM</span></span>|  
|<span data-ttu-id="a1fbf-162">LAST_PROCESSED</span><span class="sxs-lookup"><span data-stu-id="a1fbf-162">LAST_PROCESSED</span></span>|<span data-ttu-id="a1fbf-163">1/10/2008 5:24:02 PM</span><span class="sxs-lookup"><span data-stu-id="a1fbf-163">1/10/2008 5:24:02 PM</span></span>|  
|<span data-ttu-id="a1fbf-164">PREDICTION_ENTITY</span><span class="sxs-lookup"><span data-stu-id="a1fbf-164">PREDICTION_ENTITY</span></span>|<span data-ttu-id="a1fbf-165">每個問題的平均時間，</span><span class="sxs-lookup"><span data-stu-id="a1fbf-165">Average Time Per Issue,</span></span><br /><br /> <span data-ttu-id="a1fbf-166">服務等級，</span><span class="sxs-lookup"><span data-stu-id="a1fbf-166">Grade Of Service,</span></span><br /><br /> <span data-ttu-id="a1fbf-167">訂單數目</span><span class="sxs-lookup"><span data-stu-id="a1fbf-167">Number Of Orders</span></span>|  
|<span data-ttu-id="a1fbf-168">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a1fbf-168">MINING_PARAMETERS</span></span>|<span data-ttu-id="a1fbf-169">HOLDOUT_PERCENTAGE=30, HOLDOUT_SEED=0,</span><span class="sxs-lookup"><span data-stu-id="a1fbf-169">HOLDOUT_PERCENTAGE=30, HOLDOUT_SEED=0,</span></span><br /><br /> <span data-ttu-id="a1fbf-170">MAXIMUM_INPUT_ATTRIBUTES=255, MAXIMUM_OUTPUT_ATTRIBUTES=255,</span><span class="sxs-lookup"><span data-stu-id="a1fbf-170">MAXIMUM_INPUT_ATTRIBUTES=255, MAXIMUM_OUTPUT_ATTRIBUTES=255,</span></span><br /><br /> <span data-ttu-id="a1fbf-171">MAXIMUM_STATES=100, SAMPLE_SIZE=10000, HIDDEN_NODE_RATIO=4</span><span class="sxs-lookup"><span data-stu-id="a1fbf-171">MAXIMUM_STATES=100, SAMPLE_SIZE=10000, HIDDEN_NODE_RATIO=4</span></span>|  
  
###  <a name="sample-query-3-retrieving-the-input-attributes-for-the-model"></a><a name="bkmk_Query3"></a><span data-ttu-id="a1fbf-172">範例查詢3：抓取模型的輸入屬性</span><span class="sxs-lookup"><span data-stu-id="a1fbf-172">Sample Query 3: Retrieving the Input Attributes for the Model</span></span>  
 <span data-ttu-id="a1fbf-173">您可以查詢輸入層 (NODE_TYPE = 18) 的子節點 (NODE_TYPE = 20)，擷取建立模型所使用的輸入屬性和值的配對。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-173">You can retrieve the input attribute-value pairs that were used to create the model by querying the child nodes (NODE_TYPE = 20) of the input layer (NODE_TYPE = 18).</span></span> <span data-ttu-id="a1fbf-174">下列查詢會從節點描述傳回輸入屬性的清單。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-174">The following query returns a list of input attributes from the node descriptions.</span></span>  
  
```  
SELECT NODE_DESCRIPTION  
FROM [Call Center Default NN].CONTENT  
WHERE NODE_TYPE = 2  
```  
  
 <span data-ttu-id="a1fbf-175">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="a1fbf-175">Example results:</span></span>  
  
|<span data-ttu-id="a1fbf-176">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a1fbf-176">NODE_DESCRIPTION</span></span>|  
|-----------------------|  
|<span data-ttu-id="a1fbf-177">每個問題的平均時間=64.7094100096 - 77.4002099712</span><span class="sxs-lookup"><span data-stu-id="a1fbf-177">Average Time Per Issue=64.7094100096 - 77.4002099712</span></span>|  
|<span data-ttu-id="a1fbf-178">週中的日=Fri.</span><span class="sxs-lookup"><span data-stu-id="a1fbf-178">Day Of Week=Fri.</span></span>|  
|<span data-ttu-id="a1fbf-179">層級 1 運算子</span><span class="sxs-lookup"><span data-stu-id="a1fbf-179">Level 1 Operators</span></span>|  
  
 <span data-ttu-id="a1fbf-180">結果中只有少數代表性的資料列會顯示在此處。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-180">Only a few representative rows from the results are shown here.</span></span> <span data-ttu-id="a1fbf-181">不過，您可以發現，根據輸入屬性的資料類型，NODE_DESCRIPTION 會提供稍微不同的資訊。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-181">However, you can see that the NODE_DESCRIPTION provides slightly different information depending on the data type of the input attribute.</span></span>  
  
-   <span data-ttu-id="a1fbf-182">如果屬性是離散值或離散化的值，則會傳回屬性及其值或其離散化的範圍。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-182">If the attribute is a discrete or discretized value, the attribute and either its value or its discretized range are returned.</span></span>  
  
-   <span data-ttu-id="a1fbf-183">如果屬性為連續的數值資料類型，則 NODE_DESCRIPTION contains 僅包含屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-183">If the attribute is a continuous numeric data type, the NODE_DESCRIPTION contains only the attribute name.</span></span> <span data-ttu-id="a1fbf-184">不過，您可以擷取 NODE_DISTRIBUTION 巢狀資料表以取得平均值，或傳回 NODE_RULE 以取得數值範圍的最小值與最大值。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-184">However, you can retrieve the nested NODE_DISTRIBUTION table to obtain the mean, or return the NODE_RULE to obtain the minimum and maximum values of the numeric range.</span></span>  
  
 <span data-ttu-id="a1fbf-185">下列查詢顯示如何查詢 NODE_DISTRIBUTION 巢狀資料表，以便在一個資料行中傳回屬性，並在另一個資料行中傳回其值。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-185">The following query shows how to query the nested NODE_DISTRIBUTION table to return the attributes in one column, and their values in another column.</span></span> <span data-ttu-id="a1fbf-186">若是連續屬性，屬性值會以其平均值表示。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-186">For continuous attributes, the value of the attribute is represented by its mean.</span></span>  
  
```  
SELECT FLATTENED   
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE  
FROM NODE_DISTRIBUTION) as t  
FROM [Call Center Default NN -- Predict Service and Orders].CONTENT  
WHERE NODE_TYPE = 21  
```  
  
 <span data-ttu-id="a1fbf-187">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="a1fbf-187">Example results:</span></span>  
  
|<span data-ttu-id="a1fbf-188">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1fbf-188">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="a1fbf-189">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="a1fbf-189">t.ATTRIBUTE_VALUE</span></span>|  
|-----------------------|------------------------|  
|<span data-ttu-id="a1fbf-190">每個問題的平均時間</span><span class="sxs-lookup"><span data-stu-id="a1fbf-190">Average Time Per Issue</span></span>|<span data-ttu-id="a1fbf-191">64.7094100096 - 77.4002099712</span><span class="sxs-lookup"><span data-stu-id="a1fbf-191">64.7094100096 - 77.4002099712</span></span>|  
|<span data-ttu-id="a1fbf-192">週中的日</span><span class="sxs-lookup"><span data-stu-id="a1fbf-192">Day Of Week</span></span>|<span data-ttu-id="a1fbf-193">Fri.</span><span class="sxs-lookup"><span data-stu-id="a1fbf-193">Fri.</span></span>|  
|<span data-ttu-id="a1fbf-194">層級 1 運算子</span><span class="sxs-lookup"><span data-stu-id="a1fbf-194">Level 1 Operators</span></span>|<span data-ttu-id="a1fbf-195">3.2962962962963</span><span class="sxs-lookup"><span data-stu-id="a1fbf-195">3.2962962962963</span></span>|  
  
 <span data-ttu-id="a1fbf-196">最小與最大範圍值會儲存在 NODE_RULE 資料行中，而且會以 XML 片段表示，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="a1fbf-196">The minimum and maximum range values are stored in the NODE_RULE column, and are represented as an XML fragment, as shown in the following example:</span></span>  
  
```  
<NormContinuous field="Level 1 Operators">    
  <LinearNorm orig="2.83967303681711" norm="-1" />    
  <LinearNorm orig="3.75291955577548" norm="1" />    
</NormContinuous>    
```  
  
###  <a name="sample-query-4-retrieving-weights-from-the-hidden-layer"></a><a name="bkmk_Query4"></a> <span data-ttu-id="a1fbf-197">範例查詢 4：從隱藏層擷取加權</span><span class="sxs-lookup"><span data-stu-id="a1fbf-197">Sample Query 4: Retrieving Weights from the Hidden Layer</span></span>  
 <span data-ttu-id="a1fbf-198">類神經網路模型的模型內容結構化的方式可以讓網路中任何節點之詳細資料的擷取更為容易。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-198">The model content of a neural network model is structured in a way that makes it easy to retrieve details about any node in the network.</span></span> <span data-ttu-id="a1fbf-199">此外，節點識別碼提供的資訊可協助您識別節點類型之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-199">Moreover, the ID numbers of the nodes provide information that helps you identify relationships among the node types.</span></span>  
  
 <span data-ttu-id="a1fbf-200">下列查詢示範如何擷取儲存在隱藏層特定節點下的係數。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-200">The following query demonstrates how to retrieve the coefficients that are stored under a particular node of the hidden layer.</span></span> <span data-ttu-id="a1fbf-201">隱藏層由僅包含中繼資料的組合管理節點 (NODE_TYPE = 19)，以及包含各種屬性和值組合之係數的多個子節點 (NODE_TYPE = 22) 所組成。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-201">The hidden layer consists of an organizer node (NODE_TYPE = 19), which contains only metadata, and multiple child nodes (NODE_TYPE = 22), which contain the coefficients for the various combinations of attributes and values.</span></span> <span data-ttu-id="a1fbf-202">此查詢僅傳回係數節點。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-202">This query returns only the coefficient nodes.</span></span>  
  
```  
SELECT FLATTENED TOP 1 NODE_UNIQUE_NAME,   
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, VALUETYPE  
FROM NODE_DISTRIBUTION) as t  
FROM  [Call Center Default NN -- Predict Service and Orders].CONTENT  
WHERE NODE_TYPE = 22  
AND [PARENT_UNIQUE_NAME] = '40000000200000000' FROM [Call Center Default NN].CONTENT  
```  
  
 <span data-ttu-id="a1fbf-203">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="a1fbf-203">Example results:</span></span>  
  
|<span data-ttu-id="a1fbf-204">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1fbf-204">NODE_UNIQUE_NAME</span></span>|<span data-ttu-id="a1fbf-205">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1fbf-205">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="a1fbf-206">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="a1fbf-206">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="a1fbf-207">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="a1fbf-207">t.VALUETYPE</span></span>|  
|------------------------|-----------------------|------------------------|-----------------|  
|<span data-ttu-id="a1fbf-208">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="a1fbf-208">70000000200000000</span></span>|<span data-ttu-id="a1fbf-209">6000000000000000a</span><span class="sxs-lookup"><span data-stu-id="a1fbf-209">6000000000000000a</span></span>|<span data-ttu-id="a1fbf-210">-0.178616518</span><span class="sxs-lookup"><span data-stu-id="a1fbf-210">-0.178616518</span></span>|<span data-ttu-id="a1fbf-211">7</span><span class="sxs-lookup"><span data-stu-id="a1fbf-211">7</span></span>|  
|<span data-ttu-id="a1fbf-212">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="a1fbf-212">70000000200000000</span></span>|<span data-ttu-id="a1fbf-213">6000000000000000b</span><span class="sxs-lookup"><span data-stu-id="a1fbf-213">6000000000000000b</span></span>|<span data-ttu-id="a1fbf-214">-0.267561918</span><span class="sxs-lookup"><span data-stu-id="a1fbf-214">-0.267561918</span></span>|<span data-ttu-id="a1fbf-215">7</span><span class="sxs-lookup"><span data-stu-id="a1fbf-215">7</span></span>|  
|<span data-ttu-id="a1fbf-216">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="a1fbf-216">70000000200000000</span></span>|<span data-ttu-id="a1fbf-217">6000000000000000c</span><span class="sxs-lookup"><span data-stu-id="a1fbf-217">6000000000000000c</span></span>|<span data-ttu-id="a1fbf-218">0.11069497</span><span class="sxs-lookup"><span data-stu-id="a1fbf-218">0.11069497</span></span>|<span data-ttu-id="a1fbf-219">7</span><span class="sxs-lookup"><span data-stu-id="a1fbf-219">7</span></span>|  
|<span data-ttu-id="a1fbf-220">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="a1fbf-220">70000000200000000</span></span>|<span data-ttu-id="a1fbf-221">6000000000000000d</span><span class="sxs-lookup"><span data-stu-id="a1fbf-221">6000000000000000d</span></span>|<span data-ttu-id="a1fbf-222">0.123757712</span><span class="sxs-lookup"><span data-stu-id="a1fbf-222">0.123757712</span></span>|<span data-ttu-id="a1fbf-223">7</span><span class="sxs-lookup"><span data-stu-id="a1fbf-223">7</span></span>|  
|<span data-ttu-id="a1fbf-224">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="a1fbf-224">70000000200000000</span></span>|<span data-ttu-id="a1fbf-225">6000000000000000e</span><span class="sxs-lookup"><span data-stu-id="a1fbf-225">6000000000000000e</span></span>|<span data-ttu-id="a1fbf-226">0.294565343</span><span class="sxs-lookup"><span data-stu-id="a1fbf-226">0.294565343</span></span>|<span data-ttu-id="a1fbf-227">7</span><span class="sxs-lookup"><span data-stu-id="a1fbf-227">7</span></span>|  
|<span data-ttu-id="a1fbf-228">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="a1fbf-228">70000000200000000</span></span>|<span data-ttu-id="a1fbf-229">6000000000000000f</span><span class="sxs-lookup"><span data-stu-id="a1fbf-229">6000000000000000f</span></span>|<span data-ttu-id="a1fbf-230">0.22245318</span><span class="sxs-lookup"><span data-stu-id="a1fbf-230">0.22245318</span></span>|<span data-ttu-id="a1fbf-231">7</span><span class="sxs-lookup"><span data-stu-id="a1fbf-231">7</span></span>|  
|<span data-ttu-id="a1fbf-232">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="a1fbf-232">70000000200000000</span></span>||<span data-ttu-id="a1fbf-233">0.188805045</span><span class="sxs-lookup"><span data-stu-id="a1fbf-233">0.188805045</span></span>|<span data-ttu-id="a1fbf-234">7</span><span class="sxs-lookup"><span data-stu-id="a1fbf-234">7</span></span>|  
  
 <span data-ttu-id="a1fbf-235">此處顯示的部分結果示範類神經網路模型內容如何讓隱藏節點與輸入節點相關聯。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-235">The partial results shown here demonstrate how the neural network model content relates the hidden node to the input nodes.</span></span>  
  
-   <span data-ttu-id="a1fbf-236">節點在隱藏層中的唯一名稱永遠以 70000000 做為開頭。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-236">The unique names of nodes in the hidden layer always begin with 70000000.</span></span>  
  
-   <span data-ttu-id="a1fbf-237">節點在輸入層中的唯一名稱永遠以 60000000 做為開頭。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-237">The unique names of nodes in the input layer always begin with 60000000.</span></span>  
  
 <span data-ttu-id="a1fbf-238">因此，這些結果會告訴您，已經有六個不同的係數 (VALUETYPE = 7) 傳遞給以識別碼 70000000200000000 表示的節點，</span><span class="sxs-lookup"><span data-stu-id="a1fbf-238">Thus, these results tell you that the node denoted by the ID 70000000200000000 had six different coefficients (VALUETYPE = 7) passed to it.</span></span> <span data-ttu-id="a1fbf-239">這些係數的值位於 ATTRIBUTE_VALUE 資料行中。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-239">The values of the coefficients are in the ATTRIBUTE_VALUE column.</span></span> <span data-ttu-id="a1fbf-240">您可以使用 ATTRIBUTE_NAME 資料行中的節點識別碼，正確地判斷此係數用於哪個輸入屬性。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-240">You can determine exactly which input attribute the coefficient is for by using the node ID in the ATTRIBUTE_NAME column.</span></span> <span data-ttu-id="a1fbf-241">例如，節點識別碼 6000000000000000a 表示輸入屬性及值 `Day of Week = 'Tue.'` 。您可以使用節點識別碼來建立查詢，或者可以使用 [Microsoft 一般內容樹狀檢視器](../microsoft-generic-content-tree-viewer-data-mining.md)瀏覽到該節點。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-241">For example, the node ID 6000000000000000a refers to input attribute and value, `Day of Week = 'Tue.'` You can use the node ID to create a query, or you can browse to the node by using the [Microsoft Generic Content Tree Viewer](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
 <span data-ttu-id="a1fbf-242">同樣地，如果您在輸出層 layer (NODE_TYPE = 23) 中查詢節點的 NODE_DISTRIBUTION 資料表，您可以看到每個輸出值的係數。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-242">Similarly, if you query the NODE_DISTRIBUTION table of the nodes in the output layer (NODE_TYPE = 23), you can see the coefficients for each output value.</span></span> <span data-ttu-id="a1fbf-243">不過，在輸出層中，這些指標會回頭參考隱藏層的節點。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-243">However, in the output layer, the pointers refer back to the nodes of the hidden layer.</span></span> <span data-ttu-id="a1fbf-244">如需詳細資訊，請參閱 [類神經網路模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-244">For more information, see [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md).</span></span>  
  
## <a name="using-a-neural-network-model-to-make-predictions"></a><span data-ttu-id="a1fbf-245">使用類神經網路模型進行預測</span><span class="sxs-lookup"><span data-stu-id="a1fbf-245">Using a Neural Network Model to Make Predictions</span></span>  
 <span data-ttu-id="a1fbf-246">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 類神經網路演算法同時支援分類與迴歸。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-246">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm supports both classification and regression.</span></span> <span data-ttu-id="a1fbf-247">您可以搭配這些模型使用預測函數來提供新的資料，並建立單一或批次預測。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-247">You can use prediction functions with these models to provide new data and create either singleton or batch predictions.</span></span>  
  
###  <a name="sample-query-5-creating-a-singleton-prediction"></a><a name="bkmk_Query5"></a><span data-ttu-id="a1fbf-248">範例查詢5：建立單一預測</span><span class="sxs-lookup"><span data-stu-id="a1fbf-248">Sample Query 5: Creating a Singleton Prediction</span></span>  
 <span data-ttu-id="a1fbf-249">在類神經網路模型上建立預測查詢最簡單的方式就是使用預測查詢產生器 (可在 **和** 中，資料採礦設計師的 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [採礦預測] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]索引標籤上取得)。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-249">The easiest way to build a prediction query on a neural network model is to use the Prediction Query Builder, available on the **Mining Prediction** tab of Data Mining Designer in both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="a1fbf-250">您可以在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 類神經網路檢視器中瀏覽模型來篩選感興趣的屬性並檢視趨勢，然後切換到 **[採礦預測]** 索引標籤來建立查詢，並針對這些趨勢預測新的值。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-250">You can browse the model in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network Viewer to filter attributes of interest and view trends, and then switch to the **Mining Prediction** tab to create a query and predict new values for those trends.</span></span>  
  
 <span data-ttu-id="a1fbf-251">例如，您可以瀏覽撥接中心模型來檢視訂單量與其他屬性間的關聯。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-251">For example, you can browse the call center model to view correlations between the order volumes and other attributes.</span></span> <span data-ttu-id="a1fbf-252">若要這麼做，請在檢視器中開啟模型，然後在 [**輸入**] 中選取 [] **\<All>** 。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-252">To do this, open the model in the viewer, and for **Input**, select **\<All>**.</span></span>  <span data-ttu-id="a1fbf-253">接著，為 **[輸出]** 選取 **[訂單數目]**。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-253">Next, for **Output**, select **Number of Orders**.</span></span> <span data-ttu-id="a1fbf-254">為 **[值 1]** 選取代表最多訂單的範圍，並為 **[值 2]** 選取代表最少訂單的範圍。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-254">For **Value 1**, select the range that represents the most orders, and for **Value 2**, select the range that represents the fewest orders.</span></span> <span data-ttu-id="a1fbf-255">然後，您可以看一下模型與訂單量關聯的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-255">You can then see at a glance all the attributes that the model correlates with order volume.</span></span>  
  
 <span data-ttu-id="a1fbf-256">透過瀏覽檢視器中的結果，您會發現一週的某幾天訂單量較低，而運算子數目的增加似乎與較高的銷售量互相關聯。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-256">By browsing the results in the viewer, you find that certain days of the week have low order volumes, and that an increase in the number of operators seems to be correlated with higher sales.</span></span> <span data-ttu-id="a1fbf-257">接著，您可以在模型上使用預測查詢來測試 "what if" 假設，並詢問在訂單量低的天數上增加層級 2 運算子的數目是否會增加訂單。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-257">You could then use a prediction query on the model to test a "what if" hypothesis and ask if increasing the number of level 2 operators on a low-volume day would increase orders.</span></span> <span data-ttu-id="a1fbf-258">若要這樣做，建立如下的查詢：</span><span class="sxs-lookup"><span data-stu-id="a1fbf-258">To do this, create a query such as the following:</span></span>  
  
```  
SELECT Predict([Call Center Default NN].[Number of Orders]) AS [Predicted Orders],  
PredictProbability([Call Center Default NN].[Number of Orders]) AS [Probability]  
FROM [Call Center Default NN]  
NATURAL PREDICTION JOIN   
(SELECT 'Tue.' AS [Day of Week],  
13 AS [Level 2 Operators]) AS t  
```  
  
 <span data-ttu-id="a1fbf-259">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="a1fbf-259">Example results:</span></span>  
  
|<span data-ttu-id="a1fbf-260">預測的訂單</span><span class="sxs-lookup"><span data-stu-id="a1fbf-260">Predicted Orders</span></span>|<span data-ttu-id="a1fbf-261">機率</span><span class="sxs-lookup"><span data-stu-id="a1fbf-261">Probability</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="a1fbf-262">364</span><span class="sxs-lookup"><span data-stu-id="a1fbf-262">364</span></span>|<span data-ttu-id="a1fbf-263">0.9532 .。。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-263">0.9532...</span></span>|  
  
 <span data-ttu-id="a1fbf-264">預測的銷售量高於目前星期二的銷售量範圍，而且預測的機率相當高。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-264">The predicted sales volume is higher than the current range of sales for Tuesday, and the probability of the prediction is very high.</span></span> <span data-ttu-id="a1fbf-265">不過，您可能想要使用批次處理測試模型的各種假設，藉以建立多個預測。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-265">However, you might want to create multiple predictions by using a batch process to test a variety of hypotheses on the model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1fbf-266">適用於 Excel 2007 的資料採礦增益集提供羅吉斯迴歸精靈，讓您輕鬆回應複雜的問題，例如，需要多少位二級操作員，才能將某個排班的服務等級提升至目標等級。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-266">The Data Mining Add-Ins for Excel 2007 provide logistic regression wizards that make it easy to answer complex questions, such as how many Level Two Operators would be needed to improve service grade to a target level for a specific shift.</span></span> <span data-ttu-id="a1fbf-267">您可以免費下載資料採礦增益集，其中包含類神經網路和/或羅吉斯迴歸演算法的精靈。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-267">The data mining add-ins are a free download, and include wizards that are based on the neural network and/or logistic regression algorithms.</span></span> <span data-ttu-id="a1fbf-268">如需詳細資訊，請參閱 [適用於 Office 2007 的資料採礦增益集](https://go.microsoft.com/fwlink/?LinkID=117790) 網站。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-268">For more information, see the [Data Mining Add-ins for Office 2007](https://go.microsoft.com/fwlink/?LinkID=117790) Web site.</span></span>  
  
## <a name="list-of-prediction-functions"></a><span data-ttu-id="a1fbf-269">預測函數的清單</span><span class="sxs-lookup"><span data-stu-id="a1fbf-269">List of Prediction Functions</span></span>  
 <span data-ttu-id="a1fbf-270">所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 演算法都支援一組常用的函數。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-270">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="a1fbf-271">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 類神經網路演算法沒有專用的預測函數，不過，此演算法支援下表所列出的函數。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-271">There are no prediction functions that are specific to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm; however, the algorithm supports the functions that are listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a1fbf-272">預測函數</span><span class="sxs-lookup"><span data-stu-id="a1fbf-272">Prediction Function</span></span>|<span data-ttu-id="a1fbf-273">使用量</span><span class="sxs-lookup"><span data-stu-id="a1fbf-273">Usage</span></span>|  
|[<span data-ttu-id="a1fbf-274">IsDescendant &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a1fbf-274">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="a1fbf-275">確定某個節點是否為類神經網路圖中另一個節點的子系。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-275">Determines whether one node is a child of another node in the neural network graph.</span></span>|  
|[<span data-ttu-id="a1fbf-276">PredictAdjustedProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a1fbf-276">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="a1fbf-277">傳回加權機率。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-277">Returns the weighted probability.</span></span>|  
|[<span data-ttu-id="a1fbf-278">PredictHistogram &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a1fbf-278">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="a1fbf-279">傳回與目前預測值相關之值的資料表。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-279">Returns a table of values related to the current predicted value.</span></span>|  
|[<span data-ttu-id="a1fbf-280">PredictVariance &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a1fbf-280">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="a1fbf-281">傳回預測值的變異數。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-281">Returns variance for the predicted value.</span></span>|  
|[<span data-ttu-id="a1fbf-282">PredictProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a1fbf-282">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="a1fbf-283">傳回預測值的機率。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-283">Returns probability  for the predicted value.</span></span>|  
|[<span data-ttu-id="a1fbf-284">PredictStdev &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a1fbf-284">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="a1fbf-285">傳回預測值的標準差。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-285">Returns the standard deviance for the predicted value.</span></span>|  
|[<span data-ttu-id="a1fbf-286">PredictSupport &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="a1fbf-286">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="a1fbf-287">若是類神經網路與羅吉斯迴歸模型，則會傳回代表整個模型之定型集大小的單一值。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-287">For neural network and logistic regression models, returns a single value that represents the size of the training set for the entire model.</span></span>|  
  
 <span data-ttu-id="a1fbf-288">如需特定函數的語法，請參閱[資料採礦延伸模組 &#40;DMX&#41; 函數參考](/sql/dmx/data-mining-extensions-dmx-function-reference)。</span><span class="sxs-lookup"><span data-stu-id="a1fbf-288">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1fbf-289">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1fbf-289">See Also</span></span>  
 <span data-ttu-id="a1fbf-290">[Microsoft 類神經網路演算法](microsoft-neural-network-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="a1fbf-290">[Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md) </span></span>  
 <span data-ttu-id="a1fbf-291">[Microsoft 類神經網路演算法技術參考](microsoft-neural-network-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a1fbf-291">[Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="a1fbf-292">[類神經網路模型的採礦模型內容 &#40;Analysis Services 資料採礦&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="a1fbf-292">[Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="a1fbf-293">第五課：建立類神經網路和羅吉斯迴歸模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="a1fbf-293">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
  
