---
title: 預設包含 NULL 值的資料行 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- columns [XML in SQL Server], null default value
ms.assetid: 9381c07f-6887-4a62-9730-32661f9aa87c
author: rothja
ms.author: jroth
ms.openlocfilehash: 92ea51101f73695be2075a1b41deb62ca021f496
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585180"
---
# <a name="columns-that-contain-a-null-value-by-default"></a><span data-ttu-id="9807c-102">預設包含 NULL 值的資料行</span><span class="sxs-lookup"><span data-stu-id="9807c-102">Columns that Contain a Null Value By Default</span></span>
  <span data-ttu-id="9807c-103">依預設，資料行中的 Null 值會與缺少的屬性、節點或元素相對應。</span><span class="sxs-lookup"><span data-stu-id="9807c-103">By default, a null value in a column maps to the absence of the attribute, node, or element.</span></span> <span data-ttu-id="9807c-104">此預設行為是可以覆寫的，方法為使用 ELEMENTS 指示詞來要求元素中心的 XML，並指定 XSINIL 來要求為 NULL 值加入元素，如下列查詢所示：</span><span class="sxs-lookup"><span data-stu-id="9807c-104">This default behavior can be overwritten by requesting element-centric XML using the ELEMENTS directive and specifying XSINIL to request adding elements for NULL values, as shown in the following query:</span></span>  
  
```  
SELECT EmployeeID as "@EmpID",   
       FirstName  as "EmpName/First",   
       MiddleName as "EmpName/Middle",   
       LastName   as "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH, ELEMENTS XSINIL  
```  
  
 <span data-ttu-id="9807c-105">下列範例會顯示結果。</span><span class="sxs-lookup"><span data-stu-id="9807c-105">The following shows the result.</span></span> <span data-ttu-id="9807c-106">請注意如果沒有指定 XSINIL，將不會有 <`Middle`> 元素。</span><span class="sxs-lookup"><span data-stu-id="9807c-106">Note that if XSINIL is not specified, the <`Middle`> element will be absent.</span></span>  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9807c-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9807c-107">See Also</span></span>  
 [<span data-ttu-id="9807c-108">搭配 FOR XML 使用 PATH 模式</span><span class="sxs-lookup"><span data-stu-id="9807c-108">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
