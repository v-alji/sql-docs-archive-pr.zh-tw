---
title: 教學課程： 將參數加入至報表 （報表產生器） |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eab34ec4-b3ad-4a76-95cc-07b2f75ee6d7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dff41066a2d505ab53b17a10fb3da9b6cb17130f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704785"
---
# <a name="tutorial-add-a-parameter-to-your-report-report-builder"></a><span data-ttu-id="77e76-102">教學課程：將參數加入至報表 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="77e76-102">Tutorial: Add a Parameter to Your Report (Report Builder)</span></span>
  <span data-ttu-id="77e76-103">將參數加入至報表可讓使用者從資料來源或報表中篩選報表資料。</span><span class="sxs-lookup"><span data-stu-id="77e76-103">Add a parameter to your report to let users filter report data from the data source or in the report.</span></span> <span data-ttu-id="77e76-104">系統會針對您包含在資料集查詢中的每個查詢參數，自動建立報表參數。</span><span class="sxs-lookup"><span data-stu-id="77e76-104">Report parameters are created automatically for each query parameter that you include in a dataset query.</span></span> <span data-ttu-id="77e76-105">參數資料類型會決定該類型會如何在報表檢視器工具列上顯示。</span><span class="sxs-lookup"><span data-stu-id="77e76-105">The parameter data type determines how it appears on the report view toolbar.</span></span>  
  
 <span data-ttu-id="77e76-106">![rs_tut_Parameter](../../2014/tutorials/media/rs-tut-parameter.gif "rs_tut_Parameter")</span><span class="sxs-lookup"><span data-stu-id="77e76-106">![rs_tut_Parameter](../../2014/tutorials/media/rs-tut-parameter.gif "rs_tut_Parameter")</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="77e76-107">您將瞭解的內容</span><span class="sxs-lookup"><span data-stu-id="77e76-107">What You Will Learn</span></span>  
 <span data-ttu-id="77e76-108">在本教學課程中，您將學習如何執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="77e76-108">In this tutorial you will learn how to do the following:</span></span>  
  
1.  [<span data-ttu-id="77e76-109">從資料表或矩陣精靈建立矩陣報表和資料集</span><span class="sxs-lookup"><span data-stu-id="77e76-109">Create a Matrix Report and Dataset from the Table or Matrix Wizard</span></span>](#Setup)  
  
2.  [<span data-ttu-id="77e76-110">從資料表或矩陣精靈組織資料、選擇配置和樣式</span><span class="sxs-lookup"><span data-stu-id="77e76-110">Organize Data, Choose Layout, and Style from the Table or Matrix Wizard</span></span>](#CompleteWizard)  
  
3.  [<span data-ttu-id="77e76-111">加入查詢參數來建立報表參數</span><span class="sxs-lookup"><span data-stu-id="77e76-111">Add a Query Parameter to Create a Report Parameter</span></span>](#Query)  
  
4.  [<span data-ttu-id="77e76-112">變更報表參數的預設資料類型和其他屬性</span><span class="sxs-lookup"><span data-stu-id="77e76-112">Change Default Data Type and Other Properties for a Report Parameter</span></span>](#ChangeDefaultProperties)  
  
    1.  [<span data-ttu-id="77e76-113">加入資料集來提供可用值與顯示名稱</span><span class="sxs-lookup"><span data-stu-id="77e76-113">Add a Dataset to Provide Available Values and Display Names</span></span>](#AddDataset)  
  
    2.  [<span data-ttu-id="77e76-114">指定可以用於建立多個值之下拉式清單的值</span><span class="sxs-lookup"><span data-stu-id="77e76-114">Specify Available Values to Create a Drop-List of Values</span></span>](#AvailableValues)  
  
    3.  [<span data-ttu-id="77e76-115">指定預設值讓報表能夠自動執行</span><span class="sxs-lookup"><span data-stu-id="77e76-115">Specify Default Values so the Report Runs Automatically</span></span>](#DefaultValues)  
  
    4.  [<span data-ttu-id="77e76-116">從具有名稱/值組的資料集中查閱值</span><span class="sxs-lookup"><span data-stu-id="77e76-116">Look up a Value from a Dataset that has Name/Value Pairs</span></span>](#NameValue)  
  
5.  [<span data-ttu-id="77e76-117">在報表中顯示選取的參數值</span><span class="sxs-lookup"><span data-stu-id="77e76-117">Display the Selected Parameter Value in the Report</span></span>](#Expression)  
  
6.  [<span data-ttu-id="77e76-118">在篩選中使用報表參數</span><span class="sxs-lookup"><span data-stu-id="77e76-118">Use the Report Parameter in a Filter</span></span>](#Filter)  
  
7.  [<span data-ttu-id="77e76-119">將報表參數變更為可以接受多個值</span><span class="sxs-lookup"><span data-stu-id="77e76-119">Change the Report Parameter to Accept Multiple Values</span></span>](#Multivalued)  
  
8.  [<span data-ttu-id="77e76-120">加入條件式可見性的布林參數</span><span class="sxs-lookup"><span data-stu-id="77e76-120">Add a Boolean Parameter for Conditional Visibility</span></span>](#Boolean)  
  
9. [<span data-ttu-id="77e76-121">加入報表標題</span><span class="sxs-lookup"><span data-stu-id="77e76-121">Add a Report Title</span></span>](#Title)  
  
10. [<span data-ttu-id="77e76-122">儲存報表</span><span class="sxs-lookup"><span data-stu-id="77e76-122">Save the Report</span></span>](#Save)  
  
> [!NOTE]  
>  <span data-ttu-id="77e76-123">在本教學課程中，精靈的步驟會合併為一個程序。</span><span class="sxs-lookup"><span data-stu-id="77e76-123">In this tutorial, the steps for the wizard are consolidated into one procedure.</span></span> <span data-ttu-id="77e76-124">如需如何瀏覽至報表伺服器、選擇資料來源以及建立資料集的逐步指示，請參閱本系列的第一個教學課程：[教學課程：建立基本資料表報表 &#40;報表產生器&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="77e76-124">For step-by-step instructions about how to browse to a report server, choose a data source, and create a dataset, see the first tutorial in this series: [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="77e76-125">完成本教學課程的估計時間：25 分鐘。</span><span class="sxs-lookup"><span data-stu-id="77e76-125">Estimated time to complete this tutorial: 25 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77e76-126">需求</span><span class="sxs-lookup"><span data-stu-id="77e76-126">Requirements</span></span>  
 <span data-ttu-id="77e76-127">如需需求的資訊，請參閱[教學課程的必要條件 &#40;報表產生器&#41;](../reporting-services/report-builder-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="77e76-127">For information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="1-create-a-matrix-report-and-dataset-from-the-table-or-matrix-wizard"></a><a name="Setup"></a><span data-ttu-id="77e76-128">1. 從資料表或矩陣 Wizard 建立矩陣報表和資料集</span><span class="sxs-lookup"><span data-stu-id="77e76-128">1. Create a Matrix Report and Dataset from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="77e76-129">建立矩陣報表、資料來源與資料集。</span><span class="sxs-lookup"><span data-stu-id="77e76-129">Create a matrix report, a data source, and a dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77e76-130">在本教學課程中，查詢會包含資料值，因此不需要外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="77e76-130">In this tutorial, the query contains the data values, so that it does not need an external data source.</span></span> <span data-ttu-id="77e76-131">這樣會使查詢相當冗長。</span><span class="sxs-lookup"><span data-stu-id="77e76-131">This makes the query quite long.</span></span> <span data-ttu-id="77e76-132">在商業環境中，查詢不會包含資料。</span><span class="sxs-lookup"><span data-stu-id="77e76-132">In a business environment, a query would not contain the data.</span></span> <span data-ttu-id="77e76-133">這僅供教學之用。</span><span class="sxs-lookup"><span data-stu-id="77e76-133">This is for learning purposes only.</span></span>  
  
#### <a name="to-create-a-new-matrix-report"></a><span data-ttu-id="77e76-134">若要建立新的矩陣報表</span><span class="sxs-lookup"><span data-stu-id="77e76-134">To create a new matrix report</span></span>  
  
1.  <span data-ttu-id="77e76-135">按一下 [ **開始**]、依序指向 [ **程式集**] 和 [ [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**報表產生器**]，然後按一下 [ **報表產生器**]。</span><span class="sxs-lookup"><span data-stu-id="77e76-135">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**Report Builder**, and then click **Report Builder**.</span></span>  
  
     <span data-ttu-id="77e76-136">[**消費者入門**] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="77e76-136">The **Getting Started** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="77e76-137"> 如果 **[使用者入門]** 對話方塊沒有出現，請在 **[報表產生器]** 按鈕中按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-137">If the **Getting Started** dialog box does not appear, from the **Report Builder** button, click **New**.</span></span>  
  
2.  <span data-ttu-id="77e76-138">在左窗格中，確認已選取 **[報表]** 。</span><span class="sxs-lookup"><span data-stu-id="77e76-138">In the left pane, verify that **Report** is selected.</span></span>  
  
3.  <span data-ttu-id="77e76-139">在右窗格中，按一下 **[資料表或矩陣精靈]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-139">In the right pane, click **Table or Matrix Wizard**.</span></span>  
  
4.  <span data-ttu-id="77e76-140">按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="77e76-140">Click **Create**.</span></span>  
  
5.  <span data-ttu-id="77e76-141">在 **[選擇資料集]** 頁面上，按一下 **[建立資料集]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-141">On the **Choose a dataset** page, click **Create a dataset**.</span></span>  
  
6.  <span data-ttu-id="77e76-142">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="77e76-142">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="77e76-143">在 **[選擇與資料來源的連接]** 頁面上，選取類型為 **[SQL Server]** 的資料來源。</span><span class="sxs-lookup"><span data-stu-id="77e76-143">On the **Choose a connection to a data source** page, select a data source that is type **SQL Server**.</span></span> <span data-ttu-id="77e76-144">請從清單中選取資料來源，或者瀏覽到報表伺服器再進行選取。</span><span class="sxs-lookup"><span data-stu-id="77e76-144">Select a data source from the list or browse to the report server to select one.</span></span>  
  
8.  <span data-ttu-id="77e76-145">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="77e76-145">Click **Next**.</span></span>  
  
9. <span data-ttu-id="77e76-146">在 **[設計查詢]** 頁面上，按一下 **[當成文字編輯]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-146">On the **Design a query** page, click **Edit as Text**.</span></span>  
  
10. <span data-ttu-id="77e76-147">將下列查詢貼入查詢窗格中：</span><span class="sxs-lookup"><span data-stu-id="77e76-147">Paste the following query into the query pane:</span></span>  
  
    ```  
    ;WITH CTE (StoreID, Subcategory, Quantity)   
    AS (  
    SELECT 200 AS StoreID, 'Digital SLR Cameras' AS Subcategory, 2002 AS Quantity  
    UNION SELECT  200 AS StoreID, 'Camcorders' AS Subcategory, 1954 AS Quantity  
    UNION SELECT  200 AS StoreID, 'Accessories' AS Subcategory, 1895 AS Quantity  
    UNION SELECT  199 AS StoreID, 'Digital Cameras' AS Subcategory, 1849 AS Quantity  
    UNION SELECT  306 AS StoreID, 'Digital SLR Cameras' AS Subcategory, 1579 AS Quantity  
    UNION SELECT  306 AS StoreID, 'Camcorders' AS Subcategory, 1561 AS Quantity  
    UNION SELECT  306 AS StoreID, 'Digital Cameras' AS Subcategory, 1553 AS Quantity  
    UNION SELECT  306 AS StoreID, 'Accessories' AS Subcategory, 1534 AS Quantity  
    UNION SELECT 307 AS StoreID, 'Accessories' AS Subcategory, 1755 AS Quantity  
    UNION SELECT 307 AS StoreID, 'Camcorders' AS Subcategory, 1631 AS Quantity  
    UNION SELECT 307 AS StoreID, 'Digital SLR Cameras' AS Subcategory, 1772 AS Quantity)  
    SELECT StoreID, Subcategory, Quantity  
    FROM CTE  
    ```  
  
     <span data-ttu-id="77e76-148">此查詢會將數個 [!INCLUDE[tsql](../includes/tsql-md.md)] SELECT 陳述式的結果結合在一個通用資料表運算式內，來指定以 Contoso 範例資料庫中簡化之資料為基礎的值。</span><span class="sxs-lookup"><span data-stu-id="77e76-148">This query combines the results of several [!INCLUDE[tsql](../includes/tsql-md.md)] SELECT statements inside a common table expression to specify values that are based on simplified data from the Contoso sample database.</span></span> <span data-ttu-id="77e76-149">Contoso 銷售資料表示客戶商品的全球銷售資料。</span><span class="sxs-lookup"><span data-stu-id="77e76-149">The Contoso sales data represents international sales data for consumer goods.</span></span> <span data-ttu-id="77e76-150">本教學課程會使用相機的銷售資料。</span><span class="sxs-lookup"><span data-stu-id="77e76-150">This tutorial uses sales data for cameras.</span></span> <span data-ttu-id="77e76-151">其中的子類別有數位相機、數位單眼反光式 (SLR) 相機、攝錄影機與相關配件。</span><span class="sxs-lookup"><span data-stu-id="77e76-151">The subcategories represent digital cameras, digital single lens reflex (SLR) cameras, camcorders, and accessories.</span></span>  
  
     <span data-ttu-id="77e76-152">查詢所指定的資料行名稱包含商店識別碼、銷售項目類別，以及三個商店之銷售訂單中所訂購的數量。</span><span class="sxs-lookup"><span data-stu-id="77e76-152">The query specifies column names that include a store identifier, a sales item subcategory, and the quantity ordered for sales orders from three stores.</span></span> <span data-ttu-id="77e76-153">在這個查詢中，商店名稱並不屬於結果集的內容。</span><span class="sxs-lookup"><span data-stu-id="77e76-153">In this query, the store name is not part of the result set.</span></span> <span data-ttu-id="77e76-154">稍後在本教學課程中，您會利用個別資料集查詢對應於商店識別碼的商店名稱。</span><span class="sxs-lookup"><span data-stu-id="77e76-154">Later in this tutorial, you will look up the name of the store that corresponds to the store identifier from a separate dataset.</span></span>  
  
     <span data-ttu-id="77e76-155">此查詢並不包含查詢參數。</span><span class="sxs-lookup"><span data-stu-id="77e76-155">This query does not contain query parameters.</span></span> <span data-ttu-id="77e76-156">您稍後將在本教學課程中加入參數。</span><span class="sxs-lookup"><span data-stu-id="77e76-156">You will add query parameters later in this tutorial.</span></span>  
  
11. <span data-ttu-id="77e76-157">在 [查詢設計工具] 工具列上，按一下 [**執行**] (**！**) 。</span><span class="sxs-lookup"><span data-stu-id="77e76-157">On the query designer toolbar, click **Run** (**!**).</span></span> <span data-ttu-id="77e76-158">結果集會顯示 11 個資料列，這些資料列會顯示四間商店中每個子類別所銷售的項目數量，並包含下列資料行：StoreID、Subcategory、Quantity。</span><span class="sxs-lookup"><span data-stu-id="77e76-158">The result set displays 11 rows of data that show the quantity of items sold for each subcategory for four stores, and includes the following columns: StoreID, Subcategory, Quantity.</span></span>  
  
12. <span data-ttu-id="77e76-159">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="77e76-159">Click **Next**.</span></span>  
  
##  <a name="2-organize-data-choose-layout-and-style-from-the-table-or-matrix-wizard"></a><a name="CompleteWizard"></a><span data-ttu-id="77e76-160">2. 從資料表或矩陣 Wizard 組織資料、選擇配置和樣式</span><span class="sxs-lookup"><span data-stu-id="77e76-160">2. Organize Data, Choose Layout, and Style from the Table or Matrix Wizard</span></span>  
 <span data-ttu-id="77e76-161">使用精靈提供起始設計來顯示資料。</span><span class="sxs-lookup"><span data-stu-id="77e76-161">Use the wizard to provide a starting design on which to display data.</span></span> <span data-ttu-id="77e76-162">精靈中的預覽窗格可協助您在完成資料表或矩陣設計之前，先視覺化群組資料的結果。</span><span class="sxs-lookup"><span data-stu-id="77e76-162">The preview pane in the wizard helps you to visualize the result of grouping data before you complete the table or matrix design.</span></span>  
  
#### <a name="to-organize-data-into-groups"></a><span data-ttu-id="77e76-163">若要將資料組織為群組</span><span class="sxs-lookup"><span data-stu-id="77e76-163">To organize data into groups</span></span>  
  
1.  <span data-ttu-id="77e76-164">在 [排列欄位]\*\*\*\* 頁面上，將 [Subcategory] 拖曳至 [資料列群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77e76-164">On the **Arrange fields** page, drag Subcategory to **Row groups**.</span></span>  
  
2.  <span data-ttu-id="77e76-165">將 [StoreID] 拖曳至 [資料行群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77e76-165">Drag StoreID to **Column groups**.</span></span>  
  
3.  <span data-ttu-id="77e76-166">將 [Quantity] 拖曳至 [值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77e76-166">Drag Quantity to **Values**.</span></span>  
  
     <span data-ttu-id="77e76-167">現在，您已經按照子類別的分組，以資料列組織銷售量的值。</span><span class="sxs-lookup"><span data-stu-id="77e76-167">You have organized the quantity sold values in rows grouped by subcategory.</span></span> <span data-ttu-id="77e76-168">每一間商店都會有一個資料行。</span><span class="sxs-lookup"><span data-stu-id="77e76-168">There will be one column for each store.</span></span>  
  
4.  <span data-ttu-id="77e76-169">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="77e76-169">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="77e76-170">在 **[選擇配置]** 頁面的 **[選項]** 下方，確定已經選取 **[顯示小計和總計]** 。</span><span class="sxs-lookup"><span data-stu-id="77e76-170">On the **Choose a Layout** page, under **Options**, verify that **Show subtotals and grand totals** is selected.</span></span>  
  
     <span data-ttu-id="77e76-171">當您執行報表時，最後一個資料行將會顯示所有商店之每個子類別的總數量，而最後一個資料列則會顯示每家商店之所有子類別的總數量。</span><span class="sxs-lookup"><span data-stu-id="77e76-171">When you run the report, the last column will show the total quantity of each subcategory for all stores, and the last row will show the total quantity for all subcategories for each store.</span></span>  
  
6.  <span data-ttu-id="77e76-172">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="77e76-172">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="77e76-173">在 [**選擇樣式**] 頁面的 [樣式] 窗格中，選取樣式。</span><span class="sxs-lookup"><span data-stu-id="77e76-173">On the **Choose a Style** page, in the Styles pane, select a style.</span></span>  
  
8.  <span data-ttu-id="77e76-174">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="77e76-174">Click **Finish**.</span></span>  
  
     <span data-ttu-id="77e76-175">矩陣會加入至設計介面。</span><span class="sxs-lookup"><span data-stu-id="77e76-175">The matrix is added to the design surface.</span></span> <span data-ttu-id="77e76-176">此矩陣會顯示 3 個資料行和 3 個資料列。</span><span class="sxs-lookup"><span data-stu-id="77e76-176">The matrix displays three columns and three rows.</span></span> <span data-ttu-id="77e76-177">第一個資料列的資料格內容為 Subcategory、StoreID 和 Total。</span><span class="sxs-lookup"><span data-stu-id="77e76-177">The contents of the cells in the first row are Subcategory, [StoreID], and Total.</span></span> <span data-ttu-id="77e76-178">第二個資料列的資料格內容包含多個運算式，分別表示子類別、每家商店所售出的項目數量以及所有商店之每個子類別的數量總計。</span><span class="sxs-lookup"><span data-stu-id="77e76-178">The contents of the cells in the second row contain expressions that represent the subcategory, the quantity of items sold for each store, and the total quantity for each subcategory for all stores.</span></span> <span data-ttu-id="77e76-179">最後一個資料列的資料格顯示每家商店的銷售總額。</span><span class="sxs-lookup"><span data-stu-id="77e76-179">The cells in the final row display the grand total for each store.</span></span>  
  
9. <span data-ttu-id="77e76-180">按一下矩陣內部，將滑鼠停留在第一個資料行的邊緣，抓取控點並且擴展資料行寬度。</span><span class="sxs-lookup"><span data-stu-id="77e76-180">Click in the matrix, hover over the edge of the first column, grab the handle, and expand the column width.</span></span>  
  
10. <span data-ttu-id="77e76-181">按一下 **[執行]** 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="77e76-181">Click **Run** to preview the report.</span></span>  
  
 <span data-ttu-id="77e76-182">報表就會在報表伺服器上執行，並且顯示標題以及進行報表處理的時間。</span><span class="sxs-lookup"><span data-stu-id="77e76-182">The report runs on the report server and displays the title and the time the report processing occurred.</span></span>  
  
 <span data-ttu-id="77e76-183">在這個案例中，資料行標題顯示的商店識別碼而非商店名稱。</span><span class="sxs-lookup"><span data-stu-id="77e76-183">In this scenario, the column headings display the store identifier but not the store name.</span></span> <span data-ttu-id="77e76-184">稍後，您會加入運算式，在包含商店識別碼/商店名稱組的資料集中，查詢商店名稱。</span><span class="sxs-lookup"><span data-stu-id="77e76-184">Later, you will add an expression to look up the store name in a dataset that contains store identifier/store name pairs.</span></span>  
  
##  <a name="3-add-a-query-parameter-to-create-a-report-parameter"></a><a name="Query"></a><span data-ttu-id="77e76-185">3. 加入查詢參數來建立報表參數</span><span class="sxs-lookup"><span data-stu-id="77e76-185">3. Add a Query Parameter to Create a Report Parameter</span></span>  
 <span data-ttu-id="77e76-186">當您將查詢參數加入至查詢時，報表產生器會自動建立一個單一值報表參數，其中包含名稱、提示與資料類型的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="77e76-186">When you add a query parameter to a query, Report Builder automatically creates a single-valued report parameter with default properties for name, prompt, and data type.</span></span>  
  
#### <a name="to-add-a-query-parameter"></a><span data-ttu-id="77e76-187">若要加入查詢參數</span><span class="sxs-lookup"><span data-stu-id="77e76-187">To add a query parameter</span></span>  
  
1.  <span data-ttu-id="77e76-188">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="77e76-188">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="77e76-189">在 [報表資料] 窗格中，展開 [資料集]\*\*\*\* 資料夾，並以滑鼠右鍵按一下 **DataSet1**，然後按一下 [查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77e76-189">In the Report Data pane, expand the **Datasets** folder, right-click **DataSet1**, and then click **Query**.</span></span>  
  
3.  <span data-ttu-id="77e76-190">新增下列 [!INCLUDE[tsql](../includes/tsql-md.md)] `WHERE` 子句做為查詢中的最後一行：</span><span class="sxs-lookup"><span data-stu-id="77e76-190">Add the following [!INCLUDE[tsql](../includes/tsql-md.md)] `WHERE` clause as the last line in the query:</span></span>  
  
    ```  
    WHERE StoreID = (@StoreID)  
    ```  
  
     <span data-ttu-id="77e76-191">`WHERE`子句會將抓取的資料限制為查詢參數所指定的存放區識別碼 *@StoreID* 。</span><span class="sxs-lookup"><span data-stu-id="77e76-191">The `WHERE` clause limits the retrieved data to the store identifier that is specified by the query parameter *@StoreID*.</span></span>  
  
4.  <span data-ttu-id="77e76-192">在 [查詢設計工具] 工具列上，按一下 [**執行**] (**！**) 。</span><span class="sxs-lookup"><span data-stu-id="77e76-192">On the query designer toolbar, click **Run** (**!**).</span></span> <span data-ttu-id="77e76-193">**定義查詢參數**] 對話方塊隨即開啟，並且提示您輸入查詢參數的值*@StoreID*。</span><span class="sxs-lookup"><span data-stu-id="77e76-193">The **Define Query Parameters** dialog box opens and prompts for a value for the query parameter *@StoreID*.</span></span>  
  
5.  <span data-ttu-id="77e76-194">在 **[參數值]** 中，輸入 **200**。</span><span class="sxs-lookup"><span data-stu-id="77e76-194">In **Parameter Value**, type **200**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="77e76-195">結果集會針對商店識別碼 **200**顯示 Accessories、Camcorders 與 Digital SLR Cameras 售出的數量。</span><span class="sxs-lookup"><span data-stu-id="77e76-195">The result set displays the quantities sold for Accessories, Camcorders, and Digital SLR Cameras for the store identifier **200**.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="77e76-196">在 [報表資料] 窗格中，展開 **[參數]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="77e76-196">In the Report Data pane, expand the **Parameters** folder.</span></span>  
  
 <span data-ttu-id="77e76-197">請注意，現在有一個名為的報表參數 *@StoreID* 。</span><span class="sxs-lookup"><span data-stu-id="77e76-197">Notice that there is now a report parameter named *@StoreID*.</span></span> <span data-ttu-id="77e76-198">根據預設，參數的資料類型為 **[文字]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-198">By default, the parameter has data type **Text**.</span></span> <span data-ttu-id="77e76-199">由於商店識別碼是一個整數，所以在下一個步驟中，您會將資料類型變更為 Integer。</span><span class="sxs-lookup"><span data-stu-id="77e76-199">Because the store identifier is an integer, you will change the data type to Integer in the next procedure.</span></span>  
  
##  <a name="4-change-default-data-type-and-other-properties-for-a-report-parameter"></a><a name="ChangeDefaultProperties"></a><span data-ttu-id="77e76-200">4. 變更報表參數的預設資料類型和其他屬性</span><span class="sxs-lookup"><span data-stu-id="77e76-200">4. Change Default Data Type and Other Properties for a Report Parameter</span></span>  
 <span data-ttu-id="77e76-201">建立報表參數之後，您可以調整屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="77e76-201">After a report parameter is created, you can adjust the default values for properties.</span></span>  
  
#### <a name="to-change-the-default-data-type-for-a-report-parameter"></a><span data-ttu-id="77e76-202">若要變更報表參數的預設資料類型</span><span class="sxs-lookup"><span data-stu-id="77e76-202">To change the default data type for a report parameter</span></span>  
  
1.  <span data-ttu-id="77e76-203">在 [報表資料] 窗格的 [**參數**] 節點下，以滑鼠右鍵按一下 *@StoreID* ，然後按一下 [**參數屬性**]。</span><span class="sxs-lookup"><span data-stu-id="77e76-203">In the Report Data pane under the **Parameters** node, right-click *@StoreID*, and then click **Parameter Properties**.</span></span>  
  
2.  <span data-ttu-id="77e76-204">在 [提示] 中輸入 **商店識別碼？**</span><span class="sxs-lookup"><span data-stu-id="77e76-204">In Prompt, type **Store identifier?**</span></span> <span data-ttu-id="77e76-205">。當您執行報表時，此文字會出現在報表檢視器工具列上。</span><span class="sxs-lookup"><span data-stu-id="77e76-205">This text appears on the report viewer toolbar when you run the report.</span></span>  
  
3.  <span data-ttu-id="77e76-206">在 **[資料類型]** 的下拉式清單中，選取 **[整數]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-206">In **Data type**, from the drop-down list, select **Integer**.</span></span>  
  
4.  <span data-ttu-id="77e76-207">接受對話方塊中其餘的預設值。</span><span class="sxs-lookup"><span data-stu-id="77e76-207">Accept the remaining default values in the dialog box.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="77e76-208">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="77e76-208">Preview the report.</span></span> <span data-ttu-id="77e76-209">報表檢視器會顯示的提示 *@StoreID* 。</span><span class="sxs-lookup"><span data-stu-id="77e76-209">The report viewer displays the prompt for *@StoreID*.</span></span>  
  
7.  <span data-ttu-id="77e76-210">在報表檢視器工具列上，就在 Store ID 旁，輸入 **200**，然後按一下 **[檢視報表]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-210">On the report viewer toolbar, next to Store ID, type **200**, and then click **View Report**.</span></span>  
  
##  <a name="4a-add-a-dataset-to-provide-available-values-and-display-names"></a><a name="AddDataset"></a><span data-ttu-id="77e76-211">4a.</span><span class="sxs-lookup"><span data-stu-id="77e76-211">4a.</span></span> <span data-ttu-id="77e76-212">加入資料集來提供可用值與顯示名稱</span><span class="sxs-lookup"><span data-stu-id="77e76-212">Add a Dataset to Provide Available Values and Display Names</span></span>  
 <span data-ttu-id="77e76-213">為了確保使用者只會輸入有效的參數值，您可以建立列出多個值的下拉式清單，供使用者選擇。</span><span class="sxs-lookup"><span data-stu-id="77e76-213">To ensure a user can type only valid values for a parameter, you can create a drop-down list of values to choose from.</span></span> <span data-ttu-id="77e76-214">這些值可以取自資料集或是根據您另外指定的清單。</span><span class="sxs-lookup"><span data-stu-id="77e76-214">The values can come from a dataset or from a list that you specify.</span></span> <span data-ttu-id="77e76-215">可用的值必須透過資料集提供，且該資料集具有不含參數參考的查詢。</span><span class="sxs-lookup"><span data-stu-id="77e76-215">Available values must be supplied from a dataset that has a query that does not contain a reference to the parameter.</span></span>  
  
#### <a name="to-create-a-dataset-for-valid-values-for-a-parameter"></a><span data-ttu-id="77e76-216">建立資料集以提供有效的參數值</span><span class="sxs-lookup"><span data-stu-id="77e76-216">To create a dataset for valid values for a parameter</span></span>  
  
1.  <span data-ttu-id="77e76-217">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="77e76-217">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="77e76-218">在 [報表資料] 窗格中，以滑鼠右鍵按一下 [資料集]\*\*\*\* 資料夾，然後按一下 [加入資料集]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77e76-218">In the Report Data pane, right-click the **Datasets** folder, and then click **Add Dataset**.</span></span>  
  
3.  <span data-ttu-id="77e76-219">在 **[名稱]** 中輸入 **Stores**。</span><span class="sxs-lookup"><span data-stu-id="77e76-219">In **Name**, type **Stores**.</span></span>  
  
4.  <span data-ttu-id="77e76-220">選取 **[在報表中使用內嵌資料集]** 選項。</span><span class="sxs-lookup"><span data-stu-id="77e76-220">Select the **Use a dataset embedded in my report** option.</span></span>  
  
5.  <span data-ttu-id="77e76-221">在 **[資料來源]** 中，從下拉式清單選擇您於第一個步驟中建立的資料集。</span><span class="sxs-lookup"><span data-stu-id="77e76-221">In **Data source**, from the drop-down list, choose the data source you created in the first procedure.</span></span>  
  
6.  <span data-ttu-id="77e76-222">在 **[查詢類型]** 中，確認已選取 **[文字]** 。</span><span class="sxs-lookup"><span data-stu-id="77e76-222">In **Query type**, verify that **Text** is selected.</span></span>  
  
7.  <span data-ttu-id="77e76-223">在 **[查詢]** 中，貼上下列文字：</span><span class="sxs-lookup"><span data-stu-id="77e76-223">In **Query**, paste the following text:</span></span>  
  
    ```  
    SELECT 200 AS StoreID, 'Contoso Catalog Store' as StoreName  
    UNION SELECT 199 AS StoreID, 'Contoso North America Online Store' as StoreName  
    UNION SELECT 307 AS StoreID, 'Contoso Asia Online Store' as StoreName  
    UNION SELECT 306 AS StoreID, 'Contoso Europe Online Store' as StoreName  
    ```  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="77e76-224">[報表資料] 窗格會在 **Stores** 資料集節點下顯示 StoreID 和 StoreName 欄位。</span><span class="sxs-lookup"><span data-stu-id="77e76-224">The Report Data pane displays the fields StoreID and StoreName under the **Stores** dataset node.</span></span>  
  
##  <a name="4b-specify-available-values-to-create-a-drop-down-list-of-values"></a><a name="AvailableValues"></a><span data-ttu-id="77e76-225">4b.</span><span class="sxs-lookup"><span data-stu-id="77e76-225">4b.</span></span> <span data-ttu-id="77e76-226">指定可以用於建立多個值之下拉式清單的值</span><span class="sxs-lookup"><span data-stu-id="77e76-226">Specify Available Values to Create a Drop-down List of Values</span></span>  
 <span data-ttu-id="77e76-227">建立資料集來提供可用的值之後，您必須變更報表屬性，以指定要用於填入 ReportViewer 工具列中有效下拉式清單值的資料集與欄位。</span><span class="sxs-lookup"><span data-stu-id="77e76-227">After you create a dataset to provide available values, you must change the report properties to specify which dataset and which field to use to populate the drop-down list of valid values on the reportviewer toolbar.</span></span>  
  
#### <a name="to-provide-available-values-for-a-parameter-from-a-dataset"></a><span data-ttu-id="77e76-228">若要從資料集提供可用的參數值</span><span class="sxs-lookup"><span data-stu-id="77e76-228">To provide available values for a parameter from a dataset</span></span>  
  
1.  <span data-ttu-id="77e76-229">在 [報表資料] 窗格中，以滑鼠右鍵按一下參數 *@StoreID* ，然後按一下 [**參數屬性**]。</span><span class="sxs-lookup"><span data-stu-id="77e76-229">In the Report Data pane, right-click the parameter *@StoreID*, and then click **Parameter Properties**.</span></span>  
  
2.  <span data-ttu-id="77e76-230">按一下 **[可用的值]**，然後按一下 **[從查詢取得值]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-230">Click **Available Values**, and then click **Get values from a query**.</span></span>  
  
3.  <span data-ttu-id="77e76-231">在 [資料集]\*\*\*\* 的下拉式清單中，按一下 [Stores]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77e76-231">In **Dataset**, from the drop-down list, click **Stores**.</span></span>  
  
4.  <span data-ttu-id="77e76-232">在 [值欄位]\*\*\*\* 的下拉式清單中，按一下 [StoreID]。</span><span class="sxs-lookup"><span data-stu-id="77e76-232">In **Value field**, from the drop-down list, click StoreID.</span></span>  
  
5.  <span data-ttu-id="77e76-233">從 [標籤欄位]\*\*\*\* 的下拉式清單中，按一下 StoreName。</span><span class="sxs-lookup"><span data-stu-id="77e76-233">In **Label field**, from the drop-down list, click StoreName.</span></span> <span data-ttu-id="77e76-234">標籤欄位會指定值的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="77e76-234">The label field specifies the display name for the value.</span></span>  
  
6.  <span data-ttu-id="77e76-235">按一下 [一般]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77e76-235">Click **General**.</span></span>  
  
7.  <span data-ttu-id="77e76-236">在 [提示] 中輸入 **商店名稱？**。</span><span class="sxs-lookup"><span data-stu-id="77e76-236">In Prompt, type **Store name?**</span></span>  
  
     <span data-ttu-id="77e76-237">使用現在會從商店名稱的清單中選取，而非從商店識別碼的清單中選取。</span><span class="sxs-lookup"><span data-stu-id="77e76-237">The user will now select from a list of store names instead of store identifiers.</span></span> <span data-ttu-id="77e76-238">請注意，參數資料類型仍為 **[整數]** ，因為參數是根據商店識別項而不是商店名稱。</span><span class="sxs-lookup"><span data-stu-id="77e76-238">Note that the parameter data type remains **Integer** because the parameter is based on the store identifier, not the store name.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
9. <span data-ttu-id="77e76-239">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="77e76-239">Preview the report.</span></span>  
  
     <span data-ttu-id="77e76-240">在報表檢視器工具列中，參數文字方塊現在是顯示的下拉式清單 **\<Select a Value>** 。</span><span class="sxs-lookup"><span data-stu-id="77e76-240">In the report viewer toolbar, the parameter text box is now a drop-down list that displays **\<Select a Value>**.</span></span>  
  
10. <span data-ttu-id="77e76-241">從下拉式清單中選取 Contoso Catalog Store，然後按一下 **[檢視報表]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-241">From the drop-down list, select Contoso Catalog Store, and then click **View Report**.</span></span>  
  
 <span data-ttu-id="77e76-242">報表會針對商店識別碼 **200**顯示 Accessories、Camcorders 與 Digital SLR Cameras 售出的數量。</span><span class="sxs-lookup"><span data-stu-id="77e76-242">The report displays the quantity sold for Accessories, Camcorders, and Digital SLR Cameras for the store identifier **200**.</span></span>  
  
##  <a name="4c-specify-default-values-so-the-report-runs-automatically"></a><a name="DefaultValues"></a><span data-ttu-id="77e76-243">4c.</span><span class="sxs-lookup"><span data-stu-id="77e76-243">4c.</span></span> <span data-ttu-id="77e76-244">指定預設值讓報表能夠自動執行</span><span class="sxs-lookup"><span data-stu-id="77e76-244">Specify Default Values so the Report Runs Automatically</span></span>  
 <span data-ttu-id="77e76-245">您可以指定每一個參數的預設值，讓報表能夠自動執行。</span><span class="sxs-lookup"><span data-stu-id="77e76-245">You can specify a default value for each parameter so the report runs automatically.</span></span>  
  
#### <a name="to-specify-a-default-value-from-a-dataset"></a><span data-ttu-id="77e76-246">若要從資料集指定預設值</span><span class="sxs-lookup"><span data-stu-id="77e76-246">To specify a default value from a dataset</span></span>  
  
1.  <span data-ttu-id="77e76-247">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="77e76-247">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="77e76-248">在 [報表資料] 窗格中，以滑鼠右鍵按一下 [] *@StoreID* ，然後按一下 [**參數屬性**]。</span><span class="sxs-lookup"><span data-stu-id="77e76-248">In the Report Data pane, right-click *@StoreID*, and then click **Parameter Properties**.</span></span>  
  
3.  <span data-ttu-id="77e76-249">按一下 **[預設值]**，然後按一下 **[從查詢取得值]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-249">Click **Default Values**, and then click **Get values from a query**.</span></span>  
  
4.  <span data-ttu-id="77e76-250">在 [資料集]\*\*\*\* 的下拉式清單中，按一下 [Stores]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77e76-250">In **Dataset**, from the drop-down list, click **Stores**.</span></span>  
  
5.  <span data-ttu-id="77e76-251">在 [值欄位]\*\*\*\* 的下拉式清單中，按一下 [StoreID]。</span><span class="sxs-lookup"><span data-stu-id="77e76-251">In **Value field**, from the drop-down list, click StoreID.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="77e76-252">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="77e76-252">Preview the report.</span></span>  
  
 <span data-ttu-id="77e76-253">若是 *@StoreID* ，報表檢視器會顯示值 "Contoso 北美洲 Online Store"。</span><span class="sxs-lookup"><span data-stu-id="77e76-253">For *@StoreID*, the report viewer displays the value "Contoso North America Online Store".</span></span> <span data-ttu-id="77e76-254">這是來自資料集 **Stores**中結果集的第一個值。</span><span class="sxs-lookup"><span data-stu-id="77e76-254">This is the first value from the result set for the dataset **Stores**.</span></span> <span data-ttu-id="77e76-255">報表會針對商店識別碼 **199**顯示  Digital Cameras 售出的數量。</span><span class="sxs-lookup"><span data-stu-id="77e76-255">The report displays the quantity sold for Digital Cameras for store identifier **199**.</span></span>  
  
#### <a name="to-specify-a-custom-default-value"></a><span data-ttu-id="77e76-256">若要指定自訂預設值</span><span class="sxs-lookup"><span data-stu-id="77e76-256">To specify a custom default value</span></span>  
  
1.  <span data-ttu-id="77e76-257">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="77e76-257">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="77e76-258">在 [報表資料] 窗格中，以滑鼠右鍵按一下 [] *@StoreID* ，然後按一下 [**參數屬性**]。</span><span class="sxs-lookup"><span data-stu-id="77e76-258">In the Report Data pane, right-click *@StoreID*, and then click **Parameter Properties**.</span></span>  
  
3.  <span data-ttu-id="77e76-259">按一下 **[預設值]**，再按一下 **[指定值]**，然後按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-259">Click **Default Values**, and click **Specify values**, and then click **Add**.</span></span> <span data-ttu-id="77e76-260">新的值資料列隨即加入。</span><span class="sxs-lookup"><span data-stu-id="77e76-260">A new value row is added.</span></span>  
  
4.  <span data-ttu-id="77e76-261">在 [ **值**] 中，輸入 **200**。</span><span class="sxs-lookup"><span data-stu-id="77e76-261">In **Value**, type **200**.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="77e76-262">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="77e76-262">Preview the report.</span></span>  
  
 <span data-ttu-id="77e76-263">對於 *@StoreID* ，報表檢視器會顯示值 "Contoso Catalog Store"。</span><span class="sxs-lookup"><span data-stu-id="77e76-263">For *@StoreID*, the report viewer displays the value "Contoso Catalog Store".</span></span> <span data-ttu-id="77e76-264">這是商店識別碼 **200**的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="77e76-264">This is the display name for store identifier **200**.</span></span> <span data-ttu-id="77e76-265">報表會針對商店識別碼 **200**顯示 Accessories、Camcorders 與 Digital SLR Cameras 售出的數量。</span><span class="sxs-lookup"><span data-stu-id="77e76-265">The report displays the quantity sold for Accessories, Camcorders, and Digital SLR Cameras for the store identifier **200**.</span></span>  
  
##  <a name="4d-look-up-a-value-from-a-dataset-that-has-namevalue-pairs"></a><a name="NameValue"></a><span data-ttu-id="77e76-266">4d.</span><span class="sxs-lookup"><span data-stu-id="77e76-266">4d.</span></span> <span data-ttu-id="77e76-267">從具有名稱/值組的資料集中查閱值</span><span class="sxs-lookup"><span data-stu-id="77e76-267">Look up a Value from a Dataset that has Name/Value Pairs</span></span>  
 <span data-ttu-id="77e76-268">資料集可能同時包含識別碼與對應的名稱欄位。</span><span class="sxs-lookup"><span data-stu-id="77e76-268">A dataset might contain both the identifier and the corresponding name field.</span></span> <span data-ttu-id="77e76-269">如果您只有識別碼，那麼可以查詢包含名稱/值組之資料集 (您先前建立) 中的對應名稱。</span><span class="sxs-lookup"><span data-stu-id="77e76-269">When you only have an identifier, you can look up the corresponding name in a dataset that you created that includes name/value pairs.</span></span>  
  
#### <a name="to-look-up-a-value-from-a-dataset"></a><span data-ttu-id="77e76-270">若要從資料集查詢值</span><span class="sxs-lookup"><span data-stu-id="77e76-270">To look up a value from a dataset</span></span>  
  
1.  <span data-ttu-id="77e76-271">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="77e76-271">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="77e76-272">在設計介面的矩陣中，即第一個資料列欄標題中，以滑鼠右鍵按一下 `[StoreID]`，然後按一下 [運算式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77e76-272">On the design surface, in the matrix, in the first row column header, right-click `[StoreID]` and then click **Expression**.</span></span>  
  
3.  <span data-ttu-id="77e76-273">在運算式窗格中，刪除所有文字，但是保留開頭的 `equals` (=)。</span><span class="sxs-lookup"><span data-stu-id="77e76-273">In the expression pane, delete all text except the beginning `equals` (=).</span></span>  
  
4.  <span data-ttu-id="77e76-274">在 **[類別目錄]** 中，展開 **[一般函數]**，再按一下 **[其他]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-274">In **Category**, expand **Common Functions**, and click **Miscellaneous**.</span></span> <span data-ttu-id="77e76-275">[項目] 窗格顯示函數集。</span><span class="sxs-lookup"><span data-stu-id="77e76-275">The Item pane displays a set of functions.</span></span>  
  
5.  <span data-ttu-id="77e76-276">在 [項目] 中，按兩下 **[查詢]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-276">In Item, double-click **Lookup**.</span></span> <span data-ttu-id="77e76-277">運算式窗格會顯示 `=Lookup(`。</span><span class="sxs-lookup"><span data-stu-id="77e76-277">The expression pane displays `=Lookup(`.</span></span> <span data-ttu-id="77e76-278">[範例] 窗格會示 Lookup 語法的範例。</span><span class="sxs-lookup"><span data-stu-id="77e76-278">The Example pane displays an example of Lookup syntax.</span></span>  
  
6.  <span data-ttu-id="77e76-279">輸入下列運算式： `=Lookup(Fields!StoreID.Value,Fields!StoreID.Value,Fields!StoreName.Value,"Stores")`</span><span class="sxs-lookup"><span data-stu-id="77e76-279">Type the following expression: `=Lookup(Fields!StoreID.Value,Fields!StoreID.Value,Fields!StoreName.Value,"Stores")`</span></span>  
  
     <span data-ttu-id="77e76-280">Lookup 函數會接受 StoreID 值並在 "Stores" 資料集中尋找該值，然後再傳回 StoreName 值。</span><span class="sxs-lookup"><span data-stu-id="77e76-280">The Lookup function takes the value for StoreID, looks it up in the "Stores" dataset, and returns the StoreName value.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="77e76-281">[存放區] 資料行標題包含複雜運算式的顯示文字： **<\<Expr>>** 。</span><span class="sxs-lookup"><span data-stu-id="77e76-281">The store column header contains the display text for a complex expression: **<\<Expr>>**.</span></span>  
  
8.  <span data-ttu-id="77e76-282">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="77e76-282">Preview the report.</span></span>  
  
 <span data-ttu-id="77e76-283">每一頁頂端的文字方塊會顯示商店名稱，而非商店識別碼。</span><span class="sxs-lookup"><span data-stu-id="77e76-283">The text box at the top of each page displays the store name instead of the store identifier.</span></span>  
  
##  <a name="5-display-the-selected-parameter-value-in-the-report"></a><a name="Expression"></a><span data-ttu-id="77e76-284">5. 在報表中顯示選取的參數值</span><span class="sxs-lookup"><span data-stu-id="77e76-284">5. Display the Selected Parameter Value in the Report</span></span>  
 <span data-ttu-id="77e76-285">如果使用者對報表有任何疑問，這有助於明白先前選擇了哪些參數值。</span><span class="sxs-lookup"><span data-stu-id="77e76-285">When a user has questions about a report, it helps to know which parameter values they chose.</span></span> <span data-ttu-id="77e76-286">您可以在報表中保留使用者為每一個參數所選取的值。</span><span class="sxs-lookup"><span data-stu-id="77e76-286">You can preserve user-selected values for each parameter in the report.</span></span> <span data-ttu-id="77e76-287">其中一個方法是在頁尾的文字方塊中顯示參數。</span><span class="sxs-lookup"><span data-stu-id="77e76-287">One way is to display the parameters in a text box in the page footer.</span></span>  
  
#### <a name="to-display-the-selected-parameter-value-and-label-on-a-page-footer"></a><span data-ttu-id="77e76-288">若要在頁尾中顯示選取的參數值與標籤</span><span class="sxs-lookup"><span data-stu-id="77e76-288">To display the selected parameter value and label on a page footer</span></span>  
  
1.  <span data-ttu-id="77e76-289">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="77e76-289">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="77e76-290">以滑鼠右鍵按一下頁尾，指向 **[插入]**，然後按一下 **[文字方塊]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-290">Right-click the page footer, point to **Insert**, and then click **Text Box**.</span></span> <span data-ttu-id="77e76-291">將文字方塊拖曳到具有時間戳記的文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="77e76-291">Drag the text box next to the text box with the time stamp.</span></span> <span data-ttu-id="77e76-292">抓取文字方塊的側邊控點，然後拉長寬度。</span><span class="sxs-lookup"><span data-stu-id="77e76-292">Grab the side handle of the text box and expand the width.</span></span>  
  
3.  <span data-ttu-id="77e76-293">從 [報表資料] 窗格中，將參數拖曳 *@StoreID* 至文字方塊。</span><span class="sxs-lookup"><span data-stu-id="77e76-293">From the Report Data pane, drag the parameter *@StoreID* to the text box.</span></span> <span data-ttu-id="77e76-294">此文字方塊便會顯示 `[@StoreID]`。</span><span class="sxs-lookup"><span data-stu-id="77e76-294">The text box displays `[@StoreID]`.</span></span>  
  
4.  <span data-ttu-id="77e76-295">若要顯示參數標籤，按一下文字方塊，直到插入游標出現在現有運算式之後，輸入一個空格，然後將參數的其他複本從 [報表資料] 窗格拖曳至文字方塊。</span><span class="sxs-lookup"><span data-stu-id="77e76-295">To display the parameter label, click in the text box until the insert cursor appears after the existing expression, type a space, and then drag another copy of the parameter from the Report Data pane to the text box.</span></span> <span data-ttu-id="77e76-296">此文字方塊便會顯示 `[@StoreID] [@StoreID]`。</span><span class="sxs-lookup"><span data-stu-id="77e76-296">The text box displays `[@StoreID] [@StoreID]`.</span></span>  
  
5.  <span data-ttu-id="77e76-297">以滑鼠右鍵按一下第一個運算式，然後按一下 **[運算式]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-297">Right-click the first expression and click **Expression**.</span></span> <span data-ttu-id="77e76-298">**[運算式]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="77e76-298">The **Expression** dialog box opens.</span></span> <span data-ttu-id="77e76-299">將文字 `Value` 取代為 `Label`。</span><span class="sxs-lookup"><span data-stu-id="77e76-299">Replace the text `Value` by `Label`.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="77e76-300">文字便會顯示 `[@StoreID.Label] [@StoreID]`。</span><span class="sxs-lookup"><span data-stu-id="77e76-300">The text displays: `[@StoreID.Label] [@StoreID]`.</span></span>  
  
7.  <span data-ttu-id="77e76-301">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="77e76-301">Preview the report.</span></span>  
  
##  <a name="6-use-the-report-parameter-in-a-filter"></a><a name="Filter"></a><span data-ttu-id="77e76-302">6. 在篩選中使用報表參數</span><span class="sxs-lookup"><span data-stu-id="77e76-302">6. Use the Report Parameter in a Filter</span></span>  
 <span data-ttu-id="77e76-303">篩選有助於控制在自外部資料來源擷取報表後，要在其中使用哪些資料。</span><span class="sxs-lookup"><span data-stu-id="77e76-303">Filters help control which data to use in a report after it is retrieved from an external data source.</span></span> <span data-ttu-id="77e76-304">若要協助使用者可以控制他們想要看的資料，您可以在矩陣的篩選中加入報表參數。</span><span class="sxs-lookup"><span data-stu-id="77e76-304">To let a user help control the data they want to see, you can include the report parameter in a filter for the matrix.</span></span>  
  
#### <a name="to-specify-a-parameter-in-a-matrix-filter"></a><span data-ttu-id="77e76-305">若要在矩陣篩選中指定參數</span><span class="sxs-lookup"><span data-stu-id="77e76-305">To specify a parameter in a matrix filter</span></span>  
  
1.  <span data-ttu-id="77e76-306">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="77e76-306">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="77e76-307">以滑鼠右鍵按一下矩陣上的資料行標頭控制代碼，然後按一下 **[Tablix 屬性]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-307">Right-click a row or column header handle on the matrix, and then click **Tablix Properties**.</span></span>  
  
3.  <span data-ttu-id="77e76-308">按一下 **[篩選]**，然後按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-308">Click **Filters**, and then click **Add**.</span></span> <span data-ttu-id="77e76-309">新的篩選資料列隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="77e76-309">A new filter row appears.</span></span>  
  
4.  <span data-ttu-id="77e76-310">在 [運算式]\*\*\*\* 的下拉式清單中，選取 StoreID 資料集欄位。</span><span class="sxs-lookup"><span data-stu-id="77e76-310">In **Expression**, from the drop-down list, select the dataset field StoreID.</span></span> <span data-ttu-id="77e76-311">資料類型會顯示 **[整數]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-311">The data type displays **Integer**.</span></span> <span data-ttu-id="77e76-312">當運算式值為資料集欄位時，會自動設定資料類型。</span><span class="sxs-lookup"><span data-stu-id="77e76-312">When the expression value is a dataset field, the data type is set automatically.</span></span>  
  
5.  <span data-ttu-id="77e76-313">在 [**運算子**] 中，確認 `equals` 已選取 [ (=) ]。</span><span class="sxs-lookup"><span data-stu-id="77e76-313">In **Operator**, verify that `equals` (=) is selected.</span></span>  
  
6.  <span data-ttu-id="77e76-314">在 **[值]** 中，輸入 `[@StoreID]`。</span><span class="sxs-lookup"><span data-stu-id="77e76-314">In **Value**, type `[@StoreID]`.</span></span> <span data-ttu-id="77e76-315">`[@StoreID]` 為表示 `=Parameters!StoreID.Value`的簡單運算式語法。</span><span class="sxs-lookup"><span data-stu-id="77e76-315">`[@StoreID]` is the simple expression syntax that represents `=Parameters!StoreID.Value`.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="77e76-316">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="77e76-316">Preview the report.</span></span>  
  
     <span data-ttu-id="77e76-317">矩陣只會顯示 "Contoso Catalog Store" 的資料。</span><span class="sxs-lookup"><span data-stu-id="77e76-317">The matrix displays data only for "Contoso Catalog Store".</span></span>  
  
9. <span data-ttu-id="77e76-318">在報表檢視器工具列上，為 **[Store name?]** 選取 **[Contoso Asia Online Store]**，然後按一下 **[檢視報表]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-318">On the report viewer toolbar, for **Store name?**, select **Contoso Asia Online Store**, and then click **View Report**.</span></span>  
  
 <span data-ttu-id="77e76-319">矩陣會顯示對應於您所選商店的資料。</span><span class="sxs-lookup"><span data-stu-id="77e76-319">The matrix displays data that corresponds to the store that you selected.</span></span>  
  
##  <a name="7-change-the-report-parameter-to-accept-multiple-values"></a><a name="Multivalued"></a><span data-ttu-id="77e76-320">7. 變更報表參數以接受多個值</span><span class="sxs-lookup"><span data-stu-id="77e76-320">7. Change the Report Parameter to Accept Multiple Values</span></span>  
 <span data-ttu-id="77e76-321">若要將參數由單一值變更為多重值，您必須變更查詢以及所有包含參數參考的所有運算式，包含篩選條件。</span><span class="sxs-lookup"><span data-stu-id="77e76-321">To change a parameter from single to multivalued, you must change the query, and all expressions that contain a reference to the parameter, including filters.</span></span> <span data-ttu-id="77e76-322">多重值參數為值的陣列。</span><span class="sxs-lookup"><span data-stu-id="77e76-322">A multivalued parameter is an array of values.</span></span> <span data-ttu-id="77e76-323">在資料集查詢中，查詢語法必須經過測試，確認值組中包含一個值。</span><span class="sxs-lookup"><span data-stu-id="77e76-323">In a dataset query, query syntax must test for inclusion of one value in a set of values.</span></span> <span data-ttu-id="77e76-324">在報表運算式中，運算式語法必須存取值的陣列，而不是單一值。</span><span class="sxs-lookup"><span data-stu-id="77e76-324">In a report expression, expression syntax must access an array of values instead of an individual value.</span></span>  
  
#### <a name="to-change-a-parameter-from-single-to-multivalued"></a><span data-ttu-id="77e76-325">將參數由單一值變更為多重值</span><span class="sxs-lookup"><span data-stu-id="77e76-325">To change a parameter from single to multivalued</span></span>  
  
1.  <span data-ttu-id="77e76-326">切換至 [設計] 檢視。</span><span class="sxs-lookup"><span data-stu-id="77e76-326">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="77e76-327">在 [報表資料] 窗格中，以滑鼠右鍵按一下 [] *@StoreID* ，然後按一下 [**參數屬性**]。</span><span class="sxs-lookup"><span data-stu-id="77e76-327">In the Report Data pane, right-click *@StoreID*, and then click **Parameter Properties**.</span></span>  
  
3.  <span data-ttu-id="77e76-328">選取 **[允許多個值]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-328">Select **Allow multiple values**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="77e76-329">在 [報表資料] 窗格中，展開 [資料集]\*\*\*\* 資料夾，並以滑鼠右鍵按一下 **DataSet1**，然後按一下 [查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77e76-329">In the Report Data pane, expand the **Datasets** folder, right-click **DataSet1**, and then click **Query**.</span></span>  
  
6.  <span data-ttu-id="77e76-330">在 `equals` `IN` [!INCLUDE[tsql](../includes/tsql-md.md)] 查詢中最後一行的子句中，將 (=) 變更為 `WHERE` ：</span><span class="sxs-lookup"><span data-stu-id="77e76-330">Change `equals` (=) to `IN` in the [!INCLUDE[tsql](../includes/tsql-md.md)] `WHERE` clause in the last line in the query:</span></span>  
  
    ```  
    WHERE StoreID IN (@StoreID)  
    ```  
  
     <span data-ttu-id="77e76-331">`IN` 運算子會測試一個值，確認已包含一組值。</span><span class="sxs-lookup"><span data-stu-id="77e76-331">The `IN` operator tests a value for inclusion in a set of values.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="77e76-332">以滑鼠右鍵按一下矩陣上的資料行標頭控制代碼，然後按一下 **[Tablix 屬性]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-332">Right-click a row or column header handle on the matrix, and then click **Tablix Properties**.</span></span>  
  
9. <span data-ttu-id="77e76-333">按一下 **[篩選]** 。</span><span class="sxs-lookup"><span data-stu-id="77e76-333">Click **Filters**.</span></span>  
  
10. <span data-ttu-id="77e76-334">在 **[運算子]** 中，選取 **[In]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-334">In **Operator**, select **In**.</span></span>  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. <span data-ttu-id="77e76-335">在顯示頁尾中參數的文字方塊中，刪除所有文字。</span><span class="sxs-lookup"><span data-stu-id="77e76-335">In the text box that displays the parameter in the page footer, delete all text.</span></span>  
  
13. <span data-ttu-id="77e76-336">以滑鼠右鍵按一下文字方塊，然後按一下 **[運算式]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-336">Right-click the text box, and then click **Expression**.</span></span> <span data-ttu-id="77e76-337">輸入下列運算式： `=Join(Parameters!StoreID.Label, ", ")`</span><span class="sxs-lookup"><span data-stu-id="77e76-337">Type the following expression: `=Join(Parameters!StoreID.Label, ", ")`</span></span>  
  
     <span data-ttu-id="77e76-338">這個運算式會串聯使用者選取的所有商店名稱。</span><span class="sxs-lookup"><span data-stu-id="77e76-338">This expression concatenates all store names that the user selected.</span></span>  
  
14. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
15. <span data-ttu-id="77e76-339">在您剛剛建立之運算式前面的文字方塊上按一下，然後輸入下列：選取的參數值：</span><span class="sxs-lookup"><span data-stu-id="77e76-339">Click in the text box in front of the expression that you just created, and then type the following: Parameter Values Selected:.</span></span>  
  
16. <span data-ttu-id="77e76-340">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="77e76-340">Preview the report.</span></span>  
  
17. <span data-ttu-id="77e76-341">按一下 [Store Name?] 旁的下拉式清單</span><span class="sxs-lookup"><span data-stu-id="77e76-341">Click the drop-down list next to Store Name?</span></span>  
  
     <span data-ttu-id="77e76-342">每一個有效值會顯示在核取方塊旁。</span><span class="sxs-lookup"><span data-stu-id="77e76-342">Each valid value appears next to a check box.</span></span>  
  
18. <span data-ttu-id="77e76-343">按一下 **[全選]**，然後按一下 **[檢視報表]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-343">Click **Select All**, and then click **View Report**.</span></span>  
  
     <span data-ttu-id="77e76-344">報表會示所有商店中所有子類別的出售數量。</span><span class="sxs-lookup"><span data-stu-id="77e76-344">The report displays the quantity sold for all subcategories for all stores.</span></span>  
  
19. <span data-ttu-id="77e76-345">從下拉式清單中，按一下 [全選]\*\*\*\* 清除清單，並按一下 [Contoso Catalog Store] 與 [Contoso Asia Online Store]，然後按一下 [檢視報表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77e76-345">From the drop-down list, click **Select All** to clear the list, click "Contoso Catalog Store" and "Contoso Asia Online Store", and then click **View Report**.</span></span>  
  
##  <a name="8-add-a-boolean-parameter-for-conditional-visibility"></a><a name="Boolean"></a><span data-ttu-id="77e76-346">8. 加入條件式可見度的布林值參數</span><span class="sxs-lookup"><span data-stu-id="77e76-346">8. Add a Boolean Parameter for Conditional Visibility</span></span>  
  
#### <a name="to-add-a-boolean-parameter"></a><span data-ttu-id="77e76-347">加入布林參數</span><span class="sxs-lookup"><span data-stu-id="77e76-347">To add a boolean parameter</span></span>  
  
1.  <span data-ttu-id="77e76-348">在設計介面的 [報表資料] 窗格中，以滑鼠右鍵按一下 [參數]\*\*\*\*，然後按一下 [加入參數]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77e76-348">On the design surface, in the Report Data pane, right-click **Parameters**, and click **Add Parameter**.</span></span>  
  
2.  <span data-ttu-id="77e76-349">在 **[名稱]** 中，輸入 ShowSelections</span><span class="sxs-lookup"><span data-stu-id="77e76-349">In **Name**, type ShowSelections.</span></span>  
  
3.  <span data-ttu-id="77e76-350">在 **[提示]** 中，輸入 Show selections?</span><span class="sxs-lookup"><span data-stu-id="77e76-350">In **Prompt**, type Show selections?</span></span>  
  
4.  <span data-ttu-id="77e76-351">在 **[資料類型]** 的下拉式清單中，按一下 **[布林值]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-351">In **Data type**, from the drop-down list, click **Boolean**.</span></span>  
  
5.  <span data-ttu-id="77e76-352">按一下 **[預設值]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-352">Click **Default Values**.</span></span>  
  
6.  <span data-ttu-id="77e76-353">按一下 **[指定值]**，然後按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-353">Click **Specify value**, and then click **Add**.</span></span>  
  
7.  <span data-ttu-id="77e76-354">在 **[值]** 中，輸入 **False**。</span><span class="sxs-lookup"><span data-stu-id="77e76-354">In **Value**, type **False**.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-set-visibility-based-on-a-boolean-parameter"></a><span data-ttu-id="77e76-355">根據布林參數設定可見性</span><span class="sxs-lookup"><span data-stu-id="77e76-355">To set visibility based on a boolean parameter</span></span>  
  
1.  <span data-ttu-id="77e76-356">在設計介面上，以滑鼠右鍵按一下頁尾中顯示參數值的文字方塊，然後按一下 [文字方塊屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="77e76-356">On the design surface, right-click the text box in the page footer that displays the parameter values, and then click **Text Box Properties**.</span></span>  
  
2.  <span data-ttu-id="77e76-357">按一下 **[可見性]** 。</span><span class="sxs-lookup"><span data-stu-id="77e76-357">Click **Visibility**.</span></span>  
  
3.  <span data-ttu-id="77e76-358">選取 **[依據運算式顯示或隱藏]** 選項，然後按一下 **Fx**運算式按鈕。</span><span class="sxs-lookup"><span data-stu-id="77e76-358">Select the option **Show or hide based on an expression**, and then click the expression button **Fx**.</span></span>  
  
4.  <span data-ttu-id="77e76-359">輸入下列運算式： `=Not Parameters!ShowSelections.Value`</span><span class="sxs-lookup"><span data-stu-id="77e76-359">Type the following expression: `=Not Parameters!ShowSelections.Value`</span></span>  
  
     <span data-ttu-id="77e76-360">文字方塊 Visibility 選項會由 Hidden 屬性所控制。</span><span class="sxs-lookup"><span data-stu-id="77e76-360">The text box Visibility option is controlled by the property Hidden.</span></span> <span data-ttu-id="77e76-361">套用 `Not` 運算子，如此一來，當選取該參數時，Hidden 屬性會為 False，而且會顯示文字方塊。</span><span class="sxs-lookup"><span data-stu-id="77e76-361">Apply the `Not` operator so that when the parameter is selected, the Hidden property is false, and the text box will be displayed.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="77e76-362">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="77e76-362">Preview the report.</span></span>  
  
     <span data-ttu-id="77e76-363">顯示參數選項的文字方塊不會出現。</span><span class="sxs-lookup"><span data-stu-id="77e76-363">The text box that displays the parameter choices does not appear.</span></span>  
  
8.  <span data-ttu-id="77e76-364">在報表檢視器工具列中，按一下 [**顯示選擇**] 旁的 `True` 。</span><span class="sxs-lookup"><span data-stu-id="77e76-364">In the report viewer toolbar, next to **Show selections**, click `True`.</span></span>  
  
9. <span data-ttu-id="77e76-365">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="77e76-365">Preview the report.</span></span>  
  
 <span data-ttu-id="77e76-366">頁尾中的文字方塊會顯示您所選取的所有商店。</span><span class="sxs-lookup"><span data-stu-id="77e76-366">The text box in the page footer displays all the store names that you selected.</span></span>  
  
##  <a name="9-add-a-report-title"></a><a name="Title"></a><span data-ttu-id="77e76-367">9. 加入報表標題</span><span class="sxs-lookup"><span data-stu-id="77e76-367">9. Add a Report Title</span></span>  
  
#### <a name="to-add-a-report-title"></a><span data-ttu-id="77e76-368">若要加入報表標題</span><span class="sxs-lookup"><span data-stu-id="77e76-368">To add a report title</span></span>  
  
1.  <span data-ttu-id="77e76-369">在設計介面上，按一下 **[按一下以加入標題]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-369">On the design surface, click **Click to add title**.</span></span>  
  
2.  <span data-ttu-id="77e76-370">輸入「參數化產品銷售」，然後按一下文字方塊外部。</span><span class="sxs-lookup"><span data-stu-id="77e76-370">Type Parameterized Product Sales, and then click outside the text box.</span></span>  
  
##  <a name="10-save-the-report"></a><a name="Save"></a><span data-ttu-id="77e76-371">10. 儲存報表</span><span class="sxs-lookup"><span data-stu-id="77e76-371">10. Save the Report</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="77e76-372">若要將報表儲存在報表伺服器上</span><span class="sxs-lookup"><span data-stu-id="77e76-372">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="77e76-373">在 **[報表產生器]** 按鈕中，按一下 **[另存新檔]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-373">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="77e76-374">按一下 **[最近使用的網站和伺服器]**。</span><span class="sxs-lookup"><span data-stu-id="77e76-374">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="77e76-375">選取或輸入您有權儲存報表之報表伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="77e76-375">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="77e76-376">**[連接到報表伺服器]** 訊息隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="77e76-376">The message **Connecting to report server appears**.</span></span> <span data-ttu-id="77e76-377">連接完成時，您就會看見報表伺服器管理員指定為預設報表位置之報表資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="77e76-377">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>  
  
4.  <span data-ttu-id="77e76-378">在 **[名稱]** 中，將預設名稱取代為「參數化產品銷售」。</span><span class="sxs-lookup"><span data-stu-id="77e76-378">In **Name**, replace the default name with Parameterized Sales Report.</span></span>  
  
5.  <span data-ttu-id="77e76-379">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="77e76-379">Click **Save**.</span></span>  
  
 <span data-ttu-id="77e76-380">報表就會儲存至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="77e76-380">The report is saved to the report server.</span></span> <span data-ttu-id="77e76-381">您所連接的報表伺服器會顯示在視窗底部的狀態列中。</span><span class="sxs-lookup"><span data-stu-id="77e76-381">The report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="77e76-382">後續步驟</span><span class="sxs-lookup"><span data-stu-id="77e76-382">Next Steps</span></span>  
 <span data-ttu-id="77e76-383">以上總結如何將參數加入至報表的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="77e76-383">This concludes the walkthrough for how to add a parameter to your report.</span></span> <span data-ttu-id="77e76-384">若要深入了解參數，請參閱[報表參數 &#40;報表產生器和報表設計師&#41;](report-design/report-parameters-report-builder-and-report-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="77e76-384">To learn more about parameters, see [Report Parameters &#40;Report Builder and Report Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77e76-385">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77e76-385">See Also</span></span>  
 <span data-ttu-id="77e76-386">[教學課程 &#40;報表產生器&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="77e76-386">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 [<span data-ttu-id="77e76-387">SQL Server 2014 中的報表產生器</span><span class="sxs-lookup"><span data-stu-id="77e76-387">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
