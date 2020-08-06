---
title: 使用 sql：溢位欄位 (SQLXML 4.0) 來抓取未消耗的資料 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- unconsumed data
- storing unconsumed data
- retrieving unconsumed data
- annotated XSD schemas, unconsumed data
- overflow data [SQLXML]
- sql:overflow-field
ms.assetid: 8526998d-b47d-4a32-8dc2-7f50a8d11097
author: rothja
ms.author: jroth
ms.openlocfilehash: 796fda9428954c5f18c5d37b353de9fd4122551e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599427"
---
# <a name="retrieving-unconsumed-data-using-the-sqloverflow-field-sqlxml-40"></a><span data-ttu-id="8e7e6-102">使用 sql:overflow-field 擷取未耗用的資料 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="8e7e6-102">Retrieving Unconsumed Data Using the sql:overflow-field (SQLXML 4.0)</span></span>
  <span data-ttu-id="8e7e6-103">當記錄使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] OPENXML 函數，從 XML 文件的資料庫中插入，可以將來源 XML 文件中所有未耗用的資料儲存在資料行中。</span><span class="sxs-lookup"><span data-stu-id="8e7e6-103">When records are inserted in a database from an XML document by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] OPENXML function, all the unconsumed data from the source XML document can be stored in a column.</span></span> <span data-ttu-id="8e7e6-104">當您使用註解式結構描述擷取資料庫中的資料時，您可以指定 `sql:overflow-field` 屬性來識別儲存溢位資料之資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="8e7e6-104">When you retrieve data from a database by using annotated schemas, you can specify the `sql:overflow-field` attribute to identify the column in the table in which the overflow data is stored.</span></span> <span data-ttu-id="8e7e6-105">`sql:overflow-field`可以在上指定屬性 **\<element>** 。</span><span class="sxs-lookup"><span data-stu-id="8e7e6-105">The `sql:overflow-field` attribute can be specified on **\<element>**.</span></span>  
  
 <span data-ttu-id="8e7e6-106">然後以下列方式擷取此資料：</span><span class="sxs-lookup"><span data-stu-id="8e7e6-106">This data is then retrieved in these ways:</span></span>  
  
-   <span data-ttu-id="8e7e6-107">儲存在溢位資料行中的屬性會加入到包含 `sql:overflow-field` 註解的元素中。</span><span class="sxs-lookup"><span data-stu-id="8e7e6-107">Attributes stored in the overflow column are added to the element that contains the `sql:overflow-field` annotation.</span></span>  
  
-   <span data-ttu-id="8e7e6-108">儲存在資料庫之溢位資料行中的子元素及其下階會當做在結構描述中明確指定之內容之後的子元素加入 </span><span class="sxs-lookup"><span data-stu-id="8e7e6-108">The child elements and their descendents, stored in the overflow column in the database, are added as child elements following the content that is explicitly specified in the schema.</span></span> <span data-ttu-id="8e7e6-109">(不會保留任何順序)。</span><span class="sxs-lookup"><span data-stu-id="8e7e6-109">(No order is preserved.)</span></span>  
  
## <a name="examples"></a><span data-ttu-id="8e7e6-110">範例</span><span class="sxs-lookup"><span data-stu-id="8e7e6-110">Examples</span></span>  
 <span data-ttu-id="8e7e6-111">若要使用下列範例建立工作範例，您必須符合某些需求。</span><span class="sxs-lookup"><span data-stu-id="8e7e6-111">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="8e7e6-112">如需詳細資訊，請參閱[執行 SQLXML 範例的需求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="8e7e6-112">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-sqloverflow-field-for-an-element"></a><span data-ttu-id="8e7e6-113">A.</span><span class="sxs-lookup"><span data-stu-id="8e7e6-113">A.</span></span> <span data-ttu-id="8e7e6-114">針對元素指定 sql:overflow-field</span><span class="sxs-lookup"><span data-stu-id="8e7e6-114">Specifying sql:overflow-field for an element</span></span>  
 <span data-ttu-id="8e7e6-115">此範例假設已經執行下列指令碼，因此名為 Customers2 的資料表存在於 tempdb 資料庫中：</span><span class="sxs-lookup"><span data-stu-id="8e7e6-115">This example assumes that the following script has been run so that a table named Customers2 exists in the tempdb database:</span></span>  
  
```  
USE tempdb  
CREATE TABLE Customers2 (  
CustomerID       VARCHAR(10),   
ContactName    VARCHAR(30),   
AddressOverflow    NVARCHAR(500))  
  
GO  
INSERT INTO Customers2 VALUES (  
'ALFKI',   
'Joe',  
'<Address>  
  <Address1>Maple St.</Address1>  
  <Address2>Apt. E105</Address2>  
  <City>Seattle</City>  
  <State>WA</State>  
  <Zip>98147</Zip>  
 </Address>')  
GO  
```  
  
 <span data-ttu-id="8e7e6-116">此外，您必須建立 tempdb 資料庫的虛擬目錄，以及 `template` 名為 "template" 之類型的範本虛擬名稱。</span><span class="sxs-lookup"><span data-stu-id="8e7e6-116">In addition, you must create a virtual directory for the tempdb database-and a template virtual name of `template` type named "template".</span></span>  
  
 <span data-ttu-id="8e7e6-117">在下列範例中，對應結構描述會擷取儲存在 Customers2 資料表之 AddressOverflow 資料行中的未耗用資料：</span><span class="sxs-lookup"><span data-stu-id="8e7e6-117">In the following example, the mapping schema retrieves the unconsumed data that is stored in the AddressOverflow column of the Customers2 table:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Customers2" sql:overflow-field="AddressOverflow" >  
    <xsd:complexType>  
      <xsd:attribute name="CustomerID"  type="xsd:integer"/>  
      <xsd:attribute name="ContactName"  type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="8e7e6-118">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="8e7e6-118">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="8e7e6-119">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="8e7e6-119">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="8e7e6-120">將檔案儲存為 Overflow.xml。</span><span class="sxs-lookup"><span data-stu-id="8e7e6-120">Save the file as Overflow.xml.</span></span>  
  
2.  <span data-ttu-id="8e7e6-121">複製下列範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="8e7e6-121">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="8e7e6-122">將檔案儲存為 OverflowT.xml 並放在與儲存 Overflow.xml 相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="8e7e6-122">Save the file as OverflowT.xml in the same directory where you saved Overflow.xml.</span></span> <span data-ttu-id="8e7e6-123">範本中的查詢會選取 Customers2 資料表中的記錄。</span><span class="sxs-lookup"><span data-stu-id="8e7e6-123">The query in the template selects the records in the Customers2 table.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="Overflow.xml">  
            /Customers2  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="8e7e6-124">針對對應結構描述 (Overflow.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="8e7e6-124">The directory path specified for the mapping schema (Overflow.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="8e7e6-125">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="8e7e6-125">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\Overflow.xml"  
    ```  
  
3.  <span data-ttu-id="8e7e6-126">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="8e7e6-126">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="8e7e6-127">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="8e7e6-127">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="8e7e6-128">以下為結果集：</span><span class="sxs-lookup"><span data-stu-id="8e7e6-128">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customers2 CustomerID="ALFKI" ContactName="Joe">  
    <Address1>Maple St.</Address1>   
    <Address2>Apt. E105</Address2>   
    <City>Seattle</City>   
    <State>WA</State>   
    <Zip>98147</Zip>   
  </Customers2>  
</ROOT>  
```  
  
  
