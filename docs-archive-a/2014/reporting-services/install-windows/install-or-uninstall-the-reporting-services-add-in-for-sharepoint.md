---
title: 安裝或卸載適用于 SharePoint (SharePoint 2010 和 SharePoint 2013) 的 Reporting Services 增益集 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2804a9a-08ea-4f4a-805d-a2c19c68733d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e30014ec823e89172b36f35d7f313568432a26f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597639"
---
# <a name="install-or-uninstall-the-reporting-services-add-in-for-sharepoint-sharepoint-2010-and-sharepoint-2013"></a><span data-ttu-id="052bd-102">安裝或解除安裝 SharePoint 的 Reporting Services 增益集 (SharePoint 2010 和 SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="052bd-102">Install or Uninstall the Reporting Services Add-in for SharePoint (SharePoint 2010 and SharePoint 2013)</span></span>
  <span data-ttu-id="052bd-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 在 sharepoint 伺服器上執行適用于 sharepoint 產品的安裝封裝增益集 ( # A0) ，以在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sharepoint 部署中啟用功能。</span><span class="sxs-lookup"><span data-stu-id="052bd-103">Run the installation package [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for SharePoint products (rsSharePoint.msi) on SharePoint servers to enable [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features within a SharePoint deployment.</span></span> <span data-ttu-id="052bd-104">功能包含 Power View、報表檢視器 Web 組件、URL Proxy 端點、內容類型以及應用程式頁面，讓您可以建立、檢視及管理報表、報表模型、資料來源以及在 SharePoint 網站上的其他報表伺服器內容。</span><span class="sxs-lookup"><span data-stu-id="052bd-104">Features include Power View, a Report Viewer Web Part, a URL proxy endpoint, content types, and application pages so that you can create, view, and manage reports, report models, data sources and other report server content on a SharePoint site.</span></span> <span data-ttu-id="052bd-105">適用於 SharePoint 產品的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集是以 SharePoint 模式執行之報表伺服器的必要元件。</span><span class="sxs-lookup"><span data-stu-id="052bd-105">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for SharePoint products is a required component for a report server that runs in SharePoint mode.</span></span> <span data-ttu-id="052bd-106">增益集可以從 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安裝精靈安裝，或是從 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 功能套件下載 rsSharePoint.msi。</span><span class="sxs-lookup"><span data-stu-id="052bd-106">The add-in can be installed from either the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] setup wizard or by downloading the rsSharePoint.msi from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] feature pack.</span></span> <span data-ttu-id="052bd-107">如需增益集版本和下載頁面的清單，請參閱 [尋找適用於 SharePoint 產品之 Reporting Services 增益集的位置](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)。</span><span class="sxs-lookup"><span data-stu-id="052bd-107">For a list of the versions of the add-in and download pages, see [Where to find the Reporting Services add-in for SharePoint Products](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).</span></span>

||
|-|
|<span data-ttu-id="052bd-108">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="052bd-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010</span></span>|

 <span data-ttu-id="052bd-109">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="052bd-109">**In this topic:**</span></span>

-   [<span data-ttu-id="052bd-110">先決條件</span><span class="sxs-lookup"><span data-stu-id="052bd-110">Prerequisites</span></span>](#bkmk_prereq)

-   [<span data-ttu-id="052bd-111">增益集的安裝內容</span><span class="sxs-lookup"><span data-stu-id="052bd-111">What Does The Add-in Install?</span></span>](#bkmk_whatinstalled)

-   [<span data-ttu-id="052bd-112">安裝方法的總覽</span><span class="sxs-lookup"><span data-stu-id="052bd-112">Overview of the Installation Methods</span></span>](#bkmk_3ways_to_install)

-   [<span data-ttu-id="052bd-113">使用安裝檔案安裝增益集 rsSharePoint.msi</span><span class="sxs-lookup"><span data-stu-id="052bd-113">Install the add-in using the installation file rsSharePoint.msi</span></span>](#bkmk_install_rssharepoint)

    -   [<span data-ttu-id="052bd-114">僅限檔案安裝</span><span class="sxs-lookup"><span data-stu-id="052bd-114">Files-only installation</span></span>](#bkmk_files_only_installation)

-   [<span data-ttu-id="052bd-115">如何移除 Reporting Services 增益集</span><span class="sxs-lookup"><span data-stu-id="052bd-115">How to Remove the Reporting Services Add-in</span></span>](#bkmk_remove_addin)

-   [<span data-ttu-id="052bd-116">如何從命令列修復 rsSharePoint.msi</span><span class="sxs-lookup"><span data-stu-id="052bd-116">How to Repair rssharepoint.msi from the Command Line</span></span>](#bkmk_repair)

-   [<span data-ttu-id="052bd-117">設定記錄檔</span><span class="sxs-lookup"><span data-stu-id="052bd-117">Setup Log Files</span></span>](#bkmk_logfiles)

-   [<span data-ttu-id="052bd-118">升級</span><span class="sxs-lookup"><span data-stu-id="052bd-118">Upgrade</span></span>](#bkmk_upgrade)

-   [<span data-ttu-id="052bd-119">rsCustomAction.exe</span><span class="sxs-lookup"><span data-stu-id="052bd-119">RsCustomAction.exe</span></span>](#bkmk_rscustomaction)

##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> <span data-ttu-id="052bd-120">必要條件</span><span class="sxs-lookup"><span data-stu-id="052bd-120">Prerequisites</span></span>
 <span data-ttu-id="052bd-121">安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集是整合報表伺服器與 SharePoint 產品之執行個體的數個必要步驟之一。</span><span class="sxs-lookup"><span data-stu-id="052bd-121">Installing the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in is one of several steps that are necessary for integrating a report server with an instance of a SharePoint product.</span></span> <span data-ttu-id="052bd-122">如需有關使用 SharePoint 模式之完整需求集的詳細資訊，請參閱＜ [Hardware and Software Requirements for Reporting Services in SharePoint Mode](../../../2014/sql-server/install/hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode.md)＞。</span><span class="sxs-lookup"><span data-stu-id="052bd-122">For more information about the complete set of requirements for using SharePoint mode, see [Hardware and Software Requirements for Reporting Services in SharePoint Mode](../../../2014/sql-server/install/hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode.md).</span></span> <span data-ttu-id="052bd-123">如需有關安裝和設定的詳細資訊 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，請參閱[安裝 sharepoint 2013 Reporting Services sharepoint 模式](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)。</span><span class="sxs-lookup"><span data-stu-id="052bd-123">For more information on installing and configuring [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Install Reporting Services SharePoint Mode for SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).</span></span>

-   <span data-ttu-id="052bd-124">若要整合 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 與具備多重 Web 前端應用程式的 SharePoint 伺服器陣列，請在具有 Web 伺服器前端的伺服器陣列中之每部電腦上安裝增益集。</span><span class="sxs-lookup"><span data-stu-id="052bd-124">If you are integrating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] with a SharePoint farm that has multiple Web front end applications, install the add-in to each computer in the farm that has a Web server front-end.</span></span> <span data-ttu-id="052bd-125">請只針對將用來存取報表伺服器內容的 Web 前端進行這項處理。</span><span class="sxs-lookup"><span data-stu-id="052bd-125">Do this only for Web front ends that will be used to access report server content.</span></span>

-   <span data-ttu-id="052bd-126">若要安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集，您必須是電腦上的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="052bd-126">To install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in, you must be an administrator on the computer.</span></span> <span data-ttu-id="052bd-127">例如，如果您要在命令提示字元中執行 rsSharePoint.msi，則應使用 **[以系統管理員身分執行]** 選項以系統管理員權限開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="052bd-127">For example if you are going to run the rsSharePoint.msi at the command prompt, you should open the command prompt with administrator privileges by using the **Run as administrator** option.</span></span>

-   <span data-ttu-id="052bd-128">您必須是 SharePoint Farm Administrators 群組成員才能安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集。</span><span class="sxs-lookup"><span data-stu-id="052bd-128">To install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in, you must be a member of the SharePoint Farm Administrators group.</span></span>

-   <span data-ttu-id="052bd-129">您必須是網站集合管理員，才能啟動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 整合功能。</span><span class="sxs-lookup"><span data-stu-id="052bd-129">You must be a Site Collection administrator to activate the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] integration feature.</span></span>

-   <span data-ttu-id="052bd-130">如需使用增益集部署範例的圖表，請參閱[SharePoint 中 SQL SERVER BI 功能的部署拓撲](../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="052bd-130">For diagrams of example deployments with the add-in, see [Deployment Topologies for SQL Server BI Features in SharePoint](../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).</span></span>

##  <a name="what-does-the-add-in-install"></a><a name="bkmk_whatinstalled"></a><span data-ttu-id="052bd-131">增益集的安裝內容為何？</span><span class="sxs-lookup"><span data-stu-id="052bd-131">What Does The Add-in Install?</span></span>
 <span data-ttu-id="052bd-132">增益集的安裝程序是由兩個階段組成，這兩個階段都會在完成標準安裝時自動完成：</span><span class="sxs-lookup"><span data-stu-id="052bd-132">The add-in setup process is composed of two phases, both are completed automatically when you complete a standard installation:</span></span>

-   <span data-ttu-id="052bd-133">第一階段是安裝檔案至適當的資料夾。</span><span class="sxs-lookup"><span data-stu-id="052bd-133">The first phase is to install files to the proper folders.</span></span> <span data-ttu-id="052bd-134">該資料夾是 SharePoint 部署的標準。</span><span class="sxs-lookup"><span data-stu-id="052bd-134">The folders are standard for SharePoint deployments.</span></span> <span data-ttu-id="052bd-135">rsCustomAction.exe 是所安裝的檔案之一。</span><span class="sxs-lookup"><span data-stu-id="052bd-135">One of the files that is installed is rsCustomAction.exe.</span></span>

-   <span data-ttu-id="052bd-136">安裝的第二部分是執行自訂動作集，利用 SharePoint 註冊 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 檔案。</span><span class="sxs-lookup"><span data-stu-id="052bd-136">The second portion of the installation is to run a set of custom actions to register the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] files with SharePoint.</span></span> <span data-ttu-id="052bd-137">從 rsCustomAction.exe 執行自訂動作。</span><span class="sxs-lookup"><span data-stu-id="052bd-137">The custom actions are run from rsCustomAction.exe.</span></span> <span data-ttu-id="052bd-138">當完整的兩階段安裝作業完成時，系統就會移除該 exe 檔。</span><span class="sxs-lookup"><span data-stu-id="052bd-138">The exe is removed when the full two phase installation completes.</span></span> <span data-ttu-id="052bd-139">您可以執行 **僅限檔案** 的安裝，在安裝結束時不執行 rsCustomAction.exe，並將其留在磁碟機中。</span><span class="sxs-lookup"><span data-stu-id="052bd-139">You can run a **files only** installation and rsCustomAction.exe is not run at the end of installation and it is left on the drive.</span></span>

## <a name="the-reporting-services-installation-order"></a><span data-ttu-id="052bd-140">Reporting Services 安裝順序</span><span class="sxs-lookup"><span data-stu-id="052bd-140">The Reporting Services Installation order</span></span>
 <span data-ttu-id="052bd-141">此增益集可以在安裝 SharePoint 之前或 SharePoint 安裝之後進行安裝。</span><span class="sxs-lookup"><span data-stu-id="052bd-141">The add-in can be installed before installing SharePoint or after SharePoint installation.</span></span> <span data-ttu-id="052bd-142">此增益集會遵循 SharePoint 預先部署標準，將檔案安裝在 SharePoint 安裝使用的位置中。</span><span class="sxs-lookup"><span data-stu-id="052bd-142">The add-in follows SharePoint pre-deployment standards and installs files in locations used by the SharePoint installation.</span></span>

> [!NOTE]
>  <span data-ttu-id="052bd-143">在 SharePoint 產品之前安裝此增益集的好處是，當新的伺服器加入到伺服器陣列時，SharePoint 伺服器陣列將會設定和啟動 Reporting Services 增益集。</span><span class="sxs-lookup"><span data-stu-id="052bd-143">The advantage of installing the add-in prior to the SharePoint product is that as new servers are added to the farm, the Reporting Services Add-in will be configured and activated by the SharePoint farm.</span></span>

 <span data-ttu-id="052bd-144">**SharePoint 2010**</span><span class="sxs-lookup"><span data-stu-id="052bd-144">**SharePoint 2010**</span></span>

-   <span data-ttu-id="052bd-145">SharePoint 2010 產品準備工具會安裝 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 版本的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集。</span><span class="sxs-lookup"><span data-stu-id="052bd-145">The SharePoint 2010 Products Preparation tool installs the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] version of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="052bd-146">包含 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 功能需要使用的新版本增益集。</span><span class="sxs-lookup"><span data-stu-id="052bd-146">includes a new version of the add-in that is required for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] features.</span></span>

     <span data-ttu-id="052bd-147">如果您執行 SharePoint 產品準備工具，您仍然需要安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 增益集的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="052bd-147">If you run the SharePoint Products Preparation Tool, you still need to install the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.</span></span>

-   <span data-ttu-id="052bd-148">如果您先行安裝了 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 增益集的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 版本，則當您執行 SharePoint 產品準備工具時，會看到以下的對話方塊，表示在偵測到較新版時，準備工具並未安裝舊版增益集。</span><span class="sxs-lookup"><span data-stu-id="052bd-148">If you install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in first, then when you run the SharePoint Products preparation tool you will see the following dialog indicating the preparation tool did not install the older version of the add-in as the newer version was detected.</span></span> <span data-ttu-id="052bd-149">這是預期的行為</span><span class="sxs-lookup"><span data-stu-id="052bd-149">This is expected behavior</span></span>

     <span data-ttu-id="052bd-150">![已安裝 SSRS 增益集。](../../../2014/sql-server/install/media/rs-sharepointprereq-complete.gif "已安裝 SSRS 增益集。")</span><span class="sxs-lookup"><span data-stu-id="052bd-150">![SSRS add-in is already installed.](../../../2014/sql-server/install/media/rs-sharepointprereq-complete.gif "SSRS add-in is already installed.")</span></span>

 <span data-ttu-id="052bd-151">**SharePoint 2013**</span><span class="sxs-lookup"><span data-stu-id="052bd-151">**SharePoint 2013**</span></span>

 <span data-ttu-id="052bd-152">SharePoint 20103 產品準備**工具不會安裝** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 適用于 sharepoint 產品的增益集。</span><span class="sxs-lookup"><span data-stu-id="052bd-152">The SharePoint 20103 Products Preparation tool does **Not** install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products.</span></span>

##  <a name="overview-of-the-installation-methods"></a><a name="bkmk_3ways_to_install"></a> <span data-ttu-id="052bd-153">安裝方法概觀</span><span class="sxs-lookup"><span data-stu-id="052bd-153">Overview of the Installation Methods</span></span>
 <span data-ttu-id="052bd-154">您 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 可以使用下列兩種方法的其中一種來安裝適用于 SharePoint 產品的增益集：</span><span class="sxs-lookup"><span data-stu-id="052bd-154">The [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for SharePoint products can be installed using one of the following two methods:</span></span>

-   <span data-ttu-id="052bd-155">**安裝精靈：** ![注意](../../../2014/reporting-services/media/rs-fyinote.png "注意")新的使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，安裝精靈可以安裝增益集 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="052bd-155">**The installation wizard:** ![note](../../../2014/reporting-services/media/rs-fyinote.png "note")New with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the add-in can be installed by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation wizard.</span></span> <span data-ttu-id="052bd-156">在精靈的 [功能選擇]\*\*\*\* 頁面上，選擇 [適用於 SharePoint 產品的 Reporting Services 增益集]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="052bd-156">Choose **Reporting Services Add-in for SharePoint Products** on the **Feature Selection** page of the wizard.</span></span>

-   <span data-ttu-id="052bd-157">**rsSharepoint.msi** ：該增益集可以直接從安裝媒體安裝，或下載後安裝。</span><span class="sxs-lookup"><span data-stu-id="052bd-157">**rsSharepoint.msi:** The add-in can be installed directly from the installation media or downloaded and installed.</span></span> <span data-ttu-id="052bd-158">rsSharepoint.msi 同時支援圖形化使用者介面和命令列安裝。</span><span class="sxs-lookup"><span data-stu-id="052bd-158">The rsSharepoint.msi supports both a graphical user interface and a command line installation.</span></span> <span data-ttu-id="052bd-159">您必須以系統管理員權限執行 .msi，方式是先開啟提高權限的命令提示字元，然後從命令列執行 rsSharepoint.msi。</span><span class="sxs-lookup"><span data-stu-id="052bd-159">You must run the .msi with administrator privileges by first opening a command prompt with elevated permissions, and then running the rsSharepoint.msi from the command line.</span></span> <span data-ttu-id="052bd-160">如需下載此增益集的詳細資訊，請參閱 [尋找適用於 SharePoint 產品之 Reporting Services 增益集的位置](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)。</span><span class="sxs-lookup"><span data-stu-id="052bd-160">For more information on downloading the add-in, see [Where to find the Reporting Services add-in for SharePoint Products](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).</span></span>

    > [!NOTE]
    >  <span data-ttu-id="052bd-161">如果您使用 **/q** 參數進行無訊息命令列安裝，將不會顯示使用者授權合約。</span><span class="sxs-lookup"><span data-stu-id="052bd-161">If you use the **/q** switch for a silent command line installation, the end-user license agreement will not be displayed.</span></span> <span data-ttu-id="052bd-162">不論安裝方式為何，使用此軟體皆受到授權合約的限制，同時您有責任遵從授權合約的規定。</span><span class="sxs-lookup"><span data-stu-id="052bd-162">Regardless of the installation method, the use of this software is governed by a license agreement and you are responsible for complying with the license agreement.</span></span>

##  <a name="install-the-add-in-using-the-installation-file-rssharepointmsi"></a><a name="bkmk_install_rssharepoint"></a> <span data-ttu-id="052bd-163">使用安裝檔 rsSharePoint.msi 安裝增益集</span><span class="sxs-lookup"><span data-stu-id="052bd-163">Install the add-in using the installation file rsSharePoint.msi</span></span>
 <span data-ttu-id="052bd-164">此章節與直接安裝 rssharepoint.msi 相關，可以執行 .msi 安裝精靈或命令列安裝。</span><span class="sxs-lookup"><span data-stu-id="052bd-164">This section is related to installing the rssharepoint.msi directly, by either running the .msi installation wizard or a command line installation.</span></span> <span data-ttu-id="052bd-165">如果您使用 SQL Server 安裝精靈安裝增益集，則不需遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="052bd-165">If you installed the add-in using the SQL Server installation Wizard, you do not need to follow these steps.</span></span>

 <span data-ttu-id="052bd-166">您可以執行下列命令以看到完整的命令列參數清單：</span><span class="sxs-lookup"><span data-stu-id="052bd-166">You can see a full list of command line switches by running the following command:</span></span>

```
Rssharepoint.msi /?
```

1.  <span data-ttu-id="052bd-167">下載安裝程式 (`rsSharepoint.msi` 增益集的) [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="052bd-167">Download the Setup program (`rsSharepoint.msi`) for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.</span></span> <span data-ttu-id="052bd-168">如需下載此增益集的詳細資訊，請參閱 [尋找適用於 SharePoint 產品之 Reporting Services 增益集的位置](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)。</span><span class="sxs-lookup"><span data-stu-id="052bd-168">For more information on downloading the add-in, see [Where to find the Reporting Services add-in for SharePoint Products](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).</span></span>

2.  <span data-ttu-id="052bd-169">以管理員的身分執行 `rsSharepoint.msi`，執行安裝精靈。</span><span class="sxs-lookup"><span data-stu-id="052bd-169">As an administrator, run `rsSharepoint.msi` to run the Installation Wizard.</span></span> <span data-ttu-id="052bd-170">此精靈會顯示 [歡迎使用] 頁面、軟體授權合約和註冊資訊頁面。</span><span class="sxs-lookup"><span data-stu-id="052bd-170">The wizard displays a Welcome page, the Software license terms, and a registration information page.</span></span> <span data-ttu-id="052bd-171">安裝程式會在下列路徑下建立資料夾，並將檔案複製到資料夾：</span><span class="sxs-lookup"><span data-stu-id="052bd-171">Setup creates folders under the following path and copies files to the folders:</span></span>

     `%program files%\common files\Microsoft Shared\Web Server Extensions\14\`

     <span data-ttu-id="052bd-172">或</span><span class="sxs-lookup"><span data-stu-id="052bd-172">or</span></span>

     `%program files%\common files\Microsoft Shared\Web Server Extensions\15\`

3.  <span data-ttu-id="052bd-173">在 SharePoint 管理中心設定報表伺服器設定與功能啟用。</span><span class="sxs-lookup"><span data-stu-id="052bd-173">Configure the report server settings and feature activation in SharePoint Central Administration.</span></span> <span data-ttu-id="052bd-174">.</span><span class="sxs-lookup"><span data-stu-id="052bd-174">.</span></span> <span data-ttu-id="052bd-175">如需安裝和設定 sharepoint 模式的詳細資訊 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，請參閱[安裝 sharepoint 2010 Reporting Services sharepoint 模式](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)。</span><span class="sxs-lookup"><span data-stu-id="052bd-175">For more information on installing and configuring [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode, see [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).</span></span>

###  <a name="files-only-installation"></a><a name="bkmk_files_only_installation"></a><span data-ttu-id="052bd-176">僅限檔案安裝</span><span class="sxs-lookup"><span data-stu-id="052bd-176">Files-only installation</span></span>
 <span data-ttu-id="052bd-177">若要安裝檔案但略過自訂動作階段，請從命令列執行 rssharepoint.msi 並加上 SKIPCA 選項：</span><span class="sxs-lookup"><span data-stu-id="052bd-177">To install the files but skip the custom action phase of installation, run the rssharepoint.msi from the command line with the SKIPCA option:</span></span>

1.  <span data-ttu-id="052bd-178">**以系統管理員許可權**開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="052bd-178">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="052bd-179">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="052bd-179">Run the following command:</span></span>

    ```cmd
    Msiexec.exe /i rsSharePoint.msi SKIPCA=1
    ```

 <span data-ttu-id="052bd-180">將會開啟安裝使用者介面並正常運作，同時會安裝 `rsCustomAction.exe` 檔案。</span><span class="sxs-lookup"><span data-stu-id="052bd-180">The installation user interface will open and run as normal and the `rsCustomAction.exe` file is installed.</span></span> <span data-ttu-id="052bd-181">但 .exe 不會在安裝結束時執行，而且當安裝完成時，`rsCustomAction.exe` 會保留在電腦中。</span><span class="sxs-lookup"><span data-stu-id="052bd-181">However, the .exe will not run at the end of the installation and `rsCustomAction.exe` will remain on the computer when the installation is completed.</span></span>

### <a name="use-a-two-step-installation-to-troubleshoot-installation-issues-or-install-the-content-types"></a><span data-ttu-id="052bd-182">使用兩步驟安裝來疑難排解安裝問題，或安裝內容類型。</span><span class="sxs-lookup"><span data-stu-id="052bd-182">Use a two-step installation to troubleshoot installation issues or install the content types</span></span>
 <span data-ttu-id="052bd-183">若您在安裝期間發生錯誤，或 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 內容類型沒有顯示在文件庫設定中，您可以從命令列將安裝程式以兩步驟的流程執行：</span><span class="sxs-lookup"><span data-stu-id="052bd-183">If you get errors during installation or the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] content types do not appear in the document library settings, you can run Setup as a two-step process from the command line:</span></span>

1.  <span data-ttu-id="052bd-184">**以系統管理員權限** 開啟命令提示字元，並依前一章節所述內容，執行僅限檔案安裝。</span><span class="sxs-lookup"><span data-stu-id="052bd-184">Open a command prompt **with administrator permissions** and run a files only installation as described in the previous section.</span></span>

2.  <span data-ttu-id="052bd-185">執行自訂動作可執行檔：</span><span class="sxs-lookup"><span data-stu-id="052bd-185">Run the custom actions executable:</span></span>

    1.  <span data-ttu-id="052bd-186">導覽至包含 `rsCustomAction.exe` 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="052bd-186">Navigate to the folder that contains the file `rsCustomAction.exe`.</span></span> <span data-ttu-id="052bd-187">此檔案會隨僅限檔案安裝增益集複製到您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="052bd-187">This file is copied to your computer by the files only installation of the add-in.</span></span> <span data-ttu-id="052bd-188">`rsCustomAction.exe`位於 **% Temp%** 目錄中。</span><span class="sxs-lookup"><span data-stu-id="052bd-188">`rsCustomAction.exe` is located in the **%Temp%** directory.</span></span> <span data-ttu-id="052bd-189">若要導覽至檔案，請在命令提示字元中輸入下列內容：</span><span class="sxs-lookup"><span data-stu-id="052bd-189">To navigate to the file, type the following from the command prompt:</span></span>

         <span data-ttu-id="052bd-190">**CD %temp%**。</span><span class="sxs-lookup"><span data-stu-id="052bd-190">**CD %temp%**.</span></span>

         <span data-ttu-id="052bd-191">此檔案應該位於：**\Users\\<您的名稱\>\AppData\Local\Temp**</span><span class="sxs-lookup"><span data-stu-id="052bd-191">The file should be located in: **\Users\\<your name\>\AppData\Local\Temp**</span></span>

    2.  <span data-ttu-id="052bd-192">鍵入下列命令。</span><span class="sxs-lookup"><span data-stu-id="052bd-192">Type the following command.</span></span> <span data-ttu-id="052bd-193">完成此組態步驟將需要幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="052bd-193">This configuration step will take several minutes to finish.</span></span> <span data-ttu-id="052bd-194">在此程序期間，將會重新啟動 W3SVC 服務。</span><span class="sxs-lookup"><span data-stu-id="052bd-194">The W3SVC service will be restarted during this process.</span></span> <span data-ttu-id="052bd-195">會以程式複製檔案、暫存器元件等形式顯示數個狀態訊息，同時會執行 SharePoint 產品設定精靈。</span><span class="sxs-lookup"><span data-stu-id="052bd-195">Several Status messages will be displayed as the program copies files, registers components, and runs the SharePoint Product Configuration Wizard.</span></span>

        ```cmd
        rsCustomAction.exe /i
        ```

    3.  <span data-ttu-id="052bd-196">根據您的伺服器環境而定，變更生效所需的時間可能會有所不同。</span><span class="sxs-lookup"><span data-stu-id="052bd-196">The amount of time it takes for the changes to take effect may vary, depending on your server environment.</span></span> <span data-ttu-id="052bd-197">您也可以執行 **iisreset** 強制執行更快的更新。</span><span class="sxs-lookup"><span data-stu-id="052bd-197">You can also run **iisreset** to force a quicker update.</span></span>

### <a name="quiet-installation-for-scripting"></a><span data-ttu-id="052bd-198">指令碼的無訊息安裝</span><span class="sxs-lookup"><span data-stu-id="052bd-198">Quiet installation for scripting</span></span>
 <span data-ttu-id="052bd-199">您可以使用 **/q**或 **/quiet**參數，進行不會顯示任何對話方塊或警告的「無訊息」安裝。</span><span class="sxs-lookup"><span data-stu-id="052bd-199">You can use the **/q** or **/quiet** switches for a "quiet" installation that will not display any dialogs or warnings.</span></span> <span data-ttu-id="052bd-200">如果您想要將增益集的安裝撰寫為指令碼，無訊息安裝相當實用。</span><span class="sxs-lookup"><span data-stu-id="052bd-200">The quiet installation is useful if you want to script the installation of the add-in.</span></span>

> [!NOTE]
>  <span data-ttu-id="052bd-201">如果您使用 **/q** 參數進行無訊息命令列安裝，將不會顯示使用者授權合約。</span><span class="sxs-lookup"><span data-stu-id="052bd-201">If you use the **/q** switch for a silent command line installation, the end-user license agreement will not be displayed.</span></span> <span data-ttu-id="052bd-202">不論安裝方式為何，使用此軟體皆受到授權合約的限制，同時您有責任遵從授權合約的規定。</span><span class="sxs-lookup"><span data-stu-id="052bd-202">Regardless of the installation method, the use of this software is governed by a license agreement and you are responsible for complying with the license agreement.</span></span>

 <span data-ttu-id="052bd-203">若要執行無訊息安裝：</span><span class="sxs-lookup"><span data-stu-id="052bd-203">To perform a quiet installation:</span></span>

1.  <span data-ttu-id="052bd-204">**以系統管理員許可權**開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="052bd-204">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="052bd-205">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="052bd-205">Run the following command:</span></span>

    ```cmd
    Msiexec.exe /i rsSharePoint.msi /q
    ```

##  <a name="how-to-remove-the-reporting-services-add-in"></a><a name="bkmk_remove_addin"></a><span data-ttu-id="052bd-206">如何移除 Reporting Services 增益集</span><span class="sxs-lookup"><span data-stu-id="052bd-206">How to Remove the Reporting Services Add-in</span></span>
 <span data-ttu-id="052bd-207">您可以從 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows [控制台] 或命令列，解除安裝適用於 SharePoint 產品的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 增益集。</span><span class="sxs-lookup"><span data-stu-id="052bd-207">You can uninstall the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for SharePoint Products from [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows control panel or the command line.</span></span>

1.  <span data-ttu-id="052bd-208">使用 [控制台] 將會完整解除安裝目前電腦上的檔案， **並且** 從 SharePoint 伺服器陣列中移除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 物件和功能。</span><span class="sxs-lookup"><span data-stu-id="052bd-208">Using control panel will run a complete uninstall of the files on the current computer **AND** it will remove the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] object and features from the SharePoint farm.</span></span> <span data-ttu-id="052bd-209">移除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 物件和功能時，您就無法再檢閱和更新報表。</span><span class="sxs-lookup"><span data-stu-id="052bd-209">When the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] object and features are removed you can no longer review and update reports.</span></span>

2.  <span data-ttu-id="052bd-210">解除安裝增益集的命令列方法可讓您使用 LocalOnly 參數僅移除本機電腦上的增益集檔案，而伺服器陣列中的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 物件和功能不會變更。</span><span class="sxs-lookup"><span data-stu-id="052bd-210">The command line method to uninstall the add-in allows you to use the LocalOnly parameter to only remove the add-in files from the local computer and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] object and features in the farm will not be changed.</span></span>

 <span data-ttu-id="052bd-211">解除安裝增益集將會移除在報表伺服器上用以處理報表的伺服器整合功能。</span><span class="sxs-lookup"><span data-stu-id="052bd-211">Uninstalling the add-in will remove server integration features that are used to process reports on a report server.</span></span> <span data-ttu-id="052bd-212">同時也會從 SharePoint 管理中心及其他自訂的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 頁面，移除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 頁面。</span><span class="sxs-lookup"><span data-stu-id="052bd-212">It will also remove the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pages from SharePoint Central Administration and other custom [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pages.</span></span> <span data-ttu-id="052bd-213">您可能也會想要移除受影響的 SharePoint 網站上所有不再使用的報表和其他報表伺服器項目。</span><span class="sxs-lookup"><span data-stu-id="052bd-213">You may also want to remove any reports and other report server items that you no longer use on the affected SharePoint sites.</span></span> <span data-ttu-id="052bd-214">移除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集之後，即無法再執行這些項目。</span><span class="sxs-lookup"><span data-stu-id="052bd-214">They will not run after the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in is removed.</span></span>

 <span data-ttu-id="052bd-215">若要解除安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集，您必須有仍在執行中的 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] 或 [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] 安裝。</span><span class="sxs-lookup"><span data-stu-id="052bd-215">To uninstall the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in, you must have a [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] or [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installation still running.</span></span> <span data-ttu-id="052bd-216">如果您先解除安裝 SharePoint 2010，您必須將它重新安裝，才能解除安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集。</span><span class="sxs-lookup"><span data-stu-id="052bd-216">If you uninstall the SharePoint 2010 first, you must reinstall it to uninstall the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.</span></span>

 <span data-ttu-id="052bd-217">解除安裝此增益集的步驟，對於獨立的伺服器和伺服器陣列而言，都是一樣的。</span><span class="sxs-lookup"><span data-stu-id="052bd-217">The steps for uninstalling the add-in are the same for both stand-alone servers and server farms.</span></span> <span data-ttu-id="052bd-218">安裝程式會移除程式檔案以及在安裝期間所加入的任何組態設定。</span><span class="sxs-lookup"><span data-stu-id="052bd-218">Setup will remove program files and any configuration settings that were added during installation.</span></span>

 <span data-ttu-id="052bd-219">解除安裝增益集不會移除下列項目：</span><span class="sxs-lookup"><span data-stu-id="052bd-219">Uninstalling the add-in will not remove the following:</span></span>

-   <span data-ttu-id="052bd-220">針對用來存取 SharePoint 組態和內容資料庫的報表伺服器服務帳戶所建立的登入。</span><span class="sxs-lookup"><span data-stu-id="052bd-220">Logins created for the Report Server service account that is used to access the SharePoint configuration and content databases.</span></span> <span data-ttu-id="052bd-221">您必須從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 用來主控 SharePoint 資料庫的實例，刪除報表伺服器服務帳戶的任何登入。</span><span class="sxs-lookup"><span data-stu-id="052bd-221">You must delete any logins for the Report Server service account from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance used to host the SharePoint databases.</span></span>

-   <span data-ttu-id="052bd-222">為報表使用者所建立的權限或群組。</span><span class="sxs-lookup"><span data-stu-id="052bd-222">Permissions or groups that you created for report users.</span></span> <span data-ttu-id="052bd-223">如果您已建立自訂的權限等級或 SharePoint 群組來授與對報表伺服器功能的存取權，就應該撤銷所有不再需要的權限。</span><span class="sxs-lookup"><span data-stu-id="052bd-223">If you created custom permission levels or SharePoint groups to grant access to report server features, you should revoke any permissions that are no longer required.</span></span>

-   <span data-ttu-id="052bd-224">上傳到 SharePoint 文件庫的資料檔案，包括報表定義 (.rdl)、共用資料來源 (.rsds) 及發行的報表項目 (.rsc) 檔案。</span><span class="sxs-lookup"><span data-stu-id="052bd-224">Data files that you uploaded to a SharePoint library, including report definition (.rdl), shared data source (.rsds), and published report items (.rsc) files.</span></span> <span data-ttu-id="052bd-225">這些檔案並沒有刪除，但無法再執行。</span><span class="sxs-lookup"><span data-stu-id="052bd-225">They are not deleted, but they will no longer run.</span></span> <span data-ttu-id="052bd-226">您必須手動刪除這些檔案。</span><span class="sxs-lookup"><span data-stu-id="052bd-226">You must delete the files manually.</span></span>

-   <span data-ttu-id="052bd-227">安裝程式不會刪除報表伺服器資料庫或修改用於整合作業的報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="052bd-227">Setup will not delete the report server database or modify the report server instance that was used for integrated operations.</span></span>

### <a name="to-uninstall-from-windows-control-panel"></a><span data-ttu-id="052bd-228">若要從 Windows 控制台解除安裝</span><span class="sxs-lookup"><span data-stu-id="052bd-228">To Uninstall from Windows Control Panel</span></span>
 <span data-ttu-id="052bd-229">若要從 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows [控制台] 啟動精靈並移除增益集：</span><span class="sxs-lookup"><span data-stu-id="052bd-229">To start the wizard from [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Control Panel and remove the add-in:</span></span>

1.  <span data-ttu-id="052bd-230">在 [控制台] 中的 **[程式]**，選取 **[解除安裝程式]**。</span><span class="sxs-lookup"><span data-stu-id="052bd-230">In Control Panel, in **Programs**, select **Uninstall a Program**</span></span>

2.  <span data-ttu-id="052bd-231">選取 [適用於 SharePoint 的 Microsoft SQL Server RS 增益集]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="052bd-231">Select **Microsoft SQL Server RS Add-in for SharePoint**.</span></span> <span data-ttu-id="052bd-232">您也可以從命令提示字元中執行 **rssharepoint.msi** (不使用任何參數)，藉以啟動解除安裝精靈。</span><span class="sxs-lookup"><span data-stu-id="052bd-232">You can also start the uninstall wizard by running **rssharepoint.msi** from the command prompt with no switches.</span></span>

3.  <span data-ttu-id="052bd-233">按一下 **[移除]** 。</span><span class="sxs-lookup"><span data-stu-id="052bd-233">Click **Remove**.</span></span>

### <a name="uninstall-from-the-command-line"></a><span data-ttu-id="052bd-234">從命令列解除安裝</span><span class="sxs-lookup"><span data-stu-id="052bd-234">Uninstall from the command line</span></span>
 <span data-ttu-id="052bd-235">若要從命令列解除安裝增益集：</span><span class="sxs-lookup"><span data-stu-id="052bd-235">To uninstall the add-in from the command line:</span></span>

1.  <span data-ttu-id="052bd-236">**以系統管理員許可權**開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="052bd-236">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="052bd-237">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="052bd-237">Run the following command:</span></span>

    ```cmd
    msiexec.exe /uninstall rsSharePoint.msi
    ```

3.  <span data-ttu-id="052bd-238">您會看到確認訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="052bd-238">You will see a confirmation message box.</span></span> <span data-ttu-id="052bd-239">按一下 [是] 。</span><span class="sxs-lookup"><span data-stu-id="052bd-239">Click **Yes**.</span></span>

### <a name="uninstall-the-add-in-from-the-local-server-only"></a><span data-ttu-id="052bd-240">只從本機伺服器解除安裝增益集</span><span class="sxs-lookup"><span data-stu-id="052bd-240">Uninstall the add-in from the local server only</span></span>
 <span data-ttu-id="052bd-241">上述解除安裝增益集的方法會從伺服器陣列中移除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能和物件。</span><span class="sxs-lookup"><span data-stu-id="052bd-241">The previous methods of uninstalling the add-in will remove the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features and object from the farm.</span></span> <span data-ttu-id="052bd-242">如果您擁有多伺服器的伺服器陣列，而只想要解除安裝本機電腦上的增益集，並且讓 SharePoint 伺服器陣列保持運作狀態，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="052bd-242">If you have a multi-server farm and want to uninstall the add-in from only the local computer and leave the SharePoint farm in a functional state, complete the following steps:</span></span>

1.  <span data-ttu-id="052bd-243">**以系統管理員許可權**開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="052bd-243">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="052bd-244">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="052bd-244">Run the following command:</span></span>

    ```cmd
    Msiexec.exe /uninstall rsSharePoint.msi LocalOnly=1
    ```

 <span data-ttu-id="052bd-245">此作業會從 SharePoint 取消 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 元件的註冊並會移除檔案，但只作用於本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="052bd-245">This will unregister the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components from SharePoint and remove the files, but for the local computer only.</span></span>

 <span data-ttu-id="052bd-246">如果您想要從 SharePoint 取消 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能的註冊，但將檔案留在磁碟上以供稍後使用，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="052bd-246">If you want to unregister the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features from SharePoint but leave the files on the disk for use later, complete the following steps:</span></span>

1.  <span data-ttu-id="052bd-247">**以系統管理員許可權**開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="052bd-247">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="052bd-248">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="052bd-248">Run the following command:</span></span>

    ```cmd
    rsCustomAction.exe /p
    ```

 <span data-ttu-id="052bd-249">上述步驟假設您已安裝 .msi 且 SkipCA=1，同時可以使用 rscusstomaction.exe。</span><span class="sxs-lookup"><span data-stu-id="052bd-249">The above steps assume you completed an installation of the .msi with SkipCA=1 and the rscusstomaction.exe is available.</span></span> <span data-ttu-id="052bd-250">如需詳細資訊，請參閱説明僅限檔案安裝一節。</span><span class="sxs-lookup"><span data-stu-id="052bd-250">For more information, see the section describing the files only installation.</span></span>

##  <a name="how-to-repair-rssharepointmsi-from-the-command-line"></a><a name="bkmk_repair"></a><span data-ttu-id="052bd-251">如何從命令列修復 rssharepoint.msi</span><span class="sxs-lookup"><span data-stu-id="052bd-251">How to Repair rssharepoint.msi from the Command Line</span></span>
 <span data-ttu-id="052bd-252">若要使用命令列修復或解除安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集，請完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="052bd-252">To repair or uninstall the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in using the command line, complete the following steps:</span></span>

1.  <span data-ttu-id="052bd-253">**以系統管理員許可權**開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="052bd-253">Open a command prompt **with administrator permissions**.</span></span>

2.  <span data-ttu-id="052bd-254">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="052bd-254">Run the following command:</span></span>

    ```cmd
    msiexec.exe /f rssharepoint.msi
    ```

##  <a name="setup-log-files"></a><a name="bkmk_logfiles"></a><span data-ttu-id="052bd-255">安裝程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="052bd-255">Setup Log Files</span></span>
 <span data-ttu-id="052bd-256">執行安裝程式時，會為已安裝 **增益集的使用者，將資訊記錄到** %temp% [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 資料夾中的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="052bd-256">When Setup runs, it logs information to a log file in the **%temp%** folder for the user who installed the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.</span></span> <span data-ttu-id="052bd-257">例如， **c:\Users \\<username \> \AppData\Local\Temp** 。檔案名為**RS_SP_ \<number> .log**，例如**RS_SP_0 .log**。</span><span class="sxs-lookup"><span data-stu-id="052bd-257">For example **c:\Users\\<username\>\AppData\Local\Temp** .The file name is **RS_SP_\<number>.log**, for example **RS_SP_0.log**.</span></span> <span data-ttu-id="052bd-258">該記錄檔中的每項錯誤，都會以 "SSRSCustomActionError" 字串開頭。</span><span class="sxs-lookup"><span data-stu-id="052bd-258">Each error in the log starts with the string "SSRSCustomActionError".</span></span>

> [!NOTE]
>  <span data-ttu-id="052bd-259">AppData 在 Windows 作業系統中是隱藏的資料夾。</span><span class="sxs-lookup"><span data-stu-id="052bd-259">AppData is a hidden folder in the Windows operating system.</span></span> <span data-ttu-id="052bd-260">您需要修改 Windows 檔案總管資料夾的設定，才可看到隱藏的檔案與資料夾。</span><span class="sxs-lookup"><span data-stu-id="052bd-260">You may need to modify your Windows Explorer folder settings so you can see hidden files and folders.</span></span>

#### <a name="view-a-log-file-with-windows-notepad"></a><span data-ttu-id="052bd-261">利用 Windows 記事本檢視記錄檔</span><span class="sxs-lookup"><span data-stu-id="052bd-261">View a log file with Windows Notepad</span></span>

1.  <span data-ttu-id="052bd-262">下列命令會變更命令提示字元路徑，列出 rs 記錄檔後利用 Windows 記事本開啟其中一個檔案：</span><span class="sxs-lookup"><span data-stu-id="052bd-262">The following commands will change the command prompt path, list the rs log files and then open one of the files with Windows Notepad:</span></span>

    ```cmd
    cd %temp%
    ```

    ```cmd
    dir rs_sp*.log
    ```

    ```cmd
    notepad rs_sp_3.log
    ```

#### <a name="view-a-log-file-with-powershell"></a><span data-ttu-id="052bd-263">利用 PowerShell 檢視記錄檔</span><span class="sxs-lookup"><span data-stu-id="052bd-263">View a Log file with PowerShell</span></span>

1.  <span data-ttu-id="052bd-264">從 SharePoint 管理命令介面輸入下列命令，從包含 "ssrscustomactionerror" 的檔案傳回已篩選過的資料列清單：</span><span class="sxs-lookup"><span data-stu-id="052bd-264">Type the following command from the SharePoint Management Shell to return a filtered list of rows from the file, that contain "ssrscustomactionerror":</span></span>

    ```powershell
    Get-Content -Path C:\Users\<UserName\AppData\Local\Temp\rs_sp_0.log | Select-String "ssrscustomactionerror"
    ```

2.  <span data-ttu-id="052bd-265">這些輸出看起來類似於下列文字：</span><span class="sxs-lookup"><span data-stu-id="052bd-265">The output will look similar to the following:</span></span>

     <span data-ttu-id="052bd-266">`2011-05-23 12:40:12: SSRSCustomActionError: SharePoint is installed, but not configured`.</span><span class="sxs-lookup"><span data-stu-id="052bd-266">`2011-05-23 12:40:12: SSRSCustomActionError: SharePoint is installed, but not configured`.</span></span>

##  <a name="upgrade"></a><a name="bkmk_upgrade"></a><span data-ttu-id="052bd-267">更新</span><span class="sxs-lookup"><span data-stu-id="052bd-267">Upgrade</span></span>
 <span data-ttu-id="052bd-268">如果您已擁有 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集的現有安裝，則可以升級至目前版本。</span><span class="sxs-lookup"><span data-stu-id="052bd-268">If you have an existing installation of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in, you can upgrade to the current version.</span></span> <span data-ttu-id="052bd-269">增益集的安裝程式會偵測現有的版本，並提示您確認升級作業。</span><span class="sxs-lookup"><span data-stu-id="052bd-269">The add-in setup will detect the existing version and prompt you to confirm the update.</span></span> <span data-ttu-id="052bd-270">這些訊息類似於下列文字：</span><span class="sxs-lookup"><span data-stu-id="052bd-270">The message will be similar to the following:</span></span>

 <span data-ttu-id="052bd-271">**在您的系統上偵測到較低版本的此產品。您要升級現有的安裝嗎？**</span><span class="sxs-lookup"><span data-stu-id="052bd-271">**A Lower version of this product has been detected on your system. Would you like to upgrade your existing installation?**</span></span>

 <span data-ttu-id="052bd-272">如果確認，將會移除舊版增益集並安裝新版本。</span><span class="sxs-lookup"><span data-stu-id="052bd-272">If you confirm, the older version of the add-in will be removed and then the new version will be installed.</span></span>

 <span data-ttu-id="052bd-273">請注意， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集無法感知執行個體。</span><span class="sxs-lookup"><span data-stu-id="052bd-273">Note that the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in is not instance-aware.</span></span> <span data-ttu-id="052bd-274">在電腦上只能安裝一個增益集執行個體。</span><span class="sxs-lookup"><span data-stu-id="052bd-274">You can only have one instance of the add-in on a computer.</span></span> <span data-ttu-id="052bd-275">目前版本無法與相異版本並存。</span><span class="sxs-lookup"><span data-stu-id="052bd-275">You cannot run different versions side-by-side the current version.</span></span>

##  <a name="rscustomactionexe"></a><a name="bkmk_rscustomaction"></a><span data-ttu-id="052bd-276">RsCustomAction.exe</span><span class="sxs-lookup"><span data-stu-id="052bd-276">RsCustomAction.exe</span></span>
 <span data-ttu-id="052bd-277">下表摘要列出 rscustomaction.exe 參數：</span><span class="sxs-lookup"><span data-stu-id="052bd-277">The following table summarizes the rscustomaction.exe switches:</span></span>

|<span data-ttu-id="052bd-278">Switch</span><span class="sxs-lookup"><span data-stu-id="052bd-278">Switch</span></span>|<span data-ttu-id="052bd-279">描述</span><span class="sxs-lookup"><span data-stu-id="052bd-279">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="052bd-280">i</span><span class="sxs-lookup"><span data-stu-id="052bd-280">i</span></span>|<span data-ttu-id="052bd-281">安裝自訂動作。</span><span class="sxs-lookup"><span data-stu-id="052bd-281">Install the custom actions.</span></span> <span data-ttu-id="052bd-282">此作業會在 SharePoint 中註冊 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 元件。</span><span class="sxs-lookup"><span data-stu-id="052bd-282">This will register the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components in SharePoint.</span></span> <span data-ttu-id="052bd-283">此作業會重新啟動 W3SVCservice。</span><span class="sxs-lookup"><span data-stu-id="052bd-283">This will restart the W3SVCservice.</span></span>|
|<span data-ttu-id="052bd-284">r</span><span class="sxs-lookup"><span data-stu-id="052bd-284">r</span></span>|<span data-ttu-id="052bd-285">修復</span><span class="sxs-lookup"><span data-stu-id="052bd-285">Repair</span></span>|
|<span data-ttu-id="052bd-286">u</span><span class="sxs-lookup"><span data-stu-id="052bd-286">u</span></span>|<span data-ttu-id="052bd-287">解除安裝。</span><span class="sxs-lookup"><span data-stu-id="052bd-287">Uninstall.</span></span> <span data-ttu-id="052bd-288">此作業會從整個 SharePoint 伺服器陣列中取消 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 元件的註冊，但會將檔案留在磁碟中。</span><span class="sxs-lookup"><span data-stu-id="052bd-288">This will unregister the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components from the entire SharePoint farm but leave the files on disk.</span></span> <span data-ttu-id="052bd-289">此作業會重新啟動 W3SVCservice。</span><span class="sxs-lookup"><span data-stu-id="052bd-289">This will restart the W3SVCservice.</span></span>|
|<span data-ttu-id="052bd-290">p</span><span class="sxs-lookup"><span data-stu-id="052bd-290">p</span></span>|<span data-ttu-id="052bd-291">本機解除安裝。</span><span class="sxs-lookup"><span data-stu-id="052bd-291">Local uninstall.</span></span> <span data-ttu-id="052bd-292">此作業會從本機電腦取消 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 元件的註冊。</span><span class="sxs-lookup"><span data-stu-id="052bd-292">This will unregister the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components from only the local computer.</span></span> <span data-ttu-id="052bd-293">檔案將會留在磁碟上。</span><span class="sxs-lookup"><span data-stu-id="052bd-293">The files will remain on disk.</span></span> <span data-ttu-id="052bd-294">此作業會重新啟動 W3SVCservice。</span><span class="sxs-lookup"><span data-stu-id="052bd-294">This will restart the W3SVCservice.</span></span>|
|<span data-ttu-id="052bd-295">t</span><span class="sxs-lookup"><span data-stu-id="052bd-295">t</span></span>|<span data-ttu-id="052bd-296">僅限 SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 2005。</span><span class="sxs-lookup"><span data-stu-id="052bd-296">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 2005 only.</span></span> <span data-ttu-id="052bd-297">此切換作業會測試報表伺服器是否能與報表伺服器資料庫正常連接。</span><span class="sxs-lookup"><span data-stu-id="052bd-297">The switch tests if the report server has a working connection to the report server database.</span></span>|

## <a name="configuring-reporting-services"></a><span data-ttu-id="052bd-298">設定 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="052bd-298">Configuring Reporting Services</span></span>
 <span data-ttu-id="052bd-299">在所有需要的電腦上安裝該增益集之後，需要從 SharePoint 管理中心設定報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="052bd-299">After you have installed the add-in on all the necessary computers, you need to configure the report server from SharePoint Central Administration.</span></span> <span data-ttu-id="052bd-300">所需要的步驟取決於不同技術之安裝順序。</span><span class="sxs-lookup"><span data-stu-id="052bd-300">The steps that are needed depend on the order which the different technologies were installed.</span></span> <span data-ttu-id="052bd-301">如需詳細資訊，請參閱[安裝 sharepoint 2010 Reporting Services Sharepoint 模式](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)和[Reporting Services 報表伺服器 &#40;sharepoint 模式&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)</span><span class="sxs-lookup"><span data-stu-id="052bd-301">For more information, see [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) and [Reporting Services Report Server &#40;SharePoint Mode&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="052bd-302">另請參閱</span><span class="sxs-lookup"><span data-stu-id="052bd-302">See Also</span></span>
 <span data-ttu-id="052bd-303">[Reporting Services Sharepoint 模式安裝 sharepoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) [Reporting Services 報表伺服器 &#40;sharepoint 模式&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)</span><span class="sxs-lookup"><span data-stu-id="052bd-303">[Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) [Reporting Services Report Server &#40;SharePoint Mode&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)</span></span>
