---
title: MSSQL_ENG014150 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014150 error
ms.assetid: c3dd3109-abf3-4b38-a4e9-ef48d0235656
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4c926d05be9613ff559f119484fa5e238d71d861
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585308"
---
# <a name="mssql_eng014150"></a><span data-ttu-id="169f8-102">MSSQL_ENG014150</span><span class="sxs-lookup"><span data-stu-id="169f8-102">MSSQL_ENG014150</span></span>
    
## <a name="message-details"></a><span data-ttu-id="169f8-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="169f8-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="169f8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="169f8-104">Product Name</span></span>|<span data-ttu-id="169f8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="169f8-105">SQL Server</span></span>|  
|<span data-ttu-id="169f8-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="169f8-106">Event ID</span></span>|<span data-ttu-id="169f8-107">14150</span><span class="sxs-lookup"><span data-stu-id="169f8-107">14150</span></span>|  
|<span data-ttu-id="169f8-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="169f8-108">Event Source</span></span>|<span data-ttu-id="169f8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="169f8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="169f8-110">元件</span><span class="sxs-lookup"><span data-stu-id="169f8-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="169f8-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="169f8-111">Symbolic Name</span></span>||  
|<span data-ttu-id="169f8-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="169f8-112">Message Text</span></span>|<span data-ttu-id="169f8-113">複寫 -%s：代理程式 %s 成功。</span><span class="sxs-lookup"><span data-stu-id="169f8-113">Replication-%s: agent %s succeeded.</span></span> <span data-ttu-id="169f8-114">%s</span><span class="sxs-lookup"><span data-stu-id="169f8-114">%s</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="169f8-115">說明</span><span class="sxs-lookup"><span data-stu-id="169f8-115">Explanation</span></span>  
 <span data-ttu-id="169f8-116">這個訊息表示複寫代理程式已順利地完成執行。</span><span class="sxs-lookup"><span data-stu-id="169f8-116">This message indicates that a replication agent has successfully finished running.</span></span> <span data-ttu-id="169f8-117">複寫使用下列代理程式：</span><span class="sxs-lookup"><span data-stu-id="169f8-117">Replication uses the following agents:</span></span>  
  
-   <span data-ttu-id="169f8-118">快照集代理程式。</span><span class="sxs-lookup"><span data-stu-id="169f8-118">The Snapshot Agent.</span></span> <span data-ttu-id="169f8-119">此代理程式是由所有發行集使用。</span><span class="sxs-lookup"><span data-stu-id="169f8-119">This agent is used by all publications.</span></span>  
  
-   <span data-ttu-id="169f8-120">記錄讀取器代理程式。</span><span class="sxs-lookup"><span data-stu-id="169f8-120">The Log Reader Agent.</span></span> <span data-ttu-id="169f8-121">此代理程式是由所有交易式發行集使用。</span><span class="sxs-lookup"><span data-stu-id="169f8-121">This agent is used by all transactional publications.</span></span>  
  
-   <span data-ttu-id="169f8-122">佇列讀取器代理程式。</span><span class="sxs-lookup"><span data-stu-id="169f8-122">The Queue Reader Agent.</span></span> <span data-ttu-id="169f8-123">此代理程式是由為佇列更新訂閱而啟用的交易式發行集使用。</span><span class="sxs-lookup"><span data-stu-id="169f8-123">This agent is used by transactional publications enabled for queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="169f8-124">散發代理程式。</span><span class="sxs-lookup"><span data-stu-id="169f8-124">The Distribution Agent.</span></span> <span data-ttu-id="169f8-125">此代理程式會同步處理交易式和快照式發行集的訂閱。</span><span class="sxs-lookup"><span data-stu-id="169f8-125">This agent synchronizes subscriptions to transactional and snapshot publications.</span></span>  
  
-   <span data-ttu-id="169f8-126">合併代理程式。</span><span class="sxs-lookup"><span data-stu-id="169f8-126">The Merge Agent.</span></span> <span data-ttu-id="169f8-127">此代理程式會同步處理合併發行集的訂閱。</span><span class="sxs-lookup"><span data-stu-id="169f8-127">This agent synchronizes subscriptions to merge publications.</span></span>  
  
-   <span data-ttu-id="169f8-128">複寫維護作業。</span><span class="sxs-lookup"><span data-stu-id="169f8-128">Replication maintenance jobs.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="169f8-129">使用者動作</span><span class="sxs-lookup"><span data-stu-id="169f8-129">User Action</span></span>  
 <span data-ttu-id="169f8-130">記錄讀取器代理程式、佇列讀取器代理程式，以及散發代理程式通常都是連續執行，而其他代理程式則通常是視需要或依排程執行。</span><span class="sxs-lookup"><span data-stu-id="169f8-130">The Log Reader Agent, Queue Reader Agent, and Distribution Agent typically run continuously, whereas the other agents typically run on demand or on a schedule.</span></span> <span data-ttu-id="169f8-131">如果不認為代理程式已完成執行，請檢查代理程式的狀態。</span><span class="sxs-lookup"><span data-stu-id="169f8-131">If you do not expect an agent to have completed a run, check the status of the agent.</span></span> <span data-ttu-id="169f8-132">如需相關資訊，請參閱 [Monitor Replication Agents](agents/replication-agents-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="169f8-132">For more information, see [Monitor Replication Agents](agents/replication-agents-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="169f8-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="169f8-133">See Also</span></span>  
 <span data-ttu-id="169f8-134">[複寫代理程式管理](agents/replication-agent-administration.md) </span><span class="sxs-lookup"><span data-stu-id="169f8-134">[Replication Agent Administration](agents/replication-agent-administration.md) </span></span>  
 <span data-ttu-id="169f8-135">[錯誤和事件參考 &#40;複寫&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="169f8-135">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="169f8-136">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span><span class="sxs-lookup"><span data-stu-id="169f8-136">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span></span>  
 <span data-ttu-id="169f8-137">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="169f8-137">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span></span>  
 <span data-ttu-id="169f8-138">[Replication Merge Agent](agents/replication-merge-agent.md) </span><span class="sxs-lookup"><span data-stu-id="169f8-138">[Replication Merge Agent](agents/replication-merge-agent.md) </span></span>  
 <span data-ttu-id="169f8-139">[複寫佇列讀取器代理程式](agents/replication-queue-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="169f8-139">[Replication Queue Reader Agent](agents/replication-queue-reader-agent.md) </span></span>  
 [<span data-ttu-id="169f8-140">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="169f8-140">Replication Snapshot Agent</span></span>](agents/replication-snapshot-agent.md)  
  
  
