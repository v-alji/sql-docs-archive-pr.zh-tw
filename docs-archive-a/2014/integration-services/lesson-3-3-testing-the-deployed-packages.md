---
title: 步驟 3：測試已部署的套件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9159da3f-c9ca-4015-9e85-3bf4373a1349
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d11ae071d97d9fdadec6ee144813c91519b54ea4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595184"
---
# <a name="step-3-testing-the-deployed-packages"></a><span data-ttu-id="7ed1e-102">步驟 3：測試部署的封裝</span><span class="sxs-lookup"><span data-stu-id="7ed1e-102">Step 3: Testing the Deployed Packages</span></span>
  <span data-ttu-id="7ed1e-103">在這項工作中，您會測試已部署到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]執行個體的封裝。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-103">In this task, you will test the packages that you deployed to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>

 <span data-ttu-id="7ed1e-104">在其他 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 教學課程中，則是使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)][偵錯] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]功能表上的 **[開始偵錯]** 選項，在 **(** 的開發環境) 中執行封裝。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-104">In other [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] tutorials, you ran packages in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the development environment for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], using the **Start Debugging** option on the **Debug** menu.</span></span> <span data-ttu-id="7ed1e-105">這時將會以不同的方式執行封裝。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-105">This time you will run the packages differently.</span></span>

 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="7ed1e-106">提供了幾項工具，您可以用來在測試和實際執行環境中執行封裝，這些工具為：命令提示字元公用程式 `dtexec` 和「執行封裝公用程式」。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-106">provides several tools that you can use to run packages in the test and production environment: the command prompt utility `dtexec` and the Execute Package Utility.</span></span> <span data-ttu-id="7ed1e-107">「執行封裝公用程式」是以 `dtexec` 為基礎所建立的圖形化工具。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-107">The Execute Package Utility is a graphical tool that is built on `dtexec`.</span></span> <span data-ttu-id="7ed1e-108">這兩項工具都會立即執行封裝。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-108">Both of these tools execute the package immediately.</span></span> <span data-ttu-id="7ed1e-109">此外， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 還提供了 SQL Server Agent 的子系統，這套子系統是特別設計的，它會將封裝執行排程為 SQL Server Agent 作業中的一個步驟。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-109">In addition, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provides a subsystem of SQL Server Agent that is especially designed for scheduling package execution as a step in a SQL Server Agent job.</span></span>

 <span data-ttu-id="7ed1e-110">您將會使用「執行封裝公用程式」來執行部署的封裝。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-110">You will use the Execute Package Utility to run the deployed packages.</span></span> <span data-ttu-id="7ed1e-111">封裝將會直接使用，因此，您不必更新對話方塊中任何頁面上的資訊。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-111">The packages will be used as is; therefore, you do not have to update information on any pages in the dialog box.</span></span> <span data-ttu-id="7ed1e-112">您將會從 [一般] 頁面開始執行封裝，這也就是「執行封裝公用程式」的第一個頁面。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-112">You will run the packages from the General page, which is the first page in the Execute Package Utility.</span></span> <span data-ttu-id="7ed1e-113">如果需要，可以按一下其他頁面，以查看頁面中所包含的各封裝資訊。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-113">If you like, you can click the other pages too see the information that they contain for each package.</span></span>

> [!NOTE]
>  <span data-ttu-id="7ed1e-114">為了確保封裝能夠在這個教學課程的內容中順利執行，請不要修改任何選項。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-114">To ensure that the packages run successfully in the context of this tutorial, you should not modify any options.</span></span>

 <span data-ttu-id="7ed1e-115">使用「執行封裝公用程式」在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中執行封裝之前，請確定 Integration Services 服務正在執行中。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-115">Before you run packages in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] by using the Execute Package Utility, ensure that the Integration Services service is running.</span></span> <span data-ttu-id="7ed1e-116">Integration Services 服務可提供封裝儲存體和執行的支援。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-116">The Integration Services service provides support for package storage and execution.</span></span> <span data-ttu-id="7ed1e-117">如果停止服務，就無法連接到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ，而且 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 不會列出要執行的封裝。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-117">If the service is stopped, you cannot connect to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] does not list the packages to run.</span></span> <span data-ttu-id="7ed1e-118">此外，您還必須具有在部署封裝的執行個體上執行封裝的權限。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-118">You also must have permissions to run the package on the instance where the package has been deployed.</span></span> <span data-ttu-id="7ed1e-119">如需詳細資訊，請參閱 [Integration Services 角色 &#40;SSIS 服務&#41;](security/integration-services-roles-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-119">For more information, see [Integration Services Roles &#40;SSIS Service&#41;](security/integration-services-roles-ssis-service.md).</span></span>

 <span data-ttu-id="7ed1e-120">[存放的封裝] 資料夾內的最上層資料夾是使用者定義的資料夾，Integration Services 服務會加以監視。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-120">The top-level folders within the Stored Packages folder are the user-defined folders that Integration Services service monitors.</span></span> <span data-ttu-id="7ed1e-121">您可以依照需要，在 MsDtsSrvr.ini.xml 檔案中指定任意個資料夾。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-121">You can specify as many or few folders in the MsDtsSrvr.ini.xml file as you want.</span></span> <span data-ttu-id="7ed1e-122">這個教學課程會假設您要使用預設的 MsDtsSrvr.ini.xml 檔案，而且 [存放的封裝] 資料夾內最上層資料夾的名稱分別為 File System 和 MSDB。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-122">This tutorial assumes that you are using the default MsDtsSrvr.ini.xml file, and that the names of the top-level folders within Stored Packages are File System and MSDB.</span></span>

### <a name="to-connect-to-integration-services-in-sql-server-management-studio"></a><span data-ttu-id="7ed1e-123">若要在 SQL Server Management Studio 中連接到 Integration Services</span><span class="sxs-lookup"><span data-stu-id="7ed1e-123">To connect to Integration Services in SQL Server Management Studio</span></span>

1.  <span data-ttu-id="7ed1e-124">按一下 **[開始]** ，依序指向 **[所有程式]** 和 **[Microsoft SQL Server]** ，然後按一下 **[SQL Server Management Studio]** 。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-124">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Management Studio**.</span></span>

2.  <span data-ttu-id="7ed1e-125">在 **[連接到伺服器]** 對話方塊中，從 **[伺服器類型]** 清單中選取 **[Integration Services]** ，並在 **[伺服器名稱]** 方塊中提供伺服器名稱，然後按一下 **[連接]** 。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-125">In the **Connect to Server** dialog box, select **Integration Services** in the **Server type** list, provide a server name in the **Server name** box, and click **Connect**.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="7ed1e-126">如果您無法連接到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務目前可能沒有執行。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-126">If you cannot connect to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is likely not running.</span></span> <span data-ttu-id="7ed1e-127">若要了解此服務的狀態，請按一下 **[開始]** ，依序指向 **[所有程式]** 、 **[Microsoft SQL Server]** 和 **[組態工具]** ，然後按一下 **[SQL Server 組態管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-127">To learn the status of the service, click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span> <span data-ttu-id="7ed1e-128">在左窗格中，按一下 **[SQL Server 服務]** 。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-128">In the left pane, click **SQL Server Services**.</span></span> <span data-ttu-id="7ed1e-129">在右窗格中，尋找 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-129">In the right pane, find the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="7ed1e-130">如果此服務尚未執行，請將它啟動。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-130">Start the service if it is not already running.</span></span>

     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="7ed1e-131">隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-131">opens.</span></span> <span data-ttu-id="7ed1e-132">依預設，[物件總管] 視窗會開啟並放置在 SQL Server Management Studio 的右上角。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-132">By default the Object Explorer window is open and placed in the upper right corner of the studio.</span></span> <span data-ttu-id="7ed1e-133">如果 [物件總管] 未開啟，請按一下 **[檢視]** 功能表上的 **[物件總管]** 。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-133">If Object Explorer is not open, click **Object Explorer** on the **View** menu.</span></span>

### <a name="to-run-the-packages-using-the-execute-package-utility"></a><span data-ttu-id="7ed1e-134">若要使用執行封裝公用程式來執行封裝</span><span class="sxs-lookup"><span data-stu-id="7ed1e-134">To run the packages using the Execute Package Utility</span></span>

1.  <span data-ttu-id="7ed1e-135">在 [物件總管] 中，展開 [存放的封裝] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-135">In Object Explorer, expand the Stored Packages folder.</span></span>

2.  <span data-ttu-id="7ed1e-136">展開 [MSDB] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-136">Expand the MSDB folder.</span></span> <span data-ttu-id="7ed1e-137">由於您已將封裝部署到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，因此所有部署的封裝都會存放在 msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫中，而且所有部署的封裝都會出現在 MSDB 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-137">Because you deployed the packages to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], all the deployed packages are stored in the msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database, and all deployed packages appear in the MSDB folder.</span></span> <span data-ttu-id="7ed1e-138">除非您已將封裝部署到「部署教學課程」以外的檔案系統中，否則 [File System] 資料夾應該是空的。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-138">The File System folder is empty, unless you have deployed packages to the file system outside of the Deployment Tutorial.</span></span>

3.  <span data-ttu-id="7ed1e-139">從封裝清單的最上方開始，以滑鼠右鍵按一下 [DataTransfer]，然後按一下 **[執行封裝]** 。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-139">Starting at the top of the package list, right-click DataTransfer, and click **Run Package**.</span></span>

4.  <span data-ttu-id="7ed1e-140">在 **[執行封裝公用程式]** 對話方塊中，按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-140">In the **Execute Package Utility** dialog box, click **Execute**.</span></span>

5.  <span data-ttu-id="7ed1e-141">在 **[執行封裝公用程式]** 對話方塊中，檢視封裝的執行進度和執行結果。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-141">In the **Execute Package Utility** dialog box, view the progress and execution results of the package.</span></span> <span data-ttu-id="7ed1e-142">當 **[停止]** 按鈕變成無法使用的狀態時，即表示封裝已完成，請按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-142">When the **Stop** button becomes unavailable, which indicates that the package has completed, click **Close**.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="7ed1e-143">如果在封裝執行中按一下 **[停止]** ，封裝將無法完成。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-143">If you click **Stop** while the package is running, the package will not finish.</span></span>

6.  <span data-ttu-id="7ed1e-144">在 **[執行封裝公用程式]** 對話方塊中，按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-144">In the **Execute Package Utility** dialog box, click **Close**.</span></span>

7.  <span data-ttu-id="7ed1e-145">針對 LoadXML 封裝，重複步驟 3 到 6。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-145">Repeat steps 3 - 6 for the LoadXML package.</span></span>

8.  <span data-ttu-id="7ed1e-146">在 **[檔案]** 功能表上按一下 **[結束]** 。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-146">On the **File** menu, click **Exit**.</span></span>

### <a name="to-verify-the-results-of-the-datatransfer-package"></a><span data-ttu-id="7ed1e-147">若要確認 DataTransfer 封裝的結果</span><span class="sxs-lookup"><span data-stu-id="7ed1e-147">To verify the results of the DataTransfer package</span></span>

1.  <span data-ttu-id="7ed1e-148">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中的工具列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-148">On the toolbar in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], click **New Query**.</span></span>

2.  <span data-ttu-id="7ed1e-149">在 **[連接到伺服器]** 對話方塊中，從 **[伺服器類型]** 清單中選取 **[Database Engine]** ，並在 **[伺服器名稱]** 方塊中提供安裝教學課程封裝所在的伺服器名稱或是輸入 (local)，然後選取驗證模式。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-149">In the **Connect to Server** dialog box, select **Database Engine** in the **Server type** list, provide the name of the server name on which you installed the tutorial packages or type (local) in the **Server name** box, and select an authentication mode.</span></span> <span data-ttu-id="7ed1e-150">如果要使用「SQL Server 驗證」，請提供使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-150">If using SQL Server Authentication, provide a user name and password.</span></span>

3.  <span data-ttu-id="7ed1e-151">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-151">Click **Connect**.</span></span>

4.  <span data-ttu-id="7ed1e-152">在查詢視窗中，輸入或貼上下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="7ed1e-152">In the query window, type or paste the following SQL statement:</span></span>

     `USE AdventureWorks`

     `SELECT * FROM HighIncomeCustomers`

5.  <span data-ttu-id="7ed1e-153">按 **F5** ，或按一下工具列上的 [執行] 圖示。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-153">Press **F5** or click the Execute icon on the toolbar.</span></span>

     <span data-ttu-id="7ed1e-154">查詢會傳回 31 個資料列。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-154">The query returns 31 rows of data.</span></span> <span data-ttu-id="7ed1e-155">傳回結果包含文字檔 Customers.txt 中 [YearlyIncome] 資料行值大於 100000 的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-155">The return result contains any rows from the text file, Customers.txt, that have values larger than 100000 in the YearlyIncome column.</span></span>

6.  <span data-ttu-id="7ed1e-156">找到 [DeploymentTutorial] 資料夾，以滑鼠右鍵按一下 XML 記錄檔 Deployment Tutorial Log，然後按一下 [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-156">Locate the DeploymentTutorial folder, right-click the log XML file, Deployment Tutorial Log, and then click **Open**.</span></span> <span data-ttu-id="7ed1e-157">您可以使用「記事本」或其他文字/XML 編輯器來開啟此檔案。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-157">You can open the file by using Notepad or the text/XML editor of choice.</span></span>

### <a name="to-verify-the-results-of-the-loadxmldata-package"></a><span data-ttu-id="7ed1e-158">若要確認 LoadXMLData 封裝的結果</span><span class="sxs-lookup"><span data-stu-id="7ed1e-158">To verify the results of the LoadXMLData package</span></span>

1.  <span data-ttu-id="7ed1e-159">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中的工具列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-159">On the toolbar in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], click **New Query**.</span></span>

2.  <span data-ttu-id="7ed1e-160">如果提示您重新連接，請在 **[連接到伺服器]** 對話方塊中，從 **[伺服器類型]** 清單中選取 **[Database Engine]** ，並在 **[伺服器名稱]** 方塊中提供安裝教學課程封裝所在的伺服器名稱或是輸入 (local)，然後選取驗證模式。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-160">If prompted to connect again, in the **Connect to Server** dialog box, select **Database Engine** in the **Server type** list, provide the name of the server on which you installed the tutorial packages or enter (local) in the **Server name** box, and select an authentication mode.</span></span> <span data-ttu-id="7ed1e-161">如果要使用「SQL Server 驗證」，請提供使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-161">If using SQL Server Authentication, provide a user name and password.</span></span>

3.  <span data-ttu-id="7ed1e-162">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-162">Click **Connect**.</span></span>

4.  <span data-ttu-id="7ed1e-163">在查詢視窗中，輸入或貼上下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="7ed1e-163">In the query window, type or paste the following SQL statement:</span></span>

     `USE AdventureWorks`

     `SELECT * FROM OrderDatesByCountryRegion`

5.  <span data-ttu-id="7ed1e-164">按 **F5** ，或按一下工具列上的 [執行] 圖示。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-164">Press **F5** or click the Execute icon on the toolbar.</span></span>

     <span data-ttu-id="7ed1e-165">查詢會傳回 21 個資料列。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-165">The query returns 21 rows of data.</span></span> <span data-ttu-id="7ed1e-166">傳回結果是由 XML 資料檔 (orders.xml) 中的資料列所組成。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-166">The return result consists of the rows from the XML data file, orders.xml.</span></span> <span data-ttu-id="7ed1e-167">每一個資料列都是依國家/地區排序的摘要；資料列中會列出國家/地區的名稱、每個國家/地區的訂單數目，以及最新和最舊訂單的日期。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-167">Each row is a summary by country/region; the row lists the name of a country/region, the number of orders for each country/region and the dates of the newest and oldest orders.</span></span>

<span data-ttu-id="7ed1e-168">![Integration Services 圖示 (小型) ](media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="7ed1e-168">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="7ed1e-169">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="7ed1e-169">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="7ed1e-170">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="7ed1e-170">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="7ed1e-171">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="7ed1e-171">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ed1e-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ed1e-172">See Also</span></span>
 [<span data-ttu-id="7ed1e-173">dtexec 公用程式</span><span class="sxs-lookup"><span data-stu-id="7ed1e-173">dtexec Utility</span></span>](packages/dtexec-utility.md)


