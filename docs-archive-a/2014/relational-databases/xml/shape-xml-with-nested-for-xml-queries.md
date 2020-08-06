---
title: 使用巢狀 FOR XML 查詢組成 XML | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML query
- queries [XML in SQL Server], nested FOR XML
- XML [SQL Server], FOR XML queries
ms.assetid: 8dc42c05-16e8-4b7b-a5d3-550b55acae26
author: rothja
ms.author: jroth
ms.openlocfilehash: 738b5b3ec67dada90c851d284ccc8b3009a51aa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597678"
---
# <a name="shape-xml-with-nested-for-xml-queries"></a><span data-ttu-id="47105-102">使用巢狀 FOR XML 查詢組成 XML</span><span class="sxs-lookup"><span data-stu-id="47105-102">Shape XML with Nested FOR XML Queries</span></span>
  <span data-ttu-id="47105-103">以下範例會查詢 `Production.Product` 資料表，以擷取特定產品的 `ListPrice` 及 `StandardCost` 值。</span><span class="sxs-lookup"><span data-stu-id="47105-103">The following example queries the `Production.Product` table to retrieve the `ListPrice` and `StandardCost` values of a specific product.</span></span> <span data-ttu-id="47105-104">兩個價格都會以 <`Price`> 元素傳回，而且每個 <`Price`> 元素都有一個 `PriceType` 屬性，使查詢值得關注。</span><span class="sxs-lookup"><span data-stu-id="47105-104">To make the query interesting, both prices are returned in a <`Price`> element, and each <`Price`> element has a `PriceType` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47105-105">範例</span><span class="sxs-lookup"><span data-stu-id="47105-105">Example</span></span>  
 <span data-ttu-id="47105-106">以下是預期的 XML 外觀：</span><span class="sxs-lookup"><span data-stu-id="47105-106">This is the expected shape of the XML:</span></span>  
  
```  
<xsd:schema xmlns:schema="urn:schemas-microsoft-com:sql:SqlRowSet2" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="https://schemas.microsoft.com/sqlserver/2004/sqltypes" targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet2" elementFormDefault="qualified">  
  <xsd:import namespace="https://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="https://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />  
  <xsd:element name="Production.Product" type="xsd:anyType" />  
</xsd:schema>  
<Production.Product xmlns="urn:schemas-microsoft-com:sql:SqlRowSet2" ProductID="520">  
  <Price xmlns="" PriceType="ListPrice">133.34</Price>  
  <Price xmlns="" PriceType="StandardCost">98.77</Price>  
</Production.Product>  
```  
  
 <span data-ttu-id="47105-107">以下是巢狀 FOR XML 查詢：</span><span class="sxs-lookup"><span data-stu-id="47105-107">This is the nested FOR XML query:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Product.ProductID,   
          (SELECT 'ListPrice' as PriceType,   
                   CAST(CAST(ListPrice as NVARCHAR(40)) as XML)   
           FROM    Production.Product Price   
           WHERE   Price.ProductID=Product.ProductID   
           FOR XML AUTO, TYPE),  
          (SELECT  'StandardCost' as PriceType,   
                   CAST(CAST(StandardCost as NVARCHAR(40)) as XML)   
           FROM    Production.Product Price   
           WHERE   Price.ProductID=Product.ProductID   
           FOR XML AUTO, TYPE)  
FROM Production.Product  
WHERE ProductID=520  
for XML AUTO, TYPE, XMLSCHEMA  
```  
  
 <span data-ttu-id="47105-108">請注意下列項目是從上一個查詢而來：</span><span class="sxs-lookup"><span data-stu-id="47105-108">Note the following from the previous query:</span></span>  
  
-   <span data-ttu-id="47105-109">外部 SELECT 陳述式會建構擁有 **ProductID** 屬性的 <`Product`> 元素，以及兩個 <`Price`> 子元素。</span><span class="sxs-lookup"><span data-stu-id="47105-109">The outer SELECT statement constructs the <`Product`> element that has a **ProductID** attribute and two <`Price`> child elements.</span></span>  
  
-   <span data-ttu-id="47105-110">兩個內部 SELECT 陳述式會建構兩個 <`Price`> 元素，每個都具有一個 **PriceType** 屬性與會傳回產品價格的 XML。</span><span class="sxs-lookup"><span data-stu-id="47105-110">The two inner SELECT statements construct two <`Price`> elements, each with a **PriceType** attribute and XML that returns the product price.</span></span>  
  
-   <span data-ttu-id="47105-111">外部 SELECT 陳述式中的 XMLSCHEMA 指示詞會產生內嵌的 XSD 結構描述，描述產生之 XML 的外觀。</span><span class="sxs-lookup"><span data-stu-id="47105-111">The XMLSCHEMA directive in the outer SELECT statement generates the inline XSD schema that describes the shape of the resulting XML.</span></span>  
  
 <span data-ttu-id="47105-112">您可以撰寫 FOR XML 查詢，然後對結果撰寫 XQuery 以重新安排 XML 的外觀，使查詢值得關注，如以下查詢所述：</span><span class="sxs-lookup"><span data-stu-id="47105-112">To make the query interesting, you can write the FOR XML query and then write an XQuery against the result to reshape the XML, as shown in the following query:</span></span>  
  
```  
SELECT ProductID,   
 ( SELECT p2.ListPrice, p2.StandardCost  
   FROM Production.Product p2   
   WHERE Product.ProductID = p2.ProductID  
   FOR XML AUTO, ELEMENTS XSINIL, type ).query('  
                                   for $p in /p2/*  
                                   return   
                                    <Price PriceType = "{local-name($p)}">  
                                     { data($p) }  
                                    </Price>  
                                  ')  
FROM Production.Product  
WHERE ProductID = 520  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="47105-113">先前的範例使用 `query()` 資料類型的 `xml` 方法，以查詢內部 FOR XML 查詢傳回的 XML，並建構預期的結果。</span><span class="sxs-lookup"><span data-stu-id="47105-113">The previous example uses the `query()` method of the `xml` data type to query the XML returned by the inner FOR XML query and construct the expected result.</span></span>  
  
 <span data-ttu-id="47105-114">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="47105-114">This is the result:</span></span>  
  
```  
<Production.Product ProductID="520">  
  <Price PriceType="ListPrice">133.3400</Price>  
  <Price PriceType="StandardCost">98.7700</Price>  
</Production.Product>  
```  
  
## <a name="see-also"></a><span data-ttu-id="47105-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47105-115">See Also</span></span>  
 [<span data-ttu-id="47105-116">使用巢狀 FOR XML 查詢</span><span class="sxs-lookup"><span data-stu-id="47105-116">Use Nested FOR XML Queries</span></span>](use-nested-for-xml-queries.md)  
  
  
