---
title: 設定和管理報表伺服器 (Reporting Services SharePoint 模式) |Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 846e86d0-fbbb-426c-97f9-f179cd42b390
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ce7c1f524eec4785ddbc25d95c641d070ecbf408
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707282"
---
# <a name="configuration-and-administration-of-a-report-server-reporting-services-sharepoint-mode"></a><span data-ttu-id="f169c-102">設定和管理報表伺服器 (Reporting Services SharePoint 模式)</span><span class="sxs-lookup"><span data-stu-id="f169c-102">Configuration and Administration of a Report Server (Reporting Services SharePoint Mode)</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="f169c-103">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 是以伺服器為基礎的報告平臺，可提供各種現成可用的工具和服務，協助您建立、部署和管理組織的報告，以及可讓您擴充和自訂報表功能的程式設計功能。</span><span class="sxs-lookup"><span data-stu-id="f169c-103">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] is a server-based reporting platform that provides a full range of ready-to-use tools and services to help you create, deploy, and manage reports for your organization, as well as programming features that enable you to extend and customize your reporting functionality.</span></span> <span data-ttu-id="f169c-104">您可以將報表環境與 SharePoint 產品整合，以體驗使用 SharePoint 網站所提供之共同作業環境的優點。</span><span class="sxs-lookup"><span data-stu-id="f169c-104">You can integrate your reporting environment with a SharePoint product to experience the benefits of using the collaborative environment provided by SharePoint sites.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f169c-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="f169c-105">In this section</span></span>  
 <span data-ttu-id="f169c-106">使用下列章節可幫助您更佳了解概念、部署案例、程序等等，讓您將 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 環境與 SharePoint 產品或技術整合：</span><span class="sxs-lookup"><span data-stu-id="f169c-106">Use the following sections to help you understand concepts, deployment scenarios, procedures, and more for integrating your [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] environment with a SharePoint product or technology:</span></span>  
  
-   <span data-ttu-id="f169c-107">SharePoint 文件庫中的功能表選項</span><span class="sxs-lookup"><span data-stu-id="f169c-107">Menu options in a SharePoint document library</span></span>  
  
    -   [<span data-ttu-id="f169c-108">SharePoint 使用者的資料警示管理員</span><span class="sxs-lookup"><span data-stu-id="f169c-108">Data Alert Manager for SharePoint Users</span></span>](../../2014/reporting-services/data-alert-manager-for-sharepoint-users.md)  
  
    -   [<span data-ttu-id="f169c-109">建立及管理 SharePoint 模式報表伺服器的訂閱</span><span class="sxs-lookup"><span data-stu-id="f169c-109">Create and Manage Subscriptions for SharePoint Mode Report Servers</span></span>](subscriptions/create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md)  
  
    -   [<span data-ttu-id="f169c-110">從 SharePoint 網站更新報表資料來源的認證</span><span class="sxs-lookup"><span data-stu-id="f169c-110">Update Credentials in Report Data Sources from a SharePoint Site</span></span>](report-data/update-credentials-in-report-data-sources-from-a-sharepoint-site.md)  
  
    -   [<span data-ttu-id="f169c-111">管理共用資料集</span><span class="sxs-lookup"><span data-stu-id="f169c-111">Manage Shared Datasets</span></span>](report-data/manage-shared-datasets.md)  
  
    -   [<span data-ttu-id="f169c-112">在已發行的報表上設定參數 &#40;SharePoint 整合模式中的 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f169c-112">Set Parameters on a Published Report &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md)  
  
    -   [<span data-ttu-id="f169c-113">設定處理選項 &#40;SharePoint 整合模式的 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f169c-113">Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../../2014/reporting-services/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
    -   [<span data-ttu-id="f169c-114">快取重新整理選項 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="f169c-114">Cache Refresh Options &#40;Report Manager&#41;</span></span>](../../2014/reporting-services/cache-refresh-options-report-manager.md)  
  
-   [<span data-ttu-id="f169c-115">Reporting Services 網站集合功能</span><span class="sxs-lookup"><span data-stu-id="f169c-115">Reporting Services Site Collection Features</span></span>](../../2014/reporting-services/reporting-services-site-collection-features.md)  
  
-   [<span data-ttu-id="f169c-116">在 SharePoint 中啟用報表伺服器和 Power View 整合功能</span><span class="sxs-lookup"><span data-stu-id="f169c-116">Activate the Report Server and Power View Integration Features in SharePoint</span></span>](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)  
  
-   [<span data-ttu-id="f169c-117">Reporting Services 網站設定和網站功能 &#40;SharePoint 模式&#41;</span><span class="sxs-lookup"><span data-stu-id="f169c-117">Reporting Services Site Settings and Site Features&#40;SharePoint Mode&#41;</span></span>](../../2014/reporting-services/reporting-services-site-settings-and-site-features-sharepoint-mode.md)  
  
-   [<span data-ttu-id="f169c-118">在 SharePoint 管理中心啟動報表伺服器檔案同步處理功能</span><span class="sxs-lookup"><span data-stu-id="f169c-118">Activate the Report Server File Sync Feature in SharePoint Central Administration</span></span>](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)  
  
-   [<span data-ttu-id="f169c-119">將報表伺服器內容類型加入至 SharePoint 整合模式下的程式庫 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f169c-119">Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)  
  
-   [<span data-ttu-id="f169c-120">比較報表檢視器中的本機模式與連接模式報表 &#40;SharePoint 模式的 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f169c-120">Local Mode vs. Connected Mode Reports in the Report Viewer &#40;Reporting Services in SharePoint Mode&#41;</span></span>](../../2014/reporting-services/local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md)  
  
-   [<span data-ttu-id="f169c-121">將文件上傳到 SharePoint 文件庫 &#40;SharePoint 模式的 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f169c-121">Upload Documents to a SharePoint Library &#40;Reporting Services in SharePoint Mode&#41;</span></span>](../../2014/reporting-services/upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)  
  
-   [<span data-ttu-id="f169c-122">設定處理選項 &#40;SharePoint 整合模式的 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f169c-122">Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../../2014/reporting-services/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
 <span data-ttu-id="f169c-123">如需有關 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 的更多一般資訊，請參閱《[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 線上叢書》中的 [Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="f169c-123">For more general information about [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], see [Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="f169c-124">如需有關其他 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 元件、工具和資源的詳細資訊，請參閱《 [SQL Server 線上叢書](../index.yml)》。</span><span class="sxs-lookup"><span data-stu-id="f169c-124">For information about other [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] components, tools, and resources, see [SQL Server Books Online](../index.yml).</span></span>  
  
  
