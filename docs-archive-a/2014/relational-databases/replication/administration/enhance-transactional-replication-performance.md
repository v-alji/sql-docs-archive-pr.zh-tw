---
title: 增強異動複寫效能 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publications [SQL Server replication], design and performance
- performance [SQL Server replication], transactional replication
- designing databases [SQL Server], replication performance
- performance [SQL Server replication], snapshot replication
- snapshot replication [SQL Server], performance
- subscriptions [SQL Server replication], performance considerations
- agents [SQL Server replication], performance
- Distribution Agent, performance
- transactional replication, performance
- Log Reader Agent, performance
ms.assetid: 67084a67-43ff-4065-987a-3b16d1841565
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fe802796b129ff9bdb50e5dea13e1fe98beee269
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709233"
---
# <a name="enhance-transactional-replication-performance"></a><span data-ttu-id="90479-102">增強異動複寫效能</span><span class="sxs-lookup"><span data-stu-id="90479-102">Enhance Transactional Replication Performance</span></span>
  <span data-ttu-id="90479-103">除了考慮＜ [增強一般複寫效能](enhance-general-replication-performance.md)＞中所述的一般效能提示之外，還要考慮異動複寫特定的以下幾個其他方面。</span><span class="sxs-lookup"><span data-stu-id="90479-103">After considering the general performance tips described in [Enhancing General Replication Performance](enhance-general-replication-performance.md), consider these additional areas specific to transactional replication.</span></span>  
  
## <a name="database-design"></a><span data-ttu-id="90479-104">資料庫設計</span><span class="sxs-lookup"><span data-stu-id="90479-104">Database Design</span></span>  
  
-   <span data-ttu-id="90479-105">將應用程式設計中的交易量最小化。</span><span class="sxs-lookup"><span data-stu-id="90479-105">Minimize transaction size in your application design.</span></span>  
  
     <span data-ttu-id="90479-106">依預設，異動複寫會根據交易界限傳播變更。</span><span class="sxs-lookup"><span data-stu-id="90479-106">By default, transactional replication propagates changes according to transaction boundaries.</span></span> <span data-ttu-id="90479-107">如果交易較小，便不太可能發生「散發代理程式」因網路問題而必須重新傳送交易的情況。</span><span class="sxs-lookup"><span data-stu-id="90479-107">If transactions are smaller, it is less likely that the Distribution Agent will have to resend a transaction due to network issues.</span></span> <span data-ttu-id="90479-108">如果需要代理程式來重新傳送交易，則傳送的資料量較小。</span><span class="sxs-lookup"><span data-stu-id="90479-108">If the agent is required to resend a transaction, the amount of data sent is smaller.</span></span>  
  
## <a name="distributor-configuration"></a><span data-ttu-id="90479-109">散發者組態</span><span class="sxs-lookup"><span data-stu-id="90479-109">Distributor Configuration</span></span>  
  
-   <span data-ttu-id="90479-110">在專用伺服器上設定散發者。</span><span class="sxs-lookup"><span data-stu-id="90479-110">Configure the Distributor on a dedicated server.</span></span>  
  
     <span data-ttu-id="90479-111">透過設定遠端「散發者」可以降低「發行者」端的處理負擔。</span><span class="sxs-lookup"><span data-stu-id="90479-111">You can reduce processing overhead on the Publisher by configuring a remote Distributor.</span></span> <span data-ttu-id="90479-112">如需詳細資訊，請參閱 [Configure Distribution](../configure-distribution.md)＞。</span><span class="sxs-lookup"><span data-stu-id="90479-112">For more information, see [Configure Distribution](../configure-distribution.md).</span></span>  
  
-   <span data-ttu-id="90479-113">適當調整散發資料庫的大小。</span><span class="sxs-lookup"><span data-stu-id="90479-113">Size the distribution database appropriately.</span></span>  
  
     <span data-ttu-id="90479-114">用一般負載量為系統測試複寫，以決定需要多少空間儲存命令。</span><span class="sxs-lookup"><span data-stu-id="90479-114">Test replication with a typical load for your system to determine how much space is required to store commands.</span></span> <span data-ttu-id="90479-115">確認資料庫大小足夠儲存命令，且無須經常自動成長。</span><span class="sxs-lookup"><span data-stu-id="90479-115">Ensure the database is large enough to store commands without having to auto-grow frequently.</span></span> <span data-ttu-id="90479-116">如需變更資料庫大小的詳細資訊，請參閱 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="90479-116">For more information about changing the size of a database, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
## <a name="publication-design"></a><span data-ttu-id="90479-117">發行集設計</span><span class="sxs-lookup"><span data-stu-id="90479-117">Publication Design</span></span>  
  
-   <span data-ttu-id="90479-118">批次更新到已發行資料表時，複寫預存程序執行。</span><span class="sxs-lookup"><span data-stu-id="90479-118">Replicate stored procedure execution when making batch updates to published tables.</span></span>  
  
     <span data-ttu-id="90479-119">如果您的批次更新偶而會影響到訂閱者的大量資料列，則應該考慮使用預存程序來更新發行的資料表，並發行預存程序的執行。</span><span class="sxs-lookup"><span data-stu-id="90479-119">If you have batch updates that occasionally affect a large number of rows at the Subscriber, you should consider updating the published table using a stored procedure and publish the execution of the stored procedure.</span></span> <span data-ttu-id="90479-120">「散發代理程式」不會傳送每一個受影響資料列的更新或刪除，卻會使用相同的參數值在「訂閱者」端執行相同的程序。</span><span class="sxs-lookup"><span data-stu-id="90479-120">Instead of sending an update or delete for every row affected, the Distribution Agent executes the same procedure at the Subscriber with the same parameter values.</span></span> <span data-ttu-id="90479-121">如需詳細資訊，請參閱 [Publishing Stored Procedure Execution in Transactional Replication](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="90479-121">For more information, see [Publishing Stored Procedure Execution in Transactional Replication](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="90479-122">跨多發行集傳播發行項。</span><span class="sxs-lookup"><span data-stu-id="90479-122">Spread articles across multiple publications.</span></span>  
  
     <span data-ttu-id="90479-123">如果您無法使用 **-SubscriptionStreams** 參數 (本主題中稍後將進行討論)，請考慮建立多個發行集。</span><span class="sxs-lookup"><span data-stu-id="90479-123">If you cannot use the **-SubscriptionStreams** parameter (described later in this topic), consider creating multiple publications.</span></span> <span data-ttu-id="90479-124">在這些發行集間分散發行項允許複寫將變更平行套用到各個「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="90479-124">Spreading articles across these publications allows replication to apply changes in parallel to Subscribers.</span></span>  
  
## <a name="subscription-considerations"></a><span data-ttu-id="90479-125">訂閱考量因素</span><span class="sxs-lookup"><span data-stu-id="90479-125">Subscription Considerations</span></span>  
  
-   <span data-ttu-id="90479-126">如果您在同一「發行者」端有多個發行集，請使用獨立代理程式而非共用代理程式 (此為「新增發行集精靈」的預設值)。</span><span class="sxs-lookup"><span data-stu-id="90479-126">Use independent agents rather than shared agents if you have multiple publications on the same Publisher (this is the default for the New Publication Wizard).</span></span>  
  
-   <span data-ttu-id="90479-127">連續執行代理程式來代替非常頻繁的排程執行。</span><span class="sxs-lookup"><span data-stu-id="90479-127">Run agents continuously instead of on very frequent schedules.</span></span>  
  
     <span data-ttu-id="90479-128">將代理程式設定為連續執行來代替建立頻繁的排程 (例如每分鐘) 可提升複寫效能，因為代理程式不必啟動和停止。</span><span class="sxs-lookup"><span data-stu-id="90479-128">Setting the agents to run continuously rather than creating frequent schedules (such as every minute) improves replication performance, because the agent does not have to start and stop.</span></span> <span data-ttu-id="90479-129">當您將「散發代理程式」設定為連續執行時，變更將以低度延遲傳播到拓撲中連接的其他伺服器。</span><span class="sxs-lookup"><span data-stu-id="90479-129">When you set the Distribution Agent to run continuously, changes are propagated with low latency to the other servers that are connected in the topology.</span></span> <span data-ttu-id="90479-130">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="90479-130">For more information, see:</span></span>  
  
    -   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="90479-131">:[指定同步處理排程](../specify-synchronization-schedules.md)</span><span class="sxs-lookup"><span data-stu-id="90479-131">: [Specify Synchronization Schedules](../specify-synchronization-schedules.md)</span></span>  
  
## <a name="distribution-agent-and-log-reader-agent-parameters"></a><span data-ttu-id="90479-132">散發代理程式和記錄讀取器代理程式參數</span><span class="sxs-lookup"><span data-stu-id="90479-132">Distribution Agent and Log Reader Agent Parameters</span></span>  
  
-   <span data-ttu-id="90479-133">若要解決意外的一次性瓶頸，請針對記錄讀取器代理程式使用 **-MaxCmdsInTran**參數。</span><span class="sxs-lookup"><span data-stu-id="90479-133">To resolve accidental, one-time bottlenecks use the **-MaxCmdsInTran** parameter for the Log Reader Agent.</span></span>  
  
     <span data-ttu-id="90479-134">**-MaxCmdsInTran**參數會指定當記錄讀取器將命令寫入散發資料庫時，分組到交易中的最大語句數目。</span><span class="sxs-lookup"><span data-stu-id="90479-134">The **-MaxCmdsInTran** parameter specifies the maximum number of statements grouped into a transaction as the Log Reader writes commands to the distribution database.</span></span> <span data-ttu-id="90479-135">使用此參數可讓「記錄讀取器代理程式」和「散發作業代理程式」在「訂閱者」端套用命令時，於「發行者」端將大型交易 (由許多命令組成) 分割成幾個較小的交易。</span><span class="sxs-lookup"><span data-stu-id="90479-135">Using this parameter allows the Log Reader Agent and Distribution Agent to divide large transactions (consisting of many commands) at the Publisher into several smaller transactions when applying commands at the Subscriber.</span></span> <span data-ttu-id="90479-136">指定此參數可以降低「散發者」的競爭，並減少「發行者」和「訂閱者」之間的延遲。</span><span class="sxs-lookup"><span data-stu-id="90479-136">Specifying this parameter can reduce contention at the Distributor and reduce latency between the Publisher and Subscriber.</span></span> <span data-ttu-id="90479-137">因為原始交易是以較小的單位來套用，所以「訂閱者」在原始交易結束之前可以存取大量的邏輯「發行者」交易資料列，打破了嚴格的交易不可部份完成性。</span><span class="sxs-lookup"><span data-stu-id="90479-137">Because the original transaction is applied in smaller units, the Subscriber can access rows of a large logical Publisher transaction prior to the end of the original transaction, breaking strict transactional atomicity.</span></span> <span data-ttu-id="90479-138">預設值為 **0**，保留「發行者」的交易界限。</span><span class="sxs-lookup"><span data-stu-id="90479-138">The default is **0**, which preserves the transaction boundaries of the Publisher.</span></span> <span data-ttu-id="90479-139">此參數不會套用至 Oracle 發行者。</span><span class="sxs-lookup"><span data-stu-id="90479-139">This parameter does not apply to Oracle Publishers.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="90479-140">`MaxCmdsInTran` 的設計不是為了要永遠開啟。</span><span class="sxs-lookup"><span data-stu-id="90479-140">`MaxCmdsInTran` was not designed to be always turned on.</span></span> <span data-ttu-id="90479-141">其存在的目的是為了解決有人不小心在單一交易中執行大量 DML 作業的狀況 (使得整筆交易在散發資料庫之前延遲命令的散發、鎖定持有等等)。</span><span class="sxs-lookup"><span data-stu-id="90479-141">It exists to work around cases where someone accidentally performed a large number of DML operations in a single transaction (causing delay in distribution of commands until the entire transaction is in distribution database, locks being held, etc.).</span></span> <span data-ttu-id="90479-142">如果您習慣性地遇到這個狀況，您應該檢閱您的應用程式，並找出減少交易大小的方法。</span><span class="sxs-lookup"><span data-stu-id="90479-142">If you routinely fall into this situation, you should review your applications and find ways to reduce the transaction size.</span></span>  
  
-   <span data-ttu-id="90479-143">針對散發代理程式，請使用 **-SubscriptionStreams**參數。</span><span class="sxs-lookup"><span data-stu-id="90479-143">Use the **-SubscriptionStreams** parameter for the Distribution Agent.</span></span>  
  
     <span data-ttu-id="90479-144">**-SubscriptionStreams**參數可以大幅改善匯總複寫輸送量。</span><span class="sxs-lookup"><span data-stu-id="90479-144">The **-SubscriptionStreams** parameter can greatly improve aggregate replication throughput.</span></span> <span data-ttu-id="90479-145">它允許至「訂閱者」的多個連接平行套用批次變更，同時在使用單一執行緒時維護現有的許多交易特性。</span><span class="sxs-lookup"><span data-stu-id="90479-145">It allows multiple connections to a Subscriber to apply batches of changes in parallel, while maintaining many of the transactional characteristics present when using a single thread.</span></span> <span data-ttu-id="90479-146">如果有一個連接無法執行或認可，則所有連接都將中止目前批次，且代理程式將使用單一資料流重試失敗的批次。</span><span class="sxs-lookup"><span data-stu-id="90479-146">If one of the connections fails to execute or commit, all connections will abort the current batch, and the agent will use a single stream to retry the failed batches.</span></span> <span data-ttu-id="90479-147">在此重試階段完成之前，「訂閱者」端可能會出現暫時的交易不一致性。</span><span class="sxs-lookup"><span data-stu-id="90479-147">Before this retry phase completes, there can be temporary transactional inconsistencies at the Subscriber.</span></span> <span data-ttu-id="90479-148">成功認可失敗的批次後，「訂閱者」將返回交易一致性的狀態。</span><span class="sxs-lookup"><span data-stu-id="90479-148">After the failed batches are successfully committed, the Subscriber is brought back to a state of transactional consistency.</span></span>  
  
     <span data-ttu-id="90479-149">此代理程式參數的值可以使用[sp_addsubscription &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)的\*\* \@ subscriptionstreams\*\*來指定。</span><span class="sxs-lookup"><span data-stu-id="90479-149">A value for this agent parameter can be specified using the **\@subscriptionstreams** of [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).</span></span>  
  
-   <span data-ttu-id="90479-150">為「記錄讀取器代理程式」增加 **-ReadBatchSize** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="90479-150">Increase the value of the **-ReadBatchSize** parameter for the Log Reader Agent.</span></span>  
  
     <span data-ttu-id="90479-151">「記錄讀取器代理程式」與「散發代理程式」支援交易讀取與認可作業的批次大小。</span><span class="sxs-lookup"><span data-stu-id="90479-151">The Log Reader Agent and Distribution Agent support batch sizes for transaction read and commit operations.</span></span> <span data-ttu-id="90479-152">批次大小的預設值是 500 項交易。</span><span class="sxs-lookup"><span data-stu-id="90479-152">Batch sizes default to 500 transactions.</span></span> <span data-ttu-id="90479-153">「記錄讀取器代理程式」會從記錄檔中讀取特定數量的交易，無論這些交易是否都標示為複寫。</span><span class="sxs-lookup"><span data-stu-id="90479-153">The Log Reader Agent reads the specific number of transactions from the log, whether or not they are marked for replication.</span></span> <span data-ttu-id="90479-154">當大量交易寫入發行資料庫，但標示要複寫的只是其中小部分子集時，您就應該使用 **-ReadBatchSize** 參數來增加「記錄讀取器代理程式」的讀取批次大小。</span><span class="sxs-lookup"><span data-stu-id="90479-154">When a large number of transactions is written to a publication database, but only a small subset of those are marked for replication, you should use the **-ReadBatchSize** parameter to increase the read batch size of the Log Reader Agent.</span></span> <span data-ttu-id="90479-155">此參數不會套用至 Oracle 發行者。</span><span class="sxs-lookup"><span data-stu-id="90479-155">This parameter does not apply to Oracle Publishers.</span></span>  
  
-   <span data-ttu-id="90479-156">為「散發代理程式」增加 **-CommitBatchSize** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="90479-156">Increase the value of the **-CommitBatchSize** parameter for the Distribution Agent.</span></span>  
  
     <span data-ttu-id="90479-157">認可一組交易的負擔是固定的；透過以較低頻率認可較大的交易量，負擔會分散到較大量的資料。</span><span class="sxs-lookup"><span data-stu-id="90479-157">Committing a set of transactions has a fixed overhead; by committing a larger number of transactions less frequently, the overhead is spread across a larger volume of data.</span></span> <span data-ttu-id="90479-158">但是，由於套用變更的成本還受限於其他因素，例如包含記錄檔之磁碟的最大 I/O，因此增加此參數的好處不那麼明顯。</span><span class="sxs-lookup"><span data-stu-id="90479-158">However, the benefit of increasing this parameter drops off as the cost of applying changes is gated by other factors, such as the maximum I/O of the disk that contains the log.</span></span> <span data-ttu-id="90479-159">此外，還要考慮反向作用：任何導致散發代理程式重新啟動的失敗都必須回復，並重新套用更大量的交易。</span><span class="sxs-lookup"><span data-stu-id="90479-159">Additionally, there is a trade off to be considered: any failure that causes the Distribution Agent to start over must rollback and reapply a larger number of transactions.</span></span> <span data-ttu-id="90479-160">對於不穩定的網路，當發生錯誤時，值越低導致的錯誤就越少，要回復並重新套用的交易數也越少。</span><span class="sxs-lookup"><span data-stu-id="90479-160">For unreliable networks, a lower value can result in less failures and a smaller number of transactions to rollback and reapply if a failure occurs.</span></span>  
  
-   <span data-ttu-id="90479-161">為「記錄讀取器代理程式」減少 **-PollingInterval** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="90479-161">Decrease the value of the **-PollingInterval** parameter for the Log Reader Agent.</span></span>  
  
     <span data-ttu-id="90479-162">**-PollingInterval** 參數指定針對待複寫交易查詢已發行資料庫之交易記錄檔的頻率。</span><span class="sxs-lookup"><span data-stu-id="90479-162">The **-PollingInterval** parameter specifies how often the transaction log of a published database is queried for transactions to replicate.</span></span> <span data-ttu-id="90479-163">預設值是 5 秒。</span><span class="sxs-lookup"><span data-stu-id="90479-163">The default is 5 seconds.</span></span> <span data-ttu-id="90479-164">如果減小此值，記錄檔輪詢將更頻繁，這會降低從發行集資料庫到散發資料庫之交易傳遞的延遲。</span><span class="sxs-lookup"><span data-stu-id="90479-164">If you decrease this value, the log is polled more frequently, which can result in lower latency for the delivery of transactions from the publication database to the distribution database.</span></span> <span data-ttu-id="90479-165">但是，您應在降低延遲需求和因更頻繁地輪詢而導致伺服器負載增加之間進行平衡。</span><span class="sxs-lookup"><span data-stu-id="90479-165">However, you should balance the need for lower latency against the increased load on the server from polling more frequently.</span></span>  
  
 <span data-ttu-id="90479-166">可於代理程式設定檔和命令列中指定代理程式參數。</span><span class="sxs-lookup"><span data-stu-id="90479-166">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="90479-167">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="90479-167">For more information, see:</span></span>  
  
-   [<span data-ttu-id="90479-168">處理複寫代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="90479-168">Work with Replication Agent Profiles</span></span>](../agents/replication-agent-profiles.md)  
  
-   [<span data-ttu-id="90479-169">檢視並修改複寫代理程式命令提示字元參數 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="90479-169">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](../agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
-   [<span data-ttu-id="90479-170">Replication Agent Executables Concepts</span><span class="sxs-lookup"><span data-stu-id="90479-170">Replication Agent Executables Concepts</span></span>](../concepts/replication-agent-executables-concepts.md)  
  
  
