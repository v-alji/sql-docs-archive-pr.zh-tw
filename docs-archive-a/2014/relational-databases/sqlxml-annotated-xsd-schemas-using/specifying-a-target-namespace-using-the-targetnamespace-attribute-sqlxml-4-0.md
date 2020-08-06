---
title: 使用 targetNamespace 屬性來指定目標命名空間 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces [SQLXML], annotated XSD schemas
- targetNamespace attribute
- XSD schemas [SQLXML], target namespaces
- annotated XSD schemas, target namespaces
- xsd:targetNamespace
- attributeFormDefault attribute
- elementFormDefault attribute
- target namespaces [SQLXML]
ms.assetid: f3df9877-6672-4444-8245-2670063c9310
author: rothja
ms.author: jroth
ms.openlocfilehash: 823bcbf7f4906a2e1d2ced1ff58b681c0ca41a8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599426"
---
# <a name="specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-40"></a><span data-ttu-id="e6fe5-102">使用 targetNamespace 屬性來指定目標命名空間 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="e6fe5-102">Specifying a Target Namespace Using the targetNamespace Attribute (SQLXML 4.0)</span></span>
  <span data-ttu-id="e6fe5-103">在撰寫 XSD 架構時，您可以使用 XSD **targetNamespace**屬性來指定目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-103">In writing XSD schemas, you can use the XSD **targetNamespace** attribute to specify a target namespace.</span></span> <span data-ttu-id="e6fe5-104">本主題描述 XSD **targetNamespace**、 **elementFormDefault**和**attributeFormDefault**屬性如何作用、它們如何影響所產生的 XML 實例，以及如何使用命名空間來指定 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-104">This topic describes how the XSD **targetNamespace**, **elementFormDefault**, and **attributeFormDefault** attributes work, how they affect the XML instance that is generated, and how XPath queries are specified with namespaces.</span></span>  
  
 <span data-ttu-id="e6fe5-105">您可以使用**xsd： targetNamespace**屬性，將預設命名空間中的元素和屬性放入不同的命名空間。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-105">You can use the **xsd:targetNamespace** attribute to place elements and attributes from the default namespace into a different namespace.</span></span> <span data-ttu-id="e6fe5-106">您也可以指定本機宣告的元素及結構描述的屬性是否應該以命名空間限定的形式出現 (使用前置詞明確限定或是依照預設的隱含方式限定)。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-106">You can also specify whether the locally declared elements and attributes of the schema should appear qualified by a namespace, either explicitly by using a prefix or implicitly by default.</span></span> <span data-ttu-id="e6fe5-107">您可以在專案上使用**elementFormDefault**和**attributeFormDefault**屬性 **\<xsd:schema>** ，以全域指定本機專案和屬性的限定性，也可以使用**form**屬性來分別指定個別的元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-107">You can use the **elementFormDefault** and **attributeFormDefault** attributes on the **\<xsd:schema>** element to globally specify the qualification of local elements and attributes, or you can use the **form** attribute to specify individual elements and attributes separately.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e6fe5-108">範例</span><span class="sxs-lookup"><span data-stu-id="e6fe5-108">Examples</span></span>  
 <span data-ttu-id="e6fe5-109">若要使用下列範例建立工作範例，您必須符合某些需求。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-109">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="e6fe5-110">如需詳細資訊，請參閱[執行 SQLXML 範例的需求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-110">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-a-target-namespace"></a><span data-ttu-id="e6fe5-111">A.</span><span class="sxs-lookup"><span data-stu-id="e6fe5-111">A.</span></span> <span data-ttu-id="e6fe5-112">指定目標命名空間</span><span class="sxs-lookup"><span data-stu-id="e6fe5-112">Specifying a target namespace</span></span>  
 <span data-ttu-id="e6fe5-113">下列 XSD 架構會使用**xsd： targetNamespace**屬性來指定目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-113">The following XSD schema specifies a target namespace by using the **xsd:targetNamespace** attribute.</span></span> <span data-ttu-id="e6fe5-114">此架構也會將**elementFormDefault**和**attributeFormDefault**屬性值設定為「不**合格**」， (這些屬性的預設值) 。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-114">The schema also sets the **elementFormDefault** and **attributeFormDefault** attribute values to **"unqualified"** (the default value for these attributes).</span></span> <span data-ttu-id="e6fe5-115">這是全域宣告，並會影響架構 **\<Order>**) 中 (**CustomerID**、**連絡人**和**訂單**的屬性) 和屬性中 (的所有本機專案。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-115">This is a global declaration and affects all the local elements (**\<Order>** in the schema) and attributes (**CustomerID**, **ContactName**, and **OrderID** in the schema).</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
            xmlns:CO="urn:MyNamespace"   
            targetNamespace="urn:MyNamespace" >  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer"   
               sql:relation="Sales.Customer"   
               type="CO:CustomerType" />  
  
  <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                     sql:relationship="CustOrders"  
                     type="CO:OrderType" />  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
        <xsd:attribute name="SalesPersonID"  type="xsd:string" />  
  </xsd:complexType>  
  <xsd:complexType name="OrderType" >  
     <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
     <xsd:attribute name="CustomerID" type="xsd:string" />  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 <span data-ttu-id="e6fe5-116">在此結構描述中：</span><span class="sxs-lookup"><span data-stu-id="e6fe5-116">In the schema:</span></span>  
  
-   <span data-ttu-id="e6fe5-117">**CustomerType**和**OrderType**類型宣告是全域的，因此會包含在架構的目標命名空間中。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-117">The **CustomerType** and **OrderType** type declarations are global and, therefore, are included in the schema's target namespace.</span></span> <span data-ttu-id="e6fe5-118">因此，在專案及其子專案的宣告中參考這些類型時 **\<Customer>** ，會 **\<Order>** 指定與目標命名空間相關聯的前置詞。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-118">As a result, when these types are referenced in the declaration of **\<Customer>** element and its **\<Order>** child element, a prefix is specified that is associated with the target namespace.</span></span>  
  
-   <span data-ttu-id="e6fe5-119">**\<Customer>** 元素也會包含在架構的目標命名空間中，因為它是架構中的全域元素。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-119">The **\<Customer>** element is also included in the target namespace of the schema because it is a global element in the schema.</span></span>  
  
 <span data-ttu-id="e6fe5-120">針對此結構描述執行下列 XPath 查詢：</span><span class="sxs-lookup"><span data-stu-id="e6fe5-120">Execute the following XPath query against the schema:</span></span>  
  
```  
(/CO:Customer[@CustomerID=1)   
```  
  
 <span data-ttu-id="e6fe5-121">XPath 查詢會產生這個執行個體文件 (只顯示一些訂單)：</span><span class="sxs-lookup"><span data-stu-id="e6fe5-121">The XPath query generates this instance document (only a few of the orders are shown):</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <y0:Customer xmlns:y0="urn:MyNamespace"   
      CustomerID="ALFKI" ContactName="Maria Anders">  
        <Order CustomerID="ALFKI" OrderID="10643" />   
        <Order CustomerID="ALFKI" OrderID="10692" />   
        ...  
  </y0:Customer>  
  </ROOT>  
```  
  
 <span data-ttu-id="e6fe5-122">這個實例檔會定義 urn： MyNamespace 命名空間，並將前置詞 (y0) 關聯。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-122">This instance document defines the urn:MyNamespace namespace and associates a prefix (y0) to it.</span></span> <span data-ttu-id="e6fe5-123">前置詞僅適用于 **\<Customer>** 全域元素。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-123">The prefix is applied only to the **\<Customer>** global element.</span></span> <span data-ttu-id="e6fe5-124"> (專案是全域的，因為它會宣告為 **\<xsd:schema>** 架構中元素的子系。 ) </span><span class="sxs-lookup"><span data-stu-id="e6fe5-124">(The element is global because it is declared as a child of **\<xsd:schema>** element in the schema.)</span></span>  
  
 <span data-ttu-id="e6fe5-125">前置詞不會套用至本機專案和屬性，因為在架構中， **elementFormDefault**和**attributeFormDefault**屬性的值設定為「不**合格**」。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-125">The prefix is not applied to the local elements and attributes because the value of **elementFormDefault** and **attributeFormDefault** attributes is set to **"unqualified"** in the schema.</span></span> <span data-ttu-id="e6fe5-126">請注意，專案 **\<Order>** 是本機的，因為它的宣告會顯示為定義專案之元素的子系 **\<complexType>** **\<CustomerType>** 。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-126">Note that the **\<Order>** element is local because its declaration appears as a child of the **\<complexType>** element that defines the **\<CustomerType>** element.</span></span> <span data-ttu-id="e6fe5-127">同樣地， (**CustomerID**、「**訂單**」和「**連絡人姓名**」) 的屬性是 local，而不是 global。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-127">Similarly, the attributes (**CustomerID**, **OrderID**, and **ContactName**) are local, not global.</span></span>  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a><span data-ttu-id="e6fe5-128">若要建立這個結構描述的工作範例</span><span class="sxs-lookup"><span data-stu-id="e6fe5-128">To create a working sample of this schema</span></span>  
  
1.  <span data-ttu-id="e6fe5-129">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-129">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="e6fe5-130">將此檔案儲存為 targetNameSpace.xml。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-130">Save the file as targetNameSpace.xml.</span></span>  
  
2.  <span data-ttu-id="e6fe5-131">複製下列範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-131">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="e6fe5-132">將檔案儲存為 targetNameSpaceT.xml，並放在與 targetNamespace.xml 相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-132">Save the file as targetNameSpaceT.xml in the same directory where you saved targetNamespace.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="targetNamespace.xml"  
                       xmlns:CO="urn:MyNamespace" >  
        /CO:Customer[@CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="e6fe5-133">範本中的 XPath 查詢會傳回 **\<Customer>** CustomerID 為1之客戶的元素。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-133">The XPath query in the template returns the **\<Customer>** element for the customer with a CustomerID of 1.</span></span> <span data-ttu-id="e6fe5-134">請注意，XPath 查詢會針對此查詢中的元素 (而不是屬性) 來指定命名空間前置詞 </span><span class="sxs-lookup"><span data-stu-id="e6fe5-134">Note that the XPath query specifies the namespace prefix for the element in the query and not for the attribute.</span></span> <span data-ttu-id="e6fe5-135">(如同結構描述中所指定，本機屬性並未限定)。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-135">(Local attributes are not qualified, as specified in the schema.)</span></span>  
  
     <span data-ttu-id="e6fe5-136">針對對應結構描述 (targetNamespace.xml) 所指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-136">The directory path specified for the mapping schema (targetNamespace.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="e6fe5-137">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="e6fe5-137">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\targetNamepsace.xml"  
    ```  
  
3.  <span data-ttu-id="e6fe5-138">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-138">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="e6fe5-139">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-139">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="e6fe5-140">如果架構指定具有 **"合格"** 值的**elementFormDefault**和**attributeFormDefault**屬性，實例檔將會具有所有本機專案和限定的屬性。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-140">If the schema specifies **elementFormDefault** and **attributeFormDefault** attributes with value **"qualified"**, the instance document will have all of the local elements and attributes qualified.</span></span> <span data-ttu-id="e6fe5-141">您可以變更先前的架構，以將這些屬性包含在 **\<xsd:schema>** 元素中，然後再次執行範本。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-141">You can change the previous schema to include these attributes in the **\<xsd:schema>** element and execute the template again.</span></span> <span data-ttu-id="e6fe5-142">因為這些屬性現在也會在此執行個體中限定，所以 XPath 查詢將會變更為可包含命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="e6fe5-142">Because the attributes are now also qualified in the instance, the XPath query will change to include the namespace prefix.</span></span>  
  
 <span data-ttu-id="e6fe5-143">這是修改過的 XPath 查詢：</span><span class="sxs-lookup"><span data-stu-id="e6fe5-143">This is the revised XPath query:</span></span>  
  
```  
/CO:Customer[@CO:CustomerID=1]  
```  
  
 <span data-ttu-id="e6fe5-144">這是傳回的 XML 文件：</span><span class="sxs-lookup"><span data-stu-id="e6fe5-144">This is the XML document that is returned:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <y0:Customer xmlns:y0="urn:MyNamespace" CustomerID="1" SalesPersonID="280">  
      <Order SalesOrderID="43860" CustomerID="1" />   
      <Order SalesOrderID="44501" CustomerID="1" />   
      <Order SalesOrderID="45283" CustomerID="1" />   
      <Order SalesOrderID="46042" CustomerID="1" />   
   </y0:Customer>  
</ROOT>  
```  
  
  
