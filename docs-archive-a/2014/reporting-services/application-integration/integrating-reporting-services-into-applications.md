---
title: 將 Reporting Services 整合到應用程式 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- integrating reports [Reporting Services]
- custom applications [SSRS]
- Reporting Services, application integration
- application integration [Reporting Services]
- reports [Reporting Services], integrating
ms.assetid: 49eb539c-d89b-4291-839a-0ec1a65cd270
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3ab92008c5beb4d931e8e781857d766bb56a1efd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585161"
---
# <a name="integrating-reporting-services-into-applications"></a><span data-ttu-id="be234-102">將 Reporting Services 整合到應用程式</span><span class="sxs-lookup"><span data-stu-id="be234-102">Integrating Reporting Services into Applications</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="be234-103">是開放且可延伸的報表平台，用以提供開發人員一組完整的 API 以開發方案。</span><span class="sxs-lookup"><span data-stu-id="be234-103">is an open and extensible reporting platform designed to provide developers with a comprehensive set of APIs for developing solutions.</span></span>  
  
 <span data-ttu-id="be234-104">有三個選項可整合 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 到自訂應用程式：報表伺服器 Web 服務（也稱為 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SOAP API）、的 ReportViewer 控制項以及 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] URL 存取。</span><span class="sxs-lookup"><span data-stu-id="be234-104">There are three options for integrating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into custom applications: the Report Server Web service, also known as the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SOAP API, the ReportViewer controls for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)], and URL access.</span></span> <span data-ttu-id="be234-105">每個選項都提供不同的方法，將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 整合到應用程式中。</span><span class="sxs-lookup"><span data-stu-id="be234-105">Each option provides a different approach for integrating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into your applications.</span></span>  
  
## <a name="report-server-web-service"></a><span data-ttu-id="be234-106">報表伺服器 Web 服務</span><span class="sxs-lookup"><span data-stu-id="be234-106">Report Server Web Service</span></span>  
 <span data-ttu-id="be234-107">報表伺服器 Web 服務是用於針對 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 進行開發的主要介面。</span><span class="sxs-lookup"><span data-stu-id="be234-107">The Report Server Web service is the primary interface for developing against [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="be234-108">不論您是開發程式碼以管理報表目錄，或是開發程式碼將報表轉譯成支援的格式，Web 服務都會公開所需的方法，來將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 整合到應用程式。</span><span class="sxs-lookup"><span data-stu-id="be234-108">Whether you are developing code to manage your report catalog or developing code to render reports to a supported format, the Web service exposes all the necessary methods to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into your applications.</span></span> <span data-ttu-id="be234-109">這類應用程式的範例是報表管理員，它是隨附在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中，使用 Web 服務來管理報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="be234-109">An example of one such application is Report Manager, which is included with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]; it uses the Web service to manage the report server database.</span></span>  
  
## <a name="reportviewer-controls-for-visual-studio"></a><span data-ttu-id="be234-110">Visual Studio 的 ReportViewer 控制項</span><span class="sxs-lookup"><span data-stu-id="be234-110">ReportViewer Controls for Visual Studio</span></span>  
 <span data-ttu-id="be234-111">[!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] 隨附的 ReportViewer 控制項是用以將報表檢視整合到應用程式。</span><span class="sxs-lookup"><span data-stu-id="be234-111">The ReportViewer controls included with [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] are used for integrating report viewing into your applications.</span></span> <span data-ttu-id="be234-112">有兩個控制項：一個用於 Windows Form 應用程式，另一個用於 Web Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="be234-112">There are two controls: one for Windows Forms-based applications and one for Web Forms applications.</span></span> <span data-ttu-id="be234-113">每個控制項都提供可檢視已部署到報表伺服器的報表功能，以及轉譯尚未安裝報表伺服器的環境中所存在之報表的能力。</span><span class="sxs-lookup"><span data-stu-id="be234-113">Each control provides the capability for viewing reports that have been deployed to a report server as well as the ability to render reports that exist in an environment where a report server has not been installed.</span></span>  
  
## <a name="url-access"></a><span data-ttu-id="be234-114">URL 存取</span><span class="sxs-lookup"><span data-stu-id="be234-114">URL Access</span></span>  
 <span data-ttu-id="be234-115">如果 ReportViewer 控制項不是一個選項，則 URL 存取是將報表檢視整合到應用程式的另一個選項。</span><span class="sxs-lookup"><span data-stu-id="be234-115">URL access is another option for integrating report viewing into your applications if the ReportViewer controls are not an option.</span></span> <span data-ttu-id="be234-116">此外，URL 存取對於透過電子郵件將報表連結傳送到使用者非常有用。</span><span class="sxs-lookup"><span data-stu-id="be234-116">In addition, URL access is useful for sending links to reports to users via e-mail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="be234-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="be234-117">In This Section</span></span>  
 [<span data-ttu-id="be234-118">使用 SOAP 整合 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="be234-118">Integrating Reporting Services Using SOAP</span></span>](../application-integration/integrating-reporting-services-using-soap.md)  
 <span data-ttu-id="be234-119">描述如何使用報表伺服器 Web 服務，將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表導覽與管理整合到現有的商務應用程式。</span><span class="sxs-lookup"><span data-stu-id="be234-119">Describes how to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report navigation and management into your existing business applications using the Report Server Web service.</span></span>  
  
 [<span data-ttu-id="be234-120">使用 ReportViewer 控制項整合 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="be234-120">Integrating Reporting Services Using the ReportViewer Controls</span></span>](../application-integration/integrating-reporting-services-using-reportviewer-controls.md)  
 <span data-ttu-id="be234-121">描述如何使用 ReportViewer 控制項將報表檢視整合到現有的應用程式。</span><span class="sxs-lookup"><span data-stu-id="be234-121">Describes how to integrate report viewing into your existing applications using the ReportViewer controls.</span></span>  
  
 [<span data-ttu-id="be234-122">使用 URL 存取整合 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="be234-122">Integrating Reporting Services Using URL Access</span></span>](../application-integration/integrating-reporting-services-using-url-access.md)  
 <span data-ttu-id="be234-123">描述如何使用 URL 存取，將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表導覽整合到現有的商務應用程式。</span><span class="sxs-lookup"><span data-stu-id="be234-123">Describes how to integrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report navigation into your existing business applications using URL access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be234-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be234-124">See Also</span></span>  
 <span data-ttu-id="be234-125">[報表管理員 &#40;SSRS 原生模式&#41;](../../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="be234-125">[Report Manager  &#40;SSRS Native Mode&#41;](../../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="be234-126">[在 URL 存取和 SOAP 之間選擇](../../../2014/reporting-services/application-integration/choosing-between-url-access-and-soap.md) </span><span class="sxs-lookup"><span data-stu-id="be234-126">[Choosing Between URL Access and SOAP](../../../2014/reporting-services/application-integration/choosing-between-url-access-and-soap.md) </span></span>  
 <span data-ttu-id="be234-127">[SSRS&#41;&#40;的技術參考](../../../2014/reporting-services/technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="be234-127">[Technical Reference &#40;SSRS&#41;](../../../2014/reporting-services/technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="be234-128">報表伺服器 Web 服務</span><span class="sxs-lookup"><span data-stu-id="be234-128">Report Server Web Service</span></span>](../report-server-web-service/report-server-web-service.md)  
  
  
