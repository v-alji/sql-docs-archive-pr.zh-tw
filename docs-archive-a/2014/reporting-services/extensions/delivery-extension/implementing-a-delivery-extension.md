---
title: 實作傳遞延伸模組 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery [Reporting Services]
- custom delivery extensions [Reporting Services]
- extensions [Reporting Services], delivery
- delivery extensions [Reporting Services]
ms.assetid: 600cd229-efcd-480e-8c95-3c3c39ff4e7a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af1e804e029dae77fb7836577aa8d4a45ad20109
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607292"
---
# <a name="implementing-a-delivery-extension"></a><span data-ttu-id="65e0e-102">實作傳遞延伸模組</span><span class="sxs-lookup"><span data-stu-id="65e0e-102">Implementing a Delivery Extension</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="65e0e-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 可讓使用者建立和發行報表，一旦建立和發行，就可以傳遞給各個位置。</span><span class="sxs-lookup"><span data-stu-id="65e0e-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] enables users to create and publish reports that, once created and published, can be delivered to various locations.</span></span> <span data-ttu-id="65e0e-104">除此之外，[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 包括數個傳遞延伸模組以及一個傳遞 API，可讓開發人員建立其他的傳遞延伸模組，以進一步擴充在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的傳遞功能。</span><span class="sxs-lookup"><span data-stu-id="65e0e-104">In addition, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] includes several delivery extensions and a delivery API that enable developers to create additional delivery extensions to further extend the functionality of delivery in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="65e0e-105">如需傳遞延伸模組的範例實作，請參閱 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (SQL Server Reporting Services 產品範例)。</span><span class="sxs-lookup"><span data-stu-id="65e0e-105">For a sample implementation of a delivery extension, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="65e0e-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="65e0e-106">In This Section</span></span>  
 <span data-ttu-id="65e0e-107">[傳遞延伸模組總覽] 傳遞-延伸模組-overview.md) </span><span class="sxs-lookup"><span data-stu-id="65e0e-107">[Delivery Extensions Overview]delivery-extensions-overview.md)</span></span>  
 <span data-ttu-id="65e0e-108">介紹如何為 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 撰寫自訂傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="65e0e-108">Introduces how to write a custom delivery extension for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="65e0e-109">準備實作傳遞延伸模組</span><span class="sxs-lookup"><span data-stu-id="65e0e-109">Preparing to Implement a Delivery Extension</span></span>](preparing-to-implement-a-delivery-extension.md)  
 <span data-ttu-id="65e0e-110">描述實作 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 傳遞延伸模組時可用的介面與類別，以及在實作之前要考慮的問題。</span><span class="sxs-lookup"><span data-stu-id="65e0e-110">Describes the interfaces and classes available when implementing an [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension, as well as issues to consider before implementation.</span></span>  
  
 [<span data-ttu-id="65e0e-111">建立傳遞延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="65e0e-111">Creating a Delivery Extension Library</span></span>](creating-a-delivery-extension-library.md)  
 <span data-ttu-id="65e0e-112">描述為 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 傳遞延伸模組指派命名空間，以及將傳遞延伸模組編譯成為程式庫 DLL。</span><span class="sxs-lookup"><span data-stu-id="65e0e-112">Describes assigning a namespace for your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension and compiling your delivery extension into a library DLL.</span></span>  
  
 [<span data-ttu-id="65e0e-113">實作傳遞延伸模組的 IDeliveryExtension 介面</span><span class="sxs-lookup"><span data-stu-id="65e0e-113">Implementing the IDeliveryExtension Interface for a Delivery Extension</span></span>](implementing-the-ideliveryextension-interface-for-a-delivery-extension.md)  
 <span data-ttu-id="65e0e-114">描述傳遞延伸模組的屬性，以及如何實作自己的傳遞延伸模組類別。</span><span class="sxs-lookup"><span data-stu-id="65e0e-114">Describes the attributes of a delivery extension, and how to implement your own delivery extension class.</span></span>  
  
 [<span data-ttu-id="65e0e-115">使用傳遞延伸模組的通知類別</span><span class="sxs-lookup"><span data-stu-id="65e0e-115">Using a Notification Class for a Delivery Extension</span></span>](using-a-notification-class-for-a-delivery-extension.md)  
 <span data-ttu-id="65e0e-116">描述 **Notification** 類別的屬性，以及如何在傳遞延伸模組實作中使用它。</span><span class="sxs-lookup"><span data-stu-id="65e0e-116">Describes the attributes of a **Notification** class and how to use it in your delivery extension implementation.</span></span>  
  
 [<span data-ttu-id="65e0e-117">使用傳遞延伸模組的設定類別</span><span class="sxs-lookup"><span data-stu-id="65e0e-117">Using the Setting Class for a Delivery Extension</span></span>](using-the-setting-class-for-a-delivery-extension.md)  
 <span data-ttu-id="65e0e-118">描述 **Setting** 類別的屬性，以及如何在傳遞延伸模組實作中使用它。</span><span class="sxs-lookup"><span data-stu-id="65e0e-118">Describes the attributes of a **Setting** class and how to use it in your delivery extension implementation.</span></span>  
  
 [<span data-ttu-id="65e0e-119">使用傳遞延伸模組的 IDeliveryReportServerInformation 介面</span><span class="sxs-lookup"><span data-stu-id="65e0e-119">Using the IDeliveryReportServerInformation Interface for a Delivery Extension</span></span>](using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md)  
 <span data-ttu-id="65e0e-120">描述 **IDeliveryReportServerInformation** 介面的屬性，以及如何在傳遞延伸模組實作中使用它。</span><span class="sxs-lookup"><span data-stu-id="65e0e-120">Describes the attributes of a **IDeliveryReportServerInformation** interface and how to use it in your delivery extension implementation.</span></span>  
  
 [<span data-ttu-id="65e0e-121">使用傳遞延伸模組的報表類別</span><span class="sxs-lookup"><span data-stu-id="65e0e-121">Using the Report Class for a Delivery Extension</span></span>](using-the-report-class-for-a-delivery-extension.md)  
 <span data-ttu-id="65e0e-122">描述 **Report** 類別的屬性，以及如何在傳遞延伸模組實作中使用它。</span><span class="sxs-lookup"><span data-stu-id="65e0e-122">Describes the attributes of a **Report** class and how to use it in your delivery extension implementation.</span></span>  
  
 [<span data-ttu-id="65e0e-123">使用傳遞延伸模組的 RenderedOutputFile 類別</span><span class="sxs-lookup"><span data-stu-id="65e0e-123">Using the RenderedOutputFile Class for a Delivery Extension</span></span>](using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
 <span data-ttu-id="65e0e-124">描述 **RenderedOutputFile** 類別的屬性，以及如何在傳遞延伸模組實作中使用它。</span><span class="sxs-lookup"><span data-stu-id="65e0e-124">Describes the attributes of a **RenderedOutputFile** class and how to use it in your delivery extension implementation.</span></span>  
  
 [<span data-ttu-id="65e0e-125">實作傳遞延伸模組的 ISubscriptionBaseUIUserControl 介面</span><span class="sxs-lookup"><span data-stu-id="65e0e-125">Implementing the ISubscriptionBaseUIUserControl Interface for a Delivery Extension</span></span>](implementing-the-isubscriptionbaseuiusercontrol-interface.md)  
 <span data-ttu-id="65e0e-126">描述傳遞延伸模組使用者控制項的屬性，以及如何為訂閱實作自己的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="65e0e-126">Describes the attributes of a delivery extension user control and how to implement your own user interface for a subscription.</span></span>  
  
 [<span data-ttu-id="65e0e-127">部署傳遞延伸模組</span><span class="sxs-lookup"><span data-stu-id="65e0e-127">Deploying a Delivery Extension</span></span>](deploying-a-delivery-extension.md)  
 <span data-ttu-id="65e0e-128">描述如何部署您的傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="65e0e-128">Describes how to deploy your delivery extension.</span></span>  
  
 [<span data-ttu-id="65e0e-129">偵錯傳遞延伸模組程式碼</span><span class="sxs-lookup"><span data-stu-id="65e0e-129">Debugging Delivery Extension Code</span></span>](debugging-delivery-extension-code.md)  
 <span data-ttu-id="65e0e-130">描述如何偵錯您的傳遞延伸模組中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="65e0e-130">Describes how to debug code in your delivery extension.</span></span>  
  
 [<span data-ttu-id="65e0e-131">移除傳遞延伸模組</span><span class="sxs-lookup"><span data-stu-id="65e0e-131">Removing a Delivery Extension</span></span>](removing-a-delivery-extension.md)  
 <span data-ttu-id="65e0e-132">描述如何從報表伺服器移除傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="65e0e-132">Describes how to remove a delivery extension from a report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65e0e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65e0e-133">See Also</span></span>  
 <span data-ttu-id="65e0e-134">[Reporting Services 延伸模組](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="65e0e-134">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 [<span data-ttu-id="65e0e-135">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="65e0e-135">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
