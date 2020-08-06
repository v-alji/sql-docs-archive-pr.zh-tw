---
title: 發行集屬性，發行項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.pubproperties.articles.f1
ms.assetid: bdeea318-a153-44b8-9e51-9155f3bad18b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b88c54a6fc8c33193af7573ebd9b7c9931d8fbe6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702697"
---
# <a name="publication-properties-articles"></a><span data-ttu-id="e6859-102">發行集屬性，發行項</span><span class="sxs-lookup"><span data-stu-id="e6859-102">Publication Properties, Articles</span></span>
  <span data-ttu-id="e6859-103">**[發行集屬性]** 對話方塊的 **[發行項]** 頁面：包含有關發行集內所含發行項的資訊；可讓您將發行項加入至現有的發行集或從現有的發行集卸除發行項；以及可讓您變更發行項屬性和資料行篩選。</span><span class="sxs-lookup"><span data-stu-id="e6859-103">The **Articles** page of the **Publication Properties** dialog box: contains information about the articles contained in a publication; allows you to add articles to and drop articles from existing publications; and allows you to change article properties and column filtering.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6859-104">建立發行集之後，某些屬性變更需要新的快照集。</span><span class="sxs-lookup"><span data-stu-id="e6859-104">After a publication is created, some property changes require a new snapshot.</span></span> <span data-ttu-id="e6859-105">如果發行集有訂閱，則某些變更還需要重新初始化所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="e6859-105">If a publication has subscriptions, some changes also require all subscriptions to be reinitialized.</span></span> <span data-ttu-id="e6859-106">如需詳細資訊，請參閱[變更發行集與發行項屬性](publish/change-publication-and-article-properties.md)和[在現有發行集中新增和卸除發行項](publish/add-articles-to-and-drop-articles-from-existing-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="e6859-106">For more information, see [Change Publication and Article Properties](publish/change-publication-and-article-properties.md) and [Add Articles to and Drop Articles from Existing Publications](publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
 <span data-ttu-id="e6859-107">如果您發行的資料庫物件相依於一或多個其他資料庫物件，就必須發行所有參考物件。</span><span class="sxs-lookup"><span data-stu-id="e6859-107">If you are publishing a database object that depends on one or more other database objects, you must publish all referenced objects.</span></span> <span data-ttu-id="e6859-108">例如，如果您發行相依於資料表的檢視表，同時也必須發行該資料表。</span><span class="sxs-lookup"><span data-stu-id="e6859-108">For example, if you publish a view that depends on a table, you must publish the table also.</span></span>  
  
 <span data-ttu-id="e6859-109">無法發行的物件旁邊會有一個紅色的圖示，且精靈頁面底部的資訊面板中會顯示說明。</span><span class="sxs-lookup"><span data-stu-id="e6859-109">Objects that cannot be published have a red icon next to them, with an explanation in the information panel at the bottom of the wizard page.</span></span> <span data-ttu-id="e6859-110">下列物件無法發行：</span><span class="sxs-lookup"><span data-stu-id="e6859-110">The following objects cannot be published:</span></span>  
  
-   <span data-ttu-id="e6859-111">加密的物件。</span><span class="sxs-lookup"><span data-stu-id="e6859-111">Encrypted objects.</span></span>  
  
-   <span data-ttu-id="e6859-112">包含允許 NULL 之資料行的索引檢視。</span><span class="sxs-lookup"><span data-stu-id="e6859-112">Indexed views containing columns that allow NULL.</span></span>  
  
-   <span data-ttu-id="e6859-113">沒有主索引鍵的資料表，無法在交易式發行集內發行。</span><span class="sxs-lookup"><span data-stu-id="e6859-113">Tables without primary keys cannot be published in transactional publications.</span></span>  
  
-   <span data-ttu-id="e6859-114">資料表無法同時發行到合併式發行集以及啟用佇列更新訂閱的交易式發行集。</span><span class="sxs-lookup"><span data-stu-id="e6859-114">Tables cannot be published in both a merge publication and a transactional publication enabled for queued updating subscriptions.</span></span> <span data-ttu-id="e6859-115">如需在多個發行集內發行發行項的詳細資訊，請參閱[發行資料和資料庫物件](publish/publish-data-and-database-objects.md)的＜在多個發行集內發行資料表＞一節。</span><span class="sxs-lookup"><span data-stu-id="e6859-115">For more information about publishing an article in more than one publication, see the "Publishing Tables in More Than One Publication" section in [Publish Data and Database Objects](publish/publish-data-and-database-objects.md).</span></span>  
  
## <a name="oracle-publishers"></a><span data-ttu-id="e6859-116">Oracle 發行者</span><span class="sxs-lookup"><span data-stu-id="e6859-116">Oracle Publishers</span></span>  
 <span data-ttu-id="e6859-117">Oracle 發行者有其他的注意事項：</span><span class="sxs-lookup"><span data-stu-id="e6859-117">There are additional considerations for Oracle Publishers:</span></span>  
  
-   <span data-ttu-id="e6859-118">如需可以從 Oracle 發行之物件的清單，請參閱＜ [Design Considerations and Limitations for Oracle Publishers](non-sql/design-considerations-and-limitations-for-oracle-publishers.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e6859-118">For a list of objects that can be published from Oracle, see [Design Considerations and Limitations for Oracle Publishers](non-sql/design-considerations-and-limitations-for-oracle-publishers.md).</span></span> <span data-ttu-id="e6859-119">無法發行的物件不會顯示。</span><span class="sxs-lookup"><span data-stu-id="e6859-119">Objects that cannot be published are not displayed.</span></span>  
  
-   <span data-ttu-id="e6859-120">如需可以發行之資料類型的清單，請參閱＜ [Data Type Mapping for Oracle Publishers](non-sql/data-type-mapping-for-oracle-publishers.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e6859-120">For a list of data types that can be published, see [Data Type Mapping for Oracle Publishers](non-sql/data-type-mapping-for-oracle-publishers.md).</span></span> <span data-ttu-id="e6859-121">具有無法發行之資料類型的資料行不會顯示。</span><span class="sxs-lookup"><span data-stu-id="e6859-121">Columns with data types that cannot be published are not displayed.</span></span>  
  
## <a name="column-filters"></a><span data-ttu-id="e6859-122">資料行篩選</span><span class="sxs-lookup"><span data-stu-id="e6859-122">Column Filters</span></span>  
 <span data-ttu-id="e6859-123">在 **[發行的物件]** 窗格中展開一個資料表，然後只選取必要的資料行，以篩選這個頁面上的資料行 (資料列可以在這個精靈的 **[篩選資料表的資料列]** 頁面中篩選)。</span><span class="sxs-lookup"><span data-stu-id="e6859-123">Filter columns on this page by expanding a table in the **Objects to publish** pane and then selecting only the columns required (rows can be filtered in the **Filter Table Rows** page of this wizard).</span></span> <span data-ttu-id="e6859-124">資料行的篩選功能有很多優點，包括安全性 (可防止機密資料被複寫) 和效能 (例如可避免複寫大型二進位大型物件 (BLOB) 資料行)。</span><span class="sxs-lookup"><span data-stu-id="e6859-124">Filtering columns is useful for a number of reasons, including security (preventing sensitive data from being replicated) and performance (avoiding replication of large binary large object (BLOB) columns, for example).</span></span> <span data-ttu-id="e6859-125">如需資料行篩選的詳細資訊，包括無法篩選的資料行類型清單，請參閱[篩選發行的資料](publish/filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e6859-125">For more information about column filtering, including a list of column types that cannot be filtered, see [Filter Published Data](publish/filter-published-data.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e6859-126">選項。</span><span class="sxs-lookup"><span data-stu-id="e6859-126">Options</span></span>  
 <span data-ttu-id="e6859-127">**[發行的物件]** 窗格可以讓您：</span><span class="sxs-lookup"><span data-stu-id="e6859-127">The **Objects to publish** pane allows you to:</span></span>  
  
-   <span data-ttu-id="e6859-128">檢視所有可以複寫的物件。</span><span class="sxs-lookup"><span data-stu-id="e6859-128">View all objects available for replication.</span></span>  
  
-   <span data-ttu-id="e6859-129">透過選取該物件旁邊的核取方塊，即可將發行項加入至發行集。</span><span class="sxs-lookup"><span data-stu-id="e6859-129">Add an article to a publication by selecting the check box next to that object.</span></span>  
  
-   <span data-ttu-id="e6859-130">透過清除該物件旁邊的核取方塊，即可從發行集卸除發行項。</span><span class="sxs-lookup"><span data-stu-id="e6859-130">Drop an article from a publication by clearing the check box next to that object.</span></span> <span data-ttu-id="e6859-131">如需何時可以卸除發行項的資訊，請參閱[在現有發行集中新增和卸除發行項](publish/add-articles-to-and-drop-articles-from-existing-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="e6859-131">For information about when articles can be dropped, see [Add Articles to and Drop Articles from Existing Publications](publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
-   <span data-ttu-id="e6859-132">選取某物件類型 (例如 **[資料表]** ) 旁的核取方塊，將特定類型 (例如資料表) 的所有物件加入發行集。</span><span class="sxs-lookup"><span data-stu-id="e6859-132">Include all objects of a particular type (such as a table) in the publication by selecting the check box next to that object type (such as **Tables**).</span></span>  
  
-   <span data-ttu-id="e6859-133">展開資料表節點，以查看資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="e6859-133">Expand table nodes to see the columns in the table.</span></span>  
  
-   <span data-ttu-id="e6859-134">透過清除資料行旁邊的核取方塊來篩選出發行集的資料表資料行，或透過選取核取方塊來包含未發行的資料行。</span><span class="sxs-lookup"><span data-stu-id="e6859-134">Filter table columns out of a publication by clearing the check box next to the column or include unpublished columns by selecting the check box.</span></span>  
  
-   <span data-ttu-id="e6859-135">以滑鼠右鍵按一下窗格中的物件，以查看該物件的命令功能表。</span><span class="sxs-lookup"><span data-stu-id="e6859-135">Right-click an object in the pane to see a menu of commands for that object.</span></span>  
  
 <span data-ttu-id="e6859-136">**發行項屬性**</span><span class="sxs-lookup"><span data-stu-id="e6859-136">**Article Properties**</span></span>  
 <span data-ttu-id="e6859-137">按一下 **[發行項屬性]** ，然後按一下下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="e6859-137">Click **Article Properties** , and then click one of the following:</span></span>  
  
-   <span data-ttu-id="e6859-138">按一下 [設定醒目提示 \<ObjectType> 發行項的屬性]，以啟動 [發行項屬性 - \<ObjectName>] 對話方塊；在這個對話方塊中所做屬性變更只會套用至 [發行項] 頁面上物件窗格中醒目提示的物件。</span><span class="sxs-lookup"><span data-stu-id="e6859-138">Click **Set Properties of Highlighted \<ObjectType> Article** to launch the **Article Properties - \<ObjectName>** dialog box; property changes made in this dialog box are applied only to the object that is highlighted in the object pane on the **Articles** page.</span></span>  
  
-   <span data-ttu-id="e6859-139">按一下 [設定所有 \<ObjectType> 發行項的屬性]，以啟動 [所有 \<ObjectType> 發行項的屬性] 對話方塊；在這個對話方塊中所做的屬性變更會套用至 [發行項] 頁面上物件窗格中屬於該類型的所有物件，包含尚未選取發行的物件。</span><span class="sxs-lookup"><span data-stu-id="e6859-139">Click **Set Properties of All \<ObjectType> Articles**, to launch the **Properties for All \<ObjectType> Articles** dialog box; property changes made in this dialog box are applied to all objects of that type in the object pane on the **Articles** page, including ones not yet selected for publication.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e6859-140">在 [所有 \<ObjectType> 發行項的屬性] 對話方塊中所做屬性變更，會覆寫先前在 [發行項屬性 - \<ObjectName>] 對話方塊中所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="e6859-140">Property changes made in the **Properties for All \<ObjectType> Articles** dialog box override any made previously in the **Article Properties - \<ObjectName>** dialog box.</span></span> <span data-ttu-id="e6859-141">例如，若要設定所有屬於某物件類型之發行項的一些預設值，但同時要設定個別物件的某些屬性，則請先設定所有發行項的預設值，</span><span class="sxs-lookup"><span data-stu-id="e6859-141">If, for example, you want to set a number of defaults for all articles of an object type, but also want to set some properties for individual objects, set the defaults for all articles first.</span></span> <span data-ttu-id="e6859-142">然後再設定個別物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="e6859-142">Then set the properties for the individual objects.</span></span>  
  
 <span data-ttu-id="e6859-143">**反白的資料表僅限下載**</span><span class="sxs-lookup"><span data-stu-id="e6859-143">**Highlighted table is download-only**</span></span>  
 <span data-ttu-id="e6859-144">僅限合併式複寫。</span><span class="sxs-lookup"><span data-stu-id="e6859-144">Merge replication only.</span></span> <span data-ttu-id="e6859-145">僅限 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="e6859-145">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="e6859-146">選取以指定如果使用客訂閱，則訂閱者端不允許變更。</span><span class="sxs-lookup"><span data-stu-id="e6859-146">Select to specify that changes are disallowed at the Subscriber if a client subscription is used.</span></span> <span data-ttu-id="e6859-147">因為僅限下載的發行項不能在訂閱者端進行更新，追蹤中繼資料不會傳送給訂閱者。</span><span class="sxs-lookup"><span data-stu-id="e6859-147">Because download-only articles cannot be updated at the Subscriber, tracking metadata is not sent to Subscribers.</span></span> <span data-ttu-id="e6859-148">如此可減少訂閱者上的儲存體並提高效能，特別是網路連接緩慢時。</span><span class="sxs-lookup"><span data-stu-id="e6859-148">This can lead to reduced storage on the Subscribers and a performance benefit, especially if the network connection is slow.</span></span> <span data-ttu-id="e6859-149">此選項對應至 **[發行項屬性]** 對話方塊中， **[同步處理方向]** 選項的 **[僅限下載至訂閱者，禁止訂閱者變更]** 值。</span><span class="sxs-lookup"><span data-stu-id="e6859-149">This option corresponds to a value of **Download-only to Subscriber, prohibit Subscriber changes** for the option **Synchronization direction** in the **Article Properties** dialog box.</span></span> <span data-ttu-id="e6859-150">如需詳細資訊，請參閱[使用僅限下載的發行項最佳化合併式複寫效能](merge/optimize-merge-replication-performance-with-download-only-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="e6859-150">For more information, see [Optimize Merge Replication Performance with Download-Only Articles](merge/optimize-merge-replication-performance-with-download-only-articles.md).</span></span>  
  
 <span data-ttu-id="e6859-151">**僅顯示清單中已核取的物件**</span><span class="sxs-lookup"><span data-stu-id="e6859-151">**Show only checked objects in the list**</span></span>  
 <span data-ttu-id="e6859-152">選取這個核取方塊，就只會顯示在物件窗格中選取的發行項。</span><span class="sxs-lookup"><span data-stu-id="e6859-152">Select this check box to show only those articles that are selected in the object pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6859-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6859-153">See Also</span></span>  
 <span data-ttu-id="e6859-154">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="e6859-154">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="e6859-155">[檢視及修改發行集屬性](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="e6859-155">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="e6859-156">[建立和套用初始快照集](create-and-apply-the-initial-snapshot.md) </span><span class="sxs-lookup"><span data-stu-id="e6859-156">[Create and Apply the Initial Snapshot](create-and-apply-the-initial-snapshot.md) </span></span>  
 <span data-ttu-id="e6859-157">[重新初始化訂閱](reinitialize-a-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="e6859-157">[Reinitialize a Subscription](reinitialize-a-subscription.md) </span></span>  
 [<span data-ttu-id="e6859-158">發行資料和資料庫物件</span><span class="sxs-lookup"><span data-stu-id="e6859-158">Publish Data and Database Objects</span></span>](publish/publish-data-and-database-objects.md)  
  
  
