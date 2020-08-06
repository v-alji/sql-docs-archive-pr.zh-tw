---
title: 相依性網狀圖表逐步解說 (資料採礦增益集) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Visio shapes, dependency network
- shapes, data mining
- shapes, network
- dependencies
- diagram, dependency network
- data mining layout toolbar
- dependency network
ms.assetid: aac732a8-5262-4649-b7d7-3ccf6f9cfa8b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 07f97dac7ffb0211f0ff1e1b58c2e0792d026174
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605931"
---
# <a name="dependency-network-diagram-walkthrough-data-mining-add-ins"></a><span data-ttu-id="8d361-102">相依性網路圖表逐步解說 (資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="8d361-102">Dependency Network Diagram Walkthrough (Data Mining Add-ins)</span></span>
  <span data-ttu-id="8d361-103">許多不同類型的資料採礦模型都會使用網路圖形做為探索資料關聯性的方式。</span><span class="sxs-lookup"><span data-stu-id="8d361-103">Several different types of data mining models use a network graph as a way of exploring relationships in the data.</span></span> <span data-ttu-id="8d361-104">您可以使用 [相依性**網路**] 圖形將這些模型匯入 Visio，然後繼續自訂並增強版面配置。</span><span class="sxs-lookup"><span data-stu-id="8d361-104">You can import these models into Visio using the **Dependency Network** shape and then continue to customize and enhance the layout.</span></span> <span data-ttu-id="8d361-105">**適用于 Visio 的資料採礦圖形**包含下列用來處理相依性網狀圖表的自訂控制項：</span><span class="sxs-lookup"><span data-stu-id="8d361-105">The **Data Mining Shapes for Visio** include the following custom controls for working with dependency network diagrams:</span></span>  
  
-   <span data-ttu-id="8d361-106">網路圖形的轉譯控制項</span><span class="sxs-lookup"><span data-stu-id="8d361-106">Rendering controls for the network graph</span></span>  
  
     <span data-ttu-id="8d361-107">這些選項屬於精靈的一部分，而這個精靈是在您將圖形放入 Visio 工作區時啟動。</span><span class="sxs-lookup"><span data-stu-id="8d361-107">These options are part of the wizard that is launched when you drop a shape into the Visio workspace.</span></span>  
  
-   <span data-ttu-id="8d361-108">**資料採礦版面**組態工具欄</span><span class="sxs-lookup"><span data-stu-id="8d361-108">**Data Mining Layout** toolbar</span></span>  
  
     <span data-ttu-id="8d361-109">這些選項會加入至 Visio 工作區以協助您與相依性網路圖形互動。</span><span class="sxs-lookup"><span data-stu-id="8d361-109">These options are added to the Visio workspace to help you interact with the dependency network graph.</span></span>  
  
## <a name="build-a-dependency-network-graph"></a><span data-ttu-id="8d361-110">建立相依性網路圖形</span><span class="sxs-lookup"><span data-stu-id="8d361-110">Build a Dependency Network Graph</span></span>  
 <span data-ttu-id="8d361-111">您可以將圖形放到 Visio 頁面上，以啟動相依性**網路 Visio 圖形 Wizard**並設定圖表選項。</span><span class="sxs-lookup"><span data-stu-id="8d361-111">You drop a shape onto the Visio page to launch the **Dependency Net Visio Shape Wizard** and set diagram options.</span></span>  
  
#### <a name="use-the-dependency-net-visio-shape-wizard"></a><span data-ttu-id="8d361-112">使用相依性網路 Visio 圖形精靈</span><span class="sxs-lookup"><span data-stu-id="8d361-112">Use the Dependency Net Visio Shape Wizard</span></span>  
  
1.  <span data-ttu-id="8d361-113">如果您在 [**圖形**] 清單中看不到 [ **Microsoft 資料採礦圖形**]，請按一下 [**更多圖形**]，選取 [**開啟**樣板]，然後從預設安裝位置開啟範本。</span><span class="sxs-lookup"><span data-stu-id="8d361-113">If you do not see **Microsoft Data Mining Shapes** in the **Shapes** list, click **More Shapes**, select **Open Stencil**, and open the template from the default installation location.</span></span>  
  
     <span data-ttu-id="8d361-114">\<drive>： \Program files (x85) \Microsoft SQL Server 2012 DM 增益集</span><span class="sxs-lookup"><span data-stu-id="8d361-114">\<drive>:\Program files (x85)\Microsoft SQL Server 2012 DM Add-Ins</span></span>  
  
2.  <span data-ttu-id="8d361-115">將 [相依性**網路**] 圖形拖曳至頁面上，以啟動精靈。</span><span class="sxs-lookup"><span data-stu-id="8d361-115">Drag the **Dependency Network** shape onto the page to start the wizard.</span></span> <span data-ttu-id="8d361-116">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="8d361-116">Click **Next**.</span></span>  
  
3.  <span data-ttu-id="8d361-117">在相依性**網路 Visio 圖形 Wizard**的 [歡迎使用] 頁面上，按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="8d361-117">On the welcome page of the **Dependency Network Visio Shape Wizard**, click **Next**.</span></span>  
  
4.  <span data-ttu-id="8d361-118">在 [相依性**網路 Visio 圖形 Wizard]** 的 [**選取資料來源**] 頁面上，選擇 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 具有您想要視覺化之模型的伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="8d361-118">On the **Select a Data Source** page of the **Dependency Network Visio Shape Wizard**, choose a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server that has the model you want to visualize.</span></span>  
  
5.  <span data-ttu-id="8d361-119">選取適當的 [採礦模型]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="8d361-119">Select an appropriate mining model, and click **Next**.</span></span>  
  
     <span data-ttu-id="8d361-120">若要選取適當的模型，您可以在 [**屬性**] 窗格中，檢查名稱、描述、資料行和資料類型。</span><span class="sxs-lookup"><span data-stu-id="8d361-120">To select an appropriate model, you can review the name, description, columns, and type of data in the **Properties** pane.</span></span>  
  
     <span data-ttu-id="8d361-121">此圖形支援使用下列演算法所建立的模型：</span><span class="sxs-lookup"><span data-stu-id="8d361-121">This shape supports models created by using these algorithms:</span></span>  
  
    -   <span data-ttu-id="8d361-122">貝氏機率分類</span><span class="sxs-lookup"><span data-stu-id="8d361-122">Naïve Bayes</span></span>  
  
    -   <span data-ttu-id="8d361-123">決策樹</span><span class="sxs-lookup"><span data-stu-id="8d361-123">Decision Trees</span></span>  
  
    -   <span data-ttu-id="8d361-124">關聯規則</span><span class="sxs-lookup"><span data-stu-id="8d361-124">Association Rules</span></span>  
  
6.  <span data-ttu-id="8d361-125">在頁面上，**選取要**轉譯的節點、自訂圖形的大小，並選擇性地篩選成隻包含特定的節點。</span><span class="sxs-lookup"><span data-stu-id="8d361-125">On the page, **Select Nodes to Render**, customize the size of the graph, and optionally filter to only include certain nodes.</span></span>  
  
     <span data-ttu-id="8d361-126">使用大型資料集時，相依性圖形可能會變得很龐大，而且包含許多相關物件，以*節點*表示。</span><span class="sxs-lookup"><span data-stu-id="8d361-126">With a large dataset, a dependency graph can become huge, and contain many related objects, represented as *nodes*.</span></span> <span data-ttu-id="8d361-127">您可以使用此對話方塊來建立僅包含感興趣節點的自訂網路圖形。</span><span class="sxs-lookup"><span data-stu-id="8d361-127">By using this dialog box, you can create a custom network graph that includes only the nodes of interest.</span></span>  
  
     <span data-ttu-id="8d361-128">[藝術預留位置]</span><span class="sxs-lookup"><span data-stu-id="8d361-128">[art placeholder]</span></span>  
  
     <span data-ttu-id="8d361-129">**要提取的節點數目**</span><span class="sxs-lookup"><span data-stu-id="8d361-129">**Number of nodes to fetch**</span></span>  
     <span data-ttu-id="8d361-130">如果模型包含的節點少於指定的節點數目，這個設定沒有作用。</span><span class="sxs-lookup"><span data-stu-id="8d361-130">If the model contains fewer than the specified number of nodes, this setting has no effect.</span></span> <span data-ttu-id="8d361-131">如果模型包含的節點超過指定的數目，則只會顯示關聯性最強的節點。</span><span class="sxs-lookup"><span data-stu-id="8d361-131">If the model contains more nodes than the specified number, only the strongest nodes are displayed.</span></span>  
  
     <span data-ttu-id="8d361-132">**名稱包含**</span><span class="sxs-lookup"><span data-stu-id="8d361-132">**Name contains**</span></span>  
     <span data-ttu-id="8d361-133">將這個方塊保留空白，然後按一下綠色箭頭，即可擷取模型中的所有節點。</span><span class="sxs-lookup"><span data-stu-id="8d361-133">Leave this box blank and click the green arrow to retrieve all nodes in the model.</span></span>  
  
     <span data-ttu-id="8d361-134">或者，輸入字串，然後按一下綠色箭頭，只傳回包含指定字串的節點。</span><span class="sxs-lookup"><span data-stu-id="8d361-134">Or, type a string and click the green arrow to return only those nodes that contain the specified string.</span></span>  
  
     <span data-ttu-id="8d361-135">您可以使用範例資料建立的大部分模型都不會太大，因此在此範例中，請將節點的數目提高至 10，然後按一下綠色箭頭以執行查詢並取得所有節點的清單。</span><span class="sxs-lookup"><span data-stu-id="8d361-135">Most of the models that you can create with the sample data are not big, so for this example, increase the number of nodes to 10, and then click the green arrow to run a query and get the list of all nodes.</span></span>  
  
7.  <span data-ttu-id="8d361-136">按一下 [ **Advanced** ] 以設定圖形的陰影和形狀選項。</span><span class="sxs-lookup"><span data-stu-id="8d361-136">Click **Advanced** to set shading and shape options for the graph.</span></span>  
  
8.  <span data-ttu-id="8d361-137">按一下 [關閉] 以**結束**[ **Advanced** options] 對話方塊，然後按一下 **[完成**] 以建立圖形。</span><span class="sxs-lookup"><span data-stu-id="8d361-137">Click **Close** to exit the **Advanced** options dialog box, and then click **Finish** to create the graph.</span></span>  
  
## <a name="explore-and-modify-the-finished-diagram"></a><span data-ttu-id="8d361-138">探索和修改完成的圖表</span><span class="sxs-lookup"><span data-stu-id="8d361-138">Explore and Modify the Finished Diagram</span></span>  
 <span data-ttu-id="8d361-139">在 Visio 建立相依性網路圖形之後，您就可以繼續使用 Visio 中的功能來修改並增強圖形。</span><span class="sxs-lookup"><span data-stu-id="8d361-139">After Visio has created the network dependency graph, you can continue to modify and enhance the graph by using the features in Visio.</span></span>  
  
 <span data-ttu-id="8d361-140">下圖顯示相依性網路圖形的預設配置。</span><span class="sxs-lookup"><span data-stu-id="8d361-140">The following graphic shows the default layout of a dependency network graph.</span></span>  
  
 <span data-ttu-id="8d361-141">[藝術預留位置]</span><span class="sxs-lookup"><span data-stu-id="8d361-141">[art placeholder]</span></span>  
  
1.  <span data-ttu-id="8d361-142">使用 [工作**窗格]** 功能區的 [移動**流覽\*\*\*\*和縮放**] 控制項，將焦點放在圖形的某個區段上，然後在圖表中四處移動。</span><span class="sxs-lookup"><span data-stu-id="8d361-142">Use the **Pan and Zoom** control, in the **Task Pane** area of the Visio **View** ribbon, to focus on a section of the graph and move around the diagram.</span></span>  
  
2.  <span data-ttu-id="8d361-143">使用 [Visio**重新配置頁面**] 選項所提供的不同圖形版面配置進行實驗。</span><span class="sxs-lookup"><span data-stu-id="8d361-143">Experiment with different graph layouts provided by the Visio **Re-Layout Page** option.</span></span>  
  
3.  <span data-ttu-id="8d361-144">按一下 [**增益集**] 功能區，然後顯示用來處理資料採礦圖表的其中一個自訂工具列：</span><span class="sxs-lookup"><span data-stu-id="8d361-144">Click the **Add-Ins** ribbon, and then display one of the custom toolbars used for working with data mining diagrams:</span></span>  
  
     <span data-ttu-id="8d361-145">**配置**</span><span class="sxs-lookup"><span data-stu-id="8d361-145">**Layout**</span></span>  
     <span data-ttu-id="8d361-146">最佳化頁面上的節點配置及變更檢視，以便顯示所有節點。</span><span class="sxs-lookup"><span data-stu-id="8d361-146">Optimizes the layout of nodes on the page, and changes the view so that all nodes are visible.</span></span>  
  
     <span data-ttu-id="8d361-147">**調整頁面大小**</span><span class="sxs-lookup"><span data-stu-id="8d361-147">**Resize Page**</span></span>  
     <span data-ttu-id="8d361-148">變更頁面大小，以便顯示所有節點。</span><span class="sxs-lookup"><span data-stu-id="8d361-148">Changes the size of the page so that all nodes are visible.</span></span>  
  
     <span data-ttu-id="8d361-149">**邊緣強度**</span><span class="sxs-lookup"><span data-stu-id="8d361-149">**Edge Strength**</span></span>  
     <span data-ttu-id="8d361-150">切換整個圖形的邊緣強度顯示。</span><span class="sxs-lookup"><span data-stu-id="8d361-150">Toggles display of edge strength for the entire graph.</span></span> <span data-ttu-id="8d361-151">邊緣是節點之間的連接。</span><span class="sxs-lookup"><span data-stu-id="8d361-151">An edge is a connection between nodes.</span></span> <span data-ttu-id="8d361-152">您可以使用滑桿控制項來篩選出關聯性不強的連接。</span><span class="sxs-lookup"><span data-stu-id="8d361-152">You can use the slider control to filter out connections that are not strong.</span></span>  
  
     <span data-ttu-id="8d361-153">**滑桿**</span><span class="sxs-lookup"><span data-stu-id="8d361-153">**Slider**</span></span>  
     <span data-ttu-id="8d361-154">**滑杆**可協助您控制相依性網狀圖表中顯示之關聯性的強度。</span><span class="sxs-lookup"><span data-stu-id="8d361-154">The **Slider** helps you control the strength of the relationships that are displayed in the dependency network diagram.</span></span>  
  
     <span data-ttu-id="8d361-155">圖形中的每個節點代表一個狀態。</span><span class="sxs-lookup"><span data-stu-id="8d361-155">Each node in the graph represents a state.</span></span> <span data-ttu-id="8d361-156">箭頭代表兩個狀態之間的轉換以及與轉換相關聯的機率。</span><span class="sxs-lookup"><span data-stu-id="8d361-156">An arrow represents a transition between two states and the probability that is associated with the transition.</span></span> <span data-ttu-id="8d361-157">若要減少圖形中的節點數目，請將滑動軸向上移。</span><span class="sxs-lookup"><span data-stu-id="8d361-157">To reduce the number of nodes in the graph, move the slider bar up.</span></span>  
  
     <span data-ttu-id="8d361-158">若要增加圖形中的節點數目，請將滑動軸向下移。</span><span class="sxs-lookup"><span data-stu-id="8d361-158">To increase the number of nodes in the graph, move the slider bar down.</span></span>  
  
     <span data-ttu-id="8d361-159">**新增專案**</span><span class="sxs-lookup"><span data-stu-id="8d361-159">**Add Items**</span></span>  
     <span data-ttu-id="8d361-160">開啟 [**選取要**轉譯的節點] 對話方塊，讓您可以選取要加入至圖形的新節點。</span><span class="sxs-lookup"><span data-stu-id="8d361-160">Opens the **Select Nodes to Render** dialog box so that you can select new nodes to add to the graph.</span></span>  
  
4.  <span data-ttu-id="8d361-161">您可以視需要將圖形變得簡單或詳細，並且加入註解，同時維持模型的連接。</span><span class="sxs-lookup"><span data-stu-id="8d361-161">You can make the graphs as simple or elaborate as you like, and add annotations, while staying connected to the model.</span></span>  
  
     <span data-ttu-id="8d361-162">[圖案預留位置]</span><span class="sxs-lookup"><span data-stu-id="8d361-162">[ art placeholder]</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="8d361-163">原本在舊版增益集中提供的反白顯示相依節點和其他捷徑功能表選項無法在 Office 2013 中運作。</span><span class="sxs-lookup"><span data-stu-id="8d361-163">Highlighting of dependent nodes and other shortcut menu options that were available in previous versions of the Add-Ins do not work in Office 2013.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d361-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d361-164">See Also</span></span>  
 [<span data-ttu-id="8d361-165">針對 Visio 資料採礦圖表進行疑難排解 &#40;SQL Server 資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="8d361-165">Troubleshooting Visio Data Mining Diagrams &#40;SQL Server Data Mining Add-ins&#41;</span></span>](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
