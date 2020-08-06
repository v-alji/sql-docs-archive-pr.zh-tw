---
title: 教學課程：使用 OData 來源 [SSIS] |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 2c64cf8b-5edb-48df-8ffe-697096258f71
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a13b04494ed00251774b490b1cc929769a869acb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599078"
---
# <a name="tutorial-using-the-odata-source-ssis"></a><span data-ttu-id="8544d-102">教學課程：使用 OData 來源 [SSIS]</span><span class="sxs-lookup"><span data-stu-id="8544d-102">Tutorial: Using the OData Source [SSIS]</span></span>
  <span data-ttu-id="8544d-103">本教學課程將逐步引導您進行從範例 **Northwind** OData 服務 (http://services.odata.org/V3/Northwind/Northwind.svc/) 擷取 **Employees** 集合，然後將該集合載入一般檔案的程序。</span><span class="sxs-lookup"><span data-stu-id="8544d-103">This tutorial walks you through the process to extract the **Employees** collection from the sample **Northwind** OData service (http://services.odata.org/V3/Northwind/Northwind.svc/), and then load it into a flat file.</span></span>  
  
## <a name="1-create-an-integration-services-project"></a><span data-ttu-id="8544d-104">1.建立 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="8544d-104">1. Create an Integration Services Project</span></span>  
  
1.  <span data-ttu-id="8544d-105">啟動 **[SQL Server Data Tools]** 或 [ [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]]。</span><span class="sxs-lookup"><span data-stu-id="8544d-105">Launch **SQL Server Data Tools** or [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span>  
  
2.  <span data-ttu-id="8544d-106">按一下 [檔案]  ，指向 [新增]  ，然後按一下 [專案]  。</span><span class="sxs-lookup"><span data-stu-id="8544d-106">Click **File**, point to **New**, and click **Project**.</span></span>  
  
3.  <span data-ttu-id="8544d-107">在 **[新增專案]** 對話方塊中，依序展開 **[已安裝的]** 、 **[範本]** 、 **[Business Intelligence]** ，然後按一下 **[Integration Services]** 。</span><span class="sxs-lookup"><span data-stu-id="8544d-107">In the **New Project** dialog box, expand **Installed**, expand **Templates**, expand **Business Intelligence**, and click **Integration Services**.</span></span>  
  
4.  <span data-ttu-id="8544d-108">選取該專案類型的 **[Integration Services 專案]** 。</span><span class="sxs-lookup"><span data-stu-id="8544d-108">Select **Integration Services Project** for the type of project.</span></span>  
  
5.  <span data-ttu-id="8544d-109">輸入專案的 **[名稱]** 並選取 **[位置]** ，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="8544d-109">Enter a **name** and select a **location** for the project, and click **OK**.</span></span>  
  
## <a name="2-add-and-configure-odata-source-to-the-ssis-package"></a><span data-ttu-id="8544d-110">2.將 OData 來源加入至 SSIS 封裝並進行設定</span><span class="sxs-lookup"><span data-stu-id="8544d-110">2. Add and Configure OData Source to the SSIS Package</span></span>  
  
1.  <span data-ttu-id="8544d-111">從 [SSIS 工具箱]  將 [資料流程工作]  拖放至 SSIS 封裝的控制流程設計介面。</span><span class="sxs-lookup"><span data-stu-id="8544d-111">Drag-drop a **Data Flow Task** from the **SSIS Toolbox** on to the control flow design surface of your SSIS package.</span></span>  
  
2.  <span data-ttu-id="8544d-112">按一下 **[資料流程]** 索引標籤或按兩下新加入的 **[資料流程工作]** ，啟動 **[資料流程設計介面]**。</span><span class="sxs-lookup"><span data-stu-id="8544d-112">Click the **Data Flow** tab, or double click on the newly added **Data Flow Task** to launch the **Data Flow design surface**.</span></span>  
  
3.  <span data-ttu-id="8544d-113">從 [SSIS 工具箱]  的 [Common]  群組中拖放 [OData 來源]  。</span><span class="sxs-lookup"><span data-stu-id="8544d-113">Drag-drop **OData Source** from the **Common** group in the **SSIS Toolbox**.</span></span> <span data-ttu-id="8544d-114">初次安裝 **OData 來源** 時，它會出現在 **SSIS 工具箱** 的 **Common**群組下方。</span><span class="sxs-lookup"><span data-stu-id="8544d-114">When the **OData Source** is first installed, it will appear under the **Common** group in the **SSIS Toolbox**.</span></span>  
  
4.  <span data-ttu-id="8544d-115">按兩下 **[OData 來源]** 元件，啟動 **[OData 來源編輯器]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8544d-115">Double click the **OData Source** component to launch the **OData Source Editor** dialog box.</span></span>  
  
5.  <span data-ttu-id="8544d-116">按一下 [新增...]\*\*\*\* 以新增 OData 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="8544d-116">Click **New...** to add a new OData Connection Manager.</span></span>  
  
6.  <span data-ttu-id="8544d-117">輸入 **[服務文件位置]** 的 OData 服務 URL。</span><span class="sxs-lookup"><span data-stu-id="8544d-117">Enter the OData service URL for **Service document location**.</span></span> <span data-ttu-id="8544d-118">這可以是服務文件的 URL，或是特定摘要或實體的 URL。</span><span class="sxs-lookup"><span data-stu-id="8544d-118">This can be the URL to the service document, or to a specific feed or entity.</span></span> <span data-ttu-id="8544d-119">基於本教學課程的目的，請輸入 [http://services.odata.org/V3/Northwind/Northwind.svc/](http://services.odata.org/V3/Northwind/Northwind.svc/) 。</span><span class="sxs-lookup"><span data-stu-id="8544d-119">For the purpose of this tutorial, type [http://services.odata.org/V3/Northwind/Northwind.svc/](http://services.odata.org/V3/Northwind/Northwind.svc/).</span></span>  
  
7.  <span data-ttu-id="8544d-120">確認已選取 **[Windows 驗證]** 做為用來存取 OData 服務的 **[驗證]** 。</span><span class="sxs-lookup"><span data-stu-id="8544d-120">Confirm that **Windows Authentication** is selected for the **authentication** to use to access the OData Service.</span></span> <span data-ttu-id="8544d-121">**[Windows 驗證]** 預設為選取狀態。</span><span class="sxs-lookup"><span data-stu-id="8544d-121">**Windows Authentication** is selected by default.</span></span> <span data-ttu-id="8544d-122">若要使用基本驗證，請選取 **[使用此使用者名稱和密碼]**。</span><span class="sxs-lookup"><span data-stu-id="8544d-122">To use basic authentication, select **Use this user name and password**.</span></span>  
  
8.  <span data-ttu-id="8544d-123">針對連接按一下 **[測試連接]** ，然後按一下 **[確定]** 建立 OData 連接管理員的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8544d-123">Click **Test Connection** to the connection, and click **OK** to create an instance of OData Connection Manager.</span></span>  
  
9. <span data-ttu-id="8544d-124">在 **[OData 來源編輯器]** 對話方塊中，確認已針對 **[在資源路徑上使用集合]** 選項選取 **[集合]** 。</span><span class="sxs-lookup"><span data-stu-id="8544d-124">In the **OData Source Editor** Dialog Box, confirm that **Collection** is selected for **Use collection on resource path** option.</span></span>  
  
10. <span data-ttu-id="8544d-125">從 **[集合]** 下拉式清單中選取 **[Employees]**。</span><span class="sxs-lookup"><span data-stu-id="8544d-125">From the **Collection** drop down list, select **Employees**.</span></span>  
  
11. <span data-ttu-id="8544d-126">針對 **[查詢選項]** 輸入任何其他 OData 查詢選項或篩選。</span><span class="sxs-lookup"><span data-stu-id="8544d-126">Enter any additional OData query options or filters for **Query Options**.</span></span> <span data-ttu-id="8544d-127">例如</span><span class="sxs-lookup"><span data-stu-id="8544d-127">Ex.</span></span> <span data-ttu-id="8544d-128">$orderby=CompanyName&$top=100。</span><span class="sxs-lookup"><span data-stu-id="8544d-128">$orderby=CompanyName&$top=100.</span></span> <span data-ttu-id="8544d-129">針對本教學課程的用途，輸入 **$top=5**。</span><span class="sxs-lookup"><span data-stu-id="8544d-129">For the purpose of this tutorial, enter **$top=5**.</span></span>  
  
12. <span data-ttu-id="8544d-130">按一下 **[預覽]** 預覽資料。</span><span class="sxs-lookup"><span data-stu-id="8544d-130">Click **Preview** to preview the data.</span></span>  
  
13. <span data-ttu-id="8544d-131">按一下左側功能窗格中的 **[資料行]** ，切換至 **[資料行]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="8544d-131">Click **Columns** in the left navigation pane to switch to the **Columns** page.</span></span>  
  
14. <span data-ttu-id="8544d-132">透過選取核取方塊的方式，從 **[可用的外部資料行]** 選取 **[EmployeeID]**、 **[FirstName]** 和 **[LastName]** 。</span><span class="sxs-lookup"><span data-stu-id="8544d-132">Select **EmployeeID**, **FirstName**, and **LastName** from **Available External Columns** by checking the check boxes.</span></span>  
  
15. <span data-ttu-id="8544d-133">按一下 **[確定]** ，關閉 **[OData 來源編輯器]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8544d-133">Click **OK** to close the **OData Source Editor** dialog box.</span></span>  
  
## <a name="3-add-flat-file-destination-and-test-the-solution"></a><span data-ttu-id="8544d-134">3.加入一般檔案目的地並測試方案</span><span class="sxs-lookup"><span data-stu-id="8544d-134">3. Add Flat File Destination and Test the Solution</span></span>  
  
1.  <span data-ttu-id="8544d-135">現在，從 [SSIS 工具箱]\*\*\*\* 將 [一般檔案目的地]\*\*\*\* 拖放至 [OData 來源]\*\*\*\* 元件下方的資料流程設計介面。</span><span class="sxs-lookup"><span data-stu-id="8544d-135">Now, drag-drop a **Flat File Destination** from **SSIS Toolbox** to the Data Flow design surface below the **OData Source** component.</span></span>  
  
2.  <span data-ttu-id="8544d-136">使用藍色箭頭連接 **[OData 來源]** 元件與 **[一般檔案目的地]** 元件。</span><span class="sxs-lookup"><span data-stu-id="8544d-136">Connect **OData Source** component with the **Flat File Destination** component using blue arrow.</span></span>  
  
3.  <span data-ttu-id="8544d-137">按兩下 [一般檔案目的地]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8544d-137">Double-click on **Flat File Destination**.</span></span> <span data-ttu-id="8544d-138">**[一般檔案目的地編輯器]** 對話方塊應會隨即出現。</span><span class="sxs-lookup"><span data-stu-id="8544d-138">You should see the **Flat File Destination Editor** dialog box.</span></span>  
  
4.  <span data-ttu-id="8544d-139">在 **[一般檔案目的地編輯器]** 對話方塊中，按一下 **[新增]** 建立新的一般檔案連接管理員。</span><span class="sxs-lookup"><span data-stu-id="8544d-139">In the **Flat File Destination Editor** dialog box, click **New** to create a new flat file connection manager.</span></span>  
  
5.  <span data-ttu-id="8544d-140">在 **[一般檔案格式]** 對話方塊中，選取 **[使用分隔符號]**。</span><span class="sxs-lookup"><span data-stu-id="8544d-140">In the **Flat File Format** dialog box, select **Delimited**.</span></span> <span data-ttu-id="8544d-141">**[一般檔案連接管理員編輯器]** 對話方塊應會隨即出現。</span><span class="sxs-lookup"><span data-stu-id="8544d-141">You should see the **Flat File Connection Manager Editor** dialog box.</span></span>  
  
6.  <span data-ttu-id="8544d-142">在 [一般檔案連線管理員編輯器]\*\*\*\* 對話方塊中，輸入 **c:\Employees.txt** 作為 [檔案名稱]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8544d-142">In the **Flat File Connection Manager Editor** dialog box, for the **File name**, enter **c:\Employees.txt**.</span></span>  
  
7.  <span data-ttu-id="8544d-143">在左側功能窗格中，按一下 **[資料行]**。</span><span class="sxs-lookup"><span data-stu-id="8544d-143">In the left navigation pane, click **Columns**.</span></span> <span data-ttu-id="8544d-144">您可以在此頁面上預覽資料。</span><span class="sxs-lookup"><span data-stu-id="8544d-144">You can preview the data on this page.</span></span>  
  
8.  <span data-ttu-id="8544d-145">按一下 [確定]，關閉 **[一般檔案連接管理員編輯器]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8544d-145">Click OK to close the **Flat File Connection Manager** Editor dialog box.</span></span>  
  
9. <span data-ttu-id="8544d-146">在 **[一般檔案目的地編輯器]** 對話方塊中，按一下左邊功能窗格中的 **[對應]** 。</span><span class="sxs-lookup"><span data-stu-id="8544d-146">In the **Flat File Destination Editor** dialog box, click **Mappings** in the left navigation pane.</span></span> <span data-ttu-id="8544d-147">檢閱對應。</span><span class="sxs-lookup"><span data-stu-id="8544d-147">Review the mappings.</span></span>  
  
10. <span data-ttu-id="8544d-148">按一下 [確定]，關閉 **[一般檔案目的地編輯器]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8544d-148">Click OK to close the **Flat File Destination Editor** dialog box.</span></span>  
  
11. <span data-ttu-id="8544d-149">編譯並執行 SSIS 封裝。</span><span class="sxs-lookup"><span data-stu-id="8544d-149">Compile and execute the SSIS package.</span></span> <span data-ttu-id="8544d-150">確認建立的輸出檔包含 OData 摘要中 5 位員工的 [識別碼]、[名字] 和 [姓氏]。</span><span class="sxs-lookup"><span data-stu-id="8544d-150">Verify that the output file is created with ID, First Name, and Last Name for 5 employees from the OData feed.</span></span>  
  
  
