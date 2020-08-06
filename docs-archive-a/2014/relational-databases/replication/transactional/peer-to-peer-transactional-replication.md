---
title: 點對點異動複寫 | Microsoft Docs
ms.custom: ''
ms.date: 08/29/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- bidirectional replication
- transactional replication, bidirectional replication
- bidirectional transactional replication
- transactional replication, peer-to-peer replication
- peer-to-peer transactional replication
ms.assetid: 23e7e8c1-002f-4e69-8c99-d63e4100de64
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f61db9a8e7cecb107fd1b27fae966d133e043c8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596632"
---
# <a name="peer-to-peer-transactional-replication"></a><span data-ttu-id="b792f-102">@loopback_detection</span><span class="sxs-lookup"><span data-stu-id="b792f-102">Peer-to-Peer Transactional Replication</span></span>
  <span data-ttu-id="b792f-103">點對點複寫藉由維護多個伺服器執行個體之間的資料複本 (也稱為 *「節點」* ) 來提供向外延展和高可用性解決方案。</span><span class="sxs-lookup"><span data-stu-id="b792f-103">Peer-to-peer replication provides a scale-out and high-availability solution by maintaining copies of data across multiple server instances, also referred to as *nodes*.</span></span> <span data-ttu-id="b792f-104">點對點複寫是以異動複寫為基礎，會以接近即時、交易式的方式傳播一致的變更。</span><span class="sxs-lookup"><span data-stu-id="b792f-104">Built on the foundation of transactional replication, peer-to-peer replication propagates transactionally consistent changes in near real-time.</span></span> <span data-ttu-id="b792f-105">如此可讓需要向外延展讀取作業的應用程式將來自用戶端的讀取散發到多個節點之間。</span><span class="sxs-lookup"><span data-stu-id="b792f-105">This enables applications that require scale-out of read operations to distribute the reads from clients across multiple nodes.</span></span> <span data-ttu-id="b792f-106">由於會以接近即時的方式在節點之間維護資料，所以點對點複寫會提供資料備援性，這樣可提高資料的可用性。</span><span class="sxs-lookup"><span data-stu-id="b792f-106">Because data is maintained across the nodes in near real-time, peer-to-peer replication provides data redundancy, which increases the availability of data.</span></span>  
  
 <span data-ttu-id="b792f-107">請考慮 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b792f-107">Consider a Web application.</span></span> <span data-ttu-id="b792f-108">這樣會在以下方面因為點對點複寫而獲益：</span><span class="sxs-lookup"><span data-stu-id="b792f-108">This can benefit from peer-to-peer replication in the following ways:</span></span>  
  
-   <span data-ttu-id="b792f-109">目錄查詢和其他讀取會在多個節點之間散發。</span><span class="sxs-lookup"><span data-stu-id="b792f-109">Catalog queries and other reads are spread across multiple nodes.</span></span> <span data-ttu-id="b792f-110">如此可在讀取數目增加時，讓效能維持一致。</span><span class="sxs-lookup"><span data-stu-id="b792f-110">This enables performance to remain consistent as reads increase.</span></span>  
  
-   <span data-ttu-id="b792f-111">如果系統中的其中一個節點失敗，應用程式層就可以將該節點的寫入重新導向另一個節點，</span><span class="sxs-lookup"><span data-stu-id="b792f-111">If one of the nodes in the system fails, an application layer can redirect the writes for that node to another node.</span></span> <span data-ttu-id="b792f-112">這樣會維護可用性。</span><span class="sxs-lookup"><span data-stu-id="b792f-112">This maintains availability.</span></span>  
  
-   <span data-ttu-id="b792f-113">如果節點需要維護或是整個系統需要升級，可以讓每一個節點離線工作，然後再加回系統中，而不會影響應用程式的可用性。</span><span class="sxs-lookup"><span data-stu-id="b792f-113">If a node requires maintenance or the whole system requires an upgrade, each node can be taken offline and added back to the system without affecting the availability of the application.</span></span>  
  
 <span data-ttu-id="b792f-114">雖然點對點複寫可向外延展讀取作業，但是拓撲的效能會類似於單一節點的效能。</span><span class="sxs-lookup"><span data-stu-id="b792f-114">Although peer-to-peer replication enables scaling out of read operations, write performance for the topology is like that for a single node.</span></span> <span data-ttu-id="b792f-115">這是因為在最後，所有的插入、更新和刪除都會傳播到所有節點。</span><span class="sxs-lookup"><span data-stu-id="b792f-115">This is because ultimately all inserts, updates, and deletes are propagated to all nodes.</span></span> <span data-ttu-id="b792f-116">當有變更套用到給定節點時，複寫可加以辨識，並防止變更在各節點間循環多次。</span><span class="sxs-lookup"><span data-stu-id="b792f-116">Replication recognizes when a change has been applied to a given node and prevents changes from cycling through the nodes more than one time.</span></span> <span data-ttu-id="b792f-117">基於以下原因，我們強烈建議您最好只在節點上執行每一個資料列的寫入作業：</span><span class="sxs-lookup"><span data-stu-id="b792f-117">We strongly recommend that write operations for each row be performed at only node, for the following reasons:</span></span>  
  
-   <span data-ttu-id="b792f-118">如果在一個以上的節點上修改資料列，它可能會在此資料列傳播到其他節點時，造成衝突或甚至是遺失更新。</span><span class="sxs-lookup"><span data-stu-id="b792f-118">If a row is modified at more than one node, it can cause a conflict or even a lost update when the row is propagated to other nodes.</span></span>  
  
-   <span data-ttu-id="b792f-119">在複寫變更時，一定會牽涉到某些延遲。</span><span class="sxs-lookup"><span data-stu-id="b792f-119">There is always some latency involved when changes are replicated.</span></span> <span data-ttu-id="b792f-120">如果是需要立即看到最近變更的應用程式，在多個節點之間對應用程式動態進行負載平衡可能會發生問題。</span><span class="sxs-lookup"><span data-stu-id="b792f-120">For applications that require the latest change to be seen immediately, dynamically load balancing the application across multiple nodes can be problematic.</span></span>  
  
 <span data-ttu-id="b792f-121">點對點複寫包含了可在點對點拓撲之間啟用衝突偵測的選項，</span><span class="sxs-lookup"><span data-stu-id="b792f-121">Peer-to-peer replication includes the option to enable conflict detection across a peer-to-peer topology.</span></span> <span data-ttu-id="b792f-122">這個選項可避免因為未偵測到的衝突所導致的問題，包括不一致的應用程式行為和遺失更新。</span><span class="sxs-lookup"><span data-stu-id="b792f-122">This option helps prevent the issues that are caused from undetected conflicts, including inconsistent application behavior and lost updates.</span></span> <span data-ttu-id="b792f-123">啟用這個選項時，預設會將衝突的變更視為造成散發代理程式失敗的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="b792f-123">By enabling this option, by default a conflicting change is treated as a critical error that causes the failure of the Distribution Agent.</span></span> <span data-ttu-id="b792f-124">在發生衝突時，此拓撲會維持不一致的狀態，直到以手動方式解決衝突並讓拓撲之間的資料變成一致為止。</span><span class="sxs-lookup"><span data-stu-id="b792f-124">In the event of a conflict, the topology remains in an inconsistent state until the conflict is resolved manually and the data is made consistent across the topology.</span></span> <span data-ttu-id="b792f-125">如需相關資訊，請參閱 [Conflict Detection in Peer-to-Peer Replication](peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="b792f-125">For more information, see [Conflict Detection in Peer-to-Peer Replication](peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b792f-126">若要避免潛在的資料不一致問題，請務必要避免發生點對點拓撲中的衝突，即使是啟用了衝突偵測也一樣。</span><span class="sxs-lookup"><span data-stu-id="b792f-126">To avoid potential data inconsistency, make sure that you avoid conflicts in a peer-to-peer topology, even with conflict detection enabled.</span></span> <span data-ttu-id="b792f-127">若要確定只在一個節點上執行特定資料列的寫入作業，存取和變更資料的應用程式必須分割插入、更新和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="b792f-127">To ensure that write operations for a particular row are performed at only one node, applications that access and change data must partition insert, update, and delete operations.</span></span> <span data-ttu-id="b792f-128">這樣的分割可確保，從一個節點對給定資料列的修改會在其他節點修改該資料列之前，與拓撲中的所有其他節點同步處理。</span><span class="sxs-lookup"><span data-stu-id="b792f-128">This partitioning ensures that modifications to a given row originating at one node are synchronized with all other nodes in the topology before the row is modified by a different node.</span></span> <span data-ttu-id="b792f-129">如果應用程式需要複雜的衝突偵測與解決功能，請使用合併式複寫。</span><span class="sxs-lookup"><span data-stu-id="b792f-129">If an application requires sophisticated conflict detection and resolution capabilities, use merge replication.</span></span> <span data-ttu-id="b792f-130">如需詳細資訊，請參閱[合併式複寫](../merge/merge-replication.md)和[偵測及解決合併式複寫衝突](../merge/advanced-merge-replication-conflict-detection-and-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="b792f-130">For more information, see [Merge Replication](../merge/merge-replication.md) and [Detect and Resolve Merge Replication Conflicts](../merge/advanced-merge-replication-conflict-detection-and-resolution.md).</span></span>  
  
## <a name="peer-to-peer-topologies"></a><span data-ttu-id="b792f-131">點對點拓撲</span><span class="sxs-lookup"><span data-stu-id="b792f-131">Peer-to-Peer Topologies</span></span>  
 <span data-ttu-id="b792f-132">以下案例說明點對點複寫的一般用法。</span><span class="sxs-lookup"><span data-stu-id="b792f-132">The following scenarios illustrate typical uses for peer-to-peer replication.</span></span>  
  
### <a name="topology-that-has-two-participating-databases"></a><span data-ttu-id="b792f-133">有兩個參與資料庫的拓撲</span><span class="sxs-lookup"><span data-stu-id="b792f-133">Topology That Has Two Participating Databases</span></span>  
 <span data-ttu-id="b792f-134">![點對點複寫，兩個節點](../media/repl-multinode-01.gif "點對點複寫，兩個節點")</span><span class="sxs-lookup"><span data-stu-id="b792f-134">![Peer-to-peer replication, two nodes](../media/repl-multinode-01.gif "Peer-to-peer replication, two nodes")</span></span>  
  
 <span data-ttu-id="b792f-135">上面的兩個圖都顯示兩個參與資料庫，而且使用者傳輸量會透過應用程式伺服器導向資料庫。</span><span class="sxs-lookup"><span data-stu-id="b792f-135">Both of the preceding illustrations show two participating databases, with user traffic directed to the databases through an application server.</span></span> <span data-ttu-id="b792f-136">這種組態可用於從網站到工作群組應用程式的各種應用程式，且具有下列優點：</span><span class="sxs-lookup"><span data-stu-id="b792f-136">This configuration can be used for a variety of applications, from Web sites to workgroup applications, and provides the following benefits:</span></span>  
  
-   <span data-ttu-id="b792f-137">提升讀取效能，因為讀取會在兩台伺服器間展開。</span><span class="sxs-lookup"><span data-stu-id="b792f-137">Improved read performance, because reads are spread out over two servers.</span></span>  
  
-   <span data-ttu-id="b792f-138">在需要維護或一個節點失敗時具有更高的可用性。</span><span class="sxs-lookup"><span data-stu-id="b792f-138">Higher availability if maintenance is required or in case of failure at one node.</span></span>  
  
 <span data-ttu-id="b792f-139">在兩個圖例中，讀取活動在參與的資料庫間均負載平衡，但對更新的處理方式有所不同：</span><span class="sxs-lookup"><span data-stu-id="b792f-139">In both illustrations, read activity is load-balanced between the participating databases, but updates are handled differently:</span></span>  
  
-   <span data-ttu-id="b792f-140">在左側，會在兩個伺服器之間分割更新。</span><span class="sxs-lookup"><span data-stu-id="b792f-140">On the left, updates are partitioned between the two servers.</span></span> <span data-ttu-id="b792f-141">舉例來說，如果資料庫包含產品目錄，您可以讓一個自訂應用程式將名稱以 A 到 M 開頭之產品的更新導向節點 **A** ，將名稱以 N 到 Z 開頭之產品的更新導向節點 **B** 。隨後，更新會再複寫到其他節點。</span><span class="sxs-lookup"><span data-stu-id="b792f-141">If the database contained a product catalog, you could, for example, have a custom application direct updates to node **A** for product names that start with A through M, and direct updates to node **B** for product names that start with N through Z. Updates are then replicated to the other node.</span></span>  
  
-   <span data-ttu-id="b792f-142">在右側，所有的更新都會導向節點 **B**。更新會從這裡複寫到節點 **A**。如果 **B** 離線 (例如，為了進行維護)，應用程式伺服器就可以將所有活動導向 **A**。當 **B** 再次連線時，更新可以流向它，而且應用程式伺服器可將所有更新移回 **B**，或是繼續將更新導向 **A**。</span><span class="sxs-lookup"><span data-stu-id="b792f-142">On the right, all updates are directed to node **B**. From there, updates are replicated to node **A**. If **B** is offline (for example, for maintenance), the application server can direct all activity to **A**. When **B** is back online, updates can flow to it, and the application server can move all updates back to **B** or keep directing them to **A**.</span></span>  
  
 <span data-ttu-id="b792f-143">點對點複寫對以上兩種方法均支援，但是右側的中央更新範例也經常與標準異動複寫一起使用。</span><span class="sxs-lookup"><span data-stu-id="b792f-143">Peer-to-peer replication can support either approach, but the central update example on the right is also often used with standard transactional replication.</span></span>  
  
### <a name="topologies-that-have-three-or-more-participating-databases"></a><span data-ttu-id="b792f-144">有三個或更多參與資料庫的拓撲</span><span class="sxs-lookup"><span data-stu-id="b792f-144">Topologies That Have Three or More Participating Databases</span></span>  
 <span data-ttu-id="b792f-145">![點對點複寫至分散的位置](../media/repl-multinode-02.gif "點對點複寫至分散的位置")</span><span class="sxs-lookup"><span data-stu-id="b792f-145">![Peer-to-peer replication to dispersed locations](../media/repl-multinode-02.gif "Peer-to-peer replication to dispersed locations")</span></span>  
  
 <span data-ttu-id="b792f-146">上圖顯示為一家全球軟體支援公司提供資料的三個參與資料庫，其分公司分別設在洛杉磯、倫敦和台北。</span><span class="sxs-lookup"><span data-stu-id="b792f-146">The preceding illustration shows three participating databases that provide data for a worldwide software support organization, with offices in Los Angeles, London, and Taipei.</span></span> <span data-ttu-id="b792f-147">每個辦事處的支援工程師都會接聽客戶來電，同時輸入並更新每一個客戶來電的資訊。</span><span class="sxs-lookup"><span data-stu-id="b792f-147">The support engineers at each office take customer calls and enter and update information about each customer call.</span></span> <span data-ttu-id="b792f-148">這三個分公司的時差為八小時，這樣工作日就不會有重疊。</span><span class="sxs-lookup"><span data-stu-id="b792f-148">The time zones for the three offices are eight hours apart, so there is no overlap in the workday.</span></span> <span data-ttu-id="b792f-149">當台北分公司下班時，倫敦分公司就開始一天的工作。</span><span class="sxs-lookup"><span data-stu-id="b792f-149">As the Taipei office closes, the London office is opening for the day.</span></span> <span data-ttu-id="b792f-150">如果當一個辦事處即將下班時仍有來電，則來電將轉到將開始工作的下一個辦事處的代表那裡。</span><span class="sxs-lookup"><span data-stu-id="b792f-150">If a call is still in progress as one office is closing, the call is transferred to a representative at the next office to open.</span></span>  
  
 <span data-ttu-id="b792f-151">每一處都有資料庫和應用程式伺服器，供支援工程師輸入並更新有關客戶來電的資訊。</span><span class="sxs-lookup"><span data-stu-id="b792f-151">Each location has a database and an application server, which are used by the support engineers as they enter and update information about customer calls.</span></span> <span data-ttu-id="b792f-152">此拓撲是依時間分割，</span><span class="sxs-lookup"><span data-stu-id="b792f-152">The topology is partitioned by time.</span></span> <span data-ttu-id="b792f-153">因此更新就只會發生在目前正在營業的節點，隨後更新會流向其他參與資料庫。</span><span class="sxs-lookup"><span data-stu-id="b792f-153">Therefore, updates occur only at the node that is currently open for business, and then the updates flow to the other participating databases.</span></span> <span data-ttu-id="b792f-154">此拓撲具有下列優點：</span><span class="sxs-lookup"><span data-stu-id="b792f-154">This topology provides the following benefits:</span></span>  
  
-   <span data-ttu-id="b792f-155">獨立而不隔離：每一個分公司都可以獨立插入、更新或刪除資料，且還可以共用資料，因為資料會複寫到所有其他的參與資料庫。</span><span class="sxs-lookup"><span data-stu-id="b792f-155">Independence without isolation: Each office can insert, update, or delete data independently but can also share the data because it is replicated to all other participating databases.</span></span>  
  
-   <span data-ttu-id="b792f-156">在發生失敗或要允許對一或多個參與資料庫進行維護時，具有更高的可用性。</span><span class="sxs-lookup"><span data-stu-id="b792f-156">Higher availability in case of failure or to allow maintenance at one or more of the participating databases.</span></span>  
  
     <span data-ttu-id="b792f-157">![點對點複寫，三或四個節點](../media/repl-multinode-04.gif "點對點複寫，三或四個節點")</span><span class="sxs-lookup"><span data-stu-id="b792f-157">![Peer-to-peer replication, three and four nodes](../media/repl-multinode-04.gif "Peer-to-peer replication, three and four nodes")</span></span>  
  
 <span data-ttu-id="b792f-158">上圖顯示如何將節點加入到三個節點的拓撲。</span><span class="sxs-lookup"><span data-stu-id="b792f-158">The preceding illustration shows the addition of a node to the three-node topology.</span></span> <span data-ttu-id="b792f-159">基於以下原因，可以在此案例中加入節點：</span><span class="sxs-lookup"><span data-stu-id="b792f-159">A node could be added in this scenario for the following reasons:</span></span>  
  
-   <span data-ttu-id="b792f-160">因為另一個辦事處已開始上班。</span><span class="sxs-lookup"><span data-stu-id="b792f-160">Because another office is opened.</span></span>  
  
-   <span data-ttu-id="b792f-161">在發生磁碟錯誤或其他重大失敗時，提供更高的可用性來支援維護或增加容錯功能。</span><span class="sxs-lookup"><span data-stu-id="b792f-161">To provide higher availability to support maintenance or increase fault tolerance if a disk failure or other major failure occurs.</span></span>  
  
 <span data-ttu-id="b792f-162">請注意在具有三個或四個節點的拓撲中，所有的資料庫都會發行及訂閱所有其他資料庫。</span><span class="sxs-lookup"><span data-stu-id="b792f-162">Notice that in both the three- and four-node topologies, all databases publish and subscribe to all other databases.</span></span> <span data-ttu-id="b792f-163">這樣會在有維護需求或是其中一或多個節點失敗時，提供最大的可用性。</span><span class="sxs-lookup"><span data-stu-id="b792f-163">This provides maximum availability in case of maintenance needs or failure of one or more nodes.</span></span> <span data-ttu-id="b792f-164">新增節點後，您必須針對效能以及部署與管理的複雜度來平衡可用性和延展性。</span><span class="sxs-lookup"><span data-stu-id="b792f-164">As nodes are added, you must balance availability and scalability needs against performance and the complexity of deployment and administration.</span></span>  
  
## <a name="configuring-peer-to-peer-replication"></a><span data-ttu-id="b792f-165">設定點對點異動複寫</span><span class="sxs-lookup"><span data-stu-id="b792f-165">Configuring Peer-to-Peer Replication</span></span>  
 <span data-ttu-id="b792f-166">設定點對點複寫拓撲與設定一系列標準交易式發行集和訂閱類似。</span><span class="sxs-lookup"><span data-stu-id="b792f-166">Configuring a peer-to-peer replication topology is very similar to configuring a series of standard transactional publications and subscriptions.</span></span> <span data-ttu-id="b792f-167">以下主題中的步驟顯示三節點系統的組態，與顯示點對點拓撲的上圖左側組態類似。</span><span class="sxs-lookup"><span data-stu-id="b792f-167">The steps described in the following topics show the configuration of a three-node system, similar to the configuration shown on the left in the previous illustration that shows peer-to-peer topology.</span></span>  
  
## <a name="considerations-for-using-peer-to-peer-replication"></a><span data-ttu-id="b792f-168">使用點對點複寫的考量</span><span class="sxs-lookup"><span data-stu-id="b792f-168">Considerations for Using Peer-to-Peer Replication</span></span>  
 <span data-ttu-id="b792f-169">本章節提供在您使用點對點複寫時，所要考量的資訊與指導方針。</span><span class="sxs-lookup"><span data-stu-id="b792f-169">This section provides information and guidelines to consider when you use peer-to-peer replication.</span></span>  
  
### <a name="general-considerations"></a><span data-ttu-id="b792f-170">一般考量</span><span class="sxs-lookup"><span data-stu-id="b792f-170">General Considerations</span></span>  
  
-   <span data-ttu-id="b792f-171">點對點複寫只適用於 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的 Enterprise 版本。</span><span class="sxs-lookup"><span data-stu-id="b792f-171">Peer-to-peer replication is available only in Enterprise versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="b792f-172">參與點對點複寫的所有資料庫都應該包含相同的結構描述和資料：</span><span class="sxs-lookup"><span data-stu-id="b792f-172">All databases that participate in peer-to-peer replication should contain identical schema and data:</span></span>  
  
    -   <span data-ttu-id="b792f-173">物件名稱、物件結構描述和發行集名稱都應相同。</span><span class="sxs-lookup"><span data-stu-id="b792f-173">Object names, object schema, and publication names should be identical.</span></span>  
  
    -   <span data-ttu-id="b792f-174">發行集必須允許複寫結構描述變更</span><span class="sxs-lookup"><span data-stu-id="b792f-174">Publications must allow schema changes to be replicated.</span></span> <span data-ttu-id="b792f-175">(這是發行集屬性 **replicate_ddl** 的 **1** 設定值，這是預設值)。如需詳細資訊，請參閱[對發行集資料庫進行結構描述變更](../publish/make-schema-changes-on-publication-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="b792f-175">(This is a setting of **1** for the publication property **replicate_ddl**, which is the default setting.) For more information, see [Make Schema Changes on Publication Databases](../publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
    -   <span data-ttu-id="b792f-176">不支援資料列和資料行篩選。</span><span class="sxs-lookup"><span data-stu-id="b792f-176">Row and column filtering are not supported.</span></span>  
  
-   <span data-ttu-id="b792f-177">我們建議您最好讓每一個節點都使用它自己的散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="b792f-177">We recommend that each node use its own distribution database.</span></span> <span data-ttu-id="b792f-178">避免潛在的單一失敗點。</span><span class="sxs-lookup"><span data-stu-id="b792f-178">This eliminates the potential of having a single point of failure.</span></span>  
  
-   <span data-ttu-id="b792f-179">資料表與其他物件不能包含在單一發行集資料庫的多個點對點發行集中。</span><span class="sxs-lookup"><span data-stu-id="b792f-179">Tables and other objects cannot be included in multiple peer-to-peer publications in a single publication database.</span></span>  
  
-   <span data-ttu-id="b792f-180">在建立任何訂閱前，必須先啟用點對點複寫的發行集。</span><span class="sxs-lookup"><span data-stu-id="b792f-180">A publication must be enabled for peer-to-peer replication before any subscriptions are created.</span></span>  
  
-   <span data-ttu-id="b792f-181">訂閱必須使用備份或藉由 [僅支援複寫]  選項進行初始化。</span><span class="sxs-lookup"><span data-stu-id="b792f-181">Subscriptions must be initialized by using a backup or with the **'replication support only'** option.</span></span> <span data-ttu-id="b792f-182">如需詳細資訊，請參閱 [不使用快照集初始化交易式訂閱](../initialize-a-transactional-subscription-without-a-snapshot.md)中手動初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="b792f-182">For more information, see [Initialize a Transactional Subscription Without a Snapshot](../initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
-   <span data-ttu-id="b792f-183">我們不建議您使用識別欄位。</span><span class="sxs-lookup"><span data-stu-id="b792f-183">We do not recommend the use of identity columns.</span></span> <span data-ttu-id="b792f-184">使用識別時，您必須手動管理指派給每個參與資料庫中資料表的範圍。</span><span class="sxs-lookup"><span data-stu-id="b792f-184">When using identities, you must manually manage the ranges assigned to the tables at each participating database.</span></span> <span data-ttu-id="b792f-185">如需詳細資訊，請參閱[複寫識別資料行](../publish/replicate-identity-columns.md)中的＜為手動識別範圍管理指派範圍＞一節。</span><span class="sxs-lookup"><span data-stu-id="b792f-185">For more information, see the section "Assigning Ranges for Manual Identity Range Management" in [Replicate Identity Columns](../publish/replicate-identity-columns.md).</span></span>  
  
### <a name="feature-restrictions"></a><span data-ttu-id="b792f-186">功能限制</span><span class="sxs-lookup"><span data-stu-id="b792f-186">Feature Restrictions</span></span>  
 <span data-ttu-id="b792f-187">點對點複寫支援異動複寫的核心功能，但是不支援以下選項：</span><span class="sxs-lookup"><span data-stu-id="b792f-187">Peer-to-peer replication supports the core features of transactional replication, but does not support the following options:</span></span>  
  
-   <span data-ttu-id="b792f-188">使用快照集進行初始化和重新初始化。</span><span class="sxs-lookup"><span data-stu-id="b792f-188">Initialization and reinitialization with a snapshot.</span></span>  
  
-   <span data-ttu-id="b792f-189">資料列和資料行篩選。</span><span class="sxs-lookup"><span data-stu-id="b792f-189">Row and column filters.</span></span>  
  
-   <span data-ttu-id="b792f-190">時間戳記資料行。</span><span class="sxs-lookup"><span data-stu-id="b792f-190">Timestamp columns.</span></span>  
  
-   <span data-ttu-id="b792f-191">非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 發行者或訂閱者。</span><span class="sxs-lookup"><span data-stu-id="b792f-191">Non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Publishers and Subscribers.</span></span>  
  
-   <span data-ttu-id="b792f-192">立即更新和佇列更新訂閱。</span><span class="sxs-lookup"><span data-stu-id="b792f-192">Immediate updating and queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="b792f-193">匿名訂閱。</span><span class="sxs-lookup"><span data-stu-id="b792f-193">Anonymous subscriptions.</span></span>  
  
-   <span data-ttu-id="b792f-194">部分訂閱。</span><span class="sxs-lookup"><span data-stu-id="b792f-194">Partial subscriptions.</span></span>  
  
-   <span data-ttu-id="b792f-195">可附加訂閱與可轉換訂閱</span><span class="sxs-lookup"><span data-stu-id="b792f-195">Attachable subscriptions and transformable subscriptions.</span></span> <span data-ttu-id="b792f-196">(這兩個選項在 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]中都已被取代)。</span><span class="sxs-lookup"><span data-stu-id="b792f-196">(Both of these options were deprecated in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].)</span></span>  
  
-   <span data-ttu-id="b792f-197">共用的散發代理程式。</span><span class="sxs-lookup"><span data-stu-id="b792f-197">Shared Distribution Agents.</span></span>  
  
-   <span data-ttu-id="b792f-198">散發代理程式參數 **-SubscriptionStreams** 和記錄讀取器代理程式參數 **-MaxCmdsInTran**。</span><span class="sxs-lookup"><span data-stu-id="b792f-198">The Distribution Agent parameter **-SubscriptionStreams** and the Log Reader Agent parameter **-MaxCmdsInTran**.</span></span>  
  
-   <span data-ttu-id="b792f-199">發行項屬性\*\* \@ destination_owner**和** \@ destination_table\*\*。</span><span class="sxs-lookup"><span data-stu-id="b792f-199">The article properties **\@destination_owner** and **\@destination_table**.</span></span>  

-   <span data-ttu-id="b792f-200">點對點異動複寫不支援建立點對點發行集的單向交易式訂閱</span><span class="sxs-lookup"><span data-stu-id="b792f-200">Peer-to-Peer transactional replication does not support creating a one-way transactional subscription to a Peer-to-Peer publication</span></span>
  
 <span data-ttu-id="b792f-201">下列屬性有特殊考量：</span><span class="sxs-lookup"><span data-stu-id="b792f-201">The following properties have special considerations:</span></span>  
  
-   <span data-ttu-id="b792f-202">發行集屬性\*\* \@ allow_initialize_from_backup\*\*需要的值 `true` 。</span><span class="sxs-lookup"><span data-stu-id="b792f-202">The publication property **\@allow_initialize_from_backup** requires a value of `true`.</span></span>  
  
-   <span data-ttu-id="b792f-203">發行項屬性\*\* \@ replicate_ddl**需要的值 `true` 為;** \@ identityrangemanagementoption**需要的值 `manual` 為;而** \@ 狀態**則需要設定選項**24\*\* 。</span><span class="sxs-lookup"><span data-stu-id="b792f-203">The article property **\@replicate_ddl** requires a value of `true`; **\@identityrangemanagementoption** requires a value of `manual`; and **\@status** requires that option **24** is set.</span></span>  
  
-   <span data-ttu-id="b792f-204">發行項屬性的值\*\* \@ ins_cmd**、 \*\* \@ del_cmd**和\*\* \@ upd_cmd\*\*不能設定為 `SQL` 。</span><span class="sxs-lookup"><span data-stu-id="b792f-204">The value for article properties **\@ins_cmd**, **\@del_cmd**, and **\@upd_cmd** cannot be set to `SQL`.</span></span>  
  
-   <span data-ttu-id="b792f-205">\*\* \@ Sync_type\*\*的訂用帳戶屬性需要或的值 `none` `automatic` 。</span><span class="sxs-lookup"><span data-stu-id="b792f-205">The subscription property **\@sync_type** requires a value of `none` or `automatic`.</span></span>  
  
### <a name="maintenance-considerations"></a><span data-ttu-id="b792f-206">維護考量</span><span class="sxs-lookup"><span data-stu-id="b792f-206">Maintenance Considerations</span></span>  
 <span data-ttu-id="b792f-207">下列動作需要停止系統。</span><span class="sxs-lookup"><span data-stu-id="b792f-207">The following actions require the system to be quiesced.</span></span> <span data-ttu-id="b792f-208">這表示停止所有節點上已發行之資料表的活動，並確定每個節點都已收到來自其他所有節點的所有變更。</span><span class="sxs-lookup"><span data-stu-id="b792f-208">This means stopping activity on published tables at all nodes and making sure that each node has received all changes from all other nodes.</span></span>  
  
-   <span data-ttu-id="b792f-209">將 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 節點加入至現有的拓撲</span><span class="sxs-lookup"><span data-stu-id="b792f-209">Adding a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] node to an existing topology</span></span>  
  
-   <span data-ttu-id="b792f-210">將發行項新增至現有的發行集</span><span class="sxs-lookup"><span data-stu-id="b792f-210">Adding an article to an existing publication</span></span>  
  
-   <span data-ttu-id="b792f-211">變更結構描述</span><span class="sxs-lookup"><span data-stu-id="b792f-211">Making schema changes</span></span>  
  
-   <span data-ttu-id="b792f-212">從備份還原節點</span><span class="sxs-lookup"><span data-stu-id="b792f-212">Restoring a node from a backup</span></span>  
  
 <span data-ttu-id="b792f-213">如需詳細資訊，請參閱[停止複寫拓撲 &#40;複寫 Transact-SQL 程式設計&#41;](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md) 和[管理點對點拓撲 &#40;複寫 Transact-SQL 程式設計&#41;](../administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="b792f-213">For more information, see [Quiesce a Replication Topology &#40;Replication Transact-SQL Programming&#41;](../administration/quiesce-a-replication-topology-replication-transact-sql-programming.md) and [Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](../administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md).</span></span>  
  
-   <span data-ttu-id="b792f-214">如果您將新的節點加入至點對點拓撲，則應該只從新節點加入之後所建立的備份進行還原。</span><span class="sxs-lookup"><span data-stu-id="b792f-214">If you add a new node to a peer-to-peer topology, you should restore only from backups that were created after the new node was added.</span></span>  
  
-   <span data-ttu-id="b792f-215">您無法重新初始化點對點拓撲中的訂閱。</span><span class="sxs-lookup"><span data-stu-id="b792f-215">You cannot reinitialize subscriptions in a peer-to-peer topology.</span></span> <span data-ttu-id="b792f-216">如果您必須確定節點有資料的新副本，請在節點還原備份。</span><span class="sxs-lookup"><span data-stu-id="b792f-216">If you have to ensure that a node has a new copy of the data, restore a backup at the node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b792f-217">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b792f-217">See Also</span></span>  
 <span data-ttu-id="b792f-218">[管理點對點拓撲 &#40;複寫 Transact-SQL 程式設計&#41;](../administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span><span class="sxs-lookup"><span data-stu-id="b792f-218">[Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](../administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span></span>  
 <span data-ttu-id="b792f-219">[備份與還原快照式和異動複寫的策略](../administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="b792f-219">[Strategies for Backing Up and Restoring Snapshot and Transactional Replication](../administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md) </span></span>  
 [<span data-ttu-id="b792f-220">異動複寫的發行集類型</span><span class="sxs-lookup"><span data-stu-id="b792f-220">Publication Types for Transactional Replication</span></span>](transactional-replication.md)  
  
  
