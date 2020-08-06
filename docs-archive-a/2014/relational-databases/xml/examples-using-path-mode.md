---
title: 範例：使用 PATH 模式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode, examples
ms.assetid: 3564e13b-9b97-49ef-8cf9-6a78677b09a3
author: rothja
ms.author: jroth
ms.openlocfilehash: 0876d93ffe246b6129a3838f8dbae47f3be7ffaf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710462"
---
# <a name="examples-using-path-mode"></a><span data-ttu-id="9ae35-102">範例：使用 PATH 模式</span><span class="sxs-lookup"><span data-stu-id="9ae35-102">Examples: Using PATH Mode</span></span>
  <span data-ttu-id="9ae35-103">以下範例說明使用 PATH 模式從 SELECT 查詢產生 XML。</span><span class="sxs-lookup"><span data-stu-id="9ae35-103">The following examples illustrate the use of PATH mode in generating XML from a SELECT query.</span></span> <span data-ttu-id="9ae35-104">這些查詢中有許多是針對自行車製造指示的 XML 文件所指定，這些文件是儲存在 ProductModel 資料表的 Instructions 資料行中。</span><span class="sxs-lookup"><span data-stu-id="9ae35-104">Many of these queries are specified against the bicycle manufacturing instructions XML documents that are stored in the Instructions column of the ProductModel table.</span></span>  
  
## <a name="specifying-a-simple-path-mode-query"></a><span data-ttu-id="9ae35-105">指定簡單 PATH 模式查詢</span><span class="sxs-lookup"><span data-stu-id="9ae35-105">Specifying a simple PATH mode query</span></span>  
 <span data-ttu-id="9ae35-106">此查詢指定 FOR XML PATH 模式。</span><span class="sxs-lookup"><span data-stu-id="9ae35-106">This query specifies a FOR XML PATH mode.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT   
       ProductModelID,  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 OR ProductModelID=119  
FOR XML PATH;  
GO  
```  
  
 <span data-ttu-id="9ae35-107">以下結果是元素中心的 XML，在產生的資料列集中每個資料行值都是包裝在元素中。</span><span class="sxs-lookup"><span data-stu-id="9ae35-107">The following result is element-centric XML where each column value in the resulting rowset is wrapped in an element.</span></span> <span data-ttu-id="9ae35-108">因為 `SELECT` 子句並不會為資料行名稱指定任何別名，所以產生的子元素名稱與 `SELECT` 子句中對應的資料行名稱相同。</span><span class="sxs-lookup"><span data-stu-id="9ae35-108">Because the `SELECT` clause does not specify any aliases for the column names, the child element names generated are the same as the corresponding column names in the `SELECT` clause.</span></span> <span data-ttu-id="9ae35-109">資料列集中的每個資料列都會加入 <`row`> 標記。</span><span class="sxs-lookup"><span data-stu-id="9ae35-109">For each row in the rowset a <`row`> tag is added.</span></span>  
  
 `<row>`  
  
 `<ProductModelID>122</ProductModelID>`  
  
 `<Name>All-Purpose Bike Stand</Name>`  
  
 `</row>`  
  
 `<row>`  
  
 `<ProductModelID>119</ProductModelID>`  
  
 `<Name>Bike Wash</Name>`  
  
 `</row>`  
  
 <span data-ttu-id="9ae35-110">下列結果與指定 `RAW` 選項之 `ELEMENTS` 模式查詢的結果相同。</span><span class="sxs-lookup"><span data-stu-id="9ae35-110">The following result is the same as the `RAW` mode query with the `ELEMENTS` option specified.</span></span> <span data-ttu-id="9ae35-111">它會為結果集中的每個資料列傳回元素中心的 XML 加上預設 <`row`> 元素。</span><span class="sxs-lookup"><span data-stu-id="9ae35-111">It returns element-centric XML with a default <`row`> element for each row in the result set.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 OR ProductModelID=119  
FOR XML RAW, ELEMENTS;  
```  
  
 <span data-ttu-id="9ae35-112">您可以選擇性地指定資料列元素名稱以覆寫預設的 <`row`>。</span><span class="sxs-lookup"><span data-stu-id="9ae35-112">You can optionally specify the row element name to overwrite the default <`row`>.</span></span> <span data-ttu-id="9ae35-113">例如，下列查詢會為資料列集中的每個資料列傳回 <`ProductModel`> 元素。</span><span class="sxs-lookup"><span data-stu-id="9ae35-113">For example, the following query returns the <`ProductModel`> element for each row in the rowset.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML PATH ('ProductModel');  
GO  
```  
  
 <span data-ttu-id="9ae35-114">產生的 XML 將會有指定的資料列元素名稱。</span><span class="sxs-lookup"><span data-stu-id="9ae35-114">The resulting XML will have a specified row element name.</span></span>  
  
 `<ProductModel>`  
  
 `<ProductModelID>122</ProductModelID>`  
  
 `<Name>All-Purpose Bike Stand</Name>`  
  
 `</ProductModel>`  
  
 `<ProductModel>`  
  
 `<ProductModelID>119</ProductModelID>`  
  
 `<Name>Bike Wash</Name>`  
  
 `</ProductModel>`  
  
 <span data-ttu-id="9ae35-115">如果您指定零長度的字串，就不會產生包裝的元素。</span><span class="sxs-lookup"><span data-stu-id="9ae35-115">If you specify a zero-length string, the wrapping element is not produced.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 OR ProductModelID=119  
FOR XML PATH ('');  
GO  
```  
  
 <span data-ttu-id="9ae35-116">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="9ae35-116">This is the result:</span></span>  
  
 `<ProductModelID>122</ProductModelID>`  
  
 `<Name>All-Purpose Bike Stand</Name>`  
  
 `<ProductModelID>119</ProductModelID>`  
  
 `<Name>Bike Wash</Name>`  
  
## <a name="specifying-xpath-like-column-names"></a><span data-ttu-id="9ae35-117">指定類似 XPath 的資料行名稱</span><span class="sxs-lookup"><span data-stu-id="9ae35-117">Specifying XPath-like column names</span></span>  
 <span data-ttu-id="9ae35-118">在以下查詢中，指定的 `ProductModelID` 資料行名稱是以 '\@' 開頭，而且不包含斜線 ('/')。</span><span class="sxs-lookup"><span data-stu-id="9ae35-118">In the following query the `ProductModelID` column name specified starts with '\@' and does not contain a slash mark ('/').</span></span> <span data-ttu-id="9ae35-119">因此，會在產生的 XML 中建立含有對應資料行值之 <`row`> 元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="9ae35-119">Therefore, an attribute of the <`row`> element that has the corresponding column value is created in the resulting XML.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID AS "@id",  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 OR ProductModelID=119  
FOR XML PATH ('ProductModelData');  
GO  
```  
  
 <span data-ttu-id="9ae35-120">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="9ae35-120">This is the result:</span></span>  
  
 `< ProductModelData id="122">`  
  
 `<Name>All-Purpose Bike Stand</Name>`  
  
 `</ ProductModelData >`  
  
 `< ProductModelData id="119">`  
  
 `<Name>Bike Wash</Name>`  
  
 `</ ProductModelData >`  
  
 <span data-ttu-id="9ae35-121">您可以在 `root` 中指定 `FOR XML`選項，以加入單一最上層元素。</span><span class="sxs-lookup"><span data-stu-id="9ae35-121">You can add a single top-level element by specifying the `root` option in `FOR XML`.</span></span>  
  
```  
SELECT ProductModelID AS "@id",  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML PATH ('ProductModelData'), root ('Root');  
GO  
```  
  
 <span data-ttu-id="9ae35-122">若要產生階層，您可以加入類似 PATH 的語法。</span><span class="sxs-lookup"><span data-stu-id="9ae35-122">To generate a hierarchy, you can include PATH-like syntax.</span></span> <span data-ttu-id="9ae35-123">例如，將 `Name` 資料行的資料行名稱變更為 "SomeChild/ModelName"，您就可以取得具有階層的 XML，如下列結果所示：</span><span class="sxs-lookup"><span data-stu-id="9ae35-123">For example, change the column name for the `Name` column to "SomeChild/ModelName" and you will obtain XML with hierarchy, as shown in this result:</span></span>  
  
 `<Root>`  
  
 `<ProductModelData id="122">`  
  
 `<SomeChild>`  
  
 `<ModelName>All-Purpose Bike Stand</ModelName>`  
  
 `</SomeChild>`  
  
 `</ProductModelData>`  
  
 `<ProductModelData id="119">`  
  
 `<SomeChild>`  
  
 `<ModelName>Bike Wash</ModelName>`  
  
 `</SomeChild>`  
  
 `</ProductModelData>`  
  
 `</Root>`  
  
 <span data-ttu-id="9ae35-124">除了產品型號識別碼與名稱之外，下列查詢還會擷取該產品型號的製造指示位置。</span><span class="sxs-lookup"><span data-stu-id="9ae35-124">Besides the product model ID and name, the following query retrieves the manufacturing instruction locations for the product model.</span></span> <span data-ttu-id="9ae35-125">由於 Instructions 資料行是 `xml` 類型，所以可以指定 `query()` 資料類型的 `xml` 方法來擷取位置。</span><span class="sxs-lookup"><span data-stu-id="9ae35-125">Because the Instructions column is of `xml` type, the `query()` method of `xml` data type is specified to retrieve the location.</span></span>  
  
```  
SELECT ProductModelID AS "@id",  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
                /MI:root/MI:Location   
              ') AS ManuInstr  
FROM Production.ProductModel  
WHERE ProductModelID = 7  
FOR XML PATH ('ProductModelData'), root ('Root');  
GO  
```  
  
 <span data-ttu-id="9ae35-126">以下是部份結果。</span><span class="sxs-lookup"><span data-stu-id="9ae35-126">This is the partial result.</span></span> <span data-ttu-id="9ae35-127">因為查詢會將 ManuInstr 指定為數據行名稱，所以方法所傳回的 XML `query()` 會包裝在 <> 標記中，如下所 `ManuInstr` 示：</span><span class="sxs-lookup"><span data-stu-id="9ae35-127">Because the query specifies ManuInstr as the column name, the XML returned by the `query()` method is wrapped in a <`ManuInstr`> tag as shown in the following:</span></span>  
  
 `<Root>`  
  
 `<ProductModelData id="7">`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<ManuInstr>`  
  
 `<MI:Location xmlns:MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"`  
  
 `<MI:step>...</MI:step>...`  
  
 `</MI:Location>`  
  
 `...`  
  
 `</ManuInstr>`  
  
 `</ProductModelData>`  
  
 `</Root>`  
  
 <span data-ttu-id="9ae35-128">在上述 FOR XML 查詢中，您可以加入 <`Root`> 與 <`ProductModelData`> 元素的命名空間。</span><span class="sxs-lookup"><span data-stu-id="9ae35-128">In the previous FOR XML query, you may want to include namespaces for the <`Root`> and <`ProductModelData`> elements.</span></span> <span data-ttu-id="9ae35-129">完成此動作的方式是先使用 WITH XMLNAMESPACES 與 FOR XML 查詢中的前置詞，以定義命名空間繫結的前置詞。</span><span class="sxs-lookup"><span data-stu-id="9ae35-129">You can do this by first defining the prefix to namespace binding by using WITH XMLNAMESPACES and using prefixes in the FOR XML query.</span></span> <span data-ttu-id="9ae35-130">如需詳細資訊，請參閱 [使用 WITH XMLNAMESPACES 將命名空間加入至查詢](add-namespaces-to-queries-with-with-xmlnamespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="9ae35-130">For more information, see [Add Namespaces to Queries with WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md).</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
WITH XMLNAMESPACES (  
   'uri1' AS ns1,    
   'uri2' AS ns2,  
   'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions' as MI)  
SELECT ProductModelID AS "ns1:ProductModelID",  
       Name           AS "ns1:Name",  
       Instructions.query('  
                /MI:root/MI:Location   
              ')   
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH ('ns2:ProductInfo'), root('ns1:root');  
GO  
```  
  
 <span data-ttu-id="9ae35-131">請注意， `MI` 前置詞在 `WITH XMLNAMESPACES`中也有定義。</span><span class="sxs-lookup"><span data-stu-id="9ae35-131">Note that the `MI` prefix is also defined in the `WITH XMLNAMESPACES`.</span></span> <span data-ttu-id="9ae35-132">因此，指定之 `query()` 類型的 `xml` 方法不會定義查詢初構中的前置詞。</span><span class="sxs-lookup"><span data-stu-id="9ae35-132">As a result, the `query()` method of the `xml` type specified does not define the prefix in the query prolog.</span></span> <span data-ttu-id="9ae35-133">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="9ae35-133">This is the result:</span></span>  
  
 `<ns1:root xmlns:MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" xmlns="uri2" xmlns:ns2="uri2" xmlns:ns1="uri1">`  
  
 `<ns2:ProductInfo>`  
  
 `<ns1:ProductModelID>7</ns1:ProductModelID>`  
  
 `<ns1:Name>HL Touring Frame</ns1:Name>`  
  
 `<MI:Location xmlns:MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"`  
  
 `LaborHours="2.5" LotSize="100" MachineHours="3" SetupHours="0.5" LocationID="10" xmlns="">`  
  
 `<MI:step>`  
  
 `Insert <MI:material>aluminum sheet MS-2341</MI:material> into the <MI:tool>T-85A framing tool</MI:tool>.`  
  
 `</MI:step>`  
  
 `...`  
  
 `</MI:Location>`  
  
 `...`  
  
 `</ns2:ProductInfo>`  
  
 `</ns1:root>`  
  
## <a name="generating-a-value-list-using-path-mode"></a><span data-ttu-id="9ae35-134">使用 PATH 模式產生值清單</span><span class="sxs-lookup"><span data-stu-id="9ae35-134">Generating a value list using PATH mode</span></span>  
 <span data-ttu-id="9ae35-135">對於每個產品型號，此查詢會建構產品識別碼的值清單。</span><span class="sxs-lookup"><span data-stu-id="9ae35-135">For each product model, this query constructs a value list of product IDs.</span></span> <span data-ttu-id="9ae35-136">對於每個產品識別碼，此查詢也會建構 <`ProductName`> 的巢狀元素，如下列 XML 片段所示：</span><span class="sxs-lookup"><span data-stu-id="9ae35-136">For each product ID, the query also constructs <`ProductName`> nested elements, as shown in this XML fragment:</span></span>  
  
 `<ProductModelData ProductModelID="7" ProductModelName="..."`  
  
 `ProductIDs="product id list in the product model" >`  
  
 `<ProductName>...</ProductName>`  
  
 `<ProductName>...</ProductName>`  
  
 `...`  
  
 `</ProductModelData>`  
  
 <span data-ttu-id="9ae35-137">這是會產生您所需 XML 的查詢：</span><span class="sxs-lookup"><span data-stu-id="9ae35-137">This is the query that produces the XML you want:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID     AS "@ProductModelID",  
       Name               S "@ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
       FOR XML PATH ('')) S "@ProductIDs",  
       (SELECT Name AS "ProductName"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
        FOR XML PATH ('')) as "ProductNames"  
FROM   Production.ProductModel  
WHERE  ProductModelID= 7 or ProductModelID=9  
FOR XML PATH('ProductModelData');  
```  
  
 <span data-ttu-id="9ae35-138">請注意下列項目是從上一個查詢而來：</span><span class="sxs-lookup"><span data-stu-id="9ae35-138">Note the following from the previous query:</span></span>  
  
-   <span data-ttu-id="9ae35-139">第一個巢狀 `SELECT` 使用 `data()` 做為資料行名稱，以傳回 ProductID 的清單。</span><span class="sxs-lookup"><span data-stu-id="9ae35-139">The first nested `SELECT` returns a list of ProductIDs by using `data()` as the column name.</span></span> <span data-ttu-id="9ae35-140">因為查詢在 `FOR XML PATH`中將空字串指定為資料列元素名稱，所以不會產生元素。</span><span class="sxs-lookup"><span data-stu-id="9ae35-140">Because the query specifies an empty string as the row element name in `FOR XML PATH`, no element is generated.</span></span> <span data-ttu-id="9ae35-141">值清單會改指派給 `ProductID` 屬性。</span><span class="sxs-lookup"><span data-stu-id="9ae35-141">Instead, the value list is assigned to the `ProductID` attribute.</span></span>  
  
-   <span data-ttu-id="9ae35-142">第二個巢狀 `SELECT` 會擷取產品型號中的產品名稱。</span><span class="sxs-lookup"><span data-stu-id="9ae35-142">The second nested `SELECT` retrieves product names for products in the product model.</span></span> <span data-ttu-id="9ae35-143">它會產生包裝在 <`ProductNames`> 元素中的 <`ProductName`> 元素，因為查詢會將 `ProductNames` 指定為資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="9ae35-143">It generates <`ProductName`> elements that are returned wrapped in the <`ProductNames`> element, because the query specifies `ProductNames` as the column name.</span></span>  
  
 <span data-ttu-id="9ae35-144">以下是部份結果：</span><span class="sxs-lookup"><span data-stu-id="9ae35-144">This is the partial result:</span></span>  
  
 `<ProductModelData PId="7"`  
  
 `ProductModelName="HL Touring Frame"`  
  
 `ProductIDs="885 887 ...">`  
  
 `<ProductNames>`  
  
 `<ProductName>HL Touring Frame - Yellow, 60</ProductName>`  
  
 `<ProductName>HL Touring Frame - Yellow, 46</ProductName></ProductNames>`  
  
 `...`  
  
 `</ProductModelData>`  
  
 `<ProductModelData PId="9"`  
  
 `ProductModelName="LL Road Frame"`  
  
 `ProductIDs="722 723 724 ...">`  
  
 `<ProductNames>`  
  
 `<ProductName>LL Road Frame - Black, 58</ProductName>`  
  
 `<ProductName>LL Road Frame - Black, 60</ProductName>`  
  
 `<ProductName>LL Road Frame - Black, 62</ProductName>`  
  
 `...`  
  
 `</ProductNames>`  
  
 `</ProductModelData>`  
  
 <span data-ttu-id="9ae35-145">建構產品名稱的子查詢會以實體化字串傳回結果，然後加入 XML。</span><span class="sxs-lookup"><span data-stu-id="9ae35-145">The subquery constructing the product names returns the result as a string that is entitized and then added to the XML.</span></span> <span data-ttu-id="9ae35-146">如果您加入類型指示詞 `FOR XML PATH (''), type`，子查詢會以 `xml` 類型傳回結果，而且不會發生實體化。</span><span class="sxs-lookup"><span data-stu-id="9ae35-146">If you add the type directive, `FOR XML PATH (''), type`, the subquery returns the result as `xml` type and no entitization occurs.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID AS "@ProductModelID",  
      Name AS "@ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
       FOR XML PATH ('')  
       ) AS "@ProductIDs",  
       (  
       SELECT Name AS "ProductName"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
       FOR XML PATH (''), type  
       ) AS "ProductNames"  
  
FROM Production.ProductModel  
WHERE ProductModelID= 7 OR ProductModelID=9  
FOR XML PATH('ProductModelData');  
```  
  
## <a name="adding-namespaces-in-the-resulting-xml"></a><span data-ttu-id="9ae35-147">在產生的 XML 中加入命名空間</span><span class="sxs-lookup"><span data-stu-id="9ae35-147">Adding namespaces in the resulting XML</span></span>  
 <span data-ttu-id="9ae35-148">如＜ [使用 WITH XMLNAMESPACES 新增命名空間](add-namespaces-to-queries-with-with-xmlnamespaces.md)＞主題中所述，您可以使用 WITH XMLNAMESPACES 在 PATH 模式查詢中包含命名空間。</span><span class="sxs-lookup"><span data-stu-id="9ae35-148">As described in [Adding Namespaces Using WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md), you can use WITH XMLNAMESPACES to include namespaces in the PATH mode queries.</span></span> <span data-ttu-id="9ae35-149">例如，SELECT 子句中指定的名稱包括命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="9ae35-149">For example, names specified in the SELECT clause include namespace prefixes.</span></span> <span data-ttu-id="9ae35-150">下列 `PATH` 模式查詢會建構包含命名空間的 XML。</span><span class="sxs-lookup"><span data-stu-id="9ae35-150">The following `PATH` mode query constructs XML with namespaces.</span></span>  
  
```  
SELECT 'en'    as "English/@xml:lang",  
       'food'  as "English",  
       'ger'   as "German/@xml:lang",  
       'Essen' as "German"  
FOR XML PATH ('Translation')  
GO  
```  
  
 <span data-ttu-id="9ae35-151">加入至 <`English`> 元素的 `@xml:lang` 屬性是在預先定義的 xml 命名空間中定義。</span><span class="sxs-lookup"><span data-stu-id="9ae35-151">The `@xml:lang` attribute added to the <`English`> element is defined in the predefined xml namespace.</span></span>  
  
 <span data-ttu-id="9ae35-152">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="9ae35-152">This is the result:</span></span>  
  
 `<Translation>`  
  
 `<English xml:lang="en">food</English>`  
  
 `<German xml:lang="ger">Essen</German>`  
  
 `</Translation>`  
  
 <span data-ttu-id="9ae35-153">下列查詢與範例 C 相似，除了它使用 `WITH XMLNAMESPACES` 在 XML 結果中加入命名空間之外。</span><span class="sxs-lookup"><span data-stu-id="9ae35-153">The following query is similar to example C, except that it uses `WITH XMLNAMESPACES` to include namespaces in the XML result.</span></span> <span data-ttu-id="9ae35-154">如需詳細資訊，請參閱 [使用 WITH XMLNAMESPACES 將命名空間加入至查詢](add-namespaces-to-queries-with-with-xmlnamespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="9ae35-154">For more information, see [Add Namespaces to Queries with WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md).</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
WITH XMLNAMESPACES ('uri1' AS ns1,  DEFAULT 'uri2')  
SELECT ProductModelID AS "@ns1:ProductModelID",  
      Name AS "@ns1:ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
       FOR XML PATH ('')  
       ) AS "@ns1:ProductIDs",  
       (  
       SELECT ProductID AS "@ns1:ProductID",   
              Name AS "@ns1:ProductName"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
       FOR XML PATH , type   
       ) AS "ns1:ProductNames"  
FROM Production.ProductModel  
WHERE ProductModelID= 7 OR ProductModelID=9  
FOR XML PATH('ProductModelData'), root('root');  
```  
  
 <span data-ttu-id="9ae35-155">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="9ae35-155">This is the result:</span></span>  
  
 `<root xmlns="uri2" xmlns:ns1="uri1">`  
  
 `<ProductModelData ns1:ProductModelID="7" ns1:ProductModelName="HL Touring Frame" ns1:ProductIDs="885 887 888 889 890 891 892 893">`  
  
 `<ns1:ProductNames>`  
  
 `<row xmlns="uri2" xmlns:ns1="uri1" ns1:ProductID="885" ns1:ProductName="HL Touring Frame - Yellow, 60" />`  
  
 `<row xmlns="uri2" xmlns:ns1="uri1" ns1:ProductID="887" ns1:ProductName="HL Touring Frame - Yellow, 46" />`  
  
 `...`  
  
 `</ns1:ProductNames>`  
  
 `</ProductModelData>`  
  
 `<ProductModelData ns1:ProductModelID="9" ns1:ProductModelName="LL Road Frame" ns1:ProductIDs="722 723 724 725 726 727 728 729 730 736 737 738">`  
  
 `<ns1:ProductNames>`  
  
 `<row xmlns="uri2" xmlns:ns1="uri1" ns1:ProductID="722" ns1:ProductName="LL Road Frame - Black, 58" />`  
  
 `...`  
  
 `</ns1:ProductNames>`  
  
 `</ProductModelData>`  
  
 `</root>`  
  
## <a name="see-also"></a><span data-ttu-id="9ae35-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ae35-156">See Also</span></span>  
 [<span data-ttu-id="9ae35-157">搭配 FOR XML 使用 PATH 模式</span><span class="sxs-lookup"><span data-stu-id="9ae35-157">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
