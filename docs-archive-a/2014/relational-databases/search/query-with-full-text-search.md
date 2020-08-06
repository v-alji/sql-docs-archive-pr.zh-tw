---
title: 使用全文檢索搜尋進行查詢 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- queries [full-text search], about full-text queries
- queries [full-text search], predicates
- full-text queries [SQL Server], about full-text queries
- full-text search [SQL Server], querying SQL Server
- full-text queries [SQL Server]
- queries [full-text search], functions
ms.assetid: 7624ba76-594b-4be5-ac10-c3ac4a3529bd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d78707925303d5e19d93b170f257d76fb7d1747d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700972"
---
# <a name="query-with-full-text-search"></a><span data-ttu-id="540a9-102">Query with Full-Text Search</span><span class="sxs-lookup"><span data-stu-id="540a9-102">Query with Full-Text Search</span></span>
  <span data-ttu-id="540a9-103">為了定義全文檢索搜尋， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 全文檢索查詢會使用全文檢索述詞 (CONTAINS 和 FREETEXT) 與函數 (CONTAINSTABLE 和 FREETEXTTABLE)。</span><span class="sxs-lookup"><span data-stu-id="540a9-103">To define full-text searches, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] full-text queries use the full-text predicates (CONTAINS and FREETEXT) and functions (CONTAINSTABLE and FREETEXTTABLE.</span></span> <span data-ttu-id="540a9-104">這些項目支援豐富的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語法，而這種語法支援各種形式的查詢詞彙。</span><span class="sxs-lookup"><span data-stu-id="540a9-104">These support rich [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax that supports a variety of forms of query terms.</span></span> <span data-ttu-id="540a9-105">若要撰寫全文檢索查詢，您必須了解使用這些述詞與函數的時機和方式。</span><span class="sxs-lookup"><span data-stu-id="540a9-105">To write full-text queries, you must learn when and how to use these predicates and functions.</span></span>  
  
##  <a name="overview-of-the-full-text-predicates-contains-and-freetext"></a><a name="OV_ft_predicates"></a><span data-ttu-id="540a9-106">概述 (CONTAINS 和 FREETEXT 的全文檢索述詞) </span><span class="sxs-lookup"><span data-stu-id="540a9-106">Overview of the Full-Text Predicates (CONTAINS and FREETEXT)</span></span>  
 <span data-ttu-id="540a9-107">CONTAINS 和 FREETEXT 述詞會傳回 TRUE 或 FALSE 值。</span><span class="sxs-lookup"><span data-stu-id="540a9-107">The CONTAINS and FREETEXT predicates return a TRUE or FALSE value.</span></span> <span data-ttu-id="540a9-108">它們只能用來指定選取準則，以便判斷給定的資料列是否符合全文檢索查詢。</span><span class="sxs-lookup"><span data-stu-id="540a9-108">They can be used only to specify selection criteria for determining whether a given row matches the full-text query.</span></span> <span data-ttu-id="540a9-109">符合的資料列就會傳回結果集中。</span><span class="sxs-lookup"><span data-stu-id="540a9-109">Matching rows are returned in the result set.</span></span> <span data-ttu-id="540a9-110">CONTAINS 和 FREETEXT 都是在 SELECT 陳述式的 WHERE 或 HAVING 子句中指定的。</span><span class="sxs-lookup"><span data-stu-id="540a9-110">CONTAINS and FREETEXT are specified in the WHERE or HAVING clause of a SELECT statement.</span></span> <span data-ttu-id="540a9-111">它們可與任何其他 [!INCLUDE[tsql](../../includes/tsql-md.md)] 述詞結合，例如 LIKE 和 BETWEEN。</span><span class="sxs-lookup"><span data-stu-id="540a9-111">They can be combined with any of the other [!INCLUDE[tsql](../../includes/tsql-md.md)] predicates, such as LIKE and BETWEEN.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="540a9-112">如需這些述詞的語法和引數的詳細資訊，請參閱[CONTAINS &#40;transact-sql&#41;](/sql/t-sql/queries/contains-transact-sql)和[FREETEXT &#40;transact-sql&#41;](/sql/t-sql/queries/freetext-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="540a9-112">For information about the syntax and arguments of these predicates, see [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) and [FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql).</span></span>  
  
 <span data-ttu-id="540a9-113">使用 CONTAINS 或 FREETEXT 時，您可以指定要搜尋資料表中的單一資料行、資料行清單或所有資料行。</span><span class="sxs-lookup"><span data-stu-id="540a9-113">When using CONTAINS or FREETEXT, you can specify either a single column, a list of columns, or all columns in the table to be searched.</span></span> <span data-ttu-id="540a9-114">此外，您可以針對斷詞和詞幹分析、同義字查閱以及非搜尋字移除，指定給定全文檢索查詢將使用之資源的語言。</span><span class="sxs-lookup"><span data-stu-id="540a9-114">Optionally, you can specify the language whose resources will be used by given full-text query for word breaking and stemming, thesaurus lookups, and noise-word removal.</span></span>  
  
 <span data-ttu-id="540a9-115">CONTAINS 和 FREETEXT 適用於不同種類的比對，如下所示：</span><span class="sxs-lookup"><span data-stu-id="540a9-115">CONTAINS and FREETEXT are useful for different kind of matches, as follows:</span></span>  
  
-   <span data-ttu-id="540a9-116">使用 CONTAINS (或 CONTAINSTABLE) 以進行下列各種比對：單字和片語的精確或模糊 (較不精確) 比對、單字彼此在一定距離之間的接近度，或加權相符。</span><span class="sxs-lookup"><span data-stu-id="540a9-116">Use CONTAINS (or CONTAINSTABLE) for precise or fuzzy (less precise) matches to single words and phrases, the proximity of words within a certain distance of one another, or weighted matches.</span></span> <span data-ttu-id="540a9-117">使用 CONTAINS 時，您至少必須指定一個指定您要搜尋之文字的搜尋條件，以及判斷是否相符的條件。</span><span class="sxs-lookup"><span data-stu-id="540a9-117">When using CONTAINS, you must specify at least one search condition that specifies the text that you are searching for and the conditions that determine matches.</span></span>  
  
     <span data-ttu-id="540a9-118">您可以在搜尋條件之間使用邏輯作業。</span><span class="sxs-lookup"><span data-stu-id="540a9-118">You can use logical operation between search conditions.</span></span> <span data-ttu-id="540a9-119">如需詳細資訊，請參閱本主題稍後的[使用布林運算子-and、OR 和 NOT (IN CONTAINS 和 CONTAINSTABLE) ](#Using_Boolean_Operators)。</span><span class="sxs-lookup"><span data-stu-id="540a9-119">For more information, see [Using Boolean operators-AND, OR, AND NOT (in CONTAINS and CONTAINSTABLE)](#Using_Boolean_Operators), later in this topic.</span></span>  
  
-   <span data-ttu-id="540a9-120">使用 FREETEXT (或 FREETEXTTABLE) 來比對指定之單字、片語或句子 (「Freetext 字串」\*\*(Freetext String)) 的意義，但不比對確切的用字。</span><span class="sxs-lookup"><span data-stu-id="540a9-120">Use FREETEXT (or FREETEXTTABLE) for matching the meaning, but not the exact wording, of specified words, phrases or sentences (the *freetext string*).</span></span> <span data-ttu-id="540a9-121">如果在指定之資料行的全文檢索索引中找到任何詞彙或任何形式的詞彙，就會產生相符項目。</span><span class="sxs-lookup"><span data-stu-id="540a9-121">Matches are generated if any term or form of any term is found in the full-text index of a specified column.</span></span>  
  
 <span data-ttu-id="540a9-122">您可以在 CONTAINS 或 FREETEXT 述詞中使用四部分名稱，以便在連結的伺服器上查詢目標資料表的全文檢索索引資料行。</span><span class="sxs-lookup"><span data-stu-id="540a9-122">You can use a four-part name in the CONTAINS or FREETEXT predicate to query full-text indexed columns of the target tables on a linked server.</span></span> <span data-ttu-id="540a9-123">若要準備遠端伺服器來接收全文檢索查詢，請針對遠端伺服器上的目標資料表與資料行建立全文檢索索引，然後加入遠端伺服器成為連結的伺服器。</span><span class="sxs-lookup"><span data-stu-id="540a9-123">To prepare a remote server to receive full-text queries, create a full-text index on the target tables and columns on the remote server and then add the remote server as a linked server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="540a9-124">當資料庫相容性層級設定為100時， [OUTPUT 子句](/sql/t-sql/queries/output-clause-transact-sql)中不允許使用全文檢索述詞。</span><span class="sxs-lookup"><span data-stu-id="540a9-124">Full-text predicates are not allowed in the [OUTPUT Clause](/sql/t-sql/queries/output-clause-transact-sql) when the database compatibility level is set to 100.</span></span>  
  
 
  
### <a name="examples"></a><span data-ttu-id="540a9-125">範例</span><span class="sxs-lookup"><span data-stu-id="540a9-125">Examples</span></span>  
  
#### <a name="a-using-contains-with-simple_term"></a><span data-ttu-id="540a9-126">A.</span><span class="sxs-lookup"><span data-stu-id="540a9-126">A.</span></span> <span data-ttu-id="540a9-127">搭配使用 CONTAINS 與 <simple_term></span><span class="sxs-lookup"><span data-stu-id="540a9-127">Using CONTAINS with <simple_term></span></span>  
 <span data-ttu-id="540a9-128">下列範例會尋找所有價格是 `$80.99` ，且含有 `"Mountain"`這個單字的產品。</span><span class="sxs-lookup"><span data-stu-id="540a9-128">The following example finds all products with a price of `$80.99` that contain the word `"Mountain"`.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Name, ListPrice  
FROM Production.Product  
WHERE ListPrice = 80.99  
   AND CONTAINS(Name, 'Mountain')  
GO  
```  
  
#### <a name="b-using-freetext-to-search-for-words-containing-specified-character-values"></a><span data-ttu-id="540a9-129">B.</span><span class="sxs-lookup"><span data-stu-id="540a9-129">B.</span></span> <span data-ttu-id="540a9-130">使用 FREETEXT 搜尋含有所指定字元值的單字</span><span class="sxs-lookup"><span data-stu-id="540a9-130">Using FREETEXT to search for words containing specified character values</span></span>  
 <span data-ttu-id="540a9-131">下列範例會搜尋包含 vital、safety 和 components 相關單字的所有文件。</span><span class="sxs-lookup"><span data-stu-id="540a9-131">The following example searches for all documents containing the words related to vital, safety, components.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Title  
FROM Production.Document  
WHERE FREETEXT (Document, 'vital safety components')  
GO  
```  
  
 
  
##  <a name="overview-of-the-full-text-functions-containstable-and-freetexttable"></a><a name="OV_ft_functions_CONTAINSTABLE_FREETEXTTABLE"></a> <span data-ttu-id="540a9-132">(CONTAINSTABLE 和 FREETEXTTABLE 的全文檢索函數總覽) </span><span class="sxs-lookup"><span data-stu-id="540a9-132">Overview of the Full-Text Functions (CONTAINSTABLE and FREETEXTTABLE)</span></span>  
 <span data-ttu-id="540a9-133">CONTAINSTABLE 和 FREETEXTTABLE 函數的參考方式就如同 SELECT 陳述式之 FROM 子句中的一般資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="540a9-133">The CONTAINSTABLE and FREETEXTTABLE functions are referenced like a regular table name in the FROM clause of a SELECT statement.</span></span> <span data-ttu-id="540a9-134">它們會傳回符合全文檢索查詢之零、一或多個資料列的資料表。</span><span class="sxs-lookup"><span data-stu-id="540a9-134">They return a table of zero, one, or more rows that match the full-text query.</span></span> <span data-ttu-id="540a9-135">傳回的資料表僅包含基底資料表的資料列，而這些資料列符合函數之全文檢索搜尋條件中指定的選取準則。</span><span class="sxs-lookup"><span data-stu-id="540a9-135">The returned table contains only rows of the base table that match the selection criteria specified in the full-text search condition of the function.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="540a9-136">如需這些函數的語法和引數的詳細資訊，請參閱[CONTAINSTABLE &#40;transact-sql&#41;](/sql/relational-databases/system-functions/containstable-transact-sql)和[FREETEXTTABLE &#40;transact-sql&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="540a9-136">For information about the syntax and arguments of these functions, see [CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) and [FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql).</span></span>  
  
 <span data-ttu-id="540a9-137">使用其中一個函數的查詢會針對每個資料列傳回一個相關次序值 (RANK) 和全文檢索索引鍵 (KEY)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="540a9-137">Queries using one of these functions return a relevance ranking value (RANK) and full-text key (KEY) for each row, as follows:</span></span>  
  
-   <span data-ttu-id="540a9-138">KEY 資料行</span><span class="sxs-lookup"><span data-stu-id="540a9-138">KEY column</span></span>  
  
     <span data-ttu-id="540a9-139">KEY 資料行會傳回所傳回之資料列的唯一值。</span><span class="sxs-lookup"><span data-stu-id="540a9-139">The KEY column returns unique values of the returned rows.</span></span> <span data-ttu-id="540a9-140">KEY 資料行可用來指定選取準則。</span><span class="sxs-lookup"><span data-stu-id="540a9-140">The KEY column can be used to specify selection criteria.</span></span>  
  
-   <span data-ttu-id="540a9-141">RANK 資料行</span><span class="sxs-lookup"><span data-stu-id="540a9-141">RANK column</span></span>  
  
     <span data-ttu-id="540a9-142">RANK 資料行會傳回每個資料列的「等級值」\*\*(Rank Value)，表示資料列與選取準則的符合程度。</span><span class="sxs-lookup"><span data-stu-id="540a9-142">The RANK column returns a *rank value* for each row that indicates how well the row matched the selection criteria.</span></span> <span data-ttu-id="540a9-143">資料列中文字或文件的等級值越高，該資料列與給定全文檢索查詢的關聯性就越大。</span><span class="sxs-lookup"><span data-stu-id="540a9-143">The higher the rank value of the text or document in a row, the more relevant the row is for the given full-text query.</span></span> <span data-ttu-id="540a9-144">請注意，不同的資料列可能會以完全相同的方式排序等級。</span><span class="sxs-lookup"><span data-stu-id="540a9-144">Note that different rows can be ranked identically.</span></span> <span data-ttu-id="540a9-145">您可以透過指定選擇性 *top_n_by_rank* 參數，限制要傳回的相符項目數。</span><span class="sxs-lookup"><span data-stu-id="540a9-145">You can limit the number of matches to be returned by specifying the optional *top_n_by_rank* parameter.</span></span> <span data-ttu-id="540a9-146">如需詳細資訊，請參閱 [限制 RANK 的搜索結果](limit-search-results-with-rank.md)。</span><span class="sxs-lookup"><span data-stu-id="540a9-146">For more information, see [Limit Search Results with RANK](limit-search-results-with-rank.md).</span></span>  
  
 <span data-ttu-id="540a9-147">使用其中一個函數時，您必須指定要進行全文檢索搜尋的基底資料表。</span><span class="sxs-lookup"><span data-stu-id="540a9-147">When using either of these functions, you must specify the base table that is to be full-text searched.</span></span> <span data-ttu-id="540a9-148">與述詞一樣，您可以指定要搜尋資料表中的單一資料行、資料行清單或所有資料行，而且可以選擇性地指定給定全文檢索查詢將使用之資源的語言。</span><span class="sxs-lookup"><span data-stu-id="540a9-148">As with the predicates, you can specify a single column, a list of columns, or all columns in the table to be searched, and optionally, the language whose resources will be used by given full-text query.</span></span>  
  
 <span data-ttu-id="540a9-149">CONTAINSTABLE 適用的比對種類與 CONTAINS 相同，而 FREETEXTTABLE 適用的比對種類則與 FREETEXT 相同。</span><span class="sxs-lookup"><span data-stu-id="540a9-149">CONTAINSTABLE is useful for the same kinds of matches as CONTAINS, and FREETEXTTABLE is useful for the same kinds of matches as FREETEXT.</span></span> <span data-ttu-id="540a9-150">如需詳細資訊，請參閱本主題前面的 [全文檢索述詞 (CONTAINS 和 FREETEXT) 的概觀](#OV_ft_predicates)。</span><span class="sxs-lookup"><span data-stu-id="540a9-150">For more information, see [Overview of the Full-Text Predicates (CONTAINS and FREETEXT)](#OV_ft_predicates), earlier in this topic.</span></span> <span data-ttu-id="540a9-151">執行使用 CONTAINSTABLE 與 FREETEXTTABLE 函數的查詢時，您必須明確聯結傳回的資料列與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 基底資料表中的資料列。</span><span class="sxs-lookup"><span data-stu-id="540a9-151">When running queries that use the CONTAINSTABLE and FREETEXTTABLE functions you must explicitly join rows that are returned with the rows in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base table.</span></span>  
  
 <span data-ttu-id="540a9-152">一般而言，CONTAINSTABLE 或 FREETEXTTABLE 的結果必須與基底資料表聯結。</span><span class="sxs-lookup"><span data-stu-id="540a9-152">Typically, the result of CONTAINSTABLE or FREETEXTTABLE needs to be joined with the base table.</span></span> <span data-ttu-id="540a9-153">在這種情況下，您必須知道唯一索引鍵資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="540a9-153">In such cases, you need to know the unique key column name.</span></span> <span data-ttu-id="540a9-154">這個資料行 (出現在每個啟用全文檢索的資料表中) 用來強制資料表的唯一資料列 (*unique\*\*key column*)。</span><span class="sxs-lookup"><span data-stu-id="540a9-154">This column, which occurs in every full-text enabled table, is used to enforce unique rows for the table (the *unique\*\*key column*).</span></span> <span data-ttu-id="540a9-155">如需詳細資訊，請參閱 [管理全文檢索索引](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="540a9-155">For more information, see [Manage Full-Text Indexes](../indexes/indexes.md).</span></span>  
  
 
  
### <a name="examples"></a><span data-ttu-id="540a9-156">範例</span><span class="sxs-lookup"><span data-stu-id="540a9-156">Examples</span></span>  
  
#### <a name="a-using-containstable"></a><span data-ttu-id="540a9-157">A.</span><span class="sxs-lookup"><span data-stu-id="540a9-157">A.</span></span> <span data-ttu-id="540a9-158">使用 CONTAINSTABLE</span><span class="sxs-lookup"><span data-stu-id="540a9-158">Using CONTAINSTABLE</span></span>  
 <span data-ttu-id="540a9-159">下列範例會傳回 **Description** 資料行在 "light" 或 "lightweight" 字附近包含 "aluminum" 這個字之所有產品的描述識別碼和描述。</span><span class="sxs-lookup"><span data-stu-id="540a9-159">The following example returns the description ID and description of all products for which the **Description** column contain the word "aluminum" near either the word "light" or the word "lightweight."</span></span> <span data-ttu-id="540a9-160">只會傳回排名值大於或等於 2 的資料列。</span><span class="sxs-lookup"><span data-stu-id="540a9-160">Only rows with a rank value of 2 or higher are returned.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT FT_TBL.ProductDescriptionID,  
   FT_TBL.Description,   
   KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL INNER JOIN  
   CONTAINSTABLE (Production.ProductDescription,  
      Description,   
      '(light NEAR aluminum) OR  
      (lightweight NEAR aluminum)'  
   ) AS KEY_TBL  
   ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK > 2  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  
#### <a name="b-using-freetexttable"></a><span data-ttu-id="540a9-161">B.</span><span class="sxs-lookup"><span data-stu-id="540a9-161">B.</span></span> <span data-ttu-id="540a9-162">使用 FREETEXTTABLE</span><span class="sxs-lookup"><span data-stu-id="540a9-162">Using FREETEXTTABLE</span></span>  
 <span data-ttu-id="540a9-163">下列範例將擴充 FREETEXTTABLE 查詢，以便先傳回最高等級的資料列，並將每個資料列的等級加至選取清單。</span><span class="sxs-lookup"><span data-stu-id="540a9-163">The following example extends a FREETEXTTABLE query to return the highest ranked rows first and to add the ranking of each row to the select list.</span></span> <span data-ttu-id="540a9-164">若要指定查詢，您必須知道**ProductDescriptionID**是資料表的唯一索引鍵資料行 `ProductDescription` 。</span><span class="sxs-lookup"><span data-stu-id="540a9-164">To specify the query, you must know that **ProductDescriptionID** is the unique key column for the `ProductDescription` table.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT KEY_TBL.RANK, FT_TBL.Description  
FROM Production.ProductDescription AS FT_TBL   
     INNER JOIN  
     FREETEXTTABLE(Production.ProductDescription, Description,  
                    'perfect all-around bike') AS KEY_TBL  
     ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 <span data-ttu-id="540a9-165">下面是相同查詢的擴充，它只傳回等級值大於或等於 10 的資料列：</span><span class="sxs-lookup"><span data-stu-id="540a9-165">Here is an extension of the same query that only returns rows with a rank value of 10 or greater:</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT KEY_TBL.RANK, FT_TBL.Description  
FROM Production.ProductDescription AS FT_TBL   
     INNER JOIN  
     FREETEXTTABLE(Production.ProductDescription, Description,  
                    'perfect all-around bike') AS KEY_TBL  
     ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK >= 10  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 
  
##  <a name="using-boolean-operators---and-or-and-not---in-contains-and-containstable"></a><a name="Using_Boolean_Operators"></a><span data-ttu-id="540a9-166">使用布林運算子-AND、OR 和 NOT in CONTAINS 和 CONTAINSTABLE</span><span class="sxs-lookup"><span data-stu-id="540a9-166">Using Boolean operators - AND, OR, and NOT - in CONTAINS and CONTAINSTABLE</span></span>  
 <span data-ttu-id="540a9-167">CONTAINS 述詞與 CONTAINSTABLE 函數會使用相同的搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="540a9-167">The CONTAINS predicate and CONTAINSTABLE function use the same search conditions.</span></span> <span data-ttu-id="540a9-168">兩者都支援使用布林運算子（AND、OR 和 NOT）來結合數個搜尋詞彙，以執行邏輯作業。</span><span class="sxs-lookup"><span data-stu-id="540a9-168">Both support combining several search terms by using Boolean operators-AND, OR, AND NOT-to perform logical operations.</span></span> <span data-ttu-id="540a9-169">例如，您可以使用 AND 來尋找同時包含 "latte" 和 "New York-style bagel" 的資料列。</span><span class="sxs-lookup"><span data-stu-id="540a9-169">You could use AND, for example, to find rows that contain both "latte" and "New York-style bagel".</span></span> <span data-ttu-id="540a9-170">例如，您可以使用 AND NOT 來尋找包含 "bagel" 但不包含 "cream cheese" 的資料列。</span><span class="sxs-lookup"><span data-stu-id="540a9-170">You can use AND NOT, for example, to find the rows that contain "bagel" but do not contain "cream cheese".</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="540a9-171">相較之下，FREETEXT 和 FREETEXTTABLE 會將布林詞彙視為要搜尋的單字。</span><span class="sxs-lookup"><span data-stu-id="540a9-171">In contrast, FREETEXT and FREETEXTTABLE treat the Boolean terms as words to be searched.</span></span>  
  
 <span data-ttu-id="540a9-172">如需結合 CONTAINS 與使用邏輯運算子 AND、OR 和 NOT 之其他述詞的詳細資訊，請參閱[搜尋條件 &#40;Transact-SQL&#41;](/sql/t-sql/queries/search-condition-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="540a9-172">For information about combining CONTAINS with other predicates that use the logical operators AND, OR, and NOT, see [Search Condition &#40;Transact-SQL&#41;](/sql/t-sql/queries/search-condition-transact-sql).</span></span>  
  
### <a name="example"></a><span data-ttu-id="540a9-173">範例</span><span class="sxs-lookup"><span data-stu-id="540a9-173">Example</span></span>  
 <span data-ttu-id="540a9-174">下列範例會使用 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 資料庫的 ProductDescription 資料表。</span><span class="sxs-lookup"><span data-stu-id="540a9-174">The following example uses the ProductDescription table of the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="540a9-175">此查詢會使用 CONTAINS 述詞來搜尋描述識別碼不等於 5，而且描述同時包含 "Aluminum" 與 "spindle" 這兩個單字的描述。</span><span class="sxs-lookup"><span data-stu-id="540a9-175">The query uses the CONTAINS predicate to search for descriptions in which the description ID is not equal to 5 and the description contains both the word "Aluminum" and the word "spindle."</span></span> <span data-ttu-id="540a9-176">搜尋條件會使用 AND 布林運算子。</span><span class="sxs-lookup"><span data-stu-id="540a9-176">The search condition uses the AND Boolean operator.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Description  
FROM Production.ProductDescription  
WHERE ProductDescriptionID <> 5 AND  
   CONTAINS(Description, 'aluminum AND spindle')  
GO  
```  
  
 
  
##  <a name="additional-considerations-for-full-text-queries"></a><a name="Additional_Considerations"></a><span data-ttu-id="540a9-177">全文檢索查詢的其他考慮</span><span class="sxs-lookup"><span data-stu-id="540a9-177">Additional Considerations for Full-Text Queries</span></span>  
 <span data-ttu-id="540a9-178">撰寫全文檢索查詢時，請同時考量下列事項：</span><span class="sxs-lookup"><span data-stu-id="540a9-178">When writing full-text queries also consider the following:</span></span>  
  
-   <span data-ttu-id="540a9-179">LANGUAGE 選項</span><span class="sxs-lookup"><span data-stu-id="540a9-179">The LANGUAGE option</span></span>  
  
     <span data-ttu-id="540a9-180">許多查詢詞彙主要取決於斷詞工具行為。</span><span class="sxs-lookup"><span data-stu-id="540a9-180">Many query terms depend heavily on word-breaker behavior.</span></span> <span data-ttu-id="540a9-181">若要確保您使用正確的斷詞工具 (和字幹分析器) 和同義字檔案，我們建議您指定 LANGUAGE 選項。</span><span class="sxs-lookup"><span data-stu-id="540a9-181">To ensure that you are using the correct word breaker (and stemmer) and thesaurus file, we recommend that you specify the LANGUAGE option.</span></span> <span data-ttu-id="540a9-182">如需詳細資訊，請參閱 [選擇建立全文檢索索引時的語言](choose-a-language-when-creating-a-full-text-index.md)。</span><span class="sxs-lookup"><span data-stu-id="540a9-182">For more information, see [Choose a Language When Creating a Full-Text Index](choose-a-language-when-creating-a-full-text-index.md).</span></span>  
  
-   <span data-ttu-id="540a9-183">停用字詞</span><span class="sxs-lookup"><span data-stu-id="540a9-183">Stopwords</span></span>  
  
     <span data-ttu-id="540a9-184">定義全文檢索查詢時，全文檢索引擎會從搜尋準則中捨棄停用字詞 (也稱為非搜尋字)。</span><span class="sxs-lookup"><span data-stu-id="540a9-184">When defining a full-text query, the Full-Text Engine discards stopwords (also called noise words) from the search criteria.</span></span> <span data-ttu-id="540a9-185">停用字詞是指 "a"、"and"、"is" 或 "the" 等字，這些字雖然經常出現，但通常對搜尋特定文字並無幫助。</span><span class="sxs-lookup"><span data-stu-id="540a9-185">Stopwords are words such as "a," "and," "is," or "the," that can occur frequently but that typically do not help when searching for particular text.</span></span> <span data-ttu-id="540a9-186">停用字詞會列於停用字詞表中。</span><span class="sxs-lookup"><span data-stu-id="540a9-186">Stopwords are listed in a stoplist.</span></span> <span data-ttu-id="540a9-187">每個全文檢索索引都會與特定停用字詞表相關聯，以便判斷哪些停用字詞會在建立索引時，從查詢或索引中省略。</span><span class="sxs-lookup"><span data-stu-id="540a9-187">Each full-text index is associated with a specific stoplist, which determines what stopwords are omitted from the query or the index at indexing time.</span></span> <span data-ttu-id="540a9-188">如需詳細資訊，請參閱 [設定及管理全文檢索搜尋的停用字詞與停用字詞表](full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="540a9-188">For more information, see [Configure and Manage Stopwords and Stoplists for Full-Text Search](full-text-search.md).</span></span>  
  
-   <span data-ttu-id="540a9-189">同義字</span><span class="sxs-lookup"><span data-stu-id="540a9-189">The thesaurus</span></span>  
  
     <span data-ttu-id="540a9-190">FREETEXT 和 FREETEXTTABLE 查詢預設會使用同義字。</span><span class="sxs-lookup"><span data-stu-id="540a9-190">FREETEXT and FREETEXTTABLE queries use the thesaurus by default.</span></span> <span data-ttu-id="540a9-191">CONTAINS 和 CONTAINSTABLE 支援選擇性 THESAURUS 引數。</span><span class="sxs-lookup"><span data-stu-id="540a9-191">CONTAINS and CONTAINSTABLE support an optional THESAURUS argument.</span></span>  
  
-   <span data-ttu-id="540a9-192">區分大小寫</span><span class="sxs-lookup"><span data-stu-id="540a9-192">Case sensitivity</span></span>  
  
     <span data-ttu-id="540a9-193">全文檢索搜尋查詢是不分大小寫的。</span><span class="sxs-lookup"><span data-stu-id="540a9-193">Full-text search queries are case-insensitive.</span></span> <span data-ttu-id="540a9-194">但在日文中，有多種發音拼字法，它的拼音正規化概念就類似不區分大小寫 (例如，kana = insensitivity)。</span><span class="sxs-lookup"><span data-stu-id="540a9-194">However, in Japanese, there are multiple phonetic orthographies in which the concept of orthographic normalization is akin to case insensitivity (for example, kana = insensitivity).</span></span> <span data-ttu-id="540a9-195">這類拼字法正規化並未支援。</span><span class="sxs-lookup"><span data-stu-id="540a9-195">This type of orthographic normalization is not supported.</span></span>  
  

  
##  <a name="querying-varbinarymax-and-xml-columns"></a><a name="varbinary"></a><span data-ttu-id="540a9-196">查詢 Varbinary (max) 和 xml 資料行</span><span class="sxs-lookup"><span data-stu-id="540a9-196">Querying varbinary(max) and xml Columns</span></span>  
 <span data-ttu-id="540a9-197">如果已建立 `varbinary(max)`、`varbinary` 或 `xml` 資料行的全文檢索索引，您就可以使用全文檢索述詞 (CONTAINS 和 FREETEXT) 與函數 (CONTAINSTABLE 和 FREETEXTTABLE) 來查詢它，就像查詢任何其他全文檢索索引資料行一樣。</span><span class="sxs-lookup"><span data-stu-id="540a9-197">If a `varbinary(max)`, `varbinary`, or `xml` column is full-text indexed, it can be queried using the full-text predicates (CONTAINS and FREETEXT) and functions (CONTAINSTABLE and FREETEXTTABLE), like any other full-text indexed column.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="540a9-198">全文檢索搜尋也會處理 image 資料行。</span><span class="sxs-lookup"><span data-stu-id="540a9-198">Full-text search also works with image columns.</span></span> <span data-ttu-id="540a9-199">不過，`image` 資料類型將在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的未來版本中移除。</span><span class="sxs-lookup"><span data-stu-id="540a9-199">However, the `image` data type will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="540a9-200">請避免在新的開發作業中使用此資料類型，並且計畫修改目前使用此資料類型的應用程式。</span><span class="sxs-lookup"><span data-stu-id="540a9-200">Avoid using this data type in new development work, and plan to modify applications that currently use it.</span></span> <span data-ttu-id="540a9-201">請改用 `varbinary(max)` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="540a9-201">Use the `varbinary(max)` data type instead.</span></span>  
  
### <a name="varbinarymax-or-varbinary-data"></a><span data-ttu-id="540a9-202">varbinary(max) 或 varbinary 資料</span><span class="sxs-lookup"><span data-stu-id="540a9-202">varbinary(max) or varbinary data</span></span>  
 <span data-ttu-id="540a9-203">單一 `varbinary(max)` 或 `varbinary` 資料行可以儲存多種類型的文件。</span><span class="sxs-lookup"><span data-stu-id="540a9-203">A single `varbinary(max)` or `varbinary` column can store many types of documents.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="540a9-204">支援已在作業系統中安裝並提供篩選的任何文件類型。</span><span class="sxs-lookup"><span data-stu-id="540a9-204">supports any document type for which a filter is installed and available in the operative system.</span></span> <span data-ttu-id="540a9-205">每份文件的文件類型都是由文件的副檔名所識別。</span><span class="sxs-lookup"><span data-stu-id="540a9-205">The document type of each document is identified by the file extension of the document.</span></span> <span data-ttu-id="540a9-206">例如，全文檢索搜尋會針對 .doc 副檔名使用支援 Microsoft Word 文件的篩選。</span><span class="sxs-lookup"><span data-stu-id="540a9-206">For example, for a .doc file extension, full-text search uses the filter that supports Microsoft Word documents.</span></span> <span data-ttu-id="540a9-207">如需可用文件類型的清單，請查詢 [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="540a9-207">For a list of available document types, query the [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="540a9-208">請注意，全文檢索引擎可以運用安裝在作業系統中的現有篩選。</span><span class="sxs-lookup"><span data-stu-id="540a9-208">Note that the Full-Text Engine can leverage existing filters that are installed in the operating system.</span></span> <span data-ttu-id="540a9-209">您必須先將作業系統篩選、斷詞工具和字幹分析器載入伺服器執行個體中，然後才能使用它們，如下所示：</span><span class="sxs-lookup"><span data-stu-id="540a9-209">Before you can use operating-system filters, word breakers, and stemmers, you must load them in the server instance, as follows:</span></span>  
  
```  
EXEC sp_fulltext_service @action='load_os_resources', @value=1  
```  
  
 <span data-ttu-id="540a9-210">若要針對 `varbinary(max)` 資料行建立全文檢索索引，全文檢索引擎需要 `varbinary(max)` 資料行中文件副檔名的存取權。</span><span class="sxs-lookup"><span data-stu-id="540a9-210">To create a full-text index on a `varbinary(max)` column, the Full-Text Engine needs access to the file extensions of the documents in the `varbinary(max)` column.</span></span> <span data-ttu-id="540a9-211">這項資訊必須儲存在稱為類型資料行的資料表資料行中，而此資料行必須與全文檢索索引中的 `varbinary(max)` 資料行相關聯。</span><span class="sxs-lookup"><span data-stu-id="540a9-211">This information must be stored in a table column, called a type column, that must be associated with the `varbinary(max)` column in the full-text index.</span></span> <span data-ttu-id="540a9-212">建立文件的索引時，全文檢索引擎會使用類型資料行中的副檔名來識別要使用的篩選。</span><span class="sxs-lookup"><span data-stu-id="540a9-212">When indexing a document, the Full-Text Engine uses the file extension in the type column to identify which filter to use.</span></span>  
  
 
  
### <a name="xml-data"></a><span data-ttu-id="540a9-213">xml 資料</span><span class="sxs-lookup"><span data-stu-id="540a9-213">xml data</span></span>  
 <span data-ttu-id="540a9-214">`xml` 資料類型資料行只會儲存 XML 文件和片段，而且只有 XML 篩選會用於這些文件。</span><span class="sxs-lookup"><span data-stu-id="540a9-214">An `xml` data type column stores only XML documents and fragments, and only the XML filter is used for the documents.</span></span> <span data-ttu-id="540a9-215">因此，類型資料行是不必要的。</span><span class="sxs-lookup"><span data-stu-id="540a9-215">Therefore, a type column is unnecessary.</span></span> <span data-ttu-id="540a9-216">在 `xml` 資料行上，全文檢索索引會建立 XML 元素內容的索引，但忽略 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="540a9-216">On `xml` columns, the full-text index indexes the content of the XML elements, but ignores the XML markup.</span></span> <span data-ttu-id="540a9-217">屬性值是全文檢索索引的值 (除非它們是數值)。</span><span class="sxs-lookup"><span data-stu-id="540a9-217">Attribute values are full-text indexed unless they are numeric values.</span></span> <span data-ttu-id="540a9-218">元素標記會當做 Token 界限來使用。</span><span class="sxs-lookup"><span data-stu-id="540a9-218">Element tags are used as token boundaries.</span></span> <span data-ttu-id="540a9-219">系統支援包含多種語言且格式正確的 XML 或 HTML 文件和片段。</span><span class="sxs-lookup"><span data-stu-id="540a9-219">Well-formed XML or HTML documents and fragments containing multiple languages are supported.</span></span>  
  
 <span data-ttu-id="540a9-220">如需有關在資料行上查詢的詳細資訊 `xml` ，請參閱[使用 XML 資料行進行全文檢索搜尋](../xml/use-full-text-search-with-xml-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="540a9-220">For more information about querying on an `xml` column, see [Use Full-Text Search with XML Columns](../xml/use-full-text-search-with-xml-columns.md).</span></span>  
  
 
  
##  <a name="supported-forms-of-query-terms"></a><a name="supported"></a><span data-ttu-id="540a9-221">支援的查詢詞彙形式</span><span class="sxs-lookup"><span data-stu-id="540a9-221">Supported Forms of Query Terms</span></span>  
 <span data-ttu-id="540a9-222">本節摘要說明全文檢索述詞和資料列集值函數針對每一種查詢形式所提供的支援。</span><span class="sxs-lookup"><span data-stu-id="540a9-222">This section summarizes the support provided for each form of query by the full-text predicates and rowset-valued functions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="540a9-223">如果是有提供查詢詞彙的語法，請按下表 **支援者** 列中的對應連結。</span><span class="sxs-lookup"><span data-stu-id="540a9-223">For the syntax a given query term, click the corresponding links in **Supported by** column of the following table.</span></span>  
  
|<span data-ttu-id="540a9-224">查詢詞彙形式</span><span class="sxs-lookup"><span data-stu-id="540a9-224">Query-term form</span></span>|<span data-ttu-id="540a9-225">描述</span><span class="sxs-lookup"><span data-stu-id="540a9-225">Description</span></span>|<span data-ttu-id="540a9-226">支援者</span><span class="sxs-lookup"><span data-stu-id="540a9-226">Supported by</span></span>|  
|----------------------|-----------------|------------------|  
|<span data-ttu-id="540a9-227">一或多個特定的單字或片語 ( *「不可分割的詞彙」* (Simple Term))</span><span class="sxs-lookup"><span data-stu-id="540a9-227">One or more specific words or phrases (*simple term*)</span></span>|<span data-ttu-id="540a9-228">在全文檢索搜尋中，字詞 (或 *token*) 是一種字串，其邊界是由適當的斷詞工具所識別，後面緊接著指定之語言的語言規則。</span><span class="sxs-lookup"><span data-stu-id="540a9-228">In full-text search, a word (or *token*) is a string whose boundaries are identified by appropriate word breakers, following the linguistic rules of the specified language.</span></span> <span data-ttu-id="540a9-229">有效的片語是由多個字詞所組成 (不論字詞之間是否有標點符號)。</span><span class="sxs-lookup"><span data-stu-id="540a9-229">A valid phrase consists of multiple words, with or without any punctuation marks between them.</span></span><br /><br /> <span data-ttu-id="540a9-230">例如，"可頌麵包" 是單字，而 "caf？？</span><span class="sxs-lookup"><span data-stu-id="540a9-230">For example, "croissant" is a word, and "caf??</span></span> <span data-ttu-id="540a9-231">au lait "是一種片語。</span><span class="sxs-lookup"><span data-stu-id="540a9-231">au lait" is a phrase.</span></span> <span data-ttu-id="540a9-232">這類字詞與片語稱為簡單詞彙。</span><span class="sxs-lookup"><span data-stu-id="540a9-232">Words and phrases such as these are called simple terms.</span></span><br /><br /> <span data-ttu-id="540a9-233">如需詳細資訊，請參閱本主題稍後的 [搜尋特定字詞或片語 (簡單詞彙)](#Simple_Term)。</span><span class="sxs-lookup"><span data-stu-id="540a9-233">For more information, see [Searching for Specific word or Phrase (Simple Term)](#Simple_Term), later in this topic.</span></span>|<span data-ttu-id="540a9-234">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) 和 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 會尋找完全相符的片語。</span><span class="sxs-lookup"><span data-stu-id="540a9-234">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) look for an exact match for the phrase.</span></span><br /><br /> <span data-ttu-id="540a9-235">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) 和 [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 會將片語分解成個別的字詞。</span><span class="sxs-lookup"><span data-stu-id="540a9-235">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) and [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) break up the phrase into separate words.</span></span>|  
|<span data-ttu-id="540a9-236">以指定之文字開頭的單字或片語 ( *「前置詞彙」* (Prefix Term))</span><span class="sxs-lookup"><span data-stu-id="540a9-236">A word or a phrase where the words begin with specified text (*prefix term*)</span></span>|<span data-ttu-id="540a9-237">前置詞彙是指附加至單字前面以便產生衍生字或字形變化的字串。</span><span class="sxs-lookup"><span data-stu-id="540a9-237">A prefix term refers to a string that is affixed to the front of a word to produce a derivative word or an inflected form.</span></span><br /><br /> <span data-ttu-id="540a9-238">對於單一前置詞彙而言，任何以指定之詞彙為開頭的單字都會成為結果集的一部分。</span><span class="sxs-lookup"><span data-stu-id="540a9-238">For a single prefix term, any word starting with the specified term will be part of the result set.</span></span> <span data-ttu-id="540a9-239">例如，詞彙 "auto\*" 與 "automatic"、"automobile" 等字相符。</span><span class="sxs-lookup"><span data-stu-id="540a9-239">For example, the term "auto\*" matches "automatic", "automobile", and so forth.</span></span><br /><br /> <span data-ttu-id="540a9-240">對於片語而言，片語中的每個單字都會被視為前置詞彙。</span><span class="sxs-lookup"><span data-stu-id="540a9-240">For a phrase, each word within the phrase is considered to be a prefix term.</span></span> <span data-ttu-id="540a9-241">例如，"auto tran\*" 詞彙符合 "automatic transmission" 及 "automobile transducer"，但不符合 "automatic motor transmission"。</span><span class="sxs-lookup"><span data-stu-id="540a9-241">For example, the term "auto tran\*" matches "automatic transmission" and "automobile transducer", but it does not match "automatic motor transmission".</span></span><br /><br /> <span data-ttu-id="540a9-242">如需詳細資訊，請參閱本主題稍後的 [執行前置詞搜尋 (前置詞彙)](#Prefix_Term)。</span><span class="sxs-lookup"><span data-stu-id="540a9-242">For more information, see [Performing Prefix Searches (Prefix Term)](#Prefix_Term), later in this topic.</span></span>|<span data-ttu-id="540a9-243">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) 和 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="540a9-243">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)</span></span>|  
|<span data-ttu-id="540a9-244">字形變化特定單字 (*產生詞彙的形式-字形變化*) </span><span class="sxs-lookup"><span data-stu-id="540a9-244">Inflectional forms of a specific word (*generation term-inflectional*)</span></span>|<span data-ttu-id="540a9-245">變化形式是指動詞的不同時態和變化或是名詞的單複數。</span><span class="sxs-lookup"><span data-stu-id="540a9-245">The inflectional forms are the different tenses and conjugations of a verb or the singular and plural forms of a noun.</span></span> <span data-ttu-id="540a9-246">例如，搜尋 "drive" 單字的變化形式。</span><span class="sxs-lookup"><span data-stu-id="540a9-246">For example, search for the inflectional form of the word "drive".</span></span> <span data-ttu-id="540a9-247">如果資料表的不同資料列中包括 "drive"、"drives"、"drove"、"driving" 及 "driven" 等字，因為所有這些單字都是從 "drive" 這個字所變化產生，所以它們都會出現在結果集中。</span><span class="sxs-lookup"><span data-stu-id="540a9-247">If various rows in the table include the words "drive", "drives", "drove", "driving", and "driven", all would be in the result set because each of these can be inflectionally generated from the word drive.</span></span><br /><br /> <span data-ttu-id="540a9-248">如需詳細資訊，請參閱本主題稍後的 [搜尋特定單字的變化形式 (衍生詞彙)](#Inflectional_Generation_Term)。</span><span class="sxs-lookup"><span data-stu-id="540a9-248">For more information, see [Searching for the Inflectional Form of a Specific Word (Generation Term)](#Inflectional_Generation_Term), later in this topic.</span></span>|<span data-ttu-id="540a9-249">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql)和[FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql)預設會尋找所有指定單字的字形變化詞彙。</span><span class="sxs-lookup"><span data-stu-id="540a9-249">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) and [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) look for inflectional terms of all specified words by default.</span></span><br /><br /> <span data-ttu-id="540a9-250">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) 和 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 支援選擇性 INFLECTIONAL 引數。</span><span class="sxs-lookup"><span data-stu-id="540a9-250">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) support an optional INFLECTIONAL argument.</span></span>|  
|<span data-ttu-id="540a9-251">特定單字 (*產生詞彙*的同義形式-同義字) </span><span class="sxs-lookup"><span data-stu-id="540a9-251">Synonymous forms of a specific word (*generation term-thesaurus*)</span></span>|<span data-ttu-id="540a9-252">同義字 (Thesaurus) 會針對詞彙定義使用者指定的同義字 (Synonym)。</span><span class="sxs-lookup"><span data-stu-id="540a9-252">A thesaurus defines user-specified synonyms for terms.</span></span> <span data-ttu-id="540a9-253">例如，如果將 "{car, automobile, truck, van}" 這個項目加入同義字中，則您可搜尋 "car" 這個字的同義字變化。</span><span class="sxs-lookup"><span data-stu-id="540a9-253">For example, if an entry, "{car, automobile, truck, van}", is added to a thesaurus, you can search for the thesaurus form of the word "car".</span></span> <span data-ttu-id="540a9-254">由於 "automobile"、"truck"、"van" 或 "car" 這些字都是屬於內含 "car" 這個字的同義字展開集，因此所查詢之資料表中含有這些字的所有資料列都會出現在結果集中。</span><span class="sxs-lookup"><span data-stu-id="540a9-254">All rows in the table queried that include the words "automobile", "truck", "van", or "car", appear in the result set because each of these words belong to the synonym expansion set containing the word "car".</span></span><br /><br /> <span data-ttu-id="540a9-255">如需同義字檔案的結構詳細資訊，請參閱 [設定及管理全文檢索搜尋的同義字檔案](configure-and-manage-thesaurus-files-for-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="540a9-255">For information about the structure of thesaurus files, see [Configure and Manage Thesaurus Files for Full-Text Search](configure-and-manage-thesaurus-files-for-full-text-search.md).</span></span>|<span data-ttu-id="540a9-256">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql)和[FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql)預設會使用同義字。</span><span class="sxs-lookup"><span data-stu-id="540a9-256">[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) and [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) use the thesaurus by default.</span></span><br /><br /> <span data-ttu-id="540a9-257">[CONTAINS](/sql/t-sql/queries/contains-transact-sql)和[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)支援選擇性的同義字引數。</span><span class="sxs-lookup"><span data-stu-id="540a9-257">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) support an optional THESAURUS argument.</span></span>|  
|<span data-ttu-id="540a9-258">靠近另一個單字或片語的單字或片語 ( *「相近詞彙」* (Proximity Term))</span><span class="sxs-lookup"><span data-stu-id="540a9-258">A word or phrase close to another word or phrase (*proximity term*)</span></span>|<span data-ttu-id="540a9-259">相近詞彙表示彼此互相靠近的字詞或片語。您也可以指定分隔第一個和最後一個搜尋詞彙的非搜尋詞彙數目上限。</span><span class="sxs-lookup"><span data-stu-id="540a9-259">A proximity term indicates words or phrases that are near to each other., You can also specify the maximum number of non-search terms that separate the first and last search terms.</span></span> <span data-ttu-id="540a9-260">此外，您可以依任何順序或是您所指定的順序來搜尋字詞或片語。</span><span class="sxs-lookup"><span data-stu-id="540a9-260">In addition, you can search for words or phrases in any order, or in the order in which you specify them.</span></span><br /><br /> <span data-ttu-id="540a9-261">例如，您要尋找 "ice" 單字接近 "hockey" 單字或 "ice skating" 片語接近 "ice hockey" 片語的資料列。</span><span class="sxs-lookup"><span data-stu-id="540a9-261">For example, you want to find the rows in which the word "ice" is near the word "hockey" or in which the phrase "ice skating" is near the phrase "ice hockey".</span></span><br /><br /> <span data-ttu-id="540a9-262">如需詳細資訊，請參閱 [使用 NEAR 搜尋靠近另一個單字的字詞](search-for-words-close-to-another-word-with-near.md).</span><span class="sxs-lookup"><span data-stu-id="540a9-262">For more information, see [Search for Words Close to Another Word with NEAR](search-for-words-close-to-another-word-with-near.md).</span></span>|<span data-ttu-id="540a9-263">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) 和 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="540a9-263">[CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)</span></span>|  
|<span data-ttu-id="540a9-264">使用加權值的單字或片語 ( *「加權詞彙」* (Weighted Term))</span><span class="sxs-lookup"><span data-stu-id="540a9-264">Words or phrases using weighted values (*weighted term*)</span></span>|<span data-ttu-id="540a9-265">加權值是表示每個字詞與片語在一組字詞與片語中的重要程度。</span><span class="sxs-lookup"><span data-stu-id="540a9-265">A weighting value that indicates the degree of importance for each word and phrase within a set of words and phrases.</span></span> <span data-ttu-id="540a9-266">最小的加權值是 0.0，最大則為 1.0。</span><span class="sxs-lookup"><span data-stu-id="540a9-266">A weight value of 0.0 is the lowest, and a weight value of 1.0 is the highest.</span></span><br /><br /> <span data-ttu-id="540a9-267">例如，在搜尋多個詞彙的查詢中，您可以指派每個搜尋單字的加權值，以指出它與搜尋條件中之其他單字的相對重要性。</span><span class="sxs-lookup"><span data-stu-id="540a9-267">For example, in a query searching for multiple terms, you can assign each search word a weight value indicating its importance relative to the other words in the search condition.</span></span> <span data-ttu-id="540a9-268">這類型之查詢的結果會根據您指派給搜尋單字的相對加權，先傳回最相關的資料列。</span><span class="sxs-lookup"><span data-stu-id="540a9-268">The results for this type of query return the most relevant rows first, according to the relative weight you have assigned to search words.</span></span> <span data-ttu-id="540a9-269">結果集包含具有任何指定之詞彙的文件或資料列 (或它們之間的內容)。不過，因為與不同搜尋詞彙相關聯的加權值具有變化，所以某些結果會被視為比其他結果更相關。</span><span class="sxs-lookup"><span data-stu-id="540a9-269">The result sets contain documents or rows containing any of the specified terms (or content between them); however, some results will be considered more relevant than others because of the variation in the weighted values associated with different searched terms.</span></span><br /><br /> <span data-ttu-id="540a9-270">如需詳細資訊，請參閱本主題稍後的 [使用加權值來搜尋字詞或片語 (加權詞彙)](#Weighted_Term)。</span><span class="sxs-lookup"><span data-stu-id="540a9-270">For more information, see [Searching for Words or Phrases Using Weighted Values (Weighted Term)](#Weighted_Term), later in this topic.</span></span>|[<span data-ttu-id="540a9-271">CONTAINSTABLE</span><span class="sxs-lookup"><span data-stu-id="540a9-271">CONTAINSTABLE</span></span>](/sql/relational-databases/system-functions/containstable-transact-sql)|  
  

  
###  <a name="searching-for-specific-word-or-phrase-simple-term"></a><a name="Simple_Term"></a><span data-ttu-id="540a9-272">搜尋特定單字或片語 (簡單詞彙) </span><span class="sxs-lookup"><span data-stu-id="540a9-272">Searching for Specific Word or Phrase (Simple Term)</span></span>  
 <span data-ttu-id="540a9-273">您可以使用 [CONTAINS](/sql/t-sql/queries/contains-transact-sql)、 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)、 [FREETEXT](/sql/t-sql/queries/freetext-transact-sql)或 [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 來搜尋資料表中的特定片語。</span><span class="sxs-lookup"><span data-stu-id="540a9-273">You can use [CONTAINS](/sql/t-sql/queries/contains-transact-sql), [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql), [FREETEXT](/sql/t-sql/queries/freetext-transact-sql), or [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) to search a table for a specific phrase.</span></span> <span data-ttu-id="540a9-274">例如，如果您要搜尋 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 資料庫中的 `ProductReview` 資料表，以尋找具有 "learning curve" 片語之產品的所有註解，可依照下列方式使用 CONTAINS 述詞：</span><span class="sxs-lookup"><span data-stu-id="540a9-274">For example, if you want to search the `ProductReview` table in the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database to find all comments about a product with the phrase "learning curve", you could use the CONTAINS predicate as follows:</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Comments  
FROM Production.ProductReview  
WHERE CONTAINS(Comments, '"learning curve"')  
GO  
```  
  
 <span data-ttu-id="540a9-275">搜尋條件 (在此範例中是 "learning curve") 有時候可能相當複雜，且由一個或多個詞彙組成。</span><span class="sxs-lookup"><span data-stu-id="540a9-275">The search condition, in this case "learning curve", can be quite complex and can be composed of one or more terms</span></span>  
  
 
  
###  <a name="performing-prefix-searches-prefix-term"></a><a name="Prefix_Term"></a> <span data-ttu-id="540a9-276">(前置詞) 執行前置字元搜尋</span><span class="sxs-lookup"><span data-stu-id="540a9-276">Performing Prefix Searches (Prefix Term)</span></span>  
 <span data-ttu-id="540a9-277">您可以使用 [CONTAINS](/sql/t-sql/queries/contains-transact-sql) 或 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 來搜尋具有指定之前置詞的字詞或片語。</span><span class="sxs-lookup"><span data-stu-id="540a9-277">You can use [CONTAINS](/sql/t-sql/queries/contains-transact-sql) or [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) to search for words or phrases with a specified prefix.</span></span> <span data-ttu-id="540a9-278">傳回資料行內包含以指定之前置詞開頭之文字的所有項目。</span><span class="sxs-lookup"><span data-stu-id="540a9-278">All entries in the column that contain text beginning with the specified prefix are returned.</span></span> <span data-ttu-id="540a9-279">例如，若要搜尋包含 `top`- 前置詞的所有資料列，如同在 `top``ple`、 `top``ping`和 `top`中。</span><span class="sxs-lookup"><span data-stu-id="540a9-279">For example, to search for all rows that contain the prefix `top`-, as in `top``ple`, `top``ping`, and `top`.</span></span> <span data-ttu-id="540a9-280">此查詢看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="540a9-280">The query looks like this:</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Description, ProductDescriptionID  
FROM Production.ProductDescription  
WHERE CONTAINS (Description, '"top*"' )  
GO  
```  
  
 <span data-ttu-id="540a9-281">傳回的項目是與星號 (\*) 前指定之文字相符的所有文字。</span><span class="sxs-lookup"><span data-stu-id="540a9-281">All text that matches the text specified before the asterisk (\*) is returned.</span></span> <span data-ttu-id="540a9-282">如果文字及星號未以雙引號 (") 分隔，例如 `CONTAINS (DESCRIPTION, 'top*')`，則全文檢索搜尋就不會將星號視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="540a9-282">If the text and asterisk are not delimited by double quotation marks, as in `CONTAINS (DESCRIPTION, 'top*')`, full-text search does not consider the asterisk to be a wildcard..</span></span>  
  
 <span data-ttu-id="540a9-283">若前置詞彙為片語，每個組成片語的 Token 都會被視為個別的前置項目。</span><span class="sxs-lookup"><span data-stu-id="540a9-283">When the prefix term is a phrase, each token making up the phrase is considered a separate prefix term.</span></span> <span data-ttu-id="540a9-284">傳回的資料列均包含以前置詞彙開頭的單字。</span><span class="sxs-lookup"><span data-stu-id="540a9-284">All rows that have words beginning with the prefix terms will be returned.</span></span> <span data-ttu-id="540a9-285">例如，"light bread\*" 這個前置詞彙找到的是包含 "light breaded"、"lightly breaded" 或 "light bread" 文字的資料列，而不會傳回如 "lightly toasted bread" 的資料列。</span><span class="sxs-lookup"><span data-stu-id="540a9-285">For example, the prefix term "light bread\*" will find rows with text of "light breaded," "lightly breaded," or "light bread," but it will not return "lightly toasted bread".</span></span>  
  
 
  
###  <a name="searching-for-inflectional-forms-of-a-specific-word-generation-term"></a><a name="Inflectional_Generation_Term"></a><span data-ttu-id="540a9-286">搜尋特定單字 (產生詞彙的字形變化形式) </span><span class="sxs-lookup"><span data-stu-id="540a9-286">Searching for Inflectional Forms of a Specific Word (Generation Term)</span></span>  
 <span data-ttu-id="540a9-287">您可以使用 [CONTAINS](/sql/t-sql/queries/contains-transact-sql)、 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)、 [FREETEXT](/sql/t-sql/queries/freetext-transact-sql)或 [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 搜尋動詞的所有不同時態和變化或名詞的單複數形式 (變化形式搜尋)，或是特定字詞的同義字形式 (同義字搜尋)。</span><span class="sxs-lookup"><span data-stu-id="540a9-287">You can use [CONTAINS](/sql/t-sql/queries/contains-transact-sql), [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql), [FREETEXT](/sql/t-sql/queries/freetext-transact-sql), or [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) to search for all the different tenses and conjugations of a verb or both the singular and plural forms of a noun (an inflectional search) or for synonymous forms of a specific word (a thesaurus search).</span></span>  
  
 <span data-ttu-id="540a9-288">下列範例會在 `Comments` 資料庫中 `ProductReview` 資料表的 `AdventureWorks` 資料行內，搜尋任何形式的 "foot" ("foot"、"feet" 等)。</span><span class="sxs-lookup"><span data-stu-id="540a9-288">The following example searches for any form of "foot" ("foot", "feet", and so on) in the `Comments` column of the `ProductReview` table in the `AdventureWorks` database.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Comments, ReviewerName  
FROM Production.ProductReview  
WHERE CONTAINS (Comments, 'FORMSOF(INFLECTIONAL, "foot")')  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="540a9-289">全文檢索搜尋會使用字幹分析器，此工具可讓您搜尋動詞的不同時態和變化或是名詞的單複數形式。</span><span class="sxs-lookup"><span data-stu-id="540a9-289">Full-text search uses stemmers, which allow you to search for the different tenses and conjugations of a verb, or both the singular and plural forms of a noun.</span></span> <span data-ttu-id="540a9-290">如需字幹分析器的詳細資訊，請參閱 [設定及管理搜尋的斷詞工具與字幹分析器](configure-and-manage-word-breakers-and-stemmers-for-search.md)。</span><span class="sxs-lookup"><span data-stu-id="540a9-290">For more information about stemmers, see [Configure and Manage Word Breakers and Stemmers for Search](configure-and-manage-word-breakers-and-stemmers-for-search.md).</span></span>  
  

  
###  <a name="searching-for-words-or-phrases-using-weighted-values-weighted-term"></a><a name="Weighted_Term"></a><span data-ttu-id="540a9-291">使用加權值搜尋單字或片語 (加權詞彙) </span><span class="sxs-lookup"><span data-stu-id="540a9-291">Searching for Words or Phrases Using Weighted Values (Weighted Term)</span></span>  
 <span data-ttu-id="540a9-292">您可以使用 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 來搜尋字詞或片語，並指定加權值。</span><span class="sxs-lookup"><span data-stu-id="540a9-292">You can use [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) to search for words or phrases and specify a weighting value.</span></span> <span data-ttu-id="540a9-293">加權值是介於 0.0 到 1.0 之間的數字，用來指示每個字詞與片語在一組字詞與片語中的重要程度。</span><span class="sxs-lookup"><span data-stu-id="540a9-293">Weight, measured as a number from 0.0 through 1.0, indicates the importance of each word and phrase within a set of words and phrases.</span></span> <span data-ttu-id="540a9-294">最小的加權值是 0.0，最大則為 1.0。</span><span class="sxs-lookup"><span data-stu-id="540a9-294">A weight of 0.0 is the lowest, and a weight of 1.0 is the highest.</span></span>  
  
 <span data-ttu-id="540a9-295">下列範例顯示一項查詢，此查詢會搜尋所有客戶的地址，並使用加權值，找出以 "Bay" 字串開頭且連接 "Street" 或 "View" 的所有文字。</span><span class="sxs-lookup"><span data-stu-id="540a9-295">The following example shows a query that searches for all customer addresses, using weights, in which any text beginning with the string "Bay" has either "Street" or "View".</span></span> <span data-ttu-id="540a9-296">資料列中包含越多指定的字詞，結果就會為該資料列指定越高的等級。</span><span class="sxs-lookup"><span data-stu-id="540a9-296">The results give a higher rank to those rows that contain more of the words specified.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT AddressLine1, KEY_TBL.RANK   
FROM Person.Address AS Address INNER JOIN  
CONTAINSTABLE(Person.Address, AddressLine1, 'ISABOUT ("Bay*",   
         Street WEIGHT(0.9),   
         View WEIGHT(0.1)  
         ) ' ) AS KEY_TBL  
ON Address.AddressID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 <span data-ttu-id="540a9-297">加權詞彙可以搭配任何不可分割的詞彙、前置詞彙、衍生詞彙或相近詞彙一起使用。</span><span class="sxs-lookup"><span data-stu-id="540a9-297">A weighted term can be used in conjunction with any simple term, prefix term, generation term, or proximity term.</span></span>  
  

  
##  <a name="viewing-the-tokenization-result-of-a-word-breaker-thesaurus-and-stoplist-combination"></a><a name="tokens"></a><span data-ttu-id="540a9-298">查看斷詞工具、同義字和停用字詞表組合的 token 化結果</span><span class="sxs-lookup"><span data-stu-id="540a9-298">Viewing the Tokenization Result of a Word Breaker, Thesaurus, and Stoplist Combination</span></span>  
 <span data-ttu-id="540a9-299">將指定的斷詞工具、同義字和停用字詞表組合套用至查詢字串輸入之後，您就可以使用 **sys.dm_fts_parser** 動態管理檢視來檢視 Token 化結果。</span><span class="sxs-lookup"><span data-stu-id="540a9-299">After applying a given word breaker, thesaurus, and stoplist combination to a query string input, you can view the tokenization result by using the **sys.dm_fts_parser** dynamic management view.</span></span> <span data-ttu-id="540a9-300">如需詳細資訊，請參閱 [sys.dm_fts_parser &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="540a9-300">For more information, see [sys.dm_fts_parser &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql).</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="540a9-301">另請參閱</span><span class="sxs-lookup"><span data-stu-id="540a9-301">See Also</span></span>  
 <span data-ttu-id="540a9-302">[CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="540a9-302">[CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) </span></span>  
 <span data-ttu-id="540a9-303">[CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="540a9-303">[CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span></span>  
 <span data-ttu-id="540a9-304">[FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="540a9-304">[FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql) </span></span>  
 <span data-ttu-id="540a9-305">[FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="540a9-305">[FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql) </span></span>  
 <span data-ttu-id="540a9-306">[建立全文檢索搜尋查詢 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="540a9-306">[Create Full-Text Search Queries &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md) </span></span>  
 [<span data-ttu-id="540a9-307">改善全文檢索查詢的效能</span><span class="sxs-lookup"><span data-stu-id="540a9-307">Improve the Performance of Full-Text Queries</span></span>](improve-the-performance-of-full-text-queries.md)  
  
  
