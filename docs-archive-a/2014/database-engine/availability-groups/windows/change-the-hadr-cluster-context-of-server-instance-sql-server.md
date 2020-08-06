---
title: 變更伺服器執行個體的 HADR 叢集內容 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- Availability replicas [SQL Server], change WSFC cluster context
ms.assetid: ecd99f91-b9a2-4737-994e-507065a12f80
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cbc29fa2ebaaf2bbc9e577b5bd303e8a0dd0ec4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708677"
---
# <a name="change-the-hadr-cluster-context-of-server-instance-sql-server"></a><span data-ttu-id="32bf2-102">變更伺服器執行個體的 HADR 叢集內容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="32bf2-102">Change the HADR Cluster Context of Server Instance (SQL Server)</span></span>
  <span data-ttu-id="32bf2-103">本主題描述如何使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 和更新版本中的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 切換 [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] 執行個體的 HADR 叢集內容。</span><span class="sxs-lookup"><span data-stu-id="32bf2-103">This topic describes how to switch the HADR cluster context of an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] and later versions.</span></span> <span data-ttu-id="32bf2-104">「HADR 叢集內容」\*\* 會決定哪個 Windows Server 容錯移轉叢集 (WSFC) 叢集管理伺服器執行個體所裝載可用性複本的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="32bf2-104">The *HADR cluster context* determines which Windows Server Failover Clustering (WSFC) cluster manages the metadata for availability replicas hosted by the server instance.</span></span>  
  
 <span data-ttu-id="32bf2-105">僅在跨叢集移轉 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 至新 WSFC 叢集上的 [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] 執行個體時，才切換 HADR 叢集內容。</span><span class="sxs-lookup"><span data-stu-id="32bf2-105">Switch the HADR cluster context only during a cross-cluster migration of [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] to an instance of [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] on a new WSFC cluster.</span></span> <span data-ttu-id="32bf2-106">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 的跨叢集移轉支援以最短的可用性群組停機時間升級為 [!INCLUDE[win8](../../../includes/win8-md.md)] 或 [!INCLUDE[win8srv](../../../includes/win8srv-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="32bf2-106">Cross-cluster migration of [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] supports OS upgrade to [!INCLUDE[win8](../../../includes/win8-md.md)] or [!INCLUDE[win8srv](../../../includes/win8srv-md.md)] with minimal downtime of availability groups.</span></span> <span data-ttu-id="32bf2-107">如需詳細資訊，請參閱[針對作業系統升級進行 AlwaysOn 可用性群組的跨叢集移轉](https://msdn.microsoft.com/library/jj873730.aspx)。</span><span class="sxs-lookup"><span data-stu-id="32bf2-107">For more information, see [Cross-Cluster Migration of AlwaysOn Availability Groups for OS Upgrade](https://msdn.microsoft.com/library/jj873730.aspx).</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="32bf2-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="32bf2-108">Before You Begin</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="32bf2-109">僅在跨叢集移轉 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 部署時才切換 HADR 叢集內容。</span><span class="sxs-lookup"><span data-stu-id="32bf2-109">Switch the HADR cluster context only during cross-cluster migration of [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] deployments.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="32bf2-110">限制事項</span><span class="sxs-lookup"><span data-stu-id="32bf2-110">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="32bf2-111">您只能將 HADR 叢集內容從本機 WSFC 叢集切換至遠端叢集，然後從遠端叢集切換回本機叢集。</span><span class="sxs-lookup"><span data-stu-id="32bf2-111">You can switch the HADR cluster context only from the local WSFC cluster to a remote cluster and then back from the remote cluster to the local cluster.</span></span> <span data-ttu-id="32bf2-112">您無法將 HADR 叢集內容從某一個遠端叢集切換至另一個遠端叢集。</span><span class="sxs-lookup"><span data-stu-id="32bf2-112">You cannot switch the HADR cluster context from one remote cluster to another remote cluster.</span></span>  
  
-   <span data-ttu-id="32bf2-113">HADR 叢集內容只有在 SQL Server 執行個體未裝載任何可用性複本時，才能切換至遠端叢集。</span><span class="sxs-lookup"><span data-stu-id="32bf2-113">The HADR cluster context can be switched to a remote cluster only when the instance of SQL Server is not hosting any availability replicas.</span></span>  
  
-   <span data-ttu-id="32bf2-114">遠端 HADR 叢集內容隨時可以切換回本機叢集。</span><span class="sxs-lookup"><span data-stu-id="32bf2-114">A remote HADR cluster context can be switched back to the local cluster at any time.</span></span> <span data-ttu-id="32bf2-115">不過，只要伺服器執行個體裝載任何可用性複本，內容就不能再次切換。</span><span class="sxs-lookup"><span data-stu-id="32bf2-115">However, the context cannot be switched again as long as the server instance is hosting any availability replicas.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="32bf2-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="32bf2-116">Prerequisites</span></span>  
  
-   <span data-ttu-id="32bf2-117">您變更 HADR 叢集內容所在的伺服器執行個體必須執行 [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] 或更新版本 (Enterprise Edition 或更新版本)。</span><span class="sxs-lookup"><span data-stu-id="32bf2-117">The server instance on which you change the HADR cluster context must be running [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] or above (Enterprise edition or above).</span></span>  
  
-   <span data-ttu-id="32bf2-118">伺服器執行個體必須針對 AlwaysOn 啟用。</span><span class="sxs-lookup"><span data-stu-id="32bf2-118">The server instance must be enabled for AlwaysOn.</span></span> <span data-ttu-id="32bf2-119">如需詳細資訊，請參閱[啟用和停用 AlwaysOn 可用性群組 &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="32bf2-119">For more information, see [Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="32bf2-120">若要符合從本機叢集內容切換至遠端叢集的資格，伺服器執行個體不可裝載任何可用性複本。</span><span class="sxs-lookup"><span data-stu-id="32bf2-120">To be eligible to be switched from the local cluster context to a remote cluster cluster, a server instance cannot be hosting any availability replicas.</span></span> <span data-ttu-id="32bf2-121">[sys.availability_replicas](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) 目錄檢視不應傳回任何資料列。</span><span class="sxs-lookup"><span data-stu-id="32bf2-121">The [sys.availability_replicas](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) catalog view should not return any rows.</span></span>  
  
     <span data-ttu-id="32bf2-122">如果伺服器執行個體上有任何可用性複本存在，您必須先執行下列其中一項操作，才能變更 HADR 叢集內容：</span><span class="sxs-lookup"><span data-stu-id="32bf2-122">If any availability replicas exist on the server instance, before you can change the HADR cluster context, you must do one of the following:</span></span>  
  
    |<span data-ttu-id="32bf2-123">複本角色</span><span class="sxs-lookup"><span data-stu-id="32bf2-123">Replica Role</span></span>|<span data-ttu-id="32bf2-124">動作</span><span class="sxs-lookup"><span data-stu-id="32bf2-124">Action</span></span>|<span data-ttu-id="32bf2-125">連結</span><span class="sxs-lookup"><span data-stu-id="32bf2-125">Link</span></span>|  
    |------------------|------------|----------|  
    |<span data-ttu-id="32bf2-126">Primary</span><span class="sxs-lookup"><span data-stu-id="32bf2-126">Primary</span></span>|<span data-ttu-id="32bf2-127">讓可用性群組離線。</span><span class="sxs-lookup"><span data-stu-id="32bf2-127">Take the availability group offline.</span></span>|[<span data-ttu-id="32bf2-128">讓可用性群組離線 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="32bf2-128">Take an Availability Group Offline &#40;SQL Server&#41;</span></span>](../../take-an-availability-group-offline-sql-server.md)|  
    |<span data-ttu-id="32bf2-129">次要</span><span class="sxs-lookup"><span data-stu-id="32bf2-129">Secondary</span></span>|<span data-ttu-id="32bf2-130">從本身的可用性群組移除複本</span><span class="sxs-lookup"><span data-stu-id="32bf2-130">Remove the replica from its availability group</span></span>|[<span data-ttu-id="32bf2-131">將次要複本從可用性群組移除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="32bf2-131">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)|  
  
-   <span data-ttu-id="32bf2-132">所有同步認可複本都必須是 SYNCHRONIZED，您才能從遠端叢集切換至本機叢集。</span><span class="sxs-lookup"><span data-stu-id="32bf2-132">Before you can switch from a remote cluster to the local cluster, all synchronous-commit replicas must be SYNCHRONIZED.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="32bf2-133">建議</span><span class="sxs-lookup"><span data-stu-id="32bf2-133">Recommendations</span></span>  
  
-   <span data-ttu-id="32bf2-134">我們建議您指定完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="32bf2-134">We recommend that you specify the full domain name.</span></span> <span data-ttu-id="32bf2-135">這是因為，為了尋找簡短名稱的目標 IP 位址，ALTER SERVER CONFIGURATION 會使用 DNS 解析。</span><span class="sxs-lookup"><span data-stu-id="32bf2-135">This is because to find the target IP address of a short name, ALTER SERVER CONFIGURATION uses DNS resolution.</span></span> <span data-ttu-id="32bf2-136">在某些情況下，根據 DNS 搜尋順序，使用簡短名稱可能會產生混淆。</span><span class="sxs-lookup"><span data-stu-id="32bf2-136">Under some situations, depending on the DNS searching order, using a short name could cause confusion.</span></span> <span data-ttu-id="32bf2-137">例如，請考慮下列命令，該命令是在 `abc` 網域 (`node1.abc.com`) 中的節點上執行。</span><span class="sxs-lookup"><span data-stu-id="32bf2-137">For example, consider the following command, which is executed on a node in the `abc` domain, (`node1.abc.com`).</span></span> <span data-ttu-id="32bf2-138">預期的目的地叢集是 `CLUS01` 網域 ( `xyz` ) 中的`clus01.xyz.com`叢集。</span><span class="sxs-lookup"><span data-stu-id="32bf2-138">The intended destination cluster is the `CLUS01` cluster in the `xyz` domain (`clus01.xyz.com`).</span></span> <span data-ttu-id="32bf2-139">不過，本機網域主機也會裝載名為 `CLUS01` (`clus01.abc.com`) 的叢集。</span><span class="sxs-lookup"><span data-stu-id="32bf2-139">However, the local  domain hosts also hosts a cluster named `CLUS01` (`clus01.abc.com`).</span></span>  
  
     <span data-ttu-id="32bf2-140">如果已指定目標叢集的簡短名稱 `CLUS01`，則 DNS 名稱解析可能會傳回錯誤叢集 `clus01.abc.com`的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="32bf2-140">If the short name of the target cluster, `CLUS01`, were specified, DNS name resolution could return the IP address of the wrong cluster, `clus01.abc.com`.</span></span> <span data-ttu-id="32bf2-141">為避免發生這類混淆情況，請指定目標叢集的完整名稱，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="32bf2-141">To avoid such confusion, specify the full name of the target cluster, as in the following example:</span></span>  
  
    ```  
    ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = 'clus01.xyz.com'  
    ```  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="32bf2-142">Security</span><span class="sxs-lookup"><span data-stu-id="32bf2-142">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="32bf2-143">權限</span><span class="sxs-lookup"><span data-stu-id="32bf2-143">Permissions</span></span>  
  
-   <span data-ttu-id="32bf2-144">**SQL Server 登入**</span><span class="sxs-lookup"><span data-stu-id="32bf2-144">**SQL Server login**</span></span>  
  
     <span data-ttu-id="32bf2-145">需要 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="32bf2-145">Requires CONTROL SERVER permission.</span></span>  
  
-   <span data-ttu-id="32bf2-146">**SQL Server 服務帳戶**</span><span class="sxs-lookup"><span data-stu-id="32bf2-146">**SQL Server service account**</span></span>  
  
     <span data-ttu-id="32bf2-147">伺服器執行個體的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務帳戶必須具備：</span><span class="sxs-lookup"><span data-stu-id="32bf2-147">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account of the server instance must have:</span></span>  
  
    -   <span data-ttu-id="32bf2-148">開啟目的地 WSFC 叢集的權限。</span><span class="sxs-lookup"><span data-stu-id="32bf2-148">Permission to open the destination WSFC cluster.</span></span>  
  
    -   <span data-ttu-id="32bf2-149">遠端 WSFC 讀寫存取。</span><span class="sxs-lookup"><span data-stu-id="32bf2-149">Remote WSFC read-write access.</span></span>  
  
 
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="32bf2-150">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="32bf2-150">Using Transact-SQL</span></span>  
 <span data-ttu-id="32bf2-151">**變更可用性複本的 WSFC 叢集內容**</span><span class="sxs-lookup"><span data-stu-id="32bf2-151">**To change the WSFC cluster context of an availability replica**</span></span>  
  
1.  <span data-ttu-id="32bf2-152">連接到裝載可用性群組之主要複本或次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="32bf2-152">Connect to the server instance that hosts either the primary replica or a secondary replica of the availability group.</span></span>  
  
2.  <span data-ttu-id="32bf2-153">使用 [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql) 陳述式的 SET HADR CLUSTER CONTEXT 子句，如下所示：</span><span class="sxs-lookup"><span data-stu-id="32bf2-153">Use the SET HADR CLUSTER CONTEXT clause of the [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="32bf2-154">ALTER SERVER CONFIGURATION SET HADR 叢集內容 **=** { **' *`windows_cluster`* '** |本機</span><span class="sxs-lookup"><span data-stu-id="32bf2-154">ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT **=** { **'*`windows_cluster`*'** | LOCAL }</span></span>  
  
     <span data-ttu-id="32bf2-155">其中</span><span class="sxs-lookup"><span data-stu-id="32bf2-155">where,</span></span>  
  
     <span data-ttu-id="32bf2-156">*windows_cluster*</span><span class="sxs-lookup"><span data-stu-id="32bf2-156">*windows_cluster*</span></span>  
     <span data-ttu-id="32bf2-157">WSFC 叢集的叢集物件名稱 (CON)。</span><span class="sxs-lookup"><span data-stu-id="32bf2-157">The cluster object name (CON) of a WSFC cluster.</span></span> <span data-ttu-id="32bf2-158">您可以指定簡短名稱或完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="32bf2-158">You can specify either the short name or the full domain name.</span></span> <span data-ttu-id="32bf2-159">我們建議您指定完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="32bf2-159">We recommend that you specify the full domain name.</span></span> <span data-ttu-id="32bf2-160">如需詳細資訊，請參閱本主題稍早的[建議](#Recommendations)。</span><span class="sxs-lookup"><span data-stu-id="32bf2-160">For more information, see [Recommendations](#Recommendations), earlier in this topic.</span></span>  
  
     <span data-ttu-id="32bf2-161">LOCAL</span><span class="sxs-lookup"><span data-stu-id="32bf2-161">LOCAL</span></span>  
     <span data-ttu-id="32bf2-162">本機 WSFC 叢集。</span><span class="sxs-lookup"><span data-stu-id="32bf2-162">The local WSFC cluster.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="32bf2-163">範例</span><span class="sxs-lookup"><span data-stu-id="32bf2-163">Examples</span></span>  
 <span data-ttu-id="32bf2-164">下列範例會將 HADR 叢集內容變更為不同叢集。</span><span class="sxs-lookup"><span data-stu-id="32bf2-164">The following example changes the HADR cluster context to a different cluster.</span></span> <span data-ttu-id="32bf2-165">為了識別目的地 WSFC 叢集 `clus01`，此範例會指定完整叢集物件名稱 `clus01.xyz.com`。</span><span class="sxs-lookup"><span data-stu-id="32bf2-165">To identify the destination WSFC cluster, `clus01`, the example specifies the full cluster object name, `clus01.xyz.com`.</span></span>  
  
```  
ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = 'clus01.xyz.com';  
```  
  
 <span data-ttu-id="32bf2-166">下列範例會將 HADR 叢集內容變更為本機 WSFC 叢集。</span><span class="sxs-lookup"><span data-stu-id="32bf2-166">The following example changes the HADR cluster context to the local WSFC cluster.</span></span>  
  
```  
ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = LOCAL;  
```  
  

  
##  <a name="follow-up-after-switching-the-cluster-context-of-an-availability-replica"></a><a name="FollowUp"></a> <span data-ttu-id="32bf2-167">後續操作：切換可用性複本的叢集內容之後</span><span class="sxs-lookup"><span data-stu-id="32bf2-167">Follow Up: After Switching the Cluster Context of an Availability Replica</span></span>  
 <span data-ttu-id="32bf2-168">新的 HADR 叢集內容會立即生效，不需要重新啟動伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="32bf2-168">The new HADR cluster context takes effect immediately, without restarting the server instance.</span></span> <span data-ttu-id="32bf2-169">HADR 叢集內容設定是持續性的執行個體層級設定，即使伺服器執行個體重新啟動也會保持不變。</span><span class="sxs-lookup"><span data-stu-id="32bf2-169">The HADR cluster context setting is a persistent instance-level setting that remains unchanged if the server instance restarts.</span></span>  
  
 <span data-ttu-id="32bf2-170">藉由查詢 [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql) 動態管理檢視確認新的 HADR 叢集內容，如下所示：</span><span class="sxs-lookup"><span data-stu-id="32bf2-170">Confirm the new HADR cluster context by querying the [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql) dynamic management view, as follows:</span></span>  
  
```  
SELECT cluster_name FROM sys.dm_hadr_cluster  
```  
  
 <span data-ttu-id="32bf2-171">此查詢應該會傳回您設定其 HADR 叢集內容之叢集的名稱。</span><span class="sxs-lookup"><span data-stu-id="32bf2-171">This query should return the name of the cluster to which you set the HADR cluster context.</span></span>  
  
 <span data-ttu-id="32bf2-172">當 HADR 叢集內容切換至新的叢集時：</span><span class="sxs-lookup"><span data-stu-id="32bf2-172">When the HADR cluster context is switched to a new cluster:</span></span>  
  
-   <span data-ttu-id="32bf2-173">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體目前裝載的任何可用性複本的中繼資料都會清除。</span><span class="sxs-lookup"><span data-stu-id="32bf2-173">The metadata is cleaned up for any availability replicas that are currently hosted by the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="32bf2-174">之前屬於某個可用性複本的所有資料庫現在都會是 RESTORING 狀態。</span><span class="sxs-lookup"><span data-stu-id="32bf2-174">All the databases that previously belonged to an availability replica are now in the RESTORING state.</span></span>  
  
 
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="32bf2-175">相關工作</span><span class="sxs-lookup"><span data-stu-id="32bf2-175">Related Tasks</span></span>  
  
-   [<span data-ttu-id="32bf2-176">移除可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="32bf2-176">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](remove-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="32bf2-177">讓可用性群組離線 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="32bf2-177">Take an Availability Group Offline &#40;SQL Server&#41;</span></span>](../../take-an-availability-group-offline-sql-server.md)  
  
-   [<span data-ttu-id="32bf2-178">將次要複本加入至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="32bf2-178">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="32bf2-179">將次要複本從可用性群組移除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="32bf2-179">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="32bf2-180">建立或設定可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="32bf2-180">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="32bf2-181">將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="32bf2-181">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
 
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="32bf2-182">相關內容</span><span class="sxs-lookup"><span data-stu-id="32bf2-182">Related Content</span></span>  
  
-   <span data-ttu-id="32bf2-183">[SQL Server 2012 技術文件](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="32bf2-183">[SQL Server 2012 Technical Articles](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="32bf2-184">SQL Server AlwaysOn 團隊部落格：官方 SQL Server AlwaysOn 團隊部落格</span><span class="sxs-lookup"><span data-stu-id="32bf2-184">SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
  
  
## <a name="see-also"></a><span data-ttu-id="32bf2-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32bf2-185">See Also</span></span>  
 <span data-ttu-id="32bf2-186">使用 &#40;[AlwaysOn 可用性群組 (SQL Server) ](always-on-availability-groups-sql-server.md) [Windows Server 容錯移轉叢集&#41; WSFC SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="32bf2-186">[AlwaysOn Availability Groups (SQL Server)](always-on-availability-groups-sql-server.md) [Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span></span>  
 [<span data-ttu-id="32bf2-187">ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="32bf2-187">ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-server-configuration-transact-sql)  
  
  
