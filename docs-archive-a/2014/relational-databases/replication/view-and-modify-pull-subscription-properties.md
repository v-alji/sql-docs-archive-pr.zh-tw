---
title: 檢視及修改提取訂閱屬性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- modifying subscriptions
- viewing replication properties
- modifying replication properties, pull subscriptions
- pull subscriptions [SQL Server replication], modifying
- subscriptions [SQL Server replication], pull
- pull subscriptions [SQL Server replication], properties
- modifying subscriptions, SQL Server Management Studio
ms.assetid: 1601e54f-86f0-49e8-b023-87a5d1def033
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1b847a22d31bbf3ea7540c55339fe27531134125
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585250"
---
# <a name="view-and-modify-pull-subscription-properties"></a><span data-ttu-id="b2e76-102">檢視及修改提取訂閱屬性</span><span class="sxs-lookup"><span data-stu-id="b2e76-102">View and Modify Pull Subscription Properties</span></span>
  <span data-ttu-id="b2e76-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 Replication Management Objects (RMO)，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中檢視及修改提取訂閱屬性。</span><span class="sxs-lookup"><span data-stu-id="b2e76-103">This topic describes how to view and modify pull subscription properties in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="b2e76-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="b2e76-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b2e76-105">**若要檢視及修改提取訂閱屬性，請使用：**</span><span class="sxs-lookup"><span data-stu-id="b2e76-105">**To view and modify pull subscription properties, using:**</span></span>  
  
     [<span data-ttu-id="b2e76-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b2e76-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b2e76-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b2e76-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="b2e76-108">Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="b2e76-108">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b2e76-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b2e76-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="b2e76-110">在 [訂閱屬性 - \<Publisher>：\<PublicationDatabase>] 對話方塊中檢視發行者或訂閱者的提取訂閱屬性，該對話方塊可從 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 取得。</span><span class="sxs-lookup"><span data-stu-id="b2e76-110">View pull subscription properties from the Publisher or the Subscriber in the **Subscription Properties - \<Publisher>: \<PublicationDatabase>** dialog box, which is available from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="b2e76-111">「訂閱者」可看見更多屬性，而屬性可於「訂閱者」端修改。</span><span class="sxs-lookup"><span data-stu-id="b2e76-111">More properties are visible from the Subscriber, and properties can be modified at the Subscriber.</span></span> <span data-ttu-id="b2e76-112">您也可以從 **[所有訂閱]** 索引標籤上的「發行者」檢視屬性，該索引標籤位於「複寫監視器」中。</span><span class="sxs-lookup"><span data-stu-id="b2e76-112">You can also view properties from the Publisher on the **All Subscriptions** tab, which is available in Replication Monitor.</span></span> <span data-ttu-id="b2e76-113">如需啟動複寫監視器的詳細資訊，請參閱[啟動複寫監視器](monitor/start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="b2e76-113">For information about starting Replication Monitor, see [Start the Replication Monitor](monitor/start-the-replication-monitor.md).</span></span>  
  
#### <a name="to-view-pull-subscription-properties-from-the-publisher-in-management-studio"></a><span data-ttu-id="b2e76-114">從 Management Studio 中的發行者檢視提取訂閱屬性</span><span class="sxs-lookup"><span data-stu-id="b2e76-114">To view pull subscription properties from the Publisher in Management Studio</span></span>  
  
1.  <span data-ttu-id="b2e76-115">連接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的發行者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="b2e76-115">Connect to the Publisher in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="b2e76-116">展開 **[複寫]** 資料夾，然後展開 **[本機發行集]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b2e76-116">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="b2e76-117">展開適當的發行集，以滑鼠右鍵按一下訂閱，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="b2e76-117">Expand the appropriate publication, right-click a subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="b2e76-118">檢視屬性，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="b2e76-118">View properties, and then click **OK**.</span></span>  
  
#### <a name="to-view-and-modify-pull-subscription-properties-from-the-subscriber-in-management-studio"></a><span data-ttu-id="b2e76-119">從 Management Studio 中的訂閱者檢視和修改提取訂閱屬性</span><span class="sxs-lookup"><span data-stu-id="b2e76-119">To view and modify pull subscription properties from the Subscriber in Management Studio</span></span>  
  
1.  <span data-ttu-id="b2e76-120">連接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的訂閱者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="b2e76-120">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="b2e76-121">展開 **[複寫]** 資料夾，然後展開 **[本機訂閱]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b2e76-121">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="b2e76-122">以滑鼠右鍵按一下訂閱，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="b2e76-122">Right-click a subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="b2e76-123">必要時修改任何屬性，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="b2e76-123">Modify any properties if necessary, and then click **OK**.</span></span>  
  
#### <a name="to-view-pull-subscription-properties-from-the-publisher-in-replication-monitor"></a><span data-ttu-id="b2e76-124">從複寫監視器中的發行者檢視提取訂閱屬性</span><span class="sxs-lookup"><span data-stu-id="b2e76-124">To view pull subscription properties from the Publisher in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="b2e76-125">在複寫監視器的左窗格中展開發行者群組，展開發行者，然後按一下發行集。</span><span class="sxs-lookup"><span data-stu-id="b2e76-125">Expand a Publisher group in the left pane of Replication Monitor, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="b2e76-126">按一下 **[所有訂閱]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b2e76-126">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="b2e76-127">以滑鼠右鍵按一下訂閱，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="b2e76-127">Right-click a subscription, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="b2e76-128">檢視屬性，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="b2e76-128">View properties, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b2e76-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b2e76-129">Using Transact-SQL</span></span>  
 <span data-ttu-id="b2e76-130">您可以使用複寫預存程序來以程式設計的方式修改提取訂閱及存取其屬性。</span><span class="sxs-lookup"><span data-stu-id="b2e76-130">Pull subscriptions can be modified and their properties accessed programmatically using replication stored procedures.</span></span> <span data-ttu-id="b2e76-131">使用哪些預存程序要依訂閱所屬的發行集類型而定。</span><span class="sxs-lookup"><span data-stu-id="b2e76-131">The stored procedures used depend on the type of publication to which the subscription belongs.</span></span>  
  
#### <a name="to-view-the-properties-of-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="b2e76-132">檢視快照式或交易式發行集之提取訂閱的屬性</span><span class="sxs-lookup"><span data-stu-id="b2e76-132">To view the properties of a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="b2e76-133">在訂閱者上，執行 [sp_helppullsubscription](/sql/relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b2e76-133">At the Subscriber, execute [sp_helppullsubscription](/sql/relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql).</span></span> <span data-ttu-id="b2e76-134">指定 **@publisher** 、 **@publisher_db** 和 **@publication** 。</span><span class="sxs-lookup"><span data-stu-id="b2e76-134">Specify **@publisher**, **@publisher_db**, and **@publication**.</span></span> <span data-ttu-id="b2e76-135">這樣會傳回儲存於訂閱者上之系統資料表內的訂閱相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b2e76-135">This returns information about the subscription that is stored in system tables at the Subscriber.</span></span>  
  
2.  <span data-ttu-id="b2e76-136">在訂閱者上，執行 [sp_helpsubscription_properties](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b2e76-136">At the Subscriber, execute [sp_helpsubscription_properties](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql).</span></span> <span data-ttu-id="b2e76-137">指定 **@publisher** 、 **@publisher_db** 、 **@publication** 和的下列其中一個值 **@publication_type** ：</span><span class="sxs-lookup"><span data-stu-id="b2e76-137">Specify **@publisher**, **@publisher_db**, **@publication**, and one of the following values for **@publication_type**:</span></span>  
  
    -   <span data-ttu-id="b2e76-138">**0** - 訂閱屬於交易式發行集。</span><span class="sxs-lookup"><span data-stu-id="b2e76-138">**0** - Subscription belongs to a transactional publication.</span></span>  
  
    -   <span data-ttu-id="b2e76-139">**1** - 訂閱屬於快照式發行集。</span><span class="sxs-lookup"><span data-stu-id="b2e76-139">**1** - Subscription belongs to a snapshot publication.</span></span>  
  
3.  <span data-ttu-id="b2e76-140">在發行者上，執行 [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b2e76-140">At the Publisher, execute [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).</span></span> <span data-ttu-id="b2e76-141">指定 **@publication** 和 **@subscriber** 。</span><span class="sxs-lookup"><span data-stu-id="b2e76-141">Specify **@publication** and **@subscriber**.</span></span>  
  
4.  <span data-ttu-id="b2e76-142">在發行者上，執行[sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)，並指定 **@subscriber** 。</span><span class="sxs-lookup"><span data-stu-id="b2e76-142">At the Publisher, execute [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql), specifying **@subscriber**.</span></span> <span data-ttu-id="b2e76-143">這樣會顯示與訂閱者有關的資訊。</span><span class="sxs-lookup"><span data-stu-id="b2e76-143">This displays information about the Subscriber.</span></span>  
  
#### <a name="to-change-the-properties-of-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="b2e76-144">變更快照式或交易式發行集之提取訂閱的屬性</span><span class="sxs-lookup"><span data-stu-id="b2e76-144">To change the properties of a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="b2e76-145">在訂閱者上，執行[sp_change_subscription_properties](/sql/relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql)，並指定 **@publisher** 、 **@publisher_db** 、 **@publication** 、 **0** (交易式) 的值或**1** (的快照集) **@publication_type** 、做為變更的訂閱屬性， **@property** 以及做為的新值 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="b2e76-145">At the Subscriber, execute [sp_change_subscription_properties](/sql/relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql), specifying **@publisher**, **@publisher_db**, **@publication**, a value of either **0** (transactional) or **1** (snapshot) for **@publication_type**, the subscription property being changed as **@property**, and the new value as **@value**.</span></span>  
  
2.  <span data-ttu-id="b2e76-146">(選擇性) 在訂閱資料庫的訂閱者上，執行 [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b2e76-146">(Optional) At the Subscriber on the subscription database, execute [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql).</span></span> <span data-ttu-id="b2e76-147">針對指定散發代理程式作業的識別碼 **@jobid** ，並將下列資料轉換服務 (DTS) 封裝屬性：</span><span class="sxs-lookup"><span data-stu-id="b2e76-147">Specify the ID of the Distribution Agent job for **@jobid**, and the following Data Transformation Services (DTS) package properties:</span></span>  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     <span data-ttu-id="b2e76-148">這樣會變更訂閱的 DTS 封裝屬性。</span><span class="sxs-lookup"><span data-stu-id="b2e76-148">This changes the DTS package properties of a subscription.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b2e76-149">可以執行 [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)來取得作業識別碼。</span><span class="sxs-lookup"><span data-stu-id="b2e76-149">The job ID can be obtained by executing [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).</span></span>  
  
#### <a name="to-view-the-properties-of-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="b2e76-150">檢視合併式發行集之提取訂閱的屬性</span><span class="sxs-lookup"><span data-stu-id="b2e76-150">To view the properties of a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="b2e76-151">在訂閱者上，執行 [sp_helpmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b2e76-151">At the Subscriber, execute [sp_helpmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql).</span></span> <span data-ttu-id="b2e76-152">指定 **@publisher** 、 **@publisher_db** 和 **@publication** 。</span><span class="sxs-lookup"><span data-stu-id="b2e76-152">Specify **@publisher**, **@publisher_db**, and **@publication**.</span></span>  
  
2.  <span data-ttu-id="b2e76-153">在訂閱者上，執行 [sp_helpsubscription_properties](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b2e76-153">At the Subscriber, execute [sp_helpsubscription_properties](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql).</span></span> <span data-ttu-id="b2e76-154">指定 **@publisher** 、 **@publisher_db** 、 **@publication** ，以及2的值 **@publication_type** 。</span><span class="sxs-lookup"><span data-stu-id="b2e76-154">Specify **@publisher**, **@publisher_db**, **@publication**, and a value of 2 for **@publication_type**.</span></span>  
  
3.  <span data-ttu-id="b2e76-155">在發行者上執行 [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql) ，以顯示訂閱資訊。</span><span class="sxs-lookup"><span data-stu-id="b2e76-155">At the Publisher, execute [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql) to display subscription information.</span></span> <span data-ttu-id="b2e76-156">若要傳回特定訂閱的相關資訊，您必須指定 **@publication** 、 **@subscriber** ，以及的**pull**值 **@subscription_type** 。</span><span class="sxs-lookup"><span data-stu-id="b2e76-156">To return information on a specific subscription, you must specify **@publication**, **@subscriber**, and a value of **pull** for **@subscription_type**.</span></span>  
  
4.  <span data-ttu-id="b2e76-157">在發行者上，執行[sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)，並指定 **@subscriber** 。</span><span class="sxs-lookup"><span data-stu-id="b2e76-157">At the Publisher, execute [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql), specifying **@subscriber**.</span></span> <span data-ttu-id="b2e76-158">這樣會顯示與訂閱者有關的資訊。</span><span class="sxs-lookup"><span data-stu-id="b2e76-158">This displays information about the Subscriber.</span></span>  
  
#### <a name="to-change-the-properties-of-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="b2e76-159">變更合併式發行集之提取訂閱的屬性</span><span class="sxs-lookup"><span data-stu-id="b2e76-159">To change the properties of a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="b2e76-160">在訂閱者上，執行 [sp_changemergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b2e76-160">At the Subscriber, execute [sp_changemergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql).</span></span> <span data-ttu-id="b2e76-161">指定 **@publication** 、 **@publisher** 、 **@publisher_db** 、將變更為的訂閱屬性 **@property** ，並將新的值指定為 **@value** 。</span><span class="sxs-lookup"><span data-stu-id="b2e76-161">Specify **@publication**, **@publisher**, **@publisher_db**, the subscription property being changed as **@property**, and the new value as **@value**.</span></span>  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="b2e76-162">使用 Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="b2e76-162">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="b2e76-163">用於檢視或修改提取訂閱屬性的 RMO 類別，將取決於該提取訂閱所訂閱的發行集類型而定。</span><span class="sxs-lookup"><span data-stu-id="b2e76-163">The RMO classes you use to view or modify pull subscription properties depend on the type of publication to which the pull subscription is subscribed.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="b2e76-164">檢視或修改快照式或交易式發行集之提取訂閱的屬性</span><span class="sxs-lookup"><span data-stu-id="b2e76-164">To view or modify properties of a pull subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="b2e76-165">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與「訂閱者」的連接。</span><span class="sxs-lookup"><span data-stu-id="b2e76-165">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="b2e76-166">建立 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b2e76-166">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> class.</span></span>  
  
3.  <span data-ttu-id="b2e76-167">設定 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>和 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="b2e76-167">Set the <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="b2e76-168">針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定步驟 1 中的連接。</span><span class="sxs-lookup"><span data-stu-id="b2e76-168">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="b2e76-169">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="b2e76-169">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="b2e76-170">如果此方法傳回 `false`，則表示步驟 3 中的訂閱屬性定義不正確，或者此訂閱不存在於伺服器上。</span><span class="sxs-lookup"><span data-stu-id="b2e76-170">If this method returns `false`, either the subscription properties in step 3 were defined incorrectly or the subscription does not exist on the server.</span></span>  
  
6.  <span data-ttu-id="b2e76-171">(選擇性) 若要變更屬性，請針對其中一個可設定的 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> 屬性設定新的值，然後呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b2e76-171">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> properties that can be set, and then call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="b2e76-172">(選擇性) 若要檢視新的設定，請呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> 方法，重新載入發行項的屬性。</span><span class="sxs-lookup"><span data-stu-id="b2e76-172">(Optional) To view the new settings, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> method to reload the properties for the article.</span></span>  
  
8.  <span data-ttu-id="b2e76-173">關閉所有連接。</span><span class="sxs-lookup"><span data-stu-id="b2e76-173">Close all connections.</span></span>  
  
#### <a name="to-view-or-modify-properties-of-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="b2e76-174">檢視或修改合併式發行集之提取訂閱的屬性</span><span class="sxs-lookup"><span data-stu-id="b2e76-174">To view or modify properties of a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="b2e76-175">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與「訂閱者」的連接。</span><span class="sxs-lookup"><span data-stu-id="b2e76-175">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="b2e76-176">建立 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b2e76-176">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> class.</span></span>  
  
3.  <span data-ttu-id="b2e76-177">設定 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>和 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="b2e76-177">Set the <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, and <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> properties.</span></span>  
  
4.  <span data-ttu-id="b2e76-178">針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定步驟 1 中的連接。</span><span class="sxs-lookup"><span data-stu-id="b2e76-178">Set the connection from step 1 for the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property.</span></span>  
  
5.  <span data-ttu-id="b2e76-179">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="b2e76-179">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="b2e76-180">如果此方法傳回 `false`，則表示步驟 3 中的訂閱屬性定義不正確，或者此訂閱不存在於伺服器上。</span><span class="sxs-lookup"><span data-stu-id="b2e76-180">If this method returns `false`, either the subscription properties in step 3 were defined incorrectly or the subscription does not exist on the server.</span></span>  
  
6.  <span data-ttu-id="b2e76-181">(選擇性) 若要變更屬性，請針對其中一個可設定的 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> 屬性設定新的值，然後呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b2e76-181">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> properties that can be set, and then call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="b2e76-182">(選擇性) 若要檢視新的設定，請呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> 方法，重新載入發行項的屬性。</span><span class="sxs-lookup"><span data-stu-id="b2e76-182">(Optional) To view the new settings, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> method to reload the properties for the article.</span></span>  
  
8.  <span data-ttu-id="b2e76-183">關閉所有連接。</span><span class="sxs-lookup"><span data-stu-id="b2e76-183">Close all connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e76-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2e76-184">See Also</span></span>  
 <span data-ttu-id="b2e76-185">[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="b2e76-185">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="b2e76-186">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="b2e76-186">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="b2e76-187">訂閱發行集</span><span class="sxs-lookup"><span data-stu-id="b2e76-187">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
