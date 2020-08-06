---
title: 排程方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- schedules [Reporting Services], methods
- reports [Reporting Services], scheduling
- shared schedules [Reporting Services], methods
- methods [Reporting Services], scheduling
ms.assetid: 68ae13f9-d91e-4572-a82a-8fa42001569e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 735da4f22d523fd40dd031f55e203fa9a4204f5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592430"
---
# <a name="scheduling-methods"></a><span data-ttu-id="bdede-102">排程方法</span><span class="sxs-lookup"><span data-stu-id="bdede-102">Scheduling Methods</span></span>
  <span data-ttu-id="bdede-103">您可以使用這些方法來建立並管理執行和傳遞報表的共用排程，並快取報表伺服器所運用的重新整理計劃。</span><span class="sxs-lookup"><span data-stu-id="bdede-103">You can use these methods to create and manage shared schedules for report execution and delivery, and to cache refresh plans utilized by the report server.</span></span>  
  
|<span data-ttu-id="bdede-104">方法</span><span class="sxs-lookup"><span data-stu-id="bdede-104">Method</span></span>|<span data-ttu-id="bdede-105">動作</span><span class="sxs-lookup"><span data-stu-id="bdede-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateCacheRefreshPlan%2A>|<span data-ttu-id="bdede-106">建立項目的快取重新整理計劃。</span><span class="sxs-lookup"><span data-stu-id="bdede-106">Creates a cache refresh plan for an item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.CreateSchedule%2A>|<span data-ttu-id="bdede-107">建立新的共用排程。</span><span class="sxs-lookup"><span data-stu-id="bdede-107">Creates a new shared schedule.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DeleteCacheRefreshPlan%2A>|<span data-ttu-id="bdede-108">刪除快取重新整理計劃。</span><span class="sxs-lookup"><span data-stu-id="bdede-108">Deletes a cache refresh plan.</span></span>|  
|<xref:ReportService2010.ReportingService2010.DeleteSchedule%2A>|<span data-ttu-id="bdede-109">刪除根據特定排程識別碼的共用排程。</span><span class="sxs-lookup"><span data-stu-id="bdede-109">Deletes a shared schedule based on a specific schedule ID.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetCacheRefreshPlanProperties%2A>|<span data-ttu-id="bdede-110">傳回指定之快取重新整理計劃的屬性。</span><span class="sxs-lookup"><span data-stu-id="bdede-110">Returns the properties of the specified cache refresh plan.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetScheduleProperties%2A>|<span data-ttu-id="bdede-111">傳回共用排程的屬性值。</span><span class="sxs-lookup"><span data-stu-id="bdede-111">Returns the values of properties of a shared schedule.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListCacheRefreshPlans%2A>|<span data-ttu-id="bdede-112">傳回與目錄項目關聯的快取重新整理計劃清單。</span><span class="sxs-lookup"><span data-stu-id="bdede-112">Returns a list of the cache refresh plans associated with a catalog item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListScheduledItems%2A>|<span data-ttu-id="bdede-113">傳回與共用排程關聯的項目清單。</span><span class="sxs-lookup"><span data-stu-id="bdede-113">Returns a list of items that are associated with a shared schedule.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListSchedules%2A>|<span data-ttu-id="bdede-114">傳回報表伺服器或 SharePoint 網站上所有共用排程的清單。</span><span class="sxs-lookup"><span data-stu-id="bdede-114">Returns a list of all shared schedules at the report server or the SharePoint site.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListScheduleStates%2A>|<span data-ttu-id="bdede-115">傳回支援的排程狀態清單。</span><span class="sxs-lookup"><span data-stu-id="bdede-115">Returns a list of supported schedule states.</span></span>|  
|<xref:ReportService2010.ReportingService2010.PauseSchedule%2A>|<span data-ttu-id="bdede-116">暫停給定排程的執行。</span><span class="sxs-lookup"><span data-stu-id="bdede-116">Pauses the execution of a given schedule.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ResumeSchedule%2A>|<span data-ttu-id="bdede-117">繼續已暫停的共用排程。</span><span class="sxs-lookup"><span data-stu-id="bdede-117">Resumes a shared schedule that has been paused.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetCacheRefreshPlanProperties%2A>|<span data-ttu-id="bdede-118">設定快取重新整理計劃的屬性。</span><span class="sxs-lookup"><span data-stu-id="bdede-118">Sets the properties of a cache refresh plan.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetScheduleProperties%2A>|<span data-ttu-id="bdede-119">設定共用排程的屬性值。</span><span class="sxs-lookup"><span data-stu-id="bdede-119">Sets the value of properties of a shared schedule.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bdede-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdede-120">See Also</span></span>  
 <span data-ttu-id="bdede-121">[使用 Web 服務和 .NET Framework 建置應用程式](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="bdede-121">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="bdede-122">[報表伺服器 Web 服務](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="bdede-122">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="bdede-123">[報表伺服器 Web 服務方法](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="bdede-123">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="bdede-124">技術參考 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="bdede-124">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
