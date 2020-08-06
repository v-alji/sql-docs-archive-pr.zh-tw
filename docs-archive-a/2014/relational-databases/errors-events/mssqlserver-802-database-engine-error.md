---
title: MSSQLSERVER_802 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 802 (Database Engine error)
ms.assetid: 5892ed24-4dcb-4bf9-a8a4-a7ca898832d5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9edcdda1410d7651f7c7531ef98c64c85741f15a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607415"
---
# <a name="mssqlserver_802"></a><span data-ttu-id="b773a-102">MSSQLSERVER_802</span><span class="sxs-lookup"><span data-stu-id="b773a-102">MSSQLSERVER_802</span></span>
    
## <a name="details"></a><span data-ttu-id="b773a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b773a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b773a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b773a-104">Product Name</span></span>|<span data-ttu-id="b773a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b773a-105">SQL Server</span></span>|  
|<span data-ttu-id="b773a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b773a-106">Event ID</span></span>|<span data-ttu-id="b773a-107">802</span><span class="sxs-lookup"><span data-stu-id="b773a-107">802</span></span>|  
|<span data-ttu-id="b773a-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="b773a-108">Event Source</span></span>|<span data-ttu-id="b773a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b773a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b773a-110">元件</span><span class="sxs-lookup"><span data-stu-id="b773a-110">Component</span></span>|<span data-ttu-id="b773a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b773a-111">SQLEngine</span></span>|  
|<span data-ttu-id="b773a-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b773a-112">Symbolic Name</span></span>|<span data-ttu-id="b773a-113">NO_BUFS</span><span class="sxs-lookup"><span data-stu-id="b773a-113">NO_BUFS</span></span>|  
|<span data-ttu-id="b773a-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b773a-114">Message Text</span></span>|<span data-ttu-id="b773a-115">緩衝集區裡沒有足夠的可用記憶體。</span><span class="sxs-lookup"><span data-stu-id="b773a-115">There is insufficient memory available in the buffer pool.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b773a-116">說明</span><span class="sxs-lookup"><span data-stu-id="b773a-116">Explanation</span></span>  
 <span data-ttu-id="b773a-117">當緩衝集區已滿，而且緩衝集區已經無法成長時，就會造成這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="b773a-117">This is caused when the buffer pool is full and the buffer pool can not grow any larger.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b773a-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b773a-118">User Action</span></span>  
 <span data-ttu-id="b773a-119">下列清單概述有助於疑難排解記憶體錯誤的一般步驟：</span><span class="sxs-lookup"><span data-stu-id="b773a-119">The following list outlines general steps that will help in troubleshooting memory errors:</span></span>  
  
1.  <span data-ttu-id="b773a-120">確認是否有其他應用程式或服務正在耗用此伺服器的記憶體。</span><span class="sxs-lookup"><span data-stu-id="b773a-120">Verify whether other applications or services are consuming memory on this server.</span></span> <span data-ttu-id="b773a-121">重新設定比較不重要的應用程式或服務，以降低其記憶體耗用量。</span><span class="sxs-lookup"><span data-stu-id="b773a-121">Reconfigure less critical applications or services to consume less memory.</span></span>  
  
2.  <span data-ttu-id="b773a-122">開始收集以下內容的效能監視器計數：[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **：Buffer Manager**、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **：記憶體管理員**。</span><span class="sxs-lookup"><span data-stu-id="b773a-122">Start collecting performance monitor counters for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: Buffer Manager**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: Memory Manager**.</span></span>  
  
3.  <span data-ttu-id="b773a-123">檢查下列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記憶體組態參數：</span><span class="sxs-lookup"><span data-stu-id="b773a-123">Check the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory configuration parameters:</span></span>  
  
    -   <span data-ttu-id="b773a-124">**max server memory**</span><span class="sxs-lookup"><span data-stu-id="b773a-124">**max server memory**</span></span>  
  
    -   <span data-ttu-id="b773a-125">**min server memory**</span><span class="sxs-lookup"><span data-stu-id="b773a-125">**min server memory**</span></span>  
  
    -   <span data-ttu-id="b773a-126">**min memory per query**</span><span class="sxs-lookup"><span data-stu-id="b773a-126">**min memory per query**</span></span>  
  
     <span data-ttu-id="b773a-127">注意任何不尋常的設定，並視需要加以更正。</span><span class="sxs-lookup"><span data-stu-id="b773a-127">Notice any unusual settings and correct them as necessary.</span></span> <span data-ttu-id="b773a-128">說明 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的增加記憶體需求。</span><span class="sxs-lookup"><span data-stu-id="b773a-128">Account for increased memory requirements for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b773a-129">預設值列於《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜設定伺服器組態選項＞。</span><span class="sxs-lookup"><span data-stu-id="b773a-129">Default settings are listed in "Setting Server Configuration Options" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
4.  <span data-ttu-id="b773a-130">當您看到這些錯誤訊息時，請觀察 DBCC MEMORYSTATUS 輸出以及它變更的方式。</span><span class="sxs-lookup"><span data-stu-id="b773a-130">Observe DBCC MEMORYSTATUS output and the way it changes when you see these error messages.</span></span>  
  
5.  <span data-ttu-id="b773a-131">檢查工作負載 (並行工作階段的數目以及目前正在執行的查詢數)。</span><span class="sxs-lookup"><span data-stu-id="b773a-131">Check the workload (number of concurrent sessions, currently executing queries).</span></span>  
  
 <span data-ttu-id="b773a-132">下列動作可以為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供更多可用的記憶體：</span><span class="sxs-lookup"><span data-stu-id="b773a-132">The following actions may make more memory available to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="b773a-133">如果有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外的應用程式正在耗用資源，請嘗試停止這些應用程式或在不同的伺服器上執行這些應用程式。</span><span class="sxs-lookup"><span data-stu-id="b773a-133">If applications besides [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are consuming resources, try stopping these applications or running them on a separate server.</span></span>  
  
-   <span data-ttu-id="b773a-134">如果已經設定 **max server memory**，請增加其設定值。</span><span class="sxs-lookup"><span data-stu-id="b773a-134">If you have configured **max server memory,** increase the setting.</span></span>  
  
 <span data-ttu-id="b773a-135">執行下列 DBCC 命令，以便釋放數個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記憶體快取。</span><span class="sxs-lookup"><span data-stu-id="b773a-135">Run the following DBCC commands to free several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory caches.</span></span>  
  
-   <span data-ttu-id="b773a-136">DBCC FREESYSTEMCACHE</span><span class="sxs-lookup"><span data-stu-id="b773a-136">DBCC FREESYSTEMCACHE</span></span>  
  
-   <span data-ttu-id="b773a-137">DBCC FREESESSIONCACHE</span><span class="sxs-lookup"><span data-stu-id="b773a-137">DBCC FREESESSIONCACHE</span></span>  
  
-   <span data-ttu-id="b773a-138">DBCC FREEPROCCACHE</span><span class="sxs-lookup"><span data-stu-id="b773a-138">DBCC FREEPROCCACHE</span></span>  
  
 <span data-ttu-id="b773a-139">如果仍繼續發生該問題，您必須進一步研究，而且可能必須降低工作負載。</span><span class="sxs-lookup"><span data-stu-id="b773a-139">If the problem continues, you will need to investigate further and possibly reduce workload.</span></span>  
  
  
