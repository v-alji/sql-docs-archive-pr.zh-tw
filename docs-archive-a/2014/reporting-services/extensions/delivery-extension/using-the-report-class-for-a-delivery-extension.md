---
title: 使用傳遞延伸模組的報表類別 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], report information
- Report class
ms.assetid: 1145ac63-eafd-452a-82af-16f85b1676dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a3f750c2383253636db255cbe9f1ce0ee676a9d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607274"
---
# <a name="using-the-report-class-for-a-delivery-extension"></a><span data-ttu-id="e155c-102">使用傳遞延伸模組的報表類別</span><span class="sxs-lookup"><span data-stu-id="e155c-102">Using the Report Class for a Delivery Extension</span></span>
  <span data-ttu-id="e155c-103"><xref:Microsoft.ReportingServices.Interfaces.Report> 類別代表報表伺服器資料庫中的報表。</span><span class="sxs-lookup"><span data-stu-id="e155c-103">The <xref:Microsoft.ReportingServices.Interfaces.Report> class represents a report in the report server database.</span></span> <span data-ttu-id="e155c-104">任何訂閱都與特定報表相關聯。</span><span class="sxs-lookup"><span data-stu-id="e155c-104">Any subscription is associated with a specific report.</span></span> <span data-ttu-id="e155c-105">報表包含在通知中。</span><span class="sxs-lookup"><span data-stu-id="e155c-105">The report is contained in the notification.</span></span> <span data-ttu-id="e155c-106">您的傳遞延伸模組可以使用屬於通知一部分的 <xref:Microsoft.ReportingServices.Interfaces.Report> 物件來轉譯報表。</span><span class="sxs-lookup"><span data-stu-id="e155c-106">Your delivery extension can use the <xref:Microsoft.ReportingServices.Interfaces.Report> object that is part of the notification to render the report.</span></span> <span data-ttu-id="e155c-107"><xref:Microsoft.ReportingServices.Interfaces.Report> 物件也包含報表特定屬性，例如在報表伺服器上的報表 URL 以及報表名稱。</span><span class="sxs-lookup"><span data-stu-id="e155c-107">The <xref:Microsoft.ReportingServices.Interfaces.Report> object also contains report-specific properties, such as the URL to the report on the report server and the name of the report.</span></span> <span data-ttu-id="e155c-108">這些屬性全部都可以做為傳遞提供者的一部分。</span><span class="sxs-lookup"><span data-stu-id="e155c-108">These properties can all be used as part of your delivery provider.</span></span>  
  
 <span data-ttu-id="e155c-109"><xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> 類別的 <xref:Microsoft.ReportingServices.Interfaces.Report>方法可用以轉譯報表。</span><span class="sxs-lookup"><span data-stu-id="e155c-109">The <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> method of the <xref:Microsoft.ReportingServices.Interfaces.Report> class can be used to render a report.</span></span> <span data-ttu-id="e155c-110"><xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> 方法會傳回一或多個 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 物件的陣列，全部加起來即可構成單一轉譯報表。</span><span class="sxs-lookup"><span data-stu-id="e155c-110">The <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> method returns an array of one or more <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> objects that together comprise a single rendered report.</span></span> <span data-ttu-id="e155c-111">第一個 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 物件是轉譯報表。</span><span class="sxs-lookup"><span data-stu-id="e155c-111">The first <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object is the rendered report.</span></span> <span data-ttu-id="e155c-112">任何其他 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 物件都是必須連同報表資料一起傳遞的資源 (例如，HTML 檔案與相關聯的影像)。</span><span class="sxs-lookup"><span data-stu-id="e155c-112">Any other <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> objects are resources that must be delivered along with the report data (for example, an HTML file and associated images).</span></span> <span data-ttu-id="e155c-113">是單一資料流轉譯延伸模組的轉譯延伸模組 (IMAGE、PDF、MHTML 和 Excel) 只會在陣列中傳回一個 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 物件。</span><span class="sxs-lookup"><span data-stu-id="e155c-113">Rendering extensions that are single-stream rendering extensions (IMAGE, PDF, MHTML, and Excel) return only one <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object in the array.</span></span>  
  
 <span data-ttu-id="e155c-114">包含報表資料流的 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 物件，可以包括在傳遞中。</span><span class="sxs-lookup"><span data-stu-id="e155c-114">The <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object, which contains the report stream, can be included as part of a delivery.</span></span>  
  
 <span data-ttu-id="e155c-115">如需如何使用 <xref:Microsoft.ReportingServices.Interfaces.Report> 類別的範例，請參閱 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (SQL Server Reporting Services 產品範例)</span><span class="sxs-lookup"><span data-stu-id="e155c-115">For an example of how to use the <xref:Microsoft.ReportingServices.Interfaces.Report> class, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e155c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e155c-116">See Also</span></span>  
 <span data-ttu-id="e155c-117">[實作傳遞延伸模組](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="e155c-117">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 <span data-ttu-id="e155c-118">[Reporting Services 延伸模組程式庫](../reporting-services-extension-library.md) </span><span class="sxs-lookup"><span data-stu-id="e155c-118">[Reporting Services Extension Library](../reporting-services-extension-library.md) </span></span>  
 [<span data-ttu-id="e155c-119">使用傳遞延伸模組的 RenderedOutputFile 類別</span><span class="sxs-lookup"><span data-stu-id="e155c-119">Using the RenderedOutputFile Class for a Delivery Extension</span></span>](using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
  
  
