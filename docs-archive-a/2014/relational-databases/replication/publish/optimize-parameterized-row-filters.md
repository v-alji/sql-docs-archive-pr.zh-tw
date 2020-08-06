---
title: 最佳化參數化資料列篩選 | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- precomputed partitions [SQL Server replication]
- filters [SQL Server replication], parameterized
- merge replication precomputed partitions [SQL Server replication], SQL Server Management Studio
- parameterized filters [SQL Server replication], optimizing
ms.assetid: 49349605-ebd0-4757-95be-c0447f30ba13
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f1c6448d8e2dba7a68fab441d4d08fd4a4a1db4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708178"
---
# <a name="optimize-parameterized-row-filters"></a><span data-ttu-id="1c922-102">最佳化參數化資料列篩選</span><span class="sxs-lookup"><span data-stu-id="1c922-102">Optimize Parameterized Row Filters</span></span>
  <span data-ttu-id="1c922-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中最佳化參數化資料列篩選。</span><span class="sxs-lookup"><span data-stu-id="1c922-103">This topic describes how to optimize parameterized row filters in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1c922-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="1c922-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1c922-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="1c922-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1c922-106">建議</span><span class="sxs-lookup"><span data-stu-id="1c922-106">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="1c922-107">**若要最佳化參數化資料列篩選，請使用：**</span><span class="sxs-lookup"><span data-stu-id="1c922-107">**To optimize parameterized row filters, using:**</span></span>  
  
     [<span data-ttu-id="1c922-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1c922-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1c922-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1c922-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1c922-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="1c922-110">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="1c922-111">建議</span><span class="sxs-lookup"><span data-stu-id="1c922-111">Recommendations</span></span>  
  
-   <span data-ttu-id="1c922-112">在使用參數化篩選器時，您可以在建立發行集時，藉由指定 [使用資料分割群組]  選項或 [保留資料分割變更]  選項來控制合併式複寫要如何處理篩選。</span><span class="sxs-lookup"><span data-stu-id="1c922-112">When you use parameterized filters, you can control how the filters are processed by merge replication by specifying either the **use partition groups** option or the **keep partition changes** option when you create a publication.</span></span> <span data-ttu-id="1c922-113">這兩個選項都可以透過在發行集資料庫中儲存其他中繼資料，以提升具有篩選發行項之發行集的同步處理效能。</span><span class="sxs-lookup"><span data-stu-id="1c922-113">These options improve the synchronization performance for publications with filtered articles by storing additional metadata in the publication database.</span></span> <span data-ttu-id="1c922-114">您可以在建立發行項時，藉由設定 [資料分割選項]  來控制要如何在訂閱者之間共用資料。</span><span class="sxs-lookup"><span data-stu-id="1c922-114">You can control how the data is shared among Subscribers by setting **partition options** when you create an article.</span></span> <span data-ttu-id="1c922-115">如需有關這些需求的詳細資訊，請參閱＜ [參數化資料列篩選器](../merge/parameterized-filters-parameterized-row-filters.md)＞。</span><span class="sxs-lookup"><span data-stu-id="1c922-115">For more information about these requirements, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
     <span data-ttu-id="1c922-116">對於 [!INCLUDE[ssEW](../../../includes/ssew-md.md)]SQL Server Compact 訂閱者，必須將 keep_partition_changes 設為 true，才能確保正確傳播刪除。</span><span class="sxs-lookup"><span data-stu-id="1c922-116">With [!INCLUDE[ssEW](../../../includes/ssew-md.md)]SQL Server Compact subscribers, keep_partition_changes must be set to true to ensure that deletes are correctly propagated.</span></span> <span data-ttu-id="1c922-117">設為 false 時，訂閱者所擁有的資料列可能比預期多。</span><span class="sxs-lookup"><span data-stu-id="1c922-117">When set to false, the subscriber might have more rows than expected.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1c922-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1c922-118">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="1c922-119">下列設定可用於最佳化參數化資料列篩選器：</span><span class="sxs-lookup"><span data-stu-id="1c922-119">The following settings can be used to optimize parameterized row filters:</span></span>  
  
 <span data-ttu-id="1c922-120">**資料分割選項**</span><span class="sxs-lookup"><span data-stu-id="1c922-120">**Partition Options**</span></span>  
 <span data-ttu-id="1c922-121">您可以在 [發行項屬性 - \<Article>] 對話方塊的 [屬性] 頁面上，或是在 [新增篩選] 對話方塊中，設定此選項。</span><span class="sxs-lookup"><span data-stu-id="1c922-121">Set this option on the **Properties** page of the **Article Properties - \<Article>** dialog box, or in the **Add Filter** dialog box.</span></span> <span data-ttu-id="1c922-122">[新增發行集] 精靈和 [發行集屬性 - \<Publication>] 對話方塊中皆提供這兩個對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1c922-122">Both dialog boxes are available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="1c922-123">[發行項屬性 - \<Article>] 對話方塊可讓您針對此選項，指定 [新增篩選] 對話方塊中未提供的其他值。</span><span class="sxs-lookup"><span data-stu-id="1c922-123">The **Article Properties - \<Article>** dialog box allows you to specify additional values for this option that are not available in the **Add Filter** dialog box.</span></span>  
  
 <span data-ttu-id="1c922-124">**預先計算資料分割**</span><span class="sxs-lookup"><span data-stu-id="1c922-124">**Precompute Partitions**</span></span>  
 <span data-ttu-id="1c922-125">依預設，如果發行集中的發行項符合一組需求，則此選項要設定為 **[True]** 。</span><span class="sxs-lookup"><span data-stu-id="1c922-125">This option is set to **True** by default if the articles in your publication adhere to a set of requirements.</span></span> <span data-ttu-id="1c922-126">如需這些需求的詳細資訊，請參閱[使用預先計算的資料分割最佳化參數化篩選效能](../merge/parameterized-filters-optimize-for-precomputed-partitions.md)。</span><span class="sxs-lookup"><span data-stu-id="1c922-126">For more information about these requirements, see [Optimize Parameterized Filter Performance with Precomputed Partitions](../merge/parameterized-filters-optimize-for-precomputed-partitions.md).</span></span> <span data-ttu-id="1c922-127">您可以在 [發行集屬性 - \<Publication>] 對話方塊的 [訂閱選項] 頁面上，修改此選項。</span><span class="sxs-lookup"><span data-stu-id="1c922-127">Modify this option on the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box.</span></span>  
  
 <span data-ttu-id="1c922-128">**最佳化同步處理**</span><span class="sxs-lookup"><span data-stu-id="1c922-128">**Optimize Synchronization**</span></span>  
 <span data-ttu-id="1c922-129">只有在 **[預先計算資料分割]** 設定為 **[False]** 時，此選項才應設定為 **[True]** 。</span><span class="sxs-lookup"><span data-stu-id="1c922-129">This option should be set to **True** only if **Precompute Partitions** is set to **False**.</span></span> <span data-ttu-id="1c922-130">您可以在 [發行集屬性 - \<Publication>] 對話方塊的 [訂閱選項] 頁面上，設定此選項。</span><span class="sxs-lookup"><span data-stu-id="1c922-130">Set this option on the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box.</span></span>  
  
 <span data-ttu-id="1c922-131">如需使用 [新增發行集] 精靈並存取 [發行集屬性 - \<Publication>] 對話方塊的詳細資訊，請參閱[建立發行集](create-a-publication.md)和[檢視及修改發行集屬性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="1c922-131">For more information about using the New Publication Wizard and accessing the **Publication Properties - \<Publication>** dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-set-partition-options-in-the-add-filter-or-edit-filter-dialog-box"></a><span data-ttu-id="1c922-132">若要在加入篩選或編輯篩選對話方塊中設定資料分割選項</span><span class="sxs-lookup"><span data-stu-id="1c922-132">To set Partition options in the Add Filter or Edit Filter dialog box</span></span>  
  
1.  <span data-ttu-id="1c922-133">在 [新增發行集] 精靈的 [篩選資料表的資料列] 頁面上，或是在 [發行集屬性 - \<Publication>] 對話方塊的 [篩選資料列] 頁面上，按一下 [新增]，然後按一下 [新增篩選]。</span><span class="sxs-lookup"><span data-stu-id="1c922-133">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, click **Add**, and then click **Add Filter**.</span></span>  
  
2.  <span data-ttu-id="1c922-134">建立參數化篩選。</span><span class="sxs-lookup"><span data-stu-id="1c922-134">Create a parameterized filter.</span></span> <span data-ttu-id="1c922-135">如需詳細資訊，請參閱 [針對合併發行項定義及修改參數化資料列篩選](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)。</span><span class="sxs-lookup"><span data-stu-id="1c922-135">For more information, see [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).</span></span>  
  
3.  <span data-ttu-id="1c922-136">選取符合資料在訂閱者之間共用資料方式的選項：</span><span class="sxs-lookup"><span data-stu-id="1c922-136">Select the option that matches how data will be shared among Subscribers:</span></span>  
  
    -   <span data-ttu-id="1c922-137">**這個資料表中的一個資料列會提供給多個訂閱**</span><span class="sxs-lookup"><span data-stu-id="1c922-137">**A row from this table will go to multiple subscriptions**</span></span>  
  
    -   <span data-ttu-id="1c922-138">**這個資料表中的一個資料列只會提供給一個訂閱**</span><span class="sxs-lookup"><span data-stu-id="1c922-138">**A row from this table will go to only one subscription**</span></span>  
  
     <span data-ttu-id="1c922-139">若您選取 **[這個資料表中的一個資料列只會提供給一個訂閱]** ，合併式複寫可藉由儲存和處理較少中繼資料來將效能最佳化。</span><span class="sxs-lookup"><span data-stu-id="1c922-139">If you select **A row from this table will go to only one subscription**, merge replication can optimize performance by storing and processing less metadata.</span></span> <span data-ttu-id="1c922-140">不過您必須確定資料分割方式不會將資料列複寫至多個訂閱者。</span><span class="sxs-lookup"><span data-stu-id="1c922-140">However, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber.</span></span> <span data-ttu-id="1c922-141">如需進一步資訊，請參閱主題＜ [參數化資料列篩選器](../merge/parameterized-filters-parameterized-row-filters.md)＞中的「設定資料分割選項」。</span><span class="sxs-lookup"><span data-stu-id="1c922-141">For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="1c922-142">如果您位於 [發行集屬性 - \<Publication>] 對話方塊中，請按一下 [確定] 以儲存並關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1c922-142">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-set-partition-options-in-the-article-properties---article-dialog-box"></a><span data-ttu-id="1c922-143">設定 [發行項屬性 - \<Article>] 對話方塊中的分割區選項</span><span class="sxs-lookup"><span data-stu-id="1c922-143">To set Partition Options in the Article Properties - \<Article> dialog box</span></span>  
  
1.  <span data-ttu-id="1c922-144">在 [新增發行集] 精靈的 [發行項] 頁面上，或是在 [發行集屬性 - \<Publication>] 對話方塊中，選取一個資料表，然後按一下 [發行項屬性]。</span><span class="sxs-lookup"><span data-stu-id="1c922-144">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a table, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="1c922-145">按一下 **[設定反白顯示資料表發行項的屬性]** 或 **[設定所有資料表發行項的屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="1c922-145">Click **Set Properties of Highlighted Table Article** or **Set Properties of All Table Articles**.</span></span>  
  
3.  <span data-ttu-id="1c922-146">在 [發行項屬性 - \<Article>] 對話方塊之 [屬性] 索引標籤的 [目的地物件] 區段中，指定 [分割區選項] 的下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="1c922-146">In the **Destination Object** section of the **Properties** tab of the **Article Properties - \<Article>** dialog box, specify one of the following values for **Partition Options**:</span></span>  
  
    -   <span data-ttu-id="1c922-147">**重疊**</span><span class="sxs-lookup"><span data-stu-id="1c922-147">**Overlapping**</span></span>  
  
    -   <span data-ttu-id="1c922-148">**重疊，不允許變更資料分割外的資料**</span><span class="sxs-lookup"><span data-stu-id="1c922-148">**Overlapping, disallow out-of-partition data changes**</span></span>  
  
    -   <span data-ttu-id="1c922-149">**不重疊，單一訂閱**</span><span class="sxs-lookup"><span data-stu-id="1c922-149">**Nonoverlapping, single subscription**</span></span>  
  
    -   <span data-ttu-id="1c922-150">**不重疊，共用於訂閱之間**</span><span class="sxs-lookup"><span data-stu-id="1c922-150">**Nonoverlapping, shared between subscriptions**</span></span>  
  
     <span data-ttu-id="1c922-151">如需這些選項及其如何與 **[加入篩選]** 和 **[編輯篩選]** 對話方塊中可用之選項相關聯的詳細資訊，請參閱＜ [參數化資料列篩選器](../merge/parameterized-filters-parameterized-row-filters.md)＞的「設定資料分割選項」一節。</span><span class="sxs-lookup"><span data-stu-id="1c922-151">For more information about these options and how they relate to the options available in the **Add Filter** and **Edit Filter** dialog boxes, see the "Setting 'partition options'" section of [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="1c922-152">如果您位於 [發行集屬性 - \<Publication>] 對話方塊中，請按一下 [確定] 以儲存並關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1c922-152">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-set-precompute-partitions"></a><span data-ttu-id="1c922-153">若要設定預先計算資料分割</span><span class="sxs-lookup"><span data-stu-id="1c922-153">To set Precompute Partitions</span></span>  
  
1.  <span data-ttu-id="1c922-154">在 [發行集屬性 - \<Publication>] 對話方塊的 [訂閱選項] 頁面上，選取 [預先計算分割區] 選項的值。</span><span class="sxs-lookup"><span data-stu-id="1c922-154">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, select a value for the **Precompute Partitions** option.</span></span> <span data-ttu-id="1c922-155">在下列情況下，該屬性是唯讀的：</span><span class="sxs-lookup"><span data-stu-id="1c922-155">The property is read-only if:</span></span>  
  
    -   <span data-ttu-id="1c922-156">發行集不符合預先計算資料分割的需求。</span><span class="sxs-lookup"><span data-stu-id="1c922-156">The publication does not meet the requirements for precomputed partitions.</span></span>  
  
    -   <span data-ttu-id="1c922-157">尚未產生此發行集的快照集。</span><span class="sxs-lookup"><span data-stu-id="1c922-157">A snapshot has not yet been generated for the publication.</span></span> <span data-ttu-id="1c922-158">在此情況下，選項會顯示 **[建立快照時會自動設定]** 的值。</span><span class="sxs-lookup"><span data-stu-id="1c922-158">In this case, the option displays a value of **Set automatically when a snapshot is created**.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-set-optimize-synchronization"></a><span data-ttu-id="1c922-159">若要設定最佳化同步處理</span><span class="sxs-lookup"><span data-stu-id="1c922-159">To set Optimize Synchronization</span></span>  
  
1.  <span data-ttu-id="1c922-160">在 [**發行集屬性 \<Publication> -** ] 對話方塊的 [**訂閱選項**] 頁面上，針對 [**優化同步**處理] 選項選取 [ **True** ] 值。</span><span class="sxs-lookup"><span data-stu-id="1c922-160">On the **Subscription Options** page of the **Publication Properties - \<Publication>** dialog box, select a value of **True** for the **Optimize Synchronization** option.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1c922-161">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1c922-161">Using Transact-SQL</span></span>  
 <span data-ttu-id="1c922-162">如需\*\* \@ keep_partition_changes**和** \@ use_partition_groups\*\*篩選選項的定義，請參閱[sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1c922-162">For definitions of the filtering options for **\@keep_partition_changes** and **\@use_partition_groups**, see [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span>  
  
#### <a name="to-specify-merge-filter-optimizations-when-creating-a-new-publication"></a><span data-ttu-id="1c922-163">在建立新的發行集時指定合併篩選最佳化</span><span class="sxs-lookup"><span data-stu-id="1c922-163">To specify merge filter optimizations when creating a new publication</span></span>  
  
1.  <span data-ttu-id="1c922-164">在發行集資料庫的發行者上，執行 [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1c922-164">At the Publisher on the publication database, execute [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span> <span data-ttu-id="1c922-165">針對下列其中一個參數指定\*\* \@ 發行\*\*集和的值 `true` ：</span><span class="sxs-lookup"><span data-stu-id="1c922-165">Specify **\@publication** and a value of `true` for one the following parameters:</span></span>  
  
    -   <span data-ttu-id="1c922-166">\*\* \@ use_partition_groups\*\*：-最高效能優化，前提是發行項符合預先計算資料分割的需求。</span><span class="sxs-lookup"><span data-stu-id="1c922-166">**\@use_partition_groups**: - the highest performance optimization, provided that the articles conform to the requirements for precomputed partitions.</span></span> <span data-ttu-id="1c922-167">如需詳細資訊，請參閱[使用預先計算的資料分割最佳化參數化篩選效能](../merge/parameterized-filters-optimize-for-precomputed-partitions.md)。</span><span class="sxs-lookup"><span data-stu-id="1c922-167">For more information, see [Optimize Parameterized Filter Performance with Precomputed Partitions](../merge/parameterized-filters-optimize-for-precomputed-partitions.md).</span></span>  
  
    -   <span data-ttu-id="1c922-168">\*\* \@ keep_partition_changes\*\* -如果無法使用預先計算的資料分割，請使用此優化。</span><span class="sxs-lookup"><span data-stu-id="1c922-168">**\@keep_partition_changes** - use this optimization if precomputed partitions cannot be used.</span></span>  
  
2.  <span data-ttu-id="1c922-169">加入此發行集的快照集作業。</span><span class="sxs-lookup"><span data-stu-id="1c922-169">Add a snapshot job for the publication.</span></span> <span data-ttu-id="1c922-170">如需詳細資訊，請參閱[建立發行集](create-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="1c922-170">For more information see [Create a Publication](create-a-publication.md).</span></span>  
  
3.  <span data-ttu-id="1c922-171">在發行集資料庫的發行者上，執行 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)並指定下列參數：</span><span class="sxs-lookup"><span data-stu-id="1c922-171">At the Publisher on the publication database, execute [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql), specifying the following parameters:</span></span>  
  
    -   <span data-ttu-id="1c922-172">\*\* \@ 發行\*\*集-步驟1中的發行集名稱。</span><span class="sxs-lookup"><span data-stu-id="1c922-172">**\@publication** - the name of the publication from step 1.</span></span>  
  
    -   <span data-ttu-id="1c922-173">\*\* \@ 文章\*\*-發行項的名稱</span><span class="sxs-lookup"><span data-stu-id="1c922-173">**\@article** - a name for the article</span></span>  
  
    -   <span data-ttu-id="1c922-174">\*\* \@ source_object\*\* -要發行的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="1c922-174">**\@source_object** - the database object being published.</span></span>  
  
    -   <span data-ttu-id="1c922-175">\*\* \@ subset_filterclause\*\* -用來以水準方式篩選發行項的選擇性參數化篩選子句。</span><span class="sxs-lookup"><span data-stu-id="1c922-175">**\@subset_filterclause** - the optional parameterized filter clause used to horizontally filter the article.</span></span>  
  
    -   <span data-ttu-id="1c922-176">\*\* \@ partition_options\*\* -已篩選之發行項的資料分割選項。</span><span class="sxs-lookup"><span data-stu-id="1c922-176">**\@partition_options** - the partition options for the filtered article.</span></span>  
  
4.  <span data-ttu-id="1c922-177">針對發行集中的每一個發行項重複步驟 3。</span><span class="sxs-lookup"><span data-stu-id="1c922-177">Repeat step 3 for each article in the publication.</span></span>  
  
5.  <span data-ttu-id="1c922-178">(選擇性) 在發行集資料庫的發行者上，執行 [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) ，以定義兩個發行項之間的聯結篩選。</span><span class="sxs-lookup"><span data-stu-id="1c922-178">(Optional) At the Publisher on the publication database, execute [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) to define a join filter between two articles.</span></span> <span data-ttu-id="1c922-179">如需詳細資訊，請參閱 [定義和修改合併發行項之間的聯結篩選](define-and-modify-a-join-filter-between-merge-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="1c922-179">For more information, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
#### <a name="to-view-and-modify-merge-filter-behaviors-for-an-existing-publication"></a><span data-ttu-id="1c922-180">檢視及修改現有發行集的合併篩選行為</span><span class="sxs-lookup"><span data-stu-id="1c922-180">To view and modify merge filter behaviors for an existing publication</span></span>  
  
1.  <span data-ttu-id="1c922-181"> (發行集資料庫之發行者上的選擇性) ，請執行[sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)，指\定\** \@ 發\行\**集。</span><span class="sxs-lookup"><span data-stu-id="1c922-181">(Optional) At the Publisher on the publication database, execute [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), specifying **\@publication**.</span></span> <span data-ttu-id="1c922-182">請注意結果集中 **keep_partition_changes** 和 **use_partition_groups** 的值。</span><span class="sxs-lookup"><span data-stu-id="1c922-182">Note the value of **keep_partition_changes** and **use_partition_groups** in the result set.</span></span>  
  
2.  <span data-ttu-id="1c922-183">(選擇性) 在發行集資料庫的發行者上，執行 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1c922-183">(Optional) At the Publisher on the publication database, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="1c922-184">為 [ \*\* \@ 屬性\*\*] 指定 [ **use_partition_groups** ] 的值，並為 [值] 指定 `true` 或 `false` 。 \*\* \@ \*\*</span><span class="sxs-lookup"><span data-stu-id="1c922-184">Specify a value of **use_partition_groups** for **\@property** and either `true` or `false` for **\@value**.</span></span>  
  
3.  <span data-ttu-id="1c922-185">(選擇性) 在發行集資料庫的發行者上，執行 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1c922-185">(Optional) At the Publisher on the publication database, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="1c922-186">為 [ \*\* \@ 屬性\*\*] 指定 [ **keep_partition_changes** ] 的值，並為 [值] 指定 `true` 或 `false` 。 \*\* \@ \*\*</span><span class="sxs-lookup"><span data-stu-id="1c922-186">Specify a value of **keep_partition_changes** for **\@property** and either `true` or `false` for **\@value**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1c922-187">啟用**keep_partition_changes**時，您必須先停用**use_partition_groups** ，並為\*\* \@ force_reinit_subscription**指定**1\*\*的值。</span><span class="sxs-lookup"><span data-stu-id="1c922-187">When enabling **keep_partition_changes**, you must first disable **use_partition_groups** and specify a value of **1** for **\@force_reinit_subscription**.</span></span>  
  
4.  <span data-ttu-id="1c922-188">(選擇性) 在發行集資料庫的發行者上，執行 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1c922-188">(Optional) At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="1c922-189">為 [ \*\* \@ 屬性**] 指定 [ **partition_options** ] 的值，並為 [ \*\* \@ 值**] 指定適當的值。</span><span class="sxs-lookup"><span data-stu-id="1c922-189">Specify a value of **partition_options** for **\@property** and the appropriate value for **\@value**.</span></span> <span data-ttu-id="1c922-190">如需這些篩選選項的定義，請參閱 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="1c922-190">See [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) for definitions of these filtering options.</span></span>  
  
5.  <span data-ttu-id="1c922-191">(選擇性) 在必要時，啟動快照集代理程式來重新產生快照集。</span><span class="sxs-lookup"><span data-stu-id="1c922-191">(Optional) Start the Snapshot Agent to regenerate the snapshot if necessary.</span></span> <span data-ttu-id="1c922-192">如需哪些變更需要產生新快照集的資訊，請參閱[變更發行集與發行項屬性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="1c922-192">For information about which changes require a new snapshot to be generated, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c922-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c922-193">See Also</span></span>  
 <span data-ttu-id="1c922-194">[在合併發行項之間自動產生一組聯結篩選 &#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md) </span><span class="sxs-lookup"><span data-stu-id="1c922-194">[Automatically Generate a Set of Join Filters Between Merge Articles &#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md) </span></span>  
 <span data-ttu-id="1c922-195">[針對合併發行項定義及修改參數化資料列篩選](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="1c922-195">[Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span></span>  
 [<span data-ttu-id="1c922-196">參數化資料列篩選器</span><span class="sxs-lookup"><span data-stu-id="1c922-196">Parameterized Row Filters</span></span>](../merge/parameterized-filters-parameterized-row-filters.md)  
  
  
