---
title: 時序群集叢集特性索引標籤 (採礦模型檢視器) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.characteristics.f1
ms.assetid: 3a9e8a0c-7d03-47cc-8625-e68d73a8c947
author: minewiskan
ms.author: owend
ms.openlocfilehash: c991005cb4daa436c86d09037ef523499add84e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708709"
---
# <a name="sequence-clustering-cluster-characteristics-tab-mining-model-viewer"></a><span data-ttu-id="7b0fe-102">時序叢集的叢集特性索引標籤 (採礦模型檢視器)</span><span class="sxs-lookup"><span data-stu-id="7b0fe-102">Sequence Clustering Cluster Characteristics Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="7b0fe-103">**[Microsoft 時序叢集檢視器]** 中的 **[叢集特性]** 索引標籤提供定義時序叢集之特性的詳細清單。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-103">The **Cluster Characteristics** tab in the **Microsoft Sequence Clustering Viewer** provides a detailed list of the characteristics that define a sequence cluster.</span></span> <span data-ttu-id="7b0fe-104">這些特性可包括簡單屬性/值組以及狀態之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-104">Those characteristics can include simple attribute-value pairs as well as transitions between states.</span></span>  
  
 <span data-ttu-id="7b0fe-105">可以使用此時序叢集模型檢視，向下鑽研叢集內容，以及查看代表叢集的時序。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-105">Use this view of a sequence clustering model to drill down into the cluster contents, and see the sequences that are representative of a cluster.</span></span>  
  
 <span data-ttu-id="7b0fe-106">\*\*如需詳細資訊，請參閱 \*\* [Microsoft 時序叢集演算法](data-mining/microsoft-sequence-clustering-algorithm.md)、[使用 Microsoft 時序叢集檢視器瀏覽模型](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-106">**For More Information:** [Microsoft Sequence Clustering Algorithm](data-mining/microsoft-sequence-clustering-algorithm.md), [Browse a Model Using the Microsoft Sequence Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="7b0fe-107">選項</span><span class="sxs-lookup"><span data-stu-id="7b0fe-107">Options</span></span>  
 <span data-ttu-id="7b0fe-108">**重新整理檢視器內容**</span><span class="sxs-lookup"><span data-stu-id="7b0fe-108">**Refresh viewer content**</span></span>  
 <span data-ttu-id="7b0fe-109">在檢視器中重新載入採礦模型。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-109">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="7b0fe-110">**採礦模型**</span><span class="sxs-lookup"><span data-stu-id="7b0fe-110">**Mining Model**</span></span>  
 <span data-ttu-id="7b0fe-111">選擇包含在目前採礦結構中，您要檢視的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-111">Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="7b0fe-112">採礦模型會在其關聯的檢視器中開啟。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-112">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="7b0fe-113">**檢視者**</span><span class="sxs-lookup"><span data-stu-id="7b0fe-113">**Viewer**</span></span>  
 <span data-ttu-id="7b0fe-114">選擇用來瀏覽選取之採礦模型的檢視器。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-114">Choose a viewer to use in exploring the selected mining model.</span></span> <span data-ttu-id="7b0fe-115">可以使用自訂檢視器，或 **[Microsoft 一般內容樹狀檢視器]**。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-115">You can use the custom viewer, or the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="7b0fe-116">還可以使用外掛程式檢視器 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-116">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="7b0fe-117">**Cluster**</span><span class="sxs-lookup"><span data-stu-id="7b0fe-117">**Cluster**</span></span>  
 <span data-ttu-id="7b0fe-118">選擇要檢視的叢集。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-118">Choose the cluster you want to view.</span></span>  
  
 <span data-ttu-id="7b0fe-119">**的特性\<Cluster>**</span><span class="sxs-lookup"><span data-stu-id="7b0fe-119">**Characteristics for \<Cluster>**</span></span>  
 <span data-ttu-id="7b0fe-120">此資料表提供已指派給目前叢集之時序的清單 (依機率排序)。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-120">This table provides a list of the sequences that were assigned to the current cluster, ordered by probability.</span></span> <span data-ttu-id="7b0fe-121">請記住，時序基本上是一個屬性/值組，後面跟著一個或多個其他的屬性/值組。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-121">Remember that a sequence is basically one attribute-value pair, followed by one or more additional attribute-value pairs.</span></span> <span data-ttu-id="7b0fe-122">時序及其機率的組合定義了每個叢集的特性。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-122">The combination of sequences and their probabilities are the defining characteristics of each cluster.</span></span>  
  
 <span data-ttu-id="7b0fe-123">例如，以購物籃分析為基礎的時序叢集模型中，一個叢集的最上層特性可能是客戶選擇促銷項目，然後在不再購買其他項目的情況下結束交易。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-123">For example, in a sequence clustering model based on market basket analysis, one cluster might have as its top characteristic a customer choosing the sale item and then ending the transaction without purchasing anything more.</span></span> <span data-ttu-id="7b0fe-124">在試圖分析伺服器失敗的時序叢集模型中，叢集的主要特性可能是一系列高頻率錯誤事件。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-124">In a sequence clustering model that seeks to analyze server failures, the primary characteristics of a cluster might be a series of high frequency error events.</span></span>  
  
|<span data-ttu-id="7b0fe-125">值</span><span class="sxs-lookup"><span data-stu-id="7b0fe-125">Value</span></span>|<span data-ttu-id="7b0fe-126">描述</span><span class="sxs-lookup"><span data-stu-id="7b0fe-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7b0fe-127">**變數**</span><span class="sxs-lookup"><span data-stu-id="7b0fe-127">**Variable**</span></span>|<span data-ttu-id="7b0fe-128">此資料行表示特性是值還是轉換。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-128">This column indicates whether the characteristic is a value, or a transition.</span></span><br /><br /> <span data-ttu-id="7b0fe-129">如果特性是值，則 [**變數**] 資料行會包含屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-129">If the characteristic is a value, the **Variable** column contains the attribute name.</span></span><br /><br /> <span data-ttu-id="7b0fe-130">如果特性表示狀態轉換，則 [**變數**] 資料行會包含「轉換」文字。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-130">If the characteristic represents a state transition, the **Variable** column contains the text "Transitions".</span></span>|  
|<span data-ttu-id="7b0fe-131">**值**</span><span class="sxs-lookup"><span data-stu-id="7b0fe-131">**Values**</span></span>|<span data-ttu-id="7b0fe-132">此資料行的值取決於特性是簡單屬性/值組，還是一個表示項目或事件通用時序的狀態轉換。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-132">The value of this column depends on whether the characteristic is a simple attribute-value pair, or a state transition representing a common sequence of items or events.</span></span><br /><br /> <span data-ttu-id="7b0fe-133">如果特性是值，則 [**值**] 資料行會包含狀態。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-133">If the characteristic is a value, the **Value** column contains the state.</span></span><br /><br /> <span data-ttu-id="7b0fe-134">如果特性表示狀態轉換，則 [**值**] 資料行會包含狀態轉換的描述。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-134">If the characteristic represents a state transition, the **Value** column contains the description of the state transition.</span></span>|  
|<span data-ttu-id="7b0fe-135">**機率**</span><span class="sxs-lookup"><span data-stu-id="7b0fe-135">**Probability**</span></span>|<span data-ttu-id="7b0fe-136">此資料行會顯示長條，用於表示此特性 (簡單屬性/值組或狀態的某種組合) 是目前叢集之成員的相對機率。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-136">This column displays a bar that indicates the relative probability that this characteristic (either a simple attribute-value pair, or some combination of states) are members of the current cluster.</span></span><br /><br /> <span data-ttu-id="7b0fe-137">可以將滑鼠停留在長條上方，來顯示特性的頻率值。</span><span class="sxs-lookup"><span data-stu-id="7b0fe-137">You can hover the mouse over the par to display the frequency value of the characteristic.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b0fe-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b0fe-138">See Also</span></span>  
 <span data-ttu-id="7b0fe-139">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="7b0fe-139">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="7b0fe-140">[&#40;資料採礦模型設計工具的採礦模型檢視器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="7b0fe-140">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="7b0fe-141">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="7b0fe-141">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
