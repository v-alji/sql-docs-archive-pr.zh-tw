---
title: 準備實作傳遞延伸模組 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- interfaces [Reporting Services]
- delivery extensions [Reporting Services], implementing
ms.assetid: aee1608d-374f-4ad3-bc23-fe07fdaa52b7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bbf98286e6ed35542d8117b4b87b5ff3425def69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607286"
---
# <a name="preparing-to-implement-a-delivery-extension"></a><span data-ttu-id="59354-102">準備實作傳遞延伸模組</span><span class="sxs-lookup"><span data-stu-id="59354-102">Preparing to Implement a Delivery Extension</span></span>
  <span data-ttu-id="59354-103">在您實作 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 傳遞延伸模組之前，應該定義要實作的介面。</span><span class="sxs-lookup"><span data-stu-id="59354-103">Before you implement your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension, you should define the interfaces to implement.</span></span> <span data-ttu-id="59354-104">您需要先決定將如何使用傳遞延伸模組、傳遞延伸模組將需要的設定，以及您將需要實作的特定功能以傳遞報表通知。</span><span class="sxs-lookup"><span data-stu-id="59354-104">You first need to decide how your delivery extension will be used, what settings your delivery extension will require, and the specific functionality you will need to implement in order to deliver report notifications.</span></span>  
  
 <span data-ttu-id="59354-105">每個 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 傳遞延伸模組必須提供下列功能：</span><span class="sxs-lookup"><span data-stu-id="59354-105">Each [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension must provide the following functionality:</span></span>  
  
-   <span data-ttu-id="59354-106">代表延伸模組與當地語系化延伸模組名稱的 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 介面實作。</span><span class="sxs-lookup"><span data-stu-id="59354-106">An <xref:Microsoft.ReportingServices.Interfaces.IExtension> interface implementation that represents the extension and a localized extension name.</span></span>  
  
-   <span data-ttu-id="59354-107"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 實作，建立可用以傳遞報表通知給一般使用者的傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="59354-107">An <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> implementation that creates a delivery extension that can be used to deliver report notifications to end users.</span></span>  
  
-   <span data-ttu-id="59354-108">處理訂閱之特定使用者資料的功能。</span><span class="sxs-lookup"><span data-stu-id="59354-108">The ability to process specific user data for a subscription.</span></span>  
  
 <span data-ttu-id="59354-109">每個傳遞延伸模組都可以增強以包括下列功能：</span><span class="sxs-lookup"><span data-stu-id="59354-109">Each delivery extension can be enhanced to include the following functionality:</span></span>  
  
-   <span data-ttu-id="59354-110">[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 使用者控制項實作，允許使用者使用報表管理員建立使用傳遞延伸模組的報表訂閱。</span><span class="sxs-lookup"><span data-stu-id="59354-110">An [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] user control implementation that enables end users to use Report Manager to create report subscriptions that use the delivery extension.</span></span>  
  
 <span data-ttu-id="59354-111">下表描述傳遞延伸模組之可用的介面與類別。</span><span class="sxs-lookup"><span data-stu-id="59354-111">The following table describes the available interfaces and classes for delivery extensions.</span></span>  
  
|<span data-ttu-id="59354-112">介面或類別</span><span class="sxs-lookup"><span data-stu-id="59354-112">Interface or class</span></span>|<span data-ttu-id="59354-113">描述</span><span class="sxs-lookup"><span data-stu-id="59354-113">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="59354-114"><xref:Microsoft.ReportingServices.Interfaces.IExtension> 介面</span><span class="sxs-lookup"><span data-stu-id="59354-114"><xref:Microsoft.ReportingServices.Interfaces.IExtension> Interface</span></span>|<span data-ttu-id="59354-115">代表 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的擴充功能。</span><span class="sxs-lookup"><span data-stu-id="59354-115">Represents an extension in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
|<span data-ttu-id="59354-116"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 介面</span><span class="sxs-lookup"><span data-stu-id="59354-116"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> Interface</span></span>|<span data-ttu-id="59354-117">代表 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="59354-117">Represents a delivery extension in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
|<span data-ttu-id="59354-118"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> 介面</span><span class="sxs-lookup"><span data-stu-id="59354-118"><xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> Interface</span></span>|<span data-ttu-id="59354-119">包含傳遞延伸模組所需的報表伺服器的資訊 (例如，可用轉譯延伸模組的清單)。</span><span class="sxs-lookup"><span data-stu-id="59354-119">Contains information about the report server that is required by delivery extensions (for example, a list of the available rendering extensions).</span></span>|  
|<span data-ttu-id="59354-120"><xref:Microsoft.ReportingServices.Interfaces.Setting> 類別</span><span class="sxs-lookup"><span data-stu-id="59354-120"><xref:Microsoft.ReportingServices.Interfaces.Setting> Class</span></span>|<span data-ttu-id="59354-121">表示延伸模組的設定。</span><span class="sxs-lookup"><span data-stu-id="59354-121">Represents a setting for an extension.</span></span>|  
|<span data-ttu-id="59354-122"><xref:Microsoft.ReportingServices.Interfaces.Notification> 類別</span><span class="sxs-lookup"><span data-stu-id="59354-122"><xref:Microsoft.ReportingServices.Interfaces.Notification> Class</span></span>|<span data-ttu-id="59354-123">包含傳遞延伸模組用以傳遞報表的訂閱資訊。</span><span class="sxs-lookup"><span data-stu-id="59354-123">Contains subscription information that delivery extensions use to deliver reports.</span></span>|  
|<span data-ttu-id="59354-124"><xref:Microsoft.ReportingServices.Interfaces.Report> 類別</span><span class="sxs-lookup"><span data-stu-id="59354-124"><xref:Microsoft.ReportingServices.Interfaces.Report> Class</span></span>|<span data-ttu-id="59354-125">代表報表的特定資訊與方法，允許傳遞延伸模組傳遞報表給使用者。</span><span class="sxs-lookup"><span data-stu-id="59354-125">Represents report-specific information and methods that enable delivery extensions to deliver reports to users.</span></span>|  
|<span data-ttu-id="59354-126"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 類別</span><span class="sxs-lookup"><span data-stu-id="59354-126"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> Class</span></span>|<span data-ttu-id="59354-127">表示轉譯延伸模組的輸出。</span><span class="sxs-lookup"><span data-stu-id="59354-127">Represents the output from a rendering extension.</span></span> <span data-ttu-id="59354-128"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 物件包含傳遞延伸模組所需的相關聯檔案名稱與類型資訊，這是為了處理轉譯延伸模組所傳回的資料流。</span><span class="sxs-lookup"><span data-stu-id="59354-128">A <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object contains the associated file name and type information that is required by the delivery extension in order to process the stream returned by the rendering extension.</span></span>|  
|<span data-ttu-id="59354-129"><xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> 介面</span><span class="sxs-lookup"><span data-stu-id="59354-129"><xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> Interface</span></span>|<span data-ttu-id="59354-130">表示從報表管理員中的使用者，擷取傳遞延伸模組特定訂閱資訊之使用者控制項 (例如，電子郵件地址或是檔案共用的路徑)。</span><span class="sxs-lookup"><span data-stu-id="59354-130">A user control that represents the means to retrieve delivery extension-specific subscription information from the user in Report Manager (for example, an e-mail address or the path to a file share).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59354-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59354-131">See Also</span></span>  
 <span data-ttu-id="59354-132">[Reporting Services 延伸模組](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="59354-132">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="59354-133">[實作傳遞延伸模組](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="59354-133">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="59354-134">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="59354-134">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
