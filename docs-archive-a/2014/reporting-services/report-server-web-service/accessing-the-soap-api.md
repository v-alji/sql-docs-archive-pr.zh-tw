---
title: 存取 SOAP API | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- XML Web service [Reporting Services], WSDL
- Web service [Reporting Services], SOAP
- calling Web service
- SOAP [Reporting Services], accessing
- Report Server Web service, SOAP
- Web service [Reporting Services], WSDL
- WSDL [Reporting Services]
- XML Web service [Reporting Services], SOAP
- Report Server Web service, WSDL
- referencing WSDL
ms.assetid: 63bb870a-4dbf-46bd-8921-78f8ebe5fd75
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6e8a0c21bb53deff746cfd916b6ae2c96fa0de19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599335"
---
# <a name="accessing-the-soap-api"></a><span data-ttu-id="9b5df-102">存取 SOAP API</span><span class="sxs-lookup"><span data-stu-id="9b5df-102">Accessing the SOAP API</span></span>
  <span data-ttu-id="9b5df-103">報表伺服器 Web 服務透過 HTTP 使用簡易物件存取通訊協定 (SOAP)，並在用戶端程式與報表伺服器之間當做通訊介面。</span><span class="sxs-lookup"><span data-stu-id="9b5df-103">The Report Server Web service uses Simple Object Access Protocol (SOAP) over HTTP and acts as a communications interface between client programs and the report server.</span></span> <span data-ttu-id="9b5df-104">Web 服務提供兩個端點 (一個用於報表執行，一個用於報表管理)，並且含有方法以及一組您可用以存取完整功能的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 之複雜類型的物件。</span><span class="sxs-lookup"><span data-stu-id="9b5df-104">The Web service provides two endpoints - one for report execution and one for report management - and consists of methods and a set of complex type objects that you can use to access the complete functionality of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="9b5df-105">若要呼叫服務，您必須參考 Reporting Services Web 服務描述語言 (WSDL)。</span><span class="sxs-lookup"><span data-stu-id="9b5df-105">To call the service, you must reference the Reporting Services Web Services Description Language (WSDL).</span></span>  
  
## <a name="referencing-the-reporting-services-wsdl"></a><span data-ttu-id="9b5df-106">參考 Reporting Services WSDL</span><span class="sxs-lookup"><span data-stu-id="9b5df-106">Referencing the Reporting Services WSDL</span></span>  
 <span data-ttu-id="9b5df-107">若要順利呼叫 Web 服務，您必須知道如何存取服務，服務支援哪些作業、服務需要哪些參數以及服務會傳回哪些內容。</span><span class="sxs-lookup"><span data-stu-id="9b5df-107">To call a Web service successfully, you must know how to access the service, what operations the service supports, what parameters the service expects, and what the service returns.</span></span> <span data-ttu-id="9b5df-108">WSDL 是以電腦可讀取或處理的 XML 文件提供這項資訊。</span><span class="sxs-lookup"><span data-stu-id="9b5df-108">WSDL provides this information in an XML document that can be read or processed by a computer.</span></span>  
  
 <span data-ttu-id="9b5df-109">報表伺服器 Web 服務是以三個不同的端點公開。</span><span class="sxs-lookup"><span data-stu-id="9b5df-109">The Report Server Web services are exposed in three different endpoints.</span></span> <span data-ttu-id="9b5df-110">每個端點都有不同的 WSDL 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="9b5df-110">The name of the WSDL file is different for each endpoint.</span></span> <span data-ttu-id="9b5df-111"><xref:ReportService2010> 端點包含以原生模式或 SharePoint 整合模式在報表伺服器上管理物件的方法。</span><span class="sxs-lookup"><span data-stu-id="9b5df-111">The <xref:ReportService2010> endpoint contains methods for managing objects in a Report Server in either native or SharePoint integrated mode.</span></span> <span data-ttu-id="9b5df-112">這個端點的 WSDL 是透過 `ReportService2010.asmx?wsdl.` 來存取。</span><span class="sxs-lookup"><span data-stu-id="9b5df-112">The WSDL for this endpoint is accessed through `ReportService2010.asmx?wsdl.`</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9b5df-113"><xref:ReportService2005> 和 <xref:ReportService2006> 端點是在 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 中被取代。</span><span class="sxs-lookup"><span data-stu-id="9b5df-113">The <xref:ReportService2005> and <xref:ReportService2006> endpoints are deprecated in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="9b5df-114"><xref:ReportService2010> 端點包含這兩個端點的功能，並包含額外的管理功能。</span><span class="sxs-lookup"><span data-stu-id="9b5df-114">The <xref:ReportService2010> endpoint includes the functionalities of both endpoints and contains additional management features.</span></span>  
  
-   <span data-ttu-id="9b5df-115"><xref:ReportExecution2005> 端點可讓開發人員以程式設計方式處理及轉譯報表伺服器中的報表。</span><span class="sxs-lookup"><span data-stu-id="9b5df-115">The <xref:ReportExecution2005> endpoint allows developers to programmatically process and render reports in a Report Server.</span></span> <span data-ttu-id="9b5df-116">這個端點的 WSDL 是透過 `ReportExecution2005.asmx?wsdl` 來存取。</span><span class="sxs-lookup"><span data-stu-id="9b5df-116">The WSDL for this endpoint is accessed through `ReportExecution2005.asmx?wsdl`.</span></span>  
  
 <span data-ttu-id="9b5df-117">WSDL 可供支援 SOAP 和 Web 服務的開發工具組使用，例如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK。</span><span class="sxs-lookup"><span data-stu-id="9b5df-117">WSDL can be consumed by development kits that support SOAP and Web services, such as the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
 <span data-ttu-id="9b5df-118">下列範例示範 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 管理 WSDL 檔案的 URL 格式。</span><span class="sxs-lookup"><span data-stu-id="9b5df-118">The following example shows the format of the URL to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] management WSDL file:</span></span>  
  
```  
http://server/reportserver/ReportService2010.asmx?wsdl  
```  
  
 <span data-ttu-id="9b5df-119">下表將描述 URL 中的每個元素。</span><span class="sxs-lookup"><span data-stu-id="9b5df-119">The following table describes each element in the URL.</span></span>  
  
|<span data-ttu-id="9b5df-120">URL 元素</span><span class="sxs-lookup"><span data-stu-id="9b5df-120">URL element</span></span>|<span data-ttu-id="9b5df-121">描述</span><span class="sxs-lookup"><span data-stu-id="9b5df-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="9b5df-122">*伺服器*</span><span class="sxs-lookup"><span data-stu-id="9b5df-122">*server*</span></span>|<span data-ttu-id="9b5df-123">這是部署報表伺服器的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="9b5df-123">The name of the server on which the report server is deployed.</span></span>|  
|<span data-ttu-id="9b5df-124">*reportserver*</span><span class="sxs-lookup"><span data-stu-id="9b5df-124">*reportserver*</span></span>|<span data-ttu-id="9b5df-125">包含 XML Web 服務的資料夾。</span><span class="sxs-lookup"><span data-stu-id="9b5df-125">The name of the folder that contains the XML Web service.</span></span> <span data-ttu-id="9b5df-126">這是在安裝期間設定的。</span><span class="sxs-lookup"><span data-stu-id="9b5df-126">This is configured during setup.</span></span>|  
|<span data-ttu-id="9b5df-127">*\<endpoint name>.asmx*</span><span class="sxs-lookup"><span data-stu-id="9b5df-127">*\<endpoint name>.asmx*</span></span>|<span data-ttu-id="9b5df-128">Web 服務端點的名稱。</span><span class="sxs-lookup"><span data-stu-id="9b5df-128">The name of the web service endpoint.</span></span>|  
  
 <span data-ttu-id="9b5df-129">如需有關 WSDL 格式的詳細資訊，請參閱全球資訊網協會 (W3C) WSDL 規格，網址為 http://www.w3.org/TR/wsdl。</span><span class="sxs-lookup"><span data-stu-id="9b5df-129">For more information about the WSDL format, see the World Wide Web Consortium (W3C) WSDL specification at http://www.w3.org/TR/wsdl.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b5df-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b5df-130">See Also</span></span>  
 <span data-ttu-id="9b5df-131">[使用 Web 服務和 .NET Framework 建置應用程式](net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="9b5df-131">[Building Applications Using the Web Service and the .NET Framework](net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="9b5df-132">報表伺服器 Web 服務</span><span class="sxs-lookup"><span data-stu-id="9b5df-132">Report Server Web Service</span></span>](report-server-web-service.md)  
  
  
