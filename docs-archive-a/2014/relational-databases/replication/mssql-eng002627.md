---
title: MSSQL_ENG002627 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG002627 error
ms.assetid: 7f4136ac-3784-4a41-a98c-8a02308e4883
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cf481635d6a24570792c9da04fe71ebea885ce5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709162"
---
# <a name="mssql_eng002627"></a><span data-ttu-id="29971-102">MSSQL_ENG002627</span><span class="sxs-lookup"><span data-stu-id="29971-102">MSSQL_ENG002627</span></span>
    
## <a name="message-details"></a><span data-ttu-id="29971-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="29971-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="29971-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="29971-104">Product Name</span></span>|<span data-ttu-id="29971-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="29971-105">SQL Server</span></span>|  
|<span data-ttu-id="29971-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="29971-106">Event ID</span></span>|<span data-ttu-id="29971-107">2627</span><span class="sxs-lookup"><span data-stu-id="29971-107">2627</span></span>|  
|<span data-ttu-id="29971-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="29971-108">Event Source</span></span>|<span data-ttu-id="29971-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="29971-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="29971-110">元件</span><span class="sxs-lookup"><span data-stu-id="29971-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="29971-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="29971-111">Symbolic Name</span></span>|<span data-ttu-id="29971-112">N/A</span><span class="sxs-lookup"><span data-stu-id="29971-112">N/A</span></span>|  
|<span data-ttu-id="29971-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="29971-113">Message Text</span></span>|<span data-ttu-id="29971-114">違反 %ls 條件約束 '%.\*ls'。</span><span class="sxs-lookup"><span data-stu-id="29971-114">Violation of %ls constraint '%.\*ls'.</span></span> <span data-ttu-id="29971-115">無法在物件 '%.\*ls' 中插入重複的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="29971-115">Cannot insert duplicate key in object '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="29971-116">說明</span><span class="sxs-lookup"><span data-stu-id="29971-116">Explanation</span></span>  
 <span data-ttu-id="29971-117">這是不論複寫資料庫與否，都有可能發生的一般性錯誤。</span><span class="sxs-lookup"><span data-stu-id="29971-117">This is a general error that can be raised regardless of whether a database is replicated.</span></span> <span data-ttu-id="29971-118">在複寫資料庫中，通常是因為主要索引鍵未於拓撲之間適當管理，才會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="29971-118">In replicated databases, the error is typically raised because primary keys have not been managed appropriately across the topology.</span></span> <span data-ttu-id="29971-119">在散發環境中，務必確認主要索引鍵資料行或其他唯一資料行中，並未於多個節點插入相同的值。</span><span class="sxs-lookup"><span data-stu-id="29971-119">In a distributed environment it is essential to ensure that the same value is not inserted into a primary key column or any other unique column at more than one node.</span></span> <span data-ttu-id="29971-120">可能的原因包括：</span><span class="sxs-lookup"><span data-stu-id="29971-120">Possible causes include the following:</span></span>  
  
-   <span data-ttu-id="29971-121">同時在多個節點發生資料列的插入與更新動作。</span><span class="sxs-lookup"><span data-stu-id="29971-121">Inserts and updates to a row are occurring at more than one node.</span></span> <span data-ttu-id="29971-122">合併式複寫與異動複寫的可更新訂閱，皆提供衝突偵測和解決方案，但最好還是在單一節點插入或更新給定資料列。</span><span class="sxs-lookup"><span data-stu-id="29971-122">Merge replication and updatable subscriptions for transactional replication both provide conflict detection and resolution, but it is still preferable to insert or update a given row at only one node.</span></span> <span data-ttu-id="29971-123">點對點交易不提供衝突偵測和解決方案；必須先分割插入與更新。</span><span class="sxs-lookup"><span data-stu-id="29971-123">Peer-to-peer transactional does not provide conflict detection and resolution; it requires that inserts and updates be partitioned.</span></span>  
  
-   <span data-ttu-id="29971-124">插入訂閱者的資料列應該是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="29971-124">A row was inserted at a Subscriber that should be read-only.</span></span> <span data-ttu-id="29971-125">快照集發行集的訂閱者應設定唯讀，交易式發行集的訂閱者亦同；除非已使用可更新訂閱或點對點異動複寫。</span><span class="sxs-lookup"><span data-stu-id="29971-125">Subscribers to snapshot publications should be treated as read-only, as should Subscribers to transactional publications unless updatable subscriptions or peer-to-peer transactional replication is used.</span></span>  
  
-   <span data-ttu-id="29971-126">已使用具有識別欄位的資料表，但並未適當管理資料行。</span><span class="sxs-lookup"><span data-stu-id="29971-126">A table with an identity column is being used, but the column is not managed appropriately.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="29971-127">使用者動作</span><span class="sxs-lookup"><span data-stu-id="29971-127">User Action</span></span>  
 <span data-ttu-id="29971-128">必須依照錯誤產生的原因採取動作：</span><span class="sxs-lookup"><span data-stu-id="29971-128">The action required depends on the reason the error was raised:</span></span>  
  
-   <span data-ttu-id="29971-129">同時在多個節點發生資料列的插入與更新動作。</span><span class="sxs-lookup"><span data-stu-id="29971-129">Inserts and updates to a row are occurring at more than one node.</span></span>  
  
     <span data-ttu-id="29971-130">不論使用哪一種複寫類型，建議您隨時分割插入和更新；因為這樣可以減少衝突偵測與解決方案所需的處理。</span><span class="sxs-lookup"><span data-stu-id="29971-130">Regardless of the type of replication used, we recommend that you partition inserts and updates whenever possible, because this reduces the processing required for conflict detection and resolution.</span></span> <span data-ttu-id="29971-131">點對點異動複寫需要分割插入和更新。</span><span class="sxs-lookup"><span data-stu-id="29971-131">For peer-to-peer transactional replication, partitioning inserts and updates is required.</span></span> <span data-ttu-id="29971-132">如需相關資訊，請參閱 [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="29971-132">For more information, see [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="29971-133">插入訂閱者的資料列應該是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="29971-133">A row was inserted at a Subscriber that should be read-only.</span></span>  
  
     <span data-ttu-id="29971-134">請勿於訂閱者插入或更新資料列，除非您使用合併式複寫、有可更新訂閱的異動複寫或點對點異動複寫。</span><span class="sxs-lookup"><span data-stu-id="29971-134">Do not insert or update rows at the Subscriber unless you are using merge replication, transactional replication with updatable subscriptions, or peer-to-peer transactional replication.</span></span>  
  
-   <span data-ttu-id="29971-135">已使用具有識別欄位的資料表，但並未適當管理資料行。</span><span class="sxs-lookup"><span data-stu-id="29971-135">A table with an identity column is being used, but the column is not managed appropriately.</span></span>  
  
     <span data-ttu-id="29971-136">針對合併式複寫以及有可更新訂閱的異動複寫，應由複寫來自動管理識別欄位。</span><span class="sxs-lookup"><span data-stu-id="29971-136">For merge replication and transactional replication with updatable subscriptions, identity columns should be managed automatically by replication.</span></span> <span data-ttu-id="29971-137">點對點異動複寫必須手動管理。</span><span class="sxs-lookup"><span data-stu-id="29971-137">For peer-to-peer transactional replication, they must be managed manually.</span></span> <span data-ttu-id="29971-138">如需詳細資訊，請參閱[複寫識別資料欄](publish/replicate-identity-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="29971-138">For more information, see [Replicate Identity Columns](publish/replicate-identity-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29971-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29971-139">See Also</span></span>  
 <span data-ttu-id="29971-140">[錯誤和事件參考 &#40;複寫&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="29971-140">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="29971-141">[合併式複寫](merge/merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="29971-141">[Merge Replication](merge/merge-replication.md) </span></span>  
 <span data-ttu-id="29971-142">[Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="29971-142">[Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md) </span></span>  
 [<span data-ttu-id="29971-143">Updatable Subscriptions for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="29971-143">Updatable Subscriptions for Transactional Replication</span></span>](transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
