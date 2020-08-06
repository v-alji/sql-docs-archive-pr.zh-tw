---
title: 使用 Windows 驗證新增資料庫鏡像見證 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- witness [SQL Server], establishing
- Windows authentication [SQL Server]
- database mirroring [SQL Server], witness
ms.assetid: bf5e87df-91a4-49f9-ae88-2a6dcf644510
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 88684c3a1ca12ea579859759ed804ca281647fa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593590"
---
# <a name="add-a-database-mirroring-witness-using-windows-authentication-transact-sql"></a><span data-ttu-id="6a7b4-102">使用 Windows 驗證加入資料庫鏡像見證 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6a7b4-102">Add a Database Mirroring Witness Using Windows Authentication (Transact-SQL)</span></span>
  <span data-ttu-id="6a7b4-103">為設定資料庫的見證，資料庫擁有者會指派 Database Engine 執行個體給見證伺服器的角色。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-103">To set up a witness for a database, the database owner assigns a Database Engine instance to the role of witness server.</span></span> <span data-ttu-id="6a7b4-104">見證伺服器執行個體可以與主體或鏡像伺服器執行個體在相同電腦上執行，但是這會大幅地減少自動容錯移轉的強固性。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-104">The witness server instance can run on the same computer as the principal or mirror server instance, but this substantially reduces the robustness of automatic failover.</span></span>  
  
 <span data-ttu-id="6a7b4-105">我們強烈建議見證應該位在另一台電腦上。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-105">We strongly recommend that the witness reside on a separate computer.</span></span> <span data-ttu-id="6a7b4-106">給定的伺服器可以參與具有相同或不同夥伴的多個並行資料庫鏡像工作階段。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-106">A given server can participate in multiple concurrent database mirroring sessions with the same or different partners.</span></span> <span data-ttu-id="6a7b4-107">一個給定的伺服器可以在某些工作階段中是夥伴，在其他工作階段中是見證。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-107">A given server can be a partner in some sessions and a witness in other sessions.</span></span>  
  
 <span data-ttu-id="6a7b4-108">見證是專門用於具有自動容錯移轉的高安全性模式。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-108">The witness is intended exclusively for high-safety mode with automatic failover.</span></span> <span data-ttu-id="6a7b4-109">在您設定見證之前，我們強烈建議您確定 SAFETY 屬性目前已設定為 FULL。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-109">Before you set a witness, we strongly recommend that you ensure that the SAFETY property is currently set to FULL.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6a7b4-110">我們建議您在離峰時間設定資料庫鏡像，因為組態會影響效能。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-110">We recommend that you configure database mirroring during off-peak hours because configuration can impact performance.</span></span>  
  
### <a name="to-establish-a-witness"></a><span data-ttu-id="6a7b4-111">若要建立見證</span><span class="sxs-lookup"><span data-stu-id="6a7b4-111">To establish a witness</span></span>  
  
1.  <span data-ttu-id="6a7b4-112">在見證伺服器執行個體上，確定資料庫鏡像有端點存在。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-112">On the witness server instance, ensure that an endpoint exists for database mirroring.</span></span> <span data-ttu-id="6a7b4-113">不管要支援的鏡像工作階段有多少個，伺服器執行個體都必須只有一個資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-113">Regardless of the number of mirroring session to be supported, the server instance must have only one database mirroring endpoint.</span></span> <span data-ttu-id="6a7b4-114">如果您想要在資料庫鏡像會話中以獨佔方式使用此伺服器實例做為見證，請將見證的角色指派給 (角色 **=** 見證) 的端點。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-114">If you intend to use this server instance exclusively as a witness in database mirroring sessions, assign the role of witness to the endpoint (ROLE **=** WITNESS).</span></span> <span data-ttu-id="6a7b4-115">如果您打算使用這個伺服器執行個體，作為一或多個其他資料庫鏡像工作階段中的夥伴，請將端點的角色指派為 ALL。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-115">If you intend to use this server instance as a partner in one or more other database mirroring sessions, assign the role of the endpoint as ALL.</span></span>  
  
     <span data-ttu-id="6a7b4-116">若要執行 SET WITNESS 陳述式，資料庫鏡像工作階段必須已經啟動 (在夥伴之間)，而且見證端點的 STATE 必須設為 STARTED。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-116">To execute a SET WITNESS statement, the database mirroring session must already be started (between the partners), and the STATE of the endpoint of the witness must be set to STARTED.</span></span>  
  
     <span data-ttu-id="6a7b4-117">若要了解見證伺服器執行個體是否具有它的資料庫鏡像端點，以及了解其角色和狀態，請在該執行個體上，使用下列 Transact-SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="6a7b4-117">To learn whether the witness server instance has its database mirroring endpoint and to learn its role and state, on that instance, use the following Transact-SQL statement:</span></span>  
  
    ```  
    SELECT role_desc, state_desc FROM sys.database_mirroring_endpoints  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="6a7b4-118">若資料庫鏡像端點存在且已在使用中，我們建議您在該伺服器執行個體上為每個工作階段使用該端點。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-118">If a database mirroring endpoint exists and is already in use, we recommend that you use that endpoint for every session on the server instance.</span></span> <span data-ttu-id="6a7b4-119">卸除使用中端點會中斷現有工作階段的連接。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-119">Dropping an in-use endpoint disrupts the connections of the existing sessions.</span></span> <span data-ttu-id="6a7b4-120">如果已針對工作階段設定見證，則卸除資料庫鏡像端點可能會導致該工作階段的主體伺服器失去仲裁；若發生此情況，則資料庫會離線，並中斷連接到資料庫的所有使用者。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-120">If a witness has been set for a session, dropping the database mirroring endpoint can cause the principal server of that session to lose quorum; if that occurs, the database is taken offline and its users are disconnected.</span></span> <span data-ttu-id="6a7b4-121">如需詳細資訊，請參閱[仲裁：見證如何影響資料庫可用性 &#40;資料庫鏡像&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-121">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
     <span data-ttu-id="6a7b4-122">如果見證缺少端點，請參閱[建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-122">If the witness lacks an endpoint, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).</span></span>  
  
2.  <span data-ttu-id="6a7b4-123">若夥伴執行個體是以不同網域使用者帳戶執行，請為每個執行個體中 master 資料庫的不同帳戶建立登入。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-123">If the partner instances are running under different domain user accounts, create a login for the different accounts in the master database of each instance.</span></span> <span data-ttu-id="6a7b4-124">如需詳細資訊，請參閱 [使用 Windows 驗證允許資料庫鏡像的網路存取 &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-124">For more information, see [Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
3.  <span data-ttu-id="6a7b4-125">連接到主體伺服器並執行以下陳述式：</span><span class="sxs-lookup"><span data-stu-id="6a7b4-125">Connect to the principal server and issue the following statement:</span></span>  
  
     <span data-ttu-id="6a7b4-126">ALTER DATABASE *<database_name>* 設定見證 **=** _<server_network_address>_</span><span class="sxs-lookup"><span data-stu-id="6a7b4-126">ALTER DATABASE *<database_name>* SET WITNESS **=** _<server_network_address>_</span></span>  
  
     <span data-ttu-id="6a7b4-127">其中 *<資料庫名稱>* 是要鏡像的資料庫名稱 (此名稱在兩個夥伴中都相同)，而 *<伺服器網路位址>* 是見證伺服器執行個體的伺服器網路位址。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-127">where *<database_name>* is the name of the database to be mirrored (this name is the same on both partners), and *<server_network_address>* is the server network address of the witness server instance.</span></span>  
  
     <span data-ttu-id="6a7b4-128">伺服器網路位址的語法如下：</span><span class="sxs-lookup"><span data-stu-id="6a7b4-128">The syntax for a server network address is as follows:</span></span>  
  
     <span data-ttu-id="6a7b4-129">TCP：**//** \<_system-address> _**：**\<*port>\*</span><span class="sxs-lookup"><span data-stu-id="6a7b4-129">TCP **://**\<_system-address>_**:**\<*port>\*</span></span>  
  
     <span data-ttu-id="6a7b4-130">其中 \<*system-address>\* 是清楚識別目的地電腦系統的字串，而 \<*port>\* 是合作夥伴伺服器執行個體之鏡像端點所使用的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-130">where \<*system-address>\* is a string that unambiguously identifies the destination computer system, and \<*port>\* is the port number used by the mirroring endpoint of the partner server instance.</span></span> <span data-ttu-id="6a7b4-131">如需詳細資訊，請參閱 [指定伺服器網路位址 &#40;資料庫鏡像&#41;](specify-a-server-network-address-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-131">For more information, see [Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md).</span></span>  
  
     <span data-ttu-id="6a7b4-132">例如，在主體伺服器執行個體上，下列 ALTER DATABASE 陳述式會設定見證。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-132">For example, on the principal server instance, the following ALTER DATABASE statement sets the witness.</span></span> <span data-ttu-id="6a7b4-133">資料庫名稱是 **AdventureWorks**、系統位址是 DBSERVER3 (見證系統的名稱)，而見證之資料庫鏡像端點所使用的連接埠是 `7022`：</span><span class="sxs-lookup"><span data-stu-id="6a7b4-133">The database name is **AdventureWorks**, the system address is DBSERVER3-the name of the witness system, and the port used by the database mirroring endpoint of the witness is `7022`:</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
      SET WITNESS = 'TCP://DBSERVER3:7022'  
    ```  
  
## <a name="example"></a><span data-ttu-id="6a7b4-134">範例</span><span class="sxs-lookup"><span data-stu-id="6a7b4-134">Example</span></span>  
 <span data-ttu-id="6a7b4-135">以下範例會建立資料庫鏡像見證。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-135">The following example establishes a data mirroring witness.</span></span> <span data-ttu-id="6a7b4-136">在見證伺服器執行個體 ( `WITNESSHOST4`上的預設執行個體) 上：</span><span class="sxs-lookup"><span data-stu-id="6a7b4-136">On the witness server instance (default instance on `WITNESSHOST4`):</span></span>  
  
1.  <span data-ttu-id="6a7b4-137">使用通訊埠 `7022`僅為 WITNESS 角色的此伺服器執行個體建立端點。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-137">Create an endpoint for this server instance for the WITNESS role only using port `7022`.</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=WITNESS)  
    GO  
    ```  
  
2.  <span data-ttu-id="6a7b4-138">若見證是以 `SOMEDOMAIN\witnessuser`執行，但夥伴是以 `MYDOMAIN\dbousername`執行，請為夥伴執行個體的使用者帳戶建立登入。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-138">Create a login for domain user account of partner instances, if different; for example, assume that the witness is running as `SOMEDOMAIN\witnessuser`, but the partners are running as `MYDOMAIN\dbousername`.</span></span> <span data-ttu-id="6a7b4-139">為夥伴建立登入，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6a7b4-139">Create a login for the partners, as follows:</span></span>  
  
    ```  
    --Create a login for the partner server instances,  
    --which are both running as MYDOMAIN\dbousername:  
    USE master ;  
    GO  
    CREATE LOGIN [MYDOMAIN\dbousername] FROM WINDOWS ;  
    GO  
    --Grant connect permissions on endpoint to login account   
    --of partners  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [MYDOMAIN\dbousername];  
    GO  
    ```  
  
3.  <span data-ttu-id="6a7b4-140">在每一個伺服器執行個體上，為見證伺服器執行個體建立登入：</span><span class="sxs-lookup"><span data-stu-id="6a7b4-140">On each of the partner server instances, create a login for the witness server instance:</span></span>  
  
    ```  
    --Create a login for the witness server instance,  
    --which is running as SOMEDOMAIN\witnessuser:  
    USE master ;  
    GO  
    CREATE LOGIN [SOMEDOMAIN\witnessuser] FROM WINDOWS ;  
    GO  
    --Grant connect permissions on endpoint to login account   
    --of partners  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [SOMEDOMAIN\witnessuser];  
    GO  
    ```  
  
4.  <span data-ttu-id="6a7b4-141">在主體伺服器上設定見證 (位於 `WITNESSHOST4`)：</span><span class="sxs-lookup"><span data-stu-id="6a7b4-141">On the principal server, set the witness (which is on `WITNESSHOST4`):</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
        SET WITNESS =   
        'TCP://WITNESSHOST4:7022'  
    GO  
    ```  
  
> [!NOTE]  
>  <span data-ttu-id="6a7b4-142">伺服器網路位址依通訊埠編號表示目標伺服器執行個體，它對應到執行個體的鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-142">The server network address indicates the target server instance by the port number, which maps to the mirroring endpoint of the instance.</span></span>  
  
 <span data-ttu-id="6a7b4-143">如需顯示安全性設定、準備鏡像資料庫、設定夥伴及新增見證的完整範例，請參閱[設定資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="6a7b4-143">For a complete example showing security setup, preparing the mirror database, setting up the partners, and adding a witness, see [Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a7b4-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a7b4-144">See Also</span></span>  
 <span data-ttu-id="6a7b4-145">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6a7b4-145">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="6a7b4-146">[使用 Windows 驗證允許資料庫鏡像的網路存取 &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="6a7b4-146">[Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md) </span></span>  
 <span data-ttu-id="6a7b4-147">[建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="6a7b4-147">[Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span></span>  
 <span data-ttu-id="6a7b4-148">[使用 Windows 驗證建立資料庫鏡像工作階段 &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="6a7b4-148">[Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md) </span></span>  
 <span data-ttu-id="6a7b4-149">[從資料庫鏡像工作階段移除見證 &#40;SQL Server&#41;](remove-the-witness-from-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6a7b4-149">[Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;](remove-the-witness-from-a-database-mirroring-session-sql-server.md) </span></span>  
 [<span data-ttu-id="6a7b4-150">資料庫鏡像見證</span><span class="sxs-lookup"><span data-stu-id="6a7b4-150">Database Mirroring Witness</span></span>](database-mirroring-witness.md)  
  
  
