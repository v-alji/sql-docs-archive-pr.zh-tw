---
title: SSRS 服務應用程式的佈建訂用帳戶及警示 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services Shared Service
- SharePoint Mode [Reporting Services]
- SharePoint Mode
- Reporting Services Service Application
- SSRS service application
ms.assetid: d0de3f1f-4887-47fb-bacf-46aaad74c4be
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9c09033b6a31295b8fbe42058cba9059f5d05629
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710301"
---
# <a name="provision-subscriptions-and-alerts-for-ssrs-service-applications"></a><span data-ttu-id="0d40e-102">SSRS 服務應用程式的佈建訂閱及警示</span><span class="sxs-lookup"><span data-stu-id="0d40e-102">Provision Subscriptions and Alerts for SSRS Service Applications</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="0d40e-103">訂閱和資料警示需要 SQL Server Agent，並且需要 SQL Server Agent 的權限組態。</span><span class="sxs-lookup"><span data-stu-id="0d40e-103">subscriptions and data alerts require SQL Server Agent and require the configuration of permissions for SQL Server Agent.</span></span> <span data-ttu-id="0d40e-104">如果您看到錯誤訊息指出需要 SQL Server Agent，而您已確認 SQL Server Agent 正在執行，則請更新或驗證權限。</span><span class="sxs-lookup"><span data-stu-id="0d40e-104">If you see error messages that indicate SQL Server Agent is required and you have verified SQL Server Agent is running, then update or verify permissions.</span></span> <span data-ttu-id="0d40e-105">本主題的範圍是 SharePoint 模式的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，且本主題說明三種可以用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 訂閱來更新 SQL Server Agent 權限的方法。</span><span class="sxs-lookup"><span data-stu-id="0d40e-105">The scope of this topic is [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode and the topic describes three ways you can update the permissions of SQL Server Agent with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscriptions.</span></span> <span data-ttu-id="0d40e-106">在本主題中用來執行步驟的認證必須要有足夠的權限，才能針對服務應用程式、msdb 和 master 資料庫中的物件授與 RSExecRole 的執行權限。</span><span class="sxs-lookup"><span data-stu-id="0d40e-106">The credentials you use for the steps in this topic need to have sufficient permissions to grant execute permissions to the RSExecRole for objects in the service application, msdb, and master databases.</span></span>

||
|-|
|<span data-ttu-id="0d40e-107">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="0d40e-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010</span></span>|

 <span data-ttu-id="0d40e-108">![對於服務應用程式資料庫的 SQL Agent 權限](../../../2014/sql-server/install/media/rs-provisionsqlagent.gif "對於服務應用程式資料庫的 SQL Agent 權限")</span><span class="sxs-lookup"><span data-stu-id="0d40e-108">![SQL Agent permissions to Service Application DBs](../../../2014/sql-server/install/media/rs-provisionsqlagent.gif "SQL Agent permissions to Service Application DBs")</span></span>

||<span data-ttu-id="0d40e-109">描述</span><span class="sxs-lookup"><span data-stu-id="0d40e-109">Description</span></span>|
|------|-----------------|
|<span data-ttu-id="0d40e-110">**1**</span><span class="sxs-lookup"><span data-stu-id="0d40e-110">**1**</span></span>|<span data-ttu-id="0d40e-111">主控 Reporting Services 服務應用程式資料庫的 SQL Server Database Engine 執行個體。</span><span class="sxs-lookup"><span data-stu-id="0d40e-111">The instance of SQL Server Database engine that is hosting the Reporting Services service application databases.</span></span>|
|<span data-ttu-id="0d40e-112">**2**</span><span class="sxs-lookup"><span data-stu-id="0d40e-112">**2**</span></span>|<span data-ttu-id="0d40e-113">SQL Database Engine 執行個體的 SQL Server Agent 執行個體。</span><span class="sxs-lookup"><span data-stu-id="0d40e-113">The instance of SQL Server agent for the instance of the SQL database engine.</span></span>|
|<span data-ttu-id="0d40e-114">**3**</span><span class="sxs-lookup"><span data-stu-id="0d40e-114">**3**</span></span>|<span data-ttu-id="0d40e-115">Reporting Services 服務應用程式資料庫。</span><span class="sxs-lookup"><span data-stu-id="0d40e-115">The Reporting Services service application databases.</span></span> <span data-ttu-id="0d40e-116">這些名稱會以用於建立服務應用程式的資訊為基礎。</span><span class="sxs-lookup"><span data-stu-id="0d40e-116">The names are based on the information used for creating the service application.</span></span> <span data-ttu-id="0d40e-117">以下是範例資料庫名稱：</span><span class="sxs-lookup"><span data-stu-id="0d40e-117">The following are example database names:</span></span><br /><br /> <span data-ttu-id="0d40e-118">ReportingService_2fbae157295d49df86d0b85760c704b0</span><span class="sxs-lookup"><span data-stu-id="0d40e-118">ReportingService_2fbae157295d49df86d0b85760c704b0</span></span><br /><br /> <span data-ttu-id="0d40e-119">ReportingService_2fbae157295d49df86d0b85760c704b0_Alerting</span><span class="sxs-lookup"><span data-stu-id="0d40e-119">ReportingService_2fbae157295d49df86d0b85760c704b0_Alerting</span></span><br /><br /> <span data-ttu-id="0d40e-120">ReportingService_2fbae157295d49df86d0b85760c704b0TempDB</span><span class="sxs-lookup"><span data-stu-id="0d40e-120">ReportingService_2fbae157295d49df86d0b85760c704b0TempDB</span></span>|
|<span data-ttu-id="0d40e-121">**4**</span><span class="sxs-lookup"><span data-stu-id="0d40e-121">**4**</span></span>|<span data-ttu-id="0d40e-122">SQL Server Database Engine 執行個體的 master 和 MSDB 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0d40e-122">The master and MSDB database of the instance of the SQL Server Database engine.</span></span>|

 <span data-ttu-id="0d40e-123">使用下列三種方法之一來更新權限：</span><span class="sxs-lookup"><span data-stu-id="0d40e-123">Use one the following three methods to update the permissions:</span></span>

1.  <span data-ttu-id="0d40e-124">從 [條款、訂閱和警示]  頁面上鍵入認證，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="0d40e-124">From the **Provisions and Subscriptions and Alerts** page, type credentials and click **ok**.</span></span>

2.  <span data-ttu-id="0d40e-125">從 [提供訂閱和警示] 頁面按一下 [下載指令碼]  按鈕，下載可用來設定權限的 Transact SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="0d40e-125">From the Provisions and Subscriptions and Alerts page, click the **Download Script** button to download a transact SQL script that can be used to configure permissions.</span></span>

3.  <span data-ttu-id="0d40e-126">執行 PowerShell Cmdlet，以建立可用來設定權限的 Transact-SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="0d40e-126">Run a PowerShell cmdlet to build a transact SQL script that can be used to configure permissions.</span></span>

### <a name="to-update-permissions-using-the-provision-page"></a><span data-ttu-id="0d40e-127">若要使用佈建頁面更新權限</span><span class="sxs-lookup"><span data-stu-id="0d40e-127">To update permissions using the provision page</span></span>

1.  <span data-ttu-id="0d40e-128">從 SharePoint 管理中心，按一下 [應用程式管理]  群組中的 [管理服務應用程式]  。</span><span class="sxs-lookup"><span data-stu-id="0d40e-128">From SharePoint Central Administration, in the **Application Management** group click **Manage Service Applications**</span></span>

2.  <span data-ttu-id="0d40e-129">在清單中尋找服務應用程式，並按一下應用程式的名稱，或按一下 [類型]  欄選取服務應用程式，然後按一下 SharePoint 功能區中的 [管理]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="0d40e-129">Find your service application in the list and click the name of the application or click the **Type** column to select the services application and click the **Manage** button in the SharePoint ribbon.</span></span>

3.  <span data-ttu-id="0d40e-130">在 [管理 Reporting Services 應用程式]  頁面上，按一下 [提供訂閱和警示]  。</span><span class="sxs-lookup"><span data-stu-id="0d40e-130">On the **Manage Reporting Services Application** page, click **Provision Subscriptions and Alerts**.</span></span>

4.  <span data-ttu-id="0d40e-131">如果 SharePoint 管理員對 Master 資料庫和服務應用程式資料庫有足夠的權限，請輸入這些認證。</span><span class="sxs-lookup"><span data-stu-id="0d40e-131">If the SharePoint administrator has enough privileges to the Master database and the service application databases, type those credentials.</span></span>

5.  <span data-ttu-id="0d40e-132">按一下 [確定]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="0d40e-132">Click the **OK** button.</span></span>

##  <a name="to-download-the-transact-sql-script"></a><a name="bkmk_download"></a> <span data-ttu-id="0d40e-133">下載 Transact-SQL 指令碼</span><span class="sxs-lookup"><span data-stu-id="0d40e-133">To download the Transact-SQL Script</span></span>

1.  <span data-ttu-id="0d40e-134">從 SharePoint 管理中心，按一下 [應用程式管理]  群組中的 [管理服務應用程式]  。</span><span class="sxs-lookup"><span data-stu-id="0d40e-134">From SharePoint Central Administration, in the **Application Management** group click **Manage Service Applications**</span></span>

2.  <span data-ttu-id="0d40e-135">在清單中尋找服務應用程式，並按一下應用程式的名稱，或按一下 [類型]  欄選取服務應用程式，然後按一下 SharePoint 功能區中的 [管理]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="0d40e-135">Find your service application in the list and click the name of the application or click the **Type** column to select the services application and click the **Manage** button in the SharePoint ribbon.</span></span>

3.  <span data-ttu-id="0d40e-136">在 [管理 Reporting Services 應用程式]  頁面上，按一下 [提供訂閱和警示]  。</span><span class="sxs-lookup"><span data-stu-id="0d40e-136">On the **Manage Reporting Services Application** page, click **Provision Subscriptions and Alerts**.</span></span>

4.  <span data-ttu-id="0d40e-137">在 [檢視狀態]  區域中，確認 SQL Server Agent 正在執行。</span><span class="sxs-lookup"><span data-stu-id="0d40e-137">In the **View Status** area, verify SQL Server Agent is running.</span></span>

5.  <span data-ttu-id="0d40e-138">按一下 [下載指令碼]  ，下載您可以在 SQL Server Management Studio 中執行以授與權限的 Transact-SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="0d40e-138">Click **Download Script** to download a transact SQL script you can run in SQL Server Management studio to grant permissions.</span></span> <span data-ttu-id="0d40e-139">建立的指令碼檔案名稱會包含 Reporting Services 服務應用程式的名稱，例如 **[服務應用程式的名稱]-GrantRights.sql**。</span><span class="sxs-lookup"><span data-stu-id="0d40e-139">The script file name that is created will contain the name of your Reporting Services service application name, for example **[name of the service application]-GrantRights.sql**.</span></span>

### <a name="to-generate-the-transact-sql-statement-with-powershell"></a><span data-ttu-id="0d40e-140">使用 PowerShell 產生 Transact-SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="0d40e-140">To generate the Transact-SQL statement with PowerShell</span></span>

1.  <span data-ttu-id="0d40e-141">您也可以在 SharePoint 2010 管理命令介面中使用 Windows PowerShell Cmdlet 建立 Transact-SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="0d40e-141">You can also use a Windows PowerShell cmdlet in the SharePoint 2010 Management Shell to create the Transact-SQL script.</span></span>

2.  <span data-ttu-id="0d40e-142">在 [開始]  功能表上，按一下 [所有程式]  。</span><span class="sxs-lookup"><span data-stu-id="0d40e-142">On the **Start** menu, click **All Programs**.</span></span>

3.  <span data-ttu-id="0d40e-143">展開 [ **Microsoft SharePoint 2010 產品**]，然後按一下 [ **SharePoint 2010 管理命令**介面]。</span><span class="sxs-lookup"><span data-stu-id="0d40e-143">Expand **Microsoft SharePoint 2010 Products** and click **SharePoint 2010 Management Shell**.</span></span>

4.  <span data-ttu-id="0d40e-144">透過取代報表伺服器資料庫的名稱、應用程式集區帳戶及陳述式的路徑，來更新下列 PowerShell Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0d40e-144">Update the following PowerShell cmdlet by replacing the name of the report server database, application pool account, and the path of the statement.</span></span>

     <span data-ttu-id="0d40e-145">**Cmdlet 的語法：** `Get-SPRSDatabaseRightsScript -DatabaseName <ReportingServices database name> -UserName <app pool account> -IsWindowsUser | Out-File <path of statement>`</span><span class="sxs-lookup"><span data-stu-id="0d40e-145">**Syntax of cmdlet:** `Get-SPRSDatabaseRightsScript -DatabaseName <ReportingServices database name> -UserName <app pool account> -IsWindowsUser | Out-File <path of statement>`</span></span>

     <span data-ttu-id="0d40e-146">**範例 Cmdlet：** `Get-SPRSDatabaseRightsScript -DatabaseName ReportingService_46fd00359f894b828907b254e3f6257c -UserName "NT AUTHORITY\NETWORK SERVICE" -IsWindowsUser | Out-File c:\SQLServerAgentrights.sql`</span><span class="sxs-lookup"><span data-stu-id="0d40e-146">**Sample cmdlet:** `Get-SPRSDatabaseRightsScript -DatabaseName ReportingService_46fd00359f894b828907b254e3f6257c -UserName "NT AUTHORITY\NETWORK SERVICE" -IsWindowsUser | Out-File c:\SQLServerAgentrights.sql`</span></span>

## <a name="using-the-transact-sql-script"></a><span data-ttu-id="0d40e-147">使用 Transact-SQL 指令碼</span><span class="sxs-lookup"><span data-stu-id="0d40e-147">Using the Transact-SQL Script</span></span>
 <span data-ttu-id="0d40e-148">下列程序可搭配從佈建頁面下載的指令碼，或透過 PowerShell 建立的指令碼使用。</span><span class="sxs-lookup"><span data-stu-id="0d40e-148">The following procedures can be used with scripts download from the provisions page or scripts created using PowerShell.</span></span>

#### <a name="to-load-the-transact-sql-script-in-sql-server-management-studio"></a><span data-ttu-id="0d40e-149">在 SQL Server Management Studio 中載入 Transact-SQL 指令碼</span><span class="sxs-lookup"><span data-stu-id="0d40e-149">To load the Transact-SQL script in SQL Server Management Studio</span></span>

1.  <span data-ttu-id="0d40e-150">若要開啟 SQL Server Management Studio，請在 [**開始**] 功能表上，按一下 [ **Microsoft SQL Server 2012** ，然後按一下 [ **SQL Server Management Studio**]。</span><span class="sxs-lookup"><span data-stu-id="0d40e-150">To open SQL Server Management Studio, on the **Start** menu, click **Microsoft SQL Server 2012** and click **SQL Server Management Studio**.</span></span>

2.  <span data-ttu-id="0d40e-151">在 [連接到伺服器]  對話方塊上，設定下列選項：</span><span class="sxs-lookup"><span data-stu-id="0d40e-151">In the **Connect to Server** dialog box set the following options:</span></span>

    -   <span data-ttu-id="0d40e-152">在 [伺服器類型]  清單中，選取 [資料庫引擎] </span><span class="sxs-lookup"><span data-stu-id="0d40e-152">In the **Server type** list, select **Database Engine**</span></span>

    -   <span data-ttu-id="0d40e-153">在 [伺服器名稱]  中，鍵入您要設定 SQL Server Agent 的 SQL Server 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="0d40e-153">In **Server Name**, type the name of the SQL Server instance on which you want to configure SQL Server Agent.</span></span>

    -   <span data-ttu-id="0d40e-154">選取驗證模式。</span><span class="sxs-lookup"><span data-stu-id="0d40e-154">Select an authentication mode.</span></span>

    -   <span data-ttu-id="0d40e-155">如果使用 SQL Server 驗證連接，請提供登入和密碼。</span><span class="sxs-lookup"><span data-stu-id="0d40e-155">If connecting using SQL Server Authentication, provide a login and password.</span></span>

3.  <span data-ttu-id="0d40e-156">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="0d40e-156">Click **Connect**.</span></span>

#### <a name="to-run-the-transact-sql-statement"></a><span data-ttu-id="0d40e-157">執行 Transact-SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="0d40e-157">To run the Transact-SQL statement</span></span>

1.  <span data-ttu-id="0d40e-158">在 SQL Server Management Studio 的工具列上，按一下 [新增查詢]  。</span><span class="sxs-lookup"><span data-stu-id="0d40e-158">On the toolbar of SQL Server Management Studio, click **New Query**.</span></span>

2.  <span data-ttu-id="0d40e-159">在 [檔案]  功能表上，按一下 [開啟]  ，然後按一下 [檔案]  。</span><span class="sxs-lookup"><span data-stu-id="0d40e-159">On the **File** menu, click **Open**, and then click **File**.</span></span>

3.  <span data-ttu-id="0d40e-160">瀏覽至您在 SharePoint 2010 管理命令介面中產生之 Transact-SQL 陳述式的儲存所在資料夾。</span><span class="sxs-lookup"><span data-stu-id="0d40e-160">Navigate to the folder where you saved the Transact-SQL statement that you generated in SharePoint 2010 Management Shell.</span></span>

4.  <span data-ttu-id="0d40e-161">按一下檔案，然後按一下 [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="0d40e-161">Click the file and then click **Open**.</span></span>

     <span data-ttu-id="0d40e-162">陳述式隨即會加入查詢視窗。</span><span class="sxs-lookup"><span data-stu-id="0d40e-162">The statement is added to the query window.</span></span>

5.  <span data-ttu-id="0d40e-163">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="0d40e-163">Click **Execute**.</span></span>


