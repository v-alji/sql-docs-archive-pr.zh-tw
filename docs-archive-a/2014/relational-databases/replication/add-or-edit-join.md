---
title: 新增或編輯聯結 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.addeditjoin.f1
ms.assetid: 3b546560-720f-48b8-9d63-cf159290e9d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e3e17b084a232375734601b515821273d482fcd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591964"
---
# <a name="add-or-edit-join"></a><span data-ttu-id="464cc-102">加入或編輯聯結</span><span class="sxs-lookup"><span data-stu-id="464cc-102">Add or Edit Join</span></span>
  <span data-ttu-id="464cc-103">**[加入聯結]** 和 **[編輯聯結]** 對話方塊可讓您為合併發行集加入和編輯聯結篩選。</span><span class="sxs-lookup"><span data-stu-id="464cc-103">The **Add Join** and **Edit Join** dialog boxes allow you to add and edit join filters for merge publications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="464cc-104">編輯現有發行集內的篩選需要該發行集的新快照集。</span><span class="sxs-lookup"><span data-stu-id="464cc-104">Editing a filter in an existing publication requires a new snapshot for the publication.</span></span> <span data-ttu-id="464cc-105">如果發行集有訂閱，就必須重新初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="464cc-105">If a publication has subscriptions, the subscriptions must be reinitialized.</span></span> <span data-ttu-id="464cc-106">如需屬性變更的詳細資訊，請參閱[變更發行集與發行項屬性](publish/change-publication-and-article-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="464cc-106">For more information about property changes, see [Change Publication and Article Properties](publish/change-publication-and-article-properties.md).</span></span>  
  
 <span data-ttu-id="464cc-107">聯結篩選可讓您根據發行集內相關資料表的篩選方式來篩選資料表。</span><span class="sxs-lookup"><span data-stu-id="464cc-107">A join filter allows a table to be filtered based on how a related table in the publication is filtered.</span></span> <span data-ttu-id="464cc-108">通常，父資料表會使用參數化資料列篩選器進行篩選，然後一個或多個聯結篩選會以您在資料表之間定義聯結的相同方式進行定義。</span><span class="sxs-lookup"><span data-stu-id="464cc-108">Typically a parent table is filtered using a parameterized row filter; then one or more join filters are defined in much the same way that you define a join between tables.</span></span> <span data-ttu-id="464cc-109">聯結篩選會擴充資料列篩選，以便只有當資料與聯結篩選子句相符時，才複寫相關資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="464cc-109">The join filters extend the row filter so that the data in the related tables is replicated only if it matches the join filter clause.</span></span>  
  
 <span data-ttu-id="464cc-110">聯結篩選通常會遵循為套用到之資料表所定義的主索引鍵/外部索引鍵關聯性，但並非嚴格受限於主索引鍵/外部索引鍵關聯性。</span><span class="sxs-lookup"><span data-stu-id="464cc-110">Join filters typically follow the primary key/foreign key relationships defined for the tables to which they are applied, but they are not limited strictly to primary key/foreign key relationships.</span></span> <span data-ttu-id="464cc-111">聯結篩選可以根據任何比較兩個發行項資料表中之相關資料的邏輯。</span><span class="sxs-lookup"><span data-stu-id="464cc-111">The join filter can be based on any logic that compares related data in two article tables.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="464cc-112">聯結篩選可以包含無限數量的資料表，但如果篩選的資料表數量過多，會影響合併處理過程中的效能。</span><span class="sxs-lookup"><span data-stu-id="464cc-112">Join Filters can involve an unlimited number of tables, but filters with a large number of tables can impact performance during merge processing.</span></span> <span data-ttu-id="464cc-113">若您正在產生五個以上資料表的聯結篩選，請考慮其他方案：不要篩選小型、無法變更或主要為查詢資料表的資料表。</span><span class="sxs-lookup"><span data-stu-id="464cc-113">If you are generating join filters of five or more tables, consider other solutions: do not filter tables that are small, not subject to change, or are primarily lookup tables.</span></span> <span data-ttu-id="464cc-114">聯結篩選只能用於必須在訂閱者中分割的資料表之間。</span><span class="sxs-lookup"><span data-stu-id="464cc-114">Use join filters only between tables that must be partitioned among Subscribers.</span></span>  
  
## <a name="options"></a><span data-ttu-id="464cc-115">選項。</span><span class="sxs-lookup"><span data-stu-id="464cc-115">Options</span></span>  
 <span data-ttu-id="464cc-116">這個對話方塊包括三個步驟的處理程序，以在兩個資料表之間建立一個聯結篩選。</span><span class="sxs-lookup"><span data-stu-id="464cc-116">This dialog box involves a three-step process to create a join filter between two tables.</span></span> <span data-ttu-id="464cc-117">若要建立一個以上的聯結篩選，就必須執行此對話方塊一次以上。</span><span class="sxs-lookup"><span data-stu-id="464cc-117">Creating more than one join filter requires more than one pass through the dialog box.</span></span>  
  
1.  <span data-ttu-id="464cc-118">**確認已篩選的資料表並選取聯結的資料表**</span><span class="sxs-lookup"><span data-stu-id="464cc-118">**Verify filtered table and select the joined table**</span></span>  
  
    -   <span data-ttu-id="464cc-119">如果您正在加入新聯結，請確認 **[已篩選的資料表]** 文字方塊中的資料表是正確的 (如果不正確，請按一下 **[取消]** ，在 **[篩選資料表的資料列]** 頁面上選取正確的資料表，然後按一下 **[加入聯結]** 即可回到此對話方塊)。</span><span class="sxs-lookup"><span data-stu-id="464cc-119">If you are adding a new join, verify that the table in the **Filtered table** text box is correct (if it is not correct, click **Cancel**, select the correct table on the **Filter Table Rows** page, and click **Add Join** to return to this dialog box).</span></span> <span data-ttu-id="464cc-120">接著，從 **[聯結的資料表]** 下拉式清單方塊中選取資料表。</span><span class="sxs-lookup"><span data-stu-id="464cc-120">Then select a table from the **Joined table** drop-down list box.</span></span>  
  
    -   <span data-ttu-id="464cc-121">如果是編輯現有的聯結，則資料表名稱已經指定且無法變更。</span><span class="sxs-lookup"><span data-stu-id="464cc-121">If you are editing an existing join, the table names will be specified already and cannot be changed.</span></span> <span data-ttu-id="464cc-122">若要變更涉及聯結的資料表，必須在 **[篩選資料表的資料列]** 頁面上刪除現有的聯結篩選，然後在不同的資料表之間建立新聯結。</span><span class="sxs-lookup"><span data-stu-id="464cc-122">To change the tables involved in the join, you must delete the existing join filter on the **Filter Table Rows** page and create a new join between different tables.</span></span>  
  
2.  <span data-ttu-id="464cc-123">**建立聯結陳述式**</span><span class="sxs-lookup"><span data-stu-id="464cc-123">**Create the join statement**</span></span>  
  
    -   <span data-ttu-id="464cc-124">如果是加入新聯結，請選取 **[使用產生器建立陳述式]** 或 **[手動寫入聯結陳述式]** 。</span><span class="sxs-lookup"><span data-stu-id="464cc-124">If you are adding a new join, select either **Use the builder to create the statement** or **Write the join statement manually**.</span></span> <span data-ttu-id="464cc-125">如果您一開始是以手動寫入聯結，就無法使用產生器。</span><span class="sxs-lookup"><span data-stu-id="464cc-125">If you begin writing the join manually, you cannot use the builder.</span></span>  
  
         <span data-ttu-id="464cc-126">如果選取使用產生器，請使用方格中的資料行 ([結合]、[已篩選的資料表資料行] 、[運算子] 和 [聯結的資料表資料行] ) 來建立聯結陳述式。</span><span class="sxs-lookup"><span data-stu-id="464cc-126">If you select to use the builder, use the columns in the grid (**Conjunction**, **Filtered table column**, **Operator**, and **Joined table column**) to build a join statement.</span></span> <span data-ttu-id="464cc-127">方格中的每個資料行均包含一個下拉式清單方塊，可讓您選取兩個資料行和一個運算子 ( **=** 、 **<>** 、 **<=** 、 **\<**, **>=** 、 **>** 、**like**)。</span><span class="sxs-lookup"><span data-stu-id="464cc-127">Each column in the grid contains a drop-down list box, allowing you to select two columns and an operator (**=**, **<>**, **<=**, **\<**, **>=**, **>**, **like**).</span></span> <span data-ttu-id="464cc-128">結果會在 **[預覽]** 文字區域中顯示。</span><span class="sxs-lookup"><span data-stu-id="464cc-128">The results are displayed in the **Preview** text area.</span></span> <span data-ttu-id="464cc-129">如果聯結涉及一對以上的資料行，請從 **[結合]** 資料行中選取一個結合 ( **[AND]** 或 **[OR]** )，然後輸入兩個或更多的資料行及另一個運算子。</span><span class="sxs-lookup"><span data-stu-id="464cc-129">If the join involves more than one pair of columns, select a conjunction (**AND** or **OR**) from the **Conjunction** column, and then enter two more columns and another operator.</span></span>  
  
         <span data-ttu-id="464cc-130">如果選取手動寫入陳述式，請在 **[聯結陳述式]** 文字區域寫入聯結陳述式。</span><span class="sxs-lookup"><span data-stu-id="464cc-130">If you select to write the statement manually, write the join statement in the **Join statement** text area.</span></span> <span data-ttu-id="464cc-131">使用 **[已篩選的資料表資料行]** 清單方塊和 **[聯結的資料表資料行]** 清單方塊，將資料行拖放到 **[聯結陳述式]** 文字區域。</span><span class="sxs-lookup"><span data-stu-id="464cc-131">Use the **Filtered table columns** list box and **Joined table columns** list box to drag and drop columns to the **Join statement** text area.</span></span>  
  
    -   <span data-ttu-id="464cc-132">如果是編輯現有的聯結，您必須以手動進行編輯。</span><span class="sxs-lookup"><span data-stu-id="464cc-132">If you are editing an existing join, you must make edits manually.</span></span>  
  
3.  <span data-ttu-id="464cc-133">**指定聯結選項**</span><span class="sxs-lookup"><span data-stu-id="464cc-133">**Specify join options**</span></span>  
  
    -   <span data-ttu-id="464cc-134">如果在已篩選的資料表中聯結的資料行是唯一的，請選取 **[唯一索引鍵]** 。</span><span class="sxs-lookup"><span data-stu-id="464cc-134">If the column on which you join in the filtered table is unique, select **Unique key**.</span></span> <span data-ttu-id="464cc-135">如果資料行是唯一的，合併處理可以使用特殊效能最佳化。</span><span class="sxs-lookup"><span data-stu-id="464cc-135">The merge process has special performance optimizations available if the column is unique.</span></span>  
  
        > [!CAUTION]  
        >  <span data-ttu-id="464cc-136">選取此選項表示聯結篩選中的子資料表與父資料表之間的關聯性是一對一或一對多。</span><span class="sxs-lookup"><span data-stu-id="464cc-136">Selecting this option indicates that the relationship between the child and parent tables in a join filter is one to one or one to many.</span></span> <span data-ttu-id="464cc-137">如果在父資料表中的聯結資料行有保證唯一性的條件約束，請僅選取此選項。</span><span class="sxs-lookup"><span data-stu-id="464cc-137">Only select this option if you have a constraint on the joining column in the parent table that guarantees uniqueness.</span></span> <span data-ttu-id="464cc-138">如果選項設定不正確，則資料可能發生非聚合的情況。</span><span class="sxs-lookup"><span data-stu-id="464cc-138">If the option is set incorrectly, non-convergence of data can occur.</span></span>  
  
    -   <span data-ttu-id="464cc-139">僅限 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="464cc-139">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="464cc-140">依預設，合併式複寫在同步處理過程中會按逐個資料列的方式處理變更。</span><span class="sxs-lookup"><span data-stu-id="464cc-140">By default, merge replication processes changes on a row-by-row basis during synchronization.</span></span> <span data-ttu-id="464cc-141">若要將相關的變更作為一個單位來處理，請選取 **[邏輯記錄]** 。</span><span class="sxs-lookup"><span data-stu-id="464cc-141">To have related changes processed as a unit, select **Logical record**.</span></span> <span data-ttu-id="464cc-142">只有當發行項與發行集之使用邏輯記錄的需求均符合時，才可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="464cc-142">This option is available only if the article and publication requirements for using logical records are met.</span></span> <span data-ttu-id="464cc-143">如需詳細資訊，請參閱[使用邏輯記錄分組相關資料列的變更](merge/group-changes-to-related-rows-with-logical-records.md)中的＜使用邏輯記錄的考量＞一節。</span><span class="sxs-lookup"><span data-stu-id="464cc-143">For more information, see the section "Considerations for Using Logical Records" in [Group Changes to Related Rows with Logical Records](merge/group-changes-to-related-rows-with-logical-records.md).</span></span>  
  
 <span data-ttu-id="464cc-144">您加入或編輯篩選之後，請按一下 **[確定]** 以儲存變更並關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="464cc-144">After you have added or edited a filter, click **OK** to save changes and close the dialog box.</span></span> <span data-ttu-id="464cc-145">您指定的篩選會被剖析，並會針對 SELECT 子句中的資料表執行。</span><span class="sxs-lookup"><span data-stu-id="464cc-145">The filter you specified is parsed and run against the table in the SELECT clause.</span></span> <span data-ttu-id="464cc-146">如果篩選陳述式包含語法錯誤或其他問題，則系統會通知您，然後您可以編輯該篩選陳述式。</span><span class="sxs-lookup"><span data-stu-id="464cc-146">If the filter statement contains syntax errors or other problems, you will be notified and will be able to edit the filter statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="464cc-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="464cc-147">See Also</span></span>  
 <span data-ttu-id="464cc-148">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="464cc-148">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="464cc-149">[檢視及修改發行集屬性](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="464cc-149">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="464cc-150">[篩選發行的資料](publish/filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="464cc-150">[Filter Published Data](publish/filter-published-data.md) </span></span>  
 <span data-ttu-id="464cc-151">[Join Filters](merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="464cc-151">[Join Filters](merge/join-filters.md) </span></span>  
 <span data-ttu-id="464cc-152">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="464cc-152">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 [<span data-ttu-id="464cc-153">發行資料和資料庫物件</span><span class="sxs-lookup"><span data-stu-id="464cc-153">Publish Data and Database Objects</span></span>](publish/publish-data-and-database-objects.md)  
  
  
