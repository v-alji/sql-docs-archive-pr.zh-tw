---
title: 使用巢狀 AUTO 模式查詢產生同層級 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- queries [XML in SQL Server], nested AUTO mode
- nested AUTO mode query
ms.assetid: 748d9899-589d-4420-8048-1258e9e67c20
author: rothja
ms.author: jroth
ms.openlocfilehash: 20362942bdd0f7e7537433b664e5e63461ded499
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710421"
---
# <a name="generate-siblings-with-a-nested-auto-mode-query"></a><span data-ttu-id="36eda-102">使用巢狀 AUTO 模式查詢產生同層級</span><span class="sxs-lookup"><span data-stu-id="36eda-102">Generate Siblings with a Nested AUTO Mode Query</span></span>
  <span data-ttu-id="36eda-103">以下範例示範如何使用巢狀 AUTO 模式查詢產生同層級。</span><span class="sxs-lookup"><span data-stu-id="36eda-103">The following example shows how to generate siblings by using a nested AUTO mode query.</span></span> <span data-ttu-id="36eda-104">其他產生這類 XML 的唯一方式是使用 EXPLICIT 模式。</span><span class="sxs-lookup"><span data-stu-id="36eda-104">The only other way to generate such XML is to use the EXPLICIT mode.</span></span> <span data-ttu-id="36eda-105">但是，這可能會相當繁雜。</span><span class="sxs-lookup"><span data-stu-id="36eda-105">However, this can be cumbersome.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36eda-106">範例</span><span class="sxs-lookup"><span data-stu-id="36eda-106">Example</span></span>  
 <span data-ttu-id="36eda-107">此查詢會建構提供銷售訂單資訊的 XML。</span><span class="sxs-lookup"><span data-stu-id="36eda-107">This query constructs XML that provides sales order information.</span></span> <span data-ttu-id="36eda-108">這包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="36eda-108">This includes the following:</span></span>  
  
-   <span data-ttu-id="36eda-109">銷售訂單標頭資訊、 `SalesOrderID`、 `SalesPersonID`和 `OrderDate`。</span><span class="sxs-lookup"><span data-stu-id="36eda-109">Sales order header information, `SalesOrderID`, `SalesPersonID`, and `OrderDate`.</span></span> [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] <span data-ttu-id="36eda-110">會將這些資訊儲存在 `SalesOrderHeader` 資料表中。</span><span class="sxs-lookup"><span data-stu-id="36eda-110">stores this information in the `SalesOrderHeader` table.</span></span>  
  
-   <span data-ttu-id="36eda-111">銷售訂單詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="36eda-111">Sales order detail information.</span></span> <span data-ttu-id="36eda-112">這包括一或多項已訂購的產品、單價及訂購的數量。</span><span class="sxs-lookup"><span data-stu-id="36eda-112">This includes one or more products ordered, the unit price, and the quantity ordered.</span></span> <span data-ttu-id="36eda-113">此項資訊是儲存在 `SalesOrderDetail` 資料表中。</span><span class="sxs-lookup"><span data-stu-id="36eda-113">This information is stored in the `SalesOrderDetail` table.</span></span>  
  
-   <span data-ttu-id="36eda-114">銷售人員資訊。</span><span class="sxs-lookup"><span data-stu-id="36eda-114">Sales person information.</span></span> <span data-ttu-id="36eda-115">這是承接訂單的銷售人員。</span><span class="sxs-lookup"><span data-stu-id="36eda-115">This is the salesperson who took the order.</span></span> <span data-ttu-id="36eda-116">`SalesPerson` 資料表提供 `SalesPersonID`。</span><span class="sxs-lookup"><span data-stu-id="36eda-116">The `SalesPerson` table provides the `SalesPersonID`.</span></span> <span data-ttu-id="36eda-117">對於此查詢，您必須將此資料表聯結到 `Employee` 資料表，才能找到銷售人員的名稱。</span><span class="sxs-lookup"><span data-stu-id="36eda-117">For this query, you have to join this table to the `Employee` table to find the name of the sales person.</span></span>  
  
 <span data-ttu-id="36eda-118">下述的兩個相異 `SELECT` 查詢會產生外觀上有些許不同的 XML。</span><span class="sxs-lookup"><span data-stu-id="36eda-118">The two distinct `SELECT` queries that follow generate XML with a small difference in shape.</span></span>  
  
 <span data-ttu-id="36eda-119">第一個查詢會產生 XML，而 <`SalesPerson`> 及 <`SalesOrderHeader`> 會顯示為 <`SalesOrder`> 的同層級子系：</span><span class="sxs-lookup"><span data-stu-id="36eda-119">The first query generates XML in which <`SalesPerson`> and <`SalesOrderHeader`> appear as sibling children of <`SalesOrder`>:</span></span>  
  
```  
SELECT   
      (SELECT top 2 SalesOrderID, SalesPersonID, CustomerID,  
         (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
           from Sales.SalesOrderDetail  
            WHERE  SalesOrderDetail.SalesOrderID =   
                   SalesOrderHeader.SalesOrderID  
            FOR XML AUTO, TYPE)  
        FROM  Sales.SalesOrderHeader  
        WHERE SalesOrderHeader.SalesOrderID = SalesOrder.SalesOrderID  
        for xml auto, type),  
        (SELECT *   
         FROM  (SELECT SalesPersonID, EmployeeID  
              FROM Sales.SalesPerson, HumanResources.Employee  
              WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As   
                     SalesPerson  
         WHERE  SalesPerson.SalesPersonID = SalesOrder.SalesPersonID  
       FOR XML AUTO, TYPE)  
FROM (SELECT SalesOrderHeader.SalesOrderID, SalesOrderHeader.SalesPersonID  
      FROM Sales.SalesOrderHeader, Sales.SalesPerson  
      WHERE SalesOrderHeader.SalesPersonID = SalesPerson.SalesPersonID  
     ) as SalesOrder  
ORDER BY SalesOrder.SalesOrderID  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="36eda-120">在上一個查詢中，最外層 `SELECT` 陳述式會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="36eda-120">In the previous query, the outermost `SELECT` statement does the following:</span></span>  
  
-   <span data-ttu-id="36eda-121">查詢 `SalesOrder` 子句中指定的資料列集 `FROM`。</span><span class="sxs-lookup"><span data-stu-id="36eda-121">Queries the rowset, `SalesOrder`, specified in the `FROM` clause.</span></span> <span data-ttu-id="36eda-122">結果是具有一或多個 <`SalesOrder`> 元素的 XML。</span><span class="sxs-lookup"><span data-stu-id="36eda-122">The result is an XML with one or more <`SalesOrder`> elements.</span></span>  
  
-   <span data-ttu-id="36eda-123">指定 `AUTO` 模式和 `TYPE` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="36eda-123">Specifies `AUTO` mode and the `TYPE` directive.</span></span> <span data-ttu-id="36eda-124">`AUTO`模式會將查詢結果轉換為 XML，而指示詞會 `TYPE` 以類型傳回結果 `xml` 。</span><span class="sxs-lookup"><span data-stu-id="36eda-124">`AUTO` mode transforms the query result into XML, and the `TYPE` directive returns the result as `xml` type.</span></span>  
  
-   <span data-ttu-id="36eda-125">包括以逗號分隔的兩個巢狀 `SELECT` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="36eda-125">Includes two nested `SELECT` statements separated by a comma.</span></span> <span data-ttu-id="36eda-126">第一個巢狀 `SELECT` 陳述式會擷取銷售訂單資訊、標頭及詳細資料，而第二個巢狀 `SELECT` 陳述式會擷取銷售人員資訊。</span><span class="sxs-lookup"><span data-stu-id="36eda-126">The first nested `SELECT` retrieves sales order information, header and details, and the second nested `SELECT` statement retrieves salesperson information.</span></span>  
  
    -   <span data-ttu-id="36eda-127">擷取 `SELECT` 、 `SalesOrderID`與 `SalesPersonID`的 `CustomerID` 陳述式本身，包含另一個會傳回銷售訂單詳細資訊的巢狀 `SELECT ... FOR XML` 陳述式 (具有 `AUTO` 模式與 `TYPE` 指示詞)。</span><span class="sxs-lookup"><span data-stu-id="36eda-127">The `SELECT` statement that retrieves `SalesOrderID`, `SalesPersonID`, and `CustomerID` itself includes another nested `SELECT ... FOR XML` statement (with `AUTO` mode and `TYPE` directive) that returns sales order detail information.</span></span>  
  
 <span data-ttu-id="36eda-128">擷取銷售人員資訊的 `SELECT` 陳述式，會查詢以 `SalesPerson`子句建立的資料列集 `FROM` 。</span><span class="sxs-lookup"><span data-stu-id="36eda-128">The `SELECT` statement that retrieves the sales person information queries a rowset, `SalesPerson`, created in the `FROM` clause.</span></span> <span data-ttu-id="36eda-129">為了要使 `FOR XML` 查詢能夠運作，您必須對以 `FROM` 子句產生的匿名資料列集提供名稱。</span><span class="sxs-lookup"><span data-stu-id="36eda-129">For `FOR XML` queries to work, you must provide a name for the anonymous rowset generated in the `FROM` clause.</span></span> <span data-ttu-id="36eda-130">在此情況下，提供的名稱為 `SalesPerson`。</span><span class="sxs-lookup"><span data-stu-id="36eda-130">In this case, the name provided is `SalesPerson`.</span></span>  
  
 <span data-ttu-id="36eda-131">以下是部份結果：</span><span class="sxs-lookup"><span data-stu-id="36eda-131">This is the partial result:</span></span>  
  
```  
<SalesOrder>  
  <Sales.SalesOrderHeader SalesOrderID="43659" SalesPersonID="279" CustomerID="676">  
    <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="776" OrderQty="1" UnitPrice="2024.9940" />  
    <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="777" OrderQty="3" UnitPrice="2024.9940" />  
    <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="778" OrderQty="1" UnitPrice="2024.9940" />  
  </Sales.SalesOrderHeader>  
  <SalesPerson SalesPersonID="279" EmployeeID="279" />  
</SalesOrder>  
...  
```  
  
 <span data-ttu-id="36eda-132">以下查詢會產生相同的銷售訂單資訊，<`SalesPerson`> 在產生的 XML 中還會顯示為 <`SalesOrderDetail`> 的同層級：</span><span class="sxs-lookup"><span data-stu-id="36eda-132">The following query generates the same sales order information, except that in the resulting XML, the <`SalesPerson`> appears as a sibling of <`SalesOrderDetail`>:</span></span>  
  
```  
<SalesOrder>  
    <SalesOrderHeader ...>  
          <SalesOrderDetail .../>  
          <SalesOrderDetail .../>  
          ...  
          <SalesPerson .../>  
    </SalesOrderHeader>  
  
</SalesOrder>  
<SalesOrder>  
  ...  
</SalesOrder>  
```  
  
 <span data-ttu-id="36eda-133">此查詢如下：</span><span class="sxs-lookup"><span data-stu-id="36eda-133">This is the query:</span></span>  
  
```  
SELECT SalesOrderID, SalesPersonID, CustomerID,  
             (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
              from Sales.SalesOrderDetail  
              WHERE SalesOrderDetail.SalesOrderID = SalesOrderHeader.SalesOrderID  
              FOR XML AUTO, TYPE),  
              (SELECT *   
               FROM  (SELECT SalesPersonID, EmployeeID  
                    FROM Sales.SalesPerson, HumanResources.Employee  
                    WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As SalesPerson  
               WHERE  SalesPerson.SalesPersonID = SalesOrderHeader.SalesPersonID  
         FOR XML AUTO, TYPE)  
FROM Sales.SalesOrderHeader  
WHERE SalesOrderID=43659 or SalesOrderID=43660  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="36eda-134">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="36eda-134">This is the result:</span></span>  
  
```  
<Sales.SalesOrderHeader SalesOrderID="43659" SalesPersonID="279" CustomerID="676">  
  <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="776" OrderQty="1" UnitPrice="2024.9940" />  
  <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="777" OrderQty="3" UnitPrice="2024.9940" />  
  <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="778" OrderQty="1" UnitPrice="2024.9940" />  
  <SalesPerson SalesPersonID="279" EmployeeID="279" />  
</Sales.SalesOrderHeader>  
<Sales.SalesOrderHeader SalesOrderID="43660" SalesPersonID="279" CustomerID="117">  
  <Sales.SalesOrderDetail SalesOrderID="43660" ProductID="762" OrderQty="1" UnitPrice="419.4589" />  
  <Sales.SalesOrderDetail SalesOrderID="43660" ProductID="758" OrderQty="1" UnitPrice="874.7940" />  
  <SalesPerson SalesPersonID="279" EmployeeID="279" />  
</Sales.SalesOrderHeader>  
```  
  
 <span data-ttu-id="36eda-135">因為 `TYPE` 指示詞會以 `xml` 類型傳回查詢結果，所以您可以使用不同的 `xml` 資料類型方法查詢產生的 XML。</span><span class="sxs-lookup"><span data-stu-id="36eda-135">Because the `TYPE` directive returns a query result as `xml` type, you can query the resulting XML by using various `xml` data type methods.</span></span> <span data-ttu-id="36eda-136">如需詳細資訊，請參閱 [XML 資料類型方法](/sql/t-sql/xml/xml-data-type-methods)。</span><span class="sxs-lookup"><span data-stu-id="36eda-136">For more information, see [xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods).</span></span> <span data-ttu-id="36eda-137">在下列查詢中，請注意下列項目：</span><span class="sxs-lookup"><span data-stu-id="36eda-137">In the following query, note the following:</span></span>  
  
-   <span data-ttu-id="36eda-138">先前的查詢已加入 `FROM` 子句中。</span><span class="sxs-lookup"><span data-stu-id="36eda-138">The previous query is added in the `FROM` clause.</span></span> <span data-ttu-id="36eda-139">查詢結果會以資料表傳回。</span><span class="sxs-lookup"><span data-stu-id="36eda-139">The query result is returned as a table.</span></span> <span data-ttu-id="36eda-140">請注意新增的 `XmlCol` 別名。</span><span class="sxs-lookup"><span data-stu-id="36eda-140">Note the `XmlCol` alias that is added.</span></span>  
  
-   <span data-ttu-id="36eda-141">`SELECT` 子句會對 `XmlCol` 子句中傳回的 `FROM` 指定 XQuery。</span><span class="sxs-lookup"><span data-stu-id="36eda-141">The `SELECT` clause specifies an XQuery against the `XmlCol` returned in the `FROM` clause.</span></span> <span data-ttu-id="36eda-142">`query()` 資料類型的 `xml` 方法則用來指定 XQuery。</span><span class="sxs-lookup"><span data-stu-id="36eda-142">The `query()` method of the `xml` data type is used in specifying the XQuery.</span></span> <span data-ttu-id="36eda-143">如需詳細資訊，請參閱 [query&#40;&#41; 方法 &#40;xml 資料類型&#41;](/sql/t-sql/xml/query-method-xml-data-type)。</span><span class="sxs-lookup"><span data-stu-id="36eda-143">For more information, see [query&#40;&#41; Method &#40;xml Data Type&#41;](/sql/t-sql/xml/query-method-xml-data-type).</span></span>  
  
    ```  
    SELECT XmlCol.query('<Root> { /* } </Root>')  
    FROM (  
    SELECT SalesOrderID, SalesPersonID, CustomerID,  
                 (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
                  from Sales.SalesOrderDetail  
                  WHERE SalesOrderDetail.SalesOrderID = SalesOrderHeader.SalesOrderID  
                  FOR XML AUTO, TYPE),  
                  (SELECT *   
                   FROM  (SELECT SalesPersonID, EmployeeID  
                        FROM Sales.SalesPerson, HumanResources.Employee  
                        WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As SalesPerson  
                   WHERE  SalesPerson.SalesPersonID = SalesOrderHeader.SalesPersonID  
             FOR XML AUTO, TYPE)  
    FROM Sales.SalesOrderHeader  
    WHERE SalesOrderID='43659' or SalesOrderID='43660'  
    FOR XML AUTO, TYPE ) as T(XmlCol)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="36eda-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36eda-144">See Also</span></span>  
 [<span data-ttu-id="36eda-145">使用巢狀 FOR XML 查詢</span><span class="sxs-lookup"><span data-stu-id="36eda-145">Use Nested FOR XML Queries</span></span>](use-nested-for-xml-queries.md)  
  
  
