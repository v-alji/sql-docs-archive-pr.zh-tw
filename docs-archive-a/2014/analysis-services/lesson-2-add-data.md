---
title: 第2課：加入資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 13c3a8cc-b1db-4aba-ad9b-038b7971be8d
author: minewiskan
ms.author: owend
ms.openlocfilehash: c844ea6558949407ca9b8206601ff7fe802ec399
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593666"
---
# <a name="lesson-2-add-data"></a><span data-ttu-id="32d6a-102">第 2 課：加入資料</span><span class="sxs-lookup"><span data-stu-id="32d6a-102">Lesson 2: Add Data</span></span>
  <span data-ttu-id="32d6a-103">在這一課，您將會使用 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中的 [資料表匯入精靈] 連接 AdventureWorksDW SQL Database、選取資料、預覽及篩選資料，然後將資料匯入您的模型工作空間。</span><span class="sxs-lookup"><span data-stu-id="32d6a-103">In this lesson, you will use the Table Import Wizard in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] to connect to the AdventureWorksDW SQL database, select data, preview, and filter the data, and then import the data into your model workspace.</span></span>  
  
 <span data-ttu-id="32d6a-104">使用 [資料表匯入精靈] 可讓您從各種關聯式來源匯入資料：Access、SQL、Oracle、Sybase、Informix、DB2、Teradata 以及其他來源。</span><span class="sxs-lookup"><span data-stu-id="32d6a-104">By using the Table Import Wizard, you can import data from a variety of relational sources: Access, SQL, Oracle, Sybase, Informix, DB2, Teradata, and more.</span></span> <span data-ttu-id="32d6a-105">從每一個關聯式來源匯入資料的步驟非常類似以下所述內容。</span><span class="sxs-lookup"><span data-stu-id="32d6a-105">The steps for importing data from each of these relational sources are very similar to what is described below.</span></span> <span data-ttu-id="32d6a-106">此外，您也可以使用預存程序選取資料。</span><span class="sxs-lookup"><span data-stu-id="32d6a-106">Additionally, data can be selected using a stored procedure.</span></span>  
  
 <span data-ttu-id="32d6a-107">若要深入了解匯入資料和可做為匯入來源的各種不同類型資料來源，請參閱[資料來源 &#40;SSAS 表格式&#41;](data-sources-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="32d6a-107">To learn more about importing data and the different types of data sources you can import from, see [Data Sources &#40;SSAS Tabular&#41;](data-sources-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="32d6a-108">這堂課的預估完成時間：**20 分鐘**</span><span class="sxs-lookup"><span data-stu-id="32d6a-108">Estimated time to complete this lesson: **20 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="32d6a-109">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="32d6a-109">Prerequisites</span></span>  
 <span data-ttu-id="32d6a-110">本主題是表格式模型教學課程的一部分，請依序完成。</span><span class="sxs-lookup"><span data-stu-id="32d6a-110">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="32d6a-111">在執行這堂課中的工作之前，您必須已完成上一堂課：[第1課：建立新的表格式模型專案](lesson-1-create-a-new-tabular-model-project.md)。</span><span class="sxs-lookup"><span data-stu-id="32d6a-111">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 1: Create a New Tabular Model Project](lesson-1-create-a-new-tabular-model-project.md).</span></span>  
  
## <a name="create-a-connection"></a><span data-ttu-id="32d6a-112">建立連接</span><span class="sxs-lookup"><span data-stu-id="32d6a-112">Create a Connection</span></span>  
  
#### <a name="to-create-a-connection-to-a-the-adventureworksdw2012-database"></a><span data-ttu-id="32d6a-113">若要建立與 AdventureWorksDW2012 資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="32d6a-113">To create a connection to a the AdventureWorksDW2012 database</span></span>  
  
1.  <span data-ttu-id="32d6a-114">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中，按一下 [模型]\*\*\*\* 功能表，然後按一下 [從資料來源匯入]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="32d6a-114">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **Model** menu, and then click **Import from Data Source**.</span></span>  
  
     <span data-ttu-id="32d6a-115">這樣會啟動 [資料表匯入精靈]，引導您設定與資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="32d6a-115">This launches the Table Import Wizard which guides you through setting up a connection to a data source.</span></span> <span data-ttu-id="32d6a-116">如果 [從資料來源匯入]\*\*\*\* 呈現灰色，請按兩下**方案總管**中的 **Model.bim**，在設計師中開啟模型。</span><span class="sxs-lookup"><span data-stu-id="32d6a-116">If **Import from Data Source** is greyed out, double click **Model.bim** in **Solution Explorer** to open the model in the designer.</span></span>  
  
2.  <span data-ttu-id="32d6a-117">在 [資料表匯入精靈]\*\*\*\* 的 [關聯式資料庫]\*\*\*\* 底下，按一下 [Microsoft SQL Server]\*\*\*\*，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="32d6a-117">In the **Table Import Wizard**, under **Relational Databases**, click **Microsoft SQL Server**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="32d6a-118">在 [**連接到 Microsoft SQL Server 資料庫]** 頁面的 [**易記連接名稱**] 中，輸入 `Adventure Works DB from SQL` 。</span><span class="sxs-lookup"><span data-stu-id="32d6a-118">In the **Connect to a Microsoft SQL Server Database** page, in **Friendly Connection Name**, type `Adventure Works DB from SQL`.</span></span>  
  
4.  <span data-ttu-id="32d6a-119">在 [伺服器名稱]\*\*\*\* 中，輸入您安裝 AdventureWorksDW 資料庫的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="32d6a-119">In **Server name**, type the name of the server you installed the AdventureWorksDW database.</span></span>  
  
5.  <span data-ttu-id="32d6a-120">在 [資料庫名稱]\*\*\*\* 欄位中，按一下向下箭頭並選取 **AdventureWorksDW**，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="32d6a-120">In the **Database name** field, click the down arrow and select **AdventureWorksDW**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="32d6a-121">在 [模擬資訊]\*\*\*\* 頁面中，您必須指定 Analysis Services 在匯入和處理資料時，用來連接資料來源的認證。</span><span class="sxs-lookup"><span data-stu-id="32d6a-121">In the **Impersonation Information** page, you need to specify the credentials Analysis Services will use to connect to the data source when importing and processing data.</span></span> <span data-ttu-id="32d6a-122">確認已選取 [特定的 Windows 使用者名稱和密碼]\*\*\*\*，然後在 [使用者名稱]\*\*\*\* 和 [密碼]\*\*\*\* 中輸入您的 Windows 登入認證，再按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="32d6a-122">Verify **Specific Windows user name and password** is selected, and then in **User Name** and **Password**, enter your Windows logon credentials, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="32d6a-123">使用 Windows 使用者帳戶和密碼是連線至資料來源最安全的方法。</span><span class="sxs-lookup"><span data-stu-id="32d6a-123">Using a Windows user account and password provides the most secure method of connecting to a data source.</span></span> <span data-ttu-id="32d6a-124">如需詳細資訊，請參閱[模擬 &#40;SSAS 表格式&#41;](tabular-models/impersonation-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="32d6a-124">For more information, see [Impersonation &#40;SSAS Tabular&#41;](tabular-models/impersonation-ssas-tabular.md).</span></span>  
  
7.  <span data-ttu-id="32d6a-125">在 [選擇如何匯入資料]\*\*\*\* 頁面中，確認已選取 [從資料表和檢視表清單來選取要匯入的資料]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="32d6a-125">In the **Choose How to Import the Data** page, verify **Select from a list of tables and views to choose the data to import** is selected.</span></span> <span data-ttu-id="32d6a-126">若要從資料表和檢視表的清單中選取，請按一下 [下一步]\*\*\*\* 顯示來源資料庫內所有來源資料表的清單。</span><span class="sxs-lookup"><span data-stu-id="32d6a-126">You want to select from a list of tables and views, so click **Next** to display a list of all the source tables in the source database.</span></span>  
  
8.  <span data-ttu-id="32d6a-127">在 [選取資料表和檢視表]\*\*\*\* 頁面中，選取下列資料表的核取方塊：**DimCustomer**、**DimDate**、**DimGeography**、**DimProduct**、**DimProductCategory**、**DimProductSubcategory** 和 **FactInternetSales**。</span><span class="sxs-lookup"><span data-stu-id="32d6a-127">In the **Select Tables and Views** page, select the check box for the following tables: **DimCustomer**, **DimDate**, **DimGeography**, **DimProduct**, **DimProductCategory**, **DimProductSubcategory**, and **FactInternetSales**.</span></span>  
  
9. <span data-ttu-id="32d6a-128">模型中的資料表最好使用較容易理解的名稱。</span><span class="sxs-lookup"><span data-stu-id="32d6a-128">We want to give the tables in the model more easily understood names.</span></span> <span data-ttu-id="32d6a-129">按一下 [易記名稱]\*\*\*\* 資料行中 **DimCustomer** 的資料格。</span><span class="sxs-lookup"><span data-stu-id="32d6a-129">Click on the cell in the **Friendly Name** column for **DimCustomer**.</span></span> <span data-ttu-id="32d6a-130">從 DimCustomer 中移除 "Dim"，以重新命名資料表。</span><span class="sxs-lookup"><span data-stu-id="32d6a-130">Rename the table by removing "Dim" from DimCustomer.</span></span>  
  
10. <span data-ttu-id="32d6a-131">重新命名其他資料表：</span><span class="sxs-lookup"><span data-stu-id="32d6a-131">Rename the other tables:</span></span>  
  
    |<span data-ttu-id="32d6a-132">來源名稱</span><span class="sxs-lookup"><span data-stu-id="32d6a-132">Source name</span></span>|<span data-ttu-id="32d6a-133">易記名稱</span><span class="sxs-lookup"><span data-stu-id="32d6a-133">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="32d6a-134">DimDate</span><span class="sxs-lookup"><span data-stu-id="32d6a-134">DimDate</span></span>|<span data-ttu-id="32d6a-135">Date</span><span class="sxs-lookup"><span data-stu-id="32d6a-135">Date</span></span>|  
    |<span data-ttu-id="32d6a-136">DimGeography</span><span class="sxs-lookup"><span data-stu-id="32d6a-136">DimGeography</span></span>|<span data-ttu-id="32d6a-137">[地理位置]</span><span class="sxs-lookup"><span data-stu-id="32d6a-137">Geography</span></span>|  
    |<span data-ttu-id="32d6a-138">DimProduct</span><span class="sxs-lookup"><span data-stu-id="32d6a-138">DimProduct</span></span>|<span data-ttu-id="32d6a-139">產品</span><span class="sxs-lookup"><span data-stu-id="32d6a-139">Product</span></span>|  
    |<span data-ttu-id="32d6a-140">DimProductCategory</span><span class="sxs-lookup"><span data-stu-id="32d6a-140">DimProductCategory</span></span>|<span data-ttu-id="32d6a-141">產品類別</span><span class="sxs-lookup"><span data-stu-id="32d6a-141">Product Category</span></span>|  
    |<span data-ttu-id="32d6a-142">DimProductSubcategory</span><span class="sxs-lookup"><span data-stu-id="32d6a-142">DimProductSubcategory</span></span>|<span data-ttu-id="32d6a-143">產品子類別目錄</span><span class="sxs-lookup"><span data-stu-id="32d6a-143">Product Subcategory</span></span>|  
    |<span data-ttu-id="32d6a-144">FactInternetSales</span><span class="sxs-lookup"><span data-stu-id="32d6a-144">FactInternetSales</span></span>|<span data-ttu-id="32d6a-145">Internet Sales</span><span class="sxs-lookup"><span data-stu-id="32d6a-145">Internet Sales</span></span>|  
  
     <span data-ttu-id="32d6a-146">**請不要**按一下 [完成]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="32d6a-146">**DO NOT** click **Finish**.</span></span>  
  
 <span data-ttu-id="32d6a-147">現在，您已經連接到資料庫、選取了要匯入的資料表，並且已使用易記的資料表名稱，即可前往下一節[在匯入之前篩選資料表資料](#FilterData)。</span><span class="sxs-lookup"><span data-stu-id="32d6a-147">Now that you have connected to the database, selected the tables to import, and given the tables friendly names, go to the next section, [Filter the Table Data prior to Importing](#FilterData).</span></span>  
  
##  <a name="filter-the-table-data"></a><a name="FilterData"></a><span data-ttu-id="32d6a-148">篩選資料表資料</span><span class="sxs-lookup"><span data-stu-id="32d6a-148">Filter the Table Data</span></span>  
 <span data-ttu-id="32d6a-149">您要從資料庫匯入的 DimCustomer 資料表包含來自原始 SQL Server Adventure Works 資料庫的資料子集。</span><span class="sxs-lookup"><span data-stu-id="32d6a-149">The DimCustomer table that you are importing from the database contains a subset of the data from the original SQL Server Adventure Works database.</span></span> <span data-ttu-id="32d6a-150">您將會從 DimCustomer 資料表中篩選出一些不必要的資料行。</span><span class="sxs-lookup"><span data-stu-id="32d6a-150">You will filter out some of the columns from the DimCustomer table that aren't necessary.</span></span> <span data-ttu-id="32d6a-151">如果可能的話，您會想要篩選掉不會使用的資料，以便節省模型使用的記憶體中空間。</span><span class="sxs-lookup"><span data-stu-id="32d6a-151">When possible, you will want to filter out data that will not be used in order to save in-memory space used by the model.</span></span>  
  
#### <a name="to-filter-the-table-data-prior-to-importing"></a><span data-ttu-id="32d6a-152">若要在匯入之前篩選資料表資料</span><span class="sxs-lookup"><span data-stu-id="32d6a-152">To filter the table data prior to importing</span></span>  
  
1.  <span data-ttu-id="32d6a-153">選取 **Customer** 資料表的資料列，然後按一下 [預覽和篩選]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="32d6a-153">Select the row for the **Customer** table, and then click **Preview & Filter**.</span></span> <span data-ttu-id="32d6a-154">[預覽選取的資料表]\*\*\*\* 視窗隨即開啟，其中會顯示 DimCustomer 來源資料表內的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="32d6a-154">The **Preview Selected Table** window opens with all the columns in the DimCustomer source table displayed.</span></span>  
  
2.  <span data-ttu-id="32d6a-155">清除下列資料行上方的核取方塊：</span><span class="sxs-lookup"><span data-stu-id="32d6a-155">Clear the checkbox at the top of the following columns:</span></span>  
  
    |<span data-ttu-id="32d6a-156">客戶</span><span class="sxs-lookup"><span data-stu-id="32d6a-156">Customer</span></span>|  
    |--------------|  
    |<span data-ttu-id="32d6a-157">**SpanishEducation**</span><span class="sxs-lookup"><span data-stu-id="32d6a-157">**SpanishEducation**</span></span>|  
    |<span data-ttu-id="32d6a-158">**FrenchEducation**</span><span class="sxs-lookup"><span data-stu-id="32d6a-158">**FrenchEducation**</span></span>|  
    |<span data-ttu-id="32d6a-159">**SpanishOccupation**</span><span class="sxs-lookup"><span data-stu-id="32d6a-159">**SpanishOccupation**</span></span>|  
    |<span data-ttu-id="32d6a-160">**FrenchOccupation**</span><span class="sxs-lookup"><span data-stu-id="32d6a-160">**FrenchOccupation**</span></span>|  
  
     <span data-ttu-id="32d6a-161">因為這些資料行的值與網際網路銷售分析無關，所以不需要匯入這些資料行。</span><span class="sxs-lookup"><span data-stu-id="32d6a-161">Since the values for these columns are not relevant to Internet sales analysis, there is no need to import these columns.</span></span> <span data-ttu-id="32d6a-162">消除不必要的資料行列將使您的模型變小。</span><span class="sxs-lookup"><span data-stu-id="32d6a-162">Eliminating unnecessary columns will make your model smaller.</span></span>  
  
3.  <span data-ttu-id="32d6a-163">確認已檢查過所有其他資料行，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="32d6a-163">Verify that all other columns are checked, and then click **OK**.</span></span>  
  
     <span data-ttu-id="32d6a-164">請注意，[套用的**篩選**] 字樣現在會顯示在 [ **Customer** ] 資料列的 [**篩選詳細資料] 資料**行;如果您按一下該連結，您會看到剛才套用之篩選的文字描述。</span><span class="sxs-lookup"><span data-stu-id="32d6a-164">Notice the words **Applied filters** are now displayed in the **Filter Details** column in the **Customer** row; if you click on that link you'll see a text description of the filters you just applied.</span></span>  
  
4.  <span data-ttu-id="32d6a-165">藉由清除每個資料表中下列資料行的核取方塊，篩選其餘資料表：</span><span class="sxs-lookup"><span data-stu-id="32d6a-165">Filter the remaining tables by clearing the checkboxes for the following columns in each table:</span></span>  
  
    |<span data-ttu-id="32d6a-166">Date</span><span class="sxs-lookup"><span data-stu-id="32d6a-166">Date</span></span>|  
    |----------|  
    |<span data-ttu-id="32d6a-167">**DateKey**</span><span class="sxs-lookup"><span data-stu-id="32d6a-167">**DateKey**</span></span>|  
    |<span data-ttu-id="32d6a-168">**SpanishDayNameOfWeek**</span><span class="sxs-lookup"><span data-stu-id="32d6a-168">**SpanishDayNameOfWeek**</span></span>|  
    |<span data-ttu-id="32d6a-169">**FrenchDayNameOfWeek**</span><span class="sxs-lookup"><span data-stu-id="32d6a-169">**FrenchDayNameOfWeek**</span></span>|  
    |<span data-ttu-id="32d6a-170">**SpanishMonthName**</span><span class="sxs-lookup"><span data-stu-id="32d6a-170">**SpanishMonthName**</span></span>|  
    |<span data-ttu-id="32d6a-171">**FrenchMonthName**</span><span class="sxs-lookup"><span data-stu-id="32d6a-171">**FrenchMonthName**</span></span>|  
  
    |<span data-ttu-id="32d6a-172">[地理位置]</span><span class="sxs-lookup"><span data-stu-id="32d6a-172">Geography</span></span>|  
    |---------------|  
    |<span data-ttu-id="32d6a-173">**SpanishCountryRegionName**</span><span class="sxs-lookup"><span data-stu-id="32d6a-173">**SpanishCountryRegionName**</span></span>|  
    |<span data-ttu-id="32d6a-174">**FrenchCountryRegionName**</span><span class="sxs-lookup"><span data-stu-id="32d6a-174">**FrenchCountryRegionName**</span></span>|  
    |<span data-ttu-id="32d6a-175">**IpAddressLocator**</span><span class="sxs-lookup"><span data-stu-id="32d6a-175">**IpAddressLocator**</span></span>|  
  
    |<span data-ttu-id="32d6a-176">產品</span><span class="sxs-lookup"><span data-stu-id="32d6a-176">Product</span></span>|  
    |-------------|  
    |<span data-ttu-id="32d6a-177">**SpanishProductName**</span><span class="sxs-lookup"><span data-stu-id="32d6a-177">**SpanishProductName**</span></span>|  
    |<span data-ttu-id="32d6a-178">**FrenchProductName**</span><span class="sxs-lookup"><span data-stu-id="32d6a-178">**FrenchProductName**</span></span>|  
    |<span data-ttu-id="32d6a-179">**FrenchDescription**</span><span class="sxs-lookup"><span data-stu-id="32d6a-179">**FrenchDescription**</span></span>|  
    |<span data-ttu-id="32d6a-180">**ChineseDescription**</span><span class="sxs-lookup"><span data-stu-id="32d6a-180">**ChineseDescription**</span></span>|  
    |<span data-ttu-id="32d6a-181">**ArabicDescription**</span><span class="sxs-lookup"><span data-stu-id="32d6a-181">**ArabicDescription**</span></span>|  
    |<span data-ttu-id="32d6a-182">**HebrewDescription**</span><span class="sxs-lookup"><span data-stu-id="32d6a-182">**HebrewDescription**</span></span>|  
    |<span data-ttu-id="32d6a-183">**ThaiDescription**</span><span class="sxs-lookup"><span data-stu-id="32d6a-183">**ThaiDescription**</span></span>|  
    |<span data-ttu-id="32d6a-184">**GermanDescription**</span><span class="sxs-lookup"><span data-stu-id="32d6a-184">**GermanDescription**</span></span>|  
    |<span data-ttu-id="32d6a-185">**JapaneseDescription**</span><span class="sxs-lookup"><span data-stu-id="32d6a-185">**JapaneseDescription**</span></span>|  
    |<span data-ttu-id="32d6a-186">**TurkishDescription**</span><span class="sxs-lookup"><span data-stu-id="32d6a-186">**TurkishDescription**</span></span>|  
  
    |<span data-ttu-id="32d6a-187">產品類別</span><span class="sxs-lookup"><span data-stu-id="32d6a-187">Product Category</span></span>|  
    |----------------------|  
    |<span data-ttu-id="32d6a-188">**SpanishProductCategoryName**</span><span class="sxs-lookup"><span data-stu-id="32d6a-188">**SpanishProductCategoryName**</span></span>|  
    |<span data-ttu-id="32d6a-189">**FrenchProductCategoryName**</span><span class="sxs-lookup"><span data-stu-id="32d6a-189">**FrenchProductCategoryName**</span></span>|  
  
    |<span data-ttu-id="32d6a-190">產品子類別目錄</span><span class="sxs-lookup"><span data-stu-id="32d6a-190">Product Subcategory</span></span>|  
    |-------------------------|  
    |<span data-ttu-id="32d6a-191">**SpanishProductSubcategoryName**</span><span class="sxs-lookup"><span data-stu-id="32d6a-191">**SpanishProductSubcategoryName**</span></span>|  
    |<span data-ttu-id="32d6a-192">**FrenchProductSubcategoryName**</span><span class="sxs-lookup"><span data-stu-id="32d6a-192">**FrenchProductSubcategoryName**</span></span>|  
  
    |<span data-ttu-id="32d6a-193">Internet Sales</span><span class="sxs-lookup"><span data-stu-id="32d6a-193">Internet Sales</span></span>|  
    |--------------------|  
    |<span data-ttu-id="32d6a-194">**OrderDateKey**</span><span class="sxs-lookup"><span data-stu-id="32d6a-194">**OrderDateKey**</span></span>|  
    |<span data-ttu-id="32d6a-195">**DueDateKey**</span><span class="sxs-lookup"><span data-stu-id="32d6a-195">**DueDateKey**</span></span>|  
    |<span data-ttu-id="32d6a-196">**ShipDateKey**</span><span class="sxs-lookup"><span data-stu-id="32d6a-196">**ShipDateKey**</span></span>|  
  
 <span data-ttu-id="32d6a-197">現在您已預覽並篩選掉不必要的資料，那麼就可以開始匯入資料。</span><span class="sxs-lookup"><span data-stu-id="32d6a-197">Now that you have previewed and filtered out unnecessary data, you can import the data.</span></span> <span data-ttu-id="32d6a-198">請前往下一節 **匯入選取的資料表和資料行資料**。</span><span class="sxs-lookup"><span data-stu-id="32d6a-198">Go to the next section **Import the Selected Tables and Column Data**.</span></span>  
  
##  <a name="import-the-selected-tables-and-column-data"></a><a name="Import"></a><span data-ttu-id="32d6a-199">匯入選取的資料表和資料行資料</span><span class="sxs-lookup"><span data-stu-id="32d6a-199">Import the Selected Tables and Column Data</span></span>  
 <span data-ttu-id="32d6a-200">現在您可以匯入選取的資料。</span><span class="sxs-lookup"><span data-stu-id="32d6a-200">You can now import the selected data.</span></span> <span data-ttu-id="32d6a-201">此精靈會匯入資料表資料，包含資料表之間的任何關聯性。</span><span class="sxs-lookup"><span data-stu-id="32d6a-201">The wizard imports the table data along with any relationships between tables.</span></span> <span data-ttu-id="32d6a-202">新的資料表和資料行會在模型中使用您指定的易記名稱建立，而且不會匯入您篩選掉的資料。</span><span class="sxs-lookup"><span data-stu-id="32d6a-202">New tables and columns are created in the model using the friendly names you specified, and data that you filtered out will not be imported.</span></span>  
  
#### <a name="to-import-the-selected-tables-and-column-data"></a><span data-ttu-id="32d6a-203">匯入選取的資料表和資料行資料</span><span class="sxs-lookup"><span data-stu-id="32d6a-203">To import the selected tables and column data</span></span>  
  
1.  <span data-ttu-id="32d6a-204">檢閱您的選擇。</span><span class="sxs-lookup"><span data-stu-id="32d6a-204">Review your selections.</span></span> <span data-ttu-id="32d6a-205">如果確認無誤，請按一下 [完成]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="32d6a-205">If everything looks OK, click **Finish**.</span></span>  
  
     <span data-ttu-id="32d6a-206">當匯入資料時，精靈會顯示已經提取的資料列數。</span><span class="sxs-lookup"><span data-stu-id="32d6a-206">While importing the data, the wizard displays how many rows have been fetched.</span></span> <span data-ttu-id="32d6a-207">所有資料都匯入之後，就會顯示一則訊息，指出此作業已順利完成。</span><span class="sxs-lookup"><span data-stu-id="32d6a-207">When all the data has been imported, a message indicating success is displayed.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="32d6a-208">若要查看在匯入的資料表之間自動建立的關聯性，請在 [資料準備]\*\*\*\* 資料列上按一下 [詳細資料]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="32d6a-208">To see the relationships that were automatically created between the imported tables, on the **Data preparation** row, click **Details**.</span></span>  
  
2.  <span data-ttu-id="32d6a-209">按一下 **關閉**。</span><span class="sxs-lookup"><span data-stu-id="32d6a-209">Click **Close**.</span></span>  
  
     <span data-ttu-id="32d6a-210">精靈隨即關閉，而且您可以看見模型設計師。</span><span class="sxs-lookup"><span data-stu-id="32d6a-210">The wizard closes and the model designer is visible.</span></span> <span data-ttu-id="32d6a-211">每一個資料表都已經加入成為模型設計師中的新索引標籤。</span><span class="sxs-lookup"><span data-stu-id="32d6a-211">Each table has been added as a new tab in the model designer.</span></span>  
  
## <a name="save-the-model-project"></a><span data-ttu-id="32d6a-212">儲存模型專案</span><span class="sxs-lookup"><span data-stu-id="32d6a-212">Save the Model Project</span></span>  
 <span data-ttu-id="32d6a-213">請您務必經常儲存模型專案。</span><span class="sxs-lookup"><span data-stu-id="32d6a-213">It is important to frequently save your model project.</span></span>  
  
#### <a name="to-save-the-model-project"></a><span data-ttu-id="32d6a-214">儲存模型專案</span><span class="sxs-lookup"><span data-stu-id="32d6a-214">To save the model project</span></span>  
  
-   <span data-ttu-id="32d6a-215">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中的 [檔案]\*\*\*\* 功能表上，按一下 [全部儲存]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="32d6a-215">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **File** menu, and then click **Save All**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="32d6a-216">後續步驟</span><span class="sxs-lookup"><span data-stu-id="32d6a-216">Next Step</span></span>  
 <span data-ttu-id="32d6a-217">若要繼續進行本教學課程，請前往下一課： [第 3 課：重新命名資料行](rename-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="32d6a-217">To continue this tutorial, go to the next lesson: [Lesson 3: Rename Columns](rename-columns.md).</span></span>  
  
  
