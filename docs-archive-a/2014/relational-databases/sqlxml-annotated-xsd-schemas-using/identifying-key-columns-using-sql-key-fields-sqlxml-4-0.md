---
title: 使用 sql：索引鍵-欄位來識別索引鍵資料行 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- nesting XML results
- proper nesting in results [SQLXML]
- sql:key-fields
- XSD schemas [SQLXML], key columns
- identifying key columns [SQLXML]
- annotated XSD schemas, key columns
- key columns [SQLXML]
- relationships [SQLXML], key columns
- hierarchical relationships [SQLXML]
- key-fields annotation
ms.assetid: 1a5ad868-8602-45c4-913d-6fbb837eebb0
author: rothja
ms.author: jroth
ms.openlocfilehash: 0ab12b34874a54bad2e08a96d08ebd0cc994f946
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709025"
---
# <a name="identifying-key-columns-using-sqlkey-fields-sqlxml-40"></a><span data-ttu-id="a57e3-102">使用 sql:key-fields 來識別索引鍵資料行 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="a57e3-102">Identifying Key Columns Using sql:key-fields (SQLXML 4.0)</span></span>
  <span data-ttu-id="a57e3-103">針對 XSD 結構描述指定 XPath 查詢時，在大部分情況下都需要索引鍵資訊，才能在結果中取得正確的巢狀結構。</span><span class="sxs-lookup"><span data-stu-id="a57e3-103">When an XPath query is specified against an XSD schema, key information is required in most cases to obtain proper nesting in the result.</span></span> <span data-ttu-id="a57e3-104">指定 `sql:key-fields` 註解是確保產生適當階層的方式。</span><span class="sxs-lookup"><span data-stu-id="a57e3-104">Specifying the `sql:key-fields` annotation is a way of ensuring that the appropriate hierarchy is generated.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a57e3-105">若要確保正確的巢狀結構，建議您針對對應至資料表的元素指定 `sql:key-fields`。</span><span class="sxs-lookup"><span data-stu-id="a57e3-105">To ensure proper nesting, it is recommended that you specify `sql:key-fields` for elements that map to tables.</span></span> <span data-ttu-id="a57e3-106">產生的 XML 會區分基礎結果集的排序。</span><span class="sxs-lookup"><span data-stu-id="a57e3-106">The XML produced is sensitive to the ordering of the underlying result set.</span></span> <span data-ttu-id="a57e3-107">如果沒有指定 `sql:key-fields`，產生的 XML 格式可能會不正確。</span><span class="sxs-lookup"><span data-stu-id="a57e3-107">If `sql:key-fields` is not specified, the XML generated might not be formed properly.</span></span>  
  
 <span data-ttu-id="a57e3-108">`sql:key-fields` 的值會識別在關聯中唯一識別資料列的資料行。</span><span class="sxs-lookup"><span data-stu-id="a57e3-108">The value of `sql:key-fields` identifies the column(s) that uniquely identify the rows in the relation.</span></span> <span data-ttu-id="a57e3-109">如果需要多個資料行才能唯一識別某個資料列，這些資料行值就會以空格隔開。</span><span class="sxs-lookup"><span data-stu-id="a57e3-109">If more than one column is required to uniquely identify a row, the column values are delimited by spaces.</span></span>  
  
 <span data-ttu-id="a57e3-110">`sql:key-fields`當元素包含 **\<sql:relationship>** 定義于元素和子專案之間的，但未提供在父元素中指定之資料表的主鍵時，您必須使用注釋。</span><span class="sxs-lookup"><span data-stu-id="a57e3-110">You must use the `sql:key-fields` annotation when an element contains a **\<sql:relationship>** that is defined between the element and a child element but does not provide the primary key of the table that is specified in the parent element.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a57e3-111">範例</span><span class="sxs-lookup"><span data-stu-id="a57e3-111">Examples</span></span>  
 <span data-ttu-id="a57e3-112">若要使用下列範例建立工作範例，您必須符合某些需求。</span><span class="sxs-lookup"><span data-stu-id="a57e3-112">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="a57e3-113">如需詳細資訊，請參閱[執行 SQLXML 範例的需求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="a57e3-113">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-producing-the-appropriate-nesting-when-sqlrelationship-does-not-provide-sufficient-information"></a><span data-ttu-id="a57e3-114">A.</span><span class="sxs-lookup"><span data-stu-id="a57e3-114">A.</span></span> <span data-ttu-id="a57e3-115">當未提供足夠的資訊時，產生適當的嵌套 \<sql:relationship></span><span class="sxs-lookup"><span data-stu-id="a57e3-115">Producing the appropriate nesting when \<sql:relationship> does not provide sufficient information</span></span>  
 <span data-ttu-id="a57e3-116">這則範例會顯示必須指定 `sql:key-fields` 的位置。</span><span class="sxs-lookup"><span data-stu-id="a57e3-116">This example shows where `sql:key-fields` must be specified.</span></span>  
  
 <span data-ttu-id="a57e3-117">請考慮下列結構描述。</span><span class="sxs-lookup"><span data-stu-id="a57e3-117">Consider the following schema.</span></span> <span data-ttu-id="a57e3-118">架構會指定和專案之間的階層， **\<Order>** **\<Customer>** 其中專案 **\<Order>** 是父元素，而 **\<Customer>** 元素是子系。</span><span class="sxs-lookup"><span data-stu-id="a57e3-118">The schema specifies a hierarchy between the **\<Order>** and **\<Customer>** elements in which the **\<Order>** element is the parent and the **\<Customer>** element is a child.</span></span>  
  
 <span data-ttu-id="a57e3-119">**\<sql:relationship>** 標記是用來指定父子式關聯性。</span><span class="sxs-lookup"><span data-stu-id="a57e3-119">The **\<sql:relationship>** tag is used to specify the parent-child relationship.</span></span> <span data-ttu-id="a57e3-120">它會將 Sales.SalesOrderHeader 資料表中的 CustomerID 識別為參考 Sales.Customer 資料表中 CustomerID 子索引鍵的父索引鍵。</span><span class="sxs-lookup"><span data-stu-id="a57e3-120">It identifies CustomerID in the Sales.SalesOrderHeader table as the parent key that refers to the CustomerID child key in the Sales.Customer table.</span></span> <span data-ttu-id="a57e3-121">中提供的資訊 **\<sql:relationship>** 並不足以唯一識別父資料表中的資料列 (SalesOrderHeader) 。</span><span class="sxs-lookup"><span data-stu-id="a57e3-121">The information provided in **\<sql:relationship>** is not sufficient to uniquely identify rows in the parent table (Sales.SalesOrderHeader).</span></span> <span data-ttu-id="a57e3-122">因此，如果沒有 `sql:key-fields` 註解，產生的階層就會不正確。</span><span class="sxs-lookup"><span data-stu-id="a57e3-122">Therefore, without the `sql:key-fields` annotation, the hierarchy that is generated is inaccurate.</span></span>  
  
 <span data-ttu-id="a57e3-123">在 `sql:key-fields` 上指定了時 **\<Order>** ，批註會唯一識別父 (SalesOrderHeader 資料表) 中的資料列，而且其子項目會顯示在其父系之下。</span><span class="sxs-lookup"><span data-stu-id="a57e3-123">With `sql:key-fields` specified on **\<Order>**, the annotation uniquely identifies the rows in the parent (Sales.SalesOrderHeader table), and its child elements appear below its parent.</span></span>  
  
 <span data-ttu-id="a57e3-124">這是結構描述：</span><span class="sxs-lookup"><span data-stu-id="a57e3-124">This is the schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="OrdCust"  
        parent="Sales.SalesOrderHeader"  
        parent-key="CustomerID"  
        child="Sales.Customer"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"   
               sql:key-fields="SalesOrderID">  
   <xsd:complexType>  
     <xsd:sequence>  
     <xsd:element name="Customer" sql:relation="Sales.Customer"   
                       sql:relationship="OrdCust"  >  
       <xsd:complexType>  
         <xsd:attribute name="CustID" sql:field="CustomerID" />  
         <xsd:attribute name="SoldBy" sql:field="SalesPersonID" />  
       </xsd:complexType>  
     </xsd:element>  
     </xsd:sequence>  
     <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
     <xsd:attribute name= "CustomerID" type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a><span data-ttu-id="a57e3-125">若要建立這個結構描述的工作範例</span><span class="sxs-lookup"><span data-stu-id="a57e3-125">To create a working sample of this schema</span></span>  
  
1.  <span data-ttu-id="a57e3-126">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="a57e3-126">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="a57e3-127">將檔案儲存為 KeyFields1.xml。</span><span class="sxs-lookup"><span data-stu-id="a57e3-127">Save the file as KeyFields1.xml.</span></span>  
  
2.  <span data-ttu-id="a57e3-128">複製下列範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="a57e3-128">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="a57e3-129">將檔案儲存為 KeyFields1T.xml，並放在儲存 KeyFields1.xml 的相同目錄中。</span><span class="sxs-lookup"><span data-stu-id="a57e3-129">Save the file as KeyFields1T.xml in the same directory where you saved KeyFields1.xml.</span></span> <span data-ttu-id="a57e3-130">範本中的 XPath 查詢會傳回 **\<Order>** CustomerID 小於3的所有元素。</span><span class="sxs-lookup"><span data-stu-id="a57e3-130">The XPath query in the template returns all the **\<Order>** elements with a CustomerID of less than 3.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="KeyFields1.xml">  
            /Order[@CustomerID < 3]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="a57e3-131">針對對應結構描述 (KeyFields1.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="a57e3-131">The directory path specified for the mapping schema (KeyFields1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="a57e3-132">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="a57e3-132">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\KeyFields1.xml"  
    ```  
  
3.  <span data-ttu-id="a57e3-133">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="a57e3-133">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="a57e3-134">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="a57e3-134">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="a57e3-135">這是部分結果集：</span><span class="sxs-lookup"><span data-stu-id="a57e3-135">This is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
    <Order SalesOrderID="43860" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    <Order SalesOrderID="44501" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    <Order SalesOrderID="45283" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    .....  
</ROOT>  
```  
  
### <a name="b-specifying-sqlkey-fields-to-produce-proper-nesting-in-the-result"></a><span data-ttu-id="a57e3-136">B.</span><span class="sxs-lookup"><span data-stu-id="a57e3-136">B.</span></span> <span data-ttu-id="a57e3-137">指定 sql:key-fields 在結果中產生適當的巢狀結構</span><span class="sxs-lookup"><span data-stu-id="a57e3-137">Specifying sql:key-fields to produce proper nesting in the result</span></span>  
 <span data-ttu-id="a57e3-138">在下列架構中，沒有使用指定的階層 **\<sql:relationship>** 。</span><span class="sxs-lookup"><span data-stu-id="a57e3-138">In the following schema, there is no hierarchy specified using **\<sql:relationship>**.</span></span> <span data-ttu-id="a57e3-139">此結構描述仍然需要指定 `sql:key-fields` 註解，才能唯一識別 HumanResources.Employee 資料表中的員工。</span><span class="sxs-lookup"><span data-stu-id="a57e3-139">The schema still requires specifying the `sql:key-fields` annotation to uniquely identify employees in the HumanResources.Employee table.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="HumanResources.Employee" sql:key-fields="EmployeeID" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Title">  
          <xsd:complexType>  
            <xsd:simpleContent>  
              <xsd:extension base="xsd:string">  
                 <xsd:attribute name="EmployeeID" type="xsd:integer" />  
              </xsd:extension>  
            </xsd:simpleContent>  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
   </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a><span data-ttu-id="a57e3-140">若要建立這個結構描述的工作範例</span><span class="sxs-lookup"><span data-stu-id="a57e3-140">To create a working sample of this schema</span></span>  
  
1.  <span data-ttu-id="a57e3-141">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="a57e3-141">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="a57e3-142">將檔案儲存為 KeyFields2.xml。</span><span class="sxs-lookup"><span data-stu-id="a57e3-142">Save the file as KeyFields2.xml.</span></span>  
  
2.  <span data-ttu-id="a57e3-143">複製下列範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="a57e3-143">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="a57e3-144">將檔案儲存為 KeyFields2T.xml，並放在儲存 KeyFields2.xml 的相同目錄中。</span><span class="sxs-lookup"><span data-stu-id="a57e3-144">Save the file as KeyFields2T.xml in the same directory where you saved KeyFields2.xml.</span></span> <span data-ttu-id="a57e3-145">範本中的 XPath 查詢會傳回所有 **\<HumanResources.Employee>** 元素：</span><span class="sxs-lookup"><span data-stu-id="a57e3-145">The XPath query in the template returns all the **\<HumanResources.Employee>** elements:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="KeyFields2.xml">  
        /HumanResources.Employee  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="a57e3-146">針對對應結構描述 (KeyFields2.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="a57e3-146">The directory path specified for the mapping schema (KeyFields2.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="a57e3-147">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="a57e3-147">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\KeyFields2.xml"  
    ```  
  
3.  <span data-ttu-id="a57e3-148">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="a57e3-148">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="a57e3-149">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="a57e3-149">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="a57e3-150">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="a57e3-150">This is the result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <HumanResources.Employee>  
    <Title EmployeeID="1">Production Technician - WC60</Title>   
  </HumanResources.Employee>  
  <HumanResources.Employee>  
    <Title EmployeeID="2">Marketing Assistant</Title>   
  </HumanResources.Employee>  
  <HumanResources.Employee>  
    <Title EmployeeID="3">Engineering Manager</Title>   
  </HumanResources.Employee>  
  ...  
</ROOT>  
```  
  
  
