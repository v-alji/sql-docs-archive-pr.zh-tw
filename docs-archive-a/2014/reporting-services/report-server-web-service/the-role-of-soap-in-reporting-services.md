---
title: Reporting Services 中的 SOAP 角色 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- SOAP [Reporting Services], role in Reporting Services
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: f229c3ef-f2ca-448f-98f1-b8df350b9992
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 05445eb1c95c5761595944867b6d0c20a6f1a412
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700813"
---
# <a name="the-role-of-soap-in-reporting-services"></a><span data-ttu-id="11d24-102">The Role of SOAP in Reporting Services</span><span class="sxs-lookup"><span data-stu-id="11d24-102">The Role of SOAP in Reporting Services</span></span>
  <span data-ttu-id="11d24-103">報表伺服器 Web 服務透過網路使用簡易物件存取通訊協定 (SOAP) 訊息，傳送以文字為基礎的命令。</span><span class="sxs-lookup"><span data-stu-id="11d24-103">The Report Server Web service uses Simple Object Access Protocol (SOAP) messaging to send text-based commands over a network.</span></span> <span data-ttu-id="11d24-104">這些命令使用 XML 文字的格式，以 HTTP 透過全球資訊網來傳送文字。</span><span class="sxs-lookup"><span data-stu-id="11d24-104">These commands take the form of XML text that is sent over the World Wide Web using HTTP.</span></span> <span data-ttu-id="11d24-105">透過使用 SOAP 做為其通訊協定，報表伺服器 Web 服務允許應用程式和元件使用開放且廣為接受的基礎結構，來與報表伺服器交換資料。</span><span class="sxs-lookup"><span data-stu-id="11d24-105">By using SOAP as its communication protocol, the Report Server Web service allows applications and components to exchange data with the report server using an open and widely accepted infrastructure.</span></span> <span data-ttu-id="11d24-106">SOAP 標準是定義在 www.w3.org/TR/SOAP。</span><span class="sxs-lookup"><span data-stu-id="11d24-106">The SOAP standard is defined at www.w3.org/TR/SOAP.</span></span>  
  
 <span data-ttu-id="11d24-107">任何用戶端應用程式都可以當做 SOAP 用戶端使用，只要它是 SOAP 感知並且可傳送 SOAP 要求。</span><span class="sxs-lookup"><span data-stu-id="11d24-107">Any client application can act as a SOAP client as long as it is SOAP-aware and can send SOAP requests.</span></span> <span data-ttu-id="11d24-108">報表管理員就是這類的 SOAP 用戶端。</span><span class="sxs-lookup"><span data-stu-id="11d24-108">Report Manager is one such SOAP client.</span></span> <span data-ttu-id="11d24-109">它提供儲存所有報表與報表相關內容之報表伺服器資料庫的介面。</span><span class="sxs-lookup"><span data-stu-id="11d24-109">It provides an interface to the report server database in which all reports and report-related content is stored.</span></span> <span data-ttu-id="11d24-110">使用者可以使用應用程式，來瀏覽和管理報表伺服器命名空間中的報表與資料夾。</span><span class="sxs-lookup"><span data-stu-id="11d24-110">End users can use the application to browse through and manage reports and folders in the report server namespace.</span></span> <span data-ttu-id="11d24-111">報表管理員是建立在報表伺服器 Web 服務基礎結構上。</span><span class="sxs-lookup"><span data-stu-id="11d24-111">Report Manager is built on the Report Server Web service infrastructure.</span></span>  
  
 <span data-ttu-id="11d24-112">報表伺服器可做為 SOAP 伺服器，這是可從 SOAP 用戶端接受要求並建立適當回應的 SOAP 感知服務。</span><span class="sxs-lookup"><span data-stu-id="11d24-112">A report server acts as a SOAP server, a SOAP-aware service that can accept requests from SOAP clients and create appropriate responses.</span></span> <span data-ttu-id="11d24-113">伺服器會處理要求並將編碼的回應傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="11d24-113">The server handles the requests and sends encoded responses back to the client.</span></span>  
  
 <span data-ttu-id="11d24-114">在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的 SOAP 訊息有許多不同的形式，端視用戶端所提出的要求類型而定。</span><span class="sxs-lookup"><span data-stu-id="11d24-114">SOAP messages in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] take many different forms, depending on the type of request made by the client.</span></span> <span data-ttu-id="11d24-115">下列範例代表簡單的 SOAP 用戶端要求，以移除報表伺服器資料庫中的項目。</span><span class="sxs-lookup"><span data-stu-id="11d24-115">The following example represents a simple SOAP client request to remove an item from the report server database.</span></span>  
  
```  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <soap:Body>  
        <DeleteItem xmlns="https://www.microsoft.com/sql/ReportingServer">  
            <item>/Samples/Report1</item>  
        </DeleteItem>  
    </soap:Body>  
</soap:Envelope>  
```  
  
 <span data-ttu-id="11d24-116">SOAP 本身需要將訊息放入 `Envelope` 元素中，並且在 `Body` 元素中含有大量的訊息。</span><span class="sxs-lookup"><span data-stu-id="11d24-116">The SOAP itself requires that messages be put into an `Envelope` element, with the bulk of the message inside a `Body` element.</span></span> <span data-ttu-id="11d24-117">在此範例中，本文包含對 <xref:ReportService2010.ReportingService2010.DeleteItem%2A> 方法的呼叫，這需要代表要刪除的項目路徑之字串參數。</span><span class="sxs-lookup"><span data-stu-id="11d24-117">In this example, the body contains a call to the <xref:ReportService2010.ReportingService2010.DeleteItem%2A> method, which takes a string parameter representing the path of the item to delete.</span></span> <span data-ttu-id="11d24-118">您可以建立 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 用戶端 proxy 類別，將所有 SOAP 作業封裝成方法。</span><span class="sxs-lookup"><span data-stu-id="11d24-118">You can create a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] client proxy class that encapsulates all SOAP operations into methods.</span></span> <span data-ttu-id="11d24-119">下列 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 方法代表稍早指定的 SOAP 範例。</span><span class="sxs-lookup"><span data-stu-id="11d24-119">The following [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] method represents the SOAP example given earlier.</span></span>  
  
```  
public void DeleteItem(string item);  
```  
  
 <span data-ttu-id="11d24-120">伺服器的回應可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="11d24-120">The response from the server might look like the following:</span></span>  
  
```  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <soap:Body>  
        <DeleteItemResponse xmlns="https://www.microsoft.com/sql/ReportingServer" />  
    </soap:Body>  
</soap:Envelope>  
```  
  
 <span data-ttu-id="11d24-121"><xref:ReportService2010.ReportingService2010.DeleteItem%2A> 方法沒有傳回值，所以會傳回空的回應。</span><span class="sxs-lookup"><span data-stu-id="11d24-121">The <xref:ReportService2010.ReportingService2010.DeleteItem%2A> method has no return value, so an empty response is returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11d24-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11d24-122">See Also</span></span>  
 <span data-ttu-id="11d24-123">[存取 SOAP API](accessing-the-soap-api.md) </span><span class="sxs-lookup"><span data-stu-id="11d24-123">[Accessing the SOAP API](accessing-the-soap-api.md) </span></span>  
 <span data-ttu-id="11d24-124">[報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="11d24-124">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="11d24-125">[Reporting Services 報表伺服器](../reporting-services-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="11d24-125">[Reporting Services Report Server](../reporting-services-report-server.md) </span></span>  
 [<span data-ttu-id="11d24-126">報表伺服器 Web 服務</span><span class="sxs-lookup"><span data-stu-id="11d24-126">Report Server Web Service</span></span>](report-server-web-service.md)  
  
  
