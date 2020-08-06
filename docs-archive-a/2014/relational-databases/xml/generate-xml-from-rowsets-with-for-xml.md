---
title: 使用 FOR XML 從資料列集產生 XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, generating XML from rowsets
ms.assetid: d061c0f1-3de9-4ad1-bbca-ce45d064b6c8
author: rothja
ms.author: jroth
ms.openlocfilehash: dcf9feb4dab9ad1149ab433c9d9b4999c96c1cdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710418"
---
# <a name="generate-xml-from-rowsets-with-for-xml"></a><span data-ttu-id="3b93b-102">使用 FOR XML 從資料列集產生 XML</span><span class="sxs-lookup"><span data-stu-id="3b93b-102">Generate XML from Rowsets with FOR XML</span></span>
  <span data-ttu-id="3b93b-103">您可以 `xml` 使用 FOR XML 搭配新的**type**指示詞，從資料列集產生資料類型實例。</span><span class="sxs-lookup"><span data-stu-id="3b93b-103">You can generate an `xml` data type instance from a rowset by using FOR XML with the new **TYPE** directive.</span></span>  
  
 <span data-ttu-id="3b93b-104">可以將結果指派給 `xml` 資料類型資料行、變數或參數。</span><span class="sxs-lookup"><span data-stu-id="3b93b-104">The result can be assigned to an `xml` data type column, variable, or parameter.</span></span> <span data-ttu-id="3b93b-105">此外，還可以將 FOR XML 巢狀化，以產生任何階層式結構。</span><span class="sxs-lookup"><span data-stu-id="3b93b-105">Also, FOR XML can be nested to generate any hierarchical structure.</span></span> <span data-ttu-id="3b93b-106">與 FOR XML EXPLICIT 相較，這樣撰寫巢狀 FOR XML 更為方便，但是對於較深的階層，其效能可能沒那麼好。</span><span class="sxs-lookup"><span data-stu-id="3b93b-106">This makes nested FOR XML much more convenient to write than FOR XML EXPLICIT, but it may not perform as well for deep hierarchies.</span></span> <span data-ttu-id="3b93b-107">FOR XML 也導入了一種新的 PATH 模式。</span><span class="sxs-lookup"><span data-stu-id="3b93b-107">FOR XML also introduces a new PATH mode.</span></span> <span data-ttu-id="3b93b-108">這種新模式可以在資料行值出現的 XML 樹狀結構中指定路徑。</span><span class="sxs-lookup"><span data-stu-id="3b93b-108">This new mode specifies the path in the XML tree where a column's value appears.</span></span>  
  
 <span data-ttu-id="3b93b-109">新的 **FOR XML TYPE** 指示詞可用來定義含有 SQL 語法之關聯式資料的唯讀 XML 檢視。</span><span class="sxs-lookup"><span data-stu-id="3b93b-109">The new **FOR XML TYPE** directive can be used to define read-only XML views over relational data with SQL syntax.</span></span> <span data-ttu-id="3b93b-110">您可以用 SQL 陳述式和內嵌的 XQuery 來查詢該檢視，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="3b93b-110">The view can be queried with SQL statements and embedded XQuery, as shown in the following example.</span></span> <span data-ttu-id="3b93b-111">您也可以在預存程序中參照這些 SQL 檢視。</span><span class="sxs-lookup"><span data-stu-id="3b93b-111">You can also refer to these SQL views in stored procedures.</span></span>  
  
## <a name="example-sql-view-returning-generated-xml-data-type"></a><span data-ttu-id="3b93b-112">範例：傳回所產生之 XML 資料類型的 SQL 檢視</span><span class="sxs-lookup"><span data-stu-id="3b93b-112">Example: SQL View Returning Generated xml Data Type</span></span>  
 <span data-ttu-id="3b93b-113">下列 SQL 檢視定義會建立一個 XML 檢視，可供檢視從 XML 資料行中擷取的關聯式資料行、pk 及書籍作者。</span><span class="sxs-lookup"><span data-stu-id="3b93b-113">The following SQL view definition creates an XML view over a relational column, pk, and book authors retrieved from an XML column:</span></span>  
  
```  
CREATE VIEW V (xmlVal) AS  
SELECT pk, xCol.query('/book/author')  
FROM   T  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="3b93b-114">V view 包含單一資料列，其中具有 XML 類型的單一 columnxmlVal， `.` 它可以像一般 `xml` 資料類型實例一樣進行查詢。</span><span class="sxs-lookup"><span data-stu-id="3b93b-114">The V view contains a single row with a single columnxmlVal of XML type`.` It can be queried like a regular `xml` data type instance.</span></span> <span data-ttu-id="3b93b-115">例如，下列查詢會傳回名字叫 "David" 的作者：</span><span class="sxs-lookup"><span data-stu-id="3b93b-115">For example, the following query returns the author whose first name is "David":</span></span>  
  
```  
SELECT xmlVal.query('//author[first-name = "David"]')  
FROM   V  
```  
  
 <span data-ttu-id="3b93b-116">SQL 檢視定義有點像用註解結構描述來建立的 XML 檢視。</span><span class="sxs-lookup"><span data-stu-id="3b93b-116">SQL view definitions are somewhat similar to XML views that are created by using annotated schemas.</span></span> <span data-ttu-id="3b93b-117">但是，有幾個重要的相異之處。</span><span class="sxs-lookup"><span data-stu-id="3b93b-117">However, there are important differences.</span></span> <span data-ttu-id="3b93b-118">SQL 檢視定義是唯讀的，而且必須用內嵌的 XQuery 來操控。</span><span class="sxs-lookup"><span data-stu-id="3b93b-118">The SQL view definition is read-only and must be manipulated with embedded XQuery.</span></span> <span data-ttu-id="3b93b-119">XML 檢視則是用註解結構描述所建立。</span><span class="sxs-lookup"><span data-stu-id="3b93b-119">The XML views are created by using annotated schema.</span></span> <span data-ttu-id="3b93b-120">此外，SQL 檢視會先將 XML 結果具體化，再套用 XQuery 運算式，而 XML 檢視上的 XPath 查詢則是會在基礎資料表上評估 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="3b93b-120">Additionally, the SQL view materializes the XML result before applying the XQuery expression, while the XPath queries on XML views evaluate SQL queries on the underlying tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b93b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b93b-121">See Also</span></span>  
 [<span data-ttu-id="3b93b-122">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3b93b-122">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
