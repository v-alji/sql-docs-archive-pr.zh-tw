---
title: Reporting Services 中的例外狀況處理簡介 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], exception handling
- errors [Reporting Services]
- exceptions [Reporting Services]
- Report Server Web service, exception handling
- XML Web service [Reporting Services], exception handling
ms.assetid: 54381870-ce67-482b-aa83-6a838cdbf9b9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 091b1f40d293515617e369b750a5f18dfe12951b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699319"
---
# <a name="introducing-exception-handling-in-reporting-services"></a><span data-ttu-id="c1426-102">Reporting Services 中的例外狀況處理簡介</span><span class="sxs-lookup"><span data-stu-id="c1426-102">Introducing Exception Handling in Reporting Services</span></span>
  <span data-ttu-id="c1426-103">如果您的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 應用程式將要求傳送到報表伺服器 Web 服務，但是此服務無法處理，則服務會將 SOAP 例外狀況傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="c1426-103">If your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] application sends a request to the Report Server Web service that the service is unable to process, the service returns a SOAP exception to the client.</span></span> <span data-ttu-id="c1426-104">報表伺服器 Web 服務擲回的處理例外狀況是所開發應用程式的重要部分之一，因為當錯誤發生時，可以傳回有用的資訊給使用者。</span><span class="sxs-lookup"><span data-stu-id="c1426-104">Handling exceptions thrown by the Report Server Web service is an important part of the applications that you develop because you can return useful information to users when errors occur.</span></span>  
  
 <span data-ttu-id="c1426-105">本節包含的特定資訊，是有關處理例外狀況以防止使用者的無效輸入，並將有意義的錯誤資訊傳回給使用者。</span><span class="sxs-lookup"><span data-stu-id="c1426-105">This section contains specific information about handling exceptions, preventing user input that is not valid, and returning meaningful error information to users.</span></span> <span data-ttu-id="c1426-106">如需例外狀況處理的一般資訊，請參閱 SDK 檔中的「處理和擲回例外狀況」 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c1426-106">For general information about exception handling, see "Handling and Throwing Exceptions" in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1426-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="c1426-107">In This Section</span></span>  
  
|<span data-ttu-id="c1426-108">主題</span><span class="sxs-lookup"><span data-stu-id="c1426-108">Topic</span></span>|<span data-ttu-id="c1426-109">描述</span><span class="sxs-lookup"><span data-stu-id="c1426-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c1426-110">處理 Reporting Services 中的例外狀況</span><span class="sxs-lookup"><span data-stu-id="c1426-110">Handling Exceptions in Reporting Services</span></span>](handling-exceptions-in-reporting-services.md)|<span data-ttu-id="c1426-111">提供 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的例外狀況概觀以及從 Web 服務傳回錯誤的 SOAP 角色。</span><span class="sxs-lookup"><span data-stu-id="c1426-111">Provides an overview of exceptions in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and the role of SOAP in returning errors from a Web service.</span></span>|  
|[<span data-ttu-id="c1426-112">Reporting Services 例外處理的最佳作法</span><span class="sxs-lookup"><span data-stu-id="c1426-112">Best Practices for Reporting Services Exception Handling</span></span>](best-practices/best-practices-for-reporting-services-exception-handling.md)|<span data-ttu-id="c1426-113">提供如何處理 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的例外狀況之建議。</span><span class="sxs-lookup"><span data-stu-id="c1426-113">Provides recommendations on how to handle exceptions in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="c1426-114">Reporting Services SoapException 類別</span><span class="sxs-lookup"><span data-stu-id="c1426-114">Reporting Services SoapException Class</span></span>](soapexception-class/reporting-services-soapexception-class.md)|<span data-ttu-id="c1426-115">描述 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的 **SoapException** 類別。</span><span class="sxs-lookup"><span data-stu-id="c1426-115">Describes the **SoapException** class in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c1426-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1426-116">See Also</span></span>  
 [<span data-ttu-id="c1426-117">使用 Web 服務和 .NET Framework 建置應用程式</span><span class="sxs-lookup"><span data-stu-id="c1426-117">Building Applications Using the Web Service and the .NET Framework</span></span>](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
