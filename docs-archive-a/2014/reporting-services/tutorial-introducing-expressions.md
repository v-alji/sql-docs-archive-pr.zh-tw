---
title: 教學課程：運算式簡介 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2d05ef4c-5f91-48b2-8795-f0a201a0b3cc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62a815800dba0730052eb812124d4561d031d0e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706106"
---
# <a name="tutorial-introducing-expressions"></a><span data-ttu-id="7a7cc-102">教學課程：運算式簡介</span><span class="sxs-lookup"><span data-stu-id="7a7cc-102">Tutorial: Introducing Expressions</span></span>
  <span data-ttu-id="7a7cc-103">運算式可協助您建立強大而靈活的報表。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-103">Expressions help you create powerful and flexible reports.</span></span> <span data-ttu-id="7a7cc-104">本教學課程將教您建立和實作使用一般函數和運算子的運算式。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-104">This tutorial teaches you to create and implement expressions that use common functions and operators.</span></span> <span data-ttu-id="7a7cc-105">您將使用 [**運算式**] 對話方塊來撰寫串連名稱值、在不同的資料集中查閱值、依據域值顯示不同圖片等的運算式。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-105">You will use the **Expression** dialog box to write expressions that concatenate name values, look up values in a separate dataset, display different pictures based on field values, and so on.</span></span>  
  
 <span data-ttu-id="7a7cc-106">報表是橫條報表，其中採用白色和某種色彩交替的資料列色彩。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-106">The report is a barred report with alternating row colors in white and a color.</span></span> <span data-ttu-id="7a7cc-107">報表包含選取非白色資料列色彩的參數。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-107">The report includes a parameter for selecting the color of the non-white rows.</span></span>  
  
 <span data-ttu-id="7a7cc-108">下圖顯示報表，與您將要建立的報表相似。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-108">The following illustration shows a report similar to the one you will create.</span></span>  
  
 <span data-ttu-id="7a7cc-109">![rs_ExpressionsTutorial](../../2014/tutorials/media/rs-expressionstutorial.gif "rs_ExpressionsTutorial")</span><span class="sxs-lookup"><span data-stu-id="7a7cc-109">![rs_ExpressionsTutorial](../../2014/tutorials/media/rs-expressionstutorial.gif "rs_ExpressionsTutorial")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="7a7cc-110">您將瞭解的內容</span><span class="sxs-lookup"><span data-stu-id="7a7cc-110">What You Will Learn</span></span>  
 <span data-ttu-id="7a7cc-111">在本教學課程中，您將學習如何執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="7a7cc-111">In this tutorial you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="7a7cc-112">從資料表或矩陣精靈建立資料表報表和資料集</span><span class="sxs-lookup"><span data-stu-id="7a7cc-112">Create a Table Report and Dataset from the Table or Matrix Wizard</span></span>](#Setup)  
  
2.  [<span data-ttu-id="7a7cc-113">更新資料來源和資料集的預設名稱</span><span class="sxs-lookup"><span data-stu-id="7a7cc-113">Update Default Names of the Data Source and Dataset</span></span>](#UpdateNames)  
  
3.  [<span data-ttu-id="7a7cc-114">顯示名字、縮寫和姓氏</span><span class="sxs-lookup"><span data-stu-id="7a7cc-114">Display First Name, Initial, and Last Name</span></span>](#Concatenate)  
  
4.  [<span data-ttu-id="7a7cc-115">使用影像顯示性別</span><span class="sxs-lookup"><span data-stu-id="7a7cc-115">Use Images to Display Gender</span></span>](#Gender)  
  
5.  [<span data-ttu-id="7a7cc-116">查閱 CountryRegion 名稱</span><span class="sxs-lookup"><span data-stu-id="7a7cc-116">Look Up CountryRegion Name</span></span>](#Lookup)  
  
6.  [<span data-ttu-id="7a7cc-117">計算自上次購買後的日數</span><span class="sxs-lookup"><span data-stu-id="7a7cc-117">Count Days Since Last Purchase</span></span>](#Count)  
  
7.  [<span data-ttu-id="7a7cc-118">使用指標顯示銷售比較</span><span class="sxs-lookup"><span data-stu-id="7a7cc-118">Use an Indicator to Show Sales Comparison</span></span>](#Indicator)  
  
8.  [<span data-ttu-id="7a7cc-119">將報表設為「綠色橫條」報表</span><span class="sxs-lookup"><span data-stu-id="7a7cc-119">Make the Report a "Green Bar" Report</span></span>](#GreenBar)  
  
### <a name="other-optional-steps"></a><span data-ttu-id="7a7cc-120">其他選擇性步驟</span><span class="sxs-lookup"><span data-stu-id="7a7cc-120">Other Optional Steps</span></span>  
  
-   [<span data-ttu-id="7a7cc-121">格式化日期資料行</span><span class="sxs-lookup"><span data-stu-id="7a7cc-121">Format Date Column</span></span>](#DateFormat)  
  
-   [<span data-ttu-id="7a7cc-122">加入報表標題</span><span class="sxs-lookup"><span data-stu-id="7a7cc-122">Add a Report Title</span></span>](#Title)  
  
-   [<span data-ttu-id="7a7cc-123">儲存報表</span><span class="sxs-lookup"><span data-stu-id="7a7cc-123">Save the Report</span></span>](#Save)  
  
 <span data-ttu-id="7a7cc-124">完成本教學課程的估計時間：30 分鐘。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-124">Estimated time to complete this tutorial: 30 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a7cc-125">需求</span><span class="sxs-lookup"><span data-stu-id="7a7cc-125">Requirements</span></span>  
 <span data-ttu-id="7a7cc-126">如需需求的資訊，請參閱[教學課程的必要條件 &#40;報表產生器&#41;](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-126">For information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-table-report-and-dataset-from-the-table-or-matrix-wizard"></a><a name="Setup"></a><span data-ttu-id="7a7cc-127">1. 從資料表或矩陣 Wizard 建立資料表報表和資料集</span><span class="sxs-lookup"><span data-stu-id="7a7cc-127">1. Create a Table Report and Dataset from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="7a7cc-128">建立資料表報表、資料來源與資料集。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-128">Create a table report, a data source, and a dataset.</span></span> <span data-ttu-id="7a7cc-129">當您配置資料表時，只會包含少數欄位。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-129">When you lay out the table, you will include only a few fields.</span></span> <span data-ttu-id="7a7cc-130">在完成精靈之後，您將手動加入資料行。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-130">After you complete the wizard you will manually add columns.</span></span> <span data-ttu-id="7a7cc-131">精靈方便您配置資料表並套用樣式。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-131">The wizard makes it easy for you to lay out the table and apply a style.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a7cc-132">在本教學課程中，查詢會包含資料值，因此不需要外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-132">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="7a7cc-133">這樣會使查詢相當冗長。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-133">This makes the query quite long.</span></span> <span data-ttu-id="7a7cc-134">在商業環境中，查詢不會包含資料。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-134">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="7a7cc-135">這僅供教學之用。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-135">This is for learning purposes only.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a7cc-136">在本教學課程中，精靈的步驟會合併為一個程序。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-136">In this tutorial, the steps for the wizard are consolidated into one procedure.</span></span> <span data-ttu-id="7a7cc-137">如需如何瀏覽至報表伺服器、選擇資料來源以及建立資料集的逐步指示，請參閱本系列的第一個教學課程：[教學課程：建立基本資料表報表 &#40;報表產生器&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-137">For step-by-step instructions about how to browse to a report server, choose a data source, and create a dataset, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
#### <a name="to-create-a-new-table-report"></a><span data-ttu-id="7a7cc-138">若要建立新資料表報表</span><span class="sxs-lookup"><span data-stu-id="7a7cc-138">To create a new table report</span></span>  
  
1.  <span data-ttu-id="7a7cc-139">按一下 [**開始**]，指向 [**程式**]，按一下 [ [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **報表產生器**]，然後按一下 [**報表產生器**]。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-139">Click **Start**, point to **Programs**, click [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="7a7cc-140">[**消費者入門**] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-140">The **Getting Started** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7a7cc-141"> 如果 **[使用者入門]** 對話方塊沒有出現，請在 **[報表產生器]** 按鈕中按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-141">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7a7cc-142">如果您偏好使用 ClickOnce 版本的報表產生器，請開啟報表管理員，然後按一下 [**報表產生器**]，或移至 SharePoint 網站，其中會啟用 Reporting Services 內容類型（例如報表），然後在共用文件庫的 [**檔**] 索引標籤上，按一下 [**新增檔**] 功能表上的 [**報表產生器報表**]。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-142">If you prefer using the ClickOnce version of Report Builder, open Report Manager and click **Report Builder**, or go to a SharePoint site on which Reporting Services content types such as reports are enabled and click **Report Builder Report** on the **New Document** menu on the **Documents** tab of a shared documents library.</span></span>  
  
2.  <span data-ttu-id="7a7cc-143">在左窗格中，確認已選取 **[新增報表]** 。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-143">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="7a7cc-144">在右窗格中，按一下 **[資料表或矩陣精靈]**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-144">In the right pane, click **Table or Matrix Wizard**.</span></span>  
  
4.  <span data-ttu-id="7a7cc-145">在 **[選擇資料集]** 頁面上，按一下 **[建立資料集]**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-145">On the **Choose a dataset** page, click **Create a dataset**.</span></span>  
  
5.  <span data-ttu-id="7a7cc-146">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-146">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="7a7cc-147">在 **[選擇與資料來源的連接]** 頁面上，選取類型為 **[SQL Server]** 的資料來源。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-147">On the **Choose a connection to a data source** page, select a data source that is type **SQL Server**.</span></span> <span data-ttu-id="7a7cc-148">請從清單中選取資料來源，或者瀏覽到報表伺服器再進行選取。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-148">Select a data source from the list or browse to the report server to select one.</span></span>  
  
7.  <span data-ttu-id="7a7cc-149">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-149">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="7a7cc-150">在 **[設計查詢]** 頁面上，按一下 **[當成文字編輯]**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-150">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
9. <span data-ttu-id="7a7cc-151">將下列查詢貼入查詢窗格中：</span><span class="sxs-lookup"><span data-stu-id="7a7cc-151">Paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT 'Lauren' AS FirstName,'Johnson' AS LastName, 'American Samoa' AS StateProvince, 1 AS CountryRegionID,'Unknown' AS Gender, CAST(9996.60 AS money) AS YTDPurchase, CAST('2010-6-10' AS date) AS LastPurchase  
    UNION SELECT'Warren' AS FirstName, 'Pal' AS LastName, 'New South Wales' AS StateProvince, 2 AS CountryRegionID, 'Male' AS Gender, CAST(5747.25 AS money) AS YTDPurchase, CAST('2010-7-3' AS date) AS LastPurchase  
    UNION SELECT 'Fernando' AS FirstName, 'Ross' AS LastName, 'Alberta' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(9248.15 AS money) AS YTDPurchase, CAST('2010-10-17' AS date) AS LastPurchase  
    UNION SELECT 'Rob' AS FirstName, 'Caron' AS LastName, 'Northwest Territories' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(742.50 AS money) AS YTDPurchase, CAST('2010-4-29' AS date) AS LastPurchase  
    UNION SELECT 'James' AS FirstName, 'Bailey' AS LastName, 'British Columbia' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(1147.50 AS money) AS YTDPurchase, CAST('2010-6-15' AS date) AS LastPurchase  
    UNION SELECT  'Bridget' AS FirstName, 'She' AS LastName, 'Hamburg' AS StateProvince, 4 AS CountryRegionID, 'Female' AS Gender, CAST(7497.30 AS money) AS YTDPurchase, CAST('2010-5-10' AS date) AS LastPurchase  
    UNION SELECT 'Alexander' AS FirstName, 'Martin' AS LastName, 'Saxony' AS StateProvince, 4 AS CountryRegionID, 'Male' AS Gender, CAST(2997.60 AS money) AS YTDPurchase, CAST('2010-11-19' AS date) AS LastPurchase  
    UNION SELECT 'Yolanda' AS FirstName, 'Sharma' AS LastName ,'Micronesia' AS StateProvince, 5 AS CountryRegionID, 'Female' AS Gender, CAST(3247.95 AS money) AS YTDPurchase, CAST('2010-8-23' AS date) AS LastPurchase  
    UNION SELECT 'Marc' AS FirstName, 'Zimmerman' AS LastName, 'Moselle' AS StateProvince, 6 AS CountryRegionID, 'Male' AS Gender, CAST(1200.00 AS money) AS YTDPurchase, CAST('2010-11-16' AS date) AS LastPurchase  
    UNION SELECT 'Katherine' AS FirstName, 'Abel' AS LastName, 'Moselle' AS StateProvince, 6 AS CountryRegionID, 'Female' AS Gender, CAST(2025.00 AS money) AS YTDPurchase, CAST('2010-12-1' AS date) AS LastPurchase  
    UNION SELECT 'Nicolas' as FirstName, 'Anand' AS LastName, 'Seine (Paris)' AS StateProvince, 6 AS CountryRegionID, 'Male' AS Gender, CAST(1425.00 AS money) AS YTDPurchase, CAST('2010-12-11' AS date) AS LastPurchase  
    UNION SELECT 'James' AS FirstName, 'Peters' AS LastName, 'England' AS StateProvince, 12 AS CountryRegionID, 'Male' AS Gender, CAST(887.50 AS money) AS YTDPurchase, CAST('2010-8-15' AS date) AS LastPurchase  
    UNION SELECT 'Alison' AS FirstName, 'Nath' AS LastName, 'Alaska' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(607.50 AS money) AS YTDPurchase, CAST('2010-10-13' AS date) AS LastPurchase  
    UNION SELECT 'Grace' AS FirstName, 'Patterson' AS LastName, 'Kansas' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(1215.00 AS money) AS YTDPurchase, CAST('2010-10-18' AS date) AS LastPurchase  
    UNION SELECT 'Bobby' AS FirstName, 'Sanchez' AS LastName, 'North Dakota' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(6191.00 AS money) AS YTDPurchase, CAST('2010-9-17' AS date) AS LastPurchase  
    UNION SELECT 'Charles' AS FirstName, 'Reed' AS LastName, 'Nebraska' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(8772.00 AS money) AS YTDPurchase, CAST('2010-8-27' AS date) AS LastPurchase  
    UNION SELECT 'Orlando' AS FirstName, 'Romeo' AS LastName, 'Texas' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(8578.00 AS money) AS YTDPurchase, CAST('2010-7-29' AS date) AS LastPurchase  
    UNION SELECT 'Cynthia' AS FirstName, 'Randall' AS LastName, 'Utah' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(7218.10 AS money) AS YTDPurchase, CAST('2010-1-11' AS date) AS LastPurchase  
    UNION SELECT 'Rebecca' AS FirstName, 'Roberts' AS LastName, 'Washington' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(8357.80 AS money) AS YTDPurchase, CAST('2010-10-28' AS date) AS LastPurchase  
    UNION SELECT 'Cristian' AS FirstName, 'Petulescu' AS LastName, 'Wisconsin' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(3470.00 AS money) AS YTDPurchase, CAST('2010-11-30' AS date) AS LastPurchase  
    UNION SELECT 'Cynthia' AS FirstName, 'Randall' AS LastName, 'Utah' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(7218.10 AS money) AS YTDPurchase, CAST('2010-1-11' AS date) AS LastPurchase  
    UNION SELECT 'Rebecca' AS FirstName, 'Roberts' AS LastName, 'Washington' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(8357.80 AS money) AS YTDPurchase, CAST('2010-10-28' AS date) AS LastPurchase  
    UNION SELECT 'Cristian' AS FirstName, 'Petulescu' AS LastName, 'Wisconsin' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(3470.00 AS money) AS YTDPurchase, CAST('2010-11-30' AS date) AS LastPurchase  
    ```  
  
     <span data-ttu-id="7a7cc-152">查詢會指定資料行名稱，其中包括出生日期、名字、姓氏、省份、國家/地區識別碼、性別，以及今年到目前的購買記錄。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-152">The query specifies column names that include a birth date, first name, last name, state or province, country/region identifier, gender, and year-to-date purchases.</span></span>  
  
10. <span data-ttu-id="7a7cc-153">在 [查詢設計工具] 工具列上，按一下 [**執行**] (**！**) 。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-153">On the query designer toolbar, click **Run** (**!**).</span></span> <span data-ttu-id="7a7cc-154">結果集會顯示 20 個資料列，並且包括下列資料行：FirstName、LastName、StateProvince、CountryRegionID、Gender、YTDPurchase 和 LastPurchase。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-154">The result set displays 20 rows of data and includes the following columns: FirstName, LastName, StateProvince, CountryRegionID, Gender, YTDPurchase, and LastPurchase.</span></span>  
  
11. <span data-ttu-id="7a7cc-155">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-155">Click **Next**.</span></span>  
  
12. <span data-ttu-id="7a7cc-156">在 [排列欄位]\*\*\*\* 頁面上，依指定的順序將下列欄位從 [可用的欄位]\*\*\*\* 清單拖曳至 [值]\*\*\*\* 清單。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-156">On the **Arrange fields** page, drag the following fields, in the specified order, from the **Available Fields** list to the **Values** list.</span></span>  
  
    -   <span data-ttu-id="7a7cc-157">StateProvince</span><span class="sxs-lookup"><span data-stu-id="7a7cc-157">StateProvince</span></span>  
  
    -   <span data-ttu-id="7a7cc-158">CountryRegionID</span><span class="sxs-lookup"><span data-stu-id="7a7cc-158">CountryRegionID</span></span>  
  
    -   <span data-ttu-id="7a7cc-159">LastPurchase</span><span class="sxs-lookup"><span data-stu-id="7a7cc-159">LastPurchase</span></span>  
  
    -   <span data-ttu-id="7a7cc-160">YTDPurchase</span><span class="sxs-lookup"><span data-stu-id="7a7cc-160">YTDPurchase</span></span>  
  
     <span data-ttu-id="7a7cc-161">由於 CountryRegionID 和 YTDPurchase 包含數值資料，因此預設會套用 SUM 彙總。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-161">Because the CountryRegionID and YTDPurchase contain numeric data, the SUM aggregate is applied to them by default.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7a7cc-162">但是不包括 [FirstName] 和 [LastName] 欄位。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-162">The FirstName and LastName fields are not included.</span></span> <span data-ttu-id="7a7cc-163">您將在後續步驟中加入這兩個欄位。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-163">You will add them in a later step.</span></span>  
  
13. <span data-ttu-id="7a7cc-164">在 [**值**] 清單中，以滑鼠右鍵按一下 `CountryRegionID` 並按一下 [ **Sum** ] 選項。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-164">In the **Values** list, right-click `CountryRegionID` and click the **Sum** option.</span></span>  
  
     <span data-ttu-id="7a7cc-165">[加總] 不再套用至 CountryRegionID。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-165">Sum is no longer applied to CountryRegionID.</span></span>  
  
14. <span data-ttu-id="7a7cc-166">以滑鼠右鍵按一下 [值]\*\*\*\* 清單中的 [YTDPurchase]\*\*\*\*，然後按一下 [加總]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-166">In the **Values** list, right-click **YTDPurchase** and click the **Sum** option.</span></span>  
  
     <span data-ttu-id="7a7cc-167">[加總] 不再套用至 YTDPurchase。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-167">Sum is no longer applied to YTDPurchase.</span></span>  
  
15. <span data-ttu-id="7a7cc-168">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-168">Click **Next**.</span></span>  
  
16. <span data-ttu-id="7a7cc-169">在 [選擇配置]\*\*\*\* 頁面上，按 一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-169">On the **Choose the layout** page, click **Next**.</span></span>  
  
17. <span data-ttu-id="7a7cc-170">在 [**選擇樣式**] 頁面上，按一下 [**平板**電腦]，然後按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-170">On the **Choose a style** page, click **Slate**, and then click **Finish**.</span></span>  
  
##  <a name="2-update-default-names-of-the-data-source-and-dataset"></a><a name="UpdateNames"></a><span data-ttu-id="7a7cc-171">2. 更新資料來源和資料集的預設名稱</span><span class="sxs-lookup"><span data-stu-id="7a7cc-171">2. Update Default Names of the Data Source and Dataset</span></span>  
  
#### <a name="to-update-the-default-name-of-the-data-source"></a><span data-ttu-id="7a7cc-172">若要更新資料來源的預設名稱</span><span class="sxs-lookup"><span data-stu-id="7a7cc-172">To update the default name of the data source</span></span>  
  
1.  <span data-ttu-id="7a7cc-173">在 [報表資料] 窗格中，展開 [資料來源]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-173">In the Report Data pane, expand **Data Sources**.</span></span>  
  
2.  <span data-ttu-id="7a7cc-174">以滑鼠右鍵按一下 **DataSource1**，然後按一下 [資料來源屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-174">Right-click **DataSource1** and click **Data Source Properties.**</span></span>  
  
3.  <span data-ttu-id="7a7cc-175">在 [名稱]\*\*\*\* 方塊中，鍵入 **ExpressionsDataSource**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-175">In the **Name** box, type **ExpressionsDataSource**</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-update-the-default-name-of-the-dataset"></a><span data-ttu-id="7a7cc-176">若要更新資料集的預設名稱</span><span class="sxs-lookup"><span data-stu-id="7a7cc-176">To update the default name of the dataset</span></span>  
  
1.  <span data-ttu-id="7a7cc-177">在 [報表資料] 窗格中，展開 [資料集]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-177">In the Report Data pane, expand **Datasets**.</span></span>  
  
2.  <span data-ttu-id="7a7cc-178">以滑鼠右鍵按一下 **DataSet1**，然後按一下 [資料集屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-178">Right-click **DataSet1** and click **Dataset Properties.**</span></span>  
  
3.  <span data-ttu-id="7a7cc-179">在 [名稱]\*\*\*\* 方塊中，輸入**運算式**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-179">In the **Name** box, type **Expressions**</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="3-display-first-name-initial-and-last-name"></a><a name="Concatenate"></a><span data-ttu-id="7a7cc-180">3. 顯示名字、初始名稱和姓氏</span><span class="sxs-lookup"><span data-stu-id="7a7cc-180">3. Display First Name, Initial, and Last Name</span></span>  
 <span data-ttu-id="7a7cc-181">在運算式中，使用 **Left** 函數和 **Concatenate** (**&**) 運算子，以將結果評估為包括縮寫和姓氏的名稱。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-181">Use the **Left** function and the **Concatenate** (**&**) operator in an expression that evaluates to a name that includes an initial and a last name.</span></span> <span data-ttu-id="7a7cc-182">您可以逐步建立運算式，或是在程序中先略過，再從教學課程將運算式複製/貼上至 [運算式]\*\*\*\* 對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-182">You can build the expression step by step or skip ahead in the procedure and copy/paste the expression from the tutorial into the **Expression** dialog box.</span></span>  
  
#### <a name="to-add-the-name-column"></a><span data-ttu-id="7a7cc-183">若要加入名稱資料行</span><span class="sxs-lookup"><span data-stu-id="7a7cc-183">To add the Name column</span></span>  
  
1.  <span data-ttu-id="7a7cc-184">以滑鼠右鍵按一下 **StateProvince** 資料行，指向 [插入資料行]\*\*\*\*，然後按一下 [左方]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-184">Right-click the **StateProvince** column, point to **Insert Column**, and then click **Left**.</span></span>  
  
     <span data-ttu-id="7a7cc-185">新資料行就會新增至 **StateProvince** 資料行的左方。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-185">A new column is added to the left of the **StateProvince** column.</span></span>  
  
2.  <span data-ttu-id="7a7cc-186">按一下新資料行的標題，並輸入**名稱**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-186">Click the title of the new column and type **Name**</span></span>  
  
3.  <span data-ttu-id="7a7cc-187">以滑鼠右鍵按一下 [名稱]\*\*\*\* 資料行的資料格，然後按一下 [運算式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-187">Right-click the data cell for the **Name** column and click **Expression**.</span></span>  
  
4.  <span data-ttu-id="7a7cc-188">在 [運算式]\*\*\*\* 對話方塊中，展開 [一般函數]\*\*\*\*，並按一下 [文字]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-188">In the **Expression** dialog box, expand **Common Functions**, and then click **Text**.</span></span>  
  
5.  <span data-ttu-id="7a7cc-189">在 [項目]\*\*\*\* 清單中，按兩下 [左方]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-189">In the **Item** list, double-click **Left**.</span></span>  
  
     <span data-ttu-id="7a7cc-190">**Left** 函數隨即新增至運算式中。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-190">The **Left** function is added to the expression.</span></span>  
  
6.  <span data-ttu-id="7a7cc-191">在 [類別目錄]\*\*\*\* 清單中，按一下 [欄位 (運算式)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-191">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
7.  <span data-ttu-id="7a7cc-192">在 [值]\*\*\*\* 清單中，按兩下 **FirstName**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-192">In the **Values** list, double-click **FirstName**.</span></span>  
  
8.  <span data-ttu-id="7a7cc-193">輸入 **, 1)**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-193">Type **, 1)**</span></span>  
  
     <span data-ttu-id="7a7cc-194">此運算式會從 **FirstName** 值中擷取一個字元 (從左邊算起)。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-194">This expression extracts one character from the **FirstName** value, counting from the left.</span></span>  
  
9. <span data-ttu-id="7a7cc-195">輸入 **&" "&**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-195">Type **&" "&**</span></span>  
  
10. <span data-ttu-id="7a7cc-196">在 [值]\*\*\*\* 清單中，按兩下 **LastName**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-196">In the **Values** list, double-click **LastName**.</span></span>  
  
     <span data-ttu-id="7a7cc-197">完成的運算式為： `=Left(Fields!FirstName.Value, 1) &" "& Fields!LastName.Value`</span><span class="sxs-lookup"><span data-stu-id="7a7cc-197">The completed expression: `=Left(Fields!FirstName.Value, 1) &" "& Fields!LastName.Value`</span></span>  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. <span data-ttu-id="7a7cc-198">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-198">Click **Run** to preview the report.</span></span>  
  
##  <a name="4-use-images-to-display-gender"></a><a name="Gender"></a><span data-ttu-id="7a7cc-199">4. 使用影像顯示性別</span><span class="sxs-lookup"><span data-stu-id="7a7cc-199">4. Use Images to Display Gender</span></span>  
 <span data-ttu-id="7a7cc-200">使用影像顯示人員的性別，並且使用第三個影像識別未知的性別值。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-200">Use images to show the gender of a person, and identify unknown gender values by using a third image.</span></span> <span data-ttu-id="7a7cc-201">您會在報表中加入三個隱藏影像，以及一個新的資料行來顯示這些影像，然後依據 [Gender] 欄位中的值決定出現在資料行中的影像。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-201">You will add to the report three hidden images and a new column to display the images, and then determine the image that appears in the column based on the value of the Gender field.</span></span>  
  
 <span data-ttu-id="7a7cc-202">若要在製作橫條報表時套用色彩至包含影像的資料表資料格，您會先加入矩形，然後將影像加入矩形中。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-202">To apply a color to the table cell that contains the image when you make the report a barred report, you will add a rectangle and then add the image to the rectangle.</span></span> <span data-ttu-id="7a7cc-203">您必須使用矩形，才能將背景色彩套用至矩形，而不是套用至影像。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-203">You need to use a rectangle because you can apply a background color to a rectangle, but not to an image.</span></span>  
  
 <span data-ttu-id="7a7cc-204">本教學課程會使用 Windows 所安裝的影像，不過您可以使用任何影像。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-204">The tutorial uses images that are installed with Windows, but you can use any images available to you.</span></span> <span data-ttu-id="7a7cc-205">您將使用內嵌影像，這些影像不必安裝到本機電腦或報表伺服器上。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-205">You will use embedded images, and they do not need to be installed on your local computer or the report server.</span></span>  
  
#### <a name="to-add-images-to-the-report-body"></a><span data-ttu-id="7a7cc-206">若要將影像加入至報表主體</span><span class="sxs-lookup"><span data-stu-id="7a7cc-206">To add images to the report body</span></span>  
  
1.  <span data-ttu-id="7a7cc-207">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-207">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="7a7cc-208">在功能區的 [插入]\*\*\*\* 索引標籤上，按一下 [影像]\*\*\*\*，然後按一下資料表下方的報表主體。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-208">On the **Insert** tab of the ribbon, click **Image** and then click in the report body, below the table.</span></span>  
  
     <span data-ttu-id="7a7cc-209">[影像屬性]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-209">The **Image Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="7a7cc-210">按一下 [匯入]\*\*\*\* 並導覽至 C:\Users\Public\Public Pictures\Sample Pictures。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-210">Click **Import** and navigate to C:\Users\Public\Public Pictures\Sample Pictures.</span></span>  
  
4.  <span data-ttu-id="7a7cc-211">按一下 Penguins.JPG，然後按一下[開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-211">Click Penguins.JPG and click **Open**.</span></span>  
  
     <span data-ttu-id="7a7cc-212">在 [影像屬性]\*\*\*\* 對話方塊中，按一下 [可見性]\*\*\*\*，然後按一下 [隱藏]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-212">In the **Image Properties** dialog box, click **Visibility** and then click the **Hide** option.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="7a7cc-213">重複步驟 2 到 5，但選擇 Koala.JPG。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-213">Repeat steps 2 through 5, but choose Koala.JPG.</span></span>  
  
7.  <span data-ttu-id="7a7cc-214">重複步驟 2 到 5，但是選擇 Tulips.JPG。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-214">Repeat steps 2 through 5, but choose Tulips.JPG.</span></span>  
  
#### <a name="to-add-the-gender-column"></a><span data-ttu-id="7a7cc-215">若要加入性別資料行</span><span class="sxs-lookup"><span data-stu-id="7a7cc-215">To add the Gender column</span></span>  
  
1.  <span data-ttu-id="7a7cc-216">以滑鼠右鍵按一下 [名稱]\*\*\*\* 資料行，指向 [插入資料行]\*\*\*\*，然後按一下 [右方]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-216">Right-click the **Name** column, point to **Insert Column**, and then click **Right**.</span></span>  
  
     <span data-ttu-id="7a7cc-217">新資料行就會新增至 [名稱]\*\*\*\* 資料行的右方。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-217">A new column is added to the right of the **Name** column.</span></span>  
  
2.  <span data-ttu-id="7a7cc-218">按一下新資料行的標題，並輸入**性別**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-218">Click the title of the new column and type **Gender**</span></span>  
  
#### <a name="to-add-a-rectangle"></a><span data-ttu-id="7a7cc-219">若要加入矩形</span><span class="sxs-lookup"><span data-stu-id="7a7cc-219">To add a rectangle</span></span>  
  
-   <span data-ttu-id="7a7cc-220">在功能區的 [插入]\*\*\*\* 索引標籤上，按一下 [矩形]\*\*\*\*，然後按一下 [性別]\*\*\*\* 資料行的資料格。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-220">On the **Insert** tab of the ribbon, click **Rectangle** and then click in the data cell of the **Gender** column.</span></span>  
  
     <span data-ttu-id="7a7cc-221">如此矩形就會加入至資料格。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-221">A rectangle is added to the cell.</span></span>  
  
#### <a name="to-add-an-image-to-the-rectangle"></a><span data-ttu-id="7a7cc-222">若要將影像加入矩形中</span><span class="sxs-lookup"><span data-stu-id="7a7cc-222">To add an image to the rectangle</span></span>  
  
1.  <span data-ttu-id="7a7cc-223">以滑鼠右鍵按一下矩形，指向 [插入]\*\*\*\*，然後按一下 [影像]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-223">Right-click in the rectangle, point to **Insert**, and then click **Image**.</span></span>  
  
2.  <span data-ttu-id="7a7cc-224">在 [影像屬性]\*\*\*\* 對話方塊中，按一下 [使用此影像]\*\*\*\* 旁邊的向下鍵，並選取您新增的其中一個影像，例如 Penguins.JPG。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-224">In the **Image Properties** dialog box, click the down arrow beside **Use this image**, and select one of the images you added, for example, Penguins.JPG.</span></span>  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-use-images-to-show-gender"></a><span data-ttu-id="7a7cc-225">若要使用影像顯示性別</span><span class="sxs-lookup"><span data-stu-id="7a7cc-225">To use images to show gender</span></span>  
  
1.  <span data-ttu-id="7a7cc-226">在 [性別]\*\*\*\* 資料行的資料格中，以滑鼠右鍵按一下影像，然後按一下 [影像屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-226">Right-click the image in the data cell in the **Gender** column and click **Image Properties**.</span></span>  
  
2.  <span data-ttu-id="7a7cc-227">在 [影像屬性]\*\*\*\* 對話方塊中，按一下 [使用此影像]\*\*\*\* 文字方塊旁邊的運算式 **fx** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-227">In the **Image Properties** dialog box, click the expression **fx** button next to the **Use this image** text box.</span></span>  
  
3.  <span data-ttu-id="7a7cc-228">在 [運算式]\*\*\*\* 對話方塊中，展開 [一般函數]\*\*\*\*，並按一下 [程式流程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-228">In the **Expression** dialog box, expand **Common Functions** and click **Program Flow**.</span></span>  
  
4.  <span data-ttu-id="7a7cc-229">在 [項目]\*\*\*\* 清單中，按兩下 [Switch]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-229">In the **Item** list, double-click **Switch**.</span></span>  
  
5.  <span data-ttu-id="7a7cc-230">在 [類別目錄]\*\*\*\* 清單中，按一下 [欄位 (運算式)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-230">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
6.  <span data-ttu-id="7a7cc-231">在 [值]\*\*\*\* 清單中，按兩下 [性別]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-231">In the **Values** list, double-click **Gender**.</span></span>  
  
7.  <span data-ttu-id="7a7cc-232">輸入 **="Male", "Koala",**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-232">Type **="Male", "Koala",**</span></span>  
  
8.  <span data-ttu-id="7a7cc-233">在 [值]\*\*\*\* 清單中，按兩下 [性別]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-233">In the **Values** list, double-click **Gender**.</span></span>  
  
9. <span data-ttu-id="7a7cc-234">輸入 **="Female", "Penguins",**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-234">Type **="Female", "Penguins",**</span></span>  
  
10. <span data-ttu-id="7a7cc-235">在 [值]\*\*\*\* 清單中，按兩下 [性別]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-235">In the **Values** list, double-click **Gender**.</span></span>  
  
11. <span data-ttu-id="7a7cc-236">輸入 **="Unknown", "Tulips")**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-236">Type **="Unknown", "Tulips")**</span></span>  
  
     <span data-ttu-id="7a7cc-237">完成的運算式為： `=Switch(Fields!Gender.Value ="Male", "Koala",Fields!Gender.Value ="Female","Penguins",Fields!Gender.Value ="Unknown","Tulips")`</span><span class="sxs-lookup"><span data-stu-id="7a7cc-237">The completed expression: `=Switch(Fields!Gender.Value ="Male", "Koala",Fields!Gender.Value ="Female","Penguins",Fields!Gender.Value ="Unknown","Tulips")`</span></span>  
  
12. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
13. <span data-ttu-id="7a7cc-238">再按一次 [確定]\*\*\*\*，關閉 [影像屬性]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-238">Click **OK** again to close the **Image Properties** dialog box.</span></span>  
  
14. <span data-ttu-id="7a7cc-239">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-239">Click **Run** to preview the report.</span></span>  
  
##  <a name="5-look-up-countryregion-name"></a><a name="Lookup"></a><span data-ttu-id="7a7cc-240">5. 查閱國家/地區名稱</span><span class="sxs-lookup"><span data-stu-id="7a7cc-240">5. Look Up CountryRegion Name</span></span>  
 <span data-ttu-id="7a7cc-241">建立 CountryRegion 資料集並使用 **Lookup** 函數顯示國家/地區的名稱，而不使用國家/地區的識別碼。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-241">Create the CountryRegion dataset and use the **Lookup** function to display the name of a country/region instead of the identifier of the country/region.</span></span>  
  
#### <a name="to-create-the-countryregion-dataset"></a><span data-ttu-id="7a7cc-242">若要建立 CountryRegion 資料集</span><span class="sxs-lookup"><span data-stu-id="7a7cc-242">To create the CountryRegion dataset</span></span>  
  
1.  <span data-ttu-id="7a7cc-243">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-243">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="7a7cc-244">在 [報表資料] 窗格中，按一下 [**新增**]，然後按一下 [**資料集**]。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-244">In the Report Data pane, click **New** and then click **Dataset**.</span></span>  
  
3.  <span data-ttu-id="7a7cc-245">按一下 **[使用內嵌在我的報表中的資料集]**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-245">Click **Use a dataset embedded in my report**.</span></span>  
  
4.  <span data-ttu-id="7a7cc-246">在 [資料來源]\*\*\*\* 清單中，選取 ExpressionsDataSource。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-246">In the **Data source** list, select ExpressionsDataSource.</span></span>  
  
5.  <span data-ttu-id="7a7cc-247">在 [名稱]\*\*\*\* 方塊中，鍵入 **CountryRegion**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-247">In the **Name** box, type **CountryRegion**</span></span>  
  
6.  <span data-ttu-id="7a7cc-248">驗證已選取 [文字]\*\*\*\* 查詢類型，並按一下 [查詢設計工具]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-248">Verify that the **Text** query type is selected and click **Query Designer**.</span></span>  
  
7.  <span data-ttu-id="7a7cc-249">按一下 **[當成文字編輯]**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-249">Click **Edit as Text**.</span></span>  
  
8.  <span data-ttu-id="7a7cc-250">複製下列查詢並貼入查詢窗格中：</span><span class="sxs-lookup"><span data-stu-id="7a7cc-250">Copy and paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT 1 AS ID, 'American Samoa' AS CountryRegion  
    UNION SELECT 2 AS CountryRegionID, 'Australia' AS CountryRegion  
    UNION SELECT 3 AS ID, 'Canada' AS CountryRegion  
    UNION SELECT 4 AS ID, 'Germany' AS CountryRegion  
    UNION SELECT 5 AS ID, 'Micronesia' AS CountryRegion  
    UNION SELECT 6 AS ID, 'France' AS CountryRegion  
    UNION SELECT 7 AS ID, 'United States' AS CountryRegion  
    UNION SELECT 8 AS ID, 'Brazil' AS CountryRegion  
    UNION SELECT 9 AS ID, 'Mexico' AS CountryRegion  
    UNION SELECT 10 AS ID, 'Japan' AS CountryRegion  
    UNION SELECT 10 AS ID, 'Australia' AS CountryRegion  
    UNION SELECT 12 AS ID, 'United Kingdom' AS CountryRegion  
    ```  
  
9. <span data-ttu-id="7a7cc-251">按一下 [**執行**] (**！**) 以執行查詢。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-251">Click **Run** (**!**) to run the query.</span></span>  
  
     <span data-ttu-id="7a7cc-252">查詢結果為國家/地區識別碼和名稱。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-252">The query results are the country/region identifiers and names.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. <span data-ttu-id="7a7cc-253">再按一次 [確定]\*\*\*\*，關閉 [資料集屬性]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-253">Click **OK** again to close the **Dataset Properties** dialog box.</span></span>  
  
#### <a name="to-look-up-values-in-the-countryregion-dataset"></a><span data-ttu-id="7a7cc-254">若要查閱 CountryRegion 資料集中的值</span><span class="sxs-lookup"><span data-stu-id="7a7cc-254">To look up values in the CountryRegion dataset</span></span>  
  
1.  <span data-ttu-id="7a7cc-255">按一下 [國家/地區 ID]\*\*\*\* 資料行標題，並刪除 ID 這兩個字。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-255">Click the **Country Region ID** column title and delete the text: ID.</span></span>  
  
2.  <span data-ttu-id="7a7cc-256">以滑鼠右鍵按一下 [國家/地區]\*\*\*\* 資料行的資料格，然後按一下 [運算式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-256">Right-click the data cell for the **Country Region** column and click **Expression**.</span></span>  
  
3.  <span data-ttu-id="7a7cc-257">刪除運算式，但保留開頭的等號 (=)。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-257">Delete the expression except the initial equal (=) sign.</span></span>  
  
     <span data-ttu-id="7a7cc-258">剩下的運算式為： `=`</span><span class="sxs-lookup"><span data-stu-id="7a7cc-258">The remaining expression is: `=`</span></span>  
  
4.  <span data-ttu-id="7a7cc-259">在 [運算式]\*\*\*\* 對話方塊中，展開 [一般函數]\*\*\*\*，並按一下 [其他]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-259">In the **Expression** dialog box, expand **Common Functions** and click **Miscellaneous**.</span></span>  
  
5.  <span data-ttu-id="7a7cc-260">在 [項目]\*\*\*\* 清單中，按兩下 [Lookup]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-260">In the **Item** list, double-click **Lookup**.</span></span>  
  
6.  <span data-ttu-id="7a7cc-261">在 [類別目錄]\*\*\*\* 清單中，按一下 [欄位 (運算式)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-261">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
7.  <span data-ttu-id="7a7cc-262">在 [**值**] 清單中，按兩下 `CountryRegionID` 。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-262">In the **Values** list, double-click `CountryRegionID`.</span></span>  
  
8.  <span data-ttu-id="7a7cc-263">如果游標不在 `CountryRegionID.Value` 的正後方，請將它放至該處。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-263">If the cursor is not already immediately after `CountryRegionID.Value`, place it there.</span></span>  
  
9. <span data-ttu-id="7a7cc-264">刪除右括號，然後輸入 **,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-264">Delete the right parenthesis and then type **,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")**</span></span>  
  
     <span data-ttu-id="7a7cc-265">完成的運算式為： `=Lookup(Fields!CountryRegionID.Value,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")`</span><span class="sxs-lookup"><span data-stu-id="7a7cc-265">The completed expression: `=Lookup(Fields!CountryRegionID.Value,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")`</span></span>  
  
     <span data-ttu-id="7a7cc-266">**Lookup** 函數的語法會在 CountryRegion 資料集中指定 CountryRegionID 與 ID 之間的查閱，而該資料集會傳回 CountryRegion 值，並在同一個資料集中包含此值。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-266">The syntax of the **Lookup** function specifies a lookup between CountryRegionID and ID in the CountryRegion dataset that returns the CountryRegion value, which is also in the CountryRegion dataset.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. <span data-ttu-id="7a7cc-267">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-267">Click **Run** to preview the report.</span></span>  
  
##  <a name="6-count-days-since-last-purchase"></a><a name="Count"></a><span data-ttu-id="7a7cc-268">6. 計算自上次購買後的天數</span><span class="sxs-lookup"><span data-stu-id="7a7cc-268">6. Count Days Since Last Purchase</span></span>  
 <span data-ttu-id="7a7cc-269">新增資料行，然後使用**Now**函數或 `ExecutionTime` 內建全域變數，計算自個人上次購買後的當日天數。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-269">Add a column and then use the **Now** function or the `ExecutionTime` built-in global variable to calculate the number of days from today since a person's last purchases.</span></span>  
  
#### <a name="to-add-the-days-ago-column"></a><span data-ttu-id="7a7cc-270">若要加入 [天前] 資料行</span><span class="sxs-lookup"><span data-stu-id="7a7cc-270">To add the Days Ago column</span></span>  
  
1.  <span data-ttu-id="7a7cc-271">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-271">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="7a7cc-272">以滑鼠右鍵按一下 [上次購買]\*\*\*\* 資料行，指向 [插入資料行]\*\*\*\*，然後按一下 [右方]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-272">Right-click the **Last Purchase** column, point to **Insert Column**, and then click **Right**.</span></span>  
  
     <span data-ttu-id="7a7cc-273">新資料行就會新增至 [上次購買]\*\*\*\* 資料行的右方。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-273">A new column is added to the right of the **Last Purchase** column.</span></span>  
  
3.  <span data-ttu-id="7a7cc-274">在資料行標頭中，輸入 **天前**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-274">In the column header, type **Days Ago**</span></span>  
  
4.  <span data-ttu-id="7a7cc-275">以滑鼠右鍵按一下 [天前]\*\*\*\* 資料行的資料格，然後按一下 [運算式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-275">Right-click the data cell for the **Days Ago** column and click **Expression**.</span></span>  
  
5.  <span data-ttu-id="7a7cc-276">在 [運算式]\*\*\*\* 對話方塊中，展開 [一般函數]\*\*\*\*，並按一下 [日期和時間]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-276">In the **Expression** dialog box, expand **Common Functions**, and then click **Date & Time**.</span></span>  
  
6.  <span data-ttu-id="7a7cc-277">在 [項目]\*\*\*\* 清單中，按兩下 [DateDiff]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-277">In the **Item** list, double-click **DateDiff**.</span></span>  
  
7.  <span data-ttu-id="7a7cc-278">如果游標不在 `DateDiff(` 的正後方，請將它放至該處。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-278">If the cursor is not already immediately after `DateDiff(`, place it there.</span></span>  
  
8.  <span data-ttu-id="7a7cc-279">輸入 **"d",**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-279">Type **"d",**</span></span>  
  
9. <span data-ttu-id="7a7cc-280">在 [類別目錄]\*\*\*\* 清單中，按一下 [欄位 (運算式)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-280">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
10. <span data-ttu-id="7a7cc-281">在 [值]\*\*\*\* 清單中，按兩下 **LastPurchase**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-281">In the **Values** list, double-click **LastPurchase**.</span></span>  
  
11. <span data-ttu-id="7a7cc-282">如果游標不在 `Fields!LastPurchase.Value` 的正後方，請將它放至該處。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-282">If the cursor is not already immediately after `Fields!LastPurchase.Value`, place it there.</span></span>  
  
12. <span data-ttu-id="7a7cc-283">輸入 **、**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-283">Type **,**</span></span>  
  
13. <span data-ttu-id="7a7cc-284">在 [類別清單]\*\*\*\* 中，再次按一下 [日期和時間]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-284">In the **Category** list, click **Date & Time** again.</span></span>  
  
14. <span data-ttu-id="7a7cc-285">在 [項目]\*\*\*\* 清單中，按兩下 [Now]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-285">In the **Item** list, double-click **Now**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="7a7cc-286">在生產報表中，不應該在隨報表轉譯而評估多次的運算式中使用 **Now** 函數 (例如，報表的詳細資料列)。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-286">In production reports you should not use the **Now** function in expressions that are evaluated multiple times as the report renders (for example, in the detail rows of a report).</span></span> <span data-ttu-id="7a7cc-287">**Now** 的值會依資料列而改變，而不同的值會影響運算式的評估結果，導致結果稍微不一致。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-287">The value of **Now** changes from row to row and the different values affect the evaluation results of expressions, which leads to results that are subtly inconsistent.</span></span> <span data-ttu-id="7a7cc-288">因此，您應該改用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 提供的 `ExecutionTime` 全域變數。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-288">Instead, you should use the `ExecutionTime` global variable that [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] provides.</span></span>  
  
15. <span data-ttu-id="7a7cc-289">如果游標不在 `Now(` 的正後方，請將它放至該處。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-289">If the cursor is not already immediately after `Now(`, place it there.</span></span>  
  
16. <span data-ttu-id="7a7cc-290">刪除左括號，然後輸入 **)**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-290">Delete the left parenthesis and then type **)**</span></span>  
  
     <span data-ttu-id="7a7cc-291">完成的運算式為： `=DateDiff("d", Fields!LastPurchase.Value, Now)`</span><span class="sxs-lookup"><span data-stu-id="7a7cc-291">The completed expression: `=DateDiff("d", Fields!LastPurchase.Value, Now)`</span></span>  
  
17. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="7-use-an-indicator-to-show-sales-comparison"></a><a name="Indicator"></a><span data-ttu-id="7a7cc-292">7. 使用指標顯示銷售比較</span><span class="sxs-lookup"><span data-stu-id="7a7cc-292">7. Use an Indicator to Show Sales Comparison</span></span>  
 <span data-ttu-id="7a7cc-293">加入新的資料行，並使用指標來顯示使用者的年初迄今 (YTD) 購買高於或低於平均 YTD 購買。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-293">Add a new column and use an indicator to show whether a person's year-to-date (YTD) purchases are above or below the average YTD purchases.</span></span> <span data-ttu-id="7a7cc-294">**Round** 函數會移除值的小數。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-294">The **Round** function removes decimals from values.</span></span>  
  
 <span data-ttu-id="7a7cc-295">設定指標及其狀態需要進行許多步驟。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-295">The configuration of the indicator and its states requires many steps.</span></span> <span data-ttu-id="7a7cc-296">如果您想要，您可以在「設定指標」程式中直接跳過，然後從這個教學課程將完成的運算式複製/貼上至 [**運算式**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-296">If you want to, in the "To configure the indicator" procedure, you can skip ahead and copy/paste the completed expressions from this tutorial into the **Expression** dialog box.</span></span>  
  
#### <a name="to-add-the--or---avg-sales-column"></a><span data-ttu-id="7a7cc-297">若要加入平均銷售增減資料行</span><span class="sxs-lookup"><span data-stu-id="7a7cc-297">To add the + or - AVG Sales column</span></span>  
  
1.  <span data-ttu-id="7a7cc-298">以滑鼠右鍵按一下 [YTD 購買]\*\*\*\* 資料行，指向 [插入資料行]\*\*\*\*，然後按一下 [右方]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-298">Right-click the **YTD Purchase** column, point to **Insert Column**, and then click **Right**.</span></span>  
  
     <span data-ttu-id="7a7cc-299">新資料行就會新增至 [YTD 購買]\*\*\*\* 資料行的右方。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-299">A new column is added to the right of the **YTD Purchase** column.</span></span>  
  
2.  <span data-ttu-id="7a7cc-300">按一下資料行的標題，並輸入**平均銷售增減**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-300">Click the title of the column and type **+ or - AVG Sales**</span></span>  
  
#### <a name="to-add-an-indicator"></a><span data-ttu-id="7a7cc-301">若要加入指標</span><span class="sxs-lookup"><span data-stu-id="7a7cc-301">To add an indicator</span></span>  
  
1.  <span data-ttu-id="7a7cc-302">在功能區的 [插入]\*\*\*\* 索引標籤上，按一下 [指標]\*\*\*\*，然後按一下 [平均銷售增減]\*\*\*\* 資料行的資料格。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-302">On the **Insert** tab of the ribbon, click **Indicator**, and then click the data cell for the **+ or - AVG Sales** column.</span></span>  
  
     <span data-ttu-id="7a7cc-303">[選取指標類型]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-303">The **Select Indicator Type** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="7a7cc-304">在圖示集的 [方向性]\*\*\*\* 群組中，按一下三個灰色箭頭的圖示集。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-304">In the **Directional** group of icon sets, click the set of three gray arrows.</span></span>  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-configure-the-indicator"></a><span data-ttu-id="7a7cc-305">若要設定指標</span><span class="sxs-lookup"><span data-stu-id="7a7cc-305">To configure the indicator</span></span>  
  
1.  <span data-ttu-id="7a7cc-306">以滑鼠右鍵按一下指標，按一下 [指標屬性]\*\*\*\*，然後按一下 [值和狀態]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-306">Right-click the indicator, click **Indicator Properties**, and then click **Value and States**.</span></span>  
  
2.  <span data-ttu-id="7a7cc-307">按一下 [值]\*\*\*\* 文字方塊旁邊的 [運算式 fx]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-307">Click the expression **fx** button next to the **Value** text box.</span></span>  
  
3.  <span data-ttu-id="7a7cc-308">在 [運算式]\*\*\*\* 對話方塊中，展開 [一般函數]\*\*\*\*，並按一下 [數學]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-308">In the **Expression** dialog box, expand **Common Functions**, and then click **Math**.</span></span>  
  
4.  <span data-ttu-id="7a7cc-309">在 [項目]\*\*\*\* 清單中，按兩下 [Round]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-309">In the **Item** list, double-click **Round**.</span></span>  
  
5.  <span data-ttu-id="7a7cc-310">在 [類別目錄]\*\*\*\* 清單中，按一下 [欄位 (運算式)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-310">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
6.  <span data-ttu-id="7a7cc-311">在 [值]\*\*\*\* 清單中，按兩下 **YTDPurchase**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-311">In the **Values** list, double-click **YTDPurchase**.</span></span>  
  
7.  <span data-ttu-id="7a7cc-312">如果游標不在 `Fields!YTDPurchase.Value` 的正後方，請將它放至該處。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-312">If the cursor is not already immediately after `Fields!YTDPurchase.Value`, place it there.</span></span>  
  
8.  <span data-ttu-id="7a7cc-313">型**-**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-313">Type  **-**</span></span>  
  
9. <span data-ttu-id="7a7cc-314">再次展開 [一般函數]\*\*\*\*，然後按一下 [彙總]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-314">Expand **Common Functions** again and click **Aggregate**.</span></span>  
  
10. <span data-ttu-id="7a7cc-315">在 [項目]\*\*\*\* 清單中，按兩下 [Avg]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-315">In the **Item** list, double-click **Avg**.</span></span>  
  
11. <span data-ttu-id="7a7cc-316">在 [類別目錄]\*\*\*\* 清單中，按一下 [欄位 (運算式)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-316">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
12. <span data-ttu-id="7a7cc-317">在 [值]\*\*\*\* 清單中，按兩下 **YTDPurchase**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-317">In the **Values** list, double-click **YTDPurchase**.</span></span>  
  
13. <span data-ttu-id="7a7cc-318">如果游標不在 `Fields!YTDPurchase.Value` 的正後方，請將它放至該處。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-318">If the cursor is not already immediately after `Fields!YTDPurchase.Value`, place it there.</span></span>  
  
14. <span data-ttu-id="7a7cc-319">輸入 **, "Expressions"))**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-319">Type **, "Expressions"))**</span></span>  
  
     <span data-ttu-id="7a7cc-320">完成的運算式為： `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions"))`</span><span class="sxs-lookup"><span data-stu-id="7a7cc-320">The completed expression: `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions"))`</span></span>  
  
15. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
16. <span data-ttu-id="7a7cc-321">在 [狀態度量單位]\*\*\*\* 方塊中，選取 [數值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-321">In the **States Measurement Unit** box, select **Numeric**.</span></span>  
  
17. <span data-ttu-id="7a7cc-322">在具有向下鍵的資料列中，按一下 [開始]\*\*\*\* 值的文字方塊右邊的 **fx** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-322">In the row with the down-pointing arrow, click the **fx** button to the right of the text box for the **Start** value.</span></span>  
  
18. <span data-ttu-id="7a7cc-323">在 [運算式]\*\*\*\* 對話方塊中，展開 [一般函數]\*\*\*\*，並按一下 [數學]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-323">In the **Expression** dialog box, expand **Common Functions**, and then click **Math**.</span></span>  
  
19. <span data-ttu-id="7a7cc-324">在 [項目]\*\*\*\* 清單中，按兩下 [Round]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-324">In the **Item** list, double-click **Round**.</span></span>  
  
20. <span data-ttu-id="7a7cc-325">在 [類別目錄]\*\*\*\* 清單中，按一下 [欄位 (運算式)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-325">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
21. <span data-ttu-id="7a7cc-326">在 [值]\*\*\*\* 清單中，按兩下 **YTDPurchase**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-326">In the **Values** list, double-click **YTDPurchase**.</span></span>  
  
22. <span data-ttu-id="7a7cc-327">如果游標不在 `Fields!YTDPurchase.Value` 的正後方，請將它放至該處。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-327">If the cursor is not already immediately after `Fields!YTDPurchase.Value`, place it there.</span></span>  
  
23. <span data-ttu-id="7a7cc-328">型**-**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-328">Type  **-**</span></span>  
  
24. <span data-ttu-id="7a7cc-329">再次展開 [一般函數]\*\*\*\*，然後按一下 [彙總]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-329">Expand **Common Functions** again and click **Aggregate**.</span></span>  
  
25. <span data-ttu-id="7a7cc-330">在 [項目]\*\*\*\* 清單中，按兩下 [Avg]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-330">In the **Item** list, double-click **Avg**.</span></span>  
  
26. <span data-ttu-id="7a7cc-331">在 [類別目錄]\*\*\*\* 清單中，按一下 [欄位 (運算式)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-331">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
27. <span data-ttu-id="7a7cc-332">在 [值]\*\*\*\* 清單中，按兩下 **YTDPurchase**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-332">In the **Values** list, double-click **YTDPurchase**.</span></span>  
  
28. <span data-ttu-id="7a7cc-333">如果游標不在 `Fields!YTDPurchase.Value` 的正後方，請將它放至該處。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-333">If the cursor is not already immediately after `Fields!YTDPurchase.Value`, place it there.</span></span>  
  
29. <span data-ttu-id="7a7cc-334">輸入 **, "Expressions")) < 0**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-334">Type **, "Expressions")) < 0**</span></span>  
  
     <span data-ttu-id="7a7cc-335">完成的運算式為： `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) < 0`</span><span class="sxs-lookup"><span data-stu-id="7a7cc-335">The completed expression: `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) < 0`</span></span>  
  
30. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
31. <span data-ttu-id="7a7cc-336">在 [結束]\*\*\*\* 值的文字方塊中，輸入 **0**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-336">In the text box for the **End** value, type **0**</span></span>  
  
32. <span data-ttu-id="7a7cc-337">按一下具有橫向箭號的資料列，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-337">Click the row with the horizontal-pointing arrow and click **Delete**.</span></span>  
  
33. <span data-ttu-id="7a7cc-338">在具有向上鍵的資料列中，於 [開始]\*\*\*\* 方塊中輸入 **0**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-338">In the row with the up-pointing arrow, in the **Start** box, type **0**</span></span>  
  
34. <span data-ttu-id="7a7cc-339">按一下 [結束]\*\*\*\* 值的文字方塊右邊的 **fx** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-339">Click the **fx** button to the right of the text box for the **End** value.</span></span>  
  
35. <span data-ttu-id="7a7cc-340">在 [**運算式**] 對話方塊中，建立運算式：`=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) >0`</span><span class="sxs-lookup"><span data-stu-id="7a7cc-340">In the **Expression** dialog box, create the expression: `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) >0`</span></span>  
  
36. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
37. <span data-ttu-id="7a7cc-341">再按一次 [確定]\*\*\*\*，關閉 [指標屬性]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-341">Click **OK** again to close the **Indicator properties** dialog box.</span></span>  
  
38. <span data-ttu-id="7a7cc-342">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-342">Click **Run** to preview the report.</span></span>  
  
##  <a name="8-make-the-report-a-green-bar-report"></a><a name="GreenBar"></a><span data-ttu-id="7a7cc-343">8. 將報表設為「綠色橫條」報表</span><span class="sxs-lookup"><span data-stu-id="7a7cc-343">8. Make the Report a "Green Bar" Report</span></span>  
 <span data-ttu-id="7a7cc-344">使用參數指定套用至報表中交替資料列的色彩，使其變成橫條報表。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-344">Use a parameter to specify the color to apply to alternating rows in the report, making it a barred report.</span></span>  
  
#### <a name="to-add-a-parameter"></a><span data-ttu-id="7a7cc-345">若要加入參數</span><span class="sxs-lookup"><span data-stu-id="7a7cc-345">To add a parameter</span></span>  
  
1.  <span data-ttu-id="7a7cc-346">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-346">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="7a7cc-347">在 [報表資料]\*\*\*\* 窗格中，以滑鼠右鍵按一下 [參數]\*\*\*\*，然後按一下 [加入參數]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-347">In the **Report Data** pane, right-click **Parameters** and click **Add Parameter**.</span></span>  
  
     <span data-ttu-id="7a7cc-348">**[報表參數屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-348">The **Report Parameter Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="7a7cc-349">在 [提示]\*\*\*\* 中，鍵入**選擇色彩**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-349">In **Prompt**, type **Choose color**</span></span>  
  
4.  <span data-ttu-id="7a7cc-350">在 [名稱]\*\*\*\* 中，輸入 **RowColor**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-350">In **Name**, type **RowColor**</span></span>  
  
5.  <span data-ttu-id="7a7cc-351">在左窗格中，按一下 [可用的值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-351">In the left pane, click **Available Values**.</span></span>  
  
6.  <span data-ttu-id="7a7cc-352">按一下 [指定值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-352">Click **Specify values**.</span></span>  
  
7.  <span data-ttu-id="7a7cc-353">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-353">Click **Add**.</span></span>  
  
8.  <span data-ttu-id="7a7cc-354">在 [標籤]\*\*\*\* 方塊中，輸入 **Yellow**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-354">In the **Label** box, type: **Yellow**</span></span>  
  
9. <span data-ttu-id="7a7cc-355">在 [值]\*\*\*\* 方塊中，輸入 **Yellow**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-355">In the **Value** box, type **Yellow**</span></span>  
  
10. <span data-ttu-id="7a7cc-356">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-356">Click **Add**.</span></span>  
  
11. <span data-ttu-id="7a7cc-357">在 [標籤]\*\*\*\* 方塊中，鍵入 **Green**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-357">In the **Label** box, type **Green**</span></span>  
  
12. <span data-ttu-id="7a7cc-358">在 [值]\*\*\*\* 方塊中，鍵入 **PaleGreen**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-358">In the **Value** box, type **PaleGreen**</span></span>  
  
13. <span data-ttu-id="7a7cc-359">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-359">Click **Add**.</span></span>  
  
14. <span data-ttu-id="7a7cc-360">在 [標籤]\*\*\*\* 方塊中，鍵入 **Blue**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-360">In the **Label** box, type **Blue**</span></span>  
  
15. <span data-ttu-id="7a7cc-361">在 [值]\*\*\*\* 方塊中，鍵入 **LightBlue**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-361">In the **Value** box, type **LightBlue**</span></span>  
  
16. <span data-ttu-id="7a7cc-362">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-362">Click **Add**.</span></span>  
  
17. <span data-ttu-id="7a7cc-363">在 [標籤]\*\*\*\* 方塊中，鍵入 **Pink**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-363">In the **Label** box, type **Pink**</span></span>  
  
18. <span data-ttu-id="7a7cc-364">在 [值]\*\*\*\* 方塊中，輸入 **Pink**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-364">In the **Value** box, type **Pink**</span></span>  
  
19. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-apply-alternating-colors-to-detail-rows"></a><span data-ttu-id="7a7cc-365">若要套用交替色彩至詳細資料列</span><span class="sxs-lookup"><span data-stu-id="7a7cc-365">To apply alternating colors to detail rows</span></span>  
  
1.  <span data-ttu-id="7a7cc-366">按一下功能區上的 [檢視]\*\*\*\* 索引標籤，並確認已選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-366">Click the **View** tab on the ribbon and verify that **Properties** is selected.</span></span>  
  
2.  <span data-ttu-id="7a7cc-367">按一下 [名稱]\*\*\*\* 資料行的資料格，然後按 Shift 鍵。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-367">Click the data cell for the **Name** column and press the Shift key.</span></span>  
  
3.  <span data-ttu-id="7a7cc-368">逐一按下資料列中的其他資料格。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-368">One by one, click the other cells in the row.</span></span>  
  
4.  <span data-ttu-id="7a7cc-369">在 [屬性] 窗格中，按一下 **BackgroundColor**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-369">In the Properties pane, click **BackgroundColor**.</span></span>  
  
     <span data-ttu-id="7a7cc-370">如果 [屬性]\*\*\*\* 窗格中依類別目錄列出屬性，您將會在 [填滿] 類別目錄底下找到 **BackgroundColor**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-370">If your Properties pane lists properties by category, you will find the **BackgroundColor** under the **Fill** category.</span></span>  
  
5.  <span data-ttu-id="7a7cc-371">按一下向下鍵，然後按一下 [運算式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-371">Click the down arrow and then click **Expression**.</span></span>  
  
6.  <span data-ttu-id="7a7cc-372">在 [運算式]\*\*\*\* 對話方塊中，展開 [一般函數]\*\*\*\*，然後按一下 [程式流程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-372">In the **Expression** dialog box, expand **Common Functions**, and then click **Program Flow**.</span></span>  
  
7.  <span data-ttu-id="7a7cc-373">在 [項目]\*\*\*\* 清單中，按兩下 [IIf]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-373">In the **Item** list, double-click **IIf**.</span></span>  
  
8.  <span data-ttu-id="7a7cc-374">展開 [一般函數]\*\*\*\*，然後按一下 [彙總]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-374">Expand **Common Functions** and click **Aggregate**.</span></span>  
  
9. <span data-ttu-id="7a7cc-375">在 [項目]\*\*\*\* 清單中，按兩下 [RunningValue]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-375">In the **Item** list, double-click **RunningValue**.</span></span>  
  
10. <span data-ttu-id="7a7cc-376">在 [類別目錄]\*\*\*\* 清單中，按一下 [欄位 (運算式)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-376">In the **Category** list, click **Fields (Expressions)**.</span></span>  
  
11. <span data-ttu-id="7a7cc-377">在 [值]\*\*\*\* 清單中，按兩下 **FirstName**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-377">In the **Values** list, double-click **FirstName**.</span></span>  
  
12. <span data-ttu-id="7a7cc-378">如果游標不在 `Fields!FirstName.Value` 的正後方，請將它放至該處並輸入 **,**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-378">If the cursor is not already immediately after `Fields!FirstName.Value`, place it there and type **,**</span></span>  
  
13. <span data-ttu-id="7a7cc-379">展開 [一般函數]\*\*\*\*，然後按一下 [彙總]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-379">Expand **Common Functions** and click **Aggregate**.</span></span>  
  
14. <span data-ttu-id="7a7cc-380">在 [項目]\*\*\*\* 清單中，按兩下 [Count]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-380">In the **Item** list, double-click **Count**.</span></span>  
  
15. <span data-ttu-id="7a7cc-381">如果游標不在 `Count(` 的正後方，請將它放至該處。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-381">If the cursor is not already immediately after `Count(`, place it there.</span></span>  
  
16. <span data-ttu-id="7a7cc-382">刪除左括弧，然後輸入 \*\*，"運算式" ) \*\*</span><span class="sxs-lookup"><span data-stu-id="7a7cc-382">Delete the left parenthesis and then type **,"Expressions")**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7a7cc-383">“Expressions” 是要在其中計算資料列的資料集名稱。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-383">Expressions is the name of the dataset in which to count data rows.</span></span>  
  
17. <span data-ttu-id="7a7cc-384">展開 [運算子]\*\*\*\* 並按一下 [算術]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-384">Expand **Operators** and click **Arithmetic**.</span></span>  
  
18. <span data-ttu-id="7a7cc-385">在 [項目]\*\*\*\* 清單中，按兩下 [Mod]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-385">In the **Item** list, double-click **Mod**.</span></span>  
  
19. <span data-ttu-id="7a7cc-386">如果游標不在 `Mod` 的正後方，請將它放至該處。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-386">If the cursor is not already immediately after `Mod`, place it there.</span></span>  
  
20. <span data-ttu-id="7a7cc-387">輸入 **2 =0,**</span><span class="sxs-lookup"><span data-stu-id="7a7cc-387">Type  **2 =0,**</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="7a7cc-388">務必在輸入數字 2 之前加入一個空格。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-388">Be sure you include a space before you type the number 2.</span></span>  
  
21. <span data-ttu-id="7a7cc-389">按一下 [參數]\*\*\*\*，然後在 [值]\*\*\*\* 清單中按兩下 [RowColor]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-389">Click **Parameters** and in the **Values** list, double-click **RowColor**.</span></span>  
  
22. <span data-ttu-id="7a7cc-390">如果游標不在 `Parameters!RowColor.Value` 的正後方，請將它放至該處。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-390">If the cursor is not already immediately after `Parameters!RowColor.Value`, place it there.</span></span>  
  
23. <span data-ttu-id="7a7cc-391">輸入 \*\*，"白色" ) \*\*</span><span class="sxs-lookup"><span data-stu-id="7a7cc-391">Type **, "White")**</span></span>  
  
     <span data-ttu-id="7a7cc-392">完成的運算式為： `=IIf(RunningValue(Fields!FirstName.Value,Count, "Expressions") Mod 2 =0, Parameters!RowColor.Value, "White")`</span><span class="sxs-lookup"><span data-stu-id="7a7cc-392">The completed expression: `=IIf(RunningValue(Fields!FirstName.Value,Count, "Expressions") Mod 2 =0, Parameters!RowColor.Value, "White")`</span></span>  
  
24. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="run-the-report"></a><span data-ttu-id="7a7cc-393">執行報表</span><span class="sxs-lookup"><span data-stu-id="7a7cc-393">Run the Report</span></span>  
  
1.  <span data-ttu-id="7a7cc-394">如果您不是在 [首頁]\*\*\*\* 索引標籤上，請按一下 [首頁]\*\*\*\* 返回設計檢視。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-394">If not on the **Home** tab, click **Home** to return to design view.</span></span>  
  
2.  <span data-ttu-id="7a7cc-395">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-395">Click **Run**.</span></span>  
  
3.  <span data-ttu-id="7a7cc-396">在 [選擇色彩]\*\*\*\* 下拉式清單中，選取報表上非白色橫條的色彩。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-396">In the **Choose color** drop-down list, select the color of the non-white bars on the report.</span></span>  
  
4.  <span data-ttu-id="7a7cc-397">按一下 [檢視報表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-397">Click **View Report**.</span></span>  
  
     <span data-ttu-id="7a7cc-398">報表隨即呈現，而且交替的資料列會使用您選擇的背景。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-398">The report renders and alternating rows have the background that you chose.</span></span>  
  
##  <a name="optional-format-date-column"></a><a name="DateFormat"></a> <span data-ttu-id="7a7cc-399">(選擇性) 格式日期資料行</span><span class="sxs-lookup"><span data-stu-id="7a7cc-399">(optional) Format Date Column</span></span>  
 <span data-ttu-id="7a7cc-400">格式化包含日期的 [上次購買]\*\*\*\* 資料行。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-400">Format the **Last Purchase** column, which contains dates.</span></span>  
  
#### <a name="to-format-date-column"></a><span data-ttu-id="7a7cc-401">若要格式化日期資料行</span><span class="sxs-lookup"><span data-stu-id="7a7cc-401">To format date column</span></span>  
  
1.  <span data-ttu-id="7a7cc-402">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-402">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="7a7cc-403">以滑鼠右鍵按一下 [上次購買]\*\*\*\* 資料行的資料格，然後按一下 [文字方塊屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-403">Right-click the data cell for the **Last Purchase** column and click **Text Box Properties**.</span></span>  
  
3.  <span data-ttu-id="7a7cc-404">在 [文字方塊屬性]\*\*\*\* 對話方塊中，依序按一下 [數字]\*\*\*\* 和 [日期]\*\*\*\*，然後輸入 **\*1/31/2000**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-404">In the **Text Box Properties** dialog box, click **Number**, click **Date**, and then click the type **\*1/31/2000**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="optional-add-a-report-title"></a><a name="Title"></a> <span data-ttu-id="7a7cc-405">(選擇性) 加入報表標題</span><span class="sxs-lookup"><span data-stu-id="7a7cc-405">(optional) Add a Report Title</span></span>  
 <span data-ttu-id="7a7cc-406">加入報表的標題。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-406">Add a title to the report.</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="7a7cc-407">若要加入報表標題</span><span class="sxs-lookup"><span data-stu-id="7a7cc-407">To add a report title</span></span>  
  
1.  <span data-ttu-id="7a7cc-408">在設計介面上，按一下 **[按一下以加入標題]**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-408">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="7a7cc-409">輸入**銷售比較摘要**，然後按一下文字方塊外部。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-409">Type **Sales Comparison Summary**, and then click outside the text box.</span></span>  
  
3.  <span data-ttu-id="7a7cc-410">以滑鼠右鍵按一下包含**銷售比較摘要**的文字方塊，然後按一下 [文字方塊屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-410">Right-click the text box that contains **Sales Comparison Summary** and click **Text Box Properties**.</span></span>  
  
4.  <span data-ttu-id="7a7cc-411">在 [文字方塊屬性]\*\*\*\* 對話方塊中，按一下 [字型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-411">In the **Text Box Properties** dialog box, click **Font**.</span></span>  
  
5.  <span data-ttu-id="7a7cc-412">在 [大小]\*\*\*\* 清單中，選取 [18pt]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-412">In the **Size** list, select **18pt**.</span></span>  
  
6.  <span data-ttu-id="7a7cc-413">在 [色彩]\*\*\*\* 清單中，選取 [灰色]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-413">In the **Color** list, select **Gray**.</span></span>  
  
7.  <span data-ttu-id="7a7cc-414">選取 [粗體]\*\*\*\* 和 [斜體]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-414">Select  **Bold** and  **Italic**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="optional-save-the-report"></a><a name="Save"></a> <span data-ttu-id="7a7cc-415">(選擇性) 儲存報表</span><span class="sxs-lookup"><span data-stu-id="7a7cc-415">(optional) Save the Report</span></span>  
 <span data-ttu-id="7a7cc-416">您可以將報表儲存至報表伺服器、SharePoint 文件庫或您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-416">You can save reports to a report server, SharePoint library, or your computer.</span></span> <span data-ttu-id="7a7cc-417">如需詳細資訊，請參閱[儲存報表 &#40;報表產生器&#41;](report-builder/saving-reports-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-417">For more information, see [Saving Reports &#40;Report Builder&#41;](report-builder/saving-reports-report-builder.md).</span></span>  
  
 <span data-ttu-id="7a7cc-418">本教學課程會將報表儲存至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-418">In this tutorial, save the report to a report server.</span></span> <span data-ttu-id="7a7cc-419">如果您沒有報表伺服器的存取權，請將報表儲存在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-419">If you do not have access to a report server, save the report to your computer.</span></span>  
  
#### <a name="to-save-the-report-to-a-report-server"></a><span data-ttu-id="7a7cc-420">若要將報表儲存至報表伺服器</span><span class="sxs-lookup"><span data-stu-id="7a7cc-420">To save the report to a report server</span></span>  
  
1.  <span data-ttu-id="7a7cc-421">在 **[報表產生器]** 按鈕中，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-421">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="7a7cc-422">按一下 **[最近使用的網站和伺服器]**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-422">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="7a7cc-423">選取或輸入您有權儲存報表之報表伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-423">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="7a7cc-424">「正在連接到報表伺服器」訊息隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-424">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="7a7cc-425">連接完成時，您將會看見報表伺服器管理員指定為預設報表位置之報表資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-425">When the connection is complete, you will see the contents of the report folder that the report server administrator specified as the default report location.</span></span>  
  
4.  <span data-ttu-id="7a7cc-426">在 [名稱]\*\*\*\* 中，將預設名稱取代為**銷售比較摘要**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-426">In **Name**, replace the default name with **Sales Comparison Summary**.</span></span>  
  
5.  <span data-ttu-id="7a7cc-427">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-427">Click **Save**.</span></span>  
  
 <span data-ttu-id="7a7cc-428">報表就會儲存至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-428">The report is saved to the report server.</span></span> <span data-ttu-id="7a7cc-429">您連接之報表伺服器的名稱會顯示在視窗底部的狀態列中。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-429">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-to-your-computer"></a><span data-ttu-id="7a7cc-430">若要將報表儲存到您的電腦上</span><span class="sxs-lookup"><span data-stu-id="7a7cc-430">To save the report to your computer</span></span>  
  
1.  <span data-ttu-id="7a7cc-431">在 **[報表產生器]** 按鈕中，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-431">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="7a7cc-432">按一下 **[桌面]**、 **[我的文件]** 或 **[我的電腦]**，然後瀏覽到您要儲存報表的資料夾。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-432">Click **Desktop**, **My Documents**, or **My computer**, and then browse to the folder where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="7a7cc-433">在 [名稱]\*\*\*\* 中，將預設名稱取代為**銷售比較摘要**。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-433">In **Name**, replace the default name with **Sales Comparison Summary**.</span></span>  
  
4.  <span data-ttu-id="7a7cc-434">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="7a7cc-434">Click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a7cc-435">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a7cc-435">See Also</span></span>  
 <span data-ttu-id="7a7cc-436">[運算式 &#40;報表產生器及 SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7a7cc-436">[Expressions &#40;Report Builder and SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7a7cc-437">[運算式範例 &#40;報表產生器及 SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7a7cc-437">[Expression Examples &#40;Report Builder and SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7a7cc-438">[指標 &#40;報表產生器和 SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7a7cc-438">[Indicators &#40;Report Builder and SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7a7cc-439">[&#40;報表產生器和 SSRS 的影像、文字方塊、矩形和線條&#41;](report-design/rectangles-and-lines-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7a7cc-439">[Images, Text Boxes, Rectangles, and Lines &#40;Report Builder and SSRS&#41;](report-design/rectangles-and-lines-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7a7cc-440">[資料表 &#40;報表產生器和 SSRS&#41;](report-design/tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7a7cc-440">[Tables &#40;Report Builder  and SSRS&#41;](report-design/tables-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7a7cc-441">將資料加入報表 &#40;報表產生器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7a7cc-441">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-data/report-datasets-ssrs.md)  
  
  
