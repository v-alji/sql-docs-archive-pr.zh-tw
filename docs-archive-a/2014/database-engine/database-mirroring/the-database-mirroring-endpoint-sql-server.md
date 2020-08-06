---
title: 資料庫鏡像端點 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- database mirroring [SQL Server], endpoint
- endpoints [SQL Server], AlwaysOn Availability Groups
- endpoints [SQL Server], database mirroring
- Availability Groups [SQL Server], endpoint
ms.assetid: 39332dc5-678e-4650-9217-6aa3cdc41635
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5d9728ad642d978378305a21de4b6a9db068c397
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607068"
---
# <a name="the-database-mirroring-endpoint-sql-server"></a><span data-ttu-id="e9f34-102">資料庫鏡像端點 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e9f34-102">The Database Mirroring Endpoint (SQL Server)</span></span>
  <span data-ttu-id="e9f34-103">若要參與 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 或資料庫鏡像，伺服器執行個體就需要有自己專用的 *「資料庫鏡像端點」* (Database Mirroring Endpoint)。</span><span class="sxs-lookup"><span data-stu-id="e9f34-103">To participate in [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] or database mirroring a server instance requires its own, dedicated *database mirroring endpoint*.</span></span> <span data-ttu-id="e9f34-104">這個端點是特殊目的之端點，專門用來接收其他伺服器執行個體的連接。</span><span class="sxs-lookup"><span data-stu-id="e9f34-104">This endpoint is a special-purpose endpoint that is used exclusively to receive connections from other server instances.</span></span> <span data-ttu-id="e9f34-105">在給定的伺服器執行個體上，任何其他伺服器執行個體的每個 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 或資料庫鏡像連接都需要一個資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="e9f34-105">On a given server instance, every [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] or database mirroring connection to any other server instance uses a single database mirroring endpoint.</span></span>  
  
 <span data-ttu-id="e9f34-106">資料庫鏡像端點使用「傳輸控制通訊協定」(TCP)，在參與資料庫鏡像工作階段或裝載可用性複本的伺服器執行個體之間傳送和接收訊息。</span><span class="sxs-lookup"><span data-stu-id="e9f34-106">Database mirroring endpoints use Transmission Control Protocol (TCP) to send and receive messages between the server instances participating database mirroring sessions or hosting availability replicas.</span></span> <span data-ttu-id="e9f34-107">資料庫鏡像端點會在唯一的 TCP 通訊埠編號上接聽。</span><span class="sxs-lookup"><span data-stu-id="e9f34-107">The database mirroring endpoint listens on a unique TCP port number.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e9f34-108">主體伺服器或主要複本的用戶端連接不會使用資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="e9f34-108">Client connections to a principal server or primary replica do not use the database mirroring endpoint.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e9f34-109">未來的 Microsoft SQL Server 版本將移除資料庫鏡像功能。</span><span class="sxs-lookup"><span data-stu-id="e9f34-109">The database mirroring feature will be removed in a future version of Microsoft SQL Server.</span></span> <span data-ttu-id="e9f34-110">請避免在新的開發工作中使用這項功能，並規劃將目前使用資料庫鏡像的應用程式修改為使用 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e9f34-110">Avoid using this feature in new development work, and plan to modify applications that currently use database mirroring to use [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] instead.</span></span>  
  
  
##  <a name="server-network-address"></a><a name="ServerNetworkAddress"></a> <span data-ttu-id="e9f34-111">伺服器網路位址</span><span class="sxs-lookup"><span data-stu-id="e9f34-111">Server Network Address</span></span>  
 <span data-ttu-id="e9f34-112">伺服器執行個體的網路位址 (其「伺服器網路位址」或「端點 URL」) 包含其端點的通訊埠編號，以及其主機電腦的系統和網域名稱。</span><span class="sxs-lookup"><span data-stu-id="e9f34-112">The network address of a server instance (its *server network address* or *Endpoint URL*) contains the port number of its endpoint, as well as the system and domain name of its host computer.</span></span> <span data-ttu-id="e9f34-113">通訊埠編號會唯一識別特定伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="e9f34-113">The port number uniquely identifies a specific server instance.</span></span>  
  
 <span data-ttu-id="e9f34-114">下圖說明如何唯一識別相同伺服器上的兩個伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="e9f34-114">The following figure illustrates how two server instances on the same server are uniquely identified.</span></span> <span data-ttu-id="e9f34-115">這兩個伺服器執行個體的伺服器網路位址包含相同的系統名稱 `MYSYSTEM`和網域名稱 `Adventure-Works.MyDomain.com`。</span><span class="sxs-lookup"><span data-stu-id="e9f34-115">The server network addresses of both server instances contain the same system name, `MYSYSTEM`, and domain name, `Adventure-Works.MyDomain.com`.</span></span> <span data-ttu-id="e9f34-116">若要讓系統將連接傳送到伺服器執行個體，伺服器網路位址會包含與特定伺服器執行個體之鏡像端點相關聯的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="e9f34-116">To enable the system to route connections to a server instance, a server network address includes the port number associated with the mirroring endpoint of a particular server instance.</span></span>  
  
 <span data-ttu-id="e9f34-117">![預設執行個體的伺服器網路位址](../media/dbm-2-instances-ports-1-system.gif "預設執行個體的伺服器網路位址")</span><span class="sxs-lookup"><span data-stu-id="e9f34-117">![Server network addresses of a default instance](../media/dbm-2-instances-ports-1-system.gif "Server network addresses of a default instance")</span></span>  
  
 <span data-ttu-id="e9f34-118">依預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體不包含資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="e9f34-118">By default, an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not contain a database mirroring endpoint.</span></span> <span data-ttu-id="e9f34-119">設定資料庫鏡像工作階段時，必須以手動方式建立這些資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="e9f34-119">These must be created manually as part of setting up a database mirroring session.</span></span> <span data-ttu-id="e9f34-120">系統管理員必須在參與資料庫鏡像的每個伺服器執行個體中建立不同的端點。</span><span class="sxs-lookup"><span data-stu-id="e9f34-120">The system administrator must create a separate endpoint in each server instance that is to participate in database mirroring.</span></span> <span data-ttu-id="e9f34-121">請注意，如果給定電腦上多個伺服器執行個體需要資料庫鏡像端點，請為每個端點指定不同的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="e9f34-121">Note that if more than one server instance on a given computer requires a database mirroring endpoint, specify a different port number for each endpoint.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e9f34-122">如果執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的電腦具有防火牆，此防火牆的組態必須允許端點中所指定的通訊埠同時使用內送和外送連接。</span><span class="sxs-lookup"><span data-stu-id="e9f34-122">If the computer running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has a firewall, the firewall configuration must allow both incoming and outgoing connections for the port specified in the endpoint.</span></span>  
  
 <span data-ttu-id="e9f34-123">對於資料庫鏡像和 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]，會在端點上設定驗證與加密。</span><span class="sxs-lookup"><span data-stu-id="e9f34-123">For database mirroring and [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], authentication and encryption are configured on the endpoint.</span></span> <span data-ttu-id="e9f34-124">如需詳細資訊，請參閱[資料庫鏡像的傳輸安全性和 AlwaysOn 可用性群組 &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f34-124">For more information, see [Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e9f34-125">請不要重新設定使用中資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="e9f34-125">Do not reconfigure an in-use database mirroring endpoint.</span></span> <span data-ttu-id="e9f34-126">伺服器執行個體會使用彼此的端點來了解其他系統的狀態。</span><span class="sxs-lookup"><span data-stu-id="e9f34-126">The server instances use each other's endpoints to learn the state of the other systems.</span></span> <span data-ttu-id="e9f34-127">如果端點重新設定，它可能會重新啟動，而這對其他伺服器執行個體可能會是一項錯誤。</span><span class="sxs-lookup"><span data-stu-id="e9f34-127">If the endpoint is reconfigured, it might restart, which can appear to be an error to the other server instances.</span></span> <span data-ttu-id="e9f34-128">對於自動容錯移轉模式，這點尤其重要，因為在這種模式中重新設定夥伴上的端點，可能會導致發生容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="e9f34-128">This is particularly important for automatic failover mode, in which reconfiguring the endpoint on a partner could cause a failover to occur.</span></span>  
  
  
##  <a name="determining-the-authentication-type-for-a-database-mirroring-endpoint"></a><a name="EndpointAuthenticationTypes"></a> <span data-ttu-id="e9f34-129">決定資料庫鏡像端點的驗證類型</span><span class="sxs-lookup"><span data-stu-id="e9f34-129">Determining the Authentication Type for a Database Mirroring Endpoint</span></span>  
 <span data-ttu-id="e9f34-130">請務必了解，伺服器執行個體的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶會決定可用於資料庫鏡像端點的驗證類型，如下：</span><span class="sxs-lookup"><span data-stu-id="e9f34-130">It is important to understand that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service accounts of your server instances determine what type of authentication you can use for your database mirroring endpoints, as follows:</span></span>  
  
-   <span data-ttu-id="e9f34-131">如果每個伺服器執行個體各自在網域服務帳戶下執行，您可以將 Windows 驗證用於資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="e9f34-131">If every server instance is running under a domain service account, you can use Windows Authentication for your database mirroring endpoints.</span></span> <span data-ttu-id="e9f34-132">如果所有伺服器執行個體是以相同的網域使用者帳戶執行，兩個 **master** 資料庫中都會自動存在正確的使用者登入。</span><span class="sxs-lookup"><span data-stu-id="e9f34-132">If all the server instances run as the same domain user account, the correct user logins exist automatically in both **master** databases.</span></span> <span data-ttu-id="e9f34-133">這樣可簡化可用性資料庫的安全性組態，建議您使用。</span><span class="sxs-lookup"><span data-stu-id="e9f34-133">This simplifies the security configuration for the availability databases and is recommended.</span></span>  
  
     <span data-ttu-id="e9f34-134">如果裝載可用性群組之可用性複本的任何伺服器執行個體是以不同的帳戶執行，則每一個帳戶的登入都必須在其他伺服器執行個體的 **master** 中建立。</span><span class="sxs-lookup"><span data-stu-id="e9f34-134">If any server instances that are hosting the availability replicas for an availability group run as different accounts, the login each account must be created in **master** on the other server instance.</span></span> <span data-ttu-id="e9f34-135">然後，該登入必須被授與 CONNECT 權限，才能連接到該伺服器執行個體的資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="e9f34-135">Then, that login must be granted CONNECT permissions to connect to the database mirroring endpoint of that server instance.</span></span> <span data-ttu-id="e9f34-136">如需詳細資訊，請[設定資料庫鏡像的登入帳戶或 AlwaysOn 可用性群組 &#40;SQL Server&#41;](set-up-login-accounts-database-mirroring-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f34-136">For more information, [Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](set-up-login-accounts-database-mirroring-always-on-availability.md).</span></span>  
  
     <span data-ttu-id="e9f34-137">如果您的伺服器執行個體使用 Windows 驗證，可透過 [!INCLUDE[tsql](../../includes/tsql-md.md)]、PowerShell 或新增可用性群組精靈來建立資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="e9f34-137">If your server instances use Windows Authentication, you can create database mirroring endpoints by using [!INCLUDE[tsql](../../includes/tsql-md.md)], PowerShell, or the New Availability Group Wizard.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e9f34-138">如果將要裝載可用性複本的伺服器執行個體缺少資料庫鏡像端點，新增可用性群組精靈會自動建立使用 Windows 驗證的資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="e9f34-138">If a server instance that is to host an availability replica lacks a database mirroring endpoint, the New Availability Group Wizard can automatically create a database mirroring endpoint that uses Windows Authentication.</span></span> <span data-ttu-id="e9f34-139">如需詳細資訊，請參閱[使用可用性群組精靈 &#40;SQL Server Management Studio&#41;](../availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f34-139">For more information, see [Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;](../availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="e9f34-140">如果有任何伺服器執行個體在內建帳戶之下執行 (例如本機系統、本機服務或網路服務，或是非網域帳戶)，您必須將憑證用於端點驗證。</span><span class="sxs-lookup"><span data-stu-id="e9f34-140">If any server instance is running under a built-in account, such as Local System, Local Service, or Network Service, or a nondomain account, you must use certificates for endpoint authentication.</span></span> <span data-ttu-id="e9f34-141">如果您要針對資料庫鏡像端點使用憑證，您的系統管理員必須設定每一個伺服器執行個體同時在傳出和傳入的連接上使用憑證。</span><span class="sxs-lookup"><span data-stu-id="e9f34-141">If you are using certificates for your database mirroring endpoints, your system administrator must configure each server instance to use certificates on both outbound and inbound connections.</span></span>  
  
     <span data-ttu-id="e9f34-142">沒有任何自動的方法可以設定使用憑證的資料庫鏡像安全性。</span><span class="sxs-lookup"><span data-stu-id="e9f34-142">There is no automated method for configuring database mirroring security using certificates.</span></span> <span data-ttu-id="e9f34-143">您將需要使用 CREATE ENDPOINT [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式或 `New-SqlHadrEndpoint` PowerShell 指令程式。</span><span class="sxs-lookup"><span data-stu-id="e9f34-143">You will need to use either CREATE ENDPOINT [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or the `New-SqlHadrEndpoint` PowerShell cmdlet.</span></span> <span data-ttu-id="e9f34-144">如需詳細資訊，請參閱 [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e9f34-144">For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span> <span data-ttu-id="e9f34-145">如需在伺服器實例上啟用憑證驗證的相關資訊，請參閱[使用資料庫鏡像端點的憑證 &#40;transact-sql&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f34-145">For information about enabling certificate authentication on a server instance, see [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).</span></span>  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="e9f34-146">相關工作</span><span class="sxs-lookup"><span data-stu-id="e9f34-146">Related Tasks</span></span>  

### <a name="to-configure-a-database-mirroring-endpoint"></a><span data-ttu-id="e9f34-147">若要設定資料庫鏡像端點</span><span class="sxs-lookup"><span data-stu-id="e9f34-147">To Configure a Database Mirroring Endpoint</span></span>
  
-   [<span data-ttu-id="e9f34-148">建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e9f34-148">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="e9f34-149">使用資料庫鏡像端點憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e9f34-149">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [<span data-ttu-id="e9f34-150">允許資料庫鏡像端點使用輸出連線的憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e9f34-150">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [<span data-ttu-id="e9f34-151">允許資料庫鏡像端點使用輸入連線的憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e9f34-151">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="e9f34-152">指定伺服器網路位址 &#40;資料庫鏡像&#41;</span><span class="sxs-lookup"><span data-stu-id="e9f34-152">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](specify-a-server-network-address-database-mirroring.md)  
  
-   [<span data-ttu-id="e9f34-153">在新增或修改可用性複本時指定端點 URL &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e9f34-153">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](../availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="e9f34-154">使用可用性群組精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="e9f34-154">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/sql-server-management-studio-ssms.md)  
  
 <span data-ttu-id="e9f34-155">**若要檢視有關資料庫鏡像端點的資訊**</span><span class="sxs-lookup"><span data-stu-id="e9f34-155">**To View Information About the Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="e9f34-156">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e9f34-156">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
  
## <a name="see-also"></a><span data-ttu-id="e9f34-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9f34-157">See Also</span></span>  
 <span data-ttu-id="e9f34-158">[資料庫鏡像和 AlwaysOn 可用性群組的傳輸安全性 &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="e9f34-158">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="e9f34-159">[為資料庫鏡像組態進行疑難排解 &#40;SQL Server&#41; &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e9f34-159">[Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md) </span></span>  
 <span data-ttu-id="e9f34-160">[dm_hadr_availability_replica_states &#40;Transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e9f34-160">[sys.dm_hadr_availability_replica_states &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql) </span></span>  
 [<span data-ttu-id="e9f34-161">sys.dm_db_mirroring_connections &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e9f34-161">sys.dm_db_mirroring_connections &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-connections)  
