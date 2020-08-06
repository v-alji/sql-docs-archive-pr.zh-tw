---
title: 訂閱發行集 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.conc.subtopubs.f1
helpviewer_keywords:
- subscriptions [SQL Server replication], about subscriptions
- pull subscriptions [SQL Server replication]
- subscriptions [SQL Server replication]
- push subscriptions [SQL Server replication], about push subscriptions
- merge replication subscribing [SQL Server replication]
- merge replication subscribing [SQL Server replication], about subscribing
- publications [SQL Server replication], subscribing
- push subscriptions [SQL Server replication]
- pull subscriptions [SQL Server replication], about pull subscriptions
- snapshot replication [SQL Server], subscribing
- transactional replication, subscribing
ms.assetid: 088ee30a-05ab-47c4-92ed-316b93e12445
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c565aae26c6d549eb67043168797d5fb059c8e2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585255"
---
# <a name="subscribe-to-publications"></a><span data-ttu-id="da3de-102">訂閱發行集</span><span class="sxs-lookup"><span data-stu-id="da3de-102">Subscribe to Publications</span></span>
  <span data-ttu-id="da3de-103">訂閱是指要求一份發行集中的資料和資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="da3de-103">A subscription is a request for a copy of the data and database objects in a publication.</span></span> <span data-ttu-id="da3de-104">訂閱會定義將收到的發行集，以及收到的位置和時間。</span><span class="sxs-lookup"><span data-stu-id="da3de-104">A subscription defines which publication will be received, and where and when it will be received.</span></span> <span data-ttu-id="da3de-105">規劃訂閱時，請考慮要執行代理程式處理的位置。</span><span class="sxs-lookup"><span data-stu-id="da3de-105">When planning for subscriptions, consider where you want agent processing to occur.</span></span> <span data-ttu-id="da3de-106">您選擇的訂閱類型會控制代理程式執行的位置。</span><span class="sxs-lookup"><span data-stu-id="da3de-106">The type of subscription you choose controls where the agent runs.</span></span> <span data-ttu-id="da3de-107">若為發送訂閱，則「合併代理程式」或「散發代理程式」會在「散發者」執行；若為提取訂閱，則代理程式會在「訂閱者」執行。</span><span class="sxs-lookup"><span data-stu-id="da3de-107">With a push subscription, the Merge Agent or Distribution Agent runs at the Distributor, whereas with a pull subscription, agents run at the Subscribers.</span></span> <span data-ttu-id="da3de-108">建立訂閱之後，就不能變更訂閱的類型。</span><span class="sxs-lookup"><span data-stu-id="da3de-108">After a subscription is created, it cannot be changed from one type to another.</span></span>  
  
|<span data-ttu-id="da3de-109">訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="da3de-109">Subscription</span></span>|<span data-ttu-id="da3de-110">特性</span><span class="sxs-lookup"><span data-stu-id="da3de-110">Characteristics</span></span>|<span data-ttu-id="da3de-111">使用時機</span><span class="sxs-lookup"><span data-stu-id="da3de-111">Use When</span></span>|  
|------------------|---------------------|--------------|  
|<span data-ttu-id="da3de-112">發送訂閱</span><span class="sxs-lookup"><span data-stu-id="da3de-112">Push Subscription</span></span>|<span data-ttu-id="da3de-113">在發送訂閱中，「訂閱者」不需發出請求，「發行者」便會將變更傳播給「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="da3de-113">With a push subscription, the Publisher propagates changes to a Subscriber without a request from the Subscriber.</span></span> <span data-ttu-id="da3de-114">變更可以在需要時發散給「訂閱者」，或是根據排程發散給「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="da3de-114">Changes can be pushed to Subscribers on demand, continuously, or on a scheduled basis.</span></span> <span data-ttu-id="da3de-115">「散發代理程式」或「合併代理程式」是在「散發者」中執行。</span><span class="sxs-lookup"><span data-stu-id="da3de-115">The Distribution Agent or Merge Agent runs at the Distributor.</span></span>|<span data-ttu-id="da3de-116">通常是連續或根據定期排程進行資料同步。</span><span class="sxs-lookup"><span data-stu-id="da3de-116">Data will typically be synchronized continuously or on a frequently recurring schedule.</span></span><br /><br /> <span data-ttu-id="da3de-117">發行集需要近乎即時移動資料。</span><span class="sxs-lookup"><span data-stu-id="da3de-117">Publications require near real-time movement of data.</span></span><br /><br /> <span data-ttu-id="da3de-118">即使「散發者」的處理器額外負荷較高，也不會影響效能。</span><span class="sxs-lookup"><span data-stu-id="da3de-118">The higher processor overhead at the Distributor does not affect performance.</span></span><br /><br /> <span data-ttu-id="da3de-119">最常搭配快照和異動複寫使用。</span><span class="sxs-lookup"><span data-stu-id="da3de-119">Most often used with snapshot and transactional replication.</span></span>|  
|<span data-ttu-id="da3de-120">提取訂閱</span><span class="sxs-lookup"><span data-stu-id="da3de-120">Pull Subscription</span></span>|<span data-ttu-id="da3de-121">在提取訂閱中，「訂閱者」必須請求傳送「發行者」中的變更。</span><span class="sxs-lookup"><span data-stu-id="da3de-121">With a pull subscription, the Subscriber requests changes made at the Publisher.</span></span> <span data-ttu-id="da3de-122">提取訂閱允許使用者在「訂閱者」中判斷何時要同步資料變更。</span><span class="sxs-lookup"><span data-stu-id="da3de-122">Pull subscriptions allow the user at the Subscriber to determine when the data changes are synchronized.</span></span> <span data-ttu-id="da3de-123">「散發代理程式」或「合併代理程式」是在「訂閱者」中執行。</span><span class="sxs-lookup"><span data-stu-id="da3de-123">The Distribution Agent or the Merge Agent runs at the Subscriber.</span></span>|<span data-ttu-id="da3de-124">資料通常是在需要時或根據排程進行同步處理，而不是持續進行。</span><span class="sxs-lookup"><span data-stu-id="da3de-124">Data will typically be synchronized on demand or on a schedule rather than continuously.</span></span><br /><br /> <span data-ttu-id="da3de-125">發行集擁有大量「訂閱者」，且 (或) 其需要過多資源，而無法在「散發者」執行所有代理程式。</span><span class="sxs-lookup"><span data-stu-id="da3de-125">The publication has a large number of Subscribers, and/or it would be too resource-intensive to run all the agents at the Distributor.</span></span><br /><br /> <span data-ttu-id="da3de-126">「訂閱者」是獨立的、中斷的以及/或機動的。</span><span class="sxs-lookup"><span data-stu-id="da3de-126">Subscribers are autonomous, disconnected, and/or mobile.</span></span> <span data-ttu-id="da3de-127">「訂閱者」將決定其連接及同步變更的時機。</span><span class="sxs-lookup"><span data-stu-id="da3de-127">Subscribers will determine when they will connect and synchronize changes.</span></span><br /><br /> <span data-ttu-id="da3de-128">最常搭配合併複寫使用。</span><span class="sxs-lookup"><span data-stu-id="da3de-128">Most often used with merge replication.</span></span>|  
  
## <a name="merge-replication-subscription-types"></a><span data-ttu-id="da3de-129">合併複寫訂閱類型</span><span class="sxs-lookup"><span data-stu-id="da3de-129">Merge Replication Subscription Types</span></span>  
 <span data-ttu-id="da3de-130">所有複寫類型都允許發送和提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="da3de-130">All replication types allow push and pull subscriptions.</span></span> <span data-ttu-id="da3de-131">合併複寫會使用另外兩個詞彙來區分訂閱︰客訂閱和主訂閱。</span><span class="sxs-lookup"><span data-stu-id="da3de-131">Merge replication uses two additional terms to distinguish subscriptions: client subscriptions and server subscriptions.</span></span> <span data-ttu-id="da3de-132">客訂閱和主訂閱類型都可搭配發送和提取訂閱使用。</span><span class="sxs-lookup"><span data-stu-id="da3de-132">Both client and server subscription types can be used with push and pull subscriptions.</span></span> <span data-ttu-id="da3de-133">客訂閱適用大部份的「訂閱者」，而主訂閱通常用於重新發行資料給其他「訂閱者」的「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="da3de-133">Client subscriptions are appropriate for most Subscribers, whereas server subscriptions are typically used for Subscribers that republish data to other Subscribers.</span></span> <span data-ttu-id="da3de-134">訂閱選擇也會影響衝突解決。</span><span class="sxs-lookup"><span data-stu-id="da3de-134">Subscription choice also affects conflict resolution.</span></span>  
  
## <a name="non-sql-server-subscribers"></a><span data-ttu-id="da3de-135">非 SQL Server 訂閱者</span><span class="sxs-lookup"><span data-stu-id="da3de-135">Non-SQL Server Subscribers</span></span>  
 <span data-ttu-id="da3de-136">Oracle 和 IBM DB2 都可使用發送訂閱來訂閱快照集和交易式發行集。</span><span class="sxs-lookup"><span data-stu-id="da3de-136">Oracle and IBM DB2 can subscribe to snapshot and transactional publications using push subscriptions.</span></span> <span data-ttu-id="da3de-137">如需詳細資訊，請參閱 [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md)。</span><span class="sxs-lookup"><span data-stu-id="da3de-137">For more information, see [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md).</span></span>  
  
## <a name="creating-subscriptions"></a><span data-ttu-id="da3de-138">建立訂閱</span><span class="sxs-lookup"><span data-stu-id="da3de-138">Creating Subscriptions</span></span>  
 <span data-ttu-id="da3de-139">若要建立訂閱，您必須提供下列資訊︰</span><span class="sxs-lookup"><span data-stu-id="da3de-139">To create a subscription, you supply the following information:</span></span>  
  
-   <span data-ttu-id="da3de-140">發行集的名稱。</span><span class="sxs-lookup"><span data-stu-id="da3de-140">The name of the publication.</span></span>  
  
-   <span data-ttu-id="da3de-141">「訂閱者」和訂閱資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="da3de-141">The name of the Subscriber and the subscription database.</span></span>  
  
-   <span data-ttu-id="da3de-142">在「散發者」或「訂閱者」執行「散發代理程式」或「合併代理程式」。</span><span class="sxs-lookup"><span data-stu-id="da3de-142">Whether the Distribution Agent or Merge Agent runs at the Distributor or at the Subscriber.</span></span>  
  
-   <span data-ttu-id="da3de-143">「散發代理程式」或「合併代理程式」會持續執行、定期執行，或是需要時才執行。</span><span class="sxs-lookup"><span data-stu-id="da3de-143">Whether the Distribution Agent or Merge Agent runs continuously, on a scheduled basis, or on demand only.</span></span>  
  
-   <span data-ttu-id="da3de-144">「快照集代理程式」是否應該為訂閱建立初始快照集，以及「散發代理程式」或「合併代理程式」是否應該在「訂閱者」中套用該快照集。</span><span class="sxs-lookup"><span data-stu-id="da3de-144">Whether the Snapshot Agent should create an initial snapshot for the subscription and whether the Distribution Agent or Merge Agent should apply that snapshot at the Subscriber.</span></span>  
  
-   <span data-ttu-id="da3de-145">用來執行「散發代理程式」或「合併代理程式」的帳戶。</span><span class="sxs-lookup"><span data-stu-id="da3de-145">Accounts under which the Distribution Agent or Merge Agent will run.</span></span>  
  
-   <span data-ttu-id="da3de-146">合併複寫的訂閱類型為︰主或客。</span><span class="sxs-lookup"><span data-stu-id="da3de-146">For merge replication, the type of subscription: server or client.</span></span>  
  
 <span data-ttu-id="da3de-147">**若要建立發送訂閱**</span><span class="sxs-lookup"><span data-stu-id="da3de-147">**To create a push subscription**</span></span>  
  
 [<span data-ttu-id="da3de-148">建立發送訂閱</span><span class="sxs-lookup"><span data-stu-id="da3de-148">Create a Push Subscription</span></span>](create-a-push-subscription.md)  
  
 <span data-ttu-id="da3de-149">**若要檢視或修改發送訂閱屬性**</span><span class="sxs-lookup"><span data-stu-id="da3de-149">**To view or modify push subscription properties**</span></span>  
  
 [<span data-ttu-id="da3de-150">檢視及修改發送訂閱屬性</span><span class="sxs-lookup"><span data-stu-id="da3de-150">View and Modify Push Subscription Properties</span></span>](view-and-modify-push-subscription-properties.md)  
  
 <span data-ttu-id="da3de-151">**若要刪除發送訂閱**</span><span class="sxs-lookup"><span data-stu-id="da3de-151">**To delete a push subscription**</span></span>  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="da3de-152">:[刪除發送訂閱](delete-a-push-subscription.md)</span><span class="sxs-lookup"><span data-stu-id="da3de-152">: [Delete a Push Subscription](delete-a-push-subscription.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="da3de-153">刪除訂閱並不會移除「訂閱者」中已發行的物件。</span><span class="sxs-lookup"><span data-stu-id="da3de-153">Deleting a subscription does not remove published objects from the Subscriber.</span></span>  
  
 <span data-ttu-id="da3de-154">**若要建立提取訂閱**</span><span class="sxs-lookup"><span data-stu-id="da3de-154">**To create a pull subscription**</span></span>  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="da3de-155">:[建立提取訂閱](create-a-pull-subscription.md)</span><span class="sxs-lookup"><span data-stu-id="da3de-155">: [Create a Pull Subscription](create-a-pull-subscription.md)</span></span>  
  
 <span data-ttu-id="da3de-156">**若要檢視或修改提取訂閱屬性**</span><span class="sxs-lookup"><span data-stu-id="da3de-156">**To view or modify pull subscription properties**</span></span>  
  
 [<span data-ttu-id="da3de-157">檢視及修改提取訂閱屬性</span><span class="sxs-lookup"><span data-stu-id="da3de-157">View and Modify Pull Subscription Properties</span></span>](view-and-modify-pull-subscription-properties.md)  
  
 <span data-ttu-id="da3de-158">**若要刪除提取訂閱**</span><span class="sxs-lookup"><span data-stu-id="da3de-158">**To delete a pull subscription**</span></span>  
  
 [<span data-ttu-id="da3de-159">刪除提取訂閱</span><span class="sxs-lookup"><span data-stu-id="da3de-159">Delete a Pull Subscription</span></span>](delete-a-pull-subscription.md)  
  
## <a name="see-also"></a><span data-ttu-id="da3de-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da3de-160">See Also</span></span>  
 <span data-ttu-id="da3de-161">[保護訂閱者](security/secure-the-subscriber.md) </span><span class="sxs-lookup"><span data-stu-id="da3de-161">[Secure the Subscriber](security/secure-the-subscriber.md) </span></span>  
 [<span data-ttu-id="da3de-162">訂閱逾期與停用</span><span class="sxs-lookup"><span data-stu-id="da3de-162">Subscription Expiration and Deactivation</span></span>](subscription-expiration-and-deactivation.md)  
  
  
