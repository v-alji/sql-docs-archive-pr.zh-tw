---
title: SQL Server 2014 的安裝 |Microsoft Docs
ms.custom: ''
ms.date: 09/09/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
f1_keywords:
- sql12.portal.Installation.f1
helpviewer_keywords:
- installing SQL Server, initial installation
- installation [SQL Server]
- initial installation [SQL Server]
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 62630400f276b00de8acfa875244558cdb39e47b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688150"
---
# <a name="installation-for-sql-server-2014"></a><span data-ttu-id="da656-102">SQL Server 2014 安裝</span><span class="sxs-lookup"><span data-stu-id="da656-102">Installation for SQL Server 2014</span></span>
 ## <a name="download-sql-server-2014-express"></a>[<span data-ttu-id="da656-103">下載 SQL Server 2014 Express</span><span class="sxs-lookup"><span data-stu-id="da656-103">Download SQL Server 2014 Express</span></span>](http://www.hanselman.com/blog/DownloadSQLServerExpress.aspx)
  <span data-ttu-id="da656-104">**感謝[Scott Hanselman](http://www.hanselman.com/)在一處收集所有安裝程式套件連結！**</span><span class="sxs-lookup"><span data-stu-id="da656-104">**Thank you to [Scott Hanselman](http://www.hanselman.com/) for collecting all of the installer package links in one place!**</span></span>
  
  <span data-ttu-id="da656-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝精靈提供了安裝所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件的單一功能樹狀目錄：</span><span class="sxs-lookup"><span data-stu-id="da656-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard provides a single feature tree to install all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components:</span></span>  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]  
  
-   [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]  
  
-   <span data-ttu-id="da656-106">管理工具</span><span class="sxs-lookup"><span data-stu-id="da656-106">Management tools</span></span>  
  
-   <span data-ttu-id="da656-107">連接元件</span><span class="sxs-lookup"><span data-stu-id="da656-107">Connectivity components</span></span>  
  
 <span data-ttu-id="da656-108">您可以個別安裝每個元件，也可以選取上面所列出元件的組合。</span><span class="sxs-lookup"><span data-stu-id="da656-108">You can install each component individually or select a combination of the components listed above.</span></span> <span data-ttu-id="da656-109">若要在中提供的版本和元件之間做出最佳選擇 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 的版本和元件](../../sql-server/editions-and-components-of-sql-server-2016.md)和[SQL Server 2014 版本所支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="da656-109">To make the best choice among the editions and components available in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Editions and Components of SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md) and [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="da656-110">有 32 位元和 64 位元兩種版本。</span><span class="sxs-lookup"><span data-stu-id="da656-110">is available in 32-bit and 64-bit editions.</span></span>
 
 <span data-ttu-id="da656-111">**試試看：**</span><span class="sxs-lookup"><span data-stu-id="da656-111">**Try it out:**</span></span>  
  
-   <span data-ttu-id="da656-112">有 Azure 帳戶嗎？</span><span class="sxs-lookup"><span data-stu-id="da656-112">Have an Azure account?</span></span>  <span data-ttu-id="da656-113">然後前往**[這裡](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2016RTMEnterpriseWindowsServer2012R2)** 來啟動已安裝 SQL Server 2014 Service Pack 1 (SP1) 的虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="da656-113">Then go **[Here](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2016RTMEnterpriseWindowsServer2012R2)** to spin up a Virtual Machine with SQL Server 2014 Service Pack 1 (SP1) already installed.</span></span> <span data-ttu-id="da656-114">如需 SQL Server 2014 (SP1) 的詳細資訊，請參閱[SQL Server 2014 Service Pack 1 版本資訊](https://support.microsoft.com/kb/3058865)。</span><span class="sxs-lookup"><span data-stu-id="da656-114">For more information on SQL Server 2014 (SP1), see [SQL Server 2014 Service Pack 1 release information](https://support.microsoft.com/kb/3058865).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="da656-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="da656-115">In This Section</span></span>  
 <span data-ttu-id="da656-116">不論您是使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝精靈或命令提示字元來安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，安裝程序都包括下列步驟：</span><span class="sxs-lookup"><span data-stu-id="da656-116">Regardless of whether you use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard or the command prompt to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Setup involves the following steps:</span></span>  
  
 [<span data-ttu-id="da656-117">規劃 SQL Server 安裝</span><span class="sxs-lookup"><span data-stu-id="da656-117">Planning a SQL Server Installation</span></span>](../../sql-server/install/planning-a-sql-server-installation.md)  
 <span data-ttu-id="da656-118">描述如何準備您的電腦安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="da656-118">Describes how to prepare your computer for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="da656-119">硬體及軟體需求。</span><span class="sxs-lookup"><span data-stu-id="da656-119">Hardware and software requirements.</span></span>  
  
-   <span data-ttu-id="da656-120">系統組態檢查需求和封鎖問題。</span><span class="sxs-lookup"><span data-stu-id="da656-120">System Configuration Checker requirements and blocking issues.</span></span>  
  
-   <span data-ttu-id="da656-121">安全性考量。</span><span class="sxs-lookup"><span data-stu-id="da656-121">Security considerations.</span></span>  
  
 [<span data-ttu-id="da656-122">安裝 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="da656-122">Install SQL Server 2014</span></span>](install-sql-server.md)  
 <span data-ttu-id="da656-123">說明 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的安裝選項。</span><span class="sxs-lookup"><span data-stu-id="da656-123">Describes installation options for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="da656-124">升級為 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="da656-124">Upgrade to SQL Server 2014</span></span>](upgrade-sql-server.md)  
 <span data-ttu-id="da656-125">說明用以升級至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的選項。</span><span class="sxs-lookup"><span data-stu-id="da656-125">Describes options for upgrading to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="da656-126">解除安裝 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="da656-126">Uninstall SQL Server 2014</span></span>](../../sql-server/install/uninstall-sql-server.md)  
 <span data-ttu-id="da656-127">說明解除安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 與 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]的程序。</span><span class="sxs-lookup"><span data-stu-id="da656-127">Describes procedures to uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].</span></span>  
  
 [<span data-ttu-id="da656-128">SQL Server 容錯移轉叢集安裝</span><span class="sxs-lookup"><span data-stu-id="da656-128">SQL Server Failover Cluster Installation</span></span>](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 <span data-ttu-id="da656-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式文件集中的這一節將說明如何安裝及設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集。</span><span class="sxs-lookup"><span data-stu-id="da656-129">This section of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup documentation explains how to install, and configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster.</span></span>  
  
 [<span data-ttu-id="da656-130">安裝 SQL Server 2014 BI 功能</span><span class="sxs-lookup"><span data-stu-id="da656-130">Install SQL Server 2014 BI Features</span></span>](../../sql-server/install/install-sql-server-business-intelligence-features.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="da656-131">屬於 Microsoft BI 平台的功能包括 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]，以及用來建立或處理分析資料的數種用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="da656-131">features that are part of the Microsoft BI platform include [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and several client applications used for creating or working with analytical data.</span></span> <span data-ttu-id="da656-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式文件中的這一節將說明如何安裝 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="da656-132">This section of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup documentation explains how to install [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="da656-133">相關章節</span><span class="sxs-lookup"><span data-stu-id="da656-133">Related Sections</span></span>  
 [<span data-ttu-id="da656-134">安裝的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="da656-134">Installation How-to Topics</span></span>](../../sql-server/install/installation-how-to-topics.md)  
 <span data-ttu-id="da656-135">提供如何從安裝精靈、從命令提示字元、使用組態檔及使用 SysPrep 安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的程序性主題連結。</span><span class="sxs-lookup"><span data-stu-id="da656-135">Provides links to procedural topics for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] from the installation wizard, from the command prompt, by using configuration files, and by using SysPrep.</span></span>  
  
 [<span data-ttu-id="da656-136">安裝 SharePoint &#40;PowerPivot 和 Reporting Services 的 SQL Server BI 功能&#41;</span><span class="sxs-lookup"><span data-stu-id="da656-136">Install SQL Server BI Features with SharePoint &#40;PowerPivot and Reporting Services&#41;</span></span>](../../sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md)  
 <span data-ttu-id="da656-137">本節說明如何在 SharePoint 環境中安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能，</span><span class="sxs-lookup"><span data-stu-id="da656-137">This section explains how to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features in a SharePoint environment.</span></span> <span data-ttu-id="da656-138">同時也會列出特定版本 SharePoint 能使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="da656-138">It identifies which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features are available given a specific version and edition of SharePoint.</span></span> <span data-ttu-id="da656-139">除此之外還會提供 PowerPivot for SharePoint 及 SharePoint 模式下的 Reporting Services 安裝程序。</span><span class="sxs-lookup"><span data-stu-id="da656-139">It also includes installation procedures for PowerPivot for SharePoint and Reporting Services in SharePoint mode.</span></span>  
  
 [<span data-ttu-id="da656-140">安裝 SQL Server 範例和範例資料庫</span><span class="sxs-lookup"><span data-stu-id="da656-140">Installing SQL Server Samples and Sample Databases</span></span>](https://sqlserversamples.codeplex.com/)  
 <span data-ttu-id="da656-141">描述如何安裝及設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 範例與範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="da656-141">Describes how to install and configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] samples and sample databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da656-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da656-142">See Also</span></span>  
 <span data-ttu-id="da656-143">[SQL Server 安裝的新功能](../../sql-server/install/what-s-new-in-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="da656-143">[What's New in SQL Server Installation](../../sql-server/install/what-s-new-in-sql-server-installation.md) </span></span>  
 [<span data-ttu-id="da656-144">安裝 SQL Server 2014 的硬體與軟體需求</span><span class="sxs-lookup"><span data-stu-id="da656-144">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
