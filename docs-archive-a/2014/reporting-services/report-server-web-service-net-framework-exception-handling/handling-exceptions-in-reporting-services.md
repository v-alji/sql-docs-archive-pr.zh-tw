---
title: 處理 Reporting Services 中的例外狀況 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], exceptions
- .NET Framework [Reporting Services]
- exceptions [Reporting Services], about exception handling
- SoapException object
ms.assetid: 1a443432-2db5-48c5-bc29-433b4688082f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1d887853b475f7b4d673d7b04343ae9bc71644d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703834"
---
# <a name="handling-exceptions-in-reporting-services"></a><span data-ttu-id="b5d9c-102">處理 Reporting Services 中的例外狀況</span><span class="sxs-lookup"><span data-stu-id="b5d9c-102">Handling Exceptions in Reporting Services</span></span>
  <span data-ttu-id="b5d9c-103">無法完成 Reporting Services SOAP API 用戶端要求時，報表伺服器會傳回錯誤，而非呼叫的預期結果。</span><span class="sxs-lookup"><span data-stu-id="b5d9c-103">When a Reporting Services SOAP API client request cannot be completed, the report server returns an error rather than the expected results of the call.</span></span> <span data-ttu-id="b5d9c-104">無法完成呼叫時，則會以 SOAP **Fault** XML 項目傳回報表伺服器 Web 服務的錯誤。</span><span class="sxs-lookup"><span data-stu-id="b5d9c-104">When a call cannot complete, an error for the Report Server Web service is returned as a SOAP **Fault** XML element.</span></span> <span data-ttu-id="b5d9c-105">該錯誤的關鍵描述項目為 **detail** 項目，此項目會包含報表伺服器提供的所有錯誤資訊以及任何其他 Web 服務錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="b5d9c-105">The key descriptive element of the fault is the **detail** element, which includes all of the error information provided by the report server as well as any additional Web service error information.</span></span> <span data-ttu-id="b5d9c-106">報表伺服器錯誤碼是 **detail** 項目中的主要資訊。</span><span class="sxs-lookup"><span data-stu-id="b5d9c-106">The key information in the **detail** element is the report server error code.</span></span> <span data-ttu-id="b5d9c-107">您可以根據訊息與錯誤碼，決定要在應用程式中採取的下一個適當動作。</span><span class="sxs-lookup"><span data-stu-id="b5d9c-107">Based on the message and error code, you can determine the next appropriate action to take in your applications.</span></span> <span data-ttu-id="b5d9c-108">如需有關 SOAP 錯誤的詳細資訊，請參閱全球資訊網協會 (W3C) 網站，網址為 http://www.w3.org/TR/SOAP。</span><span class="sxs-lookup"><span data-stu-id="b5d9c-108">For more information about SOAP faults, see the World Wide Web Consortium (W3C) Web site at http://www.w3.org/TR/SOAP.</span></span>  
  
## <a name="soap-faults-and-the-net-framework"></a><span data-ttu-id="b5d9c-109">SOAP 錯誤與 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b5d9c-109">SOAP Faults and the .NET Framework</span></span>  
 <span data-ttu-id="b5d9c-110">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 中，如果對 Web 服務的用戶端要求中發生錯誤，報表伺服器就會擲回 **SoapException** 物件，向呼叫 Web 服務的用戶端程式碼傳遞該錯誤。</span><span class="sxs-lookup"><span data-stu-id="b5d9c-110">In the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], if an error occurs in a client request to the Web service, the report server communicates the error to the client code that calls the Web service by throwing a **SoapException** object.</span></span> <span data-ttu-id="b5d9c-111">**SoapException** 會包裝 SOAP 錯誤中包含的資訊。</span><span class="sxs-lookup"><span data-stu-id="b5d9c-111">The **SoapException** wraps the information contained in a SOAP fault.</span></span> <span data-ttu-id="b5d9c-112">**SoapException** 的 **Detail** 屬性會與 SOAP 錯誤中的 **detail** 項目對應。</span><span class="sxs-lookup"><span data-stu-id="b5d9c-112">The **Detail** property of the **SoapException** maps to the **detail** element in the SOAP fault.</span></span> <span data-ttu-id="b5d9c-113">應用程式應該使用 try/catch 區塊來捕捉 **SoapException** 物件，並使用 **SoapException** 的 **Detail** 屬性來採取適當的動作。</span><span class="sxs-lookup"><span data-stu-id="b5d9c-113">Applications should catch the **SoapException** object with a try/catch block and use the **Detail** property of the **SoapException** to take appropriate action.</span></span> <span data-ttu-id="b5d9c-114">如需 **SoapException** 類別以及 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中 **Detail** 屬性的詳細資訊，請參閱 [Reporting Services SoapException 類別](soapexception-class/reporting-services-soapexception-class.md)。</span><span class="sxs-lookup"><span data-stu-id="b5d9c-114">For more information about the **SoapException** class and the **Detail** property in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Reporting Services SoapException Class](soapexception-class/reporting-services-soapexception-class.md).</span></span> <span data-ttu-id="b5d9c-115">如需 **SoapException** 類別的詳細資訊，請參閱 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 文件。</span><span class="sxs-lookup"><span data-stu-id="b5d9c-115">For more information about the **SoapException** class, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5d9c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5d9c-116">See Also</span></span>  
 <span data-ttu-id="b5d9c-117">[Detail 屬性](soapexception-class/detail-property.md) </span><span class="sxs-lookup"><span data-stu-id="b5d9c-117">[Detail Property](soapexception-class/detail-property.md) </span></span>  
 <span data-ttu-id="b5d9c-118">[Reporting Services 中的例外狀況處理簡介](introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="b5d9c-118">[Introducing Exception Handling in Reporting Services](introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="b5d9c-119">Reporting Services SoapException 類別</span><span class="sxs-lookup"><span data-stu-id="b5d9c-119">Reporting Services SoapException Class</span></span>](soapexception-class/reporting-services-soapexception-class.md)  
  
  
