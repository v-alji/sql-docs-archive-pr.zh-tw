---
title: SQL Server 的 Memory Node | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d5bbc3f581ea9ececeb7d55a614ef27c3c72de7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606244"
---
# <a name="sql-server-memory-node"></a><span data-ttu-id="e65a4-102">SQL Server, Memory Node</span><span class="sxs-lookup"><span data-stu-id="e65a4-102">SQL Server, Memory Node</span></span>
  <span data-ttu-id="e65a4-103">Microsoft **中的** Memory Node [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件會提供計數器，可監視 NUMA 節點的伺服器記憶體使用狀況。</span><span class="sxs-lookup"><span data-stu-id="e65a4-103">The **Memory Node** object in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides counters to monitor server memory usage on NUMA nodes.</span></span>  
  
## <a name="memory-node-counters"></a><span data-ttu-id="e65a4-104">Memory Node 計數器</span><span class="sxs-lookup"><span data-stu-id="e65a4-104">Memory Node Counters</span></span>  
 <span data-ttu-id="e65a4-105">下表描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Memory Node** 計數器。</span><span class="sxs-lookup"><span data-stu-id="e65a4-105">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Memory Node** counters.</span></span>  
  
|<span data-ttu-id="e65a4-106">SQL Server Memory Manager 計數器</span><span class="sxs-lookup"><span data-stu-id="e65a4-106">SQL Server Memory Manager counters</span></span>|<span data-ttu-id="e65a4-107">描述</span><span class="sxs-lookup"><span data-stu-id="e65a4-107">Description</span></span>|  
|----------------------------------------|-----------------|  
|<span data-ttu-id="e65a4-108">**Database Node Memory (KB)**</span><span class="sxs-lookup"><span data-stu-id="e65a4-108">**Database Node Memory (KB)**</span></span>|<span data-ttu-id="e65a4-109">指定伺服器目前用於此節點之資料庫頁面的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="e65a4-109">Specifies the amount of memory the server is currently using on this node for database pages.</span></span>|  
|<span data-ttu-id="e65a4-110">**Free Node Memory (KB)**</span><span class="sxs-lookup"><span data-stu-id="e65a4-110">**Free Node Memory (KB)**</span></span>|<span data-ttu-id="e65a4-111">指定伺服器未用於此節點的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="e65a4-111">Specifies the amount of memory the server is not using on this node.</span></span>|  
|<span data-ttu-id="e65a4-112">**Foreign Node Memory (KB)**</span><span class="sxs-lookup"><span data-stu-id="e65a4-112">**Foreign Node Memory (KB)**</span></span>|<span data-ttu-id="e65a4-113">指定此節點上非 NUMA 本機記憶體的數量。</span><span class="sxs-lookup"><span data-stu-id="e65a4-113">Specifies the amount of non NUMA-local memory on this node.</span></span>|  
|<span data-ttu-id="e65a4-114">**Stolen Memory Node (KB)**</span><span class="sxs-lookup"><span data-stu-id="e65a4-114">**Stolen Memory Node (KB)**</span></span>|<span data-ttu-id="e65a4-115">指定伺服器用於此節點之資料庫頁面以外目的的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="e65a4-115">Specifies the amount of memory the server is using on this node for purposes other than database pages.</span></span>|  
|<span data-ttu-id="e65a4-116">**Target Node Memory**</span><span class="sxs-lookup"><span data-stu-id="e65a4-116">**Target Node Memory**</span></span>|<span data-ttu-id="e65a4-117">指定此節點的理想記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="e65a4-117">Specifies the ideal amount of memory for this node.</span></span>|  
|<span data-ttu-id="e65a4-118">**Total Node Memory**</span><span class="sxs-lookup"><span data-stu-id="e65a4-118">**Total Node Memory**</span></span>|<span data-ttu-id="e65a4-119">表示伺服器已在此節點上認可的記憶體總數。</span><span class="sxs-lookup"><span data-stu-id="e65a4-119">Indicates the total amount of memory the server has committed on this node.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e65a4-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e65a4-120">See Also</span></span>  
 <span data-ttu-id="e65a4-121">[監視資源使用量 &#40;系統監視器&#41;](monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="e65a4-121">[Monitor Resource Usage &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="e65a4-122">[SQL Server 的 Buffer Manager 物件](sql-server-buffer-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="e65a4-122">[SQL Server, Buffer Manager Object](sql-server-buffer-manager-object.md) </span></span>  
 [<span data-ttu-id="e65a4-123">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e65a4-123">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
