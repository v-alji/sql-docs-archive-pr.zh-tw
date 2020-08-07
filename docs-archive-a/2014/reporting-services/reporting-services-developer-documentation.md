---
title: 開發人員&#39;s 指南 (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- developer's guide [Reporting Services]
- Reporting Services, programming
- programming [Reporting Services]
ms.assetid: d8afa405-1012-4349-a72d-e10d94f8453d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bcf880db543c891a0ffccab932fddc614df34e17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703793"
---
# <a name="developer39s-guide-reporting-services"></a><span data-ttu-id="82303-102">開發人員&#39;s 指南 (Reporting Services) </span><span class="sxs-lookup"><span data-stu-id="82303-102">Developer&#39;s Guide (Reporting Services)</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="82303-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 提供一些可在自有應用程式中利用的程式設計介面。</span><span class="sxs-lookup"><span data-stu-id="82303-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] offers several programming interfaces that you can leverage in your own applications.</span></span> <span data-ttu-id="82303-104">您可以使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 的現有功能和能力，將自訂報表與管理工具建立到網站和 Windows 應用程式中，或是可以延伸 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 平台。</span><span class="sxs-lookup"><span data-stu-id="82303-104">You can use the existing features and capabilities of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] to build custom reporting and management tools into Web sites and Windows applications, or you can extend the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] platform.</span></span>  
  
 <span data-ttu-id="82303-105">擴充 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 平台包括建立可用於資料存取、報表傳遞等的新元件與資源。</span><span class="sxs-lookup"><span data-stu-id="82303-105">Extending the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] platform includes creating new components and resources that can be used for data access, report delivery and more.</span></span> <span data-ttu-id="82303-106">您可以將這些元件與資源行銷到在其組織中使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 的公司。</span><span class="sxs-lookup"><span data-stu-id="82303-106">You can market these components and resources to companies that are using [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in their organization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="82303-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="82303-107">In This Section</span></span>  
 [<span data-ttu-id="82303-108">將 Reporting Services 整合到應用程式</span><span class="sxs-lookup"><span data-stu-id="82303-108">Integrating Reporting Services into Applications</span></span>](application-integration/integrating-reporting-services-into-applications.md)  
 <span data-ttu-id="82303-109">提供如何使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 將報表整合到自訂應用程式的概觀。</span><span class="sxs-lookup"><span data-stu-id="82303-109">Provides an overview of how to use [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] to integrate reporting into custom applications.</span></span> <span data-ttu-id="82303-110">描述何時使用直接的 URL 存取，以及何時使用 Web 服務存取報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="82303-110">Describes when to use direct URL access and when to use the Web service to access the report server.</span></span>  
  
 [<span data-ttu-id="82303-111">報表伺服器 Web 服務</span><span class="sxs-lookup"><span data-stu-id="82303-111">Report Server Web Service</span></span>](report-server-web-service/report-server-web-service.md)  
 <span data-ttu-id="82303-112">報表伺服器 Web 服務提供報表伺服器的完整功能存取。</span><span class="sxs-lookup"><span data-stu-id="82303-112">The Report Server Web service provides access to the full functionality of the report server.</span></span> <span data-ttu-id="82303-113">Web 服務透過 HTTP 使用 SOAP，並設計成做為用戶端程式與報表伺服器之間的通訊介面。</span><span class="sxs-lookup"><span data-stu-id="82303-113">The Web service uses SOAP over HTTP and is designed to act as a communications interface between client programs and the report server.</span></span> <span data-ttu-id="82303-114">Web 服務及其方法會公開報表伺服器的功能，並可讓您為任何部分的報表生命週期建立從管理到執行的自訂工具。</span><span class="sxs-lookup"><span data-stu-id="82303-114">The Web service and its methods expose the functionality of the report server and allow you to create custom tools for any part of the report life cycle, from management to execution.</span></span>  
  
 [<span data-ttu-id="82303-115">URL 存取 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="82303-115">URL Access &#40;SSRS&#41;</span></span>](url-access-ssrs.md)  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="82303-116">支援一組完整且以 URL 為基礎的要求，讓您得以使用快速且輕鬆的存取點來進行報表導覽和檢視。</span><span class="sxs-lookup"><span data-stu-id="82303-116">supports a complete set of URL-based requests that you can use as a quick and easy access point for report navigation and viewing.</span></span> <span data-ttu-id="82303-117">您可以和報表伺服器 Web 服務搭配使用這項技術，將完整的報表方案整合到自訂商務應用程式。</span><span class="sxs-lookup"><span data-stu-id="82303-117">You can use this technology in conjunction with the Report Server Web service to integrate a complete reporting solution into your custom business applications.</span></span> <span data-ttu-id="82303-118">當將報表整合為 Web 入口網站的一部分時，或是當從網頁瀏覽器檢視報表時，URL 存取將特別有用。</span><span class="sxs-lookup"><span data-stu-id="82303-118">URL access is particularly useful when integrating reports as part of a Web portal or when viewing reports from a Web browser.</span></span>  
  
 [<span data-ttu-id="82303-119">Reporting Services 延伸模組</span><span class="sxs-lookup"><span data-stu-id="82303-119">Reporting Services Extensions</span></span>](extensions/reporting-services-extensions.md)  
 <span data-ttu-id="82303-120">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 的模組化架構是針對擴充性所設計。</span><span class="sxs-lookup"><span data-stu-id="82303-120">The modular architecture of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] is designed for extensibility.</span></span> <span data-ttu-id="82303-121">現在可以使用 Managed 程式碼 API，這樣您就可以輕鬆地開發、安裝和管理許多 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 元件取用的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="82303-121">A managed code API is available so that you can easily develop, install, and manage extensions consumed by many [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] components.</span></span> <span data-ttu-id="82303-122">您可以使用建立元件， [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 並加入新的轉譯 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 、安全性、傳遞和資料處理功能，以滿足不斷演進的商務需求。</span><span class="sxs-lookup"><span data-stu-id="82303-122">You can create assemblies using the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] and add new [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] rendering, security, delivery, and data processing functionality to meet your evolving business needs.</span></span>  
  
 [<span data-ttu-id="82303-123">自訂報表項目</span><span class="sxs-lookup"><span data-stu-id="82303-123">Custom Report Items</span></span>](custom-report-items/custom-report-items.md)  
 <span data-ttu-id="82303-124">描述如何建立自訂報表項目，將功能加入現有控制項的 RDL 或是擴充功能。</span><span class="sxs-lookup"><span data-stu-id="82303-124">Describes how to create Custom Report Items to add functionality to RDL or extend functionality of existing controls.</span></span>  
  
 [<span data-ttu-id="82303-125">將自訂組件與報表搭配使用</span><span class="sxs-lookup"><span data-stu-id="82303-125">Using Custom Assemblies with Reports</span></span>](custom-assemblies/using-custom-assemblies-with-reports.md)  
 <span data-ttu-id="82303-126">描述如何在報表定義中包括程式碼參考，將自訂組件與報表搭配使用。</span><span class="sxs-lookup"><span data-stu-id="82303-126">Describes how to use custom assemblies with Reports by including code references within the report definition.</span></span>  
  
 [<span data-ttu-id="82303-127">存取 Reporting Services WMI 提供者</span><span class="sxs-lookup"><span data-stu-id="82303-127">Access the Reporting Services WMI Provider</span></span>](tools/access-the-reporting-services-wmi-provider.md)  
 <span data-ttu-id="82303-128">描述如何使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] WMI 提供者來管理報表伺服器部署。</span><span class="sxs-lookup"><span data-stu-id="82303-128">Describes how to use the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] WMI Provider to manage report server deployments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82303-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82303-129">See Also</span></span>  
 <span data-ttu-id="82303-130">[Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) </span><span class="sxs-lookup"><span data-stu-id="82303-130">[Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) </span></span>  
 <span data-ttu-id="82303-131">[&#40;SSRS&#41;的報表定義語言](reports/report-definition-language-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="82303-131">[Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md) </span></span>  
 <span data-ttu-id="82303-132">[SSRS&#41;&#40;的技術參考](technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="82303-132">[Technical Reference &#40;SSRS&#41;](technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="82303-133">安全開發 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="82303-133">Secure Development &#40;Reporting Services&#41;</span></span>](extensions/secure-development/secure-development-reporting-services.md)  
  
  
