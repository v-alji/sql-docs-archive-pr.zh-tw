---
title: 使用 RANK 限制搜索結果 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- row ranking [full-text search]
- relevance ranking values [full-text search]
- full-text search [SQL Server], rankings
- index rankings [full-text search]
- ranked results [full-text search]
- rankings [full-text search]
- per-row rank values [full-text search]
ms.assetid: 06a776e6-296c-4ec7-9fa5-0794709ccb17
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ab1b930b3238cb541965e1984d1561f1a1c22d87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702609"
---
# <a name="limit-search-results-with-rank"></a><span data-ttu-id="be8a7-102">限制 RANK 的搜索結果</span><span class="sxs-lookup"><span data-stu-id="be8a7-102">Limit Search Results with RANK</span></span>
  <span data-ttu-id="be8a7-103">[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 和 [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 函數會傳回名為 RANK 的資料行，其中包含 0 到 1000 (順位值) 的序數值。</span><span class="sxs-lookup"><span data-stu-id="be8a7-103">The [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) and [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) functions return a column named RANK that contains ordinal values from 0 through 1000 (rank values).</span></span> <span data-ttu-id="be8a7-104">這些值的用途，在根據傳回資料列符合選取準則的程度予以分級。</span><span class="sxs-lookup"><span data-stu-id="be8a7-104">These values are used to rank the rows returned according to how well they match the selection criteria.</span></span> <span data-ttu-id="be8a7-105">等級值僅表示結果集中資料列相關性的相對順序，其值越低表示相關性越低。</span><span class="sxs-lookup"><span data-stu-id="be8a7-105">The rank values indicate only a relative order of relevance of the rows in the result set, with a lower value indicating lower relevance.</span></span> <span data-ttu-id="be8a7-106">實際的值並不重要，而且每次執行查詢後該值通常會不一樣。</span><span class="sxs-lookup"><span data-stu-id="be8a7-106">The actual values are unimportant and typically differ each time the query is run.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be8a7-107">CONTAINS 與 FREETEXT 述詞不會傳回任何等級值。</span><span class="sxs-lookup"><span data-stu-id="be8a7-107">The CONTAINS and FREETEXT predicates do not return any rank values.</span></span>  
  
 <span data-ttu-id="be8a7-108">符合搜尋條件的項目數通常會非常龐大。</span><span class="sxs-lookup"><span data-stu-id="be8a7-108">The number of items matching a search condition is often very large.</span></span> <span data-ttu-id="be8a7-109">若要防止 CONTAINSTABLE 或 FREETEXTTABLE 查詢傳回太多相符項目，請使用選擇性 *top_n_by_rank* 參數，以便僅傳回資料列的子集。</span><span class="sxs-lookup"><span data-stu-id="be8a7-109">To prevent CONTAINSTABLE or FREETEXTTABLE queries from returning too many matches, use the optional *top_n_by_rank* parameter, which returns only a subset of rows.</span></span> <span data-ttu-id="be8a7-110">*top_n_by_rank* 是整數值 *n*，其中指定依遞減順序僅傳回 *n* 個最高等級的相符項目。</span><span class="sxs-lookup"><span data-stu-id="be8a7-110">*top_n_by_rank* is an integer value, *n*, that specifies that only the *n* highest ranked matches are to be returned, in descending order.</span></span> <span data-ttu-id="be8a7-111">如果結合 *top_n_by_rank* 與其他參數，則查詢所傳回的資料列數目會少於實際符合所有述詞的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="be8a7-111">If *top_n_by_rank* is combined with other parameters, the query could return fewer rows than the number of rows that actually match all the predicates.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="be8a7-112">將依照等級來排序相符項目，並且最多只傳回指定的資料列數。</span><span class="sxs-lookup"><span data-stu-id="be8a7-112">orders the matches by rank and returns only up to the specified number of rows.</span></span> <span data-ttu-id="be8a7-113">此選項可能大幅地增加效能。</span><span class="sxs-lookup"><span data-stu-id="be8a7-113">This choice can result in a dramatic increase in performance.</span></span> <span data-ttu-id="be8a7-114">例如，通常從一百萬個資料列中傳回 100,000 列的查詢，如果只要求前 100 個資料列的話，就會處理得更為快速。</span><span class="sxs-lookup"><span data-stu-id="be8a7-114">For example, a query that would normally return 100,000 rows from a table of one million rows are processed more quickly if only the top 100 rows are requested.</span></span>  
  
##  <a name="examples-of-using-rank-to-limit-search-results"></a><a name="examples"></a> <span data-ttu-id="be8a7-115">使用 RANK 限制搜尋結果的範例</span><span class="sxs-lookup"><span data-stu-id="be8a7-115">Examples of Using RANK to Limit Search Results</span></span>  
  
### <a name="example-a-searching-for-only-the-top-three-matches"></a><span data-ttu-id="be8a7-116">範例 A：只搜尋前三個相符項目</span><span class="sxs-lookup"><span data-stu-id="be8a7-116">Example A: Searching for only the top three matches</span></span>  
 <span data-ttu-id="be8a7-117">下列範例會使用 CONTAINSTABLE，以便只傳回前三個相符項目。</span><span class="sxs-lookup"><span data-stu-id="be8a7-117">The following example uses CONTAINSTABLE to return only the top three matches.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT K.RANK, AddressLine1, City  
FROM Person.Address AS A  
  INNER JOIN  
  CONTAINSTABLE(Person.Address, AddressLine1, 'ISABOUT ("des*",  
    Rue WEIGHT(0.5),  
    Bouchers WEIGHT(0.9))',  
    3) AS K  
  ON A.AddressID = K.[KEY]  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
RANK        Address                          City  
----------- -------------------------------- ------------------------------  
172         9005, rue des Bouchers           Paris  
172         5, rue des Bouchers              Orleans  
172         5, rue des Bouchers              Metz  
  
(3 row(s) affected)  
```  
  
  
### <a name="example-b-searching-for-the-top-ten-matches"></a><span data-ttu-id="be8a7-118">範例 B：搜尋前十個相符項目</span><span class="sxs-lookup"><span data-stu-id="be8a7-118">Example B: Searching for the top ten matches</span></span>  
 <span data-ttu-id="be8a7-119">下列範例會使用 CONTAINSTABLE 傳回 `Description` 資料行在 "light" 或 "lightweight" 字附近包含 "aluminum" 一字的前 5 項產品描述。</span><span class="sxs-lookup"><span data-stu-id="be8a7-119">The following example uses CONTAINSTABLE to return the description of the top 5 products where the `Description` column contains the word "aluminum" near either the word "light" or the word "lightweight".</span></span>  
  
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
      (lightweight NEAR aluminum)',  
      5  
   ) AS KEY_TBL  
   ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
GO  
```  
  
  
##  <a name="how-search-query-results-are-ranked"></a><a name="how"></a> <span data-ttu-id="be8a7-120">搜尋查詢結果如何排序次序</span><span class="sxs-lookup"><span data-stu-id="be8a7-120">How Search Query Results Are Ranked</span></span>  
 <span data-ttu-id="be8a7-121">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的全文檢索搜尋可以產生選擇性分數 (或次序值)，表示全文檢索查詢傳回之資料的相關性。</span><span class="sxs-lookup"><span data-stu-id="be8a7-121">Full-text search in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can generate an optional score (or rank value) that indicates the relevance of the data returned by a full-text query.</span></span> <span data-ttu-id="be8a7-122">這個等級值是針對每個資料列計算的，而且可當做排序準則使用，以便依據相關性排序給定查詢的結果集。</span><span class="sxs-lookup"><span data-stu-id="be8a7-122">This rank value is calculated on every row and can be used as an ordering criteria to sort the result set of a given query by relevance.</span></span> <span data-ttu-id="be8a7-123">等級值僅表示結果集中資料列相關性的相對順序。</span><span class="sxs-lookup"><span data-stu-id="be8a7-123">The rank values indicate only a relative order of relevance of the rows in the result set.</span></span> <span data-ttu-id="be8a7-124">實際的值並不重要，而且每次執行查詢後該值通常會不一樣。</span><span class="sxs-lookup"><span data-stu-id="be8a7-124">The actual values are unimportant and typically differ each time the query is run.</span></span> <span data-ttu-id="be8a7-125">次序值不會在查詢之間保存任何重要性。</span><span class="sxs-lookup"><span data-stu-id="be8a7-125">The rank value does not hold any significance across queries.</span></span>  
  
### <a name="statistics-for-ranking"></a><span data-ttu-id="be8a7-126">排序的統計資料</span><span class="sxs-lookup"><span data-stu-id="be8a7-126">Statistics for Ranking</span></span>  
 <span data-ttu-id="be8a7-127">建立索引時會收集統計資料供評定等級使用。</span><span class="sxs-lookup"><span data-stu-id="be8a7-127">When an index is built, statistics are collected for use in ranking.</span></span> <span data-ttu-id="be8a7-128">建立全文檢索目錄的程序並不會直接導致單一索引結構。</span><span class="sxs-lookup"><span data-stu-id="be8a7-128">The process of building a full-text catalog does not directly result in a single index structure.</span></span> <span data-ttu-id="be8a7-129">相反地，Full-Text Engine for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會在編製資料索引時建立中繼索引。</span><span class="sxs-lookup"><span data-stu-id="be8a7-129">Instead, the Full-Text Engine for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] creates intermediate indexes as data is indexed.</span></span> <span data-ttu-id="be8a7-130">接著，全文檢索引擎會視需要將這些索引合併到較大的索引。</span><span class="sxs-lookup"><span data-stu-id="be8a7-130">The Full-Text Engine then merges these indexes into a larger index as needed.</span></span> <span data-ttu-id="be8a7-131">此程序可以重複許多次。</span><span class="sxs-lookup"><span data-stu-id="be8a7-131">This process can be repeated many times.</span></span> <span data-ttu-id="be8a7-132">接著，全文檢索引擎會執行「主要合併」，將所有的中繼索引合併至較大的主索引。</span><span class="sxs-lookup"><span data-stu-id="be8a7-132">The Full-Text Engine then conducts a "master merge" that combines all of the intermediate indexes into one large master index.</span></span>  
  
 <span data-ttu-id="be8a7-133">統計資料是在每個中繼索引層級中收集。</span><span class="sxs-lookup"><span data-stu-id="be8a7-133">Statistics are collected at each intermediate index level.</span></span> <span data-ttu-id="be8a7-134">合併索引時會合併統計資料。</span><span class="sxs-lookup"><span data-stu-id="be8a7-134">The statistics are merged when the indexes are merged.</span></span> <span data-ttu-id="be8a7-135">某些統計資料值只能在主要合併程序期間產生。</span><span class="sxs-lookup"><span data-stu-id="be8a7-135">Some statistical values can only be generated during the master merging process.</span></span>  
  
 <span data-ttu-id="be8a7-136">計算查詢結果集的等級時， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會使用最大中繼索引的統計資料。</span><span class="sxs-lookup"><span data-stu-id="be8a7-136">While ranking a query result set, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] uses statistics from the largest intermediate index.</span></span> <span data-ttu-id="be8a7-137">需視中繼索引合併與否而定。</span><span class="sxs-lookup"><span data-stu-id="be8a7-137">This depends on whether intermediate indexes have been merged or not.</span></span> <span data-ttu-id="be8a7-138">因此，如果中繼索引尚未合併，等級統計資料的精確度可能會有所變動。</span><span class="sxs-lookup"><span data-stu-id="be8a7-138">As a result, ranking statistics can vary in accuracy if the intermediate indexes have not been merged.</span></span> <span data-ttu-id="be8a7-139">這能解釋為何在一段時間的新增、修改、刪除全文檢索索引資料，以及在合併較小的索引之後，相同的查詢會傳回不同的等級結果。</span><span class="sxs-lookup"><span data-stu-id="be8a7-139">This explains why the same query can return different rank results over time as full-text indexed data is added, modified, and deleted, and as the smaller indexes are merged.</span></span>  
  
 <span data-ttu-id="be8a7-140">為了降低索引大小與計算的複雜度，通常會將統計資料四捨五入。</span><span class="sxs-lookup"><span data-stu-id="be8a7-140">To minimize the size of the index and computational complexity, statistics are often rounded.</span></span>  
  
 <span data-ttu-id="be8a7-141">下列清單包含一些計算等級時常用的重要詞彙與統計資料值。</span><span class="sxs-lookup"><span data-stu-id="be8a7-141">The list below includes some commonly used terms and statistical values that are important in calculating rank.</span></span>  
  
 <span data-ttu-id="be8a7-142">屬性</span><span class="sxs-lookup"><span data-stu-id="be8a7-142">Property</span></span>  
 <span data-ttu-id="be8a7-143">資料列的全文檢索索引資料行。</span><span class="sxs-lookup"><span data-stu-id="be8a7-143">A full-text indexed column of the row.</span></span>  
  
 <span data-ttu-id="be8a7-144">Document</span><span class="sxs-lookup"><span data-stu-id="be8a7-144">Document</span></span>  
 <span data-ttu-id="be8a7-145">在查詢中傳回的實體。</span><span class="sxs-lookup"><span data-stu-id="be8a7-145">The entity that is returned in queries.</span></span> <span data-ttu-id="be8a7-146">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，它會對應至資料列。</span><span class="sxs-lookup"><span data-stu-id="be8a7-146">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] this corresponds to a row.</span></span> <span data-ttu-id="be8a7-147">文件可以有多種屬性，就像資料列可以有多個全文檢索索引資料行。</span><span class="sxs-lookup"><span data-stu-id="be8a7-147">A document can have multiple properties, just as a row can have multiple full-text indexed columns.</span></span>  
  
 <span data-ttu-id="be8a7-148">索引</span><span class="sxs-lookup"><span data-stu-id="be8a7-148">Index</span></span>  
 <span data-ttu-id="be8a7-149">一或多個文件的單一反向索引。</span><span class="sxs-lookup"><span data-stu-id="be8a7-149">A single inverted index of one or more documents.</span></span> <span data-ttu-id="be8a7-150">它可能完全位於記憶體或磁碟中。</span><span class="sxs-lookup"><span data-stu-id="be8a7-150">This may be entirely in memory or on disk.</span></span> <span data-ttu-id="be8a7-151">許多查詢統計資料會與符合項目的個別索引有關。</span><span class="sxs-lookup"><span data-stu-id="be8a7-151">Many query statistics are relative to the individual index where the match occurred.</span></span>  
  
 <span data-ttu-id="be8a7-152">全文檢索目錄</span><span class="sxs-lookup"><span data-stu-id="be8a7-152">Full-Text Catalog</span></span>  
 <span data-ttu-id="be8a7-153">被視為查詢的一個實體的中繼索引集合。</span><span class="sxs-lookup"><span data-stu-id="be8a7-153">A collection of intermediate indexes treated as one entity for queries.</span></span> <span data-ttu-id="be8a7-154">目錄為 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理員可看見的組織單位。</span><span class="sxs-lookup"><span data-stu-id="be8a7-154">Catalogs are the unit of organization visible to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] administrator.</span></span>  
  
 <span data-ttu-id="be8a7-155">單字、Token 或項目</span><span class="sxs-lookup"><span data-stu-id="be8a7-155">Word, token or item</span></span>  
 <span data-ttu-id="be8a7-156">全文檢索引擎中的比對單位。</span><span class="sxs-lookup"><span data-stu-id="be8a7-156">The unit of matching in the full-text engine.</span></span> <span data-ttu-id="be8a7-157">會依語言特有的文字分隔，將文件中的文字資料流 Token 化為字組或 Token。</span><span class="sxs-lookup"><span data-stu-id="be8a7-157">Streams of text from documents are tokenized into words, or tokens by language-specific word breakers.</span></span>  
  
 <span data-ttu-id="be8a7-158">出現次數</span><span class="sxs-lookup"><span data-stu-id="be8a7-158">Occurrence</span></span>  
 <span data-ttu-id="be8a7-159">文件屬性中的文字位移，此文字位移由文字分隔來決定。</span><span class="sxs-lookup"><span data-stu-id="be8a7-159">The word offset in a document property as determined by the word breaker.</span></span> <span data-ttu-id="be8a7-160">第一個字是在發生 1，下個字是在發生 2，其餘依此類推。</span><span class="sxs-lookup"><span data-stu-id="be8a7-160">The first word is at occurrence 1, the next at 2, and so on.</span></span> <span data-ttu-id="be8a7-161">為避免片語誤判與近似查詢，句子的結尾與段落結尾會加入較大的發生間距。</span><span class="sxs-lookup"><span data-stu-id="be8a7-161">In order to avoid false positives in phrase and proximity queries, end-of-sentence and end-of-paragraph introduce larger occurrence gaps.</span></span>  
  
 <span data-ttu-id="be8a7-162">TermFrequency</span><span class="sxs-lookup"><span data-stu-id="be8a7-162">TermFrequency</span></span>  
 <span data-ttu-id="be8a7-163">資料列中出現的索引鍵值次數。</span><span class="sxs-lookup"><span data-stu-id="be8a7-163">The number times the key value occurs in a row.</span></span>  
  
 <span data-ttu-id="be8a7-164">IndexedRowCount</span><span class="sxs-lookup"><span data-stu-id="be8a7-164">IndexedRowCount</span></span>  
 <span data-ttu-id="be8a7-165">已編製索引的資料列總數。</span><span class="sxs-lookup"><span data-stu-id="be8a7-165">Total number of rows indexed.</span></span> <span data-ttu-id="be8a7-166">這會根據中繼索引中所維護的計數來計算。</span><span class="sxs-lookup"><span data-stu-id="be8a7-166">This is computed, based on counts maintained in the intermediate indexes.</span></span> <span data-ttu-id="be8a7-167">此數字在精確度上會有所不同。</span><span class="sxs-lookup"><span data-stu-id="be8a7-167">This number can vary in accuracy.</span></span>  
  
 <span data-ttu-id="be8a7-168">KeyRowCount</span><span class="sxs-lookup"><span data-stu-id="be8a7-168">KeyRowCount</span></span>  
 <span data-ttu-id="be8a7-169">含有指定索引鍵之全文檢索目錄的資料列總數。</span><span class="sxs-lookup"><span data-stu-id="be8a7-169">Total number of rows in the full-text catalog that contain a given key.</span></span>  
  
 <span data-ttu-id="be8a7-170">MaxOccurrence</span><span class="sxs-lookup"><span data-stu-id="be8a7-170">MaxOccurrence</span></span>  
 <span data-ttu-id="be8a7-171">全文檢索目錄中針對特定屬性儲存在資料列中的發生次數最大值。</span><span class="sxs-lookup"><span data-stu-id="be8a7-171">The largest occurrence stored in a full-text catalog for a given property in a row.</span></span>  
  
 <span data-ttu-id="be8a7-172">MaxQueryRank</span><span class="sxs-lookup"><span data-stu-id="be8a7-172">MaxQueryRank</span></span>  
 <span data-ttu-id="be8a7-173">全文檢索引擎會傳回最大的等級是 1000。</span><span class="sxs-lookup"><span data-stu-id="be8a7-173">The maximum rank, 1000, returned by the Full-Text Engine.</span></span>  
  
  
### <a name="rank-computation-issues"></a><span data-ttu-id="be8a7-174">等級計算問題</span><span class="sxs-lookup"><span data-stu-id="be8a7-174">Rank Computation Issues</span></span>  
 <span data-ttu-id="be8a7-175">計算等級的程序取決於幾項因素。</span><span class="sxs-lookup"><span data-stu-id="be8a7-175">The process of computing rank, depends on a number of factors.</span></span>  <span data-ttu-id="be8a7-176">不同語言的文字在分隔 Token 化文字的方式上會有所差異。</span><span class="sxs-lookup"><span data-stu-id="be8a7-176">Different language word breakers tokenize text differently.</span></span> <span data-ttu-id="be8a7-177">例如，使用某種文字分隔時會將 "dog-house" 字串分解成 "dog" "house"，而使用另一種文字分隔時會分解成 "dog-house"。</span><span class="sxs-lookup"><span data-stu-id="be8a7-177">For example, the string "dog-house" could be broken into "dog" "house" by one word breaker and into "dog-house" by another.</span></span> <span data-ttu-id="be8a7-178">這表示比對和等級會依據指定的語言而異，因為不僅單字不同，而且文件長度也不同。</span><span class="sxs-lookup"><span data-stu-id="be8a7-178">This means that matching and ranking will vary based on the language specified, because not only are the words different, but so is the document length.</span></span> <span data-ttu-id="be8a7-179">文件長度的差異會影響所有查詢的等級。</span><span class="sxs-lookup"><span data-stu-id="be8a7-179">The document length difference can affect ranking for all queries.</span></span>  
  
 <span data-ttu-id="be8a7-180">統計資料 (例如 `IndexRowCount`) 可能會有很大的差異。</span><span class="sxs-lookup"><span data-stu-id="be8a7-180">Statistics such as `IndexRowCount` can vary widely.</span></span> <span data-ttu-id="be8a7-181">例如，如果某個目錄在主索引中有 20 億個資料列，則會將一個新文件的索引編製到記憶體的中繼索引。而該文件會根據記憶體索引中的文件數目所得的等級，與主索引的文件等級進行非對稱比較。</span><span class="sxs-lookup"><span data-stu-id="be8a7-181">For example, if a catalog has 2 billion rows in the master index, then one new document is indexed into an in-memory intermediate index, and ranks for that document based on the number of documents in the in-memory index could be skewed compared with ranks for documents from the master index.</span></span> <span data-ttu-id="be8a7-182">因此，建議您在執行任何會造成大量資料列編製索引或重新編製索引的母體擴展動作後，使用 ALTER FULLTEXT CATALOG ... REORGANIZE [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式來將這些索引與主要的索引合併。</span><span class="sxs-lookup"><span data-stu-id="be8a7-182">For this reason, it is recommended that after any population that results in large number of rows being indexed or re-indexed the indexes be merged into a master index using the ALTER FULLTEXT CATALOG ... REORGANIZE [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="be8a7-183">全文檢索引擎也會根據參數 (例如中繼索引的數目與大小) 來自動合併索引。</span><span class="sxs-lookup"><span data-stu-id="be8a7-183">The Full-Text Engine will also automatically merge the indexes based on parameters such as the number and size of intermediate indexes.</span></span>  
  
 <span data-ttu-id="be8a7-184">`MaxOccurrence` 值會正規化為 32 種範圍中的其中一種。</span><span class="sxs-lookup"><span data-stu-id="be8a7-184">`MaxOccurrence` values are normalized into 1 of 32 ranges.</span></span> <span data-ttu-id="be8a7-185">這表示，會將長度 50 個字的文件視為與長度 100 個字的文件一樣。</span><span class="sxs-lookup"><span data-stu-id="be8a7-185">This means, for example, that a document 50 words long is treated the same as a document 100 words long.</span></span> <span data-ttu-id="be8a7-186">下表用於正規化作業。</span><span class="sxs-lookup"><span data-stu-id="be8a7-186">Below is the table used for normalization.</span></span> <span data-ttu-id="be8a7-187">因為檔長度在相鄰資料表值32和128之間的範圍內，所以會有效地將其視為具有相同的長度，128 (32 < `docLength` <= 128) 。</span><span class="sxs-lookup"><span data-stu-id="be8a7-187">Because the document lengths are in the range between adjacent table values 32 and 128, they are effectively treated as having the same length, 128 (32 < `docLength` <= 128).</span></span>  
  
```  
{ 16, 32, 128, 256, 512, 725, 1024, 1450, 2048, 2896, 4096, 5792, 8192, 11585,   
16384, 23170, 28000, 32768, 39554, 46340, 55938, 65536, 92681, 131072, 185363,   
262144, 370727, 524288, 741455, 1048576, 2097152, 4194304 };  
  
```  
  
  
### <a name="ranking-of-containstable"></a><span data-ttu-id="be8a7-188">CONTAINSTABLE 的等級</span><span class="sxs-lookup"><span data-stu-id="be8a7-188">Ranking of CONTAINSTABLE</span></span>  
 <span data-ttu-id="be8a7-189">[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 等級會使用下列演算法：</span><span class="sxs-lookup"><span data-stu-id="be8a7-189">[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) ranking uses the following algorithm:</span></span>  
  
```  
StatisticalWeight = Log2( ( 2 + IndexedRowCount ) / KeyRowCount )  
Rank = min( MaxQueryRank, HitCount * 16 * StatisticalWeight / MaxOccurrence )  
```  
  
 <span data-ttu-id="be8a7-190">片語比對會像個別索引鍵一樣來分級，但是會估計 `KeyRowCount` 值 (含有片語的資料列數目)，而且該值可能不正確並高於實際值。</span><span class="sxs-lookup"><span data-stu-id="be8a7-190">Phrase matches are ranked just like individual keys except that `KeyRowCount` (the number of rows containing the phrase) is estimated and can be inaccurate and higher than the actual number.</span></span>  
  
 <span data-ttu-id="be8a7-191">**NEAR 的等級**</span><span class="sxs-lookup"><span data-stu-id="be8a7-191">**Ranking of NEAR**</span></span>  
  
 <span data-ttu-id="be8a7-192">CONTAINSTABLE 支援使用 NEAR 選項來查詢彼此相近的兩個或多個搜尋詞彙。</span><span class="sxs-lookup"><span data-stu-id="be8a7-192">CONTAINSTABLE supports querying for two or more search terms in proximity to each other by using the NEAR option.</span></span> <span data-ttu-id="be8a7-193">每個傳回之資料列的等級值是以許多參數為基礎。</span><span class="sxs-lookup"><span data-stu-id="be8a7-193">The rank value of each returned row is based on several parameters.</span></span> <span data-ttu-id="be8a7-194">其中一個主要次序因數是相對於文件長度的符合項目 (或「叫用」  ) 總數。</span><span class="sxs-lookup"><span data-stu-id="be8a7-194">One major ranking factor is the total number of matches (or *hits*) relative to the length of the document.</span></span> <span data-ttu-id="be8a7-195">因此，例如，如果 100 個字的文件和 900 個字的文件包含完全相同的符合項目，100 個字的文件就會具有較高的等級。</span><span class="sxs-lookup"><span data-stu-id="be8a7-195">Thus, for example, if a 100-word document and a 900-word document contain identical matches, the 100-word document is ranked higher.</span></span>  
  
 <span data-ttu-id="be8a7-196">資料列中每個叫用的總長度也會根據該叫用之第一個和最後一個搜尋詞彙之間的距離影響該資料列的等級。</span><span class="sxs-lookup"><span data-stu-id="be8a7-196">The total length of each hit in a row will also contribute to the ranking of that row based on the distance between the first and last search terms of that hit.</span></span> <span data-ttu-id="be8a7-197">距離越小，叫用對資料列等級值造成的影響就越大。</span><span class="sxs-lookup"><span data-stu-id="be8a7-197">The smaller the distance, the more the hit contributes to the rank value of the row.</span></span> <span data-ttu-id="be8a7-198">如果全文檢索查詢沒有指定整數做為最大距離，只包含距離大於 100 個邏輯詞彙之叫用的文件將具有等級 0。</span><span class="sxs-lookup"><span data-stu-id="be8a7-198">If a full-text query does not specify an integer as the maximum distance, a document that contains only hits whose distances are greater than 100 logical terms apart, will have a ranking of 0.</span></span>  
  
 <span data-ttu-id="be8a7-199">**ISABOUT 的等級**</span><span class="sxs-lookup"><span data-stu-id="be8a7-199">**Ranking of ISABOUT**</span></span>  
  
 <span data-ttu-id="be8a7-200">CONTAINSTABLE 支援使用 ISABOUT 選項來查詢加權詞彙。</span><span class="sxs-lookup"><span data-stu-id="be8a7-200">CONTAINSTABLE supports querying for weighted terms by using the ISABOUT option.</span></span> <span data-ttu-id="be8a7-201">ISABOUT 是傳統資訊擷取詞彙中的向量空間查詢。</span><span class="sxs-lookup"><span data-stu-id="be8a7-201">ISABOUT is a vector-space query in traditional information retrieval terminology.</span></span> <span data-ttu-id="be8a7-202">預設使用的等級演算法是 Jaccard，這是一個相當有名的公式。</span><span class="sxs-lookup"><span data-stu-id="be8a7-202">The default ranking algorithm used is Jaccard, a widely known formula.</span></span> <span data-ttu-id="be8a7-203">會針對查詢中的每個詞彙計算等級，然後進行結合，如下表所述。</span><span class="sxs-lookup"><span data-stu-id="be8a7-203">The ranking is computed for each term in the query and then combined as described below.</span></span>  
  
```  
ContainsRank = same formula used for CONTAINSTABLE ranking of a single term (above).  
Weight = the weight specified in the query for each term. Default weight is 1.  
WeightedSum = ??[key=1 to n] ContainsRankKey * WeightKey  
Rank =  ( MaxQueryRank * WeightedSum ) / ( ( ??[key=1 to n] ContainsRankKey^2 )   
      + ( ??[key=1 to n] WeightKey^2 ) - ( WeightedSum ) )  
  
```  
  
  
### <a name="ranking-of-freetexttable"></a><span data-ttu-id="be8a7-204">FREETEXTTABLE 的等級</span><span class="sxs-lookup"><span data-stu-id="be8a7-204">Ranking of FREETEXTTABLE</span></span>  
 <span data-ttu-id="be8a7-205">[FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 等級是以 OKAPI BM25 等級公式為基礎。</span><span class="sxs-lookup"><span data-stu-id="be8a7-205">[FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) ranking is based on the OKAPI BM25 ranking formula.</span></span> <span data-ttu-id="be8a7-206">FREETEXTTABLE 查詢會透過變化衍生項 (原始查詢字的變化型式) 將單字加入到查詢中。這些單字會視為個別單字，而且與來源產生字沒有特殊的關聯性。</span><span class="sxs-lookup"><span data-stu-id="be8a7-206">FREETEXTTABLE queries will add words to the query via inflectional generation (inflected forms of the original query words); these words are treated as separate words with no special relationship to the words from which they were generated.</span></span> <span data-ttu-id="be8a7-207">由「同義字」功能所產生的同義字會視為個別詞彙，且加權值相同的詞彙。</span><span class="sxs-lookup"><span data-stu-id="be8a7-207">Synonyms generated from the Thesaurus feature are treated as separate, equally weighted terms.</span></span> <span data-ttu-id="be8a7-208">查詢中的每個單字都是計算等級的基礎。</span><span class="sxs-lookup"><span data-stu-id="be8a7-208">Each word in the query contributes to the rank.</span></span>  
  
```  
Rank = ??[Terms in Query] w ( ( ( k1 + 1 ) tf ) / ( K + tf ) ) * ( ( k3 + 1 ) qtf / ( k3 + qtf ) ) )  
Where:   
w is the Robertson-Sparck Jones weight.   
In simplified form, w is defined as:   
w = log10 ( ( ( r + 0.5 ) * ( N - R + r + 0.5 ) ) / ( ( R - r + 0.5 ) * ( n - r + 0.5 ) )  
N is the number of indexed rows for the property being queried.   
n is the number of rows containing the word.   
K is ( k1 * ( ( 1 - b ) + ( b * dl / avdl ) ) ).   
dl is the property length, in word occurrences.   
avdl is the average length of the property being queried, in word occurrences.   
k1, b, and k3 are the constants 1.2, 0.75, and 8.0, respectively.   
tf is the frequency of the word in the queried property in a specific row.   
qtf is the frequency of the term in the query.   
```  
  
  
## <a name="see-also"></a><span data-ttu-id="be8a7-209">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be8a7-209">See Also</span></span>  
 [<span data-ttu-id="be8a7-210">使用全文檢索搜尋查詢</span><span class="sxs-lookup"><span data-stu-id="be8a7-210">Query with Full-Text Search</span></span>](query-with-full-text-search.md)  
  
  
