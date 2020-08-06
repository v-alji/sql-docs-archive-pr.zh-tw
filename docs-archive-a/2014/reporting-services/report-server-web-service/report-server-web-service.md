---
title: 報表伺服器 Web 服務 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SSIS, Web service
- Web service [Reporting Services]
- Reporting Services, extending
- SQL Server Reporting Services, Web service
- Reporting Services, Web service
- XML Web service [Reporting Services]
- Report Server Web service
ms.assetid: 16c21dec-6b46-4497-9a0c-1b0f2b6ab8fc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8bb43a0fa52a243bd250f70fac16e18d949f8197
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595645"
---
# <a name="report-server-web-service"></a><span data-ttu-id="15f38-102">報表伺服器 Web 服務</span><span class="sxs-lookup"><span data-stu-id="15f38-102">Report Server Web Service</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="15f38-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]透過報表伺服器 Web 服務，提供報表伺服器的完整功能存取權。</span><span class="sxs-lookup"><span data-stu-id="15f38-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] provides access to the full functionality of the report server through the Report Server Web service.</span></span> <span data-ttu-id="15f38-104">報表伺服器 Web 服務是一種具有 SOAP API 的 XML Web 服務。</span><span class="sxs-lookup"><span data-stu-id="15f38-104">The Report Server Web service is an XML Web service with a SOAP API.</span></span> <span data-ttu-id="15f38-105">它使用 SOAP over HTTP，並做為用戶端程式與報表伺服器之間的通訊介面。</span><span class="sxs-lookup"><span data-stu-id="15f38-105">It uses SOAP over HTTP and acts as a communications interface between client programs and the report server.</span></span> <span data-ttu-id="15f38-106">Web 服務提供兩個端點 (一個用於報表執行，一個用於報表管理)，並含有可公開報表伺服器功能的方法，這些方法可讓您為任何部分的報表生命週期建立自訂工具。</span><span class="sxs-lookup"><span data-stu-id="15f38-106">The Web service provides two endpoints - one for report execution and one for report management - with methods that expose the functionality of the report server and enable you to create custom tools for any part of the report life cycle.</span></span>  
  
 <span data-ttu-id="15f38-107">有三種主要的方式可開發以 Web 服務為基礎的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="15f38-107">There are three primary ways to develop [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applications based on the Web service.</span></span> <span data-ttu-id="15f38-108">您可以：</span><span class="sxs-lookup"><span data-stu-id="15f38-108">You can:</span></span>  
  
-   <span data-ttu-id="15f38-109">使用和 SDK 開發應用程式 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="15f38-109">Develop applications using [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.</span></span> <span data-ttu-id="15f38-110">如需使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 建置 Web 服務應用程式的詳細資訊，請參閱[使用 Web 服務和 .NET Framework 建置應用程式](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="15f38-110">For more information about using the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] to build Web service applications, see [Building Applications Using the Web Service and the .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md).</span></span>  
  
-   <span data-ttu-id="15f38-111">使用 **rs** 公用程式 (RS.exe)，即 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 指令碼環境來開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="15f38-111">Develop applications using the **rs** utility (RS.exe), the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] script environment.</span></span> <span data-ttu-id="15f38-112">透過 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 與 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 指令碼，您可以執行任何報表伺服器 Web 服務作業。</span><span class="sxs-lookup"><span data-stu-id="15f38-112">With [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] scripts, you can run any of the Report Server Web service operations.</span></span> <span data-ttu-id="15f38-113">如需以 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 編寫指令碼的詳細資訊，請參閱[利用 rs.exe 公用程式與 Web 服務編寫指令碼](../tools/script-with-the-rs-exe-utility-and-the-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="15f38-113">For more information about scripting in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Script with the rs.exe Utility and the Web Service](../tools/script-with-the-rs-exe-utility-and-the-web-service.md).</span></span>  
  
-   <span data-ttu-id="15f38-114">使用任何啟用 SOAP 的開發工具集來開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="15f38-114">Develop applications using any SOAP-enabled set of development tools.</span></span> <span data-ttu-id="15f38-115">如需詳細資訊，請參閱 [Reporting Services 中的 SOAP 角色](../report-server-web-service/the-role-of-soap-in-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="15f38-115">For more information, see [The Role of SOAP in Reporting Services](../report-server-web-service/the-role-of-soap-in-reporting-services.md).</span></span>  
  
## <a name="programming-diagram"></a><span data-ttu-id="15f38-116">程式設計圖表</span><span class="sxs-lookup"><span data-stu-id="15f38-116">Programming Diagram</span></span>  
 <span data-ttu-id="15f38-117">![報表伺服器 Web 服務部署選項](../../../2014/reporting-services/media/reportserviceswebserviceprog-01.gif "報表伺服器 Web 服務部署選項")</span><span class="sxs-lookup"><span data-stu-id="15f38-117">![Report Server Web service development options](../../../2014/reporting-services/media/reportserviceswebserviceprog-01.gif "Report Server Web service development options")</span></span>  
<span data-ttu-id="15f38-118">Reporting Services 可用的 Web 服務開發選項</span><span class="sxs-lookup"><span data-stu-id="15f38-118">Reporting Services available Web service development options</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15f38-119">本節內容</span><span class="sxs-lookup"><span data-stu-id="15f38-119">In This Section</span></span>  
 [<span data-ttu-id="15f38-120">報表伺服器 Web 服務方法</span><span class="sxs-lookup"><span data-stu-id="15f38-120">Report Server Web Service Methods</span></span>](../report-server-web-service/methods/report-server-web-service-methods.md)  
 <span data-ttu-id="15f38-121">描述每個報表伺服器 Web 服務的功能及方法。</span><span class="sxs-lookup"><span data-stu-id="15f38-121">Describes the features and methods of each Report Server Web service.</span></span>  
  
 [<span data-ttu-id="15f38-122">The Role of SOAP in Reporting Services</span><span class="sxs-lookup"><span data-stu-id="15f38-122">The Role of SOAP in Reporting Services</span></span>](../report-server-web-service/the-role-of-soap-in-reporting-services.md)  
 <span data-ttu-id="15f38-123">提供 SOAP 的概觀以及在報表伺服器 Web 服務中如何使用它。</span><span class="sxs-lookup"><span data-stu-id="15f38-123">Provides an overview of SOAP and how it is used in the Report Server Web services.</span></span>  
  
 [<span data-ttu-id="15f38-124">存取 SOAP API</span><span class="sxs-lookup"><span data-stu-id="15f38-124">Accessing the SOAP API</span></span>](../report-server-web-service/accessing-the-soap-api.md)  
 <span data-ttu-id="15f38-125">描述 Web 服務描述語言 (WSDL) 並提供 URL 以存取 Reporting Services WSDL 檔案。</span><span class="sxs-lookup"><span data-stu-id="15f38-125">Describes the Web Service Description Language (WSDL) and provides URLs for accessing a Reporting Services WSDL file.</span></span>  
  
 [<span data-ttu-id="15f38-126">使用 Web 服務和 .NET Framework 建置應用程式</span><span class="sxs-lookup"><span data-stu-id="15f38-126">Building Applications Using the Web Service and the .NET Framework</span></span>](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
 <span data-ttu-id="15f38-127">包含有關開發應用程式與 Web 服務以呼叫 Reporting Services SOAP API 的資訊。</span><span class="sxs-lookup"><span data-stu-id="15f38-127">Contains information about developing applications and Web services that call the Reporting Services SOAP API.</span></span>  
  
 [<span data-ttu-id="15f38-128">利用 rs.exe 公用程式與 Web 服務編寫指令碼</span><span class="sxs-lookup"><span data-stu-id="15f38-128">Script with the rs.exe Utility and the Web Service</span></span>](../tools/script-with-the-rs-exe-utility-and-the-web-service.md)  
 <span data-ttu-id="15f38-129">提供 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 指令碼環境的概觀。</span><span class="sxs-lookup"><span data-stu-id="15f38-129">Provides an overview of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] scripting environment.</span></span>  
  
 [<span data-ttu-id="15f38-130">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="15f38-130">Technical Reference &#40;SSRS&#41;</span></span>](../../../2014/reporting-services/technical-reference-ssrs.md)  
 <span data-ttu-id="15f38-131">包含報表伺服器 Web 服務方法及對應之複雜類型的特有參考資料。</span><span class="sxs-lookup"><span data-stu-id="15f38-131">Contains reference material specific to Report Server Web services methods and corresponding complex types.</span></span>  
  
## <a name="user-requirements-for-web-service-development"></a><span data-ttu-id="15f38-132">Web 服務開發的使用者需求</span><span class="sxs-lookup"><span data-stu-id="15f38-132">User Requirements for Web Service Development</span></span>  
 <span data-ttu-id="15f38-133">若要使用報表伺服器 Web 服務開發應用程式，您需要：</span><span class="sxs-lookup"><span data-stu-id="15f38-133">To develop applications using the Report Server Web service, you need:</span></span>  
  
-   <span data-ttu-id="15f38-134">在有網際網路連線及可存取報表伺服器的電腦上安裝 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer 5.5 或更新的版本。</span><span class="sxs-lookup"><span data-stu-id="15f38-134">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer 5.5 or later installed on a computer with an Internet connection to and access to the report server.</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="15f38-135">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 或 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]如果您想要使用開發和部署應用程式，請在電腦上安裝 SDK [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="15f38-135">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK installed on a computer if you want to develop and deploy [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applications using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span>  
  
-   <span data-ttu-id="15f38-136">深入瞭解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 特性和功能。</span><span class="sxs-lookup"><span data-stu-id="15f38-136">An in-depth understanding of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features and capabilities.</span></span>  
  
-   <span data-ttu-id="15f38-137">對 SOAP 和 [!INCLUDE[vstecwebservices](../../includes/vstecwebservices-md.md)]有確實的了解。</span><span class="sxs-lookup"><span data-stu-id="15f38-137">A firm understanding of SOAP and [!INCLUDE[vstecwebservices](../../includes/vstecwebservices-md.md)].</span></span>  
  
-   <span data-ttu-id="15f38-138">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 如果您打算使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 做為開發平臺，則為相容語言（例如或）的開發經驗。</span><span class="sxs-lookup"><span data-stu-id="15f38-138">Development experience in a [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-compatible language such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] or [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], if you plan to use the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] as your development platform.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15f38-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15f38-139">See Also</span></span>  
 [<span data-ttu-id="15f38-140">報表伺服器 Web 服務</span><span class="sxs-lookup"><span data-stu-id="15f38-140">Report Server Web Service</span></span>](../report-server-web-service/report-server-web-service.md)  
  
  
