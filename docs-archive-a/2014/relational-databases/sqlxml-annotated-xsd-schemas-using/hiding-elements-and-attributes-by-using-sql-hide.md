---
title: 使用 sql： hide 來隱藏專案和屬性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- hiding elements
- element mapping [SQLXML], hiding attributes and elements
- hide annotation
- sql:hide
- table/view mapping [SQLXML], hiding attributes and elements
- table mapping [SQLXML], hiding attributes and elements
- hiding attributes
- annotated XSD schemas, hiding attributes and elements
- attribute mapping [SQLXML], hiding attributes and elements
- column mapping [SQLXML]
- element hiding [SQLXML]
- XSD schemas [SQLXML], hiding attributes and elements
- attribute hiding [SQLXML]
ms.assetid: 0978301b-f068-46b6-82b9-dc555161f52e
author: rothja
ms.author: jroth
ms.openlocfilehash: 5a3beb48be1d9809b170faeafa964ba45156ac28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709030"
---
# <a name="hiding-elements-and-attributes-by-using-sqlhide"></a><span data-ttu-id="fe9e2-102">使用 sql:hide 來隱藏元素和屬性</span><span class="sxs-lookup"><span data-stu-id="fe9e2-102">Hiding Elements and Attributes by Using sql:hide</span></span>
  <span data-ttu-id="fe9e2-103">針對 XSD 結構描述執行 XPath 查詢時，產生的 XML 文件會具有在結構描述中指定的元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="fe9e2-103">When an XPath query is executed against an XSD schema, the resulting XML document has elements and attributes that are specified in the schema.</span></span> <span data-ttu-id="fe9e2-104">您可以使用 `sql:hide` 註解來指定某些元素和屬性要在結構描述中隱藏。</span><span class="sxs-lookup"><span data-stu-id="fe9e2-104">You can specify that some elements and attributes be hidden in the schema by using the `sql:hide` annotation.</span></span> <span data-ttu-id="fe9e2-105">當查詢的選取準則需要結構描述中的特定元素或屬性，但是您不想要在產生的 XML 文件中傳回這些項目時，這樣做就很有用。</span><span class="sxs-lookup"><span data-stu-id="fe9e2-105">This is useful when the selection criteria of the query require particular elements or attributes in the schema, but you do not want them returned in the XML document that is generated.</span></span>  
  
 <span data-ttu-id="fe9e2-106">`sql:hide` 註解接受布林值 (0 = false，1 = true)。</span><span class="sxs-lookup"><span data-stu-id="fe9e2-106">The `sql:hide` annotation takes a Boolean value (0=false, 1=true).</span></span> <span data-ttu-id="fe9e2-107">可接受的值為 0、1、true 和 false。</span><span class="sxs-lookup"><span data-stu-id="fe9e2-107">The acceptable values are 0, 1, true, and false.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="fe9e2-108">範例</span><span class="sxs-lookup"><span data-stu-id="fe9e2-108">Examples</span></span>  
 <span data-ttu-id="fe9e2-109">若要使用下列範例建立工作範例，您必須符合某些需求。</span><span class="sxs-lookup"><span data-stu-id="fe9e2-109">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="fe9e2-110">如需詳細資訊，請參閱[執行 SQLXML 範例的需求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="fe9e2-110">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-sqlhide-on-an-attribute"></a><span data-ttu-id="fe9e2-111">A.</span><span class="sxs-lookup"><span data-stu-id="fe9e2-111">A.</span></span> <span data-ttu-id="fe9e2-112">針對屬性指定 sql:hide</span><span class="sxs-lookup"><span data-stu-id="fe9e2-112">Specifying sql:hide on an attribute</span></span>  
 <span data-ttu-id="fe9e2-113">此範例中的 XSD 架構是由 **\<Person.Contact>** 具有**ContactID**、 **FirstName**和**LastName**屬性的元素所組成。</span><span class="sxs-lookup"><span data-stu-id="fe9e2-113">The XSD schema in this example consists of an **\<Person.Contact>** element with **ContactID**, **FirstName**, and **LastName** attributes.</span></span>  
  
 <span data-ttu-id="fe9e2-114">**\<Person.Contact>** 元素屬於複雜類型，因此會對應至相同名稱的資料表， (預設對應) 。</span><span class="sxs-lookup"><span data-stu-id="fe9e2-114">The **\<Person.Contact>** element is of complex type and, therefore, maps to the table of the same name (default mapping).</span></span> <span data-ttu-id="fe9e2-115">元素的所有屬性 **\<Person.Contact>** 都是簡單類型，而且會對應至 AdventureWorks 資料庫中 Contacttable 的相同名稱的資料行。</span><span class="sxs-lookup"><span data-stu-id="fe9e2-115">All the attributes of **\<Person.Contact>** element are of simple type and map to columns with the same names in the Person.Contacttable in the AdventureWorks database.</span></span> <span data-ttu-id="fe9e2-116">在架構中， `sql:hide` 批註是在**ContactID**屬性上指定的。</span><span class="sxs-lookup"><span data-stu-id="fe9e2-116">In the schema, the `sql:hide` annotation is specified on the **ContactID** attribute.</span></span> <span data-ttu-id="fe9e2-117">針對此架構指定 XPath 查詢時，XML 檔中不會傳回**ContactID** 。</span><span class="sxs-lookup"><span data-stu-id="fe9e2-117">When an XPath query is specified against this schema, the **ContactID** is not returned in the XML document.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID"  sql:hide="true" />   
       <xsd:attribute name="FirstName"   type="xsd:string" />   
       <xsd:attribute name="LastName"    type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="fe9e2-118">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="fe9e2-118">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="fe9e2-119">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="fe9e2-119">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="fe9e2-120">將檔案儲存為 Hide.xml。</span><span class="sxs-lookup"><span data-stu-id="fe9e2-120">Save the file as Hide.xml.</span></span>  
  
2.  <span data-ttu-id="fe9e2-121">複製下列範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="fe9e2-121">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="fe9e2-122">將檔案儲存為 HideT.xml 並放在儲存 Hide.xml 的相同目錄中。</span><span class="sxs-lookup"><span data-stu-id="fe9e2-122">Save the file as HideT.xml in the same directory where you saved Hide.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="Hide.xml">  
            /Person.Contact[@ContactID="1"]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="fe9e2-123">針對對應結構描述 (Hide.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="fe9e2-123">The directory path specified for the mapping schema (Hide.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="fe9e2-124">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="fe9e2-124">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\Hide.xml"  
    ```  
  
3.  <span data-ttu-id="fe9e2-125">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="fe9e2-125">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="fe9e2-126">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="fe9e2-126">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="fe9e2-127">以下為結果集：</span><span class="sxs-lookup"><span data-stu-id="fe9e2-127">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <Person.Contact FirstName="Gustavo" LastName="Achong" />   
</ROOT>  
```  
  
 <span data-ttu-id="fe9e2-128">針對某個元素指定 `sql:hide` 時，此元素及其屬性或子元素就不會顯示在產生的 XML 文件中。</span><span class="sxs-lookup"><span data-stu-id="fe9e2-128">When `sql:hide` is specified on an element, the element and its attributes or child elements do not appear in the XML document that is generated.</span></span> <span data-ttu-id="fe9e2-129">以下是在元素上指定的另一個 XSD 架構 `sql:hide` **\<OD>** ：</span><span class="sxs-lookup"><span data-stu-id="fe9e2-129">Here is another XSD schema in which `sql:hide` is specified on the **\<OD>** element:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:annotation>  
    <xsd:documentation>  
      Sales.Customer-Sales.SalesOrderHeader-Sales.SalesOrderDetail Schema  
      Copyright 2004 Microsoft. All rights reserved.  
    </xsd:documentation>  
    <xsd:appinfo>  
      <sql:relationship name="CustomerOrder"  
         parent="Sales.Customer"  
                  parent-key="CustomerID"  
                  child-key="CustomerID"  
                  child="Sales.SalesOrderHeader" />  
       <sql:relationship name="OrderOrderDetails"  
                  parent="Sales.SalesOrderHeader"  
                  parent-key="SalesOrderID"  
                  child-key="SalesOrderID"  
                  child="Sales.SalesOrderDetail"/>  
    </xsd:appinfo>  
  </xsd:annotation>  
  
  <xsd:element name="Customers" sql:relation="Sales.Customer">  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"   
                     maxOccurs="unbounded"   
                     sql:relationship="CustomerOrder">  
          <xsd:complexType>  
            <xsd:sequence>  
               <xsd:element name="OD" sql:relation="Sales.SalesOrderDetail"                                       maxOccurs="unbounded"                                       sql:relationship="OrderOrderDetails"                                       sql:hide="1">  
                  <xsd:complexType>  
                    <xsd:attribute name="SalesOrderID" type="xsd:string"/>  
                    <xsd:attribute name="ProductID" type="xsd:string"/>  
                  </xsd:complexType>  
               </xsd:element>  
            </xsd:sequence>  
          <xsd:attribute name="CustomerID" type="xsd:string"/>  
          <xsd:attribute name="OID" sql:field="SalesOrderID"   
                                    type="xsd:string"/>  
          <xsd:attribute name="OrderDate" type="xsd:date"/>   
        </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
    <xsd:attribute name="CID" sql:field="CustomerID"   
                                type="xsd:string"/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="fe9e2-130">針對此架構指定 XPath 查詢 (例如 `/Customers[@CID="1"]`) 時，所產生的 XML 檔不會包含 **\<OD>** 元素和其子系，如下列部分結果所示：</span><span class="sxs-lookup"><span data-stu-id="fe9e2-130">When an XPath query (for example `/Customers[@CID="1"]`) is specified against this schema, the XML document that is generated does not include the **\<OD>** element and its children, as shown in this partial result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customers CID="1">  
    <Order CustomerID="1" OID="43860" OrderDate="2001-08-01" />   
    <Order CustomerID="1" OID="44501" OrderDate="2001-11-01" />   
    <Order CustomerID="1" OID="45283" OrderDate="2002-02-01" />   
    <Order CustomerID="1" OID="46042" OrderDate="2002-05-01" />   
  </Customers>  
</ROOT>  
```  
  
  
