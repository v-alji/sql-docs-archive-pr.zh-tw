---
title: 以多維度和資料採礦模式安裝 Analysis Services |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Analysis Services, about installing Analysis Services
- installing Analysis Services
- SSAS, installing
- Analysis Services, installing
- SQL Server Analysis Services, installing
ms.assetid: 8a1f33e8-2bd6-4fb8-bd46-c86f2a067f60
author: heidisteen
ms.author: heidist
ms.openlocfilehash: e88d4440a65392b4f6351fa2503ea7819cf528b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585776"
---
# <a name="install-analysis-services-in-multidimensional-and-data-mining-mode"></a><span data-ttu-id="ae173-102">以多維度及資料採礦模式安裝 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="ae173-102">Install Analysis Services in Multidimensional and Data Mining Mode</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="ae173-103">提供商業智慧應用程式的線上分析處理 (OLAP) 和資料採礦功能。</span><span class="sxs-lookup"><span data-stu-id="ae173-103">provides online analytical processing (OLAP) and data mining functionality for business intelligence applications.</span></span> <span data-ttu-id="ae173-104">在此版本中，當您 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 在多*維度模式下*安裝時，可以使用 OLAP 資料庫和資料採礦模型的支援。</span><span class="sxs-lookup"><span data-stu-id="ae173-104">In this release, support for OLAP databases and data mining models is available when you install [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in *Multidimensional mode*.</span></span> <span data-ttu-id="ae173-105">多維度模式是執行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的三種伺服器模式之一，</span><span class="sxs-lookup"><span data-stu-id="ae173-105">Multidimensional mode is one of three server modes that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] runs in.</span></span> <span data-ttu-id="ae173-106">也是預設模式。</span><span class="sxs-lookup"><span data-stu-id="ae173-106">It is the default mode.</span></span> <span data-ttu-id="ae173-107">如果您使用預設值安裝 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]，則會取得執行多維度資料庫和資料採礦模型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae173-107">If you install [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] using default values, you will get an instance that runs multidimensional databases and data mining models.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="ae173-108">是一項多執行個體功能，表示您可以在單一電腦上安裝一個以上的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體，或是與舊版並存執行新的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae173-108">is a multi-instance feature, which means that you can install more than one instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] on a single computer, or run a new instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] side-by-side an earlier version.</span></span> <span data-ttu-id="ae173-109">每個執行個體會有特定的伺服器模式。</span><span class="sxs-lookup"><span data-stu-id="ae173-109">Server mode is specific to an instance.</span></span> <span data-ttu-id="ae173-110">使用其他模式需要您安裝其他伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae173-110">Using other modes requires that you install additional instances of the server.</span></span>  
  
 <span data-ttu-id="ae173-111">您可以單獨安裝 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]，或是一併安裝其他元件。</span><span class="sxs-lookup"><span data-stu-id="ae173-111">You can install [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] by itself or with other components.</span></span> <span data-ttu-id="ae173-112">如果您只安裝 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，當您在安裝精靈的 [特徵選取] 頁面上選取 [ **Analysis Services** ] 時，會安裝下列功能 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="ae173-112">If you install just [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the following features are installed when you select **Analysis Services** on the Feature Selection page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard:</span></span>  
  
-   <span data-ttu-id="ae173-113">用於執行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫和資料採礦模型的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器</span><span class="sxs-lookup"><span data-stu-id="ae173-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server for running [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases and data mining models</span></span>  
  
-   <span data-ttu-id="ae173-114">用於進行來源資料庫之 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料存取的資料提供者</span><span class="sxs-lookup"><span data-stu-id="ae173-114">Data providers used for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data access to source databases</span></span>  
  
-   <span data-ttu-id="ae173-115">SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="ae173-115">SQL Server Configuration Manager</span></span>  
  
## <a name="choosing-additional-features"></a><span data-ttu-id="ae173-116">選擇其他功能</span><span class="sxs-lookup"><span data-stu-id="ae173-116">Choosing additional features</span></span>  
 <span data-ttu-id="ae173-117">Analysis Services OLAP 和資料倉儲方案將需要安裝其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件，才能開發、部署和管理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ae173-117">Analysis Services OLAP and data warehouse solutions will require the installation of additional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components to enable the development, deployment, and administration of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases.</span></span> <span data-ttu-id="ae173-118">下列其他功能是許多典型使用者案例的選項：</span><span class="sxs-lookup"><span data-stu-id="ae173-118">The following additional features are options for many typical user scenarios:</span></span>  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="ae173-119">，用於建立和檢視 Analysis Services 資料結構和資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="ae173-119">, used to create and view Analysis Services data structures and data mining models.</span></span>  
  
-   <span data-ttu-id="ae173-120">用戶端工具連接性元件，用於在用戶端和伺服器之間進行通訊，包括 DB-Library、ODBC 和 OLE DB 的網路程式庫。</span><span class="sxs-lookup"><span data-stu-id="ae173-120">Client tools connectivity components, used for communication between clients and servers, including network libraries for DB-Library, ODBC, and OLE DB.</span></span>  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]<span data-ttu-id="ae173-121">，用來移動、複製和轉換資料的一組圖形化和可程式化物件。</span><span class="sxs-lookup"><span data-stu-id="ae173-121">, a set of graphical and programmable objects for moving, copying, and transforming data.</span></span>  
  
-   <span data-ttu-id="ae173-122">管理工具，包括 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 和複寫監視器。</span><span class="sxs-lookup"><span data-stu-id="ae173-122">Management tools, including [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], and Replication Monitor.</span></span>  
  
## <a name="installation-tasks"></a><span data-ttu-id="ae173-123">安裝工作</span><span class="sxs-lookup"><span data-stu-id="ae173-123">Installation Tasks</span></span>  
 <span data-ttu-id="ae173-124">安裝工作包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="ae173-124">Installation tasks include the following:</span></span>  
  
|<span data-ttu-id="ae173-125">連結</span><span class="sxs-lookup"><span data-stu-id="ae173-125">Links</span></span>|<span data-ttu-id="ae173-126">工作</span><span class="sxs-lookup"><span data-stu-id="ae173-126">Tasks</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="ae173-127">安裝 SQL Server 2014 和[設定 Windows 服務帳戶和許可權](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)[的硬體和軟體需求](hardware-and-software-requirements-for-installing-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ae173-127">[Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>|<span data-ttu-id="ae173-128">執行安裝程式之前，請先檢查安裝 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 所需的必要條件，並決定要用來提供伺服器的帳戶。</span><span class="sxs-lookup"><span data-stu-id="ae173-128">Before you run Setup, check prerequisites for installing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and determine which account you will use to provision the server.</span></span>|  
|<span data-ttu-id="ae173-129">[從安裝精靈安裝 SQL Server 2014 &#40;安裝程式&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="ae173-129">[Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).</span></span>|<span data-ttu-id="ae173-130">執行 SQL Server 安裝程式，安裝軟體。</span><span class="sxs-lookup"><span data-stu-id="ae173-130">Run SQL Server Setup to install the software.</span></span>|  
|[<span data-ttu-id="ae173-131">設定 Windows 防火牆以允許 Analysis Services 存取</span><span class="sxs-lookup"><span data-stu-id="ae173-131">Configure the Windows Firewall to Allow Analysis Services Access</span></span>](https://docs.microsoft.com/analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access)|<span data-ttu-id="ae173-132">安裝程式結束後，您必須設定防火牆設定，以允許遠端連接伺服器。</span><span class="sxs-lookup"><span data-stu-id="ae173-132">After Setup is finished, you must configure firewall settings to allow remote connections to the server.</span></span>|  
|[<span data-ttu-id="ae173-133">物件和作業的存取權授權 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ae173-133">Authorizing access to objects and operations &#40;Analysis Services&#41;</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services)|<span data-ttu-id="ae173-134">存取 Analysis Services 資料庫的使用者至少必須在伺服器上具有一個資料庫的「讀取」權限。</span><span class="sxs-lookup"><span data-stu-id="ae173-134">Users who access Analysis Services databases must have Read permission on at least one database on the server.</span></span>|  
  
## <a name="related-content"></a><span data-ttu-id="ae173-135">相關內容</span><span class="sxs-lookup"><span data-stu-id="ae173-135">Related Content</span></span>  
 <span data-ttu-id="ae173-136">您可以在下列主題中找到其他設定內容：</span><span class="sxs-lookup"><span data-stu-id="ae173-136">Additional setup content can be found in the following topics:</span></span>  
  
 [<span data-ttu-id="ae173-137">以表格模式安裝 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="ae173-137">Install Analysis Services in Tabular Mode</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services)  
  
 [<span data-ttu-id="ae173-138">PowerPivot for SharePoint 2010 安裝</span><span class="sxs-lookup"><span data-stu-id="ae173-138">PowerPivot for SharePoint 2010 Installation</span></span>](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
 [<span data-ttu-id="ae173-139">判斷 Analysis Services 執行個體的伺服器模式</span><span class="sxs-lookup"><span data-stu-id="ae173-139">Determine the Server Mode of an Analysis Services Instance</span></span>](https://docs.microsoft.com/analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance)  
  
 [<span data-ttu-id="ae173-140">SQL Server 資料採礦增益集</span><span class="sxs-lookup"><span data-stu-id="ae173-140">SQL Server Data Mining Add-ins</span></span>](https://www.microsoft.com/download/details.aspx?id=35578)  
  
 <span data-ttu-id="ae173-141">根據預設，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程序中不會安裝範例資料庫、範例程式碼和用戶端應用程式增益集。</span><span class="sxs-lookup"><span data-stu-id="ae173-141">By default, sample databases, sample code, and client application add-ins are not installed as part of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span> <span data-ttu-id="ae173-142">若要安裝範例資料庫和範例程式碼，請參閱 [CodePlex 網站](https://go.microsoft.com/fwlink/?LinkId=87843)。</span><span class="sxs-lookup"><span data-stu-id="ae173-142">To install sample databases and sample code, see the [CodePlex Web site](https://go.microsoft.com/fwlink/?LinkId=87843).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae173-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae173-143">See Also</span></span>  
 <span data-ttu-id="ae173-144">[SQL Server 2012 版本所支援的功能](https://go.microsoft.com/fwlink/?linkid=232473) </span><span class="sxs-lookup"><span data-stu-id="ae173-144">[Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) </span></span>  
 <span data-ttu-id="ae173-145">[語言和定序 &#40;Analysis Services&#41;](../../../2014/analysis-services/languages-and-collations-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="ae173-145">[Languages and Collations &#40;Analysis Services&#41;](../../../2014/analysis-services/languages-and-collations-analysis-services.md) </span></span>  
 [<span data-ttu-id="ae173-146">升級 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="ae173-146">Upgrade Analysis Services</span></span>](../../database-engine/install-windows/upgrade-analysis-services.md)  
  
  
