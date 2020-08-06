---
title: 語意搜尋 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server]
- semantic search [SQL Server], overview
- statistical semantic search [SQL Server]
- statistical semantic search [SQL Server], overview
ms.assetid: cd8faa9d-07db-420d-93f4-a2ea7c974b97
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 91062864b77ba3c62a87d66b8ff93068f9c10c8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704013"
---
# <a name="semantic-search-sql-server"></a><span data-ttu-id="c4c3a-102">語意搜尋 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c4c3a-102">Semantic Search (SQL Server)</span></span>
  <span data-ttu-id="c4c3a-103">統計語意搜尋會擷取統計上相關的「主要片語」並建立其索引，藉以深入解析儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中的非結構化文件。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-103">Statistical Semantic Search provides deep insight into unstructured documents stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases by extracting and indexing statistically relevant *key phrases*.</span></span> <span data-ttu-id="c4c3a-104">然後，它也會使用這些主要片語來識別「相似或相關文件」\*\*，並建立其索引。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-104">Then it also uses these key phrases to identify and index *documents that are similar or related*.</span></span>  
  
 <span data-ttu-id="c4c3a-105">使用三個 Transact-SQL 資料列集函數，以結構化資料形式擷取結果，就可以查詢這些語意索引。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-105">You query these semantic indexes by using three Transact-SQL rowset functions to retrieve the results as structured data.</span></span>  
  
##  <a name="what-can-i-do-with-semantic-search"></a><a name="whatcanido"></a><span data-ttu-id="c4c3a-106">我可以使用語義搜尋來做什麼？</span><span class="sxs-lookup"><span data-stu-id="c4c3a-106">What Can I Do with Semantic Search?</span></span>  
 <span data-ttu-id="c4c3a-107">雖然語意搜尋是以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中現有的全文檢索搜尋功能為建立基礎，但是可以實現超過關鍵字搜尋的新案例。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-107">Semantic search builds upon the existing full-text search feature in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but enables new scenarios that extend beyond keyword searches.</span></span> <span data-ttu-id="c4c3a-108">全文檢索搜尋可讓您查詢文件中的「字詞」**，而語意搜尋則可讓您查詢文件的「意義」**。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-108">While full-text search lets you query the *words* in a document, semantic search lets you query the *meaning* of the document.</span></span> <span data-ttu-id="c4c3a-109">目前可能的方案包含自動標記擷取、相關內容探索，以及相似內容的階層式導覽。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-109">Solutions that are now possible include automatic tag extraction, related content discovery, and hierarchical navigation across similar content.</span></span> <span data-ttu-id="c4c3a-110">例如，您可以查詢主要片語的索引來建立組織或文件主體的分類。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-110">For example, you can query the index of key phrases to build the taxonomy for an organization, or for a corpus of documents.</span></span> <span data-ttu-id="c4c3a-111">或者，您可以查詢文件相似度索引來識別符合工作描述的履歷表。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-111">Or, you can query the document similarity index to identify resumes that match a job description.</span></span>  
  
 <span data-ttu-id="c4c3a-112">下列各範例示範語意搜尋的功能。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-112">The following examples demonstrate the capabilities of Semantic Search.</span></span>  
  
###  <a name="find-the-key-phrases-in-a-document"></a><a name="find1"></a><span data-ttu-id="c4c3a-113">在檔中尋找主要片語</span><span class="sxs-lookup"><span data-stu-id="c4c3a-113">Find the Key Phrases in a Document</span></span>  
 <span data-ttu-id="c4c3a-114">下列查詢會取得範例文件中已識別的主要片語。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-114">The following query gets the key phrases that were identified in the sample document.</span></span> <span data-ttu-id="c4c3a-115">它會依照排列每個主要片語之統計重要性次序的分數，以遞減順序呈現結果。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-115">It presents the results in descending order by the score that ranks the statistical significance of each key phrase.</span></span> <span data-ttu-id="c4c3a-116">此查詢會呼叫 [semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql) 函數。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-116">This query calls the [semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql) function.</span></span>  
  
```sql  
SET @Title = 'Sample Document.docx'  
  
SELECT @DocID = DocumentID  
    FROM Documents  
    WHERE DocumentTitle = @Title  
  
SELECT @Title AS Title, keyphrase, score  
    FROM SEMANTICKEYPHRASETABLE(Documents, *, @DocID)  
    ORDER BY score DESC  
  
```  
  
  
  
###  <a name="find-similar-or-related-documents"></a><a name="find2"></a><span data-ttu-id="c4c3a-117">尋找相似或相關的檔</span><span class="sxs-lookup"><span data-stu-id="c4c3a-117">Find Similar or Related Documents</span></span>  
 <span data-ttu-id="c4c3a-118">下列查詢會取得識別為與範例文件相似或相關的文件。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-118">The following query gets the documents that were identified as similar or related to the sample document.</span></span> <span data-ttu-id="c4c3a-119">它會依照排列這兩份文件之相似度次序的分數，以遞減順序呈現結果。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-119">It presents the results in descending order by the score that ranks the similarity of the 2 documents.</span></span> <span data-ttu-id="c4c3a-120">此查詢會呼叫 [semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql) 函數。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-120">This query calls the [semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql) function.</span></span>  
  
```vb  
SET @Title = 'Sample Document.docx'  
  
SELECT @DocID = DocumentID  
    FROM Documents  
    WHERE DocumentTitle = @Title  
  
SELECT @Title AS SourceTitle, DocumentTitle AS MatchedTitle,  
        DocumentID, score  
    FROM SEMANTICSIMILARITYTABLE(Documents, *, @DocID)  
    INNER JOIN Documents ON DocumentID = matched_document_key  
    ORDER BY score DESC  
  
```  
  
  
  
###  <a name="find-the-key-phrases-that-make-documents-similar-or-related"></a><a name="find3"></a><span data-ttu-id="c4c3a-121">尋找讓檔相似或相關的主要片語</span><span class="sxs-lookup"><span data-stu-id="c4c3a-121">Find the Key Phrases That Make Documents Similar or Related</span></span>  
 <span data-ttu-id="c4c3a-122">下列查詢會取得讓兩份範例文件相似或相關的主要片語。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-122">The following query gets the key phrases that make the 2 sample documents similar or related to one another.</span></span> <span data-ttu-id="c4c3a-123">它會依照排列每個主要片語之加權次序的分數，以遞減順序呈現結果。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-123">It presents the results in descending order by the score that ranks the weight of each key phrase.</span></span> <span data-ttu-id="c4c3a-124">此查詢會呼叫 [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql) 函數。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-124">This query calls the [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql) function.</span></span>  
  
```sql  
SET @SourceTitle = 'first.docx'  
SET @MatchedTitle = 'second.docx'  
  
SELECT @SourceDocID = DocumentID FROM Documents WHERE DocumentTitle = @SourceTitle  
SELECT @MatchedDocID = DocumentID FROM Documents WHERE DocumentTitle = @MatchedTitle  
  
SELECT @SourceTitle AS SourceTitle, @MatchedTitle AS MatchedTitle, keyphrase, score  
    FROM semanticsimilaritydetailstable(Documents, DocumentContent,  
        @SourceDocID, DocumentContent, @MatchedDocID)  
    ORDER BY score DESC  
  
```  
  
  
  
##  <a name="storing-documents-in-sql-server"></a><a name="store"></a><span data-ttu-id="c4c3a-125">將檔儲存在 SQL Server</span><span class="sxs-lookup"><span data-stu-id="c4c3a-125">Storing Documents in SQL Server</span></span>  
 <span data-ttu-id="c4c3a-126">在您使用語意搜尋索引文件前，必須先將文件儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-126">Before you can index documents with Semantic Search, you have to store the documents in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="c4c3a-127">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中的 FileTable 功能可讓非結構化檔案和文件成為關聯式資料庫的首要成員。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-127">The FileTable feature in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] makes unstructured files and documents first-class citizens of the relational database.</span></span> <span data-ttu-id="c4c3a-128">因此，資料庫開發人員可以在 Transact-SQL 集合式作業中，操作文件以及結構化資料。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-128">As a result, database developers can manipulate documents together with structured data in Transact-SQL set-based operations.</span></span>  
  
 <span data-ttu-id="c4c3a-129">如需有關 FileTable 功能的詳細資訊，請參閱 [FileTables &#40;SQL Server&#41;](../blob/filetables-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-129">For more information about the FileTable feature, see [FileTables &#40;SQL Server&#41;](../blob/filetables-sql-server.md).</span></span> <span data-ttu-id="c4c3a-130">如需有關 FILESTREAM 功能 (這是將文件儲存至資料庫的另一個選擇) 的詳細資訊，請參閱 [FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-130">For information about the FILESTREAM feature, which is another option for storing documents in the database, see [FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md).</span></span>  
  
  
  
##  <a name="related-tasks"></a><a name="reltasks"></a> <span data-ttu-id="c4c3a-131">相關工作</span><span class="sxs-lookup"><span data-stu-id="c4c3a-131">Related Tasks</span></span>  
 [<span data-ttu-id="c4c3a-132">安裝及設定語意搜尋</span><span class="sxs-lookup"><span data-stu-id="c4c3a-132">Install and Configure Semantic Search</span></span>](install-and-configure-semantic-search.md)  
 <span data-ttu-id="c4c3a-133">描述統計語意搜尋的必要元件以及如何安裝或檢查這些必要元件。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-133">Describes the prerequisites for statistical semantic search and how to install or check them.</span></span>  
  
 [<span data-ttu-id="c4c3a-134">在資料表和資料行上啟用語意搜尋</span><span class="sxs-lookup"><span data-stu-id="c4c3a-134">Enable Semantic Search on Tables and Columns</span></span>](enable-semantic-search-on-tables-and-columns.md)  
 <span data-ttu-id="c4c3a-135">描述如何針對包含文件或文字的選取資料行啟用或停用統計語意索引。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-135">Describes how to enable or disable statistical semantic indexing on selected columns that contain documents or text.</span></span>  
  
 [<span data-ttu-id="c4c3a-136">使用語意搜尋在文件中尋找主要片語</span><span class="sxs-lookup"><span data-stu-id="c4c3a-136">Find Key Phrases in Documents with Semantic Search</span></span>](find-key-phrases-in-documents-with-semantic-search.md)  
 <span data-ttu-id="c4c3a-137">描述如何在設定為統計語意索引的文件或文字資料行中尋找主要片語。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-137">Describes how to find the key phrases in documents or text columns that are configured for statistical semantic indexing.</span></span>  
  
 [<span data-ttu-id="c4c3a-138">使用語意搜尋尋找相似及相關的文件</span><span class="sxs-lookup"><span data-stu-id="c4c3a-138">Find Similar and Related Documents with Semantic Search</span></span>](find-similar-and-related-documents-with-semantic-search.md)  
 <span data-ttu-id="c4c3a-139">描述如何在設定進行統計語意索引的資料行中尋找相似或相關的文件或文字值，以及相似或相關程度的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-139">Describes how to find similar or related documents or text values, and information about how they are similar or related, in columns that are configured for statistical semantic indexing.</span></span>  
  
 [<span data-ttu-id="c4c3a-140">管理及監視語意搜尋</span><span class="sxs-lookup"><span data-stu-id="c4c3a-140">Manage and Monitor Semantic Search</span></span>](manage-and-monitor-semantic-search.md)  
 <span data-ttu-id="c4c3a-141">描述語意索引的程序以及與監視及管理索引相關的工作。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-141">Describes the process of semantic indexing and the tasks related to monitoring and managing the indexes.</span></span>  
  
##  <a name="related-content"></a><a name="relcontent"></a> <span data-ttu-id="c4c3a-142">相關內容</span><span class="sxs-lookup"><span data-stu-id="c4c3a-142">Related Content</span></span>  
 [<span data-ttu-id="c4c3a-143">語意搜尋 DDL、函數、預存程序及檢視</span><span class="sxs-lookup"><span data-stu-id="c4c3a-143">Semantic Search DDL, Functions, Stored Procedures, and Views</span></span>](../views/views.md)  
 <span data-ttu-id="c4c3a-144">列出加入或變更以支援統計語意搜尋的 Transact-SQL 陳述式和 SQL Server 資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="c4c3a-144">Lists the Transact-SQL statements and the SQL Server database objects added or changed to support statistical semantic search.</span></span>  
  
  
