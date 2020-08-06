---
title: 轉譯及執行方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- rendered reports [Reporting Services]
- reports [Reporting Services], execution options
- methods [Reporting Services], execution options
- methods [Reporting Services], rendering
ms.assetid: 12626aad-f0be-4653-87d0-60eb3a3fff78
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0bc793e9a18e993989563fd3526ff12272f775c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704858"
---
# <a name="rendering-and-execution-methods"></a><span data-ttu-id="80f4a-102">轉譯及執行方法</span><span class="sxs-lookup"><span data-stu-id="80f4a-102">Rendering and Execution Methods</span></span>
  <span data-ttu-id="80f4a-103">您可以使用這些方法來管理項目執行和快取，以及報表轉譯。</span><span class="sxs-lookup"><span data-stu-id="80f4a-103">You can use these methods to manage item execution and caching, and report rendering.</span></span>  
  
|<span data-ttu-id="80f4a-104">方法</span><span class="sxs-lookup"><span data-stu-id="80f4a-104">Method</span></span>|<span data-ttu-id="80f4a-105">動作</span><span class="sxs-lookup"><span data-stu-id="80f4a-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.FlushCache%2A>|<span data-ttu-id="80f4a-106">使項目的快取失效。</span><span class="sxs-lookup"><span data-stu-id="80f4a-106">Invalidates the cache for an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetCacheOptions%2A>|<span data-ttu-id="80f4a-107">傳回項目的快取組態，以及描述項目快取複本到期時間的設定。</span><span class="sxs-lookup"><span data-stu-id="80f4a-107">Returns the cache configuration for an item and the settings that describe when the cached copy of the item expires.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetExecutionOptions%2A>|<span data-ttu-id="80f4a-108">傳回個別項目的執行選項及相關聯的設定。</span><span class="sxs-lookup"><span data-stu-id="80f4a-108">Returns the execution option and associated settings for an individual item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListExecutionSettings%2A>|<span data-ttu-id="80f4a-109">傳回支援的執行設定清單。</span><span class="sxs-lookup"><span data-stu-id="80f4a-109">Returns a list of supported execution settings.</span></span>|  
|<xref:ReportExecution2005.ReportExecutionService.Render%2A>|<span data-ttu-id="80f4a-110">處理指定的報表，並依照指定的格式轉譯該報表。</span><span class="sxs-lookup"><span data-stu-id="80f4a-110">Processes the specified report and renders it in a specified format.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetCacheOptions%2A>|<span data-ttu-id="80f4a-111">設定要快取的項目，並提供指定項目快取複本到期時間的設定。</span><span class="sxs-lookup"><span data-stu-id="80f4a-111">Configures an item to be cached and provides settings that specify when the cached copy of the item expires.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetExecutionOptions%2A>|<span data-ttu-id="80f4a-112">設定指定之項目的執行選項及相關聯的執行屬性。</span><span class="sxs-lookup"><span data-stu-id="80f4a-112">Sets execution options and associated execution properties for a specified item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.UpdateItemExecutionSnapshot%2A>|<span data-ttu-id="80f4a-113">產生指定之項目的項目執行快照集。</span><span class="sxs-lookup"><span data-stu-id="80f4a-113">Generates an item execution snapshot for a specified item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80f4a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80f4a-114">See Also</span></span>  
 <span data-ttu-id="80f4a-115">[使用 Web 服務和 .NET Framework 建置應用程式](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="80f4a-115">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="80f4a-116">[報表伺服器 Web 服務](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="80f4a-116">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="80f4a-117">[報表伺服器 Web 服務方法](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="80f4a-117">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="80f4a-118">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="80f4a-118">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
