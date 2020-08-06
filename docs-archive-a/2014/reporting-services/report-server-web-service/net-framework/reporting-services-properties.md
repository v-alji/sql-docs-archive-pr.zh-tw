---
title: Reporting Services 屬性 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- report servers [Reporting Services], properties
- properties [Reporting Services], about properties
- reports [Reporting Services], properties
- Report Server Web service, properties
- report properties [Reporting Services]
- XML Web service [Reporting Services], properties
- Web service [Reporting Services], properties
- properties [Reporting Services]
ms.assetid: 8c855194-4c20-4ecc-a328-5137d54b560c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 61f1f50ea7a49acc616a36a4eaf1d3d5fcdf269a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688506"
---
# <a name="reporting-services-properties"></a><span data-ttu-id="e8806-102">Reporting Services 屬性</span><span class="sxs-lookup"><span data-stu-id="e8806-102">Reporting Services Properties</span></span>
  <span data-ttu-id="e8806-103">報表伺服器會定義一組對於報表伺服器是全域的系統屬性，以及一組與報表伺服器資料庫中儲存的個別項目相關聯的項目屬性。</span><span class="sxs-lookup"><span data-stu-id="e8806-103">The report server defines a set of system properties that are global to the report server and a set of item properties that are associated with an individual item stored in the report server database.</span></span> <span data-ttu-id="e8806-104">報表伺服器所定義的屬性無法刪除，而且在某些情況下，它們是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="e8806-104">Properties defined by the report server cannot be deleted, and in some cases they are read-only.</span></span> <span data-ttu-id="e8806-105">應用程式可以將其他使用者定義的屬性加入系統與項目屬性，以擴充系統屬性與項目屬性。</span><span class="sxs-lookup"><span data-stu-id="e8806-105">An application can extend system properties and item properties by adding additional user-defined properties to the system and item properties.</span></span>  
  
 <span data-ttu-id="e8806-106">下列 Web 服務方法會抓取並設定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 屬性。</span><span class="sxs-lookup"><span data-stu-id="e8806-106">The following Web service methods retrieve and set [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] properties.</span></span>  
  
|<span data-ttu-id="e8806-107">方法</span><span class="sxs-lookup"><span data-stu-id="e8806-107">Method</span></span>|<span data-ttu-id="e8806-108">動作</span><span class="sxs-lookup"><span data-stu-id="e8806-108">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GetProperties%2A>|<span data-ttu-id="e8806-109">傳回報表伺服器資料庫中項目上一或多個屬性的值。</span><span class="sxs-lookup"><span data-stu-id="e8806-109">Returns the values of one or more properties on an item in the report server database.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>|<span data-ttu-id="e8806-110">傳回一個或多個系統屬性。</span><span class="sxs-lookup"><span data-stu-id="e8806-110">Returns one or more system properties.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetProperties%2A>|<span data-ttu-id="e8806-111">在報表伺服器資料庫中設定項目的一或多個屬性。</span><span class="sxs-lookup"><span data-stu-id="e8806-111">Sets one or more properties of an item in the report server database.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>|<span data-ttu-id="e8806-112">設定一個或多個系統屬性。</span><span class="sxs-lookup"><span data-stu-id="e8806-112">Sets one or more system properties.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="e8806-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="e8806-113">In This Section</span></span>  
  
|<span data-ttu-id="e8806-114">主題</span><span class="sxs-lookup"><span data-stu-id="e8806-114">Topic</span></span>|<span data-ttu-id="e8806-115">描述</span><span class="sxs-lookup"><span data-stu-id="e8806-115">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e8806-116">報表伺服器項目屬性</span><span class="sxs-lookup"><span data-stu-id="e8806-116">Report Server Item Properties</span></span>](reporting-services-properties-report-server-item-properties.md)|<span data-ttu-id="e8806-117">描述在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的項目特定屬性。</span><span class="sxs-lookup"><span data-stu-id="e8806-117">Describes the item-specific properties in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="e8806-118">報表伺服器系統屬性</span><span class="sxs-lookup"><span data-stu-id="e8806-118">Report Server System Properties</span></span>](reporting-services-properties-report-server-system-properties.md)|<span data-ttu-id="e8806-119">描述在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的系統特定屬性。</span><span class="sxs-lookup"><span data-stu-id="e8806-119">Describes the system-specific properties in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8806-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8806-120">See Also</span></span>  
 <span data-ttu-id="e8806-121">[使用 Web 服務和 .NET Framework 建置應用程式](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="e8806-121">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="e8806-122">[報表伺服器 Web 服務](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="e8806-122">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="e8806-123">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e8806-123">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
