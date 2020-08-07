---
title: MSSQLSERVER_8645 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8645 (Database Engine error)
ms.assetid: 63d6d6d7-3850-4061-8e96-b1fa665e3180
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7be9774452e2008c34ecb52d228a0123992c5368
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597856"
---
# <a name="mssqlserver_8645"></a><span data-ttu-id="12482-102">MSSQLSERVER_8645</span><span class="sxs-lookup"><span data-stu-id="12482-102">MSSQLSERVER_8645</span></span>
    
## <a name="details"></a><span data-ttu-id="12482-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="12482-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="12482-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="12482-104">Product Name</span></span>|<span data-ttu-id="12482-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="12482-105">SQL Server</span></span>|  
|<span data-ttu-id="12482-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="12482-106">Event ID</span></span>|<span data-ttu-id="12482-107">8645</span><span class="sxs-lookup"><span data-stu-id="12482-107">8645</span></span>|  
|<span data-ttu-id="12482-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="12482-108">Event Source</span></span>|<span data-ttu-id="12482-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="12482-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="12482-110">元件</span><span class="sxs-lookup"><span data-stu-id="12482-110">Component</span></span>|<span data-ttu-id="12482-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="12482-111">SQLEngine</span></span>|  
|<span data-ttu-id="12482-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="12482-112">Symbolic Name</span></span>|<span data-ttu-id="12482-113">MEMTIMEDOUT_ERR</span><span class="sxs-lookup"><span data-stu-id="12482-113">MEMTIMEDOUT_ERR</span></span>|  
|<span data-ttu-id="12482-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="12482-114">Message Text</span></span>|<span data-ttu-id="12482-115">等候記憶體資源來執行查詢時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="12482-115">A time out occurred while waiting for memory resources to execute the query.</span></span> <span data-ttu-id="12482-116">請重新執行查詢。</span><span class="sxs-lookup"><span data-stu-id="12482-116">Rerun the query.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="12482-117">說明</span><span class="sxs-lookup"><span data-stu-id="12482-117">Explanation</span></span>  
 <span data-ttu-id="12482-118">等候記憶體資源來執行資源集區 'default' 中的查詢時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="12482-118">A timeout occurred while waiting for memory resources to execute the query in the resource pool 'default'.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="12482-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="12482-119">User Action</span></span>  
 <span data-ttu-id="12482-120">如果您未使用資源管理員，我們建議您對整個伺服器狀態和負載進行驗證，或者檢查資源集區或工作負載群組設定。</span><span class="sxs-lookup"><span data-stu-id="12482-120">If you are not using Resource Governor, we recommend that you verify the overall server state and load, or check the resource pool or workload group settings.</span></span>  
  
 <span data-ttu-id="12482-121">下列清單概述有助於疑難排解記憶體錯誤的一般步驟：</span><span class="sxs-lookup"><span data-stu-id="12482-121">The following list outlines general steps that will help in troubleshooting memory errors:</span></span>  
  
1.  <span data-ttu-id="12482-122">確認是否有其他應用程式或服務正在耗用此伺服器的記憶體。</span><span class="sxs-lookup"><span data-stu-id="12482-122">Verify whether other applications or services are consuming memory on this server.</span></span> <span data-ttu-id="12482-123">重新設定比較不重要的應用程式或服務，以降低其記憶體耗用量。</span><span class="sxs-lookup"><span data-stu-id="12482-123">Reconfigure less critical applications or services to consume less memory.</span></span>  
  
2.  <span data-ttu-id="12482-124">開始收集下列項目的效能監視器計數：**SQL Server：緩衝區管理員**、**SQL Server：記憶體管理員**。</span><span class="sxs-lookup"><span data-stu-id="12482-124">Start collecting performance monitor counters for **SQL Server: Buffer Manager**, **SQL Server: Memory Manager**.</span></span>  
  
3.  <span data-ttu-id="12482-125">檢查下列 SQL Server 記憶體組態參數：</span><span class="sxs-lookup"><span data-stu-id="12482-125">Check the following SQL Server memory configuration parameters:</span></span>  
  
    -   <span data-ttu-id="12482-126">**max server memory**</span><span class="sxs-lookup"><span data-stu-id="12482-126">**max server memory**</span></span>  
  
    -   <span data-ttu-id="12482-127">**min server memory**</span><span class="sxs-lookup"><span data-stu-id="12482-127">**min server memory**</span></span>  
  
    -   <span data-ttu-id="12482-128">**min memory per query**</span><span class="sxs-lookup"><span data-stu-id="12482-128">**min memory per query**</span></span>  
  
     <span data-ttu-id="12482-129">注意不尋常的設定，</span><span class="sxs-lookup"><span data-stu-id="12482-129">Notice unusual settings.</span></span> <span data-ttu-id="12482-130">並且視需要加以更正。</span><span class="sxs-lookup"><span data-stu-id="12482-130">Correct them as necessary.</span></span> <span data-ttu-id="12482-131">說明 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的增加記憶體需求。</span><span class="sxs-lookup"><span data-stu-id="12482-131">Account for increased memory requirements for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="12482-132">預設值列於《SQL Server 線上叢書》中的＜設定伺服器組態選項＞。</span><span class="sxs-lookup"><span data-stu-id="12482-132">Default settings are listed in "Setting Server Configuration Options" in SQL Server Books Online.</span></span>  
  
4.  <span data-ttu-id="12482-133">當您看到這些錯誤訊息時，請觀察 DBCC MEMORYSTATUS 輸出以及它變更的方式。</span><span class="sxs-lookup"><span data-stu-id="12482-133">Observe DBCC MEMORYSTATUS output and the way it changes when you see these error messages.</span></span>  
  
5.  <span data-ttu-id="12482-134">檢查工作負載 (例如，並行工作階段的數目以及目前正在執行的查詢數)。</span><span class="sxs-lookup"><span data-stu-id="12482-134">Check the workload (for example, number of concurrent sessions, currently executing queries).</span></span>  
  
 <span data-ttu-id="12482-135">下列動作可以為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供更多可用的記憶體：</span><span class="sxs-lookup"><span data-stu-id="12482-135">The following actions may make more memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="12482-136">如果有 SQL Server 以外的應用程式正在耗用資源，請嘗試停止執行這些應用程式或考慮在不同的伺服器上執行這些應用程式。</span><span class="sxs-lookup"><span data-stu-id="12482-136">If applications besides SQL Server are consuming resources, try stopping running these applications or consider running them on a separate server.</span></span> <span data-ttu-id="12482-137">這將會移除外部的記憶體壓力。</span><span class="sxs-lookup"><span data-stu-id="12482-137">This will remove external memory pressure.</span></span>  
  
-   <span data-ttu-id="12482-138">如果已經設定 **max server memory,** ，請增加其設定值。</span><span class="sxs-lookup"><span data-stu-id="12482-138">If you have configured **max server memory,** increase its setting.</span></span>  
  
 <span data-ttu-id="12482-139">執行下列 DBCC 命令，以釋放數個 SQL Server 記憶體快取。</span><span class="sxs-lookup"><span data-stu-id="12482-139">Run the following DBCC commands to free several SQL Server memory caches.</span></span>  
  
-   <span data-ttu-id="12482-140">DBCC FREESYSTEMCACHE</span><span class="sxs-lookup"><span data-stu-id="12482-140">DBCC FREESYSTEMCACHE</span></span>  
  
-   <span data-ttu-id="12482-141">DBCC FREESESSIONCACHE</span><span class="sxs-lookup"><span data-stu-id="12482-141">DBCC FREESESSIONCACHE</span></span>  
  
-   <span data-ttu-id="12482-142">DBCC FREEPROCCACHE</span><span class="sxs-lookup"><span data-stu-id="12482-142">DBCC FREEPROCCACHE</span></span>  
  
 <span data-ttu-id="12482-143">如果仍繼續發生該問題，您必須進一步研究，而且可能必須降低工作負載。</span><span class="sxs-lookup"><span data-stu-id="12482-143">If the problem continues, you will need to investigate further and possibly reduce workload.</span></span>  
  
  
