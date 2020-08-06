---
title: 使用 sqlcmd 連接至 Database Engine
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sqlcmd utility, Database Engine connections
- Named Pipes [SQL Server], sqlcmd utility
- TCP/IP [SQL Server], client protocols
- network protocols [SQL Server], sqlcmd utility
- protocols [SQL Server], sqlcmd utility
- VIA
- client protocols [SQL Server]
ms.assetid: 74b0fb71-7f8e-4171-9431-d07528532524
author: rothja
ms.author: jroth
ms.openlocfilehash: 3b409683b651e3e6508baced5eb3bc9fcc631e2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592592"
---
# <a name="connect-to-the-database-engine-with-sqlcmd"></a><span data-ttu-id="76339-102">使用 sqlcmd 連接至 Database Engine</span><span class="sxs-lookup"><span data-stu-id="76339-102">Connect to the Database Engine With sqlcmd</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="76339-103">支援使用 TCP/IP 網路通訊協定 (預設值) 和具名管道通訊協定，來進行用戶端通訊。</span><span class="sxs-lookup"><span data-stu-id="76339-103">supports client communication with the TCP/IP network protocol (the default), and the named pipes protocol.</span></span> <span data-ttu-id="76339-104">如果用戶端是連接到同一部電腦上的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體，也可以使用共用記憶體通訊協定。</span><span class="sxs-lookup"><span data-stu-id="76339-104">The shared memory protocol is also available if the client is connecting to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on the same computer.</span></span> <span data-ttu-id="76339-105">選取通訊協定有三種常見的方法。</span><span class="sxs-lookup"><span data-stu-id="76339-105">There are three common methods of selecting the protocol.</span></span> <span data-ttu-id="76339-106">**sqlcmd** 公用程式所使用的通訊協定是以下列順序決定：</span><span class="sxs-lookup"><span data-stu-id="76339-106">The protocol used by the **sqlcmd** utility is determined in the following order:</span></span>  
  
-   <span data-ttu-id="76339-107">**sqlcmd** 使用指定為連接字串一部分的通訊協定，如下所述。</span><span class="sxs-lookup"><span data-stu-id="76339-107">**sqlcmd** uses the protocol specified as part of the connection string as described below.</span></span>  
  
-   <span data-ttu-id="76339-108">如果沒有任何通訊協定指定為連接字串的一部分，則 **sqlcmd** 會使用定義為所連接之別名一部分的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="76339-108">If no protocol is specified as part the connection string, **sqlcmd** will use the protocol defined as part of the alias that it is connecting to.</span></span> <span data-ttu-id="76339-109">若要設定 **sqlcmd** 透過建立別名來使用特定的網路通訊協定，請參閱[建立或刪除用戶端使用的伺服器別名 #40;SQL Server 組態管理員&#41;](../../database-engine/configure-windows/create-or-delete-a-server-alias-for-use-by-a-client.md)。</span><span class="sxs-lookup"><span data-stu-id="76339-109">To configure **sqlcmd** to use a specific network protocol by creating an alias, see [Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/create-or-delete-a-server-alias-for-use-by-a-client.md).</span></span>  
  
-   <span data-ttu-id="76339-110">如果未使用其他方法指定通訊協定，則 **sqlcmd** 會使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員中通訊協定順序所判斷的網路通訊協定。</span><span class="sxs-lookup"><span data-stu-id="76339-110">If the protocol is not specified in some other way, **sqlcmd** will use the network protocol determined by the protocol order in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
 <span data-ttu-id="76339-111">下列範例顯示各種不同的方法，用以連接到通訊埠 1433 的預設 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體，以及假設要接聽通訊埠 1691 的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="76339-111">The following examples show various ways of connecting to the default instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] on port 1433, and named instances of [!INCLUDE[ssDE](../../includes/ssde-md.md)] presumed to be listening on port 1691.</span></span> <span data-ttu-id="76339-112">其中一部分範例使用回送網路卡的 IP 位址 (127.0.0.1)。</span><span class="sxs-lookup"><span data-stu-id="76339-112">Some of these examples use the IP address of the loopback adapter (127.0.0.1).</span></span> <span data-ttu-id="76339-113">請使用您電腦網路介面卡的 IP 位址進行測試。</span><span class="sxs-lookup"><span data-stu-id="76339-113">Test using the IP address of your computer network interface card.</span></span>  
  
 <span data-ttu-id="76339-114">指定執行個體名稱，以連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="76339-114">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by specifying the instance name:</span></span>  
  
```  
sqlcmd -S ComputerA  
sqlcmd -S ComputerA\instanceB  
```  
  
 <span data-ttu-id="76339-115">指定 IP 位址，以連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="76339-115">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by specifying the IP address:</span></span>  
  
```  
sqlcmd -S 127.0.0.1  
sqlcmd -S 127.0.0.1\instanceB  
```  
  
 <span data-ttu-id="76339-116">指定 TCP\IP 通訊埠編號，以連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="76339-116">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by specifying the TCP\IP port number:</span></span>  
  
```  
sqlcmd -S ComputerA,1433  
sqlcmd -S ComputerA,1691  
sqlcmd -S 127.0.0.1,1433  
sqlcmd -S 127.0.0.1,1691  
```  
  
### <a name="to-connect-using-tcpip"></a><span data-ttu-id="76339-117">若要使用 TCP/IP 連接</span><span class="sxs-lookup"><span data-stu-id="76339-117">To connect using TCP/IP</span></span>  
  
-   <span data-ttu-id="76339-118">使用下列常見語法進行連接：</span><span class="sxs-lookup"><span data-stu-id="76339-118">Connect using the following general syntax:</span></span>  
  
    ```  
    sqlcmd -S tcp:<computer name>,<port number>  
    ```  
  
-   <span data-ttu-id="76339-119">連接到預設執行個體：</span><span class="sxs-lookup"><span data-stu-id="76339-119">Connect to the default instance:</span></span>  
  
    ```  
    sqlcmd -S tcp:ComputerA,1433  
    sqlcmd -S tcp:127.0.0.1,1433  
    ```  
  
-   <span data-ttu-id="76339-120">連接到具名執行個體：</span><span class="sxs-lookup"><span data-stu-id="76339-120">Connect to a named instance:</span></span>  
  
    ```  
    sqlcmd -S tcp:ComputerA,1691  
    sqlcmd -S tcp:127.0.0.1,1691  
    ```  
  
### <a name="to-connect-using-named-pipes"></a><span data-ttu-id="76339-121">若要使用具名管道連接</span><span class="sxs-lookup"><span data-stu-id="76339-121">To connect using named pipes</span></span>  
  
-   <span data-ttu-id="76339-122">使用下列一般語法的其中之一連接：</span><span class="sxs-lookup"><span data-stu-id="76339-122">Connect using one of the following general syntax:</span></span>  
  
    ```  
    sqlcmd -S np:\\<computer name>\<pipe name>  
    ```  
  
-   <span data-ttu-id="76339-123">連接到預設執行個體：</span><span class="sxs-lookup"><span data-stu-id="76339-123">Connect to the default instance:</span></span>  
  
    ```  
    sqlcmd -S np:\\ComputerA\pipe\sql\query  
    sqlcmd -S np:\\127.0.0.1\pipe\sql\query  
    ```  
  
-   <span data-ttu-id="76339-124">連接到具名執行個體：</span><span class="sxs-lookup"><span data-stu-id="76339-124">Connect to a named instance instance:</span></span>  
  
    ```  
    sqlcmd -S np:\\ComputerA\pipe\MSSQL$<instancename>\sql\query  
    sqlcmd -S np:\\127.0.0.1\pipe\MSSQL$<instancename>\sql\query  
    ```  
  
### <a name="to-connect-using-shared-memory-a-local-procedure-call-from-a-client-on-the-server"></a><span data-ttu-id="76339-125">若要使用伺服器上用戶端的共用記憶體 (本機程序呼叫) 連接</span><span class="sxs-lookup"><span data-stu-id="76339-125">To connect using shared memory (a local procedure call) from a client on the server</span></span>  
  
-   <span data-ttu-id="76339-126">使用下列一般語法的其中之一連接：</span><span class="sxs-lookup"><span data-stu-id="76339-126">Connect using one of the following general syntax:</span></span>  
  
    ```  
    sqlcmd -S lpc:<computer name>  
    ```  
  
-   <span data-ttu-id="76339-127">連接到預設執行個體：</span><span class="sxs-lookup"><span data-stu-id="76339-127">Connect to the default instance:</span></span>  
  
    ```  
    sqlcmd -S lpc:ComputerA  
    ```  
  
-   <span data-ttu-id="76339-128">連接到具名執行個體：</span><span class="sxs-lookup"><span data-stu-id="76339-128">Connect to a named instance:</span></span>  
  
    ```  
    sqlcmd -S lpc:ComputerA\<instancename>  
    ```  
  
  
