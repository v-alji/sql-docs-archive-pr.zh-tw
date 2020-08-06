---
title: 在查詢中使用批註式 XSD 架構 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML]
- inline schemas [SQLXML]
- XPath queries [SQLXML], annotated XSD schemas in queries
- queries [SQLXML], annotated XSD schemas
- retrieving data
- mapping schema [SQLXML], queries
- multiple inline schemas
- annotated XSD schemas, queries
- XSD schemas [SQLXML], queries
- templates [SQLXML], annotated XSD schemas in queries
ms.assetid: 927a30a2-eae8-420d-851d-551c5f884f3c
author: rothja
ms.author: jroth
ms.openlocfilehash: c3038ea234f707da7a87a030cb4110510f5a77c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597725"
---
# <a name="using-annotated-xsd-schemas-in-queries-sqlxml-40"></a><span data-ttu-id="d281b-102">在查詢中使用註解式 XSD 結構描述 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="d281b-102">Using Annotated XSD Schemas in Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="d281b-103">您可以針對 XSD 結構描述指定範本中的 XPath 查詢，藉以針對註解式結構描述指定查詢來擷取資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="d281b-103">You can specify queries against an annotated schema to retrieve data from the database by specifying XPath queries in a template against the XSD schema.</span></span>  
  
 <span data-ttu-id="d281b-104">**\<sql:xpath-query>** 元素可讓您針對批註式架構所定義的 XML view，指定 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="d281b-104">The **\<sql:xpath-query>** element allows you to specify an XPath query against the XML view that is defined by the annotated schema.</span></span> <span data-ttu-id="d281b-105">要對其執行 XPath 查詢的批註式架構，會使用專案的屬性來識別 `mapping-schema` **\<sql:xpath-query>** 。</span><span class="sxs-lookup"><span data-stu-id="d281b-105">The annotated schema against which the XPath query is to be executed is identified by using the `mapping-schema` attribute of the **\<sql:xpath-query>** element.</span></span>  
  
 <span data-ttu-id="d281b-106">範本是包含一或多個查詢的有效 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="d281b-106">Templates are valid XML documents that contain one or more queries.</span></span> <span data-ttu-id="d281b-107">FOR XML 和 XPath 查詢會傳回文件片段。</span><span class="sxs-lookup"><span data-stu-id="d281b-107">The FOR XML and XPath queries return a document fragment.</span></span> <span data-ttu-id="d281b-108">範本對於文件片段就像是容器一樣；因此，範本會提供一種方式來指定單一的上層元素。</span><span class="sxs-lookup"><span data-stu-id="d281b-108">Templates act as containers for the document fragments; templates thus provide a way to specify a single, top-level element.</span></span>  
  
 <span data-ttu-id="d281b-109">本主題中的範例會使用範本，針對註解式結構描述指定 XPath 查詢來擷取資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="d281b-109">The examples in this topic use templates to specify an XPath query against an annotated schema to retrieve data from the database.</span></span>  
  
 <span data-ttu-id="d281b-110">例如，請考慮下列註解式結構描述：</span><span class="sxs-lookup"><span data-stu-id="d281b-110">For example, consider this annotated schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID" type="xsd:string" />   
       <xsd:attribute name="FirstName" type="xsd:string" />   
       <xsd:attribute name="LastName"  type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="d281b-111">基於圖解用途，此 XSD 結構描述會以檔案名稱 Schema2.xml 儲存。</span><span class="sxs-lookup"><span data-stu-id="d281b-111">For the purpose of illustration, this XSD schema is stored in file named Schema2.xml.</span></span> <span data-ttu-id="d281b-112">接著，您可以針對註解式結構描述，在下列範本檔 (Schema2T.xml) 中指定 XPath 查詢：</span><span class="sxs-lookup"><span data-stu-id="d281b-112">You could then have an XPath query against the annotated schema specified in the following template file (Schema2T.xml):</span></span>  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql"  
     >  
          Person.Contact[@ContactID="1"]  
</sql:xpath-query>  
```  
  
 <span data-ttu-id="d281b-113">然後，您可以建立及使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs)，將查詢當做範本檔的一部分執行。</span><span class="sxs-lookup"><span data-stu-id="d281b-113">You can then create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the query as part of a template file.</span></span> <span data-ttu-id="d281b-114">如需詳細資訊，請參閱[SQLXML 4.0&#41;中 &#40;已被取代的批註式 XDR 架構](annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="d281b-114">For more information, see [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
## <a name="using-inline-mapping-schemas"></a><span data-ttu-id="d281b-115">使用內嵌的對應結構描述</span><span class="sxs-lookup"><span data-stu-id="d281b-115">Using Inline Mapping Schemas</span></span>  
 <span data-ttu-id="d281b-116">註解式結構描述可以直接包含在範本中，接著就可以針對內嵌的結構描述指定範本中的 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="d281b-116">An annotated schema can be included directly in a template, and then an XPath query can be specified in the template against the inline schema.</span></span> <span data-ttu-id="d281b-117">範本也可以是一個 Updategram。</span><span class="sxs-lookup"><span data-stu-id="d281b-117">The template can also be an updategram.</span></span>  
  
 <span data-ttu-id="d281b-118">一個範本可以包含多個內嵌結構描述。</span><span class="sxs-lookup"><span data-stu-id="d281b-118">A template can include multiple inline schemas.</span></span> <span data-ttu-id="d281b-119">若要使用範本中包含的內嵌架構，請在元素上指定具有唯一值的**id**屬性 **\<xsd:schema>** ，然後使用 **#idvalue**來參考內嵌架構。</span><span class="sxs-lookup"><span data-stu-id="d281b-119">To use an inline schema that is included in a template, specify the **id** attribute with a unique value on the **\<xsd:schema>** element, and then use **#idvalue** to reference the inline schema.</span></span> <span data-ttu-id="d281b-120">**Id**屬性的行為與**sql： id** ( {urn：架構-microsoft-com： xml-sql} id) 在 XDR 架構中使用的相同。</span><span class="sxs-lookup"><span data-stu-id="d281b-120">The **id** attribute is identical in behavior to the **sql:id** ({urn:schemas-microsoft-com:xml-sql}id) used in XDR schemas.</span></span>  
  
 <span data-ttu-id="d281b-121">例如，下列範本指定兩個內嵌的註解式結構描述：</span><span class="sxs-lookup"><span data-stu-id="d281b-121">For example, the following template specifies two inline-annotated schemas:</span></span>  
  
```  
<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'>  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
        xmlns:ms='urn:schemas-microsoft-com:mapping-schema'  
        id='InLineSchema1' sql:is-mapping-schema='1'>  
  <xsd:element name='Employees' ms:relation='HumanResources.Employee'>  
    <xsd:complexType>  
      <xsd:attribute name='LoginID'   
                     type='xsd:string'/>  
      <xsd:attribute name='Title'   
                     type='xsd:string'/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
        xmlns:ms='urn:schemas-microsoft-com:mapping-schema'  
        id='InLineSchema2' sql:is-mapping-schema='1'>  
  <xsd:element name='Contacts' ms:relation='Person.Contact'>  
    <xsd:complexType>  
  
      <xsd:attribute name='ContactID'   
                     type='xsd:string' />  
      <xsd:attribute name='FirstName'   
                     type='xsd:string' />  
      <xsd:attribute name='LastName'   
                     type='xsd:string' />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
  
<sql:xpath-query xmlns:sql='urn:schemas-microsoft-com:xml-sql'   
        mapping-schema='#InLineSchema1'>  
    /Employees[@LoginID='adventure-works\guy1']  
</sql:xpath-query>  
  
<sql:xpath-query xmlns:sql='urn:schemas-microsoft-com:xml-sql'   
        mapping-schema='#InLineSchema2'>  
    /Contacts[@ContactID='1']  
</sql:xpath-query>  
</ROOT>  
```  
  
 <span data-ttu-id="d281b-122">範本也會指定兩個 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="d281b-122">The template also specifies two XPath queries.</span></span> <span data-ttu-id="d281b-123">每個專案都會藉 **\<xpath-query>** 由指定屬性來唯一識別對應架構 `mapping-schema` 。</span><span class="sxs-lookup"><span data-stu-id="d281b-123">Each of the **\<xpath-query>** elements uniquely identifies the mapping schema by specifying the `mapping-schema` attribute.</span></span>  
  
 <span data-ttu-id="d281b-124">當您在範本中指定內嵌架構時， `sql:is-mapping-schema` 也必須在元素上指定批註 **\<xsd:schema>** 。</span><span class="sxs-lookup"><span data-stu-id="d281b-124">When you specify an inline schema in the template, the `sql:is-mapping-schema` annotation must also be specified on the **\<xsd:schema>** element.</span></span> <span data-ttu-id="d281b-125">`sql:is-mapping-schema` 會接受布林值 (0 = false，1 = true)。</span><span class="sxs-lookup"><span data-stu-id="d281b-125">The `sql:is-mapping-schema` takes a Boolean value (0=false, 1=true).</span></span> <span data-ttu-id="d281b-126">具有**sql： is-對應架構 = "1"** 的內嵌架構會被視為內嵌批註的架構，而且不會在 XML 檔中傳回。</span><span class="sxs-lookup"><span data-stu-id="d281b-126">An inline schema with **sql:is-mapping-schema="1"** is treated as inline annotated schema and is not returned in the XML document.</span></span>  
  
 <span data-ttu-id="d281b-127">`sql:is-mapping-schema` 註解屬於範本命名空間 `urn:schemas-microsoft-com:xml-sql`。</span><span class="sxs-lookup"><span data-stu-id="d281b-127">The `sql:is-mapping-schema` annotation belongs to the template namespace `urn:schemas-microsoft-com:xml-sql`.</span></span>  
  
 <span data-ttu-id="d281b-128">若要測試此範例，將範本 (InlineSchemaTemplate.xml) 儲存在本機目錄中，然後建立及使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 來執行範本。</span><span class="sxs-lookup"><span data-stu-id="d281b-128">To test this example, save the template (InlineSchemaTemplate.xml) in a local directory and then create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span> <span data-ttu-id="d281b-129">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="d281b-129">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="d281b-130">除了在 `mapping-schema` 範本的專案上指定屬性 **\<sql:xpath-query>** (當有 XPath 查詢) 或 updategram 中的 **\<updg:sync>** 元素時，您也可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d281b-130">In addition to specifying the `mapping-schema` attribute on the **\<sql:xpath-query>** element in a template (when there is an XPath query), or on **\<updg:sync>** element in an updategram, you can do the following:</span></span>  
  
-   <span data-ttu-id="d281b-131">在 `mapping-schema` **\<ROOT>** 範本中 (全域宣告) 的元素上指定屬性。</span><span class="sxs-lookup"><span data-stu-id="d281b-131">Specify the `mapping-schema` attribute on the **\<ROOT>** element (global declaration) in the template.</span></span> <span data-ttu-id="d281b-132">接著，這個對應結構描述會變成沒有明確 `mapping-schema` 註解之所有 XPath 和 Updategram 節點使用的預設結構描述。</span><span class="sxs-lookup"><span data-stu-id="d281b-132">This mapping schema then becomes the default schema that will be used by all XPath and updategram nodes that have no explicit `mapping-schema` annotation.</span></span>  
  
-   <span data-ttu-id="d281b-133">使用 ADO `mapping schema` 物件指定 `Command` 屬性。</span><span class="sxs-lookup"><span data-stu-id="d281b-133">Specify the `mapping schema` attribute by using the ADO `Command` object.</span></span>  
  
 <span data-ttu-id="d281b-134">在 `mapping-schema` 或元素上指定的屬性 **\<xpath-query>** **\<updg:sync>** 具有最高的優先順序; ADO `Command` 物件的優先順序最低。</span><span class="sxs-lookup"><span data-stu-id="d281b-134">The `mapping-schema` attribute that is specified on the **\<xpath-query>** or **\<updg:sync>** element has the highest precedence; the ADO `Command` object has the lowest precedence.</span></span>  
  
 <span data-ttu-id="d281b-135">請注意，如果您在範本中指定 XPath 查詢，且未指定執行 XPath 查詢所依據的對應架構，則會將 XPath 查詢視為**dbobject**類型查詢。</span><span class="sxs-lookup"><span data-stu-id="d281b-135">Note that if you specify an XPath query in a template and do not specify a mapping schema against which the XPath query is executed, the XPath query is treated as a **dbobject** type query.</span></span> <span data-ttu-id="d281b-136">例如，假設有以下的範本：</span><span class="sxs-lookup"><span data-stu-id="d281b-136">For example, consider this template:</span></span>  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql">  
          Production.ProductPhoto[@ProductPhotoID='100']/@LargePhoto  
</sql:xpath-query>  
```  
  
 <span data-ttu-id="d281b-137">此範本會指定一個 XPath 查詢，但不會指定對應結構描述。</span><span class="sxs-lookup"><span data-stu-id="d281b-137">The template specifies an XPath query but it does not specify a mapping schema.</span></span> <span data-ttu-id="d281b-138">因此，此查詢會被視為**dbobject**類型查詢，其中 ProductPhoto 是資料表名稱，而 @ProductPhotoID = ' 100 ' 則是找到識別碼值為100之產品相片的述詞。</span><span class="sxs-lookup"><span data-stu-id="d281b-138">Therefore, this query is treated as a **dbobject** type query in which Production.ProductPhoto is the table name and @ProductPhotoID='100' is a predicate that finds a product photo with the ID value of 100.</span></span> <span data-ttu-id="d281b-139">@LargePhoto這是要從中取得值的資料行。</span><span class="sxs-lookup"><span data-stu-id="d281b-139">@LargePhoto is the column from which to retrieve the value.</span></span>  
  
  
