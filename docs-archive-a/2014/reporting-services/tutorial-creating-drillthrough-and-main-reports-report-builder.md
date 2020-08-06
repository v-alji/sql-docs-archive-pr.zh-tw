---
title: 教學課程：建立鑽研及主報表 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7168c8d3-cef5-4c4a-a0bf-fff1ac5b8b71
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d7d30b59a0c5523ed50df06f8587bbd701ae4c79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706114"
---
# <a name="tutorial-creating-drillthrough-and-main-reports-report-builder"></a><span data-ttu-id="80241-102">教學課程：建立鑽研及主報表 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="80241-102">Tutorial: Creating Drillthrough and Main Reports (Report Builder)</span></span>
  <span data-ttu-id="80241-103">本教學課程將教導您如何建立兩種報表：鑽研報表與主報表。</span><span class="sxs-lookup"><span data-stu-id="80241-103">This tutorial teaches you how to create two kinds of reports: a drillthrough report and a main report.</span></span> <span data-ttu-id="80241-104">這些報表中使用的範例銷售資料是從 Analysis Services Cube 擷取的。</span><span class="sxs-lookup"><span data-stu-id="80241-104">The sample sales data used in these reports is retrieved from an Analysis Services cube.</span></span> <span data-ttu-id="80241-105">下圖顯示您將建立的報表。</span><span class="sxs-lookup"><span data-stu-id="80241-105">The following illustration shows the reports you will create.</span></span>  
  
 <span data-ttu-id="80241-106">![rs_DrillthroughCubeTutorial](../../2014/tutorials/media/rs-drillthroughcubetutorial.gif "rs_DrillthroughCubeTutorial")</span><span class="sxs-lookup"><span data-stu-id="80241-106">![rs_DrillthroughCubeTutorial](../../2014/tutorials/media/rs-drillthroughcubetutorial.gif "rs_DrillthroughCubeTutorial")</span></span>  
  
 <span data-ttu-id="80241-107">下圖顯示主報表中的域值（遊戲和玩具）如何顯示在「鑽看」報表的標題中。</span><span class="sxs-lookup"><span data-stu-id="80241-107">The following illustration shows how the field value, Games and Toys, in the main report displays in the drillthrough report's title.</span></span> <span data-ttu-id="80241-108">鑽研報表中的資料與 Games and Toys 產品類別目錄有關。</span><span class="sxs-lookup"><span data-stu-id="80241-108">The data in the drillthrough pertains to the Games and Toys product category.</span></span>  
  
 <span data-ttu-id="80241-109">![rs_DrillthroughCubeTutorialParmExpr](../../2014/tutorials/media/rs-drillthroughcubetutorialparmexpr.gif "rs_DrillthroughCubeTutorialParmExpr")</span><span class="sxs-lookup"><span data-stu-id="80241-109">![rs_DrillthroughCubeTutorialParmExpr](../../2014/tutorials/media/rs-drillthroughcubetutorialparmexpr.gif "rs_DrillthroughCubeTutorialParmExpr")</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="80241-110">學習內容</span><span class="sxs-lookup"><span data-stu-id="80241-110">What You Will Learn</span></span>  
 <span data-ttu-id="80241-111">**在鑽研報表中，您將了解如何：**</span><span class="sxs-lookup"><span data-stu-id="80241-111">**In the drillthrough report you will learn how to:**</span></span>  
  
1.  [<span data-ttu-id="80241-112">從資料表或矩陣精靈建立鑽研矩陣報表和資料集</span><span class="sxs-lookup"><span data-stu-id="80241-112">Create a Drillthrough Matrix Report and Dataset from the Table or Matrix Wizard</span></span>](#DMatrixAndDataset)  
  
    1.  [<span data-ttu-id="80241-113">指定資料連接</span><span class="sxs-lookup"><span data-stu-id="80241-113">Specify a Data Connection</span></span>](#DConnection)  
  
    2.  [<span data-ttu-id="80241-114">建立 MDX 查詢</span><span class="sxs-lookup"><span data-stu-id="80241-114">Create an MDX Query</span></span>](#DMDXQuery)  
  
    3.  [<span data-ttu-id="80241-115">將資料組織為群組樣式</span><span class="sxs-lookup"><span data-stu-id="80241-115">Organize Data into Groups Style</span></span>](#DLayout)  
  
    4.  [<span data-ttu-id="80241-116">加入小計和總計</span><span class="sxs-lookup"><span data-stu-id="80241-116">Add Subtotals and Totals</span></span>](#DTotals)  
  
    5.  [<span data-ttu-id="80241-117">選擇樣式</span><span class="sxs-lookup"><span data-stu-id="80241-117">Choose a Style</span></span>](#DStyle)  
  
2.  [<span data-ttu-id="80241-118">將資料格式化為貨幣</span><span class="sxs-lookup"><span data-stu-id="80241-118">Format Data as Currency</span></span>](#DFormat)  
  
3.  [<span data-ttu-id="80241-119">新增資料行以在走勢圖中顯示銷售值</span><span class="sxs-lookup"><span data-stu-id="80241-119">Add columns to Show Sales Values in Sparklines</span></span>](#DSparkline)  
  
4.  [<span data-ttu-id="80241-120">加入具有產品類別目錄名稱的報表標題</span><span class="sxs-lookup"><span data-stu-id="80241-120">Add Report Title with Product Category Name</span></span>](#DReportTitle)  
  
5.  [<span data-ttu-id="80241-121">更新參數屬性</span><span class="sxs-lookup"><span data-stu-id="80241-121">Update Parameter Properties</span></span>](#DParameter)  
  
6.  [<span data-ttu-id="80241-122">將報表儲存至 SharePoint 文件庫</span><span class="sxs-lookup"><span data-stu-id="80241-122">Save the Report to a SharePoint Library</span></span>](#DSave)  
  
 <span data-ttu-id="80241-123">**在主報表中，您將了解如何：**</span><span class="sxs-lookup"><span data-stu-id="80241-123">**In the main report you will learn how to:**</span></span>  
  
1.  [<span data-ttu-id="80241-124">從資料表或矩陣精靈建立主要矩陣報表和資料集</span><span class="sxs-lookup"><span data-stu-id="80241-124">Create the Main Matrix Report and Dataset from the Table or Matrix Wizard</span></span>](#MMatrixAndDataset)  
  
    1.  [<span data-ttu-id="80241-125">指定資料連接</span><span class="sxs-lookup"><span data-stu-id="80241-125">Specify a Data Connection</span></span>](#MConnection)  
  
    2.  [<span data-ttu-id="80241-126">建立 MDX 查詢</span><span class="sxs-lookup"><span data-stu-id="80241-126">Create an MDX Query</span></span>](#MMDXQuery)  
  
    3.  [<span data-ttu-id="80241-127">將資料組織為群組</span><span class="sxs-lookup"><span data-stu-id="80241-127">Organize Data into Groups</span></span>](#MLayout)  
  
    4.  [<span data-ttu-id="80241-128">加入小計和總計</span><span class="sxs-lookup"><span data-stu-id="80241-128">Add Subtotals and Totals</span></span>](#MTotals)  
  
    5.  [<span data-ttu-id="80241-129">選擇樣式</span><span class="sxs-lookup"><span data-stu-id="80241-129">Choose a Style</span></span>](#MStyle)  
  
2.  [<span data-ttu-id="80241-130">移除總計資料列</span><span class="sxs-lookup"><span data-stu-id="80241-130">Remove the Grand Total Row</span></span>](#MGrandTotal)  
  
3.  [<span data-ttu-id="80241-131">設定用於鑽研的文字方塊動作</span><span class="sxs-lookup"><span data-stu-id="80241-131">Configure Text Box Action for Drillthrough</span></span>](#MDrillthrough)  
  
4.  [<span data-ttu-id="80241-132">以指標取代數值</span><span class="sxs-lookup"><span data-stu-id="80241-132">Replace Numeric Values with Indicators</span></span>](#MIndicators)  
  
5.  [<span data-ttu-id="80241-133">更新參數屬性</span><span class="sxs-lookup"><span data-stu-id="80241-133">Update Parameter Properties</span></span>](#MParameter)  
  
6.  [<span data-ttu-id="80241-134">加入報表標題</span><span class="sxs-lookup"><span data-stu-id="80241-134">Add a Report Title</span></span>](#MTitle)  
  
7.  [<span data-ttu-id="80241-135">將報表儲存至 SharePoint 文件庫</span><span class="sxs-lookup"><span data-stu-id="80241-135">Save the Report to a SharePoint Library</span></span>](#MSave)  
  
8.  [<span data-ttu-id="80241-136">執行主報表和鑽研報表</span><span class="sxs-lookup"><span data-stu-id="80241-136">Run the Main and Drillthrough Reports</span></span>](#MRunReports)  
  
 <span data-ttu-id="80241-137">完成本教學課程的估計時間：30 分鐘。</span><span class="sxs-lookup"><span data-stu-id="80241-137">Estimated time to complete this tutorial: 30 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80241-138">需求</span><span class="sxs-lookup"><span data-stu-id="80241-138">Requirements</span></span>  
 <span data-ttu-id="80241-139">這個教學課程需要能夠存取 Contoso Sales Cube。</span><span class="sxs-lookup"><span data-stu-id="80241-139">This tutorial requires access to the Contoso Sales cube.</span></span> <span data-ttu-id="80241-140">這個需求同時適用於鑽研報表和主報表。</span><span class="sxs-lookup"><span data-stu-id="80241-140">This requirement applies to both the drillthrough and the main reports.</span></span> <span data-ttu-id="80241-141">如需需求的詳細資訊，請參閱[教學課程的必要條件 &#40;報表產生器&#41;](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="80241-141">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-drillthrough-report-from-the-table-or-matrix-wizard"></a><a name="DMatrixAndDataset"></a><span data-ttu-id="80241-142">1. 從資料表或矩陣 Wizard 建立鑽研報表</span><span class="sxs-lookup"><span data-stu-id="80241-142">1. Create a Drillthrough Report from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="80241-143">從 [使用者入門] 對話方塊中，使用 **[資料表或矩陣精靈]** 建立矩陣報表。</span><span class="sxs-lookup"><span data-stu-id="80241-143">From the Getting Started dialog box, create a matrix report by using the **Table or Matrix Wizard**.</span></span> <span data-ttu-id="80241-144">精靈中可用的模式有兩種：報表設計和共用資料集設計。</span><span class="sxs-lookup"><span data-stu-id="80241-144">There are two modes available in the wizard: report design and shared dataset design.</span></span> <span data-ttu-id="80241-145">在本教學課程中，您將使用報表設計模式。</span><span class="sxs-lookup"><span data-stu-id="80241-145">In this tutorial, you will use the report design mode.</span></span>  
  
#### <a name="to-create-a-new-report"></a><span data-ttu-id="80241-146">建立新的報表</span><span class="sxs-lookup"><span data-stu-id="80241-146">To create a new report</span></span>  
  
1.  <span data-ttu-id="80241-147">按一下 [ **開始**]、依序指向 [ **程式集**] 和 [ [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **報表產生器**]，然後按一下 [ **報表產生器**]。</span><span class="sxs-lookup"><span data-stu-id="80241-147">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="80241-148">**[使用者入門]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="80241-148">The **Getting Started** dialog box opens.</span></span> <span data-ttu-id="80241-149">如果沒有出現，請在 **[報表產生器]** 按鈕中按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="80241-149">If it does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
2.  <span data-ttu-id="80241-150">在左窗格中，確認已選取 **[新增報表]** 。</span><span class="sxs-lookup"><span data-stu-id="80241-150">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="80241-151">在右窗格中，確認已選取 **[資料表或矩陣精靈]** 。</span><span class="sxs-lookup"><span data-stu-id="80241-151">In the right pane, verify that **Table or Matrix Wizard** is selected.</span></span>  
  
##  <a name="1a-specify-a-data-connection"></a><a name="DConnection"></a><span data-ttu-id="80241-152">1a.</span><span class="sxs-lookup"><span data-stu-id="80241-152">1a.</span></span> <span data-ttu-id="80241-153">指定資料連接</span><span class="sxs-lookup"><span data-stu-id="80241-153">Specify a Data Connection</span></span>  
 <span data-ttu-id="80241-154">資料連接包含連接至外部資料來源所需的資訊，例如 Analysis Services Cube 或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="80241-154">A data connection contains the information necessary to connect to an external data source such as an Analysis Services cube or a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="80241-155">若要指定資料連接，您可以使用來自報表伺服器的共用資料來源，或是建立僅在此報表中使用的內嵌資料來源。</span><span class="sxs-lookup"><span data-stu-id="80241-155">To specify a data connection, you can use a shared data source from the report server or create an embedded data source that is used only in this report.</span></span> <span data-ttu-id="80241-156">在本教學課程中，您將使用內嵌資料來源。</span><span class="sxs-lookup"><span data-stu-id="80241-156">In this tutorial, you will use an embedded data source.</span></span> <span data-ttu-id="80241-157">若要深入了解如何使用共用資料來源，請參閱[取得資料連線的替代方式 &#40;報表產生器&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="80241-157">To learn more about using a shared data source, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
#### <a name="to-create-an-embedded-data-source"></a><span data-ttu-id="80241-158">建立內嵌資料來源</span><span class="sxs-lookup"><span data-stu-id="80241-158">To create an embedded data source</span></span>  
  
1.  <span data-ttu-id="80241-159">在 **[選擇資料集]** 頁面上，選取 **[建立資料集]**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="80241-159">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span> <span data-ttu-id="80241-160">**[選擇與資料來源的連接]** 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="80241-160">The **Choose a connection to a data source** page opens.</span></span>  
  
2.  <span data-ttu-id="80241-161">按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="80241-161">Click **New**.</span></span> <span data-ttu-id="80241-162">**[資料來源屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="80241-162">The **Data Source Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="80241-163">在 **[名稱]** 中輸入 **Online and Reseller Sales Detail** 做為資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="80241-163">In **Name**, type **Online and Reseller Sales Detail** as the name for the data source.</span></span>  
  
4.  <span data-ttu-id="80241-164">在 **[選取連接類型]** 中，選取 **[Microsoft SQL Server Analysis Services]**，然後按一下 **[建立]**。</span><span class="sxs-lookup"><span data-stu-id="80241-164">In **Select a connection type**, select **Microsoft SQL Server Analysis Services**, and then click **Build**.</span></span>  
  
5.  <span data-ttu-id="80241-165">在 **[資料來源]** 中，確認資料來源為 **[Microsoft SQL Server Analysis Services (AdomdClient)]**。</span><span class="sxs-lookup"><span data-stu-id="80241-165">In **Data source**, verify that the data source is **Microsoft SQL Server Analysis Services (AdomdClient)**.</span></span>  
  
6.  <span data-ttu-id="80241-166">在 **[伺服器名稱]** 中，輸入安裝 Analysis Services 執行個體所在伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="80241-166">In **Server name**, type the name of a server where an instance of Analysis Services is installed.</span></span>  
  
7.  <span data-ttu-id="80241-167">在 [選取或輸入資料庫名稱]\*\*\*\* 中，選取 [Contoso] Cube。</span><span class="sxs-lookup"><span data-stu-id="80241-167">In **Select or enter a database name**, select the Contoso cube.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. <span data-ttu-id="80241-168">確認 **[連接字串]** 包含下列語法：</span><span class="sxs-lookup"><span data-stu-id="80241-168">Verify that **Connection string** contains the following syntax:</span></span>  
  
    ```  
    Data Source=<servername>; Initial Catalog = Contoso  
    ```  
  
     <span data-ttu-id="80241-169">`<servername>` 是已安裝 Analysis Services 之 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="80241-169">The `<servername>` is the name of an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] with Analysis Services installed.</span></span>  
  
10. <span data-ttu-id="80241-170">按一下 **[認證類型]**。</span><span class="sxs-lookup"><span data-stu-id="80241-170">Click **Credentials type**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="80241-171">根據如何設定資料來源的權限而定，您可能需要變更預設的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="80241-171">Depending on how permissions are configured on the data source, you might need to change the default authentication options.</span></span> <span data-ttu-id="80241-172">如需詳細資訊，請參閱 [安全性 &#40;報表產生器&#41;](report-builder/security-report-builder.md)中建立的行動報表。</span><span class="sxs-lookup"><span data-stu-id="80241-172">For more information, see [Security &#40;Report Builder&#41;](report-builder/security-report-builder.md).</span></span>  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="80241-173">**[選擇與資料來源的連接]** 頁面隨即出現。</span><span class="sxs-lookup"><span data-stu-id="80241-173">The **Choose a connection to a data source** page appears.</span></span>  
  
12. <span data-ttu-id="80241-174">若要確認您能夠連接至資料來源，請按一下 **[測試連接]**。</span><span class="sxs-lookup"><span data-stu-id="80241-174">To verify that you can connect to the data source, click **Test Connection**.</span></span>  
  
     <span data-ttu-id="80241-175">隨即出現 [**已成功建立訊息連接**]。</span><span class="sxs-lookup"><span data-stu-id="80241-175">The message **Connection created successfully** appears.</span></span>  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
14. <span data-ttu-id="80241-176">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="80241-176">Click **Next**.</span></span>  
  
##  <a name="1b-create-an-mdx-query"></a><a name="DMDXQuery"></a><span data-ttu-id="80241-177">1a-1b.</span><span class="sxs-lookup"><span data-stu-id="80241-177">1b.</span></span> <span data-ttu-id="80241-178">建立 MDX 查詢</span><span class="sxs-lookup"><span data-stu-id="80241-178">Create an MDX Query</span></span>  
 <span data-ttu-id="80241-179">在報表中，您可以使用擁有預先定義查詢的共用資料集，或是建立只在報表中使用的內嵌資料集。</span><span class="sxs-lookup"><span data-stu-id="80241-179">In a report, you can use a shared dataset that has a predefined query, or you can create an embedded dataset for use only in your report.</span></span> <span data-ttu-id="80241-180">在本教學課程中，您將建立內嵌資料集。</span><span class="sxs-lookup"><span data-stu-id="80241-180">In this tutorial, you will create an embedded dataset.</span></span>  
  
#### <a name="to-create-query-filters"></a><span data-ttu-id="80241-181">若要建立查詢篩選</span><span class="sxs-lookup"><span data-stu-id="80241-181">To create query filters</span></span>  
  
1.  <span data-ttu-id="80241-182">在 [**設計查詢**] 頁面的 [中繼資料] 窗格中，按一下 [ \*\* ( ... ) \*\*] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="80241-182">On the **Design a query** page, in the Metadata pane, click the button **(...)**.</span></span>  
  
2.  <span data-ttu-id="80241-183">在 [選取 Cube]\*\*\*\* 對話方塊中，按一下 [Sales]，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="80241-183">In the **Cube Selection** dialog box, click Sales, and then click **OK**.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="80241-184">如果您不想要手動建置 MDX 查詢，請按一下![切換到設計模式](media/rsqdicon-designmode.gif "切換到設計模式")圖示，將查詢設計工具切換到 [查詢] 模式，並將完成的 MDX 貼到查詢設計工具，然後繼續進行[建立資料集](#DSkip)中的步驟 6。</span><span class="sxs-lookup"><span data-stu-id="80241-184">If you do not want to build the MDX query manually, click the ![Switch to Design mode](media/rsqdicon-designmode.gif "Switch to Design mode") icon, toggle the query designer to Query mode, paste the completed MDX to the query designer, and then proceed to step 6 in [To create the dataset](#DSkip).</span></span>  
  
    ```  
    SELECT NON EMPTY { [Measures].[Sales Amount], [Measures].[Sales Return Amount] } ON COLUMNS, NON EMPTY { ([Channel].[Channel Name].[Channel Name].ALLMEMBERS * [Product].[Product Category Name].[Product Category Name].ALLMEMBERS * [Product].[Product Subcategory Name].[Product Subcategory Name].ALLMEMBERS ) } DIMENSION PROPERTIES MEMBER_CAPTION, MEMBER_UNIQUE_NAME ON ROWS FROM ( SELECT ( { [Date].[Calendar Year].&[2009] } ) ON COLUMNS FROM ( SELECT ( { [Sales Territory].[Sales Territory Group].&[North America] } ) ON COLUMNS FROM ( SELECT ( STRTOSET(@ProductProductCategoryName, CONSTRAINED) ) ON COLUMNS FROM ( SELECT ( { [Channel].[Channel Name].&[2], [Channel].[Channel Name].&[4] } ) ON COLUMNS FROM [Sales])))) WHERE ( [Sales Territory].[Sales Territory Group].&[North America], [Date].[Calendar Year].&[2009] ) CELL PROPERTIES VALUE, BACK_COLOR, FORE_COLOR, FORMATTED_VALUE, FORMAT_STRING, FONT_NAME, FONT_SIZE, FONT_FLAGS  
    ```  
  
3.  <span data-ttu-id="80241-185">在 [量值群組] 窗格中，展開 Channel，然後將 Channel Name 拖曳到篩選窗格中的 [階層]\*\*\*\* 資料行。</span><span class="sxs-lookup"><span data-stu-id="80241-185">In the Measure Group pane, expand Channel, and then drag Channel Name to the **Hierarchy** column in the filter pane.</span></span>  
  
     <span data-ttu-id="80241-186">維度名稱 Channel 就會自動新增至 [維度]\*\*\*\* 資料行。</span><span class="sxs-lookup"><span data-stu-id="80241-186">The dimension name, Channel, is automatically added to the **Dimension** column.</span></span> <span data-ttu-id="80241-187">請勿變更 **[維度]** 或 **[運算子]** 資料行。</span><span class="sxs-lookup"><span data-stu-id="80241-187">Do not change the **Dimension** or **Operator** columns.</span></span>  
  
4.  <span data-ttu-id="80241-188">若要開啟 **[篩選運算式]** 清單，按一下 **[篩選運算式]** 資料行。</span><span class="sxs-lookup"><span data-stu-id="80241-188">To open the **Filter Expression** list, click the down arrow in the **Filter Expression** column.</span></span>  
  
5.  <span data-ttu-id="80241-189">在篩選運算式清單中，展開 **[所有通道]**，然後依序按一下 **[線上]**、 **[轉售商]** 和 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="80241-189">In the filter expression list, expand **All Channel**, click **Online**, click **Reseller**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="80241-190">此查詢現在包含一個僅內含下列通道的篩選：線上和轉售商。</span><span class="sxs-lookup"><span data-stu-id="80241-190">The query now includes a filter to include only these channels: Online and Reseller.</span></span>  
  
6.  <span data-ttu-id="80241-191">展開 Sales Territory 維度，然後將 Sales Territory Group 拖曳至 [階層]\*\*\*\* 資料行 (在 **Channel Name** 底下)。</span><span class="sxs-lookup"><span data-stu-id="80241-191">Expand the Sales Territory dimension, and then drag Sales Territory Group to the **Hierarchy** column (below **Channel Name**).</span></span>  
  
7.  <span data-ttu-id="80241-192">開啟 **[篩選運算式]** 清單，展開 **[所有銷售領域]**，按一下 **[北美洲]**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="80241-192">Open the **Filter Expression** list, expand **All Sales Territory**, click **North America**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="80241-193">此查詢現在有一個僅包含 [北美洲] 銷售額的篩選。</span><span class="sxs-lookup"><span data-stu-id="80241-193">The query now has a filter to include only sales in North America.</span></span>  
  
8.  <span data-ttu-id="80241-194">在 [量值群組] 窗格中，展開 Date，然後將 Calendar Year 拖曳至篩選窗格中的 [階層]\*\*\*\* 資料行。</span><span class="sxs-lookup"><span data-stu-id="80241-194">In the Measure Group pane, expand Date, and then drag Calendar Year to the **Hierarchy** column in the filter pane.</span></span>  
  
     <span data-ttu-id="80241-195">維度名稱 Date 就會自動新增至 [維度]\*\*\*\* 資料行。</span><span class="sxs-lookup"><span data-stu-id="80241-195">The dimension name, Date, is automatically added to the **Dimension** column.</span></span> <span data-ttu-id="80241-196">請勿變更 **[維度]** 或 **[運算子]** 資料行。</span><span class="sxs-lookup"><span data-stu-id="80241-196">Do not change the **Dimension** or **Operator** columns.</span></span>  
  
9. <span data-ttu-id="80241-197">若要開啟 **[篩選運算式]** 清單，按一下 **[篩選運算式]** 資料行。</span><span class="sxs-lookup"><span data-stu-id="80241-197">To open the **Filter Expression** list, click the down arrow in the **Filter Expression** column.</span></span>  
  
10. <span data-ttu-id="80241-198">在篩選運算式清單中，展開 **[所有日期]**，按一下 **[2009 年]**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="80241-198">In the filter expression list, expand **All Date**, click **Year 2009**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="80241-199">此查詢現在包含一個僅內含 2009 年日曆年度的篩選。</span><span class="sxs-lookup"><span data-stu-id="80241-199">The query now includes a filter to include only the calendar year 2009.</span></span>  
  
#### <a name="to-create-the-parameter"></a><span data-ttu-id="80241-200">若要建立參數</span><span class="sxs-lookup"><span data-stu-id="80241-200">To create the parameter</span></span>  
  
1.  <span data-ttu-id="80241-201">展開 Product 維度，然後將 Product Category Name 成員拖曳至 [階層]\*\*\*\* 資料行 (在 **Calendar Year** 底下)。</span><span class="sxs-lookup"><span data-stu-id="80241-201">Expand the Product dimension, and then drag the Product Category Name member to the **Hierarchy** column below **Calendar Year**.</span></span>  
  
2.  <span data-ttu-id="80241-202">開啟 **[篩選運算式]** 清單，按一下 **[所有產品]**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="80241-202">Open the **Filter Expression** list, click **All Products**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="80241-203">按一下 **[參數]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="80241-203">Click the **Parameter** checkbox.</span></span> <span data-ttu-id="80241-204">此查詢現在包含參數 ProductProductCategoryName。</span><span class="sxs-lookup"><span data-stu-id="80241-204">The query now includes the parameter ProductProductCategoryName.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="80241-205">此參數包含產品類別目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="80241-205">The parameter contains the names of product categories.</span></span> <span data-ttu-id="80241-206">當您按一下主報表中的產品類別目錄名稱時，系統會使用此參數將其名稱傳遞到鑽研報表。</span><span class="sxs-lookup"><span data-stu-id="80241-206">When you click a product category name in the main report, its name is passed to the drillthrough report by using this parameter.</span></span>  
  
###  <a name="to-create-the-dataset"></a><a name="DSkip"></a><span data-ttu-id="80241-207">若要建立資料集</span><span class="sxs-lookup"><span data-stu-id="80241-207">To create the dataset</span></span>  
  
1.  <span data-ttu-id="80241-208">從 Channel 維度中，將 Channel Name 拖曳至資料窗格。</span><span class="sxs-lookup"><span data-stu-id="80241-208">From the Channel dimension, drag Channel Name to the data pane.</span></span>  
  
2.  <span data-ttu-id="80241-209">從 Product 維度中，將 Product Category Name 拖曳到資料窗格，然後將其放置在 Channel Name 的右側。</span><span class="sxs-lookup"><span data-stu-id="80241-209">From the Product dimension, drag Product Category Name to the data pane, and then place it to the right of Channel Name.</span></span>  
  
3.  <span data-ttu-id="80241-210">從 Product 維度中，將 Product Subcategory Name 拖曳到資料窗格，然後將其放置在 Product Category Name 的右側。</span><span class="sxs-lookup"><span data-stu-id="80241-210">From the Product dimension, drag Product Subcategory Name to the data pane, and then place it to the right of Product Category Name.</span></span>  
  
4.  <span data-ttu-id="80241-211">在 [中繼資料] 窗格中，展開 [量值]\*\*\*\*，然後展開 Sales。</span><span class="sxs-lookup"><span data-stu-id="80241-211">In the Metadata pane, expand **Measure**, and then expand Sales.</span></span>  
  
5.  <span data-ttu-id="80241-212">將 Sales Amount 量值拖曳到資料窗格中，然後將其放置到 Product Subcategory Name 的右側。</span><span class="sxs-lookup"><span data-stu-id="80241-212">Drag the Sales Amount measure to the data pane, and then place it to the right of Product Subcategory Name.</span></span>  
  
6.  <span data-ttu-id="80241-213">在查詢設計工具工具列上，按一下 **[執行 (!)]**。</span><span class="sxs-lookup"><span data-stu-id="80241-213">On the query designer toolbar, click **Run (!)**.</span></span>  
  
7.  <span data-ttu-id="80241-214">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="80241-214">Click **Next**.</span></span>  
  
##  <a name="1c-organize-data-into-groups"></a><a name="DLayout"></a><span data-ttu-id="80241-215">1c.</span><span class="sxs-lookup"><span data-stu-id="80241-215">1c.</span></span> <span data-ttu-id="80241-216">將資料組織為群組</span><span class="sxs-lookup"><span data-stu-id="80241-216">Organize Data into Groups</span></span>  
 <span data-ttu-id="80241-217">當您選取將資料分組的欄位時，會設計包含資料列和資料行的矩陣，以顯示詳細資料和彙總資料。</span><span class="sxs-lookup"><span data-stu-id="80241-217">When you select the fields on which to group the data, you design a matrix with rows and columns that displays detail and aggregated data.</span></span>  
  
#### <a name="to-organize-data-into-groups"></a><span data-ttu-id="80241-218">若要將資料組織為群組</span><span class="sxs-lookup"><span data-stu-id="80241-218">To organize data into groups</span></span>  
  
1.  <span data-ttu-id="80241-219">若要切換成 [設計] 檢視，按一下 **[設計]**。</span><span class="sxs-lookup"><span data-stu-id="80241-219">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="80241-220">在 [排列欄位]\*\*\*\* 頁面上，將 Product_Subcategory_Name 拖曳至 [資料列群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="80241-220">On the **Arrange fields** page, drag Product_Subcategory_Name to **Row groups**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="80241-221">名稱中的空格會以底線 (_) 取代。</span><span class="sxs-lookup"><span data-stu-id="80241-221">The spaces in the names are replaced with underscores (_).</span></span> <span data-ttu-id="80241-222">例如，Product Category Name 是 Product_Category_Name。</span><span class="sxs-lookup"><span data-stu-id="80241-222">For example Product Category Name is Product_Category_Name.</span></span>  
  
3.  <span data-ttu-id="80241-223">將 Channel_Name 拖曳至 [資料行群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="80241-223">Drag Channel_Name to **Column groups**.</span></span>  
  
4.  <span data-ttu-id="80241-224">將 Sales_Amount 拖曳至 [值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="80241-224">Drag Sales_Amount to **Values**.</span></span>  
  
     <span data-ttu-id="80241-225">Sum 函數 (數值欄位的預設彙總) 會自動彙總 Sales_Amount。</span><span class="sxs-lookup"><span data-stu-id="80241-225">Sales_Amount is automatically aggregated by the Sum function, the default aggregate for numeric fields.</span></span> <span data-ttu-id="80241-226">值為 `[Sum(Sales_Amount)]`。</span><span class="sxs-lookup"><span data-stu-id="80241-226">The value is `[Sum(Sales_Amount)]`.</span></span>  
  
     <span data-ttu-id="80241-227">若要檢視其他可用的彙總函式，開啟下拉式清單 (不要變更彙總函式)。</span><span class="sxs-lookup"><span data-stu-id="80241-227">To view the other aggregate functions available, open the drop-down list (do not change the aggregate function).</span></span>  
  
5.  <span data-ttu-id="80241-228">將 Sales_Return_Amount 拖曳至 [值]\*\*\*\*，並將其放置在 `[Sum(Sales_Amount)]` 之下。</span><span class="sxs-lookup"><span data-stu-id="80241-228">Drag Sales_Return_Amount to **Values**, and then place it below `[Sum(Sales_Amount)]`.</span></span>  
  
     <span data-ttu-id="80241-229">步驟 4 和步驟 5 指定了矩陣中要顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="80241-229">Steps 4 and 5 specify the data to display in the matrix.</span></span>  
  
6.  <span data-ttu-id="80241-230">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="80241-230">Click **Next**.</span></span>  
  
##  <a name="1d-add-subtotals-and-totals"></a><a name="DTotals"></a><span data-ttu-id="80241-231">1d.</span><span class="sxs-lookup"><span data-stu-id="80241-231">1d.</span></span> <span data-ttu-id="80241-232">加入小計和總計</span><span class="sxs-lookup"><span data-stu-id="80241-232">Add Subtotals and Totals</span></span>  
 <span data-ttu-id="80241-233">建立群組之後，您可以加入並格式化要顯示欄位彙總值的資料列。</span><span class="sxs-lookup"><span data-stu-id="80241-233">After you create groups, you can add and format rows where the aggregate values for the fields will display.</span></span> <span data-ttu-id="80241-234">您也可以選擇要顯示所有資料，或是讓使用者以互動方式展開和摺疊分組資料。</span><span class="sxs-lookup"><span data-stu-id="80241-234">You can also choose whether to show all the data or to let a user expand and collapse grouped data interactively.</span></span>  
  
#### <a name="to-add-subtotals-and-totals"></a><span data-ttu-id="80241-235">加入小計和總計</span><span class="sxs-lookup"><span data-stu-id="80241-235">To add subtotals and totals</span></span>  
  
1.  <span data-ttu-id="80241-236">在 [**選擇版面**配置] 頁面的 [**選項**] 底下，確認已選取 [**顯示小計和總計**]。</span><span class="sxs-lookup"><span data-stu-id="80241-236">On the **Choose the layout** page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
     <span data-ttu-id="80241-237">精靈的 [預覽] 窗格會顯示含有四個資料列的矩陣。</span><span class="sxs-lookup"><span data-stu-id="80241-237">The wizard Preview pane displays a matrix with four rows.</span></span>  
  
2.  <span data-ttu-id="80241-238">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="80241-238">Click **Next**.</span></span>  
  
##  <a name="1e-choose-a-style"></a><a name="DStyle"></a><span data-ttu-id="80241-239">1e.</span><span class="sxs-lookup"><span data-stu-id="80241-239">1e.</span></span> <span data-ttu-id="80241-240">選擇樣式</span><span class="sxs-lookup"><span data-stu-id="80241-240">Choose a Style</span></span>  
 <span data-ttu-id="80241-241">樣式會指定字型樣式、色彩集和框線樣式。</span><span class="sxs-lookup"><span data-stu-id="80241-241">A style specifies a font style, a set of colors, and a border style.</span></span>  
  
#### <a name="to-specify-a-style"></a><span data-ttu-id="80241-242">若要指定樣式</span><span class="sxs-lookup"><span data-stu-id="80241-242">To specify a style</span></span>  
  
1.  <span data-ttu-id="80241-243">在 [**選擇樣式**] 頁面的 [樣式] 窗格中，選取 [石板]。</span><span class="sxs-lookup"><span data-stu-id="80241-243">On the **Choose a Style** page, in the Styles pane, select Slate.</span></span>  
  
2.  <span data-ttu-id="80241-244">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="80241-244">Click **Finish**.</span></span>  
  
     <span data-ttu-id="80241-245">資料表會加入至設計介面。</span><span class="sxs-lookup"><span data-stu-id="80241-245">The table is added to the design surface.</span></span>  
  
3.  <span data-ttu-id="80241-246">若要預覽報表，按一下 **[執行 (!)]**。</span><span class="sxs-lookup"><span data-stu-id="80241-246">To preview the report, click **Run (!)**.</span></span>  
  
##  <a name="2-format-data-as-currency"></a><a name="DFormat"></a><span data-ttu-id="80241-247">2. 將資料格式化為貨幣</span><span class="sxs-lookup"><span data-stu-id="80241-247">2. Format Data as Currency</span></span>  
 <span data-ttu-id="80241-248">將貨幣格式套用到鑽研報表中的銷售量欄位。</span><span class="sxs-lookup"><span data-stu-id="80241-248">Apply currency formatting to the sales amount fields in the drillthrough report.</span></span>  
  
#### <a name="to-format-data-as-currency"></a><span data-ttu-id="80241-249">若要將資料格式化為貨幣</span><span class="sxs-lookup"><span data-stu-id="80241-249">To format data as currency</span></span>  
  
1.  <span data-ttu-id="80241-250">若要切換成 [設計] 檢視，按一下 **[設計]**。</span><span class="sxs-lookup"><span data-stu-id="80241-250">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="80241-251">若要一次選取並格式化多個資料格，按下 Ctrl 鍵，然後選取包含數值銷售資料的資料格。</span><span class="sxs-lookup"><span data-stu-id="80241-251">To select and format multiple cells at one time, press the Ctrl key, and then select the cells that contain the numeric sales data.</span></span>  
  
3.  <span data-ttu-id="80241-252">在 **[主資料夾]** 索引標籤的 **[數值]** 群組中，按一下 **[貨幣]**。</span><span class="sxs-lookup"><span data-stu-id="80241-252">On the **Home** tab, in the **Number** group, click **Currency**.</span></span>  
  
##  <a name="3-add-columns-to-show-sales-values-in-sparklines"></a><a name="DSparkline"></a><span data-ttu-id="80241-253">3. 加入資料行以便在走勢圖中顯示銷售值</span><span class="sxs-lookup"><span data-stu-id="80241-253">3. Add Columns to Show Sales Values in Sparklines</span></span>  
 <span data-ttu-id="80241-254">報表會顯示走勢圖中的值，而不會將銷售額與銷售報酬顯示為貨幣值。</span><span class="sxs-lookup"><span data-stu-id="80241-254">Instead of showing sales and sales returns as currency values, the report shows the values in a sparkline.</span></span>  
  
#### <a name="to-add-sparklines-to-columns"></a><span data-ttu-id="80241-255">若要將走勢圖加入至資料行</span><span class="sxs-lookup"><span data-stu-id="80241-255">To add sparklines to columns</span></span>  
  
1.  <span data-ttu-id="80241-256">若要切換成 [設計] 檢視，按一下 **[設計]**。</span><span class="sxs-lookup"><span data-stu-id="80241-256">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="80241-257">在矩陣的 [總計] 群組中，以滑鼠右鍵按一下 **[銷售量]** 資料行，按一下 **[插入資料行]**，然後按一下 **[右方]**。</span><span class="sxs-lookup"><span data-stu-id="80241-257">In the Total group of the matrix, right-click the **Sales Amount** column, click **Insert Column**, and then click **Right**.</span></span>  
  
     <span data-ttu-id="80241-258">空白資料行就會加入至 **[銷售量]** 的右方。</span><span class="sxs-lookup"><span data-stu-id="80241-258">An empty column is added to the right of **Sales Amount**.</span></span>  
  
3.  <span data-ttu-id="80241-259">在功能區上，按一下 [矩形]\*\*\*\*，然後按一下 [Product_Subcategory] 資料列群組中 `[Sum(Sales_Amount)]` 資料格右側的空資料格。</span><span class="sxs-lookup"><span data-stu-id="80241-259">On the ribbon, click **Rectangle**, and then click the empty cell to the right of the `[Sum(Sales_Amount)]` cell in the [Product_Subcategory] row group.</span></span>  
  
4.  <span data-ttu-id="80241-260">在功能區上，按一下 **[走勢圖]** 圖示，然後按一下加入矩形的資料格。</span><span class="sxs-lookup"><span data-stu-id="80241-260">On the ribbon, click the **Sparkline** icon, and then click the cell where the rectangle was added.</span></span>  
  
5.  <span data-ttu-id="80241-261">在 **[選取走勢圖類型]** 對話方塊中，確認已選取 **[資料行]** 類型。</span><span class="sxs-lookup"><span data-stu-id="80241-261">In the **Select Sparkline Type** dialog box, verify that **Column** type is selected.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="80241-262">以滑鼠右鍵按一下走勢圖。</span><span class="sxs-lookup"><span data-stu-id="80241-262">Right-click the sparkline.</span></span>  
  
8.  <span data-ttu-id="80241-263">在 [圖表資料] 窗格中，按一下**新增欄位**圖示，然後按一下 [Sales_Amount]。</span><span class="sxs-lookup"><span data-stu-id="80241-263">In the Chart Data pane, click the **Add field** icon, and then click Sales_Amount.</span></span>  
  
9. <span data-ttu-id="80241-264">以滑鼠右鍵按一下 `Sales_Return_Amount` 資料行，然後將資料行加入至該資料行的右側。</span><span class="sxs-lookup"><span data-stu-id="80241-264">Right-click the `Sales_Return_Amount` column, and then add a column to the right of it.</span></span>  
  
10. <span data-ttu-id="80241-265">重複步驟 2 至 6。</span><span class="sxs-lookup"><span data-stu-id="80241-265">Repeat steps 2 through 6.</span></span>  
  
11. <span data-ttu-id="80241-266">以滑鼠右鍵按一下走勢圖。</span><span class="sxs-lookup"><span data-stu-id="80241-266">Right-click the sparkline.</span></span>  
  
12. <span data-ttu-id="80241-267">在 [圖表資料] 窗格中，按一下**新增欄位** 圖示，然後按一下 [Sales_Return_Amount]。</span><span class="sxs-lookup"><span data-stu-id="80241-267">In the Chart Data pane, click the **Add field** icon, and then click Sales_Return_Amount.</span></span>  
  
13. <span data-ttu-id="80241-268">若要預覽報表，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="80241-268">To preview the report, click **Run**.</span></span>  
  
##  <a name="4-add-report-title-with-product-category-name"></a><a name="DReportTitle"></a><span data-ttu-id="80241-269">4. 加入具有產品類別目錄名稱的報表標題</span><span class="sxs-lookup"><span data-stu-id="80241-269">4. Add Report Title with Product Category Name</span></span>  
 <span data-ttu-id="80241-270">報表標題會出現在報表的頂端。</span><span class="sxs-lookup"><span data-stu-id="80241-270">A report title appears at the top of the report.</span></span> <span data-ttu-id="80241-271">您可以將報表標題放置在報表頁首，如果報表不使用報表頁首，則可以放置在報表主體頂端的文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="80241-271">You can place the report title in a report header or, if the report does not use one, in a text box at the top of the report body.</span></span> <span data-ttu-id="80241-272">在本教學課程中，您將使用自動放置在報表主體頂端的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="80241-272">In this tutorial, you will use the text box that is automatically placed at the top of the report body.</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="80241-273">若要加入報表標題</span><span class="sxs-lookup"><span data-stu-id="80241-273">To add a report title</span></span>  
  
1.  <span data-ttu-id="80241-274">若要切換成 [設計] 檢視，按一下 **[設計]**。</span><span class="sxs-lookup"><span data-stu-id="80241-274">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="80241-275">在設計介面上，按一下 **[按一下以加入標題]**。</span><span class="sxs-lookup"><span data-stu-id="80241-275">On the design surface, click **Click to add title**.</span></span>  
  
3.  <span data-ttu-id="80241-276">輸入 **Sales and Returns for Category:**。</span><span class="sxs-lookup"><span data-stu-id="80241-276">Type **Sales and Returns for Category:**.</span></span>  
  
4.  <span data-ttu-id="80241-277">以滑鼠右鍵按一下，然後按一下 **[建立預留位置]**。</span><span class="sxs-lookup"><span data-stu-id="80241-277">Right-click, and then click **Create Placeholder**.</span></span>  
  
5.  <span data-ttu-id="80241-278">按一下 **[值]** 清單右側的 **(fx)** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="80241-278">Click the **(fx)** button to the right of the **Value** list.</span></span>  
  
6.  <span data-ttu-id="80241-279">在 **[運算式]** 對話方塊的 [類別目錄] 窗格中，按一下 **[資料集]**，然後在 **[值]** 清單中，按兩下 `First(Product_Category_Name)`。</span><span class="sxs-lookup"><span data-stu-id="80241-279">In the **Expression** dialog box, in the Category pane, click **Dataset**, and then in the **Values** list double-click `First(Product_Category_Name)`.</span></span>  
  
     <span data-ttu-id="80241-280">**[運算式]** 方塊包含下列運算式：</span><span class="sxs-lookup"><span data-stu-id="80241-280">The **Expression** box contains the following expression:</span></span>  
  
    ```  
    =First(Fields!Product_Category_Name.Value, "DataSet1")  
    ```  
  
7.  <span data-ttu-id="80241-281">若要預覽報表，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="80241-281">To preview the report, click **Run**.</span></span>  
  
 <span data-ttu-id="80241-282">報表標題包含第一個產品類別目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="80241-282">The report title includes the name of the first product category.</span></span> <span data-ttu-id="80241-283">稍後，在您當做鑽研報表執行此報表之後，產品類別目錄名稱將會動態變更，以反映在主報表中按下之產品類別目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="80241-283">Later, after you run this report as a drillthrough report, the product category name will dynamically change to reflect the name of the product category that was clicked in the main report.</span></span>  
  
##  <a name="5-update-parameter-properties"></a><a name="DParameter"></a><span data-ttu-id="80241-284">5. 更新參數屬性</span><span class="sxs-lookup"><span data-stu-id="80241-284">5. Update Parameter Properties</span></span>  
 <span data-ttu-id="80241-285">參數預設是可見的，但不適合這個報表。</span><span class="sxs-lookup"><span data-stu-id="80241-285">By default parameters are visible, which is not appropriate for this report.</span></span> <span data-ttu-id="80241-286">您將要更新鑽研報表的參數屬性。</span><span class="sxs-lookup"><span data-stu-id="80241-286">You will update the parameter properties for the drillthrough report.</span></span>  
  
#### <a name="to-hide-a-parameter"></a><span data-ttu-id="80241-287">若要隱藏參數</span><span class="sxs-lookup"><span data-stu-id="80241-287">To hide a parameter</span></span>  
  
1.  <span data-ttu-id="80241-288">在 [報表資料] 窗格中，展開 **[參數]**。</span><span class="sxs-lookup"><span data-stu-id="80241-288">In the Report Data pane, expand **Parameters**.</span></span>  
  
2.  <span data-ttu-id="80241-289">以滑鼠右鍵按一下 [ \@ ProductProductCategoryName]，然後按一下 [**參數屬性**]。</span><span class="sxs-lookup"><span data-stu-id="80241-289">Right-click \@ProductProductCategoryName, and then click **Parameter Properties**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="80241-290">名稱旁邊的 \@ 字元表示這是一個參數。</span><span class="sxs-lookup"><span data-stu-id="80241-290">The \@ character next to the name indicates that this is a parameter.</span></span>  
  
3.  <span data-ttu-id="80241-291">在 **[一般]** 索引標籤上，按一下 **[隱藏]**。</span><span class="sxs-lookup"><span data-stu-id="80241-291">On the **General** tab, click **Hidden**.</span></span>  
  
4.  <span data-ttu-id="80241-292">在 **[提示]** 方塊中，輸入 **Product Category**。</span><span class="sxs-lookup"><span data-stu-id="80241-292">In the **Prompt** box, type **Product Category**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="80241-293">參數是隱藏的，因此絕不會使用這個提示。</span><span class="sxs-lookup"><span data-stu-id="80241-293">Because the parameter is hidden, this prompt is never used.</span></span>  
  
5.  <span data-ttu-id="80241-294">或者，按一下 **[可用的值]** 和 **[預設值]** ，然後檢閱其選項。</span><span class="sxs-lookup"><span data-stu-id="80241-294">Optionally, click **Available Values** and **Default Values** and review their options.</span></span> <span data-ttu-id="80241-295">請不要變更這些索引標籤上的任何選項。</span><span class="sxs-lookup"><span data-stu-id="80241-295">Do not change any options on these tabs.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="6-save-the-report-to-a-sharepoint-library"></a><a name="DSave"></a><span data-ttu-id="80241-296">6. 將報表儲存至 SharePoint 文件庫</span><span class="sxs-lookup"><span data-stu-id="80241-296">6. Save the Report to a SharePoint Library</span></span>  
 <span data-ttu-id="80241-297">您可以將報表儲存至 SharePoint 文件庫、報表伺服器或您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="80241-297">You can save the report to a SharePoint library, report server, or your computer.</span></span> <span data-ttu-id="80241-298">如果將報表儲存到您的電腦，就無法使用數個 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能，例如報表組件和子報表。</span><span class="sxs-lookup"><span data-stu-id="80241-298">If you save the report to your computer, a number of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features such as report parts and subreports are not available.</span></span> <span data-ttu-id="80241-299">在本教學課程中，您會將報表儲存至 SharePoint 程式庫。</span><span class="sxs-lookup"><span data-stu-id="80241-299">In this tutorial, you will save the report to a SharePoint library.</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="80241-300">若要儲存報表</span><span class="sxs-lookup"><span data-stu-id="80241-300">To save the report</span></span>  
  
1.  <span data-ttu-id="80241-301">在報表產生器的按鈕中，按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="80241-301">From the Report Builder button, click **Save**.</span></span> <span data-ttu-id="80241-302">**[另存為報表]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="80241-302">The **Save As Report** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="80241-303">如果您重新儲存報表，報表會自動重新儲存到之前的位置。</span><span class="sxs-lookup"><span data-stu-id="80241-303">If you are resaving a report, it is automatically resaved to its previous location.</span></span> <span data-ttu-id="80241-304">若要變更位置，使用 **[另存新檔]** 選項。</span><span class="sxs-lookup"><span data-stu-id="80241-304">To change the location, use the **Save As** option.</span></span>  
  
2.  <span data-ttu-id="80241-305">若要顯示最近使用過的報表伺服器和 SharePoint 網站清單，按一下 **[最近使用的網站和伺服器]**。</span><span class="sxs-lookup"><span data-stu-id="80241-305">To show a list of recently used report servers and SharePoint sites, click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="80241-306">選取或輸入您有權儲存報表之 SharePoint 網站的名稱。</span><span class="sxs-lookup"><span data-stu-id="80241-306">Select or type the name of the SharePoint site where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="80241-307">SharePoint 文件庫的 URL 具有下列語法：</span><span class="sxs-lookup"><span data-stu-id="80241-307">The URL of the SharePoint library has the following syntax:</span></span>  
  
    ```  
    Http://<ServerName>/<Sites>/  
    ```  
  
4.  <span data-ttu-id="80241-308">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="80241-308">Click **Save**.</span></span>  
  
     <span data-ttu-id="80241-309">**[最近使用的網站和伺服器]** 會列出 SharePoint 網站上的文件庫。</span><span class="sxs-lookup"><span data-stu-id="80241-309">**Recent Sites and Servers** lists the libraries on the SharePoint site.</span></span>  
  
5.  <span data-ttu-id="80241-310">導覽到您將儲存報表的文件庫。</span><span class="sxs-lookup"><span data-stu-id="80241-310">Navigate to the library where you will save the report.</span></span>  
  
6.  <span data-ttu-id="80241-311">在 **[名稱]** 方塊中，將預設名稱取代為 **ResellerVSOnlineDrillthrough**。</span><span class="sxs-lookup"><span data-stu-id="80241-311">In the **Name** box, replace the default name with **ResellerVSOnlineDrillthrough**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="80241-312">您會將主報表儲存至相同的位置。</span><span class="sxs-lookup"><span data-stu-id="80241-312">You will save the main report to the same location.</span></span> <span data-ttu-id="80241-313">如果您想要將主報表和鑽研報表儲存到不同的網站或文件庫，必須在主報表中更新 **[移至報表]** 動作的路徑。</span><span class="sxs-lookup"><span data-stu-id="80241-313">If you want to save the main and drillthrough reports to different sites or libraries, you must update the path of the **Go to report** action in the main report.</span></span>  
  
7.  <span data-ttu-id="80241-314">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="80241-314">Click **Save**.</span></span>  
  
##  <a name="1-create-a-new-report-from-the-table-or-matrix-wizard"></a><a name="MMatrixAndDataset"></a><span data-ttu-id="80241-315">1. 從資料表或矩陣 Wizard 建立新的報表</span><span class="sxs-lookup"><span data-stu-id="80241-315">1. Create a New Report from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="80241-316">從 **[使用者入門]** 對話方塊中，使用 **[資料表或矩陣精靈]** 建立矩陣報表。</span><span class="sxs-lookup"><span data-stu-id="80241-316">From the **Getting Started** dialog box, create a matrix report by using the **Table or Matrix Wizard**.</span></span>  
  
#### <a name="to-create-a-new-report"></a><span data-ttu-id="80241-317">建立新的報表</span><span class="sxs-lookup"><span data-stu-id="80241-317">To create a new report</span></span>  
  
1.  <span data-ttu-id="80241-318">按一下 [ **開始**]、依序指向 [ **程式集**] 和 [ [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **報表產生器**]，然後按一下 [ **報表產生器**]。</span><span class="sxs-lookup"><span data-stu-id="80241-318">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Report Builder**, and then click **Report Builder**.</span></span>  
  
2.  <span data-ttu-id="80241-319">在 **[使用者入門]** 對話方塊中，確認已選取 **[新增報表]** ，然後按一下 **[資料表或矩陣精靈]**。</span><span class="sxs-lookup"><span data-stu-id="80241-319">In the **Getting Started** dialog box, verify that **New Report** is selected, and then click **Table or Matrix Wizard**.</span></span>  
  
##  <a name="1a-specify-a-data-connection"></a><a name="MConnection"></a><span data-ttu-id="80241-320">1a.</span><span class="sxs-lookup"><span data-stu-id="80241-320">1a.</span></span> <span data-ttu-id="80241-321">指定資料連接</span><span class="sxs-lookup"><span data-stu-id="80241-321">Specify a Data Connection</span></span>  
 <span data-ttu-id="80241-322">您會將內嵌的資料來源儲存到主報表。</span><span class="sxs-lookup"><span data-stu-id="80241-322">You will add an embedded data source to the main report.</span></span>  
  
#### <a name="to-create-an-embedded-data-source"></a><span data-ttu-id="80241-323">建立內嵌資料來源</span><span class="sxs-lookup"><span data-stu-id="80241-323">To create an embedded data source</span></span>  
  
1.  <span data-ttu-id="80241-324">在 **[選擇資料集]** 頁面上，選取 **[建立資料集]**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="80241-324">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="80241-325">按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="80241-325">Click **New**.</span></span>  
  
3.  <span data-ttu-id="80241-326">在 **[名稱]** 中輸入 **Online and Reseller Sales Main** 做為資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="80241-326">In **Name**, type **Online and Reseller Sales Main** as the name for the data source.</span></span>  
  
4.  <span data-ttu-id="80241-327">在 **[選取連接類型]** 中，選取 **[Microsoft SQL Server Analysis Services]**，然後按一下 **[建立]**。</span><span class="sxs-lookup"><span data-stu-id="80241-327">In **Select a connection type**, select **Microsoft SQL Server Analysis Services**, and then click **Build**.</span></span>  
  
5.  <span data-ttu-id="80241-328">在 **[資料來源]** 中，確認資料來源為 **[Microsoft SQL Server Analysis Services (AdomdClient)]**。</span><span class="sxs-lookup"><span data-stu-id="80241-328">In **Data source**, verify that the data source is **Microsoft SQL Server Analysis Services (AdomdClient)**.</span></span>  
  
6.  <span data-ttu-id="80241-329">在 [**伺服器名稱**] 中，輸入安裝實例所在伺服器的名稱 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="80241-329">In **Server name**, type the name of a server where an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] is installed.</span></span>  
  
7.  <span data-ttu-id="80241-330">在 [選取或輸入資料庫名稱]\*\*\*\* 中，選取 [Contoso] Cube。</span><span class="sxs-lookup"><span data-stu-id="80241-330">In **Select or enter a database name**, select the Contoso cube.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. <span data-ttu-id="80241-331">確認 **[連接字串]** 包含下列語法：</span><span class="sxs-lookup"><span data-stu-id="80241-331">Verify that the **Connection string** contains the following syntax:</span></span>  
  
    ```  
    Data Source=<servername>; Initial Catalog = Contoso  
    ```  
  
10. <span data-ttu-id="80241-332">按一下 **[認證類型]**。</span><span class="sxs-lookup"><span data-stu-id="80241-332">Click **Credentials type**.</span></span>  
  
     <span data-ttu-id="80241-333">根據如何設定資料來源的權限而定，您可能需要變更預設的驗證。</span><span class="sxs-lookup"><span data-stu-id="80241-333">Depending on how permissions are configured on the data source, you might need to change the default authentication.</span></span>  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. <span data-ttu-id="80241-334">若要確認您能夠連接至資料來源，請按一下 **[測試連接]**。</span><span class="sxs-lookup"><span data-stu-id="80241-334">To verify that you can connect to the data source, click **Test Connection**.</span></span>  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
14. <span data-ttu-id="80241-335">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="80241-335">Click **Next**.</span></span>  
  
##  <a name="1b-create-an-mdx-query"></a><a name="MMDXQuery"></a><span data-ttu-id="80241-336">1a-1b.</span><span class="sxs-lookup"><span data-stu-id="80241-336">1b.</span></span> <span data-ttu-id="80241-337">建立 MDX 查詢</span><span class="sxs-lookup"><span data-stu-id="80241-337">Create an MDX Query</span></span>  
 <span data-ttu-id="80241-338">接著，建立內嵌的資料集。</span><span class="sxs-lookup"><span data-stu-id="80241-338">Next, create an embedded dataset.</span></span> <span data-ttu-id="80241-339">若要這樣做，您將使用查詢設計工具建立篩選、參數、導出成員，以及資料集本身。</span><span class="sxs-lookup"><span data-stu-id="80241-339">To do so, you will use the query designer to create filters, parameters, and calculated members as well as the dataset itself.</span></span>  
  
#### <a name="to-create-query-filters"></a><span data-ttu-id="80241-340">若要建立查詢篩選</span><span class="sxs-lookup"><span data-stu-id="80241-340">To create query filters</span></span>  
  
1.  <span data-ttu-id="80241-341">在 [**設計查詢**] 頁面的 [中繼資料] 窗格中，按一下 [cube] 區段中的省略號\*\* ( ...] ) \*\*。</span><span class="sxs-lookup"><span data-stu-id="80241-341">On the **Design a query** page, in the Metadata pane, in the cube section, click the ellipsis **(...)**.</span></span>  
  
2.  <span data-ttu-id="80241-342">在 [選取 Cube]\*\*\*\* 對話方塊中，按一下 [Sales]，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="80241-342">In the **Cube Selection** dialog box, click Sales, and then click **OK**.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="80241-343">如果您不想要手動建置 MDX 查詢，請按一下![切換到設計模式](media/rsqdicon-designmode.gif "切換到設計模式")圖示，將查詢設計工具切換到 [查詢] 模式，並將完成的 MDX 貼到查詢設計工具，然後繼續進行[建立資料集](#MSkip)中的步驟 5。</span><span class="sxs-lookup"><span data-stu-id="80241-343">If you do not want to build the MDX query manually, click the ![Switch to Design mode](media/rsqdicon-designmode.gif "Switch to Design mode") icon, toggle the query designer to Query mode, paste the completed MDX to the query designer, and then proceed to step 5 in [To create the dataset](#MSkip).</span></span>  
  
    ```  
    WITH MEMBER [Measures].[Net QTY] AS [Measures].[Sales Quantity] -[Measures].[Sales Return Quantity] MEMBER [Measures].[Net Sales] AS [Measures].[Sales Amount] - [Measures].[Sales Return Amount] SELECT NON EMPTY { [Measures].[Net QTY], [Measures].[Net Sales] } ON COLUMNS, NON EMPTY { ([Channel].[Channel Name].[Channel Name].ALLMEMBERS * [Product].[Product Category Name].[Product Category Name].ALLMEMBERS ) } DIMENSION PROPERTIES MEMBER_CAPTION, MEMBER_UNIQUE_NAME ON ROWS FROM ( SELECT ( { [Date].[Calendar Year].&[2009] } ) ON COLUMNS FROM ( SELECT ( STRTOSET(@ProductProductCategoryName, CONSTRAINED) ) ON COLUMNS FROM ( SELECT ( { [Sales Territory].[Sales Territory Group].&[North America] } ) ON COLUMNS FROM ( SELECT ( { [Channel].[Channel Name].&[2], [Channel].[Channel Name].&[4] } ) ON COLUMNS FROM [Sales])))) WHERE ( [Sales Territory].[Sales Territory Group].&[North America], [Date].[Calendar Year].&[2009] ) CELL PROPERTIES VALUE, BACK_COLOR, FORE_COLOR, FORMATTED_VALUE, FORMAT_STRING, FONT_NAME, FONT_SIZE, FONT_FLAGSQuery text: Code.  
    ```  
  
3.  <span data-ttu-id="80241-344">在 [量值群組] 窗格中，展開 Channel，然後將 Channel Name 拖曳到篩選窗格中的 [階層]\*\*\*\* 資料行。</span><span class="sxs-lookup"><span data-stu-id="80241-344">In the Measure Group pane, expand Channel, and then drag Channel Name to the **Hierarchy** column in the filter pane.</span></span>  
  
     <span data-ttu-id="80241-345">維度名稱 Channel 就會自動新增至 [維度]\*\*\*\* 資料行。</span><span class="sxs-lookup"><span data-stu-id="80241-345">The dimension name, Channel, is automatically added to the **Dimension** column.</span></span> <span data-ttu-id="80241-346">請勿變更 **[維度]** 或 **[運算子]** 資料行。</span><span class="sxs-lookup"><span data-stu-id="80241-346">Do not change the **Dimension** or **Operator** columns.</span></span>  
  
4.  <span data-ttu-id="80241-347">若要開啟 **[篩選運算式]** 清單，按一下 **[篩選運算式]** 資料行。</span><span class="sxs-lookup"><span data-stu-id="80241-347">To open the **Filter Expression** list, click the down arrow in the **Filter Expression** column.</span></span>  
  
5.  <span data-ttu-id="80241-348">在篩選運算式清單中，展開 **[所有通道]**，然後依序按一下 **[線上]** 、 **[轉售商]** 和 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="80241-348">In the filter expression list, expand **All Channel**, click **Online** and **Reseller**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="80241-349">此查詢現在包含一個僅內含下列通道的篩選：線上和轉售商。</span><span class="sxs-lookup"><span data-stu-id="80241-349">The query now includes a filter to include only these channels: Online and Reseller.</span></span>  
  
6.  <span data-ttu-id="80241-350">展開 [銷售領域] 維度，然後將 [銷售領域] 群組拖曳**至 [階層**] 資料行（在 [**通道名稱**] 底下）。</span><span class="sxs-lookup"><span data-stu-id="80241-350">Expand the Sales Territory dimension, and then drag Sales Territory Group to the **Hierarchy** column, below **Channel Name**.</span></span>  
  
7.  <span data-ttu-id="80241-351">開啟 **[篩選運算式]** 清單，展開 **[所有銷售領域]**，按一下 **[北美洲]**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="80241-351">Open the **Filter Expression** list, expand **All Sales Territory**, click **North America**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="80241-352">此查詢現在有一個僅包含 [北美洲] 銷售額的篩選。</span><span class="sxs-lookup"><span data-stu-id="80241-352">The query now has a filter to include only sales in North America.</span></span>  
  
8.  <span data-ttu-id="80241-353">在 [量值群組] 窗格中，展開 Date，然後將 Calendar Year 拖曳至篩選窗格中的 [階層]\*\*\*\* 資料行。</span><span class="sxs-lookup"><span data-stu-id="80241-353">In the Measure Group pane, expand Date, and drag Calendar Year to the **Hierarchy** column in the filter pane.</span></span>  
  
     <span data-ttu-id="80241-354">維度名稱 Date 就會自動新增至 [維度]\*\*\*\* 資料行。</span><span class="sxs-lookup"><span data-stu-id="80241-354">The dimension name, Date, is automatically added to the **Dimension** column.</span></span> <span data-ttu-id="80241-355">請勿變更 **[維度]** 或 **[運算子]** 資料行。</span><span class="sxs-lookup"><span data-stu-id="80241-355">Do not change the **Dimension** or **Operator** columns.</span></span>  
  
9. <span data-ttu-id="80241-356">若要開啟 **[篩選運算式]** 清單，按一下 **[篩選運算式]** 資料行。</span><span class="sxs-lookup"><span data-stu-id="80241-356">To open the **Filter Expression** list, click the down arrow in the **Filter Expression** column.</span></span>  
  
10. <span data-ttu-id="80241-357">在篩選運算式清單中，展開 **[所有日期]**，按一下 **[2009 年]**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="80241-357">In the filter expression list, expand **All Date**, click **Year 2009**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="80241-358">此查詢現在包含一個僅內含 2009 年日曆年度的篩選。</span><span class="sxs-lookup"><span data-stu-id="80241-358">The query now includes a filter to include only the calendar year 2009.</span></span>  
  
#### <a name="to-create-the-parameter"></a><span data-ttu-id="80241-359">若要建立參數</span><span class="sxs-lookup"><span data-stu-id="80241-359">To create the parameter</span></span>  
  
1.  <span data-ttu-id="80241-360">展開 Product 維度，然後將 Product Category Name 拖曳至 [階層]\*\*\*\* 資料行 (在 **Sales Territory Group** 底下)。</span><span class="sxs-lookup"><span data-stu-id="80241-360">Expand the Product dimension, and then drag the Product Category Name member to the **Hierarchy** column below **Sales Territory Group**.</span></span>  
  
2.  <span data-ttu-id="80241-361">開啟 **[篩選運算式]** 清單，按一下 **[所有產品]**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="80241-361">Open the **Filter Expression** list, click **All Products**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="80241-362">按一下 **[參數]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="80241-362">Click the **Parameter** checkbox.</span></span> <span data-ttu-id="80241-363">此查詢現在包含參數 ProductProductCategoryName。</span><span class="sxs-lookup"><span data-stu-id="80241-363">The query now includes the parameter ProductProductCategoryName.</span></span>  
  
#### <a name="to-create-calculated-members"></a><span data-ttu-id="80241-364">若要建立導出成員</span><span class="sxs-lookup"><span data-stu-id="80241-364">To create calculated members</span></span>  
  
1.  <span data-ttu-id="80241-365">將游標放在 [導出成員] 窗格內部，按一下滑鼠右鍵，然後按一下 **[新增導出成員]**。</span><span class="sxs-lookup"><span data-stu-id="80241-365">Place the cursor inside the Calculated Members pane, right-click, and then click **New Calculated Member**.</span></span>  
  
2.  <span data-ttu-id="80241-366">在 [中繼資料] 窗格中，展開 [**量值**]，然後展開 [Sales]。</span><span class="sxs-lookup"><span data-stu-id="80241-366">In the Metadata pane, expand **Measures** and then expand Sales.</span></span>  
  
3.  <span data-ttu-id="80241-367">將 Sales Quantity 量值拖曳至 [運算式]\*\*\*\* 方塊，並鍵入減號字元 (-)，然後將 Sales Return Quantity 量值拖曳至 [運算式]\*\*\*\* 方塊，將其放置在減號字元後面。</span><span class="sxs-lookup"><span data-stu-id="80241-367">Drag the Sales Quantity measure to the **Expression** box, type the subtraction character (-), and then drag the Sales Return Quantity measure to the **Expression** box; place it after the subtraction character.</span></span>  
  
     <span data-ttu-id="80241-368">下列程式碼顯示運算式：</span><span class="sxs-lookup"><span data-stu-id="80241-368">The following code shows the expression:</span></span>  
  
    ```  
    [Measures].[Sales Quantity] - [Measures].[Sales Return Quantity]  
    ```  
  
4.  <span data-ttu-id="80241-369">在 [名稱] 中，輸入 **Net QTY**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="80241-369">In the Name box, type **Net QTY**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="80241-370">[導出成員] 窗格會列出 **Net QTY** 導出成員。</span><span class="sxs-lookup"><span data-stu-id="80241-370">The Calculated Members pane lists the **Net QTY** calculated member.</span></span>  
  
5.  <span data-ttu-id="80241-371">以滑鼠右鍵按一下 **[導出成員]**，然後按一下 **[新增導出成員]**。</span><span class="sxs-lookup"><span data-stu-id="80241-371">Right-click **Calculated Members**, and then click **New Calculated Member**.</span></span>  
  
6.  <span data-ttu-id="80241-372">在 [中繼資料] 窗格中，展開 [量值]\*\*\*\*，然後展開 Sales。</span><span class="sxs-lookup"><span data-stu-id="80241-372">In the Metadata pane, expand **Measures**, and then expand Sales.</span></span>  
  
7.  <span data-ttu-id="80241-373">將 Sales Amount 量值拖曳至 [運算式]\*\*\*\* 方塊，並鍵入減號字元 (-)，然後將 Sales Return Amount 量值拖曳至 [運算式]\*\*\*\* 方塊，將其放置在減號字元後面。</span><span class="sxs-lookup"><span data-stu-id="80241-373">Drag the Sales Amount measure to the **Expression** box, type the subtraction character (-), and then drag the Sales Return Amount measure to the **Expression** box; place it after the subtraction character.</span></span>  
  
     <span data-ttu-id="80241-374">下列程式碼顯示運算式：</span><span class="sxs-lookup"><span data-stu-id="80241-374">The following code shows the expression:</span></span>  
  
    ```  
    [Measures].[Sales Amount] - [Measures].[Sales Return Amount]  
    ```  
  
8.  <span data-ttu-id="80241-375">在 **[名稱]** 方塊中輸入  **Net Sales**，然後按一下 **[確定]**。[導出成員] 窗格會列出 **Net Sales** 導出成員。</span><span class="sxs-lookup"><span data-stu-id="80241-375">In the **Name** box, type  **Net Sales**, and then click **OK**.The Calculated Members pane lists the **Net Sales** calculated member.</span></span>  
  
###  <a name="to-create-the-dataset"></a><a name="MSkip"></a><span data-ttu-id="80241-376">若要建立資料集</span><span class="sxs-lookup"><span data-stu-id="80241-376">To create the dataset</span></span>  
  
1.  <span data-ttu-id="80241-377">從 Channel 維度中，將 Channel Name 拖曳至資料窗格。</span><span class="sxs-lookup"><span data-stu-id="80241-377">From the Channel dimension, drag Channel Name to the data pane.</span></span>  
  
2.  <span data-ttu-id="80241-378">從 Product 維度中，將 Product Category Name 拖曳到資料窗格，然後將其放置在 Channel Name 的右側。</span><span class="sxs-lookup"><span data-stu-id="80241-378">From the Product dimension, drag Product Category Name to the data pane, and then place it to the right of Channel Name.</span></span>  
  
3.  <span data-ttu-id="80241-379">從 [導出成員]\*\*\*\* 中，將 `Net QTY` 拖曳至資料窗格，然後將其放置在 Product Category Name 的右側。</span><span class="sxs-lookup"><span data-stu-id="80241-379">From **Calculated Members**, drag `Net QTY` to the data pane, and then place it to the right of Product Category Name.</span></span>  
  
4.  <span data-ttu-id="80241-380">從 [導出成員] 中，將 Net Sales 拖曳到資料窗格，然後將其放置在 `Net QTY`的右側。</span><span class="sxs-lookup"><span data-stu-id="80241-380">From Calculated Members, drag Net Sales to the data pane, and then place it to the right of `Net QTY`.</span></span>  
  
5.  <span data-ttu-id="80241-381">在查詢設計工具工具列上，按一下 **[執行 (!)]**。</span><span class="sxs-lookup"><span data-stu-id="80241-381">On the query designer toolbar, click **Run (!)**.</span></span>  
  
     <span data-ttu-id="80241-382">檢閱查詢結果集。</span><span class="sxs-lookup"><span data-stu-id="80241-382">Review the query result set.</span></span>  
  
6.  <span data-ttu-id="80241-383">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="80241-383">Click **Next**.</span></span>  
  
##  <a name="1c-organize-data-into-groups"></a><a name="MLayout"></a><span data-ttu-id="80241-384">1c.</span><span class="sxs-lookup"><span data-stu-id="80241-384">1c.</span></span> <span data-ttu-id="80241-385">將資料組織為群組</span><span class="sxs-lookup"><span data-stu-id="80241-385">Organize Data into Groups</span></span>  
 <span data-ttu-id="80241-386">當您選取將資料分組的欄位時，會設計包含資料列和資料行的矩陣，以顯示詳細資料和彙總資料。</span><span class="sxs-lookup"><span data-stu-id="80241-386">When you select the fields on which to group data, you design a matrix with rows and columns that displays detail and aggregated data.</span></span>  
  
#### <a name="to-organize-data-into-groups"></a><span data-ttu-id="80241-387">若要將資料組織為群組</span><span class="sxs-lookup"><span data-stu-id="80241-387">To organize data into groups</span></span>  
  
1.  <span data-ttu-id="80241-388">在 [排列欄位]\*\*\*\* 頁面上，將 Product_Category_Name 拖曳至 [資料列群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="80241-388">On the **Arrange fields** page, drag Product_Category_Name to **Row groups**.</span></span>  
  
2.  <span data-ttu-id="80241-389">將 Channel_Name 拖曳至 [資料行群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="80241-389">Drag Channel_Name to **Column groups**.</span></span>  
  
3.  <span data-ttu-id="80241-390">將 `Net_QTY` 拖曳至 **[值]**。</span><span class="sxs-lookup"><span data-stu-id="80241-390">Drag `Net_QTY` to **Values**.</span></span>  
  
     <span data-ttu-id="80241-391">`Net_QTY` 。</span><span class="sxs-lookup"><span data-stu-id="80241-391">`Net_QTY` is automatically aggregated by the Sum function, the default aggregate for numeric fields.</span></span> <span data-ttu-id="80241-392">值為 `[Sum(Net_QTY)]`。</span><span class="sxs-lookup"><span data-stu-id="80241-392">The value is `[Sum(Net_QTY)]`.</span></span>  
  
     <span data-ttu-id="80241-393">若要檢視其他可用的彙總函式，開啟下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="80241-393">To view the other aggregate functions available, open the drop-down list.</span></span> <span data-ttu-id="80241-394">請不要變更彙總函式。</span><span class="sxs-lookup"><span data-stu-id="80241-394">Do not change the aggregate function.</span></span>  
  
4.  <span data-ttu-id="80241-395">將 `Net_Sales_Return` 拖曳至 **[值]** ，並將其放置在 `[Sum(Net_QTY)]`之下。</span><span class="sxs-lookup"><span data-stu-id="80241-395">Drag `Net_Sales_Return` to **Values** and then place it below `[Sum(Net_QTY)]`.</span></span>  
  
     <span data-ttu-id="80241-396">步驟 3 和步驟 4 指定了矩陣中要顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="80241-396">Steps 3 and 4 specify the data to display in the matrix.</span></span>  
  
##  <a name="1d-add-subtotals-and-totals"></a><a name="MTotals"></a><span data-ttu-id="80241-397">1d.</span><span class="sxs-lookup"><span data-stu-id="80241-397">1d.</span></span> <span data-ttu-id="80241-398">加入小計和總計</span><span class="sxs-lookup"><span data-stu-id="80241-398">Add Subtotals and Totals</span></span>  
 <span data-ttu-id="80241-399">您可以在報表中顯示小計和總計。</span><span class="sxs-lookup"><span data-stu-id="80241-399">You can show subtotals and grand totals in reports.</span></span> <span data-ttu-id="80241-400">主報表中的資料會顯示為指標，而且您將會在完成精靈後移除總計。</span><span class="sxs-lookup"><span data-stu-id="80241-400">The data in the main report displays as an indicator; you will remove the grand total after you complete the wizard.</span></span>  
  
#### <a name="to-add-subtotals-and-grand-totals"></a><span data-ttu-id="80241-401">若要加入小計和總計</span><span class="sxs-lookup"><span data-stu-id="80241-401">To add subtotals and grand totals</span></span>  
  
1.  <span data-ttu-id="80241-402">在 [**選擇版面**配置] 頁面的 [**選項**] 底下，確認已選取 [**顯示小計和總計**]。</span><span class="sxs-lookup"><span data-stu-id="80241-402">On the **Choose the layout** page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
     <span data-ttu-id="80241-403">精靈的 [預覽] 窗格會顯示含有四個資料列的矩陣。</span><span class="sxs-lookup"><span data-stu-id="80241-403">The wizard Preview pane displays a matrix with four rows.</span></span>  <span data-ttu-id="80241-404">當您執行報表時，每個資料列都會以下列方式顯示：第一個資料列是資料行群組、第二個資料列包含資料行標題、第三個資料列包含產品類別目錄資料 (`[Sum(Net_ QTY)]` 和 `[Sum(Net_Sales)]`，而第四個資料列包含總計。</span><span class="sxs-lookup"><span data-stu-id="80241-404">When you run the report, each row will display in the following way: The first row is the column group, the second row contains the column headings, the third row contains the product category data (`[Sum(Net_ QTY)]` and `[Sum(Net_Sales)]`, and the fourth row contains the totals.</span></span>  
  
2.  <span data-ttu-id="80241-405">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="80241-405">Click **Next**.</span></span>  
  
##  <a name="1e-choose-a-style"></a><a name="MStyle"></a><span data-ttu-id="80241-406">1e.</span><span class="sxs-lookup"><span data-stu-id="80241-406">1e.</span></span> <span data-ttu-id="80241-407">選擇樣式</span><span class="sxs-lookup"><span data-stu-id="80241-407">Choose a Style</span></span>  
 <span data-ttu-id="80241-408">將 [石板] 樣式套用到報表。</span><span class="sxs-lookup"><span data-stu-id="80241-408">Apply the Slate style to the report.</span></span> <span data-ttu-id="80241-409">這是鑽研報表使用的相同樣式。</span><span class="sxs-lookup"><span data-stu-id="80241-409">This is the same style that the drillthrough report uses.</span></span>  
  
#### <a name="to-specify-a-style"></a><span data-ttu-id="80241-410">若要指定樣式</span><span class="sxs-lookup"><span data-stu-id="80241-410">To specify a style</span></span>  
  
1.  <span data-ttu-id="80241-411">在 [**選擇樣式**] 頁面的 [樣式] 窗格中，選取 [石板]。</span><span class="sxs-lookup"><span data-stu-id="80241-411">On the **Choose a Style** page, in the Styles pane, select Slate.</span></span>  
  
2.  <span data-ttu-id="80241-412">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="80241-412">Click **Finish**.</span></span>  
  
3.  <span data-ttu-id="80241-413">若要預覽報表，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="80241-413">To preview the report, click **Run**.</span></span>  
  
##  <a name="2-remove-the-grand-total-row"></a><a name="MGrandTotal"></a><span data-ttu-id="80241-414">2. 移除總計資料列</span><span class="sxs-lookup"><span data-stu-id="80241-414">2. Remove the Grand Total Row</span></span>  
 <span data-ttu-id="80241-415">資料值會顯示為指標狀態，包括資料行群組總計。</span><span class="sxs-lookup"><span data-stu-id="80241-415">The data values are shown as indictor states, including the column group totals.</span></span> <span data-ttu-id="80241-416">移除顯示總計的資料列。</span><span class="sxs-lookup"><span data-stu-id="80241-416">Remove the row that displays the grand total.</span></span>  
  
#### <a name="to-remove-the-grand-total-row"></a><span data-ttu-id="80241-417">若要移除總計資料列</span><span class="sxs-lookup"><span data-stu-id="80241-417">To remove the grand total row</span></span>  
  
1.  <span data-ttu-id="80241-418">若要切換成 [設計] 檢視，按一下 **[設計]**。</span><span class="sxs-lookup"><span data-stu-id="80241-418">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="80241-419">按一下 [總計] 資料列 (矩陣中的最後一個資料列)，按一下滑鼠右鍵，然後按一下 **[刪除資料列]**。</span><span class="sxs-lookup"><span data-stu-id="80241-419">Click the Total row (the last row in the matrix), right-click, and then click **Delete Rows**.</span></span>  
  
3.  <span data-ttu-id="80241-420">若要預覽報表，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="80241-420">To preview the report, click **Run**.</span></span>  
  
##  <a name="3-configure-text-box-action-for-drillthrough"></a><a name="MDrillthrough"></a><span data-ttu-id="80241-421">3. 設定用於鑽取的文字方塊動作</span><span class="sxs-lookup"><span data-stu-id="80241-421">3. Configure Text Box Action for Drillthrough</span></span>  
 <span data-ttu-id="80241-422">若要啟用鑽研，請在主報表的文字方塊上指定動作。</span><span class="sxs-lookup"><span data-stu-id="80241-422">To enable the drillthrough, specify an action on a text box in the main report.</span></span>  
  
#### <a name="to-enable-an-action"></a><span data-ttu-id="80241-423">若要啟用動作</span><span class="sxs-lookup"><span data-stu-id="80241-423">To enable an action</span></span>  
  
1.  <span data-ttu-id="80241-424">若要切換成 [設計] 檢視，按一下 **[設計]**。</span><span class="sxs-lookup"><span data-stu-id="80241-424">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="80241-425">以滑鼠右鍵按一下包含 Product_Category_Name 的資料格，然後按一下 [文字方塊屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="80241-425">Right-click the cell that contains Product_Category_Name, and then click **Text Box Properties**.</span></span>  
  
3.  <span data-ttu-id="80241-426">按一下 [動作]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="80241-426">Click the **Action** tab.</span></span>  
  
4.  <span data-ttu-id="80241-427">選取 [**移至報表]。**</span><span class="sxs-lookup"><span data-stu-id="80241-427">Select **Go to report.**</span></span>  
  
5.  <span data-ttu-id="80241-428">在 **[指定報表]** 中，按一下 **[瀏覽]**，然後找出名稱為 ResellerVSOnlineDrillthrough 的鑽研報表。</span><span class="sxs-lookup"><span data-stu-id="80241-428">In **Specify a report**, click **Browse**, and then locate the drillthrough report named ResellerVSOnlineDrillthrough.</span></span>  
  
6.  <span data-ttu-id="80241-429">若要加入參數以執行鑽研報表，按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="80241-429">To add a parameter to run the drillthrough report, click **Add**.</span></span>  
  
7.  <span data-ttu-id="80241-430">在 [名稱]\*\*\*\* 清單中，選取 ProductProductCategoryName。</span><span class="sxs-lookup"><span data-stu-id="80241-430">In the **Name** list, select ProductProductCategoryName.</span></span>  
  
8.  <span data-ttu-id="80241-431">在 **[值]** 中，輸入 `[Product_Category_Name.UniqueName]`。</span><span class="sxs-lookup"><span data-stu-id="80241-431">In **Value**, type `[Product_Category_Name.UniqueName]`.</span></span>  
  
     <span data-ttu-id="80241-432">Product_Category_Name 是資料集中的欄位。</span><span class="sxs-lookup"><span data-stu-id="80241-432">Product_Category_Name is a field in the dataset.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="80241-433">您必須加入 `UniqueName` 屬性，因為鑽研動作需要唯一的值。</span><span class="sxs-lookup"><span data-stu-id="80241-433">You must include the `UniqueName` property because the drillthrough action requires a unique value.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-format-the-drillthrough-field"></a><span data-ttu-id="80241-434">若要格式化鑽研欄位</span><span class="sxs-lookup"><span data-stu-id="80241-434">To format the drillthrough field</span></span>  
  
1.  <span data-ttu-id="80241-435">以滑鼠右鍵按一下包含 `Product_Category_Name`的資料格，然後按一下 **[文字方塊屬性]**。</span><span class="sxs-lookup"><span data-stu-id="80241-435">Right-click the cell that contains the `Product_Category_Name`, and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="80241-436">按一下 **[字型]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="80241-436">Click the **Font** tab.</span></span>  
  
3.  <span data-ttu-id="80241-437">在 **[效果]** 清單中，選取 **[底線]**。</span><span class="sxs-lookup"><span data-stu-id="80241-437">In the **Effects** list, select **Underline**.</span></span>  
  
4.  <span data-ttu-id="80241-438">在 **[色彩]** 清單中，選取 **[藍色]**。</span><span class="sxs-lookup"><span data-stu-id="80241-438">In the **Color** list, select **Blue**.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="80241-439">若要預覽報表，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="80241-439">To preview your report, click **Run**.</span></span>  
  
 <span data-ttu-id="80241-440">產品類別目錄名稱會採用一般連結的格式 (藍色和底線)。</span><span class="sxs-lookup"><span data-stu-id="80241-440">The product category names are in the common link format (blue and underlined).</span></span>  
  
##  <a name="4-replace-numeric-values-with-indicators"></a><a name="MIndicators"></a><span data-ttu-id="80241-441">4. 以指標取代數值</span><span class="sxs-lookup"><span data-stu-id="80241-441">4. Replace Numeric Values with Indicators</span></span>  
 <span data-ttu-id="80241-442">使用指標顯示 [線上] 與 [轉售商] 通道之數量與銷售額的狀態。</span><span class="sxs-lookup"><span data-stu-id="80241-442">Use indicators to show the state of quantities and sales for Online and Reseller channels.</span></span>  
  
#### <a name="to-add-an-indicator-for-net-qty-values"></a><span data-ttu-id="80241-443">若要加入 Net QTY 值的指標</span><span class="sxs-lookup"><span data-stu-id="80241-443">To add an indicator for Net QTY values</span></span>  
  
1.  <span data-ttu-id="80241-444">若要切換成 [設計] 檢視，按一下 **[設計]**。</span><span class="sxs-lookup"><span data-stu-id="80241-444">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="80241-445">在功能區上，按一下 **[矩形]** 圖示，然後在 `[Sum(Net QTY)]` 資料行群組的 `[Product_Category_Name]` 資料列群組中，按一下 `Channel_Name` 資料格。</span><span class="sxs-lookup"><span data-stu-id="80241-445">On the ribbon, click the **Rectangle** icon, and then click in the `[Sum(Net QTY)]` cell in the `[Product_Category_Name]` row group in the `Channel_Name` column group.</span></span>  
  
3.  <span data-ttu-id="80241-446">在功能區上，按一下 **[指標]** 圖示，然後按一下矩形內部。</span><span class="sxs-lookup"><span data-stu-id="80241-446">On the ribbon, click the **Indicator** icon, and then click inside the rectangle.</span></span> <span data-ttu-id="80241-447">**[選取指標類型]** 對話方塊隨即開啟，其中已選取 **[方向性]** 指標。</span><span class="sxs-lookup"><span data-stu-id="80241-447">The **Select Indicator Type** dialog box opens with the **Directional** indicator selected.</span></span>  
  
4.  <span data-ttu-id="80241-448">按一下 **[三記號]** 類型，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="80241-448">Click the **3 Signs** type, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="80241-449">以滑鼠右鍵按一下指標，然後在 [量測計資料] 窗格中，按一下 **[(未指定)]** 旁邊的向下鍵。</span><span class="sxs-lookup"><span data-stu-id="80241-449">Right-click the indicator and in the Gauge Data pane, click the down arrow next to **(Unspecified)**.</span></span> <span data-ttu-id="80241-450">選取 `Net_QTY`。</span><span class="sxs-lookup"><span data-stu-id="80241-450">Select `Net_QTY`.</span></span>  
  
6.  <span data-ttu-id="80241-451">在 `[Sum(Net QTY)]` [總計] `[Product_Category_Name]` 內，針對 **資料列群組中的**資料格，重複步驟 2 到 5。</span><span class="sxs-lookup"><span data-stu-id="80241-451">Repeat steps 2 through 5 for the `[Sum(Net QTY)]` cell in the `[Product_Category_Name]` row group within **Total**.</span></span>  
  
#### <a name="to-add-an-indicator-for-net-sales-values"></a><span data-ttu-id="80241-452">若要加入 Net Sales 值的指標</span><span class="sxs-lookup"><span data-stu-id="80241-452">To add an indicator for Net Sales values</span></span>  
  
1.  <span data-ttu-id="80241-453">在功能區上，按一下 **[矩形]** 圖示，然後在 `[Sum(Net_Sales)]` 資料行群組的 `[Product_Category_Name]` 資料列群組中，按一下 `Channel_Name` 資料格內部。</span><span class="sxs-lookup"><span data-stu-id="80241-453">On the ribbon, click the **Rectangle** icon, and then click inside the `[Sum(Net_Sales)]` cell in the `[Product_Category_Name]` row group in the `Channel_Name` column group.</span></span>  
  
2.  <span data-ttu-id="80241-454">在功能區上，按一下 **[指標]** 圖示，然後按一下矩形內部。</span><span class="sxs-lookup"><span data-stu-id="80241-454">On the ribbon, click the **Indicator** icon, and then click inside the rectangle.</span></span>  
  
3.  <span data-ttu-id="80241-455">按一下 **[三記號]** 類型，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="80241-455">Click the **3 Signs** type, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="80241-456">以滑鼠右鍵按一下指標，然後在 [量測計資料] 窗格中，按一下 **[(未指定)]** 旁邊的向下鍵。</span><span class="sxs-lookup"><span data-stu-id="80241-456">Right-click the indicator and in the Gauge Data pane, click the down arrow next to **(Unspecified)**.</span></span> <span data-ttu-id="80241-457">選取 `Net_Sales`。</span><span class="sxs-lookup"><span data-stu-id="80241-457">Select `Net_Sales`.</span></span>  
  
5.  <span data-ttu-id="80241-458">在 `[Sum(Net_Sales)]` [總計] `[Product_Category_Name]` 內，針對 **資料列群組中的**資料格，重複步驟 1 到 4。</span><span class="sxs-lookup"><span data-stu-id="80241-458">Repeat steps 1 through 4 for the `[Sum(Net_Sales)]` cell in the `[Product_Category_Name]` row group within **Total**.</span></span>  
  
6.  <span data-ttu-id="80241-459">若要預覽報表，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="80241-459">To preview your report, click **Run**.</span></span>  
  
##  <a name="5-update-parameter-properties"></a><a name="MParameter"></a><span data-ttu-id="80241-460">5. 更新參數屬性</span><span class="sxs-lookup"><span data-stu-id="80241-460">5. Update Parameter Properties</span></span>  
 <span data-ttu-id="80241-461">參數預設是可見的，但不適合這個報表。</span><span class="sxs-lookup"><span data-stu-id="80241-461">By default, parameters are visible, which is not appropriate for this report.</span></span> <span data-ttu-id="80241-462">您將更新參數屬性，讓參數變成內部的。</span><span class="sxs-lookup"><span data-stu-id="80241-462">You will update the parameter properties to make the parameter internal.</span></span>  
  
#### <a name="to-make-the-parameter-internal"></a><span data-ttu-id="80241-463">若要將參數變成內部的</span><span class="sxs-lookup"><span data-stu-id="80241-463">To make the parameter internal</span></span>  
  
1.  <span data-ttu-id="80241-464">在 [報表資料] 窗格中，展開 **[參數]**。</span><span class="sxs-lookup"><span data-stu-id="80241-464">In the Report Data pane, expand **Parameters**.</span></span>  
  
2.  <span data-ttu-id="80241-465">以滑鼠右鍵按一下 `@ProductProductCategoryName,` ，然後按一下 **[參數屬性]**。</span><span class="sxs-lookup"><span data-stu-id="80241-465">Right-click `@ProductProductCategoryName,` and then click **Parameter Properties**.</span></span>  
  
3.  <span data-ttu-id="80241-466">在 **[一般]** 索引標籤上，按一下 **[內部]**。</span><span class="sxs-lookup"><span data-stu-id="80241-466">On the **General** tab, click **Internal**.</span></span>  
  
4.  <span data-ttu-id="80241-467">或者，按一下 **[可用的值]** 和 **[預設值]** 索引標籤，然後檢閱其選項。</span><span class="sxs-lookup"><span data-stu-id="80241-467">Optionally, click the **Available Values** and **Default Values** tabs and review their options.</span></span> <span data-ttu-id="80241-468">請不要變更這些索引標籤上的任何選項。</span><span class="sxs-lookup"><span data-stu-id="80241-468">Do not change any options on these tabs.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="6-add-a-report-title"></a><a name="MTitle"></a><span data-ttu-id="80241-469">6. 加入報表標題</span><span class="sxs-lookup"><span data-stu-id="80241-469">6. Add a Report Title</span></span>  
 <span data-ttu-id="80241-470">將標題加入到主報表中</span><span class="sxs-lookup"><span data-stu-id="80241-470">Add a title to the main report.</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="80241-471">若要加入報表標題</span><span class="sxs-lookup"><span data-stu-id="80241-471">To add a report title</span></span>  
  
1.  <span data-ttu-id="80241-472">在設計介面上，按一下 **[按一下以加入標題]**。</span><span class="sxs-lookup"><span data-stu-id="80241-472">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="80241-473">類型 **2009 Product Category Sales:Online and Reseller Category:**。</span><span class="sxs-lookup"><span data-stu-id="80241-473">Type **2009 Product Category Sales: Online and Reseller Category:**.</span></span>  
  
3.  <span data-ttu-id="80241-474">選取您輸入的文字。</span><span class="sxs-lookup"><span data-stu-id="80241-474">Select the text you typed.</span></span>  
  
4.  <span data-ttu-id="80241-475">在功能區的 **[主資料夾]** 索引標籤上，選取 [字型] 群組中的 **[Times New Roman]** 字型、 **[16pt]** 大小，以及 **[粗體]** 和 **[斜體]** 樣式。</span><span class="sxs-lookup"><span data-stu-id="80241-475">On the **Home** tab of the ribbon, in the Font group, select the **Times New Roman** font, **16pt** size, and the **Bold** and **Italic** styles.</span></span>  
  
5.  <span data-ttu-id="80241-476">若要預覽報表，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="80241-476">To preview your report, click **Run**.</span></span>  
  
##  <a name="7-save-the-main-report-to-a-sharepoint-library"></a><a name="MSave"></a><span data-ttu-id="80241-477">7. 將主報表儲存至 SharePoint 文件庫</span><span class="sxs-lookup"><span data-stu-id="80241-477">7. Save the Main Report to a SharePoint Library</span></span>  
 <span data-ttu-id="80241-478">將主報表儲存至 SharePoint 文件庫。</span><span class="sxs-lookup"><span data-stu-id="80241-478">Save the main report to a SharePoint library.</span></span>  
  
#### <a name="to-save-the-report"></a><span data-ttu-id="80241-479">若要儲存報表</span><span class="sxs-lookup"><span data-stu-id="80241-479">To save the report</span></span>  
  
1.  <span data-ttu-id="80241-480">若要切換成 [設計] 檢視，按一下 **[設計]**。</span><span class="sxs-lookup"><span data-stu-id="80241-480">To switch to design view, click **Design**.</span></span>  
  
2.  <span data-ttu-id="80241-481">在報表產生器的按鈕中，按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="80241-481">From the Report Builder button, click **Save**.</span></span>  
  
3.  <span data-ttu-id="80241-482">或者，若要顯示最近使用過的報表伺服器和 SharePoint 網站清單，按一下 **[最近使用的網站和伺服器]**。</span><span class="sxs-lookup"><span data-stu-id="80241-482">Optionally, to show a list of recently used report servers and SharePoint sites, click **Recent Sites and Servers**.</span></span>  
  
4.  <span data-ttu-id="80241-483">選取或輸入您有權儲存報表之 SharePoint 網站的名稱。</span><span class="sxs-lookup"><span data-stu-id="80241-483">Select or type the name of the SharePoint site where you have permission to save reports.</span></span> <span data-ttu-id="80241-484">SharePoint 文件庫的 URL 具有下列語法：</span><span class="sxs-lookup"><span data-stu-id="80241-484">The URL of the SharePoint library has the following syntax:</span></span>  
  
    ```  
    Http://<ServerName>/<Sites>/  
    ```  
  
5.  <span data-ttu-id="80241-485">導覽到您要儲存報表的文件庫。</span><span class="sxs-lookup"><span data-stu-id="80241-485">Navigate to the library where you want to save the report.</span></span>  
  
6.  <span data-ttu-id="80241-486">在 **[名稱]** 中，將預設名稱取代成 **ResellerVSOnlineMain**。</span><span class="sxs-lookup"><span data-stu-id="80241-486">In **Name**, replace the default name with **ResellerVSOnlineMain**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="80241-487">將主報表儲存到儲存鑽研報表的相同位置。</span><span class="sxs-lookup"><span data-stu-id="80241-487">Save the main report to the same location where you saved the drillthrough report.</span></span> <span data-ttu-id="80241-488">若要將主報表和鑽研報表儲存到不同的網站或文件庫，請確認主報表中的 **[移至報表]** 動作指向鑽研報表的正確路徑。</span><span class="sxs-lookup"><span data-stu-id="80241-488">To save the main and drillthrough reports to different sites or libraries, confirm that the **Go to report** action in the main report, points to the correct location of the drillthrough report.</span></span>  
  
7.  <span data-ttu-id="80241-489">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="80241-489">Click **Save**.</span></span>  
  
##  <a name="8-run-the-main-and-drillthrough-reports"></a><a name="MRunReports"></a><span data-ttu-id="80241-490">8. 執行主報表和鑽取報告</span><span class="sxs-lookup"><span data-stu-id="80241-490">8. Run the Main and Drillthrough Reports</span></span>  
 <span data-ttu-id="80241-491">執行主報表，然後按一下產品類別目錄資料行中的值以執行鑽研報表。</span><span class="sxs-lookup"><span data-stu-id="80241-491">Run the main report, and then click values in the product category column to run the drillthrough report.</span></span>  
  
#### <a name="to-run-the-reports"></a><span data-ttu-id="80241-492">若要執行報表</span><span class="sxs-lookup"><span data-stu-id="80241-492">To run the reports</span></span>  
  
1.  <span data-ttu-id="80241-493">開啟儲存報表的 SharePoint 文件庫。</span><span class="sxs-lookup"><span data-stu-id="80241-493">Open the SharePoint library where the reports are saved.</span></span>  
  
2.  <span data-ttu-id="80241-494">按兩下 ResellerVSOnlineMain。</span><span class="sxs-lookup"><span data-stu-id="80241-494">Double-click ResellerVSOnlineMain.</span></span>  
  
     <span data-ttu-id="80241-495">報表就會執行並顯示產品類別目錄銷售資訊。</span><span class="sxs-lookup"><span data-stu-id="80241-495">The report runs and displays product category sales information.</span></span>  
  
3.  <span data-ttu-id="80241-496">在包含產品類別目錄名稱的資料行中，按一下 **[Games and Toys]** 連結。</span><span class="sxs-lookup"><span data-stu-id="80241-496">Click the **Games and Toys** link in the column that contains product category names.</span></span>  
  
     <span data-ttu-id="80241-497">鑽研報表便會執行，並只顯示 Games and Toys 產品類別目錄的值。</span><span class="sxs-lookup"><span data-stu-id="80241-497">The drillthrough report runs, displaying only the values for the Games and Toys product category.</span></span>  
  
4.  <span data-ttu-id="80241-498">若要返回主報表，按一下 Internet Explorer 的 [上一頁] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="80241-498">To return to the main report, click the Internet Explorer back button.</span></span>  
  
5.  <span data-ttu-id="80241-499">或者，按一下其他產品類別目錄的名稱以進行探索。</span><span class="sxs-lookup"><span data-stu-id="80241-499">Optionally, explore other product categories by clicking their names.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80241-500">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80241-500">See Also</span></span>  
 [<span data-ttu-id="80241-501">教學課程 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="80241-501">Tutorials &#40;Report Builder&#41;</span></span>](report-builder-tutorials.md)  
  
  
