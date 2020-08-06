---
title: 在合併發行項之間自動產生一組聯結篩選 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- automatic join filter generation
- join filters
ms.assetid: 7ef419f4-c17f-42a5-9068-174a3ec08941
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4bfdbf93aad134e4da873a6aade307754a2637e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584388"
---
# <a name="automatically-generate-a-set-of-join-filters-between-merge-articles-sql-server-management-studio"></a><span data-ttu-id="095ac-102">在合併發行項之間自動產生一組聯結篩選 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="095ac-102">Automatically Generate a Set of Join Filters Between Merge Articles (SQL Server Management Studio)</span></span>
  <span data-ttu-id="095ac-103">您可在 [新增發行集精靈] 的 [篩選資料表的資料列] 頁面上，或在 [發行集屬性 - \<Publication>] 對話方塊的 [篩選資料列] 頁面上，自動產生一組聯結篩選。</span><span class="sxs-lookup"><span data-stu-id="095ac-103">Automatically generate a set of join filters on the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="095ac-104">如需使用精靈及存取對話方塊的詳細資訊，請參閱[建立發行集](create-a-publication.md)和[檢視及修改發行集屬性](view-and-modify-publication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="095ac-104">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="095ac-105">如果在初始化發行集的訂閱之後，在 [發行集屬性 - \<Publication>] 對話方塊中自動產生了一組聯結篩選，則必須在經過變更之後，產生一個新快照集並重新初始化所有的訂閱。</span><span class="sxs-lookup"><span data-stu-id="095ac-105">If you automatically generate a set of join filters in the **Publication Properties - \<Publication>** dialog box after subscriptions to the publication have been initialized, you must generate a new snapshot and reinitialize all subscriptions after making the change.</span></span> <span data-ttu-id="095ac-106">如需屬性變更需求的詳細資訊，請參閱[變更發行集與發行項屬性](change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="095ac-106">For more information about requirements for property changes, see [Change Publication and Article Properties](change-publication-and-article-properties.md).</span></span>  
  
 <span data-ttu-id="095ac-107">可以為一組資料表手動建立聯結篩選，或根據資料表中定義之主索引鍵關聯性的外部索引鍵，複寫可以自動產生篩選。</span><span class="sxs-lookup"><span data-stu-id="095ac-107">Join filters can be created manually for a set of tables, or replication can generate the filters automatically based on the foreign key to primary key relationships defined on the tables.</span></span> <span data-ttu-id="095ac-108">如需手動建立聯結篩選的詳細資訊，請參閱[定義和修改合併發行項之間的聯結篩選](define-and-modify-a-join-filter-between-merge-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="095ac-108">For more information about creating join filters manually, see [Define and Modify a Join Filter Between Merge Articles](define-and-modify-a-join-filter-between-merge-articles.md).</span></span>  
  
### <a name="to-automatically-generate-a-set-of-join-filters-between-merge-articles"></a><span data-ttu-id="095ac-109">若要在合併發行項之間自動產生一組聯結篩選</span><span class="sxs-lookup"><span data-stu-id="095ac-109">To automatically generate a set of join filters between merge articles</span></span>  
  
1.  <span data-ttu-id="095ac-110">在 [新增發行集精靈] 的 [篩選資料表的資料列] 頁面上，或在 [發行集屬性 - \<Publication>] 的 [篩選資料列] 頁面上，按一下 [新增]，然後按一下 [自動產生篩選]。</span><span class="sxs-lookup"><span data-stu-id="095ac-110">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, click **Add**, and then click **Automatically Generate Filters**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="095ac-111">自動產生篩選會刪除發行集中任何現有的資料列篩選或聯結篩選。</span><span class="sxs-lookup"><span data-stu-id="095ac-111">Automatically generating filters deletes any existing row filters or join filters in the publication.</span></span> <span data-ttu-id="095ac-112">您可以在自動產生一組篩選之後加入篩選。</span><span class="sxs-lookup"><span data-stu-id="095ac-112">You can add filters after automatically generating a set of filters.</span></span>  
  
2.  <span data-ttu-id="095ac-113">遵循 **[產生篩選]** 對話方塊中的處理建立資料列篩選。</span><span class="sxs-lookup"><span data-stu-id="095ac-113">Follow the process in the **Generate Filters** dialog box to create a row filter.</span></span> <span data-ttu-id="095ac-114">資料列篩選隨後會透過主索引鍵和外部索引鍵的關聯性擴充到與已篩選資料表相關的資料表。</span><span class="sxs-lookup"><span data-stu-id="095ac-114">The row filter is then extended to the tables related to the filtered table through primary key and foreign key relationships.</span></span>  
  
    1.  <span data-ttu-id="095ac-115">從下拉式清單方塊中選取要篩選的資料表。</span><span class="sxs-lookup"><span data-stu-id="095ac-115">Select a table to filter from the drop-down list box.</span></span>  
  
    2.  <span data-ttu-id="095ac-116">在 **[篩選陳述式]** 文字方塊中建立篩選陳述式。</span><span class="sxs-lookup"><span data-stu-id="095ac-116">Create a filter statement in the **Filter statement** text box.</span></span> <span data-ttu-id="095ac-117">您可直接在文字區域輸入，也可以從 **[資料行]** 清單方塊中拖曳資料行。</span><span class="sxs-lookup"><span data-stu-id="095ac-117">You can type directly in the text area, and you can also drag and drop columns from the **Columns** list box.</span></span>  
  
         <span data-ttu-id="095ac-118">**[篩選陳述式]** 文字區域包括預設文字，其格式為：</span><span class="sxs-lookup"><span data-stu-id="095ac-118">The **Filter statement** text area includes the default text, which is in the form of:</span></span>  
  
        ```  
        SELECT <published_columns> FROM [tableowner].[tablename] WHERE  
        ```  
  
         <span data-ttu-id="095ac-119">預設文字無法變更；使用標準 SQL 語法在 WHERE 關鍵字之後，為靜態資料列篩選或參數化資料列篩選器輸入篩選子句。</span><span class="sxs-lookup"><span data-stu-id="095ac-119">The default text cannot be changed; type the filter clause for a static row filter or a parameterized row filter after the WHERE keyword using standard SQL syntax.</span></span> <span data-ttu-id="095ac-120">參數化資料列篩選器的完整篩選子句類似於：</span><span class="sxs-lookup"><span data-stu-id="095ac-120">The complete filter clause for a parameterized row filter would look like:</span></span>  
  
        ```  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE LoginID = SUSER_SNAME()  
        ```  
  
         <span data-ttu-id="095ac-121">WHERE 子句應使用兩部份命名；不支援三部份及四部份命名。</span><span class="sxs-lookup"><span data-stu-id="095ac-121">The WHERE clause should use two-part naming; three-part naming and four-part naming are not supported.</span></span>  
  
    3.  <span data-ttu-id="095ac-122">指定篩選選項。</span><span class="sxs-lookup"><span data-stu-id="095ac-122">Specify filter options.</span></span>  
  
         <span data-ttu-id="095ac-123">選取符合資料在訂閱者之間共用資料方式的選項：[這個資料表中的一個資料列會提供給多個訂閱] 或 [這個資料表中的一個資料列只會提供給一個訂閱]。</span><span class="sxs-lookup"><span data-stu-id="095ac-123">Select the option that matches how data will be shared among Subscribers: **A row from this table will go to multiple subscriptions** or **A row from this table will go to only one subscription**.</span></span> <span data-ttu-id="095ac-124">若您選取 **[這個資料表中的一個資料列只會提供給一個訂閱]** ，合併式複寫可藉由儲存和處理較少中繼資料來將效能最佳化。</span><span class="sxs-lookup"><span data-stu-id="095ac-124">If you select **A row from this table will go to only one subscription**, merge replication can optimize performance by storing and processing less metadata.</span></span> <span data-ttu-id="095ac-125">不過您必須確定資料分割方式不會將資料列複寫至多個訂閱者。</span><span class="sxs-lookup"><span data-stu-id="095ac-125">However, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber.</span></span> <span data-ttu-id="095ac-126">如需進一步資訊，請參閱主題＜ [參數化資料列篩選器](../merge/parameterized-filters-parameterized-row-filters.md)＞中的「設定資料分割選項」。</span><span class="sxs-lookup"><span data-stu-id="095ac-126">For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="095ac-127">您指定的篩選會被剖析，並會針對 SELECT 子句中的資料表執行。</span><span class="sxs-lookup"><span data-stu-id="095ac-127">The filter you specified is parsed and run against the table in the SELECT clause.</span></span> <span data-ttu-id="095ac-128">如果篩選陳述式包含語法錯誤或其他問題，則系統會通知您，然後您可以編輯該篩選陳述式。</span><span class="sxs-lookup"><span data-stu-id="095ac-128">If the filter statement contains syntax errors or other problems, you will be notified and will be able to edit the filter statement.</span></span>  
  
     <span data-ttu-id="095ac-129">剖析陳述式之後，複寫會建立必要的聯結篩選，並在 **[篩選資料表的資料列]** 或 **[篩選資料列]** 頁面上的 **[已篩選的資料表]** 窗格中顯示它們。</span><span class="sxs-lookup"><span data-stu-id="095ac-129">After the statement is parsed, replication creates the necessary join filters and displays them in the **Filtered Tables** pane on the **Filter Table Rows** or **Filter Rows** page.</span></span> <span data-ttu-id="095ac-130">如果您從「新增發行集精靈」產生篩選，且尚未針對此精靈執行的「發行者」設定「散發者」，您會被提示要進行設定。</span><span class="sxs-lookup"><span data-stu-id="095ac-130">If you are generating filters from the New Publication Wizard and have not yet configured the Distributor for the Publisher against which this wizard is running, you are prompted to configure it.</span></span>  
  
4.  <span data-ttu-id="095ac-131">如果位於 [發行集屬性 - \<Publication>] 對話方塊中，請按一下 [確定] 以儲存並關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="095ac-131">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
### <a name="to-modify-a-filter-that-was-automatically-generated"></a><span data-ttu-id="095ac-132">若要修改自動產生的篩選</span><span class="sxs-lookup"><span data-stu-id="095ac-132">To modify a filter that was automatically generated</span></span>  
  
1.  <span data-ttu-id="095ac-133">在 [新增發行集精靈] 的 [篩選資料表的資料列] 頁面上，或在 [發行集屬性 - \<Publication>] 的 [篩選資料列] 頁面上，從 [已篩選的資料表] 窗格中選取一個篩選，然後按一下 [編輯]。</span><span class="sxs-lookup"><span data-stu-id="095ac-133">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Edit**.</span></span>  
  
2.  <span data-ttu-id="095ac-134">在 **[編輯篩選]** 或 **[編輯聯結]** 對話方塊中修改篩選。</span><span class="sxs-lookup"><span data-stu-id="095ac-134">In the **Edit Filter** or **Edit Join** dialog box, modify the filter.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-filter-that-was-automatically-generated"></a><span data-ttu-id="095ac-135">若要刪除自動產生的篩選</span><span class="sxs-lookup"><span data-stu-id="095ac-135">To delete a filter that was automatically generated</span></span>  
  
1.  <span data-ttu-id="095ac-136">在 [新增發行集精靈] 的 [篩選資料表的資料列] 頁面上，或在 [發行集屬性 - \<Publication>] 的 [篩選資料列] 頁面上，從 [已篩選的資料表] 窗格中選取一個篩選，然後按一下 [刪除]。</span><span class="sxs-lookup"><span data-stu-id="095ac-136">On the **Filter Table Rows** page of the New Publication Wizard or the **Filter Rows** page of the **Publication Properties - \<Publication>**, select a filter in the **Filtered Tables** pane, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="095ac-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="095ac-137">See Also</span></span>  
 <span data-ttu-id="095ac-138">[Join Filters](../merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="095ac-138">[Join Filters](../merge/join-filters.md) </span></span>  
 [<span data-ttu-id="095ac-139">參數化資料列篩選器</span><span class="sxs-lookup"><span data-stu-id="095ac-139">Parameterized Row Filters</span></span>](../merge/parameterized-filters-parameterized-row-filters.md)  
  
  
