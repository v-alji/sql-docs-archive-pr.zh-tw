---
title: 建立交易式發行集的可更新訂閱 (Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 07/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- updateable transactional subscriptions
- updateable transactional subscriptions, SSMS
ms.assetid: f9ef89ed-36f6-431b-8843-25d445ec137f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e784216116bdb9ab308dff5fa998740b0fa459b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709149"
---
# <a name="create-an-updatable-subscription-to-a-transactional-publication-management-studio"></a><span data-ttu-id="c5aa0-102">建立交易式發行集的可更新訂閱 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="c5aa0-102">Create an Updatable Subscription to a Transactional Publication (Management Studio)</span></span>

> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
 
<span data-ttu-id="c5aa0-103">異動複寫可使用立即或佇列更新訂閱，讓訂閱者上所做的變更傳播回到發行者。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-103">Transactional replication enables changes made at a Subscriber to be propagated back to the Publisher using either immediate or queued updating subscriptions.</span></span> <span data-ttu-id="c5aa0-104">您可以使用複寫預存程序以程式設計的方式建立更新訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-104">You can create an updating subscription programmatically using replication stored procedures.</span></span>

<span data-ttu-id="c5aa0-105">在 [新增訂閱精靈] 的 [可更新訂閱] 頁面上設定可更新訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-105">Configure updatable subscriptions on the **Updatable Subscriptions** page of the **New Subscription Wizard**.</span></span> <span data-ttu-id="c5aa0-106">此頁面僅在為可更新訂閱啟用了交易式發行集之後才可用。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-106">This page is only available if you have enabled a transactional publication for updatable subscriptions.</span></span> <span data-ttu-id="c5aa0-107">如需啟用可更新訂閱的詳細資訊，請參閱[啟用交易式發行集的可更新訂閱](enable-updating-subscriptions-for-transactional-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-107">For more information about enabling updatable subscriptions, see [Enable Updating Subscriptions for Transactional Publications](enable-updating-subscriptions-for-transactional-publications.md).</span></span>   
  
## <a name="configure-an-updatable-subscription-from-the-publisher"></a><span data-ttu-id="c5aa0-108">從發行者設定可更新訂閱</span><span class="sxs-lookup"><span data-stu-id="c5aa0-108">Configure an updatable subscription from the Publisher</span></span>  

1. <span data-ttu-id="c5aa0-109">連線到 Microsoft SQL Server Management Studio 中的發行者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-109">Connect to the Publisher in Microsoft SQL Server Management Studio, and then expand the server node.</span></span>
2. <span data-ttu-id="c5aa0-110">展開 **[複寫]** 資料夾，然後展開 **[本機發行集]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-110">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>
3. <span data-ttu-id="c5aa0-111">以滑鼠右鍵按一下為更新訂閱啟用的交易式發行集，然後按一下 [新增訂閱]。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-111">Right-click a transactional publication enabled for updating subscriptions, and then click **New Subscriptions**.</span></span>
4. <span data-ttu-id="c5aa0-112">遵循精靈中的頁面來指定訂閱的選項，例如散發代理程式應在何處執行。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-112">Follow pages in the wizard to specify options for the subscription, such as where the Distribution Agent should run.</span></span>
5. <span data-ttu-id="c5aa0-113">在 [新增訂閱精靈] 的 [可更新的訂閱] 頁面上，確定已選取 [複寫]。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-113">On the **Updatable Subscriptions** page of the **New Subscription Wizard**, ensure **Replicate** is selected.</span></span>
6. <span data-ttu-id="c5aa0-114">從 [在發行者端認可] 下拉式清單中選取一個選項：</span><span class="sxs-lookup"><span data-stu-id="c5aa0-114">Select an option from the **Commit at Publisher** drop-down list:</span></span>

    *  <span data-ttu-id="c5aa0-115">若要使用立即更新訂閱，請選取 [同時認可變更]。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-115">To use immediate updating subscriptions, select **Simultaneously commit changes**.</span></span> <span data-ttu-id="c5aa0-116">如果您選取這個選項，而且發行集允許佇列更新訂閱 (使用 [新增發行集精靈] 所建立之發行集的預設值)，訂閱屬性 **update_mode** 會設定為 **failover**。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-116">If you select this option, and the publication allows queued updating subscriptions (the default for publications created with the New Publication Wizard), the subscription property **update_mode** is set to **failover**.</span></span> <span data-ttu-id="c5aa0-117">如有必要，這個模式允許您以後可切換至佇列更新。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-117">This mode allows you to switch to queued updating later if necessary.</span></span>
    *  <span data-ttu-id="c5aa0-118">若要使用佇列更新訂閱，請選取 [佇列變更且盡可能認可]。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-118">To use queued updating subscriptions, select **Queue changes and commit when possible**.</span></span> <span data-ttu-id="c5aa0-119">如果您選取這個選項，而發行集允許立即更新訂閱 (使用 [新增發行集精靈] 建立之發行集的預設值)，而且訂閱者執行的是 SQL Server 2005 或更新版本，則訂閱屬性 **update_mode** 會設定為 queued failover。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-119">If you select this option, and the publication allows immediate updating subscriptions (the default for publications created with the New Publication Wizard), and the Subscriber is running SQL Server 2005 or a later version, the subscription property **update_mode** is set to queued failover.</span></span> <span data-ttu-id="c5aa0-120">如有必要，這個模式允許您以後可切換至立即更新。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-120">This mode allows you to switch to immediate updating later if necessary.</span></span>

    <span data-ttu-id="c5aa0-121">如需切換更新模式的資訊，請參閱[切換可更新之交易式訂閱的更新模式](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-121">For information about switching update modes, see [Switch Between Update Modes for an Updatable Transactional Subscription](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).</span></span>

7. <span data-ttu-id="c5aa0-122">針對使用立即更新或將 **update_mode** 設定為 **queued failover**，會顯示 [可更新訂閱的登入] 頁面。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-122">The **Login for Updatable Subscriptions** page is displayed for subscriptions that use immediate updating or have **update_mode** set to **queued failover**.</span></span> <span data-ttu-id="c5aa0-123">在 [可更新訂閱的登入] 頁面上，指定連線到發行者之連結的伺服器，以立即更新訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-123">On the **Login for Updatable Subscriptions** page, specify a linked server over which connections to the Publisher are made for immediate updating subscriptions.</span></span> <span data-ttu-id="c5aa0-124">在訂閱者端引發的觸發程序，會使用這些連接將變更傳播至發行者。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-124">Connections are used by the triggers that fire at the Subscriber and propagate changes to the Publisher.</span></span> <span data-ttu-id="c5aa0-125">選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="c5aa0-125">Select one of the following options:</span></span>

    * <span data-ttu-id="c5aa0-126">**建立使用 SQL Server 驗證來連線的連結伺服器。**</span><span class="sxs-lookup"><span data-stu-id="c5aa0-126">**Create a linked server that connects using SQL Server Authentication.**</span></span> <span data-ttu-id="c5aa0-127">若您已透過尚未定義遠端伺服器或訂閱者與發行者之間連結的伺服器，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-127">Select this option if you have not defined a remote server or linked server between the Subscriber and the Publisher.</span></span> <span data-ttu-id="c5aa0-128">複寫會為您建立連結伺服器。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-128">Replication creates a linked server for you.</span></span> <span data-ttu-id="c5aa0-129">您必須指定已存在於發行者的帳戶。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-129">The account you specify must already exist at the Publisher.</span></span>
    * <span data-ttu-id="c5aa0-130">**使用您已定義的連結伺服器或遠端伺服器。**</span><span class="sxs-lookup"><span data-stu-id="c5aa0-130">**Use a linked server or remote server that you have already defined.**</span></span> <span data-ttu-id="c5aa0-131">若您已透過 [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql)、[sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)、SQL Server Management Studio 或其他方法定義遠端伺服器或訂閱者與發行者之間連結的伺服器，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-131">Select this option if you have defined a remote server or linked server between the Subscriber and the Publisher using [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql), SQL Server Management Studio, or another method.</span></span>

    <span data-ttu-id="c5aa0-132">如需連結伺服器帳戶所需權限的資訊，請參閱[在這裡輸入連結描述](../security/secure-the-subscriber.md)的**佇列更新訂閱**。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-132">For information about the permissions required by the linked server account, see the **Queued Updating Subscriptions** of [enter link description here](../security/secure-the-subscriber.md).</span></span>

8. <span data-ttu-id="c5aa0-133">完成精靈。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-133">Complete the wizard.</span></span>

## <a name="configure-an-updatable-subscription-from-the-subscriber"></a><span data-ttu-id="c5aa0-134">從訂閱者設定可更新訂閱</span><span class="sxs-lookup"><span data-stu-id="c5aa0-134">Configure an updatable subscription from the Subscriber</span></span>


1. <span data-ttu-id="c5aa0-135">連線到 SQL Server Management Studio 中的訂閱者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-135">Connect to the Subscriber in SQL Server Management Studio, and then expand the server node.</span></span>
2. <span data-ttu-id="c5aa0-136">展開 **[複寫]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-136">Expand the **Replication** folder.</span></span>
3. <span data-ttu-id="c5aa0-137">以滑鼠右鍵按一下 **[區域訂閱]** 資料夾，然後按一下 **[新增訂閱]** 。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-137">Right-click the **Local Subscriptions** folder, and then click **New Subscriptions**.</span></span>
4. <span data-ttu-id="c5aa0-138">在 [新增訂閱精靈] 的 [發行集] 頁面上，從 [發行者] 下拉式清單中選取 [<尋找 SQL Server 發行者>]。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-138">On the **Publication** page of the **New Subscription Wizard**, select **Find SQL Server Publisher** from the **Publisher** drop-down list.</span></span>
5. <span data-ttu-id="c5aa0-139">連接到 **[連接到伺服器]** 對話方塊中的發行者。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-139">Connect to the Publisher in the **Connect to Server** dialog box.</span></span>
6. <span data-ttu-id="c5aa0-140">在 [發行集] 頁面上選取為更新訂閱啟用的交易式發行集。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-140">Select a transactional publication enabled for updating subscriptions on the **Publication** page.</span></span>
7. <span data-ttu-id="c5aa0-141">遵循精靈中的頁面來指定訂閱的選項，例如散發代理程式應在何處執行。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-141">Follow pages in the wizard to specify options for the subscription, such as where the Distribution Agent should run.</span></span>
8. <span data-ttu-id="c5aa0-142">在 [新增訂閱精靈] 的 [可更新的訂閱] 頁面上，確定已選取 [複寫]。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-142">On the **Updatable Subscriptions** page of the New Subscription Wizard, ensure **Replicate** is selected.</span></span>
9. <span data-ttu-id="c5aa0-143">從 [在發行者端認可] 下拉式清單中選取一個選項：</span><span class="sxs-lookup"><span data-stu-id="c5aa0-143">Select an option from the **Commit at Publisher** drop-down list:</span></span>

    * <span data-ttu-id="c5aa0-144">若要使用立即更新訂閱，請選取 [同時認可變更]。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-144">To use immediate updating subscriptions, select **Simultaneously commit changes**.</span></span> <span data-ttu-id="c5aa0-145">如果您選取這個選項，而且發行集允許佇列更新訂閱 (使用 [新增發行集精靈] 所建立之發行集的預設值)，訂閱屬性 **update_mode** 會設定為 **failover**。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-145">If you select this option, and the publication allows queued updating subscriptions (the default for publications created with the New Publication Wizard), the subscription property **update_mode** is set to **failover**.</span></span> <span data-ttu-id="c5aa0-146">如有必要，這個模式允許您以後可切換至佇列更新。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-146">This mode allows you to switch to queued updating later if necessary.</span></span>
    * <span data-ttu-id="c5aa0-147">若要使用佇列更新訂閱，請選取 [佇列變更且盡可能認可]。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-147">To use queued updating subscriptions, select **Queue changes and commit when possible**.</span></span> <span data-ttu-id="c5aa0-148">如果您選取這個選項，而發行集允許立即更新訂閱 (使用 [新增發行集精靈] 建立之發行集的預設值)，而且訂閱者執行的是 SQL Server 2005 或更新版本，則訂閱屬性 **update_mode** 會設定為 **queued failover**。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-148">If you select this option, and the publication allows immediate updating subscriptions (the default for publications created with the New Publication Wizard), and the Subscriber is running SQL Server 2005 or a later version, the subscription property **update_mode** is set to queued **failover**.</span></span> <span data-ttu-id="c5aa0-149">如有必要，這個模式允許您以後可切換至立即更新。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-149">This mode allows you to switch to immediate updating later if necessary.</span></span>

    <span data-ttu-id="c5aa0-150">如需切換更新模式的資訊，請參閱[切換可更新之交易式訂閱的更新模式](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-150">For information about switching update modes, see [Switch Between Update Modes for an Updatable Transactional Subscription](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).</span></span>

10. <span data-ttu-id="c5aa0-151">針對使用立即更新或將 **update_mode** 設定為 **queued failover**，會顯示 [可更新訂閱的登入] 頁面。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-151">The **Login for Updatable Subscriptions** page is displayed for subscriptions that use immediate updating or have **update_mode** set to queued **failover**.</span></span> <span data-ttu-id="c5aa0-152">在 [可更新訂閱的登入] 頁面上，指定連線到發行者之連結的伺服器，以立即更新訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-152">On the **Login for Updatable Subscriptions** page, specify a linked server over which connections to the Publisher are made for immediate updating subscriptions.</span></span> <span data-ttu-id="c5aa0-153">在訂閱者端引發的觸發程序，會使用這些連接將變更傳播至發行者。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-153">Connections are used by the triggers that fire at the Subscriber and propagate changes to the Publisher.</span></span> <span data-ttu-id="c5aa0-154">選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="c5aa0-154">Select one of the following options:</span></span>

    * <span data-ttu-id="c5aa0-155">**建立使用 SQL Server 驗證來連線的連結伺服器。**</span><span class="sxs-lookup"><span data-stu-id="c5aa0-155">**Create a linked server that connects using SQL Server Authentication.**</span></span> <span data-ttu-id="c5aa0-156">若您已透過尚未定義遠端伺服器或訂閱者與發行者之間連結的伺服器，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-156">Select this option if you have not defined a remote server or linked server between the Subscriber and the Publisher.</span></span> <span data-ttu-id="c5aa0-157">複寫會為您建立連結伺服器。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-157">Replication creates a linked server for you.</span></span> <span data-ttu-id="c5aa0-158">您必須指定已存在於發行者的帳戶。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-158">The account you specify must already exist at the Publisher.</span></span>
    * <span data-ttu-id="c5aa0-159">**使用您已定義的連結伺服器或遠端伺服器。**</span><span class="sxs-lookup"><span data-stu-id="c5aa0-159">**Use a linked server or remote server that you have already defined.**</span></span> <span data-ttu-id="c5aa0-160">若您已透過 [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql)、[sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)、SQL Server Management Studio 或其他方法定義遠端伺服器或訂閱者與發行者之間連結的伺服器，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-160">Select this option if you have defined a remote server or linked server between the Subscriber and the Publisher using [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql), SQL Server Management Studio, or another method.</span></span>

    <span data-ttu-id="c5aa0-161">如需連結伺服器帳戶所需權限的資訊，請參閱[在這裡輸入連結描述](../security/secure-the-subscriber.md)的**佇列更新訂閱**。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-161">For information about the permissions required by the linked server account, see the **Queued Updating Subscriptions** of [enter link description here](../security/secure-the-subscriber.md).</span></span>

11. <span data-ttu-id="c5aa0-162">完成精靈。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-162">Complete the wizard.</span></span>

## <a name="create-an-immediate-updating-pull-subscription"></a><span data-ttu-id="c5aa0-163">建立立即更新提取訂閱</span><span class="sxs-lookup"><span data-stu-id="c5aa0-163">Create an immediate updating pull subscription</span></span>

1. <span data-ttu-id="c5aa0-164">在發行者上，執行 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)來確認發行集可支援立即更新訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-164">At the Publisher, verify that the publication supports immediate updating subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="c5aa0-165">如果結果集中 `allow_sync_tran` 的值為 `1`，則表示發行集可支援立即更新訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-165">If the value of `allow_sync_tran` in the result set is `1`, the publication supports immediate updating subscriptions.</span></span>
    * <span data-ttu-id="c5aa0-166">如果結果集中 `allow_sync_tran` 的值為 `0`，則表示必須在啟用立即更新訂閱的情況下重新建立發行集。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-166">If the value of `allow_sync_tran` in the result set is `0`, the publication must be recreated with immediate updating subscriptions enabled.</span></span>

2. <span data-ttu-id="c5aa0-167">在發行者上，執行 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)來確認發行集可支援提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-167">At the Publisher, verify that the publication supports pull subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="c5aa0-168">如果結果集中 `allow_pull` 的值為 `1`，則表示發行集可支援提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-168">If the value of `allow_pull` in the result set is `1`, the publication supports pull subscriptions.</span></span>
    * <span data-ttu-id="c5aa0-169">如果 `allow_pull` 的值是 `0`，請執行 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)，並針對 `allow_pull` 指定 `@property` 、針對 `true` 指定 `@value`。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-169">If the value of `allow_pull` is `0`, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying `allow_pull` for `@property` and `true` for `@value`.</span></span> 

3. <span data-ttu-id="c5aa0-170">在訂閱者上，執行 [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-170">At the Subscriber, execute [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql).</span></span> <span data-ttu-id="c5aa0-171">指定 `@publisher` 和 `@publication`，並對 `@update_mode`指定下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="c5aa0-171">Specify `@publisher` and `@publication`, and one of the following values for `@update_mode`:</span></span>

    * <span data-ttu-id="c5aa0-172">`sync tran` - 啟用立即更新的訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-172">`sync tran` - enables the subscription for immediate updating.</span></span>
    * <span data-ttu-id="c5aa0-173">`failover` - 啟用立即更新的訂閱，且利用佇列更新來做為容錯移轉選項。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-173">`failover` - enables the subscription for immediate updating with queued updating as a failover option.</span></span>

    > [!NOTE]  
>  <span data-ttu-id="c5aa0-174">`failover` - 要求也要針對佇列更新訂閱啟用發行集。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-174">`failover` requires that the publication also be enabled for queued updating subscriptions.</span></span> 
 
4. <span data-ttu-id="c5aa0-175">在訂閱者上，執行 [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-175">At the Subscriber, execute [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql).</span></span> <span data-ttu-id="c5aa0-176">指定下列項目：</span><span class="sxs-lookup"><span data-stu-id="c5aa0-176">Specify the following:</span></span>

    * <span data-ttu-id="c5aa0-177">`@publisher`、 `@publisher_db`和 `@publication` 參數。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-177">The `@publisher`, `@publisher_db`, and `@publication` parameters.</span></span> 
    * <span data-ttu-id="c5aa0-178">Microsoft Windows 認證，「訂閱者」上的「散發代理程式」執行時會針對 `@job_login` 和 `@job_password`使用該認證。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-178">The Microsoft Windows credentials under which the Distribution Agent at the Subscriber runs for `@job_login` and `@job_password`.</span></span> 

    > [!NOTE]  
>  <span data-ttu-id="c5aa0-179">使用「Windows 整合式驗證」建立的連接一律使用由 `@job_login` 和 `@job_password`指定的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-179">Connections made using Windows Integrated Authentication are always made using the Windows credentials specified by `@job_login` and `@job_password`.</span></span> <span data-ttu-id="c5aa0-180">散發代理程式一律使用「Windows 整合式驗證」建立與訂閱者的本機連接。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-180">The Distribution Agent always makes the local connection to the Subscriber using Windows Integrated Authentication.</span></span> <span data-ttu-id="c5aa0-181">依預設，代理程式會使用「Windows 整合式驗證」連接到散發者。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-181">By default, the agent connects to the Distributor using Windows Integrated Authentication.</span></span> 
 
    * <span data-ttu-id="c5aa0-182">(選擇性) `0` 的 `@distributor_security_mode` 值和 `@distributor_login` 和 `@distributor_password`的 Microsoft SQL Server 登入資訊，如果您需要在連接到散發者時使用 SQL Server 驗證的話。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-182">(Optional) A value of `0` for `@distributor_security_mode` and the Microsoft SQL Server login information for `@distributor_login` and `@distributor_password`, if you need to use SQL Server Authentication when connecting to the Distributor.</span></span> 
    * <span data-ttu-id="c5aa0-183">此訂閱之散發代理程式作業的排程。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-183">A schedule for the Distribution Agent job for this subscription.</span></span> 

5. <span data-ttu-id="c5aa0-184">在訂閱資料庫的訂閱者上，執行 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-184">At the Subscriber on the subscription database, execute [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql).</span></span> <span data-ttu-id="c5aa0-185">指定 `@publisher`、 `@publication`、 `@publisher_db`的發行集資料庫名稱，和 `@security_mode`的下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="c5aa0-185">Specify `@publisher`, `@publication`, the name of the publication database for `@publisher_db`, and one of the following values for `@security_mode`:</span></span> 

    * <span data-ttu-id="c5aa0-186">`0` - 在發行者上進行更新時使用「SQL Server 驗證」。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-186">`0` - Use SQL Server Authentication when making updates at the Publisher.</span></span> <span data-ttu-id="c5aa0-187">此選項要求您在發行者上針對 `@login` 和 `@password`指定有效的登入。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-187">This option requires you to specify a valid login at the Publisher for `@login` and `@password`.</span></span>
    * <span data-ttu-id="c5aa0-188">`1` - 在連接到發行者時，使用在訂閱者上進行變更之使用者的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-188">`1` - Use the security context of the user making changes at the Subscriber when connecting to the Publisher.</span></span> <span data-ttu-id="c5aa0-189">如需與此安全性模式有關的限制，請參閱 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-189">See [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) for restrictions related to this security mode.</span></span>
    * <span data-ttu-id="c5aa0-190">`2` - 使用透過 [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)所建立之現有使用者定義的連結伺服器登入。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-190">`2` - Use an existing, user-defined linked server login created using [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span>

6. <span data-ttu-id="c5aa0-191">在發行者上，執行 [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) ，並指定 `@publication`、 `@subscriber`、 `@destination_db`、 `@subscription_type`的提取值，以及針對 `@update_mode`指定在步驟 3 中指定的相同值。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-191">At the publisher, execute [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) specifying `@publication`, `@subscriber`, `@destination_db`, a value of pull for `@subscription_type`, and the same value specified in step 3 for `@update_mode`.</span></span>

<span data-ttu-id="c5aa0-192">這樣會在發行者上註冊提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-192">This registers the pull subscription at the Publisher.</span></span> 


## <a name="create-an-immediate-updating-push-subscription"></a><span data-ttu-id="c5aa0-193">建立立即更新發送訂閱</span><span class="sxs-lookup"><span data-stu-id="c5aa0-193">Create an immediate updating push subscription</span></span> 

1. <span data-ttu-id="c5aa0-194">在發行者上，執行 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)來確認發行集可支援立即更新訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-194">At the Publisher, verify that the publication supports immediate updating subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="c5aa0-195">如果結果集中 `allow_sync_tran` 的值為 `1`，則表示發行集可支援立即更新訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-195">If the value of `allow_sync_tran` in the result set is `1`, the publication supports immediate updating subscriptions.</span></span>
    * <span data-ttu-id="c5aa0-196">如果結果集中 `allow_sync_tran` 的值為 `0`，則表示必須在啟用立即更新訂閱的情況下重新建立發行集。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-196">If the value of `allow_sync_tran` in the result set is `0`, the publication must be recreated with immediate updating subscriptions enabled.</span></span>

2. <span data-ttu-id="c5aa0-197">在發行者上，執行 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)來確認發行集可支援發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-197">At the Publisher, verify that the publication supports push subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="c5aa0-198">如果結果集中 `allow_push` 的值為 `1`，則表示發行集可支援發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-198">If the value of `allow_push` in the result set is `1`, the publication supports push subscriptions.</span></span>
    * <span data-ttu-id="c5aa0-199">如果 `allow_push` 的值是 `0`，請執行 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)，並針對 `allow_push` 指定 `@property` 、針對 `true` 指定 `@value`。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-199">If the value of `allow_push` is `0`, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying `allow_push` for `@property` and `true` for `@value`.</span></span> 

3. <span data-ttu-id="c5aa0-200">在發行者上，執行 [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-200">At the Publisher, execute [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).</span></span> <span data-ttu-id="c5aa0-201">指定 `@publication`、 `@subscriber`、 `@destination_db`，並對 `@update_mode`指定下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="c5aa0-201">Specify `@publication`, `@subscriber`, `@destination_db`, and one of the following values for `@update_mode`:</span></span>

    * <span data-ttu-id="c5aa0-202">`sync tran` - 啟用立即更新的支援。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-202">`sync tran` - enables support for immediate updating.</span></span>
    * <span data-ttu-id="c5aa0-203">`failover` - 啟用立即更新的支援，並將佇列更新當做容錯移轉選項。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-203">`failover` - enables support for immediate updating with queued updating as a failover option.</span></span>

    > [!NOTE]  
>  <span data-ttu-id="c5aa0-204">`failover` - 要求也要針對佇列更新訂閱啟用發行集。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-204">`failover` requires that the publication also be enabled for queued updating subscriptions.</span></span> 
 
4. <span data-ttu-id="c5aa0-205">在發行者上，執行 [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-205">At the Publisher, execute [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql).</span></span> <span data-ttu-id="c5aa0-206">指定下列參數：</span><span class="sxs-lookup"><span data-stu-id="c5aa0-206">Specify the following parameters:</span></span>

    * <span data-ttu-id="c5aa0-207">`@subscriber``@subscriber_db`和 `@publication`。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-207">`@subscriber`, `@subscriber_db`, and `@publication`.</span></span> 
    * <span data-ttu-id="c5aa0-208">散發代理程式在散發者上執行時，針對 `@job_login` 和 `@job_password`所使用的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-208">The Windows credentials under which the Distribution Agent at the Distributor runs for `@job_login` and `@job_password`.</span></span> 

    > [!NOTE]  
>  <span data-ttu-id="c5aa0-209">使用「Windows 整合式驗證」建立的連接一律使用由 `@job_login` 和 `@job_password`指定的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-209">Connections made using Windows Integrated Authentication are always made using the Windows credentials specified by `@job_login` and `@job_password`.</span></span> <span data-ttu-id="c5aa0-210">散發代理程式一律使用「Windows 整合式驗證」建立與散發者的本機連接。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-210">The Distribution Agent always makes the local connection to the Distributor using Windows Integrated Authentication.</span></span> <span data-ttu-id="c5aa0-211">依預設，代理程式會使用「Windows 整合式驗證」連接到訂閱者。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-211">By default, the agent will connect to the Subscriber using Windows Integrated Authentication.</span></span> 

    * <span data-ttu-id="c5aa0-212">(選擇性) `0` 的 `@subscriber_security_mode` 值和 `@subscriber_login` 和 `@subscriber_password`的 SQL Server 登入資訊，如果您需要在連接到訂閱者時使用 SQL Server 驗證的話。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-212">(Optional) A value of `0` for `@subscriber_security_mode` and the SQL Server login information for `@subscriber_login` and `@subscriber_password`, if you need to use SQL Server Authentication when connecting to the Subscriber.</span></span> 
    * <span data-ttu-id="c5aa0-213">此訂閱之散發代理程式作業的排程。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-213">A schedule for the Distribution Agent job for this subscription.</span></span>

5. <span data-ttu-id="c5aa0-214">在訂閱資料庫的訂閱者上，執行 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-214">At the Subscriber on the subscription database, execute [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql).</span></span> <span data-ttu-id="c5aa0-215">指定 `@publisher`、 `@publication`、 `@publisher_db`的發行集資料庫名稱，和 `@security_mode`的下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="c5aa0-215">Specify `@publisher`, `@publication`, the name of the publication database for `@publisher_db`, and one of the following values for `@security_mode`:</span></span> 

     * <span data-ttu-id="c5aa0-216">`0` - 在發行者上進行更新時使用「SQL Server 驗證」。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-216">`0` - Use SQL Server Authentication when making updates at the Publisher.</span></span> <span data-ttu-id="c5aa0-217">此選項要求您在發行者上針對 `@login` 和 `@password`指定有效的登入。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-217">This option requires you to specify a valid login at the Publisher for `@login` and `@password`.</span></span>
     * <span data-ttu-id="c5aa0-218">`1` - 在連接到發行者時，使用在訂閱者上進行變更之使用者的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-218">`1` - Use the security context of the user making changes at the Subscriber when connecting to the Publisher.</span></span> <span data-ttu-id="c5aa0-219">如需與此安全性模式有關的限制，請參閱 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-219">See [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) for restrictions related to this security mode.</span></span>
     * <span data-ttu-id="c5aa0-220">`2` - 使用透過 [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)所建立之現有使用者定義的連結伺服器登入。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-220">`2` - Use an existing, user-defined linked server login created using [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span>


## <a name="create-a-queued-updating-pull-subscription"></a><span data-ttu-id="c5aa0-221">建立佇列更新提取訂閱</span><span class="sxs-lookup"><span data-stu-id="c5aa0-221">Create a queued updating pull subscription</span></span> ##

1. <span data-ttu-id="c5aa0-222">在發行者上，執行 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)來確認發行集可支援佇列更新訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-222">At the Publisher, verify that the publication supports queued updating subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="c5aa0-223">如果結果集中 `allow_queued_tran` 的值為 `1`，則表示發行集可支援立即更新訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-223">If the value of `allow_queued_tran` in the result set is `1`, the publication supports immediate updating subscriptions.</span></span>
    * <span data-ttu-id="c5aa0-224">如果結果集中 `allow_queued_tran` 的值為 `0`，則表示必須在啟用佇列更新訂閱的情況下重新建立發行集。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-224">If the value of `allow_queued_tran` in the result set is `0`, the publication must be recreated with queued updating subscriptions enabled.</span></span>

2. <span data-ttu-id="c5aa0-225">在發行者上，執行 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)來確認發行集可支援提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-225">At the Publisher, verify that the publication supports pull subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="c5aa0-226">如果結果集中 `allow_pull` 的值為 `1`，則表示發行集可支援提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-226">If the value of `allow_pull` in the result set is `1`, the publication supports pull subscriptions.</span></span>
    * <span data-ttu-id="c5aa0-227">如果 `allow_pull` 的值是 `0`，請執行 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)，並針對 `allow_pull` 指定 `@property` 、針對 `true` 指定 `@value`。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-227">If the value of `allow_pull` is `0`, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying `allow_pull` for `@property` and `true` for `@value`.</span></span> 

3. <span data-ttu-id="c5aa0-228">在訂閱者上，執行 [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-228">At the Subscriber, execute [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql).</span></span> <span data-ttu-id="c5aa0-229">指定 `@publisher` 和 `@publication`，並對 `@update_mode`指定下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="c5aa0-229">Specify `@publisher` and `@publication`, and one of the following values for `@update_mode`:</span></span>

    * <span data-ttu-id="c5aa0-230">`queued tran` - 啟用佇列更新的訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-230">`queued tran` - enables the subscription for queued updating.</span></span>
    * <span data-ttu-id="c5aa0-231">`queued failover` - 啟用佇列更新的支援，並將立即更新當作容錯移轉選項。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-231">`queued failover` - enables support for queued updating with immediate updating as a failover option.</span></span>

    > [!NOTE]  
>  <span data-ttu-id="c5aa0-232">`queued failover` - 要求也要針對立即更新訂閱啟用發行集。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-232">`queued failover` requires that the publication also be enabled for immediate updating subscriptions.</span></span> <span data-ttu-id="c5aa0-233">若要容錯移轉到立即更新，您必須使用 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) ，以定義訂閱者上的變更複寫到發行者時所用的認證。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-233">To fail over to immediate updating, you must use [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) to define the credentials under which changes at the Subscriber are replicated to the Publisher.</span></span>
 
4. <span data-ttu-id="c5aa0-234">在訂閱者上，執行 [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-234">At the Subscriber, execute [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql).</span></span> <span data-ttu-id="c5aa0-235">指定下列參數：</span><span class="sxs-lookup"><span data-stu-id="c5aa0-235">Specify the following parameters:</span></span>

    * <span data-ttu-id="c5aa0-236">@publisher`@publisher_db`和 `@publication`。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-236">@publisher, `@publisher_db`, and `@publication`.</span></span> 
    * <span data-ttu-id="c5aa0-237">Windows 認證，「訂閱者」上的「散發代理程式」執行時會針對 `@job_login` 和 `@job_password`使用該認證。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-237">The Windows credentials under which the Distribution Agent at the Subscriber runs for `@job_login` and `@job_password`.</span></span> 

    > [!NOTE]  
>  <span data-ttu-id="c5aa0-238">使用「Windows 整合式驗證」建立的連接一律使用由 `@job_login` 和 `@job_password`指定的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-238">Connections made using Windows Integrated Authentication are always made using the Windows credentials specified by `@job_login` and `@job_password`.</span></span> <span data-ttu-id="c5aa0-239">散發代理程式一律使用「Windows 整合式驗證」建立與訂閱者的本機連接。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-239">The Distribution Agent always makes the local connection to the Subscriber using Windows Integrated Authentication.</span></span> <span data-ttu-id="c5aa0-240">依預設，代理程式會使用「Windows 整合式驗證」連接到散發者。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-240">By default, the agent connects to the Distributor using Windows Integrated Authentication.</span></span> 
 
    * <span data-ttu-id="c5aa0-241">(選擇性) `0` 的 `@distributor_security_mode` 值和 `@distributor_login` 和 `@distributor_password`的 SQL Server 登入資訊，如果您需要在連接到散發者時使用 SQL Server 驗證的話。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-241">(Optional) A value of `0` for `@distributor_security_mode` and the SQL Server login information for `@distributor_login` and `@distributor_password`, if you need to use SQL Server Authentication when connecting to the Distributor.</span></span> 
    * <span data-ttu-id="c5aa0-242">此訂閱之散發代理程式作業的排程。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-242">A schedule for the Distribution Agent job for this subscription.</span></span>

5. <span data-ttu-id="c5aa0-243">在發行者上，執行 [sp_addsubscriber](/sql/relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql) ，在發行者註冊訂閱者，並指定 `@publication`、 `@subscriber`、 `@destination_db`、 `@subscription_type`的提取值，以及針對 `@update_mode`指定在步驟 3 中指定的相同值。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-243">At the publisher, execute [sp_addsubscriber](/sql/relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql) to register the Subscriber at the Publisher, specifying `@publication`, `@subscriber`, `@destination_db`, a value of pull for `@subscription_type`, and the same value specified in step 3 for `@update_mode`.</span></span>

<span data-ttu-id="c5aa0-244">這樣會在發行者上註冊提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-244">This registers the pull subscription at the Publisher.</span></span> 


## <a name="to-create-a-queued-updating-push-subscription"></a><span data-ttu-id="c5aa0-245">建立佇列更新發送訂閱</span><span class="sxs-lookup"><span data-stu-id="c5aa0-245">To create a queued updating push subscription</span></span> ##

1. <span data-ttu-id="c5aa0-246">在發行者上，執行 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)來確認發行集可支援佇列更新訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-246">At the Publisher, verify that the publication supports queued updating subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="c5aa0-247">如果結果集中 allow_queued_tran 的值為 1，則表示發行集可支援立即更新訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-247">If the value of allow_queued_tran in the result set is 1, the publication supports immediate updating subscriptions.</span></span>
    * <span data-ttu-id="c5aa0-248">如果結果集中 allow_queued_tran 的值為 0，則表示必須在啟用佇列更新訂閱的情況下重新建立發行集。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-248">If the value of allow_queued_tran in the result set is 0, the publication must be recreated with queued updating subscriptions enabled.</span></span> <span data-ttu-id="c5aa0-249">如需詳細資訊，請參閱＜如何：啟用交易式發行集的可更新訂閱 (複寫 Transact-SQL 程式設計)＞。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-249">For more information, see How to: Enable Updating Subscriptions for Transactional Publications (Replication Transact-SQL Programming).</span></span>

2. <span data-ttu-id="c5aa0-250">在發行者上，執行 [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)來確認發行集可支援發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-250">At the Publisher, verify that the publication supports push subscriptions by executing [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql).</span></span> 

    * <span data-ttu-id="c5aa0-251">如果結果集中 `allow_push` 的值為 `1`，則表示發行集可支援發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-251">If the value of `allow_push` in the result set is `1`, the publication supports push subscriptions.</span></span>
    * <span data-ttu-id="c5aa0-252">如果 `allow_push` 的值是 `0`，請執行 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)，並針對 `@property` 指定 allow_push、針對 `true` 指定 `@value`。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-252">If the value of `allow_push` is `0`, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specifying allow_push for `@property` and `true` for `@value`.</span></span> 

3. <span data-ttu-id="c5aa0-253">在發行者上，執行 [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-253">At the Publisher, execute [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql).</span></span> <span data-ttu-id="c5aa0-254">指定 `@publication`、 `@subscriber`、 `@destination_db`，並對 `@update_mode`指定下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="c5aa0-254">Specify `@publication`, `@subscriber`, `@destination_db`, and one of the following values for `@update_mode`:</span></span>

    * <span data-ttu-id="c5aa0-255">`queued tran` - 啟用佇列更新的訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-255">`queued tran` - enables the subscription for queued updating.</span></span>
    * <span data-ttu-id="c5aa0-256">`queued failover` - 啟用佇列更新的支援，並將立即更新當作容錯移轉選項。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-256">`queued failover` - enables support for queued updating with immediate updating as a failover option.</span></span>

    > [!NOTE]  
>  <span data-ttu-id="c5aa0-257">queued failover 選項要求也要針對立即更新訂閱啟用發行集。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-257">The queued failover option requires that the publication also be enabled for immediate updating subscriptions.</span></span> <span data-ttu-id="c5aa0-258">若要容錯移轉到立即更新，您必須使用 [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) ，以定義訂閱者上的變更複寫到發行者時所用的認證。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-258">To fail over to immediate updating, you must use [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) to define the credentials under which changes at the Subscriber are replicated to the Publisher.</span></span>

4. <span data-ttu-id="c5aa0-259">在發行者上，執行 [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-259">At the Publisher, execute [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql).</span></span> <span data-ttu-id="c5aa0-260">指定下列參數：</span><span class="sxs-lookup"><span data-stu-id="c5aa0-260">Specify the following parameters:</span></span>

    * <span data-ttu-id="c5aa0-261">`@subscriber``@subscriber_db`和 `@publication`。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-261">`@subscriber`, `@subscriber_db`, and `@publication`.</span></span> 
    * <span data-ttu-id="c5aa0-262">散發代理程式在散發者上執行時，針對 `@job_login` 和 `@job_password`所使用的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-262">The Windows credentials under which the Distribution Agent at the Distributor runs for `@job_login` and `@job_password`.</span></span> 

    > [!NOTE]  
>  <span data-ttu-id="c5aa0-263">使用「Windows 整合式驗證」建立的連接一律使用由 `@job_login` 和 `@job_password`指定的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-263">Connections made using Windows Integrated Authentication are always made using the Windows credentials specified by `@job_login` and `@job_password`.</span></span> <span data-ttu-id="c5aa0-264">散發代理程式一律使用「Windows 整合式驗證」建立與散發者的本機連接。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-264">The Distribution Agent always makes the local connection to the Distributor using Windows Integrated Authentication.</span></span> <span data-ttu-id="c5aa0-265">依預設，代理程式會使用「Windows 整合式驗證」連接到訂閱者。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-265">By default, the agent connects to the Subscriber using Windows Integrated Authentication.</span></span> 
 
    * <span data-ttu-id="c5aa0-266">(選擇性) `0` 的 `@subscriber_security_mode` 值和 `@subscriber_login` 和 `@subscriber_password`的 SQL Server 登入資訊，如果您需要在連接到訂閱者時使用 SQL Server 驗證的話。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-266">(Optional) A value of `0` for `@subscriber_security_mode` and the SQL Server login information for `@subscriber_login` and `@subscriber_password`, if you need to use SQL Server Authentication when connecting to the Subscriber.</span></span> 
    * <span data-ttu-id="c5aa0-267">此訂閱之散發代理程式作業的排程。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-267">A schedule for the Distribution Agent job for this subscription.</span></span>


## <a name="example"></a><span data-ttu-id="c5aa0-268">範例</span><span class="sxs-lookup"><span data-stu-id="c5aa0-268">Example</span></span> ##

<span data-ttu-id="c5aa0-269">此範例會建立發行集的立即更新提取訂閱，此發行集可支援立即更新訂閱。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-269">This example creates an immediate updating pull subscription to a publication that supports immediate updating subscriptions.</span></span> <span data-ttu-id="c5aa0-270">登入和密碼值是在執行階段使用 sqlcmd 指令碼變數提供的。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-270">Login and password values are supplied at runtime using sqlcmd scripting variables.</span></span>

> [!NOTE]  
>  <span data-ttu-id="c5aa0-271">此指令碼使用 sqlcmd 指令碼變數。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-271">This script uses sqlcmd scripting variables.</span></span> <span data-ttu-id="c5aa0-272">它們的格式為 `$(MyVariable)`。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-272">They are in the form `$(MyVariable)`.</span></span> <span data-ttu-id="c5aa0-273">如需如何在命令列和 SQL Server Management Studio 中，使用指令碼變數的詳細資訊，請參閱[複寫系統預存程序概念](../concepts/replication-system-stored-procedures-concepts.md)主題中的＜執行複寫指令碼＞一節。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-273">For information about how to use scripting variables on the command line and in SQL Server Management Studio, see the **Executing Replication Scripts** section in the topic [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md).</span></span>

```sql
-- Execute this batch at the Subscriber.
DECLARE @publication AS sysname;
DECLARE @publicationDB AS sysname;
DECLARE @publisher AS sysname;
DECLARE @login AS sysname;
DECLARE @password AS nvarchar(512);
SET @publication = N'AdvWorksProductTran';
SET @publicationDB = N'AdventureWorks2008R2';
SET @publisher = $(PubServer);
SET @login = $(Login);
SET @password = $(Password);

-- At the subscription database, create a pull subscription to a transactional 
-- publication using immediate updating with queued updating as a failover.
EXEC sp_addpullsubscription 
    @publisher = @publisher, 
    @publication = @publication, 
    @publisher_db = @publicationDB, 
    @update_mode = N'failover', 
    @subscription_type = N'pull';

-- Add an agent job to synchronize the pull subscription, 
-- which uses Windows Authentication when connecting to the Distributor.
EXEC sp_addpullsubscription_agent 
    @publisher = @publisher, 
    @publisher_db = @publicationDB, 
    @publication = @publication,
    @job_login = @login,
    @job_password = @password; 

-- Add a Windows Authentication-based linked server that enables the 
-- Subscriber-side triggers to make updates at the Publisher. 
EXEC sp_link_publication 
    @publisher = @publisher, 
    @publication = @publication,
    @publisher_db = @publicationDB, 
    @security_mode = 0,
    @login = @login,
    @password = @password;
GO

USE AdventureWorks2008R2;
GO

-- Execute this batch at the Publisher.
DECLARE @publication AS sysname;
DECLARE @subscriptionDB AS sysname;
DECLARE @subscriber AS sysname;
SET @publication = N'AdvWorksProductTran'; 
SET @subscriptionDB = N'AdventureWorks2008R2Replica'; 
SET @subscriber = $(SubServer);

-- At the Publisher, register the subscription, using the defaults.
USE [AdventureWorks2008R2]
EXEC sp_addsubscription 
    @publication = @publication, 
    @subscriber = @subscriber, 
    @destination_db = @subscriptionDB, 
    @subscription_type = N'pull', 
    @update_mode = N'failover';
GO
```

## <a name="set-queued-updating-conflict-resolution-options-sql-server-management-studio"></a><span data-ttu-id="c5aa0-274">設定佇列更新衝突解決選項 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="c5aa0-274">Set Queued Updating Conflict Resolution Options (SQL Server Management Studio)</span></span>
  <span data-ttu-id="c5aa0-275">在 [發行集屬性 - \<Publication>] 對話方塊的 [訂閱選項] 頁面上，針對支援佇列更新訂閱的發行集設定衝突解決選項。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-275">Set conflict resolution options for publications that support queued updating subscriptions on the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="c5aa0-276">如需有關存取這個對話方塊的詳細資訊，請參閱＜ [View and Modify Publication Properties](view-and-modify-publication-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="c5aa0-276">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
### <a name="to-set-queued-updating-conflict-resolution-options"></a><span data-ttu-id="c5aa0-277">若要設定佇列更新衝突解決選項</span><span class="sxs-lookup"><span data-stu-id="c5aa0-277">To set queued updating conflict resolution options</span></span>  
  
1.  <span data-ttu-id="c5aa0-278">在 [發行集屬性 - \<Publication>] 對話方塊的 [訂閱選項] 頁面中，選取下列 [衝突解決原則] 選項的其中一個值：</span><span class="sxs-lookup"><span data-stu-id="c5aa0-278">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, select one of the following values for the **Conflict resolution policy** option:</span></span>    
    -   <span data-ttu-id="c5aa0-279">**[保留發行者變更]**</span><span class="sxs-lookup"><span data-stu-id="c5aa0-279">**Keep the Publisher change**</span></span>    
    -   <span data-ttu-id="c5aa0-280">**[保留訂閱者變更]**</span><span class="sxs-lookup"><span data-stu-id="c5aa0-280">**Keep the Subscriber change**</span></span>    
    -   <span data-ttu-id="c5aa0-281">**[重新初始化訂閱]**</span><span class="sxs-lookup"><span data-stu-id="c5aa0-281">**Reinitialize the subscription**</span></span>    
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

## <a name="see-also"></a><span data-ttu-id="c5aa0-282">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5aa0-282">See Also</span></span> ##
 <span data-ttu-id="c5aa0-283">[Create a Publication](create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="c5aa0-283">[Create a Publication](create-a-publication.md) </span></span>  
 <span data-ttu-id="c5aa0-284">[Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="c5aa0-284">[Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md) </span></span>  
 [<span data-ttu-id="c5aa0-285">以指令碼變數使用 sqlcmd</span><span class="sxs-lookup"><span data-stu-id="c5aa0-285">Use sqlcmd with Scripting Variables</span></span>](../../scripting/sqlcmd-use-with-scripting-variables.md)   

  
