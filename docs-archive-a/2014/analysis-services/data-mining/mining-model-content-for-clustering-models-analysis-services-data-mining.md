---
title: 群集模型的模型內容 (Analysis Services 資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- nearest neighbor [Data Mining]
- clustering [Data Mining]
- mining model content, clustering models
- clustering algorithms [Analysis Services]
ms.assetid: aed1b7d3-8f20-4eeb-b156-0229f942cefd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 400575d5c6ce8094b67500d15a86137302282fa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594838"
---
# <a name="mining-model-content-for-clustering-models-analysis-services---data-mining"></a><span data-ttu-id="a8536-102">叢集模型的採礦模型內容 (Analysis Services - 資料採礦)</span><span class="sxs-lookup"><span data-stu-id="a8536-102">Mining Model Content for Clustering Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="a8536-103">本主題說明使用 Microsoft 叢集演算法的模型專用的採礦模型內容。</span><span class="sxs-lookup"><span data-stu-id="a8536-103">This topic describes mining model content that is specific to models that use the Microsoft Clustering algorithm.</span></span> <span data-ttu-id="a8536-104">如需適用於所有模型類型的一般採礦模型內容說明，請參閱 [採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a8536-104">For a general explanation of mining model content for all model types, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-a-clustering-model"></a><span data-ttu-id="a8536-105">了解叢集模型的結構</span><span class="sxs-lookup"><span data-stu-id="a8536-105">Understanding the Structure of a Clustering Model</span></span>  
 <span data-ttu-id="a8536-106">叢集模型有簡單的結構。</span><span class="sxs-lookup"><span data-stu-id="a8536-106">A clustering model has a simple structure.</span></span> <span data-ttu-id="a8536-107">每個模型都擁有代表模型及其中繼資料的單一父節點，而每個父節點則擁有群集的一般清單 (NODE_TYPE = 5)。</span><span class="sxs-lookup"><span data-stu-id="a8536-107">Each model has a single parent node that represents the model and its metadata, and each parent node has a flat list of clusters (NODE_TYPE = 5).</span></span> <span data-ttu-id="a8536-108">下列影像顯示這個組織。</span><span class="sxs-lookup"><span data-stu-id="a8536-108">This organization is shown in the following image.</span></span>  
  
 <span data-ttu-id="a8536-109">![群集的模型內容結構](../media/modelcontentstructure-clust.gif "群集的模型內容結構")</span><span class="sxs-lookup"><span data-stu-id="a8536-109">![structure of model content for clustering](../media/modelcontentstructure-clust.gif "structure of model content for clustering")</span></span>  
  
 <span data-ttu-id="a8536-110">每個子節點都代表單一群集，且包含有關該群集之案例屬性的詳細統計資料。</span><span class="sxs-lookup"><span data-stu-id="a8536-110">Each child node represents a single cluster and contains detailed statistics about the attributes of the cases in that cluster.</span></span> <span data-ttu-id="a8536-111">這包含群集中的案例計數，以及區分此群集與其他群集的值散發。</span><span class="sxs-lookup"><span data-stu-id="a8536-111">This includes a count of the number of cases in the cluster, and the distribution of values that distinguish the cluster from other clusters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8536-112">您不需反覆運算節點來取得群集的計數或描述；模型的父節點也會計算及列出群集。</span><span class="sxs-lookup"><span data-stu-id="a8536-112">You do not need to iterate through the nodes to get a count or description of the clusters; the model parent node also counts and lists the clusters.</span></span>  
  
 <span data-ttu-id="a8536-113">父節點包含有用的統計資料，可描述所有培訓案例的實際散發。</span><span class="sxs-lookup"><span data-stu-id="a8536-113">The parent node contains useful statistics that describe the actual distribution of all the training cases.</span></span> <span data-ttu-id="a8536-114">這些統計資料可在巢狀資料表資料行 NODE_DISTRIBUTION 中找到。</span><span class="sxs-lookup"><span data-stu-id="a8536-114">These statistics are found in the nested table column, NODE_DISTRIBUTION.</span></span> <span data-ttu-id="a8536-115">例如，下表顯示 NODE_DISTRIBUTION 資料表的數個資料列，描述叢集模型 `TM_Clustering`(您在 [資料採礦基本教學課程](../../tutorials/basic-data-mining-tutorial.md)中建立) 的客戶人口統計分佈：</span><span class="sxs-lookup"><span data-stu-id="a8536-115">For example, the following table shows several rows from the NODE_DISTRIBUTION table that describe the distribution of customer demographics for the clustering model, `TM_Clustering`, that you create in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md):</span></span>  
  
|<span data-ttu-id="a8536-116">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8536-116">ATTRIBUTE_NAME</span></span>|<span data-ttu-id="a8536-117">ATRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="a8536-117">ATRIBUTE_VALUE</span></span>|<span data-ttu-id="a8536-118">SUPPORT</span><span class="sxs-lookup"><span data-stu-id="a8536-118">SUPPORT</span></span>|<span data-ttu-id="a8536-119">PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="a8536-119">PROBABILITY</span></span>|<span data-ttu-id="a8536-120">variance</span><span class="sxs-lookup"><span data-stu-id="a8536-120">VARIANCE</span></span>|<span data-ttu-id="a8536-121">VALUE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a8536-121">VALUE_TYPE</span></span>|  
|---------------------|---------------------|-------------|-----------------|--------------|-----------------|  
|<span data-ttu-id="a8536-122">年齡</span><span class="sxs-lookup"><span data-stu-id="a8536-122">Age</span></span>|<span data-ttu-id="a8536-123">Missing</span><span class="sxs-lookup"><span data-stu-id="a8536-123">Missing</span></span>|<span data-ttu-id="a8536-124">0</span><span class="sxs-lookup"><span data-stu-id="a8536-124">0</span></span>|<span data-ttu-id="a8536-125">0</span><span class="sxs-lookup"><span data-stu-id="a8536-125">0</span></span>|<span data-ttu-id="a8536-126">0</span><span class="sxs-lookup"><span data-stu-id="a8536-126">0</span></span>|<span data-ttu-id="a8536-127">1 (遺漏)</span><span class="sxs-lookup"><span data-stu-id="a8536-127">1 (Missing)</span></span>|  
|<span data-ttu-id="a8536-128">年齡</span><span class="sxs-lookup"><span data-stu-id="a8536-128">Age</span></span>|<span data-ttu-id="a8536-129">44.9016152716593</span><span class="sxs-lookup"><span data-stu-id="a8536-129">44.9016152716593</span></span>|<span data-ttu-id="a8536-130">12939</span><span class="sxs-lookup"><span data-stu-id="a8536-130">12939</span></span>|<span data-ttu-id="a8536-131">1</span><span class="sxs-lookup"><span data-stu-id="a8536-131">1</span></span>|<span data-ttu-id="a8536-132">125.663453102554</span><span class="sxs-lookup"><span data-stu-id="a8536-132">125.663453102554</span></span>|<span data-ttu-id="a8536-133">3 (連續)</span><span class="sxs-lookup"><span data-stu-id="a8536-133">3 (Continuous)</span></span>|  
|<span data-ttu-id="a8536-134">性別</span><span class="sxs-lookup"><span data-stu-id="a8536-134">Gender</span></span>|<span data-ttu-id="a8536-135">Missing</span><span class="sxs-lookup"><span data-stu-id="a8536-135">Missing</span></span>|<span data-ttu-id="a8536-136">0</span><span class="sxs-lookup"><span data-stu-id="a8536-136">0</span></span>|<span data-ttu-id="a8536-137">0</span><span class="sxs-lookup"><span data-stu-id="a8536-137">0</span></span>|<span data-ttu-id="a8536-138">0</span><span class="sxs-lookup"><span data-stu-id="a8536-138">0</span></span>|<span data-ttu-id="a8536-139">1 (遺漏)</span><span class="sxs-lookup"><span data-stu-id="a8536-139">1 (Missing)</span></span>|  
|<span data-ttu-id="a8536-140">性別</span><span class="sxs-lookup"><span data-stu-id="a8536-140">Gender</span></span>|<span data-ttu-id="a8536-141">F</span><span class="sxs-lookup"><span data-stu-id="a8536-141">F</span></span>|<span data-ttu-id="a8536-142">6350</span><span class="sxs-lookup"><span data-stu-id="a8536-142">6350</span></span>|<span data-ttu-id="a8536-143">0.490764355823479</span><span class="sxs-lookup"><span data-stu-id="a8536-143">0.490764355823479</span></span>|<span data-ttu-id="a8536-144">0</span><span class="sxs-lookup"><span data-stu-id="a8536-144">0</span></span>|<span data-ttu-id="a8536-145">4 (離散)</span><span class="sxs-lookup"><span data-stu-id="a8536-145">4 (Discrete)</span></span>|  
|<span data-ttu-id="a8536-146">性別</span><span class="sxs-lookup"><span data-stu-id="a8536-146">Gender</span></span>|<span data-ttu-id="a8536-147">M</span><span class="sxs-lookup"><span data-stu-id="a8536-147">M</span></span>|<span data-ttu-id="a8536-148">6589</span><span class="sxs-lookup"><span data-stu-id="a8536-148">6589</span></span>|<span data-ttu-id="a8536-149">0.509235644176521</span><span class="sxs-lookup"><span data-stu-id="a8536-149">0.509235644176521</span></span>|<span data-ttu-id="a8536-150">0</span><span class="sxs-lookup"><span data-stu-id="a8536-150">0</span></span>|<span data-ttu-id="a8536-151">4 (離散)</span><span class="sxs-lookup"><span data-stu-id="a8536-151">4 (Discrete)</span></span>|  
  
 <span data-ttu-id="a8536-152">從這些結果可以看到建置模型時使用了 12939 個案例、男女比率約為 50-50，平均年齡則為 44。</span><span class="sxs-lookup"><span data-stu-id="a8536-152">From these results, you can see that there were 12939 cases used to build the model, that the ratio of males to females was about 50-50, and that the mean age was 44.</span></span> <span data-ttu-id="a8536-153">描述性統計資料是根據報告的屬性是否為連續的數值資料類型 (例如 age) 或離散值類型 (例如 gender) 而定。</span><span class="sxs-lookup"><span data-stu-id="a8536-153">The descriptive statistics vary depending on whether the attribute being reported is a continuous numeric data type, such as age, or a discrete value type, such as gender.</span></span> <span data-ttu-id="a8536-154">連續資料類型會計算統計量值「平均值」\*\* 和「變異數」**，離散資料類型則會計算「機率」** 和「支援」\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8536-154">The statistical measures *mean* and *variance* are computed for continuous data types, whereas *probability* and *support* are computed for discrete data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8536-155">變異數代表叢集的總變異數。</span><span class="sxs-lookup"><span data-stu-id="a8536-155">The variance represents the total variance for the cluster.</span></span> <span data-ttu-id="a8536-156">當變異數的值很小時，代表資料行中大多數的值都相當接近平均值。</span><span class="sxs-lookup"><span data-stu-id="a8536-156">When the value for variance is small, it indicates that most values in the column were fairly close to the mean.</span></span> <span data-ttu-id="a8536-157">若要取得標準差，請計算變異數的平方根。</span><span class="sxs-lookup"><span data-stu-id="a8536-157">To obtain the standard deviation, calculate the square root of the variance.</span></span>  
  
 <span data-ttu-id="a8536-158">請注意，每個屬性都有一個 `Missing` 值類型，告訴您該屬性有多少沒有資料的案例。</span><span class="sxs-lookup"><span data-stu-id="a8536-158">Note that for each of the attributes there is a `Missing` value type that tells you how many cases had no data for that attribute.</span></span> <span data-ttu-id="a8536-159">遺漏的資料可能很多，而且視資料類型而會對計算造成不同的影響。</span><span class="sxs-lookup"><span data-stu-id="a8536-159">Missing data can be significant and affects calculations in different ways, depending on the data type.</span></span> <span data-ttu-id="a8536-160">如需詳細資訊，請參閱 [遺漏值 &#40;Analysis Services - 資料採礦&#41;](missing-values-analysis-services-data-mining.md)預先定義的模型旗標外，協力廠商外掛程式也可能擁有其他的模型旗標。</span><span class="sxs-lookup"><span data-stu-id="a8536-160">For more information, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
## <a name="model-content-for-a-clustering-model"></a><span data-ttu-id="a8536-161">叢集模型的模型內容</span><span class="sxs-lookup"><span data-stu-id="a8536-161">Model Content for a Clustering Model</span></span>  
 <span data-ttu-id="a8536-162">本章節僅針對採礦模型內容中與叢集模型相關的資料行，提供詳細資料和範例。</span><span class="sxs-lookup"><span data-stu-id="a8536-162">This section provides detail and examples only for those columns in the mining model content that are relevant for clustering models.</span></span>  
  
 <span data-ttu-id="a8536-163">如需結構描述資料列集 (例如，MODEL_CATALOG 和 MODEL_NAME) 中之一般用途資料行的詳細資訊，請參閱 [採礦模型內容 &amp;#40;Analysis Services - 資料採礦&amp;#41;](mining-model-content-analysis-services-data-mining.md)(採礦模型內容 &#40;Analysis Services - 資料採礦&#41;)。</span><span class="sxs-lookup"><span data-stu-id="a8536-163">For information about the general-purpose columns in the schema rowset, such as MODEL_CATALOG and MODEL_NAME, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="a8536-164">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a8536-164">MODEL_CATALOG</span></span>  
 <span data-ttu-id="a8536-165">模型儲存位置所在資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="a8536-165">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="a8536-166">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="a8536-166">MODEL_NAME</span></span>  
 <span data-ttu-id="a8536-167">模型的名稱。</span><span class="sxs-lookup"><span data-stu-id="a8536-167">Name of the model.</span></span>  
  
 <span data-ttu-id="a8536-168">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8536-168">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="a8536-169">在叢集模型中永遠為空白，因為模式中沒有可預測的屬性。</span><span class="sxs-lookup"><span data-stu-id="a8536-169">Always blank in clustering models because there is no predictable attribute in the mode.</span></span>  
  
 <span data-ttu-id="a8536-170">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8536-170">NODE_NAME</span></span>  
 <span data-ttu-id="a8536-171">永遠與 NODE_UNIQUE_NAME 相同。</span><span class="sxs-lookup"><span data-stu-id="a8536-171">Always same as NODE_UNIQUE_NAME.</span></span>  
  
 <span data-ttu-id="a8536-172">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8536-172">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="a8536-173">節點在模型內的唯一識別項。</span><span class="sxs-lookup"><span data-stu-id="a8536-173">A unique identifier for the node within the model.</span></span> <span data-ttu-id="a8536-174">這項值不能被改變。</span><span class="sxs-lookup"><span data-stu-id="a8536-174">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="a8536-175">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a8536-175">NODE_TYPE</span></span>  
 <span data-ttu-id="a8536-176">叢集模型會輸出下列節點類型：</span><span class="sxs-lookup"><span data-stu-id="a8536-176">A clustering model outputs the following node types:</span></span>  
  
|<span data-ttu-id="a8536-177">節點識別碼和名稱</span><span class="sxs-lookup"><span data-stu-id="a8536-177">Node ID and Name</span></span>|<span data-ttu-id="a8536-178">描述</span><span class="sxs-lookup"><span data-stu-id="a8536-178">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="a8536-179">1 (模型)</span><span class="sxs-lookup"><span data-stu-id="a8536-179">1 (Model)</span></span>|<span data-ttu-id="a8536-180">模型的根節點。</span><span class="sxs-lookup"><span data-stu-id="a8536-180">Root node for model.</span></span>|  
|<span data-ttu-id="a8536-181">5 (群集)</span><span class="sxs-lookup"><span data-stu-id="a8536-181">5 (Cluster)</span></span>|<span data-ttu-id="a8536-182">包含群集中的案例計數、群集中的案例特性以及描述群集值的統計資料。</span><span class="sxs-lookup"><span data-stu-id="a8536-182">Contains a count of cases in the cluster, the characteristics of cases in the cluster, and statistics that describe the values in the cluster.</span></span>|  
  
 <span data-ttu-id="a8536-183">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="a8536-183">NODE_CAPTION</span></span>  
 <span data-ttu-id="a8536-184">提供顯示用途的好記名稱。</span><span class="sxs-lookup"><span data-stu-id="a8536-184">A friendly name for display purposes.</span></span> <span data-ttu-id="a8536-185">在建立模型時，NODE_UNIQUE_NAME 的值會自動用來當做標題。</span><span class="sxs-lookup"><span data-stu-id="a8536-185">When you create a model, the value of NODE_UNIQUE_NAME is automatically used as the caption.</span></span> <span data-ttu-id="a8536-186">不過，您可以用程式設計的方式或使用檢視器來變更 NODE_CAPTION 的值，以更新群集的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="a8536-186">However, you can change the value for NODE_CAPTION to update the display name for the cluster, either programmatically or by using the viewer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8536-187">在重新處理模型時，所有的名稱變更都會由新值所覆寫。</span><span class="sxs-lookup"><span data-stu-id="a8536-187">When you reprocess the model, all name changes will be overwritten by the new values.</span></span> <span data-ttu-id="a8536-188">您不能在模型中保存名稱，或者在不同版本的模型之間追蹤群集成員資格的變更。</span><span class="sxs-lookup"><span data-stu-id="a8536-188">You cannot persist names in the model, or track changes in cluster membership between different versions of a model.</span></span>  
  
 <span data-ttu-id="a8536-189">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="a8536-189">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="a8536-190">節點所擁有子系數目的估計。</span><span class="sxs-lookup"><span data-stu-id="a8536-190">An estimate of the number of children that the node has.</span></span>  
  
 <span data-ttu-id="a8536-191">**父節點** ：指出模型中的叢集數。</span><span class="sxs-lookup"><span data-stu-id="a8536-191">**Parent node** Indicates the number of clusters in the model.</span></span>  
  
 <span data-ttu-id="a8536-192">**分葉節點** ：永遠為 0。</span><span class="sxs-lookup"><span data-stu-id="a8536-192">**Cluster nodes** Always 0.</span></span>  
  
 <span data-ttu-id="a8536-193">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="a8536-193">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="a8536-194">節點之父系的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="a8536-194">The unique name of the node's parent.</span></span>  
  
 <span data-ttu-id="a8536-195">**父節點** ：永遠為 NULL</span><span class="sxs-lookup"><span data-stu-id="a8536-195">**Parent node** Always NULL</span></span>  
  
 <span data-ttu-id="a8536-196">**叢集節點** ：通常為 000。</span><span class="sxs-lookup"><span data-stu-id="a8536-196">**Cluster nodes** Usually 000.</span></span>  
  
 <span data-ttu-id="a8536-197">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a8536-197">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="a8536-198">節點的描述。</span><span class="sxs-lookup"><span data-stu-id="a8536-198">A description of the node.</span></span>  
  
 <span data-ttu-id="a8536-199">**父節點** ：永遠為 **(All)**。</span><span class="sxs-lookup"><span data-stu-id="a8536-199">**Parent node** Always **(All)**.</span></span>  
  
 <span data-ttu-id="a8536-200">**叢集節點** ：將叢集與其他叢集加以區分之主要屬性的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="a8536-200">**Cluster nodes** A comma-separated list of the primary attributes that distinguish the cluster from other clusters.</span></span>  
  
 <span data-ttu-id="a8536-201">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="a8536-201">NODE_RULE</span></span>  
 <span data-ttu-id="a8536-202">不用於叢集模型。</span><span class="sxs-lookup"><span data-stu-id="a8536-202">Not used for clustering models.</span></span>  
  
 <span data-ttu-id="a8536-203">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="a8536-203">MARGINAL_RULE</span></span>  
 <span data-ttu-id="a8536-204">不用於叢集模型。</span><span class="sxs-lookup"><span data-stu-id="a8536-204">Not used for clustering models.</span></span>  
  
 <span data-ttu-id="a8536-205">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="a8536-205">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="a8536-206">與此節點關聯的機率。</span><span class="sxs-lookup"><span data-stu-id="a8536-206">The probability associated with this node.</span></span> <span data-ttu-id="a8536-207">**父節點** ：永遠為 1。</span><span class="sxs-lookup"><span data-stu-id="a8536-207">**Parent node** Always 1.</span></span>  
  
 <span data-ttu-id="a8536-208">**叢集節點** ：機率代表屬性的複合機率，且依用來建立叢集模型的演算法不同而有一些調整。</span><span class="sxs-lookup"><span data-stu-id="a8536-208">**Cluster nodes** The probability represents the compound probability of the attributes, with some adjustments depending on the algorithm used to create the clustering model.</span></span>  
  
 <span data-ttu-id="a8536-209">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="a8536-209">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="a8536-210">從父節點到達節點的機率。</span><span class="sxs-lookup"><span data-stu-id="a8536-210">The probability of reaching the node from the parent node.</span></span> <span data-ttu-id="a8536-211">在叢集模型中，臨界機率永遠與節點機率相同。</span><span class="sxs-lookup"><span data-stu-id="a8536-211">In a clustering model, the marginal probability is always the same as the node probability.</span></span>  
  
 <span data-ttu-id="a8536-212">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="a8536-212">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="a8536-213">包含節點之機率長條圖的資料表。</span><span class="sxs-lookup"><span data-stu-id="a8536-213">A table that contains the probability histogram of the node.</span></span>  
  
 <span data-ttu-id="a8536-214">**父節點** ：請參閱本主題的簡介。</span><span class="sxs-lookup"><span data-stu-id="a8536-214">**Parent node** See the Introduction to this topic.</span></span>  
  
 <span data-ttu-id="a8536-215">**叢集節點** ：代表此叢集所含案例的屬性及值的分佈。</span><span class="sxs-lookup"><span data-stu-id="a8536-215">**Cluster nodes** Represents the distribution of attributes and values for cases that are included in this cluster.</span></span>  
  
 <span data-ttu-id="a8536-216">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="a8536-216">NODE_SUPPORT</span></span>  
 <span data-ttu-id="a8536-217">支援這個節點的案例數目。</span><span class="sxs-lookup"><span data-stu-id="a8536-217">The number of cases that support this node.</span></span> <span data-ttu-id="a8536-218">**父節點** ：指出整個模型的定型案例數目。</span><span class="sxs-lookup"><span data-stu-id="a8536-218">**Parent node** Indicates the number of training cases for the entire model.</span></span>  
  
 <span data-ttu-id="a8536-219">**叢集節點** ：以案例數指出叢集大小。</span><span class="sxs-lookup"><span data-stu-id="a8536-219">**Cluster nodes** Indicates the size of the cluster as a number of cases.</span></span>  
  
 <span data-ttu-id="a8536-220">**注意** ：如果模型使用 K-Means 叢集，則每個案例都可以僅屬於一個叢集。</span><span class="sxs-lookup"><span data-stu-id="a8536-220">**Note** If the model uses K-Means clustering, each case can belong to only one cluster.</span></span> <span data-ttu-id="a8536-221">不過，如果模型使用 EM 群集，則每個案例都可以屬於不同的群集，且會針對案例所屬的每個群集為該案例指派一個加權距離。</span><span class="sxs-lookup"><span data-stu-id="a8536-221">However, if the model uses EM clustering, each case can belong to different cluster, and the case is assigned a weighted distance for each cluster to which it belongs.</span></span> <span data-ttu-id="a8536-222">因此，對於 EM 模型而言，個別群集的支援總和會大於整體模型的支援。</span><span class="sxs-lookup"><span data-stu-id="a8536-222">Therefore, for EM models the sum of support for an individual cluster is greater than support for the overall model.</span></span>  
  
 <span data-ttu-id="a8536-223">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="a8536-223">MSOLAP_MODEL_COLUMN</span></span>  
 <span data-ttu-id="a8536-224">不用於叢集模型。</span><span class="sxs-lookup"><span data-stu-id="a8536-224">Not used for clustering models.</span></span>  
  
 <span data-ttu-id="a8536-225">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="a8536-225">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="a8536-226">顯示與節點相關聯的分數。</span><span class="sxs-lookup"><span data-stu-id="a8536-226">Displays a score associated with the node.</span></span>  
  
 <span data-ttu-id="a8536-227">**父節點** ：叢集模型的 Bayesian Information Criterion (BIC) 分數。</span><span class="sxs-lookup"><span data-stu-id="a8536-227">**Parent node** The Bayesian Information Criterion (BIC) score for the clustering model.</span></span>  
  
 <span data-ttu-id="a8536-228">**分葉節點** ：永遠為 0。</span><span class="sxs-lookup"><span data-stu-id="a8536-228">**Cluster nodes** Always 0.</span></span>  
  
 <span data-ttu-id="a8536-229">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="a8536-229">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="a8536-230">主要用於顯示用途。</span><span class="sxs-lookup"><span data-stu-id="a8536-230">A label used for display purposes.</span></span> <span data-ttu-id="a8536-231">您無法變更此標題。</span><span class="sxs-lookup"><span data-stu-id="a8536-231">You cannot change this caption.</span></span>  
  
 <span data-ttu-id="a8536-232">**父節點** ：模型的類型：叢集模型</span><span class="sxs-lookup"><span data-stu-id="a8536-232">**Parent node** The type of model: Cluster model</span></span>  
  
 <span data-ttu-id="a8536-233">**叢集節點** ：叢集的名稱。</span><span class="sxs-lookup"><span data-stu-id="a8536-233">**Cluster nodes** The name of the cluster.</span></span> <span data-ttu-id="a8536-234">範例：群集 1。</span><span class="sxs-lookup"><span data-stu-id="a8536-234">Example: Cluster 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8536-235">備註</span><span class="sxs-lookup"><span data-stu-id="a8536-235">Remarks</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="a8536-236">提供多種建立叢集模型的方法。</span><span class="sxs-lookup"><span data-stu-id="a8536-236">provides multiple methods for creating a clustering model.</span></span> <span data-ttu-id="a8536-237">如果您不知道所使用的模型是用什麼方法建立的，可以用程式設計的方式、使用 ADOMD 用戶端或 AMO 或者查詢資料採礦結構描述的資料列集，來擷取模型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a8536-237">If you do not know which method was used to create the model that you are working with, you can retrieve the model metadata programmatically, by using an ADOMD client or AMO, or by querying the data mining schema rowset.</span></span> <span data-ttu-id="a8536-238">如需詳細資訊，請參閱 [查詢用於建立採礦模型的參數](query-the-parameters-used-to-create-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="a8536-238">For more information, see [Query the Parameters Used to Create a Mining Model](query-the-parameters-used-to-create-a-mining-model.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8536-239">不論您使用的叢集方法或參數為何，模型的結構和內容都會保持相同。</span><span class="sxs-lookup"><span data-stu-id="a8536-239">The structure and content of the model stay the same, regardless of which clustering method or parameters you use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8536-240">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8536-240">See Also</span></span>  
 <span data-ttu-id="a8536-241">[&#40;Analysis Services 的採礦模型內容-資料採礦&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="a8536-241">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="a8536-242">[資料採礦模型檢視器](data-mining-model-viewers.md) </span><span class="sxs-lookup"><span data-stu-id="a8536-242">[Data Mining Model Viewers](data-mining-model-viewers.md) </span></span>  
 <span data-ttu-id="a8536-243">[Microsoft 群集演算法](microsoft-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="a8536-243">[Microsoft Clustering Algorithm](microsoft-clustering-algorithm.md) </span></span>  
 [<span data-ttu-id="a8536-244">資料採礦查詢</span><span class="sxs-lookup"><span data-stu-id="a8536-244">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
