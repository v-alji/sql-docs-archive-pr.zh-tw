---
title: SQL Server 的 Workload Group Stats 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Workload Group Stats object
- 'SQLServer: Workload Group Stats'
ms.assetid: ca20e4f6-50ec-4456-900d-87d280fde2b3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fb363803c562b305687e78e1315f1c4255041b1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594023"
---
# <a name="sql-server-workload-group-stats-object"></a><span data-ttu-id="549a6-102">SQL Server, Workload Group Stats 物件</span><span class="sxs-lookup"><span data-stu-id="549a6-102">SQL Server, Workload Group Stats Object</span></span>
  <span data-ttu-id="549a6-103">SQLServer:Workload Group Stats 物件包含效能計數器，可報告資源管理員工作負載群組統計資料的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="549a6-103">The SQLServer:Workload Group Stats object contains performance counters that report information about Resource Governor workload group statistics.</span></span>  
  
 <span data-ttu-id="549a6-104">每個作用中工作負載群組都會建立 SQLServer:Workload Group Stats 效能物件的執行個體，而且此執行個體的名稱與資源管理員工作負載群組名稱相同。</span><span class="sxs-lookup"><span data-stu-id="549a6-104">Each active workload group creates an instance of the SQLServer:Workload Group Stats performance object that has the same instance name as the Resource Governor workload group name.</span></span> <span data-ttu-id="549a6-105">下表描述這個執行個體支援的計數器。</span><span class="sxs-lookup"><span data-stu-id="549a6-105">The following table describes counters supported on this instance.</span></span>  
  
|<span data-ttu-id="549a6-106">計數器名稱</span><span class="sxs-lookup"><span data-stu-id="549a6-106">Counter name</span></span>|<span data-ttu-id="549a6-107">描述</span><span class="sxs-lookup"><span data-stu-id="549a6-107">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="549a6-108">Queued requests</span><span class="sxs-lookup"><span data-stu-id="549a6-108">Queued requests</span></span>|<span data-ttu-id="549a6-109">目前正在等候收取的佇列要求數目。</span><span class="sxs-lookup"><span data-stu-id="549a6-109">The current number of queued requests that is waiting to be picked up.</span></span> <span data-ttu-id="549a6-110">如果到達 GROUP_MAX_REQUESTS 限制之後調整流速，則這個計數可以是非零。</span><span class="sxs-lookup"><span data-stu-id="549a6-110">This count can be non-zero if throttling occurs after the GROUP_MAX_REQUESTS limit is reached.</span></span>|  
|<span data-ttu-id="549a6-111">Active requests</span><span class="sxs-lookup"><span data-stu-id="549a6-111">Active requests</span></span>|<span data-ttu-id="549a6-112">目前正在這個工作負載群組中執行的要求數目。</span><span class="sxs-lookup"><span data-stu-id="549a6-112">The number of requests that are currently running in this workload group.</span></span> <span data-ttu-id="549a6-113">這個計數應該等於群組識別碼所篩選之 sys.dm_exec_requests 中的資料列計數。</span><span class="sxs-lookup"><span data-stu-id="549a6-113">This should be equivalent to the count of rows from sys.dm_exec_requests filtered by group ID.</span></span>|  
|<span data-ttu-id="549a6-114">Requests completed/sec</span><span class="sxs-lookup"><span data-stu-id="549a6-114">Requests completed/sec</span></span>|<span data-ttu-id="549a6-115">在這個工作負載群組中完成的要求數目。</span><span class="sxs-lookup"><span data-stu-id="549a6-115">The number of requests that have completed in this workload group.</span></span> <span data-ttu-id="549a6-116">這個數目是累計的。</span><span class="sxs-lookup"><span data-stu-id="549a6-116">This number is cumulative.</span></span>|  
|<span data-ttu-id="549a6-117">CPU usage %</span><span class="sxs-lookup"><span data-stu-id="549a6-117">CPU usage %</span></span>|<span data-ttu-id="549a6-118">這個工作負載群組中所有要求的 CPU 頻寬使用量 (相對於電腦所測得並正規化為系統上的所有 CPU)。</span><span class="sxs-lookup"><span data-stu-id="549a6-118">The CPU bandwidth usage by all requests in this workload group measured relative to the computer and normalized to all the CPUs on the system.</span></span> <span data-ttu-id="549a6-119">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序可用的 CPU 數量變更時，這個值將會變更。</span><span class="sxs-lookup"><span data-stu-id="549a6-119">This value will change as the amount of CPU available to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process changes.</span></span> <span data-ttu-id="549a6-120">但是，它不會正規化為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序收到的內容。</span><span class="sxs-lookup"><span data-stu-id="549a6-120">It is not normalized to what the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process receives.</span></span>|  
|<span data-ttu-id="549a6-121">Max request CPU time (ms)</span><span class="sxs-lookup"><span data-stu-id="549a6-121">Max request CPU time (ms)</span></span>|<span data-ttu-id="549a6-122">目前正在這個工作負載群組中執行之要求所使用的最大 CPU 時間 (以毫秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="549a6-122">The maximum CPU time, in milliseconds, used by a request currently running in the workload group.</span></span>|  
|<span data-ttu-id="549a6-123">Blocked requests</span><span class="sxs-lookup"><span data-stu-id="549a6-123">Blocked requests</span></span>|<span data-ttu-id="549a6-124">目前在工作負載群組中封鎖的要求數目。</span><span class="sxs-lookup"><span data-stu-id="549a6-124">The current number of blocked requests in the workload group.</span></span> <span data-ttu-id="549a6-125">這個值可用來判斷工作負載特性。</span><span class="sxs-lookup"><span data-stu-id="549a6-125">This can be used to determine workload characteristics.</span></span>|  
|<span data-ttu-id="549a6-126">Reduced memory grants/sec</span><span class="sxs-lookup"><span data-stu-id="549a6-126">Reduced memory grants/sec</span></span>|<span data-ttu-id="549a6-127">每秒小於理想記憶體授權數量的查詢數目。</span><span class="sxs-lookup"><span data-stu-id="549a6-127">The number of queries that are getting less than ideal amount of memory grants per second.</span></span>|  
|<span data-ttu-id="549a6-128">Max request memory grant (KB)</span><span class="sxs-lookup"><span data-stu-id="549a6-128">Max request memory grant (KB)</span></span>|<span data-ttu-id="549a6-129">查詢之記憶體授權的最大值 (以 KB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="549a6-129">The maximum value of memory grant, in kilobytes (KB), for a query.</span></span>|  
|<span data-ttu-id="549a6-130">Query optimizations/sec</span><span class="sxs-lookup"><span data-stu-id="549a6-130">Query optimizations/sec</span></span>|<span data-ttu-id="549a6-131">在這個工作負載群組中每秒發生的查詢最佳化數目。</span><span class="sxs-lookup"><span data-stu-id="549a6-131">The number of query optimizations that have happened in this workload group per second.</span></span> <span data-ttu-id="549a6-132">這個值可用來判斷工作負載特性。</span><span class="sxs-lookup"><span data-stu-id="549a6-132">This can be used to determine workload characteristics.</span></span>|  
|<span data-ttu-id="549a6-133">Suboptimal plans/sec</span><span class="sxs-lookup"><span data-stu-id="549a6-133">Suboptimal plans/sec</span></span>|<span data-ttu-id="549a6-134">在這個工作負載群組中每秒產生的次佳計畫數目。</span><span class="sxs-lookup"><span data-stu-id="549a6-134">The number of suboptimal plans that are generated in this workload group per second.</span></span>|  
|<span data-ttu-id="549a6-135">Active parallel threads</span><span class="sxs-lookup"><span data-stu-id="549a6-135">Active parallel threads</span></span>|<span data-ttu-id="549a6-136">目前平行執行緒使用量的計數。</span><span class="sxs-lookup"><span data-stu-id="549a6-136">The current count of parallel threads usage.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="549a6-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="549a6-137">See Also</span></span>  
 <span data-ttu-id="549a6-138">[監視資源使用量 &#40;系統監視器&#41;](monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="549a6-138">[Monitor Resource Usage &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="549a6-139">[SQL Server, Resource Pool Stats 物件](sql-server-resource-pool-stats-object.md) </span><span class="sxs-lookup"><span data-stu-id="549a6-139">[SQL Server, Resource Pool Stats Object](sql-server-resource-pool-stats-object.md) </span></span>  
 [<span data-ttu-id="549a6-140">資源管理員</span><span class="sxs-lookup"><span data-stu-id="549a6-140">Resource Governor</span></span>](../resource-governor/resource-governor.md)  
  
  
