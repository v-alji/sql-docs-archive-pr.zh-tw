---
title: 使用或不使用網路執行 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- verifying Server service has been started
- net start [SQL Server]
- command prompt [SQL Server], connections
- SQL Server services, networks
- status information [SQL Server], Server service
- running SQL Server
- networking [SQL Server], SQL Server with or without
- services [SQL Server], networks
- starting Server service
- SQL Server, running
ms.assetid: 54eac961-5c7a-4481-982d-f93a64b5c2f4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a80e7e4d42f322bc42d0c67c57e3a1f9bddb87a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596269"
---
# <a name="run-sql-server-with-or-without-a-network"></a><span data-ttu-id="2d1a0-102">使用 (或不使用) 網路執行 SQL Server</span><span class="sxs-lookup"><span data-stu-id="2d1a0-102">Run SQL Server With or Without a Network</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="2d1a0-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可在網路上執行，也可在不使用網路的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="2d1a0-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can run on a network, or it can function without a network.</span></span>  
  
## <a name="running-sql-server-on-a-network"></a><span data-ttu-id="2d1a0-104">在網路上執行 SQL Server</span><span class="sxs-lookup"><span data-stu-id="2d1a0-104">Running SQL Server on a Network</span></span>  
 <span data-ttu-id="2d1a0-105">若要讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 能夠透過網路通訊，就必須執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="2d1a0-105">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to communicate over a network, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service must be running.</span></span> <span data-ttu-id="2d1a0-106">根據預設， [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 會自行啟動內建的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="2d1a0-106">By default, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows automatically starts the built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="2d1a0-107">若要查看是否已啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務，可在命令提示字元中輸入：</span><span class="sxs-lookup"><span data-stu-id="2d1a0-107">To find out whether the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service has been started, at the command prompt, type the following:</span></span>  
  
 <span data-ttu-id="2d1a0-108">**net start**</span><span class="sxs-lookup"><span data-stu-id="2d1a0-108">**net start**</span></span>  
  
 <span data-ttu-id="2d1a0-109">若與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 相關的服務已啟動，則會在 **net start** 輸出中出現下列服務：</span><span class="sxs-lookup"><span data-stu-id="2d1a0-109">If the services associated with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] have been started, the following services will appear in the **net start** output:</span></span>  
  
-   <span data-ttu-id="2d1a0-110">Analysis Services (MSSQLSERVER)</span><span class="sxs-lookup"><span data-stu-id="2d1a0-110">Analysis Services (MSSQLSERVER)</span></span>  
  
-   <span data-ttu-id="2d1a0-111">SQL Server (MSSQLSERVER)</span><span class="sxs-lookup"><span data-stu-id="2d1a0-111">SQL Server (MSSQLSERVER)</span></span>  
  
-   <span data-ttu-id="2d1a0-112">SQL Server Agent (MSSQLSERVER)</span><span class="sxs-lookup"><span data-stu-id="2d1a0-112">SQL Server Agent (MSSQLSERVER)</span></span>  
  
## <a name="running-sql-server-without-a-network"></a><span data-ttu-id="2d1a0-113">不使用網路執行 SQL Server</span><span class="sxs-lookup"><span data-stu-id="2d1a0-113">Running SQL Server Without a Network</span></span>  
 <span data-ttu-id="2d1a0-114">在不使用網路的情況下執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體時，就不需要內建的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="2d1a0-114">When running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without a network, you do not need to start the built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="2d1a0-115">即使未使用網路， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、SQL Server 組態管理員以及 **net start** 和 **net stop** 命令仍可作用，因此啟動及停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的程序，與在網路作業或獨立作業中的程序相同。</span><span class="sxs-lookup"><span data-stu-id="2d1a0-115">Because [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], SQL Server Configuration Manager, and the **net start** and **net stop** commands are functional even without a network, the procedures for starting and stopping an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are identical for a network or stand-alone operation.</span></span>  
  
 <span data-ttu-id="2d1a0-116">從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sqlcmd **之類的本機用戶端連接獨立的**執行個體時，您可以不使用網路，而使用本機管道直接連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="2d1a0-116">When connecting to an instance of a stand-alone [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a local client such as **sqlcmd**, you bypass the network and connect directly to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a local pipe.</span></span> <span data-ttu-id="2d1a0-117">本機管道與網路管道的差別在於是否使用網路。</span><span class="sxs-lookup"><span data-stu-id="2d1a0-117">The difference between a local pipe and a network pipe is whether you are using a network.</span></span> <span data-ttu-id="2d1a0-118">除非另外指向，否則本機與網路管道都會使用標準管道 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .\pipe\sql\query) 建立與\\\\執行個體的連接。</span><span class="sxs-lookup"><span data-stu-id="2d1a0-118">Both local and network pipes establish a connection with an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the standard pipe (\\\\.\pipe\sql\query), unless otherwise directed.</span></span>  
  
 <span data-ttu-id="2d1a0-119">當您未指定伺服器名稱而連接到本機 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體時，就會使用本機管道。</span><span class="sxs-lookup"><span data-stu-id="2d1a0-119">When you connect to an instance of a local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without specifying a server name, you are using a local pipe.</span></span> <span data-ttu-id="2d1a0-120">當您連接到本機 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，並明確指定伺服器名稱時，使用的是網路管道或別的網路跨處理序通訊 (IPC) 機制，如 Internetwork Packet Exchange (IPX) /Sequenced Packet Exchange (SPX) (假設您已將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設成可使用多個網路)。</span><span class="sxs-lookup"><span data-stu-id="2d1a0-120">When you connect to an instance of a local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and specify a server name explicitly, you are using either a network pipe or another network interprocess communication (IPC) mechanism, such as Internetwork Packet Exchange/Sequenced Packet Exchange (IPX/SPX) (assuming you have configured [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use multiple networks).</span></span> <span data-ttu-id="2d1a0-121">由於獨立的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不支援網路管道，因此從用戶端連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體時，必須省略不必要的 **/** <伺服器名稱> 引數。</span><span class="sxs-lookup"><span data-stu-id="2d1a0-121">Because a stand-alone [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not support network pipes, you must omit the unnecessary **/**_<Server_name>_ argument when connecting to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a client.</span></span> <span data-ttu-id="2d1a0-122">例如，若要從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] osql **連接到獨立**執行個體，請輸入：</span><span class="sxs-lookup"><span data-stu-id="2d1a0-122">For example, to connect to a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from **osql**, type:</span></span>  
  
 <span data-ttu-id="2d1a0-123">**osql /Usa /P** _\<saPassword>_</span><span class="sxs-lookup"><span data-stu-id="2d1a0-123">**osql /Usa /P** _\<saPassword>_</span></span>  
  
  
