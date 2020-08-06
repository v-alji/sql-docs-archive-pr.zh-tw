---
title: 呼叫 Web 服務方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- Web service [Reporting Services], calls
- calling Web service
- Report Server Web service, SOAP
- XML Web service [Reporting Services], calls
- Report Server Web service, calls
- XML Web service [Reporting Services], SOAP
- SOAP [Reporting Services], calls
ms.assetid: f6f0c6e3-8bb5-4c44-9d19-1872edc72746
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 87f1485b4e3c0ed064e42bb3b411fece96eba8d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688545"
---
# <a name="calling-web-service-methods"></a><span data-ttu-id="f3c3d-102">呼叫 Web 服務方法</span><span class="sxs-lookup"><span data-stu-id="f3c3d-102">Calling Web Service Methods</span></span>
  <span data-ttu-id="f3c3d-103">當您使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] proxy 類別來呼叫 Web 服務作業時，您可以使用該類別的方法來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="f3c3d-103">When you use a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] proxy class to call Web service operations, you do so by using the methods of that class.</span></span> <span data-ttu-id="f3c3d-104">這些方法會像在 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 類別庫中類別的任何其他方法一樣回應。</span><span class="sxs-lookup"><span data-stu-id="f3c3d-104">These methods respond like any other method of a class in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] class library.</span></span> <span data-ttu-id="f3c3d-105">所有的 Web 服務方法都有公用存取權，而且會要求您提供適當數目的引數與引數類型。</span><span class="sxs-lookup"><span data-stu-id="f3c3d-105">All Web service methods have public access and require you to supply the appropriate number of arguments and argument types.</span></span> <span data-ttu-id="f3c3d-106">在專案中建立 Proxy 類別的執行個體之後，可以呼叫方法來透過報表伺服器執行報表作業。</span><span class="sxs-lookup"><span data-stu-id="f3c3d-106">After you have created an instance of the proxy class in your project, you can call the methods to perform reporting operations via the report server.</span></span> <span data-ttu-id="f3c3d-107">下列 C# 程式碼範例說明 <xref:ReportService2010.ReportingService2010> Proxy 類別的 <xref:ReportService2010.ReportingService2010.ListChildren%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f3c3d-107">The following C# code illustrates the use of the <xref:ReportService2010.ReportingService2010.ListChildren%2A> method of the <xref:ReportService2010.ReportingService2010> proxy class.</span></span> <span data-ttu-id="f3c3d-108">此程式碼是用以遞迴呼叫傳回 <xref:ReportService2010.CatalogItem> 物件陣列的 Web 服務，這些物件包含報表伺服器資料庫中所有項目的清單：</span><span class="sxs-lookup"><span data-stu-id="f3c3d-108">The code is used to make a recursive call to the Web service that returns an array of <xref:ReportService2010.CatalogItem> objects that contains a list of all items in the report server database:</span></span>  
  
```vb  
Dim rs As New ReportingService2010()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
Dim items As CatalogItem() = rs.ListChildren("/", True)  
```  
  
```csharp  
ReportingService2010 rs = new ReportingService2010();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
CatalogItem[] items = rs.ListChildren("/", true);  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3c3d-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3c3d-109">See Also</span></span>  
 <span data-ttu-id="f3c3d-110">[使用 Web 服務和 .NET Framework 建置應用程式](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="f3c3d-110">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="f3c3d-111">[報表伺服器 Web 服務](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="f3c3d-111">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="f3c3d-112">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f3c3d-112">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
