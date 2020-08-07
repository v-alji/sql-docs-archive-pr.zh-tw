---
title: 範例：指定 XMLTEXT 指示詞 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XMLTEXT directive
ms.assetid: e78008ec-51e8-4fd1-b86f-1058a781de17
author: rothja
ms.author: jroth
ms.openlocfilehash: d14299ad3e989c6600434b857a650fbbddd7a590
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599388"
---
# <a name="example-specifying-the-xmltext-directive"></a><span data-ttu-id="867ac-102">範例：指定 XMLTEXT 指示詞</span><span class="sxs-lookup"><span data-stu-id="867ac-102">Example: Specifying the XMLTEXT Directive</span></span>
  <span data-ttu-id="867ac-103">此範例說明如何在使用 EXPLICIT 模式的 `SELECT` 陳述式中，使用 `XMLTEXT` 指示詞將溢位資料行中的資料定址。</span><span class="sxs-lookup"><span data-stu-id="867ac-103">This example illustrates how data in the overflow column is addressed by using the `XMLTEXT` directive in a `SELECT` statement using EXPLICIT mode.</span></span>  
  
 <span data-ttu-id="867ac-104">假設有 `Person` 資料表。</span><span class="sxs-lookup"><span data-stu-id="867ac-104">Consider the `Person` table.</span></span> <span data-ttu-id="867ac-105">此資料表有一個 `Overflow` 資料行，可用來儲存 XML 文件的未消耗部分。</span><span class="sxs-lookup"><span data-stu-id="867ac-105">This table has an `Overflow` column that stores the unconsumed part of the XML document.</span></span>  
  
```  
USE tempdb;  
GO  
CREATE TABLE Person(PersonID varchar(5), PersonName varchar(20), Overflow nvarchar(200));  
GO  
INSERT INTO Person VALUES   
    ('P1','Joe',N'<SomeTag attr1="data">content</SomeTag>')  
   ,('P2','Joe',N'<SomeTag attr2="data"/>')  
   ,('P3','Joe',N'<SomeTag attr3="data" PersonID="P">content</SomeTag>');  
```  
  
 <span data-ttu-id="867ac-106">此查詢從 `Person` 資料表擷取資料行。</span><span class="sxs-lookup"><span data-stu-id="867ac-106">This query retrieves columns from the `Person` table.</span></span> <span data-ttu-id="867ac-107">對於 `Overflow` 資料行，並未指定 *AttributeName*，但「指示詞」會將 `XMLTEXT` 設為提供通用資料表資料行名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="867ac-107">For the `Overflow` column, *AttributeName* is not specified, but *directive* is set to `XMLTEXT` as part of providing a universal table column name.</span></span>  
  
```  
SELECT 1 as Tag, NULL as parent,  
       PersonID as [Parent!1!PersonID],  
       PersonName as [Parent!1!PersonName],  
       Overflow as [Parent!1!!XMLTEST] -- No AttributeName; XMLTEXT directive  
FROM Person  
FOR XML EXPLICIT;  
```  
  
 <span data-ttu-id="867ac-108">在產生的 XML 文件中：</span><span class="sxs-lookup"><span data-stu-id="867ac-108">In the resulting XML document:</span></span>  
  
-   <span data-ttu-id="867ac-109">因為 `Overflow` 資料行未指定 *AttributeName*，但指定 `xmltext` 指示詞，所以 <`overflow`> 元素中的屬性會附加到封閉式 <`Parent`> 元素的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="867ac-109">Because *AttributeName* is not specified for the `Overflow` column and the `xmltext` directive is specified, the attributes in the <`overflow`> element are appended to the attribute list of the enclosing <`Parent`> element.</span></span>  
  
-   <span data-ttu-id="867ac-110">因為 <`xmltext`> 元素中的 `PersonID` 屬性與在相同元素層級上擷取的 `PersonID` 屬性衝突，所以即使 `PersonID` 為 NULL，還是會忽略 <`xmltext`> 元素中的屬性。</span><span class="sxs-lookup"><span data-stu-id="867ac-110">Because the `PersonID`attribute in the <`xmltext`> element conflicts with the `PersonID` attribute retrieved on the same element level, the attribute in the <`xmltext`> element is ignored, even if `PersonID` is NULL.</span></span> <span data-ttu-id="867ac-111">一般而言，屬性會覆寫溢位中相同名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="867ac-111">Generally, an attribute overrides an attribute of the same name in the overflow.</span></span>  
  
 <span data-ttu-id="867ac-112">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="867ac-112">This is the result:</span></span>  
  
 `<Parent PersonID="P1" PersonName="Joe" attr1="data">content</Parent>`  
  
 `<Parent PersonID="P2" PersonName="Joe" attr2="data"></Parent>`  
  
 `<Parent PersonID="P3" PersonName="Joe" attr3="data">content</Parent>`  
  
 <span data-ttu-id="867ac-113">如果溢位資料有子元素而且指定相同的查詢，則 `Overflow` 資料行中的子元素將會新增為封閉式 <`Parent`> 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="867ac-113">If the overflow data has subelements and the same query is specified, the subelements in the `Overflow` column are added as the subelements of the enclosing <`Parent`> element.</span></span>  
  
 <span data-ttu-id="867ac-114">例如，變更 `Person` 資料表中的資料，讓 `Overflow` 資料行現在擁有子元素。</span><span class="sxs-lookup"><span data-stu-id="867ac-114">For example, change the data in the `Person` table so that the `Overflow` column now has subelements.</span></span>  
  
```  
USE tempdb;  
GO  
TRUNCATE TABLE Person;  
GO  
INSERT INTO Person VALUES   
    ('P1','Joe',N'<SomeTag attr1="data">content</SomeTag>')  
   ,('P2','Joe',N'<SomeTag attr2="data"/>')  
    ,('P3','Joe',N'<SomeTag attr3="data" PersonID="P"><name>PersonName</name></SomeTag>');  
```  
  
 <span data-ttu-id="867ac-115">如果執行相同的查詢，則 <`xmltext`> 元素中的子元素將會新增為封閉式 <`Parent`> 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="867ac-115">If the same query is executed, the subelements in the <`xmltext`> element are added as subelements of the enclosing <`Parent`> element:</span></span>  
  
```  
SELECT 1 as Tag, NULL as parent,  
       PersonID as [Parent!1!PersonID],  
       PersonName as [Parent!1!PersonName],  
       Overflow as [Parent!1!!XMLTEXT] -- no AttributeName, XMLTEXT directive  
FROM Person  
FOR XML EXPLICIT;  
```  
  
 <span data-ttu-id="867ac-116">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="867ac-116">This is the result:</span></span>  
  
 `<Parent PersonID="P1" PersonName="Joe" attr1="data">content</Parent>`  
  
 `<Parent PersonID="P2" PersonName="Joe" attr2="data"></Parent>`  
  
 `<Parent PersonID="P3" PersonName="Joe" attr3="data">`  
  
 `<name>PersonName</name>`  
  
 `</Parent>`  
  
 <span data-ttu-id="867ac-117">如果以 `xmltext` 指示詞指定 *AttributeName*，則 <`overflow`> 元素的屬性將會新增為封閉式 <`Parent`> 元素的子元素屬性。</span><span class="sxs-lookup"><span data-stu-id="867ac-117">If *AttributeName* is specified with the `xmltext` directive, the attributes of the <`overflow`> element are added as attributes of the subelements of the enclosing <`Parent`> element.</span></span> <span data-ttu-id="867ac-118">為*AttributeName*指定的名稱會成為子項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="867ac-118">The name specified for *AttributeName* becomes the name of the subelement.</span></span>  
  
 <span data-ttu-id="867ac-119">在此查詢中， *AttributeName*（<`overflow`>）會與指示詞一起指定 `xmltext` ：</span><span class="sxs-lookup"><span data-stu-id="867ac-119">In this query, *AttributeName*, <`overflow`>, is specified together with the `xmltext` directive:</span></span>  
  
```  
SELECT 1 as Tag, NULL as parent,  
       PersonID as [Parent!1!PersonID],  
       PersonName as [Parent!1!PersonName],  
       Overflow as [Parent!1!overflow!XMLTEXT] -- Overflow is AttributeName  
                      -- XMLTEXT is a directive  
FROM Person  
FOR XML EXPLICIT  
```  
  
 <span data-ttu-id="867ac-120">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="867ac-120">This is the result:</span></span>  
  
 `<Parent PersonID="P1" PersonName="Joe">`  
  
 `<overflow attr1="data">content</overflow>`  
  
 `</Parent>`  
  
 `<Parent PersonID="P2" PersonName="Joe">`  
  
 `<overflow attr2="data" />`  
  
 `</Parent>`  
  
 `<Parent PersonID="P3" PersonName="Joe">`  
  
 `<overflow attr3="data" PersonID="P">`  
  
 `<name>PersonName</name>`  
  
 `</overflow>`  
  
 `</Parent>`  
  
 <span data-ttu-id="867ac-121">在此查詢元素中， *屬性指定為* directive `PersonName` 。</span><span class="sxs-lookup"><span data-stu-id="867ac-121">In this query element, *directive* is specified for `PersonName` attribute.</span></span> <span data-ttu-id="867ac-122">`PersonName` 的這個結果將會新增為封閉式 <`Parent`> 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="867ac-122">This results in `PersonName` being added as a subelement of the enclosing <`Parent`> element.</span></span> <span data-ttu-id="867ac-123"><`xmltext`> 的屬性仍然會附加到封閉式 <`Parent`> 元素。</span><span class="sxs-lookup"><span data-stu-id="867ac-123">The attributes of the <`xmltext`> are still appended to the enclosing <`Parent`> element.</span></span> <span data-ttu-id="867ac-124"><`overflow`> 元素的內容 (子元素) 將會附加到封閉式 <`Parent`> 元素的其他子元素前面。</span><span class="sxs-lookup"><span data-stu-id="867ac-124">The contents of the <`overflow`> element, subelements, are prepended to the other subelements of the enclosing <`Parent`> elements.</span></span>  
  
```  
SELECT 1      AS Tag, NULL as parent,  
       PersonID   AS [Parent!1!PersonID],  
       PersonName AS [Parent!1!PersonName!element], -- element directive  
       Overflow   AS [Parent!1!!XMLTEXT]  
FROM Person  
FOR XML EXPLICIT;  
```  
  
 <span data-ttu-id="867ac-125">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="867ac-125">This is the result:</span></span>  
  
 `<Parent PersonID="P1" attr1="data">content<PersonName>Joe</PersonName>`  
  
 `</Parent>`  
  
 `<Parent PersonID="P2" attr2="data">`  
  
 `<PersonName>Joe</PersonName>`  
  
 `</Parent>`  
  
 `<Parent PersonID="P3" attr3="data">`  
  
 `<name>PersonName</name>`  
  
 `<PersonName>Joe</PersonName>`  
  
 `</Parent>`  
  
 <span data-ttu-id="867ac-126">如果 `XMLTEXT` 資料行資料包含根元素的屬性，這些屬性不會顯示於 XML 資料結構描述中，而且 MSXML 剖析器並不會驗證產生的 XML 文件片段。</span><span class="sxs-lookup"><span data-stu-id="867ac-126">If the `XMLTEXT` column data contains attributes on the root element, these attributes are not shown in the XML data schema and the MSXML parser does not validate the resulting XML document fragment.</span></span> <span data-ttu-id="867ac-127">例如：</span><span class="sxs-lookup"><span data-stu-id="867ac-127">For example:</span></span>  
  
```  
SELECT 1 AS Tag,  
       0 ASParent,  
       N'<overflow a="1"/>' AS 'overflow!1!!xmltext'  
FOR XML EXPLICIT, xmldata;  
```  
  
 <span data-ttu-id="867ac-128">以下是結果。</span><span class="sxs-lookup"><span data-stu-id="867ac-128">This is the result.</span></span> <span data-ttu-id="867ac-129">請注意，在傳回的結構描述中，結構描述已經遺漏溢位屬性 `a` ：</span><span class="sxs-lookup"><span data-stu-id="867ac-129">Note that in the returned schema, the overflow attribute `a` is missing from the schema:</span></span>  
  
 `<Schema name="Schema2"`  
  
 `xmlns="urn:schemas-microsoft-com:xml-data"`  
  
 `xmlns:dt="urn:schemas-microsoft-com:datatypes">`  
  
 `<ElementType name="overflow" content="mixed" model="open">`  
  
 `</ElementType>`  
  
 `</Schema>`  
  
 `<overflow xmlns="x-schema:#Schema2" a="1">`  
  
 `</overflow>`  
  
## <a name="see-also"></a><span data-ttu-id="867ac-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="867ac-130">See Also</span></span>  
 [<span data-ttu-id="867ac-131">搭配 FOR XML 使用 EXPLICIT 模式</span><span class="sxs-lookup"><span data-stu-id="867ac-131">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
