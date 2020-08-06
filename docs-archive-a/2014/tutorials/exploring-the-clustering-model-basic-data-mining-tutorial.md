---
title: 探索群集模型 (基本資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ce8aa034-161b-473f-baec-9c29e0a8e5f5
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: cca9d395fece59f607c8faf209128b9d32663a06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710081"
---
# <a name="exploring-the-clustering-model-basic-data-mining-tutorial"></a><span data-ttu-id="f459b-102">瀏覽群集模型 (基本資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="f459b-102">Exploring the Clustering Model (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="f459b-103">[!INCLUDE[msCoName](../includes/msconame-md.md)]群集演算法會將案例分組至包含類似特性的群集。</span><span class="sxs-lookup"><span data-stu-id="f459b-103">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm groups cases into clusters that contain similar characteristics.</span></span> <span data-ttu-id="f459b-104">這些群集對於瀏覽資料、識別資料的異常及建立預測很有幫助。</span><span class="sxs-lookup"><span data-stu-id="f459b-104">These groupings are useful for exploring data, identifying anomalies in the data, and creating predictions.</span></span>  
  
 <span data-ttu-id="f459b-105">[!INCLUDE[msCoName](../includes/msconame-md.md)] 叢集檢視器會提供下列索引標籤，用來瀏覽叢集採礦模型：</span><span class="sxs-lookup"><span data-stu-id="f459b-105">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Cluster Viewer provides the following tabs for use in exploring clustering mining models:</span></span>  
  

  
##  <a name="cluster-diagram-tab"></a><a name="ClusterDiagramTab"></a><span data-ttu-id="f459b-106">[群集圖表] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="f459b-106">Cluster Diagram Tab</span></span>  
 <span data-ttu-id="f459b-107">[群集圖表] 索引標籤會顯示採礦模型中的所有群集。</span><span class="sxs-lookup"><span data-stu-id="f459b-107">The Cluster Diagram tab displays all the clusters that are in a mining model.</span></span> <span data-ttu-id="f459b-108">群集之間的線代表「相似程度」，並根據群集的相似程度加上陰影。</span><span class="sxs-lookup"><span data-stu-id="f459b-108">The lines between the clusters represent "closeness" and are shaded based on how similar the clusters are.</span></span> <span data-ttu-id="f459b-109">每一個群集的實際色彩各代表變數的頻率和群集中的狀態。</span><span class="sxs-lookup"><span data-stu-id="f459b-109">The actual color of each cluster represents the frequency of the variable and the state in the cluster.</span></span>  
  
#### <a name="to-explore-the-model-in-the-cluster-diagram-tab"></a><span data-ttu-id="f459b-110">若要在群集圖表索引標籤中瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="f459b-110">To explore the model in the Cluster Diagram tab</span></span>  
  
1.  <span data-ttu-id="f459b-111">使用 [**採礦模型檢視器**] 索引標籤頂端的 [**採礦模型**] 清單，切換到 `TM_Clustering` 模型。</span><span class="sxs-lookup"><span data-stu-id="f459b-111">Use the **Mining Model** list at the top of the **Mining Model Viewer** tab to switch to the `TM_Clustering` model.</span></span>  
  
2.  <span data-ttu-id="f459b-112">在 [**檢視器]** 清單中，選取 [ **Microsoft 叢集檢視器]**。</span><span class="sxs-lookup"><span data-stu-id="f459b-112">In the **Viewer** list, select **Microsoft Cluster Viewer**.</span></span>  
  
3.  <span data-ttu-id="f459b-113">在 [**陰影變數**] 方塊中，選取 [**自行車買方**]。</span><span class="sxs-lookup"><span data-stu-id="f459b-113">In the **Shading Variable** box, select **Bike Buyer**.</span></span>  
  
     <span data-ttu-id="f459b-114">預設變數是 [擴展]，但您可以將其變更為模型中的任何**屬性，以**探索哪些叢集包含擁有您想要之屬性的成員。</span><span class="sxs-lookup"><span data-stu-id="f459b-114">The default variable is **Population**, but you can change this to any attribute in the model, to discover which clusters contain members that have the attributes you want.</span></span>  
  
4.  <span data-ttu-id="f459b-115">在 [**狀態**] 方塊中選取**1** ，以探索已購買自行車的案例。</span><span class="sxs-lookup"><span data-stu-id="f459b-115">Select **1** in the **State** box to explore those cases where a bike was purchased.</span></span>  
  
     <span data-ttu-id="f459b-116">**密度**圖例會描述在陰影變數和狀態中所選取之屬性狀態配對的密度。</span><span class="sxs-lookup"><span data-stu-id="f459b-116">The **Density** legend describes the density of the attribute state pair selected in the Shading Variable and the State.</span></span> <span data-ttu-id="f459b-117">在此範例中，它會告訴我們，clusterwith 最深的陰影具有自行車購買者的最高百分比。</span><span class="sxs-lookup"><span data-stu-id="f459b-117">In this example it tells us that the clusterwith the darkest shading has the highest percentage of bike buyers.</span></span>  
  
5.  <span data-ttu-id="f459b-118">將滑鼠暫停在最深陰影的群集上方。</span><span class="sxs-lookup"><span data-stu-id="f459b-118">Pause your mouse over the cluster with the darkest shading.</span></span>  
  
     <span data-ttu-id="f459b-119">工具提示會顯示具有 `Bike Buyer = 1` 屬性的案例百分比。</span><span class="sxs-lookup"><span data-stu-id="f459b-119">A tooltip displays the percentage of cases that have the attribute, `Bike Buyer = 1`.</span></span>  
  
6.  <span data-ttu-id="f459b-120">選取最高密度的叢集，在叢集上按一下滑鼠右鍵，選取 [**重新命名**叢集]，然後輸入**自行車購買**者，以供日後辨識。</span><span class="sxs-lookup"><span data-stu-id="f459b-120">Select the cluster that has the highest density, right-click the cluster, select **Rename Cluster** and type **Bike Buyers High** for later identification.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="f459b-121">尋找具有最淺陰影 (和最低密度) 的群集。</span><span class="sxs-lookup"><span data-stu-id="f459b-121">Find the cluster that has the lightest shading (and the lowest density).</span></span> <span data-ttu-id="f459b-122">在叢集上按一下滑鼠右鍵，選取 [**重新命名**叢集]，然後輸入**自行車買家 Low**。</span><span class="sxs-lookup"><span data-stu-id="f459b-122">Right-click the cluster, select **Rename Cluster** and type **Bike Buyers Low**.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="f459b-123">按一下 [**自行車購買**者] 高叢集，並將它拖曳到窗格的某個區域，讓您清楚瞭解其與其他叢集的連接。</span><span class="sxs-lookup"><span data-stu-id="f459b-123">Click the **Bike Buyers High** cluster and drag it to an area of the pane that will give you a clear view of its connections to the other clusters.</span></span>  
  
     <span data-ttu-id="f459b-124">當您選取群集時，將此群集連接至其他群集的線條會反白顯示，如此您就可以輕鬆看見這個群集的所有關聯性。</span><span class="sxs-lookup"><span data-stu-id="f459b-124">When you select a cluster, the lines that connect this cluster to other clusters are highlighted, so that you can easily see all the relationships for this cluster.</span></span> <span data-ttu-id="f459b-125">當未選取此群集時，您可以透過線條的明暗度來區分圖表中所有群集之間關聯性的強烈程度。</span><span class="sxs-lookup"><span data-stu-id="f459b-125">When the cluster is not selected, you can tell by the darkness of the lines how strong the relationships are amongst all the clusters in the diagram.</span></span> <span data-ttu-id="f459b-126">如果陰影很淡或不存在，則表示群集不太相似。</span><span class="sxs-lookup"><span data-stu-id="f459b-126">If the shading is light or nonexistent, the clusters are not very similar.</span></span>  
  
9. <span data-ttu-id="f459b-127">利用網路左側的滑動軸，可以篩選掉較弱的連結，並找出關聯性最近的群集。</span><span class="sxs-lookup"><span data-stu-id="f459b-127">Use the slider to the left of the network, to filter out the weaker links and find the clusters with the closest relationships.</span></span> <span data-ttu-id="f459b-128">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 行銷部門在判斷傳遞目標郵件的最佳方法時，可能會想要將類似的群集結合在一起。</span><span class="sxs-lookup"><span data-stu-id="f459b-128">The [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] marketing department might want to combine similar clusters together when determining the best method for delivering the targeted mailing.</span></span>  
  

  
##  <a name="cluster-profiles-tab"></a><a name="ClusterProfilesTab"></a><span data-ttu-id="f459b-129">群集設定檔索引標籤</span><span class="sxs-lookup"><span data-stu-id="f459b-129">Cluster Profiles Tab</span></span>  
 <span data-ttu-id="f459b-130">[**群集設定檔**] 索引標籤會提供模型的整體觀點 `TM_Clustering` 。</span><span class="sxs-lookup"><span data-stu-id="f459b-130">The **Cluster Profiles** tab provides an overall view of the `TM_Clustering` model.</span></span> <span data-ttu-id="f459b-131">[**群集設定檔**] 索引標籤包含模型中每個叢集的資料行。</span><span class="sxs-lookup"><span data-stu-id="f459b-131">The **Cluster Profiles** tab contains a column for each cluster in the model.</span></span> <span data-ttu-id="f459b-132">第一個資料行列出至少與一個群集相關聯的變數。</span><span class="sxs-lookup"><span data-stu-id="f459b-132">The first column lists the attributes that are associated with at least one cluster.</span></span> <span data-ttu-id="f459b-133">檢視器的其餘部份含有每一個群集的變數，其狀態的分佈情形。</span><span class="sxs-lookup"><span data-stu-id="f459b-133">The rest of the viewer contains the distribution of the states of an attribute for each cluster.</span></span> <span data-ttu-id="f459b-134">離散變數的分佈會顯示為彩色列，其中包含**長條圖**列清單中所顯示的最大橫條數。</span><span class="sxs-lookup"><span data-stu-id="f459b-134">The distribution of a discrete variable is shown as a colored bar with the maximum number of bars displayed in the **Histogram bars** list.</span></span> <span data-ttu-id="f459b-135">連續變數是以鑽石圖顯示，代表在每一個群集中的平均與標準差。</span><span class="sxs-lookup"><span data-stu-id="f459b-135">Continuous attributes are displayed with a diamond chart, which represents the mean and standard deviation in each cluster.</span></span>  
  
#### <a name="to-explore-the-model-in-the-cluster-profiles-tab"></a><span data-ttu-id="f459b-136">若要在群集設定檔索引標籤中瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="f459b-136">To explore the model in the Cluster Profiles tab</span></span>  
  
1.  <span data-ttu-id="f459b-137">將**長條圖**列設定為**5**。</span><span class="sxs-lookup"><span data-stu-id="f459b-137">Set **Histogram** bars to **5**.</span></span>  
  
     <span data-ttu-id="f459b-138">在我們的模型中，5 是任何一個變數的最大狀態數。</span><span class="sxs-lookup"><span data-stu-id="f459b-138">In our model, 5 is the maximum number of states for any one variable.</span></span>  
  
2.  <span data-ttu-id="f459b-139">如果「**挖掘圖例**」封鎖**屬性設定檔**的顯示，請將它移出。</span><span class="sxs-lookup"><span data-stu-id="f459b-139">If the **Mining Legend** blocks the display of the **Attribute profiles**, move it out of the way.</span></span>  
  
3.  <span data-ttu-id="f459b-140">選取 [**自行車買家 High** ] 資料行，並將它拖曳至 **[擴展**] 資料行的右邊。</span><span class="sxs-lookup"><span data-stu-id="f459b-140">Select the **Bike Buyers High** column and drag it to the right of the **Population** column.</span></span>  
  
4.  <span data-ttu-id="f459b-141">選取 [**自行車購買者下限**] 資料行，並將它拖曳至 [**自行車買家 High** ] 資料行的右邊。</span><span class="sxs-lookup"><span data-stu-id="f459b-141">Select the **Bike Buyers Low** column and drag it to the right of the **Bike Buyers High** column.</span></span>  
  
5.  <span data-ttu-id="f459b-142">按一下 [**自行車買家 High** ] 資料行。</span><span class="sxs-lookup"><span data-stu-id="f459b-142">Click the **Bike Buyers High** column.</span></span>  
  
     <span data-ttu-id="f459b-143">[**變數**] 資料行會依該叢集的重要性順序排序。</span><span class="sxs-lookup"><span data-stu-id="f459b-143">The **Variables** column is sorted in order of importance for that cluster.</span></span> <span data-ttu-id="f459b-144">捲動資料行，並檢閱 Bike Buyer High 群集的特性。</span><span class="sxs-lookup"><span data-stu-id="f459b-144">Scroll through the column and review characteristics of the Bike Buyer High cluster.</span></span> <span data-ttu-id="f459b-145">例如，它們可能會有比較短的通勤距離。</span><span class="sxs-lookup"><span data-stu-id="f459b-145">For example, they are more likely to have a short commute.</span></span>  
  
6.  <span data-ttu-id="f459b-146">按兩下 [**自行車購買**者] [High] 資料行中的 [**年齡**] 資料格。</span><span class="sxs-lookup"><span data-stu-id="f459b-146">Double-click the **Age** cell in the **Bike Buyers High** column.</span></span>  
  
     <span data-ttu-id="f459b-147">[**挖掘圖例**] 會顯示更詳細的觀點，您可以看到這些客戶的年齡範圍以及平均年齡。</span><span class="sxs-lookup"><span data-stu-id="f459b-147">The **Mining Legend** displays a more detailed view and you can see the age range of these customers as well as the mean age.</span></span>  
  
7.  <span data-ttu-id="f459b-148">以滑鼠右鍵按一下 [**自行車購買者下限**] 資料行，然後選取 [**隱藏資料行**]。</span><span class="sxs-lookup"><span data-stu-id="f459b-148">Right-click the **Bike Buyers Low** column and select **Hide Column**.</span></span>  
  

  
##  <a name="cluster-characteristics-tab"></a><a name="ClusterCharacteristicsTab"></a><span data-ttu-id="f459b-149">群集特性索引標籤</span><span class="sxs-lookup"><span data-stu-id="f459b-149">Cluster Characteristics Tab</span></span>  
 <span data-ttu-id="f459b-150">使用 [叢集**特性**] 索引標籤，您可以更詳細地檢查組成叢集的特性。</span><span class="sxs-lookup"><span data-stu-id="f459b-150">With the **Cluster Characteristics** tab, you can examine in more detail the characteristics that make up a cluster.</span></span> <span data-ttu-id="f459b-151">您可以一次瀏覽一個群集，而不是比較所有群集的特性 (如同 [群集設定檔] 索引標籤上的處理方式)。</span><span class="sxs-lookup"><span data-stu-id="f459b-151">Instead of comparing the characteristics of all of the clusters (as in the Cluster Profiles tab), you can explore one cluster at a time.</span></span> <span data-ttu-id="f459b-152">例如，如果您**從 [叢集**] 清單中選取 [**自行車購買者高**]，就可以看到此叢集中客戶的特性。</span><span class="sxs-lookup"><span data-stu-id="f459b-152">For example, if you select **Bike Buyers High** from the **Cluster** list, you can see the characteristics of the customers in this cluster.</span></span> <span data-ttu-id="f459b-153">雖然這個顯示與 [群集設定檔] 檢視器不同，但是找到的結果是相同的。</span><span class="sxs-lookup"><span data-stu-id="f459b-153">Though the display is different from the Cluster Profiles viewer, the findings are the same.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f459b-154">除非您設定**holdoutseed**的初始值，否則每次處理模型時，結果會有所不同。</span><span class="sxs-lookup"><span data-stu-id="f459b-154">Unless you set an initial value for **holdoutseed**, results will vary each time you process the model.</span></span> <span data-ttu-id="f459b-155">如需詳細資訊，請參閱[HoldoutSeed 元素](https://docs.microsoft.com/bi-reference/assl/properties/holdoutseed-element)</span><span class="sxs-lookup"><span data-stu-id="f459b-155">For more information, see [HoldoutSeed Element](https://docs.microsoft.com/bi-reference/assl/properties/holdoutseed-element)</span></span>  
  

  
##  <a name="cluster-discrimination-tab"></a><a name="ClusterDiscriminationTab"></a><span data-ttu-id="f459b-156">群集辨識索引標籤</span><span class="sxs-lookup"><span data-stu-id="f459b-156">Cluster Discrimination Tab</span></span>  
 <span data-ttu-id="f459b-157">使用 [**叢集**辨識] 索引標籤，您可以探索區別另一個叢集的特性。</span><span class="sxs-lookup"><span data-stu-id="f459b-157">With the **Cluster Discrimination** tab, you can explore the characteristics that distinguish one cluster from another.</span></span> <span data-ttu-id="f459b-158">在您選取兩個叢集（一個來自 [叢集**1** ] 清單，另一個來自 [**群集 2** ] 清單）之後，檢視器會計算叢集之間的差異，並顯示最能區分叢集的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="f459b-158">After you select two clusters, one from the **Cluster 1** list, and one from the **Cluster 2** list, the viewer calculates the differences between the clusters and displays a list of the attributes that distinguish the clusters most.</span></span>  
  
#### <a name="to-explore-the-model-in-the-cluster-discrimination-tab"></a><span data-ttu-id="f459b-159">若要在群集辨識索引標籤中瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="f459b-159">To explore the model in the Cluster Discrimination tab</span></span>  
  
1.  <span data-ttu-id="f459b-160">在 [**群集 1** ] 方塊中，選取 [**自行車買家 High**]。</span><span class="sxs-lookup"><span data-stu-id="f459b-160">In the **Cluster 1** box, select **Bike Buyers High**.</span></span>  
  
2.  <span data-ttu-id="f459b-161">在 [**群集 2** ] 方塊中，選取 [**自行車買家 Low**]。</span><span class="sxs-lookup"><span data-stu-id="f459b-161">In the **Cluster 2** box, select **Bike Buyers Low**.</span></span>  
  
3.  <span data-ttu-id="f459b-162">按一下 [**變數**] 以字母順序排序。</span><span class="sxs-lookup"><span data-stu-id="f459b-162">Click **Variables** to sort alphabetically.</span></span>  
  
     <span data-ttu-id="f459b-163">**自行車購買**者的低與**自行車購買者高階**叢集的客戶之間，有一些較大的差異，包括年齡、汽車擁有權、子女數目和地區。</span><span class="sxs-lookup"><span data-stu-id="f459b-163">Some of the more substantial differences among the customers in the **Bike Buyers Low** and **Bike Buyers High** clusters include age, car ownership, number of children, and region.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="f459b-164">相關工作</span><span class="sxs-lookup"><span data-stu-id="f459b-164">Related Tasks</span></span>  
 <span data-ttu-id="f459b-165">請參閱下列主題，瀏覽其他採礦模型。</span><span class="sxs-lookup"><span data-stu-id="f459b-165">See the following topics to explore the other mining models.</span></span>  
  
-   [<span data-ttu-id="f459b-166">流覽決策樹模型 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="f459b-166">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="f459b-167">探索貝氏貝氏機率分類模型 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="f459b-167">Exploring the Naive Bayes Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="f459b-168">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="f459b-168">Next Task in Lesson</span></span>  
 [<span data-ttu-id="f459b-169">探索貝氏貝氏機率分類模型 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="f459b-169">Exploring the Naive Bayes Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="f459b-170">本課程的前一項工作</span><span class="sxs-lookup"><span data-stu-id="f459b-170">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="f459b-171">流覽決策樹模型 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="f459b-171">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="f459b-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f459b-172">See Also</span></span>  
 <span data-ttu-id="f459b-173">[使用 Microsoft 叢集檢視器流覽模型](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="f459b-173">[Browse a Model Using the Microsoft Cluster Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md) </span></span>  
 <span data-ttu-id="f459b-174">[&#40;採礦模型檢視器&#41;的 [叢集辨識] 索引標籤](../../2014/analysis-services/cluster-discrimination-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="f459b-174">[Cluster Discrimination Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/cluster-discrimination-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="f459b-175">[[叢集設定檔] 索引標籤 &#40;&#41;的採礦模型檢視器](../../2014/analysis-services/cluster-profiles-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="f459b-175">[Cluster Profiles Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/cluster-profiles-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="f459b-176">[[叢集特性] 索引標籤 &#40;[採礦模型檢視器]&#41;](../../2014/analysis-services/cluster-characteristics-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="f459b-176">[Cluster Characteristics Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/cluster-characteristics-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="f459b-177">[[叢集圖表] 索引標籤 &#40;[採礦模型檢視器]&#41;](../../2014/analysis-services/cluster-diagram-tab-mining-model-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="f459b-177">[Cluster Diagram Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/cluster-diagram-tab-mining-model-viewer.md)</span></span>  
  
  
