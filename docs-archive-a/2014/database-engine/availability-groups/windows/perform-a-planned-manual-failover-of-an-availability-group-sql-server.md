---
title: 執行可用性群組的已規劃手動容錯移轉 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.manualfailover.f1
helpviewer_keywords:
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: 419f655d-3f9a-4e7d-90b9-f0bab47b3178
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c62942eaa8f4ab4472bca5c7123e5999eb069216
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703305"
---
# <a name="perform-a-planned-manual-failover-of-an-availability-group-sql-server"></a><span data-ttu-id="dfed6-102">執行可用性群組的已規劃手動容錯移轉 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="dfed6-102">Perform a Planned Manual Failover of an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="dfed6-103">本主題說明如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 中的 PowerShell，在不遺失資料的情況下對 AlwaysOn 可用性群組執行手動容錯移轉 (*規劃的手動容錯移轉*)。</span><span class="sxs-lookup"><span data-stu-id="dfed6-103">This topic describes how to perform a manual failover without data loss (a *planned manual failover*) on an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="dfed6-104">可用性群組會在可用性複本層級容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="dfed6-104">An availability group fails over at the level of an availability replica.</span></span> <span data-ttu-id="dfed6-105">已規劃的手動容錯移轉就像任何 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 容錯移轉一樣，會將次要複本轉換成主要角色，同時將先前的主要複本轉換成次要角色。</span><span class="sxs-lookup"><span data-stu-id="dfed6-105">A planned manual failover, like any [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] failover, transitions a secondary replica to primary role and, concurrently, transitions the former primary replica to the secondary role.</span></span>  
  
 <span data-ttu-id="dfed6-106">只有在主要複本和目標次要複本在同步認可模式下執行，而且目前經過同步處理之後才支援的已規劃手動容錯移轉，會保留聯結至目標次要複本上可用性群組之次要資料庫中的所有資料。</span><span class="sxs-lookup"><span data-stu-id="dfed6-106">A planned manual failover, which is supported only when the primary replica and the target secondary replica are running in synchronous-commit mode and are currently synchronized, preserves all the data in the secondary databases that are joined to the availability group on the target secondary replica.</span></span> <span data-ttu-id="dfed6-107">一旦之前的主要複本轉換成次要角色之後，其資料庫會變成次要資料庫，並開始與新的主要資料庫進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="dfed6-107">Once the former primary replica transitions to the secondary role, its databases become secondary databases and begin synchronizing with the new primary databases.</span></span> <span data-ttu-id="dfed6-108">在將它們全部轉換成 SYNCHRONIZED 狀態之後，新的次要複本就會變成有資格當做未來已規劃之手動容錯移轉的目標。</span><span class="sxs-lookup"><span data-stu-id="dfed6-108">After they all transition into the SYNCHRONIZED state, the new secondary replica becomes eligible to serve as the target of a future planned manual failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dfed6-109">如果次要和主要複本都設定成自動容錯移轉模式，一旦次要複本經過同步處理之後，也可以當做自動容錯移轉的目標。</span><span class="sxs-lookup"><span data-stu-id="dfed6-109">If the secondary and primary replicas are both configured for automatic failover mode, once the secondary replica is synchronized, it can also serve as the target for an automatic failover.</span></span> <span data-ttu-id="dfed6-110">如需詳細資訊，請參閱[可用性模式 &#40;AlwaysOn 可用性群組&#41;](availability-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="dfed6-110">For more information, see [Availability Modes &#40;AlwaysOn Availability Groups&#41;](availability-modes-always-on-availability-groups.md).</span></span>  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="dfed6-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="dfed6-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="dfed6-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="dfed6-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="dfed6-113">目標次要複本接受命令之後，容錯移轉命令就會傳回。</span><span class="sxs-lookup"><span data-stu-id="dfed6-113">A failover command returns as soon as the target secondary replica has accepted the command.</span></span> <span data-ttu-id="dfed6-114">不過，在可用性群組完成容錯移轉之後，會以非同步方式復原資料庫。</span><span class="sxs-lookup"><span data-stu-id="dfed6-114">However, database recovery occurs asynchronously after the availability group has finished failing over.</span></span>  
  
-   <span data-ttu-id="dfed6-115">容錯移轉時，不會保留可用性群組內跨資料庫的一致性。</span><span class="sxs-lookup"><span data-stu-id="dfed6-115">Cross-database consistency across databases within the availability group is not maintained on failover.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dfed6-116">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 不支援跨資料庫交易和分散式交易。</span><span class="sxs-lookup"><span data-stu-id="dfed6-116">Cross-database transactions and distributed transactions are not supported by [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="dfed6-117">如需詳細資訊，請參閱[資料庫鏡像或 AlwaysOn 可用性群組不支援跨資料庫交易 &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="dfed6-117">For more information, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="dfed6-118">必要條件和限制</span><span class="sxs-lookup"><span data-stu-id="dfed6-118">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="dfed6-119">目標次要複本和主要複本都必須在同步認可可用性模式下執行。</span><span class="sxs-lookup"><span data-stu-id="dfed6-119">The target secondary replica and the primary replica must both be running in synchronous-commit availability mode.</span></span>  
  
-   <span data-ttu-id="dfed6-120">目標次要複本目前必須與主要複本進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="dfed6-120">The target secondary replica must currently be synchronized with the primary replica.</span></span> <span data-ttu-id="dfed6-121">這需要此次要複本上的所有次要資料庫都必須已經聯結至可用性群組，並與其對應的主要資料庫進行同步處理 (亦即，本機次要資料庫必須是 SYNCHRONIZED)。</span><span class="sxs-lookup"><span data-stu-id="dfed6-121">This requires that all the secondary databases on this secondary replica must have been joined to the availability group and be synchronized with their corresponding primary databases (that is, the local secondary databases must be SYNCHRONIZED).</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="dfed6-122">若要判斷次要複本的容錯移轉整備，請查詢 [sys.dm_hadr_database_cluster_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql) 動態管理檢視中的 **is_failover_ready** 資料行，或是查看 [AlwaysOn 群組儀表板](use-the-always-on-dashboard-sql-server-management-studio.md)的 [容錯移轉整備]\*\*\*\* 資料行。</span><span class="sxs-lookup"><span data-stu-id="dfed6-122">To determine the failover readiness of an secondary replica, query the **is_failover_ready** column in the [sys.dm_hadr_database_cluster_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql) dynamic management view, or look at the **Failover Readiness** column of the [AlwaysOn Group Dashboard](use-the-always-on-dashboard-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="dfed6-123">只有在目標次要複本上才支援這個工作。</span><span class="sxs-lookup"><span data-stu-id="dfed6-123">This task is supported only on the target secondary replica.</span></span> <span data-ttu-id="dfed6-124">您必須連接到裝載目標次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="dfed6-124">You must be connected to the server instance that hosts the target secondary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="dfed6-125">Security</span><span class="sxs-lookup"><span data-stu-id="dfed6-125">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="dfed6-126">權限</span><span class="sxs-lookup"><span data-stu-id="dfed6-126">Permissions</span></span>  
 <span data-ttu-id="dfed6-127">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="dfed6-127">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="dfed6-128">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="dfed6-128">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="dfed6-129">**手動容錯移轉可用性群組**</span><span class="sxs-lookup"><span data-stu-id="dfed6-129">**To manually fail over an availability group**</span></span>  
  
1.  <span data-ttu-id="dfed6-130">在 [物件總管] 中，連接至裝載需要容錯移轉之可用性群組次要複本的伺服器執行個體，然後展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="dfed6-130">In Object Explorer, connect to a server instance that hosts a secondary replica of the availability group that needs to be failed over, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="dfed6-131">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="dfed6-131">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="dfed6-132">以滑鼠右鍵按一下要容錯移轉的可用性群組，然後選取 [容錯移轉]  命令。</span><span class="sxs-lookup"><span data-stu-id="dfed6-132">Right-click the availability group to be failed over, and select the **Failover** command.</span></span>  
  
4.  <span data-ttu-id="dfed6-133">這會啟動「容錯移轉可用性群組精靈」。</span><span class="sxs-lookup"><span data-stu-id="dfed6-133">This launches the Failover Availability Group Wizard.</span></span> <span data-ttu-id="dfed6-134">如需詳細資訊，請參閱[使用容錯移轉可用性群組精靈 &#40;SQL Server Management Studio&#41;](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="dfed6-134">For more information, see [Use the Fail Over Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="dfed6-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="dfed6-135">Using Transact-SQL</span></span>  
 <span data-ttu-id="dfed6-136">**手動容錯移轉可用性群組**</span><span class="sxs-lookup"><span data-stu-id="dfed6-136">**To manually fail over an availability group**</span></span>  
  
1.  <span data-ttu-id="dfed6-137">連接到裝載目標次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="dfed6-137">Connect to the server instance that hosts the target secondary replica.</span></span>  
  
2.  <span data-ttu-id="dfed6-138">使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 陳述式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dfed6-138">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="dfed6-139">ALTER AVAILABILITY GROUP *group_name* FAILOVER</span><span class="sxs-lookup"><span data-stu-id="dfed6-139">ALTER AVAILABILITY GROUP *group_name* FAILOVER</span></span>  
  
     <span data-ttu-id="dfed6-140">其中 <群組名稱> 是可用性群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="dfed6-140">where *group_name* is the name of the availability group.</span></span>  
  
     <span data-ttu-id="dfed6-141">下列範例會將*MyAg*可用性群組手動故障處理到已連接的次要複本。</span><span class="sxs-lookup"><span data-stu-id="dfed6-141">The following example manually fails over the *MyAg* availability group to the connected secondary replica.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAg FAILOVER;  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="dfed6-142">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dfed6-142">Using PowerShell</span></span>  
 <span data-ttu-id="dfed6-143">**手動容錯移轉可用性群組**</span><span class="sxs-lookup"><span data-stu-id="dfed6-143">**To manually fail over an availability group**</span></span>  
  
1.  <span data-ttu-id="dfed6-144">將目錄 (`cd`) 切換到裝載目標次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="dfed6-144">Change directory (`cd`) to the server instance that hosts the target secondary replica.</span></span>  
  
2.  <span data-ttu-id="dfed6-145">使用 `Switch-SqlAvailabilityGroup` 指令程式。</span><span class="sxs-lookup"><span data-stu-id="dfed6-145">Use the `Switch-SqlAvailabilityGroup` cmdlet.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dfed6-146">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="dfed6-146">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell environment.</span></span> <span data-ttu-id="dfed6-147">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="dfed6-147">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
     <span data-ttu-id="dfed6-148">下列範例會將*MyAg*可用性群組手動故障處理至具有指定路徑的次要複本。</span><span class="sxs-lookup"><span data-stu-id="dfed6-148">The following example manually fails over the *MyAg* availability group to the secondary replica with the specified path.</span></span>  
  
    ```powershell
    Switch-SqlAvailabilityGroup -Path SQLSERVER:\Sql\SecondaryServer\InstanceName\AvailabilityGroups\MyAg  
    ```  
  
 <span data-ttu-id="dfed6-149">**若要設定和使用 SQL Server PowerShell 提供者**</span><span class="sxs-lookup"><span data-stu-id="dfed6-149">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="dfed6-150">SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="dfed6-150">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
-   [<span data-ttu-id="dfed6-151">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="dfed6-151">Get Help SQL Server PowerShell</span></span>](../../../powershell/sql-server-powershell.md)  
  
##  <a name="follow-up-after-manually-failing-over-an-availability-group"></a><a name="FollowUp"></a><span data-ttu-id="dfed6-152">後續操作：手動容錯移轉可用性群組之後</span><span class="sxs-lookup"><span data-stu-id="dfed6-152">Follow Up: After Manually Failing Over an Availability Group</span></span>  
 <span data-ttu-id="dfed6-153">如果您容錯移轉可用性群組的 [!INCLUDE[ssFosAuto](../../../includes/ssfosauto-md.md)] 外部：調整 WSFC 節點的仲裁投票，以反映您的新可用性群組組態。</span><span class="sxs-lookup"><span data-stu-id="dfed6-153">If you failed over outside of the [!INCLUDE[ssFosAuto](../../../includes/ssfosauto-md.md)] of the availability group, adjust the quorum votes of the WSFC nodes to reflect your new availability group configuration.</span></span> <span data-ttu-id="dfed6-154">如需詳細資訊，請參閱[使用 SQL Server &#40;WSFC&#41; 的 Windows Server 容錯移轉](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)叢集。</span><span class="sxs-lookup"><span data-stu-id="dfed6-154">For more information, see [Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfed6-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfed6-155">See Also</span></span>  
 <span data-ttu-id="dfed6-156">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="dfed6-156">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="dfed6-157">[容錯移轉和容錯移轉模式 &#40;AlwaysOn 可用性群組&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="dfed6-157">[Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="dfed6-158">執行可用性群組的強制手動容錯移轉 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="dfed6-158">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
