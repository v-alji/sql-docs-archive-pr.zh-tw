---
title: 流覽購物籃模型 (中繼資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: da1c9cb7-6c32-4b9b-96ec-ecea772aeb77
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d6246aa9330042f0e8033b6f2633a3ed24331ba7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704470"
---
# <a name="exploring-the-market-basket-models-intermediate-data-mining-tutorial"></a><span data-ttu-id="2bfba-102">探索購物籃模型 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="2bfba-102">Exploring the Market Basket Models (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="2bfba-103">現在您已建立 `Association` 模型，您可以 [!INCLUDE[msCoName](../includes/msconame-md.md)] 在資料採礦設計師的 [**採礦模型檢視器**] 索引標籤中，使用 [關聯檢視器] 來進行探索。</span><span class="sxs-lookup"><span data-stu-id="2bfba-103">Now that you have built the `Association` model, you can explore it by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Viewer in the **Mining Model Viewer** tab of Data Mining Designer.</span></span> <span data-ttu-id="2bfba-104">此教學課程會逐步引導您使用檢視器來探索項目之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="2bfba-104">This tutorial walks you through using the viewer to explore relationships between items.</span></span> <span data-ttu-id="2bfba-105">此檢視器可幫助您快速地查看哪些產品經常一起出現，並大概了解新興的模式。</span><span class="sxs-lookup"><span data-stu-id="2bfba-105">The viewer helps you see at a glance which products tend to appear together, and get a general idea of the emerging patterns.</span></span>  
  
 <span data-ttu-id="2bfba-106">[ [!INCLUDE[msCoName](../includes/msconame-md.md)] 關聯檢視器] 包含三個索引標籤：**規則**、**專案集**和相依性**網路**。</span><span class="sxs-lookup"><span data-stu-id="2bfba-106">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Viewer contains three tabs: **Rules**, **Itemsets**, and **Dependency Network**.</span></span> <span data-ttu-id="2bfba-107">因為每一個索引標籤都會呈現稍微不同的資料檢視，所以當您探索模型時，您通常會在不同的窗格之間來回切換幾次，以獲得有用的資訊。</span><span class="sxs-lookup"><span data-stu-id="2bfba-107">Because each tab reveals a slightly different view of the data, when you are exploring a model, you will typically switch back and forth between the different panes several times as you pursue insights.</span></span>  
  
-   [<span data-ttu-id="2bfba-108">相依性網路索引標籤</span><span class="sxs-lookup"><span data-stu-id="2bfba-108">Dependency Network tab</span></span>](#bkmk_DepNet)  
  
-   [<span data-ttu-id="2bfba-109">專案集索引標籤</span><span class="sxs-lookup"><span data-stu-id="2bfba-109">Itemsets tab</span></span>](#bkmk_Itemsets)  
  
-   [<span data-ttu-id="2bfba-110">規則索引標籤</span><span class="sxs-lookup"><span data-stu-id="2bfba-110">Rules tab</span></span>](#bkmk_Rules)  
  
-   [<span data-ttu-id="2bfba-111">一般內容檢視</span><span class="sxs-lookup"><span data-stu-id="2bfba-111">Generic Content View</span></span>](#bkmk_ContentViewer)  
  
 <span data-ttu-id="2bfba-112">在本教學課程中，您將從 [相依性**網路**] 索引標籤開始，然後使用 [**規則**] 索引標籤和 [**專案集**] 索引標籤，加深您對檢視器中所顯示的關聯性</span><span class="sxs-lookup"><span data-stu-id="2bfba-112">For this tutorial, you will start on the **Dependency Network** tab, and then use the **Rules** tab and **Itemsets** tab to deepen your understanding of the relationships revealed in the viewer.</span></span> <span data-ttu-id="2bfba-113">您也會使用 [ **Microsoft 一般內容樹狀檢視器]** 來取得個別規則或專案集的詳細統計資料。</span><span class="sxs-lookup"><span data-stu-id="2bfba-113">You will also use the **Microsoft Generic Content Tree Viewer** to retrieve detailed statistics for individual rules or itemsets.</span></span>  
  
##  <a name="dependency-network-tab"></a><a name="bkmk_DepNet"></a><span data-ttu-id="2bfba-114">相依性網路索引標籤</span><span class="sxs-lookup"><span data-stu-id="2bfba-114">Dependency Network Tab</span></span>  
 <span data-ttu-id="2bfba-115">使用 [相依性**網路**] 索引標籤，您可以調查模型中不同專案的互動。</span><span class="sxs-lookup"><span data-stu-id="2bfba-115">With the **Dependency Network** tab, you can investigate the interaction of the different items in the model.</span></span> <span data-ttu-id="2bfba-116">檢視器中的每一個節點都代表某個項目，而節點之間的線條則代表規則。</span><span class="sxs-lookup"><span data-stu-id="2bfba-116">Each node in the viewer represents an item, while the lines between them represent rules.</span></span> <span data-ttu-id="2bfba-117">您可以透過選取某個節點，查看其他哪些節點會預測選取的項目，或目前的項目預測出哪些項目。</span><span class="sxs-lookup"><span data-stu-id="2bfba-117">By selecting a node, you can see which other nodes predict the selected item, or which items the current item predicts.</span></span> <span data-ttu-id="2bfba-118">在某些情況下，項目之間會存在雙向關聯，表示它們通常會出現在同一項交易中。</span><span class="sxs-lookup"><span data-stu-id="2bfba-118">In some cases, there is a two-way association between items, meaning that they often appear in the same transaction.</span></span> <span data-ttu-id="2bfba-119">您可以參考此索引標籤底部的色彩圖例來判斷關聯的方向。</span><span class="sxs-lookup"><span data-stu-id="2bfba-119">You can refer to the color legend at the bottom of the tab to determine the direction of the association.</span></span>  
  
 <span data-ttu-id="2bfba-120">連接兩個項目的線條表示，這兩個項目很可能同時出現在單一交易中。</span><span class="sxs-lookup"><span data-stu-id="2bfba-120">A line connecting two items means that these items are likely to appear in a transaction together.</span></span> <span data-ttu-id="2bfba-121">換句話說，客戶很可能一起購買這兩個項目。</span><span class="sxs-lookup"><span data-stu-id="2bfba-121">In other words, customers are likely to buy these items together.</span></span> <span data-ttu-id="2bfba-122">滑動軸與規則的機率相關。</span><span class="sxs-lookup"><span data-stu-id="2bfba-122">The slider is associated with the probability of the rule.</span></span> <span data-ttu-id="2bfba-123">將滑動軸往上移或往下移來篩選掉微弱的關聯，也就是機率很低的規則。</span><span class="sxs-lookup"><span data-stu-id="2bfba-123">Move the slider up or down to filter out weak associations, meaning rules with low probability.</span></span>  
  
 <span data-ttu-id="2bfba-124">[相依性網路] 圖表會顯示成對的規則，其可以邏輯方式表示為->B，這表示如果產品 A 已購買，則可能會有產品 B。</span><span class="sxs-lookup"><span data-stu-id="2bfba-124">The dependency network graph shows pairwise rules, which can be represented logically as A->B, meaning if Product A is purchased, then Product B is likely.</span></span> <span data-ttu-id="2bfba-125">圖形無法顯示 AB >C 類型的規則。</span><span class="sxs-lookup"><span data-stu-id="2bfba-125">The graph cannot show rules of the type AB->C.</span></span> <span data-ttu-id="2bfba-126">如果您移動滑動軸來顯示所有規則，但是在圖表中仍然未看到任何線條，這表示沒有任何成對規則符合演算法參數的準則。</span><span class="sxs-lookup"><span data-stu-id="2bfba-126">If you move the slider to show all rules but still do not see any lines in the graph, it means that there were no pairwise rules that met the criteria of the algorithm parameters.</span></span>  
  
 <span data-ttu-id="2bfba-127">您也可以依據名稱來尋找節點，其方式是輸入屬性名稱的第一個字母。</span><span class="sxs-lookup"><span data-stu-id="2bfba-127">You can also find nodes by name, by typing the first letters of the attribute name.</span></span> <span data-ttu-id="2bfba-128">如需詳細資訊，請參閱[尋找節點對話方塊 &#40;採礦模型檢視器&#41;](../../2014/analysis-services/find-node-dialog-box-mining-model-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="2bfba-128">For more information, see [Find Node Dialog Box &#40;Mining Model Viewer&#41;](../../2014/analysis-services/find-node-dialog-box-mining-model-viewer.md).</span></span>  
  
#### <a name="to-open-the-association-mode-in-the-microsoft-assocaition-rules-viewer"></a><span data-ttu-id="2bfba-129">若要在 Microsoft 關聯規則檢視器中開啟關聯模式</span><span class="sxs-lookup"><span data-stu-id="2bfba-129">To open the Association mode in the Microsoft Assocaition Rules Viewer</span></span>  
  
1.  <span data-ttu-id="2bfba-130">在**方案總管**中，按兩下 [關聯結構]。</span><span class="sxs-lookup"><span data-stu-id="2bfba-130">In **Solution Explorer**, double-click the Association structure.</span></span>  
  
2.  <span data-ttu-id="2bfba-131">在資料採礦設計師中，按一下 **[採礦模型檢視器]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2bfba-131">In Data Mining Designer, click the **Mining Model Viewer** tab.</span></span>  
  
3.  <span data-ttu-id="2bfba-132">從 [**採礦模型**] 下拉式清單中的 [採礦模型] 清單中選取 [關聯]。</span><span class="sxs-lookup"><span data-stu-id="2bfba-132">Select Association from the list of mining models in the **Mining Model** dropdown list.</span></span>  
  
#### <a name="to-navigate-the-dependency-graph-and-locate-specific-nodes"></a><span data-ttu-id="2bfba-133">若要導覽相依性圖表及尋找特定的節點</span><span class="sxs-lookup"><span data-stu-id="2bfba-133">To navigate the dependency graph and locate specific nodes</span></span>  
  
1.  <span data-ttu-id="2bfba-134">在 [**模型檢視器**] 索引標籤中，按一下 [相依性**網路**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2bfba-134">In the **Mining Model Viewer** tab, click the **Dependency Network** tab.</span></span>  
  
2.  <span data-ttu-id="2bfba-135">按一下 [**放大**數次]，直到您可以輕鬆地查看每個節點的標籤為止。</span><span class="sxs-lookup"><span data-stu-id="2bfba-135">Click **Zoom In** several times, until you can easily view the labels for each node.</span></span>  
  
     <span data-ttu-id="2bfba-136">根據預設，顯示此圖表時，將可看見所有的節點。</span><span class="sxs-lookup"><span data-stu-id="2bfba-136">By default, the graph displays with all nodes visible.</span></span> <span data-ttu-id="2bfba-137">複雜模型中可能有許多節點，使得每一個節點看起來很小。</span><span class="sxs-lookup"><span data-stu-id="2bfba-137">In a complex model, there may be many nodes, making each node quite small.</span></span>  
  
3.  <span data-ttu-id="2bfba-138">按一下 **+** 檢視器右下角的 [登入]，然後按住滑鼠按鍵以移動圖形。</span><span class="sxs-lookup"><span data-stu-id="2bfba-138">Click the **+** sign in the lower right-hand corner of the viewer and hold down the mouse button to pan around the graph.</span></span>  
  
4.  <span data-ttu-id="2bfba-139">在檢視器的左側，將滑杆向下拖曳，並將其從 [**所有連結**] ([預設) ] 移至滑杆控制項的底部。</span><span class="sxs-lookup"><span data-stu-id="2bfba-139">On the left side of the viewer, drag the slider down, moving it from **All Links** (the default) to the bottom of the slider control.</span></span>  
  
5.  <span data-ttu-id="2bfba-140">檢視器會更新此圖表，現在它只會顯示 Touring Tire 與 Touring Tire Tube 項目之間最強的關聯。</span><span class="sxs-lookup"><span data-stu-id="2bfba-140">The viewer updates the graph to now show only the strongest association, between the Touring Tire and Touring Tire Tube items.</span></span>  
  
6.  <span data-ttu-id="2bfba-141">按一下標示為「**旅行輪胎電子管 = 現有**」的節點。</span><span class="sxs-lookup"><span data-stu-id="2bfba-141">Click the node labeled **Touring Tire Tube = Existing**.</span></span>  
  
     <span data-ttu-id="2bfba-142">此圖表會更新，僅反白顯示與此項目之間有強烈相關性的項目。</span><span class="sxs-lookup"><span data-stu-id="2bfba-142">The graph is updated to highlight only items that are strongly related to this item.</span></span> <span data-ttu-id="2bfba-143">請注意兩個項目之間的箭頭方向。</span><span class="sxs-lookup"><span data-stu-id="2bfba-143">Note the direction of the arrow between the two items.</span></span>  
  
7.  <span data-ttu-id="2bfba-144">在檢視器的左邊，將滑動軸再次往上拖曳，將它從底部移到中間附近。</span><span class="sxs-lookup"><span data-stu-id="2bfba-144">On the left side of the viewer, drag the slider up again, moving it from the bottom to around the middle.</span></span>  
  
     <span data-ttu-id="2bfba-145">請注意連接兩個項目之箭頭的變更。</span><span class="sxs-lookup"><span data-stu-id="2bfba-145">Note the changes in the arrow that connects the two items.</span></span>  
  
8.  <span data-ttu-id="2bfba-146">從 [相依性網路] 窗格頂端的下拉式清單中，選取 [**只顯示內容名稱**]。</span><span class="sxs-lookup"><span data-stu-id="2bfba-146">Select **Show attribute name only** from the dropdown list at the top of the Dependency Network pane.</span></span>  
  
     <span data-ttu-id="2bfba-147">圖表中的文字標籤會更新，只顯示模型名稱。</span><span class="sxs-lookup"><span data-stu-id="2bfba-147">The text labels in the graph are updated to show only the model name.</span></span>  
  
 [<span data-ttu-id="2bfba-148">回到頁首</span><span class="sxs-lookup"><span data-stu-id="2bfba-148">Back to Top</span></span>](#bkmk_DepNet)  
  
##  <a name="itemsets-tab"></a><a name="bkmk_Itemsets"></a><span data-ttu-id="2bfba-149">專案集索引標籤</span><span class="sxs-lookup"><span data-stu-id="2bfba-149">Itemsets Tab</span></span>  
 <span data-ttu-id="2bfba-150">接下來，您將會深入了解此模型針對 Touring Tire 和 Touring Tire Tube 產品所產生的規則與項目集。</span><span class="sxs-lookup"><span data-stu-id="2bfba-150">Next, you will learn more about the rules and itemsets generated by the model for the Touring Tire and Touring Tire Tube products.</span></span> <span data-ttu-id="2bfba-151">[**專案集**] 索引標籤會顯示與關聯分析演算法所探索的專案集相關的三個重要資訊片段 [!INCLUDE[msCoName](../includes/msconame-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="2bfba-151">The **Itemsets** tab displays three important pieces of information that relate to the itemsets that the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm discovers:</span></span>  
  
-   <span data-ttu-id="2bfba-152">**支援：** 專案集發生所在的交易數目。</span><span class="sxs-lookup"><span data-stu-id="2bfba-152">**Support:** The number of transactions in which the itemset occurs.</span></span>  
  
-   <span data-ttu-id="2bfba-153">**大小：** 專案集內的專案數。</span><span class="sxs-lookup"><span data-stu-id="2bfba-153">**Size:** The number of items in the itemset.</span></span>  
  
-   <span data-ttu-id="2bfba-154">**專案：** 包含在每個專案集內的專案清單。</span><span class="sxs-lookup"><span data-stu-id="2bfba-154">**Items:** A list of the items included in each itemset.</span></span>  
  
 <span data-ttu-id="2bfba-155">演算法可能會產生許多項目集，這會因演算法參數的設定方式而不同。</span><span class="sxs-lookup"><span data-stu-id="2bfba-155">Depending on how the algorithm parameters are set, the algorithm might generate many itemsets.</span></span> <span data-ttu-id="2bfba-156">檢視器中傳回的每個項目集都代表已賣出此項目的交易。</span><span class="sxs-lookup"><span data-stu-id="2bfba-156">Each itemset that is returned in the viewer represents transactions in which the item was sold.</span></span> <span data-ttu-id="2bfba-157">藉由使用 [**專案集**] 索引標籤頂端的控制項，您可以篩選檢視器，只顯示包含指定之最低支援和專案集大小的專案集。</span><span class="sxs-lookup"><span data-stu-id="2bfba-157">By using the controls at the top of the **Itemsets** tab, you can filter the viewer to show only the itemsets that contain a specified minimum support and itemset size.</span></span>  
  
 <span data-ttu-id="2bfba-158">如果您正在使用不同的採礦模型，而且未列出任何項目集，這是因為沒有任何項目集符合演算法參數的準則。</span><span class="sxs-lookup"><span data-stu-id="2bfba-158">If you are working with a different mining model and no itemsets are listed, it is because no itemsets met the criteria of the algorithm parameters.</span></span> <span data-ttu-id="2bfba-159">在這類情況下，您可以變更演算法參數，允許具有較低支援的項目集。</span><span class="sxs-lookup"><span data-stu-id="2bfba-159">In such a scenario, you can change the algorithm parameters to allow itemsets that have lower support.</span></span>  
  
#### <a name="to-filter-the-itemsets-that-are-shown-in-the-viewer-by-name"></a><span data-ttu-id="2bfba-160">若要依名稱篩選檢視器中顯示的項目集</span><span class="sxs-lookup"><span data-stu-id="2bfba-160">To filter the itemsets that are shown in the viewer by name</span></span>  
  
1.  <span data-ttu-id="2bfba-161">按一下檢視器的 [**專案集**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2bfba-161">Click the **Itemsets** tab of the viewer.</span></span>  
  
2.  <span data-ttu-id="2bfba-162">在 [**篩選**專案集] 方塊中，輸入 `Touring Tire` ，然後按一下方塊外。</span><span class="sxs-lookup"><span data-stu-id="2bfba-162">In the **Filter Itemset** box, type `Touring Tire`, and then click outside the box.</span></span>  
  
     <span data-ttu-id="2bfba-163">此篩選會傳回包含這個字串的所有項目。</span><span class="sxs-lookup"><span data-stu-id="2bfba-163">The filter returns all items that contain this string.</span></span>  
  
3.  <span data-ttu-id="2bfba-164">在 [**顯示**] 清單中，選取 [**只顯示內容名稱**]。</span><span class="sxs-lookup"><span data-stu-id="2bfba-164">In the **Show** list, select **Show attribute name only**.</span></span>  
  
4.  <span data-ttu-id="2bfba-165">選取 [**顯示完整名稱**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2bfba-165">Select the **Show long name** check box.</span></span>  
  
     <span data-ttu-id="2bfba-166">項目集的清單會更新，僅顯示包含 Touring Tire 字串的項目集。</span><span class="sxs-lookup"><span data-stu-id="2bfba-166">The list of itemsets is updated to show only the itemsets that contain the string Touring Tire.</span></span> <span data-ttu-id="2bfba-167">項目集的完整名稱包括了內含每一個項目之屬性和值的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="2bfba-167">The long name of the itemset includes the name of the table that contains the attribute and value for each item.</span></span>  
  
5.  <span data-ttu-id="2bfba-168">清除 [**顯示完整名稱**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2bfba-168">Clear the **Show long name** check box.</span></span>  
  
     <span data-ttu-id="2bfba-169">項目集的清單會更新，僅顯示簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="2bfba-169">The list of itemsets is updated to show only the short name.</span></span>  
  
 <span data-ttu-id="2bfba-170">[**支援**] 資料行中的值表示每個專案集的交易數目。</span><span class="sxs-lookup"><span data-stu-id="2bfba-170">The values in the **Support** column indicate the number of transactions for each itemset.</span></span> <span data-ttu-id="2bfba-171">項目集的交易表示包含此項目集內所有項目的購買。</span><span class="sxs-lookup"><span data-stu-id="2bfba-171">A transaction for an itemset means a purchase that included all the items in the itemset.</span></span>  
  
 <span data-ttu-id="2bfba-172">根據預設，檢視器會依照支援的遞減順序列出項目集。</span><span class="sxs-lookup"><span data-stu-id="2bfba-172">By default, the viewer lists the itemsets in descending order by support.</span></span> <span data-ttu-id="2bfba-173">您可以按一下資料行標頭，依照不同的資料行排序，例如項目集大小或名稱。</span><span class="sxs-lookup"><span data-stu-id="2bfba-173">You can click on the column headers to sort by a different column, such as the itemset size or name.</span></span> <span data-ttu-id="2bfba-174">如果您有興趣進一步了解項目集內包含的個別交易，您可以從項目集鑽研到個別案例。</span><span class="sxs-lookup"><span data-stu-id="2bfba-174">If you are interested in learning more about the individual transactions that are included in an itemset, you can drill through from the itemsets to the individual cases.</span></span> <span data-ttu-id="2bfba-175">鑽研結果中的結構資料行是模型中未使用的客戶收入等級和客戶識別碼。</span><span class="sxs-lookup"><span data-stu-id="2bfba-175">The structure columns in the drillthrough results are the customer's income level and customer ID, which were not used in the model.</span></span>  
  
#### <a name="to-view-details-for-an-itemset"></a><span data-ttu-id="2bfba-176">若要檢視項目集的詳細資料</span><span class="sxs-lookup"><span data-stu-id="2bfba-176">To view details for an itemset</span></span>  
  
1.  <span data-ttu-id="2bfba-177">在專案集清單中，按一下 [專案集] 資料行**標題，依**名稱排序。</span><span class="sxs-lookup"><span data-stu-id="2bfba-177">In the list of itemsets, click the **Itemset** column heading to sort by name.</span></span>  
  
2.  <span data-ttu-id="2bfba-178">找出專案， `Touring Tire` (沒有第二個專案) 。</span><span class="sxs-lookup"><span data-stu-id="2bfba-178">Locate the item, `Touring Tire` (with no second item).</span></span>  
  
3.  <span data-ttu-id="2bfba-179">以滑鼠右鍵按一下專案， `Touring Tire` 選取 [ **Drill Through**向下切入]，然後選取 [**模型和結構資料行**]。</span><span class="sxs-lookup"><span data-stu-id="2bfba-179">Right-click the item, `Touring Tire`, select **Drill Through**, and then select **Model and Structure Columns**.</span></span>  
  
     <span data-ttu-id="2bfba-180">[**向下**切入] 對話方塊會顯示當做這個專案集支援使用的個別交易。</span><span class="sxs-lookup"><span data-stu-id="2bfba-180">The **Drill Through** dialog box displays the individual transactions used as support for this itemset.</span></span>  
  
4.  <span data-ttu-id="2bfba-181">展開巢狀資料表 vAssocSeqLineItems，檢視交易中的實際購買清單。</span><span class="sxs-lookup"><span data-stu-id="2bfba-181">Expand the nested table, vAssocSeqLineItems, to view the actual list of purchases in the transaction.</span></span>  
  
#### <a name="to-filter-itemsets-by-support-or-size"></a><span data-ttu-id="2bfba-182">若要依照支援或大小篩選項目集</span><span class="sxs-lookup"><span data-stu-id="2bfba-182">To filter itemsets by support or size</span></span>  
  
1.  <span data-ttu-id="2bfba-183">清除可能存在於 [**篩選**專案集] 方塊中的任何文字。</span><span class="sxs-lookup"><span data-stu-id="2bfba-183">Clear any text that might be in the **Filter Itemset** box.</span></span> <span data-ttu-id="2bfba-184">您無法將文字篩選與數值篩選一起使用。</span><span class="sxs-lookup"><span data-stu-id="2bfba-184">You cannot use a text filter together with a numeric filter.</span></span>  
  
2.  <span data-ttu-id="2bfba-185">在 [**最小支援**] 方塊中，輸入100，然後按一下檢視器的背景。</span><span class="sxs-lookup"><span data-stu-id="2bfba-185">In the **Minimum support** box, type 100, and then click the background of the viewer.</span></span>  
  
     <span data-ttu-id="2bfba-186">項目集的清單會更新，僅顯示支援至少為 100 的項目集。</span><span class="sxs-lookup"><span data-stu-id="2bfba-186">The list of itemsets is updated to show only itemsets with support of at least 100.</span></span>  
  
 [<span data-ttu-id="2bfba-187">回到頁首</span><span class="sxs-lookup"><span data-stu-id="2bfba-187">Back to Top</span></span>](#bkmk_DepNet)  
  
##  <a name="rules-tab"></a><a name="bkmk_Rules"></a><span data-ttu-id="2bfba-188">規則索引標籤</span><span class="sxs-lookup"><span data-stu-id="2bfba-188">Rules Tab</span></span>  
 <span data-ttu-id="2bfba-189">[**規則**] 索引標籤會顯示與演算法找到的規則相關的下列資訊。</span><span class="sxs-lookup"><span data-stu-id="2bfba-189">The **Rules** tab displays the following information that is related to the rules that the algorithm finds.</span></span>  
  
-   <span data-ttu-id="2bfba-190">機率 **：** 規則的*可能性*，定義為指定左側專案的右手邊專案機率。</span><span class="sxs-lookup"><span data-stu-id="2bfba-190">**Probability:** The *likelihood* of a rule, defined as the probability of the right-hand item given the left-hand side item.</span></span>  
  
-   <span data-ttu-id="2bfba-191">**重要性：** 規則實用性的量值。</span><span class="sxs-lookup"><span data-stu-id="2bfba-191">**Importance:** A measure of the usefulness of a rule.</span></span> <span data-ttu-id="2bfba-192">較大的值表示較好的規則。</span><span class="sxs-lookup"><span data-stu-id="2bfba-192">A greater value means a better rule.</span></span>  
  
     <span data-ttu-id="2bfba-193">提供重要性可幫助您測量規則的實用性，因為單獨使用機率可能會產生誤導。</span><span class="sxs-lookup"><span data-stu-id="2bfba-193">Importance is provided to help you gauge the usefulness of a rule, because probability alone can be misleading.</span></span> <span data-ttu-id="2bfba-194">例如，如果每筆交易都包含一個水壺 (或許將水壺當做促銷活動的贈品自動加入到每一個客戶的購物車內)，此模型會建立一個規則來預測水壺的機率為 1。</span><span class="sxs-lookup"><span data-stu-id="2bfba-194">For example, if every transaction contains a water bottle--perhaps the water bottle is added to each customer's cart automatically as part of a promotion--the model would create a rule predicting that water bottle has a probability of 1.</span></span> <span data-ttu-id="2bfba-195">如果這個規則只根據機率將會非常精確，但是無法提供實用的資訊。</span><span class="sxs-lookup"><span data-stu-id="2bfba-195">Based on probability alone, this rule is very accurate, but it does not provide useful information.</span></span>  
  
-   <span data-ttu-id="2bfba-196">**規則：** 規則的定義。</span><span class="sxs-lookup"><span data-stu-id="2bfba-196">**Rule:** The definition of the rule.</span></span> <span data-ttu-id="2bfba-197">若為購物籃模型，規則會描述特定的項目組合。</span><span class="sxs-lookup"><span data-stu-id="2bfba-197">For a market basket model, a rule describes a specific combination of items.</span></span>  
  
 <span data-ttu-id="2bfba-198">每項規則都可用來根據其他項目的出現情況，預測這個項目在交易中的出現狀況。</span><span class="sxs-lookup"><span data-stu-id="2bfba-198">Each rule can be used to predict the presence of an item in a transaction based on the presence of other items.</span></span> <span data-ttu-id="2bfba-199">就像在 [**專案集**] 索引標籤中，您可以篩選規則，只顯示最有趣的規則。</span><span class="sxs-lookup"><span data-stu-id="2bfba-199">Just like in the **Itemsets** tab, you can filter the rules so that only the most interesting rules are shown.</span></span> <span data-ttu-id="2bfba-200">如果您正在使用沒有任何規則的採礦模型，您可能會想要變更演算法參數，以降低規則的機率臨界值。</span><span class="sxs-lookup"><span data-stu-id="2bfba-200">If you are working with a mining model that does not have any rules, you might want to change the algorithm parameters to lower the probability threshold for rules.</span></span>  
  
#### <a name="to-see-only-rules-that-include-the-mountain-200-bicycle"></a><span data-ttu-id="2bfba-201">若要查看只包含 Mountain-200 自行車的規則</span><span class="sxs-lookup"><span data-stu-id="2bfba-201">To see only rules that include the Mountain-200 bicycle</span></span>  
  
1.  <span data-ttu-id="2bfba-202">在 [**採礦模型檢視器**] 索引標籤中，按一下 [**規則**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2bfba-202">In the **Mining Model Viewer** tab, click the **Rules** tab.</span></span>  
  
2.  <span data-ttu-id="2bfba-203">在 [**篩選規則**] 方塊中，輸入 `Mountain-200` 。</span><span class="sxs-lookup"><span data-stu-id="2bfba-203">In the **Filter Rule** box, enter `Mountain-200`.</span></span>  
  
     <span data-ttu-id="2bfba-204">清除 [**顯示完整名稱**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2bfba-204">Clear the **Show long name** check box.</span></span>  
  
3.  <span data-ttu-id="2bfba-205">從 [**顯示**] 清單中，選取 [**只顯示內容名稱**]。</span><span class="sxs-lookup"><span data-stu-id="2bfba-205">From the **Show** list, select **Show attribute name only**.</span></span>  
  
     <span data-ttu-id="2bfba-206">檢視器只會顯示包含 "" 這些字的規則 `Mountain-200` 。</span><span class="sxs-lookup"><span data-stu-id="2bfba-206">The viewer will then display only the rules that contain the words "`Mountain-200`".</span></span> <span data-ttu-id="2bfba-207">此規則的機率會告訴您，當有人購買 `Mountain-200` 自行車時，該人員也會購買另一個列出的產品。</span><span class="sxs-lookup"><span data-stu-id="2bfba-207">The probability of the rule tells you how likely it is that when someone buys a `Mountain-200` bicycle, that person will also buy the other listed product.</span></span>  
  
 <span data-ttu-id="2bfba-208">這些規則會依照機率的遞減順序排序，但是您可以按一下資料行標題來變更排序次序。</span><span class="sxs-lookup"><span data-stu-id="2bfba-208">The rules are ordered by probability in descending order, but you can click the column headings to change the sort order.</span></span> <span data-ttu-id="2bfba-209">如果您很有興趣了解特定規則的詳細資料，您可以使用鑽研來檢視支援的案例。</span><span class="sxs-lookup"><span data-stu-id="2bfba-209">If you are interested in finding out more details about a particular rule, you can use drillthrough to view the supporting cases.</span></span>  
  
#### <a name="to-view-cases-that-support-a-particular-rule"></a><span data-ttu-id="2bfba-210">若要檢視可支援特定規則的案例</span><span class="sxs-lookup"><span data-stu-id="2bfba-210">To view cases that support a particular rule</span></span>  
  
1.  <span data-ttu-id="2bfba-211">在 [**規則**] 索引標籤中，以滑鼠右鍵按一下您要查看的規則。</span><span class="sxs-lookup"><span data-stu-id="2bfba-211">In the **Rules** tab, right-click the rule that you want to view.</span></span>  
  
2.  <span data-ttu-id="2bfba-212">選取 [**向下切入**]，然後選取 [**僅模型資料行**] 或 [**模型和結構資料行**]。</span><span class="sxs-lookup"><span data-stu-id="2bfba-212">Select **Drill Through**, and then select **Model Columns Only**, or **Model and Structure Columns**.</span></span>  
  
     <span data-ttu-id="2bfba-213">[**向下**切入] 對話方塊會提供窗格頂端的規則摘要，以及用來作為規則支援資料的所有案例清單。</span><span class="sxs-lookup"><span data-stu-id="2bfba-213">The **Drill Through** dialog box provides a summary of the rule at the top of the pane, and a list of all cases that were used as supporting data for the rule.</span></span>  
  
 [<span data-ttu-id="2bfba-214">回到頁首</span><span class="sxs-lookup"><span data-stu-id="2bfba-214">Back to Top</span></span>](#bkmk_DepNet)  
  
##  <a name="generic-content-tree-viewer"></a><a name="bkmk_ContentViewer"></a><span data-ttu-id="2bfba-215">一般內容樹狀檢視器</span><span class="sxs-lookup"><span data-stu-id="2bfba-215">Generic Content Tree Viewer</span></span>  
 <span data-ttu-id="2bfba-216">此檢視器可用於所有模型，不論演算法或模型類型為何。</span><span class="sxs-lookup"><span data-stu-id="2bfba-216">This viewer can be used for all models, regardless of the algorithm or model type.</span></span> <span data-ttu-id="2bfba-217">[ **Microsoft 一般內容樹狀檢視器]** 可從 [**檢視器]** 下拉式清單中取得。</span><span class="sxs-lookup"><span data-stu-id="2bfba-217">The **Microsoft Generic Content Tree Viewer** is available from the **Viewer** drop-down list.</span></span>  
  
 <span data-ttu-id="2bfba-218">內容樹狀結構會將採礦模型表示為節點的序列，其中的每一個節點都表示所學習到有關某些資料集的知識。</span><span class="sxs-lookup"><span data-stu-id="2bfba-218">A content tree is a representation of a mining model as a series of nodes, where each node represents learned knowledge about some subset of the data.</span></span> <span data-ttu-id="2bfba-219">節點可以包含模式、一組規則、叢集，或是共用某些特性之日期範圍的定義。</span><span class="sxs-lookup"><span data-stu-id="2bfba-219">The node can contain a pattern, a set of rules, a cluster, or the definition of a range of dates that share some characteristics.</span></span> <span data-ttu-id="2bfba-220">節點的確切內容會因為演算法和可預測之屬性的類型而有所不同，但是內容的一般表示都是相同的。</span><span class="sxs-lookup"><span data-stu-id="2bfba-220">The exact content of the node differs depending on the algorithm and the type of the predictable attribute, but the general representation of the content is the same.</span></span> <span data-ttu-id="2bfba-221">您可以展開每一個節點，以查看詳細資料的遞增層級，並將任何節點的內容複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="2bfba-221">You can expand each node to see increasing levels of detail, and copy the content of any node to the Clipboard.</span></span>  
  
#### <a name="to-view-details-about-the-rule-by-using-the-content-viewer"></a><span data-ttu-id="2bfba-222">若要使用內容檢視器來檢視有關此規則的詳細資料</span><span class="sxs-lookup"><span data-stu-id="2bfba-222">To view details about the rule by using the content viewer</span></span>  
  
1.  <span data-ttu-id="2bfba-223">在 [**採礦模型檢視器**] 索引標籤中，從**檢視器**清單中選取 [ **Microsoft 一般內容樹狀檢視器**]。</span><span class="sxs-lookup"><span data-stu-id="2bfba-223">In the **Mining Model Viewer** tab, select **Microsoft Generic Content Tree Viewer** from the **Viewer** list.</span></span>  
  
2.  <span data-ttu-id="2bfba-224">在 [節點標題] 窗格中，捲動到清單的底部，然後按一下最後一個節點。</span><span class="sxs-lookup"><span data-stu-id="2bfba-224">In the Node Caption pane, scroll to the bottom of the list, and click the last node.</span></span>  
  
     <span data-ttu-id="2bfba-225">檢視器會先顯示項目集，接著再顯示規則，但是不會加以分組。</span><span class="sxs-lookup"><span data-stu-id="2bfba-225">The viewer shows itemsets first and rules next, but does not group them.</span></span> <span data-ttu-id="2bfba-226">有一個最簡單的方法可尋找特定節點，那就是建立內容查詢。</span><span class="sxs-lookup"><span data-stu-id="2bfba-226">The easiest way to find a specific node is to create a content query.</span></span> <span data-ttu-id="2bfba-227">如需詳細資訊，請參閱 [關聯模型查詢範例](../../2014/analysis-services/data-mining/association-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="2bfba-227">For more information, see [Association Model Query Examples](../../2014/analysis-services/data-mining/association-model-query-examples.md).</span></span>  
  
3.  <span data-ttu-id="2bfba-228">在 [節點詳細資料] 窗格中，檢閱 NODE_TYPE 和 NODE_DESCRIPTION 的值。</span><span class="sxs-lookup"><span data-stu-id="2bfba-228">In the Node Details pane, review the value for NODE_TYPE and NODE_DESCRIPTION.</span></span>  
  
     <span data-ttu-id="2bfba-229">節點類型 8 是一個規則，而節點類型 7 則是一個項目集。</span><span class="sxs-lookup"><span data-stu-id="2bfba-229">A node type of 8 is a rule, and a node type of 7 is an itemset.</span></span> <span data-ttu-id="2bfba-230">對於規則而言，NODE_DESCRIPTION 的值會告訴您組成此規則的條件。</span><span class="sxs-lookup"><span data-stu-id="2bfba-230">For a rule, the value of NODE_DESCRIPTION tells you the conditions that make up the rule.</span></span> <span data-ttu-id="2bfba-231">對於項目集而言，NODE_DESCRIPTION 的值會告訴您包含在此項目集中的項目。</span><span class="sxs-lookup"><span data-stu-id="2bfba-231">For an itemset, the value of NODE_DESCRIPTION tells you the items included in the itemset.</span></span>  
  
 <span data-ttu-id="2bfba-232">您也可以建立內容查詢，以取得有關規則的詳細統計資料。</span><span class="sxs-lookup"><span data-stu-id="2bfba-232">You can also create a content query to obtain detailed statistics about the rules.</span></span> <span data-ttu-id="2bfba-233">如需有關「採礦模型內容」和如何解讀的詳細資訊，請參閱[關聯模型的模型內容 &#40;Analysis Services 資料採礦&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="2bfba-233">For more information about mining model content and how to interpret it, see [Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md).</span></span>  
  
 [<span data-ttu-id="2bfba-234">回到頁首</span><span class="sxs-lookup"><span data-stu-id="2bfba-234">Back to Top</span></span>](#bkmk_DepNet)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="2bfba-235">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="2bfba-235">Next Task in Lesson</span></span>  
 [<span data-ttu-id="2bfba-236">&#40;中繼資料採礦教學課程來篩選模型中的嵌套資料表&#41;</span><span class="sxs-lookup"><span data-stu-id="2bfba-236">Filtering a Nested Table in a Mining Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="2bfba-237">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bfba-237">See Also</span></span>  
 <span data-ttu-id="2bfba-238">[第3課：建立購物籃案例 &#40;中繼資料採礦教學課程&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="2bfba-238">[Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md) </span></span>  
 <span data-ttu-id="2bfba-239">[第4課：建立時序群集案例 &#40;中繼資料採礦教學課程&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="2bfba-239">[Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md) </span></span>  
 <span data-ttu-id="2bfba-240">[Microsoft 關聯分析演算法](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="2bfba-240">[Microsoft Association Algorithm](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) </span></span>  
 [<span data-ttu-id="2bfba-241">Microsoft 關聯分析演算法技術參考</span><span class="sxs-lookup"><span data-stu-id="2bfba-241">Microsoft Association Algorithm Technical Reference</span></span>](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)  
  
  
