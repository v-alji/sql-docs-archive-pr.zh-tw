---
title: 定義及修改靜態資料列篩選 | Microsoft 文件
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- modifying filters, static row
- static row filters
- filters [SQL Server replication], static row
ms.assetid: a6ebb026-026f-4c39-b6a9-b9998c3babab
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d13fd93b6afdcce6b55e9b181f52087fd620913c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592619"
---
# <a name="define-and-modify-a-static-row-filter"></a><span data-ttu-id="5146e-102">定義及修改靜態資料列篩選</span><span class="sxs-lookup"><span data-stu-id="5146e-102">Define and Modify a Static Row Filter</span></span>
  <span data-ttu-id="5146e-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中定義及修改靜態資料列篩選。</span><span class="sxs-lookup"><span data-stu-id="5146e-103">This topic describes how to define and modify a static row filter in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="5146e-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="5146e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5146e-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="5146e-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5146e-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="5146e-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="5146e-107">建議</span><span class="sxs-lookup"><span data-stu-id="5146e-107">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="5146e-108">**若要定義及修改靜態資料列篩選，請使用：**</span><span class="sxs-lookup"><span data-stu-id="5146e-108">**To define and modify a static row filter, using:**</span></span>  
  
     [<span data-ttu-id="5146e-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5146e-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5146e-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5146e-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5146e-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="5146e-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="5146e-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="5146e-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="5146e-113">如果您在初始化發行集的訂閱後，新增、修改或刪除靜態資料列篩選，則必須在進行變更後產生新的快照集並重新初始化所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="5146e-113">If you add, modify, or delete a static row filter after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="5146e-114">如需屬性變更需求的詳細資訊，請參閱[變更發行集與發行項屬性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="5146e-114">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
-   <span data-ttu-id="5146e-115">如果為點對點異動複寫啟用發行集，則無法篩選資料表。</span><span class="sxs-lookup"><span data-stu-id="5146e-115">If the publication is enabled for peer-to-peer transactional replication, tables cannot be filtered.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="5146e-116">建議</span><span class="sxs-lookup"><span data-stu-id="5146e-116">Recommendations</span></span>  
  
-   <span data-ttu-id="5146e-117">由於這些篩選都是靜態的，所以所有訂閱者都將收到相同子集的資料。</span><span class="sxs-lookup"><span data-stu-id="5146e-117">Because these filters are static, all subscribers will receive the same subset of the data.</span></span> <span data-ttu-id="5146e-118">如果您需要動態篩選屬於合併式發行集之資料表發行項內的資料，好讓每一個訂閱者都會收到不同的資料分割，請參閱＜ [針對合併發行項定義及修改參數化資料列篩選](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5146e-118">If you need to dynamically filter rows in a table article belonging to a merge publication so that each subscriber receives a different partition of the data, see [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).</span></span> <span data-ttu-id="5146e-119">合併式複寫也可讓您根據現有的資料列篩選來篩選相關的資料列。</span><span class="sxs-lookup"><span data-stu-id="5146e-119">Merge replication also enables you to filter related rows based on an existing row filter.</span></span> <span data-ttu-id="5146e-120">如需詳細資訊，請參閱 [定義和修改合併發行項之間的聯結篩選](define-and-modify-a-join-filter-between-merge-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="5146e-120">For more information, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5146e-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5146e-121">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="5146e-122">您可在 [新增發行集精靈] 的 [篩選資料表的資料列] 頁面上，或在 [發行集屬性 - \<Publication>] 對話方塊的 [篩選資料列] 頁面上，定義、修改及刪除靜態資料列篩選。</span><span class="sxs-lookup"><span data-stu-id="5146e-122">Define, modify, and delete static row filters on the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="5146e-123">如需使用精靈及存取對話方塊的詳細資訊，請參閱[建立發行集](create-a-publication.md)和[檢視及修改發行集屬性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="5146e-123">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-define-a-static-row-filter"></a><span data-ttu-id="5146e-124">若要定義靜態資料列篩選</span><span class="sxs-lookup"><span data-stu-id="5146e-124">To define a static row filter</span></span>  
  
1.  <span data-ttu-id="5146e-125">在 [新增發行集精靈] 的 [篩選資料表的資料列] 頁面上，或在 [發行集屬性 - \<Publication>] 對話方塊的 [篩選資料列] 頁面上，所採取的動作會視發行集類型而定：</span><span class="sxs-lookup"><span data-stu-id="5146e-125">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, the action you take depends on the type of publication:</span></span>  
  
    -   <span data-ttu-id="5146e-126">對於快照式或交易式發行集，請按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="5146e-126">For a snapshot or transactional publication, click **Add**.</span></span>  
  
    -   <span data-ttu-id="5146e-127">對於合併式發行集，請按一下 **[加入]** ，然後按一下 **[加入篩選]** 。</span><span class="sxs-lookup"><span data-stu-id="5146e-127">For a merge publication, click **Add**, and then click **Add Filter**.</span></span>  
  
2.  <span data-ttu-id="5146e-128">在 **[加入篩選]** 對話方塊中，從下拉式清單方塊中選取要篩選的資料表。</span><span class="sxs-lookup"><span data-stu-id="5146e-128">In the **Add Filter** dialog box, select a table to filter from the drop-down list box.</span></span>  
  
3.  <span data-ttu-id="5146e-129">在 **[篩選陳述式]** 文字區域中建立篩選陳述式。</span><span class="sxs-lookup"><span data-stu-id="5146e-129">Create a filter statement in the **Filter statement** text area.</span></span> <span data-ttu-id="5146e-130">您可直接在文字區域輸入，也可以從 **[資料行]** 清單方塊中拖曳資料行。</span><span class="sxs-lookup"><span data-stu-id="5146e-130">You can type directly in the text area, and you can also drag and drop columns from the **Columns** list box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5146e-131">WHERE 子句應使用兩部份命名；不支援三部份及四部份命名。</span><span class="sxs-lookup"><span data-stu-id="5146e-131">The WHERE clause should use two-part naming; three-part naming and four-part naming are not supported.</span></span> <span data-ttu-id="5146e-132">如果發行集來自「Oracle 發行者」，則 WHERE 子句必須與 Oracle 語法相容。</span><span class="sxs-lookup"><span data-stu-id="5146e-132">If the publication is from an Oracle Publisher, the WHERE clause must be compliant with Oracle syntax.</span></span>  
  
    -   <span data-ttu-id="5146e-133">**[篩選陳述式]** 文字區域包括預設文字，其格式為：</span><span class="sxs-lookup"><span data-stu-id="5146e-133">The **Filter statement** text area includes the default text, which is in the form of:</span></span>  
  
        ```sql  
        SELECT <published_columns> FROM [schema].[tablename] WHERE  
        ```  
  
    -   <span data-ttu-id="5146e-134">預設的文字無法變更；使用標準 SQL 語法，在 WHERE 關鍵字後面輸入篩選子句。</span><span class="sxs-lookup"><span data-stu-id="5146e-134">The default text cannot be changed; type the filter clause after the WHERE keyword using standard SQL syntax.</span></span> <span data-ttu-id="5146e-135">完整的篩選子句應類似於：</span><span class="sxs-lookup"><span data-stu-id="5146e-135">The complete filter clause would appear like:</span></span>  
  
        ```sql  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE [LoginID] = 'adventure-works\ranjit0'  
        ```  
  
    -   <span data-ttu-id="5146e-136">靜態資料列篩選可以包含使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="5146e-136">A static row filter can include a user-defined function.</span></span> <span data-ttu-id="5146e-137">含有使用者定義函數的靜態資料列篩選之完整的篩選子句應類似於：</span><span class="sxs-lookup"><span data-stu-id="5146e-137">The complete filter clause for a static row filter with a user-defined function would appear like:</span></span>  
  
        ```sql  
        SELECT <published_columns> FROM [Sales].[SalesOrderHeader] WHERE MyFunction([Freight]) > 100  
        ```  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="5146e-138">如果位於 [發行集屬性 - \<Publication>] 對話方塊中，請按一下 [確定] 以儲存並關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5146e-138">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-modify-a-static-row-filter"></a><span data-ttu-id="5146e-139">若要修改靜態資料列篩選</span><span class="sxs-lookup"><span data-stu-id="5146e-139">To modify a static row filter</span></span>  
  
1.  <span data-ttu-id="5146e-140">在 [新增發行集精靈] 的 [篩選資料表的資料列] 頁面上，或在 [發行集屬性 - \<Publication>] 對話方塊的 [篩選資料列] 頁面上，從 [已篩選的資料表] 窗格中選取一個篩選，然後按一下 [編輯]。</span><span class="sxs-lookup"><span data-stu-id="5146e-140">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, select a filter in the **Filtered Tables** pane, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="5146e-141">在 **[編輯篩選]** 對話方塊中，修改篩選。</span><span class="sxs-lookup"><span data-stu-id="5146e-141">In the **Edit Filter** dialog box, modify the filter.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-static-row-filter"></a><span data-ttu-id="5146e-142">若要刪除靜態資料列篩選</span><span class="sxs-lookup"><span data-stu-id="5146e-142">To delete a static row filter</span></span>  
  
1.  <span data-ttu-id="5146e-143">在 [新增發行集精靈] 的 [篩選資料表的資料列] 頁面上，或在 [發行集屬性 - \<Publication>] 對話方塊的 [篩選資料列] 頁面上，從 [已篩選的資料表] 窗格中選取一個篩選，然後按一下 [刪除]。</span><span class="sxs-lookup"><span data-stu-id="5146e-143">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box, select a filter in the **Filtered Tables** pane, and then click **Delete**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5146e-144">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5146e-144">Using Transact-SQL</span></span>  
 <span data-ttu-id="5146e-145">當您建立資料表發行項時，可以定義 WHERE 子句從發行項篩選資料列。</span><span class="sxs-lookup"><span data-stu-id="5146e-145">When creating table articles, you can define a WHERE clause to filter rows out of an article.</span></span> <span data-ttu-id="5146e-146">您也可以在定義資料列篩選之後，加以變更。</span><span class="sxs-lookup"><span data-stu-id="5146e-146">You can also change a row filter after it has been defined.</span></span> <span data-ttu-id="5146e-147">您可以使用複寫預存程序來以程式設計的方式建立及修改靜態資料列篩選。</span><span class="sxs-lookup"><span data-stu-id="5146e-147">Static row filters can be created and modified programmatically using replication stored procedures.</span></span>  
  
#### <a name="to-define-a-static-row-filter-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="5146e-148">為快照式或交易式發行集定義靜態資料列篩選</span><span class="sxs-lookup"><span data-stu-id="5146e-148">To define a static row filter for a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="5146e-149">定義要篩選的發行項。</span><span class="sxs-lookup"><span data-stu-id="5146e-149">Define the article to filter.</span></span> <span data-ttu-id="5146e-150">如需詳細資訊，請參閱 [定義發行項](define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="5146e-150">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
2.  <span data-ttu-id="5146e-151">在發行集資料庫的發行者端，執行 [sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5146e-151">At the Publisher on the publication database, execute [sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql).</span></span> <span data-ttu-id="5146e-152">為 **\@article** 指定發行項的名稱、為 **\@publication** 指定發行集的名稱、為 **\@filter_name** 指定篩選的名稱，並為 **\@filter_clause** (不包括 `WHERE`) 指定篩選子句。</span><span class="sxs-lookup"><span data-stu-id="5146e-152">Specify the name of the article for **\@article**, the name of the publication for **\@publication**, a name for the filter for **\@filter_name**, and the filtering clause for **\@filter_clause** (not including `WHERE`).</span></span>  
  
3.  <span data-ttu-id="5146e-153">如果仍然必須定義資料行篩選，請參閱＜ [定義及修改資料行篩選](define-and-modify-a-column-filter.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5146e-153">If a column filter must still be defined, see [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span> <span data-ttu-id="5146e-154">否則，執行 [sp_articleview &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5146e-154">Otherwise, execute [sp_articleview &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="5146e-155">為 **\@publication** 指定發行集的名稱、為 **\@article** 指定篩選的發行項名稱，並為 **\@filter_clause** 指定步驟 2 中所指定的篩選子句。</span><span class="sxs-lookup"><span data-stu-id="5146e-155">Specify the publication name for **\@publication**, the name of the filtered article for **\@article**, and the filter clause specified in step 2 for **\@filter_clause**.</span></span> <span data-ttu-id="5146e-156">這樣會針對篩選的發行項建立同步處理物件。</span><span class="sxs-lookup"><span data-stu-id="5146e-156">This creates the synchronization objects for the filtered article.</span></span>  
  
#### <a name="to-modify-a-static-row-filter-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="5146e-157">為快照式或交易式發行集修改靜態資料列篩選</span><span class="sxs-lookup"><span data-stu-id="5146e-157">To modify a static row filter for a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="5146e-158">在發行集資料庫的發行者端，執行 [sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5146e-158">At the Publisher on the publication database, execute [sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql).</span></span> <span data-ttu-id="5146e-159">為 **\@article** 指定發行項的名稱、為 **\@publication** 指定發行集的名稱、為 **\@filter_name** 指定新的篩選名稱，並為 **\@filter_clause** (不包括 `WHERE`) 指定新的篩選子句。</span><span class="sxs-lookup"><span data-stu-id="5146e-159">Specify the name of the article for **\@article**, the name of the publication for **\@publication**, a name for the new filter for **\@filter_name**, and the new filtering clause for **\@filter_clause** (not including `WHERE`).</span></span> <span data-ttu-id="5146e-160">由於這項變更將會讓現有訂閱中的資料失效，所以請為 **\@force_reinit_subscription** 指定 **1** 值。</span><span class="sxs-lookup"><span data-stu-id="5146e-160">Because this change will invalidate data in existing subscriptions, specify a value of **1** for **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="5146e-161">在發行集資料庫的發行者端，執行 [sp_articleview &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5146e-161">At the Publisher on the publication database, execute [sp_articleview &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="5146e-162">為 **\@publication** 指定發行集的名稱、為 **\@article** 指定篩選的發行項名稱，並為 **\@filter_clause** 指定步驟 1 中所指定的篩選子句。</span><span class="sxs-lookup"><span data-stu-id="5146e-162">Specify the publication name for **\@publication**, the name of the filtered article for **\@article**, and the filter clause specified in step 1 for **\@filter_clause**.</span></span> <span data-ttu-id="5146e-163">這樣會重新建立可定義篩選之發行項的檢視。</span><span class="sxs-lookup"><span data-stu-id="5146e-163">This re-creates the view that defines the filtered article.</span></span>  
  
3.  <span data-ttu-id="5146e-164">針對此發行集重新執行快照集代理程式作業，以產生更新的快照集。</span><span class="sxs-lookup"><span data-stu-id="5146e-164">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span> <span data-ttu-id="5146e-165">如需詳細資訊，請參閱 [建立和套用初始快照集](../create-and-apply-the-initial-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="5146e-165">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
4.  <span data-ttu-id="5146e-166">重新初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="5146e-166">Reinitialize subscriptions.</span></span> <span data-ttu-id="5146e-167">如需詳細資訊，請參閱 [重新初始化訂閱](../reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="5146e-167">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
#### <a name="to-delete-a-static-row-filter-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="5146e-168">為快照式或交易式發行集刪除靜態資料列篩選</span><span class="sxs-lookup"><span data-stu-id="5146e-168">To delete a static row filter for a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="5146e-169">在發行集資料庫的發行者端，執行 [sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5146e-169">At the Publisher on the publication database, execute [sp_articlefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql).</span></span> <span data-ttu-id="5146e-170">為 **\@article** 指定發行項的名稱、為 **\@publication** 指定發行集的名稱、為 **\@filter_name** 指定 NULL 的值，並為 **\@filter_clause** 指定 NULL 的值。</span><span class="sxs-lookup"><span data-stu-id="5146e-170">Specify the name of the article for **\@article**, the name of the publication for **\@publication**, a value of NULL for **\@filter_name**, and a value of NULL for **\@filter_clause**.</span></span> <span data-ttu-id="5146e-171">由於這項變更將會讓現有訂閱中的資料失效，所以請為 **\@force_reinit_subscription** 指定 **1** 值。</span><span class="sxs-lookup"><span data-stu-id="5146e-171">Because this change will invalidate data in existing subscriptions, specify a value of **1** for **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="5146e-172">針對此發行集重新執行快照集代理程式作業，以產生更新的快照集。</span><span class="sxs-lookup"><span data-stu-id="5146e-172">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span> <span data-ttu-id="5146e-173">如需詳細資訊，請參閱 [建立和套用初始快照集](../create-and-apply-the-initial-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="5146e-173">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
3.  <span data-ttu-id="5146e-174">重新初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="5146e-174">Reinitialize subscriptions.</span></span> <span data-ttu-id="5146e-175">如需詳細資訊，請參閱 [重新初始化訂閱](../reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="5146e-175">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
#### <a name="to-define-a-static-row-filter-for-a-merge-publication"></a><span data-ttu-id="5146e-176">為合併式發行集定義靜態資料列篩選</span><span class="sxs-lookup"><span data-stu-id="5146e-176">To define a static row filter for a merge publication</span></span>  
  
1.  <span data-ttu-id="5146e-177">在發行集資料庫的發行者端，執行 [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5146e-177">At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="5146e-178">為 **\@subset_filterclause** (不包括 `WHERE`) 指定篩選子句。</span><span class="sxs-lookup"><span data-stu-id="5146e-178">Specify the filtering clause for **\@subset_filterclause** (not including `WHERE`).</span></span> <span data-ttu-id="5146e-179">如需詳細資訊，請參閱 [定義發行項](define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="5146e-179">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
2.  <span data-ttu-id="5146e-180">如果仍然必須定義資料行篩選，請參閱＜ [定義及修改資料行篩選](define-and-modify-a-column-filter.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5146e-180">If a column filter must still be defined, see [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).</span></span>  
  
#### <a name="to-modify-a-static-row-filter-for-a-merge-publication"></a><span data-ttu-id="5146e-181">為合併式發行集修改靜態資料列篩選</span><span class="sxs-lookup"><span data-stu-id="5146e-181">To modify a static row filter for a merge publication</span></span>  
  
1.  <span data-ttu-id="5146e-182">在發行集資料庫的發行者端，執行 [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5146e-182">At the Publisher on the publication database, execute [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="5146e-183">為 **\@publication** 指定發行集的名稱、為 **\@article** 指定篩選的發行項名稱、為 **\@property** 指定 **subset_filterclause** 值，並為 **\@value** (不包括 `WHERE`) 指定新的篩選子句。</span><span class="sxs-lookup"><span data-stu-id="5146e-183">Specify the publication name for **\@publication**, the name of the filtered article for **\@article**, a value of **subset_filterclause** for **\@property**, and the new filtering clause for **\@value** (not including `WHERE`).</span></span> <span data-ttu-id="5146e-184">由於這項變更將會讓現有訂閱中的資料失效，所以請為 **\@force_reinit_subscription** 指定 1 值。</span><span class="sxs-lookup"><span data-stu-id="5146e-184">Because this change will invalidate data in existing subscriptions, specify a value of 1 for **\@force_reinit_subscription**.</span></span>  
  
2.  <span data-ttu-id="5146e-185">針對此發行集重新執行快照集代理程式作業，以產生更新的快照集。</span><span class="sxs-lookup"><span data-stu-id="5146e-185">Rerun the Snapshot Agent job for the publication to generate an updated snapshot.</span></span> <span data-ttu-id="5146e-186">如需詳細資訊，請參閱 [建立和套用初始快照集](../create-and-apply-the-initial-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="5146e-186">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
3.  <span data-ttu-id="5146e-187">重新初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="5146e-187">Reinitialize subscriptions.</span></span> <span data-ttu-id="5146e-188">如需詳細資訊，請參閱 [重新初始化訂閱](../reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="5146e-188">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="5146e-189">範例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5146e-189">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="5146e-190">在此異動複寫範例中，會以水平方式篩選此發行項，以移除所有不再生產的產品。</span><span class="sxs-lookup"><span data-stu-id="5146e-190">In this transactional replication example, the article is filtered horizontally to remove all discontinued products.</span></span>  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpub.sql#sp_addtranarticle)]  
  
 <span data-ttu-id="5146e-191">在此合併式複寫範例中，會以水平方式篩選發行項，以便只傳回屬於指定之銷售人員的資料列。</span><span class="sxs-lookup"><span data-stu-id="5146e-191">In this merge replication example, the articles are filtered horizontally to return only rows that belong to the specified salesperson.</span></span> <span data-ttu-id="5146e-192">也會使用聯結篩選。</span><span class="sxs-lookup"><span data-stu-id="5146e-192">A join filter is also used.</span></span> <span data-ttu-id="5146e-193">如需詳細資訊，請參閱 [定義和修改合併發行項之間的聯結篩選](define-and-modify-a-join-filter-between-merge-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="5146e-193">For more information, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
## <a name="see-also"></a><span data-ttu-id="5146e-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5146e-194">See Also</span></span>  
 <span data-ttu-id="5146e-195">[針對合併發行項定義及修改參數化資料列篩選](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span><span class="sxs-lookup"><span data-stu-id="5146e-195">[Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) </span></span>  
 <span data-ttu-id="5146e-196">[變更發行集與發行項屬性](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="5146e-196">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="5146e-197">[篩選發行的資料](filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="5146e-197">[Filter Published Data](filter-published-data.md) </span></span>  
 [<span data-ttu-id="5146e-198">合併式複寫之篩選發行資料</span><span class="sxs-lookup"><span data-stu-id="5146e-198">Filter Published Data for Merge Replication</span></span>](../merge/filter-published-data-for-merge-replication.md)  
  
  
