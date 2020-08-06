---
title: 使用 FOR XML 的 RAW 模式 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML RAW mode
- XMLSCHEMA option
- FOR XML clause, RAW mode
- RAW FOR XML mode
- ELEMENTS directive
- RAW mode
- XMLDATA option
ms.assetid: 02c1bc0b-760c-4589-9ab1-6927c6d9c734
author: rothja
ms.author: jroth
ms.openlocfilehash: b2908a98336ec8a6e12029ad471f22a33d7a4dcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706286"
---
# <a name="use-raw-mode-with-for-xml"></a><span data-ttu-id="523f3-102">搭配 FOR XML 使用 RAW 模式</span><span class="sxs-lookup"><span data-stu-id="523f3-102">Use RAW Mode with FOR XML</span></span>
  <span data-ttu-id="523f3-103">RAW 模式會將查詢結果集中的每個資料列轉換成具備一般識別碼 \<row>，或可選擇性提供元素名稱的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="523f3-103">RAW mode transforms each row in the query result set into an XML element that has the generic identifier \<row>, or the optionally provided element name.</span></span> <span data-ttu-id="523f3-104">根據預設，資料列集中每個不是 NULL 的資料行值都會對應到 \<row> 元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="523f3-104">By default, each column value in the rowset that is not NULL is mapped to an attribute of the \<row> element.</span></span> <span data-ttu-id="523f3-105">若將 ELEMENTS 指示詞新增到 FOR XML 子句，則每個資料行值都會對應到 \<row> 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="523f3-105">If the ELEMENTS directive is added to the FOR XML clause, each column value is mapped to a subelement of the \<row> element.</span></span> <span data-ttu-id="523f3-106">您還可以搭配 ELEMENTS 指示詞，選擇性地指定 XSINIL 選項，將結果集的 NULL 資料行值對應到具有 xsi:nil=`"`true`"`屬性的元素。</span><span class="sxs-lookup"><span data-stu-id="523f3-106">Together with the ELEMENTS directive, you can optionally specify the XSINIL option to map NULL column values in the result set to an element that has the attribute, xsi:nil=`"`true`"`.</span></span>  
  
 <span data-ttu-id="523f3-107">您可以要求結果 XML 傳回結構描述。</span><span class="sxs-lookup"><span data-stu-id="523f3-107">You can request a schema for the resulting XML.</span></span> <span data-ttu-id="523f3-108">指定 XMLDATA 選項可傳回內嵌 XDR 結構描述。</span><span class="sxs-lookup"><span data-stu-id="523f3-108">Specifying the XMLDATA option returns an in-line XDR schema.</span></span> <span data-ttu-id="523f3-109">指定 XMLSCHEMA 選項則可傳回內嵌 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="523f3-109">Specifying the XMLSCHEMA option returns an in-line XSD schema.</span></span> <span data-ttu-id="523f3-110">結構描述會出現在資料的開頭。</span><span class="sxs-lookup"><span data-stu-id="523f3-110">The schema appears at the start of the data.</span></span> <span data-ttu-id="523f3-111">在結果中，結構描述命名空間參考會在每個最上層的元素重複出現。</span><span class="sxs-lookup"><span data-stu-id="523f3-111">In the result, the schema namespace reference is repeated for every top-level element.</span></span>  
  
 <span data-ttu-id="523f3-112">FOR XML 子句中必須指定 BINARY BASE64 選項，才能以 Base64 編碼格式傳回二進位資料。</span><span class="sxs-lookup"><span data-stu-id="523f3-112">The BINARY BASE64 option must be specified in the FOR XML clause to return the binary data in base64-encoded format.</span></span> <span data-ttu-id="523f3-113">在 RAW 模式中，若未指定 BINARY BASE64 選項，則擷取二進位資料就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="523f3-113">In RAW mode, retrieving binary data without specifying the BINARY BASE64 option will result in an error.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="523f3-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="523f3-114">In This Section</span></span>  
 <span data-ttu-id="523f3-115">本區段包含下列範例：</span><span class="sxs-lookup"><span data-stu-id="523f3-115">This section contains the following examples:</span></span>  
  
-   [<span data-ttu-id="523f3-116">範例：以 XML 的形式擷取產品型號資訊</span><span class="sxs-lookup"><span data-stu-id="523f3-116">Example: Retrieving Product Model Information as XML</span></span>](example-retrieving-product-model-information-as-xml.md)  
  
-   [<span data-ttu-id="523f3-117">範例：使用 ELEMENTS 指示詞指定 XSINIL</span><span class="sxs-lookup"><span data-stu-id="523f3-117">Example: Specifying XSINIL with the ELEMENTS Directive</span></span>](example-specifying-xsinil-with-the-elements-directive.md)  
  
-   [<span data-ttu-id="523f3-118">範例：使用 XMLDATA 和 XMLSCHEMA 選項來要求結構描述作為結果</span><span class="sxs-lookup"><span data-stu-id="523f3-118">Example: Requesting Schemas as Results with the XMLDATA and XMLSCHEMA Options</span></span>](example-requesting-schemas-as-results-with-the-xmldata-and-xmlschema-options.md)  
  
-   [<span data-ttu-id="523f3-119">範例：擷取二進位資料</span><span class="sxs-lookup"><span data-stu-id="523f3-119">Example: Retrieving Binary Data</span></span>](example-retrieving-binary-data.md)  
  
-   [<span data-ttu-id="523f3-120">範例：重新命名 &#60;row&#62; 元素</span><span class="sxs-lookup"><span data-stu-id="523f3-120">Example: Renaming the &#60;row&#62; Element</span></span>](example-renaming-the-row-element.md)  
  
-   [<span data-ttu-id="523f3-121">範例：為 FOR XML 產生的 XML 指定根元素</span><span class="sxs-lookup"><span data-stu-id="523f3-121">Example: Specifying a Root Element for the XML Generated by FOR XML</span></span>](example-specifying-a-root-element-for-the-xml-generated-by-for-xml.md)  
  
-   [<span data-ttu-id="523f3-122">範例：查詢 XMLType 資料行</span><span class="sxs-lookup"><span data-stu-id="523f3-122">Example: Querying XMLType Columns</span></span>](example-querying-xmltype-columns.md)  
  
## <a name="see-also"></a><span data-ttu-id="523f3-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="523f3-123">See Also</span></span>  
 <span data-ttu-id="523f3-124">[使用 WITH XMLNAMESPACES 將命名空間加入至查詢](add-namespaces-to-queries-with-with-xmlnamespaces.md) </span><span class="sxs-lookup"><span data-stu-id="523f3-124">[Add Namespaces to Queries with WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md) </span></span>  
 <span data-ttu-id="523f3-125">[搭配 FOR XML 使用 AUTO 模式](use-auto-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="523f3-125">[Use AUTO Mode with FOR XML](use-auto-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="523f3-126">[搭配 FOR XML 使用 EXPLICIT 模式](use-explicit-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="523f3-126">[Use EXPLICIT Mode with FOR XML](use-explicit-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="523f3-127">[搭配 FOR XML 使用 PATH 模式](use-path-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="523f3-127">[Use PATH Mode with FOR XML](use-path-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="523f3-128">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="523f3-128">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="523f3-129">FOR XML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="523f3-129">FOR XML &#40;SQL Server&#41;</span></span>](../xml/for-xml-sql-server.md)  
  
  
