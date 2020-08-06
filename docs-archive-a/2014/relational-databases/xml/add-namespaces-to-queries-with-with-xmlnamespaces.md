---
title: 使用 WITH XMLNAMESPACES 將命名空間新增至查詢 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ELEMENTS XSINIL directive
- adding namespaces
- XSINIL directive
- default namespaces
- queries [XML in SQL Server], WITH XMLNAMESPACES clause
- predefined namespaces [XML in SQL Server]
- FOR XML clause, WITH XMLNAMESPACES clause
- namespaces [XML in SQL Server]
- xml data type [SQL Server], WITH XMLNAMESPACES clause
- WITH XMLNAMESPACES clause
ms.assetid: 2189cb5e-4460-46c5-a254-20c833ebbfec
author: rothja
ms.author: jroth
ms.openlocfilehash: ed5d719a845996215fffc18af64401779f848cd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585195"
---
# <a name="add-namespaces-to-queries-with-with-xmlnamespaces"></a><span data-ttu-id="3359f-102">使用 WITH XMLNAMESPACES 將命名空間加入至查詢</span><span class="sxs-lookup"><span data-stu-id="3359f-102">Add Namespaces to Queries with WITH XMLNAMESPACES</span></span>
  <span data-ttu-id="3359f-103">[WITH XMLNAMESPACES &#40;Transact-SQL&#41;](/sql/t-sql/xml/with-xmlnamespaces) 會以下列方式支援命名空間 URI：</span><span class="sxs-lookup"><span data-stu-id="3359f-103">[WITH XMLNAMESPACES (Transact-SQL)](/sql/t-sql/xml/with-xmlnamespaces) provides namespace URI support in the following way:</span></span>  
  
-   <span data-ttu-id="3359f-104">它可以在 [使用 FOR XML 查詢建構 XML](for-xml-sql-server.md) 時，讓命名空間前置詞到 URI 的對應可供使用。</span><span class="sxs-lookup"><span data-stu-id="3359f-104">It makes the namespace prefix to URI mapping available when [Constructing XML Using FOR XML](for-xml-sql-server.md) queries.</span></span>  
  
-   <span data-ttu-id="3359f-105">它讓 [xml 資料類型方法](/sql/t-sql/xml/xml-data-type-methods)的靜態命名空間內容，有 URI 對應的命名空間可用。</span><span class="sxs-lookup"><span data-stu-id="3359f-105">It makes the namespace to URI mapping available to the static namespace context of the [xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods).</span></span>  
  
## <a name="using-with-xmlnamespaces-in-the-for-xml-queries"></a><span data-ttu-id="3359f-106">在 FOR XML 查詢中使用 WITH XMLNAMESPACES</span><span class="sxs-lookup"><span data-stu-id="3359f-106">Using WITH XMLNAMESPACES in the FOR XML Queries</span></span>  
 <span data-ttu-id="3359f-107">WITH XMLNAMESPACES 讓您可以在 FOR XML 查詢中包括 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="3359f-107">WITH XMLNAMESPACES lets you include XML namespaces in FOR XML queries.</span></span> <span data-ttu-id="3359f-108">例如，請看下列的 FOR XML 查詢：</span><span class="sxs-lookup"><span data-stu-id="3359f-108">For example, consider the following FOR XML query:</span></span>  
  
```  
SELECT ProductID, Name, Color  
FROM   Production.Product  
WHERE  ProductID=316 or ProductID=317  
FOR XML RAW  
```  
  
 <span data-ttu-id="3359f-109">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="3359f-109">This is the result:</span></span>  
  
```  
<row ProductID="316" Name="Blade" />  
<row ProductID="317" Name="LL Crankarm" Color="Black" />  
  
```  
  
 <span data-ttu-id="3359f-110">若要將命名空間加入到 FOR XML 查詢所建構的 XML 中，請先使用 WITH NAMESPACES 子句，指定命名空間前置詞到 URI 的對應。</span><span class="sxs-lookup"><span data-stu-id="3359f-110">To add namespaces to the XML constructed by the FOR XML query, first specify the namespace prefix to URI mappings by using the WITH NAMESPACES clause.</span></span> <span data-ttu-id="3359f-111">接著，使用命名空間前置詞，在查詢中指定名稱，如下列修改過的查詢所示。</span><span class="sxs-lookup"><span data-stu-id="3359f-111">Then, use the namespace prefixes in specifying the names in the query as shown in the following modified query.</span></span> <span data-ttu-id="3359f-112">請注意，WITH XMLNAMESPACES 子句會指定命名空間前置詞 (`ns1`) 到 URI (`uri`) 的對應。</span><span class="sxs-lookup"><span data-stu-id="3359f-112">Note that the WITH XMLNAMESPACES clause specifies the namespace prefix (`ns1`) to URI (`uri`) mapping.</span></span> <span data-ttu-id="3359f-113">然後 `ns1` 前置詞會用來指定 FOR XML 查詢要建構的元素及屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="3359f-113">The `ns1` prefix is then used in specifying the element and attribute names to be constructed by the FOR XML query.</span></span>  
  
```  
WITH XMLNAMESPACES ('uri' as ns1)  
SELECT ProductID as 'ns1:ProductID',  
       Name      as 'ns1:Name',   
       Color     as 'ns1:Color'  
FROM Production.Product  
WHERE ProductID=316 or ProductID=317  
FOR XML RAW ('ns1:Prod'), ELEMENTS  
  
```  
  
 <span data-ttu-id="3359f-114">XML 結果會包括命名空間前置詞：</span><span class="sxs-lookup"><span data-stu-id="3359f-114">The XML result includes the namespace prefixes:</span></span>  
  
```  
<ns1:Prod xmlns:ns1="uri">  
  <ns1:ProductID>316</ns1:ProductID>  
  <ns1:Name>Blade</ns1:Name>  
</ns1:Prod>  
<ns1:Prod xmlns:ns1="uri">  
  <ns1:ProductID>317</ns1:ProductID>  
  <ns1:Name>LL Crankarm</ns1:Name>  
  <ns1:Color>Black</ns1:Color>  
</ns1:Prod>  
  
```  
  
 <span data-ttu-id="3359f-115">下列適用於 WITH XMLNAMESPACES 子句：</span><span class="sxs-lookup"><span data-stu-id="3359f-115">The following applies to the WITH XMLNAMESPACES clause:</span></span>  
  
-   <span data-ttu-id="3359f-116">只有 FOR XML 查詢的 RAW、AUTO 及 PATH 模式才支援。</span><span class="sxs-lookup"><span data-stu-id="3359f-116">It is supported only on the RAW, AUTO, and PATH modes of the FOR XML queries.</span></span> <span data-ttu-id="3359f-117">不支援 EXPLICIT 模式。</span><span class="sxs-lookup"><span data-stu-id="3359f-117">The EXPLICIT mode is not supported.</span></span>  
  
-   <span data-ttu-id="3359f-118">它只會影響 FOR XML 查詢的命名空間前置詞及 **xml** 資料類型方法，但不會影響 XML 剖析器。</span><span class="sxs-lookup"><span data-stu-id="3359f-118">It only affects the namespace prefixes of FOR XML queries and the **xml** data type methods, but not the XML parser.</span></span> <span data-ttu-id="3359f-119">例如，下列查詢會傳回錯誤，因為 XML 文件沒有 myNS 前置詞的命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="3359f-119">For example, the following query returns an error, because the XML document has no namespace declaration for the myNS prefix.</span></span>  
  
-   <span data-ttu-id="3359f-120">如果正在使用 WITH XMLNAMESPACES 子句，就不能使用 FOR XML 指示詞、XMLSCHEMA 及 XMLDATA。</span><span class="sxs-lookup"><span data-stu-id="3359f-120">The FOR XML directives, XMLSCHEMA and XMLDATA cannot be used when a WITH XMLNAMESPACES clause is being used.</span></span>  
  
    ```  
    CREATE TABLE T (x xml)  
    go  
    WITH XMLNAMESPACES ('http://abc' as myNS )  
    INSERT INTO T VALUES('<myNS:root/>')  
    ```  
  
## <a name="using-the-xsinil-directive"></a><span data-ttu-id="3359f-121">使用 XSINIL 指示詞</span><span class="sxs-lookup"><span data-stu-id="3359f-121">Using the XSINIL Directive</span></span>  
 <span data-ttu-id="3359f-122">若您正在使用 ELEMENTS XSINIL 指示詞，就無法在 WITH XMLNAMESPACES 子句中定義 xsi 前置詞。</span><span class="sxs-lookup"><span data-stu-id="3359f-122">You cannot define the xsi prefix in the WITH XMLNAMESPACES clause if you are using the ELEMENTS XSINIL directive.</span></span> <span data-ttu-id="3359f-123">不過，它會在您使用 ELEMENTS XSINIL 時自動加入。</span><span class="sxs-lookup"><span data-stu-id="3359f-123">Instead, it is added automatically when you use ELEMENTS XSINIL.</span></span> <span data-ttu-id="3359f-124">下列查詢會使用 ELEMENTS XSINIL，以產生元素中心的 XML，其中 Null 值會對應到 **xsi:nil** 屬性設為 True 的元素。</span><span class="sxs-lookup"><span data-stu-id="3359f-124">The following query uses ELEMENTS XSINIL that generates element-centric XML where null values are mapped to elements that have the **xsi:nil** attribute set to True.</span></span>  
  
```  
WITH XMLNAMESPACES ('uri' as ns1)  
SELECT ProductID as 'ns1:ProductID',  
       Name      as 'ns1:Name',   
       Color     as 'ns1:Color'  
FROM Production.Product  
WHERE ProductID=316   
FOR XML RAW, ELEMENTS XSINIL  
```  
  
 <span data-ttu-id="3359f-125">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="3359f-125">This is the result:</span></span>  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns1="uri">  
  <ns1:ProductID>316</ns1:ProductID>  
  <ns1:Name>Blade</ns1:Name>  
  <ns1:Color xsi:nil="true" />  
</row>  
```  
  
## <a name="specifying-default-namespaces"></a><span data-ttu-id="3359f-126">指定預設命名空間</span><span class="sxs-lookup"><span data-stu-id="3359f-126">Specifying Default Namespaces</span></span>  
 <span data-ttu-id="3359f-127">您可以使用 DEFAULT 關鍵字來宣告預設的命名空間，而不需要宣告命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="3359f-127">Instead of declaring a namespace prefix, you can declare a default namespace by using a DEFAULT keyword.</span></span> <span data-ttu-id="3359f-128">在 FOR XML 查詢中，它會將預設的命名空間繫結到產生之 XML 中的 XML 節點。</span><span class="sxs-lookup"><span data-stu-id="3359f-128">In the FOR XML query, it will bind the default namespace to XML nodes in the resulting XML.</span></span> <span data-ttu-id="3359f-129">在下面的範例中，WITH XMLNAMESPACES 定義兩個連同預設命名空間一起定義的命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="3359f-129">In the following example, the WITH XMLNAMESPACES defines two namespace prefixes that are defined together with a default namespace.</span></span>  
  
```  
WITH XMLNAMESPACES ('uri1' as ns1,   
                    'uri2' as ns2,  
                    DEFAULT 'uri2')  
SELECT ProductID,   
      Name,  
      Color  
FROM Production.Product   
WHERE ProductID=316 or ProductID=317  
FOR XML RAW ('ns1:Product'), ROOT('ns2:root'), ELEMENTS  
```  
  
 <span data-ttu-id="3359f-130">此 FOR XML 查詢會產生元素中心的 XML。</span><span class="sxs-lookup"><span data-stu-id="3359f-130">The FOR XML query generates element-centric XML.</span></span> <span data-ttu-id="3359f-131">請注意，此查詢在命名節點時兩個命名空間前置詞都會使用。</span><span class="sxs-lookup"><span data-stu-id="3359f-131">Note that the query uses both the namespace prefixes in naming nodes.</span></span> <span data-ttu-id="3359f-132">在 SELECT 子句中，ProductID、Name 及 Color 並未指定具有任何前置詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="3359f-132">In the SELECT clause, the ProductID, Name, and Color do not specify a name with any prefix.</span></span> <span data-ttu-id="3359f-133">因此，產生之 XML 中的對應元素會隸屬於預設的命名空間。</span><span class="sxs-lookup"><span data-stu-id="3359f-133">Therefore, the corresponding elements in the resulting XML belong to the default namespace.</span></span>  
  
```  
<ns2:root xmlns="uri2" xmlns:ns2="uri2" xmlns:ns1="uri1">  
  <ns1:Product>  
    <ProductID>316</ProductID>  
    <Name>Blade</Name>  
  </ns1:Product>  
  <ns1:Product>  
    <ProductID>317</ProductID>  
    <Name>LL Crankarm</Name>  
    <Color>Black</Color>  
  </ns1:Product>  
</ns2:root>  
```  
  
 <span data-ttu-id="3359f-134">下列查詢和前一個查詢很類似，差別只在下列查詢指定了 FOR XML AUTO 模式。</span><span class="sxs-lookup"><span data-stu-id="3359f-134">The following query is similar to the previous one, except that the FOR XML AUTO mode is specified.</span></span>  
  
```  
WITH XMLNAMESPACES ('uri1' as ns1,  'uri2' as ns2,DEFAULT 'uri2')  
SELECT ProductID,   
      Name,  
      Color  
FROM Production.Product as "ns1:Product"  
WHERE ProductID=316 or ProductID=317  
FOR XML AUTO, ROOT('ns2:root'), ELEMENTS  
```  
  
## <a name="using-predefined-namespaces"></a><span data-ttu-id="3359f-135">使用預先定義的命名空間</span><span class="sxs-lookup"><span data-stu-id="3359f-135">Using Predefined Namespaces</span></span>  
 <span data-ttu-id="3359f-136">使用預先定義的命名空間時，除了使用 ELEMENTS XSINIL 時的 xml 命名空間及 xsi 命名空間之外，您必須使用 WITH XMLNAMESPACES 明確地指定命名空間繫結。</span><span class="sxs-lookup"><span data-stu-id="3359f-136">When you use predefined namespaces, except the xml namespace and the xsi namespace when ELEMENTS XSINIL is used, you must explicitly specify the namespace binding by using WITH XMLNAMESPACES.</span></span> <span data-ttu-id="3359f-137">下列查詢針對預先定義的命名空間 (`urn:schemas-microsoft-com:xml-sql`) 明確地定義了命名空間前置詞到 URI 的繫結。</span><span class="sxs-lookup"><span data-stu-id="3359f-137">The following query explicitly defines the namespace prefix to URI binding for the predefined namespace (`urn:schemas-microsoft-com:xml-sql`).</span></span>  
  
```  
WITH XMLNAMESPACES ('urn:schemas-microsoft-com:xml-sql' as sql)  
SELECT 'SELECT * FROM Customers FOR XML AUTO, ROOT("a")' AS "sql:query"  
FOR XML PATH('sql:root')  
```  
  
 <span data-ttu-id="3359f-138">以下是結果。</span><span class="sxs-lookup"><span data-stu-id="3359f-138">This is the result.</span></span> <span data-ttu-id="3359f-139">SQLXML 的使用者對這個 XML 範本很熟悉。</span><span class="sxs-lookup"><span data-stu-id="3359f-139">SQLXML users are familiar with this XML template.</span></span> <span data-ttu-id="3359f-140">如需詳細資訊，請參閱 [SQLXML 4.0 程式設計概念](../sqlxml/sqlxml-4-0-programming-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="3359f-140">For more information, see [SQLXML 4.0 Programming Concepts](../sqlxml/sqlxml-4-0-programming-concepts.md).</span></span>  
  
```  
<sql:root xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>SELECT * FROM Customers FOR XML AUTO, ROOT("a")</sql:query>  
</sql:root>  
```  
  
 <span data-ttu-id="3359f-141">只有 xml 命名空間前置詞，不用在 WITH XMLNAMESPACES 中明確定義就可以使用，如以下 PATH 模式查詢中所示。</span><span class="sxs-lookup"><span data-stu-id="3359f-141">Only the xml namespace prefix can be used without explicitly defining it in WITH XMLNAMESPACES, as shown in the following PATH mode query.</span></span> <span data-ttu-id="3359f-142">同時，若前置詞已經宣告了，就必須將它繫結到命名空間 http://www.w3.org/XML/1998/namespace 。</span><span class="sxs-lookup"><span data-stu-id="3359f-142">Also, if the prefix is declared, it has to be bound to the namespace http://www.w3.org/XML/1998/namespace.</span></span> <span data-ttu-id="3359f-143">SELECT 子句中指定的名稱會參考不是使用 WITH XMLNAMESPACES 明確定義的 xml 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="3359f-143">The names specified in the SELECT clause refer to the xml namespace prefix that is not explicitly defined by using WITH XMLNAMESPACES.</span></span>  
  
```  
SELECT 'en'    as "English/@xml:lang",  
       'food'  as "English",  
       'ger'   as "German/@xml:lang",  
       'Essen' as "German"  
FOR XML PATH ('Translation')  
go  
```  
  
 <span data-ttu-id="3359f-144">@xml:lang 屬性會使用預先定義的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="3359f-144">The @xml:lang attributes use the predefined xml namespace.</span></span> <span data-ttu-id="3359f-145">因為 XML 1.0 版不需要明確宣告 xml 命名空間繫結，所以結果不會包括命名空間繫結的明確宣告。</span><span class="sxs-lookup"><span data-stu-id="3359f-145">Because XML version 1.0 does not require the explicit declaration of the xml namespace binding, the result will not include an explicit declaration of the namespace binding.</span></span>  
  
 <span data-ttu-id="3359f-146">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="3359f-146">This is the result:</span></span>  
  
```  
<Translation>  
  <English xml:lang="en">food</English>  
  <German xml:lang="ger">Essen</German>  
</Translation>  
```  
  
## <a name="using-with-xmlnamespaces-with-the-xml-data-type-methods"></a><span data-ttu-id="3359f-147">將 WITH XMLNAMESPACES 搭配 xml 資料類型方法使用</span><span class="sxs-lookup"><span data-stu-id="3359f-147">Using WITH XMLNAMESPACES with the xml Data Type Methods</span></span>  
 <span data-ttu-id="3359f-148">在 SELECT 查詢中指定 [xml 資料類型方法](/sql/t-sql/xml/xml-data-type-methods) (或 UPDATE 中指定 **modify()** 方法) 時，全部都必須在其初構中重複命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="3359f-148">The [xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) specified in a SELECT query, or in UPDATE when it is the **modify()** method, all have to repeat the namespace declaration in their prolog.</span></span> <span data-ttu-id="3359f-149">這可能會很費時。</span><span class="sxs-lookup"><span data-stu-id="3359f-149">This can be time-consuming.</span></span> <span data-ttu-id="3359f-150">例如，下列查詢會擷取其目錄描述確實包括規格的產品型號識別碼。</span><span class="sxs-lookup"><span data-stu-id="3359f-150">For example, the following query retrieves product model IDs whose catalog descriptions do include specification.</span></span> <span data-ttu-id="3359f-151">也就是說，有 <`Specifications`> 元素。</span><span class="sxs-lookup"><span data-stu-id="3359f-151">That is, the <`Specifications`> element exists.</span></span>  
  
```  
SELECT ProductModelID, CatalogDescription.query('  
declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
    <Product   
        ProductModelID= "{ sql:column("ProductModelID") }"   
        />  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('  
    declare namespace  pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     /pd:ProductDescription[(pd:Specifications)]'  
    ) = 1  
```  
  
 <span data-ttu-id="3359f-152">在上一個查詢中， **query()** 及 **exist()** 方法都在其初構中宣告了相同的命名空間。</span><span class="sxs-lookup"><span data-stu-id="3359f-152">In the previous query, both the **query()** and **exist()** methods declare the same namespace in their prolog.</span></span> <span data-ttu-id="3359f-153">例如：</span><span class="sxs-lookup"><span data-stu-id="3359f-153">For example:</span></span>  
  
```  
declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
```  
  
 <span data-ttu-id="3359f-154">另外，您也可以先宣告 WITH XMLNAMESPACES，然後在查詢中使用命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="3359f-154">Alternatively, you can declare WITH XMLNAMESPACES first and use the namespace prefixes in the query.</span></span> <span data-ttu-id="3359f-155">在此情況中， **query()** 及 **exist()** 方法就不需要在初構中包含命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="3359f-155">In this case, the **query()** and **exist()** methods  do not have to include namespace declarations in their prolog.</span></span>  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' as pd)  
SELECT ProductModelID, CatalogDescription.query('  
    <Product   
        ProductModelID= "{ sql:column("ProductModelID") }"   
        />  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('  
     /pd:ProductDescription[(pd:Specifications)]'  
    ) = 1  
Go  
```  
  
 <span data-ttu-id="3359f-156">請注意，XQuery 初構中的明確宣告會覆寫命名空間前置詞，以及 WITH 子句中定義的預設元素命名空間。</span><span class="sxs-lookup"><span data-stu-id="3359f-156">Note that an explicit declaration in the XQuery prolog overrides the namespace prefix and the default element namespace that are defined in the WITH clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3359f-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3359f-157">See Also</span></span>  
 <span data-ttu-id="3359f-158">[xml 資料類型方法](/sql/t-sql/xml/xml-data-type-methods) </span><span class="sxs-lookup"><span data-stu-id="3359f-158">[xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) </span></span>  
 <span data-ttu-id="3359f-159">[XQuery 語言參考 &#40;SQL Server&#41;](/sql/xquery/xquery-language-reference-sql-server) </span><span class="sxs-lookup"><span data-stu-id="3359f-159">[XQuery Language Reference &#40;SQL Server&#41;](/sql/xquery/xquery-language-reference-sql-server) </span></span>  
 <span data-ttu-id="3359f-160">[WITH XMLNAMESPACES &#40;Transact-SQL&#41;](/sql/t-sql/xml/with-xmlnamespaces) </span><span class="sxs-lookup"><span data-stu-id="3359f-160">[WITH XMLNAMESPACES &#40;Transact-SQL&#41;](/sql/t-sql/xml/with-xmlnamespaces) </span></span>  
 [<span data-ttu-id="3359f-161">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3359f-161">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
