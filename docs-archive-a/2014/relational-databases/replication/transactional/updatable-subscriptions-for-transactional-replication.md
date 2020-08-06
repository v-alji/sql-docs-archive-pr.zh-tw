---
title: 異動複寫的可更新訂閱 | Microsoft 文件
ms.custom: ''
ms.date: 03/31/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, updatable subscriptions
- updatable subscriptions, about updatable subscriptions
- queued updating subscriptions [SQL Server replication]
- immediate updating subscriptions
- subscriptions [SQL Server replication], updatable
- updatable subscriptions
ms.assetid: 8eec95cb-3a11-436e-bcee-bdcd05aa5c5a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e0b739ffe34a14519ff5290c406805ff7715edce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606738"
---
# <a name="updatable-subscriptions-for-transactional-replication"></a><span data-ttu-id="525f2-102">Updatable Subscriptions for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="525f2-102">Updatable Subscriptions for Transactional Replication</span></span>

<span data-ttu-id="525f2-103">**適用物件：** SQL Server 2008 (和更新版本) </span><span class="sxs-lookup"><span data-stu-id="525f2-103">**Applies to:** SQL Server 2008 (and later)</span></span>

    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
<span data-ttu-id="525f2-104">在 SQL Server 2014 中，異動複寫透過可更新的訂閱和點對點複寫支援訂閱者端的更新。</span><span class="sxs-lookup"><span data-stu-id="525f2-104">In SQL Server 2014, transactional replication supports updates at Subscribers through updatable subscriptions and peer-to-peer replication.</span></span> <span data-ttu-id="525f2-105">以下是兩種可以更新的訂閱類型：</span><span class="sxs-lookup"><span data-stu-id="525f2-105">The following are the two types of updatable subscriptions:</span></span>  
  
-   <span data-ttu-id="525f2-106">立即更新。</span><span class="sxs-lookup"><span data-stu-id="525f2-106">Immediate updating.</span></span> <span data-ttu-id="525f2-107">發行者和訂閱者必須連接，以便更新訂閱者端的資料。</span><span class="sxs-lookup"><span data-stu-id="525f2-107">The Publisher and Subscriber must be connected to update data at the Subscriber.</span></span>  
  
-   <span data-ttu-id="525f2-108">佇列更新。發行者和訂閱者不必連接，即可更新訂閱者端的資料。</span><span class="sxs-lookup"><span data-stu-id="525f2-108">Queued updating The Publisher and Subscriber do not have to be connected to update data at the Subscriber.</span></span> <span data-ttu-id="525f2-109">更新可在訂閱者或發行者離線時進行。</span><span class="sxs-lookup"><span data-stu-id="525f2-109">Updates can be made while the Subscriber or Publisher is offline.</span></span>  
  
 <span data-ttu-id="525f2-110">當資料在訂閱者端更新時，它會先傳播至發行者，然後再傳播至其他訂閱者。</span><span class="sxs-lookup"><span data-stu-id="525f2-110">When data is updated at a Subscriber, it is first propagated to the Publisher and then propagated to other Subscribers.</span></span> <span data-ttu-id="525f2-111">如果使用立即更新，則透過使用兩階段認可通訊協定，變更會立即傳播。</span><span class="sxs-lookup"><span data-stu-id="525f2-111">If immediate updating is used, the changes are propagated immediately using the two-phase commit protocol.</span></span> <span data-ttu-id="525f2-112">如果使用佇列更新，則變更會儲存於佇列中；然後，佇列交易會在網路連接可用時，在發行者端上非同步套用。</span><span class="sxs-lookup"><span data-stu-id="525f2-112">If queued updating is used, the changes are stored in a queue; the queued transactions are then applied asynchronously at the Publisher whenever network connectivity is available.</span></span> <span data-ttu-id="525f2-113">因為更新會非同步地傳播到「發行者」，因此相同的資料可能已經被「發行者」或另一個「訂閱者」更新過，所以在套用更新時可能會出現衝突。</span><span class="sxs-lookup"><span data-stu-id="525f2-113">Because the updates are propagated asynchronously to the Publisher, the same data may have been updated by the Publisher or by another Subscriber and conflicts can occur when applying the updates.</span></span> <span data-ttu-id="525f2-114">衝突會偵測出來，並且根據建立發行集時設定的衝突解決原則來解決。</span><span class="sxs-lookup"><span data-stu-id="525f2-114">Conflicts are detected and resolved according to a conflict resolution policy that is set when creating the publication.</span></span>  
  
 <span data-ttu-id="525f2-115">如果在「新增發行集精靈」中建立具有可更新訂閱的交易式發行集，則會啟用立即更新和佇列更新。</span><span class="sxs-lookup"><span data-stu-id="525f2-115">If you create a transactional publication with updatable subscriptions in the New Publication Wizard, both immediate updating and queued updating are enabled.</span></span> <span data-ttu-id="525f2-116">如果以預存程序建立發行集，則可啟用一個或兩個選項。</span><span class="sxs-lookup"><span data-stu-id="525f2-116">If you create a publication with stored procedures, you can enable one or both options.</span></span> <span data-ttu-id="525f2-117">建立發行集的訂閱時，則需指定要使用的更新模式。</span><span class="sxs-lookup"><span data-stu-id="525f2-117">When you create a subscription to the publication, you specify which update mode to use.</span></span> <span data-ttu-id="525f2-118">必要時，可切換更新模式。</span><span class="sxs-lookup"><span data-stu-id="525f2-118">You can then switch between update modes if necessary.</span></span> <span data-ttu-id="525f2-119">如需詳細資訊，請參閱下面的＜切換更新模式＞一節。</span><span class="sxs-lookup"><span data-stu-id="525f2-119">For more information, see the following section "Switching between Update Modes".</span></span>  
  
 <span data-ttu-id="525f2-120">若要為交易式發行集啟用可更新的訂閱，請參閱＜ [Enable Updating Subscriptions for Transactional Publications](../publish/enable-updating-subscriptions-for-transactional-publications.md)＞。</span><span class="sxs-lookup"><span data-stu-id="525f2-120">To enable updatable subscriptions for transactional publications, [Enable Updating Subscriptions for Transactional Publications](../publish/enable-updating-subscriptions-for-transactional-publications.md)</span></span>  
  
 <span data-ttu-id="525f2-121">若為交易式發行集建立可更新的訂閱，請參閱＜ [Create an Updatable Subscription to a Transactional Publication](../publish/create-an-updatable-subscription-to-a-transactional-publication.md)＞。</span><span class="sxs-lookup"><span data-stu-id="525f2-121">To create updatable subscriptions for transactional publications, see [Create an Updatable Subscription to a Transactional Publication](../publish/create-an-updatable-subscription-to-a-transactional-publication.md)</span></span>  
  
## <a name="switching-between-update-modes"></a><span data-ttu-id="525f2-122">切換更新模式</span><span class="sxs-lookup"><span data-stu-id="525f2-122">Switching Between Update Modes</span></span>  
 <span data-ttu-id="525f2-123">使用可更新訂閱時，可以指定訂閱應使用一個更新模式，如果應用程式有所要求，再切換至另一個更新模式。</span><span class="sxs-lookup"><span data-stu-id="525f2-123">When using updatable subscriptions you can specify that a subscription should use one update mode and then switch to the other if the application requires it.</span></span> <span data-ttu-id="525f2-124">例如，您可以指定訂閱應使用立即更新，但是如果系統錯誤造成失去網路連接，則切換至佇列更新。</span><span class="sxs-lookup"><span data-stu-id="525f2-124">For example, you can specify that a subscription should use immediate updating, but switch to queued updating if a system failure results in the loss of network connectivity.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="525f2-125">複寫不會自動切換更新模式。</span><span class="sxs-lookup"><span data-stu-id="525f2-125">Replication does not switch automatically between update modes.</span></span> <span data-ttu-id="525f2-126">您必須透過 SQL Server Management Studio 設定更新模式，或者您的應用程式必須呼叫 [sp_setreplfailovermode &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql) 模式，才能在兩種模式之間切換。</span><span class="sxs-lookup"><span data-stu-id="525f2-126">You must set the update mode through SQL Server Management Studio or your application must call [sp_setreplfailovermode &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql) to switch between modes.</span></span>  
  
 <span data-ttu-id="525f2-127">如果從立即更新切換至佇列更新，則在「訂閱者」和「發行者」連接，且「佇列讀取器代理程式」將佇列中所有暫止訊息套用至「發行者」之前，無法切換回立即更新。</span><span class="sxs-lookup"><span data-stu-id="525f2-127">If you switch from immediate updating to queued updating, you cannot switch back to immediate updating until the Subscriber and Publisher are connected and the Queue Reader Agent has applied all pending messages in the queue to the Publisher.</span></span>  
  
 <span data-ttu-id="525f2-128">**切換更新模式**</span><span class="sxs-lookup"><span data-stu-id="525f2-128">**To switch between update modes**</span></span>  
  
 <span data-ttu-id="525f2-129">若要切換更新模式，則必須啟用兩種更新模式的發行集和訂閱，然後必要時在它們之間進行切換。</span><span class="sxs-lookup"><span data-stu-id="525f2-129">To switch between updating modes, you must enable the publication and subscription for both update modes, and then switch between them if necessary.</span></span> <span data-ttu-id="525f2-130">如需相關資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="525f2-130">For more information, see</span></span>  
<span data-ttu-id="525f2-131">[切換可更新之交易式訂閱的更新模式](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="525f2-131">[Switch Between Update Modes for an Updatable Transactional Subscription](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).</span></span>  
  
### <a name="considerations-for-using-updatable-subscriptions"></a><span data-ttu-id="525f2-132">使用可更新訂閱之考量</span><span class="sxs-lookup"><span data-stu-id="525f2-132">Considerations for Using Updatable Subscriptions</span></span>  
  
-   <span data-ttu-id="525f2-133">在更新訂閱或佇列更新訂閱啟用發行集後，則無法停用該發行集的選項 (雖然訂閱不需要使用該選項)。</span><span class="sxs-lookup"><span data-stu-id="525f2-133">After a publication is enabled for updating subscriptions or queued updating subscriptions, the option cannot be disabled for the publication (although subscriptions do not need to use it).</span></span> <span data-ttu-id="525f2-134">若要停用該選項，則必須刪除發行集並建立一個新的發行集。</span><span class="sxs-lookup"><span data-stu-id="525f2-134">To disable the option, the publication must be deleted and a new one created.</span></span>  
  
-   <span data-ttu-id="525f2-135">不支援重新發行資料。</span><span class="sxs-lookup"><span data-stu-id="525f2-135">Republishing data is not supported.</span></span>  
  
-   <span data-ttu-id="525f2-136">複寫將 **msrepl_tran_version** 資料行加入已發行的資料表中，用來進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="525f2-136">Replication adds the **msrepl_tran_version** column to published tables for tracking purposes.</span></span> <span data-ttu-id="525f2-137">因為這是新增的資料行，所以所有 `INSERT` 陳述式均應包含資料行清單。</span><span class="sxs-lookup"><span data-stu-id="525f2-137">Because of this additional column, all `INSERT` statements should include a column list.</span></span>  
  
-   <span data-ttu-id="525f2-138">若要在支援更新訂閱的發行集之資料表中進行結構描述變更，則必須停止「發行者」和「訂閱者」上所有資料表的活動，且暫止資料變更必須在進行任何結構描述變更前傳播至所有節點。</span><span class="sxs-lookup"><span data-stu-id="525f2-138">To make schema changes on a table in a publication that supports updating subscriptions, all activity on the table must be stopped at the Publisher and Subscribers, and pending data changes must be propagated to all nodes before making any schema changes.</span></span> <span data-ttu-id="525f2-139">這會確保未處理完畢的交易不與暫止結構描述變更發生衝突。</span><span class="sxs-lookup"><span data-stu-id="525f2-139">This ensures that outstanding transactions do not conflict with the pending schema change.</span></span> <span data-ttu-id="525f2-140">結構描述變更傳播至所有節點之後，可於已發行的資料表上繼續進行活動。</span><span class="sxs-lookup"><span data-stu-id="525f2-140">After the schema changes have propagated to all nodes, activity can resume on the published tables.</span></span> <span data-ttu-id="525f2-141">如需詳細資訊，請參閱[停止複寫拓撲 &#40;複寫 Transact-SQL 程式設計&#41;](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="525f2-141">For more information, see [Quiesce a Replication Topology &#40;Replication Transact-SQL Programming&#41;](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md).</span></span>  
  
-   <span data-ttu-id="525f2-142">如果計劃切換更新模式，則「佇列讀取器代理程式」在訂閱初始化後必須至少執行一次 (依預設，「佇列讀取器代理程式」會持續執行)。</span><span class="sxs-lookup"><span data-stu-id="525f2-142">If you plan to switch between update modes, the Queue Reader Agent must run at least once after the subscription has been initialized (by default, the Queue Reader Agent runs continuously).</span></span>  
  
-   <span data-ttu-id="525f2-143">如果「訂閱者」資料庫是水平分割，且在此分割中有存在於訂閱者端，而非在發行者端的資料列，則訂閱者無法更新這些已經存在的資料列。</span><span class="sxs-lookup"><span data-stu-id="525f2-143">If the Subscriber database is partitioned horizontally and there are rows in the partition that exist at the Subscriber, but not at the Publisher, the Subscriber cannot update the preexisting rows.</span></span> <span data-ttu-id="525f2-144">嘗試更新這些資料列會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="525f2-144">Attempting to update these rows returns an error.</span></span> <span data-ttu-id="525f2-145">資料列應該從資料表刪除，然後在發行者端加入。</span><span class="sxs-lookup"><span data-stu-id="525f2-145">The rows should be deleted from the table and then added at the Publisher.</span></span>  
  
### <a name="updates-at-the-subscriber"></a><span data-ttu-id="525f2-146">在訂閱者端的更新</span><span class="sxs-lookup"><span data-stu-id="525f2-146">Updates at the Subscriber</span></span>  
  
-   <span data-ttu-id="525f2-147">即使訂閱已過期或為非使用中，訂閱者端的更新也會傳播至發行者。</span><span class="sxs-lookup"><span data-stu-id="525f2-147">Updates at the Subscriber are propagated to the Publisher even if a subscription is expired or is inactive.</span></span> <span data-ttu-id="525f2-148">請確定所有此類訂閱都已卸除或重新初始化。</span><span class="sxs-lookup"><span data-stu-id="525f2-148">Ensure that any such subscriptions are either dropped or reinitialized.</span></span>  
  
-   <span data-ttu-id="525f2-149">若使用 `TIMESTAMP` 或 `IDENTITY` 資料行，且這兩個資料行在複寫時成為其基底資料類型，就不應更新訂閱者中這些資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="525f2-149">If `TIMESTAMP` or `IDENTITY` columns are used, and they are replicated as their base data types, values in these columns should not be updated at the Subscriber.</span></span>  
  
-   <span data-ttu-id="525f2-150">因為訂閱者無法從複寫變更追蹤觸發器中所插入或刪除的資料表中讀取 `text`、`ntext` 或 `image` 值，所以訂閱者無法更新或插入這些值。</span><span class="sxs-lookup"><span data-stu-id="525f2-150">Subscribers cannot update or insert `text`, `ntext` or `image` values because it is not possible to read from the inserted or deleted tables inside the replication change-tracking triggers.</span></span> <span data-ttu-id="525f2-151">因為資料會由發行者所覆寫，所以訂閱者也同樣無法使用 `WRITETEXT` 或 `UPDATETEXT` 更新或插入 `text` 或 `image` 值。</span><span class="sxs-lookup"><span data-stu-id="525f2-151">Similarly, Subscribers cannot update or insert `text` or `image` values using `WRITETEXT` or `UPDATETEXT` because the data is overwritten by the Publisher.</span></span> <span data-ttu-id="525f2-152">您反而可以將 `text` 及 `image` 資料行分割到不同的資料表，並在交易中修改這兩個資料表。</span><span class="sxs-lookup"><span data-stu-id="525f2-152">Instead, you could partition the `text` and `image` columns into a separate table and modify the two tables within a transaction.</span></span>  
  
     <span data-ttu-id="525f2-153">若要更新訂閱者中的大型物件，請使用資料類型 `varchar(max)`、`nvarchar(max)`、`varbinary(max)`，而不要個別使用 `text`、`ntext` 及 `image` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="525f2-153">To update large objects at a Subscriber, use the data types `varchar(max)`, `nvarchar(max)`, `varbinary(max)` instead of `text`, `ntext`, and `image` data types, respectively.</span></span>  
  
-   <span data-ttu-id="525f2-154">若更新專用索引鍵 (包含主索引鍵) 會造成重複 (例如更新格式 `UPDATE <column> SET <column> =<column>+1` )，將無法執行此作業，而且會因為違反不重複原則而遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="525f2-154">Updates to unique keys (including primary keys) that generate duplicates (for example, an update of the form `UPDATE <column> SET <column> =<column>+1` are not allowed and will be rejected because of a uniqueness violation.</span></span> <span data-ttu-id="525f2-155">這是因為在訂閱者進行的設定更新，會在每個資料列受到影響時，透過複寫方式個別的 `UPDATE` 陳述式進行傳播。</span><span class="sxs-lookup"><span data-stu-id="525f2-155">This is because set updates made at the Subscriber are propagated by replication as individual `UPDATE` statements for each row affected.</span></span>  
  
-   <span data-ttu-id="525f2-156">如果「訂閱者」資料庫是水平分割，且在此分割中有存在於「訂閱者」端，而非在「發行者」端的資料列，則「訂閱者」無法更新這些已經存在的資料列。</span><span class="sxs-lookup"><span data-stu-id="525f2-156">If the Subscriber database is partitioned horizontally and there are rows in the partition that exist at the Subscriber but not at the Publisher, the Subscriber cannot update the pre-existing rows.</span></span> <span data-ttu-id="525f2-157">嘗試更新這些資料列會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="525f2-157">Attempting to update these rows returns an error.</span></span> <span data-ttu-id="525f2-158">資料列應該從資料表刪除，然後再次插入。</span><span class="sxs-lookup"><span data-stu-id="525f2-158">The rows should be deleted from the table and inserted again.</span></span>  
  
### <a name="user-defined-triggers"></a><span data-ttu-id="525f2-159">使用者自訂觸發程序</span><span class="sxs-lookup"><span data-stu-id="525f2-159">User-defined Triggers</span></span>  
  
-   <span data-ttu-id="525f2-160">若應用程式在訂閱者需要觸發器，便應使用 `NOT FOR REPLICATION` 選項同時在發行者與訂閱者定義觸發器。</span><span class="sxs-lookup"><span data-stu-id="525f2-160">If the application requires triggers at the Subscriber, the triggers should be defined with the `NOT FOR REPLICATION` option at the Publisher and Subscriber.</span></span> <span data-ttu-id="525f2-161">這會確保觸發器僅為原始資料變更而引發，而不會在複寫變更時引發。</span><span class="sxs-lookup"><span data-stu-id="525f2-161">This ensures that triggers fire only for the original data change, but not when that change is replicated.</span></span>  
  
     <span data-ttu-id="525f2-162">請確保複寫觸發器更新資料表時不會引發使用者自訂的觸發器。</span><span class="sxs-lookup"><span data-stu-id="525f2-162">Ensure that the user-defined trigger does not fire when the replication trigger updates the table.</span></span> <span data-ttu-id="525f2-163">這可藉由在使用者定義的觸發程式主體中呼叫 `sp_check_for_sync_trigger` 程序達成。</span><span class="sxs-lookup"><span data-stu-id="525f2-163">This is accomplished by calling the procedure `sp_check_for_sync_trigger` in the body of the user-defined trigger.</span></span> <span data-ttu-id="525f2-164">如需詳細資訊，請參閱 [sp_check_for_sync_trigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-check-for-sync-trigger-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="525f2-164">For more information, see [sp_check_for_sync_trigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-check-for-sync-trigger-transact-sql).</span></span>  
  
### <a name="immediate-updating"></a><span data-ttu-id="525f2-165">立即更新</span><span class="sxs-lookup"><span data-stu-id="525f2-165">Immediate Updating</span></span>  
  
-   <span data-ttu-id="525f2-166">對於立即更新訂閱，「訂閱者」端的變更會傳播至「發行者」，並使用「Microsoft 分散式交易協調器」(MS DTC) 來套用。</span><span class="sxs-lookup"><span data-stu-id="525f2-166">For immediate updating subscriptions, changes at the Subscriber are propagated to the Publisher and applied using Microsoft Distributed Transaction Coordinator (MS DTC).</span></span> <span data-ttu-id="525f2-167">請確定已在「發行者」和「訂閱者」端安裝並設定了 MS DTC。</span><span class="sxs-lookup"><span data-stu-id="525f2-167">Ensure that MS DTC is installed and configured at the Publisher and Subscriber.</span></span> <span data-ttu-id="525f2-168">如需詳細資訊，請參閱 Windows 文件集。</span><span class="sxs-lookup"><span data-stu-id="525f2-168">For more information, see the Windows documentation.</span></span>  
  
-   <span data-ttu-id="525f2-169">立即更新訂閱使用的觸發器要求連接到「發行者」以複寫變更。</span><span class="sxs-lookup"><span data-stu-id="525f2-169">The triggers used by immediate updating subscriptions require a connection to the Publisher to replicate changes.</span></span>  
  
-   <span data-ttu-id="525f2-170">如果發行集允許立即更新訂閱，且發行集中的發行項具有資料行篩選，則無法篩選無預設值的不可為 Null 資料行。</span><span class="sxs-lookup"><span data-stu-id="525f2-170">If the publication allows immediate updating subscriptions and an article in the publication has a column filter, you cannot filter out non-nullable columns without defaults.</span></span>  
  
### <a name="queued-updating"></a><span data-ttu-id="525f2-171">佇列更新</span><span class="sxs-lookup"><span data-stu-id="525f2-171">Queued Updating</span></span>  
  
-   <span data-ttu-id="525f2-172">包含在合併式發行集的資料表也無法發行為允許佇列更新訂閱的部分交易式發行集。</span><span class="sxs-lookup"><span data-stu-id="525f2-172">Tables included in a merge publication cannot also be published as part of a transactional publication that allows queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="525f2-173">在使用佇立更新時，不建議更新主索引鍵資料行，這是因為主索引鍵是所有查詢的記錄定位器。</span><span class="sxs-lookup"><span data-stu-id="525f2-173">Updates made to primary key columns are not recommended when using queued updating because the primary key is used as a record locator for all queries.</span></span> <span data-ttu-id="525f2-174">若衝突解決原則是設為「訂閱者優先」，則應在更新主索引鍵時多加注意。</span><span class="sxs-lookup"><span data-stu-id="525f2-174">When the conflict resolution policy is set to Subscriber Wins, updates to primary keys should be made with caution.</span></span> <span data-ttu-id="525f2-175">若「發行者」與「訂閱者」的主索引鍵均更新，則結果將會是有著不同主索引鍵的兩資料列。</span><span class="sxs-lookup"><span data-stu-id="525f2-175">If updates to the primary key are made at both the Publisher and at the Subscriber, the result will be two rows with different primary keys.</span></span>  
  
-   <span data-ttu-id="525f2-176">對於資料類型為 `SQL_VARIANT` 的資料行：當在訂閱者插入或更新資料後，資料會在從訂閱者複製到佇列時，由佇列讀取器代理程式以下列方式加以對應：</span><span class="sxs-lookup"><span data-stu-id="525f2-176">For columns of data type `SQL_VARIANT`: when data is inserted or updated at the Subscriber, it is mapped in the following way by the Queue Reader Agent when it is copied from the Subscriber to the queue:</span></span>  
  
    -   <span data-ttu-id="525f2-177">`BIGINT`、`DECIMAL`、`NUMERIC`、`MONEY` 和 `SMALLMONEY` 對應至 `NUMERIC`。</span><span class="sxs-lookup"><span data-stu-id="525f2-177">`BIGINT`, `DECIMAL`, `NUMERIC`, `MONEY`, and `SMALLMONEY` are mapped to `NUMERIC`.</span></span>  
  
    -   <span data-ttu-id="525f2-178">`BINARY` 和 `VARBINARY` 對應至 `VARBINARY` 資料。</span><span class="sxs-lookup"><span data-stu-id="525f2-178">`BINARY` and `VARBINARY` are mapped to `VARBINARY` data.</span></span>  
  
### <a name="conflict-detection-and-resolution"></a><span data-ttu-id="525f2-179">衝突偵測與解決方案</span><span class="sxs-lookup"><span data-stu-id="525f2-179">Conflict Detection and Resolution</span></span>  
  
-   <span data-ttu-id="525f2-180">對於「訂閱者成功」衝突原則：至主索引鍵資料行的更新不支援衝突解決。</span><span class="sxs-lookup"><span data-stu-id="525f2-180">For the Subscriber Wins conflict policy: conflict resolution is not supported for updates to primary key columns.</span></span>  
  
-   <span data-ttu-id="525f2-181">複寫不會解決因外部索引鍵條件約束錯誤引起的衝突：</span><span class="sxs-lookup"><span data-stu-id="525f2-181">Conflicts due to foreign key constraint failures are not resolved by replication:</span></span>  
  
    -   <span data-ttu-id="525f2-182">如果衝突是非預期的且資料分割正常 (「訂閱者」不更新相同資料列)，則可使用「發行者」和「訂閱者」上的外部索引鍵條件約束。</span><span class="sxs-lookup"><span data-stu-id="525f2-182">If conflicts are not expected and data is well partitioned (Subscribers do not update the same rows), you can use foreign key constraints on the Publisher and Subscribers.</span></span>  
  
    -   <span data-ttu-id="525f2-183">如果預期會發生衝突：在使用「訂閱者成功」衝突解決時，不應使用發行者或訂閱者端的外部索引鍵條件約束；在使用「發行者成功」衝突解決時，不應使用訂閱者端的外部索引鍵條件約束。</span><span class="sxs-lookup"><span data-stu-id="525f2-183">If conflicts are expected: you should not use foreign key constraints at the Publisher or Subscriber if you use "Subscriber wins" conflict resolution; you should not use foreign key constraints at the Subscriber if you use "Publisher wins" conflict resolution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="525f2-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="525f2-184">See Also</span></span>  
 <span data-ttu-id="525f2-185">[Peer-to-Peer Transactional Replication](peer-to-peer-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="525f2-185">[Peer-to-Peer Transactional Replication](peer-to-peer-transactional-replication.md) </span></span>  
 <span data-ttu-id="525f2-186">[異動複寫](transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="525f2-186">[Transactional Replication](transactional-replication.md) </span></span>  
 <span data-ttu-id="525f2-187">[發行資料和資料庫物件](../publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="525f2-187">[Publish Data and Database Objects](../publish/publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="525f2-188">訂閱發行集</span><span class="sxs-lookup"><span data-stu-id="525f2-188">Subscribe to Publications</span></span>](../subscribe-to-publications.md)  
  
  
