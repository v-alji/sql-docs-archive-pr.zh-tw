---
title: 教學課程：地圖報表 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8d831356-7efa-40cc-ae95-383b3eecf833
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b737bb3fe74eb3524f2944a7458cb4837b1aeedf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706101"
---
# <a name="tutorial-map-report-report-builder"></a><span data-ttu-id="2a245-102">教學課程：地圖報表 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="2a245-102">Tutorial: Map Report (Report Builder)</span></span>
  <span data-ttu-id="2a245-103">本教學課程的設計在於協助您了解，可對照地理背景顯示報告資料的地圖功能。</span><span class="sxs-lookup"><span data-stu-id="2a245-103">This tutorial is designed to help you learn about the map features you can use to display report data against a geographic background.</span></span>  
  
 <span data-ttu-id="2a245-104">地圖是以空間資料為基礎，通常由點、線條和多邊形所組成。</span><span class="sxs-lookup"><span data-stu-id="2a245-104">Maps are based on spatial data that typically consists of points, lines, and polygons.</span></span> <span data-ttu-id="2a245-105">例如，多邊行可表示某一縣的輪廓，線條可表示一條路，點則可表示城市的位置。</span><span class="sxs-lookup"><span data-stu-id="2a245-105">For example, a polygon can represent the outline of a county, a line can represent a road, and a point can represent the location of a city.</span></span> <span data-ttu-id="2a245-106">每一種空間資料會在不同的地圖圖層上顯示為一組地圖元素。</span><span class="sxs-lookup"><span data-stu-id="2a245-106">Each type of spatial data is displayed on a separate map layer as a set of map elements.</span></span>  
  
 <span data-ttu-id="2a245-107">若要變化地圖元素的外觀，可以指定一個欄位，其中包含比對地圖元素與資料集中分析資料的值。</span><span class="sxs-lookup"><span data-stu-id="2a245-107">To vary the appearance of map elements, you specify a field that has values that match the map elements with analytical data from a dataset.</span></span> <span data-ttu-id="2a245-108">您也可以定義規則，使色彩、大小或其他屬性根據某個資料範圍變化。</span><span class="sxs-lookup"><span data-stu-id="2a245-108">You can also define rules that vary color, size, or other properties based on ranges of data.</span></span>  
  
 <span data-ttu-id="2a245-109">在本教學課程中，您將建立地圖報表，用於顯示紐約州各郡的商店位置。</span><span class="sxs-lookup"><span data-stu-id="2a245-109">In this tutorial, you will build a map report that displays store locations in New York state counties.</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="2a245-110">您將瞭解的內容</span><span class="sxs-lookup"><span data-stu-id="2a245-110">What You Will Learn</span></span>  
 <span data-ttu-id="2a245-111">在本教學課程中，您將學習如何執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="2a245-111">In this tutorial you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="2a245-112">從地圖精靈建立含多邊形圖層的地圖</span><span class="sxs-lookup"><span data-stu-id="2a245-112">Create a Map with a Polygon Layer from the Map Wizard</span></span>](#Map)  
  
2.  [<span data-ttu-id="2a245-113">加入地圖點圖層以顯示商店位置</span><span class="sxs-lookup"><span data-stu-id="2a245-113">Add a Map Point Layer to Display Store Locations</span></span>](#PointLayer)  
  
3.  [<span data-ttu-id="2a245-114">加入地圖線條圖層以顯示路線</span><span class="sxs-lookup"><span data-stu-id="2a245-114">Add a Map Line Layer to Display a Route</span></span>](#LineLayer)  
  
4.  [<span data-ttu-id="2a245-115">加入 Bing Maps 圖格背景</span><span class="sxs-lookup"><span data-stu-id="2a245-115">Add a Bing Maps Tile Background</span></span>](#TileLayer)  
  
5.  [<span data-ttu-id="2a245-116">使圖層變透明</span><span class="sxs-lookup"><span data-stu-id="2a245-116">Make a Layer Transparent</span></span>](#Transparent)  
  
6.  [<span data-ttu-id="2a245-117">依據銷售量變化郡的色彩</span><span class="sxs-lookup"><span data-stu-id="2a245-117">Vary County Color Based on Sales</span></span>](#Vary)  
  
    1.  [<span data-ttu-id="2a245-118">建立空間資料與分析資料之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="2a245-118">Build a Relationship between Spatial and Analytical Data</span></span>](#Relationship)  
  
    2.  [<span data-ttu-id="2a245-119">指定多邊形的色彩規則</span><span class="sxs-lookup"><span data-stu-id="2a245-119">Specify Color Rules for Polygons</span></span>](#ColorRules)  
  
    3.  [<span data-ttu-id="2a245-120">依據貨幣格式化色階中的資料</span><span class="sxs-lookup"><span data-stu-id="2a245-120">Format the Data in the Color Scale as Currency</span></span>](#ColorScale)  
  
    4.  [<span data-ttu-id="2a245-121">建立新的圖例</span><span class="sxs-lookup"><span data-stu-id="2a245-121">Create a New Legend</span></span>](#NewLegend)  
  
    5.  [<span data-ttu-id="2a245-122">讓圖例與色彩規則產生關聯</span><span class="sxs-lookup"><span data-stu-id="2a245-122">Associate Legend and Color Rules</span></span>](#Associate)  
  
    6.  [<span data-ttu-id="2a245-123">清除未包含資料之郡的色彩</span><span class="sxs-lookup"><span data-stu-id="2a245-123">Clear Color from Counties with No Data</span></span>](#NoData)  
  
7.  [<span data-ttu-id="2a245-124">加入自訂點</span><span class="sxs-lookup"><span data-stu-id="2a245-124">Add a Custom Point</span></span>](#CustomPoint)  
  
8.  [<span data-ttu-id="2a245-125">將地圖檢視置中</span><span class="sxs-lookup"><span data-stu-id="2a245-125">Center the Map View</span></span>](#CenterView)  
  
9. [<span data-ttu-id="2a245-126">加入報表標題</span><span class="sxs-lookup"><span data-stu-id="2a245-126">Add a Report Title</span></span>](#Title)  
  
10. [<span data-ttu-id="2a245-127">儲存報表</span><span class="sxs-lookup"><span data-stu-id="2a245-127">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="2a245-128">在本教學課程中，精靈的步驟會合併成兩個程序：一個程序用來建立資料集，另一個程序用來建立資料表。</span><span class="sxs-lookup"><span data-stu-id="2a245-128">In this tutorial, the steps for the wizard are consolidated into two procedures: one to create the dataset and one to create a table.</span></span> <span data-ttu-id="2a245-129">如需如何瀏覽至報表伺服器、選擇資料來源、建立資料集以及執行精靈的逐步指示，請參閱本系列的第一個教學課程：[教學課程：建立基本資料表報表 &#40;報表產生器&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="2a245-129">For step-by-step instructions about how to browse to a report server, choose a data source, create a dataset, and run the wizard, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="2a245-130">完成本教學課程的估計時間：30 分鐘。</span><span class="sxs-lookup"><span data-stu-id="2a245-130">Estimated time to complete this tutorial: 30 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a245-131">需求</span><span class="sxs-lookup"><span data-stu-id="2a245-131">Requirements</span></span>  
 <span data-ttu-id="2a245-132">如需需求的資訊，請參閱[教學課程的必要條件 &#40;報表產生器&#41;](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="2a245-132">For information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-map-with-a-polygon-layer-from-the-map-wizard"></a><a name="Map"></a><span data-ttu-id="2a245-133">1. 從地圖 Wizard 建立具有多邊形圖層的地圖</span><span class="sxs-lookup"><span data-stu-id="2a245-133">1. Create a Map with a Polygon Layer from the Map Wizard</span></span>  
 <span data-ttu-id="2a245-134">從地圖庫將地圖加入至報表。</span><span class="sxs-lookup"><span data-stu-id="2a245-134">Add a map to your report from the map gallery.</span></span> <span data-ttu-id="2a245-135">地圖中包含一個顯示紐約州各郡的圖層。</span><span class="sxs-lookup"><span data-stu-id="2a245-135">The map has one layer that displays the counties in New York state.</span></span> <span data-ttu-id="2a245-136">各郡的形狀是以空間資料為基礎的多邊形，這些資料內嵌於地圖庫的地圖中。</span><span class="sxs-lookup"><span data-stu-id="2a245-136">The shape of each county is a polygon based on spatial data that is embedded in the map from the map gallery.</span></span>  
  
#### <a name="to-add-a-map-with-the-map-wizard-in-a-new-report"></a><span data-ttu-id="2a245-137">使用新報表中的地圖精靈加入地圖</span><span class="sxs-lookup"><span data-stu-id="2a245-137">To add a map with the map wizard in a new report</span></span>  
  
1.  <span data-ttu-id="2a245-138">按一下 [ **開始**]、依序指向 [ **程式集**] 和 [ [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**報表產生器**]，然後按一下 [ **報表產生器**]。</span><span class="sxs-lookup"><span data-stu-id="2a245-138">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="2a245-139">[使用者入門] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="2a245-139">The Getting Started dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2a245-140"> 如果 [使用者入門] 對話方塊沒有出現，請在 [報表產生器] 按鈕中按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-140">If the Getting Started dialog box does not appear, from the Report Builder button, click **New**.</span></span>  
  
2.  <span data-ttu-id="2a245-141">在左窗格中，確認已選取 **[報表]** 。</span><span class="sxs-lookup"><span data-stu-id="2a245-141">In the left pane, verify that **Report** is selected.</span></span>  
  
3.  <span data-ttu-id="2a245-142">在右窗格中，按一下 **[地圖精靈]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-142">In the right pane, click **Map Wizard**.</span></span>  
  
4.  <span data-ttu-id="2a245-143">按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="2a245-143">Click **Create**.</span></span>  
  
5.  <span data-ttu-id="2a245-144">在 **[選擇空間資料的來源]** 頁面中，確認已選取 **[地圖庫]** 。</span><span class="sxs-lookup"><span data-stu-id="2a245-144">**Choose a source of spatial data** page, verify that **Map gallery** is selected.</span></span>  
  
6.  <span data-ttu-id="2a245-145">在 [地圖庫] 窗格中，展開 **[USA]** 下的 **[依郡的州]**，然後按一下 **[紐約]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-145">In the Map Gallery pane, expand **States by County** under **USA**, and click **New York**.</span></span>  
  
     <span data-ttu-id="2a245-146">[地圖預覽] 窗格會顯示紐約郡的地圖。</span><span class="sxs-lookup"><span data-stu-id="2a245-146">The Map Preview pane displays the New York county map.</span></span>  
  
7.  <span data-ttu-id="2a245-147">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="2a245-147">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="2a245-148">接受 **[選擇空間資料及地圖檢視選項]** 頁面上的預設值。</span><span class="sxs-lookup"><span data-stu-id="2a245-148">On the **Choose spatial data and map view options** page, accept the defaults.</span></span> <span data-ttu-id="2a245-149">根據預設，地圖庫中的地圖元素將自動內嵌在報表定義中。</span><span class="sxs-lookup"><span data-stu-id="2a245-149">By default, map elements from a map gallery will automatically be embedded in the report definition.</span></span>  
  
9. <span data-ttu-id="2a245-150">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="2a245-150">Click **Next**.</span></span>  
  
10. <span data-ttu-id="2a245-151">在 **[選擇地圖視覺效果]** 頁面上，確認已選取 **[基本地圖]** ，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-151">On the **Choose map visualization** page, verify **Basic Map** is selected, and click **Next**.</span></span>  
  
11. <span data-ttu-id="2a245-152">在 **[選擇色彩主題和資料視覺效果]** 頁面上，選取 **[顯示標籤]** 選項。</span><span class="sxs-lookup"><span data-stu-id="2a245-152">On the **Choose color theme and data visualization** page, select the **Display labels** option.</span></span>  
  
12. <span data-ttu-id="2a245-153">如果已經選取 **[單色地圖]** 選項，請清除該選項。</span><span class="sxs-lookup"><span data-stu-id="2a245-153">If it is selected, clear the **Single color map** option.</span></span>  
  
13. <span data-ttu-id="2a245-154">從 [**資料欄位**] 下拉式清單中，按一下 [#COUNTYNAME]。</span><span class="sxs-lookup"><span data-stu-id="2a245-154">From the **Data field** drop-down list, click #COUNTYNAME.</span></span> <span data-ttu-id="2a245-155">精靈中的 [地圖預覽] 窗格會顯示下列項目：</span><span class="sxs-lookup"><span data-stu-id="2a245-155">The Map Preview pane in the wizard displays the following items:</span></span>  
  
    -   <span data-ttu-id="2a245-156">包含 **地圖標題**文字的標題。</span><span class="sxs-lookup"><span data-stu-id="2a245-156">A title with the text **Map Title**.</span></span>  
  
    -   <span data-ttu-id="2a245-157">顯示紐約各郡的地圖，其中各郡都是不同的色彩，而且每次郡名稱符合郡區域時就會顯示出來。</span><span class="sxs-lookup"><span data-stu-id="2a245-157">A map that displays counties in New York where each county is a different color and the county name appears wherever it fits over the county area.</span></span>  
  
    -   <span data-ttu-id="2a245-158">包含標題以及項目 1 至 5 之清單的圖例。</span><span class="sxs-lookup"><span data-stu-id="2a245-158">A legend that contains a title and a list of items 1 through 5.</span></span>  
  
    -   <span data-ttu-id="2a245-159">包含值 0 到 160，而且沒有色彩的色階。</span><span class="sxs-lookup"><span data-stu-id="2a245-159">A color scale that contains values 0 to 160 and no color.</span></span>  
  
    -   <span data-ttu-id="2a245-160">顯示公里 (km) 和英哩 (mi) 的距離標尺。</span><span class="sxs-lookup"><span data-stu-id="2a245-160">A distance scale that displays kilometers (km) and miles (mi).</span></span>  
  
14. <span data-ttu-id="2a245-161">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="2a245-161">Click **Finish**.</span></span>  
  
     <span data-ttu-id="2a245-162">地圖就會加入至設計介面。</span><span class="sxs-lookup"><span data-stu-id="2a245-162">The map is added to the design surface.</span></span>  
  
15. <span data-ttu-id="2a245-163">按一下地圖來選取它，然後顯示 **[地圖圖層]** 窗格。</span><span class="sxs-lookup"><span data-stu-id="2a245-163">Click the map to select it and display the **Map Layers Pane**.</span></span> <span data-ttu-id="2a245-164">**[地圖圖層]** 窗格會顯示一個 **[內嵌]** 圖層類型的多邊形圖層。</span><span class="sxs-lookup"><span data-stu-id="2a245-164">The **Map Layers Pane** shows one polygon layer of layer type **Embedded**.</span></span> <span data-ttu-id="2a245-165">每個郡在此圖層上都是一個內嵌的地圖元素。</span><span class="sxs-lookup"><span data-stu-id="2a245-165">Each county is an embedded map element on this layer.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2a245-166">如果看不到 **[地圖圖層]** 窗格，表示它可能在目前檢視之外顯示。</span><span class="sxs-lookup"><span data-stu-id="2a245-166">If you do not see the **Map Layers** pane, it might be displayed outside your current view.</span></span> <span data-ttu-id="2a245-167">請使用 [設計檢視] 視窗底部的捲軸來切換檢視。</span><span class="sxs-lookup"><span data-stu-id="2a245-167">Use the scroll bar at the bottom of the Design view window to change your view.</span></span> <span data-ttu-id="2a245-168">或者，在 **[檢視]** 索引標籤中，清除 **[屬性]** 或 **[報表資料]** 選項，即可提供更多設計介面區域。</span><span class="sxs-lookup"><span data-stu-id="2a245-168">Alternatively, in the **View** tab, clear the **Properties** or the **Report Data** option to provide more design surface area.</span></span>  
  
16. <span data-ttu-id="2a245-169">以滑鼠右鍵按一下地圖標題，然後按一下 **[標題屬性]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-169">Right-click the map title, and then click **Title Properties**.</span></span>  
  
17. <span data-ttu-id="2a245-170">將標題文字取代成 **依商店的銷售量**。</span><span class="sxs-lookup"><span data-stu-id="2a245-170">Replace the title text with **Sales by Store**.</span></span>  
  
18. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
19. <span data-ttu-id="2a245-171">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="2a245-171">Preview the report.</span></span>  
  
 <span data-ttu-id="2a245-172">呈現的報表會顯示地圖標題、地圖和距離標尺。</span><span class="sxs-lookup"><span data-stu-id="2a245-172">The rendered report displays the map title, the map, and the distance scale.</span></span> <span data-ttu-id="2a245-173">各郡會位於地圖多邊形圖層上。</span><span class="sxs-lookup"><span data-stu-id="2a245-173">The counties are on a map polygon layer.</span></span> <span data-ttu-id="2a245-174">每一個郡都是一個多邊形，其色彩會依色彩調色盤的色彩而變化，但是這些色彩不會與任何資料產生關聯。</span><span class="sxs-lookup"><span data-stu-id="2a245-174">Each county is a polygon that varies by color from a color palette, but the colors are not associated with any data.</span></span> <span data-ttu-id="2a245-175">距離標尺會同時以公里和英哩顯示距離。</span><span class="sxs-lookup"><span data-stu-id="2a245-175">The distance scale displays distances in both kilometers and miles.</span></span>  
  
 <span data-ttu-id="2a245-176">地圖圖例和色階因為沒有與各郡相關聯的分析資料，因此不會顯示。</span><span class="sxs-lookup"><span data-stu-id="2a245-176">The map legend and color scale do not yet appear because there is no analytical data associated with each county.</span></span> <span data-ttu-id="2a245-177">您稍後將在本教學課程中加入分析資料。</span><span class="sxs-lookup"><span data-stu-id="2a245-177">You will add analytical data later in this tutorial.</span></span>  
  
##  <a name="2-add-a-map-point-layer-to-display-store-locations"></a><a name="PointLayer"></a><span data-ttu-id="2a245-178">2. 加入地圖點圖層以顯示商店位置</span><span class="sxs-lookup"><span data-stu-id="2a245-178">2. Add a Map Point Layer to Display Store Locations</span></span>  
 <span data-ttu-id="2a245-179">使用地圖圖層精靈加入點圖層，用於顯示商店的位置。</span><span class="sxs-lookup"><span data-stu-id="2a245-179">Use the map layer wizard to add a point layer that displays the locations of stores.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a245-180">在本教學課程中，查詢會包含資料值，因此不需要外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="2a245-180">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="2a245-181">這樣會使查詢相當冗長。</span><span class="sxs-lookup"><span data-stu-id="2a245-181">This makes the query quite long.</span></span> <span data-ttu-id="2a245-182">在商業環境中，查詢不會包含資料。</span><span class="sxs-lookup"><span data-stu-id="2a245-182">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="2a245-183">這僅供教學之用。</span><span class="sxs-lookup"><span data-stu-id="2a245-183">This is for learning purposes only.</span></span>  
  
#### <a name="to-add-a-point-layer-based-on-a-sql-server-spatial-query"></a><span data-ttu-id="2a245-184">根據 SQL Server 空間查詢加入點圖層</span><span class="sxs-lookup"><span data-stu-id="2a245-184">To add a point layer based on a SQL Server spatial query</span></span>  
  
1.  <span data-ttu-id="2a245-185">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="2a245-185">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="2a245-186">按兩下地圖來顯示 **[地圖圖層]** 窗格。</span><span class="sxs-lookup"><span data-stu-id="2a245-186">Double-click the map to display the **Map Layer** pane.</span></span> <span data-ttu-id="2a245-187">在工具列上，按一下**新增圖層精靈**按鈕 ![rs_IconMapLayerWizard](../../2014/tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard")。</span><span class="sxs-lookup"><span data-stu-id="2a245-187">On the toolbar, click the **New layer wizard** button ![rs_IconMapLayerWizard](../../2014/tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard").</span></span>  
  
3.  <span data-ttu-id="2a245-188">在 [**選擇空間資料的來源**] 頁面上，選取 [ **SQL Server 空間查詢**]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-188">On the **Choose a source of spatial data** page, select **SQL Server spatial query**, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="2a245-189">在 **[選擇含有 SQL Server 空間資料的資料集]** 頁面上，按一下 **[新增含有 SQL Server 空間資料的資料集]**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-189">On the **Choose a dataset with SQL Server spatial data** page, click **Add a new dataset with SQL Server spatial data**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="2a245-190">在 **[選擇到 SQL Server 空間資料來源的連接]** 頁面上，選取現有的資料來源，或瀏覽至報表伺服器並選取資料來源。</span><span class="sxs-lookup"><span data-stu-id="2a245-190">On the **Choose a connection to a SQL Server spatial data source** page, select an existing data source or browse to the report server and select a data source.</span></span>  
  
6.  <span data-ttu-id="2a245-191">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="2a245-191">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="2a245-192">在 [設計查詢] 頁面上，按一下 [當做**文字編輯**]。</span><span class="sxs-lookup"><span data-stu-id="2a245-192">On the Design a Query page, click **Edit as Text**.</span></span>  
  
8.  <span data-ttu-id="2a245-193">在 [查詢] 窗格中，貼上下列文字：</span><span class="sxs-lookup"><span data-stu-id="2a245-193">Paste the following text in the query pane:</span></span>  
  
    ```  
    Select 114 as StoreKey, 'Contoso Albany Store' as StoreName, 1125 as SellingArea, 'Albany' as City, 'Albany' as County,   
     CAST(1000000 as money) as Sales, CAST('POINT(-73.7472924218681 42.6564617079878)' as geography) AS SpatialLocation  
    UNION ALL SELECT 115 AS StoreKey, 'Contoso New York No.1 Store' AS  StoreName, 500 as SellingArea, 'New York' AS City, 'New York City' as County,  
     CAST('2000000' as money) as Sales, CAST('POINT(-73.9922069374483 40.7549638237402)' as geography) AS SpatialLocation  
    UNION ALL Select 116 as StoreKey, 'Contoso Rochester No.1 Store' as StoreName, 462 as SellingArea, 'Rochester' as City,  'Monroe' as County,    
     CAST(3000000 as money) as Sales, CAST('POINT(-77.624041566786 43.1547066024338)' as geography)  AS SpatialLocation  
    UNION ALL Select 117 as StoreKey, 'Contoso New York No.2 Store' as StoreName, 700 as SellingArea, 'New York' as City,'New York City' as County,    
      CAST(4000000 as money) as Sales, CAST('POINT(-73.9712488 40.7830603)' as geography) AS SpatialLocation  
    UNION ALL Select 118 as StoreKey, 'Contoso Syracuse Store' as StoreName, 680 as SellingArea, 'Syracuse' as City, 'Onondaga' as County,  
     CAST(5000000 as money) as Sales, CAST('POINT(-76.1349120532546 43.0610223535974)' as geography) AS SpatialLocation  
    UNION ALL Select 120 as StoreKey, 'Contoso Plattsburgh Store' as StoreName, 560 as SellingArea, 'Plattsburgh' as City,  'Clinton' as County,  
     CAST(6000000 as money) as Sales, CAST('POINT(-73.4728622833178 44.7028831413324)' as geography) AS SpatialLocation  
    UNION ALL Select 121 as StoreKey, 'Contoso Brooklyn Store' as StoreName, 1125 as SellingArea, 'Brooklyn' as City, 'New York City' as County,  
     CAST(7000000 as money) as Sales, CAST('POINT (-73.9638533447143 40.6785123489351)' as geography) AS SpatialLocation  
    UNION ALL Select 122 as StoreKey, 'Contoso Oswego Store' as StoreName, 500 as SellingArea, 'Oswego' as City, 'Oswego' as County,    
     CAST(8000000 as money) as Sales, CAST('POINT(-76.4602850815536 43.4353224527794)' as geography) AS SpatialLocation  
    UNION ALL Select 123 as StoreKey, 'Contoso Ithaca Store' as StoreName, 460 as SellingArea, 'Ithaca' as City, 'Tompkins' as County,  
     CAST(9000000 as money) as Sales, CAST('POINT(-76.5001866085881 42.4310489934743)' as geography) AS SpatialLocation  
    UNION ALL Select 124 as StoreKey, 'Contoso Rochester No.2 Store' as StoreName, 700 as SellingArea, 'Rochester' as City, 'Monroe' as County,    
     CAST(100000 as money) as Sales, CAST('POINT(-77.6240415667866 43.1547066024338)' as geography) AS SpatialLocation  
    UNION ALL Select 125 as StoreKey, 'Contoso Queens Store' as StoreName, 700 as SellingArea,'Queens' as City, 'New York City' as County,  
     CAST(500000 as money) as Sales, CAST('POINT(-73.7930979029883 40.7152781765927)' as geography) AS SpatialLocation  
    UNION ALL Select 126 as StoreKey, 'Contoso Elmira Store' as StoreName, 680 as SellingArea, 'Elmira' as City, 'Chemung' as County,  
     CAST(800000 as money) as Sales, CAST('POINT(-76.7397414783301 42.0736492742663)' as geography) AS SpatialLocation  
    UNION ALL Select 127 as StoreKey, 'Contoso Poestenkill Store' as StoreName, 455 as SellingArea, 'Poestenkill' as City, 'Rensselaer' as County,    
    CAST(1500000 as money) as Sales, CAST('POINT(-73.5626737425063 42.6940551238618)' as geography) AS SpatialLocation  
    ```  
  
9. <span data-ttu-id="2a245-194">在 [查詢設計工具] 工具列上，按一下 [**執行**] (**！**) 。</span><span class="sxs-lookup"><span data-stu-id="2a245-194">On the query designer toolbar, click **Run** (**!**).</span></span>  
  
     <span data-ttu-id="2a245-195">結果集會顯示七個資料行：StoreKey、StoreName、SellingArea、City、County、Sales 和 SpatialLocation。</span><span class="sxs-lookup"><span data-stu-id="2a245-195">The result set displays seven columns: StoreKey, StoreName, SellingArea, City, County, Sales, and SpatialLocation.</span></span> <span data-ttu-id="2a245-196">此資料表示在紐約州中販賣消費品的商店集。</span><span class="sxs-lookup"><span data-stu-id="2a245-196">This data represents a set of stores in New York State that sell consumer goods.</span></span> <span data-ttu-id="2a245-197">結果集中的每個資料列都包含一個商店識別碼、商店名稱、可用於產品展示的區域、商店所在的城市和郡、銷售總額，以及經緯度的空間位置。</span><span class="sxs-lookup"><span data-stu-id="2a245-197">Each row in the result set contains a store identifier, store name, the area available for product display, the city and county where the store is located, the sales total, and the spatial location in longitude and latitude.</span></span> <span data-ttu-id="2a245-198">展示區域的範圍是從 455 平方英尺到 1125 平方英尺。</span><span class="sxs-lookup"><span data-stu-id="2a245-198">The display area ranges from 455 square feet to 1125 square feet.</span></span>  
  
10. <span data-ttu-id="2a245-199">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="2a245-199">Click **Next**.</span></span>  
  
     <span data-ttu-id="2a245-200">此時會為您建立名為 DataSet1 的報表資料集。</span><span class="sxs-lookup"><span data-stu-id="2a245-200">The report dataset named DataSet1 is created for you.</span></span> <span data-ttu-id="2a245-201">在完成精靈後，可以使用 [報表資料] 來檢視其欄位集合。</span><span class="sxs-lookup"><span data-stu-id="2a245-201">After you complete the wizard, you can use the Report Data to its field collection.</span></span>  
  
11. <span data-ttu-id="2a245-202">在 [**選擇空間資料和地圖視圖選項**] 頁面上，確認 [**空間] 欄位**為 `SpatialLocation` ，而 [**圖層類型**] 為 [**點**]。</span><span class="sxs-lookup"><span data-stu-id="2a245-202">On the **Choose a spatial data and map view options** page, verify that the **Spatial field** is `SpatialLocation` and that the **Layer type** is **Point**.</span></span> <span data-ttu-id="2a245-203">接受此頁面上的其他預設值。</span><span class="sxs-lookup"><span data-stu-id="2a245-203">Accept the other defaults on this page.</span></span>  
  
     <span data-ttu-id="2a245-204">地圖檢視會顯示圓形，這些圓形會標示每一家商店的位置。</span><span class="sxs-lookup"><span data-stu-id="2a245-204">The map view displays circles that mark the location of each store.</span></span>  
  
12. <span data-ttu-id="2a245-205">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="2a245-205">Click **Next**.</span></span>  
  
13. <span data-ttu-id="2a245-206">指定地圖類型，此地圖會顯示依分析資料更改的標記。</span><span class="sxs-lookup"><span data-stu-id="2a245-206">Specify a map type that displays markers that vary by analytic data.</span></span> <span data-ttu-id="2a245-207">在 [選擇地圖視覺效果] 頁面上，按一下 **[分析標記地圖]**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-207">On the Choose map visualization page, click **Analytical Marker Map**, and then click **Next**.</span></span>  
  
14. <span data-ttu-id="2a245-208">在 **[選擇分析資料集]** 頁面上，按一下 DataSet1。</span><span class="sxs-lookup"><span data-stu-id="2a245-208">On the **Choose the analytical dataset** page, click DataSet1.</span></span> <span data-ttu-id="2a245-209">此資料集同時包含將在新的點圖層上顯示的分析資料和空間資料。</span><span class="sxs-lookup"><span data-stu-id="2a245-209">This dataset contains both analytical data and spatial data that will be displayed on the new point layer.</span></span>  
  
15. <span data-ttu-id="2a245-210">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="2a245-210">Click **Next**.</span></span>  
  
16. <span data-ttu-id="2a245-211">在 **[選擇色彩主題和資料視覺效果]** 頁面上，清除 **[使用標記色彩將資料視覺化]** 選項，然後選取 **[使用標記類型將資料視覺化]** 選項。</span><span class="sxs-lookup"><span data-stu-id="2a245-211">On the **Choose color theme and data visualization** page, clear the **Use marker colors to visualize data** option, and then select the option **Use marker types to visualize data**.</span></span>  
  
17. <span data-ttu-id="2a245-212">在 **[資料欄位]** 中選取 `[Sum(SellingArea)]` ，讓標記類型依據保留用於顯示產品的區域大小變化。</span><span class="sxs-lookup"><span data-stu-id="2a245-212">In **Data field**, select `[Sum(SellingArea)]` to vary marker types by the size of the area a store sets aside to display the products.</span></span>  
  
18. <span data-ttu-id="2a245-213">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="2a245-213">Click **Finish**.</span></span>  
  
     <span data-ttu-id="2a245-214">地圖圖層會加入至報表。</span><span class="sxs-lookup"><span data-stu-id="2a245-214">The map layer is added to the report.</span></span> <span data-ttu-id="2a245-215">圖例會根據 SellingArea 值顯示標記類型。</span><span class="sxs-lookup"><span data-stu-id="2a245-215">The legend displays marker types based on SellingArea values.</span></span>  
  
     <span data-ttu-id="2a245-216">按兩下地圖來顯示 **[地圖圖層]** 窗格。</span><span class="sxs-lookup"><span data-stu-id="2a245-216">Double-click the map to display the **Map Layer** pane.</span></span> <span data-ttu-id="2a245-217">**[地圖圖層]** 窗格會顯示一個新圖層 PointLayer1，其空間資料來源類型為 **DataRegion**。</span><span class="sxs-lookup"><span data-stu-id="2a245-217">The **Map Layer** pane displays a new layer, PointLayer1, with spatial data source type **DataRegion**.</span></span>  
  
19. <span data-ttu-id="2a245-218">加入圖例標題。</span><span class="sxs-lookup"><span data-stu-id="2a245-218">Add a legend title.</span></span> <span data-ttu-id="2a245-219">以滑鼠右鍵按一下圖例標題，然後按一下 **[圖例標題屬性]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-219">Right-click the legend title, and then click **Legend Title Properties**.</span></span>  
  
20. <span data-ttu-id="2a245-220">刪除標題，然後輸入 **顯示區域 (平方英尺)**。</span><span class="sxs-lookup"><span data-stu-id="2a245-220">Delete the title, and type **Display Area (Square Feet)**.</span></span>  
  
21. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
22. <span data-ttu-id="2a245-221">檢視精靈設定的預設值。</span><span class="sxs-lookup"><span data-stu-id="2a245-221">View the default values that were set by the wizard.</span></span> <span data-ttu-id="2a245-222">在 **[地圖圖層]** 窗格中，以滑鼠右鍵按一下點圖層，然後按一下 **[標記類型規則]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-222">In the **Map Layers Pane**, right-click the point layer, and then click **Marker Type Rule**.</span></span>  
  
     <span data-ttu-id="2a245-223">在 **[一般]** 索引標籤上，標記會依照出現在圖例中的順序列出。</span><span class="sxs-lookup"><span data-stu-id="2a245-223">On the **General** tab, the markers are listed in the order in which they appear in the legend.</span></span> <span data-ttu-id="2a245-224">在 **[分佈]** 索引標籤上，子範圍的數目為 5。</span><span class="sxs-lookup"><span data-stu-id="2a245-224">On the **Distribution** tab, the number of subranges is 5.</span></span> <span data-ttu-id="2a245-225">在 **[圖例]** 索引標籤上，圖例文字會設為顯示每個範圍的開始和結束值。</span><span class="sxs-lookup"><span data-stu-id="2a245-225">On the **Legend** tab, the legend text is set to display the start and end value in each range.</span></span>  
  
23. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
24. <span data-ttu-id="2a245-226">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="2a245-226">Preview the report.</span></span>  
  
 <span data-ttu-id="2a245-227">地圖會顯示紐約州商店的位置。</span><span class="sxs-lookup"><span data-stu-id="2a245-227">The map displays the locations of stores in New York state.</span></span> <span data-ttu-id="2a245-228">每家商店的標記類型是根據顯示區域而定。</span><span class="sxs-lookup"><span data-stu-id="2a245-228">The marker type for each store is based on the display area.</span></span> <span data-ttu-id="2a245-229">有五種顯示區域範圍會自動計算。</span><span class="sxs-lookup"><span data-stu-id="2a245-229">Five ranges of display area were automatically calculated for you.</span></span>  
  
##  <a name="3-add-a-map-line-layer-to-display-a-route"></a><a name="LineLayer"></a><span data-ttu-id="2a245-230">3. 加入地圖線條圖層以顯示路線</span><span class="sxs-lookup"><span data-stu-id="2a245-230">3. Add a Map Line Layer to Display a Route</span></span>  
 <span data-ttu-id="2a245-231">使用地圖圖層精靈，加入顯示兩個商店之間路線的地圖圖層。</span><span class="sxs-lookup"><span data-stu-id="2a245-231">Use the map layer wizard to add a map layer that displays a route between two stores.</span></span> <span data-ttu-id="2a245-232">在本教學課程中，路徑是從三個商店位置建立。</span><span class="sxs-lookup"><span data-stu-id="2a245-232">In this tutorial, the path is created from three store locations.</span></span> <span data-ttu-id="2a245-233">在商業應用程式中，路徑可能是商店之間的最佳路線。</span><span class="sxs-lookup"><span data-stu-id="2a245-233">In a business application, the path might be the best route between stores.</span></span>  
  
#### <a name="to-add-a-line-layer-to-map"></a><span data-ttu-id="2a245-234">將線條圖層加入至地圖</span><span class="sxs-lookup"><span data-stu-id="2a245-234">To add a line layer to map</span></span>  
  
1.  <span data-ttu-id="2a245-235">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="2a245-235">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="2a245-236">按兩下地圖來顯示 **[地圖圖層]** 窗格。</span><span class="sxs-lookup"><span data-stu-id="2a245-236">Double-click the map to display the **Map Layer** pane.</span></span> <span data-ttu-id="2a245-237">在工具列上，按一下 **[新增圖層精靈]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-237">On the toolbar, click **New layer wizard**.</span></span>  
  
3.  <span data-ttu-id="2a245-238">在 **[選擇空間資料的來源]** 頁面上，選取 **[SQL Server 空間查詢]** ，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-238">On the **Choose a source of spatial data** page, select **SQL Server spatial query** and click **Next**.</span></span>  
  
4.  <span data-ttu-id="2a245-239">在 **[選擇含有 SQL Server 空間資料的資料集]** 頁面上，按一下 **[新增含有 SQL Server 空間資料的資料集]** ，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-239">On the **Choose a dataset with SQL Server spatial data** page, click **Add a new dataset with SQL Server spatial data** and click **Next**.</span></span>  
  
5.  <span data-ttu-id="2a245-240">在 **[選擇到 SQL Server 空間資料來源的連接]** 上，選取 [DataSource1]，也就是您在第一個程序中建立的資料來源。</span><span class="sxs-lookup"><span data-stu-id="2a245-240">On the **Choose a connection to a SQL Server spatial data source**, select DataSource1, the data source that you created in the first procedure.</span></span>  
  
6.  <span data-ttu-id="2a245-241">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="2a245-241">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="2a245-242">在 [**設計查詢**] 頁面上，按一下 [當做**文字編輯**]。</span><span class="sxs-lookup"><span data-stu-id="2a245-242">On the **Design a Query** page, click **Edit as Text**.</span></span> <span data-ttu-id="2a245-243">查詢設計工具會切換為以文字為基礎的模式。</span><span class="sxs-lookup"><span data-stu-id="2a245-243">The query designer switches to text-based mode.</span></span>  
  
8.  <span data-ttu-id="2a245-244">在 [查詢] 窗格中，貼上下列文字：</span><span class="sxs-lookup"><span data-stu-id="2a245-244">Paste the following text in the query pane:</span></span>  
  
    ```  
    SELECT N'Path' AS Name, CAST('LINESTRING(  
       -76.5001866085881 42.4310489934743,  
       -76.4602850815536 43.4353224527794,  
       -73.4728622833178 44.7028831413324)' AS geography) as Route  
    ```  
  
9. <span data-ttu-id="2a245-245">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="2a245-245">Click **Next**.</span></span>  
  
     <span data-ttu-id="2a245-246">路徑會出現在地圖上，並且連接三家商店。</span><span class="sxs-lookup"><span data-stu-id="2a245-246">A path appears on the map that connects three stores.</span></span>  
  
10. <span data-ttu-id="2a245-247">在 **[選擇空間資料及地圖檢視選項]** 頁面上，確認 **[空間欄位]** 為 **[路線]** ，而 **[圖層類型]** 為 **[線條]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-247">On the **Choose spatial data and map view options** page, verify that the **Spatial field** is **Route** and that the **Layer type** is **Line**.</span></span> <span data-ttu-id="2a245-248">接受其他預設值。</span><span class="sxs-lookup"><span data-stu-id="2a245-248">Accept the other defaults.</span></span>  
  
     <span data-ttu-id="2a245-249">地圖檢視會顯示從紐約州北部某家商店到紐約州南部某家商店的路徑。</span><span class="sxs-lookup"><span data-stu-id="2a245-249">The map view displays a path from a store in the northern part of New York state to a store in the southern part of New York state.</span></span>  
  
11. <span data-ttu-id="2a245-250">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="2a245-250">Click **Next**.</span></span>  
  
12. <span data-ttu-id="2a245-251">在 **[選擇地圖視覺效果]** 頁面上，按一下 **[基本線條地圖]**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-251">On the **Choose map visualization** page, click **Basic Line Map**, and then click **Next**.</span></span>  
  
13. <span data-ttu-id="2a245-252">在 **[選擇色彩主題和資料視覺效果]** 上，選取 **[單一色彩地圖]** 選項。</span><span class="sxs-lookup"><span data-stu-id="2a245-252">On the **Choose color theme and data visualization**, select the option **Single color map**.</span></span> <span data-ttu-id="2a245-253">路徑會根據所選主題的單一色彩顯示。</span><span class="sxs-lookup"><span data-stu-id="2a245-253">The path appears as a single color based on the selected theme.</span></span>  
  
14. <span data-ttu-id="2a245-254">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="2a245-254">Click **Finish**.</span></span>  
  
 <span data-ttu-id="2a245-255">地圖會顯示新的線條圖層，其空間資料來源類型為 **DataSet**。</span><span class="sxs-lookup"><span data-stu-id="2a245-255">The map displays a new line layer with spatial data source type **DataSet**.</span></span> <span data-ttu-id="2a245-256">在此範例中，空間資料來自資料集，但是分析資料與線條沒有產生關聯。</span><span class="sxs-lookup"><span data-stu-id="2a245-256">In this example, the spatial data comes from a dataset but no analytical data is associated with the line.</span></span>  
  
##  <a name="4-add-a-bing-maps-tile-background"></a><a name="TileLayer"></a><span data-ttu-id="2a245-257">4. 加入 Bing 地圖底圖背景</span><span class="sxs-lookup"><span data-stu-id="2a245-257">4. Add a Bing Maps Tile Background</span></span>  
 <span data-ttu-id="2a245-258">加入顯示 Bing Maps 圖格背景的地圖圖層。</span><span class="sxs-lookup"><span data-stu-id="2a245-258">Add a map layer that displays a Bing Maps tile background.</span></span>  
  
#### <a name="to-add-a-virtual-earth-tile-background"></a><span data-ttu-id="2a245-259">加入虛擬地球圖格背景</span><span class="sxs-lookup"><span data-stu-id="2a245-259">To add a Virtual Earth tile background</span></span>  
  
1.  <span data-ttu-id="2a245-260">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="2a245-260">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="2a245-261">按兩下地圖來顯示 **[地圖圖層]** 窗格。</span><span class="sxs-lookup"><span data-stu-id="2a245-261">Double-click the map to display the **Map Layer** pane.</span></span> <span data-ttu-id="2a245-262">在工具列上，按一下**新增圖層**![rs_IconMapAddLayer](../../2014/tutorials/media/rs-iconmapaddlayer.gif "rs_IconMapAddLayer")。</span><span class="sxs-lookup"><span data-stu-id="2a245-262">On the toolbar, click **Add Layer**![rs_IconMapAddLayer](../../2014/tutorials/media/rs-iconmapaddlayer.gif "rs_IconMapAddLayer").</span></span>  
  
3.  <span data-ttu-id="2a245-263">從下拉式清單中，按一下 **[圖格圖層]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-263">From the drop-down list, click **Tile Layer**.</span></span>  
  
     <span data-ttu-id="2a245-264">**[地圖圖層]** 窗格中的最後一個圖層是 TileLayer1。</span><span class="sxs-lookup"><span data-stu-id="2a245-264">The last layer in the **Map Layer** pane is TileLayer1.</span></span> <span data-ttu-id="2a245-265">根據預設，影像分割圖層會顯示路段圖樣式。</span><span class="sxs-lookup"><span data-stu-id="2a245-265">By default, the tile layer displays the road map style.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2a245-266">您也可以在精靈中的 **[選擇空間資料及地圖檢視選項]** 頁面上加入圖格圖層。</span><span class="sxs-lookup"><span data-stu-id="2a245-266">In the wizard, you can also add a tile layer on the **Choose spatial data and map view options** page.</span></span> <span data-ttu-id="2a245-267">若要執行這項操作，請選取 **[加入此地圖檢是的 Bing Maps 背景]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-267">To do this, select **Add a Bing Maps background for this map view**.</span></span> <span data-ttu-id="2a245-268">在呈現的報表中，圖格背景會顯示目前地圖檢視區置中與縮放層級的 Bing Maps 圖格。</span><span class="sxs-lookup"><span data-stu-id="2a245-268">In a rendered report, the tile background displays Bing Maps tiles for the current map viewport center and zoom level.</span></span>  
  
4.  <span data-ttu-id="2a245-269">按一下 TileLayer1 上的向下箭頭，然後按一下 **[影像分割屬性]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-269">Click the down arrow on TileLayer1, and then click **Tile Properties**.</span></span>  
  
5.  <span data-ttu-id="2a245-270">在 **[類型]** 中，選取 **[空照圖]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-270">In **Type**, select **Aerial**.</span></span> <span data-ttu-id="2a245-271">空照圖檢視不包含文字。</span><span class="sxs-lookup"><span data-stu-id="2a245-271">The aerial view does not contain text.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="5-make-a-layer-transparent"></a><a name="Transparent"></a><span data-ttu-id="2a245-272">5. 使圖層變透明</span><span class="sxs-lookup"><span data-stu-id="2a245-272">5. Make a Layer Transparent</span></span>  
 <span data-ttu-id="2a245-273">若要讓某一個圖層上的項目透過另一個圖層顯示，您可以調整圖層的順序以及各圖層的透明度，以獲得需要的效果。</span><span class="sxs-lookup"><span data-stu-id="2a245-273">To let the items on one layer show through another layer, you can adjust the order of layers and the transparency of each layer to get the effect that you want.</span></span>  
  
#### <a name="to-set-the-transparency-of-a-layer"></a><span data-ttu-id="2a245-274">設定圖層的透明度</span><span class="sxs-lookup"><span data-stu-id="2a245-274">To set the transparency of a layer</span></span>  
  
1.  <span data-ttu-id="2a245-275">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="2a245-275">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="2a245-276">按兩下地圖來顯示 **[地圖圖層]** 窗格。</span><span class="sxs-lookup"><span data-stu-id="2a245-276">Double-click the map to display the **Map Layer** pane.</span></span>  
  
3.  <span data-ttu-id="2a245-277">按一下 PolygonLayer1 上的向下箭頭，然後按一下 **[圖層資料]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-277">Click the down arrow on PolygonLayer1, and then click **Layer Data**.</span></span> <span data-ttu-id="2a245-278">**[地圖多邊形圖層屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="2a245-278">The **Map Polygon Layer Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="2a245-279">按一下 **[可見性]** 。</span><span class="sxs-lookup"><span data-stu-id="2a245-279">Click **Visibility**.</span></span>  
  
5.  <span data-ttu-id="2a245-280">在 **[透明度 (%)]** 中，輸入 **30**。</span><span class="sxs-lookup"><span data-stu-id="2a245-280">In **Transparency (%)**, type **30**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 <span data-ttu-id="2a245-281">設計介面會將郡顯示為半透明。</span><span class="sxs-lookup"><span data-stu-id="2a245-281">The design surface displays the counties as semi-transparent.</span></span>  
  
##  <a name="6-vary-county-color-based-on-sales"></a><a name="Vary"></a><span data-ttu-id="2a245-282">6. 根據銷售來改變縣市色彩</span><span class="sxs-lookup"><span data-stu-id="2a245-282">6. Vary County Color Based on Sales</span></span>  
 <span data-ttu-id="2a245-283">多邊形圖層上的每個郡都有不同的色彩，因為報表處理器會自動根據您在地圖精靈最後一頁上選擇的主題，指派色彩調色盤中的色彩值。</span><span class="sxs-lookup"><span data-stu-id="2a245-283">Each county on the polygon layer has a different color because the report processor automatically assigns a color value from the color palette based on the theme that you chose on the last page of the map wizard.</span></span>  
  
 <span data-ttu-id="2a245-284">在下列的步驟中，指定一個色彩規則，讓特定色彩與每個郡的商店銷售額範圍產生關聯。</span><span class="sxs-lookup"><span data-stu-id="2a245-284">In the following steps, specify a color rule to associate specific colors with a range of store sales for each county.</span></span> <span data-ttu-id="2a245-285">紅色、黃色、綠色分別表示相對的高、中、低銷售額。</span><span class="sxs-lookup"><span data-stu-id="2a245-285">The colors red-yellow-green indicate relative high-middle-low sales.</span></span> <span data-ttu-id="2a245-286">格式化色階來顯示貨幣。</span><span class="sxs-lookup"><span data-stu-id="2a245-286">Format the color scale to show currency.</span></span> <span data-ttu-id="2a245-287">在新的圖例中顯示年度銷售額範圍。</span><span class="sxs-lookup"><span data-stu-id="2a245-287">Display the annual sales ranges in a new legend.</span></span> <span data-ttu-id="2a245-288">對於未包含商店的郡，不使用色彩則表示沒有相關聯的資料。</span><span class="sxs-lookup"><span data-stu-id="2a245-288">For counties that do not contain stores, use no color to show that there is no associated data.</span></span>  
  
###  <a name="6a-build-a-relationship-between-spatial-and-analytical-data"></a><a name="Relationship"></a><span data-ttu-id="2a245-289">6a.</span><span class="sxs-lookup"><span data-stu-id="2a245-289">6a.</span></span> <span data-ttu-id="2a245-290">建立空間資料與分析資料之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="2a245-290">Build a Relationship between Spatial and Analytical Data</span></span>  
 <span data-ttu-id="2a245-291">若要根據分析資料的色彩變化郡的形狀，您必須先讓分析資料與空間資料產生關聯。</span><span class="sxs-lookup"><span data-stu-id="2a245-291">To vary the county shapes by color based on analytical data, you first must associate the analytical data with the spatial data.</span></span> <span data-ttu-id="2a245-292">在本教學課程中，您將使用郡名稱進行比對。</span><span class="sxs-lookup"><span data-stu-id="2a245-292">In this tutorial, you will use the county name to match on.</span></span>  
  
##### <a name="to-build-a-relationship-between-spatial-data-and-analytical-data"></a><span data-ttu-id="2a245-293">建立空間資料與分析資料間的關聯性</span><span class="sxs-lookup"><span data-stu-id="2a245-293">To build a relationship between spatial data and analytical data</span></span>  
  
1.  <span data-ttu-id="2a245-294">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="2a245-294">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="2a245-295">按兩下地圖來顯示 **[地圖圖層]** 窗格。</span><span class="sxs-lookup"><span data-stu-id="2a245-295">Double-click the map to display the **Map Layer** pane.</span></span>  
  
3.  <span data-ttu-id="2a245-296">按一下 PolygonLayer1 上的向下箭頭，然後按一下 **[圖層資料]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-296">Click the down arrow on PolygonLayer1, and then click **Layer Data**.</span></span> <span data-ttu-id="2a245-297">**[地圖多邊形圖層屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="2a245-297">The **Map Polygon Layer Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="2a245-298">按一下 **[分析資料]** 。</span><span class="sxs-lookup"><span data-stu-id="2a245-298">Click **Analytical data**.</span></span>  
  
5.  <span data-ttu-id="2a245-299">從下拉式清單中選取 DataSet1。</span><span class="sxs-lookup"><span data-stu-id="2a245-299">From the drop-down list, select DataSet1.</span></span> <span data-ttu-id="2a245-300">當您為各郡指定空間資料查詢時，精靈就會建立此資料集。</span><span class="sxs-lookup"><span data-stu-id="2a245-300">This dataset was created by the wizard when you specified the spatial data query for the counties.</span></span>  
  
6.  <span data-ttu-id="2a245-301">在 **[要比對的欄位]** 中，按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-301">In **Fields to match on**, click **Add**.</span></span> <span data-ttu-id="2a245-302">新的資料列隨即加入。</span><span class="sxs-lookup"><span data-stu-id="2a245-302">A new row is added.</span></span>  
  
7.  <span data-ttu-id="2a245-303">在 **[從空間資料集]** 的下拉式清單中，按一下 [COUNTYNAME]。</span><span class="sxs-lookup"><span data-stu-id="2a245-303">In **From spatial dataset**, from the drop-down list, click COUNTYNAME.</span></span>  
  
8.  <span data-ttu-id="2a245-304">在 **[從分析資料集]** 的下拉式清單中，按一下 [郡]。</span><span class="sxs-lookup"><span data-stu-id="2a245-304">In **From analytical dataset**, from the drop-down list, click [County].</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. <span data-ttu-id="2a245-305">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="2a245-305">Preview the report.</span></span>  
  
 <span data-ttu-id="2a245-306">透過指定空間資料來源和分析資料集中的比對欄位，就可以讓報表處理器根據地圖元素為分析資料分組。</span><span class="sxs-lookup"><span data-stu-id="2a245-306">By specifying a match field from the spatial data source and from the analytical dataset, you enable the report processor to group analytical data based on the map elements.</span></span> <span data-ttu-id="2a245-307">資料繫結的地圖元素擁有與您所指定值比對成功的項目。</span><span class="sxs-lookup"><span data-stu-id="2a245-307">A data-bound map element has a successful match for the values that you specified.</span></span>  
  
 <span data-ttu-id="2a245-308">每一個有商店的郡所使用的色彩，都是依據您在精靈中所選擇樣式的調色盤而定。</span><span class="sxs-lookup"><span data-stu-id="2a245-308">Each county that contains a store has a color that is based on the color palette for the style that you chose in the wizard.</span></span>  
  
###  <a name="6b-specify-color-rules-for-polygons"></a><a name="ColorRules"></a><span data-ttu-id="2a245-309">6b.</span><span class="sxs-lookup"><span data-stu-id="2a245-309">6b.</span></span> <span data-ttu-id="2a245-310">指定多邊形的色彩規則</span><span class="sxs-lookup"><span data-stu-id="2a245-310">Specify Color Rules for Polygons</span></span>  
 <span data-ttu-id="2a245-311">若要建立讓各郡的色彩隨商店銷售額變化的規則，您必須指定範圍值、該範圍中要顯示的區間數目，以及要使用的色彩。</span><span class="sxs-lookup"><span data-stu-id="2a245-311">To create a rule that varies the color of each county based store sales, you must specify the range values, the number of divisions within that range that you want to display, and the colors to use.</span></span>  
  
##### <a name="to-specify-color-rules-for-all-polygons-that-have-associated-data"></a><span data-ttu-id="2a245-312">為所有擁有相關資料的多邊形指定色彩規則</span><span class="sxs-lookup"><span data-stu-id="2a245-312">To specify color rules for all polygons that have associated data</span></span>  
  
1.  <span data-ttu-id="2a245-313">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="2a245-313">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="2a245-314">按一下 PolygonLayer1 上的向下箭頭，然後按一下 **[多邊形色彩規則]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-314">Click the down arrow on PolygonLayer1, and then click **Polygon Color Rule**.</span></span> <span data-ttu-id="2a245-315">**[地圖色彩規則屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="2a245-315">The **Map Color Rules Properties** dialog box opens.</span></span> <span data-ttu-id="2a245-316">您會發現已選取 **[使用調色盤將資料視覺化]** 色彩規則選項。</span><span class="sxs-lookup"><span data-stu-id="2a245-316">Notice that the color rule option **Visualize data by using color palette** is selected.</span></span> <span data-ttu-id="2a245-317">此選項是由精靈設定。</span><span class="sxs-lookup"><span data-stu-id="2a245-317">This option was set by the wizard.</span></span>  
  
3.  <span data-ttu-id="2a245-318">選取 **[使用色彩範圍將資料視覺化]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-318">Select **Visualize data by using color ranges**.</span></span> <span data-ttu-id="2a245-319">開始色彩、中間色彩和結束色彩選項會取代調色盤選項。</span><span class="sxs-lookup"><span data-stu-id="2a245-319">The palette option is replaced by start color, middle color, and end color options.</span></span>  
  
4.  <span data-ttu-id="2a245-320">定義每個郡銷售額的範圍值。</span><span class="sxs-lookup"><span data-stu-id="2a245-320">Define range values for sales per county.</span></span> <span data-ttu-id="2a245-321">從 **[資料欄位]** 的下拉式清單中，選取 [ `[Sum(Sales)]`]。</span><span class="sxs-lookup"><span data-stu-id="2a245-321">In **Data field**, from the drop-down list, select `[Sum(Sales)]`.</span></span>  
  
5.  <span data-ttu-id="2a245-322">若要改變格式，以千為單位顯示貨幣，則將運算式變更如下： `=Sum(Fields!Sales.Value)/1000`</span><span class="sxs-lookup"><span data-stu-id="2a245-322">To change the format to display currency in thousands, change the expression to the following: `=Sum(Fields!Sales.Value)/1000`</span></span>  
  
6.  <span data-ttu-id="2a245-323">將 **[開始色彩]** 變更為 **[紅色]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-323">Change **Start color** to **Red**.</span></span>  
  
7.  <span data-ttu-id="2a245-324">將 **[結束色彩]** 變更為 **[綠色]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-324">Change **End color** to **Green**.</span></span>  
  
     <span data-ttu-id="2a245-325">**[紅色]** 表示低銷售值、 **[黃色]** 表示中銷售值，而 **[綠色]** 表示高銷售值。</span><span class="sxs-lookup"><span data-stu-id="2a245-325">**Red** represents low sales values, **Yellow** represents middle sales values, and **Green** represents high sales values.</span></span> <span data-ttu-id="2a245-326">報表處理器會根據這些值以及您在 **[分佈]** 頁面上選擇的選項，計算色彩範圍。</span><span class="sxs-lookup"><span data-stu-id="2a245-326">The report processor calculates a range of colors based on these values and the options that you choose on the **Distribution** page.</span></span>  
  
8.  <span data-ttu-id="2a245-327">按一下 **[分佈]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-327">Click **Distribution**.</span></span>  
  
9. <span data-ttu-id="2a245-328">請確認分佈類型為 **[最佳]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-328">Verify that the distribution type is **Optimal**.</span></span> <span data-ttu-id="2a245-329">針對步驟 5 中的運算式，最佳分佈會將值分割成子範圍，這些子範圍會讓每個範圍中的項目數目和每個範圍的涵蓋範圍。</span><span class="sxs-lookup"><span data-stu-id="2a245-329">For the expression from step 5, optimal distribution divides the values into subranges that balance the number of items in each range and the span for each range.</span></span>  
  
10. <span data-ttu-id="2a245-330">接受此頁面上其他選項的預設值。</span><span class="sxs-lookup"><span data-stu-id="2a245-330">Accept the default values for other options on this page.</span></span> <span data-ttu-id="2a245-331">如果您選取最佳分佈類型，則報表執行時，會計算子範圍的數目。</span><span class="sxs-lookup"><span data-stu-id="2a245-331">When you select the optimal distribution type, the number of subranges are calculated when the report runs.</span></span>  
  
11. <span data-ttu-id="2a245-332">按一下 **[圖例]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-332">Click **Legend**.</span></span>  
  
12. <span data-ttu-id="2a245-333">在 **[色階選項]** 中，確認已選取 **[在色階中顯示]** 。</span><span class="sxs-lookup"><span data-stu-id="2a245-333">In **Color scale options**, verify that **Show in color scale** is selected.</span></span>  
  
13. <span data-ttu-id="2a245-334">在 **[在此圖例中顯示]** 的下拉式清單中，選取空行。</span><span class="sxs-lookup"><span data-stu-id="2a245-334">In **Show in this legend**, from the drop-down list, select the blank line.</span></span> <span data-ttu-id="2a245-335">現在您只能以色階顯示色彩範圍。</span><span class="sxs-lookup"><span data-stu-id="2a245-335">For now, you will show the color ranges only in the color scale.</span></span>  
  
14. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 <span data-ttu-id="2a245-336">色階會顯示五種色彩：紅色、橙色、黃色、黃綠色與綠色。</span><span class="sxs-lookup"><span data-stu-id="2a245-336">The color scale displays five colors: red, orange, yellow, yellow green, and green.</span></span> <span data-ttu-id="2a245-337">每一種色彩都代表一個銷售額範圍，該範圍是根據各郡的銷售額自動計算。</span><span class="sxs-lookup"><span data-stu-id="2a245-337">Each color represents a sales range that is automatically calculated based on the sales by county.</span></span>  
  
###  <a name="6c-format-the-data-in-the-color-scale-as-currency"></a><a name="ColorScale"></a><span data-ttu-id="2a245-338">6c.</span><span class="sxs-lookup"><span data-stu-id="2a245-338">6c.</span></span> <span data-ttu-id="2a245-339">依據貨幣格式化色階中的資料</span><span class="sxs-lookup"><span data-stu-id="2a245-339">Format the Data in the Color Scale as Currency</span></span>  
 <span data-ttu-id="2a245-340">根據預設，資料會使用一般格式。</span><span class="sxs-lookup"><span data-stu-id="2a245-340">By default, data has a general format.</span></span> <span data-ttu-id="2a245-341">您可以套用自訂格式。</span><span class="sxs-lookup"><span data-stu-id="2a245-341">You can apply custom formats.</span></span>  
  
##### <a name="to-set-the-format-for-the-color-scale"></a><span data-ttu-id="2a245-342">設定色階的格式</span><span class="sxs-lookup"><span data-stu-id="2a245-342">To set the format for the color scale</span></span>  
  
1.  <span data-ttu-id="2a245-343">以滑鼠右鍵按一下色階，然後按一下 **[色階屬性]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-343">Right-click the color scale, and then click **Color Scale Properties**.</span></span>  
  
2.  <span data-ttu-id="2a245-344">按一下 **[數值]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-344">Click **Number**.</span></span>  
  
3.  <span data-ttu-id="2a245-345">在 **[類別目錄]** 中，按一下 **[貨幣]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-345">In **Category**, click **Currency**.</span></span>  
  
4.  <span data-ttu-id="2a245-346">在 **[小數位數]** 中，輸入 **0**。</span><span class="sxs-lookup"><span data-stu-id="2a245-346">In **Decimal places**, type **0**.</span></span> <span data-ttu-id="2a245-347">此格式會指定貨幣不要有小數位數。</span><span class="sxs-lookup"><span data-stu-id="2a245-347">This format specifies no decimal places for currency.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="2a245-348">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="2a245-348">Preview the report.</span></span>  
  
 <span data-ttu-id="2a245-349">色階會以每個範圍的貨幣格式顯示年度銷售額。</span><span class="sxs-lookup"><span data-stu-id="2a245-349">The color scale displays annual sales in currency format for each range.</span></span>  
  
###  <a name="6d-create-a-new-legend"></a><a name="NewLegend"></a><span data-ttu-id="2a245-350">6d.</span><span class="sxs-lookup"><span data-stu-id="2a245-350">6d.</span></span> <span data-ttu-id="2a245-351">建立新的圖例</span><span class="sxs-lookup"><span data-stu-id="2a245-351">Create a New Legend</span></span>  
 <span data-ttu-id="2a245-352">根據預設，所有規則都會在第一個圖例中顯示。</span><span class="sxs-lookup"><span data-stu-id="2a245-352">By default, all rules display in the first legend.</span></span> <span data-ttu-id="2a245-353">若要改善地圖的顯示效果，可以加入圖例。</span><span class="sxs-lookup"><span data-stu-id="2a245-353">To improve the display for a map, you can add legends.</span></span>  
  
 <span data-ttu-id="2a245-354">若要改變預設顯示，可以執行兩個步驟：建立新的圖例，然後將地圖圖層的規則結果與新圖例產生關聯。</span><span class="sxs-lookup"><span data-stu-id="2a245-354">To change the default display, there are two steps: create a new legend and then associate the rule results for a map layer with the new legend.</span></span>  
  
##### <a name="to-create-a-new-legend"></a><span data-ttu-id="2a245-355">建立新的圖例</span><span class="sxs-lookup"><span data-stu-id="2a245-355">To create a new legend</span></span>  
  
1.  <span data-ttu-id="2a245-356">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="2a245-356">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="2a245-357">以滑鼠右鍵按一下檢視區外部的地圖，然後按一下 **[加入圖例]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-357">Right-click the map outside the viewport, and then click **Add Legend**.</span></span> <span data-ttu-id="2a245-358">新圖例會加入地圖的預設位置。</span><span class="sxs-lookup"><span data-stu-id="2a245-358">A new legend is added to the map at a default location.</span></span>  
  
3.  <span data-ttu-id="2a245-359">以滑鼠右鍵按一下圖例，然後按一下 **[圖例屬性]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-359">Right-click the legend, and then click **Legend Properties**.</span></span>  
  
4.  <span data-ttu-id="2a245-360">在 **[位置選項]** 中，按一下指定您要讓圖例顯示在檢視區的相對位置。</span><span class="sxs-lookup"><span data-stu-id="2a245-360">In **Position options**, click the location that specifies where you want the legend to appear relative to the viewport.</span></span> <span data-ttu-id="2a245-361">設計介面上的地圖會變更，以顯示您選項的效果。</span><span class="sxs-lookup"><span data-stu-id="2a245-361">The map on the design surface changes to show the effect of your selections.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="2a245-362">按一下圖例上的 **[影像分割]** 來選取圖例標題。</span><span class="sxs-lookup"><span data-stu-id="2a245-362">Click **Title** on the legend to select the legend title.</span></span>  
  
7.  <span data-ttu-id="2a245-363">再按一下 **[影像分割]** 以進入文字的插入模式。</span><span class="sxs-lookup"><span data-stu-id="2a245-363">Click **Title** again to enter insert mode for the text.</span></span> <span data-ttu-id="2a245-364">將 **[標題]** 取代成 **[銷售額 (千)]**，然後按一下文字外部。</span><span class="sxs-lookup"><span data-stu-id="2a245-364">Replace **Title** by **Sales (Thousands)**, and then click outside the text.</span></span>  
  
 <span data-ttu-id="2a245-365">圖例會展開以顯示標題。</span><span class="sxs-lookup"><span data-stu-id="2a245-365">The legend expands to display the title.</span></span>  
  
###  <a name="6e-associate-legend-and-color-rules"></a><a name="Associate"></a><span data-ttu-id="2a245-366">6e.</span><span class="sxs-lookup"><span data-stu-id="2a245-366">6e.</span></span> <span data-ttu-id="2a245-367">讓圖例與色彩規則產生關聯</span><span class="sxs-lookup"><span data-stu-id="2a245-367">Associate Legend and Color Rules</span></span>  
 <span data-ttu-id="2a245-368">每個圖例都可以顯示一或多組規則結果。</span><span class="sxs-lookup"><span data-stu-id="2a245-368">Each legend can display one or more sets of rule results.</span></span>  
  
##### <a name="to-associate-a-legend-with-color-rules"></a><span data-ttu-id="2a245-369">讓圖例與色彩規則產生關聯</span><span class="sxs-lookup"><span data-stu-id="2a245-369">To associate a legend with color rules</span></span>  
  
1.  <span data-ttu-id="2a245-370">按兩下地圖來顯示 **[地圖圖層]** 窗格。</span><span class="sxs-lookup"><span data-stu-id="2a245-370">Double-click the map to display the **Map Layer** pane.</span></span>  
  
2.  <span data-ttu-id="2a245-371">按一下 PolygonLayer1 上的向下箭頭，然後按一下 **[多邊形色彩規則]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-371">Click the down arrow on PolygonLayer1, and then click **Polygon Color Rule**.</span></span> <span data-ttu-id="2a245-372">**[地圖色彩規則屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="2a245-372">The **Map Color Rules Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="2a245-373">按一下 **[圖例]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-373">Click **Legend**.</span></span>  
  
4.  <span data-ttu-id="2a245-374">在 **[色階選項]** 中，清除 **[以色階顯示]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-374">In **Color scale options**, clear **Show in color scale**.</span></span>  
  
5.  <span data-ttu-id="2a245-375">在 **[圖例選項]** 的下拉式清單中，選取 [Legend2]。</span><span class="sxs-lookup"><span data-stu-id="2a245-375">In **Legend options**, from the drop-down list, select Legend2.</span></span> <span data-ttu-id="2a245-376">圖例文字選項隨即出現。</span><span class="sxs-lookup"><span data-stu-id="2a245-376">The legend text option appears.</span></span> <span data-ttu-id="2a245-377">根據預設，圖例文字是以一般 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 格式字串格式化。</span><span class="sxs-lookup"><span data-stu-id="2a245-377">By default, legend text is formatted with a general [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] format string.</span></span> <span data-ttu-id="2a245-378">N0 中的 0 會指定不使用小數位數。</span><span class="sxs-lookup"><span data-stu-id="2a245-378">The 0 in N0 specifies no decimal digits.</span></span>  
  
6.  <span data-ttu-id="2a245-379">在 [**圖例文字**] 中，使用下列格式來指定不含小數位數的貨幣：`#FROMVALUE {C0} - #TOVALUE {C0}`</span><span class="sxs-lookup"><span data-stu-id="2a245-379">In **Legend text**, use the following format to specify currency with no decimal digits: `#FROMVALUE {C0} - #TOVALUE {C0}`</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="2a245-380">在設計介面上，圖例會顯示色彩範圍，其中範例資料會格式化為貨幣。</span><span class="sxs-lookup"><span data-stu-id="2a245-380">On the design surface, the legend displays the color ranges with sample data formatted as currency.</span></span>  
  
8.  <span data-ttu-id="2a245-381">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="2a245-381">Preview the report.</span></span>  
  
 <span data-ttu-id="2a245-382">與商店和銷售額相關聯的郡會依據色彩規則顯示。</span><span class="sxs-lookup"><span data-stu-id="2a245-382">The counties that have associated stores and sales display according to the color rules.</span></span> <span data-ttu-id="2a245-383">沒有銷售額的郡則不會顯示任何色彩。</span><span class="sxs-lookup"><span data-stu-id="2a245-383">Counties that have no sales have no color.</span></span>  
  
###  <a name="6f-change-color-for-counties-with-no-data"></a><a name="NoData"></a><span data-ttu-id="2a245-384">6f.</span><span class="sxs-lookup"><span data-stu-id="2a245-384">6f.</span></span> <span data-ttu-id="2a245-385">變更未包含資料之郡的色彩</span><span class="sxs-lookup"><span data-stu-id="2a245-385">Change Color for Counties with No Data</span></span>  
 <span data-ttu-id="2a245-386">您可以針對圖層上的所有地圖元素設定預設顯示選項。</span><span class="sxs-lookup"><span data-stu-id="2a245-386">You can set the default display options for all map elements on a layer.</span></span> <span data-ttu-id="2a245-387">色彩規則的優先順序高於這些顯示選項。</span><span class="sxs-lookup"><span data-stu-id="2a245-387">Color rules take precedence over these display options.</span></span>  
  
##### <a name="to-set-the-display-properties-for-all-elements-on-a-layer"></a><span data-ttu-id="2a245-388">設定圖層上所有元素的顯示屬性</span><span class="sxs-lookup"><span data-stu-id="2a245-388">To set the display properties for all elements on a layer</span></span>  
  
1.  <span data-ttu-id="2a245-389">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="2a245-389">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="2a245-390">按兩下地圖來顯示 **[地圖圖層]** 窗格。</span><span class="sxs-lookup"><span data-stu-id="2a245-390">Double-click the map to display the **Map Layer** pane.</span></span>  
  
3.  <span data-ttu-id="2a245-391">按一下 PolygonLayer1 上的向下箭頭，然後按一下 **[多邊形屬性]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-391">Click the down arrow on PolygonLayer1, and then click **Polygon Properties**.</span></span> <span data-ttu-id="2a245-392">**[地圖多邊形屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="2a245-392">The **Map Polygon Properties** dialog box opens.</span></span> <span data-ttu-id="2a245-393">此對話方塊中設定的顯示選項會先套用至圖層上的所有多邊形，然後才會套用規則為主的顯示選項。</span><span class="sxs-lookup"><span data-stu-id="2a245-393">Display options set in this dialog box apply to all polygons on the layer before rule-based display options are applied.</span></span>  
  
4.  <span data-ttu-id="2a245-394">按一下 **[填滿]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-394">Click **Fill**.</span></span>  
  
5.  <span data-ttu-id="2a245-395">確認填滿樣式是 [**實心]。**</span><span class="sxs-lookup"><span data-stu-id="2a245-395">Verify that the fill style is **Solid.**</span></span> <span data-ttu-id="2a245-396">漸層和模式會套用至所有色彩。</span><span class="sxs-lookup"><span data-stu-id="2a245-396">Gradients and patterns apply to all colors.</span></span>  
  
6.  <span data-ttu-id="2a245-397">在 **[色彩]** 中，按一下向下箭頭，然後按一下 **[淺鋼青]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-397">In **Color**, click the down arrow, and then click **Light Steel Blue**.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="2a245-398">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="2a245-398">Preview the report.</span></span>  
  
 <span data-ttu-id="2a245-399">沒有相關資料的郡會顯示為藍色。</span><span class="sxs-lookup"><span data-stu-id="2a245-399">Counties that have no associated data display as blue.</span></span> <span data-ttu-id="2a245-400">只有包含相關分析資料的郡會以您所指定色彩規則中的 **[紅色]** 到 **[綠色]** 色彩顯示。</span><span class="sxs-lookup"><span data-stu-id="2a245-400">Only counties that have associated analytical data appear in the **Red** through **Green** colors from the color rules that you specified.</span></span>  
  
##  <a name="7-add-a-custom-point"></a><a name="CustomPoint"></a><span data-ttu-id="2a245-401">7. 加入自訂點</span><span class="sxs-lookup"><span data-stu-id="2a245-401">7. Add a Custom Point</span></span>  
 <span data-ttu-id="2a245-402">若要表示尚未建立的新商店，請指定一個點並使用 **[圖釘]** 標記類型。</span><span class="sxs-lookup"><span data-stu-id="2a245-402">To represent a new store that has not yet been built, specify a point and use the **PushPin** marker type.</span></span>  
  
#### <a name="to-add-a-custom-point"></a><span data-ttu-id="2a245-403">加入自訂點</span><span class="sxs-lookup"><span data-stu-id="2a245-403">To add a custom point</span></span>  
  
1.  <span data-ttu-id="2a245-404">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="2a245-404">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="2a245-405">按兩下地圖來顯示 **[地圖圖層]** 窗格。</span><span class="sxs-lookup"><span data-stu-id="2a245-405">Double-click the map to display the **Map Layer** pane.</span></span> <span data-ttu-id="2a245-406">在工具列上，按一下 **[加入圖層]**，然後按一下 **[點圖層]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-406">On the toolbar, click **Add Layer**, and then click **Point Layer**.</span></span>  
  
     <span data-ttu-id="2a245-407">新的點圖層便會加入至地圖中。</span><span class="sxs-lookup"><span data-stu-id="2a245-407">A new point layer is added to the map.</span></span> <span data-ttu-id="2a245-408">根據預設，點圖層的空間資料類型為 **[內嵌]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-408">By default, the point layer has spatial data type **Embedded**.</span></span>  
  
3.  <span data-ttu-id="2a245-409">按一下 PointLayer2 上的向下箭頭，然後按一下 **[加入點]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-409">Click the down arrow on PointLayer2, and then click **Add Point**.</span></span>  
  
4.  <span data-ttu-id="2a245-410">將指標移到地圖檢視區上。</span><span class="sxs-lookup"><span data-stu-id="2a245-410">Move the pointer over the map viewport.</span></span> <span data-ttu-id="2a245-411">游標會變更為十字形狀。</span><span class="sxs-lookup"><span data-stu-id="2a245-411">The cursor changes to crosshairs.</span></span>  
  
5.  <span data-ttu-id="2a245-412">按一下地圖上您要加入點的位置。</span><span class="sxs-lookup"><span data-stu-id="2a245-412">Click the location on the map where you want to add a point.</span></span> <span data-ttu-id="2a245-413">在此教學課程中，按一下某一個郡中路線開始處旁邊的位置。</span><span class="sxs-lookup"><span data-stu-id="2a245-413">In this tutorial, click a location in a county next to the start of the route.</span></span> <span data-ttu-id="2a245-414">以圓形標示的點就會加入至圖層中您所按的位置。</span><span class="sxs-lookup"><span data-stu-id="2a245-414">A point marked by a circle is added to the layer at the location where you clicked.</span></span> <span data-ttu-id="2a245-415">根據預設，系統會選取點。</span><span class="sxs-lookup"><span data-stu-id="2a245-415">By default, the point is selected.</span></span>  
  
6.  <span data-ttu-id="2a245-416">以滑鼠右鍵按一下您加入的點，然後按一下 **[內嵌點屬性]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-416">Right-click the point you added, and then click **Embedded Point Properties**.</span></span>  
  
7.  <span data-ttu-id="2a245-417">選取 **[覆寫此圖層的點選項]** 選項。</span><span class="sxs-lookup"><span data-stu-id="2a245-417">Select the option **Override point options for this layer**.</span></span> <span data-ttu-id="2a245-418">對話方塊中會出現一個額外的頁面。</span><span class="sxs-lookup"><span data-stu-id="2a245-418">Additional pages appear in the dialog box.</span></span> <span data-ttu-id="2a245-419">您在此處設定的值，其優先順序高於圖層或色彩規則的顯示選項。</span><span class="sxs-lookup"><span data-stu-id="2a245-419">Values that you set here take precedence over display options for the layer or for color rules.</span></span>  
  
8.  <span data-ttu-id="2a245-420">按一下 **[標記]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-420">Click **Marker**.</span></span>  
  
9. <span data-ttu-id="2a245-421">選取 **[星形]** 做為 **[標記類型]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-421">For **Marker type**, select **Star**.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. <span data-ttu-id="2a245-422">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="2a245-422">Preview the report.</span></span>  
  
 <span data-ttu-id="2a245-423">您加入的新點會以 **[星形]** 顯示。</span><span class="sxs-lookup"><span data-stu-id="2a245-423">The new point you added appears as a **Star**.</span></span>  
  
#### <a name="to-add-a-label-for-the-custom-point"></a><span data-ttu-id="2a245-424">加入自訂點的標籤</span><span class="sxs-lookup"><span data-stu-id="2a245-424">To add a label for the custom point</span></span>  
  
1.  <span data-ttu-id="2a245-425">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="2a245-425">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="2a245-426">以滑鼠右鍵按一下您剛加入的點，然後按一下 **[內嵌點屬性]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-426">Right-click the point you just added, and then click **Embedded Point Properties**.</span></span>  
  
3.  <span data-ttu-id="2a245-427">按一下 **[標籤]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-427">Click **Labels**.</span></span>  
  
4.  <span data-ttu-id="2a245-428">在 **[標籤文字]** 中，輸入 **新商店**。</span><span class="sxs-lookup"><span data-stu-id="2a245-428">In **Label text**, type **New Store**.</span></span>  
  
5.  <span data-ttu-id="2a245-429">在 **[位置]** 中，按一下 **[上方]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-429">In **Placement**, click **Top**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="2a245-430">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="2a245-430">Preview the report.</span></span>  
  
 <span data-ttu-id="2a245-431">標籤會出現在商店位置上方。</span><span class="sxs-lookup"><span data-stu-id="2a245-431">The label appears above the store location.</span></span>  
  
##  <a name="center-the-map-view"></a><a name="CenterView"></a><span data-ttu-id="2a245-432">置中地圖視圖</span><span class="sxs-lookup"><span data-stu-id="2a245-432">Center the Map View</span></span>  
 <span data-ttu-id="2a245-433">變更地圖檢視區的置中與縮放層級。</span><span class="sxs-lookup"><span data-stu-id="2a245-433">Change the map viewport center and zoom level.</span></span>  
  
#### <a name="to-change-the-viewport"></a><span data-ttu-id="2a245-434">變更檢視區</span><span class="sxs-lookup"><span data-stu-id="2a245-434">To change the viewport</span></span>  
  
1.  <span data-ttu-id="2a245-435">以滑鼠右鍵按一下地圖檢視區，然後按一下 **[檢視區屬性]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-435">Right-click the map viewport, and then click **Viewport Properties**.</span></span>  
  
2.  <span data-ttu-id="2a245-436">按一下 **[置中與縮放]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-436">Click **Center and Zoom**.</span></span>  
  
3.  <span data-ttu-id="2a245-437">確認已選取 **[設定檢視置中與縮放層級]** 選項。</span><span class="sxs-lookup"><span data-stu-id="2a245-437">Verify that the option **Set a view center and zoom level** is selected.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="2a245-438">以滑鼠左鍵按一下地圖檢視區，然後將檢視區的中央拖曳至需要的位置。</span><span class="sxs-lookup"><span data-stu-id="2a245-438">Left-click the map viewport, and drag the center of the viewport to the location that you want.</span></span>  
  
6.  <span data-ttu-id="2a245-439">使用滑鼠滾輪變更檢視區的縮放層級。</span><span class="sxs-lookup"><span data-stu-id="2a245-439">Use the mouse wheel to change the zoom level of the viewport.</span></span>  
  
7.  <span data-ttu-id="2a245-440">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="2a245-440">Preview the report.</span></span>  
  
 <span data-ttu-id="2a245-441">在 [設計] 檢視中，顯示介面和檢視上的地圖是以範例資料為基礎。</span><span class="sxs-lookup"><span data-stu-id="2a245-441">In Design view, the map on the display surface and the view is based on sample data.</span></span> <span data-ttu-id="2a245-442">在呈現的報表中，地圖檢視會在您指定的檢視上置中。</span><span class="sxs-lookup"><span data-stu-id="2a245-442">In the rendered report, the map view is centered on the view that you specified.</span></span>  
  
##  <a name="add-a-report-title"></a><a name="Title"></a><span data-ttu-id="2a245-443">加入報表標題</span><span class="sxs-lookup"><span data-stu-id="2a245-443">Add a Report Title</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="2a245-444">若要加入報表標題</span><span class="sxs-lookup"><span data-stu-id="2a245-444">To add a report title</span></span>  
  
1.  <span data-ttu-id="2a245-445">在設計介面上，按一下 **[按一下以加入標題]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-445">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="2a245-446">輸入 **紐約商店的銷售額** ，然後按一下文字方塊外部。</span><span class="sxs-lookup"><span data-stu-id="2a245-446">Type **Sales in New York Stores** and then click outside the text box.</span></span>  
  
 <span data-ttu-id="2a245-447">這個標題就會顯示在報表的頂端。</span><span class="sxs-lookup"><span data-stu-id="2a245-447">This title will appear at the top of the report.</span></span> <span data-ttu-id="2a245-448">沒有定義任何頁首時，位於報表主體頂端的項目就相當於報表頁首。</span><span class="sxs-lookup"><span data-stu-id="2a245-448">Items at the top of the report body when there is no page header defined are the equivalent of a report header.</span></span>  
  
##  <a name="save-the-report"></a><a name="Save"></a><span data-ttu-id="2a245-449">儲存報表</span><span class="sxs-lookup"><span data-stu-id="2a245-449">Save the Report</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="2a245-450">若要儲存報表</span><span class="sxs-lookup"><span data-stu-id="2a245-450">To save the report</span></span>  
  
1.  <span data-ttu-id="2a245-451">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="2a245-451">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="2a245-452">在 [報表產生器] 按鈕中，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="2a245-452">From the Report Builder button, click **Save As**.</span></span>  
  
3.  <span data-ttu-id="2a245-453">在 **[名稱]** 中輸入 **紐約的商店銷售額**。</span><span class="sxs-lookup"><span data-stu-id="2a245-453">In **Name**, type **Store Sales in New York**.</span></span>  
  
 <span data-ttu-id="2a245-454">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="2a245-454">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2a245-455">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2a245-455">Next Steps</span></span>  
 <span data-ttu-id="2a245-456">以上總結如何將地圖加入至報表的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="2a245-456">This concludes the walkthrough for how to add a map to your report.</span></span>  
  
 <span data-ttu-id="2a245-457">如需詳細資訊，請參閱[Maps &#40;報表產生器和 SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) ，以及 blogs.msdn.com 上[SQL Server Reporting Services 的空間資料](https://go.microsoft.com/fwlink/?LinkId=152771)的 blog 專案製圖調整。</span><span class="sxs-lookup"><span data-stu-id="2a245-457">For more information, see [Maps &#40;Report Builder and SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) and the blog entry [Cartographic Adjustment of Spatial Data for SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=152771) on blogs.msdn.com.</span></span>  
  
 <span data-ttu-id="2a245-458">如需更多教學課程，請參閱[教學課程 &#40;報表產生器&#41;](report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="2a245-458">For more tutorials, see [Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a245-459">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a245-459">See Also</span></span>  
 <span data-ttu-id="2a245-460">[教學課程 &#40;報表產生器&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="2a245-460">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 <span data-ttu-id="2a245-461">[SQL Server 2014 中的報表產生器](report-builder/report-builder-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="2a245-461">[Report Builder in SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md) </span></span>  
 <span data-ttu-id="2a245-462">[Map Wizard 和地圖圖層 Wizard &#40;報表產生器和 SSRS&#41;](report-design/map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2a245-462">[Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;](report-design/map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2a245-463">使用規則與分析資料更改多邊形、線條與點顯示 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2a245-463">Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;</span></span>](report-design/vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)  
  
  
