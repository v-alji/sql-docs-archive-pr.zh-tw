---
title: 定義和修改合併發行項之間的聯結篩選| Microsoft 文件
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server replication], join
- merge replication join filters [SQL Server replication]
- modifying filters, join
- join filters
ms.assetid: f7f23415-43ff-40f5-b3e0-0be1d148ee5b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0770a17ce4c50c9c0e3b8728db85c0f9e80b555b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606757"
---
# <a name="define-and-modify-a-join-filter-between-merge-articles"></a><span data-ttu-id="2e18e-102">定義和修改合併發行項之間的聯結篩選</span><span class="sxs-lookup"><span data-stu-id="2e18e-102">Define and Modify a Join Filter Between Merge Articles</span></span>
  <span data-ttu-id="2e18e-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中定義及修改合併發行項之間的聯結篩選。</span><span class="sxs-lookup"><span data-stu-id="2e18e-103">This topic describes how to define and modify a join filter between merge articles in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="2e18e-104">合併式複寫支援聯結篩選，聯結篩選通常會配合參數化篩選一起使用，以將資料表資料分割擴充到其他相關的資料表發行項。</span><span class="sxs-lookup"><span data-stu-id="2e18e-104">Merge replication supports join filters, which are typically used in conjunction with parameterized filters to extend table partitioning to other related table articles.</span></span>  
  
 <span data-ttu-id="2e18e-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="2e18e-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2e18e-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="2e18e-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2e18e-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="2e18e-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2e18e-108">建議</span><span class="sxs-lookup"><span data-stu-id="2e18e-108">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="2e18e-109">**若要定義和修改合併發行項之間的聯結篩選，請使用：**</span><span class="sxs-lookup"><span data-stu-id="2e18e-109">**To define and modify a join filter between merge articles, using:**</span></span>  
  
     [<span data-ttu-id="2e18e-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2e18e-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2e18e-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2e18e-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2e18e-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="2e18e-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2e18e-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="2e18e-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="2e18e-114">若要建立聯結篩選，發行集至少必須包含兩個相關的資料表。</span><span class="sxs-lookup"><span data-stu-id="2e18e-114">To create a join filter, a publication must contain at least two related tables.</span></span> <span data-ttu-id="2e18e-115">聯結篩選會擴充資料列篩選；因此您必須先定義一個資料表上的資料列篩選，然後才可利用聯結在另一個資料表上擴充篩選。</span><span class="sxs-lookup"><span data-stu-id="2e18e-115">A join filter extends a row filter; therefore you must define a row filter on one table before you can extend the filter with a join to another table.</span></span> <span data-ttu-id="2e18e-116">定義好一個聯結篩選後，如果發行集包含其他相關資料表，您可以用另一個聯結篩選擴充這個聯結篩選。</span><span class="sxs-lookup"><span data-stu-id="2e18e-116">After one join filter is defined, you can extend this join filter with another join filter if the publication contains additional related tables.</span></span>  
  
-   <span data-ttu-id="2e18e-117">如果您在初始化發行集的訂閱後，新增、修改或刪除聯結篩選，則必須在進行變更後產生新的快照集並重新初始化所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="2e18e-117">If you add, modify, or delete a join filter after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="2e18e-118">如需屬性變更需求的詳細資訊，請參閱[變更發行集與發行項屬性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2e18e-118">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="2e18e-119">建議</span><span class="sxs-lookup"><span data-stu-id="2e18e-119">Recommendations</span></span>  
  
-   <span data-ttu-id="2e18e-120">可以為一組資料表手動建立聯結篩選，或者根據資料表中定義的外部索引鍵與主索引鍵之間的關聯性自動產生篩選。</span><span class="sxs-lookup"><span data-stu-id="2e18e-120">Join filters can be created manually for a set of tables, or replication can generate the filters automatically based on the relationships between foreign keys and primary keys defined on the tables.</span></span> <span data-ttu-id="2e18e-121">如需自動產生一組聯結篩選的詳細資訊，請參閱[在合併發行項之間自動產生一組聯結篩選 &#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="2e18e-121">For more information on generating a set of join filters automatically, see [Automatically Generate a Set of Join Filters Between Merge Articles &#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2e18e-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2e18e-122">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="2e18e-123">您可以在 [新增發行集] 精靈的 [篩選資料表的資料列] 頁面上，或是在 [發行集屬性 - \<Publication>] 對話方塊的 [篩選資料列] 頁面上，定義、修改及刪除聯結篩選。</span><span class="sxs-lookup"><span data-stu-id="2e18e-123">Define, modify, and delete join filters on the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="2e18e-124">如需使用精靈及存取對話方塊的詳細資訊，請參閱[建立發行集](create-a-publication.md)和[檢視及修改發行集屬性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2e18e-124">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-define-a-join-filter"></a><span data-ttu-id="2e18e-125">若要定義聯結篩選</span><span class="sxs-lookup"><span data-stu-id="2e18e-125">To define a join filter</span></span>  
  
1.  <span data-ttu-id="2e18e-126">在 [新增發行集] 精靈的 [篩選資料表的資料列] 頁面上，或是在 [發行集屬性 - \<Publication>] 對話方塊的 [篩選資料列] 頁面上，從 [已篩選的資料表] 窗格中選取一個現有的資料列篩選或聯結篩選。</span><span class="sxs-lookup"><span data-stu-id="2e18e-126">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select an existing row filter or join filter in the **Filtered Tables** pane.</span></span>  
  
2.  <span data-ttu-id="2e18e-127">按一下 **[加入]** ，然後按一下 **[加入聯結以擴充選取的篩選]** 。</span><span class="sxs-lookup"><span data-stu-id="2e18e-127">Click **Add**, and then click **Add Join to Extend the Selected Filter**.</span></span>  
  
3.  <span data-ttu-id="2e18e-128">建立聯結陳述式：選取 [使用產生器建立陳述式]  或 [手動寫入 join 陳述式] 。</span><span class="sxs-lookup"><span data-stu-id="2e18e-128">Create the join statement: select either **Use the builder to create the statement** or **Write the join the statement manually**.</span></span>  
  
    -   <span data-ttu-id="2e18e-129">如果選取使用產生器，請使用方格中的資料行 ([結合]、[已篩選的資料表資料行] 、[運算子] 和 [聯結的資料表資料行] ) 來建立聯結陳述式。</span><span class="sxs-lookup"><span data-stu-id="2e18e-129">If you select to use the builder, use the columns in the grid (**Conjunction**, **Filtered table column**, **Operator**, and **Joined table column**) to build a join statement.</span></span>  
  
         <span data-ttu-id="2e18e-130">方格中的每個資料行都包含下拉式方塊，可讓您選取兩個資料行和一個運算子 ( **=** 、 **<>** 、 **<=** 、 **\<**, **>=** 、 **>** ，以及 **like**)。</span><span class="sxs-lookup"><span data-stu-id="2e18e-130">Each column in the grid contains a drop-down combo box, allowing you to select two columns and an operator (**=**, **<>**, **<=**, **\<**, **>=**, **>**, and **like**).</span></span> <span data-ttu-id="2e18e-131">結果會在 **[預覽]** 文字區域中顯示。</span><span class="sxs-lookup"><span data-stu-id="2e18e-131">The results are displayed in the **Preview** text area.</span></span> <span data-ttu-id="2e18e-132">如果聯結涉及多對資料行，請從 **[結合]** 資料行中選取一個結合 (AND 或 OR)，然後輸入兩個或更多的資料行及一個運算子。</span><span class="sxs-lookup"><span data-stu-id="2e18e-132">If the join involves more than one pair of columns, select a conjunction (AND or OR) from the **Conjunction** column, and then enter two more columns and an operator.</span></span>  
  
    -   <span data-ttu-id="2e18e-133">如果選取手動寫入陳述式，請在 **[聯結陳述式]** 文字區域寫入聯結陳述式。</span><span class="sxs-lookup"><span data-stu-id="2e18e-133">If you select to write the statement manually, write the join statement in the **Join statement** text area.</span></span> <span data-ttu-id="2e18e-134">使用 **[已篩選的資料表資料行]** 清單方塊與 **[聯結的資料表資料行]** 清單方塊將資料行拖放到 **[Join 陳述式]** 文字區域。</span><span class="sxs-lookup"><span data-stu-id="2e18e-134">Use the **Filtered table columns** list box and the **Joined table columns** list box to drag and drop columns to the **Join statement** text area.</span></span>  
  
    -   <span data-ttu-id="2e18e-135">完整的聯結陳述式應類似於：</span><span class="sxs-lookup"><span data-stu-id="2e18e-135">The complete join statement would appear like:</span></span>  
  
        ```  
        SELECT <published_columns> FROM [Sales].[SalesOrderHeader] INNER JOIN [Sales].[SalesOrderDetail] ON [SalesOrderHeader].[SalesOrderID] = [SalesOrderDetail].[SalesOrderID]  
        ```  
  
         <span data-ttu-id="2e18e-136">JOIN 子句應該使用兩段式命名；不支援三段式和四段式命名。</span><span class="sxs-lookup"><span data-stu-id="2e18e-136">The JOIN clause should use two-part naming; three-part naming and four-part naming are not supported.</span></span>  
  
4.  <span data-ttu-id="2e18e-137">指定聯結選項：</span><span class="sxs-lookup"><span data-stu-id="2e18e-137">Specify join options:</span></span>  
  
    -   <span data-ttu-id="2e18e-138">如果在篩選的資料表 (父系資料表) 中聯結的資料行是唯一的，請選擇 **[唯一索引鍵]** 。</span><span class="sxs-lookup"><span data-stu-id="2e18e-138">If the column on which you join in the filtered table (the parent table) is unique, select **Unique key**.</span></span>  
  
        > [!CAUTION]  
        >  <span data-ttu-id="2e18e-139">選取此選項表示聯結篩選中的子資料表與父資料表之間的關聯性是一對一或一對多。</span><span class="sxs-lookup"><span data-stu-id="2e18e-139">Selecting this option indicates that the relationship between the child and parent tables in a join filter is one to one or one to many.</span></span> <span data-ttu-id="2e18e-140">如果在子系資料表中的聯結資料行有保證唯一性的條件約束，請僅選取此選項。</span><span class="sxs-lookup"><span data-stu-id="2e18e-140">Only select this option if you have a constraint on the joining column in the child table that guarantees uniqueness.</span></span> <span data-ttu-id="2e18e-141">如果選項設定不正確，則資料可能發生非聚合的情況。</span><span class="sxs-lookup"><span data-stu-id="2e18e-141">If the option is set incorrectly, non-convergence of data can occur.</span></span>  
  
    -   <span data-ttu-id="2e18e-142">依預設，合併式複寫在同步處理過程中會按逐個資料列的方式處理變更。</span><span class="sxs-lookup"><span data-stu-id="2e18e-142">By default, merge replication processes changes on a row-by-row basis during synchronization.</span></span> <span data-ttu-id="2e18e-143">若要將篩選資料表及聯結資料表之資料列中的相關變更作為一個單位進行處理，請選取 [邏輯記錄] \([!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 及更新版本\)。</span><span class="sxs-lookup"><span data-stu-id="2e18e-143">To have related changes in rows of both the filtered table and the joined table processed as a unit, select **Logical record** ([!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] and later versions only).</span></span> <span data-ttu-id="2e18e-144">只有當發行項與發行集之使用邏輯記錄的需求均符合時，才可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="2e18e-144">This option is available only if the article and publication requirements for using logical records are met.</span></span> <span data-ttu-id="2e18e-145">如需詳細資訊，請參閱[使用邏輯記錄分組相關資料列的變更](../merge/group-changes-to-related-rows-with-logical-records.md)中的＜使用邏輯記錄的考量＞一節。</span><span class="sxs-lookup"><span data-stu-id="2e18e-145">For more information see the section "Considerations for Using Logical Records" in [Group Changes to Related Rows with Logical Records](../merge/group-changes-to-related-rows-with-logical-records.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="2e18e-146">如果您位於 [發行集屬性 - \<Publication>] 對話方塊中，請按一下 [確定] 以儲存並關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2e18e-146">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
#### <a name="to-modify-a-join-filter"></a><span data-ttu-id="2e18e-147">若要修改聯結篩選</span><span class="sxs-lookup"><span data-stu-id="2e18e-147">To modify a join filter</span></span>  
  
1.  <span data-ttu-id="2e18e-148">在 [新增發行集] 精靈的 [篩選資料表的資料列] 頁面上，或是在 [發行集屬性 - \<Publication>] 的 [篩選資料列] 頁面上，從 [已篩選的資料表] 窗格中選取一個篩選，然後按一下 [編輯]。</span><span class="sxs-lookup"><span data-stu-id="2e18e-148">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="2e18e-149">在 **[編輯聯結]** 對話方塊中，修改篩選。</span><span class="sxs-lookup"><span data-stu-id="2e18e-149">In the **Edit Join** dialog box, modify the filter.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-join-filter"></a><span data-ttu-id="2e18e-150">若要刪除聯結篩選</span><span class="sxs-lookup"><span data-stu-id="2e18e-150">To delete a join filter</span></span>  
  
1.  <span data-ttu-id="2e18e-151">在 [新增發行集] 精靈的 [篩選資料表的資料列] 頁面上，或是在 [發行集屬性 - \<Publication>] 的 [篩選資料列] 頁面上，從 [已篩選的資料表] 窗格中選取一個篩選，然後按一下 [刪除]。</span><span class="sxs-lookup"><span data-stu-id="2e18e-151">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Delete**.</span></span> <span data-ttu-id="2e18e-152">如果您刪除的聯結篩選本身已由其他聯結擴充，也會一併刪除這些聯結。</span><span class="sxs-lookup"><span data-stu-id="2e18e-152">If the join filter you delete is itself extended by other joins, those joins will also be deleted.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2e18e-153">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2e18e-153">Using Transact-SQL</span></span>  
 <span data-ttu-id="2e18e-154">這些程序顯示父發行項上的參數化篩選，其中包含此發行項與相關子發行項之間的聯結篩選。</span><span class="sxs-lookup"><span data-stu-id="2e18e-154">These procedures show a parameterized filter on a parent article with join filters between this article and related child articles.</span></span> <span data-ttu-id="2e18e-155">您可以使用複寫預存程序來以程式設計的方式定義及修改聯結篩選。</span><span class="sxs-lookup"><span data-stu-id="2e18e-155">Join filters can be defined and modified programmatically using replication stored procedures.</span></span>  
  
#### <a name="to-define-a-join-filter-to-extend-an-article-filter-to-related-articles-in-a-merge-publication"></a><span data-ttu-id="2e18e-156">定義聯結篩選，將發行項擴充到合併式發行集中的相關發行項</span><span class="sxs-lookup"><span data-stu-id="2e18e-156">To define a join filter to extend an article filter to related articles in a merge publication</span></span>  
  
1.  <span data-ttu-id="2e18e-157">針對聯結的發行項定義篩選，此發行項也稱為父發行項。</span><span class="sxs-lookup"><span data-stu-id="2e18e-157">Define the filtering for the article being joined to, which is also known as the parent article.</span></span>  
  
    -   <span data-ttu-id="2e18e-158">如需使用參數化資料列篩選器篩選的發行項，請參閱＜ [針對合併發行項定義及修改參數化資料列篩選](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)＞。</span><span class="sxs-lookup"><span data-stu-id="2e18e-158">For an article filtered using a parameterized row filter, see [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).</span></span>  
  
    -   <span data-ttu-id="2e18e-159">如需使用靜態資料列篩選進行篩選的發行項，請參閱＜ [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)＞。</span><span class="sxs-lookup"><span data-stu-id="2e18e-159">For an article filtered using a static row filter, see [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).</span></span>  
  
2.  <span data-ttu-id="2e18e-160">在發行集資料庫的發行者端，執行 [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) 來針對發行集定義一個或多個相關發行項，這些發行項也稱為子發行項。</span><span class="sxs-lookup"><span data-stu-id="2e18e-160">At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) to define one or more related articles, which are also known as child articles, for the publication.</span></span> <span data-ttu-id="2e18e-161">如需詳細資訊，請參閱 [定義發行項](define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="2e18e-161">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
3.  <span data-ttu-id="2e18e-162">在發行集資料庫的發行者端，執行 [sp_addmergefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2e18e-162">At the Publisher on the publication database, execute [sp_addmergefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql).</span></span> <span data-ttu-id="2e18e-163">針對指定 **@publication** 此篩選的唯一名稱、針對指定 **@filtername** 步驟2中建立的子發行項名稱、針對 **@article** 指定聯結的父發行項名稱， **@join_articlename** 並針對下列其中一個值 **@join_unique_key** ：</span><span class="sxs-lookup"><span data-stu-id="2e18e-163">Specify **@publication**, a unique name for this filter for **@filtername**, the name of the child article created in step 2 for **@article**, the name of the parent article being joined to for **@join_articlename**, and one of the following values for **@join_unique_key**:</span></span>  
  
    -   <span data-ttu-id="2e18e-164">**0** - 指示父發行項與子發行項之間的多對一或多對多的聯結。</span><span class="sxs-lookup"><span data-stu-id="2e18e-164">**0** - indicates a many-to-one or many-to-many join between the parent and child articles.</span></span>  
  
    -   <span data-ttu-id="2e18e-165">**1** - 指示父發行項與子發行項之間的一對一或一對多的聯結。</span><span class="sxs-lookup"><span data-stu-id="2e18e-165">**1** - indicates a one-to-one or one-to-many join between the parent and child articles.</span></span>  
  
     <span data-ttu-id="2e18e-166">這樣會定義兩個發行項之間的聯結篩選。</span><span class="sxs-lookup"><span data-stu-id="2e18e-166">This defines a join filter between the two articles.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="2e18e-167">只有在 **@join_unique_key** 保證唯一性的父發行項之基礎資料表中的聯結資料行上有條件約束時，才會設定為**1** 。</span><span class="sxs-lookup"><span data-stu-id="2e18e-167">Only set **@join_unique_key** to **1** if you have a constraint on the joining column in the underlying table for the parent article that guarantees uniqueness.</span></span> <span data-ttu-id="2e18e-168">如果 **@join_unique_key** 未正確設定為**1** ，可能會發生非聚合的資料。</span><span class="sxs-lookup"><span data-stu-id="2e18e-168">If **@join_unique_key** is set to **1** incorrectly, non-convergence of data may occur.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="2e18e-169">範例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2e18e-169">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="2e18e-170">這個範例會針對合併式發行集定義發行項，其中會針對 `SalesOrderDetail` 資料表篩選 `SalesOrderHeader` 資料表發行項 (前者資料表本身會使用靜態資料列篩選來進行篩選)。</span><span class="sxs-lookup"><span data-stu-id="2e18e-170">This example defines an article for a merge publication, where the `SalesOrderDetail` table article is filtered against the `SalesOrderHeader` table that is itself filtered using a static row filter.</span></span> <span data-ttu-id="2e18e-171">如需詳細資訊，請參閱 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)。</span><span class="sxs-lookup"><span data-stu-id="2e18e-171">For more information, see [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).</span></span>  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
 <span data-ttu-id="2e18e-172">此範例會在合併式發行集中定義一組發行項，其中的發行項會使用一系列的聯結篩選來針對 `Employee` 資料表進行篩選 (此資料表本身是使用 [LoginID](/sql/t-sql/functions/host-name-transact-sql) 資料行中 **HOST_NAME** 值上的參數化資料列篩選來進行篩選)。</span><span class="sxs-lookup"><span data-stu-id="2e18e-172">This example defines a group of articles in a merge publication where the articles are filtered with a series of join filters against the `Employee` table that is itself filtered using a parameterized row filter on the value of [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql) in the **LoginID** column.</span></span> <span data-ttu-id="2e18e-173">如需詳細資訊，請參閱 [針對合併發行項定義及修改參數化資料列篩選](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)。</span><span class="sxs-lookup"><span data-stu-id="2e18e-173">For more information, see [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).</span></span>  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubdynamic1.sql#sp_mergedynamicpub1)]  
  
## <a name="see-also"></a><span data-ttu-id="2e18e-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e18e-174">See Also</span></span>  
 <span data-ttu-id="2e18e-175">[Join Filters](../merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="2e18e-175">[Join Filters](../merge/join-filters.md) </span></span>  
 <span data-ttu-id="2e18e-176">[Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="2e18e-176">[Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 <span data-ttu-id="2e18e-177">[變更發行集與發行項屬性](change-publication-and-article-properties.md) </span><span class="sxs-lookup"><span data-stu-id="2e18e-177">[Change Publication and Article Properties](change-publication-and-article-properties.md) </span></span>  
 <span data-ttu-id="2e18e-178">[針對合併式複寫篩選發行的資料](../merge/filter-published-data-for-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="2e18e-178">[Filter Published Data for Merge Replication](../merge/filter-published-data-for-merge-replication.md) </span></span>  
 <span data-ttu-id="2e18e-179">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="2e18e-179">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 <span data-ttu-id="2e18e-180">[定義合併資料表發行項之間的邏輯記錄關聯性](define-a-logical-record-relationship-between-merge-table-articles.md) </span><span class="sxs-lookup"><span data-stu-id="2e18e-180">[Define a Logical Record Relationship Between Merge Table Articles](define-a-logical-record-relationship-between-merge-table-articles.md) </span></span>  
 [<span data-ttu-id="2e18e-181">針對合併發行項定義及修改參數化資料列篩選</span><span class="sxs-lookup"><span data-stu-id="2e18e-181">Define and Modify a Parameterized Row Filter for a Merge Article</span></span>](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)  
  
  
