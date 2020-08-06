---
title: 升級 Master Data Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9c3543f3-3eb9-455d-a9bf-f17e9506ad21
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a0f137d6ca5a68a72e381780505ec8c93ae3c740
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594162"
---
# <a name="upgrade-master-data-services"></a><span data-ttu-id="fcdbe-102">升級 Master Data Services</span><span class="sxs-lookup"><span data-stu-id="fcdbe-102">Upgrade Master Data Services</span></span>
  <span data-ttu-id="fcdbe-103">升級至 Microsoft [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2 的情況有四種。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-103">There are four scenarios for upgrading to Microsoft [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2.</span></span> <span data-ttu-id="fcdbe-104">請選擇最適合您情況的情況。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-104">Choose the scenario that fits your situation.</span></span>  
  
-   [<span data-ttu-id="fcdbe-105">升級但不包含 Database Engine 升級</span><span class="sxs-lookup"><span data-stu-id="fcdbe-105">Upgrade without Database Engine Upgrade</span></span>](#noengine)  
  
-   [<span data-ttu-id="fcdbe-106">升級且包含 Database Engine 升級</span><span class="sxs-lookup"><span data-stu-id="fcdbe-106">Upgrade with Database Engine Upgrade</span></span>](#engine)  
  
-   [<span data-ttu-id="fcdbe-107">在兩部電腦的情況下升級</span><span class="sxs-lookup"><span data-stu-id="fcdbe-107">Upgrade in Two-Computer Scenario</span></span>](#twocomputer)  
  
-   [<span data-ttu-id="fcdbe-108">包含從備份中還原資料庫的升級</span><span class="sxs-lookup"><span data-stu-id="fcdbe-108">Upgrade with Restoring a Database from Backup</span></span>](#restore)  
  
> [!IMPORTANT]
>  -   <span data-ttu-id="fcdbe-109">不支援從 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP1 版本升級到 CTP2 版本。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-109">Upgrading from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP1 release to the CTP2 release is not supported.</span></span>  
> -   <span data-ttu-id="fcdbe-110">在執行任何升級之前備份您的資料庫。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-110">Back up your database before performing any upgrade.</span></span>  
> -   <span data-ttu-id="fcdbe-111">升級程序會重新建立預存程序，並升級 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]使用的資料表。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-111">The upgrade process recreates stored procedures and upgrades tables used by [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="fcdbe-112">您對這些元件所做的任何自訂可能會遺失。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-112">Any customizations you have made to either of these components may be lost.</span></span>  
> -   <span data-ttu-id="fcdbe-113">模型部署封裝只能在之前建立這些封裝的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本中使用。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-113">Model deployment packages can be used only in the edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] they were created in.</span></span> <span data-ttu-id="fcdbe-114">您無法將中建立的模型部署封裝部署 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] / [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-114">You cannot deploy model deployment packages created in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]/[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
> -   <span data-ttu-id="fcdbe-115">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 將 Master Data Services 和 Data Quality Services 升級為 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2 之後，您可以繼續使用  SP1 版適用於 Excel 的 Master Data Services 增益集。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-115">You can continue using the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 version of Master Data Services Add-In for Excel after upgrading Master Data Services and Data Quality Services to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2.</span></span> <span data-ttu-id="fcdbe-116">不過，在升級為 SQL Server 2014 CTP2 之後，任何舊版適用於 Excel 的 Master Data Services 增益集將無法運作。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-116">However, any earlier version of the Master Data Services Add-In for Excel will not work after upgrading to SQL Server 2014 CTP2.</span></span> <span data-ttu-id="fcdbe-117">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 您可以在 [這裡](https://go.microsoft.com/fwlink/?LinkId=328664)下載  SP1 版適用於 Excel 的 Master Data Services 增益集。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-117">You can download the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 version of Master Data Services Add-In for Excel from [here](https://go.microsoft.com/fwlink/?LinkId=328664).</span></span>  
  
##  <a name="upgrade-without-database-engine-upgrade"></a><a name="noengine"></a> <span data-ttu-id="fcdbe-118">升級但不包含 Database Engine 升級</span><span class="sxs-lookup"><span data-stu-id="fcdbe-118">Upgrade without Database Engine Upgrade</span></span>  
 <span data-ttu-id="fcdbe-119">此案例可視為並存安裝，因為 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] / [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 和 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 都是以平行方式安裝在同一部電腦或不同的電腦上。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-119">This scenario can be considered a side-by-side installation, because both [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]/[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] and [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] are installed in parallel, on either the same computer or separate computers.</span></span>  
  
 <span data-ttu-id="fcdbe-120">在此情況下，您會繼續使用 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 主控您的 MDS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-120">In this scenario you continue to use [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] to host your MDS database.</span></span> <span data-ttu-id="fcdbe-121">但是，您必須升級 MDS 資料庫的結構描述，然後建立 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 應用程式以存取 MDS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-121">However, you must upgrade the schema of the MDS database, and then create a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] web application to access the MDS database.</span></span> <span data-ttu-id="fcdbe-122">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Web 應用程式無法再存取 MDS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-122">The MDS database can no longer be accessed by the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] web application.</span></span>  
  
 <span data-ttu-id="fcdbe-123">如果您選擇在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 同一部電腦上安裝和舊版 SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] / [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) ，您可以這樣做，因為檔案會安裝在不同的位置。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-123">If you choose to install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] and an earlier version of SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]/[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) on the same computer, you can do so because the files are installed in a different location.</span></span>  
  
-   <span data-ttu-id="fcdbe-124">根據預設，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，檔案會安裝到 *磁碟機*:\Program Files\Microsoft SQL Server\120\Master Data Services。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-124">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], by default, the files are installed at *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services.</span></span>  
  
-   <span data-ttu-id="fcdbe-125">根據預設，在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]中，檔案會安裝到 *磁碟機*:\Program Files\Microsoft SQL Server\110\Master Data Services。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-125">In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], by default, the files are installed at *drive*:\Program Files\Microsoft SQL Server\110\Master Data Services.</span></span>  
  
-   <span data-ttu-id="fcdbe-126">根據預設，在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]中，檔案會安裝到 *磁碟機*:\Program Files\Microsoft SQL Server\Master Data Services。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-126">In [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], by default, the files are installed at *drive*:\Program Files\Microsoft SQL Server\Master Data Services.</span></span>  
  
 <span data-ttu-id="fcdbe-127">若要執行此工作，請完成下列步驟。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-127">To perform this task, complete the following steps.</span></span>  
  
1.  <span data-ttu-id="fcdbe-128">安裝 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 及您想要的其他任何功能。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-128">Install [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] and any other features you want.</span></span>  
  
    1.  <span data-ttu-id="fcdbe-129">開啟 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝程式精靈。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-129">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup wizard.</span></span>  
  
    2.  <span data-ttu-id="fcdbe-130">按一下左窗格中的 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-130">In the left pane, click **Installation**.</span></span>  
  
    3.  <span data-ttu-id="fcdbe-131">按一下右窗格中的 [新增 SQL Server 獨立安裝或將功能加入至現有安裝]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-131">In the right pane, click **New SQL Server stand-alone installation or add features to an existing installation**.</span></span>  
  
    4.  <span data-ttu-id="fcdbe-132">在 [功能選擇] 頁面上，選取 [[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]] 以及您想要安裝的其他任何功能。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-132">On the **Feature Selection** page, select **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** and any other features you want to install.</span></span>  
  
    5.  <span data-ttu-id="fcdbe-133">完成精靈。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-133">Complete the wizard.</span></span>  
  
2.  <span data-ttu-id="fcdbe-134">在安裝完成後，升級 MDS 資料庫結構描述。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-134">When the installation is complete, upgrade the MDS database schema.</span></span>  
  
    1.  <span data-ttu-id="fcdbe-135">開啟 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版的 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-135">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="fcdbe-136">若要升級 MDS 資料庫結構描述，您必須以建立 MDS 資料庫時指定之系統管理員帳戶的身分登入。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-136">To upgrade the MDS database schema, you must be logged in as the Administrator Account that was specified when the MDS database was created.</span></span> <span data-ttu-id="fcdbe-137">在 MDS 資料庫的 mdm.tblUser 中，這位使用者的 [識別碼] 值為 **1**。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-137">In the MDS database, in mdm.tblUser, this user has the **ID** value of **1**.</span></span> <span data-ttu-id="fcdbe-138">如需變更此使用者的詳細資訊，請參閱[將系統管理員帳戶變更 &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-138">For information on changing this user, see [Change the System Administrator Account &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md).</span></span>  
  
    2.  <span data-ttu-id="fcdbe-139">按一下左窗格中的 [資料庫組態]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-139">In the left pane, click **Database Configuration**.</span></span>  
  
    3.  <span data-ttu-id="fcdbe-140">在右窗格中，按一下 [**選取資料庫**]，然後指定 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 資料庫實例的資訊。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-140">In the right pane, click **Select Database** and specify the information for your [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] database instance.</span></span>  
  
    4.  <span data-ttu-id="fcdbe-141">按一下 [升級資料庫] 可啟動 [升級資料庫精靈]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-141">Click **Upgrade Database** to start the **Upgrade Database Wizard**.</span></span> <span data-ttu-id="fcdbe-142">如需詳細資訊，請參閱[升級資料庫精靈 &#40;Master Data Services 組態管理員&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-142">For more information, see [Upgrade Database Wizard &#40;Master Data Services Configuration Manager&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).</span></span>  
  
3.  <span data-ttu-id="fcdbe-143">升級完成後，請建立 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-143">When the upgrade is complete, create a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] web application.</span></span>  
  
    1.  <span data-ttu-id="fcdbe-144">開啟 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版的 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-144">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
    2.  <span data-ttu-id="fcdbe-145">按一下左窗格中的 **[Web 組態]** 。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-145">In the left pane, click **Web Configuration**.</span></span>  
  
    3.  <span data-ttu-id="fcdbe-146">從右窗格的 [網站] 清單中，選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="fcdbe-146">In the right pane, from the **Website** list, select one of the following options:</span></span>  
  
        -   <span data-ttu-id="fcdbe-147">[預設的網站]，然後按一下 [建立應用程式]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-147">**Default Web Site**, then click **Create Application**.</span></span>  
  
        -   <span data-ttu-id="fcdbe-148">[建立新的網站]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-148">**Create new site**.</span></span> <span data-ttu-id="fcdbe-149">建立網站時，便會自動建立新的 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-149">A new web application is automatically created when the website is created.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="fcdbe-150">在 SQL Server 2014 版的 Master Data Services 組態管理員中，可讓您選取您在舊版 SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) 中的現有 MDS Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-150">Your existing MDS web application from an earlier version of SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) is available for selection in the SQL Server 2014 version of Master Data Services Configuration Manager.</span></span> <span data-ttu-id="fcdbe-151">您絕不能選取現有的 Web 應用程式，而是必須建立 MDS 的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-151">You must not select the existing web application, and instead must create a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] web application for MDS.</span></span> <span data-ttu-id="fcdbe-152">否則，當您嘗試將 Web 應用程式與升級的 MDS 資料庫建立關聯時，將會收到錯誤，說明因為該頁面的相關組態資料無效，所以無法存取所要求的頁面。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-152">Otherwise, you will receive an error when you try to associate the web application with the upgraded MDS database stating that the requested page cannot be accessed because the related configuration data for the page is invalid.</span></span>  
        >   
        >  <span data-ttu-id="fcdbe-153">如果您要為 MDS Web 應用程式使用相同的名稱 (別名) 做為現有 ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) Web 應用程式，您必須先將 Web 應用程式和相關聯的應用程式集區從 IIS 刪除，然後使用 SQL Server 2014 版的 Master Data Services 組態管理員，以相同的名稱建立 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-153">If you want to use the same name (alias) for MDS web application as your existing ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) web application, you must first delete the web application and the associated application pool from IIS, and then create a web application with the same name using SQL Server 2014 version of Master Data Services Configuration Manager.</span></span> <span data-ttu-id="fcdbe-154">如需從 IIS 移除 Web 應用程式和應用程式集區的資訊，請參閱 [移除應用程式 (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) 和 [移除應用程式集區 (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538)。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-154">For information about removing web application and application pools from IIS, see [Remove an Application (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) and [Remove an Application Pool (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538).</span></span>  
  
4.  <span data-ttu-id="fcdbe-155">現在將新的 Web 應用程式與升級的 MDS 資料庫建立關聯。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-155">Now associate the new web application with the upgraded MDS database.</span></span>  
  
    1.  <span data-ttu-id="fcdbe-156">在 [建立應用程式與資料庫間的關聯] 區段中，按一下 [選取]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-156">In the **Associate Application with Database** section, click **Select**.</span></span>  
  
    2.  <span data-ttu-id="fcdbe-157">選取 MDS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-157">Select the MDS database.</span></span>  
  
    3.  <span data-ttu-id="fcdbe-158">按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-158">Click **Apply**.</span></span>  
  
##  <a name="upgrade-with-database-engine-upgrade"></a><a name="engine"></a> <span data-ttu-id="fcdbe-159">升級且包含 Database Engine 升級</span><span class="sxs-lookup"><span data-stu-id="fcdbe-159">Upgrade with Database Engine Upgrade</span></span>  
 <span data-ttu-id="fcdbe-160">在此案例中，您要將資料庫引擎和 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 應用程式從 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 SQL Server 2012 升級到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-160">In this scenario you will upgrade both the database engine and [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] application from [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or SQL Server 2012 to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="fcdbe-161">若要執行此工作，請完成下列步驟。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-161">To perform this task, complete the following steps.</span></span>  
  
1.  <span data-ttu-id="fcdbe-162">**僅限 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]** ：開啟 [控制台] > [程式和功能]，並解除安裝 Microsoft [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-162">**For [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] only**: Open **Control Panel** > **Programs and Features** and uninstall Microsoft [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].</span></span>  
  
2.  <span data-ttu-id="fcdbe-163">將資料庫引擎升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-163">Upgrade the database engine to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
    1.  <span data-ttu-id="fcdbe-164">開啟 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝程式精靈。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-164">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup wizard.</span></span>  
  
    2.  <span data-ttu-id="fcdbe-165">按一下左窗格中的 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-165">In the left pane, click **Installation**.</span></span>  
  
    3.  <span data-ttu-id="fcdbe-166">在右窗格中，按一下 [**從 SQL Server 2005]、[SQL Server 2008]、[SQL Server 2008 R2] 或 [SQL Server 2012**]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-166">In the right pane, click **Upgrade from SQL Server 2005, SQL Server 2008, SQL Server 2008 R2 or SQL Server 2012**.</span></span>  
  
    4.  <span data-ttu-id="fcdbe-167">完成精靈。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-167">Complete the wizard.</span></span>  
  
3.  <span data-ttu-id="fcdbe-168">\*\* [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 僅適用于\*\*：升級完成時，請新增 **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** 功能。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-168">**For [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] only**: When the upgrade is complete, add the **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** feature.</span></span>  
  
    1.  <span data-ttu-id="fcdbe-169">開啟 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝程式精靈。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-169">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup wizard.</span></span>  
  
    2.  <span data-ttu-id="fcdbe-170">按一下左窗格中的 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-170">In the left pane, click **Installation**.</span></span>  
  
    3.  <span data-ttu-id="fcdbe-171">按一下右窗格中的 [新增 SQL Server 獨立安裝或將功能加入至現有安裝]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-171">In the right pane, click **New SQL Server stand-alone installation or add features to an existing installation**.</span></span>  
  
    4.  <span data-ttu-id="fcdbe-172">在嚮導的 [**安裝類型**] 頁面上，選取 [**將功能加入到現有的實例**] 選項，然後選擇要安裝 MDS 資料庫的實例。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-172">On the **Installation Type** page of the wizard, select the **Add features to an existing instance** option, and choose the instance where MDS database is installed.</span></span>  
  
    5.  <span data-ttu-id="fcdbe-173">在 [**特徵選取**] 頁面的 [**共用功能**] 底下，選取 **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** 。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-173">On the **Feature Selection** page, under **Shared Features**, select **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]**.</span></span>  
  
    6.  <span data-ttu-id="fcdbe-174">完成精靈。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-174">Complete the wizard.</span></span>  
  
4.  <span data-ttu-id="fcdbe-175">升級 MDS 資料庫結構描述。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-175">Upgrade the MDS database schema.</span></span>  
  
    1.  <span data-ttu-id="fcdbe-176">開啟 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版的 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-176">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="fcdbe-177">若要升級 MDS 資料庫結構描述，您必須以建立 MDS 資料庫時指定之系統管理員帳戶的身分登入。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-177">To upgrade the MDS database schema, you must be logged in as the Administrator Account that was specified when the MDS database was created.</span></span> <span data-ttu-id="fcdbe-178">在 MDS 資料庫的 mdm.tblUser 中，這位使用者的 [識別碼] 值為 **1**。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-178">In the MDS database, in mdm.tblUser, this user has the **ID** value of **1**.</span></span> <span data-ttu-id="fcdbe-179">如需變更此使用者的詳細資訊，請參閱[將系統管理員帳戶變更 &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-179">For information on changing this user, see [Change the System Administrator Account &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md).</span></span>  
  
    2.  <span data-ttu-id="fcdbe-180">按一下左窗格中的 [資料庫組態]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-180">In the left pane, click **Database Configuration**.</span></span>  
  
    3.  <span data-ttu-id="fcdbe-181">在右窗格中，按一下 [**選取資料庫**]，然後指定資料庫實例的資訊。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-181">In the right pane, click **Select Database** and specify the information for your database instance.</span></span>  
  
    4.  <span data-ttu-id="fcdbe-182">按一下 [升級資料庫] 可啟動 [升級資料庫精靈]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-182">Click **Upgrade Database** to start the **Upgrade Database Wizard**.</span></span> <span data-ttu-id="fcdbe-183">如需詳細資訊，請參閱[升級資料庫精靈 &#40;Master Data Services 組態管理員&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-183">For more information, see [Upgrade Database Wizard &#40;Master Data Services Configuration Manager&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).</span></span>  
  
    5.  <span data-ttu-id="fcdbe-184">按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-184">Click **Apply**.</span></span>  
  
5.  <span data-ttu-id="fcdbe-185">升級完成後，請建立 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-185">When the upgrade is complete, create a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] web application.</span></span>  
  
    1.  <span data-ttu-id="fcdbe-186">開啟 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版的 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-186">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
    2.  <span data-ttu-id="fcdbe-187">按一下左窗格中的 **[Web 組態]** 。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-187">In the left pane, click **Web Configuration**.</span></span>  
  
    3.  <span data-ttu-id="fcdbe-188">從右窗格的 [網站] 清單中，選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="fcdbe-188">In the right pane, from the **Website** list, select one of the following options:</span></span>  
  
        -   <span data-ttu-id="fcdbe-189">[預設的網站]，然後按一下 [建立應用程式]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-189">**Default Web Site**, then click **Create Application**.</span></span>  
  
        -   <span data-ttu-id="fcdbe-190">[建立新的網站]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-190">**Create new site**.</span></span> <span data-ttu-id="fcdbe-191">建立網站時，便會自動建立新的 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-191">A new web application is automatically created when the website is created.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="fcdbe-192">在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 版的 Master Data Services 組態管理員中，可讓您選取您在舊版 SQL Server ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) 中的現有 MDS Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-192">Your existing MDS web application from an earlier version of SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) is available for selection in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Master Data Services Configuration Manager.</span></span> <span data-ttu-id="fcdbe-193">您絕不能選取現有的 Web 應用程式，而是必須建立 MDS 的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-193">You must not select the existing web application, and instead must create a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] web application for MDS.</span></span> <span data-ttu-id="fcdbe-194">否則，當您嘗試將 Web 應用程式與升級的 MDS 資料庫建立關聯時，將會收到錯誤，說明因為該頁面的相關組態資料無效，所以無法存取所要求的頁面。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-194">Otherwise, you will receive an error when you try to associate the web application with the upgraded MDS database stating that the requested page cannot be accessed because the related configuration data for the page is invalid.</span></span>  
        >   
        >  <span data-ttu-id="fcdbe-195">如果您要為 MDS Web 應用程式使用相同的名稱 (別名) 做為現有 ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) Web 應用程式，您必須先將 Web 應用程式和相關聯的應用程式集區從 IIS 刪除，然後使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版的 Master Data Services 組態管理員，以相同的名稱建立 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-195">If you want to use the same name (alias) for MDS web application as your existing ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) web application, you must first delete the web application and the associated application pool from IIS, and then create a web application with the same name using [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Master Data Services Configuration Manager.</span></span> <span data-ttu-id="fcdbe-196">如需從 IIS 移除 Web 應用程式和應用程式集區的資訊，請參閱 [移除應用程式 (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) 和 [移除應用程式集區 (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538)。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-196">For information about removing web application and application pools from IIS, see [Remove an Application (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) and [Remove an Application Pool (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538).</span></span>  
  
6.  <span data-ttu-id="fcdbe-197">現在將新的 Web 應用程式與升級的 MDS 資料庫建立關聯。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-197">Now associate the new web application with the upgraded MDS database.</span></span>  
  
    1.  <span data-ttu-id="fcdbe-198">在 [建立應用程式與資料庫間的關聯] 區段中，按一下 [選取]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-198">In the **Associate Application with Database** section, click **Select**.</span></span>  
  
    2.  <span data-ttu-id="fcdbe-199">選取 MDS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-199">Select the MDS database.</span></span>  
  
    3.  <span data-ttu-id="fcdbe-200">按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-200">Click **Apply**.</span></span>  
  
##  <a name="upgrade-in-two-computer-scenario"></a><a name="twocomputer"></a> <span data-ttu-id="fcdbe-201">在兩部電腦的情況下升級</span><span class="sxs-lookup"><span data-stu-id="fcdbe-201">Upgrade in Two-Computer Scenario</span></span>  
 <span data-ttu-id="fcdbe-202">此情況包括升級在兩部電腦上安裝 SQL Server 的系統：一部安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]，另一部安裝 SQL Server 2008 R2 或 SQL Server 2012。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-202">This scenario involves upgrading a system in which SQL Server is installed on two computers: one with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], and the other with SQL Server 2008 R2 or SQL Server 2012.</span></span>  
  
 <span data-ttu-id="fcdbe-203">如果安裝 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]，則繼續分別使用 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]，在一部電腦上裝載您的 MDS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-203">If [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] is installed, you continue to use [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] respectively to host your MDS database on one computer.</span></span> <span data-ttu-id="fcdbe-204">但是，您必須升級 MDS 資料庫的結構描述，然後使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 應用程式來存取 MDS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-204">However, you must upgrade the schema of the MDS database, and then use the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] web application to access the MDS database.</span></span> <span data-ttu-id="fcdbe-205">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Web 應用程式無法再存取 MDS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-205">The MDS database can no longer be accessed by the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] web application.</span></span>  
  
-   <span data-ttu-id="fcdbe-206">根據預設，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，檔案會安裝到 *磁碟機*:\Program Files\Microsoft SQL Server\120\Master Data Services。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-206">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], by default, the files are installed at *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services.</span></span>  
  
-   <span data-ttu-id="fcdbe-207">根據預設，在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]中，檔案會安裝到 *磁碟機*:\Program Files\Microsoft SQL Server\110\Master Data Services。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-207">In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], by default, the files are installed at *drive*:\Program Files\Microsoft SQL Server\110\Master Data Services.</span></span>  
  
-   <span data-ttu-id="fcdbe-208">根據預設，在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]中，檔案會安裝到 *磁碟機*:\Program Files\Microsoft SQL Server\Master Data Services。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-208">In [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], by default, the files are installed at *drive*:\Program Files\Microsoft SQL Server\Master Data Services.</span></span>  
  
 <span data-ttu-id="fcdbe-209">若要執行此工作，請完成下列步驟。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-209">To perform this task, complete the following steps.</span></span>  
  
1.  <span data-ttu-id="fcdbe-210">安裝 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 及您想要的其他任何功能。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-210">Install [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] and any other features you want.</span></span>  
  
    1.  <span data-ttu-id="fcdbe-211">開啟 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝程式精靈。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-211">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup wizard.</span></span>  
  
    2.  <span data-ttu-id="fcdbe-212">按一下左窗格中的 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-212">In the left pane, click **Installation**.</span></span>  
  
    3.  <span data-ttu-id="fcdbe-213">按一下右窗格中的 [新增 SQL Server 獨立安裝或將功能加入至現有安裝]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-213">In the right pane, click **New SQL Server stand-alone installation or add features to an existing installation**.</span></span>  
  
    4.  <span data-ttu-id="fcdbe-214">在 [功能選擇] 頁面上，選取 [[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]] 以及您想要安裝的其他任何功能。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-214">On the **Feature Selection** page, select **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** and any other features you want to install.</span></span>  
  
    5.  <span data-ttu-id="fcdbe-215">完成精靈。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-215">Complete the wizard.</span></span>  
  
2.  <span data-ttu-id="fcdbe-216">在安裝完成後，升級 MDS 資料庫結構描述。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-216">When the installation is complete, upgrade the MDS database schema.</span></span>  
  
    1.  <span data-ttu-id="fcdbe-217">開啟 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版的 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-217">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="fcdbe-218">若要升級 MDS 資料庫結構描述，您必須以建立 MDS 資料庫時指定之系統管理員帳戶的身分登入。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-218">To upgrade the MDS database schema, you must be logged in as the Administrator Account that was specified when the MDS database was created.</span></span> <span data-ttu-id="fcdbe-219">在 MDS 資料庫的 mdm.tblUser 中，這位使用者的 [識別碼] 值為 **1**。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-219">In the MDS database, in mdm.tblUser, this user has the **ID** value of **1**.</span></span> <span data-ttu-id="fcdbe-220">如需變更此使用者的詳細資訊，請參閱[將系統管理員帳戶變更 &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-220">For information on changing this user, see [Change the System Administrator Account &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md).</span></span>  
  
    2.  <span data-ttu-id="fcdbe-221">按一下左窗格中的 [資料庫組態]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-221">In the left pane, click **Database Configuration**.</span></span>  
  
    3.  <span data-ttu-id="fcdbe-222">在右窗格中，按一下 [**選取資料庫**]，然後在另一部 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 電腦上指定或資料庫實例的資訊（如果 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 已安裝在另一部電腦上）。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-222">In the right pane, click **Select Database** and specify the information for your [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] database instance on the other computer, if [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] is installed on the other computer.</span></span>  
  
    4.  <span data-ttu-id="fcdbe-223">按一下 [升級資料庫] 可啟動 [升級資料庫精靈]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-223">Click **Upgrade Database** to start the **Upgrade Database Wizard**.</span></span> <span data-ttu-id="fcdbe-224">如需詳細資訊，請參閱[升級資料庫精靈 &#40;Master Data Services 組態管理員&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-224">For more information, see [Upgrade Database Wizard &#40;Master Data Services Configuration Manager&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).</span></span>  
  
3.  <span data-ttu-id="fcdbe-225">升級完成後，請建立 SQL Server 2014 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-225">When the upgrade is complete, create a SQL Server 2014 web application.</span></span>  
  
    1.  <span data-ttu-id="fcdbe-226">開啟 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版的 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-226">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
    2.  <span data-ttu-id="fcdbe-227">按一下左窗格中的 **[Web 組態]** 。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-227">In the left pane, click **Web Configuration**.</span></span>  
  
    3.  <span data-ttu-id="fcdbe-228">從右窗格的 [網站] 清單中，選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="fcdbe-228">In the right pane, from the **Website** list, select one of the following options:</span></span>  
  
        -   <span data-ttu-id="fcdbe-229">[預設的網站]，然後按一下 [建立應用程式]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-229">**Default Web Site**, then click **Create Application**.</span></span>  
  
        -   <span data-ttu-id="fcdbe-230">[建立新的網站]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-230">**Create new site**.</span></span> <span data-ttu-id="fcdbe-231">建立網站時，便會自動建立新的 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-231">A new web application is automatically created when the website is created.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="fcdbe-232">在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 版的 Master Data Services 組態管理員中，可讓您選取您在舊版 SQL Server ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) 中的現有 MDS Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-232">Your existing MDS web application from an earlier version of SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) is available for selection in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Master Data Services Configuration Manager.</span></span> <span data-ttu-id="fcdbe-233">您絕不能選取現有的 Web 應用程式，而是必須建立 MDS 的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-233">You must not select the existing web application, and instead must create a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] web application for MDS.</span></span> <span data-ttu-id="fcdbe-234">否則，當您嘗試將 Web 應用程式與升級的 MDS 資料庫建立關聯時，將會收到錯誤，說明因為該頁面的相關組態資料無效，所以無法存取所要求的頁面。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-234">Otherwise, you will receive an error when you try to associate the web application with the upgraded MDS database stating that the requested page cannot be accessed because the related configuration data for the page is invalid.</span></span>  
        >   
        >  <span data-ttu-id="fcdbe-235">如果您要為 MDS Web 應用程式使用相同的名稱 (別名) 做為現有 ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) Web 應用程式，您必須先將 Web 應用程式和相關聯的應用程式集區從 IIS 刪除，然後使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版的 Master Data Services 組態管理員，以相同的名稱建立 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-235">If you want to use the same name (alias) for MDS web application as your existing ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) web application, you must first delete the web application and the associated application pool from IIS, and then create a web application with the same name using [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Master Data Services Configuration Manager.</span></span> <span data-ttu-id="fcdbe-236">如需從 IIS 移除 Web 應用程式和應用程式集區的資訊，請參閱 [移除應用程式 (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) 和 [移除應用程式集區 (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538)。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-236">For information about removing web application and application pools from IIS, see [Remove an Application (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) and [Remove an Application Pool (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538).</span></span>  
  
4.  <span data-ttu-id="fcdbe-237">現在將此 Web 應用程式與升級的 MDS 資料庫產生關聯。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-237">Now associate the web application with the upgraded MDS database.</span></span>  
  
    1.  <span data-ttu-id="fcdbe-238">在 [建立應用程式與資料庫間的關聯] 區段中，按一下 [選取]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-238">In the **Associate Application with Database** section, click **Select**.</span></span>  
  
    2.  <span data-ttu-id="fcdbe-239">選取 MDS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-239">Select the MDS database.</span></span>  
  
    3.  <span data-ttu-id="fcdbe-240">按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-240">Click **Apply**.</span></span>  
  
##  <a name="upgrade-with-restoring-a-database-from-backup"></a><a name="restore"></a> <span data-ttu-id="fcdbe-241">包含從備份中還原資料庫的升級</span><span class="sxs-lookup"><span data-stu-id="fcdbe-241">Upgrade with Restoring a Database from Backup</span></span>  
 <span data-ttu-id="fcdbe-242">在這種情況中，[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 會隨著 SQL Server 2008 R2 或 SQL Server 2012 安裝在同一部電腦或兩部不同的電腦上。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-242">In this scenario, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] is installed along with SQL Server 2008 R2 or SQL Server 2012 on the same computer or two different computers.</span></span> <span data-ttu-id="fcdbe-243">此外，資料庫會在升級之前，備份至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2 之前的版本上，而且資料庫必須還原。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-243">Also, a database was backed up on a version earlier than the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2 release, prior to upgrade, and the database has to be restored.</span></span>  
  
-   <span data-ttu-id="fcdbe-244">根據預設，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，檔案會安裝到 *磁碟機*:\Program Files\Microsoft SQL Server\120\Master Data Services。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-244">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], by default, the files are installed at *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services.</span></span>  
  
-   <span data-ttu-id="fcdbe-245">根據預設，在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]中，檔案會安裝到 *磁碟機*:\Program Files\Microsoft SQL Server\110\Master Data Services。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-245">In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], by default, the files are installed at *drive*:\Program Files\Microsoft SQL Server\110\Master Data Services.</span></span>  
  
-   <span data-ttu-id="fcdbe-246">根據預設，在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]中，檔案會安裝到 *磁碟機*:\Program Files\Microsoft SQL Server\Master Data Services。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-246">In [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], by default, the files are installed at *drive*:\Program Files\Microsoft SQL Server\Master Data Services.</span></span>  
  
 <span data-ttu-id="fcdbe-247">若要執行此工作，請完成下列步驟。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-247">To perform this task, complete the following steps.</span></span>  
  
1.  <span data-ttu-id="fcdbe-248">安裝 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 及您想要的其他任何功能。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-248">Install [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] and any other features you want.</span></span>  
  
    1.  <span data-ttu-id="fcdbe-249">開啟 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝程式精靈。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-249">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup wizard.</span></span>  
  
    2.  <span data-ttu-id="fcdbe-250">按一下左窗格中的 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-250">In the left pane, click **Installation**.</span></span>  
  
    3.  <span data-ttu-id="fcdbe-251">按一下右窗格中的 [新增 SQL Server 獨立安裝或將功能加入至現有安裝]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-251">In the right pane, click **New SQL Server stand-alone installation or add features to an existing installation**.</span></span>  
  
    4.  <span data-ttu-id="fcdbe-252">在 [功能選擇] 頁面上，選取 [[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]] 以及您想要安裝的其他任何功能。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-252">On the **Feature Selection** page, select **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** and any other features you want to install.</span></span>  
  
    5.  <span data-ttu-id="fcdbe-253">完成精靈。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-253">Complete the wizard.</span></span>  
  
2.  <span data-ttu-id="fcdbe-254">還原備份的資料庫。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-254">Restore the database that was backed up.</span></span>  
  
3.  <span data-ttu-id="fcdbe-255">在安裝完成後，升級 MDS 資料庫結構描述。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-255">When the installation is complete, upgrade the MDS database schema.</span></span>  
  
    1.  <span data-ttu-id="fcdbe-256">開啟 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版的 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-256">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="fcdbe-257">若要升級 MDS 資料庫結構描述，您必須以建立 MDS 資料庫時指定之系統管理員帳戶的身分登入。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-257">To upgrade the MDS database schema, you must be logged in as the Administrator Account that was specified when the MDS database was created.</span></span> <span data-ttu-id="fcdbe-258">在 MDS 資料庫的 mdm.tblUser 中，這位使用者的 [識別碼] 值為 **1**。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-258">In the MDS database, in mdm.tblUser, this user has the **ID** value of **1**.</span></span> <span data-ttu-id="fcdbe-259">如需變更此使用者的詳細資訊，請參閱[將系統管理員帳戶變更 &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-259">For information on changing this user, see [Change the System Administrator Account &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md).</span></span>  
  
    2.  <span data-ttu-id="fcdbe-260">按一下左窗格中的 [資料庫組態]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-260">In the left pane, click **Database Configuration**.</span></span>  
  
    3.  <span data-ttu-id="fcdbe-261">在右窗格中，按一下 [**選取資料庫**]，然後指定 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 資料庫實例的資訊。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-261">In the right pane, click **Select Database** and specify the information for your [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] database instance.</span></span>  
  
    4.  <span data-ttu-id="fcdbe-262">按一下 [升級資料庫] 可啟動 [升級資料庫精靈]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-262">Click **Upgrade Database** to start the **Upgrade Database Wizard**.</span></span> <span data-ttu-id="fcdbe-263">如需詳細資訊，請參閱[升級資料庫精靈 &#40;Master Data Services 組態管理員&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-263">For more information, see [Upgrade Database Wizard &#40;Master Data Services Configuration Manager&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).</span></span>  
  
4.  <span data-ttu-id="fcdbe-264">升級完成後，請建立 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-264">When the upgrade is complete, create a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] web application.</span></span>  
  
    1.  <span data-ttu-id="fcdbe-265">開啟 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版的 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-265">Open the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
    2.  <span data-ttu-id="fcdbe-266">按一下左窗格中的 **[Web 組態]** 。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-266">In the left pane, click **Web Configuration**.</span></span>  
  
    3.  <span data-ttu-id="fcdbe-267">從右窗格的 [網站] 清單中，選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="fcdbe-267">In the right pane, from the **Website** list, select one of the following options:</span></span>  
  
        -   <span data-ttu-id="fcdbe-268">[預設的網站]，然後按一下 [建立應用程式]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-268">**Default Web Site**, then click **Create Application**.</span></span>  
  
        -   <span data-ttu-id="fcdbe-269">[建立新的網站]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-269">**Create new site**.</span></span> <span data-ttu-id="fcdbe-270">建立網站時，便會自動建立新的 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-270">A new web application is automatically created when the website is created.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="fcdbe-271">在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 版的 Master Data Services 組態管理員中，可讓您選取您在舊版 SQL Server ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) 中的現有 MDS Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-271">Your existing MDS web application from an earlier version of SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) is available for selection in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Master Data Services Configuration Manager.</span></span> <span data-ttu-id="fcdbe-272">您絕不能選取現有的 Web 應用程式，而是必須建立 MDS 的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-272">You must not select the existing web application, and instead must create a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] web application for MDS.</span></span> <span data-ttu-id="fcdbe-273">否則，當您嘗試將 Web 應用程式與升級的 MDS 資料庫建立關聯時，將會收到錯誤，說明因為該頁面的相關組態資料無效，所以無法存取所要求的頁面。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-273">Otherwise, you will receive an error when you try to associate the web application with the upgraded MDS database stating that the requested page cannot be accessed because the related configuration data for the page is invalid.</span></span>  
        >   
        >  <span data-ttu-id="fcdbe-274">如果您要為 MDS Web 應用程式使用相同的名稱 (別名) 做為現有 ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) Web 應用程式，您必須先將 Web 應用程式和相關聯的應用程式集區從 IIS 刪除，然後使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版的 Master Data Services 組態管理員，以相同的名稱建立 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-274">If you want to use the same name (alias) for MDS web application as your existing ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) web application, you must first delete the web application and the associated application pool from IIS, and then create a web application with the same name using [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of Master Data Services Configuration Manager.</span></span> <span data-ttu-id="fcdbe-275">如需從 IIS 移除 Web 應用程式和應用程式集區的資訊，請參閱 [移除應用程式 (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) 和 [移除應用程式集區 (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538)。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-275">For information about removing web application and application pools from IIS, see [Remove an Application (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) and [Remove an Application Pool (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538).</span></span>  
  
5.  <span data-ttu-id="fcdbe-276">現在將新的 Web 應用程式與升級的 MDS 資料庫建立關聯。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-276">Now associate the new web application with the upgraded MDS database.</span></span>  
  
    1.  <span data-ttu-id="fcdbe-277">在 [建立應用程式與資料庫間的關聯] 區段中，按一下 [選取]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-277">In the **Associate Application with Database** section, click **Select**.</span></span>  
  
    2.  <span data-ttu-id="fcdbe-278">選取 MDS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-278">Select the MDS database.</span></span>  
  
    3.  <span data-ttu-id="fcdbe-279">按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-279">Click **Apply**.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="fcdbe-280">疑難排解</span><span class="sxs-lookup"><span data-stu-id="fcdbe-280">Troubleshooting</span></span>  
 <span data-ttu-id="fcdbe-281">**問題：** 當您開啟 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web 應用程式時，會顯示「用戶端版本與資料庫版本不相容」錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-281">**Issue:** When you open the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application, a "client version is not compatible with the database version" error message is displayed.</span></span>  
  
 <span data-ttu-id="fcdbe-282">**解決方案：** 當 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 主資料管理員 web 應用程式嘗試存取已升級為 Master Data Services 的資料庫時，就會發生這個問題 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-282">**Solution:** This issue occurs when a [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Master Data Manager web application tries to access a database that has been upgraded to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Master Data Services.</span></span> <span data-ttu-id="fcdbe-283">您必須改用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-283">You must use a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] web application instead.</span></span>  
  
 <span data-ttu-id="fcdbe-284">如果您升級 MDS 資料庫結構描述時，未在 IIS 中停止 [MDS 應用程式集區] 然後再重新啟動，也可能會發生此問題。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-284">This issue may also occur if you did not stop and restart the **MDS Application Pool** in IIS when upgrading the MDS database schema.</span></span> <span data-ttu-id="fcdbe-285">重新啟動 [MDS 應用程式集區] 即可更正此問題。</span><span class="sxs-lookup"><span data-stu-id="fcdbe-285">Restart the **MDS Application Pool** to correct the issue.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcdbe-286">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcdbe-286">See Also</span></span>  
 [<span data-ttu-id="fcdbe-287">安裝 Master Data Services</span><span class="sxs-lookup"><span data-stu-id="fcdbe-287">Install Master Data Services</span></span>](../../master-data-services/install-windows/install-master-data-services.md)  
  
  
