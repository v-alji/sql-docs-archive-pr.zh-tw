---
title: 使用 Analysis Services 教學課程專案的修改版本 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 685aa217-de1b-4df2-bf22-095228c40775
author: minewiskan
ms.author: owend
ms.openlocfilehash: b833a05a567f37443cf89f7356a0855e0827ea73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597426"
---
# <a name="using-a-modified-version-of-the-analysis-services-tutorial-project"></a><span data-ttu-id="1d08a-102">使用 Analysis Services 教學課程專案的已修改版本</span><span class="sxs-lookup"><span data-stu-id="1d08a-102">Using a Modified Version of the Analysis Services Tutorial Project</span></span>
  <span data-ttu-id="1d08a-103">本教學課程的其餘課程是依據您在前面三課所完成之 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程專案的增強型版本。</span><span class="sxs-lookup"><span data-stu-id="1d08a-103">The remaining lessons in this tutorial are based on an enhanced version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project that you completed in the first three lessons.</span></span> <span data-ttu-id="1d08a-104">更多的資料表和具名計算已新增至 **Adventure Works DW 2012** 資料來源檢視、更多的維度已新增至專案，而且這些新維度已新增至 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube。</span><span class="sxs-lookup"><span data-stu-id="1d08a-104">Additional tables and named calculations have been added to the **Adventure Works DW 2012** data source view, additional dimensions have been added to the project, and these new dimensions have been added to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="1d08a-105">此外，已加入第二個量值群組，它包含第二個事實資料表的量值。</span><span class="sxs-lookup"><span data-stu-id="1d08a-105">In addition, a second measure group has been added, which contains measures from a second fact table.</span></span> <span data-ttu-id="1d08a-106">這個增強型專案可讓您繼續學習如何在商業智慧應用程式中加入功能，而不必重複已學過的技巧。</span><span class="sxs-lookup"><span data-stu-id="1d08a-106">This enhanced project will enable you to continue learning how to add functionality to your business intelligence application without having to repeat the skills you have already learned.</span></span>  
  
 <span data-ttu-id="1d08a-107">在您繼續這個教學課程之前，必須先下載、解壓縮、載入和處理 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程專案的增強型版本。</span><span class="sxs-lookup"><span data-stu-id="1d08a-107">Before you can continue with the tutorial, you must download, extract, load and process the enhanced version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project.</span></span>  <span data-ttu-id="1d08a-108">使用本課程中的指示，以確保您已經執行所有步驟。</span><span class="sxs-lookup"><span data-stu-id="1d08a-108">Use the instructions in this lesson to ensure you have performed all the steps.</span></span>  
  
## <a name="downloading-and-extracting-the-project-file"></a><span data-ttu-id="1d08a-109">下載並解壓縮專案檔案</span><span class="sxs-lookup"><span data-stu-id="1d08a-109">Downloading and Extracting the Project File</span></span>  
  
1.  <span data-ttu-id="1d08a-110">[按一下這裡](https://go.microsoft.com/fwlink/?LinkID=221866) 前往下載頁面，此頁面會提供此教學課程隨附的範例專案。</span><span class="sxs-lookup"><span data-stu-id="1d08a-110">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to go to the download page that provides the sample projects that go with this tutorial.</span></span> <span data-ttu-id="1d08a-111">本教學課程專案已包含於 **Analysis Services Tutorial SQL Server 2012** 下載中。</span><span class="sxs-lookup"><span data-stu-id="1d08a-111">The tutorial projects are included in the **Analysis Services Tutorial SQL Server 2012** download.</span></span>  
  
2.  <span data-ttu-id="1d08a-112">按一下 [Analysis Services Tutorial SQL Server 2012]\*\*\*\*，下載包含適用於此教學課程之專案的套件。</span><span class="sxs-lookup"><span data-stu-id="1d08a-112">Click **Analysis Services Tutorial SQL Server 2012** to download the package that contains the projects for this tutorial.</span></span>  
  
     <span data-ttu-id="1d08a-113">根據預設，.zip 檔案會儲存至 [下載] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1d08a-113">By default, a .zip file is saved to the Downloads folder.</span></span> <span data-ttu-id="1d08a-114">您必須將 .zip 檔案移至路徑較短的位置 (例如，建立 C:\Tutorials 資料夾來儲存檔案)。</span><span class="sxs-lookup"><span data-stu-id="1d08a-114">You must move the .zip file to a location that has a shorter path (for example, create a C:\Tutorials folder to store the files).</span></span>  <span data-ttu-id="1d08a-115">接著，您可以解壓縮包含在 .zip 檔案中的檔案。</span><span class="sxs-lookup"><span data-stu-id="1d08a-115">You can then extract the files contained in the .zip file.</span></span> <span data-ttu-id="1d08a-116">如果您嘗試從路徑較長的 [下載] 資料夾解壓縮檔案，將會獲得課程 1。</span><span class="sxs-lookup"><span data-stu-id="1d08a-116">If you attempt to unzip the files from the Downloads folder, which has a longer path, you will only get Lesson 1.</span></span>  
  
3.  <span data-ttu-id="1d08a-117">在根磁碟機上或附近建立一個子資料夾，例如 C:\Tutorial。</span><span class="sxs-lookup"><span data-stu-id="1d08a-117">Create a subfolder at or near the root drive, for example, C:\Tutorial.</span></span>  
  
4.  <span data-ttu-id="1d08a-118">將 **Analysis Services Tutorial SQL Server 2012.zip** 移動到子資料夾。</span><span class="sxs-lookup"><span data-stu-id="1d08a-118">Move the **Analysis Services Tutorial SQL Server 2012.zip** file to the subfolder.</span></span>  
  
5.  <span data-ttu-id="1d08a-119">以滑鼠右鍵按一下該檔案，然後選取 [Extract All(全部解壓縮)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d08a-119">Right-click the file and select **Extract All**.</span></span>  
  
6.  <span data-ttu-id="1d08a-120">瀏覽至 **Lesson 4 Start** 資料夾以尋找 **Analysis Services Tutorial.sln** 檔案。</span><span class="sxs-lookup"><span data-stu-id="1d08a-120">Browse to the **Lesson 4 Start** folder to find the **Analysis Services Tutorial.sln** file.</span></span>  
  
## <a name="loading-and-processing-the-enhanced-project"></a><span data-ttu-id="1d08a-121">載入和處理增強型專案</span><span class="sxs-lookup"><span data-stu-id="1d08a-121">Loading and Processing the Enhanced Project</span></span>  
  
1.  <span data-ttu-id="1d08a-122">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 的 [檔案**File** ] 功能表上，按一下 [**關閉方案**] 以關閉您不會使用的檔案。</span><span class="sxs-lookup"><span data-stu-id="1d08a-122">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **File** menu, click **Close Solution** to close files you won't be using.</span></span>  
  
2.  <span data-ttu-id="1d08a-123">在 [檔案]\*\*\*\* 功能表上，指向 [開啟舊檔]\*\*\*\*，再按一下 [專案/方案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d08a-123">On the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="1d08a-124">瀏覽到您解壓縮教學課程專案檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="1d08a-124">Browse to the location where you extracted the tutorial project files.</span></span>  
  
     <span data-ttu-id="1d08a-125">尋找名為 **Lesson 4 Start**的資料夾，然後按兩下 Analysis Services Tutorial.sln。</span><span class="sxs-lookup"><span data-stu-id="1d08a-125">Find the folder named **Lesson 4 Start**, and then double-click Analysis Services Tutorial.sln.</span></span>  
  
4.  <span data-ttu-id="1d08a-126">將 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程專案的增強型版本部署到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]的本機執行個體，或另一個執行個體，並確認處理已順利完成。</span><span class="sxs-lookup"><span data-stu-id="1d08a-126">Deploy the enhanced version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project to the local instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], or to another instance, and verify that processing completes successfully.</span></span>  
  
## <a name="understanding-the-enhancements-to-the-project"></a><span data-ttu-id="1d08a-127">了解專案的增強功能</span><span class="sxs-lookup"><span data-stu-id="1d08a-127">Understanding the Enhancements to the Project</span></span>  
 <span data-ttu-id="1d08a-128">這個專案的增強型版本與您在前面 3 課所完成的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程專案的版本不同。</span><span class="sxs-lookup"><span data-stu-id="1d08a-128">The enhanced version of the project is different from the version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project that you completed in the first three lessons.</span></span> <span data-ttu-id="1d08a-129">下列章節將描述其差異。</span><span class="sxs-lookup"><span data-stu-id="1d08a-129">The differences are described in the following sections.</span></span> <span data-ttu-id="1d08a-130">在繼續本教學課程的其餘課程之前，請檢閱這項資訊。</span><span class="sxs-lookup"><span data-stu-id="1d08a-130">Review this information before continuing with the remaining lessons in the tutorial.</span></span>  
  
### <a name="data-source-view"></a><span data-ttu-id="1d08a-131">[資料來源檢視]</span><span class="sxs-lookup"><span data-stu-id="1d08a-131">Data Source View</span></span>  
 <span data-ttu-id="1d08a-132">增強型專案中的資料來源檢視多包含一個事實資料表及四個維度資料表，它們來自 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="1d08a-132">The data source view in the enhanced project contains one additional fact table and four additional dimension tables from the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span>  
  
 <span data-ttu-id="1d08a-133">請注意，資料來源檢視中的十個資料表使得 \<All Tables> 圖表變得很擁擠，</span><span class="sxs-lookup"><span data-stu-id="1d08a-133">Notice that with ten tables in the data source view, the \<All Tables> diagram is becoming crowded.</span></span> <span data-ttu-id="1d08a-134">以致於不容易了解資料表之間的關聯性及尋找特定資料表。</span><span class="sxs-lookup"><span data-stu-id="1d08a-134">This makes it difficult to easily understand the relationships between the tables and to locate specific tables.</span></span> <span data-ttu-id="1d08a-135">為了解決這個問題，資料表分成兩個邏輯圖表：[網際網路銷售]\*\*\*\* 圖表和 [轉售商銷售]\*\*\*\* 圖表。</span><span class="sxs-lookup"><span data-stu-id="1d08a-135">To solve this problem, the tables are organized into two logical diagrams, the **Internet Sales** diagram and the **Reseller Sales** diagram.</span></span> <span data-ttu-id="1d08a-136">這些圖表各以單一事實資料表為中心。</span><span class="sxs-lookup"><span data-stu-id="1d08a-136">These diagrams are each organized around a single fact table.</span></span> <span data-ttu-id="1d08a-137">建立邏輯圖表可讓您檢視及使用資料來源檢視中的資料表的特定子集，而不是檢視單一圖表中的所有資料表及其關聯性。</span><span class="sxs-lookup"><span data-stu-id="1d08a-137">Creating logical diagrams lets you view and work with a specific subset of the tables in a data source view instead of always viewing all the tables and their relationships in a single diagram.</span></span>  
  
#### <a name="internet-sales-diagram"></a><span data-ttu-id="1d08a-138">Internet Sales 圖表</span><span class="sxs-lookup"><span data-stu-id="1d08a-138">Internet Sales Diagram</span></span>  
 <span data-ttu-id="1d08a-139">[網際網路銷售]\*\*\*\* 圖表包含透過網際網路直接向客戶銷售 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] 產品之相關資料表。</span><span class="sxs-lookup"><span data-stu-id="1d08a-139">The **Internet Sales** diagram contains the tables that are related to the sale of [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] products directly to customers through the Internet.</span></span> <span data-ttu-id="1d08a-140">圖表中的資料表為 4 個維度資料表和 1 個事實資料表，這些是您在第 1 課新增至 **Adventure Works DW 2012** 資料來源檢視中的資料表。</span><span class="sxs-lookup"><span data-stu-id="1d08a-140">The tables in the diagram are the four dimension tables and one fact table that you added to the **Adventure Works DW 2012** data source view in Lesson 1.</span></span> <span data-ttu-id="1d08a-141">這些資料表如下：</span><span class="sxs-lookup"><span data-stu-id="1d08a-141">These tables are as follows:</span></span>  
  
-   <span data-ttu-id="1d08a-142">**地理位置**</span><span class="sxs-lookup"><span data-stu-id="1d08a-142">**Geography**</span></span>  
  
-   <span data-ttu-id="1d08a-143">**Customer**</span><span class="sxs-lookup"><span data-stu-id="1d08a-143">**Customer**</span></span>  
  
-   <span data-ttu-id="1d08a-144">**日期**</span><span class="sxs-lookup"><span data-stu-id="1d08a-144">**Date**</span></span>  
  
-   <span data-ttu-id="1d08a-145">**產品**</span><span class="sxs-lookup"><span data-stu-id="1d08a-145">**Product**</span></span>  
  
-   <span data-ttu-id="1d08a-146">**InternetSales**</span><span class="sxs-lookup"><span data-stu-id="1d08a-146">**InternetSales**</span></span>  
  
#### <a name="reseller-sales-diagram"></a><span data-ttu-id="1d08a-147">轉售商銷售圖表</span><span class="sxs-lookup"><span data-stu-id="1d08a-147">Reseller Sales Diagram</span></span>  
 <span data-ttu-id="1d08a-148">[轉售商銷售]\*\*\*\* 圖表包含與轉售商銷售 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] 產品有關的資料表。</span><span class="sxs-lookup"><span data-stu-id="1d08a-148">The **Reseller Sales** diagram contains the tables that are related to the sale of [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] products by resellers.</span></span> <span data-ttu-id="1d08a-149">此圖表包含下列七個維度資料表及一個事實資料表，它們來自 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 資料庫：</span><span class="sxs-lookup"><span data-stu-id="1d08a-149">This diagram contains the following seven dimension tables and one fact table from the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database:</span></span>  
  
-   <span data-ttu-id="1d08a-150">**轉售商**</span><span class="sxs-lookup"><span data-stu-id="1d08a-150">**Reseller**</span></span>  
  
-   <span data-ttu-id="1d08a-151">**促銷**</span><span class="sxs-lookup"><span data-stu-id="1d08a-151">**Promotion**</span></span>  
  
-   <span data-ttu-id="1d08a-152">**SalesTerritory**</span><span class="sxs-lookup"><span data-stu-id="1d08a-152">**SalesTerritory**</span></span>  
  
-   <span data-ttu-id="1d08a-153">**地理位置**</span><span class="sxs-lookup"><span data-stu-id="1d08a-153">**Geography**</span></span>  
  
-   <span data-ttu-id="1d08a-154">**日期**</span><span class="sxs-lookup"><span data-stu-id="1d08a-154">**Date**</span></span>  
  
-   <span data-ttu-id="1d08a-155">**產品**</span><span class="sxs-lookup"><span data-stu-id="1d08a-155">**Product**</span></span>  
  
-   <span data-ttu-id="1d08a-156">**員工**</span><span class="sxs-lookup"><span data-stu-id="1d08a-156">**Employee**</span></span>  
  
-   <span data-ttu-id="1d08a-157">**ResellerSales**</span><span class="sxs-lookup"><span data-stu-id="1d08a-157">**ResellerSales**</span></span>  
  
 <span data-ttu-id="1d08a-158">請注意，**DimGeography**、**DimDate** 和 **DimProduct** 資料表同時用於 [網際網路銷售額]\*\*\*\* 圖表和 [轉售商銷售]\*\*\*\* 圖表。</span><span class="sxs-lookup"><span data-stu-id="1d08a-158">Notice that the **DimGeography**, **DimDate**, and **DimProduct** tables are used in both the **Internet Sales** diagram and the **Reseller Sales** diagram.</span></span> <span data-ttu-id="1d08a-159">維度資料表可連結至多個事實資料表。</span><span class="sxs-lookup"><span data-stu-id="1d08a-159">Dimension tables can be linked to multiple fact tables.</span></span>  
  
### <a name="database-and-cube-dimensions"></a><span data-ttu-id="1d08a-160">資料庫和 Cube 維度</span><span class="sxs-lookup"><span data-stu-id="1d08a-160">Database and Cube Dimensions</span></span>  
 <span data-ttu-id="1d08a-161">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程專案包含 5 個新資料庫維度， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 包含這 5 個與 Cube 維度相同的維度。</span><span class="sxs-lookup"><span data-stu-id="1d08a-161">The [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project contains five new database dimensions, and the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube contains these same five dimensions as cube dimensions.</span></span> <span data-ttu-id="1d08a-162">這些維度已定義為具有階層和屬性，這些已使用具名計算、構成要素成員索引鍵和顯示資料夾來修改過。</span><span class="sxs-lookup"><span data-stu-id="1d08a-162">These dimensions have been defined to have user hierarchies and attributes that were modified by using named calculations, composition member keys, and display folders.</span></span> <span data-ttu-id="1d08a-163">下列清單描述的是新的維度。</span><span class="sxs-lookup"><span data-stu-id="1d08a-163">The new dimensions are described in the following list.</span></span>  
  
 <span data-ttu-id="1d08a-164">Reseller 維度</span><span class="sxs-lookup"><span data-stu-id="1d08a-164">Reseller Dimension</span></span>  
 <span data-ttu-id="1d08a-165">Reseller 維度是依據 **Adventure Works DW 2012** 資料來源檢視中的 **Reseller** 資料表。</span><span class="sxs-lookup"><span data-stu-id="1d08a-165">The Reseller dimension is based on the **Reseller** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
 <span data-ttu-id="1d08a-166">Promotion 維度</span><span class="sxs-lookup"><span data-stu-id="1d08a-166">Promotion Dimension</span></span>  
 <span data-ttu-id="1d08a-167">Promotion 維度是依據 **Adventure Works DW 2012** 資料來源檢視中的 **Promotion** 資料表。</span><span class="sxs-lookup"><span data-stu-id="1d08a-167">The Promotion dimension is based on the **Promotion** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
 <span data-ttu-id="1d08a-168">Sales Territory 維度</span><span class="sxs-lookup"><span data-stu-id="1d08a-168">Sales Territory Dimension</span></span>  
 <span data-ttu-id="1d08a-169">Sales Territory 維度是依據 **Adventure Works DW 2012** 資料來源檢視中的 **SalesTerritory** 資料表。</span><span class="sxs-lookup"><span data-stu-id="1d08a-169">The Sales Territory dimension is based on the **SalesTerritory** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
 <span data-ttu-id="1d08a-170">Employee 維度</span><span class="sxs-lookup"><span data-stu-id="1d08a-170">Employee Dimension</span></span>  
 <span data-ttu-id="1d08a-171">Employee 維度是依據 **Adventure Works DW 2012** 資料來源檢視中的 **Employee** 資料表。</span><span class="sxs-lookup"><span data-stu-id="1d08a-171">The Employee dimension is based on the **Employee** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
 <span data-ttu-id="1d08a-172">Geography 維度</span><span class="sxs-lookup"><span data-stu-id="1d08a-172">Geography Dimension</span></span>  
 <span data-ttu-id="1d08a-173">Geography 維度是依據 **Adventure Works DW 2012** 資料來源檢視中的 **Geography** 資料表。</span><span class="sxs-lookup"><span data-stu-id="1d08a-173">The Geography dimension is based on the **Geography** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
#### <a name="analysis-services-cube"></a><span data-ttu-id="1d08a-174">Analysis Services Cube</span><span class="sxs-lookup"><span data-stu-id="1d08a-174">Analysis Services Cube</span></span>  
 <span data-ttu-id="1d08a-175">**Analysis Services Tutorial** Cube 現在包含兩個量值群組：以 **InternetSales** 資料表為基礎的原始量值群組，和以 **Adventure Works DW 2012** 資料來源檢視中的 **ResellerSales** 資料表為基礎的另一個量值群組。</span><span class="sxs-lookup"><span data-stu-id="1d08a-175">The **Analysis Services Tutorial** cube now contains two measure groups, the original measure group based on the **InternetSales** table and a second measure group based on the **ResellerSales** table in the **Adventure Works DW 2012** data source view.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="1d08a-176">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="1d08a-176">Next Task in Lesson</span></span>  
 [<span data-ttu-id="1d08a-177">定義父子式階層中父屬性 (Attribute) 的屬性 (Property)</span><span class="sxs-lookup"><span data-stu-id="1d08a-177">Defining Parent Attribute Properties in a Parent-Child Hierarchy</span></span>](lesson-4-2-defining-parent-attribute-properties-in-a-parent-child-hierarchy.md) 
  
## <a name="see-also"></a><span data-ttu-id="1d08a-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d08a-178">See Also</span></span>  
 [<span data-ttu-id="1d08a-179">部署 Analysis Services 專案</span><span class="sxs-lookup"><span data-stu-id="1d08a-179">Deploying an Analysis Services Project</span></span>](lesson-2-5-deploying-an-analysis-services-project.md)  
  
  
