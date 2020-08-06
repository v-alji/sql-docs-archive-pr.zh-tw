---
title: '[叢集辨識] 索引標籤 ([) 的模型檢視器] |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.discrimination.f1
ms.assetid: ae7cfff7-ab1c-4cf5-9a91-97b21d15d85f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 35435736bcdf1b1962de6babace2def953bbfff0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593691"
---
# <a name="cluster-discrimination-tab-mining-model-viewer"></a><span data-ttu-id="b9208-102">叢集辨識索引標籤 (採礦模型檢視器)</span><span class="sxs-lookup"><span data-stu-id="b9208-102">Cluster Discrimination Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="b9208-103">使用 [叢集辨識]\*\*\*\* 索引標籤，即可比較存在於一個叢集模型中的兩個叢集。</span><span class="sxs-lookup"><span data-stu-id="b9208-103">Use the **Cluster Discrimination** tab to compare two clusters that exist in a clustering model.</span></span> <span data-ttu-id="b9208-104">可以查看屬性和值的不同組合在叢集中的表示方式。</span><span class="sxs-lookup"><span data-stu-id="b9208-104">You can see how different combinations of attributes and values are represented within the clusters.</span></span>  
  
 <span data-ttu-id="b9208-105">**如需詳細資訊，請參閱** [Microsoft 叢集演算法](data-mining/microsoft-clustering-algorithm.md)、 [使用 Microsoft 叢集檢視器瀏覽模型](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="b9208-105">**For More Information:** [Microsoft Clustering Algorithm](data-mining/microsoft-clustering-algorithm.md), [Browse a Model Using the Microsoft Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="b9208-106">選項</span><span class="sxs-lookup"><span data-stu-id="b9208-106">Options</span></span>  
 <span data-ttu-id="b9208-107">**重新整理檢視器內容**</span><span class="sxs-lookup"><span data-stu-id="b9208-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="b9208-108">在檢視器中重新載入採礦模型。</span><span class="sxs-lookup"><span data-stu-id="b9208-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="b9208-109">**採礦模型**</span><span class="sxs-lookup"><span data-stu-id="b9208-109">**Mining Model**</span></span>  
 <span data-ttu-id="b9208-110">在目前採礦結構中選擇採礦模型。</span><span class="sxs-lookup"><span data-stu-id="b9208-110">Choose a mining model from those in the current mining structure.</span></span> <span data-ttu-id="b9208-111">採礦模型會在其關聯的檢視器中開啟。</span><span class="sxs-lookup"><span data-stu-id="b9208-111">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="b9208-112">**檢視者**</span><span class="sxs-lookup"><span data-stu-id="b9208-112">**Viewer**</span></span>  
 <span data-ttu-id="b9208-113">選擇用來瀏覽選取之採礦模型的檢視器。</span><span class="sxs-lookup"><span data-stu-id="b9208-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="b9208-114">您可以使用自訂的叢集模型檢視器，或 [!INCLUDE[msCoName](../includes/msconame-md.md)] 採礦內容檢視器。</span><span class="sxs-lookup"><span data-stu-id="b9208-114">You can use the custom viewer for clustering models, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="b9208-115">還可以使用外掛程式檢視器 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="b9208-115">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="b9208-116">**叢集 1**</span><span class="sxs-lookup"><span data-stu-id="b9208-116">**Cluster 1**</span></span>  
 <span data-ttu-id="b9208-117">選取叢集，以便與另一個叢集進行比較。</span><span class="sxs-lookup"><span data-stu-id="b9208-117">Select a cluster, so that you can compare it to another cluster.</span></span>  
  
 <span data-ttu-id="b9208-118">**群集 2**</span><span class="sxs-lookup"><span data-stu-id="b9208-118">**Cluster 2**</span></span>  
 <span data-ttu-id="b9208-119">從採礦模型中的叢集清單選取第二個叢集，以便與 [叢集 1]\*\*\*\* 比較。</span><span class="sxs-lookup"><span data-stu-id="b9208-119">Select a second cluster from the list of clusters in the mining model, to compare to **Cluster 1**.</span></span> <span data-ttu-id="b9208-120">還可以將叢集與其補數 (表示模型中不屬於所選叢集的所有案例) 進行比較。</span><span class="sxs-lookup"><span data-stu-id="b9208-120">You can also compare a cluster to its complement, meaning all cases in the model except those in the selected cluster.</span></span>  
  
 <span data-ttu-id="b9208-121">**和的辨識分數 \<cluster 1>\<cluster 2>**</span><span class="sxs-lookup"><span data-stu-id="b9208-121">**Discrimination scores for \<cluster 1> and \<cluster 2>**</span></span>  
 <span data-ttu-id="b9208-122">圖形中的資料行提供有關每個屬性/值組與兩個選定叢集之間如何相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="b9208-122">The columns in the graph provide information about how each attribute-value pair is related to the two selected clusters.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b9208-123">**變數**</span><span class="sxs-lookup"><span data-stu-id="b9208-123">**Variables**</span></span>|<span data-ttu-id="b9208-124">採礦模型中的屬性。</span><span class="sxs-lookup"><span data-stu-id="b9208-124">An attribute in the mining model.</span></span>|  
|<span data-ttu-id="b9208-125">**值**</span><span class="sxs-lookup"><span data-stu-id="b9208-125">**Values**</span></span>|<span data-ttu-id="b9208-126">[變數]\*\*\*\* 中所選屬性的值。</span><span class="sxs-lookup"><span data-stu-id="b9208-126">A value of the attribute selected in **Variables**.</span></span>|  
|<span data-ttu-id="b9208-127">**照顧\<cluster 1>**</span><span class="sxs-lookup"><span data-stu-id="b9208-127">**Favors \<cluster 1>**</span></span>|<span data-ttu-id="b9208-128">左側的橫條圖表示所選屬性/值組代表 [叢集 1]\*\*\*\* 中所選叢集的機率。</span><span class="sxs-lookup"><span data-stu-id="b9208-128">The bar graph on the left represents the probability that the selected attribute-value pair is representative of the cluster selected in **Cluster 1**.</span></span> <span data-ttu-id="b9208-129">將滑鼠暫時放在長條上方，可查看以百分比表示的值。</span><span class="sxs-lookup"><span data-stu-id="b9208-129">You can pause the mouse over the bar to see the value, represented as a percentage.</span></span> <span data-ttu-id="b9208-130">請注意，即使值為零，也不表示叢集中的屬性值不一定會遺失，只是散發會對另一個叢集進行強式比對。</span><span class="sxs-lookup"><span data-stu-id="b9208-130">Note that even if the value is zero, it doesn't mean the attribute-value is necessarily missing from the cluster, just that the distribution strongly favors one cluster over the other.</span></span>|  
|<span data-ttu-id="b9208-131">**照顧\<cluster 2>**</span><span class="sxs-lookup"><span data-stu-id="b9208-131">**Favors \<cluster 2>**</span></span>|<span data-ttu-id="b9208-132">右側的橫條圖表示所選屬性/值組代表 [叢集 2]\*\*\*\* 中所選叢集的機率。</span><span class="sxs-lookup"><span data-stu-id="b9208-132">The bar graph on the right represents the probability that the selected attribute-value pair is representative of the cluster selected in **Cluster 2**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b9208-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9208-133">See Also</span></span>  
 <span data-ttu-id="b9208-134">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="b9208-134">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="b9208-135">[&#40;資料採礦模型設計工具的採礦模型檢視器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="b9208-135">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="b9208-136">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="b9208-136">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
