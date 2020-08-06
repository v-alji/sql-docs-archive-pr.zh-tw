---
title: 設定訂閱的逾期期限 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], expiration
- expiration [SQL Server replication]
- retention periods [SQL Server replication]
- deactivating subscriptions
ms.assetid: 542f0613-5817-42d0-b841-fb2c94010665
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bc0ecb449af64b88cf3ded032c78c2e399dd4234
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596650"
---
# <a name="set-the-expiration-period-for-subscriptions"></a><span data-ttu-id="2496e-102">設定訂閱的逾期期限</span><span class="sxs-lookup"><span data-stu-id="2496e-102">Set the Expiration Period for Subscriptions</span></span>
  <span data-ttu-id="2496e-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中設定訂閱的逾期期限。</span><span class="sxs-lookup"><span data-stu-id="2496e-103">This topic describes how to set the expiration period for subscriptions in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="2496e-104">訂閱的逾期期限可決定訂閱到期及移除之前的期間。</span><span class="sxs-lookup"><span data-stu-id="2496e-104">The expiration period for subscriptions determines the period of time before a subscription expires and is removed.</span></span> <span data-ttu-id="2496e-105">如需詳細資訊，請參閱 [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="2496e-105">For more information, see [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md).</span></span>  
  
 <span data-ttu-id="2496e-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="2496e-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2496e-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="2496e-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2496e-108">建議</span><span class="sxs-lookup"><span data-stu-id="2496e-108">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="2496e-109">**若要設定訂閱的逾期期限，請使用：**</span><span class="sxs-lookup"><span data-stu-id="2496e-109">**To set the expiration period for subscriptions, using:**</span></span>  
  
     [<span data-ttu-id="2496e-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2496e-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2496e-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2496e-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2496e-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="2496e-112">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="2496e-113">建議</span><span class="sxs-lookup"><span data-stu-id="2496e-113">Recommendations</span></span>  
  
-   <span data-ttu-id="2496e-114">訂閱過期期間也稱為 *「發行集保留期限」* 。</span><span class="sxs-lookup"><span data-stu-id="2496e-114">The subscription expiration period is also referred to as the *publication retention period*.</span></span> <span data-ttu-id="2496e-115">清除合併式複寫的中繼資料取決於此設定：</span><span class="sxs-lookup"><span data-stu-id="2496e-115">Cleanup of merge replication metadata is dependent on this setting:</span></span>  
  
    -   <span data-ttu-id="2496e-116">複寫無法在發行集和訂閱資料庫中清除中繼資料，直到到達保留期限為止。</span><span class="sxs-lookup"><span data-stu-id="2496e-116">Replication cannot clean up metadata in the publication and subscription databases until the retention period is reached.</span></span> <span data-ttu-id="2496e-117">小心指定保留期限的高數值，因為此值可能對複寫效能產生負面影響。</span><span class="sxs-lookup"><span data-stu-id="2496e-117">Use caution in specifying a high value for the retention period, because it can negatively impact replication performance.</span></span> <span data-ttu-id="2496e-118">若您能夠確實預測所有訂閱者都會在該時間週期內定期同步處理，建議您使用較低設定。</span><span class="sxs-lookup"><span data-stu-id="2496e-118">It is recommended that you use a lower setting if you can reliably predict that all Subscribers will synchronize regularly within that time period.</span></span>  
  
         <span data-ttu-id="2496e-119">合併式發行集的保留期限具有 24 小時寬限期，可配合不同時區的「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="2496e-119">The retention period for merge publications has a 24-hour grace period to accommodate Subscribers in different time zones.</span></span> <span data-ttu-id="2496e-120">例如，如果您設定的保留期限是一天，實際的保留期限便是 48 小時。</span><span class="sxs-lookup"><span data-stu-id="2496e-120">If, for example, you set a retention period of one day, the actual retention period is 48 hours.</span></span>  
  
    -   <span data-ttu-id="2496e-121">您可以將訂閱指定為永不過期，不過強烈建議您不要使用此值，因為如此便無法清除中繼資料了。</span><span class="sxs-lookup"><span data-stu-id="2496e-121">It is possible to specify that subscriptions never expire, but it is strongly recommended that you do not use this value, because metadata cannot be cleaned up.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2496e-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2496e-122">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="2496e-123">您可在 [發行集屬性 - \<Publication>] 對話方塊的 [一般] 頁面上，設定訂閱的逾期期限。</span><span class="sxs-lookup"><span data-stu-id="2496e-123">Set the expiration period for subscriptions on the **General** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="2496e-124">如需有關存取這個對話方塊的詳細資訊，請參閱＜ [View and Modify Publication Properties](view-and-modify-publication-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="2496e-124">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-set-the-expiration-period-for-subscriptions"></a><span data-ttu-id="2496e-125">若要設定訂閱的過期期間</span><span class="sxs-lookup"><span data-stu-id="2496e-125">To set the expiration period for subscriptions</span></span>  
  
1.  <span data-ttu-id="2496e-126">在 [發行集屬性 - \<Publication>] 對話方塊其 [一般] 頁面的 [訂閱過期] 區段中，指定訂閱是否應過期。</span><span class="sxs-lookup"><span data-stu-id="2496e-126">In the **Subscription expiration** section on the **General** page of the **Publication Properties - \<Publication>** dialog box, specify whether subscriptions should expire.</span></span>  
  
2.  <span data-ttu-id="2496e-127">如果應過期，則指定過期期間。</span><span class="sxs-lookup"><span data-stu-id="2496e-127">If they should expire, specify an expiration time period.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2496e-128">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2496e-128">Using Transact-SQL</span></span>  
 <span data-ttu-id="2496e-129">您可以使用複寫預存程序，在建立發行集時設定這個值，或是在稍後修改這個值。</span><span class="sxs-lookup"><span data-stu-id="2496e-129">You can use replication stored procedures to either set this value when a publication is created or modify this value at a later time.</span></span>  
  
#### <a name="to-set-the-expiration-period-for-a-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="2496e-130">設定快照式或交易式發行集之訂閱的逾期期限</span><span class="sxs-lookup"><span data-stu-id="2496e-130">To set the expiration period for a subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="2496e-131">在發行者上，執行 [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2496e-131">At the Publisher, execute [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql).</span></span> <span data-ttu-id="2496e-132">為 **\@retention** 指定所要的訂閱逾期期限 (以小時為單位)。</span><span class="sxs-lookup"><span data-stu-id="2496e-132">Specify the desired subscription expiration period, in hours, for **\@retention**.</span></span> <span data-ttu-id="2496e-133">預設的逾期期限為 336 小時。</span><span class="sxs-lookup"><span data-stu-id="2496e-133">The default expiration period is 336 hours.</span></span> <span data-ttu-id="2496e-134">如需詳細資訊，請參閱[建立發行集](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="2496e-134">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-set-the-expiration-period-for-a-subscription-to-a-merge-publication"></a><span data-ttu-id="2496e-135">設定合併式發行集之訂閱的逾期期限</span><span class="sxs-lookup"><span data-stu-id="2496e-135">To set the expiration period for a subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="2496e-136">在發行者端，執行 [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2496e-136">At the Publisher, execute [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span> <span data-ttu-id="2496e-137">為 **\@retention** 指定所要的訂閱逾期期限值。</span><span class="sxs-lookup"><span data-stu-id="2496e-137">Specify the desired value for the subscription expiration period for **\@retention**.</span></span> <span data-ttu-id="2496e-138">為 **\@retention_period_unit** 指定所表示的逾期期限單位，它可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="2496e-138">Specify the units in which the expiration period is expressed for **\@retention_period_unit**, which can be one of the following:</span></span>  
  
    -   <span data-ttu-id="2496e-139">**1** = 週</span><span class="sxs-lookup"><span data-stu-id="2496e-139">**1** = week</span></span>  
  
    -   <span data-ttu-id="2496e-140">**2** = 月</span><span class="sxs-lookup"><span data-stu-id="2496e-140">**2** = month</span></span>  
  
    -   <span data-ttu-id="2496e-141">**3** = 年</span><span class="sxs-lookup"><span data-stu-id="2496e-141">**3** = year</span></span>  
  
     <span data-ttu-id="2496e-142">預設的逾期期限為 14 天。</span><span class="sxs-lookup"><span data-stu-id="2496e-142">The default expiration period is 14 days.</span></span> <span data-ttu-id="2496e-143">如需詳細資訊，請參閱[建立發行集](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="2496e-143">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-change-the-expiration-period-for-a-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="2496e-144">變更快照式或交易式發行集之訂閱的逾期期限</span><span class="sxs-lookup"><span data-stu-id="2496e-144">To change the expiration period for a subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="2496e-145">在發行者上，執行 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2496e-145">At the Publisher, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql).</span></span> <span data-ttu-id="2496e-146">為 **\@property** 指定 **retention**，並為 **\@value** 指定新的訂閱逾期期限 (以小時為單位)。</span><span class="sxs-lookup"><span data-stu-id="2496e-146">Specify **retention** for **\@property** and the new subscription expiration period, in hours, for **\@value**.</span></span>  
  
#### <a name="to-change-the-expiration-period-for-a-subscription-to-a-merge-publication"></a><span data-ttu-id="2496e-147">變更合併式發行集之訂閱的逾期期限</span><span class="sxs-lookup"><span data-stu-id="2496e-147">To change the expiration period for a subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="2496e-148">在發行者上，執行 [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)，指定 **\@publication** 和 **\@publisher**。</span><span class="sxs-lookup"><span data-stu-id="2496e-148">At the Publisher, execute [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), specifying **\@publication** and **\@publisher**.</span></span> <span data-ttu-id="2496e-149">請注意結果集中 **retention_period_unit** 的值，它可以是下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="2496e-149">Note the value of **retention_period_unit** in the result set, which can be one of the following:</span></span>  
  
    -   <span data-ttu-id="2496e-150">**0** = 日</span><span class="sxs-lookup"><span data-stu-id="2496e-150">**0** = day</span></span>  
  
    -   <span data-ttu-id="2496e-151">**1** = 週</span><span class="sxs-lookup"><span data-stu-id="2496e-151">**1** = week</span></span>  
  
    -   <span data-ttu-id="2496e-152">**2** = 月</span><span class="sxs-lookup"><span data-stu-id="2496e-152">**2** = month</span></span>  
  
    -   <span data-ttu-id="2496e-153">**3** = 年</span><span class="sxs-lookup"><span data-stu-id="2496e-153">**3** = year</span></span>  
  
2.  <span data-ttu-id="2496e-154">在發行者上，執行 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2496e-154">At the Publisher, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="2496e-155">為 **\@property** 指定 **retention**，並為 **\@value** 指定新的訂閱逾期期限 (以步驟 1 中保留期限單位為根據的文字)。</span><span class="sxs-lookup"><span data-stu-id="2496e-155">Specify **retention** for **\@property** and the new subscription expiration period, as text based on the retention period unit from step 1, for **\@value**.</span></span>  
  
3.  <span data-ttu-id="2496e-156">(選擇性) 在發行者上，執行 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2496e-156">(Optional) At the Publisher, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="2496e-157">為 **\@property** 指定 **retention_period_unit**，並為 **\@value** 指定新的訂閱逾期期限單位。</span><span class="sxs-lookup"><span data-stu-id="2496e-157">Specify **retention_period_unit** for **\@property** and a new unit for the subscription expiration period for **\@value**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2496e-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2496e-158">See Also</span></span>  
 <span data-ttu-id="2496e-159">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="2496e-159">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="2496e-160">訂閱逾期與停用</span><span class="sxs-lookup"><span data-stu-id="2496e-160">Subscription Expiration and Deactivation</span></span>](../subscription-expiration-and-deactivation.md)  
  
  
