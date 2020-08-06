---
title: 決策樹模型查詢範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- decision tree algorithms [Analysis Services]
- content queries [DMX]
- decision trees [Analysis Services]
ms.assetid: ceaf1370-9dd1-4d1a-a143-7f89a723ef80
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7a6b158a42c9ca90bf2cfd2e9b981a1e2a735ccc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688369"
---
# <a name="decision-trees-model-query-examples"></a><span data-ttu-id="aca60-102">決策樹模型查詢範例</span><span class="sxs-lookup"><span data-stu-id="aca60-102">Decision Trees Model Query Examples</span></span>
  <span data-ttu-id="aca60-103">當您針對資料採礦模型建立查詢時，可以建立內容查詢來提供有關分析期間所發現之模式的詳細資料，或是建立預測查詢來使用模型中的模式，為新的資料進行預測。</span><span class="sxs-lookup"><span data-stu-id="aca60-103">When you create a query against a data mining model, you can create a content query, which provides details about the patterns discovered in analysis, or you can create a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="aca60-104">例如，決策樹模型的內容查詢可能會提供有關每一樹狀結構層上之案例數的統計資料，或是區分案例的規則。</span><span class="sxs-lookup"><span data-stu-id="aca60-104">For example, a content query for a decision trees model might provide statistics about the number of cases at each level of the tree, or the rules that differentiate between cases.</span></span> <span data-ttu-id="aca60-105">或者，預測查詢會將此模型對應到新的資料，以便產生建議、分類等等。</span><span class="sxs-lookup"><span data-stu-id="aca60-105">Alternatively, a prediction query maps the model to new data in order to generate recommendations, classifications, and so forth.</span></span> <span data-ttu-id="aca60-106">您也可以使用查詢來擷取有關模型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="aca60-106">You can also retrieve metadata about the model by using a query.</span></span>  
  
 <span data-ttu-id="aca60-107">本節說明如何針對以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 決策樹演算法為基礎的模型來建立查詢。</span><span class="sxs-lookup"><span data-stu-id="aca60-107">This section explains how to create queries for models that are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm.</span></span>  
  
 <span data-ttu-id="aca60-108">**內容查詢**</span><span class="sxs-lookup"><span data-stu-id="aca60-108">**Content Queries**</span></span>  
  
 [<span data-ttu-id="aca60-109">從資料採礦結構描述資料列集擷取模型參數</span><span class="sxs-lookup"><span data-stu-id="aca60-109">Retrieving Model Parameters from the Data Mining Schema Rowset</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="aca60-110">使用 DMX 取得有關模型中樹狀結構的詳細資料</span><span class="sxs-lookup"><span data-stu-id="aca60-110">Getting Details about Trees in the Model by Using DMX</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="aca60-111">從模型擷取子樹</span><span class="sxs-lookup"><span data-stu-id="aca60-111">Retrieving Subtrees from the Model</span></span>](#bkmk_Query3)  
  
 <span data-ttu-id="aca60-112">**預測查詢**</span><span class="sxs-lookup"><span data-stu-id="aca60-112">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="aca60-113">傳回包含機率的預測</span><span class="sxs-lookup"><span data-stu-id="aca60-113">Returning Predictions with Probabilities</span></span>](#bkmk_Query4)  
  
 [<span data-ttu-id="aca60-114">從決策樹模型預測關聯</span><span class="sxs-lookup"><span data-stu-id="aca60-114">Predicting Associations from a Decision Trees Model</span></span>](#bkmk_Query5)  
  
 [<span data-ttu-id="aca60-115">從決策樹模型擷取迴歸公式</span><span class="sxs-lookup"><span data-stu-id="aca60-115">Retrieving a Regression Formula from a Decision Trees Model</span></span>](#bkmk_Query6)  
  
##  <a name="finding-information-about-a-decision-trees-model"></a><a name="bkmk_top2"></a> <span data-ttu-id="aca60-116">尋找有關決策樹模型的資訊</span><span class="sxs-lookup"><span data-stu-id="aca60-116">Finding Information about a Decision Trees Model</span></span>  
 <span data-ttu-id="aca60-117">若要在決策樹模型的內容上建立有意義的查詢，您應該了解模型內容的結構，以及哪一種節點類型會儲存那一種資訊。</span><span class="sxs-lookup"><span data-stu-id="aca60-117">To create meaningful queries on the content of a decision trees model, you should understand the structure of the model content, and which node types store what kind of information.</span></span> <span data-ttu-id="aca60-118">如需詳細資訊，請參閱 [決策樹模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="aca60-118">For more information, see [Mining Model Content for Decision Tree Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md).</span></span>  
  
###  <a name="sample-query-1-retrieving-model-parameters-from-the-data-mining-schema-rowset"></a><a name="bkmk_Query1"></a> <span data-ttu-id="aca60-119">範例查詢 1：從資料採礦結構描述資料列集擷取模型參數</span><span class="sxs-lookup"><span data-stu-id="aca60-119">Sample Query 1: Retrieving Model Parameters from the Data Mining Schema Rowset</span></span>  
 <span data-ttu-id="aca60-120">您可以藉由查詢資料採礦結構描述資料列集來尋找有關此模型的中繼資料，例如此模型建立的時間、上次處理此模型的時間、此模型所根據的採礦結構名稱，以及用來當做可預測屬性的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="aca60-120">By querying the data mining schema rowset, you can find metadata about the model, such as when it was created, when the model was last processed, the name of the mining structure that the model is based on, and the name of the column used as the predictable attribute.</span></span> <span data-ttu-id="aca60-121">您也可以傳回初次建立此模型時所使用的參數。</span><span class="sxs-lookup"><span data-stu-id="aca60-121">You can also return the parameters that were used when the model was first created.</span></span>  
  
```  
select MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_Decision Tree'  
```  
  
 <span data-ttu-id="aca60-122">範例結果：</span><span class="sxs-lookup"><span data-stu-id="aca60-122">Sample results:</span></span>  
  
 <span data-ttu-id="aca60-123">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aca60-123">MINING_PARAMETERS</span></span>  
  
 <span data-ttu-id="aca60-124">COMPLEXITY_PENALTY=0.5, MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_OUTPUT_ATTRIBUTES=255,MINIMUM_SUPPORT=10,SCORE_METHOD=4,SPLIT_METHOD=3,FORCE_REGRESSOR=</span><span class="sxs-lookup"><span data-stu-id="aca60-124">COMPLEXITY_PENALTY=0.5, MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_OUTPUT_ATTRIBUTES=255,MINIMUM_SUPPORT=10,SCORE_METHOD=4,SPLIT_METHOD=3,FORCE_REGRESSOR=</span></span>  
  
###  <a name="sample-query-2-returning-details-about-the-model-content-by-using-dmx"></a><a name="bkmk_Query2"></a> <span data-ttu-id="aca60-125">範例查詢 2：使用 DMX 傳回有關模型內容的詳細資料</span><span class="sxs-lookup"><span data-stu-id="aca60-125">Sample Query 2: Returning Details about the Model Content by Using DMX</span></span>  
 <span data-ttu-id="aca60-126">下列查詢會傳回您在 [資料採礦基本教學課程](../../tutorials/basic-data-mining-tutorial.md)中建立模型時所建立之決策樹模型的一些基本資訊。</span><span class="sxs-lookup"><span data-stu-id="aca60-126">The following query returns some basic information about the decision trees that were created when you built the model in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span> <span data-ttu-id="aca60-127">每個樹狀結構都會儲存在它自己的節點中。</span><span class="sxs-lookup"><span data-stu-id="aca60-127">Each tree structure is stored in its own node.</span></span> <span data-ttu-id="aca60-128">由於此模型只包含單一可預測屬性，因此只有一個樹狀節點。</span><span class="sxs-lookup"><span data-stu-id="aca60-128">Because this model contains a single predictable attribute, there is only one tree node.</span></span> <span data-ttu-id="aca60-129">但是，如果您使用決策樹演算法來建立關聯模型，可能會有好幾百個樹狀結構，每一個產品都有一個。</span><span class="sxs-lookup"><span data-stu-id="aca60-129">However, if you create an association model by using the Decision Trees algorithm, there might be hundreds of trees, one for each product.</span></span>  
  
 <span data-ttu-id="aca60-130">此查詢會傳回類型 2 的所有節點，這些節點是代表特定可預測屬性之樹狀結構的最上層節點。</span><span class="sxs-lookup"><span data-stu-id="aca60-130">This query returns all the nodes of type 2, which are the top level nodes of a tree that represents a particular predictable attribute.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aca60-131">`CHILDREN_CARDINALITY` 資料行必須括在括號中，以便與同名的 MDX 保留關鍵字區分。</span><span class="sxs-lookup"><span data-stu-id="aca60-131">The column, `CHILDREN_CARDINALITY`, must be enclosed in brackets to distinguish it from the MDX reserved keyword of the same name.</span></span>  
  
```  
SELECT MODEL_NAME, NODE_NAME, NODE_CAPTION,   
NODE_SUPPORT, [CHILDREN_CARDINALITY]  
FROM TM_DecisionTrees.CONTENT  
WHERE NODE_TYPE = 2  
```  
  
 <span data-ttu-id="aca60-132">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="aca60-132">Example results:</span></span>  
  
|<span data-ttu-id="aca60-133">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="aca60-133">MODEL_NAME</span></span>|<span data-ttu-id="aca60-134">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="aca60-134">NODE_NAME</span></span>|<span data-ttu-id="aca60-135">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="aca60-135">NODE_CAPTION</span></span>|<span data-ttu-id="aca60-136">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="aca60-136">NODE_SUPPORT</span></span>|<span data-ttu-id="aca60-137">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="aca60-137">CHILDREN_CARDINALITY</span></span>|  
|-----------------|----------------|-------------------|-------------------|---------------------------|  
|<span data-ttu-id="aca60-138">TM_DecisionTree</span><span class="sxs-lookup"><span data-stu-id="aca60-138">TM_DecisionTree</span></span>|<span data-ttu-id="aca60-139">000000001</span><span class="sxs-lookup"><span data-stu-id="aca60-139">000000001</span></span>|<span data-ttu-id="aca60-140">全部</span><span class="sxs-lookup"><span data-stu-id="aca60-140">All</span></span>|<span data-ttu-id="aca60-141">12939</span><span class="sxs-lookup"><span data-stu-id="aca60-141">12939</span></span>|<span data-ttu-id="aca60-142">5</span><span class="sxs-lookup"><span data-stu-id="aca60-142">5</span></span>|  
  
 <span data-ttu-id="aca60-143">這些結果代表什麼意思？</span><span class="sxs-lookup"><span data-stu-id="aca60-143">What do these results tell you?</span></span> <span data-ttu-id="aca60-144">在決策樹模型中，特定節點的基數會告訴您該節點擁有多少下層子節點。</span><span class="sxs-lookup"><span data-stu-id="aca60-144">In a decision trees model, the cardinality of a particular node tells you how many immediate children that node has.</span></span> <span data-ttu-id="aca60-145">這個節點的基數是 5，表示此模型已將潛在自行車買主的目標母體分成 5 個子群組。</span><span class="sxs-lookup"><span data-stu-id="aca60-145">The cardinality for this node is 5, meaning that the model divided the target population of potential bike buyers into 5 subgroups.</span></span>  
  
 <span data-ttu-id="aca60-146">下列相關查詢會傳回這五個子群組的子節點，連同這些子節點中屬性和值的分佈。</span><span class="sxs-lookup"><span data-stu-id="aca60-146">The following related query returns the children for these five subgroups, together with the distribution of attributes and values in the child nodes.</span></span> <span data-ttu-id="aca60-147">由於統計資料 (如支援、機率和變異數) 會儲存在巢狀資料表 `NODE_DISTRIBUTION` 中，所以這個範例會使用 `FLATTENED` 關鍵字來輸出巢狀資料表資料行。</span><span class="sxs-lookup"><span data-stu-id="aca60-147">Because statistics such as support, probability, and variance are stored in the nested table, `NODE_DISTRIBUTION`, this example uses the `FLATTENED` keyword to output the nested table columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aca60-148">巢狀資料表資料行 `SUPPORT` 必須括在括號中，以便與同名的保留關鍵字區分。</span><span class="sxs-lookup"><span data-stu-id="aca60-148">The nested table column, `SUPPORT`, must be enclosed in brackets to distinguish it from the reserved keyword of the same name.</span></span>  
  
```  
SELECT FLATTENED NODE_NAME, NODE_CAPTION,  
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, [SUPPORT]  
FROM NODE_DISTRIBUTION) AS t  
FROM TM_DecisionTree.CONTENT  
WHERE [PARENT_UNIQUE_NAME] = '000000001'  
```  
  
 <span data-ttu-id="aca60-149">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="aca60-149">Example results:</span></span>  
  
|<span data-ttu-id="aca60-150">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="aca60-150">NODE_NAME</span></span>|<span data-ttu-id="aca60-151">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="aca60-151">NODE_CAPTION</span></span>|<span data-ttu-id="aca60-152">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="aca60-152">T.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="aca60-153">T.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="aca60-153">T.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="aca60-154">SUPPORT</span><span class="sxs-lookup"><span data-stu-id="aca60-154">SUPPORT</span></span>|  
|----------------|-------------------|-----------------------|------------------------|-------------|  
|<span data-ttu-id="aca60-155">00000000100</span><span class="sxs-lookup"><span data-stu-id="aca60-155">00000000100</span></span>|<span data-ttu-id="aca60-156">Number Cars Owned = 0</span><span class="sxs-lookup"><span data-stu-id="aca60-156">Number Cars Owned = 0</span></span>|<span data-ttu-id="aca60-157">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="aca60-157">Bike Buyer</span></span>|<span data-ttu-id="aca60-158">Missing</span><span class="sxs-lookup"><span data-stu-id="aca60-158">Missing</span></span>|<span data-ttu-id="aca60-159">0</span><span class="sxs-lookup"><span data-stu-id="aca60-159">0</span></span>|  
|<span data-ttu-id="aca60-160">00000000100</span><span class="sxs-lookup"><span data-stu-id="aca60-160">00000000100</span></span>|<span data-ttu-id="aca60-161">Number Cars Owned = 0</span><span class="sxs-lookup"><span data-stu-id="aca60-161">Number Cars Owned = 0</span></span>|<span data-ttu-id="aca60-162">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="aca60-162">Bike Buyer</span></span>|<span data-ttu-id="aca60-163">0</span><span class="sxs-lookup"><span data-stu-id="aca60-163">0</span></span>|<span data-ttu-id="aca60-164">1067</span><span class="sxs-lookup"><span data-stu-id="aca60-164">1067</span></span>|  
|<span data-ttu-id="aca60-165">00000000100</span><span class="sxs-lookup"><span data-stu-id="aca60-165">00000000100</span></span>|<span data-ttu-id="aca60-166">Number Cars Owned = 0</span><span class="sxs-lookup"><span data-stu-id="aca60-166">Number Cars Owned = 0</span></span>|<span data-ttu-id="aca60-167">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="aca60-167">Bike Buyer</span></span>|<span data-ttu-id="aca60-168">1</span><span class="sxs-lookup"><span data-stu-id="aca60-168">1</span></span>|<span data-ttu-id="aca60-169">1875</span><span class="sxs-lookup"><span data-stu-id="aca60-169">1875</span></span>|  
|<span data-ttu-id="aca60-170">00000000101</span><span class="sxs-lookup"><span data-stu-id="aca60-170">00000000101</span></span>|<span data-ttu-id="aca60-171">Number Cars Owned = 3</span><span class="sxs-lookup"><span data-stu-id="aca60-171">Number Cars Owned = 3</span></span>|<span data-ttu-id="aca60-172">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="aca60-172">Bike Buyer</span></span>|<span data-ttu-id="aca60-173">Missing</span><span class="sxs-lookup"><span data-stu-id="aca60-173">Missing</span></span>|<span data-ttu-id="aca60-174">0</span><span class="sxs-lookup"><span data-stu-id="aca60-174">0</span></span>|  
|<span data-ttu-id="aca60-175">00000000101</span><span class="sxs-lookup"><span data-stu-id="aca60-175">00000000101</span></span>|<span data-ttu-id="aca60-176">Number Cars Owned = 3</span><span class="sxs-lookup"><span data-stu-id="aca60-176">Number Cars Owned = 3</span></span>|<span data-ttu-id="aca60-177">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="aca60-177">Bike Buyer</span></span>|<span data-ttu-id="aca60-178">0</span><span class="sxs-lookup"><span data-stu-id="aca60-178">0</span></span>|<span data-ttu-id="aca60-179">678</span><span class="sxs-lookup"><span data-stu-id="aca60-179">678</span></span>|  
|<span data-ttu-id="aca60-180">00000000101</span><span class="sxs-lookup"><span data-stu-id="aca60-180">00000000101</span></span>|<span data-ttu-id="aca60-181">Number Cars Owned = 3</span><span class="sxs-lookup"><span data-stu-id="aca60-181">Number Cars Owned = 3</span></span>|<span data-ttu-id="aca60-182">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="aca60-182">Bike Buyer</span></span>|<span data-ttu-id="aca60-183">1</span><span class="sxs-lookup"><span data-stu-id="aca60-183">1</span></span>|<span data-ttu-id="aca60-184">473</span><span class="sxs-lookup"><span data-stu-id="aca60-184">473</span></span>|  
  
 <span data-ttu-id="aca60-185">從這些結果中，您可以得知在購買自行車的客戶 (`[Bike Buyer]` = 1) 中，有 1067 位客戶擁有 0 輛汽車，而有 473 位客戶擁有 3 輛汽車。</span><span class="sxs-lookup"><span data-stu-id="aca60-185">From these results, you can tell that of the customers who bought a bike (`[Bike Buyer]` = 1), 1067 customers had 0 cars and 473 customers had 3 cars.</span></span>  
  
###  <a name="sample-query-3-retrieving-subtrees-from-the-model"></a><a name="bkmk_Query3"></a> <span data-ttu-id="aca60-186">範例查詢 3：從模型擷取子樹</span><span class="sxs-lookup"><span data-stu-id="aca60-186">Sample Query 3: Retrieving Subtrees from the Model</span></span>  
 <span data-ttu-id="aca60-187">假設您想要進一步探索哪些客戶購買自行車的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="aca60-187">Suppose you wanted to discover more about the customers who did buy a bike.</span></span> <span data-ttu-id="aca60-188">您可以在查詢中使用 [IsDescendant &#40;DMX&#41;](/sql/dmx/isdescendant-dmx) 函數 (如下列範例所示)，檢視任何子樹的其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="aca60-188">You can view additional detail for any of the sub-trees by using the [IsDescendant &#40;DMX&#41;](/sql/dmx/isdescendant-dmx) function in the query, as shown in the following example.</span></span> <span data-ttu-id="aca60-189">此查詢會傳回自行車買主的人數，其方式是從包含 42 歲以上之客戶的樹狀結構中擷取分葉節點 (NODE_TYPE = 4)。</span><span class="sxs-lookup"><span data-stu-id="aca60-189">The query returns the count of bike purchasers by retrieving leaf nodes (NODE_TYPE = 4) from the tree that contains customers who are over 42 years of age.</span></span> <span data-ttu-id="aca60-190">此查詢會將巢狀資料表的資料列限制為 Bike Buyer = 1 的資料列。</span><span class="sxs-lookup"><span data-stu-id="aca60-190">The query restricts rows from the nested table to those where Bike Buyer = 1.</span></span>  
  
```  
SELECT FLATTENED NODE_NAME, NODE_CAPTION,NODE_TYPE,  
(  
SELECT [SUPPORT] FROM NODE_DISTRIBUTION WHERE ATTRIBUTE_NAME = 'Bike Buyer' AND ATTRIBUTE_VALUE = '1'  
) AS t  
FROM TM_DecisionTree.CONTENT  
WHERE ISDESCENDANT('0000000010001')  
AND NODE_TYPE = 4  
```  
  
 <span data-ttu-id="aca60-191">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="aca60-191">Example results:</span></span>  
  
|<span data-ttu-id="aca60-192">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="aca60-192">NODE_NAME</span></span>|<span data-ttu-id="aca60-193">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="aca60-193">NODE_CAPTION</span></span>|<span data-ttu-id="aca60-194">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="aca60-194">t.SUPPORT</span></span>|  
|----------------|-------------------|---------------|  
|<span data-ttu-id="aca60-195">000000001000100</span><span class="sxs-lookup"><span data-stu-id="aca60-195">000000001000100</span></span>|<span data-ttu-id="aca60-196">Yearly Income >= 26000 and < 42000</span><span class="sxs-lookup"><span data-stu-id="aca60-196">Yearly Income >= 26000 and < 42000</span></span>|<span data-ttu-id="aca60-197">266</span><span class="sxs-lookup"><span data-stu-id="aca60-197">266</span></span>|  
|<span data-ttu-id="aca60-198">00000000100010100</span><span class="sxs-lookup"><span data-stu-id="aca60-198">00000000100010100</span></span>|<span data-ttu-id="aca60-199">Total Children = 3</span><span class="sxs-lookup"><span data-stu-id="aca60-199">Total Children = 3</span></span>|<span data-ttu-id="aca60-200">75</span><span class="sxs-lookup"><span data-stu-id="aca60-200">75</span></span>|  
|<span data-ttu-id="aca60-201">0000000010001010100</span><span class="sxs-lookup"><span data-stu-id="aca60-201">0000000010001010100</span></span>|<span data-ttu-id="aca60-202">Number Children At Home = 1</span><span class="sxs-lookup"><span data-stu-id="aca60-202">Number Children At Home = 1</span></span>|<span data-ttu-id="aca60-203">75</span><span class="sxs-lookup"><span data-stu-id="aca60-203">75</span></span>|  
  
## <a name="making-predictions-using-a-decision-trees-model"></a><span data-ttu-id="aca60-204">使用決策樹模型進行預測</span><span class="sxs-lookup"><span data-stu-id="aca60-204">Making Predictions using a Decision Trees Model</span></span>  
 <span data-ttu-id="aca60-205">由於決策樹可用於各種工作，包括分類、迴歸，甚至是關聯，所以當您在決策樹模型上建立預測查詢時，您有許多可用的選項。</span><span class="sxs-lookup"><span data-stu-id="aca60-205">Because decision trees can be used for various tasks, including classification, regression, and even association, when you create a prediction query on a decision tree model you have many options available to you.</span></span> <span data-ttu-id="aca60-206">您必須了解此模型的建立目的，才能了解預測的結果。</span><span class="sxs-lookup"><span data-stu-id="aca60-206">You must understand the purpose for which the model was created to understand the results of prediction.</span></span> <span data-ttu-id="aca60-207">下列查詢範例說明三種不同的案例：</span><span class="sxs-lookup"><span data-stu-id="aca60-207">The following query samples illustrate three different scenarios:</span></span>  
  
-   <span data-ttu-id="aca60-208">傳回分類模型的預測，連同正確預測的機率，然後根據機率篩選結果。</span><span class="sxs-lookup"><span data-stu-id="aca60-208">Returning a prediction for a classification model, together with the probability of the prediction being correct, and then filtering the results by the probability;</span></span>  
  
-   <span data-ttu-id="aca60-209">建立單一查詢來預測關聯。</span><span class="sxs-lookup"><span data-stu-id="aca60-209">Creating a singleton query to predict associations;</span></span>  
  
-   <span data-ttu-id="aca60-210">當輸入和輸出之間的關係為線性時，針對決策樹的一部分擷取迴歸公式。</span><span class="sxs-lookup"><span data-stu-id="aca60-210">Retrieving the regression formula for a part of a decision tree where the relationship between the input and output is linear.</span></span>  
  
###  <a name="sample-query-4-returning-predictions-with-probabilities"></a><a name="bkmk_Query4"></a> <span data-ttu-id="aca60-211">範例查詢 4：傳回包含機率的預測</span><span class="sxs-lookup"><span data-stu-id="aca60-211">Sample Query 4: Returning Predictions with Probabilities</span></span>  
 <span data-ttu-id="aca60-212">下列範例查詢會使用您在 [資料採礦基本教學課程](../../tutorials/basic-data-mining-tutorial.md)中建立的決策樹模型。</span><span class="sxs-lookup"><span data-stu-id="aca60-212">The following sample query uses the decision tree model that was created in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span> <span data-ttu-id="aca60-213">此查詢會從 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] DW 的 dbo.ProspectiveBuyers 資料表傳入一組新的取樣資料，以便預測新資料集中的哪些客戶將購買自行車。</span><span class="sxs-lookup"><span data-stu-id="aca60-213">The query passes in a new set of sample data, from the table dbo.ProspectiveBuyers in [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] DW, to predict which of the customers in the new data set will purchase a bike.</span></span>  
  
 <span data-ttu-id="aca60-214">此查詢使用預測函數 [PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx)，它會傳回一個巢狀資料表，其中包含此模型所探索之機率的有用資訊。</span><span class="sxs-lookup"><span data-stu-id="aca60-214">The query uses the prediction function [PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx), which returns a nested table that contains useful information about the probabilities discovered by the model.</span></span> <span data-ttu-id="aca60-215">此查詢的最終 WHERE 子句會篩選結果，以便只傳回預測為可能購買自行車之機率大於 0% 的客戶。</span><span class="sxs-lookup"><span data-stu-id="aca60-215">The final WHERE clause of the query filters the results to return only those customers who are predicted as likely to buy a bike, with a probability greater than 0%.</span></span>  
  
```  
SELECT  
  [TM_DecisionTree].[Bike Buyer],  
  PredictHistogram([Bike Buyer]) as Results  
From  
  [TM_DecisionTree]  
PREDICTION JOIN  
  OPENQUERY([Adventure Works DW Multidimensional 2012],  
    'SELECT  
      [FirstName],  
      [LastName],  
      [MaritalStatus],  
      [Gender],  
      [YearlyIncome],  
      [TotalChildren],  
      [NumberChildrenAtHome],  
      [HouseOwnerFlag],  
      [NumberCarsOwned]  
    FROM  
      [dbo].[ProspectiveBuyer]  
    ') AS t  
ON  
  [TM_DecisionTree].[First Name] = t.[FirstName] AND  
  [TM_DecisionTree].[Last Name] = t.[LastName] AND  
  [TM_DecisionTree].[Marital Status] = t.[MaritalStatus] AND  
  [TM_DecisionTree].[Gender] = t.[Gender] AND  
  [TM_DecisionTree].[Yearly Income] = t.[YearlyIncome] AND  
  [TM_DecisionTree].[Total Children] = t.[TotalChildren] AND  
  [TM_DecisionTree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
  [TM_DecisionTree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
  [TM_DecisionTree].[Number Cars Owned] = t.[NumberCarsOwned]  
WHERE [Bike Buyer] = 1  
AND PredictProbability([Bike Buyer]) >'.05'  
```  
  
 <span data-ttu-id="aca60-216">依預設， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會傳回具有資料行標籤 **Expression**的巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="aca60-216">By default, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns nested tables with the column label, **Expression**.</span></span> <span data-ttu-id="aca60-217">您可以為傳回的資料行設定別名來變更這個標籤。</span><span class="sxs-lookup"><span data-stu-id="aca60-217">You can change this label by aliasing the column that is returned.</span></span> <span data-ttu-id="aca60-218">如果您這樣做，此別名 (此案例中為 **Results**) 會用來當作資料行標題及巢狀資料表中的值。</span><span class="sxs-lookup"><span data-stu-id="aca60-218">If you do this, the alias (in this case, **Results**) is used as both the column heading and as the value in the nested table.</span></span> <span data-ttu-id="aca60-219">您必須展開此巢狀資料表，才能看到結果。</span><span class="sxs-lookup"><span data-stu-id="aca60-219">You must expand the nested table to see the results.</span></span>  
  
 <span data-ttu-id="aca60-220">自行車購買者 = 1 的範例結果：</span><span class="sxs-lookup"><span data-stu-id="aca60-220">Example results where Bike Buyer = 1:</span></span>  
  
|<span data-ttu-id="aca60-221">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="aca60-221">Bike Buyer</span></span>|<span data-ttu-id="aca60-222">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="aca60-222">$SUPPORT</span></span>|<span data-ttu-id="aca60-223">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="aca60-223">$PROBABILITY</span></span>|<span data-ttu-id="aca60-224">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="aca60-224">$ADJUSTEDPROBABILITY</span></span>|<span data-ttu-id="aca60-225">$VARIANCE</span><span class="sxs-lookup"><span data-stu-id="aca60-225">$VARIANCE</span></span>|<span data-ttu-id="aca60-226">$STDEV</span><span class="sxs-lookup"><span data-stu-id="aca60-226">$STDEV</span></span>|  
|----------------|--------------|------------------|--------------------------|---------------|------------|  
|<span data-ttu-id="aca60-227">1</span><span class="sxs-lookup"><span data-stu-id="aca60-227">1</span></span>|<span data-ttu-id="aca60-228">2540</span><span class="sxs-lookup"><span data-stu-id="aca60-228">2540</span></span>|<span data-ttu-id="aca60-229">0.634849242045644</span><span class="sxs-lookup"><span data-stu-id="aca60-229">0.634849242045644</span></span>|<span data-ttu-id="aca60-230">0.013562168281562</span><span class="sxs-lookup"><span data-stu-id="aca60-230">0.013562168281562</span></span>|<span data-ttu-id="aca60-231">0</span><span class="sxs-lookup"><span data-stu-id="aca60-231">0</span></span>|<span data-ttu-id="aca60-232">0</span><span class="sxs-lookup"><span data-stu-id="aca60-232">0</span></span>|  
|<span data-ttu-id="aca60-233">0</span><span class="sxs-lookup"><span data-stu-id="aca60-233">0</span></span>|<span data-ttu-id="aca60-234">1460</span><span class="sxs-lookup"><span data-stu-id="aca60-234">1460</span></span>|<span data-ttu-id="aca60-235">0.364984174579377</span><span class="sxs-lookup"><span data-stu-id="aca60-235">0.364984174579377</span></span>|<span data-ttu-id="aca60-236">0.00661336932550915</span><span class="sxs-lookup"><span data-stu-id="aca60-236">0.00661336932550915</span></span>|<span data-ttu-id="aca60-237">0</span><span class="sxs-lookup"><span data-stu-id="aca60-237">0</span></span>|<span data-ttu-id="aca60-238">0</span><span class="sxs-lookup"><span data-stu-id="aca60-238">0</span></span>|  
||<span data-ttu-id="aca60-239">0</span><span class="sxs-lookup"><span data-stu-id="aca60-239">0</span></span>|<span data-ttu-id="aca60-240">0.000166583374979177</span><span class="sxs-lookup"><span data-stu-id="aca60-240">0.000166583374979177</span></span>|<span data-ttu-id="aca60-241">0.000166583374979177</span><span class="sxs-lookup"><span data-stu-id="aca60-241">0.000166583374979177</span></span>|<span data-ttu-id="aca60-242">0</span><span class="sxs-lookup"><span data-stu-id="aca60-242">0</span></span>|<span data-ttu-id="aca60-243">0</span><span class="sxs-lookup"><span data-stu-id="aca60-243">0</span></span>|  
  
 <span data-ttu-id="aca60-244">如果提供者不支援階層式資料列集 (例如這裡顯示的內容)，您可以在查詢中使用 FLATTENED 關鍵字，以資料表的形式傳回結果，此資料表包含了用來取代重複資料行值的 Null。</span><span class="sxs-lookup"><span data-stu-id="aca60-244">If your provider does not support hierarchical rowsets, such as those shown here, you can use the FLATTENED keyword in the query to return the results as a table that contains nulls in place of the repeated column values.</span></span> <span data-ttu-id="aca60-245">如需詳細資訊，請參閱[巢狀資料表 &#40;Analysis Services - 資料採礦&#41;](nested-tables-analysis-services-data-mining.md) 或[了解 DMX Select 陳述式](/sql/dmx/understanding-the-dmx-select-statement)。</span><span class="sxs-lookup"><span data-stu-id="aca60-245">For more information, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](nested-tables-analysis-services-data-mining.md) or [Understanding the DMX Select Statement](/sql/dmx/understanding-the-dmx-select-statement).</span></span>  
  
###  <a name="sample-query-5-predicting-associations-from-a-decision-trees-model"></a><a name="bkmk_Query5"></a> <span data-ttu-id="aca60-246">範例查詢 5：從決策樹模型預測關聯</span><span class="sxs-lookup"><span data-stu-id="aca60-246">Sample Query 5: Predicting Associations from a Decision Trees Model</span></span>  
 <span data-ttu-id="aca60-247">下列範例查詢是以關聯採礦結構為基礎。</span><span class="sxs-lookup"><span data-stu-id="aca60-247">The following sample query is based on the Association mining structure.</span></span> <span data-ttu-id="aca60-248">若要依照此範例進行，您可以將新的模型加入至此採礦結構，然後選取 Microsoft 決策樹做為演算法。</span><span class="sxs-lookup"><span data-stu-id="aca60-248">To follow along with this example, you can add a new model to this mining structure, and select Microsoft Decision Trees as the algorithm.</span></span> <span data-ttu-id="aca60-249">如需如何建立關聯採礦模型的詳細資訊，請參閱[第 3 課︰建立購物籃狀況 &#40;中繼資料採礦教學課程&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="aca60-249">For more information on how to create the Association mining structure, see [Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md).</span></span>  
  
 <span data-ttu-id="aca60-250">下列範例查詢為單一查詢，您可以在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中輕鬆地建立此查詢，其方式是選擇欄位，然後從下拉式清單中選取這些欄位的值。</span><span class="sxs-lookup"><span data-stu-id="aca60-250">The following sample query is a singleton query, which you can create easily in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] by choosing fields and then selecting values for those fields from a drop-down list.</span></span>  
  
```  
SELECT PredictAssociation([DT_Association].[v Assoc Seq Line Items],3)  
FROM  
  [DT_Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Patch kit' AS [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 <span data-ttu-id="aca60-251">預期的結果：</span><span class="sxs-lookup"><span data-stu-id="aca60-251">Expected results:</span></span>  
  
|<span data-ttu-id="aca60-252">模型</span><span class="sxs-lookup"><span data-stu-id="aca60-252">Model</span></span>|  
|-----------|  
|<span data-ttu-id="aca60-253">Mountain-200</span><span class="sxs-lookup"><span data-stu-id="aca60-253">Mountain-200</span></span>|  
|<span data-ttu-id="aca60-254">Mountain Tire Tube</span><span class="sxs-lookup"><span data-stu-id="aca60-254">Mountain Tire Tube</span></span>|  
|<span data-ttu-id="aca60-255">Touring Tire Tube</span><span class="sxs-lookup"><span data-stu-id="aca60-255">Touring Tire Tube</span></span>|  
  
 <span data-ttu-id="aca60-256">結果告訴您建議已經購買 Patch Kit 產品的客戶來購買的三件最佳產品。</span><span class="sxs-lookup"><span data-stu-id="aca60-256">The results tell you the three best products to recommend to customers who have purchased the Patch Kit product.</span></span> <span data-ttu-id="aca60-257">當您做出建議時，也可以提供多個產品當作輸入，其方式是輸入值，或是使用 [單一查詢輸入]\*\*\*\* 對話方塊以及加入或移除值。</span><span class="sxs-lookup"><span data-stu-id="aca60-257">You can also provide multiple products as input when you make recommendations, either by typing in values, or by using the **Singleton Query Input** dialog box and adding or removing values.</span></span> <span data-ttu-id="aca60-258">下列範例查詢會示範如何提供多個值，根據這些值進行預測。</span><span class="sxs-lookup"><span data-stu-id="aca60-258">The following sample query shows how the multiple values are provided, upon which to make a prediction.</span></span> <span data-ttu-id="aca60-259">定義輸入值之 SELECT 陳述式中的 UNION 子句會用來連接值。</span><span class="sxs-lookup"><span data-stu-id="aca60-259">Values are connected by a UNION clause in the SELECT statement that defines the input values.</span></span>  
  
```  
SELECT PredictAssociation([DT_Association].[v Assoc Seq Line Items],3)  
From  
  [DT_Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Racing Socks' AS [Model]  
  UNION SELECT 'Women''s Mountain Shorts' AS [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 <span data-ttu-id="aca60-260">預期的結果：</span><span class="sxs-lookup"><span data-stu-id="aca60-260">Expected results:</span></span>  
  
|<span data-ttu-id="aca60-261">模型</span><span class="sxs-lookup"><span data-stu-id="aca60-261">Model</span></span>|  
|-----------|  
|<span data-ttu-id="aca60-262">Long-Sleeve Logo Jersey</span><span class="sxs-lookup"><span data-stu-id="aca60-262">Long-Sleeve Logo Jersey</span></span>|  
|<span data-ttu-id="aca60-263">Mountain-400-W</span><span class="sxs-lookup"><span data-stu-id="aca60-263">Mountain-400-W</span></span>|  
|<span data-ttu-id="aca60-264">Classic Vest</span><span class="sxs-lookup"><span data-stu-id="aca60-264">Classic Vest</span></span>|  
  
###  <a name="sample-query-6-retrieving-a-regression-formula-from-a-decision-trees-model"></a><a name="bkmk_Query6"></a> <span data-ttu-id="aca60-265">範例查詢 6：從決策樹模型擷取迴歸公式</span><span class="sxs-lookup"><span data-stu-id="aca60-265">Sample Query 6: Retrieving a Regression Formula from a Decision Trees Model</span></span>  
 <span data-ttu-id="aca60-266">當您建立的決策樹模型在連續屬性上包含迴歸時，您可以使用迴歸公式來進行預測，或是可以擷取有關此迴歸公式的資訊。</span><span class="sxs-lookup"><span data-stu-id="aca60-266">When you create a decision tree model that contains a regression on a continuous attribute, you can use the regression formula to make predictions, or you can extract information about the regression formula.</span></span> <span data-ttu-id="aca60-267">如需迴歸模型上之查詢的詳細資訊，請參閱 [線性迴歸模型查詢範例](linear-regression-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="aca60-267">For more information about queries on regression models, see [Linear Regression Model Query Examples](linear-regression-model-query-examples.md).</span></span>  
  
 <span data-ttu-id="aca60-268">如果決策樹模型包含迴歸節點及分散於離散屬性或範圍上之節點的混合，您只能建立傳回迴歸節點的查詢。</span><span class="sxs-lookup"><span data-stu-id="aca60-268">If a decision trees model contains a mixture of regression nodes and nodes that split on discrete attributes or ranges, you can create a query that returns only the regression node.</span></span> <span data-ttu-id="aca60-269">NODE_DISTRIBUTION 資料表包含迴歸公式的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="aca60-269">The NODE_DISTRIBUTION table contains the details of the regression formula.</span></span> <span data-ttu-id="aca60-270">在此範例中，資料行會扁平化，而且會設定 NODE_DISTRIBUTION 資料表的別名來方便檢視。</span><span class="sxs-lookup"><span data-stu-id="aca60-270">In this example, the columns are flattened and the NODE_DISTRIBUTION table is aliased for easier viewing.</span></span> <span data-ttu-id="aca60-271">但是在此模型中，未找到任何迴歸輸入變數可以將 Income 與其他連續屬性產生關聯。</span><span class="sxs-lookup"><span data-stu-id="aca60-271">However, in this model, no regressors were found to relate Income with other continuous attributes.</span></span> <span data-ttu-id="aca60-272">在這類情況下， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會傳回此屬性的平均值以及模型中該屬性的總變異數。</span><span class="sxs-lookup"><span data-stu-id="aca60-272">In such cases, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns the mean value of the attribute and the total variance in the model for that attribute.</span></span>  
  
```  
SELECT FLATTENED NODE_DISTRIBUTION AS t  
FROM DT_Predict. CONTENT  
WHERE NODE_TYPE = 25  
```  
  
 <span data-ttu-id="aca60-273">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="aca60-273">Example results:</span></span>  
  
|<span data-ttu-id="aca60-274">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="aca60-274">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="aca60-275">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="aca60-275">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="aca60-276">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="aca60-276">t.SUPPORT</span></span>|<span data-ttu-id="aca60-277">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="aca60-277">t.PROBABILITY</span></span>|<span data-ttu-id="aca60-278">t.VARIANCE</span><span class="sxs-lookup"><span data-stu-id="aca60-278">t.VARIANCE</span></span>|<span data-ttu-id="aca60-279">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="aca60-279">t.VALUETYPE</span></span>|  
|-----------------------|------------------------|---------------|-------------------|----------------|-----------------|  
|<span data-ttu-id="aca60-280">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="aca60-280">Yearly Income</span></span>|<span data-ttu-id="aca60-281">Missing</span><span class="sxs-lookup"><span data-stu-id="aca60-281">Missing</span></span>|<span data-ttu-id="aca60-282">0</span><span class="sxs-lookup"><span data-stu-id="aca60-282">0</span></span>|<span data-ttu-id="aca60-283">0.000457142857142857</span><span class="sxs-lookup"><span data-stu-id="aca60-283">0.000457142857142857</span></span>|<span data-ttu-id="aca60-284">0</span><span class="sxs-lookup"><span data-stu-id="aca60-284">0</span></span>|<span data-ttu-id="aca60-285">1</span><span class="sxs-lookup"><span data-stu-id="aca60-285">1</span></span>|  
|<span data-ttu-id="aca60-286">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="aca60-286">Yearly Income</span></span>|<span data-ttu-id="aca60-287">57220.8876687257</span><span class="sxs-lookup"><span data-stu-id="aca60-287">57220.8876687257</span></span>|<span data-ttu-id="aca60-288">17484</span><span class="sxs-lookup"><span data-stu-id="aca60-288">17484</span></span>|<span data-ttu-id="aca60-289">0.999542857142857</span><span class="sxs-lookup"><span data-stu-id="aca60-289">0.999542857142857</span></span>|<span data-ttu-id="aca60-290">1041275619.52776</span><span class="sxs-lookup"><span data-stu-id="aca60-290">1041275619.52776</span></span>|<span data-ttu-id="aca60-291">3</span><span class="sxs-lookup"><span data-stu-id="aca60-291">3</span></span>|  
||<span data-ttu-id="aca60-292">57220.8876687257</span><span class="sxs-lookup"><span data-stu-id="aca60-292">57220.8876687257</span></span>|<span data-ttu-id="aca60-293">0</span><span class="sxs-lookup"><span data-stu-id="aca60-293">0</span></span>|<span data-ttu-id="aca60-294">0</span><span class="sxs-lookup"><span data-stu-id="aca60-294">0</span></span>|<span data-ttu-id="aca60-295">1041216662.54387</span><span class="sxs-lookup"><span data-stu-id="aca60-295">1041216662.54387</span></span>|<span data-ttu-id="aca60-296">11</span><span class="sxs-lookup"><span data-stu-id="aca60-296">11</span></span>|  
  
 <span data-ttu-id="aca60-297">如需迴歸模型中所用的值類型和統計資料的詳細資訊，請參閱[線性迴歸模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="aca60-297">For more information about the value types and the statistics used in regression models, see [Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md).</span></span>  
  
## <a name="list-of-prediction-functions"></a><span data-ttu-id="aca60-298">預測函數的清單</span><span class="sxs-lookup"><span data-stu-id="aca60-298">List of Prediction Functions</span></span>  
 <span data-ttu-id="aca60-299">所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 演算法都支援一組常用的函數。</span><span class="sxs-lookup"><span data-stu-id="aca60-299">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="aca60-300">不過， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 決策樹演算法支援下表所列出的其他函數。</span><span class="sxs-lookup"><span data-stu-id="aca60-300">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm supports the additional functions listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aca60-301">預測函數</span><span class="sxs-lookup"><span data-stu-id="aca60-301">Prediction Function</span></span>|<span data-ttu-id="aca60-302">使用量</span><span class="sxs-lookup"><span data-stu-id="aca60-302">Usage</span></span>|  
|[<span data-ttu-id="aca60-303">IsDescendant &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="aca60-303">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="aca60-304">確定某個節點是否為模型中另一個節點的子系。</span><span class="sxs-lookup"><span data-stu-id="aca60-304">Determines whether one node is a child of another node in the model.</span></span>|  
|[<span data-ttu-id="aca60-305">IsInNode &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="aca60-305">IsInNode &#40;DMX&#41;</span></span>](/sql/dmx/isinnode-dmx)|<span data-ttu-id="aca60-306">指示指定的節點是否包含目前案例。</span><span class="sxs-lookup"><span data-stu-id="aca60-306">Indicates whether the specified node contains the current case.</span></span>|  
|[<span data-ttu-id="aca60-307">PredictAdjustedProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="aca60-307">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="aca60-308">傳回加權機率。</span><span class="sxs-lookup"><span data-stu-id="aca60-308">Returns the weighted probability.</span></span>|  
|[<span data-ttu-id="aca60-309">PredictAssociation &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="aca60-309">PredictAssociation &#40;DMX&#41;</span></span>](/sql/dmx/predictassociation-dmx)|<span data-ttu-id="aca60-310">預測關聯資料集的成員資格。</span><span class="sxs-lookup"><span data-stu-id="aca60-310">Predicts membership in an associative dataset.</span></span>|  
|[<span data-ttu-id="aca60-311">PredictHistogram &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="aca60-311">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="aca60-312">傳回與目前預測值相關之值的資料表。</span><span class="sxs-lookup"><span data-stu-id="aca60-312">Returns a table of values related to the current predicted value.</span></span>|  
|[<span data-ttu-id="aca60-313">PredictNodeId &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="aca60-313">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="aca60-314">傳回每個案例的 Node_ID。</span><span class="sxs-lookup"><span data-stu-id="aca60-314">Returns the Node_ID for each case.</span></span>|  
|[<span data-ttu-id="aca60-315">PredictProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="aca60-315">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="aca60-316">傳回預測值的機率。</span><span class="sxs-lookup"><span data-stu-id="aca60-316">Returns probability for the predicted value.</span></span>|  
|[<span data-ttu-id="aca60-317">PredictStdev &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="aca60-317">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="aca60-318">傳回指定之資料行的預測標準差。</span><span class="sxs-lookup"><span data-stu-id="aca60-318">Returns the predicted standard deviation for the specified column.</span></span>|  
|[<span data-ttu-id="aca60-319">PredictSupport &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="aca60-319">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="aca60-320">傳回指定狀態的支援值。</span><span class="sxs-lookup"><span data-stu-id="aca60-320">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="aca60-321">PredictVariance &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="aca60-321">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="aca60-322">傳回指定之資料行的變異數。</span><span class="sxs-lookup"><span data-stu-id="aca60-322">Returns the variance of a specified column.</span></span>|  
  
 <span data-ttu-id="aca60-323">如需所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 演算法通用函數的清單，請參閱[一般預測函數 &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx)。</span><span class="sxs-lookup"><span data-stu-id="aca60-323">For a list of the functions that are common to all [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, see [General Prediction Functions &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).</span></span> <span data-ttu-id="aca60-324">如需特定函數的語法，請參閱[資料採礦延伸模組 &#40;DMX&#41; 函數參考](/sql/dmx/data-mining-extensions-dmx-function-reference)。</span><span class="sxs-lookup"><span data-stu-id="aca60-324">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aca60-325">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aca60-325">See Also</span></span>  
 <span data-ttu-id="aca60-326">[資料採礦查詢](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="aca60-326">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="aca60-327">[Microsoft 決策樹演算法](microsoft-decision-trees-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="aca60-327">[Microsoft Decision Trees Algorithm](microsoft-decision-trees-algorithm.md) </span></span>  
 <span data-ttu-id="aca60-328">[Microsoft 決策樹演算法技術參考](microsoft-decision-trees-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="aca60-328">[Microsoft Decision Trees Algorithm Technical Reference](microsoft-decision-trees-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="aca60-329">決策樹模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="aca60-329">Mining Model Content for Decision Tree Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)  
  
  
