---
title: FOR XML 子句的基本語法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- BINARY BASE64 directive
- ROOT directive
- FOR XML clause, BINARY BASE64 directive
- FOR XML clause, syntax
- FOR XML clause, ROOT directive
ms.assetid: df19ecbf-d28e-4e9c-aaa3-700f8bbd3be4
author: rothja
ms.author: jroth
ms.openlocfilehash: dc0410e7a54674673f64442d8a3cf9476d250033
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585193"
---
# <a name="basic-syntax-of-the-for-xml-clause"></a><span data-ttu-id="a2ff0-102">FOR XML 子句的基本語法</span><span class="sxs-lookup"><span data-stu-id="a2ff0-102">Basic Syntax of the FOR XML Clause</span></span>
  <span data-ttu-id="a2ff0-103">FOR XML 模式可以是 RAW、AUTO、EXPLICIT 或 PATH。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-103">The FOR XML mode can be RAW, AUTO, EXPLICIT, or PATH.</span></span> <span data-ttu-id="a2ff0-104">它可以決定產生 XML 的外觀。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-104">It determines the shape of the resulting XML.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a2ff0-105">FOR XML 選項的 XMLDATA 指示詞已被取代。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-105">The XMLDATA directive to the FOR XML option is deprecated.</span></span> <span data-ttu-id="a2ff0-106">在 RAW 和 AUTO 模式的情況下，請使用 XSD 產生。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-106">Use XSD generation in the case of RAW and AUTO modes.</span></span> <span data-ttu-id="a2ff0-107">EXPLICT 模式中沒有 XMLDATA 指示詞的替代項目。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-107">There is no replacement for the XMLDATA directive in EXPLICT mode.</span></span> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="a2ff0-108">以下是[FOR 子句 (transact-sql) ](/sql/t-sql/queries/select-for-clause-transact-sql)中所述的基本語法：</span><span class="sxs-lookup"><span data-stu-id="a2ff0-108">Following is the basic syntax that is described in [FOR Clause (Transact-SQL)](/sql/t-sql/queries/select-for-clause-transact-sql):</span></span>  
  
```  
[ FOR { BROWSE | <XML> } ]  
<XML> ::=  
XML   
    {   
      { RAW [ ('ElementName') ] | AUTO }   
        [   
           <CommonDirectives>   
           [ , { XMLDATA | XMLSCHEMA [ ('TargetNameSpaceURI') ]} ]   
           [ , ELEMENTS [ XSINIL | ABSENT ]   
        ]  
      | EXPLICIT   
        [   
           <CommonDirectives>   
           [ , XMLDATA ]   
        ]  
      | PATH [ ('ElementName') ]   
        [   
           <CommonDirectives>   
           [ , ELEMENTS [ XSINIL | ABSENT ] ]  
        ]  
     }   
  
 <CommonDirectives> ::=   
   [ , BINARY BASE64 ]  
   [ , TYPE ]  
   [ , ROOT [ ('RootName') ] ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a2ff0-109">引數</span><span class="sxs-lookup"><span data-stu-id="a2ff0-109">Arguments</span></span>  
 <span data-ttu-id="a2ff0-110">RAW[('*ElementName*')]</span><span class="sxs-lookup"><span data-stu-id="a2ff0-110">RAW[('*ElementName*')]</span></span>  
 <span data-ttu-id="a2ff0-111">使用查詢結果並將結果集中的每一個資料列轉換為 XML 元素，該元素包含作為元素標記的泛用識別碼 \<row />。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-111">Takes the query result and transforms each row in the result set into an XML element that has a generic identifier, \<row />, as the element tag.</span></span> <span data-ttu-id="a2ff0-112">當您使用此指示詞時，您可以選擇性地指定資料列元素的名稱。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-112">You can optionally specify a name for the row element when you use this directive.</span></span> <span data-ttu-id="a2ff0-113">產生的 XML 將會使用指定的 *ElementName* 作為針對每個資料列所產生的資料列元素。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-113">The resulting XML will use the specified *ElementName* as the row element generated for each row.</span></span> <span data-ttu-id="a2ff0-114">如需詳細資訊，請參閱 [搭配 FOR XML 使用 RAW 模式](use-raw-mode-with-for-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-114">For more information, see [Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="a2ff0-115">AUTO</span><span class="sxs-lookup"><span data-stu-id="a2ff0-115">AUTO</span></span>  
 <span data-ttu-id="a2ff0-116">將查詢結果以簡易巢狀 XML 樹狀結構傳回。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-116">Returns query results in a simple, nested XML tree.</span></span> <span data-ttu-id="a2ff0-117">FROM 子句中的每個資料表至少都有一個資料行是列在 SELECT 子句中，這些資料表是以 XML 元素表示。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-117">Each table in the FROM clause for which at least one column is listed in the SELECT clause is represented as an XML element.</span></span> <span data-ttu-id="a2ff0-118">列在 SELECT 子句中的資料行會對應到適當的元素屬性。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-118">The columns listed in the SELECT clause are mapped to the appropriate element attributes.</span></span> <span data-ttu-id="a2ff0-119">如需詳細資訊，請參閱 [搭配 FOR XML 使用 AUTO 模式](use-auto-mode-with-for-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-119">For more information, see [Use AUTO Mode with FOR XML](use-auto-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="a2ff0-120">EXPLICIT</span><span class="sxs-lookup"><span data-stu-id="a2ff0-120">EXPLICIT</span></span>  
 <span data-ttu-id="a2ff0-121">指定產生之 XML 樹狀結構的形狀已明確地定義。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-121">Specifies that the shape of the resulting XML tree is defined explicitly.</span></span> <span data-ttu-id="a2ff0-122">透過使用此模式，必須以特定方式撰寫查詢，這樣才能明確地指定您需要的巢狀其他資訊。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-122">By using this mode, queries must be written in a particular way so additional information about the nesting you want is specified explicitly.</span></span> <span data-ttu-id="a2ff0-123">如需詳細資訊，請參閱 [搭配 FOR XML 使用 EXPLICIT 模式](use-explicit-mode-with-for-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-123">For more information, see [Use EXPLICIT Mode with FOR XML](use-explicit-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="a2ff0-124">PATH</span><span class="sxs-lookup"><span data-stu-id="a2ff0-124">PATH</span></span>  
 <span data-ttu-id="a2ff0-125">提供更簡單的方式來混合元素與屬性，並引用其他的巢狀來代表複雜的屬性。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-125">Provides a simpler way to mix elements and attributes, and to introduce additional nesting for representing complex properties.</span></span> <span data-ttu-id="a2ff0-126">您可以使用 FOR XML EXPLICIT 模式查詢來建構從資料列集而來的這類 XML，但是 PATH 模式對於可能會比較繁雜的 EXPLICIT 模式查詢提供較簡單的替代方案。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-126">You can use FOR XML EXPLICIT mode queries to construct this kind of XML from a rowset, but the PATH mode provides a simpler alternative to the possibly cumbersome EXPLICIT mode queries.</span></span> <span data-ttu-id="a2ff0-127">PATH 模式還可撰寫巢狀 FOR XML 查詢及 TYPE 指示詞，以傳回 **xml** 類型執行個體，這將可讓您撰寫較不複雜的查詢。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-127">PATH mode, together with the ability to write nested FOR XML queries and the TYPE directive to return **xml** type instances, allows you to write queries with less complexity.</span></span> <span data-ttu-id="a2ff0-128">它為撰寫大部份的 EXPLICIT 模式查詢提供替代方案。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-128">It provides an alternative to writing most EXPLICIT mode queries.</span></span> <span data-ttu-id="a2ff0-129">根據預設，PATH 模式會針對結果集中的每個資料列產生 \<row> 元素包裝函式。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-129">By default, PATH mode generates a \<row> element wrapper for each row in the result set.</span></span> <span data-ttu-id="a2ff0-130">您可以選擇性地指定元素名稱。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-130">You can optionally specify an element name.</span></span> <span data-ttu-id="a2ff0-131">如果您有選擇，則會將指定名稱做為包裝函數的元素名稱。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-131">If you do, the specified name is used as the wrapper element name.</span></span> <span data-ttu-id="a2ff0-132">如果您提供空白字串 (FOR XML PATH (''))，就不會產生包裝函數元素。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-132">If you provide an empty string (FOR XML PATH ('')), no wrapper element is generated.</span></span> <span data-ttu-id="a2ff0-133">如需詳細資訊，請參閱 [搭配 FOR XML 使用 PATH 模式](use-path-mode-with-for-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-133">For more information, see [Use PATH Mode with FOR XML](use-path-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="a2ff0-134">XMLDATA</span><span class="sxs-lookup"><span data-stu-id="a2ff0-134">XMLDATA</span></span>  
 <span data-ttu-id="a2ff0-135">指定應傳回的內嵌 XML-Data Reduced (XDR) 結構描述。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-135">Specifies that an inline XML-Data Reduced (XDR) schema should be returned.</span></span> <span data-ttu-id="a2ff0-136">結構描述則是文件預先決定的內嵌結構描述。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-136">The schema is prepended to the document as an inline schema.</span></span> <span data-ttu-id="a2ff0-137">如需實用範例，請參閱 [搭配 FOR XML 使用 RAW 模式](use-raw-mode-with-for-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-137">For a working sample, see [Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="a2ff0-138">XMLSCHEMA</span><span class="sxs-lookup"><span data-stu-id="a2ff0-138">XMLSCHEMA</span></span>  
 <span data-ttu-id="a2ff0-139">傳回內嵌 W3C XML 結構描述 (XSD)。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-139">Returns an inline W3C XML Schema (XSD).</span></span> <span data-ttu-id="a2ff0-140">在指定此指示詞時，您可以選擇性地指定目標命名空間 URI。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-140">You can optionally specify a target namespace URI when specifying this directive.</span></span> <span data-ttu-id="a2ff0-141">這將會傳回結構描述中指定的命名空間。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-141">This returns the specified namespace in the schema.</span></span> <span data-ttu-id="a2ff0-142">如需詳細資訊，請參閱 [產生內嵌 XSD 結構描述](generate-an-inline-xsd-schema.md)。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-142">For more information, see [Generate an Inline XSD Schema](generate-an-inline-xsd-schema.md).</span></span> <span data-ttu-id="a2ff0-143">如需實用範例，請參閱 [搭配 FOR XML 使用 RAW 模式](use-raw-mode-with-for-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-143">For a working sample, see [Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="a2ff0-144">ELEMENTS</span><span class="sxs-lookup"><span data-stu-id="a2ff0-144">ELEMENTS</span></span>  
 <span data-ttu-id="a2ff0-145">若指定了 ELEMENTS 選項，則資料行會以子元素傳回。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-145">If the ELEMENTS option is specified, the columns are returned as subelements.</span></span> <span data-ttu-id="a2ff0-146">否則這些資料行會對應到 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-146">Otherwise, they are mapped to XML attributes.</span></span> <span data-ttu-id="a2ff0-147">此選項只在 RAW、AUTO 以及 PATH 模式中才有支援。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-147">This option is supported in RAW, AUTO, and PATH modes only.</span></span> <span data-ttu-id="a2ff0-148">在使用此指示詞時，您可以選擇性地指定 XSINIL 或 ABSENT。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-148">You can optionally specify XSINIL or ABSENT when you use this directive.</span></span> <span data-ttu-id="a2ff0-149">XSINIL 可指定將含有 **xsi:nil** 屬性的元素，設為針對 NULL 資料行值所建立的 True。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-149">XSINIL specifies that an element that has an **xsi:nil** attribute set to True be created for NULL column values.</span></span> <span data-ttu-id="a2ff0-150">依預設或當同時指定 ABSENT 與 ELEMENTS 時，就不會針對 NULL 值建立任何元素。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-150">By default or when ABSENT is specified together with ELEMENTS, no elements are created for NULL values.</span></span> <span data-ttu-id="a2ff0-151">如需實用範例，請參閱 [搭配 FOR XML 使用 RAW 模式](use-raw-mode-with-for-xml.md) 和 [搭配 FOR XML 使用 AUTO 模式](use-auto-mode-with-for-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-151">For a working sample, see [Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md) and [Use AUTO Mode with FOR XML](use-auto-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="a2ff0-152">BINARY BASE64</span><span class="sxs-lookup"><span data-stu-id="a2ff0-152">BINARY BASE64</span></span>  
 <span data-ttu-id="a2ff0-153">若指定 BINARY Base64 選項，則任何由查詢所傳回的二進位資料都會以 base64 編碼格式表示。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-153">If the BINARY Base64 option is specified, any binary data returned by the query is represented in base64-encoded format.</span></span> <span data-ttu-id="a2ff0-154">若要使用 RAW 和 EXPLICIT 模式擷取二進位資料，必須指定此選項。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-154">To retrieve binary data by using RAW and EXPLICIT mode, this option must be specified.</span></span> <span data-ttu-id="a2ff0-155">在 AUTO 模式下，二進位資料在預設下是以參考來傳回。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-155">In AUTO mode, binary data is returned as a reference by default.</span></span> <span data-ttu-id="a2ff0-156">如需實用範例，請參閱 [搭配 FOR XML 使用 RAW 模式](use-raw-mode-with-for-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-156">For a working sample, see [Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="a2ff0-157">TYPE</span><span class="sxs-lookup"><span data-stu-id="a2ff0-157">TYPE</span></span>  
 <span data-ttu-id="a2ff0-158">指定查詢以 **xml** 類型傳回結果。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-158">Specifies that the query returns the results as the **xml** type.</span></span> <span data-ttu-id="a2ff0-159">如需詳細資訊，請參閱 [FOR XML 查詢中的 TYPE 指示詞](type-directive-in-for-xml-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-159">For more information, see [TYPE Directive in FOR XML Queries](type-directive-in-for-xml-queries.md).</span></span>  
  
 <span data-ttu-id="a2ff0-160">ROOT [('*RootName*')]</span><span class="sxs-lookup"><span data-stu-id="a2ff0-160">ROOT [('*RootName*')]</span></span>  
 <span data-ttu-id="a2ff0-161">指定將單一最上層元素加入產生的 XML。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-161">Specifies that a single, top-level element be added to the resulting XML.</span></span> <span data-ttu-id="a2ff0-162">您可以選擇性地指定要產生的根元素名稱。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-162">You can optionally specify the root element name to generate.</span></span> <span data-ttu-id="a2ff0-163">預設值是 "root"。</span><span class="sxs-lookup"><span data-stu-id="a2ff0-163">The default value is "root".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2ff0-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2ff0-164">See Also</span></span>  
 <span data-ttu-id="a2ff0-165">[使用 FOR XML 的 RAW 模式](use-raw-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="a2ff0-165">[Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="a2ff0-166">[搭配 FOR XML 使用 AUTO 模式](use-auto-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="a2ff0-166">[Use AUTO Mode with FOR XML](use-auto-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="a2ff0-167">[搭配 FOR XML 使用 EXPLICIT 模式](use-explicit-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="a2ff0-167">[Use EXPLICIT Mode with FOR XML](use-explicit-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="a2ff0-168">[搭配 FOR XML 使用 PATH 模式](use-path-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="a2ff0-168">[Use PATH Mode with FOR XML](use-path-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="a2ff0-169">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a2ff0-169">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="a2ff0-170">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a2ff0-170">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
