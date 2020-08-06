---
title: 搭配 FOR XML 使用 AUTO 模式 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, AUTO mode
- ELEMENTS option
- FOR XML AUTO mode
- AUTO FOR XML mode
ms.assetid: 7140d656-1d42-4f01-a533-5251429f4450
author: rothja
ms.author: jroth
ms.openlocfilehash: 232cc046667c6d31cb9657a7abdc862204507d23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596565"
---
# <a name="use-auto-mode-with-for-xml"></a><span data-ttu-id="c0dc2-102">搭配 FOR XML 使用 AUTO 模式</span><span class="sxs-lookup"><span data-stu-id="c0dc2-102">Use AUTO Mode with FOR XML</span></span>
  <span data-ttu-id="c0dc2-103">如同 [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md)中所述，AUTO 模式會將查詢結果當作巢狀 XML 元素傳回。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-103">As described in [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md), AUTO mode returns query results as nested XML elements.</span></span> <span data-ttu-id="c0dc2-104">這對於從查詢結果產生出來的 XML 外觀，並未提供很大的控制權。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-104">This does not provide much control over the shape of the XML generated from a query result.</span></span> <span data-ttu-id="c0dc2-105">如果您想要產生簡單的階層，AUTO 模式查詢會很有用。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-105">The AUTO mode queries are useful if you want to generate simple hierarchies.</span></span> <span data-ttu-id="c0dc2-106">不過， [搭配 FOR XML 使用 EXPLICIT 模式](use-explicit-mode-with-for-xml.md) 和 [搭配 FOR XML 使用 PATH 模式](use-path-mode-with-for-xml.md) 提供更多控制權和彈性來從查詢結果決定 XML 的形狀。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-106">However, [Use EXPLICIT Mode with FOR XML](use-explicit-mode-with-for-xml.md) and [Use PATH Mode with FOR XML](use-path-mode-with-for-xml.md) provide more control and flexibility in deciding the shape of the XML from a query result.</span></span>  
  
 <span data-ttu-id="c0dc2-107">FROM 子句中的每個資料表都至少有一資料行是列在 SELECT 子句中，這些資料表是以 XML 元素表示。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-107">Each table in the FROM clause, from which at least one column is listed in the SELECT clause, is represented as an XML element.</span></span> <span data-ttu-id="c0dc2-108">若在 FOR XML 子句中指定選用性的 ELEMENTS 選項，SELECT 子句中所列的資料行就會對應至屬性或子元素。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-108">The columns listed in the SELECT clause are mapped to attributes or subelements, if the optional ELEMENTS option is specified in the FOR XML clause.</span></span>  
  
 <span data-ttu-id="c0dc2-109">所產生之 XML 中的 XML 階層 (巢狀元素)，是依據 SELECT 子句中指定資料行所識別的資料表順序。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-109">The XML hierarchy, nesting of the elements, in the resulting XML is based on the order of tables identified by the columns specified in the SELECT clause.</span></span> <span data-ttu-id="c0dc2-110">因此，在 SELECT 子句中指定的資料行名稱順序是很重要的。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-110">Therefore, the order in which column names are specified in the SELECT clause is significant.</span></span> <span data-ttu-id="c0dc2-111">所識別的左邊第一個資料表，會形成所產生之 XML 文件的最上層元素。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-111">The first, leftmost table that is identified forms the top element in the resulting XML document.</span></span> <span data-ttu-id="c0dc2-112">由 SELECT 陳述式之資料行所識別的左邊第二個資料表，則形成最上層元素中的子元素，以此類推。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-112">The second leftmost table, identified by columns in the SELECT statement, forms a subelement within the top element, and so on.</span></span>  
  
 <span data-ttu-id="c0dc2-113">如果 SELECT 子句中列出的資料行名稱是來自 SELECT 子句先前指定之資料行所識別的資料表，這時會加入該資料行，做為已建立之元素的屬性，而不是開啟新的階層架構層級。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-113">If a column name listed in the SELECT clause is from a table that is already identified by a previously specified column in the SELECT clause, the column is added as an attribute of the element already created, instead of opening a new level of hierarchy.</span></span> <span data-ttu-id="c0dc2-114">而如果指定了 ELEMENTS 選項，便會加入資料行做為屬性。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-114">If the ELEMENTS option is specified, the column is added as an attribute.</span></span>  
  
 <span data-ttu-id="c0dc2-115">例如，執行以下的查詢：</span><span class="sxs-lookup"><span data-stu-id="c0dc2-115">For example, execute this query:</span></span>  
  
```  
SELECT Cust.CustomerID,   
       OrderHeader.CustomerID,  
       OrderHeader.SalesOrderID,   
       OrderHeader.Status,  
       Cust.CustomerType  
FROM Sales.Customer Cust, Sales.SalesOrderHeader OrderHeader  
WHERE Cust.CustomerID = OrderHeader.CustomerID  
ORDER BY Cust.CustomerID  
FOR XML AUTO  
```  
  
 <span data-ttu-id="c0dc2-116">以下是部份結果：</span><span class="sxs-lookup"><span data-stu-id="c0dc2-116">This is the partial result:</span></span>  
  
```  
<Cust CustomerID="1" CustomerType="S">  
  <OrderHeader CustomerID="1" SalesOrderID="43860" Status="5" />  
  <OrderHeader CustomerID="1" SalesOrderID="44501" Status="5" />  
  <OrderHeader CustomerID="1" SalesOrderID="45283" Status="5" />  
  <OrderHeader CustomerID="1" SalesOrderID="46042" Status="5" />  
</Cust>  
...  
```  
  
 <span data-ttu-id="c0dc2-117">請注意 SELECT 子句中的下列各項：</span><span class="sxs-lookup"><span data-stu-id="c0dc2-117">Note the following in the SELECT clause:</span></span>  
  
-   <span data-ttu-id="c0dc2-118">CustomerID 會參考 Cust 資料表。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-118">The CustomerID references the Cust table.</span></span> <span data-ttu-id="c0dc2-119">因此，會建立 <`Cust`> 元素，並加入 CustomerID 做為其屬性。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-119">Therefore, a <`Cust`> element is created and CustomerID is added as its attribute.</span></span>  
  
-   <span data-ttu-id="c0dc2-120">接著，OrderHeader.CustomerID、OrderHeader.SaleOrderID 及 OrderHeader.Status 這三個資料行會參考 OrderHeader 資料表。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-120">Next, three columns, OrderHeader.CustomerID, OrderHeader.SaleOrderID, and OrderHeader.Status, reference the OrderHeader table.</span></span> <span data-ttu-id="c0dc2-121">因此，會加入 <`OrderHeader`> 元素做為 <`Cust`> 元素的子元素，並加入這三個資料行，做為 <`OrderHeader`> 的屬性。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-121">Therefore, an <`OrderHeader`> element is added as a subelement of the <`Cust`> element and the three columns are added as attributes of <`OrderHeader`>.</span></span>  
  
-   <span data-ttu-id="c0dc2-122">接下來，Cust.CustomerType 資料行又會參考已由 Cust.CustomerID 資料行所識別的 Cust 資料表。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-122">Next, the Cust.CustomerType column again references the Cust table that was already identified by the Cust.CustomerID column.</span></span> <span data-ttu-id="c0dc2-123">因此並未建立任何新元素。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-123">Therefore, no new element is created.</span></span> <span data-ttu-id="c0dc2-124">反之，會將 CustomerType 屬性加入先前所建立的 <`Cust`> 元素。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-124">Instead, the CustomerType attribute is added to the <`Cust`> element that was previously created.</span></span>  
  
-   <span data-ttu-id="c0dc2-125">查詢會為資料表名稱指定別名。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-125">The query specifies aliases for the table names.</span></span> <span data-ttu-id="c0dc2-126">這些別名會以對應的元素名稱來顯示。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-126">These aliases appear as corresponding element names.</span></span>  
  
-   <span data-ttu-id="c0dc2-127">若要將所有子系集合在一個父系之下，則需要 ORDER BY。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-127">ORDER BY is required to group all children under one parent.</span></span>  
  
 <span data-ttu-id="c0dc2-128">此查詢和上一個查詢類似，不同的是 SELECT 子句會將 OrderHeader 資料表中的資料行，指定在 Cust 資料表中的資料行之前。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-128">This query is similar to the previous one, except the SELECT clause specifies columns in the OrderHeader table before the columns in the Cust table.</span></span> <span data-ttu-id="c0dc2-129">因此，會先建立 <`OrderHeader`> 元素，然後再加入 <`Cust`> 子元素。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-129">Therefore, first <`OrderHeader`> element is created and then the <`Cust`> child element is added to it.</span></span>  
  
```  
select OrderHeader.CustomerID,  
       OrderHeader.SalesOrderID,   
       OrderHeader.Status,  
       Cust.CustomerID,   
       Cust.CustomerType  
from Sales.Customer Cust, Sales.SalesOrderHeader OrderHeader  
where Cust.CustomerID = OrderHeader.CustomerID  
for xml auto  
```  
  
 <span data-ttu-id="c0dc2-130">以下是部份結果：</span><span class="sxs-lookup"><span data-stu-id="c0dc2-130">This is the partial result:</span></span>  
  
```  
<OrderHeader CustomerID="1" SalesOrderID="43860" Status="5">  
  <Cust CustomerID="1" CustomerType="S" />  
</OrderHeader>  
...  
```  
  
 <span data-ttu-id="c0dc2-131">若將 ELEMENTS 選項加入 FOR XML 子句，則會傳回元素中心的 XML。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-131">If the ELEMENTS option is added in the FOR XML clause, element-centric XML is returned.</span></span>  
  
```  
SELECT Cust.CustomerID,   
       OrderHeader.CustomerID,  
       OrderHeader.SalesOrderID,   
       OrderHeader.Status,  
       Cust.CustomerType  
FROM Sales.Customer Cust, Sales.SalesOrderHeader OrderHeader  
WHERE Cust.CustomerID = OrderHeader.CustomerID  
ORDER BY Cust.CustomerID  
FOR XML AUTO, ELEMENTS  
```  
  
 <span data-ttu-id="c0dc2-132">以下是部份結果：</span><span class="sxs-lookup"><span data-stu-id="c0dc2-132">This is the partial result:</span></span>  
  
```  
<Cust>  
  <CustomerID>1</CustomerID>  
  <CustomerType>S</CustomerType>  
  <OrderHeader>  
    <CustomerID>1</CustomerID>  
    <SalesOrderID>43860</SalesOrderID>  
    <Status>5</Status>  
  </OrderHeader>  
   ...  
</Cust>  
...  
```  
  
 <span data-ttu-id="c0dc2-133">在此查詢中，建立 \<Cust> 元素時，會一一比較資料列中的 CustomerID 值，因為 CustomerID 是資料表的主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-133">In this query, the CustomerID values are compared from one row to the next in creating the \<Cust> elements, because CustomerID is the primary key of the table.</span></span> <span data-ttu-id="c0dc2-134">若未將 CustomerID 識別成資料表的主索引鍵，則會一一比較資料列中的所有資料行值 (在此查詢中是 CustomerID、CustomerType)。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-134">If CustomerID is not identified as the primary key for the table, all the column values (CustomerID, CustomerType in this query) are compared from one row to the next.</span></span> <span data-ttu-id="c0dc2-135">若值有所差異，就會將新的 \<Cust> 元素加入 XML。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-135">If the values differ, a new \<Cust> element is added to the XML.</span></span>  
  
 <span data-ttu-id="c0dc2-136">在比較這些資料行的值時，如果所要比較的任何資料行中具有 **text**、 **ntext**、 **image**或 **xml**類型，FOR XML 就會認定該值是不同的 (即使該值可能是相同的)，而不加以比較。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-136">When comparing these column values, if any of the columns to be compared are of type **text**, **ntext**, **image**, or **xml**, FOR XML assumes that the values are different and not compared, even though they may be the same.</span></span> <span data-ttu-id="c0dc2-137">這是因為不支援比較大型物件。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-137">This is because comparing large objects is not supported.</span></span> <span data-ttu-id="c0dc2-138">針對所選取的每個資料列，都會將元素加入結果中。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-138">Elements are added to the result for each row selected.</span></span> <span data-ttu-id="c0dc2-139">請注意， **(n)varchar(max)** 及 **varbinary(max)** 的資料行會進行比較。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-139">Note that columns of **(n)varchar(max)** and **varbinary(max)** are compared.</span></span>  
  
 <span data-ttu-id="c0dc2-140">當 SELECT 子句中的資料行無法與 FROM 子句中所識別的任何資料表建立關聯 (例如：彙總資料行或計算資料行)，在清單中發現該資料行時，就會將其加入至最深之巢狀層級中的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-140">When a column in the SELECT clause cannot be associated with any of the tables identified in the FROM clause, as in the case of an aggregate column or computed column, the column is added in the XML document in the deepest nesting level in place when it is encountered in the list.</span></span> <span data-ttu-id="c0dc2-141">若該資料行是出現在 SELECT 子句中的第一個資料行，則會將該資料行新增至最上層元素。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-141">If such a column appears as the first column in the SELECT clause, the column is added to the top element.</span></span>  
  
 <span data-ttu-id="c0dc2-142">若在 SELECT 子句中指定星號 (\*) 萬用字元，就會根據查詢引擎所傳回的資料列順序，以上述同樣的方式來決定巢狀作業。</span><span class="sxs-lookup"><span data-stu-id="c0dc2-142">If the asterisk (\*) wildcard character is specified in the SELECT clause, the nesting is determined in the same way as previously described, based on the order that the rows are returned by the query engine.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c0dc2-143">本節內容</span><span class="sxs-lookup"><span data-stu-id="c0dc2-143">In This Section</span></span>  
 <span data-ttu-id="c0dc2-144">下列主題提供有關 AUTO 模式的詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="c0dc2-144">The following topics provide more information about AUTO mode:</span></span>  
  
-   [<span data-ttu-id="c0dc2-145">使用 BINARY BASE64 選項</span><span class="sxs-lookup"><span data-stu-id="c0dc2-145">Use the BINARY BASE64 Option</span></span>](use-the-binary-base64-option.md)  
  
-   [<span data-ttu-id="c0dc2-146">用來形成傳回之 XML 的 AUTO 模式啟發式方法</span><span class="sxs-lookup"><span data-stu-id="c0dc2-146">AUTO Mode Heuristics in Shaping Returned XML</span></span>](auto-mode-heuristics-in-shaping-returned-xml.md)  
  
-   [<span data-ttu-id="c0dc2-147">範例：使用 AUTO 模式</span><span class="sxs-lookup"><span data-stu-id="c0dc2-147">Examples: Using AUTO Mode</span></span>](examples-using-auto-mode.md)  
  
## <a name="see-also"></a><span data-ttu-id="c0dc2-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0dc2-148">See Also</span></span>  
 <span data-ttu-id="c0dc2-149">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c0dc2-149">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="c0dc2-150">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c0dc2-150">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
