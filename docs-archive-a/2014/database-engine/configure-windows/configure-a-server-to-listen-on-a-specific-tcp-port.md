---
title: 設定伺服器接聽特定 TCP 通訊埠 (SQL Server 組態管理員) |Microsoft Docs
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- fixed port
- static ports
- ports [SQL Server], assigning numbers
- assigning port numbers
- dynamic ports [SQL Server]
- TCP/IP [SQL Server], port numbers
ms.assetid: 2276a5ed-ae3f-4855-96d8-f5bf01890640
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4feb740910c65580e8ea3170d03481e6cb628860
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585597"
---
# <a name="configure-a-server-to-listen-on-a-specific-tcp-port-sql-server-configuration-manager"></a><span data-ttu-id="afd5d-102">設定伺服器接聽特定 TCP 通訊埠 (SQL Server 組態管理員)</span><span class="sxs-lookup"><span data-stu-id="afd5d-102">Configure a Server to Listen on a Specific TCP Port (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="afd5d-103">此主題描述如何使用 SQL Server 組態管理員，將 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體設定為在特定固定通訊埠上接聽。</span><span class="sxs-lookup"><span data-stu-id="afd5d-103">This topic describes how to configure an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] to listen on a specific fixed port by using the SQL Server Configuration Manager.</span></span> <span data-ttu-id="afd5d-104">當啟用時，預設的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體會在 TCP 通訊埠 1433 上接聽。</span><span class="sxs-lookup"><span data-stu-id="afd5d-104">If enabled, the default instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] listens on TCP port 1433.</span></span> <span data-ttu-id="afd5d-105">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 和 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 的具名執行個體是針對動態通訊埠所設定。</span><span class="sxs-lookup"><span data-stu-id="afd5d-105">Named instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssEW](../../includes/ssew-md.md)] are configured for dynamic ports.</span></span> <span data-ttu-id="afd5d-106">這表示，當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務啟動時，它們會選取可用的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="afd5d-106">This means they select an available port when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service is started.</span></span> <span data-ttu-id="afd5d-107">透過防火牆連接到具名執行個體時，設定 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 接聽特定通訊埠，如此才能在防火牆中開啟適當的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="afd5d-107">When you are connecting to a named instance through a firewall, configure the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to listen on a specific port, so that the appropriate port can be opened in the firewall.</span></span>  
  
 <span data-ttu-id="afd5d-108">如需預設 Windows 防火牆設定的詳細資訊以及影響 Database Engine、Analysis Services、Reporting Services 和 Integration Services 之 TCP 通訊埠的描述，請參閱 [設定 Windows 防火牆以允許 SQL Server 存取](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)。</span><span class="sxs-lookup"><span data-stu-id="afd5d-108">For more information about the default Windows firewall settings, and a description of the TCP ports that affect the Database Engine, Analysis Services, Reporting Services, and Integration Services, see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="afd5d-109">選取通訊埠編號時，請參閱 [http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)，以取得指派給特定應用程式的通訊埠編號清單。</span><span class="sxs-lookup"><span data-stu-id="afd5d-109">When selecting a port number, consult [http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers) for a list of port numbers that are assigned to specific applications.</span></span> <span data-ttu-id="afd5d-110">選取未指派的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="afd5d-110">Select an unassigned port number.</span></span> <span data-ttu-id="afd5d-111">如需詳細資訊，請參閱 [The default dynamic port range for TCP/IP has changed in Windows Vista and in Windows Server 2008](https://support.microsoft.com/kb/929851)(在 Windows Vista 和 Windows Server 2008 中，TCP/IP 的預設動態通訊埠範圍已變更)。</span><span class="sxs-lookup"><span data-stu-id="afd5d-111">For more information, see [The default dynamic port range for TCP/IP has changed in Windows Vista and in Windows Server 2008](https://support.microsoft.com/kb/929851).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="afd5d-112">資料庫引擎會在重新啟動之後開始接聽新的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="afd5d-112">The Database Engine begins listening on a new port when restarted.</span></span> <span data-ttu-id="afd5d-113">不過， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務會監視登錄，並在組態變更時回報新的通訊埠編號，即使資料庫引擎可能不會用到亦然。</span><span class="sxs-lookup"><span data-stu-id="afd5d-113">However the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service monitors the registry and reports the new port number as soon as the configuration is changed, even though the Database Engine might not be using it.</span></span> <span data-ttu-id="afd5d-114">重新啟動資料庫引擎可確保一致性並避免連接失敗。</span><span class="sxs-lookup"><span data-stu-id="afd5d-114">Restart the Database Engine to ensure consistency and avoid connection failures.</span></span>  
  
 <span data-ttu-id="afd5d-115">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="afd5d-115">**In This Topic**</span></span>  
  
-   <span data-ttu-id="afd5d-116">**若要使用下列項目，將伺服器設定為在特定 TCP 通訊埠上接聽：**</span><span class="sxs-lookup"><span data-stu-id="afd5d-116">**To configure a server to listen on a specific TCP port, using:**</span></span>  
  
     [<span data-ttu-id="afd5d-117">SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="afd5d-117">SQL Server Configuration Manager</span></span>](#SSMSProcedure)  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="afd5d-118">使用 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="afd5d-118">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-assign-a-tcpip-port-number-to-the-sql-server-database-engine"></a><span data-ttu-id="afd5d-119">若要為 SQL Server Database Engine 指派 TCP/IP 通訊埠編號</span><span class="sxs-lookup"><span data-stu-id="afd5d-119">To assign a TCP/IP port number to the SQL Server Database Engine</span></span>  
  
1.  <span data-ttu-id="afd5d-120">在 [SQL Server 組態管理員] 的主控台窗格中，依序展開 [SQL Server 網路組態] 和 [\<instance name> 的通訊協定]，然後按兩下 [TCP/IP]。</span><span class="sxs-lookup"><span data-stu-id="afd5d-120">In SQL Server Configuration Manager, in the console pane, expand **SQL Server Network Configuration**, expand **Protocols for \<instance name>**, and then double-click **TCP/IP**.</span></span>  
  
2.  <span data-ttu-id="afd5d-121">在 [TCP/IP 內容] 對話方塊的 [IP 位址] 索引標籤上會出現數個 IP 位址，這些 IP 位址的格式是 **IP1**、**IP2** 到 **IPAll**。</span><span class="sxs-lookup"><span data-stu-id="afd5d-121">In the **TCP/IP Properties** dialog box, on the **IP Addresses** tab, several IP addresses appear in the format **IP1**, **IP2**, up to **IPAll**.</span></span> <span data-ttu-id="afd5d-122">其中一個是供回送介面卡的 IP 位址 127.0.0.1 使用。</span><span class="sxs-lookup"><span data-stu-id="afd5d-122">One of these is for the IP address of the loopback adapter, 127.0.0.1.</span></span> <span data-ttu-id="afd5d-123">同時會出現額外的 IP 位址代表電腦上的每個 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="afd5d-123">Additional IP addresses appear for each IP Address on the computer.</span></span> <span data-ttu-id="afd5d-124">以滑鼠右鍵按一下每個位址，然後按一下 [屬性]\*\*\*\* 以識別要設定的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="afd5d-124">Right-click each address, and then click **Properties** to identify the IP address that you want to configure.</span></span>  
  
3.  <span data-ttu-id="afd5d-125">如果 **[TCP 動態通訊埠]** 對話方塊包含 **0**，代表 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 正在接聽動態通訊埠，請將 0 刪除。</span><span class="sxs-lookup"><span data-stu-id="afd5d-125">If the **TCP Dynamic Ports** dialog box contains **0**, indicating the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is listening on dynamic ports, delete the 0.</span></span>  
  
4.  <span data-ttu-id="afd5d-126">在 [IP_n_ 屬性]  區域方塊的 [TCP 通訊埠] 方塊中，鍵入您想要讓此 IP 位址接聽的連接埠號碼，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="afd5d-126">In the **IP**_n_ **Properties** area box, in the **TCP Port** box, type the port number you want this IP address to listen on, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="afd5d-127">在主控台窗格中，按一下 [SQL Server 服務]。</span><span class="sxs-lookup"><span data-stu-id="afd5d-127">In the console pane, click **SQL Server Services**.</span></span>  
  
6.  <span data-ttu-id="afd5d-128">在 [詳細資料窗格] 中，以滑鼠右鍵按一下 [SQL Server (\<instance name>)] ，然後按一下 [重新啟動]，先停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 後再重新啟動。</span><span class="sxs-lookup"><span data-stu-id="afd5d-128">In the details pane, right-click **SQL Server (**\<instance name>**)** and then click **Restart**, to stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="afd5d-129">設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接聽特定通訊埠之後，有三種方式可利用用戶端應用程式連接到特定通訊埠：</span><span class="sxs-lookup"><span data-stu-id="afd5d-129">After you have configured [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to listen on a specific port, there are three ways to connect to a specific port with a client application:</span></span>  
  
-   <span data-ttu-id="afd5d-130">執行伺服器上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務，依名稱連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="afd5d-130">Run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service on the server to connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance by name.</span></span>  
  
-   <span data-ttu-id="afd5d-131">在用戶端上建立別名，指定通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="afd5d-131">Create an alias on the client, specifying the port number.</span></span>  
  
-   <span data-ttu-id="afd5d-132">設定用戶端使用自訂連接字串進行連接。</span><span class="sxs-lookup"><span data-stu-id="afd5d-132">Program the client to connect using a custom connection string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afd5d-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afd5d-133">See Also</span></span>  
 [<span data-ttu-id="afd5d-134">建立或刪除用戶端使用的伺服器別名 &#40;SQL Server 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="afd5d-134">Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;</span></span>](create-or-delete-a-server-alias-for-use-by-a-client.md)  
  
  
