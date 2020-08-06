---
title: 實作傳遞延伸模組的 IDeliveryExtension 介面 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], attributes
- delivery extensions [Reporting Services], class creation
- IDeliveryExtension interface
ms.assetid: ab0344db-510b-403f-8dbf-b9831553765d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a0f9ab0767a09016d4f4bc1158988965bfc13b27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607290"
---
# <a name="implementing-the-ideliveryextension-interface-for-a-delivery-extension"></a><span data-ttu-id="6b4f7-102">實作傳遞延伸模組的 IDeliveryExtension 介面</span><span class="sxs-lookup"><span data-stu-id="6b4f7-102">Implementing the IDeliveryExtension Interface for a Delivery Extension</span></span>
  <span data-ttu-id="6b4f7-103">您的傳遞延伸模組類別是用以根據通知的內容，將報告通知傳遞給使用者。</span><span class="sxs-lookup"><span data-stu-id="6b4f7-103">Your delivery extension class is used to deliver report notifications to users based on the contents of the notifications.</span></span> <span data-ttu-id="6b4f7-104">傳遞延伸模組類別也提供基礎結構，以驗證傳遞給傳遞延伸模組的使用者設定。</span><span class="sxs-lookup"><span data-stu-id="6b4f7-104">The delivery extension class also provides infrastructure for validating user settings that are passed to the delivery extension.</span></span> <span data-ttu-id="6b4f7-105">此外，您的傳遞延伸模組類別應該包含特定的屬性，讓用戶端可用以取得有關延伸模組的名稱、延伸模組支援的設定，以及可供傳遞延伸模組使用的轉譯格式。</span><span class="sxs-lookup"><span data-stu-id="6b4f7-105">In addition, your delivery extension class should contain specific properties that clients can use to gain information about the name of the extension, the settings that the extension supports, and the rendering formats that are available to the delivery extension.</span></span>  
  
 <span data-ttu-id="6b4f7-106">![IDeliveryExtension 介面程序](../../media/bk-ext-02.gif "IDeliveryExtension 介面程序")</span><span class="sxs-lookup"><span data-stu-id="6b4f7-106">![IDeliveryExtension interface process](../../media/bk-ext-02.gif "IDeliveryExtension interface process")</span></span>  
<span data-ttu-id="6b4f7-107">IDeliveryExtension 介面允許使用者資料的驗證以及供用戶端了解必要的傳遞設定</span><span class="sxs-lookup"><span data-stu-id="6b4f7-107">The IDeliveryExtension interface allows validation of user data as well as for clients to learn about the required delivery settings</span></span>  
  
 <span data-ttu-id="6b4f7-108">若要建立傳遞延伸模組類別，請實作 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 與 <xref:Microsoft.ReportingServices.Interfaces.IExtension>。</span><span class="sxs-lookup"><span data-stu-id="6b4f7-108">To create a delivery extension class, implement <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> and <xref:Microsoft.ReportingServices.Interfaces.IExtension>.</span></span> <span data-ttu-id="6b4f7-109">**IDeliveryExtension** 介面允許傳遞延伸模組使用 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> 方法來傳遞報表通知，並使用 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ValidateUserData%2A> 方法來驗證內送延伸模組設定。</span><span class="sxs-lookup"><span data-stu-id="6b4f7-109">The **IDeliveryExtension** interface enables your delivery extension to deliver report notifications using the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> method and to validate incoming extension settings using the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ValidateUserData%2A> method.</span></span> <span data-ttu-id="6b4f7-110">**IExtension** 介面允許您的傳遞延伸模組實作當地語系化延伸模組名稱，並處理儲存在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 設定檔中的延伸模組特定設定資訊。</span><span class="sxs-lookup"><span data-stu-id="6b4f7-110">The **IExtension** interface enables your delivery extension to implement a localized extension name and to process extension-specific configuration information stored in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] configuration file.</span></span> <span data-ttu-id="6b4f7-111">透過實作 **IExtension**，您的傳遞延伸模組包含 <xref:Microsoft.ReportingServices.Interfaces.Extension.LocalizedName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="6b4f7-111">By implementing **IExtension**, your delivery extension contains the <xref:Microsoft.ReportingServices.Interfaces.Extension.LocalizedName%2A> property.</span></span> <span data-ttu-id="6b4f7-112">強烈建議 [!INCLUDE[ssRS](../../../includes/ssrs.md)] 傳遞延伸模組支援 **LocalizedName** 屬性，這樣使用者就會在使用者介面中遇到延伸模組的熟悉名稱，例如報表管理員。</span><span class="sxs-lookup"><span data-stu-id="6b4f7-112">It is strongly recommended that [!INCLUDE[ssRS](../../../includes/ssrs.md)] delivery extensions support the **LocalizedName** property, so that users encounter a familiar name for the extension in a user interface, such as Report Manager.</span></span>  
  
 <span data-ttu-id="6b4f7-113">您的傳遞延伸模組也必須實作 **IDeliveryExtension** 介面的 **ExtensionSettings** 屬性。</span><span class="sxs-lookup"><span data-stu-id="6b4f7-113">Your delivery extension must also implement the **ExtensionSettings** property of the **IDeliveryExtension** interface.</span></span> <span data-ttu-id="6b4f7-114">報表伺服器會使用 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> 屬性傳回的值，來評估傳遞延伸模組所需的設定。</span><span class="sxs-lookup"><span data-stu-id="6b4f7-114">The report server uses the value returned by the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> property to evaluate the settings that a delivery extension requires.</span></span> <span data-ttu-id="6b4f7-115">與傳遞延伸模組互動的用戶端，會使用報表伺服器 Web 服務的 <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> 方法，來為傳遞延伸模組傳回設定清單。</span><span class="sxs-lookup"><span data-stu-id="6b4f7-115">Clients that interact with delivery extensions use the <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> method of the Report Server Web service to return a list of settings for the delivery extension.</span></span>  
  
 <span data-ttu-id="6b4f7-116">您也可以使用傳遞延伸模組類別，來擷取和處理儲存在 RSReportServer.config 檔案中的自訂組態資料。</span><span class="sxs-lookup"><span data-stu-id="6b4f7-116">You can also use your delivery extension class to retrieve and process custom configuration data stored in the RSReportServer.config file.</span></span> <span data-ttu-id="6b4f7-117">如需有關處理自訂組態資料的詳細資訊，請參閱＜<xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A>＞方法。</span><span class="sxs-lookup"><span data-stu-id="6b4f7-117">For more information about processing custom configuration data, see the <xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="6b4f7-118">如需範例 **IDeliveryExtension** 類別實作，請參閱 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (SQL Server Reporting Services 產品範例)。</span><span class="sxs-lookup"><span data-stu-id="6b4f7-118">For a sample **IDeliveryExtension** class implementation, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b4f7-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b4f7-119">See Also</span></span>  
 <span data-ttu-id="6b4f7-120">[實作傳遞延伸模組](../delivery-extension/implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="6b4f7-120">[Implementing a Delivery Extension](../delivery-extension/implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="6b4f7-121">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="6b4f7-121">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
