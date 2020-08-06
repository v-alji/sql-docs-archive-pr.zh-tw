---
title: 使用語意搜尋在文件中尋找主要片語 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], key phrase queries
ms.assetid: 6ee3676e-ed5d-43ec-aeca-1eed78967111
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8388fb704bf13f44d025e6e32a1450d537f61832
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697864"
---
# <a name="find-key-phrases-in-documents-with-semantic-search"></a><span data-ttu-id="0ff33-102">使用語意搜尋找到文件中的主要片語</span><span class="sxs-lookup"><span data-stu-id="0ff33-102">Find Key Phrases in Documents with Semantic Search</span></span>
  <span data-ttu-id="0ff33-103">描述如何在設定為統計語意索引的文件或文字資料行中尋找主要片語。</span><span class="sxs-lookup"><span data-stu-id="0ff33-103">Describes how to find the key phrases in documents or text columns that are configured for statistical semantic indexing.</span></span>  
  
##  <a name="finding-key-phrases-in-documents"></a><a name="BasicsQueryKey"></a><span data-ttu-id="0ff33-104">在檔中尋找主要片語</span><span class="sxs-lookup"><span data-stu-id="0ff33-104">Finding Key Phrases in Documents</span></span>  
  
###  <a name="how-to-find-the-key-phrases-in-documents-with-semantickeyphrasetable"></a><a name="howtofind"></a><span data-ttu-id="0ff33-105">如何：使用 SEMANTICKEYPHRASETABLE 在檔中尋找主要片語</span><span class="sxs-lookup"><span data-stu-id="0ff33-105">How to: Find the Key Phrases in Documents with SEMANTICKEYPHRASETABLE</span></span>  
 <span data-ttu-id="0ff33-106">若要在特定文件中識別主要片語，或識別包含特定主要片語的文件，請查詢 [semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql) 函數。</span><span class="sxs-lookup"><span data-stu-id="0ff33-106">To identify the key phrases in specific documents, or to identify documents that contain specific key phrases, query the function [semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql).</span></span>  
  
 <span data-ttu-id="0ff33-107">SEMANTICKEYPHRASETABLE 會傳回包含零個、一個或多個資料列的資料表，表示與指定之資料表資料行相關聯的主要片語。</span><span class="sxs-lookup"><span data-stu-id="0ff33-107">SEMANTICKEYPHRASETABLE returns a table with zero, one, or more rows for those key phrases associated with columns in the specified table.</span></span> <span data-ttu-id="0ff33-108">您可以在 SELECT 陳述式的 FROM 子句中參考這個資料列集函數，就像是一般資料表名稱一樣。</span><span class="sxs-lookup"><span data-stu-id="0ff33-108">This rowset function can be referenced in the FROM clause of a SELECT statement as if it were a regular table name.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0ff33-109">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，只有單一字會針對語意搜尋編制索引，多字片語 (ngrams) 則不會編制索引。</span><span class="sxs-lookup"><span data-stu-id="0ff33-109">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], only single words are indexed for semantic search; multi-word phrases (ngrams) are not indexed.</span></span> <span data-ttu-id="0ff33-110">此外，相同字的不同形式會個別編制索引，例如 "computer" 和 "computers" 會個別編制索引。</span><span class="sxs-lookup"><span data-stu-id="0ff33-110">Also, various forms of the same word are indexed separately; for example, "computer" and "computers" are indexed separately.</span></span>  
  
 <span data-ttu-id="0ff33-111">如需 SEMANTICKEYPHRASETABLE 函數所需之參數及其傳回之結果資料表的詳細資訊，請參閱 [semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0ff33-111">For detailed information about the parameters required by the SEMANTICKEYPHRASETABLE function, and about the table of results that it returns, see [semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0ff33-112">您設定為目標的資料行必須已啟用全文檢索和語意索引。</span><span class="sxs-lookup"><span data-stu-id="0ff33-112">The columns that you target must have full-text and semantic indexing enabled.</span></span>  
  
###  <a name="example-1-find-the-top-key-phrases-in-a-specific-document"></a><a name="HowToTopPhrases"></a><span data-ttu-id="0ff33-113">範例1：在特定檔中尋找前幾個主要片語</span><span class="sxs-lookup"><span data-stu-id="0ff33-113">Example 1: Find the Top Key Phrases in a Specific Document</span></span>  
 <span data-ttu-id="0ff33-114">下列範例會從 AdventureWorks 範例資料庫之 Production.Document 資料表 Document 資料行 @DocumentId 變數所指定的文件中，擷取前 10 個主要片語。</span><span class="sxs-lookup"><span data-stu-id="0ff33-114">The following example retrieves the top 10 key phrases from the document specified by the @DocumentId variable in the Document column of the Production.Document table of the AdventureWorks sample database.</span></span> <span data-ttu-id="0ff33-115">@DocumentId 變數是指來自全文檢索索引之索引鍵資料行的值。</span><span class="sxs-lookup"><span data-stu-id="0ff33-115">The @DocumentId variable represents a value from the key column of the full-text index.</span></span>  
  
```sql  
SELECT TOP(10) KEYP_TBL.keyphrase  
FROM SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document,  
    @DocumentId  
    ) AS KEYP_TBL  
ORDER BY KEYP_TBL.score DESC;  
GO  
```  
  
 <span data-ttu-id="0ff33-116">**SEMANTICKEYPHRASETABLE** 函數會使用索引搜尋有效率地擷取這些結果，而不會使用資料表掃描。</span><span class="sxs-lookup"><span data-stu-id="0ff33-116">The **SEMANTICKEYPHRASETABLE** function retrieves these results efficiently by using an index seek instead of a table scan.</span></span>  
  
###  <a name="example-2-find-the-top-documents-that-contain-a-specific-key-phrase"></a><a name="HowToTopDocuments"></a><span data-ttu-id="0ff33-117">範例2：尋找包含特定關鍵字組的前幾份檔</span><span class="sxs-lookup"><span data-stu-id="0ff33-117">Example 2: Find the Top Documents that Contain a Specific Key Phrase</span></span>  
 <span data-ttu-id="0ff33-118">下列範例會從 AdventureWorks 範例資料庫 Production.Document 資料表的 Document 資料行中，擷取前 25 份包含主要片語的 "Bracket" 的文件。</span><span class="sxs-lookup"><span data-stu-id="0ff33-118">The following example retrieves the top 25 documents that contain the key phrase "Bracket" from the Document column of the Production.Document table of the AdventureWorks sample database.</span></span>  
  
```sql  
SELECT TOP (25) DOC_TBL.DocumentID, DOC_TBL.DocumentSummary  
FROM Production.Document AS DOC_TBL  
    INNER JOIN SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document  
    ) AS KEYP_TBL  
ON DOC_TBL.DocumentID = KEYP_TBL.document_key  
WHERE KEYP_TBL.keyphrase = 'Bracket'  
ORDER BY KEYP_TBL.Score DESC;  
GO  
```  
  
  
