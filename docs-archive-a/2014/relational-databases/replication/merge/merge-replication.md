---
title: 合併式複寫 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], about merge replication
- merge replication [SQL Server replication]
ms.assetid: ff87c368-4c00-4e48-809d-ea752839551e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7feef9e4debc228d1685c664c072139d60b56c22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584433"
---
# <a name="merge-replication"></a><span data-ttu-id="b861d-102">合併式複寫</span><span class="sxs-lookup"><span data-stu-id="b861d-102">Merge Replication</span></span>
  <span data-ttu-id="b861d-103">合併式複寫與異動複寫類似，通常以發行集資料庫物件和資料的快照集啟動。</span><span class="sxs-lookup"><span data-stu-id="b861d-103">Merge replication, like transactional replication, typically starts with a snapshot of the publication database objects and data.</span></span> <span data-ttu-id="b861d-104">在「發行者」和「訂閱者」端所作的後續資料變更和結構描述修改可使用觸發程序進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="b861d-104">Subsequent data changes and schema modifications made at the Publisher and Subscribers are tracked with triggers.</span></span> <span data-ttu-id="b861d-105">該「訂閱者」在連接到網路時會與「發行者」同步，並且在「發行者」與「訂閱者」之間交換自上次同步處理後進行過變更的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="b861d-105">The Subscriber synchronizes with the Publisher when connected to the network and exchanges all rows that have changed between the Publisher and Subscriber since the last time synchronization occurred.</span></span>

 <span data-ttu-id="b861d-106">合併式複寫通常會在伺服器至用戶端環境中使用。</span><span class="sxs-lookup"><span data-stu-id="b861d-106">Merge replication is typically used in server-to-client environments.</span></span> <span data-ttu-id="b861d-107">合併式複寫適合於下列任何情況：</span><span class="sxs-lookup"><span data-stu-id="b861d-107">Merge replication is appropriate in any of the following situations:</span></span>

-   <span data-ttu-id="b861d-108">多個訂閱者可能會在不同時間更新相同的資料，並將這些變更傳播到發行者與其他訂閱者。</span><span class="sxs-lookup"><span data-stu-id="b861d-108">Multiple Subscribers might update the same data at various times and propagate those changes to the Publisher and to other Subscribers.</span></span>

-   <span data-ttu-id="b861d-109">「訂閱者」需要接收資料、離線變更資料，稍後同步變更「發行者」和其他「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="b861d-109">Subscribers need to receive data, make changes offline, and later synchronize changes with the Publisher and other Subscribers.</span></span>

-   <span data-ttu-id="b861d-110">每個訂閱者需要一個不同的資料分割。</span><span class="sxs-lookup"><span data-stu-id="b861d-110">Each Subscriber requires a different partition of data.</span></span>

-   <span data-ttu-id="b861d-111">可能會發生衝突，而在發生衝突時，您需要偵測與解決衝突的能力。</span><span class="sxs-lookup"><span data-stu-id="b861d-111">Conflicts might occur and, when they do, you need the ability to detect and resolve them.</span></span>

-   <span data-ttu-id="b861d-112">應用程式需要淨資料變更，而非對中繼資料狀態的存取。</span><span class="sxs-lookup"><span data-stu-id="b861d-112">The application requires net data change rather than access to intermediate data states.</span></span> <span data-ttu-id="b861d-113">例如，如果資料列在「訂閱者」與「發行者」同步之前，於「訂閱者」端變更了五次，則該資料列只需在「發行者」端變更一次，以反映最終資料變更 (即第五次的值)。</span><span class="sxs-lookup"><span data-stu-id="b861d-113">For example, if a row changes five times at a Subscriber before it synchronizes with a Publisher, the row will change only once at the Publisher to reflect the net data change (that is, the fifth value).</span></span>

 <span data-ttu-id="b861d-114">合併式複寫允許各站台自發地工作，然後將更新合併到單一的統一結果。</span><span class="sxs-lookup"><span data-stu-id="b861d-114">Merge replication allows various sites to work autonomously and later merge updates into a single, uniform result.</span></span> <span data-ttu-id="b861d-115">因為是在多個節點更新，所以相同的資料可能已由發行者和多個訂閱者更新。</span><span class="sxs-lookup"><span data-stu-id="b861d-115">Because updates are made at more than one node, the same data may have been updated by the Publisher and by more than one Subscriber.</span></span> <span data-ttu-id="b861d-116">因此，合併更新時可能會發生衝突，而合併式複寫提供數個處理衝突的方法。</span><span class="sxs-lookup"><span data-stu-id="b861d-116">Therefore, conflicts can occur when updates are merged and merge replication provides a number of ways to handle conflicts.</span></span>

 <span data-ttu-id="b861d-117">合併式複寫是由「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 快照集代理程式」與「合併代理程式」所實作。</span><span class="sxs-lookup"><span data-stu-id="b861d-117">Merge replication is implemented by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Snapshot Agent and Merge Agent.</span></span> <span data-ttu-id="b861d-118">如果發行集未經篩選或使用靜態篩選，則「快照集代理程式」會建立單一快照集。</span><span class="sxs-lookup"><span data-stu-id="b861d-118">If the publication is unfiltered or uses static filters, the Snapshot Agent creates a single snapshot.</span></span> <span data-ttu-id="b861d-119">如果發行集使用參數化篩選，則「快照集代理程式」會為資料的各資料分割建立快照集。</span><span class="sxs-lookup"><span data-stu-id="b861d-119">If the publication uses parameterized filters, the Snapshot Agent creates a snapshot for each partition of data.</span></span> <span data-ttu-id="b861d-120">「合併代理程式」會將初始快照集套用至「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="b861d-120">The Merge Agent applies the initial snapshots to the Subscribers.</span></span> <span data-ttu-id="b861d-121">另外這會合併建立初始快照集之後在「發行者」或「訂閱者」端發生的累加資料變更，並且偵測是否發生任何衝突，並根據您設定的規則加以解決。</span><span class="sxs-lookup"><span data-stu-id="b861d-121">It also merges incremental data changes that occurred at the Publisher or Subscribers after the initial snapshot was created, and detects and resolves any conflicts according to rules you configure.</span></span>

 <span data-ttu-id="b861d-122">若要追蹤變更，合併式複寫 (和具有佇列更新訂閱的異動複寫) 必須可以唯一地識別每個已發行資料表中的每個資料列。</span><span class="sxs-lookup"><span data-stu-id="b861d-122">To track changes, merge replication (and transactional replication with queued updating subscriptions) must be able to uniquely identify every row in every published table.</span></span> <span data-ttu-id="b861d-123">若要完整此操作，合併式複寫會將資料行 `rowguid` 加入至每個資料表 (除非資料表已經擁有的資料行是包含 `uniqueidentifier` 屬性集的 `ROWGUIDCOL` 資料類型 (在此情況下將使用此資料行))。</span><span class="sxs-lookup"><span data-stu-id="b861d-123">To accomplish this merge replication adds the column `rowguid` to every table, unless the table already has a column of data type `uniqueidentifier` with the `ROWGUIDCOL` property set (in which case this column is used).</span></span> <span data-ttu-id="b861d-124">如果從發行集卸除資料表，`rowguid` 資料行會遭到移除；如果現有資料行是用來進行追蹤，則不會移除資料行。</span><span class="sxs-lookup"><span data-stu-id="b861d-124">If the table is dropped from the publication, the `rowguid` column is removed; if an existing column was used for tracking, the column is not removed.</span></span> <span data-ttu-id="b861d-125">篩選不得包含複寫識別資料列所使用的 `rowguidcol`。</span><span class="sxs-lookup"><span data-stu-id="b861d-125">A filter must not include the `rowguidcol` used by replication to identify rows.</span></span> <span data-ttu-id="b861d-126">`newid()` 函數的提供是為了當做 `rowguid` 資料行的預設值，不過客戶可以提供每個資料列的 GUID (如有需要)。</span><span class="sxs-lookup"><span data-stu-id="b861d-126">The `newid()` function is provided as a default for the `rowguid` column, however customers can provide a guid for each row if needed.</span></span> <span data-ttu-id="b861d-127">但是，請勿提供值 00000000-0000-0000-0000-000000000000。</span><span class="sxs-lookup"><span data-stu-id="b861d-127">However, do not provide value 00000000-0000-0000-0000-000000000000.</span></span>

 <span data-ttu-id="b861d-128">下圖顯示合併複寫中使用的元件。</span><span class="sxs-lookup"><span data-stu-id="b861d-128">The following diagram shows the components used in merge replication.</span></span>

 <span data-ttu-id="b861d-129">![合併式複寫元件和資料流程](../media/merge.gif "合併式複寫元件和資料流程")</span><span class="sxs-lookup"><span data-stu-id="b861d-129">![Merge replication components and data flow](../media/merge.gif "Merge replication components and data flow")</span></span>


