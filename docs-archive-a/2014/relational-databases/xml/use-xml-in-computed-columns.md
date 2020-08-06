---
title: 在計算資料行中使用 XML | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- computed columns, XML
- XML [SQL Server], computed columns
ms.assetid: 1313b889-69b4-4018-9868-0496dd83bf44
author: rothja
ms.author: jroth
ms.openlocfilehash: 33a7549823dc3e4a23cecfa97d7345a6421cb1b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686849"
---
# <a name="use-xml-in-computed-columns"></a><span data-ttu-id="488ba-102">使用計算資料行中的 XML</span><span class="sxs-lookup"><span data-stu-id="488ba-102">Use XML in Computed Columns</span></span>
  <span data-ttu-id="488ba-103">XML 執行個體可依計算資料行的來源或依計算資料行的類型顯示。</span><span class="sxs-lookup"><span data-stu-id="488ba-103">XML instances can appear as a source for a computed column, or as a type of computed column.</span></span> <span data-ttu-id="488ba-104">本主題的範例將示範如何搭配計算資料行使用 XML。</span><span class="sxs-lookup"><span data-stu-id="488ba-104">The examples in this topic show how to use XML with computed columns.</span></span>  
  
## <a name="creating-computed-columns-from-xml-columns"></a><span data-ttu-id="488ba-105">從 XML 資料行建立計算資料行</span><span class="sxs-lookup"><span data-stu-id="488ba-105">Creating Computed Columns from XML Columns</span></span>  
 <span data-ttu-id="488ba-106">在下列 `CREATE TABLE` 陳述式中，從 `xml` 計算出`col2`類型資料行 ( `col1`)：</span><span class="sxs-lookup"><span data-stu-id="488ba-106">In the following `CREATE TABLE` statement, an `xml` type column (`col2`) is computed from `col1`:</span></span>  
  
```  
CREATE TABLE T(col1 varchar(max), col2 AS CAST(col1 AS xml) )    
```  
  
 <span data-ttu-id="488ba-107">`xml` 資料類型也可依建立計算資料行的來源顯示，如下列 `CREATE TABLE` 陳述式所示：</span><span class="sxs-lookup"><span data-stu-id="488ba-107">The `xml` data type can also appear as a source in creating a computed column, as shown in the following `CREATE TABLE` statement:</span></span>  
  
```  
CREATE TABLE T (col1 xml, col2 as cast(col1 as varchar(1000) ))   
```  
  
 <span data-ttu-id="488ba-108">您可以從 `xml` 類型的資料行擷取值以建立計算資料行，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="488ba-108">You can create a computed column by extracting a value from an `xml` type column as shown in the following example.</span></span> <span data-ttu-id="488ba-109">因為 `xml` 資料類型方法無法直接用來建立計算資料行，本範例先定義一個函數 (`my_udf`)，以傳回 XML 執行個體的值。</span><span class="sxs-lookup"><span data-stu-id="488ba-109">Because the `xml` data type methods cannot be used directly in creating computed columns, the example first defines a function (`my_udf`) that returns a value from an XML instance.</span></span> <span data-ttu-id="488ba-110">該函數會包裝 `value()` 類型的 `xml` 方法。</span><span class="sxs-lookup"><span data-stu-id="488ba-110">The function wraps the `value()` method of the `xml` type.</span></span> <span data-ttu-id="488ba-111">接著會在計算資料行的 `CREATE TABLE` 陳述式中指定函數名稱。</span><span class="sxs-lookup"><span data-stu-id="488ba-111">The function name is then specified in the `CREATE TABLE` statement for the computed column.</span></span>  
  
```  
CREATE FUNCTION my_udf(@var xml) returns int  
AS BEGIN   
RETURN @var.value('(/ProductDescription/@ProductModelID)[1]' , 'int')  
END  
GO  
-- Use the function in CREATE TABLE.  
CREATE TABLE T (col1 xml, col2 as dbo.my_udf(col1) )  
GO  
-- Try adding a row.   
INSERT INTO T values('<ProductDescription ProductModelID="1" />')  
GO  
-- Verify results.  
SELECT col2, col1  
FROM T  
  
```  
  
 <span data-ttu-id="488ba-112">就如同上述範例，下列範例定義一個函數，以傳回計算資料行的 `xml` 類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="488ba-112">As in the previous example, the following example defines a function to return an `xml` type instance for a computed column.</span></span> <span data-ttu-id="488ba-113">在函數中， `query()` 資料類型的 `xml` 方法會擷取 `xml` 類型參數中的值。</span><span class="sxs-lookup"><span data-stu-id="488ba-113">Inside the function, the `query()` method of the `xml` data type retrieves a value from an `xml` type parameter.</span></span>  
  
```  
CREATE FUNCTION my_udf(@var xml)   
  RETURNS xml AS   
BEGIN   
   RETURN @var.query('ProductDescription/Features')  
END  
```  
  
 <span data-ttu-id="488ba-114">在下列 `CREATE TABLE` 陳述式中， `Col2` 是一個計算資料行，它使用了該函數所傳回的 XML 資料 (`<Features>` 元素)：</span><span class="sxs-lookup"><span data-stu-id="488ba-114">In the following `CREATE TABLE` statement, `Col2` is a computed column that uses the XML data (`<Features>` element) that is returned by the function:</span></span>  
  
```  
CREATE TABLE T (Col1 xml, Col2 as dbo.my_udf(Col1) )  
-- Insert a row in table T.  
INSERT INTO T VALUES('  
<ProductDescription ProductModelID="1" >  
  <Features>  
    <Feature1>description</Feature1>  
    <Feature2>description</Feature2>  
  </Features>  
</ProductDescription>')  
-- Verify the results.  
SELECT *  
FROM T  
```  
  
### <a name="in-this-section"></a><span data-ttu-id="488ba-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="488ba-115">In This Section</span></span>  
  
|<span data-ttu-id="488ba-116">主題</span><span class="sxs-lookup"><span data-stu-id="488ba-116">Topic</span></span>|<span data-ttu-id="488ba-117">描述</span><span class="sxs-lookup"><span data-stu-id="488ba-117">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="488ba-118">使用計算資料行升級常用的 XML 值</span><span class="sxs-lookup"><span data-stu-id="488ba-118">Promote Frequently Used XML Values with Computed Columns</span></span>](promote-frequently-used-xml-values-with-computed-columns.md)|<span data-ttu-id="488ba-119">描述如何搭配計算資料行和屬性資料表使用屬性升級。</span><span class="sxs-lookup"><span data-stu-id="488ba-119">Describes how to use property promotion with computed columns and property tables.</span></span>|  
  
  
