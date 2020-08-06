---
title: '[叢集特性] 索引標籤 () 的採礦模型檢視器 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.characteristics.f1
ms.assetid: 8e33ed1d-1ce4-405d-895b-7e995b2c910d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 959d94767b6cb27d9ebb6e06c592034fca20ac89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593067"
---
# <a name="cluster-characteristics-tab-mining-model-viewer"></a><span data-ttu-id="7750a-102">叢集特性索引標籤 (採礦模型檢視器)</span><span class="sxs-lookup"><span data-stu-id="7750a-102">Cluster Characteristics Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="7750a-103">[叢集特性]\*\*\*\* 索引標籤可讓您瀏覽叢集模型中某個叢集的特性，或瀏覽該模型中所有案例集合的特性。</span><span class="sxs-lookup"><span data-stu-id="7750a-103">The **Cluster Characteristics** tab lets you explore the characteristics of a cluster in a clustering model, or the set of all cases in the model.</span></span> <span data-ttu-id="7750a-104">圖形會將每個屬性/值組的重要性顯示為定義叢集的特性 (相較於其他叢集)。</span><span class="sxs-lookup"><span data-stu-id="7750a-104">The graph shows the importance of each attribute-value pair as a characteristic that defines the cluster, in comparison with other clusters.</span></span>  
  
 <span data-ttu-id="7750a-105">**如需詳細資訊，請參閱** [Microsoft 叢集演算法](data-mining/microsoft-clustering-algorithm.md)、 [使用 Microsoft 叢集檢視器瀏覽模型](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="7750a-105">**For More Information:** [Microsoft Clustering Algorithm](data-mining/microsoft-clustering-algorithm.md), [Browse a Model Using the Microsoft Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="7750a-106">選項</span><span class="sxs-lookup"><span data-stu-id="7750a-106">Options</span></span>  
 <span data-ttu-id="7750a-107">**重新整理檢視器內容**</span><span class="sxs-lookup"><span data-stu-id="7750a-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="7750a-108">在檢視器中重新載入採礦模型。</span><span class="sxs-lookup"><span data-stu-id="7750a-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="7750a-109">**採礦模型**</span><span class="sxs-lookup"><span data-stu-id="7750a-109">**Mining Model**</span></span>  
 <span data-ttu-id="7750a-110">在目前採礦結構中選擇採礦模型。</span><span class="sxs-lookup"><span data-stu-id="7750a-110">Choose a mining model from those in the current mining structure.</span></span> <span data-ttu-id="7750a-111">採礦模型會在自訂檢視器中開啟。</span><span class="sxs-lookup"><span data-stu-id="7750a-111">The mining model will open in the custom viewer.</span></span>  
  
 <span data-ttu-id="7750a-112">**檢視者**</span><span class="sxs-lookup"><span data-stu-id="7750a-112">**Viewer**</span></span>  
 <span data-ttu-id="7750a-113">選擇用來瀏覽選取之採礦模型的檢視器。</span><span class="sxs-lookup"><span data-stu-id="7750a-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="7750a-114">可以使用與此模型類型關聯的自訂檢視器，或 [!INCLUDE[msCoName](../includes/msconame-md.md)] 採礦內容檢視器。</span><span class="sxs-lookup"><span data-stu-id="7750a-114">You can use the custom viewer associated with this model type, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="7750a-115">還可以使用任何可用的外掛程式檢視器。</span><span class="sxs-lookup"><span data-stu-id="7750a-115">You can also use any plug-in viewers that are available.</span></span>  
  
 <span data-ttu-id="7750a-116">**Cluster**</span><span class="sxs-lookup"><span data-stu-id="7750a-116">**Cluster**</span></span>  
 <span data-ttu-id="7750a-117">選擇要查看的叢集，或選擇 [母體擴展 (全部)]\*\*\*\* 以查看模型屬性的整體分佈情況。</span><span class="sxs-lookup"><span data-stu-id="7750a-117">Choose the cluster you want to view, or choose **Population (All)** to see the distribution of attributes for the model as a whole.</span></span>  
  
 <span data-ttu-id="7750a-118">**的特性\<cluster>**</span><span class="sxs-lookup"><span data-stu-id="7750a-118">**Characteristics for \<cluster>**</span></span>  
 <span data-ttu-id="7750a-119">圖形包含描述所選取叢集之特性的下列資料行。</span><span class="sxs-lookup"><span data-stu-id="7750a-119">The graph contains the following columns, which describe the characteristics of the selected cluster.</span></span>  
  
|<span data-ttu-id="7750a-120">值</span><span class="sxs-lookup"><span data-stu-id="7750a-120">Value</span></span>|<span data-ttu-id="7750a-121">描述</span><span class="sxs-lookup"><span data-stu-id="7750a-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7750a-122">**變數**</span><span class="sxs-lookup"><span data-stu-id="7750a-122">**Variable**</span></span>|<span data-ttu-id="7750a-123">列出在所選叢集中找到的採礦模型屬性。</span><span class="sxs-lookup"><span data-stu-id="7750a-123">Lists the attributes from the mining model that are found in the selected cluster.</span></span>|  
|<span data-ttu-id="7750a-124">**值**</span><span class="sxs-lookup"><span data-stu-id="7750a-124">**Values**</span></span>|<span data-ttu-id="7750a-125">列出在目前所選叢集中找到的目前屬性的值。</span><span class="sxs-lookup"><span data-stu-id="7750a-125">Lists the values of the current attributes that are found in the currently selected cluster.</span></span>|  
|<span data-ttu-id="7750a-126">**機率**</span><span class="sxs-lookup"><span data-stu-id="7750a-126">**Probability**</span></span>|<span data-ttu-id="7750a-127">長條表示屬性/值組做為此叢集的辨別特性的強度。</span><span class="sxs-lookup"><span data-stu-id="7750a-127">The bar indicates the strength of the attribute-value pair as a distinguishing feature of this cluster.</span></span> <span data-ttu-id="7750a-128">如果您將滑鼠停留在長條上方，則可查看以百分比表示的機率值。</span><span class="sxs-lookup"><span data-stu-id="7750a-128">If you hover the mouse over the bar, you can see the probability value, represented as a percentage.</span></span> <span data-ttu-id="7750a-129">這表示，在任何特定案例中使用此屬性和值組合時，該案例會屬於此叢集的機率。</span><span class="sxs-lookup"><span data-stu-id="7750a-129">What this indicates is, given this attribute and value combination in any particular case, what is the probability that the case would belong in this cluster.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7750a-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7750a-130">See Also</span></span>  
 <span data-ttu-id="7750a-131">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="7750a-131">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="7750a-132">[&#40;資料採礦模型設計工具的採礦模型檢視器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="7750a-132">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="7750a-133">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="7750a-133">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
