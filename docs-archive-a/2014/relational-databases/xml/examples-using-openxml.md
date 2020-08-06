---
title: 範例：使用 OPENXML | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ColPattern [XML in SQL Server]
- XML [SQL Server], mapping data
- OPENXML statement, about OPENXML statement
- overflow in XML document [SQL Server]
- mapping XML data [SQL Server]
- combining attribute-centric and element centric mapping
- unconsumed data
- attribute-centric mapping
- column patterns [XML in SQL Server]
- XML [SQL Server], overflow handling
- row patterns [XML in SQL Server]
- rowpattern [XML in SQL Server]
- flags parameter
- element-centric mapping [SQL Server]
- edge tables
ms.assetid: 689297f3-adb0-4d8d-bf62-cfda26210164
author: rothja
ms.author: jroth
ms.openlocfilehash: 09fc6ad073b12df2f9fbd8ebc6a59149f6154ced
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710473"
---
# <a name="examples-using-openxml"></a><span data-ttu-id="9eeb8-102">範例：使用 OPENXML</span><span class="sxs-lookup"><span data-stu-id="9eeb8-102">Examples: Using OPENXML</span></span>
  <span data-ttu-id="9eeb8-103">在此主題下的範例將說明如何使用 OPENXML 來建立 XML 文件的資料列集檢視。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-103">The examples in this topic show how OPENXML is used to create a rowset view of an XML document.</span></span> <span data-ttu-id="9eeb8-104">如需 OPENXML 語法的相關資訊，請參閱 [OPENXML &#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-104">For information about the syntax of OPENXML, see [OPENXML &#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql).</span></span> <span data-ttu-id="9eeb8-105">範例中將說明 OPENXML 的各個方面，但是不指定 OPENXML 的中繼屬性。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-105">The examples show all aspects of OPENXML, but do not specify metaproperties in OPENXML.</span></span> <span data-ttu-id="9eeb8-106">如需如何指定 OPENXML 的中繼屬性的詳細資訊，請參閱 [在 OPENXML 中指定中繼屬性](specify-metaproperties-in-openxml.md)。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-106">For more information about how to specify metaproperties in OPENXML, see [Specify Metaproperties in OPENXML](specify-metaproperties-in-openxml.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9eeb8-107">範例</span><span class="sxs-lookup"><span data-stu-id="9eeb8-107">Examples</span></span>  
 <span data-ttu-id="9eeb8-108">在擷取資料時， *rowpattern* 是用來識別 XML 文件中決定資料列的節點。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-108">In retrieving the data, *rowpattern* is used to identify the nodes in the XML document that determine the rows.</span></span> <span data-ttu-id="9eeb8-109">另外， *rowpattern* 是以 XPath 模式語言表示，該語言使用於 MSXML XPath 實作中。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-109">Additionally, *rowpattern* is expressed in the XPath pattern language that is used in the MSXML XPath implementation.</span></span> <span data-ttu-id="9eeb8-110">例如，如果模式結尾是元素或屬性，則會為 *rowpattern*所選取的每一個元素或屬性節點建立一個資料列。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-110">For example, if the pattern ends in an element or an attribute, a row is created for each element or attribute node that is selected by *rowpattern*.</span></span>  
  
 <span data-ttu-id="9eeb8-111">*flags* 值提供預設對應。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-111">The *flags* value provides default mapping.</span></span> <span data-ttu-id="9eeb8-112">若在 *SchemaDeclaration* 中未指定 *ColPattern*，則假設為 *flags* 中所指定的對應。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-112">If no *ColPattern* is specified in the *SchemaDeclaration*, the mapping specified in *flags* is assumed.</span></span> <span data-ttu-id="9eeb8-113">若在 *SchemaDeclaration* 中指定 *ColPattern* ，則略過 *flags*值。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-113">The *flags* value is ignored if *ColPattern* is specified in *SchemaDeclaration*.</span></span> <span data-ttu-id="9eeb8-114">指定的 *ColPattern* 將決定處理溢位和未使用資料的對應 (屬性中心或元素中心) 以及行為。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-114">The specified *ColPattern* determines the mapping, attribute-centric or element-centric, and also the behavior in dealing with overflow and unconsumed data.</span></span>  
  
### <a name="a-executing-a-simple-select-statement-with-openxml"></a><span data-ttu-id="9eeb8-115">A.</span><span class="sxs-lookup"><span data-stu-id="9eeb8-115">A.</span></span> <span data-ttu-id="9eeb8-116">以 OPENXML 執行簡單的 SELECT 陳述式</span><span class="sxs-lookup"><span data-stu-id="9eeb8-116">Executing a simple SELECT statement with OPENXML</span></span>  
 <span data-ttu-id="9eeb8-117">此範例中的 XML 文件是由 <`Customer`>、<`Order`> 和 <`OrderDetail`> 元素組成。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-117">The XML document in this example is made up of the <`Customer`>, <`Order`>, and <`OrderDetail`> elements.</span></span> <span data-ttu-id="9eeb8-118">OPENXML 陳述式所擷取的客戶資訊是來自於 XML 文件中的兩個資料行資料列集： **CustomerID** 和 **ContactName**。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-118">The OPENXML statement retrieves customer information in a two-column rowset, **CustomerID** and **ContactName**, from the XML document.</span></span>  
  
 <span data-ttu-id="9eeb8-119">首先，呼叫 **sp_xml_preparedocument** 預存程序以取得文件控制代碼。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-119">First, the **sp_xml_preparedocument** stored procedure is called to obtain a document handle.</span></span> <span data-ttu-id="9eeb8-120">接著將此文件控制代碼傳遞至 OPENXML。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-120">This document handle is passed to OPENXML.</span></span>  
  
 <span data-ttu-id="9eeb8-121">OPENXML 陳述式說明下列各項：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-121">The OPENXML statement illustrates the following:</span></span>  
  
-   <span data-ttu-id="9eeb8-122">*rowpattern* (/ROOT/Customer) 識別要處理的 <`Customer`> 節點。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-122">*rowpattern* (/ROOT/Customer) identifies the <`Customer`> nodes to process.</span></span>  
  
-   <span data-ttu-id="9eeb8-123">*flags* 參數值設為 **1** ，表示屬性中心的對應。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-123">The *flags* parameter value is set to **1** and indicates attribute-centric mapping.</span></span> <span data-ttu-id="9eeb8-124">因此，XML 屬性對應至 *SchemaDeclaration*中定義之資料列集的資料行。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-124">As a result, the XML attributes map to the columns in the rowset defined in *SchemaDeclaration*.</span></span>  
  
-   <span data-ttu-id="9eeb8-125">在 WITH 子句內的 *SchemaDeclaration*中，指定的 *ColName* 值與對應的 XML 屬性名稱相符。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-125">In *SchemaDeclaration*, in the WITH clause, the specified *ColName* values match the corresponding XML attribute names.</span></span> <span data-ttu-id="9eeb8-126">因此不會在 *SchemaDeclaration* 中指定 *ColPattern*參數。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-126">Therefore, the *ColPattern* parameter is not specified in *SchemaDeclaration*.</span></span>  
  
 <span data-ttu-id="9eeb8-127">然後，SELECT 陳述式擷取由 OPENXML 所提供之資料列集內的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-127">The SELECT statement then retrieves all the columns in the rowset provided by OPENXML.</span></span>  
  
```  
DECLARE @DocHandle int  
DECLARE @XmlDocument nvarchar(1000)  
SET @XmlDocument = N'<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order OrderID="10248" CustomerID="VINET" EmployeeID="5"   
          OrderDate="1996-07-04T00:00:00">  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order OrderID="10283" CustomerID="LILAS" EmployeeID="3"   
          OrderDate="1996-08-16T00:00:00">  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @DocHandle OUTPUT, @XmlDocument  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@DocHandle, '/ROOT/Customer',1)  
      WITH (CustomerID  varchar(10),  
            ContactName varchar(20))  
EXEC sp_xml_removedocument @DocHandle  
```  
  
 <span data-ttu-id="9eeb8-128">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-128">This is the result:</span></span>  
  
```  
CustomerID ContactName            
---------- --------------------   
VINET      Paul Henriot  
LILAS      Carlos Gonzlez  
```  
  
 <span data-ttu-id="9eeb8-129">由於 <`Customer`> 元素不具有任何子元素，若相同的 SELECT 陳述式以 *flags* 設為 **2** 來執行 (表示元素中心的對應)，則兩個客戶的 **CustomerID** 及 **ContactName** 值將以 NULL 傳回。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-129">Because the <`Customer`> elements do not have any subelements, if the same SELECT statement is executed with *flags* set to **2** to indicate element-centric mapping, the values of **CustomerID** and **ContactName** for both the customers are returned as NULL.</span></span>  
  
 <span data-ttu-id="9eeb8-130">@xmlDocument 也可以是 **ML** 類型或 **(n)varchar(max)** 類型。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-130">The @xmlDocument can also be of **xml** type or of **(n)varchar(max)** type.</span></span>  
  
 <span data-ttu-id="9eeb8-131">如果 XML 文件中的 <`CustomerID`> 和 <`ContactName`> 是子元素，元素中心的對應會擷取這些值。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-131">If <`CustomerID`> and <`ContactName`> in the XML document are subelements, the element-centric mapping retrieves the values.</span></span>  
  
```  
DECLARE @XmlDocumentHandle int  
DECLARE @XmlDocument nvarchar(1000)  
SET @XmlDocument = N'<ROOT>  
<Customer>  
   <CustomerID>VINET</CustomerID>  
   <ContactName>Paul Henriot</ContactName>  
   <Order OrderID="10248" CustomerID="VINET" EmployeeID="5" OrderDate="1996-07-04T00:00:00">  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer>     
   <CustomerID>LILAS</CustomerID>  
   <ContactName>Carlos Gonzlez</ContactName>  
   <Order OrderID="10283" CustomerID="LILAS" EmployeeID="3" OrderDate="1996-08-16T00:00:00">  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @XmlDocumentHandle OUTPUT, @XmlDocument  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT    *  
FROM      OPENXML (@XmlDocumentHandle, '/ROOT/Customer',2)  
           WITH (CustomerID  varchar(10),  
                 ContactName varchar(20))  
EXEC sp_xml_removedocument @XmlDocumentHandle  
```  
  
 <span data-ttu-id="9eeb8-132">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-132">This is the result:</span></span>  
  
```  
CustomerID ContactName            
---------- --------------------   
VINET      Paul Henriot  
LILAS      Carlos Gonzlez  
```  
  
 <span data-ttu-id="9eeb8-133">請注意， **sp_xml_preparedocument** 傳回的文件控制代碼是對批次的期間有效，而不是對工作階段有效。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-133">Note that the document handle returned by **sp_xml_preparedocument** is valid for the duration of the batch and not the session.</span></span>  
  
### <a name="b-specifying-colpattern-for-mapping-between-rowset-columns-and-the-xml-attributes-and-elements"></a><span data-ttu-id="9eeb8-134">B.</span><span class="sxs-lookup"><span data-stu-id="9eeb8-134">B.</span></span> <span data-ttu-id="9eeb8-135">指定 ColPattern 來進行資料列集資料行與 XML 屬性和元素之間的對應</span><span class="sxs-lookup"><span data-stu-id="9eeb8-135">Specifying ColPattern for mapping between rowset columns and the XML attributes and elements</span></span>  
 <span data-ttu-id="9eeb8-136">此範例將說明如何在選用的 *ColPattern* 參數中指定 XPath 模式，以提供資料列集資料行與 XML 屬性和元素之間的對應。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-136">This example shows how the XPath pattern is specified in the optional *ColPattern* parameter to provide mapping between rowset columns and the XML attributes and elements.</span></span>  
  
 <span data-ttu-id="9eeb8-137">此範例中的 XML 文件是由 <`Customer`>、<`Order`> 和 <`OrderDetail`> 元素組成。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-137">The XML document in this example is made up of the <`Customer`>, <`Order`>, and <`OrderDetail`> elements.</span></span> <span data-ttu-id="9eeb8-138">OPENXML 陳述式所擷取的客戶及訂單資訊是來自於 XML 文件中的資料列集 (**CustomerID**、 **OrderDate**、 **ProdID**及 **Qty**)。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-138">The OPENXML statement retrieves customer and order information as a rowset (**CustomerID**, **OrderDate**, **ProdID**, and **Qty**) from the XML document.</span></span>  
  
 <span data-ttu-id="9eeb8-139">首先，呼叫 **sp_xml_preparedocument** 預存程序以取得文件控制代碼。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-139">First, the **sp_xml_preparedocument** stored procedure is called to obtain a document handle.</span></span> <span data-ttu-id="9eeb8-140">接著將此文件控制代碼傳遞至 OPENXML。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-140">This document handle is passed to OPENXML.</span></span>  
  
 <span data-ttu-id="9eeb8-141">OPENXML 陳述式說明下列各項：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-141">The OPENXML statement illustrates the following:</span></span>  
  
-   <span data-ttu-id="9eeb8-142">*rowpattern* (/ROOT/Customer/Order/OrderDetail) 識別要處理的 <`OrderDetail`> 節點。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-142">*rowpattern* (/ROOT/Customer/Order/OrderDetail) identifies the <`OrderDetail`> nodes to process.</span></span>  
  
 <span data-ttu-id="9eeb8-143">舉例來說， *flags* 參數值設為 **2** ，表示元素中心的對應。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-143">For illustration, the *flags* parameter value is set to **2** and indicates element-centric mapping.</span></span> <span data-ttu-id="9eeb8-144">不過， *ColPattern* 中指定的對應會覆寫此對應。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-144">However, the mapping specified in *ColPattern* overwrites this mapping.</span></span> <span data-ttu-id="9eeb8-145">也就是說， *ColPattern* 中所指定的 XPath 模式會將資料列集的資料行對應到屬性。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-145">That is, the XPath pattern specified in *ColPattern* maps the columns in the rowset to attributes.</span></span> <span data-ttu-id="9eeb8-146">這會導致屬性中心的對應。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-146">This results in attribute-centric mapping.</span></span>  
  
 <span data-ttu-id="9eeb8-147">在 WITH 子句內的 *SchemaDeclaration*中，亦使用 *ColName* 與 *ColType* 參數來指定 *ColPattern* 。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-147">In *SchemaDeclaration*, in the WITH clause, *ColPattern* is also specified with the *ColName* and *ColType* parameters.</span></span> <span data-ttu-id="9eeb8-148">選用的 *ColPattern* 是指定的 XPath 模式，它表示下列各項：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-148">The optional *ColPattern* is the XPath pattern specified and indicates the following:</span></span>  
  
-   <span data-ttu-id="9eeb8-149">資料列集的 **OrderID**、**CustomerID** 和 **OrderDate** 資料行對應到 *rowpattern* 所識別節點的父系之屬性，且 *rowpattern* 識別 <`OrderDetail`> 節點。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-149">The **OrderID**, **CustomerID**, and **OrderDate** columns in the rowset map to the attributes of the parent of the nodes identified by *rowpattern*, and *rowpattern* identifies the <`OrderDetail`> nodes.</span></span> <span data-ttu-id="9eeb8-150">因此，**CustomerID** 和 **OrderDate** 資料行對應到 <`Order`> 元素的 **CustomerID** 和 **OrderDate** 屬性。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-150">Therefore, the **CustomerID** and **OrderDate** columns map to **CustomerID** and **OrderDate** attributes of the <`Order`> element.</span></span>  
  
-   <span data-ttu-id="9eeb8-151">資料列集的 **ProdID** 及 **Qty** 資料行對應至 **rowpattern** 中所識別節點的 **ProductID** 及 *Quantity*屬性。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-151">The **ProdID** and **Qty** columns in the rowset map to the **ProductID** and **Quantity** attributes of the nodes identified in *rowpattern*.</span></span>  
  
 <span data-ttu-id="9eeb8-152">然後，SELECT 陳述式擷取由 OPENXML 所提供之資料列集內的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-152">The SELECT statement then retrieves all the columns in the rowset provided by OPENXML.</span></span>  
  
```  
DECLARE @XmlDocumentHandle int  
DECLARE @XmlDocument nvarchar(1000)  
SET @XmlDocument = N'<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order OrderID="10248" CustomerID="VINET" EmployeeID="5"   
           OrderDate="1996-07-04T00:00:00">  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order OrderID="10283" CustomerID="LILAS" EmployeeID="3"   
           OrderDate="1996-08-16T00:00:00">  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @XmlDocumentHandle OUTPUT, @XmlDocument  
-- Execute a SELECT stmt using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@XmlDocumentHandle, '/ROOT/Customer/Order/OrderDetail',2)  
WITH (OrderID     int         '../@OrderID',  
      CustomerID  varchar(10) '../@CustomerID',  
      OrderDate   datetime    '../@OrderDate',  
      ProdID      int         '@ProductID',  
      Qty         int         '@Quantity')  
EXEC sp_xml_removedocument @XmlDocumentHandle  
```  
  
 <span data-ttu-id="9eeb8-153">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-153">This is the result:</span></span>  
  
```  
OrderID CustomerID        OrderDate          ProdID    Qty  
-------------------------------------------------------------  
10248    VINET     1996-07-04 00:00:00.000     11       12  
10248    VINET     1996-07-04 00:00:00.000     42       10  
10283    LILAS     1996-08-16 00:00:00.000     72        3  
```  
  
 <span data-ttu-id="9eeb8-154">指定為 *ColPattern* 的 XPath 模式也可以指定為將 XML 元素對應到資料列集資料行。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-154">The XPath pattern specified as *ColPattern* can also be specified to map the XML elements to the rowset columns.</span></span> <span data-ttu-id="9eeb8-155">這會導致元素中心的對應。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-155">This results in element-centric mapping.</span></span> <span data-ttu-id="9eeb8-156">在下列範例中，XML 文件 <`CustomerID`> 和 <`OrderDate`> 是 <`Orders`> 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-156">In the following example, the XML document <`CustomerID`> and <`OrderDate`> are subelements of the <`Orders`> element.</span></span> <span data-ttu-id="9eeb8-157">由於 *ColPattern* 覆寫了 *flags* 參數中所指定的對應，因此在 OPENXML 中並未指定 *flags* 參數。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-157">Because *ColPattern* overwrites the mapping specified in the *flags* parameter, the *flags* parameter is not specified in OPENXML.</span></span>  
  
```  
DECLARE @docHandle int  
DECLARE @XmlDocument nvarchar(1000)  
SET @XmlDocument = N'<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order EmployeeID="5" >  
      <OrderID>10248</OrderID>  
      <CustomerID>VINET</CustomerID>  
      <OrderDate>1996-07-04T00:00:00</OrderDate>  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order  EmployeeID="3" >  
      <OrderID>10283</OrderID>  
      <CustomerID>LILAS</CustomerID>  
      <OrderDate>1996-08-16T00:00:00</OrderDate>  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @docHandle OUTPUT, @XmlDocument  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@docHandle, '/ROOT/Customer/Order/OrderDetail')  
WITH (CustomerID  varchar(10)   '../CustomerID',  
      OrderDate   datetime      '../OrderDate',  
      ProdID      int           '@ProductID',  
      Qty         int           '@Quantity')  
EXEC sp_xml_removedocument @docHandle  
```  
  
### <a name="c-combining-attribute-centric-and-element-centric-mapping"></a><span data-ttu-id="9eeb8-158">C.</span><span class="sxs-lookup"><span data-stu-id="9eeb8-158">C.</span></span> <span data-ttu-id="9eeb8-159">結合以屬性為主及以元素為主的對應</span><span class="sxs-lookup"><span data-stu-id="9eeb8-159">Combining attribute-centric and element-centric mapping</span></span>  
 <span data-ttu-id="9eeb8-160">在此範例中， *flags* 參數設為 **3** ，表示將套用屬性中心和元素中心的兩種對應。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-160">In this example, the *flags* parameter is set to **3** and indicates that both attribute-centric and element-centric mapping will be applied.</span></span> <span data-ttu-id="9eeb8-161">在此情況下，會先套用屬性中心的對應，然後所有尚未處理的資料行則套用元素中心的對應。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-161">In this case, the attribute-centric mapping is applied first, and then element-centric mapping is applied for all the columns not yet dealt with.</span></span>  
  
```  
DECLARE @docHandle int  
DECLARE @XmlDocument nvarchar(1000)  
SET @XmlDocument =N'<ROOT>  
<Customer CustomerID="VINET"  >  
     <ContactName>Paul Henriot</ContactName>  
   <Order OrderID="10248" CustomerID="VINET" EmployeeID="5"   
          OrderDate="1996-07-04T00:00:00">  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" >   
     <ContactName>Carlos Gonzlez</ContactName>  
   <Order OrderID="10283" CustomerID="LILAS" EmployeeID="3"   
          OrderDate="1996-08-16T00:00:00">  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @docHandle OUTPUT, @XmlDocument  
  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@docHandle, '/ROOT/Customer',3)  
      WITH (CustomerID  varchar(10),  
            ContactName varchar(20))  
EXEC sp_xml_removedocument @docHandle  
```  
  
 <span data-ttu-id="9eeb8-162">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-162">This is the result</span></span>  
  
```  
CustomerID ContactName            
---------- --------------------   
VINET      Paul Henriot  
LILAS      Carlos Gonzlez  
```  
  
 <span data-ttu-id="9eeb8-163">屬性中心的對應套用於 **CustomerID**。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-163">The attribute-centric mapping is applied for **CustomerID**.</span></span> <span data-ttu-id="9eeb8-164"><`Customer`> 元素中沒有 **ContactName** 屬性。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-164">There is no **ContactName** attribute in the <`Customer`> element.</span></span> <span data-ttu-id="9eeb8-165">因此，套用元素中心的對應。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-165">Therefore, element-centric mapping is applied.</span></span>  
  
### <a name="d-specifying-the-text-xpath-function-as-colpattern"></a><span data-ttu-id="9eeb8-166">D.</span><span class="sxs-lookup"><span data-stu-id="9eeb8-166">D.</span></span> <span data-ttu-id="9eeb8-167">指定 text() XPath 函數為 ColPattern</span><span class="sxs-lookup"><span data-stu-id="9eeb8-167">Specifying the text() XPath function as ColPattern</span></span>  
 <span data-ttu-id="9eeb8-168">此範例中的 XML 文件是由 <`Customer`> 和 <`Order`> 元素組成。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-168">The XML document in this example is made up of the <`Customer`> and <`Order`> elements.</span></span> <span data-ttu-id="9eeb8-169">OPENXML 陳述式擷取的資料列集是由 <`Order`> 元素的 **oid** 屬性、*rowpattern* 所識別的節點父系的識別碼以及元素內容的分葉值字串所組成。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-169">The OPENXML statement retrieves a rowset that is made up of the **oid** attribute from the <`Order`> element, the ID of the parent of the node identified by *rowpattern*, and the leaf-value string of the element content.</span></span>  
  
 <span data-ttu-id="9eeb8-170">首先，呼叫 **sp_xml_preparedocument** 預存程序以取得文件控制代碼。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-170">First, the **sp_xml_preparedocument** stored procedure is called to obtain a document handle.</span></span> <span data-ttu-id="9eeb8-171">接著將此文件控制代碼傳遞至 OPENXML。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-171">This document handle is passed to OPENXML.</span></span>  
  
 <span data-ttu-id="9eeb8-172">OPENXML 陳述式說明下列各項：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-172">The OPENXML statement illustrates the following:</span></span>  
  
-   <span data-ttu-id="9eeb8-173">*rowpattern* (/root/Customer/Order) 識別要處理的 <`Order`> 節點。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-173">*rowpattern* (/root/Customer/Order) identifies the <`Order`> nodes to process.</span></span>  
  
-   <span data-ttu-id="9eeb8-174">*flags* 參數值設為 **1** ，表示屬性中心的對應。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-174">The *flags* parameter value is set to **1** and indicates attribute-centric mapping.</span></span> <span data-ttu-id="9eeb8-175">因此，XML 屬性對應至 *SchemaDeclaration*中所定義的資料列集資料行。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-175">As a result, the XML attributes map to the rowset columns defined in *SchemaDeclaration*.</span></span>  
  
-   <span data-ttu-id="9eeb8-176">在 WITH 子句內的 *SchemaDeclaration* 中，資料列集資料行名稱 **oid** 和 **amount** 符合相對應的 XML 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-176">In *SchemaDeclaration* in the WITH clause, the **oid** and **amount** rowset column names match the corresponding XML attribute names.</span></span> <span data-ttu-id="9eeb8-177">因此未指定 *ColPattern* 參數。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-177">Therefore, the *ColPattern* parameter is not specified.</span></span> <span data-ttu-id="9eeb8-178">針對資料列集中的 **comment** 資料行， XPath 函數 **text()** 指定為 *ColPattern*。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-178">For the **comment** column in the rowset, the XPath function, **text()**, is specified as *ColPattern*.</span></span> <span data-ttu-id="9eeb8-179">這將會覆寫 *flags*中所指定之屬性中心的對應，而資料行將包含元素內容的分葉值字串。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-179">This overwrites the attribute-centric mapping specified in *flags*, and the column contains the leaf-value string of the element content.</span></span>  
  
 <span data-ttu-id="9eeb8-180">然後，SELECT 陳述式擷取由 OPENXML 所提供之資料列集內的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-180">The SELECT statement then retrieves all the columns in the rowset provided by OPENXML.</span></span>  
  
```  
DECLARE @docHandle int  
DECLARE @xmlDocument nvarchar(1000)  
--sample XML document  
SET @xmlDocument =N'<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was very satisfied  
      </Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue   
             white red">  
            <Urgency>Important</Urgency>  
            Happy Customer.  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @docHandle OUTPUT, @xmlDocument  
  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@docHandle, '/root/Customer/Order', 1)  
     WITH (oid     char(5),   
           amount  float,   
           comment ntext 'text()')  
EXEC sp_xml_removedocument @docHandle  
```  
  
 <span data-ttu-id="9eeb8-181">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-181">This is the result:</span></span>  
  
```  
oid   amount        comment  
----- -----------   -----------------------------  
O1    3.5           NULL  
O2    13.4          Customer was very satisfied  
O3    100.0         Happy Customer.  
O4    10000.0       NULL  
```  
  
### <a name="e-specifying-tablename-in-the-with-clause"></a><span data-ttu-id="9eeb8-182">E.</span><span class="sxs-lookup"><span data-stu-id="9eeb8-182">E.</span></span> <span data-ttu-id="9eeb8-183">在 WITH 子句中指定 TableName</span><span class="sxs-lookup"><span data-stu-id="9eeb8-183">Specifying TableName in the WITH clause</span></span>  
 <span data-ttu-id="9eeb8-184">此範例在 WITH 子句中指定 *TableName* ，而不是在 *SchemaDeclaration*中。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-184">This example specifies *TableName* in the WITH clause instead of *SchemaDeclaration*.</span></span> <span data-ttu-id="9eeb8-185">若您具有所需結構的資料表，且不需要資料行模式 ( *ColPattern* 參數)，這會是相當有用的方式。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-185">This is useful if you have a table that has the structure you want and no column patterns, *ColPattern* parameter, are required.</span></span>  
  
 <span data-ttu-id="9eeb8-186">此範例中的 XML 文件是由 <`Customer`> 和 <`Order`> 元素組成。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-186">The XML document in this example is made up of the <`Customer`> and <`Order`> elements.</span></span> <span data-ttu-id="9eeb8-187">OPENXML 陳述式所擷取的訂單資訊是來自於 XML 文件中的三個資料行資料列集 (**oid**、 **date**及 **amount**)。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-187">The OPENXML statement retrieves order information in a three-column rowset (**oid**, **date**, and **amount**) from the XML document.</span></span>  
  
 <span data-ttu-id="9eeb8-188">首先，呼叫 **sp_xml_preparedocument** 預存程序以取得文件控制代碼。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-188">First, the **sp_xml_preparedocument** stored procedure is called to obtain a document handle.</span></span> <span data-ttu-id="9eeb8-189">接著將此文件控制代碼傳遞至 OPENXML。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-189">This document handle is passed to OPENXML.</span></span>  
  
 <span data-ttu-id="9eeb8-190">OPENXML 陳述式說明下列各項：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-190">The OPENXML statement illustrates the following:</span></span>  
  
-   <span data-ttu-id="9eeb8-191">*rowpattern* (/root/Customer/Order) 識別要處理的 <`Order`> 節點。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-191">*rowpattern* (/root/Customer/Order) identifies the <`Order`> nodes to process.</span></span>  
  
-   <span data-ttu-id="9eeb8-192">WITH 子句中沒有 *SchemaDeclaration* 。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-192">There is no *SchemaDeclaration* in the WITH clause.</span></span> <span data-ttu-id="9eeb8-193">相反地，有指定資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-193">Instead, a table name is specified.</span></span> <span data-ttu-id="9eeb8-194">因此，資料表結構描述是做為資料列集結構描述使用。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-194">Therefore, the table schema is used as the rowset schema.</span></span>  
  
-   <span data-ttu-id="9eeb8-195">*flags* 參數值設為 **1** ，表示屬性中心的對應。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-195">The *flags* parameter value is set to **1** and indicates attribute-centric mapping.</span></span> <span data-ttu-id="9eeb8-196">因此，由 *rowpattern*識別的元素屬性是對應到相同名稱的資料列集資料行。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-196">Therefore, attributes of the elements, identified by *rowpattern*, map to the rowset columns with the same name.</span></span>  
  
 <span data-ttu-id="9eeb8-197">然後，SELECT 陳述式擷取由 OPENXML 所提供之資料列集內的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-197">The SELECT statement then retrieves all the columns in the rowset provided by OPENXML.</span></span>  
  
```  
-- Create a test table. This table schema is used by OPENXML as the  
-- rowset schema.  
CREATE TABLE T1(oid char(5), date datetime, amount float)  
GO  
DECLARE @docHandle int  
DECLARE @xmlDocument nvarchar(1000)  
-- Sample XML document  
SET @xmlDocument =N'<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was very   
             satisfied</Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue   
             white red">  
          <Urgency>Important</Urgency>  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>'  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @docHandle OUTPUT, @xmlDocument  
  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@docHandle, '/root/Customer/Order', 1)  
     WITH T1  
EXEC sp_xml_removedocument @docHandle  
```  
  
 <span data-ttu-id="9eeb8-198">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-198">This is the result:</span></span>  
  
```  
oid   date                        amount  
----- --------------------------- ----------  
O1    1996-01-20 00:00:00.000     3.5  
O2    1997-04-30 00:00:00.000     13.4  
O3    1999-07-14 00:00:00.000     100.0  
O4    1996-01-20 00:00:00.000     10000.0  
```  
  
### <a name="f-obtaining-the-result-in-an-edge-table-format"></a><span data-ttu-id="9eeb8-199">F.</span><span class="sxs-lookup"><span data-stu-id="9eeb8-199">F.</span></span> <span data-ttu-id="9eeb8-200">取得邊緣資料表格式的結果</span><span class="sxs-lookup"><span data-stu-id="9eeb8-200">Obtaining the result in an edge table format</span></span>  
 <span data-ttu-id="9eeb8-201">在此範例中，OPENXML 陳述式未指定 WITH 子句。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-201">In this example, the WITH clause is not specified in the OPENXML statement.</span></span> <span data-ttu-id="9eeb8-202">因此，OPENXML 所產生的資料列集具有邊緣資料表格式。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-202">As a result, the rowset generated by OPENXML has an edge table format.</span></span> <span data-ttu-id="9eeb8-203">SELECT 陳述式以邊緣資料表傳回所有資料行。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-203">The SELECT statement returns all the columns in the edge table.</span></span>  
  
 <span data-ttu-id="9eeb8-204">此範例中的範例 XML 文件是由 <`Customer`>、<`Order`> 和 <`OrderDetail`> 元素組成。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-204">The sample XML document in the example is made up of the <`Customer`>, <`Order`>, and <`OrderDetail`> elements.</span></span>  
  
 <span data-ttu-id="9eeb8-205">首先，呼叫 **sp_xml_preparedocument** 預存程序以取得文件控制代碼。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-205">First, the **sp_xml_preparedocument** stored procedure is called to obtain a document handle.</span></span> <span data-ttu-id="9eeb8-206">接著將此文件控制代碼傳遞至 OPENXML。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-206">This document handle is passed to OPENXML.</span></span>  
  
 <span data-ttu-id="9eeb8-207">OPENXML 陳述式說明下列各項：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-207">The OPENXML statement illustrates the following:</span></span>  
  
-   <span data-ttu-id="9eeb8-208">*rowpattern* (/ROOT/Customer) 識別要處理的 <`Customer`> 節點。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-208">*rowpattern* (/ROOT/Customer) identifies the <`Customer`> nodes to process.</span></span>  
  
-   <span data-ttu-id="9eeb8-209">未提供 WITH 子句。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-209">The WITH clause is not provided.</span></span> <span data-ttu-id="9eeb8-210">因此，OPENXML 以邊緣資料表格式傳回資料列集。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-210">Therefore, OPENXML returns the rowset in an edge table format.</span></span>  
  
 <span data-ttu-id="9eeb8-211">然後，SELECT 陳述式擷取邊緣資料表中的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-211">The SELECT statement then retrieves all the columns in the edge table.</span></span>  
  
```  
DECLARE @docHandle int  
DECLARE @xmlDocument nvarchar(1000)  
SET @xmlDocument = N'<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order CustomerID="VINET" EmployeeID="5" OrderDate=  
           "1996-07-04T00:00:00">  
      <OrderDetail OrderID="10248" ProductID="11" Quantity="12"/>  
      <OrderDetail OrderID="10248" ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order CustomerID="LILAS" EmployeeID="3" OrderDate=  
           "1996-08-16T00:00:00">  
      <OrderDetail OrderID="10283" ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @docHandle OUTPUT, @xmlDocument  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@docHandle, '/ROOT/Customer')  
  
EXEC sp_xml_removedocument @docHandle  
```  
  
 <span data-ttu-id="9eeb8-212">結果是以邊緣資料表傳回。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-212">The result is returned as an edge table.</span></span> <span data-ttu-id="9eeb8-213">您可以針對邊緣資料表寫入查詢以取得資訊。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-213">You can write queries against the edge table to obtain information.</span></span> <span data-ttu-id="9eeb8-214">例如：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-214">For example:</span></span>  
  
-   <span data-ttu-id="9eeb8-215">以下查詢傳回文件中 **Customer** 節點的數目。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-215">The following query returns the number of **Customer** nodes in the document.</span></span> <span data-ttu-id="9eeb8-216">由於未指定 WITH 子句，因此 OPENXML 傳回邊緣資料表。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-216">Because the WITH clause is not specified, OPENXML returns an edge table.</span></span> <span data-ttu-id="9eeb8-217">SELECT 陳述式查詢邊緣資料表。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-217">The SELECT statement queries the edge table.</span></span>  
  
    ```  
    SELECT count(*)  
    FROM OPENXML(@docHandle, '/')  
    WHERE localname = 'Customer'  
    ```  
  
-   <span data-ttu-id="9eeb8-218">下列查詢傳回元素類型之 XML 節點的本機名稱。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-218">The following query returns the local names of XML nodes of element type.</span></span>  
  
    ```  
    SELECT distinct localname   
    FROM OPENXML(@docHandle, '/')   
    WHERE nodetype = 1   
    ORDER BY localname  
    ```  
  
### <a name="g-specifying-rowpattern-ending-with-an-attribute"></a><span data-ttu-id="9eeb8-219">G.</span><span class="sxs-lookup"><span data-stu-id="9eeb8-219">G.</span></span> <span data-ttu-id="9eeb8-220">指定 rowpattern 結束於屬性</span><span class="sxs-lookup"><span data-stu-id="9eeb8-220">Specifying rowpattern ending with an attribute</span></span>  
 <span data-ttu-id="9eeb8-221">此範例中的 XML 文件是由 <`Customer`>、<`Order`> 和 <`OrderDetail`> 元素組成。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-221">The XML document in this example is made up of the <`Customer`>, <`Order`>, and <`OrderDetail`> elements.</span></span> <span data-ttu-id="9eeb8-222">OPENXML 陳述式所擷取的訂單詳細資訊是來自於 XML 文件中的三的資料行資料列集 (**ProductID**、 **Quantity**和 **OrderID**)。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-222">The OPENXML statement retrieves information about the order details in a three-column rowset (**ProductID**, **Quantity**, and **OrderID**) from the XML document.</span></span>  
  
 <span data-ttu-id="9eeb8-223">首先，呼叫 **sp_xml_preparedocument** 預存程序以取得文件控制代碼。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-223">First, the **sp_xml_preparedocument** is called to obtain a document handle.</span></span> <span data-ttu-id="9eeb8-224">接著將此文件控制代碼傳遞至 OPENXML。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-224">This document handle is passed to OPENXML.</span></span>  
  
 <span data-ttu-id="9eeb8-225">OPENXML 陳述式說明下列各項：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-225">The OPENXML statement illustrates the following:</span></span>  
  
-   <span data-ttu-id="9eeb8-226">*rowpattern* (/ROOT/Customer/Order/OrderDetail/\@ProductID) 結束於 XML 屬性 ( **ProductID**)。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-226">*rowpattern* (/ROOT/Customer/Order/OrderDetail/\@ProductID) ends with an XML attribute, **ProductID**.</span></span> <span data-ttu-id="9eeb8-227">在結果資料列集中，為每個在 XML 文件中選取的屬性節點建立資料列。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-227">In the resulting rowset, a row is created for each attribute node selected in the XML document.</span></span>  
  
-   <span data-ttu-id="9eeb8-228">在此範例中，未指定 *flags* 參數。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-228">In this example, the *flags* parameter is not specified.</span></span> <span data-ttu-id="9eeb8-229">相反地，由 *ColPattern* 參數指定對應。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-229">Instead, the mappings are specified by the *ColPattern* parameter.</span></span>  
  
 <span data-ttu-id="9eeb8-230">在 WITH 子句內的 *SchemaDeclaration* 中，亦使用 *ColName* 與 *ColType* 參數來指定 *ColPattern* 。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-230">In *SchemaDeclaration* in the WITH clause, *ColPattern* is also specified with the *ColName* and *ColType* parameters.</span></span> <span data-ttu-id="9eeb8-231">選用的 *ColPattern* 是指定的 XPath 模式，它表示下列各項：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-231">The optional *ColPattern* is the XPath pattern specified to indicate the following:</span></span>  
  
-   <span data-ttu-id="9eeb8-232">針對資料列集內的**ProdID**資料行指定為 *ColPattern* 的 XPath 模式 ( **.** ) 識別內容節點，即目前節點。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-232">The XPath pattern (**.**) specified as *ColPattern* for the **ProdID** column in the rowset identifies the context node, current node.</span></span> <span data-ttu-id="9eeb8-233">根據所指定的 *rowpattern*，這是 <`OrderDetail`> 元素的 **ProductID** 屬性。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-233">As per the *rowpattern* specified, it is the **ProductID** attribute of the <`OrderDetail`> element.</span></span>  
  
-   <span data-ttu-id="9eeb8-234">針對資料列集內的 **Qty** 資料行所指定的 *ColPattern*、 **../\@Quantity**，識別內容節點 \<ProductID> 之父節點 <`OrderDetail`> 的 **Quantity** 屬性。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-234">The *ColPattern*, **../\@Quantity**, specified for the **Qty** column in the rowset identifies the **Quantity** attribute of the parent, <`OrderDetail`>, node of the context node, \<ProductID>.</span></span>  
  
-   <span data-ttu-id="9eeb8-235">同樣地，針對資料列集內的 **OID** 資料行所指定的 *ColPattern*、 **../../\@OrderID**，識別內容節點的父節點之父系 <`Order`> 的 **OrderID** 屬性。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-235">Similarly, the *ColPattern*, **../../\@OrderID**, specified for the **OID** column in the rowset identifies the **OrderID** attribute of the parent, <`Order`>, of the parent node of the context node.</span></span> <span data-ttu-id="9eeb8-236">父節點是 <`OrderDetail`>，內容節點是 <`ProductID`>。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-236">The parent node is <`OrderDetail`>, and the context node is <`ProductID`>.</span></span>  
  
 <span data-ttu-id="9eeb8-237">然後，SELECT 陳述式擷取由 OPENXML 所提供之資料列集內的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-237">The SELECT statement then retrieves all the columns in the rowset provided by OPENXML.</span></span>  
  
```  
DECLARE @docHandle int  
DECLARE @xmlDocument nvarchar(1000)  
--Sample XML document  
SET @xmlDocument =N'<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order OrderID="10248" CustomerID="VINET" EmployeeID="5" OrderDate=  
           "1996-07-04T00:00:00">  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order OrderID="10283" CustomerID="LILAS" EmployeeID="3" OrderDate=  
           "1996-08-16T00:00:00">  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @docHandle OUTPUT, @xmlDocument  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@docHandle, '/ROOT/Customer/Order/OrderDetail/@ProductID')  
       WITH ( ProdID  int '.',  
              Qty     int '../@Quantity',  
              OID     int '../../@OrderID')  
EXEC sp_xml_removedocument @docHandle  
```  
  
 <span data-ttu-id="9eeb8-238">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-238">This is the result:</span></span>  
  
```  
ProdID      Qty         OID  
----------- ----------- -------   
11          12          10248  
42          10          10248  
72          3           10283  
```  
  
### <a name="h-specifying-an-xml-document-that-has-multiple-text-nodes"></a><span data-ttu-id="9eeb8-239">H.</span><span class="sxs-lookup"><span data-stu-id="9eeb8-239">H.</span></span> <span data-ttu-id="9eeb8-240">指定含有多個文字節點的 XML 文件</span><span class="sxs-lookup"><span data-stu-id="9eeb8-240">Specifying an XML document that has multiple text nodes</span></span>  
 <span data-ttu-id="9eeb8-241">若在 XML 文件中具有多個文字節點，含有 *ColPattern\*\*\*text()*\* 的 SELECT 陳述式將只傳回第一個文字節點，而不是所有節點。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-241">If you have multiple text nodes in an XML document, a SELECT statement with a *ColPattern*, **text()**, returns only the first text node, instead of all of them.</span></span> <span data-ttu-id="9eeb8-242">例如：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-242">For example:</span></span>  
  
```  
DECLARE @h int  
EXEC sp_xml_preparedocument @h OUTPUT,  
         N'<root xmlns:a="urn:1">  
           <a:Elem abar="asdf">  
             T<a>a</a>U  
           </a:Elem>  
         </root>',  
         '<ns xmlns:b="urn:1" />'  
  
SELECT * FROM openxml(@h, '/root/b:Elem')  
      WITH (Col1 varchar(20) 'text()')  
EXEC sp_xml_removedocument @h  
```  
  
 <span data-ttu-id="9eeb8-243">SELECT 陳述式傳回的結果為 **T** ，而非 **TaU**。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-243">The SELECT statement returns **T** as the result, and not **TaU**.</span></span>  
  
### <a name="i-specifying-the-xml-data-type-in-the-with-clause"></a><span data-ttu-id="9eeb8-244">I.</span><span class="sxs-lookup"><span data-stu-id="9eeb8-244">I.</span></span> <span data-ttu-id="9eeb8-245">在 WITH 子句中指定 xml 資料類型</span><span class="sxs-lookup"><span data-stu-id="9eeb8-245">Specifying the xml data type in the WITH clause</span></span>  
 <span data-ttu-id="9eeb8-246">在 WITH 子句中，對應到 **xml** 資料類型資料行的資料行模式，不論具類型或不具類型，都必須傳回空序列或元素的序列、處理指示、文字節點和註解。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-246">In the WITH clause, a column pattern that is mapped to the **xml** data type column, whether typed or untyped, must return either an empty sequence or a sequence of elements, processing instructions, text nodes, and comments.</span></span> <span data-ttu-id="9eeb8-247">此資料轉換成 **xml** 資料類型。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-247">The data is cast to an **xml** data type.</span></span>  
  
 <span data-ttu-id="9eeb8-248">在下列範例中，WITH 子句中的資料表結構描述宣告包含 **xml** 類型資料行。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-248">In the following example, the table schema declaration in the WITH clause includes **xml** type columns.</span></span>  
  
```  
DECLARE @h int  
DECLARE @x xml  
set @x = '<Root>  
  <row id="1"><lname>Duffy</lname>  
   <Address>  
            <Street>111 Maple</Street>  
            <City>Seattle</City>  
   </Address>  
  </row>  
  <row id="2"><lname>Wang</lname>  
   <Address>  
            <Street>222 Pine</Street>  
            <City>Bothell</City>  
   </Address>  
  </row>  
</Root>'  
  
EXEC sp_xml_preparedocument @h output, @x  
SELECT *  
FROM   OPENXML (@h, '/Root/row', 10)  
      WITH (id int '@id',  
  
            lname    varchar(30),  
            xmlname  xml 'lname',  
            OverFlow xml '@mp:xmltext')  
EXEC sp_xml_removedocument @h  
```  
  
 <span data-ttu-id="9eeb8-249">特別是，您要將 **xml** 類型變數 (\@x) 傳遞至 **sp_xml_preparedocument()** 函式。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-249">Specifically, you are passing an **xml** type variable (\@x) to the **sp_xml_preparedocument()** function.</span></span>  
  
 <span data-ttu-id="9eeb8-250">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-250">This is the result:</span></span>  
  
```  
id  lname   xmlname                   OverFlow  
--- ------- ------------------------------ -------------------------------  
1   Duffy   <lname>Duffy</lname>  <row><Address>  
                                   <Street>111 Maple</Street>  
                                   <City>Seattle</City>  
                                  </Address></row>  
2   Wang    <lname>Wang</lname>   <row><Address>  
                                    <Street>222 Pine</Street>  
                                    <City>Bothell</City>  
                                   </Address></row>  
```  
  
 <span data-ttu-id="9eeb8-251">請注意結果的下列各項：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-251">Note the following from the result:</span></span>  
  
-   <span data-ttu-id="9eeb8-252">若為 **varchar(30)** 類型的 **lname** 資料行，會從對應的 <`lname`> 元素擷取其值。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-252">For the **lname** column of **varchar(30)** type, its value is retrieved from the corresponding <`lname`> element.</span></span>  
  
-   <span data-ttu-id="9eeb8-253">若為 **xml** 類型的 **xmlname** 資料行，會傳回相同名稱元素作為它的值。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-253">For the **xmlname** column of **xml** type, the same name element is returned as its value.</span></span>  
  
-   <span data-ttu-id="9eeb8-254">此旗標設為 10。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-254">The flag is set to 10.</span></span> <span data-ttu-id="9eeb8-255">10 表示 2 + 8，其中 2 指示元素中心的對應，8 表示只有未耗用的 XML 資料才加入至 WITH 子句中定義的 OverFlow 資料行。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-255">The 10 means 2 + 8, where 2 indicates element-centric mapping and 8 indicates that only unconsumed XML data should be added to the OverFlow column defined in the WITH clause.</span></span> <span data-ttu-id="9eeb8-256">如果您將旗標設為 2，則整個 XML 文件會複製到在 WITH 子句中指定的 OverFlow 資料行。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-256">If you set the flag to 2, the whole XML document is copied to the OverFlow column that is specified in the WITH clause.</span></span>  
  
-   <span data-ttu-id="9eeb8-257">假如 WITH 子句中的資料行是具類型的 XML 資料行，但 XML 執行個體不符合此結構描述，則會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-257">In case the column in the WITH clause is a typed XML column and the XML instance does not confirm to the schema, an error is returned.</span></span>  
  
### <a name="j-retrieving-individual-values-from-multivalued-attributes"></a><span data-ttu-id="9eeb8-258">J.</span><span class="sxs-lookup"><span data-stu-id="9eeb8-258">J.</span></span> <span data-ttu-id="9eeb8-259">從多值屬性中擷取個別的值</span><span class="sxs-lookup"><span data-stu-id="9eeb8-259">Retrieving individual values from multivalued attributes</span></span>  
 <span data-ttu-id="9eeb8-260">XML 文件可以擁有多重值的屬性。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-260">An XML document can have attributes that are multivalued.</span></span> <span data-ttu-id="9eeb8-261">例如， **IDREFS** 屬性可為多重值。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-261">For example, the **IDREFS** attribute can be multivalued.</span></span> <span data-ttu-id="9eeb8-262">在 XML 文件中，多重值的屬性值是指定為字串，並以空格區隔其值。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-262">In an XML document, the multivalued attribute values are specified as a string, with the values separated by a space.</span></span> <span data-ttu-id="9eeb8-263">在下列 XML 文件中，\<Student> 元素的 **attends** 屬性與 \<Class> 的 **attendedBy** 屬性為多重值。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-263">In the following XML document, the **attends** attribute of the \<Student> element and the **attendedBy** attribute of \<Class> are multivalued.</span></span> <span data-ttu-id="9eeb8-264">從多重值 XML 屬性中擷取個別的值，並將每個值儲存於資料庫中的個別資料列需要額外的工作。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-264">Retrieving individual values from a multivalued XML attribute and storing each value in a separate row in the database requires additional work.</span></span> <span data-ttu-id="9eeb8-265">此範例顯示其處理過程。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-265">This example shows the process.</span></span>  
  
 <span data-ttu-id="9eeb8-266">此範例 XML 文件由下列元素構成：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-266">This sample XML document is made up of the following elements:</span></span>  
  
-   \<Student>  
  
     <span data-ttu-id="9eeb8-267">**id** (學生識別碼)、 **name**與 **attends** 屬性。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-267">The **id** (student ID), **name**, and **attends** attributes.</span></span> <span data-ttu-id="9eeb8-268">**attends** 屬性為多重值屬性。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-268">The **attends** attribute is a multivalued attribute.</span></span>  
  
-   \<Class>  
  
     <span data-ttu-id="9eeb8-269">**id** (班級識別碼)、 **name**與 **attendedBy** 屬性。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-269">The **id** (class ID), **name**, and **attendedBy** attributes.</span></span> <span data-ttu-id="9eeb8-270">**attendedBy** 屬性為多重值屬性。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-270">The **attendedBy** attribute is a multivalued attribute.</span></span>  
  
 <span data-ttu-id="9eeb8-271">\<Student> 中的 **attends** 屬性與 \<Class> 中的 **attendedBy** 屬性代表學生與類別資料表之間的 **m:n** 關聯性。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-271">The **attends** attribute in \<Student> and the **attendedBy** attribute in \<Class> represent a **m:n** relationship between the Student and Class tables.</span></span> <span data-ttu-id="9eeb8-272">一位學生可以選擇多種學科而一種學科可以收授多位學生。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-272">A student can take many classes and a class can have many students.</span></span>  
  
 <span data-ttu-id="9eeb8-273">假設您要切割此文件並將文件儲存於資料庫，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-273">Assume that you want to shred this document and save it in the database as shown in the following:</span></span>  
  
-   <span data-ttu-id="9eeb8-274">將 \<Student> 資料儲存於 Students 資料表中。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-274">Save the \<Student> data in the Students table.</span></span>  
  
-   <span data-ttu-id="9eeb8-275">將 \<Class> 資料儲存於 Courses 資料表中。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-275">Save the \<Class> data in the Courses table.</span></span>  
  
-   <span data-ttu-id="9eeb8-276">將 Student 與 Class 之間的 **m:n** 關聯性資料儲存於 CourseAttendence 資料表中。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-276">Save the **m:n** relationship data, between Student and Class, in the CourseAttendence table.</span></span> <span data-ttu-id="9eeb8-277">取出這些值需要額外的工作。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-277">Additional work is required to extract the values.</span></span> <span data-ttu-id="9eeb8-278">若要擷取此資訊並將之儲存於資料表，請使用下列預存程序：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-278">To retrieve this information and store it in the table, use these stored procedures:</span></span>  
  
    -   <span data-ttu-id="9eeb8-279">**Insert_Idrefs_Values**</span><span class="sxs-lookup"><span data-stu-id="9eeb8-279">**Insert_Idrefs_Values**</span></span>  
  
         <span data-ttu-id="9eeb8-280">將學科識別碼與學生識別碼的值插入 CourseAttendence 資料表。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-280">Inserts the values of course ID and student ID in the CourseAttendence table.</span></span>  
  
    -   <span data-ttu-id="9eeb8-281">**Extract_idrefs_values**</span><span class="sxs-lookup"><span data-stu-id="9eeb8-281">**Extract_idrefs_values**</span></span>  
  
         <span data-ttu-id="9eeb8-282">從每個 \<Course> 元素中擷取個別的學生識別碼。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-282">Extracts the individual student IDs from each \<Course> element.</span></span> <span data-ttu-id="9eeb8-283">使用邊緣資料表來擷取這些值。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-283">An edge table is used to retrieve these values.</span></span>  
  
 <span data-ttu-id="9eeb8-284">以下為其步驟：</span><span class="sxs-lookup"><span data-stu-id="9eeb8-284">Here are the steps:</span></span>  
  
```  
-- Create these tables:  
DROP TABLE CourseAttendance  
DROP TABLE Students  
DROP TABLE Courses  
GO  
CREATE TABLE Students(  
                id   varchar(5) primary key,  
                name varchar(30)  
                )  
GO  
CREATE TABLE Courses(  
               id       varchar(5) primary key,  
               name     varchar(30),  
               taughtBy varchar(5)  
)  
GO  
CREATE TABLE CourseAttendance(  
             id         varchar(5) references Courses(id),  
             attendedBy varchar(5) references Students(id),  
             constraint CourseAttendance_PK primary key (id, attendedBy)  
)  
go  
-- Create these stored procedures:  
DROP PROCEDURE f_idrefs  
GO  
CREATE PROCEDURE f_idrefs  
    @t      varchar(500),  
    @idtab  varchar(50),  
    @id     varchar(5)  
AS  
DECLARE @sp int  
DECLARE @att varchar(5)  
SET @sp = 0  
WHILE (LEN(@t) > 0)  
BEGIN   
    SET @sp = CHARINDEX(' ', @t+ ' ')  
    SET @att = LEFT(@t, @sp-1)  
    EXEC('INSERT INTO '+@idtab+' VALUES ('''+@id+''', '''+@att+''')')  
    SET @t = SUBSTRING(@t+ ' ', @sp+1, LEN(@t)+1-@sp)  
END  
Go  
  
DROP PROCEDURE fill_idrefs  
GO  
CREATE PROCEDURE fill_idrefs   
    @xmldoc     int,  
    @xpath      varchar(100),  
    @from       varchar(50),  
    @to         varchar(50),  
    @idtable    varchar(100)  
AS  
DECLARE @t varchar(500)  
DECLARE @id varchar(5)  
  
/* Temporary edge table */  
SELECT *   
INTO #TempEdge   
FROM OPENXML(@xmldoc, @xpath)  
  
DECLARE fillidrefs_cursor CURSOR FOR  
    SELECT CAST(iv.text AS nvarchar(200)) AS id,  
           CAST(av.text AS nvarchar(4000)) AS refs  
    FROM   #TempEdge c, #TempEdge i,  
           #TempEdge iv, #TempEdge a, #TempEdge av  
    WHERE  c.id = i.parentid  
    AND    UPPER(i.localname) = UPPER(@from)  
    AND    i.id = iv.parentid  
    AND    c.id = a.parentid  
    AND    UPPER(a.localname) = UPPER(@to)  
    AND    a.id = av.parentid  
  
OPEN fillidrefs_cursor  
FETCH NEXT FROM fillidrefs_cursor INTO @id, @t  
WHILE (@@FETCH_STATUS <> -1)  
BEGIN  
    IF (@@FETCH_STATUS <> -2)  
    BEGIN  
        execute f_idrefs @t, @idtable, @id  
    END  
    FETCH NEXT FROM fillidrefs_cursor INTO @id, @t  
END  
CLOSE fillidrefs_cursor  
DEALLOCATE fillidrefs_cursor  
Go  
-- This is the sample document that is shredded and the data is stored in the preceding tables.  
DECLARE @h int  
EXECUTE sp_xml_preparedocument @h OUTPUT, N'<Data>  
  <Student id = "s1" name = "Student1"  attends = "c1 c3 c6"  />  
  <Student id = "s2" name = "Student2"  attends = "c2 c4" />  
  <Student id = "s3" name = "Student3"  attends = "c2 c4 c6" />  
  <Student id = "s4" name = "Student4"  attends = "c1 c3 c5" />  
  <Student id = "s5" name = "Student5"  attends = "c1 c3 c5 c6" />  
  <Student id = "s6" name = "Student6" />  
  
  <Class id = "c1" name = "Intro to Programming"   
         attendedBy = "s1 s4 s5" />  
  <Class id = "c2" name = "Databases"   
         attendedBy = "s2 s3" />  
  <Class id = "c3" name = "Operating Systems"   
         attendedBy = "s1 s4 s5" />  
  <Class id = "c4" name = "Networks" attendedBy = "s2 s3" />  
  <Class id = "c5" name = "Algorithms and Graphs"   
         attendedBy =  "s4 s5"/>  
  <Class id = "c6" name = "Power and Pragmatism"   
         attendedBy = "s1 s3 s5" />  
</Data>'  
  
INSERT INTO Students SELECT * FROM OPENXML(@h, '//Student') WITH Students  
  
INSERT INTO Courses SELECT * FROM OPENXML(@h, '//Class') WITH Courses  
/* Using the edge table */  
EXECUTE fill_idrefs @h, '//Class', 'id', 'attendedby', 'CourseAttendance'  
  
SELECT * FROM Students  
SELECT * FROM Courses  
SELECT * FROM CourseAttendance  
  
EXECUTE sp_xml_removedocument @h  
```  
  
### <a name="k-retrieving-binary-from-base64-encoded-data-in-xml"></a><span data-ttu-id="9eeb8-285">K.</span><span class="sxs-lookup"><span data-stu-id="9eeb8-285">K.</span></span> <span data-ttu-id="9eeb8-286">從 XML 的 Base64 編碼資料中擷取二進位資料</span><span class="sxs-lookup"><span data-stu-id="9eeb8-286">Retrieving binary from base64 encoded data in XML</span></span>  
 <span data-ttu-id="9eeb8-287">二進位資料常常使用 Base64 編碼而包含在 XML 中。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-287">Binary data is frequently included in XML using base64 encoding.</span></span> <span data-ttu-id="9eeb8-288">當您使用 OPENXML 來切割此 XML 時，會接收到 Base64 編碼資料。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-288">When you shred this XML by using OPENXML, you receive the base64 encoded data.</span></span> <span data-ttu-id="9eeb8-289">此範例示範如何將 Base64 編碼資料轉換回二進位。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-289">This example shows how you can convert the base64 encoded data back to binary.</span></span>  
  
-   <span data-ttu-id="9eeb8-290">以範例二進位資料建立資料表。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-290">Create a table with sample binary data.</span></span>  
  
-   <span data-ttu-id="9eeb8-291">使用 FOR XML 查詢和 BINARY BASE64 選項來建構將二進位資料編碼成 base64 的 XML。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-291">Use a FOR XML query and the BINARY BASE64 option to construct XML that has the binary data encoded as base64.</span></span>  
  
-   <span data-ttu-id="9eeb8-292">使用 OPENXML 來切割 XML。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-292">Shred the XML by using OPENXML.</span></span> <span data-ttu-id="9eeb8-293">OPENXML 傳回的資料將為 Base64 編碼資料。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-293">The data returned by OPENXML will be base64 encoded data.</span></span> <span data-ttu-id="9eeb8-294">接下來，呼叫 .value 函數將此資料轉換回二進位。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-294">Next, call the .value function to convert it back to binary.</span></span>  
  
```  
CREATE TABLE T (Col1 int primary key, Col2 varbinary(100))  
go  
-- Insert sample binary data  
INSERT T VALUES(1, 0x1234567890)   
go  
 -- Create test XML document that has base64 encoded binary data (use FOR XML query and specify BINARY BASE64 option)  
SELECT * FROM T  
FOR XML AUTO, BINARY BASE64  
go  
-- result  
-- <T Col1="1" Col2="EjRWeJA="/>  
  
-- Now shredd the sample XML using OPENXML.   
-- Call the .value function to convert   
-- the base64 encoded data returned by OPENXML to binary.  
DECLARE @h int ;  
EXEC sp_xml_preparedocument @h OUTPUT, '<T Col1="1" Col2="EjRWeJA="/>' ;  
SELECT Col1,   
CAST('<binary>' + Col2 + '</binary>' AS XML).value('.', 'varbinary(max)') AS BinaryCol   
FROM openxml(@h, '/T')   
WITH (Col1 integer, Col2 varchar(max)) ;  
EXEC sp_xml_removedocument @h ;  
GO  
```  
  
 以下是結果。 <span data-ttu-id="9eeb8-296">傳回的二進位資料是資料表 T 的原始二進位資料。</span><span class="sxs-lookup"><span data-stu-id="9eeb8-296">The binary data returned is the original binary data in table T.</span></span>  
  
```  
Col1        BinaryCol  
----------- ---------------------  
1           0x1234567890  
```  
  
## <a name="see-also"></a><span data-ttu-id="9eeb8-297">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9eeb8-297">See Also</span></span>  
 <span data-ttu-id="9eeb8-298">[sp_xml_preparedocument &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9eeb8-298">[sp_xml_preparedocument &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql) </span></span>  
 <span data-ttu-id="9eeb8-299">[sp_xml_removedocument &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9eeb8-299">[sp_xml_removedocument &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql) </span></span>  
 <span data-ttu-id="9eeb8-300">[OPENXML &#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9eeb8-300">[OPENXML &#40;Transact-SQL&#41;](/sql/t-sql/functions/openxml-transact-sql) </span></span>  
 [<span data-ttu-id="9eeb8-301">OPENXML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9eeb8-301">OPENXML &#40;SQL Server&#41;</span></span>](openxml-sql-server.md)  
  
  
