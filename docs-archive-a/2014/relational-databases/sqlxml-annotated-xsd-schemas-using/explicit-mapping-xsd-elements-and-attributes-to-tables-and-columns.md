---
title: XSD 元素和屬性對資料表和資料行的明確對應 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- explicit schema mapping [SQLXML]
- XPath queries [SQLXML], annotated XSD schemas in queries
- sql:field
- row mapping [SQLXML]
- attribute mapping [SQLXML], explicit mapping
- field annotation
- XSD schemas [SQLXML], mapping attributes and elements
- names [SQLXML]
- relation annotation
- table/view mapping [SQLXML], explicit mapping
- sql:relation
- mapping schema [SQLXML], explicit mapping
- annotated XSD schemas, mapping attributes and elements
- column mapping [SQLXML]
- element mapping [SQLXML], explicit mapping
- table mapping [SQLXML], explicit mapping
- element/attribute mapping [SQLXML]
ms.assetid: 7a5ebeb6-7322-4141-a307-ebcf95976146
author: rothja
ms.author: jroth
ms.openlocfilehash: f3400682b5f28835ca039912aab058691929a6c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592554"
---
# <a name="explicit-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-40"></a><span data-ttu-id="247cb-102">XSD 元素和屬性對資料表和資料行的明確對應 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="247cb-102">Explicit Mapping of XSD Elements and Attributes to Tables and Columns (SQLXML 4.0)</span></span>
  <span data-ttu-id="247cb-103">使用 XSD 結構描述提供關聯式資料庫的 XML 檢視表時，必須將結構描述的元素但屬性對應到資料庫的資料表和資料行。</span><span class="sxs-lookup"><span data-stu-id="247cb-103">When using an XSD schema to provide an XML view of the relational database , the elements and attributes of the schema must be mapped to tables and columns of the database.</span></span> <span data-ttu-id="247cb-104">資料庫資料表/檢視表中的資料列將會對應到 XML 文件中的元素。</span><span class="sxs-lookup"><span data-stu-id="247cb-104">The rows in the database table/view will map to elements in the XML document.</span></span> <span data-ttu-id="247cb-105">資料庫中的資料行值會對應到屬性或元素。</span><span class="sxs-lookup"><span data-stu-id="247cb-105">The column values in the database map to attributes or elements.</span></span>  
  
 <span data-ttu-id="247cb-106">針對註解式 XSD 結構描述指定 XPath 查詢時，結構描述中元素和屬性的資料會從所對應的資料表和資料行對應。</span><span class="sxs-lookup"><span data-stu-id="247cb-106">When XPath queries are specified against the annotated XSD schema, the data for the elements and attributes in the schema is retrieved from the tables and columns to which they map.</span></span> <span data-ttu-id="247cb-107">若要從資料庫取得單一值，在 XSD 結構描述中指定的對應必須同時擁有關聯和欄位規格。</span><span class="sxs-lookup"><span data-stu-id="247cb-107">To obtain a single value from the database, the mapping specified in the XSD schema must have both relation and field specification.</span></span> <span data-ttu-id="247cb-108">如果元素/屬性的名稱與資料表/檢視表或所對應的資料行名稱不同，則會將 `sql:relation` 和 `sql:field` 屬性用於指定 XML 文件中之元素或屬性和資料庫中之資料表 (檢視表) 或資料行之間的對應。</span><span class="sxs-lookup"><span data-stu-id="247cb-108">If the name of an element/attribute is not the same name as the table/view or column name to which it maps, the `sql:relation` and `sql:field` annotations are used to specify the mapping between an element or attribute in an XML document and the table (view) or column in a database.</span></span>  
  
## <a name="sql-relation"></a><span data-ttu-id="247cb-109">sql-relation</span><span class="sxs-lookup"><span data-stu-id="247cb-109">sql-relation</span></span>  
 <span data-ttu-id="247cb-110">加入 `sql:relation` 註解，將 XSD 結構描述中的 XML 節點對應至資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="247cb-110">The `sql:relation` annotation is added to map an XML node in the XSD schema to a database table.</span></span> <span data-ttu-id="247cb-111">資料表 (檢視表) 的名稱會指定為 `sql:relation` 註解的值。</span><span class="sxs-lookup"><span data-stu-id="247cb-111">The name of a table (view) is specified as the value of the `sql:relation` annotation.</span></span>  
  
 <span data-ttu-id="247cb-112">在元素上指定 `sql:relation` 時，此註解的範圍會套用到該元素之複雜類型定義中描述的所有屬性和子元素中，因此可在撰寫註解時提供捷徑。</span><span class="sxs-lookup"><span data-stu-id="247cb-112">When `sql:relation` is specified on an element, the scope of this annotation applies to all attributes and child elements that are described in the complex type definition of that element, therefore providing a shortcut in writing annotations.</span></span>  
  
 <span data-ttu-id="247cb-113">`sql:relation`當中有效的識別碼 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 在 XML 中無效時，批註也很有用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="247cb-113">The `sql:relation` annotation is also useful when identifiers that are valid in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are not valid in XML.</span></span> <span data-ttu-id="247cb-114">例如，"Order Details" 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中是有效的資料表名稱，但是在 XML 中是無效的。</span><span class="sxs-lookup"><span data-stu-id="247cb-114">For example, "Order Details" is a valid table name in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] but not in XML.</span></span> <span data-ttu-id="247cb-115">在這種情況下，可以使用 `sql:relation` 註解來指定對應，例如：</span><span class="sxs-lookup"><span data-stu-id="247cb-115">In such cases, the `sql:relation` annotation can be used to specify the mapping, for example:</span></span>  
  
```  
<xsd:element name="OD" sql:relation="[Order Details]">  
```  
  
## <a name="sql-field"></a><span data-ttu-id="247cb-116">sql-field</span><span class="sxs-lookup"><span data-stu-id="247cb-116">sql-field</span></span>  
 <span data-ttu-id="247cb-117">`sql-field` 註解會將元素或屬性對應到資料庫資料行。</span><span class="sxs-lookup"><span data-stu-id="247cb-117">The `sql-field` annotation maps an element or attribute to a database column.</span></span> <span data-ttu-id="247cb-118">加入 `sql:field` 註解，將結構描述中的 XML 節點對應至資料庫資料行。</span><span class="sxs-lookup"><span data-stu-id="247cb-118">The `sql:field` annotation is added to map an XML node in the schema to a database column.</span></span> <span data-ttu-id="247cb-119">您無法在空內容元素上指定 `sql:field`。</span><span class="sxs-lookup"><span data-stu-id="247cb-119">You cannot specify `sql:field` on an empty content element.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="247cb-120">範例</span><span class="sxs-lookup"><span data-stu-id="247cb-120">Examples</span></span>  
 <span data-ttu-id="247cb-121">若要使用下列範例建立工作範例，您必須符合某些需求。</span><span class="sxs-lookup"><span data-stu-id="247cb-121">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="247cb-122">如需詳細資訊，請參閱[執行 SQLXML 範例的需求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="247cb-122">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-the-sqlrelation-and-sqlfield-annotations"></a><span data-ttu-id="247cb-123">A.</span><span class="sxs-lookup"><span data-stu-id="247cb-123">A.</span></span> <span data-ttu-id="247cb-124">指定 sql:relation 和 sql:field 註解</span><span class="sxs-lookup"><span data-stu-id="247cb-124">Specifying the sql:relation and sql:field annotations</span></span>  
 <span data-ttu-id="247cb-125">在此範例中，XSD 架構是由複雜類型的元素所組成， **\<Contact>** 其中包含 **\<FName>** 和子專案 **\<LName>** ，以及**ContactID**屬性。</span><span class="sxs-lookup"><span data-stu-id="247cb-125">In this example, the XSD schema consists of an **\<Contact>** element of complex type with **\<FName>** and **\<LName>** child elements and the **ContactID** attribute.</span></span>  
  
 <span data-ttu-id="247cb-126">批註會將 `sql:relation` **\<Contact>** 元素對應至 AdventureWorks 資料庫中的 Person. Contact 資料表。</span><span class="sxs-lookup"><span data-stu-id="247cb-126">The `sql:relation` annotation maps the **\<Contact>** element to the Person.Contact table in the AdventureWorks database.</span></span> <span data-ttu-id="247cb-127">批註會將 `sql:field` **\<FName>** 元素對應至 FirstName 資料行，並將 **\<LName>** 元素對應至 LastName 資料行。</span><span class="sxs-lookup"><span data-stu-id="247cb-127">The `sql:field` annotation maps the **\<FName>** element to the FirstName column and the **\<LName>** element to the LastName column.</span></span>  
  
 <span data-ttu-id="247cb-128">未指定**ContactID**屬性的注釋。</span><span class="sxs-lookup"><span data-stu-id="247cb-128">No annotation is specified for the **ContactID** attribute.</span></span> <span data-ttu-id="247cb-129">這會導致將屬性預設對應到具有相同名稱的資料行。</span><span class="sxs-lookup"><span data-stu-id="247cb-129">This results in a default mapping of the attribute to the column with the same name.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Contact" sql:relation="Person.Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"  
                     sql:field="FirstName"   
                     type="xsd:string" />   
        <xsd:element name="LName"    
                     sql:field="LastName"    
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="247cb-130">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="247cb-130">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="247cb-131">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="247cb-131">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="247cb-132">將檔案儲存為 MySchema-annotated.xml。</span><span class="sxs-lookup"><span data-stu-id="247cb-132">Save the file as MySchema-annotated.xml.</span></span>  
  
2.  <span data-ttu-id="247cb-133">複製下列範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="247cb-133">Copy the following template below and paste it into a text file.</span></span> <span data-ttu-id="247cb-134">將檔案儲存為 MySchema-annotatedT.xml 並放在與儲存 MySchema-annotated.xml 相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="247cb-134">Save the file as MySchema-annotatedT.xml in the same directory where you saved MySchema-annotated.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="MySchema-annotated.xml">  
        /Contact  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="247cb-135">針對對應結構描述 (MySchema-annotated.xml) 指定的目錄路徑，與儲存範本之目錄相關。</span><span class="sxs-lookup"><span data-stu-id="247cb-135">The directory path specified for the mapping schema (MySchema-annotated.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="247cb-136">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="247cb-136">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchema-annotated.xml"  
    ```  
  
3.  <span data-ttu-id="247cb-137">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="247cb-137">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="247cb-138">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="247cb-138">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="247cb-139">部分結果集如下：</span><span class="sxs-lookup"><span data-stu-id="247cb-139">Here is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
 <Contact ContactID="1">   
    <FName>Gustavo</FName>   
    <LName>Achong</LName>   
 </Contact>   
  .....  
</ROOT>  
```  
  
  
