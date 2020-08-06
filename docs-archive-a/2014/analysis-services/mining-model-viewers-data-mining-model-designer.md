---
title: " (資料採礦模型設計師) 的採礦模型檢視器 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.viewers.f1
ms.assetid: 4ba391d5-c97b-4848-ba7c-7d096fa4b7dd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4cc1c9d72a08ef49ed2f4f466953d2ba61394178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707953"
---
# <a name="mining-model-viewers-data-mining-model-designer"></a><span data-ttu-id="06b4a-102">採礦模型檢視器 (資料採礦模型設計師)</span><span class="sxs-lookup"><span data-stu-id="06b4a-102">Mining Model Viewers (Data Mining Model Designer)</span></span>
  <span data-ttu-id="06b4a-103">使用 **[採礦模型檢視器]** 索引標籤，即可瀏覽採礦結構所包含的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="06b4a-103">Use the **Mining Model Viewer** tab to explore the mining models that a mining structure contains.</span></span>

 <span data-ttu-id="06b4a-104">您要先選取採礦模型，然後再選取檢視器。</span><span class="sxs-lookup"><span data-stu-id="06b4a-104">First you select the mining model and then you select a viewer.</span></span> <span data-ttu-id="06b4a-105">每一個模型一定都有兩個可用的檢視器：自訂檢視器 (可包含多個索引標籤) 和一般檢視器。</span><span class="sxs-lookup"><span data-stu-id="06b4a-105">Each model always has two viewers available: a custom viewer, which can include multiple tabs, and the generic viewer.</span></span>

 <span data-ttu-id="06b4a-106">如需如何使用每個檢視器的逐步解說，請參閱 [資料採礦模型檢視器](data-mining/data-mining-model-viewers.md)。</span><span class="sxs-lookup"><span data-stu-id="06b4a-106">For a walkthrough of how to use each viewer, see [Data Mining Model Viewers](data-mining/data-mining-model-viewers.md).</span></span>

## <a name="common-options"></a><span data-ttu-id="06b4a-107">一般選項</span><span class="sxs-lookup"><span data-stu-id="06b4a-107">Common Options</span></span>
 <span data-ttu-id="06b4a-108">**重新整理檢視器內容** 在檢視器中重新載入採礦模型。</span><span class="sxs-lookup"><span data-stu-id="06b4a-108">**Refresh viewer content** Reload the mining model in the viewer.</span></span>

 <span data-ttu-id="06b4a-109">**採礦模型** 選擇包含在目前採礦結構中，您要檢視的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="06b4a-109">**Mining Model** Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="06b4a-110">採礦模型將會先在其關聯的自訂檢視器中開啟。</span><span class="sxs-lookup"><span data-stu-id="06b4a-110">The mining model will first open in its associated custom viewer.</span></span>

 <span data-ttu-id="06b4a-111">**檢視器** 選擇用來瀏覽選取之採礦模型的檢視器。</span><span class="sxs-lookup"><span data-stu-id="06b4a-111">**Viewer** Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="06b4a-112">這份清單包含 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 為每個採礦模型提供的查看 [!INCLUDE[msCoName](../includes/msconame-md.md)] 器、挖掘內容檢視器，以及任何外掛程式檢視器。</span><span class="sxs-lookup"><span data-stu-id="06b4a-112">This list includes the viewers that [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides for each mining model, the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer, and any plug-in viewers.</span></span>

 <span data-ttu-id="06b4a-113">下圖顯示相同模型的自訂檢視器和一般檢視器。</span><span class="sxs-lookup"><span data-stu-id="06b4a-113">The following diagram shows a custom viewer and the generic viewer for the same model.</span></span>

-   <span data-ttu-id="06b4a-114">上方圖表顯示以 Microsoft 時間序列演算法為基礎之採礦模型的檢視器。</span><span class="sxs-lookup"><span data-stu-id="06b4a-114">The upper diagram shows the viewer for a mining model based on the Microsoft Time Series algorithm.</span></span> <span data-ttu-id="06b4a-115">這個特定自訂檢視器會自動建立時間序列的圖形，並提供五個預測。</span><span class="sxs-lookup"><span data-stu-id="06b4a-115">This particular custom viewer automatically creates a graph of the time series and provides five predictions.</span></span>

-   <span data-ttu-id="06b4a-116">下方圖表顯示使用 **[Microsoft 一般內容樹狀檢視器]** 時所顯示的相同模型。</span><span class="sxs-lookup"><span data-stu-id="06b4a-116">The lower diagram shows the same model displayed using the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="06b4a-117">此檢視器會根據標準化結構描述呈現採礦模型的內容。</span><span class="sxs-lookup"><span data-stu-id="06b4a-117">This viewer presents the contents of the mining model according to a standardized schema.</span></span> <span data-ttu-id="06b4a-118">如需詳細資訊，請參閱 [Microsoft 一般內容樹狀檢視器 &#40;資料採礦&#41;](microsoft-generic-content-tree-viewer-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="06b4a-118">For more information, see [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](microsoft-generic-content-tree-viewer-data-mining.md).</span></span>

 <span data-ttu-id="06b4a-119">![採礦模型設計工具的概觀](media/generic-mining-model-tab1.gif "採礦模型設計工具的概觀")</span><span class="sxs-lookup"><span data-stu-id="06b4a-119">![Overview of mining model designer](media/generic-mining-model-tab1.gif "Overview of mining model designer")</span></span>

## <a name="viewers-and-their-components"></a><span data-ttu-id="06b4a-120">檢視器及其元件</span><span class="sxs-lookup"><span data-stu-id="06b4a-120">Viewers and Their Components</span></span>
 <span data-ttu-id="06b4a-121">根據您所選取的模型，將會看見不同的自訂檢視器，而且它會依照您用來建立選定資料採礦模型的演算法而訂製。</span><span class="sxs-lookup"><span data-stu-id="06b4a-121">Depending on the model that you select, you will see a different custom viewer, tailored to the algorithm that you used to create the selected data mining model.</span></span> <span data-ttu-id="06b4a-122">每一個自訂檢視器都有各種工具和對話方塊，可幫助您瀏覽模型中的統計資料和模式。</span><span class="sxs-lookup"><span data-stu-id="06b4a-122">Each custom viewer has a variety of tools and dialog boxes for helping you explore the statistics and patterns in the model.</span></span>

 <span data-ttu-id="06b4a-123">下列清單描述的是每個自訂檢視器中的選項。</span><span class="sxs-lookup"><span data-stu-id="06b4a-123">The following list describes the options in each of the custom viewers.</span></span>

### <a name="microsoft-association-rules-algorithm"></a><span data-ttu-id="06b4a-124">Microsoft 關聯規則演算法</span><span class="sxs-lookup"><span data-stu-id="06b4a-124">Microsoft Association Rules Algorithm</span></span>

-   [<span data-ttu-id="06b4a-125">使用 Microsoft 關聯規則檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="06b4a-125">Browse a Model Using the Microsoft Association Rules Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)

    -   <span data-ttu-id="06b4a-126">[專案集索引標籤 &#40;&#41;的 [採礦模型檢視器]](itemsets-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-126">[Itemsets Tab &#40;Mining Model Viewer&#41;](itemsets-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="06b4a-127">[[規則] 索引標籤 &#40;&#41;的採礦模型檢視器](rules-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-127">[Rules Tab &#40;Mining Model Viewer&#41;](rules-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="06b4a-128">[[相依性網路] 索引標籤 &#40;&#41;的採礦模型檢視器](dependency-network-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-128">[Dependency Network Tab &#40;Mining Model Viewer&#41;](dependency-network-tab-mining-model-viewer.md)</span></span>

### <a name="microsoft-clustering-algorithm"></a><span data-ttu-id="06b4a-129">Microsoft 群集演算法</span><span class="sxs-lookup"><span data-stu-id="06b4a-129">Microsoft Clustering Algorithm</span></span>

-   [<span data-ttu-id="06b4a-130">使用 Microsoft 叢集檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="06b4a-130">Browse a Model Using the Microsoft Cluster Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)

    -   <span data-ttu-id="06b4a-131">[[叢集圖表] 索引標籤 &#40;[採礦模型檢視器]&#41;](cluster-diagram-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-131">[Cluster Diagram Tab &#40;Mining Model Viewer&#41;](cluster-diagram-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="06b4a-132">[[叢集設定檔] 索引標籤 &#40;&#41;的採礦模型檢視器](cluster-profiles-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-132">[Cluster Profiles Tab &#40;Mining Model Viewer&#41;](cluster-profiles-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="06b4a-133">[[叢集特性] 索引標籤 &#40;[採礦模型檢視器]&#41;](cluster-characteristics-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-133">[Cluster Characteristics Tab &#40;Mining Model Viewer&#41;](cluster-characteristics-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="06b4a-134">[&#40;採礦模型檢視器&#41;的 [叢集辨識] 索引標籤](cluster-discrimination-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-134">[Cluster Discrimination Tab &#40;Mining Model Viewer&#41;](cluster-discrimination-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="06b4a-135">[[挖掘圖例] 對話方塊 &#40;[採礦模型檢視器]&#41;](mining-legend-dialog-box-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-135">[Mining Legend Dialog Box &#40;Mining Model Viewer&#41;](mining-legend-dialog-box-mining-model-viewer.md)</span></span>

### <a name="microsoft-decision-tree-algorithm"></a><span data-ttu-id="06b4a-136">Microsoft 決策樹演算法</span><span class="sxs-lookup"><span data-stu-id="06b4a-136">Microsoft Decision Tree Algorithm</span></span>

-   [<span data-ttu-id="06b4a-137">使用 Microsoft 樹狀檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="06b4a-137">Browse a Model Using the Microsoft Tree Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)

    -   <span data-ttu-id="06b4a-138">[[決策樹] 索引標籤 &#40;[採礦模型檢視器]&#41;](decision-tree-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-138">[Decision Tree Tab &#40;Mining Model Viewer&#41;](decision-tree-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="06b4a-139">[[相依性網路] 索引標籤 &#40;&#41;的採礦模型檢視器](dependency-network-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-139">[Dependency Network Tab &#40;Mining Model Viewer&#41;](dependency-network-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="06b4a-140">[[挖掘圖例] 對話方塊 &#40;[採礦模型檢視器]&#41;](mining-legend-dialog-box-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-140">[Mining Legend Dialog Box &#40;Mining Model Viewer&#41;](mining-legend-dialog-box-mining-model-viewer.md)</span></span>

### <a name="microsoft-linear-regression-algorithm"></a><span data-ttu-id="06b4a-141">Microsoft 線性迴歸演算法</span><span class="sxs-lookup"><span data-stu-id="06b4a-141">Microsoft Linear Regression Algorithm</span></span>

-   [<span data-ttu-id="06b4a-142">使用 Microsoft 類神經網路檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="06b4a-142">Browse a Model Using the Microsoft Neural Network Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)

    -   <span data-ttu-id="06b4a-143">[[決策樹] 索引標籤 &#40;[採礦模型檢視器]&#41;](decision-tree-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-143">[Decision Tree Tab &#40;Mining Model Viewer&#41;](decision-tree-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="06b4a-144">[[相依性網路] 索引標籤 &#40;&#41;的採礦模型檢視器](dependency-network-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-144">[Dependency Network Tab &#40;Mining Model Viewer&#41;](dependency-network-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="06b4a-145">[[挖掘圖例] 對話方塊 &#40;[採礦模型檢視器]&#41;](mining-legend-dialog-box-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-145">[Mining Legend Dialog Box &#40;Mining Model Viewer&#41;](mining-legend-dialog-box-mining-model-viewer.md)</span></span>

### <a name="microsoft-logistic-regression-algorithm"></a><span data-ttu-id="06b4a-146">Microsoft 羅吉斯迴歸演算法</span><span class="sxs-lookup"><span data-stu-id="06b4a-146">Microsoft Logistic Regression Algorithm</span></span>

-   [<span data-ttu-id="06b4a-147">使用 Microsoft 類神經網路檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="06b4a-147">Browse a Model Using the Microsoft Neural Network Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)

### <a name="microsoft-nave-bayes-algorithm"></a><span data-ttu-id="06b4a-148">Microsoft 貝氏機率分類演算法</span><span class="sxs-lookup"><span data-stu-id="06b4a-148">Microsoft Naïve Bayes Algorithm</span></span>

-   [<span data-ttu-id="06b4a-149">使用 Microsoft 貝氏機率分類檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="06b4a-149">Browse a Model Using the Microsoft Naive Bayes Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)

    -   <span data-ttu-id="06b4a-150">[[相依性網路] 索引標籤 &#40;&#41;的採礦模型檢視器](dependency-network-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-150">[Dependency Network Tab &#40;Mining Model Viewer&#41;](dependency-network-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="06b4a-151">[[屬性設定檔] 索引標籤 &#40;[採礦模型檢視器&#41;](attribute-profiles-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-151">[Attribute Profiles Tab &#40;Mining Model Viewer&#41;](attribute-profiles-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="06b4a-152">[[屬性特性] 索引標籤 &#40;[採礦模型檢視器]&#41;](attribute-characteristics-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-152">[Attribute Characteristics Tab &#40;Mining Model Viewer&#41;](attribute-characteristics-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="06b4a-153">[[屬性辨識] 索引標籤 &#40;[採礦模型檢視器]&#41;](attribute-discrimination-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-153">[Attribute Discrimination Tab &#40;Mining Model Viewer&#41;](attribute-discrimination-tab-mining-model-viewer.md)</span></span>

### <a name="microsoft-neural-network-algorithm"></a><span data-ttu-id="06b4a-154">Microsoft Neural Network Algorithm</span><span class="sxs-lookup"><span data-stu-id="06b4a-154">Microsoft Neural Network Algorithm</span></span>

-   [<span data-ttu-id="06b4a-155">使用 Microsoft 類神經網路檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="06b4a-155">Browse a Model Using the Microsoft Neural Network Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)

    -   <span data-ttu-id="06b4a-156">[[相依性網路] 索引標籤 &#40;&#41;的採礦模型檢視器](dependency-network-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-156">[Dependency Network Tab &#40;Mining Model Viewer&#41;](dependency-network-tab-mining-model-viewer.md)</span></span>

    -   [<span data-ttu-id="06b4a-157">類神經網路 &#40;採礦模型檢視器&#41;</span><span class="sxs-lookup"><span data-stu-id="06b4a-157">Neural Network &#40;Mining Model Viewer&#41;</span></span>](neural-network-mining-model-viewer.md)

    -   <span data-ttu-id="06b4a-158">[[尋找節點] 對話方塊 &#40;[採礦模型檢視器]&#41;](find-node-dialog-box-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-158">[Find Node Dialog Box &#40;Mining Model Viewer&#41;](find-node-dialog-box-mining-model-viewer.md)</span></span>

### <a name="microsoft-sequence-clustering-algorithm"></a><span data-ttu-id="06b4a-159">Microsoft 時序叢集演算法</span><span class="sxs-lookup"><span data-stu-id="06b4a-159">Microsoft Sequence Clustering Algorithm</span></span>

-   [<span data-ttu-id="06b4a-160">使用 Microsoft 時序叢集檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="06b4a-160">Browse a Model Using the Microsoft Sequence Cluster Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)

    -   <span data-ttu-id="06b4a-161">[時序群集叢集圖表索引標籤 &#40;[採礦模型檢視器]](sequence-clustering-cluster-diagram-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-161">[Sequence Clustering Cluster Diagram Tab &#40;Mining Model Viewer](sequence-clustering-cluster-diagram-tab-mining-model-viewer.md)</span></span>

    -   <span data-ttu-id="06b4a-162">[時序群集 [叢集設定檔] 索引標籤 &#40;[採礦模型檢視器]](sequence-clustering-cluster-profiles-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-162">[Sequence Clustering Cluster Profiles Tab &#40;Mining Model Viewer](sequence-clustering-cluster-profiles-tab-mining-model-viewer.md)</span></span>

    -   [<span data-ttu-id="06b4a-163">時序群集叢集特性索引標籤 &#40;採礦模型檢視器&#41;</span><span class="sxs-lookup"><span data-stu-id="06b4a-163">Sequence Clustering Cluster Characteristics Tab &#40;Mining Model Viewer&#41;</span></span>](sequence-clustering-cluster-characteristics-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="06b4a-164">時序群集叢集辨識索引標籤 &#40;採礦模型檢視器&#41;</span><span class="sxs-lookup"><span data-stu-id="06b4a-164">Sequence Clustering Cluster Discrimination Tab &#40;Mining Model Viewer&#41;</span></span>](sequence-clustering-cluster-discrimination-tab-mining-model-viewer.md)

    -   <span data-ttu-id="06b4a-165">[時序群集 [叢集轉換] 索引標籤 &#40;&#41;的採礦模型檢視器](sequence-clustering-cluster-transition-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-165">[Sequence Clustering Cluster Transition Tab &#40;Mining Model Viewer&#41;](sequence-clustering-cluster-transition-tab-mining-model-viewer.md)</span></span>

### <a name="microsoft-time-series-algorithm"></a><span data-ttu-id="06b4a-166">Microsoft 時間序列演算法</span><span class="sxs-lookup"><span data-stu-id="06b4a-166">Microsoft Time Series Algorithm</span></span>

-   [<span data-ttu-id="06b4a-167">使用 Microsoft 時間序列檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="06b4a-167">Browse a Model Using the Microsoft Time Series Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md)

    -   [<span data-ttu-id="06b4a-168">模型索引標籤 &#40;採礦模型檢視器&#41;</span><span class="sxs-lookup"><span data-stu-id="06b4a-168">Model Tab &#40;Mining Model Viewers&#41;</span></span>](model-tab-mining-model-viewers.md)

    -   <span data-ttu-id="06b4a-169">[[圖表] 索引標籤 &#40;採礦模型檢視器&#41;](chart-tab-mining-model-viewers.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-169">[Chart Tab &#40;Mining Model Viewers&#41;](chart-tab-mining-model-viewers.md)</span></span>

    -   <span data-ttu-id="06b4a-170">[[挖掘圖例] 對話方塊 &#40;[採礦模型檢視器]&#41;](mining-legend-dialog-box-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-170">[Mining Legend Dialog Box &#40;Mining Model Viewer&#41;](mining-legend-dialog-box-mining-model-viewer.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="06b4a-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06b4a-171">See Also</span></span>
 <span data-ttu-id="06b4a-172">[採礦模型 view &#40;資料採礦模型設計工具&#41;](mining-models-view-data-mining-model-designer.md) [&#40;資料採礦模型設計工具&#41;](mining-structure-view-data-mining-model-designer.md) [挖掘精確度圖表設計工具 &#40;資料採礦&#41;](mining-accuracy-chart-designer-data-mining.md) [預測查詢產生器 &#40;資料採礦&#41;](prediction-query-builder-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="06b4a-172">[Mining Models View &#40;Data Mining Model Designer&#41;](mining-models-view-data-mining-model-designer.md) [Mining Structure View &#40;Data Mining Model Designer&#41;](mining-structure-view-data-mining-model-designer.md) [Mining Accuracy Chart Designer &#40;Data Mining&#41;](mining-accuracy-chart-designer-data-mining.md) [Prediction Query Builder &#40;Data Mining&#41;](prediction-query-builder-data-mining.md)</span></span>


