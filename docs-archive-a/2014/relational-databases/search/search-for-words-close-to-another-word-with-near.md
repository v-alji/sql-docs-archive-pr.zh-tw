---
title: 使用 NEAR 搜尋靠近另一個單字的字詞 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- word searches [full-text search]
- NEAR option [full-text search]
- phrase searches [full-text search]
- proximity searches [full-text search]
- full-text search [SQL Server], proximity searches
- full-text queries [SQL Server], proximity
- queries [full-text search], proximity
ms.assetid: 87520646-4865-49ae-8790-f766b80a41f3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8c2d187ea3ed951ac6f17eb4babc5f4f77451d4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704021"
---
# <a name="search-for-words-close-to-another-word-with-near"></a><span data-ttu-id="57e62-102">使用 NEAR 搜尋靠近另一個單字的字詞</span><span class="sxs-lookup"><span data-stu-id="57e62-102">Search for Words Close to Another Word with NEAR</span></span>
  <span data-ttu-id="57e62-103">您可以在 [CONTAINS](/sql/t-sql/queries/contains-transact-sql) 述詞或 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 函數中使用鄰近字詞 (NEAR)，以便搜尋彼此接近的單字或片語。</span><span class="sxs-lookup"><span data-stu-id="57e62-103">You can use a proximity term (NEAR) in a [CONTAINS](/sql/t-sql/queries/contains-transact-sql) predicate or [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) function to search for words or phrases near one another.</span></span> <span data-ttu-id="57e62-104">您也可以指定分隔第一個和最後一個搜尋詞彙之非搜尋詞彙的數目上限。</span><span class="sxs-lookup"><span data-stu-id="57e62-104">You can also specify the maximum number of non-search terms that separate the first and last search terms.</span></span> <span data-ttu-id="57e62-105">此外，您也可以依任何順序或是您所指定的順序來搜尋單字或片語。</span><span class="sxs-lookup"><span data-stu-id="57e62-105">In addition, you can search for words or phrases in any order, or you can search for words and phrases in the order in which you specify them.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="57e62-106">支援舊版的[泛型相近詞彙](#Generic_NEAR)（現在已被取代）和[自訂鄰近詞彙](#Custom_NEAR)（中的新功能） [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="57e62-106">supports both the earlier [generic proximity term](#Generic_NEAR), which is now deprecated, and the [custom proximity term](#Custom_NEAR), which is new in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
##  <a name="the-custom-proximity-term"></a><a name="Custom_NEAR"></a><span data-ttu-id="57e62-107">自訂相近詞彙</span><span class="sxs-lookup"><span data-stu-id="57e62-107">The Custom Proximity Term</span></span>  
 <span data-ttu-id="57e62-108">自訂相近詞彙導入下列新功能：</span><span class="sxs-lookup"><span data-stu-id="57e62-108">The custom proximity term introduces the following new capabilities:</span></span>  
  
-   <span data-ttu-id="57e62-109">您可以指定分隔第一個和最後一個搜尋字詞之非搜尋字詞的數目上限 (或「最大距離」\*\*)，以便構成符合項目。</span><span class="sxs-lookup"><span data-stu-id="57e62-109">You can specify the maximum number of non-search terms, or *maximum distance*, that separates the first and last search terms in order to constitute a match.</span></span>  
  
-   <span data-ttu-id="57e62-110">如果您指定了詞彙的數目上限，也可以指定符合項目必須按照指定的順序包含搜尋詞彙。</span><span class="sxs-lookup"><span data-stu-id="57e62-110">If you specify the maximum number of terms, you can also specify that matches must contain the search terms in the specified order.</span></span>  
  
 <span data-ttu-id="57e62-111">若要成為符合項目，文字字串必須：</span><span class="sxs-lookup"><span data-stu-id="57e62-111">To qualify as a match, a string of text must:</span></span>  
  
-   <span data-ttu-id="57e62-112">以其中一個指定的搜尋詞彙為開頭，並且以其中一個指定的其他搜尋詞彙為結尾。</span><span class="sxs-lookup"><span data-stu-id="57e62-112">Start with one of the specified search terms and end with the one of the other specified search terms.</span></span>  
  
-   <span data-ttu-id="57e62-113">包含所有指定的搜尋詞彙。</span><span class="sxs-lookup"><span data-stu-id="57e62-113">Contain all of the specified search terms.</span></span>  
  
-   <span data-ttu-id="57e62-114">出現在第一個和最後一個搜尋詞彙之間的非搜尋詞彙 (包括停用字詞) 數目必須小於或等於最大距離 (如果有指定的話)。</span><span class="sxs-lookup"><span data-stu-id="57e62-114">The number of non-search terms, including stopwords, that occur between the first and last search terms must be less than or equal to the maximum distance, if specified.</span></span>  
  
 <span data-ttu-id="57e62-115">基本語法如下：</span><span class="sxs-lookup"><span data-stu-id="57e62-115">The basic syntax is:</span></span>  
  
 <span data-ttu-id="57e62-116">NEAR (</span><span class="sxs-lookup"><span data-stu-id="57e62-116">NEAR (</span></span>  
  
 <span data-ttu-id="57e62-117">{</span><span class="sxs-lookup"><span data-stu-id="57e62-117">{</span></span>  
  
 <span data-ttu-id="57e62-118">*search_term* [,.。。*n* ]</span><span class="sxs-lookup"><span data-stu-id="57e62-118">*search_term* [ ,...*n* ]</span></span>  
  
 |  
  
 <span data-ttu-id="57e62-119"> (*search_term* [,.。。*n* ] ) [，<maximum_distance> [，<match_order>]]</span><span class="sxs-lookup"><span data-stu-id="57e62-119">(*search_term* [ ,...*n* ] ) [, <maximum_distance> [, <match_order> ] ]</span></span>  
  
 <span data-ttu-id="57e62-120">}</span><span class="sxs-lookup"><span data-stu-id="57e62-120">}</span></span>  
  
 <span data-ttu-id="57e62-121">)</span><span class="sxs-lookup"><span data-stu-id="57e62-121">)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="57e62-122">如需 <custom_proximity_term> 語法的詳細資訊，請參閱 [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="57e62-122">For more information about the <custom_proximity_term> syntax, see [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql).</span></span>  
  
 <span data-ttu-id="57e62-123">例如，您可以搜尋與 'Smith' 距離兩個詞彙以內的 'John'，如下所示：</span><span class="sxs-lookup"><span data-stu-id="57e62-123">For example, you could search for 'John' within two terms of 'Smith', as follows:</span></span>  
  
```  
CONTAINS(column_name, 'NEAR((John, Smith), 2)')  
```  
  
 <span data-ttu-id="57e62-124">符合的部分字串範例包括 "`John Jacob Smith`" 和 "`Smith, John`"。</span><span class="sxs-lookup"><span data-stu-id="57e62-124">Some examples of strings that match are "`John Jacob Smith`" and "`Smith, John`".</span></span> <span data-ttu-id="57e62-125">"`John Jones knows Fred Smith`" 字串包含三個中介非搜尋詞彙，所以它不是符合項目。</span><span class="sxs-lookup"><span data-stu-id="57e62-125">The string "`John Jones knows Fred Smith`" contains three intervening non-search terms, so it is not a match.</span></span>  
  
 <span data-ttu-id="57e62-126">若要要求按照指定的順序尋找詞彙，您會將範例相近詞彙變更為 `NEAR((John, Smith),2, TRUE).` 。這樣就會搜尋與 "`John`" 距離兩個詞彙以內的 "`Smith`"，但是只有當 "`John`" 在 "`Smith`" 前面時才符合。</span><span class="sxs-lookup"><span data-stu-id="57e62-126">To require that the terms be found in the specified order, you would change the example proximity term to `NEAR((John, Smith),2, TRUE).` This searches for "`John`" within two terms of "`Smith`" but only when "`John`" precedes "`Smith`".</span></span> <span data-ttu-id="57e62-127">在由左至右閱讀的語言 (例如英文) 中，符合的字串範例為 "`John Jacob Smith`"。</span><span class="sxs-lookup"><span data-stu-id="57e62-127">In a language that reads from left to right, such as English, an example of a string that matches is "`John Jacob Smith`".</span></span>  
  
 <span data-ttu-id="57e62-128">請注意，若為由右至左閱讀的語言 (例如阿拉伯文或希伯來文)，全文檢索引擎就會按照反向順序套用指定的詞彙。</span><span class="sxs-lookup"><span data-stu-id="57e62-128">Note that for a language that reads from right to left, such as Arabic or Hebrew, the Full-Text Engine applies the specified terms in reverse order.</span></span> <span data-ttu-id="57e62-129">此外， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的 [物件總管] 會自動反轉以由右至左書寫語言所指定之單字的顯示順序。</span><span class="sxs-lookup"><span data-stu-id="57e62-129">Also, Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] automatically reverses the display order of words specified in right-to-left languages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="57e62-130">如需詳細資訊，請參閱本主題稍後的＜[有關鄰近搜尋的其他考量](#Additional_Considerations)＞。</span><span class="sxs-lookup"><span data-stu-id="57e62-130">For more information, see "[Additional Considerations about Proximity Searches](#Additional_Considerations)," later in this topic.</span></span>  
  
### <a name="how-maximum-distance-is-measured"></a><span data-ttu-id="57e62-131">最大距離的測量方式</span><span class="sxs-lookup"><span data-stu-id="57e62-131">How Maximum Distance Is Measured</span></span>  
 <span data-ttu-id="57e62-132">特定的最大距離 (例如 10 或 25) 會決定給定字串中出現在第一個和最後一個搜尋詞彙之間的非搜尋詞彙 (包含停用字詞) 數目。</span><span class="sxs-lookup"><span data-stu-id="57e62-132">A specific maximum distance, such as 10 or 25, determines how many non-search terms, including stopwords, can occur between the first and last search terms in a given string.</span></span> <span data-ttu-id="57e62-133">例如， `NEAR((dogs, cats, "hunting mice"), 3)` 會傳回下列資料列，其中非搜尋詞彙的總數是三 ("`enjoy`"、"`but`" 和 "`avoid`")：</span><span class="sxs-lookup"><span data-stu-id="57e62-133">For example, `NEAR((dogs, cats, "hunting mice"), 3)` would return the following row, in which the total number of non-search terms is three ("`enjoy`", "`but`", and "`avoid`"):</span></span>  
  
 <span data-ttu-id="57e62-134">"`Cats` `enjoy` `hunting mice``, but avoid` `dogs``.`"</span><span class="sxs-lookup"><span data-stu-id="57e62-134">"`Cats` `enjoy` `hunting mice``, but avoid` `dogs``.`"</span></span>  
  
 <span data-ttu-id="57e62-135">相同的相近詞彙不會傳回下列資料列，因為四個非搜尋詞彙 ("`enjoy`"、"`but`"、"`usually`" 和 "`avoid`") 超過了最大距離：</span><span class="sxs-lookup"><span data-stu-id="57e62-135">The same proximity term would not return the following row, because the maximum distance is exceeded by the four non-search terms ("`enjoy`", "`but`", "`usually`", and "`avoid`"):</span></span>  
  
 <span data-ttu-id="57e62-136">"`Cats` `enjoy` `hunting mice``, but usually avoid` `dogs``.`"</span><span class="sxs-lookup"><span data-stu-id="57e62-136">"`Cats` `enjoy` `hunting mice``, but usually avoid` `dogs``.`"</span></span>  
  
### <a name="combining-a-custom-proximity-term-with-other-terms"></a><span data-ttu-id="57e62-137">結合自訂相近詞彙與其他詞彙</span><span class="sxs-lookup"><span data-stu-id="57e62-137">Combining a Custom Proximity Term with Other Terms</span></span>  
 <span data-ttu-id="57e62-138">您可以結合自訂相近詞彙與其他某些詞彙。</span><span class="sxs-lookup"><span data-stu-id="57e62-138">You can combine a custom proximity term with some other terms.</span></span> <span data-ttu-id="57e62-139">您可以使用 AND (&)、OR (|) 或 AND NOT (&!) 來結合自訂鄰近字詞與其他自訂鄰近字詞、不可分割的字詞或前置字詞。</span><span class="sxs-lookup"><span data-stu-id="57e62-139">You can use AND (&), OR (|), or AND NOT (&!) to combine a custom proximity term with another custom proximity term, a simple term, or a prefix term.</span></span> <span data-ttu-id="57e62-140">例如：</span><span class="sxs-lookup"><span data-stu-id="57e62-140">For example:</span></span>  
  
-   <span data-ttu-id="57e62-141">CONTAINS('NEAR((*term1*,*term2*),5) AND *term3*')</span><span class="sxs-lookup"><span data-stu-id="57e62-141">CONTAINS('NEAR((*term1*,*term2*),5) AND *term3*')</span></span>  
  
-   <span data-ttu-id="57e62-142">CONTAINS('NEAR((*term1*,*term2*),5) OR *term3*')</span><span class="sxs-lookup"><span data-stu-id="57e62-142">CONTAINS('NEAR((*term1*,*term2*),5) OR *term3*')</span></span>  
  
-   <span data-ttu-id="57e62-143">CONTAINS('NEAR((*term1*,*term2*),5) AND NOT *term3*')</span><span class="sxs-lookup"><span data-stu-id="57e62-143">CONTAINS('NEAR((*term1*,*term2*),5) AND NOT *term3*')</span></span>  
  
-   <span data-ttu-id="57e62-144">CONTAINS('NEAR((*term1*,*term2*),5) AND NEAR((*term3*,*term4*),2)')</span><span class="sxs-lookup"><span data-stu-id="57e62-144">CONTAINS('NEAR((*term1*,*term2*),5) AND NEAR((*term3*,*term4*),2)')</span></span>  
  
-   <span data-ttu-id="57e62-145">CONTAINS('NEAR((*term1*,*term2*),5) OR NEAR((*term3*,*term4*),2, TRUE)')</span><span class="sxs-lookup"><span data-stu-id="57e62-145">CONTAINS('NEAR((*term1*,*term2*),5) OR NEAR((*term3*,*term4*),2, TRUE)')</span></span>  
  
 <span data-ttu-id="57e62-146">例如</span><span class="sxs-lookup"><span data-stu-id="57e62-146">For example,</span></span>  
  
```  
CONTAINS(column_name, 'NEAR((term1, term2), 5, TRUE) AND term3')  
```  
  
 <span data-ttu-id="57e62-147">您無法將自訂的鄰近詞彙與泛型相近詞彙結合 (*term1*接近*term2*) 、產生詞彙 (ISABOUT ... ) 或加權詞彙 (FORMSOF ... ) 。</span><span class="sxs-lookup"><span data-stu-id="57e62-147">You cannot combine a custom proximity term with a generic proximity term (*term1* NEAR *term2*), a generation term (ISABOUT ...), or a weighted term (FORMSOF ...).</span></span>  
  
### <a name="example-using-the-custom-proximity-term"></a><span data-ttu-id="57e62-148">範例：使用自訂相近詞彙</span><span class="sxs-lookup"><span data-stu-id="57e62-148">Example: Using the Custom Proximity Term</span></span>  
 <span data-ttu-id="57e62-149">下列範例會在 `Production.Document` 範例資料庫的 `AdventureWorks2012` 資料表中搜尋包含與 "bracket" 一字位於相同文件中之 "reflector" 一字的所有文件摘要。</span><span class="sxs-lookup"><span data-stu-id="57e62-149">The following example searches the `Production.Document` table of the `AdventureWorks2012` sample database for all document summaries that contain the word "reflector" in the same document as the word "bracket".</span></span>  
  
```  
SELECT DocumentNode, Title, DocumentSummary  
FROM Production.Document AS DocTable   
INNER JOIN CONTAINSTABLE(Production.Document, Document,  
  'NEAR(bracket, reflector)' ) AS KEY_TBL  
  ON DocTable.DocumentNode = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK > 50  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  

  
##  <a name="additional-considerations-for-proximity-searches"></a><a name="Additional_Considerations"></a><span data-ttu-id="57e62-150">鄰近搜尋的其他考慮</span><span class="sxs-lookup"><span data-stu-id="57e62-150">Additional Considerations for Proximity Searches</span></span>  
 <span data-ttu-id="57e62-151">本節將討論同時影響泛型和自訂鄰近搜尋的考量：</span><span class="sxs-lookup"><span data-stu-id="57e62-151">This section discusses consideration that affect both generic and custom proximity searches:</span></span>  
  
-   <span data-ttu-id="57e62-152">搜尋詞彙的重疊項目</span><span class="sxs-lookup"><span data-stu-id="57e62-152">Overlapping occurrences of search terms</span></span>  
  
     <span data-ttu-id="57e62-153">所有鄰近搜尋都只會尋找非重疊項目。</span><span class="sxs-lookup"><span data-stu-id="57e62-153">All proximity searches always look for only non-overlapping occurrences.</span></span> <span data-ttu-id="57e62-154">搜尋詞彙的重疊項目絕對不會成為符合項目。</span><span class="sxs-lookup"><span data-stu-id="57e62-154">Overlapping occurrences of search terms never qualify as matches.</span></span> <span data-ttu-id="57e62-155">例如，請考慮下列相近詞彙，它會按照此順序搜尋最大距離為兩個詞彙的 "`A`" 和 "`AA`"：</span><span class="sxs-lookup"><span data-stu-id="57e62-155">For example, consider the following proximity term, which searches "`A`" and "`AA`" in this order with a maximum distance of two terms:</span></span>  
  
    ```  
    CONTAINS(column_name, 'NEAR((A,AA),2, TRUE')  
    ```  
  
     <span data-ttu-id="57e62-156">可能的符合項目為 "`AAA`"、"`A.AA`" 和 "`A..AA`"。</span><span class="sxs-lookup"><span data-stu-id="57e62-156">The possible matches are as "`AAA`", "`A.AA`", and "`A..AA`".</span></span> <span data-ttu-id="57e62-157">只包含 "`AA`" 的資料列則不符合。</span><span class="sxs-lookup"><span data-stu-id="57e62-157">Rows containing just "`AA`" would not match.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="57e62-158">您可以指定重疊的詞彙，例如 `NEAR("mountain bike", "bike trails")` 或 `(NEAR(comfort*, comfortable), 5)`。</span><span class="sxs-lookup"><span data-stu-id="57e62-158">You can specify terms that overlap, for example, `NEAR("mountain bike", "bike trails")` or `(NEAR(comfort*, comfortable), 5)`.</span></span> <span data-ttu-id="57e62-159">指定重疊的詞彙會增加可能的符合項目排列，因而增加查詢的複雜性。</span><span class="sxs-lookup"><span data-stu-id="57e62-159">Specifying a overlapping terms increases the complexity of the query by increasing the possible match permutations.</span></span> <span data-ttu-id="57e62-160">如果您大量指定這類重疊的詞彙，查詢可能會耗盡資源並失敗。</span><span class="sxs-lookup"><span data-stu-id="57e62-160">If you specify a large number of such overlapping terms, the query can run out of resources and fail.</span></span> <span data-ttu-id="57e62-161">如果發生這種情況，請簡化查詢，然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="57e62-161">If this occurs, simplify the query and try again.</span></span>  
  
-   <span data-ttu-id="57e62-162">泛型 NEAR 和自訂 NEAR (不論是否指定最大距離) 都表示詞彙之間的邏輯距離，而非詞彙之間的絕對距離。</span><span class="sxs-lookup"><span data-stu-id="57e62-162">Both generic NEAR and custom NEAR (regardless of whether a maximum distance is specified) indicate the logical distance between terms, rather than the absolute distance between them.</span></span> <span data-ttu-id="57e62-163">例如，在某個段落中，不同片語或句子內的詞彙會比相同片語或句子內的詞彙被視為距離較遠，不論其實際距離為何都一樣，不過前提是它們都互不相關。</span><span class="sxs-lookup"><span data-stu-id="57e62-163">For example, terms within different phrases or sentences within a paragraph are treated as farther apart than terms in the same phrase or sentence, regardless of their actual proximity, on the assumption that they are less related.</span></span> <span data-ttu-id="57e62-164">同樣地，不同段落中的詞彙則被視為距離更遠。</span><span class="sxs-lookup"><span data-stu-id="57e62-164">Likewise, terms in different paragraphs are treated as being even farther apart.</span></span> <span data-ttu-id="57e62-165">如果某個符合項目跨越句子、段落或章節的結尾，用於排列文件等級的間距會分別增加 8、128 或 1024。</span><span class="sxs-lookup"><span data-stu-id="57e62-165">If a match spans the end of a sentence, paragraph, or chapter, the gap used for ranking a document is increased by 8, 128, or 1024, respectively.</span></span>  
  
-   <span data-ttu-id="57e62-166">相近詞彙對於 CONTAINSTABLE 函數排列等級的影響</span><span class="sxs-lookup"><span data-stu-id="57e62-166">Impact of proximity terms on ranking by the CONTAINSTABLE function</span></span>  
  
     <span data-ttu-id="57e62-167">在 CONTAINSTABLE 函數中使用 NEAR 時，文件的叫用次數相對於其長度以及每次叫用中第一個和最後一個搜尋詞彙之間的距離就會影響每份文件的等級。</span><span class="sxs-lookup"><span data-stu-id="57e62-167">When NEAR is used in the CONTAINSTABLE function, the number of hits in a document relative to its length as well as the distance between the first and last search terms in each of the hits affects the ranking of each document.</span></span> <span data-ttu-id="57e62-168">對於泛型相近詞彙而言，如果符合的搜尋詞彙距離 >50 個邏輯詞彙，針對文件傳回的等級就是 0。</span><span class="sxs-lookup"><span data-stu-id="57e62-168">For a generic proximity term, if the matched search terms are >50 logical terms apart, the rank returned on a document is 0.</span></span> <span data-ttu-id="57e62-169">若為沒有指定整數做為最大距離的自訂相近詞彙，只包含間距 >100 個邏輯詞彙之叫用的文件將收到的等級為 0。</span><span class="sxs-lookup"><span data-stu-id="57e62-169">For a custom proximity term that does not specify an integer as the maximum distance, a document that contains only hits whose gap is >100 logical terms will receive a ranking of 0.</span></span> <span data-ttu-id="57e62-170">如需自訂鄰近搜尋等級的詳細資訊，請參閱[限制 RANK 的搜索結果](limit-search-results-with-rank.md)。</span><span class="sxs-lookup"><span data-stu-id="57e62-170">For more information about ranking of custom proximity searches, see [Limit Search Results with RANK](limit-search-results-with-rank.md).</span></span>  
  
-   <span data-ttu-id="57e62-171">[轉換非搜尋字]\*\*\*\* 伺服器選項</span><span class="sxs-lookup"><span data-stu-id="57e62-171">The **transform noise words** server option</span></span>  
  
     <span data-ttu-id="57e62-172">如果您在鄰近搜尋中指定停用字詞，則 [轉換非搜尋字]\*\*\*\* 的值會影響 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理停用字詞的方式。</span><span class="sxs-lookup"><span data-stu-id="57e62-172">The value of **transform noise words** impacts how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] treats stopwords if they are specified in proximity searches.</span></span> <span data-ttu-id="57e62-173">如需詳細資訊，請參閱 [轉換非搜尋字伺服器組態選項](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="57e62-173">For more information, see [transform noise words Server Configuration Option](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md).</span></span>  
  

  
##  <a name="the-deprecated-generic-proximity-term"></a><a name="Generic_NEAR"></a><span data-ttu-id="57e62-174">已被取代的泛型相近詞彙</span><span class="sxs-lookup"><span data-stu-id="57e62-174">The Deprecated Generic Proximity Term</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]<span data-ttu-id="57e62-175">建議您使用[自訂鄰近字詞](#Custom_NEAR)。</span><span class="sxs-lookup"><span data-stu-id="57e62-175">We recommend that you use the [custom proximity term](#Custom_NEAR).</span></span>  
  
 <span data-ttu-id="57e62-176">泛型鄰近字詞表示指定的搜尋字詞必須全部都出現在同一份文件中，才會傳回符合項目，而不論搜尋字詞之間的非搜尋字詞數目 (「距離」\*\*) 為何。</span><span class="sxs-lookup"><span data-stu-id="57e62-176">A generic proximity term indicates that the specified search terms must all occur in a document for a match to be returned, regardless of the number of non-search terms (the *distance*) between the search terms.</span></span> <span data-ttu-id="57e62-177">基本語法如下：</span><span class="sxs-lookup"><span data-stu-id="57e62-177">The basic syntax is:</span></span>  
  
 <span data-ttu-id="57e62-178">{ *search_term* {NEAR | ~} *search_term* }[ ,...*n* ]</span><span class="sxs-lookup"><span data-stu-id="57e62-178">{ *search_term* { NEAR | ~ } *search_term* } [ ,...*n* ]</span></span>  
  
 <span data-ttu-id="57e62-179">例如，在下列範例中，'fox' 和 'chicken' 這兩個字必須同時出現 (按照任何順序)，才會產生符合項目：</span><span class="sxs-lookup"><span data-stu-id="57e62-179">For example, in the following examples, the words 'fox' and 'chicken' must both appear, in either order, to produce a match:</span></span>  
  
-   `CONTAINS(column_name, 'fox NEAR chicken')`  
  
-   `CONTAINSTABLE(table_name, column_name, 'fox ~ chicken')`  
  
> [!NOTE]  
>  <span data-ttu-id="57e62-180">如需 <generic_proximity_term> 語法的相關資訊，請參閱 [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="57e62-180">For information about the <generic_proximity_term> syntax, see [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql).</span></span>  
  
 <span data-ttu-id="57e62-181">如需詳細資訊，請參閱本主題稍後的＜[有關鄰近搜尋的其他考量](#Additional_Considerations)＞。</span><span class="sxs-lookup"><span data-stu-id="57e62-181">For more information, see "[Additional Considerations about Proximity Searches](#Additional_Considerations)," later in this topic.</span></span>  
  
### <a name="combining-a-generic-proximity-term-with-other-terms"></a><span data-ttu-id="57e62-182">結合泛型相近詞彙與其他詞彙</span><span class="sxs-lookup"><span data-stu-id="57e62-182">Combining a Generic Proximity Term with Other Terms</span></span>  
 <span data-ttu-id="57e62-183">您可以使用 AND (&)、OR (|) 或 AND NOT (&!) 來結合泛型鄰近字詞與其他泛型鄰近字詞、不可分割的字詞或前置字詞。</span><span class="sxs-lookup"><span data-stu-id="57e62-183">You can use AND (&), OR (|), or AND NOT (&!) to combine a generic proximity term with another generic proximity term, a simple term, or a prefix term.</span></span> <span data-ttu-id="57e62-184">例如：</span><span class="sxs-lookup"><span data-stu-id="57e62-184">For example:</span></span>  
  
```  
CONTAINSTABLE (Production.ProductDescription,  
   Description,   
   '(light NEAR aluminum) OR  
   (lightweight NEAR aluminum)'  
)  
```  
  
 <span data-ttu-id="57e62-185">您不能將泛型相近詞彙與自訂相近詞彙結合，例如 `NEAR((term1,term2),5)` ，加權詞彙 (ISABOUT ... ) ，或 (FORMSOF ... ) 的代詞。</span><span class="sxs-lookup"><span data-stu-id="57e62-185">You cannot combine a generic proximity term with a custom proximity term, such as `NEAR((term1,term2),5)`, a weighted term (ISABOUT ...), or a generational term (FORMSOF ...).</span></span>  
  
### <a name="example-using-the-generic-proximity-term"></a><span data-ttu-id="57e62-186">範例：使用泛型相近詞彙</span><span class="sxs-lookup"><span data-stu-id="57e62-186">Example: Using the Generic Proximity Term</span></span>  
 <span data-ttu-id="57e62-187">下列範例會使用泛型相近詞彙來搜尋與 "bracket" 一字位於相同文件中的 "reflector" 一字。</span><span class="sxs-lookup"><span data-stu-id="57e62-187">The following example uses the generic proximity term to search for the word "reflector" in the same document as the word "bracket".</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT DocumentNode, Title, DocumentSummary  
FROM Production.Document AS DocTable INNER JOIN  
  CONTAINSTABLE(Production.Document, Document,  
  '(reflector NEAR bracket)' ) AS KEY_TBL  
  ON DocTable.DocumentNode = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  
 <span data-ttu-id="57e62-188">請注意，將 CONTAINSTABLE 中的詞彙顛倒也可以得到相同的結果：</span><span class="sxs-lookup"><span data-stu-id="57e62-188">Notice that you can also reverse the terms in CONTAINSTABLE to get the same result:</span></span>  
  
```  
CONTAINSTABLE(Production.Document, Document, '(bracket NEAR reflector)' ) AS KEY_TBL  
```  
  
 <span data-ttu-id="57e62-189">您可以使用 (~) 字元來取代前面查詢中的 NEAR 關鍵字，也可得到相同的結果：</span><span class="sxs-lookup"><span data-stu-id="57e62-189">You can use the tilde character (~) in place of the NEAR keyword in the earlier query, and get the same results:</span></span>  
  
```  
CONTAINSTABLE(Production.Document, Document, '(reflector ~ bracket)' ) AS KEY_TBL  
```  
  
 <span data-ttu-id="57e62-190">搜尋條件中可以指定兩個以上單字或片語。</span><span class="sxs-lookup"><span data-stu-id="57e62-190">More than two words or phrases can be specified in the search conditions.</span></span> <span data-ttu-id="57e62-191">例如，您可以撰寫：</span><span class="sxs-lookup"><span data-stu-id="57e62-191">For example, it is possible to write:</span></span>  
  
```  
CONTAINSTABLE(Production.Document, Document, '(reflector ~ bracket ~ installation)' ) AS KEY_TBL  
```  
  
 <span data-ttu-id="57e62-192">這表示 "reflector" 必須與 "bracket" 位於相同的文件中，而且 "bracket" 必須與 "installation" 位於相同的文件中。</span><span class="sxs-lookup"><span data-stu-id="57e62-192">This means that "reflector" must be in the same document as "bracket", and "bracket" must be in the same document as "installation".</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="57e62-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57e62-193">See Also</span></span>  
 <span data-ttu-id="57e62-194">[CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57e62-194">[CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span></span>  
 <span data-ttu-id="57e62-195">[使用全文檢索搜尋進行查詢](query-with-full-text-search.md) </span><span class="sxs-lookup"><span data-stu-id="57e62-195">[Query with Full-Text Search](query-with-full-text-search.md) </span></span>  
 [<span data-ttu-id="57e62-196">CONTAINS &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="57e62-196">CONTAINS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/contains-transact-sql)  
  
  
