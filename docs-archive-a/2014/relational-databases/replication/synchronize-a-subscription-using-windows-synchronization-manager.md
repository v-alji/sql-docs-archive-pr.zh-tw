---
title: 使用 Windows 同步處理管理員同步處理訂閱 (Windows 同步處理管理員) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], Windows Synchronization Manager
- Windows Synchronization Manager
ms.assetid: 80f15dd6-e84d-4f96-9866-5b34ea531f1e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bb31c344f91c68b04e03dd218f22b09bec44830b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701023"
---
# <a name="synchronize-a-subscription-using-windows-synchronization-manager-windows-synchronization-manager"></a><span data-ttu-id="54caa-102">使用 Windows Synchronization Manager 同步處理訂閱 (Windows Synchronization Manager)</span><span class="sxs-lookup"><span data-stu-id="54caa-102">Synchronize a Subscription Using Windows Synchronization Manager (Windows Synchronization Manager)</span></span>
  <span data-ttu-id="54caa-103">如果 Microsoft[!INCLUDE[msCoName](../../includes/msconame-md.md)] 與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows Synchronization Manager 在相同的電腦上執行，則 Synchronization Manager 只能用於同步處理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 發行集的訂閱 (它也可以用於同步處理離線檔案和網頁)。</span><span class="sxs-lookup"><span data-stu-id="54caa-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Synchronization Manager can only be used to synchronize subscriptions to Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] publications if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running on the same computer as Synchronization Manager (it can also be used to synchronize offline files and Web pages).</span></span> <span data-ttu-id="54caa-104">若要使用 Synchronization Manager：</span><span class="sxs-lookup"><span data-stu-id="54caa-104">To use Synchronization Manager:</span></span>  
  
1.  <span data-ttu-id="54caa-105">在 [訂閱屬性 - \<Subscriber>: \<SubscriptionDatabase>] 對話方塊中，啟用提取訂閱與 Windows Synchronization Manager 的同步處理。</span><span class="sxs-lookup"><span data-stu-id="54caa-105">Enable the synchronization of pull subscriptions with Windows Synchronization Manager in the **Subscription Properties - \<Subscriber>: \<SubscriptionDatabase>** dialog box.</span></span> <span data-ttu-id="54caa-106">如需存取此對話方塊的詳細資訊，請參閱[檢視及修改提取訂閱屬性](view-and-modify-pull-subscription-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="54caa-106">For more information about accessing this dialog box, see [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).</span></span>  
  
2.  <span data-ttu-id="54caa-107">透過 Windows 中的 **[開始]** 功能表存取 Synchronization Manager。</span><span class="sxs-lookup"><span data-stu-id="54caa-107">Access Synchronization Manager through the **Start** menu in Windows.</span></span>  
  
 <span data-ttu-id="54caa-108">Synchronization Manager 允許您為合併訂閱使用「互動解決器」。</span><span class="sxs-lookup"><span data-stu-id="54caa-108">Synchronization Manager allows you to use the Interactive Resolver for merge subscriptions.</span></span> <span data-ttu-id="54caa-109">通常，同步處理期間偵測到的衝突會自動解決，但是如果啟用了互動式解決方案，衝突可由使用者在同步處理期間解決。</span><span class="sxs-lookup"><span data-stu-id="54caa-109">Typically, conflicts detected during synchronization are resolved automatically, but if interactive resolution is enabled, conflicts can be resolved by a user during synchronization.</span></span> <span data-ttu-id="54caa-110">如果是在 Windows Synchronization Manager 之外執行同步處理 (如 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或複寫監視器中已排程的同步處理或視需要同步處理)，則不需要使用者的介入，就會根據為發行項指定的解決器自動解決衝突。</span><span class="sxs-lookup"><span data-stu-id="54caa-110">If a synchronization is performed outside of Windows Synchronization Manager (as a scheduled synchronization or an on demand synchronization in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Replication Monitor), conflicts are resolved automatically without user intervention, according to the resolver specified for the article.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="54caa-111">從 [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] 和 [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)]開始，64 位元版本的 Windows Synchronization Manager 無法偵測 32 位元訂閱。</span><span class="sxs-lookup"><span data-stu-id="54caa-111">Beginning with [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] and [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)], 64-bit versions of the Windows Synchronization Manager cannot detect 32-bit subscriptions.</span></span>  
  
### <a name="to-enable-the-synchronization-of-pull-subscriptions-with-windows-synchronization-manager"></a><span data-ttu-id="54caa-112">若要使用 Windows Synchronization Manager 啟用提取訂閱同步處理</span><span class="sxs-lookup"><span data-stu-id="54caa-112">To enable the synchronization of pull subscriptions with Windows Synchronization Manager</span></span>  
  
1.  <span data-ttu-id="54caa-113">在 [訂閱屬性 - \<Subscriber>: \<SubscriptionDatabase>] 對話方塊的 [一般] 頁面上，針對 [使用 Windows Synchronization Manager] 選項選取 [啟用] 的值。</span><span class="sxs-lookup"><span data-stu-id="54caa-113">On the **General** page of the **Subscription Properties - \<Subscriber>: \<SubscriptionDatabase>** dialog box, select a value of **Enable** for the **Use Windows Synchronization Manager** option.</span></span>  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-synchronize-a-pull-subscription-with-synchronization-manager"></a><span data-ttu-id="54caa-114">若要使用 Synchronization Manager 同步處理提取訂閱</span><span class="sxs-lookup"><span data-stu-id="54caa-114">To synchronize a pull subscription with Synchronization Manager</span></span>  
  
1.  <span data-ttu-id="54caa-115">請利用下列其中一種方法來啟動 Synchronization Manager：</span><span class="sxs-lookup"><span data-stu-id="54caa-115">Launch Synchronization Manager using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="54caa-116">在 Internet Explorer 中，按一下 **[工具]** ，然後按一下 **[同步處理]** 。</span><span class="sxs-lookup"><span data-stu-id="54caa-116">In Internet Explorer, click **Tools**, and then click **Synchronize**.</span></span>  
  
    -   <span data-ttu-id="54caa-117">按一下 **[開始]** ，依序指向 **[程式集]** (或 **[程式集]** ) 和 **[附屬應用程式]** ，然後按一下 **[同步處理]** 。</span><span class="sxs-lookup"><span data-stu-id="54caa-117">Click **Start**, point to **Programs** or **All Programs**, point to **Accessories**, and then click **Synchronize**.</span></span>  
  
    -   <span data-ttu-id="54caa-118">按一下 **[開始]** ，然後按一下 **[執行]**</span><span class="sxs-lookup"><span data-stu-id="54caa-118">Click **Start**, and then click **Run.**</span></span> <span data-ttu-id="54caa-119">在 [**執行**] 對話方塊的 `mobsync.exe` [**開啟**] 欄位中輸入，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="54caa-119">In the **Run** dialog box, type `mobsync.exe` in the **Open** field, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="54caa-120">在 **[要同步處理的項目]** 對話方塊中，選取要同步處理的訂閱。</span><span class="sxs-lookup"><span data-stu-id="54caa-120">In the **Items to Synchronize** dialog box, select the subscriptions to synchronize.</span></span> <span data-ttu-id="54caa-121">訂閱會列在電腦上安裝的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體之下。</span><span class="sxs-lookup"><span data-stu-id="54caa-121">Subscriptions are listed under the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span>  
  
3.  <span data-ttu-id="54caa-122">按一下 **[同步處理]** 。</span><span class="sxs-lookup"><span data-stu-id="54caa-122">Click **Synchronize**.</span></span>  
  
### <a name="to-reinitialize-a-pull-subscription-with-synchronization-manager"></a><span data-ttu-id="54caa-123">若要使用 Synchronization Manager 重新初始化提取訂閱</span><span class="sxs-lookup"><span data-stu-id="54caa-123">To reinitialize a pull subscription with Synchronization Manager</span></span>  
  
1.  <span data-ttu-id="54caa-124">在 **[要同步處理的項目]** 對話方塊中，選取訂閱，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="54caa-124">In the **Items to Synchronize** dialog box, select a subscription, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="54caa-125">在 **[SQL Server 訂閱屬性]** 對話方塊中，按一下 **[重新初始化訂閱]** 。</span><span class="sxs-lookup"><span data-stu-id="54caa-125">In the **SQL Server Subscription Properties** dialog box, click **Reinitialize Subscription**.</span></span>  
  
3.  <span data-ttu-id="54caa-126">按一下 [是] 。</span><span class="sxs-lookup"><span data-stu-id="54caa-126">Click **Yes**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="54caa-127">下次同步處理訂閱時，依預設，訂閱資料庫會套用一個新的快照集。</span><span class="sxs-lookup"><span data-stu-id="54caa-127">The next time the subscription is synchronized, by default a new snapshot is applied to the subscription database.</span></span> <span data-ttu-id="54caa-128">如需詳細資訊，請參閱 [重新初始化訂閱](reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="54caa-128">For more information, see [Reinitialize Subscriptions](reinitialize-subscriptions.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="54caa-129">合併式複寫允許在套用快照集前，將尚未處理完畢的變更上傳到「發行者」，但是此選項在 Synchronization Manager 中不可用。</span><span class="sxs-lookup"><span data-stu-id="54caa-129">Merge replication allows any outstanding changes to be uploaded to the Publisher before the snapshot is applied, but this option is not available from Synchronization Manager.</span></span> <span data-ttu-id="54caa-130">若要上傳變更，請在重新初始化訂閱前，對其執行同步處理。</span><span class="sxs-lookup"><span data-stu-id="54caa-130">To upload changes, synchronize the subscription before reinitializing it.</span></span>  
  
### <a name="to-set-properties-for-a-pull-subscription-in-synchronization-manager"></a><span data-ttu-id="54caa-131">若要在 Synchronization Manager 中設定提取訂閱的屬性</span><span class="sxs-lookup"><span data-stu-id="54caa-131">To set properties for a pull subscription in Synchronization Manager</span></span>  
  
1.  <span data-ttu-id="54caa-132">在 **[要同步處理的項目]** 對話方塊中，選取訂閱，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="54caa-132">In the **Items to Synchronize** dialog box, select a subscription, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="54caa-133">在下列索引標籤中檢視並修改屬性：</span><span class="sxs-lookup"><span data-stu-id="54caa-133">View and modify properties on the following tabs:</span></span>  
  
    -   <span data-ttu-id="54caa-134">**識別**</span><span class="sxs-lookup"><span data-stu-id="54caa-134">**Identification**</span></span>  
  
    -   <span data-ttu-id="54caa-135">**[訂閱者登入]** 、 **[散發者登入]** 和 **[發行者登入]** (僅用於合併式複寫)</span><span class="sxs-lookup"><span data-stu-id="54caa-135">**Subscriber Login**, **Distributor Login**, and **Publisher Login** (for merge replication only)</span></span>  
  
    -   <span data-ttu-id="54caa-136">**[Web 伺服器資訊]** (用於執行 SQL Server 2005 或更新版本之「訂閱者」端的合併訂閱)</span><span class="sxs-lookup"><span data-stu-id="54caa-136">**Web Server Information** (for merge subscriptions on Subscribers running SQL Server 2005 or later)</span></span>  
  
    -   <span data-ttu-id="54caa-137">**其他**</span><span class="sxs-lookup"><span data-stu-id="54caa-137">**Other**</span></span>  
  
     <span data-ttu-id="54caa-138">建議對所有連接使用「Windows 驗證」。</span><span class="sxs-lookup"><span data-stu-id="54caa-138">It is recommended to use Windows Authentication for all connections.</span></span> <span data-ttu-id="54caa-139">如需「散發代理程式」和「合併代理程式」所需權限的詳細資訊，請參閱＜ [Replication Agent Security Model](security/replication-agent-security-model.md)＞。</span><span class="sxs-lookup"><span data-stu-id="54caa-139">For information about the permissions required by the Distribution Agent and the Merge Agent, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-remove-a-pull-subscription-from-synchronization-manager"></a><span data-ttu-id="54caa-140">若要從 Synchronization Manager 中移除提取訂閱</span><span class="sxs-lookup"><span data-stu-id="54caa-140">To remove a pull subscription from Synchronization Manager</span></span>  
  
1.  <span data-ttu-id="54caa-141">在 **[要同步處理的項目]** 對話方塊中，選取訂閱，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="54caa-141">In the **Items to Synchronize** dialog box, select a subscription, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="54caa-142">在 **[SQL Server 訂閱屬性]** 對話方塊中按一下 **[移除訂閱]** 。</span><span class="sxs-lookup"><span data-stu-id="54caa-142">In the **SQL Server Subscription Properties** dialog box, click **Remove Subscription**.</span></span>  
  
3.  <span data-ttu-id="54caa-143">在 **[移除訂閱]** 對話方塊中選取一個選項。</span><span class="sxs-lookup"><span data-stu-id="54caa-143">Select an option in the **Remove Subscription** dialog box.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-use-the-interactive-resolver"></a><span data-ttu-id="54caa-144">若要使用互動解決器</span><span class="sxs-lookup"><span data-stu-id="54caa-144">To use the Interactive Resolver</span></span>  
  
1.  <span data-ttu-id="54caa-145">啟用發行項和訂閱以使用互動式解決方案。</span><span class="sxs-lookup"><span data-stu-id="54caa-145">Enable the article and subscription to use interactive resolution.</span></span> <span data-ttu-id="54caa-146">如需詳細資訊，請參閱[指定合併發行項的互動式衝突解決方法](../../relational-databases/replication/publish/specify-merge-replication-properties.md#interactive-conflict-resolution)。</span><span class="sxs-lookup"><span data-stu-id="54caa-146">For more information, see [Specify Interactive Conflict Resolution for Merge Articles](../../relational-databases/replication/publish/specify-merge-replication-properties.md#interactive-conflict-resolution).</span></span>
  
2.  <span data-ttu-id="54caa-147">在 Synchronization Manager 中開始同步處理訂閱之後，如果啟用了互動式衝突解決方案，且一個或多個發行項有衝突，則「互動解決器」會自動啟動。</span><span class="sxs-lookup"><span data-stu-id="54caa-147">After the subscription begins synchronizing in Synchronization Manager, the Interactive Resolver launches automatically if interactive conflict resolution is enabled and there are conflicts for one or more articles.</span></span> <span data-ttu-id="54caa-148">「互動解決器」每次顯示一個衝突，並為每個衝突提供一個建議的解決方案 (視建立發行集和訂閱時指定的解決器而定)。</span><span class="sxs-lookup"><span data-stu-id="54caa-148">The Interactive Resolver displays conflicts one at a time, with a suggested resolution for each conflict (based on the resolver specified when the publication and subscription were created).</span></span>  
  
3.  <span data-ttu-id="54caa-149">選擇性地編輯任何在「互動解決器」中顯示的資料行，然後按下列其中一個按鈕，以解決衝突：</span><span class="sxs-lookup"><span data-stu-id="54caa-149">Optionally edit any of the columns displayed in the Interactive Resolver, and then click one of the following buttons to resolve the conflict:</span></span>  
  
    -   <span data-ttu-id="54caa-150">**[接受建議]**</span><span class="sxs-lookup"><span data-stu-id="54caa-150">**Accept Suggested**</span></span>  
  
    -   <span data-ttu-id="54caa-151">**[接受發行者]**</span><span class="sxs-lookup"><span data-stu-id="54caa-151">**Accept Publisher**</span></span>  
  
    -   <span data-ttu-id="54caa-152">**[接受訂閱者]**</span><span class="sxs-lookup"><span data-stu-id="54caa-152">**Accept Subscriber**</span></span>  
  
    -   <span data-ttu-id="54caa-153">**[自動解決所有衝突]** (會解決目前所有的衝突，而無需進一步的輸入)</span><span class="sxs-lookup"><span data-stu-id="54caa-153">**Resolve All Automatically** (all current conflicts are resolved without further input)</span></span>  
  
     <span data-ttu-id="54caa-154">選取的資料列然後會被套用到「發行者」和 (或)「訂閱者」；在後續同步處理期間，它會傳播到其他節點。</span><span class="sxs-lookup"><span data-stu-id="54caa-154">The selected row is then applied to the Publisher and/or Subscriber; it is propagated to other nodes in the topology during subsequent synchronizations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="54caa-155">僅當編輯為針對解決方案所選取之資料列的一部分時，才會被套用。</span><span class="sxs-lookup"><span data-stu-id="54caa-155">Edits are only applied if they are part of the row that is chosen for resolution.</span></span> <span data-ttu-id="54caa-156">例如，如果您在 **[發行者]** 下進行了編輯，然後按一下 **[接受訂閱者]** ，則編輯會被捨棄。</span><span class="sxs-lookup"><span data-stu-id="54caa-156">For example, if you make edits under **Publisher**, and then click **Accept Subscriber**, the edits are discarded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54caa-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54caa-157">See Also</span></span>  
 [<span data-ttu-id="54caa-158">Interactive Conflict Resolution</span><span class="sxs-lookup"><span data-stu-id="54caa-158">Interactive Conflict Resolution</span></span>](merge/advanced-merge-replication-conflict-interactive-resolution.md)  
  
