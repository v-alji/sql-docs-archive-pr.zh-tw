---
title: 範例：擷取員工資訊 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- EXPLICIT mode
ms.assetid: 63cd6569-2600-485b-92b4-1f6ba09db219
author: rothja
ms.author: jroth
ms.openlocfilehash: ae4578aedb7dbcc63388d5ef797e3a0bf5d8c306
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596568"
---
# <a name="example-retrieving-employee-information"></a><span data-ttu-id="729f4-102">範例：擷取員工資訊</span><span class="sxs-lookup"><span data-stu-id="729f4-102">Example: Retrieving Employee Information</span></span>
  <span data-ttu-id="729f4-103">此範例會擷取每個員工的員工識別碼及員工名稱。</span><span class="sxs-lookup"><span data-stu-id="729f4-103">This example retrieves an employee ID and employee name for each employee.</span></span> <span data-ttu-id="729f4-104">在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫中，employeeID 可以從 Employee 資料表中的 BusinessEntityID 資料行取得。</span><span class="sxs-lookup"><span data-stu-id="729f4-104">In the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, the employeeID can be obtained from the BusinessEntityID column in the Employee table.</span></span> <span data-ttu-id="729f4-105">員工名稱可以從 Person 資料表取得。</span><span class="sxs-lookup"><span data-stu-id="729f4-105">Employee names can be obtained from the Person table.</span></span> <span data-ttu-id="729f4-106">BusinessEntityID 資料行可用於聯結資料表。</span><span class="sxs-lookup"><span data-stu-id="729f4-106">The BusinessEntityID column can be used to join the tables.</span></span>  
  
 <span data-ttu-id="729f4-107">假設想要 FOR XML EXPLICIT 轉換產生 XML，如下所示：</span><span class="sxs-lookup"><span data-stu-id="729f4-107">Assume that you want FOR XML EXPLICIT transformation to generate XML as shown in the following:</span></span>  
  
```  
<Employee EmpID="1" >  
  <Name FName="Ken" LName="S??nchez" />  
</Employee>  
...  
```  
  
 <span data-ttu-id="729f4-108">因為階層中有兩個層級，所以您要撰寫兩個 `SELECT` 查詢並套用 UNION ALL。</span><span class="sxs-lookup"><span data-stu-id="729f4-108">Because there are two levels in the hierarchy, you would write two `SELECT` queries and apply UNION ALL.</span></span> <span data-ttu-id="729f4-109">上述為第一個查詢，其會擷取 <`Employee`> 元素及其屬性的值。</span><span class="sxs-lookup"><span data-stu-id="729f4-109">This is the first query that retrieves values for the <`Employee`> element and its attributes.</span></span> <span data-ttu-id="729f4-110">查詢會將 `1` 指派為 <`Employee`> 元素的 `Tag` 值，並將 NULL 指派為 `Parent`，因為這是最上層元素。</span><span class="sxs-lookup"><span data-stu-id="729f4-110">The query assigns `1` as `Tag` value for the <`Employee`> element and NULL as `Parent`, because it is the top-level element.</span></span>  
  
```  
SELECT 1    as Tag,  
       NULL as Parent,  
       E.BusinessEntityID AS [Employee!1!EmpID],  
       NULL       as [Name!2!FName],  
       NULL       as [Name!2!LName]  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
ON  E.BusinessEntityID = P.BusinessEntityID;  
```  
  
 <span data-ttu-id="729f4-111">上述為第二個查詢。</span><span class="sxs-lookup"><span data-stu-id="729f4-111">This is the second query.</span></span> <span data-ttu-id="729f4-112">它會擷取 <`Name`> 元素的值。</span><span class="sxs-lookup"><span data-stu-id="729f4-112">It retrieves values for the <`Name`> element.</span></span> <span data-ttu-id="729f4-113">它會將 `2` 指派為 <`Name`> 元素的 `Tag` 值，並將 `1` 指派為識別 <`Employee`> 做為父系的 `Parent` 標記值。</span><span class="sxs-lookup"><span data-stu-id="729f4-113">It assigns `2` as `Tag` value for the <`Name`> element and `1` as `Parent` tag value identifying <`Employee`> as the parent.</span></span>  
  
```  
SELECT 2 as Tag,  
       1 as Parent,  
       E.BusinessEntityID,  
       FirstName,   
       LastName   
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P  
ON  E.BusinessEntityID = P.BusinessEntityID;  
```  
  
 <span data-ttu-id="729f4-114">您可以利用 `UNION AL`L 合併這些查詢、套用 `FOR XML EXPLICIT`，然後指定所需的 `ORDER BY` 子句。</span><span class="sxs-lookup"><span data-stu-id="729f4-114">You combine these queries with `UNION AL`L, apply `FOR XML EXPLICIT`, and specify the required `ORDER BY` clause.</span></span> <span data-ttu-id="729f4-115">您必須先按 `BusinessEntityID` 排序資料列集，然後再按名稱排序，讓名稱中的 NULL 值最先出現。</span><span class="sxs-lookup"><span data-stu-id="729f4-115">You must sort the rowset first by `BusinessEntityID` and then by name so that the NULL values in the name appear first.</span></span> <span data-ttu-id="729f4-116">執行以下未使用 FOR XML 子句的查詢，就可以看見產生了通用資料表。</span><span class="sxs-lookup"><span data-stu-id="729f4-116">By executing the following query without the FOR XML clause, you can see the universal table generated.</span></span>  
  
 <span data-ttu-id="729f4-117">以下為最後查詢：</span><span class="sxs-lookup"><span data-stu-id="729f4-117">This is the final query:</span></span>  
  
```  
SELECT 1    as Tag,  
       NULL as Parent,  
       E.BusinessEntityID as [Employee!1!EmpID],  
       NULL       as [Name!2!FName],  
       NULL       as [Name!2!LName]  
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
ORDER BY [Employee!1!EmpID],[Name!2!FName]  
FOR XML EXPLICIT;  
```  
  
 <span data-ttu-id="729f4-118">以下是部份結果：</span><span class="sxs-lookup"><span data-stu-id="729f4-118">This is the partial result:</span></span>  
  
 `<Employee EmpID="1">`  
  
 `<Name FName="Ken" LName="S??nchez" />`  
  
 `</Employee>`  
  
 `<Employee EmpID="2">`  
  
 `<Name FName="Terri" LName="Duffy" />`  
  
 `</Employee>`  
  
 `...`  
  
 <span data-ttu-id="729f4-119">第一個 `SELECT` 會指定產生之資料列集中的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="729f4-119">The first `SELECT` specifies names for columns in the resulting rowset.</span></span> <span data-ttu-id="729f4-120">這些名稱會形成兩個資料行群組。</span><span class="sxs-lookup"><span data-stu-id="729f4-120">These names form two column groups.</span></span> <span data-ttu-id="729f4-121">資料行名稱中有 `Tag` 值 `1` 的群組，可將 `Employee` 識別為元素，並將 `EmpID` 識別為屬性。</span><span class="sxs-lookup"><span data-stu-id="729f4-121">The group that has `Tag` value `1` in the column name identifies `Employee` as an element and `EmpID` as the attribute.</span></span> <span data-ttu-id="729f4-122">其他資料行群組在資料行中有 `Tag` 值 `2`，而且可將 <`Name`> 識別為元素，並將 `FName` 及 `LName` 識別為屬性。</span><span class="sxs-lookup"><span data-stu-id="729f4-122">The other column group has `Tag` value `2` in the column and identifies <`Name`> as the element and `FName` and `LName` as the attributes.</span></span>  
  
 <span data-ttu-id="729f4-123">下表會顯示此查詢產生的部分資料列集：</span><span class="sxs-lookup"><span data-stu-id="729f4-123">The following table shows the partial rowset generated by the query:</span></span>  
  
 `Tag Parent  Employee!1!EmpID Name!2!FName Name!2!LName`  
  
 `--- ------  ---------------- ------------ ------------`  
  
 `1   NULL    1                NULL         NULL`  
  
 `2   1       1                Ken          S??nchez`  
  
 `1   NULL    2                NULL         NULL`  
  
 `2   1       2                Terri        Duffy`  
  
 `1   NULL    3                NULL         NULL`  
  
 `2   1       3                Roberto      Tamburello`  
  
 `...`  
  
 <span data-ttu-id="729f4-124">以下是如何處理通用資料表的資料列，以產生結果 XML 樹狀結構：</span><span class="sxs-lookup"><span data-stu-id="729f4-124">This is how the rows in the universal table are processed to produce the resulting XML tree:</span></span>  
  
 <span data-ttu-id="729f4-125">第一個資料列會識別 `Tag` 值 `1`。</span><span class="sxs-lookup"><span data-stu-id="729f4-125">The first row identifies `Tag` value `1`.</span></span> <span data-ttu-id="729f4-126">因此，會識別 `Tag` 值 `1` 的資料行群組 `Employee!1!EmpID`。</span><span class="sxs-lookup"><span data-stu-id="729f4-126">Therefore, the column group that has the `Tag` value `1` is identified, `Employee!1!EmpID`.</span></span> <span data-ttu-id="729f4-127">此資料行會將 `Employee` 識別為元素名稱。</span><span class="sxs-lookup"><span data-stu-id="729f4-127">This column identifies `Employee` as the element name.</span></span> <span data-ttu-id="729f4-128">然後就會建立擁有 `EmpID` 屬性的 <`Employee`> 元素。</span><span class="sxs-lookup"><span data-stu-id="729f4-128">An <`Employee`> element is then created that has `EmpID` attributes.</span></span> <span data-ttu-id="729f4-129">對應的資料行值會指派給這些屬性。</span><span class="sxs-lookup"><span data-stu-id="729f4-129">Corresponding column values are assigned to these attributes.</span></span>  
  
 <span data-ttu-id="729f4-130">第二個資料列具有 `Tag` 值 `2`。</span><span class="sxs-lookup"><span data-stu-id="729f4-130">The second row has the `Tag` value `2`.</span></span> <span data-ttu-id="729f4-131">因此，會識別資料行名稱中 `Tag` 值為 `2` 的資料行群組 `Name!2!FName`、 `Name!2!LName`。</span><span class="sxs-lookup"><span data-stu-id="729f4-131">Therefore, the column group that has the `Tag` value `2` in the column name, `Name!2!FName`, `Name!2!LName`, is identified.</span></span> <span data-ttu-id="729f4-132">這些資料行名稱會將 `Name` 識別為元素名稱。</span><span class="sxs-lookup"><span data-stu-id="729f4-132">These column names identify `Name` as element name.</span></span> <span data-ttu-id="729f4-133">此外會建立擁有 `FName` 與 `LName` 屬性的 <`Name`> 元素。</span><span class="sxs-lookup"><span data-stu-id="729f4-133">A <`Name`> element is created that has `FName` and `LName` attributes.</span></span> <span data-ttu-id="729f4-134">然後將對應的資料行值指派給這些屬性。</span><span class="sxs-lookup"><span data-stu-id="729f4-134">Corresponding column values are then assigned to these attributes.</span></span> <span data-ttu-id="729f4-135">此資料列會將 `1` 識別為 `Parent`。</span><span class="sxs-lookup"><span data-stu-id="729f4-135">This row identifies `1` as `Parent`.</span></span> <span data-ttu-id="729f4-136">此元素子系便會加入到先前的 <`Employee`> 元素。</span><span class="sxs-lookup"><span data-stu-id="729f4-136">This element child is added to the previous <`Employee`> element.</span></span>  
  
 <span data-ttu-id="729f4-137">這個處理序會對資料列集中其餘的資料列重複進行。</span><span class="sxs-lookup"><span data-stu-id="729f4-137">This process is repeated for rest of the rows in the rowset.</span></span> <span data-ttu-id="729f4-138">請記下通用資料表中資料列排序的優先順序，如此 FOR XML EXPLICIT 就可以依序處理資料列集，並產生您想要的 XML。</span><span class="sxs-lookup"><span data-stu-id="729f4-138">Note the importance of ordering the rows in the universal table so that FOR XML EXPLICIT can process the rowset in order and generate the XML you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="729f4-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="729f4-139">See Also</span></span>  
 [<span data-ttu-id="729f4-140">搭配 FOR XML 使用 EXPLICIT 模式</span><span class="sxs-lookup"><span data-stu-id="729f4-140">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
