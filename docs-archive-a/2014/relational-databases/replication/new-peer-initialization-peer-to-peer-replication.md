---
title: 新的對等 (Peer) 初始化 (點對點複寫) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.init.f1
ms.assetid: 050c00e1-78bd-4d9c-affe-40e22feb4d94
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 26658fdfbcf0d3d3a88bedbace4102cda6cee9c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598286"
---
# <a name="new-peer-initialization-peer-to-peer-replication"></a><span data-ttu-id="2f45e-102">新的對等 (Peer) 初始化 (點對點複寫)</span><span class="sxs-lookup"><span data-stu-id="2f45e-102">New Peer Initialization (Peer-to-Peer Replication)</span></span>
  <span data-ttu-id="2f45e-103">您可以使用 **[新的對等 (Peer) 初始化]** 頁面來指定對等 (Peer) 資料庫的初始化方式</span><span class="sxs-lookup"><span data-stu-id="2f45e-103">Use the **New Peer Initialization** page to specify how peer databases were initialized.</span></span> <span data-ttu-id="2f45e-104">您必須先初始化 (對等，才能完成此 wizard。 ) 對等是以手動方式初始化，或使用由異動複寫所提供的「**使用初始化**」的備份功能。</span><span class="sxs-lookup"><span data-stu-id="2f45e-104">(Peers must be initialized before you complete this wizard.) Peers are initialized manually or by using the **initialize with backup** functionality that is provided by transactional replication.</span></span> <span data-ttu-id="2f45e-105"> (點對點異動複寫不支援使用快照集初始化對等。 ) 如果必須使用不同的方法來初始化不同的對等，您必須執行嚮導多次，以個別新增對等。</span><span class="sxs-lookup"><span data-stu-id="2f45e-105">(Peer-to-peer transactional replication does not support initializing peers by using a snapshot.) If different peers have to be initialized using different methods, you must add the peers separately by running the wizard multiple times.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2f45e-106">選項</span><span class="sxs-lookup"><span data-stu-id="2f45e-106">Options</span></span>  
 <span data-ttu-id="2f45e-107">**指定要如何初始化新的對等 (Peer) 資料庫**</span><span class="sxs-lookup"><span data-stu-id="2f45e-107">**Specify how the new peer database(s) was initialized**</span></span>  
 <span data-ttu-id="2f45e-108">所有發行物件的結構描述和資料，都必須存在於每一個對等 (Peer) 上。</span><span class="sxs-lookup"><span data-stu-id="2f45e-108">The schema and data for all published objects must be present at each peer.</span></span> <span data-ttu-id="2f45e-109">選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="2f45e-109">Select one of the following options:</span></span>  
  
-   <span data-ttu-id="2f45e-110">如果您已手動建立發行物件的結構描述，或者已還原備份，而且第一個發行集資料庫在建立備份之後未變更任何資料，請選取第一個選項。</span><span class="sxs-lookup"><span data-stu-id="2f45e-110">Select the first option if you have manually created the schema for published objects or you have restored a backup, and no data changes have been made at the first publication database since the backup was taken.</span></span> <span data-ttu-id="2f45e-111">如果您是手動建立結構描述，就必須確定所有必要的資料存在於每一個對等 (Peer) 上。</span><span class="sxs-lookup"><span data-stu-id="2f45e-111">If you created the schema manually, you must ensure that all required data is present at each peer.</span></span> <span data-ttu-id="2f45e-112">此選項對應至訂閱屬性 **sync_type** 的 **replication support only**值。</span><span class="sxs-lookup"><span data-stu-id="2f45e-112">This option corresponds to a value of **replication support only** for the subscription property **sync_type**.</span></span>  
  
-   <span data-ttu-id="2f45e-113">如果您已還原備份，且第一個發行集資料庫在執行備份之後已變更資料，請選取第二個選項。</span><span class="sxs-lookup"><span data-stu-id="2f45e-113">Select the second option if you have restored a backup, and data changes have been made at the first publication database since the backup was taken.</span></span> <span data-ttu-id="2f45e-114">如此一來，複寫就必須傳遞來自第一個發行集資料庫中、未包含在備份內的變更。</span><span class="sxs-lookup"><span data-stu-id="2f45e-114">Replication must now deliver changes from the first publication database that were not included in the backup.</span></span> <span data-ttu-id="2f45e-115">此選項對應至訂閱屬性 **sync_type** 的 **initialize with backup**值。</span><span class="sxs-lookup"><span data-stu-id="2f45e-115">This option corresponds to a value of **initialize with backup** for the subscription property **sync_type**.</span></span>  
  
     <span data-ttu-id="2f45e-116">發行集啟用點對點複寫時，會設定 **allow_initialize_from_backup** 發行集屬性。</span><span class="sxs-lookup"><span data-stu-id="2f45e-116">When a publication is enabled for peer-to-peer replication, the **allow_initialize_from_backup** publication property is set.</span></span> <span data-ttu-id="2f45e-117">複寫會立即開始追蹤第一個發行集資料庫的變更。</span><span class="sxs-lookup"><span data-stu-id="2f45e-117">Replication immediately starts to track changes in the first publication database.</span></span> <span data-ttu-id="2f45e-118">因此，在已選取 **initialize with backup** 選項的情況下，這些變更就可以傳遞至一或多個對等 (Peer) 的還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f45e-118">Therefore, these changes can be delivered to a restored database at one or more peers if the **initialize with backup** option is selected.</span></span> <span data-ttu-id="2f45e-119">按一下 **[瀏覽]** 按鈕找出所使用的備份，而且複寫將從備份中讀取記錄序號 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="2f45e-119">Click the **Browse** button to locate the backup used, and replication will read the log sequence number (LSN) from the backup.</span></span> <span data-ttu-id="2f45e-120">在第一個發行集資料庫中，具有較高 LSN 的所有變更將會傳遞至每一個對等 (Peer)。</span><span class="sxs-lookup"><span data-stu-id="2f45e-120">All changes in the first publication database that have a higher LSN will be delivered to each peer.</span></span>  
  
     <span data-ttu-id="2f45e-121">如果您正在建立或加入至包含 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]的拓撲，這個選項可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="2f45e-121">This option might not be available if you are creating or adding to a topology that includes [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="2f45e-122">下表顯示了當您將節點加入至現有拓撲時，這個選項是否可用。</span><span class="sxs-lookup"><span data-stu-id="2f45e-122">The following table shows whether the option is available when you are adding a node to an existing topology.</span></span>  
  
    |<span data-ttu-id="2f45e-123">新節點</span><span class="sxs-lookup"><span data-stu-id="2f45e-123">New node</span></span>|<span data-ttu-id="2f45e-124">第一個節點</span><span class="sxs-lookup"><span data-stu-id="2f45e-124">First node</span></span>|<span data-ttu-id="2f45e-125">其他節點</span><span class="sxs-lookup"><span data-stu-id="2f45e-125">Additional nodes</span></span>|<span data-ttu-id="2f45e-126">選項</span><span class="sxs-lookup"><span data-stu-id="2f45e-126">Option</span></span>|  
    |--------------|----------------|----------------------|------------|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|<span data-ttu-id="2f45e-127">已停用</span><span class="sxs-lookup"><span data-stu-id="2f45e-127">Disabled</span></span>|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|<span data-ttu-id="2f45e-128">無</span><span class="sxs-lookup"><span data-stu-id="2f45e-128">None</span></span>|<span data-ttu-id="2f45e-129">已停用</span><span class="sxs-lookup"><span data-stu-id="2f45e-129">Disabled</span></span>|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|<span data-ttu-id="2f45e-130">已停用</span><span class="sxs-lookup"><span data-stu-id="2f45e-130">Disabled</span></span>|  
    |[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|<span data-ttu-id="2f45e-131">無</span><span class="sxs-lookup"><span data-stu-id="2f45e-131">None</span></span>|<span data-ttu-id="2f45e-132">啟用</span><span class="sxs-lookup"><span data-stu-id="2f45e-132">Enabled</span></span>|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|<span data-ttu-id="2f45e-133">無</span><span class="sxs-lookup"><span data-stu-id="2f45e-133">None</span></span>|<span data-ttu-id="2f45e-134">啟用</span><span class="sxs-lookup"><span data-stu-id="2f45e-134">Enabled</span></span>|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|<span data-ttu-id="2f45e-135">啟用</span><span class="sxs-lookup"><span data-stu-id="2f45e-135">Enabled</span></span>|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|<span data-ttu-id="2f45e-136">無</span><span class="sxs-lookup"><span data-stu-id="2f45e-136">None</span></span>|<span data-ttu-id="2f45e-137">啟用</span><span class="sxs-lookup"><span data-stu-id="2f45e-137">Enabled</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2f45e-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f45e-138">See Also</span></span>  
 <span data-ttu-id="2f45e-139">[管理點對點拓撲 &#40;複寫 Transact-SQL 程式設計&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span><span class="sxs-lookup"><span data-stu-id="2f45e-139">[Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span></span>  
 [<span data-ttu-id="2f45e-140">@loopback_detection</span><span class="sxs-lookup"><span data-stu-id="2f45e-140">Peer-to-Peer Transactional Replication</span></span>](transactional/peer-to-peer-transactional-replication.md)  
  
  
