---
title: 安裝 SharePoint 2010 Reporting Services SharePoint 模式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 47efa72e-1735-4387-8485-f8994fb08c8c
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 8be76ab37ce66f4ef93d29093202768aa85c4fb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598172"
---
# <a name="install-reporting-services-sharepoint-mode-for-sharepoint-2010"></a><span data-ttu-id="ad8ca-102">安裝適用於 SharePoint 2010 的 Reporting Services SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="ad8ca-102">Install Reporting Services SharePoint Mode for SharePoint 2010</span></span>
  <span data-ttu-id="ad8ca-103">本主題中的程序會引導您完成 SharePoint 模式之 Reporting Services 報表伺服器的單一伺服器安裝。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-103">The procedures in this topic guide you through a single server installation of a Reporting Services report server in SharePoint mode.</span></span> <span data-ttu-id="ad8ca-104">這些步驟包含執行 [SQL Server 安裝精靈]，以及使用 SharePoint 2010 管理中心的其他組態工作。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-104">The steps include running the SQL Server installation wizard as well as additional configuration tasks that use SharePoint 2010 central administration.</span></span> <span data-ttu-id="ad8ca-105">本主題也可以用於現有安裝的個別程序，例如建立 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-105">The topic can also be used for individual procedures for an existing installation, for example to create a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="ad8ca-106">如需將其他 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 伺服器加入至現有伺服器陣列的詳細資訊，請參閱[將其他報表伺服器新增至伺服器陣列 &#40;SSRS 向外延展&#41;](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md) ，然後[將額外的 Reporting Services Web 前端新增至伺服器](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)陣列。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-106">For information on adding additional [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] servers to an existing farm, see [Add an Additional Report Server to a Farm &#40;SSRS Scale-out&#41;](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md) and [Add an Additional Reporting Services Web Front-end to a Farm](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md).</span></span>  
  
||  
|-|  
|<span data-ttu-id="ad8ca-107">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="ad8ca-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010</span></span>|  
  
 <span data-ttu-id="ad8ca-108">單一伺服器安裝對開發和測試案例很實用，但是不建議在實際執行環境中使用。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-108">A single server installation is useful for development and testing scenarios but is not recommended for production environments.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ad8ca-109">如需將和現有 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式安裝升級至的相關資訊 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，請參閱[升級和遷移 Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-109">For information on upgrading and existing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode installation to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).</span></span>  
  

  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> <span data-ttu-id="ad8ca-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="ad8ca-110">Prerequisites</span></span>  
  
-   > [!IMPORTANT]  
    >  <span data-ttu-id="ad8ca-111">設定及管理 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式時，不再需要或支援 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-111">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager is no longer required or supported to configure and administer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span> <span data-ttu-id="ad8ca-112">您可以使用 SharePoint 管理中心，在 SharePoint 模式下設定報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-112">Use SharePoint Central Administration to configure a report server in SharePoint mode.</span></span> <span data-ttu-id="ad8ca-113">如需詳細資訊，請參閱[管理 Reporting Services SharePoint 服務應用程式](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-113">For more information, see [Manage a Reporting Services SharePoint Service Application](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).</span></span>  
  
-   <span data-ttu-id="ad8ca-114">檢閱下列需求主題，包括 SharePoint 2010 產品：</span><span class="sxs-lookup"><span data-stu-id="ad8ca-114">Review the following topics for requirements, including SharePoint 2010 products:</span></span>  
  
    -   [<span data-ttu-id="ad8ca-115">線上版本資訊</span><span class="sxs-lookup"><span data-stu-id="ad8ca-115">Online Release Notes</span></span>](https://msdn.microsoft.com/library/dn169381.aspx)
  
    -   [<span data-ttu-id="ad8ca-116">在 SharePoint 2010 伺服器陣列中使用 SQL Server BI 功能的指引</span><span class="sxs-lookup"><span data-stu-id="ad8ca-116">Guidance for Using SQL Server BI Features in a SharePoint 2010 Farm</span></span>](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
-   <span data-ttu-id="ad8ca-117">本主題不涵蓋 SharePoint 2010 產品的安裝。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-117">This topic does no cover the installation of SharePoint 2010 Products.</span></span> <span data-ttu-id="ad8ca-118">如需詳細資訊，請參閱[在 SharePoint 2010 伺服器陣列中使用 SQL SERVER BI 功能的指導](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)方針。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-118">For more information, see [Guidance for Using SQL Server BI Features in a SharePoint 2010 Farm](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md).</span></span>  
  
-   <span data-ttu-id="ad8ca-119">這些程序並非是用於設定 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 報表伺服器，而且亦不適用於舊版報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-119">These procedures are intended for configuring a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] report server and do not work for previous versions of report server.</span></span> <span data-ttu-id="ad8ca-120">舊版報表伺服器不是使用 SharePoint 共用服務架構。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-120">Previous versions of report server did not use the SharePoint Shared Service architecture.</span></span> <span data-ttu-id="ad8ca-121">例如，SQL Server 2008 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表伺服器和 SQL Server 2008 R2 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-121">For example, SQL Server 2008 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report servers and SQL Server 2008 R2 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report servers.</span></span>  
  
-   <span data-ttu-id="ad8ca-122">確認**SharePoint 2010 Administration**服務已在 Windows 伺服器管理員中啟動。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-122">Verify the **SharePoint 2010 Administration** service is started in Windows Server Manager.</span></span>  
  
 <span data-ttu-id="ad8ca-123">![在 1 個伺服器安裝上的 SSRS 元件](../../../2014/sql-server/install/media/rs-deployment-1-server.gif "在 1 個伺服器安裝上的 SSRS 元件")</span><span class="sxs-lookup"><span data-stu-id="ad8ca-123">![SSRS components on a 1 server installation](../../../2014/sql-server/install/media/rs-deployment-1-server.gif "SSRS components on a 1 server installation")</span></span>  
  
### <a name="database-considerations-for-a-single-server-configuration"></a><span data-ttu-id="ad8ca-124">單一伺服器組態的資料庫考量</span><span class="sxs-lookup"><span data-stu-id="ad8ca-124">Database Considerations for a Single Server Configuration</span></span>  
  
-   <span data-ttu-id="ad8ca-125">Reporting Services 和 SharePoint 產品及技術都使用 SQL Server 關聯式資料庫儲存應用程式資料。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-125">Both Reporting Services and SharePoint products and technologies use SQL Server relational databases to store application data.</span></span>  
  
-   [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] <span data-ttu-id="ad8ca-126">需要相容之 SQL 引擎的 SQL Server Evaluation Edition 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-126">requires a compatible SQL Server evaluation edition instance of the SQL Engine.</span></span>  
  
-   <span data-ttu-id="ad8ca-127">SharePoint 產品可以使用現有的資料庫執行個體。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-127">SharePoint products can use an existing database instance.</span></span> <span data-ttu-id="ad8ca-128">如果沒有安裝 Database Engine 執行個體，SharePoint 產品安裝程式會安裝 SQL Server Express Edition 做為 SharePoint 應用程式資料庫。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-128">If an instance of Database Engine is not installed, the SharePoint Products Setup program installs SQL Server Express Edition for the SharePoint application databases.</span></span>  
  
-   <span data-ttu-id="ad8ca-129">報表伺服器執行個體無法使用 SQL Server Express Edition 做為其資料庫；</span><span class="sxs-lookup"><span data-stu-id="ad8ca-129">The report server instance cannot use the SQL Server Express Edition for its database.</span></span> <span data-ttu-id="ad8ca-130">但是，由 SharePoint 產品所安裝的 SQL Server Express Edition 執行個體可以與其他 Database Engine 版本並存。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-130">However, the SQL Server Express Edition instance that is installed by the SharePoint product can exist side-by-side with other Database Engine editions.</span></span>  
  

  
##  <a name="install-reporting-services-report-server-in-sharepoint-mode"></a><a name="bkmk_install_SSRS"></a><span data-ttu-id="ad8ca-131">以 SharePoint 模式安裝 Reporting Services 報表伺服器</span><span class="sxs-lookup"><span data-stu-id="ad8ca-131">Install Reporting Services Report Server in SharePoint mode</span></span>  
  
1.  <span data-ttu-id="ad8ca-132">執行 [SQL Server 安裝精靈]。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-132">Run the SQL Server Installation Wizard.</span></span>  
  
2.  <span data-ttu-id="ad8ca-133">在精靈的左側按一下 **[安裝]** ，然後按一下 **[新增 SQL Server 獨立安裝或將功能加入至現有安裝]**。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-133">Click **Installation** in the left side of the wizard and then click **New SQL Server stand-alone installation or add features to an existing installation**.</span></span>  
  
3.  <span data-ttu-id="ad8ca-134">在 **[安裝程式支援規則]** 頁面上按一下 **[確定]** (假設已通過所有規則)。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-134">Click **OK** on the **Setup Support Rules** page, assuming all rules passed.</span></span>  
  
4.  <span data-ttu-id="ad8ca-135">在 **[安裝程式支援檔案]** 頁面中按一下 **[安裝]** 。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-135">Click **Install** on the **Setup Support Files** page.</span></span>  
  
5.  <span data-ttu-id="ad8ca-136">在支援檔案完成安裝且支援規則顯示 [**通過**] 狀態之後，按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-136">Click **Next** after the support files have completed installing and the support rules show a status of **passed**.</span></span> <span data-ttu-id="ad8ca-137">檢閱任何警告或封鎖問題。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-137">Review any warnings or blocking issues.</span></span>  
  
6.  <span data-ttu-id="ad8ca-138">在 [**產品金鑰**] 頁面上，輸入您的金鑰或接受「企業評估版」的預設值。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-138">On the **Product Key** page, type your key or accept the default of the 'Enterprise Evaluation' edition.</span></span>  
  
     <span data-ttu-id="ad8ca-139">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-139">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="ad8ca-140">檢閱並接受授權條款。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-140">Review and accept the license terms.</span></span> <span data-ttu-id="ad8ca-141">Microsoft 感謝您同意傳送功能使用資料，協助改進產品功能及支援。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-141">Microsoft appreciates you clicking to agree to send feature usage data to help improve product features and support.</span></span>  
  
     <span data-ttu-id="ad8ca-142">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-142">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="ad8ca-143">在 [**安裝程式角色**] 頁面上，選取 [ **SQL Server 功能安裝**]。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-143">Select **SQL Server Feature Installation** on the **Setup Role** page.</span></span>  
  
     <span data-ttu-id="ad8ca-144">按 **[下一步]**</span><span class="sxs-lookup"><span data-stu-id="ad8ca-144">Click **Next**</span></span>  
  
     <span data-ttu-id="ad8ca-145">![適用於安裝程式角色的 SQL Server 功能安裝](../../../2014/sql-server/install/media/rs-setuprole.gif "適用於安裝程式角色的 SQL Server 功能安裝")</span><span class="sxs-lookup"><span data-stu-id="ad8ca-145">![SQL Server Feature Installation for setup role](../../../2014/sql-server/install/media/rs-setuprole.gif "SQL Server Feature Installation for setup role")</span></span>  
  
9. <span data-ttu-id="ad8ca-146">在 **[特徵選取]** 頁面上，選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="ad8ca-146">Select the following on the **Feature Selection** page:</span></span>  
  
    -   <span data-ttu-id="ad8ca-147">**Reporting Services-SharePoint**</span><span class="sxs-lookup"><span data-stu-id="ad8ca-147">**Reporting Services - SharePoint**</span></span>  
  
    -   <span data-ttu-id="ad8ca-148">**適用于 SharePoint 2010 產品的 Reporting Services 增益集**。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-148">**Reporting Services add-in for SharePoint 2010 products**.</span></span> <span data-ttu-id="ad8ca-149">![注意](../../../2014/reporting-services/media/rs-fyinote.png "注意")安裝增益集的 [安裝精靈] 選項是版本的新功能 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-149">![note](../../../2014/reporting-services/media/rs-fyinote.png "note")The installation wizard option for installing the add-in is new with the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] release.</span></span>  
  
    -   <span data-ttu-id="ad8ca-150">如果您尚未有 SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體，您也可以針對完整的環境選取 **[Database Engine Services]** 和 **[管理工具 - 完整]** 。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-150">If you do not already have an instance of SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)], you could also select **Database Engine Services** and **Management Tools Complete** for a complete environment.</span></span>  
  
     <span data-ttu-id="ad8ca-151">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-151">Click **Next**.</span></span>  
  
     <span data-ttu-id="ad8ca-152">![適用于 SharePoint 模式的 SSRS 功能選取](../../../2014/sql-server/install/media/rs-setupfeatureselection-sharepoint-with-circles.gif "適用于 SharePoint 模式的 SSRS 功能選取")</span><span class="sxs-lookup"><span data-stu-id="ad8ca-152">![SSRS Feature Selection for SharePoint mode](../../../2014/sql-server/install/media/rs-setupfeatureselection-sharepoint-with-circles.gif "SSRS Feature Selection for SharePoint mode")</span></span>  
  
10. <span data-ttu-id="ad8ca-153">按一下 [**安裝規則**] 頁面上的 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-153">Click **Next** on the **Installation Rules** page.</span></span> <span data-ttu-id="ad8ca-154">檢閱任何警告或封鎖問題。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-154">Review any warnings or blocking issues.</span></span>  
  
11. <span data-ttu-id="ad8ca-155">如果您選取 Database Engine 服務，請接受 **[執行個體組態]** 頁面上的預設 **[MSSQLSERVER]** 執行個體，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-155">If you selected the Database Engine services, accept the default instance of **MSSQLSERVER** on the **Instance Configuration** page and click **Next**.</span></span> <span data-ttu-id="ad8ca-156">Reporting Services 共用服務架構與舊版 Reporting Services 架構不同，不是以 SQL Server「執行個體」為基礎。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-156">The Reporting Services shared service architecture is not based on a SQL Server "instance" was the previous Reporting Services architecture.</span></span>  
  
12. <span data-ttu-id="ad8ca-157">檢閱 **[磁碟空間需求]** 頁面，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-157">Review the **Disk Space Requirements** page and click **Next**.</span></span>  
  
13. <span data-ttu-id="ad8ca-158">在 [**伺服器**設定] 頁面上，輸入適當的認證。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-158">On the **Server Configuration** page type appropriate credentials.</span></span> <span data-ttu-id="ad8ca-159">如果您想要使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 資料警示或訂閱功能，則必須將 SQL Server Agent 的 **[啟動類型]** 變更為 **[自動]**。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-159">If you want to use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data alerting or subscription features, you need to change the **Startup Type** for SQL Server Agent to **Automatic**.</span></span>  
  
     <span data-ttu-id="ad8ca-160">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-160">Click **Next**.</span></span>  
  
14. <span data-ttu-id="ad8ca-161">如果您選取了 Database Engine 服務，就會看到 **[資料庫引擎組態]** 頁面。請將適當的帳戶加入至 SQL 管理員清單，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-161">If you selected the Database Engine services, you will see the **Database Engine Configuration** page, add appropriate accounts to the list of SQL Administrators and click **Next**.</span></span>  
  
15. <span data-ttu-id="ad8ca-162">在 **[Reporting Services 組態]** 頁面上，您應該會看到已選取 **[只安裝]** 選項。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-162">On the **Reporting Services Configuration** page you should see the **Install only** option is selected.</span></span> <span data-ttu-id="ad8ca-163">此選項會安裝報表伺服器檔案，但不會設定 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的 SharePoint 環境。完成 SQL Server 安裝之後，您需要遵循本主題中的其他章節設定 SharePoint 環境，</span><span class="sxs-lookup"><span data-stu-id="ad8ca-163">This option installs the report server files, and does not configure the SharePoint environment for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].When the SQL Server installation is complete, follow the other sections of this topic to configure the SharePoint environment.</span></span> <span data-ttu-id="ad8ca-164">包括安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共用服務及建立 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-164">This Includes installing the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service and creating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span>  
  
     <span data-ttu-id="ad8ca-165">![rs_SQL11_SETUP_SSRS_configpage_withcircles](../../../2014/sql-server/install/media/rs-kj-setup-ssrs-configpage-withcircles.gif "rs_SQL11_SETUP_SSRS_configpage_withcircles")</span><span class="sxs-lookup"><span data-stu-id="ad8ca-165">![rs_SQL11_SETUP_SSRS_configpage_withcircles](../../../2014/sql-server/install/media/rs-kj-setup-ssrs-configpage-withcircles.gif "rs_SQL11_SETUP_SSRS_configpage_withcircles")</span></span>  
  
16. <span data-ttu-id="ad8ca-166">按一下 **[錯誤報告]** 頁面上的核取方塊傳送錯誤報告，協助 Microsoft 改進 SQL Server 功能與服務。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-166">Help Microsoft improve SQL Server features and services by clicking the check box to send error reports on the **Error Reporting** page.</span></span>  
  
     <span data-ttu-id="ad8ca-167">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-167">Click **Next**.</span></span>  
  
17. <span data-ttu-id="ad8ca-168">檢閱任何警告，然後在 **[安裝組態規則]** 頁面上按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-168">Review any warnings and then click **Next** on the **Installation Configuration Rules** page.</span></span>  
  
18. <span data-ttu-id="ad8ca-169">在 **[準備安裝]** 頁面上檢閱安裝摘要，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-169">On the **Ready to Install** page, review the installation summary and then click **Next**.</span></span> <span data-ttu-id="ad8ca-170">摘要會包含**Reporting Services**節點，其中包含**SharePointFilesOnlyMode**的安裝模式值以及帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-170">The summary will include a **Reporting Services** node that will include the installation mode value of **SharePointFilesOnlyMode** as well as the account information.</span></span>  
  

  
##  <a name="install-and-start-the-reporting-services-sharepoint-service"></a><a name="bkmk_install_SSRS_sharedservice"></a><span data-ttu-id="ad8ca-171">安裝並啟動 Reporting Services SharePoint 服務</span><span class="sxs-lookup"><span data-stu-id="ad8ca-171">Install and Start the Reporting Services SharePoint Service</span></span>  
 <span data-ttu-id="ad8ca-172">![PowerShell 相關內容](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell 相關內容")</span><span class="sxs-lookup"><span data-stu-id="ad8ca-172">![PowerShell related content](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell related content")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ad8ca-173">如果您要將安裝到現有的 SharePoint 伺服器陣列中，**則不需要**完成本節中的步驟。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-173">If you are installing into an existing SharePoint farm, **you do not need to** complete the steps in this section.</span></span> <span data-ttu-id="ad8ca-174">在上一節執行 [SQL Server 安裝精靈] 時，會安裝並啟動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 服務。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-174">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint service was installed and started when you ran the SQL Server installation wizard in the previous section.</span></span>  
  
 <span data-ttu-id="ad8ca-175">必要檔案會隨 [SQL Server 安裝精靈] 安裝，但是您必須在 SharePoint 伺服器陣列中註冊服務。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-175">The necessary files were installed as part of the SQL Server installation wizard, but the services need to be registered into the SharePoint farm.</span></span> <span data-ttu-id="ad8ca-176">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本引進了適用於 SharePoint 模式中 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的 PowerShell 支援。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-176">The [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] release introduces PowerShell support for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="ad8ca-177">下列步驟將引導您開啟 SharePoint 管理命令介面並執行指令程式：</span><span class="sxs-lookup"><span data-stu-id="ad8ca-177">The following steps guide you through opening the SharePoint Management Shell and running cmdlets:</span></span>  
  
1.  <span data-ttu-id="ad8ca-178">按一下 [**開始**] 按鈕</span><span class="sxs-lookup"><span data-stu-id="ad8ca-178">Click the **Start** button</span></span>  
  
2.  <span data-ttu-id="ad8ca-179">按一下 [ **Microsoft SharePoint 2010 產品**] 群組。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-179">Click the **Microsoft SharePoint 2010 Products** group.</span></span>  
  
3.  <span data-ttu-id="ad8ca-180">以滑鼠右鍵按一下 [ **SharePoint 2010 管理命令**介面] 按一下 [**以系統管理員身分執行**]。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-180">Right-click **SharePoint 2010 Management Shell** click **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="ad8ca-181">執行下列 PowerShell 命令安裝 SharePoint 服務。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-181">Run the following PowerShell command to install the SharePoint service.</span></span> <span data-ttu-id="ad8ca-182">成功完成命令會在管理命令介面中顯示新行。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-182">A successful completion of the command displays a new line in the management shell.</span></span> <span data-ttu-id="ad8ca-183">成功完成命令之後，不會有任何訊息傳回管理命令介面：</span><span class="sxs-lookup"><span data-stu-id="ad8ca-183">No message is returned to the management shell when the command completes successfully:</span></span>  
  
    ```powershell
    Install-SPRSService  
    ```  
  
5.  <span data-ttu-id="ad8ca-184">執行下列 PowerShell 命令安裝服務 Proxy：</span><span class="sxs-lookup"><span data-stu-id="ad8ca-184">Run the following PowerShell command to install the service proxy:</span></span>  
  
    ```powershell
    Install-SPRSServiceProxy  
    ```  
  
6.  <span data-ttu-id="ad8ca-185">執行下列 PowerShell 命令啟動服務，或參閱下列附註，以取得從 SharePoint 管理中心啟動服務的指示：</span><span class="sxs-lookup"><span data-stu-id="ad8ca-185">Run the following PowerShell command to start the service or see the following notes for instructions to start the service from SharePoint Central administration:</span></span>  
  
    ```powershell
    Get-SPServiceInstance -All | Where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
    ```  
  
 <span data-ttu-id="ad8ca-186">您也可以從 SharePoint 管理中心啟動服務，而不是執行第三個 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-186">You can also start the service from SharePoint central Administration rather than running the third PowerShell command.</span></span> <span data-ttu-id="ad8ca-187">下列步驟也可用於確認服務是否執行。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-187">The following steps are also useful to verify that the service is running.</span></span>  
  
1.  <span data-ttu-id="ad8ca-188">在 SharePoint 管理中心內，按一下 **[系統設定]** 群組中的 **[管理伺服器上的服務]** 。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-188">In SharePoint Central Administration, click **Manage Services on Server** in the **System Settings** group.</span></span>  
  
2.  <span data-ttu-id="ad8ca-189">找到 **[SQL Server Reporting Services 服務]** ，然後按一下 [動作] 欄中的 **[啟動]** 。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-189">Find **SQL Server Reporting Services Service** and click **Start** in the Action column.</span></span>  
  
3.  <span data-ttu-id="ad8ca-190">Reporting Services 服務的狀態會從 **[已停止]** 變更為 **[已啟動]**。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-190">The status of the Reporting Services service will change from **Stopped** to **Started**.</span></span> <span data-ttu-id="ad8ca-191">如果清單中沒有 Reporting Services 服務，請使用 PowerShell 安裝該服務。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-191">If the Reporting Services service is not in the list, use PowerShell to install the service.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ad8ca-192">如果 Reporting Services 服務停留在 [**啟動**中] 狀態，而未變更為 [**已啟動**]，請確認已在 Windows 伺服器管理員中啟動「SharePoint 2010 系統管理」服務。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-192">If the Reporting Services service stays in the **Starting** status and does not change to **Started**, verify the 'SharePoint 2010 Administration' service is started in Windows Server Manager.</span></span>  

##  <a name="create-a-reporting-services-service-application"></a><a name="bkmk_create_serrviceapplication"></a><span data-ttu-id="ad8ca-193">建立 Reporting Services 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="ad8ca-193">Create a Reporting Services Service Application</span></span>  
 <span data-ttu-id="ad8ca-194">本節提供建立服務應用程式的步驟，以及屬性的描述 (如果您要檢閱現有的服務應用程式)。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-194">This section provides the steps to create a service application and a description of the properties, if you are reviewing an existing service application.</span></span>  
  
1.  <span data-ttu-id="ad8ca-195">在 [SharePoint 管理中心] 的 [**應用程式管理**] 群組中，按一下 [**管理服務應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-195">In SharePoint Central Administration, in the **Application Management** group, click **Manage Service Applications**.</span></span>  
  
2.  <span data-ttu-id="ad8ca-196">在 SharePoint 功能區中，按一下 **[新增]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-196">In the SharePoint ribbon, click the **New** button.</span></span>  
  
3.  <span data-ttu-id="ad8ca-197">在 [新增] 功能表中，按一下 **[SQL Server Reporting Services 服務應用程式]**。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-197">In the New menu, click **SQL Server Reporting Services Service Application.**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="ad8ca-198">如果此 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 選項未出現在清單中，表示\*\* [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 未安裝共用服務\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-198">If the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] option does not appear in the list, it is an **indication that the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service is not installed**.</span></span> <span data-ttu-id="ad8ca-199">檢閱上一節中，如何使用 PowerShell Cmdlt 來安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-199">Review the previous section on how to use PowerShell cmdlts to install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service.</span></span>  
  
4.  <span data-ttu-id="ad8ca-200">在 **[建立新的 SQL Server Reporting Services 服務應用程式]** 頁面中，輸入應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-200">In the **Create SQL Server Reporting Services Service Application** page, enter a name for the application.</span></span> <span data-ttu-id="ad8ca-201">如果您要建立多個 Reporting Services 服務應用程式，描述性名稱或命名慣例可協助您安排管理及管理作業工作。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-201">If you are creating multiple Reporting Services service applications, a descriptive name or naming convention helps you organize your administration and management operations.</span></span>  
  
5.  <span data-ttu-id="ad8ca-202">在 **[應用程式集區]** 區段中，建立應用程式的新應用程式集區 (建議)。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-202">In **Application Pool** section, create a new application pool for the application (recommended).</span></span> <span data-ttu-id="ad8ca-203">針對新應用程式集區，使用與服務應用程式相同的名稱，可讓進行中的管理更容易。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-203">Using the same name for the new application pool as the service application, makes ongoing administration easier.</span></span>  
  
     <span data-ttu-id="ad8ca-204">請針對此應用程式集區選取或建立受管理的帳戶。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-204">Select or create a managed account for the application pool.</span></span> <span data-ttu-id="ad8ca-205">請務必指定網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-205">Be sure to specify a domain user account.</span></span> <span data-ttu-id="ad8ca-206">網域使用者帳戶會啟用 SharePoint 受管理帳戶功能，好讓您在一個地方更新密碼和帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-206">A domain user account enables the use of the SharePoint managed account feature, which lets you update passwords and account information in one place.</span></span> <span data-ttu-id="ad8ca-207">如果您計劃將部署向外延展，以包括在相同識別下執行的其他服務執行個體，也需要網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-207">Domain accounts are also required if you plan to scale out the deployment to include additional service instances that run under the same identity.</span></span>  
  
6.  <span data-ttu-id="ad8ca-208">在 **[資料庫伺服器]** 中，您可以使用目前的伺服器或選擇不同的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-208">In the **Database Server**, you can use the current server or choose a different SQL Server.</span></span>  
  
7.  <span data-ttu-id="ad8ca-209">在 **[資料庫名稱]** 中，預設值是 `ReportingService_<guid>`，這是唯一的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-209">In **Database Name** the default value is `ReportingService_<guid>`, which is a unique database name.</span></span> <span data-ttu-id="ad8ca-210">若您要輸入新值，請輸入唯一值。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-210">If you type a new value, type a unique value.</span></span>  
  
8.  <span data-ttu-id="ad8ca-211">在 **[資料庫驗證]** 中，預設值是 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-211">In **Database Authentication**, the default is Windows Authentication.</span></span> <span data-ttu-id="ad8ca-212">如果您選擇 **[SQL 驗證]**，請參考 SharePoint 管理員指南，以了解有關如何在 SharePoint 部署中使用這個驗證類型的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-212">If you choose **SQL Authentication**, refer to the SharePoint administrator guide for best practices on how to use this authentication type in a SharePoint deployment.</span></span>  
  
9. <span data-ttu-id="ad8ca-213">在 **[Web 應用程式關聯]** 區段中，選取要佈建以供目前 Reporting Services 服務應用程式存取的 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-213">In the **Web Application Association** section, select the Web Application to be provisioned for access by the current Reporting Services Service Application.</span></span> <span data-ttu-id="ad8ca-214">您可以建立一個 Reporting Services 服務應用程式與一個 Web 應用程式的關聯。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-214">You can associate one Reporting Services service application to one web application.</span></span> <span data-ttu-id="ad8ca-215">如果目前所有的 Web 應用程式已有相關聯的 Reporting Services 服務應用程式，則會顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-215">If all of the current web applications are already associated with a Reporting Services service application, you see a warning message.</span></span>  
  
10. <span data-ttu-id="ad8ca-216">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-216">Click **OK**.</span></span>  
  
11. <span data-ttu-id="ad8ca-217">服務應用程式的建立程序會需要數分鐘才能完成。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-217">The process to create a service application could take several minutes to complete.</span></span> <span data-ttu-id="ad8ca-218">完成後，您會看到確認訊息及 **[提供訂閱和警示]** 頁面的連結。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-218">When it is complete, you will see a confirmation message and a link to a **Provision Subscriptions and Alerts** page.</span></span> <span data-ttu-id="ad8ca-219">如果您想使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 訂閱和警示功能，請完成佈建步驟。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-219">Complete the provision step if you want to use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscriptions and alerts features.</span></span> <span data-ttu-id="ad8ca-220">如需詳細資訊，請參閱 [SSRS 服務應用程式的佈建訂用帳戶及警示](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-220">For more information, see [Provision Subscriptions and Alerts for SSRS Service Applications](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md).</span></span>  
  
 <span data-ttu-id="ad8ca-221">![PowerShell 相關內容](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell 相關內容")如需使用 PowerShell 建立 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式的相關資訊，請參閱[使用 powershell 建立 Reporting Services 服務應用程式](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md#bkmk_powershell_create_ssrs_serviceapp)。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-221">![PowerShell related content](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell related content") For information on using PowerShell to create a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application, see [To create a Reporting Services Service Application using PowerShell](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md#bkmk_powershell_create_ssrs_serviceapp).</span></span>  
  

  
##  <a name="activate-the-power-view-site-collection-feature"></a><a name="bkmk_powerview"></a><span data-ttu-id="ad8ca-222">啟動 Power View 網站集合功能。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-222">Activate the Power View Site Collection Feature.</span></span>  
 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]<span data-ttu-id="ad8ca-223">（ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 適用于 Enterprise Edition 之增益集的功能） [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 是網站集合功能。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-223">, a feature of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Enterprise Edition, is a site collection feature.</span></span> <span data-ttu-id="ad8ca-224">將會針對根網站集合以及安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集之後所建立的網站集合自動啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-224">The feature is activated automatically for root site collections and site collections created after the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in is installed.</span></span> <span data-ttu-id="ad8ca-225">如果您打算使用 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]，請確認此功能是否已啟用。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-225">If you plan to use [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], verify that the feature is activated.</span></span>  
  
 <span data-ttu-id="ad8ca-226">如果您在安裝 SharePoint 2010 產品之後安裝適用於 SharePoint 2010 產品的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集，則只會針對根網站集合啟用報表伺服器整合功能和 Power View 整合功能。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-226">If you install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint 2010 Products after the installation of the SharePoint 2010 product, then the Report Server integration feature and the Power View integration feature will only be activated for root site collections.</span></span> <span data-ttu-id="ad8ca-227">如果是其他網站集合，請手動啟用這些功能。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-227">For other site collections, manually activate the features.</span></span>  
  
#### <a name="to-activate-the-power-view-feature"></a><span data-ttu-id="ad8ca-228">若要啟用 Power View 功能</span><span class="sxs-lookup"><span data-stu-id="ad8ca-228">To Activate the Power View Feature</span></span>  
  
1.  <span data-ttu-id="ad8ca-229">開啟瀏覽器，移至所要的 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-229">Open your browser to the desired SharePoint site.</span></span>  
  
2.  <span data-ttu-id="ad8ca-230">按一下 **[網站動作]** 。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-230">Click **Site Actions**.</span></span>  
  
3.  <span data-ttu-id="ad8ca-231">按一下 **[站台設定]** 。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-231">Click **Site Settings**.</span></span>  
  
4.  <span data-ttu-id="ad8ca-232">在網站集合管理群組中，按一下 **[網站集合功能]** 。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-232">Click **Site Collection Features** in the Site Collection Administration Group.</span></span>  
  
5.  <span data-ttu-id="ad8ca-233">在清單中尋找 **[Power View 整合功能]** 。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-233">Find **Power View Integration Feature** in the list.</span></span>  
  
6.  <span data-ttu-id="ad8ca-234">按一下 [啟用]。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-234">Click **Activate**.</span></span>  
  
 <span data-ttu-id="ad8ca-235">每個網站集合都已完成這個程序。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-235">This procedure is completed per site collection.</span></span> <span data-ttu-id="ad8ca-236">如需詳細資訊，請參閱[在 SharePoint 中啟用報表伺服器和 Power View 整合功能](../../reporting-services/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-236">For more information, see [Activate the Report Server and Power View Integration Features in SharePoint](../../reporting-services/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)  .</span></span>  
  
##  <a name="additional-configuration"></a><a name="bkmk_additional_config"></a><span data-ttu-id="ad8ca-237">其他設定</span><span class="sxs-lookup"><span data-stu-id="ad8ca-237">Additional Configuration</span></span>  
 <span data-ttu-id="ad8ca-238">本節描述多數 SharePoint 部署中重要的其他組態步驟。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-238">This section describes additional configuration steps that are important in most SharePoint deployments.</span></span>  
  
###  <a name="provision-subscriptions-and-alerts"></a><a name="bkmk_provision_agent"></a><span data-ttu-id="ad8ca-239">布建訂閱和警示</span><span class="sxs-lookup"><span data-stu-id="ad8ca-239">Provision Subscriptions and Alerts</span></span>  
 <span data-ttu-id="ad8ca-240">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 訂閱和資料警示可能需要 SQL Server Agent 權限組態。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-240">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscription and data alert features may require the configuration of SQL Server Agent permissions.</span></span> <span data-ttu-id="ad8ca-241">如果您看到錯誤訊息，指出需要 SQL Server Agent，且您已確認 SQL Server Agent 正在執行，則請更新權限。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-241">If you see an error message that indicates SQL Server Agent is required and you have verified SQL Server Agent is running, update the permissions.</span></span> <span data-ttu-id="ad8ca-242">您可以在成功建立服務應用程式頁面上，按一下 **[提供訂閱和警示]** 連結，以移至其他頁面並提供 SQL Server Agent。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-242">You can click the link **Provision Subscriptions and Alerts** on the create service application success page to go to another page for provisioning SQL Server Agent.</span></span> <span data-ttu-id="ad8ca-243">如果您的部署跨電腦界限 (例如 SQL Server 資料庫執行個體位於其他電腦上)，則需要提供步驟。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-243">The provision step is needed if your deployment crosses machine boundaries, for example when the SQL Server database instance is on a different machine.</span></span> <span data-ttu-id="ad8ca-244">如需詳細資訊，請參閱[SSRS 服務應用程式的布建訂閱和警示](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)</span><span class="sxs-lookup"><span data-stu-id="ad8ca-244">For more information, see [Provision Subscriptions and Alerts for SSRS Service Applications](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)</span></span>  
  

  
### <a name="configure-e-mail-for-a-service-application"></a><span data-ttu-id="ad8ca-245">設定服務應用程式的電子郵件</span><span class="sxs-lookup"><span data-stu-id="ad8ca-245">Configure e-mail for a service application</span></span>  
 <span data-ttu-id="ad8ca-246">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 資料警示功能會以電子郵件訊息傳送警示。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-246">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data alerts feature sends alerts in e-mail messages.</span></span> <span data-ttu-id="ad8ca-247">若要傳送電子郵件，您可能需要設定 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式，以及修改服務應用程式的電子郵件傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-247">To send e-mail you may need to configure your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application and you may need to modify the e-mail delivery extension for the service application.</span></span> <span data-ttu-id="ad8ca-248">如果您計劃針對 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 訂閱功能使用電子郵件傳遞延伸模組，則需要電子郵件設定。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-248">If you plan to use the e-mail delivery extension for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscription feature, the e-mail settings are required.</span></span> <span data-ttu-id="ad8ca-249">如需詳細資訊，請參閱[設定 Reporting Services 服務應用程式的電子郵件 &#40;SharePoint 2010 和 SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md)。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-249">For more information, see [Configure E-mail for a Reporting Services Service Application &#40;SharePoint 2010 and SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md)</span></span>  
  

  
### <a name="add-reporting-services-content-types"></a><span data-ttu-id="ad8ca-250">加入 Reporting Services 內容類型</span><span class="sxs-lookup"><span data-stu-id="ad8ca-250">Add Reporting Services Content Types</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="ad8ca-251">會提供預先定義的內容類型，可用來管理共用資料來源 (.rsds) 檔、報表模型 (.smdl) 檔，以及報表產生器的報表定義 (.rdl) 檔。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-251">provides predefined content types that are used to manage shared data source (.rsds) files, report models (.smdl), and Report Builder report definition (.rdl) files.</span></span> <span data-ttu-id="ad8ca-252">將 **[報表產生器報表]**、 **[報表模型]** 和 **[報表資料來源]** 內容類型加入至文件庫會啟用 **[新增]** 命令，讓您能夠建立該類型的新文件。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-252">Adding a **Report Builder Report**, **Report Model**, and **Report Data Source** content type to a library enables the **New** command so that you can create new documents of that type.</span></span> <span data-ttu-id="ad8ca-253">如需詳細資訊，請參閱[將報表伺服器內容類型加入至程式庫 &#40;SharePoint 整合模式中的 Reporting Services&#41;](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-253">For more information, see [Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).</span></span>  
  

  
### <a name="activate-the-file-sync-feature"></a><span data-ttu-id="ad8ca-254">啟用檔案同步處理功能</span><span class="sxs-lookup"><span data-stu-id="ad8ca-254">Activate the File sync feature</span></span>  
 <span data-ttu-id="ad8ca-255">如果使用者經常直接上傳已發行的報表項目至 SharePoint 文件庫，報表伺服器檔案同步處理功能會很有協助。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-255">If users will frequently upload published report items directly to SharePoint document libraries, the report server file sync feature will be beneficial.</span></span> <span data-ttu-id="ad8ca-256">檔案同步處理功能會更頻繁地同步處理報表伺服器目錄與文件庫中的項目。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-256">The file sync feature will synchronize the report server catalog with items in document libraries on a more frequent basis.</span></span> <span data-ttu-id="ad8ca-257">如需詳細資訊，請參閱 [在 SharePoint 管理中心啟動報表伺服器檔案同步處理功能](../../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)。</span><span class="sxs-lookup"><span data-stu-id="ad8ca-257">For more information, see [Activate the Report Server File Sync Feature in SharePoint Central Administration](../../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad8ca-258">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad8ca-258">See Also</span></span>  
 <span data-ttu-id="ad8ca-259">[適用于 Reporting Services SharePoint 模式的 PowerShell Cmdlet](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="ad8ca-259">[PowerShell cmdlets for Reporting Services SharePoint Mode](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="ad8ca-260">[SQL Server 2012 版本所支援的功能](https://go.microsoft.com/fwlink/?linkid=232473) </span><span class="sxs-lookup"><span data-stu-id="ad8ca-260">[Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) </span></span>  
 [<span data-ttu-id="ad8ca-261">Reporting Services SharePoint 服務和服務應用程式</span><span class="sxs-lookup"><span data-stu-id="ad8ca-261">Reporting Services SharePoint Service and Service Applications</span></span>](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md)  
