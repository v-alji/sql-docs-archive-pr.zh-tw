---
title: 具有 XPath 節點測試名稱的資料行 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
- XPath node test
ms.assetid: b48adccd-3b6b-486a-b326-20f57170186f
author: rothja
ms.author: jroth
ms.openlocfilehash: 6555815d97308bed6e70d9fedb9858fc3abe7685
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688662"
---
# <a name="columns-with-the-name-of-an-xpath-node-test"></a><span data-ttu-id="f40b7-102">具有 XPath 節點測試名稱的資料行</span><span class="sxs-lookup"><span data-stu-id="f40b7-102">Columns with the Name of an XPath Node Test</span></span>
  <span data-ttu-id="f40b7-103">如果資料行名稱是其中一個 XPath 節點測試，將會對應內容，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="f40b7-103">If the column name is one of the XPath node tests, the content is mapped as shown in the following table.</span></span> <span data-ttu-id="f40b7-104">如果資料行名稱是 XPath 節點測試，會將內容對應至對應的節點。</span><span class="sxs-lookup"><span data-stu-id="f40b7-104">When the column name is an XPath node test, the content is mapped to the corresponding node.</span></span> <span data-ttu-id="f40b7-105">如果資料行的 SQL 類型是 `xml`，就會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="f40b7-105">If the SQL type of the column is `xml`, an error is returned.</span></span>  
  
|<span data-ttu-id="f40b7-106">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="f40b7-106">Column Name</span></span>|<span data-ttu-id="f40b7-107">行為</span><span class="sxs-lookup"><span data-stu-id="f40b7-107">Behavior</span></span>|  
|-----------------|--------------|  
|<span data-ttu-id="f40b7-108">text()</span><span class="sxs-lookup"><span data-stu-id="f40b7-108">text()</span></span>|<span data-ttu-id="f40b7-109">對於有 text() 名稱的資料行，將會以文字節點加入該資料行中的字串值。</span><span class="sxs-lookup"><span data-stu-id="f40b7-109">For a column with the name of text(), the string value in that column is added as a text node.</span></span>|  
|<span data-ttu-id="f40b7-110">comment()</span><span class="sxs-lookup"><span data-stu-id="f40b7-110">comment()</span></span>|<span data-ttu-id="f40b7-111">對於有 comment() 名稱的資料行，將會以 XML 註解加入該資料行中的字串值。</span><span class="sxs-lookup"><span data-stu-id="f40b7-111">For a column with the name of comment(), the string value in that column is added as an XML comment.</span></span>|  
|<span data-ttu-id="f40b7-112">node()</span><span class="sxs-lookup"><span data-stu-id="f40b7-112">node()</span></span>|<span data-ttu-id="f40b7-113">對於有 node() 名稱的資料行，其結果與資料行名稱為萬用字元 (\*) 的結果相同。</span><span class="sxs-lookup"><span data-stu-id="f40b7-113">For a column with the name of node(), the result is the same as it is when the column name is a wildcard character (\*).</span></span>|  
|<span data-ttu-id="f40b7-114">processing-instruction(name)</span><span class="sxs-lookup"><span data-stu-id="f40b7-114">processing-instruction(name)</span></span>|<span data-ttu-id="f40b7-115">對於有處理指示名稱的資料行，將會以處理指示目標名稱的 PI 值加入該資料行中的字串值。</span><span class="sxs-lookup"><span data-stu-id="f40b7-115">For a column with the name of a processing instruction, the string value in that column is added as the PI value for the processing instruction target name.</span></span>|  
  
 <span data-ttu-id="f40b7-116">下列查詢會將節點測試的用途顯示為資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="f40b7-116">The following query shows the use of the node tests as column names.</span></span> <span data-ttu-id="f40b7-117">它會在產生的 XML 中加入文字節點和註解。</span><span class="sxs-lookup"><span data-stu-id="f40b7-117">It adds text nodes and comments in the resulting XML.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
        'Example of using node tests such as text(), comment(), processing-instruction()'                as "comment()",  
        'Some PI'                   as "processing-instruction(PI)",  
        'Employee name and address data' as "text()",  
        'middle name is optional'        as "EmpName/text()",  
        FirstName                        as "EmpName/First",   
        MiddleName                       as "EmpName/Middle",   
        LastName                         as "EmpName/Last",  
        AddressLine1                     as "Address/AddrLine1",  
        AddressLine2                     as "Address/AddrLIne2",  
        City                             as "Address/City"  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P   
    ON P.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.BusinessEntityAddress AS BAE  
    ON BAE.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.Address AS A  
    ON BAE.AddressID = A.AddressID  
WHERE  E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 <span data-ttu-id="f40b7-118">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="f40b7-118">This is the result:</span></span>  
  
 `<row EmpID="1">`  
  
 `<!--Example of using node tests such as text(), comment(), processing-instruction() -->`  
  
 `<?PI Some PI?>`  
  
 `Employee name and address data`  
  
 `<EmpName>middle name is optional`  
  
 `<First>Ken</First>`  
  
 `<Last>S??nchez</Last>`  
  
 `</EmpName>`  
  
 `<Address>`  
  
 `<AddrLine1>4350 Minute Dr.</AddrLine1>`  
  
 `<City>Minneapolis</City>`  
  
 `</Address>`  
  
 `</row>`  
  
## <a name="see-also"></a><span data-ttu-id="f40b7-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f40b7-119">See Also</span></span>  
 [<span data-ttu-id="f40b7-120">搭配 FOR XML 使用 PATH 模式</span><span class="sxs-lookup"><span data-stu-id="f40b7-120">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
