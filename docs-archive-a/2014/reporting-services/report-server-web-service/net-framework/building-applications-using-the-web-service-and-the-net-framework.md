---
title: 使用 Web 服務和 .NET Framework 建置應用程式 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, application building
- .NET Framework [Reporting Services]
- XML Web service [Reporting Services], client creation
- reports [Reporting Services], building
- Web service [Reporting Services], application building
- Report Server Web service, client creation
- client configuration [Reporting Services]
- XML Web service [Reporting Services], application building
- Web service [Reporting Services], client creation
ms.assetid: 92a9678c-bc4f-4d7a-ba44-85989bfe27ca
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5f14a0f2d231d54d12129852b6226c02afd211d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688542"
---
# <a name="building-applications-using-the-web-service-and-the-net-framework"></a><span data-ttu-id="d487b-102">Building Applications Using the Web Service and the .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d487b-102">Building Applications Using the Web Service and the .NET Framework</span></span>
  <span data-ttu-id="d487b-103">使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ，您可以使用熟悉的程式設計結構，例如方法、基本類型，以及使用者定義的複雜類型，來處理 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="d487b-103">With the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], you can use familiar programming constructs, such as methods, primitive types, and user-defined complex types to work with Web services.</span></span> <span data-ttu-id="d487b-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 包含您可用以建立 Web 服務用戶端的基礎結構與工具，而這些用戶端可呼叫任何全球資訊網協會 (W3C) 符合標準的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="d487b-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] contains an infrastructure and tools you can use to create Web service clients that can call any World Wide Web Consortium (W3C) standards-compliant Web service.</span></span>  
  
 <span data-ttu-id="d487b-105">報表伺服器 Web 服務用戶端是與使用簡易物件存取通訊協定 (SOAP) 訊息的報表伺服器，進行通訊的任何元件或是應用程式。</span><span class="sxs-lookup"><span data-stu-id="d487b-105">A Report Server Web service client is any component or application that communicates with a report server using Simple Object Access Protocol (SOAP) messages.</span></span>  
  
 <span data-ttu-id="d487b-106">**若要使用 .NET Framework 來建立報表伺服器 Web 服務用戶端，請遵循以下基本步驟：**</span><span class="sxs-lookup"><span data-stu-id="d487b-106">**To create a Report Server Web service client using the .NET Framework, follow these basic steps:**</span></span>  
  
1.  <span data-ttu-id="d487b-107">建立 Web 服務的 Proxy 類別。</span><span class="sxs-lookup"><span data-stu-id="d487b-107">Create a proxy class for the Web service.</span></span>  
  
     <span data-ttu-id="d487b-108">若要這樣做，請將 Proxy 類別或是 Web 參考加入開發專案、參考用戶端程式碼中的 Proxy 類別，並建立該 Proxy 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d487b-108">To do this, add a proxy class or Web reference to your development project, reference the proxy class in your client code, and create an instance of that proxy.</span></span> <span data-ttu-id="d487b-109">如需詳細資訊，請參閱[建立 Web 服務 Proxy](creating-the-web-service-proxy.md)。</span><span class="sxs-lookup"><span data-stu-id="d487b-109">For more information, see [Creating the Web Service Proxy](creating-the-web-service-proxy.md).</span></span>  
  
2.  <span data-ttu-id="d487b-110">在報表伺服器中驗證 Web 服務用戶端。</span><span class="sxs-lookup"><span data-stu-id="d487b-110">Authenticate the Web service client with the report server.</span></span>  
  
     <span data-ttu-id="d487b-111">若要這樣做，請將服務物件的 <xref:System.Web.Services.Protocols.WebClientProtocol.Credentials%2A> 屬性設定為等於報表伺服器上已驗證使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="d487b-111">To do this, set the service object's <xref:System.Web.Services.Protocols.WebClientProtocol.Credentials%2A> property equal to the credentials of an authenticated user on the report server.</span></span> <span data-ttu-id="d487b-112">如需詳細資訊，請參閱 [Web 服務驗證](web-service-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="d487b-112">For more information, see [Web Service Authentication](web-service-authentication.md).</span></span>  
  
3.  <span data-ttu-id="d487b-113">請呼叫對應至您要叫用之 Web 服務作業的 Proxy 類別之方法。</span><span class="sxs-lookup"><span data-stu-id="d487b-113">Call the method of the proxy class corresponding to the Web service operation that you want to invoke.</span></span>  
  
     <span data-ttu-id="d487b-114">若要這樣做，請呼叫 Web 服務方法並提供必要的引數。</span><span class="sxs-lookup"><span data-stu-id="d487b-114">To do this, call a Web service method and supply the necessary arguments.</span></span> <span data-ttu-id="d487b-115">如需 Web 服務方法的詳細資訊，請參閱[報表伺服器 Web 服務方法](../methods/report-server-web-service-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="d487b-115">For more information about the Web service methods, see [Report Server Web Service Methods](../methods/report-server-web-service-methods.md).</span></span> <span data-ttu-id="d487b-116">如需呼叫的詳細資訊，請參閱[呼叫 Web 服務方法](calling-web-service-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="d487b-116">For more information about calling, see [Calling Web Service Methods](calling-web-service-methods.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d487b-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="d487b-117">In This Section</span></span>  
  
|<span data-ttu-id="d487b-118">主題</span><span class="sxs-lookup"><span data-stu-id="d487b-118">Topic</span></span>|<span data-ttu-id="d487b-119">描述</span><span class="sxs-lookup"><span data-stu-id="d487b-119">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d487b-120">建立 Web 服務 Proxy</span><span class="sxs-lookup"><span data-stu-id="d487b-120">Creating the Web Service Proxy</span></span>](creating-the-web-service-proxy.md)|<span data-ttu-id="d487b-121">描述使用將 proxy 類別加入至您的專案的方式 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d487b-121">Describes the ways to add a proxy class to your project using [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>|  
|[<span data-ttu-id="d487b-122">Web 服務驗證</span><span class="sxs-lookup"><span data-stu-id="d487b-122">Web Service Authentication</span></span>](web-service-authentication.md)|<span data-ttu-id="d487b-123">描述如何驗證報表伺服器 Web 服務的呼叫。</span><span class="sxs-lookup"><span data-stu-id="d487b-123">Describes how calls to the Report Server Web service are authenticated.</span></span>|  
|[<span data-ttu-id="d487b-124">呼叫 Web 服務方法</span><span class="sxs-lookup"><span data-stu-id="d487b-124">Calling Web Service Methods</span></span>](calling-web-service-methods.md)|<span data-ttu-id="d487b-125">描述如何使用 SOAP API 呼叫中的 Web 服務方法 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d487b-125">Describes how to use the SOAP API to call Web service methods in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>|  
|[<span data-ttu-id="d487b-126">設定 Web 服務的 URL 屬性</span><span class="sxs-lookup"><span data-stu-id="d487b-126">Setting the Url Property of the Web Service</span></span>](setting-the-url-property-of-the-web-service.md)|<span data-ttu-id="d487b-127">說明如何在建立 Web 參考之後，以程式設計方式將 Web 服務 Proxy 導向新伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="d487b-127">Explains how to programmatically direct your Web service proxy to a new server URL after you have created your Web reference.</span></span>|  
|[<span data-ttu-id="d487b-128">提供 Web 服務方法引數</span><span class="sxs-lookup"><span data-stu-id="d487b-128">Supplying Web Service Method Arguments</span></span>](supplying-web-service-method-arguments.md)|<span data-ttu-id="d487b-129">描述如何叫用 Web 服務方法並提供方法引數。</span><span class="sxs-lookup"><span data-stu-id="d487b-129">Describes how to invoke a Web service method and supply method arguments.</span></span>|  
|[<span data-ttu-id="d487b-130">省略選擇性 Web 服務物件的值</span><span class="sxs-lookup"><span data-stu-id="d487b-130">Omitting Values for Optional Web Service Objects</span></span>](omitting-values-for-optional-web-service-objects.md)|<span data-ttu-id="d487b-131">描述如何為選擇性 Web 服務物件省略值。</span><span class="sxs-lookup"><span data-stu-id="d487b-131">Describes how to omit values for optional Web service objects.</span></span>|  
|[<span data-ttu-id="d487b-132">使用安全的 Web 服務方法</span><span class="sxs-lookup"><span data-stu-id="d487b-132">Using Secure Web Service Methods</span></span>](using-secure-web-service-methods.md)|<span data-ttu-id="d487b-133">描述 **SecureConnectionLevel** 設定，以及它影響 Reporting Services SOAP API 使用方式的方法。</span><span class="sxs-lookup"><span data-stu-id="d487b-133">Describes the **SecureConnectionLevel** setting and the way in which it affects the use of the Reporting Services SOAP API.</span></span>|  
|[<span data-ttu-id="d487b-134">將裝置資訊設定傳遞至轉譯延伸模組</span><span class="sxs-lookup"><span data-stu-id="d487b-134">Passing Device Information Settings to Rendering Extensions</span></span>](passing-device-information-settings-to-rendering-extensions.md)|<span data-ttu-id="d487b-135">描述用以將報表轉譯成不同格式的裝置資訊設定。</span><span class="sxs-lookup"><span data-stu-id="d487b-135">Describes the device information settings that are used to render reports to different formats.</span></span>|  
|[<span data-ttu-id="d487b-136">Reporting Services 傳遞延伸模組設定</span><span class="sxs-lookup"><span data-stu-id="d487b-136">Reporting Services Delivery Extension Settings</span></span>](reporting-services-delivery-extension-settings.md)|<span data-ttu-id="d487b-137">描述使用報表伺服器電子郵件傳遞報表所用的設定。</span><span class="sxs-lookup"><span data-stu-id="d487b-137">Describes the settings that are used to deliver reports using report server e-mail.</span></span>|  
|[<span data-ttu-id="d487b-138">使用 Reporting Services SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="d487b-138">Using Reporting Services SOAP Headers</span></span>](../../report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)|<span data-ttu-id="d487b-139">說明 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中 SOAP 標頭的用法。</span><span class="sxs-lookup"><span data-stu-id="d487b-139">Explains the use of SOAP headers in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="d487b-140">Reporting Services 中的例外狀況處理簡介</span><span class="sxs-lookup"><span data-stu-id="d487b-140">Introducing Exception Handling in Reporting Services</span></span>](../../report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)|<span data-ttu-id="d487b-141">提供有關 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 處理錯誤之方法的資訊。</span><span class="sxs-lookup"><span data-stu-id="d487b-141">Provides information about the way in which [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] handles errors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d487b-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d487b-142">See Also</span></span>  
 <span data-ttu-id="d487b-143">[報表伺服器 Web 服務](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="d487b-143">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="d487b-144">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d487b-144">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
