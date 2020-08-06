---
title: 複寫訂閱者及 AlwaysOn 可用性群組 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 01/16/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover subscribers with AlwaysOn
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 0995f269-0580-43ed-b8bf-02b9ad2d7ee6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 449b5ac416f2ae86395c40a984678ed4258b3b85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596908"
---
# <a name="replication-subscribers-and-alwayson-availability-groups-sql-server"></a><span data-ttu-id="08fbf-102">複寫訂閱者及 AlwaysOn 可用性群組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="08fbf-102">Replication Subscribers and AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="08fbf-103">當包含複寫訂閱者資料庫的 AlwaysOn 可用性群組容錯移轉時，複寫訂閱可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="08fbf-103">When an AlwaysOn availability group containing a database that is a replication subscriber fails over, the replication subscription might fail.</span></span> <span data-ttu-id="08fbf-104">針對交易式複寫推播訂閱者，若訂用帳戶是使用 AGI 接聽程式名稱建立時，散發代理程式將繼續自動複寫。</span><span class="sxs-lookup"><span data-stu-id="08fbf-104">For transactional replication push subscribers, the distribution agent will continue to replicate automatically after a failover if the subscription was created using the AG listener name.</span></span> <span data-ttu-id="08fbf-105">針對交易式複寫推播訂閱者，若訂用帳戶是使用 AGI 接聽程式名稱建立且原始訂閱者伺服器已啟動並執行時，散發代理程式將繼續自動複寫。</span><span class="sxs-lookup"><span data-stu-id="08fbf-105">For transactional replication pull subscribers, the distribution agent will continue to replicate automatically after a failover, if the subscription was created using the AG listener name and the original subscriber server is up and running.</span></span> <span data-ttu-id="08fbf-106">這是因為散發代理程式作業只會在原始訂閱者 (AG 的原始複本) 上建立。</span><span class="sxs-lookup"><span data-stu-id="08fbf-106">This is because the distribution agent jobs only get created on the original subscriber (primary replica of the AG).</span></span> <span data-ttu-id="08fbf-107">如果是合併訂閱者，複寫管理員必須透過重新建立訂閱，手動重新設定訂閱者。</span><span class="sxs-lookup"><span data-stu-id="08fbf-107">For merge subscribers, a replication administrator must manually reconfigure the subscriber, by recreating the subscription.</span></span>  
  
## <a name="what-is-supported"></a><span data-ttu-id="08fbf-108">支援項目</span><span class="sxs-lookup"><span data-stu-id="08fbf-108">What is Supported</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="08fbf-109">複寫支援發行者的自動容錯移轉、交易式訂閱者的自動容錯移轉，以及合併訂閱者的手動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="08fbf-109">replication supports the automatic failover of the publisher, the automatic failover of transactional subscribers, and the manual failover of merge subscribers.</span></span> <span data-ttu-id="08fbf-110">不支援可用性資料庫的散發者容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="08fbf-110">The failover of a distributor on an availability database is not supported.</span></span> <span data-ttu-id="08fbf-111">AlwaysOn 無法結合 Websync 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Compact 案例。</span><span class="sxs-lookup"><span data-stu-id="08fbf-111">AlwaysOn cannot be combined with Websync and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Compact scenarios.</span></span>  
  
 <span data-ttu-id="08fbf-112">**合併提取訂閱的容錯移轉**</span><span class="sxs-lookup"><span data-stu-id="08fbf-112">**Failover of a Merge Pull Subscription**</span></span>  
  
 <span data-ttu-id="08fbf-113">提取訂閱在可用性群組容錯移轉時失敗，因為提取代理程式找不到儲存在裝載主要複本之伺服器執行個體的 **msdb** 資料庫中的作業，這個伺服器執行個體已失敗，因此無法使用。</span><span class="sxs-lookup"><span data-stu-id="08fbf-113">A pull subscription fails upon availability group failover, because pull agent cannot find the jobs stored in the **msdb** database of the server instance that hosts the primary replica; which is not available because the server instance has failed.</span></span>  
  
 <span data-ttu-id="08fbf-114">**合併發送訂閱的容錯移轉**</span><span class="sxs-lookup"><span data-stu-id="08fbf-114">**Failover of a Merge Push Subscription**</span></span>  
  
 <span data-ttu-id="08fbf-115">發送訂閱在可用性群組容錯移轉時失敗，因為發送代理程式無法再連接至原始訂閱者上的原始訂閱資料庫。</span><span class="sxs-lookup"><span data-stu-id="08fbf-115">A push subscription fails upon availability group failover, because the push agent can no longer connect to original subscription database on original subscriber.</span></span>  
  
## <a name="how-to-create-transactional-subscription-in-an-alwayson-environment"></a><span data-ttu-id="08fbf-116">如何在 AlwaysOn 環境中建立交易式訂閱</span><span class="sxs-lookup"><span data-stu-id="08fbf-116">How to Create Transactional Subscription in an AlwaysOn Environment</span></span>  
 <span data-ttu-id="08fbf-117">對於異動複寫，請使用下列步驟來設定和容錯移轉訂閱者可用性群組：</span><span class="sxs-lookup"><span data-stu-id="08fbf-117">For transactional replication, use the following steps to configure and failover a subscriber availability group:</span></span>  
  
1.  <span data-ttu-id="08fbf-118">在建立訂閱之前，將訂閱者資料庫加入至適當的 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="08fbf-118">Before creating the subscription, add the subscriber database to the appropriate AlwaysOn availability group.</span></span>  
  
2.  <span data-ttu-id="08fbf-119">將訂閱者的可用性群組接聽程式做為連結的伺服器加入至可用性群組的所有節點。</span><span class="sxs-lookup"><span data-stu-id="08fbf-119">Add the subscriber's availability group Listener as a linked server to all nodes of the availability group.</span></span> <span data-ttu-id="08fbf-120">這個步驟可確保所有可能的容錯移轉夥伴都知道且可以連接到接聽程式。</span><span class="sxs-lookup"><span data-stu-id="08fbf-120">This step ensures that all potential failover partners are aware of and can connect to the listener.</span></span>  
  
3.  <span data-ttu-id="08fbf-121">使用下列＜ **建立異動複寫發送訂閱** ＞一節中的指令碼，使用訂閱者的可用性群組接聽程式名稱來建立訂閱。</span><span class="sxs-lookup"><span data-stu-id="08fbf-121">Using the script in the **Creating a Transactional Replication Push Subscription** section below, create the subscription using the name of the availability group listener of the subscriber.</span></span> <span data-ttu-id="08fbf-122">在容錯移轉之後，接聽程式名稱一定會維持有效，而訂閱者的實際伺服器名稱將取決於成為新主要複本的實際節點。</span><span class="sxs-lookup"><span data-stu-id="08fbf-122">After a failover, the listener name will always remain valid, whereas the actual server name of the subscriber will depend on the actual node that became the new primary.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="08fbf-123">訂閱必須使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 指令碼來建立，無法使用 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]來建立。</span><span class="sxs-lookup"><span data-stu-id="08fbf-123">The subscription must be created by using a [!INCLUDE[tsql](../../../includes/tsql-md.md)] script and cannot be created using [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].</span></span>  
  
4.  <span data-ttu-id="08fbf-124">如果建立提取訂閱：</span><span class="sxs-lookup"><span data-stu-id="08fbf-124">If creating a pull subscription:</span></span>  
  
    1.  <span data-ttu-id="08fbf-125">在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]，在主要訂閱者節點上開啟 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="08fbf-125">In [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], on the primary subscriber node, open the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent tree.</span></span>  
  
    2.  <span data-ttu-id="08fbf-126">識別 **提取散發代理程式** 作業，並且編輯作業。</span><span class="sxs-lookup"><span data-stu-id="08fbf-126">Identify the **Pull Distribution Agent** job and edit the job.</span></span>  
  
    3.  <span data-ttu-id="08fbf-127">在 **執行代理程式** 作業步驟，檢查 `-Publisher` 和 `-Distributor` 參數。</span><span class="sxs-lookup"><span data-stu-id="08fbf-127">On the **Run Agent** job step, check the `-Publisher` and `-Distributor` parameters.</span></span> <span data-ttu-id="08fbf-128">確定這些參數包含發行者和散發者伺服器的正確直接伺服器和執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="08fbf-128">Make sure that these parameters contain the correct direct server and instance names of the publisher and distributor server.</span></span>  
  
    4.  <span data-ttu-id="08fbf-129">將 `-Subscriber` 參數變更為訂閱者的可用性群組接聽程式名稱。</span><span class="sxs-lookup"><span data-stu-id="08fbf-129">Change the `-Subscriber` parameter to the subscriber's availability group listener name.</span></span>  
  
 <span data-ttu-id="08fbf-130">遵循這些步驟建立訂閱時，在容錯移轉後就不需要執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="08fbf-130">When you create your subscription following these steps, then you won't have to do anything after a failover.</span></span>  
  
## <a name="creating-a-transactional-replication-push-subscription"></a><span data-ttu-id="08fbf-131">建立異動複寫發送訂閱</span><span class="sxs-lookup"><span data-stu-id="08fbf-131">Creating a Transactional Replication Push Subscription</span></span>  
  
```  
-- commands to execute at the publisher, in the publisher database:  
use [<publisher database name>]  
EXEC sp_addsubscription @publication = N'<publication name>',   
       @subscriber = N'<availability group listener name>',   
       @destination_db = N'<subscriber database name>',   
       @subscription_type = N'Push',   
       @sync_type = N'automatic', @article = N'all', @update_mode = N'read only', @subscriber_type = 0;  
GO  
  
EXEC sp_addpushsubscription_agent @publication = N'<publication name>',   
       @subscriber = N'<availability group listener name>',   
       @subscriber_db = N'<subscriber database name>',   
       @job_login = null, @job_password = null, @subscriber_security_mode = 1;  
GO  
```  
  
## <a name="to-resume-the-merge-agents-after-the-availability-group-of-the-subscriber-fails-over"></a><span data-ttu-id="08fbf-132">若要在訂閱者的可用性群組容錯移轉之後繼續合併代理程式</span><span class="sxs-lookup"><span data-stu-id="08fbf-132">To Resume the Merge Agents After the Availability Group of the Subscriber Fails Over</span></span>  
 <span data-ttu-id="08fbf-133">如果是合併式複寫，複寫管理員必須透過下列步驟手動重新設定訂閱者：</span><span class="sxs-lookup"><span data-stu-id="08fbf-133">For merge replication, a replication administrator must manually reconfigure the subscriber with the following steps:</span></span>  
  
1.  <span data-ttu-id="08fbf-134">執行 `sp_subscription_cleanup` 移除訂閱者的舊訂閱。</span><span class="sxs-lookup"><span data-stu-id="08fbf-134">Execute `sp_subscription_cleanup` to remove the old subscription for the subscriber.</span></span> <span data-ttu-id="08fbf-135">在新的主要複本 (原來為次要複本) 上執行此動作。</span><span class="sxs-lookup"><span data-stu-id="08fbf-135">Perform this action on the new primary replica (which was formerly the secondary replica).</span></span>  
  
2.  <span data-ttu-id="08fbf-136">從新快照集開始建立新訂閱，重新建立訂閱。</span><span class="sxs-lookup"><span data-stu-id="08fbf-136">Recreate the subscription by creating a new subscription, beginning with a new snapshot.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="08fbf-137">目前的程序不適用於合併式複寫訂閱者，但是合併式複寫的主要案例是非連接的使用者 (桌上型電腦、筆記型電腦、手持式裝置)，這些使用者不會在訂閱者上使用 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="08fbf-137">The current process is inconvenient for merge replication subscribers, however the main scenario for merge replication is disconnected users (desktops, laptops, handset devices) which will not use AlwaysOn availability groups on the subscriber.</span></span>  
  
  
