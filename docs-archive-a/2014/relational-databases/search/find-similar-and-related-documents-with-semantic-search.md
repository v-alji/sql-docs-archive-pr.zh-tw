---
title: 使用語意搜尋尋找相似及相關的文件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], document similarity queries
ms.assetid: 9f527883-031b-442f-8e95-24bc0151ecbf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b11493b5b04fa9308e3afbe56176251225248338
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606718"
---
# <a name="find-similar-and-related-documents-with-semantic-search"></a><span data-ttu-id="e03f1-102">使用語意搜尋尋找相似及相關的文件</span><span class="sxs-lookup"><span data-stu-id="e03f1-102">Find Similar and Related Documents with Semantic Search</span></span>
  <span data-ttu-id="e03f1-103">描述如何在設定進行統計語意索引的資料行中尋找相似或相關的文件或文字值，以及相似或相關程度的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e03f1-103">Describes how to find similar or related documents or text values, and information about how they are similar or related, in columns that are configured for statistical semantic indexing.</span></span>  
  
##  <a name="finding-similar-or-related-documents"></a><a name="BasicsQuerySimilar"></a><span data-ttu-id="e03f1-104">尋找相似或相關的檔</span><span class="sxs-lookup"><span data-stu-id="e03f1-104">Finding Similar or Related Documents</span></span>  
  
###  <a name="how-to-find-similar-or-related-documents-with-semanticsimilaritytable"></a><a name="HowToQuerySimilar"></a><span data-ttu-id="e03f1-105">如何：使用 SEMANTICSIMILARITYTABLE 尋找相似或相關的檔</span><span class="sxs-lookup"><span data-stu-id="e03f1-105">How To: Find Similar or Related Documents with SEMANTICSIMILARITYTABLE</span></span>  
 <span data-ttu-id="e03f1-106">若要識別特定資料行中的相似或相關文件，請查詢 [semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql) 函數。</span><span class="sxs-lookup"><span data-stu-id="e03f1-106">To identify similar or related documents in a specific column, query the function [semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql).</span></span>  
  
 <span data-ttu-id="e03f1-107">**SEMANTICSIMILARITYTABLE** 會傳回含有零個、一個或多個資料列的資料表，其中所指定資料行中的內容會與所指定文件的語意相似。</span><span class="sxs-lookup"><span data-stu-id="e03f1-107">**SEMANTICSIMILARITYTABLE** returns a table of zero, one, or more rows whose content in the specified column is semantically similar to the specified document.</span></span> <span data-ttu-id="e03f1-108">您可以在 SELECT 陳述式的 FROM 子句中參考這個資料列集函數，就像是一般資料表名稱一樣。</span><span class="sxs-lookup"><span data-stu-id="e03f1-108">This rowset function can be referenced in the FROM clause of a SELECT statement like a regular table name.</span></span>  
  
 <span data-ttu-id="e03f1-109">您不能跨資料行查詢類似文件。</span><span class="sxs-lookup"><span data-stu-id="e03f1-109">You cannot query across columns for similar documents.</span></span> <span data-ttu-id="e03f1-110">**SEMANTICSIMILARITYTABLE** 函數只從與來源資料行相同的資料行中擷取結果，而來源資料行是透過 **source_key** 引數進行識別。</span><span class="sxs-lookup"><span data-stu-id="e03f1-110">The **SEMANTICSIMILARITYTABLE** function only retrieves results from the same column as the source column, which is identified by the **source_key** argument.</span></span>  
  
 <span data-ttu-id="e03f1-111">如需 **SEMANTICSIMILARITYTABLE** 函數所需參數及其所傳回結果資料表的詳細資訊，請參閱 [semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e03f1-111">For detailed information about the parameters required by the **SEMANTICSIMILARITYTABLE** function, and about the table of results that it returns, see [semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e03f1-112">您設定為目標的資料行必須已啟用全文檢索和語意索引。</span><span class="sxs-lookup"><span data-stu-id="e03f1-112">The columns that you target must have full-text and semantic indexing enabled.</span></span>  
  
###  <a name="example-find-the-top-documents-that-are-similar-to-another-document"></a><a name="HowToIdentifySimilar"></a><span data-ttu-id="e03f1-113">範例：尋找與另一份檔相似的前幾個檔</span><span class="sxs-lookup"><span data-stu-id="e03f1-113">Example: Find the Top Documents That Are Similar to Another Document</span></span>  
 <span data-ttu-id="e03f1-114">下列範例會 *@CandidateID* 從 AdventureWorks2012 範例資料庫的 humanresources.jobcandidate 資料表中，抓取與指定的候選項目類似的前10名候選物件。</span><span class="sxs-lookup"><span data-stu-id="e03f1-114">The following example retrieves the top 10 candidates who are similar to the candidate specified by *@CandidateID* from the HumanResources.JobCandidate table in the AdventureWorks2012 sample database.</span></span>  
  
```scr  
SELECT TOP(10) KEY_TBL.matched_document_key AS Candidate_ID  
FROM SEMANTICSIMILARITYTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume,  
    @CandidateID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
GO  
```  
  
##  <a name="finding-information-about-how-documents-are-similar-or-related"></a><a name="BasicsQuerySimilarity"></a><span data-ttu-id="e03f1-115">尋找檔相似或相關的資訊</span><span class="sxs-lookup"><span data-stu-id="e03f1-115">Finding Information about How Documents Are Similar or Related</span></span>  
  
###  <a name="how-to-find-information-about-how-documents-are-similar-or-related-with-semanticsimilaritydetailstable"></a><a name="HowToQuerySimilarity"></a><span data-ttu-id="e03f1-116">如何：尋找檔類似或與 SEMANTICSIMILARITYDETAILSTABLE 相關的資訊</span><span class="sxs-lookup"><span data-stu-id="e03f1-116">How To: Find Information about How Documents Are Similar or Related with SEMANTICSIMILARITYDETAILSTABLE</span></span>  
 <span data-ttu-id="e03f1-117">若要取得讓文件相似或相關之主要片語的詳細資訊，您可以查詢 [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql) 函數。</span><span class="sxs-lookup"><span data-stu-id="e03f1-117">To get information about the key phrases that make documents similar or related, you can query the function [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql).</span></span>  
  
 <span data-ttu-id="e03f1-118">**SEMANTICSIMILARITYDETAILSTABLE** 會傳回含有零個、一個或多個資料列的資料表，表示其內容為語意相似之兩份文件 (來源文件和比對文件) 之間的共同主要片語。</span><span class="sxs-lookup"><span data-stu-id="e03f1-118">**SEMANTICSIMILARITYDETAILSTABLE** returns a table of zero, one, or more rows of key phrases common across two documents (a source document and a matched document) whose content is semantically similar.</span></span> <span data-ttu-id="e03f1-119">您可以在 SELECT 陳述式的 FROM 子句中參考這個資料列集函數，就像是一般資料表名稱一樣。</span><span class="sxs-lookup"><span data-stu-id="e03f1-119">This rowset function can be referenced in the FROM clause of a SELECT statement like a regular table name.</span></span>  
  
 <span data-ttu-id="e03f1-120">如需 **SEMANTICSIMILARITYDETAILSTABLE** 函數所需參數及其所傳回結果資料表的詳細資訊，請參閱 [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e03f1-120">For detailed information about the parameters required by the **SEMANTICSIMILARITYDETAILSTABLE** function, and about the table of results that it returns, see [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e03f1-121">您設定為目標的資料行必須已啟用全文檢索和語意索引。</span><span class="sxs-lookup"><span data-stu-id="e03f1-121">The columns that you target must have full-text and semantic indexing enabled.</span></span>  
  
###  <a name="example-find-the-top-key-phrases-that-are-similar-between-documents"></a><a name="HowToSimilarPhrases"></a><span data-ttu-id="e03f1-122">範例：尋找檔之間相似的前幾個主要片語</span><span class="sxs-lookup"><span data-stu-id="e03f1-122">Example: Find the Top Key Phrases That Are Similar between Documents</span></span>  
 <span data-ttu-id="e03f1-123">下列範例從 AdventureWorks2012 範例資料庫的 **HumanResources.JobCandidate** 資料表擷取所指定候選人之間相似度分數最高的 5 個主要片語。</span><span class="sxs-lookup"><span data-stu-id="e03f1-123">The following example retrieves the 5 key phrases that have the highest similarity score between the specified candidates in **HumanResources.JobCandidate** table of the AdventureWorks2012 sample database.</span></span>  
  
```sql  
SELECT TOP(5) KEY_TBL.keyphrase, KEY_TBL.score  
FROM SEMANTICSIMILARITYDETAILSTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume, @CandidateID,  
    Resume, @MatchedID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
GO  
```  
  
  
