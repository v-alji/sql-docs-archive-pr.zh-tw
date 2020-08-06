---
title: 預存程序事件類別目錄 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Stored Procedures event category [SQL Server]
- SQL Server event classes, Stored Procedures event category
- event classes [SQL Server], Stored Procedures event category
ms.assetid: 71bebaa3-a05a-4695-b349-078cecd0949a
author: stevestein
ms.author: sstein
ms.openlocfilehash: df2e0d9a4c077ff16eba09bc5ebb6447d5d27595
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710646"
---
# <a name="stored-procedures-event-category"></a><span data-ttu-id="1fd39-102">Stored Procedures 事件類別目錄</span><span class="sxs-lookup"><span data-stu-id="1fd39-102">Stored Procedures Event Category</span></span>
  <span data-ttu-id="1fd39-103">**Stored Procedures** 事件類別目錄包含一般的預存程序事件。</span><span class="sxs-lookup"><span data-stu-id="1fd39-103">The **Stored Procedures** event category contains general stored procedure events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1fd39-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="1fd39-104">In This Section</span></span>  
  
|<span data-ttu-id="1fd39-105">主題</span><span class="sxs-lookup"><span data-stu-id="1fd39-105">Topic</span></span>|<span data-ttu-id="1fd39-106">描述</span><span class="sxs-lookup"><span data-stu-id="1fd39-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1fd39-107">RPC:Completed 事件類別</span><span class="sxs-lookup"><span data-stu-id="1fd39-107">RPC:Completed Event Class</span></span>](rpc-completed-event-class.md)|<span data-ttu-id="1fd39-108">指出遠端程序呼叫 (RPC) 已完成。</span><span class="sxs-lookup"><span data-stu-id="1fd39-108">Indicates that a remote procedure call (RPC) has been completed.</span></span>|  
|[<span data-ttu-id="1fd39-109">PreConnect:Completed 事件類別</span><span class="sxs-lookup"><span data-stu-id="1fd39-109">PreConnect:Completed Event Class</span></span>](preconnect-completed-event-class.md)|<span data-ttu-id="1fd39-110">指出資源管理員分類函數執行完成。</span><span class="sxs-lookup"><span data-stu-id="1fd39-110">Indicates when the Resource Governor classifier function finishes execution.</span></span>|  
|[<span data-ttu-id="1fd39-111">PreConnect:Starting 事件類別</span><span class="sxs-lookup"><span data-stu-id="1fd39-111">PreConnect:Starting Event Class</span></span>](preconnect-starting-event-class.md)|<span data-ttu-id="1fd39-112">指出資源管理員分類函數開始執行。</span><span class="sxs-lookup"><span data-stu-id="1fd39-112">Indicates when the Resource Governor classifier function starts execution.</span></span>|  
|[<span data-ttu-id="1fd39-113">RPC Output Parameter 事件類別</span><span class="sxs-lookup"><span data-stu-id="1fd39-113">RPC Output Parameter Event Class</span></span>](rpc-output-parameter-event-class.md)|<span data-ttu-id="1fd39-114">追蹤遠端程序呼叫執行之後的輸出參數值。</span><span class="sxs-lookup"><span data-stu-id="1fd39-114">Traces the output parameter values of remote procedure calls after execution.</span></span>|  
|[<span data-ttu-id="1fd39-115">RPC:Starting 事件類別</span><span class="sxs-lookup"><span data-stu-id="1fd39-115">RPC:Starting Event Class</span></span>](rpc-starting-event-class.md)|<span data-ttu-id="1fd39-116">指出遠端程序呼叫已開始。</span><span class="sxs-lookup"><span data-stu-id="1fd39-116">Indicates that a remote procedure call is starting.</span></span>|  
|[<span data-ttu-id="1fd39-117">SP:CacheHit 事件類別</span><span class="sxs-lookup"><span data-stu-id="1fd39-117">SP:CacheHit Event Class</span></span>](sp-cachehit-event-class.md)|<span data-ttu-id="1fd39-118">指出預存程序已在快取中。</span><span class="sxs-lookup"><span data-stu-id="1fd39-118">Indicates that the stored procedure is in the cache.</span></span>|  
|[<span data-ttu-id="1fd39-119">SP:CacheInsert 事件類別</span><span class="sxs-lookup"><span data-stu-id="1fd39-119">SP:CacheInsert Event Class</span></span>](sp-cacheinsert-event-class.md)|<span data-ttu-id="1fd39-120">指出已將預存程序放入快取中。</span><span class="sxs-lookup"><span data-stu-id="1fd39-120">Indicates that the stored procedure has been brought into the cache.</span></span>|  
|[<span data-ttu-id="1fd39-121">SP:CacheMiss 事件類別</span><span class="sxs-lookup"><span data-stu-id="1fd39-121">SP:CacheMiss Event Class</span></span>](sp-cachemiss-event-class.md)|<span data-ttu-id="1fd39-122">指出在快取中找不到預存程序。</span><span class="sxs-lookup"><span data-stu-id="1fd39-122">Indicates that the stored procedure was not found in the cache.</span></span>|  
|[<span data-ttu-id="1fd39-123">SP:CacheRemove 事件類別</span><span class="sxs-lookup"><span data-stu-id="1fd39-123">SP:CacheRemove Event Class</span></span>](sp-cacheremove-event-class.md)|<span data-ttu-id="1fd39-124">指出已從快取移除預存程序。</span><span class="sxs-lookup"><span data-stu-id="1fd39-124">Indicates that the stored procedure has been removed from the cache.</span></span>|  
|[<span data-ttu-id="1fd39-125">SP:Completed 事件類別</span><span class="sxs-lookup"><span data-stu-id="1fd39-125">SP:Completed Event Class</span></span>](sp-completed-event-class.md)|<span data-ttu-id="1fd39-126">指出已完成預存程序的執行。</span><span class="sxs-lookup"><span data-stu-id="1fd39-126">Indicates that execution of the stored procedure has completed.</span></span>|  
|[<span data-ttu-id="1fd39-127">SP:Recompile 事件類別</span><span class="sxs-lookup"><span data-stu-id="1fd39-127">SP:Recompile Event Class</span></span>](sp-recompile-event-class.md)|<span data-ttu-id="1fd39-128">指出已重新編譯預存程序。</span><span class="sxs-lookup"><span data-stu-id="1fd39-128">Indicates that the stored procedure has been recompiled.</span></span>|  
|[<span data-ttu-id="1fd39-129">SP:Starting 事件類別</span><span class="sxs-lookup"><span data-stu-id="1fd39-129">SP:Starting Event Class</span></span>](sp-starting-event-class.md)|<span data-ttu-id="1fd39-130">指出預存程序的執行已開始。</span><span class="sxs-lookup"><span data-stu-id="1fd39-130">Indicates that execution of the stored procedure is starting.</span></span>|  
|[<span data-ttu-id="1fd39-131">SP:StmtCompleted 事件類別</span><span class="sxs-lookup"><span data-stu-id="1fd39-131">SP:StmtCompleted Event Class</span></span>](sp-stmtcompleted-event-class.md)|<span data-ttu-id="1fd39-132">指出已經完成預存程序中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1fd39-132">Indicates that a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement within a stored procedure has completed.</span></span>|  
|[<span data-ttu-id="1fd39-133">SP:StmtStarting 事件類別</span><span class="sxs-lookup"><span data-stu-id="1fd39-133">SP:StmtStarting Event Class</span></span>](sp-stmtstarting-event-class.md)|<span data-ttu-id="1fd39-134">指出已經開始預存程序中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1fd39-134">Indicates that a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement within a stored procedure has started.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1fd39-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fd39-135">See Also</span></span>  
 <span data-ttu-id="1fd39-136">[擴充事件](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="1fd39-136">[Extended Events](../extended-events/extended-events.md) </span></span>  
 [<span data-ttu-id="1fd39-137">sp_trace_setevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1fd39-137">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
