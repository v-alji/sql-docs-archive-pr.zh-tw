---
title: 監視記憶體使用量 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- tuning databases [SQL Server], memory
- monitoring server performance [SQL Server], memory usage
- isolating memory [SQL Server]
- paging rate [SQL Server]
- memory [SQL Server], monitoring usage
- monitoring [SQL Server], memory usage
- low-memory conditions
- database monitoring [SQL Server], memory usage
- available memory [SQL Server]
- page faults [SQL Server]
- monitoring performance [SQL Server], memory usage
- server performance [SQL Server], memory
ms.assetid: 1aee3933-a11c-4b87-91b7-32f5ea38c87f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1986d9576f9b067cad18f27d4febbf097ed52703
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707402"
---
# <a name="monitor-memory-usage"></a><span data-ttu-id="ba077-102">監視記憶體使用量</span><span class="sxs-lookup"><span data-stu-id="ba077-102">Monitor Memory Usage</span></span>
  <span data-ttu-id="ba077-103">定期監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，以確認記憶體使用量是在正常範圍內。</span><span class="sxs-lookup"><span data-stu-id="ba077-103">Monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] periodically to confirm that memory usage is within typical ranges.</span></span>  
  
 <span data-ttu-id="ba077-104">若要監視低記憶體的狀況，請使用以下物件計數器：</span><span class="sxs-lookup"><span data-stu-id="ba077-104">To monitor for a low-memory condition, use the following object counters:</span></span>  
  
-   <span data-ttu-id="ba077-105">**記憶體：Available Bytes**</span><span class="sxs-lookup"><span data-stu-id="ba077-105">**Memory: Available Bytes**</span></span>  
  
-   <span data-ttu-id="ba077-106">**記憶體：Pages/sec**</span><span class="sxs-lookup"><span data-stu-id="ba077-106">**Memory: Pages/sec**</span></span>  
  
 <span data-ttu-id="ba077-107">**Available Bytes** 計數器代表目前有多少記憶體位元組可供處理序使用。</span><span class="sxs-lookup"><span data-stu-id="ba077-107">The **Available Bytes** counter indicates how many bytes of memory are currently available for use by processes.</span></span> <span data-ttu-id="ba077-108">**Pages/sec** 計數器會顯示由於硬體分頁錯誤而自磁碟取出，或由於分頁錯誤而寫入磁碟，以釋出工作集內空間的分頁數。</span><span class="sxs-lookup"><span data-stu-id="ba077-108">The **Pages/sec** counter indicates the number of pages that either were retrieved from disk due to hard page faults or written to disk to free space in the working set due to page faults.</span></span>  
  
 <span data-ttu-id="ba077-109">若 **Available Bytes** 計數器的數值偏低，代表電腦整體地缺乏記憶體，或有某個應用程式沒有釋出記憶體。</span><span class="sxs-lookup"><span data-stu-id="ba077-109">Low values for the **Available Bytes** counter can indicate that there is an overall shortage of memory on the computer or that an application is not releasing memory.</span></span> <span data-ttu-id="ba077-110">**Pages/sec** 計數器數值過高可能代表過度分頁。</span><span class="sxs-lookup"><span data-stu-id="ba077-110">A high rate for the **Pages/sec** counter could indicate excessive paging.</span></span> <span data-ttu-id="ba077-111">監視**記憶體：Page Faults/sec** 計數器可確認磁碟活動並非分頁所造成。</span><span class="sxs-lookup"><span data-stu-id="ba077-111">Monitor the **Memory: Page Faults/sec** counter to make sure that the disk activity is not caused by paging.</span></span>  
  
 <span data-ttu-id="ba077-112">分頁率 (連同分頁錯誤) 低是正常的，即使有許多可用記憶體的電腦也是如此。</span><span class="sxs-lookup"><span data-stu-id="ba077-112">A low rate of paging (and hence page faults) is typical, even if the computer has plenty of available memory.</span></span> <span data-ttu-id="ba077-113">當「Microsoft Windows 虛擬記憶體管理員 (VMM)」修剪 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和其他處理序的工作集大小時，它會從這些處理序取得分頁。</span><span class="sxs-lookup"><span data-stu-id="ba077-113">The Microsoft Windows Virtual Memory Manager (VMM) takes pages from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and other processes as it trims the working-set sizes of those processes.</span></span> <span data-ttu-id="ba077-114">此 VMM 活動會造成分頁錯誤。</span><span class="sxs-lookup"><span data-stu-id="ba077-114">This VMM activity tends to cause page faults.</span></span> <span data-ttu-id="ba077-115">若要判斷 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或其他處理序是否為過度分頁的原因，您可以監視**處理序：Page Faults/sec** 計數器 (針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序執行個體)。</span><span class="sxs-lookup"><span data-stu-id="ba077-115">To determine whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or another process is the cause of excessive paging, monitor the **Process: Page Faults/sec** counter for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process instance.</span></span>  
  
 <span data-ttu-id="ba077-116">如需有關解決過度分頁的詳細資訊，請參閱 Windows 作業系統文件。</span><span class="sxs-lookup"><span data-stu-id="ba077-116">For more information about resolving excessive paging, see the Windows operating system documentation.</span></span>  
  
## <a name="isolating-memory-used-by-sql-server"></a><span data-ttu-id="ba077-117">隔離 SQL Server 所使用的記憶體</span><span class="sxs-lookup"><span data-stu-id="ba077-117">Isolating Memory Used by SQL Server</span></span>  
 <span data-ttu-id="ba077-118">根據預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會根據可用的系統資源，動態變更它的記憶體需求。</span><span class="sxs-lookup"><span data-stu-id="ba077-118">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] changes its memory requirements dynamically, on the basis of available system resources.</span></span> <span data-ttu-id="ba077-119">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 需要更多記憶體，它將詢問作業系統以判斷是否有可用的實體記憶體，並使用可用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="ba077-119">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] needs more memory, it queries the operating system to determine whether free physical memory is available and uses the available memory.</span></span> <span data-ttu-id="ba077-120">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 並不需要目前配置給它的記憶體，它會釋出記憶體給作業系統。</span><span class="sxs-lookup"><span data-stu-id="ba077-120">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not need the memory currently allocated to it, it releases the memory to the operating system.</span></span> <span data-ttu-id="ba077-121">不過，您可以使用 **minservermemory**和 **maxservermemory** 伺服器組態選項，覆寫選項以動態使用記憶體。</span><span class="sxs-lookup"><span data-stu-id="ba077-121">However, you can override the option to dynamically use memory by using the **minservermemory**, and **maxservermemory** server configuration options.</span></span> <span data-ttu-id="ba077-122">如需詳細資訊，請參閱＜ [伺服器記憶體選項](../../database-engine/configure-windows/server-memory-server-configuration-options.md)＞。</span><span class="sxs-lookup"><span data-stu-id="ba077-122">For more information, see [Server Memory Options](../../database-engine/configure-windows/server-memory-server-configuration-options.md).</span></span>  
  
 <span data-ttu-id="ba077-123">若要監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所使用的記憶體數量，請檢查下列效能計數器：</span><span class="sxs-lookup"><span data-stu-id="ba077-123">To monitor the amount of memory that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses, examine the following performance counters:</span></span>  
  
-   <span data-ttu-id="ba077-124">**處理序：Working Set**</span><span class="sxs-lookup"><span data-stu-id="ba077-124">**Process: Working Set**</span></span>  
  
-   <span data-ttu-id="ba077-125">**SQL Server：緩衝區管理員：Buffer Cache Hit Ratio**</span><span class="sxs-lookup"><span data-stu-id="ba077-125">**SQL Server: Buffer Manager: Buffer Cache Hit Ratio**</span></span>  
  
-   <span data-ttu-id="ba077-126">**SQL Server：緩衝區管理員：Database Pages**</span><span class="sxs-lookup"><span data-stu-id="ba077-126">**SQL Server: Buffer Manager: Database Pages**</span></span>  
  
-   <span data-ttu-id="ba077-127">**SQL Server：記憶體管理員：Total Server Memory (KB)**</span><span class="sxs-lookup"><span data-stu-id="ba077-127">**SQL Server: Memory Manager: Total Server Memory (KB)**</span></span>  
  
 <span data-ttu-id="ba077-128">**WorkingSet** 計數器顯示處理序使用的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="ba077-128">The **WorkingSet** counter shows the amount of memory that is used by a process.</span></span> <span data-ttu-id="ba077-129">如果這個數字一直低於 **「最小伺服器記憶體」** 與 **「最大伺服器記憶體」** 伺服器選項設定的記憶體數量，則代表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設定的記憶體過多。</span><span class="sxs-lookup"><span data-stu-id="ba077-129">If this number is consistently below the amount of memory that is set by the **min server memory** and **max server memory** server options, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to use too much memory.</span></span>  
  
 <span data-ttu-id="ba077-130">**Buffer Cache Hit Ratio** 計數器專供應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="ba077-130">The **Buffer Cache Hit Ratio** counter is specific to an application.</span></span> <span data-ttu-id="ba077-131">不過，其數值最好為 90% 或更高。</span><span class="sxs-lookup"><span data-stu-id="ba077-131">However, a rate of 90 percent or higher is desirable.</span></span> <span data-ttu-id="ba077-132">請持續增加記憶體，直到該數值持續大於 90%。</span><span class="sxs-lookup"><span data-stu-id="ba077-132">Add more memory until the value is consistently greater than 90 percent.</span></span> <span data-ttu-id="ba077-133">數值大於 90% 代表有超過 90% 的資料要求，可自資料快取中得到所需的資料。</span><span class="sxs-lookup"><span data-stu-id="ba077-133">A value greater than 90 percent indicates that more than 90 percent of all requests for data were satisfied from the data cache.</span></span>  
  
 <span data-ttu-id="ba077-134">若 **TotalServerMemory (KB)** 計數器和電腦中的實體記憶體數量相比一直很高，可能代表需要更多的記憶體。</span><span class="sxs-lookup"><span data-stu-id="ba077-134">If the **TotalServerMemory (KB)** counter is consistently high compared to the amount of physical memory in the computer, it may indicate that more memory is required.</span></span>  
  
## <a name="determining-current-memory-allocation"></a><span data-ttu-id="ba077-135">決定目前的記憶體配置</span><span class="sxs-lookup"><span data-stu-id="ba077-135">Determining Current Memory Allocation</span></span>  
 <span data-ttu-id="ba077-136">以下查詢會傳回目前配置之記憶體的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ba077-136">The following query returns information about currently allocated memory.</span></span>  
  
```  
SELECT  
(physical_memory_in_use_kb/1024) AS Memory_usedby_Sqlserver_MB,  
(locked_page_allocations_kb/1024) AS Locked_pages_used_Sqlserver_MB,  
(total_virtual_address_space_kb/1024) AS Total_VAS_in_MB,  
process_physical_memory_low,  
process_virtual_memory_low  
FROM sys.dm_os_process_memory;  
```  
  
  
