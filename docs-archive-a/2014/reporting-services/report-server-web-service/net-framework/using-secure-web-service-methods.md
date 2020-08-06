---
title: 使用安全的 Web 服務方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], secure connections
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: 87329299-c2ea-4517-9148-d855726768a9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e88a164602f9bbe6ad42c3897285a484cac94466
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707054"
---
# <a name="using-secure-web-service-methods"></a><span data-ttu-id="626e8-102">使用安全的 Web 服務方法</span><span class="sxs-lookup"><span data-stu-id="626e8-102">Using Secure Web Service Methods</span></span>
  <span data-ttu-id="626e8-103">某些報表伺服器 Web 服務方法在叫用時，可能需要安全的連接。</span><span class="sxs-lookup"><span data-stu-id="626e8-103">Certain Report Server Web service methods may require a secure connection when you invoke them.</span></span> <span data-ttu-id="626e8-104">需要安全連接的方法是由 RSReportServer.config 檔案中的 `SecureConnectionLevel` 設定所決定。</span><span class="sxs-lookup"><span data-stu-id="626e8-104">The methods that require a secure connection are determined by the `SecureConnectionLevel` setting in the RSReportServer.config file.</span></span> <span data-ttu-id="626e8-105">設定值有效範圍為 0 及以上的整數值。</span><span class="sxs-lookup"><span data-stu-id="626e8-105">The value of the setting is an integer value with a valid range of 0 and higher.</span></span> <span data-ttu-id="626e8-106">下表描述這些值。</span><span class="sxs-lookup"><span data-stu-id="626e8-106">The following table describes these values.</span></span>  
  
|<span data-ttu-id="626e8-107">層級</span><span class="sxs-lookup"><span data-stu-id="626e8-107">Level</span></span>|<span data-ttu-id="626e8-108">描述</span><span class="sxs-lookup"><span data-stu-id="626e8-108">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="626e8-109">**0**</span><span class="sxs-lookup"><span data-stu-id="626e8-109">**0**</span></span>|<span data-ttu-id="626e8-110">不安全。</span><span class="sxs-lookup"><span data-stu-id="626e8-110">Not secure.</span></span> <span data-ttu-id="626e8-111">對 Reporting Services SOAP API 的呼叫不需要安全連接。</span><span class="sxs-lookup"><span data-stu-id="626e8-111">Calls made to the Reporting Services SOAP API do not require a secure connection.</span></span>|  
|<span data-ttu-id="626e8-112">大於 **0**</span><span class="sxs-lookup"><span data-stu-id="626e8-112">Greater than **0**</span></span>|<span data-ttu-id="626e8-113">安全。</span><span class="sxs-lookup"><span data-stu-id="626e8-113">Secure.</span></span> <span data-ttu-id="626e8-114">所有對 Reporting Services SOAP API 的呼叫都需要安全連接。</span><span class="sxs-lookup"><span data-stu-id="626e8-114">All calls made to the Reporting Services SOAP API require a secure connection.</span></span>|  
  
 <span data-ttu-id="626e8-115">您可以使用 Web 服務的 <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> 方法，根據報表伺服器目前的組態，傳回需要安全連接的 Web 服務方法清單。</span><span class="sxs-lookup"><span data-stu-id="626e8-115">You can use the <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> method of the Web service to return a list of Web service methods that require a secure connection according to the current configuration of the report server.</span></span> <span data-ttu-id="626e8-116">在 SSL 案例中，您應該評估 <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> 傳回的方法清單，並視要呼叫的方法而定，將 Web 服務的配置名稱變更為 "https" 或 "http"。</span><span class="sxs-lookup"><span data-stu-id="626e8-116">In an SSL scenario, you should evaluate the list of methods that are returned by <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> and change the scheme name of the Web service URI to "https" or "http" depending on the method being called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="626e8-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="626e8-117">See Also</span></span>  
 <span data-ttu-id="626e8-118">[使用 Web 服務和 .NET Framework 建置應用程式](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="626e8-118">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="626e8-119">報表伺服器 Web 服務</span><span class="sxs-lookup"><span data-stu-id="626e8-119">Report Server Web Service</span></span>](../report-server-web-service.md)  
  
  
