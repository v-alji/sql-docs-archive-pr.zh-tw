---
title: MSSQLSERVER_701 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 701 (Database Engine error)
ms.assetid: 3b975000-63a1-43c2-a40f-89d0a8a36bef
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 542535223d3e394c72079092411add143de61545
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594084"
---
# <a name="mssqlserver_701"></a><span data-ttu-id="43cff-102">MSSQLSERVER_701</span><span class="sxs-lookup"><span data-stu-id="43cff-102">MSSQLSERVER_701</span></span>
    
## <a name="details"></a><span data-ttu-id="43cff-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="43cff-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="43cff-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="43cff-104">Product Name</span></span>|<span data-ttu-id="43cff-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="43cff-105">SQL Server</span></span>|  
|<span data-ttu-id="43cff-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="43cff-106">Event ID</span></span>|<span data-ttu-id="43cff-107">701</span><span class="sxs-lookup"><span data-stu-id="43cff-107">701</span></span>|  
|<span data-ttu-id="43cff-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="43cff-108">Event Source</span></span>|<span data-ttu-id="43cff-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="43cff-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="43cff-110">元件</span><span class="sxs-lookup"><span data-stu-id="43cff-110">Component</span></span>|<span data-ttu-id="43cff-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="43cff-111">SQLEngine</span></span>|  
|<span data-ttu-id="43cff-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="43cff-112">Symbolic Name</span></span>|<span data-ttu-id="43cff-113">NOSYSMEM</span><span class="sxs-lookup"><span data-stu-id="43cff-113">NOSYSMEM</span></span>|  
|<span data-ttu-id="43cff-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="43cff-114">Message Text</span></span>|<span data-ttu-id="43cff-115">系統記憶體不足，無法執行此查詢。</span><span class="sxs-lookup"><span data-stu-id="43cff-115">There is insufficient system memory to run this query.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="43cff-116">說明</span><span class="sxs-lookup"><span data-stu-id="43cff-116">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="43cff-117">無法配置足夠的記憶體來執行查詢。</span><span class="sxs-lookup"><span data-stu-id="43cff-117">has failed to allocate sufficient memory to run the query.</span></span> <span data-ttu-id="43cff-118">有各種原因會造成此錯誤，包括作業系統設定、實體記憶體可用性或目前工作負載的記憶體限制。</span><span class="sxs-lookup"><span data-stu-id="43cff-118">This can be caused by a variety of reasons including operating system settings, physical memory availability, or memory limits on the current workload.</span></span> <span data-ttu-id="43cff-119">在大部分情況下，交易失敗並非造成此錯誤的原因。</span><span class="sxs-lookup"><span data-stu-id="43cff-119">In most cases, the transaction that failed is not the cause of this error.</span></span>  
  
 <span data-ttu-id="43cff-120">診斷查詢 (例如 DBCC 陳述式) 可能會因為伺服器記憶體不足而失敗。</span><span class="sxs-lookup"><span data-stu-id="43cff-120">Diagnostic queries, such as DBCC statements, may fail because server the does not have sufficient memory.</span></span>  
  
 <span data-ttu-id="43cff-121">等候記憶體資源來執行資源集區 'default' 中的查詢時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="43cff-121">A timeout occurred while waiting for memory resources to execute the query in the resource pool 'default'.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="43cff-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="43cff-122">User Action</span></span>  
 <span data-ttu-id="43cff-123">如果您未使用資源管理員，我們建議您對整個伺服器狀態和負載進行驗證，或者檢查資源集區或工作負載群組設定。</span><span class="sxs-lookup"><span data-stu-id="43cff-123">If you are not using Resource Governor, we recommend that you verify the overall server state and load, or check the resource pool or workload group settings.</span></span>  
  
 <span data-ttu-id="43cff-124">下列清單概述有助於疑難排解記憶體錯誤的一般步驟：</span><span class="sxs-lookup"><span data-stu-id="43cff-124">The following list outlines general steps that will help in troubleshooting memory errors:</span></span>  
  
1.  <span data-ttu-id="43cff-125">確認是否有其他應用程式或服務正在耗用此伺服器的記憶體。</span><span class="sxs-lookup"><span data-stu-id="43cff-125">Verify whether other applications or services are consuming memory on this server.</span></span> <span data-ttu-id="43cff-126">重新設定比較不重要的應用程式或服務，以降低其記憶體耗用量。</span><span class="sxs-lookup"><span data-stu-id="43cff-126">Reconfigure less critical applications or services to consume less memory.</span></span>  
  
2.  <span data-ttu-id="43cff-127">開始收集以下內容的效能監視器計數：[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **：緩衝區管理員**、**SQL Server：記憶體管理員**。</span><span class="sxs-lookup"><span data-stu-id="43cff-127">Start collecting performance monitor counters for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: Buffer Manager**, **SQL Server: Memory Manager**.</span></span>  
  
3.  <span data-ttu-id="43cff-128">檢查下列 SQL Server 記憶體組態參數：</span><span class="sxs-lookup"><span data-stu-id="43cff-128">Check the following SQL Server memory configuration parameters:</span></span>  
  
    -   <span data-ttu-id="43cff-129">**max server memory**</span><span class="sxs-lookup"><span data-stu-id="43cff-129">**max server memory**</span></span>  
  
    -   <span data-ttu-id="43cff-130">**min server memory**</span><span class="sxs-lookup"><span data-stu-id="43cff-130">**min server memory**</span></span>  
  
    -   <span data-ttu-id="43cff-131">**min memory per query**</span><span class="sxs-lookup"><span data-stu-id="43cff-131">**min memory per query**</span></span>  
  
     <span data-ttu-id="43cff-132">注意不尋常的設定，</span><span class="sxs-lookup"><span data-stu-id="43cff-132">Notice unusual settings.</span></span> <span data-ttu-id="43cff-133">並且視需要加以更正。</span><span class="sxs-lookup"><span data-stu-id="43cff-133">Correct them as necessary.</span></span> <span data-ttu-id="43cff-134">說明增加的記憶體需求。</span><span class="sxs-lookup"><span data-stu-id="43cff-134">Account for increased memory requirements.</span></span> <span data-ttu-id="43cff-135">預設值列於《SQL Server 線上叢書》中的＜設定伺服器組態選項＞。</span><span class="sxs-lookup"><span data-stu-id="43cff-135">Default settings are listed in "Setting Server Configuration Options" in SQL Server Books Online.</span></span>  
  
4.  <span data-ttu-id="43cff-136">當您看到這些錯誤訊息時，請觀察 DBCC MEMORYSTATUS 輸出以及它變更的方式。</span><span class="sxs-lookup"><span data-stu-id="43cff-136">Observe DBCC MEMORYSTATUS output and the way it changes when you see these error messages.</span></span>  
  
5.  <span data-ttu-id="43cff-137">檢查工作負載 (例如，並行工作階段的數目以及目前正在執行的查詢數)。</span><span class="sxs-lookup"><span data-stu-id="43cff-137">Check the workload (for example, number of concurrent sessions, currently executing queries).</span></span>  
  
 <span data-ttu-id="43cff-138">下列動作可以為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供更多可用的記憶體：</span><span class="sxs-lookup"><span data-stu-id="43cff-138">The following actions may make more memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="43cff-139">如果有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外的應用程式正在耗用資源，請嘗試停止執行這些應用程式或考慮在不同的伺服器上執行這些應用程式。</span><span class="sxs-lookup"><span data-stu-id="43cff-139">If applications besides [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are consuming resources, try stopping running these applications or consider running them on a separate server.</span></span> <span data-ttu-id="43cff-140">這將會移除外部的記憶體壓力。</span><span class="sxs-lookup"><span data-stu-id="43cff-140">This will remove external memory pressure.</span></span>  
  
-   <span data-ttu-id="43cff-141">如果已經設定 **max server memory,** ，請增加其設定值。</span><span class="sxs-lookup"><span data-stu-id="43cff-141">If you have configured **max server memory,** increase its setting.</span></span>  
  
 <span data-ttu-id="43cff-142">執行下列 DBCC 命令，以便釋放數個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記憶體快取。</span><span class="sxs-lookup"><span data-stu-id="43cff-142">Run the following DBCC commands to free several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory caches.</span></span>  
  
-   <span data-ttu-id="43cff-143">DBCC FREESYSTEMCACHE</span><span class="sxs-lookup"><span data-stu-id="43cff-143">DBCC FREESYSTEMCACHE</span></span>  
  
-   <span data-ttu-id="43cff-144">DBCC FREESESSIONCACHE</span><span class="sxs-lookup"><span data-stu-id="43cff-144">DBCC FREESESSIONCACHE</span></span>  
  
-   <span data-ttu-id="43cff-145">DBCC FREEPROCCACHE</span><span class="sxs-lookup"><span data-stu-id="43cff-145">DBCC FREEPROCCACHE</span></span>  
  
 <span data-ttu-id="43cff-146">如果仍繼續發生該問題，您必須進一步研究，而且可能必須降低工作負載。</span><span class="sxs-lookup"><span data-stu-id="43cff-146">If the problem continues, you will need to investigate further and possibly reduce workload.</span></span>  
  
  
