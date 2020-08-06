---
title: 使用 XPath 查詢的簡介 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], about XPath queries
- W3C XPath specification
- XPath queries [SQLXML], functionality
ms.assetid: 01050a8e-0ccc-4a02-a4eb-b48be5c3f4f3
author: rothja
ms.author: jroth
ms.openlocfilehash: dd173f16ee0e97dac1c45039f75022bbf2dc0782
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585254"
---
# <a name="introduction-to-using-xpath-queries-sqlxml-40"></a><span data-ttu-id="a87f0-102">使用 XPath 查詢的簡介 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="a87f0-102">Introduction to Using XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="a87f0-103">您可以將 XML 路徑語言 (XPath) 查詢指定成 URL 的一部分或在範本中指定此查詢。</span><span class="sxs-lookup"><span data-stu-id="a87f0-103">An XML Path Language (XPath) query can be specified as part of a URL or within a template.</span></span> <span data-ttu-id="a87f0-104">對應結構描述會決定這個產生片段的結構，而且系統會從資料庫中擷取值。</span><span class="sxs-lookup"><span data-stu-id="a87f0-104">The mapping schema determines the structure of this resulting fragment, and the values are retrieved from the database.</span></span> <span data-ttu-id="a87f0-105">這個程序在概念上類似於使用 CREATE VIEW 陳述式來建立檢視，然後針對它們撰寫 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="a87f0-105">This process is conceptually similar to creating views using the CREATE VIEW statement and writing SQL queries against them.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a87f0-106">若要了解 SQLXML 4.0 中的 XPath 查詢，您必須熟悉 XML 檢視和相關的概念，例如範本與對應結構描述。</span><span class="sxs-lookup"><span data-stu-id="a87f0-106">To understand XPath queries in SQLXML 4.0, you must be familiar with XML views and related concepts such as templates and mapping schema.</span></span> <span data-ttu-id="a87f0-107">如需詳細資訊，請參閱[批註式 XSD 架構簡介 &#40;SQLXML 4.0&#41;](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)，以及全球資訊網協會 (W3C) 所定義的 XPath 標準。</span><span class="sxs-lookup"><span data-stu-id="a87f0-107">For more information, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md), and the XPath standard defined by the World Wide Web Consortium (W3C).</span></span>  
  
 <span data-ttu-id="a87f0-108">XML 文件是由元素節點、屬性節點、文字節點等節點所組成。</span><span class="sxs-lookup"><span data-stu-id="a87f0-108">An XML document consists of nodes such as an element node, attribute node, text node, and so on.</span></span> <span data-ttu-id="a87f0-109">例如，請考慮下列 XML 文件：</span><span class="sxs-lookup"><span data-stu-id="a87f0-109">For example, consider this XML document:</span></span>  
  
```  
<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was  
          very satisfied</Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue white red">  
          <Urgency>Important</Urgency>  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>  
```  
  
 <span data-ttu-id="a87f0-110">在本檔中， **\<Customer>** 是元素節點， **cid**是屬性節點，而「**重要**」是文位元組點。</span><span class="sxs-lookup"><span data-stu-id="a87f0-110">In this document, **\<Customer>** is an element node, **cid** is an attribute node, and **"Important"** is a text node.</span></span>  
  
 <span data-ttu-id="a87f0-111">XPath 是一種圖表導覽語言，可用來從 XML 文件中選取一組節點。</span><span class="sxs-lookup"><span data-stu-id="a87f0-111">XPath is a graph navigation language used to select a set of nodes from an XML document.</span></span> <span data-ttu-id="a87f0-112">每個 XPath 運算子都會根據前一個 XPath 運算子所選取的節點集來選取節點集。</span><span class="sxs-lookup"><span data-stu-id="a87f0-112">Each XPath operator selects a node-set based on a node-set selected by a previous XPath operator.</span></span> <span data-ttu-id="a87f0-113">例如，假設有一組 **\<Customer>** 節點，則 XPath 可以選取 **\<Order>** **日期**屬性值為 **"7/14/1999"** 的所有節點。</span><span class="sxs-lookup"><span data-stu-id="a87f0-113">For example, given a set of **\<Customer>** nodes, XPath can select all **\<Order>** nodes with the **date** attribute value of **"7/14/1999"**.</span></span> <span data-ttu-id="a87f0-114">產生的節點集會包含訂單日期為 7/14/1999 的所有訂單。</span><span class="sxs-lookup"><span data-stu-id="a87f0-114">The resulting node-set contains all the orders with order date 7/14/1999.</span></span>  
  
 <span data-ttu-id="a87f0-115">全球資訊網協會 (W3C) 將 XPath 語言定義成標準導覽語言。</span><span class="sxs-lookup"><span data-stu-id="a87f0-115">The XPath language is defined by the World Wide Web Consortium (W3C) as a standard navigation language.</span></span> <span data-ttu-id="a87f0-116">SQLXML 4.0 會執行 W3C XPath 規格的子集，其位於 http://www.w3.org/TR/1999/PR-xpath-19991008.html 。</span><span class="sxs-lookup"><span data-stu-id="a87f0-116">SQLXML 4.0 implements a subset of the W3C XPath specification, which is located at http://www.w3.org/TR/1999/PR-xpath-19991008.html.</span></span>  
  
 <span data-ttu-id="a87f0-117">下面是 W3C XPath 實作與 SQLXML 4.0 實作之間的重要差異。</span><span class="sxs-lookup"><span data-stu-id="a87f0-117">The following are key differences between the W3C XPath implementation and the SQLXML 4.0 implementation.</span></span>  
  
-   <span data-ttu-id="a87f0-118">**根目錄查詢**</span><span class="sxs-lookup"><span data-stu-id="a87f0-118">**Root queries**</span></span>  
  
     <span data-ttu-id="a87f0-119">SQLXML 4.0 不支援根目錄查詢 (/)。</span><span class="sxs-lookup"><span data-stu-id="a87f0-119">SQLXML 4.0 does not support the root query (/).</span></span> <span data-ttu-id="a87f0-120">每個 XPath 查詢都必須從架構的最上層開始 **\<ElementType>** 。</span><span class="sxs-lookup"><span data-stu-id="a87f0-120">Every XPath query must begin at a top-level **\<ElementType>** in the schema.</span></span>  
  
-   <span data-ttu-id="a87f0-121">**報告錯誤**</span><span class="sxs-lookup"><span data-stu-id="a87f0-121">**Reporting errors**</span></span>  
  
     <span data-ttu-id="a87f0-122">W3C XPath 規格沒有定義任何錯誤條件。</span><span class="sxs-lookup"><span data-stu-id="a87f0-122">The W3C XPath specification defines no error conditions.</span></span> <span data-ttu-id="a87f0-123">無法選取任何節點的 XPath 查詢會傳回空的節點集。</span><span class="sxs-lookup"><span data-stu-id="a87f0-123">XPath queries that fail to select any nodes return an empty node-set.</span></span> <span data-ttu-id="a87f0-124">在 SQLXML 4.0 中，查詢可能會傳回許多錯誤訊息類型。</span><span class="sxs-lookup"><span data-stu-id="a87f0-124">In SQLXML 4.0, a query can return many types of error messages.</span></span>  
  
-   <span data-ttu-id="a87f0-125">**檔順序**</span><span class="sxs-lookup"><span data-stu-id="a87f0-125">**Document order**</span></span>  
  
     <span data-ttu-id="a87f0-126">在 SQLXML 4.0 中，不一定會決定文件順序。</span><span class="sxs-lookup"><span data-stu-id="a87f0-126">In SQLXML 4.0, document order is not always determined.</span></span> <span data-ttu-id="a87f0-127">因此，系統不會實作使用文件順序 (例如 `following`) 的數值述詞和軸。</span><span class="sxs-lookup"><span data-stu-id="a87f0-127">Therefore, numeric predicates and axes that use document order (such as `following`) are not implemented.</span></span>  
  
     <span data-ttu-id="a87f0-128">缺少文件順序也就表示只有當節點對應至單一資料列中的單一資料行時，才能夠評估該節點的字串值。</span><span class="sxs-lookup"><span data-stu-id="a87f0-128">The lack of document order also means that the string value of a node can be evaluated only when that node maps to a single column in a single row.</span></span> <span data-ttu-id="a87f0-129">具有子元素的元素或是 IDREFS 或 NMTOKENS 節點無法轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="a87f0-129">An element with child elements or an IDREFS or NMTOKENS node cannot be converted to string.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a87f0-130">在某些情況下，來自 `key-fields` 註解的 `relationship` 註解或索引鍵可能會產生具決定性的文件順序。</span><span class="sxs-lookup"><span data-stu-id="a87f0-130">In some cases, the `key-fields` annotation or keys from the `relationship` annotation can result in a deterministic document order.</span></span> <span data-ttu-id="a87f0-131">不過，這不是這些批註的主要使用，如需詳細資訊，請參閱[使用 sql：索引鍵欄位識別索引鍵資料行 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)和[使用 Sql： relationship 指定關聯性 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="a87f0-131">However, this is not the primary use of these annotations For more information, see [Identifying Key Columns Using sql:key-fields &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md) and [Specifying Relationships Using sql:relationship &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="a87f0-132">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="a87f0-132">**Data types**</span></span>  
  
     <span data-ttu-id="a87f0-133">SQLXML 4.0 在實作 XPath `string`、`number` 和 `boolean` 資料類型方面有所限制。</span><span class="sxs-lookup"><span data-stu-id="a87f0-133">SQLXML 4.0 has limitations in implementing the XPath `string`, `number`, and `boolean` data types.</span></span> <span data-ttu-id="a87f0-134">如需詳細資訊，請參閱[&#40;SQLXML 4.0&#41;的 XPath 資料類型](xpath-data-types-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="a87f0-134">For more information, see [XPath Data Types &#40;SQLXML 4.0&#41;](xpath-data-types-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="a87f0-135">**交叉乘積查詢**</span><span class="sxs-lookup"><span data-stu-id="a87f0-135">**Cross-product queries**</span></span>  
  
     <span data-ttu-id="a87f0-136">SQLXML 4.0 不支援交叉乘積 XPath 查詢，例如 `Customers[Order/@OrderDate=Order/@ShipDate]`。</span><span class="sxs-lookup"><span data-stu-id="a87f0-136">SQLXML 4.0 does not support cross-product XPath queries, such as `Customers[Order/@OrderDate=Order/@ShipDate]`.</span></span> <span data-ttu-id="a87f0-137">這個查詢會選取 OrderDate 等於 ShipDate 之任何訂單的所有客戶。</span><span class="sxs-lookup"><span data-stu-id="a87f0-137">This query selects all Customers with any Order for which the OrderDate equals the ShipDate of any Order.</span></span>  
  
     <span data-ttu-id="a87f0-138">不過，SQLXML 4.0 支援 `Customer[Order[@OrderDate=@ShippedDate]]` 等查詢，其中系統會刪除 OrderDate 等於其 ShipDate 之任何訂單的客戶。</span><span class="sxs-lookup"><span data-stu-id="a87f0-138">However, SQLXML 4.0 does support queries such as `Customer[Order[@OrderDate=@ShippedDate]]`, which selects Customers with any Order for which the OrderDate equals its ShipDate.</span></span>  
  
-   <span data-ttu-id="a87f0-139">**錯誤處理和安全性**</span><span class="sxs-lookup"><span data-stu-id="a87f0-139">**Error handling and security**</span></span>  
  
     <span data-ttu-id="a87f0-140">根據所使用的結構描述和 XPath 查詢運算式，在特定條件下，[!INCLUDE[tsql](../../includes/tsql-md.md)] 錯誤可能會公開給使用者。</span><span class="sxs-lookup"><span data-stu-id="a87f0-140">Depending on the schema and XPath query expression that are used, [!INCLUDE[tsql](../../includes/tsql-md.md)] errors could be exposed to users under certain conditions.</span></span>  
  
 <span data-ttu-id="a87f0-141">下列各節中的表格會提供有關在 SQLXML 4.0 中實作 XPath 查詢與 W3C 規格的差異之處。</span><span class="sxs-lookup"><span data-stu-id="a87f0-141">The tables in the following sections provide details about how the implementation of XPath queries in SQLXML 4.0 differs from the W3C specification in these areas.</span></span>  
  
## <a name="supported-functionality"></a><span data-ttu-id="a87f0-142">支援的功能</span><span class="sxs-lookup"><span data-stu-id="a87f0-142">Supported Functionality</span></span>  
 <span data-ttu-id="a87f0-143">下表將顯示在 SQLXML 4.0 中實作之 XPath 語言的功能。</span><span class="sxs-lookup"><span data-stu-id="a87f0-143">The following table shows the features of the XPath language that are implemented in SQLXML 4.0.</span></span>  
  
|<span data-ttu-id="a87f0-144">特徵</span><span class="sxs-lookup"><span data-stu-id="a87f0-144">Feature</span></span>|<span data-ttu-id="a87f0-145">項目</span><span class="sxs-lookup"><span data-stu-id="a87f0-145">Item</span></span>|<span data-ttu-id="a87f0-146">範例查詢的連結</span><span class="sxs-lookup"><span data-stu-id="a87f0-146">Link to sample queries</span></span>|  
|-------------|----------|----------------------------|  
|<span data-ttu-id="a87f0-147">軸</span><span class="sxs-lookup"><span data-stu-id="a87f0-147">Axes</span></span>|<span data-ttu-id="a87f0-148">`attribute`、`child`、`parent` 和 `self` 軸</span><span class="sxs-lookup"><span data-stu-id="a87f0-148">`attribute`, `child`, `parent`, and `self` axes</span></span>|[<span data-ttu-id="a87f0-149">在 XPath 查詢中指定軸 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="a87f0-149">Specifying Axes in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-axes-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="a87f0-150">布林值述詞，包括連續和巢狀述詞</span><span class="sxs-lookup"><span data-stu-id="a87f0-150">Boolean-valued predicates including successive and nested predicates</span></span>||[<span data-ttu-id="a87f0-151">在 XPath 查詢中指定算術運算子 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="a87f0-151">Specifying Arithmetic Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="a87f0-152">所有關係運算子</span><span class="sxs-lookup"><span data-stu-id="a87f0-152">All relational operators</span></span>|<span data-ttu-id="a87f0-153">=、！ =、<、 \<=, > 、>=</span><span class="sxs-lookup"><span data-stu-id="a87f0-153">=, !=, <, \<=, >, >=</span></span>|[<span data-ttu-id="a87f0-154">在 XPath 查詢中指定關聯式運算子 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="a87f0-154">Specifying Relational Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-relational-operators-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="a87f0-155">算術運算子</span><span class="sxs-lookup"><span data-stu-id="a87f0-155">Arithmetic operators</span></span>|<span data-ttu-id="a87f0-156">+、-、\*、div</span><span class="sxs-lookup"><span data-stu-id="a87f0-156">+, -, \*, div</span></span>|[<span data-ttu-id="a87f0-157">在 XPath 查詢中指定算術運算子 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="a87f0-157">Specifying Arithmetic Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="a87f0-158">明確轉換函數</span><span class="sxs-lookup"><span data-stu-id="a87f0-158">Explicit conversion functions</span></span>|<span data-ttu-id="a87f0-159">`number()`, `string()`, `Boolean()`</span><span class="sxs-lookup"><span data-stu-id="a87f0-159">`number()`, `string()`, `Boolean()`</span></span>|[<span data-ttu-id="a87f0-160">在 XPath 查詢中指定明確轉換函數 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="a87f0-160">Specifying Explicit Conversion Functions in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="a87f0-161">布林運算子</span><span class="sxs-lookup"><span data-stu-id="a87f0-161">Boolean operators</span></span>|<span data-ttu-id="a87f0-162">AND、OR</span><span class="sxs-lookup"><span data-stu-id="a87f0-162">AND, OR</span></span>|[<span data-ttu-id="a87f0-163">在 XPath 查詢中指定布林運算子 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="a87f0-163">Specifying Boolean Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-boolean-operators-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="a87f0-164">布林函數</span><span class="sxs-lookup"><span data-stu-id="a87f0-164">Boolean functions</span></span>|<span data-ttu-id="a87f0-165">`true()`, `false()`, `not()`</span><span class="sxs-lookup"><span data-stu-id="a87f0-165">`true()`, `false()`, `not()`</span></span>|[<span data-ttu-id="a87f0-166">在 &#40;SQLXML 4.0&#41;的 XPath 查詢中指定布耳函數</span><span class="sxs-lookup"><span data-stu-id="a87f0-166">Specifying Boolean Functions in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-boolean-functions-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="a87f0-167">XPath 變數</span><span class="sxs-lookup"><span data-stu-id="a87f0-167">XPath variables</span></span>||[<span data-ttu-id="a87f0-168">在 XPath 查詢中指定 XPath 變數 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="a87f0-168">Specifying XPath Variables in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-xpath-variables-in-xpath-queries-sqlxml-4-0.md)|  
  
## <a name="unsupported-functionality"></a><span data-ttu-id="a87f0-169">不支援的功能</span><span class="sxs-lookup"><span data-stu-id="a87f0-169">Unsupported Functionality</span></span>  
 <span data-ttu-id="a87f0-170">下表將顯示沒有在 SQLXML 4.0 中實作之 XPath 語言的功能。</span><span class="sxs-lookup"><span data-stu-id="a87f0-170">The following table shows the features of the XPath language that are not implemented in SQLXML 4.0.</span></span>  
  
|<span data-ttu-id="a87f0-171">特徵</span><span class="sxs-lookup"><span data-stu-id="a87f0-171">Feature</span></span>|<span data-ttu-id="a87f0-172">項目</span><span class="sxs-lookup"><span data-stu-id="a87f0-172">Item</span></span>|  
|-------------|----------|  
|<span data-ttu-id="a87f0-173">軸</span><span class="sxs-lookup"><span data-stu-id="a87f0-173">Axes</span></span>|<span data-ttu-id="a87f0-174">`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`</span><span class="sxs-lookup"><span data-stu-id="a87f0-174">`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`</span></span>|  
|<span data-ttu-id="a87f0-175">數值述詞</span><span class="sxs-lookup"><span data-stu-id="a87f0-175">Numeric-valued predicates</span></span>||  
|<span data-ttu-id="a87f0-176">算術運算子</span><span class="sxs-lookup"><span data-stu-id="a87f0-176">Arithmetic operators</span></span>|<span data-ttu-id="a87f0-177">mod</span><span class="sxs-lookup"><span data-stu-id="a87f0-177">mod</span></span>|  
|<span data-ttu-id="a87f0-178">節點函數</span><span class="sxs-lookup"><span data-stu-id="a87f0-178">Node functions</span></span>|<span data-ttu-id="a87f0-179">`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`</span><span class="sxs-lookup"><span data-stu-id="a87f0-179">`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`</span></span>|  
|<span data-ttu-id="a87f0-180">字串函數</span><span class="sxs-lookup"><span data-stu-id="a87f0-180">String functions</span></span>|<span data-ttu-id="a87f0-181">`string()`, `concat()`, `starts-with()`, `contains()`, `substring-before()`, `substring-after()`, `substring()`, `string-length()`, `normalize()`, `translate()`</span><span class="sxs-lookup"><span data-stu-id="a87f0-181">`string()`, `concat()`, `starts-with()`, `contains()`, `substring-before()`, `substring-after()`, `substring()`, `string-length()`, `normalize()`, `translate()`</span></span>|  
|<span data-ttu-id="a87f0-182">布林函數</span><span class="sxs-lookup"><span data-stu-id="a87f0-182">Boolean functions</span></span>|`lang()`|  
|<span data-ttu-id="a87f0-183">數值函數</span><span class="sxs-lookup"><span data-stu-id="a87f0-183">Numeric functions</span></span>|<span data-ttu-id="a87f0-184">`sum()`, `floor()`, `ceiling()`, `round()`</span><span class="sxs-lookup"><span data-stu-id="a87f0-184">`sum()`, `floor()`, `ceiling()`, `round()`</span></span>|  
|<span data-ttu-id="a87f0-185">Union 運算子</span><span class="sxs-lookup"><span data-stu-id="a87f0-185">Union operator</span></span>|<span data-ttu-id="a87f0-186">&#124;</span><span class="sxs-lookup"><span data-stu-id="a87f0-186">&#124;</span></span>|  
  
 <span data-ttu-id="a87f0-187">當您在範本中指定 XPath 查詢時，請注意下列行為：</span><span class="sxs-lookup"><span data-stu-id="a87f0-187">When you specify XPath queries in a template, note the following behavior:</span></span>  
  
-   <span data-ttu-id="a87f0-188">XPath 可以包含在 XML (中有特殊意義的字元（例如 < 或 &，而範本則是) 的 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="a87f0-188">XPath can contain characters such as < or & that have special meanings in XML (and template is an XML document).</span></span> <span data-ttu-id="a87f0-189">您必須使用 XML & 編碼來將這些字元轉義，或在 URL 中指定 XPath。</span><span class="sxs-lookup"><span data-stu-id="a87f0-189">You must escape these characters using XML &-encoding, or specify the XPath in the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a87f0-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a87f0-190">See Also</span></span>  
 [<span data-ttu-id="a87f0-191">在 SQLXML 4.0 中使用 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="a87f0-191">Using XPath Queries in SQLXML 4.0</span></span>](using-xpath-queries-in-sqlxml-4-0.md)  
  
  
