---
title: 訂閱逾期與停用 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Distributors [SQL Server replication], distribution retention period
- subscriptions [SQL Server replication], expiration
- publications [SQL Server replication], publication retention periods
- expiration [SQL Server replication]
- retention periods [SQL Server replication]
- publication retention periods
- distribution retention period
- subscriptions [SQL Server replication], deactivation
- deactivating subscriptions
ms.assetid: 4d03f5ab-e721-4f56-aebc-60f6a56c1e07
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6d81e8b5c02fcfe5399be9e63c8160036a999547
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708153"
---
# <a name="subscription-expiration-and-deactivation"></a><span data-ttu-id="c414c-102">訂閱逾期與停用</span><span class="sxs-lookup"><span data-stu-id="c414c-102">Subscription Expiration and Deactivation</span></span>
  <span data-ttu-id="c414c-103">如果訂閱在指定 *「保留期限」* 內未執行同步處理，則可以停用訂閱或使訂閱過期。</span><span class="sxs-lookup"><span data-stu-id="c414c-103">Subscriptions can be deactivated or can expire if they are not synchronized within a specified *retention period*.</span></span> <span data-ttu-id="c414c-104">發生的動作依複寫類型及超過的保留期限而定。</span><span class="sxs-lookup"><span data-stu-id="c414c-104">The action that occurs depends on the type of replication and the retention period that is exceeded.</span></span>  
  
 <span data-ttu-id="c414c-105">若要設定保留期限，請參閱[設定訂閱的逾期期限](publish/set-the-expiration-period-for-subscriptions.md)、[設定交易式發行集的散發保留期限 &#40;SQL Server Management Studio&#41;](set-distribution-retention-period-for-transactional-publications.md) 和[設定發行與散發](configure-publishing-and-distribution.md)。</span><span class="sxs-lookup"><span data-stu-id="c414c-105">To set retention periods, see [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md), [Set the Distribution Retention Period for Transactional Publications &#40;SQL Server Management Studio&#41;](set-distribution-retention-period-for-transactional-publications.md), and [Configure Publishing and Distribution](configure-publishing-and-distribution.md).</span></span>  
  
## <a name="transactional-replication"></a><span data-ttu-id="c414c-106">異動複寫</span><span class="sxs-lookup"><span data-stu-id="c414c-106">Transactional Replication</span></span>  
 <span data-ttu-id="c414c-107">異動複寫會使用最大散發保留期限 (**@max_distretention** sp_adddistributiondb 的參數[&#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql)) 和發行集保留期限 (sp_addpublication **@retention** [transact-sql &#40;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)&#41;的參數：</span><span class="sxs-lookup"><span data-stu-id="c414c-107">Transactional replication uses the maximum distribution retention period (the **@max_distretention** parameter of [sp_adddistributiondb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql)) and the publication retention period (the **@retention** parameter of [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)):</span></span>  
  
-   <span data-ttu-id="c414c-108">如果在最高散發保留期限內 (預設值為 72 小時) 未同步處理訂閱，並且散發資料庫中有變更尚未傳遞至「訂閱者」，則「散發者」上執行的 **Distribution clean up** 工作會將訂閱標記為停用。</span><span class="sxs-lookup"><span data-stu-id="c414c-108">If a subscription is not synchronized within the maximum distribution retention period (default of 72 hours) and there are changes in the distribution database that have not been delivered to the Subscriber, the subscription will be marked deactivated by the **Distribution clean up** job that runs on the Distributor.</span></span> <span data-ttu-id="c414c-109">訂閱必須重新初始化。</span><span class="sxs-lookup"><span data-stu-id="c414c-109">The subscription must be reinitialized.</span></span>  
  
-   <span data-ttu-id="c414c-110">如果在發行集保留期限內 (預設值為 336 小時) 未同步處理訂閱，則訂閱將過期並由「發行者」上執行的 **Expired subscription clean up** 工作卸除。</span><span class="sxs-lookup"><span data-stu-id="c414c-110">If a subscription is not synchronized within the publication retention period (default of 336 hours), the subscription will expire and be dropped by the **Expired subscription clean up** job that runs on the Publisher.</span></span> <span data-ttu-id="c414c-111">訂閱必須重新建立並同步處理。</span><span class="sxs-lookup"><span data-stu-id="c414c-111">The subscription must be recreated and synchronized.</span></span>  
  
     <span data-ttu-id="c414c-112">若發送訂閱已過期，會完全移除；但提取訂閱不會移除。</span><span class="sxs-lookup"><span data-stu-id="c414c-112">If a push subscription expires, it is completely removed, but pull subscriptions are not.</span></span> <span data-ttu-id="c414c-113">您必須在訂閱者端清除提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="c414c-113">You must clean up pull subscriptions at the Subscriber.</span></span> <span data-ttu-id="c414c-114">如需詳細資訊，請參閱 [Delete a Pull Subscription](delete-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="c414c-114">For more information, see [Delete a Pull Subscription](delete-a-pull-subscription.md).</span></span>  
  
## <a name="merge-replication"></a><span data-ttu-id="c414c-115">合併式複寫</span><span class="sxs-lookup"><span data-stu-id="c414c-115">Merge Replication</span></span>  
 <span data-ttu-id="c414c-116">合併式複寫會使用發行集保留期限 **@retention** ， (**@retention_period_unit** [sp_addmergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)) 的和參數。</span><span class="sxs-lookup"><span data-stu-id="c414c-116">Merge replication uses the publication retention period (the **@retention** and **@retention_period_unit** parameters of [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)).</span></span> <span data-ttu-id="c414c-117">訂閱過期後，就必須重新初始化，因為訂閱的中繼資料已被移除。</span><span class="sxs-lookup"><span data-stu-id="c414c-117">When a subscription expires, it must be reinitialized, because metadata for the subscription is removed.</span></span> <span data-ttu-id="c414c-118">未重新初始化的訂閱，由「發行者」上執行的 **Expired subscription clean up** 作業卸除。</span><span class="sxs-lookup"><span data-stu-id="c414c-118">Subscriptions that are not reinitialized are dropped by the **Expired subscription clean up** job that runs on the Publisher.</span></span> <span data-ttu-id="c414c-119">依預設此作業每日執行，並移除所有尚未同步處理為兩倍發行保留期限的發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="c414c-119">By default, this job runs daily; it removes all push subscriptions that have not synchronized for double the length of the publication retention period.</span></span> <span data-ttu-id="c414c-120">例如：</span><span class="sxs-lookup"><span data-stu-id="c414c-120">For example:</span></span>  
  
-   <span data-ttu-id="c414c-121">若發行的保留期限為 14 天，訂閱若未於 14 天內同步處理就會過期。</span><span class="sxs-lookup"><span data-stu-id="c414c-121">If a publication has a retention period of 14 days, a subscription can expire if it has not synchronized within 14 days.</span></span>  
  
     <span data-ttu-id="c414c-122">如果發行者正在執行 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更新版本，且訂閱的代理程式來自 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更新版本，則訂閱只有在該訂閱分割資料變更時才會過期。</span><span class="sxs-lookup"><span data-stu-id="c414c-122">If the Publisher is running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or a later version and the agent for the subscription is from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or a later version, a subscription only expires if there have been changes to the data in that subscription's partition.</span></span> <span data-ttu-id="c414c-123">例如，假設訂閱者收到德國客戶的客戶資料。</span><span class="sxs-lookup"><span data-stu-id="c414c-123">For example, suppose a Subscriber receives customer data only for customers in Germany.</span></span> <span data-ttu-id="c414c-124">若保留期限設定為 14 天，只有當德國客戶資料在過去 14 天變更，訂閱才會在第14 天過期。</span><span class="sxs-lookup"><span data-stu-id="c414c-124">If the retention period is set to 14 days, the subscription expires on day 14 only if there have been changes to the German customer data in the last 14 days.</span></span>  
  
-   <span data-ttu-id="c414c-125">從上一次同步處理後的第 14 到 27 天，訂閱皆可重新初始化。</span><span class="sxs-lookup"><span data-stu-id="c414c-125">From 14 days to 27 days after the last synchronization, the subscription can be reinitialized.</span></span>  
  
-   <span data-ttu-id="c414c-126">在上一次同步處理後的 28 天，訂閱由 **Expired subscription clean up** 作業卸除。</span><span class="sxs-lookup"><span data-stu-id="c414c-126">At 28 days after the last synchronization, the subscription is dropped by the **Expired subscription clean up** job.</span></span> <span data-ttu-id="c414c-127">若發送訂閱已過期，會完全移除；但提取訂閱不會移除。</span><span class="sxs-lookup"><span data-stu-id="c414c-127">If a push subscription expires, it is completely removed, but pull subscriptions are not.</span></span> <span data-ttu-id="c414c-128">您必須在訂閱者端清除提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="c414c-128">You must clean up pull subscriptions at the Subscriber.</span></span> <span data-ttu-id="c414c-129">如需詳細資訊，請參閱 [Delete a Pull Subscription](delete-a-pull-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="c414c-129">For more information, see [Delete a Pull Subscription](delete-a-pull-subscription.md).</span></span>  
  
### <a name="considerations-for-setting-the-publication-retention-period-for-merge-publications"></a><span data-ttu-id="c414c-130">設定合併式發行集保留期限的考量</span><span class="sxs-lookup"><span data-stu-id="c414c-130">Considerations for Setting the Publication Retention Period for Merge Publications</span></span>  
 <span data-ttu-id="c414c-131">設定合併式發行集的保留期限時，請記住以下考量：</span><span class="sxs-lookup"><span data-stu-id="c414c-131">Keep the following considerations in mind when setting the retention period for merge publications:</span></span>  
  
-   <span data-ttu-id="c414c-132">合併式發行集的保留期限具有 24 小時寬限期，可配合不同時區的「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="c414c-132">The retention period for merge publications has a 24-hour grace period to accommodate Subscribers in different time zones.</span></span> <span data-ttu-id="c414c-133">例如，如果您設定的保留期限是一天，實際的保留期限便是 48 小時。</span><span class="sxs-lookup"><span data-stu-id="c414c-133">If, for example, you set a retention period of one day, the actual retention period is 48 hours.</span></span>  
  
-   <span data-ttu-id="c414c-134">合併式複寫中繼資料的清除相依於發行集保留期限：</span><span class="sxs-lookup"><span data-stu-id="c414c-134">Cleanup of merge replication metadata is dependent on the publication retention period:</span></span>  
  
    -   <span data-ttu-id="c414c-135">複寫無法在發行集和訂閱資料庫中清除中繼資料，直到到達保留期限為止。</span><span class="sxs-lookup"><span data-stu-id="c414c-135">Replication cannot clean up metadata in the publication and subscription databases until the retention period is reached.</span></span> <span data-ttu-id="c414c-136">小心指定保留期限的高數值，因為此值可能對複寫效能產生負面影響。</span><span class="sxs-lookup"><span data-stu-id="c414c-136">Use caution in specifying a high value for the retention period, because it can negatively impact replication performance.</span></span> <span data-ttu-id="c414c-137">若您能夠確實預測所有訂閱者都會在該時間週期內定期同步處理，建議您使用較低設定。</span><span class="sxs-lookup"><span data-stu-id="c414c-137">It is recommended that you use a lower setting if you can reliably predict that all Subscribers will synchronize regularly within that time period.</span></span>  
  
    -   <span data-ttu-id="c414c-138">您可以指定訂閱永遠不會過期 () 的值為 0 **@retention** ，但強烈建議您不要使用此值，因為中繼資料無法清除。</span><span class="sxs-lookup"><span data-stu-id="c414c-138">It is possible to specify that subscriptions never expire (a value of 0 for **@retention**), but it is strongly recommended that you do not use this value, because metadata cannot be cleaned up.</span></span>  
  
-   <span data-ttu-id="c414c-139">任何重新發行者的保留期限必須設定為等於或少於原始「發行者」的設定值。</span><span class="sxs-lookup"><span data-stu-id="c414c-139">The retention period for any republisher must be set to a value equal to or less than the retention period set at the original Publisher.</span></span> <span data-ttu-id="c414c-140">對所有的「發行者」及其替代性同步處理夥伴，也應該使用相同的發行保留值。</span><span class="sxs-lookup"><span data-stu-id="c414c-140">You should also use the same publication retention values for all Publishers and their alternate synchronization partners.</span></span> <span data-ttu-id="c414c-141">使用不同值可能會導致非交集的情況。</span><span class="sxs-lookup"><span data-stu-id="c414c-141">Using different values may lead to non-convergence.</span></span> <span data-ttu-id="c414c-142">若您需要變更發行集保留值，請重新初始化訂閱者，以避免資料無法聚合。</span><span class="sxs-lookup"><span data-stu-id="c414c-142">If you need to change the publication retention value, reinitialize the Subscriber to avoid the non-convergence of data.</span></span>  
  
-   <span data-ttu-id="c414c-143">在清除之後，如果發行集保留期限加長，而訂閱嘗試與發行者 (已刪除中繼資料) 合併，則由於保留值增加而使訂閱不會過期。</span><span class="sxs-lookup"><span data-stu-id="c414c-143">If, after a clean up, the publication retention period is increased and a subscription tries to merge with the Publisher (which has already deleted the metadata), the subscription will not expire because of the increased retention value.</span></span> <span data-ttu-id="c414c-144">不過，發行者則會因沒有足夠的中繼資料可以下載訂閱者的變更，而導致無法聚合。</span><span class="sxs-lookup"><span data-stu-id="c414c-144">However, the Publisher does not have enough metadata to download changes to the Subscriber, which leads to non-convergence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c414c-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c414c-145">See Also</span></span>  
 <span data-ttu-id="c414c-146">[重新初始化訂閱](reinitialize-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="c414c-146">[Reinitialize Subscriptions](reinitialize-subscriptions.md) </span></span>  
 <span data-ttu-id="c414c-147">[複寫代理程式管理](agents/replication-agent-administration.md) </span><span class="sxs-lookup"><span data-stu-id="c414c-147">[Replication Agent Administration](agents/replication-agent-administration.md) </span></span>  
 [<span data-ttu-id="c414c-148">訂閱發行集</span><span class="sxs-lookup"><span data-stu-id="c414c-148">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
