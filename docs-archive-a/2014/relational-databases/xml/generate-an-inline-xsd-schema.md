---
title: 產生內嵌 XSD 結構描述 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XSD schemas [SQL Server]
- XMLSCHEMA option
- schemas [SQL Server], XML
- XDR schemas
- FOR XML clause, inline XSD schema generation
- inline XSD schema generation [SQL Server]
- XMLDATA option
ms.assetid: 04b35145-1cca-45f4-9eb7-990abf2e647d
author: rothja
ms.author: jroth
ms.openlocfilehash: 2af748d4fc6ae67f57568be58ec7f59876098f52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710433"
---
# <a name="generate-an-inline-xsd-schema"></a><span data-ttu-id="93543-102">產生內嵌 XSD 結構描述</span><span class="sxs-lookup"><span data-stu-id="93543-102">Generate an Inline XSD Schema</span></span>
  <span data-ttu-id="93543-103">在 FOR XML 子句中，您可以要求您的查詢將內嵌結構描述連同查詢結果一起傳回。</span><span class="sxs-lookup"><span data-stu-id="93543-103">In a FOR XML clause, you can request that your query return an inline schema together with the query results.</span></span> <span data-ttu-id="93543-104">如果您要的是 XDR 結構描述，請在 FOR XML 子句中使用 XMLDATA 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="93543-104">If you want an XDR schema, you use the XMLDATA keyword in the FOR XML clause.</span></span> <span data-ttu-id="93543-105">而如果您要的是 XSD 結構描述，則請使用 XMLSCHEMA 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="93543-105">If you want an XSD schema, you use the XMLSCHEMA keyword.</span></span>  
  
 <span data-ttu-id="93543-106">此主題描述 XMLSCHEMA 關鍵字，並說明所產生之內嵌 XSD 結構描述的結構。</span><span class="sxs-lookup"><span data-stu-id="93543-106">This topic describes the XMLSCHEMA keyword and explains the structure of the resulting inline XSD schema.</span></span> <span data-ttu-id="93543-107">以下是要求內嵌結構描述時的一些限制：</span><span class="sxs-lookup"><span data-stu-id="93543-107">Following are the limitations when you are requesting inline schemas:</span></span>  
  
-   <span data-ttu-id="93543-108">您只能在 RAW 和 AUTO 模式中指定 XMLSCHEMA，但不能在 EXPLICIT 模式中指定。</span><span class="sxs-lookup"><span data-stu-id="93543-108">You can specify XMLSCHEMA only in RAW and AUTO mode, not in EXPLICIT mode.</span></span>  
  
-   <span data-ttu-id="93543-109">如果巢狀 FOR XML 查詢指定了 TYPE 指示詞，則查詢結果會是 `xml` 類型，但此結果會當做不具類型之 XML 資料的執行個體來處理。</span><span class="sxs-lookup"><span data-stu-id="93543-109">If a nested FOR XML query specifies the TYPE directive, the query result is of `xml` type, and this result is treated as an instance of untyped XML data.</span></span> <span data-ttu-id="93543-110">如需詳細資訊，請參閱 [XML 資料 &#40;SQL Server&#41;](xml-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="93543-110">For more information, see [XML Data &#40;SQL Server&#41;](xml-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="93543-111">當您在 FOR XML 查詢中指定 XMLSCHEMA 時，會同時收到結構描述和 XML 資料做為查詢結果。</span><span class="sxs-lookup"><span data-stu-id="93543-111">When you specify XMLSCHEMA in a FOR XML query, you receive both a schema and XML data, the query result.</span></span> <span data-ttu-id="93543-112">此資料的每一個最上層元素使用預設命名空間宣告來參考上一個結構描述，此宣告再參考內嵌結構描述的目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="93543-112">Each top-level element of the data refers to the previous schema by using a default namespace declaration that, in turn, refers to the target namespace of the inline schema.</span></span>  
  
 <span data-ttu-id="93543-113">例如：</span><span class="sxs-lookup"><span data-stu-id="93543-113">For example:</span></span>  
  
```  
<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:schema="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">  
  <xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />  
  <xsd:element name="Production.ProductModel">  
    <xsd:complexType>  
      <xsd:attribute name="ProductModelID" type="sqltypes:int" use="required" />  
      <xsd:attribute name="Name" use="required">  
        <xsd:simpleType sqltypes:sqlTypeAlias="[AdventureWorks2012].[dbo].[Name]">  
          <xsd:restriction base="sqltypes:nvarchar" sqltypes:localeId="1033" sqltypes:sqlCompareOptions="IgnoreCase IgnoreKanaType IgnoreWidth" sqltypes:sqlSortId="52">  
            <xsd:maxLength value="50" />  
          </xsd:restriction>  
        </xsd:simpleType>  
      </xsd:attribute>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
<Production.ProductModel xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1" ProductModelID="1" Name="Classic Vest" />  
```  
  
 <span data-ttu-id="93543-114">此結果包含 XML 結構描述和 XML 結果。</span><span class="sxs-lookup"><span data-stu-id="93543-114">The result includes XML schema and the XML result.</span></span> <span data-ttu-id="93543-115">結果中的 <`ProductModel`> 最上層元素使用預設命名空間宣告 xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1"，來參考結構描述。</span><span class="sxs-lookup"><span data-stu-id="93543-115">The <`ProductModel`> top-level element in the result refers to the schema by using the default namespace declaration, xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1" .</span></span>  
  
 <span data-ttu-id="93543-116">結果的結構描述部份可能包含了描述多個命名空間的多個結構描述文件。</span><span class="sxs-lookup"><span data-stu-id="93543-116">The schema part of the result may contain multiple schema documents that describe multiple namespaces.</span></span> <span data-ttu-id="93543-117">至少會傳回下列兩份結構描述文件：</span><span class="sxs-lookup"><span data-stu-id="93543-117">At a minimum, the following two schema documents are returned:</span></span>  
  
-   <span data-ttu-id="93543-118">一份結構描述文件用於 **Sqltypes** 命名空間，並對其傳回基底 SQL 類型。</span><span class="sxs-lookup"><span data-stu-id="93543-118">One schema document for the **Sqltypes** namespace, and for which the base SQL types are being returned.</span></span>  
  
-   <span data-ttu-id="93543-119">另一份結構描述文件描述 FOR XML 查詢結果的外觀。</span><span class="sxs-lookup"><span data-stu-id="93543-119">Another schema document that describes the shape of the FOR XML query result.</span></span>  
  
 <span data-ttu-id="93543-120">另外，如果查詢結果中包含任何具類型的 `xml` 資料類型，則與這些具類型的 `xml` 資料類型相關聯的結構描述也會包含在內。</span><span class="sxs-lookup"><span data-stu-id="93543-120">Also, if any typed `xml` data types are included in the query result, the schemas associated with those typed `xml` data types are included.</span></span>  
  
 <span data-ttu-id="93543-121">在描述 FOR XML 結果外觀的結構描述文件中，目標命名空間包含固定部分，以及會自動遞增的數值部分。</span><span class="sxs-lookup"><span data-stu-id="93543-121">The target namespace of the schema document that describes the shape of the FOR XML result contains a fixed portion and a numeric portion that increments automatically.</span></span> <span data-ttu-id="93543-122">此命名空間的格式如下所示，其中 *n* 是正整數。</span><span class="sxs-lookup"><span data-stu-id="93543-122">The format of this namespace is shown in the following where *n* is a positive integer.</span></span> <span data-ttu-id="93543-123">例如，在上一個查詢中，urn:schemas-microsoft-com:sql:SqlRowSet1 就是目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="93543-123">For example, in the previous query, urn:schemas-microsoft-com:sql:SqlRowSet1 is the target namespace.</span></span>  
  
```  
urn:schemas-microsoft-com:sql:SqlRowSetn  
```  
  
 <span data-ttu-id="93543-124">每次執行都會導致結果中的目標命名空間發生改變，但這可能不是您想要的。</span><span class="sxs-lookup"><span data-stu-id="93543-124">The change in the target namespaces in the result that occurred from one execution to another may not be desirable.</span></span> <span data-ttu-id="93543-125">例如，如果您查詢產生的 XML，目標命名空間中的變更會要求您更新查詢。</span><span class="sxs-lookup"><span data-stu-id="93543-125">For example, if you query the resulting XML, the change in target namespace will require that you update your query.</span></span> <span data-ttu-id="93543-126">您可在 XMLSCHEMA 選項加入 FOR XML 子句時，選擇性地指定目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="93543-126">You can optionally specify a target namespace when the XMLSCHEMA option is added in the FOR XML clause.</span></span> <span data-ttu-id="93543-127">產生的 XML 將會包含您所提供的命名空間，並且維持不變，不論您執行查詢多少次都一樣。</span><span class="sxs-lookup"><span data-stu-id="93543-127">The resulting XML will include the namespace you provided and will remain the same, regardless of how many times you run the query.</span></span>  
  
```  
SELECT ProductModelID, Name  
FROM   Production.ProductModel  
WHERE ProductModelID=1  
FOR XML AUTO, XMLSCHEMA ('MyURI')  
```  
  
## <a name="entity-elements"></a><span data-ttu-id="93543-128">實體元素</span><span class="sxs-lookup"><span data-stu-id="93543-128">Entity Elements</span></span>  
 <span data-ttu-id="93543-129">若要討論針對查詢結果而產生之 XSD 結構描述結構的詳細資料，必須先說明實體元素</span><span class="sxs-lookup"><span data-stu-id="93543-129">In order to discuss the details of the XSD schema structure generated for the query result, the entity element has to first be described</span></span>  
  
 <span data-ttu-id="93543-130">由 FOR XML 查詢所傳回之 XML 資料中的實體元素，是從資料表產生的元素，而非從資料行產生。</span><span class="sxs-lookup"><span data-stu-id="93543-130">An entity element in the XML data returned by FOR XML query is an element that is generated from a table and not from a column.</span></span> <span data-ttu-id="93543-131">例如，下列 FOR XML 查詢會從 `Person` 資料庫中的 `AdventureWorks2012` 資料表傳回連絡資訊。</span><span class="sxs-lookup"><span data-stu-id="93543-131">For example, the following FOR XML query returns contact information from the `Person` table in the `AdventureWorks2012` database.</span></span>  
  
```  
SELECT BusinessEntityID, FirstName  
FROM Person.Person  
WHERE BusinessEntityID = 1  
FOR XML AUTO, ELEMENTS  
```  
  
 <span data-ttu-id="93543-132">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="93543-132">This is the result:</span></span>  
  
 `<Person>`  
  
 `<BusinessEntityID>1</BusinessEntityID>`  
  
 `<FirstName>Ken</FirstName>`  
  
 `</Person>`  
  
 <span data-ttu-id="93543-133">在此結果中，<`Person`> 是實體元素。</span><span class="sxs-lookup"><span data-stu-id="93543-133">In this result, <`Person`> is the entity element.</span></span> <span data-ttu-id="93543-134">在 XML 結果中可能有多個實體元素，每一個元素在內嵌 XSD 結構描述中都有全域宣告。</span><span class="sxs-lookup"><span data-stu-id="93543-134">There can be multiple entity elements in the XML result and each of these has a global declaration in the inline XSD schema.</span></span> <span data-ttu-id="93543-135">例如，下列查詢擷取特定訂單的銷售訂單標頭和詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="93543-135">For example, the following query retrieves sales order header and detail information for a specific order.</span></span>  
  
```  
SELECT  SalesOrderHeader.SalesOrderID, ProductID, OrderQty  
FROM    Sales.SalesOrderHeader, Sales.SalesOrderDetail  
WHERE   SalesOrderHeader.SalesOrderID = SalesOrderDetail.SalesOrderID  
AND     SalesOrderHeader.SalesOrderID=5001  
FOR XML AUTO, ELEMENTS, XMLSCHEMA  
```  
  
 <span data-ttu-id="93543-136">因為此查詢指定 ELEMENTS 指示詞，所以產生的 XML 是元素中心的。</span><span class="sxs-lookup"><span data-stu-id="93543-136">Because the query specifies the ELEMENTS directive, the resulting XML is element-centric.</span></span> <span data-ttu-id="93543-137">此查詢也指定 XMLSCHEMA 指示詞。</span><span class="sxs-lookup"><span data-stu-id="93543-137">The query also specifies the XMLSCHEMA directive.</span></span> <span data-ttu-id="93543-138">因此，會傳回內嵌 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="93543-138">Therefore, an inline XSD schema is returned.</span></span> <span data-ttu-id="93543-139">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="93543-139">This is the result:</span></span>  
  
 `<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:schema="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">`  
  
 `<xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />`  
  
 `<xsd:element name="Sales.SalesOrderHeader">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="SalesOrderID" type="sqltypes:int" />`  
  
 `<xsd:element ref="schema:Sales.SalesOrderDetail" minOccurs="0" maxOccurs="unbounded" />`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `<xsd:element name="Sales.SalesOrderDetail">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="ProductID" type="sqltypes:int" />`  
  
 `<xsd:element name="OrderQty" type="sqltypes:smallint" />`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `</xsd:schema>`  
  
 <span data-ttu-id="93543-140">請注意下列項目是從上一個查詢而來：</span><span class="sxs-lookup"><span data-stu-id="93543-140">Note the following from the previous query:</span></span>  
  
-   <span data-ttu-id="93543-141">在結果中，<`SalesOrderHeader`> 和 <`SalesOrderDetail`> 是實體元素。</span><span class="sxs-lookup"><span data-stu-id="93543-141">In the result, <`SalesOrderHeader`> and <`SalesOrderDetail`> are entity elements.</span></span> <span data-ttu-id="93543-142">因為它們都是實體元素，所以在結構描述中已有全域宣告。</span><span class="sxs-lookup"><span data-stu-id="93543-142">Because of this, they are globally declared in the schema.</span></span> <span data-ttu-id="93543-143">也就是說，此宣告會出現在 <`Schema`> 元素內的最上層。</span><span class="sxs-lookup"><span data-stu-id="93543-143">That is, the declaration appears at the top level inside the <`Schema`> element.</span></span>  
  
-   <span data-ttu-id="93543-144"><`SalesOrderID`>、<`ProductID`> 和 <`OrderQty`> 不是實體元素，因為它們對應到資料行。</span><span class="sxs-lookup"><span data-stu-id="93543-144">The <`SalesOrderID`>, <`ProductID`>, and <`OrderQty`> are not entity elements, because they map to columns.</span></span> <span data-ttu-id="93543-145">因為 ELEMENTS 指示詞的緣故，資料行的資料是以 XML 中的元素傳回。</span><span class="sxs-lookup"><span data-stu-id="93543-145">The column data is returned as elements in the XML, because of the ELEMENTS directive.</span></span> <span data-ttu-id="93543-146">這些元素對應至實體元素之複雜類型的本機元素。</span><span class="sxs-lookup"><span data-stu-id="93543-146">These are mapped to local elements of the entity element's complex type.</span></span> <span data-ttu-id="93543-147">請注意，如果未指定 ELEMENTS 指示詞，則 `SalesOrderID`、 `ProductID` 和 `OrderQty` 值會對應至相對應實體元素之複雜類型的本機屬性。</span><span class="sxs-lookup"><span data-stu-id="93543-147">Note that if the ELEMENTS directive is not specified, the `SalesOrderID`, `ProductID` and `OrderQty` values are mapped to local attributes of the corresponding entity element's complex type.</span></span>  
  
## <a name="attribute-name-clashes"></a><span data-ttu-id="93543-148">屬性名稱衝突</span><span class="sxs-lookup"><span data-stu-id="93543-148">Attribute Name Clashes</span></span>  
 <span data-ttu-id="93543-149">以下討論是以 `CustOrder` 和 `CustOrderDetail` 資料表為基礎。</span><span class="sxs-lookup"><span data-stu-id="93543-149">The following discussion is based on the `CustOrder` and `CustOrderDetail` tables.</span></span> <span data-ttu-id="93543-150">若要測試下列範例，請建立這些資料表並加入您自己的範例資料：</span><span class="sxs-lookup"><span data-stu-id="93543-150">To test the following samples, create these tables and add your own sample data:</span></span>  
  
```  
CREATE TABLE CustOrder (OrderID int primary key, CustomerID int)  
GO  
CREATE TABLE CustOrderDetail (OrderID int, ProductID int, Qty int)  
GO  
```  
  
 <span data-ttu-id="93543-151">在 FOR XML 中，有時候相同的名稱會表示不同的屬性 (Property) 或屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="93543-151">In FOR XML, the same name is sometimes used to indicate different properties, attributes.</span></span> <span data-ttu-id="93543-152">例如，下列屬性中心的 RAW 模式查詢會產生兩個屬性，其名稱都是 OrderID。</span><span class="sxs-lookup"><span data-stu-id="93543-152">For example, the following attribute-centric RAW mode query generates two attributes that have the same name, OrderID.</span></span> <span data-ttu-id="93543-153">這樣會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="93543-153">This generates an error.</span></span>  
  
```  
SELECT CustOrder.OrderID,   
       CustOrderDetail.ProductID,   
       CustOrderDetail.OrderID  
FROM   dbo.CustOrder, dbo.CustOrderDetail  
WHERE  CustOrder.OrderID = CustOrderDetail.OrderID  
FOR XML RAW, XMLSCHEMA  
```  
  
 <span data-ttu-id="93543-154">不過，因為兩個元素具有相同名稱是可接受的，所以，您可以加入 ELEMENTS 指示詞來解決此問題：</span><span class="sxs-lookup"><span data-stu-id="93543-154">However, because it is acceptable to have two elements that have the same name, you can eliminate the problem by adding the ELEMENTS directive:</span></span>  
  
```  
SELECT CustOrder.OrderID,  
       CustOrderDetail.ProductID,   
       CustOrderDetail.OrderID  
from   dbo.CustOrder, dbo.CustOrderDetail  
where  CustOrder.OrderID = CustOrderDetail.OrderID  
FOR XML RAW, XMLSCHEMA, ELEMENTS  
```  
  
 <span data-ttu-id="93543-155">以下是結果。</span><span class="sxs-lookup"><span data-stu-id="93543-155">This is the result.</span></span> <span data-ttu-id="93543-156">請注意內嵌 XSD 結構描述中，OrderID 元素定義了兩次。</span><span class="sxs-lookup"><span data-stu-id="93543-156">Note in the inline XSD schema, the OrderID element is defined two times.</span></span> <span data-ttu-id="93543-157">其中一個宣告將 minOccurs 設為 0，對應於 CustOrderDetail 資料表的 OrderID；第二個宣告對應於 `CustOrder` 資料表的 OrderID 主索引鍵資料行，其中的 minOccurs 預設為 1。</span><span class="sxs-lookup"><span data-stu-id="93543-157">One of the declarations has minOccurs set to 0, corresponding to the OrderID from the CustOrderDetail table, and the second one maps to the OrderID primary key column of the `CustOrder` table where minOccurs is 1 by default.</span></span>  
  
 `<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">`  
  
 `<xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />`  
  
 `<xsd:element name="row">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="OrderID" type="sqltypes:int" />`  
  
 `<xsd:element name="ProductID" type="sqltypes:int" minOccurs="0" />`  
  
 `<xsd:element name="OrderID" type="sqltypes:int" minOccurs="0" />`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `</xsd:schema>`  
  
## <a name="element-name-clashes"></a><span data-ttu-id="93543-158">元素名稱衝突</span><span class="sxs-lookup"><span data-stu-id="93543-158">Element Name Clashes</span></span>  
 <span data-ttu-id="93543-159">在 FOR XML 中，可以使用相同的名稱來表示兩個子元素。</span><span class="sxs-lookup"><span data-stu-id="93543-159">In FOR XML, the same name can be used to indicate two subelements.</span></span> <span data-ttu-id="93543-160">例如，下列查詢會擷取產品的 ListPrice 和 DealerPrice 值，但此查詢對這兩個資料行指定相同的別名：Price。</span><span class="sxs-lookup"><span data-stu-id="93543-160">For example, the following query retrieves ListPrice and DealerPrice values of products, but the query specifies the same alias, Price, for these two columns.</span></span> <span data-ttu-id="93543-161">因此，產生的資料列集將具有兩個相同名稱的資料行。</span><span class="sxs-lookup"><span data-stu-id="93543-161">Therefore, the resulting rowset will have two columns with same name.</span></span>  
  
### <a name="case-1-both-subelements-are-nonkey-columns-of-the-same-type-and-can-be-null"></a><span data-ttu-id="93543-162">案例 1：兩個子元素都是非索引鍵資料行且類型相同，並且可以是 NULL</span><span class="sxs-lookup"><span data-stu-id="93543-162">Case 1: Both subelements are nonkey columns of the same type and can be NULL</span></span>  
 <span data-ttu-id="93543-163">在下列查詢中，兩個子元素都是相同類型的非索引鍵之索引資料行，而且可以是 NULL。</span><span class="sxs-lookup"><span data-stu-id="93543-163">In the following query, both subelements are nonkey columns of the same type and can be NULL.</span></span>  
  
```  
DROP TABLE T  
go  
CREATE TABLE T (ProductID int primary key, ListPrice money, DealerPrice money)  
go  
INSERT INTO T values (1, 1.25, null)  
go  
  
SELECT ProductID, ListPrice Price, DealerPrice Price  
FROM   T  
for    XML RAW, ELEMENTS, XMLSCHEMA  
```  
  
 <span data-ttu-id="93543-164">這是所產生的對應 XML。</span><span class="sxs-lookup"><span data-stu-id="93543-164">This is the corresponding XML generated.</span></span> <span data-ttu-id="93543-165">以下只顯示內嵌 XSD 的一部分：</span><span class="sxs-lookup"><span data-stu-id="93543-165">Only a fraction of the inline XSD is shown:</span></span>  
  
 `...`  
  
 `<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">`  
  
 `<xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" />`  
  
 `<xsd:element name="row">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="ProductID" type="sqltypes:int" />`  
  
 `<xsd:element name="Price" type="sqltypes:money" minOccurs="0" maxOccurs="2" />`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `</xsd:schema>`  
  
 `<row xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1">`  
  
 `<ProductID>1</ProductID>`  
  
 `<Price>1.2500</Price>`  
  
 `</row>`  
  
 <span data-ttu-id="93543-166">請注意內嵌 XSD 結構描述中的下列各項：</span><span class="sxs-lookup"><span data-stu-id="93543-166">Note the following in the inline XSD schema:</span></span>  
  
-   <span data-ttu-id="93543-167">ListPrice 和 DealerPrice 都屬於相同類型 `money`，而且在資料表中都可以是 NULL。</span><span class="sxs-lookup"><span data-stu-id="93543-167">Both the ListPrice and DealerPrice are of the same type, `money`, and both can be NULL in the table.</span></span> <span data-ttu-id="93543-168">因此，由於它們可能不會在產生的 XML 中傳回，所以在 <`row`> 元素 (其 minOccurs=0 且 maxOccurs=2) 的複雜類型宣告中，只有一個 <`Price`> 子元素。</span><span class="sxs-lookup"><span data-stu-id="93543-168">Therefore, because they may not be returned in the resulting XML, there is only one <`Price`> child element in the complex type declaration of the <`row`> element that has minOccurs=0 and maxOccurs=2.</span></span>  
  
-   <span data-ttu-id="93543-169">結果，因為 `DealerPrice` 值在資料表中是 NULL，所以只有 `ListPrice` 會做為 <`Price`> 元素傳回。</span><span class="sxs-lookup"><span data-stu-id="93543-169">In the result, because the `DealerPrice` value is NULL in the table, only `ListPrice` is returned as a <`Price`> element.</span></span> <span data-ttu-id="93543-170">如果將 `XSINIL` 參數加入 ELEMENTS 指示詞，您會收到兩個元素，它們將對應至 DealerPrice 的 <`Price`> 元素的 `xsi:nil` 值設定為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="93543-170">If you add the `XSINIL` parameter to the ELEMENTS directive, you will receive both of the elements that have the `xsi:nil` value set to TRUE for the<`Price`> element that corresponds to DealerPrice.</span></span> <span data-ttu-id="93543-171">您也會在內嵌 XSD 結構描述的 <`row`> 複雜類型定義中，接收到兩個 <`Price`> 子元素，這兩個子元素的 `nillable` 屬性都設為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="93543-171">You will also receive two <`Price`> child elements in the <`row`> complex type definition in the inline XSD schema with the `nillable` attribute set to TRUE for both.</span></span> <span data-ttu-id="93543-172">以下片段是部分結果：</span><span class="sxs-lookup"><span data-stu-id="93543-172">This fragment is a partial result:</span></span>  
  
 `...`  
  
 `<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">`  
  
 `<xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" />`  
  
 `<xsd:element name="row">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="ProductID" type="sqltypes:int" nillable="1" />`  
  
 `<xsd:element name="Price" type="sqltypes:money" nillable="1" />`  
  
 `<xsd:element name="Price" type="sqltypes:money" nillable="1" />`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `</xsd:schema>`  
  
 `<row xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">`  
  
 `<ProductID>1</ProductID>`  
  
 `<Price>1.2500</Price>`  
  
 `<Price xsi:nil="true" />`  
  
 `</row>`  
  
### <a name="case-2-one-key-and-one-nonkey-column-of-the-same-type"></a><span data-ttu-id="93543-173">案例 2：一個索引鍵資料行和一個非索引鍵資料行且類型相同</span><span class="sxs-lookup"><span data-stu-id="93543-173">Case 2: One key and one nonkey column of the same type</span></span>  
 <span data-ttu-id="93543-174">下列查詢說明類型相同的索引鍵資料行和非索引鍵之索引資料行。</span><span class="sxs-lookup"><span data-stu-id="93543-174">The following query illustrates one key and one nonkey column of the same type.</span></span>  
  
```  
CREATE TABLE T (Col1 int primary key, Col2 int, Col3 nvarchar(20))  
go  
INSERT INTO T VALUES (1, 1, 'test')  
go   
```  
  
 <span data-ttu-id="93543-175">下列針對資料表 **T** 的查詢，為 Col1 和 Col2 指定了相同別名，其中 Col1 是不能為 Null 的主索引鍵，而 Col2 則可以是 Null。</span><span class="sxs-lookup"><span data-stu-id="93543-175">The following query against table **T** specifies the same alias for Col1 and Col2, where Col1 is a primary key and cannot be null, and Col2 can be null.</span></span> <span data-ttu-id="93543-176">這會產生兩個同層級元素，兩者都是 <`row`> 元素的子系。</span><span class="sxs-lookup"><span data-stu-id="93543-176">This generates two sibling elements that are children of the <`row`> element.</span></span>  
  
```  
SELECT Col1 as Col, Col2 as Col, Col3  
FROM T  
FOR XML RAW, ELEMENTS, XMLSCHEMA  
```  
  
 <span data-ttu-id="93543-177">以下是結果。</span><span class="sxs-lookup"><span data-stu-id="93543-177">This is the result.</span></span> <span data-ttu-id="93543-178">以下只顯示內嵌 XSD 結構描述的一部份：</span><span class="sxs-lookup"><span data-stu-id="93543-178">Only a fragment of the inline XSD schema is shown.</span></span>  
  
 `...`  
  
 `<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">`  
  
 `<xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" />`  
  
 `<xsd:element name="row">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="Col" type="sqltypes:int" />`  
  
 `<xsd:element name="Col" type="sqltypes:int" minOccurs="0" />`  
  
 `<xsd:element name="Col3" minOccurs="0">`  
  
 `<xsd:simpleType>`  
  
 `<xsd:restriction base="sqltypes:nvarchar"`  
  
 `sqltypes:localeId="1033"`  
  
 `sqltypes:sqlCompareOptions="IgnoreCase`  
  
 `IgnoreKanaType IgnoreWidth"`  
  
 `sqltypes:sqlSortId="52">`  
  
 `<xsd:maxLength value="20" />`  
  
 `</xsd:restriction>`  
  
 `</xsd:simpleType>`  
  
 `</xsd:element>`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `</xsd:schema>`  
  
 `<row xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1">`  
  
 `<Col>1</Col>`  
  
 `<Col>1</Col>`  
  
 `<Col3>test</Col3>`  
  
 `</row>`  
  
 <span data-ttu-id="93543-179">請注意，在內嵌 XSD 結構描述中，對應於 Col2 的 <`Col`> 元素，其 minOccurs 是設為 0。</span><span class="sxs-lookup"><span data-stu-id="93543-179">Note in the inline XSD schema that the <`Col`> element corresponding to the Col2 has minOccurs set to 0.</span></span>  
  
### <a name="case-3-both-elements-of-different-types-and-corresponding-columns-can-be-null"></a><span data-ttu-id="93543-180">案例 3：兩個不同類型的元素，且對應的資料行可以是 NULL</span><span class="sxs-lookup"><span data-stu-id="93543-180">Case 3: Both elements of different types and corresponding columns can be NULL</span></span>  
 <span data-ttu-id="93543-181">下列查詢是針對案例 2 所顯示的範例資料表而指定：</span><span class="sxs-lookup"><span data-stu-id="93543-181">The following query is specified against the sample table shown in case 2:</span></span>  
  
```  
SELECT Col1, Col2 as Col, Col3 as Col  
FROM T  
FOR XML RAW, ELEMENTS, XMLSCHEMA  
```  
  
 <span data-ttu-id="93543-182">下列查詢中，Col2 和 Col3 使用相同別名。</span><span class="sxs-lookup"><span data-stu-id="93543-182">In the following query, Col2 and Col3 are given the same aliases.</span></span> <span data-ttu-id="93543-183">這會產生兩個具有相同名稱的同層級元素，且在結果中這兩者都是 <`raw`> 元素的子系。</span><span class="sxs-lookup"><span data-stu-id="93543-183">This generates two sibling elements that have the same name and that are both children of the <`raw`> element in the result.</span></span> <span data-ttu-id="93543-184">這兩個資料行屬於不同類型，而且兩者都可以是 NULL。</span><span class="sxs-lookup"><span data-stu-id="93543-184">Both of these columns are of different types and both can be NULL.</span></span> <span data-ttu-id="93543-185">以下是結果。</span><span class="sxs-lookup"><span data-stu-id="93543-185">This is the result.</span></span> <span data-ttu-id="93543-186">只顯示一部份的內嵌 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="93543-186">Only partial inline XSD schema is shown.</span></span>  
  
 `...`  
  
 `<xsd:schema targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet1" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" elementFormDefault="qualified">`  
  
 `<xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" />`  
  
 `<xsd:simpleType name="Col1">`  
  
 `<xsd:restriction base="sqltypes:int" />`  
  
 `</xsd:simpleType>`  
  
 `<xsd:simpleType name="Col2">`  
  
 `<xsd:restriction base="sqltypes:nvarchar" sqltypes:localeId="1033"`  
  
 `sqltypes:sqlCompareOptions="IgnoreCase`  
  
 `IgnoreKanaType IgnoreWidth" sqltypes:sqlSortId="52">`  
  
 `<xsd:maxLength value="20" />`  
  
 `</xsd:restriction>`  
  
 `</xsd:simpleType>`  
  
 `<xsd:element name="row">`  
  
 `<xsd:complexType>`  
  
 `<xsd:sequence>`  
  
 `<xsd:element name="Col1" type="sqltypes:int" />`  
  
 `<xsd:element name="Col" minOccurs="0" maxOccurs="2" type="xsd:anySimpleType" />`  
  
 `</xsd:sequence>`  
  
 `</xsd:complexType>`  
  
 `</xsd:element>`  
  
 `</xsd:schema>`  
  
 `<row xmlns="urn:schemas-microsoft-com:sql:SqlRowSet1">`  
  
 `<Col1>1</Col1>`  
  
 `<Col xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"`  
  
 `xsi:type="Col1">1</Col>`  
  
 `<Col xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"`  
  
 `xsi:type="Col2">test</Col>`  
  
 `</row>`  
  
 <span data-ttu-id="93543-187">請注意內嵌 XSD 結構描述中的下列各項：</span><span class="sxs-lookup"><span data-stu-id="93543-187">Note the following in the inline XSD schema:</span></span>  
  
-   <span data-ttu-id="93543-188">因為 Col2 和 Col3 可以是 NULL，所以 <`Col`> 元素宣告將 minOccurs 指定為 0，將 maxOccurs 指定為 2。</span><span class="sxs-lookup"><span data-stu-id="93543-188">Because both Col2 and Col3 can be NULL, the <`Col`> element declaration specifies the minOccurs as 0 and maxOccurs as 2.</span></span>  
  
-   <span data-ttu-id="93543-189">因為這兩個 <`Col`> 元素是同層級，所以在結構描述中有一個元素宣告。</span><span class="sxs-lookup"><span data-stu-id="93543-189">Because both the <`Col`> elements are siblings, there is one element declaration in the schema.</span></span> <span data-ttu-id="93543-190">同時，因為兩元素也都是不同類型 (雖然都是簡單類型)，所以結構描述中的元素類型是 `xsd:anySimpleType`。</span><span class="sxs-lookup"><span data-stu-id="93543-190">Also, because both of the elements are also of different types, though both are simple types, the type of the element in the schema is `xsd:anySimpleType`.</span></span> <span data-ttu-id="93543-191">在結果中，每一個執行個體類型是由 `xsi:type` 屬性加以識別。</span><span class="sxs-lookup"><span data-stu-id="93543-191">In the result, each instance type is identified by the `xsi:type` attribute.</span></span>  
  
-   <span data-ttu-id="93543-192">在結果中，<`Col`> 元素的每一個執行個體是使用 `xsi:type` 屬性來參考其執行個體類型。</span><span class="sxs-lookup"><span data-stu-id="93543-192">In the result, every instance of the <`Col`> element refers to its instance type by using the `xsi:type` attribute.</span></span>  
  
  
