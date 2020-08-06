---
title: 管理全文檢索索引 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: 28ff17dc-172b-4ac4-853f-990b5dc02fd1
author: rothja
ms.author: jroth
ms.openlocfilehash: 92eb3669930407b359b8eeed4d3df2e802bdacdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607021"
---
# <a name="manage-full-text-indexes"></a><span data-ttu-id="49537-102">管理全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="49537-102">Manage Full-Text Indexes</span></span>
     
##  <a name="viewing-and-changing-the-properties-of-a-full-text-index"></a><a name="view"></a><span data-ttu-id="49537-103">查看和變更全文檢索索引的屬性</span><span class="sxs-lookup"><span data-stu-id="49537-103">Viewing and Changing the Properties of a Full-Text Index</span></span>  
  
#### <a name="to-view-or-change-the-properties-of-a-full-text-index-in-management-studio"></a><span data-ttu-id="49537-104">在 Management Studio 中檢視或變更全文檢索索引的屬性</span><span class="sxs-lookup"><span data-stu-id="49537-104">To view or change the properties of a full-text index in Management Studio</span></span>  
  
1.  <span data-ttu-id="49537-105">在 [物件總管] 中，展開伺服器。</span><span class="sxs-lookup"><span data-stu-id="49537-105">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="49537-106">展開 [資料庫]，然後展開包含全文檢索索引的資料庫。</span><span class="sxs-lookup"><span data-stu-id="49537-106">Expand **Databases**, and then expand the database that contains the full-text index.</span></span>  
  
3.  <span data-ttu-id="49537-107">展開 **[資料表]** 。</span><span class="sxs-lookup"><span data-stu-id="49537-107">Expand **Tables**.</span></span>  
  
4.  <span data-ttu-id="49537-108">以滑鼠右鍵按一下已定義全文檢索索引的資料表、選取 [全文檢索索引]，然後按一下 [全文檢索索引] 內容功能表上的 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="49537-108">Right-click the table on which the full-text index is defined, select **Full-Text index**, and on the **Full-Text index** context menu, click **Properties**.</span></span> <span data-ttu-id="49537-109">這樣就會開啟 [全文檢索索引屬性]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="49537-109">This opens the **Full-text index Properties** dialog box.</span></span>  
  
5.  <span data-ttu-id="49537-110">在 **[選取頁面]** 窗格中，您可以選取下列任何頁面：</span><span class="sxs-lookup"><span data-stu-id="49537-110">In the **Select a page** pane, you can select any of the following pages:</span></span>  
  
    |<span data-ttu-id="49537-111">頁面</span><span class="sxs-lookup"><span data-stu-id="49537-111">Page</span></span>|<span data-ttu-id="49537-112">描述</span><span class="sxs-lookup"><span data-stu-id="49537-112">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="49537-113">**一般**</span><span class="sxs-lookup"><span data-stu-id="49537-113">**General**</span></span>|<span data-ttu-id="49537-114">顯示全文檢索索引的基本屬性。</span><span class="sxs-lookup"><span data-stu-id="49537-114">Displays basic properties of the full-text index.</span></span> <span data-ttu-id="49537-115">這些屬性包括許多可修改的屬性和一些無法變更的屬性，例如資料庫名稱、資料表名稱，以及全文檢索索引鍵資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="49537-115">These include several modifiable properties and a number of unchangeable properties such as database name, table name, and the name of full-text key column.</span></span> <span data-ttu-id="49537-116">可修改的屬性包括：</span><span class="sxs-lookup"><span data-stu-id="49537-116">The modifiable properties are:</span></span><br /><br /> <span data-ttu-id="49537-117">**全文檢索索引停用字詞表**</span><span class="sxs-lookup"><span data-stu-id="49537-117">**Full-Text Index Stoplist**</span></span><br /><br /> <span data-ttu-id="49537-118">**全文檢索索引已啟用**</span><span class="sxs-lookup"><span data-stu-id="49537-118">**Full-Text Indexing Enabled**</span></span><br /><br /> <span data-ttu-id="49537-119">**變更追蹤**</span><span class="sxs-lookup"><span data-stu-id="49537-119">**Change Tracking**</span></span><br /><br /> <span data-ttu-id="49537-120">**搜尋屬性清單**</span><span class="sxs-lookup"><span data-stu-id="49537-120">**Search Property List**</span></span><br /><br /> <br /><br /> <span data-ttu-id="49537-121">如需詳細資訊，請參閱[全文檢索搜尋 &#40;一般頁面&#41;](full-text-index-properties-general-page.md)。</span><span class="sxs-lookup"><span data-stu-id="49537-121">For more information, see [Full-Text Index Properties &#40;General Page&#41;](full-text-index-properties-general-page.md).</span></span>|  
    |<span data-ttu-id="49537-122">**資料行**</span><span class="sxs-lookup"><span data-stu-id="49537-122">**Columns**</span></span>|<span data-ttu-id="49537-123">顯示可用於全文檢索索引的資料表資料行。</span><span class="sxs-lookup"><span data-stu-id="49537-123">Displays the table columns that are available for full-text indexing.</span></span> <span data-ttu-id="49537-124">系統會針對選取的資料行建立全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="49537-124">The selected column or columns are full-text indexed.</span></span> <span data-ttu-id="49537-125">您可以選取任意數目的可用資料行，以便包含在全文檢索索引中。</span><span class="sxs-lookup"><span data-stu-id="49537-125">You can select as many of the available columns as you want to include in the full-text index.</span></span> <span data-ttu-id="49537-126">如需詳細資訊，請參閱[全文檢索搜尋 &#40;資料行頁面&#41;](../../2014/database-engine/full-text-index-properties-columns-page.md)。</span><span class="sxs-lookup"><span data-stu-id="49537-126">For more information, see [Full-Text Index Properties &#40;Columns Page&#41;](../../2014/database-engine/full-text-index-properties-columns-page.md).</span></span>|  
    |<span data-ttu-id="49537-127">**排程**</span><span class="sxs-lookup"><span data-stu-id="49537-127">**Schedules**</span></span>|<span data-ttu-id="49537-128">您可以使用這個頁面來建立或管理 SQL Server Agent 作業的排程，以便針對全文檢索索引母體擴展啟動累加資料表母體擴展。</span><span class="sxs-lookup"><span data-stu-id="49537-128">Use this page to create or manage schedules for a SQL Server Agent job that starts an incremental table population for the full-text index populations.</span></span> <span data-ttu-id="49537-129">如需詳細資訊，請參閱 [擴展全文檢索索引](../relational-databases/indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="49537-129">For more information, see [Populate Full-Text Indexes](../relational-databases/indexes/indexes.md).</span></span><br /><br /> <span data-ttu-id="49537-130"><strong> \* \* 重要 \* 事項 \* </strong> ：結束 [**全文檢索索引屬性**] 對話方塊之後，任何新建立的排程都會與 SQL Server Agent 作業相關聯， (在*database_name*上啟動累加資料表擴展。*table_name*) 。</span><span class="sxs-lookup"><span data-stu-id="49537-130"><strong>\*\* Important \*\*</strong> After you exit the **Full-Text Index Properties** dialog box, any newly created schedule is associated with a SQL Server Agent job (Start Incremental Table Population on *database_name*.*table_name*).</span></span>|  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)] <span data-ttu-id="49537-131">儲存任何變更並結束 [全文檢索索引屬性]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="49537-131">to save any changes and exit the **Full-text index Properties** dialog box.</span></span>  
  
##  <a name="viewing-the-properties-of-indexed-tables-and-columns"></a><a name="props"></a><span data-ttu-id="49537-132">查看索引資料表和資料行的屬性</span><span class="sxs-lookup"><span data-stu-id="49537-132">Viewing the Properties of Indexed Tables and Columns</span></span>  
 <span data-ttu-id="49537-133">您可以使用許多 [!INCLUDE[tsql](../includes/tsql-md.md)] 函數 (例如 OBJECTPROPERTYEX) 以取得各種全文檢索索引屬性的值。</span><span class="sxs-lookup"><span data-stu-id="49537-133">Several [!INCLUDE[tsql](../includes/tsql-md.md)] functions such as OBJECTPROPERTYEX can be used to obtain the value of various full-text indexing properties.</span></span> <span data-ttu-id="49537-134">此資訊適用於管理和疑難排解全文檢索搜尋。</span><span class="sxs-lookup"><span data-stu-id="49537-134">This information is useful for administering and troubleshooting full-text search.</span></span>  
  
 <span data-ttu-id="49537-135">下表列出索引資料表和資料行的相關全文檢索屬性及其相關的 [!INCLUDE[tsql](../includes/tsql-md.md)] 函數。</span><span class="sxs-lookup"><span data-stu-id="49537-135">The following table lists the full-text properties related to indexed tables and columns and their related [!INCLUDE[tsql](../includes/tsql-md.md)] functions.</span></span>  
  
|<span data-ttu-id="49537-136">屬性</span><span class="sxs-lookup"><span data-stu-id="49537-136">Property</span></span>|<span data-ttu-id="49537-137">描述</span><span class="sxs-lookup"><span data-stu-id="49537-137">Description</span></span>|<span data-ttu-id="49537-138">函式</span><span class="sxs-lookup"><span data-stu-id="49537-138">Function</span></span>|  
|--------------|-----------------|--------------|  
|`FullTextTypeColumn`|<span data-ttu-id="49537-139">在資料表中，用來保存資料行文件類型資訊的 TYPE COLUMN。</span><span class="sxs-lookup"><span data-stu-id="49537-139">TYPE COLUMN in the table that holds the document type information of the column.</span></span>|[<span data-ttu-id="49537-140">COLUMNPROPERTY</span><span class="sxs-lookup"><span data-stu-id="49537-140">COLUMNPROPERTY</span></span>](/sql/t-sql/functions/columnproperty-transact-sql)|  
|`IsFulltextIndexed`|<span data-ttu-id="49537-141">資料行是否已啟用全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="49537-141">Whether a column has been enabled for full-text indexing.</span></span>|<span data-ttu-id="49537-142">COLUMNPROPERTY</span><span class="sxs-lookup"><span data-stu-id="49537-142">COLUMNPROPERTY</span></span>|  
|`IsFulltextKey`|<span data-ttu-id="49537-143">索引是否為資料表的全文檢索索引鍵。</span><span class="sxs-lookup"><span data-stu-id="49537-143">Whether the index is the full-text key for a table.</span></span>|[<span data-ttu-id="49537-144">INDEXPROPERTY</span><span class="sxs-lookup"><span data-stu-id="49537-144">INDEXPROPERTY</span></span>](/sql/t-sql/functions/indexproperty-transact-sql)|  
|<span data-ttu-id="49537-145">**TableFulltextBackgroundUpdateIndexOn**</span><span class="sxs-lookup"><span data-stu-id="49537-145">**TableFulltextBackgroundUpdateIndexOn**</span></span>|<span data-ttu-id="49537-146">資料表是否擁有全文檢索的背景更新索引。</span><span class="sxs-lookup"><span data-stu-id="49537-146">Whether a table has full-text background update indexing.</span></span>|[<span data-ttu-id="49537-147">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="49537-147">OBJECTPROPERTYEX</span></span>](/sql/t-sql/functions/objectproperty-transact-sql)|  
|`TableFulltextCatalogId`|<span data-ttu-id="49537-148">資料表之全文檢索索引資料所在的全文檢索目錄識別碼。</span><span class="sxs-lookup"><span data-stu-id="49537-148">Full-text catalog ID in which the full-text index data for the table resides.</span></span>|<span data-ttu-id="49537-149">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="49537-149">OBJECTPROPERTYEX</span></span>|  
|`TableFulltextChangeTrackingOn`|<span data-ttu-id="49537-150">資料表是否已啟用全文檢索變更追蹤。</span><span class="sxs-lookup"><span data-stu-id="49537-150">Whether a table has full-text change-tracking enabled.</span></span>|<span data-ttu-id="49537-151">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="49537-151">OBJECTPROPERTYEX</span></span>|  
|`TableFulltextDocsProcessed`|<span data-ttu-id="49537-152">全文檢索索引啟動之後所處理的資料列數。</span><span class="sxs-lookup"><span data-stu-id="49537-152">Number of rows processed since the start of full-text indexing.</span></span>|<span data-ttu-id="49537-153">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="49537-153">OBJECTPROPERTYEX</span></span>|  
|<span data-ttu-id="49537-154">**TableFulltextFailCount**</span><span class="sxs-lookup"><span data-stu-id="49537-154">**TableFulltextFailCount**</span></span>|<span data-ttu-id="49537-155">全文檢索搜尋未建立索引的資料列數。</span><span class="sxs-lookup"><span data-stu-id="49537-155">Number of rows Full-Text Search did not index.</span></span>|<span data-ttu-id="49537-156">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="49537-156">OBJECTPROPERTYEX</span></span>|  
|<span data-ttu-id="49537-157">**TableFulltextItemCount**</span><span class="sxs-lookup"><span data-stu-id="49537-157">**TableFulltextItemCount**</span></span>|<span data-ttu-id="49537-158">已順利建立全文檢索索引的資料列數。</span><span class="sxs-lookup"><span data-stu-id="49537-158">Number of rows that were successfully full-text indexed.</span></span>|<span data-ttu-id="49537-159">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="49537-159">OBJECTPROPERTYEX</span></span>|  
|`TableFulltextKeyColumn`|<span data-ttu-id="49537-160">全文檢索唯一索引鍵資料行的資料行識別碼。</span><span class="sxs-lookup"><span data-stu-id="49537-160">The column ID of the full-text unique key column.</span></span>|<span data-ttu-id="49537-161">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="49537-161">OBJECTPROPERTYEX</span></span>|  
|`TableFullTextMergeStatus`|<span data-ttu-id="49537-162">具有全文檢索索引的資料表目前是否正在合併。</span><span class="sxs-lookup"><span data-stu-id="49537-162">Whether a table that has a full-text index is currently in merging.</span></span>|<span data-ttu-id="49537-163">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="49537-163">OBJECTPROPERTYEX</span></span>|  
|<span data-ttu-id="49537-164">**TableFulltextPendingChanges**</span><span class="sxs-lookup"><span data-stu-id="49537-164">**TableFulltextPendingChanges**</span></span>|<span data-ttu-id="49537-165">要處理的暫止變更追蹤項目數。</span><span class="sxs-lookup"><span data-stu-id="49537-165">Number of pending change tracking entries to process.</span></span>|<span data-ttu-id="49537-166">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="49537-166">OBJECTPROPERTYEX</span></span>|  
|`TableFulltextPopulateStatus`|<span data-ttu-id="49537-167">全文檢索資料表的母體擴展狀態。</span><span class="sxs-lookup"><span data-stu-id="49537-167">Population status of a full-text table.</span></span>|<span data-ttu-id="49537-168">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="49537-168">OBJECTPROPERTYEX</span></span>|  
|`TableHasActiveFulltextIndex`|<span data-ttu-id="49537-169">資料表是否擁有使用中全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="49537-169">Whether a table has an active full-text index.</span></span>|<span data-ttu-id="49537-170">OBJECTPROPERTYEX</span><span class="sxs-lookup"><span data-stu-id="49537-170">OBJECTPROPERTYEX</span></span>|  
  
##  <a name="getting-information-about-the-full-text-key-column"></a><a name="key"></a><span data-ttu-id="49537-171">取得全文檢索索引鍵資料行的相關資訊</span><span class="sxs-lookup"><span data-stu-id="49537-171">Getting Information about the Full-Text Key Column</span></span>  
 <span data-ttu-id="49537-172">一般而言，CONTAINSTABLE 或 FREETEXTTABLE 資料列集值函數的結果必須與基底資料表聯結。</span><span class="sxs-lookup"><span data-stu-id="49537-172">Typically, the result of CONTAINSTABLE or FREETEXTTABLE rowset-valued functions need to be joined with the base table.</span></span> <span data-ttu-id="49537-173">在這種情況下，您必須知道唯一索引鍵資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="49537-173">In such cases, you need to know the unique key column name.</span></span> <span data-ttu-id="49537-174">您可以查詢給定的唯一索引是否當做全文檢索索引鍵使用，而且可以取得全文檢索索引鍵資料行的識別碼。</span><span class="sxs-lookup"><span data-stu-id="49537-174">You can inquire whether a given unique index is used as the full-text key, and you can obtain the identifier of the full-text key column.</span></span>  
  
#### <a name="to-inquire-whether-a-given-unique-index-is-used-as-the-full-text-key-column"></a><span data-ttu-id="49537-175">若要查詢給定的唯一索引是否當做全文檢索索引鍵資料行使用</span><span class="sxs-lookup"><span data-stu-id="49537-175">To inquire whether a given unique index is used as the full-text key column</span></span>  
  
1.  <span data-ttu-id="49537-176">使用 [SELECT](/sql/t-sql/queries/select-transact-sql) 陳述式來呼叫 [INDEXPROPERTY](/sql/t-sql/functions/indexproperty-transact-sql) 函數。</span><span class="sxs-lookup"><span data-stu-id="49537-176">Use a [SELECT](/sql/t-sql/queries/select-transact-sql) statement to call the [INDEXPROPERTY](/sql/t-sql/functions/indexproperty-transact-sql) function.</span></span> <span data-ttu-id="49537-177">在函式呼叫中，使用 OBJECT_ID 函數，將資料表的名稱 (*table_name*) 轉換成資料表識別碼、指定資料表的唯一索引名稱，以及指定 `IsFulltextKey` 索引屬性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="49537-177">In the function call use the OBJECT_ID function to convert the name of the table (*table_name*) into the table ID, specify the name of a unique index for the table, and specify the `IsFulltextKey` index property, as follows:</span></span>  
  
    ```  
    SELECT INDEXPROPERTY( OBJECT_ID('table_name'), 'index_name',  'IsFulltextKey' );  
    ```  
  
     <span data-ttu-id="49537-178">如果索引是用來強制全文檢索索引鍵資料行的唯一性，這個陳述式就會傳回 1。如果不是，便傳回 0。</span><span class="sxs-lookup"><span data-stu-id="49537-178">This statement returns 1 if the index is used to enforce uniqueness of the full-text key column and 0 if it is not.</span></span>  
  
 <span data-ttu-id="49537-179">**範例**</span><span class="sxs-lookup"><span data-stu-id="49537-179">**Example**</span></span>  
  
 <span data-ttu-id="49537-180">下列範例會查詢 `PK_Document_DocumentID` 索引是否用來強制全文檢索索引鍵資料行的唯一性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="49537-180">The following example inquires whether the `PK_Document_DocumentID` index is used to enforce the uniqueness of the full-text key column, as follows:</span></span>  
  
```  
USE AdventureWorks  
GO  
SELECT INDEXPROPERTY ( OBJECT_ID('Production.Document'), 'PK_Document_DocumentID',  'IsFulltextKey' )  
```  
  
 <span data-ttu-id="49537-181">如果 `PK_Document_DocumentID` 索引是用來強制全文檢索索引鍵資料行的唯一性，這個範例就會傳回 1。</span><span class="sxs-lookup"><span data-stu-id="49537-181">This example returns 1 if the `PK_Document_DocumentID` index is used to enforce uniqueness of the full-text key column.</span></span> <span data-ttu-id="49537-182">否則，它會傳回 0 或 NULL。</span><span class="sxs-lookup"><span data-stu-id="49537-182">Otherwise, it returns 0 or NULL.</span></span> <span data-ttu-id="49537-183">NULL 表示您正在使用無效的索引名稱、索引名稱沒有對應至資料表，或者資料表不存在等。</span><span class="sxs-lookup"><span data-stu-id="49537-183">NULL implies you are using an invalid index name, the index name does not correspond to the table, the table does not exist, or so forth.</span></span>  
  
#### <a name="to-find-the-identifier-of-the-full-text-key-column"></a><span data-ttu-id="49537-184">尋找全文檢索索引鍵資料行的識別碼</span><span class="sxs-lookup"><span data-stu-id="49537-184">To find the identifier of the full-text key column</span></span>  
  
1.  <span data-ttu-id="49537-185">每個啟用全文檢索的資料表都具有一個用來強制資料表之唯一資料列的資料行 (*unique\*\*key column*)。</span><span class="sxs-lookup"><span data-stu-id="49537-185">Each full-text enabled table has a column that is used to enforce unique rows for the table (the *unique\*\*key column*).</span></span> <span data-ttu-id="49537-186">從 OBJECTPROPERTYEX 函數中取得的 `TableFulltextKeyColumn` 屬性會包含唯一索引鍵資料行的資料行識別碼。</span><span class="sxs-lookup"><span data-stu-id="49537-186">The `TableFulltextKeyColumn` property, obtained from the OBJECTPROPERTYEX function, contains the column ID of the unique key column.</span></span>  
  
     <span data-ttu-id="49537-187">若要取得這個識別碼，您可以使用 SELECT 陳述式來呼叫 OBJECTPROPERTYEX 函數。</span><span class="sxs-lookup"><span data-stu-id="49537-187">To obtain this identifier, you can use a SELECT statement to call the OBJECTPROPERTYEX function.</span></span> <span data-ttu-id="49537-188">使用 OBJECT_ID 函數，將資料表的名稱 (*table_name*) 轉換成資料表識別碼，並指定 `TableFulltextKeyColumn` 屬性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="49537-188">Use the OBJECT_ID function to convert the name of the table (*table_name*) into the table ID and specify the `TableFulltextKeyColumn` property, as follows:</span></span>  
  
    ```  
    SELECT OBJECTPROPERTYEX(OBJECT_ID( 'table_name'), 'TableFulltextKeyColumn' ) AS 'Column Identifier';  
    ```  
  
 <span data-ttu-id="49537-189">**範例**</span><span class="sxs-lookup"><span data-stu-id="49537-189">**Examples**</span></span>  
  
 <span data-ttu-id="49537-190">下列範例會傳回全文檢索索引鍵資料行的識別碼或 NULL。</span><span class="sxs-lookup"><span data-stu-id="49537-190">The following example returns the identifier of the full-text key column or NULL.</span></span> <span data-ttu-id="49537-191">NULL 表示您正在使用無效的索引名稱、索引名稱沒有對應至資料表，或者資料表不存在等。</span><span class="sxs-lookup"><span data-stu-id="49537-191">NULL implies that you are using an invalid index name, the index name does not correspond to the table, the table does not exist, or so forth.</span></span>  
  
```  
USE AdventureWorks;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID('Production.Document'), 'TableFulltextKeyColumn');  
GO  
```  
  
 <span data-ttu-id="49537-192">下列範例顯示如何使用唯一索引鍵資料行的識別碼，以取得資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="49537-192">The following example shows how to use the identifier of the unique key column to obtain the name of the column.</span></span>  
  
```  
USE AdventureWorks;  
GO  
DECLARE @key_column sysname  
SET @key_column = Col_Name(Object_Id('Production.Document'),  
ObjectProperty(Object_id('Production.Document'),  
'TableFulltextKeyColumn')   
)  
SELECT @key_column AS 'Unique Key Column';  
GO  
```  
  
 <span data-ttu-id="49537-193">這個範例會傳回名為 `Unique Key Column`的結果集資料行，其中顯示包含 Document 資料表之唯一索引鍵資料行名稱的單一資料列 DocumentID。</span><span class="sxs-lookup"><span data-stu-id="49537-193">This example returns a result set column named `Unique Key Column`, which displays a single row containing the name of the unique key column of the Document table, DocumentID.</span></span> <span data-ttu-id="49537-194">請注意，如果這個查詢包含無效的索引名稱、索引名稱沒有對應至資料表，或者資料表不存在等，它就會傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="49537-194">Note that if this query contained an invalid index name, the index name did not correspond to the table, the table did not exist, and so forth, it would return NULL.</span></span>  
  
##  <a name="disabling-or-re-enabling-a-table-for-full-text-indexing"></a><a name="disable"></a><span data-ttu-id="49537-195">停用或重新啟用全文檢索索引的資料表</span><span class="sxs-lookup"><span data-stu-id="49537-195">Disabling or Re-enabling a Table for Full-Text Indexing</span></span>  
 <span data-ttu-id="49537-196">在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中，所有使用者建立的資料庫預設都會啟用全文檢索。</span><span class="sxs-lookup"><span data-stu-id="49537-196">In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], all user-created databases are full-text enabled by default.</span></span> <span data-ttu-id="49537-197">此外，個別資料表也會在建立全文檢索索引並將資料行加入索引中後，立即自動啟用全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="49537-197">Additionally, an individual table is automatically enabled for full-text indexing as soon as a full-text index is created on it and a column is added to the index.</span></span> <span data-ttu-id="49537-198">從全文檢索索引中卸除最後一個資料行之後，資料表便會自動停用全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="49537-198">A table is automatically disabled for full-text indexing when the last column is dropped from its full-text index.</span></span>  
  
 <span data-ttu-id="49537-199">在具有全文檢索索引的資料表上，您可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]來手動為資料表停用或重新啟用全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="49537-199">On a table that has a full-text index, you can manually disable or re-enable a table for full-text indexing using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-enable-a-table-for-full-text-indexing"></a><span data-ttu-id="49537-200">為資料表啟用全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="49537-200">To enable a table for full-text indexing</span></span>  
  
1.  <span data-ttu-id="49537-201">展開伺服器群組、展開 [資料庫]  ，再展開包含您要啟用全文檢索索引之資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="49537-201">Expand the server group, expand **Databases**, and expand the database that contains the table you want to enable for full-text indexing.</span></span>  
  
2.  <span data-ttu-id="49537-202">展開 [資料表]  ，然後以滑鼠右鍵按一下您想要停用或重新啟用全文檢索索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="49537-202">Expand **Tables**, and right-click the table that you want to disable or re-enable for full-text indexing.</span></span>  
  
3.  <span data-ttu-id="49537-203">選取 [全文檢索索引]  ，然後按一下 [停用全文檢索索引]  或 [啟用全文檢索索引]  。</span><span class="sxs-lookup"><span data-stu-id="49537-203">Select **Full-Text index**, and then click **Disable Full-Text index** or **Enable Full-Text index**.</span></span>  
  
##  <a name="removing-a-full-text-index-from-a-table"></a><a name="remove"></a><span data-ttu-id="49537-204">從資料表移除全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="49537-204">Removing a Full-Text Index from a Table</span></span>  
  
#### <a name="to-remove-a-full-text-index-from-a-table"></a><span data-ttu-id="49537-205">移除資料表的全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="49537-205">To remove a full-text index from a table</span></span>  
  
1.  <span data-ttu-id="49537-206">在 [物件總管] 中，以滑鼠右鍵按一下含有您要移除其全文檢索索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="49537-206">In Object Explorer, right-click the table that has the full-text index that you want to delete.</span></span>  
  
2.  <span data-ttu-id="49537-207">選取 [刪除全文檢索索引]  。</span><span class="sxs-lookup"><span data-stu-id="49537-207">Select **Delete Full-Text index**.</span></span>  
  
3.  <span data-ttu-id="49537-208">出現提示要您確認是否要刪除全文檢索索引時，按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="49537-208">When prompted, click **OK** to confirm that you want to delete the full-text index.</span></span>  
  
  
