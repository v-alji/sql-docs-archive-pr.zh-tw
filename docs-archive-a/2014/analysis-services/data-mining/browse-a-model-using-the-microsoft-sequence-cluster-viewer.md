---
title: 使用 Microsoft 時序群集檢視器流覽模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Sequence Cluster Viewer
- clusters [Analysis Services]
- data mining [Analysis Services], sequences
- discrimination [Analysis Services]
- mining model content, viewing
- mining models [Analysis Services], sequences
- Microsoft Sequence Cluster Viewer
- sequence [Analysis Services]
- transitions [Analysis Services]
ms.assetid: 3ada00aa-da9e-488a-9f53-c3e188f81f84
author: minewiskan
ms.author: owend
ms.openlocfilehash: d6e2c95a08f293dad8793ba5d4367753ae2c6db9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607181"
---
# <a name="browse-a-model-using-the-microsoft-sequence-cluster-viewer"></a><span data-ttu-id="a28b1-102">使用 Microsoft 時序叢集檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="a28b1-102">Browse a Model Using the Microsoft Sequence Cluster Viewer</span></span>
  <span data-ttu-id="a28b1-103">中的時序 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 群集檢視器 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會顯示以時序群集演算法建立的採礦模型 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a28b1-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm.</span></span> <span data-ttu-id="a28b1-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 時序群集演算法是時序分析演算法，用來瀏覽包含事件的資料，這些事件可透過遵循路徑或 *時序*加以連結。</span><span class="sxs-lookup"><span data-stu-id="a28b1-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm is a sequence analysis algorithm for use in exploring data that contains events that can be linked by following paths, or *sequences*.</span></span> <span data-ttu-id="a28b1-105">如需這個演算法的詳細資訊，請參閱 [Microsoft 時序群集演算法](microsoft-sequence-clustering-algorithm.md)。</span><span class="sxs-lookup"><span data-stu-id="a28b1-105">For more information about this algorithm, see [Microsoft Sequence Clustering Algorithm](microsoft-sequence-clustering-algorithm.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a28b1-106">若要檢視有關此模型中所用的方程式及所探索之模式的詳細資訊，請使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 一般內容樹狀檢視器。</span><span class="sxs-lookup"><span data-stu-id="a28b1-106">To view detailed information about the equations used in the model and the patterns that were discovered, use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="a28b1-107">如需詳細資訊，請參閱[使用 Microsoft 一般內容樹狀檢視器瀏覽模型](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)或 [Microsoft 一般內容樹狀檢視器 &#40;資料採礦&#41;](../microsoft-generic-content-tree-viewer-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a28b1-107">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a28b1-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 時序群集檢視器會提供類似 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 群集檢視器的功能和選項。</span><span class="sxs-lookup"><span data-stu-id="a28b1-108">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster Viewer provides functionality and options that are similar to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer.</span></span> <span data-ttu-id="a28b1-109">如需詳細資訊，請參閱 [使用 Microsoft 叢集檢視器瀏覽模型](browse-a-model-using-the-microsoft-cluster-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="a28b1-109">For more information, see [Browse a Model Using the Microsoft Cluster Viewer](browse-a-model-using-the-microsoft-cluster-viewer.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="a28b1-110">檢視器索引標籤</span><span class="sxs-lookup"><span data-stu-id="a28b1-110">Viewer Tabs</span></span>  
 <span data-ttu-id="a28b1-111">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中瀏覽採礦模型時，該模型會在適合它的檢視器中，顯示於資料採礦設計師的 **[採礦模型檢視器]** 索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="a28b1-111">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="a28b1-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 時序群集檢視器會提供下列索引標籤，用來瀏覽時序群集採礦模型：</span><span class="sxs-lookup"><span data-stu-id="a28b1-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster Viewer provides the following tabs for use in exploring sequence clustering mining models:</span></span>  
  
-   [<span data-ttu-id="a28b1-113">群集圖表</span><span class="sxs-lookup"><span data-stu-id="a28b1-113">Cluster Diagram</span></span>](#BKMK_Diagram)  
  
-   [<span data-ttu-id="a28b1-114">叢集設定檔</span><span class="sxs-lookup"><span data-stu-id="a28b1-114">Cluster Profiles</span></span>](#BKMK_Profile)  
  
-   [<span data-ttu-id="a28b1-115">叢集特性</span><span class="sxs-lookup"><span data-stu-id="a28b1-115">Cluster Characteristics</span></span>](#BKMK_Characteristics)  
  
-   [<span data-ttu-id="a28b1-116">群集辨識</span><span class="sxs-lookup"><span data-stu-id="a28b1-116">Cluster Discrimination</span></span>](#BKMK_Discrimination)  
  
-   [<span data-ttu-id="a28b1-117">群集轉換</span><span class="sxs-lookup"><span data-stu-id="a28b1-117">Cluster Transitions</span></span>](#BKMK_Transitions)  
  
###  <a name="cluster-diagram"></a><a name="BKMK_Diagram"></a><span data-ttu-id="a28b1-118">群集圖表</span><span class="sxs-lookup"><span data-stu-id="a28b1-118">Cluster Diagram</span></span>  
 <span data-ttu-id="a28b1-119">**時序群集檢視器的** [群集圖表] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 索引標籤，會顯示採礦模型中的所有群集。</span><span class="sxs-lookup"><span data-stu-id="a28b1-119">The **Cluster Diagram** tab of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster Viewer displays all the clusters that are in a mining model.</span></span> <span data-ttu-id="a28b1-120">連接一個群集與另一個群集的線條陰影代表群集的相似程度。</span><span class="sxs-lookup"><span data-stu-id="a28b1-120">The shading of the line that connects one cluster to another represents the strength of the similarity of the clusters.</span></span> <span data-ttu-id="a28b1-121">如果陰影很淡或不存在，則表示群集不太相似。</span><span class="sxs-lookup"><span data-stu-id="a28b1-121">If the shading is light or nonexistent, the clusters are not very similar.</span></span> <span data-ttu-id="a28b1-122">當線條色彩加深時，連結的相似度就更高。</span><span class="sxs-lookup"><span data-stu-id="a28b1-122">As the line becomes darker, the similarity of the links becomes stronger.</span></span> <span data-ttu-id="a28b1-123">您可以調整群集右邊的滑桿，來調整檢視器要顯示的線條數目。</span><span class="sxs-lookup"><span data-stu-id="a28b1-123">You can adjust how many lines the viewer shows by adjusting the slider to the right of the clusters.</span></span> <span data-ttu-id="a28b1-124">降低滑桿只顯示最強的連結。</span><span class="sxs-lookup"><span data-stu-id="a28b1-124">Lowering the slider shows only the strongest links.</span></span>  
  
 <span data-ttu-id="a28b1-125">依預設，陰影代表群集的母體。</span><span class="sxs-lookup"><span data-stu-id="a28b1-125">By default, the shade represents the population of the cluster.</span></span> <span data-ttu-id="a28b1-126">藉由使用 [ **ShadingVariable** ] 和 [**狀態**] 選項，您可以選取陰影所代表的屬性和狀態配對。</span><span class="sxs-lookup"><span data-stu-id="a28b1-126">By using the **ShadingVariable** and **State** options, you can select which attribute and state pair the shading represents.</span></span> <span data-ttu-id="a28b1-127">陰影愈深，表示特定狀態的屬性散發就愈大。</span><span class="sxs-lookup"><span data-stu-id="a28b1-127">The darker the shading, the greater the attribute distribution is for a specific state.</span></span> <span data-ttu-id="a28b1-128">當陰影變淡時，散發跟著減少。</span><span class="sxs-lookup"><span data-stu-id="a28b1-128">The distribution decreases as the shading gets lighter.</span></span>  
  
 <span data-ttu-id="a28b1-129">若要重新命名叢集，請以滑鼠右鍵按一下其節點，然後選取 [重新命名叢集]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a28b1-129">To rename a cluster, right-click its node and select **Rename Cluster**.</span></span> <span data-ttu-id="a28b1-130">新名稱會保存在伺服器上。</span><span class="sxs-lookup"><span data-stu-id="a28b1-130">The new name is persisted to the server.</span></span>  
  
 <span data-ttu-id="a28b1-131">若要將圖表的可見區段複製到剪貼簿，請按一下 **[複製圖表檢視]**。</span><span class="sxs-lookup"><span data-stu-id="a28b1-131">To copy the visible section of the diagram to the Clipboard, click **Copy Graph View**.</span></span> <span data-ttu-id="a28b1-132">若要複製完整圖表，請按一下 **[複製整個圖表]**。</span><span class="sxs-lookup"><span data-stu-id="a28b1-132">To copy the complete diagram, click **Copy Entire Graph**.</span></span> <span data-ttu-id="a28b1-133">您也可以使用 **[放大]** 和 **[縮小]** 來放大和縮小，或使用 **[將圖表縮放至視窗大小]**，使圖表符合視窗大小。</span><span class="sxs-lookup"><span data-stu-id="a28b1-133">You can also zoom in and out by using **Zoom In** and **Zoom Out**, or you can fit the diagram to the screen by using **Scale Diagram to Fit in Window**.</span></span>  
  
 [<span data-ttu-id="a28b1-134">回到頁首</span><span class="sxs-lookup"><span data-stu-id="a28b1-134">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="cluster-profiles"></a><a name="BKMK_Profile"></a><span data-ttu-id="a28b1-135">叢集設定檔</span><span class="sxs-lookup"><span data-stu-id="a28b1-135">Cluster Profiles</span></span>  
 <span data-ttu-id="a28b1-136">**[群集設定檔]** 索引標籤，會提供模型中的演算法所建立之群集的整體檢視。</span><span class="sxs-lookup"><span data-stu-id="a28b1-136">The **Cluster Profile** tab provides an overall view of the clusters that the algorithm in your model creates.</span></span> <span data-ttu-id="a28b1-137">在方格中的 **[母體]** 資料行後面的每一個資料行代表模型所發現的群集。</span><span class="sxs-lookup"><span data-stu-id="a28b1-137">Each column that follows the **Population** column in the grid represents a cluster that the model discovered.</span></span> <span data-ttu-id="a28b1-138">[ \<attribute> 範例] 資料列代表存在於叢集中的不同資料序列，而此 \<attribute> 列會描述該叢集包含的所有專案及其整體散發。</span><span class="sxs-lookup"><span data-stu-id="a28b1-138">The \<attribute>.samples row represents different sequences of data that exist in the cluster, and the \<attribute> row describes all the items that the cluster contains and their overall distribution.</span></span>  
  
 <span data-ttu-id="a28b1-139">[長條圖列] \*\*\*\* 選項會控制長條圖中可見的橫條數。</span><span class="sxs-lookup"><span data-stu-id="a28b1-139">The **Histogram bars** option controls the number of bars that are visible in the histogram.</span></span> <span data-ttu-id="a28b1-140">如果總列數超出您選擇要顯示的列數，就會保留最重要的列，而其餘的列將會分組放入灰色值區中。</span><span class="sxs-lookup"><span data-stu-id="a28b1-140">If more bars exist than you choose to display, the bars of highest importance are retained, and the remaining bars are grouped together into a gray bucket.</span></span>  
  
 <span data-ttu-id="a28b1-141">您可以變更群集的預設名稱，使名稱更具描述性。</span><span class="sxs-lookup"><span data-stu-id="a28b1-141">You can change the default names of the clusters, to make the names more descriptive.</span></span> <span data-ttu-id="a28b1-142">請以滑鼠右鍵按一下叢集的資料行標題並選取 [重新命名叢集]\*\*\*\*，來重新命名叢集。</span><span class="sxs-lookup"><span data-stu-id="a28b1-142">Rename a cluster by right-clicking its column heading and selecting **Rename cluster**.</span></span> <span data-ttu-id="a28b1-143">您可以選取 **[隱藏資料行]** 來隱藏群集，也可以拖曳資料行，在檢視器中將它們重新排序。</span><span class="sxs-lookup"><span data-stu-id="a28b1-143">You can hide clusters by selecting **Hide column**, and you can also drag columns to reorder them in the viewer.</span></span>  
  
 <span data-ttu-id="a28b1-144">若要開啟一個能提供更大、更詳細之叢集檢視的視窗，請按兩下 [狀態]\*\*\*\* 資料行的資料格或檢視器中的長條圖。</span><span class="sxs-lookup"><span data-stu-id="a28b1-144">To open a window that provides a larger, more detailed view of the clusters, double-click either a cell in the **States** column or a histogram in the viewer.</span></span>  
  
 [<span data-ttu-id="a28b1-145">回到頁首</span><span class="sxs-lookup"><span data-stu-id="a28b1-145">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="cluster-characteristics"></a><a name="BKMK_Characteristics"></a> <span data-ttu-id="a28b1-146">群集特性</span><span class="sxs-lookup"><span data-stu-id="a28b1-146">Cluster Characteristics</span></span>  
 <span data-ttu-id="a28b1-147">若要使用 **[群集特性]** 索引標籤，請從 **[群集]** 清單中選取群集。</span><span class="sxs-lookup"><span data-stu-id="a28b1-147">To use the **Cluster Characteristics** tab, select a cluster from the **Cluster** list.</span></span> <span data-ttu-id="a28b1-148">選取群集之後，您可以檢查構成該特定群集的特性。</span><span class="sxs-lookup"><span data-stu-id="a28b1-148">After you select a cluster, you can examine the characteristics that make up that specific cluster.</span></span> <span data-ttu-id="a28b1-149">群集包含的屬性將列於 **[變數]** 資料行中，而所列屬性的狀態則列於 **[值]** 資料行中。</span><span class="sxs-lookup"><span data-stu-id="a28b1-149">The attributes that the cluster contains are listed in the **Variables** columns, and the state of the listed attribute is listed in the **Values** column.</span></span> <span data-ttu-id="a28b1-150">屬性狀態是依重要性列出，以它們出現在群集裡的機率來描述。</span><span class="sxs-lookup"><span data-stu-id="a28b1-150">Attribute states are listed in order of importance, described by the probability that they will appear in the cluster.</span></span> <span data-ttu-id="a28b1-151">機率會在 **[機率]** 資料行中顯示。</span><span class="sxs-lookup"><span data-stu-id="a28b1-151">The probability is shown in the **Probability** column.</span></span>  
  
 [<span data-ttu-id="a28b1-152">回到頁首</span><span class="sxs-lookup"><span data-stu-id="a28b1-152">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="cluster-discrimination"></a><a name="BKMK_Discrimination"></a><span data-ttu-id="a28b1-153">群集辨識</span><span class="sxs-lookup"><span data-stu-id="a28b1-153">Cluster Discrimination</span></span>  
 <span data-ttu-id="a28b1-154">您可以使用 **[群集辨識]** 索引標籤來比較兩個群集之間的屬性，以決定時序中的項目對一個群集的喜好程度勝過另一個群集多少。</span><span class="sxs-lookup"><span data-stu-id="a28b1-154">You can use the **Cluster Discrimination** tab to compare attributes between two clusters, to determine how items in a sequence favor one cluster over another.</span></span> <span data-ttu-id="a28b1-155">請使用 **[群集 1]** 和 **[群集 2]** 清單來選取要比較的群集。</span><span class="sxs-lookup"><span data-stu-id="a28b1-155">Use the **Cluster 1** and **Cluster 2** lists to select the clusters to compare.</span></span> <span data-ttu-id="a28b1-156">檢視器會判斷群集間最重要的差異，並依重要性的順序顯示與差異相關聯的屬性狀態。</span><span class="sxs-lookup"><span data-stu-id="a28b1-156">The viewer determines the most important differences between the clusters, and displays the attribute states that are associated with the differences, in order of importance.</span></span> <span data-ttu-id="a28b1-157">屬性右邊的列會顯示狀態喜好的群集，而列的大小會顯示狀態喜好群集的程度。</span><span class="sxs-lookup"><span data-stu-id="a28b1-157">A bar to the right of the attribute shows which cluster the state favors, and the size of the bar shows how strongly the state favors the cluster.</span></span>  
  
 [<span data-ttu-id="a28b1-158">回到頁首</span><span class="sxs-lookup"><span data-stu-id="a28b1-158">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="cluster-transitions"></a><a name="BKMK_Transitions"></a><span data-ttu-id="a28b1-159">叢集轉換</span><span class="sxs-lookup"><span data-stu-id="a28b1-159">Cluster Transitions</span></span>  
 <span data-ttu-id="a28b1-160">藉由選取 **[群集轉換]** 索引標籤上的群集，您可以瀏覽所選取群集裡的時序狀態之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="a28b1-160">By selecting a cluster on the **Cluster Transitions** tab, you can browse the transitions between sequence states in the selected cluster.</span></span> <span data-ttu-id="a28b1-161">檢視器中的每一個節點都代表時序資料行的狀態。</span><span class="sxs-lookup"><span data-stu-id="a28b1-161">Each node in the viewer represents a state of the sequence column.</span></span> <span data-ttu-id="a28b1-162">箭頭代表兩個狀態之間的轉換以及與轉換相關聯的機率。</span><span class="sxs-lookup"><span data-stu-id="a28b1-162">An arrow represents a transition between two states and the probability that is associated with the transition.</span></span> <span data-ttu-id="a28b1-163">如果轉換回到原始節點，箭頭可指回到原始節點。</span><span class="sxs-lookup"><span data-stu-id="a28b1-163">If a transition returns back to the originating node, an arrow can point back to the originating node.</span></span>  
  
 <span data-ttu-id="a28b1-164">源自一個點的箭頭，代表節點是時序開頭的機率。</span><span class="sxs-lookup"><span data-stu-id="a28b1-164">An arrow that originates from a dot represents the probability that the node is the start of a sequence.</span></span> <span data-ttu-id="a28b1-165">造成 Null 的結束邊緣，則代表節點是時序結尾的機率。</span><span class="sxs-lookup"><span data-stu-id="a28b1-165">An ending edge that leads to a null represents the probability that the node is the end of the sequence.</span></span>  
  
 <span data-ttu-id="a28b1-166">您可以使用索引標籤左邊的滑桿來篩選節點的邊緣。</span><span class="sxs-lookup"><span data-stu-id="a28b1-166">You can filter the edge of the nodes by using the slider at the left of the tab.</span></span>  
  
 [<span data-ttu-id="a28b1-167">回到頁首</span><span class="sxs-lookup"><span data-stu-id="a28b1-167">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a><span data-ttu-id="a28b1-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a28b1-168">See Also</span></span>  
 <span data-ttu-id="a28b1-169">[採礦模型檢視器工作和操作說明](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="a28b1-169">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="a28b1-170">[採礦模型檢視器工作和操作說明](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="a28b1-170">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="a28b1-171">[Microsoft 時序群集演算法](microsoft-sequence-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="a28b1-171">[Microsoft Sequence Clustering Algorithm](microsoft-sequence-clustering-algorithm.md) </span></span>  
 <span data-ttu-id="a28b1-172">[資料採礦工具](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="a28b1-172">[Data Mining Tools](data-mining-tools.md) </span></span>  
 <span data-ttu-id="a28b1-173">[資料採礦模型檢視器](data-mining-model-viewers.md) </span><span class="sxs-lookup"><span data-stu-id="a28b1-173">[Data Mining Model Viewers](data-mining-model-viewers.md) </span></span>  
 [<span data-ttu-id="a28b1-174">使用 Microsoft 叢集檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="a28b1-174">Browse a Model Using the Microsoft Cluster Viewer</span></span>](browse-a-model-using-the-microsoft-cluster-viewer.md)  
  
  
