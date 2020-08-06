---
title: 檢視及修改發送訂閱屬性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing replication properties
- push subscriptions [SQL Server replication], properties
- subscriptions [SQL Server replication], push
- push subscriptions [SQL Server replication], modifying
- modifying replication properties, push subscriptions
- modifying subscriptions, SQL Server Management Studio
ms.assetid: 801d2995-7aa5-4626-906e-c8190758ec71
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c1506d4f83fcfb94d62efd01c4d6447048fecfd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706361"
---
# <a name="view-and-modify-push-subscription-properties"></a><span data-ttu-id="826a2-102">檢視及修改發送訂閱屬性</span><span class="sxs-lookup"><span data-stu-id="826a2-102">View and Modify Push Subscription Properties</span></span>
  <span data-ttu-id="826a2-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 Replication Management Objects (RMO)，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中檢視及修改發送訂閱屬性。</span><span class="sxs-lookup"><span data-stu-id="826a2-103">This topic describes how to view and modify push subscription properties in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="826a2-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="826a2-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="826a2-105">**若要檢視及修改發送訂閱屬性，請使用：**</span><span class="sxs-lookup"><span data-stu-id="826a2-105">**To view and modify push subscription properties, using:**</span></span>  
  
     [<span data-ttu-id="826a2-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="826a2-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="826a2-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="826a2-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="826a2-108">Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="826a2-108">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="826a2-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="826a2-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="826a2-110">從「發行者」在以下項目中檢視並修改發送訂閱屬性：</span><span class="sxs-lookup"><span data-stu-id="826a2-110">View and modify push subscription properties from the Publisher in:</span></span>  
  
-   <span data-ttu-id="826a2-111">[訂閱屬性 - \<Publisher>: \<PublicationDatabase>] 對話方塊，該對話方塊會在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中提供。</span><span class="sxs-lookup"><span data-stu-id="826a2-111">The **Subscription Properties - \<Publisher>: \<PublicationDatabase>** dialog box, which is available from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="826a2-112">**[所有訂閱]** 索引標籤，在「複寫監視器」中可用。</span><span class="sxs-lookup"><span data-stu-id="826a2-112">The **All Subscriptions** tab, which is available in Replication Monitor.</span></span> <span data-ttu-id="826a2-113">如需啟動複寫監視器的詳細資訊，請參閱[啟動複寫監視器](monitor/start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="826a2-113">For information about starting Replication Monitor, see [Start the Replication Monitor](monitor/start-the-replication-monitor.md).</span></span>  
  
#### <a name="to-view-and-modify-push-subscription-properties-in-management-studio"></a><span data-ttu-id="826a2-114">若要在 Management Studio 中檢視並修改發送訂閱屬性</span><span class="sxs-lookup"><span data-stu-id="826a2-114">To view and modify push subscription properties in Management Studio</span></span>  
  
1.  <span data-ttu-id="826a2-115">連接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的發行者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="826a2-115">Connect to the Publisher in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="826a2-116">展開 **[複寫]** 資料夾，然後展開 **[本機發行集]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="826a2-116">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="826a2-117">展開適當的發行集，以滑鼠右鍵按一下訂閱，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="826a2-117">Expand the appropriate publication, right-click a subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="826a2-118">必要時修改任何屬性，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="826a2-118">Modify any properties if necessary, and then click **OK**.</span></span>  
  
#### <a name="to-view-and-modify-push-subscription-properties-in-replication-monitor"></a><span data-ttu-id="826a2-119">若要在複寫監視器中檢視和修改發送訂閱屬性</span><span class="sxs-lookup"><span data-stu-id="826a2-119">To view and modify push subscription properties in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="826a2-120">在複寫監視器的左窗格中展開發行者群組，展開發行者，然後按一下發行集。</span><span class="sxs-lookup"><span data-stu-id="826a2-120">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="826a2-121">按一下 **[所有訂閱]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="826a2-121">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="826a2-122">以滑鼠右鍵按一下訂閱，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="826a2-122">Right-click a subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="826a2-123">必要時修改任何屬性，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="826a2-123">Modify any properties if necessary, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="826a2-124">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="826a2-124">Using Transact-SQL</span></span>  
 <span data-ttu-id="826a2-125">您可以使用複寫預存程序來以程式設計的方式修改發送訂閱及存取其屬性。</span><span class="sxs-lookup"><span data-stu-id="826a2-125">Push subscriptions can be modified and their properties accessed programmatically using replication stored procedures.</span></span> <span data-ttu-id="826a2-126">使用哪些預存程序要依訂閱所屬的發行集類型而定。</span><span class="sxs-lookup"><span data-stu-id="826a2-126">The stored procedures used depend on the type of publication to which the subscription belongs.</span></span>  
  
#### <a name="to-view-the-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="826a2-127">檢視快照式或交易式發行集之發送訂閱的屬性</span><span class="sxs-lookup"><span data-stu-id="826a2-127">To view the properties of a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="826a2-128">在發行集資料庫的發行者上，執行 [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="826a2-128">At the Publisher on the publication database, execute [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).</span></span> <span data-ttu-id="826a2-129">**@publication**針對，指定、 **@subscriber** 和的值**all** **@article** 。</span><span class="sxs-lookup"><span data-stu-id="826a2-129">Specify **@publication**, **@subscriber**, and a value of **all** for **@article**.</span></span>  
  
2.  <span data-ttu-id="826a2-130">在發行集資料庫的發行者上，執行 [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)，並指定 **@subscriber**存取。</span><span class="sxs-lookup"><span data-stu-id="826a2-130">At the Publisher on the publication database, execute [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql), specifying **@subscriber**.</span></span>  
  
#### <a name="to-change-the-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="826a2-131">變更快照式或交易式發行集之發送訂閱的屬性</span><span class="sxs-lookup"><span data-stu-id="826a2-131">To change the properties of a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="826a2-132">在發行集資料庫的發行者上，執行 [sp_changesubscriber](/sql/relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql)，並指定 **@subscriber** 及針對所變更的訂閱者屬性指定任何參數。</span><span class="sxs-lookup"><span data-stu-id="826a2-132">At the Publisher on the publication database, execute [sp_changesubscriber](/sql/relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql), specifying **@subscriber** and any parameters for the Subscriber properties being changed.</span></span>  
  
2.  <span data-ttu-id="826a2-133">在發行集資料庫的發行者上，執行 [sp_changesubscription](/sql/relational-databases/system-stored-procedures/sp-changesubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="826a2-133">At the Publisher on the publication database, execute [sp_changesubscription](/sql/relational-databases/system-stored-procedures/sp-changesubscription-transact-sql).</span></span> <span data-ttu-id="826a2-134">**@publication**將、 **@subscriber** 、、的值指定 **@destination_db** 為**all** **@article** 、將變更為的訂閱屬性， **@property** 以及將新的值指定為 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="826a2-134">Specify **@publication**, **@subscriber**, **@destination_db**, a value of **all** for **@article**, the subscription property being changed as **@property**, and the new value as **@value**.</span></span> <span data-ttu-id="826a2-135">這樣會變更發送訂閱的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="826a2-135">This changes security settings for the push subscription.</span></span>  
  
3.  <span data-ttu-id="826a2-136">(選擇性) 若要變更訂閱的 Data Transformation Services (DTS) 封裝屬性，請在訂閱資料庫的訂閱者上，執行 [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="826a2-136">(Optional) To change the Data Transformation Services (DTS) package properties of a subscription, execute [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql) at the Subscriber on the subscription database.</span></span> <span data-ttu-id="826a2-137">針對 **@jobid** 和下列 DTS 封裝屬性，指定散發代理程式作業的識別碼：</span><span class="sxs-lookup"><span data-stu-id="826a2-137">Specify the ID of the Distribution Agent job for **@jobid** and the following DTS package properties:</span></span>  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     <span data-ttu-id="826a2-138">這樣會變更訂閱的 DTS 封裝屬性。</span><span class="sxs-lookup"><span data-stu-id="826a2-138">This changes the DTS package properties of a subscription.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="826a2-139">可以執行 [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)來取得作業識別碼。</span><span class="sxs-lookup"><span data-stu-id="826a2-139">The job ID can be obtained by executing [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).</span></span>  
  
#### <a name="to-view-the-properties-of-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="826a2-140">檢視合併式發行集之發送訂閱的屬性</span><span class="sxs-lookup"><span data-stu-id="826a2-140">To view the properties of a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="826a2-141">在發行集資料庫的發行者上，執行 [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="826a2-141">At the Publisher on the publication database, execute [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql).</span></span> <span data-ttu-id="826a2-142">指定 **@publication** 和 **@subscriber** 。</span><span class="sxs-lookup"><span data-stu-id="826a2-142">Specify **@publication** and **@subscriber**.</span></span>  
  
2.  <span data-ttu-id="826a2-143">在發行者上，執行[sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)，並指定 **@subscriber** 。</span><span class="sxs-lookup"><span data-stu-id="826a2-143">At the Publisher, execute [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql), specifying **@subscriber**.</span></span>  
  
#### <a name="to-change-the-properties-of-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="826a2-144">變更合併式發行集之發送訂閱的屬性</span><span class="sxs-lookup"><span data-stu-id="826a2-144">To change the properties of a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="826a2-145">在發行集資料庫的發行者上，執行 [sp_changemergesubscription](/sql/relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="826a2-145">At the Publisher on the publication database, execute [sp_changemergesubscription](/sql/relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql).</span></span> <span data-ttu-id="826a2-146">指定 **@publication** 、 **@subscriber** 、 **@subscriber_db** 、將變更為的訂閱屬性 **@property** ，並將新的值指定為 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="826a2-146">Specify **@publication**, **@subscriber**, **@subscriber_db**, the subscription property being changed as **@property**, and the new value as **@value**.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="826a2-147">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="826a2-147">Example (Transact-SQL)</span></span>  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="826a2-148">使用 Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="826a2-148">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="826a2-149">用於檢視或修改發送訂閱屬性的 RMO 類別，將取決於該發送訂閱所訂閱的發行集類型而定。</span><span class="sxs-lookup"><span data-stu-id="826a2-149">The RMO classes you use to view or modify push subscription properties depend on the type of publication to which the push subscription is subscribed.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="826a2-150">檢視或修改快照式或交易式發行集之發送訂閱的屬性</span><span class="sxs-lookup"><span data-stu-id="826a2-150">To view or modify properties of a push subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="826a2-151">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="826a2-151">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="826a2-152">建立 <xref:Microsoft.SqlServer.Replication.TransSubscription> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="826a2-152">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransSubscription> class.</span></span>  
  
3.  <span data-ttu-id="826a2-153">設定 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>和 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="826a2-153">Set the <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, and <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="826a2-154">針對 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 屬性設定步驟 1 中的 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 。</span><span class="sxs-lookup"><span data-stu-id="826a2-154">Set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property setting.</span></span>  
  
5.  <span data-ttu-id="826a2-155">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="826a2-155">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="826a2-156">如果此方法傳回 `false`，則表示步驟 3 中的訂閱屬性定義不正確，或者此訂閱不存在。</span><span class="sxs-lookup"><span data-stu-id="826a2-156">If this method returns `false`, either the subscription properties in step 3 were defined incorrectly or the subscription does not exist.</span></span>  
  
6.  <span data-ttu-id="826a2-157">(選擇性) 若要變更屬性，請針對其中一個可設定的 <xref:Microsoft.SqlServer.Replication.TransSubscription> 屬性設定新的值，然後呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="826a2-157">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.TransSubscription> properties that can be set, and then call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="826a2-158">(選擇性) 若要檢視新的設定，請呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> 方法，重新載入訂閱的屬性。</span><span class="sxs-lookup"><span data-stu-id="826a2-158">(Optional) To view the new settings, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> method to reload the properties for the subscription.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="826a2-159">檢視或修改合併式發行集之發送訂閱的屬性</span><span class="sxs-lookup"><span data-stu-id="826a2-159">To view or modify properties of a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="826a2-160">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與「訂閱者」的連接。</span><span class="sxs-lookup"><span data-stu-id="826a2-160">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="826a2-161">建立 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="826a2-161">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> class.</span></span>  
  
3.  <span data-ttu-id="826a2-162">設定 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>和 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="826a2-162">Set the <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, and <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="826a2-163">針對 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 屬性設定步驟 1 中的 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 。</span><span class="sxs-lookup"><span data-stu-id="826a2-163">Set the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property setting.</span></span>  
  
5.  <span data-ttu-id="826a2-164">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="826a2-164">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="826a2-165">如果此方法傳回 `false`，則表示步驟 3 中的訂閱屬性定義不正確，或者此訂閱不存在。</span><span class="sxs-lookup"><span data-stu-id="826a2-165">If this method returns `false`, either the subscription properties in step 3 were defined incorrectly or the subscription does not exist.</span></span>  
  
6.  <span data-ttu-id="826a2-166">(選擇性) 若要變更屬性，請針對其中一個可設定的 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 屬性設定新的值，然後呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="826a2-166">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> properties that can be set, and then call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="826a2-167">(選擇性) 若要檢視新的設定，請呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> 方法，重新載入訂閱的屬性。</span><span class="sxs-lookup"><span data-stu-id="826a2-167">(Optional) To view the new settings, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> method to reload the properties for the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="826a2-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="826a2-168">See Also</span></span>  
 <span data-ttu-id="826a2-169">[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="826a2-169">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="826a2-170">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="826a2-170">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="826a2-171">訂閱發行集</span><span class="sxs-lookup"><span data-stu-id="826a2-171">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
