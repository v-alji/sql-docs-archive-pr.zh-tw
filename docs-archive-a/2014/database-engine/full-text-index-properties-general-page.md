---
title: 全文檢索索引屬性 (一般頁面) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.general.f1
ms.assetid: f4dff61c-8c2f-4ff9-abe4-70a34421448f
author: rothja
ms.author: jroth
ms.openlocfilehash: 61b9f2948df138c39230cf6f5787c395a364c695
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607043"
---
# <a name="full-text-index-properties-general-page"></a><span data-ttu-id="5da10-102">全文檢索索引屬性 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="5da10-102">Full-Text Index Properties (General Page)</span></span>
  <span data-ttu-id="5da10-103">**若要檢視或變更全文檢索索引的可修改屬性**</span><span class="sxs-lookup"><span data-stu-id="5da10-103">**To view or change the modifiable properties of a full-text index**</span></span>  
  
-   [<span data-ttu-id="5da10-104">管理全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="5da10-104">Manage Full-Text Indexes</span></span>](../relational-databases/indexes/indexes.md)  
  
## <a name="ui-element-list"></a><span data-ttu-id="5da10-105">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="5da10-105">UI element list</span></span>  
 <span data-ttu-id="5da10-106">**全文檢索目錄**</span><span class="sxs-lookup"><span data-stu-id="5da10-106">**Full-Text Catalog**</span></span>  
 <span data-ttu-id="5da10-107">顯示與全文檢索索引相關聯之全文檢索目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="5da10-107">Displays the name of the full-text catalog with which the full-text index is associated.</span></span>  
  
 <span data-ttu-id="5da10-108">**Database**</span><span class="sxs-lookup"><span data-stu-id="5da10-108">**Database**</span></span>  
 <span data-ttu-id="5da10-109">顯示全文檢索索引所在之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="5da10-109">Displays the name of the database in which the full-text index resides.</span></span>  
  
 <span data-ttu-id="5da10-110">**資料表**</span><span class="sxs-lookup"><span data-stu-id="5da10-110">**Table**</span></span>  
 <span data-ttu-id="5da10-111">顯示定義全文檢索索引之資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="5da10-111">Displays the name of the table on which the full-text index is defined.</span></span>  
  
 <span data-ttu-id="5da10-112">**全文檢索索引鍵**</span><span class="sxs-lookup"><span data-stu-id="5da10-112">**Full-Text Index Key**</span></span>  
 <span data-ttu-id="5da10-113">顯示全文檢索索引鍵的名稱，它是資料表之單一資料行的唯一索引。</span><span class="sxs-lookup"><span data-stu-id="5da10-113">Displays the name of the full-text index key, which is a unique index on a single column of the table.</span></span>  
  
 <span data-ttu-id="5da10-114">**資料表全文檢索擴展狀態**</span><span class="sxs-lookup"><span data-stu-id="5da10-114">**Table Full-Text Populate Status**</span></span>  
 <span data-ttu-id="5da10-115">顯示全文檢索索引資料表的母體擴展狀態。</span><span class="sxs-lookup"><span data-stu-id="5da10-115">Displays the population status of the full-text indexed table.</span></span>  
  
 <span data-ttu-id="5da10-116">可能的值如下：</span><span class="sxs-lookup"><span data-stu-id="5da10-116">The possible values are as follows:</span></span>  
  
 <span data-ttu-id="5da10-117">0 = 閒置。</span><span class="sxs-lookup"><span data-stu-id="5da10-117">0 = Idle.</span></span>  
  
 <span data-ttu-id="5da10-118">1 = 完整母體擴展在進行中。</span><span class="sxs-lookup"><span data-stu-id="5da10-118">1 = Full population is in progress.</span></span>  
  
 <span data-ttu-id="5da10-119">2 = 累加母體擴展在進行中。</span><span class="sxs-lookup"><span data-stu-id="5da10-119">2 = Incremental population is in progress.</span></span>  
  
 <span data-ttu-id="5da10-120">3 = 追蹤變更的傳播在進行中。</span><span class="sxs-lookup"><span data-stu-id="5da10-120">3 = Propagation of tracked changes is in progress.</span></span>  
  
 <span data-ttu-id="5da10-121">4 = 背景更新索引在進行中，例如自動變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="5da10-121">4 = Background update index is in progress, such as automatic change tracking.</span></span>  
  
 <span data-ttu-id="5da10-122">5 = 全文檢索索引在調整執行速度或暫停。</span><span class="sxs-lookup"><span data-stu-id="5da10-122">5 = Full-text indexing is throttled or paused.</span></span>  
  
 <span data-ttu-id="5da10-123">**使用中全文檢索索引**</span><span class="sxs-lookup"><span data-stu-id="5da10-123">**Active Full-Text Index**</span></span>  
 <span data-ttu-id="5da10-124">指出資料表是否具有使用中全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="5da10-124">Indicates whether the table has an active full-text index.</span></span>  
  
 <span data-ttu-id="5da10-125">1 = True</span><span class="sxs-lookup"><span data-stu-id="5da10-125">1 = True</span></span>  
  
 <span data-ttu-id="5da10-126">0 = False</span><span class="sxs-lookup"><span data-stu-id="5da10-126">0 = False</span></span>  
  
 <span data-ttu-id="5da10-127">**全文檢索索引檔案群組**</span><span class="sxs-lookup"><span data-stu-id="5da10-127">**Full-Text Index Filegroup**</span></span>  
 <span data-ttu-id="5da10-128">全文檢索索引所屬的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="5da10-128">The filegroup to which the full-text index belongs.</span></span>  
  
 <span data-ttu-id="5da10-129">**全文檢索索引停用字詞表**</span><span class="sxs-lookup"><span data-stu-id="5da10-129">**Full-Text Index Stoplist**</span></span>  
 <span data-ttu-id="5da10-130">目前與全文檢索索引產生關聯的停用字詞表。</span><span class="sxs-lookup"><span data-stu-id="5da10-130">The stoplist that is currently associated with the full-text index.</span></span> <span data-ttu-id="5da10-131">停用字詞表是 [停用字詞](../relational-databases/search/full-text-search.md)的清單。</span><span class="sxs-lookup"><span data-stu-id="5da10-131">A stoplist is a list of [stopwords](../relational-databases/search/full-text-search.md).</span></span> <span data-ttu-id="5da10-132">與全文檢索索引相關聯的停用字詞表 (如果有的話) 會套用至該索引上的全文檢索查詢。</span><span class="sxs-lookup"><span data-stu-id="5da10-132">The stoplist associated with a full-text index, if any, is applied to full-text queries on that index.</span></span> <span data-ttu-id="5da10-133">您可以從清單中選取，從索引中移除停用字詞表 **\<OFF>** ，也可以選取不同的停用字詞表; 表示系統停用字詞表 **\<SYSTEM>** 。</span><span class="sxs-lookup"><span data-stu-id="5da10-133">You can remove the stoplist from the index by selecting **\<OFF>** from the list, or you can select a different stoplist; **\<SYSTEM>** indicates the system stoplist.</span></span>  
  
 <span data-ttu-id="5da10-134">**若要建立停用字詞表**</span><span class="sxs-lookup"><span data-stu-id="5da10-134">**To create a stoplist**</span></span>  
  
-   [<span data-ttu-id="5da10-135">設定及管理全文檢索搜尋的停用字詞與停用字詞表</span><span class="sxs-lookup"><span data-stu-id="5da10-135">Configure and Manage Stopwords and Stoplists for Full-Text Search</span></span>](../relational-databases/search/full-text-search.md)  
  
 <span data-ttu-id="5da10-136">**搜尋屬性清單**</span><span class="sxs-lookup"><span data-stu-id="5da10-136">**Search Property List**</span></span>  
 <span data-ttu-id="5da10-137">目前與此全文檢索索引相關聯的搜尋屬性清單 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="5da10-137">The search property list that is currently associated with the full-text index, if any.</span></span> <span data-ttu-id="5da10-138">搜尋屬性清單會指定關聯全文檢索索引擴展時所包含的一組文件屬性。</span><span class="sxs-lookup"><span data-stu-id="5da10-138">A search property list specifies a set of document properties that are included in the associated full-text index when it is populated.</span></span> <span data-ttu-id="5da10-139">如需詳細資訊，請參閱 [使用搜索屬性清單搜索文件屬性](../relational-databases/search/search-document-properties-with-search-property-lists.md)。</span><span class="sxs-lookup"><span data-stu-id="5da10-139">For more information, see [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md).</span></span>  
  
 <span data-ttu-id="5da10-140">**\<Off>** 指出目前沒有與索引相關聯的搜尋屬性清單。</span><span class="sxs-lookup"><span data-stu-id="5da10-140">**\<Off>** indicates that there is currently no search property list associated with the index.</span></span> <span data-ttu-id="5da10-141">您可以從清單中選取，從索引中移除目前的搜尋屬性清單 **\<Off>** ，也可以從清單中選取不同的搜尋屬性清單。</span><span class="sxs-lookup"><span data-stu-id="5da10-141">You can remove the current search property list from the index by selecting **\<Off>** from the list, or you can select a different search property list from the list.</span></span> <span data-ttu-id="5da10-142">這裡只會列出目前資料庫中的搜尋屬性清單。</span><span class="sxs-lookup"><span data-stu-id="5da10-142">Only search property lists in the current database are listed here.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5da10-143">您可以將特定的搜尋屬性清單與相同資料庫中的多個全文檢索索引相關聯。</span><span class="sxs-lookup"><span data-stu-id="5da10-143">You can associate a given search property list with more than one full-text index in the same database.</span></span>  
  
 <span data-ttu-id="5da10-144">**若要建立搜尋屬性清單**</span><span class="sxs-lookup"><span data-stu-id="5da10-144">**To create a search property list**</span></span>  
  
-   [<span data-ttu-id="5da10-145">使用搜索屬性清單搜索文件屬性</span><span class="sxs-lookup"><span data-stu-id="5da10-145">Search Document Properties with Search Property Lists</span></span>](../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
 <span data-ttu-id="5da10-146">**資料表全文檢索項目計數**</span><span class="sxs-lookup"><span data-stu-id="5da10-146">**Table Full-Text Item Count**</span></span>  
 <span data-ttu-id="5da10-147">表示已順利建立全文檢索索引的資料列數。</span><span class="sxs-lookup"><span data-stu-id="5da10-147">Indicates the number of rows that were full-text indexed successfully.</span></span>  
  
 <span data-ttu-id="5da10-148">這個屬性會對應至 OBJECTPROPERTYEX [!INCLUDE[tsql](../includes/tsql-md.md)] 函數所傳回的 `TableFulltextItemCount` 屬性。</span><span class="sxs-lookup"><span data-stu-id="5da10-148">This property corresponds to the `TableFulltextItemCount` property returned by the OBJECTPROPERTYEX [!INCLUDE[tsql](../includes/tsql-md.md)] function.</span></span>  
  
 <span data-ttu-id="5da10-149">**已處理資料表全文檢索文件**</span><span class="sxs-lookup"><span data-stu-id="5da10-149">**Table Full-Text Docs Processed**</span></span>  
 <span data-ttu-id="5da10-150">顯示全文檢索索引啟動之後已經處理的資料列數。</span><span class="sxs-lookup"><span data-stu-id="5da10-150">Displays the number of rows that have been processed since the start of full-text indexing.</span></span> <span data-ttu-id="5da10-151">在建立全文檢索搜尋索引的資料表中，單一資料列的所有資料行都會被視為單一文件的一部分來建立索引。</span><span class="sxs-lookup"><span data-stu-id="5da10-151">In a table that is being indexed for full-text search, all the columns of one row are considered as part of one document to be indexed.</span></span> <span data-ttu-id="5da10-152">不會計算已刪除的資料列。</span><span class="sxs-lookup"><span data-stu-id="5da10-152">Deleted rows are not counted.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5da10-153">0</span><span class="sxs-lookup"><span data-stu-id="5da10-153">0</span></span>|<span data-ttu-id="5da10-154">表示全文檢索索引已完成，而且沒有任何作用中母體擴展。</span><span class="sxs-lookup"><span data-stu-id="5da10-154">Indicates that full-text indexing is completed and there is no active population.</span></span>|  
|<span data-ttu-id="5da10-155">> 0</span><span class="sxs-lookup"><span data-stu-id="5da10-155">> 0</span></span>|<span data-ttu-id="5da10-156">若為作用中母體擴展，表示自從下列任何一項作業以來，插入或更新作業所處理的文件數目：母體擴展、啟用含背景更新索引母體擴展的變更追蹤 (例如自動變更追蹤)、變更全文檢索索引結構描述、重建全文檢索目錄，或重新啟動 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]執行個體等等。</span><span class="sxs-lookup"><span data-stu-id="5da10-156">For an active population, indicates the number of documents processed by insert or update operations since any of the following: a population, enabling of change tracking with background update index population (such as auto change tracking), changing the full-text index schema, rebuilding the full-text catalog, restarting the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and so forth.</span></span>|  
  
 <span data-ttu-id="5da10-157">**資料表全文檢索暫止變更**</span><span class="sxs-lookup"><span data-stu-id="5da10-157">**Table Full-Text Pending Changes**</span></span>  
 <span data-ttu-id="5da10-158">要處理的暫止變更追蹤項目數。</span><span class="sxs-lookup"><span data-stu-id="5da10-158">Number of pending change tracking entries to process.</span></span>  
  
 <span data-ttu-id="5da10-159">0 = 未啟用變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="5da10-159">0 = change tracking is not enabled.</span></span>  
  
 <span data-ttu-id="5da10-160">NULL = 資料表沒有全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="5da10-160">NULL = Table does not have a full-text index.</span></span>  
  
 <span data-ttu-id="5da10-161">**資料表全文檢索失敗計數**</span><span class="sxs-lookup"><span data-stu-id="5da10-161">**Table Full-Text Fail Count**</span></span>  
 <span data-ttu-id="5da10-162">全文檢索搜尋功能尚未建立索引的資料列數。</span><span class="sxs-lookup"><span data-stu-id="5da10-162">The number of rows that full-text search did not index.</span></span>  
  
 <span data-ttu-id="5da10-163">0 = 母體擴展已完成。</span><span class="sxs-lookup"><span data-stu-id="5da10-163">0 = The population has completed.</span></span>  
  
 <span data-ttu-id="5da10-164">\>0 = 下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="5da10-164">\>0 = One of the following:</span></span>  
  
-   <span data-ttu-id="5da10-165">啟動完整、累加或手動更新變更追蹤母體擴展之後，尚未建立索引的文件數目。</span><span class="sxs-lookup"><span data-stu-id="5da10-165">The number of documents that were not indexed since the start of full, incremental, or manual change tracking population.</span></span>  
  
-   <span data-ttu-id="5da10-166">對於背景更新索引的變更追蹤，在開始母體擴展或重新開始母體擴展之後，尚未建立索引的資料列數。</span><span class="sxs-lookup"><span data-stu-id="5da10-166">For change tracking with background update index, the number of rows that were not indexed since the start of the population, or the restart of the population.</span></span> <span data-ttu-id="5da10-167">這可能是結構描述變更、重建目錄、伺服器重新啟動等所造成的。</span><span class="sxs-lookup"><span data-stu-id="5da10-167">This could be caused by a schema change, rebuild of the catalog, server restart, and so on</span></span>  
  
 <span data-ttu-id="5da10-168">**全文檢索索引已啟用**</span><span class="sxs-lookup"><span data-stu-id="5da10-168">**Full-Text Indexing Enabled**</span></span>  
 <span data-ttu-id="5da10-169">指定是否已啟用全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="5da10-169">Specifies whether full-text indexing is enabled.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5da10-170">**True**</span><span class="sxs-lookup"><span data-stu-id="5da10-170">**True**</span></span>|<span data-ttu-id="5da10-171">啟用</span><span class="sxs-lookup"><span data-stu-id="5da10-171">Enabled</span></span>|  
|<span data-ttu-id="5da10-172">**False**</span><span class="sxs-lookup"><span data-stu-id="5da10-172">**False**</span></span>|<span data-ttu-id="5da10-173">已停用</span><span class="sxs-lookup"><span data-stu-id="5da10-173">Disabled</span></span>|  
  
 <span data-ttu-id="5da10-174">**變更追蹤**</span><span class="sxs-lookup"><span data-stu-id="5da10-174">**Change Tracking**</span></span>  
 <span data-ttu-id="5da10-175">指定資料表是否已啟用全文檢索變更追蹤，而且如果有，啟用的是哪種變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="5da10-175">Specifies whether the table has full-text change-tracking enabled, and if so, what kind.</span></span> <span data-ttu-id="5da10-176">全文檢索變更追蹤會在已設定全文檢索索引的資料表或索引檢視表中，維護已經修改之資料列的記錄。</span><span class="sxs-lookup"><span data-stu-id="5da10-176">Full-text change tracking maintains a record of the rows that have been modified in a table or indexed view that has been set up for full-text indexing.</span></span> <span data-ttu-id="5da10-177">這些變更可傳播至全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="5da10-177">These changes can be propagated to the full-text index.</span></span>  
  
 <span data-ttu-id="5da10-178">**[變更追蹤]** 的值如下所示：</span><span class="sxs-lookup"><span data-stu-id="5da10-178">The **Change Tracking** values are as follows:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5da10-179">**關閉**</span><span class="sxs-lookup"><span data-stu-id="5da10-179">**Off**</span></span>|<span data-ttu-id="5da10-180">全文檢索索引不會使用基礎資料的變更來更新。</span><span class="sxs-lookup"><span data-stu-id="5da10-180">The full-text index is not updated with changes to the underlying data.</span></span>|  
|<span data-ttu-id="5da10-181">**手動**</span><span class="sxs-lookup"><span data-stu-id="5da10-181">**Manual**</span></span>|<span data-ttu-id="5da10-182">全文檢索索引不會在基礎資料發生變更時自動更新。</span><span class="sxs-lookup"><span data-stu-id="5da10-182">The full-text index is not updated automatically as changes occur to the underlying data.</span></span> <span data-ttu-id="5da10-183">但是會維護基礎資料的變更，而且您可以使用 SQL Server Agent 來依照排程，</span><span class="sxs-lookup"><span data-stu-id="5da10-183">However, changes to the underlying data are maintained, and you can propagate them to the .</span></span> <span data-ttu-id="5da10-184">或是以手動方式將其傳播到全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="5da10-184">full-text index either on a schedule using SQL Server Agent or manually.</span></span>|  
|<span data-ttu-id="5da10-185">**自動**</span><span class="sxs-lookup"><span data-stu-id="5da10-185">**Automatic**</span></span>|<span data-ttu-id="5da10-186">全文檢索索引會在基底資料表中的基礎資料發生變更時自動更新。</span><span class="sxs-lookup"><span data-stu-id="5da10-186">The full-text index is updated automatically as changes occur to the underlying data in the base table.</span></span>|  
  
 <span data-ttu-id="5da10-187">**重新擴展索引**</span><span class="sxs-lookup"><span data-stu-id="5da10-187">**Repopulate index**</span></span>  
 <span data-ttu-id="5da10-188">按一下即可在結束對話方塊時，針對全文檢索索引啟動母體擴展。</span><span class="sxs-lookup"><span data-stu-id="5da10-188">Click to start a population on the full-text index on exiting the dialog box.</span></span> <span data-ttu-id="5da10-189">請選取下列其中一種母體擴展類型：</span><span class="sxs-lookup"><span data-stu-id="5da10-189">Select one of the following types of population:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5da10-190">**完整**</span><span class="sxs-lookup"><span data-stu-id="5da10-190">**Full**</span></span>|<span data-ttu-id="5da10-191">在資料表的完整母體擴展期間，系統會針對所有資料列建立索引項目。</span><span class="sxs-lookup"><span data-stu-id="5da10-191">During a full population of a table, index entries are built for all the rows.</span></span>|  
|<span data-ttu-id="5da10-192">**增強**</span><span class="sxs-lookup"><span data-stu-id="5da10-192">**Incremental**</span></span>|<span data-ttu-id="5da10-193">累加母體擴展會針對在上一次母體擴展之後或進行時加入、刪除或修改的資料列，更新全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="5da10-193">Incremental population updates the full-text index for rows added, deleted, or modified after the last population, or while the last population was in progress.</span></span> <span data-ttu-id="5da10-194">若要執行累加母體擴展，基底資料表必須包含 `timestamp` 資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="5da10-194">Performing an incremental population requires that the base table contain a column of the `timestamp` data type.</span></span>|  
|<span data-ttu-id="5da10-195">**更新**</span><span class="sxs-lookup"><span data-stu-id="5da10-195">**Update**</span></span>|<span data-ttu-id="5da10-196">每當修改基底資料表中的資料時，就會更新全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="5da10-196">The full-text index is updated whenever the data in the base table is modified.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5da10-197">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5da10-197">See Also</span></span>  
 [<span data-ttu-id="5da10-198">全文檢索搜尋使用者入門</span><span class="sxs-lookup"><span data-stu-id="5da10-198">Get Started with Full-Text Search</span></span>](../relational-databases/search/get-started-with-full-text-search.md)  
  
  
