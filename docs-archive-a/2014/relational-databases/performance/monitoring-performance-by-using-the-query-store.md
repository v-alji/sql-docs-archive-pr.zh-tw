---
title: 使用查詢存放區監視效能 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: e06344a4-22a5-4c67-b6c6-a7060deb5de6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e5d74b9c4def9c0314569a8d0bd87939cdcb11b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606242"
---
# <a name="monitoring-performance-by-using-the-query-store"></a><span data-ttu-id="83e92-102">Monitoring Performance By Using the Query Store</span><span class="sxs-lookup"><span data-stu-id="83e92-102">Monitoring Performance By Using the Query Store</span></span>
  <span data-ttu-id="83e92-103">查詢存放區功能為 DBA 提供查詢計劃選擇及效能的深入了解。</span><span class="sxs-lookup"><span data-stu-id="83e92-103">The query store feature provides DBAs with insight on query plan choice and performance.</span></span> <span data-ttu-id="83e92-104">它能讓您快速找出因為查詢計劃中的變更所導致的效能差異，以簡化效能疑難排解。</span><span class="sxs-lookup"><span data-stu-id="83e92-104">It simplifies performance troubleshooting by enabling you to quickly find performance differences caused by changes in query plans.</span></span> <span data-ttu-id="83e92-105">該功能會自動擷取查詢、計劃及執行階段統計資料的記錄，並會保留這些記錄供您檢閱。</span><span class="sxs-lookup"><span data-stu-id="83e92-105">The feature automatically captures a history of queries, plans, and runtime statistics, and retains these for your review.</span></span> <span data-ttu-id="83e92-106">其會以時段來區分資料、供您查看資料庫使用模式，並了解何時在伺服器上發生查詢計劃變更。</span><span class="sxs-lookup"><span data-stu-id="83e92-106">It separates data by time windows, allowing you to see database usage patterns and understand when query plan changes happened on the server.</span></span> <span data-ttu-id="83e92-107">使用 [ALTER DATABASE SET](/sql/t-sql/statements/alter-database-transact-sql-set-options) 選項，可設定查詢存放區。</span><span class="sxs-lookup"><span data-stu-id="83e92-107">The query store can be configured by using the [ALTER DATABASE SET](/sql/t-sql/statements/alter-database-transact-sql-set-options) option.</span></span>

||
|-|
|<span data-ttu-id="83e92-108">**適用于**： [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] () [取得](http://azure.micosoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)。</span><span class="sxs-lookup"><span data-stu-id="83e92-108">**Applies to**: [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ([Get it](http://azure.micosoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).</span></span>|

> [!IMPORTANT]
>  <span data-ttu-id="83e92-109">目前是預覽功能。</span><span class="sxs-lookup"><span data-stu-id="83e92-109">This is currently a preview feature.</span></span> <span data-ttu-id="83e92-110">若要使用查詢存放區，您必須同意並了解運作查詢存放區受到授權合約預覽條款 (例如，Enterprise 合約、Microsoft Azure 合約或 Microsoft 線上訂用帳戶合約) 的限制，以及任何適用的 [Microsoft Azure Preview 增補使用條款](https://azure.microsoft.com/support/legal/preview-supplemental-terms/)。</span><span class="sxs-lookup"><span data-stu-id="83e92-110">To use the Query Store you must acknowledge and agree that implementation of Query Store is subject to the preview terms in your license agreement (e.g. the Enterprise Agreement, Microsoft Azure Agreement, or Microsoft Online Subscription Agreement), as well as any applicable [Supplemental Terms of Use for Microsoft Azure Preview](https://azure.microsoft.com/support/legal/preview-supplemental-terms/).</span></span>

##  <a name="enabling-the-query-store"></a><a name="Enabling"></a> <span data-ttu-id="83e92-111">啟用查詢存放區</span><span class="sxs-lookup"><span data-stu-id="83e92-111">Enabling the Query Store</span></span>
 <span data-ttu-id="83e92-112">新的資料庫預設不會啟用查詢存放區。</span><span class="sxs-lookup"><span data-stu-id="83e92-112">Query Store is not active for new databases by default.</span></span>

#### <a name="by-using-the-query-store-page-in-management-studio"></a><span data-ttu-id="83e92-113">使用 Management Studio 中的查詢存放區頁面</span><span class="sxs-lookup"><span data-stu-id="83e92-113">By Using the Query Store Page in Management Studio</span></span>

1.  <span data-ttu-id="83e92-114">在 [物件總管] 中，以滑鼠右鍵按一下資料庫，然後按一下 [屬性] 。</span><span class="sxs-lookup"><span data-stu-id="83e92-114">In Object Explorer, right-click a database, and then click **Properties**.</span></span> <span data-ttu-id="83e92-115">(需要 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]2016 版本。)</span><span class="sxs-lookup"><span data-stu-id="83e92-115">(Requires [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2016 version of [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].)</span></span>

2.  <span data-ttu-id="83e92-116">在 [資料庫屬性]  對話方塊中，選取 [查詢存放區]  頁面。</span><span class="sxs-lookup"><span data-stu-id="83e92-116">In the **Database Properties** dialog box, select the **Query Store** page.</span></span>

3.  <span data-ttu-id="83e92-117">在 [啟用] \*\*\*\* 方塊中，選取 [True] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="83e92-117">In the **Enable** box, select **True**.</span></span>

#### <a name="by-using-transact-sql-statements"></a><span data-ttu-id="83e92-118">使用 Transact-SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="83e92-118">By Using Transact-SQL Statements</span></span>

1.  <span data-ttu-id="83e92-119">使用 `ALTER DATABASE` 陳述式可啟用查詢存放區。</span><span class="sxs-lookup"><span data-stu-id="83e92-119">Use the `ALTER DATABASE` statement to enable the query store.</span></span> <span data-ttu-id="83e92-120">例如：</span><span class="sxs-lookup"><span data-stu-id="83e92-120">For example:</span></span>

    ```
    ALTER DATABASE AdventureWorks2012 SET QUERY_STORE = ON;
    ```

     <span data-ttu-id="83e92-121">如需查詢存放區的相關語法選項，請參閱[ALTER DATABASE SET 選項 &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)。</span><span class="sxs-lookup"><span data-stu-id="83e92-121">For more syntax options related to the query store, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>

> [!NOTE]
>  <span data-ttu-id="83e92-122">您無法為 master 資料庫啟用查詢存放區。</span><span class="sxs-lookup"><span data-stu-id="83e92-122">You cannot enable the query store for the master database.</span></span>



##  <a name="information-in-the-query-store"></a><a name="About"></a> <span data-ttu-id="83e92-123">查詢存放區中的資訊</span><span class="sxs-lookup"><span data-stu-id="83e92-123">Information in the Query Store</span></span>
 <span data-ttu-id="83e92-124">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中任何特定查詢的執行計劃通常會在一段時間後，因為統計資料的變更、結構描述變更、建立/刪除索引等數種不同原因而有所演變。儲存快取的查詢計劃之程序快取，只會儲存最新的執行計劃。</span><span class="sxs-lookup"><span data-stu-id="83e92-124">Execution plans for any specific query in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] typically evolve over time due to a number of different reasons such as statistics changes, schema changes, creation/deletion of indexes, etc. The procedure cache (where cached query plans are stored) only stores the latest execution plan.</span></span> <span data-ttu-id="83e92-125">計劃也會因為記憶體不足的壓力，而從計劃快取中收回。</span><span class="sxs-lookup"><span data-stu-id="83e92-125">Plans also get evicted from the plan cache due to memory pressure.</span></span> <span data-ttu-id="83e92-126">因此，因為執行計劃變更所造成的查詢效能低下，可能相形重要，而且可能需要許多時間才可解決。</span><span class="sxs-lookup"><span data-stu-id="83e92-126">As a result, query performance regressions caused by execution plan changes can be non-trivial and time consuming to resolve.</span></span>

 <span data-ttu-id="83e92-127">因為查詢存放區會為每項查詢保留多個執行計劃，其可強制套用原則以指示查詢處理器要為查詢使用特定的執行計劃。</span><span class="sxs-lookup"><span data-stu-id="83e92-127">Since the query store retains multiple execution plans per query, it can enforce policies to direct the query processor to use a specific execution plan for a query.</span></span> <span data-ttu-id="83e92-128">這也稱為強制執行計劃。</span><span class="sxs-lookup"><span data-stu-id="83e92-128">This is referred to as plan forcing.</span></span> <span data-ttu-id="83e92-129">查詢存放區中的強制執行計劃，透過類似於 [USE PLAN](/sql/t-sql/queries/hints-transact-sql-query) 查詢提示的機制加以提供，但它不需要在使用者應用程式中進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="83e92-129">Plan forcing in Query Store is provided by using a mechanism similar to the [USE PLAN](/sql/t-sql/queries/hints-transact-sql-query) query hint, but it does not require any change in user applications.</span></span> <span data-ttu-id="83e92-130">強制執行計劃可以解決在非常短的期間內，因計劃變更所導致的查詢效能低下。</span><span class="sxs-lookup"><span data-stu-id="83e92-130">Plan forcing can resolve a query performance regression caused by a plan change in a very short period of time.</span></span>

 <span data-ttu-id="83e92-131">使用查詢存放區功能的常見情況包括：</span><span class="sxs-lookup"><span data-stu-id="83e92-131">Common scenarios for using the Query Store feature are:</span></span>

-   <span data-ttu-id="83e92-132">強制執行先前的查詢計劃，快速找出並修正計劃效能低下。</span><span class="sxs-lookup"><span data-stu-id="83e92-132">Quickly find and fix a plan performance regression by forcing the previous query plan.</span></span> <span data-ttu-id="83e92-133">修正因為執行計劃變更而最近出現的效能低下。</span><span class="sxs-lookup"><span data-stu-id="83e92-133">Fix queries that have recently regressed in performance due to execution plan changes.</span></span>

-   <span data-ttu-id="83e92-134">判斷在指定的時段執行查詢的次數、協助 DBA 疑難排解資源的效能問題。</span><span class="sxs-lookup"><span data-stu-id="83e92-134">Determine the number of times a query was executed in a given time window, assisting a DBA in troubleshooting performance resource problems.</span></span>

-   <span data-ttu-id="83e92-135">識別過去 *x* 小時內的前 *n* 項查詢 (依據執行時間、記憶體耗用量等等)。</span><span class="sxs-lookup"><span data-stu-id="83e92-135">Identify top *n* queries (by execution time, memory consumption, etc.) in the past *x* hours.</span></span>

-   <span data-ttu-id="83e92-136">稽核指定的查詢之查詢計劃記錄。</span><span class="sxs-lookup"><span data-stu-id="83e92-136">Audit the history of query plans for a given query.</span></span>

-   <span data-ttu-id="83e92-137">分析特定資料庫的資源 (CPU、I/O 及記憶體) 使用模式。</span><span class="sxs-lookup"><span data-stu-id="83e92-137">Analyze the resource (CPU, I/O, and Memory) usage patterns for a particular database.</span></span>

 <span data-ttu-id="83e92-138">查詢存放區包含兩個存放區。 **計劃存放區** 可保存執行計劃資訊，而 **執行階段統計資料存放區** 則會保存執行統計資料資訊。</span><span class="sxs-lookup"><span data-stu-id="83e92-138">The query store contains two stores; a **plan store** for persisting the execution plan information, and a **runtime stats store** for persisting the execution statistics information.</span></span> <span data-ttu-id="83e92-139">在計劃存放區中可為查詢儲存的不重複之計劃的數目，受限於 `max_plans_per_query` 組態選項。</span><span class="sxs-lookup"><span data-stu-id="83e92-139">The number of unique plans that can be stored for a query in the plan store is limited by the `max_plans_per_query` configuration option.</span></span> <span data-ttu-id="83e92-140">若要增強效能，資訊會以非同步方式寫入兩個存放區。</span><span class="sxs-lookup"><span data-stu-id="83e92-140">To enhance performance, the information is written to the two stores asynchronously.</span></span> <span data-ttu-id="83e92-141">若要將空間使用量降至最低，在執行階段統計資料存放區中的執行階段執行統計資料，會以固定的時段彙總。</span><span class="sxs-lookup"><span data-stu-id="83e92-141">To minimize space usage, the runtime execution statistics in the runtime stats store are aggregated over a fixed time window.</span></span> <span data-ttu-id="83e92-142">對查詢存放區目錄檢視進行查詢時，會顯示這些存放區中的資訊。</span><span class="sxs-lookup"><span data-stu-id="83e92-142">The information in these stores is visible by querying the query store catalog views.</span></span>

 <span data-ttu-id="83e92-143">下列查詢會傳回查詢存放區中查詢與計劃的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="83e92-143">The following query returns information about queries and plans in the query store.</span></span>

```
SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*
FROM sys.query_store_plan AS Pl
JOIN sys.query_store_query AS Qry
    ON Pl.query_id = Qry.query_id
JOIN sys.query_store_query_text AS Txt
    ON Qry.query_text_id = Txt.query_text_id ;
```



## <a name="using-the-regressed-queries-feature"></a><span data-ttu-id="83e92-144">使用迴歸查詢功能</span><span class="sxs-lookup"><span data-stu-id="83e92-144">Using the Regressed Queries Feature</span></span>
 <span data-ttu-id="83e92-145">啟用查詢存放區之後，請重新整理 [物件總管] 窗格中的資料庫部分，以加入 [**查詢存放區**] 區段。</span><span class="sxs-lookup"><span data-stu-id="83e92-145">After enabling the query store, refresh the database portion of the Object Explorer pane to add the **Query Store** section.</span></span>

 <span data-ttu-id="83e92-146">![QueryStore](../../database-engine/media/querystore.PNG "QueryStore")</span><span class="sxs-lookup"><span data-stu-id="83e92-146">![QueryStore](../../database-engine/media/querystore.PNG "QueryStore")</span></span>

 <span data-ttu-id="83e92-147">選取 [迴歸查詢] \*\*\*\*，開啟 **中的 [迴歸查詢]**[!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]窗格。</span><span class="sxs-lookup"><span data-stu-id="83e92-147">Selecting **Regressed Queries**, opens the **Regressed Queries** pane in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="83e92-148">[迴歸查詢] 窗格會顯示查詢存放區中的查詢與計劃。</span><span class="sxs-lookup"><span data-stu-id="83e92-148">The Regressed Queries pane shows you the queries, and plans in the query store.</span></span> <span data-ttu-id="83e92-149">頂端的下拉式清單方塊，可供您依據各種條件選取查詢。</span><span class="sxs-lookup"><span data-stu-id="83e92-149">Drop down boxes at the top allow you to select queries based on various criteria.</span></span> <span data-ttu-id="83e92-150">選取計劃即可以圖形方式檢視查詢計劃。</span><span class="sxs-lookup"><span data-stu-id="83e92-150">Select a plan to see the graphical query plan.</span></span> <span data-ttu-id="83e92-151">提供有按鈕可供檢視來源查詢、強制執行或取消強制執行查詢計劃，以及重新整理顯示畫面。</span><span class="sxs-lookup"><span data-stu-id="83e92-151">Buttons are available to view the source query, force, and unforce a query plan, and refresh the display.</span></span>

 <span data-ttu-id="83e92-152">![RegressedQueries](../../database-engine/media/regressedqueries.PNG "RegressedQueries")</span><span class="sxs-lookup"><span data-stu-id="83e92-152">![RegressedQueries](../../database-engine/media/regressedqueries.PNG "RegressedQueries")</span></span>

 <span data-ttu-id="83e92-153">若要強制執行計畫，請選取查詢和計畫，然後按一下 [**強制計畫]。**</span><span class="sxs-lookup"><span data-stu-id="83e92-153">To force a plan, select a query and plan, and then click **Force Plan.**</span></span> <span data-ttu-id="83e92-154">您只可以強制執行由查詢計劃功能所儲存且仍保留在查詢計劃快取中的計劃。</span><span class="sxs-lookup"><span data-stu-id="83e92-154">You can only force plans that were saved by the query plan feature and are still retained in the query plan cache.</span></span>



##  <a name="configuration-options"></a><a name="Options"></a> <span data-ttu-id="83e92-155">組態選項</span><span class="sxs-lookup"><span data-stu-id="83e92-155">Configuration Options</span></span>
 <span data-ttu-id="83e92-156">OPERATION_MODE 可以 READ_WRITE 或 READ_ONLY。</span><span class="sxs-lookup"><span data-stu-id="83e92-156">OPERATION_MODE Can be READ_WRITE or READ_ONLY.</span></span>

 <span data-ttu-id="83e92-157">CLEANUP_POLICY 設定 STALE_QUERY_THRESHOLD_DAYS 引數，以指定要在查詢存放區中保留資料的天數。</span><span class="sxs-lookup"><span data-stu-id="83e92-157">CLEANUP_POLICY Configure the STALE_QUERY_THRESHOLD_DAYS argument to specify the number of days to retain data in the query store.</span></span>

 <span data-ttu-id="83e92-158">DATA_FLUSH_INTERVAL_SECONDS 決定將寫入查詢存放區之資料保存到磁碟的頻率。</span><span class="sxs-lookup"><span data-stu-id="83e92-158">DATA_FLUSH_INTERVAL_SECONDS Determines the frequency at which data written to the query store is persisted to disk.</span></span> <span data-ttu-id="83e92-159">為了獲得最佳效能，查詢存放區所收集的資料會以非同步方式寫入磁碟。</span><span class="sxs-lookup"><span data-stu-id="83e92-159">To optimize for performance, data collected by the query store is asynchronously written to the disk.</span></span> <span data-ttu-id="83e92-160">此非同步傳輸發生的頻率，以 DATA_FLUSH_INTERVAL_SECONDS 設定。</span><span class="sxs-lookup"><span data-stu-id="83e92-160">The frequency at which this asynchronous transfer occurs is configured via DATA_FLUSH_INTERVAL_SECONDS.</span></span>

 <span data-ttu-id="83e92-161">MAX_SIZE_MB 設定查詢存放區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="83e92-161">MAX_SIZE_MB Configures the maximum size of the query store.</span></span> <span data-ttu-id="83e92-162">若查詢存放區中的資料到達了 MAX_SIZE_MB 限制，查詢存放區會自動從讀寫狀態變更為唯讀，並會停止收集新的資料。</span><span class="sxs-lookup"><span data-stu-id="83e92-162">If the data in the query store hits the MAX_SIZE_MB limit, the query store automatically changes the state from read-write to read-only and stops collecting new data.</span></span>

 <span data-ttu-id="83e92-163">INTERVAL_LENGTH_MINUTES 決定執行階段執行統計資料彙總至查詢存放區的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="83e92-163">INTERVAL_LENGTH_MINUTES Determines the time interval at which runtime execution statistics data is aggregated into the query store.</span></span> <span data-ttu-id="83e92-164">若要最佳化空間的使用量，在執行階段統計資料存放區中的執行階段執行統計資料，會以固定的時段彙總。</span><span class="sxs-lookup"><span data-stu-id="83e92-164">To optimize for space usage, the runtime execution statistics in the Runtime Stats Store are aggregated over a fixed time window.</span></span> <span data-ttu-id="83e92-165">這個固定時段由 INTERVAL_LENGTH_MINUTES 所設定。</span><span class="sxs-lookup"><span data-stu-id="83e92-165">This fixed time window is configured via INTERVAL_LENGTH_MINUTES.</span></span>

 <span data-ttu-id="83e92-166">查詢 `sys.database_query_store_options` 檢視可判斷查詢存放區目前的選項。</span><span class="sxs-lookup"><span data-stu-id="83e92-166">Query the `sys.database_query_store_options` view to determine the current options of the query store.</span></span>

 <span data-ttu-id="83e92-167">如需使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式設定選項的詳細資訊，請參閱 [選項管理](#OptionMgmt)。</span><span class="sxs-lookup"><span data-stu-id="83e92-167">For more information about setting options by using [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, see [Option Management](#OptionMgmt).</span></span>

 

##  <a name="related-views-functions-and-procedures"></a><a name="Related"></a> <span data-ttu-id="83e92-168">相關檢視、函數與程序</span><span class="sxs-lookup"><span data-stu-id="83e92-168">Related Views, Functions, and Procedures</span></span>
 <span data-ttu-id="83e92-169">透過 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 或使用下列檢視與程序，即可檢視及管理查詢存放區。</span><span class="sxs-lookup"><span data-stu-id="83e92-169">The Query Store can be viewed and managed through [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] or by using the following views and procedures.</span></span>

-   [<span data-ttu-id="83e92-170">sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83e92-170">sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql)

### <a name="query-store-catalog-views"></a><span data-ttu-id="83e92-171">查詢存放區目錄檢視</span><span class="sxs-lookup"><span data-stu-id="83e92-171">Query Store Catalog Views</span></span>
 <span data-ttu-id="83e92-172">共有七個目錄檢視可提供有關查詢存放區的資訊。</span><span class="sxs-lookup"><span data-stu-id="83e92-172">Seven catalog views present information about the Query Store.</span></span>

-   [<span data-ttu-id="83e92-173">sys.database_query_store_options &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83e92-173">sys.database_query_store_options &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql)

-   [<span data-ttu-id="83e92-174">sys.query_context_settings &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83e92-174">sys.query_context_settings &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-context-settings-transact-sql)

-   [<span data-ttu-id="83e92-175">sys.query_store_plan &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83e92-175">sys.query_store_plan &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-store-plan-transact-sql)

-   [<span data-ttu-id="83e92-176">sys.query_store_query &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83e92-176">sys.query_store_query &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-store-query-transact-sql)

-   [<span data-ttu-id="83e92-177">sys.query_store_query_text &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83e92-177">sys.query_store_query_text &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql)

-   [<span data-ttu-id="83e92-178">sys.query_store_runtime_stats &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83e92-178">sys.query_store_runtime_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql)

-   [<span data-ttu-id="83e92-179">sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83e92-179">sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql)

### <a name="query-store-stored-procedures"></a><span data-ttu-id="83e92-180">查詢存放區預存程序</span><span class="sxs-lookup"><span data-stu-id="83e92-180">Query Store Stored Procedures</span></span>
 <span data-ttu-id="83e92-181">共有六個預存程序可設定查詢存放區。</span><span class="sxs-lookup"><span data-stu-id="83e92-181">Six stored procedures configure the Query Store.</span></span>

-   [<span data-ttu-id="83e92-182">sp_query_store_flush_db &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83e92-182">sp_query_store_flush_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql)

-   [<span data-ttu-id="83e92-183">sp_query_store_reset_exec_stats &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83e92-183">sp_query_store_reset_exec_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql)

-   [<span data-ttu-id="83e92-184">sp_query_store_force_plan &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83e92-184">sp_query_store_force_plan &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql)

-   [<span data-ttu-id="83e92-185">sp_query_store_unforce_plan &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83e92-185">sp_query_store_unforce_plan &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql)

-   [<span data-ttu-id="83e92-186">sp_query_store_remove_plan &#40;Transct-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83e92-186">sp_query_store_remove_plan &#40;Transct-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql)

-   [<span data-ttu-id="83e92-187">sp_query_store_remove_query &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="83e92-187">sp_query_store_remove_query &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql)



##  <a name="key-usage-scenarios"></a><a name="Scenarios"></a> <span data-ttu-id="83e92-188">主要使用方式案例</span><span class="sxs-lookup"><span data-stu-id="83e92-188">Key Usage Scenarios</span></span>

###  <a name="option-management"></a><a name="OptionMgmt"></a> <span data-ttu-id="83e92-189">選項管理</span><span class="sxs-lookup"><span data-stu-id="83e92-189">Option Management</span></span>
 <span data-ttu-id="83e92-190">本節提供管理查詢存放區功能本身的一些指導方針。</span><span class="sxs-lookup"><span data-stu-id="83e92-190">This section provides some guidelines on managing Query Store feature itself.</span></span>

 <span data-ttu-id="83e92-191">**查詢存放區目前為作用中？**</span><span class="sxs-lookup"><span data-stu-id="83e92-191">**Is Query Store currently active?**</span></span>

 <span data-ttu-id="83e92-192">查詢存放區會將其資料儲存在使用者資料庫中，這也就是為什麼它有大小的限制 (以 `MAX_STORAGE_SIZE_MB` 設定)。</span><span class="sxs-lookup"><span data-stu-id="83e92-192">Query Store stores its data inside the user database and that is why it has size limit (configured  with `MAX_STORAGE_SIZE_MB`).</span></span> <span data-ttu-id="83e92-193">若查詢存放區中的資料達到上限，查詢存放區會自動從讀寫狀態變更為唯讀，並會停止收集新的資料。</span><span class="sxs-lookup"><span data-stu-id="83e92-193">If data in Query Store hits that limit Query Store will automatically change state from read-write to read-only and stop collecting new data.</span></span>

 <span data-ttu-id="83e92-194">執行下列指令碼可判斷查詢存放區目前是否在作用中，以及其目前是否正在收集執行階段統計資料。</span><span class="sxs-lookup"><span data-stu-id="83e92-194">Execute the following script to determine if Query Store is currently active, and whether it is currently collects runtime stats or not.</span></span>

```
DECLARE @x nvarchar(100) = CAST(newid() AS nvarchar(100));
DECLARE @query nvarchar(max) = 
N'IF EXISTS
(
    SELECT * 
    FROM sys.query_store_query_text 
    WHERE query_sql_text LIKE ''%' + @x + N'%''
)
SELECT ''Query Store is active'' ;
ELSE SELECT ''Query Store is NOT active''' ;
EXEC sp_executesql @query;
```

 <span data-ttu-id="83e92-195">**取得查詢存放區選項**</span><span class="sxs-lookup"><span data-stu-id="83e92-195">**Get Query Store options**</span></span>

 <span data-ttu-id="83e92-196">若要找出查詢存放區狀態的詳細資訊，請於使用者資料庫中執行下列作業。</span><span class="sxs-lookup"><span data-stu-id="83e92-196">To find out detailed information about Query Store status, execute following in a user database.</span></span>

```
SELECT * FROM sys.database_query_store_options;
```

 <span data-ttu-id="83e92-197">**設定查詢存放區間隔**</span><span class="sxs-lookup"><span data-stu-id="83e92-197">**Setting Query Store interval**</span></span>

 <span data-ttu-id="83e92-198">您可以覆寫彙總查詢執行階段統計資料的間隔 (預設為 60 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="83e92-198">You can override interval for aggregating query runtime statistics (default is 60 minutes).</span></span>

```

      USE master;
GO

ALTER DATABASE <database_name> 
SET QUERY_STORE (INTERVAL_LENGTH_MINUTES = 15);
```

 <span data-ttu-id="83e92-199">請注意，不得使用任意值，您應使用下列其中之一：1、5、10、15、30 和 60。</span><span class="sxs-lookup"><span data-stu-id="83e92-199">Note that arbitrary values are not allowed - you should use one of the following: 1, 5, 10, 15, 30 and 60.</span></span>

 <span data-ttu-id="83e92-200">透過 `sys.database_query_store_options` 檢視，即可看到新的間隔值。</span><span class="sxs-lookup"><span data-stu-id="83e92-200">New value for interval is exposed through `sys.database_query_store_options` view.</span></span>

 <span data-ttu-id="83e92-201">如果查詢存放區的儲存體已滿，請使用下列陳述式來擴充該儲存體。</span><span class="sxs-lookup"><span data-stu-id="83e92-201">If the Query Store storage is full use the following statement to extend the storage.</span></span>

```
ALTER DATABASE <database_name> 
SET QUERY_STORE (MAX_STORAGE_SIZE_MB = <new_size>);
```

 <span data-ttu-id="83e92-202">**設定所有查詢存放區選項**</span><span class="sxs-lookup"><span data-stu-id="83e92-202">**Set all Query Store options**</span></span>

 <span data-ttu-id="83e92-203">使用單一 ALTER DATABASE 陳述式即可一次設定多個查詢存放區選項。</span><span class="sxs-lookup"><span data-stu-id="83e92-203">You can set multiple Query Store options at once with a single ALTER DATABASE statement.</span></span>

```
ALTER DATABASE <database name> 
SET QUERY_STORE (
    OPERATION_MODE = READ_WRITE,
    CLEANUP_POLICY = 
    (STALE_QUERY_THRESHOLD_DAYS = 30),
    DATA_FLUSH_INTERVAL_SECONDS = 3000,
    MAX_STORAGE_SIZE_MB = 500,
    INTERVAL_LENGTH_MINUTES = 15
);
```

 <span data-ttu-id="83e92-204">**清理空間**</span><span class="sxs-lookup"><span data-stu-id="83e92-204">**Cleaning up the space**</span></span>

 <span data-ttu-id="83e92-205">查詢存放區內部資料表於建立資料庫時建立在 PRIMARY 檔案群組中，且該組態之後無法變更。</span><span class="sxs-lookup"><span data-stu-id="83e92-205">Query Store internal tables are created in the PRIMARY filegroup during database creation and that configuration cannot be changed later.</span></span> <span data-ttu-id="83e92-206">如果您快要用完了空間，可能會想要使用下列陳述式，來清除舊的查詢存放區資料。</span><span class="sxs-lookup"><span data-stu-id="83e92-206">If you are running out of space you might want to clear older Query Store data by using the following statement.</span></span>

```
ALTER DATABASE <db_name> SET QUERY_STORE CLEAR;
```

 <span data-ttu-id="83e92-207">或者，您也可能只想要清除特定查詢資料，因為它對於查詢最佳化和計劃分析來說較不相關，但也佔用一樣的空間。</span><span class="sxs-lookup"><span data-stu-id="83e92-207">Alternatively, you might want to clear up only ad-hoc query data, since it is less relevant for query optimizations and plan analysis but takes up just as much space.</span></span>

 <span data-ttu-id="83e92-208">**刪除臨機操作查詢** 如此做會刪除只執行一次且超過 24 小時的查詢。</span><span class="sxs-lookup"><span data-stu-id="83e92-208">**Delete ad-hoc queries** This deletes the queries that were only executed only once and that are more than 24 hours old.</span></span>

```
DECLARE @id int
DECLARE adhoc_queries_cursor CURSOR 
FOR 
SELECT q.query_id
FROM sys.query_store_query_text AS qt
JOIN sys.query_store_query AS q 
    ON q.query_text_id = qt.query_text_id
JOIN sys.query_store_plan AS p 
    ON p.query_id = q.query_id
JOIN sys.query_store_runtime_stats AS rs 
    ON rs.plan_id = p.plan_id
GROUP BY q.query_id
HAVING SUM(rs.count_executions) < 2 
AND MAX(rs.last_execution_time) < DATEADD (hour, -24, GETUTCDATE())
ORDER BY q.query_id ;

OPEN adhoc_queries_cursor ;
FETCH NEXT FROM adhoc_queries_cursor INTO @id;
WHILE @@fetch_status = 0
    BEGIN 
        PRINT @id
        EXEC sp_query_store_remove_query @id
        FETCH NEXT FROM adhoc_queries_cursor INTO @id
    END 
CLOSE adhoc_queries_cursor ;
DEALLOCATE adhoc_queries_cursor;
```

 <span data-ttu-id="83e92-209">您可以用不同的邏輯來定義自己的程序，以清除不再重要的資料。</span><span class="sxs-lookup"><span data-stu-id="83e92-209">You can define your own procedure with different logic for clearing up the data that is no longer important for you.</span></span>

 <span data-ttu-id="83e92-210">以上範例使用 `sp_query_store_remove_query` 擴充預存程序，來移除不必要的資料。</span><span class="sxs-lookup"><span data-stu-id="83e92-210">The example above uses the `sp_query_store_remove_query` extended stored procedure for removing unnecessary data.</span></span> <span data-ttu-id="83e92-211">您也可以使用其他兩項程序。</span><span class="sxs-lookup"><span data-stu-id="83e92-211">You can also use two other procedures.</span></span>

-   <span data-ttu-id="83e92-212">`sp_query_store_reset_exec_stats`-清除指定計劃的執行時間統計資料。</span><span class="sxs-lookup"><span data-stu-id="83e92-212">`sp_query_store_reset_exec_stats` - clear runtime statistics for a given plan.</span></span>

-   <span data-ttu-id="83e92-213">`sp_query_store_remove_plan`-移除單一計畫。</span><span class="sxs-lookup"><span data-stu-id="83e92-213">`sp_query_store_remove_plan` - removes a single plan.</span></span>



###  <a name="performance-auditing-and-troubleshooting"></a><a name="Peformance"></a> <span data-ttu-id="83e92-214">效能稽核及疑難排解</span><span class="sxs-lookup"><span data-stu-id="83e92-214">Performance Auditing and Troubleshooting</span></span>
 <span data-ttu-id="83e92-215">因為查詢存放區會透過執行查詢來保留編譯記錄與執行階段計量，所以可以很輕易回答許多有關您工作負載的不同問題。</span><span class="sxs-lookup"><span data-stu-id="83e92-215">Because Query Store keeps history of compilation and runtime metrics throughout query executions there are many different questions you can easily answer with regards to your workload.</span></span>

 <span data-ttu-id="83e92-216">**最近*n*個在資料庫上執行的查詢。**</span><span class="sxs-lookup"><span data-stu-id="83e92-216">**Last *n* queries executed on the database.**</span></span>

```
SELECT TOP 10 qt.query_sql_text, q.query_id, 
    qt.query_text_id, p.plan_id, rs.last_execution_time
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p 
    ON q.query_id = p.query_id 
JOIN sys.query_store_runtime_stats AS rs 
    ON p.plan_id = rs.plan_id
ORDER BY rs.last_execution_time DESC;
```

 <span data-ttu-id="83e92-217">**每個查詢的執行次數。**</span><span class="sxs-lookup"><span data-stu-id="83e92-217">**Number of executions for each query.**</span></span>

```
SELECT q.query_id, qt.query_text_id, qt.query_sql_text, 
    SUM(rs.count_executions) AS total_execution_count
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p 
    ON q.query_id = p.query_id 
JOIN sys.query_store_runtime_stats AS rs 
    ON p.plan_id = rs.plan_id
GROUP BY q.query_id, qt.query_text_id, qt.query_sql_text
ORDER BY total_execution_count DESC;
```

 <span data-ttu-id="83e92-218">**在最後一個小時內，平均執行時間最長的查詢數目。**</span><span class="sxs-lookup"><span data-stu-id="83e92-218">**The number of queries with the longest average execution time within last hour.**</span></span>

```
SELECT TOP 10 rs.avg_duration, qt.query_sql_text, q.query_id,
    qt.query_text_id, p.plan_id, GETUTCDATE() AS CurrentUTCTime, 
    rs.last_execution_time 
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p 
    ON q.query_id = p.query_id 
JOIN sys.query_store_runtime_stats AS rs 
    ON p.plan_id = rs.plan_id
WHERE rs.last_execution_time > DATEADD(hour, -1, GETUTCDATE())
ORDER BY rs.avg_duration DESC;
```

 <span data-ttu-id="83e92-219">**過去24小時內，有相對應的平均資料列計數和執行計數，且平均實體 IO 讀取量最大的查詢數目。**</span><span class="sxs-lookup"><span data-stu-id="83e92-219">**The number of queries that had the biggest average physical IO reads in last 24 hours, with corresponding average row count and execution count.**</span></span>

```
SELECT TOP 10 rs.avg_physical_io_reads, qt.query_sql_text, 
    q.query_id, qt.query_text_id, p.plan_id, rs.runtime_stats_id, 
    rsi.start_time, rsi.end_time, rs.avg_rowcount, rs.count_executions
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p 
    ON q.query_id = p.query_id 
JOIN sys.query_store_runtime_stats AS rs 
    ON p.plan_id = rs.plan_id 
JOIN sys.query_store_runtime_stats_interval AS rsi 
    ON rsi.runtime_stats_interval_id = rs.runtime_stats_interval_id
WHERE rsi.start_time >= DATEADD(hour, -24, GETUTCDATE()) 
ORDER BY rs.avg_physical_io_reads DESC;
```

 <span data-ttu-id="83e92-220">**具有多個計畫的查詢。**</span><span class="sxs-lookup"><span data-stu-id="83e92-220">**Queries with multiple plans.**</span></span> <span data-ttu-id="83e92-221">這些查詢特別有趣的原因是，它們都是因為計劃選擇變更而導致低下的對象。</span><span class="sxs-lookup"><span data-stu-id="83e92-221">These queries are especially interesting because they are candidates for regressions due to plan choice change.</span></span> <span data-ttu-id="83e92-222">下列查詢能找出這些查詢以及所有計劃：</span><span class="sxs-lookup"><span data-stu-id="83e92-222">The following query identifies these queries along with all plans:</span></span>

```
WITH Query_MultPlans
AS
(
    SELECT COUNT(*) AS cnt, q.query_id 
    FROM sys.query_store_query_text AS qt
    JOIN sys.query_store_query AS q
        ON qt.query_text_id = q.query_text_id
    JOIN sys.query_store_plan AS p
        ON p.query_id = q.query_id
    GROUP BY q.query_id
    HAVING COUNT(distinct plan_id) > 1
)

SELECT q.query_id, object_name(object_id) AS ContainingObject, query_sql_text,
plan_id, p.query_plan AS plan_xml,
p.last_compile_start_time, p.last_execution_time
FROM Query_MultPlans AS qm
JOIN sys.query_store_query AS q
    ON qm.query_id = q.query_id
JOIN sys.query_store_plan AS p
    ON q.query_id = p.query_id
JOIN sys.query_store_query_text qt 
    ON qt.query_text_id = q.query_text_id
ORDER BY query_id, plan_id;
```

 <span data-ttu-id="83e92-223">**最近回歸的查詢會比較不同的時間點)  (效能。**</span><span class="sxs-lookup"><span data-stu-id="83e92-223">**Queries that recently regressed in performance (comparing different point in time).**</span></span> <span data-ttu-id="83e92-224">下列查詢範例會傳回所有過去 48 小時內，因為計劃選擇變更而導致執行時間為兩倍的查詢。</span><span class="sxs-lookup"><span data-stu-id="83e92-224">The following query example returns all queries for which execution time doubled in last 48 hours due to a plan choice change.</span></span> <span data-ttu-id="83e92-225">查詢會並列比較所有執行階段。</span><span class="sxs-lookup"><span data-stu-id="83e92-225">Query compares all runtime stat intervals side by side.</span></span>

```
SELECT 
    qt.query_sql_text, 
    q.query_id, 
    qt.query_text_id, 
    rs1.runtime_stats_id AS runtime_stats_id_1,
    rsi1.start_time AS interval_1, 
    p1.plan_id AS plan_1, 
    rs1.avg_duration AS avg_duration_1, 
    rs2.avg_duration AS avg_duration_2,
    p2.plan_id AS plan_2, 
    rsi2.start_time AS interval_2, 
    rs2.runtime_stats_id AS runtime_stats_id_2
FROM sys.query_store_query_text AS qt 
JOIN sys.query_store_query AS q 
    ON qt.query_text_id = q.query_text_id 
JOIN sys.query_store_plan AS p1 
    ON q.query_id = p1.query_id 
JOIN sys.query_store_runtime_stats AS rs1 
    ON p1.plan_id = rs1.plan_id 
JOIN sys.query_store_runtime_stats_interval AS rsi1 
    ON rsi1.runtime_stats_interval_id = rs1.runtime_stats_interval_id 
JOIN sys.query_store_plan AS p2 
    ON q.query_id = p2.query_id 
JOIN sys.query_store_runtime_stats AS rs2 
    ON p2.plan_id = rs2.plan_id 
JOIN sys.query_store_runtime_stats_interval AS rsi2 
    ON rsi2.runtime_stats_interval_id = rs2.runtime_stats_interval_id
WHERE rsi1.start_time > DATEADD(hour, -48, GETUTCDATE()) 
    AND rsi2.start_time > rsi1.start_time 
    AND p1.plan_id <> p2.plan_id
    AND rs2.avg_duration > 2*rs1.avg_duration
ORDER BY q.query_id, rsi1.start_time, rsi2.start_time;
```

 <span data-ttu-id="83e92-226">如果您想要查看所有低下的效能 (不只因方案選擇變更的相關項目)，只要從上一個查詢移除條件 `AND p1.plan_id <> p2.plan_id` 即可。</span><span class="sxs-lookup"><span data-stu-id="83e92-226">If you want to see performance all regressions (not only those related to plan choice change) than just remove condition `AND p1.plan_id <> p2.plan_id` from the previous query.</span></span>

 <span data-ttu-id="83e92-227">**最近回歸效能 (比較最近與歷程記錄執行) 的查詢。**</span><span class="sxs-lookup"><span data-stu-id="83e92-227">**Queries that recently regressed in performance (comparing recent vs. history execution).**</span></span> <span data-ttu-id="83e92-228">下一個查詢會依據執行時段，比較查詢的執行。</span><span class="sxs-lookup"><span data-stu-id="83e92-228">The next query compares query execution based periods of execution.</span></span> <span data-ttu-id="83e92-229">在此特別的範例中，查詢會比較最近期間內 (1 小時) 與記錄期間 (前一天) 的執行，並找出因 additional_duration_workload 所引發的項目。</span><span class="sxs-lookup"><span data-stu-id="83e92-229">In this particular example the query compares execution in recent period (1 hour) vs. history period (last day) and identifies those that introduced additional_duration_workload.</span></span> <span data-ttu-id="83e92-230">此度量會計算最近的平均執行與記錄的平均執行之間的差，乘以最近執行的數目。</span><span class="sxs-lookup"><span data-stu-id="83e92-230">This metrics is calculated as a difference between recent average execution and history average execution multiplied by the number of recent executions.</span></span> <span data-ttu-id="83e92-231">它實際上代表與記錄相較，最近的執行引發了多少額外的時間：</span><span class="sxs-lookup"><span data-stu-id="83e92-231">It actually represents how much of additional duration recent executions introduced compared to history:</span></span>

```
--- "Recent" workload - last 1 hour
DECLARE @recent_start_time datetimeoffset;
DECLARE @recent_end_time datetimeoffset;
SET @recent_start_time = DATEADD(hour, -1, SYSUTCDATETIME());
SET @recent_end_time = SYSUTCDATETIME();

--- "History" workload
DECLARE @history_start_time datetimeoffset;
DECLARE @history_end_time datetimeoffset;
SET @history_start_time = DATEADD(hour, -24, SYSUTCDATETIME());
SET @history_end_time = SYSUTCDATETIME();

WITH
hist AS
(
    SELECT 
        p.query_id query_id, 
        CONVERT(float, SUM(rs.avg_duration*rs.count_executions)) total_duration, 
        SUM(rs.count_executions) count_executions,
        COUNT(distinct p.plan_id) num_plans 
     FROM sys.query_store_runtime_stats AS rs
        JOIN sys.query_store_plan p ON p.plan_id = rs.plan_id
    WHERE  (rs.first_execution_time >= @history_start_time AND rs.last_execution_time < @history_end_time)
        OR (rs.first_execution_time <= @history_start_time AND rs.last_execution_time > @history_start_time)
        OR (rs.first_execution_time <= @history_end_time AND rs.last_execution_time > @history_end_time)
    GROUP BY p.query_id
),
recent AS
(
    SELECT 
        p.query_id query_id, 
        CONVERT(float, SUM(rs.avg_duration*rs.count_executions)) total_duration, 
        SUM(rs.count_executions) count_executions,
        COUNT(distinct p.plan_id) num_plans 
    FROM sys.query_store_runtime_stats AS rs
        JOIN sys.query_store_plan p ON p.plan_id = rs.plan_id
    WHERE  (rs.first_execution_time >= @recent_start_time AND rs.last_execution_time < @recent_end_time)
        OR (rs.first_execution_time <= @recent_start_time AND rs.last_execution_time > @recent_start_time)
        OR (rs.first_execution_time <= @recent_end_time AND rs.last_execution_time > @recent_end_time)
    GROUP BY p.query_id
)
SELECT 
    results.query_id query_id,
    results.query_text query_text,
    results.additional_duration_workload additional_duration_workload,
    results.total_duration_recent total_duration_recent,
    results.total_duration_hist total_duration_hist,
    ISNULL(results.count_executions_recent, 0) count_executions_recent,
    ISNULL(results.count_executions_hist, 0) count_executions_hist 
FROM
(
    SELECT
        hist.query_id query_id,
        qt.query_sql_text query_text,
        ROUND(CONVERT(float, recent.total_duration/recent.count_executions-hist.total_duration/hist.count_executions)*(recent.count_executions), 2) AS additional_duration_workload,
        ROUND(recent.total_duration, 2) total_duration_recent, 
        ROUND(hist.total_duration, 2) total_duration_hist,
        recent.count_executions count_executions_recent,
        hist.count_executions count_executions_hist   
    FROM hist 
        JOIN recent 
            ON hist.query_id = recent.query_id 
        JOIN sys.query_store_query AS q 
            ON q.query_id = hist.query_id
        JOIN sys.query_store_query_text AS qt 
            ON q.query_text_id = qt.query_text_id    
) AS results
WHERE additional_duration_workload > 0
ORDER BY additional_duration_workload DESC
OPTION (MERGE JOIN);
```



###  <a name="maintaining-query-performance-stability"></a><a name="Stability"></a><span data-ttu-id="83e92-232">維護查詢效能穩定性</span><span class="sxs-lookup"><span data-stu-id="83e92-232">Maintaining Query Performance Stability</span></span>
 <span data-ttu-id="83e92-233">若是執行多次的查詢，您可會注意到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用不同的計劃，而產生了不同的資源使用率與持續時間。</span><span class="sxs-lookup"><span data-stu-id="83e92-233">For queries that are executed multiple times you may notice that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] used different plans which resulted in different resource utilization and duration.</span></span> <span data-ttu-id="83e92-234">您可利用查詢存放區，輕鬆偵測查詢效能何時低下，以及判斷在意的時段中的最佳計劃。</span><span class="sxs-lookup"><span data-stu-id="83e92-234">With Query Store you can easily detect when the query performance regressed and determine the optimal plan within a period of interest.</span></span> <span data-ttu-id="83e92-235">然後可以對未來的查詢強制執行該最佳計劃。</span><span class="sxs-lookup"><span data-stu-id="83e92-235">Then you can force that optimal plan for future query execution.</span></span>

 <span data-ttu-id="83e92-236">也可以為具有參數 (自動設定參數或手動設定參數) 的查詢，找出不一致的查詢效能。</span><span class="sxs-lookup"><span data-stu-id="83e92-236">You can also identify inconsistent query performance for a query with parameters (either auto- parameterized or manually parameterized).</span></span> <span data-ttu-id="83e92-237">您可以在不同的計劃間，找出適合所有或大部分參數值的良好且快速之計劃，並強制執行該計劃，為更多使用者案例留下可預測的效能。</span><span class="sxs-lookup"><span data-stu-id="83e92-237">Among different plans you can identify plan which is fast and optimal enough for all or most of the parameter values and force that plan; keeping predictable performance for the wider set of user scenarios.</span></span>

 <span data-ttu-id="83e92-238">**為查詢強制執行計劃 (套用強制原則)。**</span><span class="sxs-lookup"><span data-stu-id="83e92-238">**Force or a plan for a query (apply forcing policy).**</span></span> <span data-ttu-id="83e92-239">若要為特定的查詢強制執行一項計劃，則每次查詢執行時，就會強制以該計劃執行。</span><span class="sxs-lookup"><span data-stu-id="83e92-239">When a plan is forced for a certain query, every time a query comes to execution it will be executed with the plan that is forced.</span></span>

```
EXEC sp_query_store_force_plan @query_id = 48, @plan_id = 49;
```

 <span data-ttu-id="83e92-240">使用 `sp_query_store_force_plan` 時，只能強制執行查詢存放區所記錄的計劃，做為該查詢的計劃。</span><span class="sxs-lookup"><span data-stu-id="83e92-240">When using `sp_query_store_force_plan` you can only force plans that were recorded by Query Store as a plan for that query.</span></span> <span data-ttu-id="83e92-241">換句話說，可用於查詢的計劃，是已經用於執行 Q1 的計劃 (查詢存放區當時在作用中)。</span><span class="sxs-lookup"><span data-stu-id="83e92-241">In other words, the only plans available for a query are those that were already used to execute Q1 while Query Store was active.</span></span>

 <span data-ttu-id="83e92-242">**為查詢移除強制執行計畫。**</span><span class="sxs-lookup"><span data-stu-id="83e92-242">**Remove plan forcing for a query.**</span></span> <span data-ttu-id="83e92-243">若要再次依賴 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 查詢最佳化工具來計算最佳的查詢計劃，請使用 `sp_query_store_unforce_plan` 來取消強制執行針對查詢所選取的計畫。</span><span class="sxs-lookup"><span data-stu-id="83e92-243">To rely again on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] query optimizer to calculate the optimal query plan, use `sp_query_store_unforce_plan` to unforce the plan that was selected for the query.</span></span>

```
EXEC sp_query_store_unforce_plan @query_id = 48, @plan_id = 49;
```



## <a name="see-also"></a><span data-ttu-id="83e92-244">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83e92-244">See Also</span></span>
 <span data-ttu-id="83e92-245">[監視和微調效能](../performance/monitor-and-tune-for-performance.md)[效能監視和微調工具](../performance/performance-monitoring-and-tuning-tools.md)[開啟活動監視器 &#40;SQL Server Management Studio&#41;](../performance-monitor/open-activity-monitor-sql-server-management-studio.md) [活動監視器](../performance-monitor/activity-monitor.md)</span><span class="sxs-lookup"><span data-stu-id="83e92-245">[Monitor and Tune for Performance](../performance/monitor-and-tune-for-performance.md) [Performance Monitoring and Tuning Tools](../performance/performance-monitoring-and-tuning-tools.md) [Open Activity Monitor &#40;SQL Server Management Studio&#41;](../performance-monitor/open-activity-monitor-sql-server-management-studio.md) [Activity Monitor](../performance-monitor/activity-monitor.md)</span></span>


