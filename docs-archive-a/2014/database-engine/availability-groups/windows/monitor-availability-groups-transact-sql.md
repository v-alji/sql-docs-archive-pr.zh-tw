---
title: 監視可用性群組 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- dynamic management views [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], databases
- catalog views [SQL Server], AlwaysOn Availability Groups
ms.assetid: 881a34de-8461-4811-8c62-322bf7226bed
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 103dd8eef782dfa7a4d13929b0b832dba9bc46e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594189"
---
# <a name="monitor-availability-groups-transact-sql"></a><span data-ttu-id="a039e-102">監視可用性群組 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a039e-102">Monitor Availability Groups (Transact-SQL)</span></span>
  <span data-ttu-id="a039e-103">為了透過 [!INCLUDE[tsql](../../../includes/tsql-md.md)]監視可用性群組和複本，以及相關聯的資料庫， [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 提供一組目錄和動態管理檢視與伺服器屬性。</span><span class="sxs-lookup"><span data-stu-id="a039e-103">For monitoring availability groups and replicas and the associated databases by using [!INCLUDE[tsql](../../../includes/tsql-md.md)], [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] provides a set of catalog and dynamic management views and server properties.</span></span> <span data-ttu-id="a039e-104">您可以透過 [!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT 陳述式使用這些檢視來監視可用性群組及其複本和資料庫。</span><span class="sxs-lookup"><span data-stu-id="a039e-104">Using [!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT statements, you can use the views to monitor availability groups and their replicas and databases.</span></span> <span data-ttu-id="a039e-105">針對給定可用性群組所傳回的資訊取決於連接到的是裝載主要複本或次要複本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a039e-105">The information returned for a given availability group depends on whether you are connected to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is hosting the primary replica or a secondary replica.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="a039e-106">許多這些檢視可在單一查詢中聯結，透過檢視識別碼資料行從多個檢視傳回資訊。</span><span class="sxs-lookup"><span data-stu-id="a039e-106">Many of these views can be joined using their ID columns to return information from multiple views in a single query.</span></span>  
  
 
  
##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a039e-107">權限</span><span class="sxs-lookup"><span data-stu-id="a039e-107">Permissions</span></span>  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="a039e-108">目錄檢視需要伺服器執行個體的 VIEW ANY DEFINITION 權限。</span><span class="sxs-lookup"><span data-stu-id="a039e-108">catalog views require VIEW ANY DEFINITION permission on the server instance.</span></span> [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="a039e-109">動態管理檢視需要伺服器的 VIEW SERVER STATE 權限。</span><span class="sxs-lookup"><span data-stu-id="a039e-109">dynamic management views require VIEW SERVER STATE permission on the server.</span></span>  
  
##  <a name="monitoring-the-alwayson-availability-groups-feature-on-a-server-instance"></a><a name="AoAgFeatureOnSI"></a><span data-ttu-id="a039e-110">監視伺服器實例上的 AlwaysOn 可用性群組功能</span><span class="sxs-lookup"><span data-stu-id="a039e-110">Monitoring the AlwaysOn Availability Groups Feature on a Server Instance</span></span>  
 <span data-ttu-id="a039e-111">若要監視伺服器執行個體上的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 功能，請使用下列內建函數：</span><span class="sxs-lookup"><span data-stu-id="a039e-111">To monitor the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature on a server instance, use the following built-in function:</span></span>  
  
 <span data-ttu-id="a039e-112">[SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) 函數</span><span class="sxs-lookup"><span data-stu-id="a039e-112">[SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) function</span></span>  
 <span data-ttu-id="a039e-113">傳回有關 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 是否已啟用的伺服器屬性資訊，如果已啟用，也指出它是否已在伺服器執行個體上啟動。</span><span class="sxs-lookup"><span data-stu-id="a039e-113">Returns server property information about whether [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] is enabled and, if so, whether it has started on the server instance.</span></span>  
  
 <span data-ttu-id="a039e-114">**資料行名稱：** IsHadrEnabled、HadrManagerStatus</span><span class="sxs-lookup"><span data-stu-id="a039e-114">**Column names:** IsHadrEnabled, HadrManagerStatus</span></span>  
  
##  <a name="monitoring-availability-groups-on-the-wsfc-cluster"></a><a name="WSFC"></a> <span data-ttu-id="a039e-115">監視 WSFC 叢集中的可用性群組</span><span class="sxs-lookup"><span data-stu-id="a039e-115">Monitoring Availability Groups on the WSFC Cluster</span></span>  
 <span data-ttu-id="a039e-116">若要監視裝載已啟用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]之本機伺服器執行個體的 Windows Server 容錯移轉叢集 (WSFC) 叢集，請使用下列檢視：</span><span class="sxs-lookup"><span data-stu-id="a039e-116">To monitor the Windows Server Failover Clustering (WSFC) cluster that hosts a local server instance that is enabled for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], use the following views:</span></span>  
  
 [<span data-ttu-id="a039e-117">sys.dm_hadr_cluster</span><span class="sxs-lookup"><span data-stu-id="a039e-117">sys.dm_hadr_cluster</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql)  
 <span data-ttu-id="a039e-118">如果裝載已啟用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 之 SQL Server 執行個體的 Windows Server 容錯移轉叢集 (WSFC) 節點有 WSFC 仲裁，則 **sys.dm_hadr_cluster** 會傳回一個資料列，該資料列會公開叢集名稱以及有關此仲裁的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a039e-118">If the Windows Server Failover Clustering (WSFC) node that hosts an instance of SQL Server with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] enabled has WSFC quorum, **sys.dm_hadr_cluster** returns a row that exposes the cluster name and information about the quorum.</span></span> <span data-ttu-id="a039e-119">如果 WSFC 節點沒有仲裁，則不傳回任何資料列。</span><span class="sxs-lookup"><span data-stu-id="a039e-119">If the WSFC node has no quorum, no rows are returned.</span></span>  
  
 <span data-ttu-id="a039e-120">**資料行名稱：** cluster_name、quorum_type、quorum_type_desc、quorum_state、quorum_state_desc</span><span class="sxs-lookup"><span data-stu-id="a039e-120">**Column names:** cluster_name, quorum_type, quorum_type_desc, quorum_state, quorum_state_desc</span></span>  
  
 [<span data-ttu-id="a039e-121">sys.dm_hadr_cluster_members</span><span class="sxs-lookup"><span data-stu-id="a039e-121">sys.dm_hadr_cluster_members</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql)  
 <span data-ttu-id="a039e-122">如果裝載已啟用 AlwaysOn 之 SQL Server 本機執行個體的 WSFC 節點有 WSFC 仲裁，則針對構成仲裁的每個成員及其狀態各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="a039e-122">If the WSFC node that hosts the local AlwaysOn-enabled instance of SQL Server has WSFC quorum, returns a row for each of the members that constitute the quorum and the state of each of them.</span></span>  
  
 <span data-ttu-id="a039e-123">**資料行名稱：** member_name、member_type、member_type_desc、member_state、member_state_desc、number_of_quorum_votes</span><span class="sxs-lookup"><span data-stu-id="a039e-123">**Column names:** member_name, member_type, member_type_desc, member_state, member_state_desc, number_of_quorum_votes</span></span>  
  
 [<span data-ttu-id="a039e-124">sys.dm_hadr_cluster_networks</span><span class="sxs-lookup"><span data-stu-id="a039e-124">sys.dm_hadr_cluster_networks</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)  
 <span data-ttu-id="a039e-125">針對參與可用性群組之子網路組態的每個成員，各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="a039e-125">Returns a row for every member that is participating in an availability group's subnet configuration.</span></span> <span data-ttu-id="a039e-126">您可以使用此動態管理檢視來驗證為每個可用性複本所設定的網路虛擬 IP。</span><span class="sxs-lookup"><span data-stu-id="a039e-126">You can use this dynamic management view to validate the network virtual IP that is configured for each availability replica.</span></span>  
  
 <span data-ttu-id="a039e-127">**資料行名稱：** member_name、network_subnet_ip、network_subnet_ipv4_mask、network_subnet_prefix_length、is_public、is_ipv4</span><span class="sxs-lookup"><span data-stu-id="a039e-127">**Column names:** member_name, network_subnet_ip, network_subnet_ipv4_mask, network_subnet_prefix_length, is_public, is_ipv4</span></span>  
  
 <span data-ttu-id="a039e-128">**主索引鍵：** member_name + network_subnet_IP + network_subnet_prefix_length</span><span class="sxs-lookup"><span data-stu-id="a039e-128">**Primary key:** member_name + network_subnet_IP + network_subnet_prefix_length</span></span>  
  
 [<span data-ttu-id="a039e-129">sys.dm_hadr_instance_node_map</span><span class="sxs-lookup"><span data-stu-id="a039e-129">sys.dm_hadr_instance_node_map</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-instance-node-map-transact-sql)  
 <span data-ttu-id="a039e-130">對於裝載已聯結其 AlwaysOn 可用性群組之可用性複本的每個 SQL Server 執行個體，傳回裝載伺服器執行個體的 Windows Server 容錯移轉叢集 (WSFC) 節點名稱。</span><span class="sxs-lookup"><span data-stu-id="a039e-130">For every instance of SQL Server that hosts an availability replica that is joined to its AlwaysOn availability group, returns the name of the Windows Server Failover Clustering (WSFC) node that hosts the server instance.</span></span> <span data-ttu-id="a039e-131">這個動態管理檢視有下列用途：</span><span class="sxs-lookup"><span data-stu-id="a039e-131">This dynamic management view has the following uses:</span></span>  
  
-   <span data-ttu-id="a039e-132">這個動態管理檢視適用於偵測有多個可用性複本裝載於同一個 WSFC 節點的可用性群組，如果可用性群組不正確地設定，在 FCI 容錯移轉後可能會發生此不支援的組態狀況。</span><span class="sxs-lookup"><span data-stu-id="a039e-132">This dynamic management view is useful for detecting an availability group with multiple availability replicas that are hosted on the same WSFC node, which is an unsupported configuration that could occur after an FCI failover if the availability group is incorrectly configured.</span></span>  
  
-   <span data-ttu-id="a039e-133">當多個 SQL Server 執行個體裝載於同一個 WSFC 節點時，資源 DLL 會使用此動態管理檢視，判斷要連接的 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a039e-133">When multiple SQL Server instances are hosted on the same WSFC node, the Resource DLL uses this dynamic management view to determine the instance of SQL Server to connect to.</span></span>  
  
 <span data-ttu-id="a039e-134">**資料行名稱：** ag_resource_id、instance_name、node_name</span><span class="sxs-lookup"><span data-stu-id="a039e-134">**Column names:** ag_resource_id, instance_name, node_name</span></span>  
  
 [<span data-ttu-id="a039e-135">sys.dm_hadr_name_id_map</span><span class="sxs-lookup"><span data-stu-id="a039e-135">sys.dm_hadr_name_id_map</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-name-id-map-transact-sql)  
 <span data-ttu-id="a039e-136">顯示 SQL Server 目前執行個體已聯結之 AlwaysOn 可用性群組與三個唯一識別碼的對應：可用性群組識別碼、WSFC 資源識別碼和 WSFC 群組識別碼。</span><span class="sxs-lookup"><span data-stu-id="a039e-136">Shows the mapping of AlwaysOn availability groups that the current instance of SQL Server has joined to three unique IDs: an availability group ID, a WSFC resource ID, and a WSFC Group ID.</span></span> <span data-ttu-id="a039e-137">此對應的目的是要處理重新命名 WSFC 資源/群組的案例。</span><span class="sxs-lookup"><span data-stu-id="a039e-137">The purpose of this mapping is to handle the scenario in which the WSFC resource/group is renamed.</span></span>  
  
 <span data-ttu-id="a039e-138">**資料行名稱：** ag_name、ag_id、ag_resource_id、ag_group_id</span><span class="sxs-lookup"><span data-stu-id="a039e-138">**Column names:** ag_name, ag_id, ag_resource_id, ag_group_id</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a039e-139">另請參閱本主題稍後[監視可用性複本](#AvReplicas)一節中的 **sys.dm_hadr_availability_replica_cluster_nodes** 和 **sys.dm_hadr_availability_replica_cluster_states**，以及[監視可用性資料庫](#AvDbs)一節中的 **sys.availability_databases_cluster** 和 **sys.dm_hadr_database_replica_cluster_states**。</span><span class="sxs-lookup"><span data-stu-id="a039e-139">Also see **sys.dm_hadr_availability_replica_cluster_nodes** and **sys.dm_hadr_availability_replica_cluster_states** in the [Monitoring Availability Replicas](#AvReplicas) section and **sys.availability_databases_cluster** and **sys.dm_hadr_database_replica_cluster_states** in the [Monitoring Availability Databases](#AvDbs) section, later in this topic.</span></span>  
  
 <span data-ttu-id="a039e-140">如需 WSFC 叢集和的詳細資訊 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ，請參閱[Windows Server 容錯移轉叢集 &#40;WSFC&#41; 搭配 SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)和[容錯移轉叢集和 AlwaysOn 可用性群組 &#40;](failover-clustering-and-always-on-availability-groups-sql-server.md)SQL Server&#41;。</span><span class="sxs-lookup"><span data-stu-id="a039e-140">For information about WSFC clusters and [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], see [Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) and [Failover Clustering and AlwaysOn Availability Groups &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md).</span></span>  
  
##  <a name="monitoring-availability-groups"></a><a name="AvGroups"></a> <span data-ttu-id="a039e-141">監視可用性群組</span><span class="sxs-lookup"><span data-stu-id="a039e-141">Monitoring Availability Groups</span></span>  
 <span data-ttu-id="a039e-142">若要監視伺服器執行個體裝載其可用性複本的可用性群組，請使用下列檢視：</span><span class="sxs-lookup"><span data-stu-id="a039e-142">To monitor the availability groups for which the server instance hosts an availability replica, use the following views:</span></span>  
  
 [<span data-ttu-id="a039e-143">sys.availability_groups</span><span class="sxs-lookup"><span data-stu-id="a039e-143">sys.availability_groups</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)  
 <span data-ttu-id="a039e-144">針對裝載可用性複本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 本機執行個體的每一個可用性群組，各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="a039e-144">Returns a row for each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hosts an availability replica.</span></span> <span data-ttu-id="a039e-145">每一個資料列都包含可用性群組中繼資料的快取副本。</span><span class="sxs-lookup"><span data-stu-id="a039e-145">Each row contains a cached copy of the availability group metadata.</span></span>  
  
 <span data-ttu-id="a039e-146">**資料行名稱：** group_id、name、resource_id、resource_group_id、failure_condition_level、health_check_timeout、automated_backup_preference、automated_backup_preference_desc</span><span class="sxs-lookup"><span data-stu-id="a039e-146">**Column names:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span></span>  
  
 [<span data-ttu-id="a039e-147">sys.availability_groups_cluster</span><span class="sxs-lookup"><span data-stu-id="a039e-147">sys.availability_groups_cluster</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-cluster-transact-sql)  
 <span data-ttu-id="a039e-148">針對 WSFC 叢集中的每一個可用性群組，各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="a039e-148">Returns a row for each availability group in the WSFC cluster.</span></span> <span data-ttu-id="a039e-149">每個資料列都包含 Windows Server 容錯移轉叢集 (WSFC) 叢集中的可用性群組中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a039e-149">Each row contains the availability group metadata from the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="a039e-150">**資料行名稱：** group_id、name、resource_id、resource_group_id、failure_condition_level、health_check_timeout、automated_backup_preference、automated_backup_preference_desc</span><span class="sxs-lookup"><span data-stu-id="a039e-150">**Column names:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span></span>  
  
 [<span data-ttu-id="a039e-151">sys.dm_hadr_availability_group_states</span><span class="sxs-lookup"><span data-stu-id="a039e-151">sys.dm_hadr_availability_group_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql)  
 <span data-ttu-id="a039e-152">針對擁有 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]本機執行個體之可用性複本的每一個可用性群組，各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="a039e-152">Returns a row for each availability group that possesses an availability replica on the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a039e-153">每個資料列會顯示定義給定之可用性群組健全狀況的狀態。</span><span class="sxs-lookup"><span data-stu-id="a039e-153">Each row displays the states that define the health of a given availability group.</span></span>  
  
 <span data-ttu-id="a039e-154">**資料行名稱：** group_id、primary_replica、primary_recovery_health、primary_recovery_health_desc、secondary_recovery_health、secondary_recovery_health_desc、synchronization_health、synchronization_health_desc</span><span class="sxs-lookup"><span data-stu-id="a039e-154">**Column names:** group_id, primary_replica, primary_recovery_health, primary_recovery_health_desc, secondary_recovery_health, secondary_recovery_health_desc, synchronization_health, synchronization_health_desc</span></span>  
  
##  <a name="monitoring-availability-replicas"></a><a name="AvReplicas"></a><span data-ttu-id="a039e-155">監視可用性複本</span><span class="sxs-lookup"><span data-stu-id="a039e-155">Monitoring Availability Replicas</span></span>  
 <span data-ttu-id="a039e-156">若要監視可用性複本，請使用下列檢視和系統函數：</span><span class="sxs-lookup"><span data-stu-id="a039e-156">To monitor availability replicas, use the following views and system function:</span></span>  
  
 [<span data-ttu-id="a039e-157">sys.availability_replicas</span><span class="sxs-lookup"><span data-stu-id="a039e-157">sys.availability_replicas</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)  
 <span data-ttu-id="a039e-158">針對每一個可用性群組中的每一個可用性複本 ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 本機執行個體裝載此群組的可用性複本)，各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="a039e-158">Returns a row for every availability replica in each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hosts an availability replica.</span></span>  
  
 <span data-ttu-id="a039e-159">**資料行名稱：** replica_id、group_id、replica_metadata_id、replica_server_name、owner_sid、endpoint_url、availability_mode、availability_mode_desc、failover_mode、failover_mode_desc、session_timeout、primary_role_allow_connections、primary_role_allow_connections_desc、secondary_role_allow_connections、secondary_role_allow_connections_desc、create_date、modify_date、backup_priority、read_only_routing_url</span><span class="sxs-lookup"><span data-stu-id="a039e-159">**Column names:** replica_id, group_id, replica_metadata_id, replica_server_name, owner_sid, endpoint_url, availability_mode, availability_mode_desc, failover_mode, failover_mode_desc, session_timeout, primary_role_allow_connections, primary_role_allow_connections_desc, secondary_role_allow_connections, secondary_role_allow_connections_desc, create_date, modify_date, backup_priority, read_only_routing_url</span></span>  
  
 [<span data-ttu-id="a039e-160">sys.availability_read_only_routing_lists</span><span class="sxs-lookup"><span data-stu-id="a039e-160">sys.availability_read_only_routing_lists</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
 <span data-ttu-id="a039e-161">針對 WSFC 容錯移轉叢集中 AlwaysOn 可用性群組內每個可用性複本的唯讀路由清單，各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="a039e-161">Returns a row for the read only routing list of each availability replica in an AlwaysOn availability group in the WSFC failover cluster.</span></span>  
  
 <span data-ttu-id="a039e-162">**資料行名稱：** replica_id、routing_priority、read_only_replica_id</span><span class="sxs-lookup"><span data-stu-id="a039e-162">**Column names:** replica_id, routing_priority, read_only_replica_id</span></span>  
  
 [<span data-ttu-id="a039e-163">監視可用性複本</span><span class="sxs-lookup"><span data-stu-id="a039e-163">sys.dm_hadr_availability_replica_cluster_nodes</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-nodes-transact-sql)  
 <span data-ttu-id="a039e-164">針對 Windows Server 容錯移轉叢集 (WSFC) 叢集中 AlwaysOn 可用性群組的每一個可用性複本 (不論聯結狀態為何)，各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="a039e-164">Returns a row for every availability replica (regardless of join state) of the AlwaysOn availability groups in the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="a039e-165">**資料行名稱：** group_name、replica_server_name、node_name</span><span class="sxs-lookup"><span data-stu-id="a039e-165">**Column names:** group_name, replica_server_name, node_name</span></span>  
  
 [<span data-ttu-id="a039e-166">sys.dm_hadr_availability_replica_cluster_nodes</span><span class="sxs-lookup"><span data-stu-id="a039e-166">sys.dm_hadr_availability_replica_cluster_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
 <span data-ttu-id="a039e-167">針對 Windows Server 容錯移轉叢集 (WSFC) 叢集中所有 AlwaysOn 可用性群組 (不論複本位置為何) 的每一個複本 (不論聯結狀態為何) 各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="a039e-167">Returns a row for each replica (regardless of join state) of all AlwaysOn availability groups (regardless of replica location) in the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="a039e-168">**資料行名稱：** replica_id、replica_server_name、group_id、join_state、join_state_desc</span><span class="sxs-lookup"><span data-stu-id="a039e-168">**Column names:** replica_id, replica_server_name, group_id, join_state, join_state_desc</span></span>  
  
 [<span data-ttu-id="a039e-169">sys.dm_hadr_availability_replica_states</span><span class="sxs-lookup"><span data-stu-id="a039e-169">sys.dm_hadr_availability_replica_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)  
 <span data-ttu-id="a039e-170">傳回顯示每個本機可用性複本之狀態的資料列，並針對同一個可用性群組中每一個遠端可用性複本，各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="a039e-170">Returns a row showing the state of each local availability replica and a row for each remote availability replica in the same availability group.</span></span>  
  
 <span data-ttu-id="a039e-171">**資料行名稱：** replica_id、group_id、is_local、role、role_desc、operational_state、operational_state_desc、connected_state、connected_state_desc、recovery_health、recovery_health_desc、synchronization_health、synchronization_health_desc、last_connect_error_number、last_connect_error_description 和 last_connect_error_timestamp</span><span class="sxs-lookup"><span data-stu-id="a039e-171">**Column names:** replica_id, group_id, is_local, role, role_desc, operational_state, operational_state_desc, connected_state, connected_state_desc, recovery_health, recovery_health_desc, synchronization_health, synchronization_health_desc, last_connect_error_number, last_connect_error_description, and last_connect_error_timestamp</span></span>  
  
 [<span data-ttu-id="a039e-172">sys.fn_hadr_backup_is_preferred_replica</span><span class="sxs-lookup"><span data-stu-id="a039e-172">sys.fn_hadr_backup_is_preferred_replica</span></span>](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
 <span data-ttu-id="a039e-173">判斷目前的複本是否為慣用的備份複本。</span><span class="sxs-lookup"><span data-stu-id="a039e-173">Determines whether the current replica is the preferred backup replica.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a039e-174">如需可用性複本效能計數器 ( **SQLServer:Availability Replica**  效能物件) 的相關資訊，請參閱 [SQL Server、可用性複本](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)。</span><span class="sxs-lookup"><span data-stu-id="a039e-174">For information about performance counters for availability replicas (the **SQLServer:Availability Replica**  performance object), see [SQL Server, Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).</span></span>  
  
##  <a name="monitoring-availability-databases"></a><a name="AvDbs"></a> <span data-ttu-id="a039e-175">sys.dm_hadr_database_replica_cluster_states</span><span class="sxs-lookup"><span data-stu-id="a039e-175">Monitoring Availability Databases</span></span>  
 <span data-ttu-id="a039e-176">若要監視可用性資料庫，請使用下列檢視：</span><span class="sxs-lookup"><span data-stu-id="a039e-176">To monitor availability databases, use the following views:</span></span>  
  
 [<span data-ttu-id="a039e-177">監視可用性資料庫</span><span class="sxs-lookup"><span data-stu-id="a039e-177">sys.availability_databases_cluster</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-databases-cluster-transact-sql)  
 <span data-ttu-id="a039e-178">針對屬於叢集中所有 AlwaysOn 可用性群組的 SQL Server 執行個體上的每一個資料庫，各包含一個資料列，無論本機資料庫副本是否已聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="a039e-178">Contains one row for each database on the instance of SQL Server that are part of all AlwaysOn Availability Groups in the cluster, regardless of whether the local copy database has been joined to the availability group yet.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a039e-179">當資料庫加入至可用性群組時，主要資料庫會自動聯結至此群組。</span><span class="sxs-lookup"><span data-stu-id="a039e-179">When a database is added to an availability group, the primary database is automatically joined to the group.</span></span> <span data-ttu-id="a039e-180">次要資料庫必須先在每個次要複本上備妥，然後才能聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="a039e-180">Secondary databases must be prepared on each secondary replica before they can be joined to the availability group.</span></span>  
  
 <span data-ttu-id="a039e-181">**資料行名稱：** group_id、group_database_id、database_name</span><span class="sxs-lookup"><span data-stu-id="a039e-181">**Column names:** group_id, group_database_id, database_name</span></span>  
  
 [<span data-ttu-id="a039e-182">sys.databases</span><span class="sxs-lookup"><span data-stu-id="a039e-182">sys.databases</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
 <span data-ttu-id="a039e-183">針對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體中的每個資料庫，各包含一個資料列。</span><span class="sxs-lookup"><span data-stu-id="a039e-183">Contains one row per database in the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a039e-184">如果資料庫屬於某個可用性複本，該資料庫的資料列會顯示複本的 GUID，以及資料庫在其可用性群組內的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="a039e-184">If a database belongs to an availability replica, the row for that database displays the GUID of the replica and the unique identifier of the database within its availability group.</span></span>  
  
 <span data-ttu-id="a039e-185">資料\*\* [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 行名稱：\*\* replica_id、group_database_id</span><span class="sxs-lookup"><span data-stu-id="a039e-185">**[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] column names:** replica_id, group_database_id</span></span>  
  
 [<span data-ttu-id="a039e-186">sys.dm_hadr_auto_page_repair</span><span class="sxs-lookup"><span data-stu-id="a039e-186">sys.dm_hadr_auto_page_repair</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-auto-page-repair-transact-sql)  
 <span data-ttu-id="a039e-187">針對可用性複本上的任何可用性資料庫進行的每個自動修復頁面嘗試行為，各傳回一個資料列，該可用性複本是針對伺服器執行個體的任何可用性群組所裝載。</span><span class="sxs-lookup"><span data-stu-id="a039e-187">Returns a row for every automatic page-repair attempt on any availability database on an availability replica that is hosted for any availability group by the server instance.</span></span> <span data-ttu-id="a039e-188">這個檢視包含在給定之主要或次要資料庫上進行最新自動修復頁面嘗試行為的資料列，而且每個資料庫最多 100 個資料列。</span><span class="sxs-lookup"><span data-stu-id="a039e-188">This view contains rows for the latest automatic page-repair attempts on a given primary or secondary database, with a maximum of 100 rows per database.</span></span> <span data-ttu-id="a039e-189">一旦資料庫到達上限時，下一個自動修復頁面嘗試行為的資料列就會取代其中一個現有的項目。</span><span class="sxs-lookup"><span data-stu-id="a039e-189">As soon as a database reaches the maximum, the row for its next automatic page-repair attempt replaces one of the existing entries.</span></span>  
  
 <span data-ttu-id="a039e-190">**資料行名稱：** database_id、file_id、page_id、error_type、page_status、modification_time</span><span class="sxs-lookup"><span data-stu-id="a039e-190">**Column names:** database_id, file_id, page_id, error_type, page_status, modification_time</span></span>  
  
 [<span data-ttu-id="a039e-191">sys.dm_hadr_database_replica_states</span><span class="sxs-lookup"><span data-stu-id="a039e-191">sys.dm_hadr_database_replica_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql)  
 <span data-ttu-id="a039e-192">針對參與任何可用性群組的每一個資料庫 ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 本機執行個體正在裝載此群組的可用性複本)，各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="a039e-192">Returns a row for each database that is participating in any availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is hosting an availability replica.</span></span>  
  
 <span data-ttu-id="a039e-193">**資料行名稱：** database_id、group_id、replica_id、group_database_id、is_local、synchronization_state、synchronization_state_desc、is_commit_participant、synchronization_health、synchronization_health_desc、database_state、database_state_desc、is_suspended、suspend_reason、suspend_reason_desc、recovery_lsn、truncation_lsn、last_sent_lsn、last_sent_time、last_received_lsn、last_received_time、last_hardened_lsn、last_hardened_time、last_redone_lsn、last_redone_time、log_send_queue_size、log_send_rate、redo_queue_size、redo_rate、filestream_send_rate、end_of_log_lsn、last_commit_lsn、last_commit_time、low_water_mark_for_ghosts</span><span class="sxs-lookup"><span data-stu-id="a039e-193">**Column names:** database_id, group_id, replica_id, group_database_id, is_local, synchronization_state, synchronization_state_desc, is_commit_participant, synchronization_health, synchronization_health_desc, database_state, database_state_desc, is_suspended, suspend_reason, suspend_reason_desc, recovery_lsn, truncation_lsn, last_sent_lsn, last_sent_time, last_received_lsn, last_received_time, last_hardened_lsn, last_hardened_time, last_redone_lsn, last_redone_time, log_send_queue_size, log_send_rate, redo_queue_size, redo_rate, filestream_send_rate, end_of_log_lsn, last_commit_lsn, last_commit_time, low_water_mark_for_ghosts</span></span>  
  
 [<span data-ttu-id="a039e-194">sys.availability_databases_cluster</span><span class="sxs-lookup"><span data-stu-id="a039e-194">sys.dm_hadr_database_replica_cluster_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql)  
 <span data-ttu-id="a039e-195">傳回包含資訊的資料列，該資訊的目的是為了讓您深入了解 Windows Server 容錯移轉叢集 (WSFC) 叢集中每個可用性群組內可用性資料庫的健全狀況。</span><span class="sxs-lookup"><span data-stu-id="a039e-195">Returns a row containing information intended to provide you with insight into the health of the availability databases in each availability group on the Windows Server Failover Clustering (WSFC) cluster.</span></span> <span data-ttu-id="a039e-196">當您計劃或回應容錯移轉，或要探索可用性群組中哪個次要複本阻止給定之主要資料庫的記錄截斷時，這個動態管理檢視相當實用。</span><span class="sxs-lookup"><span data-stu-id="a039e-196">This dynamic management view is useful when planning or responding to a failover or for discovering which secondary replica in an availability group is holding up log truncation on a given primary database.</span></span>  
  
 <span data-ttu-id="a039e-197">**資料行名稱：** replica_id、group_database_id、database_name、is_failover_ready、is_pending_secondary_suspend、is_database_joined、recovery_lsn、truncation_lsn</span><span class="sxs-lookup"><span data-stu-id="a039e-197">**Column names:** replica_id, group_database_id, database_name, is_failover_ready, is_pending_secondary_suspend, is_database_joined, recovery_lsn, truncation_lsn</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a039e-198">主要複本位置是可用性群組的授權來源。</span><span class="sxs-lookup"><span data-stu-id="a039e-198">The primary replica location is the authoritative source for an availability group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a039e-199">如需可用性資料庫 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 效能計數器 ( **SQLServer:Database Replica** 效能物件) 的相關資訊，請參閱 [SQL Server、資料庫複本](../../../relational-databases/performance-monitor/sql-server-database-replica.md)。</span><span class="sxs-lookup"><span data-stu-id="a039e-199">For information about the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] performance counters for availability databases (the **SQLServer:Database Replica** performance object), see [SQL Server, Database Replica](../../../relational-databases/performance-monitor/sql-server-database-replica.md).</span></span> <span data-ttu-id="a039e-200">此外，若要監視可用性資料庫上的交易記錄活動，請使用**SQLServer：** database 效能物件的下列計數器：記錄排清**寫入時間 (ms) **、記錄檔排清 **/秒**、**記錄集**區快取遺漏/秒、 **Log pool Disk Reads/sec**和**log pool Requests/sec**。如需詳細資訊，請參閱[SQL Server，資料庫物件](../../../relational-databases/performance-monitor/sql-server-databases-object.md)。</span><span class="sxs-lookup"><span data-stu-id="a039e-200">Also, to monitor transaction-log activity on availability databases, use the following counters of the **SQLServer:Databases** performance object: **Log Flush Write Time (ms)**, **Log Flushes/sec**, **Log Pool Cache Misses/sec**, **Log Pool Disk Reads/sec**, and **Log Pool Requests/sec**. For more information, see [SQL Server, Databases Object](../../../relational-databases/performance-monitor/sql-server-databases-object.md).</span></span>  
  
##  <a name="monitoring-availability-group-listeners"></a><a name="AGlisteners"></a> <span data-ttu-id="a039e-201">監視可用性群組接聽程式</span><span class="sxs-lookup"><span data-stu-id="a039e-201">Monitoring Availability Group Listeners</span></span>  
 <span data-ttu-id="a039e-202">若要監視 WSFC 叢集子網路上的可用性群組接聽程式，請使用下列檢視：</span><span class="sxs-lookup"><span data-stu-id="a039e-202">To monitor the availability group listeners on subnets of the WSFC cluster, use the following views:</span></span>  
  
 [<span data-ttu-id="a039e-203">sys.availability_group_listener_ip_addresses</span><span class="sxs-lookup"><span data-stu-id="a039e-203">sys.availability_group_listener_ip_addresses</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listener-ip-addresses-transact-sql)  
 <span data-ttu-id="a039e-204">針對目前上線供可用性群組接聽程式使用的每個符合標準虛擬 IP 位址傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="a039e-204">Returns a row for every conformant virtual IP address that is currently online for an availability group listener.</span></span>  
  
 <span data-ttu-id="a039e-205">**資料行名稱** ：listener_id、ip_address、ip_subnet_mask、is_dhcp、network_subnet_ip、network_subnet_prefix_length、network_subnet_ipv4_mask、state、state_desc</span><span class="sxs-lookup"><span data-stu-id="a039e-205">**Column names:** listener_id, ip_address, ip_subnet_mask, is_dhcp, network_subnet_ip, network_subnet_prefix_length, network_subnet_ipv4_mask, state, state_desc</span></span>  
  
 [<span data-ttu-id="a039e-206">sys.availability_group_listeners</span><span class="sxs-lookup"><span data-stu-id="a039e-206">sys.availability_group_listeners</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listeners-transact-sql)  
 <span data-ttu-id="a039e-207">若為給定的可用性群組，傳回零個資料列，表示沒有網路名稱與可用性群組相關聯，或針對 WSFC 叢集中的每個可用性群組接聽程式組態傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="a039e-207">For a given availability group, returns either zero rows indicating that no network name is associated with the availability group, or returns a row for each availability-group listener configuration in the WSFC cluster.</span></span>  
  
 <span data-ttu-id="a039e-208">**資料行名稱** ：group_id、listener_id、dns_name、port、is_conformant、ip_configuration_string_from_cluster</span><span class="sxs-lookup"><span data-stu-id="a039e-208">**Column names:** group_id, listener_id, dns_name, port, is_conformant, ip_configuration_string_from_cluster</span></span>  
  
 [<span data-ttu-id="a039e-209">sys.dm_tcp_listener_states</span><span class="sxs-lookup"><span data-stu-id="a039e-209">sys.dm_tcp_listener_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql)  
 <span data-ttu-id="a039e-210">針對每個 TCP 接聽程式傳回一個包含動態狀態資訊的資料列。</span><span class="sxs-lookup"><span data-stu-id="a039e-210">Returns a row containing dynamic-state information for each TCP listener.</span></span>  
  
 <span data-ttu-id="a039e-211">**資料行名稱：** listener_id、ip_address、is_ipv4、port、type、type_desc、state、state_desc、start_time</span><span class="sxs-lookup"><span data-stu-id="a039e-211">**Column names:** listener_id, ip_address, is_ipv4, port, type, type_desc, state, state_desc, start_time</span></span>  
  
 <span data-ttu-id="a039e-212">**主索引鍵：** listener_id</span><span class="sxs-lookup"><span data-stu-id="a039e-212">**Primary key:** listener_id</span></span>  
  
 <span data-ttu-id="a039e-213">如需可用性群組接聽程式的相關資訊，請參閱[可用性群組接聽程式、用戶端連接性及應用程式容錯移轉 &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)。</span><span class="sxs-lookup"><span data-stu-id="a039e-213">For information about availability group listeners, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a039e-214">相關工作</span><span class="sxs-lookup"><span data-stu-id="a039e-214">Related Tasks</span></span>  
 <span data-ttu-id="a039e-215">**AlwaysOn 可用性群組監視工作：**</span><span class="sxs-lookup"><span data-stu-id="a039e-215">**AlwaysOn Availability Groups monitoring tasks:**</span></span>  
  
-   [<span data-ttu-id="a039e-216">使用物件總管詳細資料監視可用性群組 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-216">Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;</span></span>](use-object-explorer-details-to-monitor-availability-groups.md)  
  
-   [<span data-ttu-id="a039e-217">檢視可用性群組屬性 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-217">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)  
  
-   [<span data-ttu-id="a039e-218">檢視可用性複本屬性 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-218">View Availability Replica Properties &#40;SQL Server&#41;</span></span>](view-availability-replica-properties-sql-server.md)  
  
-   [<span data-ttu-id="a039e-219">檢視可用性群組接聽程式屬性 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-219">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
 <span data-ttu-id="a039e-220">**AlwaysOn 可用性群組監視參考 (Transact-SQL)：**</span><span class="sxs-lookup"><span data-stu-id="a039e-220">**AlwaysOn Availability Groups monitoring reference (Transact-SQL):**</span></span>  
  
-   [<span data-ttu-id="a039e-221">SERVERPROPERTY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-221">SERVERPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)  
  
-   [<span data-ttu-id="a039e-222">sys.availability_group_listener_ip_addresses &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-222">sys.availability_group_listener_ip_addresses &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listener-ip-addresses-transact-sql)  
  
-   [<span data-ttu-id="a039e-223">sys.availability_group_listeners &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-223">sys.availability_group_listeners &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listeners-transact-sql)  
  
-   [<span data-ttu-id="a039e-224">sys.availability_databases_cluster &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-224">sys.availability_databases_cluster &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-databases-cluster-transact-sql)  
  
-   [<span data-ttu-id="a039e-225">sys.availability_groups &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-225">sys.availability_groups &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)  
  
-   [<span data-ttu-id="a039e-226">sys.availability_read_only_routing_lists &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-226">sys.availability_read_only_routing_lists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
  
-   [<span data-ttu-id="a039e-227">sys.availability_replicas &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-227">sys.availability_replicas &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)  
  
-   [<span data-ttu-id="a039e-228">sys.dm_hadr_availability_replica_cluster_nodes &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-228">sys.dm_hadr_availability_replica_cluster_nodes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-nodes-transact-sql)  
  
-   [<span data-ttu-id="a039e-229">sys.dm_hadr_availability_replica_cluster_states &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-229">sys.dm_hadr_availability_replica_cluster_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
  
-   [<span data-ttu-id="a039e-230">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-230">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
-   [<span data-ttu-id="a039e-231">sys.dm_hadr_auto_page_repair &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-231">sys.dm_hadr_auto_page_repair &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-auto-page-repair-transact-sql)  
  
-   [<span data-ttu-id="a039e-232">sys.dm_hadr_availability_group_states &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-232">sys.dm_hadr_availability_group_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql)  
  
-   [<span data-ttu-id="a039e-233">sys.dm_hadr_availability_replica_cluster_states &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-233">sys.dm_hadr_availability_replica_cluster_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
  
-   [<span data-ttu-id="a039e-234">sys.dm_hadr_availability_replica_states &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-234">sys.dm_hadr_availability_replica_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)  
  
-   [<span data-ttu-id="a039e-235">sys.dm_hadr_database_replica_states &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-235">sys.dm_hadr_database_replica_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql)  
  
-   [<span data-ttu-id="a039e-236">sys.dm_hadr_database_replica_cluster_states &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-236">sys.dm_hadr_database_replica_cluster_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql)  
  
-   [<span data-ttu-id="a039e-237">sys.dm_hadr_cluster &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-237">sys.dm_hadr_cluster &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql)  
  
-   [<span data-ttu-id="a039e-238">sys.dm_hadr_cluster_members &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-238">sys.dm_hadr_cluster_members &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql)  
  
-   [<span data-ttu-id="a039e-239">sys.dm_hadr_cluster_networks &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-239">sys.dm_hadr_cluster_networks &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)  
  
-   [<span data-ttu-id="a039e-240">sys.dm_hadr_database_replica_cluster_states &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-240">sys.dm_hadr_database_replica_cluster_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql)  
  
-   [<span data-ttu-id="a039e-241">sys.dm_hadr_database_replica_states &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-241">sys.dm_hadr_database_replica_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql)  
  
-   [<span data-ttu-id="a039e-242">sys.dm_hadr_instance_node_map &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-242">sys.dm_hadr_instance_node_map &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-instance-node-map-transact-sql)  
  
-   [<span data-ttu-id="a039e-243">sys.dm_hadr_name_id_map &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-243">sys.dm_hadr_name_id_map &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-name-id-map-transact-sql)  
  
-   [<span data-ttu-id="a039e-244">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-244">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
-   [<span data-ttu-id="a039e-245">sys.dm_tcp_listener_states &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-245">sys.dm_tcp_listener_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql)  
  
-   [<span data-ttu-id="a039e-246">sys.fn_hadr_backup_is_preferred_replica &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-246">sys.fn_hadr_backup_is_preferred_replica  &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
  
 <span data-ttu-id="a039e-247">**AlwaysOn 效能計數器：**</span><span class="sxs-lookup"><span data-stu-id="a039e-247">**AlwaysOn performance counters:**</span></span>  
  
-   [<span data-ttu-id="a039e-248">SQL Server、可用性複本</span><span class="sxs-lookup"><span data-stu-id="a039e-248">SQL Server, Availability Replica</span></span>](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)  
  
-   [<span data-ttu-id="a039e-249">SQL Server 的 Database Replica</span><span class="sxs-lookup"><span data-stu-id="a039e-249">SQL Server, Database Replica</span></span>](../../../relational-databases/performance-monitor/sql-server-database-replica.md)  
  
-   [<span data-ttu-id="a039e-250">SQL Server, Databases Object</span><span class="sxs-lookup"><span data-stu-id="a039e-250">SQL Server, Databases Object</span></span>](../../../relational-databases/performance-monitor/sql-server-databases-object.md)  
  
 <span data-ttu-id="a039e-251">**AlwaysOn 可用性群組的原則式管理**</span><span class="sxs-lookup"><span data-stu-id="a039e-251">**Policy-based management for AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="a039e-252">使用 AlwaysOn 原則來查看可用性群組的健全狀況 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-252">Use AlwaysOn Policies to View the Health of an Availability Group &#40;SQL Server&#41;</span></span>](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="a039e-253">使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-253">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="a039e-254">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a039e-254">See Also</span></span>  
 <span data-ttu-id="a039e-255">[AlwaysOn 可用性群組 (SQL Server) ](always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a039e-255">[AlwaysOn Availability Groups (SQL Server)](always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="a039e-256">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a039e-256">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="a039e-257">監視可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a039e-257">Monitoring of Availability Groups &#40;SQL Server&#41;</span></span>](monitoring-of-availability-groups-sql-server.md)  
  
  
