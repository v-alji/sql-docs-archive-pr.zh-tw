---
title: 設定可用性群組的唯讀路由 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- read-only routing
- Availability Groups [SQL Server], readable secondary replicas
- Availability Groups [SQL Server], read-only routing
- readable secondary replicas
- Availability Groups [SQL Server], client connectivity
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 7bd89ddd-0403-4930-a5eb-3c78718533d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2d51d1db75caa29814a01fc1f49bfdd49b403c3d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598001"
---
# <a name="configure-read-only-routing-for-an-availability-group-sql-server"></a><span data-ttu-id="06363-102">設定可用性群組的唯讀路由 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="06363-102">Configure Read-Only Routing for an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="06363-103">若要在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中將 AlwaysOn 可用性群組設定為支援唯讀路由，可以使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="06363-103">To configure an AlwaysOn availability group to support read-only routing in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], you can use either [!INCLUDE[tsql](../../../includes/tsql-md.md)] or PowerShell.</span></span> <span data-ttu-id="06363-104">*「唯讀路由」* (Read-Only Routing) 是指 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 將合格的唯讀連接要求路由至可用之 AlwaysOn [可讀取的次要複本](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) (亦即在以次要角色執行時，設定為允許唯讀工作負載的複本) 的功能。</span><span class="sxs-lookup"><span data-stu-id="06363-104">*Read-only routing* refers to the ability of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to route qualifying read-only connection requests to an available AlwaysOn [readable secondary replica](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) (that is, a replica that is configured to allow read-only workloads when running under the secondary role).</span></span> <span data-ttu-id="06363-105">若要支援唯讀路由，可用性群組必須具有 [可用性群組接聽程式](../../listeners-client-connectivity-application-failover.md)。</span><span class="sxs-lookup"><span data-stu-id="06363-105">To support read-only routing, the availability group must possess an [availability group listener](../../listeners-client-connectivity-application-failover.md).</span></span> <span data-ttu-id="06363-106">唯讀用戶端必須將其連接要求導向至此接聽程式，且用戶端的連接字串必須將應用程式的意圖指定為「唯讀」。</span><span class="sxs-lookup"><span data-stu-id="06363-106">Read-only clients must direct their connection requests to this listener, and the client's connection strings must specify the application intent as "read-only."</span></span> <span data-ttu-id="06363-107">換句話說必須是 *「讀取意圖的連接要求」* (Read-Intent Connection Request)。</span><span class="sxs-lookup"><span data-stu-id="06363-107">That is, they must be *read-intent connection requests*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06363-108">如需如何設定可讀取之次要複本的相關資訊，請參閱 [設定可用性複本上的唯讀存取 &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="06363-108">For information about how to configure a readable secondary replica, see [Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="06363-109">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]不支援設定唯讀路由。</span><span class="sxs-lookup"><span data-stu-id="06363-109">Configuring read-only routing is not supported by [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="06363-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="06363-110">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="06363-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="06363-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="06363-112">可用性群組必須擁有可用性群組接聽程式。</span><span class="sxs-lookup"><span data-stu-id="06363-112">The availability group must possess an availability group listener.</span></span> <span data-ttu-id="06363-113">如需詳細資訊，請參閱 [建立或設定可用性群組接聽程式 &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="06363-113">For more information, see [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).</span></span>  
  
-   <span data-ttu-id="06363-114">一或多個可用性複本必須設定為接受次要角色中的唯讀， (也就是可讀取的[次要複本](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) (AlwaysOn% 20Availability% 20Groups \)) # A3。</span><span class="sxs-lookup"><span data-stu-id="06363-114">One or more availability replicas must be configured to accept read-only in the secondary role (that is, to be [readable secondary replicas](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)(AlwaysOn%20Availability%20Groups\).md)).</span></span> <span data-ttu-id="06363-115">如需詳細資訊，請參閱 [設定可用性複本上的唯讀存取 &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="06363-115">For more information, see [Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md).</span></span>  
  
-   <span data-ttu-id="06363-116">您必須連接到裝載目前主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="06363-116">You must be connected to the server instance that hosts the current primary replica.</span></span>  
  
###  <a name="what-replica-properties-do-you-need-to-configure-to-support-read-only-routing"></a><a name="RORReplicaProperties"></a><span data-ttu-id="06363-117">您需要設定哪些複本屬性，才能支援唯讀路由？</span><span class="sxs-lookup"><span data-stu-id="06363-117">What Replica Properties Do you Need to Configure to Support Read-Only Routing?</span></span>  
  
-   <span data-ttu-id="06363-118">每一個要支援唯讀路由之可讀取的次要複本，皆必須指定 *「唯讀路由 URL」*(Read-Only Routing URL)。</span><span class="sxs-lookup"><span data-stu-id="06363-118">For each readable secondary replica that is to support read-only routing, you need to specify a *read-only routing URL*.</span></span> <span data-ttu-id="06363-119">只有在本機複本以次要角色執行時，此 URL 才會生效。</span><span class="sxs-lookup"><span data-stu-id="06363-119">This URL takes effect only when the local replica is running under the secondary role.</span></span> <span data-ttu-id="06363-120">如有必要，您必須各自指定每個複本的唯讀路由 URL。</span><span class="sxs-lookup"><span data-stu-id="06363-120">The read-only routing URL must be specified on a replica-by-replica basis, as needed.</span></span> <span data-ttu-id="06363-121">每個唯讀路由 URL 可用於將讀取意圖的連接要求路由至特定可讀取的次要複本。</span><span class="sxs-lookup"><span data-stu-id="06363-121">Each read-only routing URL is used for routing read-intent connection requests to a specific readable secondary replica.</span></span> <span data-ttu-id="06363-122">一般而言，每個可讀取的次要複本都有一個指派的唯讀路由 URL。</span><span class="sxs-lookup"><span data-stu-id="06363-122">Typically, every readable secondary replica is assigned a read-only routing URL.</span></span>  
  
     <span data-ttu-id="06363-123">如需有關計算可用性複本之唯讀路由 URL 的詳細資訊，請參閱 [計算 AlwaysOn 的 read_only_routing_url](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson)。</span><span class="sxs-lookup"><span data-stu-id="06363-123">For information about calculating the read-only routing URL for an availability replica, see [Calculating read_only_routing_url for AlwaysOn](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson).</span></span>  
  
-   <span data-ttu-id="06363-124">如果要支援唯讀路由的可用性複本為主要複本時，則必須指定 *「唯讀路由清單」*(Read-Only Routing List)。</span><span class="sxs-lookup"><span data-stu-id="06363-124">For each availability replica that you want to support read-only routing when it is the primary replica, you need to specify a *read-only routing list*.</span></span> <span data-ttu-id="06363-125">只有本機複本以主要角色執行時，給定的唯讀路由清單才會生效。</span><span class="sxs-lookup"><span data-stu-id="06363-125">A given read-only routing list takes effect only when the local replica is running under the primary role.</span></span> <span data-ttu-id="06363-126">如有必要，您必須各自指定每個複本的這份清單。</span><span class="sxs-lookup"><span data-stu-id="06363-126">This list must be specified on a replica-by-replica basis, as needed.</span></span> <span data-ttu-id="06363-127">一般而言，每份唯讀路由清單皆會包含每一個唯讀路由 URL，並在清單結尾提供本機複本的 URL。</span><span class="sxs-lookup"><span data-stu-id="06363-127">Typically, each read-only routing list would contain every read-only routing URL, with the URL of the local replica at the end of the list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="06363-128">讀取意圖的連接要求會路由至目前之主要複本的唯讀路由清單上，第一個可用之可讀取的次要複本。</span><span class="sxs-lookup"><span data-stu-id="06363-128">Read-intent connection requests are routed to the first available readable secondary on the read-only routing list of the current primary replica.</span></span> <span data-ttu-id="06363-129">沒有負載平衡。</span><span class="sxs-lookup"><span data-stu-id="06363-129">There is no load balancing.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06363-130">如需可用性群組接聽程式的相關資訊，以及唯讀路由的詳細資訊，請參閱 [可用性群組接聽程式、用戶端連接性及應用程式容錯移轉 &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)。</span><span class="sxs-lookup"><span data-stu-id="06363-130">For information about availability group listeners and more information about read-only routing, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="06363-131">Security</span><span class="sxs-lookup"><span data-stu-id="06363-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="06363-132">權限</span><span class="sxs-lookup"><span data-stu-id="06363-132">Permissions</span></span>  
  
|<span data-ttu-id="06363-133">Task</span><span class="sxs-lookup"><span data-stu-id="06363-133">Task</span></span>|<span data-ttu-id="06363-134">權限</span><span class="sxs-lookup"><span data-stu-id="06363-134">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="06363-135">若要在建立可用性群組時設定複本</span><span class="sxs-lookup"><span data-stu-id="06363-135">To configure replicas when creating an availability group</span></span>|<span data-ttu-id="06363-136">需要 **系統管理員 (sysadmin)** 固定伺服器角色的成員資格，以及 CREATE AVAILABILITY GROUP 伺服器權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="06363-136">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
|<span data-ttu-id="06363-137">若要修改可用性複本</span><span class="sxs-lookup"><span data-stu-id="06363-137">To modify an availability replica</span></span>|<span data-ttu-id="06363-138">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="06363-138">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="06363-139">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="06363-139">Using Transact-SQL</span></span>  
 <span data-ttu-id="06363-140">**若要設定唯讀路由**</span><span class="sxs-lookup"><span data-stu-id="06363-140">**To Configure read-only routing**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06363-141">如需程式碼範例，請參閱本節稍後的 [範例 (Transact-SQL)](#TsqlExample)。</span><span class="sxs-lookup"><span data-stu-id="06363-141">For a code example, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="06363-142">連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="06363-142">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="06363-143">如果您要針對新的可用性群組指定複本，請使用 [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="06363-143">If you are specifying a replica for a new availability group, use the [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="06363-144">如果您要加入或修改現有可用性群組的複本，請使用[ALTER AVAILABILITY group](/sql/t-sql/statements/alter-availability-group-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] 語句。</span><span class="sxs-lookup"><span data-stu-id="06363-144">If you are adding or modifying a replica for an existing availability group, use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span>  
  
    -   <span data-ttu-id="06363-145">若要設定次要角色的唯讀路由，請在 ADD REPLICA 或 MODIFY REPLICA WITH 子句中指定 SECONDARY_ROLE 選項，如下所示：</span><span class="sxs-lookup"><span data-stu-id="06363-145">To configure read-only routing for the secondary role, in the ADD REPLICA or MODIFY REPLICA WITH clause, specify the SECONDARY_ROLE option, as follows:</span></span>  
  
         <span data-ttu-id="06363-146">SECONDARY_ROLE \*\* (\*\* READ_ONLY_ROUTING_URL **= '** TCP：\*\*// *`system-address`* ： *`port`* ' ) \*\*</span><span class="sxs-lookup"><span data-stu-id="06363-146">SECONDARY_ROLE **(** READ_ONLY_ROUTING_URL **='** TCP **://*`system-address`*:*`port`*')**</span></span>  
  
         <span data-ttu-id="06363-147">唯讀路由 URL 的參數如下：</span><span class="sxs-lookup"><span data-stu-id="06363-147">The parameters of the read-only routing URL are as follows:</span></span>  
  
         <span data-ttu-id="06363-148">*system-address*</span><span class="sxs-lookup"><span data-stu-id="06363-148">*system-address*</span></span>  
         <span data-ttu-id="06363-149">這是明確識別目的地電腦系統的字串，例如系統名稱、完整網域名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="06363-149">Is a string, such as a system name, a fully qualified domain name, or an IP address, that unambiguously identifies the destination computer system.</span></span>  
  
         <span data-ttu-id="06363-150">*port*</span><span class="sxs-lookup"><span data-stu-id="06363-150">*port*</span></span>  
         <span data-ttu-id="06363-151">這是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體之 Database Engine 所使用的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="06363-151">Is a port number that is used by the Database Engine of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span>  
  
         <span data-ttu-id="06363-152">例如：   `SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433')`</span><span class="sxs-lookup"><span data-stu-id="06363-152">For example:   `SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433')`</span></span>  
  
         <span data-ttu-id="06363-153">在 MODIFY REPLICA 子句中，ALLOW_CONNECTIONS 是選擇性的 (如果複本已經設定為允許唯讀連接的話)。</span><span class="sxs-lookup"><span data-stu-id="06363-153">In a MODIFY REPLICA clause the ALLOW_CONNECTIONS is optional if the replica is already configured to allow read-only connections.</span></span>  
  
         <span data-ttu-id="06363-154">如需詳細資訊，請參閱 [計算 AlwaysOn 的 read_only_routing_url](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson)。</span><span class="sxs-lookup"><span data-stu-id="06363-154">For more information, see [Calculating read_only_routing_url for AlwaysOn](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson).</span></span>  
  
    -   <span data-ttu-id="06363-155">若要設定主要角色的唯讀路由，請在 ADD REPLICA 或 MODIFY REPLICA WITH 子句中指定 PRIMARY_ROLE 選項，如下所示：</span><span class="sxs-lookup"><span data-stu-id="06363-155">To configure read-only routing for the primary role, in the ADD REPLICA or MODIFY REPLICA WITH clause, specify the PRIMARY_ROLE option, as follows:</span></span>  
  
         <span data-ttu-id="06363-156">PRIMARY_ROLE \*\* (\*\* READ_ONLY_ROUTING_LIST **= ( ' *`server`* '** [ **，**.。。*n* ] **) # B3**</span><span class="sxs-lookup"><span data-stu-id="06363-156">PRIMARY_ROLE **(** READ_ONLY_ROUTING_LIST **=('*`server`*'** [ **,**...*n* ] **))**</span></span>  
  
         <span data-ttu-id="06363-157">其中， *server* 會識別裝載可用性群組中唯讀次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="06363-157">where, *server* identifies a server instance that hosts a read-only secondary replica in the availability group.</span></span>  
  
         <span data-ttu-id="06363-158">例如：   `PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('Server1','Server2'))`</span><span class="sxs-lookup"><span data-stu-id="06363-158">For example:   `PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('Server1','Server2'))`</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="06363-159">您必須先設定唯讀路由 URL，然後再設定唯讀路由清單。</span><span class="sxs-lookup"><span data-stu-id="06363-159">You must set the read-only routing URL before configuring the read-only routing list.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="06363-160">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="06363-160">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="06363-161">下列範例會將現有可用性群組 `AG1` 的兩個可用性複本修改成支援唯讀路由 (如果其中一個複本目前擁有主要角色的話)。</span><span class="sxs-lookup"><span data-stu-id="06363-161">The following example modifies two availability replicas of an existing availability group, `AG1` to support read-only routing if one of these replicas currently owns the primary role.</span></span> <span data-ttu-id="06363-162">為了識別裝載可用性複本的伺服器執行個體，此範例會指定執行個體名稱：`COMPUTER01` 和 `COMPUTER02`。</span><span class="sxs-lookup"><span data-stu-id="06363-162">To identify the server instances that host the availability replica, this example specifies the instance names-`COMPUTER01` and `COMPUTER02`.</span></span>  
  
```sql
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY));  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433'));  
  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY));  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER02.contoso.com:1433'));  
  
ALTER AVAILABILITY GROUP [AG1]   
MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('COMPUTER02','COMPUTER01')));  
  
ALTER AVAILABILITY GROUP [AG1]   
MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('COMPUTER01','COMPUTER02')));  
GO
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="06363-163">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="06363-163">Using PowerShell</span></span>  

### <a name="to-configure-read-only-routing"></a><span data-ttu-id="06363-164">若要設定唯讀路由</span><span class="sxs-lookup"><span data-stu-id="06363-164">To Configure read-only routing</span></span>
  
> [!NOTE]  
>  <span data-ttu-id="06363-165">如需程式碼範例，請參閱本節稍後的 [範例 (PowerShell)](#PSExample)。</span><span class="sxs-lookup"><span data-stu-id="06363-165">For a code example, see [Example (PowerShell)](#PSExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="06363-166">將預設值 (`cd`) 設定為裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="06363-166">Set default (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="06363-167">將可用性複本加入至可用性群組時，請使用 `New-SqlAvailabilityReplica` 指令程式。</span><span class="sxs-lookup"><span data-stu-id="06363-167">When adding an availability replica to an availability group, use the `New-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="06363-168">修改現有的可用性複本時，請使用 `Set-SqlAvailabilityReplica` 指令程式。</span><span class="sxs-lookup"><span data-stu-id="06363-168">When modifying an existing availability replica, use the `Set-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="06363-169">相關參數如下所示：</span><span class="sxs-lookup"><span data-stu-id="06363-169">The relevant parameters are as follows:</span></span>  
  
    -   <span data-ttu-id="06363-170">若要設定次要角色的唯讀路由，請指定**ReadonlyRoutingConnectionUrl " *`url`* "** 參數。</span><span class="sxs-lookup"><span data-stu-id="06363-170">To configure read-only routing for the secondary role, specify the **ReadonlyRoutingConnectionUrl"*`url`*"** parameter.</span></span>  
  
         <span data-ttu-id="06363-171">其中， *url* 是路由至複本進行唯讀連接時要使用的連接性完整網域名稱 (FQDN) 和通訊埠。</span><span class="sxs-lookup"><span data-stu-id="06363-171">where, *url* is the connectivity fully-qualified domain name (FQDN) and port to use when routing to the replica for read-only connections.</span></span> <span data-ttu-id="06363-172">例如：`-ReadonlyRoutingConnectionUrl "TCP://DBSERVER8.manufacturing.Adventure-Works.com:7024"`</span><span class="sxs-lookup"><span data-stu-id="06363-172">For example:  `-ReadonlyRoutingConnectionUrl "TCP://DBSERVER8.manufacturing.Adventure-Works.com:7024"`</span></span>  
  
         <span data-ttu-id="06363-173">如需詳細資訊，請參閱 [計算 AlwaysOn 的 read_only_routing_url](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson)。</span><span class="sxs-lookup"><span data-stu-id="06363-173">For more information, see [Calculating read_only_routing_url for AlwaysOn](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson).</span></span>  
  
    -   <span data-ttu-id="06363-174">若要設定主要角色的連接存取，請指定**ReadonlyRoutingList " *`server`* "** [ **，**.。。*n* ]，其中*server*會識別裝載可用性群組中唯讀次要複本的伺服器實例。</span><span class="sxs-lookup"><span data-stu-id="06363-174">To configure connection access for the primary role, specify **ReadonlyRoutingList"*`server`*"** [ **,**...*n* ], where *server* identifies a server instance that hosts a read-only secondary replica in the availability group.</span></span> <span data-ttu-id="06363-175">例如：`-ReadOnlyRoutingList "SecondaryServer","PrimaryServer"`</span><span class="sxs-lookup"><span data-stu-id="06363-175">For example:  `-ReadOnlyRoutingList "SecondaryServer","PrimaryServer"`</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="06363-176">您必須先設定複本的唯讀路由 URL，然後再設定其唯讀路由清單。</span><span class="sxs-lookup"><span data-stu-id="06363-176">You must set the read-only routing URL of a replica before configuring its read-only routing list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="06363-177">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="06363-177">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="06363-178">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="06363-178">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="06363-179">若要設定及使用 SQL Server PowerShell 提供者，請參閱[SQL Server PowerShell 提供者](../../../powershell/sql-server-powershell-provider.md)並[取得說明 SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="06363-179">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md) and [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>
  
###  <a name="example-powershell"></a><a name="PSExample"></a> <span data-ttu-id="06363-180">範例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="06363-180">Example (PowerShell)</span></span>  
 <span data-ttu-id="06363-181">下列範例會將可用性群組中的主要複本和一個次要複本設定為唯讀路由。</span><span class="sxs-lookup"><span data-stu-id="06363-181">The following example configures the primary replica and one secondary replica in an availability group for read-only routing.</span></span> <span data-ttu-id="06363-182">首先，此範例會將唯讀路由 URL 指派給每個複本。</span><span class="sxs-lookup"><span data-stu-id="06363-182">First, the example assigns a read-only routing URL to each replica.</span></span> <span data-ttu-id="06363-183">然後，它會設定主要複本的唯讀路由清單。</span><span class="sxs-lookup"><span data-stu-id="06363-183">Then it sets the read-only routing list on the primary replica.</span></span> <span data-ttu-id="06363-184">在連接字串中設定 "ReadOnly" 屬性的連接將會重新導向至次要複本。</span><span class="sxs-lookup"><span data-stu-id="06363-184">Connections with the "ReadOnly" property set in the connection string will be redirected to the secondary replica.</span></span> <span data-ttu-id="06363-185">如果這個次要複本無法讀取 (由 `ConnectionModeInSecondaryRole` 設定決定)，連接將會導向回到主要複本。</span><span class="sxs-lookup"><span data-stu-id="06363-185">If this secondary replica is not readable (as determined by the `ConnectionModeInSecondaryRole` setting), the connection will be directed back to the primary replica.</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\PrimaryServer\default\AvailabilityGroups\MyAg  
$primaryReplica = Get-Item "AvailabilityReplicas\PrimaryServer"  
$secondaryReplica = Get-Item "AvailabilityReplicas\SecondaryServer"  
  
Set-SqlAvailabilityReplica -ReadOnlyRoutingConnectionUrl "TCP://PrimaryServer.domain.com:1433" -InputObject $primaryReplica  
Set-SqlAvailabilityReplica -ReadOnlyRoutingConnectionUrl "TCP://SecondaryServer.domain.com:1433" -InputObject $secondaryReplica  
Set-SqlAvailabilityReplica -ReadOnlyRoutingList "SecondaryServer","PrimaryServer" -InputObject $primaryReplica  
```  
  
##  <a name="follow-up-after-configuring-read-only-routing"></a><a name="FollowUp"></a> <span data-ttu-id="06363-186">後續操作：設定唯讀路由之後</span><span class="sxs-lookup"><span data-stu-id="06363-186">Follow Up: After Configuring Read-Only Routing</span></span>  
 <span data-ttu-id="06363-187">一旦目前的主要複本和可讀取的次要複本都設定為支援兩種角色的唯讀路由之後，可讀取的次要複本就可以從經由可用性群組接聽程式連接的用戶端接收讀取意圖連接要求。</span><span class="sxs-lookup"><span data-stu-id="06363-187">Once the current primary replica and the readable secondary replicas are configured to support read-only routing in both roles, the readable secondary replicas can receive read read-intent connection requests from clients that connect via the availability group listener.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="06363-188">使用[Bcp 公用程式](../../../tools/bcp-utility.md)或[sqlcmd 公用程式](../../../tools/sqlcmd-utility.md)時，您可以藉由指定參數，為啟用唯讀存取的任何次要複本指定唯讀存取 `-K ReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="06363-188">When using the [bcp Utility](../../../tools/bcp-utility.md) or [sqlcmd Utility](../../../tools/sqlcmd-utility.md), you can specify read-only access to any secondary replica that is enabled for read-only access by specifying the `-K ReadOnly` switch.</span></span>  
  
###  <a name="requirements-and-recommendations-for-client-connection-strings"></a><a name="ConnStringReqsRecs"></a> <span data-ttu-id="06363-189">用戶端連接字串的需求和建議</span><span class="sxs-lookup"><span data-stu-id="06363-189">Requirements and Recommendations for Client Connection-Strings</span></span>  
 <span data-ttu-id="06363-190">若要讓用戶端應用程式使用唯讀路由，其連接字串必須滿足下列需求：</span><span class="sxs-lookup"><span data-stu-id="06363-190">For a client application to use read-only routing, its connection string must satisfy the following requirements:</span></span>  
  
-   <span data-ttu-id="06363-191">使用 TCP 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="06363-191">Use the TCP protocol.</span></span>  
  
-   <span data-ttu-id="06363-192">將應用程式意圖屬性 (Attribute)/屬性 (Property) 設定成唯讀。</span><span class="sxs-lookup"><span data-stu-id="06363-192">Set the application intent attribute/property to readonly.</span></span>  
  
-   <span data-ttu-id="06363-193">參考設定為支援唯讀路由之可用性群組的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="06363-193">Reference the listener of an availability group that is configured to support read-only routing.</span></span>  
  
-   <span data-ttu-id="06363-194">參考該可用性群組中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="06363-194">Reference a database in that availability group.</span></span>  
  
 <span data-ttu-id="06363-195">此外，我們建議連接字串要啟用多重子網路容錯移轉，以便針對每個子網路上的每個複本支援平行用戶端執行緒。</span><span class="sxs-lookup"><span data-stu-id="06363-195">In addition, we recommend that connection strings enable multi-subnet failover, which supports a parallel client thread for each replica on each subnet.</span></span> <span data-ttu-id="06363-196">這樣做可在容錯移轉之後盡量縮短用戶端重新連接時間。</span><span class="sxs-lookup"><span data-stu-id="06363-196">This minimizes client reconnection time after a failover.</span></span>  
  
 <span data-ttu-id="06363-197">連接字串的語法主要取決於應用程式所使用的 SQL Server 提供者。</span><span class="sxs-lookup"><span data-stu-id="06363-197">The syntax for a connection string depends on the SQL Server provider an application is using.</span></span> <span data-ttu-id="06363-198">下列 .NET Framework Data Provider 4.0.2 for SQL Server 範例連接字串說明了針對唯讀路由運作時必要且建議的連接字串部分。</span><span class="sxs-lookup"><span data-stu-id="06363-198">The following example connection string for the .NET Framework Data Provider 4.0.2 for SQL Server illustrates the parts of a connection string that are required and recommended to work for read-only routing.</span></span>  
  
```  
Server=tcp:MyAgListener,1433;Database=Db1;IntegratedSecurity=SSPI;ApplicationIntent=ReadOnly;MultiSubnetFailover=True  
```  
  
 <span data-ttu-id="06363-199">如需唯讀應用程式意圖和唯讀路由的詳細資訊，請參閱 [可用性群組接聽程式、用戶端連接性及應用程式容錯移轉 &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)。</span><span class="sxs-lookup"><span data-stu-id="06363-199">For more information about read-only application intent and read-only routing, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).</span></span>  
  
### <a name="if-read-only-routing-is-not-working-correctly"></a><span data-ttu-id="06363-200">如果唯讀路由未正確運作</span><span class="sxs-lookup"><span data-stu-id="06363-200">If Read-Only Routing is Not Working Correctly</span></span>  
 <span data-ttu-id="06363-201">如需針對唯讀路由組態進行疑難排解的相關資訊，請參閱 [唯讀路由未正確運作](troubleshoot-always-on-availability-groups-configuration-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="06363-201">For information about troubleshooting a read-only routing configuration, see [Read-Only Routing is Not Working Correctly](troubleshoot-always-on-availability-groups-configuration-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="06363-202">相關工作</span><span class="sxs-lookup"><span data-stu-id="06363-202">Related Tasks</span></span>  

### <a name="to-view-read-only-routing-configurations"></a><span data-ttu-id="06363-203">若要檢視唯讀路由組態</span><span class="sxs-lookup"><span data-stu-id="06363-203">To view read-only routing configurations</span></span>
  
-   [<span data-ttu-id="06363-204">sys.availability_read_only_routing_lists &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="06363-204">sys.availability_read_only_routing_lists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
  
-   <span data-ttu-id="06363-205">[sys.availability_replicas &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) (**read_only_routing_url** 資料行)</span><span class="sxs-lookup"><span data-stu-id="06363-205">[sys.availability_replicas &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) (**read_only_routing_url** column)</span></span>  
  
### <a name="to-configure-client-connection-access"></a><span data-ttu-id="06363-206">若要設定用戶端連接存取</span><span class="sxs-lookup"><span data-stu-id="06363-206">To configure client connection access</span></span>
  
-   [<span data-ttu-id="06363-207">建立或設定可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="06363-207">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="06363-208">設定可用性複本的唯讀存取 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="06363-208">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
### <a name="to-use-connection-strings-in-applications"></a><span data-ttu-id="06363-209">若要在應用程式中使用連接字串</span><span class="sxs-lookup"><span data-stu-id="06363-209">To use connection strings in applications</span></span>
  
-   [<span data-ttu-id="06363-210">高可用性/災害復原的 SQL Server Native Client 支援</span><span class="sxs-lookup"><span data-stu-id="06363-210">SQL Server Native Client Support for High Availability, Disaster Recovery</span></span>](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
  
-   [<span data-ttu-id="06363-211">搭配 SQL Server Native Client 使用連接字串關鍵字</span><span class="sxs-lookup"><span data-stu-id="06363-211">Using Connection String Keywords with SQL Server Native Client</span></span>](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="06363-212">相關內容</span><span class="sxs-lookup"><span data-stu-id="06363-212">Related Content</span></span>  
  
-   <span data-ttu-id="06363-213">**部落格：**</span><span class="sxs-lookup"><span data-stu-id="06363-213">**Blogs:**</span></span>  
  
     [<span data-ttu-id="06363-214">計算 AlwaysOn 的 read_only_routing_url</span><span class="sxs-lookup"><span data-stu-id="06363-214">Calculating read_only_routing_url for AlwaysOn</span></span>](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson)  
  
     [<span data-ttu-id="06363-215">SQL Server AlwaysOn 團隊部落格：官方 SQL Server AlwaysOn 團隊部落格</span><span class="sxs-lookup"><span data-stu-id="06363-215">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="06363-216">CSS SQL Server 工程師部落格</span><span class="sxs-lookup"><span data-stu-id="06363-216">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="06363-217">**白皮書：**</span><span class="sxs-lookup"><span data-stu-id="06363-217">**White papers:**</span></span>  
  
     [<span data-ttu-id="06363-218">Microsoft 的 SQL Server 2012 白皮書</span><span class="sxs-lookup"><span data-stu-id="06363-218">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="06363-219">SQL Server 客戶諮詢團隊白皮書</span><span class="sxs-lookup"><span data-stu-id="06363-219">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="06363-220">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06363-220">See Also</span></span>  
 <span data-ttu-id="06363-221">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="06363-221">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="06363-222">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="06363-222">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="06363-223">[使用中次要：可讀取的次要複本 (AlwaysOn 可用性群組) ](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="06363-223">[Active Secondaries: Readable Secondary Replicas (AlwaysOn Availability Groups)](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="06363-224">[關於可用性複本的用戶端連線存取 &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="06363-224">[About Client Connection Access to Availability Replicas &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) </span></span>  
 [<span data-ttu-id="06363-225">可用性群組接聽程式、用戶端連線及應用程式容錯移轉 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="06363-225">Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;</span></span>](../../listeners-client-connectivity-application-failover.md)  
