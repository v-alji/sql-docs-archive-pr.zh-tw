---
title: 在 Updategram 中指定批註式對應架構 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, updategrams
- data types [SQLXML], mapping schema in updategrams
- updategrams [SQLXML], annotated mapping schemas
- annotated XDR schemas, updategrams
- inverse attribute
- parent-child relationships [SQLXML]
- mapping-schema attribute
- mapping schema [SQLXML], updategrams
- sql:inverse
ms.assetid: 2e266ed9-4cfb-434a-af55-d0839f64bb9a
author: rothja
ms.author: jroth
ms.openlocfilehash: a181b3081b51cca160709703364c248e495e0214
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597740"
---
# <a name="specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-40"></a><span data-ttu-id="9280c-102">在 Updategram 中指定註解式對應結構描述 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="9280c-102">Specifying an Annotated Mapping Schema in an Updategram (SQLXML 4.0)</span></span>
  <span data-ttu-id="9280c-103">本主題說明 Updategram 中指定的對應結構描述 (XSD 或 XDR) 要如何用來處理更新。</span><span class="sxs-lookup"><span data-stu-id="9280c-103">This topic explains how the mapping schema (XSD or XDR) that is specified in an updategram is used to process the updates.</span></span> <span data-ttu-id="9280c-104">在 updategram 中，您可以提供批註對應架構的名稱，以用於將 updategram 中的元素和屬性對應至中的資料表和資料行 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9280c-104">In an updategram, you can provide the name of an annotated mapping schema to use in mapping the elements and attributes in the updategram to tables and columns in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9280c-105">在 updategram 中指定對應結構描述時，此 updategram 中指定的元素和屬性名稱必須對應到對應結構描述內的元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="9280c-105">When a mapping schema is specified in an updategram, the element and attribute names that are specified in the updategram must map to the elements and attributes in the mapping schema.</span></span>  
  
 <span data-ttu-id="9280c-106">若要指定對應架構，您可以使用 `mapping-schema` 元素的屬性 **\<sync>** 。</span><span class="sxs-lookup"><span data-stu-id="9280c-106">To specify a mapping schema, you use the `mapping-schema` attribute of the **\<sync>** element.</span></span> <span data-ttu-id="9280c-107">下列範例會示範兩個 updategram：使用簡單對應結構描述的 updategram 以及使用更複雜之結構描述的 updategram。</span><span class="sxs-lookup"><span data-stu-id="9280c-107">The following examples show two updategrams: one that uses a simple mapping schema, and one that uses a more complex schema.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9280c-108">本文件集假設您非常熟悉 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的範本和對應結構描述支援。</span><span class="sxs-lookup"><span data-stu-id="9280c-108">This documentation assumes that you are familiar with templates and mapping schema support in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9280c-109">如需詳細資訊，請參閱[批註式 XSD 架構簡介 &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="9280c-109">For more information, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md).</span></span> <span data-ttu-id="9280c-110">如需使用 XDR 的繼承應用程式，請參閱[SQLXML 4.0&#41;中 &#40;已被取代的批註式 XDR 架構](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="9280c-110">For legacy applications that use XDR, see [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
## <a name="dealing-with-data-types"></a><span data-ttu-id="9280c-111">處理資料類型</span><span class="sxs-lookup"><span data-stu-id="9280c-111">Dealing with Data Types</span></span>  
 <span data-ttu-id="9280c-112">如果架構 `image` `binary` 使用) 來指定、或 `varbinary` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料類型 (， `sql:datatype` 而且未指定 xml 資料類型，則 updategram 會假設 xml 資料類型為 `binary base 64` 。</span><span class="sxs-lookup"><span data-stu-id="9280c-112">If the schema specifies the `image`, `binary`, or `varbinary`[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type (by using `sql:datatype`) and does not specify an XML data type, the updategram assumes that the XML data type is `binary base 64`.</span></span> <span data-ttu-id="9280c-113">如果您的資料是 `bin.base` 類型，您必須明確指定此類型 (`dt:type=bin.base` 或 `type="xsd:hexBinary"`)。</span><span class="sxs-lookup"><span data-stu-id="9280c-113">If your data is `bin.base` type, you must explicitly specify the type (`dt:type=bin.base` or `type="xsd:hexBinary"`).</span></span>  
  
 <span data-ttu-id="9280c-114">如果此結構描述指定 `dateTime`、`date` 或 `time` XSD 資料類型，您也必須使用 `sql:datatype="dateTime"` 來指定對應的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="9280c-114">If the schema specifies the `dateTime`, `date`, or `time` XSD data type, you must also specify the corresponding [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type by using `sql:datatype="dateTime"`.</span></span>  
  
 <span data-ttu-id="9280c-115">處理類型的參數時 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `money` ，您必須在對應 `sql:datatype="money"` 架構的適當節點上明確指定。</span><span class="sxs-lookup"><span data-stu-id="9280c-115">When handling parameters of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `money` type, you must explicitly specify `sql:datatype="money"` on the appropriate node in the mapping schema.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9280c-116">範例</span><span class="sxs-lookup"><span data-stu-id="9280c-116">Examples</span></span>  
 <span data-ttu-id="9280c-117">若要使用下列範例建立工作範例，您必須符合[執行 SQLXML 範例的需求](../../sqlxml/requirements-for-running-sqlxml-examples.md)中所指定的需求。</span><span class="sxs-lookup"><span data-stu-id="9280c-117">To create working samples using the following examples, you must meet the requirements specified in [Requirements for Running SQLXML Examples](../../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-creating-an-updategram-with-a-simple-mapping-schema"></a><span data-ttu-id="9280c-118">A.</span><span class="sxs-lookup"><span data-stu-id="9280c-118">A.</span></span> <span data-ttu-id="9280c-119">使用簡單對應結構描述建立 updategram</span><span class="sxs-lookup"><span data-stu-id="9280c-119">Creating an updategram with a simple mapping schema</span></span>  
 <span data-ttu-id="9280c-120">下列 XSD 架構 ( # A0) 是對應架構，其會將 **\<Customer>** 元素對應至 Sales. Customer 資料表：</span><span class="sxs-lookup"><span data-stu-id="9280c-120">The following XSD schema (SampleSchema.xml) is a mapping schema that maps the **\<Customer>** element to the Sales.Customer table:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
        <xsd:attribute name="CustID"    
                       sql:field="CustomerID"   
                       type="xsd:string" />  
        <xsd:attribute name="RegionID"    
                       sql:field="TerritoryID"    
                       type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="9280c-121">下列 updategram 會將一筆記錄插入 Sales.Customer 資料表，並依賴之前的對應結構描述，適當地將此資料對應至資料表。</span><span class="sxs-lookup"><span data-stu-id="9280c-121">The following updategram inserts a record into the Sales.Customer table and relies on the previous mapping schema to properly map this data to the table.</span></span> <span data-ttu-id="9280c-122">請注意，updategram 會使用相同的元素名稱， **\<Customer>** 如架構中所定義。</span><span class="sxs-lookup"><span data-stu-id="9280c-122">Notice that the updategram uses the same element name, **\<Customer>**, as defined in the schema.</span></span> <span data-ttu-id="9280c-123">這是強制性的作法，因為 updategram 會指定特定的結構描述。</span><span class="sxs-lookup"><span data-stu-id="9280c-123">This is mandatory because the updategram specifies a particular schema.</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="9280c-124">若要測試 Updategram</span><span class="sxs-lookup"><span data-stu-id="9280c-124">To test the updategram</span></span>  
  
1.  <span data-ttu-id="9280c-125">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="9280c-125">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="9280c-126">將檔案儲存為 SampleUpdateSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="9280c-126">Save the file as SampleUpdateSchema.xml.</span></span>  
  
2.  <span data-ttu-id="9280c-127">複製底下的 updategram 範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="9280c-127">Copy the updategram template below and paste it into a text file.</span></span> <span data-ttu-id="9280c-128">將檔案儲存為 SampleUpdategram.xml 並放在與 SampleUpdateSchema.xml 相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="9280c-128">Save the file as SampleUpdategram.xml in the same directory where you saved SampleUpdateSchema.xml.</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleUpdateSchema.xml">  
        <updg:before>  
          <Customer CustID="1" RegionID="1"  />  
        </updg:before>  
        <updg:after>  
          <Customer CustID="1" RegionID="2" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="9280c-129">針對對應結構描述 (SampleUpdateSchema.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="9280c-129">The directory path specified for the mapping schema (SampleUpdateSchema.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="9280c-130">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="9280c-130">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
3.  <span data-ttu-id="9280c-131">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="9280c-131">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="9280c-132">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="9280c-132">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="9280c-133">這是相等的 XDR 結構描述：</span><span class="sxs-lookup"><span data-stu-id="9280c-133">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
   <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
         xmlns:dt="urn:schemas-microsoft-com:datatypes"   
         xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
     <ElementType name="Customer" sql:relation="Sales.Customer" >  
       <AttributeType name="CustID" />  
       <AttributeType name="RegionID" />  
  
       <attribute type="CustID" sql:field="CustomerID" />  
       <attribute type="RegionID" sql:field="TerritoryID" />  
     </ElementType>  
   </Schema>   
```  
  
### <a name="b-inserting-a-record-by-using-the-parent-child-relationship-specified-in-the-mapping-schema"></a><span data-ttu-id="9280c-134">B.</span><span class="sxs-lookup"><span data-stu-id="9280c-134">B.</span></span> <span data-ttu-id="9280c-135">使用對應結構描述內指定的父子式關聯性插入記錄</span><span class="sxs-lookup"><span data-stu-id="9280c-135">Inserting a record by using the parent-child relationship specified in the mapping schema</span></span>  
 <span data-ttu-id="9280c-136">結構描述元素可以產生關聯。</span><span class="sxs-lookup"><span data-stu-id="9280c-136">Schema elements can be related.</span></span> <span data-ttu-id="9280c-137">**\<sql:relationship>** 元素會指定架構元素之間的父子式關聯性。</span><span class="sxs-lookup"><span data-stu-id="9280c-137">The **\<sql:relationship>** element specifies the parent-child relationship between the schema elements.</span></span> <span data-ttu-id="9280c-138">這項資訊是用來更新具有主索引鍵與外部索引鍵關聯性的對應資料表。</span><span class="sxs-lookup"><span data-stu-id="9280c-138">This information is used to update corresponding tables that have primary-key/foreign-key relationship.</span></span>  
  
 <span data-ttu-id="9280c-139">下列對應架構 ( # A0) 是由兩個元素所 **\<Order>** 組成 **\<OD>** ：</span><span class="sxs-lookup"><span data-stu-id="9280c-139">The following mapping schema (SampleSchema.xml) consists of two elements, **\<Order>** and **\<OD>**:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="OD"   
                     sql:relation="Sales.SalesOrderDetail"  
                     sql:relationship="OrderOD" >  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID"   type="xsd:integer" />  
              <xsd:attribute name="ProductID" type="xsd:integer" />  
             <xsd:attribute name="UnitPrice"  type="xsd:decimal" />  
             <xsd:attribute name="OrderQty"   type="xsd:integer" />  
             <xsd:attribute name="UnitPriceDiscount"   type="xsd:decimal" />  
  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
        <xsd:attribute name="SalesOrderID"  type="xsd:integer" />  
        <xsd:attribute name="OrderDate"  type="xsd:date" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="9280c-140">下列 updategram 會使用這個 XSD 架構，將新的訂單詳細資料記錄新增 (訂單 **\<OD>** **\<after>** 43860 中區塊) 的元素。</span><span class="sxs-lookup"><span data-stu-id="9280c-140">The following updategram uses this XSD schema to add a new order detail record (an **\<OD>** element in the **\<after>** block) for order 43860.</span></span> <span data-ttu-id="9280c-141">`mapping-schema` 屬性是用來指定 updategram 中的對應結構描述。</span><span class="sxs-lookup"><span data-stu-id="9280c-141">The `mapping-schema` attribute is used to specify the mapping schema in the updategram.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="SampleUpdateSchema.xml" >  
    <updg:before>  
       <Order SalesOrderID="43860" />  
    </updg:before>  
    <updg:after>  
      <Order SalesOrderID="43860" >  
           <OD ProductID="753" UnitPrice="$10.00"  
               Quantity="5" Discount="0.0" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="9280c-142">若要測試 Updategram</span><span class="sxs-lookup"><span data-stu-id="9280c-142">To test the updategram</span></span>  
  
1.  <span data-ttu-id="9280c-143">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="9280c-143">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="9280c-144">將檔案儲存為 SampleUpdateSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="9280c-144">Save the file as SampleUpdateSchema.xml.</span></span>  
  
2.  <span data-ttu-id="9280c-145">複製上述的 updategram 範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="9280c-145">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="9280c-146">將檔案儲存為 SampleUpdategram.xml 並放在與 SampleUpdateSchema.xml 相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="9280c-146">Save the file as SampleUpdategram.xml in the same directory where you saved SampleUpdateSchema.xml.</span></span>  
  
     <span data-ttu-id="9280c-147">針對對應結構描述 (SampleUpdateSchema.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="9280c-147">The directory path specified for the mapping schema (SampleUpdateSchema.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="9280c-148">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="9280c-148">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
3.  <span data-ttu-id="9280c-149">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="9280c-149">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="9280c-150">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="9280c-150">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="9280c-151">這是相等的 XDR 結構描述：</span><span class="sxs-lookup"><span data-stu-id="9280c-151">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="OD" sql:relation="Sales.SalesOrderDetail" >  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="ProductID" />  
    <AttributeType name="UnitPrice"  dt:type="fixed.14.4" />  
    <AttributeType name="OrderQty" />  
    <AttributeType name="UnitPriceDiscount" />  
  
    <attribute type="SalesOrderID" />  
    <attribute type="ProductID" />  
    <attribute type="UnitPrice" />  
    <attribute type="OrderQty" />  
    <attribute type="UnitPriceDiscount" />  
</ElementType>  
  
<ElementType name="Order" sql:relation="Sales.SalesOrderHeader" >  
    <AttributeType name="CustomerID" />  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="OrderDate" />  
  
    <attribute type="CustomerID" />  
    <attribute type="SalesOrderID" />  
    <attribute type="OrderDate" />  
    <element type="OD" >  
             <sql:relationship   
                   key-relation="Sales.SalesOrderHeader"  
                   key="SalesOrderID"  
                   foreign-key="SalesOrderID"  
                   foreign-relation="Sales.SalesOrderDetail" />  
    </element>  
</ElementType>  
</Schema>  
```  
  
### <a name="c-inserting-a-record-by-using-the-parent-child-relationship-and-inverse-annotation-specified-in-the-xsd-schema"></a><span data-ttu-id="9280c-152">C.</span><span class="sxs-lookup"><span data-stu-id="9280c-152">C.</span></span> <span data-ttu-id="9280c-153">使用 XSD 結構描述內指定的父子式關聯性和反向註解來插入記錄</span><span class="sxs-lookup"><span data-stu-id="9280c-153">Inserting a record by using the parent-child relationship and inverse annotation specified in the XSD schema</span></span>  
 <span data-ttu-id="9280c-154">這個範例會說明 updategram 邏輯要如何使用 XSD 中指定的父子式關聯性來處理更新，以及如何使用 `inverse` 註解。</span><span class="sxs-lookup"><span data-stu-id="9280c-154">This example illustrates how the updategram logic uses the parent-child relationship specified in the XSD to process updates, and how the `inverse` annotation is used.</span></span> <span data-ttu-id="9280c-155">如需批註的詳細資訊 `inverse` ，請參閱在[sql： RELATIONSHIP &#40;SQLXML 4.0&#41;上指定 sql：反向屬性](../../sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="9280c-155">For more information about the `inverse` annotation, see [Specifying the sql:inverse Attribute on sql:relationship &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="9280c-156">這個範例假設下列資料表是在**tempdb**資料庫中：</span><span class="sxs-lookup"><span data-stu-id="9280c-156">This example assumes that the following tables are in the **tempdb** database:</span></span>  
  
-   <span data-ttu-id="9280c-157">`Cust (CustomerID, CompanyName)`，其中 `CustomerID` 是主索引鍵</span><span class="sxs-lookup"><span data-stu-id="9280c-157">`Cust (CustomerID, CompanyName)`, where `CustomerID` is the primary key</span></span>  
  
-   <span data-ttu-id="9280c-158">`Ord (OrderID, CustomerID)`，其中 `CustomerID` 是參考 `CustomerID` 資料表內之 `Cust` 主索引鍵的外部索引鍵。</span><span class="sxs-lookup"><span data-stu-id="9280c-158">`Ord (OrderID, CustomerID)`, where `CustomerID` is a foreign key that refers to the `CustomerID` primary key in the `Cust` table.</span></span>  
  
 <span data-ttu-id="9280c-159">updategram 會使用以下 XSD 結構描述，將記錄插入 Cust 和 Ord 資料表中：</span><span class="sxs-lookup"><span data-stu-id="9280c-159">The updategram uses the following XSD schema to insert records into the Cust and Ord tables :</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
       <sql:relationship name="OrdCust" inverse="true"  
                  parent="Ord"  
                  parent-key="CustomerID"  
                  child-key="CustomerID"  
                  child="Cust"/>  
  </xsd:appinfo>  
</xsd:annotation>  
  
<xsd:element name="Order" sql:relation="Ord">  
  <xsd:complexType>  
    <xsd:sequence>  
      <xsd:element ref="Customer" sql:relationship="OrdCust"/>  
    </xsd:sequence>  
    <xsd:attribute name="OrderID"   type="xsd:int"/>  
    <xsd:attribute name="CustomerID" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:element>  
  
<xsd:element name="Customer" sql:relation="Cust">  
  <xsd:complexType>  
     <xsd:attribute name="CustomerID"  type="xsd:string"/>  
    <xsd:attribute name="CompanyName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:element>  
  
</xsd:schema>  
```  
  
 <span data-ttu-id="9280c-160">這個範例中的 XSD 架構具有 **\<Customer>** 和 **\<Order>** 元素，而且它會指定兩個元素之間的父子式關聯性。</span><span class="sxs-lookup"><span data-stu-id="9280c-160">The XSD schema in this example has **\<Customer>** and **\<Order>** elements, and it specifies a parent-child relationship between the two elements.</span></span> <span data-ttu-id="9280c-161">它會 **\<Order>** 將識別為父元素和 **\<Customer>** 子專案。</span><span class="sxs-lookup"><span data-stu-id="9280c-161">It identifies **\<Order>** as the parent element and **\<Customer>** as the child element.</span></span>  
  
 <span data-ttu-id="9280c-162">此 updategram 處理邏輯會使用有關父子式關聯性的資訊來判斷哪些記錄會插入資料表中。</span><span class="sxs-lookup"><span data-stu-id="9280c-162">The updategram processing logic uses the information about the parent-child relationship to determine the order in which records are inserted into tables.</span></span> <span data-ttu-id="9280c-163">在此範例中，updategram 邏輯會先嘗試將記錄插入至 Ord 資料表 (，因為 **\<Order>** 是父) ，然後嘗試將記錄插入至「加入」資料表 (，因為 **\<Customer>** 是子) 。</span><span class="sxs-lookup"><span data-stu-id="9280c-163">In this example, the updategram logic first attempts to insert a record into the Ord table (because **\<Order>** is the parent) and then attempts to insert a record into the Cust table (because **\<Customer>** is the child).</span></span> <span data-ttu-id="9280c-164">但是，由於包含在資料庫資料表結構描述內之主索引鍵/外部索引鍵資訊的緣故，這項插入作業會造成資料庫中的外部索引鍵違規，而使得插入失敗。</span><span class="sxs-lookup"><span data-stu-id="9280c-164">However, because of the primary key/foreign key information that is contained in the database table schema, this insert operation causes a foreign key violation in the database and the insert fails.</span></span>  
  
 <span data-ttu-id="9280c-165">若要指示 updategram 邏輯在更新作業期間反轉父子式關聯性，請在 `inverse` 元素上指定批註 **\<relationship>** 。</span><span class="sxs-lookup"><span data-stu-id="9280c-165">To instruct the updategram logic to reverse the parent-child relationship during the update operation, the `inverse` annotation is specified on the **\<relationship>** element.</span></span> <span data-ttu-id="9280c-166">因此，記錄會先加入到 Cust 資料表，然後再加入到 Ord 資料表，作業就會成功。</span><span class="sxs-lookup"><span data-stu-id="9280c-166">As a result, records are added first in the Cust table and then in the Ord table, and the operation succeeds.</span></span>  
  
 <span data-ttu-id="9280c-167">下列 updategram 會使用指定的 XSD 結構描述，將訂單 (OrderID=2) 插入到 Ord 資料表，並將客戶 (CustomerID='AAAAA') 插入到 Cust 資料表：</span><span class="sxs-lookup"><span data-stu-id="9280c-167">The following updategram inserts an order (OrderID=2) in the Ord table and a customer (CustomerID='AAAAA') in the Cust table by using the specified XSD schema:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="SampleUpdateSchema.xml" >  
    <updg:before/>  
    <updg:after>  
      <Order OrderID="2" CustomerID="AAAAA" >  
        <Customer CustomerID="AAAAA" CompanyName="AAAAA Company" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="9280c-168">若要測試 Updategram</span><span class="sxs-lookup"><span data-stu-id="9280c-168">To test the updategram</span></span>  
  
1.  <span data-ttu-id="9280c-169">在**tempdb**資料庫中建立這些資料表：</span><span class="sxs-lookup"><span data-stu-id="9280c-169">Create these tables in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust(CustomerID varchar(5) primary key,   
                      CompanyName varchar(20))  
    GO  
    CREATE TABLE Ord (OrderID int primary key,   
                      CustomerID varchar(5) references Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="9280c-170">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="9280c-170">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="9280c-171">將檔案儲存為 SampleUpdateSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="9280c-171">Save the file as SampleUpdateSchema.xml.</span></span>  
  
3.  <span data-ttu-id="9280c-172">複製上述的 updategram 範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="9280c-172">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="9280c-173">將檔案儲存為 SampleUpdategram.xml 並放在與 SampleUpdateSchema.xml 相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="9280c-173">Save the file as SampleUpdategram.xml in the same directory where you saved SampleUpdateSchema.xml.</span></span>  
  
     <span data-ttu-id="9280c-174">針對對應結構描述 (SampleUpdateSchema.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="9280c-174">The directory path specified for the mapping schema (SampleUpdateSchema.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="9280c-175">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="9280c-175">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
4.  <span data-ttu-id="9280c-176">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="9280c-176">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="9280c-177">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="9280c-177">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9280c-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9280c-178">See Also</span></span>  
 [<span data-ttu-id="9280c-179">&#40;SQLXML 4.0&#41;的 Updategram 安全性考慮</span><span class="sxs-lookup"><span data-stu-id="9280c-179">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
