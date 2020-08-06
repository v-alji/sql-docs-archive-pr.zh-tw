---
title: 透過強制仲裁執行 WSFC 災害復原 (SQL Server) | Microsoft Docs
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
ms.assetid: 6cefdc18-899e-410c-9ae4-d6080f724046
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b2c9399472c6e67c9e2121a008f9283ba05943da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595553"
---
# <a name="wsfc-disaster-recovery-through-forced-quorum-sql-server"></a><span data-ttu-id="a1491-102">透過強制仲裁執行 WSFC 災害復原 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a1491-102">WSFC Disaster Recovery through Forced Quorum (SQL Server)</span></span>
  <span data-ttu-id="a1491-103">仲裁失敗的原因通常是涉及 WSFC 叢集中許多節點的系統損毀、持續性通訊失敗或設定錯誤。</span><span class="sxs-lookup"><span data-stu-id="a1491-103">Quorum failure is usually caused by a systemic disaster, or a persistent communications failure, or a misconfiguration involving several nodes in the WSFC cluster.</span></span>  <span data-ttu-id="a1491-104">若要從仲裁失敗中復原，您必須進行手動介入。</span><span class="sxs-lookup"><span data-stu-id="a1491-104">Manual intervention is required to recovery from a quorum failure.</span></span>  
  
-   <span data-ttu-id="a1491-105">**開始之前：**  [必要條件](#Prerequisites)、 [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="a1491-105">**Before you start:**  [Prerequisites](#Prerequisites), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="a1491-106">**透過強制仲裁程序執行 WSFC 災害復原** [透過強制仲裁程序執行 WSFC 災害復原](#Main)</span><span class="sxs-lookup"><span data-stu-id="a1491-106">**WSFC Disaster Recovery through the Forced Quorum Procedure** [WSFC Disaster Recovery through the Forced Quorum Procedure](#Main)</span></span>  
  
-   [<span data-ttu-id="a1491-107">相關工作</span><span class="sxs-lookup"><span data-stu-id="a1491-107">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="a1491-108">相關內容</span><span class="sxs-lookup"><span data-stu-id="a1491-108">Related Content</span></span>](#RelatedContent)  
  
##  <a name="before-you-start"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a1491-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="a1491-109">Before You Start</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="a1491-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="a1491-110">Prerequisites</span></span>  
 <span data-ttu-id="a1491-111">強制仲裁程序會假設仲裁失敗之前存在狀況良好的仲裁。</span><span class="sxs-lookup"><span data-stu-id="a1491-111">The Forced Quorum Procedure assumes that a healthy quorum existed before the quorum failure.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="a1491-112">使用者應該充分了解 Windows Server 容錯移轉叢集、WSFC 仲裁模型、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]以及環境特定部署組態的概念和互動方式。</span><span class="sxs-lookup"><span data-stu-id="a1491-112">The user should be well-informed on the concepts and interactions of Windows Server Failover Clustering, WSFC Quorum Models, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and the environment's specific deployment configuration.</span></span>  
>   
>  <span data-ttu-id="a1491-113">如需詳細資訊，請參閱：  [SQL Server 的 Windows Server 容錯移轉叢集 (WSFC)](https://msdn.microsoft.com/library/hh270278\(v=SQL.110\).aspx), [WSFC 仲裁模式和投票組態 (SQL Server)](https://msdn.microsoft.com/library/hh270280\(v=SQL.110\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="a1491-113">For more information, see:  [Windows Server Failover Clustering (WSFC) with SQL Server](https://msdn.microsoft.com/library/hh270278\(v=SQL.110\).aspx), [WSFC Quorum Modes and Voting Configuration (SQL Server)](https://msdn.microsoft.com/library/hh270280\(v=SQL.110\).aspx)</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a1491-114">Security</span><span class="sxs-lookup"><span data-stu-id="a1491-114">Security</span></span>  
 <span data-ttu-id="a1491-115">使用者必須是屬於 WSFC 叢集之每一個節點上本機 Administrators 群組成員的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="a1491-115">The user must be a domain account that is member of the local Administrators group on each node of the WSFC cluster.</span></span>  
  
##  <a name="wsfc-disaster-recovery-through-the-forced-quorum-procedure"></a><a name="Main"></a> <span data-ttu-id="a1491-116">透過強制仲裁程序執行 WSFC 災害復原</span><span class="sxs-lookup"><span data-stu-id="a1491-116">WSFC Disaster Recovery through the Forced Quorum Procedure</span></span>  
 <span data-ttu-id="a1491-117">請記住，仲裁失敗會導致 WSFC 叢集中的所有叢集服務、SQL Server 執行個體和 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]設定為離線，因為依照設定，叢集無法確保節點層級的容錯。</span><span class="sxs-lookup"><span data-stu-id="a1491-117">Remember that quorum failure will cause all clustered services, SQL Server instances, and [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], in the WSFC cluster to be set offline, because the cluster, as configured, cannot ensure node-level fault tolerance.</span></span>  <span data-ttu-id="a1491-118">仲裁失敗表示 WSFC 叢集中狀況良好的投票節點無法再滿足仲裁模型。</span><span class="sxs-lookup"><span data-stu-id="a1491-118">A quorum failure means that healthy voting nodes in the WSFC cluster no longer satisfy the quorum model.</span></span> <span data-ttu-id="a1491-119">某些節點可能已經完全失敗，而某些節點可能剛關閉 WSFC 服務且其他方面狀況良好，但是喪失與仲裁通訊的功能。</span><span class="sxs-lookup"><span data-stu-id="a1491-119">Some nodes may have failed completely, and some may have just shut down the WSFC service and are otherwise healthy, except for the loss of the ability to communicate with a quorum.</span></span>  
  
 <span data-ttu-id="a1491-120">若要讓 WSFC 叢集重新上線，您必須在現有的組態下更正仲裁失敗的根本原因、視需要復原受影響的資料庫，而且您可能會想要重新設定 WSFC 叢集中的剩餘節點，以便反映存活叢集拓撲。</span><span class="sxs-lookup"><span data-stu-id="a1491-120">To bring the WSFC cluster back online, you must correct the root cause of the quorum failure under the existing configuration, recover the affected databases as needed, and you may want to reconfigure the remaining nodes in the WSFC cluster to reflect the surviving cluster topology.</span></span>  
  
 <span data-ttu-id="a1491-121">您可以在 WSFC 叢集節點上使用 *「強制仲裁」* (Forced Quorum) 程序，以便覆寫讓叢集離線的安全控制項。</span><span class="sxs-lookup"><span data-stu-id="a1491-121">You can use the *forced quorum* procedure on a WSFC cluster node to override the safety controls that took the cluster offline.</span></span>  <span data-ttu-id="a1491-122">這個程序實際上會告知叢集暫停仲裁投票檢查，並且讓叢集中任何節點上的 WSFC 叢集資源和 SQL Server 重新上線。</span><span class="sxs-lookup"><span data-stu-id="a1491-122">This effectively tells the cluster to suspend the quorum voting checks, and lets you bring the WSFC cluster resources and SQL Server back online on any of the nodes in the cluster.</span></span>  
  
 <span data-ttu-id="a1491-123">這種類型的災害復原程序應該包括下列步驟：</span><span class="sxs-lookup"><span data-stu-id="a1491-123">This type of disaster recovery process should include the following steps:</span></span>  
  
#### <a name="to-recover-from-quorum-failure"></a><span data-ttu-id="a1491-124">若要從仲裁失敗中復原：</span><span class="sxs-lookup"><span data-stu-id="a1491-124">To Recover from Quorum Failure:</span></span>  
  
1.  <span data-ttu-id="a1491-125">**判斷失敗的範圍。**</span><span class="sxs-lookup"><span data-stu-id="a1491-125">**Determine the scope of the failure.**</span></span> <span data-ttu-id="a1491-126">您可以識別哪些可用性群組或 SQL Server 執行個體沒有回應、哪些叢集節點在線上且可供災後使用，並且檢查 Windows 事件記錄檔和 SQL Server 系統記錄檔。</span><span class="sxs-lookup"><span data-stu-id="a1491-126">Identify which availability groups or SQL Server instances are non-responsive, which cluster nodes are online and available for post-disaster use, and examine the Windows event logs and the SQL Server system logs.</span></span>  <span data-ttu-id="a1491-127">如果可行的話，您應該保留鑑識資料和系統記錄檔，以便日後分析。</span><span class="sxs-lookup"><span data-stu-id="a1491-127">Where practical, you should preserve forensic data and system logs for later analysis.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="a1491-128">在有回應的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]執行個體上，您可以藉由查詢 [sys.dm_hadr_availability_group_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql) 動態管理檢視 (DMV)，取得有關本機伺服器執行個體上擁有可用性複本之可用性群組的健全狀況資訊。</span><span class="sxs-lookup"><span data-stu-id="a1491-128">On a responsive instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], you can obtain information about the health of availability groups that possess an availability replica on the local server instance by querying the [sys.dm_hadr_availability_group_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql) dynamic management view (DMV).</span></span>  
  
2.  <span data-ttu-id="a1491-129">**在單一節點上使用強制仲裁，藉以啟動 WSFC 叢集。**</span><span class="sxs-lookup"><span data-stu-id="a1491-129">**Start the WSFC cluster by using forced quorum on a single node.**</span></span> <span data-ttu-id="a1491-130">除了 WSFC 叢集服務已關閉以外，您可以識別元件失敗數目最少的節點。</span><span class="sxs-lookup"><span data-stu-id="a1491-130">Identify a node with a minimal number of component failures, other than that the WSFC cluster service was shut down.</span></span>  <span data-ttu-id="a1491-131">請確認此節點能夠與其他大多數節點通訊。</span><span class="sxs-lookup"><span data-stu-id="a1491-131">Verify that this node can communicate with a majority of the other nodes.</span></span>  
  
     <span data-ttu-id="a1491-132">在此節點上，您可以使用強制仲裁程序來手動強制叢集上線。</span><span class="sxs-lookup"><span data-stu-id="a1491-132">On this node, manually force the cluster to come online using the forced quorum procedure.</span></span>  <span data-ttu-id="a1491-133">為了盡量降低遺失資料的可能性，請選取最後裝載可用性群組主要複本的節點。</span><span class="sxs-lookup"><span data-stu-id="a1491-133">To minimize potential data loss, select a node that was last hosting an availability group primary replica.</span></span>  
  
     <span data-ttu-id="a1491-134">如需詳細資訊，請參閱：＜  [在無仲裁情況下強制啟動 WSFC 叢集](https://msdn.microsoft.com/library/hh270275\(v=SQL.110\).aspx)＞</span><span class="sxs-lookup"><span data-stu-id="a1491-134">For more information, see:  [Force a WSFC Cluster to Start Without a Quorum](https://msdn.microsoft.com/library/hh270275\(v=SQL.110\).aspx)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a1491-135">強制仲裁設定會影響整個叢集並封鎖仲裁檢查，直到邏輯 WSFC 叢集達成大多數投票並自動轉換成一般仲裁模式的作業為止。</span><span class="sxs-lookup"><span data-stu-id="a1491-135">The forced quorum setting has a cluster-wide affect to block quorum checks until the logical WSFC cluster achieves a majority of votes and automatically transitions to a regular quorum mode of operation.</span></span>  
  
3.  <span data-ttu-id="a1491-136">**在每個其他方面狀況良好的節點上，以正常方式啟動 WSFC 服務 (一次一個節點)。**</span><span class="sxs-lookup"><span data-stu-id="a1491-136">**Start the WSFC service normally on each otherwise healthy node, one at a time.**</span></span> <span data-ttu-id="a1491-137">在其他節點上啟動叢集服務時，您不需要指定強制仲裁選項。</span><span class="sxs-lookup"><span data-stu-id="a1491-137">You do not have to specify the forced quorum option when you start the cluster service on the other nodes.</span></span>  
  
     <span data-ttu-id="a1491-138">當每個節點上的 WSFC 服務都重新上線時，它會與其他狀況良好的節點交涉，以便同步處理新叢集組態狀態。</span><span class="sxs-lookup"><span data-stu-id="a1491-138">As the WSFC service on each node comes back online, it negotiates with the other healthy nodes to synchronize the new cluster configuration state.</span></span>  <span data-ttu-id="a1491-139">請記得一次操作一個節點，避免在解析叢集的最後已知狀態時可能發生的競爭情形。</span><span class="sxs-lookup"><span data-stu-id="a1491-139">Remember to do this one node at a time to prevent potential race conditions in resolving the last known state of the cluster.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="a1491-140">請確定您所啟動的每個節點都能夠與其他新上線的節點通訊。</span><span class="sxs-lookup"><span data-stu-id="a1491-140">Ensure that each node that you start can communicate with the other newly online nodes.</span></span>  <span data-ttu-id="a1491-141">您可以考慮停用其他節點的 WSFC 服務。</span><span class="sxs-lookup"><span data-stu-id="a1491-141">Consider disabling the WSFC service on the other nodes.</span></span>  <span data-ttu-id="a1491-142">否則，您將面臨建立多個仲裁節點集的風險，亦即裂腦案例。</span><span class="sxs-lookup"><span data-stu-id="a1491-142">Otherwise,  you run the risk of creating more than one quorum node set; that is a split-brain scenario.</span></span> <span data-ttu-id="a1491-143">如果步驟 1 中的發現正確無誤，應該不會發生這種狀況。</span><span class="sxs-lookup"><span data-stu-id="a1491-143">If your findings in step 1 were accurate, this should not occur.</span></span>  
  
4.  <span data-ttu-id="a1491-144">**套用新的仲裁模式和節點投票組態。**</span><span class="sxs-lookup"><span data-stu-id="a1491-144">**Apply new quorum mode and node vote configuration.**</span></span> <span data-ttu-id="a1491-145">如果強制仲裁成功重新啟動叢集中的所有節點，而仲裁失敗的根本原因已獲得解決，則不需要對原始仲裁模式和節點投票組態進行變更。</span><span class="sxs-lookup"><span data-stu-id="a1491-145">If forcing quorum successfully restarted all the nodes in the cluster and the root cause of the quorum failure has been corrected, changes to the original quorum mode and node vote configuration are unnecessary.</span></span>  
  
     <span data-ttu-id="a1491-146">否則，您應該評估新復原的叢集節點和可用性複本拓撲，並且依適當情況變更每個節點的仲裁模式和投票指派。</span><span class="sxs-lookup"><span data-stu-id="a1491-146">Otherwise, you should evaluate the newly recovered cluster node and availability replica topology, and change the quorum mode and vote assignments for each node as appropriate.</span></span> <span data-ttu-id="a1491-147">尚未復原的節點應該會設定為離線，或將其節點投票設定為零。</span><span class="sxs-lookup"><span data-stu-id="a1491-147">Un-recovered nodes should be set offline or have their node votes set to zero.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="a1491-148">此時，叢集中的節點和 SQL Server 執行個體看起來可能已還原成一般作業狀態。</span><span class="sxs-lookup"><span data-stu-id="a1491-148">At this point, the nodes and SQL Server instances in the cluster may appear to be restored back to regular operation.</span></span>  <span data-ttu-id="a1491-149">不過，狀況良好的仲裁可能仍然不存在。</span><span class="sxs-lookup"><span data-stu-id="a1491-149">However, a healthy quorum may still not exist.</span></span>  <span data-ttu-id="a1491-150">您可以使用容錯移轉叢集管理員、SQL Server Management Studio 中的 AlwaysOn 儀表板或適當的 DMV 來確認仲裁是否已經還原。</span><span class="sxs-lookup"><span data-stu-id="a1491-150">Using the Failover Cluster Manager, or the AlwaysOn Dashboard within SQL Server Management Studio, or the appropriate DMVs, verify that a quorum has been restored.</span></span>  
  
5.  <span data-ttu-id="a1491-151">**視需要復原可用性群組資料庫複本。**</span><span class="sxs-lookup"><span data-stu-id="a1491-151">**Recover availability group database replicas as needed.**</span></span> <span data-ttu-id="a1491-152">非可用性群組資料庫應該會在一般 SQL Server 啟動程序中自行復原並重新上線。</span><span class="sxs-lookup"><span data-stu-id="a1491-152">Non-availability group databases should recover and come back online on their own as part of the regular SQL Server startup process.</span></span>  
  
     <span data-ttu-id="a1491-153">您可以依照下列順序，讓可用性群組複本重新上線，藉以盡量降低遺失資料的可能性並縮短復原時間：主要複本、同步次要複本和非同步次要複本。</span><span class="sxs-lookup"><span data-stu-id="a1491-153">You can minimize potential data loss and recovery time for the availability group replicas by bringing them back online in this sequence:  primary replica, synchronous secondary replicas, asynchronous secondary replicas.</span></span>  
  
6.  <span data-ttu-id="a1491-154">**修復或取代失敗的元件並重新驗證叢集。**</span><span class="sxs-lookup"><span data-stu-id="a1491-154">**Repair or replace failed components and re-validate cluster.**</span></span> <span data-ttu-id="a1491-155">既然您已經從初始災害和仲裁失敗中復原，就應該修復或取代失敗的節點並且據以調整相關的 WSFC 和 AlwaysOn 組態。</span><span class="sxs-lookup"><span data-stu-id="a1491-155">Now that you have recovered from the initial disaster and quorum failure, you should repair or replace the failed nodes and adjust related WSFC and AlwaysOn configurations accordingly.</span></span>  <span data-ttu-id="a1491-156">這項作業可能包括卸除可用性群組複本、從叢集中收回節點，或在節點上扁平化並重新安裝軟體。</span><span class="sxs-lookup"><span data-stu-id="a1491-156">This can include dropping availability group replicas, evicting nodes from the cluster, or flattening and re-installing software on a node.</span></span>  
  
     <span data-ttu-id="a1491-157">您必須修復或移除所有失敗的可用性複本。</span><span class="sxs-lookup"><span data-stu-id="a1491-157">You must repair or remove all failed availability replicas.</span></span>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="a1491-158">將不會截斷超過落後可用性複本最遠之最後一個已知點的交易記錄。</span><span class="sxs-lookup"><span data-stu-id="a1491-158">will not truncate the transaction log past the last known point of the farthest behind availability replica.</span></span>   <span data-ttu-id="a1491-159">如果失敗的複本並未修復或從可用性群組中移除，交易記錄將會成長，而且您將面臨在其他複本上用完交易記錄空間的風險。</span><span class="sxs-lookup"><span data-stu-id="a1491-159">If a failed replica is not repaired or removed from the availability group, the transaction logs will grow and you will run the risk of running out of transaction log space on the other replicas.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a1491-160">如果您在 WSFC 叢集上的可用性群組接聽程式結束時執行 WSFC [驗證設定精靈]，這個精靈會產生下列不正確的警告訊息：</span><span class="sxs-lookup"><span data-stu-id="a1491-160">If you run the WSFC Validate a Configuration Wizard when an availability group listener exists on the WSFC cluster, the wizard generates the following incorrect warning message:</span></span>  
    >   
    >  <span data-ttu-id="a1491-161">「網路名稱 'Name:<network_name>' 的 RegisterAllProviderIP 屬性設定為 1。在目前的叢集設定中，這個值應該設定為 0。」</span><span class="sxs-lookup"><span data-stu-id="a1491-161">"The RegisterAllProviderIP property for network name 'Name:<network_name>' is set to 1 For the current cluster configuration this value should be set to 0."</span></span>  
    >   
    >  <span data-ttu-id="a1491-162">請忽略這個訊息。</span><span class="sxs-lookup"><span data-stu-id="a1491-162">Please ignore this message.</span></span>  
  
7.  <span data-ttu-id="a1491-163">**視需要重複步驟 4。**</span><span class="sxs-lookup"><span data-stu-id="a1491-163">**Repeat step 4 as needed.**</span></span> <span data-ttu-id="a1491-164">其目標是要重新建立適當層級的容錯和高可用性，以便進行狀況良好的作業。</span><span class="sxs-lookup"><span data-stu-id="a1491-164">The goal is to re-establish the appropriate level of fault tolerance and high availability for healthy operations.</span></span>  
  
8.  <span data-ttu-id="a1491-165">**進行 RPO/RTO 分析。**</span><span class="sxs-lookup"><span data-stu-id="a1491-165">**Conduct RPO/RTO analysis.**</span></span> <span data-ttu-id="a1491-166">您應該分析 SQL Server 系統記錄檔、資料庫時間戳記和 Windows 事件記錄檔，以便判斷失敗的根本原因，並且記載實際的復原點和復原時間經驗。</span><span class="sxs-lookup"><span data-stu-id="a1491-166">You should analyze SQL Server system logs, database timestamps, and Windows event logs to determine root cause of the failure, and to document actual recovery point and recovery time experiences.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a1491-167">相關工作</span><span class="sxs-lookup"><span data-stu-id="a1491-167">Related Tasks</span></span>  
  
-   [<span data-ttu-id="a1491-168">在無仲裁情況下強制啟動 WSFC 叢集</span><span class="sxs-lookup"><span data-stu-id="a1491-168">Force a WSFC Cluster to Start Without a Quorum</span></span>](force-a-wsfc-cluster-to-start-without-a-quorum.md)  
  
-   [<span data-ttu-id="a1491-169">執行可用性群組的強制手動容錯移轉 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a1491-169">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](../../../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="a1491-170">檢視叢集仲裁 NodeWeight 設定</span><span class="sxs-lookup"><span data-stu-id="a1491-170">View Cluster Quorum NodeWeight Settings</span></span>](view-cluster-quorum-nodeweight-settings.md)  
  
-   [<span data-ttu-id="a1491-171">設定叢集仲裁 NodeWeight 設定</span><span class="sxs-lookup"><span data-stu-id="a1491-171">Configure Cluster Quorum NodeWeight Settings</span></span>](configure-cluster-quorum-nodeweight-settings.md)  
  
-   [<span data-ttu-id="a1491-172">使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a1491-172">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md) 
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="a1491-173">相關內容</span><span class="sxs-lookup"><span data-stu-id="a1491-173">Related Content</span></span>  
  
-   <span data-ttu-id="a1491-174">[檢視容錯移轉叢集的事件和記錄檔](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a1491-174">[View Events and Logs for a Failover Cluster](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="a1491-175">Get-ClusterLog 容錯移轉叢集指令程式</span><span class="sxs-lookup"><span data-stu-id="a1491-175">Get-ClusterLog Failover Cluster Cmdlet</span></span>](https://technet.microsoft.com/library/ee461045.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="a1491-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1491-176">See Also</span></span>  
 [<span data-ttu-id="a1491-177">SQL Server 的 Windows Server 容錯移轉叢集 &#40;WSFC&#41;</span><span class="sxs-lookup"><span data-stu-id="a1491-177">Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server</span></span>](windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  
