---
title: 設定接聽多個 TCP 通訊埠的資料庫引擎 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- ports [SQL Server], multiple
- TDS
- listen on multiple ports
- endpoints [SQL Server], TDS
- adding ports
- tabular data stream
- multiple ports
ms.assetid: 8e955033-06ef-403f-b813-3d8241b62f1f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ab803bcaa5ab6b6187c1a994abef02f81ae105c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592242"
---
# <a name="configure-the-database-engine-to-listen-on-multiple-tcp-ports"></a><span data-ttu-id="1e566-102">設定 Database Engine 接聽多個 TCP 通訊埠</span><span class="sxs-lookup"><span data-stu-id="1e566-102">Configure the Database Engine to Listen on Multiple TCP Ports</span></span>
  <span data-ttu-id="1e566-103">此主題描述如何使用 SQL Server 組態管理員，在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中設定 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 於多個 TCP 通訊埠上接聽。</span><span class="sxs-lookup"><span data-stu-id="1e566-103">This topic describes how to configure the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to listen on multiple TCP ports in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="1e566-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]啟用 TCP/IP 時， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 將會在由 IP 位址及 TCP 通訊埠編號構成的連接點上接聽內送連接。下列程序會建立表格式資料流 (TDS) 端點，因此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將可以在其他 TCP 通訊埠上接聽。</span><span class="sxs-lookup"><span data-stu-id="1e566-104">When TCP/IP is enabled for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssDE](../../includes/ssde-md.md)] will listen for incoming connections on a connection point consisting of an IP address and TCP port number.The following procedures create a tabular data stream (TDS) endpoint, so that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will listen on an additional TCP port.</span></span>  
  
 <span data-ttu-id="1e566-105">必須建立第二個 TDS 端點的原因包括：</span><span class="sxs-lookup"><span data-stu-id="1e566-105">Possible reasons to create a second TDS endpoint include:</span></span>  
  
-   <span data-ttu-id="1e566-106">設定防火牆以對特定子網路的本機用戶端電腦，限制存取預設端點。</span><span class="sxs-lookup"><span data-stu-id="1e566-106">Increase security by configuring the firewall to restrict access to the default endpoint to local client computers on a specific subnet.</span></span> <span data-ttu-id="1e566-107">建立該防火牆對網際網路公開的新端點，以及對伺服器支援團隊限制連接此端點的權限，為您的支援團隊維護 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的網際網路存取。</span><span class="sxs-lookup"><span data-stu-id="1e566-107">Maintain Internet access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for your support team by creating a new endpoint that the firewall exposes to the Internet, and restricting connection rights to this endpoint to your server support team.</span></span>  
  
-   <span data-ttu-id="1e566-108">在使用非統一記憶體存取 (NUMA) 時，相似化特定處理器的連接。</span><span class="sxs-lookup"><span data-stu-id="1e566-108">Affinitizing connections to specific processors when using Non-Uniform Memory Access (NUMA).</span></span>  
  
 <span data-ttu-id="1e566-109">設定 TDS 端點包含下列步驟，您能夠以任意順序來完成：</span><span class="sxs-lookup"><span data-stu-id="1e566-109">Configuring a TDS endpoint consists of the following steps, which can be done in any order:</span></span>  
  
-   <span data-ttu-id="1e566-110">建立 TCP 通訊端的 TDS 端點，然後還原預設端點的存取權 (如有必要)。</span><span class="sxs-lookup"><span data-stu-id="1e566-110">Create the TDS endpoint for the TCP port, and restore access to the default endpoint if appropriate.</span></span>  
  
-   <span data-ttu-id="1e566-111">對想要的伺服器主體授與端點存取權。</span><span class="sxs-lookup"><span data-stu-id="1e566-111">Grant access to the endpoint to the desired server principals.</span></span>  
  
-   <span data-ttu-id="1e566-112">指定選取 IP 位址的 TCP 通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="1e566-112">Specify the TCP port number for the selected IP address.</span></span>  
  
 <span data-ttu-id="1e566-113">如需預設 Windows 防火牆設定的詳細資訊以及影響 Database Engine、Analysis Services、Reporting Services 和 Integration Services 之 TCP 通訊埠的描述，請參閱 [設定 Windows 防火牆以允許 SQL Server 存取](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="1e566-113">For more information about the default Windows firewall settings, and a description of the TCP ports that affect the Database Engine, Analysis Services, Reporting Services, and Integration Services, see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-create-a-tds-endpoint"></a><span data-ttu-id="1e566-114">建立 TDS 端點</span><span class="sxs-lookup"><span data-stu-id="1e566-114">To create a TDS endpoint</span></span>  
  
-   <span data-ttu-id="1e566-115">發出以下陳述式以為伺服器上所有可用的 TCP 位址，為通訊埠 1500 建立一個稱為 **CustomConnection** 的端點。</span><span class="sxs-lookup"><span data-stu-id="1e566-115">Issue the following statement to create an endpoint named **CustomConnection** for port 1500 for all available TCP addresses on the server.</span></span>  
  
    ```  
    USE master;  
    GO  
    CREATE ENDPOINT [CustomConnection]  
    STATE = STARTED  
    AS TCP  
       (LISTENER_PORT = 1500, LISTENER_IP =ALL)  
    FOR TSQL() ;  
    GO  
    ```  
  
 <span data-ttu-id="1e566-116">當您建立新的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 端點時，就會撤銷預設 TDS 端點的 **public** 連接權限。</span><span class="sxs-lookup"><span data-stu-id="1e566-116">When you create a new [!INCLUDE[tsql](../../includes/tsql-md.md)] endpoint, connect permissions for **public** are revoked for the default TDS endpoint.</span></span> <span data-ttu-id="1e566-117">如果預設端點需要存取 **public** 群組，請使用 `GRANT CONNECT ON ENDPOINT::[TSQL Default TCP] to [public];` 陳述式重新套用此權限。</span><span class="sxs-lookup"><span data-stu-id="1e566-117">If access to the **public** group is needed for the default endpoint, reapply this permission by using the `GRANT CONNECT ON ENDPOINT::[TSQL Default TCP] to [public];` statement.</span></span>  
  
#### <a name="to-grant-access-to-the-endpoint"></a><span data-ttu-id="1e566-118">授與端點的存取權</span><span class="sxs-lookup"><span data-stu-id="1e566-118">To grant access to the endpoint</span></span>  
  
-   <span data-ttu-id="1e566-119">發出以下陳述式以對公司網域的 SQLSupport，授與 **CustomConnection** 端點的存取權。</span><span class="sxs-lookup"><span data-stu-id="1e566-119">Issue the following statement to grant access to the **CustomConnection** endpoint to the SQLSupport group in the corp domain.</span></span>  
  
    ```  
    GRANT CONNECT ON ENDPOINT::[CustomConnection] to [corp\SQLSupport] ;  
    GO  
    ```  
  
#### <a name="to-configure-the-sql-server-database-engine-to-listen-on-an-additional-tcp-port"></a><span data-ttu-id="1e566-120">設定 SQL Server Database Engine 接聽其他 TCP 通訊埠。</span><span class="sxs-lookup"><span data-stu-id="1e566-120">To configure the SQL Server Database Engine to listen on an additional TCP port</span></span>  
  
1.  <span data-ttu-id="1e566-121">在 SQL Server 組態管理員中，展開 [SQL Server 網路組態]，然後按一下 [<執行個體名稱> 的通訊協定]。</span><span class="sxs-lookup"><span data-stu-id="1e566-121">In SQL Server Configuration Manager, expand **SQL Server Network Configuration**, and then click **Protocols for**_<instance_name>_.</span></span>  
  
2.  <span data-ttu-id="1e566-122">展開 [<執行個體名稱> 的通訊協定]，然後按一下 [TCP/IP]。</span><span class="sxs-lookup"><span data-stu-id="1e566-122">Expand **Protocols for**_<instance_name>_, and then click **TCP/IP**.</span></span>  
  
3.  <span data-ttu-id="1e566-123">在右窗格中，以滑鼠右鍵按一下您要啟用之已停用的 IP 位址，然後按一下 [啟用]。</span><span class="sxs-lookup"><span data-stu-id="1e566-123">In the right pane, right-click each disabled IP address that you want to enable, and then click **Enable**.</span></span>  
  
4.  <span data-ttu-id="1e566-124">以滑鼠右鍵按一下 [IPAll]，然後按一下 [內容]。</span><span class="sxs-lookup"><span data-stu-id="1e566-124">Right-click **IPAll**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="1e566-125">在 **[TCP 通訊埠]** 方塊中，輸入想要 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 接聽的通訊埠，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="1e566-125">In the **TCP Port** box, type the ports that you want the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to listen on, separated by commas.</span></span> <span data-ttu-id="1e566-126">在我們的範例中，如果列出預設通訊埠1433，請輸入 `,1500` ，讓方塊讀取 `1433,1500` ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="1e566-126">In our example, if the default port 1433 is listed, type `,1500` so the box reads `1433,1500`, and then click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1e566-127">如果未啟用所有 IP 位址上的通訊埠，請只有在想要的位址，以內容方塊設定其他通訊埠。</span><span class="sxs-lookup"><span data-stu-id="1e566-127">If you are not enabling the port on all IP addresses, configure the additional port in the property box for only for the desired address.</span></span> <span data-ttu-id="1e566-128">接著在主控台窗格中，以滑鼠右鍵按一下 [TCP/IP]，按一下 [內容]，然後在 [全部接聽] 方塊中選取 [否]。</span><span class="sxs-lookup"><span data-stu-id="1e566-128">Then, in the console pane, right-click **TCP/IP**, click **Properties**, and in the **Listen All** box, select **No**.</span></span>  
  
6.  <span data-ttu-id="1e566-129">在左窗格中，按一下 **[SQL Server 服務]** 。</span><span class="sxs-lookup"><span data-stu-id="1e566-129">In the left pane, click **SQL Server Services**.</span></span>  
  
7.  <span data-ttu-id="1e566-130">在右窗格中，以滑鼠右鍵按一下 [SQL Server <執行個體名稱>]，然後按一下 [重新啟動]。</span><span class="sxs-lookup"><span data-stu-id="1e566-130">In the right pane, right-click **SQL Server**_<instance_name>_, and then click **Restart**.</span></span>  
  
     <span data-ttu-id="1e566-131">當 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 重新啟動時，錯誤記錄檔將會列出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正在接聽的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="1e566-131">When the [!INCLUDE[ssDE](../../includes/ssde-md.md)] restarts, the Error log will list the ports on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is listening.</span></span>  
  
#### <a name="to-connect-to-the-new-endpoint"></a><span data-ttu-id="1e566-132">連接新的端點</span><span class="sxs-lookup"><span data-stu-id="1e566-132">To connect to the new endpoint</span></span>  
  
-   <span data-ttu-id="1e566-133">使用信任連接，並假設使用者是 [corp\SQLSupport] 群組的成員，在稱為 ACCT 的伺服器上發出以下陳述式，連接 SQL Server 之預設執行個體的 **CustomConnection** 端點。</span><span class="sxs-lookup"><span data-stu-id="1e566-133">Issue the following statement to connect to the **CustomConnection** endpoint of the default instance of SQL Server on the server named ACCT, using a trusted connection, and assuming the user is a member of the [corp\SQLSupport] group.</span></span>  
  
    ```  
    sqlcmd -SACCT,1500  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1e566-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e566-134">See Also</span></span>  
 <span data-ttu-id="1e566-135">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1e566-135">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="1e566-136">[DROP ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1e566-136">[DROP ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="1e566-137">[GRANT 端點權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1e566-137">[GRANT Endpoint Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql) </span></span>  
 [<span data-ttu-id="1e566-138">將 TCP/IP 通訊埠對應到 NUMA 節點 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1e566-138">Map TCP IP Ports to NUMA Nodes &#40;SQL Server&#41;</span></span>](map-tcp-ip-ports-to-numa-nodes-sql-server.md)  
  
  
