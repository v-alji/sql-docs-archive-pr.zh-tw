---
title: 檢視可用性複本屬性 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- ', policies'
ms.assetid: 14fed3c4-8ecc-4e1c-931d-a7ec1e9f9e90
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6ca7b0508907b4d86c9ee627438a3f18e1b01fdc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701911"
---
# <a name="view-availability-replica-properties-sql-server"></a><span data-ttu-id="33cfb-102">檢視可用性複本屬性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="33cfb-102">View Availability Replica Properties (SQL Server)</span></span>
  <span data-ttu-id="33cfb-103">此主題描述如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，檢視 AlwaysOn 可用性群組的可用性複本屬性。</span><span class="sxs-lookup"><span data-stu-id="33cfb-103">This topic describes how to view the properties of an availability replica for an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="33cfb-104">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="33cfb-104">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="33cfb-105">**若要檢視及變更可用性複本的屬性**</span><span class="sxs-lookup"><span data-stu-id="33cfb-105">**To view and change properties an availability replica**</span></span>  
  
1.  <span data-ttu-id="33cfb-106">在 [物件總管] 中，連接到裝載主要複本的伺服器執行個體，然後展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="33cfb-106">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="33cfb-107">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="33cfb-107">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="33cfb-108">展開可用性複本所屬的可用性群組，然後展開 **[可用性複本]** 節點。</span><span class="sxs-lookup"><span data-stu-id="33cfb-108">Expand the availability group to which the availability replica belongs, and expand the **Availability Replicas** node.</span></span>  
  
4.  <span data-ttu-id="33cfb-109">以滑鼠右鍵按一下要檢視其屬性的可用性複本，然後選取 [屬性]\*\*\*\* 命令。</span><span class="sxs-lookup"><span data-stu-id="33cfb-109">Right-click the availability replica whose properties you want to view, and select the **Properties** command.</span></span>  
  
5.  <span data-ttu-id="33cfb-110">在 **[可用性複本屬性]** 對話方塊中，使用 **[一般]** 頁面檢視此複本的屬性。</span><span class="sxs-lookup"><span data-stu-id="33cfb-110">In the **Availability Replica Properties** dialog box, use the **General** page to view the properties of this replica.</span></span> <span data-ttu-id="33cfb-111">如果您連接至主要複本，可以變更下列屬性：可用性模式、容錯移轉模式、主要角色的連接存取、次要角色的唯讀存取 (可讀取的次要)，以及工作階段逾時值。</span><span class="sxs-lookup"><span data-stu-id="33cfb-111">If you are connected to the primary replica, you can change the following properties: availability mode, failover mode, connection access for the primary role, read-access for the secondary role (readable-secondary), and the session-timeout value.</span></span> <span data-ttu-id="33cfb-112">如需詳細資訊，請參閱[可用性複本屬性 &#40;一般頁面&#41;](availability-replica-properties-general-page.md)。</span><span class="sxs-lookup"><span data-stu-id="33cfb-112">For more information, see  [Availability Replica Properties &#40;General Page&#41;](availability-replica-properties-general-page.md).</span></span>  
  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="33cfb-113">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="33cfb-113">Using Transact-SQL</span></span>  
 <span data-ttu-id="33cfb-114">**若要檢視可用性複本的屬性和狀態**</span><span class="sxs-lookup"><span data-stu-id="33cfb-114">**To view properties and states of availability replicas**</span></span>  
  
 <span data-ttu-id="33cfb-115">若要檢視可用性複本的屬性和狀態，請使用下列檢視和系統函數：</span><span class="sxs-lookup"><span data-stu-id="33cfb-115">To view the properties and states of availability replicas, use the following views and system function:</span></span>  
  
 [<span data-ttu-id="33cfb-116">sys.availability_replicas</span><span class="sxs-lookup"><span data-stu-id="33cfb-116">sys.availability_replicas</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)  
 <span data-ttu-id="33cfb-117">針對每一個可用性群組中的每一個可用性複本 ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 本機執行個體裝載此群組的可用性複本)，各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="33cfb-117">Returns a row for every availability replica in each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hosts an availability replica.</span></span>  
  
 <span data-ttu-id="33cfb-118">**資料行名稱：** replica_id、group_id、replica_metadata_id、replica_server_name、owner_sid、endpoint_url、availability_mode、availability_mode_desc、failover_mode、failover_mode_desc、session_timeout、primary_role_allow_connections、primary_role_allow_connections_desc、secondary_role_allow_connections、secondary_role_allow_connections_desc、create_date、modify_date、backup_priority、read_only_routing_url</span><span class="sxs-lookup"><span data-stu-id="33cfb-118">**Column names:** replica_id, group_id, replica_metadata_id, replica_server_name, owner_sid, endpoint_url, availability_mode, availability_mode_desc, failover_mode, failover_mode_desc, session_timeout, primary_role_allow_connections, primary_role_allow_connections_desc, secondary_role_allow_connections, secondary_role_allow_connections_desc, create_date, modify_date, backup_priority, read_only_routing_url</span></span>  
  
 [<span data-ttu-id="33cfb-119">sys.availability_read_only_routing_lists</span><span class="sxs-lookup"><span data-stu-id="33cfb-119">sys.availability_read_only_routing_lists</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
 <span data-ttu-id="33cfb-120">針對 WSFC 容錯移轉叢集中 AlwaysOn 可用性群組內每個可用性複本的唯讀路由清單，各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="33cfb-120">Returns a row for the read only routing list of each availability replica in an AlwaysOn availability group in the WSFC failover cluster.</span></span>  
  
 <span data-ttu-id="33cfb-121">**資料行名稱：** replica_id、routing_priority、read_only_replica_id</span><span class="sxs-lookup"><span data-stu-id="33cfb-121">**Column names:** replica_id, routing_priority, read_only_replica_id</span></span>  
  
 [<span data-ttu-id="33cfb-122">監視可用性複本</span><span class="sxs-lookup"><span data-stu-id="33cfb-122">sys.dm_hadr_availability_replica_cluster_nodes</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-nodes-transact-sql)  
 <span data-ttu-id="33cfb-123">針對 Windows Server 容錯移轉叢集 (WSFC) 叢集中 AlwaysOn 可用性群組的每一個可用性複本 (不論聯結狀態為何)，各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="33cfb-123">Returns a row for every availability replica (regardless of join state) of the AlwaysOn availability groups in the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="33cfb-124">**資料行名稱：** group_name、replica_server_name、node_name</span><span class="sxs-lookup"><span data-stu-id="33cfb-124">**Column names:** group_name, replica_server_name, node_name</span></span>  
  
 [<span data-ttu-id="33cfb-125">sys.dm_hadr_availability_replica_cluster_nodes</span><span class="sxs-lookup"><span data-stu-id="33cfb-125">sys.dm_hadr_availability_replica_cluster_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
 <span data-ttu-id="33cfb-126">針對 Windows Server 容錯移轉叢集 (WSFC) 叢集中所有 AlwaysOn 可用性群組 (不論複本位置為何) 的每一個複本 (不論聯結狀態為何) 各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="33cfb-126">Returns a row for each replica (regardless of join state) of all AlwaysOn availability groups (regardless of replica location) in the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="33cfb-127">**資料行名稱：** replica_id、replica_server_name、group_id、join_state、join_state_desc</span><span class="sxs-lookup"><span data-stu-id="33cfb-127">**Column names:** replica_id, replica_server_name, group_id, join_state, join_state_desc</span></span>  
  
 [<span data-ttu-id="33cfb-128">sys.dm_hadr_availability_replica_states</span><span class="sxs-lookup"><span data-stu-id="33cfb-128">sys.dm_hadr_availability_replica_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)  
 <span data-ttu-id="33cfb-129">傳回顯示每個本機可用性複本之狀態的資料列，並針對同一個可用性群組中每一個遠端可用性複本，各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="33cfb-129">Returns a row showing the state of each local availability replica and a row for each remote availability replica in the same availability group.</span></span>  
  
 <span data-ttu-id="33cfb-130">**資料行名稱：** replica_id、group_id、is_local、role、role_desc、operational_state、operational_state_desc、connected_state、connected_state_desc、recovery_health、recovery_health_desc、synchronization_health、synchronization_health_desc、last_connect_error_number、last_connect_error_description 和 last_connect_error_timestamp</span><span class="sxs-lookup"><span data-stu-id="33cfb-130">**Column names:** replica_id, group_id, is_local, role, role_desc, operational_state, operational_state_desc, connected_state, connected_state_desc, recovery_health, recovery_health_desc, synchronization_health, synchronization_health_desc, last_connect_error_number, last_connect_error_description, and last_connect_error_timestamp</span></span>  
  
 [<span data-ttu-id="33cfb-131">sys.fn_hadr_backup_is_preferred_replica</span><span class="sxs-lookup"><span data-stu-id="33cfb-131">sys.fn_hadr_backup_is_preferred_replica</span></span>](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
 <span data-ttu-id="33cfb-132">判斷目前的複本是否為慣用的備份複本。</span><span class="sxs-lookup"><span data-stu-id="33cfb-132">Determines whether the current replica is the preferred backup replica.</span></span> <span data-ttu-id="33cfb-133">如果目前伺服器執行個體上的資料庫為慣用複本，則傳回 1。</span><span class="sxs-lookup"><span data-stu-id="33cfb-133">Returns 1 if the database on the current server instance is the preferred replica.</span></span> <span data-ttu-id="33cfb-134">否則，它會傳回 0。</span><span class="sxs-lookup"><span data-stu-id="33cfb-134">Otherwise, it returns 0.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="33cfb-135">如需可用性複本效能計數器 ( **SQLServer:Availability Replica**  效能物件) 的相關資訊，請參閱 [SQL Server、可用性複本](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)。</span><span class="sxs-lookup"><span data-stu-id="33cfb-135">For information about performance counters for availability replicas (the **SQLServer:Availability Replica**  performance object), see [SQL Server, Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).</span></span>  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="33cfb-136">相關工作</span><span class="sxs-lookup"><span data-stu-id="33cfb-136">Related Tasks</span></span>  
 <span data-ttu-id="33cfb-137">**若要檢視可用性群組的相關資訊**</span><span class="sxs-lookup"><span data-stu-id="33cfb-137">**To view information about availability groups**</span></span>  
  
-   [<span data-ttu-id="33cfb-138">檢視可用性群組屬性 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="33cfb-138">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)  
  
-   [<span data-ttu-id="33cfb-139">檢視可用性群組接聽程式屬性 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="33cfb-139">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
-   [<span data-ttu-id="33cfb-140">AlwaysOn 可用性群組 &#40;SQL Server 的操作問題 AlwaysOn 原則&#41;</span><span class="sxs-lookup"><span data-stu-id="33cfb-140">AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](always-on-policies-for-operational-issues-always-on-availability.md)
  
-   [<span data-ttu-id="33cfb-141">使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="33cfb-141">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="33cfb-142">監視可用性群組 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="33cfb-142">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
  
 <span data-ttu-id="33cfb-143">**若要管理可用性複本**</span><span class="sxs-lookup"><span data-stu-id="33cfb-143">**To manage availability replicas**</span></span>  
  
-   [<span data-ttu-id="33cfb-144">將次要複本加入至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="33cfb-144">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="33cfb-145">將次要複本聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="33cfb-145">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="33cfb-146">設定可用性複本的唯讀存取 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="33cfb-146">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="33cfb-147">變更可用性複本的可用性模式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="33cfb-147">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="33cfb-148">變更可用性複本的容錯移轉模式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="33cfb-148">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="33cfb-149">變更可用性複本的工作階段逾時期限 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="33cfb-149">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="33cfb-150">將次要複本從可用性群組移除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="33cfb-150">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
 <span data-ttu-id="33cfb-151">**管理可用性資料庫**</span><span class="sxs-lookup"><span data-stu-id="33cfb-151">**To manage an availability database**</span></span>  
  
-   [<span data-ttu-id="33cfb-152">將資料庫加入至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="33cfb-152">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
-   [<span data-ttu-id="33cfb-153">將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="33cfb-153">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="33cfb-154">暫止可用性資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="33cfb-154">Suspend an Availability Database &#40;SQL Server&#41;</span></span>](suspend-an-availability-database-sql-server.md)  
  
-   [<span data-ttu-id="33cfb-155">繼續可用性資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="33cfb-155">Resume an Availability Database &#40;SQL Server&#41;</span></span>](resume-an-availability-database-sql-server.md)  
  
-   [<span data-ttu-id="33cfb-156">將次要資料庫從可用性群組移除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="33cfb-156">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="33cfb-157">將主要資料庫從可用性群組移除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="33cfb-157">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
  
## <a name="see-also"></a><span data-ttu-id="33cfb-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33cfb-158">See Also</span></span>  
 <span data-ttu-id="33cfb-159">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="33cfb-159">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="33cfb-160">[&#40;Transact-sql&#41;監視可用性群組](monitor-availability-groups-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="33cfb-160">[Monitor Availability Groups &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md) </span></span>  
 <span data-ttu-id="33cfb-161">[AlwaysOn 可用性群組 &#40;SQL Server 的操作問題 AlwaysOn 原則&#41;](always-on-policies-for-operational-issues-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="33cfb-161">[AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md) </span></span>  
 [<span data-ttu-id="33cfb-162">管理可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="33cfb-162">Administration of an Availability Group &#40;SQL Server&#41;</span></span>](administration-of-an-availability-group-sql-server.md)  
  
  
