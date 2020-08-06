---
title: 找出瓶頸 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- resource bottlenecks [SQL Server]
- database monitoring [SQL Server], bottlenecks
- performance [SQL Server], bottlenecks
- tuning databases [SQL Server], bottlenecks
- monitoring server performance [SQL Server], bottlenecks
- monitoring performance [SQL Server], bottlenecks
- database performance [SQL Server], bottlenecks
- server performance [SQL Server], bottlenecks
- bottlenecks [SQL Server]
- identifying bottlenecks [SQL Server]
ms.assetid: db079e65-ee80-4105-aec9-f8230d0d6635
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e941b3f4a1185177cef007eb6a02a71ae1adece7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687785"
---
# <a name="identify-bottlenecks"></a><span data-ttu-id="af042-102">找出瓶頸</span><span class="sxs-lookup"><span data-stu-id="af042-102">Identify Bottlenecks</span></span>
  <span data-ttu-id="af042-103">同時存取共用資源會產生瓶頸。</span><span class="sxs-lookup"><span data-stu-id="af042-103">Simultaneous access to shared resources causes bottlenecks.</span></span> <span data-ttu-id="af042-104">通常，每個軟體系統中都會有瓶頸存在，而且這是無法避免的。</span><span class="sxs-lookup"><span data-stu-id="af042-104">In general, bottlenecks are present in every software system and are inevitable.</span></span> <span data-ttu-id="af042-105">但是，過量要求共用資源會讓回應時間變差，這時就必須找出問題並進行微調。</span><span class="sxs-lookup"><span data-stu-id="af042-105">However, excessive demands on shared resources cause poor response time and must be identified and tuned.</span></span>  
  
 <span data-ttu-id="af042-106">導致瓶頸的原因包括：</span><span class="sxs-lookup"><span data-stu-id="af042-106">Causes of bottlenecks include:</span></span>  
  
-   <span data-ttu-id="af042-107">需要額外或升級元件的資源不足。</span><span class="sxs-lookup"><span data-stu-id="af042-107">Insufficient resources, requiring additional or upgraded components.</span></span>  
  
-   <span data-ttu-id="af042-108">相同類型的資源，其工作負載分配不均 (例如，某個磁碟被獨占)。</span><span class="sxs-lookup"><span data-stu-id="af042-108">Resources of the same type among which workloads are not distributed evenly; for example, one disk is being monopolized.</span></span>  
  
-   <span data-ttu-id="af042-109">資源的功能有問題。</span><span class="sxs-lookup"><span data-stu-id="af042-109">Malfunctioning resources.</span></span>  
  
-   <span data-ttu-id="af042-110">資源的組態設定不正確。</span><span class="sxs-lookup"><span data-stu-id="af042-110">Incorrectly configured resources.</span></span>  
  
## <a name="analyzing-bottlenecks"></a><span data-ttu-id="af042-111">分析瓶頸</span><span class="sxs-lookup"><span data-stu-id="af042-111">Analyzing Bottlenecks</span></span>  
 <span data-ttu-id="af042-112">各種事件的持續時間過長，是發生瓶頸的指標，這種情況便可進行微調。</span><span class="sxs-lookup"><span data-stu-id="af042-112">Excessive durations for various events are indicators of bottlenecks that can be tuned.</span></span>  
  
 <span data-ttu-id="af042-113">例如：</span><span class="sxs-lookup"><span data-stu-id="af042-113">For example:</span></span>  
  
-   <span data-ttu-id="af042-114">可能是其他元件防止負載到達這個元件，因此增加完成負載的時間。</span><span class="sxs-lookup"><span data-stu-id="af042-114">Some other component may prevent the load from reaching this component thereby increasing the time to complete the load.</span></span>  
  
-   <span data-ttu-id="af042-115">可能是網路壅塞使得用戶端的要求更為耗時。</span><span class="sxs-lookup"><span data-stu-id="af042-115">Client requests may take longer due to network congestion.</span></span>  
  
 <span data-ttu-id="af042-116">在追蹤伺服器效能以找出瓶頸時，有下列五個主要區域需要監視。</span><span class="sxs-lookup"><span data-stu-id="af042-116">Following are five key areas to monitor when tracking server performance to identify bottlenecks.</span></span>  
  
|<span data-ttu-id="af042-117">可能瓶頸區</span><span class="sxs-lookup"><span data-stu-id="af042-117">Possible bottleneck area</span></span>|<span data-ttu-id="af042-118">對伺服器的影響</span><span class="sxs-lookup"><span data-stu-id="af042-118">Effects on the server</span></span>|  
|------------------------------|---------------------------|  
|<span data-ttu-id="af042-119">記憶體使用量</span><span class="sxs-lookup"><span data-stu-id="af042-119">Memory usage</span></span>|<span data-ttu-id="af042-120">如果配置到 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的記憶體或其可用記憶體不足，會使效能降低。</span><span class="sxs-lookup"><span data-stu-id="af042-120">Insufficient memory allocated or available to Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] degrades performance.</span></span> <span data-ttu-id="af042-121">這時必須從磁碟讀取資料，而不是直接從資料快取讀取。</span><span class="sxs-lookup"><span data-stu-id="af042-121">Data must be read from the disk rather than directly from the data cache.</span></span> <span data-ttu-id="af042-122">當需要分頁時，Microsoft Windows 作業系統需與磁碟交換資料，因此會進行過度的分頁動作。</span><span class="sxs-lookup"><span data-stu-id="af042-122">Microsoft Windows operating systems perform excessive paging by swapping data to and from the disk as the pages are needed.</span></span>|  
|<span data-ttu-id="af042-123">CPU 使用率</span><span class="sxs-lookup"><span data-stu-id="af042-123">CPU utilization</span></span>|<span data-ttu-id="af042-124">CPU 使用率若長期偏高，表示 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢需要進行微調，或需要升級 CPU。</span><span class="sxs-lookup"><span data-stu-id="af042-124">A chronically high CPU utilization rate may indicate that [!INCLUDE[tsql](../../includes/tsql-md.md)] queries need to be tuned or that a CPU upgrade is needed.</span></span>|  
|<span data-ttu-id="af042-125">磁碟輸入/輸出 (I/O)</span><span class="sxs-lookup"><span data-stu-id="af042-125">Disk input/output (I/O)</span></span>|[!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="af042-126">可以微調查詢，以減少不必要的 I/O；例如利用索引。</span><span class="sxs-lookup"><span data-stu-id="af042-126">queries can be tuned to reduce unnecessary I/O; for example, by employing indexes.</span></span>|  
|<span data-ttu-id="af042-127">使用者連線</span><span class="sxs-lookup"><span data-stu-id="af042-127">User connections</span></span>|<span data-ttu-id="af042-128">過多的使用者同時存取伺服器，會造成效能降低。</span><span class="sxs-lookup"><span data-stu-id="af042-128">Too many users may be accessing the server simultaneously causing performance degradation.</span></span>|  
|<span data-ttu-id="af042-129">封鎖的鎖定</span><span class="sxs-lookup"><span data-stu-id="af042-129">Blocking locks</span></span>|<span data-ttu-id="af042-130">設計錯誤的應用程式會造成鎖定與阻礙同時發生，而導致回應時間變長，以及交易輸送速度變慢。</span><span class="sxs-lookup"><span data-stu-id="af042-130">Incorrectly designed applications can cause locks and hamper concurrency, thus causing longer response times and lower transaction throughput rates.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af042-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af042-131">See Also</span></span>  
 <span data-ttu-id="af042-132">[監視 CPU 使用量](../performance-monitor/monitor-cpu-usage.md) </span><span class="sxs-lookup"><span data-stu-id="af042-132">[Monitor CPU Usage](../performance-monitor/monitor-cpu-usage.md) </span></span>  
 <span data-ttu-id="af042-133">[監視磁碟使用量](../performance-monitor/monitor-disk-usage.md) </span><span class="sxs-lookup"><span data-stu-id="af042-133">[Monitor Disk Usage](../performance-monitor/monitor-disk-usage.md) </span></span>  
 <span data-ttu-id="af042-134">[監視記憶體使用量](../performance-monitor/monitor-memory-usage.md) </span><span class="sxs-lookup"><span data-stu-id="af042-134">[Monitor Memory Usage](../performance-monitor/monitor-memory-usage.md) </span></span>  
 <span data-ttu-id="af042-135">[SQL Server 的 General Statistics 物件](../performance-monitor/sql-server-general-statistics-object.md) </span><span class="sxs-lookup"><span data-stu-id="af042-135">[SQL Server, General Statistics Object](../performance-monitor/sql-server-general-statistics-object.md) </span></span>  
 [<span data-ttu-id="af042-136">SQL Server 的 Locks 物件</span><span class="sxs-lookup"><span data-stu-id="af042-136">SQL Server, Locks Object</span></span>](../performance-monitor/sql-server-locks-object.md)  
  
  
