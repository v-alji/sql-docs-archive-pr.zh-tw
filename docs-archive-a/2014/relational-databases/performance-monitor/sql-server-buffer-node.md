---
title: SQL Server:Buffer Node | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Buffer Node
- Buffer Node object
ms.assetid: fd3f9f0f-7c38-4cfd-a0c5-ee93dd52d9a5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 14659e4c1191e2260bccdbcd612f510770913629
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598817"
---
# <a name="sql-serverbuffer-node"></a><span data-ttu-id="d5e4a-102">SQL Server:Buffer Node</span><span class="sxs-lookup"><span data-stu-id="d5e4a-102">SQL Server:Buffer Node</span></span>
  <span data-ttu-id="d5e4a-103">**Buffer Node** 物件提供用來補充 **Buffer Manager** 物件所提供之計數器的計數器。</span><span class="sxs-lookup"><span data-stu-id="d5e4a-103">The **Buffer Node** object provides counters that complement counters provided by the **Buffer Manager** object.</span></span> <span data-ttu-id="d5e4a-104">它可讓您監視每個非統一記憶體存取 (NUMA) 節點的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 緩衝集區頁面散發。</span><span class="sxs-lookup"><span data-stu-id="d5e4a-104">It allows you to monitor the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] buffer pool page distribution for each non-uniform memory access (NUMA) node.</span></span> <span data-ttu-id="d5e4a-105">每個 NUMA 節點都會使用 **Buffer Node** 物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="d5e4a-105">There is an instance of the **Buffer Node** object for each NUMA node in use.</span></span> <span data-ttu-id="d5e4a-106">在非 NUMA 架構上，會有單一 **Buffer Node** 物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d5e4a-106">On non-NUMA architecture, there will be a single instance of the **Buffer Node** object.</span></span>  
  
## <a name="buffer-node-performance-objects"></a><span data-ttu-id="d5e4a-107">Buffer Node 效能物件</span><span class="sxs-lookup"><span data-stu-id="d5e4a-107">Buffer Node Performance Objects</span></span>  
 <span data-ttu-id="d5e4a-108">下表描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Buffer Node** 效能物件。</span><span class="sxs-lookup"><span data-stu-id="d5e4a-108">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Buffer Node** performance objects.</span></span>  
  
|<span data-ttu-id="d5e4a-109">SQL Server Buffer Node 計數器</span><span class="sxs-lookup"><span data-stu-id="d5e4a-109">SQL Server Buffer Node counters</span></span>|<span data-ttu-id="d5e4a-110">描述</span><span class="sxs-lookup"><span data-stu-id="d5e4a-110">Description</span></span>|  
|-------------------------------------|-----------------|  
|<span data-ttu-id="d5e4a-111">**Database pages**</span><span class="sxs-lookup"><span data-stu-id="d5e4a-111">**Database pages**</span></span>|<span data-ttu-id="d5e4a-112">指出在這個具有資料庫內容之節點上的緩衝集區頁面數。</span><span class="sxs-lookup"><span data-stu-id="d5e4a-112">Indicates the number of pages in the buffer pool on this node with database content.</span></span>|  
|<span data-ttu-id="d5e4a-113">**Page life expectancy**</span><span class="sxs-lookup"><span data-stu-id="d5e4a-113">**Page life expectancy**</span></span>|<span data-ttu-id="d5e4a-114">指出頁面停留在這個沒有參考之節點的緩衝集區中的秒數下限。</span><span class="sxs-lookup"><span data-stu-id="d5e4a-114">Indicates the minimum number of seconds a page will stay in the buffer pool on this node without references.</span></span>|  
|<span data-ttu-id="d5e4a-115">**Local Node page lookups/sec**</span><span class="sxs-lookup"><span data-stu-id="d5e4a-115">**Local Node page lookups/sec**</span></span>|<span data-ttu-id="d5e4a-116">指出來自這個節點而且由這個節點滿足的查閱要求數目。</span><span class="sxs-lookup"><span data-stu-id="d5e4a-116">Indicates the number of lookup requests from this node which were satisfied from this node.</span></span>|  
|<span data-ttu-id="d5e4a-117">**Remote Note page lookups/sec**</span><span class="sxs-lookup"><span data-stu-id="d5e4a-117">**Remote Note page lookups/sec**</span></span>|<span data-ttu-id="d5e4a-118">指出來自這個節點但是由其他節點滿足的查閱要求數目。</span><span class="sxs-lookup"><span data-stu-id="d5e4a-118">Indicates the number of lookup requests from this node which were satisfied from other nodes.</span></span>|  
  
 <span data-ttu-id="d5e4a-119">如果 SQL Server 是在非 NUMA 硬體上執行，則 **Buffer Node** 和 **Buffer Manager** 物件的計數器應該相符。</span><span class="sxs-lookup"><span data-stu-id="d5e4a-119">If SQL Server is running on non-NUMA hardware, the counters of **Buffer Node** and **Buffer Manager** objects should match.</span></span>  
  
 <span data-ttu-id="d5e4a-120">在 NUMA 硬體上，所有 **Buffer Nodes** 之對應計數器的總和應符合它們與 **Buffer Manager**的對應計數器總和。</span><span class="sxs-lookup"><span data-stu-id="d5e4a-120">On NUMA hardware, sums of respective counters of all **Buffer Nodes** should match their counterparts of **Buffer Manager**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d5e4a-121">因為受限於計數器的動態本質和取樣精確度，所以計數器值和總和可能不會完全相符。</span><span class="sxs-lookup"><span data-stu-id="d5e4a-121">The counter values and sums may not match precisely due to the dynamic nature of the counters and the sampling accuracy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5e4a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5e4a-122">See Also</span></span>  
 <span data-ttu-id="d5e4a-123">[SQL Server 的 Buffer Manager 物件](sql-server-buffer-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="d5e4a-123">[SQL Server, Buffer Manager Object](sql-server-buffer-manager-object.md) </span></span>  
 <span data-ttu-id="d5e4a-124">[伺服器記憶體伺服器組態選項](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span><span class="sxs-lookup"><span data-stu-id="d5e4a-124">[Server Memory Server Configuration Options](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span></span>  
 <span data-ttu-id="d5e4a-125">[監視資源使用量 &#40;系統監視器&#41;](monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="d5e4a-125">[Monitor Resource Usage &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md) </span></span>  
 [<span data-ttu-id="d5e4a-126">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d5e4a-126">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
