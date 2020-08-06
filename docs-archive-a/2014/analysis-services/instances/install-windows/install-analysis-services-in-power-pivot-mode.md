---
title: PowerPivot for SharePoint 2013 安裝 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: d3310562-82c1-454f-9c48-33a241749238
author: minewiskan
ms.author: owend
ms.openlocfilehash: 74d0e1cc78b4004a832a312f9f8ae8deb23904f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688350"
---
# <a name="powerpivot-for-sharepoint-2013-installation"></a><span data-ttu-id="75766-102">PowerPivot for SharePoint 2013 安裝</span><span class="sxs-lookup"><span data-stu-id="75766-102">PowerPivot for SharePoint 2013 Installation</span></span>
  <span data-ttu-id="75766-103">本主題中的程序會引導您完成 SharePoint 部署模式之 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 伺服器的單一伺服器安裝。</span><span class="sxs-lookup"><span data-stu-id="75766-103">The procedures in this topic guide you through a single server installation of a [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint deployment mode.</span></span> <span data-ttu-id="75766-104">這些步驟包含執行 [SQL Server 安裝精靈]，以及使用 SharePoint 2013 管理中心的設定工作。</span><span class="sxs-lookup"><span data-stu-id="75766-104">The steps include running the SQL Server installation wizard as well as configuration tasks that use SharePoint 2013 Central Administration.</span></span>  
  
 <span data-ttu-id="75766-105">**[!INCLUDE[applies](../../../includes/applies-md.md)]** SharePoint 2013 |SharePoint 201</span><span class="sxs-lookup"><span data-stu-id="75766-105">**[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 201</span></span>  
  
 <span data-ttu-id="75766-106">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="75766-106">**In this topic:**</span></span>  
  
 [<span data-ttu-id="75766-107">背景</span><span class="sxs-lookup"><span data-stu-id="75766-107">Background</span></span>](#bkmk_background)  
  
 [<span data-ttu-id="75766-108">先決條件</span><span class="sxs-lookup"><span data-stu-id="75766-108">Prerequisites</span></span>](#bkmk_prereq)  
  
 [<span data-ttu-id="75766-109">步驟 1：安裝 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="75766-109">Step 1: Install PowerPivot for SharePoint</span></span>](#InstallSQL)  
  
 [<span data-ttu-id="75766-110">步驟 2：設定基本 Analysis Services SharePoint 整合</span><span class="sxs-lookup"><span data-stu-id="75766-110">Step 2: Configure Basic Analysis Services SharePoint Integration</span></span>](#bkmk_config)  
  
 [<span data-ttu-id="75766-111">步驟 3：確認整合</span><span class="sxs-lookup"><span data-stu-id="75766-111">Step 3: Verify the Integration</span></span>](#bkmk_verify)  
  
 [<span data-ttu-id="75766-112">設定 Windows 防火牆以允許 Analysis Services 存取</span><span class="sxs-lookup"><span data-stu-id="75766-112">Configure the Windows Firewall to Allow Analysis Services Access</span></span>](#bkmk_firewall)  
  
 [<span data-ttu-id="75766-113">升級活頁簿和排程的資料重新整理</span><span class="sxs-lookup"><span data-stu-id="75766-113">Upgrade Workbooks and Scheduled Data Refresh</span></span>](#bkmk_upgrade_workbook)  
  
 [<span data-ttu-id="75766-114">超越單一伺服器安裝-PowerPivot for Microsoft SharePoint</span><span class="sxs-lookup"><span data-stu-id="75766-114">Beyond the Single-Server Installation -PowerPivot for Microsoft SharePoint</span></span>](#bkmk_multiple_servers)  
  
##  <a name="background"></a><a name="bkmk_background"></a> <span data-ttu-id="75766-115">背景</span><span class="sxs-lookup"><span data-stu-id="75766-115">Background</span></span>  
 <span data-ttu-id="75766-116">PowerPivot for SharePoint 是中間層及後端服務的集合，可以在 SharePoint 2013 伺服器陣列中提供 PowerPivot 資料存取功能。</span><span class="sxs-lookup"><span data-stu-id="75766-116">PowerPivot for SharePoint is a collection of middle-tier and backend services that provide PowerPivot data access in a SharePoint 2013 farm.</span></span>  
  
-   <span data-ttu-id="75766-117">**後端服務** ：如果您使用 PowerPivot for Excel 建立包含分析資料的活頁簿，伺服器環境必須具有 PowerPivot for SharePoint，才可存取該資料。</span><span class="sxs-lookup"><span data-stu-id="75766-117">**Backend services:** If you use PowerPivot for Excel to create workbooks that contain analytical data, you must have PowerPivot for SharePoint to access that data in a server environment.</span></span> <span data-ttu-id="75766-118">您可以在已安裝 SharePoint Server 2013 的電腦或在沒有 SharePoint 軟體的另一部電腦上執行 SQL Server 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="75766-118">You can run SQL Server Setup on a computer that has SharePoint Server 2013 installed, or on a different computer that has no SharePoint software.</span></span> <span data-ttu-id="75766-119">Analysis Services 沒有 SharePoint 的相依性。</span><span class="sxs-lookup"><span data-stu-id="75766-119">Analysis Services does not have any dependencies on SharePoint.</span></span>  
  
     <span data-ttu-id="75766-120">**注意** ：本主題將描述 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 伺服器和後端服務的安裝。</span><span class="sxs-lookup"><span data-stu-id="75766-120">**Note:** This topic describes the installation of the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server and the backend services.</span></span>  
  
-   <span data-ttu-id="75766-121">**中介層** ：SharePoint 中 PowerPivot 體驗的增強功能，包括 PowerPivot 圖庫、排程資料重新整理、管理儀表板和資料提供者。</span><span class="sxs-lookup"><span data-stu-id="75766-121">**Middle-tier:** Enhancements to the PowerPivot experiences in SharePoint including PowerPivot Gallery, Schedule data refresh, Management dashboard, and data providers.</span></span> <span data-ttu-id="75766-122">如需有關安裝及設定中介層的詳細資訊，請參閱以下主題：</span><span class="sxs-lookup"><span data-stu-id="75766-122">For more information on installing and configuring the middle-tier, see the following:</span></span>  
  
    -   [<span data-ttu-id="75766-123">安裝或卸載 PowerPivot for SharePoint 增益集 &#40;SharePoint 2013&#41;</span><span class="sxs-lookup"><span data-stu-id="75766-123">Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)  
  
    -   [<span data-ttu-id="75766-124">設定 PowerPivot 並將方案部署 &#40;SharePoint 2013&#41;</span><span class="sxs-lookup"><span data-stu-id="75766-124">Configure PowerPivot and Deploy Solutions &#40;SharePoint 2013&#41;</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013)  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> <span data-ttu-id="75766-125">必要條件</span><span class="sxs-lookup"><span data-stu-id="75766-125">Prerequisites</span></span>  
  
1.  <span data-ttu-id="75766-126">您必須是本機系統管理員，才能執行 SQL Server 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="75766-126">You must be a local administrator to run SQL Server Setup.</span></span>  
  
2.  <span data-ttu-id="75766-127">PowerPivot for SharePoint 需要 SharePoint Server 2013 Enterprise 版。</span><span class="sxs-lookup"><span data-stu-id="75766-127">SharePoint Server 2013 enterprise edition is required for PowerPivot for SharePoint.</span></span> <span data-ttu-id="75766-128">您也可以使用 Evaluation Enterprise 版。</span><span class="sxs-lookup"><span data-stu-id="75766-128">You can also use the evaluation enterprise edition.</span></span>  
  
3.  <span data-ttu-id="75766-129">電腦必須與 Excel Services 加入相同 Active Directory 樹系中的網域。</span><span class="sxs-lookup"><span data-stu-id="75766-129">The computer must be joined to a domain in the same Active Directory forest as Excel Services.</span></span>  
  
4.  <span data-ttu-id="75766-130">必須提供 PowerPivot 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="75766-130">The PowerPivot instance name must be available.</span></span> <span data-ttu-id="75766-131">正在安裝 Analysis Services SharePoint 模式的電腦上，不能有現存的 PowerPivot 具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="75766-131">You cannot have an existing PowerPivot-named instance on the computer on which you are installing Analysis Services in SharePoint mode.</span></span>  
  
5.  <span data-ttu-id="75766-132">請參閱[SharePoint 模式下 Analysis Services Server &#40;SQL Server 2014&#41;的硬體和軟體需求](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="75766-132">Review [Hardware and Software Requirements for Analysis Services Server in SharePoint Mode &#40;SQL Server 2014&#41;](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md).</span></span>  
  
6.  <span data-ttu-id="75766-133">請參閱[SQL Server 2012 Service Pack 1 版本](https://go.microsoft.com/fwlink/?LinkID=248389)資訊 (的版本資訊 https://go.microsoft.com/fwlink/?LinkID=248389) 。</span><span class="sxs-lookup"><span data-stu-id="75766-133">Review the release notes at [SQL Server 2012 Service Pack 1 Release Notes](https://go.microsoft.com/fwlink/?LinkID=248389) (https://go.microsoft.com/fwlink/?LinkID=248389).</span></span>  
  
###  <a name="sql-server-edition-requirements"></a><a name="bkmk_sqleditions"></a> <span data-ttu-id="75766-134">SQL Server Edition 需求</span><span class="sxs-lookup"><span data-stu-id="75766-134">SQL Server Edition Requirements</span></span>  
 <span data-ttu-id="75766-135">並非在所有版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中都提供商業智慧功能。</span><span class="sxs-lookup"><span data-stu-id="75766-135">Business intelligence features are not all available in all editions of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="75766-136">如需詳細資訊，請參閱[SQL Server 2012 (https://go.microsoft.com/fwlink/?linkid=232473) 版本](https://go.microsoft.com/fwlink/?linkid=232473)[和 SQL Server 2014 的版本和元件](../../../sql-server/editions-and-components-of-sql-server-2016.md)支援的功能。</span><span class="sxs-lookup"><span data-stu-id="75766-136">For details, see [Features Supported by the Editions of SQL Server 2012 (https://go.microsoft.com/fwlink/?linkid=232473)](https://go.microsoft.com/fwlink/?linkid=232473) and [Editions and Components of SQL Server 2014](../../../sql-server/editions-and-components-of-sql-server-2016.md).</span></span>  
  
 <span data-ttu-id="75766-137">您可以在[SQL Server 2012 SP1 版本](https://go.microsoft.com/fwlink/?LinkID=248389)資訊 (找到目前的版本資訊 https://go.microsoft.com/fwlink/?LinkID=248389) 。</span><span class="sxs-lookup"><span data-stu-id="75766-137">The current release notes can be found at [SQL Server 2012 SP1 Release Notes](https://go.microsoft.com/fwlink/?LinkID=248389) (https://go.microsoft.com/fwlink/?LinkID=248389).</span></span>  
  
 <span data-ttu-id="75766-138">[Microsoft SQL Server 2012 版本資訊 (https://go.microsoft.com/fwlink/?LinkId=236893) ](https://go.microsoft.com/fwlink/?LinkId=236893)。</span><span class="sxs-lookup"><span data-stu-id="75766-138">[Microsoft SQL Server 2012 Release Notes (https://go.microsoft.com/fwlink/?LinkId=236893)](https://go.microsoft.com/fwlink/?LinkId=236893).</span></span>  
  
##  <a name="step-1-install-powerpivot-for-sharepoint"></a><a name="InstallSQL"></a><span data-ttu-id="75766-139">步驟1：安裝 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="75766-139">Step 1: Install PowerPivot for SharePoint</span></span>  
 <span data-ttu-id="75766-140">在此步驟中，您會執行 SQL Server 安裝程式，安裝 SharePoint 模式的 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="75766-140">In this step, you run SQL Server Setup to install an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode.</span></span> <span data-ttu-id="75766-141">在後續步驟中，您針對活頁簿資料模型設定 Excel Services 使用此伺服器。</span><span class="sxs-lookup"><span data-stu-id="75766-141">In a subsequent step, you configure Excel Services to use this server for workbook data models.</span></span>  
  
1.  <span data-ttu-id="75766-142">執行 [SQL Server 安裝精靈] \(Setup.exe)。</span><span class="sxs-lookup"><span data-stu-id="75766-142">Run the SQL Server Installation Wizard (Setup.exe).</span></span>  
  
2.  <span data-ttu-id="75766-143">按一下左邊功能窗格中的 **[安裝]** 。</span><span class="sxs-lookup"><span data-stu-id="75766-143">Click **Installation** in the left navigation.</span></span>  
  
3.  <span data-ttu-id="75766-144">按一下 **[新增 SQL Server 獨立安裝或將功能加入至現有安裝]**。</span><span class="sxs-lookup"><span data-stu-id="75766-144">Click **New SQL Server stand-alone installation or add features to an existing installation**.</span></span>  
  
4.  <span data-ttu-id="75766-145">如果看到 **[產品金鑰]** 頁面，請指定 Evaluation Edition 或是輸入 Enterprise Edition 授權複本的產品金鑰。</span><span class="sxs-lookup"><span data-stu-id="75766-145">If you see the **Product Key** page, specify the evaluation edition or enter a product key for a licensed copy of the enterprise edition.</span></span> <span data-ttu-id="75766-146">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="75766-146">Click **Next**.</span></span> <span data-ttu-id="75766-147">如需版本的詳細資訊，請參閱＜ [Editions and Components of SQL Server 2014](../../../sql-server/editions-and-components-of-sql-server-2016.md)＞。</span><span class="sxs-lookup"><span data-stu-id="75766-147">For more information on editions, see [Editions and Components of SQL Server 2014](../../../sql-server/editions-and-components-of-sql-server-2016.md).</span></span>  
  
5.  <span data-ttu-id="75766-148">檢閱並接受 Microsoft 軟體授權條款的條款，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="75766-148">Review and accept the Microsoft Software License Terms of agreement, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="75766-149">如果您看到 **[全域規則]** 頁面，請檢閱安裝精靈顯示的所有規則資訊。</span><span class="sxs-lookup"><span data-stu-id="75766-149">If you see the **Global Rules** page, review any rules information the setup wizard displays.</span></span>  
  
7.  <span data-ttu-id="75766-150">在 **[Microsoft Update]** 頁面上，建議您使用 Microsoft Update 來檢查更新，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="75766-150">On the **Microsoft Update** page, it is recommended you use Microsoft Update to check for updates, then click **Next**.</span></span>  
  
8.  <span data-ttu-id="75766-151">**[安裝安裝檔案]** 頁面會執行數分鐘。</span><span class="sxs-lookup"><span data-stu-id="75766-151">The **Install Setup Files** page runs for several minutes.</span></span> <span data-ttu-id="75766-152">檢閱任何規則警告或失敗規則，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="75766-152">Review any rule warnings or failed rules, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="75766-153">如果您看到另一個 **[安裝程式支援規則]**，請檢閱任何警告，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="75766-153">If you see another **Setup Support Rules**, review any warnings and click **Next**.</span></span>  
  
     <span data-ttu-id="75766-154">**注意：** 由於已啟用 Windows 防火牆，因此您會看到開放通訊埠才可啟用遠端存取的警告。</span><span class="sxs-lookup"><span data-stu-id="75766-154">**Note:** Because Windows Firewall is enabled, you see a warning to open ports to enable remote access.</span></span>  
  
10. <span data-ttu-id="75766-155">在 **[安裝程式角色]** 頁面上，選取 **[SQL Server PowerPivot for SharePoint]**。</span><span class="sxs-lookup"><span data-stu-id="75766-155">On the **Setup Role** page, select **SQL Server PowerPivot for SharePoint**.</span></span> <span data-ttu-id="75766-156">此選項會安裝 SharePoint 模式的 Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="75766-156">This option installs Analysis Services in SharePoint mode.</span></span>  
  
     <span data-ttu-id="75766-157">您可選擇性地在安裝中加入一項 Database Engine 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="75766-157">Optionally, you can add an instance of the Database Engine to your installation.</span></span> <span data-ttu-id="75766-158">在設定新的伺服器陣列時，您可能會新增資料庫引擎，而且需要資料庫伺服器來執行伺服器陣列的設定和內容資料庫。</span><span class="sxs-lookup"><span data-stu-id="75766-158">You might add the Database Engine when setting up a new farm and need a database server to run the farm's configuration and content databases.</span></span> <span data-ttu-id="75766-159">此選項也會安裝 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="75766-159">This option also installs [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
     <span data-ttu-id="75766-160">如果您加入 Database Engine，則會安裝為 **PowerPivot** 具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="75766-160">If you add the Database Engine, it is installed as a **PowerPivot** named instance.</span></span> <span data-ttu-id="75766-161">每當您指定此執行個體的連接時，請用此格式輸入資料庫名稱：[`servername`]\PowerPivot。</span><span class="sxs-lookup"><span data-stu-id="75766-161">Whenever you specify a connection to this instance, enter the database name in this format: [`servername`]\PowerPivot.</span></span>  
  
     <span data-ttu-id="75766-162">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="75766-162">Click **Next**.</span></span>  
  
     <span data-ttu-id="75766-163">![安裝程式角色](../../../sql-server/install/media/gmni-setupui-featurerole-sql2012sp1.gif "安裝程式角色")</span><span class="sxs-lookup"><span data-stu-id="75766-163">![Setup Role](../../../sql-server/install/media/gmni-setupui-featurerole-sql2012sp1.gif "Setup Role")</span></span>  
  
11. <span data-ttu-id="75766-164">[特徵選取] 會顯示各項功能的唯讀清單，以供使用者參考。</span><span class="sxs-lookup"><span data-stu-id="75766-164">In Feature Selection, a read-only list of the features is displayed for informational purposes.</span></span> <span data-ttu-id="75766-165">您無法加入或移除預先為這個角色選取的項目。</span><span class="sxs-lookup"><span data-stu-id="75766-165">You cannot add or remove items the preselected items for this role.</span></span> <span data-ttu-id="75766-166">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="75766-166">Click **Next**.</span></span>  
  
12. <span data-ttu-id="75766-167">在 **[執行個體組態]** 頁面上，顯示 'PowerPivot' 的唯讀執行個體名稱是為了給使用者參考。</span><span class="sxs-lookup"><span data-stu-id="75766-167">On the **Instance Configuration** page, a read-only instance name of 'PowerPivot' is displayed for informational purposes.</span></span> <span data-ttu-id="75766-168">此執行個體名稱是必要的，而且無法修改。</span><span class="sxs-lookup"><span data-stu-id="75766-168">This instance name is required and it cannot be modified.</span></span> <span data-ttu-id="75766-169">但是，您可以輸入唯一的執行個體識別碼來指定描述性目錄名稱和登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="75766-169">However, you can enter a unique Instance ID to specify a descriptive directory name and registry keys.</span></span> <span data-ttu-id="75766-170">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="75766-170">Click **Next**.</span></span>  
  
13. <span data-ttu-id="75766-171">在 **[伺服器組態]** 頁面上，將所有服務的 **[啟動類型]** 設定為 [自動]。</span><span class="sxs-lookup"><span data-stu-id="75766-171">On the **Server Configuration** page, configure all of the services for Automatic **Startup Type**.</span></span> <span data-ttu-id="75766-172">指定 **SQL Server Analysis Services**的所需網域帳戶和密碼，即下圖中的 **(1)** 。</span><span class="sxs-lookup"><span data-stu-id="75766-172">Specify the desired domain account and password for **SQL Server Analysis Services**, **(1)** in the following diagram.</span></span>  
  
    -   <span data-ttu-id="75766-173">針對 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]，您可以使用 **網域使用者** 帳戶或 **NetworkService** 帳戶。</span><span class="sxs-lookup"><span data-stu-id="75766-173">For [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], you can use a **domain user** account or **NetworkService** account.</span></span> <span data-ttu-id="75766-174">請勿使用 LocalSystem 或 LocalService 帳戶。</span><span class="sxs-lookup"><span data-stu-id="75766-174">Do not use LocalSystem or LocalService accounts.</span></span>  
  
    -   <span data-ttu-id="75766-175">若已新增 SQL Server Database Engine 與 SQL Server Agent，您可以將服務設定為利用網域使用者帳戶或預設虛擬帳戶加以執行。</span><span class="sxs-lookup"><span data-stu-id="75766-175">If you added the SQL Server Database Engine and SQL Server Agent, you can configure the services to run under domain user accounts or under the default virtual account.</span></span>  
  
    -   <span data-ttu-id="75766-176">絕不要使用您自己的網域使用者帳戶來提供服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="75766-176">Never provision service accounts with your own domain user account.</span></span> <span data-ttu-id="75766-177">這麼做會授與伺服器您對網路中的資源所擁有的相同權限。</span><span class="sxs-lookup"><span data-stu-id="75766-177">Doing so grants the server the same permissions that you have to the resources in your network.</span></span> <span data-ttu-id="75766-178">如果惡意使用者入侵伺服器，該使用者就會使用您的網域認證登入。</span><span class="sxs-lookup"><span data-stu-id="75766-178">If a malicious user compromises the server, that user is logged in under your domain credentials.</span></span> <span data-ttu-id="75766-179">該使用者將有權下載或使用您有權下載或使用的相同資料和應用程式。</span><span class="sxs-lookup"><span data-stu-id="75766-179">The user has the permissions to download or use the same data and applications that you do.</span></span>  
  
     <span data-ttu-id="75766-180">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="75766-180">Click **Next**.</span></span>  
  
     <span data-ttu-id="75766-181">![SSAS Server 組態](../../../sql-server/install/media/ssas-powerpivotsetupsql2012sp1-serverconfiguration.gif "SSAS Server 組態")</span><span class="sxs-lookup"><span data-stu-id="75766-181">![SSAS Server Configuration](../../../sql-server/install/media/ssas-powerpivotsetupsql2012sp1-serverconfiguration.gif "SSAS Server Configuration")</span></span>  
  
14. <span data-ttu-id="75766-182">若您正安裝 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]，則隨即會出現 **[資料庫引擎組態]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="75766-182">If you are installing the [!INCLUDE[ssDE](../../../includes/ssde-md.md)], the **Database Engine Configuration** page appears.</span></span> <span data-ttu-id="75766-183">在 [資料庫引擎組態] 中按一下 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] [加入目前使用者] **，為您的使用者帳戶授與** 執行個體的管理員權限。</span><span class="sxs-lookup"><span data-stu-id="75766-183">In [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Configuration, click **Add Current User** to grant your user account administrator permissions on the Database Engine instance.</span></span>  
  
     <span data-ttu-id="75766-184">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="75766-184">Click **Next**.</span></span>  
  
15. <span data-ttu-id="75766-185">在 **[Analysis Services 組態]** 頁面上，按一下 **[加入目前使用者]** ，為您的使用者帳戶授與管理權限。</span><span class="sxs-lookup"><span data-stu-id="75766-185">On the **Analysis Services Configuration** page, click **Add Current User** to grant your user account administrative permissions.</span></span> <span data-ttu-id="75766-186">在完成安裝程式之後，您將會需要管理權限來設定伺服器。</span><span class="sxs-lookup"><span data-stu-id="75766-186">You will need administrative permission to configure the server after Setup is finished.</span></span>  
  
    -   <span data-ttu-id="75766-187">在相同的頁面上，加入也需要管理權限之任何人的 Windows 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="75766-187">In the same page, add the Windows user account of any person who also requires administrative permissions.</span></span> <span data-ttu-id="75766-188">例如，想要在 [!INCLUDE[ssGeminiSrv](../../../includes/ssgeminisrv-md.md)] 中連接至 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 執行個體以疑難排解資料庫連接問題的所有使用者，都必須擁有系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="75766-188">For example, any user who wants to connect to the [!INCLUDE[ssGeminiSrv](../../../includes/ssgeminisrv-md.md)] instance in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to troubleshoot database connection problems must have system administrator permissions.</span></span> <span data-ttu-id="75766-189">請加入可能需要立即針對伺服器進行疑難排解或管理之任何人的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="75766-189">Add the user account of any person who might need to troubleshoot or administer the server now.</span></span>  
  
    -   > [!NOTE]  
        >  <span data-ttu-id="75766-190">需要存取 Analysis Services 伺服器執行個體的所有服務應用程式都必須具有 Analysis Services 管理權限。</span><span class="sxs-lookup"><span data-stu-id="75766-190">All service applications that require access to the Analysis Services server instance need to have Analysis Services Administrative permissions.</span></span> <span data-ttu-id="75766-191">例如，加入 Excel Services、Power View 及 Performance Point 服務的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="75766-191">For example, add the service accounts for Excel Services, Power View, and Performance Point Services.</span></span> <span data-ttu-id="75766-192">此外，請加入 SharePoint 伺服器陣列帳戶，做為裝載管理中心的 Web 應用程式的識別。</span><span class="sxs-lookup"><span data-stu-id="75766-192">Also, add the SharePoint farm account, which is used as the identity of the web application that hosts Central Administration.</span></span>  
  
     <span data-ttu-id="75766-193">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="75766-193">Click **Next**.</span></span>  
  
16. <span data-ttu-id="75766-194">在 **[錯誤報告]** 頁面上，按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="75766-194">On the **Error Reporting** page, click **Next**.</span></span>  
  
17. <span data-ttu-id="75766-195">在 [**安裝準備就緒**] 頁面上，按一下 [**安裝**]。</span><span class="sxs-lookup"><span data-stu-id="75766-195">On the **Ready to Install** page, click **Install**.</span></span>  
  
18. <span data-ttu-id="75766-196">如果您看見 **[需要重新啟動電腦]** 對話方塊，請按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="75766-196">If you see the dialog **Computer Restart Required**, click **OK**.</span></span>  
  
19. <span data-ttu-id="75766-197">安裝完成時，按一下 [關閉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="75766-197">When the installation is complete, click **Close**.</span></span>  
  
20. <span data-ttu-id="75766-198">重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="75766-198">Restart the computer.</span></span>  
  
21. <span data-ttu-id="75766-199">如果您的環境有防火牆，請檢閱《SQL Server 線上叢書》主題＜ [Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md)＞。</span><span class="sxs-lookup"><span data-stu-id="75766-199">If you have a firewall in your environment, review the SQL Server Books Online topic, [Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
### <a name="verify-the-sql-server-installation"></a><span data-ttu-id="75766-200">確認 SQL Server 安裝</span><span class="sxs-lookup"><span data-stu-id="75766-200">Verify the SQL Server Installation</span></span>  
 <span data-ttu-id="75766-201">確認 Analysis Services 服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="75766-201">Verify that the Analysis Services Service is running.</span></span>  
  
1.  <span data-ttu-id="75766-202">在 Microsoft Windows 按一下 **[開始]**，按一下 **[所有程式]**，然後按一下 **[Microsoft SQL Server 2012]** 群組。</span><span class="sxs-lookup"><span data-stu-id="75766-202">In Microsoft Windows click **Start**, click **All Programs**, and click the **Microsoft SQL Server 2012** group.</span></span>  
  
2.  <span data-ttu-id="75766-203">按一下 **[SQL Server Management Studio]**。</span><span class="sxs-lookup"><span data-stu-id="75766-203">Click **SQL Server Management Studio**.</span></span>  
  
3.  <span data-ttu-id="75766-204">連接至 Analysis Services 執行個體，例如 **[您的伺服器名稱]\POWERPIVOT**。</span><span class="sxs-lookup"><span data-stu-id="75766-204">Connect to the Analysis Services instance, for example **[your server name]\POWERPIVOT**.</span></span> <span data-ttu-id="75766-205">如果您可以連接到執行個體，表示已確認服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="75766-205">If you can connect to the instance, you have verified the Service is running.</span></span>  
  
##  <a name="step-2-configure-basic-analysis-services-sharepoint-integration"></a><a name="bkmk_config"></a><span data-ttu-id="75766-206">步驟2：設定基本 Analysis Services SharePoint 整合</span><span class="sxs-lookup"><span data-stu-id="75766-206">Step 2: Configure Basic Analysis Services SharePoint Integration</span></span>  
 <span data-ttu-id="75766-207">下列步驟描述必要的組態變更，讓您可以與 SharePoint 文件庫中的 Excel 進階資料模型互動。</span><span class="sxs-lookup"><span data-stu-id="75766-207">The following steps describe configuration changes needed so you can interact with Excel advanced data models inside a SharePoint document library.</span></span> <span data-ttu-id="75766-208">在您安裝 SharePoint Server 2013 和 SQL Server Analysis Services 之後，完成這些步驟。</span><span class="sxs-lookup"><span data-stu-id="75766-208">Complete these steps after you install SharePoint Server 2013 and SQL Server Analysis Services.</span></span>  
  
### <a name="grant-excel-services-server-administration-rights-on-analysis-services"></a><span data-ttu-id="75766-209">將 Analysis Services 的伺服器管理權限授與 Excel Services</span><span class="sxs-lookup"><span data-stu-id="75766-209">Grant Excel Services Server Administration Rights on Analysis Services</span></span>  
 <span data-ttu-id="75766-210">如果在 Analysis Services 安裝期間，便不需要完成本節；您已加入 Excel Services 應用程式服務帳戶做為 Analysis Services 管理員。</span><span class="sxs-lookup"><span data-stu-id="75766-210">You do not need to complete this section if during the Analysis Services installation; you added the Excel Services Application service account as an Analysis Services administrator.</span></span>  
  
1.  <span data-ttu-id="75766-211">在 Analysis Services 伺服器上，啟動 SQL Server Management Studio 並連接至 Analysis Services 執行個體，例如 `[MyServer]\POWERPIVOT`.</span><span class="sxs-lookup"><span data-stu-id="75766-211">On the Analysis Services server, start SQL Server Management Studio and connect to the Analysis Services instance, for example `[MyServer]\POWERPIVOT`.</span></span>  
  
2.  <span data-ttu-id="75766-212">在 [物件總管] 中，以滑鼠右鍵按一下執行個體名稱，然後按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="75766-212">In Object Explorer, Right-click the instance name and click **Properties**.</span></span>  
  
     <span data-ttu-id="75766-213">![檢視 SSAS 伺服器的屬性](../../../sql-server/install/media/as-ssms-proeprties.gif "檢視 SSAS 伺服器的屬性")</span><span class="sxs-lookup"><span data-stu-id="75766-213">![View Properties of an SSAS server](../../../sql-server/install/media/as-ssms-proeprties.gif "View Properties of an SSAS server")</span></span>  
  
3.  <span data-ttu-id="75766-214">按一下左窗格中的 **[安全性]**。</span><span class="sxs-lookup"><span data-stu-id="75766-214">In the left pane, click **Security**.</span></span> <span data-ttu-id="75766-215">加入您在步驟 1 中為 Excel Services 應用程式設定的網域登入。</span><span class="sxs-lookup"><span data-stu-id="75766-215">Add the domain login you configured for the Excel Services Application in step 1.</span></span>  
  
     <span data-ttu-id="75766-216">![SSAS 伺服器的安全性設定](../../../sql-server/install/media/as-ssms-security.gif "SSAS 伺服器的安全性設定")</span><span class="sxs-lookup"><span data-stu-id="75766-216">![Security Settings of an SSAS Server](../../../sql-server/install/media/as-ssms-security.gif "Security Settings of an SSAS Server")</span></span>  
  
### <a name="configure-excel-services-for-analysis-services-integration"></a><span data-ttu-id="75766-217">針對 Analysis Services 整合設定 Excel Services</span><span class="sxs-lookup"><span data-stu-id="75766-217">Configure Excel Services for Analysis Services integration</span></span>  
  
1.  <span data-ttu-id="75766-218">在 [SharePoint 管理中心] 的 [應用程式管理] 群組中，按一下 **[管理服務應用程式]**。</span><span class="sxs-lookup"><span data-stu-id="75766-218">In SharePoint Central Administration, in the Application Management group, click **Manage Service Applications**.</span></span>  
  
2.  <span data-ttu-id="75766-219">按一下您的服務應用程式名稱，預設為 **[Excel Services 應用程式]**。</span><span class="sxs-lookup"><span data-stu-id="75766-219">Click the name of your service application, the default is **Excel Services Application**.</span></span>  
  
3.  <span data-ttu-id="75766-220">在 **[管理 Excel Services 應用程式]** 頁面上，按一下 **[資料模型設定]**。</span><span class="sxs-lookup"><span data-stu-id="75766-220">On the **Manage Excel Services Application page**, click **Data Model Settings**.</span></span>  
  
4.  <span data-ttu-id="75766-221">按一下 **[加入伺服器]**。</span><span class="sxs-lookup"><span data-stu-id="75766-221">Click **Add Server**.</span></span>  
  
5.  <span data-ttu-id="75766-222">在 **[伺服器名稱]** 中，輸入 Analysis Services 伺服器名稱和 PowerPivot 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="75766-222">In **Server Name**, type the Analysis Services server name and the PowerPivot instance name.</span></span> <span data-ttu-id="75766-223">例如 `MyServer\POWERPIVOT`。</span><span class="sxs-lookup"><span data-stu-id="75766-223">For example `MyServer\POWERPIVOT`.</span></span> <span data-ttu-id="75766-224">PowerPivot 執行個體名稱是必要項。</span><span class="sxs-lookup"><span data-stu-id="75766-224">The PowerPivot instance name is required.</span></span>  
  
     <span data-ttu-id="75766-225">輸入描述。</span><span class="sxs-lookup"><span data-stu-id="75766-225">Type a description.</span></span>  
  
6.  <span data-ttu-id="75766-226">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="75766-226">Click **Ok**.</span></span>  
  
7.  <span data-ttu-id="75766-227">變更在數分鐘內就會生效，您也可以 **[停止]** 和 **[啟動]\*\*\*\*[Excel Calculation Services]** 服務。</span><span class="sxs-lookup"><span data-stu-id="75766-227">The changes will take effect in a few minutes or you can **Stop** and **Start** the service **Excel Calculation Services**.</span></span> <span data-ttu-id="75766-228">收件者</span><span class="sxs-lookup"><span data-stu-id="75766-228">To</span></span>  
  
     <span data-ttu-id="75766-229">另一個選項是使用系統管理權限來開啟命令提示字元，並輸入 `iisreset /noforce`。</span><span class="sxs-lookup"><span data-stu-id="75766-229">Another option is to open a command prompt with administrative privileges, and type `iisreset /noforce`.</span></span>  
  
     <span data-ttu-id="75766-230">您可以檢閱 ULS 記錄檔中的項目，驗證 Excel Services 已辨識伺服器。</span><span class="sxs-lookup"><span data-stu-id="75766-230">You can verify the server is recognized by Excel Services by reviewing entries in the ULS log.</span></span> <span data-ttu-id="75766-231">您會看到與下列文字類似的項目：</span><span class="sxs-lookup"><span data-stu-id="75766-231">You will see entries similar to the following:</span></span>  
  
    ```  
    Excel Services Application            Data Model        27           Medium                Check Administrator Access ([ServerName]\POWERPIVOT): Pass.        f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
    Excel Services Application            Data Model        27           Medium                Check Server Version ([ServerName]\POWERPIVOT): Pass (11.0.2809.24 >= 11.0.2800.0).         f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
    Excel Services Application            Data Model        27           Medium                Check Deployment Mode ([ServerName]\POWERPIVOT): Pass.            f127bd9b-bae3-e0e0-9b48-3f7b5ad1eae6  
  
    ```  
  
##  <a name="step-3-verify-the-integration"></a><a name="bkmk_verify"></a><span data-ttu-id="75766-232">步驟3：確認整合</span><span class="sxs-lookup"><span data-stu-id="75766-232">Step 3: Verify the Integration</span></span>  
 <span data-ttu-id="75766-233">下列步驟會逐步引導您建立和上傳新的活頁簿，以確認 Analysis Services 整合。</span><span class="sxs-lookup"><span data-stu-id="75766-233">The following steps walk you through creating and uploading a new workbook to verify the Analysis Services integration.</span></span> <span data-ttu-id="75766-234">您將需要使用 SQL Server 資料庫才能完成這些步驟。</span><span class="sxs-lookup"><span data-stu-id="75766-234">You will need a SQL Server database to complete the steps.</span></span>  
  
1.  <span data-ttu-id="75766-235">**注意** ：如果您已經有含交叉分析篩選器或篩選的進階活頁簿，可以將它上傳至 SharePoint 文件庫，然後確認您可以從文件庫檢視中與交叉分析篩選器和篩選互動。</span><span class="sxs-lookup"><span data-stu-id="75766-235">**Note:** If you already have an advanced workbook with slicers or filters, you can upload it to your SharePoint document library and verify you are able to interact with the slicers and filters from the document library view.</span></span>  
  
2.  <span data-ttu-id="75766-236">在 Excel 中啟動新的活頁簿。</span><span class="sxs-lookup"><span data-stu-id="75766-236">Start a new workbook in Excel.</span></span>  
  
3.  <span data-ttu-id="75766-237">在 [資料] 索引標籤上，按一下功能區上 **[取得外部資料]** 中的 **[從其他來源]**。</span><span class="sxs-lookup"><span data-stu-id="75766-237">On the Data tab, click **From Other Sources** on the ribbon in the **Get External Data**.</span></span>  
  
4.  <span data-ttu-id="75766-238">選取 **[從 SQL Server]**。</span><span class="sxs-lookup"><span data-stu-id="75766-238">Select **From SQL Server**.</span></span>  
  
5.  <span data-ttu-id="75766-239">在 **[資料連線精靈]**，輸入具有您要使用的資料庫的 SQL Server 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="75766-239">In the **Data Connection Wizard**, enter the name of the SQL Server instance that has the database you want to use.</span></span>  
  
6.  <span data-ttu-id="75766-240">或登入認證，確認已選取 **[使用 Windows 驗證]** ，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="75766-240">or Log on credentials, verify that **Use Windows Authentication** is selected, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="75766-241">選取您要使用的資料庫。</span><span class="sxs-lookup"><span data-stu-id="75766-241">Select the database you want to use.</span></span>  
  
8.  <span data-ttu-id="75766-242">確認已選取 **[連接至指定的表格]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="75766-242">Verify that the **Connect to specific table** checkbox is selected.</span></span>  
  
9. <span data-ttu-id="75766-243">按一下 **[啟用選取多個資料表並將資料表加入至 Excel 資料模型]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="75766-243">Click the **Enable selection of multiple tables and add tables to the Excel Data Model** checkbox.</span></span>  
  
10. <span data-ttu-id="75766-244">選取要匯入的資料表。</span><span class="sxs-lookup"><span data-stu-id="75766-244">Select the tables you want to import.</span></span>  
  
11. <span data-ttu-id="75766-245">按一下 **[匯入選定資料表之間的關聯性]** 核取方塊，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="75766-245">Click the checkbox **Import relationships between selected tables**, and then click **Next**.</span></span> <span data-ttu-id="75766-246">從關聯式資料庫匯入多個資料表，可讓您使用已經相關的資料表。</span><span class="sxs-lookup"><span data-stu-id="75766-246">Importing multiple tables from a relational database lets you work with tables that are already related.</span></span> <span data-ttu-id="75766-247">這個方式可以免除一些步驟，因為您不需要手動建立關聯性。</span><span class="sxs-lookup"><span data-stu-id="75766-247">You save steps because you don't have to build the relationships manually.</span></span>  
  
12. <span data-ttu-id="75766-248">在精靈的 **[儲存資料連線檔案和完成]** 頁面上，輸入您的連接名稱，然後按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="75766-248">In the **Save Data Connection File and Finish** page of the wizard,, type a dame for your connection and click **Finish**.</span></span>  
  
13. <span data-ttu-id="75766-249">**[匯入資料]** 對話方塊將會出現。</span><span class="sxs-lookup"><span data-stu-id="75766-249">The **Import Data** dialog box will appear.</span></span> <span data-ttu-id="75766-250">選擇 **[樞紐分析表]**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="75766-250">Choose **PivotTable Report**, and then click **Ok**.</span></span>  
  
14. <span data-ttu-id="75766-251">[樞紐分析表欄位清單] 會出現在活頁簿中。</span><span class="sxs-lookup"><span data-stu-id="75766-251">A PivotTable Field List appears in the workbook.</span></span>   
    <span data-ttu-id="75766-252">在欄位清單中，按一下 **[全部]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="75766-252">On the field list, click the **All** tab</span></span>  
  
15. <span data-ttu-id="75766-253">在欄位清單中的資料列、資料行和值區域，新增欄位。</span><span class="sxs-lookup"><span data-stu-id="75766-253">Add fields to the Row, Columns, and Value areas in the field list.</span></span>  
  
16. <span data-ttu-id="75766-254">將篩選或交叉分析篩選器加入至樞紐分析表。</span><span class="sxs-lookup"><span data-stu-id="75766-254">Add a slicer or a filter to the PivotTable.</span></span> <span data-ttu-id="75766-255">**請勿略過此步驟**。</span><span class="sxs-lookup"><span data-stu-id="75766-255">**Do not skip this step**.</span></span> <span data-ttu-id="75766-256">篩選或交叉分析篩選器是協助您確認 Analysis Services 安裝的元素。</span><span class="sxs-lookup"><span data-stu-id="75766-256">A slicer or filter is the element that will help you verify your Analysis Services installation.</span></span>  
  
17. <span data-ttu-id="75766-257">將活頁簿儲存至已設定 Excel Services 的 SharePoint Server 2013 文件庫。</span><span class="sxs-lookup"><span data-stu-id="75766-257">Save the workbook to a document library on a SharePoint Server 2013 that has Excel Services configured.</span></span> <span data-ttu-id="75766-258">您也可以將活頁簿儲存至檔案共用，然後將它上傳至 SharePoint Server 2013 文件庫。</span><span class="sxs-lookup"><span data-stu-id="75766-258">You can also save the workbook to a file share and then upload it to the SharePoint Server 2013 document library.</span></span>  
  
18. <span data-ttu-id="75766-259">按一下您的活頁簿名稱，在 SharePoint 中檢視它，然後按一下交叉分析篩選器或變更您先前加入的篩選。</span><span class="sxs-lookup"><span data-stu-id="75766-259">Click the name of your workbook to view it in SharePoint and click the slicer or change the filter that you previously added.</span></span> <span data-ttu-id="75766-260">如果發生資料更新，您就會知道 Analysis Services 已安裝，可供 Excel Services 使用。</span><span class="sxs-lookup"><span data-stu-id="75766-260">If a data update occurs, you know that Analysis Services is installed and available to Excel Services.</span></span> <span data-ttu-id="75766-261">如果您在 Excel 中開啟活頁簿，將會使用快取副本，而不是 Analysis Services 伺服器。</span><span class="sxs-lookup"><span data-stu-id="75766-261">If you open the workbook in Excel you will be using a cached copy and not using the Analysis Services server.</span></span>  
  
##  <a name="configure-the-windows-firewall-to-allow-analysis-services-access"></a><a name="bkmk_firewall"></a><span data-ttu-id="75766-262">設定 Windows 防火牆以允許 Analysis Services 存取</span><span class="sxs-lookup"><span data-stu-id="75766-262">Configure the Windows Firewall to Allow Analysis Services Access</span></span>  
 <span data-ttu-id="75766-263">請使用＜ [Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md) ＞主題中的資訊來判斷是否需要在防火牆中解除封鎖通訊埠，以允許存取 Analysis Services 或 PowerPivot for SharePoint。</span><span class="sxs-lookup"><span data-stu-id="75766-263">Use the information in the topic [Configure the Windows Firewall to Allow Analysis Services Access](../configure-the-windows-firewall-to-allow-analysis-services-access.md) to determine whether you need to unblock ports in a firewall to allow access to Analysis Services or PowerPivot for SharePoint.</span></span> <span data-ttu-id="75766-264">您可以遵循此主題所提供的步驟，設定通訊埠以及防火牆。</span><span class="sxs-lookup"><span data-stu-id="75766-264">You can follow the steps provided in the topic to configure both port and firewall settings.</span></span> <span data-ttu-id="75766-265">實際上，您必須執行這些步驟，才能允許存取 Analysis Services 伺服器。</span><span class="sxs-lookup"><span data-stu-id="75766-265">In practice, you should perform these steps together to allow access to your Analysis Services server.</span></span>  
  
##  <a name="upgrade-workbooks-and-scheduled-data-refresh"></a><a name="bkmk_upgrade_workbook"></a><span data-ttu-id="75766-266">升級活頁簿和排程的資料重新整理</span><span class="sxs-lookup"><span data-stu-id="75766-266">Upgrade Workbooks and Scheduled Data Refresh</span></span>  
 <span data-ttu-id="75766-267">升級在舊版 PowerPivot 中建立之活頁簿所需的步驟主要取決於建立活頁簿的 PowerPivot 版本。</span><span class="sxs-lookup"><span data-stu-id="75766-267">The steps required to upgrade workbooks created in previous versions of PowerPivot depend on what version of PowerPivot created the workbook.</span></span> <span data-ttu-id="75766-268">如需詳細資訊，請參閱 [升級活頁簿和排程的資料重新整理 &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013)。</span><span class="sxs-lookup"><span data-stu-id="75766-268">For more information, see [Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013).</span></span>  
  
##  <a name="beyond-the-single-server-installation--powerpivot-for-microsoft-sharepoint"></a><a name="bkmk_multiple_servers"></a><span data-ttu-id="75766-269">超越單一伺服器安裝-PowerPivot for Microsoft SharePoint</span><span class="sxs-lookup"><span data-stu-id="75766-269">Beyond the Single-Server Installation -PowerPivot for Microsoft SharePoint</span></span>  
 <span data-ttu-id="75766-270">**Web 前端 (WFE)** 或 **中介層**：若要在較大的 SharePoint 伺服器陣列中使用 SharePoint 模式的 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 伺服器，並且將其他 PowerPivot 功能安裝至伺服器陣列中，請在每部 SharePoint 伺服器上執行安裝程式套件 **spPowerPivot.msi** 。</span><span class="sxs-lookup"><span data-stu-id="75766-270">**Web front-end (WFE)** or **Middle-tier:**: To use an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode in a larger SharePoint farm and to install additional PowerPivot features into the farm, run the installer package **spPowerPivot.msi** on each of the SharePoint servers.</span></span> <span data-ttu-id="75766-271">spPowerPivot.msi 會安裝必要的資料提供者以及 PowerPivot for SharePoint 2013 組態工具。</span><span class="sxs-lookup"><span data-stu-id="75766-271">The spPowerPivot.msi installs required data providers and the PowerPivot for SharePoint 2013 Configuration tool.</span></span>  
  
 <span data-ttu-id="75766-272">如需有關安裝及設定中介層的詳細資訊，請參閱以下主題：</span><span class="sxs-lookup"><span data-stu-id="75766-272">For more information on installing and configuring the middle-tier, see the following:</span></span>  
  
-   [<span data-ttu-id="75766-273">安裝或卸載 PowerPivot for SharePoint 增益集 &#40;SharePoint 2013&#41;</span><span class="sxs-lookup"><span data-stu-id="75766-273">Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)  
  
-   <span data-ttu-id="75766-274">若要下載 .msi，請參閱＜ [Microsoft SQL Server 2014 PowerPivot for Microsoft SharePoint 2013](https://go.microsoft.com/fwlink/?LinkID=324854)＞</span><span class="sxs-lookup"><span data-stu-id="75766-274">To download the .msi, see [Microsoft SQL Server 2014 PowerPivot for Microsoft SharePoint 2013](https://go.microsoft.com/fwlink/?LinkID=324854)</span></span>  
  
-   [<span data-ttu-id="75766-275">設定 PowerPivot 並將方案部署 &#40;SharePoint 2013&#41;</span><span class="sxs-lookup"><span data-stu-id="75766-275">Configure PowerPivot and Deploy Solutions &#40;SharePoint 2013&#41;</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013)  
  
 <span data-ttu-id="75766-276">**備援性和伺服器負載** ：在 SharePoint 模式下安裝第二部或其他 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 伺服器可提供 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 伺服器功能的備援性。</span><span class="sxs-lookup"><span data-stu-id="75766-276">**Redundancy and server load:** Installing a second, or more [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] servers in SharePoint mode will provide redundancy of the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server functionality.</span></span> <span data-ttu-id="75766-277">其他伺服器也會分散伺服器的負載。</span><span class="sxs-lookup"><span data-stu-id="75766-277">Additional servers will also spread the load across servers.</span></span> <span data-ttu-id="75766-278">如需詳細資訊，請參閱下列：</span><span class="sxs-lookup"><span data-stu-id="75766-278">For more information, see the following:</span></span>  
  
-   <span data-ttu-id="75766-279">[設定 Analysis Services 來處理 Excel Services (中的資料模型](https://technet.microsoft.com/library/jj614437\(v=office.15\)) https://technet.microsoft.com/library/jj614437(v=office.15)) 。</span><span class="sxs-lookup"><span data-stu-id="75766-279">[Configure Analysis Services for processing data models in Excel Services](https://technet.microsoft.com/library/jj614437\(v=office.15\)) (https://technet.microsoft.com/library/jj614437(v=office.15)).</span></span>  
  
-   <span data-ttu-id="75766-280">[ (SharePoint Server 2013)  (管理 Excel Services 資料模型設定](https://technet.microsoft.com/library/jj219780\(v=office.15\)) https://technet.microsoft.com/library/jj219780(v=office.15)) 。</span><span class="sxs-lookup"><span data-stu-id="75766-280">[Manage Excel Services data model settings (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780\(v=office.15\)) (https://technet.microsoft.com/library/jj219780(v=office.15)).</span></span>  
  
 <span data-ttu-id="75766-281">![SharePoint 設定](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 設定")會[透過 Microsoft SQL Server Connect (提交意見反應和連絡人資訊](https://connect.microsoft.com/SQLServer/Feedback) https://connect.microsoft.com/SQLServer/Feedback) 。</span><span class="sxs-lookup"><span data-stu-id="75766-281">![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings") [Submit feedback and contact information through Microsoft SQL Server Connect](https://connect.microsoft.com/SQLServer/Feedback) (https://connect.microsoft.com/SQLServer/Feedback).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75766-282">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75766-282">See Also</span></span>  
 <span data-ttu-id="75766-283">[將 PowerPivot 遷移至 SharePoint 2013](https://docs.microsoft.com/analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013) </span><span class="sxs-lookup"><span data-stu-id="75766-283">[Migrate PowerPivot to SharePoint 2013](https://docs.microsoft.com/analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013) </span></span>  
 <span data-ttu-id="75766-284">[安裝或卸載 PowerPivot for SharePoint 增益集 &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) </span><span class="sxs-lookup"><span data-stu-id="75766-284">[Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) </span></span>  
 [<span data-ttu-id="75766-285">&#40;SharePoint 2013&#41;升級活頁簿和排程的資料重新整理</span><span class="sxs-lookup"><span data-stu-id="75766-285">Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013)  
  
  
