---
title: 教學課程：將橫條圖新增至報表 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6956ebd6-0217-4087-a4fa-5cc1c3804691
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01708ca548c40118daa03fac34d8a323d628b012
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594363"
---
# <a name="tutorial-add-a-bar-chart-to-your-report-report-builder"></a><span data-ttu-id="9c5d1-102">教學課程：將橫條圖加入至報表 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="9c5d1-102">Tutorial: Add a Bar Chart to Your Report (Report Builder)</span></span>
  <span data-ttu-id="9c5d1-103">橫條圖會以水平方向顯示類別目錄資料。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-103">A bar chart displays category data horizontally.</span></span> <span data-ttu-id="9c5d1-104">這樣有助於：</span><span class="sxs-lookup"><span data-stu-id="9c5d1-104">This can help to:</span></span>  
  
-   <span data-ttu-id="9c5d1-105">讓使用者容易閱讀冗長的類別目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-105">Improve readability of long category names.</span></span>  
  
-   <span data-ttu-id="9c5d1-106">讓使用者容易了解繪製成值的時間。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-106">Improve understandability of times plotted as values.</span></span>  
  
-   <span data-ttu-id="9c5d1-107">比較多個數列的相對值。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-107">Compare the relative value of multiple series.</span></span>  
  
 <span data-ttu-id="9c5d1-108">下圖顯示您將建立的橫條圖，其中以字母順序列出 2008 和 2009 年前五名銷售人員的銷售額。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-108">The following illustration shows the bar chart that you will create, with sales for 2008 and 2009 for the top five salespeople, in alphabetical order.</span></span>  
  
 <span data-ttu-id="9c5d1-109">![rs_BarChartTutorial](../../2014/tutorials/media/rs-barcharttutorial.gif "rs_BarChartTutorial")</span><span class="sxs-lookup"><span data-stu-id="9c5d1-109">![rs_BarChartTutorial](../../2014/tutorials/media/rs-barcharttutorial.gif "rs_BarChartTutorial")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="9c5d1-110">您將瞭解的內容</span><span class="sxs-lookup"><span data-stu-id="9c5d1-110">What You Will Learn</span></span>  
 <span data-ttu-id="9c5d1-111">在本教學課程中，您將學習如何執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="9c5d1-111">In this tutorial you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="9c5d1-112">從圖表精靈建立圖表</span><span class="sxs-lookup"><span data-stu-id="9c5d1-112">Create a Chart from the Chart Wizard</span></span>](#Chart)  
  
2.  [<span data-ttu-id="9c5d1-113">選擇圖表類型</span><span class="sxs-lookup"><span data-stu-id="9c5d1-113">Choose the Chart Type</span></span>](#ChartType)  
  
3.  [<span data-ttu-id="9c5d1-114">在垂直軸上顯示所有類別目錄值</span><span class="sxs-lookup"><span data-stu-id="9c5d1-114">Display all Category Values on the Vertical Axis</span></span>](#AllValues)  
  
4.  [<span data-ttu-id="9c5d1-115">修改垂直軸上的名稱顯示</span><span class="sxs-lookup"><span data-stu-id="9c5d1-115">Modify the Display of Names on the Vertical Axis</span></span>](#Sort)  
  
5.  [<span data-ttu-id="9c5d1-116">移動圖例</span><span class="sxs-lookup"><span data-stu-id="9c5d1-116">Move the Legend</span></span>](#Legend)  
  
6.  [<span data-ttu-id="9c5d1-117">移動圖表標題</span><span class="sxs-lookup"><span data-stu-id="9c5d1-117">Move the Chart Title</span></span>](#ChartTitle)  
  
7.  [<span data-ttu-id="9c5d1-118">格式化及標示水平軸</span><span class="sxs-lookup"><span data-stu-id="9c5d1-118">Format and Label the Horizontal Axis</span></span>](#Horizontal)  
  
8.  [<span data-ttu-id="9c5d1-119">加入篩選以顯示前五個值</span><span class="sxs-lookup"><span data-stu-id="9c5d1-119">Add a Filter to Display the Top Five Values</span></span>](#Filter)  
  
9. [<span data-ttu-id="9c5d1-120">加入報表標題</span><span class="sxs-lookup"><span data-stu-id="9c5d1-120">Add a Report Title</span></span>](#Title)  
  
10. [<span data-ttu-id="9c5d1-121">儲存報表</span><span class="sxs-lookup"><span data-stu-id="9c5d1-121">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="9c5d1-122">在本教學課程中，精靈的步驟會合併為一個程序。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-122">In this tutorial, the steps for the wizard are consolidated into one procedure.</span></span> <span data-ttu-id="9c5d1-123">如需如何瀏覽至報表伺服器、建立資料集以及選擇資料來源的逐步指示，請參閱本系列的第一個教學課程：[教學課程：建立基本資料表報表 &#40;報表產生器&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-123">For step-by-step instructions about how to browse to a report server, create a dataset, and choose a data source, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="9c5d1-124">完成本教學課程的估計時間：15 分鐘。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-124">Estimated time to complete this tutorial: 15 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c5d1-125">需求</span><span class="sxs-lookup"><span data-stu-id="9c5d1-125">Requirements</span></span>  
 <span data-ttu-id="9c5d1-126">如需需求的詳細資訊，請參閱[教學課程的必要條件 &#40;報表產生器&#41;](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-126">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-chart-report-from-the-chart-wizard"></a><a name="Chart"></a><span data-ttu-id="9c5d1-127">1. 從圖表 Wizard 建立圖表報表</span><span class="sxs-lookup"><span data-stu-id="9c5d1-127">1. Create a Chart Report from the Chart Wizard</span></span>  
 <span data-ttu-id="9c5d1-128">從 [**消費者入門**] 對話方塊中，建立內嵌的資料集、選擇共用資料來源，然後使用 [圖表] Wizard 建立橫條圖。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-128">From the **Getting Started** dialog box, create an embedded dataset, choose a shared data source, and create a bar chart by using the Chart Wizard.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c5d1-129">在本教學課程中，查詢會包含資料值，因此不需要外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-129">In this tutorial, the query contains the data values so that it does not need an external data source.</span></span> <span data-ttu-id="9c5d1-130">這樣會使查詢相當冗長。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-130">This makes the query quite long.</span></span> <span data-ttu-id="9c5d1-131">在商業環境中，查詢不會包含資料。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-131">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="9c5d1-132">這僅供教學之用。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-132">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-chart-report"></a><span data-ttu-id="9c5d1-133">建立新的圖表報表</span><span class="sxs-lookup"><span data-stu-id="9c5d1-133">To create a new chart report</span></span>  
  
1.  <span data-ttu-id="9c5d1-134">按一下 **[開始]**、依序指向 **[程式集]** 和 **[Microsoft SQL Server 2012 報表產生器]**，然後按一下 **[報表產生器]**。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-134">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="9c5d1-135">[**消費者入門**] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-135">The **Getting Started** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9c5d1-136">如果 [**消費者入門**] 對話方塊沒有出現，請按一下 [報表產生器] 按鈕，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-136">If the **Getting Started** dialog box does not appear, click the Report Builder button, and then click **New**.</span></span>  
  
2.  <span data-ttu-id="9c5d1-137">在左窗格中，確認已選取 **[新增報表]** 。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-137">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="9c5d1-138">在右窗格中，按一下 [圖表精靈]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-138">In the right pane, click **Chart Wizard**.</span></span>  
  
4.  <span data-ttu-id="9c5d1-139">在 [**選擇資料集**] 頁面上，按一下 [**建立資料集**]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-139">On the **Choose a dataset** page, click **Create a dataset**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="9c5d1-140">在 [選擇與資料來源的連線]\*\*\*\* 頁面上，選取現有的資料來源，或瀏覽至報表伺服器並選取資料來源，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-140">On the **Choose a connection to a data source** page, select an existing data source or browse to the report server and select a data source, and then click **Next**.</span></span> <span data-ttu-id="9c5d1-141">您可能需要輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-141">You may need to enter a user name and password.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9c5d1-142">只要您有適當的權限，選擇哪一種資料來源都無關緊要。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-142">The data source you choose is unimportant, as long as you have adequate permissions.</span></span> <span data-ttu-id="9c5d1-143">因為您不會從資料來源取得資料。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-143">You will not be getting data from the data source.</span></span> <span data-ttu-id="9c5d1-144">如需詳細資訊，請參閱[取得資料連線的替代方式 &#40;報表產生器&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-144">For more information, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
6.  <span data-ttu-id="9c5d1-145">在 **[設計查詢]** 頁面上，按一下 **[當成文字編輯]**。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-145">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
7.  <span data-ttu-id="9c5d1-146">將下列查詢貼入查詢窗格中：</span><span class="sxs-lookup"><span data-stu-id="9c5d1-146">Paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT 'Luis' as FirstName, 'Alverca' as LastName, CAST(170000.00 AS money) AS SalesYear2009, CAST(150000. AS money) AS SalesYear2008  
    UNION SELECT 'Jeffrey' as FirstName, 'Zeng' as LastName, CAST(210000. AS money) AS SalesYear2009, CAST(190000. AS money) AS SalesYear2008  
    UNION SELECT 'Houman' as FirstName, 'Pournasseh' as LastName, CAST(150000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Robin' as FirstName, 'Wood' as LastName, CAST(75000. AS money) AS SalesYear2009, CAST(175000. AS money) AS SalesYear2008  
    UNION SELECT 'Daniela' as FirstName, 'Guaita' as LastName,  CAST(170000. AS money) AS SalesYear2009, CAST(175000. AS money) AS SalesYear2008  
    UNION SELECT 'John' as FirstName, 'Yokim' as LastName, CAST(160000. AS money) AS SalesYear2009, CAST(195000. AS money) AS SalesYear2008  
    UNION SELECT 'Delphine' as FirstName, 'Ribaute' as LastName, CAST(180000. AS money) AS SalesYear2009, CAST(205000. AS money) AS SalesYear2008  
    UNION SELECT 'Robert' as FirstName, 'Hernady' as LastName, CAST(140000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Tanja' as FirstName, 'Plate' as LastName, CAST(150000. AS money) AS SalesYear2009, CAST(160000. AS money) AS SalesYear2008  
    UNION SELECT 'David' as FirstName, 'Bradley' as LastName, CAST(210000. AS money) AS SalesYear2009, CAST(180000. AS money) AS SalesYear2008  
    UNION SELECT 'Michal' as FirstName, 'Jaworski' as LastName, CAST(175000. AS money) AS SalesYear2009, CAST(220000. AS money) AS SalesYear2008  
    UNION SELECT 'Chris' as FirstName, 'Ashton' as LastName, CAST(195000. AS money) AS SalesYear2009, CAST(205000. AS money) AS SalesYear2008  
    UNION SELECT 'Pongsiri' as FirstName, 'Hirunyanitiwatna' as LastName, CAST(175000. AS money) AS SalesYear2009, CAST(215000. AS money) AS SalesYear2008  
    UNION SELECT 'Brian' as FirstName, 'Burke' as LastName, CAST(187000. AS money) AS SalesYear2009, CAST(207000. AS money) AS SalesYear2008  
    ```  
  
8.  <span data-ttu-id="9c5d1-147">(選擇性) 按一下 [執行] 按鈕 (**!**) 來查看您報表所依據的資料。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-147">(Optional) Click the Run button (**!**) to see the data your chart will be based on.</span></span>  
  
9. <span data-ttu-id="9c5d1-148">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-148">Click **Next**.</span></span>  
  
##  <a name="2-choose-the-chart-type"></a><a name="ChartType"></a><span data-ttu-id="9c5d1-149">2. 選擇圖表類型</span><span class="sxs-lookup"><span data-stu-id="9c5d1-149">2. Choose the Chart Type</span></span>  
 <span data-ttu-id="9c5d1-150">您可以選擇各種不同預先定義的圖表類型。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-150">You can choose from a variety of predefined chart types.</span></span>  
  
#### <a name="to-add-a-column-chart"></a><span data-ttu-id="9c5d1-151">加入直條圖</span><span class="sxs-lookup"><span data-stu-id="9c5d1-151">To add a column chart</span></span>  
  
1.  <span data-ttu-id="9c5d1-152">在 [選擇圖表類型]\*\*\*\* 頁面上，直條圖是預設圖表類型。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-152">On the **Choose a chart type** page, the column chart is the default chart type.</span></span>  
  
2.  <span data-ttu-id="9c5d1-153">按一下 [橫條圖]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-153">Click **Bar**, and then click **Next**.</span></span>  
  
     <span data-ttu-id="9c5d1-154">在 [**排列圖表欄位**] 頁面上，[**可用的欄位**] 窗格中有四個欄位： FirstName、LastName、SalesYear2009 和 SalesYear2008。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-154">On the **Arrange chart fields** page, there are four fields in the **Available fields** pane: FirstName, LastName, SalesYear2009, and SalesYear2008.</span></span>  
  
3.  <span data-ttu-id="9c5d1-155">將 [LastName] 拖曳至 [類別目錄] 窗格。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-155">Drag LastName to the Categories pane.</span></span>  
  
4.  <span data-ttu-id="9c5d1-156">將 [SalesYear2009] 拖曳至 [值] 窗格。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-156">Drag SalesYear2009 to the Values pane.</span></span> <span data-ttu-id="9c5d1-157">SalesYear2009 代表每位銷售人員 2009 年的銷售量。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-157">SalesYear2009 represents the sales amount for each salesperson for the year 2009.</span></span> <span data-ttu-id="9c5d1-158">[值] 窗格會顯示 `[Sum(SalesYear2009)]` ，因為圖表會顯示每項產品的彙總。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-158">The Values pane displays `[Sum(SalesYear2009)]` because the chart displays the aggregate for each product.</span></span>  
  
5.  <span data-ttu-id="9c5d1-159">將 [SalesYear2008] 拖曳至 [SalesYear2009] 下的 [值] 窗格。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-159">Drag SalesYear2008 to the Values pane under SalesYear2009.</span></span> <span data-ttu-id="9c5d1-160">SalesYear2008 代表每位銷售人員 2008 年的銷售量。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-160">SalesYear2008 represents the sales amount for each salesperson for the year 2008.</span></span>  
  
6.  <span data-ttu-id="9c5d1-161">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-161">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="9c5d1-162">在 [**選擇樣式**] 頁面的 [樣式] 窗格中，選取樣式。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-162">On the **Choose a style** page, in the Styles pane, select a style.</span></span>  
  
     <span data-ttu-id="9c5d1-163">樣式會指定字型樣式、色彩集和框線樣式。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-163">A style specifies a font style, a set of colors, and a border style.</span></span> <span data-ttu-id="9c5d1-164">當您選取樣式時，[預覽] 窗格會顯示具有該樣式的圖表範例。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-164">When you select a style, the Preview pane displays a sample of the chart with that style.</span></span>  
  
8.  <span data-ttu-id="9c5d1-165">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-165">Click **Finish**.</span></span>  
  
     <span data-ttu-id="9c5d1-166">圖表就會加入至設計介面。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-166">The chart is added to the design surface.</span></span>  
  
9. <span data-ttu-id="9c5d1-167">按一下圖表，即可顯示圖表控點。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-167">Click the chart to display the chart handles.</span></span> <span data-ttu-id="9c5d1-168">拖曳圖表的右下角，即可增加圖表的大小。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-168">Drag the bottom-right corner of the chart to increase the size of the chart.</span></span>  
  
10. <span data-ttu-id="9c5d1-169">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-169">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="9c5d1-170">報表會顯示每位銷售人員 2008 和 2009 年的銷售額橫條圖。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-170">The report displays the bar chart for sales for each sales person for the years 2008 and 2009.</span></span> <span data-ttu-id="9c5d1-171">橫條圖的長度對應至銷售總額。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-171">The length of the bar corresponds to the sales total.</span></span>  
  
##  <a name="3-modify-the-display-of-names-on-the-vertical-axis"></a><a name="AllValues"></a><span data-ttu-id="9c5d1-172">3. 修改垂直軸上的名稱顯示</span><span class="sxs-lookup"><span data-stu-id="9c5d1-172">3. Modify the Display of Names on the Vertical Axis</span></span>  
 <span data-ttu-id="9c5d1-173">根據預設，垂直軸上只會顯示部分值。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-173">By default, only some of the values on the vertical axis appear.</span></span> <span data-ttu-id="9c5d1-174">您可以變更圖表以顯示所有類別目錄。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-174">You can change the chart to display all categories.</span></span>  
  
#### <a name="to-display-all-sales-persons-along-the-category-axis-of-a-bar-chart"></a><span data-ttu-id="9c5d1-175">沿著橫條圖的類別目錄軸顯示所有銷售人員</span><span class="sxs-lookup"><span data-stu-id="9c5d1-175">To display all sales persons along the category axis of a bar chart</span></span>  
  
1.  <span data-ttu-id="9c5d1-176">切換到報表設計檢視。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-176">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="9c5d1-177">以滑鼠右鍵按一下垂直軸，然後按一下 [**垂直軸屬性**]。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-177">Right-click the vertical axis, and then click **Vertical Axis Properties**.</span></span>  
  
3.  <span data-ttu-id="9c5d1-178">在 [軸範圍和間隔]\*\*\*\* 的 [間隔]\*\*\*\* 方塊中，鍵入 **1**。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-178">Under **Axis range and interval**, in the **Interval** box, type **1**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="9c5d1-179">以滑鼠右鍵按一下垂直**軸標題**，並清除 [**顯示軸標題**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-179">Right-click the vertical **Axis Title** and clear the **Show Axis Title** check box.</span></span>  
  
6.  <span data-ttu-id="9c5d1-180">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-180">Click **Run** to preview the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c5d1-181">如果您無法在垂直軸上讀到銷售人員的名稱，可增加圖表的高度或變更軸標籤的格式選項。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-181">If you cannot read the salesperson names on the vertical axis, you can make your chart taller or change the formatting options for the axis labels.</span></span>  
  
###  <a name="display-last-name-and-first-name-on-vertical-axis"></a><a name="CategoryExpression"></a><span data-ttu-id="9c5d1-182">在垂直軸上顯示姓氏和名字</span><span class="sxs-lookup"><span data-stu-id="9c5d1-182">Display Last Name and First Name on Vertical Axis</span></span>  
 <span data-ttu-id="9c5d1-183">您可以變更類別目錄運算式，以依序包含每位銷售人員的姓氏和名字。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-183">You can change the category expression to include last name followed by first name of each sales person.</span></span>  
  
##### <a name="to-change-the-category-expression"></a><span data-ttu-id="9c5d1-184">變更類別目錄運算式</span><span class="sxs-lookup"><span data-stu-id="9c5d1-184">To change the category expression</span></span>  
  
1.  <span data-ttu-id="9c5d1-185">切換到報表設計檢視。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-185">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="9c5d1-186">按兩下圖表以顯示 [圖表資料]\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-186">Double-click the chart to display the **Chart Data** pane.</span></span>  
  
3.  <span data-ttu-id="9c5d1-187">在 [類別目錄群組]\*\*\*\* 區域中，以滑鼠右鍵按一下 [LastName]，然後按一下 [類別目錄群組屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-187">In the **Category Groups** area, right-click [LastName], and then click **Category Group Properties**.</span></span>  
  
4.  <span data-ttu-id="9c5d1-188">在 [標籤] 中，按一下運算式 (Fx) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-188">In Label, click the expression (Fx) button.</span></span>  
  
5.  <span data-ttu-id="9c5d1-189">輸入下列運算式： `=Fields!LastName.Value & ", " & Fields!FirstName.Value`</span><span class="sxs-lookup"><span data-stu-id="9c5d1-189">Type the following expression: `=Fields!LastName.Value & ", " & Fields!FirstName.Value`</span></span>  
  
     <span data-ttu-id="9c5d1-190">此運算式會串連姓氏、逗號和名字。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-190">This expression concatenates the last name, a comma, and the first name.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="9c5d1-191">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-191">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="9c5d1-192">如果您執行報表時未出現名字，可以手動重新整理資料。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-192">If the first names do not appear when you run the report, you can refresh the data manually.</span></span> <span data-ttu-id="9c5d1-193">當您依然在預覽模式時，於 [執行]\*\*\*\* 索引標籤的 [巡覽]\*\*\*\* 群組中，按一下 [重新整理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-193">While still in preview mode, on the **Run** tab in the **Navigation** group, click **Refresh**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c5d1-194">如果您無法在垂直軸上讀到銷售人員的名稱，可增加圖表的高度或變更軸標籤的格式選項。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-194">If you cannot read the salesperson names on the vertical axis, you can make your chart taller or change the formatting options for the axis labels.</span></span>  
  
##  <a name="4-change-the-sort-order-for-names-on-the-vertical-axis"></a><a name="Sort"></a><span data-ttu-id="9c5d1-195">4. 變更垂直軸上的名稱排序次序</span><span class="sxs-lookup"><span data-stu-id="9c5d1-195">4. Change the Sort Order for Names on the Vertical Axis</span></span>  
 <span data-ttu-id="9c5d1-196">當您排序圖表上的資料時，也會變更類別目錄軸上值的順序。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-196">When you sort the data on a chart, you are changing the order of values on the category axis.</span></span>  
  
#### <a name="to-sort-the-names-in-alphabetical-order-on-the-bar-chart"></a><span data-ttu-id="9c5d1-197">在橫條圖上按照字母順序排序名稱</span><span class="sxs-lookup"><span data-stu-id="9c5d1-197">To sort the names in alphabetical order on the bar chart</span></span>  
  
1.  <span data-ttu-id="9c5d1-198">切換到報表設計檢視。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-198">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="9c5d1-199">按兩下圖表以顯示 [圖表資料]\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-199">Double-click the chart to display the **Chart Data** pane.</span></span>  
  
3.  <span data-ttu-id="9c5d1-200">在 [類別目錄群組]\*\*\*\* 區域中，以滑鼠右鍵按一下 [LastName]，然後按一下 [類別目錄群組屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-200">In the **Category Groups** area, right-click [LastName], and then click **Category Group Properties**.</span></span>  
  
4.  <span data-ttu-id="9c5d1-201">按一下 **[排序]**。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-201">Click **Sorting**.</span></span> <span data-ttu-id="9c5d1-202">[變更排序選項]\*\*\*\* 頁面會顯示排序運算式的清單。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-202">The **Change sorting options** page displays a list of sort expressions.</span></span> <span data-ttu-id="9c5d1-203">根據預設，此清單包含的排序運算式與原始類別目錄群組運算式相同。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-203">By default, this list has one sort expression that is the same as the original category group expression.</span></span>  
  
5.  <span data-ttu-id="9c5d1-204">在 [排序依據] 中，按一下 [運算式] (**Fx**) ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-204">In Sort by, click the expression (**Fx**) button.</span></span>  
  
6.  <span data-ttu-id="9c5d1-205">輸入下列運算式： `=Fields!LastName.Value & ", " & Fields!FirstName.Value`</span><span class="sxs-lookup"><span data-stu-id="9c5d1-205">Type the following expression: `=Fields!LastName.Value & ", " & Fields!FirstName.Value`</span></span>  
  
7.  <span data-ttu-id="9c5d1-206">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-206">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="9c5d1-207">回到 [**類別目錄群組屬性**] 頁面的 [**順序**] 下拉式清單中，選取 [ **Z 到 A**]。這會選取反向字母順序，如此一來，名稱就會以從上而下的順序顯示。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-207">Back on the **Category Group Properties** page, in the **Order** drop-down list, select **Z to A**. This selects reverse alphabetical order so that the names appear in order from top to bottom.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. <span data-ttu-id="9c5d1-208">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-208">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="9c5d1-209">水準軸上的名稱會以反向順序排序，而**Alerca**位於頂端，而**Zeng**位於底部。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-209">The names on the horizontal axis are sorted in reverse order, with **Alerca** at the top and **Zeng** at the bottom.</span></span>  
  
##  <a name="5-move-the-legend"></a><a name="Legend"></a><span data-ttu-id="9c5d1-210">5. 移動圖例</span><span class="sxs-lookup"><span data-stu-id="9c5d1-210">5. Move the Legend</span></span>  
 <span data-ttu-id="9c5d1-211">為了改善圖表值的可讀性，您可能會想要移動圖表圖例。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-211">To improve the readability of the chart values, you might want to move the chart legend.</span></span> <span data-ttu-id="9c5d1-212">例如，在水平顯示橫條的橫條圖中，您可以變更圖例的位置，讓它位於圖表區域的上方或下方。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-212">For example, in a bar chart where bars are shown horizontally, you can change the position of the legend so that it is above or below the chart area.</span></span> <span data-ttu-id="9c5d1-213">這樣會提供更多水平空間給橫條。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-213">This gives more horizontal space to the bars.</span></span>  
  
#### <a name="to-display-the-legend-below-the-chart-area-of-a-bar-chart"></a><span data-ttu-id="9c5d1-214">在橫條圖的圖表區域下方顯示圖例</span><span class="sxs-lookup"><span data-stu-id="9c5d1-214">To display the legend below the chart area of a bar chart</span></span>  
  
1.  <span data-ttu-id="9c5d1-215">切換到報表設計檢視。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-215">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="9c5d1-216">以滑鼠右鍵按一下圖表上的圖例。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-216">Right-click the legend on the chart.</span></span>  
  
3.  <span data-ttu-id="9c5d1-217">選取 [圖例屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-217">Select **Legend Properties**.</span></span>  
  
4.  <span data-ttu-id="9c5d1-218">針對 [圖例位置]\*\*\*\*，選取不同的位置。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-218">For **Legend position**, select a different position.</span></span> <span data-ttu-id="9c5d1-219">例如，您可以將位置設定為中間底部。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-219">For example, set the position to the middle bottom option.</span></span>  
  
     <span data-ttu-id="9c5d1-220">當圖例位於圖表的頂端或底部時，圖例的配置就會從垂直變更為水平。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-220">When the legend is placed at the top or bottom of a chart, the layout of the legend changes from vertical to horizontal.</span></span> <span data-ttu-id="9c5d1-221">您可以從 [配置]\*\*\*\* 下拉式清單中選取不同的配置。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-221">You can select a different layout from the **Layout** drop-down list.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="9c5d1-222">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-222">Click **Run** to preview the report.</span></span>  
  
##  <a name="6-title-the-chart"></a><a name="ChartTitle"></a><span data-ttu-id="9c5d1-223">6. 為圖表標題</span><span class="sxs-lookup"><span data-stu-id="9c5d1-223">6. Title the Chart</span></span>  
  
#### <a name="to-change-the-chart-title-above-the-chart-area-of-a-bar-chart"></a><span data-ttu-id="9c5d1-224">變更橫條圖之圖表區域上方的圖表標題</span><span class="sxs-lookup"><span data-stu-id="9c5d1-224">To change the chart title above the chart area of a bar chart</span></span>  
  
1.  <span data-ttu-id="9c5d1-225">切換到報表設計檢視。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-225">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="9c5d1-226">選取圖表頂端的 [**圖表標題**] 這幾個字，然後輸入下列文字： **2008 和2009的銷售量**。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-226">Select the words **Chart Title** at the top of the chart, and then type the following text: **Sales for 2008 and 2009**.</span></span>  
  
3.  <span data-ttu-id="9c5d1-227">按一下文字外的任何位置。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-227">Click anywhere outside the text.</span></span>  
  
4.  <span data-ttu-id="9c5d1-228">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-228">Click **Run** to preview the report.</span></span>  
  
##  <a name="7-format-and-label-the-horizontal-axis"></a><a name="Horizontal"></a><span data-ttu-id="9c5d1-229">7. 格式化及標示水準軸</span><span class="sxs-lookup"><span data-stu-id="9c5d1-229">7. Format and Label the Horizontal Axis</span></span>  
 <span data-ttu-id="9c5d1-230">根據預設，水平軸會以一般格式顯示值，此格式會自動調整為適合圖表的大小。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-230">By default, the horizontal axis displays values in a general format that is automatically scaled to fit the size of the chart.</span></span>  
  
#### <a name="to-format-the-numbers-on-the-horizontal-axis"></a><span data-ttu-id="9c5d1-231">格式化水平軸上的數字</span><span class="sxs-lookup"><span data-stu-id="9c5d1-231">To format the numbers on the horizontal axis</span></span>  
  
1.  <span data-ttu-id="9c5d1-232">切換到報表設計檢視。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-232">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="9c5d1-233">沿著圖表的底部，按一下以選取水平軸。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-233">Click the horizontal axis along the bottom of the chart to select it.</span></span>  
  
     <span data-ttu-id="9c5d1-234">在功能區上，于 [**首頁**] 索引標籤的 [**數位**] 群組中，按一下 [**貨幣**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-234">On the ribbon, on the **Home** tab, in the **Number** group, click the **Currency** button.</span></span> <span data-ttu-id="9c5d1-235">水平軸標籤就會變更為貨幣。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-235">The horizontal axis labels change to currency.</span></span>  
  
3.  <span data-ttu-id="9c5d1-236">(選擇性) 移除小數位數。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-236">(Optional) Remove the decimal digits.</span></span> <span data-ttu-id="9c5d1-237">在 [貨幣]\*\*\*\* 按鈕附近按兩次 [減少小數位數]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-237">Near the **Currency** button, click the **Decrease Decimal** button twice.</span></span>  
  
4.  <span data-ttu-id="9c5d1-238">以滑鼠右鍵按一下水平軸，然後按一下 [水平軸屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-238">Right-click the horizontal axis, and click **Horizontal Axis Properties**.</span></span>  
  
5.  <span data-ttu-id="9c5d1-239">在 [**數位**] 索引標籤上，選取 [**以千為單位顯示值]。**</span><span class="sxs-lookup"><span data-stu-id="9c5d1-239">On the **Number** tab, select **Show values in Thousands.**</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="9c5d1-240">以滑鼠右鍵按一下 [**軸標題**]，然後按一下 [**軸標題屬性**]。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-240">Right-click **Axis Title** and click **Axis Title Properties**.</span></span>  
  
8.  <span data-ttu-id="9c5d1-241">在 [**標題] 文字方塊**中，輸入**以千為單位的銷售額**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-241">In the **Title text** box, type **Sales in thousands** and click **OK**.</span></span>  
  
9. <span data-ttu-id="9c5d1-242">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-242">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="9c5d1-243">報表會將水平軸上的銷售量顯示為以千為單位的貨幣，且沒有小數位數。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-243">The report displays the sales amount on the horizontal axis as currency in thousands, and has no decimal digits.</span></span>  
  
##  <a name="8-add-a-filter-to-display-the-top-five-values"></a><a name="Filter"></a><span data-ttu-id="9c5d1-244">8. 加入篩選以顯示前五個值</span><span class="sxs-lookup"><span data-stu-id="9c5d1-244">8. Add a Filter to Display the Top Five Values</span></span>  
 <span data-ttu-id="9c5d1-245">您可以將篩選加入至圖表，以指定要在圖表中包含或排除資料集中的哪些資料。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-245">You can add a filter to the chart to specify which data from the dataset to include or exclude in the chart.</span></span>  
  
#### <a name="to-add-a-filter-and-display-the-top-five-values"></a><span data-ttu-id="9c5d1-246">加入篩選並顯示前五個值</span><span class="sxs-lookup"><span data-stu-id="9c5d1-246">To add a filter and display the top five values</span></span>  
  
1.  <span data-ttu-id="9c5d1-247">切換到報表設計檢視。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-247">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="9c5d1-248">按兩下圖表以顯示 [圖表資料]\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-248">Double-click the chart to display the **Chart Data** pane.</span></span>  
  
3.  <span data-ttu-id="9c5d1-249">在 [類別目錄群組]\*\*\*\* 區域中，以滑鼠右鍵按一下 [LastName] 欄位，然後按一下 [類別目錄群組屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-249">In the **Category Groups** area, right-click the [LastName] field, and then click **Category Group Properties**.</span></span>  
  
4.  <span data-ttu-id="9c5d1-250">按一下 **[篩選]** 。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-250">Click **Filters**.</span></span> <span data-ttu-id="9c5d1-251">[變更篩選]\*\*\*\* 頁面可顯示篩選運算式的清單。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-251">The **Change filters** page can display a list of filter expressions.</span></span> <span data-ttu-id="9c5d1-252">根據預設，此清單是空的。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-252">By default, this list is empty.</span></span>  
  
5.  <span data-ttu-id="9c5d1-253">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-253">Click **Add**.</span></span> <span data-ttu-id="9c5d1-254">新的空白篩選隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-254">A new blank filter appears.</span></span>  
  
6.  <span data-ttu-id="9c5d1-255">在 [**運算式**] 中，輸入 **[Sum (SalesYear2009) ]**。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-255">In **Expression**, type **[Sum(SalesYear2009)]**.</span></span> <span data-ttu-id="9c5d1-256">這樣會建立基礎運算式 `=Sum(Fields!SalesYear2009.Value)`，如果您按一下 [fx]\*\*\*\* 按鈕可以看到此運算式。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-256">This creates the underlying expression `=Sum(Fields!SalesYear2009.Value)`, which you can see if you click the **fx** button.</span></span>  
  
7.  <span data-ttu-id="9c5d1-257">確認資料類型是 **Text**。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-257">Verify that the data type is **Text**.</span></span>  
  
8.  <span data-ttu-id="9c5d1-258">在 [運算子]\*\*\*\* 中，從下拉式清單選取 [前 N 個]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-258">In **Operator**, select **Top N** from the drop-down list.</span></span>  
  
9. <span data-ttu-id="9c5d1-259">在 [值]\*\*\*\* 中，鍵入下列運算式：**=5**</span><span class="sxs-lookup"><span data-stu-id="9c5d1-259">In **Value**, type the following expression: **=5**</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. <span data-ttu-id="9c5d1-260">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-260">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="9c5d1-261">如果您執行報表時結果並未經過篩選，可以手動重新整理資料。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-261">If the results are not filtered when you run the report, you can refresh the data manually.</span></span> <span data-ttu-id="9c5d1-262">在 [執行]\*\*\*\* 索引標籤的 [巡覽]\*\*\*\* 群組中，按一下 [重新整理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-262">On the **Run** tab in the **Navigation** group, click **Refresh**.</span></span>  
  
 <span data-ttu-id="9c5d1-263">此圖表就會顯示 2009 銷售資料中前五名的銷售人員名稱。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-263">The chart shows the top five salesperson names from the 2009 sales data.</span></span>  
  
##  <a name="9-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="9c5d1-264">9. 加入報表標題</span><span class="sxs-lookup"><span data-stu-id="9c5d1-264">9. Add a Report Title</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="9c5d1-265">若要加入報表標題</span><span class="sxs-lookup"><span data-stu-id="9c5d1-265">To add a report title</span></span>  
  
1.  <span data-ttu-id="9c5d1-266">在設計介面上，按一下 **[按一下以加入標題]**。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-266">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="9c5d1-267">輸入**銷售橫條圖**，按 enter，然後輸入**2009 的前五名賣方**，讓它看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="9c5d1-267">Type **Sales Bar Chart**, press ENTER, and then type **Top Five Sellers for 2009**, so it looks like this:</span></span>  
  
     <span data-ttu-id="9c5d1-268">**銷售橫條圖**</span><span class="sxs-lookup"><span data-stu-id="9c5d1-268">**Sales Bar Chart**</span></span>  
  
     <span data-ttu-id="9c5d1-269">**2009 年前五名銷售人員**</span><span class="sxs-lookup"><span data-stu-id="9c5d1-269">**Top Five Sellers for 2009**</span></span>  
  
3.  <span data-ttu-id="9c5d1-270">選取 [銷售橫條圖]\*\*\*\*，然後按一下 [粗體]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-270">Select **Sales Bar Chart**, and click the **Bold** button.</span></span>  
  
4.  <span data-ttu-id="9c5d1-271">選取**2009 的前五名賣方**，然後在 [**首頁**] 索引標籤的 [**字型**] 區段中，將字型大小設為**10**。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-271">Select **Top Five Sellers for 2009**, and in the **Font** section on the **Home** tab, set the font size to **10**.</span></span>  
  
5.  <span data-ttu-id="9c5d1-272">(選擇性) 您可能需要增加 [標題] 文字方塊的高度，才能容納兩行文字。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-272">(Optional) You may need to make the Title text box taller to accommodate the two lines of text.</span></span>  
  
     <span data-ttu-id="9c5d1-273">這個標題就會顯示在報表的頂端。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-273">This title will appear at the top of the report.</span></span> <span data-ttu-id="9c5d1-274">如果未定義任何頁首，則位於報表主體頂端的項目就相當於報表頁首。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-274">When there is no page header defined, items at the top of the report body are the equivalent of a report header.</span></span>  
  
6.  <span data-ttu-id="9c5d1-275">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-275">Click **Run** to preview the report.</span></span>  
  
##  <a name="10-save-the-report"></a><a name="Save"></a><span data-ttu-id="9c5d1-276">10. 儲存報表</span><span class="sxs-lookup"><span data-stu-id="9c5d1-276">10. Save the Report</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="9c5d1-277">若要儲存報表</span><span class="sxs-lookup"><span data-stu-id="9c5d1-277">To save the report</span></span>  
  
1.  <span data-ttu-id="9c5d1-278">切換到報表設計檢視。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-278">Switch to report design view.</span></span>  
  
2.  <span data-ttu-id="9c5d1-279">在 **[報表產生器]** 按鈕中，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-279">From the **Report Builder** button, click **Save As**.</span></span>  
  
3.  <span data-ttu-id="9c5d1-280">在 [名稱]\*\*\*\* 中，鍵入 **Sales Bar Chart**。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-280">In **Name**, type **Sales Bar Chart**.</span></span>  
  
4.  <span data-ttu-id="9c5d1-281">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-281">Click **Save**.</span></span>  
  
 <span data-ttu-id="9c5d1-282">您的報表就會儲存在報表伺服器上。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-282">Your report is saved on the report server.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9c5d1-283">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9c5d1-283">Next Steps</span></span>  
 <span data-ttu-id="9c5d1-284">您已順利完成「將橫條圖加入至報表」教學課程。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-284">You have successfully completed the Adding a Bar Chart to Your Report tutorial.</span></span> <span data-ttu-id="9c5d1-285">若要深入了解圖表，請參閱[圖表 &#40;報表產生器及 SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) 和[走勢圖和資料橫條 &#40;報表產生器及 SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9c5d1-285">To learn more about charts, see [Charts &#40;Report Builder and SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) and [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c5d1-286">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c5d1-286">See Also</span></span>  
 <span data-ttu-id="9c5d1-287">[教學課程 &#40;報表產生器&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="9c5d1-287">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="9c5d1-288">SQL Server 2014 中的報表產生器</span><span class="sxs-lookup"><span data-stu-id="9c5d1-288">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
