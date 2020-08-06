---
title: 使用具名管道建立有效的連接字串 |Microsoft Docs
description: 瞭解如何在使用具名管道通訊協定連接到 SQL Server 的實例時，建立有效的連接字串。 查看有效管道名稱的範例。
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine], named pipes
- pipes [SQL Server]
- pipes [SQL Server], connecting to
- aliases [SQL Server], named pipes
- Named Pipes [SQL Server], connection strings
ms.assetid: 90930ff2-143b-4651-8ae3-297103600e4f
author: rothja
ms.author: jroth
ms.openlocfilehash: 10f3e1d01e9e5b7b1d1c0d1bb822bf233ceee636
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595345"
---
# <a name="creating-a-valid-connection-string-using-named-pipes"></a><span data-ttu-id="9e1e9-104">使用具名管道建立有效的連接字串</span><span class="sxs-lookup"><span data-stu-id="9e1e9-104">Creating a Valid Connection String Using Named Pipes</span></span>
  <span data-ttu-id="9e1e9-105">除非使用者變更，否則當的預設實例 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接聽具名管道通訊協定時，它會使用 `\\.\pipe\sql\query` 做為管道名稱。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-105">Unless changed by the user, when the default instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] listens on the named pipes protocol, it uses `\\.\pipe\sql\query` as the pipe name.</span></span> <span data-ttu-id="9e1e9-106">其中句點表示該電腦為本機電腦， `pipe` 表示連接是具名管道，而 `sql\query` 則是管道的名稱。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-106">The period indicates that the computer is the local computer, `pipe` indicates that the connection is a named pipe, and `sql\query` is the name of the pipe.</span></span> <span data-ttu-id="9e1e9-107">若要連接到預設管道，別名必須用 `\\<computer_name>\pipe\sql\query` 做為管道名稱。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-107">To connect to the default pipe, the alias must have `\\<computer_name>\pipe\sql\query` as the pipe name.</span></span> <span data-ttu-id="9e1e9-108">若將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設定為接聽其他管道，則管道名稱必須使用該管道。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-108">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been configured to listen on a different pipe, the pipe name must use that pipe.</span></span> <span data-ttu-id="9e1e9-109">例如，如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以 `\\.\pipe\unit\app` 做為管道，則別名必須以 `\\<computer_name>\pipe\unit\app` 做為管道名稱。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-109">For instance, if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is using `\\.\pipe\unit\app` as the pipe, the alias must use `\\<computer_name>\pipe\unit\app` as the pipe name.</span></span>  
  
 <span data-ttu-id="9e1e9-110">若要建立有效的管道名稱，您必須：</span><span class="sxs-lookup"><span data-stu-id="9e1e9-110">To create a valid pipe name, you must:</span></span>  
  
-   <span data-ttu-id="9e1e9-111">指定 **別名名稱**。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-111">Specify an **Alias Name**.</span></span>  
  
-   <span data-ttu-id="9e1e9-112">選取 **[具名管道]** 做為 **[通訊協定]**。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-112">Select **Named Pipes** as the **Protocol**.</span></span>  
  
-   <span data-ttu-id="9e1e9-113">輸入 **[管道名稱]**。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-113">Enter the **Pipe Name**.</span></span> <span data-ttu-id="9e1e9-114">或者，您可以將 **[管道名稱]** 留白，在您指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [通訊協定] **與** [伺服器] **之後，** 組態管理員便會完成適當的管道名稱。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-114">Alternatively, you can leave **Pipe Name** blank and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager will complete the appropriate pipe name after you specify the **Protocol** and **Server**</span></span>  
  
-   <span data-ttu-id="9e1e9-115">指定 **[伺服器]**。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-115">Specify a **Server**.</span></span> <span data-ttu-id="9e1e9-116">對於具名執行個體，您可以提供伺服器名稱與執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-116">For a named instance you can provide a server name and instance name.</span></span>  
  
 <span data-ttu-id="9e1e9-117">在連接時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 元件會從登錄中讀取指定之別名名稱的伺服器、通訊協定和管道名稱值，並以或格式建立管道名稱 `np:\\<computer_name>\pipe\<pipename>` `np:\\<IPAddress>\pipe\<pipename>` 。若為已命名的實例，預設的管道名稱是 `\\<computer_name>\pipe\MSSQL$<instance_name>\sql\query` 。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-117">At the time of connection, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client component reads the server, protocol, and pipe name values from the registry for the specified alias name, and creates a pipe name in the format `np:\\<computer_name>\pipe\<pipename>` or `np:\\<IPAddress>\pipe\<pipename>`.For a named instance, the default pipe name is `\\<computer_name>\pipe\MSSQL$<instance_name>\sql\query`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e1e9-118">根據預設， [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 防火牆會關閉通訊埠 445。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-118">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Firewall closes port 445 by default.</span></span> <span data-ttu-id="9e1e9-119">由於 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是透過通訊埠 445 來進行通訊，因此如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設定為使用具名管道來接聽內送的用戶端連接，您就必須重新開啟該連接埠。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-119">Because [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] communicates over port 445, you must reopen the port if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to listen for incoming client connections using named pipes.</span></span> <span data-ttu-id="9e1e9-120">如需設定防火牆的相關資訊，請參閱《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜如何：設定防火牆供 SQL Server 存取＞，或請檢閱您的防火牆文件集。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-120">For information on configuring a firewall, see "How to: Configure a Firewall for SQL Server Access" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online or review your firewall documentation.</span></span>  
  
## <a name="connecting-to-the-local-server"></a><span data-ttu-id="9e1e9-121">連接到本機伺服器</span><span class="sxs-lookup"><span data-stu-id="9e1e9-121">Connecting to the Local Server</span></span>  
 <span data-ttu-id="9e1e9-122">連接到與用戶端在同一部電腦上執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，可以使用 `(local)`做為伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-122">When connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the same computer as the client, you can use `(local)`as the server name.</span></span> <span data-ttu-id="9e1e9-123">但不建議您使用 `(local)` ，因為這會造成混淆，但是若確實知道用戶端正在預期的電腦上執行，這就很有用。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-123">Using `(local)` is not encouraged because it leads to ambiguity; however it can be useful when the client is known to be running on the intended computer.</span></span> <span data-ttu-id="9e1e9-124">例如，為行動式、非連接的使用者 (例如銷售人員) 建立應用程式 (亦即 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將會在膝上型電腦上執行並儲存專案資料) 時，連接到 (local) 的用戶端一律會連接到在膝上型電腦上執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-124">For instance, when creating an application for mobile disconnected users, such as a sales force, where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will run on laptop computers and store project data, a client connecting to (local) would always connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the laptop.</span></span> <span data-ttu-id="9e1e9-125">可以使用 `localhost` 或句點 (.) 來取代 `(local)`。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-125">The word `localhost` or a period (.) can be used in place of `(local)`.</span></span>  
  
## <a name="verifying-your-connection-protocol"></a><span data-ttu-id="9e1e9-126">驗證您的連接通訊協定</span><span class="sxs-lookup"><span data-stu-id="9e1e9-126">Verifying Your Connection Protocol</span></span>  
 <span data-ttu-id="9e1e9-127">下列查詢會傳回目前連接所使用的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-127">The following query will return the protocol used for the current connection.</span></span>  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a><span data-ttu-id="9e1e9-128">範例</span><span class="sxs-lookup"><span data-stu-id="9e1e9-128">Examples</span></span>  
 <span data-ttu-id="9e1e9-129">使用伺服器名稱連接到預設管道：</span><span class="sxs-lookup"><span data-stu-id="9e1e9-129">Connecting by server name to the default pipe:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          <blank>  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 <span data-ttu-id="9e1e9-130">使用 IP 位址連接到預設管道：</span><span class="sxs-lookup"><span data-stu-id="9e1e9-130">Connecting by IP Address to the default pipe:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          <leave blank>  
Protocol           Named Pipes  
Server             <IPAddress>  
  
```  
  
 <span data-ttu-id="9e1e9-131">使用伺服器名稱連接到非預設管道：</span><span class="sxs-lookup"><span data-stu-id="9e1e9-131">Connecting by server name to a non-default pipe:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          \\<servername>\pipe\unit\app  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 <span data-ttu-id="9e1e9-132">使用伺服器名稱連接到具名執行個體：</span><span class="sxs-lookup"><span data-stu-id="9e1e9-132">Connecting by server name to a named instance:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          \\<servername>\pipe\MSSQL$<instancename>\SQL\query  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 <span data-ttu-id="9e1e9-133">使用 `localhost`連接到本機電腦：</span><span class="sxs-lookup"><span data-stu-id="9e1e9-133">Connecting to the local computer using `localhost`:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          <blank>  
Protocol           Named Pipes  
Server             localhost  
  
```  
  
 <span data-ttu-id="9e1e9-134">使用句點連接到本機電腦：</span><span class="sxs-lookup"><span data-stu-id="9e1e9-134">Connecting to the local computer using a period:</span></span>  
  
```  
Alias Name         <serveralias>  
Pipe Name          <left blank>  
Protocol           Named Pipes  
Server             .  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="9e1e9-135">若要指定網路通訊協定做為 **sqlcmd** 參數，請參閱「如何：《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜如何：使用 sqlcmd.exe 連接至 Database Engine＞。</span><span class="sxs-lookup"><span data-stu-id="9e1e9-135">To specify the network protocol as a **sqlcmd** parameter, see "How to: Connect to the Database Engine Using sqlcmd.exe" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e1e9-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e1e9-136">See Also</span></span>  
 <span data-ttu-id="9e1e9-137">[使用共用記憶體通訊協定建立有效的連接字串](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="9e1e9-137">[Creating a Valid Connection String Using Shared Memory Protocol](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md) </span></span>  
 <span data-ttu-id="9e1e9-138">[使用 TCP IP 建立有效的連接字串](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md) </span><span class="sxs-lookup"><span data-stu-id="9e1e9-138">[Creating a Valid Connection String Using TCP IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md) </span></span>  
 [<span data-ttu-id="9e1e9-139">選擇網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="9e1e9-139">Choosing a Network Protocol</span></span>](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
