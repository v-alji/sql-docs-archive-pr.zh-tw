---
title: 查看時間序列模型的公式 (資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- ARTXP
- time series algorithms [Analysis Services]
- ARIMA
- time series [Analysis Services]
- Time Series Viewer [Analysis Services]
ms.assetid: 825ef719-2f44-4979-be01-5a81f54e1a53
author: minewiskan
ms.author: owend
ms.openlocfilehash: eff61c469d34f084e6a0eb11c49a1c37c7cc97c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584820"
---
# <a name="view-the-formula-for-a-time-series-model-data-mining"></a><span data-ttu-id="7d765-102">檢視時間序列模型的公式 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="7d765-102">View the Formula for a Time Series Model (Data Mining)</span></span>
  <span data-ttu-id="7d765-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]時間序列檢視器 inData 的「挖掘設計師」提供最簡單的方式來查看時間序列模型中所使用之回歸方程式的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="7d765-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series viewer inData Mining Designer provides the easiest way to view the details of the regression equation used in a time series model.</span></span>  
  
 <span data-ttu-id="7d765-104">您可以查詢模型內容來擷取時間序列模型的迴歸公式。</span><span class="sxs-lookup"><span data-stu-id="7d765-104">You can extract the regression formula for a time series model by querying the model content.</span></span> <span data-ttu-id="7d765-105">不過，若要查看完整的 ARTXP 或 ARIMA 公式，建議您使用[Microsoft 時間序列檢視器](browse-a-model-using-the-microsoft-time-series-viewer.md)的 [**挖掘圖例**]，這會以可讀取的格式呈現所有常數。</span><span class="sxs-lookup"><span data-stu-id="7d765-105">However, to view the complete ARTXP or ARIMA formula, we recommend that you use the **Mining Legend** of the [Microsoft Time Series Viewer](browse-a-model-using-the-microsoft-time-series-viewer.md), which presents all the constants in a readable format.</span></span>  
  
 <span data-ttu-id="7d765-106">如果您建立混合模型，則會在不同的樹狀目錄中建立 ARIMA 和 ARTXP 分析，並且在表示模型的根節點處聯結。</span><span class="sxs-lookup"><span data-stu-id="7d765-106">If you create a mixed model, the ARIMA and ARTXP analyses are created in separate trees, joined at the root node representing the model.</span></span> <span data-ttu-id="7d765-107">ARIMA 和 ARTXP 樹狀目錄的結構差異很大。</span><span class="sxs-lookup"><span data-stu-id="7d765-107">The structures of the ARIMA and ARTXP trees are very different.</span></span> <span data-ttu-id="7d765-108">例如，ARTXP 樹狀目錄實際上是一種樹狀結構，類似決策樹，而 ARIMA 樹狀目錄則表示一系列移動平均。</span><span class="sxs-lookup"><span data-stu-id="7d765-108">For example, the ARTXP tree is in fact a tree structure, like a decision tree, whereas the ARIMA tree represents a series of moving averages.</span></span> <span data-ttu-id="7d765-109">因此，雖然這兩種表示法是為求方便而以單一模型呈現，不過您應該將它們視為兩個獨立的模型。</span><span class="sxs-lookup"><span data-stu-id="7d765-109">Therefore, although the two representations are presented in one model for convenience, they should be treated as two independent models.</span></span> <span data-ttu-id="7d765-110">兩個方程式也完全不同，而且無法結合或比較。</span><span class="sxs-lookup"><span data-stu-id="7d765-110">The equations are also completely different and cannot be combined or compared.</span></span>  
  
 <span data-ttu-id="7d765-111">您也可以使用 [ [Microsoft 一般內容樹狀檢視器]](../microsoft-generic-content-tree-viewer-data-mining.md)來查看時間序列模型。</span><span class="sxs-lookup"><span data-stu-id="7d765-111">You can also view time series models by using the [Microsoft Generic Content Tree Viewer](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span> <span data-ttu-id="7d765-112">如需時間序列模型內容的詳細資訊，請參閱[時間序列模型的採礦模型內容 &#40;Analysis Services 資料採礦&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="7d765-112">For more information about the content of a time series model, see [Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md).</span></span>  
  
### <a name="to-view-the-artxp-regression-formula-for-a-time-series-model"></a><span data-ttu-id="7d765-113">檢視時間序列模式的 ARTXP 迴歸公式</span><span class="sxs-lookup"><span data-stu-id="7d765-113">To view the ARTXP regression formula for a time series model</span></span>  
  
1.  <span data-ttu-id="7d765-114">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，選取您要檢視的時間序列模型，然後按一下 [瀏覽]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7d765-114">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the time series model that you want to view, and click **Browse**.</span></span>  
  
     <span data-ttu-id="7d765-115">-- 或 --</span><span class="sxs-lookup"><span data-stu-id="7d765-115">-- or --</span></span>  
  
     <span data-ttu-id="7d765-116">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，選取時間序列模型，然後按一下 [採礦模型檢視器]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7d765-116">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select the time series model, and then click the **Mining Model Viewer** tab.</span></span>  
  
2.  <span data-ttu-id="7d765-117">按一下 [模型] \*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7d765-117">Click the **Model** tab.</span></span>  
  
3.  <span data-ttu-id="7d765-118">如果模型包含多個樹狀結構，請從 [樹狀結構]\*\*\*\* 下拉式清單中選取一個單一樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="7d765-118">If the model contains multiple trees, select a single tree from the **Tree** drop-down list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7d765-119">如果您擁有一個以上的資料數列，模型將永遠包含多個樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="7d765-119">A model will always have multiple trees if you have more than one data series.</span></span> <span data-ttu-id="7d765-120">不過，您在時間序列檢視器\*\*\*\* 中看到的樹狀結構數目，會比 [Microsoft 一般內容樹狀檢視器](../microsoft-generic-content-tree-viewer-data-mining.md)中的少。</span><span class="sxs-lookup"><span data-stu-id="7d765-120">However, you will not see as many trees in the **Time Series viewer** as you will see in the [Microsoft Generic Content Tree Viewer](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span> <span data-ttu-id="7d765-121">這是因為時間序列檢視器會將每個資料數列的 ARIMA 和 ARTXP 資訊結合為單一表示法。</span><span class="sxs-lookup"><span data-stu-id="7d765-121">That is because the Time Series viewer combines the ARIMA and ARTXP information for each data series into a single representation.</span></span>  
  
4.  <span data-ttu-id="7d765-122">按一下樹狀結構中的任何分葉節點。</span><span class="sxs-lookup"><span data-stu-id="7d765-122">Click any leaf node in the tree.</span></span>  
  
     <span data-ttu-id="7d765-123">標示為 [資料數列]\*\*\*\* 的節點永遠是分葉節點，而且可以包含一個方程式。</span><span class="sxs-lookup"><span data-stu-id="7d765-123">Nodes that are labeled as **Data Series** are always leaf nodes and can contain an equation.</span></span> <span data-ttu-id="7d765-124">如果 **(All)** 節點沒有子節點，它也可以包含一個方程式。</span><span class="sxs-lookup"><span data-stu-id="7d765-124">If an **(All)** node has no child nodes, it can also contain an equation.</span></span>  
  
5.  <span data-ttu-id="7d765-125">如果沒有可用的 [採礦圖例]\*\*\*\*，以滑鼠右鍵按一下節點，然後選取 [顯示圖例]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7d765-125">If the **Mining Legend** is not available, right-click the node, and select **Show Legend**.</span></span>  
  
     <span data-ttu-id="7d765-126">ARTXP 公式會顯示在 [採礦圖例]\*\*\*\* 的前半部，當作 [樹狀節點方程式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7d765-126">The ARTXP formula is displayed in the first half of the **Mining Legend**, as the **Tree node equation**.</span></span>  
  
### <a name="to-view-the-arima-formula-for-a-time-series-model"></a><span data-ttu-id="7d765-127">檢視時間序列模式的 ARIMA 公式</span><span class="sxs-lookup"><span data-stu-id="7d765-127">To view the ARIMA formula for a time series model</span></span>  
  
1.  <span data-ttu-id="7d765-128">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，選取您要檢視的時間序列模型，然後按一下 [瀏覽]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7d765-128">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the time series model that you want to view, and click **Browse**.</span></span>  
  
     <span data-ttu-id="7d765-129">-- 或 --</span><span class="sxs-lookup"><span data-stu-id="7d765-129">-- or --</span></span>  
  
     <span data-ttu-id="7d765-130">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，選取時間序列模型，然後按一下 [採礦模型檢視器]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7d765-130">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], select the time series model, and then click the **Mining Model Viewer** tab.</span></span>  
  
2.  <span data-ttu-id="7d765-131">按一下 [模型] \*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7d765-131">Click the **Model** tab.</span></span>  
  
3.  <span data-ttu-id="7d765-132">如果模型包含多個樹狀結構，請從 [樹狀結構]\*\*\*\* 下拉式清單中選取一個單一樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="7d765-132">If the model contains multiple trees, select a single tree from the **Tree** drop-down list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7d765-133">如果您加入一個以上的資料數列，此模型將永遠有多個樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="7d765-133">The model will always have multiple trees if you include more than one data series.</span></span>  
  
4.  <span data-ttu-id="7d765-134">按一下樹狀結構中的任何節點。</span><span class="sxs-lookup"><span data-stu-id="7d765-134">Click any node in the tree.</span></span>  
  
     <span data-ttu-id="7d765-135">ARIMA 公式會顯示在 [採礦圖例]\*\*\*\* 的後半部，當作 [ARIMA 方程式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7d765-135">The ARIMA formula is displayed in the second half of the **Mining Legend**, as the **ARIMA equation**.</span></span>  
  
5.  <span data-ttu-id="7d765-136">如果沒有可用的 [採礦圖例]\*\*\*\*，以滑鼠右鍵按一下節點，然後選取 [顯示圖例]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7d765-136">If the **Mining Legend** is not available, right-click the node, and select **Show Legend**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d765-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d765-137">See Also</span></span>  
 <span data-ttu-id="7d765-138">[採礦模型檢視器工作和操作說明](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="7d765-138">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="7d765-139">[使用 Microsoft 時間序列檢視器流覽模型](browse-a-model-using-the-microsoft-time-series-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="7d765-139">[Browse a Model Using the Microsoft Time Series Viewer](browse-a-model-using-the-microsoft-time-series-viewer.md) </span></span>  
 [<span data-ttu-id="7d765-140">時間序列模型查詢範例</span><span class="sxs-lookup"><span data-stu-id="7d765-140">Time Series Model Query Examples</span></span>](time-series-model-query-examples.md)  
  
  
