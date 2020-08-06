---
title: 使用 sql：編碼 (SQLXML 4.0) 來要求 BLOB 資料的 URL 參考 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:encode
- encode annotation
- URL references to BLOB data [SQLXML]
- references to BLOB data [SQLXML]
- annotated XSD schemas, URL references to BLOB data
- requesting URL references to BLOB data
- BLOBs, URL references
- Base 64-encoded format
ms.assetid: 2f8cd93b-c636-462b-8291-167197233ee0
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a9f5edcfab4a9d7307327d97bc2099c78c666c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599428"
---
# <a name="requesting-url-references-to-blob-data-using-sqlencode-sqlxml-40"></a><span data-ttu-id="4d659-102">使用 sql:encode 要求指向 BLOB 資料的 URL 參考 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="4d659-102">Requesting URL References to BLOB Data Using sql:encode (SQLXML 4.0)</span></span>
  <span data-ttu-id="4d659-103">在註解式 XSD 結構描述中，當屬性 (或元素) 對應到 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 BLOB 資料行時，將會以 XML 中的 Base 64 編碼格式傳回資料。</span><span class="sxs-lookup"><span data-stu-id="4d659-103">In an annotated XSD schema, when an attribute (or element) is mapped to a BLOB column in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the data is returned in Base 64-encoded format within XML.</span></span>  
  
 <span data-ttu-id="4d659-104">如果您希望要傳回之資料的參考 (URI) 可以在稍後用來擷取二進位格式的 BLOB 資料，請指定 `sql:encode` 註解。</span><span class="sxs-lookup"><span data-stu-id="4d659-104">If you want a reference to the data (a URI) to be returned that can be used later to retrieve the BLOB data in a binary format, specify the `sql:encode` annotation.</span></span> <span data-ttu-id="4d659-105">您可以在屬性或簡單類型的元素上指定 `sql:encode`。</span><span class="sxs-lookup"><span data-stu-id="4d659-105">You can specify `sql:encode` on an attribute or element of simple type.</span></span>  
  
 <span data-ttu-id="4d659-106">指定 `sql:encode` 註解可指示應該傳回欄位的 URL，而不是欄位的值。</span><span class="sxs-lookup"><span data-stu-id="4d659-106">Specify the `sql:encode` annotation to indicate that a URL to the field should be returned instead of the value of the field.</span></span> <span data-ttu-id="4d659-107">`sql:encode` 會依賴主索引鍵來產生 URL 中的單一選取。</span><span class="sxs-lookup"><span data-stu-id="4d659-107">`sql:encode` depends on the primary key to generate a singleton select in the URL.</span></span> <span data-ttu-id="4d659-108">主索引鍵可以使用 `sql:key-fields` 註解來指定。</span><span class="sxs-lookup"><span data-stu-id="4d659-108">The primary key can be specified using the `sql:key-fields` annotation.</span></span>  
  
 <span data-ttu-id="4d659-109">可以將 "url" 或 "default" 值指派給 `sql:encode` 註解。</span><span class="sxs-lookup"><span data-stu-id="4d659-109">The `sql:encode` annotation can be assigned the "url" or the "default" value.</span></span> <span data-ttu-id="4d659-110">"default" 值會傳回 Base 64 編碼格式的資料。</span><span class="sxs-lookup"><span data-stu-id="4d659-110">A value of "default" returns data in Base 64-encoded format.</span></span>  
  
 <span data-ttu-id="4d659-111">`sql:encode` 註解不能搭配 `sql:use-cdata` 使用或是在 ID、IDREF、IDREFS、NMTOKEN 或 NMTOKENS 屬性類型上使用。</span><span class="sxs-lookup"><span data-stu-id="4d659-111">The `sql:encode` annotation cannot be used with `sql:use-cdata` or on the ID, IDREF, IDREFS, NMTOKEN, or NMTOKENS attribute types.</span></span> <span data-ttu-id="4d659-112">它也不能與 XSD **fixed**屬性一起使用。</span><span class="sxs-lookup"><span data-stu-id="4d659-112">It can also not be used with XSD **fixed** attribute.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d659-113">BLOB 類型的資料行不能當做索引鍵或外部索引鍵的一部分使用。</span><span class="sxs-lookup"><span data-stu-id="4d659-113">BLOB-type columns cannot be used as a part of a key or foreign key.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4d659-114">範例</span><span class="sxs-lookup"><span data-stu-id="4d659-114">Examples</span></span>  
 <span data-ttu-id="4d659-115">若要使用下列範例建立工作範例，您必須符合某些需求。</span><span class="sxs-lookup"><span data-stu-id="4d659-115">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="4d659-116">如需詳細資訊，請參閱[執行 SQLXML 範例的需求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="4d659-116">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-sqlencode-to-obtain-a-url-reference-to-blob-data"></a><span data-ttu-id="4d659-117">A.</span><span class="sxs-lookup"><span data-stu-id="4d659-117">A.</span></span> <span data-ttu-id="4d659-118">指定 sql:encode 來取得指向 BLOB 資料的 URL 參考</span><span class="sxs-lookup"><span data-stu-id="4d659-118">Specifying sql:encode to obtain a URL reference to BLOB data</span></span>  
 <span data-ttu-id="4d659-119">在此範例中，對應架構會 `sql:encode` 在**LargePhoto**屬性上指定，以抓取特定產品相片 (的 URI 參考，而不是以) 的基底64編碼格式來取得二進位資料。</span><span class="sxs-lookup"><span data-stu-id="4d659-119">In this example, the mapping schema specifies `sql:encode` on the **LargePhoto** attribute to retrieve the URI reference to a specific product photo (instead of retrieving the binary data in Base 64-encoded format).</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="ProductPhoto" sql:relation="Production.ProductPhoto"   
               sql:key-fields="ProductPhotoID" >  
   <xsd:complexType>  
      <xsd:attribute name="ProductPhotoID"  type="xsd:int"  />  
     <xsd:attribute name="LargePhoto" type="xsd:string" sql:encode="url" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="4d659-120">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="4d659-120">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="4d659-121">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="4d659-121">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="4d659-122">將檔案儲存為 sqlEncode.xml。</span><span class="sxs-lookup"><span data-stu-id="4d659-122">Save the file as sqlEncode.xml.</span></span>  
  
2.  <span data-ttu-id="4d659-123">複製下列範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="4d659-123">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="4d659-124">將檔案儲存在與 sqlEncode.xml 相同的目錄中，並儲存為 sqlEncodeT.xml。</span><span class="sxs-lookup"><span data-stu-id="4d659-124">Save the file as sqlEncodeT.xml in the same directory where you saved sqlEncode.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sqlEncode.xml">  
            /ProductPhoto[@ProductPhotoID=100]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="4d659-125">針對對應結構描述 (sqlEncode.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="4d659-125">The directory path specified for the mapping schema (sqlEncode.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="4d659-126">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="4d659-126">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\sqlEncode.xml"  
    ```  
  
3.  <span data-ttu-id="4d659-127">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="4d659-127">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="4d659-128">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="4d659-128">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="4d659-129">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="4d659-129">This is the result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <ProductPhoto ProductPhotoID="100"  
                 LargePhoto="dbobject/Production.ProductPhoto[@ProductPhotoID="100"]/@LargePhoto" />   
</ROOT>  
```  
  
  
