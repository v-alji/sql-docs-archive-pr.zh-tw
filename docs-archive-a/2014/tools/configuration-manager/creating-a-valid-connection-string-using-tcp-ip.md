---
title: 使用 TCP IP 建立有效的連接字串 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine]
- ports [SQL Server], connecting to
- TCP/IP [SQL Server], connection strings
- connection strings [Database Engine], TCP/IP
- aliases [SQL Server], TCP/IP
ms.assetid: ee5dbc2c-1fc6-42bd-bdf5-efa792557934
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5f761fa86ec4ed09c13bf4807489754c10b979ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595343"
---
# <a name="creating-a-valid-connection-string-using-tcp-ip"></a><span data-ttu-id="0b78b-102">使用 TCP IP 建立有效的連接字串</span><span class="sxs-lookup"><span data-stu-id="0b78b-102">Creating a Valid Connection String Using TCP IP</span></span>
  <span data-ttu-id="0b78b-103">若要使用 TCP/IP 建立有效的連接字串，您必須：</span><span class="sxs-lookup"><span data-stu-id="0b78b-103">To create a valid connection string using TCP/IP, you must:</span></span>  
  
-   <span data-ttu-id="0b78b-104">指定 **別名名稱**。</span><span class="sxs-lookup"><span data-stu-id="0b78b-104">Specify an **Alias Name**.</span></span>  
  
-   <span data-ttu-id="0b78b-105">針對 **[伺服器]** ，輸入您可以使用 **PING** 公用程式來連接的伺服器名稱，或是可以使用 **PING** 公用程式來連接的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="0b78b-105">For the **Server**, enter either a server name to which you can connect using the **PING** utility, or an IP address to which you can connect using the **PING** utility.</span></span> <span data-ttu-id="0b78b-106">針對具名執行個體，請附加執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="0b78b-106">For a named instance append the instance name.</span></span>  
  
-   <span data-ttu-id="0b78b-107">在 **[通訊協定]** 中指定 **[TCP/IP]** 。</span><span class="sxs-lookup"><span data-stu-id="0b78b-107">Specify **TCP/IP** for the **Protocol**.</span></span>  
  
-   <span data-ttu-id="0b78b-108">(選擇性) 在 **[通訊埠編號]** 中輸入通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="0b78b-108">Optionally, enter a port number for the **Port No**.</span></span> <span data-ttu-id="0b78b-109">預設值為 1433，也就是伺服器上 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 預設執行個體的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="0b78b-109">The default is 1433, which is the port number of the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on a server.</span></span> <span data-ttu-id="0b78b-110">若要連接到具名執行個體或未接聽通訊埠 1433 的預設執行個體，您必須提供通訊埠編號，或是啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務。</span><span class="sxs-lookup"><span data-stu-id="0b78b-110">To connect to a named instance or a default instance that is not listening on port 1433, you must provide the port number, or start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span> <span data-ttu-id="0b78b-111">如需設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務的資訊，請參閱 [SQL Server Browser 服務](../../../2014/tools/configuration-manager/sql-server-browser-service.md)。</span><span class="sxs-lookup"><span data-stu-id="0b78b-111">For information on configuring the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service, see [SQL Server Browser Service](../../../2014/tools/configuration-manager/sql-server-browser-service.md).</span></span>  
  
 <span data-ttu-id="0b78b-112">在連接時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 元件會從登錄中讀取指定之別名名稱的伺服器、通訊協定與通訊埠值，並以 `tcp:<servername>[\<instancename>],<port>` 或 `tcp:<IPAddress>[\<instancename>],<port>`格式建立連接字串。</span><span class="sxs-lookup"><span data-stu-id="0b78b-112">At the time of connection, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client component reads the server, protocol, and port values from the registry for the specified alias name, and creates a connection string in the format `tcp:<servername>[\<instancename>],<port>` or `tcp:<IPAddress>[\<instancename>],<port>`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0b78b-113">根據預設， [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 防火牆會關閉通訊埠 1433。</span><span class="sxs-lookup"><span data-stu-id="0b78b-113">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Firewall closes port 1433 by default.</span></span> <span data-ttu-id="0b78b-114">由於 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是透過連接埠 1433 來進行通訊，因此如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設定為使用 TCP/IP 來接聽內送的用戶端連接，您就必須重新開啟該通訊埠。</span><span class="sxs-lookup"><span data-stu-id="0b78b-114">Because [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] communicates over port 1433, you must reopen the port if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to listen for incoming client connections using TCP/IP.</span></span> <span data-ttu-id="0b78b-115">如需設定防火牆的相關資訊，請參閱《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜如何：設定防火牆供 SQL Server 存取＞，或請檢閱您的防火牆文件集。</span><span class="sxs-lookup"><span data-stu-id="0b78b-115">For information on configuring a firewall, see "How to: Configure a Firewall for SQL Server Access" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online or review your firewall documentation.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0b78b-116">和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 完整支援網際網路通訊協定第 4 版 (IPv4) 與網際網路通訊協定第 6 版 (IPv6)。</span><span class="sxs-lookup"><span data-stu-id="0b78b-116">and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client fully support both Internet Protocol version 4 (IPv4) and Internet Protocol version 6 (IPv6).</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0b78b-117">組態管理員可以接受 IPv4 和 IPv6 格式的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="0b78b-117">Configuration Manager accepts both IPv4 and IPv6 formats for IP addresses.</span></span> <span data-ttu-id="0b78b-118">如需有關 IPv6 的資訊，請參閱《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜使用 IPv6 連接＞。</span><span class="sxs-lookup"><span data-stu-id="0b78b-118">For information on IPv6, see "Connecting Using IPv6" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="connecting-to-the-local-server"></a><span data-ttu-id="0b78b-119">連接到本機伺服器</span><span class="sxs-lookup"><span data-stu-id="0b78b-119">Connecting to the Local Server</span></span>  
 <span data-ttu-id="0b78b-120">連接到與用戶端在同一部電腦上執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，可以使用 `(local)` 做為伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="0b78b-120">When connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the same computer as the client, you can use `(local)` as the server name.</span></span> <span data-ttu-id="0b78b-121">但不建議這麼做，因為會造成模糊不清，但是若確實知道用戶端正在預期的電腦上執行，這就很有用。</span><span class="sxs-lookup"><span data-stu-id="0b78b-121">This is not encouraged as it leads to ambiguity, however it can be useful when the client is known to be running on the intended computer.</span></span> <span data-ttu-id="0b78b-122">例如，為行動式、非連接的使用者 (例如銷售人員) 建立應用程式 (亦即 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將會在膝上型電腦上執行並儲存專案資料) 時，連接到 `(local)` 的用戶端一律會連接到在膝上型電腦上執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0b78b-122">For instance, when creating an application for mobile disconnected users, such as a sales force, where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will run on laptop computers and store project data, a client connecting to `(local)` would always connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the laptop.</span></span> <span data-ttu-id="0b78b-123">可以使用字詞 `localhost` 或句點 ( **.** ) 來取代 `(local)`。</span><span class="sxs-lookup"><span data-stu-id="0b78b-123">The word `localhost` or a period (**.**) can be used in place of `(local)`.</span></span>  
  
## <a name="verifying-your-connection-protocol"></a><span data-ttu-id="0b78b-124">驗證您的連接通訊協定</span><span class="sxs-lookup"><span data-stu-id="0b78b-124">Verifying Your Connection Protocol</span></span>  
 <span data-ttu-id="0b78b-125">下列查詢會傳回目前連接所使用的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="0b78b-125">The following query returns the protocol used for the current connection.</span></span>  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a><span data-ttu-id="0b78b-126">範例</span><span class="sxs-lookup"><span data-stu-id="0b78b-126">Examples</span></span>  
 <span data-ttu-id="0b78b-127">使用伺服器名稱連接：</span><span class="sxs-lookup"><span data-stu-id="0b78b-127">Connecting by server name:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <servername>  
  
```  
  
 <span data-ttu-id="0b78b-128">使用伺服器名稱連接到具名執行個體：</span><span class="sxs-lookup"><span data-stu-id="0b78b-128">Connecting by server name to a named instance:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <servername>\<instancename>  
  
```  
  
 <span data-ttu-id="0b78b-129">使用伺服器名稱來連接指定的通訊埠：</span><span class="sxs-lookup"><span data-stu-id="0b78b-129">Connecting by server name to a specified port:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <port>  
Protocol           TCP/IP  
Server             <servername>  
  
```  
  
 <span data-ttu-id="0b78b-130">使用 IP 位址來連接：</span><span class="sxs-lookup"><span data-stu-id="0b78b-130">Connecting by IP address:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <IPAddress>  
  
```  
  
 <span data-ttu-id="0b78b-131">使用 IP 位址連接到具名執行個體：</span><span class="sxs-lookup"><span data-stu-id="0b78b-131">Connecting by IP address to a named instance:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <IPAddress>\<instancename>  
  
```  
  
 <span data-ttu-id="0b78b-132">使用 IP 位址連接到指定的通訊埠：</span><span class="sxs-lookup"><span data-stu-id="0b78b-132">Connecting by IP address to a specified port:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <port number>  
Protocol           TCP/IP  
Server             <IPAddress>  
  
```  
  
 <span data-ttu-id="0b78b-133">使用 `(local)`連接到本機電腦：</span><span class="sxs-lookup"><span data-stu-id="0b78b-133">Connecting to the local computer using `(local)`:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             (local)  
  
```  
  
 <span data-ttu-id="0b78b-134">使用 `localhost`連接到本機電腦：</span><span class="sxs-lookup"><span data-stu-id="0b78b-134">Connecting to the local computer using `localhost`:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             localhost  
  
```  
  
 <span data-ttu-id="0b78b-135">連接到本機電腦 `localhost`上的具名執行個體：</span><span class="sxs-lookup"><span data-stu-id="0b78b-135">Connecting to a named instance on the local computer `localhost`:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             localhost\<instancename>  
  
```  
  
 <span data-ttu-id="0b78b-136">使用句點連接到本機電腦：</span><span class="sxs-lookup"><span data-stu-id="0b78b-136">Connecting to the local computer using a period:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             .  
  
```  
  
 <span data-ttu-id="0b78b-137">使用句點連接到本機電腦上的具名執行個體：</span><span class="sxs-lookup"><span data-stu-id="0b78b-137">Connecting to a named instance on the local computer using a period:</span></span>  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             .\<instancename>  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="0b78b-138">如需指定網路通訊協定作為 **sqlcmd** 參數的資訊，請參閱《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜如何：使用 sqlcmd.exe 連接到 Database Engine＞。</span><span class="sxs-lookup"><span data-stu-id="0b78b-138">For information on specifying the network protocol as a **sqlcmd** parameter, see "How to: Connect to the Database Engine Using sqlcmd.exe" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b78b-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b78b-139">See Also</span></span>  
 <span data-ttu-id="0b78b-140">[使用共用記憶體通訊協定建立有效的連接字串](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="0b78b-140">[Creating a Valid Connection String Using Shared Memory Protocol](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md) </span></span>  
 <span data-ttu-id="0b78b-141">[使用具名管道建立有效的連接字串](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md) </span><span class="sxs-lookup"><span data-stu-id="0b78b-141">[Creating a Valid Connection String Using Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md) </span></span>  
 [<span data-ttu-id="0b78b-142">選擇網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="0b78b-142">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
