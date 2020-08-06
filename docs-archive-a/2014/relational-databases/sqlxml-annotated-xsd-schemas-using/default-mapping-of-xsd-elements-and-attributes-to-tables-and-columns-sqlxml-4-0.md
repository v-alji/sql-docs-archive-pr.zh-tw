---
title: XSD 元素和屬性對資料表和資料行的預設對應 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XSD schemas [SQLXML], mapping attributes and elements
- mapping schema [SQLXML], default mapping
- element mapping [SQLXML], default mapping
- element mapping [SQLXML]
- table mapping [SQLXML]
- annotated XSD schemas, mapping attributes and elements
- table/view mapping [SQLXML]
- column mapping [SQLXML]
- attribute mapping [SQLXML], default mapping
- default schema mapping
- table mapping [SQLXML], default mapping
- testing XPath query against schema
- xml data type [SQL Server], SQLXML
- table/view mapping [SQLXML], default mapping
- element/attribute mapping [SQLXML]
ms.assetid: 9a18e92a-6cfb-4a14-993a-663a95aabb63
author: rothja
ms.author: jroth
ms.openlocfilehash: 0bccec2413e8a0a6e13283a0f3e5f63ab61e934b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595902"
---
# <a name="default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-40"></a><span data-ttu-id="810b9-102">XSD 元素和屬性對資料表和資料行的預設對應 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="810b9-102">Default Mapping of XSD Elements and Attributes to Tables and Columns (SQLXML 4.0)</span></span>
  <span data-ttu-id="810b9-103">根據預設，XSD 註解式結構描述中的複雜類型元素會對應到指定之資料庫中具有相同名稱的資料表 (檢視表)，而簡單類型的元素或屬性會對應到資料表中具有相同名稱的資料行。</span><span class="sxs-lookup"><span data-stu-id="810b9-103">By default, an element of complex type in an XSD annotated schema maps to the table (view) with the same name in the specified database, and an element or attribute of simple type maps to the column with the same name in the table.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="810b9-104">範例</span><span class="sxs-lookup"><span data-stu-id="810b9-104">Examples</span></span>  
 <span data-ttu-id="810b9-105">若要使用下列範例建立工作範例，您必須符合某些需求。</span><span class="sxs-lookup"><span data-stu-id="810b9-105">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="810b9-106">如需詳細資訊，請參閱[執行 SQLXML 範例的需求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="810b9-106">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-default-mapping"></a><span data-ttu-id="810b9-107">A.</span><span class="sxs-lookup"><span data-stu-id="810b9-107">A.</span></span> <span data-ttu-id="810b9-108">指定預設對應</span><span class="sxs-lookup"><span data-stu-id="810b9-108">Specifying default mapping</span></span>  
 <span data-ttu-id="810b9-109">在這個範例的 XDR 結構描述中不會指定任何註解。</span><span class="sxs-lookup"><span data-stu-id="810b9-109">In this example, no annotations are specified in the XSD schema.</span></span> <span data-ttu-id="810b9-110">**\<Person.Contact>** 元素屬於複雜類型，因此預設會對應到 AdventureWorks 資料庫中的 Person 資料表。</span><span class="sxs-lookup"><span data-stu-id="810b9-110">The **\<Person.Contact>** element is of complex type and, therefore, maps by default to the Person.Contact table in the AdventureWorks database.</span></span> <span data-ttu-id="810b9-111">元素的所有屬性 (ContactID、FirstName、LastName) **\<Person.Contact>** 都是簡單的類型，而且預設會對應至 Person 資料表中具有相同名稱的資料行。</span><span class="sxs-lookup"><span data-stu-id="810b9-111">All the attributes (ContactID, FirstName, LastName) of the **\<Person.Contact>** element are of simple type and map by default to columns with the same names in the Person.Contact table.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID"  type="xsd:string" />   
       <xsd:attribute name="FirstName"   type="xsd:string" />   
       <xsd:attribute name="LastName"    type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="810b9-112">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="810b9-112">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="810b9-113">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="810b9-113">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="810b9-114">將檔案儲存為 MySchema.xml。</span><span class="sxs-lookup"><span data-stu-id="810b9-114">Save the file as MySchema.xml.</span></span>  
  
2.  <span data-ttu-id="810b9-115">複製下列範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="810b9-115">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="810b9-116">將檔案儲存為 MySchemaT.xml，並放在與儲存 MySchema.xml 相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="810b9-116">Save the file as MySchemaT.xml in the same directory where you saved MySchema.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="MySchema.xml">  
            /Person.Contact  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="810b9-117">針對對應結構描述 (MySchema.xml) 指定的目錄路徑，相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="810b9-117">The directory path specified for the mapping schema (MySchema.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="810b9-118">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="810b9-118">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchema.xml"  
    ```  
  
3.  <span data-ttu-id="810b9-119">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="810b9-119">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="810b9-120">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="810b9-120">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="810b9-121">部分結果集如下：</span><span class="sxs-lookup"><span data-stu-id="810b9-121">Here is the partial result set:</span></span>  
  
```  
<?xml version="1.0" encoding="UTF-8" ?>  
<ROOT>  
  <Person.Contact ContactID="1" FirstName="Gustavo" LastName="Achong"/>  
  <Person.Contact ContactID="2" FirstName="Catherine" LastName="Abel"/>  
   ...  
</ROOT>  
```  
  
### <a name="b-mapping-an-xml-element-to-a-database-column"></a><span data-ttu-id="810b9-122">B.</span><span class="sxs-lookup"><span data-stu-id="810b9-122">B.</span></span> <span data-ttu-id="810b9-123">將 XML 元素對應至資料庫資料行</span><span class="sxs-lookup"><span data-stu-id="810b9-123">Mapping an XML element to a database column</span></span>  
 <span data-ttu-id="810b9-124">在此範例中，因為沒有使用註解，因此也會發生預設對應。</span><span class="sxs-lookup"><span data-stu-id="810b9-124">In this example, default mapping also takes place because no annotations are used.</span></span> <span data-ttu-id="810b9-125">**\<Person.Contact>** 元素屬於複雜型別，而且會對應至資料庫中具有相同名稱的資料表。</span><span class="sxs-lookup"><span data-stu-id="810b9-125">The **\<Person.Contact>** element is of complex type and maps to the table with the same name in the database.</span></span> <span data-ttu-id="810b9-126">元素 **\<FirstName>** 和的 [專案名稱] **\<LastName>** 屬性屬於簡單類型，因此會對應到具有相同名稱的資料行。 **EmployeeID**</span><span class="sxs-lookup"><span data-stu-id="810b9-126">The elements **\<FirstName>** and **\<LastName>** and the **EmployeeID** attribute are of simple type and, therefore, map to the columns with the same names.</span></span> <span data-ttu-id="810b9-127">此範例與先前範例唯一的差別在於，這些元素用於對應 FirstName 和 LastName 欄位。</span><span class="sxs-lookup"><span data-stu-id="810b9-127">The only difference between this and the previous example are that elements are used for mapping the FirstName and LastName fields.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact">  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="FirstName" type="xsd:string" />   
        <xsd:element name="LastName" type="xsd:string" />   
      </xsd:sequence>  
      <xsd:attribute name="ContactID" type="xsd:integer" />   
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="810b9-128">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="810b9-128">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="810b9-129">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="810b9-129">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="810b9-130">然後將檔案儲存為 MySchemaElements.xml。</span><span class="sxs-lookup"><span data-stu-id="810b9-130">Save the file as MySchemaElements.xml.</span></span>  
  
2.  <span data-ttu-id="810b9-131">建立下列範本 (MySchemaElementsT.xml)，並將其儲存在先前步驟中所使用的相同目錄中。</span><span class="sxs-lookup"><span data-stu-id="810b9-131">Create the following template (MySchemaElementsT.xml), and save it in the same directory used in the previous step.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="MySchemaElements.xml">  
            /Person.Contact  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="810b9-132">針對對應結構描述指定的目錄路徑是儲存範本之目錄的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="810b9-132">The directory path specified for the mapping schema is relative to the directory where the template is saved.</span></span> <span data-ttu-id="810b9-133">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="810b9-133">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchemaElements.xml"  
    ```  
  
3.  <span data-ttu-id="810b9-134">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="810b9-134">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="810b9-135">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="810b9-135">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="810b9-136">部分結果集如下：</span><span class="sxs-lookup"><span data-stu-id="810b9-136">Here is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact ContactID="1">  
    <FirstName>Gustavo</FirstName>  
    <LastName>Achong</LastName>  
  </Person.Contact>  
   ...  
</ROOT>  
```  
  
### <a name="c-mapping-an-xml-element-to-an-xml-data-type-column"></a><span data-ttu-id="810b9-137">C.</span><span class="sxs-lookup"><span data-stu-id="810b9-137">C.</span></span> <span data-ttu-id="810b9-138">將 XML 元素對應至 XML 資料類型資料行</span><span class="sxs-lookup"><span data-stu-id="810b9-138">Mapping an XML element to an XML data type column</span></span>  
 <span data-ttu-id="810b9-139">在此範例中，因為沒有使用註解，因此也會發生預設對應。</span><span class="sxs-lookup"><span data-stu-id="810b9-139">In this example, default mapping also takes place because no annotations are used.</span></span> <span data-ttu-id="810b9-140">**\<Production.ProductModel>** 元素屬於複雜型別，而且會對應至資料庫中具有相同名稱的資料表。</span><span class="sxs-lookup"><span data-stu-id="810b9-140">The **\<Production.ProductModel>** element is of complex type and maps to the table with the same name in the database.</span></span> <span data-ttu-id="810b9-141">**ProductModelID**屬性屬於簡單類型，因此會對應到具有相同名稱的資料行。</span><span class="sxs-lookup"><span data-stu-id="810b9-141">The **ProductModelID** attribute is of simple type and, therefore, map to the columns with the same names.</span></span> <span data-ttu-id="810b9-142">這個專案與先前的範例唯一的差別在於，專案 **\<Instructions>** 會對應至使用該類型的資料行 `xml` `xsd:anyType` 。</span><span class="sxs-lookup"><span data-stu-id="810b9-142">The only difference between this and the previous examples is that the **\<Instructions>** element is mapping to a column that uses the `xml` data type by using the `xsd:anyType` type.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Production.ProductModel">  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Instructions" type="xsd:anyType" />   
      </xsd:sequence>  
      <xsd:attribute name="ProductModelID" type="xsd:integer" />   
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="810b9-143">`xml` 資料類型是在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中導入。</span><span class="sxs-lookup"><span data-stu-id="810b9-143">The `xml` data type was introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="810b9-144">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="810b9-144">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="810b9-145">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="810b9-145">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="810b9-146">將檔案儲存為 MySchemaXmlAnyElements.xml。</span><span class="sxs-lookup"><span data-stu-id="810b9-146">Save the file as MySchemaXmlAnyElements.xml.</span></span>  
  
2.  <span data-ttu-id="810b9-147">建立下列範本 (MySchemaXmlAnyElementsT.xml)，並將其儲存在先前步驟中所使用的相同目錄中。</span><span class="sxs-lookup"><span data-stu-id="810b9-147">Create the following template (MySchemaXmlAnyElementsT.xml), and save it in the same directory used in the previous step.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="MySchemaXmlAnyElements.xml">  
            /Production.ProductModel[@ProductModelID=7]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="810b9-148">針對對應結構描述指定的目錄路徑是儲存範本之目錄的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="810b9-148">The directory path specified for the mapping schema is relative to the directory where the template is saved.</span></span> <span data-ttu-id="810b9-149">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="810b9-149">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchemaXmlAnyElements.xml"  
    ```  
  
3.  <span data-ttu-id="810b9-150">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="810b9-150">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="810b9-151">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="810b9-151">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="810b9-152">部分結果集如下：</span><span class="sxs-lookup"><span data-stu-id="810b9-152">Here is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductModel ProductModelID="7">  
    <Instructions>  
      <root xmlns="http:  
//schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstru  
ctions">  
...  
      </root>  
    <Instructions>  
  </Production.ProductModel>  
</ROOT>  
```  
  
## <a name="see-also"></a><span data-ttu-id="810b9-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="810b9-153">See Also</span></span>  
 <span data-ttu-id="810b9-154">[&#40;SQLXML 4.0&#41;的批註式架構安全性考慮](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="810b9-154">[Annotated Schema Security Considerations &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="810b9-155">[XML 資料 &#40;SQL Server&#41;](../xml/xml-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="810b9-155">[XML Data &#40;SQL Server&#41;](../xml/xml-data-sql-server.md) </span></span>  
 [<span data-ttu-id="810b9-156">xml 資料類型在 SQLXML 4.0 中的支援</span><span class="sxs-lookup"><span data-stu-id="810b9-156">xml Data Type Support in SQLXML 4.0</span></span>](../sqlxml/xml-data-type-support-in-sqlxml-4-0.md)  
  
  
