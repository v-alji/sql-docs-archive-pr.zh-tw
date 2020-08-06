---
title: 資料類型強制型轉和 sql： datatype 注釋 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping data types [SQLXML]
- type attribute
- sql:datatype
- data types [SQLXML], converting
- annotated XSD schemas, mapping data types
- xsd:type
- datatype annotation
- converting data types [SQLXML]
- data types [SQLXML], mapping data types
- XSD schemas [SQLXML], mapping data types
ms.assetid: db192105-e8aa-4392-b812-9d727918c005
author: rothja
ms.author: jroth
ms.openlocfilehash: 22f1b0af93e3b596d74bc107ab6947b9855a2cf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595905"
---
# <a name="data-type-coercions-and-the-sqldatatype-annotation-sqlxml-40"></a><span data-ttu-id="838fd-102">資料類型強制型轉和 sql:datatype 註解 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="838fd-102">Data Type Coercions and the sql:datatype Annotation (SQLXML 4.0)</span></span>
  <span data-ttu-id="838fd-103">在 XSD 結構描述中，`xsd:type` 屬性會指定元素或屬性的 XSD 資料類型。</span><span class="sxs-lookup"><span data-stu-id="838fd-103">In an XSD schema, the `xsd:type` attribute specifies the XSD data type of an element or attribute.</span></span> <span data-ttu-id="838fd-104">當 XSD 結構描述用於從資料庫擷取資料時，指定的資料類型則會用於將資料格式化。</span><span class="sxs-lookup"><span data-stu-id="838fd-104">When an XSD schema is used to extract data from the database, the data type specified is used to format the data.</span></span>  
  
 <span data-ttu-id="838fd-105">除了在結構描述中指定 XSD 類型，您也可以藉由使用 `sql:datatype` 註解指定 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="838fd-105">In addition to specifying an XSD type in a schema, you can also specify a Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type by using the `sql:datatype` annotation.</span></span> <span data-ttu-id="838fd-106">在 XSD 資料類型和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型之間，`xsd:type` 和 `sql:datatype` 屬性會控制對應。</span><span class="sxs-lookup"><span data-stu-id="838fd-106">The `xsd:type` and `sql:datatype` attributes control the mapping between XSD data types and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span>  
  
## <a name="xsdtype-attribute"></a><span data-ttu-id="838fd-107">xsd:type 屬性</span><span class="sxs-lookup"><span data-stu-id="838fd-107">xsd:type Attribute</span></span>  
 <span data-ttu-id="838fd-108">您可以使用 `xsd:type` 屬性指定屬性或元素之 XML 資料類型，而該屬性或元素是對應到資料行的。</span><span class="sxs-lookup"><span data-stu-id="838fd-108">You can use the `xsd:type` attribute to specify the XML data type of an attribute or element that maps to a column.</span></span> <span data-ttu-id="838fd-109">`xsd:type` 會影響從伺服器傳回的文件，以及已執行的 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="838fd-109">The `xsd:type` affects the document that is returned from the server and also the XPath query that is executed.</span></span> <span data-ttu-id="838fd-110">當 XPath 查詢針對包含 `xsd:type` 的對應結構描述執行時，XPath 則會在處理查詢的同時使用指定的資料類型。</span><span class="sxs-lookup"><span data-stu-id="838fd-110">When an XPath query is executed against a mapping schema that contains `xsd:type`, XPath uses the specified data type when it processes the query.</span></span> <span data-ttu-id="838fd-111">如需有關 XPath 如何使用的詳細資訊 `xsd:type` ，請參閱[將 XSD 資料類型對應到 Xpath 資料類型 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="838fd-111">For more information about how XPath uses `xsd:type`, see [Mapping XSD Data Types to XPath Data Types &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="838fd-112">在傳回的文件中，所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型會轉換為字串表示。</span><span class="sxs-lookup"><span data-stu-id="838fd-112">In a returned document, all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types are converted into string representations.</span></span> <span data-ttu-id="838fd-113">某些資料類型需要額外的轉換。</span><span class="sxs-lookup"><span data-stu-id="838fd-113">Some data types require additional conversions.</span></span> <span data-ttu-id="838fd-114">下表列出用於各種 `xsd:type` 值的轉換。</span><span class="sxs-lookup"><span data-stu-id="838fd-114">The following table lists the conversions that are used for various `xsd:type` values.</span></span>  
  
|<span data-ttu-id="838fd-115">XSD 資料類型</span><span class="sxs-lookup"><span data-stu-id="838fd-115">XSD data type</span></span>|<span data-ttu-id="838fd-116">SQL Server 轉換</span><span class="sxs-lookup"><span data-stu-id="838fd-116">SQL Server conversion</span></span>|  
|-------------------|---------------------------|  
|<span data-ttu-id="838fd-117">Boolean</span><span class="sxs-lookup"><span data-stu-id="838fd-117">Boolean</span></span>|<span data-ttu-id="838fd-118">CONVERT(bit, COLUMN)</span><span class="sxs-lookup"><span data-stu-id="838fd-118">CONVERT(bit, COLUMN)</span></span>|  
|<span data-ttu-id="838fd-119">Date</span><span class="sxs-lookup"><span data-stu-id="838fd-119">Date</span></span>|<span data-ttu-id="838fd-120">LEFT(CONVERT(nvarchar(4000), COLUMN, 126), 10)</span><span class="sxs-lookup"><span data-stu-id="838fd-120">LEFT(CONVERT(nvarchar(4000), COLUMN, 126), 10)</span></span>|  
|<span data-ttu-id="838fd-121">decimal</span><span class="sxs-lookup"><span data-stu-id="838fd-121">decimal</span></span>|<span data-ttu-id="838fd-122">CONVERT(money, COLUMN)</span><span class="sxs-lookup"><span data-stu-id="838fd-122">CONVERT(money, COLUMN)</span></span>|  
|<span data-ttu-id="838fd-123">id/idref/idrefs</span><span class="sxs-lookup"><span data-stu-id="838fd-123">id/idref/idrefs</span></span>|<span data-ttu-id="838fd-124">id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)</span><span class="sxs-lookup"><span data-stu-id="838fd-124">id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)</span></span>|  
|<span data-ttu-id="838fd-125">nmtoken/nmtokens</span><span class="sxs-lookup"><span data-stu-id="838fd-125">nmtoken/nmtokens</span></span>|<span data-ttu-id="838fd-126">id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)</span><span class="sxs-lookup"><span data-stu-id="838fd-126">id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)</span></span>|  
|<span data-ttu-id="838fd-127">Time</span><span class="sxs-lookup"><span data-stu-id="838fd-127">Time</span></span>|<span data-ttu-id="838fd-128">SUBSTRING(CONVERT(nvarchar(4000), COLUMN, 126), 1+CHARINDEX(N'T', CONVERT(nvarchar(4000), COLUMN, 126)), 24)</span><span class="sxs-lookup"><span data-stu-id="838fd-128">SUBSTRING(CONVERT(nvarchar(4000), COLUMN, 126), 1+CHARINDEX(N'T', CONVERT(nvarchar(4000), COLUMN, 126)), 24)</span></span>|  
|<span data-ttu-id="838fd-129">All others</span><span class="sxs-lookup"><span data-stu-id="838fd-129">All others</span></span>|<span data-ttu-id="838fd-130">No additional conversion</span><span class="sxs-lookup"><span data-stu-id="838fd-130">No additional conversion</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="838fd-131">某些由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回的值可能無法與藉由使用 `xsd:type` 指定的 XML 資料類型相容，這是因為轉換是不可行的 (例如，轉換 "XYZ" 為 `decimal` 資料類型) 或是因為值超過資料類型範圍 (例如，-100000 轉換為 `UnsignedShort` XSD 類型)。</span><span class="sxs-lookup"><span data-stu-id="838fd-131">Some of the values returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might not be compatible with the XML data types that are specified by using `xsd:type`, either because the conversion is not possible (for example, converting "XYZ" to a `decimal` data type) or because the value exceeds the range of that data type (for example, -100000 converted to an `UnsignedShort` XSD type).</span></span> <span data-ttu-id="838fd-132">不相容的類型轉換可能產生無效的 XML 文件或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤。</span><span class="sxs-lookup"><span data-stu-id="838fd-132">Incompatible type conversions might result in XML documents that are not valid, or in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] errors.</span></span>  
  
## <a name="mapping-from-sql-server-data-types-to-xsd-data-types"></a><span data-ttu-id="838fd-133">從 SQL Server 資料類型對應到 XSD 資料類型</span><span class="sxs-lookup"><span data-stu-id="838fd-133">Mapping from SQL Server Data Types to XSD Data Types</span></span>  
 <span data-ttu-id="838fd-134">下表列出從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型對應到 XSD 資料類型的明顯對應。</span><span class="sxs-lookup"><span data-stu-id="838fd-134">The following table shows an obvious mapping from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types to XSD data types.</span></span> <span data-ttu-id="838fd-135">如果您知道 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 類型，這個表格會提供您在 XSD 結構描述中可以指定的對應 XSD 類型。</span><span class="sxs-lookup"><span data-stu-id="838fd-135">If you know the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type, this table provides the corresponding XSD type that you can specify in the XSD schema.</span></span>  
  
|<span data-ttu-id="838fd-136">SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="838fd-136">SQL Server data type</span></span>|<span data-ttu-id="838fd-137">XSD 資料類型</span><span class="sxs-lookup"><span data-stu-id="838fd-137">XSD data type</span></span>|  
|--------------------------|-------------------|  
|`bigint`|`long`|  
|`binary`|`base64Binary`|  
|`bit`|`boolean`|  
|`char`|`string`|  
|`datetime`|`dateTime`|  
|`decimal`|`decimal`|  
|`float`|`double`|  
|`image`|`base64Binary`|  
|`int`|`int`|  
|`money`|`decimal`|  
|`nchar`|`string`|  
|`ntext`|`string`|  
|`nvarchar`|`string`|  
|`numeric`|`decimal`|  
|`real`|`float`|  
|`smalldatetime`|`dateTime`|  
|`smallint`|`short`|  
|`smallmoney`|`decimal`|  
|`sql_variant`|`string`|  
|`sysname`|`string`|  
|`text`|`string`|  
|`timestamp`|`dateTime`|  
|`tinyint`|`unsignedByte`|  
|`varbinary`|`base64Binary`|  
|`varchar`|`string`|  
|`uniqueidentifier`|`string`|  
  
## <a name="sqldatatype-annotation"></a><span data-ttu-id="838fd-138">sql:datatype 註解</span><span class="sxs-lookup"><span data-stu-id="838fd-138">sql:datatype Annotation</span></span>  
 <span data-ttu-id="838fd-139">`sql:datatype` 註解是用於指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型，而且該註解必須在下列狀況中指定：</span><span class="sxs-lookup"><span data-stu-id="838fd-139">The `sql:datatype` annotation is used to specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type; this annotation must be specified when:</span></span>  
  
-   <span data-ttu-id="838fd-140">您會 `dateTime` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 從 XSD `dateTime` 、 `date` 或 `time` 類型大量載入至資料行。</span><span class="sxs-lookup"><span data-stu-id="838fd-140">You are bulk loading into a `dateTime`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] column from an XSD `dateTime`, `date`, or `time` type.</span></span> <span data-ttu-id="838fd-141">在這個狀況下，您必須藉由使用 `sql:datatype="dateTime"` 指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料行資料類型。</span><span class="sxs-lookup"><span data-stu-id="838fd-141">In this case, you must identify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] column data type by using `sql:datatype="dateTime"`.</span></span> <span data-ttu-id="838fd-142">這項規則也套用於 Updategram。</span><span class="sxs-lookup"><span data-stu-id="838fd-142">This rule also applies to updategrams.</span></span>  
  
-   <span data-ttu-id="838fd-143">您會大量載入類型的資料行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `uniqueidentifier` ，而且 XSD 值是包含大括弧 ( {和} ) 的 GUID。</span><span class="sxs-lookup"><span data-stu-id="838fd-143">You are bulk loading into a column of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `uniqueidentifier` type and the XSD value is a GUID that includes braces ({ and }).</span></span> <span data-ttu-id="838fd-144">當您指定 `sql:datatype="uniqueidentifier"` 時，大括號會先從值上移除，然後才插入資料行。</span><span class="sxs-lookup"><span data-stu-id="838fd-144">When you specify `sql:datatype="uniqueidentifier"`, the braces are removed from the value before it is inserted in the column.</span></span> <span data-ttu-id="838fd-145">如果未指定 `sql:datatype`，值會跟著大括號傳送出去，而且插入或更新動作會失敗。</span><span class="sxs-lookup"><span data-stu-id="838fd-145">If `sql:datatype` is not specified, the value is sent with the braces, and the insert or update fails.</span></span>  
  
-   <span data-ttu-id="838fd-146">XML 資料類型 `base64Binary` 對應到各種 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型 (`binary`、`image` 或 `varbinary`)。</span><span class="sxs-lookup"><span data-stu-id="838fd-146">The XML data type `base64Binary` maps to various [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types (`binary`, `image`, or `varbinary`).</span></span> <span data-ttu-id="838fd-147">若要將 XML 資料類型 `base64Binary` 對應到特定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型，請使用 `sql:datatype` 註解。</span><span class="sxs-lookup"><span data-stu-id="838fd-147">To map the XML data type `base64Binary` to a specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type, use the `sql:datatype` annotation.</span></span> <span data-ttu-id="838fd-148">該註解會指定資料行明確的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型，而該資料行是屬性對應之資料行。</span><span class="sxs-lookup"><span data-stu-id="838fd-148">This annotation specifies the explicit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type of the column to which the attribute maps.</span></span> <span data-ttu-id="838fd-149">當資料儲存在資料庫中時，這樣的作法就很有用。</span><span class="sxs-lookup"><span data-stu-id="838fd-149">This is useful when data is being stored in the databases.</span></span> <span data-ttu-id="838fd-150">藉由指定 `sql:datatype` 註解，您可以識別明確的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="838fd-150">By specifying the `sql:datatype` annotation, you can identify the explicit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>  
  
 <span data-ttu-id="838fd-151">一般建議您在結構描述中指定 `sql:datatype`。</span><span class="sxs-lookup"><span data-stu-id="838fd-151">It is generally recommended that you specify `sql:datatype` in the schema.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="838fd-152">範例</span><span class="sxs-lookup"><span data-stu-id="838fd-152">Examples</span></span>  
 <span data-ttu-id="838fd-153">若要使用下列範例建立工作範例，您必須符合某些需求。</span><span class="sxs-lookup"><span data-stu-id="838fd-153">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="838fd-154">如需詳細資訊，請參閱[執行 SQLXML 範例的需求](../sqlxml/requirements-for-running-sqlxml-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="838fd-154">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-xsdtype"></a><span data-ttu-id="838fd-155">A.</span><span class="sxs-lookup"><span data-stu-id="838fd-155">A.</span></span> <span data-ttu-id="838fd-156">指定 xsd:type</span><span class="sxs-lookup"><span data-stu-id="838fd-156">Specifying xsd:type</span></span>  
 <span data-ttu-id="838fd-157">這個範例示範在結構描述中，藉由使用 `date` 屬性所指定的 XSD `xsd:type` 類型是如何影響產生的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="838fd-157">This example shows how an XSD `date` type that is specified by using the `xsd:type` attribute in the schema affects the resulting XML document.</span></span> <span data-ttu-id="838fd-158">該結構描述在 AdventureWorks 資料庫中會提供 Sales.SalesOrderHeader 資料表的 XML 檢視。</span><span class="sxs-lookup"><span data-stu-id="838fd-158">The schema provides an XML view of the Sales.SalesOrderHeader table in the AdventureWorks database.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader">  
     <xsd:complexType>  
       <xsd:attribute name="SalesOrderID" type="xsd:string" />   
       <xsd:attribute name="CustomerID"   type="xsd:string" />   
       <xsd:attribute name="OrderDate"    type="xsd:date" />   
       <xsd:attribute name="DueDate"  />   
       <xsd:attribute name="ShipDate"  type="xsd:time" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="838fd-159">在這個 XSD 結構描述中，有三種屬性會從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回日期值。</span><span class="sxs-lookup"><span data-stu-id="838fd-159">In this XSD schema, there are three attributes that return a date value from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="838fd-160">當結構描述：</span><span class="sxs-lookup"><span data-stu-id="838fd-160">When the schema:</span></span>  
  
-   <span data-ttu-id="838fd-161">指定 `xsd:type=date` 在 [**訂購**日期] 屬性上， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會顯示針對 [**訂購**] 屬性所傳回之值的日期部分。</span><span class="sxs-lookup"><span data-stu-id="838fd-161">Specifies `xsd:type=date` on the **OrderDate** attribute, the date part of the value returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the **OrderDate** attribute is displayed.</span></span>  
  
-   <span data-ttu-id="838fd-162">`xsd:type=time`在**ShipDate**屬性上指定，會 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 顯示針對**ShipDate**屬性所傳回之值的時間部分。</span><span class="sxs-lookup"><span data-stu-id="838fd-162">Specifies `xsd:type=time` on the **ShipDate** attribute, the time part of the value that is returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the **ShipDate** attribute is displayed.</span></span>  
  
-   <span data-ttu-id="838fd-163">不會 `xsd:type` 在**DueDate**屬性上指定，會顯示所傳回的相同值 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="838fd-163">Does not specify `xsd:type` on the **DueDate** attribute, the same value that is returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is displayed.</span></span>  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="838fd-164">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="838fd-164">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="838fd-165">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="838fd-165">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="838fd-166">將檔案儲存為 xsdType.xml。</span><span class="sxs-lookup"><span data-stu-id="838fd-166">Save the file as xsdType.xml.</span></span>  
  
2.  <span data-ttu-id="838fd-167">複製下列範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="838fd-167">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="838fd-168">將檔案儲存為 xsdTypeT.xml 並放在與 xsdType.xml 一樣的目錄中。</span><span class="sxs-lookup"><span data-stu-id="838fd-168">Save the file as xsdTypeT.xml in the same directory where you saved xsdType.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="xsdType.xml">  
        /Order  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="838fd-169">指定給對應結構描述 (xsdType.xml) 的目錄路徑，與儲存範本之目錄相關。</span><span class="sxs-lookup"><span data-stu-id="838fd-169">The directory path specified for the mapping schema (xsdType.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="838fd-170">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="838fd-170">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\xsdType.xml"  
    ```  
  
3.  <span data-ttu-id="838fd-171">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="838fd-171">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="838fd-172">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="838fd-172">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="838fd-173">部分結果集如下：</span><span class="sxs-lookup"><span data-stu-id="838fd-173">Here is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="43659"   
         CustomerID="676"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
  <Order SalesOrderID="43660"   
         CustomerID="117"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
 ...  
</ROOT>  
```  
  
 <span data-ttu-id="838fd-174">這是相等的 XDR 結構描述：</span><span class="sxs-lookup"><span data-stu-id="838fd-174">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="Order" sql:relation="Sales.SalesOrderHeader">  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="CustomerID"  />  
    <AttributeType name="OrderDate" dt:type="date" />  
    <AttributeType name="DueDate" />  
    <AttributeType name="ShipDate" dt:type="time" />  
  
    <attribute type="SalesOrderID" sql:field="OrderID" />  
    <attribute type="CustomerID" sql:field="CustomerID" />  
    <attribute type="OrderDate" sql:field="OrderDate" />  
    <attribute type="DueDate" sql:field="DueDate" />  
    <attribute type="ShipDate" sql:field="ShipDate" />  
</ElementType>  
</Schema>  
```  
  
### <a name="b-specifying-sql-data-type-using-sqldatatype"></a><span data-ttu-id="838fd-175">B.</span><span class="sxs-lookup"><span data-stu-id="838fd-175">B.</span></span> <span data-ttu-id="838fd-176">藉由使用 sql:datatype 指定 SQL 資料類型</span><span class="sxs-lookup"><span data-stu-id="838fd-176">Specifying SQL data type using sql:datatype</span></span>  
 <span data-ttu-id="838fd-177">如需實用範例，請參閱[XML 大量載入範例中的範例 G &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="838fd-177">For a working sample, see Example G in [XML Bulk Load Examples &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md).</span></span> <span data-ttu-id="838fd-178">在這個範例中，包含 "{" 和 "}" 的 GUID 值是大量載入的。</span><span class="sxs-lookup"><span data-stu-id="838fd-178">In this example, a GUID value including "{" and "}" is bulk loaded.</span></span> <span data-ttu-id="838fd-179">在這個範例中的結構描述會指定 `sql:datatype` 將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型識別為 `uniqueidentifier`。</span><span class="sxs-lookup"><span data-stu-id="838fd-179">The schema in this example specifies `sql:datatype` to identify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type as `uniqueidentifier`.</span></span> <span data-ttu-id="838fd-180">這個範例會說明在結構描述中什麼時候必須指定 `sql:datatype`。</span><span class="sxs-lookup"><span data-stu-id="838fd-180">This example illustrate when `sql:datatype` must be specified in the schema.</span></span>  
  
  
