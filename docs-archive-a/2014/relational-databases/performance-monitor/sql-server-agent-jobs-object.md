---
title: SQL Server Agent、Jobs 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLAgent:Jobs
- Jobs object
ms.assetid: 225b5e2d-4a78-4178-b2b6-b419df83c4aa
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 82ee57eba20d44c08eadc125e9dfd69e73c35751
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593343"
---
# <a name="sql-server-agent-jobs-object"></a><span data-ttu-id="6fb7b-102">SQL Server 代理程式、作業物件</span><span class="sxs-lookup"><span data-stu-id="6fb7b-102">SQL Server Agent, Jobs Object</span></span>
  <span data-ttu-id="6fb7b-103">SQL Server Agent 的「 **作業** 」效能物件包含報告有關 SQL Server Agent 作業資訊的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="6fb7b-103">The SQL Server Agent **Jobs** performance object contains performance counters that report information about SQL Server Agent jobs.</span></span> <span data-ttu-id="6fb7b-104">下表列出這個物件包含的計數器。</span><span class="sxs-lookup"><span data-stu-id="6fb7b-104">The table below lists the counters that this object contains.</span></span>  
  
 <span data-ttu-id="6fb7b-105">下表包含 **SQLAgent:Jobs** 計數器。</span><span class="sxs-lookup"><span data-stu-id="6fb7b-105">The table below contains the **SQLAgent:Jobs** counters.</span></span>  
  
|<span data-ttu-id="6fb7b-106">Name</span><span class="sxs-lookup"><span data-stu-id="6fb7b-106">Name</span></span>|<span data-ttu-id="6fb7b-107">描述</span><span class="sxs-lookup"><span data-stu-id="6fb7b-107">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="6fb7b-108">**Active Jobs**</span><span class="sxs-lookup"><span data-stu-id="6fb7b-108">**Active Jobs**</span></span>|<span data-ttu-id="6fb7b-109">此計數器報告目前執行中的作業數目。</span><span class="sxs-lookup"><span data-stu-id="6fb7b-109">This counter reports the number of jobs currently running.</span></span>|  
|<span data-ttu-id="6fb7b-110">**Failed jobs**</span><span class="sxs-lookup"><span data-stu-id="6fb7b-110">**Failed jobs**</span></span>|<span data-ttu-id="6fb7b-111">此計數器報告因失敗而結束的作業數目。</span><span class="sxs-lookup"><span data-stu-id="6fb7b-111">This counter reports the number of jobs that exited with failure.</span></span>|  
|<span data-ttu-id="6fb7b-112">**Job success rate**</span><span class="sxs-lookup"><span data-stu-id="6fb7b-112">**Job success rate**</span></span>|<span data-ttu-id="6fb7b-113">此計數器報告已順利完成的已執行作業百分比。</span><span class="sxs-lookup"><span data-stu-id="6fb7b-113">This counter reports the percentage of executed jobs that completed successfully.</span></span>|  
|<span data-ttu-id="6fb7b-114">**Jobs activated/minute**</span><span class="sxs-lookup"><span data-stu-id="6fb7b-114">**Jobs activated/minute**</span></span>|<span data-ttu-id="6fb7b-115">此計數器報告在上一分鐘內啟動的作業數目。</span><span class="sxs-lookup"><span data-stu-id="6fb7b-115">This counter reports the number of jobs launched within the last minute.</span></span>|  
|<span data-ttu-id="6fb7b-116">**Queued jobs**</span><span class="sxs-lookup"><span data-stu-id="6fb7b-116">**Queued jobs**</span></span>|<span data-ttu-id="6fb7b-117">此計數器報告備妥而可供 SQL Server Agent 執行，但尚未開始執行的作業數目。</span><span class="sxs-lookup"><span data-stu-id="6fb7b-117">This counter reports the number of jobs that are ready for SQL Server Agent to run, but which have not yet started running.</span></span>|  
|<span data-ttu-id="6fb7b-118">**Successful jobs**</span><span class="sxs-lookup"><span data-stu-id="6fb7b-118">**Successful jobs**</span></span>|<span data-ttu-id="6fb7b-119">此計數器報告因成功完成而結束的作業數目。</span><span class="sxs-lookup"><span data-stu-id="6fb7b-119">This counter reports the number of jobs that exited with success.</span></span>|  
  
 <span data-ttu-id="6fb7b-120">物件中的每個計數器均包含下列執行個體：</span><span class="sxs-lookup"><span data-stu-id="6fb7b-120">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="6fb7b-121">執行個體</span><span class="sxs-lookup"><span data-stu-id="6fb7b-121">Instance</span></span>|<span data-ttu-id="6fb7b-122">描述</span><span class="sxs-lookup"><span data-stu-id="6fb7b-122">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="6fb7b-123">**_Total**</span><span class="sxs-lookup"><span data-stu-id="6fb7b-123">**_Total**</span></span>|<span data-ttu-id="6fb7b-124">所有作業的資訊。</span><span class="sxs-lookup"><span data-stu-id="6fb7b-124">Information for all jobs.</span></span>|  
|<span data-ttu-id="6fb7b-125">**警示**</span><span class="sxs-lookup"><span data-stu-id="6fb7b-125">**Alerts**</span></span>|<span data-ttu-id="6fb7b-126">由警示啟動之作業的資訊。</span><span class="sxs-lookup"><span data-stu-id="6fb7b-126">Information for jobs started by alerts.</span></span>|  
|<span data-ttu-id="6fb7b-127">**其他**</span><span class="sxs-lookup"><span data-stu-id="6fb7b-127">**Others**</span></span>|<span data-ttu-id="6fb7b-128">不是由警示或排程啟動之作業的資訊。</span><span class="sxs-lookup"><span data-stu-id="6fb7b-128">Information for jobs that were not started by alerts or schedules.</span></span> <span data-ttu-id="6fb7b-129">一般而言，這些作業是手動使用 **sp_start_job**來啟動。</span><span class="sxs-lookup"><span data-stu-id="6fb7b-129">Typically these are jobs started manually using **sp_start_job**.</span></span>|  
|<span data-ttu-id="6fb7b-130">**排程**</span><span class="sxs-lookup"><span data-stu-id="6fb7b-130">**Schedules**</span></span>|<span data-ttu-id="6fb7b-131">由排程啟動之作業的資訊。</span><span class="sxs-lookup"><span data-stu-id="6fb7b-131">Information for jobs started by schedules.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6fb7b-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fb7b-132">See Also</span></span>  
 <span data-ttu-id="6fb7b-133">[實作作業](../../ssms/agent/implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="6fb7b-133">[Implement Jobs](../../ssms/agent/implement-jobs.md) </span></span>  
 <span data-ttu-id="6fb7b-134">[使用效能物件](../../ssms/agent/use-performance-objects.md) </span><span class="sxs-lookup"><span data-stu-id="6fb7b-134">[Use Performance Objects](../../ssms/agent/use-performance-objects.md) </span></span>  
 [<span data-ttu-id="6fb7b-135">監視資源使用狀況 &#40;System Monitor&#41;</span><span class="sxs-lookup"><span data-stu-id="6fb7b-135">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
