---
title: MSSQL_ENG002601 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG002601 error
ms.assetid: 657c3ae6-9e4b-4c60-becc-4caf7435c1dc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c2e8340fef83749fd6d041af42566b10ed3542c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708193"
---
# <a name="mssql_eng002601"></a><span data-ttu-id="9d88d-102">MSSQL_ENG002601</span><span class="sxs-lookup"><span data-stu-id="9d88d-102">MSSQL_ENG002601</span></span>
    
## <a name="message-details"></a><span data-ttu-id="9d88d-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="9d88d-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9d88d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9d88d-104">Product Name</span></span>|<span data-ttu-id="9d88d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9d88d-105">SQL Server</span></span>|  
|<span data-ttu-id="9d88d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9d88d-106">Event ID</span></span>|<span data-ttu-id="9d88d-107">2601</span><span class="sxs-lookup"><span data-stu-id="9d88d-107">2601</span></span>|  
|<span data-ttu-id="9d88d-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="9d88d-108">Event Source</span></span>|<span data-ttu-id="9d88d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9d88d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9d88d-110">元件</span><span class="sxs-lookup"><span data-stu-id="9d88d-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="9d88d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9d88d-111">Symbolic Name</span></span>|<span data-ttu-id="9d88d-112">N/A</span><span class="sxs-lookup"><span data-stu-id="9d88d-112">N/A</span></span>|  
|<span data-ttu-id="9d88d-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9d88d-113">Message Text</span></span>|<span data-ttu-id="9d88d-114">無法以唯一索引 '%.\*ls' 在物件 '%.\*ls' 中插入重複的索引鍵資料列。</span><span class="sxs-lookup"><span data-stu-id="9d88d-114">Cannot insert duplicate key row in object '%.\*ls' with unique index '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9d88d-115">說明</span><span class="sxs-lookup"><span data-stu-id="9d88d-115">Explanation</span></span>  
 <span data-ttu-id="9d88d-116">這是不論複寫資料庫與否，都有可能發生的一般性錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d88d-116">This is a general error that can be raised regardless of whether a database is replicated.</span></span> <span data-ttu-id="9d88d-117">在複寫資料庫中，通常是因為主要索引鍵未於拓撲之間適當管理，才會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d88d-117">In replicated databases, the error is typically raised because primary keys have not been managed appropriately across the topology.</span></span> <span data-ttu-id="9d88d-118">在散發環境中，務必確認主要索引鍵資料行或其他唯一資料行中，並未於多個節點插入相同的值。</span><span class="sxs-lookup"><span data-stu-id="9d88d-118">In a distributed environment it is essential to ensure that the same value is not inserted into a primary key column or any other unique column at more than one node.</span></span> <span data-ttu-id="9d88d-119">可能的原因包括：</span><span class="sxs-lookup"><span data-stu-id="9d88d-119">Possible causes include the following:</span></span>  
  
-   <span data-ttu-id="9d88d-120">同時在多個節點發生資料列的插入與更新動作。</span><span class="sxs-lookup"><span data-stu-id="9d88d-120">Inserts and updates to a row are occurring at more than one node.</span></span> <span data-ttu-id="9d88d-121">合併式複寫與異動複寫的可更新訂閱，皆提供衝突偵測和解決方案，但最好還是在單一節點插入或更新給定資料列。</span><span class="sxs-lookup"><span data-stu-id="9d88d-121">Merge replication and updatable subscriptions for transactional replication both provide conflict detection and resolution, but it is still preferable to insert or update a given row at only one node.</span></span> <span data-ttu-id="9d88d-122">點對點交易不提供衝突偵測和解決方案；必須先分割插入與更新。</span><span class="sxs-lookup"><span data-stu-id="9d88d-122">Peer-to-peer transactional does not provide conflict detection and resolution; it requires that inserts and updates be partitioned.</span></span>  
  
-   <span data-ttu-id="9d88d-123">插入訂閱者的資料列應該是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="9d88d-123">A row was inserted at a Subscriber that should be read-only.</span></span> <span data-ttu-id="9d88d-124">快照集發行集的訂閱者應設定唯讀，交易式發行集的訂閱者亦同；除非已使用可更新訂閱或點對點異動複寫。</span><span class="sxs-lookup"><span data-stu-id="9d88d-124">Subscribers to snapshot publications should be treated as read-only, as should Subscribers to transactional publications unless updatable subscriptions or peer-to-peer transactional replication is used.</span></span>  
  
-   <span data-ttu-id="9d88d-125">已使用具有識別欄位的資料表，但並未適當管理資料行。</span><span class="sxs-lookup"><span data-stu-id="9d88d-125">A table with an identity column is being used, but the column is not managed appropriately.</span></span>  
  
-   <span data-ttu-id="9d88d-126">在合併式複寫中，插入系統資料表 **MSmerge_contents**期間也可以發生此錯誤；引發的錯誤與以下類似：無法以唯一索引 'ucl1SycContents' 在物件 'MSmerge_contents' 中插入重複的索引鍵資料列。</span><span class="sxs-lookup"><span data-stu-id="9d88d-126">In merge replication, this error can also occur during an insert into the system table **MSmerge_contents**; the error raised is similar to: Cannot insert duplicate key row in object 'MSmerge_contents' with unique index 'ucl1SycContents.'</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9d88d-127">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9d88d-127">User Action</span></span>  
 <span data-ttu-id="9d88d-128">必須依照錯誤產生的原因採取動作：</span><span class="sxs-lookup"><span data-stu-id="9d88d-128">The action required depends on the reason the error was raised:</span></span>  
  
-   <span data-ttu-id="9d88d-129">同時在多個節點發生資料列的插入與更新動作。</span><span class="sxs-lookup"><span data-stu-id="9d88d-129">Inserts and updates to a row are occurring at more than one node.</span></span>  
  
     <span data-ttu-id="9d88d-130">不論使用哪一種複寫類型，建議您隨時分割插入和更新；因為這樣可以減少衝突偵測與解決方案所需的處理。</span><span class="sxs-lookup"><span data-stu-id="9d88d-130">Regardless of the type of replication used, we recommend that you partition inserts and updates whenever possible, because this reduces the processing required for conflict detection and resolution.</span></span> <span data-ttu-id="9d88d-131">點對點異動複寫需要分割插入和更新。</span><span class="sxs-lookup"><span data-stu-id="9d88d-131">For peer-to-peer transactional replication, partitioning inserts and updates is required.</span></span> <span data-ttu-id="9d88d-132">如需相關資訊，請參閱 [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="9d88d-132">For more information, see [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="9d88d-133">插入訂閱者的資料列應該是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="9d88d-133">A row was inserted at a Subscriber that should be read-only.</span></span>  
  
     <span data-ttu-id="9d88d-134">請勿於訂閱者插入或更新資料列，除非您使用合併式複寫、有可更新訂閱的異動複寫或點對點異動複寫。</span><span class="sxs-lookup"><span data-stu-id="9d88d-134">Do not insert or update rows at the Subscriber unless you are using merge replication, transactional replication with updatable subscriptions, or peer-to-peer transactional replication.</span></span>  
  
-   <span data-ttu-id="9d88d-135">已使用具有識別欄位的資料表，但並未適當管理資料行。</span><span class="sxs-lookup"><span data-stu-id="9d88d-135">A table with an identity column is being used, but the column is not managed appropriately.</span></span>  
  
     <span data-ttu-id="9d88d-136">針對合併式複寫以及有可更新訂閱的異動複寫，應由複寫來自動管理識別欄位。</span><span class="sxs-lookup"><span data-stu-id="9d88d-136">For merge replication and transactional replication with updatable subscriptions, identity columns should be managed automatically by replication.</span></span> <span data-ttu-id="9d88d-137">點對點異動複寫必須手動管理。</span><span class="sxs-lookup"><span data-stu-id="9d88d-137">For peer-to-peer transactional replication, they must be managed manually.</span></span> <span data-ttu-id="9d88d-138">如需詳細資訊，請參閱[複寫識別資料欄](publish/replicate-identity-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="9d88d-138">For more information, see [Replicate Identity Columns](publish/replicate-identity-columns.md).</span></span>  
  
-   <span data-ttu-id="9d88d-139">在插入系統資料表 **MSmerge_contents**期間會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d88d-139">The error occurs during an insert into the system table **MSmerge_contents**.</span></span>  
  
     <span data-ttu-id="9d88d-140">發生此錯誤是因為聯結篩選屬性 **join_unique_key**的值不正確。</span><span class="sxs-lookup"><span data-stu-id="9d88d-140">This error can occur because of an incorrect value for the join filter property **join_unique_key**.</span></span> <span data-ttu-id="9d88d-141">只有在父資料表中的聯結資料行為唯一時，此屬性才應設定為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="9d88d-141">This property should be set to TRUE only if the joined column in the parent table is unique.</span></span> <span data-ttu-id="9d88d-142">如果屬性設定為 TRUE，但是資料行不是唯一的，則會引發此錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d88d-142">If the property is set to TRUE, but the column is not unique, this error is raised.</span></span> <span data-ttu-id="9d88d-143">如需有關設定此屬性的詳細資訊，請參閱＜ [定義和修改合併發行項之間的聯結篩選](publish/define-and-modify-a-join-filter-between-merge-articles.md)＞。</span><span class="sxs-lookup"><span data-stu-id="9d88d-143">For more information on setting this property, see [Define and Modify a Join Filter Between Merge Articles](publish/define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d88d-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d88d-144">See Also</span></span>  
 [<span data-ttu-id="9d88d-145">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="9d88d-145">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
