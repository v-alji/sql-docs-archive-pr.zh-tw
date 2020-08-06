---
title: 針對合併發行項定義及修改參數化資料列篩選 | Microsoft 文件
ms.custom: ''
ms.date: 06/02/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- parameterized filters [SQL Server replication], defining
- parameterized filters [SQL Server replication], modifying
- merge replication [SQL Server replication], dynamic filters
- merge replication parameterized filters [SQL Server replication]
- filters [SQL Server replication], parameterized
- modifying filters, parameterized row
- dynamic filters [SQL Server replication]
ms.assetid: de0482a2-3cc8-4030-8a4a-14364549ac9f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d80ad53661aced22795220507398e2fcc510edd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704998"
---
# <a name="define-and-modify-a-parameterized-row-filter-for-a-merge-article"></a><span data-ttu-id="8921b-102">針對合併發行項定義及修改參數化資料列篩選</span><span class="sxs-lookup"><span data-stu-id="8921b-102">Define and Modify a Parameterized Row Filter for a Merge Article</span></span>
  <span data-ttu-id="8921b-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中定義及修改參數化資料列篩選。</span><span class="sxs-lookup"><span data-stu-id="8921b-103">This topic describes how to define and modify a parameterized row filter in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="8921b-104">在建立資料表發行項時，您可以使用參數化資料列篩選器。</span><span class="sxs-lookup"><span data-stu-id="8921b-104">When creating table articles, you can use parameterized row filters.</span></span> <span data-ttu-id="8921b-105">這些篩選器會使用 [WHERE](/sql/t-sql/queries/where-transact-sql) 子句來選取要發行的適當資料。</span><span class="sxs-lookup"><span data-stu-id="8921b-105">These filters use a [WHERE](/sql/t-sql/queries/where-transact-sql) clause to select the appropriate data to be published.</span></span> <span data-ttu-id="8921b-106">您可以指定下列系統函數的其中一或兩個，而非在子句中指定常值 (如同對靜態資料列篩選的處理)：[SUSER_SNAME](/sql/t-sql/functions/suser-sname-transact-sql) 和 [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8921b-106">Rather than specifying a literal value in the clause (as you do with a static row filter), you specify one or both of the following system functions: [SUSER_SNAME](/sql/t-sql/functions/suser-sname-transact-sql) and [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql).</span></span> <span data-ttu-id="8921b-107">如需詳細資訊，請參閱＜ [參數化資料列篩選器](../merge/parameterized-filters-parameterized-row-filters.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8921b-107">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8921b-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="8921b-108">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8921b-109">限制事項</span><span class="sxs-lookup"><span data-stu-id="8921b-109">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="8921b-110">如果您在初始化發行集的訂閱後，新增、修改或刪除參數化資料列篩選，則必須在進行變更後產生新的快照集並重新初始化所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="8921b-110">If you add, modify, or delete a parameterized row filter after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="8921b-111">如需屬性變更需求的詳細資訊，請參閱[變更發行集與發行項屬性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="8921b-111">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="8921b-112">建議</span><span class="sxs-lookup"><span data-stu-id="8921b-112">Recommendations</span></span>  
  
-   <span data-ttu-id="8921b-113">基於效能的考量，我們建議您不要在參數化資料列篩選器子句中，將函數套用至資料行名稱上，如 `LEFT([MyColumn]) = SUSER_SNAME()`。</span><span class="sxs-lookup"><span data-stu-id="8921b-113">For performance reasons, we recommend that you not apply functions to column names in parameterized row filter clauses, such as `LEFT([MyColumn]) = SUSER_SNAME()`.</span></span> <span data-ttu-id="8921b-114">如果在篩選子句中使用 HOST_NAME，並且覆寫 HOST_NAME 值，則可能需要使用 CONVERT 來轉換資料類型。</span><span class="sxs-lookup"><span data-stu-id="8921b-114">If you use HOST_NAME in a filter clause and override the HOST_NAME value, it might be necessary to convert data types using CONVERT.</span></span> <span data-ttu-id="8921b-115">如需有關此案例之最佳做法的詳細資訊，請參閱主題＜ [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)＞中的「覆寫 HOST_NAME() 值」一節。</span><span class="sxs-lookup"><span data-stu-id="8921b-115">For more information about best practices for this case, see the section "Overriding the HOST_NAME() Value" in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8921b-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8921b-116">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="8921b-117">您可在 [新增發行集精靈] 的 [篩選資料表的資料列] 頁面上，或在 [發行集屬性 - \<Publication>] 對話方塊的 [篩選資料列] 頁面上，定義、修改及刪除參數化資料列篩選。</span><span class="sxs-lookup"><span data-stu-id="8921b-117">Define, modify, and delete parameterized row filters on the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="8921b-118">如需使用精靈及存取對話方塊的詳細資訊，請參閱[建立發行集](create-a-publication.md)和[檢視及修改發行集屬性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="8921b-118">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-define-a-parameterized-row-filter"></a><span data-ttu-id="8921b-119">若要定義參數化資料列篩選器</span><span class="sxs-lookup"><span data-stu-id="8921b-119">To define a parameterized row filter</span></span>  
  
1.  <span data-ttu-id="8921b-120">在 [新增發行集] 精靈的 [篩選資料表的資料列] 頁面上，或在 [發行集屬性 - \<Publication>] 的 [篩選資料列] 頁面上，按一下 [新增]，然後按一下 [新增篩選]。</span><span class="sxs-lookup"><span data-stu-id="8921b-120">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, click **Add**, and then click **Add Filter**.</span></span>  
  
2.  <span data-ttu-id="8921b-121">在 **[加入篩選]** 對話方塊中，從下拉式清單方塊中選取要篩選的資料表。</span><span class="sxs-lookup"><span data-stu-id="8921b-121">In the **Add Filter** dialog box, select a table to filter from the drop-down list box.</span></span>  
  
3.  <span data-ttu-id="8921b-122">在 **[篩選陳述式]** 文字方塊中建立篩選陳述式。</span><span class="sxs-lookup"><span data-stu-id="8921b-122">Create a filter statement in the **Filter statement** text box.</span></span> <span data-ttu-id="8921b-123">您可直接在文字區域輸入，也可以從 **[資料行]** 清單方塊中拖曳資料行。</span><span class="sxs-lookup"><span data-stu-id="8921b-123">You can type directly in the text area, and you can also drag and drop columns from the **Columns** list box.</span></span>  
  
    -   <span data-ttu-id="8921b-124">**[篩選陳述式]** 文字區域包括預設文字，其格式為：</span><span class="sxs-lookup"><span data-stu-id="8921b-124">The **Filter statement** text area includes the default text, which is in the form of:</span></span>  
  
        ```  
        SELECT <published_columns> FROM [tableowner].[tablename] WHERE  
        ```  
  
    -   <span data-ttu-id="8921b-125">預設的文字無法變更；使用標準 SQL 語法，在 WHERE 關鍵字後面輸入篩選子句。</span><span class="sxs-lookup"><span data-stu-id="8921b-125">The default text cannot be changed; type the filter clause after the WHERE keyword using standard SQL syntax.</span></span> <span data-ttu-id="8921b-126">參數化篩選包括對系統函數 `HOST_NAME()` 與/或 `SUSER_SNAME()` 的呼叫，或參考上述一或兩個函數的使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="8921b-126">A parameterized filter includes a call to the system function `HOST_NAME()` and/or `SUSER_SNAME()`, or a user-defined function that references one or both of these functions.</span></span> <span data-ttu-id="8921b-127">下列為參數化資料列篩選器的完整篩選子句範例：</span><span class="sxs-lookup"><span data-stu-id="8921b-127">The following is an example of a complete filter clause for a parameterized row filter:</span></span>  
  
        ```  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE LoginID = SUSER_SNAME()  
        ```  
  
         <span data-ttu-id="8921b-128">WHERE 子句應使用兩部份命名；不支援三部份及四部份命名。</span><span class="sxs-lookup"><span data-stu-id="8921b-128">The WHERE clause should use two-part naming; three-part naming and four-part naming are not supported.</span></span>  
  
4.  <span data-ttu-id="8921b-129">選取符合資料在訂閱者之間共用資料方式的選項：</span><span class="sxs-lookup"><span data-stu-id="8921b-129">Select the option that matches how data will be shared among Subscribers:</span></span>  
  
    -   <span data-ttu-id="8921b-130">**這個資料表中的一個資料列會提供給多個訂閱**</span><span class="sxs-lookup"><span data-stu-id="8921b-130">**A row from this table will go to multiple subscriptions**</span></span>  
  
    -   <span data-ttu-id="8921b-131">**這個資料表中的一個資料列只會提供給一個訂閱**</span><span class="sxs-lookup"><span data-stu-id="8921b-131">**A row from this table will go to only one subscription**</span></span>  
  
     <span data-ttu-id="8921b-132">若您選取 **[這個資料表中的一個資料列只會提供給一個訂閱]** ，合併式複寫可藉由儲存和處理較少中繼資料來將效能最佳化。</span><span class="sxs-lookup"><span data-stu-id="8921b-132">If you select **A row from this table will go to only one subscription**, merge replication can optimize performance by storing and processing less metadata.</span></span> <span data-ttu-id="8921b-133">不過您必須確定資料分割方式不會將資料列複寫至多個訂閱者。</span><span class="sxs-lookup"><span data-stu-id="8921b-133">However, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber.</span></span> <span data-ttu-id="8921b-134">如需進一步資訊，請參閱主題＜ [參數化資料列篩選器](../merge/parameterized-filters-parameterized-row-filters.md)＞中的「設定資料分割選項」。</span><span class="sxs-lookup"><span data-stu-id="8921b-134">For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="8921b-135">如果位於 [發行集屬性 - \<Publication>] 對話方塊中，請按一下 [確定] 以儲存並關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8921b-135">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-modify-a-parameterized-row-filter"></a><span data-ttu-id="8921b-136">若要修改參數化資料列篩選器</span><span class="sxs-lookup"><span data-stu-id="8921b-136">To modify a parameterized row filter</span></span>  
  
1.  <span data-ttu-id="8921b-137">在 [新增發行集精靈] 的 [篩選資料表的資料列] 頁面上，或在 [發行集屬性 - \<Publication>] 的 [篩選資料列] 頁面上，從 [已篩選的資料表] 窗格中選取一個篩選，然後按一下 [編輯]。</span><span class="sxs-lookup"><span data-stu-id="8921b-137">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="8921b-138">在 **[編輯篩選]** 對話方塊中，修改篩選。</span><span class="sxs-lookup"><span data-stu-id="8921b-138">In the **Edit Filter** dialog box, modify the filter.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-parameterized-row-filter"></a><span data-ttu-id="8921b-139">若要刪除參數化資料列篩選器</span><span class="sxs-lookup"><span data-stu-id="8921b-139">To delete a parameterized row filter</span></span>  
  
1.  <span data-ttu-id="8921b-140">在 [新增發行集精靈] 的 [篩選資料表的資料列] 頁面上，或在 [發行集屬性 - \<Publication>] 的 [篩選資料列] 頁面上，從 [已篩選的資料表] 窗格中選取一個篩選，然後按一下 [刪除]。</span><span class="sxs-lookup"><span data-stu-id="8921b-140">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Delete**.</span></span>  
  

  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8921b-141">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8921b-141">Using Transact-SQL</span></span>  
 <span data-ttu-id="8921b-142">您可以使用複寫預存程序來以程式設計的方式建立及修改參數化資料列篩選器。</span><span class="sxs-lookup"><span data-stu-id="8921b-142">Parameterized row filters can be created and modified programmatically using replication stored procedures.</span></span>  
  
#### <a name="to-define-a-parameterized-row-filter-for-an-article-in-a-merge-publication"></a><span data-ttu-id="8921b-143">針對合併式發行集中的發行項定義參數化資料列篩選器</span><span class="sxs-lookup"><span data-stu-id="8921b-143">To define a parameterized row filter for an article in a merge publication</span></span>  
  
1.  <span data-ttu-id="8921b-144">在發行集資料庫的發行者端，執行 [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8921b-144">At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="8921b-145">指定 **@publication** 、發行項的名稱、針對指定 **@article** 發行的資料表、針對 **@source_object** (不包括) 的 WHERE 子句定義參數化篩選， **@subset_filterclause** `WHERE` 以及下列其中一個值 **@partition_options** ，其中描述將會從參數化資料列篩選器產生的資料分割類型：</span><span class="sxs-lookup"><span data-stu-id="8921b-145">Specify **@publication**, a name for the article for **@article**, the table being published for **@source_object**, the WHERE clause that defines the parameterized filter for **@subset_filterclause** (not including `WHERE`), and one of the following values for **@partition_options**, which describes the type of partitioning that will result from the parameterized row filter:</span></span>  
  
    -   <span data-ttu-id="8921b-146">**0** - 發行項的篩選是靜態的，或是不產生每個資料分割的唯一資料子集 (也就是「重疊」的資料分割)。</span><span class="sxs-lookup"><span data-stu-id="8921b-146">**0** - Filtering for the article either is static or does not yield a unique subset of data for each partition (an "overlapping" partition).</span></span>  
  
    -   <span data-ttu-id="8921b-147">**1** - 產生的資料分割是重疊的，而且在訂閱者上進行的更新並不會變更資料列所屬的資料分割。</span><span class="sxs-lookup"><span data-stu-id="8921b-147">**1** - Resulting partitions are overlapping, and updates made at the Subscriber cannot change the partition to which a row belongs.</span></span>  
  
    -   <span data-ttu-id="8921b-148">**2** - 發行項的篩選會產生非重疊的資料分割，但多個訂閱者可以接收相同的資料分割。</span><span class="sxs-lookup"><span data-stu-id="8921b-148">**2** - Filtering for the article yields nonoverlapping partitions, but multiple Subscribers can receive the same partition.</span></span>  
  
    -   <span data-ttu-id="8921b-149">**3** - 發行項的篩選會產生對每項訂閱而言都是唯一的非重疊資料分割。</span><span class="sxs-lookup"><span data-stu-id="8921b-149">**3** - Filtering for the article yields nonoverlapping partitions that are unique for each subscription.</span></span>  
  
#### <a name="to-change-a-parameterized-row-filter-for-an-article-in-a-merge-publication"></a><span data-ttu-id="8921b-150">針對合併式發行集中的發行項變更參數化資料列篩選器</span><span class="sxs-lookup"><span data-stu-id="8921b-150">To change a parameterized row filter for an article in a merge publication</span></span>  
  
1.  <span data-ttu-id="8921b-151">在發行集資料庫的發行者上，執行 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8921b-151">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="8921b-152">指定 **@publication** 、 **@article** 、的值 `subset_filterclause` **@property** 、定義 (不包括) 之參數化篩選的運算式， **@value** `WHERE` 以及和的值**1** **@force_invalidate_snapshot** **@force_reinit_subscription** 。</span><span class="sxs-lookup"><span data-stu-id="8921b-152">Specify **@publication**, **@article**, a value of `subset_filterclause` for **@property**, the expression that defines the parameterized filter for **@value** (not including `WHERE`), and a value of **1** for both **@force_invalidate_snapshot** and **@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="8921b-153">如果此變更會產生不同的資料分割行為，則再次執行 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="8921b-153">If this change results in different partitioning behavior, then execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) again.</span></span> <span data-ttu-id="8921b-154">指定 **@publication** 、 **@article** 、的值 `partition_options` **@property** ，以及最適合的資料分割選項， **@value** 它可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="8921b-154">Specify **@publication**, **@article**, a value of `partition_options` for **@property**, and the most appropriate partitioning option for **@value**, which can be one of the following:</span></span>  
  
    -   <span data-ttu-id="8921b-155">**0** - 發行項的篩選是靜態的，或是不產生每個資料分割的唯一資料子集 (也就是「重疊」的資料分割)。</span><span class="sxs-lookup"><span data-stu-id="8921b-155">**0** - Filtering for the article either is static or does not yield a unique subset of data for each partition (an "overlapping" partition).</span></span>  
  
    -   <span data-ttu-id="8921b-156">**1** - 產生的資料分割是重疊的，而且在訂閱者上進行的更新並不會變更資料列所屬的資料分割。</span><span class="sxs-lookup"><span data-stu-id="8921b-156">**1** - Resulting partitions are overlapping, and updates made at the Subscriber cannot change the partition to which a row belongs.</span></span>  
  
    -   <span data-ttu-id="8921b-157">**2** - 發行項的篩選會產生非重疊的資料分割，但多個訂閱者可以接收相同的資料分割。</span><span class="sxs-lookup"><span data-stu-id="8921b-157">**2** - Filtering for the article yields nonoverlapping partitions, but multiple Subscribers can receive the same partition.</span></span>  
  
    -   <span data-ttu-id="8921b-158">**3** - 發行項的篩選會產生對每項訂閱而言都是唯一的非重疊資料分割。</span><span class="sxs-lookup"><span data-stu-id="8921b-158">**3** - Filtering for the article yields nonoverlapping partitions that are unique for each subscription.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="8921b-159">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8921b-159">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="8921b-160">此範例會在合併式發行集中定義一組發行項，其中的發行項會使用一系列的聯結篩選來針對 `Employee` 資料表進行篩選 (此資料表本身是使用 **LoginID** 資料行上的參數化資料列篩選來進行篩選)。</span><span class="sxs-lookup"><span data-stu-id="8921b-160">This example defines a group of articles in a merge publication where the articles are filtered with a series of join filters against the `Employee` table that is itself filtered using a parameterized row filter on the **LoginID** column.</span></span> <span data-ttu-id="8921b-161">在同步處理期間，會覆寫 [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql) 函數傳回的值。</span><span class="sxs-lookup"><span data-stu-id="8921b-161">During synchronization, the value returned by the [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql) function is overridden.</span></span> <span data-ttu-id="8921b-162">如需詳細資訊，請參閱＜ [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)＞主題中的「覆寫 HOST_NAME() 值」。</span><span class="sxs-lookup"><span data-stu-id="8921b-162">For more information, see Overriding the HOST_NAME() Value in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubdynamic1.sql#sp_mergedynamicpub1)]  
  
  
## <a name="see-also"></a><span data-ttu-id="8921b-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8921b-163">See Also</span></span>  
 <span data-ttu-id="8921b-164">[定義和修改合併發行項之間的聯結篩選](define-and-modify-a-join-filter-between-merge-articles.md) </span><span class="sxs-lookup"><span data-stu-id="8921b-164">[Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md) </span></span>  
 <span data-ttu-id="8921b-165">[變更發行集與發行項屬性](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="8921b-165">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="8921b-166">[Join Filters](../merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="8921b-166">[Join Filters](../merge/join-filters.md) </span></span>  
 [<span data-ttu-id="8921b-167">參數化資料列篩選器</span><span class="sxs-lookup"><span data-stu-id="8921b-167">Parameterized Row Filters</span></span>](../merge/parameterized-filters-parameterized-row-filters.md)  
  
  
