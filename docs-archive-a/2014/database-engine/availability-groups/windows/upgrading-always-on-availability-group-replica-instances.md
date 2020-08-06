---
title: 以最短的停機時間和資料遺失，升級及更新可用性群組伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: f670af56-dbcc-4309-9119-f919dcad8a65
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6bac882b93016a430fbcace2d590e6cc087123d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708633"
---
# <a name="upgrade-and-update-of-availability-group-servers-with-minimal-downtime-and-data-loss"></a><span data-ttu-id="a28e1-102">在停機時間和資料遺失最少的情況下升級及更新可用性群組伺服器</span><span class="sxs-lookup"><span data-stu-id="a28e1-102">Upgrade and Update of Availability Group Servers with Minimal Downtime and Data Loss</span></span>
  <span data-ttu-id="a28e1-103">當您將伺服器執行個體從 SQL Server 2012 更新或升級至某個 Service Pack 或較新的版本時，您可以透過執行輪流更新或升級，將可用性群組的停機時間減少至只有單一手動容錯移轉的時間。</span><span class="sxs-lookup"><span data-stu-id="a28e1-103">When updating or upgrading server instances from SQL Server 2012 to a service pack or a newer version, you can reduce downtime for an availability group to only a single manual failover by performing a sequential update or upgrade.</span></span> <span data-ttu-id="a28e1-104">如果要升級 SQL Server 版本，這稱為輪流升級；如果要以 Hotfix 或 Service Pack 更新目前的 SQL Server 版本，則稱為輪流更新。</span><span class="sxs-lookup"><span data-stu-id="a28e1-104">For upgrading SQL Server versions, it is known as rolling upgrade; for updating the current SQL Server version with hotfixes or service packs, it is known as rolling update.</span></span>  
  
 <span data-ttu-id="a28e1-105">這個主題僅限討論 SQL Server 升級/更新。</span><span class="sxs-lookup"><span data-stu-id="a28e1-105">This topic limits the discussion to SQL Server upgrades/updates only.</span></span> <span data-ttu-id="a28e1-106">如需高可用性 SQL Server 實例執行所在的作業系統相關升級/更新，請參閱[針對作業系統升級 AlwaysOn 可用性群組的跨叢集遷移](https://msdn.microsoft.com/library/jj873730.aspx)</span><span class="sxs-lookup"><span data-stu-id="a28e1-106">For operating system-related upgrades/updates that the highly-available SQL Server instances are running on, see [Cross-cluster Migration of AlwaysOn Availability Groups for Operating System Upgrades](https://msdn.microsoft.com/library/jj873730.aspx)</span></span>  
  
## <a name="rolling-upgradeupdate-best-practices-for-alwayson-availability-groups"></a><span data-ttu-id="a28e1-107">AlwaysOn 可用性群組的輪流升級/更新最佳作法</span><span class="sxs-lookup"><span data-stu-id="a28e1-107">Rolling Upgrade/Update Best Practices for AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="a28e1-108">當您執行伺服器升級/更新時，應該要觀察以下最佳作法，好讓停機時間及可用性群組的資料遺失情況降至最低：</span><span class="sxs-lookup"><span data-stu-id="a28e1-108">The following best practices should be observed when performing server upgrades/updates in order to minimize downtime and data loss for your availability groups:</span></span>  
  
-   <span data-ttu-id="a28e1-109">在開始輪流升級/更新之前，</span><span class="sxs-lookup"><span data-stu-id="a28e1-109">Before starting the rolling upgrade/update,</span></span>  
  
    -   <span data-ttu-id="a28e1-110">至少在其中一個同步認可複本上執行手動容錯移轉練習</span><span class="sxs-lookup"><span data-stu-id="a28e1-110">Perform a practice manual failover on at least one of your synchronous-commit replicas</span></span>  
  
    -   <span data-ttu-id="a28e1-111">在每一個可用性資料庫上執行完整資料庫備份來保護資料</span><span class="sxs-lookup"><span data-stu-id="a28e1-111">Protect your data by performing a full database backup on every availability database</span></span>  
  
    -   <span data-ttu-id="a28e1-112">在每一個可用性資料庫上執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="a28e1-112">Run DBCC CHECKDB on every availability database</span></span>  
  
-   <span data-ttu-id="a28e1-113">一定要先升級/更新遠端次要複本節點，然後是本機次要複本節點，最後是主要複本節點。</span><span class="sxs-lookup"><span data-stu-id="a28e1-113">Always upgrade/update the remote secondary replica nodes first, then local secondary replica nodes next, and the primary replica node last.</span></span>  
  
-   <span data-ttu-id="a28e1-114">在進行升級的資料庫上，不會發生備份。</span><span class="sxs-lookup"><span data-stu-id="a28e1-114">Backups cannot occur on a database that is in the process of being upgraded.</span></span>  <span data-ttu-id="a28e1-115">在升級次要複本之前，請設定自動備份喜好設定，只在主要複本上執行備份。</span><span class="sxs-lookup"><span data-stu-id="a28e1-115">Prior to upgrading the secondary replicas, configure the automated backup preference to run backups only on the primary replica.</span></span>  <span data-ttu-id="a28e1-116">在升級主要複本之前，請修改這項設定，使其只執行次要複本的備份。</span><span class="sxs-lookup"><span data-stu-id="a28e1-116">Prior to upgrading the primary replica, modify this setting to run backups only on the secondary replicas.</span></span>  
  
-   <span data-ttu-id="a28e1-117">為了避免可用性群組在升級/更新程序期間發生意外的容錯移轉，請從所有同步認可複本中移除可用性容錯移轉，然後再開始。</span><span class="sxs-lookup"><span data-stu-id="a28e1-117">To prevent the availability group from unintended failovers during the upgrade/update process, remove availability failover from all synchronous-commit replicas before you begin.</span></span>  
  
-   <span data-ttu-id="a28e1-118">先將可用性群組容錯移轉到包含次要複本的已升級節點之前，請勿升級主要複本節點。</span><span class="sxs-lookup"><span data-stu-id="a28e1-118">Do not upgrade the primary replica node before failing over the availability group to an upgraded node with a secondary replica first.</span></span> <span data-ttu-id="a28e1-119">否則，用戶端應用程式在主要複本的升級/更新期間可能會受困於停機時間延長。</span><span class="sxs-lookup"><span data-stu-id="a28e1-119">Otherwise, client applications may suffer extended downtime during the upgrade/update on the primary replica.</span></span>  
  
-   <span data-ttu-id="a28e1-120">一定要將可用性群組容錯移轉到同步認可的次要複本節點。</span><span class="sxs-lookup"><span data-stu-id="a28e1-120">Always fail over the availability group to a synchronous-commit secondary replica node.</span></span> <span data-ttu-id="a28e1-121">如果您容錯移轉到非同步認可的次要複本，資料庫將會遭受資料遺失之苦，而且資料移動會自動暫停，直到您手動繼續資料移動為止。</span><span class="sxs-lookup"><span data-stu-id="a28e1-121">If you fail over to an asynchronous-commit secondary replica, the databases will suffer data loss, and data movement is automatically suspended until you manually resume data movement.</span></span>  
  
-   <span data-ttu-id="a28e1-122">在您升級/更新其他任何次要複本節點之前，請勿升級/更新主要複本節點。</span><span class="sxs-lookup"><span data-stu-id="a28e1-122">Do not upgrade/update the primary replica node before upgrading/updating any other secondary replica nodes.</span></span> <span data-ttu-id="a28e1-123">已升級的主要複本將無法再傳送記錄到尚未升級至相同版本的次要複本。</span><span class="sxs-lookup"><span data-stu-id="a28e1-123">An upgraded primary replica can no longer ship logs to any secondary replica that has not yet been upgraded to the same version.</span></span> <span data-ttu-id="a28e1-124">當移至次要複本的資料移動作業暫停時，該複本無法進行自動容錯移轉，而且您的可用性資料庫很容易發生資料遺失。</span><span class="sxs-lookup"><span data-stu-id="a28e1-124">When data movement to a secondary replica is suspended, no automatic failover can occur for that replica, and your availability databases are vulnerable to data loss.</span></span>  
  
-   <span data-ttu-id="a28e1-125">在容錯移轉可用性群組之前，請確認容錯移轉目標的同步處理狀態為 SYNCHRONIZED。</span><span class="sxs-lookup"><span data-stu-id="a28e1-125">Before failing over an availability group, verify that the synchronization state of the failover target is SYNCHRONIZED.</span></span>  
  
## <a name="rolling-upgradeupdate-process"></a><span data-ttu-id="a28e1-126">輪流升級/更新程序</span><span class="sxs-lookup"><span data-stu-id="a28e1-126">Rolling Upgrade/Update Process</span></span>  
 <span data-ttu-id="a28e1-127">實際上，確切的程序將取決於一些因素，例如可用性群組的部署拓撲和每個複本的認可模式。</span><span class="sxs-lookup"><span data-stu-id="a28e1-127">In practice, the exact process will depend on factors such as the deployment topology of your availability groups and the commit mode of each replica.</span></span> <span data-ttu-id="a28e1-128">但是在最簡單的案例中，輪流升級/更新是多階段的程序，其最簡單的形式包含以下步驟：</span><span class="sxs-lookup"><span data-stu-id="a28e1-128">But in the simplest scenario, a rolling upgrade/update is a multi-stage process that in its simplest form involves the following steps:</span></span>  
  
 <span data-ttu-id="a28e1-129">![HADR 案例中的可用性群組升級](../../media/alwaysonupgrade-ag-hadr.gif "HADR 案例中的可用性群組升級")</span><span class="sxs-lookup"><span data-stu-id="a28e1-129">![Availability Group Upgrade in HADR Scenario](../../media/alwaysonupgrade-ag-hadr.gif "Availability Group Upgrade in HADR Scenario")</span></span>  
  
1.  <span data-ttu-id="a28e1-130">在所有同步認可複本上移除自動容錯移轉</span><span class="sxs-lookup"><span data-stu-id="a28e1-130">Remove automatic failover on all synchronous-commit replicas</span></span>  
  
2.  <span data-ttu-id="a28e1-131">升級/更新執行非同步認可次要複本的所有遠端伺服器執行個體</span><span class="sxs-lookup"><span data-stu-id="a28e1-131">Upgrade/update all remote server instances running asynchronous-commit secondary replicas</span></span>  
  
3.  <span data-ttu-id="a28e1-132">升級/更新目前未執行主要複本的所有本機伺服器執行個體</span><span class="sxs-lookup"><span data-stu-id="a28e1-132">Upgrade/update the all local server instances that are not currently running the primary replica</span></span>  
  
4.  <span data-ttu-id="a28e1-133">手動將可用性群組容錯移轉到同步認可的次要複本</span><span class="sxs-lookup"><span data-stu-id="a28e1-133">Manually fail over the availability group to a synchronous-commit secondary replica</span></span>  
  
5.  <span data-ttu-id="a28e1-134">升級/更新之前裝載主要複本的伺服器執行個體</span><span class="sxs-lookup"><span data-stu-id="a28e1-134">Upgrade/update the server instance that formerly hosted the primary replica</span></span>  
  
6.  <span data-ttu-id="a28e1-135">視需要設定自動容錯移轉夥伴</span><span class="sxs-lookup"><span data-stu-id="a28e1-135">Configure automatic failover partners as desired</span></span>  
  
 <span data-ttu-id="a28e1-136">必要時，您可以執行額外的手動容錯移轉，讓可用性群組回到原始的組態。</span><span class="sxs-lookup"><span data-stu-id="a28e1-136">If necessary, you can perform an extra manual failover to return the availability group to its original configuration.</span></span>  
  
## <a name="availability-group-with-one-remote-secondary-replica"></a><span data-ttu-id="a28e1-137">具有一個遠端次要複本的可用性群組</span><span class="sxs-lookup"><span data-stu-id="a28e1-137">Availability Group with One Remote Secondary Replica</span></span>  
 <span data-ttu-id="a28e1-138">如果您部署可用性群組只是為了災害復原，您可能必須將可用性群組容錯移轉至非同步認可的次要複本。</span><span class="sxs-lookup"><span data-stu-id="a28e1-138">If you have deployed an availability group only for disaster recovery, you may need to fail over the availability group to an asynchronous-commit secondary replica.</span></span> <span data-ttu-id="a28e1-139">下圖說明這類組態：</span><span class="sxs-lookup"><span data-stu-id="a28e1-139">Such configuration is illustrated by the following figure:</span></span>  
  
 <span data-ttu-id="a28e1-140">![DR 案例中的可用性群組升級](../../media/agupgrade-ag-dr.gif "DR 案例中的可用性群組升級")</span><span class="sxs-lookup"><span data-stu-id="a28e1-140">![Availability Group Upgrade in DR Scenario](../../media/agupgrade-ag-dr.gif "Availability Group Upgrade in DR Scenario")</span></span>  
  
 <span data-ttu-id="a28e1-141">在此情況下，您必須在輪流升級/更新期間，將可用性群組容錯移轉至非同步認可的次要複本。</span><span class="sxs-lookup"><span data-stu-id="a28e1-141">In this situation, you must fail over the availability group to the asynchronous-commit secondary replica during the rolling upgrade/update.</span></span> <span data-ttu-id="a28e1-142">為了防止資料遺失，請將認可模式變更為同步認可，並等候次要複本同步處理，然後再容錯移轉可用性群組。</span><span class="sxs-lookup"><span data-stu-id="a28e1-142">To prevent data loss, change the commit mode to synchronous commit and wait for the secondary replica to be synchronized before you fail over the availability group.</span></span> <span data-ttu-id="a28e1-143">因此，輪流升級/更新程序可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="a28e1-143">Therefore, the rolling upgrade/update process may look as follows:</span></span>  
  
1.  <span data-ttu-id="a28e1-144">升級/更新遠端伺服器</span><span class="sxs-lookup"><span data-stu-id="a28e1-144">Upgrade/update the remote server</span></span>  
  
2.  <span data-ttu-id="a28e1-145">將認可模式變更為同步認可</span><span class="sxs-lookup"><span data-stu-id="a28e1-145">Change the commit mode to synchronous commit</span></span>  
  
3.  <span data-ttu-id="a28e1-146">等到同步處理狀態變成 SYNCHRONIZED</span><span class="sxs-lookup"><span data-stu-id="a28e1-146">Wait until synchronization state is SYNCHRONIZED</span></span>  
  
4.  <span data-ttu-id="a28e1-147">將可用性群組容錯移轉到遠端站台</span><span class="sxs-lookup"><span data-stu-id="a28e1-147">Fail over the availability group to the remote site</span></span>  
  
5.  <span data-ttu-id="a28e1-148">升級/更新本機 (主要站台) 伺服器</span><span class="sxs-lookup"><span data-stu-id="a28e1-148">Upgrade/update the local (primary site) server</span></span>  
  
6.  <span data-ttu-id="a28e1-149">將可用性群組容錯移轉到主要站台</span><span class="sxs-lookup"><span data-stu-id="a28e1-149">Fail over the availability group to the primary site</span></span>  
  
7.  <span data-ttu-id="a28e1-150">將認可模式變更為非同步認可</span><span class="sxs-lookup"><span data-stu-id="a28e1-150">Change the commit mode to asynchronous commit</span></span>  
  
 <span data-ttu-id="a28e1-151">因為與遠端站台的資料同步處理不建議使用同步認可模式的設定，所以用戶端應用程式可能會注意到，設定變更之後會立刻增加資料庫延遲。</span><span class="sxs-lookup"><span data-stu-id="a28e1-151">Since the synchronous-commit mode is not a recommended setting for data synchronization to a remote site, client applications may notice an immediate increase in database latency after the setting change.</span></span> <span data-ttu-id="a28e1-152">此外，執行容錯移轉將會導致所有未認可的記錄訊息遭到捨棄。</span><span class="sxs-lookup"><span data-stu-id="a28e1-152">Moreover, performing a failover will cause all unacknowledged log messages to be discarded.</span></span> <span data-ttu-id="a28e1-153">捨棄的記錄訊息數量可能很龐大，這是因為兩個站台之間的高度網路延遲，導致用戶端遭遇大量的交易失敗。</span><span class="sxs-lookup"><span data-stu-id="a28e1-153">The amount of discarded log messages can be quite large due to the high network latency between the two sites, causing clients to experience a high volume of transactional failure.</span></span> <span data-ttu-id="a28e1-154">您可以執行下列動作，讓用戶端應用程式的影響降至最低：</span><span class="sxs-lookup"><span data-stu-id="a28e1-154">You can minimize impact to client applications by doing the following:</span></span>  
  
-   <span data-ttu-id="a28e1-155">謹慎選擇維護期間，使其發生於用戶端流量較低的期間</span><span class="sxs-lookup"><span data-stu-id="a28e1-155">Carefully select a maintenance window during low client traffic</span></span>  
  
-   <span data-ttu-id="a28e1-156">在主要站台上升級/更新 SQL Server 時，請將可用性模式變更回非同步認可，當您再次準備好要容錯移轉至主要站台時，再還原成同步認可模式。</span><span class="sxs-lookup"><span data-stu-id="a28e1-156">While upgrading/updating SQL Server on the primary site, change the availability mode back to asynchronous commit, then revert to synchronous commit when you are ready to fail over to the primary site again</span></span>  
  
## <a name="availability-group-with-failover-cluster-instance-nodes"></a><span data-ttu-id="a28e1-157">包含容錯移轉叢集執行個體節點的可用性群組</span><span class="sxs-lookup"><span data-stu-id="a28e1-157">Availability Group with Failover Cluster Instance Nodes</span></span>  
 <span data-ttu-id="a28e1-158">如果可用性群組包含容錯移轉叢集執行個體 (FCI) 節點，您應該先升級/更新非使用中節點，然後再升級/更新使用中節點。</span><span class="sxs-lookup"><span data-stu-id="a28e1-158">If an availability group contains failover cluster instance (FCI) nodes, you should upgrade/update the inactive nodes before you upgrade/update the active nodes.</span></span> <span data-ttu-id="a28e1-159">下圖說明具有 FCI 的常見可用性群組案例 (為了擁有本機高可用性及 FCI 之間用於遠端災害復原的非同步認可) 以及升級順序。</span><span class="sxs-lookup"><span data-stu-id="a28e1-159">The figure below illustrates a common availability group scenario with FCIs for local high availability and asynchronous commit between the FCIs for remote disaster recovery, and the upgrade sequence.</span></span>  
  
 <span data-ttu-id="a28e1-160">![可用性群組升級與 FCI](../../media/agupgrade-ag-fci-dr.gif "可用性群組升級與 FCI")</span><span class="sxs-lookup"><span data-stu-id="a28e1-160">![Availability Group Upgrade with FCIs](../../media/agupgrade-ag-fci-dr.gif "Availability Group Upgrade with FCIs")</span></span>  
  
1.  <span data-ttu-id="a28e1-161">升級/更新 REMOTE2</span><span class="sxs-lookup"><span data-stu-id="a28e1-161">Upgrade/update REMOTE2</span></span>  
  
2.  <span data-ttu-id="a28e1-162">將 FCI2 容錯移轉到 REMOTE2</span><span class="sxs-lookup"><span data-stu-id="a28e1-162">Fail over FCI2 to REMOTE2</span></span>  
  
3.  <span data-ttu-id="a28e1-163">升級/更新 REMOTE1</span><span class="sxs-lookup"><span data-stu-id="a28e1-163">Upgrade/update REMOTE1</span></span>  
  
4.  <span data-ttu-id="a28e1-164">升級/更新 PRIMARY2</span><span class="sxs-lookup"><span data-stu-id="a28e1-164">Upgrade/update PRIMARY2</span></span>  
  
5.  <span data-ttu-id="a28e1-165">將 FCI1 容錯移轉到 PRIMARY2</span><span class="sxs-lookup"><span data-stu-id="a28e1-165">Fail over FCI1 to PRIMARY2</span></span>  
  
6.  <span data-ttu-id="a28e1-166">升級/更新 PRIMARY1</span><span class="sxs-lookup"><span data-stu-id="a28e1-166">Upgrade/update PRIMARY1</span></span>  
  
## <a name="upgradeupdate-sql-server-instances-with-multiple-availability-groups"></a><span data-ttu-id="a28e1-167">升級/更新具有多個可用性群組的 SQL Server 執行個體</span><span class="sxs-lookup"><span data-stu-id="a28e1-167">Upgrade/Update SQL Server Instances with Multiple Availability Groups</span></span>  
 <span data-ttu-id="a28e1-168">如果您正在執行多個可用性群組，而其中的主要複本位於不同的伺服器節點上 (主動/主動組態)，則升級/更新路徑會牽涉到更多的容錯移轉步驟，以保留程序中的高可用性。</span><span class="sxs-lookup"><span data-stu-id="a28e1-168">If you are running multiple availability groups with primary replicas on separate server nodes (an Active/Active configuration), the upgrade/update path involves more failover steps to preserve high availability in the process.</span></span> <span data-ttu-id="a28e1-169">假設您在三個伺服器節點上執行三個可用性群組，如下表所示，則所有次要複本都會以同步認可模式執行。</span><span class="sxs-lookup"><span data-stu-id="a28e1-169">Suppose you are running three availability groups on three server nodes as shown in the following table, and all secondary replicas are running in synchronous-commit mode.</span></span>  
  
|<span data-ttu-id="a28e1-170">可用性群組</span><span class="sxs-lookup"><span data-stu-id="a28e1-170">Availability Group</span></span>|<span data-ttu-id="a28e1-171">Node1</span><span class="sxs-lookup"><span data-stu-id="a28e1-171">Node1</span></span>|<span data-ttu-id="a28e1-172">Node2</span><span class="sxs-lookup"><span data-stu-id="a28e1-172">Node2</span></span>|<span data-ttu-id="a28e1-173">Node3</span><span class="sxs-lookup"><span data-stu-id="a28e1-173">Node3</span></span>|  
|------------------------|-----------|-----------|-----------|  
|<span data-ttu-id="a28e1-174">AG1</span><span class="sxs-lookup"><span data-stu-id="a28e1-174">AG1</span></span>|<span data-ttu-id="a28e1-175">Primary</span><span class="sxs-lookup"><span data-stu-id="a28e1-175">Primary</span></span>|||  
|<span data-ttu-id="a28e1-176">AG2</span><span class="sxs-lookup"><span data-stu-id="a28e1-176">AG2</span></span>||<span data-ttu-id="a28e1-177">Primary</span><span class="sxs-lookup"><span data-stu-id="a28e1-177">Primary</span></span>||  
|<span data-ttu-id="a28e1-178">AG3</span><span class="sxs-lookup"><span data-stu-id="a28e1-178">AG3</span></span>|||<span data-ttu-id="a28e1-179">Primary</span><span class="sxs-lookup"><span data-stu-id="a28e1-179">Primary</span></span>|  
  
 <span data-ttu-id="a28e1-180">在您的案例中，可能適合依照以下順序執行負載平衡的輪流升級/更新：</span><span class="sxs-lookup"><span data-stu-id="a28e1-180">It may be appropriate in your situation to perform a load-balanced rolling upgrade/update in the following sequence:</span></span>  
  
1.  <span data-ttu-id="a28e1-181">將 AG2 容錯移轉到 Node3 (以釋出 Node2)</span><span class="sxs-lookup"><span data-stu-id="a28e1-181">Fail over AG2 to Node3 (to free up Node2)</span></span>  
  
2.  <span data-ttu-id="a28e1-182">升級/更新 Node2</span><span class="sxs-lookup"><span data-stu-id="a28e1-182">Upgrade/update Node2</span></span>  
  
3.  <span data-ttu-id="a28e1-183">將 AG1 容錯移轉到 Node2 (以釋出 Node1)</span><span class="sxs-lookup"><span data-stu-id="a28e1-183">Fail over AG1 to Node2 (to free up Node1)</span></span>  
  
4.  <span data-ttu-id="a28e1-184">升級/更新 Node1</span><span class="sxs-lookup"><span data-stu-id="a28e1-184">Upgrade/update Node1</span></span>  
  
5.  <span data-ttu-id="a28e1-185">將 AG2 和 AG3 容錯移轉到 Node1 (以釋出 Node3)</span><span class="sxs-lookup"><span data-stu-id="a28e1-185">Fail over both AG2 and AG3 to Node1 (to free up Node3)</span></span>  
  
6.  <span data-ttu-id="a28e1-186">升級/更新 Node3</span><span class="sxs-lookup"><span data-stu-id="a28e1-186">Upgrade/update Node3</span></span>  
  
7.  <span data-ttu-id="a28e1-187">將 AG3 容錯移轉到 Node3</span><span class="sxs-lookup"><span data-stu-id="a28e1-187">Fail over AG3 to Node3</span></span>  
  
 <span data-ttu-id="a28e1-188">此升級/更新順序的平均停機時間少於每個可用性群組的兩次容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="a28e1-188">This upgrade/update sequence has an average downtime of less than two failovers per availability group.</span></span> <span data-ttu-id="a28e1-189">產生的組態如下表所示。</span><span class="sxs-lookup"><span data-stu-id="a28e1-189">The resulting configuration is shown in the table below.</span></span>  
  
|<span data-ttu-id="a28e1-190">可用性群組</span><span class="sxs-lookup"><span data-stu-id="a28e1-190">Availability Group</span></span>|<span data-ttu-id="a28e1-191">Node1</span><span class="sxs-lookup"><span data-stu-id="a28e1-191">Node1</span></span>|<span data-ttu-id="a28e1-192">Node2</span><span class="sxs-lookup"><span data-stu-id="a28e1-192">Node2</span></span>|<span data-ttu-id="a28e1-193">Node3</span><span class="sxs-lookup"><span data-stu-id="a28e1-193">Node3</span></span>|  
|------------------------|-----------|-----------|-----------|  
|<span data-ttu-id="a28e1-194">AG1</span><span class="sxs-lookup"><span data-stu-id="a28e1-194">AG1</span></span>||<span data-ttu-id="a28e1-195">Primary</span><span class="sxs-lookup"><span data-stu-id="a28e1-195">Primary</span></span>||  
|<span data-ttu-id="a28e1-196">AG2</span><span class="sxs-lookup"><span data-stu-id="a28e1-196">AG2</span></span>|<span data-ttu-id="a28e1-197">Primary</span><span class="sxs-lookup"><span data-stu-id="a28e1-197">Primary</span></span>|||  
|<span data-ttu-id="a28e1-198">AG3</span><span class="sxs-lookup"><span data-stu-id="a28e1-198">AG3</span></span>|||<span data-ttu-id="a28e1-199">Primary</span><span class="sxs-lookup"><span data-stu-id="a28e1-199">Primary</span></span>|  
  
 <span data-ttu-id="a28e1-200">根據您的特定實作方式，您的升級/更新路徑可能會有不同，用戶端應用程式遇到的停機時間也可能會有差異。</span><span class="sxs-lookup"><span data-stu-id="a28e1-200">Based on your specific implementation, your upgrade/update path may vary, and the downtime that client applications experience may vary as well.</span></span>  
  
  
