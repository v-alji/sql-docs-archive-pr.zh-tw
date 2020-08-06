---
title: 針對資料庫鏡像組態進行疑難排解 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- endpoints [SQL Server], database mirroring
- database mirroring [SQL Server], troubleshooting
- troubleshooting [SQL Server], database mirroring
ms.assetid: 87d3801b-dc52-419e-9316-8b1f1490946c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0dafd98f721bfc2d2d0dd64a9f97689466529407
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594689"
---
# <a name="troubleshoot-database-mirroring-configuration-sql-server"></a><span data-ttu-id="ee560-102">疑難排解資料庫鏡像組態 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ee560-102">Troubleshoot Database Mirroring Configuration (SQL Server)</span></span>
  <span data-ttu-id="ee560-103">本主題提供資訊以協助您對設定資料庫鏡像工作階段的問題進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="ee560-103">This topic provides information to help you troubleshoot problems in setting up a database mirroring session.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ee560-104">確定您符合所有 [資料庫鏡像的必要條件](prerequisites-restrictions-and-recommendations-for-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="ee560-104">Ensure that you are meeting all the [prerequisites for database mirroring](prerequisites-restrictions-and-recommendations-for-database-mirroring.md).</span></span>  
  
|<span data-ttu-id="ee560-105">問題</span><span class="sxs-lookup"><span data-stu-id="ee560-105">Issue</span></span>|<span data-ttu-id="ee560-106">總結</span><span class="sxs-lookup"><span data-stu-id="ee560-106">Summary</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="ee560-107">錯誤訊息 1418</span><span class="sxs-lookup"><span data-stu-id="ee560-107">Error Message 1418</span></span>|<span data-ttu-id="ee560-108">此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 訊息指出無法連繫伺服器網路位址或該位址不存在，並建議您確認網路位址名稱，然後重新發出命令。</span><span class="sxs-lookup"><span data-stu-id="ee560-108">This [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] message indicates that the server network address cannot be reached or does not exist, and it suggests that you verify the network address name and reissue the command.</span></span> <span data-ttu-id="ee560-109">如需詳細資訊，請參閱 [MSSQLSERVER_1418](../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md) 主題。</span><span class="sxs-lookup"><span data-stu-id="ee560-109">For more information, see the [MSSQLSERVER_1418](../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md) topic.</span></span>|  
|[<span data-ttu-id="ee560-110">帳戶</span><span class="sxs-lookup"><span data-stu-id="ee560-110">Accounts</span></span>](#Accounts)|<span data-ttu-id="ee560-111">討論正確設定在底下執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之帳戶的需求。</span><span class="sxs-lookup"><span data-stu-id="ee560-111">Discusses requirements for correctly configuring the accounts under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>|  
|[<span data-ttu-id="ee560-112">端點</span><span class="sxs-lookup"><span data-stu-id="ee560-112">Endpoints</span></span>](#Endpoints)|<span data-ttu-id="ee560-113">討論正確設定每個伺服器執行個體之資料庫鏡像端點的需求。</span><span class="sxs-lookup"><span data-stu-id="ee560-113">Discusses requirements for correctly configuring the database mirroring endpoint of each server instance.</span></span>|  
|[<span data-ttu-id="ee560-114">系統位址</span><span class="sxs-lookup"><span data-stu-id="ee560-114">SystemAddress</span></span>](#SystemAddress)|<span data-ttu-id="ee560-115">摘要說明在資料庫鏡像組態中指定伺服器執行個體之系統名稱的替代方式。</span><span class="sxs-lookup"><span data-stu-id="ee560-115">Summarizes the alternatives for specifying the system name of a server instance in a database mirroring configuration.</span></span>|  
|[<span data-ttu-id="ee560-116">網路存取</span><span class="sxs-lookup"><span data-stu-id="ee560-116">Network access</span></span>](#NetworkAccess)|<span data-ttu-id="ee560-117">說明每個伺服器執行個體要透過 TCP 來存取其他伺服器執行個體之通訊埠的需求。</span><span class="sxs-lookup"><span data-stu-id="ee560-117">Documents the requirement that each the server instance be able to access the ports of the other server instance or instances over TCP.</span></span>|  
|[<span data-ttu-id="ee560-118">鏡像資料庫的準備工作</span><span class="sxs-lookup"><span data-stu-id="ee560-118">Mirror database preparation</span></span>](#MirrorDbPrep)|<span data-ttu-id="ee560-119">摘要說明準備鏡像資料庫以便開始進行鏡像作業的需求。</span><span class="sxs-lookup"><span data-stu-id="ee560-119">Summarizes the requirements for preparing the mirror database to enable mirroring to start.</span></span>|  
|[<span data-ttu-id="ee560-120">失敗的檔案建立作業</span><span class="sxs-lookup"><span data-stu-id="ee560-120">Failed create-file operation</span></span>](#FailedCreateFileOp)|<span data-ttu-id="ee560-121">描述如何回應失敗的檔案建立作業。</span><span class="sxs-lookup"><span data-stu-id="ee560-121">Describes how to respond to a failed create-file operation.</span></span>|  
|[<span data-ttu-id="ee560-122">使用 Transact-SQL 啟動鏡像</span><span class="sxs-lookup"><span data-stu-id="ee560-122">Starting mirroring by Using Transact-SQL</span></span>](#StartDbm)|<span data-ttu-id="ee560-123">描述 ALTER DATABASE *database_name* SET PARTNER **='***partner_server***'** 陳述式的必要順序。</span><span class="sxs-lookup"><span data-stu-id="ee560-123">Describes the required order for ALTER DATABASE *database_name* SET PARTNER **='***partner_server***'** statements.</span></span>|  
|[<span data-ttu-id="ee560-124">跨資料庫交易</span><span class="sxs-lookup"><span data-stu-id="ee560-124">Cross-Database Transactions</span></span>](#CrossDbTxns)|<span data-ttu-id="ee560-125">自動容錯移轉可能導致自動以及可能不正確地解決有疑問的交易。</span><span class="sxs-lookup"><span data-stu-id="ee560-125">An automatic failover could lead to automatic and possibly incorrect resolution of in-doubt transactions.</span></span> <span data-ttu-id="ee560-126">因此，資料庫鏡像不支援跨資料庫交易。</span><span class="sxs-lookup"><span data-stu-id="ee560-126">For this reason database mirroring does not support cross-database transactions.</span></span>|  
  
##  <a name="accounts"></a><a name="Accounts"></a> <span data-ttu-id="ee560-127">帳戶</span><span class="sxs-lookup"><span data-stu-id="ee560-127">Accounts</span></span>  
 <span data-ttu-id="ee560-128">必須正確設定用來執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的帳戶。</span><span class="sxs-lookup"><span data-stu-id="ee560-128">The accounts under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running must be correctly configured.</span></span>  
  
1.  <span data-ttu-id="ee560-129">帳戶有正確的權限嗎？</span><span class="sxs-lookup"><span data-stu-id="ee560-129">Do the accounts have the correct permissions?</span></span>  
  
    1.  <span data-ttu-id="ee560-130">如果帳戶是在相同的網域帳戶中執行，則錯誤設定的可能性較低。</span><span class="sxs-lookup"><span data-stu-id="ee560-130">If the accounts are running in the same domain accounts, the chances of misconfiguration are reduced.</span></span>  
  
    2.  <span data-ttu-id="ee560-131">如果帳戶是在不同的網域中執行，或不是網域帳戶，則必須在其他電腦的 **master** 中建立一個帳戶的登入，而且必須將端點的 CONNECT 權限授與該登入。</span><span class="sxs-lookup"><span data-stu-id="ee560-131">If the accounts are running in different domains or are not domain accounts, the login of one account must be created in **master** on the other computer, and that login must be granted CONNECT permissions on the endpoint.</span></span> <span data-ttu-id="ee560-132">如需詳細資訊，請參閱 [在另一個伺服器執行個體上提供可用的資料庫時，管理中繼資料 &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ee560-132">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).</span></span> <span data-ttu-id="ee560-133">這包括 Network Service 帳戶。</span><span class="sxs-lookup"><span data-stu-id="ee560-133">This includes the Network Service account.</span></span>  
  
2.  <span data-ttu-id="ee560-134">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用本機系統帳戶以服務的方式執行，您必須使用憑證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="ee560-134">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running as a service that is using the local system account, you must use certificates for authentication.</span></span> <span data-ttu-id="ee560-135">如需詳細資訊，請參閱[使用資料庫鏡像端點憑證 &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="ee560-135">For more information, see [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).</span></span>  
  
##  <a name="endpoints"></a><a name="Endpoints"></a> <span data-ttu-id="ee560-136">Endpoints</span><span class="sxs-lookup"><span data-stu-id="ee560-136">Endpoints</span></span>  
 <span data-ttu-id="ee560-137">必須正確設定端點。</span><span class="sxs-lookup"><span data-stu-id="ee560-137">Endpoints must be correctly configured.</span></span>  
  
1.  <span data-ttu-id="ee560-138">確定每個伺服器執行個體 (主體伺服器、鏡像伺服器和任何見證) 都有資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="ee560-138">Make sure that each server instance (the principal server, mirror server, and witness, if any) has a database mirroring endpoint.</span></span> <span data-ttu-id="ee560-139">如需詳細資訊，請參閱 [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) 以及[建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) 或[使用資料庫鏡像端點憑證 &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md) (根據驗證格式而定)。</span><span class="sxs-lookup"><span data-stu-id="ee560-139">For more information, see [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) and, depending on the form of authentication, either [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) or [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).</span></span>  
  
2.  <span data-ttu-id="ee560-140">檢查通訊埠編號是否正確。</span><span class="sxs-lookup"><span data-stu-id="ee560-140">Check that the port numbers are correct.</span></span>  
  
     <span data-ttu-id="ee560-141">若要識別目前與伺服器執行個體的資料庫鏡像端點相關聯的通訊埠，請使用 [sys.database_mirroring_endpoints](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) 和 [sys.tcp_endpoints](/sql/relational-databases/system-catalog-views/sys-tcp-endpoints-transact-sql) 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="ee560-141">To identify the port currently associated with database mirroring endpoint of a server instance, use the [sys.database_mirroring_endpoints](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) and [sys.tcp_endpoints](/sql/relational-databases/system-catalog-views/sys-tcp-endpoints-transact-sql) catalog views.</span></span>  
  
3.  <span data-ttu-id="ee560-142">對於難以解釋的資料庫鏡像設定問題，我們建議您檢查每個伺服器執行個體，以判斷它是否正在接聽正確的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="ee560-142">For database mirroring setup issues that are difficult to explain, we recommend that you inspect each server instance to determine whether it is listening on the correct ports.</span></span> <span data-ttu-id="ee560-143">如需驗證通訊埠可用性的相關資訊，請參閱 [MSSQLSERVER_1418](../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md)。</span><span class="sxs-lookup"><span data-stu-id="ee560-143">For information about verifying port availability, see [MSSQLSERVER_1418](../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md).</span></span>  
  
4.  <span data-ttu-id="ee560-144">確定端點已啟動 (STATE=STARTED)。</span><span class="sxs-lookup"><span data-stu-id="ee560-144">Make sure that the endpoints are started (STATE=STARTED).</span></span> <span data-ttu-id="ee560-145">在每個伺服器執行個體上，使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ee560-145">On each server instance, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
    ```  
    SELECT state_desc FROM sys.database_mirroring_endpoints  
    ```  
  
     <span data-ttu-id="ee560-146">如需 **state_desc** 資料行的詳細資訊，請參閱 [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ee560-146">For more information about the **state_desc** column, see [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql).</span></span>  
  
     <span data-ttu-id="ee560-147">若要啟動端點，請使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ee560-147">To start an endpoint, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
    ```  
    ALTER ENDPOINT Endpoint_Mirroring   
    STATE = STARTED   
    AS TCP (LISTENER_PORT = <port_number>)  
    FOR database_mirroring (ROLE = ALL);  
    GO  
    ```  
  
     <span data-ttu-id="ee560-148">如需詳細資訊，請參閱 [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ee560-148">For more information, see [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
5.  <span data-ttu-id="ee560-149">檢查 ROLE 是否正確。</span><span class="sxs-lookup"><span data-stu-id="ee560-149">Check that the ROLE is correct.</span></span> <span data-ttu-id="ee560-150">在每個伺服器執行個體上，使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ee560-150">On each server instance use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
    ```  
    SELECT role FROM sys.database_mirroring_endpoints;  
    GO  
    ```  
  
     <span data-ttu-id="ee560-151">如需詳細資訊，請參閱 [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ee560-151">For more information, see [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql).</span></span>  
  
6.  <span data-ttu-id="ee560-152">來自其他伺服器執行個體的服務帳戶登入需要 CONNECT 權限。</span><span class="sxs-lookup"><span data-stu-id="ee560-152">The login for the service account from the other server instance requires CONNECT permission.</span></span> <span data-ttu-id="ee560-153">確定來自其他伺服器的登入具有 CONNECT 權限。</span><span class="sxs-lookup"><span data-stu-id="ee560-153">Make sure that the login from the other server has CONNECT permission.</span></span> <span data-ttu-id="ee560-154">若要判斷誰具有端點的 CONNECT 權限，請在每個伺服器執行個體上使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ee560-154">To determine who has CONNECT permission for an endpoint, on each server instance use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
    ```  
    SELECT 'Metadata Check';  
    SELECT EP.name, SP.STATE,   
       CONVERT(nvarchar(38), suser_name(SP.grantor_principal_id))   
          AS GRANTOR,   
       SP.TYPE AS PERMISSION,  
       CONVERT(nvarchar(46),suser_name(SP.grantee_principal_id))   
          AS GRANTEE   
       FROM sys.server_permissions SP , sys.endpoints EP  
       WHERE SP.major_id = EP.endpoint_id  
       ORDER BY Permission,grantor, grantee;   
    GO  
  
    ```  
  
##  <a name="system-address"></a><a name="SystemAddress"></a> <span data-ttu-id="ee560-155">系統位址</span><span class="sxs-lookup"><span data-stu-id="ee560-155">System Address</span></span>  
 <span data-ttu-id="ee560-156">您可以使用能夠明確識別系統的任何名稱，來當做資料庫鏡像組態中伺服器執行個體的系統名稱。</span><span class="sxs-lookup"><span data-stu-id="ee560-156">For the system name of a server instance in a database mirroring configuration, you can use any name that unambiguously identifies the system.</span></span> <span data-ttu-id="ee560-157">伺服器位址可以是系統名稱 (如果系統位於同一個網域內)、完整網域名稱或 IP 位址 (最好是靜態 IP 位址)。</span><span class="sxs-lookup"><span data-stu-id="ee560-157">The server address can be a system name (if the systems are in the same domain), a fully qualified domain name, or an IP address (preferably, a static IP address).</span></span> <span data-ttu-id="ee560-158">使用完整網域名稱保證可以運作。</span><span class="sxs-lookup"><span data-stu-id="ee560-158">Using the fully qualified domain name is guaranteed to work.</span></span> <span data-ttu-id="ee560-159">如需詳細資訊，請參閱 [指定伺服器網路位址 &#40;資料庫鏡像&#41;](specify-a-server-network-address-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="ee560-159">For more information, see [Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md).</span></span>  
  
##  <a name="network-access"></a><a name="NetworkAccess"></a> <span data-ttu-id="ee560-160">Network Access</span><span class="sxs-lookup"><span data-stu-id="ee560-160">Network Access</span></span>  
 <span data-ttu-id="ee560-161">每個伺服器執行個體都必須能夠透過 TCP 來存取其他伺服器執行個體的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="ee560-161">Each server instance must be able to access the ports of the other server instance or instances over TCP.</span></span> <span data-ttu-id="ee560-162">如果伺服器執行個體位在互不信任的不同網域 (不受信任的網域) 中，這點尤其重要。</span><span class="sxs-lookup"><span data-stu-id="ee560-162">This is especially important if the server instances are in different domains that do not trust each other (untrusted domains).</span></span> <span data-ttu-id="ee560-163">因為這會限制伺服器執行個體之間的許多通訊。</span><span class="sxs-lookup"><span data-stu-id="ee560-163">This restricts much of the communication between the server instances.</span></span>  
  
##  <a name="mirror-database-preparation"></a><a name="MirrorDbPrep"></a> <span data-ttu-id="ee560-164">Mirror Database Preparation</span><span class="sxs-lookup"><span data-stu-id="ee560-164">Mirror Database Preparation</span></span>  
 <span data-ttu-id="ee560-165">不論您是第一次啟動鏡像或在移除鏡像後再次啟動鏡像，請確認已備妥鏡像資料庫，可進行鏡像作業。</span><span class="sxs-lookup"><span data-stu-id="ee560-165">Whether starting mirroring for the first time or starting it again after mirroring was removed, verify that the mirror database is prepared for mirroring.</span></span>  
  
 <span data-ttu-id="ee560-166">在鏡像伺服器上建立鏡像資料庫時，請確定您使用 WITH NORECOVERY 指定了相同的資料庫名稱來還原主體資料庫的備份。</span><span class="sxs-lookup"><span data-stu-id="ee560-166">When you create the mirror database on the mirror server, make sure that you restore the backup of the principal database specifying the same database name WITH NORECOVERY.</span></span> <span data-ttu-id="ee560-167">另外，您還必須使用 WITH NORECOVERY 套用製作該備份之後建立的所有記錄備份。</span><span class="sxs-lookup"><span data-stu-id="ee560-167">Also, all log backups created after that backup was taken must also be applied, again WITH NORECOVERY.</span></span>  
  
 <span data-ttu-id="ee560-168">另外，建議鏡像資料庫的檔案路徑 (包括磁碟機代號) 最好和主體資料庫的路徑完全相同。</span><span class="sxs-lookup"><span data-stu-id="ee560-168">Also, we recommend that, if it is possible, the file path (including the drive letter) of the mirror database be identical to the path of the principal database.</span></span> <span data-ttu-id="ee560-169">如果檔案路徑必須不同，例如，如果主體資料庫在磁碟機 'F:'，但鏡像系統沒有 F: 磁碟機，您就必須在 RESTORE 陳述式中包含 MOVE 選項。</span><span class="sxs-lookup"><span data-stu-id="ee560-169">If the file paths must differ, for example, if the principal database is on drive 'F:' but the mirror system lacks an F: drive, you must include the MOVE option in the RESTORE statement.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ee560-170">如果您在建立鏡像資料庫時移動資料庫檔案，那麼稍後若不暫停鏡像作業，可能就無法將檔案加入資料庫。</span><span class="sxs-lookup"><span data-stu-id="ee560-170">If you move the database files when you are creating the mirror database, you might be unable to add files to the database later without mirroring being suspended.</span></span>  
  
 <span data-ttu-id="ee560-171">如果資料庫鏡像已經停止，則必須先將在主體資料庫上製作的所有後續記錄備份套用到鏡像資料庫，然後才能重新啟動鏡像。</span><span class="sxs-lookup"><span data-stu-id="ee560-171">If database mirroring has been stopped, all subsequent log backups taken on the principal database must be applied to the mirror database before mirroring can be restarted.</span></span>  
  
 <span data-ttu-id="ee560-172">如需詳細資訊，請參閱 [準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ee560-172">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
##  <a name="failed-create-file-operation"></a><a name="FailedCreateFileOp"></a> <span data-ttu-id="ee560-173">Failed Create-File Operation</span><span class="sxs-lookup"><span data-stu-id="ee560-173">Failed Create-File Operation</span></span>  
 <span data-ttu-id="ee560-174">若要加入檔案但又不影響鏡像工作階段，則此檔案的路徑必須同時存在兩個伺服器上。</span><span class="sxs-lookup"><span data-stu-id="ee560-174">Adding a file without impacting a mirroring session requires that the path of the file exist on both servers.</span></span> <span data-ttu-id="ee560-175">因此，如果您在建立鏡像資料庫時移動資料庫檔案，之後在鏡像資料庫上加入檔案的作業可能會失敗，而且導致鏡像暫停。</span><span class="sxs-lookup"><span data-stu-id="ee560-175">Therefore, if you move the database files when creating the mirror database, a later add-file operation might fail on the mirror database and cause mirroring to be suspended.</span></span>  
  
 <span data-ttu-id="ee560-176">若要修正這個問題：</span><span class="sxs-lookup"><span data-stu-id="ee560-176">To fix the problem:</span></span>  
  
1.  <span data-ttu-id="ee560-177">資料庫擁有者必須移除鏡像工作階段，並且還原包含加入之檔案的檔案群組完整備份。</span><span class="sxs-lookup"><span data-stu-id="ee560-177">The database owner must remove the mirroring session and restore a full backup of the filegroup that contains the added file.</span></span>  
  
2.  <span data-ttu-id="ee560-178">然後，此擁有者必須在主體伺服器上備份包含加入檔案作業的記錄，並且使用 WITH NORECOVERY 和 WITH MOVE 選項來手動在鏡像資料庫上還原記錄備份。</span><span class="sxs-lookup"><span data-stu-id="ee560-178">The owner must then back up the log containing the add-file operation on the principal server and manually restore the log backup on the mirror database using the WITH NORECOVERY and WITH MOVE options.</span></span> <span data-ttu-id="ee560-179">這樣做會在鏡像伺服器上建立指定的檔案路徑，並且將新的檔案還原至該位置。</span><span class="sxs-lookup"><span data-stu-id="ee560-179">Doing this creates the specified file path on the mirror server and restores the new file to that location.</span></span>  
  
3.  <span data-ttu-id="ee560-180">若要針對新的鏡像工作階段準備資料庫，此擁有者也必須使用 WITH NO RECOVERY，從主體伺服器還原任何其他未完成的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="ee560-180">To prepare the database for a new mirroring session, the owner must also restore WITH NO RECOVERY any other outstanding log backups from the principal server.</span></span>  
  
 <span data-ttu-id="ee560-181">如需詳細資訊，請參閱[移除資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md)、[準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)、[使用 Windows 驗證建立資料庫鏡像工作階段 &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md)、[使用資料庫鏡像端點憑證 &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md) 或[使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="ee560-181">For more information, see [Removing Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md), [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md), [Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md), [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md), or [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md).</span></span>  
  
##  <a name="starting-mirroring-by-using-transact-sql"></a><a name="StartDbm"></a><span data-ttu-id="ee560-182">使用 Transact-sql 啟動鏡像</span><span class="sxs-lookup"><span data-stu-id="ee560-182">Starting mirroring by Using Transact-SQL</span></span>  
 <span data-ttu-id="ee560-183">ALTER DATABASE *database_name* SET PARTNER **='***partner_server***'** 陳述式發出的順序非常重要。</span><span class="sxs-lookup"><span data-stu-id="ee560-183">The order in which the ALTER DATABASE *database_name* SET PARTNER **='***partner_server***'** statements are issued is very important.</span></span>  
  
1.  <span data-ttu-id="ee560-184">第一個陳述式必須在鏡像伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="ee560-184">The first statement must be run on the mirror server.</span></span> <span data-ttu-id="ee560-185">發出這個陳述式時，鏡像伺服器並不會嘗試聯繫任何其他伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="ee560-185">When this statement is issued, the mirror server does not try to contact any other server instance.</span></span> <span data-ttu-id="ee560-186">鏡像伺服器卻會指示其資料庫等到主體伺服器聯繫上鏡像伺服器為止。</span><span class="sxs-lookup"><span data-stu-id="ee560-186">Instead, the mirror server instructs its database to wait until the mirror server has been contacted by the principal server.</span></span>  
  
2.  <span data-ttu-id="ee560-187">第二個 ALTER DATABASE 陳述式必須在主體伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="ee560-187">The second ALTER DATABASE statement must be run on the principal server.</span></span> <span data-ttu-id="ee560-188">這個陳述式會讓主體伺服器嘗試連接鏡像伺服器。</span><span class="sxs-lookup"><span data-stu-id="ee560-188">This statement causes the principal server to try to connect to the mirror server.</span></span> <span data-ttu-id="ee560-189">建立該連接之後，鏡像便會嘗試在另一個連接上連接到主體伺服器。</span><span class="sxs-lookup"><span data-stu-id="ee560-189">After that connection is created, the mirror then tries to connect to the principal server on another connection.</span></span>  
  
 <span data-ttu-id="ee560-190">如需詳細資訊，請參閱 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ee560-190">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ee560-191">如需使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 啟動鏡像的相關資訊，請參閱[使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="ee560-191">For information about using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to start mirroring, see [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md).</span></span>  
  
##  <a name="cross-database-transactions"></a><a name="CrossDbTxns"></a><span data-ttu-id="ee560-192">跨資料庫交易</span><span class="sxs-lookup"><span data-stu-id="ee560-192">Cross-Database Transactions</span></span>  
 <span data-ttu-id="ee560-193">當資料庫正在具有自動容錯移轉的高安全性模式下進行鏡像時，自動容錯移轉會造成自動解析未確定的交易，但解析可能不正確。</span><span class="sxs-lookup"><span data-stu-id="ee560-193">When a database is being mirrored in high-safety mode with automatic failover, an automatic failover could lead to automatic and possibly incorrect resolution of in-doubt transactions.</span></span> <span data-ttu-id="ee560-194">如果在認可跨資料庫交易時，其中一個資料庫進行了自動容錯移轉，則資料庫之間可能會發生邏輯不一致的情況。</span><span class="sxs-lookup"><span data-stu-id="ee560-194">If an automatic failover occurs on either database while a cross-database transaction is being committed, logical inconsistencies can occur between the databases.</span></span>  
  
 <span data-ttu-id="ee560-195">可能受到自動容錯移轉影響的跨資料庫交易類型包括：</span><span class="sxs-lookup"><span data-stu-id="ee560-195">The types of cross-database transactions that can be affected by an automatic failover include the following:</span></span>  
  
-   <span data-ttu-id="ee560-196">在相同 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體中對多個資料庫進行更新的交易。</span><span class="sxs-lookup"><span data-stu-id="ee560-196">A transaction that is updating multiple databases in the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="ee560-197">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散式交易協調器 (MS DTC) 的交易。</span><span class="sxs-lookup"><span data-stu-id="ee560-197">Transactions that use a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC).</span></span>  
  
 <span data-ttu-id="ee560-198">如需詳細資訊，請參閱[資料庫鏡像或 AlwaysOn 可用性群組不支援跨資料庫交易 &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="ee560-198">For more information, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee560-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee560-199">See Also</span></span>  
 <span data-ttu-id="ee560-200">[設定資料庫鏡像 &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ee560-200">[Setting Up Database Mirroring &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="ee560-201">資料庫鏡像和 AlwaysOn 可用性群組的傳輸安全性 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ee560-201">Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](transport-security-database-mirroring-always-on-availability.md)  
  
  
