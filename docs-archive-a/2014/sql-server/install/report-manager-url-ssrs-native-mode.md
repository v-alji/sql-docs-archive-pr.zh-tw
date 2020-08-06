---
title: 報表管理員 URL (SSRS 原生模式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.rsconfigtool.reportmanagervirtualdirectory.f1
ms.assetid: 45768952-23a6-45a5-b541-e7bf192b4a78
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ec43c91bb2d24bb96cc6541d93311ce6dd234ed4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597560"
---
# <a name="report-manager-url-ssrs-native-mode"></a><span data-ttu-id="e8745-102">報表管理員 URL (SSRS 原生模式)</span><span class="sxs-lookup"><span data-stu-id="e8745-102">Report Manager URL (SSRS Native Mode)</span></span>
  <span data-ttu-id="e8745-103">使用 [報表管理員 URL] 頁面可設定或修改用於存取報表管理員的 URL。</span><span class="sxs-lookup"><span data-stu-id="e8745-103">Use the Report Manager URL page to configure or modify the URL used to access Report Manager.</span></span> <span data-ttu-id="e8745-104">根據預設，報表管理員 URL 會繼承報表伺服器 Web 服務 URL 的前置詞、IP 位址和通訊埠。</span><span class="sxs-lookup"><span data-stu-id="e8745-104">By default, the Report Manager URL inherits the prefix, IP address, and port of the Report Server Web service URL.</span></span> <span data-ttu-id="e8745-105">這是因為報表管理員會提供在相同報表伺服器服務內執行之 Web 服務的前端存取權。</span><span class="sxs-lookup"><span data-stu-id="e8745-105">This is because Report Manager provides front-end access to the Web service that runs within the same Report Server service.</span></span> <span data-ttu-id="e8745-106">如果您要隔離服務應用程式並使用報表管理員來存取不同電腦上的報表伺服器 Web 服務，您必須編輯 RSReportServer.config 檔案，讓報表管理員指向不同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e8745-106">If you are isolating the service applications and using Report Manager to access a Report Server Web service on a different computer, you must edit RSReportServer.config file to point Report Manager to a different instance.</span></span> <span data-ttu-id="e8745-107">如需設定報表管理員連接到遠端報表伺服器的詳細資訊，請參閱[Reporting Services 組態管理員 &#40;原生模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="e8745-107">For more information about configuring a Report Manager connection to a remote report server, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="e8745-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]原生模式。</span><span class="sxs-lookup"><span data-stu-id="e8745-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="e8745-109">如果您設定報表伺服器在 SharePoint 整合模式下執行，請不要建立報表管理員 URL。</span><span class="sxs-lookup"><span data-stu-id="e8745-109">If you are configuring the report server to run in SharePoint integrated mode, do not create a Report Manager URL.</span></span> <span data-ttu-id="e8745-110">以 SharePoint 整合模式執行的報表伺服器不支援報表管理員。</span><span class="sxs-lookup"><span data-stu-id="e8745-110">Report Manager is not supported on a report server that runs in SharePoint integrated mode.</span></span> <span data-ttu-id="e8745-111">如果報表管理員已經有 URL 存在，當您設定報表伺服器在 SharePoint 整合模式下執行之後，此 URL 將會變成無法使用。</span><span class="sxs-lookup"><span data-stu-id="e8745-111">If a URL already exists for Report Manager, it will become unavailable after you configure the report server to run in SharePoint integrated mode.</span></span>  
  
 <span data-ttu-id="e8745-112">若要開啟此頁面，請啟動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員，並按一下導覽窗格中的 **[報表管理員 URL]** 。</span><span class="sxs-lookup"><span data-stu-id="e8745-112">To open this page, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and click **Report Manager URL** in the navigation pane.</span></span> <span data-ttu-id="e8745-113">如需如何啟動 Configuration Manager 的詳細資訊，請參閱[Reporting Services 組態管理員 &#40;原生模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="e8745-113">For more information about how to start the Configuration Manager, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8745-114">如果報表管理員尚未啟用，您就無法設定此頁面上的選項。</span><span class="sxs-lookup"><span data-stu-id="e8745-114">If Report Manager is not enabled, you cannot set options on this page.</span></span> <span data-ttu-id="e8745-115">如需啟用報表管理員的詳細資訊，請參閱[Reporting Services 組態管理員 &#40;原生模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="e8745-115">For more information about enabling Report Manager, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e8745-116">選項</span><span class="sxs-lookup"><span data-stu-id="e8745-116">Options</span></span>  
 <span data-ttu-id="e8745-117">**虛擬目錄**</span><span class="sxs-lookup"><span data-stu-id="e8745-117">**Virtual Directory**</span></span>  
 <span data-ttu-id="e8745-118">為報表管理員指定虛擬目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="e8745-118">Specifies the virtual directory name for Report Manager.</span></span> <span data-ttu-id="e8745-119">相同電腦上的每一個報表管理員執行個體只能有一個虛擬目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="e8745-119">You can only have one virtual directory name for each Report Manager instance on the same computer.</span></span>  
  
 <span data-ttu-id="e8745-120">**URL**</span><span class="sxs-lookup"><span data-stu-id="e8745-120">**URLs**</span></span>  
 <span data-ttu-id="e8745-121">顯示為目前報表管理員執行個體定義的 URL。</span><span class="sxs-lookup"><span data-stu-id="e8745-121">Displays the URL defined for the current Report Manager instance.</span></span>  
  
 <span data-ttu-id="e8745-122">**進階**</span><span class="sxs-lookup"><span data-stu-id="e8745-122">**Advanced**</span></span>  
 <span data-ttu-id="e8745-123">為目前報表管理員執行個體加入額外的 URL。</span><span class="sxs-lookup"><span data-stu-id="e8745-123">Add an additional URL for the current Report Manager instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8745-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8745-124">See Also</span></span>  
 <span data-ttu-id="e8745-125">[設定 SSRS Configuration Manager &#40;的 URL&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="e8745-125">[Configure a URL  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="e8745-126">[&#40;SSRS Configuration Manager 的設定檔中的 Url&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="e8745-126">[URLs in Configuration Files  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="e8745-127">設定報表伺服器 URL &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="e8745-127">Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;</span></span>](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  
