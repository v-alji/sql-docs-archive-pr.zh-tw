---
title: 選擇解析程式 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- default conflict resolver
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: b7dec3fa-d9d9-409d-b946-f9b9a3202829
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0db289e923cab72bf175b172f039ea228c991110
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592629"
---
# <a name="choose-a-resolver"></a><span data-ttu-id="401c2-102">選擇解析程式</span><span class="sxs-lookup"><span data-stu-id="401c2-102">Choose a Resolver</span></span>
  <span data-ttu-id="401c2-103">選擇解決器時，請考慮應用程式中衝突解決的重要性，並考慮是否可使用預設的優先權式衝突解決器還是需要使用發行項解決器。</span><span class="sxs-lookup"><span data-stu-id="401c2-103">When choosing a resolver, consider the importance of conflict resolution in your application and whether you can use the default priority-based conflict resolver or need to use an article resolver.</span></span>  
  
 <span data-ttu-id="401c2-104">如果您的資料分割 (Partition) 方式不會讓多位使用者寫入同一資料分割區，而且您的複寫拓撲相對上比較簡單 (一個「發行者」以及少數幾個「訂閱者」)，那麼衝突發生的機會微乎其微。</span><span class="sxs-lookup"><span data-stu-id="401c2-104">If your data is partitioned without multiple users writing to the same partitions, and your replication topology is relatively basic (one Publisher and a few Subscribers), conflicts should be rare or nonexistent.</span></span> <span data-ttu-id="401c2-105">在這些環境中，您可能不需要複雜的衝突解決策略。</span><span class="sxs-lookup"><span data-stu-id="401c2-105">In these environments, you probably do not need a complex conflict resolution strategy.</span></span> <span data-ttu-id="401c2-106">建議您使用衝突解決方案的預設設定，即利用客訂閱以及先變更者為贏的策略。</span><span class="sxs-lookup"><span data-stu-id="401c2-106">A strategy using the default settings for conflict resolution, using client subscriptions and a first change in wins policy, is recommended.</span></span> <span data-ttu-id="401c2-107">如果拓撲較為複雜 (例如使用重新發行「訂閱者」)，則具有特定優先權的主訂閱可能更合適。</span><span class="sxs-lookup"><span data-stu-id="401c2-107">If the topology is more complex (using republishing Subscribers, for example), server subscriptions with specific priorities might be more appropriate.</span></span>  
  
 <span data-ttu-id="401c2-108">如果業務需求所需的方案比預設解決器能提供的要更為精確，則建議使用發行項解決器。</span><span class="sxs-lookup"><span data-stu-id="401c2-108">An article resolver is recommended if your business needs require a more finely tuned solution than is available with the default resolver.</span></span> <span data-ttu-id="401c2-109">如果選擇使用發行項解決器，建議使用商務邏輯處理常式。</span><span class="sxs-lookup"><span data-stu-id="401c2-109">If you choose to use an article resolver, it is recommended that you use a business logic handler.</span></span> <span data-ttu-id="401c2-110">如需詳細資訊，請參閱[在合併同步處理期間執行商務邏輯](execute-business-logic-during-merge-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="401c2-110">For more information, see [Execute Business Logic During Merge Synchronization](execute-business-logic-during-merge-synchronization.md).</span></span>  
  
 <span data-ttu-id="401c2-111">最後，選擇是使用預設解決器還是發行項解決器應基於應用程式的資料和商務邏輯需求。</span><span class="sxs-lookup"><span data-stu-id="401c2-111">Ultimately, choosing whether to use the default resolver or an article resolver should be based on the data and the business logic needs of the application.</span></span> <span data-ttu-id="401c2-112">試想員工在不同的「訂閱者」端將客戶排名資料輸入一組未分割的資料表中；員工的工作跨多個類別 (分公司經理、直線經理、銷售人員等)，且由工作類別決定誰的資料優先權較高。</span><span class="sxs-lookup"><span data-stu-id="401c2-112">For example, consider employees who enter customer ranking data into a set of non-partitioned tables at different Subscribers; the employees span various job categories (branch managers, line managers, sales staff), and job category determines whose data should be given priority.</span></span> <span data-ttu-id="401c2-113">在此情況下，您可以建立一個發行項解決器，使用發行項的工作類別資料來決定發生衝突時的成功者。</span><span class="sxs-lookup"><span data-stu-id="401c2-113">In this case, an article resolver can be built that uses job category data from the article to determine the winner if a conflict occurs.</span></span>  
  
 <span data-ttu-id="401c2-114">如果偶而會有衝突發生，以下是您在實作衝突解決策略時應考慮的幾個重要決定。</span><span class="sxs-lookup"><span data-stu-id="401c2-114">If conflicts are likely to occur with some frequency, here are the most important decisions you should consider when implementing a conflict resolution strategy.</span></span>  
  
|<span data-ttu-id="401c2-115">衝突解決問題</span><span class="sxs-lookup"><span data-stu-id="401c2-115">Conflict resolution issue</span></span>|<span data-ttu-id="401c2-116">建議</span><span class="sxs-lookup"><span data-stu-id="401c2-116">Recommendation</span></span>|  
|-------------------------------|--------------------|  
|<span data-ttu-id="401c2-117">不同類別的使用者需要不同的優先權值。</span><span class="sxs-lookup"><span data-stu-id="401c2-117">Different categories of users require different priority values.</span></span>|<span data-ttu-id="401c2-118">使用預設解決器，並建立具有不同優先權值的主訂閱。</span><span class="sxs-lookup"><span data-stu-id="401c2-118">Use the default resolver and create server subscriptions with different priority values.</span></span><br /><br /> <span data-ttu-id="401c2-119">-或-</span><span class="sxs-lookup"><span data-stu-id="401c2-119">-Or-</span></span><br /><br /> <span data-ttu-id="401c2-120">使用可在發行項中辨識授權值資料行之發行項解決器來協助解決衝突。</span><span class="sxs-lookup"><span data-stu-id="401c2-120">Use an article resolver that recognizes an authority value column in the article to help resolve a conflict.</span></span>|  
|<span data-ttu-id="401c2-121">希望使用先改變者為贏的衝突解決方案。</span><span class="sxs-lookup"><span data-stu-id="401c2-121">First change in wins conflict solution wanted.</span></span>|<span data-ttu-id="401c2-122">使用預設解決器並建立客訂閱。</span><span class="sxs-lookup"><span data-stu-id="401c2-122">Use the default resolver and create client subscriptions.</span></span>|  
|<span data-ttu-id="401c2-123">可接受多位使用者變更同一個資料列，只要同一資料行沒有衝突變更即可。</span><span class="sxs-lookup"><span data-stu-id="401c2-123">Multiple users changing the same data row is acceptable, as long as no conflicting changes are made to the same column.</span></span>|<span data-ttu-id="401c2-124">使用預設解決器或發行項解決器，並啟用資料行層級追蹤。</span><span class="sxs-lookup"><span data-stu-id="401c2-124">Use either the default resolver or an article resolver with column-level tracking enabled.</span></span>|  
|<span data-ttu-id="401c2-125">以旗標將資料列上任何值的多次變更標示為衝突。</span><span class="sxs-lookup"><span data-stu-id="401c2-125">Flag multiple changes to any value in a row as a conflict.</span></span>|<span data-ttu-id="401c2-126">使用預設解決器或發行項解決器，並啟用資料列層級追蹤。</span><span class="sxs-lookup"><span data-stu-id="401c2-126">Use either the default resolver or an article resolver with row-level tracking.</span></span>|  
|<span data-ttu-id="401c2-127">以旗標將邏輯記錄中任何值的多次變更標示為衝突。</span><span class="sxs-lookup"><span data-stu-id="401c2-127">Flag multiple changes to any value in a logical record as a conflict.</span></span>|<span data-ttu-id="401c2-128">使用啟用了邏輯記錄層級追蹤的預設解決器 (邏輯記錄功能不支援自訂解決器或商務邏輯處理常式)。</span><span class="sxs-lookup"><span data-stu-id="401c2-128">Use the default resolver with logical record-level tracking (the logical records feature does not support custom resolvers or business logic handlers).</span></span>|  
|<span data-ttu-id="401c2-129">衝突結果資料需與原始衝突資料不同。</span><span class="sxs-lookup"><span data-stu-id="401c2-129">Conflict outcome data needs to be different from original conflict data.</span></span>|<span data-ttu-id="401c2-130">使用可計算新值的發行項解決器。</span><span class="sxs-lookup"><span data-stu-id="401c2-130">Use an article resolver that calculates new values.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="401c2-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="401c2-131">See Also</span></span>  
 <span data-ttu-id="401c2-132">[Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md) </span><span class="sxs-lookup"><span data-stu-id="401c2-132">[Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md) </span></span>  
 <span data-ttu-id="401c2-133">[進階合併式複寫衝突偵測與解決](advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="401c2-133">[Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="401c2-134">重新發行資料</span><span class="sxs-lookup"><span data-stu-id="401c2-134">Republish Data</span></span>](../republish-data.md)  
  
  
