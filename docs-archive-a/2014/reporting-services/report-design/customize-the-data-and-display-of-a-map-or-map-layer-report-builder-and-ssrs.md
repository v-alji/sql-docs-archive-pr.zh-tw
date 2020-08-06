---
title: 自訂地圖或地圖圖層的資料和顯示 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10521"
- sql12.rtp.rptdesigner.shared.shadowdv.f1
- "10515"
- "10512"
- "10520"
- "10523"
- sql12.rtp.rptdesigner.mapgroupproperties.variables.f1
- sql12.rtp.rptdesigner.mapgroupproperties.filter.f1
- sql12.rtp.rptdesigner.shared.number.f1
- sql12.rtp.rptdesigner.shared.font.f1
- sql12.rtp.rptdesigner.mapgroupproperties.general.f1
- "10507"
ms.assetid: fdd9b994-d138-4990-a291-279b0249eb72
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 05987cea7ebde9d3587ade3f567eeb8ccef5e8fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704945"
---
# <a name="customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs"></a><span data-ttu-id="cba5d-102">自訂地圖或地圖圖層的資料和顯示 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="cba5d-102">Customize the Data and Display of a Map or Map Layer (Report Builder and SSRS)</span></span>
  <span data-ttu-id="cba5d-103">使用精靈將地圖或地圖圖層加入至報表之後，您可能會想要變更地圖在報表中的外觀。</span><span class="sxs-lookup"><span data-stu-id="cba5d-103">After you add a map or map layer to a report by using a wizard, you might want to change the way the map looks in the report.</span></span> <span data-ttu-id="cba5d-104">您可以考慮下列構想來進行改善：</span><span class="sxs-lookup"><span data-stu-id="cba5d-104">You can make improvements by considering the following ideas:</span></span>  
  
-   <span data-ttu-id="cba5d-105">若要協助您的使用者了解如何解譯地圖上的資料顯示，您可以加入圖例、色階、標籤，以及工具提示。</span><span class="sxs-lookup"><span data-stu-id="cba5d-105">To help your users understand how to interpret the data display on a map, you can add legends and a color scale, and add labels and tooltips.</span></span>  
  
-   <span data-ttu-id="cba5d-106">若要讓地圖更容易讀取，請變更置中與縮放層級、加入距離標尺，並顯示背景方格。</span><span class="sxs-lookup"><span data-stu-id="cba5d-106">To make the map easier to read, change the center and zoom level, add a distance scale, and display a background grid.</span></span>  
  
-   <span data-ttu-id="cba5d-107">若要在您執行報表時協助控制地圖繪製時間，您可以調整解析度來簡化地圖元素。</span><span class="sxs-lookup"><span data-stu-id="cba5d-107">To help control map drawing time when you run the report, you can adjust the resolution to simplify the map elements.</span></span>  
  
-   <span data-ttu-id="cba5d-108">您可以將地圖元素內嵌在報表定義中，然後變更個別元素顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="cba5d-108">You can embed map elements in the report definition, and then change how individual elements appear.</span></span> <span data-ttu-id="cba5d-109">例如，您可以使用圖釘顯示主要辦公室位置，並使用圓形顯示其他辦公室位置。</span><span class="sxs-lookup"><span data-stu-id="cba5d-109">For example, you can display the primary office location with a pushpin and other office locations with circles.</span></span>  
  
-   <span data-ttu-id="cba5d-110">您可以藉由指定自己的資料群組運算式，加入自訂區域。</span><span class="sxs-lookup"><span data-stu-id="cba5d-110">You can add customized regions by specifying your own data group expressions.</span></span>  
  
-   <span data-ttu-id="cba5d-111">您可以在包含內嵌點之地圖圖層上指定的點加入自訂位置。</span><span class="sxs-lookup"><span data-stu-id="cba5d-111">You can add a custom location at a  point that you specify on a map layer that has embedded points.</span></span> <span data-ttu-id="cba5d-112">您可以設定值，並從點圖層上的其他點個別顯示自訂點的屬性。</span><span class="sxs-lookup"><span data-stu-id="cba5d-112">You can set the value and display properties for custom points independently from other points on a point layer.</span></span>  
  
-   <span data-ttu-id="cba5d-113">若要提供更多細節，您可以在每個圖層上加入地圖元素的連結，使用者按一下這些連結，便可開啟相關的報表。</span><span class="sxs-lookup"><span data-stu-id="cba5d-113">To provide more detail, you can add links to map elements on each layer that a user can click to open related reports.</span></span>  
  
 <span data-ttu-id="cba5d-114">如需改善報表的更多想法，請參閱[規劃報表 &#40;報表產生器&#41;](planning-a-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="cba5d-114">For more ideas about improving a report, see [Planning a Report &#40;Report Builder&#41;](planning-a-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="cba5d-115">顯示選項會影響檢視報表時地圖或部分地圖顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="cba5d-115">Display options affect the way a map or the parts of a map appear when you view the report.</span></span> <span data-ttu-id="cba5d-116">有些選項可控制地圖的外觀，例如，框線和字型，或是在地圖上表示的區域。</span><span class="sxs-lookup"><span data-stu-id="cba5d-116">Some options control the appearance of the map, such as the borders and fonts or the area represented on the map.</span></span> <span data-ttu-id="cba5d-117">有些選項則控制每個圖層的內容，例如，泡泡地圖大小、標記類型、標籤或工具提示。</span><span class="sxs-lookup"><span data-stu-id="cba5d-117">Other options control the content of each layer, such as bubble sizes, marker types, labels, or tooltips.</span></span>  
  
 <span data-ttu-id="cba5d-118">地圖報表項目包含下列部分：地圖本身、地圖檢視區、一組標題、一組圖例 (圖例、色階和距離標尺)、一組圖層、每個圖層 (多邊形或線條或點) 上的一組地圖元素。</span><span class="sxs-lookup"><span data-stu-id="cba5d-118">A map report item includes the following parts: the map itself, a map viewport, a set of titles, a set of legends (legend, color scale, and distance scale), a set of layers, a set of map elements on each layer (polygons or lines or points).</span></span> <span data-ttu-id="cba5d-119">使用下列幾節中的資訊了解控制地圖不同部分之顯示選項的屬性對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cba5d-119">Use the information in the following sections to understand which property dialog box controls the display options for different parts of a map.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="change-options-for-the-map"></a><a name="Map"></a> <span data-ttu-id="cba5d-120">變更地圖的選項</span><span class="sxs-lookup"><span data-stu-id="cba5d-120">Change Options for the Map</span></span>  
 <span data-ttu-id="cba5d-121">在地圖報表項目上，您可以控制下列項目：</span><span class="sxs-lookup"><span data-stu-id="cba5d-121">On a map report item, you can control the following:</span></span>  
  
-   <span data-ttu-id="cba5d-122">加入多個標題。</span><span class="sxs-lookup"><span data-stu-id="cba5d-122">Add multiple titles.</span></span>  
  
-   <span data-ttu-id="cba5d-123">加入多個圖例。</span><span class="sxs-lookup"><span data-stu-id="cba5d-123">Add multiple legends.</span></span> <span data-ttu-id="cba5d-124">若要變更圖例的內容，您需要建立其他圖例，然後變更規則以指定要在哪個圖例中輸入每個規則所建立的圖例項目。</span><span class="sxs-lookup"><span data-stu-id="cba5d-124">To change the contents of a legend, you need to create additional legends and then change the rules to specify in which legend to enter the legend items created by each rule.</span></span>  
  
-   <span data-ttu-id="cba5d-125">加入更多圖層。</span><span class="sxs-lookup"><span data-stu-id="cba5d-125">Add more layers.</span></span>  
  
-   <span data-ttu-id="cba5d-126">隱藏或顯示距離標尺或色階。</span><span class="sxs-lookup"><span data-stu-id="cba5d-126">Hide or show the distance scale or color scale.</span></span>  
  
-   <span data-ttu-id="cba5d-127">指定陰影以提供深度的幻影。</span><span class="sxs-lookup"><span data-stu-id="cba5d-127">Provide the illusion of depth by specifying a shadow.</span></span>  
  
 <span data-ttu-id="cba5d-128">若要變更這些選項，以滑鼠右鍵按一下地圖、按一下 [地圖]  ，然後變更這些選項。</span><span class="sxs-lookup"><span data-stu-id="cba5d-128">To change these options, right-click the map, click **Map**, and change the options.</span></span>  
  
 
  
##  <a name="change-options-for-the-viewport"></a><a name="Viewport"></a> <span data-ttu-id="cba5d-129">變更檢視區的選項</span><span class="sxs-lookup"><span data-stu-id="cba5d-129">Change Options for the Viewport</span></span>  
 <span data-ttu-id="cba5d-130">使用檢視區選項來變更出現在報表中之地圖的檢視。</span><span class="sxs-lookup"><span data-stu-id="cba5d-130">Use the viewport options to change the view of the map that appears in your report.</span></span>  
  
 <span data-ttu-id="cba5d-131">空間資料來源所提供的區域可能會比您需要在報表中顯示的空間還多。</span><span class="sxs-lookup"><span data-stu-id="cba5d-131">The source of spatial data might provide more area than you need to display in the report.</span></span> <span data-ttu-id="cba5d-132">您可以使用檢視區設定置中、縮放層級，以及裁剪地圖的區域。</span><span class="sxs-lookup"><span data-stu-id="cba5d-132">You can use the viewport to set the center, the zoom level, and to crop the area for the map.</span></span>  
  
 <span data-ttu-id="cba5d-133">您可以為檢視區設定下列選項：</span><span class="sxs-lookup"><span data-stu-id="cba5d-133">The following options can be set for the viewport:</span></span>  
  
-   <span data-ttu-id="cba5d-134">選擇座標系統，並針對地理座標系統選擇投射。</span><span class="sxs-lookup"><span data-stu-id="cba5d-134">Choose the coordinate system and, for a geographic coordinate system, choose the projection.</span></span>  
  
-   <span data-ttu-id="cba5d-135">選擇地圖的中心。</span><span class="sxs-lookup"><span data-stu-id="cba5d-135">Choose the center for the map.</span></span>  
  
-   <span data-ttu-id="cba5d-136">裁剪地圖的檢視。</span><span class="sxs-lookup"><span data-stu-id="cba5d-136">Crop the view for the map.</span></span>  
  
-   <span data-ttu-id="cba5d-137">設定縮放層級。</span><span class="sxs-lookup"><span data-stu-id="cba5d-137">Set the zoom level.</span></span>  
  
-   <span data-ttu-id="cba5d-138">解析度與簡化</span><span class="sxs-lookup"><span data-stu-id="cba5d-138">Resolution and simplification.</span></span> <span data-ttu-id="cba5d-139">在繪製時間與線條和多邊形的詳細外框之間選擇一個平衡點。</span><span class="sxs-lookup"><span data-stu-id="cba5d-139">Choose a balance between drawing time and detailed outlines for lines and polygons.</span></span>  
  
 <span data-ttu-id="cba5d-140">若要變更這些選項，以滑鼠右鍵按一下地圖檢視區，然後使用 [地圖檢視區屬性對話方塊、一般](../map-viewport-properties-dialog-box-general.md) 頁面與相關的頁面。</span><span class="sxs-lookup"><span data-stu-id="cba5d-140">To change these options, right-click the map viewport, use the [Map Viewport Properties Dialog Box, General](../map-viewport-properties-dialog-box-general.md) page and related pages.</span></span>  
  

  
##  <a name="change-options-for-the-legends"></a><a name="Legends"></a> <span data-ttu-id="cba5d-141">變更圖例的選項</span><span class="sxs-lookup"><span data-stu-id="cba5d-141">Change Options for the Legends</span></span>  
 <span data-ttu-id="cba5d-142">圖例可協助使用者解譯地圖上的資料。</span><span class="sxs-lookup"><span data-stu-id="cba5d-142">Legends help users interpret the data on a map.</span></span>  
  
 <span data-ttu-id="cba5d-143">根據預設，您為圖層指定的所有規則都會將項目加入至第一個圖例中。</span><span class="sxs-lookup"><span data-stu-id="cba5d-143">By default, all rules that you specify for a layer add items to the first legend.</span></span> <span data-ttu-id="cba5d-144">此外，所有色彩規則都會顯示色階中的值。</span><span class="sxs-lookup"><span data-stu-id="cba5d-144">In addition, all color rules display values in the color scale.</span></span>  
  
-   <span data-ttu-id="cba5d-145">若要變更圖例外觀的顯示選項，包括其相對於檢視區的位置，請針對圖例本身設定選項。</span><span class="sxs-lookup"><span data-stu-id="cba5d-145">To change the display options for the appearance of the legend, including its position relative to the viewport, set options on the legend itself.</span></span>  
  
-   <span data-ttu-id="cba5d-146">若要變更圖例內容或圖例內容的格式，請針對圖層的對應規則變更圖例選項。</span><span class="sxs-lookup"><span data-stu-id="cba5d-146">To change the contents or the format of contents for a legend, change the legend options for the corresponding rules for a layer.</span></span>  
  
 <span data-ttu-id="cba5d-147">如需詳細資訊，請參閱 [變更地圖圖例、色階與相關的規則 &#40;報表產生器及 SSRS&#41;](change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="cba5d-147">For more information, see [Change Map Legends, Color Scale, and Associated Rules &#40;Report Builder and SSRS&#41;](change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="change-options-for-the-layer"></a><a name="Layer"></a> <span data-ttu-id="cba5d-148">變更圖層的選項</span><span class="sxs-lookup"><span data-stu-id="cba5d-148">Change Options for the Layer</span></span>  
 <span data-ttu-id="cba5d-149">若要顯示地圖的圖層，按一下該地圖來選取它。</span><span class="sxs-lookup"><span data-stu-id="cba5d-149">To display the layers for a map, click the map to select it.</span></span> <span data-ttu-id="cba5d-150">[地圖] 窗格隨即出現。</span><span class="sxs-lookup"><span data-stu-id="cba5d-150">The Map pane appears.</span></span> <span data-ttu-id="cba5d-151">若要變更圖層的選項，以滑鼠右鍵按一下圖層，然後使用快速鍵功能表。</span><span class="sxs-lookup"><span data-stu-id="cba5d-151">To change options for a layer, right-click the layer and use the shortcut menu.</span></span>  
  
 <span data-ttu-id="cba5d-152">根據空間資料來源傳回的空間資料，圖層可以是以下三個類型之一：多邊形圖層、線條圖層與點圖層。</span><span class="sxs-lookup"><span data-stu-id="cba5d-152">A layer can be one of three types based on the spatial data that is returned by the spatial data source: a polygon layer, a line layer, or a point layer.</span></span>  
  
 <span data-ttu-id="cba5d-153">您可以為圖層設定下列選項：</span><span class="sxs-lookup"><span data-stu-id="cba5d-153">The following options can be set for the layer:</span></span>  
  
-   <span data-ttu-id="cba5d-154">相關的分析資料與符合欄位。</span><span class="sxs-lookup"><span data-stu-id="cba5d-154">The associated analytical data and match fields.</span></span> <span data-ttu-id="cba5d-155">空間資料的來源會列在 [地圖] 窗格的圖層名稱之下。</span><span class="sxs-lookup"><span data-stu-id="cba5d-155">The source of the spatial data is listed on the Map pane under the name of the layer.</span></span> <span data-ttu-id="cba5d-156">如果來源是內嵌的，圖層的地圖元素是報表定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="cba5d-156">When the source is embedded, the map elements for the layer are part of the report definition.</span></span> <span data-ttu-id="cba5d-157">如果來源不是內嵌的，則會在執行階段擷取空間資料，而且報表處理器會在處理報表時建立圖層的地圖元素。</span><span class="sxs-lookup"><span data-stu-id="cba5d-157">If the source is not embedded, then the spatial data is retrieved at run time and the report processor creates the map elements for the layer when the report is processed.</span></span> <span data-ttu-id="cba5d-158">若要變更圖層上的資料選項，請使用 [地圖圖層] 對話方塊中的 [分析資料] 頁面。</span><span class="sxs-lookup"><span data-stu-id="cba5d-158">To change data options on the layer, use the Analytical Data page in the Map Layer dialog box.</span></span>  
  
-   <span data-ttu-id="cba5d-159">圖層繪製順序。</span><span class="sxs-lookup"><span data-stu-id="cba5d-159">Layer drawing order.</span></span> <span data-ttu-id="cba5d-160">您看到圖層在 [地圖] 窗格中列出的順序，就是圖層的反向繪製順序。</span><span class="sxs-lookup"><span data-stu-id="cba5d-160">The order that you see the layers listed in the Map pane is the reverse drawing order for the layers.</span></span> <span data-ttu-id="cba5d-161">系統會先繪製清單中的最後一個圖層。</span><span class="sxs-lookup"><span data-stu-id="cba5d-161">The last layer in the list is drawn first.</span></span> <span data-ttu-id="cba5d-162">例如，如果您希望點圖層上的點出現在多邊形圖層中的多邊形上方，點圖層應該是第一個，而多邊形圖層則是第二個。</span><span class="sxs-lookup"><span data-stu-id="cba5d-162">For example, if you want the points on a point layer to appear on top of the polygons in the polygon layer, the point layer should be first and the polygon layer second.</span></span>  
  
-   <span data-ttu-id="cba5d-163">圖層可見性，包括透明度。</span><span class="sxs-lookup"><span data-stu-id="cba5d-163">Layer visibility, including transparency.</span></span> <span data-ttu-id="cba5d-164">若要讓某個圖層透過另一個圖層顯示，請將透明度設定為高於 0 的值。</span><span class="sxs-lookup"><span data-stu-id="cba5d-164">To have one layer show through another layer, set the transparency to a value higher than 0.</span></span> <span data-ttu-id="cba5d-165">值為 100% 時，表示看不到圖層。</span><span class="sxs-lookup"><span data-stu-id="cba5d-165">A value of 100% means the layer is not visible.</span></span> <span data-ttu-id="cba5d-166">若要處理個別的圖層，您可以使用 [地圖] 窗格中的 [可見度]  圖示，輕鬆地個別顯示或隱藏每個圖層。</span><span class="sxs-lookup"><span data-stu-id="cba5d-166">To work with an individual layer, you can easily show or hide each layer independently by using the **Visibility** icon in the Map pane.</span></span> <span data-ttu-id="cba5d-167">您也可以設定縮放層級選項來指定根據縮放層級顯示或隱藏圖層上之地圖元素的時機。</span><span class="sxs-lookup"><span data-stu-id="cba5d-167">You can also set zoom level options to specify when to show or hide map elements on the layer based on the zoom level.</span></span>  
  
-   <span data-ttu-id="cba5d-168">針對目前的檢視區置中與縮放層級加入 Bing 地圖底圖圖層。</span><span class="sxs-lookup"><span data-stu-id="cba5d-168">Add a Bing map tile layer for the current viewport center and zoom level.</span></span> <span data-ttu-id="cba5d-169">您不需要為圖格圖層指定地理座標。</span><span class="sxs-lookup"><span data-stu-id="cba5d-169">You do not need to specify the geographic coordinates for a tile layer.</span></span> <span data-ttu-id="cba5d-170">當座標系統為 [地理]、投射為 [Mercator]、Bing Map 伺服器可以使用，而且已經將報表伺服器設定為支援此功能時，系統會自動載入圖格以符合檢視區。</span><span class="sxs-lookup"><span data-stu-id="cba5d-170">Tiles are automatically loaded to match the viewport area when the coordinate system is Geographic, the projection is Mercator, the Bing Maps servers are available, and when the report server has been configured to support this feature.</span></span> <span data-ttu-id="cba5d-171">您可以針對每個報告指定是否要使用安全連線來擷取圖格。</span><span class="sxs-lookup"><span data-stu-id="cba5d-171">For each report, you can specify whether to use a secure connection to retrieve tiles.</span></span>  
  
 <span data-ttu-id="cba5d-172">如需圖層的詳細資訊，請參閱[加入、變更或刪除地圖或地圖圖層 &#40;報表產生器及 SSRS&#41;](add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="cba5d-172">For more information about layers, see [Add, Change, or Delete a Map or Map Layer &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="change-data-grouping-for-the-layer"></a><a name="DataGrouping"></a> <span data-ttu-id="cba5d-173">變更圖層的資料群組</span><span class="sxs-lookup"><span data-stu-id="cba5d-173">Change Data Grouping for the Layer</span></span>  
 <span data-ttu-id="cba5d-174">您可以自訂形狀空間資料的彙總方式。</span><span class="sxs-lookup"><span data-stu-id="cba5d-174">You can customize the way to aggregate spatial data for your own shapes.</span></span> <span data-ttu-id="cba5d-175">若要設定圖層的群組屬性，請選取 [地圖] 窗格中的圖層，在圖層的 [屬性] 窗格中按一下 [群組]  ，然後按一下省略符號 (...) 開啟 [群組屬性]。</span><span class="sxs-lookup"><span data-stu-id="cba5d-175">To set the group properties for a layer, select the layer in the Map pane, and in the Properties pane for the layer, click **Group**, and then click the ellipsis (...) to open the Group properties.</span></span> <span data-ttu-id="cba5d-176">在這個對話方塊中，您可以指定群組運算式、建立群組變數，以及篩選用於群組的資料。</span><span class="sxs-lookup"><span data-stu-id="cba5d-176">In this dialog box, you can specify group expressions, create group variables, and filter data that is used for grouping.</span></span>  
  
 <span data-ttu-id="cba5d-177">群組運算式會指定與空間資料具有關聯性的分析資料如何針對圖層上的每個地圖元素進行彙總。</span><span class="sxs-lookup"><span data-stu-id="cba5d-177">The group expression specifies how analytical data that has a relationship to spatial data is aggregated for each map element on the layer.</span></span> <span data-ttu-id="cba5d-178">根據預設，群組運算式是針對空間資料與分析資料之間的關聯性指定的一組符合欄位組。</span><span class="sxs-lookup"><span data-stu-id="cba5d-178">By default, the group expression is the set of match fields that was specified for the relationship between the spatial data and the analytical data.</span></span> <span data-ttu-id="cba5d-179">例如，對於顯示國家或地區之城市位置和人口數多寡的泡泡地圖，符合欄位包含城市名稱 [City] 和地區名稱 [Region]，因為可能會有多個城市擁有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="cba5d-179">For example, for a bubble map that displays city locations and population size for a country or region, the match fields include city name [City] and region name [Region] because there can be multiple cities with the same name.</span></span> <span data-ttu-id="cba5d-180">對應的群組運算式包含兩個欄位：[City] 和 [Region]。</span><span class="sxs-lookup"><span data-stu-id="cba5d-180">The corresponding group expression includes two fields: [City] and [Region].</span></span>  
  
 <span data-ttu-id="cba5d-181">如需詳細資訊，請參閱 [Map Tips: How To Import Shapefiles Into SQL Server and Aggregate Spatial Data](https://go.microsoft.com/fwlink/?LinkID=214991)(地圖提示：如何將形狀檔匯入 SQL Server 及彙總空間資料中)。</span><span class="sxs-lookup"><span data-stu-id="cba5d-181">For more information, see [Map Tips: How To Import Shapefiles Into SQL Server and Aggregate Spatial Data](https://go.microsoft.com/fwlink/?LinkID=214991).</span></span>  
  
 
  
##  <a name="change-options-for-the-map-elements-on-the-layer"></a><a name="MapElements"></a> <span data-ttu-id="cba5d-182">變更圖層上地圖元素的選項</span><span class="sxs-lookup"><span data-stu-id="cba5d-182">Change Options for the Map Elements on the Layer</span></span>  
 <span data-ttu-id="cba5d-183">在以空間資料為基礎的圖層上，地圖元素為點、線條或多邊形。</span><span class="sxs-lookup"><span data-stu-id="cba5d-183">Map elements are the points, lines, or polygons on a layer that are based on the spatial data.</span></span> <span data-ttu-id="cba5d-184">您可以為地圖元素設定下列選項。</span><span class="sxs-lookup"><span data-stu-id="cba5d-184">For map elements, the following options can be set.</span></span> <span data-ttu-id="cba5d-185">不會是否內嵌地圖元素，這些選項都會套用到圖層上的所有地圖元素：</span><span class="sxs-lookup"><span data-stu-id="cba5d-185">These options apply to all map elements on the layer, whether or not they are embedded:</span></span>  
  
-   <span data-ttu-id="cba5d-186">標籤、標籤可見性、標籤位移與格式。</span><span class="sxs-lookup"><span data-stu-id="cba5d-186">Labels, label visibility, label offset, and formatting.</span></span>  
  
-   <span data-ttu-id="cba5d-187">框線和填滿。</span><span class="sxs-lookup"><span data-stu-id="cba5d-187">Borders and fill.</span></span>  
  
-   <span data-ttu-id="cba5d-188">鑽研動作。</span><span class="sxs-lookup"><span data-stu-id="cba5d-188">Drillthrough actions.</span></span>  
  
-   <span data-ttu-id="cba5d-189">顯示選項。</span><span class="sxs-lookup"><span data-stu-id="cba5d-189">Display options.</span></span>  
  
 <span data-ttu-id="cba5d-190">地圖元素的顯示選項會根據圖層、地圖元素、地圖元素的規則，以及內嵌地圖元素的覆寫選項，遵循其優先順序。</span><span class="sxs-lookup"><span data-stu-id="cba5d-190">Display options for map elements follow a precedence order based on the layer, the map element, rules for the map element, and override options for embedded map elements.</span></span>  
  
 <span data-ttu-id="cba5d-191">若要變更這些選項，以滑鼠右鍵按一下地圖元素，然後使用內嵌屬性對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cba5d-191">To change these options, right-click the map element, use the embedded properties dialog box.</span></span> <span data-ttu-id="cba5d-192">例如，若是內嵌的多邊形，請使用 [地圖內嵌的多邊形屬性] 對話方塊的 [一般] 頁面以及相關的頁面。</span><span class="sxs-lookup"><span data-stu-id="cba5d-192">For example, for an embedded polygon, use the Map Embedded Polygon Properties Dialog Box, General page and related pages.</span></span>  
  

  
##  <a name="understanding-display-option-precedence"></a><a name="Precedence"></a> <span data-ttu-id="cba5d-193">了解顯示選項優先順序</span><span class="sxs-lookup"><span data-stu-id="cba5d-193">Understanding Display Option Precedence</span></span>  
 <span data-ttu-id="cba5d-194">當您想要控制地圖圖層上點、線條或多邊形的顯示外觀時，您必須了解可以設定顯示選項的位置，以及哪些選項擁有較高的優先順序。</span><span class="sxs-lookup"><span data-stu-id="cba5d-194">When you want to control the display appearance of a point, line, or polygon on a map layer, you must understand where display options can be set and which options have a higher precedence.</span></span> <span data-ttu-id="cba5d-195">下列顯示選項會從最低到最高依序列出。</span><span class="sxs-lookup"><span data-stu-id="cba5d-195">The following display options are listed from lowest to highest.</span></span> <span data-ttu-id="cba5d-196">此清單中優先順序較高的顯示選項會覆寫優先順序較低的選項：</span><span class="sxs-lookup"><span data-stu-id="cba5d-196">Higher display options override lower display options in this list:</span></span>  
  
-   <span data-ttu-id="cba5d-197">圖層選項。</span><span class="sxs-lookup"><span data-stu-id="cba5d-197">Layer options.</span></span>  
  
-   <span data-ttu-id="cba5d-198">每個圖層上的點、線條或多邊形選項。</span><span class="sxs-lookup"><span data-stu-id="cba5d-198">Points, Lines, or Polygons options on each layer.</span></span> <span data-ttu-id="cba5d-199">不管處理報表時是否動態擷取地圖元素，也不管這些地圖元素是否內嵌在報表定義中，這都適用。</span><span class="sxs-lookup"><span data-stu-id="cba5d-199">This applies whether the map elements are dynamically retrieved when the report is processed or whether they the map elements are embedded in the report definition.</span></span> <span data-ttu-id="cba5d-200">例如，您可以為圖層上的所有元素指定填滿色彩。</span><span class="sxs-lookup"><span data-stu-id="cba5d-200">For example, you specify a fill color for all elements on a layer.</span></span>  
  
-   <span data-ttu-id="cba5d-201">規則。</span><span class="sxs-lookup"><span data-stu-id="cba5d-201">Rules.</span></span> <span data-ttu-id="cba5d-202">您可以設定規則來控制圖層上所有地圖元素的色彩、大小、寬度或標記類型。</span><span class="sxs-lookup"><span data-stu-id="cba5d-202">You can set rules to control color, size, width, or marker type for all map elements on a layer.</span></span> <span data-ttu-id="cba5d-203">您可以設定的規則取決於地圖圖層的類型。</span><span class="sxs-lookup"><span data-stu-id="cba5d-203">The rules that you can set depend on the type of map element.</span></span>  
  
    -   <span data-ttu-id="cba5d-204">色彩規則。</span><span class="sxs-lookup"><span data-stu-id="cba5d-204">Color Rules.</span></span> <span data-ttu-id="cba5d-205">適用於點、線條、多邊形的標記，以及多邊形中心點的標記。</span><span class="sxs-lookup"><span data-stu-id="cba5d-205">Apply to markers for points, lines, polygons, and markers for polygon center points.</span></span>  
  
    -   <span data-ttu-id="cba5d-206">大小規則。</span><span class="sxs-lookup"><span data-stu-id="cba5d-206">Size Rules.</span></span> <span data-ttu-id="cba5d-207">適用於點的標記，以及多邊形中心點的標記。</span><span class="sxs-lookup"><span data-stu-id="cba5d-207">Apply to markers for points and markers for polygon center points.</span></span>  
  
    -   <span data-ttu-id="cba5d-208">寬度規則。</span><span class="sxs-lookup"><span data-stu-id="cba5d-208">Width Rules.</span></span> <span data-ttu-id="cba5d-209">適用於線條寬度。</span><span class="sxs-lookup"><span data-stu-id="cba5d-209">Applies to line widths.</span></span>  
  
    -   <span data-ttu-id="cba5d-210">標記類型規則。</span><span class="sxs-lookup"><span data-stu-id="cba5d-210">Marker Type Rules.</span></span> <span data-ttu-id="cba5d-211">適用於點的標記，以及多邊形中心點的標記。</span><span class="sxs-lookup"><span data-stu-id="cba5d-211">Applies to markers for points and markers for polygon center points.</span></span>  
  
-   <span data-ttu-id="cba5d-212">圖層上個別內嵌點、線條或多邊形的覆寫選項。</span><span class="sxs-lookup"><span data-stu-id="cba5d-212">Override options for individual embedded points, lines, or polygons on a layer.</span></span> <span data-ttu-id="cba5d-213">您所做的變更是永久的。</span><span class="sxs-lookup"><span data-stu-id="cba5d-213">Changes that you make are permanent.</span></span> <span data-ttu-id="cba5d-214">若要還原這些變更，您必須重新載入圖層的資料。</span><span class="sxs-lookup"><span data-stu-id="cba5d-214">To revert these changes, you must reload the data for the layer.</span></span>  
  
 <span data-ttu-id="cba5d-215">如需詳細資訊，請參閱 [使用規則與分析資料更改多邊形、線條與點顯示 &#40;報表產生器及 SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)。</span><span class="sxs-lookup"><span data-stu-id="cba5d-215">For more information, see [Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="cba5d-216">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cba5d-216">See Also</span></span>  
 <span data-ttu-id="cba5d-217">[地圖精靈與地圖圖層精靈 &#40;報表產生器及 SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cba5d-217">[Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="cba5d-218">地圖 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="cba5d-218">Maps &#40;Report Builder and SSRS&#41;</span></span>](maps-report-builder-and-ssrs.md)  
  
  
