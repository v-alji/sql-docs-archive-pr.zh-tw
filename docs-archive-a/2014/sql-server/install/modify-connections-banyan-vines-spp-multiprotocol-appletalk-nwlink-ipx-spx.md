---
title: 修改使用 Banyan VINES 排序封包通訊協定 (SPP) 、通訊協定、AppleTalk 或 NWLink IPX SPX 網路通訊協定的連接 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- network protocols [SQL Server], modifying connections
- SPP [SQL Server]
- NWLink IPX/SPX [SQL Server]
- connections [SQL Server]
- AppleTalk [SQL Server]
- Sequenced Packet Protocol [SQL Server]
- Multiprotocol Net-Library [SQL Server]
- Banyan VINES Sequenced Package Protocol [SQL Server]
- IPX/SPX [SQL Server]
- protocols [SQL Server], modifying connections
- RPC [SQL Server]
ms.assetid: 5c5ae453-cc5b-4898-95c7-ad34157b1f60
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 750b9c0b76ab6c3b43908ecb8454f31ac1a25b1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708054"
---
# <a name="modify-connections-that-use-banyan-vines-sequenced-packet-protocol-spp-multiprotocol-appletalk-or-nwlink-ipx-spx-network-protocols"></a><span data-ttu-id="6836f-102">修改使用 Banyan VINES Sequenced Packet Protocol (SPP)、多重通訊協定、AppleTalk 或 NWLink IPX SPX 網路通訊協定的連線</span><span class="sxs-lookup"><span data-stu-id="6836f-102">Modify connections that use Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk, or NWLink IPX SPX network protocols</span></span>
  <span data-ttu-id="6836f-103">Upgrade Advisor 偵測到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中不支援的用戶端伺服器連接通訊協定。</span><span class="sxs-lookup"><span data-stu-id="6836f-103">The Upgrade Advisor has detected client server connectivity protocols that are not supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="6836f-104">使用 Banyan VINES Sequenced Packet Protocol (SPP)、多重通訊協定 (RPC)、AppleTalk 與 NWLink IPX/SPX 網路通訊協定的用戶端應用程式必須使用支援的通訊協定進行連接。</span><span class="sxs-lookup"><span data-stu-id="6836f-104">Client applications that use Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol (RPC), AppleTalk, or NWLink IPX/SPX network protocols must connect using a supported protocol.</span></span>  
  
## <a name="component"></a><span data-ttu-id="6836f-105">元件</span><span class="sxs-lookup"><span data-stu-id="6836f-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="6836f-106">描述</span><span class="sxs-lookup"><span data-stu-id="6836f-106">Description</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="6836f-107">不支援 Banyan VINES Sequenced Packet Protocol (SPP)、多重通訊協定、AppleTalk 或 NWLink IPX/SPX 網路通訊協定。</span><span class="sxs-lookup"><span data-stu-id="6836f-107">does not support the Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk, or NWLink IPX/SPX network protocols.</span></span> <span data-ttu-id="6836f-108">先前使用這些通訊協定進行連接的用戶端必須選取不同的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="6836f-108">Clients previously connecting with these protocols must select a different protocol.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="6836f-109">更正動作</span><span class="sxs-lookup"><span data-stu-id="6836f-109">Corrective Action</span></span>  
 <span data-ttu-id="6836f-110">變更用戶端應用程式，以便在連接至伺服器時使用支援的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="6836f-110">Change the client applications to use a supported protocol when connecting to the server.</span></span> <span data-ttu-id="6836f-111">如果您有使用了其中一個不支援之通訊協定的別名設定，則必須將別名修改為使用其中一個支援的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="6836f-111">If you have an alias setup that uses one of the unsupported protocols then the alias must be modified to use one of the supported protocols.</span></span>  
  
 <span data-ttu-id="6836f-112">如果您的應用程式連接字串特別使用或載入其中一個通訊協定，請指定 NETWORK = DBMSRPCN for RPC，NETWORK = DBMSADSN for Appletalk 或 NETWORK = DBMSVINN for Banyan VINES 屬性，或使用明確的前置詞，例如 "spx：*server\instance*" 代表 spx、"bv：*Server*" 代表 Banyan VINES、"adsp：*server*" 代表 appletalk，或 "RPC：*server*" 代表通訊協定，您必須將應用程式修改為使用其中一種支援的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="6836f-112">If your application connection string specifically uses or loads one of these protocols, by either specifying NETWORK=DBMSRPCN for RPC, NETWORK=DBMSADSN for Appletalk, or NETWORK=DBMSVINN for Banyan VINES property, or by using an explicit prefix such as "spx:*server\instance*" for SPX, "bv:*server*" for Banyan VINES, "adsp:*server*" for AppleTalk, or "rpc:*server*" for multiprotocol, then you must modify your application to use one of the supported protocols.</span></span>  
  
 <span data-ttu-id="6836f-113">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜選擇網路通訊協定＞。</span><span class="sxs-lookup"><span data-stu-id="6836f-113">For more information, see "Choosing a Network Protocol" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6836f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6836f-114">See Also</span></span>  
 <span data-ttu-id="6836f-115">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="6836f-115">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="6836f-116">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="6836f-116">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
