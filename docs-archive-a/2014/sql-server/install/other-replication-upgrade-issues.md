---
title: 其他複寫升級問題 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- system tables [SQL Server], replication
- passwords [SQL Server replication]
- versions [SQL Server replication]
- connections [SQL Server replication]
- scripts [SQL Server replication]
- ActiveX controls [SQL Server replication]
ms.assetid: 8a5e74be-4992-4f17-b20c-c3dce8f49329
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e8ce3f35ead9d3322c636462f682ef391703cfe2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599324"
---
# <a name="other-replication-upgrade-issues"></a><span data-ttu-id="797d4-102">其他複寫升級問題</span><span class="sxs-lookup"><span data-stu-id="797d4-102">Other Replication Upgrade Issues</span></span>
  <span data-ttu-id="797d4-103">本主題涵蓋 Upgrade Advisor 未報告的一些升級問題。</span><span class="sxs-lookup"><span data-stu-id="797d4-103">This topic covers a number of upgrade issues that are not reported by Upgrade Advisor.</span></span>  
  
## <a name="versions-supported"></a><span data-ttu-id="797d4-104">支援的版本</span><span class="sxs-lookup"><span data-stu-id="797d4-104">Versions Supported</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="797d4-105">支援從舊版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升級複寫的資料庫。</span><span class="sxs-lookup"><span data-stu-id="797d4-105">supports upgrading replicated databases from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="797d4-106">當節點正在升級時，您不必停止其他節點上的活動。</span><span class="sxs-lookup"><span data-stu-id="797d4-106">You do not have to stop activity at other nodes while a node is being upgraded.</span></span> <span data-ttu-id="797d4-107">請務必遵守有關拓撲中支援之版本的規則。</span><span class="sxs-lookup"><span data-stu-id="797d4-107">Ensure that you adhere to the rules regarding which versions are supported in a topology.</span></span>  
  
 <span data-ttu-id="797d4-108">當您在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的不同版本之間複寫時，通常受限於所使用之最舊版本的功能。</span><span class="sxs-lookup"><span data-stu-id="797d4-108">When you replicate between or among different versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you are usually limited to the functionality of the earliest version that is being used.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="797d4-109">由於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 磁碟儲存格式在 64 位元和 32 位元的環境中是相同的，所以複寫拓撲可結合在 32 位元環境中執行的伺服器執行個體，以及在 64 位元環境中執行的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="797d4-109">Because the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on-disk storage format is the same in the 64-bit and 32-bit environments, a replication topology can combine server instances that run in a 32-bit environment and server instances that run in a 64-bit environment.</span></span>  
  
 <span data-ttu-id="797d4-110">對於所有複寫類型而言，散發者的版本都不能比發行者的版本還舊 </span><span class="sxs-lookup"><span data-stu-id="797d4-110">For all types of replication, the Distributor version must be no earlier than the Publisher version.</span></span> <span data-ttu-id="797d4-111">(通常散發者和發行者會是相同的執行個體)。</span><span class="sxs-lookup"><span data-stu-id="797d4-111">(Frequently, the Distributor is the same instance as the Publisher.)</span></span>  
  
 <span data-ttu-id="797d4-112">如果是異動複寫，交易式發行集的訂閱者可以是兩個發行者版本的其中任何版本。</span><span class="sxs-lookup"><span data-stu-id="797d4-112">For transactional replication, a Subscriber to a transactional publication can be any version within two versions of the Publisher version.</span></span>  
  
 <span data-ttu-id="797d4-113">如果是合併式複寫，合併式發行集的訂閱者版本可以是任何不晚於發行者的版本。</span><span class="sxs-lookup"><span data-stu-id="797d4-113">For merge replication, a Subscriber to a merge publication can be any version no later than the Publisher version.</span></span>  
  
## <a name="merge-replication-batches-changes"></a><span data-ttu-id="797d4-114">合併式複寫的批次變更</span><span class="sxs-lookup"><span data-stu-id="797d4-114">Merge Replication Batches Changes</span></span>  
 <span data-ttu-id="797d4-115">合併代理程式所進行的變更會批次處理以增進效能；因此，可在單一陳述式內插入、更新或刪除多個資料列。</span><span class="sxs-lookup"><span data-stu-id="797d4-115">Changes that are made by the Merge Agent are batched to improve performance; therefore, more than one row can be inserted, updated, or deleted within a single statement.</span></span> <span data-ttu-id="797d4-116">如果發行集或訂閱資料庫中的任何已發行的資料表有觸發程序，請確定這些觸發程序可以處理多資料列插入、更新及刪除。</span><span class="sxs-lookup"><span data-stu-id="797d4-116">If any published tables in the publication or subscription databases have triggers, ensure that the triggers can handle multirow inserts, updates, and deletes.</span></span> <span data-ttu-id="797d4-117">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜DML 觸發程序的多重資料列考量＞。</span><span class="sxs-lookup"><span data-stu-id="797d4-117">For more information, see "Multirow Considerations for DML Triggers" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="activex-control-changes"></a><span data-ttu-id="797d4-118">ActiveX 控制項變更</span><span class="sxs-lookup"><span data-stu-id="797d4-118">ActiveX Control Changes</span></span>  
 <span data-ttu-id="797d4-119">下列是已經對複寫 ActiveX 控制項所做的變更：</span><span class="sxs-lookup"><span data-stu-id="797d4-119">The following changes have been made for replication ActiveX controls:</span></span>  
  
-   <span data-ttu-id="797d4-120">所有 ActiveX 控制項在撰寫指令碼和初始化時都標示為不安全。</span><span class="sxs-lookup"><span data-stu-id="797d4-120">All ActiveX controls are marked as unsafe for scripting and initialization.</span></span>  
  
-   <span data-ttu-id="797d4-121">快照集 ActiveX 控制項已經卸除。</span><span class="sxs-lookup"><span data-stu-id="797d4-121">The Snapshot ActiveX control has been dropped.</span></span> <span data-ttu-id="797d4-122">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或透過複寫預存程序來以程式設計的方式建立及管理快照集。</span><span class="sxs-lookup"><span data-stu-id="797d4-122">You can create and manage snapshots by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or programmatically by using replication stored procedures.</span></span> <span data-ttu-id="797d4-123">如需詳細資訊，請參閱《[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 線上叢書》中的＜如何：建立和套用初始快照集 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])＞和＜如何：建立初始快照集 (複寫 Transact-SQL 程式設計)＞主題。</span><span class="sxs-lookup"><span data-stu-id="797d4-123">For more information, see the topics "How to: Create and Apply the Initial Snapshot ([!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)])" and "How to: Create the Initial Snapshot (Replication Transact-SQL Programming)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
-   <span data-ttu-id="797d4-124">散發 ActiveX 控制項和合併 ActiveX 控制項已被取代。</span><span class="sxs-lookup"><span data-stu-id="797d4-124">The Distribution ActiveX control and Merge ActiveX control have been deprecated.</span></span> <span data-ttu-id="797d4-125">將會使用 Replication Management Objects (RMO) 來針對 Managed 程式碼應用程式提供類似的功能。</span><span class="sxs-lookup"><span data-stu-id="797d4-125">Similar functionality is provided for managed code applications using Replication Management Objects (RMO).</span></span> <span data-ttu-id="797d4-126">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜同步處理訂閱 (RMO 程式設計)＞。</span><span class="sxs-lookup"><span data-stu-id="797d4-126">For more information, see "Synchronizing Subscriptions (RMO Programming)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="797d4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="797d4-127">See Also</span></span>  
 [<span data-ttu-id="797d4-128">複寫升級問題</span><span class="sxs-lookup"><span data-stu-id="797d4-128">Replication Upgrade Issues</span></span>](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
  
