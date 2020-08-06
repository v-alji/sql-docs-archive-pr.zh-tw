---
title: SQL Server 的 Locks 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Locks object
- SQLServer:Locks
ms.assetid: ace04f0d-3993-4444-8317-ca39d7087e49
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f13d4ea1172d6b32b90c045a45445c5c87f48a94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592632"
---
# <a name="sql-server-locks-object"></a><span data-ttu-id="cc88e-102">SQL Server 的 Locks 物件</span><span class="sxs-lookup"><span data-stu-id="cc88e-102">SQL Server, Locks Object</span></span>
  <span data-ttu-id="cc88e-103">Microsoft **中的** SQLServer:Locks [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件會提供有關個別資源類型的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 鎖定資訊。</span><span class="sxs-lookup"><span data-stu-id="cc88e-103">The **SQLServer:Locks** object in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locks on individual resource types.</span></span> <span data-ttu-id="cc88e-104">鎖定發生於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源上，例如交易期間讀取或修改的資料列，以避免不同交易同時使用資源。</span><span class="sxs-lookup"><span data-stu-id="cc88e-104">Locks are held on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources, such as rows read or modified during a transaction, to prevent concurrent use of resources by different transactions.</span></span> <span data-ttu-id="cc88e-105">例如，若某個交易將資料表內的資料列獨佔 (X) 鎖定，就沒有其他交易可修改該資料列，直到鎖定解除為止。</span><span class="sxs-lookup"><span data-stu-id="cc88e-105">For example, if an exclusive (X) lock is held on a row within a table by a transaction, no other transaction can modify that row until the lock is released.</span></span> <span data-ttu-id="cc88e-106">將鎖定減至最少可增加並行 (Concurrency)，以改善效能。</span><span class="sxs-lookup"><span data-stu-id="cc88e-106">Minimizing locks increases concurrency, which can improve performance.</span></span> <span data-ttu-id="cc88e-107">您可同時監視 **Locks** 物件的多個執行個體，每個執行個體都代表一種資源類型的鎖定。</span><span class="sxs-lookup"><span data-stu-id="cc88e-107">Multiple instances of the **Locks** object can be monitored at the same time, with each instance representing a lock on a resource type.</span></span>  
  
 <span data-ttu-id="cc88e-108">下表描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Locks** 計數器。</span><span class="sxs-lookup"><span data-stu-id="cc88e-108">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Locks** counters.</span></span>  
  
|<span data-ttu-id="cc88e-109">SQL Server Locks 計數器</span><span class="sxs-lookup"><span data-stu-id="cc88e-109">SQL Server Locks counters</span></span>|<span data-ttu-id="cc88e-110">描述</span><span class="sxs-lookup"><span data-stu-id="cc88e-110">Description</span></span>|  
|-------------------------------|-----------------|  
|<span data-ttu-id="cc88e-111">**Average Wait Time (ms)**</span><span class="sxs-lookup"><span data-stu-id="cc88e-111">**Average Wait Time (ms)**</span></span>|<span data-ttu-id="cc88e-112">造成等候的各個鎖定要求之平均等候時間 (以毫秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="cc88e-112">Average amount of wait time (in milliseconds) for each lock request that resulted in a wait.</span></span>|  
|<span data-ttu-id="cc88e-113">**Lock Requests/sec**</span><span class="sxs-lookup"><span data-stu-id="cc88e-113">**Lock Requests/sec**</span></span>|<span data-ttu-id="cc88e-114">鎖定系統管理員每秒要求的新鎖定和鎖定轉換數。</span><span class="sxs-lookup"><span data-stu-id="cc88e-114">Number of new locks and lock conversions per second requested from the lock manager.</span></span>|  
|<span data-ttu-id="cc88e-115">**Lock Timeouts (timeout > 0)/sec**</span><span class="sxs-lookup"><span data-stu-id="cc88e-115">**Lock Timeouts (timeout > 0)/sec**</span></span>|<span data-ttu-id="cc88e-116">已逾時的每秒鎖定要求數，但不包括 NOWAIT 鎖定的要求。</span><span class="sxs-lookup"><span data-stu-id="cc88e-116">Number of lock requests per second that timed out, but excluding requests for NOWAIT locks.</span></span>|  
|<span data-ttu-id="cc88e-117">**Lock Timeouts/sec**</span><span class="sxs-lookup"><span data-stu-id="cc88e-117">**Lock Timeouts/sec**</span></span>|<span data-ttu-id="cc88e-118">已逾時的每秒鎖定要求數，包括 NOWAIT 鎖定的要求。</span><span class="sxs-lookup"><span data-stu-id="cc88e-118">Number of lock requests per second that timed out, including requests for NOWAIT locks.</span></span>|  
|<span data-ttu-id="cc88e-119">**Lock Wait Time (ms)**</span><span class="sxs-lookup"><span data-stu-id="cc88e-119">**Lock Wait Time (ms)**</span></span>|<span data-ttu-id="cc88e-120">最後一秒內的鎖定總等候時間 (以毫秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="cc88e-120">Total wait time (in milliseconds) for locks in the last second.</span></span>|  
|<span data-ttu-id="cc88e-121">**Lock Waits/sec**</span><span class="sxs-lookup"><span data-stu-id="cc88e-121">**Lock Waits/sec**</span></span>|<span data-ttu-id="cc88e-122">每秒需要呼叫者等候的鎖定要求次數。</span><span class="sxs-lookup"><span data-stu-id="cc88e-122">Number of lock requests per second that required the caller to wait.</span></span>|  
|<span data-ttu-id="cc88e-123">**Number of Deadlocks/sec**</span><span class="sxs-lookup"><span data-stu-id="cc88e-123">**Number of Deadlocks/sec**</span></span>|<span data-ttu-id="cc88e-124">造成死結的每秒鎖定要求數。</span><span class="sxs-lookup"><span data-stu-id="cc88e-124">Number of lock requests per second that resulted in a deadlock.</span></span>|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cc88e-125">可鎖定這些資源。</span><span class="sxs-lookup"><span data-stu-id="cc88e-125">can lock these resources.</span></span>  
  
|<span data-ttu-id="cc88e-126">項目</span><span class="sxs-lookup"><span data-stu-id="cc88e-126">Item</span></span>|<span data-ttu-id="cc88e-127">描述</span><span class="sxs-lookup"><span data-stu-id="cc88e-127">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="cc88e-128">**_Total**</span><span class="sxs-lookup"><span data-stu-id="cc88e-128">**_Total**</span></span>|<span data-ttu-id="cc88e-129">所有鎖定的資訊。</span><span class="sxs-lookup"><span data-stu-id="cc88e-129">Information for all locks.</span></span>|  
|<span data-ttu-id="cc88e-130">**AllocUnit**</span><span class="sxs-lookup"><span data-stu-id="cc88e-130">**AllocUnit**</span></span>|<span data-ttu-id="cc88e-131">配置單位的鎖定。</span><span class="sxs-lookup"><span data-stu-id="cc88e-131">A lock on an allocation unit.</span></span>|  
|<span data-ttu-id="cc88e-132">**應用程式**</span><span class="sxs-lookup"><span data-stu-id="cc88e-132">**Application**</span></span>|<span data-ttu-id="cc88e-133">應用程式指定資源的鎖定。</span><span class="sxs-lookup"><span data-stu-id="cc88e-133">A lock on an application-specified resource.</span></span>|  
|<span data-ttu-id="cc88e-134">**Database**</span><span class="sxs-lookup"><span data-stu-id="cc88e-134">**Database**</span></span>|<span data-ttu-id="cc88e-135">資料庫的鎖定，包括資料庫中的所有物件。</span><span class="sxs-lookup"><span data-stu-id="cc88e-135">A lock on a database, including all objects in the database.</span></span>|  
|<span data-ttu-id="cc88e-136">**Extent**</span><span class="sxs-lookup"><span data-stu-id="cc88e-136">**Extent**</span></span>|<span data-ttu-id="cc88e-137">八頁連續群組的鎖定。</span><span class="sxs-lookup"><span data-stu-id="cc88e-137">A lock on a contiguous group of 8 pages.</span></span>|  
|<span data-ttu-id="cc88e-138">**檔案**</span><span class="sxs-lookup"><span data-stu-id="cc88e-138">**File**</span></span>|<span data-ttu-id="cc88e-139">資料庫檔案的鎖定。</span><span class="sxs-lookup"><span data-stu-id="cc88e-139">A lock on a database file.</span></span>|  
|<span data-ttu-id="cc88e-140">**Heap/BTree**</span><span class="sxs-lookup"><span data-stu-id="cc88e-140">**Heap/BTree**</span></span>|<span data-ttu-id="cc88e-141">堆積或 BTree (HOBT)。</span><span class="sxs-lookup"><span data-stu-id="cc88e-141">Heap or BTree (HOBT).</span></span> <span data-ttu-id="cc88e-142">資料頁堆積的鎖定，或是索引之 BTree 結構的鎖定。</span><span class="sxs-lookup"><span data-stu-id="cc88e-142">A lock on a heap of data pages, or on the BTree structure of an index.</span></span>|  
|<span data-ttu-id="cc88e-143">**索引鍵**</span><span class="sxs-lookup"><span data-stu-id="cc88e-143">**Key**</span></span>|<span data-ttu-id="cc88e-144">索引中之資料列的鎖定。</span><span class="sxs-lookup"><span data-stu-id="cc88e-144">A lock on a row in an index.</span></span>|  
|<span data-ttu-id="cc88e-145">**中繼資料**</span><span class="sxs-lookup"><span data-stu-id="cc88e-145">**Metadata**</span></span>|<span data-ttu-id="cc88e-146">一項目錄資訊 (亦稱為中繼資料) 的鎖定。</span><span class="sxs-lookup"><span data-stu-id="cc88e-146">A lock on a piece of catalog information, also called metadata.</span></span>|  
|<span data-ttu-id="cc88e-147">**Object**</span><span class="sxs-lookup"><span data-stu-id="cc88e-147">**Object**</span></span>|<span data-ttu-id="cc88e-148">資料表、預存程序、檢視等 (包括所有資料和索引) 的鎖定。</span><span class="sxs-lookup"><span data-stu-id="cc88e-148">A lock on table, stored procedure, view, etc, including all data and indexes.</span></span> <span data-ttu-id="cc88e-149">物件可以是在 **sys.all_objects**中擁有項目的任何東西。</span><span class="sxs-lookup"><span data-stu-id="cc88e-149">The object can be anything that has an entry in **sys.all_objects**.</span></span>|  
|<span data-ttu-id="cc88e-150">**頁面**</span><span class="sxs-lookup"><span data-stu-id="cc88e-150">**Page**</span></span>|<span data-ttu-id="cc88e-151">資料庫中 8 KB 分頁的鎖定。</span><span class="sxs-lookup"><span data-stu-id="cc88e-151">A lock on an 8-kilobyte (KB) page in a database.</span></span>|  
|<span data-ttu-id="cc88e-152">**RID**</span><span class="sxs-lookup"><span data-stu-id="cc88e-152">**RID**</span></span>|<span data-ttu-id="cc88e-153">資料庫識別碼。</span><span class="sxs-lookup"><span data-stu-id="cc88e-153">Row ID.</span></span> <span data-ttu-id="cc88e-154">堆積中單一資料列的鎖定。</span><span class="sxs-lookup"><span data-stu-id="cc88e-154">A lock on a single row in a heap.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc88e-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc88e-155">See Also</span></span>  
 [<span data-ttu-id="cc88e-156">監視資源使用狀況 &#40;System Monitor&#41;</span><span class="sxs-lookup"><span data-stu-id="cc88e-156">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
