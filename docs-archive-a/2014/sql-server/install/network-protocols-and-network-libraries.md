---
title: 網路通訊協定和網路程式庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- protocols [SQL Server]
- configuration options [SQL Server], protocols
- network libraries [SQL Server]
- protocols [SQL Server], about network protocols
- pipes [SQL Server]
- network protocols [SQL Server]
- default SQL Server configurations
- library [SQL Server]
- network protocols [SQL Server], about network protocols
- configuration options [SQL Server], libraries
ms.assetid: 8cd437f6-9af1-44ce-9cb0-4d10c83da9ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8be012ea2bc9499a99ca7763446c6f26cf219a18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606027"
---
# <a name="network-protocols-and-network-libraries"></a><span data-ttu-id="fc479-102">網路通訊協定和網路程式庫</span><span class="sxs-lookup"><span data-stu-id="fc479-102">Network Protocols and Network Libraries</span></span>
  <span data-ttu-id="fc479-103">伺服器可以一次接聽或監視多個網路通訊協定。</span><span class="sxs-lookup"><span data-stu-id="fc479-103">A server can listen on, or monitor, multiple network protocols at one time.</span></span> <span data-ttu-id="fc479-104">然而，必須設定每個通訊協定。</span><span class="sxs-lookup"><span data-stu-id="fc479-104">However, each protocol must be configured.</span></span> <span data-ttu-id="fc479-105">如果未設定特定的通訊協定，則伺服器將無法接聽該通訊協定。</span><span class="sxs-lookup"><span data-stu-id="fc479-105">If a particular protocol is not configured, the server cannot listen on that protocol.</span></span> <span data-ttu-id="fc479-106">安裝之後，您可以利用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員來變更通訊協定組態。</span><span class="sxs-lookup"><span data-stu-id="fc479-106">After installation, you can change the protocol configurations using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="default-sql-server-network-configuration"></a><span data-ttu-id="fc479-107">預設 SQL Server 網路組態</span><span class="sxs-lookup"><span data-stu-id="fc479-107">Default SQL Server Network Configuration</span></span>  
 <span data-ttu-id="fc479-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的預設執行個體會設定成使用 TCP/IP 通訊埠 1433 及具名管道 \\\\.\pipe\sql\query。</span><span class="sxs-lookup"><span data-stu-id="fc479-108">A default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured for TCP/IP port 1433, and named pipe \\\\.\pipe\sql\query.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fc479-109">具名執行個體會設定成使用 TCP 動態通訊埠，而該通訊埠的通訊埠編號則由作業系統指派。</span><span class="sxs-lookup"><span data-stu-id="fc479-109">named instances are configured for TCP dynamic ports, with a port number assigned by the operating system.</span></span>  
  
 <span data-ttu-id="fc479-110">如果您無法使用動態通訊埠位址 (例如，當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 連接必須通過已設定成通過特定通訊埠位址的防火牆伺服器時)。</span><span class="sxs-lookup"><span data-stu-id="fc479-110">If you cannot use dynamic port addresses (for example, when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connections must pass through a firewall server configured to pass through specific port addresses).</span></span> <span data-ttu-id="fc479-111">選取未指派的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="fc479-111">Select an unassigned port number.</span></span> <span data-ttu-id="fc479-112">通訊埠編號指派是由 Internet Assigned Numbers Authority 所管理，而且列於 [http://www.iana.org](https://go.microsoft.com/fwlink/?LinkId=48844)。</span><span class="sxs-lookup"><span data-stu-id="fc479-112">Port number assignments are managed by the Internet Assigned Numbers Authority and are listed at [http://www.iana.org](https://go.microsoft.com/fwlink/?LinkId=48844).</span></span>  
  
 <span data-ttu-id="fc479-113">為了加強安全性，安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時不會完全啟用網路連接。</span><span class="sxs-lookup"><span data-stu-id="fc479-113">To enhance security, network connectivity is not fully enabled when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span> <span data-ttu-id="fc479-114">若要在安裝程式完成之後啟用、停用和設定網路通訊協定，請使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 網路組態區域。</span><span class="sxs-lookup"><span data-stu-id="fc479-114">To enable, disable, and configure network protocols after Setup is complete, use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Network Configuration area of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="server-message-block-protocol"></a><span data-ttu-id="fc479-115">伺服器訊息區塊通訊協定</span><span class="sxs-lookup"><span data-stu-id="fc479-115">Server Message Block Protocol</span></span>  
 <span data-ttu-id="fc479-116">周邊網路中的伺服器應該停用所有非必要的通訊協定，包括伺服器訊息區塊 (SMB) 在內。</span><span class="sxs-lookup"><span data-stu-id="fc479-116">Servers in the perimeter network should have all unnecessary protocols disabled, including server message block (SMB).</span></span> <span data-ttu-id="fc479-117">Web 伺服器和網域名稱系統 (DNS) 伺服器不需要 SMB。</span><span class="sxs-lookup"><span data-stu-id="fc479-117">Web servers and Domain Name System (DNS) servers do not require SMB.</span></span> <span data-ttu-id="fc479-118">若要還擊使用者列舉方面的威脅，應該停用這個通訊協定。</span><span class="sxs-lookup"><span data-stu-id="fc479-118">This protocol should be disabled to counter the threat of user enumeration.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="fc479-119">停用伺服器訊息區塊將會封鎖 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 Windows 叢集服務存取遠端檔案共用。</span><span class="sxs-lookup"><span data-stu-id="fc479-119">Disabling Server Message Block will block the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or Windows Cluster service from accessing the remote file share.</span></span> <span data-ttu-id="fc479-120">如果您要或打算要執行下列其中一項，則不要停用 SMB：</span><span class="sxs-lookup"><span data-stu-id="fc479-120">Do not disable SMB if you do or plan to do one of the following:</span></span>  
> 
>  -   <span data-ttu-id="fc479-121">使用 Windows 叢集節點和檔案共用多數仲裁模式</span><span class="sxs-lookup"><span data-stu-id="fc479-121">Use Windows Cluster Node and File Share Majority Quorum mode</span></span>  
> -   <span data-ttu-id="fc479-122">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝期間指定 SMB 檔案共用做為資料目錄</span><span class="sxs-lookup"><span data-stu-id="fc479-122">Specify an SMB file share as the data directory during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation</span></span>  
> -   <span data-ttu-id="fc479-123">在 SMB 檔案共用上建立資料庫檔案</span><span class="sxs-lookup"><span data-stu-id="fc479-123">Create a database file on an SMB file share</span></span>  
  
#### <a name="to-disable-smb"></a><span data-ttu-id="fc479-124">若要停用 SMB</span><span class="sxs-lookup"><span data-stu-id="fc479-124">To disable SMB</span></span>  
  
1.  <span data-ttu-id="fc479-125">在 [開始]  功能表上，指向 [設定]  ，然後按一下 [網路和撥號連線]  。</span><span class="sxs-lookup"><span data-stu-id="fc479-125">On the **Start** menu, point to **Settings**, and then click **Network and Dial-up Connections**.</span></span>  
  
     <span data-ttu-id="fc479-126">以滑鼠右鍵按一下[網際網路方向連線]，然後按一下 [內容]  。</span><span class="sxs-lookup"><span data-stu-id="fc479-126">Right-click the Internet-facing connection, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="fc479-127">選取 **[Client for Microsoft Networks]** 核取方塊，再按一下 **[解除安裝]** 。</span><span class="sxs-lookup"><span data-stu-id="fc479-127">Select the **Client for Microsoft Networks** check box, and then click **Uninstall**.</span></span>  
  
3.  <span data-ttu-id="fc479-128">請遵照解除安裝步驟。</span><span class="sxs-lookup"><span data-stu-id="fc479-128">Follow the uninstall steps.</span></span>  
  
4.  <span data-ttu-id="fc479-129">選取 **[Microsoft 網路的檔案和印表機共用]** ，再按一下 **[解除安裝]** 。</span><span class="sxs-lookup"><span data-stu-id="fc479-129">Select **File and Printer Sharing for Microsoft Networks**, and then click **Uninstall**.</span></span>  
  
5.  <span data-ttu-id="fc479-130">請遵照解除安裝步驟。</span><span class="sxs-lookup"><span data-stu-id="fc479-130">Follow the uninstall steps.</span></span>  
  
#### <a name="to-disable-smb-on-servers-accessible-from-the-internet"></a><span data-ttu-id="fc479-131">若要在可從網際網路存取的伺服器上停用 SMB</span><span class="sxs-lookup"><span data-stu-id="fc479-131">To disable SMB on servers accessible from the Internet</span></span>  
  
-   <span data-ttu-id="fc479-132">在 [本機區域連線內容] 中，使用 [傳輸控制通訊協定/網際網路通訊協定 (TCP/IP)]  內容對話方塊來移除 [File and Printer Sharing for Microsoft Networks]  和 [Client for Microsoft Networks]  。</span><span class="sxs-lookup"><span data-stu-id="fc479-132">In the Local Area Connection properties, use the **Transmission Control Protocol/Internet Protocol (TCP/IP) properties** dialog box to remove **File and Printer Sharing for Microsoft Networks** and **Client for Microsoft Networks**.</span></span>  
  
## <a name="endpoints"></a><span data-ttu-id="fc479-133">端點</span><span class="sxs-lookup"><span data-stu-id="fc479-133">Endpoints</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fc479-134">導入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 連接的新概念；伺服器端的連接是以 [!INCLUDE[tsql](../../includes/tsql-md.md)] *「端點」* (endpoint) 的概念來表示。</span><span class="sxs-lookup"><span data-stu-id="fc479-134">introduces a new concept for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connections; the connection is represented on the server end by a [!INCLUDE[tsql](../../includes/tsql-md.md)]*endpoint*.</span></span> <span data-ttu-id="fc479-135">可對 [!INCLUDE[tsql](../../includes/tsql-md.md)] 端點授與、撤銷和拒絕權限。</span><span class="sxs-lookup"><span data-stu-id="fc479-135">Permissions can be granted, revoked, and denied for [!INCLUDE[tsql](../../includes/tsql-md.md)] endpoints.</span></span> <span data-ttu-id="fc479-136">依預設，所有使用者對端點都有存取權限，除非權限遭到系統管理員 (sysadmin) 群組的成員或端點擁有者拒絕或撤銷。</span><span class="sxs-lookup"><span data-stu-id="fc479-136">By default, all users have permissions to access an endpoint unless the permissions are denied or revoked by a member of the sysadmin group or by the endpoint owner.</span></span> <span data-ttu-id="fc479-137">GRANT、REVOKE 和 DENY ENDPOINT 語法使用的是系統管理員必須從端點之目錄檢視中取得的端點識別碼。</span><span class="sxs-lookup"><span data-stu-id="fc479-137">The GRANT, REVOKE, and DENY ENDPOINT syntax uses an endpoint ID that the administrator must get from the endpoint's catalog view.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fc479-138">安裝程式會建立所有支援之網路通訊協定的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 端點，也會針對專用管理員連接建立這類端點。</span><span class="sxs-lookup"><span data-stu-id="fc479-138">Setup creates [!INCLUDE[tsql](../../includes/tsql-md.md)] endpoints for all supported network protocols, as well as for the dedicated administrator connection.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="fc479-139">安裝程式所建立的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 端點如下：</span><span class="sxs-lookup"><span data-stu-id="fc479-139">endpoints created by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup are as follows:</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="fc479-140">本機電腦</span><span class="sxs-lookup"><span data-stu-id="fc479-140">local machine</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="fc479-141">具名管道</span><span class="sxs-lookup"><span data-stu-id="fc479-141">named pipes</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="fc479-142">預設 TCP</span><span class="sxs-lookup"><span data-stu-id="fc479-142">default TCP</span></span>  
  
 <span data-ttu-id="fc479-143">如需端點的詳細資訊，請參閱[設定 Database Engine 接聽多個 TCP 通訊埠](../../database-engine/configure-windows/configure-the-database-engine-to-listen-on-multiple-tcp-ports.md)和[端點目錄檢視 &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="fc479-143">For more information about endpoints, see [Configure the Database Engine to Listen on Multiple TCP Ports](../../database-engine/configure-windows/configure-the-database-engine-to-listen-on-multiple-tcp-ports.md) and [Endpoints Catalog Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql).</span></span>  
  
 <span data-ttu-id="fc479-144">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 網路組態的詳細資訊，請參閱《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的下列主題：</span><span class="sxs-lookup"><span data-stu-id="fc479-144">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] network configurations, see the following topic in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online:</span></span>  
  
-   [<span data-ttu-id="fc479-145">伺服器網路組態</span><span class="sxs-lookup"><span data-stu-id="fc479-145">Server Network Configuration</span></span>](../../database-engine/configure-windows/server-network-configuration.md)  
  
## <a name="see-also"></a><span data-ttu-id="fc479-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc479-146">See Also</span></span>  
 <span data-ttu-id="fc479-147">[介面區組態](../../relational-databases/security/surface-area-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="fc479-147">[Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md) </span></span>  
 <span data-ttu-id="fc479-148">[SQL Server 安裝的安全性考量](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="fc479-148">[Security Considerations for a SQL Server Installation](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md) </span></span>  
 [<span data-ttu-id="fc479-149">規劃 SQL Server 安裝</span><span class="sxs-lookup"><span data-stu-id="fc479-149">Planning a SQL Server Installation</span></span>](../../../2014/sql-server/install/planning-a-sql-server-installation.md)  
  
  
