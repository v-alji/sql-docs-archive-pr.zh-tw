---
title: 使用巢狀 FOR XML 查詢 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, nested FOR XML queries
- queries [XML in SQL Server], nested FOR XML
- nested FOR XML queries
ms.assetid: 7604161a-a958-446d-b102-7dee432979d0
author: rothja
ms.author: jroth
ms.openlocfilehash: 60c4198697f8d19c9b2e5bc1b415e0787861d40a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706281"
---
# <a name="use-nested-for-xml-queries"></a><span data-ttu-id="7d405-102">使用巢狀 FOR XML 查詢</span><span class="sxs-lookup"><span data-stu-id="7d405-102">Use Nested FOR XML Queries</span></span>
  <span data-ttu-id="7d405-103">`xml`資料類型和[for xml 查詢中的 type](type-directive-in-for-xml-queries.md)指示詞可讓 for xml 查詢傳回的 xml 在伺服器以及用戶端上進行處理。</span><span class="sxs-lookup"><span data-stu-id="7d405-103">The `xml` data type and the [TYPE directive in FOR XML queries](type-directive-in-for-xml-queries.md) enable the XML returned by the FOR XML queries to be processed on the server as well as on the client.</span></span>  
  
## <a name="processing-with-xml-type-variables"></a><span data-ttu-id="7d405-104">處理 xml 類型變數</span><span class="sxs-lookup"><span data-stu-id="7d405-104">Processing with xml Type Variables</span></span>  
 <span data-ttu-id="7d405-105">您可以將 FOR XML 查詢結果指派給 `xml` 類型變數，或是使用 XQuery 以查詢結果，然後將該結果指派給 `xml` 類型變數以進行其他處理。</span><span class="sxs-lookup"><span data-stu-id="7d405-105">You can assign the FOR XML query result to an `xml` type variable, or use XQuery to query the result, and assign that result to an `xml` type variable for more processing.</span></span>  
  
```  
DECLARE @x xml  
SET @x=(SELECT ProductModelID, Name  
        FROM Production.ProductModel  
        WHERE ProductModelID=122 or ProductModelID=119  
        FOR XML RAW, TYPE)  
SELECT @x  
-- Result  
--<row ProductModelID="122" Name="All-Purpose Bike Stand" />  
--<row ProductModelID="119" Name="Bike Wash" />  
```  
  
 <span data-ttu-id="7d405-106">使用其中一種 `xml` 資料類型方法，您就可以再額外處理以變數 `@x` 傳回的 XML。</span><span class="sxs-lookup"><span data-stu-id="7d405-106">You can additionally process the XML returned in the variable, `@x`, by using one of the `xml` data type methods.</span></span> <span data-ttu-id="7d405-107">例如，您可以使用 `ProductModelID` value() 方法 [來擷取](/sql/t-sql/xml/value-method-xml-data-type)屬性值。</span><span class="sxs-lookup"><span data-stu-id="7d405-107">For example, you can retrieve the `ProductModelID` attribute value by using the [value() method](/sql/t-sql/xml/value-method-xml-data-type).</span></span>  
  
```  
DECLARE @i int;  
SET @i = (SELECT @x.value('/row[1]/@ProductModelID[1]', 'int'));  
SELECT @i;  
```  
  
 <span data-ttu-id="7d405-108">在下列範例中，因為已在 `FOR XML` 子句中指定 `TYPE` 指示詞，所以傳回的 `FOR XML` 查詢結果為 `xml` 類型。</span><span class="sxs-lookup"><span data-stu-id="7d405-108">In the following example, the `FOR XML` query result is returned as an `xml` type, because the `TYPE` directive is specified in the `FOR XML` clause.</span></span>  
  
```  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=119 or ProductModelID=122  
FOR XML RAW, TYPE,ROOT('myRoot');  
  
```  
  
 <span data-ttu-id="7d405-109">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="7d405-109">This is the result:</span></span>  
  
```  
<myRoot>  
  <row ProductModelID="122" Name="All-Purpose Bike Stand" />  
  <row ProductModelID="119" Name="Bike Wash" />  
</myRoot>  
```  
  
 <span data-ttu-id="7d405-110">因為結果為 `xml` 類型，所以您可以直接對此 XML 指定其中一個 `xml` 資料類型方法，如以下查詢所示。</span><span class="sxs-lookup"><span data-stu-id="7d405-110">Because the result is of `xml` type, you can specify one of the `xml` data type methods directly against this XML, as shown in the following query.</span></span> <span data-ttu-id="7d405-111">在查詢中，會使用 [query() 方法 (xml 資料類型)](/sql/t-sql/xml/query-method-xml-data-type) 來擷取 <`myRoot`> 元素的第一個 <`row`> 元素子項。</span><span class="sxs-lookup"><span data-stu-id="7d405-111">In the query, the [query() method (xml Data Type)](/sql/t-sql/xml/query-method-xml-data-type) is used to retrieve the first <`row`> element child of the <`myRoot`> element.</span></span>  
  
```  
SELECT  (SELECT ProductModelID, Name  
         FROM Production.ProductModel  
         WHERE ProductModelID=119 or ProductModelID=122  
         FOR XML RAW, TYPE,ROOT('myRoot')).query('/myRoot[1]/row[1]');  
  
```  
  
 <span data-ttu-id="7d405-112">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="7d405-112">This is the result:</span></span>  
  
```  
<row ProductModelID="122" Name="All-Purpose Bike Stand" />  
```  
  
## <a name="returning-inner-for-xml-query-results-to-outer-queries-as-xml-type-instances"></a><span data-ttu-id="7d405-113">將內部 FOR XML 查詢結果當做 xml 類型執行個體傳回給外部查詢</span><span class="sxs-lookup"><span data-stu-id="7d405-113">Returning Inner FOR XML Query Results to Outer Queries as xml Type Instances</span></span>  
 <span data-ttu-id="7d405-114">您可以撰寫巢狀 `FOR XML` 查詢，其中的內部查詢結果會以 `xml` 類型傳回給外部查詢。</span><span class="sxs-lookup"><span data-stu-id="7d405-114">You can write nested `FOR XML` queries where the result of the inner query is returned as an `xml` type to the outer query.</span></span> <span data-ttu-id="7d405-115">例如：</span><span class="sxs-lookup"><span data-stu-id="7d405-115">For example:</span></span>  
  
```  
SELECT Col1,   
       Col2,   
       ( SELECT Col3, Col4   
        FROM  T2  
        WHERE T2.Col = T1.Col  
        ...  
        FOR XML AUTO, TYPE )  
FROM T1  
WHERE ...  
FOR XML AUTO, TYPE;  
```  
  
 <span data-ttu-id="7d405-116">請注意下列項目是從上一個查詢而來：</span><span class="sxs-lookup"><span data-stu-id="7d405-116">Note the following from the previous query:</span></span>  
  
-   <span data-ttu-id="7d405-117">以內部 `FOR XML` 查詢產生的 XML 會加入至外部 `FOR XML`產生的 XML 中。</span><span class="sxs-lookup"><span data-stu-id="7d405-117">The XML generated by the inner `FOR XML` query is added to the XML generated by the outer `FOR XML`.</span></span>  
  
-   <span data-ttu-id="7d405-118">內部查詢指定了 `TYPE` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="7d405-118">The inner query specifies the `TYPE` directive.</span></span> <span data-ttu-id="7d405-119">因此，內部查詢所傳回的 XML 資料為 `xml` 類型。</span><span class="sxs-lookup"><span data-stu-id="7d405-119">Therefore, the XML data returned by the inner query is of `xml` type.</span></span> <span data-ttu-id="7d405-120">如果未指定 TYPE 指示詞，會以 `nvarchar(max)` 傳回內部 `FOR XML` 查詢的結果，並實體化 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="7d405-120">If the TYPE directive is not specified, the result of the inner `FOR XML` query is returned as `nvarchar(max)` and the XML data is entitized.</span></span>  
  
## <a name="controlling-the-shape-of-resulting-xml-data"></a><span data-ttu-id="7d405-121">控制產生之 XML 資料的外觀</span><span class="sxs-lookup"><span data-stu-id="7d405-121">Controlling the Shape of Resulting XML Data</span></span>  
 <span data-ttu-id="7d405-122">巢狀 FOR XML 查詢可讓您有更多的控制權，以定義所產生之 XML 資料的外觀。</span><span class="sxs-lookup"><span data-stu-id="7d405-122">Nested FOR XML queries give you more control in defining the shape of the resulting XML data.</span></span> <span data-ttu-id="7d405-123">您可以使用 FOR XML 查詢來建構部分為屬性中心、部分為元素中心的 XML。</span><span class="sxs-lookup"><span data-stu-id="7d405-123">You can use nested FOR XML queries to construct XML that is partly attribute-centric and partly element-centric.</span></span>  
  
 <span data-ttu-id="7d405-124">如需使用巢狀 FOR XML 查詢指定屬性中心及元素中心之 XML 的詳細資訊，請參閱 [與巢狀 FOR XML 查詢比較的 FOR XML 查詢](../xml/for-xml-query-compared-to-nested-for-xml-query.md) 和 [使用巢狀 FOR XML 查詢組成 XML](../xml/shape-xml-with-nested-for-xml-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="7d405-124">For more information about specifying both attribute-centric and element-centric XML with nested FOR XML queries, see [FOR XML Query Compared to Nested FOR XML Query](../xml/for-xml-query-compared-to-nested-for-xml-query.md) and [Shape XML with Nested FOR XML Queries](../xml/shape-xml-with-nested-for-xml-queries.md).</span></span>  
  
 <span data-ttu-id="7d405-125">您可以指定巢狀 AUTO 模式 FOR XML 查詢來產生含有同層級的 XML 階層。</span><span class="sxs-lookup"><span data-stu-id="7d405-125">You can generate XML hierarchies that include siblings by specifying nested AUTO mode FOR XML queries.</span></span> <span data-ttu-id="7d405-126">如需詳細資訊，請參閱 [使用巢狀 AUTO 模式查詢產生同層級](../xml/generate-siblings-with-a-nested-auto-mode-query.md)。</span><span class="sxs-lookup"><span data-stu-id="7d405-126">For more information, see [Generate Siblings with a Nested AUTO Mode Query](../xml/generate-siblings-with-a-nested-auto-mode-query.md).</span></span>  
  
 <span data-ttu-id="7d405-127">不論您使用的模式為何，巢狀 FOR XML 查詢都能提供更多的控制權以描述所產生 XML 的形狀。</span><span class="sxs-lookup"><span data-stu-id="7d405-127">Regardless of which mode you use, nested FOR XML queries provide more control in describing the shape of the resulting XML.</span></span> <span data-ttu-id="7d405-128">它們可用來取代 EXPLICIT 模式查詢。</span><span class="sxs-lookup"><span data-stu-id="7d405-128">They can be used in the place of EXPLICIT mode queries.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7d405-129">範例</span><span class="sxs-lookup"><span data-stu-id="7d405-129">Examples</span></span>  
 <span data-ttu-id="7d405-130">下列主題將提供巢狀 FOR XML 查詢的範例。</span><span class="sxs-lookup"><span data-stu-id="7d405-130">The following topics provide examples of nested FOR XML queries.</span></span>  
  
 [<span data-ttu-id="7d405-131">與巢狀 FOR XML 查詢比較的 FOR XML 查詢</span><span class="sxs-lookup"><span data-stu-id="7d405-131">FOR XML Query Compared to Nested FOR XML Query</span></span>](../xml/for-xml-query-compared-to-nested-for-xml-query.md)  
 <span data-ttu-id="7d405-132">將單一層 FOR XML 查詢與巢狀 FOR XML 查詢做比較。</span><span class="sxs-lookup"><span data-stu-id="7d405-132">Compares a single-level FOR XML query to a nested FOR XML query.</span></span> <span data-ttu-id="7d405-133">此範例包含一個示範，說明如何同時將屬性中心和元素中心 XML 指定為查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="7d405-133">This example includes a demonstration of how to specify both attribute-centric and element-centric XML as the result of the query.</span></span>  
  
 [<span data-ttu-id="7d405-134">使用巢狀 AUTO 模式查詢產生同層級</span><span class="sxs-lookup"><span data-stu-id="7d405-134">Generate Siblings with a Nested AUTO Mode Query</span></span>](../xml/generate-siblings-with-a-nested-auto-mode-query.md)  
 <span data-ttu-id="7d405-135">示範如何使用巢狀 AUTO 模式查詢產生同層級</span><span class="sxs-lookup"><span data-stu-id="7d405-135">Shows how to generate siblings by using a nested AUTO mode query</span></span>  
  
 [<span data-ttu-id="7d405-136">在 ASP.NET 中使用巢狀 FOR XML 查詢</span><span class="sxs-lookup"><span data-stu-id="7d405-136">Use Nested FOR XML Queries in ASP.NET</span></span>](use-nested-for-xml-queries-in-asp-net.md)  
 <span data-ttu-id="7d405-137">示範 ASPX 應用程式如何使用 FOR XML，從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中傳回 XML。</span><span class="sxs-lookup"><span data-stu-id="7d405-137">Demonstrates how an ASPX application can use FOR XML to return XML from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="7d405-138">使用巢狀 FOR XML 查詢組成 XML</span><span class="sxs-lookup"><span data-stu-id="7d405-138">Shape XML with Nested FOR XML Queries</span></span>](../xml/shape-xml-with-nested-for-xml-queries.md)  
 <span data-ttu-id="7d405-139">示範如何使用巢狀 FOR XML 查詢，以控制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]建立之 XML 文件的結構。</span><span class="sxs-lookup"><span data-stu-id="7d405-139">Shows how to use nested FOR XML queries to control the structure of an XML document created by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
  
