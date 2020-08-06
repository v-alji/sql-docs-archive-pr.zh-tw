---
title: 新增、變更或刪除地圖或地圖圖層 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10526"
- sql12.rtp.rptdesigner.maptilelayerproperties.general.f1
- "10529"
- "10525"
- "10535"
- sql12.rtp.rptdesigner.mappolygonlayerproperties.general.f1
- sql12.rtp.rptdesigner.shared.layervisibility.f1
- sql12.rtp.rptdesigner.mappointlayerproperties.general.f1
- sql12.rtp.rptdesigner.shared.layerfilters.f1
- "10524"
- sql12.rtp.rptdesigner.maplayerproperties.general.f1
- sql12.rtp.rptdesigner.maplinelayerproperties.general.f1
- "10532"
- "10528"
- "10527"
- sql12.rtp.rptdesigner.maplayerproperties.analyticaldata.f1
ms.assetid: 6e89815e-187e-45bf-bf63-3d5c4a246360
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4e9fd178d36ee3322c0bd94dd44d621439139b71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595768"
---
# <a name="add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs"></a><span data-ttu-id="6c082-102">加入、變更或刪除地圖或地圖圖層 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="6c082-102">Add, Change, or Delete a Map or Map Layer (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6c082-103">地圖是圖層的集合。</span><span class="sxs-lookup"><span data-stu-id="6c082-103">A map is a collection of layers.</span></span> <span data-ttu-id="6c082-104">將地圖加入至報表時，您會定義第一個圖層。</span><span class="sxs-lookup"><span data-stu-id="6c082-104">When you add a map to a report, you define the first layer.</span></span> <span data-ttu-id="6c082-105">您可以使用地圖圖層精靈建立其他圖層。</span><span class="sxs-lookup"><span data-stu-id="6c082-105">You can create additional layers by using the map layer wizard.</span></span>  
  
 <span data-ttu-id="6c082-106">加入、移除或變更圖層選項的一個最簡單的方法，就是使用地圖圖層精靈。</span><span class="sxs-lookup"><span data-stu-id="6c082-106">The easiest way to add, remove, or change options for a layer is to use the map layer wizard.</span></span> <span data-ttu-id="6c082-107">您也可以從 [地圖] 窗格手動變更選項。</span><span class="sxs-lookup"><span data-stu-id="6c082-107">You can also change options manually from the Map pane.</span></span> <span data-ttu-id="6c082-108">若要顯示 [地圖]  窗格，按一下報表設計介面上的地圖。</span><span class="sxs-lookup"><span data-stu-id="6c082-108">To display the **Map** pane, click in the map on the report design surface.</span></span> <span data-ttu-id="6c082-109">下圖顯示此窗格的幾個部分：</span><span class="sxs-lookup"><span data-stu-id="6c082-109">The following figure displays the parts of the pane:</span></span>  
  
 <span data-ttu-id="6c082-110">![rsMapLayerZone](../media/rsmaplayerzone.gif "rsMapLayerZone")</span><span class="sxs-lookup"><span data-stu-id="6c082-110">![rsMapLayerZone](../media/rsmaplayerzone.gif "rsMapLayerZone")</span></span>  
  
 <span data-ttu-id="6c082-111">地圖圖層是以它們顯示在 [地圖] 窗格中的順序，由下而上繪製。</span><span class="sxs-lookup"><span data-stu-id="6c082-111">Map layers are drawn from bottom to top in the order that they appear in the Map pane.</span></span> <span data-ttu-id="6c082-112">在上圖中，圖格圖層會最先繪製，而多邊形圖層則是最後繪製。</span><span class="sxs-lookup"><span data-stu-id="6c082-112">In the previous figure, the tile layer is drawn first and the polygon layer is drawn last.</span></span> <span data-ttu-id="6c082-113">稍後繪製的圖層可能會隱藏圖層上先前繪製的地圖元素。</span><span class="sxs-lookup"><span data-stu-id="6c082-113">Layers that are drawn later might hide map elements on layers that are drawn earlier.</span></span> <span data-ttu-id="6c082-114">您可以使用 [地圖] 窗格工具列上的方向鍵來變更圖層的順序。</span><span class="sxs-lookup"><span data-stu-id="6c082-114">You can change the order of layers by using the arrow keys on the Map pane toolbar.</span></span> <span data-ttu-id="6c082-115">若要顯示或隱藏圖層，請切換可見性圖示。</span><span class="sxs-lookup"><span data-stu-id="6c082-115">To show or hide layers, toggle the visibility icon.</span></span> <span data-ttu-id="6c082-116">您可以在 `Visibility` [**圖層資料**屬性] 對話方塊的頁面上，變更圖層的透明度。</span><span class="sxs-lookup"><span data-stu-id="6c082-116">You can change the transparency of a layer on the `Visibility` page of the **Layer Data** properties dialog box.</span></span>  
  
 <span data-ttu-id="6c082-117">下表顯示 [地圖]  窗格的工具列圖示。</span><span class="sxs-lookup"><span data-stu-id="6c082-117">The following table displays the toolbar icons for the **Map** pane.</span></span>  
  
|<span data-ttu-id="6c082-118">符號</span><span class="sxs-lookup"><span data-stu-id="6c082-118">Symbol</span></span>|<span data-ttu-id="6c082-119">描述</span><span class="sxs-lookup"><span data-stu-id="6c082-119">Description</span></span>|<span data-ttu-id="6c082-120">使用時機</span><span class="sxs-lookup"><span data-stu-id="6c082-120">When to use</span></span>|  
|------------|-----------------|-----------------|  
|<span data-ttu-id="6c082-121">![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard")</span><span class="sxs-lookup"><span data-stu-id="6c082-121">![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard")</span></span>|<span data-ttu-id="6c082-122">地圖圖層精靈</span><span class="sxs-lookup"><span data-stu-id="6c082-122">Map Layer Wizard</span></span>|<span data-ttu-id="6c082-123">若要使用精靈加入圖層，按一下 [新增圖層精靈]  。</span><span class="sxs-lookup"><span data-stu-id="6c082-123">To add a layer by using a wizard, click **New layer wizard**.</span></span>|  
|<span data-ttu-id="6c082-124">![rs_IconMapAddLayer](../../tutorials/media/rs-iconmapaddlayer.gif "rs_IconMapAddLayer")</span><span class="sxs-lookup"><span data-stu-id="6c082-124">![rs_IconMapAddLayer](../../tutorials/media/rs-iconmapaddlayer.gif "rs_IconMapAddLayer")</span></span>|<span data-ttu-id="6c082-125">加入圖層</span><span class="sxs-lookup"><span data-stu-id="6c082-125">Add Layer</span></span>|<span data-ttu-id="6c082-126">若要手動加入圖層，按一下 [加入圖層]  ，然後按一下要加入之地圖圖層的類型。</span><span class="sxs-lookup"><span data-stu-id="6c082-126">To manually add a layer, click **Add Layer**, and then click the type of map layer to add.</span></span>|  
|<span data-ttu-id="6c082-127">![rs_IconMapPolygonLayer](../media/rs-iconmappolygonlayer.gif "rs_IconMapPolygonLayer")</span><span class="sxs-lookup"><span data-stu-id="6c082-127">![rs_IconMapPolygonLayer](../media/rs-iconmappolygonlayer.gif "rs_IconMapPolygonLayer")</span></span>|<span data-ttu-id="6c082-128">多邊形圖層</span><span class="sxs-lookup"><span data-stu-id="6c082-128">Polygon Layer</span></span>|<span data-ttu-id="6c082-129">加入地圖圖層，此圖層會顯示以多組多邊形座標為基礎的區域或形狀。</span><span class="sxs-lookup"><span data-stu-id="6c082-129">Add a map layer that displays areas or shapes that are based sets of polygon coordinates.</span></span>|  
|<span data-ttu-id="6c082-130">![rs_IconMapLineLayer](../media/rs-iconmaplinelayer.gif "rs_IconMapLineLayer")</span><span class="sxs-lookup"><span data-stu-id="6c082-130">![rs_IconMapLineLayer](../media/rs-iconmaplinelayer.gif "rs_IconMapLineLayer")</span></span>|<span data-ttu-id="6c082-131">線條圖層</span><span class="sxs-lookup"><span data-stu-id="6c082-131">Line Layer</span></span>|<span data-ttu-id="6c082-132">加入地圖圖層，此圖層會顯示以多組線條座標為基礎的路徑或路線。</span><span class="sxs-lookup"><span data-stu-id="6c082-132">Add a map layer that displays paths or routes that are based on sets of line coordinates.</span></span>|  
|<span data-ttu-id="6c082-133">![rs_IconMapPointLayer](../media/rs-iconmappointlayer.gif "rs_IconMapPointLayer")</span><span class="sxs-lookup"><span data-stu-id="6c082-133">![rs_IconMapPointLayer](../media/rs-iconmappointlayer.gif "rs_IconMapPointLayer")</span></span>|<span data-ttu-id="6c082-134">點圖層</span><span class="sxs-lookup"><span data-stu-id="6c082-134">Point Layer</span></span>|<span data-ttu-id="6c082-135">加入地圖圖層，此圖層會顯示以多組點座標為基礎的位置。</span><span class="sxs-lookup"><span data-stu-id="6c082-135">Add a map layer that displays locations that are based on sets of point coordinates.</span></span>|  
|<span data-ttu-id="6c082-136">![rs_IconMapTileLayer](../media/rs-iconmaptilelayer.gif "rs_IconMapTileLayer")</span><span class="sxs-lookup"><span data-stu-id="6c082-136">![rs_IconMapTileLayer](../media/rs-iconmaptilelayer.gif "rs_IconMapTileLayer")</span></span>|<span data-ttu-id="6c082-137">影像分割圖層</span><span class="sxs-lookup"><span data-stu-id="6c082-137">Tile Layer</span></span>|<span data-ttu-id="6c082-138">加入地圖圖層，此圖層會顯示對應至檢視區所定義之目前地圖檢視區域的 Bing 地圖底圖。</span><span class="sxs-lookup"><span data-stu-id="6c082-138">Add a map layer that displays Bing Map tiles that correspond to the current map view area that is defined by the viewport.</span></span>|  
  
 <span data-ttu-id="6c082-139">[地圖] 窗格的底部為地圖檢視區域。</span><span class="sxs-lookup"><span data-stu-id="6c082-139">At the bottom of the Map pane is the Map view area.</span></span> <span data-ttu-id="6c082-140">若要變更地圖的置中或縮放選項，請使用方向鍵調整檢視置中，並使用滑動軸調整縮放層級。</span><span class="sxs-lookup"><span data-stu-id="6c082-140">To change the center or zoom options for the map, use the arrow keys to adjust the view center and the slider to adjust the zoom level.</span></span>  
  
 <span data-ttu-id="6c082-141">如需圖層的詳細資訊，請參閱 [地圖 &#40;報表產生器及 SSRS&#41;](maps-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="6c082-141">For more information about layers, see [Maps &#40;Report Builder and SSRS&#41;](maps-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="to-add-a-layer-from-the-map-layer-wizard"></a><a name="AddLayer"></a> <span data-ttu-id="6c082-142">從地圖圖層精靈加入圖層</span><span class="sxs-lookup"><span data-stu-id="6c082-142">To add a layer from the map layer wizard</span></span>  
  
-   <span data-ttu-id="6c082-143">從功能區中，按一下 [插入]  功能表上的 [地圖]  ，然後按一下 [地圖精靈]  。</span><span class="sxs-lookup"><span data-stu-id="6c082-143">From the Ribbon, on the **Insert** menu, click **Map**, and then click **Map Wizard.**</span></span> <span data-ttu-id="6c082-144">此精靈可讓您將圖層加入至現有的地圖。</span><span class="sxs-lookup"><span data-stu-id="6c082-144">The wizard enables you to add a layer to the existing map.</span></span> <span data-ttu-id="6c082-145">地圖精靈與地圖圖層精靈的大部分精靈頁面都相同。</span><span class="sxs-lookup"><span data-stu-id="6c082-145">Most wizard pages are identical between the map wizard and the map layer wizard.</span></span>  
  
     <span data-ttu-id="6c082-146">如需詳細資訊，請參閱 [地圖精靈與地圖圖層精靈 &#40;報表產生器及 SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="6c082-146">For more information, see [Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md).</span></span>  

##  <a name="to-change-options-for-a-layer-by-using-the-map-layer-wizard"></a><a name="ChangeLayer"></a> <span data-ttu-id="6c082-147">使用地圖圖層精靈來變更圖層的選項</span><span class="sxs-lookup"><span data-stu-id="6c082-147">To change options for a layer by using the map layer wizard</span></span>  
  
-   <span data-ttu-id="6c082-148">執行地圖圖層精靈。</span><span class="sxs-lookup"><span data-stu-id="6c082-148">Run the map layer wizard.</span></span> <span data-ttu-id="6c082-149">這個精靈可讓您變更您使用地圖圖層精靈所建立的圖層選項。</span><span class="sxs-lookup"><span data-stu-id="6c082-149">This wizard enables you to change options for a layer that you created by using the map layer wizard.</span></span> <span data-ttu-id="6c082-150">在 [地圖] 窗格中，以滑鼠右鍵按一下圖層，然後在工具列上按一下圖層精靈按鈕 (![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard"))。</span><span class="sxs-lookup"><span data-stu-id="6c082-150">In the Map pane, right-click the layer, and on the toolbar, click the layer wizard button (![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard")).</span></span>  
  
     <span data-ttu-id="6c082-151">如需詳細資訊，請參閱 [地圖精靈與地圖圖層精靈 &#40;報表產生器及 SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="6c082-151">For more information, see [Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md).</span></span>  

##  <a name="to-add-a-point-line-or-polygon-layer-from-the-map-pane-toolbar"></a><a name="AddVectorLayer"></a> <span data-ttu-id="6c082-152">從 [圖層] 窗格工具列加入點、線條或多邊形圖層</span><span class="sxs-lookup"><span data-stu-id="6c082-152">To add a point, line, or polygon layer from the Map pane toolbar</span></span>  
  
1.  <span data-ttu-id="6c082-153">按一下地圖，直到 [圖層] 窗格出現為止。</span><span class="sxs-lookup"><span data-stu-id="6c082-153">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="6c082-154">在工具列上，按一下 [新增圖層]  按鈕，然後從下拉式清單中按一下您要新增的圖層類型：[點]  、[線條]  或 [多邊形]  。</span><span class="sxs-lookup"><span data-stu-id="6c082-154">On the toolbar, click the **Add Layer** button, and from the drop-down list, click the type of layer that you want to add: **Point**, **Line**, or **Polygon**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6c082-155">雖然您可以手動加入地圖圖層並加以設定，我們建議您最好使用地圖圖層精靈來新增圖層。</span><span class="sxs-lookup"><span data-stu-id="6c082-155">Although you can add a map layer and configure it manually, we recommend that you use the map layer wizard to add new layers.</span></span> <span data-ttu-id="6c082-156">若要在 [地圖] 窗格工具列啟動精露，請按一下圖層精靈按鈕 (![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard"))。</span><span class="sxs-lookup"><span data-stu-id="6c082-156">To launch the wizard from the Map pane toolbar, click the layer wizard button (![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard")).</span></span>  
  
3.  <span data-ttu-id="6c082-157">以滑鼠右鍵按一下圖層，然後按一下 [圖層資料]  。</span><span class="sxs-lookup"><span data-stu-id="6c082-157">Right-click the layer, and then click **Layer Data**.</span></span>  
  
4.  <span data-ttu-id="6c082-158">在 [使用以下來源的空間資料]  中，選取空間資料的來源。</span><span class="sxs-lookup"><span data-stu-id="6c082-158">In **Use spatial data from**, select the source of spatial data.</span></span> <span data-ttu-id="6c082-159">這些選項會隨著您選取的項目而不同。</span><span class="sxs-lookup"><span data-stu-id="6c082-159">Options vary based on your selection.</span></span>  
  
     <span data-ttu-id="6c082-160">如果您想要從此圖層上的報表視覺化分析資料，請執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="6c082-160">If you want to visualize analytical from your report on this layer, do the following:</span></span>  
  
    1.  <span data-ttu-id="6c082-161">按一下 **[分析資料]** 。</span><span class="sxs-lookup"><span data-stu-id="6c082-161">Click **Analytical data**.</span></span>  
  
    2.  <span data-ttu-id="6c082-162">在 [分析資料集]  中，按一下其中包含分析資料與符合欄位之資料集的名稱，來建立分析資料與空間資料之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="6c082-162">In **Analytical dataset**, click the name of the dataset that contains analytical data and the match fields to build a relationship between analytical and spatial data.</span></span>  
  
    3.  <span data-ttu-id="6c082-163">按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="6c082-163">Click **Add**.</span></span>  
  
    4.  <span data-ttu-id="6c082-164">從空間資料集輸入符合欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="6c082-164">Type the name of the match field from the spatial dataset.</span></span>  
  
    5.  <span data-ttu-id="6c082-165">從分析資料集輸入符合欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="6c082-165">Type the name of the match field from the analytical dataset.</span></span>  
  
     <span data-ttu-id="6c082-166">如需連結空間和分析資料的詳細資訊，請參閱[自訂地圖或地圖圖層的資料和顯示 &#40;報表產生器及 SSRS&#41;](customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="6c082-166">For more information about linking spatial and analytical data, see [Customize the Data and Display of a Map or Map Layer &#40;Report Builder and SSRS&#41;](customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-filter-analytical-data-for-the-layer"></a><a name="FilterAnalyticalData"></a> <span data-ttu-id="6c082-167">篩選圖層的分析資料</span><span class="sxs-lookup"><span data-stu-id="6c082-167">To filter analytical data for the layer</span></span>  
  
1.  <span data-ttu-id="6c082-168">按一下地圖，直到 [圖層] 窗格出現為止。</span><span class="sxs-lookup"><span data-stu-id="6c082-168">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="6c082-169">以滑鼠右鍵按一下 [地圖] 窗格中的圖層，然後按一下 [圖層資料]  。</span><span class="sxs-lookup"><span data-stu-id="6c082-169">Right-click the layer in the Map pane, and then click  **Layer Data**.</span></span>  
  
3.  <span data-ttu-id="6c082-170">按一下 **[篩選]** 。</span><span class="sxs-lookup"><span data-stu-id="6c082-170">Click **Filters**.</span></span>  
  
4.  <span data-ttu-id="6c082-171">定義篩選方程式，以限制用於地圖顯示的分析資料。</span><span class="sxs-lookup"><span data-stu-id="6c082-171">Define a filter equation to limit the analytical data that is used in the map display.</span></span> <span data-ttu-id="6c082-172">如需詳細資訊，請參閱[篩選、分組和排序資料 &#40;報表產生器及&#41;](filter-equation-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="6c082-172">For more information, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md).</span></span>  

##  <a name="to-control-point-properties-for-a-point-layer-or-for-polygon-center-points"></a><a name="PointProperties"></a> <span data-ttu-id="6c082-173">控制點圖層或多邊形中心點的點屬性</span><span class="sxs-lookup"><span data-stu-id="6c082-173">To control point properties for a point layer or for polygon center points</span></span>  
  
1.  <span data-ttu-id="6c082-174">選取 [地圖點屬性]  對話方塊上的 [一般]  來變更下列地圖元素的標籤、工具提示和標記類型選項：</span><span class="sxs-lookup"><span data-stu-id="6c082-174">Select **General** on the **Map Point Properties** dialog box to change label, tooltip, and marker type options for the following map elements:</span></span>  
  
    -   <span data-ttu-id="6c082-175">點圖層上的所有動態或內嵌的點。</span><span class="sxs-lookup"><span data-stu-id="6c082-175">All dynamic or embedded points on a point layer.</span></span> <span data-ttu-id="6c082-176">點的色彩規則、大小規則與標記類型規則會覆寫這些選項。</span><span class="sxs-lookup"><span data-stu-id="6c082-176">Color rules, size rules, and marker type rules for points override these options.</span></span> <span data-ttu-id="6c082-177">若要覆寫特定內嵌點的選項，請使用 [地圖內嵌點屬性對話方塊、標記](../map-embedded-point-properties-dialog-box-marker.md) 頁面。</span><span class="sxs-lookup"><span data-stu-id="6c082-177">To override options for a specific embedded point, use the [Map Embedded Point Properties Dialog Box, Marker](../map-embedded-point-properties-dialog-box-marker.md) page.</span></span>  
  
    -   <span data-ttu-id="6c082-178">在多邊形圖層上，所有動態或內嵌之多邊形的中心點。</span><span class="sxs-lookup"><span data-stu-id="6c082-178">The center point for all dynamic or embedded polygons on a polygon layer.</span></span> <span data-ttu-id="6c082-179">中心點的色彩規則、大小規則與標記類型規則會覆寫這些選項。</span><span class="sxs-lookup"><span data-stu-id="6c082-179">Color rules, size rules, and marker type rules for center points override these options.</span></span> <span data-ttu-id="6c082-180">若要覆寫特定中心點的選項，請使用 [地圖內嵌點屬性對話方塊、標記](../map-embedded-point-properties-dialog-box-marker.md) 頁面。</span><span class="sxs-lookup"><span data-stu-id="6c082-180">To override options for a specific center point, use the [Map Embedded Point Properties Dialog Box, Marker](../map-embedded-point-properties-dialog-box-marker.md) page.</span></span>  

##  <a name="to-specify-embedded-data-as-a-source-of-spatial-data"></a><a name="Embedded"></a> <span data-ttu-id="6c082-181">將內嵌資料指定為空間資料的來源</span><span class="sxs-lookup"><span data-stu-id="6c082-181">To specify embedded data as a source of spatial data</span></span>  
  
1.  <span data-ttu-id="6c082-182">按一下地圖，直到 [圖層] 窗格出現為止。</span><span class="sxs-lookup"><span data-stu-id="6c082-182">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="6c082-183">以滑鼠右鍵按一下圖層，然後按一下 [圖層資料]  。</span><span class="sxs-lookup"><span data-stu-id="6c082-183">Right-click the layer, and then click **Layer Data**.</span></span>  
  
3.  <span data-ttu-id="6c082-184">在 [使用以下來源的空間資料]  中，選取 [內嵌在報表中的資料]  。</span><span class="sxs-lookup"><span data-stu-id="6c082-184">In **Use spatial data from**, select **Data embedded in report**.</span></span>  
  
4.  <span data-ttu-id="6c082-185">若要從現有的報表載入地圖項目，或以 ESRI 檔案為基礎建立地圖項目，按一下 [瀏覽]  ，並指向該檔案，然後按一下 [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="6c082-185">To load map elements from an existing report or to create map elements based on an ESRI file, click **Browse**, point to the file, and then click **Open**.</span></span> <span data-ttu-id="6c082-186">地圖元素便會內嵌在此報表定義中。</span><span class="sxs-lookup"><span data-stu-id="6c082-186">The map elements are embedded in this report definition.</span></span> <span data-ttu-id="6c082-187">您所指向的空間資料必須符合圖層類型。</span><span class="sxs-lookup"><span data-stu-id="6c082-187">The spatial data that you point to must match the layer type.</span></span> <span data-ttu-id="6c082-188">例如，若是點圖層，您必須指向指定點座標組的空間資料。</span><span class="sxs-lookup"><span data-stu-id="6c082-188">For example, for a point layer, you must point to spatial data that specifies sets of point coordinates.</span></span>  
  
5.  <span data-ttu-id="6c082-189">在 [空間]  欄位中，指定包含空間資料之欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="6c082-189">In **Spatial field**, specify the name of the field that contains spatial data.</span></span> <span data-ttu-id="6c082-190">您可能需要從空間資料來源決定此名稱。</span><span class="sxs-lookup"><span data-stu-id="6c082-190">You might need to determine this name from the source of spatial data.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6c082-191">如果您不知道欄位的名稱，而且您已經瀏覽到 ESRI 形狀檔，請使用 [連結到 ESRI 形狀檔 (.shp)]  選項來代替此選項。</span><span class="sxs-lookup"><span data-stu-id="6c082-191">If you do not know the name of the field and you browsed to an ESRI Shapefile, use the **Link to ESRI shape file option** instead of this option.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-specify-an-esri-shapefile-as-a-source-of-spatial-data"></a><a name="ESRI"></a> <span data-ttu-id="6c082-192">將 ESRI 形狀檔指定為空間資料的來源</span><span class="sxs-lookup"><span data-stu-id="6c082-192">To specify an ESRI Shapefile as a source of spatial data</span></span>  
  
1.  <span data-ttu-id="6c082-193">按一下地圖，直到 [圖層] 窗格出現為止。</span><span class="sxs-lookup"><span data-stu-id="6c082-193">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="6c082-194">以滑鼠右鍵按一下圖層，然後按一下 [圖層資料]  。</span><span class="sxs-lookup"><span data-stu-id="6c082-194">Right-click the layer, and then click **Layer Data**.</span></span>  
  
3.  <span data-ttu-id="6c082-195">在 [使用以下來源的空間資料]  中，選取 [連結到 ESRI 形狀檔 (.shp)]  。</span><span class="sxs-lookup"><span data-stu-id="6c082-195">In **Use spatial data from**, select **Link to ESRI Shapefile**.</span></span>  
  
4.  <span data-ttu-id="6c082-196">在 [檔案名稱]  中，鍵入 ESRI 形狀檔的位置，或按一下 [瀏覽]  以選取 ESRI 形狀檔。</span><span class="sxs-lookup"><span data-stu-id="6c082-196">In **File name**, type the location of an ESRI Shapefile, or click **Browse** to select an ESRI Shapefile.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6c082-197">如果此形狀檔在您的本機電腦上，空間資料會內嵌在報表定義中。</span><span class="sxs-lookup"><span data-stu-id="6c082-197">If the Shapefile is on your local computer, the spatial data is embedded in the report definition.</span></span> <span data-ttu-id="6c082-198">若要在處理報表時動態擷取資料，您必須將 ESRI .shp 檔及其支援檔案 .dbf 上傳至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="6c082-198">To retrieve the data dynamically when the report is processed, you must upload the ESRI .shp file and its .dbf support file to the report server.</span></span> <span data-ttu-id="6c082-199">如需詳細資訊，請參閱《SQL Server 線上叢書》中 [Reporting Services 文件](https://go.microsoft.com/fwlink/?linkid=121312) 的＜如何：上傳檔案或報表 (報表管理員)＞。</span><span class="sxs-lookup"><span data-stu-id="6c082-199">For more information, see " How to: Upload a File or Report (Report Manager)" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-specify-a-report-dataset-field-as-a-source-of-spatial-data"></a><a name="DatasetField"></a> <span data-ttu-id="6c082-200">將報表資料集欄位指定為空間資料的來源</span><span class="sxs-lookup"><span data-stu-id="6c082-200">To specify a report dataset field as a source of spatial data</span></span>  
  
1.  <span data-ttu-id="6c082-201">按一下地圖，直到 [圖層] 窗格出現為止。</span><span class="sxs-lookup"><span data-stu-id="6c082-201">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="6c082-202">以滑鼠右鍵按一下圖層，然後按一下 [圖層資料]  。</span><span class="sxs-lookup"><span data-stu-id="6c082-202">Right-click the layer, and then click **Layer Data**.</span></span>  
  
3.  <span data-ttu-id="6c082-203">在 [使用以下來源的空間資料]  中，選取 [資料集中的空間欄位]  。</span><span class="sxs-lookup"><span data-stu-id="6c082-203">In **Use spatial data from**, select **Spatial field in a dataset**.</span></span>  
  
4.  <span data-ttu-id="6c082-204">在 [資料集名稱]  中，按一下報表內包含所需空間資料之資料集的名稱。</span><span class="sxs-lookup"><span data-stu-id="6c082-204">In **Dataset name**, click the name of a dataset in the report that contains that spatial data that you want.</span></span>  
  
5.  <span data-ttu-id="6c082-205">在 [空間欄位名稱]  中，按一下資料集內包含空間資料的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="6c082-205">In **Spatial field name**, click the name of the field in the dataset that contains spatial data.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-add-a-tile-layer"></a><a name="TileLayer"></a> <span data-ttu-id="6c082-206">若要加入圖格圖層</span><span class="sxs-lookup"><span data-stu-id="6c082-206">To add a tile layer</span></span>  
  
1.  <span data-ttu-id="6c082-207">按一下地圖，直到 [圖層] 窗格出現為止。</span><span class="sxs-lookup"><span data-stu-id="6c082-207">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="6c082-208">在工具列上，按一下 [加入圖層]  按鈕，然後從下拉式清單中按一下 [圖格圖層]  。</span><span class="sxs-lookup"><span data-stu-id="6c082-208">On the toolbar, click the **Add Layer** button, and from the drop-down list, click **Tile Layer**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6c082-209">如需有關在報表中使用 Bing 地圖底圖的詳細資訊，請參閱 [其他使用規定](https://go.microsoft.com/fwlink/?LinkId=151371) 和 [隱私權聲明](https://go.microsoft.com/fwlink/?LinkId=151372)。</span><span class="sxs-lookup"><span data-stu-id="6c082-209">For more information about the use of Bing map tiles in your report, see [Additional Terms of Use](https://go.microsoft.com/fwlink/?LinkId=151371) and [Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=151372).</span></span>  
  
3.  <span data-ttu-id="6c082-210">以滑鼠右鍵按一下 [圖層] 窗格中的圖格圖層，然後按一下 [圖格屬性]  。</span><span class="sxs-lookup"><span data-stu-id="6c082-210">Right-click the tile layer in the Map pane, and then click **Tile Properties**.</span></span>  
  
4.  <span data-ttu-id="6c082-211">在 [圖格選項]  中，選取圖格樣式。</span><span class="sxs-lookup"><span data-stu-id="6c082-211">In **Tile options**, select a tile style.</span></span> <span data-ttu-id="6c082-212">如果可以使用 Bing 地圖底圖，設計介面上的圖層會更新成您選取的樣式。</span><span class="sxs-lookup"><span data-stu-id="6c082-212">If the Bing map tiles are available, the layer on the design surface updates with the style that you select.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6c082-213">當您在「地圖精靈」或「地圖圖層精靈」中加入多邊形、線條或點圖層時，也可以加入影像分割圖層。</span><span class="sxs-lookup"><span data-stu-id="6c082-213">A tile layer can also be added when you add a polygon, line, or point layer in the Map or Map Layer wizard.</span></span> <span data-ttu-id="6c082-214">在 [選擇空間資料及地圖檢視選項]  頁面上，選取 [Add a Bing Maps background for this map view (加入此地圖檢視的 Bing Maps 背景)]  選項。</span><span class="sxs-lookup"><span data-stu-id="6c082-214">On the **Choose spatial data and map view options** page, select the option **Add a Bing Maps background for this map view**.</span></span>  

##  <a name="to-change-the-drawing-order-of-a-layer"></a><a name="DrawingOrder"></a> <span data-ttu-id="6c082-215">變更圖層的繪圖順序</span><span class="sxs-lookup"><span data-stu-id="6c082-215">To change the drawing order of a layer</span></span>  
  
1.  <span data-ttu-id="6c082-216">按一下地圖，直到 [圖層] 窗格出現為止。</span><span class="sxs-lookup"><span data-stu-id="6c082-216">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="6c082-217">按一下 [圖層] 窗格中的圖層，即可選取它。</span><span class="sxs-lookup"><span data-stu-id="6c082-217">Click the layer in the Map pane to select it.</span></span>  
  
3.  <span data-ttu-id="6c082-218">在 [圖層] 窗格工具列上，按一下向上鍵或向下鍵來變更每個圖層的繪圖順序。</span><span class="sxs-lookup"><span data-stu-id="6c082-218">On the Map pane toolbar, click the up or down arrow to change the drawing order of each layer.</span></span>  

##  <a name="to-change-the-transparency-of-a-polygon-line-or-point-layer"></a><a name="Transparency"></a> <span data-ttu-id="6c082-219">變更多邊形、線條或點圖層的透明度</span><span class="sxs-lookup"><span data-stu-id="6c082-219">To change the transparency of a polygon, line, or point layer</span></span>  
  
1.  <span data-ttu-id="6c082-220">按一下地圖，直到 [圖層] 窗格出現為止。</span><span class="sxs-lookup"><span data-stu-id="6c082-220">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="6c082-221">以滑鼠右鍵按一下圖層，然後按一下 [圖層資料]  。</span><span class="sxs-lookup"><span data-stu-id="6c082-221">Right-click the layer, and then click **Layer Data**.</span></span>  
  
3.  <span data-ttu-id="6c082-222">按一下 [ `Visibility`]。</span><span class="sxs-lookup"><span data-stu-id="6c082-222">Click `Visibility`.</span></span>  
  
4.  <span data-ttu-id="6c082-223">在 [透明度選項]  中，輸入表示透明度百分比的值，例如 **40**。</span><span class="sxs-lookup"><span data-stu-id="6c082-223">In **Transparency options**, type a value that represents the percentage transparency, for example, **40**.</span></span> <span data-ttu-id="6c082-224">透明度百分比為零 (0) 表示圖層是不透明的。</span><span class="sxs-lookup"><span data-stu-id="6c082-224">Zero (0) % transparency means that the layer is opaque.</span></span> <span data-ttu-id="6c082-225">透明度百分比為 100，則表示您在報表中看不到圖層。</span><span class="sxs-lookup"><span data-stu-id="6c082-225">100% transparency means that you will not see the layer in the report.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-change-the-transparency-of-a-tile-layer"></a><a name="TileTransparency"></a> <span data-ttu-id="6c082-226">變更圖格圖層的透明度</span><span class="sxs-lookup"><span data-stu-id="6c082-226">To change the transparency of a tile layer</span></span>  
  
1.  <span data-ttu-id="6c082-227">按一下地圖，直到 [圖層] 窗格出現為止。</span><span class="sxs-lookup"><span data-stu-id="6c082-227">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="6c082-228">以滑鼠右鍵按一下圖層，然後按一下 [圖格屬性]  。</span><span class="sxs-lookup"><span data-stu-id="6c082-228">Right-click the layer, and then click **Tile Properties**.</span></span>  
  
3.  <span data-ttu-id="6c082-229">按一下 [ `Visibility`]。</span><span class="sxs-lookup"><span data-stu-id="6c082-229">Click `Visibility`.</span></span>  
  
4.  <span data-ttu-id="6c082-230">在 [透明度選項]  中，輸入表示透明度百分比的值，例如 **40**。</span><span class="sxs-lookup"><span data-stu-id="6c082-230">In **Transparency options**, type a value that represents the percentage transparency, for example, **40**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-specify-a-secure-connection-for-a-tile-layer"></a><a name="Secure"></a> <span data-ttu-id="6c082-231">為圖格圖層指定安全連接</span><span class="sxs-lookup"><span data-stu-id="6c082-231">To specify a secure connection for a tile layer</span></span>  
  
1.  <span data-ttu-id="6c082-232">按一下地圖，直到 [圖層] 窗格出現為止。</span><span class="sxs-lookup"><span data-stu-id="6c082-232">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="6c082-233">在 [圖層] 窗格中按一下圖格圖層，即可選取它。</span><span class="sxs-lookup"><span data-stu-id="6c082-233">In the Map pane, click the tile layer to select it.</span></span> <span data-ttu-id="6c082-234">[屬性] 窗格會顯示圖格圖層屬性。</span><span class="sxs-lookup"><span data-stu-id="6c082-234">The Properties pane displays the tile layer properties.</span></span>  
  
3.  <span data-ttu-id="6c082-235">在 [屬性] 窗格中，將 UseSecureConnection 設定為 **True**。</span><span class="sxs-lookup"><span data-stu-id="6c082-235">In the Properties pane, set UseSecureConnection to **True**.</span></span>  
  
 <span data-ttu-id="6c082-236">Bing Maps Web 服務的連接將會使用 HTTP SSL (安全通訊端層) 服務來擷取這個圖層的 Bing 地圖底圖。</span><span class="sxs-lookup"><span data-stu-id="6c082-236">The connection for the Bing Maps Web service will use the HTTP SSL (Secure Sockets Layer) service to retrieve Bing map tiles for this layer.</span></span>  

##  <a name="to-specify-the-language-for-tile-labels"></a><a name="Language"></a> <span data-ttu-id="6c082-237">為圖格標籤指定語言</span><span class="sxs-lookup"><span data-stu-id="6c082-237">To specify the language for tile labels</span></span>  
  
1.  <span data-ttu-id="6c082-238">根據預設，如果是顯示標籤的圖格樣式，語言是由報表產生器的預設地區設定所決定。</span><span class="sxs-lookup"><span data-stu-id="6c082-238">By default, for tile styles that display labels, the language is determined from the default locale for Report Builder.</span></span> <span data-ttu-id="6c082-239">您可以透過以下方式來自訂圖格標籤的語言設定。</span><span class="sxs-lookup"><span data-stu-id="6c082-239">You can customize the language setting for tile labels in the following ways.</span></span>  
  
    -   <span data-ttu-id="6c082-240">按一下檢視區外部的地圖，即可選取該地圖。</span><span class="sxs-lookup"><span data-stu-id="6c082-240">Click the map outside the viewport to select the map.</span></span> <span data-ttu-id="6c082-241">在 [屬性] 窗格中，針對 TileLanguage 屬性從下拉式清單中選取文化特性值。</span><span class="sxs-lookup"><span data-stu-id="6c082-241">In the Properties pane, for the TileLanguage property, select a culture value from the drop-down list.</span></span>  
  
    -   <span data-ttu-id="6c082-242">按一下報表背景，即可選取報表。</span><span class="sxs-lookup"><span data-stu-id="6c082-242">Click the report background to select the report.</span></span> <span data-ttu-id="6c082-243">在 [屬性] 窗格中，針對 Language 屬性從下拉式清單中選取文化特性值。</span><span class="sxs-lookup"><span data-stu-id="6c082-243">In the Properties pane, from for the Language property, select a culture value from the drop-down list.</span></span>  
  
     <span data-ttu-id="6c082-244">設定圖格標籤語言的優先順序如下：報表屬性 Language、報表產生器的預設地區設定，以及地圖屬性 TileLanguage。</span><span class="sxs-lookup"><span data-stu-id="6c082-244">The order of precedence for setting the tile label language is: report property Language, default locale for Report Builder, and map property TileLanguage.</span></span>  

##  <a name="to-conditionally-hide-a-layer-based-on-viewport-zoom-level"></a><a name="ConditionalHide"></a> <span data-ttu-id="6c082-245">根據檢視區縮放層級，有條件地隱藏圖層</span><span class="sxs-lookup"><span data-stu-id="6c082-245">To conditionally hide a layer based on viewport zoom level</span></span>  
  
1.  <span data-ttu-id="6c082-246">設定 `Visibility` 選項來控制地圖圖層的顯示。</span><span class="sxs-lookup"><span data-stu-id="6c082-246">Set `Visibility` options to control the display for a map layer.</span></span>  
  
    -   <span data-ttu-id="6c082-247">在 [地圖圖層] 窗格中，以滑鼠右鍵按一下圖層選取此圖層，然後按一下 [地圖圖層] 工具列上的 [屬性]，開啟 [地圖圖層屬性]  。</span><span class="sxs-lookup"><span data-stu-id="6c082-247">In the Map Layers pane, right-click a layer to select it, and on the Map Layers toolbar, click Properties to open **Map Layer Properties**.</span></span>  
  
    -   <span data-ttu-id="6c082-248">按一下 [ `Visibility`]。</span><span class="sxs-lookup"><span data-stu-id="6c082-248">Click `Visibility`.</span></span>  
  
    -   <span data-ttu-id="6c082-249">在 [圖層可見性] 中，選取 [根據縮放值顯示或隱藏]  。</span><span class="sxs-lookup"><span data-stu-id="6c082-249">In Layer visibility, select **Show or hide based on zoom value**.</span></span>  
  
    -   <span data-ttu-id="6c082-250">輸入顯示圖層時的最小和最大縮放值。</span><span class="sxs-lookup"><span data-stu-id="6c082-250">Enter minimum and maximum zoom values for when display the layer.</span></span>  
  
    -   <span data-ttu-id="6c082-251">選擇性。</span><span class="sxs-lookup"><span data-stu-id="6c082-251">Optional.</span></span> <span data-ttu-id="6c082-252">輸入透明度的值。</span><span class="sxs-lookup"><span data-stu-id="6c082-252">Enter a value for transparency.</span></span>  
  
     <span data-ttu-id="6c082-253">您也可以有條件地隱藏圖層。</span><span class="sxs-lookup"><span data-stu-id="6c082-253">You can also conditionally hide the layer.</span></span> <span data-ttu-id="6c082-254">如需詳細資訊，請參閱[隱藏項目 &#40;報表產生器及 SSRS&#41;](../report-builder/hide-an-item-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="6c082-254">For more information, see [Hide an Item &#40;Report Builder and SSRS&#41;](../report-builder/hide-an-item-report-builder-and-ssrs.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="6c082-255">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c082-255">See Also</span></span>  
 <span data-ttu-id="6c082-256">[地圖 &#40;報表產生器及 SSRS&#41;](maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6c082-256">[Maps &#40;Report Builder and SSRS&#41;](maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6c082-257">報表疑難排解：地圖報表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6c082-257">Troubleshoot Reports: Map Reports &#40;Report Builder and SSRS&#41;</span></span>](troubleshoot-reports-map-reports-report-builder-and-ssrs.md)  
