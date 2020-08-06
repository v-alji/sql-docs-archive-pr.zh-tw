---
title: 使用 sql： is-常數建立常數元素 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- element does not map [SQLXML]
- sql:is-constant
- XSD schemas [SQLXML], constant elements
- element mapping [SQLXML], constant elements
- is-constant annotation
- constant elements [SQLXML]
- annotated XSD schemas, constant elements
ms.assetid: 940eea1b-54f5-445f-b844-c894d9f3941b
author: rothja
ms.author: jroth
ms.openlocfilehash: 8deedd8547d6bc3f0154eedb889ad908750f071a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702558"
---
# <a name="creating-constant-elements-using-sqlis-constant-sqlxml-40"></a><span data-ttu-id="e4be2-102">使用 sql:is-constant 建立常數元素 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="e4be2-102">Creating Constant Elements Using sql:is-constant (SQLXML 4.0)</span></span>
  <span data-ttu-id="e4be2-103">若要指定常數元素（也就是 XSD 架構中未對應到任何資料庫資料表或資料行的專案），您可以使用 `sql:is-constant` 批註。</span><span class="sxs-lookup"><span data-stu-id="e4be2-103">To specify a constant element-that is, an element in the XSD schema that does not map to any database table or column-you can use the `sql:is-constant` annotation.</span></span> <span data-ttu-id="e4be2-104">此註解接受布林值 (0 = false，1 = true)。</span><span class="sxs-lookup"><span data-stu-id="e4be2-104">This annotation takes a Boolean value (0 = false, 1 = true).</span></span> <span data-ttu-id="e4be2-105">可接受的值為 0、1、true 和 false。</span><span class="sxs-lookup"><span data-stu-id="e4be2-105">The acceptable values are 0, 1, true, and false.</span></span> <span data-ttu-id="e4be2-106">`sql:is-constant` 註解可以在沒有任何屬性的元素上指定。</span><span class="sxs-lookup"><span data-stu-id="e4be2-106">The `sql:is-constant` annotation can be specified on an element that does not have any attributes.</span></span> <span data-ttu-id="e4be2-107">如果該註解是在值為 True (或 1) 的元素上指定，該元素不會對應到資料庫，但是仍會出現在 XML 文件中。</span><span class="sxs-lookup"><span data-stu-id="e4be2-107">If it is specified on an element with the value true (or 1), that element is not mapped to the database but still appears in the XML document.</span></span>  
  
 <span data-ttu-id="e4be2-108">`sql:is-constant` 註解可以用於：</span><span class="sxs-lookup"><span data-stu-id="e4be2-108">The `sql:is-constant` annotation can be used for:</span></span>  
  
-   <span data-ttu-id="e4be2-109">將最上層元素加入到 XML 文件中。</span><span class="sxs-lookup"><span data-stu-id="e4be2-109">Adding a top-level element to the XML document.</span></span> <span data-ttu-id="e4be2-110">XML 需要單一的最上層元素 (根元素) 供文件使用。</span><span class="sxs-lookup"><span data-stu-id="e4be2-110">XML requires a single top-level element (root element) for the document.</span></span>  
  
-   <span data-ttu-id="e4be2-111">建立容器元素，例如 **\<Orders>** 包裝所有訂單的元素。</span><span class="sxs-lookup"><span data-stu-id="e4be2-111">Creating container elements, such as an **\<Orders>** element that wraps all orders.</span></span>  
  
 <span data-ttu-id="e4be2-112">`sql:is-constant`批註可以加入至 **\<complexType>** 元素。</span><span class="sxs-lookup"><span data-stu-id="e4be2-112">The `sql:is-constant` annotation can be added to a **\<complexType>** element.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e4be2-113">範例</span><span class="sxs-lookup"><span data-stu-id="e4be2-113">Examples</span></span>  
 <span data-ttu-id="e4be2-114">若要使用下列範例建立工作範例，您必須符合某些需求。</span><span class="sxs-lookup"><span data-stu-id="e4be2-114">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="e4be2-115">如需詳細資訊，請參閱[執行 SQLXML 範例的需求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="e4be2-115">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-sqlis-constant-to-add-a-container-element"></a><span data-ttu-id="e4be2-116">A.</span><span class="sxs-lookup"><span data-stu-id="e4be2-116">A.</span></span> <span data-ttu-id="e4be2-117">指定 sql:is-constant 來加入容器元素</span><span class="sxs-lookup"><span data-stu-id="e4be2-117">Specifying sql:is-constant to add a container element</span></span>  
 <span data-ttu-id="e4be2-118">在這個批註式 XSD 架構中， **\<CustomerOrders>** 會藉由指定值為1的屬性，將定義為常數元素 `sql:is-constant` 。</span><span class="sxs-lookup"><span data-stu-id="e4be2-118">In this annotated XSD schema, **\<CustomerOrders>** is defined as a constant element by specifying the `sql:is-constant` attribute with a value of 1.</span></span> <span data-ttu-id="e4be2-119">因此， **\<CustomerOrders>** 不會對應到任何資料庫資料表或資料行。</span><span class="sxs-lookup"><span data-stu-id="e4be2-119">Therefore, **\<CustomerOrders>** is not mapped to any database table or column.</span></span> <span data-ttu-id="e4be2-120">這個常數元素是由 **\<Order>** 子項目所組成。</span><span class="sxs-lookup"><span data-stu-id="e4be2-120">This constant element consists of the **\<Order>** child elements.</span></span>  
  
 <span data-ttu-id="e4be2-121">雖然不 **\<CustomerOrders>** 會對應到任何資料庫資料表或資料行，但它仍會顯示在產生的 XML 中，做為包含子專案的容器元素 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="e4be2-121">Although **\<CustomerOrders>** does not map to any database table or column, it still appears in the resulting XML as a container element containing the **\<Order>** child elements.</span></span>  
  
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
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="CustomerOrders" sql:is-constant="1" >  
          <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"  
                           sql:relationship="CustOrders"   
                           maxOccurs="unbounded" >  
                <xsd:complexType>  
                   <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                   <xsd:attribute name="OrderDate" type="xsd:date" />  
                   <xsd:attribute name="CustomerID" type="xsd:string" />  
                </xsd:complexType>  
              </xsd:element>  
            </xsd:sequence>  
           </xsd:complexType>  
          </xsd:element>  
         </xsd:sequence>  
          <xsd:attribute name="CustomerID" type="xsd:string" />  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="e4be2-122">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="e4be2-122">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="e4be2-123">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="e4be2-123">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="e4be2-124">將檔案儲存為 isConstant.xml。</span><span class="sxs-lookup"><span data-stu-id="e4be2-124">Save the file as isConstant.xml.</span></span>  
  
2.  <span data-ttu-id="e4be2-125">複製下列範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="e4be2-125">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="e4be2-126">將檔案儲存為 isConstantT.xml，並儲存在與儲存 isConstant.xml 相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="e4be2-126">Save the file as isConstantT.xml in the same directory where you saved isConstant.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="isConstant.xml">  
            Customer[@CustomerID=1]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="e4be2-127">為對應結構描述 (isConstant.xml) 指定的目錄路徑，是儲存範本之目錄的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="e4be2-127">The directory path specified for the mapping schema (isConstant.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="e4be2-128">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="e4be2-128">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\isConstant.xml"  
    ```  
  
3.  <span data-ttu-id="e4be2-129">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="e4be2-129">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="e4be2-130">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="e4be2-130">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="e4be2-131">這是部分結果集：</span><span class="sxs-lookup"><span data-stu-id="e4be2-131">This is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
<Customer CustomerID="1">   
  <CustomerOrders>   
    <Order SalesOrderID="43860" OrderDate="2001-08-01" CustomerID="1" />   
    <Order SalesOrderID="44501" OrderDate="2001-11-01" CustomerID="1" />   
    <Order SalesOrderID="45283" OrderDate="2002-02-01" CustomerID="1" />   
    <Order SalesOrderID="46042" OrderDate="2002-05-01" CustomerID="1" />   
    ...  
  </CustomerOrders>   
</Customer>   
</ROOT>  
```  
  
  
