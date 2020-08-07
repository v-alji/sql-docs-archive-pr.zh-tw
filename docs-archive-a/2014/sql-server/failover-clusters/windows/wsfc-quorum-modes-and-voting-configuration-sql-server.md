---
title: WSFC 仲裁模式和投票組態 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
- failover clustering [SQL Server], AlwaysOn Availability Groups
ms.assetid: ca0d59ef-25f0-4047-9130-e2282d058283
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b1d5ad992c59f252f485f2d65451a72f150bef8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595552"
---
# <a name="wsfc-quorum-modes-and-voting-configuration-sql-server"></a><span data-ttu-id="2a7b9-102">WSFC 仲裁模式和投票組態 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2a7b9-102">WSFC Quorum Modes and Voting Configuration (SQL Server)</span></span>
  <span data-ttu-id="2a7b9-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 和 AlwaysOn 容錯移轉叢集執行個體 (FCI) 都會利用 Windows Server 容錯移轉叢集 (WSFC) 做為平台技術。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-103">Both [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and AlwaysOn Failover Cluster Instances (FCI) take advantage of Windows Server Failover Clustering (WSFC) as a platform technology.</span></span>  <span data-ttu-id="2a7b9-104">WSFC 使用以仲裁為基礎的方法，監視整體叢集健全狀況並最大化節點層級容錯能力。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-104">WSFC uses a quorum-based approach to monitoring overall cluster health and maximize node-level fault tolerance.</span></span> <span data-ttu-id="2a7b9-105">WSFC 仲裁模式和節點投票組態的基礎了解，對於 AlwaysOn 高可用性和災害復原方案的設計、操作和疑難排解非常重要。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-105">A fundamental understanding of WSFC quorum modes and node voting configuration is very important to designing, operating, and troubleshooting your AlwaysOn high availability and disaster recovery solution.</span></span>  
  
 <span data-ttu-id="2a7b9-106">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="2a7b9-106">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="2a7b9-107">仲裁的叢集健全狀況偵測</span><span class="sxs-lookup"><span data-stu-id="2a7b9-107">Cluster Health Detection by Quorum</span></span>](#ClusterHealthDetectionbyQuorum)  
  
-   [<span data-ttu-id="2a7b9-108">仲裁模式</span><span class="sxs-lookup"><span data-stu-id="2a7b9-108">Quorum Modes</span></span>](#QuorumModes)  
  
-   [<span data-ttu-id="2a7b9-109">投票和非投票節點</span><span class="sxs-lookup"><span data-stu-id="2a7b9-109">Voting and Non-Voting Nodes</span></span>](#VotingandNonVotingNodes)  
  
-   [<span data-ttu-id="2a7b9-110">建議的仲裁投票調整</span><span class="sxs-lookup"><span data-stu-id="2a7b9-110">Recommended Adjustments to Quorum Voting</span></span>](#RecommendedAdjustmentstoQuorumVoting)  
  
-   [<span data-ttu-id="2a7b9-111">相關工作</span><span class="sxs-lookup"><span data-stu-id="2a7b9-111">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="2a7b9-112">相關內容</span><span class="sxs-lookup"><span data-stu-id="2a7b9-112">Related Content</span></span>](#RelatedContent)  
  
##  <a name="cluster-health-detection-by-quorum"></a><a name="ClusterHealthDetectionbyQuorum"></a> <span data-ttu-id="2a7b9-113">使用仲裁進行叢集健全狀況偵測</span><span class="sxs-lookup"><span data-stu-id="2a7b9-113">Cluster Health Detection by Quorum</span></span>  
 <span data-ttu-id="2a7b9-114">WSFC 叢集中的每個節點都會參與定期的活動訊號通訊，與其他節點共用節點的健全狀況。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-114">Each node in a WSFC cluster participates in periodic heartbeat communication to share the node's health status with the other nodes.</span></span> <span data-ttu-id="2a7b9-115">沒有回應的節點是視為處於失敗狀態。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-115">Unresponsive nodes are considered to be in a failed state.</span></span>  
  
 <span data-ttu-id="2a7b9-116">*「仲裁」* (Quorum) 節點集是 WSFC 叢集中的多數投票節點和見證。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-116">A *quorum* node set is a majority of the voting nodes and witnesses in the WSFC cluster.</span></span> <span data-ttu-id="2a7b9-117">WSFC 叢集的整體健全狀況和狀態是由定期 *「仲裁投票」*(Quorum Vote) 所決定。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-117">The overall health and status of a WSFC cluster is determined by a periodic *quorum vote*.</span></span>  <span data-ttu-id="2a7b9-118">仲裁的存在意味著叢集狀況良好，能提供節點層級的容錯功能。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-118">The presence of a quorum means that the cluster is healthy and able to provide node-level fault tolerance.</span></span>  
  
 <span data-ttu-id="2a7b9-119">缺少仲裁表示叢集狀況不良。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-119">The absence of a quorum indicates that the cluster is not healthy.</span></span>  <span data-ttu-id="2a7b9-120">必須維護整體 WSFC 叢集健全狀況，以確保次要節點狀況良好，可供主要節點容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-120">Overall WSFC cluster health must be maintained in order to ensure that healthy secondary nodes are available for primary nodes to fail over to.</span></span>  <span data-ttu-id="2a7b9-121">如果仲裁投票失敗，做為預防措施，WSFC 叢集將設為離線。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-121">If the quorum vote fails, the WSFC cluster will be set offline as a precautionary measure.</span></span>  <span data-ttu-id="2a7b9-122">這也會導致在叢集中註冊的所有 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體停止。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-122">This will also cause all [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instances registered with the cluster to be stopped.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2a7b9-123">如果 WSFC 叢集因為仲裁失敗而設為離線，則需要手動操作，將其恢復上線。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-123">If a WSFC cluster is set offline because of quorum failure, manual intervention is required to bring it back online.</span></span>  
>   
>  <span data-ttu-id="2a7b9-124">如需詳細資訊，請參閱[透過強制仲裁執行 WSFC 嚴重損壞修復 &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-124">For more information, see: [WSFC Disaster Recovery through Forced Quorum &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md).</span></span>  
  
##  <a name="quorum-modes"></a><a name="QuorumModes"></a><span data-ttu-id="2a7b9-125">仲裁模式</span><span class="sxs-lookup"><span data-stu-id="2a7b9-125">Quorum Modes</span></span>  
 <span data-ttu-id="2a7b9-126">*「仲裁模式」* (Quorum Mode) 是在 WSFC 叢集層級設定，指出仲裁投票所使用的方法。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-126">A *quorum mode* is configured at the WSFC cluster level that dictates the methodology used for quorum voting.</span></span>  <span data-ttu-id="2a7b9-127">容錯移轉叢集管理員公用程式會根據叢集中的節點數來建議仲裁模式。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-127">The Failover Cluster Manager utility will recommend a quorum mode based on the number of nodes in the cluster.</span></span>  
  
 <span data-ttu-id="2a7b9-128">下列仲裁模式可用於決定何者構成投票仲裁：</span><span class="sxs-lookup"><span data-stu-id="2a7b9-128">The following quorum modes can be used to determine what constitutes a quorum of votes:</span></span>  
  
-   <span data-ttu-id="2a7b9-129">**節點多數。**</span><span class="sxs-lookup"><span data-stu-id="2a7b9-129">**Node Majority.**</span></span> <span data-ttu-id="2a7b9-130">叢集中超過一半的投票節點必須投票肯定，叢集才是狀況良好。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-130">More than one-half of the voting nodes in the cluster must vote affirmatively for the cluster to be healthy.</span></span>  
  
-   <span data-ttu-id="2a7b9-131">**節點與檔案共用多數。**</span><span class="sxs-lookup"><span data-stu-id="2a7b9-131">**Node and File Share Majority.**</span></span> <span data-ttu-id="2a7b9-132">類似於節點多數仲裁模式，不過遠端檔案共用也會設定為投票見證，而且從任何節點至該共用的連接也會列入肯定投票。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-132">Similar to Node Majority quorum mode, except that a remote file share is also configured as a voting witness, and connectivity from any node to that share is also counted as an affirmative vote.</span></span>  <span data-ttu-id="2a7b9-133">超過一半的可能投票必須是肯定，叢集才是狀況良好。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-133">More than one-half of the possible votes must be affirmative for the cluster to be healthy.</span></span>  
  
     <span data-ttu-id="2a7b9-134">最佳作法是，見證檔案共用不應位於叢集中的任何節點，而且它對叢集中的所有節點都應該是可見的。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-134">As a best practice, the witness file share should not reside on any node in the cluster, and it should be visible to all nodes in the cluster.</span></span>  
  
-   <span data-ttu-id="2a7b9-135">**節點與磁片多數。**</span><span class="sxs-lookup"><span data-stu-id="2a7b9-135">**Node and Disk Majority.**</span></span> <span data-ttu-id="2a7b9-136">類似於節點多數仲裁模式，不過共用磁碟叢集資源也會指定為投票見證，而且從任何節點至該共用磁碟的連接也會列入肯定投票。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-136">Similar to Node Majority quorum mode, except that a shared disk cluster resource is also designated as a voting witness, and connectivity from any node to that shared disk is also counted as an affirmative vote.</span></span>  <span data-ttu-id="2a7b9-137">超過一半的可能投票必須是肯定，叢集才是狀況良好。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-137">More than one-half of the possible votes must be affirmative for the cluster to be healthy.</span></span>  
  
-   <span data-ttu-id="2a7b9-138">**僅限磁碟：**</span><span class="sxs-lookup"><span data-stu-id="2a7b9-138">**Disk Only.**</span></span> <span data-ttu-id="2a7b9-139">共用磁碟叢集資源會指定為見證，而且從任何節點至該共用磁碟的連接會列入肯定投票。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-139">A shared disk cluster resource is designated as a witness, and connectivity by any node to that shared disk is counted as an affirmative vote.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="2a7b9-140">使用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]非對稱儲存組態時，如果投票節點為奇數，通常應該使用節點多數仲裁模式，如果投票節點為偶數，則使用節點與檔案共用多數仲裁模式。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-140">When using an asymmetric storage configuration for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], you should generally use the Node Majority quorum mode when you have an odd number of voting nodes, or the Node and File Share Majority quorum mode when you have an even number of voting nodes.</span></span>  
  
##  <a name="voting-and-non-voting-nodes"></a><a name="VotingandNonVotingNodes"></a> <span data-ttu-id="2a7b9-141">投票和非投票節點</span><span class="sxs-lookup"><span data-stu-id="2a7b9-141">Voting and Non-Voting Nodes</span></span>  
 <span data-ttu-id="2a7b9-142">根據預設，WSFC 叢集中的每個節點都是叢集仲裁成員，每個節點都有一票決定整體叢集健全狀況，而且每個節點都會持續嘗試建立仲裁。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-142">By default, each node in the WSFC cluster is included as a member of the cluster quorum; each node has a single vote in determining the overall cluster health, and each node will continuously attempt to establish a quorum.</span></span>  <span data-ttu-id="2a7b9-143">仲裁討論至此，針對投票決定叢集健全狀況的 WSFC 叢集節點集仔細限定為「投票節點」\*\*。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-143">The quorum discussion to this point has carefully qualified the set of WSFC cluster nodes that vote on cluster health as *voting nodes*.</span></span>  
  
 <span data-ttu-id="2a7b9-144">WSFC 叢集中沒有個別節點可針對叢集整體狀況良好或狀況不良做最後決定。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-144">No individual node in a WSFC cluster can definitively determine that the cluster as a whole is healthy or unhealthy.</span></span>  <span data-ttu-id="2a7b9-145">在任何給定時刻，從每個節點的觀點來看，某些其他節點可能看起來離線、看起來正在進行容錯移轉，或因為網路通訊失敗而看起來沒有回應。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-145">At any given moment, from the perspective of each node, some of the other nodes may appear to be offline, or appear to be in the process of failover, or appear unresponsive due to a network communication failure.</span></span>  <span data-ttu-id="2a7b9-146">仲裁投票的關鍵功能是決定 WSFC 叢集中每個節點的表面狀態是否確實為這些節點的實際狀態。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-146">A key function of the quorum vote is to determine whether the apparent state of each of node in the WSFC cluster is indeed that actual state of those nodes.</span></span>  
  
 <span data-ttu-id="2a7b9-147">針對「僅限磁碟」以外的所有仲裁模式，仲裁投票的有效性取決於叢集中所有投票節點之間的可靠通訊。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-147">For all of the quorum models except 'Disk Only', the effectiveness of a quorum vote depends on reliable communications between all of the voting nodes in the cluster.</span></span> <span data-ttu-id="2a7b9-148">相同實體子網路上節點之間的網路通訊應視為可靠；仲裁投票應該是信任的。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-148">Network communications between nodes on the same physical subnet should be considered reliable; the quorum vote should be trusted.</span></span>  
  
 <span data-ttu-id="2a7b9-149">不過，如果另一個子網路上的節點在仲裁投票中是視為無回應，但它實際上已上線，另一方面也是狀況良好，最可能的原因是子網路之間的網路通訊失敗。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-149">However, if a node on another subnet is seen as non-responsive in a quorum vote, but it is actually online and otherwise healthy, that is most likely due to a network communications failure between subnets.</span></span>  <span data-ttu-id="2a7b9-150">根據叢集拓撲、仲裁模式和容錯移轉原則組態，該網路通訊失敗實際上可能會建立多組投票節點 (或子網路)。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-150">Depending upon the cluster topology, quorum mode, and failover policy configuration, that network communications failure may effectively create more than one set (or subset) of voting nodes.</span></span>  
  
 <span data-ttu-id="2a7b9-151">當多個投票節點的子網路能夠獨立建立仲裁時，這稱為「裂腦案例」\*\*。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-151">When more than one subset of voting nodes is able to establish a quorum on its own, that is known as a *split-brain scenario*.</span></span>  <span data-ttu-id="2a7b9-152">在這種情況下，在個別仲裁中的節點可能有不同的表現方式，並且互相衝突。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-152">In such a scenario, the nodes in the separate quorums may behave differently, and in conflict with one another.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a7b9-153">只在系統管理員手動執行強制仲裁作業時，或在極罕見狀況下手動執行強制容錯移轉，而明確細分仲裁節點集，裂腦案例才是可能的。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-153">The split-brain scenario is only possible when a system administrator manually performs a forced quorum operation, or in very rare circumstances, a forced failover; explicitly subdividing the quorum node set.</span></span>  
  
 <span data-ttu-id="2a7b9-154">為了簡化仲裁設定並增加時間，您可能會想要調整每個節點的*NodeWeight*設定，讓該節點的投票不計入仲裁。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-154">In order to simplify your quorum configuration and increase up-time, you may want to adjust each node's *NodeWeight* setting so that the node's vote is not counted towards the quorum.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2a7b9-155">為了能夠使用 NodeWeight 設定，必須將以下 Hotfix 套用至 WSFC 叢集中的所有伺服器：</span><span class="sxs-lookup"><span data-stu-id="2a7b9-155">In order to use NodeWeight settings, the following hotfix must be applied to all servers in the WSFC cluster:</span></span>  
>   
>  <span data-ttu-id="2a7b9-156">[KB2494036](https://support.microsoft.com/kb/2494036)：可用來讓您設定在和中沒有仲裁投票的叢集節點 [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)][!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a7b9-156">[KB2494036](https://support.microsoft.com/kb/2494036): A hotfix is available to let you configure a cluster node that does not have quorum votes in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] and in [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]</span></span>  
  
##  <a name="recommended-adjustments-to-quorum-voting"></a><a name="RecommendedAdjustmentstoQuorumVoting"></a> <span data-ttu-id="2a7b9-157">建議的仲裁投票調整</span><span class="sxs-lookup"><span data-stu-id="2a7b9-157">Recommended Adjustments to Quorum Voting</span></span>  
 <span data-ttu-id="2a7b9-158">在啟用或停用指定 WSFC 節點的投票時，請遵循下列方針：</span><span class="sxs-lookup"><span data-stu-id="2a7b9-158">When enabling or disabling a given WSFC node's vote, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="2a7b9-159">**預設沒有任何投票。**</span><span class="sxs-lookup"><span data-stu-id="2a7b9-159">**No vote by default.**</span></span> <span data-ttu-id="2a7b9-160">假設每個節點一定要有明確的合理原因才能投票。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-160">Assume that each node should not vote without explicit justification.</span></span>  
  
-   <span data-ttu-id="2a7b9-161">**包含所有主要複本。**</span><span class="sxs-lookup"><span data-stu-id="2a7b9-161">**Include all primary replicas.**</span></span> <span data-ttu-id="2a7b9-162">裝載可用性群組主要複本或者為 FCI 慣用擁有者的每一個 WSFC 節點都應該有投票權。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-162">Each WSFC node that hosts an availability group primary replica or is the preferred owner of an FCI should have a vote.</span></span>  
  
-   <span data-ttu-id="2a7b9-163">**包含可能的自動容錯移轉擁有者。**</span><span class="sxs-lookup"><span data-stu-id="2a7b9-163">**Include possible automatic failover owners.**</span></span> <span data-ttu-id="2a7b9-164">可能因為可用性群組自動容錯移轉或 FCI 容錯移轉而裝載主要複本的每個節點都應該有投票權。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-164">Each node that could host a primary replica, as the result of an automatic availability group failover or FCI failover, should have a vote.</span></span> <span data-ttu-id="2a7b9-165">如果 WSFC 叢集中只有一個可用性群組，而且可用性複本只由獨立執行個體所裝載，這個規則只會包含屬於自動容錯移轉目標的次要複本。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-165">If there is only one availability group in the WSFC cluster and availability replicas are hosted only by standalone instances, this rule includes only the secondary replica that is the automatic failover target.</span></span>  
  
-   <span data-ttu-id="2a7b9-166">**排除次要網站節點。**</span><span class="sxs-lookup"><span data-stu-id="2a7b9-166">**Exclude secondary site nodes.**</span></span> <span data-ttu-id="2a7b9-167">一般而言，不要將投票權提供給位於次要災害復原網站的 WSFC 節點。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-167">In general, do not give votes to WSFC nodes that reside at a secondary disaster recovery site.</span></span>  <span data-ttu-id="2a7b9-168">您不會希望次要網站上的節點參與決策，使叢集在主要網站沒有任何問題時離線。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-168">You do not want nodes in the secondary site to contribute to a decision to take the cluster offline when there is nothing wrong with the primary site.</span></span>  
  
-   <span data-ttu-id="2a7b9-169">**奇數投票。**</span><span class="sxs-lookup"><span data-stu-id="2a7b9-169">**Odd number of votes.**</span></span> <span data-ttu-id="2a7b9-170">如有需要，在叢集中加入見證檔案共用、見證節點或見證磁碟，並調整仲裁模式，以避免仲裁投票中可能發生平局。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-170">If necessary, add a witness file share, a witness node, or a witness disk to the cluster and adjust the quorum mode to prevent possible ties in the quorum vote.</span></span>  
  
-   <span data-ttu-id="2a7b9-171">**容錯移轉後重新評估投票指派。**</span><span class="sxs-lookup"><span data-stu-id="2a7b9-171">**Re-assess vote assignments post-failover.**</span></span> <span data-ttu-id="2a7b9-172">您不會希望容錯移轉至不支援狀況良好仲裁的叢集組態。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-172">You do not want to fail over into a cluster configuration that does not support a healthy quorum.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2a7b9-173">在驗證 WSFC 仲裁投票組態時，如果下列任何一個條件成立，AlwaysOn 可用性群組精靈會顯示一則警告：</span><span class="sxs-lookup"><span data-stu-id="2a7b9-173">When validating WSFC quorum vote configuration, the AlwaysOn Availability Group Wizard shows a warning if any of the following conditions are true:</span></span>  
> 
>  -   <span data-ttu-id="2a7b9-174">裝載主要複本的叢集節點沒有投票權。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-174">The cluster node that hosts the primary replica does not have a vote</span></span>  
> -   <span data-ttu-id="2a7b9-175">次要複本有設定自動容錯移轉，而且它的叢集節點沒有投票權。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-175">A secondary replica is configured for automatic failover and its cluster node does not have a vote.</span></span>  
> -   <span data-ttu-id="2a7b9-176">[KB2494036](https://support.microsoft.com/kb/2494036) 不會安裝在裝載可用性複本的所有叢集節點上。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-176">[KB2494036](https://support.microsoft.com/kb/2494036) is not installed on all cluster nodes that host availability replicas.</span></span> <span data-ttu-id="2a7b9-177">針對多網站部署中的叢集節點加入或移除投票需要這個修補程式。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-177">This patch is required to add or remove votes for cluster nodes in multi-site deployments.</span></span> <span data-ttu-id="2a7b9-178">不過，單一網站部署中通常不需要，而且您可以安心地忽略警告。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-178">However, in single-site deployments, it is usually not required and you may safely ignore the warning.</span></span>  
> 
> [!TIP]
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="2a7b9-179">公開數個系統動態管理檢視 (DMV)，有助於您管理設定相關的 WSFC 叢集組態和節點仲裁投票。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-179">exposes several system dynamic management views (DMVs) that can help you manage settings related WSFC cluster configuration and node quorum voting.</span></span>  
> 
>  <span data-ttu-id="2a7b9-180">如需詳細資訊，請參閱：  [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql), [sys.dm_hadr_cluster_members](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql), [sys.dm_os_cluster_nodes](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-nodes-transact-sql), [sys.dm_hadr_cluster_networks](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2a7b9-180">For more information, see:  [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql), [sys.dm_hadr_cluster_members](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql), [sys.dm_os_cluster_nodes](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-nodes-transact-sql), [sys.dm_hadr_cluster_networks](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="2a7b9-181">相關工作</span><span class="sxs-lookup"><span data-stu-id="2a7b9-181">Related Tasks</span></span>  
  
-   [<span data-ttu-id="2a7b9-182">檢視叢集仲裁 NodeWeight 設定</span><span class="sxs-lookup"><span data-stu-id="2a7b9-182">View Cluster Quorum NodeWeight Settings</span></span>](view-cluster-quorum-nodeweight-settings.md)  
  
-   [<span data-ttu-id="2a7b9-183">設定叢集仲裁 NodeWeight 設定</span><span class="sxs-lookup"><span data-stu-id="2a7b9-183">Configure Cluster Quorum NodeWeight Settings</span></span>](configure-cluster-quorum-nodeweight-settings.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="2a7b9-184">相關內容</span><span class="sxs-lookup"><span data-stu-id="2a7b9-184">Related Content</span></span>  
  
-   [<span data-ttu-id="2a7b9-185">Microsoft SQL Server AlwaysOn 高可用性和災害復原方案指南</span><span class="sxs-lookup"><span data-stu-id="2a7b9-185">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   [<span data-ttu-id="2a7b9-186">AlwaysOn 可用性群組精靈中的仲裁投票組態檢查</span><span class="sxs-lookup"><span data-stu-id="2a7b9-186">Quorum vote configuration check in AlwaysOn Availability Group Wizards</span></span>](https://blogs.msdn.com/b/sqlalwayson/archive/2012/03/13/quorum-vote-configuration-check-in-alwayson-availability-group-wizards-andy-jing.aspx)  
  
-   <span data-ttu-id="2a7b9-187">[Windows Server 技術：容錯移轉叢集](https://technet.microsoft.com/library/cc732488\(v=WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="2a7b9-187">[Windows Server Technologies:  Failover Clusters](https://technet.microsoft.com/library/cc732488\(v=WS.10\).aspx)</span></span>  
  
-   <span data-ttu-id="2a7b9-188">[容錯移轉叢集逐步指南：在容錯移轉叢集中設定仲裁](https://technet.microsoft.com/library/cc770620\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="2a7b9-188">[Failover Cluster Step-by-Step Guide: Configuring the Quorum in a Failover Cluster](https://technet.microsoft.com/library/cc770620\(WS.10\).aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a7b9-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a7b9-189">See Also</span></span>  
 <span data-ttu-id="2a7b9-190">[透過強制仲裁 &#40;SQL Server 的 WSFC 損毀修復&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2a7b9-190">[WSFC Disaster Recovery through Forced Quorum &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md) </span></span>  
 [<span data-ttu-id="2a7b9-191">SQL Server 的 Windows Server 容錯移轉叢集 &#40;WSFC&#41;</span><span class="sxs-lookup"><span data-stu-id="2a7b9-191">Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server</span></span>](windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  
