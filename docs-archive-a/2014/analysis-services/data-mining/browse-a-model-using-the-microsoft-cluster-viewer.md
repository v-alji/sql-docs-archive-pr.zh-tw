---
title: 使用 Microsoft 叢集檢視器流覽模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clusters [Analysis Services]
- discrimination [Analysis Services]
- names [Analysis Services], clusters
- Microsoft Cluster Viewer
- mining model content, viewing
- comparing clusters
- viewing clusters
- displaying clusters
- data mining [Analysis Services], clusters
- Cluster Viewer [Analysis Services]
- mining models [Analysis Services], clusters
ms.assetid: 591fe30b-d88f-4a71-94d4-4a3907fc275d
author: minewiskan
ms.author: owend
ms.openlocfilehash: d3597c97ad285d8ddc40b398723f6d3ec652ceb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606528"
---
# <a name="browse-a-model-using-the-microsoft-cluster-viewer"></a><span data-ttu-id="aaa18-102">使用 Microsoft 叢集檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="aaa18-102">Browse a Model Using the Microsoft Cluster Viewer</span></span>
  <span data-ttu-id="aaa18-103">中的叢集 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 檢視器 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會顯示以群集演算法建立的採礦模型 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="aaa18-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm.</span></span> <span data-ttu-id="aaa18-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 群集演算法是用來瀏覽資料以識別資料中的異常及建立預測的一種分割演算法。</span><span class="sxs-lookup"><span data-stu-id="aaa18-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm is a segmentation algorithm for use in exploring data to identify anomalies in the data and to create predictions.</span></span> <span data-ttu-id="aaa18-105">如需這個演算法的詳細資訊，請參閱 [Microsoft 群集演算法](microsoft-clustering-algorithm.md)。</span><span class="sxs-lookup"><span data-stu-id="aaa18-105">For more information about this algorithm, see [Microsoft Clustering Algorithm](microsoft-clustering-algorithm.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aaa18-106">若要檢視有關此模型中所用的方程式及所探索之模式的詳細資訊，請使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 一般內容樹狀檢視器。</span><span class="sxs-lookup"><span data-stu-id="aaa18-106">To view detailed information about the equations used in the model and the patterns that were discovered, use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="aaa18-107">如需詳細資訊，請參閱[使用 Microsoft 一般內容樹狀檢視器瀏覽模型](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)或 [Microsoft 一般內容樹狀檢視器 &#40;資料採礦&#41;](../microsoft-generic-content-tree-viewer-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="aaa18-107">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="aaa18-108">檢視器索引標籤</span><span class="sxs-lookup"><span data-stu-id="aaa18-108">Viewer Tabs</span></span>  
 <span data-ttu-id="aaa18-109">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中瀏覽採礦模型時，該模型會在適合它的檢視器中，顯示於資料採礦設計師的 **[採礦模型檢視器]** 索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="aaa18-109">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="aaa18-110">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 叢集檢視器會提供下列索引標籤，用來瀏覽叢集採礦模型：</span><span class="sxs-lookup"><span data-stu-id="aaa18-110">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer provides the following tabs for use in exploring clustering mining models:</span></span>  
  
-   [<span data-ttu-id="aaa18-111">群集圖表</span><span class="sxs-lookup"><span data-stu-id="aaa18-111">Cluster Diagram</span></span>](#BKMK_Diagram)  
  
-   [<span data-ttu-id="aaa18-112">叢集設定檔</span><span class="sxs-lookup"><span data-stu-id="aaa18-112">Cluster Profiles</span></span>](#BKMK_Profile)  
  
-   [<span data-ttu-id="aaa18-113">叢集特性</span><span class="sxs-lookup"><span data-stu-id="aaa18-113">Cluster Characteristics</span></span>](#BKMK_Characteristics)  
  
-   [<span data-ttu-id="aaa18-114">群集辨識</span><span class="sxs-lookup"><span data-stu-id="aaa18-114">Cluster Discrimination</span></span>](#BKMK_Discrimination)  
  
###  <a name="cluster-diagram"></a><a name="BKMK_Diagram"></a><span data-ttu-id="aaa18-115">群集圖表</span><span class="sxs-lookup"><span data-stu-id="aaa18-115">Cluster Diagram</span></span>  
 <span data-ttu-id="aaa18-116">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 叢集檢視器的 [叢集圖表]\*\*\*\* 索引標籤會顯示採礦模型中的所有叢集。</span><span class="sxs-lookup"><span data-stu-id="aaa18-116">The **Cluster Diagram** tab of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer displays all the clusters that are in a mining model.</span></span> <span data-ttu-id="aaa18-117">連接一個群集與另一個群集的線條陰影代表群集的相似程度。</span><span class="sxs-lookup"><span data-stu-id="aaa18-117">The shading of the line that connects one cluster to another represents the strength of the similarity of the clusters.</span></span> <span data-ttu-id="aaa18-118">如果陰影很淡或不存在，則表示群集不太相似。</span><span class="sxs-lookup"><span data-stu-id="aaa18-118">If the shading is light or nonexistent, the clusters are not very similar.</span></span> <span data-ttu-id="aaa18-119">當線條色彩加深時，連結的相似度就更高。</span><span class="sxs-lookup"><span data-stu-id="aaa18-119">As the line becomes darker, the similarity of the links becomes stronger.</span></span> <span data-ttu-id="aaa18-120">您可以調整群集右邊的滑桿，來調整檢視器要顯示的線條數目。</span><span class="sxs-lookup"><span data-stu-id="aaa18-120">You can adjust how many lines the viewer shows by adjusting the slider to the right of the clusters.</span></span> <span data-ttu-id="aaa18-121">降低滑桿只顯示最強的連結。</span><span class="sxs-lookup"><span data-stu-id="aaa18-121">Lowering the slider shows only the strongest links.</span></span>  
  
 <span data-ttu-id="aaa18-122">依預設，陰影代表群集的母體。</span><span class="sxs-lookup"><span data-stu-id="aaa18-122">By default, the shade represents the population of the cluster.</span></span> <span data-ttu-id="aaa18-123">藉由使用 [ **ShadingVariable** ] 和 [**狀態**] 選項，您可以選取陰影所代表的屬性和狀態配對。</span><span class="sxs-lookup"><span data-stu-id="aaa18-123">By using the **ShadingVariable** and **State** options, you can select which attribute and state pair the shading represents.</span></span> <span data-ttu-id="aaa18-124">陰影愈深，表示特定狀態的屬性散發就愈大。</span><span class="sxs-lookup"><span data-stu-id="aaa18-124">The darker the shading, the greater the attribute distribution is for a specific state.</span></span> <span data-ttu-id="aaa18-125">當陰影變淡時，散發跟著減少。</span><span class="sxs-lookup"><span data-stu-id="aaa18-125">The distribution decreases as the shading gets lighter.</span></span>  
  
 <span data-ttu-id="aaa18-126">若要重新命名叢集，請以滑鼠右鍵按一下其節點，然後選取 [重新命名叢集]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aaa18-126">To rename a cluster, right-click its node and select **Rename Cluster**.</span></span> <span data-ttu-id="aaa18-127">新名稱會保存在伺服器上。</span><span class="sxs-lookup"><span data-stu-id="aaa18-127">The new name is persisted to the server.</span></span>  
  
 <span data-ttu-id="aaa18-128">若要將圖表的可見區段複製到剪貼簿，請按一下 **[複製圖表檢視]**。</span><span class="sxs-lookup"><span data-stu-id="aaa18-128">To copy the visible section of the diagram to the Clipboard, click **Copy Graph View**.</span></span> <span data-ttu-id="aaa18-129">若要複製完整圖表，請按一下 **[複製整個圖表]**。</span><span class="sxs-lookup"><span data-stu-id="aaa18-129">To copy the complete diagram, click **Copy Entire Graph**.</span></span> <span data-ttu-id="aaa18-130">您也可以使用 **[放大]** 和 **[縮小]** 來放大和縮小，或使用 **[將圖表縮放至視窗大小]**，使圖表符合視窗大小。</span><span class="sxs-lookup"><span data-stu-id="aaa18-130">You can also zoom in and out by using **Zoom In** and **Zoom Out**, or you can fit the diagram to the screen by using **Scale Diagram to Fit in Window**.</span></span>  
  
 [<span data-ttu-id="aaa18-131">回到頁首</span><span class="sxs-lookup"><span data-stu-id="aaa18-131">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="cluster-profiles"></a><a name="BKMK_Profile"></a><span data-ttu-id="aaa18-132">叢集設定檔</span><span class="sxs-lookup"><span data-stu-id="aaa18-132">Cluster Profiles</span></span>  
 <span data-ttu-id="aaa18-133">[叢集設定檔]\*\*\*\* 索引標籤會提供模型中的演算法所建立之叢集的整體檢視。</span><span class="sxs-lookup"><span data-stu-id="aaa18-133">The **Cluster Profiles** tab provides an overall view of the clusters that the algorithm in your model creates.</span></span> <span data-ttu-id="aaa18-134">這個檢視會顯示每一個屬性以及該屬性在每一個群集中的分佈。</span><span class="sxs-lookup"><span data-stu-id="aaa18-134">This view displays each attribute, together with the distribution of the attribute in each cluster.</span></span> <span data-ttu-id="aaa18-135">每一個資料格的資訊提示會顯示散發統計資料，而每一個資料行標題的資訊提示會顯示群集母體擴展。</span><span class="sxs-lookup"><span data-stu-id="aaa18-135">An InfoTip for each cell displays the distribution statistics, and an InfoTip for each column heading displays the cluster population.</span></span> <span data-ttu-id="aaa18-136">分隔屬性是以彩色列顯示，而連續屬性是以鑽石圖顯示，鑽石圖代表每一個群集的平均差和標準差。</span><span class="sxs-lookup"><span data-stu-id="aaa18-136">Discrete attributes are shown as colored bars, and continuous attributes are shown as a diamond chart that represents the mean and standard deviation in each cluster.</span></span> <span data-ttu-id="aaa18-137">[長條圖列] \*\*\*\* 選項會控制長條圖中可見的橫條數。</span><span class="sxs-lookup"><span data-stu-id="aaa18-137">The **Histogram bars** option controls the number of bars that are visible in the histogram.</span></span> <span data-ttu-id="aaa18-138">如果總列數超出您選擇要顯示的列數，就會保留最重要的列，而其餘的列將會分組放入灰色值區中。</span><span class="sxs-lookup"><span data-stu-id="aaa18-138">If more bars exist than you choose to display, the bars of highest importance are retained, and the remaining bars are grouped together into a gray bucket.</span></span>  
  
 <span data-ttu-id="aaa18-139">您可以變更群集的預設名稱，使名稱更具描述性。</span><span class="sxs-lookup"><span data-stu-id="aaa18-139">You can change the default names of the clusters, to make the names more descriptive.</span></span> <span data-ttu-id="aaa18-140">請以滑鼠右鍵按一下叢集的資料行標題並選取 [重新命名叢集]\*\*\*\*，來重新命名叢集。</span><span class="sxs-lookup"><span data-stu-id="aaa18-140">Rename a cluster by right-clicking its column heading and selecting **Rename cluster**.</span></span> <span data-ttu-id="aaa18-141">您也可以選取 [隱藏資料行]\*\*\*\* 來隱藏叢集。</span><span class="sxs-lookup"><span data-stu-id="aaa18-141">You can also hide clusters by selecting **Hide column**.</span></span>  
  
 <span data-ttu-id="aaa18-142">若要開啟一個能提供更大、更詳細之叢集檢視的視窗，請按兩下 [狀態]\*\*\*\* 資料行的資料格或檢視器中的長條圖。</span><span class="sxs-lookup"><span data-stu-id="aaa18-142">To open a window that provides a larger, more detailed view of the clusters, double-click either a cell in the **States** column or a histogram in the viewer.</span></span>  
  
 <span data-ttu-id="aaa18-143">按一下資料行標題，即可依該群集的重要性順序來排序屬性。</span><span class="sxs-lookup"><span data-stu-id="aaa18-143">Click a column heading to sort the attributes in order of importance for that cluster.</span></span> <span data-ttu-id="aaa18-144">您也可以拖曳資料行，在檢視器中重新排列它們。</span><span class="sxs-lookup"><span data-stu-id="aaa18-144">You can also drag columns to reorder them in the viewer.</span></span>  
  
 [<span data-ttu-id="aaa18-145">回到頁首</span><span class="sxs-lookup"><span data-stu-id="aaa18-145">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="cluster-characteristics"></a><a name="BKMK_Characteristics"></a> <span data-ttu-id="aaa18-146">群集特性</span><span class="sxs-lookup"><span data-stu-id="aaa18-146">Cluster Characteristics</span></span>  
 <span data-ttu-id="aaa18-147">若要使用 **[群集特性]** 索引標籤，請從 **[群集]** 清單中選取群集。</span><span class="sxs-lookup"><span data-stu-id="aaa18-147">To use the **Cluster Characteristics** tab, select a cluster from the **Cluster** list.</span></span> <span data-ttu-id="aaa18-148">選取群集之後，您可以檢查構成該特定群集的特性。</span><span class="sxs-lookup"><span data-stu-id="aaa18-148">After you select a cluster, you can examine the characteristics that make up that specific cluster.</span></span> <span data-ttu-id="aaa18-149">群集包含的屬性將列於 **[變數]** 資料行中，而所列屬性的狀態則列於 **[值]** 資料行中。</span><span class="sxs-lookup"><span data-stu-id="aaa18-149">The attributes that the cluster contains are listed in the **Variables** columns, and the state of the listed attribute is listed in the **Values** column.</span></span> <span data-ttu-id="aaa18-150">屬性狀態是依重要性列出，以它們出現在群集裡的機率來描述。</span><span class="sxs-lookup"><span data-stu-id="aaa18-150">Attribute states are listed in order of importance, described by the probability that they will appear in the cluster.</span></span> <span data-ttu-id="aaa18-151">機率會在 **[機率]** 資料行中顯示。</span><span class="sxs-lookup"><span data-stu-id="aaa18-151">The probability is shown in the **Probability** column.</span></span>  
  
 [<span data-ttu-id="aaa18-152">回到頁首</span><span class="sxs-lookup"><span data-stu-id="aaa18-152">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="cluster-discrimination"></a><a name="BKMK_Discrimination"></a><span data-ttu-id="aaa18-153">群集辨識</span><span class="sxs-lookup"><span data-stu-id="aaa18-153">Cluster Discrimination</span></span>  
 <span data-ttu-id="aaa18-154">您可以使用 [叢集辨識]\*\*\*\* 索引標籤來比較兩個叢集之間的屬性。</span><span class="sxs-lookup"><span data-stu-id="aaa18-154">You can use the **Cluster Discrimination** tab to compare attributes between two clusters.</span></span> <span data-ttu-id="aaa18-155">請使用 **[群集 1]** 和 **[群集 2]** 清單來選取要比較的群集。</span><span class="sxs-lookup"><span data-stu-id="aaa18-155">Use the **Cluster 1** and **Cluster 2** lists to select the clusters to compare.</span></span> <span data-ttu-id="aaa18-156">檢視器會判斷群集間最重要的差異，並依重要性的順序顯示與差異相關聯的屬性狀態。</span><span class="sxs-lookup"><span data-stu-id="aaa18-156">The viewer determines the most important differences between the clusters, and displays the attribute states that are associated with the differences, in order of importance.</span></span> <span data-ttu-id="aaa18-157">屬性右邊的列會顯示狀態喜好的群集，而列的大小會顯示狀態喜好群集的程度。</span><span class="sxs-lookup"><span data-stu-id="aaa18-157">A bar to the right of the attribute shows which cluster the state favors, and the size of the bar shows how strongly the state favors the cluster.</span></span>  
  
 [<span data-ttu-id="aaa18-158">回到頁首</span><span class="sxs-lookup"><span data-stu-id="aaa18-158">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a><span data-ttu-id="aaa18-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aaa18-159">See Also</span></span>  
 <span data-ttu-id="aaa18-160">[Microsoft 群集演算法](microsoft-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="aaa18-160">[Microsoft Clustering Algorithm](microsoft-clustering-algorithm.md) </span></span>  
 <span data-ttu-id="aaa18-161">[採礦模型檢視器工作和操作說明](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="aaa18-161">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="aaa18-162">[採礦模型檢視器工作和操作說明](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="aaa18-162">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="aaa18-163">[資料採礦工具](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="aaa18-163">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="aaa18-164">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="aaa18-164">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
  
