---
title: 重新初始化訂閱 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- initializing subscriptions [SQL Server replication], reinitializing
- subscriptions [SQL Server replication], reinitializing
- reinitializing subscriptions
ms.assetid: fb13712b-e7ad-4f1f-b605-4554bad0cb60
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6bf9c68f66a32d1a5ddcf08b845396f815385e83
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709122"
---
# <a name="reinitialize-subscriptions"></a><span data-ttu-id="a7803-102">重新初始化訂閱</span><span class="sxs-lookup"><span data-stu-id="a7803-102">Reinitialize Subscriptions</span></span>
  <span data-ttu-id="a7803-103">重新初始化訂閱涉及將一個或多個發行項的新快照集套用至一個或多個「訂閱者」：交易式和快照式複寫允許重新初始化個別發行項；合併式複寫要求重新初始化所有發行項。</span><span class="sxs-lookup"><span data-stu-id="a7803-103">Reinitializing a subscription involves applying a new snapshot of one or more articles to one or more Subscribers: transactional and snapshot replication allow individual articles to be reinitialized; merge replication requires all articles to be reinitialized.</span></span> <span data-ttu-id="a7803-104">無法重新初始化點對點異動複寫拓撲中的節點。</span><span class="sxs-lookup"><span data-stu-id="a7803-104">Nodes in a peer-to-peer transactional replication topology cannot be reinitialized.</span></span> <span data-ttu-id="a7803-105">如果您必須確定節點有資料的新副本，請在節點還原備份。</span><span class="sxs-lookup"><span data-stu-id="a7803-105">If you need to ensure a node has a new copy of the data, restore a backup at the node.</span></span> <span data-ttu-id="a7803-106">發生重新初始化的情況有兩種：</span><span class="sxs-lookup"><span data-stu-id="a7803-106">Reinitialization occurs for one of two reasons:</span></span>  
  
-   <span data-ttu-id="a7803-107">您將訂閱明確標示為要重新初始化。</span><span class="sxs-lookup"><span data-stu-id="a7803-107">You explicitly mark a subscription for reinitialization.</span></span>  
  
-   <span data-ttu-id="a7803-108">您執行了要求重新初始化的動作，例如屬性變更。</span><span class="sxs-lookup"><span data-stu-id="a7803-108">You perform an action, such as a property change, that requires a reinitialization.</span></span> <span data-ttu-id="a7803-109">如需要求重新初始化動作的詳細資訊，請參閱[變更發行集與發行項屬性](publish/change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="a7803-109">For more information about actions that require reinitialization, see [Change Publication and Article Properties](publish/change-publication-and-article-properties.md).</span></span>  
  
 <span data-ttu-id="a7803-110">在這兩種情況下，「散發代理程式」或「合併代理程式」下次執行時，將為「訂閱者」套用最新的快照集。</span><span class="sxs-lookup"><span data-stu-id="a7803-110">In both cases, the most recent snapshot is applied to the Subscriber the next time the Distribution Agent or the Merge Agent runs.</span></span> <span data-ttu-id="a7803-111">對於快照式和異動複寫，發生重新初始化時，在「訂閱者」端已經作過但尚未與「發行者」同步處理的任何變更，均將被新快照集的應用程式覆寫。</span><span class="sxs-lookup"><span data-stu-id="a7803-111">For snapshot and transactional replication, when reinitialization occurs, any changes made at the Subscriber, but not yet synchronized with the Publisher, are overwritten by the application of the new snapshot.</span></span>  
  
 <span data-ttu-id="a7803-112">對於合併式複寫，您可以選擇在套用快照集之前從「訂閱者」上傳所有資料變更。</span><span class="sxs-lookup"><span data-stu-id="a7803-112">For merge replication, you can choose to have all the data changes uploaded from the Subscriber before the snapshot is applied.</span></span> <span data-ttu-id="a7803-113">「發行者」中任何暫止的結構描述變更都將在「訂閱者」端套用，然後，自上次同步處理之後在「訂閱者」端所作的任何更新都將在套用快照集之前傳播到「發行者」。</span><span class="sxs-lookup"><span data-stu-id="a7803-113">Any pending schema changes from the Publisher are applied at the Subscriber, and then any updates that have been made at the Subscriber since the last synchronization are propagated to the Publisher before the snapshot is reapplied.</span></span> <span data-ttu-id="a7803-114">此行為由 **upload_first** 與 **automatic_reinitialization_policy** 屬性控制；如需詳細資訊，請參閱＜ [Reinitialize a Subscription](reinitialize-a-subscription.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a7803-114">This behavior is controlled by the **upload_first** and **automatic_reinitialization_policy** properties; for more information, see [Reinitialize a Subscription](reinitialize-a-subscription.md).</span></span> <span data-ttu-id="a7803-115">如果使用 SQL Server Management Studio 或「複寫監視器」將訂閱標示為要重新初始化，則在 **[重新初始化訂閱]** 對話方塊中會提供您一個選項來首先上傳變更。</span><span class="sxs-lookup"><span data-stu-id="a7803-115">If you mark a subscription for reinitialization using SQL Server Management Studio or Replication Monitor, you are given an option in the **Reinitialize Subscription(s)** dialog box to upload changes first.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a7803-116">如果在合併式複寫中新增、卸除或變更參數化篩選，則無法在重新初始化期間將「訂閱者」端暫止的變更上傳至「發行者」。</span><span class="sxs-lookup"><span data-stu-id="a7803-116">If you add, drop, or change a parameterized filter in a merge publication, pending changes at the Subscriber cannot be uploaded to the Publisher during reinitialization.</span></span> <span data-ttu-id="a7803-117">如果您要上傳暫止變更，請在變更篩選之前，同步處理所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="a7803-117">If you want to upload pending changes, synchronize all subscriptions before changing the filter.</span></span>  
  
 <span data-ttu-id="a7803-118">如果在建立訂閱時，已指定不會將初始快照集套用至「訂閱者」，然後將該訂閱標示為要重新初始化，則不會套用快照集。</span><span class="sxs-lookup"><span data-stu-id="a7803-118">If, you specified that no initial snapshot was to be applied to the Subscriber when you created the subscription, and you then mark the subscription for reinitialization, a snapshot is not applied.</span></span> <span data-ttu-id="a7803-119">如需詳細資訊，請參閱 [不使用快照集初始化交易式訂閱](initialize-a-transactional-subscription-without-a-snapshot.md)中手動初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="a7803-119">For more information, see [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
 <span data-ttu-id="a7803-120">**若要重新初始化訂閱**</span><span class="sxs-lookup"><span data-stu-id="a7803-120">**To reinitialize a subscription**</span></span>  
  
 <span data-ttu-id="a7803-121">若要重新初始化訂閱中的所有發行項，請使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、預存程序或 Replication Management Objects (RMO)。</span><span class="sxs-lookup"><span data-stu-id="a7803-121">To reinitialize all articles in a subscription, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], stored procedures or Replication Management Objects (RMO).</span></span> <span data-ttu-id="a7803-122">若要重新初始化快照式和交易式發行集中的個別發行項，則必須使用預存程序。</span><span class="sxs-lookup"><span data-stu-id="a7803-122">To reinitialize individual articles in snapshot and transactional publications, you must use stored procedures.</span></span> <span data-ttu-id="a7803-123">如需相關資訊，請參閱 [Reinitialize a Subscription](reinitialize-a-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="a7803-123">For more information, see [Reinitialize a Subscription](reinitialize-a-subscription.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7803-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7803-124">See Also</span></span>  
 <span data-ttu-id="a7803-125">[初始化訂閱](initialize-a-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="a7803-125">[Initialize a Subscription](initialize-a-subscription.md) </span></span>  
 [<span data-ttu-id="a7803-126">訂閱逾期與停用</span><span class="sxs-lookup"><span data-stu-id="a7803-126">Subscription Expiration and Deactivation</span></span>](subscription-expiration-and-deactivation.md)  
  
  
