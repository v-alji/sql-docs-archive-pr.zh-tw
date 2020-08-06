---
title: 複寫類型 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], types
ms.assetid: c1655e8d-d14c-455a-a7f9-9d2f43e88ab4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5576331004eca44bc32dbde8f430284f75e6eb70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702677"
---
# <a name="types-of-replication"></a><span data-ttu-id="9cda7-102">複寫類型</span><span class="sxs-lookup"><span data-stu-id="9cda7-102">Types of Replication</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="9cda7-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供下列可用於分散式應用程式的複寫類型：</span><span class="sxs-lookup"><span data-stu-id="9cda7-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides the following types of replication for use in distributed applications:</span></span>  
  
-   <span data-ttu-id="9cda7-104">異動複寫。</span><span class="sxs-lookup"><span data-stu-id="9cda7-104">Transactional replication.</span></span> <span data-ttu-id="9cda7-105">如需詳細資訊，請參閱 [異動複寫](transactional/transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="9cda7-105">For more information, see [Transactional Replication](transactional/transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="9cda7-106">合併式複寫。</span><span class="sxs-lookup"><span data-stu-id="9cda7-106">Merge replication.</span></span> <span data-ttu-id="9cda7-107">如需詳細資訊，請參閱[合併式複寫](merge/merge-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="9cda7-107">For more information, see [Merge Replication](merge/merge-replication.md).</span></span>  
  
-   <span data-ttu-id="9cda7-108">快照式複寫。</span><span class="sxs-lookup"><span data-stu-id="9cda7-108">Snapshot replication.</span></span> <span data-ttu-id="9cda7-109">如需詳細資訊，請參閱[快照式複寫](snapshot-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="9cda7-109">For more information, see [Snapshot Replication](snapshot-replication.md).</span></span>  
  
 <span data-ttu-id="9cda7-110">為應用程式選擇的複寫類型取決於許多因素，包括實體複寫環境、要複寫的資料類型和數量，以及資料是否在「訂閱者」端更新。</span><span class="sxs-lookup"><span data-stu-id="9cda7-110">The type of replication you choose for an application depends on many factors, including the physical replication environment, the type and quantity of data to be replicated, and whether the data is updated at the Subscriber.</span></span> <span data-ttu-id="9cda7-111">實體環境包括複寫所涉及的電腦數量和位置，以及這些電腦是用戶端 (工作站、膝上型電腦或手持式裝置) 還是伺服器。</span><span class="sxs-lookup"><span data-stu-id="9cda7-111">The physical environment includes the number and location of computers involved in replication and whether these computers are clients (workstations, laptops, or handheld devices) or servers.</span></span>  
  
 <span data-ttu-id="9cda7-112">各種類型的複寫通常會先對「發行者」和「訂閱者」之間的發行物件進行初始同步處理。</span><span class="sxs-lookup"><span data-stu-id="9cda7-112">Each type of replication typically begins with an initial synchronization of the published objects between the Publisher and Subscribers.</span></span> <span data-ttu-id="9cda7-113">此初始同步處理可由複寫使用 *「快照集」* (發行集指定之所有物件和資料的副本) 來執行。</span><span class="sxs-lookup"><span data-stu-id="9cda7-113">This initial synchronization can be performed by replication with a *snapshot*, which is a copy of all of the objects and data specified by a publication.</span></span> <span data-ttu-id="9cda7-114">快照集建立後會傳遞到「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="9cda7-114">After the snapshot is created, it is delivered to the Subscribers.</span></span> <span data-ttu-id="9cda7-115">對於某些應用程式，只需執行快照式複寫即可。</span><span class="sxs-lookup"><span data-stu-id="9cda7-115">For some applications, snapshot replication is all that is required.</span></span> <span data-ttu-id="9cda7-116">對於其他類型的應用程式，有必要讓後續的資料變更累加地流動至「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="9cda7-116">For other types of applications, it is important that subsequent data changes flow to the Subscriber incrementally over time.</span></span> <span data-ttu-id="9cda7-117">某些應用程式還要求「訂閱者」端的變更流回「發行者」端。</span><span class="sxs-lookup"><span data-stu-id="9cda7-117">Some applications also require that changes flow from the Subscriber back to the Publisher.</span></span> <span data-ttu-id="9cda7-118">異動複寫與合併式複寫可為這些類型的應用程式提供選項。</span><span class="sxs-lookup"><span data-stu-id="9cda7-118">Transactional replication and merge replication provide options for these types of applications.</span></span>  
  
 <span data-ttu-id="9cda7-119">系統不會追蹤快照集複寫中的資料變更；每次套用快照集時，快照集會完全覆寫現有資料。</span><span class="sxs-lookup"><span data-stu-id="9cda7-119">Data changes are not tracked for snapshot replication; each time a snapshot is applied, it completely overwrites the existing data.</span></span> <span data-ttu-id="9cda7-120">異動複寫透過 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 交易記錄檔追蹤變更，合併式複寫則透過觸發程序和中繼資料資料表追蹤變更。</span><span class="sxs-lookup"><span data-stu-id="9cda7-120">Transactional replication tracks changes through the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transaction log, and merge replication tracks changes through triggers and metadata tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cda7-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cda7-121">See Also</span></span>  
 [<span data-ttu-id="9cda7-122">複寫代理程式概觀</span><span class="sxs-lookup"><span data-stu-id="9cda7-122">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
