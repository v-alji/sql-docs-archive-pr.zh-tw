---
title: 使用 Microsoft 樹狀檢視器來流覽模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Tree Viewer [Analysis Services]
- predictions [Analysis Services], discrete attributes
- mining model content, viewing
- predictions [Analysis Services], continuous attributes
- mining legend [Analysis Services]
- discrete attributes [Analysis Services]
- Microsoft Decision Trees algorithm [Analysis Services]
- decision tree algorithms [Analysis Services]
- Microsoft Tree Viewer
- decision trees [Analysis Services]
- dependencies [Analysis Services]
- continuous attributes
ms.assetid: 0c96d518-ed20-40b7-8d62-b26ad6244287
author: minewiskan
ms.author: owend
ms.openlocfilehash: cebe1e05435fad453757b4f747ae809f379c410f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607182"
---
# <a name="browse-a-model-using-the-microsoft-tree-viewer"></a><span data-ttu-id="7b6ba-102">使用 Microsoft 樹狀檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="7b6ba-102">Browse a Model Using the Microsoft Tree Viewer</span></span>
  <span data-ttu-id="7b6ba-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]樹狀檢視器 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會顯示以決策樹演算法建立的決策樹 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tree Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays decision trees that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm.</span></span> <span data-ttu-id="7b6ba-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 決策樹演算法是同時支援分類與迴歸的混合式決策樹演算法。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm is a hybrid decision tree algorithm that supports both classification and regression.</span></span> <span data-ttu-id="7b6ba-105">因此，您也可以使用這個檢視器來檢視以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 線性迴歸演算法為基礎的模型。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-105">Therefore, you can also use this viewer to view models based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm.</span></span> <span data-ttu-id="7b6ba-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 決策樹演算法可用於離散和連續屬性的預測模型。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-106">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm is used for predictive modeling of both discrete and continuous attributes.</span></span> <span data-ttu-id="7b6ba-107">如需有關這個演算法的詳細資訊，請參閱＜ [Microsoft Decision Trees Algorithm](microsoft-decision-trees-algorithm.md)＞。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-107">For more information about this algorithm, see [Microsoft Decision Trees Algorithm](microsoft-decision-trees-algorithm.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b6ba-108">若要檢視有關此模型中所用的方程式及所探索之模式的詳細資訊，請使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 一般內容樹狀檢視器。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-108">To view detailed information about the equations used in the model and the patterns that were discovered, use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="7b6ba-109">如需詳細資訊，請參閱[使用 Microsoft 一般內容樹狀檢視器瀏覽模型](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)或 [Microsoft 一般內容樹狀檢視器 &#40;資料採礦&#41;](../microsoft-generic-content-tree-viewer-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-109">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_TabsPanes"></a><span data-ttu-id="7b6ba-110">檢視器索引標籤</span><span class="sxs-lookup"><span data-stu-id="7b6ba-110">Viewer Tabs</span></span>  
 <span data-ttu-id="7b6ba-111">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中瀏覽採礦模型時，該模型會在適合它的檢視器中，顯示於資料採礦設計師的 **[採礦模型檢視器]** 索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-111">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="7b6ba-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 樹狀檢視器包含下列索引標籤和窗格：</span><span class="sxs-lookup"><span data-stu-id="7b6ba-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tree Viewer includes the following tabs and panes:</span></span>  
  
-   [<span data-ttu-id="7b6ba-113">決策樹</span><span class="sxs-lookup"><span data-stu-id="7b6ba-113">Decision Tree</span></span>](#BKMK_DecisionTree)  
  
-   [<span data-ttu-id="7b6ba-114">相依性網路</span><span class="sxs-lookup"><span data-stu-id="7b6ba-114">Dependency Network</span></span>](#BKMK_DependencyNetwork)  
  
-   [<span data-ttu-id="7b6ba-115">採礦圖例</span><span class="sxs-lookup"><span data-stu-id="7b6ba-115">Mining Legend</span></span>](#BKMK_MiningLegend)  
  
###  <a name="decision-tree"></a><a name="BKMK_DecisionTree"></a><span data-ttu-id="7b6ba-116">決策樹</span><span class="sxs-lookup"><span data-stu-id="7b6ba-116">Decision Tree</span></span>  
 <span data-ttu-id="7b6ba-117">當您建立決策樹模型時， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會為每一個可預測屬性建立個別樹狀。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-117">When you build a decision tree model, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] builds a separate tree for each predictable attribute.</span></span> <span data-ttu-id="7b6ba-118">您可以從檢視器之 **[決策樹]** 索引標籤的 **[樹狀結構]** 清單中，選取個別樹狀結構來檢視它。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-118">You can view an individual tree by selecting it from the **Tree** list on the **Decision Tree** tab of the viewer.</span></span>  
  
 <span data-ttu-id="7b6ba-119">決策樹是由一系列的分割所組成，最重要的分割 (由演算法決定) 位於檢視器左邊的 **[全部]** 節點上。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-119">A decision tree is composed of a series of splits, with the most important split, as determined by the algorithm, at the left of the viewer in the **All** node.</span></span> <span data-ttu-id="7b6ba-120">其他分割出現在右邊。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-120">Additional splits occur to the right.</span></span> <span data-ttu-id="7b6ba-121">[所有]\*\*\*\* 節點中的分割最重要，因為它包含資料集內最強的導致分割條件，因此它會導致第一個分割。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-121">The split in the **All** node is most important because it contains the strongest split-causing conditional in the dataset, and therefore it caused the first split.</span></span>  
  
 <span data-ttu-id="7b6ba-122">您可以展開或摺疊樹狀結構中的個別節點，以顯示或隱藏在每一個節點之後發生的分割。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-122">You can expand or collapse individual nodes in the tree to show or hide the splits that occur after each node.</span></span> <span data-ttu-id="7b6ba-123">您也可以使用 **[決策樹]** 索引標籤上的選項，影響樹狀結構的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-123">You can also use the options on the **Decision Tree** tab to affect how the tree is displayed.</span></span> <span data-ttu-id="7b6ba-124">使用 **[顯示層級]** 滑桿，來調整樹狀結構所顯示的層級數目。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-124">Use the **Show Level** slider to adjust the number of levels that are shown in the tree.</span></span> <span data-ttu-id="7b6ba-125">使用 **[預設展開]** ，來設定模型中所有樹狀結構所顯示的預設層級數目。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-125">Use **Default Expansion** to set the default number of levels that are displayed for all trees in the model.</span></span>  
  
#### <a name="predicting-discrete-attributes"></a><span data-ttu-id="7b6ba-126">預測離散屬性</span><span class="sxs-lookup"><span data-stu-id="7b6ba-126">Predicting Discrete Attributes</span></span>  
 <span data-ttu-id="7b6ba-127">以離散可預測屬性建立樹狀結構時，檢視器會在樹狀結構的每一個節點上顯示下列各項：</span><span class="sxs-lookup"><span data-stu-id="7b6ba-127">When a tree is built with a discrete predictable attribute, the viewer displays the following on each node in the tree:</span></span>  
  
-   <span data-ttu-id="7b6ba-128">造成分割的狀況。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-128">The condition that caused the split.</span></span>  
  
-   <span data-ttu-id="7b6ba-129">代表可預測屬性之狀態分佈的長條圖，依據常用性排序。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-129">A histogram that represents the distribution of the states of the predictable attribute, ordered by popularity.</span></span>  
  
 <span data-ttu-id="7b6ba-130">您可以使用 **[長條圖]** 選項，來變更出現在樹狀之長條圖中的狀態數目。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-130">You can use the **Histogram** option to change the number of states that appear in the histograms in the tree.</span></span> <span data-ttu-id="7b6ba-131">如果可預測屬性有許多狀態，則此選項很有用。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-131">This is useful if the predictable attribute has many states.</span></span> <span data-ttu-id="7b6ba-132">狀態會依常用性順序由左至右出現在長條圖中；如果您選擇要顯示的狀態數目少於屬性中的總狀態數目，則最不常用的狀態全部會以灰色顯示。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-132">The states appear in a histogram in order of popularity from left to right; if the number of states that you choose to display is fewer than the total number of states in the attribute, the least popular states are displayed collectively in gray.</span></span> <span data-ttu-id="7b6ba-133">若要查看節點之每一個狀態的確切計數，請將指標暫停在該節點上以檢視工具提示，或選取該節點來檢視它在 **[採礦圖例]** 中的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-133">To see the exact count for each state for a node, pause the pointer over the node to view an InfoTip, or select the node to view its details in the **Mining Legend**.</span></span>  
  
 <span data-ttu-id="7b6ba-134">每一個節點的背景色彩都會代表您使用 **[背景]** 選項選取之特定屬性狀態案例的集中情形。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-134">The background color of each node represents the concentration of cases of the particular attribute state that you select by using the **Background** option.</span></span> <span data-ttu-id="7b6ba-135">您可以使用此選項來反白顯示包含您想要之特定目標的節點。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-135">You can use this option to highlight nodes that contain a particular target in which you are interested.</span></span>  
  
#### <a name="predicting-continuous-attributes"></a><span data-ttu-id="7b6ba-136">預測連續屬性</span><span class="sxs-lookup"><span data-stu-id="7b6ba-136">Predicting Continuous Attributes</span></span>  
 <span data-ttu-id="7b6ba-137">當樹狀是以連續可預測屬性建立時，檢視器會為樹狀中的每一個節點顯示鑽石形圖表，而非長條圖。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-137">When a tree is built with a continuous predictable attribute, the viewer displays a diamond chart, instead of a histogram, for each node in the tree.</span></span> <span data-ttu-id="7b6ba-138">此鑽石形圖表有一條線代表屬性的範圍。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-138">The diamond chart has a line that represents the range of the attribute.</span></span> <span data-ttu-id="7b6ba-139">鑽石形位於節點的平均值之處，而鑽石形的寬度代表在該節點的屬性變異數。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-139">The diamond is located at the mean for the node, and the width of the diamond represents the variance of the attribute at that node.</span></span> <span data-ttu-id="7b6ba-140">鑽石形越窄，表示節點所建立的預測愈精確。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-140">A thinner diamond indicates that the node can create a more accurate prediction.</span></span> <span data-ttu-id="7b6ba-141">檢視器也會顯示迴歸方程式，它是用來決定節點中的分割。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-141">The viewer also displays the regression equation, which is used to determine the split in the node.</span></span>  
  
#### <a name="additional-decision-tree-display-options"></a><span data-ttu-id="7b6ba-142">其他決策樹顯示選項</span><span class="sxs-lookup"><span data-stu-id="7b6ba-142">Additional Decision Tree Display Options</span></span>  
 <span data-ttu-id="7b6ba-143">針對決策樹模型啟用鑽研之後，您可以在樹狀結構中以滑鼠右鍵按一下節點並選取 [鑽研]\*\*\*\*，來存取支援該節點的培訓案例。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-143">When drill through is enabled for a decision tree model, you can access the training cases that support a node by right-clicking the node in the tree and selecting **Drill Through**.</span></span> <span data-ttu-id="7b6ba-144">您可以在資料採礦精靈內啟用鑽研，或在 **[採礦模型]** 索引標籤中調整採礦模型上的鑽研屬性。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-144">You can enable drill through within the Data Mining Wizard, or by adjusting the drill through property on the mining model in the **Mining Models** tab.</span></span>  
  
 <span data-ttu-id="7b6ba-145">您可以使用 **[決策樹]** 索引標籤上的縮放選項來放大或縮小樹狀，或使用 **[調成最適大小]** ，使整個模型調整成檢視器畫面大小。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-145">You can use the zoom options on the **Decision Tree** tab to zoom in or out of a tree, or use **Size to Fit** to fit the whole model in the viewer screen.</span></span> <span data-ttu-id="7b6ba-146">如果樹狀過大而無法調整成螢幕大小，您可以使用 [導覽] \*\*\*\* 選項來導覽樹狀。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-146">If a tree is too large to be sized to fit the screen, you can use the **Navigation**option to navigate through the tree.</span></span> <span data-ttu-id="7b6ba-147">按一下 **[導覽]** 就會開啟個別導覽視窗，您可以使用它來選取要顯示的模型區段。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-147">Clicking **Navigation** opens a separate navigation window that you can use to select sections of the model to display.</span></span>  
  
 <span data-ttu-id="7b6ba-148">您也可以將樹狀檢視影像複製到剪貼簿，以便將其貼到文件中或貼到影像操作軟體中。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-148">You can also copy the tree view image to the Clipboard, so that you can paste it into documents or into image manipulation software.</span></span> <span data-ttu-id="7b6ba-149">使用 **[複製圖表檢視]** 即可只複製檢視器中可見的樹狀區段，或使用 **[複製整個圖表]** 來複製樹狀中所有展開的節點。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-149">Use **Copy Graph View** to copy only the section of the tree that is visible in the viewer, or use **Copy Entire Graph** to copy all the expanded nodes in the tree.</span></span>  
  
 [<span data-ttu-id="7b6ba-150">回到頁首</span><span class="sxs-lookup"><span data-stu-id="7b6ba-150">Back to Top</span></span>](#BKMK_TabsPanes)  
  
###  <a name="dependency-network"></a><a name="BKMK_DependencyNetwork"></a><span data-ttu-id="7b6ba-151">相依性網路</span><span class="sxs-lookup"><span data-stu-id="7b6ba-151">Dependency Network</span></span>  
 <span data-ttu-id="7b6ba-152">**[相依性網路]** 會顯示模型中的輸入屬性和可預測屬性之間的相依性。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-152">The **Dependency Network** displays the dependencies between the input attributes and the predictable attributes in the model.</span></span> <span data-ttu-id="7b6ba-153">檢視器左邊的滑桿會有篩選的作用，與相依性程度相關。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-153">The slider at the left of the viewer acts as a filter that is tied to the strengths of the dependencies.</span></span> <span data-ttu-id="7b6ba-154">如果您降低滑桿，則檢視器中只會顯示最強的連結。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-154">If you lower the slider, only the strongest links are shown in the viewer.</span></span>  
  
 <span data-ttu-id="7b6ba-155">當您選取節點時，檢視器會反白顯示該節點特定的相依性。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-155">When you select a node, the viewer highlights the dependencies that are specific to the node.</span></span> <span data-ttu-id="7b6ba-156">例如，若您選擇一個可預測的節點，檢視器也會反白顯示每一個可協助預測該可預測節點的節點。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-156">For example, if you choose a predictable node, the viewer also highlights each node that helps predict the predictable node.</span></span>  
  
 <span data-ttu-id="7b6ba-157">如果檢視器包含多個節點，您可以使用 **[尋找節點]** 按鈕來搜尋特定節點。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-157">If the viewer contains numerous nodes, you can search for specific nodes by using the **Find Node** button.</span></span> <span data-ttu-id="7b6ba-158">按一下 **[尋找節點]** 就會開啟 **[尋找節點]** 對話方塊，您可以在此使用篩選來搜尋和選取特定節點。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-158">Clicking **Find Node** opens the **Find Node** dialog box, in which you can use a filter to search for and select specific nodes.</span></span>  
  
 <span data-ttu-id="7b6ba-159">檢視器底端的圖例會將色碼連結至圖表中的相依性類型。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-159">The legend at the bottom of the viewer links color codes to the type of dependency in the graph.</span></span> <span data-ttu-id="7b6ba-160">例如，當您選取可預測的節點時，可預測節點會呈現淺粉藍色陰影，而預測所選取之節點的節點則會呈現橙色陰影。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-160">For example, when you select a predictable node, the predictable node is shaded turquoise, and the nodes that predict the selected node are shaded orange.</span></span>  
  
 [<span data-ttu-id="7b6ba-161">回到頁首</span><span class="sxs-lookup"><span data-stu-id="7b6ba-161">Back to Top</span></span>](#BKMK_TabsPanes)  
  
###  <a name="mining-legend"></a><a name="BKMK_MiningLegend"></a><span data-ttu-id="7b6ba-162">[挖掘圖例]</span><span class="sxs-lookup"><span data-stu-id="7b6ba-162">Mining Legend</span></span>  
 <span data-ttu-id="7b6ba-163">當您在決策樹模型中選取節點時， **[採礦圖例]** 會顯示下列資訊：</span><span class="sxs-lookup"><span data-stu-id="7b6ba-163">The **Mining Legend** displays the following information when you select a node in the decision tree model:</span></span>  
  
-   <span data-ttu-id="7b6ba-164">節點中的案例數目，依可預測屬性的狀態細分。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-164">The number of cases in the node, broken down by the states of the predictable attribute.</span></span>  
  
-   <span data-ttu-id="7b6ba-165">節點的可預測屬性之每一個案例的機率。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-165">The probability of each case of the predictable attribute for the node.</span></span>  
  
-   <span data-ttu-id="7b6ba-166">包括可預測屬性的每一個狀態計數的長條圖。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-166">A histogram that includes a count for each state of the predictable attribute.</span></span>  
  
-   <span data-ttu-id="7b6ba-167">要連上特定節點所需的條件，亦稱為 *節點路徑*。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-167">The conditions that are required to reach a specific node, also known as the *node path*.</span></span>  
  
-   <span data-ttu-id="7b6ba-168">若為線性迴歸模型，就會顯示迴歸公式。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-168">For linear regression models, the regression formula.</span></span>  
  
 <span data-ttu-id="7b6ba-169">您可以用類似方案總管的方式來停駐和使用 **[採礦圖例]** 。</span><span class="sxs-lookup"><span data-stu-id="7b6ba-169">You can dock and work with the **Mining Legend** in a similar manner as with Solution Explorer.</span></span>  
  
 [<span data-ttu-id="7b6ba-170">回到頁首</span><span class="sxs-lookup"><span data-stu-id="7b6ba-170">Back to Top</span></span>](#BKMK_TabsPanes)  
  
## <a name="see-also"></a><span data-ttu-id="7b6ba-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b6ba-171">See Also</span></span>  
 <span data-ttu-id="7b6ba-172">[Microsoft 決策樹演算法](microsoft-decision-trees-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="7b6ba-172">[Microsoft Decision Trees Algorithm](microsoft-decision-trees-algorithm.md) </span></span>  
 <span data-ttu-id="7b6ba-173">[&#40;資料採礦模型設計工具的採礦模型檢視器&#41;](../mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="7b6ba-173">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](../mining-model-viewers-data-mining-model-designer.md) </span></span>  
 <span data-ttu-id="7b6ba-174">[採礦模型檢視器工作和操作說明](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="7b6ba-174">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="7b6ba-175">[資料採礦工具](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="7b6ba-175">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="7b6ba-176">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="7b6ba-176">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
  
