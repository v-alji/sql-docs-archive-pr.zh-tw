---
title: 安裝或卸載 PowerPivot for SharePoint 增益集 (SharePoint 2013) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: fe13ce8b-9369-4126-928a-9426f9119424
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7df54d11021163167149e5b0c1edd960fee1a2ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688322"
---
# <a name="install-or-uninstall-the-powerpivot-for-sharepoint-add-in-sharepoint-2013"></a><span data-ttu-id="1f69f-102">安裝或解除安裝 PowerPivot for SharePoint 增益集 (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="1f69f-102">Install or Uninstall the PowerPivot for SharePoint Add-in (SharePoint 2013)</span></span>
  [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] <span data-ttu-id="1f69f-103">是應用程式伺服器元件及後端服務的集合，可以在 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 伺服器陣列中提供 [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] 資料存取功能。</span><span class="sxs-lookup"><span data-stu-id="1f69f-103">is a collection of application server components and back-end services that provide [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] data access in a [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] farm.</span></span> <span data-ttu-id="1f69f-104">[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 增益集 (**spPowerpivot.msi**) 是用來安裝應用程式伺服器元件的安裝程式封裝。</span><span class="sxs-lookup"><span data-stu-id="1f69f-104">The [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint add-in (**spPowerpivot.msi**) is an installer package used to install the application server components.</span></span>

-   <span data-ttu-id="1f69f-105">SharePoint 2010 部署不需要此增益集。</span><span class="sxs-lookup"><span data-stu-id="1f69f-105">The add-in is not required for SharePoint 2010 deployments.</span></span>

-   <span data-ttu-id="1f69f-106">包含 SharePoint 2013 和 SharePoint 模式之 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 的單一伺服器部署不需要此增益集。</span><span class="sxs-lookup"><span data-stu-id="1f69f-106">The add-in is not required on a single server deployment that includes SharePoint 2013 and [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="1f69f-107">當您以 SharePoint 模式安裝 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 伺服器時，就會包含此增益集所安裝的元件。</span><span class="sxs-lookup"><span data-stu-id="1f69f-107">The components installed by the add-in are included when you install an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode.</span></span> <span data-ttu-id="1f69f-108">如需使用增益集部署範例的圖表，請參閱[SharePoint 中 SQL SERVER BI 功能的部署拓撲](../../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="1f69f-108">For diagrams of example deployments with the add-in, see [Deployment Topologies for SQL Server BI Features in SharePoint](../../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).</span></span>

 <span data-ttu-id="1f69f-109">**注意** ：本主題將描述如何安裝 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 方案檔以及 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 組態工具。</span><span class="sxs-lookup"><span data-stu-id="1f69f-109">**Note:** This topic describes installing the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] solution files and [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 Configuration tool.</span></span> <span data-ttu-id="1f69f-110">安裝之後，請參閱下列主題，以取得設定工具和其他功能的相關資訊、[設定 PowerPivot 並將方案部署 &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013)。</span><span class="sxs-lookup"><span data-stu-id="1f69f-110">After the installation, see the following topic for information on the configuration tool and additional features, [Configure PowerPivot and Deploy Solutions &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013).</span></span>

 <span data-ttu-id="1f69f-111">如需有關如何下載 **spPowerPivot.msi**的詳細資訊，請參閱 [Microsoft® SQL Server® 2014 PowerPivot® for Microsoft SharePoint®](https://go.microsoft.com/fwlink/?LinkID=324854)。</span><span class="sxs-lookup"><span data-stu-id="1f69f-111">For information on how to download **spPowerPivot.msi**, see [Microsoft® SQL Server® 2014 PowerPivot® for Microsoft SharePoint®](https://go.microsoft.com/fwlink/?LinkID=324854).</span></span>

 <span data-ttu-id="1f69f-112">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="1f69f-112">**In this topic:**</span></span>

-   [<span data-ttu-id="1f69f-113">背景</span><span class="sxs-lookup"><span data-stu-id="1f69f-113">Background</span></span>](#bkmk_background)

-   [<span data-ttu-id="1f69f-114">安裝 spPowerPivot.msi 的位置？</span><span class="sxs-lookup"><span data-stu-id="1f69f-114">Where to Install spPowerPivot.msi?</span></span>](#bkmk_where_to_install)

-   [<span data-ttu-id="1f69f-115">需求和必要條件</span><span class="sxs-lookup"><span data-stu-id="1f69f-115">Requirements and Prerequisites</span></span>](#bkmk_prereq)

-   [<span data-ttu-id="1f69f-116">若要安裝 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="1f69f-116">To Install PowerPivot for SharePoint</span></span>](#bkmk_install)

-   [<span data-ttu-id="1f69f-117">使用 PowerPivot for SharePoint 2013 組態工具部署 SharePoint 方案檔</span><span class="sxs-lookup"><span data-stu-id="1f69f-117">Deploy the SharePoint Solution Files with the PowerPivot for SharePoint 2013 Configuration Tool</span></span>](#bkmk_deploy_solution)

-   [<span data-ttu-id="1f69f-118">解除安裝或修復增益集</span><span class="sxs-lookup"><span data-stu-id="1f69f-118">Uninstall or repair the add-in</span></span>](#bkmk_remove_addin)

##  <a name="background"></a><a name="bkmk_background"></a> <span data-ttu-id="1f69f-119">背景</span><span class="sxs-lookup"><span data-stu-id="1f69f-119">Background</span></span>

-   <span data-ttu-id="1f69f-120">**應用程式伺服器：** [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 功能包括使用活頁簿做為資料來源、排程的資料重新整理與 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 管理儀表板。</span><span class="sxs-lookup"><span data-stu-id="1f69f-120">**Application Server:** [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] functionality in SharePoint 2013 includes using workbooks as a data source, scheduled data refresh, and the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Management Dashboard.</span></span>

     [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] <span data-ttu-id="1f69f-121">是部署 Analysis Services 用戶端程式庫和複製 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 安裝檔案到電腦上的**Windows 安裝程式封裝 (** spPowerpivot.msi [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] )。</span><span class="sxs-lookup"><span data-stu-id="1f69f-121">is a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Installer package (**spPowerpivot.msi**) that deploys Analysis Services client libraries and copies [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] installation files to the computer.</span></span> <span data-ttu-id="1f69f-122">此安裝程式不會在 SharePoint 中部署或設定 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="1f69f-122">The installer does not deploy or configure [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] features in SharePoint.</span></span> <span data-ttu-id="1f69f-123">預設會安裝下列元件：</span><span class="sxs-lookup"><span data-stu-id="1f69f-123">The following components install by default:</span></span>

    -   [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] <span data-ttu-id="1f69f-124">2013.此元件包含 PowerShell 指令碼 (.ps1 檔案)、SharePoint 方案套件 (.wsp)，以及在 SharePoint 2013 伺服器陣列中部署 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 的 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 2013 組態工具。</span><span class="sxs-lookup"><span data-stu-id="1f69f-124">2013. This component includes PowerShell scripts (.ps1 files), SharePoint solution packages (.wsp), and the [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013 configuration tool to deploy [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] in a SharePoint 2013 farm.</span></span>

    -   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="1f69f-125">OLE DB Provider for Analysis Services (MSOLAP)。</span><span class="sxs-lookup"><span data-stu-id="1f69f-125">OLE DB Provider for Analysis Services (MSOLAP).</span></span>

    -   <span data-ttu-id="1f69f-126">ADOMD.NET 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="1f69f-126">ADOMD.NET data provider.</span></span>

    -   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="1f69f-127">分析管理物件。</span><span class="sxs-lookup"><span data-stu-id="1f69f-127">Analysis Management Objects.</span></span>

-   <span data-ttu-id="1f69f-128">**後端服務** ：如果您使用 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for Excel 建立包含分析資料的活頁簿，伺服器環境必須具有以執行 SharePoint 模式 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 之 BI 伺服器設定的 Excel Services，才可存取該資料。</span><span class="sxs-lookup"><span data-stu-id="1f69f-128">**Backend services:** If you use [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for Excel to create workbooks that contain analytical data, you must have Excel Services configured with a BI server running [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in SharePoint mode to access that data in a server environment.</span></span> <span data-ttu-id="1f69f-129">您可以在已安裝 SharePoint Server 2013 的電腦或在沒有 SharePoint 軟體的另一部電腦上執行 SQL Server 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="1f69f-129">You can run SQL Server Setup on a computer that has SharePoint Server 2013 installed, or on a different computer that has no SharePoint software.</span></span> <span data-ttu-id="1f69f-130">Analysis Services 沒有 SharePoint 的相依性。</span><span class="sxs-lookup"><span data-stu-id="1f69f-130">Analysis Services does not have any dependencies on SharePoint.</span></span>

     <span data-ttu-id="1f69f-131">如需有關安裝、解除安裝及設定後端服務的詳細資訊，請參閱以下主題：</span><span class="sxs-lookup"><span data-stu-id="1f69f-131">For more information on installing, uninstalling, and configuring the backend services, see the following:</span></span>

    -   [<span data-ttu-id="1f69f-132">PowerPivot for SharePoint 2013 安裝</span><span class="sxs-lookup"><span data-stu-id="1f69f-132">PowerPivot for SharePoint 2013 Installation</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)

    -   [<span data-ttu-id="1f69f-133">解除安裝 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="1f69f-133">Uninstall PowerPivot for SharePoint</span></span>](../../../sql-server/install/uninstall-power-pivot-for-sharepoint.md)

##  <a name="where-to-install-sppowerpivotmsi"></a><a name="bkmk_where_to_install"></a> <span data-ttu-id="1f69f-134">在何處安裝 spPowerPivot.msi？</span><span class="sxs-lookup"><span data-stu-id="1f69f-134">Where to Install spPowerPivot.msi?</span></span>
 <span data-ttu-id="1f69f-135">建議的最佳作法是在 SharePoint 伺服器陣列的所有伺服器上安裝 **spPowerPivot.msi** 以保持組態一致性，包括應用程式伺服器和 Web 前端伺服器。</span><span class="sxs-lookup"><span data-stu-id="1f69f-135">A recommended best practice is to install **spPowerPivot.msi** on all servers in the SharePoint farm for configuration consistency, including application servers and web-front end servers.</span></span> <span data-ttu-id="1f69f-136">安裝程式套件包含 Analysis Services 資料提供者以及 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 組態工具。</span><span class="sxs-lookup"><span data-stu-id="1f69f-136">The installer package includes the Analysis Services data providers as well as the [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] configuration tool.</span></span> <span data-ttu-id="1f69f-137">當您安裝 **spPowerPivot.msi** 時，可以排除個別元件來自訂安裝。</span><span class="sxs-lookup"><span data-stu-id="1f69f-137">When you install **spPowerPivot.msi** you can customize the installation by excluding individual components.</span></span>

 <span data-ttu-id="1f69f-138">**資料提供者：** 數項 SharePoint 和 SQL Server 技術使用 Analysis Services 資料提供者，包括 Excel Services、PerformancePoint Services 和 Power View。</span><span class="sxs-lookup"><span data-stu-id="1f69f-138">**Data providers:** Several SharePoint and SQL Server technologies use the Analysis Services data providers including Excel Services, PerformancePoint Services, and Power View.</span></span> <span data-ttu-id="1f69f-139">在所有 SharePoint 伺服器上安裝 **spPowerPivot.msi** ，可確保完整的 Analysis Services 資料提供者集和 PowerPivot 連接在整個伺服器陣列中是一致可用的。</span><span class="sxs-lookup"><span data-stu-id="1f69f-139">Installing **spPowerPivot.msi** on all SharePoint servers ensures the full set of Analysis Services data providers and PowerPivot connectivity is consistently available across the farm.</span></span>

> [!NOTE]
>  <span data-ttu-id="1f69f-140">您必須使用 **spPowerPivot.msi**，在 SharePoint 2013 伺服器上安裝 Analysis Services 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="1f69f-140">You must install the Analysis Services data providers on a SharePoint 2013 server using **spPowerPivot.msi**.</span></span> <span data-ttu-id="1f69f-141">不支援 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] 功能套件中的其他安裝程式套件，因為這些套件不包含資料提供者在此環境中需要的 SharePoint 2013 支援檔案。</span><span class="sxs-lookup"><span data-stu-id="1f69f-141">Other installer packages available in the [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Feature Pack are not supported because these packages do not include the SharePoint 2013 support files that the data providers require in this environment.</span></span>

 <span data-ttu-id="1f69f-142">**組態工具：** 只有其中一個 SharePoint 伺服器才需要 PowerPivot for SharePoint 2013 組態工具。</span><span class="sxs-lookup"><span data-stu-id="1f69f-142">**Configuration Tool:** The PowerPivot for SharePoint 2013 configuration tool is required on only one of the SharePoint servers.</span></span> <span data-ttu-id="1f69f-143">不過在多伺服器的伺服器陣列中，建議的最佳作法是在至少兩個伺服器上安裝組態工具，如此一來，即使其中一個伺服器已離線，您也可以存取組態工具。</span><span class="sxs-lookup"><span data-stu-id="1f69f-143">However a recommended best practice in multi-server farms is to install the configuration tool on at least two servers so you have access to the configuration tool if one of the two servers is offline.</span></span>

##  <a name="requirements-and-prerequisites"></a><a name="bkmk_prereq"></a><span data-ttu-id="1f69f-144">需求和必要條件</span><span class="sxs-lookup"><span data-stu-id="1f69f-144">Requirements and Prerequisites</span></span>

-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="1f69f-145">SharePoint Server 2013。</span><span class="sxs-lookup"><span data-stu-id="1f69f-145">SharePoint Server 2013.</span></span>

-   <span data-ttu-id="1f69f-146">**spPowerPivot.msi** 只有 64 位元版本，符合 SharePoint 產品和技術的需求。</span><span class="sxs-lookup"><span data-stu-id="1f69f-146">**spPowerPivot.msi** is 64-bit only, in accordance with the requirements of SharePoint products and technologies.</span></span>

-   <span data-ttu-id="1f69f-147">PowerPivot 模式的 [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="1f69f-147">A [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] server in PowerPivot mode.</span></span> <span data-ttu-id="1f69f-148">Excel Services 會使用 SQL Server Analysis Services 執行個體當做 PowerPivot 伺服器。</span><span class="sxs-lookup"><span data-stu-id="1f69f-148">Excel Services will use the SQL Server Analysis Services instance as a PowerPivot server.</span></span> <span data-ttu-id="1f69f-149">Analysis Services 可在本機或遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="1f69f-149">Analysis Services can run on the local or a remote computer.</span></span>

-   <span data-ttu-id="1f69f-150">**權限** ：若要安裝 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)]，目前使用者必須是電腦的系統管理員以及 SharePoint 伺服器陣列管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="1f69f-150">**Permissions:** To install [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)], the current user is required to be an administrator on the computer and a SharePoint Farm Administrators group.</span></span>

-   <span data-ttu-id="1f69f-151">如需 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 需求和必要條件的詳細資訊，請移至[SharePoint 模式下 Analysis Services Server 的硬體和軟體需求 &#40;SQL Server 2014&#41;](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="1f69f-151">For more information on [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] requirements and pre-requisites, go to [Hardware and Software Requirements for Analysis Services Server in SharePoint Mode &#40;SQL Server 2014&#41;](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md).</span></span>

##  <a name="to-install-powerpivot-for-sharepoint"></a><a name="bkmk_install"></a><span data-ttu-id="1f69f-152">若要安裝 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="1f69f-152">To Install PowerPivot for SharePoint</span></span>
 <span data-ttu-id="1f69f-153">**spPowerpivot.msi** 安裝程式封裝同時支援圖形化使用者介面和命令列模式。</span><span class="sxs-lookup"><span data-stu-id="1f69f-153">The **spPowerpivot.msi** installer package supports both a graphical user interface and a command-line mode.</span></span> <span data-ttu-id="1f69f-154">這兩個安裝方法都需要您使用系統管理員權限執行 .msi。</span><span class="sxs-lookup"><span data-stu-id="1f69f-154">Both methods of installation require that you run the .msi with administrator privileges.</span></span> <span data-ttu-id="1f69f-155">安裝之後，請參閱下列主題，以取得設定工具和其他功能的相關資訊、[設定 PowerPivot 並將方案部署 &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013)。</span><span class="sxs-lookup"><span data-stu-id="1f69f-155">After the installation, see the following topic for information on the configuration tool and additional features, [Configure PowerPivot and Deploy Solutions &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013).</span></span>

### <a name="user-interface-installation"></a><span data-ttu-id="1f69f-156">使用者介面安裝</span><span class="sxs-lookup"><span data-stu-id="1f69f-156">User interface installation</span></span>
 <span data-ttu-id="1f69f-157">若要以圖形化使用者介面安裝 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] ，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="1f69f-157">To install [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] with the graphical user interface, complete the following steps:</span></span>

1.  <span data-ttu-id="1f69f-158">執行 **SpPowerPivot.msi**。</span><span class="sxs-lookup"><span data-stu-id="1f69f-158">Run **SpPowerPivot.msi**.</span></span>

2.  <span data-ttu-id="1f69f-159">在歡迎頁面上按 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1f69f-159">Click **Next** on the Welcome page.</span></span>

3.  <span data-ttu-id="1f69f-160">檢閱並接受授權條款，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="1f69f-160">Review and accept the license agreement, then click **Next**.</span></span>

4.  <span data-ttu-id="1f69f-161">在 **[特徵選取]** 頁面上，已預設選取所有功能。</span><span class="sxs-lookup"><span data-stu-id="1f69f-161">On the **Feature Selection** page, all of the features are selected by default.</span></span>

5.  <span data-ttu-id="1f69f-162">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="1f69f-162">Click **Next**.</span></span>

6.  <span data-ttu-id="1f69f-163">按一下 **[安裝]** 完成安裝。</span><span class="sxs-lookup"><span data-stu-id="1f69f-163">Click **Install** to install to finish the installation.</span></span>

### <a name="command-line-installation"></a><span data-ttu-id="1f69f-164">命令列安裝</span><span class="sxs-lookup"><span data-stu-id="1f69f-164">Command Line Installation</span></span>
 <span data-ttu-id="1f69f-165">對於命令列安裝，請以系統管理權限開啟命令提示字元，然後執行 **spPowerPivot.msi**。</span><span class="sxs-lookup"><span data-stu-id="1f69f-165">For a command-line installation, open a command prompt with administrative permissions, and then run the **spPowerPivot.msi**.</span></span> <span data-ttu-id="1f69f-166">例如：</span><span class="sxs-lookup"><span data-stu-id="1f69f-166">For example:</span></span>

 <span data-ttu-id="1f69f-167">`Msiexec.exe /i SpPowerPivot.msi`.</span><span class="sxs-lookup"><span data-stu-id="1f69f-167">`Msiexec.exe /i SpPowerPivot.msi`.</span></span>

 <span data-ttu-id="1f69f-168">若要建立安裝記錄檔，請使用標準 MsiExec 記錄參數。</span><span class="sxs-lookup"><span data-stu-id="1f69f-168">To create an installation log, use the standard MsiExec logging switches.</span></span> <span data-ttu-id="1f69f-169">下列範例會使用 "v" 詳細資訊記錄參數來建立記錄檔 "Install_Log.txt"。</span><span class="sxs-lookup"><span data-stu-id="1f69f-169">The following example creates the log file "Install_Log.txt" using the "v" verbose logging switch.</span></span>

```cmd
Msiexec.exe /i SpPowerPivot.msi /L v c:\test\Install_Log.txt
```

### <a name="quiet-command-line-installation-for-scripting"></a><span data-ttu-id="1f69f-170">指令碼的無訊息命令列安裝</span><span class="sxs-lookup"><span data-stu-id="1f69f-170">Quiet Command Line Installation for scripting</span></span>
 <span data-ttu-id="1f69f-171">您可以使用 **/q**或 **/quiet**參數，進行不會顯示任何對話方塊或警告的「無訊息」安裝。</span><span class="sxs-lookup"><span data-stu-id="1f69f-171">You can use the **/q** or **/quiet** switches for a "quiet" installation that will not display any dialogs or warnings.</span></span> <span data-ttu-id="1f69f-172">如果您想要將增益集的安裝撰寫為指令碼，無訊息安裝相當實用。</span><span class="sxs-lookup"><span data-stu-id="1f69f-172">The quiet installation is useful if you want to script the installation of the add-in.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="1f69f-173">如果您使用 **/q** 參數進行無訊息命令列安裝，將不會顯示使用者授權合約。</span><span class="sxs-lookup"><span data-stu-id="1f69f-173">If you use the **/q** switch for a silent command line installation, the end-user license agreement will not be displayed.</span></span> <span data-ttu-id="1f69f-174">不論安裝方式為何，使用此軟體皆受到授權合約的限制，同時您有責任遵從授權合約的規定。</span><span class="sxs-lookup"><span data-stu-id="1f69f-174">Regardless of the installation method, the use of this software is governed by a license agreement and you are responsible for complying with the license agreement.</span></span>

#### <a name="to-perform-a-quiet-installation"></a><span data-ttu-id="1f69f-175">執行無訊息安裝</span><span class="sxs-lookup"><span data-stu-id="1f69f-175">To perform a quiet installation</span></span>

1.  <span data-ttu-id="1f69f-176">**以系統管理員許可權**開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="1f69f-176">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="1f69f-177">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="1f69f-177">Run the following command:</span></span>

    ```cmd
    Msiexec.exe /i spPowerPivot.msi /q
    ```

### <a name="command-line-installation-to-include-specific-components"></a><span data-ttu-id="1f69f-178">包含特定元件的命令列安裝</span><span class="sxs-lookup"><span data-stu-id="1f69f-178">Command Line Installation to include specific components</span></span>
 <span data-ttu-id="1f69f-179">並非每部 SharePoint 伺服器都需要 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 組態工具，不過建議至少在兩部伺服器上安裝組態工具，確保在需要時隨時可用。</span><span class="sxs-lookup"><span data-stu-id="1f69f-179">The [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] Configuration tool is not required on every SharePoint server, however it is recommended to install it on at least two servers so the configuration tool is available when you need it.</span></span>

 <span data-ttu-id="1f69f-180">當您安裝 spPowerPivot.msi 時，可以使用命令列選項來安裝特定項目，例如資料提供者，而不安裝 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 組態工具。</span><span class="sxs-lookup"><span data-stu-id="1f69f-180">When you install the spPowerPivot.msi, you can use the command line options to install specific items, such as the data providers and not the [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] Configuration tool.</span></span> <span data-ttu-id="1f69f-181">下列命令列示範如何安裝組態工具以外的所有元件：</span><span class="sxs-lookup"><span data-stu-id="1f69f-181">The following command line is an example of installing all components except the configuration tool:</span></span>

```
Msiexec /i spPowerPivot.msi AGREETOLICENSE="yes" ADDLOCAL=" SQL_OLAPDM,SQL_ADOMD,SQL_AMO,SQLAS_SP_Common"
```

|<span data-ttu-id="1f69f-182">選項</span><span class="sxs-lookup"><span data-stu-id="1f69f-182">Option</span></span>|<span data-ttu-id="1f69f-183">描述</span><span class="sxs-lookup"><span data-stu-id="1f69f-183">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="1f69f-184">Analysis_Server_SP_addin</span><span class="sxs-lookup"><span data-stu-id="1f69f-184">Analysis_Server_SP_addin</span></span>|<span data-ttu-id="1f69f-185">PowerPivot 組態</span><span class="sxs-lookup"><span data-stu-id="1f69f-185">PowerPivot Configuration</span></span>|
|<span data-ttu-id="1f69f-186">SQL_OLAPDM</span><span class="sxs-lookup"><span data-stu-id="1f69f-186">SQL_OLAPDM</span></span>|<span data-ttu-id="1f69f-187">MSOLAP</span><span class="sxs-lookup"><span data-stu-id="1f69f-187">MSOLAP</span></span>|
|<span data-ttu-id="1f69f-188">SQL_ADOMD</span><span class="sxs-lookup"><span data-stu-id="1f69f-188">SQL_ADOMD</span></span>|<span data-ttu-id="1f69f-189">ADOMD.net 提供者</span><span class="sxs-lookup"><span data-stu-id="1f69f-189">ADOMD.net provider</span></span>|
|<span data-ttu-id="1f69f-190">SQL_AMO</span><span class="sxs-lookup"><span data-stu-id="1f69f-190">SQL_AMO</span></span>|<span data-ttu-id="1f69f-191">AMO 提供者</span><span class="sxs-lookup"><span data-stu-id="1f69f-191">AMO provider</span></span>|
|<span data-ttu-id="1f69f-192">SQLAS_SP_Common</span><span class="sxs-lookup"><span data-stu-id="1f69f-192">SQLAS_SP_Common</span></span>|<span data-ttu-id="1f69f-193">適用於 SharePoint 2013 的 Analysis Services 一般元件</span><span class="sxs-lookup"><span data-stu-id="1f69f-193">Analysis Services common components for SharePoint 2013</span></span>|

##  <a name="deploy-the-sharepoint-solution-files-with-the-powerpivot-for-sharepoint-2013-configuration-tool"></a><a name="bkmk_deploy_solution"></a><span data-ttu-id="1f69f-194">使用 PowerPivot for SharePoint 2013 設定工具部署 SharePoint 方案檔</span><span class="sxs-lookup"><span data-stu-id="1f69f-194">Deploy the SharePoint Solution Files with the PowerPivot for SharePoint 2013 Configuration Tool</span></span>
 <span data-ttu-id="1f69f-195">spPowerPivot.msi 複製到硬碟的其中三個檔案是 SharePoint 方案檔。</span><span class="sxs-lookup"><span data-stu-id="1f69f-195">Three of the files copied to the hard drive by spPowerPivot.msi are SharePoint solution files.</span></span> <span data-ttu-id="1f69f-196">其中一個方案檔的範圍是 Web 應用程式層級，其他檔案的範圍則是伺服器陣列層級。</span><span class="sxs-lookup"><span data-stu-id="1f69f-196">The scope of one solution file is the Web application level while the scope of the other files is the farm level.</span></span> <span data-ttu-id="1f69f-197">檔案如下：</span><span class="sxs-lookup"><span data-stu-id="1f69f-197">The files are the following:</span></span>

-   `PowerPivotFarmSolution.wsp`

-   `PowerPivotFarm14Solution.wsp`

-   `PowerPivotWebApplicationSolution.wsp`

 <span data-ttu-id="1f69f-198">方案檔複製到下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="1f69f-198">The solution files are copied to the following folder:</span></span>

 `C:\Program Files\Microsoft SQL Server\120\Tools\PowerPivotTools\SPAddinConfiguration\Resources`

 <span data-ttu-id="1f69f-199">在 .msi 安裝之後，請執行 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 組態工具，在 SharePoint 伺服器陣列中設定並部署方案。</span><span class="sxs-lookup"><span data-stu-id="1f69f-199">Following the .msi installation, run the [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] Configuration Tool to configure and deploy the solutions in the SharePoint farm.</span></span>

### <a name="to-start-the-configuration-tool"></a><span data-ttu-id="1f69f-200">啟動設定工具</span><span class="sxs-lookup"><span data-stu-id="1f69f-200">To start the configuration tool</span></span> 

 <span data-ttu-id="1f69f-201">從 Windows [開始] 畫面輸入 "power"，然後在應用程式搜尋結果中，按一下 [ **PowerPivot for SharePoint 2013**設定]。</span><span class="sxs-lookup"><span data-stu-id="1f69f-201">From the Windows Start screen type "power" and in the Apps search results, click **PowerPivot for SharePoint 2013 Configuration**.</span></span> <span data-ttu-id="1f69f-202">請注意，搜尋結果可能包含兩個連結，因為 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝程式會分別為 SharePoint 2010 和 SharePoint 2013 安裝不同的 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 組態工具。</span><span class="sxs-lookup"><span data-stu-id="1f69f-202">Note that the search results may include two links because [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] setup installs separate [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] configuration tools for SharePoint 2010 and SharePoint 2013.</span></span> <span data-ttu-id="1f69f-203">務必確定啟動 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 組態工具。</span><span class="sxs-lookup"><span data-stu-id="1f69f-203">Make sure you start the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 Configuration tool.</span></span>

 <span data-ttu-id="1f69f-204">![兩個 powerpivot 設定工具](../../media/as-powerpivot-configtools-bothicons.gif "兩個 powerpivot 設定工具")</span><span class="sxs-lookup"><span data-stu-id="1f69f-204">![two powerpivot configuration tools](../../media/as-powerpivot-configtools-bothicons.gif "two powerpivot configuration tools")</span></span>

 <span data-ttu-id="1f69f-205">**或**</span><span class="sxs-lookup"><span data-stu-id="1f69f-205">**Or**</span></span>

1.  <span data-ttu-id="1f69f-206">移至 **[開始]**、 **[所有程式]**。</span><span class="sxs-lookup"><span data-stu-id="1f69f-206">Go to **Start**, **All Programs**.</span></span>

2.  <span data-ttu-id="1f69f-207">按一下 **[Microsoft SQL Server 2014]**。</span><span class="sxs-lookup"><span data-stu-id="1f69f-207">Click **Microsoft SQL Server 2014**.</span></span>

3.  <span data-ttu-id="1f69f-208">按一下 **[組態工具]**。</span><span class="sxs-lookup"><span data-stu-id="1f69f-208">Click **Configuration Tools**.</span></span>

4.  <span data-ttu-id="1f69f-209">按一下 **[PowerPivot for SharePoint 2013 組態]**。</span><span class="sxs-lookup"><span data-stu-id="1f69f-209">Click **PowerPivot for SharePoint 2013 Configuration**.</span></span>

 <span data-ttu-id="1f69f-210">如需有關組態工具的詳細資訊，請參閱＜ [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md)＞。</span><span class="sxs-lookup"><span data-stu-id="1f69f-210">For more information on the configuration tool, see [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md).</span></span>

##  <a name="uninstall-or-repair-the-add-in"></a><a name="bkmk_remove_addin"></a><span data-ttu-id="1f69f-211">卸載或修復增益集</span><span class="sxs-lookup"><span data-stu-id="1f69f-211">Uninstall or repair the add-in</span></span>

> [!CAUTION]
>  <span data-ttu-id="1f69f-212">如果您解除安裝 **spPowerPivot.msi** ，會解除安裝資料提供者和組態工具。</span><span class="sxs-lookup"><span data-stu-id="1f69f-212">If you uninstall **spPowerPivot.msi** the data providers and the configuration tool are uninstalled.</span></span> <span data-ttu-id="1f69f-213">解除安裝資料提供者會使伺服器無法連接到 PowerPivot。</span><span class="sxs-lookup"><span data-stu-id="1f69f-213">Uninstalling the data providers will cause the server to be unable to connect to PowerPivot.</span></span>

 <span data-ttu-id="1f69f-214">您可以使用下列其中一個方法來解除安裝或修復 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="1f69f-214">You can uninstall or repair [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] using one of the following methods:</span></span>

1.  <span data-ttu-id="1f69f-215">**Windows 控制台：** 選取 **[Microsoft SQL Server 2012 PowerPivot for SharePoint 2013]**。</span><span class="sxs-lookup"><span data-stu-id="1f69f-215">**Windows control panel:** Select **Microsoft SQL Server 2012 PowerPivot for SharePoint 2013**.</span></span> <span data-ttu-id="1f69f-216">按一下 **[解除安裝]** 或 **[修復]**。</span><span class="sxs-lookup"><span data-stu-id="1f69f-216">Click either **Uninstall** or **Repair**.</span></span>

2.  <span data-ttu-id="1f69f-217">執行 spPowerPivot.msi，然後選取 **[移除]** 選項或 **[修復]** 選項。</span><span class="sxs-lookup"><span data-stu-id="1f69f-217">Run the spPowerPivot.msi and select the **Remove** option or the **Repair** option.</span></span>

 <span data-ttu-id="1f69f-218">**命令列：** 若要使用命令列修復或解除安裝 PowerPivot for SharePoint 2013，請 **以管理員權限** 開啟命令提示字元，並執行下列其中一個命令：</span><span class="sxs-lookup"><span data-stu-id="1f69f-218">**Command Line:** To repair or uninstall PowerPivot for SharePoint 2013 using the command line, open a command prompt **with administrator permissions** and run one of the following commands:</span></span>

-   <span data-ttu-id="1f69f-219">若要修復，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="1f69f-219">To Repair, run the following command:</span></span>

    ```cmd
    msiexec.exe /f spPowerPivot.msi
    ```

 <span data-ttu-id="1f69f-220">或者</span><span class="sxs-lookup"><span data-stu-id="1f69f-220">OR</span></span>

-   <span data-ttu-id="1f69f-221">若要解除安裝，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="1f69f-221">To uninstall, run the following command:</span></span>

    ```cmd
    msiexec.exe /uninstall spPowerPivot.msi
    ```
