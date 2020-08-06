---
title: Sharepoint 2010 和 SharePoint 2013) Reporting Services SharePoint 模式安裝 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- default configuration [Reporting Services]
- installing Reporting Services, SharePoint integrated mode
- installation options [Reporting Services]
ms.assetid: ac6cba68-2665-4a39-8fa3-cb7d7e6723c0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c27b6f9fbeebcc896b1a6097cb51e8d2e15924bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585781"
---
# <a name="reporting-services-sharepoint-mode-installation-sharepoint-2010-and-sharepoint-2013"></a><span data-ttu-id="75d4f-102">Reporting Services SharePoint 模式安裝 (SharePoint 2010 和 SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="75d4f-102">Reporting Services SharePoint Mode Installation (SharePoint 2010 and SharePoint 2013)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="75d4f-103">在 SharePoint 模式中，是伺服器元件的集合，可根據 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 SharePoint 產品來提供產生和傳遞報表 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="75d4f-103">in SharePoint mode is a collection of server components that provide report generation and delivery, based on [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint products.</span></span>  
  
 <span data-ttu-id="75d4f-104">在 SharePoint 模式中執行 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]，可提供 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 與資料警示功能。</span><span class="sxs-lookup"><span data-stu-id="75d4f-104">Running [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode provides the [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] and data alerting features.</span></span> <span data-ttu-id="75d4f-105">如需有關 SharePoint 模式功能的詳細資訊，請參閱[Reporting Services 報表伺服器](../reporting-services-report-server.md)中的「伺服器模式的功能支援和行為差異」一節。</span><span class="sxs-lookup"><span data-stu-id="75d4f-105">For more information regarding features in SharePoint mode, see the section "Feature Support and Behavior Differences by Server Mode" in [Reporting Services Report Server](../reporting-services-report-server.md)</span></span>  
  
 <span data-ttu-id="75d4f-106">SharePoint 模式中的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 需要兩項基本安裝：</span><span class="sxs-lookup"><span data-stu-id="75d4f-106">There are two fundamental installations needed for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode:</span></span>  
  
|<span data-ttu-id="75d4f-107">安裝</span><span class="sxs-lookup"><span data-stu-id="75d4f-107">Installation</span></span>|<span data-ttu-id="75d4f-108">描述</span><span class="sxs-lookup"><span data-stu-id="75d4f-108">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="75d4f-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 適用于 SharePoint 產品的增益集。</span><span class="sxs-lookup"><span data-stu-id="75d4f-109">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products.</span></span>|<span data-ttu-id="75d4f-110">增益集會在 SharePoint 網站前端伺服器上，安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 使用者介面 (UI) 頁面與功能。</span><span class="sxs-lookup"><span data-stu-id="75d4f-110">The add-in installs the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] user interface (UI) pages and features on a SharePoint web front-end server.</span></span> <span data-ttu-id="75d4f-111">使用者介面包含 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]、SharePoint 管理中心內的管理頁面、SharePoint 文件庫中使用的功能頁面，以及 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 資料警示頁面。</span><span class="sxs-lookup"><span data-stu-id="75d4f-111">The UI features include [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], administration pages in SharePoint Central Administration, feature pages used within SharePoint document libraries, and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Data Alerting pages.</span></span>|  
|<span data-ttu-id="75d4f-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 以 SharePoint 模式安裝的報表伺服器</span><span class="sxs-lookup"><span data-stu-id="75d4f-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server installed in SharePoint Mode</span></span>|<span data-ttu-id="75d4f-113">報表伺服器處理資料與報表的處理程序、訂閱的呈現方式，以及資料警示處理程序。</span><span class="sxs-lookup"><span data-stu-id="75d4f-113">The report server handles the data and report processing and rendering as well subscription and Data Alert processing.</span></span> <span data-ttu-id="75d4f-114">SharePoint 模式報表伺服器會架構與安裝為 SharePoint 共用服務。</span><span class="sxs-lookup"><span data-stu-id="75d4f-114">The SharePoint mode report server is architected and installed as a SharePoint Shared Service.</span></span>|  
  
 <span data-ttu-id="75d4f-115">使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝媒體，安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="75d4f-115">To install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], use the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installation media.</span></span>  
  
 <span data-ttu-id="75d4f-116">如需有關先進部署案例的指示，請參閱[部署檢查清單： Reporting Services、Power View 和 PowerPivot for SharePoint](../../sql-server/install/deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md)和[部署檢查清單：將 Reporting Services 安裝到現有的 SharePoint 伺服器陣列](../../sql-server/install/deployment-checklist-install-reporting-services-existing-sharepoint-farm.md)。</span><span class="sxs-lookup"><span data-stu-id="75d4f-116">For instructions on advanced deployment scenarios, see [Deployment Checklist: Reporting Services, Power View, and PowerPivot for SharePoint](../../sql-server/install/deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md) and [Deployment Checklist: Install Reporting Services into an Existing SharePoint Farm](../../sql-server/install/deployment-checklist-install-reporting-services-existing-sharepoint-farm.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="75d4f-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="75d4f-117">In This Section</span></span>  
 [<span data-ttu-id="75d4f-118">支援的 SharePoint 和 Reporting Services 伺服器與增益集的組合 &#40;SQL Server 2014&#41;</span><span class="sxs-lookup"><span data-stu-id="75d4f-118">Supported Combinations of SharePoint and Reporting Services Server and Add-in &#40;SQL Server 2014&#41;</span></span>](supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
 [<span data-ttu-id="75d4f-119">安裝適用於 SharePoint 2013 的 Reporting Services SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="75d4f-119">Install Reporting Services SharePoint Mode for SharePoint 2013</span></span>](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)  
  
 [<span data-ttu-id="75d4f-120">安裝 SharePoint 2010 Reporting Services SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="75d4f-120">Install Reporting Services SharePoint Mode for SharePoint 2010</span></span>](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
 [<span data-ttu-id="75d4f-121">安裝或卸載適用于 SharePoint &#40;SharePoint 2010 和 SharePoint 2013 的 Reporting Services 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="75d4f-121">Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
 [<span data-ttu-id="75d4f-122">尋找適用於 SharePoint 產品之 Reporting Services 增益集的位置</span><span class="sxs-lookup"><span data-stu-id="75d4f-122">Where to find the Reporting Services add-in for SharePoint Products</span></span>](where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
 [<span data-ttu-id="75d4f-123">將其他報表伺服器加入至伺服器陣列 &#40;SSRS 向外延展&#41;</span><span class="sxs-lookup"><span data-stu-id="75d4f-123">Add an Additional Report Server to a Farm &#40;SSRS Scale-out&#41;</span></span>](add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
 [<span data-ttu-id="75d4f-124">將其他 Reporting Services Web 前端加入至伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="75d4f-124">Add an Additional Reporting Services Web Front-end to a Farm</span></span>](add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 [<span data-ttu-id="75d4f-125">設定 Reporting Services 服務應用程式的電子郵件 &#40;SharePoint 2010 和 SharePoint 2013&#41;</span><span class="sxs-lookup"><span data-stu-id="75d4f-125">Configure E-mail for a Reporting Services Service Application &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](configure-e-mail-for-a-reporting-services-service-application.md)  
  
 [<span data-ttu-id="75d4f-126">SSRS 服務應用程式的佈建訂閱及警示</span><span class="sxs-lookup"><span data-stu-id="75d4f-126">Provision Subscriptions and Alerts for SSRS Service Applications</span></span>](provision-subscriptions-and-alerts-for-ssrs-service-applications.md)  
  
 [<span data-ttu-id="75d4f-127">對 Windows Token 服務的宣告 &#40;C2WTS&#41; 和 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="75d4f-127">Claims to Windows Token Service &#40;C2WTS&#41; and Reporting Services</span></span>](../../sql-server/install/claims-to-windows-token-service-c2wts-and-reporting-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="75d4f-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75d4f-128">See Also</span></span>  
 <span data-ttu-id="75d4f-129">[資料警示架構和工作流程](../reporting-services-data-alerts.md#AlertingWF) </span><span class="sxs-lookup"><span data-stu-id="75d4f-129">[Data Alerts Architecture and Workflow](../reporting-services-data-alerts.md#AlertingWF) </span></span>  
 [<span data-ttu-id="75d4f-130">警示系統管理員的資料警示管理員</span><span class="sxs-lookup"><span data-stu-id="75d4f-130">Data Alert Manager for Alerting Administrators</span></span>](../data-alert-manager-for-alerting-administrators.md)  
  
  
