---
title: 流覽群集模型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- clustering [data mining]
- mining model, clustering
ms.assetid: 7f3f0949-d791-403a-88e2-54cb1a803dae
author: minewiskan
ms.author: owend
ms.openlocfilehash: f1d508603acd29fde981bddc5642b54ca9413f5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593133"
---
# <a name="browsing-a-clustering-model"></a><span data-ttu-id="ad783-102">瀏覽群集模型</span><span class="sxs-lookup"><span data-stu-id="ad783-102">Browsing a Clustering Model</span></span>
  <span data-ttu-id="ad783-103">當您使用 **[流覽]** 開啟群集模型時，該模型會顯示在互動式檢視器中，類似于中的群集檢視器 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ad783-103">When you open a clustering model using **Browse**, the model is displayed in an interactive viewer, similar to the clustering viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="ad783-104">此檢視器可協助您探索已建立的叢集，並且了解叢集特性。</span><span class="sxs-lookup"><span data-stu-id="ad783-104">The viewer helps you explore the clusters that were created, and understand cluster characteristics.</span></span> <span data-ttu-id="ad783-105">您也可以將個別的區段與其他區段或母體進行比較與對照。</span><span class="sxs-lookup"><span data-stu-id="ad783-105">You can also compare and contrast individual segments with other segments or with the population.</span></span>  
  
##  <a name="explore-the-model"></a><a name="BKMK_Tabs"></a><span data-ttu-id="ad783-106">探索模型</span><span class="sxs-lookup"><span data-stu-id="ad783-106">Explore the Model</span></span>  
 <span data-ttu-id="ad783-107">[**流覽**] 視窗包含下列工具，可協助您瞭解您的群集模型並探索基礎資料群組的屬性：</span><span class="sxs-lookup"><span data-stu-id="ad783-107">The **Browse** window includes the following tools to help you understand your clustering model and explore the attributes of the underlying data groups:</span></span>  
  
-   [<span data-ttu-id="ad783-108">群集圖表</span><span class="sxs-lookup"><span data-stu-id="ad783-108">Cluster Diagram</span></span>](#BKMK_ClusterDiagram)  
  
-   [<span data-ttu-id="ad783-109">叢集設定檔</span><span class="sxs-lookup"><span data-stu-id="ad783-109">Cluster Profiles</span></span>](#BKMK_ClusterProfiles)  
  
-   [<span data-ttu-id="ad783-110">叢集特性</span><span class="sxs-lookup"><span data-stu-id="ad783-110">Cluster Characteristics</span></span>](#BKMK_ClusterCharacteristics)  
  
-   [<span data-ttu-id="ad783-111">群集辨識</span><span class="sxs-lookup"><span data-stu-id="ad783-111">Cluster Discrimination</span></span>](#BKMK_ClusterDiscrimination)  
  
 <span data-ttu-id="ad783-112">若要試驗叢集模型，您可以使用範例資料活頁簿之 [定型] 索引標籤上的範例資料，然後使用 [叢集[Wizard] 建立群集模型 &#40;適用于 Excel 的資料採礦增益集&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)和所有預設值。</span><span class="sxs-lookup"><span data-stu-id="ad783-112">To experiment with a clustering model, you can use the sample data on the Training tab of the sample data workbook, and build a clustering model using [Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md) and all the defaults.</span></span>  
  
###  <a name="cluster-diagram"></a><a name="BKMK_ClusterDiagram"></a><span data-ttu-id="ad783-113">群集圖表</span><span class="sxs-lookup"><span data-stu-id="ad783-113">Cluster Diagram</span></span>  
 <span data-ttu-id="ad783-114">[**群集圖表**] 索引標籤會顯示所有位於「採礦模型」中的叢集。</span><span class="sxs-lookup"><span data-stu-id="ad783-114">The **Cluster Diagram** tab displays all the clusters that are in a mining model.</span></span> <span data-ttu-id="ad783-115">您可以在此查看資料集包含多少個不同的群組，以及每個群組彼此之間的遠近程度。</span><span class="sxs-lookup"><span data-stu-id="ad783-115">Here you can see how many different groupings were found in your data set, and how near or far they are from each other.</span></span>  
  
##### <a name="explore-the-cluster-diagram"></a><span data-ttu-id="ad783-116">探索叢集圖表</span><span class="sxs-lookup"><span data-stu-id="ad783-116">Explore the cluster diagram</span></span>  
  
1.  <span data-ttu-id="ad783-117">按一下圖表中的 [叢集 1]。</span><span class="sxs-lookup"><span data-stu-id="ad783-117">Click Cluster 1 in the diagram.</span></span>  
  
     <span data-ttu-id="ad783-118">請注意連接所有叢集的灰色線條如何變更，好讓連往選取叢集的線條以亮藍色反白顯示。</span><span class="sxs-lookup"><span data-stu-id="ad783-118">Note how the gray lines connecting all clusters change so that lines leading to the selected cluster are highlighted in bright blue.</span></span>  
  
     <span data-ttu-id="ad783-119">![叢集圖表簡介](media/dm13-cluster-diagram-intro.gif "叢集圖表簡介")</span><span class="sxs-lookup"><span data-stu-id="ad783-119">![cluster diagram intro](media/dm13-cluster-diagram-intro.gif "cluster diagram intro")</span></span>  
  
     <span data-ttu-id="ad783-120">連接一個叢集與另一個叢集的線條濃度代表叢集的相似程度。</span><span class="sxs-lookup"><span data-stu-id="ad783-120">The intensity of the line that connects one cluster to another represents the strength of the similarity of the clusters.</span></span> <span data-ttu-id="ad783-121">如果陰影很淡或不存在，則表示群集不太相似。</span><span class="sxs-lookup"><span data-stu-id="ad783-121">If the shading is light or nonexistent, the clusters are not very similar.</span></span> <span data-ttu-id="ad783-122">當線條色彩加深時，就表示兩個叢集之間的相似度更高。</span><span class="sxs-lookup"><span data-stu-id="ad783-122">As the line becomes darker, it indicates that the similarity between the two clusters is stronger.</span></span>  
  
2.  <span data-ttu-id="ad783-123">按一下並拖曳叢集圖表左側的滑動軸，即可調整檢視器所顯示的線條數目。</span><span class="sxs-lookup"><span data-stu-id="ad783-123">Click and drag the slider to the left of the cluster diagram, to adjust how many lines the viewer shows.</span></span>  
  
     <span data-ttu-id="ad783-124">當您向下拖曳滑動軸時，只會顯示叢集之間最強的連結。</span><span class="sxs-lookup"><span data-stu-id="ad783-124">When you drag the slider down, only the strongest links between clusters are shown.</span></span> <span data-ttu-id="ad783-125">這樣有助於您將焦點放在相關的群組上。</span><span class="sxs-lookup"><span data-stu-id="ad783-125">This helps you focus on related groups.</span></span>  
  
3.  <span data-ttu-id="ad783-126">請注意 [**群集圖表**] 視窗右上角的 [**陰影變數**] 控制項。</span><span class="sxs-lookup"><span data-stu-id="ad783-126">Notice the **Shading Variable** control in the upper right corner of the **Cluster Diagram** window.</span></span>  
  
     <span data-ttu-id="ad783-127">根據預設，它會設定為 [**填入**]。</span><span class="sxs-lookup"><span data-stu-id="ad783-127">By default, it is set to **Population**.</span></span> <span data-ttu-id="ad783-128">這表示，叢集的色彩越深，支援程度越高。</span><span class="sxs-lookup"><span data-stu-id="ad783-128">What this means is that the darker clusters have greater support.</span></span>  
  
4.  <span data-ttu-id="ad783-129">將游標暫停在任何叢集上方。</span><span class="sxs-lookup"><span data-stu-id="ad783-129">Pause over any cluster with the cursor.</span></span>  
  
     <span data-ttu-id="ad783-130">系統就會顯示包含該叢集之母體的工具提示。</span><span class="sxs-lookup"><span data-stu-id="ad783-130">A ToolTip is displayed that contains the population of that cluster.</span></span>  
  
5.  <span data-ttu-id="ad783-131">現在，按一下 [**陰影變數**] 下拉式清單，然後選擇 [ **Age** ] 變數。</span><span class="sxs-lookup"><span data-stu-id="ad783-131">Now, click the **Shading Variable** dropdown list and choose the **Age** variable.</span></span> <span data-ttu-id="ad783-132">當您這麼做時，[**狀態**] 文字方塊中會出現值清單。</span><span class="sxs-lookup"><span data-stu-id="ad783-132">As you do so, a list of values appears in the **State** text box.</span></span>  
  
     <span data-ttu-id="ad783-133">當做此模型之輸入使用的 Age 資料行包含連續數值，但是基於叢集的目的，演算法一定會離散化數字。</span><span class="sxs-lookup"><span data-stu-id="ad783-133">The Age column used as input to this model contains continuous numeric values, but for the purpose of clustering, the algorithm always discretizes numbers.</span></span> <span data-ttu-id="ad783-134">您可以在這裡看到此演算法所建立的 bin 或群組，例如「非常低的 (\<=27)" and "Very High (> = 63) 」。</span><span class="sxs-lookup"><span data-stu-id="ad783-134">Here you can see the bins, or groups that the algorithm created, such as "Very Low (\<=27)" and "Very High (>=63)".</span></span>  
  
6.  <span data-ttu-id="ad783-135">從 [**狀態**] 下拉式清單中，選取 [**非常高**]，並查看圖表的變更方式。</span><span class="sxs-lookup"><span data-stu-id="ad783-135">From the **State** dropdown lists, select **Very High** and see how the diagram changes.</span></span>  
  
     <span data-ttu-id="ad783-136">透過變更陰影變數，您可以快速查看哪些叢集包含這個目標年齡群組的較多客戶，以及哪些叢集包含這個年齡群組中的少數客戶。</span><span class="sxs-lookup"><span data-stu-id="ad783-136">By changing the shading variable, you can see at a glance which clusters contain more of this targeted age group, and which clusters contain very few customers in this age group.</span></span>  
  
     <span data-ttu-id="ad783-137">![修改叢集圖表以顯示年齡](media/dm13-cluster-diagramshadebyage.gif "修改叢集圖表以顯示年齡")</span><span class="sxs-lookup"><span data-stu-id="ad783-137">![Modify the cluster diagram to show age](media/dm13-cluster-diagramshadebyage.gif "Modify the cluster diagram to show age")</span></span>  
  
     <span data-ttu-id="ad783-138">陰影越深，就表示該叢集中目標屬性和值分佈的比例越高。</span><span class="sxs-lookup"><span data-stu-id="ad783-138">The darker the shading, the larger the proportion of the target attribute and value distribution that cluster.</span></span>  
  
7.  <span data-ttu-id="ad783-139">當 [**陰影變數**] 設定為 [Age] >65 時，找出陰影最暗的叢集。</span><span class="sxs-lookup"><span data-stu-id="ad783-139">Locate the cluster that is shaded darkest when the **Shading Variable** is set to Age >65.</span></span>  
  
     <span data-ttu-id="ad783-140">將滑鼠停留在該叢集上方。</span><span class="sxs-lookup"><span data-stu-id="ad783-140">Hover the mouse over the cluster.</span></span>  
  
     <span data-ttu-id="ad783-141">現在，工具提示中顯示的值會為您指出這個叢集中超過 65 歲的客戶比例。</span><span class="sxs-lookup"><span data-stu-id="ad783-141">The value displayed in the ToolTip now shows you the population of customers in this cluster who are over 65.</span></span>  
  
8.  <span data-ttu-id="ad783-142">在叢集上按一下滑鼠右鍵，然後選取 [**重新命名**叢集]。</span><span class="sxs-lookup"><span data-stu-id="ad783-142">Right-click the cluster and select **Rename Cluster**.</span></span> <span data-ttu-id="ad783-143">輸入描述性的新名稱，例如**超過 65**。</span><span class="sxs-lookup"><span data-stu-id="ad783-143">Type a new name that is descriptive, such as **Over 65**.</span></span> <span data-ttu-id="ad783-144">此新名稱就會與模型一併儲存至伺服器，而且可在其他叢集檢視中用來識別該叢集。</span><span class="sxs-lookup"><span data-stu-id="ad783-144">The new name is saved with the model to the server and can be used for identifying the cluster in the other clustering views.</span></span>  
  
 [<span data-ttu-id="ad783-145">回到頁首</span><span class="sxs-lookup"><span data-stu-id="ad783-145">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="cluster-profiles"></a><a name="BKMK_ClusterProfiles"></a><span data-ttu-id="ad783-146">叢集設定檔</span><span class="sxs-lookup"><span data-stu-id="ad783-146">Cluster Profiles</span></span>  
 <span data-ttu-id="ad783-147">[**群集設定檔**] 索引標籤可讓您一眼就比較所有叢集的構成。</span><span class="sxs-lookup"><span data-stu-id="ad783-147">The **Cluster Profiles** tab lets you compare the makeup of all clusters at a glance.</span></span> <span data-ttu-id="ad783-148">這是熟悉模型的絕佳起點。</span><span class="sxs-lookup"><span data-stu-id="ad783-148">This is a good place to start when you are getting familiar with the model.</span></span> <span data-ttu-id="ad783-149">之後，如果您已經在探索特定叢集並且決定需要尋找相關的叢集，這個檢視也很有用。</span><span class="sxs-lookup"><span data-stu-id="ad783-149">This view is also useful later on, if you have been exploring a particular cluster and decide you need to find related ones.</span></span>  
  
 <span data-ttu-id="ad783-150">叢集**設定檔**也能讓您大致瞭解叢集彼此之間的差異。</span><span class="sxs-lookup"><span data-stu-id="ad783-150">**Cluster Profiles** also gives you a good overview of how the clusters are different from each other.</span></span> <span data-ttu-id="ad783-151">因此，您可能會發現使用這個檢視來指定每個叢集的描述性名稱很方便。</span><span class="sxs-lookup"><span data-stu-id="ad783-151">Therefore, you might find it convenient to use this view to give each cluster a descriptive name.</span></span>  
  
##### <a name="explore-the-cluster-profiles"></a><span data-ttu-id="ad783-152">探索叢集設定檔</span><span class="sxs-lookup"><span data-stu-id="ad783-152">Explore the cluster profiles</span></span>  
  
1.  <span data-ttu-id="ad783-153">按一下 [**狀態**] 資料行中職業的資料格，以查看所有職業值的清單。</span><span class="sxs-lookup"><span data-stu-id="ad783-153">Click the cell for Occupations, in the **States** column, to see the list of all values for Occupation.</span></span>  
  
2.  <span data-ttu-id="ad783-154">現在，將游標移至叢集設定檔中的 Occupation 上方。</span><span class="sxs-lookup"><span data-stu-id="ad783-154">Now move the cursor over Occupation in the cluster profiles.</span></span>  
  
     <span data-ttu-id="ad783-155">工具提示就會顯示該叢集的職業分佈。</span><span class="sxs-lookup"><span data-stu-id="ad783-155">The ToolTip shows the distribution of occupations in that cluster.</span></span>  
  
     <span data-ttu-id="ad783-156">![在 [工具提示] 或 [圖例] 中檢視詳細值](media/dm13-cluster-profile-age-tooltip.gif "在 [工具提示] 或 [圖例] 中檢視詳細值")</span><span class="sxs-lookup"><span data-stu-id="ad783-156">![View detailed values in Tooltips or in Legend](media/dm13-cluster-profile-age-tooltip.gif "View detailed values in Tooltips or in Legend")</span></span>  
  
     <span data-ttu-id="ad783-157">請注意，在某些叢集 (（例如圖形) 中的），職業清單並不完整，而且某些職業會取代為標籤 [**其他**]。</span><span class="sxs-lookup"><span data-stu-id="ad783-157">Notice that, in some clusters (such as the one in the graphic), the list of occupations is not complete, and some occupations are replaced with the label, **Other**.</span></span>  
  
     <span data-ttu-id="ad783-158">這是設計所限，因為要在長條圖中區分許多小列之間的差異可能很困難。</span><span class="sxs-lookup"><span data-stu-id="ad783-158">This is by design, because it can be hard to tell the difference between many small bars in a histogram.</span></span> <span data-ttu-id="ad783-159">根據預設，只會保留最重要的橫條，其餘的橫條則會群組在一起成為灰色的**其他**值區。</span><span class="sxs-lookup"><span data-stu-id="ad783-159">By default only the bars of highest importance are retained, and the remaining bars are grouped together into a gray **Other** bucket.</span></span>  
  
     <span data-ttu-id="ad783-160">若要變更任何長條圖中可見的橫條數，請使用 [**長條圖**列] 選項。</span><span class="sxs-lookup"><span data-stu-id="ad783-160">To change the number of bars that are visible in any histogram, use the option **Histogram bars**.</span></span>  
  
3.  <span data-ttu-id="ad783-161">請注意，[**年齡**] 資料行看起來與其他欄位不同。</span><span class="sxs-lookup"><span data-stu-id="ad783-161">Note that the **Age** column looks different from the others.</span></span> <span data-ttu-id="ad783-162">在用來代表年齡的圖表中，按一下菱形。</span><span class="sxs-lookup"><span data-stu-id="ad783-162">Click the diamond in the chart used to represent Age.</span></span>  
  
     <span data-ttu-id="ad783-163">Age 資料行原本僅包含連續數字。</span><span class="sxs-lookup"><span data-stu-id="ad783-163">The column Age originally contained only continuous numbers.</span></span> <span data-ttu-id="ad783-164">叢集演算法需要離散值，因此它便根據值的分佈，將 Age 資料行中的數值分組成有限數目的年齡群組。</span><span class="sxs-lookup"><span data-stu-id="ad783-164">The clustering algorithm requires discrete values, so it grouped the numeric values in the Age column into a limited number of age groups, based on the distribution of values.</span></span>  
  
4.  <span data-ttu-id="ad783-165">按一下叢集設定檔的其中一個菱形圖表。</span><span class="sxs-lookup"><span data-stu-id="ad783-165">Click one of the diamond charts in a cluster profile.</span></span>  
  
     <span data-ttu-id="ad783-166">只有在來源資料使用連續數值時，才會顯示這些菱形圖表。</span><span class="sxs-lookup"><span data-stu-id="ad783-166">These diamond charts are displayed only when the source data uses continuous numeric values.</span></span> <span data-ttu-id="ad783-167">菱形圖表會提供一些有用的描述性統計資料，包括每個叢集中該值的平均和標準差：</span><span class="sxs-lookup"><span data-stu-id="ad783-167">The diamond charts provide some useful descriptive statistics, including the mean and standard deviation for that value in each cluster:</span></span>  
  
    -   <span data-ttu-id="ad783-168">菱形圖表中的線條代表屬性值的範圍。</span><span class="sxs-lookup"><span data-stu-id="ad783-168">The line in the diamond chart represents the range of values for the attribute.</span></span> <span data-ttu-id="ad783-169">這些值也會顯示在**設定檔**圖表左邊的 [**狀態**] 資料行中。</span><span class="sxs-lookup"><span data-stu-id="ad783-169">The values are also shown in the **States** column at the left of the **Profiles** chart.</span></span>  
  
    -   <span data-ttu-id="ad783-170">菱形的中心位於節點的平均。</span><span class="sxs-lookup"><span data-stu-id="ad783-170">The center of the diamond is positioned at the mean for the node.</span></span>  
  
    -   <span data-ttu-id="ad783-171">菱形的寬度代表該節點的屬性變異數。</span><span class="sxs-lookup"><span data-stu-id="ad783-171">The width of the diamond represents the variance of the attribute at that node.</span></span> <span data-ttu-id="ad783-172">因此，菱形越窄，表示節點所建立的預測愈精確。</span><span class="sxs-lookup"><span data-stu-id="ad783-172">Therefore, a thinner diamond indicates that the node can create a more accurate prediction.</span></span>  
  
5.  <span data-ttu-id="ad783-173">若要在圖形中建立更多空間，請以滑鼠右鍵按一下您不需要立即查看的叢集，然後選取 [**隱藏資料行**]。</span><span class="sxs-lookup"><span data-stu-id="ad783-173">To make more room in the graph, right-click a cluster you don't need to view right away, and select **Hide Column**.</span></span> <span data-ttu-id="ad783-174">這不會將它從模型中刪除，只要暫時折迭資料行即可。</span><span class="sxs-lookup"><span data-stu-id="ad783-174">This doesn't delete it from the model, just collapses the column temporarily.</span></span>  
  
     <span data-ttu-id="ad783-175">若要查看您已隱藏的叢集，您可以按一下並拖曳資料行邊緣，或從清單中選取 [**更多**叢集] 的叢集名稱。</span><span class="sxs-lookup"><span data-stu-id="ad783-175">To view clusters that you've hidden, you can click and drag the column edge, or select the cluster name from the list, **More clusters**.</span></span>  
  
6.  <span data-ttu-id="ad783-176">向下捲動屬性清單，直到您找到 Bike Buyer 為止，然後尋找 Yes 值百分比最高的叢集。</span><span class="sxs-lookup"><span data-stu-id="ad783-176">Scroll down the attribute list till you find Bike Buyer, and then find the cluster that has the highest percentage of Yes values.</span></span>  
  
     <span data-ttu-id="ad783-177">在您要重新命名之叢集的資料行標題上按一下滑鼠右鍵，選取 [**重新命名**叢集]，然後輸入**自行車購買**者。</span><span class="sxs-lookup"><span data-stu-id="ad783-177">Right-click the column heading for the cluster that you want to rename, select **Rename cluster**, and type **Bike Buyers**.</span></span>  
  
     <span data-ttu-id="ad783-178">新的叢集名稱就會保存在所有檢視和伺服器中，直到您重新處理模型為止。</span><span class="sxs-lookup"><span data-stu-id="ad783-178">The new cluster name is persisted in all views, and on the server, until you reprocess the model.</span></span>  
  
     <span data-ttu-id="ad783-179">![重新命名叢集讓圖表更容易使用](media/dm13-cluster-rename.gif "重新命名叢集讓圖表更容易使用")</span><span class="sxs-lookup"><span data-stu-id="ad783-179">![Rename clusters to make chart easier to use](media/dm13-cluster-rename.gif "Rename clusters to make chart easier to use")</span></span>  
  
 <span data-ttu-id="ad783-180">**提示**</span><span class="sxs-lookup"><span data-stu-id="ad783-180">**Tips**</span></span>  
  
-   <span data-ttu-id="ad783-181">按一下資料行標題，即可依該群集的重要性順序來排序屬性。</span><span class="sxs-lookup"><span data-stu-id="ad783-181">Click a column heading to sort the attributes in order of importance for that cluster.</span></span>  
  
-   <span data-ttu-id="ad783-182">拖曳資料行，即可在檢視器中重新排列它們。</span><span class="sxs-lookup"><span data-stu-id="ad783-182">Drag columns to reorder them in the viewer.</span></span>  
  
-   <span data-ttu-id="ad783-183">按一下 [設定檔] 圖表中的任何資料格，即可在 [**挖掘圖例**] 中查看詳細的統計資料。</span><span class="sxs-lookup"><span data-stu-id="ad783-183">Click any cell in the profiles chart to view detailed statistics in the **Mining Legend**.</span></span>  
  
-   <span data-ttu-id="ad783-184">以滑鼠右鍵按一下任何資料格，並選取 [**鑽取模型資料行**]，將基礎資料輸出至 Excel 中的新工作表。</span><span class="sxs-lookup"><span data-stu-id="ad783-184">Right-click any cell and select **Drillthrough model columns** to output the underlying data to a new worksheet in Excel.</span></span>  
  
-   <span data-ttu-id="ad783-185">以滑鼠右鍵按一下叢集的資料行標題，然後選取 [**鑽取至結構資料**]，以取得模型中未包含之叢集成員的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ad783-185">Right-click the cluster's column heading and select **Drillthrough to structure data** to get detailed information about the cluster members that wasn't included in the model.</span></span>  
  
     <span data-ttu-id="ad783-186">例如，如果您要分析客戶，您可能會將基礎資料中的連絡人資訊保留 (的採礦結構) 但不會將它包含在模型中，因為它不適用於分析。</span><span class="sxs-lookup"><span data-stu-id="ad783-186">For example, if you are profiling customers, you might leave the contact information in the underlying data (the mining structure) but not include it in the model, because it's not useful for analysis.</span></span> <span data-ttu-id="ad783-187">不過，將客戶指派給叢集之後，您就可以使用鑽研來檢視詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ad783-187">However, after customers have been assigned to clusters, you can view the detailed data by using drillthrough.</span></span>  
  
 [<span data-ttu-id="ad783-188">回到頁首</span><span class="sxs-lookup"><span data-stu-id="ad783-188">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="cluster-characteristics"></a><a name="BKMK_ClusterCharacteristics"></a> <span data-ttu-id="ad783-189">群集特性</span><span class="sxs-lookup"><span data-stu-id="ad783-189">Cluster Characteristics</span></span>  
 <span data-ttu-id="ad783-190">[叢集特性] 檢視可讓您實際探索單一叢集，以便找出哪些屬性最能代表這個資料群組的特性。</span><span class="sxs-lookup"><span data-stu-id="ad783-190">The Cluster Characteristics view lets you really explore a single cluster, to find which attributes most strongly characterize this group of data.</span></span>  
  
##### <a name="explore-the-cluster-characteristics"></a><span data-ttu-id="ad783-191">探索叢集特性</span><span class="sxs-lookup"><span data-stu-id="ad783-191">Explore the cluster characteristics</span></span>  
  
1.  <span data-ttu-id="ad783-192">從 [叢集 **] 清單中選取 [** **超過 65**叢集]。</span><span class="sxs-lookup"><span data-stu-id="ad783-192">Select the **Over 65** cluster from the **Cluster** list.</span></span>  
  
     <span data-ttu-id="ad783-193">選取叢集之後，您就可以詳細查看構成該特定叢集的特性。</span><span class="sxs-lookup"><span data-stu-id="ad783-193">After you select a cluster, you can see in detail the characteristics that make up that specific cluster.</span></span>  
  
     <span data-ttu-id="ad783-194">群集包含的屬性將列於 **[變數]** 資料行中，而所列屬性的狀態則列於 **[值]** 資料行中。</span><span class="sxs-lookup"><span data-stu-id="ad783-194">The attributes that the cluster contains are listed in the **Variables** columns, and the state of the listed attribute is listed in the **Values** column.</span></span>  
  
     <span data-ttu-id="ad783-195">屬性狀態會依重要性順序列出，伴隨其在此叢**集中的機率，以 [機率**] 資料行中的彩色橫條表示。</span><span class="sxs-lookup"><span data-stu-id="ad783-195">Attribute states are listed in order of importance, accompanied by their probability in this cluster, represented as a colored bar in the **Probability** column.</span></span>  
  
     <span data-ttu-id="ad783-196">![叢集模型的特性](media/dm13-cluster-characteristics.gif "叢集模型的特性")</span><span class="sxs-lookup"><span data-stu-id="ad783-196">![Characteristics of a clustering model](media/dm13-cluster-characteristics.gif "Characteristics of a clustering model")</span></span>  
  
2.  <span data-ttu-id="ad783-197">按一下 [**變數**] 資料行，依屬性排序。</span><span class="sxs-lookup"><span data-stu-id="ad783-197">Click the **Variables** column to sort by attribute.</span></span>  
  
     <span data-ttu-id="ad783-198">透過變更排序變數，您就可以更輕鬆地查看收入或是否擁有汽車等變數值在群組中分佈的方式。</span><span class="sxs-lookup"><span data-stu-id="ad783-198">By changing the sort variable, you can more easily see how values for variables such as income or car ownership are distributed in the group.</span></span>  
  
3.  <span data-ttu-id="ad783-199">按一下 [**複製到 Excel**]。</span><span class="sxs-lookup"><span data-stu-id="ad783-199">Click **Copy to Excel**.</span></span>  
  
     <span data-ttu-id="ad783-200">新的工作表就會加入至包含選取叢集之特性的活頁簿。</span><span class="sxs-lookup"><span data-stu-id="ad783-200">A new worksheet is added to your workbook that contains the characteristics of the selected cluster.</span></span>  
  
4.  <span data-ttu-id="ad783-201">現在從 [**自行車購買**者] 清單中選擇不同的叢集。</span><span class="sxs-lookup"><span data-stu-id="ad783-201">Now choose a different cluster from the list, **Bike Buyers**.</span></span>  
  
5.  <span data-ttu-id="ad783-202">按一下 [**複製到 Excel**]。</span><span class="sxs-lookup"><span data-stu-id="ad783-202">Click **Copy to Excel**.</span></span>  
  
     <span data-ttu-id="ad783-203">請注意，新的叢集特性圖表會加入至它自己的工作表中。</span><span class="sxs-lookup"><span data-stu-id="ad783-203">Note that the new cluster characteristics chart is added on its own worksheet.</span></span> <span data-ttu-id="ad783-204">您可以將它移至與另一個設定檔相同的工作表，以便更輕鬆地比較它們，您可以在下一個步驟中進行。</span><span class="sxs-lookup"><span data-stu-id="ad783-204">You can move it onto the same worksheet as the other profile to make it easier to compare them, which you'll do in the next step.</span></span>  
  
 <span data-ttu-id="ad783-205">**提示**</span><span class="sxs-lookup"><span data-stu-id="ad783-205">**Tips**</span></span>  
  
-   <span data-ttu-id="ad783-206">請注意，過去65叢集中的客戶主要特性是他們不會購買您的產品！</span><span class="sxs-lookup"><span data-stu-id="ad783-206">Note that the primary characteristic of the customer in the Over 65 cluster is that they don't buy your product!</span></span> <span data-ttu-id="ad783-207">如果您想要了解原因，可以瀏覽叢集並比較群組，也可以使用適合探索原因和結果的演算法來建立相關模型，例如決策樹模型或貝氏機率分類模型。</span><span class="sxs-lookup"><span data-stu-id="ad783-207">If you want to know why this is so, you can browse clusters and compare groups, or you might create a related model using an algorithm that is good at exploring causes and outcomes, such as a decision tree model or a Naïve Bayes model.</span></span>  
  
-   <span data-ttu-id="ad783-208">如果您想要取得這個叢集 (或所有叢集) 之屬性和機率的完整清單，可以建立查詢。</span><span class="sxs-lookup"><span data-stu-id="ad783-208">If you want to get a complete list of attributes and probabilities for this cluster (or all clusters) you can create a query.</span></span> <span data-ttu-id="ad783-209">如需群集模型查詢的範例，請參閱叢集[模型查詢範例](data-mining/clustering-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="ad783-209">For examples of queries on clustering models, see [Clustering Model Query Examples](data-mining/clustering-model-query-examples.md).</span></span>  
  
 [<span data-ttu-id="ad783-210">回到頁首</span><span class="sxs-lookup"><span data-stu-id="ad783-210">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="cluster-discrimination"></a><a name="BKMK_ClusterDiscrimination"></a><span data-ttu-id="ad783-211">群集辨識</span><span class="sxs-lookup"><span data-stu-id="ad783-211">Cluster Discrimination</span></span>  
 <span data-ttu-id="ad783-212">您可以使用 **[叢集**辨識] 索引標籤來比較兩個叢集之間的屬性，或叢集與資料集內所有其他案例之間的屬性。</span><span class="sxs-lookup"><span data-stu-id="ad783-212">You use the **Cluster Discrimination** tab to compare attributes between two clusters, or between a cluster and all the other cases in the data set.</span></span>  
  
 <span data-ttu-id="ad783-213">為了強調此檢視器的功能，我們會將它與您根據 [叢集**特性**] 視圖所建立之 Excel 中的並列資料表做比較。</span><span class="sxs-lookup"><span data-stu-id="ad783-213">To highlight the features of this viewer, we'll compare it to the side-by-side tables in Excel that you created based on the **Cluster Characteristics** view.</span></span>  
  
##### <a name="explore-cluster-discrimination"></a><span data-ttu-id="ad783-214">探索叢集辨識</span><span class="sxs-lookup"><span data-stu-id="ad783-214">Explore cluster discrimination</span></span>  
  
1.  <span data-ttu-id="ad783-215">請使用 **[群集 1]** 和 **[群集 2]** 清單來選取要比較的群集。</span><span class="sxs-lookup"><span data-stu-id="ad783-215">Use the **Cluster 1** and **Cluster 2** lists to select the clusters to compare.</span></span>  
  
    -   <span data-ttu-id="ad783-216">針對 [叢集 1]，選取 [Over 65]。</span><span class="sxs-lookup"><span data-stu-id="ad783-216">For Cluster 1, select Over 65.</span></span>  
  
    -   <span data-ttu-id="ad783-217">針對 [叢集 2]，選取 [Bike Buyers]。</span><span class="sxs-lookup"><span data-stu-id="ad783-217">For Cluster 2, select Bike Buyers.</span></span>  
  
     <span data-ttu-id="ad783-218">比較結果看起來應該類似於下圖。</span><span class="sxs-lookup"><span data-stu-id="ad783-218">The comparison should look similar to the following graphic.</span></span>  
  
     <span data-ttu-id="ad783-219">![比較模型中的叢集](media/dm13-cluster-compareclusters.gif "比較模型中的叢集")</span><span class="sxs-lookup"><span data-stu-id="ad783-219">![comparing clusters in a model](media/dm13-cluster-compareclusters.gif "comparing clusters in a model")</span></span>  
  
     <span data-ttu-id="ad783-220">請注意，在幕後，叢集辨識**檢視器**會將複雜的查詢傳送至資料採礦伺服器，以便在區分兩個群組時，將最重要的屬性解壓縮，讓比較兩組客戶更容易。</span><span class="sxs-lookup"><span data-stu-id="ad783-220">Note that, under the covers, the **Cluster Discrimination** viewer sends complex queries to the data mining server, to extract the attributes that are most important in distinguishing between the two groups, making it easier to compare two sets of customers.</span></span>  
  
2.  <span data-ttu-id="ad783-221">按一下其中**一個 [喜好**] 資料行。</span><span class="sxs-lookup"><span data-stu-id="ad783-221">Click either of the **Favors...** columns.</span></span>  
  
     <span data-ttu-id="ad783-222">屬性與值清單右側的列就會顯示哪些屬性或值是選取叢集的最重要特性。</span><span class="sxs-lookup"><span data-stu-id="ad783-222">The bar to the right of the attribute and value list shows which features or values are most important as a characteristic of the selected cluster.</span></span>  
  
3.  <span data-ttu-id="ad783-223">現在，請在 Excel 中比較清單。</span><span class="sxs-lookup"><span data-stu-id="ad783-223">Now compare the lists in Excel.</span></span>  
  
     <span data-ttu-id="ad783-224">![關聯模型的相依性網路圖表](media/dm13-comparing-profiles-in-excel.gif "關聯模型的相依性網路圖表")</span><span class="sxs-lookup"><span data-stu-id="ad783-224">![Dependency network graph for an association model](media/dm13-comparing-profiles-in-excel.gif "Dependency network graph for an association model")</span></span>  
  
     <span data-ttu-id="ad783-225">因為原本在檢視器中用來建立影像的基礎統計資料已儲存至 Excel 成為資料表，所以您可以進行篩選和排序，並且檢視實際的機率值。</span><span class="sxs-lookup"><span data-stu-id="ad783-225">Because the underlying statistics that were used to build the image in the viewer are saved to Excel as tables, you can filter and sort, and view the actual probability values.</span></span>  
  
     <span data-ttu-id="ad783-226">除了使用 Excel 以外，我們也建議您嘗試 Visio 的叢集檢視器，這個檢視器不僅能讓您檢視資料點，還能廣泛地修改並增強圖形。</span><span class="sxs-lookup"><span data-stu-id="ad783-226">In addition to using Excel, we recommend that you try the cluster viewer for Visio, which also allows you to not just view data points but also extensively modify and enhance the graph.</span></span> <span data-ttu-id="ad783-227">如需詳細資訊，請參閱叢集[圖表逐步解說 &#40;資料採礦增益集&#41;](cluster-diagram-walkthrough-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="ad783-227">For more information, see [Cluster Diagram Walkthrough &#40;Data Mining Add-ins&#41;](cluster-diagram-walkthrough-data-mining-add-ins.md).</span></span>  
  
 <span data-ttu-id="ad783-228">**提示**</span><span class="sxs-lookup"><span data-stu-id="ad783-228">**Tips**</span></span>  
  
 <span data-ttu-id="ad783-229">取得客戶群組的深入解析之後，請嘗試 &#40;使用[適用于 excel 的資料表分析工具&#41;](what-if-scenario-table-analysis-tools-for-excel.md)或[目標搜尋案例 &#40;](goal-seek-scenario-table-analysis-tools-for-excel.md)適用于 Excel&#41;工具的資料表分析工具]，以探索模型中可能會變更以影響結果的因素。</span><span class="sxs-lookup"><span data-stu-id="ad783-229">After getting some insights into groups of customers, try using the [What-If Scenario &#40;Table Analysis Tools for Excel&#41;](what-if-scenario-table-analysis-tools-for-excel.md) or [Goal Seek Scenario &#40;Table Analysis Tools for Excel&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md) tools, to explore factors in the model that might be changed to affect the outcome.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad783-230">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad783-230">See Also</span></span>  
 <span data-ttu-id="ad783-231">[在 Excel 中流覽模型 &#40;SQL Server 資料採礦增益集&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="ad783-231">[Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="ad783-232">叢集 Wizard &#40;適用于 Excel 的資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="ad783-232">Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](cluster-wizard-data-mining-add-ins-for-excel.md)  
  
  
