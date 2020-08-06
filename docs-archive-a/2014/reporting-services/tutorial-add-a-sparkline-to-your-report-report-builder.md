---
title: 教學課程：將走勢圖新增至報表 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 18c90a36-48bf-4805-a960-2d1e8f00c2dc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fb1bf83810b6c743b977e399864ce2edd514f572
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704778"
---
# <a name="tutorial-add-a-sparkline-to-your-report-report-builder"></a><span data-ttu-id="1ab56-102">教學課程：將走勢圖加入至報表 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="1ab56-102">Tutorial: Add a Sparkline to Your Report (Report Builder)</span></span>
  <span data-ttu-id="1ab56-103">在本教學課程中，您要根據範例銷售資料建立基本資料表報表，然後將走勢圖加入至資料表中的儲存格。</span><span class="sxs-lookup"><span data-stu-id="1ab56-103">In this tutorial, you create a basic table report based on sample sales data, and then add a sparkline chart to a cell in the table.</span></span>  
  
 <span data-ttu-id="1ab56-104">本教學課程所建立的報表另有一個增強型版本，可從範例 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 報表產生器報表取得。</span><span class="sxs-lookup"><span data-stu-id="1ab56-104">An enhanced version of the report you create in this tutorial is available as a sample [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Report Builder report.</span></span> <span data-ttu-id="1ab56-105">如需下載此範例報表及其他專案的詳細資訊，請參閱[報表產生器範例報表](https://go.microsoft.com/fwlink/?LinkId=184851)。</span><span class="sxs-lookup"><span data-stu-id="1ab56-105">For more information about downloading this sample report and others, see [Report Builder sample reports](https://go.microsoft.com/fwlink/?LinkId=184851).</span></span> <span data-ttu-id="1ab56-106">下圖顯示與您將要建立的報表相似的範例報表。</span><span class="sxs-lookup"><span data-stu-id="1ab56-106">The following illustration shows the sample report similar to the one that you will create.</span></span>  
  
 <span data-ttu-id="1ab56-107">![rs_SparklineMatrixTutorial](../../2014/tutorials/media/rs-sparklinematrixtutorial.gif "rs_SparklineMatrixTutorial")</span><span class="sxs-lookup"><span data-stu-id="1ab56-107">![rs_SparklineMatrixTutorial](../../2014/tutorials/media/rs-sparklinematrixtutorial.gif "rs_SparklineMatrixTutorial")</span></span>  
  
 <span data-ttu-id="1ab56-108">影片 how [to：在資料表中建立走勢圖 (報表產生器 video) ](https://technet.microsoft.com/bi/ff871942.aspx)說明如何建立包含走勢圖的類似報表。</span><span class="sxs-lookup"><span data-stu-id="1ab56-108">The video [How to: Create a Sparkline in a Table (Report Builder Video)](https://technet.microsoft.com/bi/ff871942.aspx) illustrates how to create a similar report with sparklines.</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="1ab56-109">您將瞭解的內容</span><span class="sxs-lookup"><span data-stu-id="1ab56-109">What You Will Learn</span></span>  
 <span data-ttu-id="1ab56-110">在本教學課程中，您將學習如何執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="1ab56-110">In this tutorial, you will learn how to do the following:</span></span>  
  
 1. [<span data-ttu-id="1ab56-111">建立含資料表的報表</span><span class="sxs-lookup"><span data-stu-id="1ab56-111">Create a Report with a Table</span></span>](#CreateTable)  
  
 2. [<span data-ttu-id="1ab56-112">在資料表或矩陣精靈中建立查詢</span><span class="sxs-lookup"><span data-stu-id="1ab56-112">Create a Query in the Table or Matrix Wizard</span></span>](#Query)  
  
 3. [<span data-ttu-id="1ab56-113">將走勢圖加入至資料表</span><span class="sxs-lookup"><span data-stu-id="1ab56-113">Add a Sparkline to the Table</span></span>](#Sparkline)  
  
 4. [<span data-ttu-id="1ab56-114">垂直與水平對齊走勢圖</span><span class="sxs-lookup"><span data-stu-id="1ab56-114">Align the Sparklines Vertically and Horizontally</span></span>](#AlignSparklines)  
  
### <a name="other-optional-steps"></a><span data-ttu-id="1ab56-115">其他選擇性步驟</span><span class="sxs-lookup"><span data-stu-id="1ab56-115">Other Optional Steps</span></span>  
 5. [<span data-ttu-id="1ab56-116">將資料格式化為貨幣</span><span class="sxs-lookup"><span data-stu-id="1ab56-116">Format Data as Currency</span></span>](#FormatCurrency)  
  
 6. [<span data-ttu-id="1ab56-117">將資料格式化為日期</span><span class="sxs-lookup"><span data-stu-id="1ab56-117">Format Data as Dates</span></span>](#FormatDates)  
  
 7. [<span data-ttu-id="1ab56-118">變更資料行寬度</span><span class="sxs-lookup"><span data-stu-id="1ab56-118">Change Column Widths</span></span>](#Width)  
  
 8. [<span data-ttu-id="1ab56-119">加入報表標題</span><span class="sxs-lookup"><span data-stu-id="1ab56-119">Add a Report Title</span></span>](#Title)  
  
 9. [<span data-ttu-id="1ab56-120">儲存報表</span><span class="sxs-lookup"><span data-stu-id="1ab56-120">Save the Report</span></span>](#Save)  
  
 <span data-ttu-id="1ab56-121">完成本教學課程的估計時間：30 分鐘。</span><span class="sxs-lookup"><span data-stu-id="1ab56-121">Estimated time to complete this tutorial: 30 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ab56-122">需求</span><span class="sxs-lookup"><span data-stu-id="1ab56-122">Requirements</span></span>  
 <span data-ttu-id="1ab56-123">如需需求的詳細資訊，請參閱[教學課程的必要條件 &#40;報表產生器&#41;](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="1ab56-123">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-report-with-a-table"></a><a name="CreateTable"></a><span data-ttu-id="1ab56-124">1. 建立含資料表的報表</span><span class="sxs-lookup"><span data-stu-id="1ab56-124">1. Create a Report with a Table</span></span>  
  
#### <a name="to-create-a-report"></a><span data-ttu-id="1ab56-125">建立報表</span><span class="sxs-lookup"><span data-stu-id="1ab56-125">To create a report</span></span>  
  
1.  <span data-ttu-id="1ab56-126">按一下 **[開始]**、依序指向 **[程式集]** 和 **[Microsoft SQL Server 2012 報表產生器]**，然後按一下 **[報表產生器]**。</span><span class="sxs-lookup"><span data-stu-id="1ab56-126">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="1ab56-127">**[使用者入門]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="1ab56-127">The **Getting Started** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1ab56-128"> 如果 **[使用者入門]** 對話方塊沒有出現，請在 **[報表產生器]** 按鈕中按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="1ab56-128">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
2.  <span data-ttu-id="1ab56-129">在左窗格中，確認已選取 **[新增報表]** 。</span><span class="sxs-lookup"><span data-stu-id="1ab56-129">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="1ab56-130">在右窗格中，按一下 **[資料表或矩陣精靈]**。</span><span class="sxs-lookup"><span data-stu-id="1ab56-130">In the right pane, click **Table or Matrix Wizard**.</span></span>  
  
4.  <span data-ttu-id="1ab56-131">在 **[選擇資料集]** 頁面上，選取 **[建立資料集]**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="1ab56-131">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span> <span data-ttu-id="1ab56-132">**[選擇與資料來源的連接]** 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="1ab56-132">The **Choose a connection to a data source** page opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1ab56-133">本教學課程無須任何特定資料，您只需要連接到 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="1ab56-133">This tutorial does not need specific data; it just needs a connection to a [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database.</span></span> <span data-ttu-id="1ab56-134">如果您已有資料來源連接列於 [資料來源連接]\*\*\*\* 底下，就可以選取該連接並移至步驟 10。</span><span class="sxs-lookup"><span data-stu-id="1ab56-134">If you already have a data source connection listed under **Data Source Connections**, you can select it and go to step 10.</span></span> <span data-ttu-id="1ab56-135">如需詳細資訊，請參閱[取得資料連線的替代方式 &#40;報表產生器&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="1ab56-135">For more information, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
5.  <span data-ttu-id="1ab56-136">按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="1ab56-136">Click **New**.</span></span> <span data-ttu-id="1ab56-137">**[資料來源屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="1ab56-137">The **Data Source Properties** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="1ab56-138">在 [名稱]\*\*\*\* 中鍵入 **Product Sales** 作為資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="1ab56-138">In **Name**, type **Product Sales**, a name for the data source.</span></span>  
  
7.  <span data-ttu-id="1ab56-139">在 [選取連線類型]\*\*\*\* 中，驗證已選取 [Microsoft SQL Server]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ab56-139">In **Select a connection type**, verify that **Microsoft SQL Server** is selected.</span></span>  
  
8.  <span data-ttu-id="1ab56-140">在 [連接字串]\*\*\*\* 中，鍵入下列文字：</span><span class="sxs-lookup"><span data-stu-id="1ab56-140">In **Connection string**, type the following text:</span></span>  
  
     <span data-ttu-id="1ab56-141">**資料來源 =\<servername>**</span><span class="sxs-lookup"><span data-stu-id="1ab56-141">**Data Source=\<servername>**</span></span>  
  
     <span data-ttu-id="1ab56-142">\<servername>運算式 (例如 Report001) 會指定已安裝 SQL Server Database Engine 執行個體的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="1ab56-142">The expression \<servername>, for example Report001, specifies a computer on which an instance of the SQL Server Database Engine is installed.</span></span> <span data-ttu-id="1ab56-143">由於報表資料不是擷取自 SQL Server 資料庫，您不必加上資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="1ab56-143">Because the report data is not extracted from a SQL Server database, you need not include the name of a database.</span></span> <span data-ttu-id="1ab56-144">指定之伺服器上的預設資料庫將用來剖析查詢。</span><span class="sxs-lookup"><span data-stu-id="1ab56-144">The default database on the specified server is used to parse the query.</span></span>  
  
9. <span data-ttu-id="1ab56-145">按一下 **[認證]**。</span><span class="sxs-lookup"><span data-stu-id="1ab56-145">Click **Credentials**.</span></span> <span data-ttu-id="1ab56-146">輸入您存取外部資料來源所需的認證。</span><span class="sxs-lookup"><span data-stu-id="1ab56-146">Enter the credentials that you need to access the external data source.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="1ab56-147">您會回到 [選擇與資料來源的連線]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="1ab56-147">You are back on the **Choose a connection to a data source** page.</span></span>  
  
11. <span data-ttu-id="1ab56-148">若要確認您能夠連接至資料來源，請按一下 **[測試連接]**。</span><span class="sxs-lookup"><span data-stu-id="1ab56-148">To verify that you can connect to the data source, click **Test Connection**.</span></span>  
  
     <span data-ttu-id="1ab56-149">「成功建立連接」訊息就會出現。</span><span class="sxs-lookup"><span data-stu-id="1ab56-149">The message "Connection created successfully" appears.</span></span>  
  
12. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
13. <span data-ttu-id="1ab56-150">按 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="1ab56-150">Click **Next**.</span></span>  
  
##  <a name="2-create-a-query-in-the-table-wizard"></a><a name="Query"></a><span data-ttu-id="1ab56-151">2. 在資料表 Wizard 中建立查詢</span><span class="sxs-lookup"><span data-stu-id="1ab56-151">2. Create a Query in the Table Wizard</span></span>  
 <span data-ttu-id="1ab56-152">在報表中，您可以使用擁有預先定義查詢的共用資料集，或是建立只在報表中使用的內嵌資料集。</span><span class="sxs-lookup"><span data-stu-id="1ab56-152">In a report, you can use a shared dataset that has a predefined query, or you can create an embedded dataset for use only in your report.</span></span> <span data-ttu-id="1ab56-153">在本教學課程中，您將建立內嵌資料集。</span><span class="sxs-lookup"><span data-stu-id="1ab56-153">In this tutorial, you will create an embedded dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ab56-154">在本教學課程中，查詢會包含資料值，因此不需要外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="1ab56-154">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="1ab56-155">這樣會使查詢相當冗長。</span><span class="sxs-lookup"><span data-stu-id="1ab56-155">This makes the query quite long.</span></span> <span data-ttu-id="1ab56-156">在商業環境中，查詢不會包含資料。</span><span class="sxs-lookup"><span data-stu-id="1ab56-156">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="1ab56-157">這僅供教學之用。</span><span class="sxs-lookup"><span data-stu-id="1ab56-157">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-query"></a><span data-ttu-id="1ab56-158">建立查詢</span><span class="sxs-lookup"><span data-stu-id="1ab56-158">To create a query</span></span>  
  
1.  <span data-ttu-id="1ab56-159">[設計查詢]\*\*\*\* 頁面上會開啟關聯式查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="1ab56-159">On the **Design a query** page, the relational query designer is open.</span></span> <span data-ttu-id="1ab56-160">在這個教學課程中，您將使用以文字為基礎的查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="1ab56-160">For this tutorial, you will use the text-based query designer.</span></span>  
  
2.  <span data-ttu-id="1ab56-161">按一下 [當成**文字編輯**]。</span><span class="sxs-lookup"><span data-stu-id="1ab56-161">Click **Edit As Text**.</span></span> <span data-ttu-id="1ab56-162">以文字為基礎的查詢設計工具會顯示查詢窗格和結果窗格。</span><span class="sxs-lookup"><span data-stu-id="1ab56-162">The text-based query designer displays a query pane and a results pane.</span></span>  
  
3.  <span data-ttu-id="1ab56-163">將下列 [!INCLUDE[tsql](../includes/tsql-md.md)] 查詢貼入 [查詢]\*\*\*\* 方塊。</span><span class="sxs-lookup"><span data-stu-id="1ab56-163">Paste the following [!INCLUDE[tsql](../includes/tsql-md.md)] query into the **Query** box.</span></span>  
  
    ```  
    SELECT CAST('2010-01-04' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2010-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Carrying Case' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2010-01-10' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Carrying Case' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2010-01-04' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Budget Movie-Maker' as Product, CAST(1056.00 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2010-01-05' AS date) as SalesDate,  'Accessories' as Subcategory,  
       'Slim Digital' as Product, CAST(1380.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2010-01-05' AS date) as SalesDate,'Accessories' as Subcategory,    
       'Budget Movie-Maker' as Product, CAST(780.00 AS money) AS Sales, 26 as Quantity  
    UNION SELECT CAST('2010-01-07' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(3798.00 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2010-01-08' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(10400.00 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2010-01-09' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(3000.00 AS money) AS Sales, 60 as Quantity  
    UNION SELECT CAST('2010-01-10' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(7234.50 AS money) AS Sales, 39 as Quantity  
    UNION SELECT CAST('2010-01-06' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Carrying Case' as Product, CAST(10836.00 AS money) AS Sales, 84 as Quantity  
    UNION SELECT CAST('2010-01-07' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Slim Digital' as Product, CAST(2550.00 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2010-01-04' AS date) as SalesDate, 'Digital' as Subcategory,   
       'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2010-01-08' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'Slim Digital' as Product, CAST(18530.00 AS money) AS Sales, 34 as Quantity  
    UNION SELECT CAST('2010-01-06' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'Slim Digital' as Product, CAST(26576.00 AS money) AS Sales, 88 as Quantity  
    ```  
  
4.  <span data-ttu-id="1ab56-164">在 [查詢設計工具] 工具列上，按一下 [執行] (**！**) 。</span><span class="sxs-lookup"><span data-stu-id="1ab56-164">On the query designer toolbar, click Run  (**!**).</span></span>  
  
     <span data-ttu-id="1ab56-165">查詢隨即執行，並顯示 **SalesDate**、 **Subcategory**、 **Product**、 **Sales**和 **Quantity**欄位的結果集。</span><span class="sxs-lookup"><span data-stu-id="1ab56-165">The query runs and displays the result set for the fields **SalesDate**, **Subcategory**, **Product**, **Sales**, and **Quantity**.</span></span>  
  
5.  <span data-ttu-id="1ab56-166">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="1ab56-166">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="1ab56-167">在 [排列欄位]\*\*\*\* 頁面上，將 [Sales]\*\*\*\* 拖曳至 [值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ab56-167">On the **Arrange fields** page, drag **Sales** to **Values**.</span></span>  
  
     <span data-ttu-id="1ab56-168">**Sales** 是透過 Sum 函數彙總。</span><span class="sxs-lookup"><span data-stu-id="1ab56-168">**Sales** is aggregated by the Sum function.</span></span> <span data-ttu-id="1ab56-169">值為 [Sum(Sales)]。</span><span class="sxs-lookup"><span data-stu-id="1ab56-169">The value is [Sum(Sales)].</span></span>  
  
7.  <span data-ttu-id="1ab56-170">將 [Product]\*\*\*\* 拖曳至 [資料列群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ab56-170">Drag **Product** to **Row groups**.</span></span>  
  
8.  <span data-ttu-id="1ab56-171">將 [SalesDate]\*\*\*\* 拖曳至 [資料行群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ab56-171">Drag **SalesDate** to **Column groups**.</span></span>  
  
9. <span data-ttu-id="1ab56-172">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="1ab56-172">Click **Next**.</span></span>  
  
10. <span data-ttu-id="1ab56-173">在 [**選擇版面**配置] 頁面的 [**選項**] 底下，確認已選取 [**顯示小計和總計**]。</span><span class="sxs-lookup"><span data-stu-id="1ab56-173">On the **Choose the layout** page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
     <span data-ttu-id="1ab56-174">精靈的 [預覽] 窗格會顯示含有三個資料列的資料表。</span><span class="sxs-lookup"><span data-stu-id="1ab56-174">The wizard Preview pane displays a table with three rows.</span></span> <span data-ttu-id="1ab56-175">當您執行報表時，每個資料列都會以下列方式顯示：</span><span class="sxs-lookup"><span data-stu-id="1ab56-175">When you run the report, each row will display in the following way:</span></span>  
  
    1.  <span data-ttu-id="1ab56-176">第一個資料列會針對資料表出現一次，以顯示資料行標題。</span><span class="sxs-lookup"><span data-stu-id="1ab56-176">The first row will appear once for the table to show column headings.</span></span>  
  
    2.  <span data-ttu-id="1ab56-177">第二個資料列會針對每個產品重複一次，並顯示產品名稱、每日小計和產品線總計。</span><span class="sxs-lookup"><span data-stu-id="1ab56-177">The second row will repeat once for each product and display the product name, total per day, and line total.</span></span>  
  
    3.  <span data-ttu-id="1ab56-178">第三個資料列會針對資料表出現一次，以顯示總計。</span><span class="sxs-lookup"><span data-stu-id="1ab56-178">The third row will appear once for the table to display the grand totals.</span></span>  
  
11. <span data-ttu-id="1ab56-179">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="1ab56-179">Click **Next**.</span></span>  
  
12. <span data-ttu-id="1ab56-180">在 **[選擇樣式]** 頁面的 **[樣式]** 窗格中，選取 **[石板]**。</span><span class="sxs-lookup"><span data-stu-id="1ab56-180">On the **Choose a Style** page, in the **Styles** pane, select **Slate**.</span></span>  
  
     <span data-ttu-id="1ab56-181">[預覽] 窗格隨即顯示採用該樣式的資料表範例。</span><span class="sxs-lookup"><span data-stu-id="1ab56-181">The Preview pane displays a sample of the table with that style.</span></span>  
  
13. <span data-ttu-id="1ab56-182">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="1ab56-182">Click **Finish**.</span></span>  
  
14. <span data-ttu-id="1ab56-183">資料表會加入至設計介面。</span><span class="sxs-lookup"><span data-stu-id="1ab56-183">The table is added to the design surface.</span></span> <span data-ttu-id="1ab56-184">該資料表具有三個資料行和三個資料列。</span><span class="sxs-lookup"><span data-stu-id="1ab56-184">The table has three columns and three rows.</span></span>  
  
     <span data-ttu-id="1ab56-185">請查看 [群組] 窗格。</span><span class="sxs-lookup"><span data-stu-id="1ab56-185">Look in the Grouping pane.</span></span> <span data-ttu-id="1ab56-186">如果未顯示 [群組] 窗格，請按一下 [檢視]\*\*\*\* 功能表上的 [群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ab56-186">If you can't see the Grouping pane, on the **View** menu, click **Grouping**.</span></span> <span data-ttu-id="1ab56-187">[資料列群組] 窗格會顯示一個資料列群組： **Product**。</span><span class="sxs-lookup"><span data-stu-id="1ab56-187">The Row Groups pane shows one row group: **Product**.</span></span> <span data-ttu-id="1ab56-188">[資料行群組] 窗格會顯示一個資料行群組： **SalesDate**。</span><span class="sxs-lookup"><span data-stu-id="1ab56-188">The Column Groups pane shows one column group: **SalesDate**.</span></span> <span data-ttu-id="1ab56-189">詳細資料是資料集查詢擷取的所有資料。</span><span class="sxs-lookup"><span data-stu-id="1ab56-189">Detail data is all the data that is retrieved by the dataset query.</span></span>  
  
15. <span data-ttu-id="1ab56-190">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="1ab56-190">Click **Run** to preview the report.</span></span>  
  
##  <a name="3-add-a-sparkline"></a><a name="Sparkline"></a><span data-ttu-id="1ab56-191">3. 加入走勢圖</span><span class="sxs-lookup"><span data-stu-id="1ab56-191">3. Add a Sparkline</span></span>  
  
#### <a name="to-add-a-sparkline-chart-to-a-table"></a><span data-ttu-id="1ab56-192">將走勢圖加入至資料表</span><span class="sxs-lookup"><span data-stu-id="1ab56-192">To add a sparkline chart to a table</span></span>  
  
1.  <span data-ttu-id="1ab56-193">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="1ab56-193">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="1ab56-194">選取資料表中的 [總計] 資料行。</span><span class="sxs-lookup"><span data-stu-id="1ab56-194">Select the Total column in your table.</span></span>  
  
3.  <span data-ttu-id="1ab56-195">按一下滑鼠右鍵，指向 [插入資料行]\*\*\*\*，然後按一下 [左方]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ab56-195">Right-click, point to **Insert Column**, and then click **Left**.</span></span>  
  
4.  <span data-ttu-id="1ab56-196">在新的資料行中，以滑鼠右鍵按一下 [Product] 資料列，指向 [**插入**] 功能區索引標籤，然後按一下 [走勢**圖**]。</span><span class="sxs-lookup"><span data-stu-id="1ab56-196">In the new column, right-click in the [Product] row, point to the **Insert** ribbon tab, and then click **Sparkline**.</span></span>  
  
5.  <span data-ttu-id="1ab56-197">請確定已選取 [資料行] 資料**列**中的第一個走勢圖，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="1ab56-197">Make sure the first sparkline in the **Column** row is selected and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="1ab56-198">按一下走勢圖以顯示 [圖表資料] 窗格。</span><span class="sxs-lookup"><span data-stu-id="1ab56-198">Click the sparkline to show the Chart Data pane.</span></span>  
  
7.  <span data-ttu-id="1ab56-199">按一下 [值] 方塊中的加號 (+) ]，然後按一下 [**銷售**]。</span><span class="sxs-lookup"><span data-stu-id="1ab56-199">Click the plus (+) sign in the Values box, and then click **Sales**.</span></span>  
  
     <span data-ttu-id="1ab56-200">**Sales** 欄位內的值現在即為走勢圖的值。</span><span class="sxs-lookup"><span data-stu-id="1ab56-200">The values in the **Sales** field are now the values for the sparkline.</span></span>  
  
8.  <span data-ttu-id="1ab56-201">按一下 [類別目錄群組] 方塊中的加號 (+) 號，然後按一下 [ **SalesDate**]。</span><span class="sxs-lookup"><span data-stu-id="1ab56-201">Click the plus (+) sign in the Category Groups box, and then click **SalesDate**.</span></span>  
  
9. <span data-ttu-id="1ab56-202">按一下 [執行]\*\*\*\* 以預覽報表。</span><span class="sxs-lookup"><span data-stu-id="1ab56-202">Click **Run** to preview your report.</span></span>  
  
     <span data-ttu-id="1ab56-203">請注意資料表的每一列內都有走勢圖，但是圖表並不正確。</span><span class="sxs-lookup"><span data-stu-id="1ab56-203">Note that there are sparkline charts in each row of the table, but they're not correct.</span></span> <span data-ttu-id="1ab56-204">圖表中的橫條沒有彼此切齊。</span><span class="sxs-lookup"><span data-stu-id="1ab56-204">The bars in the charts don't line up with each other.</span></span> <span data-ttu-id="1ab56-205">第二個資料列只有四個橫條，而第一列有六個，因此前者的橫條比後者的橫條還要寬。</span><span class="sxs-lookup"><span data-stu-id="1ab56-205">There are only four bars in the second row of data, so the bars are wider than the bars in the first row, which has six.</span></span> <span data-ttu-id="1ab56-206">這樣您無法比較各產品每日的值，</span><span class="sxs-lookup"><span data-stu-id="1ab56-206">You can't compare values for each product per day.</span></span> <span data-ttu-id="1ab56-207">這些橫條必須彼此貼齊。</span><span class="sxs-lookup"><span data-stu-id="1ab56-207">They need to line up with each other.</span></span>  
  
     <span data-ttu-id="1ab56-208">同時請注意，每一列內最高的橫條都和該列等高。</span><span class="sxs-lookup"><span data-stu-id="1ab56-208">Also note that for each row, the tallest bar for that row is the height of the row.</span></span> <span data-ttu-id="1ab56-209">這也會造成誤導，因為每個資料列的最大值不相等：預算 Movie Maker 的最大值為 $10400，但超薄數位的最大值為 $26576-超過兩倍以上。</span><span class="sxs-lookup"><span data-stu-id="1ab56-209">This is misleading, too, because the largest values for each row are not equal: the largest value for Budget Movie-Maker is $10,400, but the largest value for Slim Digital is $26,576-more than twice as large.</span></span> <span data-ttu-id="1ab56-210">然而，這兩列內最大值橫條的高度幾乎一樣，</span><span class="sxs-lookup"><span data-stu-id="1ab56-210">And yet the largest bars in those two rows are about the same height.</span></span> <span data-ttu-id="1ab56-211">這些橫條需要能夠隨著其他走勢圖縮放。</span><span class="sxs-lookup"><span data-stu-id="1ab56-211">That also needs to be made to scale with the other sparklines.</span></span>  
  
     <span data-ttu-id="1ab56-212">![rs_SprklineMtrxUnaligndBars](../../2014/tutorials/media/rs-sprklinemtrxunaligndbars.gif "rs_SprklineMtrxUnaligndBars")</span><span class="sxs-lookup"><span data-stu-id="1ab56-212">![rs_SprklineMtrxUnaligndBars](../../2014/tutorials/media/rs-sprklinemtrxunaligndbars.gif "rs_SprklineMtrxUnaligndBars")</span></span>  
  
##  <a name="4-align-the-sparklines-vertically-and-horizontally"></a><a name="AlignSparklines"></a><span data-ttu-id="1ab56-213">4. 垂直與水準對齊走勢圖</span><span class="sxs-lookup"><span data-stu-id="1ab56-213">4. Align the Sparklines Vertically and Horizontally</span></span>  
 <span data-ttu-id="1ab56-214">當走勢圖不全都使用相同的量值時，就難以閱讀走勢圖。</span><span class="sxs-lookup"><span data-stu-id="1ab56-214">The sparklines are hard to read when they don't all use the same measurements.</span></span> <span data-ttu-id="1ab56-215">每一個走勢圖的水平和垂直軸都需要符合其餘的走勢圖。</span><span class="sxs-lookup"><span data-stu-id="1ab56-215">Both the horizontal and vertical axes for each need to match the rest.</span></span>  
  
#### <a name="to-set-alignment-for-the-sparklines-in-the-table"></a><span data-ttu-id="1ab56-216">設定資料表中走勢圖的對齊方式</span><span class="sxs-lookup"><span data-stu-id="1ab56-216">To set alignment for the sparklines in the table</span></span>  
  
1.  <span data-ttu-id="1ab56-217">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="1ab56-217">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="1ab56-218">以滑鼠右鍵按一下走勢圖，然後按一下 [垂直軸屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ab56-218">Right-click the sparkline and click **Vertical Axis Properties**.</span></span>  
  
3.  <span data-ttu-id="1ab56-219">選取 [軸對齊位置]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="1ab56-219">Check the **Align axes in** check box.</span></span>  
  
     <span data-ttu-id="1ab56-220">清單中會顯示 Tablix1。</span><span class="sxs-lookup"><span data-stu-id="1ab56-220">Tablix1 is showing in the list.</span></span> <span data-ttu-id="1ab56-221">此為唯一的選項。</span><span class="sxs-lookup"><span data-stu-id="1ab56-221">That is the only option.</span></span> <span data-ttu-id="1ab56-222">這是將每個走勢圖內的橫條高度設定成彼此的相對值。</span><span class="sxs-lookup"><span data-stu-id="1ab56-222">This sets the height of the bars in each sparkline relative to the others.</span></span>  
  
4.  <span data-ttu-id="1ab56-223">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="1ab56-223">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="1ab56-224">以滑鼠右鍵按一下走勢圖，然後按一下 [水平軸屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ab56-224">Right-click the sparkline and click **Horizontal Axis Properties**.</span></span>  
  
6.  <span data-ttu-id="1ab56-225">選取 [軸對齊位置]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="1ab56-225">Check the **Align axes in** check box.</span></span>  
  
     <span data-ttu-id="1ab56-226">清單中會顯示 Tablix1。</span><span class="sxs-lookup"><span data-stu-id="1ab56-226">Tablix1 is showing in the list.</span></span> <span data-ttu-id="1ab56-227">此為唯一的選項。</span><span class="sxs-lookup"><span data-stu-id="1ab56-227">That is the only option.</span></span> <span data-ttu-id="1ab56-228">這是將每個走勢圖內的橫條寬度設定成彼此的相對值。</span><span class="sxs-lookup"><span data-stu-id="1ab56-228">This sets the width of the bars in each sparkline relative to the others.</span></span> <span data-ttu-id="1ab56-229">如果某些走勢圖的橫條數目較少，則這些走勢圖將以空白代表缺資料。</span><span class="sxs-lookup"><span data-stu-id="1ab56-229">If some sparklines have fewer bars than others, then those sparklines will have blank spaces for the missing data.</span></span>  
  
7.  <span data-ttu-id="1ab56-230">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="1ab56-230">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="1ab56-231">按一下 [執行]\*\*\*\* 來重新預覽報表。</span><span class="sxs-lookup"><span data-stu-id="1ab56-231">Click **Run** to preview your report again.</span></span>  
  
 <span data-ttu-id="1ab56-232">請注意，所有橫條現在已與其他列內的橫條對齊。</span><span class="sxs-lookup"><span data-stu-id="1ab56-232">Note that all the bars are now aligned with the bars in the other rows.</span></span>  
  
##  <a name="5-optional-format-data-as-currency"></a><a name="FormatCurrency"></a><span data-ttu-id="1ab56-233">5. (選擇性) 將資料格式化為貨幣</span><span class="sxs-lookup"><span data-stu-id="1ab56-233">5. (Optional) Format Data as Currency</span></span>  
 <span data-ttu-id="1ab56-234">根據預設，[ **Sales** ] 欄位的摘要資料會顯示一般數位。</span><span class="sxs-lookup"><span data-stu-id="1ab56-234">By default, the summary data for the **Sales** field displays a general number.</span></span> <span data-ttu-id="1ab56-235">格式化該欄位，將數字顯示為貨幣。</span><span class="sxs-lookup"><span data-stu-id="1ab56-235">Format it to display the number as currency.</span></span> <span data-ttu-id="1ab56-236">切換 [預留位置樣式]\*\*\*\*，將格式化的文字方塊和預留位置文字顯示為範例值。</span><span class="sxs-lookup"><span data-stu-id="1ab56-236">Toggle **Placeholder Styles** to display formatted text boxes and placeholder text as sample values.</span></span>  
  
#### <a name="to-format-a-currency-field"></a><span data-ttu-id="1ab56-237">格式化貨幣欄位</span><span class="sxs-lookup"><span data-stu-id="1ab56-237">To format a currency field</span></span>  
  
1.  <span data-ttu-id="1ab56-238">按一下 [**設計**]，切換至設計檢視。</span><span class="sxs-lookup"><span data-stu-id="1ab56-238">Click **Design** to switch to design view.</span></span>  
  
2.  <span data-ttu-id="1ab56-239">按一下第二個數據列中的資料格 ([ **SalesDate** ] 資料行中的 [標題] 資料列) ，然後拖曳以選取包含的所有資料格 `[Sum(Sales)]` 。</span><span class="sxs-lookup"><span data-stu-id="1ab56-239">Click the cell in the second row (under the column headings row) in the **SalesDate** column and drag to select all cells that contain `[Sum(Sales)]`.</span></span>  
  
3.  <span data-ttu-id="1ab56-240">在 [主資料夾]\*\*\*\* 索引標籤的 [數字]\*\*\*\* 群組中，按一下 [貨幣]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1ab56-240">On the **Home** tab, in the **Number** group, click the **Currency** button.</span></span> <span data-ttu-id="1ab56-241">這些資料格就會變更為顯示格式化貨幣。</span><span class="sxs-lookup"><span data-stu-id="1ab56-241">The cells change to show the formatted currency.</span></span>  
  
     <span data-ttu-id="1ab56-242">如果您的地區設定為 [英文 (美國)]，則預設範例文字會是 [**$12,345.00**]。</span><span class="sxs-lookup"><span data-stu-id="1ab56-242">If your regional setting is English (United States), the default sample text is [**$12,345.00**].</span></span> <span data-ttu-id="1ab56-243">如果您看不到範例貨幣值，請按一下 [**數位**] 群組中的 [**預留位置樣式**]，然後按一下 [**範例值**]。</span><span class="sxs-lookup"><span data-stu-id="1ab56-243">If you do not see an example currency value, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
4.  <span data-ttu-id="1ab56-244">按一下 [執行]\*\*\*\* 以預覽報表。</span><span class="sxs-lookup"><span data-stu-id="1ab56-244">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="1ab56-245">[ **Sales** ] 的摘要值會顯示為貨幣。</span><span class="sxs-lookup"><span data-stu-id="1ab56-245">The summary values for **Sales** display as currency.</span></span>  
  
##  <a name="6-optional-format-data-as-dates"></a><a name="FormatDates"></a><span data-ttu-id="1ab56-246">6. (選擇性) 將資料格式化為日期</span><span class="sxs-lookup"><span data-stu-id="1ab56-246">6. (Optional) Format Data as Dates</span></span>  
 <span data-ttu-id="1ab56-247">根據預設，[ **SalesDate** ] 欄位會同時顯示日期和時間資訊。</span><span class="sxs-lookup"><span data-stu-id="1ab56-247">By default, the **SalesDate** field displays both date and time information.</span></span> <span data-ttu-id="1ab56-248">您可以將該欄位格式化，以便只顯示日期。</span><span class="sxs-lookup"><span data-stu-id="1ab56-248">You can format them to display only the date.</span></span>  
  
#### <a name="to-format-a-date-field-as-the-default-format"></a><span data-ttu-id="1ab56-249">將日期欄位格式化成預設格式</span><span class="sxs-lookup"><span data-stu-id="1ab56-249">To format a date field as the default format</span></span>  
  
1.  <span data-ttu-id="1ab56-250">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="1ab56-250">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="1ab56-251">按一下包含 `[SalesDate]`的資料格。</span><span class="sxs-lookup"><span data-stu-id="1ab56-251">Click the cell that contains `[SalesDate]`.</span></span>  
  
3.  <span data-ttu-id="1ab56-252">在功能區的 [**首頁**] 索引標籤上，從 [**數位**] 群組的下拉式清單中，選取 [**日期**]。</span><span class="sxs-lookup"><span data-stu-id="1ab56-252">On the Ribbon, on the **Home** tab, in the **Number** group, from the drop-down list, select **Date**.</span></span>  
  
     <span data-ttu-id="1ab56-253">資料格會顯示範例日期 **[1/31/2000]**。</span><span class="sxs-lookup"><span data-stu-id="1ab56-253">The cell displays the example date **[1/31/2000]**.</span></span> <span data-ttu-id="1ab56-254">如果您看不到範例日期，請按一下 [數字]\*\*\*\* 群組中的 [預留位置樣式]\*\*\*\*，然後按一下 [範例值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ab56-254">If you do not see an example date, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
4.  <span data-ttu-id="1ab56-255">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="1ab56-255">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="1ab56-256">**SalesDate**值會以預設的日期格式顯示。</span><span class="sxs-lookup"><span data-stu-id="1ab56-256">The **SalesDate** values display in the default date format.</span></span>  
  
##  <a name="7-optional-change-column-widths"></a><a name="Width"></a><span data-ttu-id="1ab56-257">7. (選擇性) 變更資料行寬度</span><span class="sxs-lookup"><span data-stu-id="1ab56-257">7. (Optional) Change Column Widths</span></span>  
 <span data-ttu-id="1ab56-258">根據預設，資料表中的每個資料格都會包含一個文字方塊。</span><span class="sxs-lookup"><span data-stu-id="1ab56-258">By default, each cell in a table contains a text box.</span></span> <span data-ttu-id="1ab56-259">頁面轉譯時，文字方塊會垂直展開以容納文字。</span><span class="sxs-lookup"><span data-stu-id="1ab56-259">A text box expands vertically to accommodate text when the page is rendered.</span></span> <span data-ttu-id="1ab56-260">在轉譯的報表中，每一個資料列都會依照資料列中最高的轉譯文字方塊高度展開。</span><span class="sxs-lookup"><span data-stu-id="1ab56-260">In the rendered report, each row expands to the height of the tallest rendered text box in the row.</span></span> <span data-ttu-id="1ab56-261">設計介面上資料列的高度對於轉譯報表中資料列的高度並無影響。</span><span class="sxs-lookup"><span data-stu-id="1ab56-261">The height of the row on the design surface has no affect on the height of the row in the rendered report.</span></span>  
  
 <span data-ttu-id="1ab56-262">若要減少每個資料列佔用的垂直空間數量，請展開資料行寬度以容納一行上資料行中預期的文字方塊內容。</span><span class="sxs-lookup"><span data-stu-id="1ab56-262">To reduce the amount of vertical space each row takes, expand the column width to accommodate the expected contents of the text boxes in the column on one line.</span></span>  
  
#### <a name="to-change-the-width-of-columns"></a><span data-ttu-id="1ab56-263">變更資料行的寬度</span><span class="sxs-lookup"><span data-stu-id="1ab56-263">To change the width of columns</span></span>  
  
1.  <span data-ttu-id="1ab56-264">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="1ab56-264">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="1ab56-265">按一下資料表，使資料行和資料列控點出現在資料表的上面和旁邊。</span><span class="sxs-lookup"><span data-stu-id="1ab56-265">Click the table so that column and row handles appear above and next to the table.</span></span>  
  
     <span data-ttu-id="1ab56-266">沿著資料表頂端和側邊的灰色長條是資料行和資料列控點。</span><span class="sxs-lookup"><span data-stu-id="1ab56-266">The gray bars along the top and side of the table are the column and row handles.</span></span>  
  
3.  <span data-ttu-id="1ab56-267">指向資料行控點之間的線條，使游標變成雙箭頭。</span><span class="sxs-lookup"><span data-stu-id="1ab56-267">Point to the line between column handles so that the cursor changes into a double arrow.</span></span> <span data-ttu-id="1ab56-268">將資料行拖曳到所需的大小。</span><span class="sxs-lookup"><span data-stu-id="1ab56-268">Drag the columns to the size you want.</span></span> <span data-ttu-id="1ab56-269">例如，展開 [**產品**] 的資料行，讓產品名稱顯示在一行上。</span><span class="sxs-lookup"><span data-stu-id="1ab56-269">For example, expand the column for **Product** so that the product name displays on one line.</span></span>  
  
4.  <span data-ttu-id="1ab56-270">按一下 [執行]\*\*\*\* 以預覽報表。</span><span class="sxs-lookup"><span data-stu-id="1ab56-270">Click **Run** to preview your report.</span></span>  
  
##  <a name="8-optional-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="1ab56-271">8. (選擇性) 加入報表標題</span><span class="sxs-lookup"><span data-stu-id="1ab56-271">8. (Optional) Add a Report Title</span></span>  
 <span data-ttu-id="1ab56-272">報表標題會出現在報表的頂端。</span><span class="sxs-lookup"><span data-stu-id="1ab56-272">A report title appears at the top of the report.</span></span> <span data-ttu-id="1ab56-273">您可以將報表標題放置在報表頁首，如果報表不使用報表頁首，則可以放置在報表主體頂端的文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="1ab56-273">You can place the report title in a report header or if the report does not use one, in a text box at the top of the report body.</span></span> <span data-ttu-id="1ab56-274">在本教學課程中，您將使用自動放置在報表主體頂端的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="1ab56-274">In this tutorial, you will use the text box that is automatically placed at the top of the report body.</span></span>  
  
 <span data-ttu-id="1ab56-275">您可以將不同的字型樣式、大小和色彩套用到文字的片語和個別字元，進一步加強文字。</span><span class="sxs-lookup"><span data-stu-id="1ab56-275">The text can be further enhanced by applying different font styles, sizes, and colors to phrases and individual characters of the text.</span></span> <span data-ttu-id="1ab56-276">如需詳細資訊，請參閱[在文字方塊中將文字格式化 &#40;報表產生器及 SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1ab56-276">For more information, see [Format Text in a Text Box &#40;Report Builder and SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="1ab56-277">若要加入報表標題</span><span class="sxs-lookup"><span data-stu-id="1ab56-277">To add a report title</span></span>  
  
1.  <span data-ttu-id="1ab56-278">在設計介面上，按一下 **[按一下以加入標題]**。</span><span class="sxs-lookup"><span data-stu-id="1ab56-278">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="1ab56-279">輸入 **Product Sales**，然後按一下文字方塊外部。</span><span class="sxs-lookup"><span data-stu-id="1ab56-279">Type **Product Sales**, and then click outside the text box.</span></span>  
  
3.  <span data-ttu-id="1ab56-280">以滑鼠右鍵按一下包含 [Product Sales]\*\*\*\* 的文字方塊，然後按一下 [文字方塊屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ab56-280">Right-click the text box that contains **Product Sales** and click **Text Box Properties**.</span></span>  
  
4.  <span data-ttu-id="1ab56-281">在 [文字方塊屬性]\*\*\*\* 對話方塊中，按一下 [字型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ab56-281">In the **Text Box Properties** dialog box, click **Font**.</span></span>  
  
5.  <span data-ttu-id="1ab56-282">在 [大小]\*\*\*\* 清單中，選取 [18pt]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ab56-282">In the **Size** list, select **18pt**.</span></span>  
  
6.  <span data-ttu-id="1ab56-283">在 [**色彩**] 清單中，選取 [**褐紫紅色**]。</span><span class="sxs-lookup"><span data-stu-id="1ab56-283">In the **Color** list, select **Maroon**.</span></span>  
  
7.  <span data-ttu-id="1ab56-284">選取 [粗體]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ab56-284">Select **Bold**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="9-save-the-report"></a><a name="Save"></a><span data-ttu-id="1ab56-285">9. 儲存報表</span><span class="sxs-lookup"><span data-stu-id="1ab56-285">9. Save the Report</span></span>  
 <span data-ttu-id="1ab56-286">將報表儲存至報表伺服器或您的電腦。</span><span class="sxs-lookup"><span data-stu-id="1ab56-286">Save the report to a report server or your computer.</span></span> <span data-ttu-id="1ab56-287">如果沒有將報表儲存到報表伺服器，就無法使用數個 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能，例如報表組件和子報表。</span><span class="sxs-lookup"><span data-stu-id="1ab56-287">If you do not save the report to the report server, a number of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features such as report parts and subreports are not available.</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="1ab56-288">若要將報表儲存在報表伺服器上</span><span class="sxs-lookup"><span data-stu-id="1ab56-288">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="1ab56-289">在 **[報表產生器]** 按鈕中，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="1ab56-289">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="1ab56-290">按一下 **[最近使用的網站和伺服器]**。</span><span class="sxs-lookup"><span data-stu-id="1ab56-290">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="1ab56-291">選取或輸入您有權儲存報表之報表伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="1ab56-291">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="1ab56-292">「正在連接到報表伺服器」訊息隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="1ab56-292">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="1ab56-293">連接完成時，您就會看見報表伺服器管理員指定為預設報表位置之報表資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="1ab56-293">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>  
  
4.  <span data-ttu-id="1ab56-294">將 [名稱]\*\*\*\* 中的預設名稱取代為 **Product Sales**。</span><span class="sxs-lookup"><span data-stu-id="1ab56-294">In **Name**, replace the default name with **Product Sales**.</span></span>  
  
5.  <span data-ttu-id="1ab56-295">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="1ab56-295">Click **Save**.</span></span>  
  
 <span data-ttu-id="1ab56-296">報表就會儲存至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="1ab56-296">The report is saved to the report server.</span></span> <span data-ttu-id="1ab56-297">您連接之報表伺服器的名稱會顯示在視窗底部的狀態列中。</span><span class="sxs-lookup"><span data-stu-id="1ab56-297">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="1ab56-298">將報表儲存到您的電腦上</span><span class="sxs-lookup"><span data-stu-id="1ab56-298">To save the report on your computer</span></span>  
  
1.  <span data-ttu-id="1ab56-299">在 **[報表產生器]** 按鈕中，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="1ab56-299">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="1ab56-300">按一下 [桌面]\*\*\*\*、[我的文件]\*\*\*\* 或 [我的電腦]\*\*\*\*，然後瀏覽到您要儲存報表的資料夾。</span><span class="sxs-lookup"><span data-stu-id="1ab56-300">Click **Desktop**, **My Documents**, or **My computer**, and browse to the folder where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="1ab56-301">將 [名稱]\*\*\*\* 中的預設名稱取代為 **Product Sales**。</span><span class="sxs-lookup"><span data-stu-id="1ab56-301">In **Name**, replace the default name with **Product Sales**.</span></span>  
  
4.  <span data-ttu-id="1ab56-302">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="1ab56-302">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1ab56-303">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1ab56-303">Next Steps</span></span>  
 <span data-ttu-id="1ab56-304">這總結本教學課程：建立含走勢圖的資料表報表。</span><span class="sxs-lookup"><span data-stu-id="1ab56-304">This concludes the tutorial for creating a table report with sparkline charts.</span></span> <span data-ttu-id="1ab56-305">如需走勢圖的詳細資訊，請參閱[走勢圖和資料橫條 &#40;報表產生器和 SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1ab56-305">For more information about sparklines, see [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ab56-306">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ab56-306">See Also</span></span>  
 <span data-ttu-id="1ab56-307">[教學課程 &#40;報表產生器&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="1ab56-307">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="1ab56-308">SQL Server 2014 中的報表產生器</span><span class="sxs-lookup"><span data-stu-id="1ab56-308">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
