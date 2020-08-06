---
title: 管理記憶體內部 OLTP 的記憶體 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: d82f21fa-6be1-4723-a72e-f2526fafd1b6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 90f9b638697d59a0a573a9a31c0a5faade23e870
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706701"
---
# <a name="managing-memory-for-in-memory-oltp"></a><span data-ttu-id="866a2-102">為記憶體中的 OLTP 管理記憶體</span><span class="sxs-lookup"><span data-stu-id="866a2-102">Managing Memory for In-Memory OLTP</span></span>
  <span data-ttu-id="866a2-103">記憶體最佳化資料表需要有足夠的記憶體，以將所有資料列和索引保留在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="866a2-103">Memory-optimized tables require that sufficient memory exist to keep all of the rows and indexes in memory.</span></span> <span data-ttu-id="866a2-104">因為記憶體是有限的資源，所以請務必了解並管理系統上的記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="866a2-104">Because memory is a finite resource, it is important that you understand and manage memory usage on your system.</span></span> <span data-ttu-id="866a2-105">本節的主題涵蓋了常見的記憶體使用與管理案例。</span><span class="sxs-lookup"><span data-stu-id="866a2-105">The topics in this section cover common memory use and management scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="866a2-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="866a2-106">In this section</span></span>  
  
|<span data-ttu-id="866a2-107">區段</span><span class="sxs-lookup"><span data-stu-id="866a2-107">Section</span></span>|<span data-ttu-id="866a2-108">描述</span><span class="sxs-lookup"><span data-stu-id="866a2-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="866a2-109">估計記憶體最佳化資料表的記憶體需求</span><span class="sxs-lookup"><span data-stu-id="866a2-109">Estimate Memory Requirements for Memory-Optimized Tables</span></span>](../relational-databases/in-memory-oltp/memory-optimized-tables.md)|<span data-ttu-id="866a2-110">估計資料表的記憶體需求。</span><span class="sxs-lookup"><span data-stu-id="866a2-110">Estimate a table's memory needs.</span></span>|  
|[<span data-ttu-id="866a2-111">資料庫並繫結至資源集區的指引，請參閱</span><span class="sxs-lookup"><span data-stu-id="866a2-111">Bind a Database with Memory-Optimized Tables to a Resource Pool</span></span>](../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)|<span data-ttu-id="866a2-112">繫結資料庫與資源集區的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="866a2-112">Step by step walkthrough to bind a database with a resource pool.</span></span>|  
|[<span data-ttu-id="866a2-113">監視與疑難排解記憶體使用量</span><span class="sxs-lookup"><span data-stu-id="866a2-113">Monitor and Troubleshoot Memory Usage</span></span>](../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)|<span data-ttu-id="866a2-114">您可以用來監視記憶體使用量的工具。</span><span class="sxs-lookup"><span data-stu-id="866a2-114">Tools you can use to monitor your memory usage.</span></span> <span data-ttu-id="866a2-115">同時也包含記憶體使用量太高的疑難排解方式。</span><span class="sxs-lookup"><span data-stu-id="866a2-115">Also covers troubleshooting if memory usage gets too high.</span></span>|  
|[<span data-ttu-id="866a2-116">解決記憶體不足的問題</span><span class="sxs-lookup"><span data-stu-id="866a2-116">Resolve Out Of Memory Issues</span></span>](../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md)|<span data-ttu-id="866a2-117">從 OOM (記憶體不足) 情況中復原的步驟。</span><span class="sxs-lookup"><span data-stu-id="866a2-117">Steps to recover from an OOM (Out of Memory) situation.</span></span>|  
|[<span data-ttu-id="866a2-118">還原資料庫並將其繫結至資源集區</span><span class="sxs-lookup"><span data-stu-id="866a2-118">Restore a Database and Bind it to a Resource Pool</span></span>](../relational-databases/in-memory-oltp/restore-a-database-and-bind-it-to-a-resource-pool.md)|<span data-ttu-id="866a2-119">還原 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 資料庫並將它繫結至具名資源集區的步驟。</span><span class="sxs-lookup"><span data-stu-id="866a2-119">Steps to restore an [!INCLUDE[hek_2](../includes/hek-2-md.md)] database and bind it to a named resource pool.</span></span>|  
|[<span data-ttu-id="866a2-120">記憶體中的 OLTP 記憶體回收</span><span class="sxs-lookup"><span data-stu-id="866a2-120">In-Memory OLTP Garbage Collection</span></span>](../relational-databases/in-memory-oltp/in-memory-oltp-garbage-collection.md)|<span data-ttu-id="866a2-121">了解如何對已刪除的資料列進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="866a2-121">Understand how garbage collection operates on deleted rows.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="866a2-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="866a2-122">See Also</span></span>  
 [<span data-ttu-id="866a2-123">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="866a2-123">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
