---
title: 探索時序群集模型 (中繼資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f8a485d5-47ed-4dd5-bb66-ef4d6d463845
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bac603d2480ec1f344d14351757027de749f8c86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704469"
---
# <a name="exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="95deb-102">探索時序群集模型 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="95deb-102">Exploring the Sequence Clustering Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="95deb-103">現在您已建立**具有區域**模型的時序群集，您可以使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 資料採礦設計師的 [**採礦模型檢視器**] 索引標籤中的時序群集檢視器來探索它。</span><span class="sxs-lookup"><span data-stu-id="95deb-103">Now that you have built the **Sequence Clustering with Region** model, you can explore it by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering Viewer in the **Mining Model Viewer** tab of Data Mining Designer.</span></span> <span data-ttu-id="95deb-104">時序 [!INCLUDE[msCoName](../includes/msconame-md.md)] 群集檢視器包含五個索引標籤：**群集圖表**、叢集**設定檔**、叢集**特性**、 **ClusterDiscrimination**和**狀態轉換**。</span><span class="sxs-lookup"><span data-stu-id="95deb-104">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Cluster Viewer contains five tabs: **Cluster Diagram**, **Cluster Profiles**, **Cluster Characteristics**, **ClusterDiscrimination**, and **State Transitions**.</span></span> <span data-ttu-id="95deb-105">如需如何使用此檢視器的詳細資訊，請參閱[使用 Microsoft 時序群集檢視器流覽模型](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="95deb-105">For more information about how to use this viewer, see [Browse a Model Using the Microsoft Sequence Cluster Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md).</span></span>  
  
-   <span data-ttu-id="95deb-106">[[群集圖表] 索引標籤](#bkmk_CDiagram)</span><span class="sxs-lookup"><span data-stu-id="95deb-106">[Cluster Diagram tab](#bkmk_CDiagram)</span></span>  
  
-   [<span data-ttu-id="95deb-107">群集設定檔索引標籤</span><span class="sxs-lookup"><span data-stu-id="95deb-107">Cluster Profiles tab</span></span>](#bkmk_CProfiles)  
  
-   [<span data-ttu-id="95deb-108">群集特性索引標籤</span><span class="sxs-lookup"><span data-stu-id="95deb-108">Cluster Characteristics tab</span></span>](#bkmk_CChars)  
  
-   [<span data-ttu-id="95deb-109">群集辨識索引標籤</span><span class="sxs-lookup"><span data-stu-id="95deb-109">Cluster Discrimination tab</span></span>](#bkmk_CDiscrim2)  
  
-   [<span data-ttu-id="95deb-110">狀態轉換索引標籤</span><span class="sxs-lookup"><span data-stu-id="95deb-110">State Transitions tab</span></span>](#bkmk_StateTran)  
  
-   [<span data-ttu-id="95deb-111">一般內容檢視</span><span class="sxs-lookup"><span data-stu-id="95deb-111">Generic Content View</span></span>](#bkmk_Generic)  
  
##  <a name="cluster-diagram-tab"></a><a name="bkmk_CDiagram"></a><span data-ttu-id="95deb-112">[群集圖表] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="95deb-112">Cluster Diagram Tab</span></span>  
 <span data-ttu-id="95deb-113">[**群集圖表**] 索引標籤會以圖形方式顯示演算法在資料庫中探索到的叢集。</span><span class="sxs-lookup"><span data-stu-id="95deb-113">The **Cluster Diagram** tab graphically displays the clusters that the algorithm discovered in the database.</span></span> <span data-ttu-id="95deb-114">圖表的配置代表群集的關聯性，而且類似的群集會緊密地聚集在一起。</span><span class="sxs-lookup"><span data-stu-id="95deb-114">The layout in the diagram represents the relationships of the clusters, with similar clusters grouped close together.</span></span> <span data-ttu-id="95deb-115">依預設，每一個節點的陰影都代表群集中所有案例的密度：節點的陰影越暗，表示它所包含的案例越多。</span><span class="sxs-lookup"><span data-stu-id="95deb-115">By default, the shade of each node represents the density of all cases in the cluster: the darker the shade of the node, the more cases it contains.</span></span> <span data-ttu-id="95deb-116">您可以變更節點陰影的意義，使它在每一個群集中代表屬性和狀態的支援。</span><span class="sxs-lookup"><span data-stu-id="95deb-116">You can change the meaning of the shading of the nodes so that it represents support, within each cluster, for an attribute and a state.</span></span>  
  
 <span data-ttu-id="95deb-117">您也可以重新命名群集，讓您可以更輕鬆地識別及處理目標群集。</span><span class="sxs-lookup"><span data-stu-id="95deb-117">You can also rename the clusters, to make it easier to identify and work with target clusters.</span></span> <span data-ttu-id="95deb-118">在此教學課程中，我們將會重新命名太平洋地區具有最高客戶百分比的群集，以及整體上具有最多案例的群集。</span><span class="sxs-lookup"><span data-stu-id="95deb-118">For this tutorial, you will rename the cluster that has the highest percentage of customers from the Pacific region, and the cluster that has the most cases overall.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95deb-119">當您重新處理此模型時，指派給特定群集的案例可能會變更 (視資料和模型參數而定)。</span><span class="sxs-lookup"><span data-stu-id="95deb-119">The cases that are assigned to specific clusters might change when you reprocess the model, depending on the data and the model parameters.</span></span> <span data-ttu-id="95deb-120">此外，如果您重新命名群集，在您重新處理採礦模型時將會遺失名稱。</span><span class="sxs-lookup"><span data-stu-id="95deb-120">Also, if you rename clusters, the names will be lost when you reprocess the mining model.</span></span>  
  
#### <a name="to-change-the-attribute-used-for-highlighting-clusters"></a><span data-ttu-id="95deb-121">若要變更用於反白顯示群集的屬性</span><span class="sxs-lookup"><span data-stu-id="95deb-121">To change the attribute used for highlighting clusters</span></span>  
  
1.  <span data-ttu-id="95deb-122">在 [**陰影變數**] 清單中，選取 [**模型**]。</span><span class="sxs-lookup"><span data-stu-id="95deb-122">In the **Shading Variable** list, select **Model**.</span></span>  
  
2.  <span data-ttu-id="95deb-123">選取 [**狀態**] 清單中的 [**迴圈端點**]。</span><span class="sxs-lookup"><span data-stu-id="95deb-123">Select **Cycling Cap** in the **State** list.</span></span>  
  
     <span data-ttu-id="95deb-124">此圖表會更新，以顯示每一個群集中選定產品的聚集程度。</span><span class="sxs-lookup"><span data-stu-id="95deb-124">The diagram updates to show the concentration of the selected product in each of the clusters.</span></span> <span data-ttu-id="95deb-125">具有最暗陰影的群集所包含的 Cycling Cap 密度最高。</span><span class="sxs-lookup"><span data-stu-id="95deb-125">The cluster that has the darkest shading contains the highest density of cycling caps.</span></span> <span data-ttu-id="95deb-126">您可以變更陰影變數，以使用任何輸入資料行的任何狀態。</span><span class="sxs-lookup"><span data-stu-id="95deb-126">You can change the shading variable to use any state of any input column.</span></span>  
  
3.  <span data-ttu-id="95deb-127">在 [**陰影變數**] 清單中，選取 [**填入**]。</span><span class="sxs-lookup"><span data-stu-id="95deb-127">In the **Shading Variable** list, select **Population**.</span></span>  
  
     <span data-ttu-id="95deb-128">當您將陰影變數變更成母體時，此圖表就會更新，根據大小來比較群集。</span><span class="sxs-lookup"><span data-stu-id="95deb-128">When you change the shading variable to population, the diagram updates to compare the clusters by size.</span></span> <span data-ttu-id="95deb-129">具有最暗陰影的群集所包含的案例要比其他群集多。</span><span class="sxs-lookup"><span data-stu-id="95deb-129">The cluster that has the darkest shading contains more cases than the other clusters.</span></span>  
  
#### <a name="to-rename-nodes-in-the-model"></a><span data-ttu-id="95deb-130">若要重新命名模型內的節點</span><span class="sxs-lookup"><span data-stu-id="95deb-130">To rename nodes in the model</span></span>  
  
1.  <span data-ttu-id="95deb-131">將 [**陰影變數**] 變更為 `Region` ，並將 [**狀態**] 設定為 [**太平洋**]。</span><span class="sxs-lookup"><span data-stu-id="95deb-131">Change **Shading Variable** to `Region`, and set **State** to **Pacific**.</span></span>  
  
2.  <span data-ttu-id="95deb-132">反白顯示圖表中最暗的節點。</span><span class="sxs-lookup"><span data-stu-id="95deb-132">Highlight the darkest node in the graph.</span></span>  
  
3.  <span data-ttu-id="95deb-133">在此叢集上按一下滑鼠右鍵，然後選取 [**重新命名**叢集]。</span><span class="sxs-lookup"><span data-stu-id="95deb-133">Right-click this cluster and select **Rename Cluster.**</span></span>  
  
4.  <span data-ttu-id="95deb-134">輸入 [太平洋叢集名稱]**。**</span><span class="sxs-lookup"><span data-stu-id="95deb-134">Type the name**Pacific Cluster.**</span></span>  
  
5.  <span data-ttu-id="95deb-135">將 [**陰影變數**] 的值**變更為 [** 擴展]。</span><span class="sxs-lookup"><span data-stu-id="95deb-135">Change the value of **Shading Variable** to **Population**.</span></span>  
  
6.  <span data-ttu-id="95deb-136">在更新的圖表中，尋找最暗的群集，這應該是最大的群集。</span><span class="sxs-lookup"><span data-stu-id="95deb-136">In the updated graph, locate the darkest cluster, which should be the largest cluster.</span></span> <span data-ttu-id="95deb-137">如果您不能從陰影來判斷哪一個群集最大，請將滑鼠暫時放在每一個群集的上方，並檢視工具提示，然後選擇包含最多案例的群集。</span><span class="sxs-lookup"><span data-stu-id="95deb-137">If you cannot tell by the shading which cluster is largest, pause the mouse over each cluster and view the ToolTip, and then choose the cluster that contains the most cases.</span></span>  
  
7.  <span data-ttu-id="95deb-138">在此叢集上按一下滑鼠右鍵，然後選取 [**重新命名**叢集]。</span><span class="sxs-lookup"><span data-stu-id="95deb-138">Right-click this cluster and select **Rename Cluster**.</span></span> <span data-ttu-id="95deb-139">輸入新的名稱 `Largest Cluster` 。</span><span class="sxs-lookup"><span data-stu-id="95deb-139">Type the new name, `Largest Cluster`.</span></span>  
  
 <span data-ttu-id="95deb-140">您可以從代表此群集的節點鑽研，以檢視位於每一個群集內之案例的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="95deb-140">You can drill through from the node that represents the cluster to view details of the cases that are in each cluster.</span></span> <span data-ttu-id="95deb-141">如果您想要針對分析的結果採取動作，例如傳送電子郵件給客戶，這樣的作法會很實用。</span><span class="sxs-lookup"><span data-stu-id="95deb-141">This can be useful if you want to take action on the results of your analysis, such as sending e-mail to a customer.</span></span> <span data-ttu-id="95deb-142">您也可以瀏覽您已併入結構內，但是未在模型內使用之案例的其他屬性，例如 Region 和 IncomeGroup。</span><span class="sxs-lookup"><span data-stu-id="95deb-142">You can also browse the other attributes of the cases that you included in the structure but did not use in the model, such as Region and IncomeGroup.</span></span> <span data-ttu-id="95deb-143">如需深入瞭解從採礦模型到基礎案例的詳細資訊，請參閱[&#40;資料採礦&#41;的鑽看查詢](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="95deb-143">For more information about drilling through from mining models to the underlying cases, see [Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).</span></span>  
  
#### <a name="to-drill-through-to-details-from-the-cluster-diagram"></a><span data-ttu-id="95deb-144">若要從群集圖表鑽研到詳細資料</span><span class="sxs-lookup"><span data-stu-id="95deb-144">To drill through to details from the Cluster diagram</span></span>  
  
1.  <span data-ttu-id="95deb-145">按一下滑鼠右鍵 `Pacific Cluster` ，選取**Drill Through**[向下切入]，然後選取 [**模型和結構資料行**]。</span><span class="sxs-lookup"><span data-stu-id="95deb-145">Right-click `Pacific Cluster`, select **Drill Through**, and then select **Model and Structure columns**.</span></span>  
  
     <span data-ttu-id="95deb-146">[**流覽**] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="95deb-146">The **Drill Through** dialog box opens.</span></span> <span data-ttu-id="95deb-147">未在模型中使用，但可供查詢的資料行前面會加上**結構**。</span><span class="sxs-lookup"><span data-stu-id="95deb-147">Columns that are not used in the model but that are available for querying are prefixed with **Structure**.</span></span>  
  
     <span data-ttu-id="95deb-148">您可以看到這個群集包含的客戶大多是來自太平洋地區，只有少數客戶來自其他地區。</span><span class="sxs-lookup"><span data-stu-id="95deb-148">You can see that this cluster contains mostly customers from the Pacific region, with only a few customers from other regions.</span></span>  
  
2.  <span data-ttu-id="95deb-149">按一下巢狀資料行 v Assoc Seq Line Items 中的加號，以檢視特定客戶訂單中項目的序列。</span><span class="sxs-lookup"><span data-stu-id="95deb-149">Click the plus sign in the nested column v Assoc Seq Line Items to view the sequence of items in a particular customer order.</span></span>  
  
3.  <span data-ttu-id="95deb-150">關閉 [**演練**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="95deb-150">Close the **Drill Through** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="95deb-151">[**播放**] 按鈕可讓您重新查詢資料;不過，除非其他進程已在背景中動態更新模型，否則重新查詢不會變更顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="95deb-151">The **Play** button enables you to requery the data; however, requerying does not change the data that is displayed, unless the model has been dynamically updated in the background by some other process.</span></span>  
  
 [<span data-ttu-id="95deb-152">回到頁首</span><span class="sxs-lookup"><span data-stu-id="95deb-152">Back to Top</span></span>](#bkmk_CDiagram)  
  
##  <a name="cluster-profiles-tab"></a><a name="bkmk_CProfiles"></a><span data-ttu-id="95deb-153">群集設定檔索引標籤</span><span class="sxs-lookup"><span data-stu-id="95deb-153">Cluster Profiles Tab</span></span>  
 <span data-ttu-id="95deb-154">[**群集設定檔**] 索引標籤會顯示每個叢集中的序列。</span><span class="sxs-lookup"><span data-stu-id="95deb-154">The **Cluster Profiles** tab displays the sequences that are in each cluster.</span></span> <span data-ttu-id="95deb-155">群集會列在 [**狀態**] 資料行右邊的個別資料行中。</span><span class="sxs-lookup"><span data-stu-id="95deb-155">The clusters are listed in individual columns to the right of the **States** column.</span></span>  
  
 <span data-ttu-id="95deb-156">在檢視器中，[**模型**] 資料列描述叢集中專案的整體分佈，而 [模型] 中的 [**範例**] 資料列則包含這些專案的序列。</span><span class="sxs-lookup"><span data-stu-id="95deb-156">In the viewer, the **Model** row describes the overall distribution of items in a cluster, and the **Model.samples** row contains sequences of the items.</span></span> <span data-ttu-id="95deb-157">模型中每個資料格的色彩序列的每一行 **。 [範例**] 資料清單示叢集中隨機選取之使用者的行為。</span><span class="sxs-lookup"><span data-stu-id="95deb-157">Each line of the color sequences in each cell of the **Model.samples** row represents the behavior of a randomly selected user in the cluster.</span></span>  
  
 <span data-ttu-id="95deb-158">個別序列長條圖中的每個顏色都代表一個產品型號。</span><span class="sxs-lookup"><span data-stu-id="95deb-158">Each color in an individual sequence histogram represents a product model.</span></span> <span data-ttu-id="95deb-159">採礦圖例會同時使用色彩編碼和產品型號名稱來顯示產品的序列。</span><span class="sxs-lookup"><span data-stu-id="95deb-159">The Mining Legend shows you the sequences of products by using both color-coding and the product model names.</span></span> <span data-ttu-id="95deb-160">如果您已經將其他資料行加入到模型內進行群集，例如 Region 或 Income Group，檢視器將會針對每一個資料行各包含另一個資料列，該資料列會顯示這些值在每一個群集內的分佈。</span><span class="sxs-lookup"><span data-stu-id="95deb-160">If you have added other columns to the model for clustering, such as Region or Income Group, the viewer will contain an additional row for each column that shows the distribution of these values within each cluster.</span></span>  
  
#### <a name="to-view-the-sequences-that-are-most-common-in-a-cluster"></a><span data-ttu-id="95deb-161">若要檢視群集中最常見的序列</span><span class="sxs-lookup"><span data-stu-id="95deb-161">To view the sequences that are most common in a cluster</span></span>  
  
1.  <span data-ttu-id="95deb-162">以滑鼠右鍵按一下叢集資料行中的**模型**資料列 `Largest Cluster` ，然後選取 [**顯示圖例**]。</span><span class="sxs-lookup"><span data-stu-id="95deb-162">Right-click the **Model** row in the column for the cluster `Largest Cluster`, and select **Show Legend**.</span></span>  
  
     <span data-ttu-id="95deb-163">[**色彩**] 資料行包含一個陰影長條，表示在序列中找到之專案的頻率。</span><span class="sxs-lookup"><span data-stu-id="95deb-163">The **Color** column contains a shaded bar that indicates the frequency of items found in sequences.</span></span> <span data-ttu-id="95deb-164">每一個項目都由不同的色彩表示。</span><span class="sxs-lookup"><span data-stu-id="95deb-164">Each item is represented by a different color.</span></span> <span data-ttu-id="95deb-165">[**意義**] 資料行會列出每種色彩的產品型號名稱。</span><span class="sxs-lookup"><span data-stu-id="95deb-165">The **Meaning** column lists the product model names for each color.</span></span> <span data-ttu-id="95deb-166">[**散發**] 資料行會告訴您一個序列中包含此專案的案例百分比。</span><span class="sxs-lookup"><span data-stu-id="95deb-166">The **Distribution** column tells you the percentage of cases that contained this item in a sequence.</span></span>  
  
2.  <span data-ttu-id="95deb-167">關閉 [**挖掘圖例**]。</span><span class="sxs-lookup"><span data-stu-id="95deb-167">Close the **Mining Legend**.</span></span>  
  
3.  <span data-ttu-id="95deb-168">以滑鼠右鍵按一下資料行中的 [模型] 和 [**範例**] 資料列，其中包含標題、**填入，** 然後選取 [**顯示圖例**]。</span><span class="sxs-lookup"><span data-stu-id="95deb-168">Right-click the **Model.samples** row in the column with the heading, **Population,** and select **Show Legend**.</span></span>  
  
4.  <span data-ttu-id="95deb-169">掃描整體模型中的序列清單`.`</span><span class="sxs-lookup"><span data-stu-id="95deb-169">Scan the list of sequences in the overall model`.`</span></span>  
  
     <span data-ttu-id="95deb-170">[採礦圖例] 會先列出最常見的序列，好讓您可以看到 Mountain Tire Tube 在許多序列中都是第一個項目。</span><span class="sxs-lookup"><span data-stu-id="95deb-170">The Mining Legend lists the most common sequences first, so you can see that Mountain Tire Tube is the first item in many sequences.</span></span> <span data-ttu-id="95deb-171">這表示客戶非常可能會先將 Mountain Tire Tube 放在購物籃中。</span><span class="sxs-lookup"><span data-stu-id="95deb-171">This means that a customer is very likely to put the Mountain Tire Tube in the shopping basket first.</span></span>  
  
#### <a name="to-drill-through-to-cases-from-the-cluster-viewer"></a><span data-ttu-id="95deb-172">若要從群集檢視器鑽研到案例</span><span class="sxs-lookup"><span data-stu-id="95deb-172">To drill through to cases from the cluster viewer</span></span>  
  
1.  <span data-ttu-id="95deb-173">在 [屬性] 窗格中向下鍵，直到您找到該屬性的資料列為止 `Region` 。</span><span class="sxs-lookup"><span data-stu-id="95deb-173">Scroll down in the Attribute pane until you find the row for the `Region` attribute.</span></span>  
  
     <span data-ttu-id="95deb-174">資料列包含模型中每個叢集的長條圖，再加上一個用於擴展**的額外長條圖，表示**模型中使用的整組案例。</span><span class="sxs-lookup"><span data-stu-id="95deb-174">The row contains a histogram for each cluster in the model, plus one additional histogram for **Population**, meaning the entire set of cases used in the model.</span></span> <span data-ttu-id="95deb-175">長條圖是一個具有不同色彩的長條，每一個色彩都代表一個屬性，而該屬性之色彩區段的大小則代表具有該屬性之案例的百分比。</span><span class="sxs-lookup"><span data-stu-id="95deb-175">A histogram is a bar with different colors in it, where each color represents an attribute, and the size of the colored section for that attribute represents the percentage of cases with that attribute.</span></span>  
  
2.  <span data-ttu-id="95deb-176">比較您重新命名的叢集與的長條圖 `Pacific Cluster` `Largest Cluster` 。</span><span class="sxs-lookup"><span data-stu-id="95deb-176">Compare the histograms for the clusters that you renamed `Pacific Cluster` and `Largest Cluster`.</span></span> <span data-ttu-id="95deb-177">每一個群集都會出現在不同的資料行內。</span><span class="sxs-lookup"><span data-stu-id="95deb-177">Each cluster appears in a different column.</span></span>  
  
     <span data-ttu-id="95deb-178">兩者看起來都是純色，但是色彩不同。</span><span class="sxs-lookup"><span data-stu-id="95deb-178">Both look like solid colors, but the colors are different.</span></span>  
  
3.  <span data-ttu-id="95deb-179">在資料 `Region` 列中，將滑鼠停留在的彩色長條圖上方 `Largest Cluster` 。</span><span class="sxs-lookup"><span data-stu-id="95deb-179">In the `Region` row, pause the mouse over the colored histogram for `Largest Cluster`.</span></span>  
  
     <span data-ttu-id="95deb-180">工具提示會顯示值，這些值代表每一個地區之案例的實際百分比。</span><span class="sxs-lookup"><span data-stu-id="95deb-180">The ToolTip displays values that show the actual percentages of cases from each region.</span></span>  
  
4.  <span data-ttu-id="95deb-181">以滑鼠右鍵按一下資料列中的彩色長條圖，選取 [向下切入] `Region` `Pacific Cluster` ，然後選取 [**僅模型** **Drill Through**資料行]。</span><span class="sxs-lookup"><span data-stu-id="95deb-181">Right-click the colored histogram in the `Region` row for `Pacific Cluster`, select **Drill Through**, and then select **Model Columns Only**.</span></span>  
  
5.  <span data-ttu-id="95deb-182">移動捲軸來檢閱這個群集中的所有客戶。</span><span class="sxs-lookup"><span data-stu-id="95deb-182">Move the scroll bar to review all of the customers in this cluster.</span></span>  
  
     <span data-ttu-id="95deb-183">同樣地，鑽研到詳細資料可讓您看到此群集大多包含來自太平洋地區的訂單，但也有少數來自北美和歐洲地區。</span><span class="sxs-lookup"><span data-stu-id="95deb-183">Again, from drilling through to the details you can see that the cluster contains mostly orders from the Pacific region but also a few from the North America and Europe regions.</span></span>  
  
6.  <span data-ttu-id="95deb-184">關閉 [**演練**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="95deb-184">Close the **Drill Through** dialog box.</span></span>  
  
 [<span data-ttu-id="95deb-185">回到頁首</span><span class="sxs-lookup"><span data-stu-id="95deb-185">Back to Top</span></span>](#bkmk_CDiagram)  
  
##  <a name="cluster-characteristics-tab"></a><a name="bkmk_CChars"></a><span data-ttu-id="95deb-186">群集特性索引標籤</span><span class="sxs-lookup"><span data-stu-id="95deb-186">Cluster Characteristics Tab</span></span>  
 <span data-ttu-id="95deb-187">[叢集**特性**] 索引標籤會以視覺化方式呈現所選叢集之屬性值重要性的橫條，來匯總叢集中各狀態之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="95deb-187">The **Cluster Characteristics** tab summarizes the transitions between states in a cluster by displaying bars that visually represent the importance of the attribute value for the selected cluster.</span></span> <span data-ttu-id="95deb-188">[**變數**] 資料行會告訴您所選叢集或擴展所需的模型為何：特定值或值之間的關聯性，也就是所謂的*轉換*。</span><span class="sxs-lookup"><span data-stu-id="95deb-188">The **Variables** column tells you what the model found to be important for the selected cluster or population: either a particular value or the relationship between values, known as *transition*.</span></span> <span data-ttu-id="95deb-189">[**值**] 資料行會提供有關值或轉換的詳細資訊，**而 [機率**] 資料行則會以視覺方式表示這個屬性或轉換的權數。</span><span class="sxs-lookup"><span data-stu-id="95deb-189">The **Values** column provides more detail about the value or transition, and the **Probability** column visually represents the weight of this attribute or transition.</span></span>  
  
#### <a name="to-view-the-important-attributes-for-a-cluster"></a><span data-ttu-id="95deb-190">若要檢視群集的重要屬性</span><span class="sxs-lookup"><span data-stu-id="95deb-190">To view the important attributes for a cluster</span></span>  
  
1.  <span data-ttu-id="95deb-191">**在 [叢集**] 下拉式清單中，選取 [] `Pacific Cluster` 。</span><span class="sxs-lookup"><span data-stu-id="95deb-191">In the **Cluster** dropdown list, select `Pacific Cluster`.</span></span>  
  
     <span data-ttu-id="95deb-192">清單會更新，以顯示您重新命名之叢集的特性 `Pacific Cluster` 。</span><span class="sxs-lookup"><span data-stu-id="95deb-192">The list updates to show the characteristics of the cluster that you renamed `Pacific Cluster`.</span></span> <span data-ttu-id="95deb-193">在此叢集中，最重要的特性是 `Region` 。</span><span class="sxs-lookup"><span data-stu-id="95deb-193">In this cluster, the most important characteristic is `Region`.</span></span>  
  
2.  <span data-ttu-id="95deb-194">將滑鼠停留在資料列中的陰影橫條上 `Region` 。</span><span class="sxs-lookup"><span data-stu-id="95deb-194">Pause the mouse over the shaded bar in the row for `Region`.</span></span>  
  
     <span data-ttu-id="95deb-195">這個值為 Pacific 的機率很高。</span><span class="sxs-lookup"><span data-stu-id="95deb-195">The probability of the value being Pacific is very high.</span></span> <span data-ttu-id="95deb-196">如需如何解讀這些值的詳細資訊，請參閱[Microsoft 時序群集演算法技術參考](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="95deb-196">For more information about how to interpret these values, see [Microsoft Sequence Clustering Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm-technical-reference.md).</span></span>  
  
3.  <span data-ttu-id="95deb-197">查看群集的特性清單，直到您找到第一個轉換資料列為止。</span><span class="sxs-lookup"><span data-stu-id="95deb-197">Look through the list of characteristics for the cluster until you find the first transition row.</span></span>  
  
4.  <span data-ttu-id="95deb-198">轉換資料列包含 [**變數**] 資料行中的文字轉換，以及 [**值**] 欄位中的一些連續屬性值組合。</span><span class="sxs-lookup"><span data-stu-id="95deb-198">A transition row contains the text Transition in the **Variables** column, and some combination of sequential attribute values in the **Value** column.</span></span> <span data-ttu-id="95deb-199">此序列也可包含起點和遺漏的值。</span><span class="sxs-lookup"><span data-stu-id="95deb-199">The sequence can also contain starting points and missing values.</span></span>  
  
     <span data-ttu-id="95deb-200">例如，假設轉換的值是 [Start]-> 的道路輪胎管。</span><span class="sxs-lookup"><span data-stu-id="95deb-200">For example, suppose the transition has the value, [Start] -> Road Tire Tube.</span></span> <span data-ttu-id="95deb-201">這表示此群集中的客戶經常會將 Road Tire Tube 先放在他們的購物籃中。</span><span class="sxs-lookup"><span data-stu-id="95deb-201">This means that customers in this cluster frequently put the Road Tire Tube in their shopping basket first.</span></span> <span data-ttu-id="95deb-202">這可能表示，此產品是客戶會先尋找的熱賣商品，或者可能只表示，此產品很容易在購買網站上找到。</span><span class="sxs-lookup"><span data-stu-id="95deb-202">This might signify that the product is a popular item that customers seek out first, or it might only indicate that the product is easy to find on the purchasing site.</span></span>  
  
5.  <span data-ttu-id="95deb-203">在清單中滾動，直到您找到沒有 **[Start]** 或其中**遺漏**的第一個轉換為止。</span><span class="sxs-lookup"><span data-stu-id="95deb-203">Scroll through the list until you find the first transition that does not have **[Start]** or **missing** in it.</span></span>  
  
     <span data-ttu-id="95deb-204">例如，假設您發現轉換、**旅行輪胎、旅行輪胎管**。</span><span class="sxs-lookup"><span data-stu-id="95deb-204">For example, suppose you find the transition, **Touring Tire, Touring Tire Tube**.</span></span> <span data-ttu-id="95deb-205">這表示此群集中的客戶經常一起購買這些項目 (與這個順序完全相同)。</span><span class="sxs-lookup"><span data-stu-id="95deb-205">This means that customers in this cluster frequently purchased these items together, in exactly this order.</span></span>  
  
6.  <span data-ttu-id="95deb-206">將滑鼠暫時放在這個轉換的陰影長條上方。</span><span class="sxs-lookup"><span data-stu-id="95deb-206">Pause the mouse over the shaded bar for this transition.</span></span>  
  
     <span data-ttu-id="95deb-207">這個轉換的機率會顯示成百分比。</span><span class="sxs-lookup"><span data-stu-id="95deb-207">The probability of this transition is displayed as a percentage.</span></span>  
  
7.  <span data-ttu-id="95deb-208">**在 [叢集**] 下拉式清單中，選取 [擴展] ([\*\*所有) \*\*]。</span><span class="sxs-lookup"><span data-stu-id="95deb-208">In the **Cluster** dropdown list, select **Population (All)**.</span></span>  
  
     <span data-ttu-id="95deb-209">屬性的清單會更新，以顯示用來建立模型之所有訂單的特性。</span><span class="sxs-lookup"><span data-stu-id="95deb-209">The list of attributes updates to show the characteristics of all orders used to create the model.</span></span> <span data-ttu-id="95deb-210">在此採礦模型中，區分叢集的最重要特性是 `Region` ，其值為**北美洲**。</span><span class="sxs-lookup"><span data-stu-id="95deb-210">In this mining model, the most important characteristic for distinguishing between clusters is `Region`, with a value of **North America**.</span></span>  
  
 <span data-ttu-id="95deb-211">檢閱這些工作以後，您得知兩件事。</span><span class="sxs-lookup"><span data-stu-id="95deb-211">After reviewing these tasks, you realize two things.</span></span> <span data-ttu-id="95deb-212">第一件就是您需要很多的資料，才能取得有意義的組合數目。</span><span class="sxs-lookup"><span data-stu-id="95deb-212">The first is that you need a lot of data to obtain a meaningful number of combinations.</span></span> <span data-ttu-id="95deb-213">例如，具有最高機率的序列可能會包含 **[開始] 或 [** **遺失**] 狀態。</span><span class="sxs-lookup"><span data-stu-id="95deb-213">For example, the sequences with the highest probabilities are likely to include a **[Start]** or **Missing** state.</span></span>  
  
 <span data-ttu-id="95deb-214">第二種方式是對的屬性有強式叢集效果 `Region` ，這會讓您更難以查看序列的群組。</span><span class="sxs-lookup"><span data-stu-id="95deb-214">The second is that there is a strong clustering effect on attributes for `Region`, which makes it more difficult to see the groups of sequences.</span></span> <span data-ttu-id="95deb-215">因此，您決定建立另一個只使用序列的模型，而且不包括地區或收入資料行。</span><span class="sxs-lookup"><span data-stu-id="95deb-215">Therefore, you decide to create another model that uses sequences only, and does not include the columns for region or income.</span></span>  
  
 [<span data-ttu-id="95deb-216">回到頁首</span><span class="sxs-lookup"><span data-stu-id="95deb-216">Back to Top</span></span>](#bkmk_CDiagram)  
  
##  <a name="cluster-discrimination-tab"></a><a name="bkmk_CDiscrim2"></a><span data-ttu-id="95deb-217">群集辨識索引標籤</span><span class="sxs-lookup"><span data-stu-id="95deb-217">Cluster Discrimination Tab</span></span>  
 <span data-ttu-id="95deb-218">[**叢集**辨識] 索引標籤可協助您比較兩個叢集，以判斷哪些屬性會區分特定叢集與另一個叢集。</span><span class="sxs-lookup"><span data-stu-id="95deb-218">The **Cluster Discrimination** tab helps you compare two clusters, to determine which attributes distinguish a particular cluster from another cluster.</span></span> <span data-ttu-id="95deb-219">此索引標籤包含四個**資料**行：**變數**、值、 **cluster 1**和**cluster 2**。</span><span class="sxs-lookup"><span data-stu-id="95deb-219">The tab contains four columns: **Variables**, **Values**, **Cluster 1**, and **Cluster 2**.</span></span>  <span data-ttu-id="95deb-220">您可以選擇任何叢集作為 [叢集**1** ] 和 [叢集**2**] 使用。</span><span class="sxs-lookup"><span data-stu-id="95deb-220">You can choose any cluster to use as **Cluster 1** and **Cluster 2**.</span></span>  
  
 <span data-ttu-id="95deb-221">[**變數**] 資料行會告訴您屬性的名稱，這可以是資料行名稱或資料行名稱和**轉換**文字的組合。</span><span class="sxs-lookup"><span data-stu-id="95deb-221">The **Variables** column tells you the name of the attribute, which can either be a column name or combination of column name and the word **transition**.</span></span> <span data-ttu-id="95deb-222">[**值] 資料**行會顯示內容或轉換的確切值。</span><span class="sxs-lookup"><span data-stu-id="95deb-222">The **Values** column shows the exact value of the attribute or the transition.</span></span> <span data-ttu-id="95deb-223">[叢集**1** ] 和 [叢集**2** ] 之資料行中的陰影橫條指出您要比較的群集中屬性的強度。</span><span class="sxs-lookup"><span data-stu-id="95deb-223">The shaded bars in the columns for **Cluster 1** and **Cluster 2** indicate the strength of the attribute in the clusters that you are comparing.</span></span> <span data-ttu-id="95deb-224">長條越長，就表示此群集包含具有該屬性之案例的可能性越高。</span><span class="sxs-lookup"><span data-stu-id="95deb-224">The longer the bar, the more the cluster is likely to include cases with that attribute.</span></span>  
  
#### <a name="to-compare-two-clusters-by-using-the-cluster-discrimination-tab"></a><span data-ttu-id="95deb-225">若要使用群集辨識索引標籤來比較兩個群集</span><span class="sxs-lookup"><span data-stu-id="95deb-225">To compare two clusters by using the Cluster Discrimination tab</span></span>  
  
1.  <span data-ttu-id="95deb-226">在 [**群集**辨識] 索引標籤中，針對 [叢集**1**] 選取 `Pacific Cluster` 。</span><span class="sxs-lookup"><span data-stu-id="95deb-226">In the **Cluster Discrimination** tab, for **Cluster 1**, select `Pacific Cluster`.</span></span>  
  
     <span data-ttu-id="95deb-227">根據預設，[叢集**2** ] 的選取專案會變更為 [**太平洋叢集補數**]。</span><span class="sxs-lookup"><span data-stu-id="95deb-227">By default, the selection for **Cluster 2** changes to **Complement of Pacific Cluster**.</span></span>  
  
     <span data-ttu-id="95deb-228">與所有其他案例區別的最上層屬性 `Pacific Cluster` 是區域。</span><span class="sxs-lookup"><span data-stu-id="95deb-228">The top attribute that distinguishes `Pacific Cluster` from all other cases is the region.</span></span> <span data-ttu-id="95deb-229">地區是一個很強的群集屬性，它會讓其他屬性相形失色。</span><span class="sxs-lookup"><span data-stu-id="95deb-229">Region is such a strong attribute for clustering that it obscures other attributes.</span></span> <span data-ttu-id="95deb-230">為了避免這樣的影響，請嘗試互相比較幾個較小的群集。</span><span class="sxs-lookup"><span data-stu-id="95deb-230">To avoid this effect, try comparing several of the smaller clusters to each other.</span></span> <span data-ttu-id="95deb-231">當您這樣做時，屬性的清單會變更，而且可能包括模型之間的更多轉換。</span><span class="sxs-lookup"><span data-stu-id="95deb-231">When you do so, the list of attributes changes and might include more transitions between models.</span></span>  
  
2.  <span data-ttu-id="95deb-232">找出轉換資料列，然後將滑鼠暫時放在陰影長條上方。</span><span class="sxs-lookup"><span data-stu-id="95deb-232">Locate a transition row, and pause the mouse over the shaded bar.</span></span>  
  
     <span data-ttu-id="95deb-233">[**值] 資料**行中的專案可以同時包含狀態和轉換。</span><span class="sxs-lookup"><span data-stu-id="95deb-233">The items in the **Values** column can include both states and transitions.</span></span> <span data-ttu-id="95deb-234">每個項目的陰影代表辨識率。</span><span class="sxs-lookup"><span data-stu-id="95deb-234">The shading for each item indicates the discrimination score.</span></span> <span data-ttu-id="95deb-235">若要深入瞭解不同分數的意義，請參閱時序叢集[模型 &#40;Analysis Services 資料採礦&#41;的採礦模型內容](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)。</span><span class="sxs-lookup"><span data-stu-id="95deb-235">To learn more about the meaning of different scores, see [Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md).</span></span>  
  
 [<span data-ttu-id="95deb-236">回到頁首</span><span class="sxs-lookup"><span data-stu-id="95deb-236">Back to Top</span></span>](#bkmk_CDiagram)  
  
##  <a name="state-transitions-tab"></a><a name="bkmk_StateTran"></a><span data-ttu-id="95deb-237">狀態轉換索引標籤</span><span class="sxs-lookup"><span data-stu-id="95deb-237">State Transitions Tab</span></span>  
 <span data-ttu-id="95deb-238">在 [**狀態轉換**] 索引標籤上，您可以選取叢集並流覽其狀態轉換。</span><span class="sxs-lookup"><span data-stu-id="95deb-238">On the **State Transitions** tab, you can select a cluster and browse through its state transitions.</span></span> <span data-ttu-id="95deb-239">如果您從 [叢集] 下拉式清單中選取 [擴展] \*\* ([所有) \*\* ]，則圖表會顯示整個採礦模型的狀態分佈。</span><span class="sxs-lookup"><span data-stu-id="95deb-239">If you select **Population (All)** from the cluster drop-down list, the diagram shows the distribution of states for the whole mining model.</span></span>  
  
 <span data-ttu-id="95deb-240">圖表中的每個節點都代表一種狀態，或是您嘗試分析之序列的可能值。</span><span class="sxs-lookup"><span data-stu-id="95deb-240">Each node in the graph represents a state, or possible value, of the sequences that you are trying to analyze.</span></span> <span data-ttu-id="95deb-241">節點的背景色彩代表該狀態的頻率。</span><span class="sxs-lookup"><span data-stu-id="95deb-241">The background color of the nodes represents the frequency of that state.</span></span> <span data-ttu-id="95deb-242">線條會連接某些狀態，這表示狀態之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="95deb-242">Lines connect some states, indicating a transition between states.</span></span> <span data-ttu-id="95deb-243">您可以將滑動軸上移或下移來變更轉換的機率臨界值。</span><span class="sxs-lookup"><span data-stu-id="95deb-243">You can move the slider up or down to change the probability threshold for the transitions.</span></span> <span data-ttu-id="95deb-244">數字與某些節點有關，這表示該狀態的機率。</span><span class="sxs-lookup"><span data-stu-id="95deb-244">Numbers are associated with some nodes, indicating the probability of that state.</span></span>  
  
#### <a name="to-explore-the-relationships-in-the-state-transition-tab"></a><span data-ttu-id="95deb-245">若要在狀態轉換索引標籤中探索關聯性</span><span class="sxs-lookup"><span data-stu-id="95deb-245">To explore the relationships in the State Transition tab</span></span>  
  
1.  <span data-ttu-id="95deb-246">在 [採礦模型檢視器] 的 [**狀態轉換**] 索引標籤中， `Pacific Cluster` 從群集清單中選取。</span><span class="sxs-lookup"><span data-stu-id="95deb-246">In the **State Transitions** tab of the Mining Model viewer, select `Pacific Cluster` from the list of clusters.</span></span> <span data-ttu-id="95deb-247">確定已選取 [**顯示邊緣標籤**] 選項。</span><span class="sxs-lookup"><span data-stu-id="95deb-247">Ensure that the **Show Edge Labels** option is selected.</span></span>  
  
     <span data-ttu-id="95deb-248">此圖表會更新，以顯示該群集中最常用的轉換。</span><span class="sxs-lookup"><span data-stu-id="95deb-248">The graph updates to show the transitions that are most common in this cluster.</span></span>  
  
2.  <span data-ttu-id="95deb-249">按一下透過一條線與另一個節點連接的任何節點。</span><span class="sxs-lookup"><span data-stu-id="95deb-249">Click any node that is connected by a line to another node.</span></span>  
  
     <span data-ttu-id="95deb-250">此圖表會更新，並反白顯示相關的節點。</span><span class="sxs-lookup"><span data-stu-id="95deb-250">The graph is updated and highlights the related nodes.</span></span> <span data-ttu-id="95deb-251">此線條旁邊的數值表示轉換的機率。</span><span class="sxs-lookup"><span data-stu-id="95deb-251">The numeric value next to the line indicates the probability of the transition.</span></span>  
  
3.  <span data-ttu-id="95deb-252">將滑杆向上提升至**所有連結**，以增加圖表中包含的轉換數目。</span><span class="sxs-lookup"><span data-stu-id="95deb-252">Raise the slider up to **All Links**, to increase the number of transitions included in the graph.</span></span>  
  
4.  <span data-ttu-id="95deb-253">選取 [擴展] (叢集\*\*的\*\*\*\*所有) \*\* 。</span><span class="sxs-lookup"><span data-stu-id="95deb-253">Select **Population (All)** from **Cluster**.</span></span>  
  
     <span data-ttu-id="95deb-254">請注意，當您載入不同群集時，此圖表會重設為預設顯示設定，好讓滑動軸控制項重設為中間位置。</span><span class="sxs-lookup"><span data-stu-id="95deb-254">Note that when you load a different cluster, the graph resets to the default display settings, so the slider control is reset to the middle position.</span></span>  
  
5.  <span data-ttu-id="95deb-255">按一下圖形中最暗的節點，其應為 [**運動-100**]。</span><span class="sxs-lookup"><span data-stu-id="95deb-255">Click the darkest node in the graph, which should be **Sport-100**.</span></span>  
  
     <span data-ttu-id="95deb-256">請注意，沒有任何線條可將這個產品連接其他產品。</span><span class="sxs-lookup"><span data-stu-id="95deb-256">Note that there are no lines connecting this product to other products.</span></span>  
  
6.  <span data-ttu-id="95deb-257">將滑動軸上移一個步驟，以增加圖表中包含的轉換數。</span><span class="sxs-lookup"><span data-stu-id="95deb-257">Raise the slider up one step, to increase the number of transitions included in the graph.</span></span> <span data-ttu-id="95deb-258">**所有連結**都尚未移至。</span><span class="sxs-lookup"><span data-stu-id="95deb-258">Do not go all the way to **All Links** yet.</span></span>  
  
     <span data-ttu-id="95deb-259">此圖表會更新，其方式是在圖表中加入其他幾個轉換，但是不能有包含 Sport-100 模型的轉換。</span><span class="sxs-lookup"><span data-stu-id="95deb-259">The graph is updated by adding several more transitions to the graph, but none that include the Sport-100 model.</span></span>  
  
7.  <span data-ttu-id="95deb-260">將滑杆控制項移至 [**所有連結**]。</span><span class="sxs-lookup"><span data-stu-id="95deb-260">Move the slider control all the way to **All Links**.</span></span> <span data-ttu-id="95deb-261">按一下 [Sport-100] 節點 (若尚未選取)。</span><span class="sxs-lookup"><span data-stu-id="95deb-261">Click the Sport-100 node if it is not already selected.</span></span>  
  
     <span data-ttu-id="95deb-262">此圖表會更新，以顯示許多包含 Sport-100 產品的轉換。</span><span class="sxs-lookup"><span data-stu-id="95deb-262">The graph updates to show many transitions that include the Sport-100 product.</span></span> <span data-ttu-id="95deb-263">連接線上箭頭的方向告訴您，Sport-100 項目選為此配對中的第一個項目還是第二個項目。</span><span class="sxs-lookup"><span data-stu-id="95deb-263">The direction of the arrow on the connecting line tells you whether the Sport-100 item was selected as the first item or the second item in the pair.</span></span>  
  
8.  <span data-ttu-id="95deb-264">按一下 Touring Tire 的節點，並將滑動軸控制項往下移回中間位置。</span><span class="sxs-lookup"><span data-stu-id="95deb-264">Clicking the node for Touring Tire and move the slider control back down to the middle position.</span></span>  
  
     <span data-ttu-id="95deb-265">一開始，有許多轉換線路會將旅行輪胎連接到其他產品，但當您提高機率臨界值時，從圖形中去除較不可能的轉換，只留下轉換，旅行輪胎 > 旅行輪胎管。</span><span class="sxs-lookup"><span data-stu-id="95deb-265">At first, there are many transition lines connecting Touring Tire to other products, but when you raise the probability threshold, the less likely transitions are eliminated from the graph, leaving just the transition, Touring Tire > Touring Tire Tube.</span></span> <span data-ttu-id="95deb-266">這個轉換表示，如果某位客戶將 Touring Tire 放入購物籃，則該客戶接著將 Touring Tire Tube 也放入購物籃的機率很高。</span><span class="sxs-lookup"><span data-stu-id="95deb-266">This transition means that if a customer puts a Touring Tire into the shopping basket, there is a strong probability that the customer will next put a Touring Tire Tube into the basket.</span></span>  
  
 [<span data-ttu-id="95deb-267">回到頁首</span><span class="sxs-lookup"><span data-stu-id="95deb-267">Back to Top</span></span>](#bkmk_CDiagram)  
  
##  <a name="generic-content-tree-viewer"></a><a name="bkmk_Generic"></a><span data-ttu-id="95deb-268">一般內容樹狀檢視器</span><span class="sxs-lookup"><span data-stu-id="95deb-268">Generic Content Tree Viewer</span></span>  
 <span data-ttu-id="95deb-269">此檢視器可用於所有模型，不論演算法或模型類型為何。</span><span class="sxs-lookup"><span data-stu-id="95deb-269">This viewer can be used for all models, regardless of the algorithm or model type.</span></span> <span data-ttu-id="95deb-270">[ **MicrosoftGeneric 內容樹狀檢視器]** 可從 [**檢視器]** 下拉式清單中取得。</span><span class="sxs-lookup"><span data-stu-id="95deb-270">The **MicrosoftGeneric Content Tree Viewer** is available from the **Viewer** drop-down list.</span></span>  
  
 <span data-ttu-id="95deb-271">內容樹狀結構會將任何採礦模型表示為一系列的節點，其中的每一個節點都表示所學習到有關定型資料的知識。</span><span class="sxs-lookup"><span data-stu-id="95deb-271">A content tree is a representation of any mining model as a series of nodes, wherein each node represents learned knowledge about the training data.</span></span> <span data-ttu-id="95deb-272">節點可以包含模式、一組規則、群集，或是共用某些屬性之日期範圍的定義。</span><span class="sxs-lookup"><span data-stu-id="95deb-272">The node can contain a pattern, a set of rules, a cluster, or the definition of a range of dates that share some attributes.</span></span> <span data-ttu-id="95deb-273">節點的確切內容會因為演算法和可預測屬性而有所不同，但是內容的一般表示都是相同的。</span><span class="sxs-lookup"><span data-stu-id="95deb-273">The exact content of the node differs depending on the algorithm and the predictable attribute, but the general representation of the content is the same.</span></span>  
  
 <span data-ttu-id="95deb-274">您可以展開每一個節點，以查看詳細資料的遞增層級，並將任何節點的內容複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="95deb-274">You can expand each node to see increasing levels of detail, and copy the content of any node to the Clipboard.</span></span> <span data-ttu-id="95deb-275">如需詳細資訊，請參閱 [使用 Microsoft 一般內容樹狀檢視器瀏覽模型](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="95deb-275">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span></span>  
  
#### <a name="to-view-details-for-a-sequence-clustering-model-by-using-the-generic-content-tree-viewer"></a><span data-ttu-id="95deb-276">若要使用一般內容樹狀檢視器檢視時序群集模型的詳細資料</span><span class="sxs-lookup"><span data-stu-id="95deb-276">To view details for a sequence clustering model by using the Generic Content Tree Viewer</span></span>  
  
1.  <span data-ttu-id="95deb-277">在 [**採礦模型檢視器**] 索引標籤中按一下 [**檢視器**] 清單，然後選取 [ **Microsoft 一般內容樹狀檢視器]**。</span><span class="sxs-lookup"><span data-stu-id="95deb-277">In the **Mining Model Viewer** tab, click the **Viewer** list, and select **Microsoft Generic Content Tree viewer**.</span></span>  
  
2.  <span data-ttu-id="95deb-278">在 [**節點標題**] 窗格中，按一下 [] `Pacific Cluster (1)` 。</span><span class="sxs-lookup"><span data-stu-id="95deb-278">In the **Node Caption** pane, click `Pacific Cluster (1)`.</span></span>  
  
     <span data-ttu-id="95deb-279">這個節點的名稱同時包含您指派給群集的易記名稱和基礎節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="95deb-279">The name for this node contains both the friendly name that you assigned to the cluster and the underlying node ID.</span></span> <span data-ttu-id="95deb-280">您可以使用節點識別碼，向下鑽研到模型內的其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="95deb-280">You can use the node IDs to drill down into additional detail in the model.</span></span>  
  
3.  <span data-ttu-id="95deb-281">展開第一個子節點，名為 [叢集**1 的順序層級**]。</span><span class="sxs-lookup"><span data-stu-id="95deb-281">Expand the first child node, named **Sequence level for cluster 1**.</span></span>  
  
     <span data-ttu-id="95deb-282">群集的時序層級節點包含有關該群集內包含之狀態和轉換的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="95deb-282">The sequence level node for a cluster contains details about the states and transitions that are included in that cluster.</span></span> <span data-ttu-id="95deb-283">您可以使用 NODE_DISTRIBUTION 資料行中提供的這些詳細資料，以整體方式探索每一個群集或模型的時序和狀態。</span><span class="sxs-lookup"><span data-stu-id="95deb-283">You can use these details, available in the NODE_DISTRIBUTION column, to explore the sequences and the states for each cluster or for the model as a while.</span></span>  
  
4.  <span data-ttu-id="95deb-284">繼續展開節點，並在 HTML 檢視器窗格中檢視詳細資料。</span><span class="sxs-lookup"><span data-stu-id="95deb-284">Continue to expand nodes and view the details in the HTML viewer pane.</span></span>  
  
 <span data-ttu-id="95deb-285">如需有關採礦模型內容的詳細資訊，以及如何使用檢視器中的詳細資料，請參閱時序叢集[模型 &#40;Analysis Services 資料採礦&#41;的模型內容](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)。</span><span class="sxs-lookup"><span data-stu-id="95deb-285">For more information about the mining model content, and how to use the details in the viewer, see [Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md).</span></span>  
  
 [<span data-ttu-id="95deb-286">回到頁首</span><span class="sxs-lookup"><span data-stu-id="95deb-286">Back to Top</span></span>](#bkmk_CDiagram)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="95deb-287">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="95deb-287">Next Task in Lesson</span></span>  
 [<span data-ttu-id="95deb-288">建立相關的時序群集模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="95deb-288">Creating a Related Sequence Clustering Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="95deb-289">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95deb-289">See Also</span></span>  
 <span data-ttu-id="95deb-290">[Microsoft 時序群集演算法](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="95deb-290">[Microsoft Sequence Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md) </span></span>  
 [<span data-ttu-id="95deb-291">時序叢集模型查詢範例</span><span class="sxs-lookup"><span data-stu-id="95deb-291">Sequence Clustering Model Query Examples</span></span>](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md)  
  
  
