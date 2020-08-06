---
title: 使用 Reporting Services SOAP 標頭 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- SOAP headers [Reporting Services]
- SOAP [Reporting Services], headers
- XML Web service [Reporting Services], SOAP
ms.assetid: 306d2c06-a25a-40f8-8a35-13dd32e8841e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f48be183398d4d441b5781c9f9467178c3011e32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702389"
---
# <a name="using-reporting-services-soap-headers"></a><span data-ttu-id="ae307-102">使用 Reporting Services SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="ae307-102">Using Reporting Services SOAP Headers</span></span>
  <span data-ttu-id="ae307-103">使用 SOAP 與 Web 服務方法通訊需要遵循標準格式。</span><span class="sxs-lookup"><span data-stu-id="ae307-103">Communication with a Web service method using SOAP follows a standard format.</span></span> <span data-ttu-id="ae307-104">這個格式的一部分是編碼於 XML 文件中的資料。</span><span class="sxs-lookup"><span data-stu-id="ae307-104">Part of this format is the data that is encoded in an XML document.</span></span> <span data-ttu-id="ae307-105">XML 文件是由根 **Envelope** 項目所組成，該項目則是由必要的 **Body** 項目和選擇性的 **Header** 項目組成。</span><span class="sxs-lookup"><span data-stu-id="ae307-105">The XML document consists of a root **Envelope** element, which in turn consists of a required **Body** element and an optional **Header** element.</span></span> <span data-ttu-id="ae307-106">**Body** 項目包含訊息特定的資料。</span><span class="sxs-lookup"><span data-stu-id="ae307-106">The **Body** element contains the data specific to the message.</span></span> <span data-ttu-id="ae307-107">選擇性的 **Header** 項目可能包含其他與特定訊息沒有直接關聯的資訊。</span><span class="sxs-lookup"><span data-stu-id="ae307-107">The optional **Header** element can contain additional information not directly related to the particular message.</span></span> <span data-ttu-id="ae307-108">**Header** 項目的每個子項目都稱為 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="ae307-108">Each child element of the **Header** element is called a SOAP header.</span></span>  
  
 <span data-ttu-id="ae307-109">雖然 SOAP 標頭可能會包含與訊息相關的資料，但通常是包含由 Web 伺服器基礎結構所處理的資訊。</span><span class="sxs-lookup"><span data-stu-id="ae307-109">Although the SOAP headers can contain data related to the message, they typically contain information processed by the Web server infrastructure.</span></span>  
  
 <span data-ttu-id="ae307-110">報表伺服器 Web 服務定義了多個用於 SOAP 標頭的類別：<xref:ReportService2005.BatchHeader>、<xref:ReportService2010.ItemNamespaceHeader>、<xref:ReportService2010.ServerInfoHeader>、<xref:ReportService2010.TrustedUserHeader> 和 <xref:ReportExecution2005.ExecutionHeader>。</span><span class="sxs-lookup"><span data-stu-id="ae307-110">The Report Server Web services define several classes for use in the SOAP header: <xref:ReportService2005.BatchHeader>, <xref:ReportService2010.ItemNamespaceHeader>, <xref:ReportService2010.ServerInfoHeader>, <xref:ReportService2010.TrustedUserHeader>, and <xref:ReportExecution2005.ExecutionHeader>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ae307-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="ae307-111">In This Section</span></span>  
  
|<span data-ttu-id="ae307-112">主題</span><span class="sxs-lookup"><span data-stu-id="ae307-112">Topic</span></span>|<span data-ttu-id="ae307-113">描述</span><span class="sxs-lookup"><span data-stu-id="ae307-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ae307-114">批次方法</span><span class="sxs-lookup"><span data-stu-id="ae307-114">Batching Methods</span></span>](batching-methods.md)|<span data-ttu-id="ae307-115">描述如何使用 <xref:ReportService2005.BatchHeader>，在單一交易中批次處理多項作業。</span><span class="sxs-lookup"><span data-stu-id="ae307-115">Describes how to batch multiple operations into a single transaction using <xref:ReportService2005.BatchHeader>.</span></span>|  
|[<span data-ttu-id="ae307-116">識別執行狀態</span><span class="sxs-lookup"><span data-stu-id="ae307-116">Identifying Execution State</span></span>](identifying-execution-state.md)|<span data-ttu-id="ae307-117">描述如何在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中，使用 **SessionHeader** 管理工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="ae307-117">Describes how to manage session state in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] using **SessionHeader**.</span></span>|  
|[<span data-ttu-id="ae307-118">設定 GetProperties 方法的項目命名空間</span><span class="sxs-lookup"><span data-stu-id="ae307-118">Setting the Item Namespace for the GetProperties Method</span></span>](setting-the-item-namespace-for-the-getproperties-method.md)|<span data-ttu-id="ae307-119">描述如何使用 <xref:ReportService2010.ReportingService2010.GetProperties%2A> 方法和 <xref:ReportService2010.ItemNamespaceHeader> SOAP 標頭，根據項目的路徑或識別碼來擷取屬性。</span><span class="sxs-lookup"><span data-stu-id="ae307-119">Describes how to retrieve properties based on either the path or the ID of an item by using the <xref:ReportService2010.ReportingService2010.GetProperties%2A> method and the <xref:ReportService2010.ItemNamespaceHeader> SOAP header.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ae307-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae307-120">See Also</span></span>  
 <span data-ttu-id="ae307-121">[使用 Web 服務和 .NET Framework 建置應用程式](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="ae307-121">[Building Applications Using the Web Service and the .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="ae307-122">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ae307-122">Technical Reference &#40;SSRS&#41;</span></span>](../technical-reference-ssrs.md)  
  
  
