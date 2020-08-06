---
title: Microsoft 群集演算法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- segmentation algorithms [Analysis Services]
- nearest neighbor [Data Mining]
- clustering [Data Mining]
- clusters [Analysis Services]
- relationships [Analysis Services], clusters
- algorithms [data mining]
- classification algorithms [Analysis Services]
- datasets [Analysis Services]
- clustering algorithms [Analysis Services]
ms.assetid: 92a1e67e-f46e-4960-99b2-4d20f6192fbd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9cb14e1e2672cfaef883f0686fc29206b0c8e657
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597456"
---
# <a name="microsoft-clustering-algorithm"></a><span data-ttu-id="4dd17-102">Microsoft 群集演算法</span><span class="sxs-lookup"><span data-stu-id="4dd17-102">Microsoft Clustering Algorithm</span></span>
  <span data-ttu-id="4dd17-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 群集演算法是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 所提供的分割演算法。</span><span class="sxs-lookup"><span data-stu-id="4dd17-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm is a segmentation algorithm provided by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="4dd17-104">此演算法使用反覆技巧，將資料集內的案例分成包含類似特性的群集。</span><span class="sxs-lookup"><span data-stu-id="4dd17-104">The algorithm uses iterative techniques to group cases in a dataset into clusters that contain similar characteristics.</span></span> <span data-ttu-id="4dd17-105">這些群集對於瀏覽資料、識別資料的異常及建立預測很有幫助。</span><span class="sxs-lookup"><span data-stu-id="4dd17-105">These groupings are useful for exploring data, identifying anomalies in the data, and creating predictions.</span></span>

 <span data-ttu-id="4dd17-106">群集模型會識別資料集內，無法透過偶然的邏輯觀察而衍生之關聯性。</span><span class="sxs-lookup"><span data-stu-id="4dd17-106">Clustering models identify relationships in a dataset that you might not logically derive through casual observation.</span></span> <span data-ttu-id="4dd17-107">例如，您可以從邏輯上看出騎腳踏車上班的人通常不會住在離工作地點很遠的地方。</span><span class="sxs-lookup"><span data-stu-id="4dd17-107">For example, you can logically discern that people who commute to their jobs by bicycle do not typically live a long distance from where they work.</span></span> <span data-ttu-id="4dd17-108">不過，此演算法可以尋找關於腳踏車通勤者之其他較不明顯的特性。</span><span class="sxs-lookup"><span data-stu-id="4dd17-108">The algorithm, however, can find other characteristics about bicycle commuters that are not as obvious.</span></span> <span data-ttu-id="4dd17-109">在下列圖表中，群集 A 代表可能要開車上班的人之資料，而群集 B 代表可能要騎腳踏車上班的人之資料。</span><span class="sxs-lookup"><span data-stu-id="4dd17-109">In the following diagram, cluster A represents data about people who tend to drive to work, while cluster B represents data about people who tend to ride bicycles to work.</span></span>

 <span data-ttu-id="4dd17-110">![通勤者傾向的叢集模式](../media/clustering-example.gif "通勤者傾向的叢集模式")</span><span class="sxs-lookup"><span data-stu-id="4dd17-110">![Cluster pattern of commuter tendencies](../media/clustering-example.gif "Cluster pattern of commuter tendencies")</span></span>

 <span data-ttu-id="4dd17-111">群集演算法與其他資料採礦演算法不同，例如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 決策樹演算法，因為您不必指定可預測資料行就可以建立群集模型。</span><span class="sxs-lookup"><span data-stu-id="4dd17-111">The clustering algorithm differs from other data mining algorithms, such as the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm, in that you do not have to designate a predictable column to be able to build a clustering model.</span></span> <span data-ttu-id="4dd17-112">叢集演算法會從資料中已存在的關聯性以及從演算法識別的群集嚴格地培訓模型。</span><span class="sxs-lookup"><span data-stu-id="4dd17-112">The clustering algorithm trains the model strictly from the relationships that exist in the data and from the clusters that the algorithm identifies.</span></span>

## <a name="example"></a><span data-ttu-id="4dd17-113">範例</span><span class="sxs-lookup"><span data-stu-id="4dd17-113">Example</span></span>
 <span data-ttu-id="4dd17-114">試想有一群人共用類似的人口統計資訊，而且向 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] 公司購買類似產品。</span><span class="sxs-lookup"><span data-stu-id="4dd17-114">Consider a group of people who share similar demographic information and who buy similar products from the [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] company.</span></span> <span data-ttu-id="4dd17-115">這群人即代表一個資料群集。</span><span class="sxs-lookup"><span data-stu-id="4dd17-115">This group of people represents a cluster of data.</span></span> <span data-ttu-id="4dd17-116">數個群集可存在於一個資料庫中。</span><span class="sxs-lookup"><span data-stu-id="4dd17-116">Several such clusters may exist in a database.</span></span> <span data-ttu-id="4dd17-117">藉由觀察構成群集的資料行，您可以更清楚地看到資料集內的記錄彼此如何相關。</span><span class="sxs-lookup"><span data-stu-id="4dd17-117">By observing the columns that make up a cluster, you can more clearly see how records in a dataset are related to one another.</span></span>

## <a name="how-the-algorithm-works"></a><span data-ttu-id="4dd17-118">演算法的運作方式</span><span class="sxs-lookup"><span data-stu-id="4dd17-118">How the Algorithm Works</span></span>
 <span data-ttu-id="4dd17-119">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 群集演算法會先識別資料集內的關聯性，然後依據那些關聯性產生一系列群集。</span><span class="sxs-lookup"><span data-stu-id="4dd17-119">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm first identifies relationships in a dataset and generates a series of clusters based on those relationships.</span></span> <span data-ttu-id="4dd17-120">散佈圖是以視覺方式表示演算法如何將資料分組的有用方式，如下列圖表所示。</span><span class="sxs-lookup"><span data-stu-id="4dd17-120">A scatter plot is a useful way to visually represent how the algorithm groups data, as shown in the following diagram.</span></span> <span data-ttu-id="4dd17-121">散佈圖代表資料集內的所有案例，而每一個案例是圖表上的一個點。</span><span class="sxs-lookup"><span data-stu-id="4dd17-121">The scatter plot represents all the cases in the dataset, and each case is a point on the graph.</span></span> <span data-ttu-id="4dd17-122">群集會將圖表上的點分組，並說明演算法所識別的關聯性。</span><span class="sxs-lookup"><span data-stu-id="4dd17-122">The clusters group points on the graph and illustrate the relationships that the algorithm identifies.</span></span>

 <span data-ttu-id="4dd17-123">![資料集中案例的散佈圖](../media/clustering-plot.gif "資料集中案例的散佈圖")</span><span class="sxs-lookup"><span data-stu-id="4dd17-123">![Scatter plot of cases in a dataset](../media/clustering-plot.gif "Scatter plot of cases in a dataset")</span></span>

 <span data-ttu-id="4dd17-124">第一次定義群集之後，演算法會計算群集代表點群組的程度，然後嘗試重新定義群組，來建立更能代表資料的群集。</span><span class="sxs-lookup"><span data-stu-id="4dd17-124">After first defining the clusters, the algorithm calculates how well the clusters represent groupings of the points, and then tries to redefine the groupings to create clusters that better represent the data.</span></span> <span data-ttu-id="4dd17-125">此演算法反覆執行此程序，直到它無法以重新定義群集來改進結果為止。</span><span class="sxs-lookup"><span data-stu-id="4dd17-125">The algorithm iterates through this process until it cannot improve the results more by redefining the clusters.</span></span>

 <span data-ttu-id="4dd17-126">您可以藉由選取特定的群集技巧、限制群集的數目上限或變更建立群集所需的支援量，來自訂演算法的作業方式。</span><span class="sxs-lookup"><span data-stu-id="4dd17-126">You can customize the way the algorithm works by selecting a specifying a clustering technique, limiting the maximum number of clusters, or changing the amount of support required to create a cluster.</span></span> <span data-ttu-id="4dd17-127">如需詳細資訊，請參閱 [Microsoft 群集演算法技術參考](microsoft-clustering-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="4dd17-127">For more information, see [Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md).</span></span>

## <a name="data-required-for-clustering-models"></a><span data-ttu-id="4dd17-128">叢集模型所需的資料</span><span class="sxs-lookup"><span data-stu-id="4dd17-128">Data Required for Clustering Models</span></span>
 <span data-ttu-id="4dd17-129">當您準備資料以供培訓叢集模型使用時，應該要了解特定演算法的需求，包括所需的資料量及資料的使用方式等。</span><span class="sxs-lookup"><span data-stu-id="4dd17-129">When you prepare data for use in training a clustering model, you should understand the requirements for the particular algorithm, including how much data is needed, and how the data is used.</span></span>

 <span data-ttu-id="4dd17-130">叢集模型的需求如下：</span><span class="sxs-lookup"><span data-stu-id="4dd17-130">The requirements for a clustering model are as follows:</span></span>

-   <span data-ttu-id="4dd17-131">**單一索引鍵資料行** ：每個模型都必須包含一個能唯一識別每一筆記錄的數值或文字資料行。</span><span class="sxs-lookup"><span data-stu-id="4dd17-131">**A single key column** Each model must contain one numeric or text column that uniquely identifies each record.</span></span> <span data-ttu-id="4dd17-132">不允許複合的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="4dd17-132">Compound keys are not allowed.</span></span>

-   <span data-ttu-id="4dd17-133">**輸入資料行** ：每個模型都至少包含一個輸入資料行，內含用來建置群集的值。</span><span class="sxs-lookup"><span data-stu-id="4dd17-133">**Input columns** Each model must contain at least one input column that contains the values that are used to build the clusters.</span></span> <span data-ttu-id="4dd17-134">您可以依需求擁有任何數量的輸入資料行，但根據每個資料行中的值數目，加入額外的資料行可能會增加培訓模型所需的時間。</span><span class="sxs-lookup"><span data-stu-id="4dd17-134">You can have as many input columns as you want, but depending on the number of values in each column, the addition of extra columns can increase the time it takes to train the model.</span></span>

-   <span data-ttu-id="4dd17-135">**選擇性的可預測資料行** ：演算法不需要使用可預測資料行來建置模型，但您可以加入幾乎任何資料類型的可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="4dd17-135">**Optional predictable column** The algorithm does not need a predictable column to build the model, but you can add a predictable column of almost any data type.</span></span> <span data-ttu-id="4dd17-136">可預測資料行的值可用來當做叢集模型的輸入，或者也可以指定只將其用於預測。</span><span class="sxs-lookup"><span data-stu-id="4dd17-136">The values of the predictable column can be treated as input to the clustering model, or you can specify that it be used for prediction only.</span></span> <span data-ttu-id="4dd17-137">例如，如果想要根據地區或年齡等人口統計資料進行群集而預測客戶收入，您可以將收入指定為 `PredictOnly`，然後加入所有其他的資料行 (例如地區或年齡) 做為輸入。</span><span class="sxs-lookup"><span data-stu-id="4dd17-137">For example, if you want to predict customer income by clustering on demographics such as region or age, you would specify income as `PredictOnly` and add all the other columns, such as region or age, as inputs.</span></span>

 <span data-ttu-id="4dd17-138">如需叢集模型所支援內容類型和資料類型的詳細資訊，請參閱 [Microsoft 叢集演算法技術參考](microsoft-clustering-algorithm-technical-reference.md)的＜需求＞一節。</span><span class="sxs-lookup"><span data-stu-id="4dd17-138">For more detailed information about the content types and data types supported for clustering models, see the Requirements section of [Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md).</span></span>

## <a name="viewing-a-clustering-model"></a><span data-ttu-id="4dd17-139">檢視叢集模型</span><span class="sxs-lookup"><span data-stu-id="4dd17-139">Viewing a Clustering Model</span></span>
 <span data-ttu-id="4dd17-140">若要瀏覽此模型，您可以使用 [Microsoft 群集檢視器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4dd17-140">To explore the model, you can use the **Microsoft Cluster Viewer**.</span></span> <span data-ttu-id="4dd17-141">在檢視叢集模型時， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會將叢集顯示在描述叢集關聯性的圖表中，並針對每個叢集提供詳細的設定檔、區分各個叢集的屬性清單以及整個培訓資料集的特性。</span><span class="sxs-lookup"><span data-stu-id="4dd17-141">When you view a clustering model, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] shows you the clusters in a diagram that depicts the relationships among clusters, and also provides a detailed profile of each cluster, a list of the attributes that distinguish each cluster from the others, and the characteristics of the entire training data set.</span></span> <span data-ttu-id="4dd17-142">如需詳細資訊，請參閱 [使用 Microsoft 叢集檢視器瀏覽模型](browse-a-model-using-the-microsoft-cluster-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="4dd17-142">For more information, see [Browse a Model Using the Microsoft Cluster Viewer](browse-a-model-using-the-microsoft-cluster-viewer.md).</span></span>

 <span data-ttu-id="4dd17-143">如果您想要知道更多詳細資訊，您可以在 [Microsoft 一般內容樹狀檢視器](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)中瀏覽此模型。</span><span class="sxs-lookup"><span data-stu-id="4dd17-143">If you want to know more detail, you can browse the model in the [Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span></span> <span data-ttu-id="4dd17-144">針對此模型所儲存的內容包括每個節點中所有值的分佈、每個群集的機率及其他資訊。</span><span class="sxs-lookup"><span data-stu-id="4dd17-144">The content stored for the model includes the distribution for all values in each node, the probability of each cluster, and other information.</span></span> <span data-ttu-id="4dd17-145">如需詳細資訊，請參閱 [叢集模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-clustering-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="4dd17-145">For more information, see [Mining Model Content for Clustering Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-clustering-models-analysis-services-data-mining.md).</span></span>

## <a name="creating-predictions"></a><span data-ttu-id="4dd17-146">建立預測</span><span class="sxs-lookup"><span data-stu-id="4dd17-146">Creating Predictions</span></span>
 <span data-ttu-id="4dd17-147">在此模型已培訓之後，結果會儲存成一組模式，供您瀏覽或用來做出預測。</span><span class="sxs-lookup"><span data-stu-id="4dd17-147">After the model has been trained, the results are stored as a set of patterns, which you can explore or use to make predictions.</span></span>

 <span data-ttu-id="4dd17-148">您可以建立查詢來傳回新資料是否符合已發現之群集的相關預測，或取得有關群集的描述性統計資料。</span><span class="sxs-lookup"><span data-stu-id="4dd17-148">You can create queries to return predictions about whether new data fits into the clusters that were discovered, or to obtain descriptive statistics about the clusters.</span></span>

 <span data-ttu-id="4dd17-149">如需如何針對資料採礦模型建立查詢的資訊，請參閱 [資料採礦查詢](data-mining-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="4dd17-149">For information about how to create queries against a data mining model, see [Data Mining Queries](data-mining-queries.md).</span></span> <span data-ttu-id="4dd17-150">如需如何在叢集模型中使用查詢的範例，請參閱 [叢集模型查詢範例](clustering-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="4dd17-150">For examples of how to use queries with a clustering model, see [Clustering Model Query Examples](clustering-model-query-examples.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="4dd17-151">備註</span><span class="sxs-lookup"><span data-stu-id="4dd17-151">Remarks</span></span>

-   <span data-ttu-id="4dd17-152">支援使用預測模型標記語言 (PMML) 來建立採礦模型。</span><span class="sxs-lookup"><span data-stu-id="4dd17-152">Supports the use of Predictive Model Markup Language (PMML) to create mining models.</span></span>

-   <span data-ttu-id="4dd17-153">支援鑽研。</span><span class="sxs-lookup"><span data-stu-id="4dd17-153">Supports drillthrough.</span></span>

-   <span data-ttu-id="4dd17-154">支援 OLAP 採礦模型的使用和資料採礦維度的建立。</span><span class="sxs-lookup"><span data-stu-id="4dd17-154">Supports the use of OLAP mining models and the creation of data mining dimensions.</span></span>

## <a name="see-also"></a><span data-ttu-id="4dd17-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4dd17-155">See Also</span></span>
 <span data-ttu-id="4dd17-156">[資料採礦演算法 &#40;Analysis Services 資料採礦&#41;](data-mining-algorithms-analysis-services-data-mining.md) [Microsoft 群集演算法技術參考](microsoft-clustering-algorithm-technical-reference.md)叢集[模型 &#40;Analysis Services-資料採礦&#41;](mining-model-content-for-clustering-models-analysis-services-data-mining.md) [群集模型查詢範例](clustering-model-query-examples.md)</span><span class="sxs-lookup"><span data-stu-id="4dd17-156">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) [Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md) [Mining Model Content for Clustering Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-clustering-models-analysis-services-data-mining.md) [Clustering Model Query Examples](clustering-model-query-examples.md)</span></span>


