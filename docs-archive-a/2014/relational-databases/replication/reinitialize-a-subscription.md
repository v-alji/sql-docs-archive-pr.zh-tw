---
title: 重新初始化訂閱 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- initializing subscriptions [SQL Server replication], reinitializing
- subscriptions [SQL Server replication], reinitializing
- reinitializing subscriptions
ms.assetid: ca3625c5-c62e-4ab7-9829-d511f838e385
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f751928c05caa5c4acdcc6c667dc59bb7824021b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709133"
---
# <a name="reinitialize-a-subscription"></a><span data-ttu-id="4a129-102">重新初始化訂閱</span><span class="sxs-lookup"><span data-stu-id="4a129-102">Reinitialize a Subscription</span></span>
  <span data-ttu-id="4a129-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 Replication Management Objects (RMO) 來重新初始化 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-103">This topic describes how to reinitialize a subscription in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span> <span data-ttu-id="4a129-104">個別訂閱可標示為要重新初始化，好讓下一次同步處理期間會套用新的快照集。</span><span class="sxs-lookup"><span data-stu-id="4a129-104">Individual subscriptions can be marked for reinitialization so that a new snapshot is applied during the next synchronization.</span></span>  
  
 <span data-ttu-id="4a129-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="4a129-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4a129-106">**若要重新初始化訂閱，請使用：**</span><span class="sxs-lookup"><span data-stu-id="4a129-106">**To reinitialize a subscription, using:**</span></span>  
  
     [<span data-ttu-id="4a129-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4a129-107">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4a129-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4a129-108">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="4a129-109">Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="4a129-109">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4a129-110">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4a129-110">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="4a129-111">重新初始化訂閱處理分為兩部份：</span><span class="sxs-lookup"><span data-stu-id="4a129-111">Reinitializing a subscription is a two-part process:</span></span>  
  
1.  <span data-ttu-id="4a129-112">*「標示」* 要重新初始化之發行集的單個或所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-112">A single subscription or all subscriptions to a publication are *marked* for reinitialization.</span></span> <span data-ttu-id="4a129-113">在 [重新初始化訂閱] 對話方塊中，標示要重新初始化的訂閱；您可以從 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的 [本機發行集] 資料夾和 [本機訂閱] 資料夾來存取此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4a129-113">Mark subscriptions for reinitialization in the **Reinitialize Subscription(s)** dialog box, which is available from the **Local Publications** folder and the **Local Subscriptions** folder in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="4a129-114">您也可以從「複寫監視器」中的 **[所有訂閱]** 索引標籤和發行集節點中標示訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-114">You can also mark subscriptions from the **All Subscriptions** tab and the publications node in Replication Monitor.</span></span> <span data-ttu-id="4a129-115">如需啟動複寫監視器的詳細資訊，請參閱[啟動複寫監視器](monitor/start-the-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="4a129-115">For information about starting Replication Monitor, see [Start the Replication Monitor](monitor/start-the-replication-monitor.md).</span></span> <span data-ttu-id="4a129-116">當您要標示訂閱進行重新初始化時，可用的選項如下：</span><span class="sxs-lookup"><span data-stu-id="4a129-116">When you mark a subscription for reinitialization, you have the following options:</span></span>  
  
     <span data-ttu-id="4a129-117">**使用目前的快照集**</span><span class="sxs-lookup"><span data-stu-id="4a129-117">**Use the current snapshot**</span></span>  
     <span data-ttu-id="4a129-118">選取即可將目前的快照集套用至散發代理程式或合併代理程式下一次將執行的訂閱者。</span><span class="sxs-lookup"><span data-stu-id="4a129-118">Select to apply the current snapshot to the Subscriber the next time the Distribution Agent or Merge Agent runs.</span></span> <span data-ttu-id="4a129-119">如果沒有任何有效的快照集可以使用，則不可以選取此選項。</span><span class="sxs-lookup"><span data-stu-id="4a129-119">If there is no valid snapshot available, this option cannot be selected.</span></span>  
  
     <span data-ttu-id="4a129-120">**使用新的快照集**</span><span class="sxs-lookup"><span data-stu-id="4a129-120">**Use a new snapshot**</span></span>  
     <span data-ttu-id="4a129-121">選取即可使用新的快照集重新初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-121">Select to reinitialize the subscription with a new snapshot.</span></span> <span data-ttu-id="4a129-122">唯有在快照集代理程式產生快照集之後，該快照集才能套用至訂閱者。</span><span class="sxs-lookup"><span data-stu-id="4a129-122">The snapshot can be applied to the Subscriber only after it has been generated by the Snapshot Agent.</span></span> <span data-ttu-id="4a129-123">如果設定「快照集代理程式」根據排程執行，則只有在下一個排程的「快照集代理程式」執行後，訂閱才會重新初始化。</span><span class="sxs-lookup"><span data-stu-id="4a129-123">If the Snapshot Agent is set to run on a schedule, the subscription is not reinitialized until after the next scheduled Snapshot Agent run.</span></span> <span data-ttu-id="4a129-124">選取 **[立即產生新的快照集]** ，即可立即啟動快照集代理程式。</span><span class="sxs-lookup"><span data-stu-id="4a129-124">Select **Generate the new snapshot now** to start the Snapshot Agent immediately.</span></span>  
  
     <span data-ttu-id="4a129-125">**重新初始化之前，先上傳尚未同步處理的變更**</span><span class="sxs-lookup"><span data-stu-id="4a129-125">**Upload unsynchronized changes before reinitialization**</span></span>  
     <span data-ttu-id="4a129-126">僅限合併式複寫。</span><span class="sxs-lookup"><span data-stu-id="4a129-126">Merge replication only.</span></span> <span data-ttu-id="4a129-127">選取即可在使用快照集覆寫訂閱者端的資料之前，從訂閱資料庫上傳任何暫止變更。</span><span class="sxs-lookup"><span data-stu-id="4a129-127">Select to upload any pending changes from the subscription database before the data at the Subscriber is overwritten with a snapshot.</span></span>  
  
     <span data-ttu-id="4a129-128">如果您新增、卸除或變更參數化篩選，在重新初始化期間，便無法將訂閱者的暫止變更上傳到發行者。</span><span class="sxs-lookup"><span data-stu-id="4a129-128">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="4a129-129">如果您要上傳暫止變更，請在變更篩選之前，同步處理所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-129">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
2.  <span data-ttu-id="4a129-130">訂閱會在下一次同步處理時重新初始化：(異動複寫的)「散發代理程式」或 (合併式複寫的)「合併代理程式」，為含有標示要重新初始化訂閱的每個「訂閱者」套用最新的快照集。</span><span class="sxs-lookup"><span data-stu-id="4a129-130">A subscription is reinitialized the next time it is synchronized: the Distribution Agent (for transactional replication) or Merge Agent (for merge replication) applies the most recent snapshot to each Subscriber that has a subscription marked for reinitialization.</span></span> <span data-ttu-id="4a129-131">如需有關同步處理訂閱的資訊，請參閱＜ [Synchronize a Push Subscription](synchronize-a-push-subscription.md) ＞和＜ [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)資料夾中可用。</span><span class="sxs-lookup"><span data-stu-id="4a129-131">For more information about synchronizing subscriptions, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md) and [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
#### <a name="to-mark-a-single-push-or-pull-subscription-for-reinitialization-in-management-studio-at-the-publisher"></a><span data-ttu-id="4a129-132">若要在 Management Studio (在發行者端) 中標示要重新初始化的單一發送訂閱或提取訂閱</span><span class="sxs-lookup"><span data-stu-id="4a129-132">To mark a single push or pull subscription for reinitialization in Management Studio (at the Publisher)</span></span>  
  
1.  <span data-ttu-id="4a129-133">連接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的發行者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="4a129-133">Connect to the Publisher in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="4a129-134">展開 **[複寫]** 資料夾，然後展開 **[本機發行集]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4a129-134">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="4a129-135">展開含有您要重新初始化之訂閱的發行集。</span><span class="sxs-lookup"><span data-stu-id="4a129-135">Expand the publication that has the subscription you want to reinitialize.</span></span>  
  
4.  <span data-ttu-id="4a129-136">以滑鼠右鍵按一下訂閱，然後按一下 **[重新初始化]** 。</span><span class="sxs-lookup"><span data-stu-id="4a129-136">Right-click the subscription, and then click **Reinitialize**.</span></span>  
  
5.  <span data-ttu-id="4a129-137">在 **[重新初始化訂閱]** 對話方塊中選取選項，然後按一下 **[標示為重新初始化]** 。</span><span class="sxs-lookup"><span data-stu-id="4a129-137">In the **Reinitialize Subscription(s)** dialog box, select options, and then click **Mark for Reinitialization**.</span></span>  
  
#### <a name="to-mark-a-single-pull-subscription-for-reinitialization-in-management-studio-at-the-subscriber"></a><span data-ttu-id="4a129-138">若要在 Management Studio (在訂閱者端) 中標示要重新初始化的單一提取訂閱</span><span class="sxs-lookup"><span data-stu-id="4a129-138">To mark a single pull subscription for reinitialization in Management Studio (at the Subscriber)</span></span>  
  
1.  <span data-ttu-id="4a129-139">連接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的訂閱者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="4a129-139">Connect to the Subscriber in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="4a129-140">展開 **[複寫]** 資料夾，然後展開 **[本機訂閱]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4a129-140">Expand the **Replication** folder, and then expand the **Local Subscriptions** folder.</span></span>  
  
3.  <span data-ttu-id="4a129-141">以滑鼠右鍵按一下訂閱，然後按一下 **[重新初始化]** 。</span><span class="sxs-lookup"><span data-stu-id="4a129-141">Right-click the subscription, and then click **Reinitialize**.</span></span>  
  
4.  <span data-ttu-id="4a129-142">在顯示的確認對話方塊中，按一下 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="4a129-142">In the confirmation dialog box that is displayed, click **Yes**.</span></span>  
  
#### <a name="to-mark-all-subscriptions-for-reinitialization-in-management-studio"></a><span data-ttu-id="4a129-143">若要在 Management Studio 中標示要重新初始化的所有訂閱</span><span class="sxs-lookup"><span data-stu-id="4a129-143">To mark all subscriptions for reinitialization in Management Studio</span></span>  
  
1.  <span data-ttu-id="4a129-144">連接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的發行者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="4a129-144">Connect to the Publisher in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="4a129-145">展開 **[複寫]** 資料夾，然後展開 **[本機發行集]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4a129-145">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="4a129-146">以滑鼠右鍵按一下包含您要重新初始化之訂閱的發行集，然後按一下 **[重新初始化所有訂閱]** 。</span><span class="sxs-lookup"><span data-stu-id="4a129-146">Right-click the publication with subscriptions you want to reinitialize, and then click **Reinitialize All Subscriptions**.</span></span>  
  
4.  <span data-ttu-id="4a129-147">在 **[重新初始化訂閱]** 對話方塊中選取選項，然後按一下 **[標示為重新初始化]** 。</span><span class="sxs-lookup"><span data-stu-id="4a129-147">In the **Reinitialize Subscription(s)** dialog box, select options, and then click **Mark for Reinitialization**.</span></span>  
  
#### <a name="to-mark-a-single-push-or-pull-subscription-for-reinitialization-in-replication-monitor"></a><span data-ttu-id="4a129-148">若要在複寫監視器中標示要重新初始化的單一發送或提取訂閱</span><span class="sxs-lookup"><span data-stu-id="4a129-148">To mark a single push or pull subscription for reinitialization in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="4a129-149">在複寫監視器中，展開左窗格裡的發行者群組，展開發行者，然後按一下發行集。</span><span class="sxs-lookup"><span data-stu-id="4a129-149">In Replication Monitor, expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="4a129-150">按一下 **[所有訂閱]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="4a129-150">Click the **All Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="4a129-151">在您要重新初始化的訂閱上按一下滑鼠右鍵，再按一下 **[重新初始化訂閱]** 。</span><span class="sxs-lookup"><span data-stu-id="4a129-151">Right-click the subscription you want to reinitialize, and then click **Reinitialize Subscription**.</span></span>  
  
4.  <span data-ttu-id="4a129-152">在 **[重新初始化訂閱]** 對話方塊中選取選項，然後按一下 **[標示為重新初始化]** 。</span><span class="sxs-lookup"><span data-stu-id="4a129-152">In the **Reinitialize Subscription(s)** dialog box, select options, and then click **Mark for Reinitialization**.</span></span>  
  
#### <a name="to-mark-all-subscriptions-for-reinitialization-in-replication-monitor"></a><span data-ttu-id="4a129-153">若要在複寫監視器中標示要重新初始化的所有訂閱</span><span class="sxs-lookup"><span data-stu-id="4a129-153">To mark all subscriptions for reinitialization in Replication Monitor</span></span>  
  
1.  <span data-ttu-id="4a129-154">在複寫監視器的左窗格中展開發行者群組，然後展開發行者。</span><span class="sxs-lookup"><span data-stu-id="4a129-154">In Replication Monitor, expand a Publisher group in the left pane, and then expand a Publisher.</span></span>  
  
2.  <span data-ttu-id="4a129-155">以滑鼠右鍵按一下包含您要重新初始化之訂閱的發行集，然後按一下 **[重新初始化所有訂閱]** 。</span><span class="sxs-lookup"><span data-stu-id="4a129-155">Right-click the publication with subscriptions you want to reinitialize, and then click **Reinitialize All Subscriptions**.</span></span>  
  
3.  <span data-ttu-id="4a129-156">在 **[重新初始化訂閱]** 對話方塊中選取選項，然後按一下 **[標示為重新初始化]** 。</span><span class="sxs-lookup"><span data-stu-id="4a129-156">In the **Reinitialize Subscription(s)** dialog box, select options, and then click **Mark for Reinitialization**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4a129-157">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4a129-157">Using Transact-SQL</span></span>  
 <span data-ttu-id="4a129-158">可以使用複寫預存程序來以程式設計的方式重新初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-158">Subscriptions can be reinitialized programmatically using replication stored procedures.</span></span> <span data-ttu-id="4a129-159">使用的預存程序取決於訂閱的類型 (發送訂閱或提取訂閱) 以及訂閱所屬的發行集類型而定。</span><span class="sxs-lookup"><span data-stu-id="4a129-159">The stored procedure that is used depends on the type of subscription (push or pull) and the type of publication to which the subscription belongs.</span></span>  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-transactional-publication"></a><span data-ttu-id="4a129-160">重新初始化交易式發行集的提取訂閱</span><span class="sxs-lookup"><span data-stu-id="4a129-160">To reinitialize a pull subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="4a129-161">在訂閱資料庫的訂閱者端，執行 [sp_reinitpullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitpullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4a129-161">At the Subscriber on the subscription database, execute [sp_reinitpullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitpullsubscription-transact-sql).</span></span> <span data-ttu-id="4a129-162">指定 **@publisher** 、 **@publisher_db** 和 **@publication** 。</span><span class="sxs-lookup"><span data-stu-id="4a129-162">Specify **@publisher**, **@publisher_db**, and **@publication**.</span></span> <span data-ttu-id="4a129-163">這樣會標示此訂閱，在下次執行散發代理程式時重新初始化。</span><span class="sxs-lookup"><span data-stu-id="4a129-163">This marks the subscription for reinitialization the next time the Distribution Agent runs.</span></span>  
  
2.  <span data-ttu-id="4a129-164">(選擇性) 在訂閱者上啟動散發代理程式，以同步處理此訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-164">(Optional) Start the Distribution Agent at the Subscriber to synchronize the subscription.</span></span> <span data-ttu-id="4a129-165">如需相關資訊，請參閱 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="4a129-165">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-transactional-publication"></a><span data-ttu-id="4a129-166">重新初始化交易式發行集的發送訂閱</span><span class="sxs-lookup"><span data-stu-id="4a129-166">To reinitialize a push subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="4a129-167">在發行者端，執行 [sp_reinitsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4a129-167">At the Publisher, execute [sp_reinitsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitsubscription-transact-sql).</span></span> <span data-ttu-id="4a129-168">指定 **@publication** 、 **@subscriber** 和 **@destination_db** 。</span><span class="sxs-lookup"><span data-stu-id="4a129-168">Specify **@publication**, **@subscriber**, and **@destination_db**.</span></span> <span data-ttu-id="4a129-169">這樣會標示此訂閱，在下次執行散發代理程式時重新初始化。</span><span class="sxs-lookup"><span data-stu-id="4a129-169">This marks the subscription for reinitialization the next time the Distribution Agent runs.</span></span>  
  
2.  <span data-ttu-id="4a129-170">(選擇性) 在散發者上啟動散發代理程式，以同步處理此訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-170">(Optional) Start the Distribution Agent at the Distributor to synchronize the subscription.</span></span> <span data-ttu-id="4a129-171">如需詳細資訊，請參閱 [同步處理發送訂閱](synchronize-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="4a129-171">For more information, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="4a129-172">重新初始化合併式發行集的提取訂閱</span><span class="sxs-lookup"><span data-stu-id="4a129-172">To reinitialize a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="4a129-173">在訂閱資料庫的訂閱者端，執行 [sp_reinitmergepullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitmergepullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4a129-173">At the Subscriber on the subscription database, execute [sp_reinitmergepullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitmergepullsubscription-transact-sql).</span></span> <span data-ttu-id="4a129-174">指定 **@publisher** 、 **@publisher_db** 和 **@publication** 。</span><span class="sxs-lookup"><span data-stu-id="4a129-174">Specify **@publisher**, **@publisher_db**, and **@publication**.</span></span> <span data-ttu-id="4a129-175">若要在重新初始化發生之前從訂閱者上傳變更，請為指定的值 `true` **@upload_first** 。</span><span class="sxs-lookup"><span data-stu-id="4a129-175">To upload changes from the Subscriber before reinitialization occurs, specify a value of `true` for **@upload_first**.</span></span> <span data-ttu-id="4a129-176">這樣會標示此訂閱，在下次執行合併代理程式時重新初始化。</span><span class="sxs-lookup"><span data-stu-id="4a129-176">This marks the subscription for reinitialization the next time the Merge Agent runs.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="4a129-177">如果您新增、卸除或變更參數化篩選，在重新初始化期間，便無法將訂閱者的暫止變更上傳到發行者。</span><span class="sxs-lookup"><span data-stu-id="4a129-177">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="4a129-178">如果您要上傳暫止變更，請在變更篩選之前，同步處理所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-178">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
2.  <span data-ttu-id="4a129-179">(選擇性) 在訂閱者上啟動合併代理程式，以同步處理此訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-179">(Optional) Start the Merge Agent at the Subscriber to synchronize the subscription.</span></span> <span data-ttu-id="4a129-180">如需相關資訊，請參閱 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="4a129-180">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="4a129-181">重新初始化合併式發行集的發送訂閱</span><span class="sxs-lookup"><span data-stu-id="4a129-181">To reinitialize a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="4a129-182">在發行者端，執行 [sp_reinitmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitmergesubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4a129-182">At the Publisher, execute [sp_reinitmergesubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-reinitmergesubscription-transact-sql).</span></span> <span data-ttu-id="4a129-183">指定 **@publication** 、 **@subscriber** 和 **@subscriber_db** 。</span><span class="sxs-lookup"><span data-stu-id="4a129-183">Specify **@publication**, **@subscriber**, and **@subscriber_db**.</span></span> <span data-ttu-id="4a129-184">若要在重新初始化發生之前從訂閱者上傳變更，請為指定的值 `true` **@upload_first** 。</span><span class="sxs-lookup"><span data-stu-id="4a129-184">To upload changes from the Subscriber before reinitialization occurs, specify a value of `true` for **@upload_first**.</span></span> <span data-ttu-id="4a129-185">這樣會標示此訂閱，在下次執行散發代理程式時重新初始化。</span><span class="sxs-lookup"><span data-stu-id="4a129-185">This marks the subscription for reinitialization the next time the Distribution Agent runs.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="4a129-186">如果您新增、卸除或變更參數化篩選，在重新初始化期間，便無法將訂閱者的暫止變更上傳到發行者。</span><span class="sxs-lookup"><span data-stu-id="4a129-186">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="4a129-187">如果您要上傳暫止變更，請在變更篩選之前，同步處理所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-187">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
2.  <span data-ttu-id="4a129-188">(選擇性) 在散發者上啟動合併代理程式，以同步處理此訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-188">(Optional) Start the Merge Agent at the Distributor to synchronize the subscription.</span></span> <span data-ttu-id="4a129-189">如需詳細資訊，請參閱 [同步處理發送訂閱](synchronize-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="4a129-189">For more information, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
#### <a name="to-set-the-reinitialization-policy-when-creating-a-new-merge-publication"></a><span data-ttu-id="4a129-190">在建立新的合併式發行集時，設定重新初始化原則</span><span class="sxs-lookup"><span data-stu-id="4a129-190">To set the reinitialization policy when creating a new merge publication</span></span>  
  
1.  <span data-ttu-id="4a129-191">在發行集資料庫的發行者上，執行 [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)，針對 **@automatic_reinitialization_policy**指定下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="4a129-191">At the Publisher on the publication database, execute [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql), specifying one of the following values for **@automatic_reinitialization_policy**:</span></span>  
  
    -   <span data-ttu-id="4a129-192">**1** - 在發行集的變更需要自動重新初始化訂閱之前，從訂閱者上傳變更。</span><span class="sxs-lookup"><span data-stu-id="4a129-192">**1** - changes are uploaded from the Subscriber before a subscription is automatically reinitialized as required by a change to the publication.</span></span>  
  
    -   <span data-ttu-id="4a129-193">**0** - 在發行集的變更需要自動重新初始化訂閱時，捨棄訂閱者上的變更。</span><span class="sxs-lookup"><span data-stu-id="4a129-193">**0** - changes at the Subscriber are discarded when a subscription is automatically reinitialized as required by a change to the publication.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="4a129-194">如果您新增、卸除或變更參數化篩選，在重新初始化期間，便無法將訂閱者的暫止變更上傳到發行者。</span><span class="sxs-lookup"><span data-stu-id="4a129-194">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="4a129-195">如果您要上傳暫止變更，請在變更篩選之前，同步處理所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-195">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
     <span data-ttu-id="4a129-196">如需詳細資訊，請參閱[建立發行集](publish/create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="4a129-196">For more information, see [Create a Publication](publish/create-a-publication.md).</span></span>  
  
#### <a name="to-change-the-reinitialization-policy-for-an-existing-merge-publication"></a><span data-ttu-id="4a129-197">針對現有的合併式發行集變更重新初始化原則</span><span class="sxs-lookup"><span data-stu-id="4a129-197">To change the reinitialization policy for an existing merge publication</span></span>  
  
1.  <span data-ttu-id="4a129-198">在發行集資料庫的發行者上，執行 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)，針對 **@property** @upload_first **@property** ，並針對 **@value**指定下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="4a129-198">At the Publisher on the publication database, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specifying **automatic_reinitialization_policy** for **@property** and one of the following values for **@value**:</span></span>  
  
    -   <span data-ttu-id="4a129-199">**1** - 在發行集的變更需要自動重新初始化訂閱之前，從訂閱者上傳變更。</span><span class="sxs-lookup"><span data-stu-id="4a129-199">**1** - changes are uploaded from the Subscriber before a subscription is automatically reinitialized as required by a change to the publication.</span></span>  
  
    -   <span data-ttu-id="4a129-200">**0** - 在發行集的變更需要自動重新初始化訂閱時，捨棄訂閱者上的變更。</span><span class="sxs-lookup"><span data-stu-id="4a129-200">**0** - changes at the Subscriber are discarded when a subscription is automatically reinitialized as required by a change to the publication.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="4a129-201">如果您新增、卸除或變更參數化篩選，在重新初始化期間，便無法將訂閱者的暫止變更上傳到發行者。</span><span class="sxs-lookup"><span data-stu-id="4a129-201">If you add, drop, or change a parameterized filter, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="4a129-202">如果您要上傳暫止變更，請在變更篩選之前，同步處理所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-202">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
     <span data-ttu-id="4a129-203">如需詳細資訊，請參閱 [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="4a129-203">For more information, see [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).</span></span>  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="4a129-204">使用 Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="4a129-204">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="4a129-205">個別訂閱可標示為要重新初始化，好讓下一次同步處理期間會套用新的快照集。</span><span class="sxs-lookup"><span data-stu-id="4a129-205">Individual subscriptions can be marked for reinitialization so that during the next synchronization, a new snapshot is applied.</span></span> <span data-ttu-id="4a129-206">您可以使用 Replication Management Objects (RMO) 以程式設計的方式重新初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-206">Subscriptions can be reinitialized programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="4a129-207">使用的類別取決於訂閱所屬的發行集類型及訂閱的類型 (發送訂閱或提取訂閱) 而定。</span><span class="sxs-lookup"><span data-stu-id="4a129-207">The classes you use depend on the type of publication to which the subscription belongs and the type of subscription (that is, a push or pull subscription).</span></span>  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-transactional-publication"></a><span data-ttu-id="4a129-208">重新初始化交易式發行集的提取訂閱</span><span class="sxs-lookup"><span data-stu-id="4a129-208">To reinitialize a pull subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="4a129-209">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與「訂閱者」的連接。</span><span class="sxs-lookup"><span data-stu-id="4a129-209">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="4a129-210">建立 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> 類別的執行個體，並設定 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>及針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>設定步驟 1 中的連接。</span><span class="sxs-lookup"><span data-stu-id="4a129-210">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPullSubscription> class, and set <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>, and the connection from step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="4a129-211">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="4a129-211">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4a129-212">如果此方法傳回 `false`，則表示步驟 2 中的訂閱屬性定義不正確，或者提取訂閱不存在。</span><span class="sxs-lookup"><span data-stu-id="4a129-212">If this method returns `false`, either the subscription properties in step 2 were defined incorrectly or the pull subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="4a129-213">呼叫 <xref:Microsoft.SqlServer.Replication.TransPullSubscription.Reinitialize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="4a129-213">Call the <xref:Microsoft.SqlServer.Replication.TransPullSubscription.Reinitialize%2A> method.</span></span> <span data-ttu-id="4a129-214">此方法會標示要重新初始化的訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-214">This method marks the subscription for reinitialization.</span></span>  
  
5.  <span data-ttu-id="4a129-215">同步處理提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-215">Synchronize the pull subscription.</span></span> <span data-ttu-id="4a129-216">如需相關資訊，請參閱 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="4a129-216">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-transactional-publication"></a><span data-ttu-id="4a129-217">重新初始化交易式發行集的發送訂閱</span><span class="sxs-lookup"><span data-stu-id="4a129-217">To reinitialize a push subscription to a transactional publication</span></span>  
  
1.  <span data-ttu-id="4a129-218">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="4a129-218">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="4a129-219">建立 <xref:Microsoft.SqlServer.Replication.TransSubscription> 類別的執行個體，並設定 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>及針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>設定步驟 1 中的連接。</span><span class="sxs-lookup"><span data-stu-id="4a129-219">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransSubscription> class, and set <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, and the connection from step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="4a129-220">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="4a129-220">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4a129-221">如果此方法傳回 `false`，則表示步驟 2 中的訂閱屬性定義不正確，或者發送訂閱不存在。</span><span class="sxs-lookup"><span data-stu-id="4a129-221">If this method returns `false`, either the subscription properties in step 2 were defined incorrectly or the push subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="4a129-222">呼叫 <xref:Microsoft.SqlServer.Replication.TransSubscription.Reinitialize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="4a129-222">Call the <xref:Microsoft.SqlServer.Replication.TransSubscription.Reinitialize%2A> method.</span></span> <span data-ttu-id="4a129-223">此方法會標示要重新初始化的訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-223">This method marks the subscription for reinitialization.</span></span>  
  
5.  <span data-ttu-id="4a129-224">同步處理發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-224">Synchronize the push subscription.</span></span> <span data-ttu-id="4a129-225">如需詳細資訊，請參閱 [同步處理發送訂閱](synchronize-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="4a129-225">For more information, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-pull-subscription-to-a-merge-publication"></a><span data-ttu-id="4a129-226">重新初始化合併式發行集的提取訂閱</span><span class="sxs-lookup"><span data-stu-id="4a129-226">To reinitialize a pull subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="4a129-227">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與「訂閱者」的連接。</span><span class="sxs-lookup"><span data-stu-id="4a129-227">Create a connection to the Subscriber by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="4a129-228">建立 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> 類別的執行個體，並設定 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>及針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>設定步驟 1 中的連接。</span><span class="sxs-lookup"><span data-stu-id="4a129-228">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePullSubscription> class, and set <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>, and the connection from step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="4a129-229">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="4a129-229">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4a129-230">如果此方法傳回 `false`，則表示步驟 2 中的訂閱屬性定義不正確，或者提取訂閱不存在。</span><span class="sxs-lookup"><span data-stu-id="4a129-230">If this method returns `false`, either the subscription properties in step 2 were defined incorrectly or the pull subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="4a129-231">呼叫 <xref:Microsoft.SqlServer.Replication.MergePullSubscription.Reinitialize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="4a129-231">Call the <xref:Microsoft.SqlServer.Replication.MergePullSubscription.Reinitialize%2A> method.</span></span> <span data-ttu-id="4a129-232">傳遞 `true` 的值可在重新初始化之前上傳訂閱者上的變更，或者傳遞 `false` 的值可重新初始化及遺失訂閱者上的任何暫止變更。</span><span class="sxs-lookup"><span data-stu-id="4a129-232">Pass a value of `true` to upload changes at the Subscriber before reinitialization or a value of `false` to reinitialize and lose any pending changes at the Subscriber.</span></span> <span data-ttu-id="4a129-233">此方法會標示要重新初始化的訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-233">This method marks the subscription for reinitialization.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4a129-234">如果此訂閱已過期，將無法上傳變更。</span><span class="sxs-lookup"><span data-stu-id="4a129-234">Changes cannot be uploaded if the subscription is expired.</span></span> <span data-ttu-id="4a129-235">如需詳細資訊，請參閱 [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="4a129-235">For more information, see [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md).</span></span>  
  
5.  <span data-ttu-id="4a129-236">同步處理提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-236">Synchronize the pull subscription.</span></span> <span data-ttu-id="4a129-237">如需相關資訊，請參閱 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="4a129-237">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
#### <a name="to-reinitialize-a-push-subscription-to-a-merge-publication"></a><span data-ttu-id="4a129-238">重新初始化合併式發行集的發送訂閱</span><span class="sxs-lookup"><span data-stu-id="4a129-238">To reinitialize a push subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="4a129-239">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="4a129-239">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="4a129-240">建立 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 類別的執行個體，並設定 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>及針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>設定步驟 1 中的連接。</span><span class="sxs-lookup"><span data-stu-id="4a129-240">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeSubscription> class, and set <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, and the connection from step 1 for <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.</span></span>  
  
3.  <span data-ttu-id="4a129-241">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="4a129-241">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4a129-242">如果此方法傳回 `false`，則表示步驟 2 中的訂閱屬性定義不正確，或者發送訂閱不存在。</span><span class="sxs-lookup"><span data-stu-id="4a129-242">If this method returns `false`, either the subscription properties in step 2 were defined incorrectly or the push subscription does not exist.</span></span>  
  
4.  <span data-ttu-id="4a129-243">呼叫 <xref:Microsoft.SqlServer.Replication.MergeSubscription.Reinitialize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="4a129-243">Call the <xref:Microsoft.SqlServer.Replication.MergeSubscription.Reinitialize%2A> method.</span></span> <span data-ttu-id="4a129-244">傳遞 `true` 的值可在重新初始化之前上傳訂閱者上的變更，或者傳遞 `false` 的值可重新初始化及遺失訂閱者上的任何暫止變更。</span><span class="sxs-lookup"><span data-stu-id="4a129-244">Pass a value of `true` to upload changes at the Subscriber before reinitialization or a value of `false` to reinitialize and lose any pending changes at the Subscriber.</span></span> <span data-ttu-id="4a129-245">此方法會標示要重新初始化的訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-245">This method marks the subscription for reinitialization.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4a129-246">如果此訂閱已過期，將無法上傳變更。</span><span class="sxs-lookup"><span data-stu-id="4a129-246">Changes cannot be uploaded if the subscription is expired.</span></span> <span data-ttu-id="4a129-247">如需詳細資訊，請參閱 [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="4a129-247">For more information, see [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md).</span></span>  
  
5.  <span data-ttu-id="4a129-248">同步處理發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-248">Synchronize the push subscription.</span></span> <span data-ttu-id="4a129-249">如需詳細資訊，請參閱 [同步處理發送訂閱](synchronize-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="4a129-249">For more information, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="4a129-250">範例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="4a129-250">Examples (RMO)</span></span>  
 <span data-ttu-id="4a129-251">此範例會重新初始化交易式發行集的提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-251">This example reinitializes a pull subscription to a transactional publication.</span></span>  
  
 [!code-csharp[HowTo#rmo_ReinitTranPullSub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_reinittranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_ReinitTranPullSub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_reinittranpullsub)]  
  
 <span data-ttu-id="4a129-252">此範例會在初次上傳訂閱者上的暫止變更之後，重新初始化合併式發行集的提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="4a129-252">This example reinitializes a pull subscription to a merge publication after first uploading pending changes at the Subscriber.</span></span>  
  
 [!code-csharp[HowTo#rmo_ReinitMergePullSub_WithUpload](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_reinitmergepullsub_withupload)]  
  
 [!code-vb[HowTo#rmo_vb_ReinitMergePullSub_WithUpload](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_reinitmergepullsub_withupload)]  
  
## <a name="see-also"></a><span data-ttu-id="4a129-253">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a129-253">See Also</span></span>  
 <span data-ttu-id="4a129-254">[重新初始化訂閱](reinitialize-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="4a129-254">[Reinitialize Subscriptions](reinitialize-subscriptions.md) </span></span>  
 <span data-ttu-id="4a129-255">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="4a129-255">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span></span>  
 [<span data-ttu-id="4a129-256">複寫安全性最佳作法</span><span class="sxs-lookup"><span data-stu-id="4a129-256">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
