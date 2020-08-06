---
title: 使用 sql：對應 (SQLXML 4.0) ，從產生的 XML 檔排除架構元素 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- element does not map [SQLXML]
- annotated XSD schemas, excluding schema elements
- mapped annotation
- table mapping [SQLXML], excluding schema elements
- sql:mapped
- excluding schema elements
- element mapping [SQLXML], excluding schema elements
- column mapping [SQLXML]
- XSD schemas [SQLXML], excluding schema elements
- attribute mapping [SQLXML], excluding schema elements
- table/view mapping [SQLXML], excluding schema elements
ms.assetid: 7d2649dd-0038-4a2c-b16d-f80f7c306966
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c79ae005b9630fcbfcd16bfc22c2aeb21b7bf9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595903"
---
# <a name="excluding-schema-elements-from-the-resulting-xml-document-using-sqlmapped-sqlxml-40"></a><span data-ttu-id="13735-102">使用 sql:mapped 從產生的 XML 文件排除結構描述元素 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="13735-102">Excluding Schema Elements from the Resulting XML Document Using sql:mapped (SQLXML 4.0)</span></span>
  <span data-ttu-id="13735-103">XSD 結構描述中的每個元素和屬性都會因為預設對應，而對應到資料庫資料表/檢視表和資料行。</span><span class="sxs-lookup"><span data-stu-id="13735-103">Every element and attribute in the XSD schema maps to a database table/view and column because of the default mapping.</span></span> <span data-ttu-id="13735-104">如果您要在 XSD 結構中建立沒有對應到任何資料庫資料表 (檢視表) 或資料行，而且沒有出現在 XML 中的元素，您可以指定 `sql:mapped` 註解。</span><span class="sxs-lookup"><span data-stu-id="13735-104">If you want to create an element in the XSD schema that does not map to any database table (view) or column and that does not appear in the XML, you can specify the `sql:mapped` annotation.</span></span>  
  
 <span data-ttu-id="13735-105">如果無法修改結構描述，或者如果結構描述用於驗證來自其他來源的 XML，而且不包含未儲存在資料庫中的資料，則 `sql:mapped` 註解特別實用。</span><span class="sxs-lookup"><span data-stu-id="13735-105">The `sql:mapped` annotation is especially useful if the schema cannot be modified or if the schema is used to validate XML from other sources and yet contains data that is not stored in your database.</span></span> <span data-ttu-id="13735-106">`sql:mapped` 註解與 `sql:is-constant` 不同之處在於，未對應的元素和屬性不會出現在 XML 文件中。</span><span class="sxs-lookup"><span data-stu-id="13735-106">The `sql:mapped` annotation differs from `sql:is-constant` in that the unmapped elements and attributes do not appear in the XML document.</span></span>  
  
 <span data-ttu-id="13735-107">`sql:mapped` 註解接受布林值 (0 = false，1 = true)。</span><span class="sxs-lookup"><span data-stu-id="13735-107">The `sql:mapped` annotation takes a Boolean value (0 = false, 1 = true).</span></span> <span data-ttu-id="13735-108">可接受的值為 0、1、true 和 false。</span><span class="sxs-lookup"><span data-stu-id="13735-108">The acceptable values are 0, 1, true, and false.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="13735-109">範例</span><span class="sxs-lookup"><span data-stu-id="13735-109">Examples</span></span>  
 <span data-ttu-id="13735-110">若要使用下列範例建立工作範例，您必須符合某些需求。</span><span class="sxs-lookup"><span data-stu-id="13735-110">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="13735-111">如需詳細資訊，請參閱[執行 SQLXML 範例的需求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="13735-111">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-the-sqlmapped-annotation"></a><span data-ttu-id="13735-112">A.</span><span class="sxs-lookup"><span data-stu-id="13735-112">A.</span></span> <span data-ttu-id="13735-113">指定 sql:mapped 註解</span><span class="sxs-lookup"><span data-stu-id="13735-113">Specifying the sql:mapped annotation</span></span>  
 <span data-ttu-id="13735-114">假設您有來自其他來源的 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="13735-114">Assume you have an XSD schema from some other source.</span></span> <span data-ttu-id="13735-115">這個 XSD 架構是由元素所組成， **\<Person.Contact>** 其中包含**ContactID**、 **FirstName**、 **LastName**和**HomeAddress**屬性。</span><span class="sxs-lookup"><span data-stu-id="13735-115">This XSD schema consists of an **\<Person.Contact>** element with **ContactID**, **FirstName**, **LastName**, and **HomeAddress** attributes.</span></span>  
  
 <span data-ttu-id="13735-116">在將這個 XSD 架構對應到 AdventureWorks 資料庫中的 Person. Contact 資料表 `sql:mapped` 時，會在**HomeAddress**屬性上指定，因為 employees 資料表不會儲存員工的主位址。</span><span class="sxs-lookup"><span data-stu-id="13735-116">In mapping this XSD schema to the Person.Contact table in the AdventureWorks database, `sql:mapped` is specified on the **HomeAddress** attribute because the Employees table does not store the home addresses of employees.</span></span> <span data-ttu-id="13735-117">因此，根據對應結構描述指定 XPath 查詢時，此屬性不會對應到資料庫，而且不會在產生的 XML 文件中傳回。</span><span class="sxs-lookup"><span data-stu-id="13735-117">As a result, this attribute is not mapped to the database and is not returned in the resulting XML document when an XPath query is specified against the mapping schema.</span></span>  
  
 <span data-ttu-id="13735-118">預設的對應發生於其餘的結構描述。</span><span class="sxs-lookup"><span data-stu-id="13735-118">Default mapping takes place for the rest of the schema.</span></span> <span data-ttu-id="13735-119">**\<Person.Contact>** 元素會對應至 person 資料表，而所有屬性會對應至 person 資料表中具有相同名稱的資料行。</span><span class="sxs-lookup"><span data-stu-id="13735-119">The **\<Person.Contact>** element maps to the Person.Contact table, and all the attributes map to the columns with the same name in the Person.Contact table.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact">  
    <xsd:complexType>  
      <xsd:attribute name="ContactID"   type="xsd:string"/>  
      <xsd:attribute name="FirstName"    type="xsd:string" />  
      <xsd:attribute name="LastName"     type="xsd:string" />  
      <xsd:attribute name="HomeAddress" type="xsd:string"   
                     sql:mapped="false" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="13735-120">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="13735-120">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="13735-121">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="13735-121">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="13735-122">將檔案儲存為 sql-mapped.xml。</span><span class="sxs-lookup"><span data-stu-id="13735-122">Save the file as sql-mapped.xml.</span></span>  
  
2.  <span data-ttu-id="13735-123">複製下列範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="13735-123">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="13735-124">將檔案儲存為 sql-mappedT.xml 並放在與儲存 sql-mapped.xml 相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="13735-124">Save the file as sql-mappedT.xml in the same directory where you saved sql-mapped.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sql-mapped.xml">  
            /Person.Contact[@ContactID < 10]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="13735-125">針對對應結構描述 (MySchema.xml) 指定的目錄路徑，相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="13735-125">The directory path specified for the mapping schema (MySchema.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="13735-126">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="13735-126">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\sql-mapped.xml"  
    ```  
  
3.  <span data-ttu-id="13735-127">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="13735-127">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="13735-128">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="13735-128">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="13735-129">結果集如下：</span><span class="sxs-lookup"><span data-stu-id="13735-129">This is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact ContactID="1" FirstName="Gustavo" LastName="Achong" />   
  <Person.Contact ContactID="2" FirstName="Catherine" LastName="Abel" />   
  <Person.Contact ContactID="3" FirstName="Kim" LastName="Abercrombie" />   
  <Person.Contact ContactID="4" FirstName="Humberto" LastName="Acevedo" />   
  <Person.Contact ContactID="5" FirstName="Pilar" LastName="Ackerman" />   
  <Person.Contact ContactID="6" FirstName="Frances" LastName="Adams" />   
  <Person.Contact ContactID="7" FirstName="Margaret" LastName="Smith" />   
  <Person.Contact ContactID="8" FirstName="Carla" LastName="Adams" />   
  <Person.Contact ContactID="9" FirstName="Jay" LastName="Adams" />   
</ROOT>  
```  
  
 <span data-ttu-id="13735-130">請注意，ContactID、FirstName 和 LastName 存在，但是 HomeAddress 不存在，因為對應結構描述為 `sql:mapped` 屬性指定 0。</span><span class="sxs-lookup"><span data-stu-id="13735-130">Note that the ContactID, FirstName, and LastName are present, but HomeAddress is not because the mapping schema specified 0 for the `sql:mapped` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13735-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13735-131">See Also</span></span>  
 [<span data-ttu-id="13735-132">XSD 元素和屬性對資料表和資料行的預設對應 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="13735-132">Default Mapping of XSD Elements and Attributes to Tables and Columns &#40;SQLXML 4.0&#41;</span></span>](default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
  
  
