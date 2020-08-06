---
title: '[相依性網路] 索引標籤 () 的採礦模型檢視器 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.dependencynetwork.f1
ms.assetid: e58ce1b7-20d6-42cb-ade5-916da8471e09
author: minewiskan
ms.author: owend
ms.openlocfilehash: 94ce82524445ffb8999c671c736087362ef0adfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687337"
---
# <a name="dependency-network-tab-mining-model-viewer"></a><span data-ttu-id="8b01b-102">相依性網路索引標籤 (採礦模型檢視器)</span><span class="sxs-lookup"><span data-stu-id="8b01b-102">Dependency Network Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="8b01b-103">[相依性網路]\*\*\*\* 索引標籤會提供採礦模型所包含之所有屬性的圖形檢視，並顯示這些屬性彼此相關的情況。</span><span class="sxs-lookup"><span data-stu-id="8b01b-103">The **Dependency Net** tab provides a graphical view of all attributes that the mining model contains, and shows how the attributes are related.</span></span>  
  
 <span data-ttu-id="8b01b-104">[相依性網路]\*\*\*\* 索引標籤用於多種類型的採礦模型，包括貝氏機率分類模型、決策樹模型和關聯模型。</span><span class="sxs-lookup"><span data-stu-id="8b01b-104">The **Dependency Net**  tab is used for several types of mining models, including Naïve Bayes models, decision tree models, and association models.</span></span> <span data-ttu-id="8b01b-105">如需如何在這些模型的內容中解譯 [相依性網路]\*\*\*\* 索引標籤內容的詳細資訊，請參閱下列連結：</span><span class="sxs-lookup"><span data-stu-id="8b01b-105">For more information about how to interpret the contents of the **Dependency Net**  tab in the context of these models, see the following links:</span></span>  
  
 [<span data-ttu-id="8b01b-106">使用 Microsoft 樹狀檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="8b01b-106">Browse a Model Using the Microsoft Tree Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)  
  
 [<span data-ttu-id="8b01b-107">使用 Microsoft 貝氏機率分類檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="8b01b-107">Browse a Model Using the Microsoft Naive Bayes Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
 [<span data-ttu-id="8b01b-108">使用 Microsoft 關聯規則檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="8b01b-108">Browse a Model Using the Microsoft Association Rules Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)  
  
## <a name="options"></a><span data-ttu-id="8b01b-109">選項</span><span class="sxs-lookup"><span data-stu-id="8b01b-109">Options</span></span>  
 <span data-ttu-id="8b01b-110">**重新整理檢視器內容**</span><span class="sxs-lookup"><span data-stu-id="8b01b-110">**Refresh viewer content**</span></span>  
 <span data-ttu-id="8b01b-111">在檢視器中重新載入採礦模型。</span><span class="sxs-lookup"><span data-stu-id="8b01b-111">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="8b01b-112">**採礦模型**</span><span class="sxs-lookup"><span data-stu-id="8b01b-112">**Mining Model**</span></span>  
 <span data-ttu-id="8b01b-113">在目前採礦結構中選擇要檢視的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="8b01b-113">Choose a mining model to view, from those in the current mining structure.</span></span> <span data-ttu-id="8b01b-114">採礦模型會在自訂檢視器中開啟。</span><span class="sxs-lookup"><span data-stu-id="8b01b-114">The mining model will open in a custom viewer.</span></span> <span data-ttu-id="8b01b-115">用於每個模型的自訂檢視器類型是由您用來建立該模型的演算法決定。</span><span class="sxs-lookup"><span data-stu-id="8b01b-115">The type of custom viewer that is used for each model is determined by the algorithm that you used to create the model.</span></span>  
  
 <span data-ttu-id="8b01b-116">**檢視者**</span><span class="sxs-lookup"><span data-stu-id="8b01b-116">**Viewer**</span></span>  
 <span data-ttu-id="8b01b-117">選擇用來瀏覽選取之採礦模型的檢視器。</span><span class="sxs-lookup"><span data-stu-id="8b01b-117">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="8b01b-118">可以使用為每個採礦模型提供的自訂檢視器，或 [!INCLUDE[msCoName](../includes/msconame-md.md)] 採礦內容檢視器。</span><span class="sxs-lookup"><span data-stu-id="8b01b-118">For each model, you can use either the custom viewer is provided for each mining model, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="8b01b-119">還可以使用外掛程式檢視器 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="8b01b-119">You can also use plug-in viewers if available.</span></span> <span data-ttu-id="8b01b-120">Microsoft 內容樹狀檢視器可用於所有模型，並在 HTML 資料表中表示模型內容。</span><span class="sxs-lookup"><span data-stu-id="8b01b-120">The Microsoft Content Tree Viewer can be used with all models, and represents the model content in an HTML table.</span></span>  
  
 <span data-ttu-id="8b01b-121">**放大**</span><span class="sxs-lookup"><span data-stu-id="8b01b-121">**Zoom In**</span></span>  
 <span data-ttu-id="8b01b-122">放大圖表，以便更詳細地查看屬性。</span><span class="sxs-lookup"><span data-stu-id="8b01b-122">Zoom in to the diagram, so that you can see the attributes in more detail.</span></span>  
  
 <span data-ttu-id="8b01b-123">**縮小**</span><span class="sxs-lookup"><span data-stu-id="8b01b-123">**Zoom Out**</span></span>  
 <span data-ttu-id="8b01b-124">縮小圖表，以便查看更多屬性以及這些屬性之間的連結。</span><span class="sxs-lookup"><span data-stu-id="8b01b-124">Zoom out from the diagram, so that you can see more attributes and the links between them.</span></span>  
  
 <span data-ttu-id="8b01b-125">**複製圖表檢視**</span><span class="sxs-lookup"><span data-stu-id="8b01b-125">**Copy Graph View**</span></span>  
 <span data-ttu-id="8b01b-126">將圖表的可見部分複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="8b01b-126">Copy the visible section of the diagram to the clipboard.</span></span>  
  
 <span data-ttu-id="8b01b-127">**複製整個圖表**</span><span class="sxs-lookup"><span data-stu-id="8b01b-127">**Copy Entire Graph**</span></span>  
 <span data-ttu-id="8b01b-128">將整個圖表複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="8b01b-128">Copy the complete diagram to the clipboard.</span></span>  
  
 <span data-ttu-id="8b01b-129">**連結**</span><span class="sxs-lookup"><span data-stu-id="8b01b-129">**Links**</span></span>  
 <span data-ttu-id="8b01b-130">您可以調整屬性右邊的滑動軸，來調整檢視器顯示的連結 (邊緣) 數目和節點數目。</span><span class="sxs-lookup"><span data-stu-id="8b01b-130">Adjust how many links (edges) and nodes the viewer shows by adjusting the slider to the right of the attributes.</span></span> <span data-ttu-id="8b01b-131">向下拖曳滑動軸會增大臨界值，以便只顯示最強連結。</span><span class="sxs-lookup"><span data-stu-id="8b01b-131">Dragging the slider bar down increases the threshold value, so that only the strongest links are shown.</span></span> <span data-ttu-id="8b01b-132">對於每種模型類型，都會使用略為不同的值來表示圖形中的連結：</span><span class="sxs-lookup"><span data-stu-id="8b01b-132">For each model type, a slightly different value is used to represent the links in the graph:</span></span>  
  
-   <span data-ttu-id="8b01b-133">在 **決策樹** 模型中，邊緣表示連接的預測強度 (由分岔分數部分決定)。</span><span class="sxs-lookup"><span data-stu-id="8b01b-133">In a **decision tree** model, the edges represent the predictive strength of the connection, determined partly by the split score.</span></span>  
  
-   <span data-ttu-id="8b01b-134">在 **貝氏機率分類** 模型中，兩個節點之間的連結可以是任一方向：也就是說，節點 A 可預測節點 B，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="8b01b-134">In a **Naïve Bayes** model, the links between two nodes can go either way: that is, node A can predict the node B, and vice versa.</span></span> <span data-ttu-id="8b01b-135">與邊緣關聯的分數表示連接的預測強度。</span><span class="sxs-lookup"><span data-stu-id="8b01b-135">The score associated with the edge represents the predictive strength of the connection.</span></span>  
  
-   <span data-ttu-id="8b01b-136">在 **關聯模型**中，節點之間的邊緣表示連接兩個項目集之規則的重要性分數。</span><span class="sxs-lookup"><span data-stu-id="8b01b-136">In an **association model**, the edges between nodes represent the importance score of the rule that connects two itemsets.</span></span>  
  
 <span data-ttu-id="8b01b-137">所有模型類型的一般規則是，連結愈強，兩個屬性之間的預測關聯性也就愈強。</span><span class="sxs-lookup"><span data-stu-id="8b01b-137">A general rule for all model types is that the stronger the link, the stronger the predictive relationship between the two attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b01b-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b01b-138">See Also</span></span>  
 <span data-ttu-id="8b01b-139">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8b01b-139">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="8b01b-140">[&#40;資料採礦模型設計工具的採礦模型檢視器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="8b01b-140">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="8b01b-141">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="8b01b-141">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
