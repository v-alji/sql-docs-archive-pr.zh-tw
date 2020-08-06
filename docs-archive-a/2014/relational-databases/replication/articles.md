---
title: 發行項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.articles.f1
ms.assetid: 7c743dc6-6c6d-4c92-b711-842e1b0b273e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 91336314a9538633af7c528d756d8461f7e8fe13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709226"
---
# <a name="articles"></a><span data-ttu-id="335df-102">發行項</span><span class="sxs-lookup"><span data-stu-id="335df-102">Articles</span></span>
  <span data-ttu-id="335df-103">在 **[發行項]** 頁面上，您可以指定發行集內要包含哪些資料庫物件做為發行項。</span><span class="sxs-lookup"><span data-stu-id="335df-103">On the **Articles** page, you specify which database objects to include as articles in the publication.</span></span> <span data-ttu-id="335df-104">如果您發行的資料庫物件相依於一或多個其他資料庫物件，就必須發行所有參考物件。</span><span class="sxs-lookup"><span data-stu-id="335df-104">If you are publishing a database object that depends on one or more other database objects, you must publish all referenced objects.</span></span> <span data-ttu-id="335df-105">例如，如果您發行相依於資料表的檢視表，同時也必須發行該資料表。</span><span class="sxs-lookup"><span data-stu-id="335df-105">For example, if you publish a view that depends on a table, you must publish the table also.</span></span>  
  
 <span data-ttu-id="335df-106">無法發行的物件旁邊會有一個紅色的圖示，且精靈頁面底部的資訊面板中會顯示說明。</span><span class="sxs-lookup"><span data-stu-id="335df-106">Objects that cannot be published have a red icon next to them, with an explanation in the information panel at the bottom of the wizard page.</span></span> <span data-ttu-id="335df-107">下列物件無法發行：</span><span class="sxs-lookup"><span data-stu-id="335df-107">The following objects cannot be published:</span></span>  
  
-   <span data-ttu-id="335df-108">加密的物件。</span><span class="sxs-lookup"><span data-stu-id="335df-108">Encrypted objects.</span></span>  
  
-   <span data-ttu-id="335df-109">沒有主索引鍵的資料表，無法在交易式發行集內發行。</span><span class="sxs-lookup"><span data-stu-id="335df-109">Tables without primary keys cannot be published in transactional publications.</span></span>  
  
-   <span data-ttu-id="335df-110">資料表無法同時發行到合併式發行集以及啟用佇列更新訂閱的交易式發行集。</span><span class="sxs-lookup"><span data-stu-id="335df-110">Tables cannot be published in both a merge publication and a transactional publication enabled for queued updating subscriptions.</span></span> <span data-ttu-id="335df-111">如需在多個發行集內發行發行項的詳細資訊，請參閱[發行資料和資料庫物件](publish/publish-data-and-database-objects.md)的＜在多個發行集內發行資料表＞一節。</span><span class="sxs-lookup"><span data-stu-id="335df-111">For more information about publishing an article in more than one publication, see the "Publishing Tables in More Than One Publication" section in [Publish Data and Database Objects](publish/publish-data-and-database-objects.md).</span></span>  
  
## <a name="oracle-publishers"></a><span data-ttu-id="335df-112">Oracle 發行者</span><span class="sxs-lookup"><span data-stu-id="335df-112">Oracle Publishers</span></span>  
 <span data-ttu-id="335df-113">Oracle 發行者有其他的注意事項：</span><span class="sxs-lookup"><span data-stu-id="335df-113">There are additional considerations for Oracle Publishers:</span></span>  
  
-   <span data-ttu-id="335df-114">如需可以從 Oracle 發行之物件的清單，請參閱＜ [Design Considerations and Limitations for Oracle Publishers](non-sql/design-considerations-and-limitations-for-oracle-publishers.md)＞。</span><span class="sxs-lookup"><span data-stu-id="335df-114">For a list of objects that can be published from Oracle, see [Design Considerations and Limitations for Oracle Publishers](non-sql/design-considerations-and-limitations-for-oracle-publishers.md).</span></span> <span data-ttu-id="335df-115">無法發行的物件不會顯示。</span><span class="sxs-lookup"><span data-stu-id="335df-115">Objects that cannot be published are not displayed.</span></span>  
  
-   <span data-ttu-id="335df-116">如需可以發行之資料類型的清單，請參閱＜ [Data Type Mapping for Oracle Publishers](non-sql/data-type-mapping-for-oracle-publishers.md)＞。</span><span class="sxs-lookup"><span data-stu-id="335df-116">For a list of data types that can be published, see [Data Type Mapping for Oracle Publishers](non-sql/data-type-mapping-for-oracle-publishers.md).</span></span> <span data-ttu-id="335df-117">具有無法發行之資料類型的資料行不會顯示。</span><span class="sxs-lookup"><span data-stu-id="335df-117">Columns with data types that cannot be published are not displayed.</span></span>  
  
## <a name="column-filters"></a><span data-ttu-id="335df-118">資料行篩選</span><span class="sxs-lookup"><span data-stu-id="335df-118">Column Filters</span></span>  
 <span data-ttu-id="335df-119">在 **[發行的物件]** 窗格中展開一個資料表，然後只選取必要的資料行，以篩選這個頁面上的資料行 (資料列可以在這個精靈的 **[篩選資料表的資料列]** 頁面中篩選)。</span><span class="sxs-lookup"><span data-stu-id="335df-119">Filter columns on this page by expanding a table in the **Objects to publish** pane and then selecting only the columns required (rows can be filtered in the **Filter Table Rows** page of this wizard).</span></span> <span data-ttu-id="335df-120">資料行的篩選功能有很多優點，包括安全性 (可防止機密資料被複寫) 和效能 (例如可避免複寫大型二進位大型物件 (BLOB) 資料行)。</span><span class="sxs-lookup"><span data-stu-id="335df-120">Filtering columns is useful for a number of reasons, including security (preventing sensitive data from being replicated) and performance (avoiding replication of large binary large object (BLOB) columns, for example).</span></span> <span data-ttu-id="335df-121">如需資料行篩選的詳細資訊，包括無法篩選的資料行類型清單，請參閱[篩選發行的資料](publish/filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="335df-121">For more information about column filtering, including a list of column types that cannot be filtered, see [Filter Published Data](publish/filter-published-data.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="335df-122">選項。</span><span class="sxs-lookup"><span data-stu-id="335df-122">Options</span></span>  
 <span data-ttu-id="335df-123">**[發行的物件]** 窗格可以讓您：</span><span class="sxs-lookup"><span data-stu-id="335df-123">The **Objects to publish** pane allows you to:</span></span>  
  
-   <span data-ttu-id="335df-124">檢視所有可以複寫的物件。</span><span class="sxs-lookup"><span data-stu-id="335df-124">View all objects available for replication.</span></span>  
  
-   <span data-ttu-id="335df-125">選取某個物件旁的核取方塊，將該物件加入發行集。</span><span class="sxs-lookup"><span data-stu-id="335df-125">Include an object in a publication by selecting the check box next to that object.</span></span>  
  
-   <span data-ttu-id="335df-126">選取某物件類型 (例如 **[資料表]** ) 旁的核取方塊，將特定類型 (例如資料表) 的所有物件加入發行集。</span><span class="sxs-lookup"><span data-stu-id="335df-126">Include all objects of a particular type (such as a table) in the publication by selecting the check box next to that object type (such as **Tables**).</span></span>  
  
-   <span data-ttu-id="335df-127">展開資料表節點，以查看資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="335df-127">Expand table nodes to see the columns in the table.</span></span>  
  
-   <span data-ttu-id="335df-128">清除某資料行旁的核取方塊，篩選出資料表資料行，將其排除在發行集之外。</span><span class="sxs-lookup"><span data-stu-id="335df-128">Filter table columns out of a publication by clearing the check box next to the column.</span></span>  
  
-   <span data-ttu-id="335df-129">以滑鼠右鍵按一下窗格中的物件，以查看該物件的命令功能表。</span><span class="sxs-lookup"><span data-stu-id="335df-129">Right-click an object in the pane to see a menu of commands for that object.</span></span>  
  
 <span data-ttu-id="335df-130">**發行項屬性**</span><span class="sxs-lookup"><span data-stu-id="335df-130">**Article Properties**</span></span>  
 <span data-ttu-id="335df-131">按一下 [發行項屬性] ，然後按一下下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="335df-131">Click **Article Properties**, and then click one of the following:</span></span>  
  
-   <span data-ttu-id="335df-132">按一下 [設定醒目提示 \<ObjectType> 發行項的屬性]，以啟動 [發行項屬性 - \<ObjectName>] 對話方塊；在這個對話方塊中所做屬性變更只會套用至 [發行項] 頁面上物件窗格中醒目提示的物件。</span><span class="sxs-lookup"><span data-stu-id="335df-132">Click **Set Properties of Highlighted \<ObjectType> Article** to launch the **Article Properties - \<ObjectName>** dialog box; property changes made in this dialog box are applied only to the object that is highlighted in the object pane on the **Articles** page.</span></span>  
  
-   <span data-ttu-id="335df-133">按一下 [設定所有 \<ObjectType> 發行項的屬性]，以啟動 [所有 \<ObjectType> 發行項的屬性] 對話方塊；在這個對話方塊中所做的屬性變更會套用至 [發行項] 頁面上物件窗格中屬於該類型的所有物件，包含尚未選取發行的物件。</span><span class="sxs-lookup"><span data-stu-id="335df-133">Click **Set Properties of All \<ObjectType> Articles**, to launch the **Properties for All \<ObjectType> Articles** dialog box; property changes made in this dialog box are applied to all objects of that type in the object pane on the **Articles** page, including ones not yet selected for publication.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="335df-134">在 [所有 \<ObjectType> 發行項的屬性] 對話方塊中所做屬性變更，會覆寫先前在 [發行項屬性 - \<ObjectName>] 對話方塊中所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="335df-134">Property changes made in the **Properties for All \<ObjectType> Articles** dialog box override any made previously in the **Article Properties - \<ObjectName>** dialog box.</span></span> <span data-ttu-id="335df-135">例如，若要設定所有屬於某物件類型之發行項的一些預設值，但同時要設定個別物件的某些屬性，則請先設定所有發行項的預設值，</span><span class="sxs-lookup"><span data-stu-id="335df-135">If, for example, you want to set a number of defaults for all articles of an object type, but also want to set some properties for individual objects, set the defaults for all articles first.</span></span> <span data-ttu-id="335df-136">然後再設定個別物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="335df-136">Then set the properties for the individual objects.</span></span>  
  
 <span data-ttu-id="335df-137">**反白的資料表僅限下載**</span><span class="sxs-lookup"><span data-stu-id="335df-137">**Highlighted table is download-only**</span></span>  
 <span data-ttu-id="335df-138">僅限合併式複寫。</span><span class="sxs-lookup"><span data-stu-id="335df-138">Merge replication only.</span></span> <span data-ttu-id="335df-139">僅限 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="335df-139">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only.</span></span> <span data-ttu-id="335df-140">選取以指定如果使用客訂閱，則訂閱者端不允許變更。</span><span class="sxs-lookup"><span data-stu-id="335df-140">Select to specify that changes are disallowed at the Subscriber if a client subscription is used.</span></span> <span data-ttu-id="335df-141">因為僅限下載的發行項不能在訂閱者端進行更新，追蹤中繼資料不會傳送給訂閱者。</span><span class="sxs-lookup"><span data-stu-id="335df-141">Because download-only articles cannot be updated at the Subscriber, tracking metadata is not sent to Subscribers.</span></span> <span data-ttu-id="335df-142">如此可減少訂閱者上的儲存體並提高效能，特別是網路連接緩慢時。</span><span class="sxs-lookup"><span data-stu-id="335df-142">This can lead to reduced storage on the Subscribers and a performance benefit, especially if the network connection is slow.</span></span> <span data-ttu-id="335df-143">此選項對應至 **[發行項屬性]** 對話方塊中， **[同步處理方向]** 選項的 **[僅限下載至訂閱者，禁止訂閱者變更]** 值。</span><span class="sxs-lookup"><span data-stu-id="335df-143">This option corresponds to a value of **Download-only to Subscriber, prohibit Subscriber changes** for the option **Synchronization direction** in the **Article Properties** dialog box.</span></span> <span data-ttu-id="335df-144">如需詳細資訊，請參閱[使用僅限下載的發行項最佳化合併式複寫效能](merge/optimize-merge-replication-performance-with-download-only-articles.md)。</span><span class="sxs-lookup"><span data-stu-id="335df-144">For more information, see [Optimize Merge Replication Performance with Download-Only Articles](merge/optimize-merge-replication-performance-with-download-only-articles.md).</span></span>  
  
 <span data-ttu-id="335df-145">**僅顯示清單中已核取的物件**</span><span class="sxs-lookup"><span data-stu-id="335df-145">**Show only checked objects in the list**</span></span>  
 <span data-ttu-id="335df-146">選取這個核取方塊，就只會顯示在物件窗格中選取的發行項。</span><span class="sxs-lookup"><span data-stu-id="335df-146">Select this check box to show only those articles that are selected in the object pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="335df-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="335df-147">See Also</span></span>  
 <span data-ttu-id="335df-148">[發行資料和資料庫物件](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="335df-148">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="335df-149">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="335df-149">[Create a Publication](publish/create-a-publication.md) </span></span>  
 [<span data-ttu-id="335df-150">檢視和修改發行集屬性</span><span class="sxs-lookup"><span data-stu-id="335df-150">View and Modify Publication Properties</span></span>](publish/view-and-modify-publication-properties.md)  
  
  
