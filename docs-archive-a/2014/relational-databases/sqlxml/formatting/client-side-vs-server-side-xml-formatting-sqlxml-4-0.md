---
title: 用戶端與伺服器端 XML 格式設定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- NESTED mode
- FOR XML clause, formatting
- client-side XML formatting
- server-side XPath
- server-side XML formatting
- AUTO mode
- client-side XPath
ms.assetid: f807ab7a-c5f8-4e61-9b00-23aebfabc47e
author: rothja
ms.author: jroth
ms.openlocfilehash: fa155fc6d346cb90de54e5599aca1c296623faa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597713"
---
# <a name="client-side-vs-server-side-xml-formatting-sqlxml-40"></a><span data-ttu-id="6258a-102">用戶端和伺服器端的 XML 格式化 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="6258a-102">Client-side vs. Server-side XML Formatting (SQLXML 4.0)</span></span>
  <span data-ttu-id="6258a-103">本主題描述 SQLXML 中用戶端與伺服器端 XML 格式化之間的一般差異。</span><span class="sxs-lookup"><span data-stu-id="6258a-103">This topic describes the general differences between client-side and server-side XML formatting in SQLXML.</span></span>  
  
## <a name="multiple-rowset-queries-not-supported-in-client-side-formatting"></a><span data-ttu-id="6258a-104">用戶端格式中不支援多個資料列集查詢</span><span class="sxs-lookup"><span data-stu-id="6258a-104">Multiple Rowset Queries Not Supported in Client-side Formatting</span></span>  
 <span data-ttu-id="6258a-105">當您使用用戶端 XML 格式化時，不支援會產生多個資料列集的查詢。</span><span class="sxs-lookup"><span data-stu-id="6258a-105">Queries that generate multiple rowsets are not supported when you use client-side XML formatting.</span></span> <span data-ttu-id="6258a-106">例如，假設您有一個虛擬目錄，您已在其中指定用戶端格式。</span><span class="sxs-lookup"><span data-stu-id="6258a-106">For example, assume you have a virtual directory in which you have client-side formatting specified.</span></span> <span data-ttu-id="6258a-107">請考慮這個範例範本，其中在區塊中有兩個 SELECT 語句 **\<sql:query>** ：</span><span class="sxs-lookup"><span data-stu-id="6258a-107">Consider this sample template, which has two SELECT statements in a **\<sql:query>** block:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
     SELECT FirstName FROM Person.Contact FOR XML Nested;   
     SELECT LastName FROM Person.Contact FOR XML Nested    
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="6258a-108">您可以在應用程式的程式碼中執行這個範本，而且會傳回錯誤，因為用戶端 XML 格式化不支援多個資料列集的格式。</span><span class="sxs-lookup"><span data-stu-id="6258a-108">You can execute this template in application code and an error is returned, because client-side XML formatting does not support formatting of multiple rowsets.</span></span> <span data-ttu-id="6258a-109">如果您在兩個不同的區塊中指定查詢 **\<sql:query>** ，將會得到所需的結果。</span><span class="sxs-lookup"><span data-stu-id="6258a-109">If you specify the queries in two separate **\<sql:query>** blocks, you will get the desired results.</span></span>  
  
## <a name="timestamp-maps-differently-in-client--vs-server-side-formatting"></a><span data-ttu-id="6258a-110">時間戳記在用戶端與伺服器端格式中的對應不同</span><span class="sxs-lookup"><span data-stu-id="6258a-110">timestamp Maps Differently in Client- vs. Server-side Formatting</span></span>  
 <span data-ttu-id="6258a-111">在伺服器端 XML 格式化中，`timestamp` 類型的資料庫資料行會對應到 i8 XDR 類型 (在查詢中指定 XMLDATA 選項時)。</span><span class="sxs-lookup"><span data-stu-id="6258a-111">In server-side XML formatting, the database column of `timestamp` type maps to the i8 XDR type (when the XMLDATA option is specified in the query).</span></span>  
  
 <span data-ttu-id="6258a-112">在用戶端 XML 格式化中，`timestamp` 類型的資料庫資料行會對應到 `uri` 或 `bin.base64` XDR 類型 (取決於查詢中是否指定二進位 base64 選項而定)。</span><span class="sxs-lookup"><span data-stu-id="6258a-112">In client-side XML formatting, the database column of `timestamp` type maps to either the `uri` or the `bin.base64` XDR type (depending on whether the binary base64 option is specified in the query).</span></span> <span data-ttu-id="6258a-113">`bin.base64`如果您使用 updategram 和 bulkload 功能，XDR 型別會很有用，因為這個型別會轉換成 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `timestamp` 型別。</span><span class="sxs-lookup"><span data-stu-id="6258a-113">The `bin.base64` XDR type is useful if you use the updategram and bulkload features, because this type is converted to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `timestamp` type.</span></span> <span data-ttu-id="6258a-114">如此一來，插入、更新或刪除作業都會成功。</span><span class="sxs-lookup"><span data-stu-id="6258a-114">This way, the insert, update, or delete operation succeeds.</span></span>  
  
## <a name="deep-variants-are-used-in-server-side-formatting"></a><span data-ttu-id="6258a-115">伺服器端格式中會使用深入的 VARIANT</span><span class="sxs-lookup"><span data-stu-id="6258a-115">Deep VARIANTs Are Used in Server-side Formatting</span></span>  
 <span data-ttu-id="6258a-116">在伺服器端 XML 格式化中，會使用深入類型的 VARIANT 類型。</span><span class="sxs-lookup"><span data-stu-id="6258a-116">In server-side XML formatting, the deep types of a VARIANT type are used.</span></span> <span data-ttu-id="6258a-117">如果您使用用戶端 XML 格式化，Variant 會轉換成 Unicode 字串，而且不會使用 VARIANT 的子類型。</span><span class="sxs-lookup"><span data-stu-id="6258a-117">If you use client-side XML formatting, the variants are converted to Unicode string, and the subtypes of VARIANT are not used.</span></span>  
  
## <a name="nested-mode-vs-auto-mode"></a><span data-ttu-id="6258a-118">NESTED 模式與 AUTO 模式的比較</span><span class="sxs-lookup"><span data-stu-id="6258a-118">NESTED Mode vs. AUTO Mode</span></span>  
 <span data-ttu-id="6258a-119">用戶端 FOR XML 的 NESTED 模式類似於伺服器端 FOR XML 的 AUTO 模式，但是以下情況除外：</span><span class="sxs-lookup"><span data-stu-id="6258a-119">The NESTED mode of the client-side FOR XML is similar to the AUTO mode of server-side FOR XML, with the following exceptions:</span></span>  
  
### <a name="when-you-query-views-using-auto-mode-on-the-server-side-the-view-name-is-returned-as-the-element-name-in-the-resulting-xml"></a><span data-ttu-id="6258a-120">當您在伺服器端上使用 AUTO 模式來查詢檢視表時，檢視表名稱會當做產生之 XML 中的元素名稱傳回。</span><span class="sxs-lookup"><span data-stu-id="6258a-120">When you query views using AUTO mode on the server-side, the view name is returned as the element name in the resulting XML.</span></span>  
 <span data-ttu-id="6258a-121">例如，假設下列視圖是在 AdventureWorksdatabase 中的 Person. Contact 資料表上建立的：</span><span class="sxs-lookup"><span data-stu-id="6258a-121">For example, assume that the following view is created on the Person.Contact table in the AdventureWorksdatabase:</span></span>  
  
```  
CREATE VIEW ContactView AS (SELECT ContactID as CID,  
                               FirstName  as FName,  
                               LastName  as LName  
                        FROM Person.Contact)  
```  
  
 <span data-ttu-id="6258a-122">下列範本會針對 ContactView 檢視表指定一個查詢，也會指定伺服器端 XML 格式化：</span><span class="sxs-lookup"><span data-stu-id="6258a-122">The following template specifies a query against the ContactView view, and also specifies server-side XML formatting:</span></span>  
  
```  
 <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="0">  
    SELECT *  
    FROM   ContactView  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="6258a-123">當您執行此範本時，將會傳回下列 XML </span><span class="sxs-lookup"><span data-stu-id="6258a-123">When you execute the template, the following XML is returned.</span></span> <span data-ttu-id="6258a-124"> (只會顯示部分結果。 ) 請注意，元素名稱是查詢執行時所依據的視圖名稱。</span><span class="sxs-lookup"><span data-stu-id="6258a-124">(Only partial results are shown.) Note that the element names are the names of the views against which the query is executed.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <ContactView CID="1" FName="Gustavo" LName="Achong" />   
  <ContactView CID="2" FName="Catherine" LName="Abel" />   
...  
</ROOT>  
```  
  
 <span data-ttu-id="6258a-125">當您使用對應的 NESTED 模式指定用戶端 XML 格式化時，基底資料表名稱會當做產生之 XML 中的元素名稱傳回。</span><span class="sxs-lookup"><span data-stu-id="6258a-125">When you specify client-side XML formatting by using the corresponding NESTED mode, the base table name(s) are returned as the element name(s) in the resulting XML.</span></span> <span data-ttu-id="6258a-126">例如，下列修訂的範本會執行相同的 SELECT 語句，但是 XML 格式會在用戶端上執行 (也就是，範本) 中的**用戶端 xml**會設定為 true：</span><span class="sxs-lookup"><span data-stu-id="6258a-126">For example, the following revised template executes the same SELECT statement, but the XML formatting is performed on the client-side (that is, **client-side-xml** is set to true in the template):</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    SELECT *  
    FROM   ContactView  
    FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="6258a-127">執行這個範本會產生以下 XML。</span><span class="sxs-lookup"><span data-stu-id="6258a-127">Executing this template produces the following XML.</span></span> <span data-ttu-id="6258a-128">請注意，此案例中的元素名稱是基底資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="6258a-128">Note that the element name is the base table name in this case.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact CID="1" FName="Gustavo" LName="Achong" />   
  <Person.Contact CID="2" FName="Catherine" LName="Abel" />   
...  
</ROOT>  
```  
  
### <a name="when-you-use-auto-mode-of-the-server-side-for-xml-the-table-aliases-specified-in-the-query-are-returned-as-element-names-in-the-resulting-xml"></a><span data-ttu-id="6258a-129">當您使用伺服器端 FOR XML 的 AUTO 模式時，查詢中所指定的資料表別名會當做產生之 XML 中的元素名稱傳回。</span><span class="sxs-lookup"><span data-stu-id="6258a-129">When you use AUTO mode of the server-side FOR XML, the table aliases specified in the query are returned as element names in the resulting XML.</span></span>  
 <span data-ttu-id="6258a-130">例如，假設有以下的範本：</span><span class="sxs-lookup"><span data-stu-id="6258a-130">For example, consider this template:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="0">  
    SELECT FirstName as fname,  
           LastName as lname  
    FROM   Person.Contact C  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="6258a-131">執行此範本會產生以下 XML：</span><span class="sxs-lookup"><span data-stu-id="6258a-131">Executing the template produces the following XML:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <C fname="Gustavo" lname="Achong" />   
  <C fname="Catherine" lname="Abel" />   
...  
</ROOT>   
```  
  
 <span data-ttu-id="6258a-132">當您使用用戶端 FOR XML 的 NESTED 模式時，資料表名稱會當做產生之 XML 中的元素名稱傳回 </span><span class="sxs-lookup"><span data-stu-id="6258a-132">When you use the NESTED mode of the client-side FOR XML, the table names are returned as element names in the resulting XML.</span></span> <span data-ttu-id="6258a-133">不會使用查詢中指定的 (資料表別名。 ) 例如，請考慮此範本：</span><span class="sxs-lookup"><span data-stu-id="6258a-133">(Table aliases that are specified in the query are not used.) For example, consider this template:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    SELECT FirstName as fname,  
           LastName as lname  
    FROM   Person.Contact C  
    FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="6258a-134">執行此範本會產生以下 XML：</span><span class="sxs-lookup"><span data-stu-id="6258a-134">Executing the template produces the following XML:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact fname="Gustavo" lname="Achong" />   
  <Person.Contact fname="Catherine" lname="Abel" />   
...  
</ROOT>  
```  
  
### <a name="if-you-have-a-query-that-returns-columns-as-dbobject-queries-you-cannot-use-aliases-for-these-columns"></a><span data-ttu-id="6258a-135">如果您的查詢將資料行當做 dbobject 查詢傳回，您將無法針對這些資料行使用別名。</span><span class="sxs-lookup"><span data-stu-id="6258a-135">If you have a query that returns columns as dbobject queries, you cannot use aliases for these columns.</span></span>  
 <span data-ttu-id="6258a-136">例如，假設有以下的範本，此範本所執行的查詢會傳回員工識別碼和相片。</span><span class="sxs-lookup"><span data-stu-id="6258a-136">For example, consider the following template, which executes a query that returns an employee ID and a photo.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<sql:query client-side-xml="1">  
   SELECT ProductPhotoID, LargePhoto as P  
   FROM   Production.ProductPhoto  
   WHERE  ProductPhotoID=5  
   FOR XML NESTED, elements  
</sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="6258a-137">執行這個範本會將 Photo 資料行當做 dbobject 查詢傳回。</span><span class="sxs-lookup"><span data-stu-id="6258a-137">Executing this template returns the Photo column as a dbobject query.</span></span> <span data-ttu-id="6258a-138">在此 dbobject 查詢中，`@P` 會參考不存在的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="6258a-138">In this dbobject query, `@P` refers to a column name that does not exist.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductPhoto>  
    <ProductPhotoID>5</ProductPhotoID>  
    <LargePhoto>dbobject/Production.ProductPhoto[@ProductPhotoID='5']/@P</LargePhoto>  
  </Production.ProductPhoto>  
</ROOT>  
```  
  
 <span data-ttu-id="6258a-139">如果在伺服器上完成 XML 格式設定 (**用戶端-XML = "0"**) ，則您可以針對傳回 dbobject 查詢的資料行使用別名，其中會 (傳回實際資料表和資料行名稱，即使您已) 指定別名也一樣。</span><span class="sxs-lookup"><span data-stu-id="6258a-139">If the XML formatting is done on the server (**client-side-xml="0"**), you can use the alias for the columns that return dbobject queries in which actual table and column names are returned (even if you have aliases specified).</span></span> <span data-ttu-id="6258a-140">例如，下列範本會執行查詢，並在伺服器上完成 XML 格式 (未指定**用戶端-xml**選項，而且未選取虛擬根) 的 [**在用戶端上執行**] 選項。</span><span class="sxs-lookup"><span data-stu-id="6258a-140">For example, the following template executes a query, and the XML formatting is done on the server (the **client-side-xml** option is not specified and the **Run On Client** option is not selected for the virtual root).</span></span> <span data-ttu-id="6258a-141">此查詢也會指定 AUTO 模式 (而非用戶端 NESTED 模式)。</span><span class="sxs-lookup"><span data-stu-id="6258a-141">The query also specifies AUTO mode (not the client-side NESTED mode).</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<sql:query   
   SELECT ProductPhotoID, LargePhoto as P  
   FROM   Production.ProductPhoto  
   WHERE  ProductPhotoID=5  
   FOR XML AUTO, elements  
</sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="6258a-142">當執行這個範本時，將會傳回下列 XML 文件 (請注意，LargePhoto 資料行的 dbobject 查詢中不會使用別名)。</span><span class="sxs-lookup"><span data-stu-id="6258a-142">When this template is executed, the following XML document is returned (note that aliases are not used in the dbobject query for the LargePhoto column):</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductPhoto>  
    <ProductPhotoID>5</ProductPhotoID>  
    <LargePhoto>dbobject/Production.ProductPhoto[@ProductPhotoID='5']/@LargePhoto</LargePhoto>  
  </Production.ProductPhoto>  
</ROOT>  
```  
  
### <a name="client-side-vs-server-side-xpath"></a><span data-ttu-id="6258a-143">用戶端和伺服器端的 XPath</span><span class="sxs-lookup"><span data-stu-id="6258a-143">Client-side vs. Server-side XPath</span></span>  
 <span data-ttu-id="6258a-144">用戶端 XPath 和伺服器端 XPath 的運作方式相同，但是有下列幾項差異：</span><span class="sxs-lookup"><span data-stu-id="6258a-144">Client-side XPath and server-side XPath work the same except for these differences:</span></span>  
  
-   <span data-ttu-id="6258a-145">當您使用用戶端 XPath 查詢時所套用的資料轉換與使用伺服器端 XPath 查詢時所套用的資料轉換不同。</span><span class="sxs-lookup"><span data-stu-id="6258a-145">The data conversions that are applied when you use client-side XPath queries are different from those that are applied when you use server-side XPath queries.</span></span> <span data-ttu-id="6258a-146">用戶端 XPath 會使用 CAST，而非 CONVERT 模式 126。</span><span class="sxs-lookup"><span data-stu-id="6258a-146">Client-side XPath uses CAST instead of CONVERT mode 126.</span></span>  
  
-   <span data-ttu-id="6258a-147">當您在範本中指定**用戶端-xml = "0"** (false) 時，您會要求伺服器端 xml 格式。</span><span class="sxs-lookup"><span data-stu-id="6258a-147">When you specify **client-side-xml="0"** (false) in a template, you are requesting server-side XML formatting.</span></span> <span data-ttu-id="6258a-148">因此，您無法指定 FOR XML NESTED，因為伺服器無法辨識 NESTED 選項。</span><span class="sxs-lookup"><span data-stu-id="6258a-148">Therefore, you cannot specify FOR XML NESTED because the server does not recognize the NESTED option.</span></span> <span data-ttu-id="6258a-149">這樣會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="6258a-149">This generates an error.</span></span> <span data-ttu-id="6258a-150">您必須使用伺服器可辨識的 AUTO、RAW 或 EXPLICIT 模式。</span><span class="sxs-lookup"><span data-stu-id="6258a-150">You must use the AUTO, RAW, or EXPLICIT modes, which the server does recognize.</span></span>  
  
-   <span data-ttu-id="6258a-151">當您在範本中指定**用戶端-xml = "1"** (true) 時，您會要求用戶端 xml 格式。</span><span class="sxs-lookup"><span data-stu-id="6258a-151">When you specify **client-side-xml="1"** (true) in a template, you are requesting client-side XML formatting.</span></span> <span data-ttu-id="6258a-152">在此情況下，您可以指定 FOR XML NESTED。</span><span class="sxs-lookup"><span data-stu-id="6258a-152">In this case, you can specify FOR XML NESTED.</span></span> <span data-ttu-id="6258a-153">如果您指定 FOR XML AUTO，則 XML 格式會出現在伺服器端，但在範本中指定**用戶端-XML = "1"** 。</span><span class="sxs-lookup"><span data-stu-id="6258a-153">If you specify FOR XML AUTO, the XML formatting occurs on the server side although **client-side-xml="1"** is specified in the template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6258a-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6258a-154">See Also</span></span>  
 <span data-ttu-id="6258a-155">[FOR XML 安全性考慮 &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="6258a-155">[FOR XML Security Considerations &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="6258a-156">[用戶端 XML 格式 &#40;SQLXML 4.0&#41;](client-side-xml-formatting-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="6258a-156">[Client-side XML Formatting &#40;SQLXML 4.0&#41;](client-side-xml-formatting-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="6258a-157">伺服器端 XML 格式 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="6258a-157">Server-side XML Formatting &#40;SQLXML 4.0&#41;</span></span>](server-side-xml-formatting-sqlxml-4-0.md)  
  
  
