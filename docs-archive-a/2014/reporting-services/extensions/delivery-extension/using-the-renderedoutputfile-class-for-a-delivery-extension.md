---
title: 使用傳遞延伸模組的 RenderedOutputFile 類別 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- RenderedOutputFile class
- data streams [Reporting Services]
- delivery extensions [Reporting Services], data streams
ms.assetid: 8b591801-42d5-49fa-b710-bf7e6917accf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1dcbf250a367326e5cad528384e533a9ac9d945b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607277"
---
# <a name="using-the-renderedoutputfile-class-for-a-delivery-extension"></a><span data-ttu-id="6bf2d-102">使用傳遞延伸模組的 RenderedOutputFile 類別</span><span class="sxs-lookup"><span data-stu-id="6bf2d-102">Using the RenderedOutputFile Class for a Delivery Extension</span></span>
  <span data-ttu-id="6bf2d-103"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 類別代表資料流以及與資料流的相關聯屬性的資訊。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-103">The <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> class represents a data stream and information about the data stream's associated properties.</span></span> <span data-ttu-id="6bf2d-104"><xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 類別的 **Data** 屬性，會用來代表作為 **Stream** 物件的轉譯報表或是報表資源。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-104">The **Data** property of the <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> class is used to represent a rendered report or report resource as a **Stream** object.</span></span>  
  
 <span data-ttu-id="6bf2d-105">**Report** 物件的 <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> 方法會傳回一或多個 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 物件的陣列，這些物件會構成單一的轉譯報表。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-105">The <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> method of the **Report** object returns an array of one or more <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> objects that together constitute a single rendered report.</span></span> <span data-ttu-id="6bf2d-106">第一個 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 物件是轉譯報表。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-106">The first <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object is the rendered report.</span></span> <span data-ttu-id="6bf2d-107">任何其他 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 物件都是必須連同報表資料一起傳遞的資源 (例如，HTML 檔案與相關聯的影像)。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-107">Any other <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> objects are resources that must be delivered along with the report data (for example, an HTML file and associated images).</span></span> <span data-ttu-id="6bf2d-108">屬於單一資料流轉譯延伸模組 (IMAGE、PDF、MHTML 和 EXCEL) 的轉譯延伸模組只會傳回陣列中的一個 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 物件。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-108">Rendering extensions that are single-stream rendering extensions (IMAGE, PDF, MHTML, and EXCEL) return only one <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> object in the array.</span></span>  
  
 <span data-ttu-id="6bf2d-109">如需如何使用 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 類別的範例，請參閱 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (SQL Server Reporting Services 產品範例)。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-109">For an example of how to use the <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> class, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bf2d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bf2d-110">See Also</span></span>  
 <span data-ttu-id="6bf2d-111">[實作傳遞延伸模組](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="6bf2d-111">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="6bf2d-112">Reporting Services 延伸模組程式庫</span><span class="sxs-lookup"><span data-stu-id="6bf2d-112">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
