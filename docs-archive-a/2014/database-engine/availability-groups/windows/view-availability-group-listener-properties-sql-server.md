---
title: 檢視可用性群組接聽程式屬性 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygrouplistenerproperties.general.f1
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
ms.assetid: aca0d016-3228-40b8-bdc3-285ed6d9b280
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ef7fe316394a030350ceb12a0d1b8e2d48ee1d34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585601"
---
# <a name="view-availability-group-listener-properties-sql-server"></a><span data-ttu-id="a806b-102">檢視可用性群組接聽程式屬性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a806b-102">View Availability Group Listener Properties (SQL Server)</span></span>
  <span data-ttu-id="a806b-103">此主題描述如何使用 *中的* 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 來檢視 AlwaysOn [!INCLUDE[tsql](../../../includes/tsql-md.md)] 「可用性群組接聽程式」 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)](Availability Group Listener) 的屬性。</span><span class="sxs-lookup"><span data-stu-id="a806b-103">This topic describes how to view the properties of an AlwaysOn *availability group listener* by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="a806b-104">**若要檢視接聽程式屬性，可使用下列項目：**</span><span class="sxs-lookup"><span data-stu-id="a806b-104">**To view listener properties, using:**</span></span>  
  
     [<span data-ttu-id="a806b-105">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a806b-105">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a806b-106">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a806b-106">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a806b-107">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a806b-107">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="a806b-108">**若要檢視接聽程式屬性**</span><span class="sxs-lookup"><span data-stu-id="a806b-108">**To view listener properties**</span></span>  
  
1.  <span data-ttu-id="a806b-109">在 [物件總管] 中，連接到裝載您想要檢視其接聽程式之可用性群組的任何可用性複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="a806b-109">In Object Explorer, connect to a server instance that hosts any availability replica of the availability group whose listener you want to view.</span></span> <span data-ttu-id="a806b-110">按一下伺服器名稱展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="a806b-110">Click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="a806b-111">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="a806b-111">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="a806b-112">展開可用性群組的節點，然後展開 **[可用性群組接聽程式]** 節點。</span><span class="sxs-lookup"><span data-stu-id="a806b-112">Expand the node of the availability group, and expand the **Availability Groups Listeners** node.</span></span>  
  
4.  <span data-ttu-id="a806b-113">以滑鼠右鍵按一下您想要檢視的接聽程式，然後選取 [屬性] 命令。</span><span class="sxs-lookup"><span data-stu-id="a806b-113">Right-click the listener that you want to view, and select the **Properties** command.</span></span>  
  
5.  <span data-ttu-id="a806b-114">這樣就會開啟 **[可用性群組接聽項屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a806b-114">This opens the **Availability Group Listener Properties** dialog box.</span></span> <span data-ttu-id="a806b-115">如需詳細資訊，請參閱本主題稍後的 [可用性群組接聽程式屬性 (對話方塊)](#AgListenerPropertiesDialog)。</span><span class="sxs-lookup"><span data-stu-id="a806b-115">For more information, see [Availability Group Listener Properties (Dialog Box)](#AgListenerPropertiesDialog), later in this topic.</span></span>  
  
###  <a name="availability-group-listener-properties-dialog-box"></a><a name="AgListenerPropertiesDialog"></a> <span data-ttu-id="a806b-116">可用性群組接聽程式屬性 (對話方塊)</span><span class="sxs-lookup"><span data-stu-id="a806b-116">Availability Group Listener Properties (Dialog Box)</span></span>  
 <span data-ttu-id="a806b-117">**接聽程式 DNS 名稱**</span><span class="sxs-lookup"><span data-stu-id="a806b-117">**Listener DNS Name**</span></span>  
 <span data-ttu-id="a806b-118">可用性群組接聽程式的網路名稱。</span><span class="sxs-lookup"><span data-stu-id="a806b-118">The network name of the availability group listener.</span></span>  
  
 <span data-ttu-id="a806b-119">**通訊埠**</span><span class="sxs-lookup"><span data-stu-id="a806b-119">**Port**</span></span>  
 <span data-ttu-id="a806b-120">此接聽程式所使用的 TCP 通訊埠。</span><span class="sxs-lookup"><span data-stu-id="a806b-120">The TCP port used by this listener.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a806b-121">如果您連接到主要複本，就可以使用此欄位來修改接聽程式的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="a806b-121">If you are connected the primary replica, you can use this field to modify the port number of the listener.</span></span> <span data-ttu-id="a806b-122">這項作業需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="a806b-122">This requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
 <span data-ttu-id="a806b-123">**網路模式**</span><span class="sxs-lookup"><span data-stu-id="a806b-123">**Network Mode**</span></span>  
 <span data-ttu-id="a806b-124">指出接聽程式所使用的 TCP 通訊協定，其中一個：</span><span class="sxs-lookup"><span data-stu-id="a806b-124">Indicates the TCP protocol used by the listener, one of:</span></span>  
  
 <span data-ttu-id="a806b-125">**DHCP**</span><span class="sxs-lookup"><span data-stu-id="a806b-125">**DHCP**</span></span>  
 <span data-ttu-id="a806b-126">接聽程式會使用執行動態主機設定通訊協定 (DHCP) 之伺服器所指派的動態 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="a806b-126">The listener uses an dynamic IP address that is assigned by a server running the Dynamic Host Configuration Protocol (DHCP).</span></span>  
  
 <span data-ttu-id="a806b-127">**靜態 IP**</span><span class="sxs-lookup"><span data-stu-id="a806b-127">**Static IP**</span></span>  
 <span data-ttu-id="a806b-128">接聽程式會使用一個或多個靜態 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="a806b-128">The listener uses one or more Static IP addresses.</span></span> <span data-ttu-id="a806b-129">若要存取不同的子網路，可用性群組接聽程式必須使用靜態 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="a806b-129">To access the different subnets, an availability group listener must use static IP addresses.</span></span>  
  
 <span data-ttu-id="a806b-130">此方格會顯示接聽程式所接聽的每個子網路，以及與該子網路相關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="a806b-130">The grid displays each of the subnets on which the listener listens and the IP address associated with that subnet.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a806b-131">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a806b-131">Using Transact-SQL</span></span>  
 <span data-ttu-id="a806b-132">**若要檢視接聽程式屬性**</span><span class="sxs-lookup"><span data-stu-id="a806b-132">**To view listener properties**</span></span>  
  
 <span data-ttu-id="a806b-133">若要監視可用性群組接聽程式，請使用下列檢視：</span><span class="sxs-lookup"><span data-stu-id="a806b-133">To monitor the availability group listeners, use the following views:</span></span>  
  
 [<span data-ttu-id="a806b-134">sys.availability_group_listener_ip_addresses</span><span class="sxs-lookup"><span data-stu-id="a806b-134">sys.availability_group_listener_ip_addresses</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listener-ip-addresses-transact-sql)  
 <span data-ttu-id="a806b-135">針對目前上線供可用性群組接聽程式使用的每個符合標準虛擬 IP 位址傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="a806b-135">Returns a row for every conformant virtual IP address that is currently online for an availability group listener.</span></span>  
  
 <span data-ttu-id="a806b-136">**資料行名稱** ：listener_id、ip_address、ip_subnet_mask、is_dhcp、network_subnet_ip、network_subnet_prefix_length、network_subnet_ipv4_mask、state、state_desc</span><span class="sxs-lookup"><span data-stu-id="a806b-136">**Column names:** listener_id, ip_address, ip_subnet_mask, is_dhcp, network_subnet_ip, network_subnet_prefix_length, network_subnet_ipv4_mask, state, state_desc</span></span>  
  
 [<span data-ttu-id="a806b-137">sys.availability_group_listeners</span><span class="sxs-lookup"><span data-stu-id="a806b-137">sys.availability_group_listeners</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listeners-transact-sql)  
 <span data-ttu-id="a806b-138">若為給定的可用性群組，傳回零個資料列，表示沒有網路名稱與可用性群組相關聯，或針對 WSFC 叢集中的每個可用性群組接聽程式組態傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="a806b-138">For a given availability group, returns either zero rows indicating that no network name is associated with the availability group, or returns a row for each availability-group listener configuration in the WSFC cluster.</span></span>  
  
 <span data-ttu-id="a806b-139">**資料行名稱** ：group_id、listener_id、dns_name、port、is_conformant、ip_configuration_string_from_cluster</span><span class="sxs-lookup"><span data-stu-id="a806b-139">**Column names:** group_id, listener_id, dns_name, port, is_conformant, ip_configuration_string_from_cluster</span></span>  
  
 [<span data-ttu-id="a806b-140">sys.dm_tcp_listener_states</span><span class="sxs-lookup"><span data-stu-id="a806b-140">sys.dm_tcp_listener_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql)  
 <span data-ttu-id="a806b-141">針對每個 TCP 接聽程式傳回一個包含動態狀態資訊的資料列。</span><span class="sxs-lookup"><span data-stu-id="a806b-141">Returns a row containing dynamic-state information for each TCP listener.</span></span>  
  
 <span data-ttu-id="a806b-142">**資料行名稱：** listener_id、ip_address、is_ipv4、port、type、type_desc、state、state_desc、start_time</span><span class="sxs-lookup"><span data-stu-id="a806b-142">**Column names:** listener_id, ip_address, is_ipv4, port, type, type_desc, state, state_desc, start_time</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a806b-143">如需使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 監視 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 環境的詳細資訊，請參閱 [監視可用性群組 &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md)(Availability Group Listener) 的屬性。</span><span class="sxs-lookup"><span data-stu-id="a806b-143">For more information about using [!INCLUDE[tsql](../../../includes/tsql-md.md)] to monitor your [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] environment, see [Monitor Availability Groups &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a806b-144">相關工作</span><span class="sxs-lookup"><span data-stu-id="a806b-144">Related Tasks</span></span>  
  
-   [<span data-ttu-id="a806b-145">建立或設定可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a806b-145">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="a806b-146">移除可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a806b-146">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](remove-an-availability-group-listener-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="a806b-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a806b-147">See Also</span></span>  
 <span data-ttu-id="a806b-148">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a806b-148">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="a806b-149">[可用性群組接聽程式、用戶端連接性及應用程式容錯移轉 &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="a806b-149">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 [<span data-ttu-id="a806b-150">監視可用性群組 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a806b-150">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
  
  
