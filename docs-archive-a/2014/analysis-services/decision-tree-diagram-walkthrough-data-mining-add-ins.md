---
title: 決策樹圖表逐步解說 (資料採礦增益集) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- shapes, data mining
- diagram, decision tree
- Visio shapes, decision tree
- decision tree [data mining]
ms.assetid: 9566f6a2-c750-4125-ba5e-42c7251a78c7
author: minewiskan
ms.author: owend
ms.openlocfilehash: bbe54db1ab3d00d074917db770a9a731f884f49a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594819"
---
# <a name="decision-tree-diagram-walkthrough--data-mining-add-ins"></a><span data-ttu-id="82ddb-102">決策樹圖表逐步解說 (資料採礦增益集) </span><span class="sxs-lookup"><span data-stu-id="82ddb-102">Decision Tree Diagram Walkthrough  (Data Mining Add-ins)</span></span>
  <span data-ttu-id="82ddb-103">如果您已經建立決策樹模型，就可以在 Visio 中使用 [決策樹] 圖形或 [相依性網路] 圖形來建立自訂的圖表。</span><span class="sxs-lookup"><span data-stu-id="82ddb-103">If you have created a decision tree model, you can create a customized diagram in Visio by using either the Decision Tree shape or the Dependency Network shape.</span></span> <span data-ttu-id="82ddb-104">本主題描述您可以使用 [**決策樹**] 圖形和這些控制項來執行的自訂：</span><span class="sxs-lookup"><span data-stu-id="82ddb-104">This topic describes the customizations you can perform using the **Decision Tree** shape and these controls:</span></span>  
  
-   <span data-ttu-id="82ddb-105">決策樹圖表的轉譯控制項</span><span class="sxs-lookup"><span data-stu-id="82ddb-105">Rendering controls for the decision tree diagram</span></span>  
  
     <span data-ttu-id="82ddb-106">這些選項是當您將圖形放入 Visio 工作區時啟動的**決策樹 Wizard**的一部分。</span><span class="sxs-lookup"><span data-stu-id="82ddb-106">These options are part of the **Decision Tree Wizard** that is launched when you drop a shape into the Visio workspace.</span></span>  
  
-   <span data-ttu-id="82ddb-107">**資料採礦版面**組態工具欄</span><span class="sxs-lookup"><span data-stu-id="82ddb-107">**Data Mining Layout** toolbar</span></span>  
  
     <span data-ttu-id="82ddb-108">這些選項會加入至 Visio 工作區以協助您與圖形互動。</span><span class="sxs-lookup"><span data-stu-id="82ddb-108">These options are added to the Visio workspace to help you interact with the shape.</span></span>  
  
## <a name="build-a-decision-tree-diagram"></a><span data-ttu-id="82ddb-109">建立決策樹圖表</span><span class="sxs-lookup"><span data-stu-id="82ddb-109">Build a Decision Tree Diagram</span></span>  
 <span data-ttu-id="82ddb-110">您可以將 [決策樹] 圖形放到 Visio 頁面上，以啟動**決策樹 Visio 圖形 Wizard**並設定圖表選項。</span><span class="sxs-lookup"><span data-stu-id="82ddb-110">You drop the Decision Tree shape onto the Visio page to launch the **Decision Tree Visio Shape Wizard** and set diagram options.</span></span>  
  
#### <a name="use-the-decision-tree-wizard"></a><span data-ttu-id="82ddb-111">使用決策樹精靈</span><span class="sxs-lookup"><span data-stu-id="82ddb-111">Use the Decision Tree Wizard</span></span>  
  
1.  <span data-ttu-id="82ddb-112">如果您在 [**圖形**] 清單中看不到 [ **Microsoft 資料採礦圖形**]，請按一下 [**更多圖形**]，選取 [**開啟**樣板]，然後從預設安裝位置開啟範本。</span><span class="sxs-lookup"><span data-stu-id="82ddb-112">If you do not see **Microsoft Data Mining Shapes** in the **Shapes** list, click **More Shapes**, select **Open Stencil**, and open the template from the default installation location.</span></span>  
  
     <span data-ttu-id="82ddb-113">\<drive>： \Program files (x85) \Microsoft SQL Server 2012 DM 增益集</span><span class="sxs-lookup"><span data-stu-id="82ddb-113">\<drive>:\Program files (x85)\Microsoft SQL Server 2012 DM Add-Ins</span></span>  
  
2.  <span data-ttu-id="82ddb-114">將 [**決策樹**] 圖形拖曳至頁面上。</span><span class="sxs-lookup"><span data-stu-id="82ddb-114">Drag the **Decision Tree** shape onto the page.</span></span>  
  
3.  <span data-ttu-id="82ddb-115">在 [**決策樹 Visio 圖形 Wizard]** 的 [歡迎使用] 頁面上，按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="82ddb-115">On the welcome page of the **Decision Tree Visio Shape Wizard**, click **Next**.</span></span>  
  
4.  <span data-ttu-id="82ddb-116">在叢集 Wizard 的 [**選取資料來源** **]** 頁面上，選擇 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 具有您想要視覺化之模型的伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="82ddb-116">On the **Select a Data Source** page of the **Cluster Wizard**, choose a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server that has the model you want to visualize.</span></span>  
  
5.  <span data-ttu-id="82ddb-117">選取適當的 [採礦模型]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="82ddb-117">Select an appropriate mining model, and click **Next**.</span></span>  
  
     <span data-ttu-id="82ddb-118">此圖表類型支援使用決策樹或線性迴歸演算法所建立的模型。</span><span class="sxs-lookup"><span data-stu-id="82ddb-118">This diagram type supports models created using the Decision Trees or Linear Regression algorithm.</span></span>  
  
6.  <span data-ttu-id="82ddb-119">在 [**選取決策樹**] 頁面上，選擇要顯示的個別樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="82ddb-119">On the **Select Decision Tree** page, choose an individual tree to display.</span></span>  
  
     <span data-ttu-id="82ddb-120">樹狀結構會將導致您所模型化之特定結果的互動模型化。因此，即使您的模型包含多個結果，您一次只能顯示一個樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="82ddb-120">A tree models the interactions that lead to a particular outcome you've modeled; therefore, even if your model contains multiple outcomes, you can display only one tree at a time.</span></span>  
  
7.  <span data-ttu-id="82ddb-121">在 [**選取決策樹**] 對話方塊中，您也可以設定這些轉譯選項：</span><span class="sxs-lookup"><span data-stu-id="82ddb-121">In the **Select Decision Tree** dialog box, you can also set these rendering options:</span></span>  
  
     <span data-ttu-id="82ddb-122">**最大轉譯深度**</span><span class="sxs-lookup"><span data-stu-id="82ddb-122">**Maximum Rendering Depth**</span></span>  
     <span data-ttu-id="82ddb-123">您可以使用此選項來控制顯示的節點數目。</span><span class="sxs-lookup"><span data-stu-id="82ddb-123">Use this option to control how many nodes are displayed.</span></span>  
  
     <span data-ttu-id="82ddb-124">決策樹的深度可能會過高，導致圖表無法容納在頁面上。</span><span class="sxs-lookup"><span data-stu-id="82ddb-124">A decision tree might go very deep, creating a diagram that does not fit on the page.</span></span> <span data-ttu-id="82ddb-125">請使用此控制項，將焦點放在最左邊的節點上，這些是最重要的節點。</span><span class="sxs-lookup"><span data-stu-id="82ddb-125">Use this control to focus on the leftmost nodes, which are more important.</span></span>  
  
     <span data-ttu-id="82ddb-126">預設值是三層節點。</span><span class="sxs-lookup"><span data-stu-id="82ddb-126">The default is three levels of nodes.</span></span>  
  
     <span data-ttu-id="82ddb-127">**選取值的色彩和顯示文字**</span><span class="sxs-lookup"><span data-stu-id="82ddb-127">**Select color and display text for values**</span></span>  
     <span data-ttu-id="82ddb-128">您可以選擇代表每個結果的色彩。</span><span class="sxs-lookup"><span data-stu-id="82ddb-128">Choose the color that will represent each one of the outcomes.</span></span> <span data-ttu-id="82ddb-129">如果您沒有指定色彩，系統就會使用目前的視訊佈景主題色彩來自動產生色彩。</span><span class="sxs-lookup"><span data-stu-id="82ddb-129">If you do not specify colors, they are automatically generated using the current video theme colors.</span></span>  
  
8.  <span data-ttu-id="82ddb-130">按一下 [**高級**]，針對決策樹圖表中的每個節點自訂下列選項。</span><span class="sxs-lookup"><span data-stu-id="82ddb-130">Click **Advanced** to customize the following options for each of the nodes in the decision tree diagram.</span></span>  
  
     <span data-ttu-id="82ddb-131">**陰影變數**和**狀態**</span><span class="sxs-lookup"><span data-stu-id="82ddb-131">**Shading Variable** and **State**</span></span>  
     <span data-ttu-id="82ddb-132">選擇您想要顯示在樹狀圖表中的目標結果。</span><span class="sxs-lookup"><span data-stu-id="82ddb-132">Choose the target outcome that you want to show in the tree diagram.</span></span>  
  
     <span data-ttu-id="82ddb-133">**顯示長條圖**</span><span class="sxs-lookup"><span data-stu-id="82ddb-133">**Show Histogram**</span></span>  
     <span data-ttu-id="82ddb-134">將圖表加入至每個節點，其中顯示定義該節點的規則。</span><span class="sxs-lookup"><span data-stu-id="82ddb-134">Adds a chart to each node that shows the rules that define that node.</span></span>  
  
     <span data-ttu-id="82ddb-135">**顯示標籤**</span><span class="sxs-lookup"><span data-stu-id="82ddb-135">**Show Label**</span></span>  
     <span data-ttu-id="82ddb-136">將資料行名稱加入至長條圖。</span><span class="sxs-lookup"><span data-stu-id="82ddb-136">Adds column names to the histogram.</span></span>  
  
     <span data-ttu-id="82ddb-137">**顯示機率**</span><span class="sxs-lookup"><span data-stu-id="82ddb-137">**Show Probability**</span></span>  
     <span data-ttu-id="82ddb-138">顯示每個值的機率。</span><span class="sxs-lookup"><span data-stu-id="82ddb-138">Displays the probability of each value.</span></span>  
  
     <span data-ttu-id="82ddb-139">**顯示支援**</span><span class="sxs-lookup"><span data-stu-id="82ddb-139">**Show Support**</span></span>  
     <span data-ttu-id="82ddb-140">顯示每個值的支援。</span><span class="sxs-lookup"><span data-stu-id="82ddb-140">Displays the support for each value.</span></span>  
  
     <span data-ttu-id="82ddb-141">**顯示頁尾**</span><span class="sxs-lookup"><span data-stu-id="82ddb-141">**Show Footer**</span></span>  
     <span data-ttu-id="82ddb-142">加入加總所有顯示值的頁尾。</span><span class="sxs-lookup"><span data-stu-id="82ddb-142">Adds a footer that sums all displayed values.</span></span>  
  
     <span data-ttu-id="82ddb-143">**顯示頁首**</span><span class="sxs-lookup"><span data-stu-id="82ddb-143">**Show Header**</span></span>  
     <span data-ttu-id="82ddb-144">加入資料行標題。</span><span class="sxs-lookup"><span data-stu-id="82ddb-144">Adds column headings.</span></span>  
  
     <span data-ttu-id="82ddb-145">**顯示沒有支援的狀態**</span><span class="sxs-lookup"><span data-stu-id="82ddb-145">**Show states with zero support**</span></span>  
     <span data-ttu-id="82ddb-146">讓您顯示遺漏值。</span><span class="sxs-lookup"><span data-stu-id="82ddb-146">Lets you display missing values.</span></span>  
  
9. <span data-ttu-id="82ddb-147">按一下 **[完成]** 以建立圖形。</span><span class="sxs-lookup"><span data-stu-id="82ddb-147">Click **Finish** to create the graph.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="82ddb-148">在某些環境中，圖表中的連接線可能無法在 Office 2013 中呈現。</span><span class="sxs-lookup"><span data-stu-id="82ddb-148">In some environments, connectors in the chart might fail to render in Office 2013.</span></span>  
  
## <a name="explore-and-modify-the-finished-diagram"></a><span data-ttu-id="82ddb-149">探索和修改完成的圖表</span><span class="sxs-lookup"><span data-stu-id="82ddb-149">Explore and Modify the Finished Diagram</span></span>  
 <span data-ttu-id="82ddb-150">當您完成 [**決策樹 Visio 圖形嚮導]** 之後，Visio 會在頁面上建立一個樹狀圖表，以圖形方式顯示導致預測結果的規則。</span><span class="sxs-lookup"><span data-stu-id="82ddb-150">After you have completed the **Decision Tree Visio Shape Wizard**, Visio creates a tree diagram on the page that graphically displays the rules that lead to the predicted outcome.</span></span>  
  
 <span data-ttu-id="82ddb-151">您可以繼續使用下列控制項來修改決策樹圖表的圖形：</span><span class="sxs-lookup"><span data-stu-id="82ddb-151">You can continue to modify the shape by using the following controls for decision tree diagrams:</span></span>  
  
#### <a name="using-the-decision-tree-option-menus"></a><span data-ttu-id="82ddb-152">使用決策樹選項功能表</span><span class="sxs-lookup"><span data-stu-id="82ddb-152">Using the decision tree option menus</span></span>  
  
1.  <span data-ttu-id="82ddb-153">按一下 [**增益集**] 功能區，然後顯示用來處理資料採礦圖表的其中一個自訂工具列：</span><span class="sxs-lookup"><span data-stu-id="82ddb-153">Click the **Add-Ins** ribbon, and then display one of the custom toolbars used for working with data mining diagrams:</span></span>  
  
     <span data-ttu-id="82ddb-154">**配置**</span><span class="sxs-lookup"><span data-stu-id="82ddb-154">**Layout**</span></span>  
     <span data-ttu-id="82ddb-155">最佳化樹狀結構的排列方式以符合目前的頁面。</span><span class="sxs-lookup"><span data-stu-id="82ddb-155">Optimizes the arrangement of the tree to fit the current page.</span></span>  
  
     <span data-ttu-id="82ddb-156">**調整頁面大小**</span><span class="sxs-lookup"><span data-stu-id="82ddb-156">**Resize Page**</span></span>  
     <span data-ttu-id="82ddb-157">此控制項適用於先前的 HTML 版本。</span><span class="sxs-lookup"><span data-stu-id="82ddb-157">This control was intended for earlier HTML versions.</span></span> <span data-ttu-id="82ddb-158">請改用 Visio 頁面大小調整控制項。</span><span class="sxs-lookup"><span data-stu-id="82ddb-158">Use the Visio page resizing controls instead,</span></span>  
  
     <span data-ttu-id="82ddb-159">**說明**</span><span class="sxs-lookup"><span data-stu-id="82ddb-159">**Description**</span></span>  
     <span data-ttu-id="82ddb-160">當您選取樹狀結構的節點時，按一下此選項就會顯示有關節點中案例的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="82ddb-160">When a node of the tree is selected, click this option to display details about the cases in the node.</span></span>  
  
2.  <span data-ttu-id="82ddb-161">使用 Visio**設計**功能區中的 [**重新配置頁面**] 選項來試驗不同的樹狀結構版面配置。</span><span class="sxs-lookup"><span data-stu-id="82ddb-161">Use the **Re-Layout Page** option in the Visio **Design** ribbon to experiment with different tree layouts.</span></span>  
  
3.  <span data-ttu-id="82ddb-162">使用 [**設計**] 索引標籤上的 [**連接器**] 選項，即可變更樹狀結構中節點之間所使用的連接器。</span><span class="sxs-lookup"><span data-stu-id="82ddb-162">Use the **Connectors** option on the **Design** tab to change the connectors used between nodes in the tree.</span></span>  
  
4.  <span data-ttu-id="82ddb-163">在 Visio **View**功能區的 [工作**窗格]** 區域中，使用 [**平移和縮放**] 控制項，將焦點放在圖表的特定區域。</span><span class="sxs-lookup"><span data-stu-id="82ddb-163">Use the **Pan and Zoom** control, in the **Task Pane** area of the Visio **View** ribbon, to focus on a particular area of the diagram.</span></span>  
  
5.  <span data-ttu-id="82ddb-164">以滑鼠右鍵按一下樹狀結構中的任何節點，然後從決策樹圖表特有的這些捷徑功能表選項中選擇：</span><span class="sxs-lookup"><span data-stu-id="82ddb-164">Right-click any node in the tree, and choose from these shortcut menu options specific to decision tree diagrams:</span></span>  
  
     <span data-ttu-id="82ddb-165">**修訂頁面配置**</span><span class="sxs-lookup"><span data-stu-id="82ddb-165">**Improve Page Layout**</span></span>  
     <span data-ttu-id="82ddb-166">在頁面上平均分佈節點，並調整頁面檢視，以便查看所有節點。</span><span class="sxs-lookup"><span data-stu-id="82ddb-166">Distributes the nodes evenly on the page and adjusts the page view to see all nodes.</span></span>  
  
     <span data-ttu-id="82ddb-167">**將子節點移到新頁面**</span><span class="sxs-lookup"><span data-stu-id="82ddb-167">**Move Children to New Page**</span></span>  
     <span data-ttu-id="82ddb-168">將目前選定節點的子節點移到新頁面。</span><span class="sxs-lookup"><span data-stu-id="82ddb-168">Moves the children of the currently selected node to a new page.</span></span>  
  
     <span data-ttu-id="82ddb-169">**摺疊子節點**</span><span class="sxs-lookup"><span data-stu-id="82ddb-169">**Collapse Child Nodes**</span></span>  
     <span data-ttu-id="82ddb-170">隱藏目前選定節點的子節點。</span><span class="sxs-lookup"><span data-stu-id="82ddb-170">Hides the children of the currently selected node.</span></span>  
  
     <span data-ttu-id="82ddb-171">**展開子節點**</span><span class="sxs-lookup"><span data-stu-id="82ddb-171">**Expand Child Nodes**</span></span>  
     <span data-ttu-id="82ddb-172">顯示目前選定節點的子節點。</span><span class="sxs-lookup"><span data-stu-id="82ddb-172">Displays the children of the currently selected node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82ddb-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82ddb-173">See Also</span></span>  
 [<span data-ttu-id="82ddb-174">針對 Visio 資料採礦圖表進行疑難排解 &#40;SQL Server 資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="82ddb-174">Troubleshooting Visio Data Mining Diagrams &#40;SQL Server Data Mining Add-ins&#41;</span></span>](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
