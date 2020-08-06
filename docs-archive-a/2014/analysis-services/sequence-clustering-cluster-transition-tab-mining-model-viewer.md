---
title: 時序群集 [叢集轉換] 索引標籤 () 的採礦模型檢視器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.transition.f1
ms.assetid: 40aef457-d69f-4905-a2d3-924c37bd3d97
author: minewiskan
ms.author: owend
ms.openlocfilehash: f777e48c2f69911e61420fd3b7a0a137a04e7c2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710877"
---
# <a name="sequence-clustering-cluster-transition-tab-mining-model-viewer"></a><span data-ttu-id="a7f49-102">時序叢集的叢集轉換索引標籤 (採礦模型檢視器)</span><span class="sxs-lookup"><span data-stu-id="a7f49-102">Sequence Clustering Cluster Transition Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="a7f49-103">可以使用 [Microsoft 時序叢集檢視器]\*\*\*\* 中的 [狀態轉換]\*\*\*\* 索引標籤，更仔細地查看選定叢集中屬性/值組 (或狀態) 之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="a7f49-103">The **State Transitions** tab in the **Microsoft Sequence Clustering Viewer** provides a closer look at the transitions between attribute-value pairs, or states, in the selected cluster.</span></span>  
  
 <span data-ttu-id="a7f49-104">使用此時序叢集模型檢視可檢視模式。</span><span class="sxs-lookup"><span data-stu-id="a7f49-104">Use this view of a sequence clustering model to view patterns.</span></span> <span data-ttu-id="a7f49-105">在圖表中，連結代表轉換的機率，而節點代表時序狀態。</span><span class="sxs-lookup"><span data-stu-id="a7f49-105">In the diagram, a link represents the probability of a transition, and a node represents a sequence state.</span></span>  
  
 <span data-ttu-id="a7f49-106">\*\*如需詳細資訊，請參閱 \*\* [Microsoft 時序叢集演算法](data-mining/microsoft-sequence-clustering-algorithm.md)、[使用 Microsoft 時序叢集檢視器瀏覽模型](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="a7f49-106">**For More Information:** [Microsoft Sequence Clustering Algorithm](data-mining/microsoft-sequence-clustering-algorithm.md), [Browse a Model Using the Microsoft Sequence Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="a7f49-107">選項</span><span class="sxs-lookup"><span data-stu-id="a7f49-107">Options</span></span>  
 <span data-ttu-id="a7f49-108">**重新整理檢視器內容**</span><span class="sxs-lookup"><span data-stu-id="a7f49-108">**Refresh viewer content**</span></span>  
 <span data-ttu-id="a7f49-109">在檢視器中重新載入採礦模型。</span><span class="sxs-lookup"><span data-stu-id="a7f49-109">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="a7f49-110">**採礦模型**</span><span class="sxs-lookup"><span data-stu-id="a7f49-110">**Mining Model**</span></span>  
 <span data-ttu-id="a7f49-111">選擇包含在目前採礦結構中，您要檢視的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="a7f49-111">Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="a7f49-112">採礦模型會在其關聯的檢視器中開啟。</span><span class="sxs-lookup"><span data-stu-id="a7f49-112">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="a7f49-113">**檢視者**</span><span class="sxs-lookup"><span data-stu-id="a7f49-113">**Viewer**</span></span>  
 <span data-ttu-id="a7f49-114">選擇用來瀏覽選取之採礦模型的檢視器。</span><span class="sxs-lookup"><span data-stu-id="a7f49-114">Choose a viewer to use in exploring the selected mining model.</span></span> <span data-ttu-id="a7f49-115">可以使用自訂檢視器，或 **[Microsoft 一般內容樹狀檢視器]**。</span><span class="sxs-lookup"><span data-stu-id="a7f49-115">You can use the custom viewer, or the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="a7f49-116">還可以使用外掛程式檢視器 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="a7f49-116">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="a7f49-117">**放大**</span><span class="sxs-lookup"><span data-stu-id="a7f49-117">**Zoom In**</span></span>  
 <span data-ttu-id="a7f49-118">將圖表放大，更仔細地查看狀態。</span><span class="sxs-lookup"><span data-stu-id="a7f49-118">Zoom in to the diagram, to see the states better.</span></span>  
  
 <span data-ttu-id="a7f49-119">**縮小**</span><span class="sxs-lookup"><span data-stu-id="a7f49-119">**Zoom Out**</span></span>  
 <span data-ttu-id="a7f49-120">將圖表縮小，以取得叢集中整體的狀態檢視。</span><span class="sxs-lookup"><span data-stu-id="a7f49-120">Zoom out from the diagram, to get an overall view of the states in the cluster.</span></span>  
  
 <span data-ttu-id="a7f49-121">**複製圖表檢視**</span><span class="sxs-lookup"><span data-stu-id="a7f49-121">**Copy Graph View**</span></span>  
 <span data-ttu-id="a7f49-122">將圖表的可見部分複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="a7f49-122">Copy the visible section of the diagram to the clipboard.</span></span>  
  
 <span data-ttu-id="a7f49-123">**複製整個圖表**</span><span class="sxs-lookup"><span data-stu-id="a7f49-123">**Copy Entire Graph**</span></span>  
 <span data-ttu-id="a7f49-124">將整個圖表複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="a7f49-124">Copy the complete diagram to the clipboard.</span></span>  
  
 <span data-ttu-id="a7f49-125">**Cluster**</span><span class="sxs-lookup"><span data-stu-id="a7f49-125">**Cluster**</span></span>  
 <span data-ttu-id="a7f49-126">選擇要在檢視器中顯示的群集。</span><span class="sxs-lookup"><span data-stu-id="a7f49-126">Choose a cluster to display in the viewer.</span></span> <span data-ttu-id="a7f49-127">預設會選取 [母體擴展 (全部)]\*\*\*\*，這表示整個模型中的狀態和轉換都包含在圖形中。</span><span class="sxs-lookup"><span data-stu-id="a7f49-127">By default, **Population (All)** is selected, which means that states and transitions from the entire model are included in the graph.</span></span> <span data-ttu-id="a7f49-128">在選擇某個特定叢集時，僅顯示該叢集中的狀態和轉換。</span><span class="sxs-lookup"><span data-stu-id="a7f49-128">When you choose a particular cluster, only the states and transitions that are in that cluster are displayed.</span></span>  
  
 <span data-ttu-id="a7f49-129">**秘訣：** 您可以使用 [**群集圖表**] 索引標籤重新命名叢集。只要選取叢集，按一下滑鼠右鍵，然後選取 [**重新命名**] 即可。</span><span class="sxs-lookup"><span data-stu-id="a7f49-129">**Tip:** You can rename clusters by using the **Cluster Diagram** tab. Just select a cluster, right-click, and select **Rename**.</span></span> <span data-ttu-id="a7f49-130">用更具描述性的標籤重新命名叢集，可使得在 **[狀態轉換]** 索引標籤中比較叢集變得更容易。</span><span class="sxs-lookup"><span data-stu-id="a7f49-130">Renaming clusters with a more descriptive label makes it easier to compare clusters in the **State Transitions** tab.</span></span>  
  
 <span data-ttu-id="a7f49-131">**顯示邊緣標籤**</span><span class="sxs-lookup"><span data-stu-id="a7f49-131">**Show Edge Labels**</span></span>  
 <span data-ttu-id="a7f49-132">選取此選項可在圖形的每個邊緣上顯示數字來表示轉換機率。</span><span class="sxs-lookup"><span data-stu-id="a7f49-132">Select this option to display numbers on each edge in the graph that denote the probability of the transition.</span></span>  
  
 <span data-ttu-id="a7f49-133">**連結**</span><span class="sxs-lookup"><span data-stu-id="a7f49-133">**Links**</span></span>  
 <span data-ttu-id="a7f49-134">使用滑動軸可控制圖表中顯示的狀態數目和轉換數目。</span><span class="sxs-lookup"><span data-stu-id="a7f49-134">Use the slider to control the number of states and transitions that are displayed in the chart.</span></span> <span data-ttu-id="a7f49-135">降低滑動軸只會顯示具有最高機率的狀態和轉換。</span><span class="sxs-lookup"><span data-stu-id="a7f49-135">Lowering the slider shows only the states and transitions with the highest probability.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f49-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7f49-136">See Also</span></span>  
 <span data-ttu-id="a7f49-137">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="a7f49-137">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="a7f49-138">[&#40;資料採礦模型設計工具的採礦模型檢視器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="a7f49-138">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="a7f49-139">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="a7f49-139">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
