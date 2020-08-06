---
title: SQL Server 的 Wait Statistics 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Wait Statistics object
- SQLServer:Wait Statistics
ms.assetid: cb7f917d-4291-4115-9b78-ee7692ebbb2d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5cfd2f1309cb118896ff7951b7f82feb38de60e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687790"
---
# <a name="sql-server-wait-statistics-object"></a><span data-ttu-id="2be28-102">SQL Server 的 Wait Statistics 物件</span><span class="sxs-lookup"><span data-stu-id="2be28-102">SQL Server, Wait Statistics Object</span></span>
  <span data-ttu-id="2be28-103">**SQLServer:Wait Statistics** 效能物件包含效能計數器，可報告等候狀態的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2be28-103">The **SQLServer:Wait Statistics** performance object contains performance counters that report information about wait status.</span></span>  
  
 <span data-ttu-id="2be28-104">下表列出 Wait Statistics 物件包含的計數器。</span><span class="sxs-lookup"><span data-stu-id="2be28-104">The table below lists the counters that the Wait Statistics object contains.</span></span>  
  
|<span data-ttu-id="2be28-105">SQL Server Wait Statistics 計數器</span><span class="sxs-lookup"><span data-stu-id="2be28-105">SQL Server Wait Statistics counters</span></span>|<span data-ttu-id="2be28-106">描述</span><span class="sxs-lookup"><span data-stu-id="2be28-106">Description</span></span>|  
|-----------------------------------------|-----------------|  
|<span data-ttu-id="2be28-107">**Lock waits**</span><span class="sxs-lookup"><span data-stu-id="2be28-107">**Lock waits**</span></span>|<span data-ttu-id="2be28-108">正在等候鎖定的處理序統計資料。</span><span class="sxs-lookup"><span data-stu-id="2be28-108">Statistics for processes waiting on a lock.</span></span>|  
|<span data-ttu-id="2be28-109">**Log buffer waits**</span><span class="sxs-lookup"><span data-stu-id="2be28-109">**Log buffer waits**</span></span>|<span data-ttu-id="2be28-110">等候記錄緩衝區變為可用的處理序統計資料。</span><span class="sxs-lookup"><span data-stu-id="2be28-110">Statistics for processes waiting for log buffer to be available.</span></span>|  
|<span data-ttu-id="2be28-111">**Log write waits**</span><span class="sxs-lookup"><span data-stu-id="2be28-111">**Log write waits**</span></span>|<span data-ttu-id="2be28-112">等候寫入記錄緩衝區的處理序統計資料。</span><span class="sxs-lookup"><span data-stu-id="2be28-112">Statistics for processes waiting for log buffer to be written.</span></span>|  
|<span data-ttu-id="2be28-113">**Memory grant queue waits**</span><span class="sxs-lookup"><span data-stu-id="2be28-113">**Memory grant queue waits**</span></span>|<span data-ttu-id="2be28-114">等候記憶體授權變為可用的處理序統計資料。</span><span class="sxs-lookup"><span data-stu-id="2be28-114">Statistics for processes waiting for memory grant to become available.</span></span>|  
|<span data-ttu-id="2be28-115">**Network IO waits**</span><span class="sxs-lookup"><span data-stu-id="2be28-115">**Network IO waits**</span></span>|<span data-ttu-id="2be28-116">有關等候網路 I/O 的統計資料。</span><span class="sxs-lookup"><span data-stu-id="2be28-116">Statistics relevant to wait on network I/O.</span></span>|  
|<span data-ttu-id="2be28-117">**Non-Page latch waits**</span><span class="sxs-lookup"><span data-stu-id="2be28-117">**Non-Page latch waits**</span></span>|<span data-ttu-id="2be28-118">有關非頁面閂鎖的統計資料。</span><span class="sxs-lookup"><span data-stu-id="2be28-118">Statistics relevant to non-page latches.</span></span>|  
|<span data-ttu-id="2be28-119">**Page IO latch waits**</span><span class="sxs-lookup"><span data-stu-id="2be28-119">**Page IO latch waits**</span></span>|<span data-ttu-id="2be28-120">有關頁面 I/O 閂鎖的統計資料。</span><span class="sxs-lookup"><span data-stu-id="2be28-120">Statistics relevant to page I/O latches.</span></span>|  
|<span data-ttu-id="2be28-121">**Page latch waits**</span><span class="sxs-lookup"><span data-stu-id="2be28-121">**Page latch waits**</span></span>|<span data-ttu-id="2be28-122">有關頁面閂鎖的統計資料，不包括 I/O 閂鎖。</span><span class="sxs-lookup"><span data-stu-id="2be28-122">Statistics relevant to page latches, not including I/O latches.</span></span>|  
|<span data-ttu-id="2be28-123">**Thread-safe memory objects waits**</span><span class="sxs-lookup"><span data-stu-id="2be28-123">**Thread-safe memory objects waits**</span></span>|<span data-ttu-id="2be28-124">等候安全執行緒記憶體配置器的處理序統計資料。</span><span class="sxs-lookup"><span data-stu-id="2be28-124">Statistics for processes waiting on thread-safe memory allocators.</span></span>|  
|<span data-ttu-id="2be28-125">**Transaction ownership waits**</span><span class="sxs-lookup"><span data-stu-id="2be28-125">**Transaction ownership waits**</span></span>|<span data-ttu-id="2be28-126">有關同步存取交易的處理序統計資料。</span><span class="sxs-lookup"><span data-stu-id="2be28-126">Statistics relevant to processes synchronizing access to transaction.</span></span>|  
|<span data-ttu-id="2be28-127">**Wait for the worker**</span><span class="sxs-lookup"><span data-stu-id="2be28-127">**Wait for the worker**</span></span>|<span data-ttu-id="2be28-128">有關等候工作者變為可用的處理序統計資料。</span><span class="sxs-lookup"><span data-stu-id="2be28-128">Statistics relevant to processes waiting for worker to become available.</span></span>|  
|<span data-ttu-id="2be28-129">**Workspace synchronization waits**</span><span class="sxs-lookup"><span data-stu-id="2be28-129">**Workspace synchronization waits**</span></span>|<span data-ttu-id="2be28-130">有關同步存取工作空間的處理序統計資料。</span><span class="sxs-lookup"><span data-stu-id="2be28-130">Statistics relevant to processes synchronizing access to workspace.</span></span>|  
  
 <span data-ttu-id="2be28-131">物件中的每個計數器均包含下列執行個體：</span><span class="sxs-lookup"><span data-stu-id="2be28-131">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="2be28-132">項目</span><span class="sxs-lookup"><span data-stu-id="2be28-132">Item</span></span>|<span data-ttu-id="2be28-133">描述</span><span class="sxs-lookup"><span data-stu-id="2be28-133">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="2be28-134">**Average wait time (ms)**</span><span class="sxs-lookup"><span data-stu-id="2be28-134">**Average wait time (ms)**</span></span>|<span data-ttu-id="2be28-135">所選取等候類型的平均等候時間。</span><span class="sxs-lookup"><span data-stu-id="2be28-135">Average time for the selected type of wait.</span></span>|  
|<span data-ttu-id="2be28-136">**Cumulative wait time (ms) per second**</span><span class="sxs-lookup"><span data-stu-id="2be28-136">**Cumulative wait time (ms) per second**</span></span>|<span data-ttu-id="2be28-137">所選取等候類型的每秒彙總等候時間。</span><span class="sxs-lookup"><span data-stu-id="2be28-137">Aggregated wait time per second, for the selected type of wait.</span></span>|  
|<span data-ttu-id="2be28-138">**Waits in progress**</span><span class="sxs-lookup"><span data-stu-id="2be28-138">**Waits in progress**</span></span>|<span data-ttu-id="2be28-139">目前正在等候其下類型的處理序數目。</span><span class="sxs-lookup"><span data-stu-id="2be28-139">Number of processes currently waiting on the following type.</span></span>|  
|<span data-ttu-id="2be28-140">**Waits started per second**</span><span class="sxs-lookup"><span data-stu-id="2be28-140">**Waits started per second**</span></span>|<span data-ttu-id="2be28-141">所選取等候類型的每秒開始等候數目。</span><span class="sxs-lookup"><span data-stu-id="2be28-141">Number of waits started per second of the selected type of wait.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2be28-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2be28-142">See Also</span></span>  
 [<span data-ttu-id="2be28-143">監視資源使用狀況 &#40;System Monitor&#41;</span><span class="sxs-lookup"><span data-stu-id="2be28-143">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
