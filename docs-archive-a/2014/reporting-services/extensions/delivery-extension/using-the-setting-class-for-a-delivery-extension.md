---
title: 使用傳遞延伸模組的設定類別 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], settings
- Setting class
ms.assetid: 50746639-da7c-46a5-ac7b-e87dd6b91880
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 594cf28391ae4523e1a95ad79ee5b1280ff72218
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687529"
---
# <a name="using-the-setting-class-for-a-delivery-extension"></a><span data-ttu-id="416f5-102">使用傳遞延伸模組的設定類別</span><span class="sxs-lookup"><span data-stu-id="416f5-102">Using the Setting Class for a Delivery Extension</span></span>
  <span data-ttu-id="416f5-103"><xref:Microsoft.ReportingServices.Interfaces.Setting> 類別是位在 <xref:Microsoft.ReportingServices.Interfaces> 命名空間中，並且代表有關傳遞延伸模組的延伸模組設定。</span><span class="sxs-lookup"><span data-stu-id="416f5-103">The <xref:Microsoft.ReportingServices.Interfaces.Setting> class is located in the <xref:Microsoft.ReportingServices.Interfaces> namespace and represents information about extension settings for a delivery extension.</span></span> <span data-ttu-id="416f5-104"><xref:Microsoft.ReportingServices.Interfaces.Setting> 類別提供基礎結構，以儲存有關為了使傳遞延伸模組正常運作所需的設定。</span><span class="sxs-lookup"><span data-stu-id="416f5-104">The <xref:Microsoft.ReportingServices.Interfaces.Setting> class provides infrastructure for storing information about the settings that are required in order for a delivery extension to function properly.</span></span> <span data-ttu-id="416f5-105">例如，「報表伺服器電子郵件」傳遞，使用者需要提供電子郵件傳遞特有的設定，例如收件者地址、寄件者地址、電子郵件的主旨等等。</span><span class="sxs-lookup"><span data-stu-id="416f5-105">For example, in Report Server E-Mail delivery, a user is required to supply settings specific to e-mail delivery, such as the recipient's address, the sender's address, the subject line of the e-mail, and more.</span></span> <span data-ttu-id="416f5-106">毋庸置疑地，您的自訂傳遞提供者將要求使用者提供特定的設定，傳遞延伸模組才能傳遞通知和報表。</span><span class="sxs-lookup"><span data-stu-id="416f5-106">Undoubtedly, your custom delivery providers will require the user to supply specific settings in order for the delivery extension to deliver notifications and reports.</span></span>  
  
 <span data-ttu-id="416f5-107">當實作 <xref:Microsoft.ReportingServices.Interfaces.Setting> 介面的 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> 屬性時，會使用 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 類別。</span><span class="sxs-lookup"><span data-stu-id="416f5-107">The <xref:Microsoft.ReportingServices.Interfaces.Setting> class is used when implementing the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> property of the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> interface.</span></span> <span data-ttu-id="416f5-108"><xref:Microsoft.ReportingServices.Interfaces.Setting> 類別也可在建立訂閱或通知時，用來處理使用者提供的延伸模組設定資料。</span><span class="sxs-lookup"><span data-stu-id="416f5-108">The <xref:Microsoft.ReportingServices.Interfaces.Setting> class is also used for processing the extension setting data that is supplied by a user when a subscription or notification is created.</span></span>  
  
 <span data-ttu-id="416f5-109">如需如何使用 <xref:Microsoft.ReportingServices.Interfaces.Setting> 類別的範例，請參閱 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (SQL Server Reporting Services 產品範例)。</span><span class="sxs-lookup"><span data-stu-id="416f5-109">For an example of how to use the <xref:Microsoft.ReportingServices.Interfaces.Setting> class, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="416f5-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="416f5-110">See Also</span></span>  
 <span data-ttu-id="416f5-111">[實作傳遞延伸模組](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="416f5-111">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="416f5-112">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="416f5-112">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
