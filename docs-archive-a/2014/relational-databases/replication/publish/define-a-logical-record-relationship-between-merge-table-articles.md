---
title: 定義合併資料表發行項之間的邏輯記錄關聯性 | Microsoft 文件
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication logical records [SQL Server replication]
- articles [SQL Server replication], logical records
- logical records [SQL Server replication]
ms.assetid: ff847b3a-c6b0-4eaf-b225-2ffc899c5558
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60c92a237562704e5bc5d43717f863aa78a14b55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709146"
---
# <a name="define-a-logical-record-relationship-between-merge-table-articles"></a><span data-ttu-id="27ba6-102">定義合併資料表發行項之間的邏輯記錄關聯性</span><span class="sxs-lookup"><span data-stu-id="27ba6-102">Define a Logical Record Relationship Between Merge Table Articles</span></span>
  <span data-ttu-id="27ba6-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或 Replication Management Objects (RMO)，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中定義合併資料表發行項之間的邏輯記錄關聯性。</span><span class="sxs-lookup"><span data-stu-id="27ba6-103">This topic describes how to define a logical record relationship between merge table articles in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="27ba6-104">合併式複寫可讓您在不同資料表內定義相關資料列之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="27ba6-104">Merge replication allows you to define a relationship between related rows in different tables.</span></span> <span data-ttu-id="27ba6-105">然後這些資料列在同步處理期間，可以當做交易式單位來處理。</span><span class="sxs-lookup"><span data-stu-id="27ba6-105">These rows can then be processed as a transactional unit during synchronization.</span></span> <span data-ttu-id="27ba6-106">可以在兩個發行項之間定義邏輯記錄，不論這些發行項是否有聯結篩選關聯性。</span><span class="sxs-lookup"><span data-stu-id="27ba6-106">A logical record can be defined between two articles whether or not they have a join filter relationship.</span></span> <span data-ttu-id="27ba6-107">如需詳細資訊，請參閱[使用邏輯記錄分組相關資料列的變更](../merge/group-changes-to-related-rows-with-logical-records.md)。</span><span class="sxs-lookup"><span data-stu-id="27ba6-107">For more information, see [Group Changes to Related Rows with Logical Records](../merge/group-changes-to-related-rows-with-logical-records.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="27ba6-108">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="27ba6-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="27ba6-109">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="27ba6-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="27ba6-110">限制事項</span><span class="sxs-lookup"><span data-stu-id="27ba6-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   <span data-ttu-id="27ba6-111">**若要定義合併資料表發行項之間的邏輯記錄關聯性，請使用：**</span><span class="sxs-lookup"><span data-stu-id="27ba6-111">**To define a logical record relationship between merge table articles, using:**</span></span>  
  
     [<span data-ttu-id="27ba6-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="27ba6-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="27ba6-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="27ba6-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="27ba6-114">Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="27ba6-114">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="27ba6-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="27ba6-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="27ba6-116">限制事項</span><span class="sxs-lookup"><span data-stu-id="27ba6-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="27ba6-117">如果您在初始化發行集的訂閱後，新增、修改或刪除邏輯記錄，則必須在進行變更後產生新的快照集並重新初始化所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="27ba6-117">If you add, modify, or delete a logical record after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="27ba6-118">如需屬性變更需求的詳細資訊，請參閱[變更發行集與發行項屬性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="27ba6-118">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="27ba6-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="27ba6-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="27ba6-120">您可在位於 [新增發行集精靈] 和 [發行集屬性 - \<Publication>] 對話方塊的 [新增聯結] 對話方塊中定義邏輯記錄。</span><span class="sxs-lookup"><span data-stu-id="27ba6-120">Define logical records in the **Add Join** dialog box, which is available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="27ba6-121">如需使用精靈及存取對話方塊的詳細資訊，請參閱[建立發行集](create-a-publication.md)和[檢視及修改發行集屬性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="27ba6-121">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
 <span data-ttu-id="27ba6-122">只有將邏輯記錄套用至合併式發行集中的聯結篩選，並且該發行集符合使用預先計算的資料分割要求時，方可在 **[加入聯結]** 對話方塊中定義這些邏輯記錄。</span><span class="sxs-lookup"><span data-stu-id="27ba6-122">Logical records can be defined in the **Add Join** dialog box only if they are applied to a join filter in a merge publication, and the publication follows the requirements for using precomputed partitions.</span></span> <span data-ttu-id="27ba6-123">若要定義未套用至聯結篩選的邏輯記錄，並在邏輯記錄層級設定衝突偵測和解決方案，您必須使用預存程序。</span><span class="sxs-lookup"><span data-stu-id="27ba6-123">To define logical records that are not applied to join filters and to set conflict detection and resolution at the logical record level, you must use stored procedures.</span></span>  
  
#### <a name="to-define-a-logical-record-relationship"></a><span data-ttu-id="27ba6-124">若要定義邏輯記錄關聯性</span><span class="sxs-lookup"><span data-stu-id="27ba6-124">To define a logical record relationship</span></span>  
  
1.  <span data-ttu-id="27ba6-125">在 [新增發行集精靈] 的 [篩選資料表的資料列] 頁面上，或在 [發行集屬性 - \<Publication>] 對話方塊的 [篩選資料列] 頁面上，從 [已篩選的資料表] 窗格中選取一個資料列篩選。</span><span class="sxs-lookup"><span data-stu-id="27ba6-125">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, select a row filter in the **Filtered Tables** pane.</span></span>  
  
     <span data-ttu-id="27ba6-126">邏輯記錄關聯性與聯結篩選相關聯，這會擴充資料列篩選。</span><span class="sxs-lookup"><span data-stu-id="27ba6-126">A logical record relationship is associated with a join filter, which extends a row filter.</span></span> <span data-ttu-id="27ba6-127">因此，您必須在使用聯結擴充篩選並套用邏輯記錄關聯性之前，先定義資料列篩選。</span><span class="sxs-lookup"><span data-stu-id="27ba6-127">Therefore you must define a row filter before you can extend the filter with a join and apply a logical record relationship.</span></span> <span data-ttu-id="27ba6-128">定義好一個聯結篩選後，您可以以另一個聯結篩選擴充這個聯結篩選。</span><span class="sxs-lookup"><span data-stu-id="27ba6-128">After one join filter is defined, you can extend this join filter with another join filter.</span></span> <span data-ttu-id="27ba6-129">如需定義聯結篩選的詳細資訊，請參閱＜ [定義和修改合併發行項之間的聯結篩選](define-and-modify-a-join-filter-between-merge-articles.md)＞。</span><span class="sxs-lookup"><span data-stu-id="27ba6-129">For more information about defining join filters, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
2.  <span data-ttu-id="27ba6-130">按一下 **[加入]** ，然後按一下 **[加入聯結以擴充選取的篩選]** 。</span><span class="sxs-lookup"><span data-stu-id="27ba6-130">Click **Add**, and then click **Add Join to Extend the Selected Filter**.</span></span>  
  
3.  <span data-ttu-id="27ba6-131">在 **[加入聯結]** 對話方塊中定義聯結篩選，然後選取 **[邏輯記錄]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="27ba6-131">Define a join filter in the **Add Join** dialog box, and then select the check box **Logical Record**.</span></span>  
  
4.  <span data-ttu-id="27ba6-132">如果在 [發行集屬性 - \<Publication>] 對話方塊中，請按一下 [確定] 以儲存並關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="27ba6-132">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-delete-a-logical-record-relationship"></a><span data-ttu-id="27ba6-133">若要刪除邏輯記錄關聯性</span><span class="sxs-lookup"><span data-stu-id="27ba6-133">To delete a logical record relationship</span></span>  
  
-   <span data-ttu-id="27ba6-134">僅刪除邏輯記錄關聯性，或刪除邏輯記錄關聯性及與其相關聯的聯結篩選。</span><span class="sxs-lookup"><span data-stu-id="27ba6-134">Delete only the logical record relationship or delete the logical record relationship and the join filter associated with it.</span></span>  
  
     <span data-ttu-id="27ba6-135">若要僅刪除邏輯記錄關聯性：</span><span class="sxs-lookup"><span data-stu-id="27ba6-135">To delete only the logical record relationship:</span></span>  
  
    1.  <span data-ttu-id="27ba6-136">在 [新增發行集精靈] 的 [篩選資料列] 頁面上，或在 [發行集屬性 - \<Publication>] 對話方塊的 [篩選資料列] 頁面上，從 [已篩選的資料表] 窗格中選取與邏輯記錄關聯性建立關聯的聯結篩選，然後按一下 [編輯]。</span><span class="sxs-lookup"><span data-stu-id="27ba6-136">On the **Filter Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, select the join filter associated with the logical record relationship in the **Filtered Tables** pane, and then click **Edit**.</span></span>  
  
    2.  <span data-ttu-id="27ba6-137">在 **[編輯聯結]** 對話方塊中，清除 **[邏輯記錄]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="27ba6-137">In the **Edit Join** dialog box, clear the check box **Logical Record**.</span></span>  
  
    3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="27ba6-138">若要刪除邏輯記錄關聯性及與其關聯的聯結篩選：</span><span class="sxs-lookup"><span data-stu-id="27ba6-138">To delete the logical record relationship and join filter associated with it:</span></span>  
  
    -   <span data-ttu-id="27ba6-139">在 [新增發行集精靈] 或 [發行集屬性 - \<Publication>] 對話方塊的 [篩選資料列] 頁面上，從 [已篩選的資料表] 窗格中選取一個篩選，然後按一下 [刪除]。</span><span class="sxs-lookup"><span data-stu-id="27ba6-139">On the **Filter Rows** page of the New Publication Wizard or **Publication Properties - \<Publication>** dialog box, select a filter in the **Filtered Tables** pane, and then click **Delete**.</span></span> <span data-ttu-id="27ba6-140">如果您刪除的聯結篩選本身已由其他聯結擴充，也會一併刪除這些聯結。</span><span class="sxs-lookup"><span data-stu-id="27ba6-140">If the join filter you delete is itself extended by other joins, those joins will also be deleted.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="27ba6-141">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="27ba6-141">Using Transact-SQL</span></span>  
 <span data-ttu-id="27ba6-142">您可以使用複寫預存程序，以程式設計方式指定發行項之間的邏輯記錄關聯性。</span><span class="sxs-lookup"><span data-stu-id="27ba6-142">You can programmatically specify logical record relationships between articles using replication stored procedures.</span></span>  
  
#### <a name="to-define-a-logical-record-relationship-without-an-associated-join-filter"></a><span data-ttu-id="27ba6-143">定義沒有相關聯結篩選的邏輯記錄關聯性</span><span class="sxs-lookup"><span data-stu-id="27ba6-143">To define a logical record relationship without an associated join filter</span></span>  
  
1.  <span data-ttu-id="27ba6-144">如果發行集包含任何篩選的發行項，請執行 [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)，並記下結果集中的 **use_partition_groups** 值。</span><span class="sxs-lookup"><span data-stu-id="27ba6-144">If the publication contains any articles that are filtered, execute [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), and note the value of **use_partition_groups** in the result set.</span></span>  
  
    -   <span data-ttu-id="27ba6-145">如果這個值是 **1**，則表示已經使用預先計算的資料分割。</span><span class="sxs-lookup"><span data-stu-id="27ba6-145">If the value is **1**, then precomputed partitions are already being used.</span></span>  
  
    -   <span data-ttu-id="27ba6-146">如果這個值是 **0**，請在發行集資料庫的發行者上執行 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="27ba6-146">If the value is **0**, then execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="27ba6-147">請為 **use_partition_groups** 指定 **@property** 的值，並為 **@value** 指定 **@value**。</span><span class="sxs-lookup"><span data-stu-id="27ba6-147">Specify a value of **use_partition_groups** for **@property** and a value of **true** for **@value**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="27ba6-148">如果發行集不支援預先計算的資料分割，將無法使用邏輯記錄。</span><span class="sxs-lookup"><span data-stu-id="27ba6-148">If the publication does not support precomputed partitions, then logical records cannot be used.</span></span> <span data-ttu-id="27ba6-149">如需詳細資訊，請參閱[使用預先計算的資料分割最佳化參數化篩選效能](../merge/parameterized-filters-optimize-for-precomputed-partitions.md)主題中的＜使用預先計算的資料分割之需求＞。</span><span class="sxs-lookup"><span data-stu-id="27ba6-149">For more information, see Requirements for Using Precomputed Partitions in the topic [Optimize Parameterized Filter Performance with Precomputed Partitions](../merge/parameterized-filters-optimize-for-precomputed-partitions.md).</span></span>  
  
    -   <span data-ttu-id="27ba6-150">如果此值為 NULL，則必須執行快照集代理程式，才能為發行集產生初始快照集。</span><span class="sxs-lookup"><span data-stu-id="27ba6-150">If the value is NULL, then the Snapshot Agent needs to be run to generate the initial snapshot for the publication.</span></span>  
  
2.  <span data-ttu-id="27ba6-151">如果組成此邏輯記錄的發行項不存在，請在發行集資料庫的發行者上執行 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="27ba6-151">If the articles that will comprise the logical record do not exist, execute [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="27ba6-152">針對此邏輯記錄指定下列其中一個衝突偵測和解決選項：</span><span class="sxs-lookup"><span data-stu-id="27ba6-152">Specify one of the following conflict detection and resolution options for the logical record:</span></span>  
  
    -   <span data-ttu-id="27ba6-153">若要偵測及解決邏輯記錄中相關資料列內所發生的衝突，請為 **@value** 指定 **@logical_record_level_conflict_detection** ＞和＜ **@logical_record_level_conflict_resolution**。</span><span class="sxs-lookup"><span data-stu-id="27ba6-153">To detect and resolve conflicts that occur within related rows in the logic record, specify a value of **true** for **@logical_record_level_conflict_detection** and **@logical_record_level_conflict_resolution**.</span></span>  
  
    -   <span data-ttu-id="27ba6-154">若要使用標準資料列或資料行層級的衝突偵測和解決方法，請 `false` 為和指定的值 **@logical_record_level_conflict_detection** **@logical_record_level_conflict_resolution** ，這是預設值。</span><span class="sxs-lookup"><span data-stu-id="27ba6-154">To use the standard row- or column-level conflict detection and resolution, specify a value of `false` for **@logical_record_level_conflict_detection** and **@logical_record_level_conflict_resolution**, which is the default.</span></span>  
  
3.  <span data-ttu-id="27ba6-155">針對組成此邏輯記錄的每一個發行項重複步驟 2。</span><span class="sxs-lookup"><span data-stu-id="27ba6-155">Repeat step 2 for each article that will comprise the logical record.</span></span> <span data-ttu-id="27ba6-156">您必須針對此邏輯記錄中的每一個發行項使用相同的衝突偵測和解決選項。</span><span class="sxs-lookup"><span data-stu-id="27ba6-156">You must use the same conflict detection and resolution option for each article in the logical record.</span></span> <span data-ttu-id="27ba6-157">如需詳細資訊，請參閱 [偵測和解決邏輯記錄中的衝突](../merge/advanced-merge-replication-conflict-resolving-in-logical-record.md)。</span><span class="sxs-lookup"><span data-stu-id="27ba6-157">For more information, see [Detecting and Resolving Conflicts in Logical Records](../merge/advanced-merge-replication-conflict-resolving-in-logical-record.md).</span></span>  
  
4.  <span data-ttu-id="27ba6-158">在發行集資料庫的發行者上，執行 [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="27ba6-158">At the publisher on the publication database, execute [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql).</span></span> <span data-ttu-id="27ba6-159">指定 **@publication** 、的關聯性中的一個發行項名稱 **@article** 、的第二個發行項名稱、的關聯性名稱、定義兩個發行項之關聯性的子句、的 **@join_articlename** **@filtername** **@join_filterclause** 聯結類型，以及下列專案的 **@join_unique_key** 其中一個值 **@filter_type** ：</span><span class="sxs-lookup"><span data-stu-id="27ba6-159">Specify **@publication**, the name of one article in the relationship for **@article**, the name of the second article for **@join_articlename**, a name for the relationship for **@filtername**, a clause that defines the relationship between the two articles for **@join_filterclause**, the type of join for **@join_unique_key** and one of the following values for **@filter_type**:</span></span>  
  
    -   <span data-ttu-id="27ba6-160">**2** - 定義邏輯關聯性。</span><span class="sxs-lookup"><span data-stu-id="27ba6-160">**2** - Defines a logical relationship.</span></span>  
  
    -   <span data-ttu-id="27ba6-161">**3** - 定義具有聯結篩選的邏輯關聯性。</span><span class="sxs-lookup"><span data-stu-id="27ba6-161">**3** - Defines a logical relationship with a join filter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="27ba6-162">如果未使用聯結篩選，則兩個發行項之間的關聯性方向就不是那麼重要。</span><span class="sxs-lookup"><span data-stu-id="27ba6-162">If a join filter is not used, the direction of the relationship between the two articles is not important.</span></span>  
  
5.  <span data-ttu-id="27ba6-163">針對發行集中每一個剩餘的邏輯記錄關聯性重複步驟 2。</span><span class="sxs-lookup"><span data-stu-id="27ba6-163">Repeat step 2 for each remaining logical record relationship in the publication.</span></span>  
  
#### <a name="to-change-conflict-detection-and-resolution-for-logical-records"></a><span data-ttu-id="27ba6-164">變更邏輯記錄的衝突偵測和解決方式</span><span class="sxs-lookup"><span data-stu-id="27ba6-164">To change conflict detection and resolution for logical records</span></span>  
  
1.  <span data-ttu-id="27ba6-165">若要偵測及解決邏輯記錄中相關資料列內所發生的衝突：</span><span class="sxs-lookup"><span data-stu-id="27ba6-165">To detect and resolve conflicts that occur within related rows in the logical record:</span></span>  
  
    -   <span data-ttu-id="27ba6-166">在發行集資料庫的發行者上，執行 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="27ba6-166">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="27ba6-167">請為 **@property** 指定 **@property** 的值，並為 **@value** 指定 **@value**。</span><span class="sxs-lookup"><span data-stu-id="27ba6-167">Specify a value of **logical_record_level_conflict_detection** for **@property** and a value of **true** for **@value**.</span></span> <span data-ttu-id="27ba6-168">請為 **1** 指定 **@force_invalidate_snapshot** ＞和＜ **@force_reinit_subscription**。</span><span class="sxs-lookup"><span data-stu-id="27ba6-168">Specify a value of **1** for **@force_invalidate_snapshot** and **@force_reinit_subscription**.</span></span>  
  
    -   <span data-ttu-id="27ba6-169">在發行集資料庫的發行者上，執行 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="27ba6-169">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="27ba6-170">請為 **@property** 指定 **@property** 的值，並為 **@value** 指定 **@value**。</span><span class="sxs-lookup"><span data-stu-id="27ba6-170">Specify a value of **logical_record_level_conflict_resolution** for **@property** and a value of **true** for **@value**.</span></span> <span data-ttu-id="27ba6-171">請為 **1** 指定 **@force_invalidate_snapshot** ＞和＜ **@force_reinit_subscription**。</span><span class="sxs-lookup"><span data-stu-id="27ba6-171">Specify a value of **1** for **@force_invalidate_snapshot** and **@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="27ba6-172">若要使用標準資料列層級或資料行層級的衝突偵測與解決方式：</span><span class="sxs-lookup"><span data-stu-id="27ba6-172">To use the standard row-level or column-level conflict detection and resolution:</span></span>  
  
    -   <span data-ttu-id="27ba6-173">在發行集資料庫的發行者上，執行 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="27ba6-173">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="27ba6-174">針對指定 [ **logical_record_level_conflict_detection** ] 的值 **@property** ，並針對 [] 指定的值 `false` **@value** 。</span><span class="sxs-lookup"><span data-stu-id="27ba6-174">Specify a value of **logical_record_level_conflict_detection** for **@property** and a value of `false` for **@value**.</span></span> <span data-ttu-id="27ba6-175">請為 **1** 指定 **@force_invalidate_snapshot** ＞和＜ **@force_reinit_subscription**。</span><span class="sxs-lookup"><span data-stu-id="27ba6-175">Specify a value of **1** for **@force_invalidate_snapshot** and **@force_reinit_subscription**.</span></span>  
  
    -   <span data-ttu-id="27ba6-176">在發行集資料庫的發行者上，執行 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="27ba6-176">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="27ba6-177">針對指定 [ **logical_record_level_conflict_resolution** ] 的值 **@property** ，並針對 [] 指定的值 `false` **@value** 。</span><span class="sxs-lookup"><span data-stu-id="27ba6-177">Specify a value of **logical_record_level_conflict_resolution** for **@property** and a value of `false` for **@value**.</span></span> <span data-ttu-id="27ba6-178">請為 **1** 指定 **@force_invalidate_snapshot** ＞和＜ **@force_reinit_subscription**。</span><span class="sxs-lookup"><span data-stu-id="27ba6-178">Specify a value of **1** for **@force_invalidate_snapshot** and **@force_reinit_subscription**.</span></span>  
  
#### <a name="to-remove-a-logical-record-relationship"></a><span data-ttu-id="27ba6-179">移除邏輯記錄關聯性</span><span class="sxs-lookup"><span data-stu-id="27ba6-179">To remove a logical record relationship</span></span>  
  
1.  <span data-ttu-id="27ba6-180">在發行集資料庫的發行者上，執行下列查詢來傳回有關針對指定之發行集定義之所有邏輯記錄關聯性的資訊：</span><span class="sxs-lookup"><span data-stu-id="27ba6-180">At the Publisher on the publication database, execute the following query to return information about all logical record relationships defined for the specified publication:</span></span>  
  
     [!code-sql[HowTo#sp_ReturnMergeLogicalRecords](../../../snippets/tsql/SQL15/replication/howto/tsql/createlogicalrecordpub.sql#sp_returnmergelogicalrecords)]  
  
     <span data-ttu-id="27ba6-181">請注意從結果集中 `filtername` 資料行所移除的邏輯記錄關聯性名稱。</span><span class="sxs-lookup"><span data-stu-id="27ba6-181">Note the name of the logical record relationship being removed in the `filtername` column in the result set.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="27ba6-182">此查詢會傳回與 [sp_helpmergefilter](/sql/relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql)相同的資訊，但是此系統預存程序只會傳回也屬於聯結篩選之邏輯記錄關聯性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="27ba6-182">This query returns the same information as [sp_helpmergefilter](/sql/relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql); however, this system stored procedure only returns information about logical record relationships that are also join filters.</span></span>  
  
2.  <span data-ttu-id="27ba6-183">在發行集資料庫的發行者上，執行 [sp_dropmergefilter](/sql/relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="27ba6-183">At the Publisher on the publication database, execute [sp_dropmergefilter](/sql/relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql).</span></span> <span data-ttu-id="27ba6-184">指定 **@publication** 、關聯性中的其中一個發行項名稱 **@article** ，以及步驟1中的關聯性名稱 **@filtername** 。</span><span class="sxs-lookup"><span data-stu-id="27ba6-184">Specify **@publication**, the name of one of the articles in the relationship for **@article**, and the name of the relationship from step 1 for **@filtername**.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="27ba6-185">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="27ba6-185">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="27ba6-186">這個範例會在現有的發行集上啟用預先計算的資料分割，並針對 `SalesOrderHeader` 和 `SalesOrderDetail` 資料表建立組成兩個新發行項的邏輯記錄。</span><span class="sxs-lookup"><span data-stu-id="27ba6-186">This example enables precomputed partitions on an existing publication, and creates a logical record comprising the two new articles for the `SalesOrderHeader` and `SalesOrderDetail` tables.</span></span>  
  
 [!code-sql[HowTo#sp_AddMergeLogicalRecord](../../../snippets/tsql/SQL15/replication/howto/tsql/createlogicalrecordpub.sql#sp_addmergelogicalrecord)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="27ba6-187">使用 Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="27ba6-187">Using Replication Management Objects (RMO)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27ba6-188">合併式複寫可允許您指定在邏輯記錄層級追蹤及解決衝突，但這些選項無法使用 RMO 來設定。</span><span class="sxs-lookup"><span data-stu-id="27ba6-188">Merge replication allows you to specify that conflicts be tracked and resolved at the logical record level, but these options cannot be set using RMO.</span></span>  
  
#### <a name="to-define-a-logical-record-relationship-without-an-associated-join-filter"></a><span data-ttu-id="27ba6-189">定義沒有相關聯結篩選的邏輯記錄關聯性</span><span class="sxs-lookup"><span data-stu-id="27ba6-189">To define a logical record relationship without an associated join filter</span></span>  
  
1.  <span data-ttu-id="27ba6-190">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="27ba6-190">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="27ba6-191">建立 <xref:Microsoft.SqlServer.Replication.MergePublication> 類別的執行個體、為發行集設定 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 和 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 屬性，以及將 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定為步驟 1 中所建立的連接。</span><span class="sxs-lookup"><span data-stu-id="27ba6-191">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class, set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
3.  <span data-ttu-id="27ba6-192">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="27ba6-192">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object.</span></span> <span data-ttu-id="27ba6-193">如果此方法傳回 `false`，則表示步驟 2 中的發行集屬性定義不正確，或者該發行集不存在。</span><span class="sxs-lookup"><span data-stu-id="27ba6-193">If this method returns `false`, either the publication properties in step 2 were defined incorrectly or the publication does not exist.</span></span>  
  
4.  <span data-ttu-id="27ba6-194">如果 <xref:Microsoft.SqlServer.Replication.MergePublication.PartitionGroupsOption%2A> 屬性設定為 <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.False>，請將它設定為 <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.True>。</span><span class="sxs-lookup"><span data-stu-id="27ba6-194">If the <xref:Microsoft.SqlServer.Replication.MergePublication.PartitionGroupsOption%2A> property is set to <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.False>, set it to <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.True>.</span></span>  
  
5.  <span data-ttu-id="27ba6-195">如果組成此邏輯記錄的發行項不存在，請建立 <xref:Microsoft.SqlServer.Replication.MergeArticle> 類別的執行個體，並設定以下屬性：</span><span class="sxs-lookup"><span data-stu-id="27ba6-195">If the articles that are to comprise the logical record do not exist, create an instance of the <xref:Microsoft.SqlServer.Replication.MergeArticle> class, and set the following properties:</span></span>  
  
    -   <span data-ttu-id="27ba6-196">將 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>設定為發行項名稱。</span><span class="sxs-lookup"><span data-stu-id="27ba6-196">The name of the article for <xref:Microsoft.SqlServer.Replication.Article.Name%2A>.</span></span>  
  
    -   <span data-ttu-id="27ba6-197">將 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>設定為發行集名稱。</span><span class="sxs-lookup"><span data-stu-id="27ba6-197">The name of the publication for <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>.</span></span>  
  
    -   <span data-ttu-id="27ba6-198">(選擇性) 如果以水平方式篩選此發行項，請為 <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> 屬性指定資料列篩選子句。</span><span class="sxs-lookup"><span data-stu-id="27ba6-198">(Optional) If the article is horizontally filtered, specify the row filter clause for the <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> property.</span></span> <span data-ttu-id="27ba6-199">使用此屬性可指定靜態或參數化資料列篩選器。</span><span class="sxs-lookup"><span data-stu-id="27ba6-199">Use this property to specify a static or parameterized row filter.</span></span> <span data-ttu-id="27ba6-200">如需詳細資訊，請參閱＜ [參數化資料列篩選器](../merge/parameterized-filters-parameterized-row-filters.md)＞。</span><span class="sxs-lookup"><span data-stu-id="27ba6-200">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
     <span data-ttu-id="27ba6-201">如需詳細資訊，請參閱 [定義發行項](define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="27ba6-201">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
6.  <span data-ttu-id="27ba6-202">呼叫 <xref:Microsoft.SqlServer.Replication.Article.Create%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="27ba6-202">Call the <xref:Microsoft.SqlServer.Replication.Article.Create%2A> method.</span></span>  
  
7.  <span data-ttu-id="27ba6-203">針對組成此邏輯記錄的每一個發行項重複執行步驟 5 和 6。</span><span class="sxs-lookup"><span data-stu-id="27ba6-203">Repeat steps 5 and 6 for each article comprising the logical record.</span></span>  
  
8.  <span data-ttu-id="27ba6-204">建立 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> 類別的執行個體，以定義發行項之間的邏輯記錄關聯性。</span><span class="sxs-lookup"><span data-stu-id="27ba6-204">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> class to define the logical record relationship between articles.</span></span> <span data-ttu-id="27ba6-205">然後，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="27ba6-205">Then, set the following properties:</span></span>  
  
    -   <span data-ttu-id="27ba6-206">將 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.ArticleName%2A> 屬性設定為邏輯記錄關聯性中的子發行項名稱。</span><span class="sxs-lookup"><span data-stu-id="27ba6-206">The name of the child article in the logical record relationship for the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.ArticleName%2A> property.</span></span>  
  
    -   <span data-ttu-id="27ba6-207">將 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinArticleName%2A> 屬性設定為邏輯記錄關聯性中的現有父發行項名稱。</span><span class="sxs-lookup"><span data-stu-id="27ba6-207">The name of the existing, parent article in the logical record relationship for the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinArticleName%2A> property.</span></span>  
  
    -   <span data-ttu-id="27ba6-208">將 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterName%2A> 屬性設定為邏輯記錄關聯性的名稱。</span><span class="sxs-lookup"><span data-stu-id="27ba6-208">A name for the logical record relationship for the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterName%2A> property.</span></span>  
  
    -   <span data-ttu-id="27ba6-209">將 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinFilterClause%2A> 屬性設定為定義此關聯性的運算式。</span><span class="sxs-lookup"><span data-stu-id="27ba6-209">The expression that defines the relationship for the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinFilterClause%2A> property.</span></span>  
  
    -   <span data-ttu-id="27ba6-210">將 <xref:Microsoft.SqlServer.Replication.FilterTypes.LogicalRecordLink> 屬性設定為 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterTypes%2A> 的值。</span><span class="sxs-lookup"><span data-stu-id="27ba6-210">A value of <xref:Microsoft.SqlServer.Replication.FilterTypes.LogicalRecordLink> for the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterTypes%2A> property.</span></span> <span data-ttu-id="27ba6-211">如果邏輯記錄關聯性也是聯結篩選，請針對這個屬性指定 <xref:Microsoft.SqlServer.Replication.FilterTypes.JoinFilterAndLogicalRecordLink> 的值。</span><span class="sxs-lookup"><span data-stu-id="27ba6-211">If the logical record relationship is also a join filter, specify a value of <xref:Microsoft.SqlServer.Replication.FilterTypes.JoinFilterAndLogicalRecordLink> for this property.</span></span> <span data-ttu-id="27ba6-212">如需詳細資訊，請參閱[使用邏輯記錄分組相關資料列的變更](../merge/group-changes-to-related-rows-with-logical-records.md)。</span><span class="sxs-lookup"><span data-stu-id="27ba6-212">For more information, see [Group Changes to Related Rows with Logical Records](../merge/group-changes-to-related-rows-with-logical-records.md).</span></span>  
  
9. <span data-ttu-id="27ba6-213">在代表關聯性中子發行項的物件上，呼叫 <xref:Microsoft.SqlServer.Replication.MergeArticle.AddMergeJoinFilter%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="27ba6-213">Call the <xref:Microsoft.SqlServer.Replication.MergeArticle.AddMergeJoinFilter%2A> method on the object that represents the child article in the relationship.</span></span> <span data-ttu-id="27ba6-214">傳遞步驟 8 中的 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> 物件來定義關聯性。</span><span class="sxs-lookup"><span data-stu-id="27ba6-214">Pass the <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> object from step 8 to define the relationship.</span></span>  
  
10. <span data-ttu-id="27ba6-215">針對發行集中每一個剩餘的邏輯記錄關聯性重複步驟 8 和 9。</span><span class="sxs-lookup"><span data-stu-id="27ba6-215">Repeat steps 8 and 9 for each remaining logical record relationship in the publication.</span></span>  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="27ba6-216">範例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="27ba6-216">Example (RMO)</span></span>  
 <span data-ttu-id="27ba6-217">這個範例會針對 `SalesOrderHeader` 和 `SalesOrderDetail` 資料表建立組成兩個新發行項的邏輯記錄。</span><span class="sxs-lookup"><span data-stu-id="27ba6-217">This example creates a logical record comprising the two new articles for the `SalesOrderHeader` and `SalesOrderDetail` tables.</span></span>  
  
 [!code-csharp[HowTo#rmo_CreateLogicalRecord](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createlogicalrecord)]  
  
 [!code-vb[HowTo#rmo_vb_CreateLogicalRecord](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createlogicalrecord)]  
  
## <a name="see-also"></a><span data-ttu-id="27ba6-218">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27ba6-218">See Also</span></span>  
 <span data-ttu-id="27ba6-219">[定義和修改合併發行項之間的聯結篩選](define-and-modify-a-join-filter-between-merge-articles.md) </span><span class="sxs-lookup"><span data-stu-id="27ba6-219">[Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md) </span></span>  
 <span data-ttu-id="27ba6-220">[針對合併發行項定義及修改參數化資料列篩選](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="27ba6-220">[Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span></span>  
 <span data-ttu-id="27ba6-221">[定義及修改靜態資料列篩選](define-and-modify-a-static-row-filter.md) </span><span class="sxs-lookup"><span data-stu-id="27ba6-221">[Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md) </span></span>  
 <span data-ttu-id="27ba6-222">[使用邏輯記錄分組相關資料列的變更](../merge/group-changes-to-related-rows-with-logical-records.md) </span><span class="sxs-lookup"><span data-stu-id="27ba6-222">[Group Changes to Related Rows with Logical Records](../merge/group-changes-to-related-rows-with-logical-records.md) </span></span>  
 <span data-ttu-id="27ba6-223">[使用預先計算的資料分割最佳化參數化篩選效能](../merge/parameterized-filters-optimize-for-precomputed-partitions.md) </span><span class="sxs-lookup"><span data-stu-id="27ba6-223">[Optimize Parameterized Filter Performance with Precomputed Partitions](../merge/parameterized-filters-optimize-for-precomputed-partitions.md) </span></span>  
 [<span data-ttu-id="27ba6-224">使用邏輯記錄分組相關資料列的變更</span><span class="sxs-lookup"><span data-stu-id="27ba6-224">Group Changes to Related Rows with Logical Records</span></span>](../merge/group-changes-to-related-rows-with-logical-records.md)  
  
  
