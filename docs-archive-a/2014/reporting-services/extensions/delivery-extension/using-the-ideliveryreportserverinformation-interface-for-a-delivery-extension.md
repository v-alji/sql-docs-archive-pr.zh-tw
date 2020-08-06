---
title: 使用傳遞延伸模組的 IDeliveryReportServerInformation 介面 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- IDeliveryReportServerInformation interface
- delivery extensions [Reporting Services], retrieving report server information
ms.assetid: adbce647-18f3-470c-8114-42f8bcc95dc2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 52e137d1a866305ec6435a4940fe98448bce5778
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607278"
---
# <a name="using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension"></a><span data-ttu-id="718ec-102">使用傳遞延伸模組的 IDeliveryReportServerInformation 介面</span><span class="sxs-lookup"><span data-stu-id="718ec-102">Using the IDeliveryReportServerInformation Interface for a Delivery Extension</span></span>
  <span data-ttu-id="718ec-103"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> 介面會公開您可用以擷取有關報表伺服器資訊的一些屬性。</span><span class="sxs-lookup"><span data-stu-id="718ec-103">The <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> interface exposes several properties that you can use to retrieve information about a report server.</span></span> <span data-ttu-id="718ec-104">您可以使用此資訊來傳遞通知和報表。</span><span class="sxs-lookup"><span data-stu-id="718ec-104">You can use this information to deliver notifications and reports.</span></span> <span data-ttu-id="718ec-105">當實作傳遞延伸模組類別時，會實作 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> 介面所需的 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 屬性。</span><span class="sxs-lookup"><span data-stu-id="718ec-105">When implementing your delivery extension class, you implement the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> property as required by the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> interface.</span></span> <span data-ttu-id="718ec-106"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> 屬性會傳回實作 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> 介面的物件。</span><span class="sxs-lookup"><span data-stu-id="718ec-106">The <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> property returns an object that implements the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> interface.</span></span> <span data-ttu-id="718ec-107">從這個物件，您可以取得報表伺服器目前支援的轉譯延伸模組清單。</span><span class="sxs-lookup"><span data-stu-id="718ec-107">From this object you can get a list of rendering extensions currently supported by the report server.</span></span>  
  
 <span data-ttu-id="718ec-108">下列 `for` 迴圈可用來將報表伺服器上目前可用的轉譯延伸模組清單儲存在**ArrayList**物件中。</span><span class="sxs-lookup"><span data-stu-id="718ec-108">The following `for` loop could be used to store a list of rendering extensions currently available on the report server in an **ArrayList** object.</span></span>  
  
```vb  
Dim renderFormats As New ArrayList()  
Dim e As Microsoft.ReportingServices.Interfaces.Extension  
For Each e In  ReportServerInformation.RenderingExtension  
   If e.Visible Then  
      renderFormats.Add(e.Name)  
   End If  
Next e  
```  
  
```csharp  
ArrayList renderFormats = new ArrayList();  
foreach (Microsoft.ReportingServices.Interfaces.Extension e in ReportServerInformation.RenderingExtension)  
{   
   if (e.Visible)  
   {  
      renderFormats.Add(e.Name);  
   }  
}  
```  
  
 <span data-ttu-id="718ec-109">如需 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> 介面的詳細資訊，請參閱[使用傳遞延伸模組的 IDeliveryReportServerInformation 介面](using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="718ec-109">For more information about the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> interface, see [Using the IDeliveryReportServerInformation Interface for a Delivery Extension](using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="718ec-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="718ec-110">See Also</span></span>  
 <xref:Microsoft.ReportingServices.Interfaces>   
 <span data-ttu-id="718ec-111">[執行傳遞延伸模組](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="718ec-111">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="718ec-112">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="718ec-112">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
