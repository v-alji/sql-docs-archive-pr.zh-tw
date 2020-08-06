---
title: 在現有發行集中新增和卸除發行項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], dropping
- deleting articles
- removing articles
- dropping articles
- adding articles
- administering replication, articles
- publications [SQL Server replication], adding and dropping articles
- articles [SQL Server replication], adding
ms.assetid: b148e907-e1f2-483b-bdb2-59ea596efceb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f72f15886e7105dde8d0e15dd0598a7474ed7e39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606765"
---
# <a name="add-articles-to-and-drop-articles-from-existing-publications"></a><span data-ttu-id="1c835-102">在現有發行集中加入和卸除發行項</span><span class="sxs-lookup"><span data-stu-id="1c835-102">Add Articles to and Drop Articles from Existing Publications</span></span>
  <span data-ttu-id="1c835-103">建立發行集後，可以新增或卸除發行項。</span><span class="sxs-lookup"><span data-stu-id="1c835-103">After a publication is created, it is possible to add and drop articles.</span></span> <span data-ttu-id="1c835-104">發行項可以隨時新增，但卸除發行項所需的動作取決於複寫的類型以及卸除發行項的時機。</span><span class="sxs-lookup"><span data-stu-id="1c835-104">Articles can be added at any time, but the actions required for dropping articles depend on the type of replication and when the article is dropped.</span></span>  
  
## <a name="adding-articles"></a><span data-ttu-id="1c835-105">加入發行項</span><span class="sxs-lookup"><span data-stu-id="1c835-105">Adding Articles</span></span>  
 <span data-ttu-id="1c835-106">新增發行項涉及的動作包括：在發行集中新增發行項、建立發行集的新快照集、同步處理訂閱以套用新發行項的結構描述和資料。</span><span class="sxs-lookup"><span data-stu-id="1c835-106">Adding an article involves: adding the article to the publication; creating a new snapshot for the publication; synchronizing the subscription to apply the schema and data for the new article.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c835-107">如果您將發行項新增至合併式發行集且現有某發行項相依於新的發行項，則您必須使用 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) 和 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) 的 **\@processing_order** 參數來指定兩個發行項的處理順序。</span><span class="sxs-lookup"><span data-stu-id="1c835-107">If you add an article to a merge publication and an existing article depends on the new article, you must specify a processing order for both articles using the **\@processing_order** parameter of [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) and [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="1c835-108">請考慮下列狀況：您發行資料表但未發行該資料表所參考的函數。</span><span class="sxs-lookup"><span data-stu-id="1c835-108">Consider the following scenario: you publish a table but you do not publish a function that the table references.</span></span> <span data-ttu-id="1c835-109">如果您未發行該函數，該資料表就無法在「訂閱者」端建立。</span><span class="sxs-lookup"><span data-stu-id="1c835-109">If you do not publish the function, the table cannot be created at the Subscriber.</span></span> <span data-ttu-id="1c835-110">當您將函式新增至發行集時：請將 **sp_addmergearticle** 的 **\@processing_order** 參數值指定為 **1**；並將 **sp_changemergearticle** 的 **\@processing_order** 參數值指定為 **2**，指定 **\@article** 參數的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="1c835-110">When you add the function to the publication: specify a value of **1** for the **\@processing_order** parameter of **sp_addmergearticle**; and specify a value of **2** for the **\@processing_order** parameter of **sp_changemergearticle**, specifying the table name for the parameter **\@article**.</span></span> <span data-ttu-id="1c835-111">此處理順序可確保您先在「訂閱者」端建立函數之後才建立相依於此函數的資料表。</span><span class="sxs-lookup"><span data-stu-id="1c835-111">This processing order ensures that you create the function at the Subscriber before the table that depends on it.</span></span> <span data-ttu-id="1c835-112">您可對每個發行項使用不同的編號，只要函數的編號低於資料表的編號即可。</span><span class="sxs-lookup"><span data-stu-id="1c835-112">You can use different numbers for each article, as long as the number for the function is lower than the number for the table.</span></span>  
  
1.  <span data-ttu-id="1c835-113">透過下列方法之一新增一或多個發行項：</span><span class="sxs-lookup"><span data-stu-id="1c835-113">Add one or more articles through one of the following methods:</span></span>  
  
    -   [<span data-ttu-id="1c835-114">在發行集中新增和卸除發行項 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="1c835-114">Add Articles to and Drop Articles from a Publication &#40;SQL Server Management Studio&#41;</span></span>](add-articles-to-and-drop-articles-from-a-publication.md)  
  
    -   [<span data-ttu-id="1c835-115">定義發行項</span><span class="sxs-lookup"><span data-stu-id="1c835-115">Define an Article</span></span>](define-an-article.md)  
  
2.  <span data-ttu-id="1c835-116">新增發行項到發行集後，您必須為發行集 (和所有資料分割，如果該發行集為含參數化篩選的合併式發行集) 建立一個新快照集。</span><span class="sxs-lookup"><span data-stu-id="1c835-116">After adding an article to a publication, you must create a new snapshot for the publication (and all partitions if it is a merge publication with parameterized filters).</span></span> <span data-ttu-id="1c835-117">隨後，「散發代理程式」或「合併代理程式」會將新發行項的結構描述和資料複製到「訂閱者」 (不會重新初始化整個發行集)。</span><span class="sxs-lookup"><span data-stu-id="1c835-117">The Distribution Agent or Merge Agent then copies the schema and data for the new article to the Subscriber (it does not reinitialize the entire publication).</span></span>  
  
    -   <span data-ttu-id="1c835-118">若要建立新的快照集，請參閱＜ [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md)＞。</span><span class="sxs-lookup"><span data-stu-id="1c835-118">To create a new snapshot, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
    -   <span data-ttu-id="1c835-119">若要使用參數化篩選建立合併式發行集的新快照集，請參閱[使用參數化篩選建立合併式發行集的快照集](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="1c835-119">To create a new snapshot for a merge publication with parameterized filters, see [Create a Snapshot for a Merge Publication with Parameterized Filters](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).</span></span>  
  
3.  <span data-ttu-id="1c835-120">建立快照集後，同步處理訂閱，以複製新發行項的結構描述和資料。</span><span class="sxs-lookup"><span data-stu-id="1c835-120">After the snapshot is created, synchronize the subscription to copy the schema and data for the new article.</span></span>  
  
    -   <span data-ttu-id="1c835-121">若要同步處理發送訂閱，請參閱＜ [Synchronize a Push Subscription](../synchronize-a-push-subscription.md)＞。</span><span class="sxs-lookup"><span data-stu-id="1c835-121">To synchronize a push subscription, see [Synchronize a Push Subscription](../synchronize-a-push-subscription.md).</span></span>  
  
    -   <span data-ttu-id="1c835-122">若要同步處理提取訂閱，請參閱＜ [Synchronize a Pull Subscription](../synchronize-a-pull-subscription.md)＞。</span><span class="sxs-lookup"><span data-stu-id="1c835-122">To synchronize a pull subscription, see [Synchronize a Pull Subscription](../synchronize-a-pull-subscription.md).</span></span>  
  
## <a name="dropping-articles"></a><span data-ttu-id="1c835-123">卸除發行項</span><span class="sxs-lookup"><span data-stu-id="1c835-123">Dropping Articles</span></span>  
 <span data-ttu-id="1c835-124">發行項可以隨時從發行集中卸除，但必須考慮下列行為：</span><span class="sxs-lookup"><span data-stu-id="1c835-124">Articles can be dropped from a publication at any time, but you must take into account the following behaviors:</span></span>  
  
-   <span data-ttu-id="1c835-125">從發行集中卸除發行項不會從發行集資料庫中移除物件，或從訂閱資料庫中移除對應物件。</span><span class="sxs-lookup"><span data-stu-id="1c835-125">Dropping an article from a publication does not remove the object from the publication database or the corresponding object from the subscription database.</span></span> <span data-ttu-id="1c835-126">必要時請使用 DROP \<Object> 來移除這些物件。</span><span class="sxs-lookup"><span data-stu-id="1c835-126">Use DROP \<Object> to remove these objects if necessary.</span></span> <span data-ttu-id="1c835-127">透過外部索引鍵條件約束卸除與其他已發佈發行項相關的發行項時，建議手動卸除訂閱者端的資料表，或執行視需要的指令碼：指定包含適當 DROP \<Object> 陳述式的指令碼。</span><span class="sxs-lookup"><span data-stu-id="1c835-127">When you drop an article that is related to other published articles through foreign key constraints, we recommend that you drop the table at the Subscriber manually or by using on-demand script execution: specify a script that includes the appropriate DROP \<Object> statements.</span></span> <span data-ttu-id="1c835-128">如需詳細資訊，請參閱[在同步處理期間執行指令碼 &#40;複寫 Transact-SQL 程式設計&#41;](../execute-scripts-during-synchronization-replication-transact-sql-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="1c835-128">For more information, see [Execute Scripts During Synchronization &#40;Replication Transact-SQL Programming&#41;](../execute-scripts-during-synchronization-replication-transact-sql-programming.md).</span></span>  
  
-   <span data-ttu-id="1c835-129">如果合併式發行集的相容性層級為 90RTM 或更高，可以隨時卸除發行項，但需要一個新快照集。</span><span class="sxs-lookup"><span data-stu-id="1c835-129">For merge publications with a compatibility level of 90RTM or higher, articles can be dropped at any time, but a new snapshot is required.</span></span> <span data-ttu-id="1c835-130">此外：</span><span class="sxs-lookup"><span data-stu-id="1c835-130">Additionally:</span></span>  
  
    -   <span data-ttu-id="1c835-131">如果發行項是聯結篩選或邏輯記錄關聯性中的父發行項，則必須先卸除此關聯性 (需要重新初始化)。</span><span class="sxs-lookup"><span data-stu-id="1c835-131">If an article is a parent article in a join filter or logical record relationship, the relationships must be dropped first, which requires reinitialization.</span></span>  
  
    -   <span data-ttu-id="1c835-132">如果發行項含發行集中的最終參數化篩選，則訂閱必須重新初始化。</span><span class="sxs-lookup"><span data-stu-id="1c835-132">If an article has the last parameterized filter in a publication, subscriptions must be reinitialized.</span></span>  
  
-   <span data-ttu-id="1c835-133">對於相容性層級低於 90RTM 的合併式發行集，可以在訂閱的初始同步處理之前卸除發行項，無需特殊考量。</span><span class="sxs-lookup"><span data-stu-id="1c835-133">For merge publications with a compatibility level lower than 90RTM, articles can be dropped with no special considerations prior to the initial synchronization of subscriptions.</span></span> <span data-ttu-id="1c835-134">如果在同步處理一個或多個訂閱後卸除發行項，則必須卸除、重新建立並同步處理訂閱。</span><span class="sxs-lookup"><span data-stu-id="1c835-134">If an article is dropped after one or more subscriptions is synchronized, the subscriptions must be dropped, re-created, and synchronized.</span></span>  
  
-   <span data-ttu-id="1c835-135">對於快照式或交易式發行集，可以在建立訂閱之前卸除發行項，無需特殊考量。</span><span class="sxs-lookup"><span data-stu-id="1c835-135">For snapshot or transactional publications, articles can be dropped with no special considerations prior to subscriptions being created.</span></span> <span data-ttu-id="1c835-136">如果在建立一或多個訂閱後卸除發行項，則必須卸除、重新建立並同步處理訂閱。</span><span class="sxs-lookup"><span data-stu-id="1c835-136">If an article is dropped after one or more subscriptions is created, the subscriptions must be dropped, recreated, and synchronized.</span></span> <span data-ttu-id="1c835-137">如需卸除訂閱的詳細資訊，請參閱[訂閱發行集](../subscribe-to-publications.md)和 [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1c835-137">For more information about dropping subscriptions, see [Subscribe to Publications](../subscribe-to-publications.md) and [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql).</span></span> <span data-ttu-id="1c835-138">**sp_dropsubscription** 允許您從訂閱中卸除單一發行項，而非整個訂閱。</span><span class="sxs-lookup"><span data-stu-id="1c835-138">**sp_dropsubscription** allows you to drop a single article from the subscription rather than the entire subscription.</span></span>  
  
1.  <span data-ttu-id="1c835-139">從發行集中卸除發行項涉及卸除發行項並建立該發行集的新快照集。</span><span class="sxs-lookup"><span data-stu-id="1c835-139">Dropping an article from a publication involves dropping the article and creating a new snapshot for the publication.</span></span> <span data-ttu-id="1c835-140">卸除發行項會使目前快照集無效，因此必須建立新快照集。</span><span class="sxs-lookup"><span data-stu-id="1c835-140">Dropping an article invalidates the current snapshot; therefore a new snapshot must be created.</span></span>  
  
    -   <span data-ttu-id="1c835-141">若要從發行集卸除發行項，請參閱[在發行集中新增和卸除發行項 (&#40;SQL Server Management Studio&#41;](add-articles-to-and-drop-articles-from-a-publication.md) 或[刪除發行項](delete-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="1c835-141">To drop an article from a publication, see [Add Articles to and Drop Articles from a Publication &#40;SQL Server Management Studio&#41;](add-articles-to-and-drop-articles-from-a-publication.md) or [Delete an Article](delete-an-article.md).</span></span>  
  
2.  <span data-ttu-id="1c835-142">從發行集中卸除發行項後，您必須為發行集 (和所有資料分割，如果該發行集為含有參數化篩選的合併式發行集) 建立一個新快照集。</span><span class="sxs-lookup"><span data-stu-id="1c835-142">After dropping an article from a publication, you must create a new snapshot for the publication (and all partitions if it is a merge publication with parameterized filters).</span></span>  
  
    -   <span data-ttu-id="1c835-143">若要建立新的快照集，請參閱＜ [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md)＞。</span><span class="sxs-lookup"><span data-stu-id="1c835-143">To create a new snapshot, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
    -   <span data-ttu-id="1c835-144">若要使用參數化篩選建立合併式發行集的新快照集，請參閱[使用參數化篩選建立合併式發行集的快照集](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="1c835-144">To create a new snapshot for a merge publication with parameterized filters, see [Create a Snapshot for a Merge Publication with Parameterized Filters](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).</span></span>  
  
 <span data-ttu-id="1c835-145">如上所提到的，在某些情況下，卸除發行項需要卸除、重新建立並同步處理訂閱。</span><span class="sxs-lookup"><span data-stu-id="1c835-145">As noted above, in some cases dropping an article requires subscriptions to be dropped, recreated, and then synchronized.</span></span> <span data-ttu-id="1c835-146">如需詳細資訊，請參閱[訂閱發行集](../subscribe-to-publications.md)和[同步處理資料](../synchronize-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1c835-146">For more information, see [Subscribe to Publications](../subscribe-to-publications.md) and [Synchronize Data](../synchronize-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c835-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c835-147">See Also</span></span>  
 <span data-ttu-id="1c835-148">[發行資料和資料庫物件](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="1c835-148">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="1c835-149">[重新初始化訂閱](../reinitialize-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="1c835-149">[Reinitialize Subscriptions](../reinitialize-subscriptions.md) </span></span>  
 [<span data-ttu-id="1c835-150">對發行集資料庫進行結構描述變更</span><span class="sxs-lookup"><span data-stu-id="1c835-150">Make Schema Changes on Publication Databases</span></span>](make-schema-changes-on-publication-databases.md)  
  
  
