---
title: 教學課程：將文字格式化 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 67d8513e-8a70-464b-b87f-e91d010cfd82
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c96b500f8aa30b77c78f75ccd1342398fd44eb2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706113"
---
# <a name="tutorial-format-text-report-builder"></a><span data-ttu-id="4d682-102">教學課程：格式化文字 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="4d682-102">Tutorial: Format Text (Report Builder)</span></span>
  <span data-ttu-id="4d682-103">在本教學課程中，您將能練習以各種不同的方式格式化文字。</span><span class="sxs-lookup"><span data-stu-id="4d682-103">In this tutorial, you can practice formatting text in various ways.</span></span> <span data-ttu-id="4d682-104">使用資料來源和資料集設定空白報表之後，您可以挑選想要探索的步驟來進行。</span><span class="sxs-lookup"><span data-stu-id="4d682-104">After you set up the blank report with the data source and dataset, you can pick and choose the steps that you want to explore.</span></span>  
  
 <span data-ttu-id="4d682-105">下圖顯示報表，與您將要建立的報表相似。</span><span class="sxs-lookup"><span data-stu-id="4d682-105">The following illustration shows a report similar to the one you will create.</span></span>  
  
 <span data-ttu-id="4d682-106">![rs_FormatTextFinal](../../2014/tutorials/media/rs-formattextfinal.gif "rs_FormatTextFinal")</span><span class="sxs-lookup"><span data-stu-id="4d682-106">![rs_FormatTextFinal](../../2014/tutorials/media/rs-formattextfinal.gif "rs_FormatTextFinal")</span></span>  
  
 <span data-ttu-id="4d682-107">您在某個步驟故意出錯，所以知道錯誤的原因是什麼。</span><span class="sxs-lookup"><span data-stu-id="4d682-107">In one step, you make a mistake on purpose so you can see why it is a mistake.</span></span> <span data-ttu-id="4d682-108">接著您要更正錯誤以便達到想要的效果。</span><span class="sxs-lookup"><span data-stu-id="4d682-108">Then you correct the mistake to achieve the desired effect.</span></span>  
  
 <span data-ttu-id="4d682-109">本教學課程所建立的報表另有一個增強型版本，可從範例 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 報表產生器報表取得。</span><span class="sxs-lookup"><span data-stu-id="4d682-109">An enhanced version of the report you create in this tutorial is available as a sample [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Report Builder report.</span></span> <span data-ttu-id="4d682-110">如需下載此範例報表及其他專案的詳細資訊，請參閱[報表產生器範例報表](https://go.microsoft.com/fwlink/?LinkId=184851)。</span><span class="sxs-lookup"><span data-stu-id="4d682-110">For more information about downloading this sample report and others, see [Report Builder sample reports](https://go.microsoft.com/fwlink/?LinkId=184851).</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="4d682-111">您將瞭解的內容</span><span class="sxs-lookup"><span data-stu-id="4d682-111">What You Will Learn</span></span>  
  
### <a name="set-up-the-report"></a><span data-ttu-id="4d682-112">設定報表</span><span class="sxs-lookup"><span data-stu-id="4d682-112">Set Up the Report</span></span>  
 1. [<span data-ttu-id="4d682-113">建立具有資料來源和資料集的空白報表</span><span class="sxs-lookup"><span data-stu-id="4d682-113">Create a Blank Report with a Data Source and Dataset</span></span>](#CreateReport)  
  
 2. [<span data-ttu-id="4d682-114">將欄位加入至報表設計介面 (先做錯，再用正確的方法)</span><span class="sxs-lookup"><span data-stu-id="4d682-114">Add a Field to the Report Design Surface (Incorrectly, then Correctly)</span></span>](#AddField)  
  
 3. [<span data-ttu-id="4d682-115">將資料表加入至報表 Design Surface</span><span class="sxs-lookup"><span data-stu-id="4d682-115">Add a Table to the Report Design Surface</span></span>](#AddTable)  
  
### <a name="pick-and-choose"></a><span data-ttu-id="4d682-116">隨意挑選</span><span class="sxs-lookup"><span data-stu-id="4d682-116">Pick and Choose</span></span>  
 [<span data-ttu-id="4d682-117">將超連結加入至報表</span><span class="sxs-lookup"><span data-stu-id="4d682-117">Add a Hyperlink to the Report</span></span>](#AddHyperlink)  
  
 [<span data-ttu-id="4d682-118">旋轉報表中的文字</span><span class="sxs-lookup"><span data-stu-id="4d682-118">Rotate Text in the Report</span></span>](#RotateText)  
  
 [<span data-ttu-id="4d682-119">顯示 HTML 格式的文字</span><span class="sxs-lookup"><span data-stu-id="4d682-119">Displaying Text with HTML Formatting</span></span>](#FormatHTML)  
  
 [<span data-ttu-id="4d682-120">貨幣格式</span><span class="sxs-lookup"><span data-stu-id="4d682-120">Format Currency</span></span>](#FormatCurrency)  
  
 [<span data-ttu-id="4d682-121">儲存報表</span><span class="sxs-lookup"><span data-stu-id="4d682-121">Save the Report</span></span>](#Save)  
  
 <span data-ttu-id="4d682-122">完成這個教學課程的估計時間：30 分鐘。</span><span class="sxs-lookup"><span data-stu-id="4d682-122">Estimated time to complete this tutorial: 20 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d682-123">需求</span><span class="sxs-lookup"><span data-stu-id="4d682-123">Requirements</span></span>  
 <span data-ttu-id="4d682-124">如需需求的詳細資訊，請參閱[教學課程的必要條件 &#40;報表產生器&#41;](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="4d682-124">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="create-a-blank-report-with-a-data-source-and-dataset"></a><a name="CreateReport"></a><span data-ttu-id="4d682-125">建立具有資料來源和資料集的空白報表</span><span class="sxs-lookup"><span data-stu-id="4d682-125">Create a Blank Report with a Data Source and Dataset</span></span>  
  
#### <a name="to-create-a-blank-report"></a><span data-ttu-id="4d682-126">建立空白報表</span><span class="sxs-lookup"><span data-stu-id="4d682-126">To create a blank report</span></span>  
  
1.  <span data-ttu-id="4d682-127">按一下 [ **開始**]、依序指向 [ **程式集**] 和 [ [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**報表產生器**]，然後按一下 [ **報表產生器**]。</span><span class="sxs-lookup"><span data-stu-id="4d682-127">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**Report Builder**, and then click **Report Builder**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4d682-128">**[使用者入門]** 對話方塊應會隨即出現。</span><span class="sxs-lookup"><span data-stu-id="4d682-128">The **Getting Started** dialog box should appear.</span></span> <span data-ttu-id="4d682-129">如果沒有出現，請從 [報表產生器] 按鈕按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="4d682-129">If it does not, from the Report Builder button, click **New**.</span></span>  
  
2.  <span data-ttu-id="4d682-130">在 **[使用者入門]** 對話方塊的左窗格中，確認已選取 **[新增報表]** 。</span><span class="sxs-lookup"><span data-stu-id="4d682-130">In the left pane of the **Getting Started** dialog box, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="4d682-131">在右窗格中，按一下 **[空白報表]**。</span><span class="sxs-lookup"><span data-stu-id="4d682-131">In the right pane, click **Blank Report**.</span></span>  
  
#### <a name="to-create-a-data-source"></a><span data-ttu-id="4d682-132">建立資料來源</span><span class="sxs-lookup"><span data-stu-id="4d682-132">To create a data source</span></span>  
  
1.  <span data-ttu-id="4d682-133">在 [報表資料] 窗格中，按一下 **[新增]**，然後按一下 **[資料來源]**。</span><span class="sxs-lookup"><span data-stu-id="4d682-133">In the Report Data pane, click **New**, and then click **Data Source**.</span></span>  
  
2.  <span data-ttu-id="4d682-134">在 [名稱]\*\*\*\* 方塊中，鍵入：**TextDataSource**</span><span class="sxs-lookup"><span data-stu-id="4d682-134">In the **Name** box, type: **TextDataSource**</span></span>  
  
3.  <span data-ttu-id="4d682-135">按一下 **[使用內嵌於報表中的連接]**。</span><span class="sxs-lookup"><span data-stu-id="4d682-135">Click **Use a connection embedded in my report**.</span></span>  
  
4.  <span data-ttu-id="4d682-136">確認連線類型為 [Microsoft SQL Server]，然後在 [**連接字串**] 方塊中輸入： **Data Source \<servername> =**</span><span class="sxs-lookup"><span data-stu-id="4d682-136">Verify that the connection type is Microsoft SQL Server, and then in the **Connection string** box type: **Data Source = \<servername>**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4d682-137">\<servername>運算式 (例如 Report001) 會指定已安裝 SQL Server Database Engine 執行個體的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="4d682-137">The expression \<servername>, for example Report001, specifies a computer on which an instance of the SQL Server Database Engine is installed.</span></span> <span data-ttu-id="4d682-138">本教學課程無須任何特定資料，您只需要連接到 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="4d682-138">This tutorial does not need specific data; it just needs a connection to a [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database.</span></span> <span data-ttu-id="4d682-139">如果您已有資料來源連接列於 [資料來源連接]\*\*\*\* 底下，就可以選取該連接並移至下一個程序「建立資料集」。</span><span class="sxs-lookup"><span data-stu-id="4d682-139">If you already have a data source connection listed under **Data Source Connections**, you can select it and go to the next procedure, "To create a dataset."</span></span> <span data-ttu-id="4d682-140">如需詳細資訊，請參閱[取得資料連線的替代方式 &#40;報表產生器&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="4d682-140">For more information, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-create-a-dataset"></a><span data-ttu-id="4d682-141">建立資料集</span><span class="sxs-lookup"><span data-stu-id="4d682-141">To create a dataset</span></span>  
  
1.  <span data-ttu-id="4d682-142">在 [報表資料] 窗格中，按一下 **[新增]**，然後按一下 **[資料集]**。</span><span class="sxs-lookup"><span data-stu-id="4d682-142">In the Report Data pane, click **New**, and then click **Dataset**.</span></span>  
  
2.  <span data-ttu-id="4d682-143">確認資料來源為 **TextDataSource**。</span><span class="sxs-lookup"><span data-stu-id="4d682-143">Verify that the data source is **TextDataSource**.</span></span>  
  
3.  <span data-ttu-id="4d682-144">在 [名稱]\*\*\*\* 方塊中，鍵入：**TextDataset**。</span><span class="sxs-lookup"><span data-stu-id="4d682-144">In the **Name** box, type: **TextDataset.**</span></span>  
  
4.  <span data-ttu-id="4d682-145">確認已選取 **[文字]** 查詢類型，然後按一下 **[查詢設計工具]**。</span><span class="sxs-lookup"><span data-stu-id="4d682-145">Verify that the **Text** query type is selected, and then click **Query Designer**.</span></span>  
  
5.  <span data-ttu-id="4d682-146">按一下 **[當成文字編輯]**。</span><span class="sxs-lookup"><span data-stu-id="4d682-146">Click **Edit as Text**.</span></span>  
  
6.  <span data-ttu-id="4d682-147">將下列查詢貼入查詢窗格中：</span><span class="sxs-lookup"><span data-stu-id="4d682-147">Paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    ```  
  
7.  <span data-ttu-id="4d682-148">按一下 [執行]\(**!**) 來執行查詢。</span><span class="sxs-lookup"><span data-stu-id="4d682-148">Click Run (**!**) to run the query.</span></span>  
  
     <span data-ttu-id="4d682-149">查詢結果會成為可供報表顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="4d682-149">The query results are the data available to display in your report.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="add-a-field-to-the-report-design-surface"></a><a name="AddField"></a><span data-ttu-id="4d682-150">將欄位加入至報表 Design Surface</span><span class="sxs-lookup"><span data-stu-id="4d682-150">Add a Field to the Report Design Surface</span></span>  
 <span data-ttu-id="4d682-151">如果希望擷取自資料集的欄位出現在報表中，您可能會不加思索地直接將欄位拖曳到設計介面。</span><span class="sxs-lookup"><span data-stu-id="4d682-151">If you want a field from your dataset to appear in a report, your first impulse may be to drag it directly to the design surface.</span></span> <span data-ttu-id="4d682-152">此練習將點出為何這樣做無效，以及應該改用的方法。</span><span class="sxs-lookup"><span data-stu-id="4d682-152">This exercise points out why that doesn't work and what to do instead.</span></span>  
  
#### <a name="to-add-a-field-to-the-report-and-get-the-wrong-result"></a><span data-ttu-id="4d682-153">將欄位加入至報表 (會得到錯誤的結果)</span><span class="sxs-lookup"><span data-stu-id="4d682-153">To add a field to the report (and get the wrong result)</span></span>  
  
1.  <span data-ttu-id="4d682-154">將 [FullName]\*\*\*\* 欄位從 [報表資料] 窗格拖曳到設計介面。</span><span class="sxs-lookup"><span data-stu-id="4d682-154">Drag the **FullName** field from the Report Data pane to the design surface.</span></span>  
  
     <span data-ttu-id="4d682-155">報表產生器會建立一個內有運算式 (以 \<Expr>表示) 的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="4d682-155">Report Builder creates a text box with an expression in it, represented as \<Expr>.</span></span>  
  
2.  <span data-ttu-id="4d682-156">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4d682-156">Click **Run**.</span></span>  
  
     <span data-ttu-id="4d682-157">請注意，只有一筆記錄**Fernando Ross**，這是查詢中第一筆記錄的字母順序。</span><span class="sxs-lookup"><span data-stu-id="4d682-157">Note that there is just one record, **Fernando Ross**, which is alphabetically the first record in the query.</span></span> <span data-ttu-id="4d682-158">欄位並未重複成顯示該欄位內的其他記錄。</span><span class="sxs-lookup"><span data-stu-id="4d682-158">The field does not repeat to show the other records in that field.</span></span>  
  
3.  <span data-ttu-id="4d682-159">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="4d682-159">Click **Design** to return to design view.</span></span>  
  
4.  <span data-ttu-id="4d682-160">選取文字方塊中的運算式 \<Expr> 。</span><span class="sxs-lookup"><span data-stu-id="4d682-160">Select the expression \<Expr> in the text box.</span></span>  
  
5.  <span data-ttu-id="4d682-161">在 [屬性] 窗格中，您會看到 [值]\*\*\*\* 屬性如下 (若未看見 [屬性] 窗格，請檢查 [檢視]\*\*\*\* 索引標籤上的 [屬性]\*\*\*\*)：</span><span class="sxs-lookup"><span data-stu-id="4d682-161">In the Properties pane, for the **Value** property, you see the following (if you don't see the Properties pane, on the **View** tab, check **Properties**):</span></span>  
  
    ```  
    =First(Fields!FullName.Value, "TextDataSet")  
    ```  
  
     <span data-ttu-id="4d682-162">`First` 函數是設計成僅擷取欄位內的第一個值，而其目的也已達到。</span><span class="sxs-lookup"><span data-stu-id="4d682-162">The `First` function is designed to retrieve only the first value in a field, and that is what it has done.</span></span>  
  
     <span data-ttu-id="4d682-163">直接將欄位拖曳到設計介面會建立文字方塊。</span><span class="sxs-lookup"><span data-stu-id="4d682-163">Dragging the field directly to the design surface created a text box.</span></span> <span data-ttu-id="4d682-164">文字方塊本身並非資料區，所以不會顯示來自報表資料集的資料。</span><span class="sxs-lookup"><span data-stu-id="4d682-164">Text boxes by themselves are not data regions, so they do not display data from a report dataset.</span></span> <span data-ttu-id="4d682-165">位於資料區 (例如資料表、矩陣和清單) 內的文字方塊才會顯示資料。</span><span class="sxs-lookup"><span data-stu-id="4d682-165">Text boxes in data regions, such as tables, matrices, and lists, do display data.</span></span>  
  
6.  <span data-ttu-id="4d682-166">選取文字方塊 (如果您已選取運算式，請按 ESC 鍵選取文字方塊)，然後按下 DELETE 鍵。</span><span class="sxs-lookup"><span data-stu-id="4d682-166">Select the text box (if you have the expression selected, press ESC to select the text box), and press the DELETE key.</span></span>  
  
#### <a name="to-add-a-field-to-the-report-and-get-the-right-result"></a><span data-ttu-id="4d682-167">將欄位加入至報表 (會得到正確的結果)</span><span class="sxs-lookup"><span data-stu-id="4d682-167">To add a field to the report (and get the right result)</span></span>  
  
1.  <span data-ttu-id="4d682-168">在功能區的 [插入]\*\*\*\* 索引標籤上，按一下 [資料區]\*\*\*\* 區域內的 [清單]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4d682-168">On the **Insert** tab of the ribbon, in the **Data Regions** area, click **List**.</span></span> <span data-ttu-id="4d682-169">按一下設計介面，然後進行拖曳以建立寬約 2 英吋且高約 1 英吋的方塊。</span><span class="sxs-lookup"><span data-stu-id="4d682-169">Click the design surface, and then drag to create a box that about two inches wide and one inch tall.</span></span>  
  
2.  <span data-ttu-id="4d682-170">將 [FullName]\*\*\*\* 欄位從 [報表資料] 窗格拖曳到清單方塊中。</span><span class="sxs-lookup"><span data-stu-id="4d682-170">Drag the **FullName** field from the Report Data pane to the list box.</span></span>  
  
     <span data-ttu-id="4d682-171">這回報表產生器會建立一個內有運算式 `[FullName]` 的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="4d682-171">This time Report Builder creates a text box with the expression `[FullName]` in it.</span></span>  
  
3.  <span data-ttu-id="4d682-172">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4d682-172">Click **Run**.</span></span>  
  
     <span data-ttu-id="4d682-173">請注意，此時方塊已經重複成顯示查詢中的所有記錄。</span><span class="sxs-lookup"><span data-stu-id="4d682-173">Note that this time the box repeats to show all the records in the query.</span></span>  
  
4.  <span data-ttu-id="4d682-174">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="4d682-174">Click **Design** to return to design view.</span></span>  
  
5.  <span data-ttu-id="4d682-175">選取文字方塊中的運算式。</span><span class="sxs-lookup"><span data-stu-id="4d682-175">Select the expression in the text box.</span></span>  
  
6.  <span data-ttu-id="4d682-176">在 [屬性] 窗格中，您會看到 [值]\*\*\*\* 屬性如下：</span><span class="sxs-lookup"><span data-stu-id="4d682-176">In the Properties pane, for the **Value** property, you see the following:</span></span>  
  
    ```  
    =Fields!FullName.Value  
    ```  
  
     <span data-ttu-id="4d682-177">透過將文字方塊拖曳到清單資料區，就可以顯示資料集內的資料。</span><span class="sxs-lookup"><span data-stu-id="4d682-177">By dragging the text box to the list data region, you display the data that is in the dataset.</span></span>  
  
7.  <span data-ttu-id="4d682-178">選取清單方塊，然後按下 DELETE 鍵。</span><span class="sxs-lookup"><span data-stu-id="4d682-178">Select the list box and press the DELETE key.</span></span>  
  
##  <a name="add-a-table-to-the-report-design-surface"></a><a name="AddTable"></a><span data-ttu-id="4d682-179">將資料表加入至報表 Design Surface</span><span class="sxs-lookup"><span data-stu-id="4d682-179">Add a Table to the Report Design Surface</span></span>  
 <span data-ttu-id="4d682-180">建立這個資料表，以便能夠在其中放置超連結和旋轉的文字。</span><span class="sxs-lookup"><span data-stu-id="4d682-180">Create this table so that you'll have a place to put hyperlinks and rotated text.</span></span>  
  
#### <a name="to-add-a-table-to-the-report"></a><span data-ttu-id="4d682-181">將資料表加入至報表</span><span class="sxs-lookup"><span data-stu-id="4d682-181">To add a table to the report</span></span>  
  
1.  <span data-ttu-id="4d682-182">在 [**插入**] 功能表上，按一下 [**資料表**]，然後按一下 [**資料表嚮導]**。</span><span class="sxs-lookup"><span data-stu-id="4d682-182">On the **Insert** menu, click **Table**, and then click **Table Wizard**.</span></span>  
  
2.  <span data-ttu-id="4d682-183">在 [新增資料表或矩陣] wizard 的 [**選擇資料集**] 頁面上，按一下 [**選擇此報表或共用資料集中的現有資料集**]，然後按一下**此報表) 中的 [TextDataset (**]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="4d682-183">On the **Choose a dataset** page of the New Table or Matrix wizard, click **Choose an existing dataset in this report or a shared dataset**, and click **TextDataset (in this Report)**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="4d682-184">在 [**排欄欄位**] 頁面上，將 [**區域**]、[ **linktext>**] 和 [**產品**] 欄位拖曳至 [**資料\*\*\*\*列群組**]，將 [ **Sales** ] 欄位拖曳至 [值]，然後按一下 **[**</span><span class="sxs-lookup"><span data-stu-id="4d682-184">On the **Arrange fields** page, drag the **Territory**, **LinkText**, and **Product** fields to **Row groups**, drag the **Sales** field to **Values**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="4d682-185">在 [**選擇**配置] 頁面上，清除 [**展開/** 折迭群組] 核取方塊，讓您可以看見整個資料表，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="4d682-185">On the **Choose the layout** page, clear the **Expand/collapse groups** check box so you can see the whole table, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="4d682-186">在 [**選擇樣式**] 頁面上，按一下 [**平板**電腦]，然後按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="4d682-186">On the **Choose a style** page, click **Slate**, and then click **Finish**.</span></span>  
  
6.  <span data-ttu-id="4d682-187">將資料表拖曳到標題區塊下方。</span><span class="sxs-lookup"><span data-stu-id="4d682-187">Drag the table so it is below the title block.</span></span>  
  
7.  <span data-ttu-id="4d682-188">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4d682-188">Click **Run**.</span></span>  
  
     <span data-ttu-id="4d682-189">資料表看起來似乎沒問題，不過卻有兩個總計資料列。</span><span class="sxs-lookup"><span data-stu-id="4d682-189">The table looks OK, but it has two Total rows.</span></span> <span data-ttu-id="4d682-190">**Linktext>** 欄位不需要總計資料列。</span><span class="sxs-lookup"><span data-stu-id="4d682-190">The **LinkText** field doesn't need a Total row.</span></span>  
  
8.  <span data-ttu-id="4d682-191">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="4d682-191">Click **Design** to return to design view.</span></span>  
  
9. <span data-ttu-id="4d682-192">以滑鼠右鍵按一下包含的文字方塊 `[LinkText]` ，然後按一下 [**分割資料格**]。</span><span class="sxs-lookup"><span data-stu-id="4d682-192">Right-click the text box that contains `[LinkText]`, and click **Split Cells**.</span></span>  
  
10. <span data-ttu-id="4d682-193">選取資料格下方的空白資料格 `[LinkText]` ，然後按住 SHIFT 鍵並選取其右邊的兩個數據格： [ **Product** ] 資料行中的 [ **Total** ] 資料格，以及 `[Sum(Sales)]` [ **Sales** ] 資料行中的資料格。</span><span class="sxs-lookup"><span data-stu-id="4d682-193">Select the empty cell below the `[LinkText]` cell, and then hold down the SHIFT key and select the two cells to its right: the **Total** cell in the **Product** column and the `[Sum(Sales)]` cell in the **Sales** column.</span></span>  
  
11. <span data-ttu-id="4d682-194">選取這三個數據格後，以滑鼠右鍵按一下其中一個資料格，然後按一下 [**刪除資料列**]。</span><span class="sxs-lookup"><span data-stu-id="4d682-194">With those three cells selected, right-click one of those cells and click **Delete Row**.</span></span>  
  
12. <span data-ttu-id="4d682-195">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4d682-195">Click **Run**.</span></span>  
  
##  <a name="add-a-hyperlink-to-the-report"></a><a name="AddHyperlink"></a><span data-ttu-id="4d682-196">將超連結加入至報表</span><span class="sxs-lookup"><span data-stu-id="4d682-196">Add a Hyperlink to the Report</span></span>  
 <span data-ttu-id="4d682-197">在本節中，您要加入超連結指向上一節資料表中的文字。</span><span class="sxs-lookup"><span data-stu-id="4d682-197">In this section, you add a hyperlink to text in the table from the previous section.</span></span>  
  
#### <a name="to-add-a-hyperlink-to-the-report"></a><span data-ttu-id="4d682-198">加入超連結至報表</span><span class="sxs-lookup"><span data-stu-id="4d682-198">To add a hyperlink to the report</span></span>  
  
1.  <span data-ttu-id="4d682-199">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="4d682-199">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="4d682-200">以滑鼠右鍵按一下含有 `[LinkText]` 的資料格，然後按一下 [文字方塊屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4d682-200">Right-click in the cell containing `[LinkText]`, and click **Text Box Properties**.</span></span>  
  
3.  <span data-ttu-id="4d682-201">在 [**文字方塊屬性**] 方塊中，按一下 [**動作**]。</span><span class="sxs-lookup"><span data-stu-id="4d682-201">In the **Text Box Properties** box, click **Action**.</span></span>  
  
4.  <span data-ttu-id="4d682-202">按一下 [**移至 URL**]。</span><span class="sxs-lookup"><span data-stu-id="4d682-202">Click **Go to URL**.</span></span>  
  
5.  <span data-ttu-id="4d682-203">在 [**選取 url** ] 方塊中，按一下 **[URL]**，然後按一下 [**確定**]。</span><span class="sxs-lookup"><span data-stu-id="4d682-203">In the **Select URL** box, click **[URL]**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="4d682-204">請注意，文字看起來並無任何改變。</span><span class="sxs-lookup"><span data-stu-id="4d682-204">Note that the text does not look any different.</span></span> <span data-ttu-id="4d682-205">您需要進行調整使其彷彿連結文字。</span><span class="sxs-lookup"><span data-stu-id="4d682-205">You need to make it look like link text.</span></span>  
  
7.  <span data-ttu-id="4d682-206">選取 `[LinkText]`。</span><span class="sxs-lookup"><span data-stu-id="4d682-206">Select `[LinkText]`.</span></span>  
  
8.  <span data-ttu-id="4d682-207">在 [**首頁**] 索引標籤的 [**字型**] 區段中，按一下 [底線] 按鈕，然後按一下 [**色彩** **] 按鈕旁邊**的下拉箭號，再按一下 [**藍色**]。</span><span class="sxs-lookup"><span data-stu-id="4d682-207">In the **Font** section of the **Home** tab, click the **Underline** button, and then click the drop-down arrow next to the **Color** button, and click **Blue**.</span></span>  
  
9. <span data-ttu-id="4d682-208">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4d682-208">Click **Run**.</span></span>  
  
     <span data-ttu-id="4d682-209">文字現在看起來就像一個連結。</span><span class="sxs-lookup"><span data-stu-id="4d682-209">The text now looks like a link.</span></span>  
  
10. <span data-ttu-id="4d682-210">按一下該連結。</span><span class="sxs-lookup"><span data-stu-id="4d682-210">Click a link.</span></span> <span data-ttu-id="4d682-211">如果您的電腦已連接至網際網路，瀏覽器將會開啟報表產生器說明主題。</span><span class="sxs-lookup"><span data-stu-id="4d682-211">If the computer is connected to the Internet, a browser will open to a Report Builder Help topic.</span></span>  
  
##  <a name="rotate-text-in-the-report"></a><a name="RotateText"></a><span data-ttu-id="4d682-212">旋轉報表中的文字</span><span class="sxs-lookup"><span data-stu-id="4d682-212">Rotate Text in the Report</span></span>  
 <span data-ttu-id="4d682-213">在本節中，您要旋轉前幾節資料表中的部分文字。</span><span class="sxs-lookup"><span data-stu-id="4d682-213">In this section, you rotate some of the text in the table from the previous sections.</span></span>  
  
#### <a name="to-rotate-text"></a><span data-ttu-id="4d682-214">旋轉文字</span><span class="sxs-lookup"><span data-stu-id="4d682-214">To rotate text</span></span>  
  
1.  <span data-ttu-id="4d682-215">按一下 **[設計]** 返回 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="4d682-215">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="4d682-216">按一下包含下列項目的資料格： `[Territory].`</span><span class="sxs-lookup"><span data-stu-id="4d682-216">Click in the cell containing `[Territory].`</span></span>  
  
3.  <span data-ttu-id="4d682-217">在 [主資料夾]\*\*\*\* 索引標籤的 [字型]\*\*\*\* 區段中，按一下 [粗體]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4d682-217">On the **Home** tab in the **Font** section, click the **Bold** button.</span></span>  
  
4.  <span data-ttu-id="4d682-218">如果 [屬性] 窗格並未開啟，請選取 [檢視]\*\*\*\* 索引標籤上的 [屬性]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="4d682-218">If the Properties pane is not open, on the **View** tab, select the **Properties** check box.</span></span>  
  
5.  <span data-ttu-id="4d682-219">在 [屬性] 窗格中找出 [WritingMode] 屬性。</span><span class="sxs-lookup"><span data-stu-id="4d682-219">Locate the WritingMode property in the Properties pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4d682-220">當 [屬性] 窗格中的屬性組織成類別目錄時，WritingMode 會位於 [當地語系化]\*\*\*\* 類別目錄中。</span><span class="sxs-lookup"><span data-stu-id="4d682-220">When the properties in the Properties pane are organized into categories, WritingMode is in the **Localization** category.</span></span> <span data-ttu-id="4d682-221">請確定您已選取資料格，而不是文字。</span><span class="sxs-lookup"><span data-stu-id="4d682-221">Be sure you have selected the cell and not the text.</span></span> <span data-ttu-id="4d682-222">WritingMode 是文字方塊的屬性，並非文字的屬性。</span><span class="sxs-lookup"><span data-stu-id="4d682-222">WritingMode is a property of the text box, not of the text.</span></span>  
  
6.  <span data-ttu-id="4d682-223">在清單方塊中，按一下 [ **Rotate270**]。</span><span class="sxs-lookup"><span data-stu-id="4d682-223">In the list box, click **Rotate270**.</span></span>  
  
7.  <span data-ttu-id="4d682-224">在 [**首頁**] 索引標籤的 [**段落**] 區段中，按一下 [**中間**] 和 [**置**中] 按鈕，以垂直和水準方式找出資料格中央的文字。</span><span class="sxs-lookup"><span data-stu-id="4d682-224">On the **Home** tab in the **Paragraph** section, click the **Middle** and **Center** buttons to locate the text in the center of the cell both vertically and horizontally.</span></span>  
  
8.  <span data-ttu-id="4d682-225">按一下 [執行] (**!**)。</span><span class="sxs-lookup"><span data-stu-id="4d682-225">Click Run (**!**).</span></span>  
  
 <span data-ttu-id="4d682-226">如今 `[Territory]` 資料格中的文字已呈垂直方向，從資料格底部往上書寫。</span><span class="sxs-lookup"><span data-stu-id="4d682-226">Now the text in the `[Territory]` cell runs vertically from the bottom to the top of the cells.</span></span>  
  
##  <a name="displaying-text-with-html-formatting"></a><a name="FormatHTML"></a><span data-ttu-id="4d682-227">顯示 HTML 格式的文字</span><span class="sxs-lookup"><span data-stu-id="4d682-227">Displaying Text with HTML Formatting</span></span>  
  
#### <a name="to-display-text-formatted-as-html"></a><span data-ttu-id="4d682-228">顯示格式化為 HTML 的文字</span><span class="sxs-lookup"><span data-stu-id="4d682-228">To display text formatted as HTML</span></span>  
  
1.  <span data-ttu-id="4d682-229">按一下 [**設計**]，切換至設計檢視。</span><span class="sxs-lookup"><span data-stu-id="4d682-229">Click **Design** to switch to design view.</span></span>  
  
2.  <span data-ttu-id="4d682-230">在 [插入]\*\*\*\* 索引標籤上，按一下 [文字方塊]\*\*\*\*，然後在設計介面上按一下並拖曳，以在資料表底下建立大約 4 英吋寬、3 英吋高的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="4d682-230">On the **Insert** tab, click **Text Box**, and then on the design surface, click and drag to create a text box under the table, about four inches wide and three inches tall.</span></span>  
  
3.  <span data-ttu-id="4d682-231">複製以下文字並將其貼入文字方塊中：</span><span class="sxs-lookup"><span data-stu-id="4d682-231">Copy this text and paste it into the text box:</span></span>  
  
    ```  
    <h4>Limitations of cascading style sheet attributes</h4>  
          <p>Only a basic set of <b>cascading style sheet (CSS)</b> attributes are defined:</p>  
          <ul><li>  
              text-align, text-indent  
            </li><li>  
              font-family, font-size  
            </li><li>  
              color  
            </li><li>  
              padding, padding-bottom, padding-top, padding-right, padding-left  
            </li><li>  
              font-weight  
            </li></ul>  
    ```  
  
4.  <span data-ttu-id="4d682-232">選取文字方塊中的所有文字。</span><span class="sxs-lookup"><span data-stu-id="4d682-232">Select all of the text in the text box.</span></span>  
  
     <span data-ttu-id="4d682-233">因為這是文字的屬性，而非文字方塊屬性，您可以在單一文字方塊中混雜純文字與使用 HTML 標記做為樣式的文字。</span><span class="sxs-lookup"><span data-stu-id="4d682-233">This is a property of the text, not the text box, so in one text box you could have a mixture of plain text and text that uses HTML tags as styles.</span></span>  
  
5.  <span data-ttu-id="4d682-234">以滑鼠右鍵按一下所有選取的文字，然後按一下 [文字屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4d682-234">Right-click all of the selected text and click **Text Properties**.</span></span>  
  
6.  <span data-ttu-id="4d682-235">在 [**一般**] 頁面的 [**標記類型**] 底下，按一下 [ **Html-將 html 標記解讀為樣式**]。</span><span class="sxs-lookup"><span data-stu-id="4d682-235">On the **General** page, under **Markup type**, click **HTML - Interpret HTML tags as styles**.</span></span>  
  
7.  <span data-ttu-id="4d682-236">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="4d682-236">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="4d682-237">按一下 [執行]\(**!**) 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="4d682-237">Click Run (**!**) to preview the report.</span></span>  
  
 <span data-ttu-id="4d682-238">文字方塊中的文字會顯示成標頭、段落和項目符號清單。</span><span class="sxs-lookup"><span data-stu-id="4d682-238">The text in the text box is displayed as a heading, paragraph, and bulleted list.</span></span>  
  
##  <a name="format-currency"></a><a name="FormatCurrency"></a><span data-ttu-id="4d682-239">貨幣格式</span><span class="sxs-lookup"><span data-stu-id="4d682-239">Format Currency</span></span>  
  
#### <a name="to-format-numbers-as-currency"></a><span data-ttu-id="4d682-240">將數字格式化為貨幣</span><span class="sxs-lookup"><span data-stu-id="4d682-240">To format numbers as currency</span></span>  
  
1.  <span data-ttu-id="4d682-241">按一下 [**設計**]，切換至設計檢視。</span><span class="sxs-lookup"><span data-stu-id="4d682-241">Click **Design** to switch to design view.</span></span>  
  
2.  <span data-ttu-id="4d682-242">按一下含有 `[Sum(Sales)]`的最上方資料表資料格，然後按住 SHIFT 鍵，再按一下含有 `[Sum(Sales)]`的底部資料表資料格。</span><span class="sxs-lookup"><span data-stu-id="4d682-242">Click the top table cell that contains `[Sum(Sales)]`, hold down the SHIFT key, and click the bottom table cell that contains `[Sum(Sales)]`.</span></span>  
  
3.  <span data-ttu-id="4d682-243">在 [主資料夾]\*\*\*\* 索引標籤的 [數字]\*\*\*\* 群組中，按一下 [貨幣]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4d682-243">On the **Home** tab, in the **Number** group, click the **Currency** button.</span></span>  
  
4.  <span data-ttu-id="4d682-244"> (選擇性) 在 [**首頁**] 索引標籤的 [**數位**] 群組中，按一下 [**預留位置樣式**] 按鈕，然後按一下 [**範例值**]，以查看數位的格式化方式。</span><span class="sxs-lookup"><span data-stu-id="4d682-244">(Optional) On the **Home** tab, in the **Number** group, click the **Placeholder Styles** button and click **Sample Values** to see how the numbers will be formatted.</span></span>  
  
5.  <span data-ttu-id="4d682-245">(選擇性) 在 [主資料夾]\*\*\*\* 索引標籤的 [數字]\*\*\*\* 群組中，按一下[減少小數位數]\*\*\*\* 按鈕兩次，顯示沒有分的貨幣數字。</span><span class="sxs-lookup"><span data-stu-id="4d682-245">(Optional) On the **Home** tab, in the **Number** group, click the **Decrease Decimals** button twice to display dollar figures with no cents.</span></span>  
  
6.  <span data-ttu-id="4d682-246">按一下 [執行]\(**!**) 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="4d682-246">Click Run (**!**) to preview the report.</span></span>  
  
 <span data-ttu-id="4d682-247">報表如今已顯示格式化的資料，更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="4d682-247">The report now displays formatted data and is easier to read.</span></span>  
  
##  <a name="save-the-report"></a><a name="Save"></a><span data-ttu-id="4d682-248">儲存報表</span><span class="sxs-lookup"><span data-stu-id="4d682-248">Save the Report</span></span>  
 <span data-ttu-id="4d682-249">您可以將報表儲存至報表伺服器、SharePoint 文件庫或您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="4d682-249">You can save reports to a report server, SharePoint library, or your computer.</span></span>  
  
 <span data-ttu-id="4d682-250">本教學課程會將報表儲存至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="4d682-250">In this tutorial, save the report to a report server.</span></span> <span data-ttu-id="4d682-251">如果您沒有報表伺服器的存取權，請將報表儲存在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="4d682-251">If you do not have access to a report server, save the report to your computer.</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="4d682-252">若要將報表儲存在報表伺服器上</span><span class="sxs-lookup"><span data-stu-id="4d682-252">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="4d682-253">在 **[報表產生器]** 按鈕中，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="4d682-253">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="4d682-254">按一下 **[最近使用的網站和伺服器]**。</span><span class="sxs-lookup"><span data-stu-id="4d682-254">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="4d682-255">選取或輸入您有權儲存報表之報表伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d682-255">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="4d682-256">「正在連接到報表伺服器」訊息隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="4d682-256">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="4d682-257">連接完成時，您就會看見報表伺服器管理員指定為預設報表位置之報表資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="4d682-257">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>  
  
4.  <span data-ttu-id="4d682-258">在 [名稱]\*\*\*\* 中，將預設名稱取代為您選擇的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d682-258">In **Name**, replace the default name with a name of your choosing.</span></span>  
  
5.  <span data-ttu-id="4d682-259">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="4d682-259">Click **Save**.</span></span>  
  
 <span data-ttu-id="4d682-260">報表就會儲存至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="4d682-260">The report is saved to the report server.</span></span> <span data-ttu-id="4d682-261">您連接之報表伺服器的名稱會顯示在視窗底部的狀態列中。</span><span class="sxs-lookup"><span data-stu-id="4d682-261">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="4d682-262">將報表儲存到您的電腦上</span><span class="sxs-lookup"><span data-stu-id="4d682-262">To save the report on your computer</span></span>  
  
1.  <span data-ttu-id="4d682-263">在 **[報表產生器]** 按鈕中，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="4d682-263">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="4d682-264">按一下 **[桌面]**、 **[我的文件]** 或 **[我的電腦]**，然後瀏覽到您要儲存報表的資料夾。</span><span class="sxs-lookup"><span data-stu-id="4d682-264">Click **Desktop**, **My Documents**, or **My computer**, and then browse to the folder where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="4d682-265">在 [名稱]\*\*\*\* 中，將預設名稱取代為您選擇的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d682-265">In **Name**, replace the default name with a name of your choosing.</span></span>  
  
4.  <span data-ttu-id="4d682-266">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="4d682-266">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4d682-267">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4d682-267">Next Steps</span></span>  
 <span data-ttu-id="4d682-268">有許多方式可以在報表產生器[教學課程：建立自由格式報表 &#40;報表產生器&#41;](../reporting-services/tutorial-creating-a-free-form-report-report-builder.md)包含更多範例。</span><span class="sxs-lookup"><span data-stu-id="4d682-268">There are many ways to format text in Report Builder [Tutorial: Creating a Free Form Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-free-form-report-report-builder.md) contains more examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d682-269">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d682-269">See Also</span></span>  
 <span data-ttu-id="4d682-270">[教學課程 &#40;報表產生器&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="4d682-270">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 <span data-ttu-id="4d682-271">[將報表專案的格式設定 &#40;報表產生器和 SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4d682-271">[Formatting Report Items &#40;Report Builder and SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4d682-272">SQL Server 2014 中的報表產生器</span><span class="sxs-lookup"><span data-stu-id="4d682-272">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
