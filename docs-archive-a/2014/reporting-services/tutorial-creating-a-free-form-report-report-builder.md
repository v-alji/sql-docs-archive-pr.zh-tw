---
title: 教學課程：建立自由格式報表 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 87288b59-faf2-4b1d-a8e4-a7582baedf2f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 515b0d2566efa4e11216a28648338c7ec43f3950
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706134"
---
# <a name="tutorial-creating-a-free-form-report-report-builder"></a><span data-ttu-id="c6d0e-102">教學課程：建立自由格式報表 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="c6d0e-102">Tutorial: Creating a Free Form Report (Report Builder)</span></span>
  <span data-ttu-id="c6d0e-103">本教學課程將教導您如何建立類似套印信件的 SSRS 自由格式報表。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-103">This tutorial teaches you how to create an SSRS free form report that resembles a forms letter.</span></span> <span data-ttu-id="c6d0e-104">您可以排列報表項目，以建立具有文字方塊、影像和其他資料區域的表單。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-104">You can arrange report items to create a form with text boxes, images and other data regions.</span></span>

 <span data-ttu-id="c6d0e-105">您在本教學課程中建立的報表，是以教學課程中所包含的範例銷售資料為基礎。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-105">The report you create in this tutorial is based on sample sales data that is included in the tutorial.</span></span> <span data-ttu-id="c6d0e-106">此報表會依領域將資訊分組，並顯示各領域的銷售經理姓名以及詳細和摘要銷售資訊。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-106">The report groups information by territory and displays the name of the sales manager for the territory as well as detailed and summary sales information.</span></span> <span data-ttu-id="c6d0e-107">您將使用清單資料區做為自由格式報表的基礎，然後加入含有影像的裝飾面板、插入資料的靜態文字、顯示詳細資訊的資料表，以及 (選擇性) 顯示摘要資訊的圓形圖和直條圖。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-107">You will use the list data region as the foundation for the free form report, and then add a decorative panel with an image, static text with data inserted, a table to show detailed information, and optionally, pie and column charts to display summary information.</span></span>

##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="c6d0e-108">您將瞭解的內容</span><span class="sxs-lookup"><span data-stu-id="c6d0e-108">What You Will Learn</span></span>
 <span data-ttu-id="c6d0e-109">在本教學課程中，您將學習如何執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c6d0e-109">In this tutorial, you will learn how to do the following:</span></span>

-   [<span data-ttu-id="c6d0e-110">建立空白報表、資料來源與資料集</span><span class="sxs-lookup"><span data-stu-id="c6d0e-110">Create a Blank Report, Data Source, and Dataset</span></span>](#BlankReport)

-   [<span data-ttu-id="c6d0e-111">加入及設定清單</span><span class="sxs-lookup"><span data-stu-id="c6d0e-111">Add and Configure a List</span></span>](#List)

-   [<span data-ttu-id="c6d0e-112">加入圖形</span><span class="sxs-lookup"><span data-stu-id="c6d0e-112">Add Graphics</span></span>](#Graphics)

-   [<span data-ttu-id="c6d0e-113">加入自由格式文字</span><span class="sxs-lookup"><span data-stu-id="c6d0e-113">Add Free Form Text</span></span>](#Text)

-   [<span data-ttu-id="c6d0e-114">加入資料表以顯示詳細資料</span><span class="sxs-lookup"><span data-stu-id="c6d0e-114">Add a Table to Show Details</span></span>](#Table)

-   [<span data-ttu-id="c6d0e-115">格式化資料</span><span class="sxs-lookup"><span data-stu-id="c6d0e-115">Format Data</span></span>](#Format)

-   [<span data-ttu-id="c6d0e-116">儲存報表</span><span class="sxs-lookup"><span data-stu-id="c6d0e-116">Save the Report</span></span>](#Save)

### <a name="other-optional-steps"></a><span data-ttu-id="c6d0e-117">其他選擇性步驟</span><span class="sxs-lookup"><span data-stu-id="c6d0e-117">Other Optional Steps</span></span>

-   [<span data-ttu-id="c6d0e-118">加入線條以區隔報表的各區域</span><span class="sxs-lookup"><span data-stu-id="c6d0e-118">Add a Line to Separate Areas of Report</span></span>](#Line)

-   [<span data-ttu-id="c6d0e-119">加入摘要資料視覺效果</span><span class="sxs-lookup"><span data-stu-id="c6d0e-119">Add Summary Data Visualization</span></span>](#Visualization)

 <span data-ttu-id="c6d0e-120">完成這個教學課程的估計時間：30 分鐘。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-120">Estimated time to complete this tutorial: 20 minutes.</span></span>

## <a name="requirements"></a><span data-ttu-id="c6d0e-121">需求</span><span class="sxs-lookup"><span data-stu-id="c6d0e-121">Requirements</span></span>
 <span data-ttu-id="c6d0e-122">如需需求的詳細資訊，請參閱[教學課程的必要條件 &#40;報表產生器&#41;](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-122">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>

##  <a name="1-create-a-blank-report-data-source-and-dataset"></a><a name="BlankReport"></a><span data-ttu-id="c6d0e-123">1. 建立空白報表、資料來源和資料集</span><span class="sxs-lookup"><span data-stu-id="c6d0e-123">1. Create a Blank Report, Data Source, and Dataset</span></span>

> [!NOTE]
>  <span data-ttu-id="c6d0e-124">在本教學課程中，查詢會包含資料值，因此報表不需要外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-124">In this tutorial, the query contains the data values so that the report does not need an external data source.</span></span> <span data-ttu-id="c6d0e-125">使用這種內部資料類型最適合用於學習目的，但這種方法會使查詢相當冗長。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-125">The use of this type of internal data is great for learning purposes, but the approach makes the query long.</span></span> <span data-ttu-id="c6d0e-126">.</span><span class="sxs-lookup"><span data-stu-id="c6d0e-126">.</span></span>

#### <a name="to-create-a-blank-report"></a><span data-ttu-id="c6d0e-127">建立空白報表</span><span class="sxs-lookup"><span data-stu-id="c6d0e-127">To create a blank report</span></span>

1.  <span data-ttu-id="c6d0e-128">按一下 **[開始]**、依序指向 **[程式集]** 和 **[Microsoft SQL Server 2012 報表產生器]**，然後按一下 **[報表產生器]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-128">Click **Start**, point to **Programs**, point to **Microsoft SQL Server 2012 Report Builder**, and then click **Report Builder**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="c6d0e-129">**[使用者入門]** 對話方塊應會隨即出現。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-129">The **Getting Started** dialog box should appear.</span></span> <span data-ttu-id="c6d0e-130">如果沒有出現，請從 [報表產生器] 按鈕按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-130">If it does not, from the Report Builder button, click **New**.</span></span>

2.  <span data-ttu-id="c6d0e-131">在 **[使用者入門]** 對話方塊的左窗格中，確認已選取 **[新增報表]** 。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-131">In the left pane of the **Getting Started** dialog box, verify that **New Report** is selected.</span></span>

3.  <span data-ttu-id="c6d0e-132">在右窗格中，按一下 **[空白報表]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-132">In the right pane, click **Blank Report**.</span></span>

#### <a name="to-create-a-new-data-source"></a><span data-ttu-id="c6d0e-133">建立新資料來源</span><span class="sxs-lookup"><span data-stu-id="c6d0e-133">To create a new data source</span></span>

1.  <span data-ttu-id="c6d0e-134">在 [報表資料] 窗格中，按一下 **[新增]**，然後按一下 **[資料來源]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-134">In the Report Data pane, click **New**, and then click **Data Source**.</span></span>

2.  <span data-ttu-id="c6d0e-135">在方塊中 `Name` ，輸入： **ListDataSource**</span><span class="sxs-lookup"><span data-stu-id="c6d0e-135">In the `Name` box, type: **ListDataSource**</span></span>

3.  <span data-ttu-id="c6d0e-136">按一下 **[使用內嵌於報表中的連接]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-136">Click **Use a connection embedded in my report**.</span></span>

4.  <span data-ttu-id="c6d0e-137">確認連線類型為 [Microsoft SQL Server]，然後在 [**連接字串**] 方塊中輸入： **Data Source \<servername> =**</span><span class="sxs-lookup"><span data-stu-id="c6d0e-137">Verify that the connection type is Microsoft SQL Server, and then in the **Connection string** box type: **Data Source = \<servername>**</span></span>

     <span data-ttu-id="c6d0e-138">\<servername>例如，Report001) 會指定已安裝 SQL Server 資料庫引擎實例的電腦。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-138">\<servername>, for example Report001, specifies a computer on which an instance of the SQL Server Database Engine is installed.</span></span> <span data-ttu-id="c6d0e-139">由於報表資料不是擷取自 SQL Server 資料庫，您不必加上資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-139">Because the report data is not extracted from a SQL Server database, you need not include the name of a database.</span></span> <span data-ttu-id="c6d0e-140">指定之伺服器上的預設資料庫將用來剖析查詢。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-140">The default database on the specified server is used to parse the query.</span></span>

5.  <span data-ttu-id="c6d0e-141">按一下 [認證] \*\*\*\*，並輸入連接到 SQL Server Database Engine 執行個體所需的認證。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-141">Click **Credentials**, and enter the credentials needed to connect to the instance of the SQL Server Database Engine.</span></span>

6.  <span data-ttu-id="c6d0e-142">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-142">Click **OK**.</span></span>

#### <a name="to-create-a-new-dataset"></a><span data-ttu-id="c6d0e-143">建立新資料集</span><span class="sxs-lookup"><span data-stu-id="c6d0e-143">To create a new dataset</span></span>

1.  <span data-ttu-id="c6d0e-144">在 [報表資料] 窗格中，按一下 **[新增]**，然後按一下 **[資料集]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-144">In the Report Data pane, click **New**, and then click **Dataset**.</span></span>

2.  <span data-ttu-id="c6d0e-145">在方塊中 `Name` ，輸入： **ListDataset。**</span><span class="sxs-lookup"><span data-stu-id="c6d0e-145">In the `Name` box, type: **ListDataset.**</span></span>

3.  <span data-ttu-id="c6d0e-146">按一下 [使用內嵌在我的報表中的資料集] \*\*\*\*，並確認資料來源是 **ListDataSource**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-146">Click **Use a dataset embedded in my report**, and verify that the data source is **ListDataSource**.</span></span>

4.  <span data-ttu-id="c6d0e-147">確認已選取 **[文字]** 查詢類型，然後按一下 **[查詢設計工具]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-147">Verify that the **Text** query type is selected, and then click **Query Designer**.</span></span>

5.  <span data-ttu-id="c6d0e-148">按一下 **[當成文字編輯]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-148">Click **Edit as Text**.</span></span>

6.  <span data-ttu-id="c6d0e-149">複製下列查詢並貼入查詢窗格中：</span><span class="sxs-lookup"><span data-stu-id="c6d0e-149">Copy and paste the following query into the query pane:</span></span>

    ```
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity
    ```

7.  <span data-ttu-id="c6d0e-150">按一下 [執行] 圖示即可執行查詢。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-150">Click Run icon to run the query.</span></span>

     <span data-ttu-id="c6d0e-151">查詢結果會成為可供報表顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-151">The query results are the data available to display in your report.</span></span>

     <span data-ttu-id="c6d0e-152">![查詢設計工具](../../2014/tutorials/media/tutorial-querydesigner.png "查詢設計工具")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-152">![Query Designer](../../2014/tutorials/media/tutorial-querydesigner.png "Query Designer")</span></span>

8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

##  <a name="2-add-and-configure-a-list"></a><a name="List"></a><span data-ttu-id="c6d0e-153">2. 加入及設定清單</span><span class="sxs-lookup"><span data-stu-id="c6d0e-153">2. Add and Configure a List</span></span>
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="c6d0e-154">提供三個資料區範本：資料表、矩陣和清單。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-154">provides three data region templates: table, matrix, and list.</span></span> <span data-ttu-id="c6d0e-155">這些範本都是以 Tablix 資料區域為基礎。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-155">These templates are all based on a tablix data region.</span></span>

 <span data-ttu-id="c6d0e-156">在本教學課程中，您將使用清單，在類似新聞稿的報表中顯示各銷售領域的銷售資訊。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-156">In this tutorial, you will use a list to display the sales information for sales territories in a report that resembles a newsletter.</span></span> <span data-ttu-id="c6d0e-157">此資訊是依領域分組。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-157">The information is grouped by territory.</span></span> <span data-ttu-id="c6d0e-158">您要加入新的資料列群組來依領域分組資料，然後刪除內建的 [詳細資料] 資料列群組。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-158">You will add a new row group that groups data by territory, and then delete the built-in Details row group.</span></span> <span data-ttu-id="c6d0e-159">這個清單範本相當適合用來建立自由格式報表。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-159">The list template is ideal for creating free form reports.</span></span> <span data-ttu-id="c6d0e-160">如需詳細資訊，請參閱[&#40;報表產生器和 SSRS&#41;清單](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-160">For more information, see [Lists &#40;Report Builder and SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="c6d0e-161">此報表會使用 Letter (8.5 X11) 紙張大小和 1 英吋的邊界。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-161">This report uses the paper size Letter (8.5 X11) and 1 inch margins.</span></span> <span data-ttu-id="c6d0e-162">若報表頁面高度超過 9 英吋或寬度超過 6 1/2 英吋，則可能產生空白頁面。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-162">A report page taller than 9 inches or wider than 6 1/2 inches might generate blank pages.</span></span>

#### <a name="to-add-a-list"></a><span data-ttu-id="c6d0e-163">加入清單</span><span class="sxs-lookup"><span data-stu-id="c6d0e-163">To add a list</span></span>

1.  <span data-ttu-id="c6d0e-164">在功能區的 **[插入]** 索引標籤上，按一下 **[資料區域]** 區域內的 **[清單]** ，然後將清單拖曳到報表主體內。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-164">On the **Insert** tab of the ribbon, in the **Data Regions** area, click **List** and then drag the list inside the report body.</span></span> <span data-ttu-id="c6d0e-165">將清單調整成高 7 英吋且寬 6.25 英吋。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-165">Make the list 7 inches tall and 6.25 inches wide.</span></span>

2.  <span data-ttu-id="c6d0e-166">按一下清單內部，在清單頂端按一下滑鼠右鍵，然後按一下 [Tablix 屬性] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-166">Click inside the list, right-click the top of the list, and then click **Tablix Properties**.</span></span>

     <span data-ttu-id="c6d0e-167">![新增清單](../../2014/tutorials/media/tutorial-addinglistwithnumbers.png "新增清單")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-167">![Adding list](../../2014/tutorials/media/tutorial-addinglistwithnumbers.png "Adding list")</span></span>

3.  <span data-ttu-id="c6d0e-168">從 **[資料集名稱]** 下拉式清單中，選取 **[ListDataset]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-168">In the **Dataset name** drop-down list, select **ListDataset**.</span></span>

4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

5.  <span data-ttu-id="c6d0e-169">在清單內部按一下滑鼠右鍵，然後按一下 [矩形屬性] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-169">Right-click inside the list, and then click **Rectangle Properties**.</span></span>

     <span data-ttu-id="c6d0e-170">![矩形屬性命令](../../2014/tutorials/media/tutorial-rectanglepropertiescommand.png "矩形屬性命令")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-170">![Rectangle Properties command](../../2014/tutorials/media/tutorial-rectanglepropertiescommand.png "Rectangle Properties command")</span></span>

6.  <span data-ttu-id="c6d0e-171">在 **[一般]** 索引標籤上，選取 **[在後方加入分頁符號]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-171">On the **General** tab, select the **Add a page break after** checkbox.</span></span>

7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

#### <a name="to-add-a-new-row-group-and-to-delete-the-details-group"></a><span data-ttu-id="c6d0e-172">加入新的資料列群組並刪除 [詳細資料] 群組</span><span class="sxs-lookup"><span data-stu-id="c6d0e-172">To add a new row group and to delete the Details group</span></span>

1.  <span data-ttu-id="c6d0e-173">在 [資料列群組] 窗格中，以滑鼠右鍵按一下 [詳細資料] 群組，然後指向 **[加入群組]**，再按一下 **[父群組]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-173">In the Row Groups pane, right-click the Details group, point to **Add Group**, and then click **Parent Group**.</span></span>

     <span data-ttu-id="c6d0e-174">![父群組命令](../../2014/tutorials/media/tutorial-parentgroupcommand.png "父群組命令")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-174">![Parent Group command](../../2014/tutorials/media/tutorial-parentgroupcommand.png "Parent Group command")</span></span>

2.  <span data-ttu-id="c6d0e-175">從下拉式清單中選取 `[Territory].`。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-175">In the drop-down list, select `[Territory].`</span></span>

3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

     <span data-ttu-id="c6d0e-176">清單中會加入一個資料行。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-176">A column is added to the list.</span></span> <span data-ttu-id="c6d0e-177">此資料行包含 `[Territory].` 資料格。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-177">The column contains the cell `[Territory].`</span></span>

4.  <span data-ttu-id="c6d0e-178">以滑鼠右鍵按一下清單中的 [Territory] 資料行，再按一下 **[刪除資料行]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-178">Right-click the Territory column in the list, and then click **Delete Columns**.</span></span>

     <span data-ttu-id="c6d0e-179">![刪除資料行](../../2014/tutorials/media/tutorial-deletecolumnscommand.png "[刪除資料行]")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-179">![Delete columns](../../2014/tutorials/media/tutorial-deletecolumnscommand.png "Delete columns")</span></span>

5.  <span data-ttu-id="c6d0e-180">按一下 [只刪除資料行] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-180">Click **Delete Columns only**.</span></span>

     <span data-ttu-id="c6d0e-181">![刪除資料行對話方塊](../../2014/tutorials/media/tutorial-deletecolumnsdialog.png "刪除資料行對話方塊")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-181">![Delete Columns dialog box](../../2014/tutorials/media/tutorial-deletecolumnsdialog.png "Delete Columns dialog box")</span></span>

6.  <span data-ttu-id="c6d0e-182">在 [資料列群組] 窗格中，在 [詳細資料] \*\*\*\* 群組上按一下滑鼠右鍵，然後按一下 [刪除群組] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-182">In the Row Groups pane, right-click the **Details** group, and then click **Delete Group**.</span></span>

     <span data-ttu-id="c6d0e-183">![刪除詳細資料群組](../../2014/tutorials/media/tutorial-deletedetailsgroup.png "刪除詳細資料群組")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-183">![Delete Details Group](../../2014/tutorials/media/tutorial-deletedetailsgroup.png "Delete Details Group")</span></span>

7.  <span data-ttu-id="c6d0e-184">按一下 **[僅刪除群組]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-184">Click **Delete Group only**.</span></span>

8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

##  <a name="3-add-graphics"></a><a name="Graphics"></a><span data-ttu-id="c6d0e-185">3. 新增圖形</span><span class="sxs-lookup"><span data-stu-id="c6d0e-185">3. Add Graphics</span></span>
 <span data-ttu-id="c6d0e-186">使用清單資料區的好處是，您可以在任何位置加入矩形和文字方塊等報表項目，而不必侷限於表格式配置。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-186">One of the advantages of using a list data region is that you can add report items such as rectangles and text boxes anywhere, instead of being limited to a tabular layout.</span></span> <span data-ttu-id="c6d0e-187">您將要透過加入圖形 (有填色的矩形) 加強報表的外觀。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-187">You will enhance the appearance of the report by adding a graphic (a rectangle filled with a color).</span></span>

#### <a name="to-add-graphic-elements-to-the-report"></a><span data-ttu-id="c6d0e-188">加入圖形元素至報表中</span><span class="sxs-lookup"><span data-stu-id="c6d0e-188">To add graphic elements to the report</span></span>

1.  <span data-ttu-id="c6d0e-189">在功能區的 [**插入**] 索引標籤上，按一下 [**矩形**]，然後將矩形拖曳到清單的左上角。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-189">On the **Insert** tab of the ribbon, click **Rectangle**,and then drag a rectangle to the upper left corner of the list.</span></span> <span data-ttu-id="c6d0e-190">將矩形調整成高 7 英吋且寬為 1 英吋。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-190">Make the rectangle 7 inches tall and 1 inch wide.</span></span>

2.  <span data-ttu-id="c6d0e-191">以滑鼠右鍵按一下矩形，然後按一下 **[矩形屬性]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-191">Right-click the rectangle, and then click **Rectangle Properties**.</span></span>

3.  <span data-ttu-id="c6d0e-192">按一下 **[填滿]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-192">Click the **Fill** tab.</span></span>

4.  <span data-ttu-id="c6d0e-193">在 [填滿色彩] \*\*\*\* 下拉式清單中，按一下 [更多色彩] \*\*\*\*，然後選取 [暗灰色] \*\*\*\* 。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-193">In the **Fill color** drop-down list, click **More Colors**, and then select the **DarkGray** color.</span></span>

     <span data-ttu-id="c6d0e-194">![選取填滿色彩](../../2014/tutorials/media/tutorial-selectfillcolorwithnumbers.png "選取填滿色彩")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-194">![Select fill color](../../2014/tutorials/media/tutorial-selectfillcolorwithnumbers.png "Select fill color")</span></span>

5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

6.  <span data-ttu-id="c6d0e-195">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-195">Click **Run** to preview the report.</span></span>

 <span data-ttu-id="c6d0e-196">報表左側現在會有深灰色矩形組成的垂直圖形。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-196">The left side of the report now has vertical graphic that consists of a dark gray rectangle.</span></span>

##  <a name="4-add-free-form-text"></a><a name="Text"></a><span data-ttu-id="c6d0e-197">4. 加入自由格式文字</span><span class="sxs-lookup"><span data-stu-id="c6d0e-197">4. Add Free Form Text</span></span>
 <span data-ttu-id="c6d0e-198">文字方塊會包含將在每個報表頁面上重複的靜態文字，還有資料欄位。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-198">A text box contains static text that is repeated on each report page as well as data fields.</span></span>

#### <a name="to-add-text-to-the-report"></a><span data-ttu-id="c6d0e-199">在報表中加入文字</span><span class="sxs-lookup"><span data-stu-id="c6d0e-199">To add text to the report</span></span>

1.  <span data-ttu-id="c6d0e-200">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-200">Click **Design** to return to design view.</span></span>

2.  <span data-ttu-id="c6d0e-201">在在功能區的 [插入] \*\*\*\* 索引標籤上，按一下 [文字方塊] \*\*\*\*，然後拖曳一個文字方塊到清單的左上角，放在您剛加入的矩形內。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-201">On the **Insert** tab of the ribbon, click **Text Box**, and then drag a text box to the upper left corner of the list, but inside of the rectangle you added previously.</span></span> <span data-ttu-id="c6d0e-202">將文字方塊調整成高約 3 英吋且寬約 5 英吋。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-202">Make the text box about 3 inches tall and 5 inches wide.</span></span>

3.  <span data-ttu-id="c6d0e-203">將滑鼠游標置於文字方塊的上半部，然後輸入 **Newsletter for** 。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-203">Place the cursor in the upper part of the text box, and then type: **Newsletter for** .</span></span>

     <span data-ttu-id="c6d0e-204">![新增電子報標題文字](../../2014/tutorials/media/tutorial-newsletterfor.png "新增電子報標題文字")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-204">![Add newsletter heading text](../../2014/tutorials/media/tutorial-newsletterfor.png "Add newsletter heading text")</span></span>

    > [!NOTE]
    >  <span data-ttu-id="c6d0e-205">記得在單字 "for" 後面多加一個空格。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-205">Be sure to include the extra space after the word "for".</span></span> <span data-ttu-id="c6d0e-206">此空格會將本段文字和下一個步驟要加入的欄位區隔開來。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-206">The space separates the text and the field that you will add in the next step.</span></span>

4.  <span data-ttu-id="c6d0e-207">將 [Territory] 欄位拖曳到文字方塊中，置於您在步驟 3 輸入的文字後面。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-207">Drag the Territory field to the text box and place it after the text you typed in step 3.</span></span>

     <span data-ttu-id="c6d0e-208">![新增領土欄位](../../2014/tutorials/media/tutorial-addterritorialfield.png "新增領土欄位")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-208">![Add Territorial field](../../2014/tutorials/media/tutorial-addterritorialfield.png "Add Territorial field")</span></span>

5.  <span data-ttu-id="c6d0e-209">全選所有文字，再按一下滑鼠右鍵，然後按一下 **[文字屬性]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-209">Select all text, right-click, and then click **Text Properties**.</span></span>

6.  <span data-ttu-id="c6d0e-210">按一下 **[字型]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-210">Click the **Font** tab.</span></span>

7.  <span data-ttu-id="c6d0e-211">在 [字型] \*\*\*\* 清單中選取 [Times New Roman] \*\*\*\*、[大小] \*\*\*\* 選取 [20 pt] \*\*\*\*、[色彩] \*\*\*\* 選取 [紅色] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-211">In the **Font** list, select **Times New Roman**; in **Size** select **20 pt**, in **Color** select **Red**.</span></span>

     <span data-ttu-id="c6d0e-212">![文字屬性](../../2014/tutorials/media/tutorial-textpropertieswithnumbers.png "[文字屬性]")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-212">![Text Properties](../../2014/tutorials/media/tutorial-textpropertieswithnumbers.png "Text Properties")</span></span>

8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

9. <span data-ttu-id="c6d0e-213">將滑鼠游標置於您在步驟 3 輸入的文字下方，然後輸入 **Hello** 。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-213">Place the cursor below the text you typed in step 3 and type: **Hello** .</span></span>

    > [!NOTE]
    >  <span data-ttu-id="c6d0e-214">記得在單字 "Hello" 後面多加一個空格。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-214">Be sure to include the extra space after the word "Hello".</span></span> <span data-ttu-id="c6d0e-215">此空格會將本段文字和下一個步驟要加入的欄位區隔開來。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-215">The space separates the text and the field that you will add in the next step.</span></span>

10. <span data-ttu-id="c6d0e-216">將 [FullName] 欄位拖曳到文字方塊中，置於您在步驟 9 輸入的文字後面，接著再輸入一個逗號 (,)。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-216">Drag the FullName field to the text box and place it after the text you typed in step 9, and then type a comma (,).</span></span>

     <span data-ttu-id="c6d0e-217">![新增全名欄位](../../2014/tutorials/media/tutorial-addfullnamefield.png "新增全名欄位")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-217">![Add Full Name field](../../2014/tutorials/media/tutorial-addfullnamefield.png "Add Full Name field")</span></span>

11. <span data-ttu-id="c6d0e-218">選取您在步驟 9 和步驟 10 加入的文字，再按一下滑鼠右鍵，然後按一下 **[文字屬性]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-218">Select the text you added in steps 9 and 10, right-click, and then click **Text Properties**.</span></span>

12. <span data-ttu-id="c6d0e-219">按一下 **[字型]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-219">Click the **Font** tab.</span></span>

13. <span data-ttu-id="c6d0e-220">在 [字型] \*\*\*\* 清單中選取 [Times New Roman] \*\*\*\*、[大小] \*\*\*\* 選取 [16 pt] \*\*\*\*、[色彩] \*\*\*\* 選取 [黑色] \*\*\*\* 。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-220">In the **Font** list, select **Times New Roman**; in **Size** select **16 pt**, in **Color** select **Black** color.</span></span>

14. [!INCLUDE[clickOK](../includes/clickok-md.md)]

15. <span data-ttu-id="c6d0e-221">將滑鼠游標置於您在步驟 9 至步驟 13 加入的文字下方，然後複製並貼入下列「馬賽克」文字：</span><span class="sxs-lookup"><span data-stu-id="c6d0e-221">Place the cursor below the text you added in steps 9 through 13, and then copy and paste the following "greeked" text:</span></span>

    ```
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin sed dolor in ipsum pulvinar egestas. Sed sed lacus at leo ornare ultricies. Vivamus velit risus, euismod nec sodales gravida, gravida in dui. Etiam ullamcorper elit vitae justo fermentum ut ullamcorper augue sodales. Ut placerat, nisl quis feugiat adipiscing, nibh est aliquet est, mollis faucibus mauris lectus quis arcu. In mollis tincidunt lacinia. In vitae erat ut lorem tincidunt luctus. Curabitur et magna nunc, sit amet adipiscing nisi. Nulla rhoncus elementum orci nec tincidunt. Aliquam imperdiet cursus erat vel tincidunt. Donec et neque ac urna rutrum sodales. In id purus et nisl dignissim dapibus. Sed rhoncus metus at felis feugiat eu tempor dolor vehicula. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam faucibus consectetur diam eu pellentesque. 
    Nulla facilisi. Proin ligula enim, porta ut tincidunt id, adipiscing sit amet eros. Ut purus sem, bibendum et vulputate sit amet, facilisis eget magna. Sed aliquam erat non erat eleifend hendrerit. Ut a ligula est, sit amet eleifend enim. Ut et nisl enim, sit amet adipiscing augue. Vivamus eu arcu ac libero posuere elementum. Integer condimentum bibendum venenatis. Integer odio tellus, feugiat in pellentesque semper, interdum nec sem. Sed cursus euismod sem, ut elementum sapien placerat vel. 
    ```

16. <span data-ttu-id="c6d0e-222">選取您在步驟 15 加入的文字，再按一下滑鼠右鍵，然後按一下 **[文字屬性]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-222">Select the text you added in steps 15, right-click, and then click **Text Properties**.</span></span>

17. <span data-ttu-id="c6d0e-223">按一下 **[字型]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-223">Click the **Font** tab.</span></span>

18. <span data-ttu-id="c6d0e-224">從 **[字型]** 清單中選取 **[Arial]**、 **[大小]** 選取 **[10 pt]**、 **[色彩]** 選取 **[黑色]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-224">In the **Font** list, select **Arial**; in **Size** select **10 pt**, in **Color** select **Black**.</span></span>

19. [!INCLUDE[clickOK](../includes/clickok-md.md)]

     <span data-ttu-id="c6d0e-225">![新增新聞稿文字](../../2014/tutorials/media/tutorial-newslettertext.png "新增新聞稿文字")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-225">![Add newsletter text](../../2014/tutorials/media/tutorial-newslettertext.png "Add newsletter text")</span></span>

20. <span data-ttu-id="c6d0e-226">將滑鼠游標置於您在步驟 15 貼入的文字下方，然後輸入 **Congratulations on your total sales of** 。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-226">Place the cursor below the text you pasted in step 15, and then type: **Congratulations on your total sales of** .</span></span>

    > [!NOTE]
    >  <span data-ttu-id="c6d0e-227">記得在單字 "of" 後面多加一個空格。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-227">Be sure to include the extra space after the word "of".</span></span> <span data-ttu-id="c6d0e-228">此空格會將本段文字和下一個步驟要加入的欄位區隔開來。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-228">The space separates the text and the field that you will add in the next step.</span></span>

21. <span data-ttu-id="c6d0e-229">將 [Sales] 欄位拖曳到文字方塊中，置於您在步驟 20 輸入的文字後面，接著再輸入一個驚嘆號 (!)。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-229">Drag the Sales field to the text box, place it after the text you typed in step 20, and then type an exclamation mark (!).</span></span>

22. <span data-ttu-id="c6d0e-230">反白顯示 [Sales] 欄位，以滑鼠右鍵按一下欄位，然後按一下 [**運算式**]。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-230">Highlight the Sales field, right-click the field, and then click **Expression**.</span></span>

23. <span data-ttu-id="c6d0e-231">在運算式方塊中，將運算式改為包含 Sum 函數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c6d0e-231">In the expression box, change the expression to include the Sum function as follows:</span></span>

    ```
    =Sum(Fields!Sales.value)
    ```

24. [!INCLUDE[clickOK](../includes/clickok-md.md)]

     <span data-ttu-id="c6d0e-232">![新增運算式到銷售欄位](../../2014/tutorials/media/tutorial-addexpressiontosalesfield.png "新增運算式到銷售欄位")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-232">![Add an expression to sales field](../../2014/tutorials/media/tutorial-addexpressiontosalesfield.png "Add an expression to sales field")</span></span>

25. <span data-ttu-id="c6d0e-233">選取您在步驟 20 至步驟 23 加入的文字，再按一下滑鼠右鍵，然後按一下 **[文字屬性]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-233">Select the text you added in steps 20 through 23, right-click, and then click **Text Properties**.</span></span>

26. <span data-ttu-id="c6d0e-234">按一下 **[字型]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-234">Click the **Font** tab.</span></span>

27. <span data-ttu-id="c6d0e-235">在 [字型] \*\*\*\* 清單中選取 [Times New Roman] \*\*\*\*、[大小] \*\*\*\* 選取 [16 pt] \*\*\*\*、[色彩] \*\*\*\* 選取 [紅色] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-235">In the **Font** list, select **Times New Roman**; in **Size** select **16 pt**, in **Color** select **Red**.</span></span>

28. [!INCLUDE[clickOK](../includes/clickok-md.md)]

29. <span data-ttu-id="c6d0e-236">選取 `[Sum(Sales)]` 並於 **[主資料夾]** 索引標籤上，按一下 **[數值]** 群組中的 **[貨幣]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-236">Select `[Sum(Sales)]` and on the **Home** tab, in the **Number** group, click the **Currency** button.</span></span>

     <span data-ttu-id="c6d0e-237">![新增貨幣符號](../../2014/tutorials/media/tutorial-addcurrencysymbol.png "新增貨幣符號")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-237">![Add currency symbol](../../2014/tutorials/media/tutorial-addcurrencysymbol.png "Add currency symbol")</span></span>

30. <span data-ttu-id="c6d0e-238">以滑鼠右鍵按一下包含「按一下以加入標題」字樣的文字方塊，然後按一下 **[刪除]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-238">Right-click the text box with the "Click to add title" text, and then click **Delete**.</span></span>

31. <span data-ttu-id="c6d0e-239">選取清單方塊，然後利用方向鍵將其移到頁面頂端。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-239">Select the list box and using the arrow keys, move it to the top of the page.</span></span>

32. <span data-ttu-id="c6d0e-240">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-240">Click **Run** to preview the report.</span></span>

 <span data-ttu-id="c6d0e-241">報表會顯示靜態文字，而且每個報表頁面含有與特定領域相關的資料。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-241">The report displays static text and each report page includes data that pertains to a territory.</span></span> <span data-ttu-id="c6d0e-242">銷售額則格式化為貨幣。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-242">Sales are formatted as currency.</span></span>

 <span data-ttu-id="c6d0e-243">![新聞稿預覽](../../2014/tutorials/media/tutorial-newsletters.png "新聞稿預覽")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-243">![Preview of Newsletter](../../2014/tutorials/media/tutorial-newsletters.png "Preview of Newsletter")</span></span>

##  <a name="5-add-a-table-to-show-sales-details"></a><a name="Table"></a><span data-ttu-id="c6d0e-244">5. 加入資料表以顯示銷售詳細資料</span><span class="sxs-lookup"><span data-stu-id="c6d0e-244">5. Add a Table to Show Sales Details</span></span>
 <span data-ttu-id="c6d0e-245">使用新增資料表和矩陣精靈，將資料表加入至自由格式報表。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-245">Use the New Table and Matrix Wizard to add a table to the free form report.</span></span> <span data-ttu-id="c6d0e-246">在完成精靈之後，您將要手動加入一個總計資料列。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-246">After you complete the wizard, you will manually add a row for totals.</span></span>

#### <a name="to-add-a-table"></a><span data-ttu-id="c6d0e-247">加入資料表</span><span class="sxs-lookup"><span data-stu-id="c6d0e-247">To add a table</span></span>

1.  <span data-ttu-id="c6d0e-248">在功能區的 **[插入]** 索引標籤上，按一下 **[資料區域]** 區域內的 **[資料表]**，然後按一下 **[資料表精靈]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-248">On the **Insert** tab of the ribbon, in the **Data Regions** area, click **Table**, and then click **Table Wizard**.</span></span>

2.  <span data-ttu-id="c6d0e-249">在 [選擇資料集] 頁面上，按一下 **[ListDataset]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-249">On the Choose a dataset page, click **ListDataset**.</span></span>

3.  <span data-ttu-id="c6d0e-250">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-250">Click **Next**.</span></span>

4.  <span data-ttu-id="c6d0e-251">在 [排列欄位]\*\*\*\* 頁面上，將 [Product] 欄位從 [可用的欄位]\*\*\*\* 拖曳至 [值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-251">On the **Arrange fields** page, drag the Product field from **Available fields** to **Values.**</span></span>

5.  <span data-ttu-id="c6d0e-252">針對 SalesDate、Quantity 和 Sales 重複步驟 4。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-252">Repeat step 4, for SalesDate, Quantity, and Sales.</span></span> <span data-ttu-id="c6d0e-253">將 SalesDate 放到 Product 底下、Quantity 放到 SalesDate 底下、Sales 放到 Quantity 底下。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-253">Place SalesDate below Product, Quantity below SalesDate, and Sales below SalesDate.</span></span>

6.  <span data-ttu-id="c6d0e-254">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-254">Click **Next**.</span></span>

7.  <span data-ttu-id="c6d0e-255">在 [選擇配置] \*\*\*\* 頁面上，檢視資料表的配置。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-255">On the **Choose the layout** page, view the layout of the table.</span></span>

     <span data-ttu-id="c6d0e-256">這個資料表非常單純，</span><span class="sxs-lookup"><span data-stu-id="c6d0e-256">The table is very simple.</span></span> <span data-ttu-id="c6d0e-257">其中包含五個資料行，而沒有任何資料列或資料行群組。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-257">It consists of five columns and has no row or column groups.</span></span> <span data-ttu-id="c6d0e-258">由於沒有群組，與群組相關的配置選項無法使用。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-258">Because it has no groups, the layout options related to groups, are not available.</span></span> <span data-ttu-id="c6d0e-259">稍後在本教學課程中，您將要手動更新資料表使其包括總計。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-259">You will manually update the table to include a total later in the tutorial.</span></span>

8.  <span data-ttu-id="c6d0e-260">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-260">Click **Next**.</span></span>

9. <span data-ttu-id="c6d0e-261">在 **[選擇樣式]** 頁面的 **[樣式]** 窗格中，選取 **[石板]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-261">On the **Choose a Style** page, in the **Styles** pane, select **Slate**.</span></span>

10. <span data-ttu-id="c6d0e-262">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-262">Click **Finish**.</span></span>

11. <span data-ttu-id="c6d0e-263">將資料表拖曳到您在第 4 課加入的文字方塊下方。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-263">Drag the table to below the text box that you added in lesson 4.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="c6d0e-264">務必將資料表置於清單內。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-264">Make sure the table is inside the list.</span></span>

12. <span data-ttu-id="c6d0e-265">確認已選取該資料表，然後在 [資料列群組] 窗格的 [詳細資料] 上按一下滑鼠右鍵，指向 [加入總計] \*\*\*\*，再按一下 [之後] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-265">Confirmed that the table is selected, then in the Row Group pane right-click Details, point to **Add Total**, and then click **After**.</span></span>

     <span data-ttu-id="c6d0e-266">![新增報表總計](../../2014/tutorials/media/tutorial-addtotal.png "新增報表總計")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-266">![Add report total](../../2014/tutorials/media/tutorial-addtotal.png "Add report total")</span></span>

13. <span data-ttu-id="c6d0e-267">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-267">Click **Run** to preview the report.</span></span>

 <span data-ttu-id="c6d0e-268">報表會顯示含有銷售額詳細資料及總計的資料表。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-268">The report displays a table with sales details and totals.</span></span>

 <span data-ttu-id="c6d0e-269">![報表中的總銷售額](../../2014/tutorials/media/tutorial-reportsalestotals.png "報表中的總銷售額")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-269">![Sales totals in report](../../2014/tutorials/media/tutorial-reportsalestotals.png "Sales totals in report")</span></span>

##  <a name="6-format-data"></a><a name="Format"></a><span data-ttu-id="c6d0e-270">6. 將資料格式化</span><span class="sxs-lookup"><span data-stu-id="c6d0e-270">6. Format Data</span></span>
 <span data-ttu-id="c6d0e-271">將數值資料格式化為貨幣，並將日期格式化為只有日和時間。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-271">Format numeric data as currency and dates as day and time only.</span></span>

#### <a name="to-format-fields-table"></a><span data-ttu-id="c6d0e-272">格式化欄位資料表</span><span class="sxs-lookup"><span data-stu-id="c6d0e-272">To format fields table</span></span>

1.  <span data-ttu-id="c6d0e-273">按一下 [**設計**]，切換至設計檢視。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-273">Click **Design** to switch to design view.</span></span>

2.  <span data-ttu-id="c6d0e-274">按一下資料表中包含 `[Sum(SalesSales)]` 的資料格，接著在 **[主資料夾]** 索引標籤的 **[數值]** 群組中，按一下 **[貨幣]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-274">Click the table cells that contain `[Sum(SalesSales)]` and on the **Home** tab, in the **Number** group, click the **Currency** button.</span></span>

     <span data-ttu-id="c6d0e-275">![新增貨幣符號至銷售總和](../../2014/tutorials/media/tutorial-sumsales-currencysymbol.png "新增貨幣符號至銷售總和")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-275">![Add currency symbol to sum sales](../../2014/tutorials/media/tutorial-sumsales-currencysymbol.png "Add currency symbol to sum sales")</span></span>

3.  <span data-ttu-id="c6d0e-276">按一下包含 `[SalesDate]` 的資料格，然後從 **[數值]** 群組的下拉式清單中，選取 **[日期]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-276">Click the cell that contains `[SalesDate]` and in the **Number** group, from the drop-down list, select **Date**.</span></span>

4.  <span data-ttu-id="c6d0e-277">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-277">Click **Run** to preview the report.</span></span>

 <span data-ttu-id="c6d0e-278">報表如今已顯示格式化的資料，更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-278">The report now displays formatted data and is easier to read.</span></span>

 <span data-ttu-id="c6d0e-279">![格式化報表中的總銷售額](../../2014/tutorials/media/tutorial-reportsalestotals-formatted.png "格式化報表中的總銷售額")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-279">![Format sales totals in report](../../2014/tutorials/media/tutorial-reportsalestotals-formatted.png "Format sales totals in report")</span></span>

##  <a name="7-save-the-report"></a><a name="Save"></a><span data-ttu-id="c6d0e-280">7. 儲存報表</span><span class="sxs-lookup"><span data-stu-id="c6d0e-280">7. Save the Report</span></span>
 <span data-ttu-id="c6d0e-281">您可以將報表儲存至報表伺服器、SharePoint 文件庫或您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-281">You can save reports to a report server, SharePoint library, or your computer.</span></span> <span data-ttu-id="c6d0e-282">您也可以將報表匯出成各種格式 (例如 Word 和 PDF)，方法是執行報表，然後從 [匯出] \*\*\*\* 功能表選取格式。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-282">You can also export the report to a variety of formats such as Word and PDF, by running the report and selecting the format from the **Export** menu.</span></span>

 <span data-ttu-id="c6d0e-283">本教學課程會將報表儲存至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-283">In this tutorial, save the report to a report server.</span></span> <span data-ttu-id="c6d0e-284">如果您沒有報表伺服器的存取權，請將報表儲存在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-284">If you do not have access to a report server, save the report to your computer.</span></span>

#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="c6d0e-285">若要將報表儲存在報表伺服器上</span><span class="sxs-lookup"><span data-stu-id="c6d0e-285">To save the report on a report server</span></span>

1.  <span data-ttu-id="c6d0e-286">在 **[報表產生器]** 按鈕中，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-286">From the **Report Builder** button, click **Save As**.</span></span>

2.  <span data-ttu-id="c6d0e-287">按一下 **[最近使用的網站和伺服器]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-287">Click **Recent Sites and Servers**.</span></span>

3.  <span data-ttu-id="c6d0e-288">選取或輸入您有權儲存報表之報表伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-288">Select or type the name of the report server where you have permission to save reports.</span></span>

     <span data-ttu-id="c6d0e-289">「正在連接到報表伺服器」訊息隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-289">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="c6d0e-290">連接完成時，您就會看見報表伺服器管理員指定為預設報表位置之報表資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-290">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>

4.  <span data-ttu-id="c6d0e-291">在中 `Name` ，將預設名稱取代為**為 salesinformationbyterritory**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-291">In `Name`, replace the default name with **SalesInformationByTerritory**.</span></span>

5.  <span data-ttu-id="c6d0e-292">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-292">Click **Save**.</span></span>

 <span data-ttu-id="c6d0e-293">報表就會儲存至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-293">The report is saved to the report server.</span></span> <span data-ttu-id="c6d0e-294">您連接之報表伺服器的名稱會顯示在視窗底部的狀態列中。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-294">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>

#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="c6d0e-295">將報表儲存到您的電腦上</span><span class="sxs-lookup"><span data-stu-id="c6d0e-295">To save the report on your computer</span></span>

1.  <span data-ttu-id="c6d0e-296">在 **[報表產生器]** 按鈕中，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-296">From the **Report Builder** button, click **Save As**.</span></span>

2.  <span data-ttu-id="c6d0e-297">按一下 **[桌面]**、 **[我的文件]** 或 **[我的電腦]**，然後瀏覽到您要儲存報表的資料夾。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-297">Click **Desktop**, **My Documents**, or **My computer**, and then browse to the folder where you want to save the report.</span></span>

3.  <span data-ttu-id="c6d0e-298">在中 `Name` ，將預設名稱取代為**為 salesinformationbyterritory**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-298">In `Name`, replace the default name with **SalesInformationByTerritory**.</span></span>

4.  <span data-ttu-id="c6d0e-299">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-299">Click **Save**.</span></span>

##  <a name="8-optional-add-a-line-to-separate-areas-of-the-report"></a><a name="Line"></a><span data-ttu-id="c6d0e-300">8. (選擇性) 加入線條以區隔報表的各區域</span><span class="sxs-lookup"><span data-stu-id="c6d0e-300">8. (Optional) Add a Line to Separate Areas of the Report</span></span>
 <span data-ttu-id="c6d0e-301">加入線條以區隔報表的編輯區和詳細資料區。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-301">Add a line to separate the editorial and details areas of the report.</span></span>

#### <a name="to-add-a-line"></a><span data-ttu-id="c6d0e-302">加入線條</span><span class="sxs-lookup"><span data-stu-id="c6d0e-302">To add a line</span></span>

1.  <span data-ttu-id="c6d0e-303">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-303">Click **Design** to return to design view.</span></span>

2.  <span data-ttu-id="c6d0e-304">在功能區的 **[插入]** 索引標籤上，按一下 **[報表項目]** 區域內的 **[線條]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-304">On the **Insert** tab of the ribbon, in the **Report Items** area, click **Line.**</span></span>

3.  <span data-ttu-id="c6d0e-305">將線條拖曳到您在第 4 課加入的自由格式文字方塊下方。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-305">Draw a line below the free form text box you added in lesson 4.</span></span>

4.  <span data-ttu-id="c6d0e-306">按一下該線條。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-306">Click the line.</span></span>

5.  <span data-ttu-id="c6d0e-307">按一下 **[主資料夾]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-307">Click the **Home** tab.</span></span>

6.  <span data-ttu-id="c6d0e-308">在 [框線] \*\*\*\* 區域內，寬度選取 [4 1/2] \*\*\*\* 點，色彩則選取 [紅色] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-308">In the **Border** area, for width select **4 1/2** pt and for color, for color select **Red**.</span></span>

     <span data-ttu-id="c6d0e-309">![新增報表行](../../2014/tutorials/media/tutorial-reportwithline.png "新增報表行")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-309">![Add line to report](../../2014/tutorials/media/tutorial-reportwithline.png "Add line to report")</span></span>

##  <a name="9-optional-add-summary-data-visualization"></a><a name="Visualization"></a><span data-ttu-id="c6d0e-310">9. (選擇性) 新增摘要資料視覺效果</span><span class="sxs-lookup"><span data-stu-id="c6d0e-310">9. (Optional) Add Summary Data Visualization</span></span>
 <span data-ttu-id="c6d0e-311">矩形可以協助您控制報表的轉譯方式。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-311">Rectangles help you control how the report renders.</span></span> <span data-ttu-id="c6d0e-312">將圓形圖和直條圖放到矩形內，以確保報表轉譯為您希望的外觀。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-312">Place a pie and column chart inside a rectangle to ensure that the report renders the way you want.</span></span>

#### <a name="to-add-a-rectangle"></a><span data-ttu-id="c6d0e-313">若要加入矩形</span><span class="sxs-lookup"><span data-stu-id="c6d0e-313">To add a rectangle</span></span>

1.  <span data-ttu-id="c6d0e-314">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-314">Click **Design** to return to design view.</span></span>

2.  <span data-ttu-id="c6d0e-315">在功能區的 **[插入]** 索引標籤上，按一下 **[報表項目]** 區域內的 **[矩形]**，然後將矩形拖曳到清單中的資料表右側。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-315">On the **Insert** tab of the ribbon, in the **Report Items** area click **Rectangle**, and then drag the rectangle inside the list, to the right of the table.</span></span> <span data-ttu-id="c6d0e-316">將矩形調整成寬為 2 英吋且高 4 英吋。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-316">Make the rectangle 2 inches wide and 4 inches tall.</span></span>

3.  <span data-ttu-id="c6d0e-317">對齊矩形和資料表的上緣。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-317">Align the tops of the rectangle and the table.</span></span>

#### <a name="to-add-a-pie-chart"></a><span data-ttu-id="c6d0e-318">加入圓形圖</span><span class="sxs-lookup"><span data-stu-id="c6d0e-318">To add a pie chart</span></span>

1.  <span data-ttu-id="c6d0e-319">在功能區的 [插入] \*\*\*\* 索引標籤上，按一下 [資料視覺效果] \*\*\*\* 區域中的 [圖表] \*\*\*\* ，然後按一下 [圖表精靈] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-319">On the **Insert** tab of the ribbon, in the **Data Visualizations** area, click **Chart,** and then click **Chart Wizard**.</span></span>

2.  <span data-ttu-id="c6d0e-320">在 [選擇資料集]  頁面上，按一下 [ListDataset] \*\*\*\*，然後按 [下一步] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-320">On the Choose a dataset page, click **ListDataset**, and then click **Next**.</span></span>

3.  <span data-ttu-id="c6d0e-321">按一下 **[圓形圖]**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-321">Click **Pie**, and then click **Next**.</span></span>

4.  <span data-ttu-id="c6d0e-322">在 [排列圖表欄位] 頁面上，將 [Product] 拖曳至 [類別目錄]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-322">On the arrange chart fields page, drag Product to **Categories**.</span></span>

5.  <span data-ttu-id="c6d0e-323">將 [數量] 拖曳至 [**值**]，然後按 **[下一步]**</span><span class="sxs-lookup"><span data-stu-id="c6d0e-323">Drag Quantity to **Values**, and then click **Next**.</span></span>

6.  <span data-ttu-id="c6d0e-324">在 **[選擇樣式]** 頁面的 **[樣式]** 窗格中，選取 **[石板]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-324">On the **Choose a Style** page, in the **Styles** pane, select **Slate**.</span></span>

7.  <span data-ttu-id="c6d0e-325">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-325">Click **Finish**.</span></span>

8.  <span data-ttu-id="c6d0e-326">調整報表左上角顯示的圖表大小，成為高 1 1/2 英吋且寬為 2 英吋。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-326">Resize the chart that appears in the upper left corner of the report, to be 1 1/2 inches tall and 2 inches wide.</span></span>

9. <span data-ttu-id="c6d0e-327">將圖表拖曳到矩形內。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-327">Drag the chart inside the rectangle.</span></span>

     <span data-ttu-id="c6d0e-328">![新增圓形圖](../../2014/tutorials/media/tutorial-addpiechart.png "新增圓形圖")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-328">![Add pie chart](../../2014/tutorials/media/tutorial-addpiechart.png "Add pie chart")</span></span>

10. <span data-ttu-id="c6d0e-329">在圖表標題上按一下滑鼠右鍵，然後按一下 [標題屬性] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-329">Right-click the chart title, and then click **Title Properties**.</span></span>

11. <span data-ttu-id="c6d0e-330">在 **[圖表標題屬性]** 對話方塊中，為 [標題文字] 輸入 **Product Quantities Sold**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-330">In the **Chart Title Properties** dialog box, in Title text, type: **Product Quantities Sold**.</span></span>

12. <span data-ttu-id="c6d0e-331">按一下 **[字型]** 索引標籤，然後從 **[大小]** 清單中按一下 **[10pt]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-331">Click the **Font** tab, and in the **Size** list, click **10pt**.</span></span>

13. [!INCLUDE[clickOK](../includes/clickok-md.md)]

#### <a name="to-add-a-column-chart"></a><span data-ttu-id="c6d0e-332">加入直條圖</span><span class="sxs-lookup"><span data-stu-id="c6d0e-332">To add a column chart</span></span>

1.  <span data-ttu-id="c6d0e-333">在功能區的 [插入] \*\*\*\* 索引標籤上，按一下 [資料視覺效果] \*\*\*\* 區域中的 [圖表] \*\*\*\* ，然後按一下 [圖表精靈] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-333">On the **Insert** tab of the ribbon, in the **Data Visualizations** area, click **Chart,** and then click **Chart Wizard**.</span></span>

2.  <span data-ttu-id="c6d0e-334">在 [選擇資料集] \*\*\*\* 頁面上，按一下 [ListDataset] \*\*\*\*，然後按 [下一步] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-334">On the **Choose a dataset** page, click **ListDataset**, and then click **Next**.</span></span>

3.  <span data-ttu-id="c6d0e-335">按一下 **[直條圖]**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-335">Click **Column**, and then click **Next**.</span></span>

4.  <span data-ttu-id="c6d0e-336">在 [排列圖表欄位] 頁面上，將 [產品] 欄位拖曳至 [**類別**]。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-336">On the arrange chart fields page, drag the Product field to **Categories**.</span></span>

5.  <span data-ttu-id="c6d0e-337">將 [Sales] 拖曳至 [值]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-337">Drag Sales to **Values,** and then click **Next**.</span></span>

     <span data-ttu-id="c6d0e-338">值會顯示在垂直軸上。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-338">Values display on the vertical axis.</span></span>

6.  <span data-ttu-id="c6d0e-339">在 **[選擇樣式]** 頁面的 **[樣式]** 窗格中，選取 **[石板]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-339">On the **Choose a Style** page, in the **Styles** pane, select **Slate**.</span></span>

7.  <span data-ttu-id="c6d0e-340">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-340">Click **Finish**.</span></span>

     <span data-ttu-id="c6d0e-341">直條圖隨即加入至報表的左上角。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-341">A column chart is added to the upper left corner of the report.</span></span>

8.  <span data-ttu-id="c6d0e-342">將圖表大小調整成寬為 2 英吋且高 2 英吋。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-342">Resize the chart to be 2 inches wide and 2 inches tall.</span></span>

9. <span data-ttu-id="c6d0e-343">將圖表拖曳到矩形內。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-343">Drag the chart inside the rectangle, below the pie chart.</span></span>

     <span data-ttu-id="c6d0e-344">![新增直條圖](../../2014/tutorials/media/tutorial-addcolumnchart.png "新增直條圖")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-344">![Add column chart](../../2014/tutorials/media/tutorial-addcolumnchart.png "Add column chart")</span></span>

10. <span data-ttu-id="c6d0e-345">以滑鼠右鍵按一下圖表標題，然後按一下 [**標題屬性**]。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-345">Right-click the chart title and then click **Title Properties**.</span></span>

11. <span data-ttu-id="c6d0e-346">在 **[圖表標題屬性]** 對話方塊中，為 [標題文字] 輸入 **Product Sales**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-346">In the **Chart Title Properties** dialog box, in Title text, type: **Product Sales**.</span></span>

12. <span data-ttu-id="c6d0e-347">按一下 [字型] \*\*\*\* 索引標籤，並在 [大小] \*\*\*\* 清單中按一下 [10pt] \*\*\*\*，然後按一下 [確定] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-347">Click the **Font** tab, and in the **Size** list click **10pt**, and then click **OK**.</span></span>

13. <span data-ttu-id="c6d0e-348">在直條圖中，以滑鼠右鍵按一下垂直軸，然後將 **[顯示軸標題]** 取消選取。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-348">In the column chart, right click the vertical axis, and then deselect **Show Axis Title**.</span></span>

14. <span data-ttu-id="c6d0e-349">針對水平軸重複步驟 13。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-349">Repeat step 13 for the horizontal axis.</span></span>

15. <span data-ttu-id="c6d0e-350">以滑鼠右鍵按一下圖例，然後按一下 **[刪除圖例]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-350">Right click the legend, and then click **Delete Legend**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="c6d0e-351">移除軸標題和圖例可以讓較小的圖表更具可讀性。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-351">Removing axis titles and the legend makes the chart more readable when it is a small size.</span></span>

 <span data-ttu-id="c6d0e-352">![變更圖表標題和移除軸標題](../../2014/tutorials/media/tutorial-columnchart-newtitle-noaxistitle.png "變更圖表標題和移除軸標題")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-352">![Change chart titles and remove axis title](../../2014/tutorials/media/tutorial-columnchart-newtitle-noaxistitle.png "Change chart titles and remove axis title")</span></span>

#### <a name="to-verify-the-charts-are-inside-the-rectangle"></a><span data-ttu-id="c6d0e-353">確認圖表位於矩形內部</span><span class="sxs-lookup"><span data-stu-id="c6d0e-353">To verify the charts are inside the rectangle</span></span>

1.  <span data-ttu-id="c6d0e-354">按一下您稍早在這一課中加入的矩形。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-354">Click the rectangle you added earlier in this lesson.</span></span>

     <span data-ttu-id="c6d0e-355">在 [屬性] 窗格中，`Name` 屬性會顯示該矩形的名稱。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-355">In the Properties pane, the `Name` property displays the name of the rectangle.</span></span>

     <span data-ttu-id="c6d0e-356">![矩形的名稱](../../2014/tutorials/media/tutorial-rectanglename.png "矩形的名稱")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-356">![Name of rectangle](../../2014/tutorials/media/tutorial-rectanglename.png "Name of rectangle")</span></span>

2.  <span data-ttu-id="c6d0e-357">按一下圓形圖。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-357">Click the pie chart.</span></span>

3.  <span data-ttu-id="c6d0e-358">在 [**屬性**] 窗格中，確認 `Parent` 屬性包含矩形的名稱。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-358">In the **Properties** pane, verify that the `Parent` property contains the name of the rectangle.</span></span>

     <span data-ttu-id="c6d0e-359">![圓形圖的父屬性](../../2014/tutorials/media/tutorial-piechart-parentproperty.png "圓形圖的父屬性")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-359">![Parent property for pie chart](../../2014/tutorials/media/tutorial-piechart-parentproperty.png "Parent property for pie chart")</span></span>

4.  <span data-ttu-id="c6d0e-360">按一下直條圖，然後重複步驟 2 和步驟 3。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-360">Click the column chart and repeat steps 2 and 3.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="c6d0e-361">如果圖表不是在矩形內部，轉譯後的報表將不會一併顯示圖表。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-361">If the charts are not inside the rectangle, the rendered report does not display the charts together.</span></span>

#### <a name="to-make-the-charts-the-same-size"></a><span data-ttu-id="c6d0e-362">將圖表調整成相同的大小</span><span class="sxs-lookup"><span data-stu-id="c6d0e-362">To make the charts the same size</span></span>

1.  <span data-ttu-id="c6d0e-363">按一下圓形圖，再按下 Ctrl 鍵，然後按一下直條圖。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-363">Click the pie chart, press the Ctrl key, and then click the column chart.</span></span>

2.  <span data-ttu-id="c6d0e-364">當兩個圖表都已選取後，按一下滑鼠右鍵，指向 **[配置]**，再按一下 **[設定成相同寬度]**。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-364">With both charts selected, right-click, point to **Layout**, and then click **Make Same Width**.</span></span>

     <span data-ttu-id="c6d0e-365">![將圖表寬度調整成相同的大小](../../2014/tutorials/media/tutorial-makechartssamewidth.png "將圖表寬度調整成相同的大小")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-365">![Make chart widths the same](../../2014/tutorials/media/tutorial-makechartssamewidth.png "Make chart widths the same")</span></span>

    > [!NOTE]
    >  <span data-ttu-id="c6d0e-366">先按的項目會決定所有已選取項目的寬度。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-366">The item you click first determines the width of all the selected items.</span></span>

3.  <span data-ttu-id="c6d0e-367">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-367">Click **Run** to preview the report.</span></span>

 <span data-ttu-id="c6d0e-368">報表如今會以圓形圖和直條圖顯示摘要銷售資料。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-368">The report now displays summary sales data in pie and column charts.</span></span>

 <span data-ttu-id="c6d0e-369">![SSRS 教學課程，任意格式的報表](../../2014/tutorials/media/tutorial-reportfinal.png "SSRS 教學課程，任意格式的報表")</span><span class="sxs-lookup"><span data-stu-id="c6d0e-369">![SSRS tutorial, free form report](../../2014/tutorials/media/tutorial-reportfinal.png "SSRS tutorial, free form report")</span></span>

## <a name="more-information"></a><span data-ttu-id="c6d0e-370">相關資訊</span><span class="sxs-lookup"><span data-stu-id="c6d0e-370">More Information</span></span>
 <span data-ttu-id="c6d0e-371">如需清單的詳細資訊，請參閱[資料表、矩陣和清單 &#40;報表產生器和 ssrs&#41;](report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)、[列出 &#40;報表產生器和 ssrs&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)、 [tablix 資料區區域 &#40;報表產生器和 Ssrs&#41;](report-design/tablix-data-region-areas-report-builder-and-ssrs.md)，以及[Tablix 資料區的儲存格、資料列和資料行 &#40;報表產生器&#41; 和 SSRS](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-371">For more information about lists, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](report-design/tables-matrices-and-lists-report-builder-and-ssrs.md), [Lists &#40;Report Builder and SSRS&#41;](report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md), [Tablix Data Region Areas &#40;Report Builder and SSRS&#41;](report-design/tablix-data-region-areas-report-builder-and-ssrs.md), and [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).</span></span>

 <span data-ttu-id="c6d0e-372">如需查詢設計工具的詳細資訊，請參閱[查詢設計工具 &#40;報表產生器&#41;](../../2014/reporting-services/query-designers-report-builder.md) 和[以文字為基礎的查詢設計工具使用者介面 &#40;報表產生器&#41;](report-data/text-based-query-designer-user-interface-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="c6d0e-372">For more information about query designers, see [Query Designers &#40;Report Builder&#41;](../../2014/reporting-services/query-designers-report-builder.md) and [Text-based Query Designer User Interface &#40;Report Builder&#41;](report-data/text-based-query-designer-user-interface-report-builder.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c6d0e-373">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6d0e-373">See Also</span></span>
 <span data-ttu-id="c6d0e-374">[SQL Server 2014 中的](report-builder/report-builder-in-sql-server-2016.md)[教學課程 &#40;報表產生器&#41;](report-builder-tutorials.md)報表產生器</span><span class="sxs-lookup"><span data-stu-id="c6d0e-374">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) [Report Builder in SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)</span></span>


