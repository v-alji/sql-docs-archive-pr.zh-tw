---
title: 切換可更新之交易式訂閱的更新模式 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, updatable subscriptions
- updatable subscriptions, update modes
- subscriptions [SQL Server replication], updatable
ms.assetid: ab5ebab1-7ee4-41f4-999b-b4f0c420c921
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c31814d1e2ab6fac64ffcde883f3cac2439828a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607379"
---
# <a name="switch-between-update-modes-for-an-updatable-transactional-subscription"></a><span data-ttu-id="c4fef-102">切換可更新之交易式訂閱的更新模式</span><span class="sxs-lookup"><span data-stu-id="c4fef-102">Switch Between Update Modes for an Updatable Transactional Subscription</span></span>
  <span data-ttu-id="c4fef-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中切換可更新之交易訂閱的更新模式。</span><span class="sxs-lookup"><span data-stu-id="c4fef-103">This topic describes how to switch between update modes for an updatable transaction subscription in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="c4fef-104">使用「新增訂閱精靈」指定可更新訂閱的模式。</span><span class="sxs-lookup"><span data-stu-id="c4fef-104">Specify the mode for updatable subscriptions using the New Subscription Wizard.</span></span> <span data-ttu-id="c4fef-105">如需使用此精靈時設定模式的資訊，請參閱[檢視及修改提取訂閱屬性](../view-and-modify-pull-subscription-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="c4fef-105">For information about setting the mode when using this wizard, see [View and Modify Pull Subscription Properties](../view-and-modify-pull-subscription-properties.md).</span></span>  
  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c4fef-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="c4fef-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c4fef-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="c4fef-107">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="c4fef-108">您可以隨時從立即更新容錯移轉到到佇列更新。</span><span class="sxs-lookup"><span data-stu-id="c4fef-108">You can fail over from immediate to queued updating at any time.</span></span> <span data-ttu-id="c4fef-109">不過在進行這項作業之後，在「訂閱者」和「發行者」連接，且「佇列讀取器代理程式」將佇列中所有暫止訊息套用至「發行者」之前，無法切換回立即更新。</span><span class="sxs-lookup"><span data-stu-id="c4fef-109">After you do, however, you cannot return to immediate updating until the Subscriber and Publisher are connected and the Queue Reader Agent has applied all pending messages in the queue to the Publisher.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="c4fef-110">建議</span><span class="sxs-lookup"><span data-stu-id="c4fef-110">Recommendations</span></span>  
  
-   <span data-ttu-id="c4fef-111">當交易式訂閱的更新訂閱支援從一種更新模式容錯移轉到另一種模式時，您可以透過程式設計的方式切換更新模式，以處理連接在短時間內變更的情況。</span><span class="sxs-lookup"><span data-stu-id="c4fef-111">When an updating subscription to a transactional publication supports failover from one updating mode to another, you can programmatically switch update modes to handle situations when connectivity changes for a short period of time.</span></span> <span data-ttu-id="c4fef-112">您可以使用複寫預存程序，以程式設計的方式並視需要而設定更新模式。</span><span class="sxs-lookup"><span data-stu-id="c4fef-112">The update mode can be set programmatically and on demand using replication stored procedures.</span></span> <span data-ttu-id="c4fef-113">如需詳細資訊，請參閱 [Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="c4fef-113">For more information, see [Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c4fef-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c4fef-114">Using SQL Server Management Studio</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c4fef-115">若要在建立訂閱後變更更新模式，則須在建立訂閱時將 **update_mode** 屬性設為 **failover** (允許從立即更新切換到佇列更新) 或 **queued failover** (允許從佇列更新切換到立即更新)。</span><span class="sxs-lookup"><span data-stu-id="c4fef-115">To change the update mode after the subscription is created, the **update_mode** property must be set to **failover** (which allows a switch from immediate updating to queued updating) or **queued failover** (which allows a switch from queued updating to immediate updating) when the subscription is created.</span></span> <span data-ttu-id="c4fef-116">這些屬性會自動在「新增訂閱精靈」中設定。</span><span class="sxs-lookup"><span data-stu-id="c4fef-116">These properties are set automatically in the New Subscription Wizard.</span></span>  
  
#### <a name="to-set-the-updating-mode-for-a-push-subscription"></a><span data-ttu-id="c4fef-117">若要設定發送訂閱的更新模式</span><span class="sxs-lookup"><span data-stu-id="c4fef-117">To set the updating mode for a push subscription</span></span>  
  
1.  <span data-ttu-id="c4fef-118">連接到 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中的訂閱者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="c4fef-118">Connect to the Subscriber in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="c4fef-119">展開 **[複寫]** 資料夾，然後展開 **[本機訂閱]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c4fef-119">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="c4fef-120">以滑鼠右鍵按一下您要設定更新模式的訂閱，再按一下 **[設定更新方法]** 。</span><span class="sxs-lookup"><span data-stu-id="c4fef-120">Right-click the subscription for which you want to set the update mode, and then click **Set Update Method**.</span></span>  
  
4.  <span data-ttu-id="c4fef-121">在 [設定更新方法 - \<Subscriber>: \<SubscriptionDatabase>] 對話方塊中，選取 [立即更新] 或 [佇列更新]。</span><span class="sxs-lookup"><span data-stu-id="c4fef-121">In the **Set Update Method - \<Subscriber>: \<SubscriptionDatabase>** dialog box, select **Immediate updating** or **Queued updating**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-set-the-updating-mode-for-a-pull-subscription"></a><span data-ttu-id="c4fef-122">若要設定提取訂閱的更新模式</span><span class="sxs-lookup"><span data-stu-id="c4fef-122">To set the updating mode for a pull subscription</span></span>  
  
1.  <span data-ttu-id="c4fef-123">在 [訂閱屬性 - \<Publisher>: \<PublicationDatabase>] 對話方塊中，選取 [立即複寫變更] 的值，或 [訂閱者更新方法] 選項的 [佇列變更]。</span><span class="sxs-lookup"><span data-stu-id="c4fef-123">In the **Subscription Properties - \<Publisher>: \<PublicationDatabase>** dialog box, select a value of **Immediately replicate changes** or **Queue changes** for the **Subscriber update method** option.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="c4fef-124">如需存取 [訂閱屬性 - \<Publisher>: \<PublicationDatabase>] 對話方塊的詳細資訊，請參閱[檢視及修改發送訂閱屬性](../view-and-modify-pull-subscription-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="c4fef-124">For more information about accessing the **Subscription Properties - \<Publisher>: \<PublicationDatabase>** dialog box, see [View and Modify Pull Subscription Properties](../view-and-modify-pull-subscription-properties.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c4fef-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c4fef-125">Using Transact-SQL</span></span>  
  
#### <a name="to-switch-between-update-modes"></a><span data-ttu-id="c4fef-126">切換更新模式</span><span class="sxs-lookup"><span data-stu-id="c4fef-126">To switch between update modes</span></span>  
  
1.  <span data-ttu-id="c4fef-127">針對提取訂閱執行 [sp_helppullsubscription](/sql/relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql) ，或針對發送訂閱執行 [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql) ，確定訂閱支援容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="c4fef-127">Verify that the subscription supports failover by executing [sp_helppullsubscription](/sql/relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql) for a pull subscription or [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql) for a push subscription.</span></span> <span data-ttu-id="c4fef-128">如果結果集中 **update mode** 的值是 **3** 或 **4**，即支援容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="c4fef-128">If the value of **update mode** in the result set is **3** or **4**, failover is supported.</span></span>  
  
2.  <span data-ttu-id="c4fef-129">在訂閱資料庫的「訂閱者」端執行 [sp_setreplfailovermode](/sql/relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c4fef-129">At the Subscriber on the subscription database, execute [sp_setreplfailovermode](/sql/relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql).</span></span> <span data-ttu-id="c4fef-130">指定 **@publisher** 、 **@publisher_db** 、 **@publication** 和的下列其中一個值 **@failover_mode** ：</span><span class="sxs-lookup"><span data-stu-id="c4fef-130">Specify **@publisher**, **@publisher_db**, **@publication**, and one of the following values for **@failover_mode**:</span></span>  
  
    -   <span data-ttu-id="c4fef-131">**queued** - 當連接已暫時遺失時，容錯移轉到佇列更新。</span><span class="sxs-lookup"><span data-stu-id="c4fef-131">**queued** - fail over to queued updating when connectivity has been temporarily lost.</span></span>  
  
    -   <span data-ttu-id="c4fef-132">**immediate** - 當連接已還原時，容錯移轉到立即更新。</span><span class="sxs-lookup"><span data-stu-id="c4fef-132">**immediate** - fail over to immediate updating when connectivity has been restored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4fef-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4fef-133">See Also</span></span>  
 [<span data-ttu-id="c4fef-134">Updatable Subscriptions for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="c4fef-134">Updatable Subscriptions for Transactional Replication</span></span>](../transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
