---
title: Microsoft 群集演算法技術參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clustering [Data Mining]
- MAXIMUM_INPUT_ATTRIBUTES parameter
- CLUSTER_SEED parameter
- MODELLING_CARDINALITY parameter
- MINIMUM_SUPPORT parameter
- STOPPING_TOLERANCE parameter
- MAXIMUM_STATES parameter
- SAMPLE_SIZE parameter
- CLUSTERING_METHOD parameter
- soft clustering [Data Mining]
- clustering algorithms [Analysis Services]
- CLUSTER_COUNT parameter
ms.assetid: ec40868a-6dc7-4dfa-aadc-dedf69e555eb
author: minewiskan
ms.author: owend
ms.openlocfilehash: ee9019f821c5608527e0bdca5eddc8f1ead52f41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597451"
---
# <a name="microsoft-clustering-algorithm-technical-reference"></a><span data-ttu-id="e6c09-102">Microsoft 群集演算法技術參考</span><span class="sxs-lookup"><span data-stu-id="e6c09-102">Microsoft Clustering Algorithm Technical Reference</span></span>
  <span data-ttu-id="e6c09-103">本節說明 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 叢集演算法的實作，包括可用來控制群集模型行為的參數。</span><span class="sxs-lookup"><span data-stu-id="e6c09-103">This section explains the implementation of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm, including the parameters that you can use to control the behavior of clustering models.</span></span> <span data-ttu-id="e6c09-104">本章節也提供在建立及處理叢集模型時如何改善效能的指南。</span><span class="sxs-lookup"><span data-stu-id="e6c09-104">It also provides guidance about how to improve performance when you create and process clustering models.</span></span>  
  
 <span data-ttu-id="e6c09-105">如需有關如何使用叢集模型的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="e6c09-105">For additional information about how to use clustering models, see the following topics:</span></span>  
  
-   [<span data-ttu-id="e6c09-106">叢集模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="e6c09-106">Mining Model Content for Clustering Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-clustering-models-analysis-services-data-mining.md)  
  
-   [<span data-ttu-id="e6c09-107">叢集模型查詢範例</span><span class="sxs-lookup"><span data-stu-id="e6c09-107">Clustering Model Query Examples</span></span>](clustering-model-query-examples.md)  
  
## <a name="implementation-of-the-microsoft-clustering-algorithm"></a><span data-ttu-id="e6c09-108">Microsoft 群集演算法的實作</span><span class="sxs-lookup"><span data-stu-id="e6c09-108">Implementation of the Microsoft Clustering Algorithm</span></span>  
 <span data-ttu-id="e6c09-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 群集演算法提供兩種方法來建立群集並將資料點指派給群集。</span><span class="sxs-lookup"><span data-stu-id="e6c09-109">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm provides two methods for creating clusters and assigning data points to the clusters.</span></span> <span data-ttu-id="e6c09-110">第一種方法是 *K-means* 演算法，這是一種硬式群集方法。</span><span class="sxs-lookup"><span data-stu-id="e6c09-110">The first, the *K-means* algorithm, is a hard clustering method.</span></span> <span data-ttu-id="e6c09-111">這代表資料點只能屬於一個群集，而且會針對該群集中每個資料點的成員資格而計算單一機率。</span><span class="sxs-lookup"><span data-stu-id="e6c09-111">This means that a data point can belong to only one cluster, and that a single probability is calculated for the membership of each data point in that cluster.</span></span> <span data-ttu-id="e6c09-112">第二種方法是 *Expectation Maximization* (EM) 方法，這是一種軟式群集\*\* 方法。</span><span class="sxs-lookup"><span data-stu-id="e6c09-112">The second method, the *Expectation Maximization* (EM) method, is a *soft clustering* method.</span></span> <span data-ttu-id="e6c09-113">這代表資料點一定屬於多個群集，而且會針對資料點和群集的每個組合而計算機率。</span><span class="sxs-lookup"><span data-stu-id="e6c09-113">This means that a data point always belongs to multiple clusters, and that a probability is calculated for each combination of data point and cluster.</span></span>  
  
 <span data-ttu-id="e6c09-114">您可以設定 *CLUSTERING_METHOD* 參數以選擇要使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="e6c09-114">You can choose which algorithm to use by setting the *CLUSTERING_METHOD* parameter.</span></span> <span data-ttu-id="e6c09-115">預設的群集方法是可擴充的 EM。</span><span class="sxs-lookup"><span data-stu-id="e6c09-115">The default method for clustering is scalable EM.</span></span>  
  
### <a name="em-clustering"></a><span data-ttu-id="e6c09-116">EM 群集</span><span class="sxs-lookup"><span data-stu-id="e6c09-116">EM Clustering</span></span>  
 <span data-ttu-id="e6c09-117">在 EM 群集中，演算法會反覆地精簡初始群集模型以符合資料，並判斷資料點存在於群集內的機率。</span><span class="sxs-lookup"><span data-stu-id="e6c09-117">In EM clustering, the algorithm iteratively refines an initial cluster model to fit the data and determines the probability that a data point exists in a cluster.</span></span> <span data-ttu-id="e6c09-118">演算法會在機率模型符合資料時結束此程序。</span><span class="sxs-lookup"><span data-stu-id="e6c09-118">The algorithm ends the process when the probabilistic model fits the data.</span></span> <span data-ttu-id="e6c09-119">用來決定符合度的函數是在模型已知時的資料對數可能性。</span><span class="sxs-lookup"><span data-stu-id="e6c09-119">The function used to determine the fit is the log-likelihood of the data given the model.</span></span>  
  
 <span data-ttu-id="e6c09-120">如果在程序期間產生空白的群集，或者如果一或多個群集的成員資格落在指定臨界值之下，則具有低母體的群集會在新的資料點重設種子，然後再重新執行 EM 演算法</span><span class="sxs-lookup"><span data-stu-id="e6c09-120">If empty clusters are generated during the process, or if the membership of one or more of the clusters falls below a given threshold, the clusters with low populations are reseeded at new points and the EM algorithm is rerun.</span></span>  
  
 <span data-ttu-id="e6c09-121">EM 群集方法的結果並非機率式。</span><span class="sxs-lookup"><span data-stu-id="e6c09-121">The results of the EM clustering method are probabilistic.</span></span> <span data-ttu-id="e6c09-122">這代表每個資料點都屬於所有的群集，但每次指定資料點給群集時都具有不同的機率。</span><span class="sxs-lookup"><span data-stu-id="e6c09-122">This means that every data point belongs to all clusters, but each assignment of a data point to a cluster has a different probability.</span></span> <span data-ttu-id="e6c09-123">因為此方法允許群集重疊，所以所有群集中的項目總和可能會超過定型集中的項目總數。</span><span class="sxs-lookup"><span data-stu-id="e6c09-123">Because the method allows for clusters to overlap, the sum of items in all the clusters may exceed the total items in the training set.</span></span> <span data-ttu-id="e6c09-124">在採礦模型結果中會調整代表支援的分數來解決這種情況。</span><span class="sxs-lookup"><span data-stu-id="e6c09-124">In the mining model results, scores that indicate support are adjusted to account for this.</span></span>  
  
 <span data-ttu-id="e6c09-125">EM 演算法是用於 Microsoft 群集模型中的預設演算法。</span><span class="sxs-lookup"><span data-stu-id="e6c09-125">The EM algorithm is the default algorithm used in Microsoft clustering models.</span></span> <span data-ttu-id="e6c09-126">之所以用這個演算法來當做預設值，是因為與 K-means 群集相較，它可提供多項優勢：</span><span class="sxs-lookup"><span data-stu-id="e6c09-126">This algorithm is used as the default because it offers multiple advantages in comparison to k-means clustering:</span></span>  
  
-   <span data-ttu-id="e6c09-127">最多只需要掃描一次資料庫。</span><span class="sxs-lookup"><span data-stu-id="e6c09-127">Requires one database scan, at most.</span></span>  
  
-   <span data-ttu-id="e6c09-128">儘管記憶體 (RAM) 有限仍可運作。</span><span class="sxs-lookup"><span data-stu-id="e6c09-128">Will work despite limited memory (RAM).</span></span>  
  
-   <span data-ttu-id="e6c09-129">能夠使用順向資料指標。</span><span class="sxs-lookup"><span data-stu-id="e6c09-129">Has the ability to use a forward-only cursor.</span></span>  
  
-   <span data-ttu-id="e6c09-130">執行速度快過取樣方法。</span><span class="sxs-lookup"><span data-stu-id="e6c09-130">Outperforms sampling approaches.</span></span>  
  
 <span data-ttu-id="e6c09-131">Microsoft 實作提供兩種選擇：可擴充的 EM 和不可擴充的 EM。</span><span class="sxs-lookup"><span data-stu-id="e6c09-131">The Microsoft implementation provides two options: scalable and non-scalable EM.</span></span> <span data-ttu-id="e6c09-132">在可擴充的 EM 中，根據預設會使用前 50,000 筆記錄來植入初始掃描。</span><span class="sxs-lookup"><span data-stu-id="e6c09-132">By default, in scalable EM, the first 50,000 records are used to seed the initial scan.</span></span> <span data-ttu-id="e6c09-133">如果這項作業成功，則模型僅會使用這些資料。</span><span class="sxs-lookup"><span data-stu-id="e6c09-133">If this is successful, the model uses this data only.</span></span> <span data-ttu-id="e6c09-134">如果無法使用 50,000 筆記錄來找到相符的模型，就會再讀取額外的 50,000 筆記錄。</span><span class="sxs-lookup"><span data-stu-id="e6c09-134">If the model cannot be fit using 50,000 records, an additional 50,000 records are read.</span></span> <span data-ttu-id="e6c09-135">在不可擴充的 EM 中，則不論資料集的大小，都會讀取整個資料集。</span><span class="sxs-lookup"><span data-stu-id="e6c09-135">In non-scalable EM, the entire dataset is read regardless of its size.</span></span> <span data-ttu-id="e6c09-136">這種方法可能會建立更正確的群集，但記憶體需求可能很高。</span><span class="sxs-lookup"><span data-stu-id="e6c09-136">This method might create more accurate clusters, but the memory requirements can be significant.</span></span> <span data-ttu-id="e6c09-137">因為可擴充的 EM 是以本機緩衝區作業，所以反覆執行資料的速度會快得多，且其演算法運用 CPU 記憶體快取的方法也比不可擴充的 EM 高明許多。</span><span class="sxs-lookup"><span data-stu-id="e6c09-137">Because scalable EM operates on a local buffer, iterating through the data is much faster, and the algorithm makes much better use of the CPU memory cache than non-scalable EM.</span></span> <span data-ttu-id="e6c09-138">此外，即使所有資料都可放入主記憶體，可擴充的 EM 速度也比不可擴充的 EM 快了三倍。</span><span class="sxs-lookup"><span data-stu-id="e6c09-138">Moreover, scalable EM is three times faster than non-scalable EM, even if all the data can fit in main memory.</span></span> <span data-ttu-id="e6c09-139">在大多數的案例中，效能改善並不會導致整個模型的品質降低。</span><span class="sxs-lookup"><span data-stu-id="e6c09-139">In the majority of cases, the performance improvement does not lead to lower quality of the complete model.</span></span>  
  
 <span data-ttu-id="e6c09-140">如需描述以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 群集演算法實作之 EM 的技術報告，請參閱 [Scaling EM (Expectation Maximization) Clustering to Large Databases](https://go.microsoft.com/fwlink/?LinkId=45964)(將 EM (Expectation Maximization) 群集擴充為大型資料庫)。</span><span class="sxs-lookup"><span data-stu-id="e6c09-140">For a technical report that describes the implementation of EM in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm, see [Scaling EM (Expectation Maximization) Clustering to Large Databases](https://go.microsoft.com/fwlink/?LinkId=45964).</span></span>  
  
### <a name="k-means-clustering"></a><span data-ttu-id="e6c09-141">K-Means 叢集</span><span class="sxs-lookup"><span data-stu-id="e6c09-141">K-Means Clustering</span></span>  
 <span data-ttu-id="e6c09-142">K-means 群集是知名的群集成員資格指派方法，作業方式是將群集中項目之間的差異最小化，並將群集之間的距離最大化。</span><span class="sxs-lookup"><span data-stu-id="e6c09-142">K-means clustering is a well-known method of assigning cluster membership by minimizing the differences among items in a cluster while maximizing the distance between clusters.</span></span> <span data-ttu-id="e6c09-143">K-means 中的 "means" 是指群集的「距心」\*\*，這是任意選擇的資料點，在選擇後會反覆調整，直到能代表群集中所有資料點的真正平均值為止。</span><span class="sxs-lookup"><span data-stu-id="e6c09-143">The "means" in k-means refers to the *centroid* of the cluster, which is a data point that is chosen arbitrarily and then refined iteratively until it represents the true mean of all data points in the cluster.</span></span> <span data-ttu-id="e6c09-144">"k" 則是指用來植入群集程序的任意數目的資料點。</span><span class="sxs-lookup"><span data-stu-id="e6c09-144">The "k" refers to an arbitrary number of points that are used to seed the clustering process.</span></span> <span data-ttu-id="e6c09-145">K-means 演算法會計算群集中資料記錄之間的歐氏距離平方 (Squared Euclidean Distance) 以及代表群集平均值的向量，然後在總和達到最小值時聚合於最終的一組 K 群集。</span><span class="sxs-lookup"><span data-stu-id="e6c09-145">The k-means algorithm calculates the squared Euclidean distances between data records in a cluster and the vector that represents the cluster mean, and converges on a final set of k clusters when that sum reaches its minimum value.</span></span>  
  
 <span data-ttu-id="e6c09-146">K-means 演算法會將每個資料點剛好指派給一個群集，而不允許成員資格有任何不確定性。</span><span class="sxs-lookup"><span data-stu-id="e6c09-146">The k-means algorithm assigns each data point to exactly one cluster, and does not allow for uncertainty in membership.</span></span> <span data-ttu-id="e6c09-147">群集中的成員資格會以與距心的距離來表示。</span><span class="sxs-lookup"><span data-stu-id="e6c09-147">Membership in a cluster is expressed as a distance from the centroid.</span></span>  
  
 <span data-ttu-id="e6c09-148">一般而言，K-means 演算法可用來建立連續屬性的群集，其中與平均值距離的計算相當簡單。</span><span class="sxs-lookup"><span data-stu-id="e6c09-148">Typically, the k-means algorithm is used for creating clusters of continuous attributes, where calculating distance to a mean is straightforward.</span></span> <span data-ttu-id="e6c09-149">不過， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 實作會使用機率，將 K-means 方法調整為適用於群集離散屬性。</span><span class="sxs-lookup"><span data-stu-id="e6c09-149">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] implementation adapts the k-means method to cluster discrete attributes, by using probabilities.</span></span>  <span data-ttu-id="e6c09-150">對離散屬性而言，資料點與特定群集的距離計算方法如下：</span><span class="sxs-lookup"><span data-stu-id="e6c09-150">For discrete attributes, the distance of a data point from a particular cluster is calculated as follows:</span></span>  
  
 <span data-ttu-id="e6c09-151">1 - P(data point, cluster)</span><span class="sxs-lookup"><span data-stu-id="e6c09-151">1 - P(data point, cluster)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6c09-152">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 群集演算法不會公開用來計算 K-means 的距離函數，而距離量值則無法用於完成的模型中。</span><span class="sxs-lookup"><span data-stu-id="e6c09-152">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm does not expose the distance function used in computing k-means, and measures of distance are not available in the completed model.</span></span> <span data-ttu-id="e6c09-153">不過，您可以使用預測函數來傳回對應至距離的值，其中距離是計算成屬於群集之資料點的機率。</span><span class="sxs-lookup"><span data-stu-id="e6c09-153">However, you can use a prediction function to return a value that corresponds to distance, where distance is computed as the probability of a data point belonging to the cluster.</span></span> <span data-ttu-id="e6c09-154">如需詳細資訊，請參閱 [ClusterProbability &#40;DMX&#41;](/sql/dmx/clusterprobability-dmx)。</span><span class="sxs-lookup"><span data-stu-id="e6c09-154">For more information, see [ClusterProbability &#40;DMX&#41;](/sql/dmx/clusterprobability-dmx).</span></span>  
  
 <span data-ttu-id="e6c09-155">K-means 演算法提供兩種資料集取樣的方法：一種是不可擴充的 K-means，這種方法會載入整個資料集，且進行一次群集行程；另一種則是可擴充的 K-means，其中演算法會使用前 50,000 個案例，且只有在需要更多資料才能達到更佳的模型與資料符合度時，才會讀取更多的案例。</span><span class="sxs-lookup"><span data-stu-id="e6c09-155">The k-means algorithm provides two methods of sampling the data set: non-scalable K-means, which loads the entire data set and makes one clustering pass, or scalable k-means, where the algorithm uses the first 50,000 cases and reads more cases only if it needs more data to achieve a good fit of model to data.</span></span>  
  
### <a name="updates-to-the-microsoft-clustering-algorithm-in-sql-server-2008"></a><span data-ttu-id="e6c09-156">SQL Server 2008 中的 Microsoft 群集演算法更新</span><span class="sxs-lookup"><span data-stu-id="e6c09-156">Updates to the Microsoft Clustering Algorithm in SQL Server 2008</span></span>  
 <span data-ttu-id="e6c09-157">在 SQL Server 2008 中， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 群集演算法的預設組態已變更為使用內部參數 NORMALIZATION = 1。</span><span class="sxs-lookup"><span data-stu-id="e6c09-157">In SQL Server 2008, the default configuration of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] clustering algorithm was changed to use the internal parameter, NORMALIZATION = 1.</span></span> <span data-ttu-id="e6c09-158">正規化是使用 Z-score 統計資料執行，採用常態分佈。</span><span class="sxs-lookup"><span data-stu-id="e6c09-158">Normalization is performed using z-score statistics, and assumes normal distribution.</span></span> <span data-ttu-id="e6c09-159">此預設行為變更的意圖是將可能有大範圍和許多極端值之屬性的影響降至最低。</span><span class="sxs-lookup"><span data-stu-id="e6c09-159">The intent of this change in the default behavior is to minimize the effect of attributes that might have large magnitudes and many outliers.</span></span> <span data-ttu-id="e6c09-160">不過，Z-score 正規化可能會在非常態分佈 (例如統一分佈) 上改變群集結果。</span><span class="sxs-lookup"><span data-stu-id="e6c09-160">However, z-score normalization may alter the clustering results on distributions that are not normal (such as uniform distributions).</span></span> <span data-ttu-id="e6c09-161">若要防止正規化，取得和 SQL Server 2005 中的 K-means 群集演算法相同的行為，您可以使用 [參數設定]\*\*\*\* 對話方塊加入自訂參數 NORMALIZATION，並將其值設定為 0。</span><span class="sxs-lookup"><span data-stu-id="e6c09-161">To prevent normalization and obtain the same behavior as the K-means clustering algorithm in SQL Server 2005, you can use the **Parameter Settings** dialog box to add the custom parameter, NORMALIZATION, and set its value to 0.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6c09-162">NORMALIZATION 參數是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 群集演算法的內部屬性，不受支援。</span><span class="sxs-lookup"><span data-stu-id="e6c09-162">The NORMALIZATION parameter is an internal property of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm and is not supported.</span></span> <span data-ttu-id="e6c09-163">一般而言，建議在群集模型中使用正規化，以改善模型結果。</span><span class="sxs-lookup"><span data-stu-id="e6c09-163">In general, the use of normalization is recommended in clustering models to improve model results.</span></span>  
  
## <a name="customizing-the-microsoft-clustering-algorithm"></a><span data-ttu-id="e6c09-164">自訂 Microsoft 群集演算法</span><span class="sxs-lookup"><span data-stu-id="e6c09-164">Customizing the Microsoft Clustering Algorithm</span></span>  
 <span data-ttu-id="e6c09-165">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 叢集演算法支援數個會影響所產生之採礦模型的行為、效能和精確度的參數。</span><span class="sxs-lookup"><span data-stu-id="e6c09-165">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm supports several parameters that affect the behavior, performance, and accuracy of the resulting mining model.</span></span>  
  
### <a name="setting-algorithm-parameters"></a><span data-ttu-id="e6c09-166">設定演算法參數</span><span class="sxs-lookup"><span data-stu-id="e6c09-166">Setting Algorithm Parameters</span></span>  
 <span data-ttu-id="e6c09-167">下表描述可用於 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 群集演算法的參數。</span><span class="sxs-lookup"><span data-stu-id="e6c09-167">The following table describes the parameters that can be used with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm.</span></span> <span data-ttu-id="e6c09-168">這些參數對於所產生之採礦模型的效能和精確度都有影響。</span><span class="sxs-lookup"><span data-stu-id="e6c09-168">These parameters affect both the performance and accuracy of the resulting mining model.</span></span>  
  
 <span data-ttu-id="e6c09-169">CLUSTERING_METHOD</span><span class="sxs-lookup"><span data-stu-id="e6c09-169">CLUSTERING_METHOD</span></span>  
 <span data-ttu-id="e6c09-170">指定演算法要使用的群集方法。</span><span class="sxs-lookup"><span data-stu-id="e6c09-170">Specifies the clustering method for the algorithm to use.</span></span> <span data-ttu-id="e6c09-171">可用的群集方法有：</span><span class="sxs-lookup"><span data-stu-id="e6c09-171">The following clustering methods are available:</span></span>  
  
|<span data-ttu-id="e6c09-172">識別碼</span><span class="sxs-lookup"><span data-stu-id="e6c09-172">ID</span></span>|<span data-ttu-id="e6c09-173">方法</span><span class="sxs-lookup"><span data-stu-id="e6c09-173">Method</span></span>|  
|--------|------------|  
|<span data-ttu-id="e6c09-174">1</span><span class="sxs-lookup"><span data-stu-id="e6c09-174">1</span></span>|<span data-ttu-id="e6c09-175">可擴充的 EM</span><span class="sxs-lookup"><span data-stu-id="e6c09-175">Scalable EM</span></span>|  
|<span data-ttu-id="e6c09-176">2</span><span class="sxs-lookup"><span data-stu-id="e6c09-176">2</span></span>|<span data-ttu-id="e6c09-177">不可擴充的 EM (Non-scalable EM)</span><span class="sxs-lookup"><span data-stu-id="e6c09-177">Non-scalable EM</span></span>|  
|<span data-ttu-id="e6c09-178">3</span><span class="sxs-lookup"><span data-stu-id="e6c09-178">3</span></span>|<span data-ttu-id="e6c09-179">可擴充的 K-means</span><span class="sxs-lookup"><span data-stu-id="e6c09-179">Scalable K-Means</span></span>|  
|<span data-ttu-id="e6c09-180">4</span><span class="sxs-lookup"><span data-stu-id="e6c09-180">4</span></span>|<span data-ttu-id="e6c09-181">不可擴充的 K-means</span><span class="sxs-lookup"><span data-stu-id="e6c09-181">Non-scalable K-Means.</span></span>|  
  
 <span data-ttu-id="e6c09-182">預設值為 1 (可擴充的 EM)。</span><span class="sxs-lookup"><span data-stu-id="e6c09-182">The default is 1 (scalable EM).</span></span>  
  
 <span data-ttu-id="e6c09-183">CLUSTER_COUNT</span><span class="sxs-lookup"><span data-stu-id="e6c09-183">CLUSTER_COUNT</span></span>  
 <span data-ttu-id="e6c09-184">指定演算法要建立的大約群集數目。</span><span class="sxs-lookup"><span data-stu-id="e6c09-184">Specifies the approximate number of clusters to be built by the algorithm.</span></span> <span data-ttu-id="e6c09-185">如果無法從資料建立大約群集數目，則演算法會盡可能建立最多的群集。</span><span class="sxs-lookup"><span data-stu-id="e6c09-185">If the approximate number of clusters cannot be built from the data, the algorithm builds as many clusters as possible.</span></span> <span data-ttu-id="e6c09-186">將 CLUSTER_COUNT 設定為 0 會造成演算法使用啟發式決定，對於建立的群集數做出最好的決定。</span><span class="sxs-lookup"><span data-stu-id="e6c09-186">Setting the CLUSTER_COUNT to 0 causes the algorithm to use heuristics to best determine the number of clusters to build.</span></span>  
  
 <span data-ttu-id="e6c09-187">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="e6c09-187">The default is 10.</span></span>  
  
 <span data-ttu-id="e6c09-188">CLUSTER_SEED</span><span class="sxs-lookup"><span data-stu-id="e6c09-188">CLUSTER_SEED</span></span>  
 <span data-ttu-id="e6c09-189">指定在模型建立的初始階段，用於隨機產生群集的種子號碼。</span><span class="sxs-lookup"><span data-stu-id="e6c09-189">Specifies the seed number that is used to randomly generate clusters for the initial stage of model building.</span></span>  
  
 <span data-ttu-id="e6c09-190">藉由變更此數字，您可以變更建立初始群集的方法，然後比較使用不同的種子而建立的模型。</span><span class="sxs-lookup"><span data-stu-id="e6c09-190">By changing this number, you can change the way that the initial clusters are built, and then compare models that have been built using different seeds.</span></span> <span data-ttu-id="e6c09-191">如果種子已變更，但找到的群集並未大幅變更，則可將模型視為相當穩定。</span><span class="sxs-lookup"><span data-stu-id="e6c09-191">If the seed is changed but the clusters that are found do not change greatly , the model can be considered relatively stable.</span></span>  
  
 <span data-ttu-id="e6c09-192">預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="e6c09-192">The default is 0.</span></span>  
  
 <span data-ttu-id="e6c09-193">MINIMUM_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="e6c09-193">MINIMUM_SUPPORT</span></span>  
 <span data-ttu-id="e6c09-194">指定建立群集所需的案例最小數目。</span><span class="sxs-lookup"><span data-stu-id="e6c09-194">Specifies the minimum number of cases that are required to build a cluster.</span></span> <span data-ttu-id="e6c09-195">如果群集中的案例數目低於此數目，則會將群集視為空白並加以捨棄。</span><span class="sxs-lookup"><span data-stu-id="e6c09-195">If the number of cases in the cluster is lower than this number, the cluster is treated as empty and discarded.</span></span>  
  
 <span data-ttu-id="e6c09-196">如果將此數目設得過高，則可能會遺漏有效的群集。</span><span class="sxs-lookup"><span data-stu-id="e6c09-196">If you set this number too high, you may miss valid clusters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6c09-197">如果您使用預設的群集方法 EM，則某些群集可能會有比指定值低的支援值。</span><span class="sxs-lookup"><span data-stu-id="e6c09-197">If you use EM, which is the default clustering method, some clusters may have a support value that is lower than the specified value.</span></span> <span data-ttu-id="e6c09-198">這是因為每個案例都會針對它在所有可能群集中的成員資格進行評估，而某些群集可能只有最少的支援。</span><span class="sxs-lookup"><span data-stu-id="e6c09-198">This is because each case is evaluated for its membership in all possible clusters, and for some clusters there may be only minimal support.</span></span>  
  
 <span data-ttu-id="e6c09-199">預設值是 1。</span><span class="sxs-lookup"><span data-stu-id="e6c09-199">The default is 1.</span></span>  
  
 <span data-ttu-id="e6c09-200">MODELLING_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="e6c09-200">MODELLING_CARDINALITY</span></span>  
 <span data-ttu-id="e6c09-201">指定在叢集處理期間建構的範例模型數目。</span><span class="sxs-lookup"><span data-stu-id="e6c09-201">Specifies the number of sample models that are constructed during the clustering process.</span></span>  
  
 <span data-ttu-id="e6c09-202">減少候選模型的數目可以改善效能，但風險是可能會遺漏某些完善的候選模型。</span><span class="sxs-lookup"><span data-stu-id="e6c09-202">Reducing the number of candidate models can improve performance at the risk of missing some good candidate models.</span></span>  
  
 <span data-ttu-id="e6c09-203">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="e6c09-203">The default is 10.</span></span>  
  
 <span data-ttu-id="e6c09-204">STOPPING_TOLERANCE</span><span class="sxs-lookup"><span data-stu-id="e6c09-204">STOPPING_TOLERANCE</span></span>  
 <span data-ttu-id="e6c09-205">指定用來決定何時到達聚合以及演算法完成模型建立的值。</span><span class="sxs-lookup"><span data-stu-id="e6c09-205">Specifies the value that is used to determine when convergence is reached and the algorithm is finished building the model.</span></span> <span data-ttu-id="e6c09-206">當群集機率的整體變更小於 STOPPING_TOLERANCE 參數除以模型大小的比率時，就到達聚合。</span><span class="sxs-lookup"><span data-stu-id="e6c09-206">Convergence is reached when the overall change in cluster probabilities is less than the ratio of the STOPPING_TOLERANCE parameter divided by the size of the model.</span></span>  
  
 <span data-ttu-id="e6c09-207">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="e6c09-207">The default is 10.</span></span>  
  
 <span data-ttu-id="e6c09-208">SAMPLE_SIZE</span><span class="sxs-lookup"><span data-stu-id="e6c09-208">SAMPLE_SIZE</span></span>  
 <span data-ttu-id="e6c09-209">指定如果 CLUSTERING_METHOD 參數設定為可擴充的其中一個群集方法時，演算法在每個行程上使用的案例數目。</span><span class="sxs-lookup"><span data-stu-id="e6c09-209">Specifies the number of cases that the algorithm uses on each pass if the CLUSTERING_METHOD parameter is set to one of the scalable clustering methods.</span></span> <span data-ttu-id="e6c09-210">將 SAMPLE_SIZE 參數設定為 0 會導致整個資料集群集在單一行程中。</span><span class="sxs-lookup"><span data-stu-id="e6c09-210">Setting the SAMPLE_SIZE parameter to 0 will cause the whole dataset to be clustered in a single pass.</span></span> <span data-ttu-id="e6c09-211">在單一行程中載入整個資料集可能會導致記憶體和效能的問題。</span><span class="sxs-lookup"><span data-stu-id="e6c09-211">Loading the entire dataset in a single pass can cause memory and performance issues.</span></span>  
  
 <span data-ttu-id="e6c09-212">預設值是 50000。</span><span class="sxs-lookup"><span data-stu-id="e6c09-212">The default is 50000.</span></span>  
  
 <span data-ttu-id="e6c09-213">MAXIMUM_INPUT_ATTRIBUTES</span><span class="sxs-lookup"><span data-stu-id="e6c09-213">MAXIMUM_INPUT_ATTRIBUTES</span></span>  
 <span data-ttu-id="e6c09-214">指定在叫用特徵選取之前，演算法可以處理輸入屬性的最大數目。</span><span class="sxs-lookup"><span data-stu-id="e6c09-214">Specifies the maximum number of input attributes that the algorithm can handle before it invokes feature selection.</span></span> <span data-ttu-id="e6c09-215">將此值設定為 0 即指定屬性數目沒有上限。</span><span class="sxs-lookup"><span data-stu-id="e6c09-215">Setting this value to 0 specifies that there is no maximum number of attributes.</span></span>  
  
 <span data-ttu-id="e6c09-216">增加屬性數目可能會使效能顯著下降。</span><span class="sxs-lookup"><span data-stu-id="e6c09-216">Increasing the number of attributes can significantly degrade performance.</span></span>  
  
 <span data-ttu-id="e6c09-217">預設值為 255。</span><span class="sxs-lookup"><span data-stu-id="e6c09-217">The default is 255.</span></span>  
  
 <span data-ttu-id="e6c09-218">MAXIMUM_STATES</span><span class="sxs-lookup"><span data-stu-id="e6c09-218">MAXIMUM_STATES</span></span>  
 <span data-ttu-id="e6c09-219">指定演算法所支援之屬性狀態的最大數目。</span><span class="sxs-lookup"><span data-stu-id="e6c09-219">Specifies the maximum number of attribute states that the algorithm supports.</span></span> <span data-ttu-id="e6c09-220">如果屬性擁有的狀態數超過最大值，則演算法會使用最常用的狀態，並忽略其餘的狀態。</span><span class="sxs-lookup"><span data-stu-id="e6c09-220">If an attribute has more states than the maximum, the algorithm uses the most popular states and ignores the remaining states.</span></span>  
  
 <span data-ttu-id="e6c09-221">增加狀態數目可能會使效能顯著下降。</span><span class="sxs-lookup"><span data-stu-id="e6c09-221">Increasing the number of states can significantly degrade performance.</span></span>  
  
 <span data-ttu-id="e6c09-222">預設值為 100。</span><span class="sxs-lookup"><span data-stu-id="e6c09-222">The default is 100.</span></span>  
  
### <a name="modeling-flags"></a><span data-ttu-id="e6c09-223">模型旗標</span><span class="sxs-lookup"><span data-stu-id="e6c09-223">Modeling Flags</span></span>  
 <span data-ttu-id="e6c09-224">演算法支援下列模型旗標。</span><span class="sxs-lookup"><span data-stu-id="e6c09-224">The algorithm supports the following modeling flags.</span></span> <span data-ttu-id="e6c09-225">您可以在建立採礦結構或採礦模型時定義模型旗標。</span><span class="sxs-lookup"><span data-stu-id="e6c09-225">You define modeling flags when you create the mining structure or mining model.</span></span> <span data-ttu-id="e6c09-226">模型旗標會指定在分析期間如何處理每個資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="e6c09-226">The modeling flags specify how values in each column are handled during analysis.</span></span>  
  
|<span data-ttu-id="e6c09-227">模型旗標</span><span class="sxs-lookup"><span data-stu-id="e6c09-227">Modeling Flag</span></span>|<span data-ttu-id="e6c09-228">描述</span><span class="sxs-lookup"><span data-stu-id="e6c09-228">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="e6c09-229">MODEL_EXISTENCE_ONLY</span><span class="sxs-lookup"><span data-stu-id="e6c09-229">MODEL_EXISTENCE_ONLY</span></span>|<span data-ttu-id="e6c09-230">資料行將被視為擁有兩個可能狀態：「遺漏」和「現有」。</span><span class="sxs-lookup"><span data-stu-id="e6c09-230">The column will be treated as having two possible states: Missing and Existing.</span></span> <span data-ttu-id="e6c09-231">Null 為遺漏值。</span><span class="sxs-lookup"><span data-stu-id="e6c09-231">A null is a missing value.</span></span><br /><br /> <span data-ttu-id="e6c09-232">適用於採礦模型資料行。</span><span class="sxs-lookup"><span data-stu-id="e6c09-232">Applies to mining model column.</span></span>|  
|<span data-ttu-id="e6c09-233">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="e6c09-233">NOT NULL</span></span>|<span data-ttu-id="e6c09-234">資料行不得包含 Null 值。</span><span class="sxs-lookup"><span data-stu-id="e6c09-234">The column cannot contain a null.</span></span> <span data-ttu-id="e6c09-235">如果 Analysis Services 在模型定型期間遇到 Null 值，將會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="e6c09-235">An error will result if Analysis Services encounters a null during model training.</span></span><br /><br /> <span data-ttu-id="e6c09-236">適用於採礦結構資料行。</span><span class="sxs-lookup"><span data-stu-id="e6c09-236">Applies to mining structure column.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6c09-237">需求</span><span class="sxs-lookup"><span data-stu-id="e6c09-237">Requirements</span></span>  
 <span data-ttu-id="e6c09-238">叢集模型必須包含索引鍵資料行和輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="e6c09-238">A clustering model must contain a key column and input columns.</span></span> <span data-ttu-id="e6c09-239">您也可以將輸入資料行定義為可預測的。</span><span class="sxs-lookup"><span data-stu-id="e6c09-239">You can also define input columns as being predictable.</span></span> <span data-ttu-id="e6c09-240">設定為 `Predict Only` 的資料行不會用來建立群集。</span><span class="sxs-lookup"><span data-stu-id="e6c09-240">Columns set to `Predict Only` are not used to build clusters.</span></span> <span data-ttu-id="e6c09-241">這些值在群集內的散發是在建立群集之後才計算的。</span><span class="sxs-lookup"><span data-stu-id="e6c09-241">The distribution of these values in the clusters are calculated after the clusters are built.</span></span>  
  
### <a name="input-and-predictable-columns"></a><span data-ttu-id="e6c09-242">輸入和可預測資料行</span><span class="sxs-lookup"><span data-stu-id="e6c09-242">Input and Predictable Columns</span></span>  
 <span data-ttu-id="e6c09-243">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 群集演算法支援下表所列的特定輸入資料行和可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="e6c09-243">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm supports the specific input columns and predictable columns that are listed in the following table.</span></span> <span data-ttu-id="e6c09-244">如需內容類型用於採礦模型時所代表意義的詳細資訊，請參閱[內容類型 &#40;資料採礦&#41;](content-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="e6c09-244">For more information about what the content types mean when used in a mining model, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>  
  
|<span data-ttu-id="e6c09-245">資料行</span><span class="sxs-lookup"><span data-stu-id="e6c09-245">Column</span></span>|<span data-ttu-id="e6c09-246">內容類型</span><span class="sxs-lookup"><span data-stu-id="e6c09-246">Content types</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="e6c09-247">輸入屬性</span><span class="sxs-lookup"><span data-stu-id="e6c09-247">Input attribute</span></span>|<span data-ttu-id="e6c09-248">Continuous、Cyclical、Discrete、Discretized、Key、Table 和 Ordered</span><span class="sxs-lookup"><span data-stu-id="e6c09-248">Continuous, Cyclical, Discrete, Discretized, Key, Table, Ordered</span></span>|  
|<span data-ttu-id="e6c09-249">可預測屬性</span><span class="sxs-lookup"><span data-stu-id="e6c09-249">Predictable attribute</span></span>|<span data-ttu-id="e6c09-250">Continuous、Cyclical、Discrete、Discretized、Table 和 Ordered</span><span class="sxs-lookup"><span data-stu-id="e6c09-250">Continuous, Cyclical, Discrete, Discretized, Table, Ordered</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="e6c09-251">系統支援 Cyclical 和 Ordered 內容類型，但是演算法將它們視為離散值，因此不會執行特殊處理。</span><span class="sxs-lookup"><span data-stu-id="e6c09-251">Cyclical and Ordered content types are supported, but the algorithm treats them as discrete values and does not perform special processing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6c09-252">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6c09-252">See Also</span></span>  
 <span data-ttu-id="e6c09-253">[Microsoft 群集演算法](microsoft-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="e6c09-253">[Microsoft Clustering Algorithm](microsoft-clustering-algorithm.md) </span></span>  
 <span data-ttu-id="e6c09-254">[群集模型查詢範例](clustering-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="e6c09-254">[Clustering Model Query Examples](clustering-model-query-examples.md) </span></span>  
 [<span data-ttu-id="e6c09-255">叢集模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="e6c09-255">Mining Model Content for Clustering Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-clustering-models-analysis-services-data-mining.md)  
  
  
