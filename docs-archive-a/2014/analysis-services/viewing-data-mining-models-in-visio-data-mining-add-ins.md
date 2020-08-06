---
title: 在 Visio (資料採礦增益集) 中查看資料採礦模型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- diagram, modifying
- templates [Visio]
- shapes, data mining
- diagram
ms.assetid: 5841adea-6650-4fae-8526-26af33edbede
author: minewiskan
ms.author: owend
ms.openlocfilehash: f3c1e63c058295b93e2562c64a6df90a30273a10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594197"
---
# <a name="viewing-data-mining-models-in-visio-data-mining-add-ins"></a><span data-ttu-id="b4120-102">在 Visio 中檢視資料採礦模型 (資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="b4120-102">Viewing Data Mining Models in Visio (Data Mining Add-ins)</span></span>
  <span data-ttu-id="b4120-103">資料採礦的 Visio 圖形可讓您連接到伺服器並建立代表現有資料採礦模型的圖表。</span><span class="sxs-lookup"><span data-stu-id="b4120-103">The Visio shapes for data mining let you connect to a server and create a diagram representing an existing data mining model.</span></span> <span data-ttu-id="b4120-104">然後，您可以使用 Visio 控制項來自訂圖表，但是也可以向下鑽研資料、公開部分基礎統計資料，以及使用基礎模型。</span><span class="sxs-lookup"><span data-stu-id="b4120-104">The diagrams can then be customized using Visio controls, but you can also drill down into data, expose some of the underlying statistics, and work with the underlying model.</span></span>  
  
## <a name="building-a-model-diagram"></a><span data-ttu-id="b4120-105">建立模型圖表</span><span class="sxs-lookup"><span data-stu-id="b4120-105">Building a Model Diagram</span></span>  
 <span data-ttu-id="b4120-106">當您開啟包含用於資料採礦之 Visio 圖形的檔案時，[**圖形**] 窗格會顯示下列圖形。</span><span class="sxs-lookup"><span data-stu-id="b4120-106">When you open the file containing the Visio shapes for data mining, the **Shapes** pane shows the following shapes.</span></span>  
  
 <span data-ttu-id="b4120-107">如果您在開啟 Visio 時沒有看見資料採礦圖形，可以從安裝資料夾開啟範本檔案。</span><span class="sxs-lookup"><span data-stu-id="b4120-107">If you do not see the data mining shapes when you open Visio, open the template file from the installation folder.</span></span>  
  
 <span data-ttu-id="b4120-108">![DM](media/dm-stencil.gif "DM")</span><span class="sxs-lookup"><span data-stu-id="b4120-108">![DM](media/dm-stencil.gif "DM")</span></span>  
  
 <span data-ttu-id="b4120-109">若要使用圖形，請將它拖曳至頁面。</span><span class="sxs-lookup"><span data-stu-id="b4120-109">To use a shape, drag it to the page.</span></span> <span data-ttu-id="b4120-110">每個圖形會開啟不同精靈，以協助您選取來源資料、設定特定圖表類型的選項，以及指定陰影和其他顯示選項。</span><span class="sxs-lookup"><span data-stu-id="b4120-110">Each of the shapes opens a different wizard, which helps you select source data, set options for the specific diagram type, and specify shading and other display options.</span></span>  
  
 <span data-ttu-id="b4120-111">下表列出您可以搭配每一種圖表類型使用的模型類型。</span><span class="sxs-lookup"><span data-stu-id="b4120-111">The following table lists the types of models that you can use with each type of diagram.</span></span>  
  
|<span data-ttu-id="b4120-112">Visio 圖形</span><span class="sxs-lookup"><span data-stu-id="b4120-112">Visio shape</span></span>|<span data-ttu-id="b4120-113">支援的模型</span><span class="sxs-lookup"><span data-stu-id="b4120-113">Supported models</span></span>|  
|-----------------|----------------------|  
|<span data-ttu-id="b4120-114">決策樹</span><span class="sxs-lookup"><span data-stu-id="b4120-114">Decision Tree</span></span>|<span data-ttu-id="b4120-115">請針對以決策樹或線性迴歸演算法為基礎的模型使用此圖形。</span><span class="sxs-lookup"><span data-stu-id="b4120-115">Use this shape for models based on the decision tree or linear regression algorithms.</span></span>|  
|<span data-ttu-id="b4120-116">相依性網路</span><span class="sxs-lookup"><span data-stu-id="b4120-116">Dependency Network</span></span>|<span data-ttu-id="b4120-117">請針對以下列任一個演算法為基礎的模型使用此圖形：貝氏機率分類、決策樹或關聯規則。</span><span class="sxs-lookup"><span data-stu-id="b4120-117">Use this shape for models based on any of the following algorithms: Naive Bayes, Decision Trees, or Association Rules.</span></span>|  
|<span data-ttu-id="b4120-118">叢集</span><span class="sxs-lookup"><span data-stu-id="b4120-118">Cluster</span></span>|<span data-ttu-id="b4120-119">請針對以叢集演算法為基礎的模型使用此圖形。</span><span class="sxs-lookup"><span data-stu-id="b4120-119">Use this shape for models based on clustering algorithms.</span></span>|  
  
 <span data-ttu-id="b4120-120">根據採礦模型中的資料類型，精靈可能會提供不同選項。</span><span class="sxs-lookup"><span data-stu-id="b4120-120">Depending on the type of data in your mining model, the wizard may offer different options.</span></span> <span data-ttu-id="b4120-121">例如，包含連續數字之資料行的視覺效果方式與類別變數有所不同。</span><span class="sxs-lookup"><span data-stu-id="b4120-121">For example, columns that contain continuous numbers are visualized differently than categorical variables.</span></span>  
  
## <a name="working-with-completed-shapes"></a><span data-ttu-id="b4120-122">使用已完成圖形</span><span class="sxs-lookup"><span data-stu-id="b4120-122">Working with Completed Shapes</span></span>  
 <span data-ttu-id="b4120-123">圖表完成之後，您可以用它來瀏覽資料採礦模型或增強圖表以用於簡報中。</span><span class="sxs-lookup"><span data-stu-id="b4120-123">After the diagram is complete, you can use it to browse the data mining model or enhance the diagram for use in presentations.</span></span>  
  
### <a name="visio-menus"></a><span data-ttu-id="b4120-124">Visio 功能表</span><span class="sxs-lookup"><span data-stu-id="b4120-124">Visio Menus</span></span>  
 <span data-ttu-id="b4120-125">Visio 提供了各種轉譯控制項、佈景主題和捷徑功能表來協助您增強圖表。</span><span class="sxs-lookup"><span data-stu-id="b4120-125">Visio provides a variety of rendering controls, themes, and shortcut menus to help enhance a diagram.</span></span>  
  
-   <span data-ttu-id="b4120-126">使用 Visio 佈景主題來更改圖表色彩。</span><span class="sxs-lookup"><span data-stu-id="b4120-126">Use Visio themes to alter diagram colors.</span></span>  
  
-   <span data-ttu-id="b4120-127">變更連接線或圖表配置。</span><span class="sxs-lookup"><span data-stu-id="b4120-127">Change connectors or diagram layout.</span></span>  
  
### <a name="data-mining-menus"></a><span data-ttu-id="b4120-128">資料採礦功能表</span><span class="sxs-lookup"><span data-stu-id="b4120-128">Data Mining Menus</span></span>  
 <span data-ttu-id="b4120-129">這些工具列和功能表項目都是由每個圖形或模型類型專用的增益集提供的。</span><span class="sxs-lookup"><span data-stu-id="b4120-129">These toolbars and menu items are provided by the add-ins that are specific to each shape or model type</span></span>  
  
-   <span data-ttu-id="b4120-130">每個圖表類型都有圖形的快速鍵功能表，可讓您存取特殊選項。</span><span class="sxs-lookup"><span data-stu-id="b4120-130">Each diagram type has a shortcut menu for the shape that lets you access special options.</span></span> <span data-ttu-id="b4120-131">雖然這個功能表中的許多選項是所有 Visio 圖形共有的，但有些選項卻是資料採礦範本特有的選項。</span><span class="sxs-lookup"><span data-stu-id="b4120-131">Although many options in this menu are common to all Visio shapes, some options are unique to the data mining templates</span></span>  
  
     <span data-ttu-id="b4120-132">例如，在決策樹圖表中，您可以按一下個別節點，然後摺疊子節點讓圖表更簡單，或將子節點移至另一個頁面。</span><span class="sxs-lookup"><span data-stu-id="b4120-132">For example, in a decision tree diagram, you can click an individual node and then collapse the child nodes to make the diagram simpler, or move child nodes to a separate page.</span></span>  
  
-   <span data-ttu-id="b4120-133">因為圖形已繫結至模型資料，所以您也可以使用圖表來進行一些瀏覽動作：</span><span class="sxs-lookup"><span data-stu-id="b4120-133">Because the shape is bound to the model data, you can also do some amount of exploration using the diagram:</span></span>  
  
     <span data-ttu-id="b4120-134">篩選顯示的節點，或者變更樹狀的層級或圖形的深度。</span><span class="sxs-lookup"><span data-stu-id="b4120-134">Filter the nodes that are displayed, or change the level of the tree or depth of the graph.</span></span>  
  
     <span data-ttu-id="b4120-135">放大特定部分、搜尋包含特定屬性的節點，或依據邊緣 (機率) 來篩選相依性圖形。</span><span class="sxs-lookup"><span data-stu-id="b4120-135">Zoom in on specific sections, search for nodes that contain a certain attribute, or filter a dependency graph by its edges (probability).</span></span>  
  
## <a name="walkthroughs"></a><span data-ttu-id="b4120-136">逐步解說</span><span class="sxs-lookup"><span data-stu-id="b4120-136">Walkthroughs</span></span>  
 <span data-ttu-id="b4120-137">如需如何使用及解譯已完成圖表的範例，請參閱以下這些主題：</span><span class="sxs-lookup"><span data-stu-id="b4120-137">For examples of how to work with and interpret a completed diagram, see these topics:</span></span>  
  
 [<span data-ttu-id="b4120-138">叢集圖表逐步解說</span><span class="sxs-lookup"><span data-stu-id="b4120-138">Cluster Diagram Walkthrough</span></span>](cluster-diagram-walkthrough-data-mining-add-ins.md)  
  
 [<span data-ttu-id="b4120-139">相依性網路圖表逐步解說</span><span class="sxs-lookup"><span data-stu-id="b4120-139">Dependency Net Diagram Walkthrough</span></span>](dependency-network-diagram-walkthrough-data-mining-add-ins.md)  
  
 [<span data-ttu-id="b4120-140">決策樹圖表逐步解說</span><span class="sxs-lookup"><span data-stu-id="b4120-140">Decision Tree Diagram Walkthrough</span></span>](decision-tree-diagram-walkthrough-data-mining-add-ins.md)  
  
## <a name="see-also"></a><span data-ttu-id="b4120-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4120-141">See Also</span></span>  
 [<span data-ttu-id="b4120-142">在 Excel 中流覽模型 &#40;SQL Server 資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="b4120-142">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
