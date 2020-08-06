---
title: 指定選擇性 XML 索引的路徑和最佳化提示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: 486ee339-165b-4aeb-b760-d2ba023d7d0a
author: rothja
ms.author: jroth
ms.openlocfilehash: 1a9d683fe57d489fdb9922b53d2c5c6825835216
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703966"
---
# <a name="specify-paths-and-optimization-hints-for-selective-xml-indexes"></a><span data-ttu-id="93d50-102">指定選擇性 XML 索引的路徑和最佳化提示</span><span class="sxs-lookup"><span data-stu-id="93d50-102">Specify Paths and Optimization Hints for Selective XML Indexes</span></span>
  <span data-ttu-id="93d50-103">本主題描述如何指定建立或修改選擇性 XML 索引時，要索引的節點路徑以及索引的最佳化提示。</span><span class="sxs-lookup"><span data-stu-id="93d50-103">This topic describes how to specify node paths to index and optimization hints for indexing when you create or alter selective XML indexes.</span></span>  
  
 <span data-ttu-id="93d50-104">您會同時在下列其中一個陳述式中指定節點路徑及最佳化提示：</span><span class="sxs-lookup"><span data-stu-id="93d50-104">You specify node paths and optimization hints at the same time in one of the following statements:</span></span>  
  
-   <span data-ttu-id="93d50-105">在 **CREATE** 陳述式的 **FOR** 子句中。</span><span class="sxs-lookup"><span data-stu-id="93d50-105">In the **FOR** clause of a **CREATE** statement.</span></span> <span data-ttu-id="93d50-106">如需詳細資訊，請參閱 [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="93d50-106">For more information, see [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).</span></span>  
  
-   <span data-ttu-id="93d50-107">在 **ALTER** 陳述式的 **ADD** 子句中。</span><span class="sxs-lookup"><span data-stu-id="93d50-107">In the **ADD** clause of an **ALTER** statement.</span></span> <span data-ttu-id="93d50-108">如需詳細資訊，請參閱 [ALTER INDEX &#40;選擇性 XML 索引&#41;](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="93d50-108">For more information, see [ALTER INDEX &#40;Selective XML Indexes&#41;](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="93d50-109">如需選擇性 XML 索引的詳細資訊，請參閱 [選擇性 XML 索引 &#40;SXI&#41;](../xml/selective-xml-indexes-sxi.md)。</span><span class="sxs-lookup"><span data-stu-id="93d50-109">For more information about selective XML indexes, see [Selective XML Indexes &#40;SXI&#41;](../xml/selective-xml-indexes-sxi.md).</span></span>  
  
##  <a name="understanding-xquery-and-sql-server-types-in-untyped-xml"></a><a name="untyped"></a> <span data-ttu-id="93d50-110">了解不具類型之 XML 中的 XQuery 和 SQL Server 類型</span><span class="sxs-lookup"><span data-stu-id="93d50-110">Understanding XQuery and SQL Server Types in Untyped XML</span></span>  
 <span data-ttu-id="93d50-111">選擇性 XML 索引支援兩種類型的系統：XQuery 類型和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 類型。</span><span class="sxs-lookup"><span data-stu-id="93d50-111">Selective XML indexes support two type systems: XQuery types and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types.</span></span> <span data-ttu-id="93d50-112">索引路徑可用來比對 XQuery 運算式，或是比對 XML 資料類型之 value() 方法的傳回類型。</span><span class="sxs-lookup"><span data-stu-id="93d50-112">The indexed path can be used either to match an XQuery expression, or to match the return type of the value() method of the XML data type.</span></span>  
  
-   <span data-ttu-id="93d50-113">如果要索引的路徑未加上註解，或是使用 XQUERY 關鍵字註解，則路徑會比對 XQuery 運算式。</span><span class="sxs-lookup"><span data-stu-id="93d50-113">When a path to index is not annotated, or is annotated with the XQUERY keyword, the path matches an XQuery expression.</span></span> <span data-ttu-id="93d50-114">XQUERY 註解的節點路徑有兩種變化：</span><span class="sxs-lookup"><span data-stu-id="93d50-114">There are two variations for XQUERY-annotated node paths:</span></span>  
  
    -   <span data-ttu-id="93d50-115">如果您未指定 XQUERY 關鍵字和 XQuery 資料類型，則會使用預設對應。</span><span class="sxs-lookup"><span data-stu-id="93d50-115">If you do not specify the XQUERY keyword and the XQuery data type, then default mappings are used.</span></span> <span data-ttu-id="93d50-116">通常效能和儲存不是最佳的。</span><span class="sxs-lookup"><span data-stu-id="93d50-116">Typically performance and storage are not optimal.</span></span>  
  
    -   <span data-ttu-id="93d50-117">如果您指定 XQUERY 關鍵字和 XQuery 資料類型，並且選擇性地指定其他最佳化提示，就可以達到最佳效能和最有效率的儲存。</span><span class="sxs-lookup"><span data-stu-id="93d50-117">If you specify the XQUERY keyword and the XQuery data type, and optionally other optimization hints, then you can achieve the best possible performance and the most efficient possible storage.</span></span> <span data-ttu-id="93d50-118">不過，轉換可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="93d50-118">However, a cast can fail.</span></span>  
  
-   <span data-ttu-id="93d50-119">如果要索引的路徑是以 SQL 關鍵字註解，則路徑符合 XML 資料類型之 value() 方法的傳回類型。</span><span class="sxs-lookup"><span data-stu-id="93d50-119">When a path to index is annotated with the SQL keyword, the path matches the return type of the value() method of the XML data type.</span></span> <span data-ttu-id="93d50-120">指定適當的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型，也就是預期從 value() 方法得到的傳回類型。</span><span class="sxs-lookup"><span data-stu-id="93d50-120">Specify the appropriate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type, which is the return type that you expect from the value() method.</span></span>  
  
 <span data-ttu-id="93d50-121">XQuery 運算式 XML 類型系統與套用至 XML 資料類型之 value() 方法的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 類型系統之間存在細微的差異。</span><span class="sxs-lookup"><span data-stu-id="93d50-121">There are subtle differences between the XQuery expressions XML type system and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type system applied to the value() method of the XML data type.</span></span> <span data-ttu-id="93d50-122">這些差異包括下列幾項：</span><span class="sxs-lookup"><span data-stu-id="93d50-122">These differences include the following:</span></span>  
  
-   <span data-ttu-id="93d50-123">XQuery 類型系統會考慮尾端空白。</span><span class="sxs-lookup"><span data-stu-id="93d50-123">The XQuery type system is aware of trailing spaces.</span></span> <span data-ttu-id="93d50-124">例如，根據 XQuery 類型語意，字串 "abc" 與 "abc " 不相等，但在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中這些字串相等。</span><span class="sxs-lookup"><span data-stu-id="93d50-124">For example, according to XQuery type semantics, the strings "abc" and "abc " are not equal, while in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] these strings are equal.</span></span>  
  
-   <span data-ttu-id="93d50-125">XQuery 浮點資料類型支援 +/- 零和 +/- 無限大這些特殊值。</span><span class="sxs-lookup"><span data-stu-id="93d50-125">XQuery floating point data types support special values of +/- zero and +/- infinity.</span></span> <span data-ttu-id="93d50-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 浮點資料類型不支援這些特殊值。</span><span class="sxs-lookup"><span data-stu-id="93d50-126">These special values are not supported in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] floating point data types.</span></span>  
  
### <a name="xquery-types-in-untyped-xml"></a><span data-ttu-id="93d50-127">不具類型 XML 中的 XQuery 類型</span><span class="sxs-lookup"><span data-stu-id="93d50-127">XQuery Types in Untyped XML</span></span>  
  
-   <span data-ttu-id="93d50-128">XQuery 類型會比對 XML 資料類型之所有方法中的 XQuery 運算式，包含 value() 方法。</span><span class="sxs-lookup"><span data-stu-id="93d50-128">XQuery types match XQuery expressions in all methods of the XML data type including the value() method.</span></span>  
  
-   <span data-ttu-id="93d50-129">XQuery 類型支援這些最佳化提示：node()、SINGLETON、DATA TYPE 和 MAXLENGTH。</span><span class="sxs-lookup"><span data-stu-id="93d50-129">XQuery types support these optimization hints: node(), SINGLETON, DATA TYPE, and MAXLENGTH.</span></span>  
  
 <span data-ttu-id="93d50-130">對於在不具類型 XML 上的 XQuery 運算式，您可以選擇兩種作業模式：</span><span class="sxs-lookup"><span data-stu-id="93d50-130">For XQuery expressions over untyped XML, you can choose between two modes of operation:</span></span>  
  
-   <span data-ttu-id="93d50-131">**預設對應模式**。</span><span class="sxs-lookup"><span data-stu-id="93d50-131">**Default mapping mode**.</span></span> <span data-ttu-id="93d50-132">在此模式中，您只會指定建立選擇性 XML 索引時的路徑。</span><span class="sxs-lookup"><span data-stu-id="93d50-132">In this mode, you specify only the path when creating a selective XML index.</span></span>  
  
-   <span data-ttu-id="93d50-133">**使用者指定的對應模式**。</span><span class="sxs-lookup"><span data-stu-id="93d50-133">**User-specified mapping mode**.</span></span> <span data-ttu-id="93d50-134">在此模式中，您會指定路徑和選用的最佳化提示。</span><span class="sxs-lookup"><span data-stu-id="93d50-134">In this mode, you specify both the path and optional optimization hints.</span></span>  
  
 <span data-ttu-id="93d50-135">預設對應模式一律使用安全且普遍的保守儲存選項。</span><span class="sxs-lookup"><span data-stu-id="93d50-135">The default mapping mode uses a conservative storage option which is always safe and general.</span></span> <span data-ttu-id="93d50-136">它可以比對任何運算式類型。</span><span class="sxs-lookup"><span data-stu-id="93d50-136">It can match any expression type.</span></span> <span data-ttu-id="93d50-137">預設對應模式的限制比最佳效能少，因為需要執行階段轉換的次數增加，而且次要索引無法使用。</span><span class="sxs-lookup"><span data-stu-id="93d50-137">A limitation of the default mapping mode is less than optimal performance, because an increased number of runtime casts are required, and secondary indexes are not available.</span></span>  
  
 <span data-ttu-id="93d50-138">以下範例是使用預設對應建立的選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="93d50-138">Here is an example of a selective XML index created with default mappings.</span></span> <span data-ttu-id="93d50-139">針對這三種路徑會使用預設節點類型 (**xs:untypedAtomic**) 和基數。</span><span class="sxs-lookup"><span data-stu-id="93d50-139">For all three paths, the default node type (**xs:untypedAtomic**) and cardinality are used.</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX example_sxi_UX_default  
ON Tbl(xmlcol)  
FOR  
(  
mypath01 =  '/a/b',  
mypath02 = '/a/b/c',  
mypath03 = '/a/b/d'  
)  
```  
  
 <span data-ttu-id="93d50-140">使用者指定的對應模式可讓您指定類型和基數，讓節點獲得更佳的效能。</span><span class="sxs-lookup"><span data-stu-id="93d50-140">The user-specified mapping mode lets you specify a type and cardinality for the node to obtain better performance.</span></span> <span data-ttu-id="93d50-141">不過，這種效能提升是藉由降低安全性 (因為轉換可能會失敗) 與普遍性 (因為只有指定的類型會與選擇性 XML 索引比對) 達成。</span><span class="sxs-lookup"><span data-stu-id="93d50-141">However, this improved performance is achieved by giving up safety - because a cast can fail - and generality - because only the specified type is matched with the selective XML index.</span></span>  
  
 <span data-ttu-id="93d50-142">不具類型 XML 轉換所支援的 XQuery 類型包括：</span><span class="sxs-lookup"><span data-stu-id="93d50-142">The XQuery types supported for untyped XML case are:</span></span>  
  
-   <span data-ttu-id="93d50-143">**xs:boolean**</span><span class="sxs-lookup"><span data-stu-id="93d50-143">**xs:boolean**</span></span>  
  
-   <span data-ttu-id="93d50-144">**xs:double**</span><span class="sxs-lookup"><span data-stu-id="93d50-144">**xs:double**</span></span>  
  
-   <span data-ttu-id="93d50-145">**xs:string**</span><span class="sxs-lookup"><span data-stu-id="93d50-145">**xs:string**</span></span>  
  
-   <span data-ttu-id="93d50-146">**xs:date**</span><span class="sxs-lookup"><span data-stu-id="93d50-146">**xs:date**</span></span>  
  
-   <span data-ttu-id="93d50-147">**xs:time**</span><span class="sxs-lookup"><span data-stu-id="93d50-147">**xs:time**</span></span>  
  
-   <span data-ttu-id="93d50-148">**xs:dateTime**</span><span class="sxs-lookup"><span data-stu-id="93d50-148">**xs:dateTime**</span></span>  
  
 <span data-ttu-id="93d50-149">如果未指定類型，則會假設節點為 **xs:untypedAtomic** 資料類型。</span><span class="sxs-lookup"><span data-stu-id="93d50-149">If the type is not specified, the node is assumed to be of the **xs:untypedAtomic** data type.</span></span>  
  
 <span data-ttu-id="93d50-150">您可以最佳化透過下列方式顯示的選擇性 XML 索引：</span><span class="sxs-lookup"><span data-stu-id="93d50-150">You can optimize the selective XML index shown in the following manner:</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX example_sxi_UX_optimized  
ON Tbl(xmlcol)  
FOR  
(  
mypath= '/a/b' as XQUERY 'node()',  
pathX = '/a/b/c' as XQUERY 'xs:double' SINGLETON,  
pathY = '/a/b/d' as XQUERY 'xs:string' MAXLENGTH(200) SINGLETON  
)  
-- mypath - Only the node value is needed; storage is saved.  
-- pathX - Performance is improved; secondary indexes are possible.  
-- pathY - Performance is improved; secondary indexes are possible; storage is saved.  
```  
  
### <a name="sql-server-types-in-untyped-xml"></a><span data-ttu-id="93d50-151">不具類型 XML 中的 SQL Server 類型</span><span class="sxs-lookup"><span data-stu-id="93d50-151">SQL Server Types in Untyped XML</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="93d50-152">類型會比對 value() 方法的傳回值。</span><span class="sxs-lookup"><span data-stu-id="93d50-152">types match the return value of the value() method.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="93d50-153">類型支援此最佳化提示：SINGLETON。</span><span class="sxs-lookup"><span data-stu-id="93d50-153">types support this optimization hint: SINGLETON.</span></span>  
  
 <span data-ttu-id="93d50-154">對於傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 類型的路徑必須強制指定類型。</span><span class="sxs-lookup"><span data-stu-id="93d50-154">Specifying a type is mandatory for paths that return [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types.</span></span> <span data-ttu-id="93d50-155">請使用您在 value() 方法中所使用的相同 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 類型。</span><span class="sxs-lookup"><span data-stu-id="93d50-155">Use the same [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type that you would use in the value() method.</span></span>  
  
 <span data-ttu-id="93d50-156">請考慮以下查詢：</span><span class="sxs-lookup"><span data-stu-id="93d50-156">Consider the following query:</span></span>  
  
```sql  
SELECT T.record,  
    T.xmldata.value('(/a/b/d)[1]', 'NVARCHAR(200)')  
FROM myXMLTable T  
```  
  
 <span data-ttu-id="93d50-157">指定的查詢會從封裝至 NVARCHAR(200) 資料類型內的路徑 `/a/b/d` 傳回值，因此要為節點指定的資料類型就很明顯。</span><span class="sxs-lookup"><span data-stu-id="93d50-157">The specified query returns a value from the path `/a/b/d` packed into an NVARCHAR(200) data type, so the data type to specify for the node is obvious.</span></span> <span data-ttu-id="93d50-158">不過，沒有用來在不具類型的 XML 中指定節點基數的結構描述。</span><span class="sxs-lookup"><span data-stu-id="93d50-158">However there is no schema to specify the cardinality of the node in untyped XML.</span></span> <span data-ttu-id="93d50-159">若要指定節點 `d` 在其父節點 `b`下最多出現一次，請建立使用 SINGLETON 最佳化提示的選擇性 XML 索引，如下所示：</span><span class="sxs-lookup"><span data-stu-id="93d50-159">To specify that node `d` appears at most once under its parent node `b`, create a selective XML index that uses the SINGLETON optimization hint as follows:</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX example_sxi_US  
ON Tbl(xmlcol)  
FOR  
(  
node1223 = '/a/b/d' as SQL NVARCHAR(200) SINGLETON  
)  
```  
  

  
##  <a name="understanding-selective-xml-index-support-for-typed-xml"></a><a name="typed"></a> <span data-ttu-id="93d50-160">了解具類型之 XML 的選擇性 XML 索引支援</span><span class="sxs-lookup"><span data-stu-id="93d50-160">Understanding Selective XML Index support for typed XML</span></span>  
 <span data-ttu-id="93d50-161">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中具類型的 XML 是與特定 XML 文件相關聯的結構描述。</span><span class="sxs-lookup"><span data-stu-id="93d50-161">Typed XML in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is a schema associated with a given XML document.</span></span> <span data-ttu-id="93d50-162">結構描述會定義節點的整體文件結構和類型。</span><span class="sxs-lookup"><span data-stu-id="93d50-162">The schema defines overall document structure and types of nodes.</span></span> <span data-ttu-id="93d50-163">如果結構描述存在，選擇性 XML 索引會在使用者升級路徑時套用結構描述結構，因此不需要指定路徑的 XQUERY 類型。</span><span class="sxs-lookup"><span data-stu-id="93d50-163">If a schema exists, Selective XML Index applies the schema structure when the user promotes paths, so there is no need to specify the XQUERY types for paths.</span></span>  
  
 <span data-ttu-id="93d50-164">選擇性 XML 索引支援下列 XSD 類型：</span><span class="sxs-lookup"><span data-stu-id="93d50-164">Selective XML Index supports following XSD types:</span></span>  
  
-   <span data-ttu-id="93d50-165">**xs:anyUri**</span><span class="sxs-lookup"><span data-stu-id="93d50-165">**xs:anyUri**</span></span>  
  
-   <span data-ttu-id="93d50-166">**xs:boolean**</span><span class="sxs-lookup"><span data-stu-id="93d50-166">**xs:boolean**</span></span>  
  
-   <span data-ttu-id="93d50-167">**xs:date**</span><span class="sxs-lookup"><span data-stu-id="93d50-167">**xs:date**</span></span>  
  
-   <span data-ttu-id="93d50-168">**xs:dateTime**</span><span class="sxs-lookup"><span data-stu-id="93d50-168">**xs:dateTime**</span></span>  
  
-   <span data-ttu-id="93d50-169">**xs:day**</span><span class="sxs-lookup"><span data-stu-id="93d50-169">**xs:day**</span></span>  
  
-   <span data-ttu-id="93d50-170">**xs:decimal**</span><span class="sxs-lookup"><span data-stu-id="93d50-170">**xs:decimal**</span></span>  
  
-   <span data-ttu-id="93d50-171">**xs:double**</span><span class="sxs-lookup"><span data-stu-id="93d50-171">**xs:double**</span></span>  
  
-   <span data-ttu-id="93d50-172">**xs:float**</span><span class="sxs-lookup"><span data-stu-id="93d50-172">**xs:float**</span></span>  
  
-   <span data-ttu-id="93d50-173">**xs:int**</span><span class="sxs-lookup"><span data-stu-id="93d50-173">**xs:int**</span></span>  
  
-   <span data-ttu-id="93d50-174">**xs:integer**</span><span class="sxs-lookup"><span data-stu-id="93d50-174">**xs:integer**</span></span>  
  
-   <span data-ttu-id="93d50-175">**xs:language**</span><span class="sxs-lookup"><span data-stu-id="93d50-175">**xs:language**</span></span>  
  
-   <span data-ttu-id="93d50-176">**xs:long**</span><span class="sxs-lookup"><span data-stu-id="93d50-176">**xs:long**</span></span>  
  
-   <span data-ttu-id="93d50-177">**xs:name**</span><span class="sxs-lookup"><span data-stu-id="93d50-177">**xs:name**</span></span>  
  
-   <span data-ttu-id="93d50-178">**xs:NCName**</span><span class="sxs-lookup"><span data-stu-id="93d50-178">**xs:NCName**</span></span>  
  
-   <span data-ttu-id="93d50-179">**xs:negativeInteger**</span><span class="sxs-lookup"><span data-stu-id="93d50-179">**xs:negativeInteger**</span></span>  
  
-   <span data-ttu-id="93d50-180">**xs:nmtoken**</span><span class="sxs-lookup"><span data-stu-id="93d50-180">**xs:nmtoken**</span></span>  
  
-   <span data-ttu-id="93d50-181">**xs:nonNegativeInteger**</span><span class="sxs-lookup"><span data-stu-id="93d50-181">**xs:nonNegativeInteger**</span></span>  
  
-   <span data-ttu-id="93d50-182">**xs:nonPositiveInteger**</span><span class="sxs-lookup"><span data-stu-id="93d50-182">**xs:nonPositiveInteger**</span></span>  
  
-   <span data-ttu-id="93d50-183">**xs:positiveInteger**</span><span class="sxs-lookup"><span data-stu-id="93d50-183">**xs:positiveInteger**</span></span>  
  
-   <span data-ttu-id="93d50-184">**xs:qname**</span><span class="sxs-lookup"><span data-stu-id="93d50-184">**xs:qname**</span></span>  
  
-   <span data-ttu-id="93d50-185">**xs:short**</span><span class="sxs-lookup"><span data-stu-id="93d50-185">**xs:short**</span></span>  
  
-   <span data-ttu-id="93d50-186">**xs:string**</span><span class="sxs-lookup"><span data-stu-id="93d50-186">**xs:string**</span></span>  
  
-   <span data-ttu-id="93d50-187">**xs:time**</span><span class="sxs-lookup"><span data-stu-id="93d50-187">**xs:time**</span></span>  
  
-   <span data-ttu-id="93d50-188">**xs:token**</span><span class="sxs-lookup"><span data-stu-id="93d50-188">**xs:token**</span></span>  
  
-   <span data-ttu-id="93d50-189">**xs:unsignedByte**</span><span class="sxs-lookup"><span data-stu-id="93d50-189">**xs:unsignedByte**</span></span>  
  
-   <span data-ttu-id="93d50-190">**xs:unsignedInt**</span><span class="sxs-lookup"><span data-stu-id="93d50-190">**xs:unsignedInt**</span></span>  
  
-   <span data-ttu-id="93d50-191">**xs:unsignedLong**</span><span class="sxs-lookup"><span data-stu-id="93d50-191">**xs:unsignedLong**</span></span>  
  
-   <span data-ttu-id="93d50-192">**xs:unsignedShort**</span><span class="sxs-lookup"><span data-stu-id="93d50-192">**xs:unsignedShort**</span></span>  
  
 <span data-ttu-id="93d50-193">在擁有相關結構描述的文件上建立選擇性 XML 索引時，於建立或修改索引時指定 XQUERY 會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="93d50-193">When Selective XML Index is created over a document that has schema associated with it, specifying a XQUERY type at index creation or altering returns an error.</span></span> <span data-ttu-id="93d50-194">使用者可以在路徑升級部分使用 SQL 類型註解。</span><span class="sxs-lookup"><span data-stu-id="93d50-194">The user can use SQL type annotations in the path promotion part.</span></span> <span data-ttu-id="93d50-195">SQL 類型必須是來自結構描述中所定義 XSD 類型的有效轉換，否則會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="93d50-195">The SQL type must be a valid conversion from the XSD type defined in the schema, or an error is thrown.</span></span> <span data-ttu-id="93d50-196">所有具有適當 XSD 表示的 SQL 類型都可支援，但不包括日期/時間類型。</span><span class="sxs-lookup"><span data-stu-id="93d50-196">All SQL types that have adequate representation in XSD are supported, with an exception of date/time types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="93d50-197">如果選擇性 XML 索引路徑升級中指定的類型與 value() 方法傳回值相同，則會使用選擇性索引。</span><span class="sxs-lookup"><span data-stu-id="93d50-197">The selective index is used if the type specified in the Selective XML Index path promotion is the same as the value() method return value.</span></span>  
  
 <span data-ttu-id="93d50-198">下列最佳化提示可以搭配具類型的 XML 文件使用：</span><span class="sxs-lookup"><span data-stu-id="93d50-198">The following optimization hints can be used with typed XML documents:</span></span>  
  
-   <span data-ttu-id="93d50-199">node() 最佳化提示。</span><span class="sxs-lookup"><span data-stu-id="93d50-199">node() optimization hint.</span></span>  
  
-   <span data-ttu-id="93d50-200">MAXLENGTH 最佳化提示可以搭配 xs:string 類型用來縮短索引值。</span><span class="sxs-lookup"><span data-stu-id="93d50-200">MAXLENGTH optimization hint can be used with xs:string types to shorten the indexed value.</span></span>  
  
 <span data-ttu-id="93d50-201">如需最佳化提示的詳細資訊，請參閱 [指定最佳化提示](#hints)。</span><span class="sxs-lookup"><span data-stu-id="93d50-201">For more information about optimization hints, see [Specifying Optimization Hints](#hints).</span></span>  
  
##  <a name="specifying-paths"></a><a name="paths"></a> <span data-ttu-id="93d50-202">指定路徑</span><span class="sxs-lookup"><span data-stu-id="93d50-202">Specifying Paths</span></span>  
 <span data-ttu-id="93d50-203">選擇性 XML 索引可讓您僅索引與預期執行之查詢相關的預存 XML 資料中節點的子集。</span><span class="sxs-lookup"><span data-stu-id="93d50-203">A selective XML index lets you index only a subset of nodes from the stored XML data that are relevant for the queries that you expect to run.</span></span> <span data-ttu-id="93d50-204">如果相關節點的子集大幅少於 XML 文件中節點的總數，選擇性 XML 索引只會儲存相關的節點。</span><span class="sxs-lookup"><span data-stu-id="93d50-204">When the subset of relevant nodes is much smaller than the total number of nodes in the XML document, the selective XML index stores only the relevant nodes.</span></span> <span data-ttu-id="93d50-205">若要利用選擇性 XML 索引的優點，請識別要索引的正確節點子集。</span><span class="sxs-lookup"><span data-stu-id="93d50-205">To benefit from a selective XML index, identify the correct subset of nodes to index.</span></span>  
  
### <a name="choosing-the-nodes-to-index"></a><span data-ttu-id="93d50-206">選擇要索引的節點</span><span class="sxs-lookup"><span data-stu-id="93d50-206">Choosing the nodes to index</span></span>  
 <span data-ttu-id="93d50-207">您可以利用下列兩種簡單的原則，識別要加入至選擇性 XML 索引的正確節點子集。</span><span class="sxs-lookup"><span data-stu-id="93d50-207">You can use the following two simple principles to identify the correct subset of nodes to add to a selective XML index.</span></span>  
  
1.  <span data-ttu-id="93d50-208">**原則 1**：若要評估特定 XQuery 運算式，請為您需要檢查的所有節點編製索引。</span><span class="sxs-lookup"><span data-stu-id="93d50-208">**Principle 1**: To evaluate a given XQuery expression, index all nodes that you need to examine.</span></span>  
  
    -   <span data-ttu-id="93d50-209">索引在 XQuery 運算式中存在或使用其值的所有節點。</span><span class="sxs-lookup"><span data-stu-id="93d50-209">Index all nodes whose existence or value is used in the XQuery expression.</span></span>  
  
    -   <span data-ttu-id="93d50-210">索引 XQuery 運算式中套用 XQuery 述詞的所有節點。</span><span class="sxs-lookup"><span data-stu-id="93d50-210">Index all nodes in the XQuery expression on which XQuery predicates are applied.</span></span>  
  
     <span data-ttu-id="93d50-211">請考慮在本主題中 [範例 XML 文件](#sample) 上進行下列簡單的查詢：</span><span class="sxs-lookup"><span data-stu-id="93d50-211">Consider the following simple query over the [sample XML document](#sample) in this topic:</span></span>  
  
    ```sql  
    SELECT T.record FROM myXMLTable T  
    WHERE T.xmldata.exist('/a/b[./c = "43"]') = 1  
    ```  
  
     <span data-ttu-id="93d50-212">為了傳回滿足此查詢的 XML 執行個體，選擇性 XML 索引需要在每一個 XML 執行個體中檢查兩個節點：</span><span class="sxs-lookup"><span data-stu-id="93d50-212">In order to return the XML instances that satisfy this query, a selective XML index needs to examine two nodes in every XML instance:</span></span>  
  
    -   <span data-ttu-id="93d50-213">節點 `c`，因為它的值在 XQuery 運算式中使用。</span><span class="sxs-lookup"><span data-stu-id="93d50-213">Node `c`, because its value is used in the XQuery expression.</span></span>  
  
    -   <span data-ttu-id="93d50-214">節點 `b`，因為述詞會在 XQuery 運算式的節點`b` 上套用。</span><span class="sxs-lookup"><span data-stu-id="93d50-214">Node `b`, because a predicate is applied over node`b` in the XQuery expression.</span></span>  
  
2.  <span data-ttu-id="93d50-215">**原則 2**：為了達到最佳效能，請為評估指定 XQuery 運算式所需的所有節點編製索引。</span><span class="sxs-lookup"><span data-stu-id="93d50-215">**Principle 2**: For best performance, index all nodes that are required to evaluate a given XQuery expression.</span></span> <span data-ttu-id="93d50-216">如果您只索引部分節點，則選擇性 XML 索引可改善僅包括索引節點的子運算式評估。</span><span class="sxs-lookup"><span data-stu-id="93d50-216">If you index only some of the nodes, then the selective XML index improves the evaluation of sub-expressions that include only indexed nodes.</span></span>  
  
 <span data-ttu-id="93d50-217">若要改善上面所示 SELECT 陳述式的效能，您可以建立下列選擇性 XML 索引：</span><span class="sxs-lookup"><span data-stu-id="93d50-217">To improve the performance of the SELECT statement shown above, you can create the following selective XML index:</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX simple_sxi  
ON Tbl(xmlcol)  
FOR  
(  
    path123 =  '/a/b',  
    path124 =  '/a/b/c'  
)  
```  
  
### <a name="indexing-identical-paths"></a><span data-ttu-id="93d50-218">索引相同路徑</span><span class="sxs-lookup"><span data-stu-id="93d50-218">Indexing identical paths</span></span>  
 <span data-ttu-id="93d50-219">您無法將相同路徑升級為路徑名稱不同的相同類型。</span><span class="sxs-lookup"><span data-stu-id="93d50-219">You cannot promote identical paths as the same data type under different path names.</span></span> <span data-ttu-id="93d50-220">例如，下列查詢會引發錯誤，因為 `pathOne` 和 `pathTwo` 相同：</span><span class="sxs-lookup"><span data-stu-id="93d50-220">For example, the following query raises an error, because `pathOne` and `pathTwo` are identical:</span></span>  
  
```sql  
CREATE SELECTIVE INDEX test_simple_sxi ON T1(xmlCol)  
FOR  
(  
    pathOne = 'book/authors/authorID' AS XQUERY 'xs:string',  
    pathTwo = 'book/authors/authorID' AS XQUERY 'xs:string'  
)  
```  
  
 <span data-ttu-id="93d50-221">不過，您可以將相同路徑升級為具有不同名稱的不同資料類型。</span><span class="sxs-lookup"><span data-stu-id="93d50-221">However, you can promote identical paths as different data types with different names.</span></span> <span data-ttu-id="93d50-222">例如，現在可接受下列查詢，因為資料類型不同：</span><span class="sxs-lookup"><span data-stu-id="93d50-222">For example, the following query is now acceptable, because the data types are different:</span></span>  
  
```sql  
CREATE SELECTIVE INDEX test_simple_sxi ON T1(xmlCol)  
FOR  
(  
    pathOne = 'book/authors/authorID' AS XQUERY 'xs:double',  
    pathTwo = 'book/authors/authorID' AS XQUERY 'xs:string'  
)  
```  
  
### <a name="examples"></a><span data-ttu-id="93d50-223">範例</span><span class="sxs-lookup"><span data-stu-id="93d50-223">Examples</span></span>  
 <span data-ttu-id="93d50-224">以下提供一些針對不同 XQuery 類型選取要索引之正確節點的其他範例。</span><span class="sxs-lookup"><span data-stu-id="93d50-224">Here are some additional examples of selecting the correct nodes to index for different XQuery types.</span></span>  
  
 <span data-ttu-id="93d50-225">**範例 1**</span><span class="sxs-lookup"><span data-stu-id="93d50-225">**Example 1**</span></span>  
  
 <span data-ttu-id="93d50-226">以下是使用 exist() 方法的簡單 XQuery：</span><span class="sxs-lookup"><span data-stu-id="93d50-226">Here is a simple XQuery that uses the exist() method:</span></span>  
  
```sql  
SELECT T.record FROM myXMLTable T  
WHERE T.xmldata.exist('/a/b/c/d/e/h') = 1  
```  
  
 <span data-ttu-id="93d50-227">下表顯示應索引的節點，以便讓這個查詢使用選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="93d50-227">The following table shows the nodes that should be indexed to let this query use the selective XML index.</span></span>  
  
|<span data-ttu-id="93d50-228">要包含在索引中的節點</span><span class="sxs-lookup"><span data-stu-id="93d50-228">Node to include in the index</span></span>|<span data-ttu-id="93d50-229">索引此節點的原因</span><span class="sxs-lookup"><span data-stu-id="93d50-229">Reason for indexing this node</span></span>|  
|----------------------------------|-----------------------------------|  
|<span data-ttu-id="93d50-230">**/a/b/c/d/e/h**</span><span class="sxs-lookup"><span data-stu-id="93d50-230">**/a/b/c/d/e/h**</span></span>|<span data-ttu-id="93d50-231">會在 exist() 方法中評估節點 `h` 是否存在。</span><span class="sxs-lookup"><span data-stu-id="93d50-231">The existence of node `h` is evaluated in the exist() method.</span></span>|  
  
 <span data-ttu-id="93d50-232">**範例 2**</span><span class="sxs-lookup"><span data-stu-id="93d50-232">**Example 2**</span></span>  
  
 <span data-ttu-id="93d50-233">以下是前一個 XQuery 較為複雜的變化，其中會套用述詞：</span><span class="sxs-lookup"><span data-stu-id="93d50-233">Here is a more complex variation of the previous XQuery, with a predicate applied:</span></span>  
  
```sql  
SELECT T.record FROM myXMLTable T  
WHERE T.xmldata.exist('/a/b/c/d/e[./f = "SQL"]') = 1  
```  
  
 <span data-ttu-id="93d50-234">下表顯示應索引的節點，以便讓這個查詢使用選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="93d50-234">The following table shows the nodes that should be indexed to let this query use the selective XML index.</span></span>  
  
|<span data-ttu-id="93d50-235">要包含在索引中的節點</span><span class="sxs-lookup"><span data-stu-id="93d50-235">Node to include in the index</span></span>|<span data-ttu-id="93d50-236">索引此節點的原因</span><span class="sxs-lookup"><span data-stu-id="93d50-236">Reason for indexing this node</span></span>|  
|----------------------------------|-----------------------------------|  
|<span data-ttu-id="93d50-237">**/a/b/c/d/e**</span><span class="sxs-lookup"><span data-stu-id="93d50-237">**/a/b/c/d/e**</span></span>|<span data-ttu-id="93d50-238">述詞會套用在節點 `e`上。</span><span class="sxs-lookup"><span data-stu-id="93d50-238">A predicate is applied over node `e`.</span></span>|  
|<span data-ttu-id="93d50-239">**/a/b/c/d/e/f**</span><span class="sxs-lookup"><span data-stu-id="93d50-239">**/a/b/c/d/e/f**</span></span>|<span data-ttu-id="93d50-240">節點 `f` 的值會在述詞內評估。</span><span class="sxs-lookup"><span data-stu-id="93d50-240">The value of node `f` is evaluated inside the predicate.</span></span>|  
  
 <span data-ttu-id="93d50-241">**範例 3**</span><span class="sxs-lookup"><span data-stu-id="93d50-241">**Example 3**</span></span>  
  
 <span data-ttu-id="93d50-242">以下查詢較為複雜，會使用 value() 子句：</span><span class="sxs-lookup"><span data-stu-id="93d50-242">Here is a more complex query with a value() clause:</span></span>  
  
```sql  
SELECT T.record,  
    T.xmldata.value('(/a/b/c/d/e[./f = "SQL"]/g)[1]', 'nvarchar(100)')  
FROM myXMLTable T  
```  
  
 <span data-ttu-id="93d50-243">下表顯示應索引的節點，以便讓這個查詢使用選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="93d50-243">The following table shows the nodes that should be indexed to let this query use the selective XML index.</span></span>  
  
|<span data-ttu-id="93d50-244">要包含在索引中的節點</span><span class="sxs-lookup"><span data-stu-id="93d50-244">Node to include in the index</span></span>|<span data-ttu-id="93d50-245">索引此節點的原因</span><span class="sxs-lookup"><span data-stu-id="93d50-245">Reason for indexing this node</span></span>|  
|----------------------------------|-----------------------------------|  
|<span data-ttu-id="93d50-246">**/a/b/c/d/e**</span><span class="sxs-lookup"><span data-stu-id="93d50-246">**/a/b/c/d/e**</span></span>|<span data-ttu-id="93d50-247">述詞會套用在節點 `e`上。</span><span class="sxs-lookup"><span data-stu-id="93d50-247">A predicate is applied over node `e`.</span></span>|  
|<span data-ttu-id="93d50-248">**/a/b/c/d/e/f**</span><span class="sxs-lookup"><span data-stu-id="93d50-248">**/a/b/c/d/e/f**</span></span>|<span data-ttu-id="93d50-249">節點 `f` 的值會在述詞內評估。</span><span class="sxs-lookup"><span data-stu-id="93d50-249">The value of node `f` is evaluated inside the predicate.</span></span>|  
|<span data-ttu-id="93d50-250">**/a/b/c/d/e/g**</span><span class="sxs-lookup"><span data-stu-id="93d50-250">**/a/b/c/d/e/g**</span></span>|<span data-ttu-id="93d50-251">節點 `g` 的值是由 value() 方法傳回。</span><span class="sxs-lookup"><span data-stu-id="93d50-251">The value of node `g` is returned by the value() method.</span></span>|  
  
 <span data-ttu-id="93d50-252">**範例 4**</span><span class="sxs-lookup"><span data-stu-id="93d50-252">**Example 4**</span></span>  
  
 <span data-ttu-id="93d50-253">以下是在 exist() 子句內使用 FLWOR 子句的查詢</span><span class="sxs-lookup"><span data-stu-id="93d50-253">Here is a query that uses a FLWOR clause inside an exist() clause.</span></span> <span data-ttu-id="93d50-254">(FLWOR 這個名稱來自五個子句，這五個子句構成 XQuery FLWOR 運算式：for、let、where、order by 和 return)。</span><span class="sxs-lookup"><span data-stu-id="93d50-254">(The name FLWOR comes from the five clauses that can make up an XQuery FLWOR expression: for, let, where, order by, and return.)</span></span>  
  
```sql  
SELECT T.record FROM myXMLTable T  
WHERE T.xmldata.exist('  
  For $x in /a/b/c/d/e  
  Where $x/f = "SQL"  
  Return $x/g  
') = 1  
```  
  
 <span data-ttu-id="93d50-255">下表顯示應索引的節點，以便讓這個查詢使用選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="93d50-255">The following table shows the nodes that should be indexed to let this query use the selective XML index.</span></span>  
  
|<span data-ttu-id="93d50-256">要包含在索引中的節點</span><span class="sxs-lookup"><span data-stu-id="93d50-256">Node to include in the index</span></span>|<span data-ttu-id="93d50-257">索引此節點的原因</span><span class="sxs-lookup"><span data-stu-id="93d50-257">Reason for indexing this node</span></span>|  
|----------------------------------|-----------------------------------|  
|<span data-ttu-id="93d50-258">**/a/b/c/d/e**</span><span class="sxs-lookup"><span data-stu-id="93d50-258">**/a/b/c/d/e**</span></span>|<span data-ttu-id="93d50-259">FLWOR 子句中會評估節點 `e` 是否存在。</span><span class="sxs-lookup"><span data-stu-id="93d50-259">The existence of node `e` is evaluated in the FLWOR clause.</span></span>|  
|<span data-ttu-id="93d50-260">**/a/b/c/d/e/f**</span><span class="sxs-lookup"><span data-stu-id="93d50-260">**/a/b/c/d/e/f**</span></span>|<span data-ttu-id="93d50-261">節點 `f` 的值會在 FLWOR 子句中評估。</span><span class="sxs-lookup"><span data-stu-id="93d50-261">The value of node `f` is evaluated in the FLWOR clause.</span></span>|  
|<span data-ttu-id="93d50-262">**/a/b/c/d/e/g**</span><span class="sxs-lookup"><span data-stu-id="93d50-262">**/a/b/c/d/e/g**</span></span>|<span data-ttu-id="93d50-263">exist() 方法會評估節點 `g` 是否存在。</span><span class="sxs-lookup"><span data-stu-id="93d50-263">The existence of node `g` is evaluated by the exist() method.</span></span>|  
  

  
##  <a name="specifying-optimization-hints"></a><a name="hints"></a> <span data-ttu-id="93d50-264">指定最佳化提示</span><span class="sxs-lookup"><span data-stu-id="93d50-264">Specifying Optimization Hints</span></span>  
 <span data-ttu-id="93d50-265">您可以使用選用的最佳化提示，為藉由選擇性 XML 索引進行索引的節點指定其他對應詳細資料。</span><span class="sxs-lookup"><span data-stu-id="93d50-265">You can use optional optimization hints to specify additional mapping details for a node indexed by a selective XML index.</span></span> <span data-ttu-id="93d50-266">例如，您可以指定節點的資料類型和基數，以及有關資料結構的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="93d50-266">For example, you can specify the data type and cardinality of the node, and certain information about the structure of the data.</span></span> <span data-ttu-id="93d50-267">這項額外資訊可提供更佳的對應。</span><span class="sxs-lookup"><span data-stu-id="93d50-267">This additional information supports better mapping.</span></span> <span data-ttu-id="93d50-268">此外還能獲得效能提升和 (或) 節省儲存空間的結果。</span><span class="sxs-lookup"><span data-stu-id="93d50-268">It also results in improvements in performance or savings in storage, or both.</span></span>  
  
 <span data-ttu-id="93d50-269">最佳化提示是選擇性的用法。</span><span class="sxs-lookup"><span data-stu-id="93d50-269">The use of optimization hints is optional.</span></span> <span data-ttu-id="93d50-270">您可以一律接受預設對應，預設對應雖然可靠，但不一定能提供最佳效能和儲存。</span><span class="sxs-lookup"><span data-stu-id="93d50-270">You can always accept the default mappings, which are reliable but may not provide optimal performance and storage.</span></span>  
  
 <span data-ttu-id="93d50-271">某些最佳化提示 (例如，SINGLETON 提示) 會對資料形成條件約束。</span><span class="sxs-lookup"><span data-stu-id="93d50-271">Some optimization hints - for example, the SINGLETON hint - introduce constraints over your data.</span></span> <span data-ttu-id="93d50-272">在某些情況下，如果不符合這些條件約束，可能會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="93d50-272">In some cases, errors may be raised when those constraints are not met.</span></span>  
  
### <a name="benefits-of-optimization-hints"></a><span data-ttu-id="93d50-273">最佳化提示的優點</span><span class="sxs-lookup"><span data-stu-id="93d50-273">Benefits of Optimization Hints</span></span>  
 <span data-ttu-id="93d50-274">下表會識別支援更有效率的儲存或提升效能的最佳化提示。</span><span class="sxs-lookup"><span data-stu-id="93d50-274">The following table identifies the optimization hints that support more efficient storage or improved performance.</span></span>  
  
|<span data-ttu-id="93d50-275">最佳化提示</span><span class="sxs-lookup"><span data-stu-id="93d50-275">Optimization hint</span></span>|<span data-ttu-id="93d50-276">更有效率的儲存</span><span class="sxs-lookup"><span data-stu-id="93d50-276">More efficient storage</span></span>|<span data-ttu-id="93d50-277">提升效能</span><span class="sxs-lookup"><span data-stu-id="93d50-277">Improved performance</span></span>|  
|-----------------------|----------------------------|--------------------------|  
|<span data-ttu-id="93d50-278">**node()**</span><span class="sxs-lookup"><span data-stu-id="93d50-278">**node()**</span></span>|<span data-ttu-id="93d50-279">是</span><span class="sxs-lookup"><span data-stu-id="93d50-279">Yes</span></span>|<span data-ttu-id="93d50-280">否</span><span class="sxs-lookup"><span data-stu-id="93d50-280">No</span></span>|  
|<span data-ttu-id="93d50-281">**SINGLETON**</span><span class="sxs-lookup"><span data-stu-id="93d50-281">**SINGLETON**</span></span>|<span data-ttu-id="93d50-282">否</span><span class="sxs-lookup"><span data-stu-id="93d50-282">No</span></span>|<span data-ttu-id="93d50-283">是</span><span class="sxs-lookup"><span data-stu-id="93d50-283">Yes</span></span>|  
|<span data-ttu-id="93d50-284">**DATA TYPE**</span><span class="sxs-lookup"><span data-stu-id="93d50-284">**DATA TYPE**</span></span>|<span data-ttu-id="93d50-285">是</span><span class="sxs-lookup"><span data-stu-id="93d50-285">Yes</span></span>|<span data-ttu-id="93d50-286">是</span><span class="sxs-lookup"><span data-stu-id="93d50-286">Yes</span></span>|  
|<span data-ttu-id="93d50-287">**MAXLENGTH**</span><span class="sxs-lookup"><span data-stu-id="93d50-287">**MAXLENGTH**</span></span>|<span data-ttu-id="93d50-288">是</span><span class="sxs-lookup"><span data-stu-id="93d50-288">Yes</span></span>|<span data-ttu-id="93d50-289">是</span><span class="sxs-lookup"><span data-stu-id="93d50-289">Yes</span></span>|  
  
### <a name="optimization-hints-and-data-types"></a><span data-ttu-id="93d50-290">最佳化提示和資料類型</span><span class="sxs-lookup"><span data-stu-id="93d50-290">Optimization Hints and Data Types</span></span>  
 <span data-ttu-id="93d50-291">您可以索引 XQuery 資料類型或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型的節點。</span><span class="sxs-lookup"><span data-stu-id="93d50-291">You can index nodes as XQuery data types or as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span> <span data-ttu-id="93d50-292">下表顯示每一種資料類型支援的最佳化提示。</span><span class="sxs-lookup"><span data-stu-id="93d50-292">The following table shows which optimization hints are supported with each data type.</span></span>  
  
|<span data-ttu-id="93d50-293">最佳化提示</span><span class="sxs-lookup"><span data-stu-id="93d50-293">Optimization hint</span></span>|<span data-ttu-id="93d50-294">XQuery 資料類型</span><span class="sxs-lookup"><span data-stu-id="93d50-294">XQuery data types</span></span>|<span data-ttu-id="93d50-295">SQL 資料類型</span><span class="sxs-lookup"><span data-stu-id="93d50-295">SQL data types</span></span>|  
|-----------------------|-----------------------|--------------------|  
|<span data-ttu-id="93d50-296">**node()**</span><span class="sxs-lookup"><span data-stu-id="93d50-296">**node()**</span></span>|<span data-ttu-id="93d50-297">是</span><span class="sxs-lookup"><span data-stu-id="93d50-297">Yes</span></span>|<span data-ttu-id="93d50-298">否</span><span class="sxs-lookup"><span data-stu-id="93d50-298">No</span></span>|  
|<span data-ttu-id="93d50-299">**SINGLETON**</span><span class="sxs-lookup"><span data-stu-id="93d50-299">**SINGLETON**</span></span>|<span data-ttu-id="93d50-300">是</span><span class="sxs-lookup"><span data-stu-id="93d50-300">Yes</span></span>|<span data-ttu-id="93d50-301">是</span><span class="sxs-lookup"><span data-stu-id="93d50-301">Yes</span></span>|  
|<span data-ttu-id="93d50-302">**DATA TYPE**</span><span class="sxs-lookup"><span data-stu-id="93d50-302">**DATA TYPE**</span></span>|<span data-ttu-id="93d50-303">是</span><span class="sxs-lookup"><span data-stu-id="93d50-303">Yes</span></span>|<span data-ttu-id="93d50-304">否</span><span class="sxs-lookup"><span data-stu-id="93d50-304">No</span></span>|  
|<span data-ttu-id="93d50-305">**MAXLENGTH**</span><span class="sxs-lookup"><span data-stu-id="93d50-305">**MAXLENGTH**</span></span>|<span data-ttu-id="93d50-306">是</span><span class="sxs-lookup"><span data-stu-id="93d50-306">Yes</span></span>|<span data-ttu-id="93d50-307">否</span><span class="sxs-lookup"><span data-stu-id="93d50-307">No</span></span>|  
  
### <a name="node-optimization-hint"></a><span data-ttu-id="93d50-308">node() 最佳化提示</span><span class="sxs-lookup"><span data-stu-id="93d50-308">node() optimization hint</span></span>  
 <span data-ttu-id="93d50-309">適用於：XQuery 資料類型</span><span class="sxs-lookup"><span data-stu-id="93d50-309">Applies to: XQuery data types</span></span>  
  
 <span data-ttu-id="93d50-310">您可以使用 node() 最佳化指定評估一般查詢時不需要其值的節點。</span><span class="sxs-lookup"><span data-stu-id="93d50-310">You can use the node() optimization to specify a node whose value is not required to evaluate the typical query.</span></span> <span data-ttu-id="93d50-311">這個提示可在一般查詢只需評估節點是否存在時，減少儲存需求</span><span class="sxs-lookup"><span data-stu-id="93d50-311">This hint reduces storage requirements when the typical query only has to evaluate the existence of the node.</span></span> <span data-ttu-id="93d50-312">(根據預設，選擇性 XML 索引會儲存所有已升級節點的值，但是不包括複雜的節點類型)。</span><span class="sxs-lookup"><span data-stu-id="93d50-312">(By default, a selective XML index stores the value for all promoted nodes, except complex node types.)</span></span>  
  
 <span data-ttu-id="93d50-313">請考慮下列範例：</span><span class="sxs-lookup"><span data-stu-id="93d50-313">Consider the following example:</span></span>  
  
```sql  
SELECT T.record FROM myXMLTable T  
WHERE T.xmldata.exist('/a/b[./c=5]') = 1  
```  
  
 <span data-ttu-id="93d50-314">若要使用選擇性 XML 索引評估此查詢，請升級節點 `b` 和 `c`。</span><span class="sxs-lookup"><span data-stu-id="93d50-314">To use a selective XML index to evaluate this query, promote nodes `b` and `c`.</span></span> <span data-ttu-id="93d50-315">不過，由於不需要節點 `b` 的值，因此您可以使用下列語法的 node() 提示：</span><span class="sxs-lookup"><span data-stu-id="93d50-315">However, since the value of node `b` is not required, you can use the node() hint with the following syntax:</span></span>  
  
 `/a/b/ as node()`  
  
 <span data-ttu-id="93d50-316">如果查詢需要已利用 node() 提示索引之節點的值，則無法使用選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="93d50-316">If a query requires the value of a node that has been indexed with the node() hint, then the selective XML index cannot be used.</span></span>  
  
### <a name="singleton-optimization-hint"></a><span data-ttu-id="93d50-317">SINGLETON 最佳化提示</span><span class="sxs-lookup"><span data-stu-id="93d50-317">SINGLETON optimization hint</span></span>  
 <span data-ttu-id="93d50-318">適用於：XQuery 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型</span><span class="sxs-lookup"><span data-stu-id="93d50-318">Applies to: XQuery or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types</span></span>  
  
 <span data-ttu-id="93d50-319">SINGLETON 最佳化提示會指定節點的基數。</span><span class="sxs-lookup"><span data-stu-id="93d50-319">The SINGLETON optimization hint specifies the cardinality of a node.</span></span> <span data-ttu-id="93d50-320">此提示可改善查詢效能，因為事先就已知道節點最多只會在其父系或上階內出現一次。</span><span class="sxs-lookup"><span data-stu-id="93d50-320">This hint improves query performance since it is known in advance that a node appears at most one time within its parent or ancestor.</span></span>  
  
 <span data-ttu-id="93d50-321">請考慮本主題中的 [範例 XML 文件](#sample) 。</span><span class="sxs-lookup"><span data-stu-id="93d50-321">Consider the [sample XML document](#sample) in this topic.</span></span>  
  
 <span data-ttu-id="93d50-322">若要使用選擇性 XML 索引查詢此文件，您可以針對節點 `d` 指定 SINGLETON 提示，因為它最多只會在其父系內出現一次。</span><span class="sxs-lookup"><span data-stu-id="93d50-322">To use a selective XML index to query this document, you can specify the SINGLETON hint for node `d` since it appears at most one time within its parent.</span></span>  
  
 <span data-ttu-id="93d50-323">如果已指定 SINGLETON 提示，但節點在其父系或上階內不只出現一次，則會在您建立索引 (針對現有資料) 或執行查詢 (針對新資料) 時引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="93d50-323">If the SINGLETON hint has been specified, but a node appears more than one time within its parent or ancestor, then an error is raised when you create the index (for existing data) or when you run a query (for new data).</span></span>  
  
### <a name="data-type-optimization-hint"></a><span data-ttu-id="93d50-324">DATA TYPE 最佳化提示</span><span class="sxs-lookup"><span data-stu-id="93d50-324">DATA TYPE optimization hint</span></span>  
 <span data-ttu-id="93d50-325">適用於：XQuery 資料類型</span><span class="sxs-lookup"><span data-stu-id="93d50-325">Applies to: XQuery data types</span></span>  
  
 <span data-ttu-id="93d50-326">DATA TYPE 最佳化提示可讓您針對索引的節點指定 XQuery 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="93d50-326">The DATA TYPE optimization hint lets you specify an XQuery or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for the indexed node.</span></span> <span data-ttu-id="93d50-327">資料類型用於對應索引節點的選擇性 XML 索引之資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="93d50-327">The data type is used for the column in the data table of the selective XML index that corresponds to the indexed node.</span></span>  
  
 <span data-ttu-id="93d50-328">將現有值轉換成指定的資料類型失敗時，插入作業 (插入索引內) 不會失敗；但是索引的資料表中會插入 null 值。</span><span class="sxs-lookup"><span data-stu-id="93d50-328">When casting an existing value to the specified data type fails, the insert operation (into the index) does not fail; however, a null value is inserted into the data table of the index.</span></span>  
  
### <a name="maxlength-optimization-hint"></a><span data-ttu-id="93d50-329">MAXLENGTH 最佳化提示</span><span class="sxs-lookup"><span data-stu-id="93d50-329">MAXLENGTH optimization hint</span></span>  
 <span data-ttu-id="93d50-330">適用於：XQuery 資料類型</span><span class="sxs-lookup"><span data-stu-id="93d50-330">Applies to: XQuery data types</span></span>  
  
 <span data-ttu-id="93d50-331">MAXLENGTH 最佳化提示可讓您限制 xs:string 資料的長度。</span><span class="sxs-lookup"><span data-stu-id="93d50-331">The MAXLENGTH optimization hint lets you limit the length of xs:string data.</span></span> <span data-ttu-id="93d50-332">MAXLENGTH 與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型無關，因為您是在指定 VARCHAR 或 NVARCHAR 資料類型時指定長度。</span><span class="sxs-lookup"><span data-stu-id="93d50-332">MAXLENGTH is not relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types since you specify the length when you specify the VARCHAR or NVARCHAR date types.</span></span>  
  
 <span data-ttu-id="93d50-333">如果現有的字串長度超過指定的 MAXLENGTH，則將該值插入索引中的作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="93d50-333">When an existing string is longer than the specified MAXLENGTH, then inserting that value into the index fails.</span></span>  
  

  
##  <a name="sample-xml-document-for-examples"></a><a name="sample"></a> <span data-ttu-id="93d50-334">做為範例的範例 XML 文件</span><span class="sxs-lookup"><span data-stu-id="93d50-334">Sample XML Document for Examples</span></span>  
 <span data-ttu-id="93d50-335">下列範例 XML 文件會在本主題的範例中參考：</span><span class="sxs-lookup"><span data-stu-id="93d50-335">The following sample XML document is referenced in the examples in this topic:</span></span>  
  
```xml  
<a>  
    <b>  
         <c atc="aa">10</c>  
         <c atc="bb">15</c>  
         <d atd1="dd" atd2="ddd">md </d>  
    </b>  
     <b>  
        <c></c>  
        <c atc="">117</c>  
     </b>  
</a>  
```  
  

  
## <a name="see-also"></a><span data-ttu-id="93d50-336">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93d50-336">See Also</span></span>  
 <span data-ttu-id="93d50-337">[選擇性 XML 索引 &#40;SXI&#41;](../xml/selective-xml-indexes-sxi.md) </span><span class="sxs-lookup"><span data-stu-id="93d50-337">[Selective XML Indexes &#40;SXI&#41;](../xml/selective-xml-indexes-sxi.md) </span></span>  
 [<span data-ttu-id="93d50-338">建立、修改和卸除選擇性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="93d50-338">Create, Alter, and Drop Selective XML Indexes</span></span>](../xml/create-alter-and-drop-selective-xml-indexes.md)  
  
  
