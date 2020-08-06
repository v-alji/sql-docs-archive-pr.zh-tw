---
title: Web 同步處理的拓撲 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Web synchronization, topologies
- IIS server configuration [SQL Server replication]
ms.assetid: 59444faf-bcb6-4421-a3df-8715753e453b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5e28ca5a222e2286d154c16ef41d3147dc56e25a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596644"
---
# <a name="topologies-for-web-synchronization"></a><span data-ttu-id="bad8b-102">Web 同步處理的拓撲</span><span class="sxs-lookup"><span data-stu-id="bad8b-102">Topologies for Web Synchronization</span></span>
  <span data-ttu-id="bad8b-103">您可以從各種 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Web 同步處理複寫拓撲中進行選擇。</span><span class="sxs-lookup"><span data-stu-id="bad8b-103">You can choose from a variety of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Web synchronization replication topologies.</span></span> <span data-ttu-id="bad8b-104">設定 Web 同步處理的一般方式包括：</span><span class="sxs-lookup"><span data-stu-id="bad8b-104">Common ways to configure Web synchronization include:</span></span>  
  
-   <span data-ttu-id="bad8b-105">單一伺服器</span><span class="sxs-lookup"><span data-stu-id="bad8b-105">Single server</span></span>  
  
-   <span data-ttu-id="bad8b-106">兩個伺服器</span><span class="sxs-lookup"><span data-stu-id="bad8b-106">Two servers</span></span>  
  
-   <span data-ttu-id="bad8b-107">多個 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) 系統和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 重新發行</span><span class="sxs-lookup"><span data-stu-id="bad8b-107">Multiple [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) systems and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] republishing</span></span>  
  
 <span data-ttu-id="bad8b-108">如需設定 Web 同步處理的資訊，請參閱[設定 Web 同步處理](configure-web-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="bad8b-108">For information about configuring Web synchronization, see [Configure Web Synchronization](configure-web-synchronization.md).</span></span>  
  
## <a name="single-server"></a><span data-ttu-id="bad8b-109">單一伺服器</span><span class="sxs-lookup"><span data-stu-id="bad8b-109">Single Server</span></span>  
 <span data-ttu-id="bad8b-110">在最簡單的拓撲中，IIS、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 發行者和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 散發者均位於單一伺服器中。</span><span class="sxs-lookup"><span data-stu-id="bad8b-110">In the simplest topology, IIS, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher, and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor all reside on a single server.</span></span> <span data-ttu-id="bad8b-111">訂閱者透過連接到發行者端的 IIS 進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="bad8b-111">Subscribers synchronize by connecting to IIS on the Publisher.</span></span> <span data-ttu-id="bad8b-112">發行者可以位於防火牆之後。</span><span class="sxs-lookup"><span data-stu-id="bad8b-112">The Publisher can be located behind a firewall.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bad8b-113">此組態建議僅在內部網路環境中使用。</span><span class="sxs-lookup"><span data-stu-id="bad8b-113">This configuration is recommended only for intranet scenarios.</span></span> <span data-ttu-id="bad8b-114">對於其他狀況，建議讓 IIS 伺服器與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 發行者/散發者位於不同的電腦中。</span><span class="sxs-lookup"><span data-stu-id="bad8b-114">For other scenarios, it is recommended that the IIS server and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher/Distributor be on separate computers.</span></span>  
  
 <span data-ttu-id="bad8b-115">![與單一伺服器進行 Web 同步處理](media/web-sync02.gif "與單一伺服器進行 Web 同步處理")</span><span class="sxs-lookup"><span data-stu-id="bad8b-115">![Web synchronization with a single server](media/web-sync02.gif "Web synchronization with a single server")</span></span>  
  
## <a name="two-servers"></a><span data-ttu-id="bad8b-116">兩個伺服器</span><span class="sxs-lookup"><span data-stu-id="bad8b-116">Two Servers</span></span>  
 <span data-ttu-id="bad8b-117">您可以將 IIS 置於一個伺服器，並在另一個伺服器上設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 發行者和散發者。</span><span class="sxs-lookup"><span data-stu-id="bad8b-117">You can place IIS on one server and configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher and Distributor on another server.</span></span> <span data-ttu-id="bad8b-118">透過防火牆可以將執行 IIS 的伺服器與網際網路隔離。</span><span class="sxs-lookup"><span data-stu-id="bad8b-118">The server running IIS can be isolated from the Internet by a firewall.</span></span> <span data-ttu-id="bad8b-119">「訂閱者」則透過連接到 IIS 進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="bad8b-119">Subscribers synchronize by connecting to IIS.</span></span>  
  
 <span data-ttu-id="bad8b-120">![與兩部伺服器進行 Web 同步處理](media/web-sync03.gif "與兩部伺服器進行 Web 同步處理")</span><span class="sxs-lookup"><span data-stu-id="bad8b-120">![Web synchronization with two servers](media/web-sync03.gif "Web synchronization with two servers")</span></span>  
  
## <a name="multiple-iis-systems-and-sql-server-republishing"></a><span data-ttu-id="bad8b-121">多個 IIS 系統與 SQL Server 重新發行</span><span class="sxs-lookup"><span data-stu-id="bad8b-121">Multiple IIS Systems and SQL Server Republishing</span></span>  
 <span data-ttu-id="bad8b-122">如果您需要支援大量「訂閱者」的同時同步處理，可以在執行 IIS 的多台電腦間分割工作。</span><span class="sxs-lookup"><span data-stu-id="bad8b-122">If you need to support very large numbers of Subscribers that synchronize at the same time, you can partition the work across multiple computers running IIS.</span></span>  
  
 <span data-ttu-id="bad8b-123">![與多部 IIS 伺服器進行 Web 同步處理](media/web-sync04.gif "與多部 IIS 伺服器進行 Web 同步處理")</span><span class="sxs-lookup"><span data-stu-id="bad8b-123">![Web synchronization with multiple IIS servers](media/web-sync04.gif "Web synchronization with multiple IIS servers")</span></span>  
  
 <span data-ttu-id="bad8b-124">如果執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的電腦上需要進一步的負載平衡，您可以在多台電腦上建立重新發行階層。</span><span class="sxs-lookup"><span data-stu-id="bad8b-124">If further load balancing is required on the computer running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can create a republishing hierarchy on multiple computers.</span></span> <span data-ttu-id="bad8b-125">最上層發行者將資料發行到訂閱者，訂閱者再重新發行資料及其負載平衡要求。</span><span class="sxs-lookup"><span data-stu-id="bad8b-125">The top-level Publisher publishes data to Subscribers, which in turn republish the data, load balancing requests from the Subscribers.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bad8b-126">訂閱者只能與特定發行者同步處理。</span><span class="sxs-lookup"><span data-stu-id="bad8b-126">Subscribers can only synchronize with a specific Publisher.</span></span> <span data-ttu-id="bad8b-127">例如，訂閱者若訂閱重新發行者 A，則在無法使用 A 時不能改為與重新發行者 B 同步處理。</span><span class="sxs-lookup"><span data-stu-id="bad8b-127">For example, a Subscriber to republisher A cannot synchronize with republisher B when A is not available.</span></span>  
  
 <span data-ttu-id="bad8b-128">![Web 同步處理和重新發佈](media/web-sync05.gif "Web 同步處理和重新發佈")</span><span class="sxs-lookup"><span data-stu-id="bad8b-128">![Web synchronization with republishing](media/web-sync05.gif "Web synchronization with republishing")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bad8b-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bad8b-129">See Also</span></span>  
 <span data-ttu-id="bad8b-130">[Configure Web Synchronization](configure-web-synchronization.md) </span><span class="sxs-lookup"><span data-stu-id="bad8b-130">[Configure Web Synchronization](configure-web-synchronization.md) </span></span>  
 [<span data-ttu-id="bad8b-131">合併式複寫的 Web 同步處理</span><span class="sxs-lookup"><span data-stu-id="bad8b-131">Web Synchronization for Merge Replication</span></span>](web-synchronization-for-merge-replication.md)  
  
  
