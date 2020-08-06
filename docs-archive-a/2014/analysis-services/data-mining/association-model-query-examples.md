---
title: 關聯模型查詢範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- association algorithms [Analysis Services]
- rules [Data Mining]
- association rules
- content queries [DMX]
ms.assetid: 68b39f5c-c439-44ac-8046-6f2d36649059
author: minewiskan
ms.author: owend
ms.openlocfilehash: a19eb2302639c7f13d48a8778969bbeca4fee18d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605951"
---
# <a name="association-model-query-examples"></a><span data-ttu-id="ad495-102">關聯模型查詢範例</span><span class="sxs-lookup"><span data-stu-id="ad495-102">Association Model Query Examples</span></span>
  <span data-ttu-id="ad495-103">在您針對資料採礦模型建立查詢時，可以建立內容查詢以提供有關在分析期間所發現的規則和項目集的詳細資料，或建立預測查詢以使用在資料中發現的關聯來進行預測。</span><span class="sxs-lookup"><span data-stu-id="ad495-103">When you create a query against a data mining model, you can create either a content query, which provides details about the rules and itemsets discovered during analysis, or you can create a prediction query, which uses the associations discovered in the data to make predictions.</span></span> <span data-ttu-id="ad495-104">對關聯模型而言，預測通常會以規則為基礎，而且可以用來進行推薦，而對內容所做的查詢則通常會探索項目集之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="ad495-104">For an association model, predictions typically are based on rules, and can be used to make recommendations, whereas queries on content typically explore the relationship among itemsets.</span></span> <span data-ttu-id="ad495-105">您也可以擷取有關模型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ad495-105">You can also retrieve metadata about the model.</span></span>  
  
 <span data-ttu-id="ad495-106">本節說明如何針對以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 關聯規則演算法為基礎的模型來建立此類查詢。</span><span class="sxs-lookup"><span data-stu-id="ad495-106">This section explains how to create these kinds of queries for models that are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm.</span></span>  
  
 <span data-ttu-id="ad495-107">**內容查詢**</span><span class="sxs-lookup"><span data-stu-id="ad495-107">**Content Queries**</span></span>  
  
 [<span data-ttu-id="ad495-108">使用 DMX 取得模型中繼資料</span><span class="sxs-lookup"><span data-stu-id="ad495-108">Getting model metadata data by using DMX</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="ad495-109">從結構描述資料列集取得中繼資料</span><span class="sxs-lookup"><span data-stu-id="ad495-109">Getting metadata from the schema rowset</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="ad495-110">擷取模型的原始參數</span><span class="sxs-lookup"><span data-stu-id="ad495-110">Retrieving the original parameters for the model</span></span>](#bkmk_Query3)  
  
 [<span data-ttu-id="ad495-111">擷取項目集和產品的清單</span><span class="sxs-lookup"><span data-stu-id="ad495-111">Retrieving a list of itemsets and products</span></span>](#bkmk_Query4)  
  
 [<span data-ttu-id="ad495-112">傳回前 10 個項目集</span><span class="sxs-lookup"><span data-stu-id="ad495-112">Returning the top 10 itemsets</span></span>](#bkmk_Query5)  
  
 <span data-ttu-id="ad495-113">**預測查詢**</span><span class="sxs-lookup"><span data-stu-id="ad495-113">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="ad495-114">預測關聯的項目</span><span class="sxs-lookup"><span data-stu-id="ad495-114">Predicting associated items</span></span>](#bkmk_Query6)  
  
 [<span data-ttu-id="ad495-115">判斷相關項目集的信心</span><span class="sxs-lookup"><span data-stu-id="ad495-115">Determining confidence for related itemsets</span></span>](#bkmk_Query7)  
  
##  <a name="finding-information-about-the-model"></a><a name="bkmk_top2"></a> <span data-ttu-id="ad495-116">尋找有關模型的資訊</span><span class="sxs-lookup"><span data-stu-id="ad495-116">Finding Information about the Model</span></span>  
 <span data-ttu-id="ad495-117">所有的採礦模型都會公開演算法根據標準化結構描述所學習的內容，也稱為採礦模型結構描述資料列集。</span><span class="sxs-lookup"><span data-stu-id="ad495-117">All mining models expose the content learned by the algorithm according to a standardized schema, which is named the mining model schema rowset.</span></span> <span data-ttu-id="ad495-118">您可以使用資料採礦延伸模組 (DMX) 陳述式或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 預存程序，針對採礦模型結構描述資料列集建立查詢。</span><span class="sxs-lookup"><span data-stu-id="ad495-118">You can create queries against the mining model schema rowset either by using Data Mining Extensions (DMX) statements, or by using [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stored procedures.</span></span> <span data-ttu-id="ad495-119">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，您也可以使用類似 SQL 的語法，將結構描述資料列集當做系統資料表直接進行查詢。</span><span class="sxs-lookup"><span data-stu-id="ad495-119">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can also query the schema rowsets directly as system tables, by using a SQL-like syntax.</span></span>  
  
###  <a name="sample-query-1-getting-model-metadata-by-using-dmx"></a><a name="bkmk_Query1"></a> <span data-ttu-id="ad495-120">範例查詢 1：使用 DMX 取得模型中繼資料</span><span class="sxs-lookup"><span data-stu-id="ad495-120">Sample Query 1: Getting Model Metadata by Using DMX</span></span>  
 <span data-ttu-id="ad495-121">下列查詢會傳回有關關聯模型 `Association`的基本中繼資料，例如模型的名稱、模型儲存位置所在的資料庫，以及模型中子節點的數目。</span><span class="sxs-lookup"><span data-stu-id="ad495-121">The following query returns basic metadata about the association model, `Association`, such as the name of the model, the database where the model is stored, and the number of child nodes in the model.</span></span> <span data-ttu-id="ad495-122">此查詢會使用 DMX 內容查詢從模型的父節點擷取中繼資料：</span><span class="sxs-lookup"><span data-stu-id="ad495-122">This query uses a DMX content query to retrieve the metadata from the parent node of the model:</span></span>  
  
```  
SELECT MODEL_CATALOG, MODEL_NAME, NODE_CAPTION,   
NODE_SUPPORT, [CHILDREN_CARDINALITY], NODE_DESCRIPTION  
FROM Association.CONTENT  
WHERE NODE_TYPE = 1  
```  
  
> [!NOTE]  
>  <span data-ttu-id="ad495-123">您必須將資料行 CHILDREN_CARDINALITY 的名稱包含在括號中，好與相同名稱的 MDX 保留關鍵字加以區別。</span><span class="sxs-lookup"><span data-stu-id="ad495-123">You must enclose the name of the column, CHILDREN_CARDINALITY, in brackets to distinguish it from the MDX reserved keyword of the same name.</span></span>  
  
 <span data-ttu-id="ad495-124">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="ad495-124">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad495-125">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ad495-125">MODEL_CATALOG</span></span>|<span data-ttu-id="ad495-126">關聯測試</span><span class="sxs-lookup"><span data-stu-id="ad495-126">Association Test</span></span>|  
|<span data-ttu-id="ad495-127">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="ad495-127">MODEL_NAME</span></span>|<span data-ttu-id="ad495-128">關聯</span><span class="sxs-lookup"><span data-stu-id="ad495-128">Association</span></span>|  
|<span data-ttu-id="ad495-129">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="ad495-129">NODE_CAPTION</span></span>|<span data-ttu-id="ad495-130">關聯規則模型</span><span class="sxs-lookup"><span data-stu-id="ad495-130">Association Rules Model</span></span>|  
|<span data-ttu-id="ad495-131">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="ad495-131">NODE_SUPPORT</span></span>|<span data-ttu-id="ad495-132">14879</span><span class="sxs-lookup"><span data-stu-id="ad495-132">14879</span></span>|  
|<span data-ttu-id="ad495-133">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="ad495-133">CHILDREN_CARDINALITY</span></span>|<span data-ttu-id="ad495-134">942</span><span class="sxs-lookup"><span data-stu-id="ad495-134">942</span></span>|  
|<span data-ttu-id="ad495-135">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ad495-135">NODE_DESCRIPTION</span></span>|<span data-ttu-id="ad495-136">Association Rules Model; ITEMSET_COUNT=679; RULE_COUNT=263; MIN_SUPPORT=14; MAX_SUPPORT=4334; MIN_ITEMSET_SIZE=0; MAX_ITEMSET_SIZE=3; MIN_PROBABILITY=0.400390625; MAX_PROBABILITY=1; MIN_LIFT=0.14309369632511; MAX_LIFT=1.95758227647523</span><span class="sxs-lookup"><span data-stu-id="ad495-136">Association Rules Model; ITEMSET_COUNT=679; RULE_COUNT=263; MIN_SUPPORT=14; MAX_SUPPORT=4334; MIN_ITEMSET_SIZE=0; MAX_ITEMSET_SIZE=3; MIN_PROBABILITY=0.400390625; MAX_PROBABILITY=1; MIN_LIFT=0.14309369632511; MAX_LIFT=1.95758227647523</span></span>|  
  
 <span data-ttu-id="ad495-137">如需這些資料行在關聯模型中的定義，請參閱 [關聯模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-association-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="ad495-137">For a definition of what these columns mean in an association model, see [Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-association-models-analysis-services-data-mining.md).</span></span>  
  
 [<span data-ttu-id="ad495-138">回到頁首</span><span class="sxs-lookup"><span data-stu-id="ad495-138">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-2-getting-additional-metadata-from-the-schema-rowset"></a><a name="bkmk_Query2"></a> <span data-ttu-id="ad495-139">範例查詢 2：從結構描述資料列集取得其他的中繼資料</span><span class="sxs-lookup"><span data-stu-id="ad495-139">Sample Query 2: Getting Additional Metadata from the Schema Rowset</span></span>  
 <span data-ttu-id="ad495-140">藉由查詢資料採礦結構描述資料列集，您可以找到與 DMX 內容查詢所傳回的相同的資訊。</span><span class="sxs-lookup"><span data-stu-id="ad495-140">By querying the data mining schema rowset, you can find the same information that is returned in a DMX content query.</span></span> <span data-ttu-id="ad495-141">不過，結構描述資料列集會提供一些其他的資料行，例如上次處理模型的日期、採礦結構，以及用來當做可預測屬性的資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="ad495-141">However, the schema rowset provides some additional columns, such as the date the model was last processed, the mining structure, and the name of the column used as the predictable attribute.</span></span>  
  
```  
SELECT MODEL_CATALOG, MODEL_NAME, SERVICE_NAME, PREDICTION_ENTITY,   
MINING_STRUCTURE, LAST_PROCESSED  
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Association'  
```  
  
 <span data-ttu-id="ad495-142">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="ad495-142">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad495-143">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ad495-143">MODEL_CATALOG</span></span>|<span data-ttu-id="ad495-144">Adventure Works DW Multidimensional 2012</span><span class="sxs-lookup"><span data-stu-id="ad495-144">Adventure Works DW Multidimensional 2012</span></span>|  
|<span data-ttu-id="ad495-145">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="ad495-145">MODEL_NAME</span></span>|<span data-ttu-id="ad495-146">關聯</span><span class="sxs-lookup"><span data-stu-id="ad495-146">Association</span></span>|  
|<span data-ttu-id="ad495-147">SERVICE_NAME</span><span class="sxs-lookup"><span data-stu-id="ad495-147">SERVICE_NAME</span></span>|<span data-ttu-id="ad495-148">關聯規則模型</span><span class="sxs-lookup"><span data-stu-id="ad495-148">Association Rules Model</span></span>|  
|<span data-ttu-id="ad495-149">PREDICTION_ENTITY</span><span class="sxs-lookup"><span data-stu-id="ad495-149">PREDICTION_ENTITY</span></span>|<span data-ttu-id="ad495-150">v Assoc Seq Line Items</span><span class="sxs-lookup"><span data-stu-id="ad495-150">v Assoc Seq Line Items</span></span>|  
|<span data-ttu-id="ad495-151">MINING_STRUCTURE</span><span class="sxs-lookup"><span data-stu-id="ad495-151">MINING_STRUCTURE</span></span>|<span data-ttu-id="ad495-152">關聯</span><span class="sxs-lookup"><span data-stu-id="ad495-152">Association</span></span>|  
|<span data-ttu-id="ad495-153">LAST_PROCESSED</span><span class="sxs-lookup"><span data-stu-id="ad495-153">LAST_PROCESSED</span></span>|<span data-ttu-id="ad495-154">9/29/2007 10:21:24 下午</span><span class="sxs-lookup"><span data-stu-id="ad495-154">9/29/2007 10:21:24 PM</span></span>|  
  
 [<span data-ttu-id="ad495-155">回到頁首</span><span class="sxs-lookup"><span data-stu-id="ad495-155">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-3-retrieving-original-parameters-for-model"></a><a name="bkmk_Query3"></a> <span data-ttu-id="ad495-156">範例查詢 3：擷取模型的原始參數</span><span class="sxs-lookup"><span data-stu-id="ad495-156">Sample Query 3: Retrieving Original Parameters for Model</span></span>  
 <span data-ttu-id="ad495-157">下列查詢會傳回單一資料行，其中包含有關在建立模型時所使用參數設定的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ad495-157">The following query returns a single column that contains details about the parameter settings that were used when the model was created.</span></span>  
  
```  
SELECT MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Association'  
```  
  
 <span data-ttu-id="ad495-158">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="ad495-158">Example results:</span></span>  
  
 <span data-ttu-id="ad495-159">MAXIMUM_ITEMSET_COUNT=200000,MAXIMUM_ITEMSET_SIZE=3,MAXIMUM_SUPPORT=1,MINIMUM_SUPPORT=9.40923449156529E-04,MINIMUM_IMPORTANCE=-999999999,MINIMUM_ITEMSET_SIZE=0,MINIMUM_PROBABILITY=0.4</span><span class="sxs-lookup"><span data-stu-id="ad495-159">MAXIMUM_ITEMSET_COUNT=200000,MAXIMUM_ITEMSET_SIZE=3,MAXIMUM_SUPPORT=1,MINIMUM_SUPPORT=9.40923449156529E-04,MINIMUM_IMPORTANCE=-999999999,MINIMUM_ITEMSET_SIZE=0,MINIMUM_PROBABILITY=0.4</span></span>  
  
 [<span data-ttu-id="ad495-160">回到頁首</span><span class="sxs-lookup"><span data-stu-id="ad495-160">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="finding-information-about-rules-and-itemsets"></a><span data-ttu-id="ad495-161">尋找有關規則和項目集的資訊</span><span class="sxs-lookup"><span data-stu-id="ad495-161">Finding Information about Rules and Itemsets</span></span>  
 <span data-ttu-id="ad495-162">關聯模型有兩種常見用法：探索有關常用項目集的詳細資訊，以及擷取有關特定規則和項目集的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ad495-162">There are two common uses of an association model: to discover information about frequent itemsets, and to extract details about particular rules and itemsets.</span></span> <span data-ttu-id="ad495-163">例如，您可能想要擷取計分為特別有趣的規則清單，或建立最常見項目集的清單。</span><span class="sxs-lookup"><span data-stu-id="ad495-163">For example, you might want to extract a list of rules that were scored as being especially interesting, or create a list of the most common itemsets.</span></span> <span data-ttu-id="ad495-164">您可以使用 DMX 內容查詢擷取此類資訊。</span><span class="sxs-lookup"><span data-stu-id="ad495-164">You retrieve such information by using a DMX content query.</span></span> <span data-ttu-id="ad495-165">也可以使用 [Microsoft 關聯檢視器]\*\*\*\* 瀏覽此資訊。</span><span class="sxs-lookup"><span data-stu-id="ad495-165">You can also browse this information by using the **Microsoft Association Viewer**.</span></span>  
  
###  <a name="sample-query-4-retrieving-list-of-itemsets-and-products"></a><a name="bkmk_Query4"></a> <span data-ttu-id="ad495-166">範例查詢 4：擷取項目集和產品的清單</span><span class="sxs-lookup"><span data-stu-id="ad495-166">Sample Query 4: Retrieving List of Itemsets and Products</span></span>  
 <span data-ttu-id="ad495-167">下列查詢會擷取所有的項目集，並附上列出每個項目集中所包含產品的巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="ad495-167">The following query retrieves all of the itemsets, together with a nested table that lists the products included in each itemset.</span></span> <span data-ttu-id="ad495-168">NODE_NAME 資料行包含項目集在模型內的唯一識別碼，NODE_CAPTION 則提供項目的文字描述。</span><span class="sxs-lookup"><span data-stu-id="ad495-168">The NODE_NAME column contains the unique ID of the itemset within the model, whereas the NODE_CAPTION provides a text description of the items.</span></span> <span data-ttu-id="ad495-169">在此範例中，巢狀資料表會扁平化，使包含兩個產品的項目集會在結果中產品兩個資料列。</span><span class="sxs-lookup"><span data-stu-id="ad495-169">In this example, the nested table is flattened, so that an itemset that contains two products generates two rows in the results.</span></span> <span data-ttu-id="ad495-170">如果用戶端支援階層資料，則您可以省略 FLATTENED 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ad495-170">You can omit the FLATTENED keyword if your client supports hierarchical data.</span></span>  
  
```  
SELECT FLATTENED NODE_NAME, NODE_CAPTION,  
NODE_PROBABILITY, NODE_SUPPORT,  
(SELECT ATTRIBUTE_NAME FROM NODE_DISTRIBUTION) as PurchasedProducts  
FROM Association.CONTENT  
WHERE NODE_TYPE = 7  
```  
  
 <span data-ttu-id="ad495-171">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="ad495-171">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad495-172">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="ad495-172">NODE_NAME</span></span>|<span data-ttu-id="ad495-173">37</span><span class="sxs-lookup"><span data-stu-id="ad495-173">37</span></span>|  
|<span data-ttu-id="ad495-174">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="ad495-174">NODE_CAPTION</span></span>|<span data-ttu-id="ad495-175">Sport-100 = Existing</span><span class="sxs-lookup"><span data-stu-id="ad495-175">Sport-100 = Existing</span></span>|  
|<span data-ttu-id="ad495-176">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="ad495-176">NODE_PROBABILITY</span></span>|<span data-ttu-id="ad495-177">0.291283016331743</span><span class="sxs-lookup"><span data-stu-id="ad495-177">0.291283016331743</span></span>|  
|<span data-ttu-id="ad495-178">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="ad495-178">NODE_SUPPORT</span></span>|<span data-ttu-id="ad495-179">4334</span><span class="sxs-lookup"><span data-stu-id="ad495-179">4334</span></span>|  
|<span data-ttu-id="ad495-180">PURCHASEDPRODUCTS.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="ad495-180">PURCHASEDPRODUCTS.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="ad495-181">v Assoc Seq Line Items(Sport-100)</span><span class="sxs-lookup"><span data-stu-id="ad495-181">v Assoc Seq Line Items(Sport-100)</span></span>|  
  
 [<span data-ttu-id="ad495-182">回到頁首</span><span class="sxs-lookup"><span data-stu-id="ad495-182">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-5-returning-top-10-itemsets"></a><a name="bkmk_Query5"></a> <span data-ttu-id="ad495-183">範例查詢 5：傳回前 10 個項目集</span><span class="sxs-lookup"><span data-stu-id="ad495-183">Sample Query 5: Returning Top 10 Itemsets</span></span>  
 <span data-ttu-id="ad495-184">此範例示範如何使用 DMX 依預設所提供的一些群組和排序函數。</span><span class="sxs-lookup"><span data-stu-id="ad495-184">This example demonstrates how to use some of the grouping and ordering functions that DMX provides by default.</span></span> <span data-ttu-id="ad495-185">在藉由每個節點的支援進行排序時，查詢會傳回前 10 個項目集。</span><span class="sxs-lookup"><span data-stu-id="ad495-185">The query returns the top 10 itemsets when ordered by the support for each node.</span></span> <span data-ttu-id="ad495-186">請注意，您不需要像在 Transact-SQL 中一樣明確地將結果分組，不過可以在每個查詢中只使用一個彙總函式。</span><span class="sxs-lookup"><span data-stu-id="ad495-186">Note that you do not need to explicitly group the results, as you would in Transact-SQL; however, you can use only one aggregate function in each query.</span></span>  
  
```  
SELECT TOP 10 (NODE_SUPPORT),NODE_NAME, NODE_CAPTION  
FROM Association.CONTENT  
WHERE NODE_TYPE = 7  
```  
  
 <span data-ttu-id="ad495-187">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="ad495-187">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad495-188">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="ad495-188">NODE_SUPPORT</span></span>|<span data-ttu-id="ad495-189">4334</span><span class="sxs-lookup"><span data-stu-id="ad495-189">4334</span></span>|  
|<span data-ttu-id="ad495-190">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="ad495-190">NODE_NAME</span></span>|<span data-ttu-id="ad495-191">37</span><span class="sxs-lookup"><span data-stu-id="ad495-191">37</span></span>|  
|<span data-ttu-id="ad495-192">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="ad495-192">NODE_CAPTION</span></span>|<span data-ttu-id="ad495-193">Sport-100 = Existing</span><span class="sxs-lookup"><span data-stu-id="ad495-193">Sport-100 = Existing</span></span>|  
  
 [<span data-ttu-id="ad495-194">回到頁首</span><span class="sxs-lookup"><span data-stu-id="ad495-194">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="making-predictions-using-the-model"></a><span data-ttu-id="ad495-195">使用模型進行預測</span><span class="sxs-lookup"><span data-stu-id="ad495-195">Making Predictions using the Model</span></span>  
 <span data-ttu-id="ad495-196">關聯規則模型常用來根據項目集中發現的關聯而產生建議。</span><span class="sxs-lookup"><span data-stu-id="ad495-196">An association rules model is often used to generate recommendations, which are based on correlations discovered in the itemsets.</span></span> <span data-ttu-id="ad495-197">因此，當您根據關聯規則模型建立預測查詢時，通常是使用模型中的規則來根據新資料進行猜測。</span><span class="sxs-lookup"><span data-stu-id="ad495-197">Therefore, when you create a prediction query based on an association rules model, you are typically using the rules in the model to make guesses based on new data.</span></span>  <span data-ttu-id="ad495-198">[PredictAssociation &#40;DMX&#41;](/sql/dmx/predictassociation-dmx) 是可傳回建議的函數，提供數個引數，可用來自訂查詢結果。</span><span class="sxs-lookup"><span data-stu-id="ad495-198">[PredictAssociation &#40;DMX&#41;](/sql/dmx/predictassociation-dmx) is the function that returns recommendations, and has several arguments that you can use to customize the query results.</span></span>  
  
 <span data-ttu-id="ad495-199">另一個說明關聯模型上的查詢可能有用的範例，是傳回不同規則及項目集的信心，讓您可以比較不同交叉銷售策略的效能。</span><span class="sxs-lookup"><span data-stu-id="ad495-199">Another example of where queries on an association model might be useful is to return the confidence for various rules and itemsets so that you can compare the effectiveness of different cross-sell strategies.</span></span> <span data-ttu-id="ad495-200">下列範例說明如何建立此類查詢。</span><span class="sxs-lookup"><span data-stu-id="ad495-200">The following examples illustrate how to create such queries.</span></span>  
  
###  <a name="sample-query-6-predicting-associated-items"></a><a name="bkmk_Query6"></a> <span data-ttu-id="ad495-201">範例查詢 6：預測相關聯項目</span><span class="sxs-lookup"><span data-stu-id="ad495-201">Sample Query 6: Predicting Associated Items</span></span>  
 <span data-ttu-id="ad495-202">這個範例會使用[中繼資料採礦教學課程 &#40;Analysis Services - 資料採礦 &#41;](../../tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) 中建立的關聯模型。</span><span class="sxs-lookup"><span data-stu-id="ad495-202">This example uses the Association model created in the [Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).</span></span> <span data-ttu-id="ad495-203">該模型示範如何建立預測查詢，以告訴您要向已購買特定產品的客戶建議什麼產品。</span><span class="sxs-lookup"><span data-stu-id="ad495-203">It demonstrates how to create a prediction query that tells you what products to recommend to a customer who has purchased a particular product.</span></span> <span data-ttu-id="ad495-204">此類型的查詢 (在 `SELECT...UNION` 陳述式中向模型提供值) 稱為單一查詢。</span><span class="sxs-lookup"><span data-stu-id="ad495-204">This type of query, where you provide values to the model in a `SELECT...UNION` statement, is called a singleton query.</span></span> <span data-ttu-id="ad495-205">因為與新值相對應的可預測模型資料行是巢狀資料表，所以您必須使用一個 `SELECT` 子句將新值對應到巢狀資料表資料行 `[Model]`，並用另一個 `SELECT` 子句將巢狀資料表資料行對應到案例層級資料行 `[v Assoc Seq Line Items]`。</span><span class="sxs-lookup"><span data-stu-id="ad495-205">Because the predictable model column that corresponds to the new values is a nested table, you must use one `SELECT` clause to map the new value to the nested table column, `[Model]`, and another `SELECT` clause to map the nested table column to the case-level column, `[v Assoc Seq Line Items]`.</span></span> <span data-ttu-id="ad495-206">將關鍵 INCLUDE-STATISTICS 加入至查詢可讓您看到建議的機率和支援。</span><span class="sxs-lookup"><span data-stu-id="ad495-206">Adding the keyword INCLUDE-STATISTICS to the query lets you see the probability and support for the recommendations.</span></span>  
  
```  
SELECT PredictAssociation([Association].[vAssocSeqLineItems],INCLUDE_STATISTICS, 3)  
FROM [Association]  
NATURAL PREDICTION JOIN   
(SELECT  
(SELECT 'Classic Vest' as [Model])  
AS [v Assoc Seq Line Items])  
AS t  
```  
  
 <span data-ttu-id="ad495-207">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="ad495-207">Example results:</span></span>  
  
|<span data-ttu-id="ad495-208">模型</span><span class="sxs-lookup"><span data-stu-id="ad495-208">Model</span></span>|<span data-ttu-id="ad495-209">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="ad495-209">$SUPPORT</span></span>|<span data-ttu-id="ad495-210">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="ad495-210">$PROBABILITY</span></span>|<span data-ttu-id="ad495-211">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="ad495-211">$ADJUSTEDPROBABILITY</span></span>|  
|-----------|--------------|------------------|--------------------------|  
|<span data-ttu-id="ad495-212">Sport-100</span><span class="sxs-lookup"><span data-stu-id="ad495-212">Sport-100</span></span>|<span data-ttu-id="ad495-213">4334</span><span class="sxs-lookup"><span data-stu-id="ad495-213">4334</span></span>|<span data-ttu-id="ad495-214">0.291283</span><span class="sxs-lookup"><span data-stu-id="ad495-214">0.291283</span></span>|<span data-ttu-id="ad495-215">0.252696</span><span class="sxs-lookup"><span data-stu-id="ad495-215">0.252696</span></span>|  
|<span data-ttu-id="ad495-216">Water Bottle</span><span class="sxs-lookup"><span data-stu-id="ad495-216">Water Bottle</span></span>|<span data-ttu-id="ad495-217">2866</span><span class="sxs-lookup"><span data-stu-id="ad495-217">2866</span></span>|<span data-ttu-id="ad495-218">0.19262</span><span class="sxs-lookup"><span data-stu-id="ad495-218">0.19262</span></span>|<span data-ttu-id="ad495-219">0.175205</span><span class="sxs-lookup"><span data-stu-id="ad495-219">0.175205</span></span>|  
|<span data-ttu-id="ad495-220">Patch kit</span><span class="sxs-lookup"><span data-stu-id="ad495-220">Patch kit</span></span>|<span data-ttu-id="ad495-221">2113</span><span class="sxs-lookup"><span data-stu-id="ad495-221">2113</span></span>|<span data-ttu-id="ad495-222">0.142012</span><span class="sxs-lookup"><span data-stu-id="ad495-222">0.142012</span></span>|<span data-ttu-id="ad495-223">0.132389</span><span class="sxs-lookup"><span data-stu-id="ad495-223">0.132389</span></span>|  
  
 [<span data-ttu-id="ad495-224">回到頁首</span><span class="sxs-lookup"><span data-stu-id="ad495-224">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-7-determining-confidence-for-related-itemsets"></a><a name="bkmk_Query7"></a> <span data-ttu-id="ad495-225">範例查詢 7：判斷相關項目集的信心</span><span class="sxs-lookup"><span data-stu-id="ad495-225">Sample Query 7: Determining Confidence for Related Itemsets</span></span>  
 <span data-ttu-id="ad495-226">雖然規則對產生建議很有用，但如果要較深入地分析資料集中的模式，則項目集比較有趣。</span><span class="sxs-lookup"><span data-stu-id="ad495-226">Whereas rules are useful for generating recommendations, itemsets are more interesting for deeper analysis of the patterns in the data set.</span></span> <span data-ttu-id="ad495-227">例如，如果您對於前述範例查詢所傳回的建議不滿意，則可以檢查其他包含產品 A 的項目集，以進一步了解產品 A 是否為客戶會搭配所有產品類型而購買的配件，或者 A 與特定產品的購買有強烈的關聯性。</span><span class="sxs-lookup"><span data-stu-id="ad495-227">For example, if you were not satisfied with the recommendation that are returned by the previous sample query, you could examine other itemsets that contain Product A, to can get a better idea of whether Product A is an accessory that people tend to buy with all kinds of products, or whether A is strongly correlated with purchases of particular products.</span></span> <span data-ttu-id="ad495-228">探索這些關聯性最簡單的方式，就是在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 關聯檢視器中篩選項目集；不過您可以藉由查詢來擷取相同的資訊。</span><span class="sxs-lookup"><span data-stu-id="ad495-228">The easiest way to explore these relationships is by filtering the itemsets in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Viewer; however, you can retrieve the same information with a query.</span></span>  
  
 <span data-ttu-id="ad495-229">下列範例查詢會傳回所有包含 Water Bottle 項目的項目集 (包含單一項目 Water Bottle)。</span><span class="sxs-lookup"><span data-stu-id="ad495-229">The following sample query returns all itemsets that include the Water Bottle item, including the single item Water bottle.</span></span>  
  
```  
SELECT TOP 100 FROM   
(  
SELECT FLATTENED NODE_CAPTION, NODE_SUPPORT,   
(SELECT ATTRIBUTE_NAME from NODE_DISTRIBUTION  
WHERE ATTRIBUTE_NAME = 'v Assoc Seq Line Items(Water Bottle)') as D  
FROM Association.CONTENT  
WHERE NODE_TYPE = 7  
) AS Items  
WHERE [D.ATTRIBUTE_NAME] <> NULL  
ORDER BY NODE_SUPPORT DESC  
```  
  
 <span data-ttu-id="ad495-230">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="ad495-230">Example results:</span></span>  
  
|<span data-ttu-id="ad495-231">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="ad495-231">NODE_CAPTION</span></span>|<span data-ttu-id="ad495-232">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="ad495-232">NODE_SUPPORT</span></span>|<span data-ttu-id="ad495-233">D.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="ad495-233">D.ATTRIBUTE_NAME</span></span>|  
|-------------------|-------------------|-----------------------|  
|<span data-ttu-id="ad495-234">Water Bottle = Existing</span><span class="sxs-lookup"><span data-stu-id="ad495-234">Water Bottle = Existing</span></span>|<span data-ttu-id="ad495-235">2866</span><span class="sxs-lookup"><span data-stu-id="ad495-235">2866</span></span>|<span data-ttu-id="ad495-236">v Assoc Seq Line Items(Water Bottle)</span><span class="sxs-lookup"><span data-stu-id="ad495-236">v Assoc Seq Line Items(Water Bottle)</span></span>|  
|<span data-ttu-id="ad495-237">Mountain Bottle Cage = Existing, Water Bottle = Existing</span><span class="sxs-lookup"><span data-stu-id="ad495-237">Mountain Bottle Cage = Existing, Water Bottle = Existing</span></span>|<span data-ttu-id="ad495-238">1136</span><span class="sxs-lookup"><span data-stu-id="ad495-238">1136</span></span>|<span data-ttu-id="ad495-239">v Assoc Seq Line Items(Water Bottle)</span><span class="sxs-lookup"><span data-stu-id="ad495-239">v Assoc Seq Line Items(Water Bottle)</span></span>|  
|<span data-ttu-id="ad495-240">Road Bottle Cage = Existing, Water Bottle = Existing</span><span class="sxs-lookup"><span data-stu-id="ad495-240">Road Bottle Cage = Existing, Water Bottle = Existing</span></span>|<span data-ttu-id="ad495-241">1068</span><span class="sxs-lookup"><span data-stu-id="ad495-241">1068</span></span>|<span data-ttu-id="ad495-242">v Assoc Seq Line Items(Water Bottle)</span><span class="sxs-lookup"><span data-stu-id="ad495-242">v Assoc Seq Line Items(Water Bottle)</span></span>|  
|<span data-ttu-id="ad495-243">Water Bottle = Existing, Sport-100 = Existing</span><span class="sxs-lookup"><span data-stu-id="ad495-243">Water Bottle = Existing, Sport-100 = Existing</span></span>|<span data-ttu-id="ad495-244">734</span><span class="sxs-lookup"><span data-stu-id="ad495-244">734</span></span>|<span data-ttu-id="ad495-245">v Assoc Seq Line Items(Water Bottle)</span><span class="sxs-lookup"><span data-stu-id="ad495-245">v Assoc Seq Line Items(Water Bottle)</span></span>|  
  
 <span data-ttu-id="ad495-246">這個查詢不但僅會從巢狀資料表傳回符合準則的資料列，還會從外部或案例資料表傳回所有的資料列。</span><span class="sxs-lookup"><span data-stu-id="ad495-246">This query returns both the rows from the nested table that match the criteria, and all the rows from the outside or case table.</span></span> <span data-ttu-id="ad495-247">因此，您必須加入條件來排除目標屬性名稱具有 Null 值的案例資料表資料列。</span><span class="sxs-lookup"><span data-stu-id="ad495-247">Therefore, you must add a condition that eliminates the case table rows that have a null value for the target attribute name.</span></span>  
  
 [<span data-ttu-id="ad495-248">回到頁首</span><span class="sxs-lookup"><span data-stu-id="ad495-248">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="function-list"></a><span data-ttu-id="ad495-249">函數清單</span><span class="sxs-lookup"><span data-stu-id="ad495-249">Function List</span></span>  
 <span data-ttu-id="ad495-250">所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 演算法都支援一組常用的函數。</span><span class="sxs-lookup"><span data-stu-id="ad495-250">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="ad495-251">不過， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 關聯分析演算法支援下表所列出的其他函數。</span><span class="sxs-lookup"><span data-stu-id="ad495-251">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association algorithm supports the additional functions listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad495-252">預測函數</span><span class="sxs-lookup"><span data-stu-id="ad495-252">Prediction Function</span></span>|<span data-ttu-id="ad495-253">使用量</span><span class="sxs-lookup"><span data-stu-id="ad495-253">Usage</span></span>|  
|[<span data-ttu-id="ad495-254">IsDescendant &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="ad495-254">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="ad495-255">確定某個節點是否為類神經網路圖中另一個節點的子系。</span><span class="sxs-lookup"><span data-stu-id="ad495-255">Determines whether one node is a child of another node in the neural network graph.</span></span>|  
|[<span data-ttu-id="ad495-256">IsInNode &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="ad495-256">IsInNode &#40;DMX&#41;</span></span>](/sql/dmx/isinnode-dmx)|<span data-ttu-id="ad495-257">指示指定的節點是否包含目前案例。</span><span class="sxs-lookup"><span data-stu-id="ad495-257">Indicates whether the specified node contains the current case.</span></span>|  
|[<span data-ttu-id="ad495-258">PredictAdjustedProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="ad495-258">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="ad495-259">傳回加權機率。</span><span class="sxs-lookup"><span data-stu-id="ad495-259">Returns the weighted probability.</span></span>|  
|[<span data-ttu-id="ad495-260">PredictAssociation &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="ad495-260">PredictAssociation &#40;DMX&#41;</span></span>](/sql/dmx/predictassociation-dmx)|<span data-ttu-id="ad495-261">預測關聯資料集的成員資格。</span><span class="sxs-lookup"><span data-stu-id="ad495-261">Predicts membership in an associative dataset.</span></span>|  
|[<span data-ttu-id="ad495-262">PredictHistogram &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="ad495-262">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="ad495-263">傳回與目前預測值相關之值的資料表。</span><span class="sxs-lookup"><span data-stu-id="ad495-263">Returns a table of values related to the current predicted value.</span></span>|  
|[<span data-ttu-id="ad495-264">PredictNodeId &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="ad495-264">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="ad495-265">傳回每個案例的 Node_ID。</span><span class="sxs-lookup"><span data-stu-id="ad495-265">Returns the Node_ID for each case.</span></span>|  
|[<span data-ttu-id="ad495-266">PredictProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="ad495-266">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="ad495-267">傳回預測值的機率。</span><span class="sxs-lookup"><span data-stu-id="ad495-267">Returns probability for the predicted value.</span></span>|  
|[<span data-ttu-id="ad495-268">PredictSupport &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="ad495-268">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="ad495-269">傳回指定狀態的支援值。</span><span class="sxs-lookup"><span data-stu-id="ad495-269">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="ad495-270">PredictVariance &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="ad495-270">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="ad495-271">傳回預測值的變異數。</span><span class="sxs-lookup"><span data-stu-id="ad495-271">Returns variance for the predicted value.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad495-272">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad495-272">See Also</span></span>  
 <span data-ttu-id="ad495-273">[Microsoft 關聯分析演算法](microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="ad495-273">[Microsoft Association Algorithm](microsoft-association-algorithm.md) </span></span>  
 <span data-ttu-id="ad495-274">[Microsoft 關聯分析演算法技術參考](microsoft-association-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ad495-274">[Microsoft Association Algorithm Technical Reference](microsoft-association-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="ad495-275">關聯模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="ad495-275">Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-association-models-analysis-services-data-mining.md)  
  
  
