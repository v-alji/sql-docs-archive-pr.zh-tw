---
title: 教學課程：建立基本資料表報表 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d9e30521-f8ae-4c45-89c3-d40727f622f7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3587e2a53e2b09dd347a2733875eafd708b8a05a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593258"
---
# <a name="tutorial-creating-a-basic-table-report-report-builder"></a><span data-ttu-id="f36db-102">教學課程：建立基本資料表報表 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="f36db-102">Tutorial: Creating a Basic Table Report (Report Builder)</span></span>
  <span data-ttu-id="f36db-103">本教學課程將教導您根據範例銷售資料建立基本資料表報表。</span><span class="sxs-lookup"><span data-stu-id="f36db-103">This tutorial teaches you to create a basic table report based on sample sales data.</span></span> <span data-ttu-id="f36db-104">下圖顯示您將建立的報表。</span><span class="sxs-lookup"><span data-stu-id="f36db-104">The following illustration shows the report you will create.</span></span>  
  
 <span data-ttu-id="f36db-105">![rs_CreateBasicReportTutorial](../../2014/tutorials/media/rs-createbasicreporttutorial.gif "rs_CreateBasicReportTutorial")</span><span class="sxs-lookup"><span data-stu-id="f36db-105">![rs_CreateBasicReportTutorial](../../2014/tutorials/media/rs-createbasicreporttutorial.gif "rs_CreateBasicReportTutorial")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="f36db-106">您將瞭解的內容</span><span class="sxs-lookup"><span data-stu-id="f36db-106">What You Will Learn</span></span>  
 <span data-ttu-id="f36db-107">在本教學課程中，您將學習如何執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="f36db-107">In this tutorial, you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="f36db-108">從使用者入門建立新報表</span><span class="sxs-lookup"><span data-stu-id="f36db-108">Create a New Report from Getting Started</span></span>](#CreateTable)  
  
    1.  [<span data-ttu-id="f36db-109">在資料表精靈中指定資料連接</span><span class="sxs-lookup"><span data-stu-id="f36db-109">Specify a Data Connection in the Table Wizard</span></span>](#DataConnection)  
  
    2.  [<span data-ttu-id="f36db-110">在資料表精靈中建立查詢</span><span class="sxs-lookup"><span data-stu-id="f36db-110">Create a Query in the Table Wizard</span></span>](#Query)  
  
    3.  [<span data-ttu-id="f36db-111">在資料表精靈中將資料組織成群組</span><span class="sxs-lookup"><span data-stu-id="f36db-111">Organize Data into Groups in the Table Wizard</span></span>](#Groups)  
  
    4.  [<span data-ttu-id="f36db-112">在資料表精靈中加入小計和總計資料列</span><span class="sxs-lookup"><span data-stu-id="f36db-112">Add Subtotal and Total Rows in the Table Wizard</span></span>](#Subtotals)  
  
    5.  [<span data-ttu-id="f36db-113">在資料表精靈中選擇樣式</span><span class="sxs-lookup"><span data-stu-id="f36db-113">Choose a Style in the Table Wizard</span></span>](#Style)  
  
2.  [<span data-ttu-id="f36db-114">將資料格式化為貨幣</span><span class="sxs-lookup"><span data-stu-id="f36db-114">Format Data as Currency</span></span>](#FormatCurrency)  
  
3.  [<span data-ttu-id="f36db-115">將資料格式化為日期</span><span class="sxs-lookup"><span data-stu-id="f36db-115">Format Data as Date</span></span>](#FormatDate)  
  
4.  [<span data-ttu-id="f36db-116">變更資料行寬度</span><span class="sxs-lookup"><span data-stu-id="f36db-116">Change Column Widths</span></span>](#Width)  
  
5.  [<span data-ttu-id="f36db-117">加入報表標題</span><span class="sxs-lookup"><span data-stu-id="f36db-117">Add a Report Title</span></span>](#Title)  
  
6.  [<span data-ttu-id="f36db-118">儲存報表</span><span class="sxs-lookup"><span data-stu-id="f36db-118">Save the Report</span></span>](#Save)  
  
7.  [<span data-ttu-id="f36db-119">匯出報表</span><span class="sxs-lookup"><span data-stu-id="f36db-119">Export the Report</span></span>](#Export)  
  
 <span data-ttu-id="f36db-120">完成這個教學課程的估計時間：30 分鐘。</span><span class="sxs-lookup"><span data-stu-id="f36db-120">Estimated time to complete this tutorial: 20 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f36db-121">需求</span><span class="sxs-lookup"><span data-stu-id="f36db-121">Requirements</span></span>  
 <span data-ttu-id="f36db-122">如需需求的詳細資訊，請參閱[教學課程的必要條件 &#40;報表產生器&#41;](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="f36db-122">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-new-report-from-getting-started"></a><a name="CreateTable"></a><span data-ttu-id="f36db-123">1. 從消費者入門建立新的報表</span><span class="sxs-lookup"><span data-stu-id="f36db-123">1. Create a New Report from Getting Started</span></span>  
 <span data-ttu-id="f36db-124">從 [**消費者入門**] 對話方塊建立資料表報表。</span><span class="sxs-lookup"><span data-stu-id="f36db-124">Create a table report from the **Getting Started** dialog box.</span></span> <span data-ttu-id="f36db-125">模式有兩種：報表設計和共用資料集設計。</span><span class="sxs-lookup"><span data-stu-id="f36db-125">There are two modes: report design and shared dataset design.</span></span> <span data-ttu-id="f36db-126">在報表設計模式中，您可以在 [報表資料] 窗格中指定資料，並且在設計介面上指定報表配置。</span><span class="sxs-lookup"><span data-stu-id="f36db-126">In report design mode, you specify data in the Report Data pane and the report layout on the design surface.</span></span> <span data-ttu-id="f36db-127">在共用資料集設計模式中，您可以建立資料集查詢，以便與其他人共用。</span><span class="sxs-lookup"><span data-stu-id="f36db-127">In shared dataset design mode, you create dataset queries to share with others.</span></span> <span data-ttu-id="f36db-128">在本教學課程中，您將使用報表設計模式。</span><span class="sxs-lookup"><span data-stu-id="f36db-128">In this tutorial, you will be using report design mode.</span></span>  
  
#### <a name="to-create-a-new-report"></a><span data-ttu-id="f36db-129">建立新的報表</span><span class="sxs-lookup"><span data-stu-id="f36db-129">To create a new report</span></span>  
  
1.  <span data-ttu-id="f36db-130">按一下 **[開始]**、依序指向 **[程式集]** 和 **[Microsoft SQL Server 2012 報表產生器]**，然後按一下 **[報表產生器]**。</span><span class="sxs-lookup"><span data-stu-id="f36db-130">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="f36db-131">**[使用者入門]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="f36db-131">The **Getting Started** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f36db-132"> 如果 **[使用者入門]** 對話方塊沒有出現，請在 **[報表產生器]** 按鈕中按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="f36db-132">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
2.  <span data-ttu-id="f36db-133">在左窗格中，確認已選取 **[新增報表]** 。</span><span class="sxs-lookup"><span data-stu-id="f36db-133">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="f36db-134">在右窗格中，確認已選取 **[資料表或矩陣精靈]** 。</span><span class="sxs-lookup"><span data-stu-id="f36db-134">In the right pane, verify that **Table or Matrix Wizard** is selected.</span></span>  
  
##  <a name="1a-specify-a-data-connection-in-the-table-wizard"></a><a name="DataConnection"></a><span data-ttu-id="f36db-135">1a.</span><span class="sxs-lookup"><span data-stu-id="f36db-135">1a.</span></span> <span data-ttu-id="f36db-136">在資料表精靈中指定資料連接</span><span class="sxs-lookup"><span data-stu-id="f36db-136">Specify a Data Connection in the Table Wizard</span></span>  
 <span data-ttu-id="f36db-137">資料連接包含連接至外部資料來源的資訊，例如 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f36db-137">A data connection contains the information to connect to an external data source such as a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="f36db-138">通常您會向資料來源擁有者取得連接資訊以及要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="f36db-138">Usually, you get the connection information and the type of credentials to use from the data source owner.</span></span> <span data-ttu-id="f36db-139">若要指定資料連接，您可以使用來自報表伺服器的共用資料來源，或是建立僅在此報表中使用的內嵌資料來源。</span><span class="sxs-lookup"><span data-stu-id="f36db-139">To specify a data connection, you can use a shared data source from the report server or create an embedded data source that is used only in this report.</span></span>  
  
 <span data-ttu-id="f36db-140">在本教學課程中，您將使用內嵌資料來源。</span><span class="sxs-lookup"><span data-stu-id="f36db-140">In this tutorial, you will use an embedded data source.</span></span> <span data-ttu-id="f36db-141">若要深入了解如何使用共用資料來源，請參閱[取得資料連線的替代方式 &#40;報表產生器&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="f36db-141">To learn more about using a shared data sources, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
#### <a name="to-create-an-embedded-data-source"></a><span data-ttu-id="f36db-142">建立內嵌資料來源</span><span class="sxs-lookup"><span data-stu-id="f36db-142">To create an embedded data source</span></span>  
  
1.  <span data-ttu-id="f36db-143">在 **[選擇資料集]** 頁面上，選取 **[建立資料集]**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="f36db-143">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span> <span data-ttu-id="f36db-144">**[選擇與資料來源的連接]** 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="f36db-144">The **Choose a connection to a data source** page opens.</span></span>  
  
2.  <span data-ttu-id="f36db-145">按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="f36db-145">Click **New**.</span></span> <span data-ttu-id="f36db-146">**[資料來源屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="f36db-146">The **Data Source Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="f36db-147">在 [**名稱**] 中，輸入**產品銷售**的資料來源名稱。</span><span class="sxs-lookup"><span data-stu-id="f36db-147">In **Name**, type **Product Sales** a name for the data source.</span></span>  
  
4.  <span data-ttu-id="f36db-148">在 [選取連線類型]\*\*\*\* 中，驗證已選取 [Microsoft SQL Server]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f36db-148">In **Select a connection type**, verify that **Microsoft SQL Server** is selected.</span></span>  
  
5.  <span data-ttu-id="f36db-149">在 [**連接字串**] 中，輸入下列文字，其中 *\<servername>* 是實例的名稱 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="f36db-149">In **Connection string**, type the following text, where *\<servername>* is the name of an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
    ```  
    Data Source=<servername>  
    ```  
  
     <span data-ttu-id="f36db-150">由於您將使用包含資料的查詢，而不是從資料庫擷取資料，因此連接字串不會包含資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="f36db-150">Because you will use a query that contains the data instead of retrieving the data from a database, the connection string does not include the database name.</span></span> <span data-ttu-id="f36db-151">如需詳細資訊，請參閱[教學課程的必要條件 &#40;報表產生器&#41;](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="f36db-151">For more information, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
6.  <span data-ttu-id="f36db-152">按一下 **[認證]**。</span><span class="sxs-lookup"><span data-stu-id="f36db-152">Click **Credentials**.</span></span> <span data-ttu-id="f36db-153">輸入您存取外部資料來源所需的認證。</span><span class="sxs-lookup"><span data-stu-id="f36db-153">Enter the credentials that you need to access the external data source.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="f36db-154">您會回到 [選擇與資料來源的連線]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="f36db-154">You are back on the **Choose a connection to a data source** page.</span></span>  
  
8.  <span data-ttu-id="f36db-155">若要確認您能夠連接至資料來源，請按一下 **[測試連接]**。</span><span class="sxs-lookup"><span data-stu-id="f36db-155">To verify that you can connect to the data source, click **Test Connection**.</span></span>  
  
     <span data-ttu-id="f36db-156">「成功建立連接」訊息就會出現。</span><span class="sxs-lookup"><span data-stu-id="f36db-156">The message "Connection created successfully" appears.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. <span data-ttu-id="f36db-157">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="f36db-157">Click **Next**.</span></span>  
  
##  <a name="1b-create-a-query-in-the-table-wizard"></a><a name="Query"></a><span data-ttu-id="f36db-158">1a-1b.</span><span class="sxs-lookup"><span data-stu-id="f36db-158">1b.</span></span> <span data-ttu-id="f36db-159">在資料表精靈中建立查詢</span><span class="sxs-lookup"><span data-stu-id="f36db-159">Create a Query in the Table Wizard</span></span>  
 <span data-ttu-id="f36db-160">在報表中，您可以使用擁有預先定義查詢的共用資料集，或是建立只在報表中使用的內嵌資料集。</span><span class="sxs-lookup"><span data-stu-id="f36db-160">In a report, you can use a shared dataset that has a predefined query, or you can create an embedded dataset for use only in your report.</span></span> <span data-ttu-id="f36db-161">在本教學課程中，您將建立內嵌資料集。</span><span class="sxs-lookup"><span data-stu-id="f36db-161">In this tutorial, you will create an embedded dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f36db-162">在本教學課程中，查詢會包含資料值，因此不需要外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="f36db-162">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="f36db-163">這樣會使查詢相當冗長。</span><span class="sxs-lookup"><span data-stu-id="f36db-163">This makes the query quite long.</span></span> <span data-ttu-id="f36db-164">在商業環境中，查詢不會包含資料。</span><span class="sxs-lookup"><span data-stu-id="f36db-164">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="f36db-165">這僅供教學之用。</span><span class="sxs-lookup"><span data-stu-id="f36db-165">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-query"></a><span data-ttu-id="f36db-166">建立查詢</span><span class="sxs-lookup"><span data-stu-id="f36db-166">To create a query</span></span>  
  
1.  <span data-ttu-id="f36db-167">[設計查詢]\*\*\*\* 頁面上會開啟關聯式查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="f36db-167">On the **Design a query** page, the relational query designer is open.</span></span> <span data-ttu-id="f36db-168">在這個教學課程中，您將使用以文字為基礎的查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="f36db-168">For this tutorial, you will use the text-based query designer.</span></span>  
  
     <span data-ttu-id="f36db-169">按一下 [當成**文字編輯**]。</span><span class="sxs-lookup"><span data-stu-id="f36db-169">Click **Edit As Text**.</span></span> <span data-ttu-id="f36db-170">以文字為基礎的查詢設計工具會顯示查詢窗格和結果窗格。</span><span class="sxs-lookup"><span data-stu-id="f36db-170">The text-based query designer displays a query pane and a results pane.</span></span>  
  
2.  <span data-ttu-id="f36db-171">將下列 [!INCLUDE[tsql](../includes/tsql-md.md)] 查詢貼入 [查詢]\*\*\*\* 方塊。</span><span class="sxs-lookup"><span data-stu-id="f36db-171">Paste the following [!INCLUDE[tsql](../includes/tsql-md.md)] query into the **Query** box.</span></span>  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Carrying Case' as Product, CAST(9924.60 AS money) AS Sales, 68 as Quantity  
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
  
3.  <span data-ttu-id="f36db-172">在 [查詢設計工具] 工具列上，按一下 [**執行**] (**！**) 。</span><span class="sxs-lookup"><span data-stu-id="f36db-172">On the query designer toolbar, click **Run** (**!**).</span></span>  
  
     <span data-ttu-id="f36db-173">查詢隨即執行，並顯示 SalesDate、Subcategory、Product、Sales 和 Quantity 欄位的結果集。</span><span class="sxs-lookup"><span data-stu-id="f36db-173">The query runs and displays the result set for the fields SalesDate, Subcategory, Product, Sales, and Quantity.</span></span>  
  
     <span data-ttu-id="f36db-174">在結果集中，欄標題是依據查詢中的名稱而定。</span><span class="sxs-lookup"><span data-stu-id="f36db-174">In the result set, the column headings are based on the names in the query.</span></span> <span data-ttu-id="f36db-175">在資料集中，欄標題會變成欄位名稱，並且儲存在報表中。</span><span class="sxs-lookup"><span data-stu-id="f36db-175">In the dataset, the column headings become the field names, and are saved in the report.</span></span> <span data-ttu-id="f36db-176">完成精靈後，您可以使用 [報表資料] 窗格檢視資料集欄位的集合。</span><span class="sxs-lookup"><span data-stu-id="f36db-176">After you complete the wizard, you can use the Report Data pane to view the collection of dataset fields.</span></span>  
  
4.  <span data-ttu-id="f36db-177">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="f36db-177">Click **Next**.</span></span>  
  
##  <a name="1c-organize-data-into-groups-in-the-table-wizard"></a><a name="Groups"></a><span data-ttu-id="f36db-178">1c.</span><span class="sxs-lookup"><span data-stu-id="f36db-178">1c.</span></span> <span data-ttu-id="f36db-179">在資料表精靈中將資料組織成群組</span><span class="sxs-lookup"><span data-stu-id="f36db-179">Organize Data into Groups in the Table Wizard</span></span>  
 <span data-ttu-id="f36db-180">選取做為群組對象的欄位時，您會設計包含資料列和資料行的資料表，以顯示詳細資料和彙總資料。</span><span class="sxs-lookup"><span data-stu-id="f36db-180">When you select fields to group on, you design a table that has rows and columns that display detail data and aggregated data.</span></span>  
  
#### <a name="to-organize-data-into-groups"></a><span data-ttu-id="f36db-181">若要將資料組織為群組</span><span class="sxs-lookup"><span data-stu-id="f36db-181">To organize data into groups</span></span>  
  
1.  <span data-ttu-id="f36db-182">在 [排列欄位]\*\*\*\* 頁面上，將 [Product] 拖曳至 [值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f36db-182">On the **Arrange fields** page, drag Product to **Values**.</span></span>  
  
2.  <span data-ttu-id="f36db-183">將 [Quantity] 拖曳至 [值]\*\*\*\* 並放置在 [Product] 之下。</span><span class="sxs-lookup"><span data-stu-id="f36db-183">Drag Quantity to **Values** and place below Product.</span></span>  
  
     <span data-ttu-id="f36db-184">Sum 函數 (數值欄位的預設彙總) 會自動彙總 [Quantity]。</span><span class="sxs-lookup"><span data-stu-id="f36db-184">Quantity is automatically aggregated by the Sum function, the default aggregate for numeric fields.</span></span> <span data-ttu-id="f36db-185">值為 [Sum(Quantity)]。</span><span class="sxs-lookup"><span data-stu-id="f36db-185">The value is [Sum(Quantity)].</span></span>  
  
     <span data-ttu-id="f36db-186">您可以開啟下拉式清單，檢視其他可用的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="f36db-186">You can open the drop-down list to view the other aggregate functions available.</span></span> <span data-ttu-id="f36db-187">請不要變更彙總函式。</span><span class="sxs-lookup"><span data-stu-id="f36db-187">Do not change the aggregate function.</span></span>  
  
3.  <span data-ttu-id="f36db-188">將 [Sales] 拖曳至 [值]\*\*\*\* 並放置在 [Sum(Quantity)] 之下。</span><span class="sxs-lookup"><span data-stu-id="f36db-188">Drag Sales to **Values** and place below [Sum(Quantity)].</span></span>  
  
     <span data-ttu-id="f36db-189">[Sales] 是透過 Sum 函數彙總。</span><span class="sxs-lookup"><span data-stu-id="f36db-189">Sales is aggregated by the Sum function.</span></span> <span data-ttu-id="f36db-190">值為 [Sum(Sales)]。</span><span class="sxs-lookup"><span data-stu-id="f36db-190">The value is [Sum(Sales)].</span></span>  
  
     <span data-ttu-id="f36db-191">步驟 1、2 和 3 會指定要在資料表中顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="f36db-191">Steps 1, 2, and 3 specify the data to display in the table.</span></span>  
  
4.  <span data-ttu-id="f36db-192">將 [SalesDate] 拖曳至 [資料列群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f36db-192">Drag SalesDate to **Row groups**.</span></span>  
  
5.  <span data-ttu-id="f36db-193">將 [Subcategory] 拖曳至 [資料列群組]\*\*\*\* 並放置在 [SalesDate] 之下。</span><span class="sxs-lookup"><span data-stu-id="f36db-193">Drag Subcategory to **Row groups** and place below SalesDate.</span></span>  
  
     <span data-ttu-id="f36db-194">步驟 4 和 5 會先依日期，再依該日期的產品子類別組織欄位的值。</span><span class="sxs-lookup"><span data-stu-id="f36db-194">Steps 4 and 5 organize the values for the fields first by date, and then by product subcategory for that date.</span></span>  
  
6.  <span data-ttu-id="f36db-195">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="f36db-195">Click **Next**.</span></span>  
  
##  <a name="1d-add-subtotal-and-total-rows-in-the-table-wizard"></a><a name="Subtotals"></a><span data-ttu-id="f36db-196">1d.</span><span class="sxs-lookup"><span data-stu-id="f36db-196">1d.</span></span> <span data-ttu-id="f36db-197">在資料表精靈中加入小計和總計資料列</span><span class="sxs-lookup"><span data-stu-id="f36db-197">Add Subtotal and Total Rows in the Table Wizard</span></span>  
 <span data-ttu-id="f36db-198">建立群組之後，您可以加入並格式化要顯示欄位彙總值的資料列。</span><span class="sxs-lookup"><span data-stu-id="f36db-198">After you create groups, you can add and format rows on which to display aggregate values for the fields.</span></span> <span data-ttu-id="f36db-199">您可以選擇要顯示所有資料，或是讓使用者以互動方式展開和摺疊分組資料。</span><span class="sxs-lookup"><span data-stu-id="f36db-199">You can choose whether to show all the data or to let a user expand and collapse grouped data interactively.</span></span>  
  
#### <a name="to-add-subtotals-and-totals"></a><span data-ttu-id="f36db-200">加入小計和總計</span><span class="sxs-lookup"><span data-stu-id="f36db-200">To add subtotals and totals</span></span>  
  
1.  <span data-ttu-id="f36db-201">在 [**選擇版面**配置] 頁面的 [**選項**] 底下，確認已選取 [**顯示小計和總計**]。</span><span class="sxs-lookup"><span data-stu-id="f36db-201">On the **Choose the layout** page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
2.  <span data-ttu-id="f36db-202">驗證已選取 [區塊式，小計位於下方]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f36db-202">Verify that **Blocked, subtotal below** is selected.</span></span>  
  
     <span data-ttu-id="f36db-203">精靈的 [預覽] 窗格會顯示含有五個資料列的資料表。</span><span class="sxs-lookup"><span data-stu-id="f36db-203">The wizard Preview pane displays a table with five rows.</span></span> <span data-ttu-id="f36db-204">當您執行報表時，每個資料列都會以下列方式顯示：</span><span class="sxs-lookup"><span data-stu-id="f36db-204">When you run the report, each row will display in the following way:</span></span>  
  
    1.  <span data-ttu-id="f36db-205">第一個資料列會針對資料表重複一次，以顯示資料行標題。</span><span class="sxs-lookup"><span data-stu-id="f36db-205">The first row will repeat once for the table to show column headings.</span></span>  
  
    2.  <span data-ttu-id="f36db-206">第二個資料列會針對銷售訂單中的每一行項目重複一次，並顯示產品名稱、訂單數量和行總計。</span><span class="sxs-lookup"><span data-stu-id="f36db-206">The second row will repeat once for each line item in the sales order and display the product name, order quantity, and line total.</span></span>  
  
    3.  <span data-ttu-id="f36db-207">第三個資料列會針對每筆銷售訂單重複一次，以顯示每筆訂單的小計。</span><span class="sxs-lookup"><span data-stu-id="f36db-207">The third row will repeat once for each sales order to display subtotals per order.</span></span>  
  
    4.  <span data-ttu-id="f36db-208">第四個資料列則會針對每個訂貨日期重複一次，以顯示每天的小計。</span><span class="sxs-lookup"><span data-stu-id="f36db-208">The fourth row will repeat once for each order date to display the subtotals per day.</span></span>  
  
    5.  <span data-ttu-id="f36db-209">第五個資料列會針對資料表重複一次，以顯示總計。</span><span class="sxs-lookup"><span data-stu-id="f36db-209">The fifth row will repeat once for the table to display the grand totals.</span></span>  
  
3.  <span data-ttu-id="f36db-210">清除 [展開/摺疊群組]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="f36db-210">Clear the option **Expand/collapse groups**.</span></span> <span data-ttu-id="f36db-211">在本教學課程中，您建立的報表不會使用向下鑽研功能，此功能可讓使用者展開父群組階層，以顯示子群組資料列和詳細資料列。</span><span class="sxs-lookup"><span data-stu-id="f36db-211">In this tutorial, the report you create does not use the drilldown feature that lets a user expand a parent group hierarchy to display child group rows and detail rows.</span></span>  
  
4.  <span data-ttu-id="f36db-212">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="f36db-212">Click **Next**.</span></span>  
  
##  <a name="1e-choose-a-style-in-the-table-wizard"></a><a name="Style"></a><span data-ttu-id="f36db-213">1e.</span><span class="sxs-lookup"><span data-stu-id="f36db-213">1e.</span></span> <span data-ttu-id="f36db-214">在資料表精靈中選擇樣式</span><span class="sxs-lookup"><span data-stu-id="f36db-214">Choose a Style in the Table Wizard</span></span>  
 <span data-ttu-id="f36db-215">樣式會指定字型樣式、色彩集和框線樣式。</span><span class="sxs-lookup"><span data-stu-id="f36db-215">A style specifies a font style, a set of colors, and a border style.</span></span>  
  
#### <a name="to-specify-a-table-style"></a><span data-ttu-id="f36db-216">指定資料表樣式</span><span class="sxs-lookup"><span data-stu-id="f36db-216">To specify a table style</span></span>  
  
1.  <span data-ttu-id="f36db-217">在 [**選擇樣式**] 頁面的 [樣式] 窗格中，選取 [海洋]。</span><span class="sxs-lookup"><span data-stu-id="f36db-217">On the **Choose a Style** page, in the Styles pane, select Ocean.</span></span>  
  
     <span data-ttu-id="f36db-218">[預覽] 窗格隨即顯示採用該樣式的資料表範例。</span><span class="sxs-lookup"><span data-stu-id="f36db-218">The Preview pane displays a sample of the table with that style.</span></span>  
  
2.  <span data-ttu-id="f36db-219">或者，按一下其他樣式，查看套用這些樣式的範例。</span><span class="sxs-lookup"><span data-stu-id="f36db-219">Optionally, click the other styles to see the sample with them applied.</span></span>  
  
3.  <span data-ttu-id="f36db-220">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="f36db-220">Click **Finish**.</span></span>  
  
 <span data-ttu-id="f36db-221">資料表會加入至設計介面。</span><span class="sxs-lookup"><span data-stu-id="f36db-221">The table is added to the design surface.</span></span> <span data-ttu-id="f36db-222">這個資料表有 5 個資料行和 5 個資料列。</span><span class="sxs-lookup"><span data-stu-id="f36db-222">The table has 5 columns and 5 rows.</span></span> <span data-ttu-id="f36db-223">[資料列群組] 窗格會顯示三個資料列群組：[SalesDate]、[Subcategory] 和 [Details]。</span><span class="sxs-lookup"><span data-stu-id="f36db-223">The Row Groups pane shows three row groups: SalesDate, Subcategory, and Details.</span></span> <span data-ttu-id="f36db-224">詳細資料是資料集查詢擷取的所有資料。</span><span class="sxs-lookup"><span data-stu-id="f36db-224">Detail data is all the data that is retrieved by the dataset query.</span></span>  
  
##  <a name="2-format-data-as-currency"></a><a name="FormatCurrency"></a><span data-ttu-id="f36db-225">2. 將資料格式化為貨幣</span><span class="sxs-lookup"><span data-stu-id="f36db-225">2. Format Data as Currency</span></span>  
 <span data-ttu-id="f36db-226">根據預設，[Sales] 欄位的摘要資料會顯示一般數字。</span><span class="sxs-lookup"><span data-stu-id="f36db-226">By default, the summary data for the Sales field displays a general number.</span></span> <span data-ttu-id="f36db-227">格式化該欄位，將數字顯示為貨幣。</span><span class="sxs-lookup"><span data-stu-id="f36db-227">Format it to display the number as currency.</span></span> <span data-ttu-id="f36db-228">切換 [預留位置樣式]\*\*\*\*，將格式化的文字方塊和預留位置文字顯示為範例值。</span><span class="sxs-lookup"><span data-stu-id="f36db-228">Toggle **Placeholder Styles** to display formatted text boxes and placeholder text as sample values.</span></span>  
  
#### <a name="to-format-a-currency-field"></a><span data-ttu-id="f36db-229">格式化貨幣欄位</span><span class="sxs-lookup"><span data-stu-id="f36db-229">To format a currency field</span></span>  
  
1.  <span data-ttu-id="f36db-230">按一下 [**設計**]，切換至設計檢視。</span><span class="sxs-lookup"><span data-stu-id="f36db-230">Click **Design** to switch to design view.</span></span>  
  
2.  <span data-ttu-id="f36db-231">在 [Sales] 資料行中，按一下第二列的資料格 (位於欄標題資料列底下)，然後向下拖曳以選取包含 `[Sum(Sales)]`的所有資料格。</span><span class="sxs-lookup"><span data-stu-id="f36db-231">Click the cell in the second row (under the column headings row) in the Sales column and drag down to select all cells that contain `[Sum(Sales)]`.</span></span>  
  
3.  <span data-ttu-id="f36db-232">在 [主資料夾]\*\*\*\* 索引標籤的 [數字]\*\*\*\* 群組中，按一下 [貨幣]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f36db-232">On the **Home** tab, in the **Number** group, click the **Currency** button.</span></span> <span data-ttu-id="f36db-233">這些資料格就會變更為顯示格式化貨幣。</span><span class="sxs-lookup"><span data-stu-id="f36db-233">The cells change to show the formatted currency.</span></span>  
  
     <span data-ttu-id="f36db-234">如果您的地區設定為 [英文 (美國)]，則預設範例文字會是 [**$12,345.00**]。</span><span class="sxs-lookup"><span data-stu-id="f36db-234">If your regional setting is English (United States), the default sample text is [**$12,345.00**].</span></span> <span data-ttu-id="f36db-235">如果您看不到範例貨幣值，請按一下 [**數位**] 群組中的 [**預留位置樣式**]，然後按一下 [**範例值**]。</span><span class="sxs-lookup"><span data-stu-id="f36db-235">If you do not see an example currency value, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
4.  <span data-ttu-id="f36db-236">按一下 [執行]\*\*\*\* 以預覽報表。</span><span class="sxs-lookup"><span data-stu-id="f36db-236">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="f36db-237">[Sales] 的摘要值會顯示為貨幣。</span><span class="sxs-lookup"><span data-stu-id="f36db-237">The summary values for Sales display as currency.</span></span>  
  
##  <a name="3-format-data-as-date"></a><a name="FormatDate"></a><span data-ttu-id="f36db-238">3. 將資料格式化為日期</span><span class="sxs-lookup"><span data-stu-id="f36db-238">3. Format Data as Date</span></span>  
 <span data-ttu-id="f36db-239">根據預設，[SalesDate] 欄位會同時顯示日期和時間資訊。</span><span class="sxs-lookup"><span data-stu-id="f36db-239">By default, the SalesDate field displays both date and time information.</span></span> <span data-ttu-id="f36db-240">您可以將該欄位格式化，以便只顯示日期。</span><span class="sxs-lookup"><span data-stu-id="f36db-240">You can format them to display only the date.</span></span>  
  
#### <a name="to-format-a-date-field-as-the-default-format"></a><span data-ttu-id="f36db-241">將日期欄位格式化成預設格式</span><span class="sxs-lookup"><span data-stu-id="f36db-241">To format a date field as the default format</span></span>  
  
1.  <span data-ttu-id="f36db-242">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="f36db-242">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="f36db-243">按一下包含 `[SalesDate]`的資料格。</span><span class="sxs-lookup"><span data-stu-id="f36db-243">Click the cell that contains `[SalesDate]`.</span></span>  
  
3.  <span data-ttu-id="f36db-244">在功能區的 [**首頁**] 索引標籤上，從 [**數位**] 群組的下拉式清單中，選取 [**日期**]。</span><span class="sxs-lookup"><span data-stu-id="f36db-244">On the Ribbon, on the **Home** tab, in the **Number** group, from the drop-down list, select **Date**.</span></span>  
  
     <span data-ttu-id="f36db-245">資料格會顯示範例日期 **[1/31/2000]**。</span><span class="sxs-lookup"><span data-stu-id="f36db-245">The cell displays the example date **[1/31/2000]**.</span></span> <span data-ttu-id="f36db-246">如果您看不到範例日期，請按一下 [數字]\*\*\*\* 群組中的 [預留位置樣式]\*\*\*\*，然後按一下 [範例值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f36db-246">If you do not see an example date, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
4.  <span data-ttu-id="f36db-247">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="f36db-247">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="f36db-248">SalesDate 值會以預設的日期格式顯示。</span><span class="sxs-lookup"><span data-stu-id="f36db-248">The SalesDate values display in the default date format.</span></span>  
  
#### <a name="to-change-the-date-format-to-a-custom-format"></a><span data-ttu-id="f36db-249">若要將日期格式變更為自訂格式</span><span class="sxs-lookup"><span data-stu-id="f36db-249">To change the date format to a custom format</span></span>  
  
1.  <span data-ttu-id="f36db-250">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="f36db-250">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="f36db-251">按一下包含 `[SalesDate]`的資料格。</span><span class="sxs-lookup"><span data-stu-id="f36db-251">Click the cell that contains `[SalesDate]`.</span></span>  
  
3.  <span data-ttu-id="f36db-252">在 [**首頁**] 索引標籤的 [**數位**] 群組中，按一下 [對話方塊啟動器]。</span><span class="sxs-lookup"><span data-stu-id="f36db-252">On the **Home** tab, in the **Number** group, click the dialog box launcher.</span></span>  
  
     <span data-ttu-id="f36db-253">啟動器是群組右邊角落的小箭頭。</span><span class="sxs-lookup"><span data-stu-id="f36db-253">The launcher is the small arrow in the right-hand corner of the group.</span></span> <span data-ttu-id="f36db-254">[文字方塊屬性]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="f36db-254">The **Text Box Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="f36db-255">在 [類別目錄] 窗格中，驗證已選取 [日期]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f36db-255">In the Category pane, verify that **Date** is selected.</span></span>  
  
5.  <span data-ttu-id="f36db-256">在 [類型]\*\*\*\* 窗格中，選取 [January 31, 2000]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f36db-256">In the **Type** pane, select **January 31, 2000**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="f36db-257">資料格就會顯示範例日期 **[January 31, 2000]**。</span><span class="sxs-lookup"><span data-stu-id="f36db-257">The cell displays the example date **[January 31, 2000]**.</span></span>  
  
7.  <span data-ttu-id="f36db-258">按一下 [執行]\*\*\*\* 以預覽報表。</span><span class="sxs-lookup"><span data-stu-id="f36db-258">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="f36db-259">SalesDate 值會使用月份的名稱，而不是月份的數字顯示。</span><span class="sxs-lookup"><span data-stu-id="f36db-259">The SalesDate value displays with the name of the month instead of the number for the month.</span></span>  
  
##  <a name="4-change-column-widths"></a><a name="Width"></a><span data-ttu-id="f36db-260">4. 變更資料行寬度</span><span class="sxs-lookup"><span data-stu-id="f36db-260">4. Change Column Widths</span></span>  
 <span data-ttu-id="f36db-261">根據預設，資料表中的每個資料格都會包含一個文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f36db-261">By default, each cell in a table contains a text box.</span></span> <span data-ttu-id="f36db-262">頁面轉譯時，文字方塊會垂直展開以容納文字。</span><span class="sxs-lookup"><span data-stu-id="f36db-262">A text box expands vertically to accommodate text when the page is rendered.</span></span> <span data-ttu-id="f36db-263">在轉譯的報表中，每一個資料列都會依照資料列中最高的轉譯文字方塊高度展開。</span><span class="sxs-lookup"><span data-stu-id="f36db-263">In the rendered report, each row expands to the height of the tallest rendered text box in the row.</span></span> <span data-ttu-id="f36db-264">設計介面上資料列的高度對於轉譯報表中資料列的高度並無影響。</span><span class="sxs-lookup"><span data-stu-id="f36db-264">The height of the row on the design surface has no affect on the height of the row in the rendered report.</span></span>  
  
 <span data-ttu-id="f36db-265">若要減少每個資料列佔用的垂直空間數量，請展開資料行寬度以容納一行上資料行中預期的文字方塊內容。</span><span class="sxs-lookup"><span data-stu-id="f36db-265">To reduce the amount of vertical space each row takes, expand the column width to accommodate the expected contents of the text boxes in the column on one line.</span></span>  
  
#### <a name="to-change-the-width-of-table-columns"></a><span data-ttu-id="f36db-266">變更資料表資料行的寬度</span><span class="sxs-lookup"><span data-stu-id="f36db-266">To change the width of table columns</span></span>  
  
1.  <span data-ttu-id="f36db-267">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="f36db-267">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="f36db-268">按一下資料表，使資料行和資料列控點出現在資料表的上面和旁邊。</span><span class="sxs-lookup"><span data-stu-id="f36db-268">Click the table so that column and row handles appear above and next to the table.</span></span>  
  
     <span data-ttu-id="f36db-269">沿著資料表頂端和側邊的灰色長條是資料行和資料列控點。</span><span class="sxs-lookup"><span data-stu-id="f36db-269">The gray bars along the top and side of the table are the column and row handles.</span></span>  
  
3.  <span data-ttu-id="f36db-270">指向資料行控點之間的線條，使游標變成雙箭頭。</span><span class="sxs-lookup"><span data-stu-id="f36db-270">Point to the line between column handles so that the cursor changes into a double arrow.</span></span> <span data-ttu-id="f36db-271">將資料行拖曳到所需的大小。</span><span class="sxs-lookup"><span data-stu-id="f36db-271">Drag the columns to the size you want.</span></span> <span data-ttu-id="f36db-272">例如，您可以展開產品的資料行，以便在同一行顯示產品名稱。</span><span class="sxs-lookup"><span data-stu-id="f36db-272">For example, expand the column for Product so that the product name displays on one line.</span></span>  
  
4.  <span data-ttu-id="f36db-273">按一下 [執行]\*\*\*\* 以預覽報表。</span><span class="sxs-lookup"><span data-stu-id="f36db-273">Click **Run** to preview your report.</span></span>  
  
##  <a name="5-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="f36db-274">5. 加入報表標題</span><span class="sxs-lookup"><span data-stu-id="f36db-274">5. Add a Report Title</span></span>  
 <span data-ttu-id="f36db-275">報表標題會出現在報表的頂端。</span><span class="sxs-lookup"><span data-stu-id="f36db-275">A report title appears at the top of the report.</span></span> <span data-ttu-id="f36db-276">您可以將報表標題放置在報表頁首，如果報表不使用報表頁首，則可以放置在報表主體頂端的文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="f36db-276">You can place the report title in a report header or if the report does not use one, in a text box at the top of the report body.</span></span> <span data-ttu-id="f36db-277">在本教學課程中，您將使用自動放置在報表主體頂端的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f36db-277">In this tutorial, you will use the text box that is automatically placed at the top of the report body.</span></span>  
  
 <span data-ttu-id="f36db-278">您可以將不同的字型樣式、大小和色彩套用到文字的片語和個別字元，進一步加強文字。</span><span class="sxs-lookup"><span data-stu-id="f36db-278">The text can be further enhanced by applying different font styles, sizes, and colors to phrases and individual characters of the text.</span></span> <span data-ttu-id="f36db-279">如需詳細資訊，請參閱[在文字方塊中將文字格式化 &#40;報表產生器及 SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f36db-279">For more information, see [Format Text in a Text Box &#40;Report Builder and SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="f36db-280">若要加入報表標題</span><span class="sxs-lookup"><span data-stu-id="f36db-280">To add a report title</span></span>  
  
1.  <span data-ttu-id="f36db-281">在設計介面上，按一下 **[按一下以加入標題]**。</span><span class="sxs-lookup"><span data-stu-id="f36db-281">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="f36db-282">輸入 **Product Sales**，然後按一下文字方塊外部。</span><span class="sxs-lookup"><span data-stu-id="f36db-282">Type **Product Sales**, and then click outside the text box.</span></span>  
  
3.  <span data-ttu-id="f36db-283">以滑鼠右鍵按一下包含 [Product Sales]\*\*\*\* 的文字方塊，然後按一下 [文字方塊屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f36db-283">Right-click the text box that contains **Product Sales** and click **Text Box Properties**.</span></span>  
  
4.  <span data-ttu-id="f36db-284">在 [文字方塊屬性]\*\*\*\* 對話方塊中，按一下 [字型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f36db-284">In the **Text Box Properties** dialog box, click **Font**.</span></span>  
  
5.  <span data-ttu-id="f36db-285">在 [大小]\*\*\*\* 清單中，選取 [18pt]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f36db-285">In the **Size** list, select **18pt**.</span></span>  
  
6.  <span data-ttu-id="f36db-286">在 [色彩]\*\*\*\* 清單中，選取 [矢菊花藍]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f36db-286">In the **Color** list, select **Cornflower Blue**.</span></span>  
  
7.  <span data-ttu-id="f36db-287">選取 [粗體]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f36db-287">Select **Bold**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="6-save-the-report"></a><a name="Save"></a><span data-ttu-id="f36db-288">6. 儲存報表</span><span class="sxs-lookup"><span data-stu-id="f36db-288">6. Save the Report</span></span>  
 <span data-ttu-id="f36db-289">將報表儲存至報表伺服器或您的電腦。</span><span class="sxs-lookup"><span data-stu-id="f36db-289">Save the report to a report server or your computer.</span></span> <span data-ttu-id="f36db-290">如果沒有將報表儲存到報表伺服器，就無法使用數個 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能，例如報表組件和子報表。</span><span class="sxs-lookup"><span data-stu-id="f36db-290">If you do not save the report to the report server, a number of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features such as report parts and subreports are not available.</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="f36db-291">若要將報表儲存在報表伺服器上</span><span class="sxs-lookup"><span data-stu-id="f36db-291">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="f36db-292">在 **[報表產生器]** 按鈕中，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="f36db-292">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="f36db-293">按一下 **[最近使用的網站和伺服器]**。</span><span class="sxs-lookup"><span data-stu-id="f36db-293">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="f36db-294">選取或輸入您有權儲存報表之報表伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="f36db-294">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="f36db-295">「正在連接到報表伺服器」訊息隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="f36db-295">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="f36db-296">連接完成時，您就會看見報表伺服器管理員指定為預設報表位置之報表資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="f36db-296">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>  
  
4.  <span data-ttu-id="f36db-297">將 [名稱]\*\*\*\* 中的預設名稱取代為 **Product Sales**。</span><span class="sxs-lookup"><span data-stu-id="f36db-297">In **Name**, replace the default name with **Product Sales**.</span></span>  
  
5.  <span data-ttu-id="f36db-298">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="f36db-298">Click **Save**.</span></span>  
  
 <span data-ttu-id="f36db-299">報表就會儲存至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="f36db-299">The report is saved to the report server.</span></span> <span data-ttu-id="f36db-300">您連接之報表伺服器的名稱會顯示在視窗底部的狀態列中。</span><span class="sxs-lookup"><span data-stu-id="f36db-300">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="f36db-301">將報表儲存到您的電腦上</span><span class="sxs-lookup"><span data-stu-id="f36db-301">To save the report on your computer</span></span>  
  
1.  <span data-ttu-id="f36db-302">在 **[報表產生器]** 按鈕中，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="f36db-302">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="f36db-303">按一下 [桌面]\*\*\*\*、[我的文件]\*\*\*\* 或 [我的電腦]\*\*\*\*，然後瀏覽到您要儲存報表的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f36db-303">Click **Desktop**, **My Documents**, or **My computer**, and browse to the folder where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="f36db-304">將 [名稱]\*\*\*\* 中的預設名稱取代為 **Product Sales**。</span><span class="sxs-lookup"><span data-stu-id="f36db-304">In **Name**, replace the default name with **Product Sales**.</span></span>  
  
4.  <span data-ttu-id="f36db-305">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="f36db-305">Click **Save**.</span></span>  
  
##  <a name="7-export-the-report"></a><a name="Export"></a><span data-ttu-id="f36db-306">7. 匯出報表</span><span class="sxs-lookup"><span data-stu-id="f36db-306">7. Export the Report</span></span>  
 <span data-ttu-id="f36db-307">報表可匯出為不同的格式，例如 Microsoft Excel 和逗號分隔值 (CSV)。</span><span class="sxs-lookup"><span data-stu-id="f36db-307">Reports can be exported to different formats such Microsoft Excel and comma separated value (CSV).</span></span> <span data-ttu-id="f36db-308">如需詳細資訊，請參閱[匯出報表 &#40;報表產生器和 SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f36db-308">For more information, see [Exporting Reports &#40;Report Builder and SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="f36db-309">在本教學課程中，您會將報表匯出到 Excel，並且設定報表上的屬性，為活頁簿索引標籤提供自訂名稱。</span><span class="sxs-lookup"><span data-stu-id="f36db-309">In this tutorial, you will export the report to Excel and set a property on the report to provide a custom name for the workbook tab.</span></span>  
  
#### <a name="to-specify-the-workbook-tab-name"></a><span data-ttu-id="f36db-310">指定活頁簿索引標籤名稱</span><span class="sxs-lookup"><span data-stu-id="f36db-310">To specify the workbook tab name</span></span>  
  
1.  <span data-ttu-id="f36db-311">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="f36db-311">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="f36db-312">按一下報表外的任何位置。</span><span class="sxs-lookup"><span data-stu-id="f36db-312">Click anywhere outside the report.</span></span>  
  
3.  <span data-ttu-id="f36db-313">.在 [屬性] 窗格中，找出 [InitialPageName] 屬性，然後輸入**Product Sales Excel**。</span><span class="sxs-lookup"><span data-stu-id="f36db-313">.In the Properties pane, locate the InitialPageName property and type **Product Sales Excel**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f36db-314">如果看不到 [屬性] 窗格，請按一下功能區上的 [視圖] 索引標籤，然後按一下 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="f36db-314">If the Properties pane is not visible, click the View tab on the ribbon, and then click **Properties**.</span></span>  
  
#### <a name="to-export-a-report-to-excel"></a><span data-ttu-id="f36db-315">將報表匯出到 Excel</span><span class="sxs-lookup"><span data-stu-id="f36db-315">To export a report to Excel</span></span>  
  
1.  <span data-ttu-id="f36db-316">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="f36db-316">Click **Run** to preview the report.</span></span>  
  
2.  <span data-ttu-id="f36db-317">.在功能區上，按一下 [**匯出**]，然後按一下 [ **Excel**]。</span><span class="sxs-lookup"><span data-stu-id="f36db-317">.On the ribbon, click **Export**, and then click **Excel**.</span></span>  
  
     <span data-ttu-id="f36db-318">[另存新檔]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="f36db-318">The **Save As** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="f36db-319">流覽至 [**檔**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f36db-319">Browse to the **Documents** folder.</span></span>  
  
4.  <span data-ttu-id="f36db-320">在 [**檔案名**] 文字方塊中，輸入**Product Sales Excel**。</span><span class="sxs-lookup"><span data-stu-id="f36db-320">In the **File name** text box, type **Product Sales Excel**.</span></span>  
  
5.  <span data-ttu-id="f36db-321">確認檔案類型為 [ **Excel 活頁簿**]。</span><span class="sxs-lookup"><span data-stu-id="f36db-321">Verify that the file type is **Excel Workbook**.</span></span>  
  
6.  <span data-ttu-id="f36db-322">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="f36db-322">Click **Save**.</span></span>  
  
#### <a name="to-view-the-report-in-excel"></a><span data-ttu-id="f36db-323">若要在 Excel 中檢視報表</span><span class="sxs-lookup"><span data-stu-id="f36db-323">To view the report in Excel</span></span>  
  
1.  <span data-ttu-id="f36db-324">開啟 [**檔**] 資料夾，然後按兩下 [**產品銷售 Excel.xlsx**]。</span><span class="sxs-lookup"><span data-stu-id="f36db-324">Open the **Documents** folder and double click **Product Sales Excel.xlsx**.</span></span>  
  
2.  <span data-ttu-id="f36db-325">確認活頁簿索引標籤的名稱是 **Product Sales Excel**。</span><span class="sxs-lookup"><span data-stu-id="f36db-325">Verify that the name of the workbook tab is **Product Sales Excel**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f36db-326">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f36db-326">Next Steps</span></span>  
 <span data-ttu-id="f36db-327">以上總結如何建立基本資料表報表的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="f36db-327">This concludes the walkthrough for how to create a basic table report.</span></span> <span data-ttu-id="f36db-328">如需資料表的詳細資訊，請參閱[資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f36db-328">For more information about tables, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f36db-329">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f36db-329">See Also</span></span>  
 <span data-ttu-id="f36db-330">[教學課程 &#40;報表產生器&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="f36db-330">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="f36db-331">SQL Server 2014 中的報表產生器</span><span class="sxs-lookup"><span data-stu-id="f36db-331">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
