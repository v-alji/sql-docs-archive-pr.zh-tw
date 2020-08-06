---
title: 重新發行資料 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- republishing data
- publishing [SQL Server replication], Subscribers
- Subscribers [SQL Server replication], republishing data
ms.assetid: a1485cf4-b1c4-49e9-ab06-8ccfaad998f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f1e4213266121b3bf55bf2857e15f71f1e94e301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585262"
---
# <a name="republish-data"></a><span data-ttu-id="358d5-102">重新發行資料</span><span class="sxs-lookup"><span data-stu-id="358d5-102">Republish Data</span></span>
  <span data-ttu-id="358d5-103">在重新發行模式中，「發行者」傳送資料到「訂閱者」，「訂閱者」再將資料重新發行給任何數量的「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="358d5-103">In a republishing model, the Publisher sends data to a Subscriber, which then republishes the data to any number of other Subscribers.</span></span> <span data-ttu-id="358d5-104">當「發行者」必須透過緩慢或昂貴的通訊連結傳送資料到「訂閱者」時，這就很有用。</span><span class="sxs-lookup"><span data-stu-id="358d5-104">This is useful when a Publisher must send data to Subscribers over a slow or expensive communications link.</span></span> <span data-ttu-id="358d5-105">如果在該連結的遠端有許多「訂閱者」，可使用發行「訂閱者」來將大量散發負載移位到連結的那一端。</span><span class="sxs-lookup"><span data-stu-id="358d5-105">If there are a number of Subscribers on the far side of that link, using a republisher shifts the bulk of the distribution load to that side of the link.</span></span>  
  
 <span data-ttu-id="358d5-106">重新發行資料包括以下步驟：</span><span class="sxs-lookup"><span data-stu-id="358d5-106">Republishing data involves the following steps:</span></span>  
  
1.  <span data-ttu-id="358d5-107">在「發行者」端建立發行集。</span><span class="sxs-lookup"><span data-stu-id="358d5-107">Create a publication at the Publisher.</span></span>  
  
2.  <span data-ttu-id="358d5-108">為要重新發行的「訂閱者」建立發行集的訂閱。</span><span class="sxs-lookup"><span data-stu-id="358d5-108">Create a subscription to the publication for the republishing Subscriber.</span></span>  
  
3.  <span data-ttu-id="358d5-109">初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="358d5-109">Initialize the subscription.</span></span> <span data-ttu-id="358d5-110">必須先初始化訂閱，然後才能在重新發行「訂閱者」時建立發行集，否則複寫將會失敗。</span><span class="sxs-lookup"><span data-stu-id="358d5-110">The subscription must be initialized before the publication is created at the republishing Subscriber, or replication will fail.</span></span>  
  
4.  <span data-ttu-id="358d5-111">在要重新發行的「訂閱者」端的訂閱資料庫中建立發行集。</span><span class="sxs-lookup"><span data-stu-id="358d5-111">Create a publication in the subscription database at the republishing Subscriber.</span></span>  
  
5.  <span data-ttu-id="358d5-112">在要重新發行的「訂閱者」端為其他「訂閱者」建立發行集的訂閱。</span><span class="sxs-lookup"><span data-stu-id="358d5-112">Create subscriptions to the publication at the republishing Subscriber for the other Subscribers.</span></span>  
  
6.  <span data-ttu-id="358d5-113">初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="358d5-113">Initialize the subscriptions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="358d5-114">如果在重新發行的拓撲中使用合併式複寫，則所有重新發行「訂閱者」均必須使用伺服器訂閱。</span><span class="sxs-lookup"><span data-stu-id="358d5-114">If you use merge replication in a republishing topology, all republishing Subscribers must use server subscriptions.</span></span> <span data-ttu-id="358d5-115">如需訂閱類型的詳細資訊，請參閱[訂閱發行集](subscribe-to-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="358d5-115">For more information about subscription types, see [Subscribe to Publications](subscribe-to-publications.md).</span></span>  
  
 <span data-ttu-id="358d5-116">在下圖中，「發行者」與重新發行者都扮演其各自的本機「散發者」角色。</span><span class="sxs-lookup"><span data-stu-id="358d5-116">In the following illustration, both the Publisher and the republisher are acting as their own local Distributors.</span></span> <span data-ttu-id="358d5-117">如果都設定為使用遠端「散發者」，每個「散發者」就必須如自己的「發行者」一樣，全部都在緩慢或昂貴通訊連結的同一邊。</span><span class="sxs-lookup"><span data-stu-id="358d5-117">If each were set up to use a remote Distributor, each Distributor would need to be on the same side of the slow or expensive communications link as its Publisher.</span></span> <span data-ttu-id="358d5-118">「發行者」必須透過可靠、高速的通訊連結以連接到遠端「散發者」。</span><span class="sxs-lookup"><span data-stu-id="358d5-118">Publishers must be connected to remote Distributors by reliable, high-speed communications links.</span></span>  
  
 <span data-ttu-id="358d5-119">![重新發佈資料](media/repl-06a.gif "重新發佈資料")</span><span class="sxs-lookup"><span data-stu-id="358d5-119">![Republishing data](media/repl-06a.gif "Republishing data")</span></span>  
  
 <span data-ttu-id="358d5-120">任何伺服器都可以同時扮演「發行者」與「訂閱者」的角色。</span><span class="sxs-lookup"><span data-stu-id="358d5-120">Any server can act as both a Publisher and Subscriber.</span></span> <span data-ttu-id="358d5-121">例如，假設下圖中位於英國倫敦，而且必須散發到美國四個不同城市的資料表發行集：芝加哥、紐約、聖地牙哥和西雅圖。</span><span class="sxs-lookup"><span data-stu-id="358d5-121">For example, consider the following diagram in which a publication of a table exists in London and must be distributed to four different cities in the United States: Chicago, New York, San Diego, and Seattle.</span></span> <span data-ttu-id="358d5-122">位於紐約的伺服器將被選來訂閱在倫敦產生的發行資料表，因為紐約網站符合這些條件：</span><span class="sxs-lookup"><span data-stu-id="358d5-122">The server in New York is chosen to subscribe to the published table originating in London, because the New York site meets these conditions:</span></span>  
  
-   <span data-ttu-id="358d5-123">到倫敦的網路連結相當可靠。</span><span class="sxs-lookup"><span data-stu-id="358d5-123">The network link back to London is relatively reliable.</span></span>  
  
-   <span data-ttu-id="358d5-124">倫敦到紐約的通訊成本是可以接受的。</span><span class="sxs-lookup"><span data-stu-id="358d5-124">The London-to-New York communication costs are acceptable.</span></span>  
  
-   <span data-ttu-id="358d5-125">從紐約到所有其他美國訂閱者網站有相當好的網路通訊線路。</span><span class="sxs-lookup"><span data-stu-id="358d5-125">There are good network communications lines from New York to all other Subscriber sites in the United States.</span></span>  
  
     <span data-ttu-id="358d5-126">![重新發佈資料至分散的位置](media/repl-06.gif "重新發佈資料至分散的位置")</span><span class="sxs-lookup"><span data-stu-id="358d5-126">![Republishing data to dispersed locations](media/repl-06.gif "Republishing data to dispersed locations")</span></span>  
  
 <span data-ttu-id="358d5-127">複寫支援下表所示的重新發行案例。</span><span class="sxs-lookup"><span data-stu-id="358d5-127">Replication supports the republishing scenarios shown in the following table.</span></span>  
  
|<span data-ttu-id="358d5-128">發行者</span><span class="sxs-lookup"><span data-stu-id="358d5-128">Publisher</span></span>|<span data-ttu-id="358d5-129">發行訂閱者</span><span class="sxs-lookup"><span data-stu-id="358d5-129">Publishing Subscriber</span></span>|<span data-ttu-id="358d5-130">用戶</span><span class="sxs-lookup"><span data-stu-id="358d5-130">Subscriber</span></span>|  
|---------------|---------------------------|----------------|  
|<span data-ttu-id="358d5-131">交易式發行集</span><span class="sxs-lookup"><span data-stu-id="358d5-131">Transactional publication</span></span>|<span data-ttu-id="358d5-132">交易式訂閱/交易式發行集</span><span class="sxs-lookup"><span data-stu-id="358d5-132">Transactional subscription/transactional publication</span></span>|<span data-ttu-id="358d5-133">交易式訂閱</span><span class="sxs-lookup"><span data-stu-id="358d5-133">Transactional subscription</span></span>|  
|<span data-ttu-id="358d5-134">交易式發行集</span><span class="sxs-lookup"><span data-stu-id="358d5-134">Transactional publication</span></span>|<span data-ttu-id="358d5-135">交易式訂閱/合併式發行集<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="358d5-135">Transactional subscription/merge publication<sup>1</sup></span></span>|<span data-ttu-id="358d5-136">合併訂閱</span><span class="sxs-lookup"><span data-stu-id="358d5-136">Merge subscription</span></span>|  
|<span data-ttu-id="358d5-137">合併式發行集</span><span class="sxs-lookup"><span data-stu-id="358d5-137">Merge publication</span></span>|<span data-ttu-id="358d5-138">合併訂閱/合併式發行集</span><span class="sxs-lookup"><span data-stu-id="358d5-138">Merge subscription/merge publication</span></span>|<span data-ttu-id="358d5-139">合併訂閱</span><span class="sxs-lookup"><span data-stu-id="358d5-139">Merge subscription</span></span>|  
|<span data-ttu-id="358d5-140">合併式發行集</span><span class="sxs-lookup"><span data-stu-id="358d5-140">Merge publication</span></span>|<span data-ttu-id="358d5-141">合併訂閱/交易式發行集</span><span class="sxs-lookup"><span data-stu-id="358d5-141">Merge subscription/transactional publication</span></span>|<span data-ttu-id="358d5-142">交易式訂閱</span><span class="sxs-lookup"><span data-stu-id="358d5-142">Transactional subscription</span></span>|  
  
 <span data-ttu-id="358d5-143"><sup>1</sup>您應該設定合併式發行集的 `@published_in_tran_pub` 屬性。</span><span class="sxs-lookup"><span data-stu-id="358d5-143"><sup>1</sup>You should set the `@published_in_tran_pub` property on the merge publication.</span></span> <span data-ttu-id="358d5-144">依預設，異動複寫預期於訂閱者端的資料表會被視為唯讀資料表。</span><span class="sxs-lookup"><span data-stu-id="358d5-144">By default, transactional replication expects tables at the Subscriber to be treated as read-only.</span></span> <span data-ttu-id="358d5-145">如果合併式複寫變更交易式訂閱中資料表的資料，就可能導致資料無法聚合。</span><span class="sxs-lookup"><span data-stu-id="358d5-145">If merge replication makes data changes to a table in a transactional subscription, non-convergence of data can occur.</span></span> <span data-ttu-id="358d5-146">若要避免此風險，建議合併式發行集中的任何此類資料表應指定為僅限下載。</span><span class="sxs-lookup"><span data-stu-id="358d5-146">To avoid this risk, we recommend that any such table be specified as download-only in the merge publication.</span></span> <span data-ttu-id="358d5-147">這會防止合併式訂閱者將資料變更上傳至資料表。</span><span class="sxs-lookup"><span data-stu-id="358d5-147">This prevents a merge Subscriber from uploading data changes to the table.</span></span> <span data-ttu-id="358d5-148">如需詳細資訊，請參閱[使用僅限下載的發行項最佳化合併式複寫效能](merge/optimize-merge-replication-performance-with-download-only-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="358d5-148">For more information, see [Optimize Merge Replication Performance with Download-Only Articles](merge/optimize-merge-replication-performance-with-download-only-articles.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="358d5-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="358d5-149">See Also</span></span>  
 <span data-ttu-id="358d5-150">[[設定散發]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="358d5-150">[Configure Distribution](configure-distribution.md) </span></span>  
 <span data-ttu-id="358d5-151">[發行資料和資料庫物件](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="358d5-151">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="358d5-152">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="358d5-152">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 <span data-ttu-id="358d5-153">[初始化訂閱](initialize-a-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="358d5-153">[Initialize a Subscription](initialize-a-subscription.md) </span></span>  
 [<span data-ttu-id="358d5-154">同步處理資料</span><span class="sxs-lookup"><span data-stu-id="358d5-154">Synchronize Data</span></span>](synchronize-data.md)  
  
  
