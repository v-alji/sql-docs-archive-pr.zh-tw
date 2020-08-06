---
title: 以萬用字元 (*) 指定名稱的資料行 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: d9551df1-5bb4-4c0b-880a-5bb049834884
author: rothja
ms.author: jroth
ms.openlocfilehash: 4b363baf8792628c2e17b1a695c19a6a338f4fb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595838"
---
# <a name="columns-with-a-name-specified-as-a-wildcard-character"></a><span data-ttu-id="e6196-102">以萬用字元 (\*) 指定名稱的資料行</span><span class="sxs-lookup"><span data-stu-id="e6196-102">Columns with a Name Specified as a Wildcard Character</span></span>
  <span data-ttu-id="e6196-103">如果以萬用字元 (\*) 指定資料行名稱，則插入該資料行內容的方式，就像是沒有指定資料行名稱一樣。</span><span class="sxs-lookup"><span data-stu-id="e6196-103">If the column name specified is a wildcard character (\*), the content of that column is inserted as if there is no column name specified.</span></span> <span data-ttu-id="e6196-104">如果此資料行是非 `xml` 類型的資料行，則會以文字節點插入資料行內容，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e6196-104">If this column is a non-`xml` type column, the column content is inserted as a text node, as shown in the following example:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
       FirstName "*",   
       MiddleName "*",   
       LastName "*"  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
    ON E.BusinessEntityID = P.BusinessEntityID  
WHERE E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 <span data-ttu-id="e6196-105">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="e6196-105">This is the result:</span></span>  
  
 `<row EmpID="1">KenJS??nchez</row>`  
  
 <span data-ttu-id="e6196-106">如果此資料行是 `xml` 類型，就會插入對應的 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="e6196-106">If the column is of `xml` type, the corresponding XML tree is inserted.</span></span> <span data-ttu-id="e6196-107">例如，下列查詢為資料行名稱指定 "\*"，該資料行名稱包含 XQuery 針對 Instructions 資料行所傳回的 XML。</span><span class="sxs-lookup"><span data-stu-id="e6196-107">For example, the following query specifies "\*" for the column name that contains the XML returned by the XQuery against the Instructions column.</span></span>  
  
```  
SELECT   
       ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
                /MI:root/MI:Location   
              ') as "*"  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH;   
GO  
```  
  
 <span data-ttu-id="e6196-108">以下是結果。</span><span class="sxs-lookup"><span data-stu-id="e6196-108">This is the result.</span></span> <span data-ttu-id="e6196-109">插入 XQuery 所傳回的 XML，但不會有包裝元素。</span><span class="sxs-lookup"><span data-stu-id="e6196-109">The XML returned by XQuery is inserted without a wrapping element.</span></span>  
  
 `<row>`  
  
 `<ProductModelID>7</ProductModelID>`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<MI:Location LocationID="10">...</MI:Location>`  
  
 `<MI:Location LocationID="20">...</MI:Location>`  
  
 `...`  
  
 `</row>`  
  
## <a name="see-also"></a><span data-ttu-id="e6196-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6196-110">See Also</span></span>  
 [<span data-ttu-id="e6196-111">搭配 FOR XML 使用 PATH 模式</span><span class="sxs-lookup"><span data-stu-id="e6196-111">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
