---
title: 提供 Web 服務方法引數 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- methods [Reporting Services], arguments
- XML Web service [Reporting Services], methods
ms.assetid: f7b9ca05-fc4c-4b30-8e5d-172dd0f4a832
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3ef5188934628589751fe92d1839da0efb265766
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707050"
---
# <a name="supplying-web-service-method-arguments"></a><span data-ttu-id="34201-102">提供 Web 服務方法引數</span><span class="sxs-lookup"><span data-stu-id="34201-102">Supplying Web Service Method Arguments</span></span>
  <span data-ttu-id="34201-103">報表伺服器 Web 服務方法會透過 HTTP 使用 SOAP 在指定的 URL 傳送要求給服務。</span><span class="sxs-lookup"><span data-stu-id="34201-103">A Report Server Web service method sends a request to the service at a given URL using SOAP over HTTP.</span></span> <span data-ttu-id="34201-104">服務會接收要求、處理要求，然後傳回回應。</span><span class="sxs-lookup"><span data-stu-id="34201-104">The service receives the request, processes it, and then returns a response.</span></span> <span data-ttu-id="34201-105">這些要求和回應是 XML 文件的形式。</span><span class="sxs-lookup"><span data-stu-id="34201-105">These requests and responses are in the form of XML documents.</span></span>  
  
## <a name="optional-parameters"></a><span data-ttu-id="34201-106">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="34201-106">Optional Parameters</span></span>  
 <span data-ttu-id="34201-107">在某些情況下，Web 服務方法可以有選擇性的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="34201-107">In some cases, a Web service method can have optional input parameters.</span></span> <span data-ttu-id="34201-108">即使 Web 服務方法的輸入參數是選擇性的，仍然必須包括它，並將參數值設定為 `null` ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 中的 `Nothing`)。</span><span class="sxs-lookup"><span data-stu-id="34201-108">Even if an input parameter for a Web service method is optional, you must still include it and set the parameter value to `null` (`Nothing` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span></span> <span data-ttu-id="34201-109">將參數值設定為 `null`，會將 SOAP 要求中該參數的元素值設定為 `null`。</span><span class="sxs-lookup"><span data-stu-id="34201-109">Setting a parameter value to `null` sets the element value for that parameter in the SOAP request to `null`.</span></span>  
  
 <span data-ttu-id="34201-110">下列範例會使用 <xref:ReportService2010.ReportingService2010.CreateFolder%2A> 方法在 Sales 資料夾中建立名為 Product Sales 的新資料夾。</span><span class="sxs-lookup"><span data-stu-id="34201-110">The following example uses the <xref:ReportService2010.ReportingService2010.CreateFolder%2A> method to create a new folder named Product Sales in the Sales folder.</span></span> <span data-ttu-id="34201-111">透過為資料夾屬性提供 `null` 值，就不會為資料夾提供使用者特定屬性：</span><span class="sxs-lookup"><span data-stu-id="34201-111">By supplying a `null` value for the folder properties, no user-specific properties are supplied for the folder:</span></span>  
  
```  
// C#  
rs.CreateFolder("Product Sales", "/Sales", null);  
```  
  
## <a name="complex-data-types"></a><span data-ttu-id="34201-112">複雜的資料類型</span><span class="sxs-lookup"><span data-stu-id="34201-112">Complex Data Types</span></span>  
 <span data-ttu-id="34201-113">報表伺服器 Web 服務的核心類別是 <xref:ReportService2010.ReportingService2010>，您使用它來叫用 SOAP 作業或是 Proxy 類別的 Web 方法。</span><span class="sxs-lookup"><span data-stu-id="34201-113">The core class of the Report Server Web service is <xref:ReportService2010.ReportingService2010>, which you use to invoke the SOAP operations or Web methods of the proxy class.</span></span> <span data-ttu-id="34201-114">若要支援此類別及其方法，[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 包括使用者定義、複雜的資料類型，這些資料類型是 Web 服務方法的輸入與輸出參數特有的。</span><span class="sxs-lookup"><span data-stu-id="34201-114">To support this class and its methods, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] includes user-defined, complex data types that are specific to the input and output parameters of the Web service methods.</span></span> <span data-ttu-id="34201-115">這些複雜的資料類型是產生的 proxy 類別的一部分，您可以在環境中進行開發時使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="34201-115">These complex data types are part of the generated proxy class, which you can use when developing in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] environment.</span></span>  
  
 <span data-ttu-id="34201-116">當您產生 Proxy 類別時，在 WSDL 檔案中定義的複雜資料類型是由 Proxy 類別所代表，這包括對應至複雜資料類型的各種 SOAP 元素。</span><span class="sxs-lookup"><span data-stu-id="34201-116">When you generate a proxy class, the complex data types that are defined in the WSDL file are represented by the classes of the proxy, which include properties that correspond to the various SOAP elements of the complex data types.</span></span> <span data-ttu-id="34201-117">這些資料類型的順序會變成可在程式碼中列舉的物件陣列。</span><span class="sxs-lookup"><span data-stu-id="34201-117">Sequences of these data types become arrays of objects that you can enumerate through in your code.</span></span> <span data-ttu-id="34201-118">這會列舉直接與 SOAP 訊息中傳送的 XML 結構搭配使用的需求。</span><span class="sxs-lookup"><span data-stu-id="34201-118">This eliminates the need to work directly with the XML structures sent in SOAP messages.</span></span> <span data-ttu-id="34201-119">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 會為您處理翻譯。</span><span class="sxs-lookup"><span data-stu-id="34201-119">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] handles that translation for you.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34201-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34201-120">See Also</span></span>  
 <span data-ttu-id="34201-121">[使用 Web 服務和 .NET Framework 建置應用程式](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="34201-121">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="34201-122">[報表伺服器 Web 服務](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="34201-122">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="34201-123">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="34201-123">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
