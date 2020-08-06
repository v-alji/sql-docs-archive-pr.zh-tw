---
title: Web 服務驗證 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], authentication
- XML Web service [Reporting Services], authentication
- Report Server Web service, authentication
ms.assetid: 852b4947-a090-4e54-8555-5a503945ceab
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0c7836d6eba8c6ab3f0a8e705ebb79c7ed73eb17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707045"
---
# <a name="web-service-authentication"></a><span data-ttu-id="48475-102">Web 服務驗證</span><span class="sxs-lookup"><span data-stu-id="48475-102">Web Service Authentication</span></span>
  <span data-ttu-id="48475-103">您可以使用 Windows 驗證或是基本驗證，以驗證對報表伺服器 Web 服務的呼叫。</span><span class="sxs-lookup"><span data-stu-id="48475-103">You can use either Windows Authentication or Basic authentication to authenticate the calls made to the Report Server Web service.</span></span> <span data-ttu-id="48475-104">任何對報表伺服器提出 SOAP 要求的用戶端，都必須實作其中一個支援的驗證通訊協定之用戶端部分。</span><span class="sxs-lookup"><span data-stu-id="48475-104">Any client that makes SOAP requests to the report server must implement the client portion of one of the supported authentication protocols.</span></span> <span data-ttu-id="48475-105">如果您使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ，則可以使用 managed 程式碼 HTTP 類別來執行驗證。</span><span class="sxs-lookup"><span data-stu-id="48475-105">If you are using the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], you can use the managed code HTTP classes to implement authentication.</span></span> <span data-ttu-id="48475-106">使用這些 API 使得連同 SOAP 要求一起傳送驗證資訊變得更容易。</span><span class="sxs-lookup"><span data-stu-id="48475-106">Using these APIs makes it easy to send authentication information along with the SOAP requests.</span></span>  
  
 <span data-ttu-id="48475-107">如果在呼叫報表伺服器 Web 服務之前沒有適當的認證，呼叫會失敗。</span><span class="sxs-lookup"><span data-stu-id="48475-107">If you do not have appropriate credentials before you make a call to the Report Server Web service, the call fails.</span></span> <span data-ttu-id="48475-108">在執行階段時，您可以藉由在呼叫其方法之前，設定表示 Web 服務之用戶端物件的 **Credentials** 屬性，將認證傳遞至 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="48475-108">At run time, you can pass credentials to the Web service by setting the **Credentials** property of the client-side object that represents the Web service before you call its methods.</span></span>  
  
 <span data-ttu-id="48475-109">下列小節包含使用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 傳送認證的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="48475-109">The following sections contain example code that sends credentials using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="windows-authentication"></a><span data-ttu-id="48475-110">Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="48475-110">Windows Authentication</span></span>  
 <span data-ttu-id="48475-111">下列程式碼將 Windows 認證傳遞到 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="48475-111">The following code passes Windows credentials to the Web service.</span></span>  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
```  
  
```csharp  
ReportingService rs = new ReportingService();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
```  
  
## <a name="basic-authentication"></a><span data-ttu-id="48475-112">基本驗證</span><span class="sxs-lookup"><span data-stu-id="48475-112">Basic Authentication</span></span>  
 <span data-ttu-id="48475-113">下列程式碼將基本認證傳遞到 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="48475-113">The following code passes Basic credentials to the Web service.</span></span>  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = New System.Net.NetworkCredential("username", "password", "domain")  
```  
  
```csharp  
ReportingService service = new ReportingService();  
service.Credentials = new System.Net.NetworkCredential("username", "password", "domain");  
```  
  
 <span data-ttu-id="48475-114">在您呼叫報表伺服器 Web 服務的任何方法之前，必須先設定認證。</span><span class="sxs-lookup"><span data-stu-id="48475-114">The credentials must be set before you call any of the methods of the Report Server Web service.</span></span> <span data-ttu-id="48475-115">如果您未設定認證，會收到錯誤碼「HTTP 401 錯誤：拒絕存取」。</span><span class="sxs-lookup"><span data-stu-id="48475-115">If you do not set the credentials, you receive the error code an HTTP 401 Error: Access Denied.</span></span> <span data-ttu-id="48475-116">您必須在使用它之前先驗證服務，但是在您設定認證之後，不需要再次設定它們，因為您會繼續使用相同的服務變數 (例如，*rs*)。</span><span class="sxs-lookup"><span data-stu-id="48475-116">You must authenticate the service before you use it, but after you have set the credentials, you do not need to set them again as long as you continue to use the same service variable (such as *rs*).</span></span>  
  
## <a name="custom-authentication"></a><span data-ttu-id="48475-117">自訂驗證</span><span class="sxs-lookup"><span data-stu-id="48475-117">Custom Authentication</span></span>  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="48475-118">包括程式設計 API，以提供開發人員設計和開發自訂驗證延伸模組的機會，又稱為安全性延伸模組。</span><span class="sxs-lookup"><span data-stu-id="48475-118">includes a programming API that provides developers with the opportunity to design and develop custom authentication extensions, known as security extensions.</span></span> <span data-ttu-id="48475-119">如需詳細資訊，請參閱＜ [Implementing a Security Extension](../../extensions/security-extension/implementing-a-security-extension.md)＞。</span><span class="sxs-lookup"><span data-stu-id="48475-119">For more information, see [Implementing a Security Extension](../../extensions/security-extension/implementing-a-security-extension.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48475-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48475-120">See Also</span></span>  
 <span data-ttu-id="48475-121">[使用 Web 服務和 .NET Framework 建置應用程式](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="48475-121">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="48475-122">報表伺服器 Web 服務</span><span class="sxs-lookup"><span data-stu-id="48475-122">Report Server Web Service</span></span>](../report-server-web-service.md)  
  
  
