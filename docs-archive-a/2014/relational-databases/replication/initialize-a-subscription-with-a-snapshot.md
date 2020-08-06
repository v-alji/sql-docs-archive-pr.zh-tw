---
title: 使用快照集初始化訂閱 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], initializing subscriptions
- initializing subscriptions [SQL Server replication], snapshots
ms.assetid: 77a9ade2-cdc0-4ae9-a02d-6e29d7c2ada0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f8b776e71e9d1197bc174169aee8ccf692884308
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585828"
---
# <a name="initialize-a-subscription-with-a-snapshot"></a><span data-ttu-id="473be-102">使用快照集初始化訂閱</span><span class="sxs-lookup"><span data-stu-id="473be-102">Initialize a Subscription with a Snapshot</span></span>
  <span data-ttu-id="473be-103">建立發行集之後，通常會建立初始快照集，並將其複製到快照集資料夾 (使用「新增發行集精靈」建立的合併式發行集預設均會發生此情況)。</span><span class="sxs-lookup"><span data-stu-id="473be-103">After a publication has been created, an initial snapshot is typically created and copied to the snapshot folder (this occurs by default for merge publications created with the New Publication Wizard).</span></span> <span data-ttu-id="473be-104">然後，在訂閱的初始同步處理期間，由「散發代理程式」(針對交易式和快取式發行集) 或「合併代理程式」(針對合併式發行集) 套用至「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="473be-104">It is then applied to the Subscriber by the Distribution Agent (for transactional and snapshot publications) or the Merge Agent (for merge publications) during the initial synchronization of the subscription.</span></span> <span data-ttu-id="473be-105">快照集處理取決於發行集的類型：</span><span class="sxs-lookup"><span data-stu-id="473be-105">The snapshot process depends on the type of publication:</span></span>  
  
-   <span data-ttu-id="473be-106">如果快照集用於不使用參數化篩選的快照式發行集、交易式發行集或合併式發行集，則快照集會在大量複製程式 (bcp) 檔案中包含結構描述，還會包含複寫所需的條件約束、擴充屬性、索引、觸發程序和系統資料表。</span><span class="sxs-lookup"><span data-stu-id="473be-106">If the snapshot is for a snapshot publication, a transactional publication, or a merge publication that doesn't use parameterized filters, the snapshot contains the schema and data in bulk copy program (bcp) files, as well as constraints, extended properties, indexes, triggers, and the system tables necessary for replication.</span></span> <span data-ttu-id="473be-107">如需建立和套用快照集的詳細資訊，請參閱[建立和套用快照集](create-and-apply-the-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="473be-107">For more information about creating and applying the snapshot, see [Create and Apply the Snapshot](create-and-apply-the-snapshot.md).</span></span>  
  
-   <span data-ttu-id="473be-108">若快照集是專為使用參數化篩選的合併式發行集而產生，該快照集會使用兩部份處理建立而成。</span><span class="sxs-lookup"><span data-stu-id="473be-108">If the snapshot is for a merge publication that uses parameterized filters, the snapshot is created using a two-part process.</span></span> <span data-ttu-id="473be-109">首先建立結構描述快照集，其中包含複寫指令碼和已發行物件的結構描述，但不包含資料。</span><span class="sxs-lookup"><span data-stu-id="473be-109">First a schema snapshot is created that contains the replication scripts and the schema of the published objects, but not the data.</span></span> <span data-ttu-id="473be-110">接下來每個訂閱皆以快照集初始化，該快照集中包含從結構描述快照集複製而來的指令碼和結構描述，以及屬於訂閱分割的資料。</span><span class="sxs-lookup"><span data-stu-id="473be-110">Each subscription is then initialized with a snapshot that includes the scripts and schema copied from the schema snapshot and the data that belongs to the subscription's partition.</span></span> <span data-ttu-id="473be-111">如需詳細資訊，請參閱 [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="473be-111">For more information, see [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md).</span></span>  
  
 <span data-ttu-id="473be-112">依照您發行集的複寫類型和發行項不同，快照集的組成檔案會不一樣。</span><span class="sxs-lookup"><span data-stu-id="473be-112">The snapshot consists of different files depending on the type of replication and the articles in your publication.</span></span> <span data-ttu-id="473be-113">這些檔案會複製到設定「散發者」時指定的預設快照集資料夾，或建立發行集時指定的替代快照集資料夾。</span><span class="sxs-lookup"><span data-stu-id="473be-113">These files are copied to the default snapshot folder specified when the Distributor was configured or the alternate snapshot folder specified when the publication was created.</span></span>  
  
|<span data-ttu-id="473be-114">複寫類型</span><span class="sxs-lookup"><span data-stu-id="473be-114">Type of Replication</span></span>|<span data-ttu-id="473be-115">一般快照集檔</span><span class="sxs-lookup"><span data-stu-id="473be-115">Common Snapshot Files</span></span>|  
|-------------------------|---------------------------|  
|<span data-ttu-id="473be-116">快照式複寫或異動複寫</span><span class="sxs-lookup"><span data-stu-id="473be-116">Snapshot Replication or Transactional Replication</span></span>|<span data-ttu-id="473be-117">結構描述 (.sch)、資料 (.bcp)、條件約束和索引 (.dri)、條件約束 (.idx)、觸發程序 (.trg，僅用於「訂閱者」) 以及壓縮的快照集檔案 (.cab)。</span><span class="sxs-lookup"><span data-stu-id="473be-117">schema (.sch); data (.bcp); constraints and indexes (.dri); constraints (.idx); triggers (.trg):for updating Subscribers only; compressed snapshot files (.cab).</span></span>|  
|<span data-ttu-id="473be-118">合併式複寫</span><span class="sxs-lookup"><span data-stu-id="473be-118">Merge Replication</span></span>|<span data-ttu-id="473be-119">結構描述 (.sch)、資料 (.bcp)、條件約束和索引 (.dri)、觸發程序 (.trg)、系統資料表資料 (.sys)、衝突資料表 (.cft) 以及壓縮的快照集檔案 (.cab)。</span><span class="sxs-lookup"><span data-stu-id="473be-119">schema (.sch); data (.bcp); constraints and indexes (.dri); triggers (.trg); system table data (.sys); conflict tables (.cft); compressed snapshot files (.cab).</span></span>|  
  
 <span data-ttu-id="473be-120">若快照集傳送期間中斷，會自動繼續並且不會重新傳送之前已傳送完成的檔案。</span><span class="sxs-lookup"><span data-stu-id="473be-120">If the snapshot transfer is interrupted at any point, it will automatically resume and will not resend any files that have already been completely transferred.</span></span> <span data-ttu-id="473be-121">快照集代理程式的傳遞單位是每個發行集發行項的 bcp 檔案，這樣一來，只傳遞一部份的檔案就必須整個重新傳遞。</span><span class="sxs-lookup"><span data-stu-id="473be-121">The unit of delivery for the Snapshot Agent is the bcp file for each publication article, so files that are partially delivered must be completely redelivered.</span></span> <span data-ttu-id="473be-122">不過，繼續快照集可大幅減少資料傳輸量，且即使連接不穩定，也可以確保即時傳遞快照集。</span><span class="sxs-lookup"><span data-stu-id="473be-122">However, resuming the snapshot can significantly reduce the amount of data transmitted and ensure timely snapshot delivery even if the connection is unreliable.</span></span>  
  
## <a name="snapshot-options"></a><span data-ttu-id="473be-123">快照集選項</span><span class="sxs-lookup"><span data-stu-id="473be-123">Snapshot Options</span></span>  
 <span data-ttu-id="473be-124">使用快照集初始化訂閱時，可以使用下列選項。</span><span class="sxs-lookup"><span data-stu-id="473be-124">There are a number of options available when initializing a subscription with a snapshot.</span></span> <span data-ttu-id="473be-125">您可以：</span><span class="sxs-lookup"><span data-stu-id="473be-125">You can:</span></span>  
  
-   <span data-ttu-id="473be-126">指定代替預設快照集資料夾位置的替代快照集資料夾位置，或同時指定這兩個位置。</span><span class="sxs-lookup"><span data-stu-id="473be-126">Specify an alternate snapshot folder location instead of, or in addition, to the default snapshot folder location.</span></span> <span data-ttu-id="473be-127">如需相關資訊，請參閱 [Alternate Snapshot Folder Locations](alternate-snapshot-folder-locations.md)。</span><span class="sxs-lookup"><span data-stu-id="473be-127">For more information, see [Alternate Snapshot Folder Locations](alternate-snapshot-folder-locations.md).</span></span>  
  
-   <span data-ttu-id="473be-128">壓縮快照集以儲存在抽取式媒體，或者透過慢速網路傳送。</span><span class="sxs-lookup"><span data-stu-id="473be-128">Compress snapshots for storage on removable media or for transfer over a slow network.</span></span> <span data-ttu-id="473be-129">如需詳細資訊，請參閱＜ [Compressed Snapshots](compressed-snapshots.md)＞。</span><span class="sxs-lookup"><span data-stu-id="473be-129">For more information, see [Compressed Snapshots](compressed-snapshots.md).</span></span>  
  
-   <span data-ttu-id="473be-130">在套用快照集之前及之後執行 Transact-SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="473be-130">Execute Transact-SQL scripts before or after the snapshot is applied.</span></span> <span data-ttu-id="473be-131">如需詳細資訊，請參閱[在套用快照集之前及之後執行指令碼](snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied)。</span><span class="sxs-lookup"><span data-stu-id="473be-131">For more information, see [Execute Scripts Before and After the Snapshot Is Applied](snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied).</span></span>  
  
-   <span data-ttu-id="473be-132">使用檔案傳輸通訊協定 (FTP) 傳送快照集檔案。</span><span class="sxs-lookup"><span data-stu-id="473be-132">Transfer snapshot files using File Transfer Protocol (FTP).</span></span> <span data-ttu-id="473be-133">如需詳細資訊，請參閱[透過 FTP 傳送快照集](transfer-snapshots-through-ftp.md)。</span><span class="sxs-lookup"><span data-stu-id="473be-133">For more information, see [Transfer Snapshots Through FTP](transfer-snapshots-through-ftp.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="473be-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="473be-134">See Also</span></span>  
 <span data-ttu-id="473be-135">[初始化訂閱](initialize-a-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="473be-135">[Initialize a Subscription](initialize-a-subscription.md) </span></span>  
 [<span data-ttu-id="473be-136">保護快照集資料夾</span><span class="sxs-lookup"><span data-stu-id="473be-136">Secure the Snapshot Folder</span></span>](security/secure-the-snapshot-folder.md)  
  
  
