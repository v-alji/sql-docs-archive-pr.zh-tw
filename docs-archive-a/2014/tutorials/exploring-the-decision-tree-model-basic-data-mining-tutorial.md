---
title: 流覽決策樹模型 (基本資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2e1472c2-3f3e-4dae-acb3-62fca374d397
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a2c7f063d7cb73cdc431fb1bc94188c9266c10c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703553"
---
# <a name="exploring-the-decision-tree-model-basic-data-mining-tutorial"></a><span data-ttu-id="df33c-102">瀏覽決策樹模型 (基本資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="df33c-102">Exploring the Decision Tree Model (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="df33c-103">[!INCLUDE[msCoName](../includes/msconame-md.md)] 決策樹演算法會根據定型集中的其餘資料行，預測哪些資料行影響了自行車的購買決策。</span><span class="sxs-lookup"><span data-stu-id="df33c-103">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm predicts which columns influence the decision to purchase a bike based upon the remaining columns in the training set.</span></span>  
  

  
##  <a name="decision-tree-tab"></a><a name="Decision_Tree_Tab"></a><span data-ttu-id="df33c-104">決策樹索引標籤</span><span class="sxs-lookup"><span data-stu-id="df33c-104">Decision Tree Tab</span></span>  
 <span data-ttu-id="df33c-105">在 [**決策樹**] 索引標籤上，您可以針對資料集內的每個可預測屬性來查看決策樹。</span><span class="sxs-lookup"><span data-stu-id="df33c-105">On the **Decision Tree** tab, you can view decision trees for every predictable attribute in the dataset.</span></span>  
  
 <span data-ttu-id="df33c-106">在此情況下，此模型只會預測一個資料行 [自行車購買者]，因此只會顯示一個樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="df33c-106">In this case, the model predicts only one column, Bike Buyer, so there is only one tree to view.</span></span> <span data-ttu-id="df33c-107">如果有更多樹狀結構，您可以使用 [**樹狀結構**] 方塊來選擇另一個樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="df33c-107">If there were more trees, you could use the **Tree** box to choose another tree.</span></span>  
  
 <span data-ttu-id="df33c-108">當您 `TM_Decision_Tree` 在決策樹檢視器中查看模型時，您可以在圖表的左側看到最重要的屬性。</span><span class="sxs-lookup"><span data-stu-id="df33c-108">As you view the `TM_Decision_Tree` model in the Decision Tree viewer, you can see the most important attributes at the left side of the chart.</span></span> <span data-ttu-id="df33c-109">「最重要」表示這些屬性對結果的影響最大。</span><span class="sxs-lookup"><span data-stu-id="df33c-109">"Most important" means that these attributes have the greatest influence on the outcome.</span></span> <span data-ttu-id="df33c-110">沿著樹狀結構 (位於圖表右側) 愈往下的屬性其影響愈小。</span><span class="sxs-lookup"><span data-stu-id="df33c-110">Attributes further down the tree (to the right of the chart) have less of an effect.</span></span>  
  
 <span data-ttu-id="df33c-111">在此範例中，年齡是預測自行車購買行為時最重要的一項因素。</span><span class="sxs-lookup"><span data-stu-id="df33c-111">In this example, age is the single most important factor in predicting bike buying.</span></span> <span data-ttu-id="df33c-112">模型會依年齡將客戶分組，然後顯示每個年齡群組的下一個最重要屬性。</span><span class="sxs-lookup"><span data-stu-id="df33c-112">The model groups customers by age, and then shows the next more important attribute for each age group.</span></span> <span data-ttu-id="df33c-113">例如，就客戶年齡層在 34 歲到 40 歲的群組來說，擁有車輛數是排在年齡後面的最強預測指標。</span><span class="sxs-lookup"><span data-stu-id="df33c-113">For example, in the group of customers aged 34 to 40, the number of cars owned is the strongest predictor after age.</span></span>  
  
#### <a name="to-explore-the-model-in-the-decision-tree-tab"></a><span data-ttu-id="df33c-114">若要在決策樹索引標籤中瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="df33c-114">To explore the model in the Decision Tree tab</span></span>  
  
1.  <span data-ttu-id="df33c-115">在 [**資料採礦設計師**] 中選取 [**採礦模型檢視器**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="df33c-115">Select the **Mining Model Viewer** tab in **Data Mining Designer**.</span></span>  
  
     <span data-ttu-id="df33c-116">根據預設，設計工具會開啟至已加入結構的第一個模型，在此案例中為 `TM_Decision_Tree` 。</span><span class="sxs-lookup"><span data-stu-id="df33c-116">By default, the designer opens to the first model that was added to the structure -- in this case, `TM_Decision_Tree`.</span></span>  
  
2.  <span data-ttu-id="df33c-117">使用放大鏡按鈕調整樹狀結構顯示大小。</span><span class="sxs-lookup"><span data-stu-id="df33c-117">Use the magnifying glass buttons to adjust the size of the tree display.</span></span>  
  
     <span data-ttu-id="df33c-118">依預設，[!INCLUDE[msCoName](../includes/msconame-md.md)] 樹狀檢視器只顯示樹狀結構的前 3 個層級。</span><span class="sxs-lookup"><span data-stu-id="df33c-118">By default, the [!INCLUDE[msCoName](../includes/msconame-md.md)] Tree Viewer shows only the first three levels of the tree.</span></span> <span data-ttu-id="df33c-119">如果樹狀結構的層級不到 3 個，則檢視器只顯示現有的層級。</span><span class="sxs-lookup"><span data-stu-id="df33c-119">If the tree contains fewer than three levels, the viewer shows only the existing levels.</span></span> <span data-ttu-id="df33c-120">您可以使用 [**顯示層級**] 滑杆或**預設的展開**清單來查看更多層級。</span><span class="sxs-lookup"><span data-stu-id="df33c-120">You can view more levels by using the **Show Level** slider or the **Default Expansion** list.</span></span>  
  
3.  <span data-ttu-id="df33c-121">將幻燈片**放映層級**投影到第四個橫條。</span><span class="sxs-lookup"><span data-stu-id="df33c-121">Slide **Show Level** to the fourth bar.</span></span>  
  
4.  <span data-ttu-id="df33c-122">將 [**背景**] 值變更為 `1` 。</span><span class="sxs-lookup"><span data-stu-id="df33c-122">Change the **Background** value to `1`.</span></span>  
  
     <span data-ttu-id="df33c-123">藉由變更 [**背景**] 設定，您可以快速查看每個節點中的案例數目，其目標值 `1` 為 [自行車買方]。</span><span class="sxs-lookup"><span data-stu-id="df33c-123">By changing the **Background** setting, you can quickly see the number of cases in each node that have the target value of `1` for [Bike Buyer].</span></span> <span data-ttu-id="df33c-124">請記住，在這個特定案例中，每個案例都代表一個客戶。</span><span class="sxs-lookup"><span data-stu-id="df33c-124">Remember that in this particular scenario, each case represents a customer.</span></span> <span data-ttu-id="df33c-125">此值 `1` 表示客戶先前已購買自行車; 值**0**表示客戶尚未購買自行車。</span><span class="sxs-lookup"><span data-stu-id="df33c-125">The value `1` indicates that the customer previously purchased a bike; the value **0** indicates that the customer has not purchased a bike.</span></span> <span data-ttu-id="df33c-126">節點的陰影愈深，表示節點中擁有目標值的案例百分比愈高。</span><span class="sxs-lookup"><span data-stu-id="df33c-126">The darker the shading of the node, the higher the percentage of cases in the node that have the target value.</span></span>  
  
5.  <span data-ttu-id="df33c-127">將游標放在標示為 [**全部**] 的節點上。</span><span class="sxs-lookup"><span data-stu-id="df33c-127">Place your cursor over the node labeled **All**.</span></span> <span data-ttu-id="df33c-128">隨即出現工具提示，顯示下列資訊：</span><span class="sxs-lookup"><span data-stu-id="df33c-128">An tooltip will display the following information:</span></span>  
  
    -   <span data-ttu-id="df33c-129">案例總數</span><span class="sxs-lookup"><span data-stu-id="df33c-129">Total number of cases</span></span>  
  
    -   <span data-ttu-id="df33c-130">非自行車購買者的案例數目</span><span class="sxs-lookup"><span data-stu-id="df33c-130">Number of non bike buyer cases</span></span>  
  
    -   <span data-ttu-id="df33c-131">自行車購買者的案例數目</span><span class="sxs-lookup"><span data-stu-id="df33c-131">Number of bike buyer cases</span></span>  
  
    -   <span data-ttu-id="df33c-132">遺漏 [Bike Buyer] 值的案例數目</span><span class="sxs-lookup"><span data-stu-id="df33c-132">Number of cases with missing values for [Bike Buyer]</span></span>  
  
     <span data-ttu-id="df33c-133">或者，將滑鼠游標放在樹狀結構其中任何一個節點上方，查看從前一個節點到達該節點所需的條件。</span><span class="sxs-lookup"><span data-stu-id="df33c-133">Alternately, place your cursor over any node in the tree to see the condition that is required to reach that node from the node that comes before it.</span></span> <span data-ttu-id="df33c-134">您也可以在 [**挖掘圖例**] 中查看這項相同的資訊。</span><span class="sxs-lookup"><span data-stu-id="df33c-134">You can also view this same information in the **Mining Legend**.</span></span>  
  
6.  <span data-ttu-id="df33c-135">按一下 [**年齡 >= 34] 和 [< 41**] 的節點。</span><span class="sxs-lookup"><span data-stu-id="df33c-135">Click on the node for **Age >=34 and < 41**.</span></span> <span data-ttu-id="df33c-136">其長條圖會顯示為一個橫跨節點的細長水平橫條，並表示在此年齡範圍中，已購買 (粉紅色) 或未購買 (藍色) 自行車的客戶分佈狀況。</span><span class="sxs-lookup"><span data-stu-id="df33c-136">The histogram is displayed as a thin horizontal bar across the node and represents the distribution of customers in this age range who previously did (pink) and did not (blue) purchase a bike.</span></span> <span data-ttu-id="df33c-137">檢視器顯示出年齡介於 34 到 40，只有一台車子或沒有車子的客戶有可能購買自行車。</span><span class="sxs-lookup"><span data-stu-id="df33c-137">The Viewer shows us that customers between the ages of 34 and 40 with one or no cars are likely to purchase a bike.</span></span> <span data-ttu-id="df33c-138">再進一步研究，我們可以發現如果客戶年齡落在 38 到 40 歲，購買自行車的可能性又更高。</span><span class="sxs-lookup"><span data-stu-id="df33c-138">Taking it one step further, we find that the likelihood to purchase a bike increases if the customer is actually age 38 to 40.</span></span>  
  
 <span data-ttu-id="df33c-139">由於您在建立結構和模型時已啟用鑽研，因此您可以從模型案例和採礦結構中擷取詳細資訊，包括未包含在採礦模型中的資料行 (例如 emailAddress 和 FirstName)。</span><span class="sxs-lookup"><span data-stu-id="df33c-139">Because you enabled drillthrough when you created the structure and model, you can retrieve detailed information from the model cases and mining structure, including those columns that were not included in the mining model (e.g., emailAddress, FirstName).</span></span>  
  
 <span data-ttu-id="df33c-140">如需詳細資訊，請參閱 [鑽研查詢 &#40;資料採礦&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="df33c-140">For more information, see [Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).</span></span>  
  
#### <a name="to-drill-through-to-case-data"></a><span data-ttu-id="df33c-141">若要鑽研案例資料</span><span class="sxs-lookup"><span data-stu-id="df33c-141">To drill through to case data</span></span>  
  
1.  <span data-ttu-id="df33c-142">以滑鼠右鍵按一下節點，然後選取 [僅**深入流覽**] 和 [**僅模型資料行**]。</span><span class="sxs-lookup"><span data-stu-id="df33c-142">Right-click a node, and select **Drill Through** then **Model Columns Only**.</span></span>  
  
     <span data-ttu-id="df33c-143">各定型案例的詳細資訊會以試算表格式顯示。</span><span class="sxs-lookup"><span data-stu-id="df33c-143">The details for each training case are displayed in spreadsheet format.</span></span> <span data-ttu-id="df33c-144">這些詳細資料來自您在建立採礦結構時，選取為案例資料表的 vTargetMail 檢視。</span><span class="sxs-lookup"><span data-stu-id="df33c-144">These details come from the vTargetMail view that you selected as the case table when building the mining structure.</span></span>  
  
2.  <span data-ttu-id="df33c-145">以滑鼠右鍵按一下節點，**然後選取 [** 向下切入] [**模型和結構資料行**]。</span><span class="sxs-lookup"><span data-stu-id="df33c-145">Right-click a node, and select **Drill Through** then **Model and Structure Columns**.</span></span>  
  
     <span data-ttu-id="df33c-146">隨即顯示相同的資料表，且結尾附加結構資料行。</span><span class="sxs-lookup"><span data-stu-id="df33c-146">The same spreadsheet displays with the structure columns appended to the end.</span></span>  
  
  
###  <a name="dependency-network-tab"></a><a name="Dependency_Network_Tab"></a><span data-ttu-id="df33c-147">相依性網路索引標籤</span><span class="sxs-lookup"><span data-stu-id="df33c-147">Dependency Network Tab</span></span>  
 <span data-ttu-id="df33c-148">[相依性**網路**] 索引標籤會顯示構成採礦模型預測能力的屬性之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="df33c-148">The **Dependency Network** tab displays the relationships between the attributes that contribute to the predictive ability of the mining model.</span></span> <span data-ttu-id="df33c-149">相依性網路檢視器更加印證我們的發現，也就是在預測自行車購買行為時，年齡和地區是重要的因素。</span><span class="sxs-lookup"><span data-stu-id="df33c-149">The Dependency Network viewer reinforces our findings that Age and Region are important factors in predicting bike buying.</span></span>  
  
##### <a name="to-explore-the-model-in-the-dependency-network-tab"></a><span data-ttu-id="df33c-150">若要在相依性網路索引標籤中瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="df33c-150">To explore the model in the Dependency Network tab</span></span>  
  
1.  <span data-ttu-id="df33c-151">按一下 `Bike Buyer` 節點以識別其相依性。</span><span class="sxs-lookup"><span data-stu-id="df33c-151">Click the `Bike Buyer` node to identify its dependencies.</span></span>  
  
     <span data-ttu-id="df33c-152">相依性網路的中央節點表示在 `Bike Buyer` 採礦模型中的可預測屬性。</span><span class="sxs-lookup"><span data-stu-id="df33c-152">The center node for the dependency network, `Bike Buyer`, represents the predictable attribute in the mining model.</span></span> <span data-ttu-id="df33c-153">圖形會反白顯示對可預測屬性有影響的任何相連節點。</span><span class="sxs-lookup"><span data-stu-id="df33c-153">The graph highlights any connected nodes that have an effect on the predictable attribute.</span></span>  
  
2.  <span data-ttu-id="df33c-154">調整 [**所有連結**] 滑杆，以識別最具影響力的屬性。</span><span class="sxs-lookup"><span data-stu-id="df33c-154">Adjust the **All Links** slider to identify the most influential attribute.</span></span>  
  
     <span data-ttu-id="df33c-155">當您向下拖曳滑杆時，只有 [自行車買方] 資料行上有弱效果的屬性會從圖表中移除。</span><span class="sxs-lookup"><span data-stu-id="df33c-155">As you drag down the slider, attributes that have only a weak effect on the [Bike Buyer] column are removed from the graph.</span></span> <span data-ttu-id="df33c-156">藉由調整滑動軸，您可以發現年齡和地區是預測自行車購買者的最大因素。</span><span class="sxs-lookup"><span data-stu-id="df33c-156">By adjusting the slider, you can discover that Age and Region are the greatest factors in predicting whether someone is a bike buyer.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="df33c-157">相關工作</span><span class="sxs-lookup"><span data-stu-id="df33c-157">Related Tasks</span></span>  
 <span data-ttu-id="df33c-158">請參閱下列主題，使用其他種類的模型來瀏覽資料。</span><span class="sxs-lookup"><span data-stu-id="df33c-158">See these topics to explore the data using the other kinds of models.</span></span>  
  
-   [<span data-ttu-id="df33c-159">&#40;基本資料採礦教學課程中探索群集模型&#41;</span><span class="sxs-lookup"><span data-stu-id="df33c-159">Exploring the Clustering Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="df33c-160">探索貝氏貝氏機率分類模型 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="df33c-160">Exploring the Naive Bayes Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="df33c-161">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="df33c-161">Next Task in Lesson</span></span>  
 [<span data-ttu-id="df33c-162">&#40;基本資料採礦教學課程中探索群集模型&#41;</span><span class="sxs-lookup"><span data-stu-id="df33c-162">Exploring the Clustering Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="df33c-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df33c-163">See Also</span></span>  
 <span data-ttu-id="df33c-164">[採礦模型檢視器工作和操作說明](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="df33c-164">[Mining Model Viewer Tasks and How-tos](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="df33c-165">[[決策樹] 索引標籤 &#40;[採礦模型檢視器]&#41;](../../2014/analysis-services/decision-tree-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="df33c-165">[Decision Tree Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/decision-tree-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="df33c-166">[[相依性網路] 索引標籤 &#40;&#41;的採礦模型檢視器](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="df33c-166">[Dependency Network Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md) </span></span>  
 [<span data-ttu-id="df33c-167">使用 Microsoft 樹狀檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="df33c-167">Browse a Model Using the Microsoft Tree Viewer</span></span>](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)  
  
  
