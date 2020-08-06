---
title: 報表伺服器 Web 服務方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- XML Web service [Reporting Services], features
- Web service [Reporting Services], features
- Report Server Web service, features
- XML Web service [Reporting Services], methods
ms.assetid: ce5afa27-e90c-44a7-b204-098a065b3665
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 37d0031ebfb4ec6d31da6aad9a8842c0623cb75b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592431"
---
# <a name="report-server-web-service-methods"></a><span data-ttu-id="1d6f1-102">報表伺服器 Web 服務方法</span><span class="sxs-lookup"><span data-stu-id="1d6f1-102">Report Server Web Service Methods</span></span>
  <span data-ttu-id="1d6f1-103">報表伺服器 Web 服務包含數個以元件功能為基礎的方法類別。</span><span class="sxs-lookup"><span data-stu-id="1d6f1-103">The Report Server Web services include several categories of methods that are based on component features.</span></span> <span data-ttu-id="1d6f1-104">這些方法是透過多個 Web 服務端點 (三個用於報表管理，一個用於報表執行) 而提供，這些端點會公開為 <xref:ReportService2010.ReportingService2010> 和 <xref:ReportExecution2005.ReportExecutionService> 類別的成員。</span><span class="sxs-lookup"><span data-stu-id="1d6f1-104">These methods are provided through several Web service endpoints (three for report management and one for report execution) which are exposed as members of the <xref:ReportService2010.ReportingService2010> and <xref:ReportExecution2005.ReportExecutionService> classes.</span></span> <span data-ttu-id="1d6f1-105">這些類別可透過 proxy 類別工具產生，例如 SDK 隨附的 wsdl.exe [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1d6f1-105">These classes can be generated through a proxy class tool such as wsdl.exe, which is included with the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK.</span></span> <span data-ttu-id="1d6f1-106">如需報表伺服器 Web 服務和 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 的詳細資訊，請參閱[使用 Web 服務和 .NET Framework 建置應用程式](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="1d6f1-106">For more information about the Report Server Web services and the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], see [Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md).</span></span>  
  
## <a name="endpoints-and-methods"></a><span data-ttu-id="1d6f1-107">端點和方法</span><span class="sxs-lookup"><span data-stu-id="1d6f1-107">Endpoints and Methods</span></span>  
 <span data-ttu-id="1d6f1-108">下表將列出報表伺服器 Web 服務的端點，以及 <xref:ReportService2010.ReportingService2010> 端點所提供之方法的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="1d6f1-108">The following table lists the endpoints of the Report Server Web service, and the categories of methods provided by the <xref:ReportService2010.ReportingService2010> endpoint.</span></span> <span data-ttu-id="1d6f1-109">如需其他端點所提供之方法的詳細資訊，請參閱[技術參考 &#40;SSRS&#41;](../../technical-reference-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1d6f1-109">For information on the methods available in the other endpoints, see [Technical Reference &#40;SSRS&#41;](../../technical-reference-ssrs.md).</span></span>  
  
|<span data-ttu-id="1d6f1-110">主題</span><span class="sxs-lookup"><span data-stu-id="1d6f1-110">Topic</span></span>|<span data-ttu-id="1d6f1-111">描述</span><span class="sxs-lookup"><span data-stu-id="1d6f1-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1d6f1-112">報表伺服器 Web 服務端點</span><span class="sxs-lookup"><span data-stu-id="1d6f1-112">Report Server Web Service Endpoints</span></span>](report-server-web-service-endpoints.md)|<span data-ttu-id="1d6f1-113">描述報表伺服器 Web 服務的管理和執行端點。</span><span class="sxs-lookup"><span data-stu-id="1d6f1-113">Describes the management and execution endpoints of the Report Server Web service.</span></span>|  
|[<span data-ttu-id="1d6f1-114">報表伺服器命名空間管理方法</span><span class="sxs-lookup"><span data-stu-id="1d6f1-114">Report Server Namespace Management Methods</span></span>](report-server-namespace-management-methods.md)|<span data-ttu-id="1d6f1-115">描述您可以用於管理報表伺服器資料庫的方法。</span><span class="sxs-lookup"><span data-stu-id="1d6f1-115">Describes methods that you can use to manage the report server database.</span></span> <span data-ttu-id="1d6f1-116">也就是說，您可以管理資料夾和資源並設定項目屬性。</span><span class="sxs-lookup"><span data-stu-id="1d6f1-116">Specifically you can manage folders and resources and set item properties.</span></span>|  
|[<span data-ttu-id="1d6f1-117">授權方法</span><span class="sxs-lookup"><span data-stu-id="1d6f1-117">Authorization Methods</span></span>](authorization-methods.md)|<span data-ttu-id="1d6f1-118">描述可用於管理工作、角色和原則的方法。</span><span class="sxs-lookup"><span data-stu-id="1d6f1-118">Describes methods that you can use to manage tasks, roles, and policies.</span></span>|  
|[<span data-ttu-id="1d6f1-119">資料來源和連接方法</span><span class="sxs-lookup"><span data-stu-id="1d6f1-119">Data Sources and Connection Methods</span></span>](data-sources-and-connection-methods.md)|<span data-ttu-id="1d6f1-120">描述可用於為報表設定資料來源連接及認證資訊並進行管理的方法。</span><span class="sxs-lookup"><span data-stu-id="1d6f1-120">Describes methods that you can use to set and manage data source connection and credential information for reports.</span></span>|  
|[<span data-ttu-id="1d6f1-121">報表參數方法</span><span class="sxs-lookup"><span data-stu-id="1d6f1-121">Report Parameters Methods</span></span>](report-parameters-methods.md)|<span data-ttu-id="1d6f1-122">描述可用於為報表設定及擷取參數的方法。</span><span class="sxs-lookup"><span data-stu-id="1d6f1-122">Describes methods that you can use to set and retrieve parameters for reports.</span></span>|  
|[<span data-ttu-id="1d6f1-123">模型方法</span><span class="sxs-lookup"><span data-stu-id="1d6f1-123">Model Methods</span></span>](../report-server-web-service.md)|<span data-ttu-id="1d6f1-124">描述可用於管理模型的方法。</span><span class="sxs-lookup"><span data-stu-id="1d6f1-124">Describes methods that you can use to manage models.</span></span>|  
|[<span data-ttu-id="1d6f1-125">轉譯及執行方法</span><span class="sxs-lookup"><span data-stu-id="1d6f1-125">Rendering and Execution Methods</span></span>](rendering-and-execution-methods.md)|<span data-ttu-id="1d6f1-126">描述可用於管理報表執行、轉譯和快取的方法。</span><span class="sxs-lookup"><span data-stu-id="1d6f1-126">Describes methods that you can use to manage report execution, rendering, and caching.</span></span>|  
|[<span data-ttu-id="1d6f1-127">報表記錄方法</span><span class="sxs-lookup"><span data-stu-id="1d6f1-127">Report History Methods</span></span>](report-history-methods.md)|<span data-ttu-id="1d6f1-128">描述可用於建立並管理報表記錄快照的方法。</span><span class="sxs-lookup"><span data-stu-id="1d6f1-128">Describes methods that you can use to create and manage report history snapshots.</span></span>|  
|[<span data-ttu-id="1d6f1-129">排程方法</span><span class="sxs-lookup"><span data-stu-id="1d6f1-129">Scheduling Methods</span></span>](scheduling-methods.md)|<span data-ttu-id="1d6f1-130">描述可用於建立並管理報表伺服器所使用之共用排程和快取重新整理計劃的方法。</span><span class="sxs-lookup"><span data-stu-id="1d6f1-130">Describes methods that you can use to create and manage shared schedules and cache refresh plans that are used by the report server.</span></span>|  
|[<span data-ttu-id="1d6f1-131">訂閱與傳遞方法</span><span class="sxs-lookup"><span data-stu-id="1d6f1-131">Subscription and Delivery Methods</span></span>](subscription-and-delivery-methods.md)|<span data-ttu-id="1d6f1-132">描述可用於建立並管理訂閱和報表傳遞的方法。</span><span class="sxs-lookup"><span data-stu-id="1d6f1-132">Describes methods that you can use to create and manage subscriptions and report delivery.</span></span>|  
|[<span data-ttu-id="1d6f1-133">連結報表方法</span><span class="sxs-lookup"><span data-stu-id="1d6f1-133">Linked Reports Methods</span></span>](linked-reports-methods.md)|<span data-ttu-id="1d6f1-134">描述可用於建立並管理連結報表的方法。</span><span class="sxs-lookup"><span data-stu-id="1d6f1-134">Describes methods that you can use to create and manage linked reports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d6f1-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d6f1-135">See Also</span></span>  
 <span data-ttu-id="1d6f1-136">[存取 SOAP API](../accessing-the-soap-api.md) </span><span class="sxs-lookup"><span data-stu-id="1d6f1-136">[Accessing the SOAP API](../accessing-the-soap-api.md) </span></span>  
 <span data-ttu-id="1d6f1-137">[使用 Web 服務和 .NET Framework 建置應用程式](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="1d6f1-137">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="1d6f1-138">[報表伺服器 Web 服務](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="1d6f1-138">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="1d6f1-139">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1d6f1-139">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
