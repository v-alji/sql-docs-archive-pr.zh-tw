---
title: 設定可用性複本上的唯讀存取 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- connection access to availability replicas
- Availability Groups [SQL Server], readable secondary replicas
- active secondary replicas [SQL Server], read-only access to
- Availability Groups [SQL Server], read-only routing
- Availability Groups [SQL Server], client connectivity
ms.assetid: 22387419-22c4-43fa-851c-5fecec4b049b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ab13081396aff46d193c1b0449d6b93042ee60d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688234"
---
# <a name="configure-read-only-access-on-an-availability-replica-sql-server"></a><span data-ttu-id="af93c-102">設定可用性複本上的唯讀存取 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="af93c-102">Configure Read-Only Access on an Availability Replica (SQL Server)</span></span>
  <span data-ttu-id="af93c-103">預設允許與主要複本之間的讀寫和讀取意圖的存取，但是不允許連接 AlwaysOn 可用性群組的次要複本。</span><span class="sxs-lookup"><span data-stu-id="af93c-103">By default both read-write and read-intent access are allowed to the primary replica and no connections are allowed to secondary replicas of an AlwaysOn availability group.</span></span> <span data-ttu-id="af93c-104">本主題說明如何藉由使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或 PowerShell，針對 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中 AlwaysOn 可用性群組的可用性複本設定連接存取。</span><span class="sxs-lookup"><span data-stu-id="af93c-104">This topic describes how to configure connection access on an availability replica of an AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell.</span></span>  
  
 <span data-ttu-id="af93c-105">如需針對次要複本啟用唯讀存取的含意資訊，以及連接存取簡介，請參閱[關於可用性複本的用戶端連接存取 &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) 和[使用中次要：可讀取的次要複本 &#40;AlwaysOn 可用性群組&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="af93c-105">For information about the implications of enabling read-only access for a secondary replica and for an introduction to connection access, see [About Client Connection Access to Availability Replicas &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) and [Active Secondaries: Readable Secondary Replicas &#40;AlwaysOn Availability Groups&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="af93c-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="af93c-106">Before You Begin</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="af93c-107">必要條件和限制</span><span class="sxs-lookup"><span data-stu-id="af93c-107">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="af93c-108">若要設定不同的連接存取，您必須連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="af93c-108">To configure different connection access, you must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="af93c-109">Security</span><span class="sxs-lookup"><span data-stu-id="af93c-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="af93c-110">權限</span><span class="sxs-lookup"><span data-stu-id="af93c-110">Permissions</span></span>  
  
|<span data-ttu-id="af93c-111">Task</span><span class="sxs-lookup"><span data-stu-id="af93c-111">Task</span></span>|<span data-ttu-id="af93c-112">權限</span><span class="sxs-lookup"><span data-stu-id="af93c-112">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="af93c-113">若要在建立可用性群組時設定複本</span><span class="sxs-lookup"><span data-stu-id="af93c-113">To configure replicas when creating an availability group</span></span>|<span data-ttu-id="af93c-114">需要 **系統管理員 (sysadmin)** 固定伺服器角色的成員資格，以及 CREATE AVAILABILITY GROUP 伺服器權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="af93c-114">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
|<span data-ttu-id="af93c-115">若要修改可用性複本</span><span class="sxs-lookup"><span data-stu-id="af93c-115">To modify an availability replica</span></span>|<span data-ttu-id="af93c-116">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="af93c-116">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="af93c-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="af93c-117">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="af93c-118">**若要設定可用性複本的存取**</span><span class="sxs-lookup"><span data-stu-id="af93c-118">**To configure access on an availability replica**</span></span>  
  
1.  <span data-ttu-id="af93c-119">在 [物件總管] 中，連接到裝載主要複本的伺服器執行個體，然後展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="af93c-119">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="af93c-120">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="af93c-120">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="af93c-121">按一下要變更複本的可用性群組。</span><span class="sxs-lookup"><span data-stu-id="af93c-121">Click the availability group whose replica you want to change.</span></span>  
  
4.  <span data-ttu-id="af93c-122">以滑鼠右鍵按一下可用性複本，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="af93c-122">Right-click the availability replica, and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="af93c-123">在 **[可用性複本屬性]** 對話方塊中，可以變更主要角色和次要角色的連接存取，如下所示：</span><span class="sxs-lookup"><span data-stu-id="af93c-123">In the **Availability Replica Properties** dialog box, you can change the connection access for the primary role and for the secondary role, as follows:</span></span>  
  
    -   <span data-ttu-id="af93c-124">如果是次要角色，請從 **[可讀取次要]** 下拉清單中選擇一個新值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="af93c-124">For the secondary role, select a new value from the **Readable secondary** drop list, as follows:</span></span>  
  
         <span data-ttu-id="af93c-125">**否**</span><span class="sxs-lookup"><span data-stu-id="af93c-125">**No**</span></span>  
         <span data-ttu-id="af93c-126">不允許使用者連接至這個複本的次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="af93c-126">No user connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="af93c-127">無法讀取這些資料庫。</span><span class="sxs-lookup"><span data-stu-id="af93c-127">They are not available for read access.</span></span> <span data-ttu-id="af93c-128">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="af93c-128">This is the default setting.</span></span>  
  
         <span data-ttu-id="af93c-129">**僅限讀取意圖**</span><span class="sxs-lookup"><span data-stu-id="af93c-129">**Read-intent only**</span></span>  
         <span data-ttu-id="af93c-130">只允許與這個複本的次要資料庫進行唯讀連接。</span><span class="sxs-lookup"><span data-stu-id="af93c-130">Only read-only connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="af93c-131">可以讀取所有次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="af93c-131">The secondary database(s) are all available for read access.</span></span>  
  
         <span data-ttu-id="af93c-132">**是**</span><span class="sxs-lookup"><span data-stu-id="af93c-132">**Yes**</span></span>  
         <span data-ttu-id="af93c-133">允許與這個複本的次要資料庫之間的所有連接，但只供讀取存取。</span><span class="sxs-lookup"><span data-stu-id="af93c-133">All connections are allowed to secondary databases of this replica, but only for read access.</span></span> <span data-ttu-id="af93c-134">可以讀取所有次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="af93c-134">The secondary database(s) are all available for read access.</span></span>  
  
    -   <span data-ttu-id="af93c-135">如果是主要角色，請從 **[主要角色的連接模式]** 下拉清單中選擇一個新值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="af93c-135">For the primary role, select a new value from the **Connections in primary role** drop list, as follows:</span></span>  
  
         <span data-ttu-id="af93c-136">**允許所有連接**</span><span class="sxs-lookup"><span data-stu-id="af93c-136">**Allow all connections**</span></span>  
         <span data-ttu-id="af93c-137">主要複本的資料庫允許所有連接。</span><span class="sxs-lookup"><span data-stu-id="af93c-137">All connections are allowed to the databases in the primary replica.</span></span> <span data-ttu-id="af93c-138">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="af93c-138">This is the default setting.</span></span>  
  
         <span data-ttu-id="af93c-139">**允取讀取/寫入連接**</span><span class="sxs-lookup"><span data-stu-id="af93c-139">**Allow read/write connections**</span></span>  
         <span data-ttu-id="af93c-140">當 Application Intent 屬性設為 **ReadWrite** 或是未設定 Application Intent 連接屬性時，便會允許連接。</span><span class="sxs-lookup"><span data-stu-id="af93c-140">When the Application Intent property is set to **ReadWrite** or the Application Intent connection property is not set, the connection is allowed.</span></span> <span data-ttu-id="af93c-141">不允許 Application Intent 連接屬性設為 **ReadOnly** 的連接。</span><span class="sxs-lookup"><span data-stu-id="af93c-141">Connections where the Application Intent connection property is set to **ReadOnly** are not allowed.</span></span> <span data-ttu-id="af93c-142">這有助於防止客戶錯誤地將讀取意圖的工作負載連接至主要複本。</span><span class="sxs-lookup"><span data-stu-id="af93c-142">This can help prevent customers from connecting a read-intent work load to the primary replica by mistake.</span></span> <span data-ttu-id="af93c-143">如需有關 Application Intent 連接屬性的詳細資訊，請參閱＜ [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)＞。</span><span class="sxs-lookup"><span data-stu-id="af93c-143">For more information about Application Intent connection property, see [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="af93c-144">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="af93c-144">Using Transact-SQL</span></span>  
 <span data-ttu-id="af93c-145">**若要設定可用性複本的存取**</span><span class="sxs-lookup"><span data-stu-id="af93c-145">**To configure access on an availability replica**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af93c-146">如需這個程序的範例，請參閱本節稍後的 [範例 &#40;Transact-SQL&#41;](#TsqlExample)。</span><span class="sxs-lookup"><span data-stu-id="af93c-146">For an example of this procedure, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="af93c-147">連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="af93c-147">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="af93c-148">如果您要針對新的可用性群組指定複本，請使用 [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="af93c-148">If you are specifying a replica for a new availability group, use the [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="af93c-149">如果您要加入或修改現有可用性群組的複本，請使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="af93c-149">If you are adding or modifying a replica of an existing availability group, use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span>  
  
    -   <span data-ttu-id="af93c-150">若要設定次要角色的連接存取，請在 ADD REPLICA 或 MODIFY REPLICA WITH 子句中指定 SECONDARY_ROLE 選項，如下所示：</span><span class="sxs-lookup"><span data-stu-id="af93c-150">To configure connection access for the secondary role, in the ADD REPLICA or MODIFY REPLICA WITH clause, specify the SECONDARY_ROLE option, as follows:</span></span>  
  
         <span data-ttu-id="af93c-151">SECONDARY_ROLE **(** ALLOW_CONNECTIONS **=** { NO | READ_ONLY | ALL } **)**</span><span class="sxs-lookup"><span data-stu-id="af93c-151">SECONDARY_ROLE **(** ALLOW_CONNECTIONS **=** { NO | READ_ONLY | ALL } **)**</span></span>  
  
         <span data-ttu-id="af93c-152">其中</span><span class="sxs-lookup"><span data-stu-id="af93c-152">where,</span></span>  
  
         <span data-ttu-id="af93c-153">否</span><span class="sxs-lookup"><span data-stu-id="af93c-153">NO</span></span>  
         <span data-ttu-id="af93c-154">不允許直接連接這個複本的次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="af93c-154">No direct connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="af93c-155">無法讀取這些資料庫。</span><span class="sxs-lookup"><span data-stu-id="af93c-155">They are not available for read access.</span></span> <span data-ttu-id="af93c-156">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="af93c-156">This is the default setting.</span></span>  
  
         <span data-ttu-id="af93c-157">READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="af93c-157">READ_ONLY</span></span>  
         <span data-ttu-id="af93c-158">只允許與這個複本的次要資料庫進行唯讀連接。</span><span class="sxs-lookup"><span data-stu-id="af93c-158">Only read-only connections are allowed to secondary databases of this replica.</span></span> <span data-ttu-id="af93c-159">可以讀取所有次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="af93c-159">The secondary database(s) are all available for read access.</span></span>  
  
         <span data-ttu-id="af93c-160">ALL</span><span class="sxs-lookup"><span data-stu-id="af93c-160">ALL</span></span>  
         <span data-ttu-id="af93c-161">允許與這個複本的次要資料庫之間的所有連接，但只供讀取存取。</span><span class="sxs-lookup"><span data-stu-id="af93c-161">All connections are allowed to secondary databases of this replica, but only for read access.</span></span> <span data-ttu-id="af93c-162">可以讀取所有次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="af93c-162">The secondary database(s) are all available for read access.</span></span>  
  
3.  <span data-ttu-id="af93c-163">若要設定主要角色的連接存取，請在 ADD REPLICA 或 MODIFY REPLICA WITH 子句中指定 PRIMARY_ROLE 選項，如下所示：</span><span class="sxs-lookup"><span data-stu-id="af93c-163">To configure connection access for the primary role, in the ADD REPLICA or MODIFY REPLICA WITH clause, specify the PRIMARY_ROLE option, as follows:</span></span>  
  
     <span data-ttu-id="af93c-164">PRIMARY_ROLE **(** ALLOW_CONNECTIONS **=** { READ_WRITE | ALL } **)**</span><span class="sxs-lookup"><span data-stu-id="af93c-164">PRIMARY_ROLE **(** ALLOW_CONNECTIONS **=** { READ_WRITE | ALL } **)**</span></span>  
  
     <span data-ttu-id="af93c-165">其中</span><span class="sxs-lookup"><span data-stu-id="af93c-165">where,</span></span>  
  
     <span data-ttu-id="af93c-166">READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="af93c-166">READ_WRITE</span></span>  
     <span data-ttu-id="af93c-167">不允許 Application Intent 連接屬性設為 **ReadOnly** 的連接。</span><span class="sxs-lookup"><span data-stu-id="af93c-167">Connections where the Application Intent connection property is set to **ReadOnly** are disallowed.</span></span>  <span data-ttu-id="af93c-168">當 Application Intent 屬性設為 **ReadWrite** 或是未設定 Application Intent 連接屬性時，便會允許連接。</span><span class="sxs-lookup"><span data-stu-id="af93c-168">When the Application Intent property is set to **ReadWrite** or the Application Intent connection property is not set, the connection is allowed.</span></span> <span data-ttu-id="af93c-169">如需有關 Application Intent 連接屬性的詳細資訊，請參閱＜ [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)＞。</span><span class="sxs-lookup"><span data-stu-id="af93c-169">For more information about Application Intent connection property, see [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
     <span data-ttu-id="af93c-170">ALL</span><span class="sxs-lookup"><span data-stu-id="af93c-170">ALL</span></span>  
     <span data-ttu-id="af93c-171">主要複本的資料庫允許所有連接。</span><span class="sxs-lookup"><span data-stu-id="af93c-171">All connections are allowed to the databases in the primary replica.</span></span> <span data-ttu-id="af93c-172">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="af93c-172">This is the default setting.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="af93c-173">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="af93c-173">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="af93c-174">下列範例會將次要複本加入名為 *AG2*的可用性群組。</span><span class="sxs-lookup"><span data-stu-id="af93c-174">The following example adds a secondary replica to an availability group named *AG2*.</span></span> <span data-ttu-id="af93c-175">接著指定一個獨立伺服器執行個體 *COMPUTER03\HADR_INSTANCE*，以裝載新的可用性複本。</span><span class="sxs-lookup"><span data-stu-id="af93c-175">A stand-alone server instance, *COMPUTER03\HADR_INSTANCE*, is specified to host the new availability replica.</span></span> <span data-ttu-id="af93c-176">將此複本設定為只允許主要角色的讀寫連接以及只允許次要角色的讀取意圖連接。</span><span class="sxs-lookup"><span data-stu-id="af93c-176">This replica configured to allow only read-write connections for the primary role and to allow only read-intent connections for secondary role.</span></span>  
  
```sql
ALTER AVAILABILITY GROUP AG2   
   ADD REPLICA ON   
      'COMPUTER03\HADR_INSTANCE' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER03:7022',  
         PRIMARY_ROLE ( ALLOW_CONNECTIONS = READ_WRITE ),  
         SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY )  
         );   
GO  
```  
  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="af93c-177">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="af93c-177">Using PowerShell</span></span>  

### <a name="to-configure-access-on-an-availability-replica"></a><span data-ttu-id="af93c-178">若要設定可用性複本的存取</span><span class="sxs-lookup"><span data-stu-id="af93c-178">To configure access on an availability replica</span></span>
  
> [!NOTE]  
>  <span data-ttu-id="af93c-179">如需程式碼範例，請參閱本節稍後的 PowerShell 範例。</span><span class="sxs-lookup"><span data-stu-id="af93c-179">For a code example, see the PowerShell examples later in this section.</span></span>  
  
1.  <span data-ttu-id="af93c-180">變更目錄 (`cd`) 為裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="af93c-180">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="af93c-181">將可用性複本加入至可用性群組時，請使用 `New-SqlAvailabilityReplica` 指令程式。</span><span class="sxs-lookup"><span data-stu-id="af93c-181">When adding an availability replica to an availability group, use the `New-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="af93c-182">修改現有的可用性複本時，請使用 `Set-SqlAvailabilityReplica` 指令程式。</span><span class="sxs-lookup"><span data-stu-id="af93c-182">When modifying an existing availability replica, use the `Set-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="af93c-183">相關參數如下所示：</span><span class="sxs-lookup"><span data-stu-id="af93c-183">The relevant parameters are as follows:</span></span>  
  
    -   <span data-ttu-id="af93c-184">若要設定次要角色的連接存取，請指定 `ConnectionModeInSecondaryRole` *secondary_role_keyword*參數，其中*secondary_role_keyword*等於下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="af93c-184">To configure connection access for the secondary role, specify the `ConnectionModeInSecondaryRole`*secondary_role_keyword* parameter, where *secondary_role_keyword* equals one of the following values:</span></span>  
  
         `AllowNoConnections`  
         <span data-ttu-id="af93c-185">不允許直接連接次要複本的資料庫，這些資料庫也不可用於讀取存取。</span><span class="sxs-lookup"><span data-stu-id="af93c-185">No direct connections are allowed to the databases in the secondary replica and the databases are not available for read access.</span></span> <span data-ttu-id="af93c-186">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="af93c-186">This is the default setting.</span></span>  
  
         `AllowReadIntentConnectionsOnly`  
         <span data-ttu-id="af93c-187">次要複本的資料庫只允許 Application Intent 屬性設為 **ReadOnly**的連接。</span><span class="sxs-lookup"><span data-stu-id="af93c-187">Connections are allowed only to the databases in the secondary replica where the Application Intent property is set to **ReadOnly**.</span></span> <span data-ttu-id="af93c-188">如需有關這個屬性的詳細資訊，請參閱＜ [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)＞。</span><span class="sxs-lookup"><span data-stu-id="af93c-188">For more information about this property, see [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
         `AllowAllConnections`  
         <span data-ttu-id="af93c-189">次要複本的資料庫允許所有連接進行唯讀存取。</span><span class="sxs-lookup"><span data-stu-id="af93c-189">All connections are allowed to the databases in the secondary replica for read-only access.</span></span>  
  
    -   <span data-ttu-id="af93c-190">若要設定主要角色的連接存取，請指定 `ConnectionModeInPrimaryRole` *primary_role_keyword*，其中*primary_role_keyword*等於下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="af93c-190">To configure connection access for the primary role, specify `ConnectionModeInPrimaryRole`*primary_role_keyword*, where *primary_role_keyword* equals one of the following values:</span></span>  
  
         `AllowReadWriteConnections`  
         <span data-ttu-id="af93c-191">不允許 Application Intent 連接屬性設為 ReadOnly 的連接。</span><span class="sxs-lookup"><span data-stu-id="af93c-191">Connections where the Application Intent connection property is set to ReadOnly are disallowed.</span></span> <span data-ttu-id="af93c-192">當 Application Intent 屬性設為 ReadWrite 或是未設定 Application Intent 連接屬性時，便會允許連接。</span><span class="sxs-lookup"><span data-stu-id="af93c-192">When the Application Intent property is set to ReadWrite or the Application Intent connection property is not set, the connection is allowed.</span></span> <span data-ttu-id="af93c-193">如需有關 Application Intent 連接屬性的詳細資訊，請參閱＜ [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)＞。</span><span class="sxs-lookup"><span data-stu-id="af93c-193">For more information about Application Intent connection property, see [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
         `AllowAllConnections`  
         <span data-ttu-id="af93c-194">主要複本的資料庫允許所有連接。</span><span class="sxs-lookup"><span data-stu-id="af93c-194">All connections are allowed to the databases in the primary replica.</span></span> <span data-ttu-id="af93c-195">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="af93c-195">This is the default setting.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="af93c-196">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="af93c-196">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell environment.</span></span> <span data-ttu-id="af93c-197">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="af93c-197">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="af93c-198">若要設定及使用 SQL Server PowerShell 提供者，請參閱[SQL Server PowerShell 提供者](../../../powershell/sql-server-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="af93c-198">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>
  
<span data-ttu-id="af93c-199">下列範例將 `ConnectionModeInSecondaryRole` 和 `ConnectionModeInPrimaryRole` 參數設定為 `AllowAllConnections`。</span><span class="sxs-lookup"><span data-stu-id="af93c-199">The following example, sets the both the `ConnectionModeInSecondaryRole` and `ConnectionModeInPrimaryRole` parameters to `AllowAllConnections`.</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\PrimaryServer\default\AvailabilityGroups\MyAg  
$primaryReplica = Get-Item "AvailabilityReplicas\PrimaryServer"  

Set-SqlAvailabilityReplica -ConnectionModeInSecondaryRole "AllowAllConnections" `
 -InputObject $primaryReplica  
Set-SqlAvailabilityReplica -ConnectionModeInPrimaryRole "AllowAllConnections" `
-InputObject $primaryReplica
```  

##  <a name="follow-up-after-configuring-read-only-access-for-an-availability-replica"></a><a name="FollowUp"></a> <span data-ttu-id="af93c-200">後續操作：針對可用性複本設定唯讀存取之後</span><span class="sxs-lookup"><span data-stu-id="af93c-200">Follow Up: After Configuring Read-Only Access for an Availability Replica</span></span>  
 <span data-ttu-id="af93c-201">**可讀取的次要複本的唯讀存取**</span><span class="sxs-lookup"><span data-stu-id="af93c-201">**Read-only access to a readable secondary replica**</span></span>  
  
-   <span data-ttu-id="af93c-202">使用[Bcp 公用程式](../../../tools/bcp-utility.md)或[sqlcmd 公用程式](../../../tools/sqlcmd-utility.md)時，您可以藉由指定參數，為啟用唯讀存取的任何次要複本指定唯讀存取 `-K ReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="af93c-202">When using the [bcp Utility](../../../tools/bcp-utility.md) or [sqlcmd Utility](../../../tools/sqlcmd-utility.md), you can specify read-only access to any secondary replica that is enabled for read-only access by specifying the `-K ReadOnly` switch.</span></span>  
  
-   <span data-ttu-id="af93c-203">若要啟用用戶端應用程式以連接到可讀取的次要副本：</span><span class="sxs-lookup"><span data-stu-id="af93c-203">To enable client applications to connect to readable secondary replicas:</span></span>  
  
    ||<span data-ttu-id="af93c-204">必要條件</span><span class="sxs-lookup"><span data-stu-id="af93c-204">Prerequisite</span></span>|<span data-ttu-id="af93c-205">連結</span><span class="sxs-lookup"><span data-stu-id="af93c-205">Link</span></span>|  
    |-|------------------|----------|  
    |<span data-ttu-id="af93c-206">![核取方塊](../../media/checkboxemptycenterxtraspacetopandright.gif "核取方塊")</span><span class="sxs-lookup"><span data-stu-id="af93c-206">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span></span>|<span data-ttu-id="af93c-207">確定可用性群組擁有接聽程式。</span><span class="sxs-lookup"><span data-stu-id="af93c-207">Ensure that the availability group has a listener.</span></span>|[<span data-ttu-id="af93c-208">建立或設定可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="af93c-208">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)|  
    |<span data-ttu-id="af93c-209">![核取方塊](../../media/checkboxemptycenterxtraspacetopandright.gif "核取方塊")</span><span class="sxs-lookup"><span data-stu-id="af93c-209">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span></span>|<span data-ttu-id="af93c-210">設定可用性群組的唯讀路由。</span><span class="sxs-lookup"><span data-stu-id="af93c-210">Configure read-only routing for the availability group.</span></span>|[<span data-ttu-id="af93c-211">設定可用性群組的唯讀路由 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="af93c-211">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)|  
  
 <span data-ttu-id="af93c-212">**容錯移轉之後可能會影響觸發程序和作業的因素**</span><span class="sxs-lookup"><span data-stu-id="af93c-212">**Factors that might affect triggers and jobs after a failover**</span></span>  
  
 <span data-ttu-id="af93c-213">如果您的觸發程序和作業在非可讀取的次要資料庫或可讀取的次要資料庫上執行時會失敗，則需要撰寫觸發程序和作業的指令碼來檢查特定複本，判斷資料庫是主要資料庫或是可讀取的次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="af93c-213">If you have triggers and jobs that will fail when running on a non-readable secondary database or on a readable secondary database, you need to script the triggers and jobs to check on a given replica to determine whether the database is a primary database or is a readable secondary database.</span></span> <span data-ttu-id="af93c-214">若要取得這項資訊，請使用 [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) 函數傳回資料庫的 **Updatability** 屬性。</span><span class="sxs-lookup"><span data-stu-id="af93c-214">To obtain this information, use the [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) function to return the **Updatability** property of the database.</span></span> <span data-ttu-id="af93c-215">若要識別唯讀資料庫，請指定 READ_ONLY 做為值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="af93c-215">To identify a read-only database, specify READ_ONLY as the value, as follows:</span></span>  
  
```  
DATABASEPROPERTYEX([db name],'Updatability') = N'READ_ONLY'  
```  
  
 <span data-ttu-id="af93c-216">若要識別讀寫資料庫，請指定 READ_WRITE 做為值。</span><span class="sxs-lookup"><span data-stu-id="af93c-216">To identify a read-write database, specify READ_WRITE as the value.</span></span>  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="af93c-217">相關工作</span><span class="sxs-lookup"><span data-stu-id="af93c-217">Related Tasks</span></span>  
  
-   [<span data-ttu-id="af93c-218">設定可用性群組的唯讀路由 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="af93c-218">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="af93c-219">建立或設定可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="af93c-219">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="af93c-220">相關內容</span><span class="sxs-lookup"><span data-stu-id="af93c-220">Related Content</span></span>  
  
-   <span data-ttu-id="af93c-221">[Always On:Value Proposition of Readable Secondary](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-value-proposition-of-readable-secondary) (Always On：可讀取次要的價值主張)</span><span class="sxs-lookup"><span data-stu-id="af93c-221">[Always On: Value Proposition of Readable Secondary](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-value-proposition-of-readable-secondary)</span></span>  
  
-   <span data-ttu-id="af93c-222">[Always On:Why there are two options to enable a secondary replica for read workload?](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-why-there-are-two-options-to-enable-a-secondary-replica-for-read-workload) (Always On：為何有兩個選項可針對讀取工作負載啟用次要複本？)</span><span class="sxs-lookup"><span data-stu-id="af93c-222">[Always On: Why there are two options to enable a secondary replica for read workload?](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-why-there-are-two-options-to-enable-a-secondary-replica-for-read-workload)</span></span>  
  
-   <span data-ttu-id="af93c-223">[Always On:Setting up Readable Secondary Replica](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-setting-up-readable-seconary-replica) (Always On：設定可讀取的次要複本)</span><span class="sxs-lookup"><span data-stu-id="af93c-223">[Always On: Setting up Readable Secondary Replica](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-setting-up-readable-seconary-replica)</span></span>  
  
-   <span data-ttu-id="af93c-224">[Always On:I just enabled Readable Secondary but my query is blocked?](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-i-just-enabled-readable-secondary-but-my-query-is-blocked) (Always On：我剛剛啟用可讀取次要，但我的查詢被封鎖？)</span><span class="sxs-lookup"><span data-stu-id="af93c-224">[Always On: I just enabled Readable Secondary but my query is blocked?](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-i-just-enabled-readable-secondary-but-my-query-is-blocked)</span></span>  
  
-   <span data-ttu-id="af93c-225">[Always On:Making latest statistics available on Readable Secondary, Read-Only database and Database Snapshot](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-making-latest-statistics-available-on-readable-secondary-read-only-database-and-database-snapshot) (Always On：在可讀取次要、唯讀資料庫和資料庫快照集上提供最新的統計資料)</span><span class="sxs-lookup"><span data-stu-id="af93c-225">[Always On: Making latest statistics available on Readable Secondary, Read-Only database and Database Snapshot](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-making-latest-statistics-available-on-readable-secondary-read-only-database-and-database-snapshot)</span></span>  
  
-   <span data-ttu-id="af93c-226">[Always On:Challenges with statistics on ReadOnly database, Database Snapshot and Secondary Replica](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-challenges-with-statistics-on-readonly-database-database-snapshot-and-secondary-replica) (Always On：唯讀資料庫、資料庫快照集和次要複本上的統計資料挑戰)</span><span class="sxs-lookup"><span data-stu-id="af93c-226">[Always On: Challenges with statistics on ReadOnly database, Database Snapshot and Secondary Replica](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-challenges-with-statistics-on-readonly-database-database-snapshot-and-secondary-replica)</span></span>  
  
-   <span data-ttu-id="af93c-227">[Always On:Impact on the primary workload when you run reporting workload on the secondary replica](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-impact-on-the-primary-workload-when-you-run-reporting-workload-on-the-secondary-replica) (Always On：在次要複本上執行報告工作負載時，對主要工作負載的影響)</span><span class="sxs-lookup"><span data-stu-id="af93c-227">[Always On: Impact on the primary workload when you run reporting workload on the secondary replica](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-impact-on-the-primary-workload-when-you-run-reporting-workload-on-the-secondary-replica)</span></span>  
  
-   <span data-ttu-id="af93c-228">[Always On:Impact of mapping reporting workload on Readable Secondary to Snapshot Isolation](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-impact-of-mapping-reporting-workload-on-readable-secondary-to-snapshot-isolation) (Always On：可讀取次要上報告工作負載對應至快照集隔離的影響)</span><span class="sxs-lookup"><span data-stu-id="af93c-228">[Always On: Impact of mapping reporting workload on Readable Secondary to Snapshot Isolation](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-impact-of-mapping-reporting-workload-on-readable-secondary-to-snapshot-isolation)</span></span>  
  
-   <span data-ttu-id="af93c-229">[Always On:Minimizing blocking of REDO thread when running reporting workload on Secondary Replica](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-minimizing-blocking-of-redo-thread-when-running-reporting-workload-on-secondary-replica) (Always On：在次要複本上執行報告工作負載時，將 REDO 執行緒封鎖降至最低)</span><span class="sxs-lookup"><span data-stu-id="af93c-229">[Always On: Minimizing blocking of REDO thread when running reporting workload on Secondary Replica](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-minimizing-blocking-of-redo-thread-when-running-reporting-workload-on-secondary-replica)</span></span>  
  
-   <span data-ttu-id="af93c-230">[Always On:Readable Secondary and data latency](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-readable-secondary-and-data-latency) (Always On：可讀取次要和資料延遲)</span><span class="sxs-lookup"><span data-stu-id="af93c-230">[Always On: Readable Secondary and data latency](https://docs.microsoft.com/archive/blogs/sqlserverstorageengine/alwayson-readable-secondary-and-data-latency)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af93c-231">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af93c-231">See Also</span></span>  
 <span data-ttu-id="af93c-232">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="af93c-232">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="af93c-233">使用中次要：可讀取的次要複本 &#40;AlwaysOn 可用性群組&#41;</span><span class="sxs-lookup"><span data-stu-id="af93c-233">Active Secondaries: Readable Secondary Replicas &#40;AlwaysOn Availability Groups&#41;</span></span>](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)  
 [<span data-ttu-id="af93c-234">關於可用性複本的用戶端連接存取 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="af93c-234">About Client Connection Access to Availability Replicas &#40;SQL Server&#41;</span></span>](about-client-connection-access-to-availability-replicas-sql-server.md)  
