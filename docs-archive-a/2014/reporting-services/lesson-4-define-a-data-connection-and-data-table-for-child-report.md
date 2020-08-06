---
title: 第 4 課：定義子報表的資料連線和資料表 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a6aa2c56-227c-43c5-a28e-c7104131ac5e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6d9144d960ad933afa65f9d4483e96b5f732d944
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592514"
---
# <a name="lesson-4-define-a-data-connection-and-data-table-for-child-report"></a><span data-ttu-id="daa2a-102">第 4 課：定義子報表的資料連接和資料表</span><span class="sxs-lookup"><span data-stu-id="daa2a-102">Lesson 4: Define a Data Connection and Data Table for Child Report</span></span>
  <span data-ttu-id="daa2a-103">設計父報表之後，下一步是要建立子報表的資料連接和資料表。</span><span class="sxs-lookup"><span data-stu-id="daa2a-103">After you design the parent report, you next step is to create a data connection and a data table for the child report.</span></span> <span data-ttu-id="daa2a-104">在本教學課程中，資料連接是指 AdventureWorks2008 資料庫。</span><span class="sxs-lookup"><span data-stu-id="daa2a-104">In this tutorial the data connection is to the AdventureWorks2008 database.</span></span> <span data-ttu-id="daa2a-105">您也可以選擇連接到 AdventureWorks2012 資料庫。</span><span class="sxs-lookup"><span data-stu-id="daa2a-105">You also have the option of connecting to the AdventureWorks2012 database.</span></span>  
  
### <a name="to-define-a-data-connection-and-datatable-by-adding-a-dataset-for-child-report"></a><span data-ttu-id="daa2a-106">若要藉由加入 DataSet 定義資料連接和 DataTable (針對子報表)</span><span class="sxs-lookup"><span data-stu-id="daa2a-106">To define a data connection and DataTable by adding a DataSet (for child report)</span></span>  
  
1.  <span data-ttu-id="daa2a-107">在 [**網站**] 功能表上，按一下 [**加入新專案**]。</span><span class="sxs-lookup"><span data-stu-id="daa2a-107">On the **Website** menu, click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="daa2a-108">在 [**加入新專案**] 對話方塊中，按一下 [**資料集**]，然後按一下 [**加入**]。</span><span class="sxs-lookup"><span data-stu-id="daa2a-108">In the **Add New Item** dialog box, click **DataSet** and then click **Add**.</span></span> <span data-ttu-id="daa2a-109">出現提示時，您應該按一下 [**是]**，將專案新增至 [ **App_Code** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="daa2a-109">When prompted, you should add the item to the **App_Code** folder by clicking **Yes**.</span></span>  
  
     <span data-ttu-id="daa2a-110">這樣會將新的 XSD 檔 **DataSet2.xsd** 加入專案，並開啟 DataSet 設計工具。</span><span class="sxs-lookup"><span data-stu-id="daa2a-110">This adds a new XSD file **DataSet2.xsd** to the project and opens the DataSet Designer.</span></span>  
  
3.  <span data-ttu-id="daa2a-111">從 [工具箱] 視窗將 **TableAdapter** 控制項拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="daa2a-111">From the Toolbox window, drag a **TableAdapter** control to the design surface.</span></span> <span data-ttu-id="daa2a-112">這樣會啟動 [ **TableAdapter** 組態精靈]。</span><span class="sxs-lookup"><span data-stu-id="daa2a-112">This launches the **TableAdapter** Configuration Wizard.</span></span>  
  
4.  <span data-ttu-id="daa2a-113">在 [**選擇您的資料連線**] 頁面上，按一下 [**新增連接**]。</span><span class="sxs-lookup"><span data-stu-id="daa2a-113">On the **Choose Your Data Connection** page, click **New Connection**.</span></span>  
  
5.  <span data-ttu-id="daa2a-114">在 [新增連線]\*\*\*\* 對話方塊中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="daa2a-114">In the **Add Connection** dialog box, perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="daa2a-115">在 [**伺服器名稱**] 方塊中，輸入**AdventureWorks2008**資料庫所在的伺服器。</span><span class="sxs-lookup"><span data-stu-id="daa2a-115">In the **Server name** box, enter the server where the **AdventureWorks2008** database is located.</span></span>  
  
         <span data-ttu-id="daa2a-116">預設的 SQL Server Express 執行個體為 **(local)\sqlexpress**。</span><span class="sxs-lookup"><span data-stu-id="daa2a-116">The default SQL Server Express instance is **(local)\sqlexpress**.</span></span>  
  
    2.  <span data-ttu-id="daa2a-117">在 [登入伺服器]\*\*\*\* 區段中，選取提供資料存取的選項。</span><span class="sxs-lookup"><span data-stu-id="daa2a-117">In the **Log on to the server** section, select the option that provides you access to the data.</span></span> <span data-ttu-id="daa2a-118">[使用 Windows 驗證]\*\*\*\* 是預設值。</span><span class="sxs-lookup"><span data-stu-id="daa2a-118">**Use Windows Authentication** is the default.</span></span>  
  
    3.  <span data-ttu-id="daa2a-119">從 [**選取或輸入資料庫名稱**] 下拉式清單中，按一下 [ **AdventureWorks2008**]。</span><span class="sxs-lookup"><span data-stu-id="daa2a-119">From the **Select or enter a database name** drop-down list, click **AdventureWorks2008**.</span></span>  
  
    4.  <span data-ttu-id="daa2a-120">按一下 [確定]\*\*\*\*，然後按 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="daa2a-120">Click **OK**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="daa2a-121">如果您已在步驟 5 (b) 中選取 [使用 SQL Server 驗證]\*\*\*\*，請選取在字串中包含機密資料或在應用程式程式碼中設定資訊的選項。</span><span class="sxs-lookup"><span data-stu-id="daa2a-121">If you selected **Use SQL Server Authentication** in Step 5 (b), select the option whether to include the sensitive data in the string or set the information in your application code.</span></span>  
  
7.  <span data-ttu-id="daa2a-122">在 [將**連接字串儲存到應用程式佈建檔**] 頁面上，輸入連接字串的名稱或接受預設**AdventureWorks2008ConnectionString**。</span><span class="sxs-lookup"><span data-stu-id="daa2a-122">On the **Save the Connection String to the Application Configuration File** page, type in the name for the connection string or accept the default **AdventureWorks2008ConnectionString**.</span></span> <span data-ttu-id="daa2a-123">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="daa2a-123">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="daa2a-124">在 [**選擇命令類型**] 頁面上，選取 [**使用 SQL 語句]**，然後按 **[下一步**]。</span><span class="sxs-lookup"><span data-stu-id="daa2a-124">On the **Choose a Command Type** page, select **Use SQL Statements**, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="daa2a-125">在 [**輸入 SQL 語句**] 頁面上，輸入下列 transact-SQL 查詢以從**AdventureWorks2008**資料庫中取出資料，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="daa2a-125">On the **Enter a SQL Statement** page, enter the following Transact-SQL query to retrieve data from the **AdventureWorks2008** database, and then click **Next**.</span></span>  
  
    ```  
    SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail  
    ```  
  
     <span data-ttu-id="daa2a-126">您也可以按一下 [**查詢**產生器] 來建立查詢，然後按一下 [**執行查詢**] 按鈕來驗證查詢。</span><span class="sxs-lookup"><span data-stu-id="daa2a-126">You can also create the query by clicking **Query Builder**, and then verify the query by clicking **Execute Query** button.</span></span> <span data-ttu-id="daa2a-127">如果查詢未傳回預期的資料，表示您可能使用較舊的 AdventureWorks 版本。</span><span class="sxs-lookup"><span data-stu-id="daa2a-127">If the query does not return the expected data, you might be using an earlier version of AdventureWorks.</span></span> <span data-ttu-id="daa2a-128">如需安裝**AdventureWorks2008**版本之 adventureworks 的詳細資訊，請參閱[逐步解說：安裝 adventureworks 資料庫](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="daa2a-128">For more information about installing the **AdventureWorks2008** version of AdventureWorks, see [Walkthrough: Installing the AdventureWorks Database](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx).</span></span>  
  
10. <span data-ttu-id="daa2a-129">在 [**選擇要產生的方法**] 頁面上，取消核取 [\*\*建立方法以直接將更新傳送至資料庫 (GenerateDBDirectMethods) \*\*]，然後按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="daa2a-129">On the **Choose Methods to Generate** page, uncheck **Create methods to send updates directly to the database (GenerateDBDirectMethods)**, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="daa2a-130">您現在已完成將 ADO.NET [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx)設定為報表的資料來源。</span><span class="sxs-lookup"><span data-stu-id="daa2a-130">You have now completed configuring the ADO.NET [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) as data source for your report.</span></span> <span data-ttu-id="daa2a-131">在 Visual Studio 中的 DataSet 設計工具頁面上，應該會看到您加入的 **DataTable** ，並且列出查詢中指定的資料行。</span><span class="sxs-lookup"><span data-stu-id="daa2a-131">On the DataSet Designer page in Visual Studio, you should see the **DataTable** you added, listing the columns specified in the query.</span></span> <span data-ttu-id="daa2a-132">根據查詢，DataSet2 包含 PurhcaseOrderDetail 資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="daa2a-132">DataSet2 contains the data from the PurhcaseOrderDetail table, based on the query.</span></span>  
  
11. <span data-ttu-id="daa2a-133">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="daa2a-133">Save the file.</span></span>  
  
12. <span data-ttu-id="daa2a-134">若要預覽資料，請按一下 [**資料**] 功能表上的 [**預覽資料**]，然後按一下 [**預覽**]。</span><span class="sxs-lookup"><span data-stu-id="daa2a-134">To preview the data, click **Preview Data** on the **Data** menu, and then click **Preview**.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="daa2a-135">下一項工作</span><span class="sxs-lookup"><span data-stu-id="daa2a-135">Next Task</span></span>  
 <span data-ttu-id="daa2a-136">您已成功建立子報表的資料連接和資料表。</span><span class="sxs-lookup"><span data-stu-id="daa2a-136">You have successfully created a data connection and data table for the child report.</span></span> <span data-ttu-id="daa2a-137">接下來您將使用 [報表精靈] 設計子報表。</span><span class="sxs-lookup"><span data-stu-id="daa2a-137">Next, you will design the child report using the Report Wizard.</span></span>  
  
  
