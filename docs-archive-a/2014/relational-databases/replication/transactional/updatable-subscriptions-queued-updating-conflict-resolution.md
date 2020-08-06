---
title: 佇列更新衝突偵測和解決 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- conflict resolution [SQL Server replication], queued updating subscriptions
- viewing queued updating conflicts
- conflict resolution [SQL Server replication]
- queued updating subscriptions [SQL Server replication]
- articles [SQL Server replication], conflict resolution
ms.assetid: 084ac587-25e7-4bd0-a385-556bbe07d02f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c4608347ab119e25caa45b0ee4a592a953e34a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606737"
---
# <a name="queued-updating-conflict-detection-and-resolution"></a><span data-ttu-id="605bf-102">Queued Updating Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="605bf-102">Queued Updating Conflict Detection and Resolution</span></span>
  <span data-ttu-id="605bf-103">因為佇列更新訂閱允許在多個位置對相同資料做修改，則在發行者同步資料時，有可能發生衝突。</span><span class="sxs-lookup"><span data-stu-id="605bf-103">Because queued updating subscriptions allow modifications to the same data at multiple locations, there may be conflicts when data is synchronized at the Publisher.</span></span> <span data-ttu-id="605bf-104">複寫會在變更與發行者同步處理時偵測是否有任何衝突，並使用您在建立發行集時選取的解決原則解決衝突。</span><span class="sxs-lookup"><span data-stu-id="605bf-104">Replication detects any conflicts when changes are synchronized with the Publisher and resolves those conflicts using the resolution policy you selected when creating the publication.</span></span> <span data-ttu-id="605bf-105">會發生下列衝突：</span><span class="sxs-lookup"><span data-stu-id="605bf-105">The following conflicts can occur:</span></span>  
  
-   <span data-ttu-id="605bf-106">更新與插入衝突。</span><span class="sxs-lookup"><span data-stu-id="605bf-106">Update and insert conflicts.</span></span> <span data-ttu-id="605bf-107">當相同的資料在兩個位置同時變更時，就會發生此衝突。</span><span class="sxs-lookup"><span data-stu-id="605bf-107">This conflict happens when the same data is changed at two locations.</span></span> <span data-ttu-id="605bf-108">一個變更成功，而另一個變更失敗。</span><span class="sxs-lookup"><span data-stu-id="605bf-108">One change wins, and the other one loses.</span></span>  
  
-   <span data-ttu-id="605bf-109">刪除衝突。</span><span class="sxs-lookup"><span data-stu-id="605bf-109">Delete conflicts.</span></span> <span data-ttu-id="605bf-110">當資料列在一處已遭刪除，而在另一處已被更新，就會發生此衝突。</span><span class="sxs-lookup"><span data-stu-id="605bf-110">This conflict occurs when the same row is deleted at one location and changed at the other.</span></span>  
  
 <span data-ttu-id="605bf-111">衝突偵測和解決可能是相當耗時間且需使用相當多資源的程序；因此，最好在應用程式中藉由建立資料分割的方式將衝突減至最少，這種方式可讓不同的訂閱者修改不同的資料子集。</span><span class="sxs-lookup"><span data-stu-id="605bf-111">Conflict detection and resolution can be a time-consuming and resource-intensive process; therefore, it is best to minimize conflicts in the application by creating data partitions so that different Subscribers modify different subsets of data.</span></span>  
  
## <a name="detecting-conflicts"></a><span data-ttu-id="605bf-112">偵測衝突</span><span class="sxs-lookup"><span data-stu-id="605bf-112">Detecting Conflicts</span></span>  
 <span data-ttu-id="605bf-113">建立發行集和啟用佇列更新時，複寫會將預設值是 **newid()** 的**uniqueidentifier**資料行 ( **msrepl_tran_version** ) 加入基礎資料表中。</span><span class="sxs-lookup"><span data-stu-id="605bf-113">When creating a publication and enabling queued updating, replication adds a **uniqueidentifier** column (**msrepl_tran_version**) with the default of **newid()** to the underlying table.</span></span> <span data-ttu-id="605bf-114">當發行的資料是在發行者或訂閱者變更，資料列會接收全域唯一識別碼 (GUID) 來指示新的資料列版本存在。</span><span class="sxs-lookup"><span data-stu-id="605bf-114">When published data is changed at either the Publisher or the Subscriber, the row receives a new globally unique identifier (GUID) to indicate that a new row version exists.</span></span> <span data-ttu-id="605bf-115">「佇列讀取器代理程式」會在同步時使用此資料行，判斷衝突是否存在。</span><span class="sxs-lookup"><span data-stu-id="605bf-115">The Queue Reader Agent uses this column during synchronization to determine if a conflict exists.</span></span>  
  
 <span data-ttu-id="605bf-116">佇列中的交易會維護新舊的值。</span><span class="sxs-lookup"><span data-stu-id="605bf-116">A transaction in a queue maintains the old and new row version values.</span></span> <span data-ttu-id="605bf-117">在發行者套用交易時，交易的 GUID 以及發行集內的 GUID 會相互比較。</span><span class="sxs-lookup"><span data-stu-id="605bf-117">When the transaction is applied at the Publisher, the GUIDs from the transaction and the GUID in the publication are compared.</span></span> <span data-ttu-id="605bf-118">若儲存在交易中的 GUID 符合發行集內的 GUID，就會更新發行集而且會指派由訂閱者產生的資料列。</span><span class="sxs-lookup"><span data-stu-id="605bf-118">If the old GUID stored in the transaction matches the GUID in the publication, the publication is updated and the row is assigned the new GUID that was generated by the Subscriber.</span></span> <span data-ttu-id="605bf-119">將發行集更新成交易中的 GUID 後，您在發行集和交易中有相符的資料列。</span><span class="sxs-lookup"><span data-stu-id="605bf-119">By updating the publication with the GUID from the transaction, you have matching row versions in the publication and in the transaction.</span></span>  
  
 <span data-ttu-id="605bf-120">若儲存在交易中的舊 GUID 不符合發行集內的 GUID，就會偵測到衝突。</span><span class="sxs-lookup"><span data-stu-id="605bf-120">If the old GUID stored in the transaction does not match the GUID in the publication, a conflict is detected.</span></span> <span data-ttu-id="605bf-121">發行集內的新 GUID 指示有兩種不同的資料列版本存在：訂閱者傳送之交易中的 GUID，另一個是存在於發行者較新的 GUID。</span><span class="sxs-lookup"><span data-stu-id="605bf-121">The new GUID in the publication indicates that two different row versions exist: one in the transaction being submitted by the Subscriber and a newer one that exists on the Publisher.</span></span> <span data-ttu-id="605bf-122">在此狀況下，會在此訂閱者交易同步之前，另一個訂閱者或發行者會先更新發行集內同一個資料列。</span><span class="sxs-lookup"><span data-stu-id="605bf-122">In this case, another Subscriber or the Publisher updated the same row in the publication before this Subscriber transaction was synchronized.</span></span>  
  
 <span data-ttu-id="605bf-123">與合併式複寫不同的是，使用 GUID 資料行並不是用來識別資料列本身，而是用來檢查資料列是否變更。</span><span class="sxs-lookup"><span data-stu-id="605bf-123">Unlike merge replication, the use of a GUID column is not used to identify the row itself, but is used to check if the row has changed.</span></span>  
  
## <a name="resolving-conflicts"></a><span data-ttu-id="605bf-124">解決衝突</span><span class="sxs-lookup"><span data-stu-id="605bf-124">Resolving Conflicts</span></span>  
 <span data-ttu-id="605bf-125">當您使用佇列更新建立發行集時，會選取要在偵測到任何衝突時使用的衝突解決器。</span><span class="sxs-lookup"><span data-stu-id="605bf-125">When you create a publication using queued updating, you select a conflict resolver to be used if any conflicts are detected.</span></span> <span data-ttu-id="605bf-126">衝突解決器會管理「佇列讀取器代理程式」進行同步處理過程中所遭遇不同版本之同一資料列的方式。</span><span class="sxs-lookup"><span data-stu-id="605bf-126">The conflict resolver governs how the Queue Reader Agent handles different versions of the same row encountered during synchronization.</span></span> <span data-ttu-id="605bf-127">只要沒有訂閱發行集時，就可以在建立發行集後變更衝突解決原則。</span><span class="sxs-lookup"><span data-stu-id="605bf-127">You can change the conflict resolution policy after the publication is created as long as there are no subscriptions to the publication.</span></span> <span data-ttu-id="605bf-128">衝突解決器選擇如下：</span><span class="sxs-lookup"><span data-stu-id="605bf-128">The conflict resolver choices are the following:</span></span>  
  
-   <span data-ttu-id="605bf-129">發行者優先 (預設值)</span><span class="sxs-lookup"><span data-stu-id="605bf-129">Publisher wins (the default)</span></span>  
  
-   <span data-ttu-id="605bf-130">發行者優先且重新初始化訂閱</span><span class="sxs-lookup"><span data-stu-id="605bf-130">Publisher wins and the subscription is reinitialized</span></span>  
  
-   <span data-ttu-id="605bf-131">訂閱者優先</span><span class="sxs-lookup"><span data-stu-id="605bf-131">Subscriber wins</span></span>  
  
 <span data-ttu-id="605bf-132">衝突可以使用「衝突檢視器」來記錄和檢視。</span><span class="sxs-lookup"><span data-stu-id="605bf-132">Conflicts are recorded and can be viewed using the Conflict Viewer.</span></span>  
  
 <span data-ttu-id="605bf-133">**若要設定佇列更新衝突解決原則**</span><span class="sxs-lookup"><span data-stu-id="605bf-133">**To set the queued updating conflict resolution policy**</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="605bf-134">：[ &#40;SQL Server Management Studio&#41;](../publish/create-an-updatable-subscription-to-a-transactional-publication.md)</span><span class="sxs-lookup"><span data-stu-id="605bf-134">: [Set Queued Updating Conflict Resolution Options &#40;SQL Server Management Studio&#41;](../publish/create-an-updatable-subscription-to-a-transactional-publication.md)</span></span>  
  
-   <span data-ttu-id="605bf-135">複寫 Transact-SQL 程式設計： [啟用交易式發行集的更新訂閱](../publish/enable-updating-subscriptions-for-transactional-publications.md)</span><span class="sxs-lookup"><span data-stu-id="605bf-135">Replication Transact-SQL programming: [Enable Updating Subscriptions for Transactional Publications](../publish/enable-updating-subscriptions-for-transactional-publications.md)</span></span>  
  
 <span data-ttu-id="605bf-136">**若要檢視資料衝突**</span><span class="sxs-lookup"><span data-stu-id="605bf-136">**To view data conflicts**</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="605bf-137">：[View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;](../view-data-conflicts-for-transactional-publications-sql-server-management-studio.md) (檢視交易式發行集的資料衝突 &#40;SQL Server Management Studio&#41;)</span><span class="sxs-lookup"><span data-stu-id="605bf-137">: [View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;](../view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)</span></span>  
  
### <a name="publisher-wins"></a><span data-ttu-id="605bf-138">發行者優先</span><span class="sxs-lookup"><span data-stu-id="605bf-138">Publisher Wins</span></span>  
 <span data-ttu-id="605bf-139">當衝突解決設定成「發行者優先」時，會以發行者的資料為基礎來維護交易一致性。</span><span class="sxs-lookup"><span data-stu-id="605bf-139">When the conflict resolution is set to the Publisher wins, transactional consistency is maintained based on the data at the Publisher.</span></span> <span data-ttu-id="605bf-140">衝突中的交易會在初始它的訂閱者復原。</span><span class="sxs-lookup"><span data-stu-id="605bf-140">The conflicting transaction is rolled back at the Subscriber that initiated it.</span></span>  
  
 <span data-ttu-id="605bf-141">「佇列讀取器代理程式」會偵測衝突，且會產生補償的命令，並張貼於散發資料庫中藉此將其傳播至訂閱者。</span><span class="sxs-lookup"><span data-stu-id="605bf-141">The Queue Reader Agent detects a conflict and compensating commands are generated and propagated to the Subscriber by posting them in the distribution database.</span></span> <span data-ttu-id="605bf-142">之後，「散發代理程式」會將補償命令套用至產生衝突交易的訂閱者。</span><span class="sxs-lookup"><span data-stu-id="605bf-142">The Distribution Agent then applies the compensating commands to the Subscriber that originated the conflicting transaction.</span></span> <span data-ttu-id="605bf-143">補償動作會更新訂閱者上的資料列，使其符合發行者上的資料列。</span><span class="sxs-lookup"><span data-stu-id="605bf-143">The compensating actions update the rows on the Subscriber to match the rows on the Publisher.</span></span>  
  
 <span data-ttu-id="605bf-144">直到套用補償命令之前，您都可以讀取最終會於訂閱者回復的交易結果。</span><span class="sxs-lookup"><span data-stu-id="605bf-144">Until the compensating commands are applied, it is possible to read the results of a transaction that will eventually be rolled back at the Subscriber.</span></span> <span data-ttu-id="605bf-145">這相當於中途讀取 (讀取未認可隔離等級)。</span><span class="sxs-lookup"><span data-stu-id="605bf-145">This is equivalent to a dirty read (read uncommitted isolation level).</span></span> <span data-ttu-id="605bf-146">針對可能發生的後續相關交易則無任何補償。</span><span class="sxs-lookup"><span data-stu-id="605bf-146">There is no compensation for the subsequent dependent transactions that can occur.</span></span> <span data-ttu-id="605bf-147">不過，交易界限將被接受，而交易中的所有動作都會經過認可，或於發生衝突時回復。</span><span class="sxs-lookup"><span data-stu-id="605bf-147">However, transaction boundaries are honored and all the actions within a transaction are either committed, or in the case of a conflict, rolled back.</span></span>  
  
### <a name="publisher-wins-and-the-subscription-is-reinitialized"></a><span data-ttu-id="605bf-148">發行者優先且重新初始化訂閱</span><span class="sxs-lookup"><span data-stu-id="605bf-148">Publisher Wins and the Subscription Is Reinitialized</span></span>  
 <span data-ttu-id="605bf-149">重新初始化訂閱者來解決衝突，可以維護訂閱者的交易一致性，不過若發行集包含大量的資料，就會耗費大量時間。</span><span class="sxs-lookup"><span data-stu-id="605bf-149">Reinitializing the Subscriber to resolve conflicts maintains strict transactional consistency at the Subscriber, but it can be time consuming if the publication contains large amounts of data.</span></span>  
  
 <span data-ttu-id="605bf-150">當「佇列讀取器代理程式」偵測到衝突，佇列中所有剩餘交易 (包括衝突中的交易) 會遭到拒絕，而且訂閱者會標示著重新初始化。</span><span class="sxs-lookup"><span data-stu-id="605bf-150">When the Queue Reader Agent detects a conflict, all remaining transactions in the queue (including the transaction in conflict) are rejected, and the Subscriber is marked for reinitialization.</span></span> <span data-ttu-id="605bf-151">為發行集產生的下一個快照集是由「散發代理程式」套用到訂閱者。</span><span class="sxs-lookup"><span data-stu-id="605bf-151">The next snapshot generated for the publication is applied by the Distribution Agent to the Subscriber.</span></span>  
  
### <a name="subscriber-wins"></a><span data-ttu-id="605bf-152">訂閱者優先</span><span class="sxs-lookup"><span data-stu-id="605bf-152">Subscriber Wins</span></span>  
 <span data-ttu-id="605bf-153">訂閱者優先原則下的衝突偵測意謂最後要更新訂閱者優先的訂閱者交易。</span><span class="sxs-lookup"><span data-stu-id="605bf-153">Conflict detection under the Subscriber wins policy means the last Subscriber transaction to update the Publisher wins.</span></span> <span data-ttu-id="605bf-154">在此狀況下，當偵測到衝突的時候，仍然會使用訂閱者傳送的交易並且會更新發行者。</span><span class="sxs-lookup"><span data-stu-id="605bf-154">In this case, when a conflict is detected, the transaction sent by the Subscriber is still used and the Publisher is updated.</span></span> <span data-ttu-id="605bf-155">此原則適用於類似變更無法符合資料完整性的應用程式。</span><span class="sxs-lookup"><span data-stu-id="605bf-155">This policy is suitable for applications where such changes do not compromise data integrity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="605bf-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="605bf-156">See Also</span></span>  
 [<span data-ttu-id="605bf-157">Updatable Subscriptions for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="605bf-157">Updatable Subscriptions for Transactional Replication</span></span>](updatable-subscriptions-for-transactional-replication.md)  
  
  
