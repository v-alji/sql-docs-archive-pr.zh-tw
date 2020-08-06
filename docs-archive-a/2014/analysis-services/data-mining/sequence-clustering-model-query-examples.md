---
title: 時序群集模型查詢範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- sequence clustering algorithms [Analysis Services]
- content queries [DMX]
- sequence [Analysis Services]
ms.assetid: 64bebcdc-70ab-43fb-8d40-57672a126602
author: minewiskan
ms.author: owend
ms.openlocfilehash: d56924f27f7986861895cf4fff21fa758cc47070
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584835"
---
# <a name="sequence-clustering-model-query-examples"></a><span data-ttu-id="f34d5-102">時序叢集模型查詢範例</span><span class="sxs-lookup"><span data-stu-id="f34d5-102">Sequence Clustering Model Query Examples</span></span>
  <span data-ttu-id="f34d5-103">當您針對資料採礦模型建立查詢時，可以建立內容查詢來提供有關模型中排序之資訊的詳細資料，或是建立預測查詢來使用模型中的模式，根據所提供的新資料進行預測。</span><span class="sxs-lookup"><span data-stu-id="f34d5-103">When you create a query against a data mining model, you can create either a content query, which provides details about the information stored in the model, or you can create a prediction query, which uses the patterns in the model to make predictions based on new data that you provide.</span></span> <span data-ttu-id="f34d5-104">對於時序群集模型，內容查詢通常會提供找到之群集的其他詳細資料，或提供這些群集中的轉換。</span><span class="sxs-lookup"><span data-stu-id="f34d5-104">For a sequence clustering model, content queries typically provide additional details about the clusters that were found, or the transitions within those clusters.</span></span> <span data-ttu-id="f34d5-105">您也可以使用查詢來擷取有關模型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f34d5-105">You can also retrieve metadata about the model by using a query.</span></span>  
  
 <span data-ttu-id="f34d5-106">時序群集模型的預測查詢通常會根據轉換的時序、包含在模型中的非時序屬性，或者時序與非時序屬性的組合，做出建議。</span><span class="sxs-lookup"><span data-stu-id="f34d5-106">Prediction queries on a sequence clustering model typically make recommendations based either on the sequences and transitions, on non-sequence attributes that were included in the model, or on a combination of sequence and non-sequence attributes.</span></span>  
  
 <span data-ttu-id="f34d5-107">本節說明如何針對以 Microsoft 時序群集演算法為基礎的模型來建立查詢。</span><span class="sxs-lookup"><span data-stu-id="f34d5-107">This section explains how to create queries for models that are based on the Microsoft Sequence Clustering algorithm.</span></span> <span data-ttu-id="f34d5-108">如需建立查詢的一般資訊，請參閱 [資料採礦查詢](data-mining-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="f34d5-108">For general information about creating queries, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
 <span data-ttu-id="f34d5-109">**內容查詢**</span><span class="sxs-lookup"><span data-stu-id="f34d5-109">**Content Queries**</span></span>  
  
 [<span data-ttu-id="f34d5-110">使用資料採礦結構描述資料列集傳回模型參數</span><span class="sxs-lookup"><span data-stu-id="f34d5-110">Using the Data Mining Schema Rowset to return model parameters</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="f34d5-111">取得狀態之時序的清單</span><span class="sxs-lookup"><span data-stu-id="f34d5-111">Getting a list of sequences for a state</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="f34d5-112">使用系統預存程式</span><span class="sxs-lookup"><span data-stu-id="f34d5-112">Using system stored procedures</span></span>](#bkmk_Query3)  
  
 <span data-ttu-id="f34d5-113">**預測查詢**</span><span class="sxs-lookup"><span data-stu-id="f34d5-113">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="f34d5-114">預測後續的一個或多個狀態</span><span class="sxs-lookup"><span data-stu-id="f34d5-114">Predict next state or states</span></span>](#bkmk_Query4)  
  
##  <a name="finding-information-about-the-sequence-clustering-model"></a><a name="bkmk_ContentQueries"></a><span data-ttu-id="f34d5-115">尋找時序群集模型的相關資訊</span><span class="sxs-lookup"><span data-stu-id="f34d5-115">Finding Information about the Sequence Clustering Model</span></span>  
 <span data-ttu-id="f34d5-116">若要在採礦模型的內容上建立有意義的查詢，您必須了解模型內容的結構，以及哪一種節點類型會儲存那一種資訊。</span><span class="sxs-lookup"><span data-stu-id="f34d5-116">To create meaningful queries on the content of a mining model, you must understand the structure of the model content, and which node types store what kind of information.</span></span> <span data-ttu-id="f34d5-117">如需詳細資訊，請參閱 [時序叢集模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-sequence-clustering-models.md)。</span><span class="sxs-lookup"><span data-stu-id="f34d5-117">For more information, see [Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-sequence-clustering-models.md).</span></span>  
  
###  <a name="sample-query-1-using-the-data-mining-schema-rowset-to-return-model-parameters"></a><a name="bkmk_Query1"></a><span data-ttu-id="f34d5-118">範例查詢1：使用資料採礦架構資料列集傳回模型參數</span><span class="sxs-lookup"><span data-stu-id="f34d5-118">Sample Query 1: Using the Data Mining Schema Rowset to Return Model Parameters</span></span>  
 <span data-ttu-id="f34d5-119">您可以藉由查詢資料採礦結構描述資料列集來尋找有關模型的各種資訊，包括基本中繼資料、此模型建立的日期和時間、上次處理此模型的日期和時間、此模型所依據之採礦結構的名稱，以及當做可預測屬性使用的資料行。</span><span class="sxs-lookup"><span data-stu-id="f34d5-119">By querying the data mining schema rowset, you can find various kinds of information about the model, including basic metadata, the date and time that the model was created and last processed, the name of the mining structure that the model is based on, and the column used as the predictable attribute.</span></span>  
  
 <span data-ttu-id="f34d5-120">下列查詢會傳回用於建立和定型模型 `[Sequence Clustering]`的參數。</span><span class="sxs-lookup"><span data-stu-id="f34d5-120">The following query returns the parameters that were used to build and train the model, `[Sequence Clustering]`.</span></span> <span data-ttu-id="f34d5-121">您可以在＜ [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)＞的第 5 課中建立此模型。</span><span class="sxs-lookup"><span data-stu-id="f34d5-121">You can create this model in Lesson 5 of the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span>  
  
```  
SELECT MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Sequence Clustering'  
```  
  
 <span data-ttu-id="f34d5-122">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="f34d5-122">Example results:</span></span>  
  
|<span data-ttu-id="f34d5-123">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f34d5-123">MINING_PARAMETERS</span></span>|  
|------------------------|  
|<span data-ttu-id="f34d5-124">CLUSTER_COUNT=15,MINIMUM_SUPPORT=10,MAXIMUM_STATES=100,MAXIMUM_SEQUENCE_STATES=64</span><span class="sxs-lookup"><span data-stu-id="f34d5-124">CLUSTER_COUNT=15,MINIMUM_SUPPORT=10,MAXIMUM_STATES=100,MAXIMUM_SEQUENCE_STATES=64</span></span>|  
  
 <span data-ttu-id="f34d5-125">請注意，此模型是使用 CLUSTER_COUNT 的預設值 10 來建立的。</span><span class="sxs-lookup"><span data-stu-id="f34d5-125">Note that this model was built by using the default value of 10 for CLUSTER_COUNT.</span></span> <span data-ttu-id="f34d5-126">當您針對 CLUSTER_COUNT 指定非零的群集數目時，此演算法會將此數目視為要尋找之約略群集數目的提示。</span><span class="sxs-lookup"><span data-stu-id="f34d5-126">When you specify a non-zero number of clusters for CLUSTER_COUNT, the algorithm treats this number as a hint for the approximate number of clusters to find.</span></span> <span data-ttu-id="f34d5-127">不過，在分析時，此演算法可能會找到更多或更少的群集。</span><span class="sxs-lookup"><span data-stu-id="f34d5-127">However, in the process of analysis, the algorithm may find more or fewer clusters.</span></span> <span data-ttu-id="f34d5-128">在此情況下，此演算法會發現 15 個群集最適合定型資料。</span><span class="sxs-lookup"><span data-stu-id="f34d5-128">In this case, the algorithm found that 15 clusters best fit the training data.</span></span> <span data-ttu-id="f34d5-129">因此，已完成模型的參數值清單會報告此演算法決定的群集計數，而不是建立模型時傳入的值。</span><span class="sxs-lookup"><span data-stu-id="f34d5-129">Therefore, the list of parameter values for the completed model reports the count of clusters as determined by the algorithm, not the value passed in when creating the model.</span></span>  
  
 <span data-ttu-id="f34d5-130">此行為與讓演算法決定最佳的群集數目有什麼不同？</span><span class="sxs-lookup"><span data-stu-id="f34d5-130">How does this behavior differ from letting the algorithm determine the best number of clusters?</span></span> <span data-ttu-id="f34d5-131">您可以做一個試驗，建立另一個使用這個相同資料的群集模型，但將 CLUSTER_COUNT 設定為 0。</span><span class="sxs-lookup"><span data-stu-id="f34d5-131">As an experiment, you can create another clustering model that uses this same data, but set CLUSTER_COUNT to 0.</span></span> <span data-ttu-id="f34d5-132">此時，演算法會偵測到 32 個群集。</span><span class="sxs-lookup"><span data-stu-id="f34d5-132">When you do this, the algorithm detects 32 clusters.</span></span> <span data-ttu-id="f34d5-133">因此，您可以透過使用 CLUSTER_COUNT 的預設值 10 來限制結果的數目。</span><span class="sxs-lookup"><span data-stu-id="f34d5-133">Therefore, by using the default value of 10 for CLUSTER_COUNT, you constrain the number of results.</span></span>  
  
 <span data-ttu-id="f34d5-134">預設使用 10 這個值，因為減少群集數目會讓多數人更容易瀏覽與了解資料中的群組。</span><span class="sxs-lookup"><span data-stu-id="f34d5-134">The value of 10 is used by default because reducing the number of clusters makes it easier for most people to browse and understand groupings in the data.</span></span> <span data-ttu-id="f34d5-135">不過，每個模型和資料集都不同。</span><span class="sxs-lookup"><span data-stu-id="f34d5-135">However, each model and set of data is different.</span></span> <span data-ttu-id="f34d5-136">您可能想要試驗不同的群集數目以查看哪個參數值會產生最精確的模型。</span><span class="sxs-lookup"><span data-stu-id="f34d5-136">You may wish to experiment with different numbers of clusters to see which parameter value yields the most accurate model.</span></span>  
  
###  <a name="sample-query-2-getting-a-list-of-sequences-for-a-state"></a><a name="bkmk_Query2"></a><span data-ttu-id="f34d5-137">範例查詢2：取得狀態的序列清單</span><span class="sxs-lookup"><span data-stu-id="f34d5-137">Sample Query 2: Getting a List of Sequences for a State</span></span>  
 <span data-ttu-id="f34d5-138">採礦模型內容會將定型資料中找到的時序儲存為結合其他所有相關狀態之清單的第一個狀態。</span><span class="sxs-lookup"><span data-stu-id="f34d5-138">The mining model content stores the sequences that are found in the training data as a first state coupled with a list of all related second states.</span></span> <span data-ttu-id="f34d5-139">第一個狀態會當做時序的標籤使用，而後續的相關狀態則稱為轉換。</span><span class="sxs-lookup"><span data-stu-id="f34d5-139">The first state is used as the label for the sequence, and the related second states are called transitions.</span></span>  
  
 <span data-ttu-id="f34d5-140">例如，下列查詢會在時序分組到群集之前，傳回模型中第一個狀態的完整清單。</span><span class="sxs-lookup"><span data-stu-id="f34d5-140">For example, the following query returns the complete list of first states in the model, before the sequences are grouped into clusters.</span></span>  <span data-ttu-id="f34d5-141">您可以傳回模型根節點當做父系 (PARENT_UNIQUE_NAME = 0) 之時序 (NODE_TYPE = 13) 的清單，藉以取得此清單。</span><span class="sxs-lookup"><span data-stu-id="f34d5-141">You can get this list by returning the list of sequences (NODE_TYPE = 13) that have the model root node as parent (PARENT_UNIQUE_NAME = 0).</span></span> <span data-ttu-id="f34d5-142">FLATTENED 關鍵字會讓結果更容易讀取。</span><span class="sxs-lookup"><span data-stu-id="f34d5-142">The FLATTENED keyword makes the results easier to read.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f34d5-143">資料行 PARENT_UNIQUE_NAME、[支援] 與 [機率] 的名稱必須括在括號內，以便與同名的保留關鍵字區別。</span><span class="sxs-lookup"><span data-stu-id="f34d5-143">The name of the columns, PARENT_UNIQUE_NAME, Support, and Probability must be enclosed in brackets to distinguish them from the reserved keywords of the same name.</span></span>  
  
```  
SELECT FLATTENED NODE_UNIQUE_NAME,  
(SELECT ATTRIBUTE_VALUE AS [Product 1],  
[Support] AS [Sequence Support],   
[Probability] AS [Sequence Probability]  
FROM NODE_DISTRIBUTION) AS t  
FROM [Sequence Clustering].CONTENT  
WHERE NODE_TYPE = 13  
AND [PARENT_UNIQUE_NAME] = 0  
```  
  
 <span data-ttu-id="f34d5-144">部分結果：</span><span class="sxs-lookup"><span data-stu-id="f34d5-144">Partial results:</span></span>  
  
|<span data-ttu-id="f34d5-145">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="f34d5-145">NODE_UNIQUE_NAME</span></span>|<span data-ttu-id="f34d5-146">產品 1</span><span class="sxs-lookup"><span data-stu-id="f34d5-146">Product 1</span></span>|<span data-ttu-id="f34d5-147">時序支援</span><span class="sxs-lookup"><span data-stu-id="f34d5-147">Sequence Support</span></span>|<span data-ttu-id="f34d5-148">時序機率</span><span class="sxs-lookup"><span data-stu-id="f34d5-148">Sequence Probability</span></span>|  
|------------------------|---------------|----------------------|--------------------------|  
|<span data-ttu-id="f34d5-149">1081327</span><span class="sxs-lookup"><span data-stu-id="f34d5-149">1081327</span></span>|<span data-ttu-id="f34d5-150">Missing</span><span class="sxs-lookup"><span data-stu-id="f34d5-150">Missing</span></span>|<span data-ttu-id="f34d5-151">0</span><span class="sxs-lookup"><span data-stu-id="f34d5-151">0</span></span>|#######|  
|<span data-ttu-id="f34d5-152">1081327</span><span class="sxs-lookup"><span data-stu-id="f34d5-152">1081327</span></span>|<span data-ttu-id="f34d5-153">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="f34d5-153">All-Purpose Bike Stand</span></span>|<span data-ttu-id="f34d5-154">17</span><span class="sxs-lookup"><span data-stu-id="f34d5-154">17</span></span>|<span data-ttu-id="f34d5-155">0.00111</span><span class="sxs-lookup"><span data-stu-id="f34d5-155">0.00111</span></span>|  
|<span data-ttu-id="f34d5-156">1081327</span><span class="sxs-lookup"><span data-stu-id="f34d5-156">1081327</span></span>|<span data-ttu-id="f34d5-157">Bike Wash</span><span class="sxs-lookup"><span data-stu-id="f34d5-157">Bike Wash</span></span>|<span data-ttu-id="f34d5-158">64</span><span class="sxs-lookup"><span data-stu-id="f34d5-158">64</span></span>|<span data-ttu-id="f34d5-159">0.00418</span><span class="sxs-lookup"><span data-stu-id="f34d5-159">0.00418</span></span>|  
|<span data-ttu-id="f34d5-160">1081327</span><span class="sxs-lookup"><span data-stu-id="f34d5-160">1081327</span></span>|<span data-ttu-id="f34d5-161">(資料列 4-36 省略)</span><span class="sxs-lookup"><span data-stu-id="f34d5-161">(rows 4-36 omitted)</span></span>|||  
|<span data-ttu-id="f34d5-162">1081327</span><span class="sxs-lookup"><span data-stu-id="f34d5-162">1081327</span></span>|<span data-ttu-id="f34d5-163">Women's Mountain Shorts</span><span class="sxs-lookup"><span data-stu-id="f34d5-163">Women's Mountain Shorts</span></span>|<span data-ttu-id="f34d5-164">506</span><span class="sxs-lookup"><span data-stu-id="f34d5-164">506</span></span>|<span data-ttu-id="f34d5-165">0.03307</span><span class="sxs-lookup"><span data-stu-id="f34d5-165">0.03307</span></span>|  
  
 <span data-ttu-id="f34d5-166">模型中的時序清單永遠依字母的遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="f34d5-166">The list of sequences in the model is always sorted alphabetically in ascending order.</span></span> <span data-ttu-id="f34d5-167">時序的排序相當重要，因為您可以查看時序的排序數字尋找相關的轉換。</span><span class="sxs-lookup"><span data-stu-id="f34d5-167">The ordering of the sequences is important because you can find the related transitions by looking at the order number of the sequence.</span></span> <span data-ttu-id="f34d5-168">`Missing` 值一定是轉換 0。</span><span class="sxs-lookup"><span data-stu-id="f34d5-168">The `Missing` value is always transition 0.</span></span>  
  
 <span data-ttu-id="f34d5-169">例如，在先前的結果中，產品 "Women's Mountain Shorts" 在模型中是時序編號 37。</span><span class="sxs-lookup"><span data-stu-id="f34d5-169">For example, in the previous results, the product "Women's Mountain Shorts" is the sequence number 37 in the model.</span></span> <span data-ttu-id="f34d5-170">您可以使用該資訊檢視在 "Women's Mountain Shorts" 後曾經購買的所有產品。</span><span class="sxs-lookup"><span data-stu-id="f34d5-170">You can use that information to view all of the products that were ever purchased after "Women's Mountain Shorts."</span></span>  
  
 <span data-ttu-id="f34d5-171">若要這樣做，首先，您要參考先前查詢中，針對 NODE_UNIQUE_NAME 傳回的值，藉以取得包含模型所有時序之節點的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f34d5-171">To do this, first, you reference the value returned for NODE_UNIQUE_NAME in the previous query, to get the ID of the node that contains all sequences for the model.</span></span> <span data-ttu-id="f34d5-172">然後您要將此值傳遞到查詢中，當做父節點的識別碼，藉以僅取得此節點中所包含的轉換，而此節點中恰好就包含模型之所有時序的清單。</span><span class="sxs-lookup"><span data-stu-id="f34d5-172">You pass this value to the query as the ID of the parent node, to get only the transitions included in this node, which happens to contain a list of al sequences for the model.</span></span> <span data-ttu-id="f34d5-173">不過，如果您要查看特定群集之轉換的清單，您可以傳入叢集節點的識別碼，然後僅查看與該群集關聯的時序。</span><span class="sxs-lookup"><span data-stu-id="f34d5-173">However, if you wanted to see the list of transitions for a specific cluster, you could pass in the ID of the cluster node, and see only the sequences associated with that cluster.</span></span>  
  
```  
SELECT NODE_UNIQUE_NAME  
FROM [Sequence Clustering].CONTENT  
WHERE NODE_DESCRIPTION = 'Transition row for sequence state 37'  
AND [PARENT_UNIQUE_NAME] = '1081327'  
```  
  
 <span data-ttu-id="f34d5-174">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="f34d5-174">Example results:</span></span>  
  
|<span data-ttu-id="f34d5-175">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="f34d5-175">NODE_UNIQUE_NAME</span></span>|  
|------------------------|  
|<span data-ttu-id="f34d5-176">1081365</span><span class="sxs-lookup"><span data-stu-id="f34d5-176">1081365</span></span>|  
  
 <span data-ttu-id="f34d5-177">以此識別碼表示的節點包含 "Women's Mountain Shorts" 產品後之時序的清單，以及支援與機率的值。</span><span class="sxs-lookup"><span data-stu-id="f34d5-177">The node represented by this ID contains a list of the sequences that follow the "Women's Mountain Shorts" product, together with the support and probability values.</span></span>  
  
```  
SELECT FLATTENED  
(SELECT ATTRIBUTE_VALUE AS Product2,  
[Support] AS [P2 Support],  
[Probability] AS [P2 Probability]  
FROM NODE_DISTRIBUTION) AS t  
FROM [Sequence Clustering].CONTENT  
WHERE NODE_UNIQUE_NAME = '1081365'  
```  
  
 <span data-ttu-id="f34d5-178">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="f34d5-178">Example results:</span></span>  
  
|<span data-ttu-id="f34d5-179">t.Product2</span><span class="sxs-lookup"><span data-stu-id="f34d5-179">t.Product2</span></span>|<span data-ttu-id="f34d5-180">t.P2 Support</span><span class="sxs-lookup"><span data-stu-id="f34d5-180">t.P2 Support</span></span>|<span data-ttu-id="f34d5-181">t.P2 Probability</span><span class="sxs-lookup"><span data-stu-id="f34d5-181">t.P2 Probability</span></span>|  
|----------------|------------------|----------------------|  
|<span data-ttu-id="f34d5-182">Missing</span><span class="sxs-lookup"><span data-stu-id="f34d5-182">Missing</span></span>|<span data-ttu-id="f34d5-183">230.7419</span><span class="sxs-lookup"><span data-stu-id="f34d5-183">230.7419</span></span>|<span data-ttu-id="f34d5-184">0.456012</span><span class="sxs-lookup"><span data-stu-id="f34d5-184">0.456012</span></span>|  
|<span data-ttu-id="f34d5-185">Classic Vest</span><span class="sxs-lookup"><span data-stu-id="f34d5-185">Classic Vest</span></span>|<span data-ttu-id="f34d5-186">8.16129</span><span class="sxs-lookup"><span data-stu-id="f34d5-186">8.16129</span></span>|<span data-ttu-id="f34d5-187">0.016129</span><span class="sxs-lookup"><span data-stu-id="f34d5-187">0.016129</span></span>|  
|<span data-ttu-id="f34d5-188">Cycling Cap</span><span class="sxs-lookup"><span data-stu-id="f34d5-188">Cycling Cap</span></span>|<span data-ttu-id="f34d5-189">60.83871</span><span class="sxs-lookup"><span data-stu-id="f34d5-189">60.83871</span></span>|<span data-ttu-id="f34d5-190">0.120235</span><span class="sxs-lookup"><span data-stu-id="f34d5-190">0.120235</span></span>|  
|<span data-ttu-id="f34d5-191">Half-Finger Gloves</span><span class="sxs-lookup"><span data-stu-id="f34d5-191">Half-Finger Gloves</span></span>|<span data-ttu-id="f34d5-192">30.41935</span><span class="sxs-lookup"><span data-stu-id="f34d5-192">30.41935</span></span>|<span data-ttu-id="f34d5-193">0.060117</span><span class="sxs-lookup"><span data-stu-id="f34d5-193">0.060117</span></span>|  
|<span data-ttu-id="f34d5-194">Long-Sleeve Logo Jersey</span><span class="sxs-lookup"><span data-stu-id="f34d5-194">Long-Sleeve Logo Jersey</span></span>|<span data-ttu-id="f34d5-195">86.80645</span><span class="sxs-lookup"><span data-stu-id="f34d5-195">86.80645</span></span>|<span data-ttu-id="f34d5-196">0.171554</span><span class="sxs-lookup"><span data-stu-id="f34d5-196">0.171554</span></span>|  
|<span data-ttu-id="f34d5-197">Racing Socks</span><span class="sxs-lookup"><span data-stu-id="f34d5-197">Racing Socks</span></span>|<span data-ttu-id="f34d5-198">28.93548</span><span class="sxs-lookup"><span data-stu-id="f34d5-198">28.93548</span></span>|<span data-ttu-id="f34d5-199">0.057185</span><span class="sxs-lookup"><span data-stu-id="f34d5-199">0.057185</span></span>|  
|<span data-ttu-id="f34d5-200">Short-Sleeve Classic Jersey</span><span class="sxs-lookup"><span data-stu-id="f34d5-200">Short-Sleeve Classic Jersey</span></span>|<span data-ttu-id="f34d5-201">60.09677</span><span class="sxs-lookup"><span data-stu-id="f34d5-201">60.09677</span></span>|<span data-ttu-id="f34d5-202">0.118768</span><span class="sxs-lookup"><span data-stu-id="f34d5-202">0.118768</span></span>|  
  
 <span data-ttu-id="f34d5-203">請注意，與 Women's Mountain Shorts 相關之各種時序的支援在模型中為 506。</span><span class="sxs-lookup"><span data-stu-id="f34d5-203">Note that support for the various sequences related to Women's Mountain Shorts is 506 in the model.</span></span> <span data-ttu-id="f34d5-204">轉換的支援值最多可以增加到 506。</span><span class="sxs-lookup"><span data-stu-id="f34d5-204">The support values for the transitions also add up to 506.</span></span> <span data-ttu-id="f34d5-205">不過，這些數目並不是完整的數目，如果您希望支援只表示包含每個轉換之案例的計數，這似乎有點多。</span><span class="sxs-lookup"><span data-stu-id="f34d5-205">However, the numbers are not whole numbers, which seems a bit odd if you expect support to simply represent a count of cases that contain each transition.</span></span> <span data-ttu-id="f34d5-206">但是，因為建立群集的方法會計算部分成員資格，群集中任何轉換的機率都必須透過屬於該特定群集的機率加權。</span><span class="sxs-lookup"><span data-stu-id="f34d5-206">However, because the method for creating clusters calculates partial membership, the probability of any transition within a cluster must be weighted by its probability of belonging to that particular cluster.</span></span>  
  
 <span data-ttu-id="f34d5-207">例如，如果有四個群集，特定時序屬於群集 1 的機會可能有 40%，屬於群集 2 的機會有 30%，屬於群集 3 的機會有 20%，而屬於群集 3 的機會有 10%。</span><span class="sxs-lookup"><span data-stu-id="f34d5-207">For example, if there are four clusters, a particular sequence might have a 40% chance of belonging to cluster 1, a 30% chance of belonging to cluster 2, a 20% chance of belonging to cluster 3, and a 10% chance of belonging to cluster 4.</span></span> <span data-ttu-id="f34d5-208">在演算法決定轉換可能所屬的群集之後，會在群集中透過群集優先機率加權機率。</span><span class="sxs-lookup"><span data-stu-id="f34d5-208">After the algorithm determines the cluster that the transition is mostly likely to belong to, it weights the probabilities within the cluster by the cluster prior probability.</span></span>  
  
###  <a name="sample-query-3-using-system-stored-procedures"></a><a name="bkmk_Query3"></a><span data-ttu-id="f34d5-209">範例查詢3：使用系統預存程式</span><span class="sxs-lookup"><span data-stu-id="f34d5-209">Sample Query 3: Using System Stored Procedures</span></span>  
 <span data-ttu-id="f34d5-210">您可以從這些查詢範例中了解，儲存在模型中的資訊相當複雜，而且您可能需要建立多個查詢，才能取得所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="f34d5-210">You can see from these query samples that the information stored in the model is complex, and that you might need to create multiple queries to get the information that you need.</span></span> <span data-ttu-id="f34d5-211">不過，Microsoft 時序群集檢視器會提供一組強大的工具，可以用圖形化的方式瀏覽包含在時序群集模型中的資訊，而且您也可以使用檢視器查詢與向下鑽研模型。</span><span class="sxs-lookup"><span data-stu-id="f34d5-211">However, the Microsoft Sequence Clustering viewer provides a powerful set of tools for graphically browsing the information contained in a sequence clustering model, and you can also use the viewer to query and drill down into the model.</span></span>  
  
 <span data-ttu-id="f34d5-212">在多數的情況下，呈現在 Microsoft 時序群集檢視器中的資訊是使用 Analysis Services 系統預存程序所建立，用於查詢模型。</span><span class="sxs-lookup"><span data-stu-id="f34d5-212">In most cases, the information that is presented in the Microsoft Sequence Clustering viewer is created by using Analysis Services system stored procedures to query the model.</span></span> <span data-ttu-id="f34d5-213">您可以根據模型內容撰寫資料採礦延伸模組 (DMX) 查詢來擷取相同的資訊，但是 Analysis Services 系統預存程序會再瀏覽或測試模型時提供一個方便的捷徑。</span><span class="sxs-lookup"><span data-stu-id="f34d5-213">You can write Data Mining Extensions (DMX) queries against the model content to retrieve the same information, but the Analysis Services system stored procedures provide a convenient shortcut when for exploration or for testing models.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f34d5-214">系統預存程序用於 Microsoft 針對與 Analysis Services 伺服器互動所提供之伺服器與用戶端進行的內部處理。</span><span class="sxs-lookup"><span data-stu-id="f34d5-214">System stored procedures are used for internal processing by the server and by the clients that Microsoft provides for interacting with the Analysis Services server.</span></span> <span data-ttu-id="f34d5-215">因此，Microsoft 保留隨時進行變更的權限。</span><span class="sxs-lookup"><span data-stu-id="f34d5-215">Therefore, Microsoft reserves the right to change them at any time.</span></span> <span data-ttu-id="f34d5-216">雖然此處所述的系統預存程序是為了提供您的方便，但是我們不支援在生產環境中使用這些預存程序。</span><span class="sxs-lookup"><span data-stu-id="f34d5-216">Although they are described here for your convenience, we do not support their use in a production environment.</span></span> <span data-ttu-id="f34d5-217">為確保生產環境的穩定性與相容性，您應該一律使用 DMX 撰寫您自己的查詢。</span><span class="sxs-lookup"><span data-stu-id="f34d5-217">To ensure stability and compatibility in a production environment, you should always write your own queries by using DMX.</span></span>  
  
 <span data-ttu-id="f34d5-218">本節提供一些如何使用系統預存程序，根據時序群集模型建立查詢的範例：</span><span class="sxs-lookup"><span data-stu-id="f34d5-218">This section provides some samples of how to use the system stored procedures to create queries against a sequence clustering model:</span></span>  
  
#### <a name="cluster-profiles-and-sample-cases"></a><span data-ttu-id="f34d5-219">群集設定檔與範例案例</span><span class="sxs-lookup"><span data-stu-id="f34d5-219">Cluster Profiles and Sample Cases</span></span>  
 <span data-ttu-id="f34d5-220">[群集設定檔] 索引標籤會顯示模型中的群集清單、每個群集的大小，以及表示包含在群集中之狀態的長條圖。</span><span class="sxs-lookup"><span data-stu-id="f34d5-220">The Cluster Profiles tab shows you a list of the clusters in the model, the size of each cluster, and a histogram that indicates the states included in the cluster.</span></span> <span data-ttu-id="f34d5-221">有兩個系統預存程序可以在查詢中用於擷取類似的資訊：</span><span class="sxs-lookup"><span data-stu-id="f34d5-221">There are two system stored procedures that you can use in queries to retrieve similar information:</span></span>  
  
-   <span data-ttu-id="f34d5-222">`GetClusterProfile` 會傳回叢集的特性，以及在叢集的 NODE_DISTRIBUTION 資料表中找到的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="f34d5-222">`GetClusterProfile` returns the characteristics of the cluster, with all the information that is found in the NODE_DISTRIBUTION table for the cluster.</span></span>  
  
-   <span data-ttu-id="f34d5-223">`GetNodeGraph` 會傳回可用於建構群集之數學圖形表示的節點與邊緣 (對應到您在時序群集檢視的第一個索引標籤上所看到的節點與邊緣)。</span><span class="sxs-lookup"><span data-stu-id="f34d5-223">`GetNodeGraph` returns nodes and edges that can be used to construct a mathematical graph representation of the clusters, corresponding to what you see on the first tab of the Sequence Clustering view.</span></span> <span data-ttu-id="f34d5-224">這些節點是群集，而邊緣則代表加權或強度。</span><span class="sxs-lookup"><span data-stu-id="f34d5-224">The nodes are clusters, and the edges represent weights or strength.</span></span>  
  
 <span data-ttu-id="f34d5-225">下列範例說明如何使用系統預存程序 `GetClusterProfiles`，傳回模型中的所有群集及其個別的設定檔。</span><span class="sxs-lookup"><span data-stu-id="f34d5-225">The following example illustrates how to use the system stored procedure, `GetClusterProfiles`, to return all of the clusters in the model, with their respective profiles.</span></span> <span data-ttu-id="f34d5-226">這個預存程序會執行一連串的 DMX 陳述式，以傳回模型中的一組完整設定檔。</span><span class="sxs-lookup"><span data-stu-id="f34d5-226">This stored procedure executes a series of DMX statements that return the complete set of profiles in the model.</span></span> <span data-ttu-id="f34d5-227">不過，若要使用此預存程序，您必須知道此模型的位址。</span><span class="sxs-lookup"><span data-stu-id="f34d5-227">However, to use this stored procedure you must know the address of the model.</span></span>  
  
 `CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterProfiles('Sequence Clustering', 2147483647, 0)`  
  
 <span data-ttu-id="f34d5-228">下列範例說明如何使用系統預存程序 `GetNodeGraph`，並指定群集識別碼 (通常與群集名稱中的數字相同) 來擷取特定群集 (群集 12) 的設定檔。</span><span class="sxs-lookup"><span data-stu-id="f34d5-228">The following example illustrates how to retrieve the profile for a specific cluster, Cluster 12, by using the system stored procedure `GetNodeGraph`, and specifying the cluster ID, which is usually the same as the number in the cluster name.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetNodeGraph('Sequence Clustering','12',0)  
```  
  
 <span data-ttu-id="f34d5-229">如果您省略群集識別碼，如下列查詢所示， `GetNodeGraph` 則會傳回所有群集設定檔已排序的扁平化清單：</span><span class="sxs-lookup"><span data-stu-id="f34d5-229">If you omit the cluster ID, as shown in the following query, `GetNodeGraph` returns an ordered, flattened list of all cluster profiles:</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetNodeGraph('Sequence Clustering','',0)  
```  
  
 <span data-ttu-id="f34d5-230">**[群集設定檔]** 索引標籤也會顯示模型範例案例的長條圖。</span><span class="sxs-lookup"><span data-stu-id="f34d5-230">The **Cluster Profile** tab also displays a histogram of model sample cases.</span></span> <span data-ttu-id="f34d5-231">這些範例案例代表模型的理想化案例。</span><span class="sxs-lookup"><span data-stu-id="f34d5-231">These sample cases represent the idealized cases for the model.</span></span> <span data-ttu-id="f34d5-232">這些案例在模型中的儲存方式與定型資料的儲存方式不同，您必須使用特殊的語法才能擷取模型的範例案例。</span><span class="sxs-lookup"><span data-stu-id="f34d5-232">These cases are not stored in the model the same way that the training data is; you must use a special syntax to retrieve the sample cases for the model.</span></span>  
  
```  
SELECT * FROM [Sequence Clustering].SAMPLE_CASES WHERE IsInNode('12')  
```  
  
 <span data-ttu-id="f34d5-233">如需詳細資訊，請參閱 [SELECT FROM &#60;model&#62;.SAMPLE_CASES &#40;DMX&#41;](/sql/dmx/select-from-model-dmx)。</span><span class="sxs-lookup"><span data-stu-id="f34d5-233">For more information, see [SELECT FROM &#60;model&#62;.SAMPLE_CASES &#40;DMX&#41;](/sql/dmx/select-from-model-dmx).</span></span>  
  
#### <a name="cluster-characteristics-and-cluster-discrimination"></a><span data-ttu-id="f34d5-234">群集特性與群集辨識</span><span class="sxs-lookup"><span data-stu-id="f34d5-234">Cluster Characteristics and Cluster Discrimination</span></span>  
 <span data-ttu-id="f34d5-235">**[群集特性]** 索引標籤會摘要每個群集的主要屬性，並以機率排序。</span><span class="sxs-lookup"><span data-stu-id="f34d5-235">The **Cluster Characteristics** tab summarizes the main attributes of each cluster, ranked by probability.</span></span> <span data-ttu-id="f34d5-236">您可以找出有多少個案例屬於某個群集，以及群集中的案例分配狀況。每個特性都有特定的支援。</span><span class="sxs-lookup"><span data-stu-id="f34d5-236">You can find out how many cases belong to a cluster, and what the distribution of cases is like in the cluster: Each characteristic has certain support.</span></span> <span data-ttu-id="f34d5-237">若要查看特定群集的特性，您必須知道該群集的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f34d5-237">To see the characteristics of a particular cluster, you must know the ID of the cluster.</span></span>  
  
 <span data-ttu-id="f34d5-238">下列範例使用系統預存程序 `GetClusterCharacteristics`，傳回機率分數超過 0.0005 指定臨界值之群集 12 的所有特性。</span><span class="sxs-lookup"><span data-stu-id="f34d5-238">The following examples uses the system stored procedure, `GetClusterCharacteristics`, to return all the characteristics of Cluster 12 that have a probability score over the specified threshold of 0.0005.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterCharacteristics('Sequence Clustering','12',0.0005)  
```  
  
 <span data-ttu-id="f34d5-239">若要傳回所有群集的特性，您可以將群集識別碼留空。</span><span class="sxs-lookup"><span data-stu-id="f34d5-239">To return the characteristics of all clusters, you can leave the cluster ID empty.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterCharacteristics('Sequence Clustering','',0.0005)  
```  
  
 <span data-ttu-id="f34d5-240">下列範例會呼叫系統預存程序 `GetClusterDiscrimination` 來比較群集 1 與群集 12 的特性。</span><span class="sxs-lookup"><span data-stu-id="f34d5-240">The following example calls the system stored procedure `GetClusterDiscrimination` to compare the characteristics of Cluster 1 and Cluster 12.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterDiscrimination('Sequence Clustering','1','12',0.0005,true)  
```  
  
 <span data-ttu-id="f34d5-241">如果您要使用 DMX 撰寫自己的查詢來比較兩個群集，或比較某個群集及其補充，您必須先擷取一組特性，再擷取您感興趣之特定群集的特性，然後比較這兩組特性。</span><span class="sxs-lookup"><span data-stu-id="f34d5-241">If you want to write your own query in DMX to compare two clusters, or compare a cluster with its complement, you must first retrieve one set of characteristics, and then retrieve the characteristics for the specific cluster that you are interested in, and compare the two sets.</span></span> <span data-ttu-id="f34d5-242">此案例較為複雜，而且通常需要進行某些用戶端處理。</span><span class="sxs-lookup"><span data-stu-id="f34d5-242">This scenario is more complicated and typically requires some client processing.</span></span>  
  
#### <a name="states-and-transitions"></a><span data-ttu-id="f34d5-243">狀態與轉換</span><span class="sxs-lookup"><span data-stu-id="f34d5-243">States and Transitions</span></span>  
 <span data-ttu-id="f34d5-244">Microsoft 時序群集的 **[狀態轉換]** 索引標籤會在後端執行複雜的查詢，藉以擷取並比較不同群集的統計資料。</span><span class="sxs-lookup"><span data-stu-id="f34d5-244">The **State Transitions** tab of the Microsoft Sequence Clustering performs complicated queries on the back end to retrieve and compare the statistics for different clusters.</span></span> <span data-ttu-id="f34d5-245">若要重新產生這些結果，需要更複雜的查詢並進行某些用戶端處理。</span><span class="sxs-lookup"><span data-stu-id="f34d5-245">To reproduce these results requires a more complex query and some client processing.</span></span>  
  
 <span data-ttu-id="f34d5-246">不過，您可以使用＜ [內容查詢](#bkmk_ContentQueries)＞一節的範例 2 中所述的 DMX 查詢，擷取時序或個別轉換的機率和狀態。</span><span class="sxs-lookup"><span data-stu-id="f34d5-246">However, you can use the DMX queries described in Example 2 of the section, [Content Queries](#bkmk_ContentQueries), to retrieve probabilities and states for sequences or for individual transitions.</span></span>  
  
## <a name="using-the-model-to-make-predictions"></a><span data-ttu-id="f34d5-247">使用模型進行預測</span><span class="sxs-lookup"><span data-stu-id="f34d5-247">Using the Model to Make Predictions</span></span>  
 <span data-ttu-id="f34d5-248">時序群集模型的預測查詢可以使用多個搭配其他群集模型使用的預測函數。</span><span class="sxs-lookup"><span data-stu-id="f34d5-248">Prediction queries on a sequence clustering model can use many of the prediction functions that are used with other clustering models.</span></span> <span data-ttu-id="f34d5-249">此外，您可以使用特殊的預測函數 [PredictSequence &#40;DMX&#41;](/sql/dmx/predictsequence-dmx)進行建議或預測後續狀態。</span><span class="sxs-lookup"><span data-stu-id="f34d5-249">In addition, you can use the special prediction function, [PredictSequence &#40;DMX&#41;](/sql/dmx/predictsequence-dmx), to make recommendations or to predict next states.</span></span>  
  
###  <a name="sample-query-4-predict-next-state-or-states"></a><a name="bkmk_Query4"></a><span data-ttu-id="f34d5-250">範例查詢4：預測下一個狀態或狀態</span><span class="sxs-lookup"><span data-stu-id="f34d5-250">Sample Query 4: Predict Next State or States</span></span>  
 <span data-ttu-id="f34d5-251">您可以使用 [PredictSequence &#40;DMX&#41;](/sql/dmx/predictsequence-dmx) 函數來預測給定值下一個最可能的狀態。</span><span class="sxs-lookup"><span data-stu-id="f34d5-251">You can use the [PredictSequence &#40;DMX&#41;](/sql/dmx/predictsequence-dmx) function to predict the next most likely state, given a value.</span></span> <span data-ttu-id="f34d5-252">您也可以預測多個後續狀態：例如，您可以傳回客戶可能購買的前三個產品的清單來顯示建議清單。</span><span class="sxs-lookup"><span data-stu-id="f34d5-252">You can also predict multiple next states: for example, you can return a list of the top three products that a customer is likely to purchase, to present a list of recommendations.</span></span>  
  
 <span data-ttu-id="f34d5-253">下列範例查詢是單一預測查詢，可傳回前五個預測及其機率。</span><span class="sxs-lookup"><span data-stu-id="f34d5-253">The following sample query is a singleton prediction query that returns the top five predictions, together with their probability.</span></span> <span data-ttu-id="f34d5-254">由於模型中包含巢狀資料表，因此您在進行預測時，必須使用巢狀資料表 `[v Assoc Seq Line Items]`做為資料行參考。</span><span class="sxs-lookup"><span data-stu-id="f34d5-254">Because the model includes a nested table, you must use the nested table, `[v Assoc Seq Line Items]`, as the column reference when making predictions.</span></span> <span data-ttu-id="f34d5-255">同時，當您提供值做為輸入時，您必須同時加入案例資料表與巢狀資料表資料行，如巢狀 SELECT 陳述式所示。</span><span class="sxs-lookup"><span data-stu-id="f34d5-255">Also, when you supply values as input, you must join both the case table and the nested table columns, as shown by the nested SELECT statements.</span></span>  
  
```  
SELECT FLATTENED PredictSequence([v Assoc Seq Line Items], 7)  
FROM [Sequence Clustering]  
NATURAL PREDICTION JOIN  
(SELECT  (SELECT 1 as [Line Number],  
   'All-Purpose Bike Stand' as [Model]) AS [v Assoc Seq Line Items])   
AS t  
```  
  
 <span data-ttu-id="f34d5-256">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="f34d5-256">Example results:</span></span>  
  
|<span data-ttu-id="f34d5-257">Expression.$Sequence</span><span class="sxs-lookup"><span data-stu-id="f34d5-257">Expression.$Sequence</span></span>|<span data-ttu-id="f34d5-258">Expression.Line Number</span><span class="sxs-lookup"><span data-stu-id="f34d5-258">Expression.Line Number</span></span>|<span data-ttu-id="f34d5-259">Expression.Model</span><span class="sxs-lookup"><span data-stu-id="f34d5-259">Expression.Model</span></span>|  
|--------------------------|----------------------------|----------------------|  
|<span data-ttu-id="f34d5-260">1</span><span class="sxs-lookup"><span data-stu-id="f34d5-260">1</span></span>||<span data-ttu-id="f34d5-261">Cycling Cap</span><span class="sxs-lookup"><span data-stu-id="f34d5-261">Cycling Cap</span></span>|  
|<span data-ttu-id="f34d5-262">2</span><span class="sxs-lookup"><span data-stu-id="f34d5-262">2</span></span>||<span data-ttu-id="f34d5-263">Cycling Cap</span><span class="sxs-lookup"><span data-stu-id="f34d5-263">Cycling Cap</span></span>|  
|<span data-ttu-id="f34d5-264">3</span><span class="sxs-lookup"><span data-stu-id="f34d5-264">3</span></span>||<span data-ttu-id="f34d5-265">Sport-100</span><span class="sxs-lookup"><span data-stu-id="f34d5-265">Sport-100</span></span>|  
|<span data-ttu-id="f34d5-266">4</span><span class="sxs-lookup"><span data-stu-id="f34d5-266">4</span></span>||<span data-ttu-id="f34d5-267">Long-Sleeve Logo Jersey</span><span class="sxs-lookup"><span data-stu-id="f34d5-267">Long-Sleeve logo Jersey</span></span>|  
|<span data-ttu-id="f34d5-268">5</span><span class="sxs-lookup"><span data-stu-id="f34d5-268">5</span></span>||<span data-ttu-id="f34d5-269">Half-Finger Gloves</span><span class="sxs-lookup"><span data-stu-id="f34d5-269">Half-Finger Gloves</span></span>|  
|<span data-ttu-id="f34d5-270">6</span><span class="sxs-lookup"><span data-stu-id="f34d5-270">6</span></span>||<span data-ttu-id="f34d5-271">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="f34d5-271">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="f34d5-272">7</span><span class="sxs-lookup"><span data-stu-id="f34d5-272">7</span></span>||<span data-ttu-id="f34d5-273">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="f34d5-273">All-Purpose Bike Stand</span></span>|  
  
 <span data-ttu-id="f34d5-274">即使您只預期有一個資料行，結果中仍有三個資料行，因為查詢永遠會為案例資料表傳回一個資料行。</span><span class="sxs-lookup"><span data-stu-id="f34d5-274">There are three columns in the results, even though you might only expect one column, because the query always returns a column for the case table.</span></span> <span data-ttu-id="f34d5-275">此處的結果已扁平化，否則，查詢將會傳回包含兩個巢狀資料表資料行的單一資料行。</span><span class="sxs-lookup"><span data-stu-id="f34d5-275">Here the results are flattened; otherwise, the query would return a single column that contains two nested table columns.</span></span>  
  
 <span data-ttu-id="f34d5-276">$sequence 資料行是 `PredictSequence` 函數預設傳回的資料行，可排序預測結果。</span><span class="sxs-lookup"><span data-stu-id="f34d5-276">The column $sequence is a column returned by default by the `PredictSequence` function to order the prediction results.</span></span> <span data-ttu-id="f34d5-277">在模型中比對時序索引鍵時需要 `[Line Number]`資料行，但是不會輸出這些索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f34d5-277">The column, `[Line Number]`, is required to match the sequence keys in the model, but the keys are not output.</span></span>  
  
 <span data-ttu-id="f34d5-278">有趣的是，All-Purpose Bike Stand 後的前幾個預測時序為 Cycling Cap 和 Cycling Cap。</span><span class="sxs-lookup"><span data-stu-id="f34d5-278">Interestingly, the top predicted sequences after All-Purpose Bike Stand are Cycling Cap and Cycling Cap.</span></span> <span data-ttu-id="f34d5-279">這不是錯誤。</span><span class="sxs-lookup"><span data-stu-id="f34d5-279">This is not an error.</span></span> <span data-ttu-id="f34d5-280">根據資料呈現給客戶的方式，以及定型模型時的分組方式，很可能有這種時序。</span><span class="sxs-lookup"><span data-stu-id="f34d5-280">Depending on how the data is presented to the customer, and how it is grouped when training the model, it is very possible to have sequences of this kind.</span></span> <span data-ttu-id="f34d5-281">例如，如果沒有辦法指定數量，客戶可能會購買一個 Cycling Cap (紅色)，然後又購買另一個 Cycling Cap (藍色)，或者在一個資料列同時購買兩個。</span><span class="sxs-lookup"><span data-stu-id="f34d5-281">For example, a customer might purchase a cycling cap (red) and then another cycling cap (blue), or purchase two in a row if there were no way to specify quantity.</span></span>  
  
 <span data-ttu-id="f34d5-282">資料列 6 和 7 中的值為預留位置。</span><span class="sxs-lookup"><span data-stu-id="f34d5-282">The values in rows 6 and 7 are placeholders.</span></span> <span data-ttu-id="f34d5-283">當您到達可能轉換之鏈結的結尾時，當做輸入傳遞的值會加入到結果中，而非終止預測結果。</span><span class="sxs-lookup"><span data-stu-id="f34d5-283">When you reach the end of the chain of possible transitions, rather than terminating the prediction results, the value that was passed as an input is added to the results.</span></span> <span data-ttu-id="f34d5-284">例如，如果您將預測的數目增加到 20，資料列 6-20 的值將會相同，也就是 All-Purpose Bike Stand。</span><span class="sxs-lookup"><span data-stu-id="f34d5-284">For example, if you increased the number of predictions to 20, the values for rows 6-20 would all be the same, All-Purpose Bike Stand.</span></span>  
  
## <a name="function-list"></a><span data-ttu-id="f34d5-285">函數清單</span><span class="sxs-lookup"><span data-stu-id="f34d5-285">Function List</span></span>  
 <span data-ttu-id="f34d5-286">所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 演算法都支援一組常用的函數。</span><span class="sxs-lookup"><span data-stu-id="f34d5-286">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="f34d5-287">不過， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 時序群集演算法也支援下表所列出的其他函數。</span><span class="sxs-lookup"><span data-stu-id="f34d5-287">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm supports the additional functions that are listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f34d5-288">預測函數</span><span class="sxs-lookup"><span data-stu-id="f34d5-288">Prediction Function</span></span>|<span data-ttu-id="f34d5-289">使用量</span><span class="sxs-lookup"><span data-stu-id="f34d5-289">Usage</span></span>|  
|[<span data-ttu-id="f34d5-290">叢集 &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="f34d5-290">Cluster &#40;DMX&#41;</span></span>](/sql/dmx/cluster-dmx)|<span data-ttu-id="f34d5-291">傳回最可能包含輸入案例的群集</span><span class="sxs-lookup"><span data-stu-id="f34d5-291">Returns the cluster that is most likely to contain the input case</span></span>|  
|[<span data-ttu-id="f34d5-292">ClusterDistance &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="f34d5-292">ClusterDistance &#40;DMX&#41;</span></span>](/sql/dmx/clusterdistance-dmx)|<span data-ttu-id="f34d5-293">傳回輸入案例與指定之群集的距離；如果沒有指定任何群集，則會傳回輸入案例與最可能之群集的距離。</span><span class="sxs-lookup"><span data-stu-id="f34d5-293">Returns the distance of the input case from the specified cluster, or if no cluster is specified, the distance of the input case from the most likely cluster.</span></span><br /><br /> <span data-ttu-id="f34d5-294">此函數可以搭配任何種類的叢集模型 (EM、K-Means 等) 使用，但是結果會隨著演算法而有所不同。</span><span class="sxs-lookup"><span data-stu-id="f34d5-294">This function can be used with any kind of clustering model (EM, K-Means, etc.), but the results differ depending on the algorithm.</span></span>|  
|[<span data-ttu-id="f34d5-295">ClusterProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="f34d5-295">ClusterProbability &#40;DMX&#41;</span></span>](/sql/dmx/clusterprobability-dmx)|<span data-ttu-id="f34d5-296">傳回輸入案例屬於指定之群集的機率。</span><span class="sxs-lookup"><span data-stu-id="f34d5-296">Returns the probability that the input case belongs to the specified cluster.</span></span>|  
|[<span data-ttu-id="f34d5-297">IsInNode &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="f34d5-297">IsInNode &#40;DMX&#41;</span></span>](/sql/dmx/isinnode-dmx)|<span data-ttu-id="f34d5-298">指示指定的節點是否包含目前案例。</span><span class="sxs-lookup"><span data-stu-id="f34d5-298">Indicates whether the specified node contains the current case.</span></span>|  
|[<span data-ttu-id="f34d5-299">PredictAdjustedProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="f34d5-299">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="f34d5-300">傳回指定狀態的已調整機率。</span><span class="sxs-lookup"><span data-stu-id="f34d5-300">Returns the adjusted probability of a specified state.</span></span>|  
|[<span data-ttu-id="f34d5-301">PredictAssociation &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="f34d5-301">PredictAssociation &#40;DMX&#41;</span></span>](/sql/dmx/predictassociation-dmx)|<span data-ttu-id="f34d5-302">預測關聯的成員資格。</span><span class="sxs-lookup"><span data-stu-id="f34d5-302">Predicts associative membership.</span></span>|  
|[<span data-ttu-id="f34d5-303">PredictCaseLikelihood &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="f34d5-303">PredictCaseLikelihood &#40;DMX&#41;</span></span>](/sql/dmx/predictcaselikelihood-dmx)|<span data-ttu-id="f34d5-304">傳回輸入案例符合現有模型的可能性。</span><span class="sxs-lookup"><span data-stu-id="f34d5-304">Returns the likelihood that an input case will fit in the existing model.</span></span>|  
|[<span data-ttu-id="f34d5-305">PredictHistogram &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="f34d5-305">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="f34d5-306">傳回表示給定資料行的預測長條圖的資料表。</span><span class="sxs-lookup"><span data-stu-id="f34d5-306">Returns a table that represents a histogram for the prediction of a given column.</span></span>|  
|[<span data-ttu-id="f34d5-307">PredictNodeId &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="f34d5-307">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="f34d5-308">傳回案例分類之節點的 Node_ID。</span><span class="sxs-lookup"><span data-stu-id="f34d5-308">Returns the Node_ID of the node to which the case is classified.</span></span>|  
|[<span data-ttu-id="f34d5-309">PredictProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="f34d5-309">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="f34d5-310">傳回指定狀態的機率。</span><span class="sxs-lookup"><span data-stu-id="f34d5-310">Returns the probability for a specified state.</span></span>|  
|[<span data-ttu-id="f34d5-311">PredictSequence &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="f34d5-311">PredictSequence &#40;DMX&#41;</span></span>](/sql/dmx/predictsequence-dmx)|<span data-ttu-id="f34d5-312">預測指定之時序資料集合的未來時序值。</span><span class="sxs-lookup"><span data-stu-id="f34d5-312">Predicts future sequence values for a specified set of sequence data.</span></span>|  
|[<span data-ttu-id="f34d5-313">PredictStdev &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="f34d5-313">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="f34d5-314">傳回指定之資料行的預測標準差。</span><span class="sxs-lookup"><span data-stu-id="f34d5-314">Returns the predicted standard deviation for the specified column.</span></span>|  
|[<span data-ttu-id="f34d5-315">PredictSupport &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="f34d5-315">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="f34d5-316">傳回指定狀態的支援值。</span><span class="sxs-lookup"><span data-stu-id="f34d5-316">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="f34d5-317">PredictVariance &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="f34d5-317">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="f34d5-318">傳回指定之資料行的變異數。</span><span class="sxs-lookup"><span data-stu-id="f34d5-318">Returns the variance of a specified column.</span></span>|  
  
 <span data-ttu-id="f34d5-319">如需所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 演算法通用函數的清單，請參閱[一般預測函數 &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx)。</span><span class="sxs-lookup"><span data-stu-id="f34d5-319">For a list of the functions that are common to all [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, see [General Prediction Functions &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).</span></span> <span data-ttu-id="f34d5-320">如需特定函數的語法，請參閱[資料採礦延伸模組 &#40;DMX&#41; 函數參考](/sql/dmx/data-mining-extensions-dmx-function-reference)。</span><span class="sxs-lookup"><span data-stu-id="f34d5-320">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f34d5-321">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f34d5-321">See Also</span></span>  
 <span data-ttu-id="f34d5-322">[資料採礦查詢](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="f34d5-322">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="f34d5-323">[Microsoft 時序群集演算法技術參考](microsoft-sequence-clustering-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f34d5-323">[Microsoft Sequence Clustering Algorithm Technical Reference](microsoft-sequence-clustering-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="f34d5-324">[Microsoft 時序群集演算法](microsoft-sequence-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="f34d5-324">[Microsoft Sequence Clustering Algorithm](microsoft-sequence-clustering-algorithm.md) </span></span>  
 [<span data-ttu-id="f34d5-325">時序叢集模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="f34d5-325">Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-sequence-clustering-models.md)  
  
  
