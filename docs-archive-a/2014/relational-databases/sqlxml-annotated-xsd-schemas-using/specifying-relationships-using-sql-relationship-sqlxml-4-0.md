---
title: 使用 sql： relationship 指定關聯性 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- IDREFS relationships [SQLXML]
- parent attribute [SQLXML]
- element relationships [SQLXML]
- multiple element relationships
- attribute relationships [SQLXML]
- sql:relationship
- relationship chains [SQLXML]
- IDREF relationships [SQLXML]
- parent-child relationships [SQLXML]
- relationship annotation
- XSD schemas [SQLXML], relationships
- annotated XSD schemas, relationships
- relationships [SQLXML], specifying
- unnamed relationships
- ID relationships [SQLXML]
- hierarchical relationships [SQLXML]
- named relationships [SQLXML]
ms.assetid: 98820afa-74e1-4e62-b336-6111a3dede4c
author: rothja
ms.author: jroth
ms.openlocfilehash: 42c703de9d564580eb0baa1349a45b193109c87a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595900"
---
# <a name="specifying-relationships-using-sqlrelationship-sqlxml-40"></a><span data-ttu-id="26e51-102">使用 sql:relationship 指定關聯性 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="26e51-102">Specifying Relationships Using sql:relationship (SQLXML 4.0)</span></span>
  <span data-ttu-id="26e51-103">XML 文件中的元素可以是相關聯的。</span><span class="sxs-lookup"><span data-stu-id="26e51-103">The elements in an XML document can be related.</span></span> <span data-ttu-id="26e51-104">元素可以是巢狀階層，而且在元素之間可以指定 ID、IDREF 或 IDREFS 關聯性。</span><span class="sxs-lookup"><span data-stu-id="26e51-104">The elements can be nested hierarchically, and ID, IDREF, or IDREFS relationships can be specified between the elements.</span></span>  
  
 <span data-ttu-id="26e51-105">例如，在 XSD 架構中， **\<Customer>** 元素包含 **\<Order>** 子項目。</span><span class="sxs-lookup"><span data-stu-id="26e51-105">For example, in an XSD schema, a **\<Customer>** element contains **\<Order>** child elements.</span></span> <span data-ttu-id="26e51-106">當架構對應到 AdventureWorks 資料庫時，專案會 **\<Customer>** 對應至 sales. Customer 資料表，而元素則會 **\<Order>** 對應至 SalesOrderHeader 資料表。</span><span class="sxs-lookup"><span data-stu-id="26e51-106">When the schema is mapped to the AdventureWorks database, the **\<Customer>** element maps to the Sales.Customer table and the **\<Order>** element maps to the Sales.SalesOrderHeader table.</span></span> <span data-ttu-id="26e51-107">Sales.Customer 和 Sales.SalesOrderHeader 這些基礎資料表是相關聯的，因為客戶下了訂單。</span><span class="sxs-lookup"><span data-stu-id="26e51-107">These underlying tables, Sales.Customer and Sales.SalesOrderHeader, are related because customers place orders.</span></span> <span data-ttu-id="26e51-108">Sales.SalesOrderHeader 資料表中的 CustomerID 是外部索引鍵，參考 Sales.Customer 資料表中的 CustomerID 主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="26e51-108">The CustomerID in the Sales.SalesOrderHeader table is a foreign key referring to the CustomerID primary key in the Sales.Customer table.</span></span> <span data-ttu-id="26e51-109">您可以使用 `sql:relationship` 註解，建立對應結構描述元素之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="26e51-109">You can establish these relationships among mapping schema elements by using the `sql:relationship` annotation.</span></span>  
  
 <span data-ttu-id="26e51-110">在註解式 XSD 結構描述中，會根據主索引鍵和基礎資料表之間元素所對應的外部索引鍵關聯性，使用 `sql:relationship` 註解以階層方式建立巢狀結構描述元素。</span><span class="sxs-lookup"><span data-stu-id="26e51-110">In the annotated XSD schema, the `sql:relationship` annotation is used to nest the schema elements hierarchically, on the basis of primary key and foreign key relationships among the underlying tables to which the elements map.</span></span> <span data-ttu-id="26e51-111">指定 `sql:relationship` 註解時，您必須識別下列項目：</span><span class="sxs-lookup"><span data-stu-id="26e51-111">In specifying the `sql:relationship` annotation, you must identify the following:</span></span>  
  
-   <span data-ttu-id="26e51-112">父資料表 (Sales.Customer) 和子資料表 (Sales.SalesOrderHeader)。</span><span class="sxs-lookup"><span data-stu-id="26e51-112">The parent table (Sales.Customer) and the child table (Sales.SalesOrderHeader).</span></span>  
  
-   <span data-ttu-id="26e51-113">在父資料表和子資料表之間組成關聯性的一或多個資料行。</span><span class="sxs-lookup"><span data-stu-id="26e51-113">The column or columns that compose the relationship between the parent and child tables.</span></span> <span data-ttu-id="26e51-114">例如，同時出現在父資料表和子資料表中的 CustomerID 資料行。</span><span class="sxs-lookup"><span data-stu-id="26e51-114">For example, the CustomerID column, which appears in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="26e51-115">這項資訊用於產生適當的階層。</span><span class="sxs-lookup"><span data-stu-id="26e51-115">This information is used to generate the proper hierarchy.</span></span>  
  
 <span data-ttu-id="26e51-116">若要提供資料表名稱和需要的聯結資訊，則要在 `sql:relationship` 註解上指定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="26e51-116">To provide the table names and the necessary join information, the following attributes are specified on the `sql:relationship` annotation.</span></span> <span data-ttu-id="26e51-117">這些屬性只對 **\<sql:relationship>** 元素有效：</span><span class="sxs-lookup"><span data-stu-id="26e51-117">These attributes are valid only with the **\<sql:relationship>** element:</span></span>  
  
 <span data-ttu-id="26e51-118">**名稱**</span><span class="sxs-lookup"><span data-stu-id="26e51-118">**Name**</span></span>  
 <span data-ttu-id="26e51-119">指定關聯性的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="26e51-119">Specifies the unique name of the relationship.</span></span>  
  
 <span data-ttu-id="26e51-120">**Parent**</span><span class="sxs-lookup"><span data-stu-id="26e51-120">**Parent**</span></span>  
 <span data-ttu-id="26e51-121">指定父關聯 (資料表)。</span><span class="sxs-lookup"><span data-stu-id="26e51-121">Specifies the parent relation (table).</span></span> <span data-ttu-id="26e51-122">這是選用的屬性；如果未指定此屬性，會從文件之子階層中的資訊取得父資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="26e51-122">This is an optional attribute; if the attribute is not specified, the parent table name is obtained from information in the child hierarchy in the document.</span></span> <span data-ttu-id="26e51-123">如果架構指定兩個使用相同 **\<sql:relationship>** 但不同父元素的父子式階層，您就不會在中指定父屬性 **\<sql:relationship>** 。</span><span class="sxs-lookup"><span data-stu-id="26e51-123">If the schema specifies two parent-child hierarchies that use the same **\<sql:relationship>** but different parent elements, you do not specify the parent attribute in **\<sql:relationship>**.</span></span> <span data-ttu-id="26e51-124">這項資訊是從結構描述的階層中取得。</span><span class="sxs-lookup"><span data-stu-id="26e51-124">This information is obtained from the hierarchy in the schema.</span></span>  
  
 <span data-ttu-id="26e51-125">**parent-key**</span><span class="sxs-lookup"><span data-stu-id="26e51-125">**parent-key**</span></span>  
 <span data-ttu-id="26e51-126">指定父系的父索引鍵。</span><span class="sxs-lookup"><span data-stu-id="26e51-126">Specifies the parent key of the parent.</span></span> <span data-ttu-id="26e51-127">如果父索引鍵由多個資料行所組成，值就會用資料行之間的空格指定。</span><span class="sxs-lookup"><span data-stu-id="26e51-127">If the parent key is composed of multiple columns, values are specified with a space between them.</span></span> <span data-ttu-id="26e51-128">在指定給多重資料行索引鍵和其對應之子索引鍵的值之間有位置性對應。</span><span class="sxs-lookup"><span data-stu-id="26e51-128">There is a positional mapping between the values that are specified for the multicolumn key and for the corresponding child key.</span></span>  
  
 <span data-ttu-id="26e51-129">**子**</span><span class="sxs-lookup"><span data-stu-id="26e51-129">**Child**</span></span>  
 <span data-ttu-id="26e51-130">指定子關聯 (資料表)。</span><span class="sxs-lookup"><span data-stu-id="26e51-130">Specifies the child relation (table).</span></span>  
  
 <span data-ttu-id="26e51-131">**child-key**</span><span class="sxs-lookup"><span data-stu-id="26e51-131">**child-key**</span></span>  
 <span data-ttu-id="26e51-132">在參考父系中之 parent-key 的子系中指定子索引鍵。</span><span class="sxs-lookup"><span data-stu-id="26e51-132">Specifies the child key in the child referring to parent-key in parent.</span></span> <span data-ttu-id="26e51-133">如果子索引鍵由多個屬性 (資料行) 所組成，則 child-key 的值就會用屬性或資料行之間的空格指定。</span><span class="sxs-lookup"><span data-stu-id="26e51-133">If the child key is composed of multiple attributes (columns), the child-key values are specified with a space between them.</span></span> <span data-ttu-id="26e51-134">在指定給多重資料行索引鍵和其對應之父索引鍵的值之間有位置性對應。</span><span class="sxs-lookup"><span data-stu-id="26e51-134">There is a positional mapping between the values that are specified for the multicolumn key and for the corresponding parent key.</span></span>  
  
 <span data-ttu-id="26e51-135">**反向方法**</span><span class="sxs-lookup"><span data-stu-id="26e51-135">**Inverse**</span></span>  
 <span data-ttu-id="26e51-136">在上指定的這個屬性 **\<sql:relationship>** 是由 updategram 所使用。</span><span class="sxs-lookup"><span data-stu-id="26e51-136">This attribute specified on **\<sql:relationship>** is used by updategrams.</span></span> <span data-ttu-id="26e51-137">如需詳細資訊，請參閱[在 sql： relationship 上指定 sql：反向屬性](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="26e51-137">For more information, see [Specifying the sql:inverse Attribute on sql:relationship](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="26e51-138">`sql:key-fields`批註必須在包含子專案的元素中指定，此專案在專案 **\<sql:relationship>** 和子系之間定義，而且未提供父元素中指定之資料表的主鍵。</span><span class="sxs-lookup"><span data-stu-id="26e51-138">The `sql:key-fields` annotation must be specified in an element that contains a child element, that has a **\<sql:relationship>** defined between the element and the child, and that does not provide the primary key of the table specified in the parent element.</span></span> <span data-ttu-id="26e51-139">即使架構未指定 **\<sql:relationship>** ，您還是必須指定， `sql:key-fields` 才能產生適當的階層。</span><span class="sxs-lookup"><span data-stu-id="26e51-139">Even if the schema does not specify **\<sql:relationship>**, you must specify `sql:key-fields` to produce the proper hierarchy.</span></span> <span data-ttu-id="26e51-140">如需詳細資訊，請參閱[使用 sql：索引鍵-欄位來識別索引鍵資料行](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="26e51-140">For more information, see [Identifying Key Columns by Using sql:key-fields](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="26e51-141">若要在結果中產生正確的巢狀結構，建議在所有的結構描述中指定 `sql:key-fields`。</span><span class="sxs-lookup"><span data-stu-id="26e51-141">To produce proper nesting in the result, it is recommended that `sql:key-fields` are specified in all schemas.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="26e51-142">範例</span><span class="sxs-lookup"><span data-stu-id="26e51-142">Examples</span></span>  
 <span data-ttu-id="26e51-143">若要使用下列範例建立工作範例，您必須符合某些需求。</span><span class="sxs-lookup"><span data-stu-id="26e51-143">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="26e51-144">如需詳細資訊，請參閱[執行 SQLXML 範例的需求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="26e51-144">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-the-sqlrelationship-annotation-on-an-element"></a><span data-ttu-id="26e51-145">A.</span><span class="sxs-lookup"><span data-stu-id="26e51-145">A.</span></span> <span data-ttu-id="26e51-146">在元素上指定 sql:relationship 註解</span><span class="sxs-lookup"><span data-stu-id="26e51-146">Specifying the sql:relationship annotation on an element</span></span>  
 <span data-ttu-id="26e51-147">下列批註式 XSD 架構包含 **\<Customer>** 和 **\<Order>** 元素。</span><span class="sxs-lookup"><span data-stu-id="26e51-147">The following annotated XSD schema includes **\<Customer>** and **\<Order>** elements.</span></span> <span data-ttu-id="26e51-148">**\<Order>** 元素是元素的子項目 **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="26e51-148">The **\<Order>** element is a child element of the **\<Customer>** element.</span></span>  
  
 <span data-ttu-id="26e51-149">在架構中， `sql:relationship` 批註是在 **\<Order>** 子項目上指定。</span><span class="sxs-lookup"><span data-stu-id="26e51-149">In the schema, the `sql:relationship` annotation is specified on the **\<Order>** child element.</span></span> <span data-ttu-id="26e51-150">關聯性本身定義于元素中 **\<xsd:appinfo>** 。</span><span class="sxs-lookup"><span data-stu-id="26e51-150">The relationship itself is defined in the **\<xsd:appinfo>** element.</span></span>  
  
 <span data-ttu-id="26e51-151">**\<relationship>** 元素會將 SalesOrderHeader 資料表中的 customerid 識別為外鍵，參考 sales. Customer 資料表中的 customerid 主要索引鍵。</span><span class="sxs-lookup"><span data-stu-id="26e51-151">The **\<relationship>** element identifies CustomerID in the Sales.SalesOrderHeader table as a foreign key that refers to the CustomerID primary key in the Sales.Customer table.</span></span> <span data-ttu-id="26e51-152">因此，屬於客戶的訂單會顯示為該元素的子項目 **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="26e51-152">Therefore, orders that belong to a customer appear as a child element of that **\<Customer>** element.</span></span>  
  
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
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                    sql:relationship="CustOrders" >  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
 <span data-ttu-id="26e51-153">上述結構描述使用具名關聯性。</span><span class="sxs-lookup"><span data-stu-id="26e51-153">The previous schema uses a named relationship.</span></span> <span data-ttu-id="26e51-154">您也可以指定一個未命名的關聯性。</span><span class="sxs-lookup"><span data-stu-id="26e51-154">You can also specify an unnamed relationship.</span></span> <span data-ttu-id="26e51-155">結果是相同的。</span><span class="sxs-lookup"><span data-stu-id="26e51-155">The results are same.</span></span>  
  
 <span data-ttu-id="26e51-156">這是修訂過的結構描述 (其中會指定未命名的關聯性)：</span><span class="sxs-lookup"><span data-stu-id="26e51-156">This is the revised schema in which an unnamed relationship is specified:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer"  type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader">  
           <xsd:annotation>  
            <xsd:appinfo>  
              <sql:relationship   
                parent="Sales.Customer"  
                parent-key="CustomerID"  
                child="Sales.SalesOrderHeader"  
                child-key="CustomerID" />  
            </xsd:appinfo>  
           </xsd:annotation>  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="26e51-157">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="26e51-157">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="26e51-158">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="26e51-158">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="26e51-159">將檔案儲存為 sql-relationship.xml。</span><span class="sxs-lookup"><span data-stu-id="26e51-159">Save the file as sql-relationship.xml.</span></span>  
  
2.  <span data-ttu-id="26e51-160">複製下列範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="26e51-160">Copy the following template below and paste it into a text file.</span></span> <span data-ttu-id="26e51-161">將檔案儲存為 sql-relationshipT.xml 並放在與儲存 sql-relationship.xml 相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="26e51-161">Save the file as sql-relationshipT.xml in the same directory where you saved sql-relationship.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sql-relationship.xml">  
            /Customer[@CustomerID=1]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="26e51-162">為對應結構描述 (sql-relationship.xml) 指定的目錄路徑，是儲存範本之目錄的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="26e51-162">The directory path specified for the mapping schema (sql-relationship.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="26e51-163">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="26e51-163">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\sql-relationship.xml"  
    ```  
  
3.  <span data-ttu-id="26e51-164">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="26e51-164">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="26e51-165">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="26e51-165">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="26e51-166">以下為結果集：</span><span class="sxs-lookup"><span data-stu-id="26e51-166">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Customer CustomerID="1">   
    <Order OrderID="43860" CustomerID="1" />   
    <Order OrderID="44501" CustomerID="1" />   
    <Order OrderID="45283" CustomerID="1" />   
    <Order OrderID="46042" CustomerID="1" />   
  </Customer>   
</ROOT>  
```  
  
### <a name="b-specifying-a-relationship-chain"></a><span data-ttu-id="26e51-167">B.</span><span class="sxs-lookup"><span data-stu-id="26e51-167">B.</span></span> <span data-ttu-id="26e51-168">指定關聯性鏈結</span><span class="sxs-lookup"><span data-stu-id="26e51-168">Specifying a relationship chain</span></span>  
 <span data-ttu-id="26e51-169">針對這個範例，假設您想要讓下列 XML 文件使用從 AdventureWorks 資料庫取得的資料：</span><span class="sxs-lookup"><span data-stu-id="26e51-169">For this example, assume that you want the following XML document using data obtained from the AdventureWorks database:</span></span>  
  
```  
<Order SalesOrderID="43659">  
  <Product Name="Mountain Bike Socks, M"/>   
  <Product Name="Sport-100 Helmet, Blue"/>  
  ...  
</Order>  
...  
```  
  
 <span data-ttu-id="26e51-170">針對 SalesOrderHeader 資料表中的每個訂單，XML 檔都有一個 **\<Order>** 元素。</span><span class="sxs-lookup"><span data-stu-id="26e51-170">For each order in the Sales.SalesOrderHeader table, the XML document has one **\<Order>** element.</span></span> <span data-ttu-id="26e51-171">而且每個 **\<Order>** 元素都有一個 **\<Product>** 子專案清單，每個專案都有一個用於訂單中的產品。</span><span class="sxs-lookup"><span data-stu-id="26e51-171">And each **\<Order>** element has a list of **\<Product>** child elements, one for each product requested in the order.</span></span>  
  
 <span data-ttu-id="26e51-172">若要指定產生此階層的 XSD 結構描述，您必須指定兩個關聯性：OrderOD 和 ODProduct。</span><span class="sxs-lookup"><span data-stu-id="26e51-172">To specify an XSD schema that will produce this hierarchy, you must specify two relationships: OrderOD and ODProduct.</span></span> <span data-ttu-id="26e51-173">OrderOD 關聯性會在 Sales.SalesOrderHeader 和 Sales.SalesOrderDetail 資料表之間指定父子式關聯性。</span><span class="sxs-lookup"><span data-stu-id="26e51-173">The OrderOD relationship specifies the parent-child relationship between the Sales.SalesOrderHeader and Sales.SalesOrderDetail tables.</span></span> <span data-ttu-id="26e51-174">ODProduct 關聯性會在 Sales.SalesOrderDetail 和 Production.Product 資料表之間指定關聯性。</span><span class="sxs-lookup"><span data-stu-id="26e51-174">The ODProduct relationship specifies the relationship between the Sales.SalesOrderDetail and Production.Product tables.</span></span>  
  
 <span data-ttu-id="26e51-175">在下列架構中， `msdata:relationship` 元素上的注釋會 **\<Product>** 指定兩個值： OrderOD 和 ODProduct。</span><span class="sxs-lookup"><span data-stu-id="26e51-175">In the following schema, the `msdata:relationship` annotation on the **\<Product>** element specifies two values: OrderOD and ODProduct.</span></span> <span data-ttu-id="26e51-176">指定這些值的順序很重要。</span><span class="sxs-lookup"><span data-stu-id="26e51-176">The order in which these values are specified is important.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <msdata:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  
    <msdata:relationship name="ODProduct"  
          parent="Sales.SalesOrderDetail"  
          parent-key="ProductID"  
          child="Production.Product"  
          child-key="ProductID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Order" msdata:relation="Sales.SalesOrderHeader"   
               msdata:key-fields="SalesOrderID" type="OrderType" />  
   <xsd:complexType name="OrderType" >  
     <xsd:sequence>  
        <xsd:element name="Product" msdata:relation="Production.Product"   
                     msdata:key-fields="ProductID"  
                     msdata:relationship="OrderOD ODProduct">  
          <xsd:complexType>  
             <xsd:attribute name="Name" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="SalesOrderID"   type="xsd:integer" />   
    </xsd:complexType>  
</xsd:schema>  
```  
  
 <span data-ttu-id="26e51-177">您可以指定匿名關聯性，而非指定具名關聯性。</span><span class="sxs-lookup"><span data-stu-id="26e51-177">Instead of specifying a named relationship, you can specify an anonymous relationship.</span></span> <span data-ttu-id="26e51-178">在此情況下，用來 **\<annotation>** **\</annotation>** 描述兩個關聯性的完整內容會顯示為的子項目 **\<Product>** 。</span><span class="sxs-lookup"><span data-stu-id="26e51-178">In this case, the entire contents of **\<annotation>**...**\</annotation>**, which describes the two relationships, appear as a child element of **\<Product>**.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Order" msdata:relation="Sales.SalesOrderHeader"   
               msdata:key-fields="SalesOrderID" type="OrderType" />  
  
   <xsd:complexType name="OrderType" >  
     <xsd:sequence>  
        <xsd:element name="Product" msdata:relation="Production.Product"   
                     msdata:key-fields="ProductID" >  
         <xsd:annotation>  
          <xsd:appinfo>  
           <msdata:relationship   
               parent="Sales.SalesOrderHeader"  
               parent-key="SalesOrderID"  
               child="Sales.SalesOrderDetail"  
               child-key="SalesOrderID" />  
  
           <msdata:relationship   
               parent="Sales.SalesOrderDetail"  
               parent-key="ProductID"  
               child="Production.Product"  
               child-key="ProductID" />  
         </xsd:appinfo>  
       </xsd:annotation>  
       <xsd:complexType>  
          <xsd:attribute name="Name" type="xsd:string" />  
       </xsd:complexType>  
     </xsd:element>  
   </xsd:sequence>  
   <xsd:attribute name="SalesOrderID"   type="xsd:integer" />   
  </xsd:complexType>  
 </xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="26e51-179">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="26e51-179">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="26e51-180">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="26e51-180">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="26e51-181">將檔案儲存為 relationshipChain.xml。</span><span class="sxs-lookup"><span data-stu-id="26e51-181">Save the file as relationshipChain.xml.</span></span>  
  
2.  <span data-ttu-id="26e51-182">複製下列範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="26e51-182">Copy the following template below and paste it into a text file.</span></span> <span data-ttu-id="26e51-183">然後將檔案儲存為 relationshipChainT.xml，並放在與儲存 relationshipChain.xml 的相同目錄中。</span><span class="sxs-lookup"><span data-stu-id="26e51-183">Save the file as relationshipChainT.xml in the same directory where you saved relationshipChain.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="relationshipChain.xml">  
            /Order  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="26e51-184">為對應結構描述 (relationshipChain.xml) 指定的目錄路徑，是儲存範本之目錄的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="26e51-184">The directory path specified for the mapping schema (relationshipChain.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="26e51-185">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="26e51-185">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\relationshipChain.xml"  
    ```  
  
3.  <span data-ttu-id="26e51-186">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="26e51-186">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="26e51-187">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="26e51-187">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="26e51-188">以下為結果集：</span><span class="sxs-lookup"><span data-stu-id="26e51-188">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Order SalesOrderID="43659">  
    <Product Name="Mountain Bike Socks, M" />   
    <Product Name="Sport-100 Helmet, Blue" />   
    <Product Name="AWC Logo Cap" />   
    <Product Name="Long-Sleeve Logo Jersey, M" />   
    <Product Name="Long-Sleeve Logo Jersey, XL" />   
    ...  
  </Order>  
  ...  
</ROOT>  
```  
  
### <a name="c-specifying-the-relationship-annotation-on-an-attribute"></a><span data-ttu-id="26e51-189">C.</span><span class="sxs-lookup"><span data-stu-id="26e51-189">C.</span></span> <span data-ttu-id="26e51-190">在屬性上指定關聯性註解</span><span class="sxs-lookup"><span data-stu-id="26e51-190">Specifying the relationship annotation on an attribute</span></span>  
 <span data-ttu-id="26e51-191">此範例中的架構包含 \<Customer> 具有 \<CustomerID> 子項目的元素和 IDREFS 類型的 OrderIDList 屬性。</span><span class="sxs-lookup"><span data-stu-id="26e51-191">The schema in this example includes a \<Customer> element with a \<CustomerID> child element and an OrderIDList attribute of IDREFS type.</span></span> <span data-ttu-id="26e51-192">\<Customer>元素會對應至 AdventureWorks 資料庫中的 Sales. Customer 資料表。</span><span class="sxs-lookup"><span data-stu-id="26e51-192">The \<Customer> element maps to the Sales.Customer table in the AdventureWorks database.</span></span> <span data-ttu-id="26e51-193">根據預設，此對應的範圍會套用至所有子專案或屬性，除非在 `sql:relation` 子項目或屬性上指定，在此情況下，必須使用專案來定義適當的主鍵/外鍵關聯性 \<relationship> 。</span><span class="sxs-lookup"><span data-stu-id="26e51-193">By default, the scope of this mapping applies to all the child elements or attributes unless `sql:relation` is specified on the child element or attribute, in which case, the appropriate primary-key/foreign-key relationship must be defined using the \<relationship> element.</span></span> <span data-ttu-id="26e51-194">同時，使用 `relation` 註解指定不同資料表的子元素或屬性也必須指定 `relationship` 註解。</span><span class="sxs-lookup"><span data-stu-id="26e51-194">And the child element or attribute, which specifies the different table using the `relation` annotation, must also specify the `relationship` annotation.</span></span>  
  
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
     </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="CustomerID"   type="xsd:string" />   
     </xsd:sequence>  
     <xsd:attribute name="OrderIDList"   
                     type="xsd:IDREFS"   
                     sql:relation="Sales.SalesOrderHeader"   
                     sql:field="SalesOrderID"  
                     sql:relationship="CustOrders" >  
        </xsd:attribute>  
    </xsd:complexType>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="26e51-195">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="26e51-195">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="26e51-196">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="26e51-196">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="26e51-197">將檔案儲存為 relationship-on-attribute.xml。</span><span class="sxs-lookup"><span data-stu-id="26e51-197">Save the file as relationship-on-attribute.xml.</span></span>  
  
2.  <span data-ttu-id="26e51-198">複製下列範本，並將其貼到檔案中。</span><span class="sxs-lookup"><span data-stu-id="26e51-198">Copy the following template and paste it into a file.</span></span> <span data-ttu-id="26e51-199">將檔案儲存為 relationship-on-attributeT.xml，並放在與儲存 relationship-on-attribute.xml 相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="26e51-199">Save the file as relationship-on-attributeT.xml in the same directory where you saved relationship-on-attribute.xml.</span></span> <span data-ttu-id="26e51-200">範本中的查詢會選取 CustomerID 為 1 的客戶。</span><span class="sxs-lookup"><span data-stu-id="26e51-200">The query in the template selects a customer with the CustomerID of 1.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="relationship-on-attribute.xml">  
        /Customer[CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="26e51-201">為對應結構描述 (relationship-on-attribute.xml) 指定的目錄路徑，是儲存範本之目錄的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="26e51-201">The directory path specified for the mapping schema (relationship-on-attribute.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="26e51-202">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="26e51-202">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\relationship-on-attribute.xml"  
    ```  
  
3.  <span data-ttu-id="26e51-203">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="26e51-203">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="26e51-204">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="26e51-204">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="26e51-205">以下為結果集：</span><span class="sxs-lookup"><span data-stu-id="26e51-205">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Customer OrderIDList="43860 44501 45283 46042">  
    <CustomerID>1</CustomerID>   
  </Customer>  
</ROOT>  
```  
  
### <a name="d-specifying-sqlrelationship-on-multiple-elements"></a><span data-ttu-id="26e51-206">D.</span><span class="sxs-lookup"><span data-stu-id="26e51-206">D.</span></span> <span data-ttu-id="26e51-207">在多重元素中指定 sql:relationship</span><span class="sxs-lookup"><span data-stu-id="26e51-207">Specifying sql:relationship on multiple elements</span></span>  
 <span data-ttu-id="26e51-208">在此範例中，批註式 XSD 架構包含 **\<Customer>** 、 **\<Order>** 和 **\<OrderDetail>** 元素。</span><span class="sxs-lookup"><span data-stu-id="26e51-208">In this example, the annotated XSD schema contains the **\<Customer>**, **\<Order>**, and **\<OrderDetail>** elements.</span></span>  
  
 <span data-ttu-id="26e51-209">**\<Order>** 元素是元素的子項目 **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="26e51-209">The **\<Order>** element is a child element of the **\<Customer>** element.</span></span> <span data-ttu-id="26e51-210">**\<sql:relationship>** 是在子專案上指定 **\<Order>** ，因此屬於客戶的訂單會顯示為的子項目 **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="26e51-210">**\<sql:relationship>** is specified on the **\<Order>** child element; therefore, orders that belong to a customer appear as child elements of **\<Customer>**.</span></span>  
  
 <span data-ttu-id="26e51-211">**\<Order>** 元素包含 **\<OrderDetail>** 子項目。</span><span class="sxs-lookup"><span data-stu-id="26e51-211">The **\<Order>** element includes the **\<OrderDetail>** child element.</span></span> <span data-ttu-id="26e51-212">**\<sql:relationship>** 是在子專案上指定 **\<OrderDetail>** ，因此訂單的相關訂單詳細資料會顯示為該元素的子項目 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="26e51-212">**\<sql:relationship>** is specified on **\<OrderDetail>** child element, so the order details that pertain to an order appear as child elements of that **\<Order>** element.</span></span>  
  
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
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="OrderDate" type="xsd:date" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="CustomerID" type="xsd:string" />  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="26e51-213">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="26e51-213">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="26e51-214">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="26e51-214">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="26e51-215">將檔案儲存為 relationship-multiple-elements.xml。</span><span class="sxs-lookup"><span data-stu-id="26e51-215">Save the file as relationship-multiple-elements.xml.</span></span>  
  
2.  <span data-ttu-id="26e51-216">複製下列範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="26e51-216">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="26e51-217">將檔案儲存為 relationship-multiple-elementsT.xml，並放在與儲存 relationship-multiple-elements.xml 相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="26e51-217">Save the file as relationship-multiple-elementsT.xml in the same directory where you saved relationship-multiple-elements.xml.</span></span> <span data-ttu-id="26e51-218">範本中的查詢會傳回 CustomerID 為 1 和 SalesOrderID 為 43860 之客戶的訂單資訊。</span><span class="sxs-lookup"><span data-stu-id="26e51-218">The query in the template returns order information for a customer with the CustomerID of 1 and SalesOrderID of 43860.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="relationship-multiple-elements.xml">  
        /Customer[@CustomerID=1]/Order[@SalesOrderID=43860]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="26e51-219">為對應結構描述 (relationship-multiple-elements.xml) 指定的目錄路徑，是儲存範本之目錄的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="26e51-219">The directory path specified for the mapping schema (relationship-multiple-elements.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="26e51-220">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="26e51-220">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\relationship-multiple-elements.xml"  
    ```  
  
3.  <span data-ttu-id="26e51-221">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="26e51-221">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="26e51-222">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="26e51-222">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="26e51-223">以下為結果集：</span><span class="sxs-lookup"><span data-stu-id="26e51-223">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="43860" OrderDate="2001-08-01" CustomerID="1">  
     <OrderDetail SalesOrderID="43860" ProductID="761" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="770" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="758" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="765" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="732" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="762" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="738" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="768" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="753" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="729" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="763" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="756" OrderQty="1" />   
  </Order>  
</ROOT>  
```  
  
### <a name="e-specifying-the-sqlrelationship-without-the-parent-attribute"></a><span data-ttu-id="26e51-224">E.</span><span class="sxs-lookup"><span data-stu-id="26e51-224">E.</span></span> <span data-ttu-id="26e51-225">指定 \<sql:relationship> 不含父屬性的</span><span class="sxs-lookup"><span data-stu-id="26e51-225">Specifying the \<sql:relationship> without the parent attribute</span></span>  
 <span data-ttu-id="26e51-226">這個範例說明如何指定 **\<sql:relationship>** 不含**父**屬性的。</span><span class="sxs-lookup"><span data-stu-id="26e51-226">This example illustrates specifying the **\<sql:relationship>** without the **parent** attribute.</span></span> <span data-ttu-id="26e51-227">例如，假設您有下列員工資料表：</span><span class="sxs-lookup"><span data-stu-id="26e51-227">For example, assume you have the following employee tables:</span></span>  
  
```  
Emp1(SalesPersonID, FirstName, LastName, ReportsTo)  
Emp2(SalesPersonID, FirstName, LastName, ReportsTo)  
```  
  
 <span data-ttu-id="26e51-228">下列 XML view 具有 **\<Emp1>** **\<Emp2>** 對應至 Emp1 和 Emp2 資料表的和元素：</span><span class="sxs-lookup"><span data-stu-id="26e51-228">The following XML view has the **\<Emp1>** and **\<Emp2>** elements mapping to the Sales.Emp1 and Sales.Emp2 tables:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="EmpOrders"  
          parent-key="SalesPersonID"  
          child="Sales.SalesOrderHeader"  
          child-key="SalesPersonID" />  
     </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Emp1" sql:relation="Sales.Emp1" type="EmpType" />  
  <xsd:element name="Emp2" sql:relation="Sales.Emp2" type="EmpType" />  
   <xsd:complexType name="EmpType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"   
                     sql:relationship="EmpOrders" >  
          <xsd:complexType>  
             <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
             <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="SalesPersonID"   type="xsd:integer" />   
        <xsd:attribute name="LastName"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
 <span data-ttu-id="26e51-229">在架構中， **\<Emp1>** 元素和專案都 **\<Emp2>** 屬於類型 `EmpType` 。</span><span class="sxs-lookup"><span data-stu-id="26e51-229">In the schema, both the **\<Emp1>** element and **\<Emp2>** element are of type `EmpType`.</span></span> <span data-ttu-id="26e51-230">此類型 `EmpType` 描述 **\<Order>** 子項目和對應的 **\<sql:relationship>** 。</span><span class="sxs-lookup"><span data-stu-id="26e51-230">The type `EmpType` describes an **\<Order>** child element and the corresponding **\<sql:relationship>**.</span></span> <span data-ttu-id="26e51-231">在這種情況下，在中不會 **\<sql:relationship>** 使用**父**屬性來識別單一父系。</span><span class="sxs-lookup"><span data-stu-id="26e51-231">In this case, there is no single parent that can be identified in **\<sql:relationship>** by using the **parent** attribute.</span></span> <span data-ttu-id="26e51-232">在這種情況下，您不會在中指定**父**屬性，而 **\<sql:relationship>** 是從架構中的階層取得**父**屬性資訊。</span><span class="sxs-lookup"><span data-stu-id="26e51-232">In this situation, you don't specify the **parent** attribute in **\<sql:relationship>**; the **parent** attribute information is obtained from the hierarchy in the schema.</span></span>  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="26e51-233">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="26e51-233">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="26e51-234">在 AdventureWorks 資料庫中建立這些資料表：</span><span class="sxs-lookup"><span data-stu-id="26e51-234">Create these tables in the AdventureWorks database:</span></span>  
  
    ```  
    USE AdventureWorks  
    CREATE TABLE Sales.Emp1 (  
           SalesPersonID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    Go  
    CREATE TABLE Sales.Emp2 (  
           SalesPersonID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    Go  
    ```  
  
2.  <span data-ttu-id="26e51-235">在資料表中加入此範例資料：</span><span class="sxs-lookup"><span data-stu-id="26e51-235">Add this sample data in the tables:</span></span>  
  
    ```  
    INSERT INTO Sales.Emp1 values (279, 'Nancy', 'Devolio',NULL)  
    INSERT INTO Sales.Emp1 values (282, 'Andrew', 'Fuller',1)  
    INSERT INTO Sales.Emp1 values (276, 'Janet', 'Leverling',1)  
    INSERT INTO Sales.Emp2 values (277, 'Margaret', 'Peacock',3)  
    INSERT INTO Sales.Emp2 values (283, 'Steven', 'Devolio',4)  
    INSERT INTO Sales.Emp2 values (275, 'Nancy', 'Buchanan',5)  
    INSERT INTO Sales.Emp2 values (281, 'Michael', 'Suyama',6)  
    ```  
  
3.  <span data-ttu-id="26e51-236">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="26e51-236">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="26e51-237">將檔案儲存為 relationship-noparent.xml。</span><span class="sxs-lookup"><span data-stu-id="26e51-237">Save the file as relationship-noparent.xml.</span></span>  
  
4.  <span data-ttu-id="26e51-238">複製下列範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="26e51-238">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="26e51-239">將檔案儲存為 relationship-noparentT.xml，並放在與儲存 relationship-noparent.xml 相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="26e51-239">Save the file as relationship-noparentT.xml in the same directory where you saved relationship-noparent.xml.</span></span> <span data-ttu-id="26e51-240">範本中的查詢會選取所有專案 \<Emp1> (因此，父系會 Emp1) 。</span><span class="sxs-lookup"><span data-stu-id="26e51-240">The query in the template selects all the \<Emp1> elements (therefore, the parent is Emp1).</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="relationship-noparent.xml">  
            /Emp1  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="26e51-241">為對應結構描述 (relationship-noparent.xml) 指定的目錄路徑，是儲存範本之目錄的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="26e51-241">The directory path specified for the mapping schema (relationship-noparent.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="26e51-242">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="26e51-242">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\relationship-noparent.xml"  
    ```  
  
5.  <span data-ttu-id="26e51-243">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="26e51-243">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="26e51-244">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="26e51-244">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="26e51-245">以下是部分結果集：</span><span class="sxs-lookup"><span data-stu-id="26e51-245">Here is a partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<Emp1 SalesPersonID="276" LastName="Leverling">  
  <Order SalesOrderID="43663" CustomerID="510" />   
  <Order SalesOrderID="43666" CustomerID="511" />   
  <Order SalesOrderID="43859" CustomerID="259" />  
  ...  
</Emp1>  
```  
  
  
