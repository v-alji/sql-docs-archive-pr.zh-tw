---
title: 報表伺服器 Web 服務端點 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- management endpoints [Reporting Services]
- Web service [Reporting Services], endpoints
- endpoints [Reporting Services]
- execution endpoints [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: f3f5d85f-9359-4508-bc5a-7f78a3cf7421
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 70281c5171eb37d9888d663542a7850820c81bea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702381"
---
# <a name="report-server-web-service-endpoints"></a><span data-ttu-id="4d725-102">報表伺服器 Web 服務端點</span><span class="sxs-lookup"><span data-stu-id="4d725-102">Report Server Web Service Endpoints</span></span>
  <span data-ttu-id="4d725-103">報表伺服器 Web 服務提供幾個端點來管理報表伺服器以及執行和導覽報表。</span><span class="sxs-lookup"><span data-stu-id="4d725-103">The Report Server Web service provides several endpoints for managing a report server as well as executing and navigating reports.</span></span>  
  
## <a name="the-management-endpoints"></a><span data-ttu-id="4d725-104">管理端點</span><span class="sxs-lookup"><span data-stu-id="4d725-104">The Management Endpoints</span></span>  
 <span data-ttu-id="4d725-105">報表伺服器上有三個端點可用來管理物件：<xref:ReportService2005>、<xref:ReportService2006> 和 <xref:ReportService2010>。</span><span class="sxs-lookup"><span data-stu-id="4d725-105">There are three endpoints available for managing objects on a report server, <xref:ReportService2005>, <xref:ReportService2006>, and <xref:ReportService2010>.</span></span> <span data-ttu-id="4d725-106"><xref:ReportService2005> 端點是用來在設定為原生模式的報表伺服器上管理物件。</span><span class="sxs-lookup"><span data-stu-id="4d725-106">The <xref:ReportService2005> endpoint is used for managing objects on a report server that is configured for native mode.</span></span> <span data-ttu-id="4d725-107"><xref:ReportService2006> 端點是用來在設定為 SharePoint 整合模式的報表伺服器上管理物件。</span><span class="sxs-lookup"><span data-stu-id="4d725-107">The <xref:ReportService2006> endpoint is used for managing objects on a report server that is configured for SharePoint integrated mode.</span></span> <span data-ttu-id="4d725-108"><xref:ReportService2010> 端點合併 <xref:ReportService2005> 和 <xref:ReportService2006> 的功能，且可用來在設定為原生模式或 SharePoint 整合模式的報表伺服器上管理物件。</span><span class="sxs-lookup"><span data-stu-id="4d725-108">The <xref:ReportService2010> endpoint merges the functionalities of <xref:ReportService2005> and <xref:ReportService2006> and can manage objects on a report server that are configured for either native or SharePoint integrated mode.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4d725-109">當報表伺服器設定為 SharePoint 整合模式時，<xref:ReportService2005> API 會傳回 `rsOperationNotSupportedSharePointMode` 錯誤。</span><span class="sxs-lookup"><span data-stu-id="4d725-109">When a report server is configured for SharePoint integrated mode, the <xref:ReportService2005> APIs will return an `rsOperationNotSupportedSharePointMode` error.</span></span> <span data-ttu-id="4d725-110">如果報表伺服器設定為原生模式，則 <xref:ReportService2006> API 會傳回 `rsOperationNotSupportedNativeMode` 錯誤。</span><span class="sxs-lookup"><span data-stu-id="4d725-110">If the report server is configured for native mode, the <xref:ReportService2006> APIs will return an `rsOperationNotSupportedNativeMode` error.</span></span> <span data-ttu-id="4d725-111">同樣地，在非預期的模式上使用 <xref:ReportService2010> 中特屬模式的 API 時，API 會傳回相對應的錯誤。</span><span class="sxs-lookup"><span data-stu-id="4d725-111">Similarly, when mode-specific APIs in <xref:ReportService2010> are used on unintended modes, the APIs will return the respective errors.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d725-112"><xref:ReportService2005> 和 <xref:ReportService2006> 端點是在 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 中被取代。</span><span class="sxs-lookup"><span data-stu-id="4d725-112">The <xref:ReportService2005> and <xref:ReportService2006> endpoints are deprecated in [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="4d725-113"><xref:ReportService2010> 端點包含這兩個端點的功能，並包含額外的管理功能。</span><span class="sxs-lookup"><span data-stu-id="4d725-113">The <xref:ReportService2010> endpoint includes the functionalities of both endpoints and contains additional management features.</span></span>  
  
 <span data-ttu-id="4d725-114">如果報表伺服器設定為原生模式或 SharePoint 整合模式，您可以使用下列其中一個 URL 來存取管理端點的 WSDL：</span><span class="sxs-lookup"><span data-stu-id="4d725-114">If the report server is configured for native mode or SharePoint integrate mode, the WSDL for the management endpoint can be accessed using one of the following URL:</span></span>  
  
```  
http://<Server Name>/ReportServer/ReportService2010.asmx?wsdl  
```  
  
 <span data-ttu-id="4d725-115">如需詳細資訊，請參閱[存取 SOAP API](../accessing-the-soap-api.md)。</span><span class="sxs-lookup"><span data-stu-id="4d725-115">For more information, see [Accessing the SOAP API](../accessing-the-soap-api.md).</span></span>  
  
## <a name="the-execution-endpoint"></a><span data-ttu-id="4d725-116">執行端點</span><span class="sxs-lookup"><span data-stu-id="4d725-116">The Execution Endpoint</span></span>  
 <span data-ttu-id="4d725-117"><xref:ReportExecution2005> 端點可讓開發人員輕鬆地自訂報表處理，並在原生模式和 SharePoint 整合模式下從報表伺服器進行轉譯。</span><span class="sxs-lookup"><span data-stu-id="4d725-117">The <xref:ReportExecution2005> endpoint makes it easy for developers to customize report processing and rendering from a report server in both native and SharePoint integrated modes.</span></span> <span data-ttu-id="4d725-118">此端點包括之前在舊版報表伺服器 Web 服務中存在的類別和方法。</span><span class="sxs-lookup"><span data-stu-id="4d725-118">The endpoint includes classes and methods that existed in earlier versions of the Report Server Web service.</span></span> <span data-ttu-id="4d725-119">此外，報表伺服器 Web 服務中也加入了許多新的類別和方法，它們可透過執行端點而公開。</span><span class="sxs-lookup"><span data-stu-id="4d725-119">In addition, many new classes and methods have been added to the Report Server Web service that are exposed through the execution endpoint.</span></span>  
  
 <span data-ttu-id="4d725-120">可以使用下列 URL 來存取管理端點的 WSDL：</span><span class="sxs-lookup"><span data-stu-id="4d725-120">The WSDL for the management endpoint can be accessed using the following URL:</span></span>  
  
```  
http://<Server Name>/ReportServer/ReportExecution2005.asmx?wsdl  
```  
  
 <span data-ttu-id="4d725-121">如果報表伺服器設定為 SharePoint 整合模式，可以使用下列 URL 來存取 WSDL：</span><span class="sxs-lookup"><span data-stu-id="4d725-121">If the report server is configured for SharePoint integrate mode, the WSDL can be accessed using the following URL:</span></span>  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportExecution2005.asmx?wsdl  
```  
  
 <span data-ttu-id="4d725-122">如需詳細資訊，請參閱[存取 SOAP API](../accessing-the-soap-api.md)。</span><span class="sxs-lookup"><span data-stu-id="4d725-122">For more information, please see [Accessing the SOAP API](../accessing-the-soap-api.md).</span></span>  
  
## <a name="sharepoint-proxy-endpoints"></a><span data-ttu-id="4d725-123">SharePoint Proxy 端點</span><span class="sxs-lookup"><span data-stu-id="4d725-123">SharePoint Proxy Endpoints</span></span>  
 <span data-ttu-id="4d725-124">當報表伺服器設定為 SharePoint 整合模式，而且已經安裝 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 增益集時，SharePoint 伺服器上會安裝一組 Proxy 端點。</span><span class="sxs-lookup"><span data-stu-id="4d725-124">When a report server is configured for SharePoint integrated mode and the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Add-in has been installed, a set of proxy endpoints are installed on the SharePoint server.</span></span> <span data-ttu-id="4d725-125">當報表伺服器設定為 SharePoint 整合模式時，這些 Proxy 端點是用來開發報表方案的主要 API。</span><span class="sxs-lookup"><span data-stu-id="4d725-125">The proxy endpoints are the primary API for developing report solutions when a report server is configured for SharePoint integrated mode.</span></span> <span data-ttu-id="4d725-126">當針對 Proxy 端點進行開發時，[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 增益集會在信任帳戶驗證模式下管理 SharePoint 伺服器與報表伺服器之間的認證交換。</span><span class="sxs-lookup"><span data-stu-id="4d725-126">When developing against the proxy endpoints, the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Add-in manages the exchange of credentials between the SharePoint server and the report server in Trusted account authentication mode.</span></span> <span data-ttu-id="4d725-127">當針對報表伺服器端點開發時，呼叫應用程式必須在信任帳戶驗證模式下管理認證交換。</span><span class="sxs-lookup"><span data-stu-id="4d725-127">When developing against the report server endpoints, the calling application will have to manage the credential exchange in Trusted account authentication mode.</span></span> <span data-ttu-id="4d725-128">下表將列出隨 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 增益集一起安裝的端點。</span><span class="sxs-lookup"><span data-stu-id="4d725-128">The following table lists the endpoints that are installed with the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Add-in.</span></span>  
  
|<span data-ttu-id="4d725-129">Proxy 端點</span><span class="sxs-lookup"><span data-stu-id="4d725-129">Proxy Endpoint</span></span>|<span data-ttu-id="4d725-130">描述</span><span class="sxs-lookup"><span data-stu-id="4d725-130">Description</span></span>|  
|--------------------|-----------------|  
|<xref:ReportService2006>|<span data-ttu-id="4d725-131">提供 API 以管理設定為 SharePoint 整合模式的報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="4d725-131">Provides the APIs for managing a report server that is configured for SharePoint integrate mode.</span></span> <span data-ttu-id="4d725-132">**注意：** 這個端點在中已被取代 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4d725-132">**Note:**  This endpoint is deprecated in [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)].</span></span>|  
|<xref:ReportService2010>|<span data-ttu-id="4d725-133">提供 API 以管理設定為原生模式或 SharePoint 整合模式的報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="4d725-133">Provides the APIs for managing a report server that is configured for either native or SharePoint integrated mode.</span></span>|  
|<xref:ReportExecution2005>|<span data-ttu-id="4d725-134">提供 API 來執行及導覽報表。</span><span class="sxs-lookup"><span data-stu-id="4d725-134">Provides the APIs for running and navigating reports.</span></span>|  
|<xref:ReportServiceAuthentication>|<span data-ttu-id="4d725-135">提供 API，在 SharePoint Web 應用程式有設定表單驗證時，針對報表伺服器來驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="4d725-135">Provides the APIs for authenticating users against a report server when the SharePoint Web application is configured for Forms Authentication.</span></span>|  
  
 <span data-ttu-id="4d725-136">下列是在 SharePoint 網站上參考 Proxy 端點的 URL 範例。</span><span class="sxs-lookup"><span data-stu-id="4d725-136">The following are example URLs for referencing the proxy endpoints on a SharePoint site.</span></span>  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportService2010.asmx  
```  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportExecution2005.asmx  
```  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportServiceAuthentication.asmx  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d725-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d725-137">See Also</span></span>  
 [<span data-ttu-id="4d725-138">使用 Web 服務和 .NET Framework 建置應用程式</span><span class="sxs-lookup"><span data-stu-id="4d725-138">Building Applications Using the Web Service and the .NET Framework</span></span>](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
