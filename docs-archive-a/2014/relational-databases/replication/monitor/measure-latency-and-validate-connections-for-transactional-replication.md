---
title: 針對異動複寫測量延遲及驗證連接 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, performance
- tracer tokens [SQL Server replication]
- latency [SQL Server replication]
- transactional replication, tracer tokens
- monitoring performance [SQL Server replication], tracer tokens
ms.assetid: 4addd426-7523-4067-8d7d-ca6bae4c9e34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3ba1e5eddfdcffa5fbefdea323f110ba9d15ca8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593941"
---
# <a name="measure-latency-and-validate-connections-for-transactional-replication"></a><span data-ttu-id="1d8ce-102">針對異動複寫測量延遲及驗證連接</span><span class="sxs-lookup"><span data-stu-id="1d8ce-102">Measure Latency and Validate Connections for Transactional Replication</span></span>
  <span data-ttu-id="1d8ce-103">本主題描述如何使用複寫監視器、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 Replication Management Objects (RMO)，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中測量延遲及驗證異動複寫的連接。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-103">This topic describes how to measure latency and validate connections for transactional replication in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using Replication Monitor, [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span> <span data-ttu-id="1d8ce-104">異動複寫具有追蹤 Token 功能，該功能會提供便利的方式來計算異動複寫拓撲中的延遲並驗證「發行者」、「散發者」及「訂閱者」之間的連接。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-104">Transactional replication provides the tracer token feature, which provides a convenient way to measure latency in transactional replication topologies and to validate the connections between the Publisher, Distributor and Subscribers.</span></span> <span data-ttu-id="1d8ce-105">Token (即少量的資料) 會寫入發行集資料庫的交易記錄，會標示為典型的已複寫交易並且會透過系統傳送，它可允許計算：</span><span class="sxs-lookup"><span data-stu-id="1d8ce-105">A token (a small amount of data) is written to the transaction log of the publication database, marked as though it were a typical replicated transaction, and sent through the system, allowing a calculation of:</span></span>  
  
-   <span data-ttu-id="1d8ce-106">在發行者端認可交易和在散發者端之散發資料庫插入對應的命令之間，所經過的時間。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-106">How much time elapses between a transaction being committed at the Publisher and the corresponding command being inserted in the distribution database at the Distributor.</span></span>  
  
-   <span data-ttu-id="1d8ce-107">在散發資料庫中插入命令和在訂閱者端認可對應的交易之間，所經過的時間。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-107">How much time elapses between a command being inserted in the distribution database and the corresponding transaction being committed at a Subscriber.</span></span>  
  
 <span data-ttu-id="1d8ce-108">根據以上計算，您可以回答許多問題，包括：</span><span class="sxs-lookup"><span data-stu-id="1d8ce-108">From these calculations, you can answer a number of questions, including:</span></span>  
  
-   <span data-ttu-id="1d8ce-109">哪些訂閱者在接收發行者的變更時，所花費的時間最長？</span><span class="sxs-lookup"><span data-stu-id="1d8ce-109">Which Subscribers take the longest to receive a change from the Publisher?</span></span>  
  
-   <span data-ttu-id="1d8ce-110">預期會收到追蹤 Token 的訂閱者中，哪些沒有接收到 (如果有的話)？</span><span class="sxs-lookup"><span data-stu-id="1d8ce-110">Of the Subscribers expected to receive the tracer token, which, if any, have not received it?</span></span>  
  
 <span data-ttu-id="1d8ce-111">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="1d8ce-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1d8ce-112">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="1d8ce-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1d8ce-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="1d8ce-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   <span data-ttu-id="1d8ce-114">**若要測量延遲及驗證連接，請使用：**</span><span class="sxs-lookup"><span data-stu-id="1d8ce-114">**To measure latency and validate connections, using:**</span></span>  
  
     [<span data-ttu-id="1d8ce-115">SQL Server 複寫監視器</span><span class="sxs-lookup"><span data-stu-id="1d8ce-115">SQL Server Replication Monitor</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1d8ce-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1d8ce-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="1d8ce-117">Replication Management Objects</span><span class="sxs-lookup"><span data-stu-id="1d8ce-117">Replication Management Objects</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1d8ce-118">開始之前</span><span class="sxs-lookup"><span data-stu-id="1d8ce-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1d8ce-119">限制事項</span><span class="sxs-lookup"><span data-stu-id="1d8ce-119">Limitations and Restrictions</span></span>  
 <span data-ttu-id="1d8ce-120">追蹤 Token 在停止系統時也很有幫助，包括停止所有活動並確認所有節點已接收全部尚未處理的變更。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-120">Tracer tokens can also be useful when quiescing a system, which involves stopping all activity and verifying that all nodes have received all outstanding changes.</span></span> <span data-ttu-id="1d8ce-121">如需詳細資訊，請參閱[停止複寫拓撲 &#40;複寫 Transact-SQL 程式設計&#41;](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-121">For more information, see [Quiesce a Replication Topology &#40;Replication Transact-SQL Programming&#41;](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md).</span></span>  
  
 <span data-ttu-id="1d8ce-122">若要使用追蹤 token，您必須使用的特定版本 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="1d8ce-122">To use tracer tokens, you must use certain versions of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="1d8ce-123">散發者必須為 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-123">The Distributor must be [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] or later.</span></span>  
  
-   <span data-ttu-id="1d8ce-124">「發行者」必須為 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 或更新版本，或為「Oracle 發行者」。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-124">The Publisher must be [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] or later or be an Oracle Publisher.</span></span>  
  
-   <span data-ttu-id="1d8ce-125">針對發送訂閱，如果訂閱者是 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 或更新版本，則會從發行者、散發者和訂閱者收集追蹤 token 統計資料。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-125">For push subscriptions, tracer token statistics are gathered from the Publisher, Distributor, and Subscribers if the Subscriber is [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 or later.</span></span>  
  
-   <span data-ttu-id="1d8ce-126">對於提取訂閱，則會從「訂閱者」收集追蹤 Token 統計資料，但只限於「訂閱者」為 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 或更新版本的情況下。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-126">For pull subscriptions, tracer token statistics are gathered from Subscribers only if the Subscriber is [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] or later.</span></span> <span data-ttu-id="1d8ce-127">如果訂閱者是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] ，則只會從發行者和散發者收集統計資料。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-127">If the Subscriber is [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)], statistics are gathered only from the Publisher and Distributor.</span></span>  
  
 <span data-ttu-id="1d8ce-128">以下為另外一些應注意的問題和限制：</span><span class="sxs-lookup"><span data-stu-id="1d8ce-128">There are also a number of other issues and restrictions to be aware of:</span></span>  
  
-   <span data-ttu-id="1d8ce-129">訂閱必須為作用狀態以便接收追蹤 Token。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-129">Subscriptions must be active to receive a tracer token.</span></span> <span data-ttu-id="1d8ce-130">如果訂閱已經過初始化，則其為作用狀態。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-130">A subscription is active if it has been initialized.</span></span>  
  
-   <span data-ttu-id="1d8ce-131">重新初始化會移除相關訂閱的所有暫止追蹤 Token。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-131">Reinitialization removes any pending tracer tokens for the relevant subscriptions.</span></span>  
  
-   <span data-ttu-id="1d8ce-132">「訂閱者」僅接收初始同步處理之後建立的追蹤 Token。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-132">Subscribers only receive tracer tokens that were created after their initial synchronization.</span></span>  
  
-   <span data-ttu-id="1d8ce-133">追蹤 Token 不會透過重新發行「訂閱者」來轉送。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-133">Tracer tokens are not forwarded by republishing Subscribers.</span></span>  
  
-   <span data-ttu-id="1d8ce-134">在容錯移轉到次要複本之後，複寫監視器就無法調整 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 發行執行個體的名稱，而且會繼續在原始主要 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體名稱之下顯示複寫資訊。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-134">After failover to a secondary, Replication Monitor is unable to adjust the name of the publishing instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and will continue to display replication information under the name of the original primary instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1d8ce-135">在容錯移轉之後，便無法使用複寫監視器輸入追蹤 Token，但是可以在複寫監視器中看到在新的發行者端使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)]輸入的追蹤 Token。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-135">After failover, a tracer token cannot be entered by using the Replication Monitor, however a tracer token entered on the new publisher by using [!INCLUDE[tsql](../../../includes/tsql-md.md)], is visible in Replication Monitor.</span></span>  
  
##  <a name="using-sql-server-replication-monitor"></a><a name="SSMSProcedure"></a><span data-ttu-id="1d8ce-136">使用 SQL Server 複寫監視器</span><span class="sxs-lookup"><span data-stu-id="1d8ce-136">Using SQL Server Replication Monitor</span></span>  
 <span data-ttu-id="1d8ce-137">如需啟動複寫監視器的詳細資訊，請參閱[啟動複寫監視器](start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-137">For information about starting Replication Monitor, see [Start the Replication Monitor](start-the-replication-monitor.md).</span></span>  
  
#### <a name="to-insert-a-tracer-token-and-view-information-on-the-token"></a><span data-ttu-id="1d8ce-138">插入追蹤 Token 並檢視 Token 上的資訊</span><span class="sxs-lookup"><span data-stu-id="1d8ce-138">To insert a tracer token and view information on the token</span></span>  
  
1.  <span data-ttu-id="1d8ce-139">在左窗格中展開發行者群組，展開發行者，然後按一下發行集。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-139">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="1d8ce-140">按一下 **[追蹤 Token]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-140">Click the **Tracer Tokens** tab.</span></span>  
  
3.  <span data-ttu-id="1d8ce-141">按一下 **[插入追蹤]**。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-141">Click **Insert Tracer**.</span></span>  
  
4.  <span data-ttu-id="1d8ce-142">在下列資料行中檢視追蹤 Token 的經過時間： **[發行者到散發者]**、 **[散發者到訂閱者]**、 **[延遲總計]**。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-142">View elapsed time for the tracer token in the following columns: **Publisher to Distributor**, **Distributor to Subscriber**, **Total Latency**.</span></span> <span data-ttu-id="1d8ce-143">值為 [**暫**止] 表示 token 尚未到達指定的點。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-143">A value of **Pending** indicates that the token has not reached a given point.</span></span>  
  
#### <a name="to-view-information-on-a-tracer-token-inserted-previously"></a><span data-ttu-id="1d8ce-144">若要檢視先前插入之追蹤 Token 上的訊息</span><span class="sxs-lookup"><span data-stu-id="1d8ce-144">To view information on a tracer token inserted previously</span></span>  
  
1.  <span data-ttu-id="1d8ce-145">在左窗格中展開發行者群組，展開發行者，然後按一下發行集。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-145">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="1d8ce-146">按一下 **[追蹤 Token]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-146">Click the **Tracer Tokens** tab.</span></span>  
  
3.  <span data-ttu-id="1d8ce-147">從 **[插入的時間]** 下拉式清單中選取時間。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-147">Select a time from the **Time inserted** drop-down list.</span></span>  
  
4.  <span data-ttu-id="1d8ce-148">在下列資料行中檢視追蹤 Token 的經過時間： **[發行者到散發者]**、 **[散發者到訂閱者]**、 **[延遲總計]**。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-148">View elapsed time for the tracer token in the following columns: **Publisher to Distributor**, **Distributor to Subscriber**, **Total Latency**.</span></span> <span data-ttu-id="1d8ce-149">值為 [**暫**止] 表示 token 尚未到達指定的點。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-149">A value of **Pending** indicates that the token has not reached a given point.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1d8ce-150">追蹤 Token 資訊與其他記錄資料的保留時間週期相同，這會由散發資料庫的記錄保留期限控制。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-150">Tracer token information is retained for the same time period as other historical data, which is governed by the history retention period of the distribution database.</span></span> <span data-ttu-id="1d8ce-151">如需變更散發資料庫屬性的詳細資訊，請參閱[檢視及修改散發者和發行者屬性](../view-and-modify-distributor-and-publisher-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-151">For information about changing distribution database properties, see [View and Modify Distributor and Publisher Properties](../view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1d8ce-152">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1d8ce-152">Using Transact-SQL</span></span>  
  
#### <a name="to-post-a-tracer-token-to-a-transactional-publication"></a><span data-ttu-id="1d8ce-153">若要將追蹤 Token 公佈到交易式發行集</span><span class="sxs-lookup"><span data-stu-id="1d8ce-153">To post a tracer token to a transactional publication</span></span>  
  
1.  <span data-ttu-id="1d8ce-154">(選擇性) 在發行集資料庫的發行者上，執行 [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-154">(Optional) At the Publisher on the publication database, execute [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> <span data-ttu-id="1d8ce-155">請確認發行集存在且狀態為使用中。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-155">Verify that the publication exists and that the status is active.</span></span>  
  
2.  <span data-ttu-id="1d8ce-156">(選擇性) 在發行集資料庫的發行者上，執行 [sp_helpsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-156">(Optional) At the Publisher on the publication database, execute [sp_helpsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).</span></span> <span data-ttu-id="1d8ce-157">請確認訂閱存在且狀態為使用中。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-157">Verify that the subscription exists and that the status is active.</span></span>  
  
3.  <span data-ttu-id="1d8ce-158">在發行集資料庫的發行者上，執行 [sp_posttracertoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql)，並指定 **@publication**。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-158">At the Publisher on the publication database, execute [sp_posttracertoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql), specifying **@publication**.</span></span> <span data-ttu-id="1d8ce-159">請注意 **@tracer_token_id** 輸出參數的值。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-159">Note the value of the **@tracer_token_id** output parameter.</span></span>  
  
#### <a name="to-determine-latency-and-validate-connections-for-a-transactional-publication"></a><span data-ttu-id="1d8ce-160">若要針對異動複寫判斷延遲並驗證連接</span><span class="sxs-lookup"><span data-stu-id="1d8ce-160">To determine latency and validate connections for a transactional publication</span></span>  
  
1.  <span data-ttu-id="1d8ce-161">使用上一個程序將追蹤 Token 公佈到發行集。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-161">Post a tracer token to the publication using the previous procedure.</span></span>  
  
2.  <span data-ttu-id="1d8ce-162">在發行集資料庫的發行者上，執行 [sp_helptracertokens &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql)，並指定 **@publication**。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-162">At the Publisher on the publication database, execute [sp_helptracertokens &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql), specifying **@publication**.</span></span> <span data-ttu-id="1d8ce-163">如此會傳回公佈到發行集的所有追蹤 Token 清單。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-163">This returns a list of all tracer tokens posted to the publication.</span></span> <span data-ttu-id="1d8ce-164">請注意結果集中所要的 **tracer_id** 。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-164">Note the desired **tracer_id** in the result set.</span></span>  
  
3.  <span data-ttu-id="1d8ce-165">在發行集資料庫的發行者上，執行 [sp_helptracertokenhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql)，並指定 **@publication**，而且針對 **@tracer_id** 指定步驟 2 的追追蹤 Token 識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-165">At the Publisher on the publication database, execute [sp_helptracertokenhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql), specifying **@publication** and the tracer token ID from step 2 for **@tracer_id**.</span></span> <span data-ttu-id="1d8ce-166">這麼做會傳回所選取追蹤 Token 的延遲資訊。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-166">This returns latency information for the selected tracer token.</span></span>  
  
#### <a name="to-remove-tracer-tokens"></a><span data-ttu-id="1d8ce-167">若要移除追蹤 Token</span><span class="sxs-lookup"><span data-stu-id="1d8ce-167">To remove tracer tokens</span></span>  
  
1.  <span data-ttu-id="1d8ce-168">在發行集資料庫的發行者上，執行 [sp_helptracertokens &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql)，並指定 **@publication**。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-168">At the Publisher on the publication database, execute [sp_helptracertokens &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql), specifying **@publication**.</span></span> <span data-ttu-id="1d8ce-169">如此會傳回公佈到發行集的所有追蹤 Token 清單。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-169">This returns a list of all tracer tokens posted to the publication.</span></span> <span data-ttu-id="1d8ce-170">請注意結果集中要刪除之追蹤 Token 的 **tracer_id** 。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-170">Note the **tracer_id** for the tracer token to delete in the result set.</span></span>  
  
2.  <span data-ttu-id="1d8ce-171">在發行集資料庫的發行者上，執行 [sp_deletetracertokenhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql)，並指定 **@publication**，而且針對 **@tracer_id** 指定步驟 2 的要刪除的追蹤識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-171">At the Publisher on the publication database, execute [sp_deletetracertokenhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql), specifying **@publication** and the ID of the tracer to delete from step 2 for **@tracer_id**.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="1d8ce-172">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1d8ce-172">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="1d8ce-173">這麼做會公佈追蹤 Token 記錄，並使用傳回的公佈追蹤 Token 識別碼檢視延遲資訊。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-173">This example posts a tracer token record and uses the returned ID of the posted tracer token to view latency information.</span></span>  
  
 [!code-sql[HowTo#sp_tracertokens](../../../snippets/tsql/SQL15/replication/howto/tsql/createtracertokens.sql#sp_tracertokens)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="1d8ce-174">使用 Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="1d8ce-174">Using Replication Management Objects (RMO)</span></span>  
  
#### <a name="to-post-a-tracer-token-to-a-transactional-publication"></a><span data-ttu-id="1d8ce-175">若要將追蹤 Token 公佈到交易式發行集</span><span class="sxs-lookup"><span data-stu-id="1d8ce-175">To post a tracer token to a transactional publication</span></span>  
  
1.  <span data-ttu-id="1d8ce-176">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-176">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="1d8ce-177">建立 <xref:Microsoft.SqlServer.Replication.TransPublication> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-177">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPublication> class.</span></span>  
  
3.  <span data-ttu-id="1d8ce-178">設定發行集的 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 和 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 屬性，並將 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定為在步驟 1 中建立的連接。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-178">Set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="1d8ce-179">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-179">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="1d8ce-180">如果此方法傳回 `false`，則表示步驟 3 中的發行集屬性定義不正確，或者該發行集不存在。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-180">If this method returns `false`, either the publication properties in step 3 were defined incorrectly or the publication does not exist.</span></span>  
  
5.  <span data-ttu-id="1d8ce-181">呼叫 <xref:Microsoft.SqlServer.Replication.TransPublication.PostTracerToken%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-181">Call the <xref:Microsoft.SqlServer.Replication.TransPublication.PostTracerToken%2A> method.</span></span> <span data-ttu-id="1d8ce-182">此方法會將追蹤 Token 插入至發行集的交易記錄。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-182">This method inserts a tracer token into the publication's transaction log.</span></span>  
  
#### <a name="to-determine-latency-and-validate-connections-for-a-transactional-publication"></a><span data-ttu-id="1d8ce-183">若要針對異動複寫判斷延遲並驗證連接</span><span class="sxs-lookup"><span data-stu-id="1d8ce-183">To determine latency and validate connections for a transactional publication</span></span>  
  
1.  <span data-ttu-id="1d8ce-184">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與散發者的連接。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-184">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="1d8ce-185">建立 <xref:Microsoft.SqlServer.Replication.PublicationMonitor> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-185">Create an instance of the <xref:Microsoft.SqlServer.Replication.PublicationMonitor> class.</span></span>  
  
3.  <span data-ttu-id="1d8ce-186">設定 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>和 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> 屬性，並將 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定為在步驟 1 中建立的連接。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-186">Set the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> properties, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="1d8ce-187">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-187">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="1d8ce-188">如果此方法傳回 `false`，則表示步驟 3 中的發行集監視器屬性定義不正確，或者該發行集不存在。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-188">If this method returns `false`, either the publication monitor properties in step 3 were defined incorrectly or the publication does not exist.</span></span>  
  
5.  <span data-ttu-id="1d8ce-189">呼叫 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-189">Call the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> method.</span></span> <span data-ttu-id="1d8ce-190">將傳回的 <xref:System.Collections.ArrayList> 物件轉換為 <xref:Microsoft.SqlServer.Replication.TracerToken> 物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-190">Cast the returned <xref:System.Collections.ArrayList> object to an array of <xref:Microsoft.SqlServer.Replication.TracerToken> objects.</span></span>  
  
6.  <span data-ttu-id="1d8ce-191">呼叫 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokenHistory%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-191">Call the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokenHistory%2A> method.</span></span> <span data-ttu-id="1d8ce-192">針對步驟 5 的追蹤 Token 傳遞 <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> 的值。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-192">Pass a value of <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> for a tracer token from step 5.</span></span> <span data-ttu-id="1d8ce-193">這麼做會以 <xref:System.Data.DataSet> 物件傳回所選取追蹤 Token 的延遲資訊。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-193">This returns latency information for the selected tracer token as a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="1d8ce-194">如果傳回所有的追蹤 Token，則「發行者」和「散發者」之間的連接以及「散發者」和「訂閱者」之間的連接兩者都存在，且複寫拓撲可以運作。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-194">If all tracer token information is returned, the connection between the Publisher and Distributor and the connection between the Distributor and the Subscriber both exist and the replication topology is functioning.</span></span>  
  
#### <a name="to-remove-tracer-tokens"></a><span data-ttu-id="1d8ce-195">若要移除追蹤 Token</span><span class="sxs-lookup"><span data-stu-id="1d8ce-195">To remove tracer tokens</span></span>  
  
1.  <span data-ttu-id="1d8ce-196">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與散發者的連接。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-196">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="1d8ce-197">建立 <xref:Microsoft.SqlServer.Replication.PublicationMonitor> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-197">Create an instance of the <xref:Microsoft.SqlServer.Replication.PublicationMonitor> class.</span></span>  
  
3.  <span data-ttu-id="1d8ce-198">設定 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>和 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> 屬性，並將 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定為在步驟 1 中建立的連接。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-198">Set the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> properties, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="1d8ce-199">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-199">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="1d8ce-200">如果此方法傳回 `false`，則表示步驟 3 中的發行集監視器屬性定義不正確，或者該發行集不存在。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-200">If this method returns `false`, either the publication monitor properties in step 3 were defined incorrectly or the publication does not exist.</span></span>  
  
5.  <span data-ttu-id="1d8ce-201">呼叫 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-201">Call the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> method.</span></span> <span data-ttu-id="1d8ce-202">將傳回的 <xref:System.Collections.ArrayList> 物件轉換為 <xref:Microsoft.SqlServer.Replication.TracerToken> 物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-202">Cast the returned <xref:System.Collections.ArrayList> object to an array of <xref:Microsoft.SqlServer.Replication.TracerToken> objects.</span></span>  
  
6.  <span data-ttu-id="1d8ce-203">呼叫 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.CleanUpTracerTokenHistory%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-203">Call the <xref:Microsoft.SqlServer.Replication.PublicationMonitor.CleanUpTracerTokenHistory%2A> method.</span></span> <span data-ttu-id="1d8ce-204">傳遞其中一個值：</span><span class="sxs-lookup"><span data-stu-id="1d8ce-204">Pass one of the following values:</span></span>  
  
    -   <span data-ttu-id="1d8ce-205">步驟 5 追蹤 Token 的 <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> 。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-205">The <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> for a tracer token from step 5.</span></span> <span data-ttu-id="1d8ce-206">這麼做會刪除所選取 Token 的資訊。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-206">This deletes information for a selected token.</span></span>  
  
    -   <span data-ttu-id="1d8ce-207"><xref:System.DateTime> 物件。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-207">A <xref:System.DateTime> object.</span></span> <span data-ttu-id="1d8ce-208">這麼做會刪除所有早於指定日期和時間的 Token 資訊。</span><span class="sxs-lookup"><span data-stu-id="1d8ce-208">This deletes information for all tokens older than the specified date and time.</span></span>  
  
###  <a name="PShellExample"></a>  
