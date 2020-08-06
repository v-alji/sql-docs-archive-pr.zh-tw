---
title: 刪除提取訂閱 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- removing subscriptions
- deleting subscriptions
- pull subscriptions [SQL Server replication], deleting
- subscriptions [SQL Server replication], pull
ms.assetid: 997c0b8e-d8d9-4eed-85b1-6baa1f8594ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f869e26075bb837b2110e9db3ac5ac7220659525
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585880"
---
# <a name="delete-a-pull-subscription"></a><span data-ttu-id="d904d-102">刪除提取訂閱</span><span class="sxs-lookup"><span data-stu-id="d904d-102">Delete a Pull Subscription</span></span>
  <span data-ttu-id="d904d-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 Replication Management Objects (RMO) 來刪除 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="d904d-103">This topic describes how to delete a pull subscription in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="d904d-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="d904d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d904d-105">**若要刪除提取訂閱，請使用：**</span><span class="sxs-lookup"><span data-stu-id="d904d-105">**To delete a pull subscription, using:**</span></span>  
  
     [<span data-ttu-id="d904d-106">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d904d-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d904d-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d904d-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="d904d-108">Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="d904d-108">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d904d-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d904d-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="d904d-110">在發行者端 (從 **的** [本機發行集] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]資料夾) 或訂閱者端 (從 **[本機訂閱]** 資料夾) 刪除提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="d904d-110">Delete a pull subscription at the Publisher (from the **Local Publications** folder in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) or the Subscriber (from the **Local Subscriptions** folder).</span></span> <span data-ttu-id="d904d-111">刪除訂閱並無法從訂閱中移除物件或資料，這些必須手動移除。</span><span class="sxs-lookup"><span data-stu-id="d904d-111">Deleting a subscription does not remove objects or data from the subscription; they must be removed manually.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-at-the-publisher"></a><span data-ttu-id="d904d-112">若要在發行者端刪除提取訂閱</span><span class="sxs-lookup"><span data-stu-id="d904d-112">To delete a pull subscription at the Publisher</span></span>  
  
1.  <span data-ttu-id="d904d-113">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的發行者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="d904d-113">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="d904d-114">展開 **[複寫]** 資料夾，然後展開 **[本機發行集]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d904d-114">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="d904d-115">展開與您要刪除的訂閱相關聯的發行集。</span><span class="sxs-lookup"><span data-stu-id="d904d-115">Expand the publication associated with the subscription you want to delete.</span></span>  
  
4.  <span data-ttu-id="d904d-116">以滑鼠右鍵按一下訂閱，然後按一下 **[刪除]** 。</span><span class="sxs-lookup"><span data-stu-id="d904d-116">Right-click the subscription, and then click **Delete**.</span></span>  
  
5.  <span data-ttu-id="d904d-117">在確認對話方塊中，選取是否要連接訂閱者以刪除訂閱資訊。</span><span class="sxs-lookup"><span data-stu-id="d904d-117">In the confirmation dialog box, select whether to connect to the Subscriber to delete subscription information.</span></span> <span data-ttu-id="d904d-118">如果清除 **[連接到訂閱者]** 核取方塊，則應在稍後連接到「訂閱者」以刪除資訊。</span><span class="sxs-lookup"><span data-stu-id="d904d-118">If you clear the **Connect to Subscriber** check box, you should connect to the Subscriber later to delete the information.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-at-the-subscriber"></a><span data-ttu-id="d904d-119">若要在訂閱者端刪除提取訂閱</span><span class="sxs-lookup"><span data-stu-id="d904d-119">To delete a pull subscription at the Subscriber</span></span>  
  
1.  <span data-ttu-id="d904d-120">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的訂閱者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="d904d-120">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="d904d-121">展開 **[複寫]** 資料夾，然後展開 **[本機訂閱]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d904d-121">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="d904d-122">以滑鼠右鍵按一下您要刪除的訂閱，然後按一下 **[刪除]** 。</span><span class="sxs-lookup"><span data-stu-id="d904d-122">Right-click the subscription you want to delete, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="d904d-123">在確認對話方塊中，選取是否要連接發行者以刪除訂閱資訊。</span><span class="sxs-lookup"><span data-stu-id="d904d-123">In the confirmation dialog box, select whether to connect to the Publisher to delete subscription information.</span></span> <span data-ttu-id="d904d-124">若您清除 **[連接到發行者]** 核取方塊，應於稍後連接到發行者以便刪除資訊。</span><span class="sxs-lookup"><span data-stu-id="d904d-124">If you clear the **Connect to Publisher** check box, you should connect to the Publisher later to delete the information.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d904d-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d904d-125">Using Transact-SQL</span></span>  
 <span data-ttu-id="d904d-126">您可以使用複寫預存程序來以程式設計的方式刪除提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="d904d-126">Pull subscriptions can be deleted programmatically using replication stored procedures.</span></span> <span data-ttu-id="d904d-127">使用哪些預存程序要依訂閱所屬的發行集類型而定。</span><span class="sxs-lookup"><span data-stu-id="d904d-127">The stored procedures used will depend on the type of publication to which the subscription belongs.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="d904d-128">刪除快照式或交易式發行集的提取訂閱</span><span class="sxs-lookup"><span data-stu-id="d904d-128">To delete a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="d904d-129">在訂閱資料庫的訂閱者端，執行 [sp_droppullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d904d-129">At the Subscriber on the subscription database, execute [sp_droppullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql).</span></span> <span data-ttu-id="d904d-130">指定 **@publication** 、 **@publisher** 和 **@publisher_db** 。</span><span class="sxs-lookup"><span data-stu-id="d904d-130">Specify **@publication**, **@publisher**, and **@publisher_db**.</span></span>  
  
2.  <span data-ttu-id="d904d-131">在發行集資料庫的發行者端，執行 [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d904d-131">At the Publisher on the publication database, execute [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql).</span></span> <span data-ttu-id="d904d-132">指定 **@publication** 和 **@subscriber** 。</span><span class="sxs-lookup"><span data-stu-id="d904d-132">Specify **@publication** and **@subscriber**.</span></span> <span data-ttu-id="d904d-133">為 **@article** 指定 **@article**。</span><span class="sxs-lookup"><span data-stu-id="d904d-133">Specify a value of **all** for **@article**.</span></span> <span data-ttu-id="d904d-134">(選擇性) 如果無法存取散發者，請為 **@ignore_distributor** 指定 **@ignore_distributor** 的值來刪除此訂閱，而不需要移除散發者端上的相關物件。</span><span class="sxs-lookup"><span data-stu-id="d904d-134">(Optional) If the Distributor cannot be accessed, specify a value of **1** for **@ignore_distributor** to delete the subscription without removing related objects at the Distributor.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="d904d-135">刪除合併式發行集的提取訂閱</span><span class="sxs-lookup"><span data-stu-id="d904d-135">To delete a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="d904d-136">在訂閱資料庫的訂閱者端，執行 [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d904d-136">At the Subscriber on the subscription database, execute [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql).</span></span> <span data-ttu-id="d904d-137">指定 **@publication** 、 **@publisher** 和 **@publisher_db** 。</span><span class="sxs-lookup"><span data-stu-id="d904d-137">Specify **@publication**, **@publisher**, and **@publisher_db**.</span></span>  
  
2.  <span data-ttu-id="d904d-138">在發行集資料庫的發行者端，執行 [sp_dropmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d904d-138">At the Publisher on the publication database, execute [sp_dropmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql).</span></span> <span data-ttu-id="d904d-139">指定 **@publication** 、 **@subscriber** 和 **@subscriber_db** 。</span><span class="sxs-lookup"><span data-stu-id="d904d-139">Specify **@publication**, **@subscriber**, and **@subscriber_db**.</span></span> <span data-ttu-id="d904d-140">為 **@subscription_type** 指定為 **@subscription_type**＞。</span><span class="sxs-lookup"><span data-stu-id="d904d-140">Specify a value of **pull** for **@subscription_type**.</span></span> <span data-ttu-id="d904d-141">(選擇性) 如果無法存取散發者，請為 **@ignore_distributor** 指定 **@ignore_distributor** 的值來刪除此訂閱，而不需要移除散發者端上的相關物件。</span><span class="sxs-lookup"><span data-stu-id="d904d-141">(Optional) If the Distributor cannot be accessed, specify a value of **1** for **@ignore_distributor** to delete the subscription without removing related objects at the Distributor.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="d904d-142">範例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d904d-142">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="d904d-143">下列範例會刪除交易式發行集的提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="d904d-143">The following example deletes a pull subscription to a transactional publication.</span></span> <span data-ttu-id="d904d-144">第一批次是在「訂閱者」上執行，而第二批次是在「發行者」上執行。</span><span class="sxs-lookup"><span data-stu-id="d904d-144">The first batch is executed at the Subscriber and the second is executed at the Publisher.</span></span>  
  
 [!code-sql[HowTo#sp_droptranpullsubscription](../../snippets/tsql/SQL15/replication/howto/tsql/droptranpullsub.sql#sp_droptranpullsubscription)]  
  
 [!code-sql[HowTo#sp_droptransubscription](../../snippets/tsql/SQL15/replication/howto/tsql/droptranpullsub.sql#sp_droptransubscription)]  
  
 <span data-ttu-id="d904d-145">下列範例會刪除合併式發行集的提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="d904d-145">The following example deletes a pull subscription to a merge publication.</span></span> <span data-ttu-id="d904d-146">第一批次是在「訂閱者」上執行，而第二批次是在「發行者」上執行。</span><span class="sxs-lookup"><span data-stu-id="d904d-146">The first batch is executed at the Subscriber and the second is executed at the Publisher.</span></span>  
  
 [!code-sql[HowTo#sp_dropmergepullsubscription](../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepullsub.sql#sp_dropmergepullsubscription)]  
  
 [!code-sql[HowTo#sp_dropmergesubscription](../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepullsub.sql#sp_dropmergesubscription)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="d904d-147">使用 Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="d904d-147">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="d904d-148">您可以使用 Replication Management Objects (RMO) 以程式設計的方式刪除提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="d904d-148">You can delete pull subscriptions programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="d904d-149">用於刪除提取訂閱的 RMO 類別依該提取訂閱所屬的發行集類型而定。</span><span class="sxs-lookup"><span data-stu-id="d904d-149">The RMO classes that you use to delete a pull subscription depend on the type of publication to which the pull subscription is subscribed.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="d904d-150">刪除快照式或交易式發行集的提取訂閱</span><span class="sxs-lookup"><span data-stu-id="d904d-150">To delete a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="d904d-151">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與訂閱者和發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="d904d-151">Create connections to both the Subscriber and Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Class.</span></span>  
  
2.  <span data-ttu-id="d904d-152">建立 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> 類別的執行個體，並設定 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>和 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="d904d-152">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> class, and set the <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> properties.</span></span> <span data-ttu-id="d904d-153">使用步驟 1 中的訂閱者連接，以設定 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="d904d-153">Use the Subscriber connection from step 1 to set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
3.  <span data-ttu-id="d904d-154">檢查 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 屬性，確認該訂閱存在。</span><span class="sxs-lookup"><span data-stu-id="d904d-154">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the subscription exists.</span></span> <span data-ttu-id="d904d-155">如果這個屬性的值為 `false`，則表示步驟 2 中的訂閱屬性定義錯誤或是此訂閱不存在。</span><span class="sxs-lookup"><span data-stu-id="d904d-155">If the value of this property is `false`, either the subscription properties in step 2 were defined incorrectly or the subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="d904d-156">呼叫 <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d904d-156">Call the <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> method.</span></span>  
  
5.  <span data-ttu-id="d904d-157">使用步驟 1 中的發行者連接建立 <xref:Microsoft.SqlServer.Replication.TransPublication> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d904d-157">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPublication> class by using the Publisher connection from step 1.</span></span> <span data-ttu-id="d904d-158">指定 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 和 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>。</span><span class="sxs-lookup"><span data-stu-id="d904d-158">Specify <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> and <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
6.  <span data-ttu-id="d904d-159">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d904d-159">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="d904d-160">如果此方法傳回 `false`，則表示步驟 5 中指定的屬性不正確，或伺服器上沒有該發行集存在。</span><span class="sxs-lookup"><span data-stu-id="d904d-160">If this method returns `false`, either the properties specified in step 5 are incorrect or the publication does not exist on the server.</span></span>  
  
7.  <span data-ttu-id="d904d-161">呼叫 <xref:Microsoft.SqlServer.Replication.TransPublication.RemovePullSubscription%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d904d-161">Call the <xref:Microsoft.SqlServer.Replication.TransPublication.RemovePullSubscription%2A> method.</span></span> <span data-ttu-id="d904d-162">為 *subscriber* 和 *subscriberDB* 參數指定訂閱者和訂閱資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="d904d-162">Specify the name of the Subscriber and the subscription database for the *subscriber* and *subscriberDB* parameters.</span></span>  
  
#### <a name="to-delete-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="d904d-163">刪除合併式發行集的提取訂閱</span><span class="sxs-lookup"><span data-stu-id="d904d-163">To delete a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="d904d-164">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與訂閱者和發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="d904d-164">Create connections to both the Subscriber and Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> Class.</span></span>  
  
2.  <span data-ttu-id="d904d-165">建立 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> 類別的執行個體，並設定 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>和 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="d904d-165">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> class, and set the <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> properties.</span></span> <span data-ttu-id="d904d-166">使用步驟 1 中的連接，以設定 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="d904d-166">Use the connection from step 1 to set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
3.  <span data-ttu-id="d904d-167">檢查 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 屬性，確認該訂閱存在。</span><span class="sxs-lookup"><span data-stu-id="d904d-167">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the subscription exists.</span></span> <span data-ttu-id="d904d-168">如果這個屬性的值為 `false`，則表示步驟 2 中的訂閱屬性定義錯誤或是此訂閱不存在。</span><span class="sxs-lookup"><span data-stu-id="d904d-168">If the value of this property is `false`, either the subscription properties in step 2 were defined incorrectly or the subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="d904d-169">呼叫 <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d904d-169">Call the <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> method.</span></span>  
  
5.  <span data-ttu-id="d904d-170">使用步驟 1 中的發行者連接建立 <xref:Microsoft.SqlServer.Replication.MergePublication> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d904d-170">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class by using the Publisher connection from step 1.</span></span> <span data-ttu-id="d904d-171">指定 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>、 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 和 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>。</span><span class="sxs-lookup"><span data-stu-id="d904d-171">Specify <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> and <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
6.  <span data-ttu-id="d904d-172">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d904d-172">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="d904d-173">如果此方法傳回 `false`，則表示步驟 5 中指定的屬性不正確，或伺服器上沒有該發行集存在。</span><span class="sxs-lookup"><span data-stu-id="d904d-173">If this method returns `false`, either the properties specified in step 5 are incorrect or the publication does not exist on the server.</span></span>  
  
7.  <span data-ttu-id="d904d-174">呼叫 <xref:Microsoft.SqlServer.Replication.MergePublication.RemovePullSubscription%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d904d-174">Call the <xref:Microsoft.SqlServer.Replication.MergePublication.RemovePullSubscription%2A> method.</span></span> <span data-ttu-id="d904d-175">為 *subscriber* 和 *subscriberDB* 參數指定訂閱者和訂閱資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="d904d-175">Specify the name of the Subscriber and the subscription database for the *subscriber* and *subscriberDB* parameters.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="d904d-176">範例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="d904d-176">Examples (RMO)</span></span>  
 <span data-ttu-id="d904d-177">此範例會刪除交易式發行集的提取訂閱，並在發行者上移除訂閱註冊。</span><span class="sxs-lookup"><span data-stu-id="d904d-177">This example deletes a pull subscription to a transactional publication and removes the subscription registration at the Publisher.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_droptranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_droptranpullsub)]  
  
 <span data-ttu-id="d904d-178">此範例會刪除合併式發行集的提取訂閱，並在發行者上移除訂閱註冊。</span><span class="sxs-lookup"><span data-stu-id="d904d-178">This example deletes a pull subscription to a merge publication and removes the subscription registration at the Publisher.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropMergePullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropmergepullsub)]  
  
## <a name="see-also"></a><span data-ttu-id="d904d-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d904d-179">See Also</span></span>  
 <span data-ttu-id="d904d-180">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="d904d-180">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 [<span data-ttu-id="d904d-181">複寫安全性最佳作法</span><span class="sxs-lookup"><span data-stu-id="d904d-181">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
