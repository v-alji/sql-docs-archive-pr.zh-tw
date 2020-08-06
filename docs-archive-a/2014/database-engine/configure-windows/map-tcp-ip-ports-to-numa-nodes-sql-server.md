---
title: 將 TCP/IP 連接埠對應到 NUMA 節點 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- NUMA
- memory [SQL Server], NUMA
- affinity NUMA
- ports [SQL Server], working with NUMA
- CPU [SQL Server], NUMA support
- NUMA, How to map a port to a NUMA node
- NUMA affinity
- TCP/IP [SQL Server], NUMA support
- non-uniform memory access
ms.assetid: 07727642-0266-4cbc-8c55-3c367e4458ca
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cf4a1bd7e02719d3884011ad3faa20a1ccc6466a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687152"
---
# <a name="map-tcp-ip-ports-to-numa-nodes-sql-server"></a><span data-ttu-id="d8eec-102">將 TCP/IP 連接埠對應到 NUMA 節點 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d8eec-102">Map TCP IP Ports to NUMA Nodes (SQL Server)</span></span>
  <span data-ttu-id="d8eec-103">此主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員，將 TCP/IP 通訊埠對應到非統一記憶體存取 (NUMA) 節點。</span><span class="sxs-lookup"><span data-stu-id="d8eec-103">This topic describes how to map TCP/IP ports to non-uniform memory access (NUMA) nodes by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="d8eec-104">在啟動時， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會將節點資訊寫入錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="d8eec-104">On startup, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] writes the node information to the error log.</span></span>  
  
 <span data-ttu-id="d8eec-105">若要判斷您想要使用之節點的節點號碼，請從錯誤記錄檔或從 **sys.dm_os_schedulers** 檢視中讀取節點資訊。</span><span class="sxs-lookup"><span data-stu-id="d8eec-105">To determine the node number of the node you want to use, either read the node information from the error log, or from the **sys.dm_os_schedulers** view.</span></span> <span data-ttu-id="d8eec-106">若要將 TCP/IP 位址和通訊埠設為單一或多重節點，請在通訊埠編號後面用方括號附加節點識別點陣圖 (相似性遮罩)。</span><span class="sxs-lookup"><span data-stu-id="d8eec-106">To set a TCP/IP address and port to single or multiple nodes, append a node identification bitmap (an affinity mask) in brackets after the port number.</span></span> <span data-ttu-id="d8eec-107">可以用十進位或十六進位格式指定節點。</span><span class="sxs-lookup"><span data-stu-id="d8eec-107">Nodes can be specified in either decimal or hexadecimal format.</span></span> <span data-ttu-id="d8eec-108">若要建立點陣圖，請由零開始，將節點從右到左編號，例如 76543210。</span><span class="sxs-lookup"><span data-stu-id="d8eec-108">To create the bitmap, first number the nodes from right to left starting with zero, as in 76543210.</span></span> <span data-ttu-id="d8eec-109">建立節點清單的二進位表示法，以 1 代表您要使用的節點，以 0 代表您不要使用的節點。</span><span class="sxs-lookup"><span data-stu-id="d8eec-109">Create a binary representation of the node list, providing 1 for nodes you want to use, and 0 for nodes you do not want to use.</span></span> <span data-ttu-id="d8eec-110">例如，若要使用 NUMA 節點 0、2 和 5，請指定 00100101。</span><span class="sxs-lookup"><span data-stu-id="d8eec-110">For example, to use NUMA nodes 0, 2, and 5, specify 00100101.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d8eec-111">NUMA 節點號碼</span><span class="sxs-lookup"><span data-stu-id="d8eec-111">NUMA node number</span></span>|<span data-ttu-id="d8eec-112">76543210</span><span class="sxs-lookup"><span data-stu-id="d8eec-112">76543210</span></span>|  
|<span data-ttu-id="d8eec-113">從右算起，0、2 和 5 的遮罩</span><span class="sxs-lookup"><span data-stu-id="d8eec-113">Mask for 0, 2, and 5 counting from right</span></span>|<span data-ttu-id="d8eec-114">00100101</span><span class="sxs-lookup"><span data-stu-id="d8eec-114">00100101</span></span>|  
  
 <span data-ttu-id="d8eec-115">將二進位表示法 (00100101) 轉換成十進位 `[37]`或十六進位 `[0x25]`。</span><span class="sxs-lookup"><span data-stu-id="d8eec-115">Convert the binary representation (00100101), into decimal `[37]`, or hexadecimal `[0x25]`.</span></span> <span data-ttu-id="d8eec-116">若要接聽所有節點，則不要提供節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="d8eec-116">To listen on all nodes, provide no node identifier.</span></span>  
  
 <span data-ttu-id="d8eec-117">如果通訊埠對應到不止一個 NUMA 節點， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會以循環方式指派節點的連接，而不會嘗試去平衡節點的負載。</span><span class="sxs-lookup"><span data-stu-id="d8eec-117">If a port is mapped to more than one NUMA node, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assigns connections to nodes in a round-robin fashion without attempting to balance load across the nodes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d8eec-118">若要讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 能夠在每個 IP 位址的多個 TCP 通訊埠上接聽，請參閱 [設定 Database Engine 接聽多個 TCP 通訊埠](configure-the-database-engine-to-listen-on-multiple-tcp-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="d8eec-118">To enable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to listen on multiple TCP ports for each IP address, see [Configure the Database Engine to Listen on Multiple TCP Ports](configure-the-database-engine-to-listen-on-multiple-tcp-ports.md).</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d8eec-119">使用 SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="d8eec-119">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-map-a-tcpip-port-to-a-numa-node"></a><span data-ttu-id="d8eec-120">若要將 TCP/IP 通訊埠對應到 NUMA 節點</span><span class="sxs-lookup"><span data-stu-id="d8eec-120">To map a TCP/IP port to a NUMA node</span></span>  
  
1.  <span data-ttu-id="d8eec-121">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員中，展開 [SQL Server 網路組態]，然後按一下 [ *\<instance name>* 的通訊協定]。</span><span class="sxs-lookup"><span data-stu-id="d8eec-121">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, expand **SQL Server Network Configuration**, and then click **Protocols for** *\<instance name>*.</span></span>  
  
2.  <span data-ttu-id="d8eec-122">在詳細資料窗格中，按兩下 [TCP/IP]。</span><span class="sxs-lookup"><span data-stu-id="d8eec-122">In the details pane, double-click **TCP/IP**.</span></span>  
  
3.  <span data-ttu-id="d8eec-123">在 **[IP 位址]** 索引標籤上，在對應到要設定之 IP 位址的區段中，在 **[TCP 通訊埠]** 方塊中，在通訊埠編號後面以方括號加入 NUMA 節點識別碼中。</span><span class="sxs-lookup"><span data-stu-id="d8eec-123">On the **IP Addresses** tab, in the section corresponding to the IP address to configure, in the **TCP Port** box, add the NUMA node identifier in brackets after the port number.</span></span> <span data-ttu-id="d8eec-124">例如，對於 TCP 通訊埠 1500 和節點 0、2 和 5，請使用 `1500[37]` 或 `1500[0x25]`。</span><span class="sxs-lookup"><span data-stu-id="d8eec-124">For example, for TCP port 1500 and nodes 0, 2, and 5, use `1500[37]`, or `1500[0x25]`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8eec-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8eec-125">See Also</span></span>  
 [<span data-ttu-id="d8eec-126">將 SQL Server 設定為使用軟體 NUMA &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d8eec-126">Configure SQL Server to Use Soft-NUMA &#40;SQL Server&#41;</span></span>](soft-numa-sql-server.md)  
  
  
