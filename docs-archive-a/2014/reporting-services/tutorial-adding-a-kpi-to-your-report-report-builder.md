---
title: 教學課程：將 KPI 新增至報表 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1bf77859-0b33-4f40-abaf-ebeeb6ebb1f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 405978721068583597adf5c4257978a222121078
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704769"
---
# <a name="tutorial-adding-a-kpi-to-your-report-report-builder"></a><span data-ttu-id="7b908-102">教學課程：將 KPI 加入至報表 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="7b908-102">Tutorial: Adding a KPI to Your Report (Report Builder)</span></span>
  <span data-ttu-id="7b908-103">關鍵效能指標 (KPI) 是具有商務重要性的可測量值。</span><span class="sxs-lookup"><span data-stu-id="7b908-103">A key performance indicator (KPI) is a measurable value that has business significance.</span></span> <span data-ttu-id="7b908-104">本教學課程將說明如何將 KPI 加入至報表。</span><span class="sxs-lookup"><span data-stu-id="7b908-104">This tutorial teaches you how to include a (KPI) in a report.</span></span> <span data-ttu-id="7b908-105">在這個案例中，依產品子類別排列的銷售摘要便是 KPI。</span><span class="sxs-lookup"><span data-stu-id="7b908-105">In this scenario, the sales summary by product subcategories is the KPI.</span></span> <span data-ttu-id="7b908-106">KPI 的目前狀態會使用色彩、量測計和指標顯示。</span><span class="sxs-lookup"><span data-stu-id="7b908-106">The current state of the KPI is shown by using colors, gauges, and indicators.</span></span>  
  
 <span data-ttu-id="7b908-107">下圖顯示您將建立的報表。</span><span class="sxs-lookup"><span data-stu-id="7b908-107">The following illustration shows the report that you will create.</span></span>  
  
 <span data-ttu-id="7b908-108">![rs_AddKPITutorial](../../2014/tutorials/media/rs-addkpitutorial.gif "rs_AddKPITutorial")</span><span class="sxs-lookup"><span data-stu-id="7b908-108">![rs_AddKPITutorial](../../2014/tutorials/media/rs-addkpitutorial.gif "rs_AddKPITutorial")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="7b908-109">您將瞭解的內容</span><span class="sxs-lookup"><span data-stu-id="7b908-109">What You Will Learn</span></span>  
 <span data-ttu-id="7b908-110">在本教學課程中，您將學習如何根據資料格的值設定資料表資料格的背景色彩來加入 KPI，以及加入和設定量測計和指標。</span><span class="sxs-lookup"><span data-stu-id="7b908-110">In this tutorial, you will learn to add a KPI by setting the background color of table cells based on cell value and add and configure a gauge and an indicator.</span></span> <span data-ttu-id="7b908-111">您也將學習如何撰寫設定資料表資料格背景色彩的運算式。</span><span class="sxs-lookup"><span data-stu-id="7b908-111">You also learn to write the expression that sets the background color of the table cells.</span></span>  
  
 <span data-ttu-id="7b908-112">本教學課程包含下列程序：</span><span class="sxs-lookup"><span data-stu-id="7b908-112">This tutorial contains the following procedures:</span></span>  
  
1.  [<span data-ttu-id="7b908-113">從資料表或矩陣精靈建立資料表報表和資料集</span><span class="sxs-lookup"><span data-stu-id="7b908-113">Create a Table Report and Dataset from the Table or Matrix Wizard</span></span>](#Table)  
  
2.  [<span data-ttu-id="7b908-114">從資料表或矩陣精靈組織資料、選擇配置和樣式</span><span class="sxs-lookup"><span data-stu-id="7b908-114">Organize Data, Choose Layout, and Style from the Table or Matrix Wizard</span></span>](#CompleteWizard)  
  
3.  [<span data-ttu-id="7b908-115">使用背景色彩顯示 KPI</span><span class="sxs-lookup"><span data-stu-id="7b908-115">Use Background Colors to Display a KPI</span></span>](#BackgroundColors)  
  
4.  [<span data-ttu-id="7b908-116">使用量測計顯示 KPI</span><span class="sxs-lookup"><span data-stu-id="7b908-116">Display a KPI by Using a Gauge</span></span>](#Gauge)  
  
5.  [<span data-ttu-id="7b908-117">使用指標顯示 KPI</span><span class="sxs-lookup"><span data-stu-id="7b908-117">Display a KPI by Using an Indicator</span></span>](#Indicator)  
  
6.  [<span data-ttu-id="7b908-118">加入報表標題</span><span class="sxs-lookup"><span data-stu-id="7b908-118">Add a Report Title</span></span>](#Title)  
  
7.  [<span data-ttu-id="7b908-119">儲存報表</span><span class="sxs-lookup"><span data-stu-id="7b908-119">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="7b908-120">在本教學課程中，精靈的步驟會合併成兩個程序：一個程序用來建立資料集，另一個程序用來建立資料表。</span><span class="sxs-lookup"><span data-stu-id="7b908-120">In this tutorial, the steps for the wizard are consolidated into two procedures: one to create the dataset and one to create a table.</span></span> <span data-ttu-id="7b908-121">如需如何瀏覽至報表伺服器、選擇資料來源、建立資料集以及執行精靈的逐步指示，請參閱本系列的第一個教學課程：[教學課程：建立基本資料表報表 &#40;報表產生器&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="7b908-121">For step-by-step instructions about how to browse to a report server, choose a data source, create a dataset, and run the wizard, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="7b908-122">完成本教學課程的估計時間：15 分鐘。</span><span class="sxs-lookup"><span data-stu-id="7b908-122">Estimated time to complete this tutorial: 15 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b908-123">需求</span><span class="sxs-lookup"><span data-stu-id="7b908-123">Requirements</span></span>  
 <span data-ttu-id="7b908-124">如需需求的詳細資訊，請參閱[教學課程的必要條件 &#40;報表產生器&#41;](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="7b908-124">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-table-report-and-dataset-from-the-table-or-matrix-wizard"></a><a name="Table"></a><span data-ttu-id="7b908-125">1. 從資料表或矩陣 Wizard 建立資料表報表和資料集</span><span class="sxs-lookup"><span data-stu-id="7b908-125">1. Create a Table Report and Dataset from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="7b908-126">從 [**消費者入門**] 對話方塊中，選擇共用資料來源、建立內嵌的資料集，並將資料顯示在資料表中。</span><span class="sxs-lookup"><span data-stu-id="7b908-126">From the **Getting Started** dialog box, choose a shared data source, create an embedded dataset, and display the data in a table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b908-127">在本教學課程中，查詢會包含資料值，因此不需要外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="7b908-127">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="7b908-128">這樣會使查詢相當冗長。</span><span class="sxs-lookup"><span data-stu-id="7b908-128">This makes the query quite long.</span></span> <span data-ttu-id="7b908-129">在商業環境中，查詢不會包含資料。</span><span class="sxs-lookup"><span data-stu-id="7b908-129">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="7b908-130">這僅供教學之用。</span><span class="sxs-lookup"><span data-stu-id="7b908-130">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-table"></a><span data-ttu-id="7b908-131">若要建立新資料表</span><span class="sxs-lookup"><span data-stu-id="7b908-131">To create a new table</span></span>  
  
1.  <span data-ttu-id="7b908-132">按一下 **[開始]**、依序指向 **[程式集]** 和 **[Microsoft SQL Server 2012 報表產生器]**，然後按一下 **[報表產生器]**。</span><span class="sxs-lookup"><span data-stu-id="7b908-132">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="7b908-133">[**消費者入門**] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="7b908-133">The **Getting Started** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7b908-134"> 如果 **[使用者入門]** 對話方塊沒有出現，請在 [報表產生器] 按鈕中按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="7b908-134">If the **Getting Started** dialog box does not appear, from the Report Builder button, click **New**.</span></span>  
  
2.  <span data-ttu-id="7b908-135">在左窗格中，確認已選取 **[新增報表]** 。</span><span class="sxs-lookup"><span data-stu-id="7b908-135">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="7b908-136">在右窗格中，按一下 **[資料表或矩陣精靈]**。</span><span class="sxs-lookup"><span data-stu-id="7b908-136">In the right pane, click **Table or Matrix Wizard**.</span></span>  
  
4.  <span data-ttu-id="7b908-137">在 [選擇資料集] 頁面上，按一下 **[建立資料集]**。</span><span class="sxs-lookup"><span data-stu-id="7b908-137">On the Choose a dataset page, click **Create a dataset**.</span></span>  
  
5.  <span data-ttu-id="7b908-138">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="7b908-138">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="7b908-139">在 [**選擇與資料來源的連接**] 頁面上，選取現有的資料來源，或流覽至報表伺服器並選取資料來源。</span><span class="sxs-lookup"><span data-stu-id="7b908-139">On the **Choose a connection to a data source** page, select an existing data source or browse to the report server and select a data source.</span></span> <span data-ttu-id="7b908-140">如果沒有資料來源可用，或無法存取報表伺服器，您可以改用內嵌資料來源。</span><span class="sxs-lookup"><span data-stu-id="7b908-140">If there no data source is available or you do not have access to a report server, you can use an embedded data source instead.</span></span> <span data-ttu-id="7b908-141">如需詳細資訊，請參閱[教學課程：建立基本資料表報表 &#40;報表產生器&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="7b908-141">For more information, see [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
7.  <span data-ttu-id="7b908-142">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="7b908-142">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="7b908-143">在 **[設計查詢]** 頁面上，按一下 **[當成文字編輯]**。</span><span class="sxs-lookup"><span data-stu-id="7b908-143">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
9. <span data-ttu-id="7b908-144">複製下列查詢並貼入查詢窗格中：</span><span class="sxs-lookup"><span data-stu-id="7b908-144">Copy and paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-11' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Mini Battery Charger' as Product, CAST(1056.00 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Accessories' as Subcategory,  
       'Telephoto Conversion Lens' as Product, CAST(1380.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,'Accessories' as Subcategory,    
       'USB Cable' as Product, CAST(780.00 AS money) AS Sales, 26 as Quantity  
    UNION SELECT CAST('2009-01-08' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(3798.00 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2009-01-09' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Business Videographer' as Product, CAST(10400.00 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2009-01-10' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Social Videographer' as Product, CAST(3000.00 AS money) AS Sales, 60 as Quantity  
    UNION SELECT CAST('2009-01-11' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Advanced Digital' as Product, CAST(7234.50 AS money) AS Sales, 39 as Quantity  
    UNION SELECT CAST('2009-01-07' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Compact Digital' as Product, CAST(10836.00 AS money) AS Sales, 84 as Quantity  
    UNION SELECT CAST('2009-01-08' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Consumer Digital' as Product, CAST(2550.00 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Digital' as Subcategory,   
       'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-09' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'SLR Camera 35mm' as Product, CAST(18530.00 AS money) AS Sales, 34 as Quantity  
    UNION SELECT CAST('2009-01-07' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'SLR Camera' as Product, CAST(26576.00 AS money) AS Sales, 88 as Quantity  
    ```  
  
10. <span data-ttu-id="7b908-145">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="7b908-145">Click **Next**.</span></span>  
  
##  <a name="2-organize-data-choose-layout-and-style-from-the-table-or-matrix-wizard"></a><a name="CompleteWizard"></a><span data-ttu-id="7b908-146">2. 從資料表或矩陣 Wizard 組織資料、選擇配置和樣式</span><span class="sxs-lookup"><span data-stu-id="7b908-146">2. Organize Data, Choose Layout, and Style from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="7b908-147">使用精靈提供起始設計來顯示資料。</span><span class="sxs-lookup"><span data-stu-id="7b908-147">Use the wizard to provide a starting design on which to display data.</span></span> <span data-ttu-id="7b908-148">精靈中的預覽窗格可協助您在完成資料表或矩陣設計之前，先視覺化群組資料的結果。</span><span class="sxs-lookup"><span data-stu-id="7b908-148">The preview pane in the wizard helps you to visualize the result of grouping data before you complete the table or matrix design.</span></span>  
  
#### <a name="to-organize-data-into-groups-choose-a-layout-and-a-style"></a><span data-ttu-id="7b908-149">若要將資料組織成群組、選擇配置和樣式</span><span class="sxs-lookup"><span data-stu-id="7b908-149">To organize data into groups, choose a layout and a style</span></span>  
  
1.  <span data-ttu-id="7b908-150">在 [排列欄位] 頁面上，將 [Product] 拖曳至 [值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7b908-150">On the Arrange fields page, drag Product to **Values**.</span></span>  
  
2.  <span data-ttu-id="7b908-151">將 [Quantity] 拖曳至 [值]\*\*\*\* 並放置在 [Product] 之下。</span><span class="sxs-lookup"><span data-stu-id="7b908-151">Drag Quantity to **Values** and place below Product.</span></span>  
  
     <span data-ttu-id="7b908-152">[Quantity] 是使用 Sum 函數摘要的，這個函數是摘要數值欄位的預設函數。</span><span class="sxs-lookup"><span data-stu-id="7b908-152">Quantity is summarized with the Sum function, the default function to summarize numeric fields.</span></span>  
  
3.  <span data-ttu-id="7b908-153">將 [Sales] 拖曳至 [值]\*\*\*\* 並放置在 [Quantity] 之下。</span><span class="sxs-lookup"><span data-stu-id="7b908-153">Drag Sales to **Values** and place below Quantity.</span></span>  
  
     <span data-ttu-id="7b908-154">步驟 1、2 和 3 會指定要在資料表中顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="7b908-154">Steps 1, 2, and 3 specify the data to display in the table.</span></span>  
  
4.  <span data-ttu-id="7b908-155">將 [SalesDate] 拖曳至 [資料列群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7b908-155">Drag SalesDate to **Row groups**.</span></span>  
  
5.  <span data-ttu-id="7b908-156">將 [Subcategory] 拖曳至 [資料列群組]\*\*\*\* 並放置在 [SalesDate] 之下。</span><span class="sxs-lookup"><span data-stu-id="7b908-156">Drag Subcategory to **Row groups** and place below SalesDate.</span></span>  
  
     <span data-ttu-id="7b908-157">步驟 4 和 5 會依日期組織欄位的值，然後再依該日期的所有銷售進行組織。</span><span class="sxs-lookup"><span data-stu-id="7b908-157">Steps 4 and 5 organize the values for the fields first by date, and then by all sales for that date.</span></span>  
  
6.  <span data-ttu-id="7b908-158">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="7b908-158">Click **Next**.</span></span>  
  
     <span data-ttu-id="7b908-159">當您執行報表時，資料表會顯示每個日期、每個日期的所有訂單，以及每個訂單的所有產品、數量和銷售總額。</span><span class="sxs-lookup"><span data-stu-id="7b908-159">When you run the report, the table displays each date, all orders for each date, and all products, quantities, and sales totals for each order.</span></span>  
  
7.  <span data-ttu-id="7b908-160">在 [選擇配置] 頁面的 [選項]\*\*\*\* 下方，確定已選取 [顯示小計和總計]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7b908-160">On the Choose the Layout page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
8.  <span data-ttu-id="7b908-161">驗證已選取 [區塊式，小計位於下方]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7b908-161">Verify that **Blocked, subtotal below** is selected.</span></span>  
  
9. <span data-ttu-id="7b908-162">清除 [展開/摺疊群組]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="7b908-162">Clear the option **Expand/collapse groups**.</span></span>  
  
     <span data-ttu-id="7b908-163">在本教學課程中，您建立的報表不會使用向下鑽研功能，此功能可讓使用者展開父群組階層，以顯示子群組資料列和詳細資料列。</span><span class="sxs-lookup"><span data-stu-id="7b908-163">In this tutorial, the report you create does not use the drilldown feature that lets a user expand a parent group hierarchy to display child group rows and detail rows.</span></span>  
  
10. <span data-ttu-id="7b908-164">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="7b908-164">Click **Next**.</span></span>  
  
11. <span data-ttu-id="7b908-165">在 [選擇樣式] 頁面的 [樣式] 窗格中選取樣式。</span><span class="sxs-lookup"><span data-stu-id="7b908-165">On the Choose a Style page, in the Styles pane, select a style.</span></span>  
  
     <span data-ttu-id="7b908-166">完成的報表圖顯示報表使用 [海洋] 樣式。</span><span class="sxs-lookup"><span data-stu-id="7b908-166">The illustration of the completed report shows the report using the Ocean style.</span></span>  
  
12. <span data-ttu-id="7b908-167">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="7b908-167">Click **Finish**.</span></span>  
  
     <span data-ttu-id="7b908-168">資料表會加入至設計介面。</span><span class="sxs-lookup"><span data-stu-id="7b908-168">The table is added to the design surface.</span></span> <span data-ttu-id="7b908-169">這個資料表具有五個資料行和五個資料列。</span><span class="sxs-lookup"><span data-stu-id="7b908-169">The table has five columns and five rows.</span></span> <span data-ttu-id="7b908-170">[資料列群組] 窗格會顯示三個資料列群組：[SalesDate]、[Subcategory] 和 [Details]。</span><span class="sxs-lookup"><span data-stu-id="7b908-170">The Row Groups pane shows three row groups: SalesDate, Subcategory, and Details.</span></span> <span data-ttu-id="7b908-171">詳細資料是資料集查詢擷取的所有資料。</span><span class="sxs-lookup"><span data-stu-id="7b908-171">Detail data is all the data that is retrieved by the dataset query.</span></span>  
  
13. <span data-ttu-id="7b908-172">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="7b908-172">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="7b908-173">資料表會針對特定日期銷售的每個產品顯示產品名稱、銷售數量和銷售總額。</span><span class="sxs-lookup"><span data-stu-id="7b908-173">For each product that is sold on a specific date, the table displays the product name, the quantity sold, and the sales total.</span></span> <span data-ttu-id="7b908-174">資料會先依銷售日期排列，然後再依子類別排列。</span><span class="sxs-lookup"><span data-stu-id="7b908-174">The data is organized first by sales date and then by subcategory.</span></span>  
  
##  <a name="3-use-background-colors-to-display-a-kpi"></a><a name="BackgroundColors"></a><span data-ttu-id="7b908-175">3. 使用背景色彩顯示 KPI</span><span class="sxs-lookup"><span data-stu-id="7b908-175">3. Use Background Colors to Display a KPI</span></span>  
 <span data-ttu-id="7b908-176">您可以將背景色彩設定成執行報表時評估的運算式。</span><span class="sxs-lookup"><span data-stu-id="7b908-176">Background colors can be set to an expression that is evaluated when you run the report.</span></span>  
  
#### <a name="to-display-the-present-state-of-a-kpi-by-using-background-colors"></a><span data-ttu-id="7b908-177">若要使用背景色彩來顯示 KPI 的目前狀態</span><span class="sxs-lookup"><span data-stu-id="7b908-177">To display the present state of a KPI by using background colors</span></span>  
  
1.  <span data-ttu-id="7b908-178">在資料表中，以滑鼠右鍵按一下資料格下方的兩個數據格， `[Sum(Sales)]` (顯示子類別目錄之銷售額) 的小計資料列，然後按一下 [**文字方塊屬性**]。</span><span class="sxs-lookup"><span data-stu-id="7b908-178">In the table, right-click two cells down from the `[Sum(Sales)]` cell (the subtotal row that displays the sales for a subcategory), and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="7b908-179">在 [**填滿**] 中，按一下 [**填滿色彩**] 選項旁邊的**fx**按鈕，然後在 [**設定 expression for： BackgroundColor** ] 欄位中輸入下列運算式：</span><span class="sxs-lookup"><span data-stu-id="7b908-179">In **Fill**, click the **fx** button next to the **Fill color** option and enter the following expression in the **Set expression for: BackgroundColor** field:</span></span>  
  
 `=IIF(Sum(Fields!Sales.Value) >= 5000 ,"Lime", IIF(Sum(Fields!Sales.Value) < 2500, "Red","Yellow"))`  
  
 <span data-ttu-id="7b908-180">這樣就會針對含有大於或等於 5000 之 `[Sum(Sales)]` 彙總總和的每個資料格，使用名為「亮綠」的綠色陰影，將背景色彩變更為綠色。</span><span class="sxs-lookup"><span data-stu-id="7b908-180">This changes the background color to green, using the shade of green named "Lime", for each cell that contains an aggregated sum for `[Sum(Sales)]` that is greater than or equal to 5000.</span></span> <span data-ttu-id="7b908-181">介於 2500 與 5000 之間的 `[Sum(Sales)]` 值會以黃色著色。</span><span class="sxs-lookup"><span data-stu-id="7b908-181">Values of `[Sum(Sales)]` between 2500 and 5000 are colored yellow.</span></span> <span data-ttu-id="7b908-182">小於 2500 的值會以紅色著色。</span><span class="sxs-lookup"><span data-stu-id="7b908-182">Values less than 2500 are colored red.</span></span>  
  
1.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
2.  <span data-ttu-id="7b908-183">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="7b908-183">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="7b908-184">在顯示子類別銷售額的小計資料列中，資料格的背景色彩會根據銷售總和的值變成紅色、黃色或綠色。</span><span class="sxs-lookup"><span data-stu-id="7b908-184">In the subtotal row that displays the sales for a subcategory, the background color of the cell is red, yellow, or green depending on value of the sales sum.</span></span>  
  
##  <a name="4-display-a-kpi-by-using-a-gauge"></a><a name="Gauge"></a><span data-ttu-id="7b908-185">4. 使用量測計顯示 KPI</span><span class="sxs-lookup"><span data-stu-id="7b908-185">4. Display a KPI by Using a Gauge</span></span>  
 <span data-ttu-id="7b908-186">量測計可說明資料集中的單一值。</span><span class="sxs-lookup"><span data-stu-id="7b908-186">A gauge depicts a single value in a dataset.</span></span> <span data-ttu-id="7b908-187">這個教學課程使用水平的線性量測計，因為它的形狀和簡單性，即使很小並用於資料表資料格內，也很容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="7b908-187">This tutorial uses a horizontal linear gauge because its shape and simplicity makes it easy to read, even in when it is a small size and used within a table cell.</span></span> <span data-ttu-id="7b908-188">如需詳細資訊，請參閱 [量測計 &#40;報表產生器及 SSRS&#41;](report-design/gauges-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7b908-188">For more information, see [Gauges &#40;Report Builder and SSRS&#41;](report-design/gauges-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-display-the-present-state-of-a-kpi-using-a-gauge"></a><span data-ttu-id="7b908-189">若要使用量測計來顯示 KPI 的目前狀態</span><span class="sxs-lookup"><span data-stu-id="7b908-189">To display the present state of a KPI using a gauge</span></span>  
  
1.  <span data-ttu-id="7b908-190">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="7b908-190">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="7b908-191">在資料表中，以滑鼠右鍵按一下您在上一個程式中變更之資料格的資料行處理常式，指向 [**插入資料行**]，然後按一下 [**右**]。</span><span class="sxs-lookup"><span data-stu-id="7b908-191">In the table, right-click the column handler for the cell that you changed in the previous procedure, point to **Insert Column**, and then click **Right**.</span></span> <span data-ttu-id="7b908-192">新的資料行就會加入至此資料表。</span><span class="sxs-lookup"><span data-stu-id="7b908-192">A new column is added to the table.</span></span>  
  
3.  <span data-ttu-id="7b908-193">在資料行標題中輸入**KPI** 。</span><span class="sxs-lookup"><span data-stu-id="7b908-193">Type **KPI** in the column heading.</span></span>  
  
4.  <span data-ttu-id="7b908-194">在 [**插入**] 索引標籤的 [**資料區**] 群組中，按一下 [量測計]，**然後按一下資料表**外部的設計介面。</span><span class="sxs-lookup"><span data-stu-id="7b908-194">On the **Insert** tab, in the **Data Regions** group, click **Gauge**, and then click the design surface outside the table.</span></span> <span data-ttu-id="7b908-195">**[選取量測計類型]** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="7b908-195">The **Select Gauge Type** dialog box appears.</span></span>  
  
5.  <span data-ttu-id="7b908-196">按一下 [**線性**]。</span><span class="sxs-lookup"><span data-stu-id="7b908-196">Click **Linear**.</span></span> <span data-ttu-id="7b908-197">會選取第一個線性量測計類型 [**水準**]。</span><span class="sxs-lookup"><span data-stu-id="7b908-197">The first linear gauge type, **Horizontal**, is selected.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="7b908-198">量測計就會加入至設計介面。</span><span class="sxs-lookup"><span data-stu-id="7b908-198">A gauge is added to the design surface.</span></span>  
  
7.  <span data-ttu-id="7b908-199">將 [Sales] 從 [報表資料] 窗格拖曳至量測計。</span><span class="sxs-lookup"><span data-stu-id="7b908-199">From the Report Data pane, drag Sales to the gauge.</span></span> <span data-ttu-id="7b908-200">當您將 [Sales] 拖曳到量測計上時，[量測計資料] 窗格隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="7b908-200">When you drag Sales across the gauge, the Gauge Data pane opens.</span></span>  
  
8.  <span data-ttu-id="7b908-201">將 Sales 放在 [**值**] 清單中。</span><span class="sxs-lookup"><span data-stu-id="7b908-201">Drop Sales in the **Values** list.</span></span>  
  
     <span data-ttu-id="7b908-202">當您將欄位放置到量測計上時，欄位會使用內建的 Sum 函數進行彙總。</span><span class="sxs-lookup"><span data-stu-id="7b908-202">When you drop the field onto the gauge, the field is aggregated by using the built-in Sum function.</span></span>  
  
9. <span data-ttu-id="7b908-203">以滑鼠右鍵按一下量測計中的指標，然後按一下 [**指標屬性**]。</span><span class="sxs-lookup"><span data-stu-id="7b908-203">Right-click the pointer in the gauge and click **Pointer Properties**.</span></span>  
  
10. <span data-ttu-id="7b908-204">在 [**指標類型**] 中，選取 [**橫條**]。</span><span class="sxs-lookup"><span data-stu-id="7b908-204">In **Pointer Type**, select **Bar**.</span></span> <span data-ttu-id="7b908-205">這樣就會將指標從標記變更為橫條，以便在量測計加入至資料表時更明顯。</span><span class="sxs-lookup"><span data-stu-id="7b908-205">This changes the pointer from a marker to a bar that will be more visible when the gauge is added to the table.</span></span>  
  
11. <span data-ttu-id="7b908-206">按一下 [**指標填滿**]。</span><span class="sxs-lookup"><span data-stu-id="7b908-206">Click **Pointer Fill**.</span></span> <span data-ttu-id="7b908-207">在 [**次要色彩**] 中，選擇 [**黃色**]。</span><span class="sxs-lookup"><span data-stu-id="7b908-207">In **Secondary Color,** pick **Yellow**.</span></span> <span data-ttu-id="7b908-208">漸層填滿模式將從白色變更為黃色。</span><span class="sxs-lookup"><span data-stu-id="7b908-208">The gradient fill pattern will change from white to yellow.</span></span>  
  
12. <span data-ttu-id="7b908-209">以滑鼠右鍵按一下量測計中的標尺，然後按一下 [標尺屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7b908-209">Right-click the scale in the gauge and click **Scale Properties**.</span></span>  
  
13. <span data-ttu-id="7b908-210">將 [**最大值**] 選項設為25000。</span><span class="sxs-lookup"><span data-stu-id="7b908-210">Set the **Maximum** option to 25000.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7b908-211">除了 25000 這類常數，您也可以使用運算式動態計算 [最大值]\*\*\*\* 選項的值。</span><span class="sxs-lookup"><span data-stu-id="7b908-211">Instead of a constant such as 25000, you can use an expression to dynamically calculate the value of the **Maximum** option.</span></span> <span data-ttu-id="7b908-212">運算式會使用彙總功能進行彙總，看起來就類似於運算式 `=Max(Sum(Fields!Sales.value), "Tablix1")`。</span><span class="sxs-lookup"><span data-stu-id="7b908-212">The expression would use the aggregate of aggregate feature and look similar to the expression `=Max(Sum(Fields!Sales.value), "Tablix1")`.</span></span>  
  
14. <span data-ttu-id="7b908-213">將資料表內部的量測計拖曳至小計資料列的第三個資料格，此小計資料列顯示您插入之資料行的子類別銷售額。</span><span class="sxs-lookup"><span data-stu-id="7b908-213">Drag the gauge inside the table into the third cell in the subtotal row that displays the sales for a subcategory of the column that you inserted.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7b908-214">您可能必須重新調整資料行，使水平的線性量測計能夠納入資料格中。</span><span class="sxs-lookup"><span data-stu-id="7b908-214">You might have to resize the column so that the horizontal linear gauge fits into the cell.</span></span> <span data-ttu-id="7b908-215">若要調整資料行的大小，請按一下資料行標頭，並使用控點來水平及垂直地調整資料格的大小。</span><span class="sxs-lookup"><span data-stu-id="7b908-215">To resize the column, click a column header and use the handles to resize the cells horizontally and vertically.</span></span>  
  
15. <span data-ttu-id="7b908-216">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="7b908-216">Click **Run** to preview the report.</span></span>  
  
     <span data-ttu-id="7b908-217">量測計中橫條的水平長度會根據 KPI 的值而變更。</span><span class="sxs-lookup"><span data-stu-id="7b908-217">The horizontal length of the bar in the gauge changes depending on the value of the KPI.</span></span>  
  
16. <span data-ttu-id="7b908-218">(選擇性) 加入最大指針來處理溢位，使任何超過刻度最大值的值都永遠會指向最大指針：</span><span class="sxs-lookup"><span data-stu-id="7b908-218">(Optional) Add a maximum pin to handle overflow so that any value over the scale maximum always points to the maximum pin:</span></span>  
  
    1.  <span data-ttu-id="7b908-219">開啟 [屬性] 窗格。</span><span class="sxs-lookup"><span data-stu-id="7b908-219">Open the Properties pane.</span></span>  
  
    2.  <span data-ttu-id="7b908-220">按一下標尺。</span><span class="sxs-lookup"><span data-stu-id="7b908-220">Click the scale.</span></span> <span data-ttu-id="7b908-221">線性標尺的屬性會顯示在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="7b908-221">The properties for the linear scale are displayed in the Properties pane.</span></span>  
  
    3.  <span data-ttu-id="7b908-222">在 [**縮放 pin** ] 分類中，展開 [ **MaximumPin** ] 節點。</span><span class="sxs-lookup"><span data-stu-id="7b908-222">In the **Scale Pins** category, expand the **MaximumPin** node.</span></span>  
  
    4.  <span data-ttu-id="7b908-223">將**Enable**屬性設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="7b908-223">Set the **Enable** property to `True`.</span></span> <span data-ttu-id="7b908-224">指針會顯示在標尺的最大值之後。</span><span class="sxs-lookup"><span data-stu-id="7b908-224">A pin appears after the maximum value on the scale.</span></span>  
  
    5.  <span data-ttu-id="7b908-225">將 [**顏色邊框**] 設定為 `Lime` 。</span><span class="sxs-lookup"><span data-stu-id="7b908-225">Set **BorderColor** to `Lime`.</span></span>  
  
17. <span data-ttu-id="7b908-226">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="7b908-226">Click **Run** to preview the report.</span></span>  
  
##  <a name="5-display-a-kpi-by-using-an-indicator"></a><a name="Indicator"></a><span data-ttu-id="7b908-227">5. 使用指標顯示 KPI</span><span class="sxs-lookup"><span data-stu-id="7b908-227">5. Display a KPI by Using an Indicator</span></span>  
 <span data-ttu-id="7b908-228">指標是小型的簡單量測計，可一目了然資料值。</span><span class="sxs-lookup"><span data-stu-id="7b908-228">Indicators are small simple gauges that communicate data values at a glance.</span></span> <span data-ttu-id="7b908-229">由於指標的尺寸小加上簡單明瞭，因此常用於資料表和矩陣。</span><span class="sxs-lookup"><span data-stu-id="7b908-229">Because of their size and simplicity, indicators are often used in tables and matrices.</span></span> <span data-ttu-id="7b908-230">如需詳細資訊，請參閱[指標 &#40;報表產生器及 SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7b908-230">For more information, see [Indicators &#40;Report Builder and SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-display-the-present-state-of-a-kpi-using-an-indicator"></a><span data-ttu-id="7b908-231">若要使用指標來顯示 KPI 的目前狀態</span><span class="sxs-lookup"><span data-stu-id="7b908-231">To display the present state of a KPI using an indicator</span></span>  
  
1.  <span data-ttu-id="7b908-232">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="7b908-232">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="7b908-233">在資料表中，以滑鼠右鍵按一下您在上一個程式中變更之資料格的資料行處理常式，指向 [**插入資料行**]，然後按一下 [**右**]。</span><span class="sxs-lookup"><span data-stu-id="7b908-233">In the table, right-click the column handler for the cell that you changed in the previous procedure, point to **Insert Column**, and then click **Right**.</span></span> <span data-ttu-id="7b908-234">新的資料行就會加入至此資料表。</span><span class="sxs-lookup"><span data-stu-id="7b908-234">A new column is added to the table.</span></span>  
  
3.  <span data-ttu-id="7b908-235">在資料行標題中輸入**KPI** 。</span><span class="sxs-lookup"><span data-stu-id="7b908-235">Type **KPI** in the column heading.</span></span>  
  
4.  <span data-ttu-id="7b908-236">按一下子類別小計的資料格。</span><span class="sxs-lookup"><span data-stu-id="7b908-236">Click the cell for the subcategory subtotal.</span></span>  
  
5.  <span data-ttu-id="7b908-237">在 [**插入**] 索引標籤的 [**資料區**] 群組中，按兩下 [**指標]。**</span><span class="sxs-lookup"><span data-stu-id="7b908-237">On the **Insert** tab, in the **Data Regions** group, double-click **Indicator.**</span></span>  
  
     <span data-ttu-id="7b908-238">[選取指標類型]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="7b908-238">The **Select Indicator Type** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="7b908-239">按一下 [**圖形**]。</span><span class="sxs-lookup"><span data-stu-id="7b908-239">Click **Shapes**.</span></span> <span data-ttu-id="7b908-240">選取第一個圖形類型 [ \*\*3 個流量燈] (無框) \*\* ]。</span><span class="sxs-lookup"><span data-stu-id="7b908-240">The first shape type, **3 Traffic Lights (Unrimmed),** is selected.</span></span>  
  
     <span data-ttu-id="7b908-241">您將在教學課程中使用這個指標。</span><span class="sxs-lookup"><span data-stu-id="7b908-241">You will use this indicator in the tutorial.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="7b908-242">指標會加入至設計介面。</span><span class="sxs-lookup"><span data-stu-id="7b908-242">The indicator is added to the design surface.</span></span>  
  
8.  <span data-ttu-id="7b908-243">以滑鼠右鍵按一下指標，然後按一下 [指標屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7b908-243">Right-click the indicator and click **Indicator Properties**.</span></span>  
  
9. <span data-ttu-id="7b908-244">按一下 [**值和狀態**]。</span><span class="sxs-lookup"><span data-stu-id="7b908-244">Click **Values and States**.</span></span>  
  
10. <span data-ttu-id="7b908-245">在 [值] 下拉式清單中，選取 **[Sum (Sales) ]**，但不要變更任何其他選項。</span><span class="sxs-lookup"><span data-stu-id="7b908-245">In the Value drop-down list, select **[Sum(Sales)]**, but do not change any other options.</span></span>  
  
     <span data-ttu-id="7b908-246">根據預設，整個資料區域會進行資料同步處理，而您會在 [同步處理範圍]\*\*\*\* 方塊中看到值 **Tablix1**，這是報表中的資料表資料區域的名稱。</span><span class="sxs-lookup"><span data-stu-id="7b908-246">By default, data synchronization occurs across the data region and you see the value **Tablix1**, the name of the table data region in the report, in the **Synchronization scope** box.</span></span>  
  
     <span data-ttu-id="7b908-247">在此報表中，您也可以變更子類別小計資料格中放置之指標的範圍，以同步處理 [SalesDate] 欄位。</span><span class="sxs-lookup"><span data-stu-id="7b908-247">In this report, you can also change the scope of an indicator placed in the cell of the subcategory subtotal to synchronize across the SalesDate field.</span></span>  
  
11. <span data-ttu-id="7b908-248">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="7b908-248">Click **Run** to preview the report.</span></span>  
  
##  <a name="6-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="7b908-249">6. 加入報表標題</span><span class="sxs-lookup"><span data-stu-id="7b908-249">6. Add a Report Title</span></span>  
 <span data-ttu-id="7b908-250">報表標題會出現在報表的頂端。</span><span class="sxs-lookup"><span data-stu-id="7b908-250">A report title appears at the top of the report.</span></span> <span data-ttu-id="7b908-251">您可以將報表標題放置在報表頁首，如果報表不使用報表頁首，則可以放置在報表主體頂端的文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="7b908-251">You can place the report title in a report header or if the report does not use one, in a text box at the top of the report body.</span></span> <span data-ttu-id="7b908-252">您將使用自動放置在報表主體頂端的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="7b908-252">You will use the text box that is automatically placed at the top of the report body.</span></span>  
  
 <span data-ttu-id="7b908-253">您可以將不同的字型樣式、大小和色彩套用到文字的片語和個別字元，進一步加強文字。</span><span class="sxs-lookup"><span data-stu-id="7b908-253">The text can be further enhanced by applying different font styles, sizes, and colors to phrases and individual characters of the text.</span></span> <span data-ttu-id="7b908-254">如需詳細資訊，請參閱[在文字方塊中將文字格式化 &#40;報表產生器及 SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7b908-254">For more information, see [Format Text in a Text Box &#40;Report Builder and SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="7b908-255">若要加入報表標題</span><span class="sxs-lookup"><span data-stu-id="7b908-255">To add a report title</span></span>  
  
1.  <span data-ttu-id="7b908-256">在設計介面上，按一下 **[按一下以加入標題]**。</span><span class="sxs-lookup"><span data-stu-id="7b908-256">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="7b908-257">輸入**產品銷售 KPI**，然後按一下文字方塊外部。</span><span class="sxs-lookup"><span data-stu-id="7b908-257">Type **Product Sales KPI**, and then click outside the text box.</span></span>  
  
3.  <span data-ttu-id="7b908-258">（選擇性）以滑鼠右鍵按一下包含**產品銷售 KPI**的文字方塊，然後按一下 [**文字方塊屬性**]，再于 [字型] 索引標籤上選取不同的字型樣式、大小和色彩。</span><span class="sxs-lookup"><span data-stu-id="7b908-258">Optionally, right-click the text box that contains **Product Sales KPI**, click **Text Box Properties**, and then on the Font tab select the different font styles, sizes and colors.</span></span>  
  
4.  <span data-ttu-id="7b908-259">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="7b908-259">Click **Run** to preview the report.</span></span>  
  
##  <a name="7-save-the-report"></a><a name="Save"></a><span data-ttu-id="7b908-260">7. 儲存報表</span><span class="sxs-lookup"><span data-stu-id="7b908-260">7. Save the Report</span></span>  
 <span data-ttu-id="7b908-261">將報表儲存至報表伺服器或您的電腦。</span><span class="sxs-lookup"><span data-stu-id="7b908-261">Save the report to a report server or your computer.</span></span> <span data-ttu-id="7b908-262">如果沒有將報表儲存到報表伺服器，就無法使用數個 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能，例如報表組件和子報表。</span><span class="sxs-lookup"><span data-stu-id="7b908-262">If you do not save the report to the report server, a number of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features such as report parts and subreports are not available.</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="7b908-263">若要將報表儲存在報表伺服器上</span><span class="sxs-lookup"><span data-stu-id="7b908-263">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="7b908-264">在 **[報表產生器]** 按鈕中，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="7b908-264">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="7b908-265">按一下 **[最近使用的網站和伺服器]**。</span><span class="sxs-lookup"><span data-stu-id="7b908-265">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="7b908-266">選取或輸入您有權儲存報表之報表伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="7b908-266">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="7b908-267">「正在連接到報表伺服器」訊息隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="7b908-267">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="7b908-268">連接完成時，您就會看見報表伺服器管理員指定為預設報表位置之報表資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="7b908-268">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>  
  
4.  <span data-ttu-id="7b908-269">將 [名稱]\*\*\*\* 中的預設名稱取代為**產品銷售 KPI**。</span><span class="sxs-lookup"><span data-stu-id="7b908-269">In **Name**, replace the default name with **Product Sales KPI**.</span></span>  
  
5.  <span data-ttu-id="7b908-270">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="7b908-270">Click **Save**.</span></span>  
  
 <span data-ttu-id="7b908-271">報表就會儲存至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="7b908-271">The report is saved to the report server.</span></span> <span data-ttu-id="7b908-272">您連接之報表伺服器的名稱會顯示在視窗底部的狀態列中。</span><span class="sxs-lookup"><span data-stu-id="7b908-272">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="7b908-273">將報表儲存到您的電腦上</span><span class="sxs-lookup"><span data-stu-id="7b908-273">To save the report on your computer</span></span>  
  
1.  <span data-ttu-id="7b908-274">在 **[報表產生器]** 按鈕中，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="7b908-274">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="7b908-275">按一下 [桌面]\*\*\*\*、[我的文件]\*\*\*\* 或 [我的電腦]\*\*\*\*，然後瀏覽到您要儲存報表的資料夾。</span><span class="sxs-lookup"><span data-stu-id="7b908-275">Click **Desktop**, **My Documents**, or **My computer**, and browse to the folder where you want to save the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b908-276">如果您無法存取報表伺服器，請按一下 [桌面]\*\*\*\*、[我的文件]\*\*\*\* 或 [我的電腦]\*\*\*\*，然後將報表儲存到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="7b908-276">If you do not have access to a report server, click **Desktop**, **My Documents**, or **My computer** and save the report to your computer.</span></span>  
  
1.  <span data-ttu-id="7b908-277">將 [名稱]\*\*\*\* 中的預設名稱取代為**產品銷售 KPI**。</span><span class="sxs-lookup"><span data-stu-id="7b908-277">In **Name**, replace the default name with **Product Sales KPI**.</span></span>  
  
2.  <span data-ttu-id="7b908-278">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="7b908-278">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7b908-279">後續步驟</span><span class="sxs-lookup"><span data-stu-id="7b908-279">Next Steps</span></span>  
 <span data-ttu-id="7b908-280">您已成功完成「將 KPI 加入至報表」教學課程。</span><span class="sxs-lookup"><span data-stu-id="7b908-280">You have successfully completed the Adding a KPI to Your Report tutorial.</span></span> <span data-ttu-id="7b908-281">如需詳細資訊，請參閱量測計 (報表產生器) 指標[&#40;報表產生器和 SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="7b908-281">For more information, see Gauges (Report Builder) [Indicators &#40;Report Builder and SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b908-282">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b908-282">See Also</span></span>  
 <span data-ttu-id="7b908-283">[教學課程 &#40;報表產生器&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="7b908-283">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="7b908-284">SQL Server 2014 中的報表產生器</span><span class="sxs-lookup"><span data-stu-id="7b908-284">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
