---
title: 刪除發送訂閱 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- removing subscriptions
- push subscriptions [SQL Server replication], deleting
- deleting subscriptions
- subscriptions [SQL Server replication], push
ms.assetid: 3c4847e2-aed9-4488-b45d-8164422bdb10
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 912958e00d117f51c5dc95c0dc1247d278acb0ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585876"
---
# <a name="delete-a-push-subscription"></a><span data-ttu-id="15609-102">刪除發送訂閱</span><span class="sxs-lookup"><span data-stu-id="15609-102">Delete a Push Subscription</span></span>
  <span data-ttu-id="15609-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 Replication Management Objects (RMO) 來刪除 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="15609-103">This topic describes how to delete a push subscription in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="15609-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="15609-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="15609-105">**若要刪除發送訂閱，請使用：**</span><span class="sxs-lookup"><span data-stu-id="15609-105">**To delete a push subscription, using:**</span></span>  
  
     [<span data-ttu-id="15609-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="15609-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="15609-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="15609-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="15609-108">Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="15609-108">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="15609-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="15609-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="15609-110">在發行者端 (從 **中的** [本機發行集] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]資料夾) 或訂閱者端 (從 **[本機訂閱]** 資料夾) 刪除發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="15609-110">Delete a push subscription at the Publisher (from the **Local Publications** folder in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) or the Subscriber (from the **Local Subscriptions** folder).</span></span> <span data-ttu-id="15609-111">刪除訂閱並無法從訂閱中移除物件或資料，這些必須手動移除。</span><span class="sxs-lookup"><span data-stu-id="15609-111">Deleting a subscription does not remove objects or data from the subscription; they must be removed manually.</span></span>  
  
#### <a name="to-delete-a-push-subscription-at-the-publisher"></a><span data-ttu-id="15609-112">若要在發行者端刪除發送訂閱</span><span class="sxs-lookup"><span data-stu-id="15609-112">To delete a push subscription at the Publisher</span></span>  
  
1.  <span data-ttu-id="15609-113">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的發行者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="15609-113">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="15609-114">展開 **[複寫]** 資料夾，然後展開 **[本機發行集]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="15609-114">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="15609-115">展開與您要刪除的訂閱相關聯的發行集。</span><span class="sxs-lookup"><span data-stu-id="15609-115">Expand the publication associated with the subscription you want to delete.</span></span>  
  
4.  <span data-ttu-id="15609-116">以滑鼠右鍵按一下訂閱，然後按一下 **[刪除]** 。</span><span class="sxs-lookup"><span data-stu-id="15609-116">Right-click the subscription, and then click **Delete**.</span></span>  
  
5.  <span data-ttu-id="15609-117">在確認對話方塊中，選取是否要連接訂閱者以刪除訂閱資訊。</span><span class="sxs-lookup"><span data-stu-id="15609-117">In the confirmation dialog box, select whether to connect to the Subscriber to delete subscription information.</span></span> <span data-ttu-id="15609-118">如果您清除 **[連接到訂閱者]** 核取方塊，則稍後應連接到「訂閱者」以刪除資訊。</span><span class="sxs-lookup"><span data-stu-id="15609-118">If you clear the **Connect to Subscriber** checkbox, you should connect to the Subscriber later to delete the information.</span></span>  
  
#### <a name="to-delete-a-push-subscription-at-the-subscriber"></a><span data-ttu-id="15609-119">若要在訂閱者端刪除發送訂閱</span><span class="sxs-lookup"><span data-stu-id="15609-119">To delete a push subscription at the Subscriber</span></span>  
  
1.  <span data-ttu-id="15609-120">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的訂閱者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="15609-120">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="15609-121">展開 **[複寫]** 資料夾，然後展開 **[本機訂閱]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="15609-121">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="15609-122">以滑鼠右鍵按一下您要刪除的訂閱，然後按一下 **[刪除]** 。</span><span class="sxs-lookup"><span data-stu-id="15609-122">Right-click the subscription you want to delete, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="15609-123">在確認對話方塊中，選取是否要連接發行者以刪除訂閱資訊。</span><span class="sxs-lookup"><span data-stu-id="15609-123">In the confirmation dialog box, select whether to connect to the Publisher to delete subscription information.</span></span> <span data-ttu-id="15609-124">若您清除 **[連接到發行者]** 核取方塊，應於稍後連接到發行者以便刪除資訊。</span><span class="sxs-lookup"><span data-stu-id="15609-124">If you clear the **Connect to Publisher** check box, you should connect to the Publisher later to delete the information.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="15609-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="15609-125">Using Transact-SQL</span></span>  
 <span data-ttu-id="15609-126">您可以使用複寫預存程序來以程式設計的方式刪除發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="15609-126">Push subscriptions can be deleted programmatically using replication stored procedures.</span></span> <span data-ttu-id="15609-127">使用哪些預存程序要依訂閱所屬的發行集類型而定。</span><span class="sxs-lookup"><span data-stu-id="15609-127">The stored procedures used depend on the type of publication to which the subscription belongs.</span></span>  
  
#### <a name="to-delete-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="15609-128">刪除快照式或交易式發行集的發送訂閱</span><span class="sxs-lookup"><span data-stu-id="15609-128">To delete a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="15609-129">在發行集資料庫的發行者端，執行 [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="15609-129">At the Publisher on the publication database, execute [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql).</span></span> <span data-ttu-id="15609-130">指定 **@publication** 和 **@subscriber** 。</span><span class="sxs-lookup"><span data-stu-id="15609-130">Specify **@publication** and **@subscriber**.</span></span> <span data-ttu-id="15609-131">為 **@article** 指定 **@article**。</span><span class="sxs-lookup"><span data-stu-id="15609-131">Specify a value of **all** for **@article**.</span></span> <span data-ttu-id="15609-132">(選擇性) 如果無法存取散發者，請為 **@ignore_distributor** 指定 **@ignore_distributor** 的值來刪除此訂閱，而不需要移除散發者端上的相關物件。</span><span class="sxs-lookup"><span data-stu-id="15609-132">(Optional) If the Distributor cannot be accessed, specify a value of **1** for **@ignore_distributor** to delete the subscription without removing related objects at the Distributor.</span></span>  
  
2.  <span data-ttu-id="15609-133">(選擇性) 在訂閱資料庫的訂閱者端，執行 [sp_subscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql) 來移除訂閱資料庫中的複寫中繼資料。</span><span class="sxs-lookup"><span data-stu-id="15609-133">At the Subscriber on the subscription database, execute [sp_subscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql) to remove replication metadata in the subscription database.</span></span>  
  
#### <a name="to-delete-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="15609-134">刪除合併式發行集的發送訂閱</span><span class="sxs-lookup"><span data-stu-id="15609-134">To delete a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="15609-135">在發行者上，執行[sp_dropmergesubscription &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql)， **@publication** 並指定、 **@subscriber** 和 **@subscriber_db** 。</span><span class="sxs-lookup"><span data-stu-id="15609-135">At the Publisher, execute [sp_dropmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql), specifying **@publication**, **@subscriber** and **@subscriber_db**.</span></span> <span data-ttu-id="15609-136">(選擇性) 如果無法存取散發者，請為 **@ignore_distributor** 指定 **@ignore_distributor** 的值來刪除此訂閱，而不需要移除散發者端上的相關物件。</span><span class="sxs-lookup"><span data-stu-id="15609-136">(Optional) If the Distributor cannot be accessed, specify a value of **1** for **@ignore_distributor** to delete the subscription without removing related objects at the Distributor.</span></span>  
  
2.  <span data-ttu-id="15609-137">在訂閱資料庫的訂閱者端，執行 [sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="15609-137">At the Subscriber on the subscription database, execute [sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql).</span></span> <span data-ttu-id="15609-138">指定 **@publisher** 、 **@publisher_db** 和 **@publication** 。</span><span class="sxs-lookup"><span data-stu-id="15609-138">Specify **@publisher**, **@publisher_db**, and **@publication**.</span></span> <span data-ttu-id="15609-139">這樣會移除訂閱資料庫中的合併中繼資料。</span><span class="sxs-lookup"><span data-stu-id="15609-139">This removes merge metadata from the subscription database.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="15609-140">範例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="15609-140">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="15609-141">此範例會刪除交易式發行集的發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="15609-141">This example deletes a push subscription to a transactional publication.</span></span>  
  
 [!code-sql[HowTo#sp_droptransubscription](../../snippets/tsql/SQL15/replication/howto/tsql/droptranpullsub.sql#sp_droptransubscription)]  
  
 <span data-ttu-id="15609-142">此範例會刪除合併式發行集的發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="15609-142">This example deletes a push subscription to a merge publication.</span></span>  
  
 [!code-sql[HowTo#sp_dropmergesubscription](../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepullsub.sql#sp_dropmergesubscription)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="15609-143">使用 Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="15609-143">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="15609-144">用於刪除發送訂閱的 RMO 類別取決於該發送訂閱所屬的發行集類型而定。</span><span class="sxs-lookup"><span data-stu-id="15609-144">The RMO classes that you use to delete a push subscription depend on the type of publication to which the push subscription is subscribed.</span></span>  
  
#### <a name="to-delete-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="15609-145">刪除快照式或交易式發行集的發送訂閱</span><span class="sxs-lookup"><span data-stu-id="15609-145">To delete a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="15609-146">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與「訂閱者」的連接。</span><span class="sxs-lookup"><span data-stu-id="15609-146">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="15609-147">建立 <xref:Microsoft.SqlServer.Replication.TransSubscription> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="15609-147">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransSubscription> class.</span></span>  
  
3.  <span data-ttu-id="15609-148">設定 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>和 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="15609-148">Set the <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, and <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="15609-149">針對 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 屬性設定步驟 1 中的 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 。</span><span class="sxs-lookup"><span data-stu-id="15609-149">Set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="15609-150">檢查 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 屬性，確認該訂閱存在。</span><span class="sxs-lookup"><span data-stu-id="15609-150">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the subscription exists.</span></span> <span data-ttu-id="15609-151">如果這個屬性的值為 `false`，則表示步驟 2 中的訂閱屬性定義錯誤或是此訂閱不存在。</span><span class="sxs-lookup"><span data-stu-id="15609-151">If the value of this property is `false`, either the subscription properties in step 2 were defined incorrectly or the subscription does not exist.</span></span>  
  
6.  <span data-ttu-id="15609-152">呼叫 <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="15609-152">Call the <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> method.</span></span>  
  
#### <a name="to-delete-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="15609-153">刪除合併式發行集的發送訂閱</span><span class="sxs-lookup"><span data-stu-id="15609-153">To delete a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="15609-154">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與「訂閱者」的連接。</span><span class="sxs-lookup"><span data-stu-id="15609-154">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="15609-155">建立 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="15609-155">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> class.</span></span>  
  
3.  <span data-ttu-id="15609-156">設定 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>和 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="15609-156">Set the <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, and <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="15609-157">針對 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 屬性設定步驟 1 中的 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 。</span><span class="sxs-lookup"><span data-stu-id="15609-157">Set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="15609-158">檢查 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 屬性，確認該訂閱存在。</span><span class="sxs-lookup"><span data-stu-id="15609-158">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the subscription exists.</span></span> <span data-ttu-id="15609-159">如果這個屬性的值為 `false`，則表示步驟 2 中的訂閱屬性定義錯誤或是此訂閱不存在。</span><span class="sxs-lookup"><span data-stu-id="15609-159">If the value of this property is `false`, either the subscription properties in step 2 were defined incorrectly or the subscription does not exist.</span></span>  
  
6.  <span data-ttu-id="15609-160">呼叫 <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="15609-160">Call the <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> method.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="15609-161">範例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="15609-161">Examples (RMO)</span></span>  
 <span data-ttu-id="15609-162">您可以使用 Replication Management Objects (RMO) 以程式設計的方式刪除發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="15609-162">You can delete push subscriptions programmatically by using Replication Management Objects (RMO).</span></span>  
  
 [!code-csharp[HowTo#rmo_DropTranPushSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_droptranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPushSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_droptranpushsub)]  
  
## <a name="see-also"></a><span data-ttu-id="15609-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15609-163">See Also</span></span>  
 <span data-ttu-id="15609-164">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="15609-164">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 [<span data-ttu-id="15609-165">複寫安全性最佳作法</span><span class="sxs-lookup"><span data-stu-id="15609-165">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
