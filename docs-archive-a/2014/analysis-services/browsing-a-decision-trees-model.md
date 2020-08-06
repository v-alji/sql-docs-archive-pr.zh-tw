---
title: 流覽決策樹模型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- tree viewer
- mining model, decision tree
- decision tree [data mining]
- dependency network
ms.assetid: 6b3dd1ae-caff-41c3-817b-802dc020ff88
author: minewiskan
ms.author: owend
ms.openlocfilehash: 809d2e494cfa7a6c4078acf95c2c70a0e68c188d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593118"
---
# <a name="browsing-a-decision-trees-model"></a><span data-ttu-id="14ed8-102">瀏覽決策樹模型</span><span class="sxs-lookup"><span data-stu-id="14ed8-102">Browsing a Decision Trees Model</span></span>
  <span data-ttu-id="14ed8-103">當您使用 **[流覽]** 開啟分類模型時，該模型會顯示在互動式決策樹檢視器中，類似于 [!INCLUDE[msCoName](../includes/msconame-md.md)] 中的決策樹檢視器 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="14ed8-103">When you open a classification model using **Browse**, the model is displayed in an interactive decision tree viewer, similar to the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="14ed8-104">此檢視器會將分類的結果顯示成圖形，而這個圖形是設計來反白顯示區分不同資料群組的準則。</span><span class="sxs-lookup"><span data-stu-id="14ed8-104">The viewer displays the results of classification as a graph that is designed to highlight the criteria that differentiate one group of data from another.</span></span> <span data-ttu-id="14ed8-105">您也可以向下鑽研個別的樹狀結構子集，並且擷取基礎資料。</span><span class="sxs-lookup"><span data-stu-id="14ed8-105">You can also drill down into individual subsets of the tree and retrieve the underlying data.</span></span>  
  
##  <a name="explore-the-model"></a><a name="bkmk_Top"></a><span data-ttu-id="14ed8-106">探索模型</span><span class="sxs-lookup"><span data-stu-id="14ed8-106">Explore the Model</span></span>  
 <span data-ttu-id="14ed8-107">以決策樹演算法為基礎的模型具有許多有趣的資訊可探索。</span><span class="sxs-lookup"><span data-stu-id="14ed8-107">Models based on the Decision Trees algorithm have lots of interesting information to explore.</span></span> <span data-ttu-id="14ed8-108">[**流覽**] 視窗包含下列索引標籤和窗格，可協助您瞭解模式並使用圖表預測結果：</span><span class="sxs-lookup"><span data-stu-id="14ed8-108">The **Browse** window includes the following tabs and panes to help you learn the patterns and predict outcomes using the graph:</span></span>  
  
-   [<span data-ttu-id="14ed8-109">決策樹</span><span class="sxs-lookup"><span data-stu-id="14ed8-109">Decision Tree</span></span>](#BKMK_DecisionTree)  
  
-   [<span data-ttu-id="14ed8-110">相依性網路</span><span class="sxs-lookup"><span data-stu-id="14ed8-110">Dependency Network</span></span>](#BKMK_DNetwork)  
  
 <span data-ttu-id="14ed8-111">若要試驗決策樹模型，您可以使用範例資料活頁簿之 [定型資料] (或 [來源資料]) 索引標籤上的範例資料，然後使用 Bike Buyer 做為可預測的屬性，建立決策樹模型。</span><span class="sxs-lookup"><span data-stu-id="14ed8-111">To experiment with a decision trees model, you can use the sample data on the Training Data (or Source Data) tab of the sample data workbook, and build a decision tree model using Bike Buyer as the predictable attribute.</span></span>  
  
###  <a name="decision-tree"></a><a name="BKMK_DecisionTree"></a><span data-ttu-id="14ed8-112">決策樹</span><span class="sxs-lookup"><span data-stu-id="14ed8-112">Decision Tree</span></span>  
 <span data-ttu-id="14ed8-113">這個檢視是要協助您了解並探索導致結果的因數。</span><span class="sxs-lookup"><span data-stu-id="14ed8-113">This view is intended to help you understand and explore the factors that lead to an outcome.</span></span>  
  
 <span data-ttu-id="14ed8-114">您可以依照下列順序，由左至右讀取決策樹圖形：</span><span class="sxs-lookup"><span data-stu-id="14ed8-114">The decision tree graph can be read from left to right as follows:</span></span>  
  
-   <span data-ttu-id="14ed8-115">矩形（稱為「*節點*」）包含資料的子集。</span><span class="sxs-lookup"><span data-stu-id="14ed8-115">The rectangles, which are referred to as *nodes*, contain subsets of the data.</span></span> <span data-ttu-id="14ed8-116">節點上的標籤會告知您該子集的定義特性。</span><span class="sxs-lookup"><span data-stu-id="14ed8-116">The label on the node tells you the defining characteristics of that subset.</span></span>  
  
-   <span data-ttu-id="14ed8-117">最左邊的節點（標記為**All**）代表完整的資料集。</span><span class="sxs-lookup"><span data-stu-id="14ed8-117">The leftmost node, labeled **All**, represents the complete data set.</span></span> <span data-ttu-id="14ed8-118">所有後續節點都代表資料的子集。</span><span class="sxs-lookup"><span data-stu-id="14ed8-118">All subsequent nodes represent subsets of the data.</span></span>  
  
-   <span data-ttu-id="14ed8-119">決策樹包含許多*分割*，或將資料分歧成以屬性為基礎之多個集合的位置。</span><span class="sxs-lookup"><span data-stu-id="14ed8-119">A decision tree contains many *splits*, or places where the data diverges into multiple sets based on attributes.</span></span>  
  
     <span data-ttu-id="14ed8-120">例如，範例模型中的第一個分割會按照年齡將資料集分成三個群組。</span><span class="sxs-lookup"><span data-stu-id="14ed8-120">For example, the first split in the sample model divides the dataset into three groups by age.</span></span>  
  
-   <span data-ttu-id="14ed8-121">緊接在 [ **All** ] 節點後面的分割是最重要的，因為它會顯示分割此資料集的主要條件。</span><span class="sxs-lookup"><span data-stu-id="14ed8-121">The split immediately after the **All** node is most important because it shows the primary condition that divides this dataset.</span></span>  
  
     <span data-ttu-id="14ed8-122">其他分割出現在右邊。</span><span class="sxs-lookup"><span data-stu-id="14ed8-122">Additional splits occur to the right.</span></span> <span data-ttu-id="14ed8-123">因此，透過分析樹狀結構的不同區段，您就可以了解哪些屬性最能影響購買行為。</span><span class="sxs-lookup"><span data-stu-id="14ed8-123">Thus, by analyzing different segments of the tree, you can learn which attributes had the most influence on purchasing behavior.</span></span>  
  
 <span data-ttu-id="14ed8-124">![關聯模型的相依性網路圖表](media/dm13-dec-tree-split-definition.gif "關聯模型的相依性網路圖表")</span><span class="sxs-lookup"><span data-stu-id="14ed8-124">![Dependency network graph for an association model](media/dm13-dec-tree-split-definition.gif "Dependency network graph for an association model")</span></span>  
  
 <span data-ttu-id="14ed8-125">利用這項資訊，您可以將行銷活動的對象鎖定在只需要鼓勵購買的客戶上。</span><span class="sxs-lookup"><span data-stu-id="14ed8-125">Using this information, you might focus a marketing campaign on customers that might simply need encouragement to make a purchase.</span></span>  
  
##### <a name="explore-the-decision-tree"></a><span data-ttu-id="14ed8-126">探索決策樹</span><span class="sxs-lookup"><span data-stu-id="14ed8-126">Explore the decision tree</span></span>  
  
1.  <span data-ttu-id="14ed8-127">按一下 [**全部**] 節點，並查看 [**挖掘圖例**]。</span><span class="sxs-lookup"><span data-stu-id="14ed8-127">Click the **All** node, and look at the **Mining Legend**.</span></span>  
  
     <span data-ttu-id="14ed8-128">它會顯示定型資料集中的確切案例計數，以及細分結果。</span><span class="sxs-lookup"><span data-stu-id="14ed8-128">It displays the exact count of cases in the training data set, as well as a breakdown of the outcomes.</span></span>  
  
     <span data-ttu-id="14ed8-129">如果您將滑鼠游標暫時放在節點上，也可以在工具提示中檢視相同的資訊。</span><span class="sxs-lookup"><span data-stu-id="14ed8-129">You can view the same information in a tooltip if you pause the mouse over a node.</span></span>  
  
2.  <span data-ttu-id="14ed8-130">按一下每個節點旁邊的加號和減號，即可展開或摺疊樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="14ed8-130">Click the plus and minus signs next to each node to expand or collapse the tree.</span></span>  
  
     <span data-ttu-id="14ed8-131">您也可以使用 [**顯示層級**] 滑杆來展開或縮小樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="14ed8-131">You can also use the **Show Level** slider to expand or shrink the tree.</span></span>  
  
3.  <span data-ttu-id="14ed8-132">您是否發現某些節點的色彩比其他節點要深？</span><span class="sxs-lookup"><span data-stu-id="14ed8-132">Notice that some nodes are darker than others?</span></span>  
  
     <span data-ttu-id="14ed8-133">根據預設，**填入**會當做陰影變數使用，這表示色彩的濃度會顯示哪些節點具有最大的支援。</span><span class="sxs-lookup"><span data-stu-id="14ed8-133">By default, **Population** is used as the shading variable, which means that the intensity of the color shows you which nodes have the most support.</span></span>  
  
     <span data-ttu-id="14ed8-134">因此，最左邊的節點色彩最深，因為它包含整個資料集。</span><span class="sxs-lookup"><span data-stu-id="14ed8-134">Therefore the leftmost node is darkest, because it contains the entire dataset.</span></span>  
  
4.  <span data-ttu-id="14ed8-135">將 [**背景**] 的值從 [**所有案例**] 變更為 **[是]**。</span><span class="sxs-lookup"><span data-stu-id="14ed8-135">Change the value for **Background** from **All Cases** to **Yes**.</span></span>  
  
     <span data-ttu-id="14ed8-136">![變更決策樹圖表以醒目提示購買者](media/dm13-dectreeshadedbuyer.gif "變更決策樹圖表以醒目提示購買者")</span><span class="sxs-lookup"><span data-stu-id="14ed8-136">![changing decision tree graph to highlight buyers](media/dm13-dectreeshadedbuyer.gif "changing decision tree graph to highlight buyers")</span></span>  
  
5.  <span data-ttu-id="14ed8-137">現在，色彩的濃度會告知您每個節點中購買自行車的客戶數目，而這就是您感興趣的行為。</span><span class="sxs-lookup"><span data-stu-id="14ed8-137">Now the intensity of the color tells you how many customers in each node purchased a bike, which is the behavior you are interested in.</span></span>  
  
     <span data-ttu-id="14ed8-138">請注意每個節點中的彩色列。</span><span class="sxs-lookup"><span data-stu-id="14ed8-138">Notice the colored bars within each node.</span></span> <span data-ttu-id="14ed8-139">這個長條圖會顯示這個資料子集內結果的分佈。</span><span class="sxs-lookup"><span data-stu-id="14ed8-139">This is a histogram that shows the distribution of outcomes within this subset of data.</span></span> <span data-ttu-id="14ed8-140">例如，在範例自行車購買者決策樹中，彩色橫條會顯示購買自行車 (Yes 值的客戶比例，) 與未 (任何值的使用者) 。</span><span class="sxs-lookup"><span data-stu-id="14ed8-140">For example, in the sample Bike Buyer decision tree, the colored bar shows the proportion of customers who bought bikes (Yes values) vs. those who did not (No values).</span></span> <span data-ttu-id="14ed8-141">若要取得確切的值，您可以按一下節點，並查看 [**挖掘圖例**]。</span><span class="sxs-lookup"><span data-stu-id="14ed8-141">To get the exact values, you can click the node and view the **Mining Legend**.</span></span>  
  
6.  <span data-ttu-id="14ed8-142">透過瀏覽圖形，您就可以了解每個資料子集如何進一步分解成更小的群組，以及哪些屬性對於預測結果最有用。</span><span class="sxs-lookup"><span data-stu-id="14ed8-142">By following the graph, you can see how each subset of data is further decomposed into smaller groups, and which attributes are most useful in predicting an outcome.</span></span>  
  
     <span data-ttu-id="14ed8-143">只要查看陰影的濃度，您就可以將重點放在一些感興趣的群組上，並且取得這些群組的詳細資料以進行比較。</span><span class="sxs-lookup"><span data-stu-id="14ed8-143">Just by looking at the intensity of the shading, you can focus on a couple groups of interest, and get more detailed data on them for comparison.</span></span> <span data-ttu-id="14ed8-144">例如，下列群組購買自行車的機率相當高：</span><span class="sxs-lookup"><span data-stu-id="14ed8-144">For example, these groups have a fairly high probability of buying bikes:</span></span>  
  
    -   <span data-ttu-id="14ed8-145">年齡 >= 32， \< 53 and Yearly Income > = 26000，子系 = 0</span><span class="sxs-lookup"><span data-stu-id="14ed8-145">Age >= 32 and \< 53 and Yearly Income >= 26000 and Children = 0</span></span>  
  
         <span data-ttu-id="14ed8-146">總案例數：1150</span><span class="sxs-lookup"><span data-stu-id="14ed8-146">Total cases: 1150</span></span>  
  
         <span data-ttu-id="14ed8-147">自行車購買者機率：18%</span><span class="sxs-lookup"><span data-stu-id="14ed8-147">Bike buyer probability: 18%</span></span>  
  
    -   <span data-ttu-id="14ed8-148">年齡 >= 32， \< 53 and Yearly Income > = 26000，子系不 = 0 且婚姻狀態 = ' Single '</span><span class="sxs-lookup"><span data-stu-id="14ed8-148">Age >= 32 and \< 53 and Yearly Income >= 26000 and Children not = 0 and Marital Status = 'Single'</span></span>  
  
         <span data-ttu-id="14ed8-149">案例總計：402</span><span class="sxs-lookup"><span data-stu-id="14ed8-149">Total cases: 402</span></span>  
  
         <span data-ttu-id="14ed8-150">自行車購買者機率：16%</span><span class="sxs-lookup"><span data-stu-id="14ed8-150">Bike buyer probability: 16%</span></span>  
  
7.  <span data-ttu-id="14ed8-151">將 [**背景**] 的值從 **[是]** 變更為 [**否**]，並查看圖形的變更方式。</span><span class="sxs-lookup"><span data-stu-id="14ed8-151">Change the value for **Background** from **Yes** to **No** and see how the graph changes.</span></span>  
  
     <span data-ttu-id="14ed8-152">![關聯模型的相依性網路圖表](media/dm13-dec-tree-background-no.gif "關聯模型的相依性網路圖表")</span><span class="sxs-lookup"><span data-stu-id="14ed8-152">![Dependency network graph for an association model](media/dm13-dec-tree-background-no.gif "Dependency network graph for an association model")</span></span>  
  
 <span data-ttu-id="14ed8-153">**提示**</span><span class="sxs-lookup"><span data-stu-id="14ed8-153">**Tips**</span></span>  
  
-   <span data-ttu-id="14ed8-154">如果您的資料可以分成多個數列，系統就會針對您想要建立模型的每組資料建立不同的模型。</span><span class="sxs-lookup"><span data-stu-id="14ed8-154">If your data can be divided into multiple series, a different model is built for each set of data that you want to model.</span></span>  
  
-   <span data-ttu-id="14ed8-155">在範例資料模型中，只有一個可預測的結果-自行車購買者，但假設您有客戶購買服務方案的相關資訊，而且也想要預測該情況。</span><span class="sxs-lookup"><span data-stu-id="14ed8-155">In the sample data model, there is only one predictable outcome - Bike Buyer - but suppose you had information about whether the customer purchased a service plan and wanted to predict that as well.</span></span> <span data-ttu-id="14ed8-156">在該情況下，您會將這些資料放入不同的資料行，並且在模型中加入兩個可預測的屬性。</span><span class="sxs-lookup"><span data-stu-id="14ed8-156">In that case you would have that data in a separate column, and include two predictable attributes in the model.</span></span>  
  
     <span data-ttu-id="14ed8-157">按一下 [決策樹] 窗格左上角的 [**長條圖**] 選項，以變更樹狀目錄中可顯示的最大狀態數目。</span><span class="sxs-lookup"><span data-stu-id="14ed8-157">Click the **Histogram** option, in the upper left corner of the Decision Tree pane, to change the maximum number of states that can appear in the histograms in the tree.</span></span> <span data-ttu-id="14ed8-158">如果可預測屬性有許多狀態，則此選項很有用。</span><span class="sxs-lookup"><span data-stu-id="14ed8-158">This is useful if the predictable attribute has many states.</span></span> <span data-ttu-id="14ed8-159">狀態會以長條圖形式出現，依常用程度從左到右排序。</span><span class="sxs-lookup"><span data-stu-id="14ed8-159">The states appear in a histogram in order of popularity from left to right.</span></span>  
  
-   <span data-ttu-id="14ed8-160">您也可以使用 [**決策樹**] 索引標籤上的選項來影響樹狀結構的顯示方式、放大或縮小，或調整圖形大小以符合視窗。</span><span class="sxs-lookup"><span data-stu-id="14ed8-160">You can also use the options on the **Decision Tree** tab to affect how the tree is displayed, by zooming in or out, or sizing the graph to fit the window.</span></span>  
  
-   <span data-ttu-id="14ed8-161">使用 **[預設展開]** ，來設定模型中所有樹狀結構所顯示的預設層級數目。</span><span class="sxs-lookup"><span data-stu-id="14ed8-161">Use **Default Expansion** to set the default number of levels that are displayed for all trees in the model.</span></span>  
  
-   <span data-ttu-id="14ed8-162">選取 [**顯示完整名稱**] 以顯示內容的完整名稱，包括資料來源。</span><span class="sxs-lookup"><span data-stu-id="14ed8-162">Select **Show long name** to display the full name of the attribute, including the data source.</span></span> <span data-ttu-id="14ed8-163">除非您的案例所取自的資料來源與每一個案例的屬性不同，否則簡短名稱和完整名稱會是相同的。</span><span class="sxs-lookup"><span data-stu-id="14ed8-163">Short names and long names are the same unless your cases are obtained from a different data source than the attributes for each case.</span></span>  
  
 [<span data-ttu-id="14ed8-164">回到頁首</span><span class="sxs-lookup"><span data-stu-id="14ed8-164">Back To Top</span></span>](#bkmk_Top)  
  
###  <a name="dependency-network"></a><a name="BKMK_DNetwork"></a><span data-ttu-id="14ed8-165">相依性網路</span><span class="sxs-lookup"><span data-stu-id="14ed8-165">Dependency Network</span></span>  
 <span data-ttu-id="14ed8-166">[相依性**網路**] 視圖會顯示模型中的輸入屬性和可預測屬性之間的連接。</span><span class="sxs-lookup"><span data-stu-id="14ed8-166">The **Dependency Network** view displays the connections between the input attributes and the predictable attributes in the model.</span></span>  
  
1.  <span data-ttu-id="14ed8-167">按一下並拖曳檢視器左側的滑動軸。</span><span class="sxs-lookup"><span data-stu-id="14ed8-167">Click and drag the slider at the left of the viewer</span></span>  
  
     <span data-ttu-id="14ed8-168">在頂端位置時，系統會顯示所有連接。</span><span class="sxs-lookup"><span data-stu-id="14ed8-168">At the top position, all connections are shown.</span></span> <span data-ttu-id="14ed8-169">當您向下拖曳滑動軸時，檢視器中只會顯示最強的連結。</span><span class="sxs-lookup"><span data-stu-id="14ed8-169">When you drag the slider down, only the strongest links are shown in the viewer.</span></span>  
  
2.  <span data-ttu-id="14ed8-170">現在，請按一下 [Bike Buyer] 節點。</span><span class="sxs-lookup"><span data-stu-id="14ed8-170">Now click the Bike Buyer node.</span></span>  
  
     <span data-ttu-id="14ed8-171">![決策樹的相依性網路檢視](media/dm13-dectree-depnet.gif "決策樹的相依性網路檢視")</span><span class="sxs-lookup"><span data-stu-id="14ed8-171">![Dependency network view for decision trees](media/dm13-dectree-depnet.gif "Dependency network view for decision trees")</span></span>  
  
     <span data-ttu-id="14ed8-172">當您選取節點時，檢視器會反白顯示該節點特定的相依性。</span><span class="sxs-lookup"><span data-stu-id="14ed8-172">When you select a node, the viewer highlights the dependencies that are specific to the node.</span></span> <span data-ttu-id="14ed8-173">在此情況下，檢視器會反白顯示有助於預測結果的每個節點。</span><span class="sxs-lookup"><span data-stu-id="14ed8-173">In this case, the viewer highlights each node that helps predict the outcome.</span></span>  
  
3.  <span data-ttu-id="14ed8-174">如果檢視器包含許多節點，您可以使用 [**尋找節點**] 按鈕來搜尋特定節點。</span><span class="sxs-lookup"><span data-stu-id="14ed8-174">If the viewer contains many nodes, you can search for specific nodes by using the **Find Node** button.</span></span> <span data-ttu-id="14ed8-175">按一下 **[尋找節點]** 就會開啟 **[尋找節點]** 對話方塊，您可以在此使用篩選來搜尋和選取特定節點。</span><span class="sxs-lookup"><span data-stu-id="14ed8-175">Clicking **Find Node** opens the **Find Node** dialog box, in which you can use a filter to search for and select specific nodes.</span></span>  
  
4.  <span data-ttu-id="14ed8-176">檢視器底端的圖例會將色碼連結至圖表中的相依性類型。</span><span class="sxs-lookup"><span data-stu-id="14ed8-176">The legend at the bottom of the viewer links color codes to the type of dependency in the graph.</span></span> <span data-ttu-id="14ed8-177">例如，當您選取可預測的節點時，可預測節點會呈現淺粉藍色陰影，而預測所選取之節點的節點則會呈現橙色陰影。</span><span class="sxs-lookup"><span data-stu-id="14ed8-177">For example, when you select a predictable node, the predictable node is shaded turquoise, and the nodes that predict the selected node are shaded orange.</span></span>  
  
 [<span data-ttu-id="14ed8-178">回到頁首</span><span class="sxs-lookup"><span data-stu-id="14ed8-178">Back To Top</span></span>](#bkmk_Top)  
  
### <a name="drill-through-to-underlying-data"></a><span data-ttu-id="14ed8-179">鑽研到基礎資料</span><span class="sxs-lookup"><span data-stu-id="14ed8-179">Drill through to Underlying Data</span></span>  
 <span data-ttu-id="14ed8-180">有數種類型的模型*支援從模型切入到基礎*案例資料的能力。</span><span class="sxs-lookup"><span data-stu-id="14ed8-180">Several types of models support the ability to *drill through* from the model to the underlying case data.</span></span> <span data-ttu-id="14ed8-181">如果您想要觸及特定客群的客戶，或是提取資料以執行進一步分析，這項功能可能非常有用。</span><span class="sxs-lookup"><span data-stu-id="14ed8-181">This can be very useful if you want to contact customers in a particular segment or pull out the data to perform further analysis.</span></span>  
  
##### <a name="get-case-data"></a><span data-ttu-id="14ed8-182">取得案例資料</span><span class="sxs-lookup"><span data-stu-id="14ed8-182">Get case data</span></span>  
  
1.  <span data-ttu-id="14ed8-183">以滑鼠右鍵按一下樹狀結構中包含所需資料的節點，然後選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="14ed8-183">Right-click the node in the tree that contains the desired data and select one of these options:</span></span>  
  
    -   <span data-ttu-id="14ed8-184">**深入瞭解模型**。</span><span class="sxs-lookup"><span data-stu-id="14ed8-184">**Drill Through Model**.</span></span> <span data-ttu-id="14ed8-185">這個選項會取得屬於選取之節點的案例，並且將它們儲存至 Excel 中的資料表。</span><span class="sxs-lookup"><span data-stu-id="14ed8-185">This option gets the cases that belong to the selected node, and saves them to a table in Excel.</span></span> <span data-ttu-id="14ed8-186">您只會取得實際用於建立模型的資料行。</span><span class="sxs-lookup"><span data-stu-id="14ed8-186">You get back only the columns of data that were actually used in building the model.</span></span>  
  
    -   <span data-ttu-id="14ed8-187">**逐一查看結構資料行**。</span><span class="sxs-lookup"><span data-stu-id="14ed8-187">**Drill Through Structure Columns**.</span></span> <span data-ttu-id="14ed8-188">這個選項會取得屬於選取之節點的案例，並且將它們儲存至 Excel 中的資料表。</span><span class="sxs-lookup"><span data-stu-id="14ed8-188">This option gets the cases that belong to the selected node, and saves them to a table in Excel.</span></span> <span data-ttu-id="14ed8-189">當您建立基礎資料時，您會取得其所提供的所有資訊，甚至是模型中未使用的資料行。</span><span class="sxs-lookup"><span data-stu-id="14ed8-189">You get all information that was available in the underlying data when you built it, even of a column wasn't used in the model.</span></span> <span data-ttu-id="14ed8-190">例如，您可能已經排除客戶地址和郵遞區號，因為這些欄位不適用於分析，但仍然保留在結構中。</span><span class="sxs-lookup"><span data-stu-id="14ed8-190">For example, you might have excluded the customer address and zip code because those fields are not useful with analysis, but left them in the structure.</span></span>  
  
     <span data-ttu-id="14ed8-191">返回 Excel 以檢視您的資料。</span><span class="sxs-lookup"><span data-stu-id="14ed8-191">Return to Excel to view your data.</span></span> <span data-ttu-id="14ed8-192">[瀏覽] 檢視器會執行查詢、將資料儲存至新工作表中的資料表，並且標示結果。</span><span class="sxs-lookup"><span data-stu-id="14ed8-192">The Browse viewer runs a query, saves the data to a table in a new worksheet, and labels the results.</span></span>  
  
     <span data-ttu-id="14ed8-193">![鑽研結果已儲存到 Excel](media/dm13-dectree-drillthroughresults.gif "鑽研結果已儲存到 Excel")</span><span class="sxs-lookup"><span data-stu-id="14ed8-193">![results of drillthrough are saved to Excel](media/dm13-dectree-drillthroughresults.gif "results of drillthrough are saved to Excel")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14ed8-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14ed8-194">See Also</span></span>  
 [<span data-ttu-id="14ed8-195">在 Excel 中流覽模型 &#40;SQL Server 資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="14ed8-195">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
