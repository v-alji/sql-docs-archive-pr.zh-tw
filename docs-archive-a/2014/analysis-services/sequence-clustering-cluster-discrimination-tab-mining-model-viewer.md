---
title: 時序群集叢集辨識索引標籤 (採礦模型檢視器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.discrimination.f1
ms.assetid: 7dd16479-2633-4f4b-83bf-cf55972a2241
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9839a6185933fd87929331558ed63c1d81c6a748
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710885"
---
# <a name="sequence-clustering-cluster-discrimination-tab-mining-model-viewer"></a><span data-ttu-id="f4938-102">時序叢集的叢集辨識索引標籤 (採礦模型檢視器)</span><span class="sxs-lookup"><span data-stu-id="f4938-102">Sequence Clustering Cluster Discrimination Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="f4938-103">[Microsoft 時序叢集檢視器]\*\*\*\* 中的 [叢集辨識]\*\*\*\* 索引標籤可比較時序叢集模型中的選定叢集。</span><span class="sxs-lookup"><span data-stu-id="f4938-103">The  **Cluster Discrimination** tab in the **Microsoft Sequence Clustering Viewer** compares selected clusters from a sequence clustering model.</span></span>  
  
 <span data-ttu-id="f4938-104">可以使用此時序叢集模型檢視，比較兩個叢集並查看哪些狀態和轉換是不同的。</span><span class="sxs-lookup"><span data-stu-id="f4938-104">Use this view of a sequence clustering model to compare two clusters and see which states and transitions are different.</span></span>  
  
 <span data-ttu-id="f4938-105">\*\*如需詳細資訊，請參閱 \*\* [Microsoft 時序叢集演算法](data-mining/microsoft-sequence-clustering-algorithm.md)、[使用 Microsoft 時序叢集檢視器瀏覽模型](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="f4938-105">**For More Information:** [Microsoft Sequence Clustering Algorithm](data-mining/microsoft-sequence-clustering-algorithm.md), [Browse a Model Using the Microsoft Sequence Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="f4938-106">選項</span><span class="sxs-lookup"><span data-stu-id="f4938-106">Options</span></span>  
 <span data-ttu-id="f4938-107">**重新整理檢視器內容**</span><span class="sxs-lookup"><span data-stu-id="f4938-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="f4938-108">在檢視器中重新載入採礦模型。</span><span class="sxs-lookup"><span data-stu-id="f4938-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="f4938-109">**採礦模型**</span><span class="sxs-lookup"><span data-stu-id="f4938-109">**Mining Model**</span></span>  
 <span data-ttu-id="f4938-110">選擇包含在目前採礦結構中，您要檢視的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="f4938-110">Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="f4938-111">採礦模型會在其關聯的檢視器中開啟。</span><span class="sxs-lookup"><span data-stu-id="f4938-111">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="f4938-112">**檢視者**</span><span class="sxs-lookup"><span data-stu-id="f4938-112">**Viewer**</span></span>  
 <span data-ttu-id="f4938-113">選擇用來瀏覽選取之採礦模型的檢視器。</span><span class="sxs-lookup"><span data-stu-id="f4938-113">Choose a viewer to use in exploring the selected mining model.</span></span> <span data-ttu-id="f4938-114">可以使用自訂檢視器，或 **[Microsoft 一般內容樹狀檢視器]**。</span><span class="sxs-lookup"><span data-stu-id="f4938-114">You can use the custom viewer, or the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="f4938-115">還可以使用外掛程式檢視器 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="f4938-115">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="f4938-116">**叢集 1**</span><span class="sxs-lookup"><span data-stu-id="f4938-116">**Cluster 1**</span></span>  
 <span data-ttu-id="f4938-117">在模型中選取叢集。</span><span class="sxs-lookup"><span data-stu-id="f4938-117">Select a cluster from those in the model.</span></span>  
  
 <span data-ttu-id="f4938-118">**群集 2**</span><span class="sxs-lookup"><span data-stu-id="f4938-118">**Cluster 2**</span></span>  
 <span data-ttu-id="f4938-119">在採礦模型中選取第二個叢集來與 **叢集 1**進行比較。</span><span class="sxs-lookup"><span data-stu-id="f4938-119">Select a second cluster in the mining model, to compare to **Cluster 1**.</span></span>  
  
 <span data-ttu-id="f4938-120">如果您未選取其他叢集，則根據預設，所選叢集會與其補數 (表示模型中不屬於叢集 1 的所有案例) 進行比較。</span><span class="sxs-lookup"><span data-stu-id="f4938-120">If you do not select another cluster, by default the selected cluster is compared to its complement, meaning all cases in the model that are not in Cluster 1.</span></span>  
  
 <span data-ttu-id="f4938-121">**和的辨識分數 \<cluster 1>\<cluster 2>**</span><span class="sxs-lookup"><span data-stu-id="f4938-121">**Discrimination scores for \<cluster 1> and \<cluster 2>**</span></span>  
 <span data-ttu-id="f4938-122">此圖表提供所選叢集的詳細比較。</span><span class="sxs-lookup"><span data-stu-id="f4938-122">This chart provides the detailed comparison of the clusters that you selected.</span></span> <span data-ttu-id="f4938-123">一般情況下，叢集模型很少以獨佔方式為單一叢集指派狀態或值。</span><span class="sxs-lookup"><span data-stu-id="f4938-123">In general, a clustering model rarely assigns states or values exclusively to a single cluster.</span></span> <span data-ttu-id="f4938-124">因此，檢視器只表示特定屬性或狀態「喜好」\*\* 某個特定叢集。</span><span class="sxs-lookup"><span data-stu-id="f4938-124">Therefore, the viewer indicates only that a particular attribute or state *favors* a particular cluster.</span></span>  
  
 <span data-ttu-id="f4938-125">整體而言，特定叢集可能主要包含某個狀態：例如，常見狀態可能為依序購買 Water Bottle 和 Water Bottle Cage。</span><span class="sxs-lookup"><span data-stu-id="f4938-125">Overall, a certain cluster might contain more of one state: for example, a common state might be the purchase of a Water Bottle and Water Bottle Cage in sequence.</span></span> <span data-ttu-id="f4938-126">但是，此順序可能存在於其他有更重要定義特性的叢集中。</span><span class="sxs-lookup"><span data-stu-id="f4938-126">However, the sequence might be present in other clusters that have more important defining characteristics.</span></span> <span data-ttu-id="f4938-127">例如，另一個叢集的最主要特性可能是交易時間非常短，並且分析顯示，Water Bottle 和 Water Bottle Cage 項目可能通常分組到此叢集中，但並非總是這樣。</span><span class="sxs-lookup"><span data-stu-id="f4938-127">For example, another cluster might be characterized most strongly by very short transaction times, and an analysis would reveal that [Water Bottle and Waterthe items are positioned to might usually be grouped in this cluster, but not always.</span></span>  
  
|<span data-ttu-id="f4938-128">值</span><span class="sxs-lookup"><span data-stu-id="f4938-128">Value</span></span>|<span data-ttu-id="f4938-129">描述</span><span class="sxs-lookup"><span data-stu-id="f4938-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f4938-130">**變數**</span><span class="sxs-lookup"><span data-stu-id="f4938-130">**Variables**</span></span>|<span data-ttu-id="f4938-131">採礦模型中的屬性。</span><span class="sxs-lookup"><span data-stu-id="f4938-131">An attribute in the mining model.</span></span>|  
|<span data-ttu-id="f4938-132">**值**</span><span class="sxs-lookup"><span data-stu-id="f4938-132">**Values**</span></span>|<span data-ttu-id="f4938-133">[變數]\*\*\*\* 中列出之屬性的狀態。</span><span class="sxs-lookup"><span data-stu-id="f4938-133">A state of the attribute that is listed in **Variables**.</span></span>|  
|<span data-ttu-id="f4938-134">**照顧\<cluster 1>**</span><span class="sxs-lookup"><span data-stu-id="f4938-134">**Favors \<cluster 1>**</span></span>|<span data-ttu-id="f4938-135">包含陰影長條，表示 [變數]\*\*\*\* 和 [值]\*\*\*\* 中列出的屬性和狀態喜好 [叢集 1]\*\*\*\* 中所選叢集的強度。</span><span class="sxs-lookup"><span data-stu-id="f4938-135">Contains a shaded bar that indicates how strongly the attribute and the state that are listed in **Variables** and **Value** favor the cluster that is selected in **Cluster 1**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f4938-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4938-136">See Also</span></span>  
 <span data-ttu-id="f4938-137">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="f4938-137">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="f4938-138">[&#40;資料採礦模型設計工具的採礦模型檢視器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="f4938-138">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="f4938-139">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="f4938-139">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
