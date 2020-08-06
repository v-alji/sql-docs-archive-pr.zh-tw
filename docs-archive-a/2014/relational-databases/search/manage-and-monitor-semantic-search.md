---
title: 管理及監視語意搜尋 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], managing
- semantic search [SQL Server], monitoring
ms.assetid: eb5c3b29-da70-42aa-aa97-7d35a3f1eb98
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 16e3af1d37f177dfe6d4e0cb090e7b8b0a4988d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702594"
---
# <a name="manage-and-monitor-semantic-search"></a><span data-ttu-id="950f1-102">管理及監視語意搜尋</span><span class="sxs-lookup"><span data-stu-id="950f1-102">Manage and Monitor Semantic Search</span></span>
  <span data-ttu-id="950f1-103">描述語意索引的程序，以及與管理及監視索引相關的工作。</span><span class="sxs-lookup"><span data-stu-id="950f1-103">Describes the process of semantic indexing and the tasks related to managing and monitoring the indexes.</span></span>  
  
##  <a name="how-to-check-the-status-of-semantic-indexing"></a><a name="HowToMonitorStatus"></a><span data-ttu-id="950f1-104">如何：檢查語義索引的狀態</span><span class="sxs-lookup"><span data-stu-id="950f1-104">How To: Check the Status of Semantic Indexing</span></span>  
 <span data-ttu-id="950f1-105">**語意索引的第一個階段是否已完成？**</span><span class="sxs-lookup"><span data-stu-id="950f1-105">**Is the first phase of semantic indexing complete?**</span></span>  
 <span data-ttu-id="950f1-106">查詢動態管理檢視 [sys.dm_fts_index_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)**status** 和 **status_description** 資料行。</span><span class="sxs-lookup"><span data-stu-id="950f1-106">Query the dynamic management view, [sys.dm_fts_index_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql), and check the **status** and **status_description** columns.</span></span>  
  
 <span data-ttu-id="950f1-107">索引的第一個階段包括擴展全文檢索關鍵字索引和語意主要片語索引，以及擷取文件相似度資料。</span><span class="sxs-lookup"><span data-stu-id="950f1-107">The first phase of indexing includes the population of the full-text keyword index and the semantic key phrase index, as well as the extraction of document similarity data.</span></span>  
  
```sql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_index_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
 <span data-ttu-id="950f1-108">**語意索引的第二個階段是否已完成？**</span><span class="sxs-lookup"><span data-stu-id="950f1-108">**Is the second phase of semantic indexing complete?**</span></span>  
 <span data-ttu-id="950f1-109">查詢動態管理檢視 [sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql)**status** 和 **status_description** 資料行。</span><span class="sxs-lookup"><span data-stu-id="950f1-109">Query the dynamic management view, [sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql), and check the **status** and **status_description** columns..</span></span>  
  
 <span data-ttu-id="950f1-110">索引的第二個階段包括擴展語意文件相似度索引。</span><span class="sxs-lookup"><span data-stu-id="950f1-110">The second phase of indexing includes the population of the semantic document similarity index.</span></span>  
  
```wql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_semantic_similarity_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
##  <a name="how-to-check-the-size-of-the-semantic-indexes"></a><a name="HowToCheckSize"></a><span data-ttu-id="950f1-111">如何：檢查語義索引的大小</span><span class="sxs-lookup"><span data-stu-id="950f1-111">How To: Check the Size of the Semantic Indexes</span></span>  
 <span data-ttu-id="950f1-112">**語意主要片語索引或語意文件相似度索引的邏輯大小為何？**</span><span class="sxs-lookup"><span data-stu-id="950f1-112">**What is the logical size of a semantic key phrase index or a semantic document similarity index?**</span></span>  
 <span data-ttu-id="950f1-113">查詢動態管理檢視 [sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="950f1-113">Query the dynamic management view, [sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql).</span></span>  
  
 <span data-ttu-id="950f1-114">邏輯大小會以索引頁面的數目表示。</span><span class="sxs-lookup"><span data-stu-id="950f1-114">The logical size is displayed in number of index pages.</span></span>  
  
```sql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_db_fts_index_physical_stats WHERE object_id = OBJECT_ID('table_name')  
GO  
```  
  
 <span data-ttu-id="950f1-115">**全文檢索目錄的全文檢索索引與語意索引的總大小為何？**</span><span class="sxs-lookup"><span data-stu-id="950f1-115">**What is the total size of the full-text and semantic indexes for a full-text catalog?**</span></span>  
 <span data-ttu-id="950f1-116">查詢 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) 中繼資料函數的 **IndexSize** 屬性。</span><span class="sxs-lookup"><span data-stu-id="950f1-116">Query the **IndexSize** property of the [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) metadata function.</span></span>  
  
```sql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'IndexSize')  
GO  
```  
  
 <span data-ttu-id="950f1-117">**全文檢索目錄的全文檢索索引和語意索引中建立了多少項目的索引？**</span><span class="sxs-lookup"><span data-stu-id="950f1-117">**How many items are indexed in the full-text and semantic indexes for a full-text catalog?**</span></span>  
 <span data-ttu-id="950f1-118">查詢 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) 中繼資料函數的 **ItemCount** 屬性。</span><span class="sxs-lookup"><span data-stu-id="950f1-118">Query the **ItemCount** property of the [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql) metadata function.</span></span>  
  
```sql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'ItemCount')  
GO  
```  
  
##  <a name="how-to-force-the-population-of-the-semantic-indexes"></a><a name="HowToForcePopulation"></a><span data-ttu-id="950f1-119">如何：強制填入語義索引</span><span class="sxs-lookup"><span data-stu-id="950f1-119">How To: Force the Population of the Semantic Indexes</span></span>  
 <span data-ttu-id="950f1-120">您可以強制全文檢索索引和語意索引的母體擴展，其方式是使用 START/STOP/PAUSE 或 RESUME POPULATION 子句搭配全文檢索索引所描述的相同語法和行為。</span><span class="sxs-lookup"><span data-stu-id="950f1-120">You can force the population of full-text and semantic indexes by using the START/STOP/PAUSE or RESUME POPULATION clause with the same syntax and behavior that is described for full-text indexes.</span></span> <span data-ttu-id="950f1-121">如需詳細資訊，請參閱 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) 和[擴展全文檢索索引](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="950f1-121">For more information, see [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) and [Populate Full-Text Indexes](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="950f1-122">因為語意索引會依據全文檢索索引，所以只有當關聯的全文檢索索引已擴展時，才會擴展語意索引。</span><span class="sxs-lookup"><span data-stu-id="950f1-122">Since semantic indexing is dependent on full-text indexing, semantic indexes are only populated when the associated full-text indexes are populated.</span></span>  
  
 <span data-ttu-id="950f1-123">**範例：開始全文檢索索引與語意索引的完整母體擴展**</span><span class="sxs-lookup"><span data-stu-id="950f1-123">**Example: Start a full population of full-text and semantic indexes**</span></span>  
  
 <span data-ttu-id="950f1-124">下列範例會改變 AdventureWorks2012 範例資料庫中 **Production.Document** 資料表上現有的全文檢索索引，以便開始完整擴展全文檢索索引與語意索引。</span><span class="sxs-lookup"><span data-stu-id="950f1-124">The following example starts full population of both full-text and semantic indexes by altering an existing full-text index on the **Production.Document** table in the AdventureWorks2012 sample database.</span></span>  
  
```vb  
USE AdventureWorks2012  
GO  
  
ALTER FULLTEXT INDEX ON Production.Document  
    START FULL POPULATION  
GO  
```  
  
##  <a name="how-to-disable-or-re-enable-semantic-indexing"></a><a name="HowToDisableIndexing"></a><span data-ttu-id="950f1-125">如何：停用或重新啟用語義索引編制</span><span class="sxs-lookup"><span data-stu-id="950f1-125">How To: Disable or Re-enable Semantic Indexing</span></span>  
 <span data-ttu-id="950f1-126">您可以啟用或停用全文檢索索引或語意索引，其方式是使用 ENABLE/DISABLE 子句搭配全文檢索索引所描述的相同語法與行為。</span><span class="sxs-lookup"><span data-stu-id="950f1-126">You can enable or disable full-text or semantic indexing by using the ENABLE/DISABLE clause with the same syntax and behavior that is described for full-text indexes.</span></span> <span data-ttu-id="950f1-127">如需詳細資訊，請參閱 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="950f1-127">For more information, see [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).</span></span>  
  
 <span data-ttu-id="950f1-128">當語意索引已停用且暫停時，語意資料的查詢會持續順利運作，並傳回之前的索引資料。</span><span class="sxs-lookup"><span data-stu-id="950f1-128">When semantic indexing is disabled and suspended, queries over semantic data continue to work successfully and to return previously indexed data.</span></span> <span data-ttu-id="950f1-129">此行為與全文檢索搜尋的行為不一致。</span><span class="sxs-lookup"><span data-stu-id="950f1-129">This behavior is not consistent with the behavior of Full-Text Search.</span></span>  
  
```sql  
-- To disable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name DISABLE  
GO  
  
-- To re-enable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name ENABLE  
GO  
```  
  
##  <a name="phases-of-semantic-indexing"></a><a name="SemanticIndexing"></a><span data-ttu-id="950f1-130">語義索引的階段</span><span class="sxs-lookup"><span data-stu-id="950f1-130">Phases of Semantic Indexing</span></span>  
 <span data-ttu-id="950f1-131">語意搜尋會針對其啟用所在的每一個資料行，建立兩種資料的索引：</span><span class="sxs-lookup"><span data-stu-id="950f1-131">Semantic Search indexes two kinds of data for each column on which it is enabled:</span></span>  
  
1.  <span data-ttu-id="950f1-132">**關鍵片語**</span><span class="sxs-lookup"><span data-stu-id="950f1-132">**Key phrases**</span></span>  
  
2.  <span data-ttu-id="950f1-133">**文件相似度**</span><span class="sxs-lookup"><span data-stu-id="950f1-133">**Document similarity**</span></span>  
  
 <span data-ttu-id="950f1-134">語意索引會連同全文檢索索引發生在兩個階段：</span><span class="sxs-lookup"><span data-stu-id="950f1-134">Semantic indexing occurs in two phases, in conjunction with full-text indexing:</span></span>  
  
1.  <span data-ttu-id="950f1-135">**階段 1**.</span><span class="sxs-lookup"><span data-stu-id="950f1-135">**Phase 1**.</span></span> <span data-ttu-id="950f1-136">全文檢索關鍵字索引和語意主要片語索引會以平行方式同時擴展。</span><span class="sxs-lookup"><span data-stu-id="950f1-136">The full-text keyword index and the semantic key phrase index are populated in parallel at the same time.</span></span> <span data-ttu-id="950f1-137">此時也會擷取建立文件相似度索引所需的資料。</span><span class="sxs-lookup"><span data-stu-id="950f1-137">The data required to index document similarity is also extracted at this time.</span></span>  
  
2.  <span data-ttu-id="950f1-138">**階段 2**：</span><span class="sxs-lookup"><span data-stu-id="950f1-138">**Phase 2**.</span></span> <span data-ttu-id="950f1-139">然後會擴展語意文件相似度索引。</span><span class="sxs-lookup"><span data-stu-id="950f1-139">The semantic document similarity index is then populated.</span></span> <span data-ttu-id="950f1-140">此索引取決於上一個階段中已擴展的兩個索引。</span><span class="sxs-lookup"><span data-stu-id="950f1-140">This index depends on both indexes that were populated in the preceding phase.</span></span>  
  
##  <a name="BestPracticeUnderstand"></a>   
##  <a name="problem-semantic-indexes-are-not-populated"></a><a name="ProblemNotPopulated"></a><span data-ttu-id="950f1-141">問題：未填入語義索引</span><span class="sxs-lookup"><span data-stu-id="950f1-141">Problem: Semantic Indexes Are Not Populated</span></span>  
 <span data-ttu-id="950f1-142">**是否已擴展關聯的全文檢索索引？**</span><span class="sxs-lookup"><span data-stu-id="950f1-142">**Are the associated full-text indexes populated?**</span></span>  
 <span data-ttu-id="950f1-143">因為語意索引會依據全文檢索索引，所以只有當關聯的全文檢索索引已擴展時，才會擴展語意索引。</span><span class="sxs-lookup"><span data-stu-id="950f1-143">Since semantic indexing is dependent on full-text indexing, semantic indexes are only populated when the associated full-text indexes are populated.</span></span>  
  
 <span data-ttu-id="950f1-144">**是否已正確安裝及設定全文檢索搜尋及語意搜尋？**</span><span class="sxs-lookup"><span data-stu-id="950f1-144">**Are full-text search and semantic search properly installed and configured?**</span></span>  
 <span data-ttu-id="950f1-145">如需詳細資訊，請參閱 [安裝及設定語意搜尋](install-and-configure-semantic-search.md)。</span><span class="sxs-lookup"><span data-stu-id="950f1-145">For more information, see [Install and Configure Semantic Search](install-and-configure-semantic-search.md).</span></span>  
  
 <span data-ttu-id="950f1-146">**FDHOST 服務是否無法使用，或是有另一個狀況導致全文檢索索引失敗？**</span><span class="sxs-lookup"><span data-stu-id="950f1-146">**Is the FDHOST service not available, or is there another condition that would cause full-text indexing to fail?**</span></span>  
 <span data-ttu-id="950f1-147">如需相關資訊，請參閱 [疑難排解全文檢索索引](troubleshoot-full-text-indexing.md)。</span><span class="sxs-lookup"><span data-stu-id="950f1-147">For more information, see [Troubleshoot Full-Text Indexing](troubleshoot-full-text-indexing.md).</span></span>  
  
  
