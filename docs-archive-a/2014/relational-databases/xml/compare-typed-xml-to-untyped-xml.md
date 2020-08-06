---
title: 比較具類型的 XML 與不具類型的 XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xml data type [SQL Server], variables
- parameters [XML in SQL Server]
- facets [XML in SQL Server]
- xml data type [SQL Server], columns
- untyped XML
- xml data type [SQL Server], typed xml
- XML [SQL Server], typed
- variables [XML in SQL Server], creating
- xml data type [SQL Server], untyped xml
- columns [XML in SQL Server], creating
- typed XML
- document mode processing [SQL Server]
- XML [SQL Server], untyped
- xml data type [SQL Server], parameters
ms.assetid: 4bc50af9-2f7d-49df-bb01-854d080c72c7
author: rothja
ms.author: jroth
ms.openlocfilehash: fae9ca930bd8741a1332b61c8272f2133590483e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688658"
---
# <a name="compare-typed-xml-to-untyped-xml"></a><span data-ttu-id="2b99a-102">比較具類型的 XML 與不具類型的 XML</span><span class="sxs-lookup"><span data-stu-id="2b99a-102">Compare Typed XML to Untyped XML</span></span>
  <span data-ttu-id="2b99a-103">您可以建立 `xml` 類型的變數、參數和資料行。</span><span class="sxs-lookup"><span data-stu-id="2b99a-103">You can create variables, parameters, and columns of the `xml` type.</span></span> <span data-ttu-id="2b99a-104">此外，也可以選擇性地將 XML 結構描述的集合與 `xml` 類型的變數、參數和資料行建立關聯。</span><span class="sxs-lookup"><span data-stu-id="2b99a-104">You can optionally associate a collection of XML schemas with a variable, parameter, or column of `xml` type.</span></span> <span data-ttu-id="2b99a-105">在此情況下， `xml` 資料類型實例稱為「具*類型*」。</span><span class="sxs-lookup"><span data-stu-id="2b99a-105">In this case, the `xml` data type instance is called *typed*.</span></span> <span data-ttu-id="2b99a-106">非此種情況下的 XML 執行個體則稱為「不具類型」。</span><span class="sxs-lookup"><span data-stu-id="2b99a-106">Otherwise, the XML instance is called *untyped*.</span></span>  
  
## <a name="well-formed-xml-and-the-xml-data-type"></a><span data-ttu-id="2b99a-107">格式正確的 XML 和 xml 資料類型</span><span class="sxs-lookup"><span data-stu-id="2b99a-107">Well-formed XML and the xml Data Type</span></span>  
 <span data-ttu-id="2b99a-108">`xml` 資料類型會實作 ISO 標準 `xml` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="2b99a-108">The `xml` data type implements the ISO standard `xml` data type.</span></span> <span data-ttu-id="2b99a-109">因此，它可以在不具類型的 XML 資料行中儲存格式良好的 XML 1.0 版文件，也可以儲存含有文字節點和任意數量之最上層元素的所謂 XML 內容片段。</span><span class="sxs-lookup"><span data-stu-id="2b99a-109">Therefore, it can store well-formed XML version 1.0 documents and also so-called XML content fragments with text nodes and an arbitrary number of top-level elements in an untyped XML column.</span></span> <span data-ttu-id="2b99a-110">系統會確認資料的格式良好、不需要將資料行繫結到 XML 結構描述，並拒絕在某種程度上格式不良的資料。</span><span class="sxs-lookup"><span data-stu-id="2b99a-110">The system checks that the data is well-formed, does not require the column to be bound to XML schemas, and rejects data that is not well-formed in the extended sense.</span></span> <span data-ttu-id="2b99a-111">對於不具類型的 XML 變數和參數而言，也是如此。</span><span class="sxs-lookup"><span data-stu-id="2b99a-111">This is true also of untyped XML variables and parameters.</span></span>  
  
## <a name="xml-schemas"></a><span data-ttu-id="2b99a-112">XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="2b99a-112">XML Schemas</span></span>  
 <span data-ttu-id="2b99a-113">XML 結構描述提供下列項目：</span><span class="sxs-lookup"><span data-stu-id="2b99a-113">An XML schema provides the following:</span></span>  
  
-   <span data-ttu-id="2b99a-114">**驗證的條件約束**</span><span class="sxs-lookup"><span data-stu-id="2b99a-114">**Validation constraints.**</span></span> <span data-ttu-id="2b99a-115">：每當指派或修改了具類型的 xml 執行個體，SQL Server 就會驗證該執行個體。</span><span class="sxs-lookup"><span data-stu-id="2b99a-115">Whenever a typed xml instance is assigned to or modified, SQL Server validates the instance.</span></span>  
  
-   <span data-ttu-id="2b99a-116">**資料類型資訊**</span><span class="sxs-lookup"><span data-stu-id="2b99a-116">**Data type information.**</span></span> <span data-ttu-id="2b99a-117">結構描述會提供 `xml` 資料類型執行個體中屬性和元素類型的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2b99a-117">Schemas provide information about the types of attributes and elements in the `xml` data type instance.</span></span> <span data-ttu-id="2b99a-118">這些類型資訊針對執行個體中所包含之值所提供的運算語意，要比不具類型的 `xml` 更精確。</span><span class="sxs-lookup"><span data-stu-id="2b99a-118">The type information provides more precise operational semantics to the values contained in the instance than is possible with untyped `xml`.</span></span> <span data-ttu-id="2b99a-119">例如，十進位的數學運算可以在十進位值上執行，但不能在字串值上執行。</span><span class="sxs-lookup"><span data-stu-id="2b99a-119">For example, decimal arithmetic operations can be performed on a decimal value, but not on a string value.</span></span> <span data-ttu-id="2b99a-120">因此，具類型的 XML 儲存會比不具類型的 XML 精簡很多。</span><span class="sxs-lookup"><span data-stu-id="2b99a-120">Because of this, typed XML storage can be made significantly more compact than untyped XML.</span></span>  
  
## <a name="choosing-typed-or-untyped-xml"></a><span data-ttu-id="2b99a-121">選擇具類型或不具類型的 XML</span><span class="sxs-lookup"><span data-stu-id="2b99a-121">Choosing Typed or Untyped XML</span></span>  
 <span data-ttu-id="2b99a-122">在下列情況下，請使用不具類型的 `xml` 資料類型：</span><span class="sxs-lookup"><span data-stu-id="2b99a-122">Use untyped `xml` data type in the following situations:</span></span>  
  
-   <span data-ttu-id="2b99a-123">您沒有 XML 資料的結構描述。</span><span class="sxs-lookup"><span data-stu-id="2b99a-123">You do not have a schema for your XML data.</span></span>  
  
-   <span data-ttu-id="2b99a-124">您有結構描述，但您不想讓伺服器驗證資料。</span><span class="sxs-lookup"><span data-stu-id="2b99a-124">You have schemas, but you do not want the server to validate the data.</span></span> <span data-ttu-id="2b99a-125">當應用程式在將資料儲存於伺服器之前執行用戶端驗證時，或是根據結構描述暫時儲存無效的 XML 資料時，或是在伺服器上使用不受支援的結構描述元件時，有時會有這種情形。</span><span class="sxs-lookup"><span data-stu-id="2b99a-125">This is sometimes the case when an application performs client-side validation before storing the data at the server, or temporarily stores XML data that is invalid according to the schema, or uses schema components that are not supported at the server.</span></span>  
  
 <span data-ttu-id="2b99a-126">`xml`在下列情況下，請使用具類型的資料類型：</span><span class="sxs-lookup"><span data-stu-id="2b99a-126">Use typed `xml` data type in the following situations:</span></span>  
  
-   <span data-ttu-id="2b99a-127">您有 XML 資料的結構描述，而且想要讓伺服器根據該 XML 結構描述來驗證 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="2b99a-127">You have schemas for your XML data and you want the server to validate your XML data according to the XML schemas.</span></span>  
  
-   <span data-ttu-id="2b99a-128">您想要依據類型資訊來利用儲存體及查詢最佳化作業。</span><span class="sxs-lookup"><span data-stu-id="2b99a-128">You want to take advantage of storage and query optimizations based on type information.</span></span>  
  
-   <span data-ttu-id="2b99a-129">您想要在編譯查詢期間更有效地利用類型資訊。</span><span class="sxs-lookup"><span data-stu-id="2b99a-129">You want to take better advantage of type information during compilation of your queries.</span></span>  
  
 <span data-ttu-id="2b99a-130">具類型的 XML 資料行、參數及變數可儲存 XML 文件或內容。</span><span class="sxs-lookup"><span data-stu-id="2b99a-130">Typed XML columns, parameters, and variables can store XML documents or content.</span></span> <span data-ttu-id="2b99a-131">但是您必須在宣告時，用旗標來指定您是要儲存文件還是內容。</span><span class="sxs-lookup"><span data-stu-id="2b99a-131">However, you have to specify with a flag whether you are storing a document or content at the time of declaration.</span></span> <span data-ttu-id="2b99a-132">此外，您也必須提供 XML 結構描述的集合。</span><span class="sxs-lookup"><span data-stu-id="2b99a-132">Additionally, you have to provide the collection of XML schemas.</span></span> <span data-ttu-id="2b99a-133">如果每個 XML 執行個體都只有一個最上層元素，請指定 DOCUMENT。</span><span class="sxs-lookup"><span data-stu-id="2b99a-133">Specify DOCUMENT if each XML instance has exactly one top-level element.</span></span> <span data-ttu-id="2b99a-134">否則，請使用 CONTENT。</span><span class="sxs-lookup"><span data-stu-id="2b99a-134">Otherwise, use CONTENT.</span></span> <span data-ttu-id="2b99a-135">查詢編譯器會在查詢編譯期間，於類型檢查中使用 DOCUMENT 旗標，以推斷單一最上層元素。</span><span class="sxs-lookup"><span data-stu-id="2b99a-135">The query compiler uses the DOCUMENT flag in type checks during query compilation to infer singleton top-level elements.</span></span>  
  
## <a name="creating-typed-xml"></a><span data-ttu-id="2b99a-136">建立具類型的 XML</span><span class="sxs-lookup"><span data-stu-id="2b99a-136">Creating Typed XML</span></span>  
 <span data-ttu-id="2b99a-137">在您可以建立具類型的 `xml` 變數、參數或資料行之前，您必須先使用[CREATE XML schema Collection &#40;transact-sql&#41;](/sql/t-sql/statements/create-xml-schema-collection-transact-sql)來註冊 XML 架構集合。</span><span class="sxs-lookup"><span data-stu-id="2b99a-137">Before you can create typed `xml` variables, parameters, or columns, you must first register the XML schema collection by using [CREATE XML SCHEMA COLLECTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-xml-schema-collection-transact-sql).</span></span> <span data-ttu-id="2b99a-138">然後，您可以將 XML 結構描述集合與 `xml` 資料類型的變數、參數或資料行產生關聯。</span><span class="sxs-lookup"><span data-stu-id="2b99a-138">You can then associate the XML schema collection with variables, parameters, or columns of the `xml` data type.</span></span>  
  
 <span data-ttu-id="2b99a-139">在下列範例中，會使用兩段式命名慣例來指定 XML 結構描述集合名稱。</span><span class="sxs-lookup"><span data-stu-id="2b99a-139">In the following examples, a two-part naming convention is used for specifying the XML schema collection name.</span></span> <span data-ttu-id="2b99a-140">第一個部分是結構描述名稱，而第二個部分是 XML 結構描述集合名稱。</span><span class="sxs-lookup"><span data-stu-id="2b99a-140">The first part is the schema name, and the second part is the XML schema collection name.</span></span>  
  
### <a name="example-associating-a-schema-collection-with-an-xml-type-variable"></a><span data-ttu-id="2b99a-141">範例：將結構描述集合與 xml 類型變數產生關聯</span><span class="sxs-lookup"><span data-stu-id="2b99a-141">Example: Associating a Schema Collection with an xml Type Variable</span></span>  
 <span data-ttu-id="2b99a-142">下列範例 `xml` 會建立類型變數，並將架構集合與它產生關聯。</span><span class="sxs-lookup"><span data-stu-id="2b99a-142">The following example creates an`xml` type variable and associates a schema collection with it.</span></span> <span data-ttu-id="2b99a-143">範例中指定的結構描述集合已經匯入 **AdventureWorks** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="2b99a-143">The schema collection specified in the example is already imported in the **AdventureWorks** database.</span></span>  
  
```  
DECLARE @x xml (Production.ProductDescriptionSchemaCollection);   
```  
  
### <a name="example-specifying-a-schema-for-an-xml-type-column"></a><span data-ttu-id="2b99a-144">範例：指定 xml 類型資料行的結構描述</span><span class="sxs-lookup"><span data-stu-id="2b99a-144">Example: Specifying a Schema for an xml Type Column</span></span>  
 <span data-ttu-id="2b99a-145">下列範例會建立具有 `xml` 類型資料行的資料表，並為此資料行指定結構描述：</span><span class="sxs-lookup"><span data-stu-id="2b99a-145">The following example creates a table with an `xml` type column and specifies a schema for the column:</span></span>  
  
```  
CREATE TABLE T1(  
 Col1 int,   
 Col2 xml (Production.ProductDescriptionSchemaCollection)) ;  
```  
  
### <a name="example-passing-an-xml-type-parameter-to-a-stored-procedure"></a><span data-ttu-id="2b99a-146">範例：將 xml 類型的參數傳遞給預存程序</span><span class="sxs-lookup"><span data-stu-id="2b99a-146">Example: Passing an xml Type Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="2b99a-147">下列範例會將 `xml` 類型的參數傳送給預存程序，並為此變數指定結構描述：</span><span class="sxs-lookup"><span data-stu-id="2b99a-147">The following example passes an `xml` type parameter to a stored procedure and specifies a schema for the variable:</span></span>  
  
```  
CREATE PROCEDURE SampleProc   
  @ProdDescription xml (Production.ProductDescriptionSchemaCollection)   
AS   
...  
```  
  
 <span data-ttu-id="2b99a-148">請注意下列有關 XML 結構描述集合的項目：</span><span class="sxs-lookup"><span data-stu-id="2b99a-148">Note the following about the XML schema collection:</span></span>  
  
-   <span data-ttu-id="2b99a-149">XML 結構描述集合只適用於使用 [建立 XML 結構描述集合](/sql/t-sql/statements/create-xml-schema-collection-transact-sql)來註冊它的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2b99a-149">An XML schema collection is available only in the database in which it was registered by using [Creating an XML Schema Collection](/sql/t-sql/statements/create-xml-schema-collection-transact-sql).</span></span>  
  
-   <span data-ttu-id="2b99a-150">如果您將字串轉換成具類型的 `xml` 資料類型，則剖析作業也會根據所指定之集合中的 XML 結構描述命名空間來執行驗證和設定類型。</span><span class="sxs-lookup"><span data-stu-id="2b99a-150">If you cast from a string to a typed `xml` data type, the parsing also performs validation and typing, based on the XML schema namespaces in the collection specified.</span></span>  
  
-   <span data-ttu-id="2b99a-151">您可以將具類型的 `xml` 資料類型轉換為不具類型的 `xml` 資料類型，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="2b99a-151">You can cast from a typed `xml` data type to an untyped `xml` data type, and vice versa.</span></span>  
  
 <span data-ttu-id="2b99a-152">如需在 SQL Server 中產生 XML 之其他方法的詳細資訊，請參閱 [建立 XML 資料的執行個體](create-instances-of-xml-data.md)。</span><span class="sxs-lookup"><span data-stu-id="2b99a-152">For more information about other ways to generate XML in SQL Server, see [Create Instances of XML Data](create-instances-of-xml-data.md).</span></span> <span data-ttu-id="2b99a-153">在產生 XML 之後，可將它指派給 `xml` 資料類型的變數，或將它儲存在 `xml` 類型資料行中，以進行其他處理。</span><span class="sxs-lookup"><span data-stu-id="2b99a-153">After XML is generated, it can be assigned either to an `xml` data type variable or stored in `xml` type columns for additional processing.</span></span>  
  
 <span data-ttu-id="2b99a-154">在資料類型的階層中，`xml` 資料類型會出現在 `sql_variant` 和使用者定義類型的下面，但是會在任何內建類型的上面。</span><span class="sxs-lookup"><span data-stu-id="2b99a-154">In the data type hierarchy, the `xml` data type appears below `sql_variant` and user-defined types, but above any of the built-in types.</span></span>  
  
### <a name="example-specifying-facets-to-constrain-a-typed-xml-column"></a><span data-ttu-id="2b99a-155">範例：指定 Facet 來約束具類型的 xml 資料行</span><span class="sxs-lookup"><span data-stu-id="2b99a-155">Example: Specifying Facets to Constrain a Typed xml Column</span></span>  
 <span data-ttu-id="2b99a-156">對於具類型的 `xml` 資料行而言，您可以約束資料行，讓儲存在其中的每個執行個體只能有單一的最上層元素。</span><span class="sxs-lookup"><span data-stu-id="2b99a-156">For typed `xml` columns, you can constrain the column to allow only single, top-level elements for each instance stored in it.</span></span> <span data-ttu-id="2b99a-157">作法是，在建立資料表時指定選擇性的 `DOCUMENT` Facet，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="2b99a-157">You do this by specifying the optional `DOCUMENT` facet when a table is created, as shown in the following example:</span></span>  
  
```  
CREATE TABLE T(Col1 xml   
   (DOCUMENT Production.ProductDescriptionSchemaCollection));  
GO  
DROP TABLE T;  
GO  
```  
  
 <span data-ttu-id="2b99a-158">依預設，儲存在具類型的 `xml` 資料行中的執行個體會儲存為 XML 內容，而非 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="2b99a-158">By default, instances stored in the typed `xml` column are stored as XML content and not as XML documents.</span></span> <span data-ttu-id="2b99a-159">這樣做可允許有下列項目：</span><span class="sxs-lookup"><span data-stu-id="2b99a-159">This allows for the following:</span></span>  
  
-   <span data-ttu-id="2b99a-160">零個或者許多最上層元素</span><span class="sxs-lookup"><span data-stu-id="2b99a-160">Zero or many top-level elements</span></span>  
  
-   <span data-ttu-id="2b99a-161">最上層元素內的文字節點</span><span class="sxs-lookup"><span data-stu-id="2b99a-161">Text nodes in top-level elements</span></span>  
  
 <span data-ttu-id="2b99a-162">您也可以藉由加入 `CONTENT` Facet，明確指定此行為，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="2b99a-162">You can also explicitly specify this behavior by adding `CONTENT` facet, as shown in the following example:</span></span>  
  
```  
CREATE TABLE T(Col1 xml(CONTENT Production.ProductDescriptionSchemaCollection));  
GO -- Default  
```  
  
 <span data-ttu-id="2b99a-163">請注意，您可以在任何定義 `xml` 類型 (具類型的 xml ) 的地方，指定選擇性的 DOCUMENT/CONTENT Facet。</span><span class="sxs-lookup"><span data-stu-id="2b99a-163">Note that you can specify the optional DOCUMENT/CONTENT facets anywhere you define `xml` type (typed xml).</span></span> <span data-ttu-id="2b99a-164">例如，當您建立具類型的 `xml` 變數時，可以加入 DOCUMENT/CONTENT Facet，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2b99a-164">For example, when you create a typed `xml` variable, you can add the DOCUMENT/CONTENT facet, as shown in the following:</span></span>  
  
```  
declare @x xml (DOCUMENT Production.ProductDescriptionSchemaCollection);  
```  
  
## <a name="document-type-definition-dtd"></a><span data-ttu-id="2b99a-165">文件類型定義 (DTD)</span><span class="sxs-lookup"><span data-stu-id="2b99a-165">Document Type Definition (DTD)</span></span>  
 <span data-ttu-id="2b99a-166">`xml` 資料類型資料行、變數及參數可以用 XML 結構描述來設定類型，但不能用 DTD 來設定。</span><span class="sxs-lookup"><span data-stu-id="2b99a-166">The `xml` data type columns, variables, and parameters can be typed by using XML schema, but not by using DTD.</span></span> <span data-ttu-id="2b99a-167">但是，內嵌 DTD 可用於不具類型和具類型的 XML 來提供預設值，並將實體參考取代為其展開的形式。</span><span class="sxs-lookup"><span data-stu-id="2b99a-167">However, inline DTD can be used for both untyped and typed XML to supply default values and to replace entity references with their expanded form.</span></span>  
  
 <span data-ttu-id="2b99a-168">您可以用協力廠商工具將 DTD 轉換成 XML 結構描述文件，並將 XML 結構描述載入資料庫中。</span><span class="sxs-lookup"><span data-stu-id="2b99a-168">You can convert DTDs to XML schema documents by using third-party tools, and load the XML schemas into the database.</span></span>  
  
## <a name="upgrading-typed-xml-from-sql-server-2005"></a><span data-ttu-id="2b99a-169">從 SQL Server 2005 升級具類型的 XML</span><span class="sxs-lookup"><span data-stu-id="2b99a-169">Upgrading Typed XML from SQL Server 2005</span></span>  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="2b99a-170">對於 XML 結構描述支援做了幾項擴充，其中包括支援 Lax 驗證，改進 **xs:date**、 **xs:time** 和 **xs:dateTime** 執行個體資料的處理，並加入了清單和聯集類型的支援。</span><span class="sxs-lookup"><span data-stu-id="2b99a-170">made several extensions to the XML Schema support, including support for lax validation, improved handling of **xs:date**, **xs:time** and **xs:dateTime** instance data, and added support for list and union types.</span></span> <span data-ttu-id="2b99a-171">在大多數情況下，這些變更並不會影響升級的使用體驗。</span><span class="sxs-lookup"><span data-stu-id="2b99a-171">In most cases the changes do not affect the upgrade experience.</span></span> <span data-ttu-id="2b99a-172">但是，如果您在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中使用允許 **xs:date**、 **xs:time**或 **xs:dateTime** 類型 (或任何子類型) 值的 XML 結構描述集合，則當您將 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 資料庫附加到更新版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]時，會進行下列升級步驟：</span><span class="sxs-lookup"><span data-stu-id="2b99a-172">However if you used an XML Schema collection in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] that allowed values of type **xs:date**, **xs:time**, or **xs:dateTime** (or any subtype) then the following upgrade steps occur when you attach your [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] database to a later version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
1.  <span data-ttu-id="2b99a-173">對於每一個 XML 資料行而言，如果它在 XML 結構描述集合中具類型 (該集合包含的元素或屬性具有 **xs:anyType**、 **xs:anySimpleType**、 **xs:date** 類型或它的任何子類型、 **xs:time** 或它的任何子類型或是 **xs:dateTime** 或它的任何子類型)，或是為包含這些類型之任何一項的聯集或清單類型時，會發生下列情況：</span><span class="sxs-lookup"><span data-stu-id="2b99a-173">For every XML column, that is typed with an XML Schema Collection that contains elements or attributes that are typed as either **xs:anyType**, **xs:anySimpleType**, **xs:date** or any of its subtypes, **xs:time** or any subtype thereof, or **xs:dateTime** or any of its subtypes, or are union or list types containing any of these types the following occurs:</span></span>  
  
    1.  <span data-ttu-id="2b99a-174">資料行上的所有 XML 索引都將會停用。</span><span class="sxs-lookup"><span data-stu-id="2b99a-174">All XML indices on the column will be disabled.</span></span>  
  
    2.  <span data-ttu-id="2b99a-175">所有的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 值都將會繼續以 Z 時區來表示，因為這些值已經正規化成 Z 時區。</span><span class="sxs-lookup"><span data-stu-id="2b99a-175">All [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] values will continue to be represented in the Z timezone, because they have been normalized to the Z timezone.</span></span>  
  
    3.  <span data-ttu-id="2b99a-176">在下列情況下，任何小於 1 年 1 月 1 日的 **xs:date** 或 **xs:dateTime** 值都會導致發生執行階段錯誤：當重建索引時，或是針對包含該值的 XML 資料類型執行 XQuery 或 XML-DML 陳述式時。</span><span class="sxs-lookup"><span data-stu-id="2b99a-176">Any **xs:date** or **xs:dateTime** values that are smaller than January 1st of year 1 will lead to a runtime error when the index gets rebuild or an XQuery or XML-DML statements gets executed against the XML data type containing that value.</span></span>  
  
2.  <span data-ttu-id="2b99a-177">**xs:date** 或 **xs:dateTime** Facet 中的任何負數年份或是 XML 結構描述集合中的預設值，將會自動更新為基底 **xs:date** 或 **xs:dateTime** 類型所允許的最小值 (例如 **xs:dateTime**的 0001-01-01T00:00:00.0000000Z)。</span><span class="sxs-lookup"><span data-stu-id="2b99a-177">Any negative years in **xs:date** or **xs:dateTime** facets or default values in an XML Schema collection will automatically be updated to the smallest value allowed by the base **xs:date** or **xs:dateTime** type (e.g., 0001-01-01T00:00:00.0000000Z for **xs:dateTime**).</span></span>  
  
 <span data-ttu-id="2b99a-178">請注意，您仍然可以使用簡單 SQL SELECT 陳述式來擷取整個 XML 資料類型，即使它包含負數年份。</span><span class="sxs-lookup"><span data-stu-id="2b99a-178">Note that you can still use a simple SQL select statement to retrieve the whole XML data type, even if it contains negative years.</span></span> <span data-ttu-id="2b99a-179">建議您使用新支援範圍中的年份來取代負數年份，或是將元素或屬性的類型變更為 **xs:string**。</span><span class="sxs-lookup"><span data-stu-id="2b99a-179">It is recommended that you replace negative years with a year within the newly supported range or change the type of the element or attribute to **xs:string**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b99a-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b99a-180">See Also</span></span>  
 <span data-ttu-id="2b99a-181">[建立 XML 資料的執行個體](create-instances-of-xml-data.md) </span><span class="sxs-lookup"><span data-stu-id="2b99a-181">[Create Instances of XML Data](create-instances-of-xml-data.md) </span></span>  
 <span data-ttu-id="2b99a-182">[xml 資料類型方法](/sql/t-sql/xml/xml-data-type-methods) </span><span class="sxs-lookup"><span data-stu-id="2b99a-182">[xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) </span></span>  
 <span data-ttu-id="2b99a-183">[XML 資料修改語言 &#40;XML DML&#41;](/sql/t-sql/xml/xml-data-modification-language-xml-dml) </span><span class="sxs-lookup"><span data-stu-id="2b99a-183">[XML Data Modification Language &#40;XML DML&#41;](/sql/t-sql/xml/xml-data-modification-language-xml-dml) </span></span>  
 [<span data-ttu-id="2b99a-184">XML 資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2b99a-184">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
