---
title: 叢集圖表逐步解說 (資料採礦增益集) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Visio shapes, cluster
- diagram, cluster
- shapes, data mining
- shapes, cluster
- data mining layout toolbar
ms.assetid: 761bef6a-37d4-4b19-944e-f2aadc75a242
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44ee8cce3cd2498d765c9b69e7f352b49cb0f115
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593690"
---
# <a name="cluster-diagram-walkthrough-data-mining-add-ins"></a><span data-ttu-id="073d2-102">叢集圖表逐步解說 (資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="073d2-102">Cluster Diagram Walkthrough (Data Mining Add-ins)</span></span>
  <span data-ttu-id="073d2-103">建立群集模型之後，您可以**使用 [叢集] 圖形將它**匯入 Visio，然後繼續自訂並增強配置。</span><span class="sxs-lookup"><span data-stu-id="073d2-103">After you have created a clustering model, you can import it into Visio using the **Cluster** shape and then continue to customize and enhance the layout.</span></span> <span data-ttu-id="073d2-104">**適用于 Visio 的資料採礦圖形**包含下列自訂控制項，可用來處理資料採礦圖表：</span><span class="sxs-lookup"><span data-stu-id="073d2-104">The **Data Mining Shapes for Visio** include the following custom controls for working with data mining diagrams:</span></span>  
  
-   <span data-ttu-id="073d2-105">叢集圖表的轉譯控制項</span><span class="sxs-lookup"><span data-stu-id="073d2-105">Rendering controls for the cluster diagram</span></span>  
  
     <span data-ttu-id="073d2-106">這些選項是在您將圖形放入 Visio 工作區時啟動的叢集**Wizard**的一部分。</span><span class="sxs-lookup"><span data-stu-id="073d2-106">These options are part of the **Cluster Wizard** that is launched when you drop a shape into the Visio workspace.</span></span>  
  
-   <span data-ttu-id="073d2-107">**資料採礦版面**組態工具欄</span><span class="sxs-lookup"><span data-stu-id="073d2-107">**Data Mining Layout** toolbar</span></span>  
  
     <span data-ttu-id="073d2-108">這些選項會加入至 Visio 工作區以協助您與資料採礦圖形互動。</span><span class="sxs-lookup"><span data-stu-id="073d2-108">These options are added to the Visio workspace to help you interact with the data mining shape.</span></span> <span data-ttu-id="073d2-109">這些選項會因您所使用的資料採礦模型類型而異。</span><span class="sxs-lookup"><span data-stu-id="073d2-109">The options are different depending on which type of data mining model you are using.</span></span>  
  
## <a name="build-a-cluster-diagram"></a><span data-ttu-id="073d2-110">建立叢集圖表</span><span class="sxs-lookup"><span data-stu-id="073d2-110">Build a Cluster Diagram</span></span>  
 <span data-ttu-id="073d2-111">這個逐步解說會示範如何在 Visio 中建立並自訂叢集圖表。</span><span class="sxs-lookup"><span data-stu-id="073d2-111">This walkthrough demonstrates how to build and customize a clustering diagram in Visio.</span></span>  
  
 <span data-ttu-id="073d2-112">若要依照步驟進行，您應該事先備妥叢集模型。</span><span class="sxs-lookup"><span data-stu-id="073d2-112">To follow along, you should have a clustering model already available.</span></span> <span data-ttu-id="073d2-113">如果您沒有模型，請使用 [叢集[] wizard &#40;適用于 Excel 的資料採礦增益集&#41;](cluster-wizard-data-mining-add-ins-for-excel.md) Wizard，並使用範例活頁簿中的訓練資料集，並使用所有預設值來建立模型。</span><span class="sxs-lookup"><span data-stu-id="073d2-113">If you do not have a model, use the [Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md) wizard and create a model using the Training data set in the sample workbook, using all the defaults.</span></span>  
  
#### <a name="use-the-cluster-visio-shape-wizard"></a><span data-ttu-id="073d2-114">使用叢集 Visio 圖形精靈</span><span class="sxs-lookup"><span data-stu-id="073d2-114">Use the Cluster Visio Shape Wizard</span></span>  
  
1.  <span data-ttu-id="073d2-115">如果您在 [**圖形**] 清單中看不到 [ **Microsoft 資料採礦圖形**]，請按一下 [**更多圖形**]，選取 [**開啟**樣板]，然後從預設安裝位置開啟範本。</span><span class="sxs-lookup"><span data-stu-id="073d2-115">If you do not see **Microsoft Data Mining Shapes** in the **Shapes** list, click **More Shapes**, select **Open Stencil**, and open the template from the default installation location.</span></span>  
  
     <span data-ttu-id="073d2-116">\<drive>： \Program files\Microsoft SQL Server 2012 DM 增益集</span><span class="sxs-lookup"><span data-stu-id="073d2-116">\<drive>:\Program files\Microsoft SQL Server 2012 DM Add-Ins</span></span>  
  
2.  <span data-ttu-id="073d2-117">**將 [叢集] 圖形拖曳**至頁面上。</span><span class="sxs-lookup"><span data-stu-id="073d2-117">Drag the **Cluster** shape onto the page.</span></span>  
  
3.  <span data-ttu-id="073d2-118">在 [叢集**Visio 圖形 Wizard]** 的 [歡迎使用] 頁面上，按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="073d2-118">On the welcome page of the **Cluster Visio Shape Wizard**, click **Next**.</span></span>  
  
4.  <span data-ttu-id="073d2-119">在叢集 Wizard 的 [**選取資料來源** **]** 頁面上，選擇 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 包含您想要視覺化之資料採礦模型的伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="073d2-119">On the **Select a Data Source** page of the **Cluster Wizard**, choose a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server that contains the data mining models you want to visualize.</span></span>  
  
5.  <span data-ttu-id="073d2-120">選取適當的 [採礦模型]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="073d2-120">Select an appropriate mining model, and click **Next**.</span></span>  
  
     <span data-ttu-id="073d2-121">若要確定您選擇群集模型，請檢查 [**屬性**] 窗格中的描述。</span><span class="sxs-lookup"><span data-stu-id="073d2-121">To make sure you choose a clustering model, review the description in the **Properties** pane.</span></span>  
  
6.  <span data-ttu-id="073d2-122">如果連線成功，在 [叢集**圖表的選項**] 頁面上，您可以決定要在 Visio 簡報中包含哪種類型的群集圖表：</span><span class="sxs-lookup"><span data-stu-id="073d2-122">If the connection is successful, on the page, **Options for cluster diagram**, you decide which type of cluster diagram to include in your Visio presentation:</span></span>  
  
     <span data-ttu-id="073d2-123">**只顯示群集形狀**</span><span class="sxs-lookup"><span data-stu-id="073d2-123">**Show cluster shapes only**</span></span>  
     <span data-ttu-id="073d2-124">這個選項會建立簡單的叢集圖表，其中每個叢集都由矩形或您所選擇的其他圖形代表。</span><span class="sxs-lookup"><span data-stu-id="073d2-124">This option creates a simple cluster diagram, with each cluster represented by a rectangle or other shape you choose</span></span>  
  
     <span data-ttu-id="073d2-125">**顯示有特性圖表的群集**</span><span class="sxs-lookup"><span data-stu-id="073d2-125">**Show clusters with characteristics chart**</span></span>  
     <span data-ttu-id="073d2-126">這個選項所建立的圖表與上述選項相同，但是圖形內部是描述叢集特性的長條圖。</span><span class="sxs-lookup"><span data-stu-id="073d2-126">This option creates the same chart as above, but inside the shapes are histograms that describe the characteristics of the cluster.</span></span>  
  
     <span data-ttu-id="073d2-127">![Visio 的叢集特性圖表範例](media/dm13-visio-cluster-samplecharshape.gif "Visio 的叢集特性圖表範例")</span><span class="sxs-lookup"><span data-stu-id="073d2-127">![Example of cluster characteristics chart in Visio](media/dm13-visio-cluster-samplecharshape.gif "Example of cluster characteristics chart in Visio")</span></span>  
  
     <span data-ttu-id="073d2-128">**顯示有辨識圖表的群集**</span><span class="sxs-lookup"><span data-stu-id="073d2-128">**Show clusters with discrimination chart**</span></span>  
     <span data-ttu-id="073d2-129">這個選項所建立的圖表與叢集圖表相同，但是改為列出目前叢集與其他叢集區別最強烈的特性。</span><span class="sxs-lookup"><span data-stu-id="073d2-129">This option creates the same chart as the cluster diagram, but instead lists the characteristics of the current cluster that most strongly distinguish it from other clusters.</span></span>  
  
     <span data-ttu-id="073d2-130">您可以在精靈建立圖表之後，以滑鼠右鍵按一下叢集並選取新的圖表類型，藉以切換成其他圖表類型。</span><span class="sxs-lookup"><span data-stu-id="073d2-130">You can switch to another chart type after the wizard has built the diagram, by right-clicking a cluster and selecting a new chart type.</span></span> <span data-ttu-id="073d2-131">現在，請選擇 [**顯示具有特性圖表的**叢集] 選項。</span><span class="sxs-lookup"><span data-stu-id="073d2-131">For now, choose the option, **Show clusters with characteristics chart**.</span></span>  
  
7.  <span data-ttu-id="073d2-132">將 [**圖表中的資料列數目**] 選項保留為5。</span><span class="sxs-lookup"><span data-stu-id="073d2-132">Leave the option, **Number of rows in the chart**, as 5.</span></span>  
  
     <span data-ttu-id="073d2-133">此選項不會變更模型中的群集數目;它只會限制可以顯示為每個叢集之功能的屬性數目。</span><span class="sxs-lookup"><span data-stu-id="073d2-133">This option doesn't change the number of clusters in the model; it simply limits the number of attributes that can be displayed as features of each cluster.</span></span>  
  
     <span data-ttu-id="073d2-134">不過，此選項會做為圖表資料的篩選，因此您稍後無法增加專案數。</span><span class="sxs-lookup"><span data-stu-id="073d2-134">However, the option acts as a filter on the chart data, so you can't increase the number of items later.</span></span>  
  
8.  <span data-ttu-id="073d2-135">按一下 [進階]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="073d2-135">Click **Advanced**.</span></span>  
  
     <span data-ttu-id="073d2-136">[叢集**選項**] 對話方塊可讓您自訂圖表中所使用之圖形的視覺外觀。</span><span class="sxs-lookup"><span data-stu-id="073d2-136">The **Cluster Options** dialog box is where you customize the visual appearance of shapes used in the diagram.</span></span> <span data-ttu-id="073d2-137">您可以變更用於圖形的色彩，以及用於叢集的圖形。</span><span class="sxs-lookup"><span data-stu-id="073d2-137">You can change the colors used in the graph, and the shape used for clusters.</span></span>  
  
     <span data-ttu-id="073d2-138">[**陰影變數**] 控制項無法在 Office 2013 中運作。</span><span class="sxs-lookup"><span data-stu-id="073d2-138">The **Shading Variable** control does not work in Office 2013.</span></span>  
  
     <span data-ttu-id="073d2-139">![按一下 [進階] 選擇形狀色彩](media/dm13-visio-clusteroptions-advanced.gif "按一下 [進階] 選擇形狀色彩")</span><span class="sxs-lookup"><span data-stu-id="073d2-139">![click Advanced to choose shape colors](media/dm13-visio-clusteroptions-advanced.gif "click Advanced to choose shape colors")</span></span>  
  
     <span data-ttu-id="073d2-140">**秘訣：** 有些色彩稍後可以使用 Visio 主題和圖形編輯控制項來改變。</span><span class="sxs-lookup"><span data-stu-id="073d2-140">**Tip:** Some colors can be altered later by using Visio themes and shape editing controls.</span></span> <span data-ttu-id="073d2-141">不過，Visio 佈景主題也會覆寫其中部分色彩選擇，因此我們建議您從預設色彩開始，逐漸套用變更。</span><span class="sxs-lookup"><span data-stu-id="073d2-141">However, Visio themes will also override some of these color selections, so we recommend starting with the default colors and gradually applying changes.</span></span>  
  
9. <span data-ttu-id="073d2-142">按一下 **[完成]** 以建立圖形。</span><span class="sxs-lookup"><span data-stu-id="073d2-142">Click **Finish** to create the graph.</span></span>  
  
     <span data-ttu-id="073d2-143">此精靈會從資料採礦模型中擷取資訊、轉譯圖形，並在每個叢集中填入屬性和值。</span><span class="sxs-lookup"><span data-stu-id="073d2-143">The wizard retrieves information from the data mining model, renders the shapes, and populates each cluster with attributes and values.</span></span>  
  
     <span data-ttu-id="073d2-144">![相依性網路](media/dm13-visiodepnet-defaultgraph.gif "相依性網路")</span><span class="sxs-lookup"><span data-stu-id="073d2-144">![a dependency network](media/dm13-visiodepnet-defaultgraph.gif "a dependency network")</span></span>  
  
## <a name="explore-and-modify-the-finished-diagram"></a><span data-ttu-id="073d2-145">探索和修改完成的圖表</span><span class="sxs-lookup"><span data-stu-id="073d2-145">Explore and Modify the Finished Diagram</span></span>  
 <span data-ttu-id="073d2-146">在圖表完成之後，您可以繼續使用 Visio 控制項來自訂外觀，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="073d2-146">After the diagram is complete, you can continue to customize the appearance using the Visio controls, as shown in the following example.</span></span>  
  
 <span data-ttu-id="073d2-147">![使用 Visio 自訂的叢集圖表](media/dm13-visio-clustercomplete1.gif "使用 Visio 自訂的叢集圖表")</span><span class="sxs-lookup"><span data-stu-id="073d2-147">![cluster diagram customized using Visio](media/dm13-visio-clustercomplete1.gif "cluster diagram customized using Visio")</span></span>  
  
 <span data-ttu-id="073d2-148">所有基本叢集圖形都由精靈產生。請使用下列工具來更新並個人化圖表：</span><span class="sxs-lookup"><span data-stu-id="073d2-148">All of the basic cluster shapes are generated by the wizard; use the following tools to update and personalize the diagram:</span></span>  
  
1.  <span data-ttu-id="073d2-149">拖曳 [叢集**選項**] 控制項中的滑杆，以篩選掉較弱的關聯性並簡化圖表。</span><span class="sxs-lookup"><span data-stu-id="073d2-149">Drag the slider in the **Cluster Options** control, to filter out weaker relationships and simplify the diagram.</span></span>  
  
2.  <span data-ttu-id="073d2-150">使用 [Visio**重新配置頁面**] 選項來試驗不同的叢集版面配置。</span><span class="sxs-lookup"><span data-stu-id="073d2-150">Use the Visio **Re-Layout Page** option to experiment with different cluster layouts.</span></span>  
  
3.  <span data-ttu-id="073d2-151">使用 [**設計**] 索引標籤上的 [**連接器**] 選項來變更連接器樣式，使線條不會跨越叢集。</span><span class="sxs-lookup"><span data-stu-id="073d2-151">Use the **Connectors** option on the **Design** tab to change the connector style to keep lines from crossing over clusters.</span></span>  
  
4.  <span data-ttu-id="073d2-152">按一下 [**增益集**] 功能區，然後顯示用來處理資料採礦圖表的其中一個自訂工具列：</span><span class="sxs-lookup"><span data-stu-id="073d2-152">Click the **Add-Ins** ribbon, and then display one of the custom toolbars used for working with data mining diagrams:</span></span>  
  
     <span data-ttu-id="073d2-153">**配置**</span><span class="sxs-lookup"><span data-stu-id="073d2-153">**Layout**</span></span>  
     <span data-ttu-id="073d2-154">最佳化叢集的排列方式以符合目前的頁面。</span><span class="sxs-lookup"><span data-stu-id="073d2-154">Optimizes the arrangement of clusters to fit in the current page.</span></span>  
  
     <span data-ttu-id="073d2-155">**調整頁面大小**</span><span class="sxs-lookup"><span data-stu-id="073d2-155">**Resize Page**</span></span>  
     <span data-ttu-id="073d2-156">此控制項適用於先前的 HTML 版本。</span><span class="sxs-lookup"><span data-stu-id="073d2-156">This control was intended for earlier HTML versions.</span></span> <span data-ttu-id="073d2-157">請改用 Visio 頁面大小調整控制項。</span><span class="sxs-lookup"><span data-stu-id="073d2-157">Use the Visio page resizing controls instead.</span></span>  
  
     <span data-ttu-id="073d2-158">**說明**</span><span class="sxs-lookup"><span data-stu-id="073d2-158">**Description**</span></span>  
     <span data-ttu-id="073d2-159">如果選取了叢集，按一下這個選項就會顯示有關叢集的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="073d2-159">If a cluster is selected, click this option to display details about the cluster.</span></span>  
  
     <span data-ttu-id="073d2-160">![按一下 [描述] 取得叢集的詳細資料](media/dm13-visio-cluster-description-control.gif "按一下 [描述] 取得叢集的詳細資料")</span><span class="sxs-lookup"><span data-stu-id="073d2-160">![click Description to get details about the cluster](media/dm13-visio-cluster-description-control.gif "click Description to get details about the cluster")</span></span>  
  
     <span data-ttu-id="073d2-161">**邊緣強度**</span><span class="sxs-lookup"><span data-stu-id="073d2-161">**Edge Strength**</span></span>  
     <span data-ttu-id="073d2-162">在連接叢集的線條上顯示信心分數。</span><span class="sxs-lookup"><span data-stu-id="073d2-162">Displays confidence scores on the lines connecting clusters.</span></span>  
  
     <span data-ttu-id="073d2-163">不過，如果您套用精靈產生之預設格式設定以外的任何特殊格式設定，包括部分背景，可能就不會顯示這些數字。</span><span class="sxs-lookup"><span data-stu-id="073d2-163">However, if you apply any special formatting other than the default generated by the wizard, including some backgrounds, these numbers might not be visible.</span></span>  
  
     <span data-ttu-id="073d2-164">**滑桿**</span><span class="sxs-lookup"><span data-stu-id="073d2-164">**Slider**</span></span>  
     <span data-ttu-id="073d2-165">篩選叢集之間的線條。</span><span class="sxs-lookup"><span data-stu-id="073d2-165">Filters the lines between clusters.</span></span> <span data-ttu-id="073d2-166">將滑動軸向上移就會移除最重要關聯以外的所有關聯。</span><span class="sxs-lookup"><span data-stu-id="073d2-166">Moving the slider up removes all but the most important associations.</span></span>  
  
     <span data-ttu-id="073d2-167">**陰影**</span><span class="sxs-lookup"><span data-stu-id="073d2-167">**Shading**</span></span>  
     <span data-ttu-id="073d2-168">此控制項無法在 Office 2013 中運作。</span><span class="sxs-lookup"><span data-stu-id="073d2-168">This control does not work in Office 2013.</span></span>  
  
5.  <span data-ttu-id="073d2-169">您可以使用 [Visio View] 功能區的 [工作**窗格]** 區域中的 [移動**流覽\*\*\*\*和縮放**] 控制項，將焦點放在一組叢集上，然後在圖表中四處移動。</span><span class="sxs-lookup"><span data-stu-id="073d2-169">Use the **Pan and Zoom** control, in the **Task Pane** area of the Visio **View** ribbon, to focus on a set of clusters and move around the diagram.</span></span>  
  
6.  <span data-ttu-id="073d2-170">以滑鼠右鍵按一下任何叢集，即可查看該叢集圖形特有的選項：</span><span class="sxs-lookup"><span data-stu-id="073d2-170">Right-click any cluster to see options specific to the cluster shape:</span></span>  
  
    -   <span data-ttu-id="073d2-171">變更圖表樣式。</span><span class="sxs-lookup"><span data-stu-id="073d2-171">Change the chart style.</span></span>  
  
    -   <span data-ttu-id="073d2-172">加入叢集特性圖表。</span><span class="sxs-lookup"><span data-stu-id="073d2-172">Add a cluster characteristics chart.</span></span>  
  
    -   <span data-ttu-id="073d2-173">加入叢集辨識圖表。</span><span class="sxs-lookup"><span data-stu-id="073d2-173">Add a cluster discrimination chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="073d2-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="073d2-174">See Also</span></span>  
 [<span data-ttu-id="073d2-175">針對 Visio 資料採礦圖表進行疑難排解 &#40;SQL Server 資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="073d2-175">Troubleshooting Visio Data Mining Diagrams &#40;SQL Server Data Mining Add-ins&#41;</span></span>](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
