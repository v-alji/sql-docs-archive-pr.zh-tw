---
title: 定義 XML 資料的序列化 | Microsoft 文件
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- entitization rules [XML in SQL Server]
- serialization
- reparsing serialized XML structures
- encoding [XML in SQL Server]
- XML [SQL Server], serialization
- xml data type [SQL Server], serialization
- typed XML
ms.assetid: 42b0b5a4-bdd6-4a60-b451-c87f14758d4b
author: rothja
ms.author: jroth
ms.openlocfilehash: df87dddd9fd4cf067125314c9d798eaa42523576
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606658"
---
# <a name="define-the-serialization-of-xml-data"></a><span data-ttu-id="8227b-102">定義 XML 資料的序列化</span><span class="sxs-lookup"><span data-stu-id="8227b-102">Define the Serialization of XML Data</span></span>
  <span data-ttu-id="8227b-103">將 XML 資料類型明確或隱含轉換成 SQL 字串或二進位類型時，會根據本主題中所列的規則來序列化 XML 資料類型的內容。</span><span class="sxs-lookup"><span data-stu-id="8227b-103">When casting the xml data type explicitly or implicitly to a SQL string or binary type, the content of the xml data type will be serialized according to the rules outlined in this topic.</span></span>  
  
## <a name="serialization-encoding"></a><span data-ttu-id="8227b-104">序列化編碼</span><span class="sxs-lookup"><span data-stu-id="8227b-104">Serialization Encoding</span></span>  
 <span data-ttu-id="8227b-105">如果 SQL 目標類型是 VARBINARY，其結果會以 UTF-16 序列化，前面有 UTF-16 位元組順序標示，但沒有 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="8227b-105">If the SQL target type is VARBINARY, the result is serialized in UTF-16 with a UTF-16-byte order mark in front, but without an XML declaration.</span></span> <span data-ttu-id="8227b-106">如果目標類型太小，則會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="8227b-106">If the target type is too small, an error is raised.</span></span>  
  
 <span data-ttu-id="8227b-107">例如：</span><span class="sxs-lookup"><span data-stu-id="8227b-107">For example:</span></span>  
  
```sql
select CAST(CAST(N'<Δ/>' as XML) as VARBINARY(MAX))  
```  
  
 <span data-ttu-id="8227b-108">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="8227b-108">This is the result:</span></span>  
  
```  
0xFFFE3C0094032F003E00  
```  
  
 <span data-ttu-id="8227b-109">如果 SQL 目標類型是 NVARCHAR 或 NCHAR，則結果會以 UTF-16 序列化，但前面沒有位元組順序標示，也沒有 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="8227b-109">If the SQL target type is NVARCHAR or NCHAR, the result is serialized in UTF-16 without the byte order mark in front and without an XML declaration.</span></span> <span data-ttu-id="8227b-110">如果目標類型太小，則會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="8227b-110">If the target type is too small, an error is raised.</span></span>  
  
 <span data-ttu-id="8227b-111">例如：</span><span class="sxs-lookup"><span data-stu-id="8227b-111">For example:</span></span>  
  
```sql
select CAST(CAST(N'<Δ/>' as XML) as NVARCHAR(MAX))  
```  
  
 <span data-ttu-id="8227b-112">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="8227b-112">This is the result:</span></span>  
  
```  
<Δ/>  
```  
  
 <span data-ttu-id="8227b-113">如果 SQL 目標類型是 VARCHAR 或 NCHAR，其結果會以對應於資料庫定序字碼頁的編碼序列化，但沒有位元組順序標示或 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="8227b-113">If the SQL target type is VARCHAR or NCHAR, the result is serialized in the encoding that corresponds to the database's collation code page without a byte order mark or XML declaration.</span></span> <span data-ttu-id="8227b-114">如果目標類型太小，或值無法對應至目標定序字碼頁，則會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="8227b-114">If the target type is too small or the value cannot be mapped to the target collation code page, an error is raised.</span></span>  
  
 <span data-ttu-id="8227b-115">例如：</span><span class="sxs-lookup"><span data-stu-id="8227b-115">For example:</span></span>  
  
```sql
select CAST(CAST(N'<Δ/>' as XML) as VARCHAR(MAX))  
```  
  
 <span data-ttu-id="8227b-116">如果目前定序的字碼頁無法表示 Unicode 字元 & # x10300;，這可能會導致錯誤，否則會以特定的編碼方式來表示它。</span><span class="sxs-lookup"><span data-stu-id="8227b-116">This may result in an error, if the current collation's code page cannot represent the Unicode character &#x10300;, or it will represent it in the specific encoding.</span></span>  
  
 <span data-ttu-id="8227b-117">將 XML 結果傳回至用戶端時，資料是以 UTF-16 編碼格式傳送。</span><span class="sxs-lookup"><span data-stu-id="8227b-117">When returning XML results to the client side, the data will be sent in UTF-16 encoding.</span></span> <span data-ttu-id="8227b-118">接著，用戶端提供者會根據其 API 規則來公開此資料。</span><span class="sxs-lookup"><span data-stu-id="8227b-118">The client-side provider will then expose the data according to its API rules.</span></span>  
  
## <a name="serialization-of-the-xml-structures"></a><span data-ttu-id="8227b-119">XML 結構的序列化</span><span class="sxs-lookup"><span data-stu-id="8227b-119">Serialization of the XML Structures</span></span>  
 <span data-ttu-id="8227b-120">**xml** 資料類型的內容以一般方式序列化。</span><span class="sxs-lookup"><span data-stu-id="8227b-120">The content of an **xml** data type is serialized in the usual way.</span></span> <span data-ttu-id="8227b-121">特別是，元素節點是對應到元素標示，而文字節點則對應到文字內容。</span><span class="sxs-lookup"><span data-stu-id="8227b-121">Specifically, element nodes are mapped to element markup, and text nodes are mapped to text content.</span></span> <span data-ttu-id="8227b-122">不過，下列章節將描述字元在何種情況下實體化，以及具類型的不可部份完成值如何序列化。</span><span class="sxs-lookup"><span data-stu-id="8227b-122">However, the circumstances under which characters are entitized and how typed atomic values are serialized are described in the following sections.</span></span>  
  
## <a name="entitization-of-xml-characters-during-serialization"></a><span data-ttu-id="8227b-123">XML 字元在序列化期間的實體化</span><span class="sxs-lookup"><span data-stu-id="8227b-123">Entitization of XML Characters During Serialization</span></span>  
 <span data-ttu-id="8227b-124">每一個已序列化的 XML 結構應該能夠加以重新剖析。</span><span class="sxs-lookup"><span data-stu-id="8227b-124">Every serialized XML structure should be capable of being reparsed.</span></span> <span data-ttu-id="8227b-125">因此，有些字元必須以實體化方式來序列化，以透過 XML 剖析器的正規化階段保留字元的反覆存取功能。</span><span class="sxs-lookup"><span data-stu-id="8227b-125">Therefore, some characters have to be serialized in an entitized way to preserve the round-trip capability of the characters through the XML parser's normalization phase .</span></span> <span data-ttu-id="8227b-126">不過，有些字元必須實體化，使文件能夠有完善的格式，以便加以剖析。</span><span class="sxs-lookup"><span data-stu-id="8227b-126">However, some characters have to be entitized so that the document is well-formed and, therefore, able to be parsed.</span></span> <span data-ttu-id="8227b-127">以下是在序列化期間所套用的實體化規則：</span><span class="sxs-lookup"><span data-stu-id="8227b-127">Following are the entitization rules that apply during serialization:</span></span>  
  
-   <span data-ttu-id="8227b-128">若字元 &、\<, and > 是出現在屬性值或元素內容中，則一律會分別實體化成 &amp;、&lt; 和 &gt;。</span><span class="sxs-lookup"><span data-stu-id="8227b-128">The characters &, \<, and > are always entitized to &amp;, &lt;, and &gt; respectively, if they occur inside an attribute value or element content.</span></span>  
  
-   <span data-ttu-id="8227b-129">因為 SQL Server 使用引號 (U+0022) 來括住屬性值，所以屬性值中的引號會實體化成 &quot;。</span><span class="sxs-lookup"><span data-stu-id="8227b-129">Because SQL Server uses a quotation mark (U+0022) for enclosing attribute values, the quotation mark in attribute values is entitized as &quot;.</span></span>  
  
-   <span data-ttu-id="8227b-130">只在伺服器上進行轉換時，Surrogate 字組會實體化成單一數字字元參考。</span><span class="sxs-lookup"><span data-stu-id="8227b-130">A surrogate pair is entitized as a single numeric character reference, when casting on the server only.</span></span> <span data-ttu-id="8227b-131">例如，Surrogate 字組 U+D800 U+DF00 會實體化成數字字元參考 &\#x00010300;。</span><span class="sxs-lookup"><span data-stu-id="8227b-131">For example the surrogate pair U+D800 U+DF00 is entitized to the numeric character reference &\#x00010300;.</span></span>  
  
-   <span data-ttu-id="8227b-132">為避免在剖析期間將定位字元 (U+0009) 和換行符號 (LF、U+000A) 正規化，已在屬性值內分別實體化成其數字字元參考 &\#x9; 和 &\#xA;。</span><span class="sxs-lookup"><span data-stu-id="8227b-132">To protect a TAB (U+0009) and a linefeed (LF, U+000A) from being normalized during parsing, they are entitized to their numeric character references &\#x9; and &\#xA; respectively, inside attribute values.</span></span>  
  
-   <span data-ttu-id="8227b-133">為避免在剖析期間將歸位字元 (CR、U+000D) 正規化，已在屬性值和元素內容內實體化成其數字字元參考 &\#xD;。</span><span class="sxs-lookup"><span data-stu-id="8227b-133">To prevent a carriage return (CR, U+000D) from being normalized during parsing, it is entitized to its numeric character reference, &\#xD; inside both attribute values and element content.</span></span>  
  
-   <span data-ttu-id="8227b-134">為了保護只包含空格的文字節點，其中一個空格字元 (通常是最後一個) 會實體化為其數字字元參考。</span><span class="sxs-lookup"><span data-stu-id="8227b-134">To protect text nodes that only contain white space, one of the white-space characters, generally the last one, is entitized as its numeric character reference.</span></span> <span data-ttu-id="8227b-135">如此一來，不論剖析期間的空格處理設定為何，重新剖析作業都會保留空格文字節點。</span><span class="sxs-lookup"><span data-stu-id="8227b-135">In this way, reparsing preserves the white-space text node, regardless of the setting of the white-space handling during parsing.</span></span>  
  
 <span data-ttu-id="8227b-136">例如：</span><span class="sxs-lookup"><span data-stu-id="8227b-136">For example:</span></span>  
  
```sql
declare @u NVARCHAR(50)  
set @u = N'<a a="  
    '+NCHAR(0xD800)+NCHAR(0xDF00)+N'>">   '+NCHAR(0xA)+N'</a>'  
select CAST(CONVERT(XML,@u,1) as NVARCHAR(50))  
```  
  
 <span data-ttu-id="8227b-137">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="8227b-137">This is the result:</span></span>  
  
```  
<a a="  
    𐌀>">     
</a>  
```  
  
 <span data-ttu-id="8227b-138">如果您不想套用最後一個空格的保護規則，您可以在從 **XML** 轉換成字串或二進位類型時，使用明確的 CONVERT 選項 1。</span><span class="sxs-lookup"><span data-stu-id="8227b-138">If you do not want to apply the last white-space protection rule, you can use the explicit CONVERT option 1 when casting from **xml** to a string or binary type.</span></span> <span data-ttu-id="8227b-139">例如，若要避免實體化，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8227b-139">For example, to avoid entitization, you can do the following:</span></span>  
  
```sql
select CONVERT(NVARCHAR(50), CONVERT(XML, '<a>   </a>', 1), 1)  
```  
  
 <span data-ttu-id="8227b-140">請注意， [query() 方法 (XML 資料類型)](/sql/t-sql/xml/query-method-xml-data-type) 會產生 XML 資料類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="8227b-140">Note that, the [query() Method (xml Data Type)](/sql/t-sql/xml/query-method-xml-data-type) results in an xml data type instance.</span></span> <span data-ttu-id="8227b-141">因此，轉換成字串或二進位類型的 **query()** 方法的任何結果，將根據前述規則而實體化。</span><span class="sxs-lookup"><span data-stu-id="8227b-141">Therefore, any result of the **query()** method that is cast to a string or binary type is entitized according to the previously described rules.</span></span> <span data-ttu-id="8227b-142">如果您要取得未實體化的字串值，請改用 [value() 方法 (XML 資料類型)](/sql/t-sql/xml/value-method-xml-data-type) 。</span><span class="sxs-lookup"><span data-stu-id="8227b-142">If you want to obtain the string values that are not entitized, you should use the [value() Method (xml Data Type)](/sql/t-sql/xml/value-method-xml-data-type) instead.</span></span> <span data-ttu-id="8227b-143">以下是使用 **query()** 方法的範例：</span><span class="sxs-lookup"><span data-stu-id="8227b-143">Following is an example of using the **query()** method:</span></span>  
  
```sql
declare @x xml  
set @x = N'<a>This example contains an entitized char: <.</a>'  
select @x.query('/a/text()')  
```  
  
 <span data-ttu-id="8227b-144">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="8227b-144">This is the result:</span></span>  
  
```  
This example contains an entitized char: <.  
```  
  
 <span data-ttu-id="8227b-145">以下是使用 **value()** 方法的範例：</span><span class="sxs-lookup"><span data-stu-id="8227b-145">Following is an example of using the **value()** method:</span></span>  
  
```sql
select @x.value('(/a/text())[1]', 'nvarchar(100)')  
```  
  
 <span data-ttu-id="8227b-146">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="8227b-146">This is the result:</span></span>  
  
```  
This example contains an entitized char: <.  
```  
  
## <a name="serializing-a-typed-xml-data-type"></a><span data-ttu-id="8227b-147">序列化 XML 類型的資料類型</span><span class="sxs-lookup"><span data-stu-id="8227b-147">Serializing a Typed xml Data Type</span></span>  
 <span data-ttu-id="8227b-148">具類型的 **xml** 資料類型執行個體根據其 XML 結構描述類型來包含具類型的值。</span><span class="sxs-lookup"><span data-stu-id="8227b-148">A typed **xml** data type instance contains values that are typed according to their XML schema types.</span></span> <span data-ttu-id="8227b-149">這些值根據其 XML 結構描述類型而序列化，並使用與 XQuery 轉換成 xs:string 時產生的相同格式。</span><span class="sxs-lookup"><span data-stu-id="8227b-149">These values are serialized according to their XML schema type in the same format as the XQuery cast to xs:string produces.</span></span> <span data-ttu-id="8227b-150">如需詳細資訊，請參閱 [XQuery 中的類型轉換規則](/sql/xquery/type-casting-rules-in-xquery)。</span><span class="sxs-lookup"><span data-stu-id="8227b-150">For more information, see [Type Casting Rules in XQuery](/sql/xquery/type-casting-rules-in-xquery).</span></span>  
  
 <span data-ttu-id="8227b-151">例如，xs:double 值 1.34e1 序列化為 13.4，如下列範例所顯示：</span><span class="sxs-lookup"><span data-stu-id="8227b-151">For example, the xs:double value 1.34e1 is serialized to 13.4 as shown in the following example:</span></span>  
  
```sql
declare @x xml  
set @x =''  
select CAST(@x.query('1.34e1') as nvarchar(50))  
```  
  
 <span data-ttu-id="8227b-152">這會傳回字串值 13.4。</span><span class="sxs-lookup"><span data-stu-id="8227b-152">This returns the string value 13.4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8227b-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8227b-153">See Also</span></span>  
 <span data-ttu-id="8227b-154">[XQuery 中的類型轉換規則](/sql/xquery/type-casting-rules-in-xquery) </span><span class="sxs-lookup"><span data-stu-id="8227b-154">[Type Casting Rules in XQuery](/sql/xquery/type-casting-rules-in-xquery) </span></span>  
 [<span data-ttu-id="8227b-155">CAST 和 CONVERT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8227b-155">CAST and CONVERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/cast-and-convert-transact-sql)  
  
  
