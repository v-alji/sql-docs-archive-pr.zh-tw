---
title: 教學課程：將圓形圖新增至報表 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eaadf7bf-c312-428a-b214-0a1fbf959c3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 318370b185dcd75a8c3c54be49c47756bad5f3c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704782"
---
# <a name="tutorial-add-a-pie-chart-to-your-report-report-builder"></a><span data-ttu-id="2f895-102">教學課程：將圓形圖加入至報表 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="2f895-102">Tutorial: Add a Pie Chart to Your Report (Report Builder)</span></span>
  <span data-ttu-id="2f895-103">圓形圖和環圈圖會將資料顯示為整體所佔的百分比。</span><span class="sxs-lookup"><span data-stu-id="2f895-103">Pie charts and doughnut charts display data as a proportion of the whole.</span></span> <span data-ttu-id="2f895-104">圓形圖最常用於在群組之間進行比較。</span><span class="sxs-lookup"><span data-stu-id="2f895-104">Pie charts are most commonly used to make comparisons between groups.</span></span> <span data-ttu-id="2f895-105">圓形圖和環圈圖以及金字塔圖和漏斗圖會構成一組稱為形狀圖的圖表。</span><span class="sxs-lookup"><span data-stu-id="2f895-105">Pie and doughnut charts, along with pyramid and funnel charts, constitute a group of charts known as shape charts.</span></span> <span data-ttu-id="2f895-106">形狀圖沒有軸。</span><span class="sxs-lookup"><span data-stu-id="2f895-106">Shape charts have no axes.</span></span> <span data-ttu-id="2f895-107">在形狀圖上放置數值欄位時，圖表會計算出每個值佔整體的百分比。</span><span class="sxs-lookup"><span data-stu-id="2f895-107">When a numeric field is dropped on a shape chart, the chart calculates the percentage of each value to the total.</span></span>  
  
 <span data-ttu-id="2f895-108">如果圓形圖上的資料點過多，資料點標籤可能會太擁擠而難以閱讀。</span><span class="sxs-lookup"><span data-stu-id="2f895-108">If there are too many data points on a pie chart, your data point labels might be too crowded to read.</span></span> <span data-ttu-id="2f895-109">在這種狀況下，請考慮使用折線圖。</span><span class="sxs-lookup"><span data-stu-id="2f895-109">In that case, consider using a line chart.</span></span> <span data-ttu-id="2f895-110">只有在您已將資料彙總成少數資料點之後，才應該考慮使用圓形圖。</span><span class="sxs-lookup"><span data-stu-id="2f895-110">Consider using pie charts only after you have aggregated your data into a few data points.</span></span>  
  
 <span data-ttu-id="2f895-111">下圖顯示您將建立的圓形圖。</span><span class="sxs-lookup"><span data-stu-id="2f895-111">The following illustration shows the pie chart you will create.</span></span>  
  
 <span data-ttu-id="2f895-112">![rs_TutorialPieChartConcave](../../2014/tutorials/media/rs-tutorialpiechartconcave.gif "rs_TutorialPieChartConcave")</span><span class="sxs-lookup"><span data-stu-id="2f895-112">![rs_TutorialPieChartConcave](../../2014/tutorials/media/rs-tutorialpiechartconcave.gif "rs_TutorialPieChartConcave")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="2f895-113">您將瞭解的內容</span><span class="sxs-lookup"><span data-stu-id="2f895-113">What You Will Learn</span></span>  
 <span data-ttu-id="2f895-114">在本教學課程中，您將學會如何：</span><span class="sxs-lookup"><span data-stu-id="2f895-114">In this tutorial, you will learn how to:</span></span>  
  
1.  [<span data-ttu-id="2f895-115">從圖表精靈建立圓形圖</span><span class="sxs-lookup"><span data-stu-id="2f895-115">Create a Pie Chart from the Chart Wizard</span></span>](#Chart)  
  
2.  [<span data-ttu-id="2f895-116">選擇圖表類型</span><span class="sxs-lookup"><span data-stu-id="2f895-116">Choose the Chart Type</span></span>](#ChartType)  
  
3.  [<span data-ttu-id="2f895-117">在每一塊配量中顯示百分比</span><span class="sxs-lookup"><span data-stu-id="2f895-117">Display Percentages in Each Slice</span></span>](#Percentages)  
  
4.  [<span data-ttu-id="2f895-118">將較小的配量收集成一塊配量</span><span class="sxs-lookup"><span data-stu-id="2f895-118">Combine Small Slices into One Slice</span></span>](#CombineSlices)  
  
5.  [<span data-ttu-id="2f895-119">自訂繪圖效果</span><span class="sxs-lookup"><span data-stu-id="2f895-119">Customize the Drawing Effect</span></span>](#DrawingEffect)  
  
6.  [<span data-ttu-id="2f895-120">加入報表標題</span><span class="sxs-lookup"><span data-stu-id="2f895-120">Add a Report Title</span></span>](#Title)  
  
7.  [<span data-ttu-id="2f895-121">儲存報表</span><span class="sxs-lookup"><span data-stu-id="2f895-121">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="2f895-122">在本教學課程中，精靈的步驟會合併為兩個程序。</span><span class="sxs-lookup"><span data-stu-id="2f895-122">In this tutorial, the steps for the wizard are consolidated into two procedures.</span></span> <span data-ttu-id="2f895-123">如需如何瀏覽至報表伺服器、新增資料來源以及新增資料集的逐步指示，請參閱本系列的第一個教學課程：[教學課程：建立基本資料表報表 &#40;報表產生器&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="2f895-123">For step-by-step instructions about how to browse to a report server, add a data source, and add a dataset, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="2f895-124">完成本教學課程的估計時間：10 分鐘</span><span class="sxs-lookup"><span data-stu-id="2f895-124">Estimated time to complete this tutorial: 10 minutes</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f895-125">需求</span><span class="sxs-lookup"><span data-stu-id="2f895-125">Requirements</span></span>  
 <span data-ttu-id="2f895-126">如需需求的詳細資訊，請參閱[教學課程的必要條件 &#40;報表產生器&#41;](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="2f895-126">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-pie-chart-from-the-chart-wizard"></a><a name="Chart"></a><span data-ttu-id="2f895-127">1. 從圖表 Wizard 建立圓形圖</span><span class="sxs-lookup"><span data-stu-id="2f895-127">1. Create a Pie Chart from the Chart Wizard</span></span>  
 <span data-ttu-id="2f895-128">從 [使用者入門] 對話方塊，使用 [圖表精靈] 建立內嵌資料集，並選擇共用資料來源，然後建立圓形圖。</span><span class="sxs-lookup"><span data-stu-id="2f895-128">From the Getting Started dialog box, use the Chart Wizard to create an embedded dataset, choose a shared data source, and create a pie chart.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2f895-129">在本教學課程中，查詢會包含資料值，因此不需要外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="2f895-129">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="2f895-130">這樣會使查詢相當冗長。</span><span class="sxs-lookup"><span data-stu-id="2f895-130">This makes the query quite long.</span></span> <span data-ttu-id="2f895-131">在商業環境中，查詢不會包含資料。</span><span class="sxs-lookup"><span data-stu-id="2f895-131">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="2f895-132">這僅供教學之用。</span><span class="sxs-lookup"><span data-stu-id="2f895-132">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-chart-report"></a><span data-ttu-id="2f895-133">建立新的圖表報表</span><span class="sxs-lookup"><span data-stu-id="2f895-133">To create a new chart report</span></span>  
  
1.  <span data-ttu-id="2f895-134">按一下 **[開始]**、依序指向 **[程式集]** 和 **[Microsoft SQL Server 2012 報表產生器]**，然後按一下 **[報表產生器]**。</span><span class="sxs-lookup"><span data-stu-id="2f895-134">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="2f895-135">[使用者入門] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="2f895-135">The Getting Started dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f895-136"> 如果 [使用者入門] 對話方塊沒有出現，請在 [報表產生器] 按鈕中按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="2f895-136">If the Getting Started dialog box does not appear, from the Report Builder button, click **New**.</span></span>  
  
2.  <span data-ttu-id="2f895-137">在左窗格中，確認已選取 **[新增報表]** 。</span><span class="sxs-lookup"><span data-stu-id="2f895-137">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="2f895-138">在右窗格中，按一下 [圖表精靈]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f895-138">In the right pane, click **Chart Wizard**.</span></span>  
  
4.  <span data-ttu-id="2f895-139">在 [**選擇資料集**] 頁面上，按一下 [**建立資料集**]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="2f895-139">On the **Choose a dataset** page, click **Create a dataset**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="2f895-140">在 [選擇與資料來源的連線]\*\*\*\* 頁面上，選取現有的資料來源，或瀏覽至報表伺服器並選取資料來源，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f895-140">On the **Choose a connection to a data source** page, select an existing data source or browse to the report server and select a data source, and then click **Next**.</span></span> <span data-ttu-id="2f895-141">您可能需要輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="2f895-141">You may need to enter a user name and password.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f895-142">只要您有適當的權限，選擇哪一種資料來源都無關緊要。</span><span class="sxs-lookup"><span data-stu-id="2f895-142">The data source you choose is unimportant, as long as you have adequate permissions.</span></span> <span data-ttu-id="2f895-143">因為您不會從資料來源取得資料。</span><span class="sxs-lookup"><span data-stu-id="2f895-143">You will not be getting data from the data source.</span></span> <span data-ttu-id="2f895-144">如需詳細資訊，請參閱[取得資料連線的替代方式 &#40;報表產生器&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="2f895-144">For more information, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
6.  <span data-ttu-id="2f895-145">在 [**設計查詢**] 頁面上，按一下 [當做**文字編輯**]。</span><span class="sxs-lookup"><span data-stu-id="2f895-145">On the **Design a Query** page, click **Edit as Text**.</span></span>  
  
7.  <span data-ttu-id="2f895-146">將下列查詢貼入查詢窗格中：</span><span class="sxs-lookup"><span data-stu-id="2f895-146">Paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT 'Advanced Digital Camera' AS Product, CAST(254995.21 AS money) AS Sales  
    UNION SELECT 'Slim Digital Camera' AS Product, CAST(164499.04 AS money) AS Sales  
    UNION SELECT 'SLR Digital Camera' AS Product, CAST(782176.79 AS money) AS Sales  
    UNION SELECT 'Lens Adapter' AS Product, CAST(36333.08 AS money) AS Sales  
    UNION SELECT 'Macro Zoom Lens' AS Product, CAST(40199.3 AS money) AS Sales  
    UNION SELECT 'USB Cable' AS Product, CAST(53245.5 AS money) AS Sales  
    UNION SELECT 'Independent Filmmaker Camcorder' AS Product, CAST(452288.0 AS money) AS Sales  
    UNION SELECT 'Full Frame Digital Camera' AS Product, CAST(247250.85 AS money) AS Sales  
    ```  
  
8.  <span data-ttu-id="2f895-147">(選擇性) 按一下 [執行] 按鈕 (**!**) 來查看您報表所依據的資料。</span><span class="sxs-lookup"><span data-stu-id="2f895-147">(Optional) Click the Run button (**!**) to see the data your chart will be based on.</span></span>  
  
9. <span data-ttu-id="2f895-148">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="2f895-148">Click **Next**.</span></span>  
  
##  <a name="2-choose-the-chart-type"></a><a name="ChartType"></a><span data-ttu-id="2f895-149">2. 選擇圖表類型</span><span class="sxs-lookup"><span data-stu-id="2f895-149">2. Choose the Chart Type</span></span>  
 <span data-ttu-id="2f895-150">您可以選擇各種不同預先定義的圖表類型。</span><span class="sxs-lookup"><span data-stu-id="2f895-150">You can choose from a variety of predefined chart types.</span></span>  
  
#### <a name="to-add-a-pie-chart"></a><span data-ttu-id="2f895-151">加入圓形圖</span><span class="sxs-lookup"><span data-stu-id="2f895-151">To add a pie chart</span></span>  
  
1.  <span data-ttu-id="2f895-152">在 [**選擇圖表類型**] 頁面上，按一下 [**圓形圖**]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="2f895-152">On the **Choose a chart type** page, click **Pie**, and then click **Next**.</span></span> <span data-ttu-id="2f895-153">[排列圖表欄位]\*\*\*\* 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="2f895-153">The **Arrange chart fields** page opens.</span></span>  
  
     <span data-ttu-id="2f895-154">在 [排列圖表欄位]\*\*\*\* 頁面上，將 [Product] 欄位拖曳至 [類別目錄]\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="2f895-154">On the **Arrange chart fields** page, drag the Product field to the **Categories** pane.</span></span> <span data-ttu-id="2f895-155">類別目錄會定義圓形圖中的配量數目。</span><span class="sxs-lookup"><span data-stu-id="2f895-155">Categories define the number of slices in the pie chart.</span></span> <span data-ttu-id="2f895-156">在這則範例中，共有八個配量，每一個代表一個產品。</span><span class="sxs-lookup"><span data-stu-id="2f895-156">In this example, there will be eight slices, one for each product.</span></span>  
  
2.  <span data-ttu-id="2f895-157">將 [Sales] 欄位拖曳至 [值]\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="2f895-157">Drag the Sales field to the **Values** pane.</span></span> <span data-ttu-id="2f895-158">Sales 代表每個子類別目錄的銷售量。</span><span class="sxs-lookup"><span data-stu-id="2f895-158">Sales represents the sales amount for the subcategory.</span></span> <span data-ttu-id="2f895-159">因為圖表會顯示每項產品的彙總，所以 [值]\*\*\*\* 窗格會顯示 `[Sum(Sales)]`。</span><span class="sxs-lookup"><span data-stu-id="2f895-159">The **Values** pane displays `[Sum(Sales)]` because the chart displays the aggregate for each product.</span></span>  
  
3.  <span data-ttu-id="2f895-160">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="2f895-160">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="2f895-161">在 [**選擇樣式**] 頁面的 [樣式] 窗格中，選取樣式。</span><span class="sxs-lookup"><span data-stu-id="2f895-161">On the **Choose a style** page, in the Styles pane, select a style.</span></span>  
  
     <span data-ttu-id="2f895-162">樣式會指定字型樣式、色彩集和框線樣式。</span><span class="sxs-lookup"><span data-stu-id="2f895-162">A style specifies a font style, a set of colors, and a border style.</span></span> <span data-ttu-id="2f895-163">當您選取樣式時，[預覽] 窗格會顯示具有該樣式的圖表範例。</span><span class="sxs-lookup"><span data-stu-id="2f895-163">When you select a style, the Preview pane displays a sample of the chart with that style.</span></span>  
  
5.  <span data-ttu-id="2f895-164">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="2f895-164">Click **Finish**.</span></span>  
  
     <span data-ttu-id="2f895-165">圖表就會加入至設計介面。</span><span class="sxs-lookup"><span data-stu-id="2f895-165">The chart is added to the design surface.</span></span>  
  
6.  <span data-ttu-id="2f895-166">按一下圖表，即可顯示圖表控點。</span><span class="sxs-lookup"><span data-stu-id="2f895-166">Click the chart to display the chart handles.</span></span> <span data-ttu-id="2f895-167">拖曳圖表的右下角，即可增加圖表的大小。</span><span class="sxs-lookup"><span data-stu-id="2f895-167">Drag the bottom-right corner of the chart to increase the size of the chart.</span></span> <span data-ttu-id="2f895-168">請注意，報表設計介面的大小會放大，以容納圖表的大小。</span><span class="sxs-lookup"><span data-stu-id="2f895-168">Note that the report design surface increases in size to accommodate the chart size.</span></span>  
  
7.  <span data-ttu-id="2f895-169">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="2f895-169">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="2f895-170">報表會顯示畫分有八個配量的圓形圖，每一塊表示一個產品。</span><span class="sxs-lookup"><span data-stu-id="2f895-170">The report displays the pie chart with eight slices, one for each product.</span></span> <span data-ttu-id="2f895-171">每個配量的大小代表該產品的銷售量。</span><span class="sxs-lookup"><span data-stu-id="2f895-171">The size of each slice represents the sales for that product.</span></span> <span data-ttu-id="2f895-172">其中 3 塊配量極少。</span><span class="sxs-lookup"><span data-stu-id="2f895-172">Three of the slices are quite thin.</span></span>  
  
##  <a name="3-display-percentages-in-each-slice"></a><a name="Percentages"></a><span data-ttu-id="2f895-173">3. 在每個配量中顯示百分比</span><span class="sxs-lookup"><span data-stu-id="2f895-173">3. Display Percentages in Each Slice</span></span>  
 <span data-ttu-id="2f895-174">在圓形圖的每個配量上，您可以顯示這個配量相較於整個圓形圖的百分比。</span><span class="sxs-lookup"><span data-stu-id="2f895-174">On each slice of the pie, you can display a percentage for this slice compared to the whole pie.</span></span>  
  
#### <a name="to-display-percentages-in-each-slice-of-the-pie-chart"></a><span data-ttu-id="2f895-175">若要在圓形圖的每個配量中顯示百分比</span><span class="sxs-lookup"><span data-stu-id="2f895-175">To display percentages in each slice of the pie chart</span></span>  
  
1.  <span data-ttu-id="2f895-176">切換到報表設計檢視。</span><span class="sxs-lookup"><span data-stu-id="2f895-176">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="2f895-177">以滑鼠右鍵按一下圓形圖，然後按一下 [顯示資料標籤]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f895-177">Right-click the pie chart and click **Show Data Labels**.</span></span> <span data-ttu-id="2f895-178">資料標籤就會顯示在圖表上。</span><span class="sxs-lookup"><span data-stu-id="2f895-178">The data labels appear on the chart.</span></span>  
  
3.  <span data-ttu-id="2f895-179">以滑鼠右鍵按一下標籤，然後按一下 [**數列標籤屬性**]。</span><span class="sxs-lookup"><span data-stu-id="2f895-179">Right-click a label, and then click **Series Label Properties**.</span></span>  
  
4.  <span data-ttu-id="2f895-180">在 [標籤資料] 中，從下拉式方塊中選取 [ **#PERCENT**]。</span><span class="sxs-lookup"><span data-stu-id="2f895-180">In Label data, from the drop-down box, select **#PERCENT**.</span></span>  
  
     <span data-ttu-id="2f895-181">若要以百分比顯示值，UseValueAsLabel 屬性必須為 False。</span><span class="sxs-lookup"><span data-stu-id="2f895-181">To display values as percentages, the UseValueAsLabel property must be false.</span></span> <span data-ttu-id="2f895-182">如果系統提示您在 [確認動作]\*\*\*\* 對話方塊中設定這個值，請按一下 [是]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f895-182">If you are prompted to set this value in the **Confirm Action** dialog, click **Yes**.</span></span>  
  
5.  <span data-ttu-id="2f895-183"> (選擇性) 若要指定標籤所顯示的小數位數，請輸入， `#PERCENT{Pn}` 其中*n*是要顯示的小數點位數。</span><span class="sxs-lookup"><span data-stu-id="2f895-183">(Optional) To specify how many decimal places the label shows, type `#PERCENT{Pn}` where *n* is the number of decimal places to display.</span></span> <span data-ttu-id="2f895-184">例如，若不要顯示任何小數位數，請輸入 `#PERCENT{P0}` 。</span><span class="sxs-lookup"><span data-stu-id="2f895-184">For example, to display no decimal places, type `#PERCENT{P0}`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f895-185">當您格式化百分比時，[數列標籤屬性]\*\*\*\* 對話方塊中的 [數字格式]\*\*\*\* 沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="2f895-185">**Number Format** in the **Series Label Properties** dialog box has no effect when you format percentages.</span></span> <span data-ttu-id="2f895-186">這會將標籤格式化成百分比，但是不會計算每個配量所代表的圓形圖百分比。</span><span class="sxs-lookup"><span data-stu-id="2f895-186">This formats the labels as percentages, but does not calculate the percentage of the pie that each slice represents.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="2f895-187">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="2f895-187">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="2f895-188">報表會顯示每個圓形圖配量佔整體的百分比。</span><span class="sxs-lookup"><span data-stu-id="2f895-188">The report displays the percentage of the whole for each pie slice.</span></span>  
  
##  <a name="4-combine-small-slices-into-one-slice"></a><a name="CombineSlices"></a><span data-ttu-id="2f895-189">4. 將小型配量結合成一個磁區</span><span class="sxs-lookup"><span data-stu-id="2f895-189">4. Combine Small Slices into One Slice</span></span>  
 <span data-ttu-id="2f895-190">圓形圖中有 3 塊配量極少。</span><span class="sxs-lookup"><span data-stu-id="2f895-190">Three of the slices in the pie are quite small.</span></span> <span data-ttu-id="2f895-191">您可以將多個比例較小的配量結合為一個代表所有配量的較大配量。</span><span class="sxs-lookup"><span data-stu-id="2f895-191">You can combine multiple small slices into one larger slice that represents all of them.</span></span>  
  
#### <a name="to-combine-any-slices-on-the-pie-chart-smaller-than-5-percent-into-one-slice"></a><span data-ttu-id="2f895-192">若要將圓形圖上小於 5% 的任何配量結合成單一配量</span><span class="sxs-lookup"><span data-stu-id="2f895-192">To combine any slices on the pie chart smaller than 5 percent into one slice</span></span>  
  
1.  <span data-ttu-id="2f895-193">切換到報表設計檢視。</span><span class="sxs-lookup"><span data-stu-id="2f895-193">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="2f895-194">在 [ **View** ] 索引標籤的 [**顯示/隱藏**] 群組中，選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="2f895-194">On the **View** tab, in the **Show/Hide** group, select **Properties**.</span></span>  
  
3.  <span data-ttu-id="2f895-195">在設計介面上按一下圓形圖的任何配量。</span><span class="sxs-lookup"><span data-stu-id="2f895-195">On the design surface, click on any slice of the pie chart.</span></span> <span data-ttu-id="2f895-196">數列的屬性會顯示在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="2f895-196">The properties for the series are displayed in the Properties pane.</span></span>  
  
4.  <span data-ttu-id="2f895-197">在 [一般] \*\*\*\* 區段中，展開 [CustomAttributes] \*\*\*\* 節點。</span><span class="sxs-lookup"><span data-stu-id="2f895-197">In the **General** section, expand the **CustomAttributes** node.</span></span>  
  
5.  <span data-ttu-id="2f895-198">將 **CollectedStyle** 屬性設定為 **SingleSlice**。</span><span class="sxs-lookup"><span data-stu-id="2f895-198">Set the **CollectedStyle** property to **SingleSlice**.</span></span>  
  
6.  <span data-ttu-id="2f895-199">確認 **CollectedThreshold** 屬性設定為 5。</span><span class="sxs-lookup"><span data-stu-id="2f895-199">Verify that the **CollectedThreshold** property is set to 5.</span></span>  
  
7.  <span data-ttu-id="2f895-200">確認 **CollectedThresholdUsePercent** 屬性設定為 **True**。</span><span class="sxs-lookup"><span data-stu-id="2f895-200">Verify that the **CollectedThresholdUsePercent** property is set to **True**.</span></span>  
  
8.  <span data-ttu-id="2f895-201">在功能區的 [**首頁**] 索引標籤上，按一下 [**執行**] 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="2f895-201">On the Ribbon, on the **Home** tab, click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="2f895-202">在圖例中，現在「其他」類別目錄就會存在。</span><span class="sxs-lookup"><span data-stu-id="2f895-202">In the legend, the category "Other" now exists.</span></span> <span data-ttu-id="2f895-203">新的圓形圖配量會將低於 5% 的所有配量結合成一個佔整個圓形圖 6% 的配量。</span><span class="sxs-lookup"><span data-stu-id="2f895-203">The new pie slice combines all the slices that were under 5% into one slice that is 6% of the whole pie.</span></span>  
  
##  <a name="5-customize-the-drawing-effect"></a><a name="DrawingEffect"></a><span data-ttu-id="2f895-204">5. 自訂繪圖效果</span><span class="sxs-lookup"><span data-stu-id="2f895-204">5. Customize the Drawing Effect</span></span>  
 <span data-ttu-id="2f895-205">在 [圖表精靈] 中，圓形圖的自訂樣式為 Ocean，外觀具有 Concave 的繪圖效果。</span><span class="sxs-lookup"><span data-stu-id="2f895-205">In the Chart Wizard, the default style for a pie chart is Ocean, which features a Concave drawing effect.</span></span> <span data-ttu-id="2f895-206">您可以在執行精靈後變更這個項目。</span><span class="sxs-lookup"><span data-stu-id="2f895-206">You can change that after you run the wizard.</span></span>  
  
#### <a name="to-add-a-drawing-effect-to-the-pie-chart"></a><span data-ttu-id="2f895-207">若要將繪製效果加入至圓形圖</span><span class="sxs-lookup"><span data-stu-id="2f895-207">To add a drawing effect to the pie chart</span></span>  
  
1.  <span data-ttu-id="2f895-208">切換到報表設計檢視。</span><span class="sxs-lookup"><span data-stu-id="2f895-208">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="2f895-209">如果 [屬性] 窗格尚未開啟，請在 [**視圖**] 索引標籤上選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="2f895-209">If the Properties pane is not already opened, on the **View** tab, select **Properties**.</span></span>  
  
3.  <span data-ttu-id="2f895-210">按兩下圓形圖本身。</span><span class="sxs-lookup"><span data-stu-id="2f895-210">Double-click the pie chart itself.</span></span> <span data-ttu-id="2f895-211">圓形圖的數列屬性就會顯示在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="2f895-211">The series properties for the pie chart are shown in the Properties pane.</span></span>  
  
4.  <span data-ttu-id="2f895-212">在 [屬性] 窗格中，展開 **[CustomAttributes]** 節點。</span><span class="sxs-lookup"><span data-stu-id="2f895-212">In the Properties pane, expand the **CustomAttributes** node.</span></span>  
  
5.  <span data-ttu-id="2f895-213">將**PieDrawingStyle**設定為**SoftEdge**。</span><span class="sxs-lookup"><span data-stu-id="2f895-213">Set the **PieDrawingStyle** to **SoftEdge**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f895-214">繪製效果和三維效果是互斥的選項。</span><span class="sxs-lookup"><span data-stu-id="2f895-214">Drawing effects and three-dimensional effects are exclusive options.</span></span> <span data-ttu-id="2f895-215">如果圖表已套用立體效果，[屬性] 窗格就無法使用**PieDrawingStyle** 。</span><span class="sxs-lookup"><span data-stu-id="2f895-215">If a chart has three-dimensional effects applied, **PieDrawingStyle** is not available on the Properties pane.</span></span>  
  
6.  <span data-ttu-id="2f895-216">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="2f895-216">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="2f895-217">下圖顯示具有柔邊效果的圓形圖。</span><span class="sxs-lookup"><span data-stu-id="2f895-217">The following illustration shows the pie chart with the soft edge effect.</span></span>  
  
 <span data-ttu-id="2f895-218">![rs_TutorialPieChartSoftEdge](../../2014/tutorials/media/rs-tutorialpiechartsoftedge.gif "rs_TutorialPieChartSoftEdge")</span><span class="sxs-lookup"><span data-stu-id="2f895-218">![rs_TutorialPieChartSoftEdge](../../2014/tutorials/media/rs-tutorialpiechartsoftedge.gif "rs_TutorialPieChartSoftEdge")</span></span>  
  
##  <a name="6-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="2f895-219">6. 加入報表標題</span><span class="sxs-lookup"><span data-stu-id="2f895-219">6. Add a Report Title</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="2f895-220">若要加入報表標題</span><span class="sxs-lookup"><span data-stu-id="2f895-220">To add a report title</span></span>  
  
1.  <span data-ttu-id="2f895-221">在設計介面上，按一下 **[按一下以加入標題]**。</span><span class="sxs-lookup"><span data-stu-id="2f895-221">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="2f895-222">輸入 **Camera and Camcorder Sales**並按 ENTER，然後輸入 **As a Percentage of Total Sales**，它看起來如下：</span><span class="sxs-lookup"><span data-stu-id="2f895-222">Type **Camera and Camcorder Sales**, press ENTER, and then type **As a Percentage of Total Sales**, so it looks like this:</span></span>  
  
     <span data-ttu-id="2f895-223">**Camera and Camcorder Sales**</span><span class="sxs-lookup"><span data-stu-id="2f895-223">**Camera and Camcorder Sales**</span></span>  
  
     <span data-ttu-id="2f895-224">**As a Percentage of Total Sales**</span><span class="sxs-lookup"><span data-stu-id="2f895-224">**As a Percentage of Total Sales**</span></span>  
  
3.  <span data-ttu-id="2f895-225">選取 [**相機和攝影機銷售**]，然後從功能區**的 [常用**] 索引標籤的 [**字型**] 區段中，按一下 [**粗體**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="2f895-225">Select **Camera and Camcorder Sales**, and click the **Bold** button from the **Font** section of the **Home** tab of the ribbon.</span></span>  
  
4.  <span data-ttu-id="2f895-226">選取 [**以總銷售額的百分比**]，然後在 [**首頁**] 索引標籤的 [**字型**] 區段中，將字型大小設為**10**。</span><span class="sxs-lookup"><span data-stu-id="2f895-226">Select **As a Percentage of Total Sales**, and in the **Font** section on the **Home** tab, set the font size to **10**.</span></span>  
  
5.  <span data-ttu-id="2f895-227">(選擇性) 您可能需要增加 [標題] 文字方塊的高度，才能容納兩行文字。</span><span class="sxs-lookup"><span data-stu-id="2f895-227">(Optional) You may need to make the Title text box taller to accommodate the two lines of text.</span></span>  
  
     <span data-ttu-id="2f895-228">這個標題就會顯示在報表的頂端。</span><span class="sxs-lookup"><span data-stu-id="2f895-228">This title will appear at the top of the report.</span></span> <span data-ttu-id="2f895-229">如果未定義任何頁首，則位於報表主體頂端的項目就相當於報表頁首。</span><span class="sxs-lookup"><span data-stu-id="2f895-229">When there is no page header defined, items at the top of the report body are the equivalent of a report header.</span></span>  
  
6.  <span data-ttu-id="2f895-230">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="2f895-230">Click **Run** to preview the report.</span></span>  
  
##  <a name="7-save-the-report"></a><a name="Save"></a><span data-ttu-id="2f895-231">7. 儲存報表</span><span class="sxs-lookup"><span data-stu-id="2f895-231">7. Save the Report</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="2f895-232">若要儲存報表</span><span class="sxs-lookup"><span data-stu-id="2f895-232">To save the report</span></span>  
  
1.  <span data-ttu-id="2f895-233">切換到報表設計檢視。</span><span class="sxs-lookup"><span data-stu-id="2f895-233">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="2f895-234">在 [報表產生器] 按鈕中，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="2f895-234">From the Report Builder button, click **Save As**.</span></span>  
  
3.  <span data-ttu-id="2f895-235">在 [名稱]\*\*\*\* 中，鍵入 **Sales Pie Chart**。</span><span class="sxs-lookup"><span data-stu-id="2f895-235">In **Name**, type **Sales Pie Chart**.</span></span>  
  
4.  <span data-ttu-id="2f895-236">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="2f895-236">Click **Save**.</span></span>  
  
 <span data-ttu-id="2f895-237">您的報表就會儲存在報表伺服器上。</span><span class="sxs-lookup"><span data-stu-id="2f895-237">Your report is saved on the report server.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2f895-238">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2f895-238">Next Steps</span></span>  
 <span data-ttu-id="2f895-239">您已成功完成「將圓形圖加入至報表」教學課程。</span><span class="sxs-lookup"><span data-stu-id="2f895-239">You have successfully completed the Adding a Pie Chart to Your Report tutorial.</span></span> <span data-ttu-id="2f895-240">若要深入了解圖表，請參閱[圖表 &#40;報表產生器及 SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) 和[走勢圖和資料橫條 &#40;報表產生器及 SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="2f895-240">To learn more about charts, see [Charts &#40;Report Builder and SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) and [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f895-241">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f895-241">See Also</span></span>  
 <span data-ttu-id="2f895-242">[教學課程 &#40;報表產生器&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="2f895-242">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="2f895-243">SQL Server 2014 中的報表產生器</span><span class="sxs-lookup"><span data-stu-id="2f895-243">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
