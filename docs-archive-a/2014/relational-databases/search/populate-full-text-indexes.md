---
title: 擴展全文檢索索引 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- index populations [full-text search]
- incremental populations [full-text search]
- populations [full-text search]
- full-text search [SQL Server], populations
- crawls [full-text search]
- automatic full-text index updates
- change tracking-based populations [full-text search]
- manual updates [full-text search]
- manual populations [full-text search]
- auto populations [full-text search]
- full-text indexes [SQL Server], key column
- full populations [full-text search]
- full-text indexes [SQL Server], populations
ms.assetid: 76767b20-ef55-49ce-8dc4-e77cb8ff618a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9ab93a3514fa260c8c3836da85c767da3c3051a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598789"
---
# <a name="populate-full-text-indexes"></a><span data-ttu-id="e36d3-102">擴展全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="e36d3-102">Populate Full-Text Indexes</span></span>
  <span data-ttu-id="e36d3-103">建立和維護全文檢索索引包括使用稱為「母體擴展」(Population) (也稱為「搜耙」(Crawl)) 的處理序來擴展索引。</span><span class="sxs-lookup"><span data-stu-id="e36d3-103">Creating and maintaining a full-text index involves populating the index by using a process called a *population* (also known as a *crawl*).</span></span>  
  
##  <a name="types-of-population"></a><a name="types"></a><span data-ttu-id="e36d3-104">填入類型</span><span class="sxs-lookup"><span data-stu-id="e36d3-104">Types of Population</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="e36d3-105">支援下列類型的擴展：完整擴展、以變更追蹤為基礎的自動或手動擴展，以及以累加時間戳記為基礎的人口。</span><span class="sxs-lookup"><span data-stu-id="e36d3-105">supports the following types of population: full population, change tracking-based automatic or manual population, and incremental timestamp-based population.</span></span>  
  
### <a name="full-population"></a><span data-ttu-id="e36d3-106">完整母體擴展</span><span class="sxs-lookup"><span data-stu-id="e36d3-106">Full Population</span></span>  
 <span data-ttu-id="e36d3-107">在完整母體擴展期間，系統會針對資料表或索引檢視表的所有資料列建立索引項目。</span><span class="sxs-lookup"><span data-stu-id="e36d3-107">During a full population, index entries are built for all the rows of a table or indexed view.</span></span> <span data-ttu-id="e36d3-108">全文檢索索引的完整母體擴展會針對基底資料表或索引檢視表的所有資料列建立索引項目。</span><span class="sxs-lookup"><span data-stu-id="e36d3-108">A full population of a full-text index, builds index entries for all the rows of the base table or indexed view.</span></span>  
  
 <span data-ttu-id="e36d3-109">根據預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會在建立新的全文檢索索引時，立即進行完整母體擴展。</span><span class="sxs-lookup"><span data-stu-id="e36d3-109">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] populates a new full-text index fully as soon as it is created.</span></span> <span data-ttu-id="e36d3-110">不過，完整母體擴展可能會耗用大量資源。</span><span class="sxs-lookup"><span data-stu-id="e36d3-110">However, a full population can consume a significant amount of resources.</span></span> <span data-ttu-id="e36d3-111">因此，在尖峰期間建立全文檢索索引時，最佳作法通常是延遲完整母體擴展直到離峰時間為止，尤其是全文檢索索引的基底資料表很龐大時。</span><span class="sxs-lookup"><span data-stu-id="e36d3-111">Therefore, when creating a full-text index during peak periods, it is often a best practice to delay the full population until an off-peak time, particularly if the base table of an full-text index is large.</span></span> <span data-ttu-id="e36d3-112">不過，此索引所屬的全文檢索目錄要等到所有全文檢索索引都擴展之後才能使用。</span><span class="sxs-lookup"><span data-stu-id="e36d3-112">However, the full-text catalog to which the index belongs is not usable until all of its full-text indexes are populated.</span></span> <span data-ttu-id="e36d3-113">若要建立全文檢索索引，但不立即擴展，請在 CREATE FULLTEXT INDEX 陳述式中指定 CHANGE_TRACKING OFF、NO POPULATION 子句。</span><span class="sxs-lookup"><span data-stu-id="e36d3-113">To create a full-text index without populating it immediately, specify the CHANGE_TRACKING OFF, NO POPULATION clause in the CREATE FULLTEXT INDEX statement.</span></span> <span data-ttu-id="e36d3-114">如果您指定 CHANGE_TRACKING MANUAL，全文檢索引擎就會使用此陳述式。</span><span class="sxs-lookup"><span data-stu-id="e36d3-114">If you specify CHANGE_TRACKING MANUAL, the Full-Text Engine uses statement.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="e36d3-115">將不會填入新的全文檢索索引，直到您使用「開始完整擴展」或「啟動增量擴展」子句執行 ALTER 全文檢索索引語句為止。</span><span class="sxs-lookup"><span data-stu-id="e36d3-115">will not populate the new full-text index until you execute an ALTER FULLTEXT INDEX statement using the START FULL POPULATION or START INCREMENTAL POPULATION clause.</span></span> <span data-ttu-id="e36d3-116">如需詳細資訊，請參閱本主題稍後的範例「A.</span><span class="sxs-lookup"><span data-stu-id="e36d3-116">For more information, see examples "A.</span></span> <span data-ttu-id="e36d3-117">建立全文檢索索引但不執行完整母體擴展」以及「B.</span><span class="sxs-lookup"><span data-stu-id="e36d3-117">Creating a full-text index without running a full population" and "B.</span></span> <span data-ttu-id="e36d3-118">針對資料表執行完整母體擴展」。</span><span class="sxs-lookup"><span data-stu-id="e36d3-118">Running a full population on table," later in this topic.</span></span>  
  

  
### <a name="change-tracking-based-population"></a><span data-ttu-id="e36d3-119">以變更追蹤為基礎的母體擴展</span><span class="sxs-lookup"><span data-stu-id="e36d3-119">Change Tracking-Based Population</span></span>  
 <span data-ttu-id="e36d3-120">在初始完整母體擴展之後，您可以選擇性地使用變更追蹤來維護全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="e36d3-120">Optionally, you can use change tracking to maintain a full-text index after its initial full population.</span></span> <span data-ttu-id="e36d3-121">因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會維護追蹤上一次母體擴展以來對基底資料表所做之變更的資料表，所以存在與變更追蹤相關聯的少量負擔。</span><span class="sxs-lookup"><span data-stu-id="e36d3-121">There is a small overhead associated with change tracking because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] maintains a table in which it tracks changes to the base table since the last population.</span></span> <span data-ttu-id="e36d3-122">使用變更追蹤時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會在基底資料表或索引檢視表中維護已經由更新、刪除或插入所修改之資料列的記錄。</span><span class="sxs-lookup"><span data-stu-id="e36d3-122">When change tracking is used, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] maintains a record of the rows in the base table or indexed view that have been modified by updates, deletes, or inserts.</span></span> <span data-ttu-id="e36d3-123">透過 WRITETEXT 和 UPDATETEXT 的資料變更並不會反映在全文檢索索引中，變更追蹤並不會收取這些變更。</span><span class="sxs-lookup"><span data-stu-id="e36d3-123">Data changes through WRITETEXT and UPDATETEXT are not reflected in the full-text index, and are not picked up with change tracking.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e36d3-124">如需包含 `timestamp` 資料行的資料表，您可以使用累加母體擴展。</span><span class="sxs-lookup"><span data-stu-id="e36d3-124">For tables containing a `timestamp` column, you can use incremental populations.</span></span>  
  
 <span data-ttu-id="e36d3-125">在建立索引期間啟用變更追蹤時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 就會在建立新的全文檢索索引之後，立即完整擴展新的全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="e36d3-125">When change tracking is enabled during index creation, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fully populates the new full-text index immediately after it is created.</span></span> <span data-ttu-id="e36d3-126">之後，系統會追蹤並傳播變更至全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="e36d3-126">Thereafter, changes are tracked and propagated to the full-text index.</span></span> <span data-ttu-id="e36d3-127">變更追蹤有兩種類型：自動 (CHANGE_TRACKING AUTO 選項) 和手動 (CHANGE_TRACKING MANUAL 選項)。</span><span class="sxs-lookup"><span data-stu-id="e36d3-127">There are two types of change tracking, automatic (CHANGE_TRACKING AUTO option) and manual (CHANGE_TRACKING MANUAL option).</span></span> <span data-ttu-id="e36d3-128">自動變更追蹤是預設的行為。</span><span class="sxs-lookup"><span data-stu-id="e36d3-128">Automatic change tracking is the default behavior.</span></span>  
  
 <span data-ttu-id="e36d3-129">變更追蹤的類型會決定擴展全文檢索索引的方式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e36d3-129">The type of change tracking determines how the full-text index is populated, as follows:</span></span>  
  
-   <span data-ttu-id="e36d3-130">自動母體擴展</span><span class="sxs-lookup"><span data-stu-id="e36d3-130">Automatic population</span></span>  
  
     <span data-ttu-id="e36d3-131">根據預設，或者如果您指定了 CHANGE_TRACKING AUTO，全文檢索引擎就會針對全文檢索索引使用自動母體擴展。</span><span class="sxs-lookup"><span data-stu-id="e36d3-131">By default, or if you specify CHANGE_TRACKING AUTO, the Full-Text Engine uses automatic population on the full-text index.</span></span> <span data-ttu-id="e36d3-132">初始完整母體擴展完成之後，系統就會追蹤變更，因為基底資料表中的資料已修改，而且追蹤的變更會自動傳播。</span><span class="sxs-lookup"><span data-stu-id="e36d3-132">After the initial full population completes, changes are tracked as data is modified in the base table, and the tracked changes are propagated automatically.</span></span> <span data-ttu-id="e36d3-133">不過，全文檢索索引會在背景更新，所以傳播的變更可能不會立即反映在索引中。</span><span class="sxs-lookup"><span data-stu-id="e36d3-133">The full-text index is updated in the background, however, so propagated changes might not be reflected immediately in the index.</span></span>  
  
     <span data-ttu-id="e36d3-134">**若要使用自動母體擴展來設定追蹤變更**</span><span class="sxs-lookup"><span data-stu-id="e36d3-134">**To set up tracking changes with automatic population**</span></span>  
  
    -   <span data-ttu-id="e36d3-135">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ...WITH CHANGE_TRACKING AUTO</span><span class="sxs-lookup"><span data-stu-id="e36d3-135">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ... WITH CHANGE_TRACKING AUTO</span></span>  
  
    -   <span data-ttu-id="e36d3-136">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ...SET CHANGE_TRACKING AUTO</span><span class="sxs-lookup"><span data-stu-id="e36d3-136">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ... SET CHANGE_TRACKING AUTO</span></span>  
  
     <span data-ttu-id="e36d3-137">如需詳細資訊，請參閱本主題稍後的範例「E.</span><span class="sxs-lookup"><span data-stu-id="e36d3-137">For more information, see example "E.</span></span> <span data-ttu-id="e36d3-138">將全文檢索索引更改成使用自動變更追蹤」。</span><span class="sxs-lookup"><span data-stu-id="e36d3-138">Altering a full-text index to use automatic change tracking," later in this topic.</span></span>  
  
-   <span data-ttu-id="e36d3-139">手動母體擴展</span><span class="sxs-lookup"><span data-stu-id="e36d3-139">Manual population</span></span>  
  
     <span data-ttu-id="e36d3-140">如果您指定了 CHANGE_TRACKING MANUAL，全文檢索引擎就會針對全文檢索索引使用手動母體擴展。</span><span class="sxs-lookup"><span data-stu-id="e36d3-140">If you specify CHANGE_TRACKING MANUAL, the Full-Text Engine uses manual population on the full-text index.</span></span> <span data-ttu-id="e36d3-141">初始完整母體擴展完成之後，系統就會追蹤變更，因為基底資料表中的資料已修改。</span><span class="sxs-lookup"><span data-stu-id="e36d3-141">After the initial full population completes, changes are tracked as data is modified in the base table.</span></span> <span data-ttu-id="e36d3-142">不過，它們不會傳播至全文檢索索引，直到您執行 ALTER FULLTEXT INDEX ...START UPDATE POPULATION 陳述式來手動套用變更。</span><span class="sxs-lookup"><span data-stu-id="e36d3-142">However, they are not propagated to the full-text index until you execute an ALTER FULLTEXT INDEX ... START UPDATE POPULATION statement.</span></span> <span data-ttu-id="e36d3-143">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 來定期呼叫這個 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e36d3-143">You can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to call this [!INCLUDE[tsql](../../includes/tsql-md.md)] statement periodically.</span></span>  
  
     <span data-ttu-id="e36d3-144">**若要使用手動母體擴展來啟動追蹤變更**</span><span class="sxs-lookup"><span data-stu-id="e36d3-144">**To start tracking changes with manual population**</span></span>  
  
    -   <span data-ttu-id="e36d3-145">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ...WITH CHANGE_TRACKING MANUAL</span><span class="sxs-lookup"><span data-stu-id="e36d3-145">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ... WITH CHANGE_TRACKING MANUAL</span></span>  
  
    -   <span data-ttu-id="e36d3-146">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ...SET CHANGE_TRACKING MANUAL</span><span class="sxs-lookup"><span data-stu-id="e36d3-146">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ... SET CHANGE_TRACKING MANUAL</span></span>  
  
     <span data-ttu-id="e36d3-147">如需詳細資訊，請參閱本主題稍後的範例「C.</span><span class="sxs-lookup"><span data-stu-id="e36d3-147">For more information, see examples "C.</span></span> <span data-ttu-id="e36d3-148">使用手動變更追蹤來建立全文檢索索引」以及「D.</span><span class="sxs-lookup"><span data-stu-id="e36d3-148">Creating a full-text index with manual change tracking" and "D.</span></span> <span data-ttu-id="e36d3-149">執行手動母體擴展」。</span><span class="sxs-lookup"><span data-stu-id="e36d3-149">Running a manual population," later in this topic.</span></span>  
  
 <span data-ttu-id="e36d3-150">**若要關閉變更追蹤**</span><span class="sxs-lookup"><span data-stu-id="e36d3-150">**To turn off change tracking**</span></span>  
  
-   <span data-ttu-id="e36d3-151">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ...WITH CHANGE_TRACKING OFF</span><span class="sxs-lookup"><span data-stu-id="e36d3-151">[CREATE FULLTEXT INDEX](/sql/t-sql/statements/create-fulltext-index-transact-sql) ... WITH CHANGE_TRACKING OFF</span></span>  
  
-   <span data-ttu-id="e36d3-152">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ...SET CHANGE_TRACKING OFF</span><span class="sxs-lookup"><span data-stu-id="e36d3-152">[ALTER FULLTEXT INDEX](/sql/t-sql/statements/alter-fulltext-index-transact-sql) ... SET CHANGE_TRACKING OFF</span></span>  
  

  
### <a name="incremental-timestamp-based-population"></a><span data-ttu-id="e36d3-153">以時間戳記為基礎的累加母體擴展</span><span class="sxs-lookup"><span data-stu-id="e36d3-153">Incremental Timestamp-Based Population</span></span>  
 <span data-ttu-id="e36d3-154">累加母體擴展是手動擴展全文檢索索引的替代機制。</span><span class="sxs-lookup"><span data-stu-id="e36d3-154">An incremental population is an alternative mechanism for manually populating a full-text index.</span></span> <span data-ttu-id="e36d3-155">您可以針對將 CHANGE_TRACKING 設定為 MANUAL 或 OFF 的全文檢索索引執行累加母體擴展。</span><span class="sxs-lookup"><span data-stu-id="e36d3-155">You can run an incremental population for a full-text index that has CHANGE_TRACKING set to MANUAL or OFF.</span></span> <span data-ttu-id="e36d3-156">如果全文檢索索引的第一個母體擴展是累加母體擴展，它就會建立所有資料列的索引，讓它相當於完整母體擴展。</span><span class="sxs-lookup"><span data-stu-id="e36d3-156">If the first population on a full-text index is an incremental population, it indexes all rows, making it equivalent to a full population.</span></span>  
  
 <span data-ttu-id="e36d3-157">累加母體擴展的執行要件是，索引資料表必須包含 `timestamp` 資料類型資料行。</span><span class="sxs-lookup"><span data-stu-id="e36d3-157">The requirement for incremental population is that the indexed table must have a column of the `timestamp` data type.</span></span> <span data-ttu-id="e36d3-158">少了 `timestamp` 資料行，就無法執行累加母體擴展。</span><span class="sxs-lookup"><span data-stu-id="e36d3-158">If a `timestamp` column does not exist, incremental population cannot be performed.</span></span> <span data-ttu-id="e36d3-159">對不含 `timestamp` 資料行的資料表提出累加母體擴展要求的話，會導致執行完整母體擴展作業。</span><span class="sxs-lookup"><span data-stu-id="e36d3-159">A request for incremental population on a table without a `timestamp` column results in a full population operation.</span></span> <span data-ttu-id="e36d3-160">此外，如果上一次母體擴展以來，影響資料表全文檢索索引的任何中繼資料已變更，便會以完整母體擴展的方式實作累加母體擴展。</span><span class="sxs-lookup"><span data-stu-id="e36d3-160">Also, if any metadata that affects the full-text index for the table has changed since the last population, incremental population requests are implemented as full populations.</span></span> <span data-ttu-id="e36d3-161">這包括由於更改任何資料行、索引或全文檢索索引定義所導致的中繼資料變更。</span><span class="sxs-lookup"><span data-stu-id="e36d3-161">This includes metadata changes caused by altering any column, index, or full-text index definitions.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e36d3-162">會使用 `timestamp` 資料行來識別上一次母體擴展以來已經變更的資料列。</span><span class="sxs-lookup"><span data-stu-id="e36d3-162">uses the `timestamp` column to identify rows that have changed since the last population.</span></span> <span data-ttu-id="e36d3-163">然後，累加母體擴展會針對在上一次母體擴展之後或進行時加入、刪除或修改的資料列，更新全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="e36d3-163">The incremental population then updates the full-text index for rows added, deleted, or modified after the last population, or while the last population was in progress.</span></span> <span data-ttu-id="e36d3-164">如果資料表遇到大量插入作業，使用累加母體擴展可能會比使用手動母體擴展更有效率。</span><span class="sxs-lookup"><span data-stu-id="e36d3-164">If a table experiences a high volume of inserts, using incremental population can be more efficient that using manual population.</span></span>  
  
 <span data-ttu-id="e36d3-165">母體擴展結束時，全文檢索引擎會記錄新的 `timestamp` 值。</span><span class="sxs-lookup"><span data-stu-id="e36d3-165">At the end of a population, the Full-Text Engine records a new `timestamp` value.</span></span> <span data-ttu-id="e36d3-166">這個值就是「SQL 收集程式」所遇過的最大 `timestamp` 值。</span><span class="sxs-lookup"><span data-stu-id="e36d3-166">This value is the largest `timestamp` value that SQL Gatherer has encountered.</span></span> <span data-ttu-id="e36d3-167">此值會在後續的累加母體擴展啟動時使用。</span><span class="sxs-lookup"><span data-stu-id="e36d3-167">This value will be used when a subsequent incremental population starts.</span></span>  
  
 <span data-ttu-id="e36d3-168">若要執行累加母體擴展，請使用 START INCREMENTAL POPULATION 子句來執行 ALTER FULLTEXT INDEX 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e36d3-168">To run an incremental population, execute an ALTER FULLTEXT INDEX statement using the START INCREMENTAL POPULATION clause.</span></span>  
  

  
##  <a name="examples-of-populating-full-text-indexes"></a><a name="examples"></a><span data-ttu-id="e36d3-169">填入全文檢索索引的範例</span><span class="sxs-lookup"><span data-stu-id="e36d3-169">Examples of Populating Full-Text Indexes</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e36d3-170">本節中的範例使用 `Production.Document` 範例資料庫的 `HumanResources.JobCandidate` 或 `AdventureWorks` 資料表。</span><span class="sxs-lookup"><span data-stu-id="e36d3-170">The examples in this section use the `Production.Document` or `HumanResources.JobCandidate` table of the `AdventureWorks` sample database.</span></span>  
  
### <a name="a-creating-a-full-text-index-without-running-a-full-population"></a><span data-ttu-id="e36d3-171">A.</span><span class="sxs-lookup"><span data-stu-id="e36d3-171">A.</span></span> <span data-ttu-id="e36d3-172">建立全文檢索索引，但不執行完整母體擴展</span><span class="sxs-lookup"><span data-stu-id="e36d3-172">Creating a full-text index without running a full population</span></span>  
 <span data-ttu-id="e36d3-173">下列範例會針對 `Production.Document` 範例資料庫的 `AdventureWorks` 資料表建立全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="e36d3-173">The following example creates a full-text index on the `Production.Document` table of the `AdventureWorks` sample database.</span></span> <span data-ttu-id="e36d3-174">這個範例會使用 WITH CHANGE_TRACKING OFF、NO POPULATION 來延遲初始完整母體擴展。</span><span class="sxs-lookup"><span data-stu-id="e36d3-174">This example uses WITH CHANGE_TRACKING OFF, NO POPULATION to delay the initial full population.</span></span>  
  
```  
CREATE UNIQUE INDEX ui_ukDoc ON Production.Document(DocumentID);  
CREATE FULLTEXT CATALOG AW_Production_FTCat;  
CREATE FULLTEXT INDEX ON Production.Document  
(  
    Document                         --Full-text index column name   
        TYPE COLUMN FileExtension    --Name of column that contains file type information  
        Language 1033                 --1033 is LCID for the English language  
)  
    KEY INDEX ui_ukDoc  
    ON AW_Production_FTCat  
    WITH CHANGE_TRACKING OFF, NO POPULATION;  
GO  
  
```  
  
### <a name="b-running-a-full-population-on-table"></a><span data-ttu-id="e36d3-175">B.</span><span class="sxs-lookup"><span data-stu-id="e36d3-175">B.</span></span> <span data-ttu-id="e36d3-176">執行資料表的完整母體擴展</span><span class="sxs-lookup"><span data-stu-id="e36d3-176">Running a full population on table</span></span>  
 <span data-ttu-id="e36d3-177">下列範例會針對 `Production.Document` 範例資料庫的 `AdventureWorks` 資料表執行完整母體擴展。</span><span class="sxs-lookup"><span data-stu-id="e36d3-177">The following example runs a full population on the `Production.Document` table of the `AdventureWorks` sample database.</span></span>  
  
```  
ALTER FULLTEXT INDEX ON Production.Document  
   START FULL POPULATION;  
```  
  
### <a name="c-creating-a-full-text-index-with-manual-change-tracking"></a><span data-ttu-id="e36d3-178">C.</span><span class="sxs-lookup"><span data-stu-id="e36d3-178">C.</span></span> <span data-ttu-id="e36d3-179">使用手動變更追蹤來建立全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="e36d3-179">Creating a full-text index with manual change tracking</span></span>  
 <span data-ttu-id="e36d3-180">下列範例會針對 `HumanResources.JobCandidate` 範例資料庫的 `AdventureWorks` 資料表建立使用變更追蹤搭配手動母體擴展的全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="e36d3-180">The following example creates a full-text index that will use change tracking with manual population on the `HumanResources.JobCandidate` table of the `AdventureWorks` sample database.</span></span>  
  
```  
USE AdventureWorks;  
GO  
CREATE UNIQUE INDEX ui_ukJobCand ON HumanResources.JobCandidate(JobCandidateID);  
CREATE FULLTEXT CATALOG ft AS DEFAULT;  
CREATE FULLTEXT INDEX ON HumanResources.JobCandidate(Resume)   
   KEY INDEX ui_ukJobCand   
   WITH CHANGE_TRACKING=MANUAL;  
GO  
```  
  
### <a name="d-running-a-manual-population"></a><span data-ttu-id="e36d3-181">D.</span><span class="sxs-lookup"><span data-stu-id="e36d3-181">D.</span></span> <span data-ttu-id="e36d3-182">執行手動母體擴展</span><span class="sxs-lookup"><span data-stu-id="e36d3-182">Running a manual population</span></span>  
 <span data-ttu-id="e36d3-183">下列範例會針對 `HumanResources.JobCandidate` 範例資料庫之 `AdventureWorks` 資料表的變更追蹤全文檢索索引執行手動母體擴展。</span><span class="sxs-lookup"><span data-stu-id="e36d3-183">The following example runs a manual population on the change-tracked full-text index of the `HumanResources.JobCandidate` table of the `AdventureWorks` sample database.</span></span>  
  
```  
USE AdventureWorks;  
GO  
ALTER FULLTEXT INDEX ON HumanResources.JobCandidate START UPDATE POPULATION;  
GO  
```  
  
### <a name="e-altering-a-full-text-index-to-use-automatic-change-tracking"></a><span data-ttu-id="e36d3-184">E.</span><span class="sxs-lookup"><span data-stu-id="e36d3-184">E.</span></span> <span data-ttu-id="e36d3-185">將全文檢索索引更改成使用自動變更追蹤</span><span class="sxs-lookup"><span data-stu-id="e36d3-185">Altering a full-text index to use automatic change tracking</span></span>  
 <span data-ttu-id="e36d3-186">下列範例會將 `HumanResources.JobCandidate` 範例資料庫之 `AdventureWorks` 資料表的全文檢索索引變更成使用變更追蹤搭配自動母體擴展。</span><span class="sxs-lookup"><span data-stu-id="e36d3-186">The following example changes the full-text index of the `HumanResources.JobCandidate` table of the `AdventureWorks` sample database to use change tracking with automatic population.</span></span>  
  
```  
USE AdventureWorks;  
GO  
ALTER FULLTEXT INDEX ON HumanResources.JobCandidate SET CHANGE_TRACKING AUTO;  
GO   
```  
  

  
##  <a name="creating-or-changing-a-schedule-for-incremental-population"></a><a name="create"></a><span data-ttu-id="e36d3-187">建立或變更增量擴展的排程</span><span class="sxs-lookup"><span data-stu-id="e36d3-187">Creating or Changing a Schedule for Incremental Population</span></span>  
  
#### <a name="to-create-or-change-a-schedule-for-incremental-population-in-management-studio"></a><span data-ttu-id="e36d3-188">在 Management Studio 中建立或變更累加母體擴展的排程</span><span class="sxs-lookup"><span data-stu-id="e36d3-188">To create or change a schedule for incremental population in Management Studio</span></span>  
  
1.  <span data-ttu-id="e36d3-189">在 [物件總管] 中，展開伺服器。</span><span class="sxs-lookup"><span data-stu-id="e36d3-189">In Object Explorer, expand the server.</span></span>  
  
2.  <span data-ttu-id="e36d3-190">展開 [資料庫]，然後展開包含全文檢索索引的資料庫。</span><span class="sxs-lookup"><span data-stu-id="e36d3-190">Expand **Databases**, and then expand the database that contains the full-text index.</span></span>  
  
3.  <span data-ttu-id="e36d3-191">展開 **[資料表]** 。</span><span class="sxs-lookup"><span data-stu-id="e36d3-191">Expand **Tables**.</span></span>  
  
 <span data-ttu-id="e36d3-192">以滑鼠右鍵按一下已定義全文檢索索引的資料表、選取 [全文檢索索引]，然後按一下 [全文檢索索引] 內容功能表上的 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="e36d3-192">Right-click the table on which the full-text index is defined, select **Full-Text index**, and on the **Full-Text index** context menu, click **Properties**.</span></span> <span data-ttu-id="e36d3-193">這樣就會開啟 [全文檢索索引屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e36d3-193">This opens the **Full-text index Properties** dialog box.</span></span>  
  
1.  <span data-ttu-id="e36d3-194">在 [**選取頁面**] 窗格中，選取 [排程]。</span><span class="sxs-lookup"><span data-stu-id="e36d3-194">In the **Select a page** pane, select Schedules.</span></span>  
  
     <span data-ttu-id="e36d3-195">您可以使用這個頁面來建立或管理 SQL Server Agent 作業的排程，以便針對全文檢索索引的基底資料表或索引檢視表啟動累加資料表母體擴展。</span><span class="sxs-lookup"><span data-stu-id="e36d3-195">Use this page to create or manage schedules for a SQL Server Agent job that starts an incremental table population on the base table or indexed view of the full-text index.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e36d3-196">如果基底資料表或檢視表沒有包含 `timestamp` 資料類型的資料行，就會執行完整母體擴展。</span><span class="sxs-lookup"><span data-stu-id="e36d3-196">If the base table or view does not contain a column of the `timestamp` data type, a full population is performed.</span></span>  
  
     <span data-ttu-id="e36d3-197">選項如下：</span><span class="sxs-lookup"><span data-stu-id="e36d3-197">The options are as follows:</span></span>  
  
    -   <span data-ttu-id="e36d3-198">若要建立新的排程，請按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="e36d3-198">To create a new schedule, click **New**.</span></span>  
  
         <span data-ttu-id="e36d3-199">這樣就會開啟 [新增全文檢索索引資料表排程] 對話方塊，可讓您建立排程。</span><span class="sxs-lookup"><span data-stu-id="e36d3-199">This opens the **New Full-Text Indexing Table Schedule** dialog box, where you can create a schedule.</span></span> <span data-ttu-id="e36d3-200">若要儲存排程，請按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="e36d3-200">To save the schedule, click **OK**.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="e36d3-201">在您結束 [全文檢索索引屬性] 對話方塊之後，SQL Server Agent 作業 (針對 <資料庫名稱>.<資料表名稱> 啟動累加資料表母體擴展) 就會與新的排程相關聯。</span><span class="sxs-lookup"><span data-stu-id="e36d3-201">A SQL Server Agent job (Start Incremental Table Population on *database_name*.*table_name*) is associated with a new schedule after you exit the **Full-Text Index Properties** dialog box.</span></span> <span data-ttu-id="e36d3-202">如果您針對全文檢索索引建立多個排程，它們都會使用相同的作業。</span><span class="sxs-lookup"><span data-stu-id="e36d3-202">If you create multiple schedules for the full-text index, they all use the same job.</span></span>  
  
    -   <span data-ttu-id="e36d3-203">若要變更排程，請選取它並按一下 [編輯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e36d3-203">To change a schedule, select it and click **Edit**.</span></span>  
  
         <span data-ttu-id="e36d3-204">這樣就會開啟 [新增全文檢索索引資料表排程] 對話方塊，可讓您修改排程。</span><span class="sxs-lookup"><span data-stu-id="e36d3-204">This opens the **New Full-Text Indexing Table Schedule** dialog box, where you can modify the schedule.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="e36d3-205">如需修改作業的詳細資訊，請參閱 [修改作業](../../ssms/agent/modify-a-job.md)。</span><span class="sxs-lookup"><span data-stu-id="e36d3-205">For information about modifying a job, see [Modify a Job](../../ssms/agent/modify-a-job.md).</span></span>  
  
    -   <span data-ttu-id="e36d3-206">若要移除排程，請選取它並按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e36d3-206">To remove a schedule, select it and click **Delete**.</span></span>  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  

  
##  <a name="troubleshooting-errors-in-a-full-text-population-crawl"></a><a name="crawl"></a><span data-ttu-id="e36d3-207">針對全文檢索擴展中的錯誤進行疑難排解 (爬網) </span><span class="sxs-lookup"><span data-stu-id="e36d3-207">Troubleshooting Errors in a Full-Text Population (Crawl)</span></span>  
 <span data-ttu-id="e36d3-208">搜耙發生錯誤時，「全文檢索搜尋」搜耙記錄功能會建立並維護搜耙記錄檔，此記錄檔是一個純文字檔。</span><span class="sxs-lookup"><span data-stu-id="e36d3-208">When an error occurs during a crawl, the Full-Text Search crawl logging facility creates and maintains a crawl log, which is a plain text file.</span></span> <span data-ttu-id="e36d3-209">每個搜耙記錄檔都對應至特定的全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="e36d3-209">Each crawl log corresponds to a particular full-text catalog.</span></span> <span data-ttu-id="e36d3-210">根據預設，指定之執行個體的搜耙記錄檔 (在此範例中為第一個執行個體) 位於 %ProgramFiles%\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\LOG 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="e36d3-210">By default crawl logs for a given instance, in this case, the first instance, are located in %ProgramFiles%\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\LOG folder.</span></span> <span data-ttu-id="e36d3-211">搜耙記錄檔會遵循下列命名結構：</span><span class="sxs-lookup"><span data-stu-id="e36d3-211">The crawl log file follows the following naming scheme:</span></span>  
  
 <span data-ttu-id="e36d3-212">SQLFT0000500008.2 \<DatabaseID> \<FullTextCatalogID> 。LOG [ \<n> ]</span><span class="sxs-lookup"><span data-stu-id="e36d3-212">SQLFT\<DatabaseID>\<FullTextCatalogID>.LOG[\<n>]</span></span>  
  
 <`DatabaseID`>  
 <span data-ttu-id="e36d3-213">資料庫的識別碼。</span><span class="sxs-lookup"><span data-stu-id="e36d3-213">The ID of a database.</span></span><span data-ttu-id="e36d3-214"> <`dbid`> 是前面加上零的五位數數位。</span><span class="sxs-lookup"><span data-stu-id="e36d3-214"> <`dbid`> is a five digit number with leading zeros.</span></span>  
  
 <`FullTextCatalogID`>  
 <span data-ttu-id="e36d3-215">全文檢索目錄識別碼。</span><span class="sxs-lookup"><span data-stu-id="e36d3-215">Full-text catalog ID.</span></span><span data-ttu-id="e36d3-216"> <`catid`> 是前面加上零的五位數數位。</span><span class="sxs-lookup"><span data-stu-id="e36d3-216"> <`catid`> is a five digit number with leading zeros.</span></span>  
  
 <`n`>  
 <span data-ttu-id="e36d3-217">是一個整數，指示相同全文檢索目錄的搜耙記錄檔數目。</span><span class="sxs-lookup"><span data-stu-id="e36d3-217">Is an integer that indicates one or more crawl logs of the same full-text catalog exist.</span></span>  
  
 <span data-ttu-id="e36d3-218">例如，SQLFT0000500008.2 是指資料庫識別碼 = 5 而且全文檢索目錄識別碼 = 8 之資料庫的搜耙記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e36d3-218">For example, SQLFT0000500008.2 is the crawl log file for a database with database ID = 5, and full-text catalog ID = 8.</span></span> <span data-ttu-id="e36d3-219">位於檔案名稱結尾的 2 表示此資料庫/目錄組有兩個搜耙記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e36d3-219">The 2 at the end of the file name indicates that there are two crawl log files for this database/catalog pair.</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="e36d3-220">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e36d3-220">See Also</span></span>  
 <span data-ttu-id="e36d3-221">[sys.dm_fts_index_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e36d3-221">[sys.dm_fts_index_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql) </span></span>  
 <span data-ttu-id="e36d3-222">[全文檢索搜尋使用者入門](get-started-with-full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="e36d3-222">[Get Started with Full-Text Search](get-started-with-full-text-search.md) </span></span>  
 <span data-ttu-id="e36d3-223">[建立及管理全文檢索索引](create-and-manage-full-text-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="e36d3-223">[Create and Manage Full-Text Indexes](create-and-manage-full-text-indexes.md) </span></span>  
 <span data-ttu-id="e36d3-224">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e36d3-224">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span></span>  
 [<span data-ttu-id="e36d3-225">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e36d3-225">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
  
