---
title: MSSQLSERVER_8651 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8651 (Database Engine error)
ms.assetid: 4cc3498d-5449-4c4e-b1f9-3271831c725a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 43a385350a05edee3759ab83d318e365f5b4f3e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698233"
---
# <a name="mssqlserver_8651"></a><span data-ttu-id="8ecf4-102">MSSQLSERVER_8651</span><span class="sxs-lookup"><span data-stu-id="8ecf4-102">MSSQLSERVER_8651</span></span>
    
## <a name="details"></a><span data-ttu-id="8ecf4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8ecf4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8ecf4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8ecf4-104">Product Name</span></span>|<span data-ttu-id="8ecf4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8ecf4-105">SQL Server</span></span>|  
|<span data-ttu-id="8ecf4-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8ecf4-106">Event ID</span></span>|<span data-ttu-id="8ecf4-107">8651</span><span class="sxs-lookup"><span data-stu-id="8ecf4-107">8651</span></span>|  
|<span data-ttu-id="8ecf4-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="8ecf4-108">Event Source</span></span>|<span data-ttu-id="8ecf4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8ecf4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8ecf4-110">元件</span><span class="sxs-lookup"><span data-stu-id="8ecf4-110">Component</span></span>|<span data-ttu-id="8ecf4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8ecf4-111">SQLEngine</span></span>|  
|<span data-ttu-id="8ecf4-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8ecf4-112">Symbolic Name</span></span>|<span data-ttu-id="8ecf4-113">MEMGRANT_ERR</span><span class="sxs-lookup"><span data-stu-id="8ecf4-113">MEMGRANT_ERR</span></span>|  
|<span data-ttu-id="8ecf4-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8ecf4-114">Message Text</span></span>|<span data-ttu-id="8ecf4-115">無法進行要求的作業，因為最小的查詢記憶體無法使用。</span><span class="sxs-lookup"><span data-stu-id="8ecf4-115">Could not perform the requested operation because the minimum query memory is not available.</span></span> <span data-ttu-id="8ecf4-116">請降低 'min memory per query' 伺服器設定選項的設定值。</span><span class="sxs-lookup"><span data-stu-id="8ecf4-116">Decrease the configured value for the 'min memory per query' server configuration option.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8ecf4-117">說明</span><span class="sxs-lookup"><span data-stu-id="8ecf4-117">Explanation</span></span>  
 <span data-ttu-id="8ecf4-118">有其他處理序正在耗用伺服器記憶體 (造成伺服器的記憶體壓力)。</span><span class="sxs-lookup"><span data-stu-id="8ecf4-118">Other processes are consuming server memory (exerting memory pressure in the server).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8ecf4-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8ecf4-119">User Action</span></span>  
 <span data-ttu-id="8ecf4-120">減少 'min memory per query' 伺服器組態選項的值，或減少伺服器的查詢負載。</span><span class="sxs-lookup"><span data-stu-id="8ecf4-120">Either decrease the configured value for the min memory per query' server configuration option or reduce the query load to the server.</span></span>  
  
 <span data-ttu-id="8ecf4-121">下列清單概述有助於疑難排解記憶體錯誤的一般步驟：</span><span class="sxs-lookup"><span data-stu-id="8ecf4-121">The following list outlines general steps that will help in troubleshooting memory errors:</span></span>  
  
1.  <span data-ttu-id="8ecf4-122">確認是否有其他應用程式或服務正在耗用此伺服器的記憶體。</span><span class="sxs-lookup"><span data-stu-id="8ecf4-122">Verify whether other applications or services are consuming memory on this server.</span></span> <span data-ttu-id="8ecf4-123">重新設定比較不重要的應用程式或服務，以降低其記憶體耗用量。</span><span class="sxs-lookup"><span data-stu-id="8ecf4-123">Reconfigure less critical applications or services to consume less memory.</span></span>  
  
2.  <span data-ttu-id="8ecf4-124">開始收集下列項目的效能監視器計數：**SQL Server：緩衝區管理員**、**SQL Server：記憶體管理員**。</span><span class="sxs-lookup"><span data-stu-id="8ecf4-124">Start collecting performance monitor counters for **SQL Server: Buffer Manager**, **SQL Server: Memory Manager**.</span></span>  
  
3.  <span data-ttu-id="8ecf4-125">檢查下列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記憶體組態參數：</span><span class="sxs-lookup"><span data-stu-id="8ecf4-125">Check the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory configuration parameters:</span></span>  
  
    -   <span data-ttu-id="8ecf4-126">**max server memory**</span><span class="sxs-lookup"><span data-stu-id="8ecf4-126">**max server memory**</span></span>  
  
    -   <span data-ttu-id="8ecf4-127">**min server memory**</span><span class="sxs-lookup"><span data-stu-id="8ecf4-127">**min server memory**</span></span>  
  
    -   <span data-ttu-id="8ecf4-128">**min memory per query**</span><span class="sxs-lookup"><span data-stu-id="8ecf4-128">**min memory per query**</span></span>  
  
     <span data-ttu-id="8ecf4-129">注意不尋常的設定，</span><span class="sxs-lookup"><span data-stu-id="8ecf4-129">Notice unusual settings.</span></span> <span data-ttu-id="8ecf4-130">並且視需要加以更正。</span><span class="sxs-lookup"><span data-stu-id="8ecf4-130">Correct them as necessary.</span></span> <span data-ttu-id="8ecf4-131">預設值列於《SQL Server 線上叢書》中的＜設定伺服器組態選項＞。</span><span class="sxs-lookup"><span data-stu-id="8ecf4-131">Default settings are listed in "Setting Server Configuration Options" in SQL Server Books Online.</span></span>  
  
4.  <span data-ttu-id="8ecf4-132">檢查工作負載 (例如，並行工作階段的數目以及目前正在執行的查詢數)。</span><span class="sxs-lookup"><span data-stu-id="8ecf4-132">Check the workload (for example, number of concurrent sessions, currently executing queries).</span></span>  
  
 <span data-ttu-id="8ecf4-133">下列動作可以為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供更多可用的記憶體：</span><span class="sxs-lookup"><span data-stu-id="8ecf4-133">The following actions may make more memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="8ecf4-134">如果有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外的應用程式正在耗用資源，請嘗試停止執行這些應用程式或考慮在不同的伺服器上執行這些應用程式。</span><span class="sxs-lookup"><span data-stu-id="8ecf4-134">If applications besides [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are consuming resources, try stopping running these applications or consider running them on a separate server.</span></span> <span data-ttu-id="8ecf4-135">這將會移除外部的記憶體壓力。</span><span class="sxs-lookup"><span data-stu-id="8ecf4-135">This will remove external memory pressure.</span></span>  
  
-   <span data-ttu-id="8ecf4-136">如果已經設定 **max server memory,** ，請增加其設定值。</span><span class="sxs-lookup"><span data-stu-id="8ecf4-136">If you have configured **max server memory,** increase its setting.</span></span>  
  
 <span data-ttu-id="8ecf4-137">執行下列 DBCC 命令，以便釋放數個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記憶體快取。</span><span class="sxs-lookup"><span data-stu-id="8ecf4-137">Run the following DBCC commands to free several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory caches.</span></span>  
  
-   <span data-ttu-id="8ecf4-138">DBCC FREESYSTEMCACHE</span><span class="sxs-lookup"><span data-stu-id="8ecf4-138">DBCC FREESYSTEMCACHE</span></span>  
  
-   <span data-ttu-id="8ecf4-139">DBCC FREESESSIONCACHE</span><span class="sxs-lookup"><span data-stu-id="8ecf4-139">DBCC FREESESSIONCACHE</span></span>  
  
-   <span data-ttu-id="8ecf4-140">DBCC FREEPROCCACHE</span><span class="sxs-lookup"><span data-stu-id="8ecf4-140">DBCC FREEPROCCACHE</span></span>  
  
 <span data-ttu-id="8ecf4-141">如果仍繼續發生該問題，您必須進一步研究，而且可能必須降低工作負載。</span><span class="sxs-lookup"><span data-stu-id="8ecf4-141">If the problem continues, you will need to investigate further and possibly reduce workload.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ecf4-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ecf4-142">See Also</span></span>  
 <span data-ttu-id="8ecf4-143">[DBCC FREESYSTEMCACHE &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-freesystemcache-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8ecf4-143">[DBCC FREESYSTEMCACHE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-freesystemcache-transact-sql) </span></span>  
 <span data-ttu-id="8ecf4-144">[DBCC FREESESSIONCACHE &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-freesessioncache-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8ecf4-144">[DBCC FREESESSIONCACHE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-freesessioncache-transact-sql) </span></span>  
 <span data-ttu-id="8ecf4-145">[DBCC FREEPROCCACHE &#40;Transact-sql&#41;](/sql/t-sql/database-console-commands/dbcc-freeproccache-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8ecf4-145">[DBCC FREEPROCCACHE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-freeproccache-transact-sql) </span></span>  
 <span data-ttu-id="8ecf4-146">[伺服器組態選項 &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8ecf4-146">[Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="8ecf4-147">[SQL Server 的 Buffer Manager 物件](../performance-monitor/sql-server-buffer-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="8ecf4-147">[SQL Server, Buffer Manager Object](../performance-monitor/sql-server-buffer-manager-object.md) </span></span>  
 [<span data-ttu-id="8ecf4-148">SQL Server 的 Memory Manager 物件</span><span class="sxs-lookup"><span data-stu-id="8ecf4-148">SQL Server, Memory Manager Object</span></span>](../performance-monitor/sql-server-memory-manager-object.md)  
  
  
