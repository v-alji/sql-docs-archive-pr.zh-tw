---
title: XML 大量載入的指導方針和限制 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XML Bulk Load [SQLXML], about XML Bulk Load
- bulk load [SQLXML], about bulk load
ms.assetid: c5885d14-c7c1-47b3-a389-455e99a7ece1
author: rothja
ms.author: jroth
ms.openlocfilehash: 08c0020ac7b28702f5a573c6158ec9d50c735b2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597754"
---
# <a name="guidelines-and-limitations-of-xml-bulk-load-sqlxml-40"></a><span data-ttu-id="f1dd2-102">XML 大量載入的指導方針和限制 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="f1dd2-102">Guidelines and Limitations of XML Bulk Load (SQLXML 4.0)</span></span>
  <span data-ttu-id="f1dd2-103">當您使用 XML 大量載入時，應該先熟悉下列指導方針和限制：</span><span class="sxs-lookup"><span data-stu-id="f1dd2-103">When you use XML Bulk Load, you should be familiar with the following guidelines and limitations:</span></span>  
  
-   <span data-ttu-id="f1dd2-104">不支援內嵌結構描述。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-104">Inline schemas are not supported.</span></span>  
  
     <span data-ttu-id="f1dd2-105">如果您的 XML 來源文件中有一個內嵌結構描述，XML 大量載入會忽略該結構描述。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-105">If you have an inline schema in the source XML document, XML Bulk Load ignores that schema.</span></span> <span data-ttu-id="f1dd2-106">您會針對 XML 資料外部的 XML 大量載入，指定對應的結構描述。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-106">You specify the mapping schema for XML Bulk Load external to the XML data.</span></span> <span data-ttu-id="f1dd2-107">您不能使用**xmlns = "x:schema"** 屬性，在節點上指定對應架構。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-107">You cannot specify the mapping schema at a node by using the **xmlns="x:schema"** attribute.</span></span>  
  
-   <span data-ttu-id="f1dd2-108">XML 文件已確認格式正確，但尚未經過驗證。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-108">An XML document is checked for being well-formed, but it is not validated.</span></span>  
  
     <span data-ttu-id="f1dd2-109">XML 大量載入會檢查 XML 檔，以判斷它的格式是否正確，也就是確保 XML 符合全球資訊網協會的 XML 1.0 建議的語法需求。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-109">XML Bulk Load checks the XML document to determine whether it is well-formed-that is, to ensure that the XML conforms to the syntax requirements of the World Wide Web Consortium's XML 1.0 recommendation.</span></span> <span data-ttu-id="f1dd2-110">如果文件的格式不正確，XML 大量載入會取消處理並傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-110">If the document is not well-formed, XML Bulk Load cancels processing and returns an error.</span></span> <span data-ttu-id="f1dd2-111">唯一的例外是當文件為片段 (例如，文件沒有單一的根元素) 時，在此情況下，XML 大量載入將會載入文件。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-111">The only exception to this is when the document is a fragment (for example, the document has no single root element), in which case XML Bulk Load will load the document.</span></span>  
  
     <span data-ttu-id="f1dd2-112">XML 大量載入不會針對 XML 資料檔中定義或參考的任何 XML 資料或 DTD 結構描述驗證文件。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-112">XML Bulk Load does not validate the document with respect to any XML-Data or DTD schema that is defined or referenced within the XML data file.</span></span> <span data-ttu-id="f1dd2-113">此外，XML 大量載入不會根據提供的對應結構描述驗證 XML 資料檔。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-113">In addition, XML Bulk Load does not validate the XML data file against the mapping schema supplied.</span></span>  
  
-   <span data-ttu-id="f1dd2-114">系統會忽略任何 XML 初構資訊。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-114">Any XML prolog information is ignored.</span></span>  
  
     <span data-ttu-id="f1dd2-115">XML 大量載入會忽略 \<root> xml 檔中元素之前和之後的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-115">XML Bulk Load ignores all the information before and after the \<root> element in the XML document.</span></span> <span data-ttu-id="f1dd2-116">例如，XML 大量載入會忽略任何 XML 宣告、內部 DTD 定義、外部 DTD 參考、註解等等。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-116">For example, XML Bulk Load ignores any XML declarations, internal DTD definitions, external DTD references, comments, and so on.</span></span>  
  
-   <span data-ttu-id="f1dd2-117">如果您擁有的對應結構描述會定義兩個資料表之間 (例如 Customer 和 CustOrder 之間) 的主索引鍵/外部索引鍵關聯性，則必須先在結構描述中描述具有主索引鍵的資料表。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-117">If you have a mapping schema that defines a primary key/foreign key relationship between two tables (such as between Customer and CustOrder), the table with the primary key must be described first in the schema.</span></span> <span data-ttu-id="f1dd2-118">包含外部索引鍵資料行的資料表稍後必須出現在結構描述中。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-118">The table with the foreign key column must appear later in the schema.</span></span> <span data-ttu-id="f1dd2-119">這是因為在架構中識別資料表的順序，是用來將它們載入資料庫的順序。例如，下列 XDR 架構在 XML 大量載入中使用時會產生錯誤，因為元素會在專案 **\<Order>** 之前描述 **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-119">The reason for this is that the order in which the tables are identified in the schema is the order that is used to load them into the database.For example, the following XDR schema will produce an error when it is used in XML Bulk Load because the **\<Order>** element is described before the **\<Customer>** element.</span></span> <span data-ttu-id="f1dd2-120">在 CustOrder 中的 CustomerID 資料行是外部索引鍵資料行，它會參考在 Cust 資料表中的 CustomerID 主索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-120">The CustomerID column in CustOrder is a foreign key column that refers to the CustomerID primary key column in the Cust table.</span></span>  
  
    ```  
    <?xml version="1.0" ?>  
    <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
            xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
            xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
        <ElementType name="Order" sql:relation="CustOrder" >  
          <AttributeType name="OrderID" />  
          <AttributeType name="CustomerID" />  
          <attribute type="OrderID" />  
          <attribute type="CustomerID" />  
        </ElementType>  
  
       <ElementType name="CustomerID" dt:type="int" />  
       <ElementType name="CompanyName" dt:type="string" />  
       <ElementType name="City" dt:type="string" />  
  
       <ElementType name="root" sql:is-constant="1">  
          <element type="Customers" />  
       </ElementType>  
       <ElementType name="Customers" sql:relation="Cust"   
                         sql:overflow-field="OverflowColumn"  >  
          <element type="CustomerID" sql:field="CustomerID" />  
          <element type="CompanyName" sql:field="CompanyName" />  
          <element type="City" sql:field="City" />  
          <element type="Order" >   
               <sql:relationship  
                   key-relation="Cust"  
                    key="CustomerID"  
                    foreign-key="CustomerID"  
                    foreign-relation="CustOrder" />  
          </element>  
       </ElementType>  
    </Schema>  
    ```  
  
-   <span data-ttu-id="f1dd2-121">如果結構描述沒有使用 `sql:overflow-field` 註解指定溢位資料行，XML 大量載入會忽略顯示在 XML 文件中的任何資料，但是不會在對應結構描述中描述。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-121">If the schema does not specify overflow columns by using the `sql:overflow-field` annotation, XML Bulk Load ignores any data that is present in the XML document but is not described in the mapping schema.</span></span>  
  
     <span data-ttu-id="f1dd2-122">每當 XML 大量載入在 XML 資料流中碰到已知的標記時，會套用您所指定的對應結構描述。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-122">XML Bulk Load applies the mapping schema that you have specified whenever it encounters known tags in the XML data stream.</span></span> <span data-ttu-id="f1dd2-123">它會忽略顯示在 XML 文件中的資料，但是不會在結構描述中描述。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-123">It ignores data that is present in the XML document but is not described in the schema.</span></span> <span data-ttu-id="f1dd2-124">例如，假設您有一個描述元素的對應架構 **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-124">For example, assume you have a mapping schema that describes a **\<Customer>** element.</span></span> <span data-ttu-id="f1dd2-125">XML 資料檔案具有根標籤 **\<AllCustomers>** (，不會在括住所有元素的架構) 中加以描述 **\<Customer>** ：</span><span class="sxs-lookup"><span data-stu-id="f1dd2-125">The XML data file has an **\<AllCustomers>** root tag (which is not described in the schema) that encloses all the **\<Customer>** elements:</span></span>  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
      <Customer>...</Customer>  
       ...  
    </AllCustomers>  
    ```  
  
     <span data-ttu-id="f1dd2-126">在此情況下，XML 大量載入會忽略 **\<AllCustomers>** 元素，並在專案開始對應 **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-126">In this case, XML Bulk Load ignores the **\<AllCustomers>** element and begins mapping at the **\<Customer>** element.</span></span> <span data-ttu-id="f1dd2-127">XML 大量載入會忽略結構描述中沒有描述但是顯示在 XML 文件中的元素。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-127">XML Bulk Load ignores the elements that are not described in the schema but are present in the XML document.</span></span>  
  
     <span data-ttu-id="f1dd2-128">請考慮包含元素的另一個 XML 源資料檔案 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-128">Consider another XML source data file that contains **\<Order>** elements.</span></span> <span data-ttu-id="f1dd2-129">這些元素不會在對應的結構描述中描述：</span><span class="sxs-lookup"><span data-stu-id="f1dd2-129">These elements are not described in the mapping schema:</span></span>  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
        <Order> ... </Order>  
        <Order> ... </Order>  
         ...  
      <Customer>...</Customer>  
        <Order> ... </Order>  
        <Order> ... </Order>  
         ...  
      ...  
    </AllCustomers>  
    ```  
  
     <span data-ttu-id="f1dd2-130">XML 大量載入會忽略這些 **\<Order>** 元素。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-130">XML Bulk Load ignores these **\<Order>** elements.</span></span> <span data-ttu-id="f1dd2-131">但是，如果您在 `sql:overflow-field` 架構中使用批註來識別資料行做為溢位資料行，則 XML 大量載入會將所有未耗用的資料儲存在此資料行中。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-131">But if you use the `sql:overflow-field`annotation in the schema to identify a column as an overflow column, XML Bulk Load stores all unconsumed data in this column.</span></span>  
  
-   <span data-ttu-id="f1dd2-132">CDATA 區段和實體參考會在儲存在資料庫之前，先轉譯成其對等字串。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-132">CDATA sections and entity references are translated to their string equivalents before they are stored in the database.</span></span>  
  
     <span data-ttu-id="f1dd2-133">在此範例中，CDATA 區段會包裝元素的值 **\<City>** 。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-133">In this example, a CDATA section wraps the value for the **\<City>** element.</span></span> <span data-ttu-id="f1dd2-134">XML 大量載入會先將字串值 ( "NY" ) ，再將 **\<City>** 元素插入資料庫中。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-134">XML Bulk Load extracts the string value ("NY") before it inserts the **\<City>** element into the database.</span></span>  
  
    ```  
    <City><![CDATA[NY]]> </City>  
    ```  
  
     <span data-ttu-id="f1dd2-135">XML 大量載入不會保留實體參考。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-135">XML Bulk Load does not preserve entity references.</span></span>  
  
-   <span data-ttu-id="f1dd2-136">如果對應結構描述指定屬性的預設值，而且 XML 來源資料不包含該屬性，XML 大量載入會使用預設值。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-136">If the mapping schema specifies the default value for an attribute and the XML source data does not contain that attribute, XML Bulk Load uses the default value.</span></span>  
  
     <span data-ttu-id="f1dd2-137">下列範例 XDR 架構會將預設值指派給**雇用**項屬性：</span><span class="sxs-lookup"><span data-stu-id="f1dd2-137">The following sample XDR schema assigns a default value to the **HireDate** attribute:</span></span>  
  
    ```  
    <?xml version="1.0" ?>  
    <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
            xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
            xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
       <ElementType name="root" sql:is-constant="1">  
          <element type="Customers" />  
       </ElementType>  
  
       <ElementType name="Customers" sql:relation="Cust3" >  
          <AttributeType name="CustomerID" dt:type="int"  />  
          <AttributeType name="HireDate"  default="2000-01-01" />  
          <AttributeType name="Salary"   />  
  
          <attribute type="CustomerID" sql:field="CustomerID" />  
          <attribute type="HireDate"   sql:field="HireDate"  />  
          <attribute type="Salary"     sql:field="Salary"    />  
       </ElementType>  
    </Schema>  
    ```  
  
     <span data-ttu-id="f1dd2-138">在此 XML 資料中，第二個元素中遺漏了「**雇用**項」屬性 **\<Customers>** 。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-138">In this XML data, the **HireDate** attribute is missing from the second **\<Customers>** element.</span></span> <span data-ttu-id="f1dd2-139">當 XML 大量載入將第二個 **\<Customers>** 元素插入資料庫時，它會使用架構中指定的預設值。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-139">When XML Bulk Load inserts the second **\<Customers>** element into the database, it uses the default value that is specified in the schema.</span></span>  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1" HireDate="1999-01-01" Salary="10000" />  
      <Customers CustomerID="2" Salary="10000" />  
    </ROOT>  
    ```  
  
-   <span data-ttu-id="f1dd2-140">不支援 `sql:url-encode` 註解：</span><span class="sxs-lookup"><span data-stu-id="f1dd2-140">The `sql:url-encode` annotation is not supported:</span></span>  
  
     <span data-ttu-id="f1dd2-141">您無法在 XML 資料輸入中指定 URL，然後預期大量載入會從該位置讀取資料。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-141">You cannot specify a URL in the XML data input and expect Bulk Load to read data from that location.</span></span>  
  
     <span data-ttu-id="f1dd2-142">系統會建立在對應結構描述中所識別的資料表 (資料庫必須存在)。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-142">The tables that are identified in the mapping schema are created (the database must exist).</span></span> <span data-ttu-id="f1dd2-143">如果資料庫中已經有一或多個資料表存在，SGDropTables 屬性會決定是否要卸載並重新建立這些預先存在的資料表。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-143">If one or more of the tables already exists in the database, the SGDropTables property determines whether these preexisting tables are to be dropped and re-created.</span></span>  
  
-   <span data-ttu-id="f1dd2-144">如果您指定 SchemaGen 屬性 (例如，SchemaGen = true) ，則會建立對應架構中所識別的資料表。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-144">If you specify the SchemaGen property (for example, SchemaGen = true), the tables that are identified in the mapping schema are created.</span></span> <span data-ttu-id="f1dd2-145">但是，SchemaGen 不會建立任何條件約束 (例如，) 這些資料表的 PRIMARY KEY/FOREIGN KEY 條件約束，但有一個例外：如果在關聯性中組成主鍵的 XML 節點定義為具有識別碼的 XML 類型 (也就是 `type="xsd:ID"` 針對 XSD) 而且 SGUseID 屬性設定為 True （針對 SchemaGen），則不只是從識別碼類型節點建立的主鍵，而是從對應架構關聯性建立主鍵/外鍵關聯性。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-145">But SchemaGen does not create any constraints (such as the PRIMARY KEY/FOREIGN KEY constraints) on these tables with one exception: If the XML nodes that constitute the primary key in a relationship are defined as having an XML type of ID (that is, `type="xsd:ID"` for XSD) AND the SGUseID property is set to True for SchemaGen, then not only are primary keys created from the ID typed nodes, but primary key/foreign key relationships are created from mapping schema relationships.</span></span>  
  
-   <span data-ttu-id="f1dd2-146">SchemaGen 不會使用 XSD 架構 facet 和延伸模組來產生關聯式 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 架構。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-146">SchemaGen does not use XSD schema facets and extensions to generate the relational [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] schema.</span></span>  
  
-   <span data-ttu-id="f1dd2-147">如果您指定 SchemaGen 屬性 (例如，SchemaGen = true) 在大量載入上，則只會更新指定之共用名稱) 的資料表 (而不會更新。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-147">If you specify the SchemaGen property (for example, SchemaGen = true) on Bulk Load, only tables (and not views of shared name) that are specified are updated.</span></span>  
  
-   <span data-ttu-id="f1dd2-148">SchemaGen 只提供從批註式 XSD 產生關聯式架構的基本功能。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-148">SchemaGen only provides basic functionality for generating the relational schema from annotated XSD.</span></span> <span data-ttu-id="f1dd2-149">如果需要，使用者應該手動修改產生的資料表。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-149">The user should modify the generated tables manually, if needed.</span></span>  
  
-   <span data-ttu-id="f1dd2-150">當資料表之間存在多個關聯性時，SchemaGen 會嘗試建立單一關聯性，其中包含兩個數據表之間的所有相關索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-150">Where more than relationship exists between tables,SchemaGen tries to create a single relationship that includes all the keys involved between the two tables.</span></span> <span data-ttu-id="f1dd2-151">這個限制可能是 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 錯誤的原因。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-151">This limitation might be the cause of a [!INCLUDE[tsql](../../../includes/tsql-md.md)] error.</span></span>  
  
-   <span data-ttu-id="f1dd2-152">當您將 XML 資料大量載入資料庫時，在對應結構描述中至少要有一個對應到資料庫資料行的屬性或子元素。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-152">When you are bulk loading XML data into a database, there must be at least one attribute or child element in the mapping schema that is mapped to a database column.</span></span>  
  
-   <span data-ttu-id="f1dd2-153">如果您要使用 XML 大量載入來插入日期值，必須以 (-)CCYY-MM-DD((+-)TZ) 格式指定這些值。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-153">If you are inserting date values by using XML Bulk Load, the values must be specified in the (-)CCYY-MM-DD((+-)TZ) format.</span></span> <span data-ttu-id="f1dd2-154">這是用於日期的標準 XSD 格式。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-154">This is the standard XSD format for the date.</span></span>  
  
-   <span data-ttu-id="f1dd2-155">某些屬性旗標與其他屬性旗標不相容。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-155">Some property flags are not compatible with other property flags.</span></span> <span data-ttu-id="f1dd2-156">例如，大量載入不同時支援 `Ignoreduplicatekeys=true` 及 `Keepidentity=false`。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-156">For example, bulk load does not support `Ignoreduplicatekeys=true` together with `Keepidentity=false`.</span></span> <span data-ttu-id="f1dd2-157">`Keepidentity=false` 時，大量載入需要伺服器才能產生索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-157">When `Keepidentity=false`, bulk load expects the server to generate the key values.</span></span> <span data-ttu-id="f1dd2-158">資料表在索引鍵上應該要有 `IDENTITY` 條件約束。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-158">Tables should have an `IDENTITY` constraint on the key.</span></span> <span data-ttu-id="f1dd2-159">伺服器不會產生重複的索引鍵，這表示不需要將 `Ignoreduplicatekeys` 設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-159">The server will not generate duplicate keys, which means there is no need for `Ignoreduplicatekeys` to be set to `true`.</span></span> <span data-ttu-id="f1dd2-160">只有在下列兩種情況下才需要將 `Ignoreduplicatekeys` 設定為 `true`：從內送資料上傳主索引鍵值到具有資料列的資料表以及可能會發生主索引鍵值衝突時。</span><span class="sxs-lookup"><span data-stu-id="f1dd2-160">`Ignoreduplicatekeys` should be set to `true` only when uploading primary key values from the incoming data into a table that has rows and there is a potential for conflict of primary key values.</span></span>  
  
  
