---
title: 建立 XML 資料的執行個體 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- type casting string instances [XML in SQL Server]
- XML [SQL Server], typed
- xml data type [SQL Server], generating instances
- casting string instances [XML in SQL Server]
- typed XML
- generating XML instances [SQL Server]
- XML [SQL Server], generating instances
- white space [XML in SQL Server]
ms.assetid: dbd6c06f-db6e-44a7-855a-6a55bf374907
author: rothja
ms.author: jroth
ms.openlocfilehash: c857b9ebbe559de34fdac925642f9270d9cbf936
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710474"
---
# <a name="create-instances-of-xml-data"></a><span data-ttu-id="390a8-102">建立 XML 資料的執行個體</span><span class="sxs-lookup"><span data-stu-id="390a8-102">Create Instances of XML Data</span></span>
  <span data-ttu-id="390a8-103">這個主題描述如何產生 XML 執行個體。</span><span class="sxs-lookup"><span data-stu-id="390a8-103">This topic describes how to generate XML instances.</span></span>  
  
 <span data-ttu-id="390a8-104">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，您可以用下列方式產生 XML 執行個體：</span><span class="sxs-lookup"><span data-stu-id="390a8-104">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can generate XML instances in the following ways:</span></span>  
  
-   <span data-ttu-id="390a8-105">類型轉換字串執行個體。</span><span class="sxs-lookup"><span data-stu-id="390a8-105">Type casting string instances.</span></span>  
  
-   <span data-ttu-id="390a8-106">使用含有 FOR XML 子句的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="390a8-106">Using the SELECT statement with the FOR XML clause.</span></span>  
  
-   <span data-ttu-id="390a8-107">使用常數指派。</span><span class="sxs-lookup"><span data-stu-id="390a8-107">Using constant assignments.</span></span>  
  
-   <span data-ttu-id="390a8-108">使用大量載入。</span><span class="sxs-lookup"><span data-stu-id="390a8-108">Using bulk load.</span></span>  
  
## <a name="type-casting-string-and-binary-instances"></a><span data-ttu-id="390a8-109">類型轉換字串和二進位執行個體</span><span class="sxs-lookup"><span data-stu-id="390a8-109">Type Casting String and Binary Instances</span></span>  
 <span data-ttu-id="390a8-110">您可以將字串 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型（例如 [**n**] [**var**]**char**、 **[n] text**、 **Varbinary**及**image**）剖析成 `xml` 資料類型，方法是將 (CAST 轉換) 或轉換 (將字串) 轉換成 `xml` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="390a8-110">You can parse any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] string data types, such as [**n**][**var**]**char**, **[n]text**, **varbinary**,and **image**, into the `xml` data type by casting (CAST) or converting (CONVERT) the string to the `xml` data type.</span></span> <span data-ttu-id="390a8-111">將會檢查不具類型的 XML 以確認它的格式正確。</span><span class="sxs-lookup"><span data-stu-id="390a8-111">Untyped XML is checked to confirm that it is well formed.</span></span> <span data-ttu-id="390a8-112">如果有與類型相關聯的架構 `xml` ，也會執行驗證。</span><span class="sxs-lookup"><span data-stu-id="390a8-112">If there is a schema associated with the `xml` type, validation is also performed.</span></span> <span data-ttu-id="390a8-113">如需詳細資訊，請參閱 [比較具類型的 XML 與不具類型的 XML](compare-typed-xml-to-untyped-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="390a8-113">For more information, see [Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md).</span></span>  
  
 <span data-ttu-id="390a8-114">XML 文件可以使用不同的編碼 (例如，UTF-8、UTF-16、windows-1252) 加以編碼。</span><span class="sxs-lookup"><span data-stu-id="390a8-114">XML documents can be encoded with different encodings (for example, UTF-8, UTF-16, windows-1252).</span></span> <span data-ttu-id="390a8-115">以下是字串與二進位來源類型如何與 XML 文件編碼互動以及剖析器作用方式的規則。</span><span class="sxs-lookup"><span data-stu-id="390a8-115">The following outlines the rules on how the string and binary source types interact with the XML document encoding and how the parser behaves.</span></span>  
  
 <span data-ttu-id="390a8-116">由於 **nvarchar** 假設使用兩個位元組的 Unicode 編碼 (例如 UTF-16 或 UCS-2)，因此 XML 剖析器會將字串值視為兩個位元組的 Unicode 編碼 XML 文件或片段。</span><span class="sxs-lookup"><span data-stu-id="390a8-116">Since **nvarchar** assumes a two-byte unicode encoding such as UTF-16 or UCS-2, the XML parser will treat the string value as a two-byte Unicode encoded XML document or fragment.</span></span> <span data-ttu-id="390a8-117">這表示必須將 XML 文件以兩個位元組的 Unicode 編碼加以編碼，才能與來源資料類型相容。</span><span class="sxs-lookup"><span data-stu-id="390a8-117">This means that the XML document needs to be encoded in a two-byte Unicode encoding as well to be compatible with the source data type.</span></span> <span data-ttu-id="390a8-118">雖然 UTF-16 編碼的 XML 文件可有 UTF-16 位元組順序標示 (BOM)，但它並不需要，因為來源類型的內容已經清楚表示，它只能為兩個位元組的 Unicode 編碼文件。</span><span class="sxs-lookup"><span data-stu-id="390a8-118">A UTF-16 encoded XML document can have a UTF-16 byte order mark (BOM), but it does not need to, since the context of the source type makes it clear that it can only be a two-byte Unicode encoded document.</span></span>  
  
 <span data-ttu-id="390a8-119">XML 剖析器會將 **varchar** 字串的內容視為一個位元組編碼的 XML 文件/片段。</span><span class="sxs-lookup"><span data-stu-id="390a8-119">The content of a **varchar** string is treated as a one-byte encoded XML document/fragment by the XML parser.</span></span> <span data-ttu-id="390a8-120">由於 **varchar** 來源字串有相關聯的字碼頁，當 XML 本身未明確指定編碼時，剖析器將使用該字碼頁進行編碼。如果 XML 執行個體具有 BOM 編碼宣告，此 BOM 或宣告必須與字碼頁一致，否則剖析器將會報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="390a8-120">Since the **varchar** source string has a code page associated, the parser will use that code page for the encoding if no explicit encoding is specified in the XML itself If an XML instance has a BOM or an encoding declaration, the BOM or declaration needs to be consistent with the code page, otherwise the parser will report an error.</span></span>  
  
 <span data-ttu-id="390a8-121">**varbinary** 的內容會被視為是直接傳送至 XML 剖析器的字碼指標資料流。</span><span class="sxs-lookup"><span data-stu-id="390a8-121">The content of **varbinary** is treated as a codepoint stream that is passed directly to the XML parser.</span></span> <span data-ttu-id="390a8-122">因此，XML 文件或片段必須以內嵌方式提供 BOM 或其他編碼資訊。</span><span class="sxs-lookup"><span data-stu-id="390a8-122">Thus, the XML document or fragment needs to provide the BOM or other encoding information inline.</span></span> <span data-ttu-id="390a8-123">剖析器只會查看資料流來決定編碼。</span><span class="sxs-lookup"><span data-stu-id="390a8-123">The parser will only look at the stream to determine the encoding.</span></span> <span data-ttu-id="390a8-124">這表示 UTF-16 編碼的 XML 必須提供 UTF-16 BOM，不具有 BOM 和宣告編碼的執行個體將被解譯為 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="390a8-124">This means that UTF-16 encoded XML needs to provide the UTF-16 BOM and an instance without BOM and without a declaration encoding will be interpreted as UTF-8.</span></span>  
  
 <span data-ttu-id="390a8-125">如果預先不知道 XML 文件的編碼，且在轉換成 XML 之前，將資料傳送為字串或二進位資料而非 XML 資料，則建議將資料視為 **varbinary**。</span><span class="sxs-lookup"><span data-stu-id="390a8-125">If the encoding of the XML document is not known in advance and the data is passed as string or binary data instead of XML data before casting to XML, it is recommended to treat the data as **varbinary**.</span></span> <span data-ttu-id="390a8-126">例如，使用 OpenRowset() 讀取 XML 檔案的資料時，必須將要讀取的資料指定為 **varbinary(max)** 值：</span><span class="sxs-lookup"><span data-stu-id="390a8-126">For example, when reading data from an XML file using OpenRowset(), one should specify the data to be read as a **varbinary(max)** value:</span></span>  
  
```  
select CAST(x as XML)   
from OpenRowset(BULK 'filename.xml', SINGLE_BLOB) R(x)  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="390a8-127">在內部以 UTF-16 編碼之有效率的二進位表示法來表示 XML。</span><span class="sxs-lookup"><span data-stu-id="390a8-127">internally represents XML in an efficient binary representation that uses UTF-16 encoding.</span></span> <span data-ttu-id="390a8-128">不會保留使用者提供的編碼，但是會在剖析過程中考慮該編碼。</span><span class="sxs-lookup"><span data-stu-id="390a8-128">User-provided encoding is not preserved, but is considered during the parse process.</span></span>  
  
### <a name="type-casting-clr-user-defined-types"></a><span data-ttu-id="390a8-129">類型轉換 CLR 使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="390a8-129">Type Casting CLR user-defined types</span></span>  
 <span data-ttu-id="390a8-130">如果 CLR 使用者定義型別具有 XML 序列化，即可將該類型的執行個體明確轉換成 XML 資料類型。</span><span class="sxs-lookup"><span data-stu-id="390a8-130">If a CLR user-defined type has an XML Serialization, instances of that type can be explicitly cast to an XML datatype.</span></span> <span data-ttu-id="390a8-131">如需有關 CLR 使用者定義型別之 XML 序列化的詳細資料，請參閱 [從 CLR 資料庫物件進行 XML 序列化](../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="390a8-131">For more details about the XML serialization of a CLR user-defined typed, see [XML Serialization from CLR Database Objects](../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md).</span></span>  
  
### <a name="white-space-handling-in-typed-xml"></a><span data-ttu-id="390a8-132">以具類型的 XML 處理空白</span><span class="sxs-lookup"><span data-stu-id="390a8-132">White Space Handling in Typed XML</span></span>  
 <span data-ttu-id="390a8-133">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，元素內容中的空白如果發生在以標記 (如開始或結束標記) 所分隔的僅空白字元資料序列內且未實體化，則會將它視為無意義。</span><span class="sxs-lookup"><span data-stu-id="390a8-133">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], white space inside element content is considered insignificant if it occurs inside a sequence of white-space-only character data delimited by markup, such as begin or end tags, and is not entitized.</span></span> <span data-ttu-id="390a8-134">(將會忽略 CDATA 區段。)空白處理的方式與 XML 1.0 規格 (由全球資訊網協會 (W3C) 所發佈) 所述的空白處理方式不同。</span><span class="sxs-lookup"><span data-stu-id="390a8-134">(CDATA sections are ignored.) This handling of white space handling is different from how white space is described in the XML 1.0 specification published by the World Wide Web Consortium (W3C).</span></span> <span data-ttu-id="390a8-135">這是因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的 XML 剖析器，只能辨識有限的 DTD 子集數目，如 XML 1.0 中所定義。</span><span class="sxs-lookup"><span data-stu-id="390a8-135">This is because the XML parser in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recognizes only a limited number of DTD subsets, as defined in XML 1.0.</span></span> <span data-ttu-id="390a8-136">如需有關 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中所支援之有限 DTD 子集的詳細資訊，請參閱 [CAST 和 CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="390a8-136">For more information about the limited DTD subsets supported in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
 <span data-ttu-id="390a8-137">依預設，只要下列任一項為真，當 XML 剖析器將字串資料轉換成 XML 時，將會捨棄無意義的空白。</span><span class="sxs-lookup"><span data-stu-id="390a8-137">By default, the XML parser discards insignificant white space when it converts string data to XML if either of the following is true:</span></span>  
  
-   <span data-ttu-id="390a8-138">`The xml:space` 未在項目或其上階項目定義屬性。</span><span class="sxs-lookup"><span data-stu-id="390a8-138">`The xml:space` attribute is not defined on an element or its ancestor elements.</span></span>  
  
-   <span data-ttu-id="390a8-139">在某個元素或在其中一個它的上階元素生效的 `xml:space` 屬性，具有預設值。</span><span class="sxs-lookup"><span data-stu-id="390a8-139">The `xml:space` attribute in effect on an element, or one of its ancestor elements, has the value of default.</span></span>  
  
 <span data-ttu-id="390a8-140">例如：</span><span class="sxs-lookup"><span data-stu-id="390a8-140">For example:</span></span>  
  
```  
declare @x xml  
set @x = '<root>      <child/>     </root>'  
select @x   
```  
  
 <span data-ttu-id="390a8-141">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="390a8-141">This is the result:</span></span>  
  
```  
<root><child/></root>  
```  
  
 <span data-ttu-id="390a8-142">然而，您可以變更此行為。</span><span class="sxs-lookup"><span data-stu-id="390a8-142">However, you can change this behavior.</span></span> <span data-ttu-id="390a8-143">若要保留 XML DT 執行個體的空白字元，請使用 CONVERT 運算子並將其選擇性的 *style* 參數值設為 1。</span><span class="sxs-lookup"><span data-stu-id="390a8-143">To preserve white space for an xml DT instance, use the CONVERT operator and its optional *style* parameter set to a value of 1.</span></span> <span data-ttu-id="390a8-144">例如：</span><span class="sxs-lookup"><span data-stu-id="390a8-144">For example:</span></span>  
  
```  
SELECT CONVERT(xml, N'<root>      <child/>     </root>', 1)  
```  
  
 <span data-ttu-id="390a8-145">如果未使用 *style* 參數或是將其值設為 0，在轉換 xml DT 執行個體時，將不會保留不重要的空白。</span><span class="sxs-lookup"><span data-stu-id="390a8-145">If the *style* parameter is either not used or its value is set to 0, insignificant white space is not preserved for the conversion of the xml DT instance.</span></span> <span data-ttu-id="390a8-146">如需如何使用 CONVERT 運算子以及將字串資料轉換成 xmlDT 執行個體時其 *style* 參數的詳細資訊，請參閱 [CAST 和 CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="390a8-146">For more information about how to use the CONVERT operator and its *style* parameter when converting string data to xml DT instances, see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
### <a name="example-cast-a-string-value-to-typed-xml-and-assign-it-to-a-column"></a><span data-ttu-id="390a8-147">範例：將字串值轉換成具類型的 XML 並將它指派給資料行</span><span class="sxs-lookup"><span data-stu-id="390a8-147">Example: Cast a string value to typed xml and assign it to a column</span></span>  
 <span data-ttu-id="390a8-148">下列範例會將包含 XML 片段的字串變數轉換成 `xml` 資料類型，然後將它儲存在類型資料 `xml` 行中：</span><span class="sxs-lookup"><span data-stu-id="390a8-148">The following example casts a string variable that contains an XML fragment to the `xml` data type and then stores it in the `xml` type column:</span></span>  
  
```  
CREATE TABLE T(c1 int primary key, c2 xml)  
go  
DECLARE  @s varchar(100)  
SET @s = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
```  
  
 <span data-ttu-id="390a8-149">下列插入作業會將字串隱含地轉換為 `xml` 類型：</span><span class="sxs-lookup"><span data-stu-id="390a8-149">The following insert operation implicitly converts from a string to the `xml` type:</span></span>  
  
```  
INSERT INTO T VALUES (3, @s)   
```  
  
 <span data-ttu-id="390a8-150">您可以明確地將字串 ( # A1 轉換成 `xml` 類型：</span><span class="sxs-lookup"><span data-stu-id="390a8-150">You can explicitly cast() the string to the `xml` type:</span></span>  
  
```  
INSERT INTO T VALUES (3, cast (@s as xml))  
```  
  
 <span data-ttu-id="390a8-151">或者您可以使用 convert()，如下列所示：</span><span class="sxs-lookup"><span data-stu-id="390a8-151">Or you can use convert(), as shown in the following:</span></span>  
  
```  
INSERT INTO T VALUES (3, convert (xml, @s))   
```  
  
### <a name="example-convert-a-string-to-typed-xml-and-assign-it-to-a-variable"></a><span data-ttu-id="390a8-152">範例：將字串轉換成具類型的 XML 並將它指派給變數</span><span class="sxs-lookup"><span data-stu-id="390a8-152">Example: Convert a string to typed xml and assign it to a variable</span></span>  
 <span data-ttu-id="390a8-153">在下列範例中，會將字串轉換成 `xml` 類型，並將其指派給 `xml` 資料類型的變數：</span><span class="sxs-lookup"><span data-stu-id="390a8-153">In the following example, a string is converted to `xml` type and assigned to a variable of the `xml` data type:</span></span>  
  
```  
declare @x xml  
declare  @s varchar(100)  
SET @s = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
set @x =convert (xml, @s)  
select @x  
```  
  
## <a name="using-the-select-statement-with-a-for-xml-clause"></a><span data-ttu-id="390a8-154">使用含有 FOR XML 子句的 SELECT 陳述式</span><span class="sxs-lookup"><span data-stu-id="390a8-154">Using the SELECT Statement with a FOR XML Clause</span></span>  
 <span data-ttu-id="390a8-155">您可以在 SELECT 陳述式中使用 FOR XML 子句以傳回 XML 的結果。</span><span class="sxs-lookup"><span data-stu-id="390a8-155">You can use the FOR XML clause in a SELECT statement to return results as XML.</span></span> <span data-ttu-id="390a8-156">例如：</span><span class="sxs-lookup"><span data-stu-id="390a8-156">For example:</span></span>  
  
```  
DECLARE @xmlDoc xml  
SET @xmlDoc = (SELECT Column1, Column2  
               FROM   Table1, Table2  
               WHERE   Some condition  
               FOR XML AUTO)  
 ...  
```  
  
 <span data-ttu-id="390a8-157">SELECT 語句會傳回文字 XML 片段，然後在指派至 `xml` 資料類型變數期間進行剖析。</span><span class="sxs-lookup"><span data-stu-id="390a8-157">The SELECT statement returns a textual XML fragment that is then parsed during the assignment to the `xml` data type variable.</span></span>  
  
 <span data-ttu-id="390a8-158">您也可以在 FOR XML 子句中使用[type](type-directive-in-for-xml-queries.md)指示詞，以直接傳回 for xml 查詢結果作為 `xml` 類型：</span><span class="sxs-lookup"><span data-stu-id="390a8-158">You can also use the [TYPE directive](type-directive-in-for-xml-queries.md) in the FOR XML clause that directly returns a FOR XML query result as `xml` type:</span></span>  
  
```  
Declare @xmlDoc xml  
SET @xmlDoc = (SELECT ProductModelID, Name  
               FROM   Production.ProductModel  
               WHERE  ProductModelID=19  
               FOR XML AUTO, TYPE)  
SELECT @xmlDoc  
```  
  
 <span data-ttu-id="390a8-159">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="390a8-159">This is the result:</span></span>  
  
```  
<Production.ProductModel ProductModelID="19" Name="Mountain-100" />...  
```  
  
 <span data-ttu-id="390a8-160">在下列範例中， `xml` FOR XML 查詢的具類型結果會插入至類型資料 `xml` 行：</span><span class="sxs-lookup"><span data-stu-id="390a8-160">In the following example, the typed `xml` result of a FOR XML query is inserted into an `xml` type column:</span></span>  
  
```  
CREATE TABLE T1 (c1 int, c2 xml)  
go  
INSERT T1(c1, c2)  
SELECT 1, (SELECT ProductModelID, Name  
           FROM Production.ProductModel  
           WHERE ProductModelID=19  
           FOR XML AUTO, TYPE)  
SELECT * FROM T1  
go  
```  
  
 <span data-ttu-id="390a8-161">如需 FOR XML 的詳細資訊，請參閱 [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="390a8-161">For more information about FOR XML, see [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="390a8-162">會將 `xml` 資料類型執行個體傳回用戶端，作為不同伺服器建構的結果 (例如使用 TYPE 指示詞的 FOR XML 查詢)，或者使用 `xml` 資料類型從 SQL 資料行、變數和輸出參數傳回 XML。</span><span class="sxs-lookup"><span data-stu-id="390a8-162">returns `xml` data type instances to the client as a result of different server constructs such as FOR XML queries that use the TYPE directive, or where the `xml` data type is used to return XML from SQL columns, variables, and output parameters.</span></span> <span data-ttu-id="390a8-163">在用戶端應用程式的程式碼中，ADO.NET 提供者會要求從伺服器以二進位編碼傳送這項 `xml` 資料類型資訊。</span><span class="sxs-lookup"><span data-stu-id="390a8-163">In client application code, the ADO.NET provider requests that this `xml` data type information be sent in a binary encoding from the server.</span></span> <span data-ttu-id="390a8-164">但若您使用的 FOR XML 不含 TYPE 指示詞，XML 資料就會以字串類型傳回。</span><span class="sxs-lookup"><span data-stu-id="390a8-164">However, if you are using FOR XML without the TYPE directive, the XML data returns as a string type.</span></span> <span data-ttu-id="390a8-165">在任一情況下，用戶端提供者將永遠可以處理任一 XML 形式。</span><span class="sxs-lookup"><span data-stu-id="390a8-165">In any case, the client provider will always be able to handle either form of XML.</span></span>  
  
## <a name="using-constant-assignments"></a><span data-ttu-id="390a8-166">使用常數指派</span><span class="sxs-lookup"><span data-stu-id="390a8-166">Using Constant Assignments</span></span>  
 <span data-ttu-id="390a8-167">在預期資料類型的實例時，可以使用字串常數 `xml` 。</span><span class="sxs-lookup"><span data-stu-id="390a8-167">A string constant can be used where an instance of the `xml` data type is expected.</span></span> <span data-ttu-id="390a8-168">這與使用 CAST 將字串隱含轉換成 XML 是相同的。</span><span class="sxs-lookup"><span data-stu-id="390a8-168">This is the same as an implied CAST of string to XML.</span></span> <span data-ttu-id="390a8-169">例如：</span><span class="sxs-lookup"><span data-stu-id="390a8-169">For example:</span></span>  
  
```  
DECLARE @xmlDoc xml  
SET @xmlDoc = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
-- Or  
SET @xmlDoc = N'<?xml version="1.0" encoding="ucs-2"?><doc/>'  
```  
  
 <span data-ttu-id="390a8-170">先前的範例會將字串隱含地轉換成 `xml` 資料類型，並將它指派給 `xml` 類型變數。</span><span class="sxs-lookup"><span data-stu-id="390a8-170">The previous example implicitly converts the string to the `xml` data type and assigns it to an `xml` type variable.</span></span>  
  
 <span data-ttu-id="390a8-171">下列範例會將常數位串插入型別資料 `xml` 行：</span><span class="sxs-lookup"><span data-stu-id="390a8-171">The following example inserts a constant string into an `xml` type column:</span></span>  
  
```  
CREATE TABLE T(c1 int primary key, c2 xml)  
INSERT INTO T VALUES (3, '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>')   
```  
  
> [!NOTE]  
>  <span data-ttu-id="390a8-172">對於具類型的 XML，將會針對指定的結構描述驗證 XML。</span><span class="sxs-lookup"><span data-stu-id="390a8-172">For typed XML, the XML is validated against the specified schema.</span></span> <span data-ttu-id="390a8-173">如需詳細資訊，請參閱 [比較具類型的 XML 與不具類型的 XML](compare-typed-xml-to-untyped-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="390a8-173">For more information, see [Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md).</span></span>  
  
## <a name="using-bulk-load"></a><span data-ttu-id="390a8-174">使用大量載入</span><span class="sxs-lookup"><span data-stu-id="390a8-174">Using Bulk Load</span></span>  
 <span data-ttu-id="390a8-175">增強的 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) 功能，可讓您在資料庫中大量載入 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="390a8-175">The enhanced [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) functionality allows you to bulk load XML documents in the database.</span></span> <span data-ttu-id="390a8-176">您可以從檔案將 XML 實例大量載入 `xml` 資料庫中的類型資料行。</span><span class="sxs-lookup"><span data-stu-id="390a8-176">You can bulk load XML instances from files into the `xml` type columns in the database.</span></span> <span data-ttu-id="390a8-177">如需實用範例，請參閱[大量匯入與匯出 XML 文件的範例 &#40;SQL Server&#41;](../import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="390a8-177">For working samples, see [Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;](../import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md).</span></span> <span data-ttu-id="390a8-178">如需有關載入 XML 文件的詳細資訊，請參閱 [載入 XML 資料](load-xml-data.md)。</span><span class="sxs-lookup"><span data-stu-id="390a8-178">For more information about loading XML documents, see [Load XML Data](load-xml-data.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="390a8-179">本節內容</span><span class="sxs-lookup"><span data-stu-id="390a8-179">In This Section</span></span>  
  
|<span data-ttu-id="390a8-180">主題</span><span class="sxs-lookup"><span data-stu-id="390a8-180">Topic</span></span>|<span data-ttu-id="390a8-181">描述</span><span class="sxs-lookup"><span data-stu-id="390a8-181">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="390a8-182">擷取及查詢 XML 資料</span><span class="sxs-lookup"><span data-stu-id="390a8-182">Retrieve and Query XML Data</span></span>](retrieve-and-query-xml-data.md)|<span data-ttu-id="390a8-183">描述當 XML 執行個體儲存於資料庫中時，未保留的 XML 執行個體部分。</span><span class="sxs-lookup"><span data-stu-id="390a8-183">Describes the parts of XML instances that are not preserved when they are stored in databases.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="390a8-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="390a8-184">See Also</span></span>  
 <span data-ttu-id="390a8-185">[比較具類型的 XML 與不具類型的 XML](compare-typed-xml-to-untyped-xml.md) </span><span class="sxs-lookup"><span data-stu-id="390a8-185">[Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md) </span></span>  
 <span data-ttu-id="390a8-186">[xml 資料類型方法](/sql/t-sql/xml/xml-data-type-methods) </span><span class="sxs-lookup"><span data-stu-id="390a8-186">[xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) </span></span>  
 <span data-ttu-id="390a8-187">[XML 資料修改語言 &#40;XML DML&#41;](/sql/t-sql/xml/xml-data-modification-language-xml-dml) </span><span class="sxs-lookup"><span data-stu-id="390a8-187">[XML Data Modification Language &#40;XML DML&#41;](/sql/t-sql/xml/xml-data-modification-language-xml-dml) </span></span>  
 [<span data-ttu-id="390a8-188">XML 資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="390a8-188">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
