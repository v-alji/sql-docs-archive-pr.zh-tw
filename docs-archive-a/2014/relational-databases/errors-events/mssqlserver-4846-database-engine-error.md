---
title: MSSQLSERVER_4846 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 4846 (Database Engine error)
ms.assetid: a455e809-1883-4c7d-b3e3-835ee5bfe258
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 923137645aae72476fb4b2ae33f0cbbf3e81c2a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698242"
---
# <a name="mssqlserver_4846"></a><span data-ttu-id="b13b2-102">MSSQLSERVER_4846</span><span class="sxs-lookup"><span data-stu-id="b13b2-102">MSSQLSERVER_4846</span></span>
    
## <a name="details"></a><span data-ttu-id="b13b2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b13b2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b13b2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b13b2-104">Product Name</span></span>|<span data-ttu-id="b13b2-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b13b2-105">SQL Server</span></span>|  
|<span data-ttu-id="b13b2-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b13b2-106">Event ID</span></span>|<span data-ttu-id="b13b2-107">4846</span><span class="sxs-lookup"><span data-stu-id="b13b2-107">4846</span></span>|  
|<span data-ttu-id="b13b2-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="b13b2-108">Event Source</span></span>|<span data-ttu-id="b13b2-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b13b2-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b13b2-110">元件</span><span class="sxs-lookup"><span data-stu-id="b13b2-110">Component</span></span>|<span data-ttu-id="b13b2-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b13b2-111">SQLEngine</span></span>|  
|<span data-ttu-id="b13b2-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b13b2-112">Symbolic Name</span></span>|<span data-ttu-id="b13b2-113">BULKPROV_MEMORY</span><span class="sxs-lookup"><span data-stu-id="b13b2-113">BULKPROV_MEMORY</span></span>|  
|<span data-ttu-id="b13b2-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b13b2-114">Message Text</span></span>|<span data-ttu-id="b13b2-115">大量資料提供者無法配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="b13b2-115">The bulk data provider failed to allocate memory.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b13b2-116">說明</span><span class="sxs-lookup"><span data-stu-id="b13b2-116">Explanation</span></span>  
 <span data-ttu-id="b13b2-117">記憶體配置失敗。</span><span class="sxs-lookup"><span data-stu-id="b13b2-117">Memory allocation failed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b13b2-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b13b2-118">User Action</span></span>  
 <span data-ttu-id="b13b2-119">請遵循下列一般步驟以疑難排解記憶體錯誤：</span><span class="sxs-lookup"><span data-stu-id="b13b2-119">Follow these general steps to troubleshoot memory errors:</span></span>  
  
1.  <span data-ttu-id="b13b2-120">確認是否有其他應用程式或服務正在耗用此伺服器的記憶體。</span><span class="sxs-lookup"><span data-stu-id="b13b2-120">Verify whether other applications or services are consuming memory on this server.</span></span> <span data-ttu-id="b13b2-121">重新設定比較不重要的應用程式或服務，以降低其記憶體耗用量。</span><span class="sxs-lookup"><span data-stu-id="b13b2-121">Reconfigure less critical applications or services to consume less memory.</span></span>  
  
2.  <span data-ttu-id="b13b2-122">開始收集下列項目的效能監視器計數：**SQL Server：緩衝區管理員**、**SQL Server：記憶體管理員**。</span><span class="sxs-lookup"><span data-stu-id="b13b2-122">Start collecting performance monitor counters for **SQL Server: Buffer Manager**, **SQL Server: Memory Manager**.</span></span>  
  
3.  <span data-ttu-id="b13b2-123">檢查下列 SQL Server 記憶體組態參數：</span><span class="sxs-lookup"><span data-stu-id="b13b2-123">Check the following SQL Server memory configuration parameters:</span></span>  
  
    -   <span data-ttu-id="b13b2-124">**max server memory**</span><span class="sxs-lookup"><span data-stu-id="b13b2-124">**max server memory**</span></span>  
  
    -   <span data-ttu-id="b13b2-125">**min server memory**</span><span class="sxs-lookup"><span data-stu-id="b13b2-125">**min server memory**</span></span>  
  
    -   <span data-ttu-id="b13b2-126">**min memory per query**</span><span class="sxs-lookup"><span data-stu-id="b13b2-126">**min memory per query**</span></span>  
  
     <span data-ttu-id="b13b2-127">注意不尋常的設定，</span><span class="sxs-lookup"><span data-stu-id="b13b2-127">Notice any unusual settings.</span></span> <span data-ttu-id="b13b2-128">並且視需要加以更正。</span><span class="sxs-lookup"><span data-stu-id="b13b2-128">Correct them as necessary.</span></span> <span data-ttu-id="b13b2-129">說明 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的記憶體需求。</span><span class="sxs-lookup"><span data-stu-id="b13b2-129">Account for memory requirements for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="b13b2-130">預設值列於《SQL Server 線上叢書》中的＜設定伺服器組態選項＞。</span><span class="sxs-lookup"><span data-stu-id="b13b2-130">Default settings are listed in "Setting Server Configuration Options" in SQL Server Books Online.</span></span>  
  
4.  <span data-ttu-id="b13b2-131">當您看到這些錯誤訊息時，請觀察 DBCC MEMORYSTATUS 輸出以及它變更的方式。</span><span class="sxs-lookup"><span data-stu-id="b13b2-131">Observe DBCC MEMORYSTATUS output and the way it changes when you see these error messages.</span></span>  
  
5.  <span data-ttu-id="b13b2-132">檢查工作負載 (例如，並行工作階段的數目以及目前正在執行的查詢數)。</span><span class="sxs-lookup"><span data-stu-id="b13b2-132">Check the workload (for example, number of concurrent sessions, currently executing queries).</span></span>  
  
 <span data-ttu-id="b13b2-133">下列動作可以為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供更多可用的記憶體：</span><span class="sxs-lookup"><span data-stu-id="b13b2-133">The following actions may make more memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="b13b2-134">如果有 SQL Server 以外的應用程式正在耗用資源，請嘗試停止執行這些應用程式或考慮在不同的伺服器上執行這些應用程式。</span><span class="sxs-lookup"><span data-stu-id="b13b2-134">If applications besides SQL Server are consuming resources, try stopping running these applications or consider running them on a separate server.</span></span> <span data-ttu-id="b13b2-135">這將會移除外部的記憶體壓力。</span><span class="sxs-lookup"><span data-stu-id="b13b2-135">This will remove external memory pressure.</span></span>  
  
-   <span data-ttu-id="b13b2-136">如果已經設定 **max server memory,** ，請增加其設定值。</span><span class="sxs-lookup"><span data-stu-id="b13b2-136">If you have configured **max server memory,** increase its setting.</span></span>  
  
 <span data-ttu-id="b13b2-137">執行下列 DBCC 命令，以便釋放數個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記憶體快取。</span><span class="sxs-lookup"><span data-stu-id="b13b2-137">Run the following DBCC commands to free several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory caches.</span></span>  
  
-   <span data-ttu-id="b13b2-138">DBCC FREESYSTEMCACHE</span><span class="sxs-lookup"><span data-stu-id="b13b2-138">DBCC FREESYSTEMCACHE</span></span>  
  
-   <span data-ttu-id="b13b2-139">DBCC FREESESSIONCACHE</span><span class="sxs-lookup"><span data-stu-id="b13b2-139">DBCC FREESESSIONCACHE</span></span>  
  
-   <span data-ttu-id="b13b2-140">DBCC FREEPROCCACHE</span><span class="sxs-lookup"><span data-stu-id="b13b2-140">DBCC FREEPROCCACHE</span></span>  
  
 <span data-ttu-id="b13b2-141">如果仍繼續發生該問題，您必須進一步研究，而且可能必須降低工作負載。</span><span class="sxs-lookup"><span data-stu-id="b13b2-141">If the problem continues, you will need to investigate further and possibly reduce workload.</span></span>  
  
  
