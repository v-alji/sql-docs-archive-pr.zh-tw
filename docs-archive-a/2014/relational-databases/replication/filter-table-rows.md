---
title: 篩選資料表的資料列 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.filtertablerows.f1
ms.assetid: 005f5c71-0401-490e-8823-adc54a2e9675
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9adeb2501adfd37658ddf05aa9956d6c3922bb80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585842"
---
# <a name="filter-table-rows"></a><span data-ttu-id="15ebb-102">篩選資料表的資料列</span><span class="sxs-lookup"><span data-stu-id="15ebb-102">Filter Table Rows</span></span>
  <span data-ttu-id="15ebb-103">**[篩選資料表的資料列]** 頁面可以讓您：</span><span class="sxs-lookup"><span data-stu-id="15ebb-103">The **Filter Table Rows** page allows you to:</span></span>  
  
-   <span data-ttu-id="15ebb-104">將靜態資料列篩選套用至快照集式、交易式和合併式發行集的資料表發行項。</span><span class="sxs-lookup"><span data-stu-id="15ebb-104">Apply static row filters to table articles in snapshot, transactional, and merge publications.</span></span>  
  
-   <span data-ttu-id="15ebb-105">將參數化資料列篩選器套用至合併式發行集的資料表發行項。</span><span class="sxs-lookup"><span data-stu-id="15ebb-105">Apply parameterized row filters to table articles in merge publications.</span></span>  
  
-   <span data-ttu-id="15ebb-106">使用聯結篩選，將合併資料表發行項的篩選擴充到相關的資料表發行項。</span><span class="sxs-lookup"><span data-stu-id="15ebb-106">Use join filters to extend filters on merge table articles to related table articles.</span></span>  
  
 <span data-ttu-id="15ebb-107">如需篩選選項的詳細資訊，請參閱[篩選發行的資料](publish/filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="15ebb-107">For more information about filtering options, see [Filter Published Data](publish/filter-published-data.md).</span></span> <span data-ttu-id="15ebb-108">篩選設定可以在 **[發行集屬性]** 對話方塊的 **[篩選資料列]** 頁面中變更。</span><span class="sxs-lookup"><span data-stu-id="15ebb-108">Filtering can be changed in the **Filter Rows** page of the **Publication Properties** dialog box.</span></span>  
  
 <span data-ttu-id="15ebb-109">若要使應用程式效能最佳化，並減少需要的遠端儲存體數量，或限制特定訂閱者對特定資料的存取，您就應該只發行需要的資料。</span><span class="sxs-lookup"><span data-stu-id="15ebb-109">To maximize application performance and reduce the amount of remote storage required, or to restrict the availability of certain data to specific Subscribers, you should publish only the data required.</span></span> <span data-ttu-id="15ebb-110">發行集可同時包括未篩選和已篩選的資料表。</span><span class="sxs-lookup"><span data-stu-id="15ebb-110">Your publication can include both unfiltered and filtered tables.</span></span> <span data-ttu-id="15ebb-111">例如，您可以包括公司產品的完整 (未篩選) 資料表，並使用資料列篩選來提供已篩選過、僅包含特定區域之客戶的資料表。</span><span class="sxs-lookup"><span data-stu-id="15ebb-111">For example, you could include the complete (unfiltered) table of company products and use row filters to provide a filtered table of customers for a specific region.</span></span> <span data-ttu-id="15ebb-112">利用篩選發行的資料，您可以：</span><span class="sxs-lookup"><span data-stu-id="15ebb-112">By filtering published data, you can:</span></span>  
  
-   <span data-ttu-id="15ebb-113">將透過網路傳送的資料總量縮減到最少。</span><span class="sxs-lookup"><span data-stu-id="15ebb-113">Minimize the amount of data sent over the network.</span></span>  
  
-   <span data-ttu-id="15ebb-114">降低訂閱者端所需的儲存空間量。</span><span class="sxs-lookup"><span data-stu-id="15ebb-114">Reduce the amount of storage space required at the Subscriber.</span></span>  
  
-   <span data-ttu-id="15ebb-115">依照個別的訂閱者需求，自訂發行集和應用程式。</span><span class="sxs-lookup"><span data-stu-id="15ebb-115">Customize publications and applications based on individual Subscriber requirements.</span></span>  
  
-   <span data-ttu-id="15ebb-116">可以避免或減少訂閱者更新資料時的衝突，因為不同資料分割可以傳送給不同的訂閱者 (不會有兩個訂閱者同時更新相同的資料值)。</span><span class="sxs-lookup"><span data-stu-id="15ebb-116">Avoid or reduce conflicts if Subscribers are updating data, because different data partitions can be sent to different Subscribers (no two Subscribers will be updating the same data values).</span></span>  
  
-   <span data-ttu-id="15ebb-117">避免傳送機密資料。</span><span class="sxs-lookup"><span data-stu-id="15ebb-117">Avoid transmitting sensitive data.</span></span> <span data-ttu-id="15ebb-118">資料列篩選與資料行篩選可用於限制訂閱者對資料的存取。</span><span class="sxs-lookup"><span data-stu-id="15ebb-118">Row filters and column filters can be used to restrict a Subscriber's access to data.</span></span> <span data-ttu-id="15ebb-119">對於合併式複寫，如果使用含有 HOST_NAME() 的參數化篩選，則有安全性考量。</span><span class="sxs-lookup"><span data-stu-id="15ebb-119">For merge replication, there are security considerations if you use a parameterized filter that includes HOST_NAME().</span></span> <span data-ttu-id="15ebb-120">如需詳細資訊，請參閱＜ [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md)＞中的「使用 HOST_NAME() 進行篩選」一節。</span><span class="sxs-lookup"><span data-stu-id="15ebb-120">For more information, see the section "Filtering with HOST_NAME()" in [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="15ebb-121">篩選不得包含複寫識別資料列所使用的 `rowguidcol`。</span><span class="sxs-lookup"><span data-stu-id="15ebb-121">A filter must not include the `rowguidcol` used by replication to identify rows.</span></span> <span data-ttu-id="15ebb-122">根據預設，這是在您設定合併式複寫時加入，且名稱為 **rowguid**的資料行。</span><span class="sxs-lookup"><span data-stu-id="15ebb-122">By default this is the column added at the time you set up merge replication and is named **rowguid**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="15ebb-123">選項。</span><span class="sxs-lookup"><span data-stu-id="15ebb-123">Options</span></span>  
 <span data-ttu-id="15ebb-124">**已篩選的資料表**</span><span class="sxs-lookup"><span data-stu-id="15ebb-124">**Filtered Tables**</span></span>  
 <span data-ttu-id="15ebb-125">當您在發行集的資料表發行項中加入篩選時，這些篩選就會擴展到窗格中。</span><span class="sxs-lookup"><span data-stu-id="15ebb-125">This pane is populated with filters as you add them to table articles in the publication.</span></span> <span data-ttu-id="15ebb-126">含有資料列篩選的資料表，會顯示為窗格中的最上層節點。</span><span class="sxs-lookup"><span data-stu-id="15ebb-126">Tables with row filters are shown as top-level nodes in the pane.</span></span> <span data-ttu-id="15ebb-127">若為合併式發行集，則透過聯結篩選而擴充篩選的資料表，就會顯示為子節點。</span><span class="sxs-lookup"><span data-stu-id="15ebb-127">For merge publications, tables to which filtering has been extended through a join filter are shown as child nodes.</span></span>  
  
 <span data-ttu-id="15ebb-128">**加入**</span><span class="sxs-lookup"><span data-stu-id="15ebb-128">**Add**</span></span>  
 <span data-ttu-id="15ebb-129">按一下 **[加入]** 即可啟動一個可讓您篩選資料表發行項的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="15ebb-129">Click **Add** to launch a dialog box that enables you to filter table articles.</span></span> <span data-ttu-id="15ebb-130">在快照集或交易式發行集按一下 **[加入]** 會立即啟動對話方塊。</span><span class="sxs-lookup"><span data-stu-id="15ebb-130">Clicking **Add** for a snapshot or transactional publication launches a dialog box immediately.</span></span> <span data-ttu-id="15ebb-131">針對合併式發行集按一下 [加入] 會顯示三個選項：[加入篩選]、[加入聯結以擴充選取的篩選]，以及 [自動產生篩選]。</span><span class="sxs-lookup"><span data-stu-id="15ebb-131">Clicking **Add** for a merge publication displays three choices: **Add Filter**; **Add Join to Extend the Selected Filter**; **Automatically Generate Filters**.</span></span>  
  
-   <span data-ttu-id="15ebb-132">選取 **[加入篩選]** 即可啟動 **[加入篩選]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="15ebb-132">Select **Add Filter** to launch the **Add Filter** dialog box.</span></span> <span data-ttu-id="15ebb-133">這個對話方塊可以讓您套用資料列篩選至資料表發行項。</span><span class="sxs-lookup"><span data-stu-id="15ebb-133">This dialog box allows you to apply row filters to a table article.</span></span> <span data-ttu-id="15ebb-134">例如，在 **[加入篩選]** 對話方塊中，您可以指定含有客戶資料的資料表在複寫到訂閱者時，只能包含法國客戶的資料。</span><span class="sxs-lookup"><span data-stu-id="15ebb-134">In the **Add Filter** dialog box, you could, for example, specify that a table with customer data should only contain data on French customers when it is replicated to Subscribers.</span></span>  
  
-   <span data-ttu-id="15ebb-135">選取 **[加入聯結以擴充選取的篩選]** 即可啟動 **[加入聯結]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="15ebb-135">Select **Add Join to Extend the Selected Filter** to launch the **Add Join** dialog box.</span></span> <span data-ttu-id="15ebb-136">**[加入聯結]** 對話方塊可以讓您擴充資料列篩選，使它篩選與具有資料列篩選的資料表相關之資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="15ebb-136">The **Add Join** dialog box allows you to extend a row filter so that it filters data in tables related to the table with the row filter.</span></span> <span data-ttu-id="15ebb-137">例如，如果客戶資料表經過篩選後只包含法國客戶的資料，而它有一個包含客戶訂單的相關資料表，那麼您就可以在兩個資料表之間定義聯結，使訂單資料表只包括法國客戶的訂單。</span><span class="sxs-lookup"><span data-stu-id="15ebb-137">For example, if a customer table is filtered so that it only contains data on French customers and there is a related table for customer orders, you can define a join between the two tables so that the orders table only includes orders from French customers.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="15ebb-138">唯有當您先在篩選窗格中選取聯結的基底資料表，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="15ebb-138">This option is available only if you first select the base table of the join in the filter pane.</span></span>  
  
-   <span data-ttu-id="15ebb-139">選取 **[自動產生篩選]** 來啟動 **[產生篩選]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="15ebb-139">Select **Automatically Generate Filters** to launch the **Generate Filters** dialog box.</span></span> <span data-ttu-id="15ebb-140">這個對話方塊可讓您在合併式發行集的一個資料表上定義資料列篩選，複寫時會自動將此篩選擴充到因外部索引鍵關聯性而相關的其他資料表。</span><span class="sxs-lookup"><span data-stu-id="15ebb-140">This dialog box allows you to define a row filter on one table in a merge publication that replication automatically extends to other tables that are related through foreign key relationships.</span></span> <span data-ttu-id="15ebb-141">例如，發行集可包括 3 個資料表：客戶資料表、訂單資料表 (含有客戶資料表的外部索引鍵) 和訂單明細資料表 (含有訂單資料表的外部索引鍵)。</span><span class="sxs-lookup"><span data-stu-id="15ebb-141">For example, a publication could include three tables: a customer table, an orders table (with a foreign key to the customer table), and an order details table (with a foreign key to the orders table).</span></span> <span data-ttu-id="15ebb-142">在客戶資料表上定義資料列篩選，複寫時會將它擴充到其他資料表。</span><span class="sxs-lookup"><span data-stu-id="15ebb-142">Define a row filter on the customer table, and replication will extend it to the other tables.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="15ebb-143">當複寫自動產生篩選時，發行集上任何現有的篩選都會被刪除。</span><span class="sxs-lookup"><span data-stu-id="15ebb-143">When filters are automatically generated by replication, any existing filters on the publication are deleted.</span></span> <span data-ttu-id="15ebb-144">若要同時包括自動產生的篩選和手動指定的篩選，請先產生篩選。</span><span class="sxs-lookup"><span data-stu-id="15ebb-144">To include both filters generated automatically and ones specified manually, generate filters first.</span></span> <span data-ttu-id="15ebb-145">您只能對每個發行集指定一個自動產生的篩選集。</span><span class="sxs-lookup"><span data-stu-id="15ebb-145">You can only specify one set of automatically generated filters for each publication.</span></span>  
  
 <span data-ttu-id="15ebb-146">**編輯**</span><span class="sxs-lookup"><span data-stu-id="15ebb-146">**Edit**</span></span>  
 <span data-ttu-id="15ebb-147">在篩選窗格中選取資料列篩選或聯結篩選，再按一下 **[編輯]** ，即可啟動 **[編輯篩選]** 或 **[編輯聯結]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="15ebb-147">Select a row filter or join filter in the filter pane and click **Edit** to launch the **Edit Filter** or **Edit Join** dialog box.</span></span>  
  
 <span data-ttu-id="15ebb-148">**刪除**</span><span class="sxs-lookup"><span data-stu-id="15ebb-148">**Delete**</span></span>  
 <span data-ttu-id="15ebb-149">在篩選窗格中選取資料列篩選或聯結篩選，再按一下 **[刪除]** 即可刪除篩選。</span><span class="sxs-lookup"><span data-stu-id="15ebb-149">Select a row filter or join filter in the filter pane and click **Delete** to delete the filter.</span></span>  
  
 <span data-ttu-id="15ebb-150">**尋找資料表**</span><span class="sxs-lookup"><span data-stu-id="15ebb-150">**Find Table**</span></span>  
 <span data-ttu-id="15ebb-151">僅適用於具有聯結篩選的合併式發行集。</span><span class="sxs-lookup"><span data-stu-id="15ebb-151">Merge publications with join filters only.</span></span> <span data-ttu-id="15ebb-152">按一下 **[尋找資料表]** ，即可在複雜篩選樹中尋找資料表。</span><span class="sxs-lookup"><span data-stu-id="15ebb-152">Click **Find Table** to find a table in a complex filter tree.</span></span> <span data-ttu-id="15ebb-153">在含有複雜關聯性的資料庫中，因為資料表可以聯結到多個資料表，所以資料表可能重複出現在篩選樹的多個位置。</span><span class="sxs-lookup"><span data-stu-id="15ebb-153">In a database with complex relationships, a table can be joined to multiple tables, and therefore can appear in more than one place in the filter tree.</span></span>  
  
 <span data-ttu-id="15ebb-154">實際資料表只出現在篩選樹的一個位置，而在其他位置，資料表是以捷徑方式顯示。</span><span class="sxs-lookup"><span data-stu-id="15ebb-154">The actual table appears in only one place in the tree, and in other places, the table is represented by a shortcut.</span></span> <span data-ttu-id="15ebb-155">資料表的捷徑只是資料表的參考，它不會顯示資料表的子節點。</span><span class="sxs-lookup"><span data-stu-id="15ebb-155">A shortcut to a table is only a reference to the table; it does not show the child nodes of the table.</span></span> <span data-ttu-id="15ebb-156">捷徑節點會以捷徑箭頭標示，展開該節點會顯示這段文字：**按一下 [尋找資料表]，以檢視 \<tablename> 的資料表**。</span><span class="sxs-lookup"><span data-stu-id="15ebb-156">A shortcut node is marked with a shortcut arrow, and expanding that node shows the text **Click Find Table to see table for \<tablename>**.</span></span>  
  
 <span data-ttu-id="15ebb-157">在窗格中選取捷徑節點，然後按一下 **[尋找資料表]** 。</span><span class="sxs-lookup"><span data-stu-id="15ebb-157">Select a shortcut node in the pane and click **Find Table**.</span></span> <span data-ttu-id="15ebb-158">窗格會展開，且反白資料表。</span><span class="sxs-lookup"><span data-stu-id="15ebb-158">The pane is expanded and the table is highlighted.</span></span> <span data-ttu-id="15ebb-159">如果您按一下 **[尋找資料表]** 但未選取捷徑節點，則會啟動 **[尋找資料表]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="15ebb-159">If you click **Find Table** without a shortcut node selected, a **Find Table** dialog box is launched.</span></span>  
  
 <span data-ttu-id="15ebb-160">**Filter**</span><span class="sxs-lookup"><span data-stu-id="15ebb-160">**Filter**</span></span>  
 <span data-ttu-id="15ebb-161">包含在篩選窗格中選取之篩選的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 定義。</span><span class="sxs-lookup"><span data-stu-id="15ebb-161">Contains the [!INCLUDE[tsql](../../includes/tsql-md.md)] definition for the filter selected in the filter pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15ebb-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15ebb-162">See Also</span></span>  
 <span data-ttu-id="15ebb-163">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="15ebb-163">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="15ebb-164">[檢視及修改發行集屬性](publish/view-and-modify-publication-properties.md) </span><span class="sxs-lookup"><span data-stu-id="15ebb-164">[View and Modify Publication Properties](publish/view-and-modify-publication-properties.md) </span></span>  
 <span data-ttu-id="15ebb-165">[篩選發行的資料](publish/filter-published-data.md) </span><span class="sxs-lookup"><span data-stu-id="15ebb-165">[Filter Published Data](publish/filter-published-data.md) </span></span>  
 <span data-ttu-id="15ebb-166">[Join Filters](merge/join-filters.md) </span><span class="sxs-lookup"><span data-stu-id="15ebb-166">[Join Filters](merge/join-filters.md) </span></span>  
 <span data-ttu-id="15ebb-167">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span><span class="sxs-lookup"><span data-stu-id="15ebb-167">[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md) </span></span>  
 [<span data-ttu-id="15ebb-168">發行資料和資料庫物件</span><span class="sxs-lookup"><span data-stu-id="15ebb-168">Publish Data and Database Objects</span></span>](publish/publish-data-and-database-objects.md)  
  
  
