---
title: 批註式 XSD 架構簡介 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces [SQLXML], annotated XSD schemas
- mapping schema [SQLXML], about mapping schema
- views [SQLXML]
- valid XSD schemas [SQLXML]
- annotations [SQLXML]
- XSD schemas [SQLXML], creating XML views
- annotated XSD schemas, creating XML views
- minimum XSD schema
- annotated XSD schemas, examples
- XML views [SQLXML]
ms.assetid: 15282db1-65c4-43be-bdb7-e9ef49cb33a2
author: rothja
ms.author: jroth
ms.openlocfilehash: b91be71569daa9e5bf4143be9f652617ba7c5b01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597722"
---
# <a name="introduction-to-annotated-xsd-schemas-sqlxml-40"></a><span data-ttu-id="a1107-102">註解式 XSD 結構描述簡介 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="a1107-102">Introduction to Annotated XSD Schemas (SQLXML 4.0)</span></span>
  <span data-ttu-id="a1107-103">您可以使用 XML 結構描述定義 (XSD) 語言來建立關聯式資料的 XML 檢視。</span><span class="sxs-lookup"><span data-stu-id="a1107-103">You can create XML views of relational data by using the XML Schema Definition (XSD) language.</span></span> <span data-ttu-id="a1107-104">接著，您就可以使用 XML 路徑語言 (XPath) 查詢來查詢這些檢視。</span><span class="sxs-lookup"><span data-stu-id="a1107-104">These views can then be queried by using XML Path language (XPath) queries.</span></span> <span data-ttu-id="a1107-105">這類似於使用 CREATE VIEW 陳述式來建立檢視，然後針對檢視指定 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="a1107-105">This is similar to creating views by using CREATE VIEW statements and then specifying SQL queries against the view.</span></span>  
  
 <span data-ttu-id="a1107-106">XML 結構描述會描述 XML 文件的結構，而且也會描述文件中資料的各種條件約束。</span><span class="sxs-lookup"><span data-stu-id="a1107-106">An XML schema describes the structure of an XML document and also describes the various constraints on the data in the document.</span></span> <span data-ttu-id="a1107-107">針對結構描述指定 XPath 查詢時，傳回之 XML 文件的結構取決於執行 XPath 查詢所針對的結構描述。</span><span class="sxs-lookup"><span data-stu-id="a1107-107">When you specify XPath queries against the schema, the structure of the XML document returned is determined by the schema against which the XPath query is executed.</span></span>  
  
 <span data-ttu-id="a1107-108">在 XSD 架構中， **\<xsd:schema>** 元素會括住整個架構; 所有元素宣告都必須包含在 **\<xsd:schema>** 元素內。</span><span class="sxs-lookup"><span data-stu-id="a1107-108">In an XSD schema, the **\<xsd:schema>** element encloses the entire schema; all element declarations must be contained within the **\<xsd:schema>** element.</span></span> <span data-ttu-id="a1107-109">您可以描述定義架構所在之命名空間的屬性，以及在架構中用來做為元素屬性的命名空間 **\<xsd:schema>** 。</span><span class="sxs-lookup"><span data-stu-id="a1107-109">You can describe attributes that define the namespace in which the schema resides and the namespaces that are used in the schema as properties of the **\<xsd:schema>** element.</span></span>  
  
 <span data-ttu-id="a1107-110">有效的 XSD 架構必須包含定義如下的 **\<xsd:schema>** 元素：</span><span class="sxs-lookup"><span data-stu-id="a1107-110">A valid XSD schema must contain the **\<xsd:schema>** element defined as follows:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<!-- additional schema definitions here -->  
</xsd:schema>  
```  
  
 <span data-ttu-id="a1107-111">**\<xsd:schema>** 元素衍生自的 XML 架構命名空間規格 http://www.w3.org/2001/XMLSchema 。</span><span class="sxs-lookup"><span data-stu-id="a1107-111">The **\<xsd:schema>** element is derived from the XML Schema namespace specification at http://www.w3.org/2001/XMLSchema.</span></span>  
  
## <a name="annotations-to-the-xsd-schema"></a><span data-ttu-id="a1107-112">XSD 結構描述的註解</span><span class="sxs-lookup"><span data-stu-id="a1107-112">Annotations to the XSD Schema</span></span>  
 <span data-ttu-id="a1107-113">您可以使用 XSD 結構描述搭配描述資料庫對應的註解、查詢資料庫，並且以 XML 文件的格式傳回結果。</span><span class="sxs-lookup"><span data-stu-id="a1107-113">You can use an XSD schema with annotations that describe the mapping to a database, query the database, and return the results in the form of an XML document.</span></span> <span data-ttu-id="a1107-114">提供註解的目的是要將 XSD 結構描述對應至資料庫資料表和資料行。</span><span class="sxs-lookup"><span data-stu-id="a1107-114">Annotations are provided to map an XSD schema to database tables and columns.</span></span> <span data-ttu-id="a1107-115">您可以針對 XSD 結構描述所建立的 XML 檢視指定 XPath 查詢來查詢資料庫，並以 XML 的格式取得結果。</span><span class="sxs-lookup"><span data-stu-id="a1107-115">XPath queries can be specified against the XML view created by the XSD schema to query the database and obtain results as an XML.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1107-116">在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 中，XSD 結構描述語言支援 [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] 中註解式 XML-Data Reduced (XDR) 結構描述語言所導入的註解。</span><span class="sxs-lookup"><span data-stu-id="a1107-116">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0, the XSD schema language supports the annotations introduced with annotated XML-Data Reduced (XDR) schema language in [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="a1107-117">註解式 XDR 在 SQLXML 4.0 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="a1107-117">Annotated XDR is deprecated in SQLXML 4.0.</span></span>  
  
 <span data-ttu-id="a1107-118">在關聯式資料庫的內容中，將任意的 XSD 結構描述對應到關聯式存放區相當實用。</span><span class="sxs-lookup"><span data-stu-id="a1107-118">In the context of the relational database, it is useful to map the arbitrary XSD schema to a relational store.</span></span> <span data-ttu-id="a1107-119">封存的其中一種方式是為 XSD 結構描述註解。</span><span class="sxs-lookup"><span data-stu-id="a1107-119">One way to achieve this is to annotate the XSD schema.</span></span> <span data-ttu-id="a1107-120">具有批註的 XSD 架構稱為*對應架構*，它會提供有關如何將 XML 資料對應到關聯式存放區的資訊。</span><span class="sxs-lookup"><span data-stu-id="a1107-120">An XSD schema with the annotations is referred to as a *mapping schema*, which provides information pertaining to how XML data is to be mapped to the relational store.</span></span> <span data-ttu-id="a1107-121">實際上，對應結構描述就是關聯式資料的 XML 檢視。</span><span class="sxs-lookup"><span data-stu-id="a1107-121">A mapping schema is, in effect, an XML view of the relational data.</span></span> <span data-ttu-id="a1107-122">這些對應可用於擷取關聯式資料做為 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="a1107-122">These mappings can be used to retrieve relational data as an XML document.</span></span>  
  
## <a name="namespace-for-annotations"></a><span data-ttu-id="a1107-123">註解的命名空間</span><span class="sxs-lookup"><span data-stu-id="a1107-123">Namespace for Annotations</span></span>  
 <span data-ttu-id="a1107-124">在 XSD 架構中，批註是使用命名空間**urn：架構-microsoft-com：對應架構**來指定。</span><span class="sxs-lookup"><span data-stu-id="a1107-124">In an XSD schema, annotations are specified by using the namespace **urn:schemas-microsoft-com:mapping-schema**.</span></span> <span data-ttu-id="a1107-125">如下列範例所示，指定命名空間最簡單的方式，就是在標記中指定它 **\<xsd:schema>** 。</span><span class="sxs-lookup"><span data-stu-id="a1107-125">As shown in the following example, the easiest way to specify the namespace is to specify it in the **\<xsd:schema>** tag.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
...  
</xsd:schema>  
```  
  
 <span data-ttu-id="a1107-126">所使用的命名空間前置詞是任意的。</span><span class="sxs-lookup"><span data-stu-id="a1107-126">The namespace prefix that is used is arbitrary.</span></span> <span data-ttu-id="a1107-127">在此檔中，會使用**sql**前置詞來表示批註命名空間，並區別此命名空間與其他命名空間中的批註。</span><span class="sxs-lookup"><span data-stu-id="a1107-127">In this documentation, the **sql** prefix is used to denote the annotation namespace and to distinguish annotations in this namespace from those in other namespaces.</span></span>  
  
## <a name="example-of-an-annotated-xsd-schema"></a><span data-ttu-id="a1107-128">註解式 XSD 結構描述的範例</span><span class="sxs-lookup"><span data-stu-id="a1107-128">Example of an Annotated XSD Schema</span></span>  
 <span data-ttu-id="a1107-129">在下列範例中，XSD 架構是由元素所組成 **\<Person.Contact>** 。</span><span class="sxs-lookup"><span data-stu-id="a1107-129">In the following example, the XSD schema consists of an **\<Person.Contact>** element.</span></span> <span data-ttu-id="a1107-130">**\<Employee>** 元素具有**ContactID**屬性和 **\<FirstName>** 和 **\<LastName>** 子項目：</span><span class="sxs-lookup"><span data-stu-id="a1107-130">The **\<Employee>** element has a **ContactID** attribute and **\<FirstName>** and **\<LastName>** child elements:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <xsd:element name="Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"    
                     type="xsd:string" />   
        <xsd:element name="LName"  
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ConID" type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="a1107-131">然後，將註解加入至這個 XSD 結構描述，以便將其元素和屬性對應至資料庫資料表和資料行：</span><span class="sxs-lookup"><span data-stu-id="a1107-131">Annotations are added to this XSD schema to map its elements and attributes to the database tables and columns:</span></span>  
  
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
        <xsd:attribute name="ConID"   
                       sql:field="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="a1107-132">在對應架構中， **\<Contact>** 元素會使用批註對應至範例 AdventureWorks 資料庫中的 Person 資料表 `sql:relation` 。</span><span class="sxs-lookup"><span data-stu-id="a1107-132">In the mapping schema, the **\<Contact>** element is mapped to the Person.Contact table in the sample AdventureWorks database by using the `sql:relation` annotation.</span></span> <span data-ttu-id="a1107-133">ConID、FName 和 LName 屬性會使用 `sql:field` 註解來對應至 Person.Contact 資料表中的 ContactID、FirstName 和 LastName 資料行。</span><span class="sxs-lookup"><span data-stu-id="a1107-133">The attributes ConID, FName, and LName are mapped to the ContactID, FirstName, and LastName columns in the Person.Contact table by using the `sql:field` annotations.</span></span>  
  
 <span data-ttu-id="a1107-134">此註解式 XSD 結構描述會提供關聯式資料的 XML 檢視。</span><span class="sxs-lookup"><span data-stu-id="a1107-134">This annotated XSD schema provides the XML view of the relational data.</span></span> <span data-ttu-id="a1107-135">您可以使用 XPath 語言來查詢這個 XML 檢視。</span><span class="sxs-lookup"><span data-stu-id="a1107-135">This XML view can be queried using the XPath language.</span></span> <span data-ttu-id="a1107-136">XPath 查詢會傳回 XML 文件當做結果，而不是 SQL 查詢所傳回的資料列集。</span><span class="sxs-lookup"><span data-stu-id="a1107-136">An XPath query returns an XML document as a result, instead of the rowset that is returned by SQL queries.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1107-137">在對應結構描述中，指定的關聯式值 (例如，資料表名稱和資料行名稱) 是否區分大小寫會取決於 SQL Server 是否使用區分大小寫的定序設定。</span><span class="sxs-lookup"><span data-stu-id="a1107-137">In the mapping schema, case-sensitivity for the specified relational values (such as table name and column name) depends upon if SQL Server is using case-sensitive collation settings.</span></span> <span data-ttu-id="a1107-138">如需詳細資訊，請參閱 [Collation and Unicode Support](../../collations/collation-and-unicode-support.md)。</span><span class="sxs-lookup"><span data-stu-id="a1107-138">For more information, see [Collation and Unicode Support](../../collations/collation-and-unicode-support.md).</span></span>  
  
## <a name="other-resources"></a><span data-ttu-id="a1107-139">其他資源</span><span class="sxs-lookup"><span data-stu-id="a1107-139">Other Resources</span></span>  
 <span data-ttu-id="a1107-140">您可以在下列網站上找到有關 XML 結構描述定義語言 (XSD)、XML 路徑語言 (XPath) 和可延伸樣式表語言轉換 (XSLT) 的資訊：</span><span class="sxs-lookup"><span data-stu-id="a1107-140">You can find more information about XML Schema Definition language (XSD), XML Path language (XPath), and Extensible Stylesheet Language Transformations (XSLT) at the following Web sites:</span></span>  
  
-   <span data-ttu-id="a1107-141">XML 架構第0部分：入門、W3C 建議 (http://www.w3.org/TR/xmlschema-0/)</span><span class="sxs-lookup"><span data-stu-id="a1107-141">XML Schema Part 0: Primer, W3C Recommendation (http://www.w3.org/TR/xmlschema-0/)</span></span>  
  
-   <span data-ttu-id="a1107-142">XML 架構第1部分：結構、W3C 建議 (http://www.w3.org/TR/xmlschema-1/)</span><span class="sxs-lookup"><span data-stu-id="a1107-142">XML Schema Part 1: Structures, W3C Recommendation (http://www.w3.org/TR/xmlschema-1/)</span></span>  
  
-   <span data-ttu-id="a1107-143">XML 架構第2部分：資料類型、W3C 建議 (http://www.w3.org/TR/xmlschema-2/)</span><span class="sxs-lookup"><span data-stu-id="a1107-143">XML Schema Part 2:Datatypes, W3C Recommendation (http://www.w3.org/TR/xmlschema-2/)</span></span>  
  
-   <span data-ttu-id="a1107-144">XML 路徑語言 (XPath)  (http://www.w3.org/TR/xpath)</span><span class="sxs-lookup"><span data-stu-id="a1107-144">XML Path Language (XPath) (http://www.w3.org/TR/xpath)</span></span>  
  
-   <span data-ttu-id="a1107-145"> (XSLT) 的 XSL 轉換 (http://www.w3.org/TR/xslt)</span><span class="sxs-lookup"><span data-stu-id="a1107-145">XSL Transformations (XSLT) (http://www.w3.org/TR/xslt)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1107-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1107-146">See Also</span></span>  
 <span data-ttu-id="a1107-147">[&#40;SQLXML 4.0&#41;的批註式架構安全性考慮](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="a1107-147">[Annotated Schema Security Considerations &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="a1107-148">批註式 XDR 架構 &#40;在 SQLXML 4.0 中被取代&#41;</span><span class="sxs-lookup"><span data-stu-id="a1107-148">Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;</span></span>](annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)  
  
  
