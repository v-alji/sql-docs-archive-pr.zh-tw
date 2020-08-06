---
title: 同步處理資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], about synchronization
- merge replication synchronization [SQL Server replication]
- scripts [SQL Server replication], synchronization and
- synchronization [SQL Server replication]
- snapshot replication [SQL Server], synchronization
- transactional replication, synchronization
- subscriptions [SQL Server replication], synchronizing
- on demand script execution
- replication [SQL Server], synchronization
- scripts [SQL Server replication]
ms.assetid: 724802f7-7d69-46d3-a330-bd8aa7f53114
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c92cc4d1ae8e836f169a731ecf3c37c81f3dbf10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701014"
---
# <a name="synchronize-data"></a><span data-ttu-id="88165-102">同步處理資料</span><span class="sxs-lookup"><span data-stu-id="88165-102">Synchronize Data</span></span>
  <span data-ttu-id="88165-103">同步資料是指在「訂閱者」端套用初始快照集後，在「發行者」與「訂閱者」之間傳播資料和結構描述變更的處理。</span><span class="sxs-lookup"><span data-stu-id="88165-103">Synchronizing data refers to the process of data and schema changes being propagated between the Publisher and Subscribers after the initial snapshot has been applied at the Subscriber.</span></span> <span data-ttu-id="88165-104">同步處理將會：</span><span class="sxs-lookup"><span data-stu-id="88165-104">Synchronization can occur:</span></span>  
  
-   <span data-ttu-id="88165-105">連續發生，一般出現在異動複寫中。</span><span class="sxs-lookup"><span data-stu-id="88165-105">Continuously, which is typical for transactional replication.</span></span>  
  
-   <span data-ttu-id="88165-106">視需要發生，一般出現在合併式複寫中。</span><span class="sxs-lookup"><span data-stu-id="88165-106">On demand, which is typical for merge replication.</span></span>  
  
-   <span data-ttu-id="88165-107">在排程時間發生，一般出現在快照式複寫中。</span><span class="sxs-lookup"><span data-stu-id="88165-107">On a schedule, which is typical for snapshot replication.</span></span>  
  
 <span data-ttu-id="88165-108">同步處理訂閱時，根據使用的複寫類型將發生不同的處理：</span><span class="sxs-lookup"><span data-stu-id="88165-108">When a subscription is synchronized, different processes occur based on the type of replication you are using:</span></span>  
  
-   <span data-ttu-id="88165-109">快照式複寫。</span><span class="sxs-lookup"><span data-stu-id="88165-109">Snapshot replication.</span></span> <span data-ttu-id="88165-110">同步處理意味著「散發代理程式」在「訂閱者」端重新套用快照集，以使訂閱資料庫中的結構描述和資料與發行集資料庫保持一致。</span><span class="sxs-lookup"><span data-stu-id="88165-110">Synchronization means that the Distribution Agent reapplies the snapshot at the Subscriber so that schema and data at the subscription database is consistent with the publication database.</span></span>  
  
     <span data-ttu-id="88165-111">如果在「發行者」端對資料或結構描述作了修改，則必須生成新的快照集，以將修改傳播到「訂閱者」端。</span><span class="sxs-lookup"><span data-stu-id="88165-111">If modifications to data or schema have been made at the Publisher, a new snapshot must be generated in order to propagate modifications to the Subscriber.</span></span>  
  
-   <span data-ttu-id="88165-112">異動複寫。</span><span class="sxs-lookup"><span data-stu-id="88165-112">Transactional replication.</span></span> <span data-ttu-id="88165-113">同步處理意味著「散發代理程式」將更新、插入、刪除和其他更改從散發資料庫傳送到「訂閱者」端。</span><span class="sxs-lookup"><span data-stu-id="88165-113">Synchronization means that the Distribution Agent transfers updates, inserts, deletes, and any other changes from the distribution database to the Subscriber.</span></span>  
  
-   <span data-ttu-id="88165-114">合併式複寫。</span><span class="sxs-lookup"><span data-stu-id="88165-114">Merge replication.</span></span> <span data-ttu-id="88165-115">同步處理意味著「合併代理程式」將更改從「訂閱者」端上傳到「發行者」端，然後再將更改從「發行者」端下載到「訂閱者」端。</span><span class="sxs-lookup"><span data-stu-id="88165-115">Synchronization means that the Merge Agent uploads changes from the Subscriber to the Publisher and then downloads changes from the Publisher to the Subscriber.</span></span> <span data-ttu-id="88165-116">當有衝突時會進行偵測並解決。</span><span class="sxs-lookup"><span data-stu-id="88165-116">Conflicts, if any, are detected and resolved.</span></span> <span data-ttu-id="88165-117">資料會被聚合，最終「發行者」端和所有「訂閱者」端都將得到相同的資料值。</span><span class="sxs-lookup"><span data-stu-id="88165-117">Data is converged, and the Publisher and all Subscribers eventually end up with the same data values.</span></span> <span data-ttu-id="88165-118">如果偵測到並解決了衝突，則將變更一些使用者認可的工作，以根據您定義的原則來解決衝突。</span><span class="sxs-lookup"><span data-stu-id="88165-118">If conflicts were detected and resolved, work that was committed by some of the users is changed to resolve the conflict according to policies you define.</span></span>  
  
 <span data-ttu-id="88165-119">每次發生同步處理時，快照式發行集都會在「訂閱者」端重新整理整個結構描述，因此所有結構描述變更都將套用至「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="88165-119">Snapshot publications completely refresh the schema at the Subscriber every time synchronization occurs, so all schema changes are applied to the Subscriber.</span></span> <span data-ttu-id="88165-120">異動複寫與合併式複寫還支援最常見的結構描述變更。</span><span class="sxs-lookup"><span data-stu-id="88165-120">Transactional replication and merge replication also support the most common schema changes.</span></span> <span data-ttu-id="88165-121">如需詳細資訊，請參閱[對發行集資料庫進行結構描述變更](publish/make-schema-changes-on-publication-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="88165-121">For more information, see [Make Schema Changes on Publication Databases](publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
 <span data-ttu-id="88165-122">若要同步處理發送訂閱，請參閱＜ [Synchronize a Push Subscription](synchronize-a-push-subscription.md)＞。</span><span class="sxs-lookup"><span data-stu-id="88165-122">To synchronize a push subscription, see [Synchronize a Push Subscription](synchronize-a-push-subscription.md).</span></span>  
  
 <span data-ttu-id="88165-123">若要同步處理提取訂閱，請參閱＜ [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)＞。</span><span class="sxs-lookup"><span data-stu-id="88165-123">To synchronize a pull subscription, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
 <span data-ttu-id="88165-124">若要設定同步處理排程，請參閱＜ [Specify Synchronization Schedules](specify-synchronization-schedules.md)＞。</span><span class="sxs-lookup"><span data-stu-id="88165-124">To set synchronization schedules, see [Specify Synchronization Schedules](specify-synchronization-schedules.md).</span></span>  
  
 <span data-ttu-id="88165-125">**若要檢視並解決同步處理衝突**</span><span class="sxs-lookup"><span data-stu-id="88165-125">**To view and resolve synchronization conflicts**</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="88165-126">:[檢視並解決合併式發行集的資料衝突 &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md)</span><span class="sxs-lookup"><span data-stu-id="88165-126">: [View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md)</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="88165-127">:[檢視交易式發行集的資料衝突 &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="88165-127">: [View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;](view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)</span></span>  
  
## <a name="executing-code-during-synchronization"></a><span data-ttu-id="88165-128">在同步處理期間執行程式碼</span><span class="sxs-lookup"><span data-stu-id="88165-128">Executing Code During Synchronization</span></span>  
 <span data-ttu-id="88165-129">複寫支援兩種同步處理時的程式碼執行方法</span><span class="sxs-lookup"><span data-stu-id="88165-129">Replication supports two methods of executing code during synchronization</span></span>  
  
-   <span data-ttu-id="88165-130">異動複寫與合併式複寫支援視需要的指令碼執行。</span><span class="sxs-lookup"><span data-stu-id="88165-130">On demand script execution is supported for transactional replication and merge replication.</span></span> <span data-ttu-id="88165-131">視需要的指令碼執行可用於指定要在同步處理期間執行的 SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="88165-131">Using on demand script execution you can specify a SQL script to run during synchronization.</span></span> <span data-ttu-id="88165-132">指令碼將複製到「訂閱者」端，並在開始同步處理時使用 **sqlcmd** 來執行。</span><span class="sxs-lookup"><span data-stu-id="88165-132">The script is copied to the Subscriber and executed using **sqlcmd** at the beginning of the synchronization process.</span></span> <span data-ttu-id="88165-133">指令碼套用至「訂閱者」後，便不具有對已複寫變更的存取權。</span><span class="sxs-lookup"><span data-stu-id="88165-133">The script does not have access to the replicated changes as they are applied to the Subscriber.</span></span> <span data-ttu-id="88165-134">如需詳細資訊，請參閱[在同步處理期間執行指令碼 &#40;複寫 Transact-SQL 程式設計&#41;](execute-scripts-during-synchronization-replication-transact-sql-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="88165-134">For more information, see [Execute Scripts During Synchronization &#40;Replication Transact-SQL Programming&#41;](execute-scripts-during-synchronization-replication-transact-sql-programming.md).</span></span>  
  
-   <span data-ttu-id="88165-135">合併式複寫支援商務邏輯處理常式。</span><span class="sxs-lookup"><span data-stu-id="88165-135">Business logic handlers are supported for merge replication.</span></span> <span data-ttu-id="88165-136">您可以使用商務邏輯處理常式架構來撰寫受管理的程式碼組件，該組件將在合併同步處理期間中被呼叫。</span><span class="sxs-lookup"><span data-stu-id="88165-136">Using the business logic handler framework you can write a managed code assembly that is called during the merge synchronization process.</span></span> <span data-ttu-id="88165-137">組件包括可對應至幾種同步處理條件的商務邏輯：資料變更、衝突和錯誤。</span><span class="sxs-lookup"><span data-stu-id="88165-137">The assembly includes business logic that can respond to a number of conditions during synchronization: data changes, conflicts, and errors.</span></span> <span data-ttu-id="88165-138">如需詳細資訊，請參閱[在合併同步處理期間執行商務邏輯](merge/execute-business-logic-during-merge-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="88165-138">For more information, see [Execute Business Logic During Merge Synchronization](merge/execute-business-logic-during-merge-synchronization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88165-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88165-139">See Also</span></span>  
 [<span data-ttu-id="88165-140">偵測及解決合併式複寫衝突</span><span class="sxs-lookup"><span data-stu-id="88165-140">Detect and Resolve Merge Replication Conflicts</span></span>](merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
