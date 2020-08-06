---
title: 教學課程：將直條圖新增至報表 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 63480059-b7b9-44b5-9d7f-91780db708b6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0ef3b3f2872c2f8181296bb05337ca18975ac2f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706150"
---
# <a name="tutorial-add-a-column-chart-to-your-report-report-builder"></a><span data-ttu-id="4c9a5-102">教學課程：將直條圖加入至報表 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="4c9a5-102">Tutorial: Add a Column Chart to Your Report (Report Builder)</span></span>
  <span data-ttu-id="4c9a5-103">直條圖是依據類別目錄群組，將數列顯示為一組垂直線。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-103">A column chart displays a series as a set of vertical bars that are grouped by category.</span></span> <span data-ttu-id="4c9a5-104">直條圖可用於：</span><span class="sxs-lookup"><span data-stu-id="4c9a5-104">A column chart can be useful to:</span></span>  
  
-   <span data-ttu-id="4c9a5-105">顯示一段時間的資料變更。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-105">Show data changes over a period of time.</span></span>  
  
-   <span data-ttu-id="4c9a5-106">比較多個數列的相對值。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-106">Compare the relative value of multiple series.</span></span>  
  
-   <span data-ttu-id="4c9a5-107">顯示移動平均來呈現趨勢。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-107">Display a moving average to show trends.</span></span>  
  
 <span data-ttu-id="4c9a5-108">下圖顯示您將建立的直條圖，內含移動平均。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-108">The following illustration shows the column chart you will create, with a moving average.</span></span>  
  
 <span data-ttu-id="4c9a5-109">![rs_TutorialColChartFinished](../../2014/tutorials/media/rs-tutorialcolchartfinished.gif "rs_TutorialColChartFinished")</span><span class="sxs-lookup"><span data-stu-id="4c9a5-109">![rs_TutorialColChartFinished](../../2014/tutorials/media/rs-tutorialcolchartfinished.gif "rs_TutorialColChartFinished")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="4c9a5-110">您將瞭解的內容</span><span class="sxs-lookup"><span data-stu-id="4c9a5-110">What You Will Learn</span></span>  
 <span data-ttu-id="4c9a5-111">在本教學課程中，您將學習如何執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="4c9a5-111">In this tutorial you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="4c9a5-112">從圖表精靈建立圖表</span><span class="sxs-lookup"><span data-stu-id="4c9a5-112">Create a Chart from the Chart Wizard</span></span>](#Chart)  
  
2.  [<span data-ttu-id="4c9a5-113">選擇圖表類型</span><span class="sxs-lookup"><span data-stu-id="4c9a5-113">Choose the Chart Type</span></span>](#ChartType)  
  
3.  [<span data-ttu-id="4c9a5-114">格式化及標示水平軸</span><span class="sxs-lookup"><span data-stu-id="4c9a5-114">Format and Label the Horizontal Axis</span></span>](#Horizontal)  
  
4.  [<span data-ttu-id="4c9a5-115">移動圖例</span><span class="sxs-lookup"><span data-stu-id="4c9a5-115">Move the Legend</span></span>](#Legend)  
  
5.  [<span data-ttu-id="4c9a5-116">為圖表加上標題</span><span class="sxs-lookup"><span data-stu-id="4c9a5-116">Title the Chart</span></span>](#ChartTitle)  
  
6.  [<span data-ttu-id="4c9a5-117">格式化及標示垂直軸</span><span class="sxs-lookup"><span data-stu-id="4c9a5-117">Format and Label the Vertical Axis</span></span>](#Vertical)  
  
7.  [<span data-ttu-id="4c9a5-118">加入移動平均</span><span class="sxs-lookup"><span data-stu-id="4c9a5-118">Add a Moving Average</span></span>](#Average)  
  
8.  [<span data-ttu-id="4c9a5-119">加入報表標題</span><span class="sxs-lookup"><span data-stu-id="4c9a5-119">Add a Report Title</span></span>](#Title)  
  
9. [<span data-ttu-id="4c9a5-120">儲存報表</span><span class="sxs-lookup"><span data-stu-id="4c9a5-120">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="4c9a5-121">在本教學課程中，精靈的步驟會合併為一個程序。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-121">In this tutorial, the steps for the wizard are consolidated into one procedure.</span></span> <span data-ttu-id="4c9a5-122">如需如何瀏覽至報表伺服器、選擇資料來源以及建立資料集的逐步指示，請參閱本系列的第一個教學課程：[教學課程：建立基本資料表報表 &#40;報表產生器&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-122">For step-by-step instructions about how to browse to a report server, choose a data source, and create a dataset, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="4c9a5-123">完成本教學課程的估計時間：15 分鐘。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-123">Estimated time to complete this tutorial: 15 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c9a5-124">需求</span><span class="sxs-lookup"><span data-stu-id="4c9a5-124">Requirements</span></span>  
 <span data-ttu-id="4c9a5-125">如需需求的資訊，請參閱[教學課程的必要條件 &#40;報表產生器&#41;](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-125">For information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-chart-report-from-the-chart-wizard"></a><a name="Chart"></a><span data-ttu-id="4c9a5-126">1. 從圖表 Wizard 建立圖表報表</span><span class="sxs-lookup"><span data-stu-id="4c9a5-126">1. Create a Chart Report from the Chart Wizard</span></span>  
 <span data-ttu-id="4c9a5-127">從 [**消費者入門**] 對話方塊中，使用 [圖表] Wizard 來建立內嵌資料集、選擇共用資料來源，以及建立直條圖。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-127">From the **Getting Started** dialog box, use the Chart Wizard to create an embedded dataset, choose a shared data source, and create a column chart.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4c9a5-128">在本教學課程中，查詢會包含資料值，因此不需要外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-128">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="4c9a5-129">這樣會使查詢相當冗長。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-129">This makes the query quite long.</span></span> <span data-ttu-id="4c9a5-130">在商業環境中，查詢不會包含資料。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-130">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="4c9a5-131">這僅供教學之用。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-131">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-chart-report"></a><span data-ttu-id="4c9a5-132">建立新的圖表報表</span><span class="sxs-lookup"><span data-stu-id="4c9a5-132">To create a new chart report</span></span>  
  
1.  <span data-ttu-id="4c9a5-133">按一下 **[開始]**、依序指向 **[程式集]** 和 **[Microsoft SQL Server 2012 報表產生器]**，然後按一下 **[報表產生器]**。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-133">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="4c9a5-134">[**消費者入門**] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-134">The **Getting Started** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4c9a5-135"> 如果 **[使用者入門]** 對話方塊沒有出現，請在 **[報表產生器]** 按鈕中按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-135">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
2.  <span data-ttu-id="4c9a5-136">在左窗格中，確認已選取 **[新增報表]** 。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-136">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="4c9a5-137">在右窗格中，按一下 [圖表精靈]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-137">In the right pane, click **Chart Wizard**.</span></span>  
  
4.  <span data-ttu-id="4c9a5-138">在 [選擇資料集]\*\*\*\* 頁面上，按一下 [建立資料集]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-138">On the **Choose a dataset page**, click **Create a dataset**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="4c9a5-139">在 [選擇與資料來源的連線]\*\*\*\* 頁面上，選取現有的資料來源，或瀏覽至報表伺服器並選取資料來源，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-139">On the **Choose a connection to a data source** page, select an existing data source or browse to the report server and select a data source, and then click **Next**.</span></span> <span data-ttu-id="4c9a5-140">您可能需要輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-140">You may need to enter a user name and password.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4c9a5-141">只要您有適當的權限，選擇哪一種資料來源都無關緊要。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-141">The data source you choose is unimportant, as long as you have adequate permissions.</span></span> <span data-ttu-id="4c9a5-142">因為您不會從資料來源取得資料。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-142">You will not be getting data from the data source.</span></span> <span data-ttu-id="4c9a5-143">如需詳細資訊，請參閱[取得資料連線的替代方式 &#40;報表產生器&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-143">For more information, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
6.  <span data-ttu-id="4c9a5-144">在 **[設計查詢]** 頁面上，按一下 **[當成文字編輯]**。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-144">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
7.  <span data-ttu-id="4c9a5-145">將下列查詢貼入查詢窗格中：</span><span class="sxs-lookup"><span data-stu-id="4c9a5-145">Paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT CAST('2009-01-01' AS date) AS SalesDate, CAST(54995.21 AS money) AS Sales  
    UNION SELECT CAST('2009-01-05' AS date) AS SalesDate, CAST(64499.04 AS money) AS Sales  
    UNION SELECT CAST('2009-02-11' AS date) AS SalesDate, CAST(37821.79 AS money) AS Sales  
    UNION SELECT CAST('2009-03-18' AS date) AS SalesDate, CAST(53633.08 AS money) AS Sales  
    UNION SELECT CAST('2009-04-23' AS date) AS SalesDate, CAST(24019.3 AS money) AS Sales  
    UNION SELECT CAST('2009-05-01' AS date) AS SalesDate, CAST(93245.5 AS money) AS Sales  
    UNION SELECT CAST('2009-06-06' AS date) AS SalesDate, CAST(55288.0 AS money) AS Sales  
    UNION SELECT CAST('2009-06-16' AS date) AS SalesDate, CAST(68733.5 AS money) AS Sales  
    UNION SELECT CAST('2009-07-16' AS date) AS SalesDate, CAST(24750.85 AS money) AS Sales  
    UNION SELECT CAST('2009-08-23' AS date) AS SalesDate, CAST(43452.3 AS money) AS Sales  
    UNION SELECT CAST('2009-09-24' AS date) AS SalesDate, CAST(58656. AS money) AS Sales  
    UNION SELECT CAST('2009-10-15' AS date) AS SalesDate, CAST(44583. AS money) AS Sales  
    UNION SELECT CAST('2009-11-21' AS date) AS SalesDate, CAST(81568. AS money) AS Sales  
    UNION SELECT CAST('2009-12-15' AS date) AS SalesDate, CAST(45973. AS money) AS Sales  
    UNION SELECT CAST('2009-12-26' AS date) AS SalesDate, CAST(96357. AS money) AS Sales  
    UNION SELECT CAST('2009-12-31' AS date) AS SalesDate, CAST(81946. AS money) AS Sales  
    ```  
  
8.  <span data-ttu-id="4c9a5-146">(選擇性) 按一下 [執行] 按鈕 (**!**) 來查看您報表所依據的資料。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-146">(Optional) Click the Run button (**!**) to see the data your chart will be based on.</span></span>  
  
9. <span data-ttu-id="4c9a5-147">按 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-147">Click **Next**.</span></span>  
  
##  <a name="2-choose-the-chart-type"></a><a name="ChartType"></a><span data-ttu-id="4c9a5-148">2. 選擇圖表類型</span><span class="sxs-lookup"><span data-stu-id="4c9a5-148">2. Choose the Chart Type</span></span>  
 <span data-ttu-id="4c9a5-149">您可以選擇各種不同預先定義的圖表類型。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-149">You can choose from a variety of predefined chart types.</span></span>  
  
#### <a name="to-add-a-column-chart"></a><span data-ttu-id="4c9a5-150">加入直條圖</span><span class="sxs-lookup"><span data-stu-id="4c9a5-150">To add a column chart</span></span>  
  
1.  <span data-ttu-id="4c9a5-151">在 [選擇圖表類型]\*\*\*\* 頁面上，直條圖是預設圖表類型。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-151">On the **Choose a chart type** page, the column chart is the default chart type.</span></span> <span data-ttu-id="4c9a5-152">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-152">Click **Next**.</span></span>  
  
2.  <span data-ttu-id="4c9a5-153">在 [排列圖表欄位]\*\*\*\* 頁面上，將 [SalesDate] 欄位拖曳至 [類別目錄]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-153">On the **Arrange chart fields** page, drag the SalesDate field to **Categories**.</span></span> <span data-ttu-id="4c9a5-154">類別目錄會顯示在水平軸上。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-154">Categories display on the horizontal axis.</span></span>  
  
3.  <span data-ttu-id="4c9a5-155">將 [Sales] 欄位拖曳至 [值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-155">Drag the Sales field to **Values**.</span></span> <span data-ttu-id="4c9a5-156">[值]\*\*\*\* 方塊會顯示 [Sum(Sales)]，因為系統會針對每個日期彙總銷售總計值的總和。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-156">The **Values** box displays Sum(Sales) because the sum of the sales total value is aggregated for each date.</span></span> <span data-ttu-id="4c9a5-157">值會顯示在垂直軸上。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-157">Values display on the vertical axis.</span></span>  
  
4.  <span data-ttu-id="4c9a5-158">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-158">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="4c9a5-159">在 [**選擇樣式**] 頁面的 [樣式] 方塊中，選取樣式。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-159">On the **Choose a Style** page, in the Styles box, select a style.</span></span>  
  
     <span data-ttu-id="4c9a5-160">樣式會指定字型樣式、色彩集和框線樣式。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-160">A style specifies a font style, a set of colors, and a border style.</span></span> <span data-ttu-id="4c9a5-161">當您選取樣式時，[預覽] 窗格會顯示具有該樣式的圖表範例。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-161">When you select a style, the Preview pane displays a sample of the chart with that style.</span></span>  
  
6.  <span data-ttu-id="4c9a5-162">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-162">Click **Finish**.</span></span>  
  
     <span data-ttu-id="4c9a5-163">圖表就會加入至設計介面。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-163">The chart is added to the design surface.</span></span>  
  
7.  <span data-ttu-id="4c9a5-164">按一下圖表，即可顯示圖表控點。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-164">Click the chart to display the chart handles.</span></span> <span data-ttu-id="4c9a5-165">拖曳圖表的右下角，即可增加圖表的大小。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-165">Drag the bottom-right corner of the chart to increase the size of the chart.</span></span> <span data-ttu-id="4c9a5-166">請注意，報表設計介面的大小會放大，以容納圖表的大小。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-166">Note that the report design surface increases in size to accommodate the chart size.</span></span>  
  
8.  <span data-ttu-id="4c9a5-167">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-167">Click **Run** to preview the report.</span></span>  
  
##  <a name="3-format-and-label-the-horizontal-axis"></a><a name="Horizontal"></a><span data-ttu-id="4c9a5-168">3. 將水準軸格式化並加上標籤</span><span class="sxs-lookup"><span data-stu-id="4c9a5-168">3. Format and Label the Horizontal Axis</span></span>  
 <span data-ttu-id="4c9a5-169">根據預設，水平軸會以一般格式顯示值，此格式會自動調整為適合圖表的大小。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-169">By default, the horizontal axis displays values in a general format that is automatically scaled to fit the size of the chart.</span></span>  
  
#### <a name="to-format-a-date-on-the-horizontal-axis"></a><span data-ttu-id="4c9a5-170">若要格式化水平軸上的日期</span><span class="sxs-lookup"><span data-stu-id="4c9a5-170">To format a date on the horizontal axis</span></span>  
  
1.  <span data-ttu-id="4c9a5-171">切換到報表設計檢視。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-171">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="4c9a5-172">以滑鼠右鍵按一下水準軸，然後按一下 [**水準軸屬性**]。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-172">Right-click the horizontal axis, and then click **Horizontal Axis Properties**.</span></span>  
  
3.  <span data-ttu-id="4c9a5-173">按一下 **[數值]**。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-173">Click **Number**.</span></span>  
  
4.  <span data-ttu-id="4c9a5-174">在 [**類別**] 中，選取 [**日期**]。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-174">In **Category**, select **Date**.</span></span>  
  
5.  <span data-ttu-id="4c9a5-175">在 [類型]\*\*\*\* 方塊中，選取 [31 Jan 2000]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-175">In the **Type** box, select **31 Jan 2000**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="4c9a5-176">在 [主資料夾] 索引標籤上，按一下 [執行]\*\*\*\* 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-176">On the Home tab, click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="4c9a5-177">日期會以您所選取的日期格式顯示。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-177">The date displays in the date format that you selected.</span></span> <span data-ttu-id="4c9a5-178">請注意，圖表並未在水平軸上標示每個類別目錄。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-178">Notice that the chart does not label every category on the horizontal axis.</span></span> <span data-ttu-id="4c9a5-179">根據預設，只有容納在軸旁的標籤才會包含在內。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-179">By default, only labels that fit next to the axis are included.</span></span>  
  
 <span data-ttu-id="4c9a5-180">您可以透過旋轉標籤和指定間隔，自訂標籤顯示。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-180">You can customize the label display by rotating the labels and specifying the interval.</span></span>  
  
#### <a name="to-rotate-the-axis-labels-and-change-the-display-interval-along-the-horizontal-axis"></a><span data-ttu-id="4c9a5-181">若要沿著水平軸旋轉軸標籤和變更顯示間隔</span><span class="sxs-lookup"><span data-stu-id="4c9a5-181">To rotate the axis labels and change the display interval along the horizontal axis</span></span>  
  
1.  <span data-ttu-id="4c9a5-182">切換到報表設計檢視。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-182">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="4c9a5-183">以滑鼠右鍵按一下水準軸標題，然後按一下 [**顯示軸標題**] 以移除標題。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-183">Right-click the horizontal axis title, and then click **Show Axis Title** to remove the title.</span></span> <span data-ttu-id="4c9a5-184">因為水平軸會顯示日期，所以不需要這個標題。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-184">Because the horizontal axis displays dates, the title is not needed.</span></span>  
  
3.  <span data-ttu-id="4c9a5-185">以滑鼠右鍵按一下水準軸，然後按一下 [**水準軸屬性**]。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-185">Right-click the horizontal axis and then click **Horizontal Axis Properties**.</span></span>  
  
4.  <span data-ttu-id="4c9a5-186">在 [**軸選項**] 頁面的 [**軸範圍和間隔**] 下，為 [**間隔**] 輸入**3** 。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-186">In the **Axis Options** page under **Axis range and interval**, type **3** for **Interval**.</span></span> <span data-ttu-id="4c9a5-187">圖表將會顯示每隔三天的資料。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-187">The chart will display every third date.</span></span>  
  
5.  <span data-ttu-id="4c9a5-188">按一下 **[標籤]**。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-188">Click **Labels**.</span></span>  
  
6.  <span data-ttu-id="4c9a5-189">在 [**變更軸標籤自動調整選項**] 中，選取 [**停用自動調整**]。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-189">In **Change axis label auto-fit options**, select **Disable auto-fit**.</span></span>  
  
7.  <span data-ttu-id="4c9a5-190">在 [標籤旋轉角度]\*\*\*\* 中，選取 [-90]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-190">In **Label rotation angle**, select **-90**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="4c9a5-191">水平軸的範例文字會旋轉 90 度。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-191">The sample text for the horizontal axis rotates by 90 degrees.</span></span>  
  
9. <span data-ttu-id="4c9a5-192">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-192">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="4c9a5-193">在圖表上，標籤會旋轉而且會顯示每隔三天的標籤。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-193">On the chart, the labels are rotated and the label for every third date is shown.</span></span>  
  
##  <a name="4-move-the-legend"></a><a name="Legend"></a><span data-ttu-id="4c9a5-194">4. 移動圖例</span><span class="sxs-lookup"><span data-stu-id="4c9a5-194">4. Move the Legend</span></span>  
 <span data-ttu-id="4c9a5-195">圖例是從類別目錄和數列資料自動建立。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-195">The legend is automatically created from category and series data.</span></span>  
  
#### <a name="to-move-the-legend-below-the-chart-area-of-a-column-chart"></a><span data-ttu-id="4c9a5-196">若要移動直條圖之圖表區域下方的圖例</span><span class="sxs-lookup"><span data-stu-id="4c9a5-196">To move the legend below the chart area of a column chart</span></span>  
  
1.  <span data-ttu-id="4c9a5-197">切換到報表設計檢視。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-197">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="4c9a5-198">以滑鼠右鍵按一下圖表上的圖例，然後按一下 [**圖例屬性**]。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-198">Right-click the legend on the chart, and then click **Legend Properties**.</span></span>  
  
3.  <span data-ttu-id="4c9a5-199">針對 [版面配置]**和 [位置**]，選取不同的位置。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-199">For **Layout and Position**, select a different position.</span></span> <span data-ttu-id="4c9a5-200">例如，您可以將位置設定為中間底部。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-200">For example, set the position to the middle bottom option.</span></span>  
  
     <span data-ttu-id="4c9a5-201">當圖例位於圖表的頂端或底部時，圖例的配置就會從垂直變更為水平。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-201">When the legend is placed at the top or bottom of a chart, the layout of the legend changes from vertical to horizontal.</span></span> <span data-ttu-id="4c9a5-202">您可以從 [配置]\*\*\*\* 下拉式清單中選取不同的配置。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-202">You can select a different layout from the **Layout** drop-down list.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="4c9a5-203">(選擇性) 因為這個教學課程只有一個類別目錄，所以不需要圖例。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-203">(Optional) Because there is only one category in this tutorial, the legend is not needed.</span></span> <span data-ttu-id="4c9a5-204">若要移除圖例，請以滑鼠右鍵按一下圖例，然後按一下 [**刪除圖例**]。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-204">To remove the legend, right-click the legend and then click **Delete Legend**.</span></span>  
  
6.  <span data-ttu-id="4c9a5-205">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-205">Click **Run** to preview the report.</span></span>  
  
##  <a name="5-title-the-chart"></a><a name="ChartTitle"></a><span data-ttu-id="4c9a5-206">5. 為圖表標題</span><span class="sxs-lookup"><span data-stu-id="4c9a5-206">5. Title the Chart</span></span>  
  
#### <a name="to-change-the-chart-title-above-the-chart-area"></a><span data-ttu-id="4c9a5-207">若要變更圖表區域上方的圖表標題</span><span class="sxs-lookup"><span data-stu-id="4c9a5-207">To change the chart title above the chart area</span></span>  
  
1.  <span data-ttu-id="4c9a5-208">切換到報表設計檢視。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-208">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="4c9a5-209">選取圖表頂端的 [**圖表標題**] 這幾個字，然後輸入下列文字：**商店銷售訂單總計**。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-209">Select the words **Chart Title** at the top of the chart, and then type the following text: **Store Sales Order Totals**.</span></span>  
  
3.  <span data-ttu-id="4c9a5-210">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-210">Click **Run** to preview the report.</span></span>  
  
##  <a name="6-format-and-label-the-vertical-axis"></a><a name="Vertical"></a><span data-ttu-id="4c9a5-211">6. 格式化垂直軸並為其加上標籤</span><span class="sxs-lookup"><span data-stu-id="4c9a5-211">6. Format and Label the Vertical Axis</span></span>  
 <span data-ttu-id="4c9a5-212">根據預設，垂直軸會以一般格式顯示值，此格式會自動調整為適合圖表的大小。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-212">By default, the vertical axis displays values in a general format that is automatically scaled to fit the size of the chart.</span></span>  
  
#### <a name="to-format-as-currency-the-numbers-on-the-vertical-axis"></a><span data-ttu-id="4c9a5-213">若要將垂直軸上的數字格式化成貨幣</span><span class="sxs-lookup"><span data-stu-id="4c9a5-213">To format as currency the numbers on the vertical axis</span></span>  
  
1.  <span data-ttu-id="4c9a5-214">切換到報表設計檢視。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-214">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="4c9a5-215">沿著圖表的側邊，按兩下垂直軸上的標籤，以便選取。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-215">Double-click the labels on the vertical axis along the side of the chart to select them.</span></span>  
  
3.  <span data-ttu-id="4c9a5-216">在功能區上，于 [**首頁**] 索引標籤的 [**數位**] 群組中，按一下 [**貨幣**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-216">On the ribbon, on the **Home** tab, in the **Number** group, click the **Currency** button.</span></span> <span data-ttu-id="4c9a5-217">這些軸標籤就會變更為顯示貨幣格式。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-217">The axis labels change to show the currency format.</span></span>  
  
4.  <span data-ttu-id="4c9a5-218">在功能區上，于 [**首頁**] 索引標籤的 [**數位**] 群組中，按一下 [**減少小**數位數] 按鈕兩次，以顯示四捨五入到最接近的金額。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-218">On the ribbon, on the **Home** tab, in the **Number** group, click the **Decrease Decimal** button two times, to show the number rounded to the nearest dollar.</span></span>  
  
5.  <span data-ttu-id="4c9a5-219">以滑鼠右鍵按一下垂直軸，然後按一下 [**垂直軸屬性**]。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-219">Right-click the vertical axis and click **Vertical Axis Properties**.</span></span>  
  
6.  <span data-ttu-id="4c9a5-220">按一下 **[數值]**。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-220">Click **Number**.</span></span> <span data-ttu-id="4c9a5-221">請注意，[**類別目錄**] 方塊中已選取 [**貨幣**]，而 [**小數位數**] 已經是**0** (零) 。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-221">Note that **Currency** is already selected in the **Category** box, and **Decimal places** is already **0** (zero).</span></span>  
  
7.  <span data-ttu-id="4c9a5-222">在 [**顯示值于**] 方塊中，按一下 [**千**]。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-222">In the **Show Values in** box, click **Thousands**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. <span data-ttu-id="4c9a5-223">以滑鼠右鍵按一下圖表側邊的垂直軸標題，然後按一下 [**軸標題屬性**]。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-223">Right-click the vertical axis title along the side of the chart and click **Axis Title Properties**.</span></span>  
  
10. <span data-ttu-id="4c9a5-224">將 [**標題文字**] 欄位中的文字取代為下列文字： [ \*\*Sales Total] (為千位) \*\*。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-224">Replace the text in the **Title text** field with the following text: **Sales Total (in Thousands)**.</span></span> <span data-ttu-id="4c9a5-225">您也可以指定各種有關如何格式化標題的選項。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-225">You can also specify a variety of options related to how the title is formatted.</span></span>  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. <span data-ttu-id="4c9a5-226">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-226">Click **Run** to preview the report.</span></span>  
  
##  <a name="7-add-a-moving-average"></a><a name="Average"></a><span data-ttu-id="4c9a5-227">7. 加入移動平均</span><span class="sxs-lookup"><span data-stu-id="4c9a5-227">7. Add a Moving Average</span></span>  
  
#### <a name="to-add-a-moving-average"></a><span data-ttu-id="4c9a5-228">若要加入移動平均</span><span class="sxs-lookup"><span data-stu-id="4c9a5-228">To add a moving average</span></span>  
  
1.  <span data-ttu-id="4c9a5-229">切換到報表設計檢視。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-229">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="4c9a5-230">按兩下圖表以顯示 [圖表資料]\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-230">Double-click the chart to display the **Chart Data** pane.</span></span>  
  
3.  <span data-ttu-id="4c9a5-231">以滑鼠右鍵按一下位於 [**值**] 區域中的 **[Sum (Sales) ]** 欄位，然後按一下 [**加入匯出數列**]。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-231">Right-click the **[Sum(Sales)]** field that is in the **Values** area, and then click **Add Calculated Series**.</span></span>  
  
4.  <span data-ttu-id="4c9a5-232">在 [公式]\*\*\*\* 中，確認已選取 [移動平均]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-232">In **Formula**, verify that **Moving average** is selected.</span></span>  
  
5.  <span data-ttu-id="4c9a5-233">在 [設定公式參數]\*\*\*\* 中，針對 [週期]\*\*\*\* 選取 [4]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-233">In **Set Formula Parameters**, for **Period**, select **4**.</span></span>  
  
6.  <span data-ttu-id="4c9a5-234">按一下 [**框線**]。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-234">Click **Border**.</span></span>  
  
7.  <span data-ttu-id="4c9a5-235">在 [**線條寬度**] 中，選取 [ **3pt**]。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-235">In **Line width**, select **3pt**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. <span data-ttu-id="4c9a5-236">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-236">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="4c9a5-237">圖表會顯示一條線，代表依照日期區分之總銷售量的移動平均 (每四個日期的平均)。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-237">The chart displays a line that shows the moving average for total sales by date, averaged over every four dates.</span></span>  
  
##  <a name="8-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="4c9a5-238">8. 加入報表標題</span><span class="sxs-lookup"><span data-stu-id="4c9a5-238">8. Add a Report Title</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="4c9a5-239">若要加入報表標題</span><span class="sxs-lookup"><span data-stu-id="4c9a5-239">To add a report title</span></span>  
  
1.  <span data-ttu-id="4c9a5-240">切換到報表設計檢視。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-240">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="4c9a5-241">在設計介面上，按一下 **[按一下以加入標題]**。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-241">On the design surface, click **Click to add title**.</span></span>  
  
3.  <span data-ttu-id="4c9a5-242">輸入**銷售圖表**，按 enter，然後輸入**2009 年1月到12月**，讓它看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="4c9a5-242">Type **Sales Chart**, press ENTER, and then type **January to December 2009**, so it looks like this:</span></span>  
  
     <span data-ttu-id="4c9a5-243">**銷售圖表**</span><span class="sxs-lookup"><span data-stu-id="4c9a5-243">**Sales Chart**</span></span>  
  
     <span data-ttu-id="4c9a5-244">**2009 年 1 月到 12 月**</span><span class="sxs-lookup"><span data-stu-id="4c9a5-244">**January to December 2009**</span></span>  
  
4.  <span data-ttu-id="4c9a5-245">選取 [**銷售圖表**]，然後在功能區**的 [常用**] 索引標籤上，按一下 [**字型**] 區段中的 [**粗體**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-245">Select **Sales Chart**, and click the **Bold** button in the **Font** section on the **Home** tab of the ribbon.</span></span>  
  
5.  <span data-ttu-id="4c9a5-246">選取 [**一月至12月 2009**]，然後在 [**首頁**] 索引標籤的 [**字型**] 區段中，將字型大小設為**10**。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-246">Select **January to December 2009**, and in the **Font** section on the **Home** tab, set the font size to **10**.</span></span>  
  
6.  <span data-ttu-id="4c9a5-247"> (選擇性) 您可能需要讓 [**標題**] 文字方塊的高度，以容納兩行文字，方法是在您按一下下邊緣的中間時，向下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-247">(Optional) You may need to make the **Title** text box taller to accommodate the two lines of text by pulling down on the double-headed arrows when you click in the middle of the bottom edge.</span></span>  
  
     <span data-ttu-id="4c9a5-248">這個標題就會顯示在報表的頂端。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-248">This title will appear at the top of the report.</span></span> <span data-ttu-id="4c9a5-249">如果未定義任何頁首，則位於報表主體頂端的項目就相當於報表頁首。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-249">When there is no page header defined, items at the top of the report body are the equivalent of a report header.</span></span>  
  
7.  <span data-ttu-id="4c9a5-250">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-250">Click **Run** to preview the report.</span></span>  
  
##  <a name="9-save-the-report"></a><a name="Save"></a><span data-ttu-id="4c9a5-251">9. 儲存報表</span><span class="sxs-lookup"><span data-stu-id="4c9a5-251">9. Save the Report</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="4c9a5-252">若要儲存報表</span><span class="sxs-lookup"><span data-stu-id="4c9a5-252">To save the report</span></span>  
  
1.  <span data-ttu-id="4c9a5-253">切換到報表設計檢視。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-253">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="4c9a5-254">在 [報表產生器] 按鈕中，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-254">From the Report Builder button, click **Save As**.</span></span>  
  
3.  <span data-ttu-id="4c9a5-255">在 [名稱]\*\*\*\* 中，鍵入 **Sales Order Column Chart**。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-255">In **Name**, type **Sales Order Column Chart**.</span></span>  
  
4.  <span data-ttu-id="4c9a5-256">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-256">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4c9a5-257">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4c9a5-257">Next Steps</span></span>  
 <span data-ttu-id="4c9a5-258">您已成功完成「將直條圖加入至報表」教學課程。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-258">You have successfully completed the Adding a Column Chart to Your Report tutorial.</span></span> <span data-ttu-id="4c9a5-259">若要深入了解圖表，請參閱[圖表 &#40;報表產生器及 SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) 和[走勢圖和資料橫條 &#40;報表產生器及 SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4c9a5-259">To learn more about charts, see [Charts &#40;Report Builder and SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) and [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c9a5-260">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c9a5-260">See Also</span></span>  
 <span data-ttu-id="4c9a5-261">[教學課程 &#40;報表產生器&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="4c9a5-261">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="4c9a5-262">SQL Server 2014 中的報表產生器</span><span class="sxs-lookup"><span data-stu-id="4c9a5-262">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
