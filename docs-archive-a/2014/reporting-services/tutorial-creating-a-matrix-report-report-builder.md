---
title: 教學課程：建立矩陣報表 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9ee19c2e-2a8c-4bb0-9274-04a5812c2e96
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3df32098d9e6400931ba2a88b2ffd22d6e015a62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706122"
---
# <a name="tutorial-creating-a-matrix-report-report-builder"></a><span data-ttu-id="30d65-102">教學課程：建立矩陣報表 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="30d65-102">Tutorial: Creating a Matrix Report (Report Builder)</span></span>
  <span data-ttu-id="30d65-103">本教學課程將教導您如何根據範例銷售資料建立基本矩陣報表。</span><span class="sxs-lookup"><span data-stu-id="30d65-103">This tutorial teaches you how to create a basic matrix report based on sample sales data.</span></span> <span data-ttu-id="30d65-104">矩陣具有巢狀資料列和資料行群組，以及一個相鄰資料行群組。</span><span class="sxs-lookup"><span data-stu-id="30d65-104">The matrix has nested row and column groups and an adjacent column group.</span></span> <span data-ttu-id="30d65-105">此外，您還將學習如何格式化資料行和旋轉文字。</span><span class="sxs-lookup"><span data-stu-id="30d65-105">You will also learn how to format columns and rotate text.</span></span> <span data-ttu-id="30d65-106">下圖顯示報表，與您將要建立的報表相似。</span><span class="sxs-lookup"><span data-stu-id="30d65-106">The following illustration shows a report similar to the one you will create.</span></span>  
  
 <span data-ttu-id="30d65-107">![rs_CreateMatixReportTutorial](../../2014/tutorials/media/rs-creatematixreporttutorial.gif "rs_CreateMatixReportTutorial")</span><span class="sxs-lookup"><span data-stu-id="30d65-107">![rs_CreateMatixReportTutorial](../../2014/tutorials/media/rs-creatematixreporttutorial.gif "rs_CreateMatixReportTutorial")</span></span>  
  
 <span data-ttu-id="30d65-108">本教學課程即將建立的報表另有一個增強型版本，可從範例 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 報表產生器報表取得。</span><span class="sxs-lookup"><span data-stu-id="30d65-108">An enhanced version of the report you will create in this tutorial is available as a sample [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Report Builder report.</span></span> <span data-ttu-id="30d65-109">如需下載此範例報表及其他專案的詳細資訊，請參閱[報表產生器範例報表](https://go.microsoft.com/fwlink/?LinkId=184851)。</span><span class="sxs-lookup"><span data-stu-id="30d65-109">For more information about downloading this sample report and others, see [Report Builder sample reports](https://go.microsoft.com/fwlink/?LinkId=184851).</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="30d65-110">您將瞭解的內容</span><span class="sxs-lookup"><span data-stu-id="30d65-110">What You Will Learn</span></span>  
 <span data-ttu-id="30d65-111">在本教學課程中，您將學會如何：</span><span class="sxs-lookup"><span data-stu-id="30d65-111">In this tutorial, you will learn how to:</span></span>  
  
1.  [<span data-ttu-id="30d65-112">從新增資料表或矩陣精靈建立矩陣報表和資料集</span><span class="sxs-lookup"><span data-stu-id="30d65-112">Create a Matrix Report and Dataset from the New Table or Matrix Wizard</span></span>](#CreateMatrix)  
  
2.  [<span data-ttu-id="30d65-113">從新增資料表或矩陣精靈組織資料、選擇配置和樣式</span><span class="sxs-lookup"><span data-stu-id="30d65-113">Organize Data and Choose Layout and Style from the New Table or Matrix Wizard</span></span>](#Groups)  
  
3.  [<span data-ttu-id="30d65-114">格式化資料</span><span class="sxs-lookup"><span data-stu-id="30d65-114">Format Data</span></span>](#FormatData)  
  
4.  [<span data-ttu-id="30d65-115">加入相鄰資料行群組</span><span class="sxs-lookup"><span data-stu-id="30d65-115">Add Adjacent Column Group</span></span>](#AdjacentGroup)  
  
5.  [<span data-ttu-id="30d65-116">變更資料行寬度</span><span class="sxs-lookup"><span data-stu-id="30d65-116">Change Column Widths</span></span>](#Width)  
  
6.  [<span data-ttu-id="30d65-117">合併矩陣資料格</span><span class="sxs-lookup"><span data-stu-id="30d65-117">Merge Matrix Cells</span></span>](#MergeCells)  
  
7.  [<span data-ttu-id="30d65-118">加入報表頁首和報表標題</span><span class="sxs-lookup"><span data-stu-id="30d65-118">Add a Report Header and Report Title</span></span>](#HeaderTitle)  
  
8.  [<span data-ttu-id="30d65-119">儲存報表</span><span class="sxs-lookup"><span data-stu-id="30d65-119">Save the Report</span></span>](#Save)  
  
### <a name="other-optional-step"></a><span data-ttu-id="30d65-120">其他選擇性步驟</span><span class="sxs-lookup"><span data-stu-id="30d65-120">Other Optional Step</span></span>  
  
1.  [<span data-ttu-id="30d65-121">將文字方塊旋轉 270 度</span><span class="sxs-lookup"><span data-stu-id="30d65-121">Rotate Text Box 270 Degrees</span></span>](#RotateTextBox)  
  
 <span data-ttu-id="30d65-122">完成這個教學課程的估計時間：30 分鐘。</span><span class="sxs-lookup"><span data-stu-id="30d65-122">Estimated time to complete this tutorial: 20 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30d65-123">需求</span><span class="sxs-lookup"><span data-stu-id="30d65-123">Requirements</span></span>  
 <span data-ttu-id="30d65-124">如需需求的詳細資訊，請參閱[教學課程的必要條件 &#40;報表產生器&#41;](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="30d65-124">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-matrix-report-and-dataset-from-the-new-table-or-matrix-wizard"></a><a name="CreateMatrix"></a><span data-ttu-id="30d65-125">1. 從 [新增資料表或矩陣] Wizard 建立矩陣報表和資料集</span><span class="sxs-lookup"><span data-stu-id="30d65-125">1. Create a Matrix Report and Dataset from the New Table or Matrix Wizard</span></span>  
 <span data-ttu-id="30d65-126">從報表產生器的 [**消費者入門**] 對話方塊中，選擇共用資料來源、建立內嵌資料集，然後在矩陣中顯示資料。</span><span class="sxs-lookup"><span data-stu-id="30d65-126">From the **Getting Started** dialog box in Report Builder, choose a shared data source, create an embedded dataset, and then display the data in a matrix.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30d65-127">在本教學課程中，查詢已經包含資料值，因此不需要外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="30d65-127">In this tutorial, the query already contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="30d65-128">這樣會使查詢相當冗長。</span><span class="sxs-lookup"><span data-stu-id="30d65-128">This makes the query quite long.</span></span> <span data-ttu-id="30d65-129">在商業環境中，查詢不會包含資料。</span><span class="sxs-lookup"><span data-stu-id="30d65-129">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="30d65-130">這僅供教學之用。</span><span class="sxs-lookup"><span data-stu-id="30d65-130">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-matrix"></a><span data-ttu-id="30d65-131">建立新矩陣</span><span class="sxs-lookup"><span data-stu-id="30d65-131">To create a new matrix</span></span>  
  
1.  <span data-ttu-id="30d65-132">按一下 **[開始]**、依序指向 **[程式集]** 和 **[Microsoft SQL Server 2012 報表產生器]**，然後按一下 **[報表產生器]**。</span><span class="sxs-lookup"><span data-stu-id="30d65-132">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="30d65-133">**[使用者入門]** 對話方塊應會隨即出現。</span><span class="sxs-lookup"><span data-stu-id="30d65-133">The **Getting Started** dialog box should appear.</span></span> <span data-ttu-id="30d65-134">如果不是，請從 [報表產生器] 按鈕按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="30d65-134">If it doesn't, from the Report Builder button, click **New**.</span></span>  
  
2.  <span data-ttu-id="30d65-135">在左窗格中，確認已選取 **[新增報表]** 。</span><span class="sxs-lookup"><span data-stu-id="30d65-135">In the left pane, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="30d65-136">在右窗格中，按一下 **[資料表或矩陣精靈]**。</span><span class="sxs-lookup"><span data-stu-id="30d65-136">In the right pane, click **Table or Matrix Wizard**.</span></span>  
  
4.  <span data-ttu-id="30d65-137">在 **[選擇資料集]** 頁面上，按一下 **[建立資料集]**。</span><span class="sxs-lookup"><span data-stu-id="30d65-137">On the **Choose a dataset** page, click **Create a dataset**.</span></span>  
  
5.  <span data-ttu-id="30d65-138">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="30d65-138">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="30d65-139">在 [**選擇與資料來源的連接**] 頁面上，選取現有的資料來源，或流覽至報表伺服器，然後選取資料來源。</span><span class="sxs-lookup"><span data-stu-id="30d65-139">On the **Choose a connection to a data source** page, select an existing data source or browse to the report server, and then select a data source.</span></span> <span data-ttu-id="30d65-140">如果沒有資料來源可用，或無法存取報表伺服器，您可以改用內嵌資料來源。</span><span class="sxs-lookup"><span data-stu-id="30d65-140">If no data source is available or you do not have access to a report server, you can use an embedded data source instead.</span></span> <span data-ttu-id="30d65-141">如需建立內嵌資料來源的詳細資訊，請參閱[教學課程：建立基本資料表報表 &#40;報表產生器&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="30d65-141">For more information about creating an embedded data source, see [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
7.  <span data-ttu-id="30d65-142">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="30d65-142">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="30d65-143">在 **[設計查詢]** 頁面上，按一下 **[當成文字編輯]**。</span><span class="sxs-lookup"><span data-stu-id="30d65-143">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
9. <span data-ttu-id="30d65-144">複製下列查詢並貼入查詢窗格中：</span><span class="sxs-lookup"><span data-stu-id="30d65-144">Copy and paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity  
    ```  
  
10. <span data-ttu-id="30d65-145">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="30d65-145">Click **Next**.</span></span>  
  
##  <a name="2-organize-data-and-choose-layout-and-style-from-the-new-table-or-matrix-wizard"></a><a name="Groups"></a><span data-ttu-id="30d65-146">2. 從 [新增資料表或矩陣] Wizard 組織資料並選擇版面配置和樣式</span><span class="sxs-lookup"><span data-stu-id="30d65-146">2. Organize Data and Choose Layout and Style from the New Table or Matrix Wizard</span></span>  
 <span data-ttu-id="30d65-147">使用精靈提供起始設計來顯示資料。</span><span class="sxs-lookup"><span data-stu-id="30d65-147">Use the wizard to provide a starting design on which to display data.</span></span> <span data-ttu-id="30d65-148">精靈中的預覽窗格可協助您在完成矩陣設計之前，先視覺化群組資料的結果。</span><span class="sxs-lookup"><span data-stu-id="30d65-148">The preview pane in the wizard helps you to visualize the result of grouping data before you complete the matrix design.</span></span>  
  
#### <a name="to-organize-data-into-groups-and-choose-a-layout-and-style"></a><span data-ttu-id="30d65-149">若要將資料組織成群組，並選擇配置和樣式</span><span class="sxs-lookup"><span data-stu-id="30d65-149">To organize data into groups and choose a layout and style</span></span>  
  
1.  <span data-ttu-id="30d65-150">在 [排列欄位]\*\*\*\* 頁面上，從 [可用的欄位]\*\*\*\* 將 [Territory] 拖曳至 [資料列群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30d65-150">On the **Arrange fields** page, drag Territory from **Available fields** to **Row groups**.</span></span>  
  
2.  <span data-ttu-id="30d65-151">將 [SalesDate] 拖曳至 [資料列群組]\*\*\*\* 並放置在 [Territory] 之下。</span><span class="sxs-lookup"><span data-stu-id="30d65-151">Drag SalesDate to **Row groups** and place it below Territory.</span></span>  
  
     <span data-ttu-id="30d65-152">欄位列於 [資料列群組]\*\*\*\* 中的順序定義了群組階層。</span><span class="sxs-lookup"><span data-stu-id="30d65-152">The order in which fields are listed in **Row groups** defines the group hierarchy.</span></span> <span data-ttu-id="30d65-153">步驟 1 和步驟 2 會先依領域再依銷售日期，組織欄位的值。</span><span class="sxs-lookup"><span data-stu-id="30d65-153">Steps 1 and 2 organize the values of the fields first by territory, and then by sales date.</span></span>  
  
3.  <span data-ttu-id="30d65-154">將 [Subcategory] 拖曳至 [資料行群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30d65-154">Drag Subcategory to **Column groups**.</span></span>  
  
4.  <span data-ttu-id="30d65-155">將 [產品] 拖曳至 [資料**行群組]，** 然後放在子類別底下。</span><span class="sxs-lookup"><span data-stu-id="30d65-155">Drag Product to **Column groups,** and then place below Subcategory.</span></span>  
  
     <span data-ttu-id="30d65-156">欄位在 [資料**行群組**] 中列出的順序會定義群組階層。</span><span class="sxs-lookup"><span data-stu-id="30d65-156">The order in which fields are listed in **Column groups** defines the group hierarchy.</span></span>  
  
     <span data-ttu-id="30d65-157">步驟 3 和步驟 4 會先依子類別目錄再依產品，組織欄位的值。</span><span class="sxs-lookup"><span data-stu-id="30d65-157">Steps 3 and 4 organize the values for the fields first by subcategory, and then by product.</span></span>  
  
5.  <span data-ttu-id="30d65-158">將 [Sales] 拖曳至 [值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30d65-158">Drag Sales to **Values**.</span></span>  
  
     <span data-ttu-id="30d65-159">[Sales] 是使用 Sum 函數進行摘要，此為摘要數值欄位的預設函數。</span><span class="sxs-lookup"><span data-stu-id="30d65-159">Sales is summarized with the Sum function, the default function to summarize numeric fields.</span></span>  
  
6.  <span data-ttu-id="30d65-160">將 [Quantity] 拖曳至 [值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30d65-160">Drag Quantity to **Values**.</span></span>  
  
     <span data-ttu-id="30d65-161">[Quantity] 是使用 Sum 函數進行摘要。</span><span class="sxs-lookup"><span data-stu-id="30d65-161">Quantity is summarized with the Sum function.</span></span>  
  
     <span data-ttu-id="30d65-162">步驟 5 和步驟 6 指定了矩陣資料格要顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="30d65-162">Steps 5 and 6 specify the data to display in the matrix data cells.</span></span>  
  
7.  <span data-ttu-id="30d65-163">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="30d65-163">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="30d65-164">在 [選擇配置] 頁面的 [選項]\*\*\*\* 下方，確定已選取 [顯示小計和總計]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30d65-164">On the Choose the Layout page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
9. <span data-ttu-id="30d65-165">驗證已選取 [區塊式，小計位於下方]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30d65-165">Verify that **Blocked, subtotal below** is selected.</span></span>  
  
10. <span data-ttu-id="30d65-166">確定已選取 [展開/摺疊群組]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="30d65-166">Verify the option **Expand/collapse groups** is selected.</span></span>  
  
11. <span data-ttu-id="30d65-167">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="30d65-167">Click **Next**.</span></span>  
  
12. <span data-ttu-id="30d65-168">在 [選擇樣式] 頁面的 [樣式] 窗格中，選取 **[石板]**。</span><span class="sxs-lookup"><span data-stu-id="30d65-168">On the Choose a Style page, in the Styles pane, select **Slate**.</span></span>  
  
13. <span data-ttu-id="30d65-169">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="30d65-169">Click **Finish**.</span></span>  
  
     <span data-ttu-id="30d65-170">矩陣會加入至設計介面。</span><span class="sxs-lookup"><span data-stu-id="30d65-170">The matrix is added to the design surface.</span></span> <span data-ttu-id="30d65-171">[資料列群組] 窗格將顯示兩個資料列群組：Territory 和 SalesDate。</span><span class="sxs-lookup"><span data-stu-id="30d65-171">The Row Groups pane shows two row groups: Territory and SalesDate.</span></span> <span data-ttu-id="30d65-172">[資料行群組] 窗格則顯示這兩個資料行群組：Subcategory 和 Product。</span><span class="sxs-lookup"><span data-stu-id="30d65-172">The Column Groups pane shows two column groups: Subcategory and Product.</span></span> <span data-ttu-id="30d65-173">詳細資料是資料集查詢擷取的所有資料。</span><span class="sxs-lookup"><span data-stu-id="30d65-173">Detail data is all the data that is retrieved by the dataset query.</span></span>  
  
14. <span data-ttu-id="30d65-174">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="30d65-174">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="30d65-175">矩陣會針對特定日期銷售的每個產品，顯示產品所屬的子類別目錄和銷售領域。</span><span class="sxs-lookup"><span data-stu-id="30d65-175">For each product that is sold on a specific date, the matrix shows the subcategory to which the product belongs and the territory of the sales.</span></span>  
  
##  <a name="3-format-data"></a><a name="FormatData"></a><span data-ttu-id="30d65-176">3. 將資料格式化</span><span class="sxs-lookup"><span data-stu-id="30d65-176">3. Format Data</span></span>  
 <span data-ttu-id="30d65-177">根據預設，[Sales] 欄位的摘要資料會顯示一般數字，而 [SalesDate] 欄位會顯示日期加上時間資訊。</span><span class="sxs-lookup"><span data-stu-id="30d65-177">By default, the summary data for the Sales field displays a general number and the SalesDate field displays both date and time information.</span></span> <span data-ttu-id="30d65-178">格式化以使 [Sales] 欄位將數字顯示為貨幣，讓 [SalesDate] 欄位只顯示日期。</span><span class="sxs-lookup"><span data-stu-id="30d65-178">Format the Sales field to display the number as currency and the SalesDate field to display only the date.</span></span> <span data-ttu-id="30d65-179">切換 [預留位置樣式]\*\*\*\*，將格式化的文字方塊和預留位置文字顯示為範例值。</span><span class="sxs-lookup"><span data-stu-id="30d65-179">Toggle **Placeholder Styles** to display formatted text boxes and placeholder text as sample values.</span></span>  
  
#### <a name="to-format-fields"></a><span data-ttu-id="30d65-180">格式化欄位</span><span class="sxs-lookup"><span data-stu-id="30d65-180">To format fields</span></span>  
  
1.  <span data-ttu-id="30d65-181">按一下 [**設計**]，切換至設計檢視。</span><span class="sxs-lookup"><span data-stu-id="30d65-181">Click **Design** to switch to design view.</span></span>  
  
2.  <span data-ttu-id="30d65-182">按下 Ctrl 鍵，然後選取包含 `[Sum(Sales)]`的 9 個資料格。</span><span class="sxs-lookup"><span data-stu-id="30d65-182">Press the Ctrl key, and then select the nine cells that contain `[Sum(Sales)]`.</span></span>  
  
3.  <span data-ttu-id="30d65-183">在 **[主資料夾]** 索引標籤的 **[數值]** 群組中，按一下 **[貨幣]**。</span><span class="sxs-lookup"><span data-stu-id="30d65-183">On the **Home** tab, in the **Number** group, click **Currency**.</span></span> <span data-ttu-id="30d65-184">資料格隨即變更為顯示格式化貨幣。</span><span class="sxs-lookup"><span data-stu-id="30d65-184">The cells changeto show the formatted currency.</span></span>  
  
     <span data-ttu-id="30d65-185">如果您的地區設定為 [英文 (美國)]，則預設範例文字會是 [**$12,345.00**]。</span><span class="sxs-lookup"><span data-stu-id="30d65-185">If your regional setting is English (United States), the default sample text is [**$12,345.00**].</span></span> <span data-ttu-id="30d65-186">如果您看不到範例貨幣值，請按一下 [**數位**] 群組中的 [**預留位置樣式**]，然後按一下 [**範例值**]。</span><span class="sxs-lookup"><span data-stu-id="30d65-186">If you do not see an example currency value, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
4.  <span data-ttu-id="30d65-187">按一下包含 `[SalesDate]`的資料格。</span><span class="sxs-lookup"><span data-stu-id="30d65-187">Click the cell that contains `[SalesDate]`.</span></span>  
  
5.  <span data-ttu-id="30d65-188">在 [**數位**] 群組中，從下拉式清單選取 [**日期**]。</span><span class="sxs-lookup"><span data-stu-id="30d65-188">In the **Number** group, from the drop-down list, select **Date**.</span></span>  
  
     <span data-ttu-id="30d65-189">資料格會顯示範例日期 **[1/31/2000]**。</span><span class="sxs-lookup"><span data-stu-id="30d65-189">The cell displays the example date **[1/31/2000]**.</span></span> <span data-ttu-id="30d65-190">如果您看不到範例日期，請按一下 [數字]\*\*\*\* 群組中的 [預留位置樣式]\*\*\*\*，然後按一下 [範例值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30d65-190">If you do not see an example date, click **Placeholder Styles** in the **Numbers** group, and then click **Sample Values**.</span></span>  
  
6.  <span data-ttu-id="30d65-191">按一下 [執行]\*\*\*\* 以預覽報表。</span><span class="sxs-lookup"><span data-stu-id="30d65-191">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="30d65-192">日期值如今只顯示日期，而銷售值顯示為貨幣。</span><span class="sxs-lookup"><span data-stu-id="30d65-192">The date values display only dates and the sales values display as currency.</span></span>  
  
##  <a name="4-add-adjacent-column-group"></a><a name="AdjacentGroup"></a><span data-ttu-id="30d65-193">4. 加入連續的資料行群組</span><span class="sxs-lookup"><span data-stu-id="30d65-193">4. Add Adjacent Column Group</span></span>  
 <span data-ttu-id="30d65-194">您可以將資料列和資料行群組巢狀套疊為父子關聯性，或彼此相鄰的同層級關聯性。</span><span class="sxs-lookup"><span data-stu-id="30d65-194">You can nest row and column groups in parent child relationships or adjacent in sibling relationships.</span></span>  
  
 <span data-ttu-id="30d65-195">加入一個與 Subcategory 資料行群組相鄰資料行群組、複製資料格以填入新資料行群組，然後使用運算式建立新資料行群組首的值。</span><span class="sxs-lookup"><span data-stu-id="30d65-195">Add a column group that is adjacent to the Subcategory column group, copy cells to populate the new column group, and then use an expression to create the value of the column group header.</span></span>  
  
#### <a name="to-add-an-adjacent-column-group"></a><span data-ttu-id="30d65-196">加入相鄰資料行群組</span><span class="sxs-lookup"><span data-stu-id="30d65-196">To add an adjacent column group</span></span>  
  
1.  <span data-ttu-id="30d65-197">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="30d65-197">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="30d65-198">以滑鼠右鍵按一下包含 `[Subcategory]` 的資料格，並指向 [新增群組]\*\*\*\*，然後按一下 [右方相鄰]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30d65-198">Right-click the cell that contains `[Subcategory]`, point to **Add Group**, and then click **Adjacent Right**.</span></span>  
  
     <span data-ttu-id="30d65-199">**[Tablix 群組]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="30d65-199">The **Tablix Group** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="30d65-200">在 [群組依據]\*\*\*\* 清單中選取 [SalesDate]，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30d65-200">In the **Group By** list, select SalesDate, and then click **OK**.</span></span>  
  
     <span data-ttu-id="30d65-201">新的資料行群組就會加入到 Subcategory 資料行群組的左邊。</span><span class="sxs-lookup"><span data-stu-id="30d65-201">A new column group is added to the left of the Subcategory column group.</span></span>  
  
4.  <span data-ttu-id="30d65-202">以滑鼠右鍵按一下新資料行群組中包含 `[SalesDate],` 的資料格，然後按一下 [運算式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30d65-202">Right-click the cell in the new column group that contains `[SalesDate],` and then click **Expression**.</span></span>  
  
5.  <span data-ttu-id="30d65-203">將下列運算式複製到運算式方塊中。</span><span class="sxs-lookup"><span data-stu-id="30d65-203">Copy the following expression to expression box.</span></span>  
  
    ```  
    =WeekdayName(DatePart("w",Fields!SalesDate.Value))  
    ```  
  
     <span data-ttu-id="30d65-204">此運算式會從銷售日期擷取星期幾。</span><span class="sxs-lookup"><span data-stu-id="30d65-204">This expression extracts the weekday name from the sales date.</span></span> <span data-ttu-id="30d65-205">如需詳細資訊，請參閱[運算式 &#40;報表產生器及 SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="30d65-205">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md).</span></span>  
  
6.  <span data-ttu-id="30d65-206">以滑鼠右鍵按一下 Subcategory 資料行群組中包含 [Total] 的資料格，然後按一下 [複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30d65-206">Right-click the cell in the Subcategory column group that contains Total, and then click **Copy**.</span></span>  
  
7.  <span data-ttu-id="30d65-207">以滑鼠右鍵按一下步驟 5 建立之運算式所在資料格正下方的資料格，然後按一下 [貼上]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30d65-207">Right-click the cell immediately below the cell that contains the expression you created in step 5 and click **Paste**.</span></span>  
  
8.  <span data-ttu-id="30d65-208">按下 Ctrl 鍵。</span><span class="sxs-lookup"><span data-stu-id="30d65-208">Press the Ctrl key.</span></span>  
  
9. <span data-ttu-id="30d65-209">在 Subcategory 群組中，按一下 [Sales] 資料行標頭及其下方的三個資料格，並按一下滑鼠右鍵，然後按一下 [複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30d65-209">In the Subcategory group, click the Sales column header and the three cells below it, right-click, and then click **Copy**.</span></span>  
  
10. <span data-ttu-id="30d65-210">將這四個資料格貼至新資料行群組中的四個空白資料格。</span><span class="sxs-lookup"><span data-stu-id="30d65-210">Paste the four cells into the four empty cells in the new column group.</span></span>  
  
11. <span data-ttu-id="30d65-211">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="30d65-211">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="30d65-212">報表多出兩個資料行，名為「星期一」和「星期二」。</span><span class="sxs-lookup"><span data-stu-id="30d65-212">The report includes columns named Monday and Tuesday.</span></span> <span data-ttu-id="30d65-213">資料集只包含這兩天的資料。</span><span class="sxs-lookup"><span data-stu-id="30d65-213">The dataset contains only data for these two days.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30d65-214">如果資料中還有別的星期，報表也會納入其資料行。</span><span class="sxs-lookup"><span data-stu-id="30d65-214">If the data included other days, the report would include columns for them as well.</span></span> <span data-ttu-id="30d65-215">每個資料行都有欄位標題、 `Sales` 和銷售總計（依地區）。</span><span class="sxs-lookup"><span data-stu-id="30d65-215">Each column has the column header, `Sales`, and sales totals by territory.</span></span>  
  
##  <a name="5-change-column-widths"></a><a name="Width"></a><span data-ttu-id="30d65-216">5. 變更資料行寬度</span><span class="sxs-lookup"><span data-stu-id="30d65-216">5. Change Column Widths</span></span>  
 <span data-ttu-id="30d65-217">含有矩陣的報表在執行時，通常會水平且垂直地展開。</span><span class="sxs-lookup"><span data-stu-id="30d65-217">A report that includes a matrix typically expands horizontally as well as vertically when it runs.</span></span> <span data-ttu-id="30d65-218">若您打算將報表匯出為印刷報表採用的格式，如 Microsoft Word 或 Adobe PDF，控制水平展開程度就特別重要。</span><span class="sxs-lookup"><span data-stu-id="30d65-218">Controlling horizontal expansion is particularly important if you plan to export the report to formats such as Microsoft Word or Adobe PDF that are used for printed reports.</span></span> <span data-ttu-id="30d65-219">如果報表水平地展開成跨多個頁面，將造成印刷報表難以判讀。</span><span class="sxs-lookup"><span data-stu-id="30d65-219">If the report expands horizontally across multiple pages, the printed report is difficult to understand.</span></span> <span data-ttu-id="30d65-220">為了盡量減少水平展開程度，您可將資料行寬度調整成以不換行的方式顯示資料所需的量。</span><span class="sxs-lookup"><span data-stu-id="30d65-220">To minimize horizontal expansion, you can resize columns to be only the width necessary to display the data without wrapping.</span></span> <span data-ttu-id="30d65-221">您也可以重新命名資料行，使顯示資料所需的寬度恰能容納其標題。</span><span class="sxs-lookup"><span data-stu-id="30d65-221">You can also rename columns so that their titles fit the width needed to display the data.</span></span>  
  
#### <a name="to-rename-and-resize-the-columns"></a><span data-ttu-id="30d65-222">資料行重新命名與調整大小</span><span class="sxs-lookup"><span data-stu-id="30d65-222">To rename and resize the columns</span></span>  
  
1.  <span data-ttu-id="30d65-223">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="30d65-223">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="30d65-224">選取離左邊最遠的 [Quantity] 資料行中的文字，然後鍵入 **QTY**。</span><span class="sxs-lookup"><span data-stu-id="30d65-224">Select the text in the furthest Quantity column to the left, and then type **QTY**.</span></span>  
  
     <span data-ttu-id="30d65-225">該資料行標題現已變成 QTY。</span><span class="sxs-lookup"><span data-stu-id="30d65-225">The column title is now QTY.</span></span>  
  
3.  <span data-ttu-id="30d65-226">針對名為 Quantity 的其餘資料行重複步驟 2，</span><span class="sxs-lookup"><span data-stu-id="30d65-226">Repeat step 2 for the other columns named Quantity.</span></span> <span data-ttu-id="30d65-227">總共還有兩個。</span><span class="sxs-lookup"><span data-stu-id="30d65-227">There are two of them.</span></span>  
  
4.  <span data-ttu-id="30d65-228">按一下矩陣，使資料行和資料列控點出現在矩陣的上面和旁邊。</span><span class="sxs-lookup"><span data-stu-id="30d65-228">Click the matrix so that column and row handles appear above and next to the matrix.</span></span>  
  
     <span data-ttu-id="30d65-229">沿著資料表頂端和側邊的灰色長條是資料行和資料列控點。</span><span class="sxs-lookup"><span data-stu-id="30d65-229">The gray bars along the top and side of the table are the column and row handles.</span></span>  
  
5.  <span data-ttu-id="30d65-230">首先要調整離左邊最遠的 QTY 資料行大小：指向該資料行控點之間的線條，使游標變成雙箭頭。</span><span class="sxs-lookup"><span data-stu-id="30d65-230">To resize the furthest QTY column to the left, point to the line between column handles so that the cursor changes into a double arrow.</span></span> <span data-ttu-id="30d65-231">將資料行往左拖曳，直到其寬度為 1/2 英吋。</span><span class="sxs-lookup"><span data-stu-id="30d65-231">Drag the column towards the left until it is 1/2 inch wide.</span></span>  
  
     <span data-ttu-id="30d65-232">要顯示數量的資料行有 1/2 英吋寬就已足夠。</span><span class="sxs-lookup"><span data-stu-id="30d65-232">A column width of 1/2 inch is adequate to display the quantity.</span></span>  
  
6.  <span data-ttu-id="30d65-233">針對名為 QTY 的其餘資料行重複步驟 5。</span><span class="sxs-lookup"><span data-stu-id="30d65-233">Repeat step 5 for the other columns named QTY.</span></span>  
  
7.  <span data-ttu-id="30d65-234">按一下 [執行]\*\*\*\* 以預覽報表。</span><span class="sxs-lookup"><span data-stu-id="30d65-234">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="30d65-235">報表中包含數量的資料行現已改名為 QTY 而且較窄。</span><span class="sxs-lookup"><span data-stu-id="30d65-235">The columns in the report that contains quantities are now named QTY and the columns are narrower.</span></span>  
  
##  <a name="6-merge-matrix-cells"></a><a name="MergeCells"></a><span data-ttu-id="30d65-236">6. 合併矩陣資料格</span><span class="sxs-lookup"><span data-stu-id="30d65-236">6. Merge Matrix Cells</span></span>  
 <span data-ttu-id="30d65-237">邊角區域是位於矩陣的左上角。</span><span class="sxs-lookup"><span data-stu-id="30d65-237">The corner area is in the upper left corner of the matrix.</span></span> <span data-ttu-id="30d65-238">邊角區域內的資料格數目，會隨矩陣中的資料列與資料行群組數目而有所不同。</span><span class="sxs-lookup"><span data-stu-id="30d65-238">Depending on the number of row and column groups in the matrix, the number of cells in the corner area varies.</span></span> <span data-ttu-id="30d65-239">本教學課程建置的矩陣其邊角區域內有四個資料格。</span><span class="sxs-lookup"><span data-stu-id="30d65-239">The matrix, built in this tutorial, has four cells in its corner area.</span></span> <span data-ttu-id="30d65-240">這些資料格排成兩列兩欄，反映了資料列與資料行群組階層的深度。</span><span class="sxs-lookup"><span data-stu-id="30d65-240">The cells are arranged in two rows and two columns, reflecting the depth of row and column group hierarchies.</span></span> <span data-ttu-id="30d65-241">本報表用不到這四個資料格，因此您要將其合併為單一資料格。</span><span class="sxs-lookup"><span data-stu-id="30d65-241">The four cells are not used in this report and you will merge them into one.</span></span>  
  
#### <a name="to-merge-matrix-cells"></a><span data-ttu-id="30d65-242">合併矩陣資料格</span><span class="sxs-lookup"><span data-stu-id="30d65-242">To merge matrix cells</span></span>  
  
1.  <span data-ttu-id="30d65-243">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="30d65-243">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="30d65-244">按一下矩陣，使資料行和資料列控點出現在矩陣的上面和旁邊。</span><span class="sxs-lookup"><span data-stu-id="30d65-244">Click the matrix so that column and row handles appear above and next to the matrix.</span></span>  
  
3.  <span data-ttu-id="30d65-245">按下 Ctrl 鍵，然後選取四個邊角資料格。</span><span class="sxs-lookup"><span data-stu-id="30d65-245">Press the Ctrl key, and then select the four corner cells.</span></span>  
  
4.  <span data-ttu-id="30d65-246">以滑鼠右鍵按一下資料格，然後按一下 [**合併資料格**]。</span><span class="sxs-lookup"><span data-stu-id="30d65-246">Right-click the cells and then click **Merge Cells**.</span></span>  
  
5.  <span data-ttu-id="30d65-247">以滑鼠右鍵按一下邊角資料格，然後按一下 [**文字方塊屬性**]。</span><span class="sxs-lookup"><span data-stu-id="30d65-247">Right-click the corner cell, and then click **Text Box Properties**.</span></span>  
  
6.  <span data-ttu-id="30d65-248">按一下 **[填滿]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="30d65-248">Click the **Fill** tab.</span></span>  
  
7.  <span data-ttu-id="30d65-249">按一下 [ (***fx***) ] 按鈕以取得**填滿色彩**。</span><span class="sxs-lookup"><span data-stu-id="30d65-249">Click the (***fx***) button for **Fill color**.</span></span>  
  
8.  <span data-ttu-id="30d65-250">複製下列運算式並貼入運算式方塊中。</span><span class="sxs-lookup"><span data-stu-id="30d65-250">Copy and paste the following expression in the expression box.</span></span>  
  
    ```  
    #96a4b2  
    ```  
  
     <span data-ttu-id="30d65-251">這是 [石板] 樣式採用的藍灰色彩的 RGB 十六進位值。</span><span class="sxs-lookup"><span data-stu-id="30d65-251">This is the RGB hex value for a gray blue color used in the Slate style.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. <span data-ttu-id="30d65-252">按一下 [執行]\*\*\*\* 以預覽報表。</span><span class="sxs-lookup"><span data-stu-id="30d65-252">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="30d65-253">上方邊角矩陣變成了單一資料格，且其色彩與資料列群組及資料行群組資料格相同。</span><span class="sxs-lookup"><span data-stu-id="30d65-253">The upper corner matrix is a single cell and has the same color as the row group and column group cells.</span></span>  
  
##  <a name="7-add-a-report-header-and-report-title"></a><a name="HeaderTitle"></a><span data-ttu-id="30d65-254">7. 加入報表頁首和報表標題</span><span class="sxs-lookup"><span data-stu-id="30d65-254">7. Add a Report Header and Report Title</span></span>  
 <span data-ttu-id="30d65-255">報表標題會出現在報表的頂端。</span><span class="sxs-lookup"><span data-stu-id="30d65-255">A report title appears at the top of the report.</span></span> <span data-ttu-id="30d65-256">您可以將報表標題放置在報表頁首，如果報表不使用報表頁首，則可以放置在報表主體頂端的文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="30d65-256">You can place the report title in a report header or if the report does not use one, in a text box at the top of the report body.</span></span> <span data-ttu-id="30d65-257">在本教學課程中，您將移除報表頂端的文字方塊，然後加入標題至頁首。</span><span class="sxs-lookup"><span data-stu-id="30d65-257">In this tutorial, you will remove the text box at the top of the report and add a title to the header.</span></span>  
  
#### <a name="to-add-a-report-header-and-report-title"></a><span data-ttu-id="30d65-258">加入報表頁首和報表標題</span><span class="sxs-lookup"><span data-stu-id="30d65-258">To add a report header and report title</span></span>  
  
1.  <span data-ttu-id="30d65-259">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="30d65-259">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="30d65-260">按一下包含 [**按一下以加入標題**] 之報表主體頂端的文字方塊，然後按下 Delete 鍵。</span><span class="sxs-lookup"><span data-stu-id="30d65-260">Click the text box at the top of the report body that contains **Click to add title**, and then press the Delete key.</span></span>  
  
3.  <span data-ttu-id="30d65-261">在功能區的 [**插入**] 索引卷**標**上，按一下 [頁首]，然後按一下 [**新增標頭**]。</span><span class="sxs-lookup"><span data-stu-id="30d65-261">On the **Insert** tab of the ribbon, click **Header** and then click **Add Header**.</span></span>  
  
     <span data-ttu-id="30d65-262">頁首就會加入至報表主體頂端。</span><span class="sxs-lookup"><span data-stu-id="30d65-262">A header is added to the top of the report body.</span></span>  
  
4.  <span data-ttu-id="30d65-263">在 [插入]\*\*\*\* 索引標籤上，按一下 [文字方塊]\*\*\*\*，然後將文字方塊拖曳至報表標題。</span><span class="sxs-lookup"><span data-stu-id="30d65-263">On the **Insert** tab, click **Text Box**, and then drag a text box inside the report header.</span></span> <span data-ttu-id="30d65-264">將文字方塊調整成長約 6 英吋且高約 3/4 英吋，然後放到報表頁首的左側。</span><span class="sxs-lookup"><span data-stu-id="30d65-264">Make the text box about 6 inches long and 3/4 inch tall and place it on the left side of the report header.</span></span>  
  
5.  <span data-ttu-id="30d65-265">在文字方塊中，鍵入 **Sales by Territory, Subcategory, and Day**。</span><span class="sxs-lookup"><span data-stu-id="30d65-265">In the text box, type **Sales by Territory, Subcategory, and Day**.</span></span>  
  
6.  <span data-ttu-id="30d65-266">選取您輸入的文字，再按一下滑鼠右鍵，然後按一下 [**文字屬性**]。</span><span class="sxs-lookup"><span data-stu-id="30d65-266">Select the text you typed, right-click, and then click **Text Properties**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="30d65-267">若要一次格式化整串文字，必須選取連續字元。</span><span class="sxs-lookup"><span data-stu-id="30d65-267">To format characters at the same time, they must be contiguous.</span></span>  
  
7.  <span data-ttu-id="30d65-268">按一下 [**文字屬性**] 對話方塊中的 [**字型**]。</span><span class="sxs-lookup"><span data-stu-id="30d65-268">In the **Text Properties** dialog box, click **Font**.</span></span>  
  
8.  <span data-ttu-id="30d65-269">在 [**字型**] 清單中，選取 [ **Times New Roman**;在 [**大小**] 中選取 [ **24 pt**]，在 [**色彩**] 中選取 [**褐紫紅色**]，**並選取 [\*\*\*\*樣式**</span><span class="sxs-lookup"><span data-stu-id="30d65-269">In the **Font** list, select **Times New Roman**; in **Size** select **24 pt**, in **Color** select **Maroon**, and in **Style** select **Italic**.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. <span data-ttu-id="30d65-270">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="30d65-270">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="30d65-271">在報表中，報表頁首包含報表標題。</span><span class="sxs-lookup"><span data-stu-id="30d65-271">The report includes a report title in the report header.</span></span>  
  
##  <a name="8-save-the-report"></a><a name="Save"></a><span data-ttu-id="30d65-272">8. 儲存報表</span><span class="sxs-lookup"><span data-stu-id="30d65-272">8. Save the Report</span></span>  
 <span data-ttu-id="30d65-273">您可以將報表儲存至報表伺服器、SharePoint 文件庫或您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="30d65-273">You can save reports to a report server, SharePoint library, or your computer.</span></span>  
  
 <span data-ttu-id="30d65-274">本教學課程會將報表儲存至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="30d65-274">In this tutorial, save the report to a report server.</span></span> <span data-ttu-id="30d65-275">如果您沒有報表伺服器的存取權，請將報表儲存在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="30d65-275">If you do not have access to a report server, save the report to your computer.</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="30d65-276">若要將報表儲存在報表伺服器上</span><span class="sxs-lookup"><span data-stu-id="30d65-276">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="30d65-277">在 **[報表產生器]** 按鈕中，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="30d65-277">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="30d65-278">按一下 **[最近使用的網站和伺服器]**。</span><span class="sxs-lookup"><span data-stu-id="30d65-278">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="30d65-279">選取或輸入您有權儲存報表之報表伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="30d65-279">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="30d65-280">「正在連接到報表伺服器」訊息隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="30d65-280">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="30d65-281">連接完成時，您將會看見報表伺服器管理員指定為預設報表位置之報表資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="30d65-281">When the connection is complete, you will see the contents of the report folder that the report server administrator specified as the default report location.</span></span>  
  
4.  <span data-ttu-id="30d65-282">在 [名稱]\*\*\*\* 中，將預設名稱取代為 **SalesByTerritorySubcategory**。</span><span class="sxs-lookup"><span data-stu-id="30d65-282">In **Name**, replace the default name with **SalesByTerritorySubcategory**.</span></span>  
  
5.  <span data-ttu-id="30d65-283">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="30d65-283">Click **Save**.</span></span>  
  
 <span data-ttu-id="30d65-284">報表就會儲存至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="30d65-284">The report is saved to the report server.</span></span> <span data-ttu-id="30d65-285">您連接之報表伺服器的名稱會顯示在視窗底部的狀態列中。</span><span class="sxs-lookup"><span data-stu-id="30d65-285">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="30d65-286">將報表儲存到您的電腦上</span><span class="sxs-lookup"><span data-stu-id="30d65-286">To save the report on your computer</span></span>  
  
1.  <span data-ttu-id="30d65-287">在 **[報表產生器]** 按鈕中，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="30d65-287">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="30d65-288">按一下 **[桌面]**、 **[我的文件]** 或 **[我的電腦]**，然後瀏覽到您要儲存報表的資料夾。</span><span class="sxs-lookup"><span data-stu-id="30d65-288">Click **Desktop**, **My Documents**, or **My computer**, and then browse to the folder where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="30d65-289">在 [名稱]\*\*\*\* 中，將預設名稱取代為 **SalesByTerritorySubcategory**。</span><span class="sxs-lookup"><span data-stu-id="30d65-289">In **Name**, replace the default name with **SalesByTerritorySubcategory**.</span></span>  
  
4.  <span data-ttu-id="30d65-290">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="30d65-290">Click **Save**.</span></span>  
  
##  <a name="9-optional-rotate-text-box-270-degrees"></a><a name="RotateTextBox"></a><span data-ttu-id="30d65-291">9. (選擇性) 旋轉文字方塊270度</span><span class="sxs-lookup"><span data-stu-id="30d65-291">9. (Optional) Rotate Text Box 270 Degrees</span></span>  
 <span data-ttu-id="30d65-292">含有矩陣的報表在執行時，可能會水平且垂直地展開。</span><span class="sxs-lookup"><span data-stu-id="30d65-292">A report with matrices can expand horizontally and vertically when it runs.</span></span> <span data-ttu-id="30d65-293">如果將文字方塊旋轉 270 度 (垂直旋轉)，就比較不佔水平空間。</span><span class="sxs-lookup"><span data-stu-id="30d65-293">By rotating text boxes vertically, or 270 degrees, you can save horizontal space.</span></span> <span data-ttu-id="30d65-294">這樣轉譯後的報表將會變窄，且若匯出為 Microsoft Word 等格式，則大概都能容納於單一列印頁面上。</span><span class="sxs-lookup"><span data-stu-id="30d65-294">The rendered report is then narrower and if exported to a format such as Microsoft Word, will be more likely to fit on a printed page.</span></span>  
  
 <span data-ttu-id="30d65-295">文字方塊也可以將文字顯示成水平、垂直 (由上而下) 的方向。</span><span class="sxs-lookup"><span data-stu-id="30d65-295">A text box can also display text as horizontal, vertical (top to bottom).</span></span> <span data-ttu-id="30d65-296">如需詳細資訊，請參閱[文字方塊 &#40;報表產生器及 SSRS&#41;](report-design/text-boxes-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="30d65-296">For more information, see [Text Boxes &#40;Report Builder and SSRS&#41;](report-design/text-boxes-report-builder-and-ssrs.md).</span></span>  
  
#### <a name="to-rotate-text-box-270-degrees"></a><span data-ttu-id="30d65-297">將文字方塊旋轉 270 度</span><span class="sxs-lookup"><span data-stu-id="30d65-297">To rotate text box 270 degrees</span></span>  
  
1.  <span data-ttu-id="30d65-298">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="30d65-298">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="30d65-299">按一下包含 `[Territory].` 的資料格。</span><span class="sxs-lookup"><span data-stu-id="30d65-299">Click the cell that contains `[Territory].`</span></span>  
  
3.  <span data-ttu-id="30d65-300">在 [屬性] 窗格中，找出 WritingMode 屬性，並在其下拉式清單中選取 [ **Rotate270**]。</span><span class="sxs-lookup"><span data-stu-id="30d65-300">In the Properties pane, locate the WritingMode property and in its drop-down list, select **Rotate270**.</span></span>  
  
     <span data-ttu-id="30d65-301">如果 [屬性] 窗格並未開啟，請按一下功能區的 [檢視]\*\*\*\* 索引標籤，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30d65-301">If the Properties pane is not open, click the **View** tab of the ribbon, and then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="30d65-302">確認 [CanGrow] 屬性已設為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="30d65-302">Verify that the CanGrow property is set to `True`.</span></span>  
  
5.  <span data-ttu-id="30d65-303">將 [Territory] 資料行的寬度調整成 1/2 英吋，並刪除資料行標題。</span><span class="sxs-lookup"><span data-stu-id="30d65-303">Resize the Territory column to be 1/2 inch wide and delete the column title.</span></span>  
  
6.  <span data-ttu-id="30d65-304">按一下 [執行]\*\*\*\* 以預覽報表。</span><span class="sxs-lookup"><span data-stu-id="30d65-304">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="30d65-305">領域名稱的寫法為由上而下的垂直方向。</span><span class="sxs-lookup"><span data-stu-id="30d65-305">The territory name is written vertically, bottom to top.</span></span> <span data-ttu-id="30d65-306">Territory 資料列群組的高度會依領域名稱的長度而變化。</span><span class="sxs-lookup"><span data-stu-id="30d65-306">The height of the Territory row group varies by the length of the territory name.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="30d65-307">後續步驟</span><span class="sxs-lookup"><span data-stu-id="30d65-307">Next Steps</span></span>  
 <span data-ttu-id="30d65-308">以上總結如何建立矩陣報表的教學課程。</span><span class="sxs-lookup"><span data-stu-id="30d65-308">This concludes the tutorial for how to create a matrix report.</span></span> <span data-ttu-id="30d65-309">如需矩陣的詳細資訊，請參閱[資料表、矩陣和清單 &#40;報表產生器和 ssrs&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)、[矩陣 &#40;報表產生器和 ssrs&#41;](report-design/create-a-matrix-report-builder-and-ssrs.md)、 [tablix 資料區區域 &#40;報表產生器和 Ssrs&#41;](report-design/tablix-data-region-areas-report-builder-and-ssrs.md)，以及[tablix 資料區 &#40;報表產生器和 ssrs](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="30d65-309">For more information about matrices, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md), [Matrices &#40;Report Builder and SSRS&#41;](report-design/create-a-matrix-report-builder-and-ssrs.md), [Tablix Data Region Areas &#40;Report Builder and SSRS&#41;](report-design/tablix-data-region-areas-report-builder-and-ssrs.md), and [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30d65-310">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30d65-310">See Also</span></span>  
 <span data-ttu-id="30d65-311">[教學課程 &#40;報表產生器&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="30d65-311">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="30d65-312">SQL Server 2014 中的報表產生器</span><span class="sxs-lookup"><span data-stu-id="30d65-312">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
