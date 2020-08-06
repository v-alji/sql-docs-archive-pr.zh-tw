---
title: 具有 AlwaysOn 可用性群組 (SQL Server) 的 Service Broker |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Service Broker, AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 881c20e5-1c99-44eb-b393-09fc5ea0f122
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da179219363422c4ec242d29be61f35dd1609823
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596286"
---
# <a name="service-broker-with-alwayson-availability-groups-sql-server"></a><span data-ttu-id="2b768-102">Service Broker 與 AlwaysOn 可用性群組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2b768-102">Service Broker with AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="2b768-103">本主題包含將 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] Service Broker 設定為使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2b768-103">This topic contains information about configuring Service Broker to work with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="2b768-104">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="2b768-104">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="2b768-105">可用性群組中服務接收遠端訊息的需求</span><span class="sxs-lookup"><span data-stu-id="2b768-105">Requirements for a Service in an Availability Group to Receive Remote Messages</span></span>](#ReceiveRemoteMessages)  
  
-   [<span data-ttu-id="2b768-106">將訊息傳送至可用性群組中之遠端服務的需求</span><span class="sxs-lookup"><span data-stu-id="2b768-106">Requirements for Sending Messages to a Remote Service in an Availability Group</span></span>](#SendRemoteMessages)  
  
##  <a name="requirements-for-a-service-in-an-availability-group-to-receive-remote-messages"></a><a name="ReceiveRemoteMessages"></a> <span data-ttu-id="2b768-107">讓可用性群組中之服務接收遠端訊息的需求</span><span class="sxs-lookup"><span data-stu-id="2b768-107">Requirements for a Service in an Availability Group to Receive Remote Messages</span></span>  
  
1.  <span data-ttu-id="2b768-108">**確定可用性群組擁有接聽程式。**</span><span class="sxs-lookup"><span data-stu-id="2b768-108">**Ensure that the availability group possesses a listener.**</span></span>  
  
     <span data-ttu-id="2b768-109">如需詳細資訊，請參閱 [建立或設定可用性群組接聽程式 &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2b768-109">For more information, see [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="2b768-110">**確定 Service Broker 端點存在而且設定正確。**</span><span class="sxs-lookup"><span data-stu-id="2b768-110">**Ensure that the Service Broker endpoint exists and is correctly configured.**</span></span>  
  
     <span data-ttu-id="2b768-111">在裝載可用性群組之可用性複本的每個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體上，依照下列方式設定 Service Broker 端點：</span><span class="sxs-lookup"><span data-stu-id="2b768-111">On every instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts an availability replica for the availability group, configure the Service Broker endpoint, as follows:</span></span>  
  
    -   <span data-ttu-id="2b768-112">將 LISTENER_IP 設定為 'ALL'。</span><span class="sxs-lookup"><span data-stu-id="2b768-112">Set LISTENER_IP to 'ALL'.</span></span> <span data-ttu-id="2b768-113">這項設定會針對繫結至可用性群組接聽程式的任何有效 IP 位址啟用連接。</span><span class="sxs-lookup"><span data-stu-id="2b768-113">This setting enables connections on any valid IP address that is bound to the availability group listener.</span></span>  
  
    -   <span data-ttu-id="2b768-114">將所有主機伺服器執行個體的 Service Broker PORT 設定為相同的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="2b768-114">Set the Service Broker PORT to the same port number on all the host server instances.</span></span>  
  
        > [!TIP]  
        >  <span data-ttu-id="2b768-115">若要檢視指定伺服器執行個體之 Service Broker 端點的通訊埠編號，請查詢 **sys.tcp_endpoints** 目錄檢視的 [port](/sql/relational-databases/system-catalog-views/sys-tcp-endpoints-transact-sql) 資料行，其中 **type_desc** = 'SERVICE_BROKER'。</span><span class="sxs-lookup"><span data-stu-id="2b768-115">To view the port number of the Service Broker endpoint on a given server instance, query the **port** column of the [sys.tcp_endpoints](/sql/relational-databases/system-catalog-views/sys-tcp-endpoints-transact-sql) catalog view, where **type_desc** = 'SERVICE_BROKER'.</span></span>  
  
     <span data-ttu-id="2b768-116">下列範例會建立使用預設 Service Broker 通訊埠 (4022) 並且接聽所有有效 IP 位址的 Windows 驗證 Service Broker 端點。</span><span class="sxs-lookup"><span data-stu-id="2b768-116">The following example creates a Windows authenticated Service Broker endpoint that uses the default Service Broker port (4022) and listens to all valid IP addresses.</span></span>  
  
    ```  
    CREATE ENDPOINT [SSBEndpoint]  
        STATE = STARTED  
        AS TCP  (LISTENER_PORT = 4022, LISTENER_IP = ALL )  
        FOR SERVICE_BROKER (AUTHENTICATION = WINDOWS)  
    ```  
  
     <span data-ttu-id="2b768-117">如需詳細資訊，請參閱 [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2b768-117">For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
3.  <span data-ttu-id="2b768-118">**授與端點的 CONNECT 權限。**</span><span class="sxs-lookup"><span data-stu-id="2b768-118">**Grant CONNECT permission on the endpoint.**</span></span>  
  
     <span data-ttu-id="2b768-119">將 Service Broker 端點的 CONNECT 權限授與 PUBLIC 或登入。</span><span class="sxs-lookup"><span data-stu-id="2b768-119">Grant CONNECT permission on the Service Broker endpoint either to PUBLIC or to a login.</span></span>  
  
     <span data-ttu-id="2b768-120">下列範例會將名為 `broker_endpoint` 之 Service Broker 端點的連接授與 PUBLIC。</span><span class="sxs-lookup"><span data-stu-id="2b768-120">The following example grants the connection on a Service Broker endpoint named `broker_endpoint` to PUBLIC.</span></span>  
  
    ```  
    GRANT CONNECT ON ENDPOINT::[broker_endpoint] TO [PUBLIC]  
    ```  
  
     <span data-ttu-id="2b768-121">如需詳細資訊，請參閱 [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2b768-121">For more information, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).</span></span>  
  
4.  <span data-ttu-id="2b768-122">**確定 msdb 包含 AutoCreatedLocal 路由或特定服務的路由。**</span><span class="sxs-lookup"><span data-stu-id="2b768-122">**Ensure that msdb contains either an AutoCreatedLocal route or a route to the specific service.**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2b768-123">根據預設，每個使用者資料庫 (包括 **msdb**) 都包含 **AutoCreatedLocal**路由。</span><span class="sxs-lookup"><span data-stu-id="2b768-123">By default, each user database, including **msdb**, contains the route **AutoCreatedLocal**.</span></span> <span data-ttu-id="2b768-124">此路由會比對所有服務名稱和 Broker 執行個體，並指定訊息應在目前執行個體內傳遞。</span><span class="sxs-lookup"><span data-stu-id="2b768-124">This route matches any service name and broker instance and specifies that the message should be delivered within the current instance.</span></span> <span data-ttu-id="2b768-125">**AutoCreatedLocal** 的優先權低於明確指定與遠端執行個體通訊之特定服務的路由。</span><span class="sxs-lookup"><span data-stu-id="2b768-125">**AutoCreatedLocal** has lower priority than routes that explicitly specify a specific service that communicates with a remote instance.</span></span>  
  
     <span data-ttu-id="2b768-126">如需建立路由的相關資訊，請參閱 [Service Broker 路由範例](https://msdn.microsoft.com/library/ms166090\(SQL.105\).aspx) (在 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 版本的《線上叢書》中) 和 [CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql)的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2b768-126">For information about creating routes, see [Service Broker Routing Examples](https://msdn.microsoft.com/library/ms166090\(SQL.105\).aspx) (in the [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] version of Books Online) and [CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql).</span></span>  
  
##  <a name="requirements-for-sending-messages-to-a-remote-service-in-an-availability-group"></a><a name="SendRemoteMessages"></a> <span data-ttu-id="2b768-127">將訊息傳送至可用性群組中之遠端服務的需求</span><span class="sxs-lookup"><span data-stu-id="2b768-127">Requirements for Sending Messages to a Remote Service in an Availability Group</span></span>  
  
1.  <span data-ttu-id="2b768-128">**建立目標服務的路由。**</span><span class="sxs-lookup"><span data-stu-id="2b768-128">**Create a route to the target service.**</span></span>  
  
     <span data-ttu-id="2b768-129">依照下列方式設定路由：</span><span class="sxs-lookup"><span data-stu-id="2b768-129">Configure the route as follows:</span></span>  
  
    -   <span data-ttu-id="2b768-130">將 ADDRESS 設定為裝載服務資料庫之可用性群組的接聽程式 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="2b768-130">Set ADDRESS to the listener IP address of availability group that hosts the service database.</span></span>  
  
    -   <span data-ttu-id="2b768-131">將 PORT 設定為您在每個遠端 SQL Server 執行個體之 Service Broker 端點中指定的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="2b768-131">Set PORT to the port that you specified in the Service Broker endpoint of each of the remote SQL Server instances.</span></span>  
  
     <span data-ttu-id="2b768-132">下列範例會針對 `RouteToTargetService` 服務建立名為 `ISBNLookupRequestService` 的路由。</span><span class="sxs-lookup"><span data-stu-id="2b768-132">The following example creates a route named `RouteToTargetService` for the `ISBNLookupRequestService` service.</span></span> <span data-ttu-id="2b768-133">此路由會以使用通訊埠 4022 的可用性群組接聽程式 `MyAgListener`做為目標。</span><span class="sxs-lookup"><span data-stu-id="2b768-133">The route targets the availability group listener, `MyAgListener`, which uses port 4022.</span></span>  
  
    ```  
    CREATE ROUTE [RouteToTargetService] WITH   
    SERVICE_NAME = 'ISBNLookupRequestService',   
    ADDRESS = 'TCP://MyAgListener:4022';  
  
    ```  
  
     <span data-ttu-id="2b768-134">如需詳細資訊，請參閱 [CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql)的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2b768-134">For more information, see [CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql).</span></span>  
  
2.  <span data-ttu-id="2b768-135">**確定 msdb 包含 AutoCreatedLocal 路由或特定服務的路由。**</span><span class="sxs-lookup"><span data-stu-id="2b768-135">**Ensure that msdb contains either an AutoCreatedLocal route or a route to the specific service.**</span></span> <span data-ttu-id="2b768-136">(如需詳細資訊，請參閱本主題稍早的 [讓可用性群組中之服務接收遠端訊息的需求](#ReceiveRemoteMessages)。)</span><span class="sxs-lookup"><span data-stu-id="2b768-136">(For more information, see [Requirements for a Service in an Availability Group to Receive Remote Messages](#ReceiveRemoteMessages), earlier in this topic.)</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="2b768-137">相關工作</span><span class="sxs-lookup"><span data-stu-id="2b768-137">Related Tasks</span></span>  
  
-   [<span data-ttu-id="2b768-138">CREATE ENDPOINT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2b768-138">CREATE ENDPOINT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-endpoint-transact-sql)  
  
-   [<span data-ttu-id="2b768-139">CREATE ROUTE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2b768-139">CREATE ROUTE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-route-transact-sql)  
  
-   [<span data-ttu-id="2b768-140">GRANT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2b768-140">GRANT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/grant-transact-sql)  
  
-   <span data-ttu-id="2b768-141">[建立或設定可用性群組接聽程式 &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2b768-141">[Create or Configure an Availability Group Listener &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).</span></span>  
  
-   [<span data-ttu-id="2b768-142">建立及設定可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2b768-142">Creation and Configuration of Availability Groups &#40;SQL Server&#41;</span></span>](creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="2b768-143">設定資料庫鏡像的登入帳戶，或 AlwaysOn 可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2b768-143">Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](../../database-mirroring/set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
## <a name="see-also"></a><span data-ttu-id="2b768-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b768-144">See Also</span></span>  
 <span data-ttu-id="2b768-145">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2b768-145">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="2b768-146">[可用性群組接聽程式、用戶端連接性及應用程式容錯移轉 &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="2b768-146">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 [<span data-ttu-id="2b768-147">SQL Server Service Broker</span><span class="sxs-lookup"><span data-stu-id="2b768-147">SQL Server Service Broker</span></span>](../../configure-windows/sql-server-service-broker.md)  
  
  
