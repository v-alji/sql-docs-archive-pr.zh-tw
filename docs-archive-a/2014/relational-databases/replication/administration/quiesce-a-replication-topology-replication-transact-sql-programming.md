---
title: 停止複寫拓撲 (複寫 Transact-SQL 程式設計) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- administering replication, quiescing
- quiesce [SQL Server replication]
- transactional replication, backup and restore
ms.assetid: 7626d575-9994-47be-b772-5b6f1b7ef7ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f12f0fb8ee3a6118e03799d17836573fb5c733df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705074"
---
# <a name="quiesce-a-replication-topology-replication-transact-sql-programming"></a><span data-ttu-id="a16ed-102">停止複寫拓撲 (複寫 Transact-SQL 程式設計)</span><span class="sxs-lookup"><span data-stu-id="a16ed-102">Quiesce a Replication Topology (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="a16ed-103">「停止」\*\* 系統包括停止所有節點上已發行資料表的活動，並確定每個節點已收到來自其他所有節點的所有變更。</span><span class="sxs-lookup"><span data-stu-id="a16ed-103">*Quiescing* a system involves stopping activity on published tables at all nodes and ensuring that each node has received all changes from all other nodes.</span></span> <span data-ttu-id="a16ed-104">本主題說明如何停止複寫拓撲 (此為數項管理工作所需)，以及如何確定節點已從其他節點接收到所有變更。</span><span class="sxs-lookup"><span data-stu-id="a16ed-104">This topic explains how to quiesce a replication topology, which is required for a number of administrative tasks, and how to ensure that a node has received all changes from other nodes.</span></span>  
  
### <a name="to-quiesce-a-transactional-replication-topology-with-read-only-subscriptions"></a><span data-ttu-id="a16ed-105">若要使用唯讀訂閱停止異動複寫拓撲</span><span class="sxs-lookup"><span data-stu-id="a16ed-105">To quiesce a transactional replication topology with read-only subscriptions</span></span>  
  
1.  <span data-ttu-id="a16ed-106">停止在「發行者」端的所有已發行資料表上的活動。</span><span class="sxs-lookup"><span data-stu-id="a16ed-106">Stop activity on all published tables at the Publisher.</span></span>  
  
2.  <span data-ttu-id="a16ed-107">在發行集資料庫的發行者端，執行 [sp_posttracertoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a16ed-107">At the Publisher on the publication database, execute [sp_posttracertoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql).</span></span>  
  
3.  <span data-ttu-id="a16ed-108">在發行集資料庫的「發行者」端，執行 [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a16ed-108">At the Publisher on the publication database, execute [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql).</span></span>  
  
4.  <span data-ttu-id="a16ed-109">確保每個「訂閱者」已接收追蹤 Token。</span><span class="sxs-lookup"><span data-stu-id="a16ed-109">Ensure that each Subscriber has received the tracer token.</span></span>  
  
### <a name="to-quiesce-a-transactional-replication-topology-with-updatable-subscriptions"></a><span data-ttu-id="a16ed-110">若要使用可更新的訂閱停止異動複寫拓撲</span><span class="sxs-lookup"><span data-stu-id="a16ed-110">To quiesce a transactional replication topology with updatable subscriptions</span></span>  
  
1.  <span data-ttu-id="a16ed-111">停止在「發行者」端和所有「訂閱者」端的所有已發行資料表上的活動。</span><span class="sxs-lookup"><span data-stu-id="a16ed-111">Stop activity on all published tables at the Publisher and all Subscribers.</span></span>  
  
2.  <span data-ttu-id="a16ed-112">如果任何「訂閱者」使用佇列更新訂閱：</span><span class="sxs-lookup"><span data-stu-id="a16ed-112">If any Subscribers use queued updating subscriptions:</span></span>  
  
    1.  <span data-ttu-id="a16ed-113">如果「佇列讀取器代理程式」並非以連續模式執行，請執行該代理程式。</span><span class="sxs-lookup"><span data-stu-id="a16ed-113">If the Queue Reader Agent is not running in continuous mode, run the agent.</span></span> <span data-ttu-id="a16ed-114">如需執行代理程式的詳細資訊，請參閱[複寫代理程式可執行檔概念](../concepts/replication-agent-executables-concepts.md)或[啟動及停止複寫代理程式 &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="a16ed-114">For more information about running agents, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
    2.  <span data-ttu-id="a16ed-115">若要確認佇列是空的，請在每個「訂閱者」端執行 [sp_replqueuemonitor](/sql/relational-databases/system-stored-procedures/sp-replqueuemonitor-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="a16ed-115">To verify that the queue is empty, execute [sp_replqueuemonitor](/sql/relational-databases/system-stored-procedures/sp-replqueuemonitor-transact-sql) at each Subscriber.</span></span>  
  
3.  <span data-ttu-id="a16ed-116">在發行集資料庫的「發行者」端，執行 [sp_posttracertoken](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a16ed-116">At the Publisher on the publication database, execute [sp_posttracertoken](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql).</span></span>  
  
4.  <span data-ttu-id="a16ed-117">在發行集資料庫的「發行者」端，執行 [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a16ed-117">At the Publisher on the publication database, execute [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql).</span></span>  
  
5.  <span data-ttu-id="a16ed-118">確保每個「訂閱者」已接收追蹤 Token。</span><span class="sxs-lookup"><span data-stu-id="a16ed-118">Ensure that each Subscriber has received the tracer token.</span></span>  
  
### <a name="to-quiesce-a-peer-to-peer-transactional-replication-topology"></a><span data-ttu-id="a16ed-119">若要停止點對點異動複寫拓撲</span><span class="sxs-lookup"><span data-stu-id="a16ed-119">To quiesce a peer-to-peer transactional replication topology</span></span>  
  
1.  <span data-ttu-id="a16ed-120">停止在所有節點的所有已發行資料表上的活動。</span><span class="sxs-lookup"><span data-stu-id="a16ed-120">Stop activity on all published tables at all nodes.</span></span>  
  
2.  <span data-ttu-id="a16ed-121">在拓撲中的每個發行集資料庫上執行 [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="a16ed-121">Execute [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) on each publication database in the topology.</span></span>  
  
3.  <span data-ttu-id="a16ed-122">如果「記錄讀取器代理程式」或「散發代理程式」並非以連續模式執行，請執行該代理程式。</span><span class="sxs-lookup"><span data-stu-id="a16ed-122">If the Log Reader Agent or Distribution Agent is not running in continuous mode, run the agent.</span></span> <span data-ttu-id="a16ed-123">「記錄讀取器代理程式」必須在「散發代理程式」之前啟動。</span><span class="sxs-lookup"><span data-stu-id="a16ed-123">The Log Reader Agent must be started before the Distribution Agent.</span></span> <span data-ttu-id="a16ed-124">如需執行代理程式的詳細資訊，請參閱[複寫代理程式可執行檔概念](../concepts/replication-agent-executables-concepts.md)或[啟動及停止複寫代理程式 &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="a16ed-124">For more information about running agents, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
4.  <span data-ttu-id="a16ed-125">在拓撲中的每個發行集資料庫上執行 [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="a16ed-125">Execute [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) on each publication database in the topology.</span></span> <span data-ttu-id="a16ed-126">確定結果集包含其他每個節點的回應。</span><span class="sxs-lookup"><span data-stu-id="a16ed-126">Ensure that the result set contains responses from each of the other nodes.</span></span>  
  
### <a name="to-ensure-a-peer-to-peer-node-has-received-all-prior-changes"></a><span data-ttu-id="a16ed-127">若要確定對等節點已接收所有先前的變更</span><span class="sxs-lookup"><span data-stu-id="a16ed-127">To ensure a peer-to-peer node has received all prior changes</span></span>  
  
1.  <span data-ttu-id="a16ed-128">在您所檢查之節點的發行集資料庫上執行 [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="a16ed-128">Execute [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) on the publication database at the node you are checking.</span></span>  
  
2.  <span data-ttu-id="a16ed-129">如果「記錄讀取器代理程式」或「散發代理程式」並非以連續模式執行，請執行該代理程式。</span><span class="sxs-lookup"><span data-stu-id="a16ed-129">If the Log Reader Agent or Distribution Agent is not running in continuous mode, run the agent.</span></span> <span data-ttu-id="a16ed-130">「記錄讀取器代理程式」必須在「散發代理程式」之前啟動。</span><span class="sxs-lookup"><span data-stu-id="a16ed-130">The Log Reader Agent must be started before the Distribution Agent.</span></span> <span data-ttu-id="a16ed-131">如需執行代理程式的詳細資訊，請參閱[複寫代理程式可執行檔概念](../concepts/replication-agent-executables-concepts.md)或[啟動及停止複寫代理程式 &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="a16ed-131">For more information about running agents, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
3.  <span data-ttu-id="a16ed-132">在您所檢查之節點的發行集資料庫上執行 [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="a16ed-132">Execute [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) on the publication database at the node you are checking.</span></span> <span data-ttu-id="a16ed-133">確定結果集包含其他每個節點的回應。</span><span class="sxs-lookup"><span data-stu-id="a16ed-133">Ensure that the result set contains responses from each of the other nodes.</span></span>  
  
### <a name="to-quiesce-a-merge-replication-topology"></a><span data-ttu-id="a16ed-134">若要停止合併式複寫拓撲</span><span class="sxs-lookup"><span data-stu-id="a16ed-134">To quiesce a merge replication topology</span></span>  
  
1.  <span data-ttu-id="a16ed-135">停止在「發行者」端和所有「訂閱者」端的所有已發行資料表上的活動。</span><span class="sxs-lookup"><span data-stu-id="a16ed-135">Stop activity on all published tables at the Publisher and at all Subscribers.</span></span>  
  
2.  <span data-ttu-id="a16ed-136">針對每項訂閱執行合併代理程式兩次：同步處理所有訂閱一次，然後再同步處理每個訂閱一次。</span><span class="sxs-lookup"><span data-stu-id="a16ed-136">Run the Merge Agent for each subscription two times: synchronize all subscriptions once and then synchronize each subscription a second time.</span></span> <span data-ttu-id="a16ed-137">這可確保所有的變更都會複寫到所有節點。</span><span class="sxs-lookup"><span data-stu-id="a16ed-137">This ensures that all changes are replicated to all nodes.</span></span> <span data-ttu-id="a16ed-138">如需執行代理程式的詳細資訊，請參閱[複寫代理程式可執行檔概念](../concepts/replication-agent-executables-concepts.md)或[啟動及停止複寫代理程式 &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="a16ed-138">For more information about running agents, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a16ed-139">如果在同步處理期間發生衝突，則在執行「合併代理程式」兩次之後，衝突解決所需的變更有可能不會傳播到所有節點。</span><span class="sxs-lookup"><span data-stu-id="a16ed-139">If conflicts occur during synchronization, it is possible that changes required by conflict resolution will not be propagated to all nodes after running the Merge Agent two times.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a16ed-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a16ed-140">See Also</span></span>  
 <span data-ttu-id="a16ed-141">[管理點對點拓撲 &#40;複寫 Transact-SQL 程式設計&#41;](administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span><span class="sxs-lookup"><span data-stu-id="a16ed-141">[Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span></span>  
 [<span data-ttu-id="a16ed-142">針對異動複寫測量延遲及驗證連接</span><span class="sxs-lookup"><span data-stu-id="a16ed-142">Measure Latency and Validate Connections for Transactional Replication</span></span>](../monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
