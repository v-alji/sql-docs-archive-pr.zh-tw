---
title: 升級 Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- upgrading databases
- databases [Analysis Services], upgrading
- installing Analysis Services, side-by-side installations
- Analysis Services upgrades
- Analysis Services upgrades, about upgrading Analysis Services
- SSAS, database migration
- upgrading Analysis Services
- installing Analysis Services, upgrading
- SSAS, upgrading
ms.assetid: a131d329-386e-4470-aaa9-ffcde4e5ec0c
author: Minewiskan
ms.author: owend
ms.openlocfilehash: 78bf7f27233bcfd46bc1f189324eddc72adcc961
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594166"
---
# <a name="upgrade-analysis-services"></a><span data-ttu-id="0d6cd-102">升級 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="0d6cd-102">Upgrade Analysis Services</span></span>
  <span data-ttu-id="0d6cd-103">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式來升級 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0d6cd-103">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to upgrade [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0d6cd-104">如需有關以 SharePoint 模式升級的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[升級 PowerPivot for SharePoint](upgrade-power-pivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="0d6cd-104">For detailed information on upgrading [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in SharePoint mode, see [Upgrade PowerPivot for SharePoint](upgrade-power-pivot-for-sharepoint.md).</span></span> <span data-ttu-id="0d6cd-105">如需升級現有 SQL Server 實例的詳細資訊，請參閱[使用安裝精靈升級至 SQL Server 2014 &#40;安裝程式&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="0d6cd-105">For more information about upgrading an existing SQL Server instance, see [Upgrade to SQL Server 2014 Using the Installation Wizard &#40;Setup&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md).</span></span>  
  
## <a name="known-upgrade-issues"></a><span data-ttu-id="0d6cd-106">已知的升級問題</span><span class="sxs-lookup"><span data-stu-id="0d6cd-106">Known Upgrade Issues</span></span>  
 <span data-ttu-id="0d6cd-107">在升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]之前，請檢閱下列文章：</span><span class="sxs-lookup"><span data-stu-id="0d6cd-107">Before upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], review the following:</span></span>  
  
-   <span data-ttu-id="0d6cd-108">[SQL Server 2014 版本](https://go.microsoft.com/fwlink/?LinkID=296445)資訊。</span><span class="sxs-lookup"><span data-stu-id="0d6cd-108">[SQL Server 2014 Release Notes](https://go.microsoft.com/fwlink/?LinkID=296445).</span></span>  
  
-   <span data-ttu-id="0d6cd-109">若要瞭解哪些 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 特性和功能已停止、已被取代或變更，請參閱[Analysis Services 回溯相容性](https://docs.microsoft.com/analysis-services/analysis-services-backward-compatibility)。</span><span class="sxs-lookup"><span data-stu-id="0d6cd-109">To learn which [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] features and functionality have been discontinued, deprecated, or changed see [Analysis Services Backward Compatibility](https://docs.microsoft.com/analysis-services/analysis-services-backward-compatibility).</span></span>  
  
## <a name="pre-upgrade-checklist"></a><span data-ttu-id="0d6cd-110">升級前檢查清單</span><span class="sxs-lookup"><span data-stu-id="0d6cd-110">Pre-Upgrade Checklist</span></span>  
 <span data-ttu-id="0d6cd-111">升級之前，請先檢閱下列資訊：</span><span class="sxs-lookup"><span data-stu-id="0d6cd-111">Before upgrading, review the following information:</span></span>  
  
-   [<span data-ttu-id="0d6cd-112">支援的版本與版本升級</span><span class="sxs-lookup"><span data-stu-id="0d6cd-112">Supported Version and Edition Upgrades</span></span>](supported-version-and-edition-upgrades.md)  
  
-   [<span data-ttu-id="0d6cd-113">安裝 SQL Server 2014 的硬體與軟體需求</span><span class="sxs-lookup"><span data-stu-id="0d6cd-113">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [<span data-ttu-id="0d6cd-114">檢查 System Configuration Checker 的參數</span><span class="sxs-lookup"><span data-stu-id="0d6cd-114">Check Parameters for the System Configuration Checker</span></span>](check-parameters-for-the-system-configuration-checker.md)  
  
-   [<span data-ttu-id="0d6cd-115">SQL Server 安裝的安全性考量</span><span class="sxs-lookup"><span data-stu-id="0d6cd-115">Security Considerations for a SQL Server Installation</span></span>](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
-   [<span data-ttu-id="0d6cd-116">備份與還原 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="0d6cd-116">Backup and Restore of Analysis Services Databases</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases)  
  
-   [<span data-ttu-id="0d6cd-117">使用 Upgrade Advisor 來準備升級</span><span class="sxs-lookup"><span data-stu-id="0d6cd-117">Use Upgrade Advisor to Prepare for Upgrades</span></span>](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
## <a name="upgrading-analysis-services"></a><span data-ttu-id="0d6cd-118">升級 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="0d6cd-118">Upgrading Analysis Services</span></span>  
 <span data-ttu-id="0d6cd-119">您可以選擇許多方式來升級伺服器和資料：</span><span class="sxs-lookup"><span data-stu-id="0d6cd-119">You can choose from several approaches to upgrade server and data:</span></span>  
  
-   <span data-ttu-id="0d6cd-120">**就地升級**會以程式檔案取代現有的程式檔案 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0d6cd-120">An **in-place upgrade** replaces the existing program files with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] program files.</span></span> <span data-ttu-id="0d6cd-121">資料庫會保持在相同的位置。</span><span class="sxs-lookup"><span data-stu-id="0d6cd-121">Databases remain in the same location.</span></span> <span data-ttu-id="0d6cd-122">程式資料夾會更新以反映新的名稱。</span><span class="sxs-lookup"><span data-stu-id="0d6cd-122">Program folders are updated to reflect the new name.</span></span>  
  
-   <span data-ttu-id="0d6cd-123">**並存升級**是指 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在具有現有 Analysis Services 實例的同一部電腦上的新安裝。</span><span class="sxs-lookup"><span data-stu-id="0d6cd-123">A **side-by-side upgrade** is a new installation of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on the same computer that has an existing Analysis Services instance.</span></span> <span data-ttu-id="0d6cd-124">您可以將資料庫移至相同電腦上的新執行個體，然後解除安裝舊版 (如果不再使用它的話)。</span><span class="sxs-lookup"><span data-stu-id="0d6cd-124">You can move databases over to the new instance on the same computer, and then uninstall the old version if you no longer use it.</span></span>  
  
-   <span data-ttu-id="0d6cd-125">您也可以在新的硬體上安裝 Analysis Services，然後將現有的資料庫移轉至該伺服器。</span><span class="sxs-lookup"><span data-stu-id="0d6cd-125">You can also install Analysis Services on new hardware and then migrate existing databases to that server.</span></span>  
  
## <a name="in-place-upgrade"></a><span data-ttu-id="0d6cd-126">就地升級</span><span class="sxs-lookup"><span data-stu-id="0d6cd-126">In-place Upgrade</span></span>  
 <span data-ttu-id="0d6cd-127">您可以將現有的實例升級 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 至， [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 而在升級過程中，會將現有的資料庫從舊的實例自動遷移到新的實例。</span><span class="sxs-lookup"><span data-stu-id="0d6cd-127">You can upgrade an existing instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and, as part of the upgrade process, automatically migrate existing databases from the old instance to the new instance.</span></span> <span data-ttu-id="0d6cd-128">由於這兩個版本之間的中繼資料和二進位資料是相容的，所以在您升級之後將會保留資料，而且不必手動移轉資料。</span><span class="sxs-lookup"><span data-stu-id="0d6cd-128">Because the metadata and binary data is compatible between the two versions, you will retain the data after you upgrade and you do not have to manually migrate the data.</span></span>  
  
 <span data-ttu-id="0d6cd-129">若要升級現有的執行個體，請執行安裝程式，並指定現有執行個體的名稱做為新執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="0d6cd-129">To upgrade an existing instance, run Setup and specify the name of the existing instance as the name of the new instance.</span></span>  
  
## <a name="upgrading-databases"></a><span data-ttu-id="0d6cd-130">升級資料庫</span><span class="sxs-lookup"><span data-stu-id="0d6cd-130">Upgrading Databases</span></span>  
 <span data-ttu-id="0d6cd-131">在舊版 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中建立的資料庫會使用舊的資料庫相容性層級設定，在升級的伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="0d6cd-131">Databases that were created in previous versions of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] run on the upgraded server under an older database compatibility level setting.</span></span> <span data-ttu-id="0d6cd-132">在下列版本中建立的資料庫，其資料庫相容性層級為 105。</span><span class="sxs-lookup"><span data-stu-id="0d6cd-132">Databases created in the following versions, have a database compatibility level of 105.</span></span> <span data-ttu-id="0d6cd-133">如果您想要使用的功能需要更新的資料庫相容性層級，就可以變更相容性層級。</span><span class="sxs-lookup"><span data-stu-id="0d6cd-133">You can change the compatibility level if you want to use features that require a newer database compatibility level.</span></span> <span data-ttu-id="0d6cd-134">否則，您可以使用原始設定，在升級的伺服器上執行資料庫。</span><span class="sxs-lookup"><span data-stu-id="0d6cd-134">Otherwise, you can run the databases on the upgraded server using the original settings.</span></span> <span data-ttu-id="0d6cd-135">如需詳細資訊，請參閱[將多維度資料庫的相容性層級設定 &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services)。</span><span class="sxs-lookup"><span data-stu-id="0d6cd-135">For more information, see [Set the Compatibility Level of a Multidimensional Database &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services).</span></span>  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0d6cd-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d6cd-136">See Also</span></span>  
 <span data-ttu-id="0d6cd-137">[SQL Server 2014 版本所支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="0d6cd-137">[Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="0d6cd-138">[規劃 SQL Server 安裝](../../sql-server/install/planning-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="0d6cd-138">[Planning a SQL Server Installation](../../sql-server/install/planning-a-sql-server-installation.md) </span></span>  
 <span data-ttu-id="0d6cd-139">[瞭解 Microsoft OLAP 架構](https://docs.microsoft.com/analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture) </span><span class="sxs-lookup"><span data-stu-id="0d6cd-139">[Understanding Microsoft OLAP Architecture](https://docs.microsoft.com/analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture) </span></span>  
 <span data-ttu-id="0d6cd-140">[升級 PowerPivot for SharePoint](upgrade-power-pivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="0d6cd-140">[Upgrade PowerPivot for SharePoint](upgrade-power-pivot-for-sharepoint.md) </span></span>  
 <span data-ttu-id="0d6cd-141">[以多維度和資料採礦模式安裝 Analysis Services](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md) </span><span class="sxs-lookup"><span data-stu-id="0d6cd-141">[Install Analysis Services in Multidimensional and Data Mining Mode](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md) </span></span>  
 [<span data-ttu-id="0d6cd-142">PowerPivot for SharePoint 2010 安裝</span><span class="sxs-lookup"><span data-stu-id="0d6cd-142">PowerPivot for SharePoint 2010 Installation</span></span>](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
