---
title: 檢視可用性群組屬性 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server]
ms.assetid: 61243c87-bd62-4510-863f-2a8f347caf1f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b7d1f57a9bd29b6c65160ec9a163bc77dfca48b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594183"
---
# <a name="view-availability-group-properties-sql-server"></a><span data-ttu-id="739ed-102">檢視可用性群組屬性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="739ed-102">View Availability Group Properties (SQL Server)</span></span>
  <span data-ttu-id="739ed-103">此主題描述如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，檢視 AlwaysOn 可用性群組的可用性群組屬性。</span><span class="sxs-lookup"><span data-stu-id="739ed-103">This topic describes how to view the properties of an availability group for an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  

  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="739ed-104">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="739ed-104">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="739ed-105">**若要檢視及變更可用性群組的屬性**</span><span class="sxs-lookup"><span data-stu-id="739ed-105">**To view and change the properties an availability group**</span></span>  
  
1.  <span data-ttu-id="739ed-106">在 [物件總管] 中，連接到裝載主要複本的伺服器執行個體，然後展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="739ed-106">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="739ed-107">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="739ed-107">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="739ed-108">以滑鼠右鍵按一下要檢視其屬性的可用性群組，然後選取 [屬性]\*\*\*\* 命令。</span><span class="sxs-lookup"><span data-stu-id="739ed-108">Right-click the availability group whose properties you want to view, and select the **Properties** command.</span></span>  
  
4.  <span data-ttu-id="739ed-109">在 **[可用性群組屬性]** 對話方塊中，使用 **[一般]** 和 **[備份喜好設定]** 頁面檢視所選可用性群組的屬性，並在某些情況下變更這些屬性。</span><span class="sxs-lookup"><span data-stu-id="739ed-109">In the **Availability Group Properties** dialog box, use the **General** and **Backup Preferences** pages to view and, in some cases, change properties of the selected availability group.</span></span> <span data-ttu-id="739ed-110">如需詳細資訊，請參閱[可用性群組屬性和新增可用性群組 &#40;一般頁面&#41;](availability-group-properties-new-availability-group-general-page.md) 和[可用性群組屬性：新增可用性群組 &#40;備份喜好設定頁面&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md)。</span><span class="sxs-lookup"><span data-stu-id="739ed-110">For more information, see [Availability Group Properties and New Availability Group &#40;General Page&#41;](availability-group-properties-new-availability-group-general-page.md) and [Availability Group Properties: New Availability Group &#40;Backup Preferences Page&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md).</span></span>  
  
     <span data-ttu-id="739ed-111">使用 **[權限]** 頁面來檢視與可用性群組相關聯的目前登入、角色和明確權限。</span><span class="sxs-lookup"><span data-stu-id="739ed-111">Use the **Permissions** page to view the current logins, roles, and explicit permissions associated with the availability group.</span></span> <span data-ttu-id="739ed-112">如需相關資訊，請參閱 [Permissions or Securables Page](../../../relational-databases/security/permissions-or-securables-page.md)。</span><span class="sxs-lookup"><span data-stu-id="739ed-112">For more information, see [Permissions or Securables Page](../../../relational-databases/security/permissions-or-securables-page.md).</span></span>  
  

  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="739ed-113">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="739ed-113">Using Transact-SQL</span></span>  
 <span data-ttu-id="739ed-114">**若要檢視可用性群組的屬性和狀態**</span><span class="sxs-lookup"><span data-stu-id="739ed-114">**To view the properties and state of an availability group**</span></span>  
  
 <span data-ttu-id="739ed-115">若要針對伺服器執行個體裝載其可用性複本的可用性群組，查詢其屬性和狀態，請使用下列檢視：</span><span class="sxs-lookup"><span data-stu-id="739ed-115">To query the properties and states of the availability groups for which the server instance hosts an availability replica, use the following views:</span></span>  
  
 [<span data-ttu-id="739ed-116">sys.availability_groups</span><span class="sxs-lookup"><span data-stu-id="739ed-116">sys.availability_groups</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)  
 <span data-ttu-id="739ed-117">針對裝載可用性複本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 本機執行個體的每一個可用性群組，各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="739ed-117">Returns a row for each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hosts an availability replica.</span></span> <span data-ttu-id="739ed-118">每一個資料列都包含可用性群組中繼資料的快取副本。</span><span class="sxs-lookup"><span data-stu-id="739ed-118">Each row contains a cached copy of the availability group metadata.</span></span>  
  
 <span data-ttu-id="739ed-119">**資料行名稱：** group_id、name、resource_id、resource_group_id、failure_condition_level、health_check_timeout、automated_backup_preference、automated_backup_preference_desc</span><span class="sxs-lookup"><span data-stu-id="739ed-119">**Column names:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span></span>  
  
 [<span data-ttu-id="739ed-120">sys.availability_groups_cluster</span><span class="sxs-lookup"><span data-stu-id="739ed-120">sys.availability_groups_cluster</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-cluster-transact-sql)  
 <span data-ttu-id="739ed-121">針對 WSFC 叢集中的每一個可用性群組，各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="739ed-121">Returns a row for each availability group in the WSFC cluster.</span></span> <span data-ttu-id="739ed-122">每個資料列都包含 Windows Server 容錯移轉叢集 (WSFC) 叢集中的可用性群組中繼資料。</span><span class="sxs-lookup"><span data-stu-id="739ed-122">Each row contains the availability group metadata from the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="739ed-123">**資料行名稱：** group_id、name、resource_id、resource_group_id、failure_condition_level、health_check_timeout、automated_backup_preference、automated_backup_preference_desc</span><span class="sxs-lookup"><span data-stu-id="739ed-123">**Column names:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span></span>  
  
 [<span data-ttu-id="739ed-124">sys.dm_hadr_availability_group_states</span><span class="sxs-lookup"><span data-stu-id="739ed-124">sys.dm_hadr_availability_group_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql)  
 <span data-ttu-id="739ed-125">針對擁有 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]本機執行個體之可用性複本的每一個可用性群組，各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="739ed-125">Returns a row for each availability group that possesses an availability replica on the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="739ed-126">每個資料列會顯示定義給定之可用性群組健全狀況的狀態。</span><span class="sxs-lookup"><span data-stu-id="739ed-126">Each row displays the states that define the health of a given availability group.</span></span>  
  
 <span data-ttu-id="739ed-127">**資料行名稱：** group_id、primary_replica、primary_recovery_health、primary_recovery_health_desc、secondary_recovery_health、secondary_recovery_health_desc、synchronization_health、synchronization_health_desc</span><span class="sxs-lookup"><span data-stu-id="739ed-127">**Column names:** group_id, primary_replica, primary_recovery_health, primary_recovery_health_desc, secondary_recovery_health, secondary_recovery_health_desc, synchronization_health, synchronization_health_desc</span></span>  
  

  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="739ed-128">相關工作</span><span class="sxs-lookup"><span data-stu-id="739ed-128">Related Tasks</span></span>  
 <span data-ttu-id="739ed-129">**若要檢視可用性群組的相關資訊**</span><span class="sxs-lookup"><span data-stu-id="739ed-129">**To view information about availability groups**</span></span>  
  
-   [<span data-ttu-id="739ed-130">檢視可用性複本屬性 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="739ed-130">View Availability Replica Properties &#40;SQL Server&#41;</span></span>](view-availability-replica-properties-sql-server.md)  
  
-   [<span data-ttu-id="739ed-131">檢視可用性群組接聽程式屬性 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="739ed-131">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
-   [<span data-ttu-id="739ed-132">AlwaysOn 可用性群組 &#40;SQL Server 的操作問題 AlwaysOn 原則&#41;</span><span class="sxs-lookup"><span data-stu-id="739ed-132">AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](always-on-policies-for-operational-issues-always-on-availability.md)
  
-   [<span data-ttu-id="739ed-133">使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="739ed-133">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="739ed-134">監視可用性群組 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="739ed-134">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
  
 <span data-ttu-id="739ed-135">**設定現有的可用性群組**</span><span class="sxs-lookup"><span data-stu-id="739ed-135">**To configure an existing availability group**</span></span>  
  
-   [<span data-ttu-id="739ed-136">將次要複本加入至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="739ed-136">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="739ed-137">將次要複本從可用性群組移除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="739ed-137">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="739ed-138">將資料庫加入至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="739ed-138">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
-   [<span data-ttu-id="739ed-139">將次要資料庫從可用性群組移除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="739ed-139">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="739ed-140">建立或設定可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="739ed-140">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="739ed-141">移除可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="739ed-141">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](remove-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="739ed-142">將主要資料庫從可用性群組移除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="739ed-142">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="739ed-143">移除可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="739ed-143">Remove an Availability Group &#40;SQL Server&#41;</span></span>](remove-an-availability-group-sql-server.md)  
  
 <span data-ttu-id="739ed-144">**手動容錯移轉可用性群組**</span><span class="sxs-lookup"><span data-stu-id="739ed-144">**To manually fail over an availability group**</span></span>  
  
-   [<span data-ttu-id="739ed-145">執行可用性群組的已規劃手動容錯移轉 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="739ed-145">Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="739ed-146">執行可用性群組的強制手動容錯移轉 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="739ed-146">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="739ed-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="739ed-147">See Also</span></span>  
 <span data-ttu-id="739ed-148">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) [監視可用性群組 &#40;Transact-sql&#41;](monitor-availability-groups-transact-sql.md) [AlwaysOn 原則，以解決 AlwaysOn 可用性群組 &#40;SQL Server 的操作問題&#41;](always-on-policies-for-operational-issues-always-on-availability.md)</span><span class="sxs-lookup"><span data-stu-id="739ed-148">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) [Monitor Availability Groups &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md) [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md)</span></span> 
  
  
