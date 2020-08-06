---
title: XTP 垃圾收集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 64ae91e5-b420-44b4-af1a-f8bca83d7f41
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 341a45c1c103f154672bb01a0648339562ee9750
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698059"
---
# <a name="xtp-garbage-collection"></a><span data-ttu-id="2d01f-102">XTP 記憶體回收</span><span class="sxs-lookup"><span data-stu-id="2d01f-102">XTP Garbage Collection</span></span>
  <span data-ttu-id="2d01f-103">XTP 記憶體回收效能物件包含與 XTP 引擎記憶體回收行程相關的計數器。</span><span class="sxs-lookup"><span data-stu-id="2d01f-103">The XTP Garbage Collection performance object contains counters related to the XTP engine's garbage collector.</span></span>  
  
 <span data-ttu-id="2d01f-104">下表描述**XTP 垃圾收集**計數器。</span><span class="sxs-lookup"><span data-stu-id="2d01f-104">This table describes the **XTP garbage Collection** counters.</span></span>  
  
|<span data-ttu-id="2d01f-105">計數器</span><span class="sxs-lookup"><span data-stu-id="2d01f-105">Counter</span></span>|<span data-ttu-id="2d01f-106">描述</span><span class="sxs-lookup"><span data-stu-id="2d01f-106">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d01f-107">**塵封角落掃描重試次數/秒 (由 GC 發出)**</span><span class="sxs-lookup"><span data-stu-id="2d01f-107">**Dusty corner scan retries/sec (GC-issued)**</span></span>|<span data-ttu-id="2d01f-108">記憶體回收行程發出塵封角落掃掠期間，(平均) 每秒因為發生寫入衝突而進行掃描的重試次數。</span><span class="sxs-lookup"><span data-stu-id="2d01f-108">The number of scan retries due to write conflicts during dusty corner sweeps issued by the garbage collector (on average), per second.</span></span> <span data-ttu-id="2d01f-109">這是層級非常低的計數器，非供客戶使用。</span><span class="sxs-lookup"><span data-stu-id="2d01f-109">This is a very low-level counter, not intended for customer use.</span></span>|  
|<span data-ttu-id="2d01f-110">**主要 GC 工作項目/秒**</span><span class="sxs-lookup"><span data-stu-id="2d01f-110">**Main GC work items/sec**</span></span>|<span data-ttu-id="2d01f-111">主要 GC 執行緒所處理的工作項目數。</span><span class="sxs-lookup"><span data-stu-id="2d01f-111">The number of work items processed by the main GC thread.</span></span>|  
|<span data-ttu-id="2d01f-112">**平行 GC 工作項目/秒**</span><span class="sxs-lookup"><span data-stu-id="2d01f-112">**Parallel GC work item/sec**</span></span>|<span data-ttu-id="2d01f-113">平行執行緒已執行 GC 工作項目的次數。</span><span class="sxs-lookup"><span data-stu-id="2d01f-113">The number of times a parallel thread has executed a GC work item.</span></span>|  
|<span data-ttu-id="2d01f-114">**已處理的資料列/秒**</span><span class="sxs-lookup"><span data-stu-id="2d01f-114">**Rows processed/sec**</span></span>|<span data-ttu-id="2d01f-115">記憶體回收行程 (平均) 每秒處理的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="2d01f-115">The number of rows processed by the garbage collector (on average), per second.</span></span>|  
|<span data-ttu-id="2d01f-116">**已處理的資料列/秒 (先在貯體中，然後移除)**</span><span class="sxs-lookup"><span data-stu-id="2d01f-116">**Rows processed/sec (first in bucket and removed)**</span></span>|<span data-ttu-id="2d01f-117">記憶體回收行程 (平均) 每秒所處理的資料列數，這些資料列會先在對應的雜湊值區中，並且能夠立即移除。</span><span class="sxs-lookup"><span data-stu-id="2d01f-117">The number of rows processed by the garbage collector that were first in the corresponding hash bucket, and were able to be removed immediately (on average), per second.</span></span>|  
|<span data-ttu-id="2d01f-118">**已處理的資料列/秒 (先在貯體中)**</span><span class="sxs-lookup"><span data-stu-id="2d01f-118">**Rows processed/sec (first in bucket)**</span></span>|<span data-ttu-id="2d01f-119">記憶體回收行程 (平均) 每秒處理的資料列數，這些資料列會先在對應的雜湊值區中。</span><span class="sxs-lookup"><span data-stu-id="2d01f-119">The number of rows processed by the garbage collector that were first in the corresponding hash bucket (on average), per second.</span></span>|  
|<span data-ttu-id="2d01f-120">**已處理的資料列/秒 (標記為取消連結)**</span><span class="sxs-lookup"><span data-stu-id="2d01f-120">**Rows processed/sec (marked for unlink)**</span></span>|<span data-ttu-id="2d01f-121">記憶體回收行程 (平均) 每秒處理的資料列數，這些資料列已標記為取消連結。</span><span class="sxs-lookup"><span data-stu-id="2d01f-121">The number of rows processed by the garbage collector that were already marked for unlink (on average), per second.</span></span>|  
|<span data-ttu-id="2d01f-122">**已處理的資料列/秒 (不需要掃掠)**</span><span class="sxs-lookup"><span data-stu-id="2d01f-122">**Rows processed/sec (no sweep needed)**</span></span>|<span data-ttu-id="2d01f-123">記憶體回收行程 (平均) 每秒處理的資料列數，這些資料列不需要塵封角落掃掠。</span><span class="sxs-lookup"><span data-stu-id="2d01f-123">The number of rows processed by the garbage collector that will not require a dusty corner sweep (on average), per second.</span></span>|  
|<span data-ttu-id="2d01f-124">**移除的掃掠過期資料列/秒**</span><span class="sxs-lookup"><span data-stu-id="2d01f-124">**Sweep expired rows removed/sec**</span></span>|<span data-ttu-id="2d01f-125">在塵封角落掃掠期間，(平均) 每秒移除的過期資料列數。</span><span class="sxs-lookup"><span data-stu-id="2d01f-125">The number of expired rows removed during dusty corner sweeps (on average), per second.</span></span>|  
|<span data-ttu-id="2d01f-126">**接觸到的掃掠過期資料列/秒**</span><span class="sxs-lookup"><span data-stu-id="2d01f-126">**Sweep expired rows touched/sec**</span></span>|<span data-ttu-id="2d01f-127">在塵封角落掃掠期間，(平均) 每秒接觸到的過期資料列數。</span><span class="sxs-lookup"><span data-stu-id="2d01f-127">The number of expired rows touched during dusty corner sweeps (on average), per second.</span></span>|  
|<span data-ttu-id="2d01f-128">**接觸到的掃掠將過期資料列/秒**</span><span class="sxs-lookup"><span data-stu-id="2d01f-128">**Sweep expiring rows touched/sec**</span></span>|<span data-ttu-id="2d01f-129">在塵封角落掃掠期間，(平均) 每秒接觸到的將過期資料列數。</span><span class="sxs-lookup"><span data-stu-id="2d01f-129">The number of expiring rows touched during dusty corner sweeps (on average), per second.</span></span>|  
|<span data-ttu-id="2d01f-130">**接觸到的掃掠資料列/秒**</span><span class="sxs-lookup"><span data-stu-id="2d01f-130">**Sweep rows touched/sec**</span></span>|<span data-ttu-id="2d01f-131">在塵封角落掃掠期間，(平均) 每秒接觸到的資料列數。</span><span class="sxs-lookup"><span data-stu-id="2d01f-131">The number of rows touched during dusty corner sweeps (on average), per second.</span></span>|  
|<span data-ttu-id="2d01f-132">**啟動的掃掠掃描/秒**</span><span class="sxs-lookup"><span data-stu-id="2d01f-132">**Sweep scans started/sec**</span></span>|<span data-ttu-id="2d01f-133">(平均) 每秒啟動的塵封角落掃掠掃描次數。</span><span class="sxs-lookup"><span data-stu-id="2d01f-133">The number of dusty corner sweep scans started (on average), per second.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d01f-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d01f-134">See Also</span></span>  
 [<span data-ttu-id="2d01f-135">XTP &#40;記憶體內部 OLTP&#41; 效能計數器</span><span class="sxs-lookup"><span data-stu-id="2d01f-135">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
