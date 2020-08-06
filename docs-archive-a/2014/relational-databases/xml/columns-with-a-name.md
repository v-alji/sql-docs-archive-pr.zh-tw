---
title: 有名稱的資料行 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: c994e089-4cfc-4e9b-b7fc-e74f6014b51a
author: rothja
ms.author: jroth
ms.openlocfilehash: 32cfe617b80ed216374249961b85eae401011a67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687570"
---
# <a name="columns-with-a-name"></a><span data-ttu-id="ecfb4-102">有名稱的資料行</span><span class="sxs-lookup"><span data-stu-id="ecfb4-102">Columns with a Name</span></span>
  <span data-ttu-id="ecfb4-103">以下是具有名稱的資料列集資料行，以區分大小寫的方式對應至產生之 XML 的特定條件：</span><span class="sxs-lookup"><span data-stu-id="ecfb4-103">The following are the specific conditions in which rowset columns with a name are mapped, case-sensitive, to the resulting XML:</span></span>  
  
-   <span data-ttu-id="ecfb4-104">此資料行名稱以 \@ 符號開頭。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-104">The column name starts with an at sign (\@).</span></span>  
  
-   <span data-ttu-id="ecfb4-105">此資料行名稱不是以 \@ 符號開頭。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-105">The column name does not start with an at sign (\@).</span></span>  
  
-   <span data-ttu-id="ecfb4-106">此資料行名稱不是以 \@ 符號開頭且包含斜線 (/)。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-106">The column name does not start with an at sign\@ and contains a slash mark (/).</span></span>  
  
-   <span data-ttu-id="ecfb4-107">數個資料行共用相同的前置詞。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-107">Several columns share the same prefix.</span></span>  
  
-   <span data-ttu-id="ecfb4-108">一個資料行具有不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-108">One column has a different name.</span></span>  
  
## <a name="column-name-starts-with-an-at-sign-"></a><span data-ttu-id="ecfb4-109">資料行名稱以 \@ 符號開頭</span><span class="sxs-lookup"><span data-stu-id="ecfb4-109">Column Name Starts with an At Sign (\@)</span></span>  
 <span data-ttu-id="ecfb4-110">如果資料行名稱的開頭是 @ sign (\@) 而且不包含斜線 (/) ，則 `row` 會建立具有對應資料行值之 <> 元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-110">If the column name starts with an at sign (\@) and does not contain a slash mark (/), an attribute of the <`row`> element that has the corresponding column value is created.</span></span> <span data-ttu-id="ecfb4-111">例如，以下查詢會傳回兩個資料行 (\@PmId、Name) 的資料列集。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-111">For example, the following query returns a two-column (\@PmId, Name) rowset.</span></span> <span data-ttu-id="ecfb4-112">在產生的 XML 中，**PmId** 屬性會加入對應的 <`row`> 元素中，並會將 ProductModelID 值指派給該元素。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-112">In the resulting XML, a **PmId** attribute is added to the corresponding <`row`> element and a value of ProductModelID is assigned to it.</span></span>  
  
```  
  
SELECT ProductModelID as "@PmId",  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH   
go  
  
```  
  
 <span data-ttu-id="ecfb4-113">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="ecfb4-113">This is the result:</span></span>  
  
```  
<row PmId="7">  
  <Name>HL Touring Frame</Name>  
</row>  
```  
  
 <span data-ttu-id="ecfb4-114">請注意在相同的層級中，屬性必須在任何其他節點類型的前面，例如元素節點與文字節點。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-114">Note that attributes must come before any other node types, such as element nodes and text nodes, in the same level.</span></span> <span data-ttu-id="ecfb4-115">下列查詢將傳回錯誤：</span><span class="sxs-lookup"><span data-stu-id="ecfb4-115">The following query will return an error:</span></span>  
  
```  
SELECT Name,  
       ProductModelID as "@PmId"  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH   
go  
```  
  
## <a name="column-name-does-not-start-with-an-at-sign-"></a><span data-ttu-id="ecfb4-116">資料行名稱不是以 \@ 符號開頭</span><span class="sxs-lookup"><span data-stu-id="ecfb4-116">Column Name Does Not Start with an At Sign (\@)</span></span>  
 <span data-ttu-id="ecfb4-117">如果資料行名稱的開頭不是 @ sign (\@) 、不是其中一個 XPath 節點測試，而且不包含斜線 (/) ，則會建立資料列元素之子專案的 XML 專案（預設為 <`row`>）。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-117">If the column name does not start with an at sign (\@), is not one of the XPath node tests, and does not contain a slash mark (/), an XML element that is a subelement of the row element, <`row`> by default, is created.</span></span>  
  
 <span data-ttu-id="ecfb4-118">下列查詢指定資料行名稱，也就是結果。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-118">The following query specifies the column name, the result.</span></span> <span data-ttu-id="ecfb4-119">因此，<`result`> 子元素會加入 <`row`> 元素。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-119">Therefore, a <`result`> element child is added to the <`row`> element.</span></span>  
  
```  
SELECT 2+2 as result  
for xml PATH  
```  
  
 <span data-ttu-id="ecfb4-120">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="ecfb4-120">This is the result:</span></span>  
  
```  
<row>  
  <result>4</result>  
</row>  
```  
  
 <span data-ttu-id="ecfb4-121">下列查詢會針對 **xml** 類型的 Instructions 資料行指定之 XQuery 所傳回的 XML，指定資料行名稱 ManuWorkCenterInformation。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-121">The following query specifies the column name, ManuWorkCenterInformation, for the XML returned by the XQuery specified against Instructions column of **xml** type.</span></span> <span data-ttu-id="ecfb4-122">因此，將以 <`row`> 元素的子元素加入 <`ManuWorkCenterInformation`> 元素。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-122">Therefore, a <`ManuWorkCenterInformation`> element is added as a child of the <`row`> element.</span></span>  
  
```  
SELECT   
       ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
                /MI:root/MI:Location   
              ') as ManuWorkCenterInformation  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH   
go  
```  
  
 <span data-ttu-id="ecfb4-123">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="ecfb4-123">This is the result:</span></span>  
  
```  
<row>  
  <ProductModelID>7</ProductModelID>  
  <Name>HL Touring Frame</Name>  
  <ManuWorkCenterInformation>  
    <MI:Location ...LocationID="10" ...></MI:Location>  
    <MI:Location ...LocationID="20" ...></MI:Location>  
     ...  
  </ManuWorkCenterInformation>  
</row>  
```  
  
## <a name="column-name-does-not-start-with-an-at-sign--and-contains-a-slash-mark-"></a><span data-ttu-id="ecfb4-124">資料行名稱不是以 \@ 符號開頭且包含斜線 (/)</span><span class="sxs-lookup"><span data-stu-id="ecfb4-124">Column Name Does Not Start with an At Sign (\@) and Contains a Slash Mark (/)</span></span>  
 <span data-ttu-id="ecfb4-125">如果資料行名稱不是以 \@ 符號開頭，但包含斜線 (/)，則資料行名稱會指出 XML 階層。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-125">If the column name does not start with an at sign (\@), but contains a slash mark (/), the column name indicates an XML hierarchy.</span></span> <span data-ttu-id="ecfb4-126">例如，如果資料行名稱是 "Name1/Name2/Name3.../Name***n*** "，則每個 Name***i*** 代表一個元素名稱，該元素以巢狀化方式出現在目前資料列元素 (for i=1) 中，或是在具有 Name***i-1***名稱之元素的底下。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-126">For example, if the column name is "Name1/Name2/Name3.../Name***n*** ", each Name***i*** represents an element name that is nested in the current row element (for i=1) or that is under the element that has the name Name***i-1***.</span></span> <span data-ttu-id="ecfb4-127">如果 Name***n*** 以 '\@' 開頭，它會對應至 Name***n-1*** 元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-127">If Name***n*** starts with '\@', it is mapped to an attribute of Name***n-1*** element.</span></span>  
  
 <span data-ttu-id="ecfb4-128">例如，下列查詢將會傳回員工識別碼與姓名，它們是以複雜的元素 EmpName 所代表，該元素包含姓名的 First、Middle 及 Last。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-128">For example, the following query returns an employee ID and name that are represented as a complex element EmpName that contains a First, Middle, and Last name.</span></span>  
  
```  
SELECT EmployeeID "@EmpID",   
       FirstName  "EmpName/First",   
       MiddleName "EmpName/Middle",   
       LastName   "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH  
```  
  
 <span data-ttu-id="ecfb4-129">該資料行名稱是在 PATH 模式中建構 XML 時當做路徑使用。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-129">The column names are used as a path in constructing XML in the PATH mode.</span></span> <span data-ttu-id="ecfb4-130">包含員工識別碼值的資料行名稱是以 ' \@ ' 開頭。因此，會將屬性**EmpID**新增至 <`row`> 元素。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-130">The column name that contains employee ID values, starts with '\@'.Therefore, an attribute, **EmpID**, is added to the <`row`> element.</span></span> <span data-ttu-id="ecfb4-131">在指出階層的資料行名稱中，所有其他的資料行都包含斜線 ('/')。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-131">All other columns include a slash mark ('/') in the column name that indicates hierarchy.</span></span> <span data-ttu-id="ecfb4-132">產生的 XML 在 <`row`> 元素底下將有 <`EmpName`> 子元素，而且 <`EmpName`> 子元素將有 <`First`>、<`Middle`> 及 <`Last`> 子元素。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-132">The resulting XML will have the <`EmpName`> child under the <`row`> element, and the <`EmpName`> child will have <`First`>, <`Middle`> and <`Last`> element children.</span></span>  
  
```  
<row EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
 <span data-ttu-id="ecfb4-133">員工中間名字為 Null，Null 值預設與缺少的元素或屬性相對應。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-133">The employee middle name is null and, by default, the null value maps to the absence of the element or attribute.</span></span> <span data-ttu-id="ecfb4-134">如果您要為 NULL 值產生元素，您可以指定具有 XSINL 的 ELEMENTS 指示詞，如下列查詢所示。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-134">If you want elements generated for the NULL values, you can specify the ELEMENTS directive with XSINIL as shown in this query.</span></span>  
  
```  
SELECT EmployeeID "@EmpID",   
       FirstName  "EmpName/First",   
       MiddleName "EmpName/Middle",   
       LastName   "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH, ELEMENTS XSINIL  
```  
  
 <span data-ttu-id="ecfb4-135">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="ecfb4-135">This is the result:</span></span>  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
      EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
 <span data-ttu-id="ecfb4-136">根據預設，PATH 模式會產生元素中心的 XML。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-136">By default, the PATH mode generates element-centric XML.</span></span> <span data-ttu-id="ecfb4-137">因此，在 PATH 模式查詢中指定 ELEMENTS 指示詞將不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-137">Therefore, specifying the ELEMENTS directive in a PATH mode query has no effect.</span></span> <span data-ttu-id="ecfb4-138">然而，如上述範例所示，ELEMENTS 指示詞加上 XSINIL 就可以為 Null 值產生元素。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-138">However, as shown in the previous example, the ELEMENTS directive is useful with XSINIL to generate elements for null values.</span></span>  
  
 <span data-ttu-id="ecfb4-139">除了識別碼與名稱之外，下列查詢還會擷取員工地址。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-139">Besides the ID and name, the following query retrieves an employee address.</span></span> <span data-ttu-id="ecfb4-140">根據地址資料行之資料行名稱中的路徑，會將 <`Address`> 子元素加入 <`row`> 元素，而地址詳細資料則會以 <`Address`> 元素的子元素加入。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-140">As per the path in the column names for address columns, an <`Address`> element child is added to the <`row`> element and the address details are added as element children of the <`Address`> element.</span></span>  
  
```  
SELECT EmployeeID   "@EmpID",   
       FirstName    "EmpName/First",   
       MiddleName   "EmpName/Middle",   
       LastName     "EmpName/Last",  
       AddressLine1 "Address/AddrLine1",  
       AddressLine2 "Address/AddrLIne2",  
       City         "Address/City"  
FROM   HumanResources.Employee E, Person.Contact C, Person.Address A  
WHERE  E.EmployeeID = C.ContactID  
AND    E.AddressID = A.AddressID  
AND    E.EmployeeID=1  
FOR XML PATH  
```  
  
 <span data-ttu-id="ecfb4-141">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="ecfb4-141">This is the result:</span></span>  
  
```  
<row EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Last>Achong</Last>  
  </EmpName>  
  <Address>  
    <AddrLine1>7726 Driftwood Drive</AddrLine1>  
    <City>Monroe</City>  
  </Address>  
</row>  
```  
  
## <a name="several-columns-share-the-same-path-prefix"></a><span data-ttu-id="ecfb4-142">數個資料行共用相同的路徑前置詞</span><span class="sxs-lookup"><span data-stu-id="ecfb4-142">Several Columns Share the Same Path Prefix</span></span>  
 <span data-ttu-id="ecfb4-143">如果數個後續的資料行共用相同的路徑前置詞，則會在相同的名稱下將它們群組在一起。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-143">If several subsequent columns share the same path prefix, they are grouped together under the same name.</span></span> <span data-ttu-id="ecfb4-144">即使不同的命名空間前置詞是與相同的命名空間繫結，但仍使用了它們，就會將路徑視為不同。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-144">If different namespace prefixes are being used even if they are bound to the same namespace, a path is considered different.</span></span> <span data-ttu-id="ecfb4-145">在上述查詢中，FirstName、MiddleName 及 LastName 資料行是共用相同的 EmpName 前置詞。因此，會將它們以 <`EmpName`> 子元素加入。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-145">In the previous query, the FirstName, MiddleName, and LastName columns share the same EmpName prefix.Therefore, they are added as children of the <`EmpName`> element.</span></span> <span data-ttu-id="ecfb4-146">當您在上述範例中建立 <`Address`> 元素時也是如此。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-146">This is also the case when you were creating the <`Address`> element in the previous example.</span></span>  
  
## <a name="one-column-has-a-different-name"></a><span data-ttu-id="ecfb4-147">一個資料行具有不同的名稱</span><span class="sxs-lookup"><span data-stu-id="ecfb4-147">One Column Has a Different Name</span></span>  
 <span data-ttu-id="ecfb4-148">如果具有不同名稱的資料行出現在其間，它將會拆散群組，如下列修改的查詢所示。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-148">If a column with a different name appears in between, it will break the grouping, as shown in the following modified query.</span></span> <span data-ttu-id="ecfb4-149">查詢會在 FirstName 與 MiddleName 資料行之間加入地址資料行，以拆散上述查詢所指定的 FirstName、MiddleName 及 LastName 的群組。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-149">The query breaks the grouping of FirstName, MiddleName, and LastName, as specified in the previous query, by adding address columns in between the FirstName and MiddleName columns.</span></span>  
  
```  
SELECT EmployeeID "@EmpID",   
       FirstName "EmpName/First",   
       AddressLine1 "Address/AddrLine1",  
       AddressLine2 "Address/AddrLIne2",  
       City "Address/City",  
       MiddleName "EmpName/Middle",   
       LastName "EmpName/Last"  
FROM   HumanResources.EmployeeAddress E, Person.Contact C, Person.Address A  
WHERE  E.EmployeeID = C.ContactID  
AND    E.AddressID = A.AddressID  
AND    E.EmployeeID=1  
FOR XML PATH  
```  
  
 <span data-ttu-id="ecfb4-150">因此，此查詢會建立兩個 <`EmpName`> 元素。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-150">As a result, the query creates two <`EmpName`> elements.</span></span> <span data-ttu-id="ecfb4-151">第一個 <`EmpName`> 元素具有 <`FirstName`> 子元素，而第二個 <`EmpName`> 元素則具有 <`MiddleName`> 及 <`LastName`> 子元素。</span><span class="sxs-lookup"><span data-stu-id="ecfb4-151">The first <`EmpName`> element has the <`FirstName`> element child and the second <`EmpName`> element has the <`MiddleName`> and <`LastName`> element children.</span></span>  
  
 <span data-ttu-id="ecfb4-152">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="ecfb4-152">This is the result:</span></span>  
  
```  
<row EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
  </EmpName>  
  <Address>  
    <AddrLine1>7726 Driftwood Drive</AddrLine1>  
    <City>Monroe</City>  
  </Address>  
  <EmpName>  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ecfb4-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecfb4-153">See Also</span></span>  
 [<span data-ttu-id="ecfb4-154">搭配 FOR XML 使用 PATH 模式</span><span class="sxs-lookup"><span data-stu-id="ecfb4-154">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
