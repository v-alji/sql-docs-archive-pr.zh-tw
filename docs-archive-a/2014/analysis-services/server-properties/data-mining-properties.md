---
title: 資料採礦屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ClusterCount property
- AllowedProvidersInOpenRowset property
- MinimumSeriesValue property
- ScoreMethod property
- MinimumImportance property
- ModellingCardinality property
- BrentTolerance property
- ComplexityPenalty property
- MaximumItemsetCount property
- MinimumSupport property
- AllowSessionMiningModels property
- HoldoutPercentage property
- ClusterCountPrior property
- MaximumSequenceStates property
- OptimizedPredictionCount property
- data mining [Analysis Services], properties
- MaximumStates property
- MaximumContinuousInputAttributes property
- MaximumOutputAttributes property
- AllowAdHocOpenRowsetQueries property
- Enabled property
- HistoricModelGap property
- SampleSize property
- MaximumInputAttributes property
- PeriodicityHint property
- MissingValueSubstitution property
- SplitMethod property
- ForceRegressor property
- MaximumBucketsForContinuousSplit property
- MaxConcurrentPredictionQueries property
- MinimumItemsetSize property
- AcyclicGraph property
- HoldoutMethod property
- StoppingTolerance property
- properties [data mining]
- AutoDetectPeriodicity property
- HoldoutTolerance property
- MinimumLeafCases property
- HoldoutSeed property
- MinimumClusterCases property
- ClusterCountDeviation property
- MinimumDependencyProbability property
- ClusteringMethod property
- MaximumItemsetSize property
- HiddenNodeRatio property
- MaximumSeriesValue property
ms.assetid: 9bc9abed-180a-4bd8-b2eb-89c62fa88110
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5ed1c47faafeb0c680e6afb6f8e509c426760da2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710869"
---
# <a name="data-mining-properties"></a><span data-ttu-id="e8208-102">資料採礦屬性</span><span class="sxs-lookup"><span data-stu-id="e8208-102">Data Mining Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="e8208-103">支援下表列出的資料採礦伺服器屬性。</span><span class="sxs-lookup"><span data-stu-id="e8208-103">supports the data mining server properties listed in the following tables.</span></span> <span data-ttu-id="e8208-104">如需有關其他伺服器屬性及如何設定伺服器屬性的詳細資訊，請參閱＜ [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e8208-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="e8208-105">**適用物件：** 僅限多維度伺服器模式</span><span class="sxs-lookup"><span data-stu-id="e8208-105">**Applies to:** Multidimensional server mode only</span></span>  
  
## <a name="non-specific-category"></a><span data-ttu-id="e8208-106">非特定類別目錄</span><span class="sxs-lookup"><span data-stu-id="e8208-106">Non-Specific Category</span></span>  
 `AllowSessionMiningModels`  
 <span data-ttu-id="e8208-107">此為布林值屬性，指出是否可以建立工作階段採礦模型。</span><span class="sxs-lookup"><span data-stu-id="e8208-107">A Boolean property that indicates whether session mining models can be created.</span></span>  
  
 <span data-ttu-id="e8208-108">此屬性的預設值為 False，表示無法建立工作階段採礦模型。</span><span class="sxs-lookup"><span data-stu-id="e8208-108">The default value for this property is false, which indicates that session mining models cannot be created.</span></span>  
  
 `AllowAdHocOpenRowsetQueries`  
 <span data-ttu-id="e8208-109">此為布林值屬性，指出是否允許特定開啟資料列集查詢。</span><span class="sxs-lookup"><span data-stu-id="e8208-109">A Boolean property that indicates whether adhoc open rowset queries are allowed.</span></span>  
  
 <span data-ttu-id="e8208-110">此屬性的預設值為 False，表示在工作階段期間不允許開啟資料列集查詢。</span><span class="sxs-lookup"><span data-stu-id="e8208-110">The default value for this property is false, which indicates that open rowset queries are not allowed during a session.</span></span>  
  
 `AllowedProvidersInOpenRowset`  
 <span data-ttu-id="e8208-111">此字串屬性會識別開啟的資料列集內所允許的提供者，其中會由提供者 ProgID 的逗號/分號分隔清單或是 [全部] 所組成。</span><span class="sxs-lookup"><span data-stu-id="e8208-111">A string property that identifies which providers are allowed in an open rowset, consisting of a comma/semi-colon separated list of provider ProgIDs, or else [All].</span></span>  
  
 `MaxConcurrentPredictionQueries`  
 <span data-ttu-id="e8208-112">此為帶正負號的 32 位元整數屬性，定義並行預測查詢的最大數目。</span><span class="sxs-lookup"><span data-stu-id="e8208-112">A signed 32-bit integer property that defines the maximum number of concurrent prediction queries.</span></span>  
  
## <a name="algorithms-category"></a><span data-ttu-id="e8208-113">演算法類別目錄</span><span class="sxs-lookup"><span data-stu-id="e8208-113">Algorithms Category</span></span>  
 `Microsoft_Association_Rules\ Enabled`  
 <span data-ttu-id="e8208-114">此為布林值屬性，指出是否啟用 Microsoft_Association_Rules 演算法。</span><span class="sxs-lookup"><span data-stu-id="e8208-114">A Boolean property that indicates whether the Microsoft_Association_Rules algorithm is enabled.</span></span>  
  
 `Microsoft_Clustering\ Enabled`  
 <span data-ttu-id="e8208-115">此為布林值屬性，指出是否啟用 Microsoft_Clustering 演算法。</span><span class="sxs-lookup"><span data-stu-id="e8208-115">A Boolean property that indicates whether the Microsoft_Clustering algorithm is enabled.</span></span>  
  
 `Microsoft_Decision_Trees\ Enabled`  
 <span data-ttu-id="e8208-116">此為布林值屬性，指出是否啟用 Microsoft_DecisionTrees 演算法。</span><span class="sxs-lookup"><span data-stu-id="e8208-116">A Boolean property that indicates whether the Microsoft_DecisionTrees algorithm is enabled.</span></span>  
  
 `Microsoft_Naive_Bayes\ Enabled`  
 <span data-ttu-id="e8208-117">此為布林值屬性，指出是否啟用 Microsoft_ Naive_Bayes 演算法。</span><span class="sxs-lookup"><span data-stu-id="e8208-117">A Boolean property that indicates whether the Microsoft_ Naive_Bayes algorithm is enabled.</span></span>  
  
 `Microsoft_Neural_Network\ Enabled`  
 <span data-ttu-id="e8208-118">此為布林值屬性，指出是否啟用 Microsoft_Neural_Network 演算法。</span><span class="sxs-lookup"><span data-stu-id="e8208-118">A Boolean property that indicates whether the Microsoft_Neural_Network algorithm is enabled.</span></span>  
  
 `Microsoft_Sequence_Clustering\ Enabled`  
 <span data-ttu-id="e8208-119">此為布林值屬性，指出是否啟用 Microsoft_Sequence_Clustering 演算法。</span><span class="sxs-lookup"><span data-stu-id="e8208-119">A Boolean property that indicates whether the Microsoft_Sequence_Clustering algorithm is enabled.</span></span>  
  
 `Microsoft_Time_Series\ Enabled`  
 <span data-ttu-id="e8208-120">此為布林值屬性，指出是否啟用 Microsoft_Time_Series 演算法。</span><span class="sxs-lookup"><span data-stu-id="e8208-120">A Boolean property that indicates whether the Microsoft_Time_Series algorithm is enabled.</span></span>  
  
 `Microsoft_Linear_Regression\ Enabled`  
 <span data-ttu-id="e8208-121">此為布林值屬性，指出是否啟用 Microsoft_Linear_Regression 演算法。</span><span class="sxs-lookup"><span data-stu-id="e8208-121">A Boolean property that indicates whether the Microsoft_Linear_Regression algorithm is enabled.</span></span>  
  
 `Microsoft_Logistic_Regression\ Enabled`  
 <span data-ttu-id="e8208-122">此為布林值屬性，指出是否啟用 Microsoft_Logistic_Regression 演算法。</span><span class="sxs-lookup"><span data-stu-id="e8208-122">A Boolean property that indicates whether the Microsoft_Logistic_Regression algorithm is enabled.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8208-123">除了定義伺服器上可用之資料採礦服務的屬性以外，還有其他資料採礦屬性可定義特定演算法的行為。</span><span class="sxs-lookup"><span data-stu-id="e8208-123">In addition to properties that define the data mining services available on the server, there are data mining properties that define the behavior of specific algorithms.</span></span> <span data-ttu-id="e8208-124">當您建立個別資料採礦模型時 (不在伺服器層級上)，可以設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="e8208-124">You configure these properties when you create an individual data mining model, not at the server level.</span></span> <span data-ttu-id="e8208-125">如需詳細資訊，請參閱[資料採礦演算法 &#40;Analysis Services - 資料採礦&#41;](../data-mining/data-mining-algorithms-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="e8208-125">For more information, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../data-mining/data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8208-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8208-126">See Also</span></span>  
 <span data-ttu-id="e8208-127">[實體架構 &#40;Analysis Services-資料採礦&#41;](../data-mining/physical-architecture-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="e8208-127">[Physical Architecture &#40;Analysis Services - Data Mining&#41;](../data-mining/physical-architecture-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="e8208-128">[在 Analysis Services 中設定伺服器屬性](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="e8208-128">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="e8208-129">判斷 Analysis Services 執行個體的伺服器模式</span><span class="sxs-lookup"><span data-stu-id="e8208-129">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
