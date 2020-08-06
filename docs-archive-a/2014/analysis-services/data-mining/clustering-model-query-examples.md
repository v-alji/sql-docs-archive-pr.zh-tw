---
title: 群集模型查詢範例 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clustering [Data Mining]
- content queries [DMX]
- clustering algorithms [Analysis Services]
ms.assetid: bf2ba332-9bc6-411a-a3af-b919c52432c8
author: minewiskan
ms.author: owend
ms.openlocfilehash: fe12b82ce2d237acd060b1e387e7a6dfbf958851
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607177"
---
# <a name="clustering-model-query-examples"></a><span data-ttu-id="4b53a-102">叢集模型查詢範例</span><span class="sxs-lookup"><span data-stu-id="4b53a-102">Clustering Model Query Examples</span></span>
  <span data-ttu-id="4b53a-103">當您根據資料採礦模型建立查詢時，可以擷取有關模型的中繼資料或建立內容查詢，以提供有關在分析中所發現之模式的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="4b53a-103">When you create a query against a data mining model, you can retrieve metadata about the model, or create a content query that provides details about the patterns discovered in analysis.</span></span> <span data-ttu-id="4b53a-104">或者，您可以建立預測查詢，這會使用模型中的模式對新資料進行預測。</span><span class="sxs-lookup"><span data-stu-id="4b53a-104">Alternatively, you can create a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="4b53a-105">每種查詢都會提供不同的資訊。</span><span class="sxs-lookup"><span data-stu-id="4b53a-105">Each type of query will provide different information.</span></span> <span data-ttu-id="4b53a-106">例如，內容查詢可能會提供有關所找到群集的詳細資料，預測查詢則會告訴您最可能包含新資料點的群集。</span><span class="sxs-lookup"><span data-stu-id="4b53a-106">For example, a content query might provide additional details about the clusters that were found, whereas a prediction query might tell you in which cluster a new data point is most likely to belong.</span></span>  
  
 <span data-ttu-id="4b53a-107">本節說明如何針對以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 叢集演算法為基礎的模型建立查詢。</span><span class="sxs-lookup"><span data-stu-id="4b53a-107">This section explains how to create queries for models that are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm.</span></span>  
  
 <span data-ttu-id="4b53a-108">**內容查詢**</span><span class="sxs-lookup"><span data-stu-id="4b53a-108">**Content Queries**</span></span>  
  
 [<span data-ttu-id="4b53a-109">使用 DMX 取得模型中繼資料</span><span class="sxs-lookup"><span data-stu-id="4b53a-109">Getting Model Metadata by Using DMX</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="4b53a-110">從結構描述資料列集擷取模型中繼資料</span><span class="sxs-lookup"><span data-stu-id="4b53a-110">Retrieving Model Metadata from the Schema Rowset</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="4b53a-111">傳回群集或群集清單</span><span class="sxs-lookup"><span data-stu-id="4b53a-111">Returning a Cluster or a List of Clusters</span></span>](#bkmk_Query3)  
  
 [<span data-ttu-id="4b53a-112">傳回群集的屬性</span><span class="sxs-lookup"><span data-stu-id="4b53a-112">Returning Attributes for a Cluster</span></span>](#bkmk_Query4)  
  
 [<span data-ttu-id="4b53a-113">使用系統預存程序傳回群集設定檔</span><span class="sxs-lookup"><span data-stu-id="4b53a-113">Returning a Cluster Profile Using System Stored Procedures</span></span>](#bkmk_Query5)  
  
 [<span data-ttu-id="4b53a-114">尋找群集的辨識因數</span><span class="sxs-lookup"><span data-stu-id="4b53a-114">Finding Discriminating Factors for a Cluster</span></span>](#bkmk_Query6)  
  
 [<span data-ttu-id="4b53a-115">傳回屬於群集的案例</span><span class="sxs-lookup"><span data-stu-id="4b53a-115">Returning Cases that Belong to a Cluster</span></span>](#bkmk_Query7)  
  
 <span data-ttu-id="4b53a-116">**預測查詢**</span><span class="sxs-lookup"><span data-stu-id="4b53a-116">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="4b53a-117">從叢集模型預測結果</span><span class="sxs-lookup"><span data-stu-id="4b53a-117">Predicting Outcomes from a Clustering Model</span></span>](#bkmk_Query8)  
  
 [<span data-ttu-id="4b53a-118">判斷群集成員資格</span><span class="sxs-lookup"><span data-stu-id="4b53a-118">Determining Cluster Membership</span></span>](#bkmk_Query9)  
  
 [<span data-ttu-id="4b53a-119">使用機率和距離傳回所有可能的群集</span><span class="sxs-lookup"><span data-stu-id="4b53a-119">Returning All Possible Clusters with Probability and Distance</span></span>](#bkmk_Query10)  
  
##  <a name="finding-information-about-the-model"></a><a name="bkmk_top2"></a> <span data-ttu-id="4b53a-120">尋找有關模型的資訊</span><span class="sxs-lookup"><span data-stu-id="4b53a-120">Finding Information about the Model</span></span>  
 <span data-ttu-id="4b53a-121">所有的採礦模型都會公開演算法根據標準化結構描述所學習的內容，也就是採礦模型結構描述資料列集。</span><span class="sxs-lookup"><span data-stu-id="4b53a-121">All mining models expose the content learned by the algorithm according to a standardized schema, the mining model schema rowset.</span></span> <span data-ttu-id="4b53a-122">您可以藉由使用資料採礦延伸模組 (DMX) 陳述式來針對採礦模型結構描述資料列集建立查詢。</span><span class="sxs-lookup"><span data-stu-id="4b53a-122">You can create queries against the mining model schema rowset by using Data Mining Extension (DMX) statements.</span></span> <span data-ttu-id="4b53a-123">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，您也可以將結構描述資料列集當做系統資料表直接進行查詢。</span><span class="sxs-lookup"><span data-stu-id="4b53a-123">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can also query the schema rowsets directly as system tables.</span></span>  
  
 [<span data-ttu-id="4b53a-124">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4b53a-124">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-1-getting-model-metadata-by-using-dmx"></a><a name="bkmk_Query1"></a> <span data-ttu-id="4b53a-125">範例查詢 1：使用 DMX 取得模型中繼資料</span><span class="sxs-lookup"><span data-stu-id="4b53a-125">Sample Query 1: Getting Model Metadata by Using DMX</span></span>  
 <span data-ttu-id="4b53a-126">下列查詢會傳回有關您在「基本資料採礦教學課程」中所建立的叢集模型 `TM_Clustering`的基本中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4b53a-126">The following query returns basic metadata about the clustering model, `TM_Clustering`, that you created in the Basic Data Mining Tutorial.</span></span> <span data-ttu-id="4b53a-127">叢集模型的父節點所提供的中繼資料包含模型的名稱、模型儲存位置所在的資料庫，以及模型中子節點的數目。</span><span class="sxs-lookup"><span data-stu-id="4b53a-127">The metadata available in the parent node of a clustering model includes the name of the model, the database where the model is stored, and the number of child nodes in the model.</span></span> <span data-ttu-id="4b53a-128">此查詢會使用 DMX 內容查詢從模型的父節點擷取中繼資料：</span><span class="sxs-lookup"><span data-stu-id="4b53a-128">This query uses a DMX content query to retrieve the metadata from the parent node of the model:</span></span>  
  
```  
SELECT MODEL_CATALOG, MODEL_NAME, NODE_CAPTION,   
NODE_SUPPORT, [CHILDREN_CARDINALITY], NODE_DESCRIPTION  
FROM TM_Clustering.CONTENT  
WHERE NODE_TYPE = 1  
```  
  
> [!NOTE]  
>  <span data-ttu-id="4b53a-129">您必須將資料行 CHILDREN_CARDINALITY 的名稱包含在括號中，好與相同名稱的「多維度運算式」(MDX) 保留關鍵字加以區別。</span><span class="sxs-lookup"><span data-stu-id="4b53a-129">You must enclose the name of the column, CHILDREN_CARDINALITY, in brackets to distinguish it from the Multidimensional Expressions (MDX) reserved keyword of the same name.</span></span>  
  
 <span data-ttu-id="4b53a-130">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="4b53a-130">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4b53a-131">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4b53a-131">MODEL_CATALOG</span></span>|<span data-ttu-id="4b53a-132">TM_Clustering</span><span class="sxs-lookup"><span data-stu-id="4b53a-132">TM_Clustering</span></span>|  
|<span data-ttu-id="4b53a-133">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="4b53a-133">MODEL_NAME</span></span>|<span data-ttu-id="4b53a-134">Adventure Works DW</span><span class="sxs-lookup"><span data-stu-id="4b53a-134">Adventure Works DW</span></span>|  
|<span data-ttu-id="4b53a-135">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="4b53a-135">NODE_CAPTION</span></span>|<span data-ttu-id="4b53a-136">群集模型</span><span class="sxs-lookup"><span data-stu-id="4b53a-136">Cluster Model</span></span>|  
|<span data-ttu-id="4b53a-137">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="4b53a-137">NODE_SUPPORT</span></span>|<span data-ttu-id="4b53a-138">12939</span><span class="sxs-lookup"><span data-stu-id="4b53a-138">12939</span></span>|  
|<span data-ttu-id="4b53a-139">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="4b53a-139">CHILDREN_CARDINALITY</span></span>|<span data-ttu-id="4b53a-140">10</span><span class="sxs-lookup"><span data-stu-id="4b53a-140">10</span></span>|  
|<span data-ttu-id="4b53a-141">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4b53a-141">NODE_DESCRIPTION</span></span>|<span data-ttu-id="4b53a-142">全部</span><span class="sxs-lookup"><span data-stu-id="4b53a-142">All</span></span>|  
  
 <span data-ttu-id="4b53a-143">如需這些資料行在叢集模型中代表意義的定義，請參閱[叢集模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-clustering-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="4b53a-143">For a definition of what these columns mean in a clustering model, see [Mining Model Content for Clustering Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-clustering-models-analysis-services-data-mining.md).</span></span>  
  
 [<span data-ttu-id="4b53a-144">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4b53a-144">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-2-retrieving-model-metadata-from-the-schema-rowset"></a><a name="bkmk_Query2"></a><span data-ttu-id="4b53a-145">範例查詢2：從架構資料列集抓取模型中繼資料</span><span class="sxs-lookup"><span data-stu-id="4b53a-145">Sample Query 2: Retrieving Model Metadata from the Schema Rowset</span></span>  
 <span data-ttu-id="4b53a-146">藉由查詢資料採礦結構描述資料列集，您可以找到與 DMX 內容查詢所傳回的相同的資訊。</span><span class="sxs-lookup"><span data-stu-id="4b53a-146">By querying the data mining schema rowset, you can find the same information that is returned in a DMX content query.</span></span> <span data-ttu-id="4b53a-147">不過，結構描述資料列集會提供某些額外的資料行。</span><span class="sxs-lookup"><span data-stu-id="4b53a-147">However, the schema rowset provides some additional columns.</span></span> <span data-ttu-id="4b53a-148">其中包括在建立模型時所使用的參數、上次處理模型的日期和時間，以及模型的擁有者。</span><span class="sxs-lookup"><span data-stu-id="4b53a-148">These include the parameters that were used when the model was created, the date and time that the model was last processed, and the owner of the model.</span></span>  
  
 <span data-ttu-id="4b53a-149">下列範例會傳回建立、修改以及上次處理模型的日期，也會傳回用來建立模型的叢集參數以及培訓集的大小。</span><span class="sxs-lookup"><span data-stu-id="4b53a-149">The following example returns the date the model was created, modified, and last processed, together with the clustering parameters that were used to build the model, and the size of the training set.</span></span> <span data-ttu-id="4b53a-150">這些資訊對於記錄模型或者判斷用來建立現有模型時所使用的群集選項很有用。</span><span class="sxs-lookup"><span data-stu-id="4b53a-150">This information can be useful for documenting the model, or for determining which of the clustering options were used to create an existing model.</span></span>  
  
```  
SELECT MODEL_NAME, DATE_CREATED, LAST_PROCESSED, PREDICTION_ENTITY, MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_Clustering'  
```  
  
 <span data-ttu-id="4b53a-151">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="4b53a-151">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4b53a-152">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="4b53a-152">MODEL_NAME</span></span>|<span data-ttu-id="4b53a-153">TM_Clustering</span><span class="sxs-lookup"><span data-stu-id="4b53a-153">TM_Clustering</span></span>|  
|<span data-ttu-id="4b53a-154">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="4b53a-154">DATE_CREATED</span></span>|<span data-ttu-id="4b53a-155">10/12/2007 7:42:51 下午</span><span class="sxs-lookup"><span data-stu-id="4b53a-155">10/12/2007 7:42:51 PM</span></span>|  
|<span data-ttu-id="4b53a-156">LAST_PROCESSED</span><span class="sxs-lookup"><span data-stu-id="4b53a-156">LAST_PROCESSED</span></span>|<span data-ttu-id="4b53a-157">10/12/2007 8:09:54 下午</span><span class="sxs-lookup"><span data-stu-id="4b53a-157">10/12/2007 8:09:54 PM</span></span>|  
|<span data-ttu-id="4b53a-158">PREDICTION_ENTITY</span><span class="sxs-lookup"><span data-stu-id="4b53a-158">PREDICTION_ENTITY</span></span>|<span data-ttu-id="4b53a-159">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="4b53a-159">Bike Buyer</span></span>|  
|<span data-ttu-id="4b53a-160">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4b53a-160">MINING_PARAMETERS</span></span>|<span data-ttu-id="4b53a-161">CLUSTER_COUNT=10,</span><span class="sxs-lookup"><span data-stu-id="4b53a-161">CLUSTER_COUNT=10,</span></span><br /><br /> <span data-ttu-id="4b53a-162">CLUSTER_SEED=0,</span><span class="sxs-lookup"><span data-stu-id="4b53a-162">CLUSTER_SEED=0,</span></span><br /><br /> <span data-ttu-id="4b53a-163">CLUSTERING_METHOD=1,</span><span class="sxs-lookup"><span data-stu-id="4b53a-163">CLUSTERING_METHOD=1,</span></span><br /><br /> <span data-ttu-id="4b53a-164">MAXIMUM_INPUT_ATTRIBUTES=255,</span><span class="sxs-lookup"><span data-stu-id="4b53a-164">MAXIMUM_INPUT_ATTRIBUTES=255,</span></span><br /><br /> <span data-ttu-id="4b53a-165">MAXIMUM_STATES=100,</span><span class="sxs-lookup"><span data-stu-id="4b53a-165">MAXIMUM_STATES=100,</span></span><br /><br /> <span data-ttu-id="4b53a-166">MINIMUM_SUPPORT=1,</span><span class="sxs-lookup"><span data-stu-id="4b53a-166">MINIMUM_SUPPORT=1,</span></span><br /><br /> <span data-ttu-id="4b53a-167">MODELLING_CARDINALITY=10,</span><span class="sxs-lookup"><span data-stu-id="4b53a-167">MODELLING_CARDINALITY=10,</span></span><br /><br /> <span data-ttu-id="4b53a-168">SAMPLE_SIZE=50000,</span><span class="sxs-lookup"><span data-stu-id="4b53a-168">SAMPLE_SIZE=50000,</span></span><br /><br /> <span data-ttu-id="4b53a-169">STOPPING_TOLERANCE=10</span><span class="sxs-lookup"><span data-stu-id="4b53a-169">STOPPING_TOLERANCE=10</span></span>|  
  
 [<span data-ttu-id="4b53a-170">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4b53a-170">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="finding-information-about-clusters"></a><span data-ttu-id="4b53a-171">尋找有關群集的資訊</span><span class="sxs-lookup"><span data-stu-id="4b53a-171">Finding Information about Clusters</span></span>  
 <span data-ttu-id="4b53a-172">叢集模型上最有用的內容查詢所傳回的資訊類型，通常與可以使用 [叢集檢視器]\*\*\*\* 瀏覽的資訊類型相同。</span><span class="sxs-lookup"><span data-stu-id="4b53a-172">The most useful content queries on clustering models generally return the same type of information that you can browse by using the **Cluster Viewer**.</span></span> <span data-ttu-id="4b53a-173">這包括群集設定檔、群集特性和群集辨識。</span><span class="sxs-lookup"><span data-stu-id="4b53a-173">This includes cluster profiles, cluster characteristics, and cluster discrimination.</span></span> <span data-ttu-id="4b53a-174">本章節提供會擷取這些資訊的查詢範例。</span><span class="sxs-lookup"><span data-stu-id="4b53a-174">This section provides examples of queries that retrieve this information.</span></span>  
  
###  <a name="sample-query-3-returning-a-cluster-or-list-of-clusters"></a><a name="bkmk_Query3"></a> <span data-ttu-id="4b53a-175">範例查詢 3：傳回群集或群集清單</span><span class="sxs-lookup"><span data-stu-id="4b53a-175">Sample Query 3: Returning a Cluster or List of Clusters</span></span>  
 <span data-ttu-id="4b53a-176">因為所有的群集都具有節點類型 5，所以您可以僅針對該類型的節點查詢模型內容，以輕鬆地擷取群集清單。</span><span class="sxs-lookup"><span data-stu-id="4b53a-176">Because all clusters have a node type of 5, you can easily retrieve a list of the clusters by querying the model content for only the nodes of that type.</span></span> <span data-ttu-id="4b53a-177">您也可以篩選由機率或支援所傳回的節點，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4b53a-177">You can also filter the nodes that are returned by probability or by support, as shown in this example.</span></span>  
  
```  
SELECT NODE_NAME, NODE_CAPTION ,NODE_SUPPORT, NODE_DESCRIPTION  
FROM TM_Clustering.CONTENT  
WHERE NODE_TYPE = 5 AND NODE_SUPPORT > 1000  
```  
  
 <span data-ttu-id="4b53a-178">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="4b53a-178">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4b53a-179">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b53a-179">NODE_NAME</span></span>|<span data-ttu-id="4b53a-180">002</span><span class="sxs-lookup"><span data-stu-id="4b53a-180">002</span></span>|  
|<span data-ttu-id="4b53a-181">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="4b53a-181">NODE_CAPTION</span></span>|<span data-ttu-id="4b53a-182">群集 2</span><span class="sxs-lookup"><span data-stu-id="4b53a-182">Cluster 2</span></span>|  
|<span data-ttu-id="4b53a-183">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="4b53a-183">NODE_SUPPORT</span></span>|<span data-ttu-id="4b53a-184">1649</span><span class="sxs-lookup"><span data-stu-id="4b53a-184">1649</span></span>|  
|<span data-ttu-id="4b53a-185">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4b53a-185">NODE_DESCRIPTION</span></span>|<span data-ttu-id="4b53a-186">English Education=Graduate Degree , 32 <=Age <=48 , Number Cars Owned=0 , 35964.0771121808 <=Yearly Income <=97407.7163393957 , English Occupation=Professional , Commute Distance=2-5 Miles , Region=North America , Bike Buyer=1 , Number Children At Home=0 , Number Cars Owned=1 , Commute Distance=0-1 Miles , English Education=Bachelors , Total Children=1 , Number Children At Home=2 , English Occupation=Skilled Manual , Marital Status=S , Total Children=0 , House Owner Flag=0 , Gender=F , Total Children=2 , Region=Pacific</span><span class="sxs-lookup"><span data-stu-id="4b53a-186">English Education=Graduate Degree , 32 <=Age <=48 , Number Cars Owned=0 , 35964.0771121808 <=Yearly Income <=97407.7163393957 , English Occupation=Professional , Commute Distance=2-5 Miles , Region=North America , Bike Buyer=1 , Number Children At Home=0 , Number Cars Owned=1 , Commute Distance=0-1 Miles , English Education=Bachelors , Total Children=1 , Number Children At Home=2 , English Occupation=Skilled Manual , Marital Status=S , Total Children=0 , House Owner Flag=0 , Gender=F , Total Children=2 , Region=Pacific</span></span>|  
  
 <span data-ttu-id="4b53a-187">您可在資料採礦結構描述資料列集中的兩個資料行中找到定義群集的屬性。</span><span class="sxs-lookup"><span data-stu-id="4b53a-187">The attributes that define the cluster can be found in two columns in the data mining schema rowset.</span></span>  
  
-   <span data-ttu-id="4b53a-188">NODE_DESCRIPTION 資料行包含以逗號分隔的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="4b53a-188">The NODE_DESCRIPTION column contains a comma-separated list of attributes.</span></span> <span data-ttu-id="4b53a-189">請注意屬性清單可以針對顯示用途而進行縮寫。</span><span class="sxs-lookup"><span data-stu-id="4b53a-189">Note that the list of attributes might be abbreviated for display purposes.</span></span>  
  
-   <span data-ttu-id="4b53a-190">NODE_DISTRIBUTION 資料行中的巢狀資料表包含群集的完整屬性清單。</span><span class="sxs-lookup"><span data-stu-id="4b53a-190">The nested table in the NODE_DISTRIBUTION column contains the full list of attributes for the cluster.</span></span> <span data-ttu-id="4b53a-191">如果用戶端不支援階層式資料列集，則您可以在 SELECT 資料行清單之前加入 FLATTENED 關鍵字傳回巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="4b53a-191">If your client does not support hierarchical rowsets, you can return the nested table by adding the FLATTENED keyword before the SELECT column list.</span></span> <span data-ttu-id="4b53a-192">如需 FLATTENED 關鍵字使用的詳細資訊，請參閱 [SELECT FROM &#60;model&#62;.CONTENT &#40;DMX&#41;](/sql/dmx/select-from-model-dimension-content-dmx)。</span><span class="sxs-lookup"><span data-stu-id="4b53a-192">For more information about the use of the FLATTENED keyword, see [SELECT FROM &#60;model&#62;.CONTENT &#40;DMX&#41;](/sql/dmx/select-from-model-dimension-content-dmx).</span></span>  
  
 [<span data-ttu-id="4b53a-193">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4b53a-193">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-4-returning-attributes-for-a-cluster"></a><a name="bkmk_Query4"></a> <span data-ttu-id="4b53a-194">範例查詢 4：傳回群集的屬性</span><span class="sxs-lookup"><span data-stu-id="4b53a-194">Sample Query 4: Returning Attributes for a Cluster</span></span>  
 <span data-ttu-id="4b53a-195">對於每個叢集而言，[叢集檢視器]\*\*\*\* 會顯示列出屬性及其值的設定檔。</span><span class="sxs-lookup"><span data-stu-id="4b53a-195">For every cluster, the **Cluster Viewer** displays a profile that lists the attributes and their values.</span></span> <span data-ttu-id="4b53a-196">檢視器也會顯示長條圖，以顯示模型中整個案例母體的值分佈情形。</span><span class="sxs-lookup"><span data-stu-id="4b53a-196">The viewer also displays a histogram that shows the distribution of values for the whole population of cases in the model.</span></span> <span data-ttu-id="4b53a-197">如果是在檢視器中瀏覽模型，則您可以輕鬆地從「採礦圖例」複製長條圖，然後將它貼入至 Excel 或 Word 文件。</span><span class="sxs-lookup"><span data-stu-id="4b53a-197">If you are browsing the model in the viewer, you can easily copy the histogram from the Mining Legend and then paste it to Excel or a Word document.</span></span> <span data-ttu-id="4b53a-198">也可以使用檢視器的 [群集特性] 窗格，以圖形方式比較不同群集的屬性。</span><span class="sxs-lookup"><span data-stu-id="4b53a-198">You can also use the Cluster Characteristics pane of the viewer to graphically compare the attributes of different clusters.</span></span>  
  
 <span data-ttu-id="4b53a-199">不過，如果一次必須取得一個以上群集的值，對模型進行查詢是比較簡單的方式。</span><span class="sxs-lookup"><span data-stu-id="4b53a-199">However, if you must obtain values for more than one cluster at a time, it is easier to query the model.</span></span> <span data-ttu-id="4b53a-200">例如，您在瀏覽模型時，可能會注意到最上面兩個叢集在 `Number Cars Owned`屬性方面不同。</span><span class="sxs-lookup"><span data-stu-id="4b53a-200">For example, when you browse the model, you might notice that the top two clusters differ with regard to one attribute, `Number Cars Owned`.</span></span> <span data-ttu-id="4b53a-201">因此可能會想針對每個群集擷取值。</span><span class="sxs-lookup"><span data-stu-id="4b53a-201">Therefore, you want to extract the values for each cluster.</span></span>  
  
```  
SELECT TOP 2 NODE_NAME,   
(SELECT ATTRIBUTE_VALUE, [PROBABILITY] FROM NODE_DISTRIBUTION WHERE ATTRIBUTE_NAME = 'Number Cars Owned')  
AS t  
FROM [TM_Clustering].CONTENT  
WHERE NODE_TYPE = 5  
```  
  
 <span data-ttu-id="4b53a-202">程式碼的第一行指定您只想要最上面兩個群集。</span><span class="sxs-lookup"><span data-stu-id="4b53a-202">The first line of the code specifies that you want only the top two clusters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b53a-203">依預設，群集會依支援來排序。</span><span class="sxs-lookup"><span data-stu-id="4b53a-203">By default, the clusters are ordered by support.</span></span> <span data-ttu-id="4b53a-204">因此，NODE_SUPPORT 資料行可以省略。</span><span class="sxs-lookup"><span data-stu-id="4b53a-204">Therefore, the NODE_SUPPORT column can be omitted.</span></span>  
  
 <span data-ttu-id="4b53a-205">程式碼的第二行會加入子 SELECT 陳述式，此陳述式僅會從巢狀資料表資料行傳回特定的資料行；</span><span class="sxs-lookup"><span data-stu-id="4b53a-205">The second line of the code adds a sub-select statement that returns only certain columns from the nested table column.</span></span> <span data-ttu-id="4b53a-206">此外，它也會將巢狀資料表的資料列限制為與目標屬性 `Number Cars Owned`相關的資料列。</span><span class="sxs-lookup"><span data-stu-id="4b53a-206">Furthermore, it restricts the rows from the nested table to those related to the target attribute, `Number Cars Owned`.</span></span> <span data-ttu-id="4b53a-207">為了檢視顯示，巢狀資料表會使用別名。</span><span class="sxs-lookup"><span data-stu-id="4b53a-207">To simplify the display, the nested table is aliased.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b53a-208">巢狀資料表資料行 `PROBABILITY`必須包含在括號中，因為它也是 MDX 保留關鍵字的名稱。</span><span class="sxs-lookup"><span data-stu-id="4b53a-208">The nested table column, `PROBABILITY`, must be enclosed in brackets because it is also the name of a reserved MDX keyword.</span></span>  
>   
>  <span data-ttu-id="4b53a-209">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="4b53a-209">Example results:</span></span>  
  
|<span data-ttu-id="4b53a-210">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="4b53a-210">NODE_NAME</span></span>|<span data-ttu-id="4b53a-211">T.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="4b53a-211">T.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="4b53a-212">T.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="4b53a-212">T.PROBABILITY</span></span>|  
|----------------|------------------------|-------------------|  
|<span data-ttu-id="4b53a-213">001</span><span class="sxs-lookup"><span data-stu-id="4b53a-213">001</span></span>|<span data-ttu-id="4b53a-214">2</span><span class="sxs-lookup"><span data-stu-id="4b53a-214">2</span></span>|<span data-ttu-id="4b53a-215">0.829207754</span><span class="sxs-lookup"><span data-stu-id="4b53a-215">0.829207754</span></span>|  
|<span data-ttu-id="4b53a-216">001</span><span class="sxs-lookup"><span data-stu-id="4b53a-216">001</span></span>|<span data-ttu-id="4b53a-217">1</span><span class="sxs-lookup"><span data-stu-id="4b53a-217">1</span></span>|<span data-ttu-id="4b53a-218">0.109354156</span><span class="sxs-lookup"><span data-stu-id="4b53a-218">0.109354156</span></span>|  
|<span data-ttu-id="4b53a-219">001</span><span class="sxs-lookup"><span data-stu-id="4b53a-219">001</span></span>|<span data-ttu-id="4b53a-220">3</span><span class="sxs-lookup"><span data-stu-id="4b53a-220">3</span></span>|<span data-ttu-id="4b53a-221">0.034481552</span><span class="sxs-lookup"><span data-stu-id="4b53a-221">0.034481552</span></span>|  
|<span data-ttu-id="4b53a-222">001</span><span class="sxs-lookup"><span data-stu-id="4b53a-222">001</span></span>|<span data-ttu-id="4b53a-223">4</span><span class="sxs-lookup"><span data-stu-id="4b53a-223">4</span></span>|<span data-ttu-id="4b53a-224">0.013503302</span><span class="sxs-lookup"><span data-stu-id="4b53a-224">0.013503302</span></span>|  
|<span data-ttu-id="4b53a-225">001</span><span class="sxs-lookup"><span data-stu-id="4b53a-225">001</span></span>|<span data-ttu-id="4b53a-226">0</span><span class="sxs-lookup"><span data-stu-id="4b53a-226">0</span></span>|<span data-ttu-id="4b53a-227">0.013453236</span><span class="sxs-lookup"><span data-stu-id="4b53a-227">0.013453236</span></span>|  
|<span data-ttu-id="4b53a-228">001</span><span class="sxs-lookup"><span data-stu-id="4b53a-228">001</span></span>|<span data-ttu-id="4b53a-229">Missing</span><span class="sxs-lookup"><span data-stu-id="4b53a-229">Missing</span></span>|<span data-ttu-id="4b53a-230">0</span><span class="sxs-lookup"><span data-stu-id="4b53a-230">0</span></span>|  
|<span data-ttu-id="4b53a-231">002</span><span class="sxs-lookup"><span data-stu-id="4b53a-231">002</span></span>|<span data-ttu-id="4b53a-232">0</span><span class="sxs-lookup"><span data-stu-id="4b53a-232">0</span></span>|<span data-ttu-id="4b53a-233">0.576980023</span><span class="sxs-lookup"><span data-stu-id="4b53a-233">0.576980023</span></span>|  
|<span data-ttu-id="4b53a-234">002</span><span class="sxs-lookup"><span data-stu-id="4b53a-234">002</span></span>|<span data-ttu-id="4b53a-235">1</span><span class="sxs-lookup"><span data-stu-id="4b53a-235">1</span></span>|<span data-ttu-id="4b53a-236">0.406623939</span><span class="sxs-lookup"><span data-stu-id="4b53a-236">0.406623939</span></span>|  
|<span data-ttu-id="4b53a-237">002</span><span class="sxs-lookup"><span data-stu-id="4b53a-237">002</span></span>|<span data-ttu-id="4b53a-238">2</span><span class="sxs-lookup"><span data-stu-id="4b53a-238">2</span></span>|<span data-ttu-id="4b53a-239">0.016380082</span><span class="sxs-lookup"><span data-stu-id="4b53a-239">0.016380082</span></span>|  
|<span data-ttu-id="4b53a-240">002</span><span class="sxs-lookup"><span data-stu-id="4b53a-240">002</span></span>|<span data-ttu-id="4b53a-241">3</span><span class="sxs-lookup"><span data-stu-id="4b53a-241">3</span></span>|<span data-ttu-id="4b53a-242">1.60E-05</span><span class="sxs-lookup"><span data-stu-id="4b53a-242">1.60E-05</span></span>|  
|<span data-ttu-id="4b53a-243">002</span><span class="sxs-lookup"><span data-stu-id="4b53a-243">002</span></span>|<span data-ttu-id="4b53a-244">4</span><span class="sxs-lookup"><span data-stu-id="4b53a-244">4</span></span>|<span data-ttu-id="4b53a-245">0</span><span class="sxs-lookup"><span data-stu-id="4b53a-245">0</span></span>|  
|<span data-ttu-id="4b53a-246">002</span><span class="sxs-lookup"><span data-stu-id="4b53a-246">002</span></span>|<span data-ttu-id="4b53a-247">Missing</span><span class="sxs-lookup"><span data-stu-id="4b53a-247">Missing</span></span>|<span data-ttu-id="4b53a-248">0</span><span class="sxs-lookup"><span data-stu-id="4b53a-248">0</span></span>|  
  
 [<span data-ttu-id="4b53a-249">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4b53a-249">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-5-return-a-cluster-profile-using-system-stored-procedures"></a><a name="bkmk_Query5"></a> <span data-ttu-id="4b53a-250">範例查詢 5：使用系統預存程序傳回群集設定檔</span><span class="sxs-lookup"><span data-stu-id="4b53a-250">Sample Query 5: Return a Cluster Profile Using System Stored Procedures</span></span>  
 <span data-ttu-id="4b53a-251">如果不想要使用 DMX 撰寫自己的查詢，也可以呼叫 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 用來使用叢集的系統預存程序當做捷徑。</span><span class="sxs-lookup"><span data-stu-id="4b53a-251">As a shortcut, rather than writing your own queries by using DMX, you can also call the system stored procedures that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses to work with clusters.</span></span> <span data-ttu-id="4b53a-252">下列範例將說明如何使用內部預存程序為識別碼 002 的群集傳回設定檔。</span><span class="sxs-lookup"><span data-stu-id="4b53a-252">The following example illustrates how to use the internal stored procedures to return the profile for a cluster with the ID of 002.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterProfiles('TM_Clustering", '002',0.0005  
```  
  
 <span data-ttu-id="4b53a-253">同樣地，您可以使用系統預存程序來傳回特定群集的特性，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="4b53a-253">Similarly, you can use a system stored procedure to return the characteristics of a specific cluster, as shown in the following example:</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterCharacteristics('TM_Clustering", '009',0.0005  
```  
  
 <span data-ttu-id="4b53a-254">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="4b53a-254">Example results:</span></span>  
  
|<span data-ttu-id="4b53a-255">屬性</span><span class="sxs-lookup"><span data-stu-id="4b53a-255">Attributes</span></span>|<span data-ttu-id="4b53a-256">值</span><span class="sxs-lookup"><span data-stu-id="4b53a-256">Values</span></span>|<span data-ttu-id="4b53a-257">頻率</span><span class="sxs-lookup"><span data-stu-id="4b53a-257">Frequency</span></span>|<span data-ttu-id="4b53a-258">支援</span><span class="sxs-lookup"><span data-stu-id="4b53a-258">Support</span></span>|  
|----------------|------------|---------------|-------------|  
|<span data-ttu-id="4b53a-259">Number Children At Home</span><span class="sxs-lookup"><span data-stu-id="4b53a-259">Number Children at Home</span></span>|<span data-ttu-id="4b53a-260">0</span><span class="sxs-lookup"><span data-stu-id="4b53a-260">0</span></span>|<span data-ttu-id="4b53a-261">0.999999829076798</span><span class="sxs-lookup"><span data-stu-id="4b53a-261">0.999999829076798</span></span>|<span data-ttu-id="4b53a-262">899</span><span class="sxs-lookup"><span data-stu-id="4b53a-262">899</span></span>|  
|<span data-ttu-id="4b53a-263">區域</span><span class="sxs-lookup"><span data-stu-id="4b53a-263">Region</span></span>|<span data-ttu-id="4b53a-264">北美洲</span><span class="sxs-lookup"><span data-stu-id="4b53a-264">North America</span></span>|<span data-ttu-id="4b53a-265">0.999852875241508</span><span class="sxs-lookup"><span data-stu-id="4b53a-265">0.999852875241508</span></span>|<span data-ttu-id="4b53a-266">899</span><span class="sxs-lookup"><span data-stu-id="4b53a-266">899</span></span>|  
|<span data-ttu-id="4b53a-267">Total Children</span><span class="sxs-lookup"><span data-stu-id="4b53a-267">Total Children</span></span>|<span data-ttu-id="4b53a-268">0</span><span class="sxs-lookup"><span data-stu-id="4b53a-268">0</span></span>|<span data-ttu-id="4b53a-269">0.993860958572323</span><span class="sxs-lookup"><span data-stu-id="4b53a-269">0.993860958572323</span></span>|<span data-ttu-id="4b53a-270">893</span><span class="sxs-lookup"><span data-stu-id="4b53a-270">893</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="4b53a-271">資料採礦系統預存程序供內部使用， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 保留依需求變更這些程序的權利。</span><span class="sxs-lookup"><span data-stu-id="4b53a-271">The data mining system stored procedures are for internal use and [!INCLUDE[msCoName](../../includes/msconame-md.md)] reserves the right to change them as needed.</span></span> <span data-ttu-id="4b53a-272">在實際執行環境中，建議您使用 DMX、AMO 或 XMLA 建立查詢。</span><span class="sxs-lookup"><span data-stu-id="4b53a-272">For production use, we recommend that you create queries by using DMX, AMO, or XMLA.</span></span>  
  
 [<span data-ttu-id="4b53a-273">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4b53a-273">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-6-find-discriminating-factors-for-a-cluster"></a><a name="bkmk_Query6"></a> <span data-ttu-id="4b53a-274">範例查詢 6：尋找群集的辨識因數</span><span class="sxs-lookup"><span data-stu-id="4b53a-274">Sample Query 6: Find Discriminating Factors for a Cluster</span></span>  
 <span data-ttu-id="4b53a-275">[叢集檢視器]\*\*\*\* 的 [叢集辨識]\*\*\*\* 索引標籤可讓您輕鬆地將某個叢集與另一個叢集相比較，或將某個叢集與所有其餘案例 (叢集的補充) 相比較。</span><span class="sxs-lookup"><span data-stu-id="4b53a-275">The **Cluster Discrimination** tab of the **Cluster Viewer** enables you to easily compare a cluster with another cluster, or compare a cluster with all remaining cases (the complement of the cluster).</span></span>  
  
 <span data-ttu-id="4b53a-276">不過，要建立傳回此資訊的查詢可能很複雜，而且您可能需要在用戶端上進行一些額外的處理，並比較兩個或更多查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="4b53a-276">However, creating queries to return this information can be complex, and you might need some additional processing on the client to store the temporary results and compare the results of two or more queries.</span></span> <span data-ttu-id="4b53a-277">所以可以使用系統預存程序當做捷徑。</span><span class="sxs-lookup"><span data-stu-id="4b53a-277">As a shortcut, you can use the system stored procedures.</span></span>  
  
 <span data-ttu-id="4b53a-278">下列查詢會傳回單一資料表，指出擁有節點識別碼 009 和 007 的兩個群集間的主要辨識因數。</span><span class="sxs-lookup"><span data-stu-id="4b53a-278">The following query returns a single table that indicates the primary discriminating factors between the two clusters that have the node IDs of 009 and 007.</span></span> <span data-ttu-id="4b53a-279">具有正值的屬性會使用群集 009，具有負值的屬性則使用群集 007。</span><span class="sxs-lookup"><span data-stu-id="4b53a-279">Attributes with positive values favor cluster 009, whereas attributes with negative values favor cluster 007.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterDiscrimination('TM_Clustering','009','007',0.0005,true)  
```  
  
 <span data-ttu-id="4b53a-280">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="4b53a-280">Example results:</span></span>  
  
|<span data-ttu-id="4b53a-281">屬性</span><span class="sxs-lookup"><span data-stu-id="4b53a-281">Attributes</span></span>|<span data-ttu-id="4b53a-282">值</span><span class="sxs-lookup"><span data-stu-id="4b53a-282">Values</span></span>|<span data-ttu-id="4b53a-283">分數</span><span class="sxs-lookup"><span data-stu-id="4b53a-283">Score</span></span>|  
|----------------|------------|-----------|  
|<span data-ttu-id="4b53a-284">區域</span><span class="sxs-lookup"><span data-stu-id="4b53a-284">Region</span></span>|<span data-ttu-id="4b53a-285">北美洲</span><span class="sxs-lookup"><span data-stu-id="4b53a-285">North America</span></span>|<span data-ttu-id="4b53a-286">100</span><span class="sxs-lookup"><span data-stu-id="4b53a-286">100</span></span>|  
|<span data-ttu-id="4b53a-287">English Occupation</span><span class="sxs-lookup"><span data-stu-id="4b53a-287">English Occupation</span></span>|<span data-ttu-id="4b53a-288">Skilled Manual</span><span class="sxs-lookup"><span data-stu-id="4b53a-288">Skilled Manual</span></span>|<span data-ttu-id="4b53a-289">94.9003803898654</span><span class="sxs-lookup"><span data-stu-id="4b53a-289">94.9003803898654</span></span>|  
|<span data-ttu-id="4b53a-290">區域</span><span class="sxs-lookup"><span data-stu-id="4b53a-290">Region</span></span>|<span data-ttu-id="4b53a-291">歐洲</span><span class="sxs-lookup"><span data-stu-id="4b53a-291">Europe</span></span>|<span data-ttu-id="4b53a-292">-72.5041051379789</span><span class="sxs-lookup"><span data-stu-id="4b53a-292">-72.5041051379789</span></span>|  
|<span data-ttu-id="4b53a-293">English Occupation</span><span class="sxs-lookup"><span data-stu-id="4b53a-293">English Occupation</span></span>|<span data-ttu-id="4b53a-294">手動</span><span class="sxs-lookup"><span data-stu-id="4b53a-294">Manual</span></span>|<span data-ttu-id="4b53a-295">-69.6503163202722</span><span class="sxs-lookup"><span data-stu-id="4b53a-295">-69.6503163202722</span></span>|  
  
 <span data-ttu-id="4b53a-296">這與您從第一個下拉式清單選取叢集 9 和從第二個下拉式清單選取叢集 7 時，在 [叢集辨識]\*\*\*\* 檢視器的圖表中所展示的資訊相同。</span><span class="sxs-lookup"><span data-stu-id="4b53a-296">This is the same information that is presented in the chart of the **Cluster Discrimination** viewer if you select Cluster 9 from the first drop-down list and Cluster 7 from the second drop-down list.</span></span> <span data-ttu-id="4b53a-297">若要將群集 9 與其補充相較，可以使用第二個參數中的空字串，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="4b53a-297">To compare cluster 9 with its complement, you use the empty string in the second parameter, as shown in the following example:</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterDiscrimination('TM_Clustering','009','',0.0005,true)  
```  
  
> [!NOTE]  
>  <span data-ttu-id="4b53a-298">資料採礦系統預存程序供內部使用， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 保留依需求變更這些程序的權利。</span><span class="sxs-lookup"><span data-stu-id="4b53a-298">The data mining system stored procedures are for internal use and [!INCLUDE[msCoName](../../includes/msconame-md.md)] reserves the right to change them as needed.</span></span> <span data-ttu-id="4b53a-299">在實際執行環境中，建議您使用 DMX、AMO 或 XMLA 建立查詢。</span><span class="sxs-lookup"><span data-stu-id="4b53a-299">For production use, we recommend that you create queries by using DMX, AMO, or XMLA.</span></span>  
  
 [<span data-ttu-id="4b53a-300">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4b53a-300">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-7-returning-cases-that-belong-to-a-cluster"></a><a name="bkmk_Query7"></a> <span data-ttu-id="4b53a-301">範例查詢 7：傳回屬於群集的案例</span><span class="sxs-lookup"><span data-stu-id="4b53a-301">Sample Query 7: Returning Cases that Belong to a Cluster</span></span>  
 <span data-ttu-id="4b53a-302">如果您已在採礦模型上啟用鑽研，則可以建立查詢以傳回有關在模型中所使用案例的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="4b53a-302">If drillthrough has been enabled on the mining model, you can create queries that return detailed information about the cases used in the model.</span></span> <span data-ttu-id="4b53a-303">此外，如果已在採礦結構上啟用鑽研，則您可以使用 [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) 函數來包含來自基礎結構的資料行。</span><span class="sxs-lookup"><span data-stu-id="4b53a-303">Moreover, if drillthrough has been enabled on the mining structure, you can include columns from the underlying structure by using the [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) function.</span></span>  
  
 <span data-ttu-id="4b53a-304">下列範例會傳回模型中使用的兩個資料行：Age 和 Region，以及另一個未用於模型中的資料行 First Name。</span><span class="sxs-lookup"><span data-stu-id="4b53a-304">The following example returns two columns that were used in the model, Age and Region, and one more column, First Name, that was not used in the model.</span></span> <span data-ttu-id="4b53a-305">該查詢只會傳回分類為 Cluster 1 的案例。</span><span class="sxs-lookup"><span data-stu-id="4b53a-305">The query returns only cases that were classified into Cluster 1.</span></span>  
  
```  
SELECT [Age], [Region], StructureColumn('First Name')  
FROM [TM_Clustering].CASES  
WHERE IsInNode('001')  
```  
  
 <span data-ttu-id="4b53a-306">若要傳回屬於群集的案例，您必須知道群集的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4b53a-306">To return the cases that belong to a cluster, you must know the ID of the cluster.</span></span> <span data-ttu-id="4b53a-307">您可以在其中一個檢視器中瀏覽模型，以取得群集的識別碼，</span><span class="sxs-lookup"><span data-stu-id="4b53a-307">You can obtain the ID of the cluster by browsing the model in one of the viewers.</span></span> <span data-ttu-id="4b53a-308">或者也可以將群集重新命名以方便參考，在這之後您可以使用名稱來取代識別碼。</span><span class="sxs-lookup"><span data-stu-id="4b53a-308">Or, you can rename a cluster for easier reference, after which you could use the name in place of an ID number.</span></span> <span data-ttu-id="4b53a-309">不過，您必須知道指派給群集的名稱會在重新處理模型之後遺失。</span><span class="sxs-lookup"><span data-stu-id="4b53a-309">However, know that the names that you assign to a cluster will be lost if the model is reprocessed.</span></span>  
  
 [<span data-ttu-id="4b53a-310">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4b53a-310">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="making-predictions-using-the-model"></a><span data-ttu-id="4b53a-311">使用模型進行預測</span><span class="sxs-lookup"><span data-stu-id="4b53a-311">Making Predictions using the Model</span></span>  
 <span data-ttu-id="4b53a-312">雖然叢集通常是用來描述和了解資料， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 實作也可以讓您進行有關叢集成員資格的預測，並傳回與預測相關聯的機率。</span><span class="sxs-lookup"><span data-stu-id="4b53a-312">Although clustering is typically used for describing and understanding data, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] implementation also lets you make prediction about cluster membership, and return probabilities associated with the prediction.</span></span> <span data-ttu-id="4b53a-313">本章節也針對如何在叢集模型上建立預測查詢提供範例。</span><span class="sxs-lookup"><span data-stu-id="4b53a-313">This section provides examples of how to create prediction queries on clustering models.</span></span> <span data-ttu-id="4b53a-314">您可以藉由指定表格式資料來源對多個案例進行預測，或者也可以藉由建立單一查詢，一次提供一個新值。</span><span class="sxs-lookup"><span data-stu-id="4b53a-314">You can make predictions for multiple cases, by specifying a tabular data source, or you can provide new values on at a time by creating a singleton query.</span></span> <span data-ttu-id="4b53a-315">為了清楚起見，本節中的範例全都是單一查詢。</span><span class="sxs-lookup"><span data-stu-id="4b53a-315">For clarity the examples in this section are all singleton queries.</span></span>  
  
 <span data-ttu-id="4b53a-316">如需如何使用 DMX 建立預測查詢的詳細資訊，請參閱[資料採礦查詢介面](data-mining-query-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="4b53a-316">For more information about how to create prediction queries using DMX, see [Data Mining Query Interfaces](data-mining-query-tools.md).</span></span>  
  
 [<span data-ttu-id="4b53a-317">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4b53a-317">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-8-predicting-outcomes-from-a-clustering-model"></a><a name="bkmk_Query8"></a> <span data-ttu-id="4b53a-318">範例查詢 8：叢集模型的預測結果</span><span class="sxs-lookup"><span data-stu-id="4b53a-318">Sample Query 8: Predicting Outcomes from a Clustering Model</span></span>  
 <span data-ttu-id="4b53a-319">如果您建立的叢集模型包含可預測屬性，則您可以使用模型來建立有關結果的預測。</span><span class="sxs-lookup"><span data-stu-id="4b53a-319">If the clustering model you create contains a predictable attribute, you can use the model to make predictions about outcomes.</span></span> <span data-ttu-id="4b53a-320">不過，模型會根據可預測資料行是設定為 `Predict` 或 `PredictOnly`，以不同的方式處理可預測屬性。</span><span class="sxs-lookup"><span data-stu-id="4b53a-320">However, the model handles the predictable attribute differently depending on whether you set the predictable column to `Predict` or `PredictOnly`.</span></span> <span data-ttu-id="4b53a-321">如果將資料行的用法設定為 `Predict`，則該屬性的值會加入至群集模型，並在完成的模型中顯示為屬性。</span><span class="sxs-lookup"><span data-stu-id="4b53a-321">If you set the usage of the column to `Predict`, the values for that attribute are added to the clustering model and appear as attributes in the finished model.</span></span> <span data-ttu-id="4b53a-322">不過，如果將資料行的使用方式設定為 `PredictOnly`，則值不會用來建立群集。</span><span class="sxs-lookup"><span data-stu-id="4b53a-322">However, if you set the usage of the column to `PredictOnly`, the values are not used to create clusters.</span></span> <span data-ttu-id="4b53a-323">反而是在模式完成後，群集演算法會根據每個案例所屬的群集，為 `PredictOnly` 屬性建立新的值。</span><span class="sxs-lookup"><span data-stu-id="4b53a-323">Instead, after the mode is completed, the clustering algorithm creates new values for the `PredictOnly` attribute based on the clusters to which each case belongs.</span></span>  
  
 <span data-ttu-id="4b53a-324">下列查詢會為模型提供單一的新案例，其中與案例有關的唯一資訊是年齡和性別。</span><span class="sxs-lookup"><span data-stu-id="4b53a-324">The following query provides a single new case to the model, where the only information about the case is the age and gender.</span></span> <span data-ttu-id="4b53a-325">SELECT 陳述式指定您有興趣的可預測屬性/值配對，而 [PredictProbability &#40;DMX&#41;](/sql/dmx/predictprobability-dmx) 函數則告訴您具有這些屬性的案例擁有目標結果的機率。</span><span class="sxs-lookup"><span data-stu-id="4b53a-325">The SELECT statement specifies the predictable attribute/value pair that you are interested in, and the [PredictProbability &#40;DMX&#41;](/sql/dmx/predictprobability-dmx) function tells you the probability that a case with those attributes will have the targeted outcome.</span></span>  
  
```  
SELECT  
  [TM_Clustering].[Bike Buyer], PredictProbability([Bike Buyer],1)  
FROM  
  [TM_Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 40 AS [Age],  
  'F' AS [Gender]) AS t  
```  
  
 <span data-ttu-id="4b53a-326">當使用方式設定為 `Predict` 時的結果範例：</span><span class="sxs-lookup"><span data-stu-id="4b53a-326">Example of results when usage is set to `Predict`:</span></span>  
  
|<span data-ttu-id="4b53a-327">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="4b53a-327">Bike Buyer</span></span>|<span data-ttu-id="4b53a-328">運算是</span><span class="sxs-lookup"><span data-stu-id="4b53a-328">Expression</span></span>|  
|----------------|----------------|  
|<span data-ttu-id="4b53a-329">1</span><span class="sxs-lookup"><span data-stu-id="4b53a-329">1</span></span>|<span data-ttu-id="4b53a-330">0.592924735740338</span><span class="sxs-lookup"><span data-stu-id="4b53a-330">0.592924735740338</span></span>|  
  
 <span data-ttu-id="4b53a-331">當使用方式設定為 `PredictOnly` 並重新處理模型時的結果範例：</span><span class="sxs-lookup"><span data-stu-id="4b53a-331">Example of results when the usage is set to `PredictOnly` and the model is reprocessed:</span></span>  
  
|<span data-ttu-id="4b53a-332">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="4b53a-332">Bike Buyer</span></span>|<span data-ttu-id="4b53a-333">運算是</span><span class="sxs-lookup"><span data-stu-id="4b53a-333">Expression</span></span>|  
|----------------|----------------|  
|<span data-ttu-id="4b53a-334">1</span><span class="sxs-lookup"><span data-stu-id="4b53a-334">1</span></span>|<span data-ttu-id="4b53a-335">0.55843544003102</span><span class="sxs-lookup"><span data-stu-id="4b53a-335">0.55843544003102</span></span>|  
  
 <span data-ttu-id="4b53a-336">在此範例中，模型中的差異並不大。</span><span class="sxs-lookup"><span data-stu-id="4b53a-336">In this example, the difference in the model is not significant.</span></span> <span data-ttu-id="4b53a-337">不過，有時候偵測值的實際散發和模型所預測的情況之間的差異可能很重要。</span><span class="sxs-lookup"><span data-stu-id="4b53a-337">However, sometimes it can be important to detect differences between the actual distribution of values and what the model predicts.</span></span> <span data-ttu-id="4b53a-338">[PredictCaseLikelihood &#40;DMX&#41;](/sql/dmx/predictcaselikelihood-dmx) 函數在此案例中很有用，因為它會告訴您在模型已知時的案例可能性。</span><span class="sxs-lookup"><span data-stu-id="4b53a-338">The [PredictCaseLikelihood &#40;DMX&#41;](/sql/dmx/predictcaselikelihood-dmx) function is useful in this scenario, because it tells you how likely a case is, given the model.</span></span>  
  
 <span data-ttu-id="4b53a-339">PredictCaseLikelihood 函數傳回的數字是機率，因此一定會介於 0 和 1 之間，.5 的值則代表隨機結果。</span><span class="sxs-lookup"><span data-stu-id="4b53a-339">The number that is returned by the PredictCaseLikelihood function is a probability, and therefore is always between 0 and 1, with a value of .5 representing random outcome.</span></span> <span data-ttu-id="4b53a-340">因此，小於 .5 的分數代表預測的案例在模型已知時不太可能發生，而超過 .5 的分數則代表預測的案例較符合模型的預測。</span><span class="sxs-lookup"><span data-stu-id="4b53a-340">Therefore, a score less than .5 means that the predicted case is unlikely, given the model, and a score over.5 indicates that the predicted case is more likely than not to fit the model.</span></span>  
  
 <span data-ttu-id="4b53a-341">例如，下列查詢會傳回兩個代表新範例案例可能性的值。</span><span class="sxs-lookup"><span data-stu-id="4b53a-341">For example, the following query returns two values that characterize the likelihood of a new sample case.</span></span> <span data-ttu-id="4b53a-342">非正規化的值代表在目前模型已知時的機率。</span><span class="sxs-lookup"><span data-stu-id="4b53a-342">The non-normalized value represents the probability given the current model.</span></span> <span data-ttu-id="4b53a-343">當您使用 NORMALIZED 關鍵字時，由函數傳回的可能性分數會藉由將「使用模型的機率」除以「不使用模型的機率」來進行調整。</span><span class="sxs-lookup"><span data-stu-id="4b53a-343">When you use the NORMALIZED keyword, the likelihood score that is returned by the function is adjusted by dividing "probability with the model" by "probability without the model".</span></span>  
  
```  
SELECT  
PredictCaseLikelihood(NORMALIZED) AS [NormalizedValue], PredictCaseLikelihood(NONNORMALIZED) AS [NonNormalizedValue]  
FROM  
  [TM_Clustering_PredictOnly]  
NATURAL PREDICTION JOIN  
(SELECT 40 AS [Age],  
  'F' AS [Gender]) AS t  
```  
  
 <span data-ttu-id="4b53a-344">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="4b53a-344">Example results:</span></span>  
  
|<span data-ttu-id="4b53a-345">NormalizedValue</span><span class="sxs-lookup"><span data-stu-id="4b53a-345">NormalizedValue</span></span>|<span data-ttu-id="4b53a-346">NonNormalizedValue</span><span class="sxs-lookup"><span data-stu-id="4b53a-346">NonNormalizedValue</span></span>|  
|---------------------|------------------------|  
|<span data-ttu-id="4b53a-347">5.56438372679893E-11</span><span class="sxs-lookup"><span data-stu-id="4b53a-347">5.56438372679893E-11</span></span>|<span data-ttu-id="4b53a-348">8.65459953145182E-68</span><span class="sxs-lookup"><span data-stu-id="4b53a-348">8.65459953145182E-68</span></span>|  
  
 <span data-ttu-id="4b53a-349">請注意，這些結果中的數字會以科學記號標記法表示。</span><span class="sxs-lookup"><span data-stu-id="4b53a-349">Note that the numbers in these results are expressed in scientific notation.</span></span>  
  
 [<span data-ttu-id="4b53a-350">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4b53a-350">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-9-determining-cluster-membership"></a><a name="bkmk_Query9"></a> <span data-ttu-id="4b53a-351">範例查詢 9：判斷群集成員資格</span><span class="sxs-lookup"><span data-stu-id="4b53a-351">Sample Query 9: Determining Cluster Membership</span></span>  
 <span data-ttu-id="4b53a-352">此範例會使用 [叢集 &#40;DMX&#41;](/sql/dmx/cluster-dmx) 函數來傳回最可能包含新案例的叢集，並使用 [ClusterProbability &#40;DMX&#41;](/sql/dmx/clusterprobability-dmx) 函數來傳回該叢集中的成員資格機率。</span><span class="sxs-lookup"><span data-stu-id="4b53a-352">This example uses the [Cluster &#40;DMX&#41;](/sql/dmx/cluster-dmx) function to return the cluster to which the new case is most likely to belong, and uses the [ClusterProbability &#40;DMX&#41;](/sql/dmx/clusterprobability-dmx) function to return the probability for membership in that cluster.</span></span>  
  
```  
SELECT Cluster(), ClusterProbability()  
FROM  
  [TM_Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 40 AS [Age],  
  'F' AS [Gender],  
  'S' AS [Marital Status]) AS t  
```  
  
 <span data-ttu-id="4b53a-353">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="4b53a-353">Example results:</span></span>  
  
|<span data-ttu-id="4b53a-354">$CLUSTER</span><span class="sxs-lookup"><span data-stu-id="4b53a-354">$CLUSTER</span></span>|<span data-ttu-id="4b53a-355">運算是</span><span class="sxs-lookup"><span data-stu-id="4b53a-355">Expression</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="4b53a-356">群集 2</span><span class="sxs-lookup"><span data-stu-id="4b53a-356">Cluster 2</span></span>|<span data-ttu-id="4b53a-357">0.397918596951617</span><span class="sxs-lookup"><span data-stu-id="4b53a-357">0.397918596951617</span></span>|  
  
 <span data-ttu-id="4b53a-358">**注意**根據預設，函數會傳回 `ClusterProbability` 最可能叢集的機率。</span><span class="sxs-lookup"><span data-stu-id="4b53a-358">**Note** By default, the `ClusterProbability` function returns the probability of the most likely cluster.</span></span> <span data-ttu-id="4b53a-359">不過，您可以使用 `ClusterProbability('cluster name')`語法來指定不同的叢集。</span><span class="sxs-lookup"><span data-stu-id="4b53a-359">However, you can specify a different cluster by using the syntax `ClusterProbability('cluster name')`.</span></span> <span data-ttu-id="4b53a-360">如果要這麼做，請注意每個預測函數的結果都與其他結果無關。</span><span class="sxs-lookup"><span data-stu-id="4b53a-360">If you do this, be aware that the results from each prediction function are independent of the other results.</span></span> <span data-ttu-id="4b53a-361">因此，第二個資料行中的機率分數所參考的群集可以與命名於第一個資料行中的群集不同。</span><span class="sxs-lookup"><span data-stu-id="4b53a-361">Therefore, the probability score in the second column could refer to a different cluster than the cluster named in the first column.</span></span>  
  
 [<span data-ttu-id="4b53a-362">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4b53a-362">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-10-returning-all-possible-clusters-with-probability-and-distance"></a><a name="bkmk_Query10"></a> <span data-ttu-id="4b53a-363">範例查詢 10：使用機率和距離傳回所有可能的群集</span><span class="sxs-lookup"><span data-stu-id="4b53a-363">Sample Query 10: Returning All Possible Clusters with Probability and Distance</span></span>  
 <span data-ttu-id="4b53a-364">在以上範例中，機率分數並不很高。</span><span class="sxs-lookup"><span data-stu-id="4b53a-364">In the previous example, the probability score was not very high.</span></span> <span data-ttu-id="4b53a-365">若要判斷是否有更好的叢集，可以使用 [PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx) 函數搭配 [叢集 &#40;DMX&#41;](/sql/dmx/cluster-dmx) 函數來傳回包含所有可能叢集的巢狀資料表，並附上新案例屬於每個叢集的機率。</span><span class="sxs-lookup"><span data-stu-id="4b53a-365">To determine if there is a better cluster, you can use the [PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx) function together with the [Cluster &#40;DMX&#41;](/sql/dmx/cluster-dmx) function to return a nested table that includes all possible clusters, together with the probability that the new case that belongs to each cluster.</span></span> <span data-ttu-id="4b53a-366">FLATTENED 關鍵字可用來將階層式資料列集變更為二維資料表以方便檢視。</span><span class="sxs-lookup"><span data-stu-id="4b53a-366">The FLATTENED keyword is used to change the hierarchical rowset into a flat table for easier viewing.</span></span>  
  
```  
SELECT FLATTENED PredictHistogram(Cluster())  
From  
  [TM_Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 40 AS [Age],  
  'F' AS [Gender],  
  'S' AS [Marital Status])  
```  
  
|<span data-ttu-id="4b53a-367">Expression.$CLUSTER</span><span class="sxs-lookup"><span data-stu-id="4b53a-367">Expression.$CLUSTER</span></span>|<span data-ttu-id="4b53a-368">Expression.$DISTANCE</span><span class="sxs-lookup"><span data-stu-id="4b53a-368">Expression.$DISTANCE</span></span>|<span data-ttu-id="4b53a-369">Expression.$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="4b53a-369">Expression.$PROBABILITY</span></span>|  
|-------------------------|--------------------------|-----------------------------|  
|<span data-ttu-id="4b53a-370">群集 2</span><span class="sxs-lookup"><span data-stu-id="4b53a-370">Cluster 2</span></span>|<span data-ttu-id="4b53a-371">0.602081403048383</span><span class="sxs-lookup"><span data-stu-id="4b53a-371">0.602081403048383</span></span>|<span data-ttu-id="4b53a-372">0.397918596951617</span><span class="sxs-lookup"><span data-stu-id="4b53a-372">0.397918596951617</span></span>|  
|<span data-ttu-id="4b53a-373">叢集 10</span><span class="sxs-lookup"><span data-stu-id="4b53a-373">Cluster 10</span></span>|<span data-ttu-id="4b53a-374">0.719691686785675</span><span class="sxs-lookup"><span data-stu-id="4b53a-374">0.719691686785675</span></span>|<span data-ttu-id="4b53a-375">0.280308313214325</span><span class="sxs-lookup"><span data-stu-id="4b53a-375">0.280308313214325</span></span>|  
|<span data-ttu-id="4b53a-376">叢集 4</span><span class="sxs-lookup"><span data-stu-id="4b53a-376">Cluster 4</span></span>|<span data-ttu-id="4b53a-377">0.867772590378791</span><span class="sxs-lookup"><span data-stu-id="4b53a-377">0.867772590378791</span></span>|<span data-ttu-id="4b53a-378">0.132227409621209</span><span class="sxs-lookup"><span data-stu-id="4b53a-378">0.132227409621209</span></span>|  
|<span data-ttu-id="4b53a-379">叢集 5</span><span class="sxs-lookup"><span data-stu-id="4b53a-379">Cluster 5</span></span>|<span data-ttu-id="4b53a-380">0.931039872200985</span><span class="sxs-lookup"><span data-stu-id="4b53a-380">0.931039872200985</span></span>|<span data-ttu-id="4b53a-381">0.0689601277990149</span><span class="sxs-lookup"><span data-stu-id="4b53a-381">0.0689601277990149</span></span>|  
|<span data-ttu-id="4b53a-382">叢集 3</span><span class="sxs-lookup"><span data-stu-id="4b53a-382">Cluster 3</span></span>|<span data-ttu-id="4b53a-383">0.942359230072167</span><span class="sxs-lookup"><span data-stu-id="4b53a-383">0.942359230072167</span></span>|<span data-ttu-id="4b53a-384">0.0576407699278328</span><span class="sxs-lookup"><span data-stu-id="4b53a-384">0.0576407699278328</span></span>|  
|<span data-ttu-id="4b53a-385">叢集 6</span><span class="sxs-lookup"><span data-stu-id="4b53a-385">Cluster 6</span></span>|<span data-ttu-id="4b53a-386">0.958973668972756</span><span class="sxs-lookup"><span data-stu-id="4b53a-386">0.958973668972756</span></span>|<span data-ttu-id="4b53a-387">0.0410263310272437</span><span class="sxs-lookup"><span data-stu-id="4b53a-387">0.0410263310272437</span></span>|  
|<span data-ttu-id="4b53a-388">叢集 7</span><span class="sxs-lookup"><span data-stu-id="4b53a-388">Cluster 7</span></span>|<span data-ttu-id="4b53a-389">0.979081275926724</span><span class="sxs-lookup"><span data-stu-id="4b53a-389">0.979081275926724</span></span>|<span data-ttu-id="4b53a-390">0.0209187240732763</span><span class="sxs-lookup"><span data-stu-id="4b53a-390">0.0209187240732763</span></span>|  
|<span data-ttu-id="4b53a-391">叢集 1</span><span class="sxs-lookup"><span data-stu-id="4b53a-391">Cluster 1</span></span>|<span data-ttu-id="4b53a-392">0.999169044818624</span><span class="sxs-lookup"><span data-stu-id="4b53a-392">0.999169044818624</span></span>|<span data-ttu-id="4b53a-393">0.000830955181376364</span><span class="sxs-lookup"><span data-stu-id="4b53a-393">0.000830955181376364</span></span>|  
|<span data-ttu-id="4b53a-394">叢集 9</span><span class="sxs-lookup"><span data-stu-id="4b53a-394">Cluster 9</span></span>|<span data-ttu-id="4b53a-395">0.999831227795894</span><span class="sxs-lookup"><span data-stu-id="4b53a-395">0.999831227795894</span></span>|<span data-ttu-id="4b53a-396">0.000168772204105754</span><span class="sxs-lookup"><span data-stu-id="4b53a-396">0.000168772204105754</span></span>|  
|<span data-ttu-id="4b53a-397">叢集 8</span><span class="sxs-lookup"><span data-stu-id="4b53a-397">Cluster 8</span></span>|<span data-ttu-id="4b53a-398">1</span><span class="sxs-lookup"><span data-stu-id="4b53a-398">1</span></span>|<span data-ttu-id="4b53a-399">0</span><span class="sxs-lookup"><span data-stu-id="4b53a-399">0</span></span>|  
  
 <span data-ttu-id="4b53a-400">根據預設值，結果是依機率排序。</span><span class="sxs-lookup"><span data-stu-id="4b53a-400">By default, the results are ranked by probability.</span></span> <span data-ttu-id="4b53a-401">結果會告訴您，即使 Cluster 2 的機率相當低，Cluster 2 仍是新資料點的最適合項目。</span><span class="sxs-lookup"><span data-stu-id="4b53a-401">The results tell you that, even though the probability for Cluster 2 is fairly low, Cluster 2 is still the best fit for the new data point.</span></span>  
  
 <span data-ttu-id="4b53a-402">**注意** ：其他的資料行 `$DISTANCE`代表從資料點到叢集的距離。</span><span class="sxs-lookup"><span data-stu-id="4b53a-402">**Note** The additional column, `$DISTANCE`, represents the distance from the data point to the cluster.</span></span> <span data-ttu-id="4b53a-403">根據預設， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 群集演算法會使用可擴充的 EM 叢集，這種方法會將多個叢集指派給每個資料點，並排列可能叢集的次序。</span><span class="sxs-lookup"><span data-stu-id="4b53a-403">By default, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering Algorithm uses scalable EM clustering, which assigns multiple clusters to each data point and ranks the possible clusters.</span></span>  <span data-ttu-id="4b53a-404">不過，如果使用 K-means 演算法建立叢集模型，則只能將一個群集指派給每個資料點，且此查詢只會傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="4b53a-404">However, if you create your clustering model using the K-means algorithm, only one cluster can be assigned to each data point, and this query would return only one row.</span></span> <span data-ttu-id="4b53a-405">了解這些差異對於解譯 [PredictCaseLikelihood &#40;DMX&#41;](/sql/dmx/predictcaselikelihood-dmx) 函數來包含來自基礎結構的資料行。</span><span class="sxs-lookup"><span data-stu-id="4b53a-405">Understanding these differences is necessary to interpret the results of the [PredictCaseLikelihood &#40;DMX&#41;](/sql/dmx/predictcaselikelihood-dmx) function.</span></span> <span data-ttu-id="4b53a-406">如需 EM 和 K-means 叢集之間差異的詳細資訊，請參閱 [Microsoft 群集演算法技術參考](microsoft-clustering-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="4b53a-406">For more information about the differences between EM and K-means clustering, see [Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md).</span></span>  
  
 [<span data-ttu-id="4b53a-407">回到頁首</span><span class="sxs-lookup"><span data-stu-id="4b53a-407">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="function-list"></a><span data-ttu-id="4b53a-408">函數清單</span><span class="sxs-lookup"><span data-stu-id="4b53a-408">Function List</span></span>  
 <span data-ttu-id="4b53a-409">所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 演算法都支援一組常用的函數。</span><span class="sxs-lookup"><span data-stu-id="4b53a-409">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="4b53a-410">不過，使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 叢集演算法建立的模型支援下表中列出的其他函數。</span><span class="sxs-lookup"><span data-stu-id="4b53a-410">However, models that are built by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm support the additional functions that are listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4b53a-411">預測函數</span><span class="sxs-lookup"><span data-stu-id="4b53a-411">Prediction Function</span></span>|<span data-ttu-id="4b53a-412">使用量</span><span class="sxs-lookup"><span data-stu-id="4b53a-412">Usage</span></span>|  
|[<span data-ttu-id="4b53a-413">叢集 &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4b53a-413">Cluster &#40;DMX&#41;</span></span>](/sql/dmx/cluster-dmx)|<span data-ttu-id="4b53a-414">傳回最可能包含輸入案例的群集。</span><span class="sxs-lookup"><span data-stu-id="4b53a-414">Returns the cluster that is most likely to contain the input case.</span></span>|  
|[<span data-ttu-id="4b53a-415">ClusterDistance &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4b53a-415">ClusterDistance &#40;DMX&#41;</span></span>](/sql/dmx/clusterdistance-dmx)|<span data-ttu-id="4b53a-416">傳回輸入案例與指定之群集的距離；如果沒有指定任何群集，則會傳回輸入案例與最可能之群集的距離。</span><span class="sxs-lookup"><span data-stu-id="4b53a-416">Returns the distance of the input case from the specified cluster, or if no cluster is specified, the distance of the input case from the most likely cluster.</span></span><br /><br /> <span data-ttu-id="4b53a-417">傳回輸入案例屬於指定之群集的機率。</span><span class="sxs-lookup"><span data-stu-id="4b53a-417">Returns the probability that the input case belongs to the specified cluster.</span></span>|  
|[<span data-ttu-id="4b53a-418">ClusterProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4b53a-418">ClusterProbability &#40;DMX&#41;</span></span>](/sql/dmx/clusterprobability-dmx)|<span data-ttu-id="4b53a-419">傳回輸入案例屬於指定之群集的機率。</span><span class="sxs-lookup"><span data-stu-id="4b53a-419">Returns the probability that the input case belongs to the specified cluster.</span></span>|  
|[<span data-ttu-id="4b53a-420">IsDescendant &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4b53a-420">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="4b53a-421">確定某個節點是否為模型中另一個節點的子系。</span><span class="sxs-lookup"><span data-stu-id="4b53a-421">Determines whether one node is a child of another node in the model.</span></span>|  
|[<span data-ttu-id="4b53a-422">IsInNode &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4b53a-422">IsInNode &#40;DMX&#41;</span></span>](/sql/dmx/isinnode-dmx)|<span data-ttu-id="4b53a-423">指示指定的節點是否包含目前案例。</span><span class="sxs-lookup"><span data-stu-id="4b53a-423">Indicates whether the specified node contains the current case.</span></span>|  
|[<span data-ttu-id="4b53a-424">PredictAdjustedProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4b53a-424">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="4b53a-425">傳回加權機率。</span><span class="sxs-lookup"><span data-stu-id="4b53a-425">Returns the weighted probability.</span></span>|  
|[<span data-ttu-id="4b53a-426">PredictAssociation &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4b53a-426">PredictAssociation &#40;DMX&#41;</span></span>](/sql/dmx/predictassociation-dmx)|<span data-ttu-id="4b53a-427">預測關聯資料集的成員資格。</span><span class="sxs-lookup"><span data-stu-id="4b53a-427">Predicts membership in an associative dataset.</span></span>|  
|[<span data-ttu-id="4b53a-428">PredictCaseLikelihood &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4b53a-428">PredictCaseLikelihood &#40;DMX&#41;</span></span>](/sql/dmx/predictcaselikelihood-dmx)|<span data-ttu-id="4b53a-429">傳回輸入案例符合現有模型的可能性。</span><span class="sxs-lookup"><span data-stu-id="4b53a-429">Returns the likelihood that an input case will fit in the existing model.</span></span>|  
|[<span data-ttu-id="4b53a-430">PredictHistogram &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4b53a-430">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="4b53a-431">傳回與目前預測值相關之值的資料表。</span><span class="sxs-lookup"><span data-stu-id="4b53a-431">Returns a table of values related to the current predicted value.</span></span>|  
|[<span data-ttu-id="4b53a-432">PredictNodeId &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4b53a-432">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="4b53a-433">傳回每個案例的 Node_ID。</span><span class="sxs-lookup"><span data-stu-id="4b53a-433">Returns the Node_ID for each case.</span></span>|  
|[<span data-ttu-id="4b53a-434">PredictProbability &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4b53a-434">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="4b53a-435">傳回預測值的機率。</span><span class="sxs-lookup"><span data-stu-id="4b53a-435">Returns probability for the predicted value.</span></span>|  
|[<span data-ttu-id="4b53a-436">PredictStdev &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4b53a-436">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="4b53a-437">傳回指定之資料行的預測標準差。</span><span class="sxs-lookup"><span data-stu-id="4b53a-437">Returns the predicted standard deviation for the specified column.</span></span>|  
|[<span data-ttu-id="4b53a-438">PredictSupport &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4b53a-438">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="4b53a-439">傳回指定狀態的支援值。</span><span class="sxs-lookup"><span data-stu-id="4b53a-439">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="4b53a-440">PredictVariance &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="4b53a-440">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="4b53a-441">傳回指定之資料行的變異數。</span><span class="sxs-lookup"><span data-stu-id="4b53a-441">Returns the variance of a specified column.</span></span>|  
  
 <span data-ttu-id="4b53a-442">如需特定函數的語法，請參閱[資料採礦延伸模組 &#40;DMX&#41; 函數參考](/sql/dmx/data-mining-extensions-dmx-function-reference)。</span><span class="sxs-lookup"><span data-stu-id="4b53a-442">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b53a-443">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b53a-443">See Also</span></span>  
 <span data-ttu-id="4b53a-444">[資料採礦查詢](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="4b53a-444">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="4b53a-445">[Microsoft 群集演算法技術參考](microsoft-clustering-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="4b53a-445">[Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="4b53a-446">Microsoft 群集演算法</span><span class="sxs-lookup"><span data-stu-id="4b53a-446">Microsoft Clustering Algorithm</span></span>](microsoft-clustering-algorithm.md)  
  
  
