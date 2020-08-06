---
title: 建立篩選的索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- filtered indexes [SQL Server], about filtered indexes
- designing indexes [SQL Server], filtered
- filtered indexes [SQL Server]
- nonclustered indexes [SQL Server], filtered
- indexes [SQL Server], filtered
ms.assetid: 25e1fcc5-45d7-4c53-8c79-5493dfaa1c74
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 77cf641ca84181496f26a995244029d0525ade63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708322"
---
# <a name="create-filtered-indexes"></a><span data-ttu-id="fa4b2-102">建立篩選的索引</span><span class="sxs-lookup"><span data-stu-id="fa4b2-102">Create Filtered Indexes</span></span>
  <span data-ttu-id="fa4b2-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中建立篩選索引。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-103">This topic describes how to create a filtered index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="fa4b2-104">篩選索引是最佳化的非叢集索引，特別適合涵蓋從妥善定義的資料子集選取而來的查詢。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-104">A filtered index is an optimized nonclustered index especially suited to cover queries that select from a well-defined subset of data.</span></span> <span data-ttu-id="fa4b2-105">篩選索引會使用篩選述詞對資料表中的部分資料列進行索引。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-105">It uses a filter predicate to index a portion of rows in the table.</span></span> <span data-ttu-id="fa4b2-106">與完整資料表索引相較，設計良好的篩選索引可以提升查詢效能、降低索引維護成本和儲存成本。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-106">A well-designed filtered index can improve query performance as well as reduce index maintenance and storage costs compared with full-table indexes.</span></span>  
  
 <span data-ttu-id="fa4b2-107">篩選索引可以提供全資料表索引所不及的下列優勢：</span><span class="sxs-lookup"><span data-stu-id="fa4b2-107">Filtered indexes can provide the following advantages over full-table indexes:</span></span>  
  
-   <span data-ttu-id="fa4b2-108">**提升的查詢效能和計畫品質**</span><span class="sxs-lookup"><span data-stu-id="fa4b2-108">**Improved query performance and plan quality**</span></span>  
  
     <span data-ttu-id="fa4b2-109">設計良好的篩選索引可以提升查詢效能和執行計畫品質，因為它比全資料表的非叢集索引來得小，且具有篩選統計資料。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-109">A well-designed filtered index improves query performance and execution plan quality because it is smaller than a full-table nonclustered index and has filtered statistics.</span></span> <span data-ttu-id="fa4b2-110">篩選統計資料比全資料表統計資料更為正確，因為僅涵蓋篩選索引中的資料列。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-110">The filtered statistics are more accurate than full-table statistics because they cover only the rows in the filtered index.</span></span>  
  
-   <span data-ttu-id="fa4b2-111">**降低的索引維護成本**</span><span class="sxs-lookup"><span data-stu-id="fa4b2-111">**Reduced index maintenance costs**</span></span>  
  
     <span data-ttu-id="fa4b2-112">只有在資料操作語言 (DML) 陳述式影響到索引中的資料時，才會對索引進行維護。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-112">An index is maintained only when data manipulation language (DML) statements affect the data in the index.</span></span> <span data-ttu-id="fa4b2-113">與完整資料表的非叢集索引相較，篩選索引可以降低維護成本，因為後者較小且僅會在索引中的資料已變更時才會進行維護。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-113">A filtered index reduces index maintenance costs compared with a full-table nonclustered index because it is smaller and is only maintained when the data in the index is changed.</span></span> <span data-ttu-id="fa4b2-114">篩選索引的數量可能很多，特別是當其包含不常變更的資料時。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-114">It is possible to have a large number of filtered indexes, especially when they contain data that is changed infrequently.</span></span> <span data-ttu-id="fa4b2-115">同樣地，如果篩選索引僅包含經常修改的資料，則因為索引的大小較小，更新統計資料的成本就會下降。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-115">Similarly, if a filtered index contains only the frequently modified data, the smaller size of the index reduces the cost of updating the statistics.</span></span>  
  
-   <span data-ttu-id="fa4b2-116">**降低的索引儲存成本**</span><span class="sxs-lookup"><span data-stu-id="fa4b2-116">**Reduced index storage costs**</span></span>  
  
     <span data-ttu-id="fa4b2-117">在不需要全資料表索引時，建立篩選索引可以縮減非叢集索引的磁碟儲存量。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-117">Creating a filtered index can reduce disk storage for nonclustered indexes when a full-table index is not necessary.</span></span> <span data-ttu-id="fa4b2-118">您可以使用多個篩選索引來取代全資料表的非叢集索引，而不會大幅增加儲存需求。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-118">You can replace a full-table nonclustered index with multiple filtered indexes without significantly increasing the storage requirements.</span></span>  
  
 <span data-ttu-id="fa4b2-119">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="fa4b2-119">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fa4b2-120">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="fa4b2-120">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fa4b2-121">設計考量</span><span class="sxs-lookup"><span data-stu-id="fa4b2-121">Design Considerations</span></span>](#Design)  
  
     [<span data-ttu-id="fa4b2-122">限制事項</span><span class="sxs-lookup"><span data-stu-id="fa4b2-122">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="fa4b2-123">安全性</span><span class="sxs-lookup"><span data-stu-id="fa4b2-123">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fa4b2-124">**使用下列方法建立篩選的索引：**</span><span class="sxs-lookup"><span data-stu-id="fa4b2-124">**To create a filtered index, using:**</span></span>  
  
     [<span data-ttu-id="fa4b2-125">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fa4b2-125">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="fa4b2-126">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fa4b2-126">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fa4b2-127">開始之前</span><span class="sxs-lookup"><span data-stu-id="fa4b2-127">Before You Begin</span></span>  
  
###  <a name="design-considerations"></a><a name="Design"></a> <span data-ttu-id="fa4b2-128">設計考量</span><span class="sxs-lookup"><span data-stu-id="fa4b2-128">Design Considerations</span></span>  
  
-   <span data-ttu-id="fa4b2-129">當資料行僅具有少數的查詢相關值時，可以在值的子集上建立篩選索引。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-129">When a column only has a small number of relevant values for queries, you can create a filtered index on the subset of values.</span></span> <span data-ttu-id="fa4b2-130">例如，當資料行中的值大部分都是 NULL 且查詢只會從非 NULL 值進行選取時，您可以針對非 NULL 的資料列建立篩選索引。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-130">For example, when the values in a column are mostly NULL and the query selects only from the non-NULL values, you can create a filtered index for the non-NULL data rows.</span></span> <span data-ttu-id="fa4b2-131">所產生的索引比在相同的索引鍵資料行上定義的全資料表非叢集索引還小，維護成本也比較低。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-131">The resulting index will be smaller and cost less to maintain than a full-table nonclustered index defined on the same key columns.</span></span>  
  
-   <span data-ttu-id="fa4b2-132">當資料表具有異質資料列時，您可以針對一或多個資料類別建立篩選索引。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-132">When a table has heterogeneous data rows, you can create a filtered index for one or more categories of data.</span></span> <span data-ttu-id="fa4b2-133">這會將查詢焦點縮小為資料表的特定區域，改善這些資料列的查詢效能。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-133">This can improve the performance of queries on these data rows by narrowing the focus of a query to a specific area of the table.</span></span> <span data-ttu-id="fa4b2-134">同樣地，所產生的索引比完整資料表非叢集索引還小，維護成本也比較低。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-134">Again, the resulting index will be smaller and cost less to maintain than a full-table nonclustered index.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="fa4b2-135">限制事項</span><span class="sxs-lookup"><span data-stu-id="fa4b2-135">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="fa4b2-136">您無法在檢視上建立篩選索引；</span><span class="sxs-lookup"><span data-stu-id="fa4b2-136">You cannot create a filtered index on a view.</span></span> <span data-ttu-id="fa4b2-137">不過，如果在檢視中參考的資料表上定義篩選索引，則可為查詢最佳化工具提供多項優點。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-137">However, the query optimizer can benefit from a filtered index defined on a table that is referenced in a view.</span></span> <span data-ttu-id="fa4b2-138">如果查詢結果會是正確的，則查詢最佳化工具會針對從檢視進行選取的查詢考慮篩選索引。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-138">The query optimizer considers a filtered index for a query that selects from a view if the query results will be correct.</span></span>  
  
-   <span data-ttu-id="fa4b2-139">篩選索引具有索引檢視表所不及的下列優勢：</span><span class="sxs-lookup"><span data-stu-id="fa4b2-139">Filtered indexes have the following advantages over indexed views:</span></span>  
  
    -   <span data-ttu-id="fa4b2-140">降低的索引維護成本。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-140">Reduced index maintenance costs.</span></span> <span data-ttu-id="fa4b2-141">例如，相較於索引檢視表而言，查詢處理器會使用較少的 CPU 資源來更新篩選索引。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-141">For example, the query processor uses fewer CPU resources to update a filtered index than an indexed view.</span></span>  
  
    -   <span data-ttu-id="fa4b2-142">改善的計畫品質。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-142">Improved plan quality.</span></span> <span data-ttu-id="fa4b2-143">例如，在查詢編譯期間，查詢最佳化工具考慮使用篩選索引的情況會比對等的索引檢視表更多。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-143">For example, during query compilation, the query optimizer considers using a filtered index in more situations than the equivalent indexed view.</span></span>  
  
    -   <span data-ttu-id="fa4b2-144">線上索引重建。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-144">Online index rebuilds.</span></span> <span data-ttu-id="fa4b2-145">您可以在篩選索引可用於查詢時，重建篩選索引。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-145">You can rebuild filtered indexes while they are available for queries.</span></span> <span data-ttu-id="fa4b2-146">線上索引重建不支援索引檢視表。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-146">Online index rebuilds are not supported for indexed views.</span></span> <span data-ttu-id="fa4b2-147">如需詳細資訊，請參閱 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) 的 REBUILD 選項。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-147">For more information, see the REBUILD option for [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
    -   <span data-ttu-id="fa4b2-148">非唯一索引。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-148">Non-unique indexes.</span></span> <span data-ttu-id="fa4b2-149">篩選索引可以是非唯一的，而索引檢視表則必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-149">Filtered indexes can be non-unique, whereas indexed views must be unique.</span></span>  
  
-   <span data-ttu-id="fa4b2-150">篩選索引定義於單一資料表，僅支援簡單比較運算子。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-150">Filtered indexes are defined on one table and only support simple comparison operators.</span></span> <span data-ttu-id="fa4b2-151">如果需要參考多個資料表或具有複雜邏輯的篩選運算式，則應該建立檢視。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-151">If you need a filter expression that references multiple tables or has complex logic, you should create a view.</span></span>  
  
-   <span data-ttu-id="fa4b2-152">如果篩選索引運算式相等於查詢述詞，且查詢並未以篩選索引運算式中的資料行傳回查詢結果，則篩選索引運算式中的資料行不需要是篩選索引定義中的索引鍵或內含資料行。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-152">A column in the filtered index expression does not need to be a key or included column in the filtered index definition if the filtered index expression is equivalent to the query predicate and the query does not return the column in the filtered index expression with the query results.</span></span>  
  
-   <span data-ttu-id="fa4b2-153">如果查詢述詞在不等於篩選索引運算式的比較中使用篩選索引運算式中的資料行，則該資料行應該是篩選索引定義中的索引鍵或內含資料行。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-153">A column in the filtered index expression should be a key or included column in the filtered index definition if the query predicate uses the column in a comparison that is not equivalent to the filtered index expression.</span></span>  
  
-   <span data-ttu-id="fa4b2-154">如果篩選索引運算式中的資料行在查詢結果集中，則該資料行應該是篩選索引定義中的索引鍵或內含資料行。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-154">A column in the filtered index expression should be a key or included column in the filtered index definition if the column is in the query result set.</span></span>  
  
-   <span data-ttu-id="fa4b2-155">資料表的叢集索引鍵並不需要是篩選索引定義中的索引鍵或內含資料行。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-155">The clustered index key of the table does not need to be a key or included column in the filtered index definition.</span></span> <span data-ttu-id="fa4b2-156">叢集索引鍵會自動包含在所有非叢集的索引中 (包含篩選索引在內)。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-156">The clustered index key is automatically included in all nonclustered indexes, including filtered indexes.</span></span>  
  
-   <span data-ttu-id="fa4b2-157">如果在篩選索引的篩選索引運算式中指定的比較運算子產生隱含或明確的資料轉換，則如果該轉換是發生在比較運算子的左側，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-157">If the comparison operator specified in the filtered index expression of the filtered index results in an implicit or explicit data conversion, an error will occur if the conversion occurs on the left side of a comparison operator.</span></span> <span data-ttu-id="fa4b2-158">解決方案是以資料轉換運算子 (CAST 或 CONVERT) 在比較運算子的右側寫下篩選索引運算式。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-158">A solution is to write the filtered index expression with the data conversion operator (CAST or CONVERT) on the right side of the comparison operator.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fa4b2-159">Security</span><span class="sxs-lookup"><span data-stu-id="fa4b2-159">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fa4b2-160">權限</span><span class="sxs-lookup"><span data-stu-id="fa4b2-160">Permissions</span></span>  
 <span data-ttu-id="fa4b2-161">需要資料表或檢視表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-161">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="fa4b2-162">使用者必須是 **系統管理員** 固定伺服器角色的成員，或是 **db_ddladmin** 和 **db_owner** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-162">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span> <span data-ttu-id="fa4b2-163">若要修改篩選索引運算式，請使用 CREATE INDEX WITH DROP_EXISTING。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-163">To modify the filtered index expression, use CREATE INDEX WITH DROP_EXISTING.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fa4b2-164">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fa4b2-164">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-filtered-index"></a><span data-ttu-id="fa4b2-165">建立篩選的索引</span><span class="sxs-lookup"><span data-stu-id="fa4b2-165">To create a filtered index</span></span>  
  
1.  <span data-ttu-id="fa4b2-166">在 [物件總管] 中，按一下加號展開資料庫，此資料庫包含您要建立篩選索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-166">In Object Explorer, click the plus sign to expand the database that contains the table on which you want to create a filtered index.</span></span>  
  
2.  <span data-ttu-id="fa4b2-167">按一下加號展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-167">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="fa4b2-168">按一下加號展開要建立篩選索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-168">Click the plus sign to expand the table on which you want to create a filtered index.</span></span>  
  
4.  <span data-ttu-id="fa4b2-169">以滑鼠右鍵按一下 [索引] 資料夾，指向 [新增索引]，然後選取 [非叢集索引…]。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-169">Right-click the **Indexes** folder, point to **New Index**, and select **Non-Clustered Index...**.</span></span>  
  
5.  <span data-ttu-id="fa4b2-170">在 **[新增索引]** 對話方塊，於 **[一般]** 頁面上的 **[索引名稱]** 方塊中輸入新索引的名稱。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-170">In the **New Index** dialog box, on the **General** page, enter the name of the new index in the **Index name** box.</span></span>  
  
6.  <span data-ttu-id="fa4b2-171">按一下 [索引鍵資料行] 下的 [新增...]。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-171">Under **Index key columns**, click **Add...**.</span></span>  
  
7.  <span data-ttu-id="fa4b2-172">在 [**從**_Table_name_選取資料行] 對話方塊中，選取要加入至唯一索引之資料表資料行的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-172">In the **Select Columns from**_table_name_ dialog box, select the check box or check boxes of the table column or columns to be added to the unique index.</span></span>  
  
8.  <span data-ttu-id="fa4b2-173">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-173">Click **OK**.</span></span>  
  
9. <span data-ttu-id="fa4b2-174">在 [篩選] 頁面的 [篩選運算式]底下，輸入要用來建立篩選索引的 SQL 運算式。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-174">On the **Filter** page, under **Filter Expression**, enter SQL expression that you'll use to create the filtered index.</span></span>  
  
10. <span data-ttu-id="fa4b2-175">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-175">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fa4b2-176">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fa4b2-176">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-filtered-index"></a><span data-ttu-id="fa4b2-177">建立篩選的索引</span><span class="sxs-lookup"><span data-stu-id="fa4b2-177">To create a filtered index</span></span>  
  
1.  <span data-ttu-id="fa4b2-178">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-178">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fa4b2-179">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-179">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fa4b2-180">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-180">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Looks for an existing filtered index named "FIBillOfMaterialsWithEndDate"  
    -- and deletes it from the table Production.BillOfMaterials if found.   
    IF EXISTS (SELECT name FROM sys.indexes  
        WHERE name = N'FIBillOfMaterialsWithEndDate'  
        AND object_id = OBJECT_ID (N'Production.BillOfMaterials'))  
    DROP INDEX FIBillOfMaterialsWithEndDate  
        ON Production.BillOfMaterials  
    GO  
    -- Creates a filtered index "FIBillOfMaterialsWithEndDate"  
    -- on the table Production.BillOfMaterials   
    -- using the columms ComponentID and StartDate.  
  
    CREATE NONCLUSTERED INDEX FIBillOfMaterialsWithEndDate  
        ON Production.BillOfMaterials (ComponentID, StartDate)  
        WHERE EndDate IS NOT NULL ;  
    GO  
    ```  
  
     <span data-ttu-id="fa4b2-181">以上的篩選索引對下列查詢有效。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-181">The filtered index above is valid for the following query.</span></span> <span data-ttu-id="fa4b2-182">您可以顯示查詢執行計畫，以判斷查詢最佳化工具是否使用了篩選索引。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-182">You can display the query execution plan to determine if the query optimizer used the filtered index.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT ProductAssemblyID, ComponentID, StartDate   
    FROM Production.BillOfMaterials  
    WHERE EndDate IS NOT NULL   
        AND ComponentID = 5   
        AND StartDate > '01/01/2008' ;  
    GO  
    ```  
  
#### <a name="to-ensure-that-a-filtered-index-is-used-in-a-sql-query"></a><span data-ttu-id="fa4b2-183">確定在 SQL 查詢中使用篩選的索引</span><span class="sxs-lookup"><span data-stu-id="fa4b2-183">To ensure that a filtered index is used in a SQL query</span></span>  
  
1.  <span data-ttu-id="fa4b2-184">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-184">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="fa4b2-185">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-185">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="fa4b2-186">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-186">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT ComponentID, StartDate FROM Production.BillOfMaterials  
        WITH ( INDEX ( FIBillOfMaterialsWithEndDate ) )   
    WHERE EndDate IN ('20000825', '20000908', '20000918');   
    GO  
    ```  
  
 <span data-ttu-id="fa4b2-187">如需詳細資訊，請參閱 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="fa4b2-187">For more information, see  [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
