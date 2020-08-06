---
title: 使用 XML 資料行進行全文檢索搜尋 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xml columns [full-text search]
- indexes [full-text search]
ms.assetid: 8096cfc6-1836-4ed5-a769-a5d63b137171
author: rothja
ms.author: jroth
ms.openlocfilehash: 2b6b23933fde6a09d043c7055b0daa7c07035cdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688629"
---
# <a name="use-full-text-search-with-xml-columns"></a><span data-ttu-id="80fb4-102">使用 XML 資料行進行全文檢索搜尋</span><span class="sxs-lookup"><span data-stu-id="80fb4-102">Use Full-Text Search with XML Columns</span></span>
  <span data-ttu-id="80fb4-103">您可以在 XML 資料行上建立全文檢索索引，以檢索 XML 值的內容，但忽略 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="80fb4-103">You can create a full-text index on XML columns that indexes the content of the XML values, but ignores the XML markup.</span></span> <span data-ttu-id="80fb4-104">元素標記會當做 Token 界限來使用。</span><span class="sxs-lookup"><span data-stu-id="80fb4-104">Element tags are used as token boundaries.</span></span> <span data-ttu-id="80fb4-105">其中會檢索下列項目：</span><span class="sxs-lookup"><span data-stu-id="80fb4-105">The following items are indexed:</span></span>  
  
-   <span data-ttu-id="80fb4-106">XML 元素的內容。</span><span class="sxs-lookup"><span data-stu-id="80fb4-106">The content of XML elements.</span></span>  
  
-   <span data-ttu-id="80fb4-107">僅限最上層元素之 XML 屬性的內容，除非這些值是數值。</span><span class="sxs-lookup"><span data-stu-id="80fb4-107">The content of XML attributes of the top-level element only, unless those values are numeric values.</span></span>  
  
 <span data-ttu-id="80fb4-108">在可能的情況下，您可以用下列方法將全文檢索搜尋與 XML 索引合併：</span><span class="sxs-lookup"><span data-stu-id="80fb4-108">When possible, you can combine full-text search with XML index in the following way:</span></span>  
  
1.  <span data-ttu-id="80fb4-109">首先，使用 SQL 全文檢索搜尋來篩選出感興趣的 XML 值。</span><span class="sxs-lookup"><span data-stu-id="80fb4-109">First, filter the XML values of interest by using SQL full-text search.</span></span>  
  
2.  <span data-ttu-id="80fb4-110">接著，查詢那些在 XML 資料行上使用 XML 索引的 XML 值。</span><span class="sxs-lookup"><span data-stu-id="80fb4-110">Next, query those XML values that use XML index on the XML column.</span></span>  
  
## <a name="example-combining-full-text-search-with-xml-querying"></a><span data-ttu-id="80fb4-111">範例：將全文檢索搜尋與 XML 查詢合併</span><span class="sxs-lookup"><span data-stu-id="80fb4-111">Example: Combining Full-text Search with XML Querying</span></span>  
 <span data-ttu-id="80fb4-112">在 XML 資料行上建立全文檢索之後，下列查詢會確認 XML 值在書名中有包含 "custom" 這個字：</span><span class="sxs-lookup"><span data-stu-id="80fb4-112">After the full-text index has been created on the XML column, the following query checks that an XML value contains the word "custom" in the title of a book:</span></span>  
  
```  
SELECT *   
FROM   T   
WHERE  CONTAINS(xCol,'custom')   
AND    xCol.exist('/book/title/text()[contains(.,"custom")]') =1  
```  
  
 <span data-ttu-id="80fb4-113">**contains()** 方法使用全文檢索來進一步設定在文件中任何地方含有 "custom" 這個字的 XML 值。</span><span class="sxs-lookup"><span data-stu-id="80fb4-113">The **contains()** method uses the full-text index to subset the XML values that contain the word "custom" anywhere in the document.</span></span> <span data-ttu-id="80fb4-114">**exist()** 子句可確定 "custom" 這個字有出現在書名中。</span><span class="sxs-lookup"><span data-stu-id="80fb4-114">The **exist()** clause ensures that the word "custom" occurs in the title of a book.</span></span>  
  
 <span data-ttu-id="80fb4-115">使用 **contains()** 和 XQuery **contains()** 的全文檢索搜尋具有不同的語意。</span><span class="sxs-lookup"><span data-stu-id="80fb4-115">A full-text search that uses **contains()** and XQuery **contains()** has different semantics.</span></span> <span data-ttu-id="80fb4-116">後者是子字串相符項，前者則是使用詞幹的 token 相符項。</span><span class="sxs-lookup"><span data-stu-id="80fb4-116">The latter is a substring match and the former is a token match that uses stemming.</span></span> <span data-ttu-id="80fb4-117">因此，如果該搜尋是要尋找書名中有 "run" 的字串，相符項中將會包含 "run"、"runs" 和 "running"，因為全文檢索 **contains()** 和 Xquery **contains()** 都滿足了。</span><span class="sxs-lookup"><span data-stu-id="80fb4-117">Therefore, if the search is for the string that has "run" in the title, the matches will include "run", "runs", and "running", because both the full-text **contains()** and the Xquery **contains()** are satisfied.</span></span> <span data-ttu-id="80fb4-118">然而，該查詢與書名中的 "customizable" 這個字不符，因為全文檢索 **contains()** 失敗，但滿足了 Xquery **contains()** 。</span><span class="sxs-lookup"><span data-stu-id="80fb4-118">However, the query does not match the word "customizable" in the title in that the full-text **contains()** fails, but the Xquery **contains()** is satisfied.</span></span> <span data-ttu-id="80fb4-119">一般而言，只要子字串相符，則應移除全文檢索 **contains()** 子句。</span><span class="sxs-lookup"><span data-stu-id="80fb4-119">Generally, for pure substring match, the full-text **contains()** clause should be removed.</span></span>  
  
 <span data-ttu-id="80fb4-120">此外，全文檢索搜尋會使用詞幹，但 XQuery **contains()** 是逐字比對的相符項。</span><span class="sxs-lookup"><span data-stu-id="80fb4-120">Additionally, full-text search uses word stemming, but XQuery **contains()** is a literal match.</span></span> <span data-ttu-id="80fb4-121">下一個範例將舉例說明之間的差異。</span><span class="sxs-lookup"><span data-stu-id="80fb4-121">This difference is illustrated in the next example.</span></span>  
  
## <a name="example-full-text-search-on-xml-values-using-stemming"></a><span data-ttu-id="80fb4-122">範例：使用詞幹對 XML 值進行全文檢索搜尋</span><span class="sxs-lookup"><span data-stu-id="80fb4-122">Example: Full-text Search on XML Values Using Stemming</span></span>  
 <span data-ttu-id="80fb4-123">在上個範例中執行的 XQuery **contains()** 檢查通常是無法排除的。</span><span class="sxs-lookup"><span data-stu-id="80fb4-123">The XQuery **contains()** check that was performed in the previous example generally cannot be eliminated.</span></span> <span data-ttu-id="80fb4-124">請考量這項查詢：</span><span class="sxs-lookup"><span data-stu-id="80fb4-124">Consider this query:</span></span>  
  
```  
SELECT *   
FROM   T   
WHERE  CONTAINS(xCol,'run')   
```  
  
 <span data-ttu-id="80fb4-125">文件中的 "ran" 之所以能夠符合搜尋條件，是因為使用詞幹，</span><span class="sxs-lookup"><span data-stu-id="80fb4-125">The word "ran" in the document matches the search condition because of stemming.</span></span> <span data-ttu-id="80fb4-126">而且沒有使用 XQuery 來檢查搜尋內容。</span><span class="sxs-lookup"><span data-stu-id="80fb4-126">Additionally, the search context is not checked by using XQuery.</span></span>  
  
 <span data-ttu-id="80fb4-127">當您使用全文檢索的 AXSD 來將 XML 分解成關聯式資料行時，在 XML 檢視上出現的 XPath 查詢就不會在基礎資料表上執行全文檢索搜尋。</span><span class="sxs-lookup"><span data-stu-id="80fb4-127">When XML is decomposed into relational columns by using AXSD that are full-text indexed, XPath queries that occur over the XML view do not perform full-text search on the underlying tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80fb4-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80fb4-128">See Also</span></span>  
 [<span data-ttu-id="80fb4-129">XML 索引 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="80fb4-129">XML Indexes &#40;SQL Server&#41;</span></span>](xml-indexes-sql-server.md)  
  
  
