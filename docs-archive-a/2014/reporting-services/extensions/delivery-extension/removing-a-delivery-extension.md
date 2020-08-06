---
title: 移除傳遞延伸模組 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- removing delivery extensions
- deleting delivery extensions
- delivery extensions [Reporting Services], removing
ms.assetid: dcb7caf2-d19a-4bc5-afb3-2b61ad11cac5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7c4320f46b5013b0fa2accbc81792748c2d9f384
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607284"
---
# <a name="removing-a-delivery-extension"></a><span data-ttu-id="7947f-102">移除傳遞延伸模組</span><span class="sxs-lookup"><span data-stu-id="7947f-102">Removing a Delivery Extension</span></span>
  <span data-ttu-id="7947f-103">若要移除 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 傳遞延伸模組，請從設定檔直接移除傳遞延伸模組的 **Extension** 項目。</span><span class="sxs-lookup"><span data-stu-id="7947f-103">To remove a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension, simply remove the **Extension** element for your delivery extension from the configuration file.</span></span> <span data-ttu-id="7947f-104">移除組態資訊之後，傳遞延伸模組就無法再用於報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="7947f-104">After the configuration information is removed, the delivery extension is no longer available to the report server.</span></span>  
  
 <span data-ttu-id="7947f-105">一旦從設定檔移除傳遞延伸模組的對應 **Extension** 項目，就不需要在報表伺服器中註冊。</span><span class="sxs-lookup"><span data-stu-id="7947f-105">Once a delivery extension's corresponding **Extension** element is removed from the configuration file, it is no longer registered with the report server.</span></span> <span data-ttu-id="7947f-106">報表伺服器會從傳遞延伸模組的清單移除項目，並停用任何使用該傳遞延伸模組的訂閱。</span><span class="sxs-lookup"><span data-stu-id="7947f-106">The report server removes the entry from the list of delivery extensions and deactivates any subscriptions which use that delivery extension.</span></span> <span data-ttu-id="7947f-107">當移除傳遞延伸模組時，使用者就不能再選取它做為通知的方法。</span><span class="sxs-lookup"><span data-stu-id="7947f-107">When a delivery extension is removed, users are no longer able to select it as a method of notification.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7947f-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7947f-108">See Also</span></span>  
 <span data-ttu-id="7947f-109">[實作傳遞延伸模組](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="7947f-109">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="7947f-110">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="7947f-110">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
