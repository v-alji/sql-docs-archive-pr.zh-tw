---
title: 範例：指定 ELEMENT 指示詞 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ELEMENT directive
ms.assetid: 80dd5d1f-fa90-4f97-a186-8fa3f460a7f3
author: rothja
ms.author: jroth
ms.openlocfilehash: a03d1049fa9df23eff759634bcd74f88f842a8e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686857"
---
# <a name="example-specifying-the-element-directive"></a><span data-ttu-id="beb25-102">範例：指定 ELEMENT 指示詞</span><span class="sxs-lookup"><span data-stu-id="beb25-102">Example: Specifying the ELEMENT Directive</span></span>
  <span data-ttu-id="beb25-103">這會擷取員工資訊，並產生元素中心的 XML，如下所示：</span><span class="sxs-lookup"><span data-stu-id="beb25-103">This retrieves employee information and generates element-centric XML as shown in the following:</span></span>  
  
```  
<Employee EmpID=...>  
  <Name>  
    <FName>...</FName>  
    <LName>...</LName>  
  </Name>  
</Employee>  
```  
  
 <span data-ttu-id="beb25-104">除了在資料行名稱中增加 `ELEMENT` 指示詞之外，該查詢維持不變。</span><span class="sxs-lookup"><span data-stu-id="beb25-104">The query remains the same, except you add the `ELEMENT` directive in the column names.</span></span> <span data-ttu-id="beb25-105">因此，<`FName`> 及 <`LName`> 元素子系 (而非屬性) 會加入到 <`Name`> 元素中。</span><span class="sxs-lookup"><span data-stu-id="beb25-105">Therefore, instead of attributes, the <`FName`> and <`LName`> element children are added to the <`Name`> element.</span></span> <span data-ttu-id="beb25-106">因為 `Employee!1!EmpID` 資料行未指定 `ELEMENT` 指示詞，所以 `EmpID` 會新增為 <`Employee`> 元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="beb25-106">Because the `Employee!1!EmpID` column does not specify the `ELEMENT` directive, `EmpID` is added as the attribute of the <`Employee`> element.</span></span>  
  
```  
SELECT 1    as Tag,  
       NULL as Parent,  
       E.BusinessEntityID as [Employee!1!EmpID],  
       NULL       as [Name!2!FName!ELEMENT],  
       NULL       as [Name!2!LName!ELEMENT]  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
ON  E.BusinessEntityID = P.BusinessEntityID  
UNION ALL  
SELECT 2 as Tag,  
       1 as Parent,  
       E.BusinessEntityID,  
       FirstName,   
       LastName   
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
ON  E.BusinessEntityID = P.BusinessEntityID  
ORDER BY [Employee!1!EmpID],[Name!2!FName!ELEMENT]  
FOR XML EXPLICIT;  
```  
  
 <span data-ttu-id="beb25-107">以下是部份結果。</span><span class="sxs-lookup"><span data-stu-id="beb25-107">This is the partial result.</span></span>  
  
 `<Employee EmpID="1">`  
  
 `<Name>`  
  
 `<FName>Ken</FName>`  
  
 `<LName>S??nchez</LName>`  
  
 `</Name>`  
  
 `</Employee>`  
  
 `<Employee EmpID="2">`  
  
 `<Name>`  
  
 `<FName>Terri</FName>`  
  
 `<LName>Duffy</LName>`  
  
 `</Name>`  
  
 `</Employee>`  
  
 `...`  
  
## <a name="see-also"></a><span data-ttu-id="beb25-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="beb25-108">See Also</span></span>  
 [<span data-ttu-id="beb25-109">搭配 FOR XML 使用 EXPLICIT 模式</span><span class="sxs-lookup"><span data-stu-id="beb25-109">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
