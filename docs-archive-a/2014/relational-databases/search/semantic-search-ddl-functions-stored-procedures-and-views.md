---
title: 語意搜尋 DDL、函式、預存程序及檢視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], database objects
ms.assetid: 182f395f-3168-48a4-b723-ef4403544f9f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ce6c23f9a8ff1d0dac8986bf6b44c7725d4badc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704014"
---
# <a name="semantic-search-ddl-functions-stored-procedures-and-views"></a><span data-ttu-id="b1cde-102">語意搜尋 DDL、函數、預存程序及檢視</span><span class="sxs-lookup"><span data-stu-id="b1cde-102">Semantic Search DDL, Functions, Stored Procedures, and Views</span></span>
  <span data-ttu-id="b1cde-103">列出支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中統計語意搜尋的 Transact-SQL 陳述式和資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="b1cde-103">Lists the Transact-SQL statements and the database objects that support statistical semantic search in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b1cde-104">如需支援全文檢索搜尋之陳述式和資料庫物件的清單，請參閱 [全文檢索搜尋 DDL、函數、預存程序與檢視](../views/views.md)。</span><span class="sxs-lookup"><span data-stu-id="b1cde-104">For the list of statements and database objects that support full-text search, see [Full-Text Search DDL, Functions, Stored Procedures, and Views](../views/views.md).</span></span>  
  
##  <a name="transact-sql-data-definition-language-ddl-statements"></a><a name="ddl"></a> <span data-ttu-id="b1cde-105">Transact-SQL 資料定義語言 (DDL) 陳述式</span><span class="sxs-lookup"><span data-stu-id="b1cde-105">Transact-SQL Data Definition Language (DDL) Statements</span></span>  
  
|<span data-ttu-id="b1cde-106">Object</span><span class="sxs-lookup"><span data-stu-id="b1cde-106">Object</span></span>|<span data-ttu-id="b1cde-107">相關資訊</span><span class="sxs-lookup"><span data-stu-id="b1cde-107">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="b1cde-108">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1cde-108">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-index-transact-sql)|[<span data-ttu-id="b1cde-109">在資料表和資料行上啟用語意搜尋</span><span class="sxs-lookup"><span data-stu-id="b1cde-109">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)|  
|[<span data-ttu-id="b1cde-110">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1cde-110">CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-index-transact-sql)|[<span data-ttu-id="b1cde-111">在資料表和資料行上啟用語意搜尋</span><span class="sxs-lookup"><span data-stu-id="b1cde-111">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)|  
  
##  <a name="system-functions"></a><a name="func"></a> <span data-ttu-id="b1cde-112">系統函數</span><span class="sxs-lookup"><span data-stu-id="b1cde-112">System Functions</span></span>  
  
|<span data-ttu-id="b1cde-113">Object</span><span class="sxs-lookup"><span data-stu-id="b1cde-113">Object</span></span>|<span data-ttu-id="b1cde-114">相關資訊</span><span class="sxs-lookup"><span data-stu-id="b1cde-114">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="b1cde-115">semantickeyphrasetable &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1cde-115">semantickeyphrasetable &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql)|[<span data-ttu-id="b1cde-116">使用語意搜尋在文件中尋找主要片語</span><span class="sxs-lookup"><span data-stu-id="b1cde-116">Find Key Phrases in Documents with Semantic Search</span></span>](find-key-phrases-in-documents-with-semantic-search.md)|  
|[<span data-ttu-id="b1cde-117">semanticsimilaritydetailstable &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1cde-117">semanticsimilaritydetailstable &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql)|[<span data-ttu-id="b1cde-118">使用語意搜尋尋找相似及相關的文件</span><span class="sxs-lookup"><span data-stu-id="b1cde-118">Find Similar and Related Documents with Semantic Search</span></span>](find-similar-and-related-documents-with-semantic-search.md)|  
|[<span data-ttu-id="b1cde-119">semanticsimilaritytable &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1cde-119">semanticsimilaritytable &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql)|[<span data-ttu-id="b1cde-120">使用語意搜尋尋找相似及相關的文件</span><span class="sxs-lookup"><span data-stu-id="b1cde-120">Find Similar and Related Documents with Semantic Search</span></span>](find-similar-and-related-documents-with-semantic-search.md)|  
  
##  <a name="system-metadata-functions"></a><a name="meta"></a> <span data-ttu-id="b1cde-121">系統中繼資料函數</span><span class="sxs-lookup"><span data-stu-id="b1cde-121">System Metadata Functions</span></span>  
  
|<span data-ttu-id="b1cde-122">Object</span><span class="sxs-lookup"><span data-stu-id="b1cde-122">Object</span></span>|<span data-ttu-id="b1cde-123">相關資訊</span><span class="sxs-lookup"><span data-stu-id="b1cde-123">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="b1cde-124">COLUMNPROPERTY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1cde-124">COLUMNPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/columnproperty-transact-sql)|[<span data-ttu-id="b1cde-125">在資料表和資料行上啟用語意搜尋</span><span class="sxs-lookup"><span data-stu-id="b1cde-125">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)|  
|[<span data-ttu-id="b1cde-126">DATABASEPROPERTYEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1cde-126">DATABASEPROPERTYEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/databasepropertyex-transact-sql)|[<span data-ttu-id="b1cde-127">在資料表和資料行上啟用語意搜尋</span><span class="sxs-lookup"><span data-stu-id="b1cde-127">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)|  
|[<span data-ttu-id="b1cde-128">FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1cde-128">FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql)|[<span data-ttu-id="b1cde-129">管理及監視語意搜尋</span><span class="sxs-lookup"><span data-stu-id="b1cde-129">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
|[<span data-ttu-id="b1cde-130">INDEXPROPERTY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1cde-130">INDEXPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/indexproperty-transact-sql)|[<span data-ttu-id="b1cde-131">管理及監視語意搜尋</span><span class="sxs-lookup"><span data-stu-id="b1cde-131">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
|[<span data-ttu-id="b1cde-132">OBJECTPROPERTYEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1cde-132">OBJECTPROPERTYEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/objectproperty-transact-sql)|[<span data-ttu-id="b1cde-133">在資料表和資料行上啟用語意搜尋</span><span class="sxs-lookup"><span data-stu-id="b1cde-133">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)|  
|[<span data-ttu-id="b1cde-134">SERVERPROPERTY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1cde-134">SERVERPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)|[<span data-ttu-id="b1cde-135">安裝及設定語意搜尋</span><span class="sxs-lookup"><span data-stu-id="b1cde-135">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)|  
  
##  <a name="system-stored-procedures"></a><a name="sproc"></a> <span data-ttu-id="b1cde-136">系統預存程序</span><span class="sxs-lookup"><span data-stu-id="b1cde-136">System Stored Procedures</span></span>  
  
|<span data-ttu-id="b1cde-137">Object</span><span class="sxs-lookup"><span data-stu-id="b1cde-137">Object</span></span>|<span data-ttu-id="b1cde-138">相關資訊</span><span class="sxs-lookup"><span data-stu-id="b1cde-138">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="b1cde-139">sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1cde-139">sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql)|[<span data-ttu-id="b1cde-140">安裝及設定語意搜尋</span><span class="sxs-lookup"><span data-stu-id="b1cde-140">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)|  
|[<span data-ttu-id="b1cde-141">sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1cde-141">sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql)|[<span data-ttu-id="b1cde-142">安裝及設定語意搜尋</span><span class="sxs-lookup"><span data-stu-id="b1cde-142">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)|  
  
##  <a name="system-views---catalog-views"></a><a name="cv"></a> <span data-ttu-id="b1cde-143">系統檢視表 - 目錄檢視</span><span class="sxs-lookup"><span data-stu-id="b1cde-143">System Views - Catalog Views</span></span>  
  
|<span data-ttu-id="b1cde-144">Object</span><span class="sxs-lookup"><span data-stu-id="b1cde-144">Object</span></span>|<span data-ttu-id="b1cde-145">相關資訊</span><span class="sxs-lookup"><span data-stu-id="b1cde-145">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="b1cde-146">sys.fulltext_index_columns &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1cde-146">sys.fulltext_index_columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)|[<span data-ttu-id="b1cde-147">管理及監視語意搜尋</span><span class="sxs-lookup"><span data-stu-id="b1cde-147">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
|[<span data-ttu-id="b1cde-148">sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1cde-148">sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql)|[<span data-ttu-id="b1cde-149">安裝及設定語意搜尋</span><span class="sxs-lookup"><span data-stu-id="b1cde-149">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)|  
|[<span data-ttu-id="b1cde-150">sys.fulltext_semantic_languages &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1cde-150">sys.fulltext_semantic_languages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql)|[<span data-ttu-id="b1cde-151">安裝及設定語意搜尋</span><span class="sxs-lookup"><span data-stu-id="b1cde-151">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)|  
  
##  <a name="system-views---dynamic-management-views"></a><a name="dmv"></a> <span data-ttu-id="b1cde-152">系統檢視表 - 動態管理檢視</span><span class="sxs-lookup"><span data-stu-id="b1cde-152">System Views - Dynamic Management Views</span></span>  
  
|<span data-ttu-id="b1cde-153">Object</span><span class="sxs-lookup"><span data-stu-id="b1cde-153">Object</span></span>|<span data-ttu-id="b1cde-154">相關資訊</span><span class="sxs-lookup"><span data-stu-id="b1cde-154">More Information</span></span>|  
|------------|----------------------|  
|[<span data-ttu-id="b1cde-155">sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1cde-155">sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql)|[<span data-ttu-id="b1cde-156">管理及監視語意搜尋</span><span class="sxs-lookup"><span data-stu-id="b1cde-156">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
|[<span data-ttu-id="b1cde-157">sys.dm_fts_index_population &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1cde-157">sys.dm_fts_index_population &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)|[<span data-ttu-id="b1cde-158">管理及監視語意搜尋</span><span class="sxs-lookup"><span data-stu-id="b1cde-158">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
|[<span data-ttu-id="b1cde-159">sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b1cde-159">sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql)|[<span data-ttu-id="b1cde-160">管理及監視語意搜尋</span><span class="sxs-lookup"><span data-stu-id="b1cde-160">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)|  
  
## <a name="see-also"></a><span data-ttu-id="b1cde-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1cde-161">See Also</span></span>  
 [<span data-ttu-id="b1cde-162">管理及監視語意搜尋</span><span class="sxs-lookup"><span data-stu-id="b1cde-162">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)  
  
  
