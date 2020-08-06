---
title: 使用 Windows 驗證建立資料庫鏡像會話 (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Windows authentication [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 143c68a5-589f-4e7f-be59-02707e1a430a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f3088333fbfd4babd209df07f8880c838ce626d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592230"
---
# <a name="establish-a-database-mirroring-session-using-windows-authentication-transact-sql"></a><span data-ttu-id="2a293-102">使用 Windows 驗證建立資料庫鏡像工作階段 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2a293-102">Establish a Database Mirroring Session Using Windows Authentication (Transact-SQL)</span></span>
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] <span data-ttu-id="2a293-103">請改用 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2a293-103">Use [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] instead.</span></span>  
  
 <span data-ttu-id="2a293-104">準備好鏡像資料庫之後 (請參閱 [準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md))，就可以建立資料庫鏡像工作階段。</span><span class="sxs-lookup"><span data-stu-id="2a293-104">After the mirror database is prepared (see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)), you can establish a database mirroring session.</span></span> <span data-ttu-id="2a293-105">主體、鏡像及見證伺服器執行個體必須是個別的伺服器執行個體，且應位於個別的主機系統上。</span><span class="sxs-lookup"><span data-stu-id="2a293-105">The principal, mirror, and witness server instances must be separate server instances, which should be on separate host systems.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2a293-106">我們建議您將資料庫鏡像作業排定在離峰時間執行，因為設定鏡像會影響效能。</span><span class="sxs-lookup"><span data-stu-id="2a293-106">We recommend that you configure database mirroring during off-peak hours because configuring mirroring can impact performance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a293-107">給定的伺服器執行個體可參與具有相同或不同夥伴的多個並行資料庫鏡像工作階段。</span><span class="sxs-lookup"><span data-stu-id="2a293-107">A given server instance can participate in multiple concurrent database mirroring sessions with the same or different partners.</span></span> <span data-ttu-id="2a293-108">伺服器執行個體可以在某些工作階段中是夥伴，在其他工作階段中是見證。</span><span class="sxs-lookup"><span data-stu-id="2a293-108">A server instance can be a partner in some sessions and a witness in other sessions.</span></span> <span data-ttu-id="2a293-109">鏡像伺服器執行個體必須執行與主體伺服器執行個體相同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="2a293-109">The mirror server instance must be running the same edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as the principal server instance.</span></span> <span data-ttu-id="2a293-110">並非所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2a293-110">Database mirroring is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2a293-111">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="2a293-111">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="2a293-112">此外，我們強烈建議您在可比較而且可以處理相同工作負載的系統上執行這些伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a293-112">Also, we strongly recommend that they run on comparable systems that can handle identical workloads.</span></span>  
  
### <a name="to-establish-a-database-mirroring-session"></a><span data-ttu-id="2a293-113">建立資料庫鏡像工作階段</span><span class="sxs-lookup"><span data-stu-id="2a293-113">To establish a database mirroring session</span></span>  
  
1.  <span data-ttu-id="2a293-114">建立鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="2a293-114">Create the mirror database.</span></span> <span data-ttu-id="2a293-115">如需詳細資訊，請參閱 [準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2a293-115">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="2a293-116">設定每個伺服器執行個體的安全性。</span><span class="sxs-lookup"><span data-stu-id="2a293-116">Set up security on each server instance.</span></span>  
  
     <span data-ttu-id="2a293-117">資料庫鏡像工作階段中的每個伺服器執行個體都需要一個資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="2a293-117">Each server instance in a database mirroring session requires a database mirroring endpoint.</span></span> <span data-ttu-id="2a293-118">如果端點不存在，您就必須自行建立。</span><span class="sxs-lookup"><span data-stu-id="2a293-118">If the endpoint does not exist, you must create it.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2a293-119">伺服器執行個體用於資料庫鏡像的驗證格式，是其資料庫鏡像端點的屬性。</span><span class="sxs-lookup"><span data-stu-id="2a293-119">The form of authentication used for database mirroring by a server instance is a property of its database mirroring endpoint.</span></span> <span data-ttu-id="2a293-120">有兩種傳輸安全性可用於資料庫鏡像：Windows 驗證或以憑證為基礎的驗證。</span><span class="sxs-lookup"><span data-stu-id="2a293-120">Two types of transport security are available for database mirroring: Windows Authentication or certificate-based authentication.</span></span> <span data-ttu-id="2a293-121">如需詳細資訊，請參閱[資料庫鏡像的傳輸安全性和 AlwaysOn 可用性群組 &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="2a293-121">For more information, see [Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md).</span></span>  
  
     <span data-ttu-id="2a293-122">確定在每個夥伴伺服器上，資料庫鏡像都有端點可供使用。</span><span class="sxs-lookup"><span data-stu-id="2a293-122">On each partner server, ensure that an endpoint exists for database mirroring.</span></span> <span data-ttu-id="2a293-123">不論要支援的鏡像工作階段數有多少，伺服器執行個體只能有一個資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="2a293-123">Regardless of the number of mirroring sessions to be supported, the server instance can have only one database mirroring endpoint.</span></span> <span data-ttu-id="2a293-124">若要讓資料庫鏡像工作階段的夥伴獨佔使用此伺服器執行個體，您可以將夥伴的角色指派給端點 (ROLE **=** PARTNER)。</span><span class="sxs-lookup"><span data-stu-id="2a293-124">If you intend to use this server instance exclusively for partners in database mirroring sessions, you can assign the role of partner to the endpoint (ROLE**=** PARTNER).</span></span> <span data-ttu-id="2a293-125">如果您也想讓其他資料庫鏡像工作階段的見證使用此伺服器，請將端點的角色指派為 ALL。</span><span class="sxs-lookup"><span data-stu-id="2a293-125">If you intend also to use this server for the witness in other database mirroring sessions, assign the role of the endpoint as ALL.</span></span>  
  
     <span data-ttu-id="2a293-126">若要執行 SET PARTNER 陳述式，兩個夥伴的端點狀態 (STATE) 必須都設為 STARTED。</span><span class="sxs-lookup"><span data-stu-id="2a293-126">To execute a SET PARTNER statement, the STATE of the endpoints of both partners must be set to STARTED.</span></span>  
  
     <span data-ttu-id="2a293-127">若要了解伺服器執行個體是否有資料庫鏡像端點，以及它在該執行個體上的角色與狀態，請使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="2a293-127">To learn whether a server instance has a database mirroring endpoint and to learn its role and state, on that instance, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    SELECT role_desc, state_desc FROM sys.database_mirroring_endpoints  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2a293-128">請不要重新設定使用中資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="2a293-128">Do not reconfigure an in-use database mirroring endpoint.</span></span> <span data-ttu-id="2a293-129">若資料庫鏡像端點存在且已在使用中，我們建議您在該伺服器執行個體上為每個工作階段使用該端點。</span><span class="sxs-lookup"><span data-stu-id="2a293-129">If a database mirroring endpoint exists and is already in use, we recommend that you use that endpoint for every session on the server instance.</span></span> <span data-ttu-id="2a293-130">卸除使用中端點可能會導致端點重新啟動，並中斷現有工作階段的連接，而這對於其他伺服器執行個體可能會是一項錯誤。</span><span class="sxs-lookup"><span data-stu-id="2a293-130">Dropping an in-use endpoint can cause the endpoint to restart, disrupting the connections of the existing sessions, which can appear to be an error to the other server instances.</span></span> <span data-ttu-id="2a293-131">在具有自動容錯移轉的高安全性模式中，這點尤其重要，因為在這種模式中重新設定夥伴上的端點，可能會導致發生容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="2a293-131">This is particularly important in high-safety mode with automatic failover, in which reconfiguring the endpoint on a partner could cause a failover to occur.</span></span> <span data-ttu-id="2a293-132">此外，如果已針對工作階段設定見證，則卸除資料庫鏡像端點可能會導致該工作階段的主體伺服器失去仲裁。若發生此情況，則資料庫會離線，並中斷與資料庫使用者的的連線。</span><span class="sxs-lookup"><span data-stu-id="2a293-132">Also, if a witness has been set for a session, dropping the database mirroring endpoint can cause the principal server of that session to lose quorum; if that occurs, the database is taken offline and its users are disconnected.</span></span> <span data-ttu-id="2a293-133">如需詳細資訊，請參閱[仲裁：見證如何影響資料庫可用性 &#40;資料庫鏡像&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="2a293-133">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
     <span data-ttu-id="2a293-134">如果任一夥伴缺少端點，請參閱[建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="2a293-134">If either partner lacks an endpoint, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).</span></span>  
  
3.  <span data-ttu-id="2a293-135">如果伺服器執行個體正在不同的網域使用者帳戶下執行，每個執行個體都會需要登入其他執行個體的 **master** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="2a293-135">If server instances are running under different domain user accounts, each requires a login in the **master** database of the others.</span></span> <span data-ttu-id="2a293-136">如果登入不存在，您就必須自行建立。</span><span class="sxs-lookup"><span data-stu-id="2a293-136">If the login does not exist, you must create it.</span></span> <span data-ttu-id="2a293-137">如需詳細資訊，請參閱 [使用 Windows 驗證允許資料庫鏡像的網路存取 &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="2a293-137">For more information, see [Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
4.  <span data-ttu-id="2a293-138">若要設定主體伺服器做為鏡像資料庫上的夥伴，請連接到該鏡像伺服器，並執行以下陳述式：</span><span class="sxs-lookup"><span data-stu-id="2a293-138">To set the principal server as partner on the mirror database, connect to the mirror server, and issue the following statement:</span></span>  
  
     <span data-ttu-id="2a293-139">ALTER DATABASE *<database_name>* 設定夥伴 **=** _<server_network_address>_</span><span class="sxs-lookup"><span data-stu-id="2a293-139">ALTER DATABASE *<database_name>* SET PARTNER **=**_<server_network_address>_</span></span>  
  
     <span data-ttu-id="2a293-140">其中 *<database_name>* 是要鏡像的資料庫名稱 (這個名稱在兩個夥伴) 上都相同，而且 *<server_network_address>* 是主體伺服器的伺服器網路位址。</span><span class="sxs-lookup"><span data-stu-id="2a293-140">where *<database_name>* is the name of the database to be mirrored (this name is the same on both partners), and *<server_network_address>* is the server network address of the principal server.</span></span>  
  
     <span data-ttu-id="2a293-141">伺服器網路位址的語法如下：</span><span class="sxs-lookup"><span data-stu-id="2a293-141">The syntax for a server network address is as follows:</span></span>  
  
     <span data-ttu-id="2a293-142">TCP：<strong>//</strong> \<*system-address> \* <strong>：</strong> \<*port> \*</span><span class="sxs-lookup"><span data-stu-id="2a293-142">TCP<strong>://</strong>\<*system-address>*<strong>:</strong>\<*port>*</span></span>  
  
     <span data-ttu-id="2a293-143">其中 \<*system-address>\* 是清楚識別目的地電腦系統的字串，而 \<*port>\* 是合作夥伴伺服器執行個體之鏡像端點所使用的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="2a293-143">where \<*system-address>\* is a string that unambiguously identifies the destination computer system, and \<*port>\* is the port number used by the mirroring endpoint of the partner server instance.</span></span> <span data-ttu-id="2a293-144">如需詳細資訊，請參閱 [指定伺服器網路位址 &#40;資料庫鏡像&#41;](specify-a-server-network-address-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="2a293-144">For more information, see [Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md).</span></span>  
  
     <span data-ttu-id="2a293-145">例如，在鏡像伺服器執行個體上，下列 ALTER DATABASE 陳述式將夥伴設為原始主體伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a293-145">For example, on the mirror server instance, the following ALTER DATABASE statement sets the partner as the original principal server instance.</span></span> <span data-ttu-id="2a293-146">資料庫名稱是 **AdventureWorks**、系統位址是 DBSERVER1 (夥伴系統的名稱)，而夥伴資料庫鏡像端點使用的通訊埠是 7022：</span><span class="sxs-lookup"><span data-stu-id="2a293-146">The database name is **AdventureWorks**, the system address is DBSERVER1-the name of the partner's system-and the port used by the partner's database mirroring endpoint is 7022:</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
       SET PARTNER = 'TCP://DBSERVER1:7022'  
    ```  
  
     <span data-ttu-id="2a293-147">此陳述式會準備鏡像伺服器，以便在主體伺服器通知之後建立工作階段。</span><span class="sxs-lookup"><span data-stu-id="2a293-147">This statement prepares the mirror server to form a session when it is contacted by the principal server.</span></span>  
  
5.  <span data-ttu-id="2a293-148">若要設定鏡像伺服器做為主體資料庫上的夥伴，請連接到該主體伺服器，並發出以下陳述式：</span><span class="sxs-lookup"><span data-stu-id="2a293-148">To set the mirror server as partner on the principal database, connect to the principal server, and issue the following statement:</span></span>  
  
     <span data-ttu-id="2a293-149">ALTER DATABASE *<database_name>* 設定夥伴 **=** _<server_network_address>_</span><span class="sxs-lookup"><span data-stu-id="2a293-149">ALTER DATABASE *<database_name>* SET PARTNER **=**_<server_network_address>_</span></span>  
  
     <span data-ttu-id="2a293-150">如需詳細資訊，請參閱步驟 4。</span><span class="sxs-lookup"><span data-stu-id="2a293-150">For more information, see step 4.</span></span>  
  
     <span data-ttu-id="2a293-151">例如，在主體伺服器執行個體上，下列 ALTER DATABASE 陳述式將夥伴設為原始鏡像伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a293-151">For example, on the principal server instance, the following ALTER DATABASE statement sets the partner as the original mirror server instance.</span></span> <span data-ttu-id="2a293-152">資料庫名稱是 **AdventureWorks**，系統位址是 DBSERVER2 (夥伴系統的名稱) 而夥伴資料庫鏡像端點使用的通訊埠是 7025：</span><span class="sxs-lookup"><span data-stu-id="2a293-152">The database name is **AdventureWorks**, the system address is DBSERVER2-the name of the partner's system-and the port used by the partner's database mirroring endpoint is 7025:</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks SET PARTNER = 'TCP://DBSERVER2:7022'  
    ```  
  
     <span data-ttu-id="2a293-153">在主體伺服器上輸入此陳述式可開始資料庫鏡像工作階段。</span><span class="sxs-lookup"><span data-stu-id="2a293-153">Entering this statement on the principal server begins the database mirroring session.</span></span>  
  
6.  <span data-ttu-id="2a293-154">依預設，工作階段會設定為完整交易安全性 (SAFETY 設定為 FULL)，它會以不含自動容錯移轉的同步高安全性模式啟動工作階段。</span><span class="sxs-lookup"><span data-stu-id="2a293-154">By default a session is set to full transaction safety (SAFETY is set to FULL), which starts the session in synchronous, high-safety mode without automatic failover.</span></span> <span data-ttu-id="2a293-155">您可以依照下列方式，將工作階段重新設定為在具有自動容錯移轉的高安全性模式下執行，或在非同步的高效能模式下執行：</span><span class="sxs-lookup"><span data-stu-id="2a293-155">You can reconfigure the session to run in high-safety mode with automatic failover or in asynchronous, high-performance mode, as follows:</span></span>  
  
    -   <span data-ttu-id="2a293-156">**具有自動容錯移轉的高安全性模式**</span><span class="sxs-lookup"><span data-stu-id="2a293-156">**High-safety mode with automatic failover**</span></span>  
  
         <span data-ttu-id="2a293-157">如果您想讓高安全性模式工作階段支援自動容錯移轉，請加入見證伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a293-157">If you want a high-safety mode session to support automatic failover, add a witness server instance.</span></span> <span data-ttu-id="2a293-158">如需詳細資訊，請參閱[使用 Windows 驗證加入資料庫鏡像見證 &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="2a293-158">For more information, see [Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md).</span></span>  
  
    -   <span data-ttu-id="2a293-159">**高效能模式**</span><span class="sxs-lookup"><span data-stu-id="2a293-159">**High-performance mode**</span></span>  
  
         <span data-ttu-id="2a293-160">或者，如果您不想進行自動容錯移轉，而且較注重效能而非可用性，請關閉交易安全性。</span><span class="sxs-lookup"><span data-stu-id="2a293-160">Alternatively, if you do not want automatic failover and you prefer to emphasize performance over availability, turn off transaction safety.</span></span> <span data-ttu-id="2a293-161">如需詳細資訊，請參閱[在資料庫鏡像工作階段中變更交易安全性 &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="2a293-161">For more information, see [Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md).</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="2a293-162">在高效能模式中，必須將 WITNESS 設定為 OFF。</span><span class="sxs-lookup"><span data-stu-id="2a293-162">In high-performance mode, WITNESS should be set to OFF.</span></span> <span data-ttu-id="2a293-163">如需詳細資訊，請參閱[仲裁：見證如何影響資料庫可用性 &#40;資料庫鏡像&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="2a293-163">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a293-164">範例</span><span class="sxs-lookup"><span data-stu-id="2a293-164">Example</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a293-165">下列範例會在夥伴之間為現有的鏡像資料庫建立資料庫鏡像工作階段。</span><span class="sxs-lookup"><span data-stu-id="2a293-165">The following example establishes a database mirroring session between partners for an existing mirror database.</span></span> <span data-ttu-id="2a293-166">如需建立鏡像資料庫的資訊，請參閱 [準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2a293-166">For information on creating a mirror database, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)=.</span></span>  
  
 <span data-ttu-id="2a293-167">此範例會顯示建立資料庫鏡像工作階段 (不使用見證) 的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="2a293-167">The example shows the basic steps for creating a database mirroring session without a witness.</span></span> <span data-ttu-id="2a293-168">這兩個夥伴是兩個電腦系統 (PARTNERHOST1 和 PARTNERHOST5) 上的預設伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a293-168">The two partners are the default server instances on two computer systems (PARTNERHOST1 and PARTNERHOST5).</span></span> <span data-ttu-id="2a293-169">這兩個夥伴執行個體會執行相同的 Windows 網域使用者帳戶 (MYDOMAIN\dbousername)。</span><span class="sxs-lookup"><span data-stu-id="2a293-169">The two partner instances run the same Windows domain user account (MYDOMAIN\dbousername).</span></span>  
  
1.  <span data-ttu-id="2a293-170">在主體伺服器執行個體 (PARTNERHOST1 上的預設執行個體) 上，使用通訊埠 7022 建立支援所有角色的端點：</span><span class="sxs-lookup"><span data-stu-id="2a293-170">On the principal server instance (default instance on PARTNERHOST1), create an endpoint that supports all roles using port 7022:</span></span>  
  
    ```  
    --create an endpoint for this instance  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO  
    --Partners under same domain user; login already exists in master.  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="2a293-171">如需設定登入的範例，請參閱 [使用 Windows 驗證允許資料庫鏡像的網路存取 &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="2a293-171">For an example of how to setup a login, see [Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
2.  <span data-ttu-id="2a293-172">在鏡像伺服器執行個體 (PARTNERHOST5 上的預設執行個體) 上，使用通訊埠 7022 建立支援所有角色的端點：</span><span class="sxs-lookup"><span data-stu-id="2a293-172">On the mirror server instance (default instance on PARTNERHOST5), create an endpoint that supports all roles using port 7022:</span></span>  
  
    ```  
    --create an endpoint for this instance  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO  
    --Partners under same domain user; login already exists in master.  
    ```  
  
3.  <span data-ttu-id="2a293-173">在主體伺服器執行個體 (位於 PARTNERHOST1) 上，備份資料庫：</span><span class="sxs-lookup"><span data-stu-id="2a293-173">On the principal server instance (on PARTNERHOST1), back up the database:</span></span>  
  
    ```  
    BACKUP DATABASE AdventureWorks   
        TO DISK = 'C:\AdvWorks_dbmirror.bak'   
        WITH FORMAT  
    GO  
    ```  
  
4.  <span data-ttu-id="2a293-174">在鏡像伺服器執行個體 (在 `PARTNERHOST5`上) 上，還原資料庫：</span><span class="sxs-lookup"><span data-stu-id="2a293-174">On the mirror server instance (on `PARTNERHOST5`), restore the database:</span></span>  
  
    ```  
    RESTORE DATABASE AdventureWorks   
        FROM DISK = 'Z:\AdvWorks_dbmirror.bak'   
        WITH NORECOVERY  
    GO  
    ```  
  
5.  <span data-ttu-id="2a293-175">建立完整資料庫備份之後，您必須在主體資料庫上建立記錄備份。</span><span class="sxs-lookup"><span data-stu-id="2a293-175">After you create the full database backup, you must create a log backup on the principal database.</span></span> <span data-ttu-id="2a293-176">例如，下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式會將記錄備份至前一次資料庫備份所使用的相同檔案：</span><span class="sxs-lookup"><span data-stu-id="2a293-176">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement backs up the log to the same file used by the preceding database backup:</span></span>  
  
    ```  
    BACKUP LOG AdventureWorks   
        TO DISK = 'C:\AdventureWorks.bak'   
    GO  
    ```  
  
6.  <span data-ttu-id="2a293-177">您必須先套用必要的記錄備份 (以及任何後續記錄備份)，才能啟動鏡像。</span><span class="sxs-lookup"><span data-stu-id="2a293-177">Before you can start mirroring, you must apply the required log backup (and any subsequent log backups).</span></span>  
  
     <span data-ttu-id="2a293-178">例如，下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式會從 C:\AdventureWorks.bak 還原第一筆記錄：</span><span class="sxs-lookup"><span data-stu-id="2a293-178">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement restores the first log from C:\AdventureWorks.bak:</span></span>  
  
    ```  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\ AdventureWorks.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
7.  <span data-ttu-id="2a293-179">在鏡像伺服器執行個體上，將 PARTNERHOST1 上的伺服器執行個體設定為夥伴 (讓它成為初始主體伺服器)：</span><span class="sxs-lookup"><span data-stu-id="2a293-179">On the mirror server instance, set the server instance on PARTNERHOST1 as the partner (making it the initial principal server):</span></span>  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks   
        SET PARTNER =   
        'TCP://PARTNERHOST1:7022'  
    GO  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2a293-180">依預設，資料庫鏡像工作階段會以同步模式執行，前提是必須有完整交易安全性 (SAFETY 設定為 FULL)。</span><span class="sxs-lookup"><span data-stu-id="2a293-180">default, a database mirroring session runs in synchronous mode, which depends on having full transaction safety (SAFETY is set to FULL).</span></span> <span data-ttu-id="2a293-181">若要讓工作階段以非同步的高效能模式執行，請將 SAFETY 設定為 OFF。</span><span class="sxs-lookup"><span data-stu-id="2a293-181">To cause a session to run in asynchronous, high-performance mode, set SAFETY to OFF.</span></span> <span data-ttu-id="2a293-182">如需詳細資訊，請參閱 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)。</span><span class="sxs-lookup"><span data-stu-id="2a293-182">For more information, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
8.  <span data-ttu-id="2a293-183">在主體伺服器執行個體上，將 `PARTNERHOST5` 上的伺服器執行個體設定為夥伴 (讓它成為初始鏡像伺服器)：</span><span class="sxs-lookup"><span data-stu-id="2a293-183">On the principal server instance, set the server instance on `PARTNERHOST5` as the partner (making it the initial mirror server):</span></span>  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks   
        SET PARTNER = 'TCP://PARTNERHOST5:7022'  
    GO  
    ```  
  
9. <span data-ttu-id="2a293-184">或者，如果您想要使用具有自動容錯移轉的高安全性模式，請設定見證伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a293-184">Optionally, if you intend to use high-safety mode with automatic failover, set up the witness server instance.</span></span> <span data-ttu-id="2a293-185">如需詳細資訊，請參閱[使用 Windows 驗證加入資料庫鏡像見證 &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="2a293-185">For more information, see [Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a293-186">如需顯示安全性設定、準備鏡像資料庫、設定夥伴及新增見證的完整範例，請參閱[設定資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2a293-186">For a complete example showing security setup, preparing the mirror database, setting up the partners, and adding a witness, see [Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a293-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a293-187">See Also</span></span>  
 <span data-ttu-id="2a293-188">[設定資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2a293-188">[Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="2a293-189">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2a293-189">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="2a293-190">[使用 Windows 驗證允許資料庫鏡像的網路存取 &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="2a293-190">[Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md) </span></span>  
 <span data-ttu-id="2a293-191">[準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2a293-191">[Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="2a293-192">[建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="2a293-192">[Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) </span></span>  
 <span data-ttu-id="2a293-193">[資料庫鏡像和記錄傳送 &#40;SQL Server&#41;](database-mirroring-and-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2a293-193">[Database Mirroring and Log Shipping &#40;SQL Server&#41;](database-mirroring-and-log-shipping-sql-server.md) </span></span>  
 <span data-ttu-id="2a293-194">[資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2a293-194">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="2a293-195">[資料庫鏡像和複寫 &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2a293-195">[Database Mirroring and Replication &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md) </span></span>  
 <span data-ttu-id="2a293-196">[設定資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2a293-196">[Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="2a293-197">[指定伺服器網路位址 &#40;資料庫鏡像&#41;](specify-a-server-network-address-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="2a293-197">[Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md) </span></span>  
 [<span data-ttu-id="2a293-198">Database Mirroring Operating Modes</span><span class="sxs-lookup"><span data-stu-id="2a293-198">Database Mirroring Operating Modes</span></span>](database-mirroring-operating-modes.md)  
  
  
