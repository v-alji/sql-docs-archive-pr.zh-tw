---
title: 使用 sql： use-CDATA 建立 CDATA 區段 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- markup characters [SQLXML]
- special characters [SQLXML]
- use-cdata annotation
- plain text [SQLXML]
- CDATA sections
- escaping blocks of text [SQLXML]
- annotated XSD schemas, CDATA sections
- sql:use-cdata
ms.assetid: 26d2b9dc-f857-44ff-bcd4-aaf64ff809d0
author: rothja
ms.author: jroth
ms.openlocfilehash: c0ba0787efbda400590a75f0f3529e3df8819e41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599436"
---
# <a name="creating-cdata-sections-using-sqluse-cdata-sqlxml-40"></a><span data-ttu-id="a844f-102">使用 sql:use-cdata 建立 CDATA 區段 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="a844f-102">Creating CDATA Sections Using sql:use-cdata (SQLXML 4.0)</span></span>
  <span data-ttu-id="a844f-103">在 XML 中，CDATA 區段可用來逸出包含字元的文字區塊，否則這些字元會被辨識為標記字元。</span><span class="sxs-lookup"><span data-stu-id="a844f-103">In XML, CDATA sections are used to escape blocks of text that contain characters that would otherwise be recognized as markup characters.</span></span>  
  
 <span data-ttu-id="a844f-104">Microsoft 中的資料庫 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 有時可以包含 XML 剖析器視為標記字元的字元; 例如，角括弧 (\< and >) 、小於或等於符號 ( # B0 =) ，而 & ( # A1) 會視為標記字元。</span><span class="sxs-lookup"><span data-stu-id="a844f-104">A database in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can sometimes contain characters that are treated as markup characters by the XML parser; for example, angle brackets (\< and >), the less-than-or-equal-to symbol (<=), and the ampersand (&) are treated as markup characters.</span></span> <span data-ttu-id="a844f-105">但是，您可以將這類型的特殊字元包裝在 CDATA 區段內，以免被視為標記字元。</span><span class="sxs-lookup"><span data-stu-id="a844f-105">However, you can wrap this type of special characters in a CDATA section to prevent them from being treated as markup characters.</span></span> <span data-ttu-id="a844f-106">XML 剖析器會將 CDATA 區段內的文字視為純文字。</span><span class="sxs-lookup"><span data-stu-id="a844f-106">The text within the CDATA section is treated by the XML parser as plain text.</span></span>  
  
 <span data-ttu-id="a844f-107">`sql:use-cdata` 註解是用來指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所傳回的資料應該包裝在 CDATA 區段內 (也就是說，它會指出 `sql:field` 指定之資料行中的值是否應該包含在 CDATA 區段內)。</span><span class="sxs-lookup"><span data-stu-id="a844f-107">The `sql:use-cdata` annotation is used to specify that the data returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should be wrapped in a CDATA section (that is, it indicates whether the value from a column that is specified by `sql:field` should be enclosed in a CDATA section).</span></span> <span data-ttu-id="a844f-108">`sql:use-cdata` 註解只能在對應至資料庫資料行的元素上指定。</span><span class="sxs-lookup"><span data-stu-id="a844f-108">The `sql:use-cdata` annotation can be specified only on elements that map to a database column.</span></span>  
  
 <span data-ttu-id="a844f-109">`sql:use-cdata` 註解接受布林值 (0 = false，1 = true)。</span><span class="sxs-lookup"><span data-stu-id="a844f-109">The `sql:use-cdata` annotation takes a Boolean value (0 = false, 1 = true).</span></span> <span data-ttu-id="a844f-110">可接受的值為 0、1、true 和 false。</span><span class="sxs-lookup"><span data-stu-id="a844f-110">The acceptable values are 0, 1, true, and false.</span></span>  
  
 <span data-ttu-id="a844f-111">此註解不能搭配 `sql:url-encode` 使用或是在 ID、IDREF、IDREFS、NMTOKEN 和 NMTOKENS 屬性類型上使用。</span><span class="sxs-lookup"><span data-stu-id="a844f-111">This annotation cannot be used with `sql:url-encode` or on the ID, IDREF, IDREFS, NMTOKEN, and NMTOKENS attribute types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a844f-112">範例</span><span class="sxs-lookup"><span data-stu-id="a844f-112">Examples</span></span>  
 <span data-ttu-id="a844f-113">若要使用下列範例建立工作範例，您必須符合某些需求。</span><span class="sxs-lookup"><span data-stu-id="a844f-113">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="a844f-114">如需詳細資訊，請參閱[執行 SQLXML 範例的需求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="a844f-114">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-sqluse-cdata-on-an-element"></a><span data-ttu-id="a844f-115">A.</span><span class="sxs-lookup"><span data-stu-id="a844f-115">A.</span></span> <span data-ttu-id="a844f-116">在元素上指定 sql:use-cdata</span><span class="sxs-lookup"><span data-stu-id="a844f-116">Specifying sql:use-cdata on an element</span></span>  
 <span data-ttu-id="a844f-117">在下列架構中， `sql:use-cdata` 會將專案中的設為 1 (True) **\<AddressLine1>** **\<Address>** 。</span><span class="sxs-lookup"><span data-stu-id="a844f-117">In the following schema, `sql:use-cdata` is set to 1 (True) for the **\<AddressLine1>** within the **\<Address>** element.</span></span> <span data-ttu-id="a844f-118">因此，資料會在 CDATA 區段內傳回。</span><span class="sxs-lookup"><span data-stu-id="a844f-118">As a result, the data is returned in a CDATA section.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Address"   
               sql:relation="Person.Address"   
               sql:key-fields="AddressID" >  
   <xsd:complexType>  
        <xsd:sequence>  
          <xsd:element name="AddressID"  type="xsd:string" />  
          <xsd:element name="AddressLine1" type="xsd:string"   
                       sql:use-cdata="1" />  
        </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="a844f-119">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="a844f-119">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="a844f-120">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="a844f-120">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="a844f-121">將檔案儲存為 UseCData.xml。</span><span class="sxs-lookup"><span data-stu-id="a844f-121">Save the file as UseCData.xml.</span></span>  
  
2.  <span data-ttu-id="a844f-122">複製下列範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="a844f-122">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="a844f-123">將檔案儲存為 UseCDataT.xml 並放在與 UseCData.xml 相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="a844f-123">Save the file as UseCDataT.xml in the same directory where you saved UseCData.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="UseCData.xml">  
            /Address[AddressID < 11]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="a844f-124">針對對應結構描述 (UseCData.xml) 指定的目錄路徑，相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="a844f-124">The directory path specified for the mapping schema (UseCData.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="a844f-125">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="a844f-125">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\UseCData.xml"  
    ```  
  
3.  <span data-ttu-id="a844f-126">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="a844f-126">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="a844f-127">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="a844f-127">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="a844f-128">這是部分結果集：</span><span class="sxs-lookup"><span data-stu-id="a844f-128">This is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Address>   
    <AddressID>1</CustomerID>   
    <AddressLine1>   
      <![CDATA[ 1970 Napa Ct.  ]]>   
    </AddressLine1>   
  </Address>  
  <Address>  
    <AddressLine1>   
      <![CDATA[ 9833 Mt. Dias Blv. ]]>   
    </AddressLine1>   
  </Address>  
  ...  
</ROOT>  
```  
  
  
