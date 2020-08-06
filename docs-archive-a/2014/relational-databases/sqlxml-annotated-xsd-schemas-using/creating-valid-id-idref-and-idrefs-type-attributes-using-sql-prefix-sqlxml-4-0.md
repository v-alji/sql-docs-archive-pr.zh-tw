---
title: 使用 sql： prefix 建立有效的 ID、IDREF 和 IDREFS 類型屬性 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- IDREFS relationships [SQLXML]
- annotated XSD schemas, ID type attribute
- IDREF type attribute [SQLXML]
- annotated XSD schemas, IDREFS type attribute
- ID type attribute [SQLXML]
- sql:prefix
- prefix annotation
- IDREF relationships [SQLXML]
- IDREFS type attribute [SQLXML]
- annotated XSD schemas, IDREF type attribute
- ID relationships [SQLXML]
ms.assetid: 1c7f77d3-81f3-4820-bb63-c4aaa4ea9aa1
author: rothja
ms.author: jroth
ms.openlocfilehash: cb9e63bebd0cebbfeed75ea5cbe2ea62683234fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595904"
---
# <a name="creating-valid-id-idref-and-idrefs-type-attributes-using-sqlprefix-sqlxml-40"></a><span data-ttu-id="26b3c-102">使用 sql:prefix 建立 Valid ID、IDREF 和 IDREFS 類型屬性 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="26b3c-102">Creating Valid ID, IDREF, and IDREFS Type Attributes Using sql:prefix (SQLXML 4.0)</span></span>
  <span data-ttu-id="26b3c-103">屬性可以指定為識別碼類型屬性。</span><span class="sxs-lookup"><span data-stu-id="26b3c-103">An attribute can be specified to be an ID type attribute.</span></span> <span data-ttu-id="26b3c-104">然後可以使用指定為 IDREF 或 IDREFS 的屬性來參考 ID 類型屬性，啟用文件之間的連結。</span><span class="sxs-lookup"><span data-stu-id="26b3c-104">Attributes specified as IDREF or IDREFS can then be used to refer to the ID type attributes, enabling links between documents.</span></span>  
  
 <span data-ttu-id="26b3c-105">ID、IDREF 和 IDREFS 會對應至 PK/FK (主索引鍵/外部索引鍵) 在資料庫中的關聯性，但是有一些差異。</span><span class="sxs-lookup"><span data-stu-id="26b3c-105">ID, IDREF, and IDREFS correspond to PK/FK (primary key/foreign key) relationships in the database, with few differences.</span></span> <span data-ttu-id="26b3c-106">在 XML 文件中，ID 類型屬性的值必須是相異的。</span><span class="sxs-lookup"><span data-stu-id="26b3c-106">In an XML document, the values of ID type attributes must be distinct.</span></span> <span data-ttu-id="26b3c-107">如果在 XML 檔中將**CustomerID**和「**訂單**」屬性指定為 ID 類型，則這些值必須是相異的。</span><span class="sxs-lookup"><span data-stu-id="26b3c-107">If **CustomerID** and **OrderID** attributes are specified as ID type in an XML document, these values must be distinct.</span></span> <span data-ttu-id="26b3c-108">然而在資料庫中，CustomerID 和 OrderID 資料行的值可以相同 </span><span class="sxs-lookup"><span data-stu-id="26b3c-108">However, in a database, CustomerID and OrderID columns can have the same values.</span></span> <span data-ttu-id="26b3c-109">(例如，CustomerID = 1 且 OrderID = 1 在資料庫中是有效的)。</span><span class="sxs-lookup"><span data-stu-id="26b3c-109">(For example, CustomerID = 1 and OrderID = 1 are valid in the database).</span></span>  
  
 <span data-ttu-id="26b3c-110">若要讓識別碼、IDREF 和 IDREFS 屬性是有效的：</span><span class="sxs-lookup"><span data-stu-id="26b3c-110">For the ID, IDREF, and IDREFS attributes to be valid:</span></span>  
  
-   <span data-ttu-id="26b3c-111">識別碼的值在 XML 文件中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="26b3c-111">The value of ID must be unique within the XML document.</span></span>  
  
-   <span data-ttu-id="26b3c-112">針對每一個 IDREF 和 IDREFS，參考的識別碼值都必須在 XML 文件中。</span><span class="sxs-lookup"><span data-stu-id="26b3c-112">For every IDREF and IDREFS, the referenced ID values must be in the XML document.</span></span>  
  
-   <span data-ttu-id="26b3c-113">ID、IDREF 和 IDREFS 的值必須是具名 Token </span><span class="sxs-lookup"><span data-stu-id="26b3c-113">The value of an ID, IDREF, and IDREFS must be a named token.</span></span> <span data-ttu-id="26b3c-114">(例如，整數值 101 不能是 ID 值)。</span><span class="sxs-lookup"><span data-stu-id="26b3c-114">(For example, the integer value 101 cannot be an ID value.)</span></span>  
  
-   <span data-ttu-id="26b3c-115">ID、IDREF 和 IDREFS 類型的屬性不能對應至類型 `text`、`ntext`、`image` 或任何其他二進位資料類型 (例如 `timestamp`) 的資料行。</span><span class="sxs-lookup"><span data-stu-id="26b3c-115">The attributes of ID, IDREF, and IDREFS type cannot be mapped to columns of the type `text`, `ntext`, or `image` or any other binary data type (for example, `timestamp`).</span></span>  
  
 <span data-ttu-id="26b3c-116">如果 XML 文件含有多個識別碼，請使用 `sql:prefix` 註解來確保值是唯一的。</span><span class="sxs-lookup"><span data-stu-id="26b3c-116">If an XML document contains multiple IDs, use the `sql:prefix` annotation to ensure that the values are unique.</span></span>  
  
 <span data-ttu-id="26b3c-117">請注意，`sql:prefix` 註解不能搭配 XSD 固定屬性一起使用。</span><span class="sxs-lookup"><span data-stu-id="26b3c-117">Note that `sql:prefix` annotation cannot be used with XSD fixed attribute.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="26b3c-118">範例</span><span class="sxs-lookup"><span data-stu-id="26b3c-118">Examples</span></span>  
 <span data-ttu-id="26b3c-119">若要使用下列範例建立工作範例，您必須符合某些需求。</span><span class="sxs-lookup"><span data-stu-id="26b3c-119">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="26b3c-120">如需詳細資訊，請參閱[執行 SQLXML 範例的需求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="26b3c-120">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-id-and-idrefs-types"></a><span data-ttu-id="26b3c-121">A.</span><span class="sxs-lookup"><span data-stu-id="26b3c-121">A.</span></span> <span data-ttu-id="26b3c-122">指定 ID 和 IDREFS 類型</span><span class="sxs-lookup"><span data-stu-id="26b3c-122">Specifying ID and IDREFS types</span></span>  
 <span data-ttu-id="26b3c-123">在下列架構中， **\<Customer>** 元素是由 **\<Order>** 子項目所組成。</span><span class="sxs-lookup"><span data-stu-id="26b3c-123">In the following schema, the **\<Customer>** element consists of the **\<Order>** child element.</span></span> <span data-ttu-id="26b3c-124">**\<Order>** 元素也有子專案，也就是 **\<OrderDetail>** 元素。</span><span class="sxs-lookup"><span data-stu-id="26b3c-124">The **\<Order>** element also has a child element, the **\<OrderDetail>** element.</span></span>  
  
 <span data-ttu-id="26b3c-125">的**OrderIDList**屬性 **\<Customer>** 是一個 IDREFS 類型屬性，它會參考元素的「**訂單**」屬性 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="26b3c-125">The **OrderIDList** attribute of **\<Customer>** is an IDREFS type attribute that refers to the **OrderID** attribute of the **\<Order>** element.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
                 parent="Sales.Customer"  
                 parent-key="CustomerID"  
                 child="Sales.SalesOrderHeader"  
                 child-key="CustomerID" />  
    <sql:relationship name="OrderOrderDetail"  
                 parent="Sales.SalesOrderHeader"  
                 parent-key="SalesOrderID"  
                 child="Sales.SalesOrderDetail"  
                 child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"    
               sql:relationship="CustOrders" maxOccurs="unbounded" >  
          <xsd:complexType>  
              <xsd:sequence>  
                <xsd:element name="OrderDetail"   
                             sql:relation="Sales.SalesOrderDetail"   
                   sql:relationship="OrderOrderDetail"   
                   maxOccurs="unbounded" >  
                  <xsd:complexType>  
                   <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                   <xsd:attribute name="ProductID" type="xsd:string" />  
                   <xsd:attribute name="OrderQty" type="xsd:integer" />  
                  </xsd:complexType>  
               </xsd:element>  
             </xsd:sequence>  
             <xsd:attribute name="SalesOrderID"   
                            type="xsd:ID" sql:prefix="ord-" />  
             <xsd:attribute name="OrderDate" type="xsd:date" />  
             <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
    <xsd:attribute name="CustomerID" type="xsd:string" />  
    <xsd:attribute name="OrderIDList" type="xsd:IDREFS"   
                   sql:relation="Sales.SalesOrderHeader" sql:field="SalesOrderID"  
                   sql:relationship="CustOrders" sql:prefix="ord-">  
    </xsd:attribute>  
  </xsd:complexType>  
</xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="26b3c-126">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="26b3c-126">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="26b3c-127">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="26b3c-127">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="26b3c-128">將檔案儲存為 sqlPrefix.xml。</span><span class="sxs-lookup"><span data-stu-id="26b3c-128">Save the file as sqlPrefix.xml.</span></span>  
  
2.  <span data-ttu-id="26b3c-129">複製下列範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="26b3c-129">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="26b3c-130">將檔案儲存在與 sqlPrefix.xml 相同的目錄中，並儲存為 sqlPrefixT.xml。</span><span class="sxs-lookup"><span data-stu-id="26b3c-130">Save the file as sqlPrefixT.xml in the same directory where you saved sqlPrefix.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="sqlPrefix.xml">  
        /Customer[@CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="26b3c-131">針對對應結構描述 (sqlPrefix.xml) 指定的目錄路徑，相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="26b3c-131">The directory path specified for the mapping schema (sqlPrefix.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="26b3c-132">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="26b3c-132">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\sqlPrefix.xml"  
    ```  
  
3.  <span data-ttu-id="26b3c-133">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="26b3c-133">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="26b3c-134">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="26b3c-134">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="26b3c-135">以下是部份結果：</span><span class="sxs-lookup"><span data-stu-id="26b3c-135">This is the partial result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="1" OrderIDList="ord-43860 ord-44501 ord-45283 ord-46042">  
    <Order SalesOrderID="ord-43860" OrderDate="2001-08-01" CustomerID="1">  
      <OrderDetail SalesOrderID="43860" ProductID="729" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="732" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="738" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="753" OrderQty="2" />   
      ...  
    </Order>  
    ...  
 </Customer>  
</ROOT>  
```  
  
  
