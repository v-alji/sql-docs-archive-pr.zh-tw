---
title: XML 索引 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- removing indexes
- deleting indexes
- secondary indexes [XML in SQL Server]
- xml data type [SQL Server], indexes
- dropping indexes
- PATH index
- DROP_EXISTING clause
- XML [SQL Server], indexes
- primary indexes [XML in SQL Server]
- indexes [SQL Server], XML
- XML indexes [SQL Server], secondary
- BLOBs, XML indexes
- disabling indexes
- XML indexes [SQL Server], modifying
- XML indexes [SQL Server]
- XML indexes [SQL Server], primary
- modifying indexes
- XML indexes [SQL Server], dropping
- VALUE index
- XML indexes [SQL Server], xml data type
- PROPERTY index
- XML indexes [SQL Server], creating
ms.assetid: f5c9209d-b3f3-4543-b30b-01365a5e7333
author: rothja
ms.author: jroth
ms.openlocfilehash: bf9a33bc18790bf8821d778746a708f78bbb3d8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597677"
---
# <a name="xml-indexes-sql-server"></a><span data-ttu-id="4790a-102">XML 索引 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4790a-102">XML Indexes (SQL Server)</span></span>
  <span data-ttu-id="4790a-103">XML 索引可建立在 `xml` 資料類型資料行上。</span><span class="sxs-lookup"><span data-stu-id="4790a-103">XML indexes can be created on `xml` data type columns.</span></span> <span data-ttu-id="4790a-104">它們會在資料行中為整個 XML 執行個體的所有標記、值和路徑編制索引，進而提高查詢效能。</span><span class="sxs-lookup"><span data-stu-id="4790a-104">They index all tags, values and paths over the XML instances in the column and benefit query performance.</span></span> <span data-ttu-id="4790a-105">在下列情況下，您的應用程式可從 XML 索引獲益：</span><span class="sxs-lookup"><span data-stu-id="4790a-105">Your application may benefit from an XML index in the following situations:</span></span>  
  
-   <span data-ttu-id="4790a-106">在您的工作負載中，經常會查詢 XML 資料行。</span><span class="sxs-lookup"><span data-stu-id="4790a-106">Queries on XML columns are common in your workload.</span></span> <span data-ttu-id="4790a-107">必須將資料修改期間的 XML 索引維護成本納入考量。</span><span class="sxs-lookup"><span data-stu-id="4790a-107">XML index maintenance cost during data modification must be considered.</span></span>  
  
-   <span data-ttu-id="4790a-108">您的 XML 值相對較大，而所擷取的部份相對較小。</span><span class="sxs-lookup"><span data-stu-id="4790a-108">Your XML values are relatively large and the retrieved parts are relatively small.</span></span> <span data-ttu-id="4790a-109">建立索引可避免在執行階段剖析整份資料，並有助於索引查閱，增進查詢處理的效率。</span><span class="sxs-lookup"><span data-stu-id="4790a-109">Building the index avoids parsing the whole data at run time and benefits index lookups for efficient query processing.</span></span>  
  
 <span data-ttu-id="4790a-110">XML 索引可分成下列類別：</span><span class="sxs-lookup"><span data-stu-id="4790a-110">XML indexes fall into the following categories:</span></span>  
  
-   <span data-ttu-id="4790a-111">主要 XML 索引</span><span class="sxs-lookup"><span data-stu-id="4790a-111">Primary XML index</span></span>  
  
-   <span data-ttu-id="4790a-112">次要 XML 索引</span><span class="sxs-lookup"><span data-stu-id="4790a-112">Secondary XML index</span></span>  
  
 <span data-ttu-id="4790a-113">在 `xml` 類型資料行上的第一個索引必須是主要的 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="4790a-113">The first index on the `xml` type column must be the primary XML index.</span></span> <span data-ttu-id="4790a-114">使用主要 XML 索引時，可支援下列次要索引類型：PATH、VALUE 和 PROPERTY。</span><span class="sxs-lookup"><span data-stu-id="4790a-114">Using the primary XML index, the following types of secondary indexes are supported: PATH, VALUE, and PROPERTY.</span></span> <span data-ttu-id="4790a-115">視查詢類型而定，這些次要索引可協助改善查詢效能。</span><span class="sxs-lookup"><span data-stu-id="4790a-115">Depending on the type of queries, these secondary indexes might help improve query performance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4790a-116">除非您已正確設定資料庫選項來處理 `xml` 資料類型一起運作，否則無法建立或修改 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="4790a-116">You cannot create or modify an XML index unless the database options are set correctly for working with the `xml` data type.</span></span> <span data-ttu-id="4790a-117">如需詳細資訊，請參閱 [使用 XML 資料行進行全文檢索搜尋](use-full-text-search-with-xml-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="4790a-117">For more information, see [Use Full-Text Search with XML Columns](use-full-text-search-with-xml-columns.md).</span></span>  
  
 <span data-ttu-id="4790a-118">XML 執行個體是以大型二進位物件 (BLOB) 儲存在 `xml` 類型資料行中。</span><span class="sxs-lookup"><span data-stu-id="4790a-118">XML instances are stored in `xml` type columns as large binary objects (BLOBs).</span></span> <span data-ttu-id="4790a-119">這些 XML 執行個體可以是大型的，而且所儲存之 `xml` 資料類型執行個體的二進位表示法最多可達 2 GB。</span><span class="sxs-lookup"><span data-stu-id="4790a-119">These XML instances can be large, and the stored binary representation of `xml` data type instances can be up to 2 GB.</span></span> <span data-ttu-id="4790a-120">如果沒有索引，這些二進位大型物件就會在執行階段切割，以便評估查詢。</span><span class="sxs-lookup"><span data-stu-id="4790a-120">Without an index, these binary large objects are shredded at run time to evaluate a query.</span></span> <span data-ttu-id="4790a-121">這項切割作業可能會很費時。</span><span class="sxs-lookup"><span data-stu-id="4790a-121">This shredding can be time-consuming.</span></span> <span data-ttu-id="4790a-122">例如，請考慮下列查詢：</span><span class="sxs-lookup"><span data-stu-id="4790a-122">For example, consider the following query:</span></span>  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS "PD")  
  
SELECT CatalogDescription.query('  
  /PD:ProductDescription/PD:Summary  
') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist ('/PD:ProductDescription/@ProductModelID[.="19"]') = 1  
```  
  
 <span data-ttu-id="4790a-123">為了選取符合 `WHERE` 子句中條件的 XML 執行個體，在執行階段會切割 `Production.ProductModel` 資料表之每個資料列中的 XML 二進位大型物件 (BLOB)。</span><span class="sxs-lookup"><span data-stu-id="4790a-123">To select the XML instances that satisfy the condition in the `WHERE` clause, the XML binary large object (BLOB) in each row of table `Production.ProductModel` is shredded at run time.</span></span> <span data-ttu-id="4790a-124">然後，便評估 `(/PD:ProductDescription/@ProductModelID[.="19"]`方法中的運算式 `exist()` )。</span><span class="sxs-lookup"><span data-stu-id="4790a-124">Then, the expression `(/PD:ProductDescription/@ProductModelID[.="19"]`) in the `exist()` method is evaluated.</span></span> <span data-ttu-id="4790a-125">此執行階段的切割可能會非常費時，端視資料行中所儲存的執行個體之大小與數目而定。</span><span class="sxs-lookup"><span data-stu-id="4790a-125">This run-time shredding can be costly, depending on the size and number of instances stored in the column.</span></span>  
  
 <span data-ttu-id="4790a-126">如果查詢 XML 二進位大型物件 (BLOB) 常在應用程式環境中發生，它將可協助索引 `xml` 類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="4790a-126">If querying XML binary large objects (BLOBs) is common in your application environment, it helps to index the `xml` type columns.</span></span> <span data-ttu-id="4790a-127">但是，在修改資料期間會有維護索引的相關成本。</span><span class="sxs-lookup"><span data-stu-id="4790a-127">However, there is a cost associated with maintaining the index during data modification.</span></span>  
  
## <a name="primary-xml-index"></a><span data-ttu-id="4790a-128">主要 XML 索引</span><span class="sxs-lookup"><span data-stu-id="4790a-128">Primary XML Index</span></span>  
 <span data-ttu-id="4790a-129">主要 XML 索引會在 XML 資料行中檢索 XML 執行個體內的所有標記、值與路徑。</span><span class="sxs-lookup"><span data-stu-id="4790a-129">The primary XML index indexes all tags, values, and paths within the XML instances in an XML column.</span></span> <span data-ttu-id="4790a-130">若要建立主要 XML 索引，出現 XML 資料行之資料表必須在資料表的主索引鍵上，具有叢集索引。</span><span class="sxs-lookup"><span data-stu-id="4790a-130">To create a primary XML index, the table in which the XML column occurs must have a clustered index on the primary key of the table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4790a-131">使用此主索引鍵，以將主要 XML 索引中的資料列與內含 XML 資料行之資料表中的資料列相互關聯。</span><span class="sxs-lookup"><span data-stu-id="4790a-131">uses this primary key to correlate rows in the primary XML index with rows in the table that contains the XML column.</span></span>  
  
 <span data-ttu-id="4790a-132">主要 XML 索引是 `xml` 資料類型資料行中 XML BLOB 的切割和保存的表示法。</span><span class="sxs-lookup"><span data-stu-id="4790a-132">The primary XML index is a shredded and persisted representation of the XML BLOBs in the `xml` data type column.</span></span> <span data-ttu-id="4790a-133">對於資料行中的每個 XML 二進位大型物件 (BLOB) 而言，索引可建立幾個資料列。</span><span class="sxs-lookup"><span data-stu-id="4790a-133">For each XML binary large object (BLOB) in the column, the index creates several rows of data.</span></span> <span data-ttu-id="4790a-134">索引中的資料列數目大約等於 XML 二進位大型物件中的節點數目。</span><span class="sxs-lookup"><span data-stu-id="4790a-134">The number of rows in the index is approximately equal to the number of nodes in the XML binary large object.</span></span> <span data-ttu-id="4790a-135">當查詢擷取完整 XML 執行個體時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會從 XML 資料行提供此執行個體。</span><span class="sxs-lookup"><span data-stu-id="4790a-135">When a query retrieves the full XML instance, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides the instance from the XML column.</span></span> <span data-ttu-id="4790a-136">XML 執行個體中的查詢會使用主要 XML 索引，並使用索引本身來傳回純量值或 XML 子樹。</span><span class="sxs-lookup"><span data-stu-id="4790a-136">Queries within XML instances use the primary XML index, and can return scalar values or XML subtrees by using the index itself.</span></span>  
  
 <span data-ttu-id="4790a-137">每個資料列都會儲存下列節點資訊：</span><span class="sxs-lookup"><span data-stu-id="4790a-137">Each row stores the following node information:</span></span>  
  
-   <span data-ttu-id="4790a-138">類似元素或屬性名稱的標記名稱。</span><span class="sxs-lookup"><span data-stu-id="4790a-138">Tag name such as an element or attribute name.</span></span>  
  
-   <span data-ttu-id="4790a-139">節點值。</span><span class="sxs-lookup"><span data-stu-id="4790a-139">Node value.</span></span>  
  
-   <span data-ttu-id="4790a-140">如元素節點、屬性節點或文字節點等節點類型。</span><span class="sxs-lookup"><span data-stu-id="4790a-140">Node type such as an element node, attribute node, or text node.</span></span>  
  
-   <span data-ttu-id="4790a-141">文件順序資訊，以內部節點識別碼表示。</span><span class="sxs-lookup"><span data-stu-id="4790a-141">Document order information, represented by an internal node identifier.</span></span>  
  
-   <span data-ttu-id="4790a-142">從每個節點至 XML 樹狀結構根節點的路徑。</span><span class="sxs-lookup"><span data-stu-id="4790a-142">Path from each node to the root of the XML tree.</span></span> <span data-ttu-id="4790a-143">在查詢中會為路徑運算式搜尋資料行。</span><span class="sxs-lookup"><span data-stu-id="4790a-143">This column is searched for path expressions in the query.</span></span>  
  
-   <span data-ttu-id="4790a-144">基底資料表的主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="4790a-144">Primary key of the base table.</span></span> <span data-ttu-id="4790a-145">基底資料表的主索引鍵會在主要 XML 索引中重複，以利向後聯結基底資料表，而基底資料表主索引鍵中資料行的最大數目是限定為 15。</span><span class="sxs-lookup"><span data-stu-id="4790a-145">The primary key of the base table is duplicated in the primary XML index for a back join with the base table, and the maximum number of columns in the primary key of the base table is limited to 15.</span></span>  
  
 <span data-ttu-id="4790a-146">此節點資訊是用以評估和建構指定查詢的 XML 結果。</span><span class="sxs-lookup"><span data-stu-id="4790a-146">This node information is used to evaluate and construct XML results for a specified query.</span></span> <span data-ttu-id="4790a-147">為了達到最佳化，標記名稱與節點類型資訊將會編碼成整數值，而 Path 資料行則會使用相同的編碼。</span><span class="sxs-lookup"><span data-stu-id="4790a-147">For optimization purposes, the tag name and the node type information are encoded as integer values, and the Path column uses the same encoding.</span></span> <span data-ttu-id="4790a-148">另外，當只知道路徑後置詞時，會以相反順序儲存路徑以允許比對路徑。</span><span class="sxs-lookup"><span data-stu-id="4790a-148">Also, paths are stored in reverse order to allow matching paths when only the path suffix is known.</span></span> <span data-ttu-id="4790a-149">例如：</span><span class="sxs-lookup"><span data-stu-id="4790a-149">For example:</span></span>  
  
-   <span data-ttu-id="4790a-150">`//ContactRecord/PhoneNumber` 只知道最後兩個步驟</span><span class="sxs-lookup"><span data-stu-id="4790a-150">`//ContactRecord/PhoneNumber` where only the last two steps are known</span></span>  
  
 <span data-ttu-id="4790a-151">OR</span><span class="sxs-lookup"><span data-stu-id="4790a-151">OR</span></span>  
  
-   <span data-ttu-id="4790a-152">`/Book/*/Title` 於運算式的中間指定了萬用字元 (`*`)。</span><span class="sxs-lookup"><span data-stu-id="4790a-152">`/Book/*/Title` where the wildcard character (`*`) is specified in the middle of the expression.</span></span>  
  
 <span data-ttu-id="4790a-153">查詢處理器會使用主要 XML 索引來進行包含 [xml 資料類型方法](/sql/t-sql/xml/xml-data-type-methods) 的查詢，並從主要索引本身傳回純量值或 XML 子樹。</span><span class="sxs-lookup"><span data-stu-id="4790a-153">The query processor uses the primary XML index for queries that involve [xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) and returns either scalar values or the XML subtrees from the primary index itself.</span></span> <span data-ttu-id="4790a-154">(這個索引會儲存重新建構 XML 執行個體的所有必要資訊)。</span><span class="sxs-lookup"><span data-stu-id="4790a-154">(This index stores all the necessary information to reconstruct the XML instance.)</span></span>  
  
 <span data-ttu-id="4790a-155">例如，下列查詢會傳回儲存在資料表之類型資料行中的摘要資訊 `CatalogDescription``xml` `ProductModel` 。</span><span class="sxs-lookup"><span data-stu-id="4790a-155">For example, the following query returns summary information stored in the `CatalogDescription``xml` type column in the `ProductModel` table.</span></span> <span data-ttu-id="4790a-156">此查詢只會針對目錄描述也儲存 <`Features`> 描述的產品型號傳回其 <`Summary`> 資訊。</span><span class="sxs-lookup"><span data-stu-id="4790a-156">The query returns <`Summary`> information only for product models whose catalog description also stores the <`Features`> description.</span></span>  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS "PD")SELECT CatalogDescription.query('  /PD:ProductDescription/PD:Summary') as ResultFROM Production.ProductModelWHERE CatalogDescription.exist ('/PD:ProductDescription/PD:Features') = 1  
```  
  
 <span data-ttu-id="4790a-157">至於主要 XML 索引，而不是切割基底資料表中每個 XML 二進位大型物件的執行個體，會針對 `exist()` 方法中所指定的運算式，循序搜尋索引中與每個 XML 二進位大型物件相對應的資料列。</span><span class="sxs-lookup"><span data-stu-id="4790a-157">With regard to the primary XML index, instead of shredding each XML binary large object instance in the base table, the rows in the index that correspond to each XML binary large object are searched sequentially for the expression specified in the `exist()` method.</span></span> <span data-ttu-id="4790a-158">如果在索引中的 Path 資料行找到了路徑，就會從主要 XML 索引擷取 <`Summary`> 元素及其子樹，並將其轉換為 XML 二進位大型物件，當做 `query()` 方法的結果。</span><span class="sxs-lookup"><span data-stu-id="4790a-158">If the path is found in the Path column in the index, the <`Summary`> element together with its subtrees is retrieved from the primary XML index and converted into an XML binary large object as the result of the `query()` method.</span></span>  
  
 <span data-ttu-id="4790a-159">請注意，在擷取完整 XML 執行個體時不會使用主要 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="4790a-159">Note that the primary XML index is not used when retrieving a full XML instance.</span></span> <span data-ttu-id="4790a-160">例如，下列查詢會從資料表擷取整個 XML 執行個體，該執行個體描述了特定產品型號的製造指示。</span><span class="sxs-lookup"><span data-stu-id="4790a-160">For example, the following query retrieves from the table the whole XML instance that describes the manufacturing instructions for a specific product model.</span></span>  
  
```  
USE AdventureWorks2012;SELECT InstructionsFROM Production.ProductModel WHERE ProductModelID=7;  
```  
  
## <a name="secondary-xml-indexes"></a><span data-ttu-id="4790a-161">次要 XML 索引</span><span class="sxs-lookup"><span data-stu-id="4790a-161">Secondary XML Indexes</span></span>  
 <span data-ttu-id="4790a-162">若要增強搜尋效能，您可以建立次要的 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="4790a-162">To enhance search performance, you can create secondary XML indexes.</span></span> <span data-ttu-id="4790a-163">在建立次要索引之前，必須先有主要 XML 索引存在。</span><span class="sxs-lookup"><span data-stu-id="4790a-163">A primary XML index must first exist before you can create secondary indexes.</span></span> <span data-ttu-id="4790a-164">以下為其類型：</span><span class="sxs-lookup"><span data-stu-id="4790a-164">These are the types:</span></span>  
  
-   <span data-ttu-id="4790a-165">PATH 次要 XML 索引</span><span class="sxs-lookup"><span data-stu-id="4790a-165">PATH secondary XML index</span></span>  
  
-   <span data-ttu-id="4790a-166">VALUE 次要 XML 索引</span><span class="sxs-lookup"><span data-stu-id="4790a-166">VALUE secondary XML index</span></span>  
  
-   <span data-ttu-id="4790a-167">PROPERTY 次要 XML 索引</span><span class="sxs-lookup"><span data-stu-id="4790a-167">PROPERTY secondary XML index</span></span>  
  
 <span data-ttu-id="4790a-168">以下是建立一或多個次要索引的一些指導方針：</span><span class="sxs-lookup"><span data-stu-id="4790a-168">Following are some guidelines for creating one or more secondary indexes:</span></span>  
  
-   <span data-ttu-id="4790a-169">如果您的工作負載在 XML 資料行上大量使用路徑運算式，PATH 次要 XML 索引就可能會加速您的工作負載。</span><span class="sxs-lookup"><span data-stu-id="4790a-169">If your workload uses path expressions significantly on XML columns, the PATH secondary XML index is likely to speed up your workload.</span></span> <span data-ttu-id="4790a-170">最常見的情況是將 **exist()** 方法使用在 Transact-SQL 的 WHERE 子句中的 XML 資料行上。</span><span class="sxs-lookup"><span data-stu-id="4790a-170">The most common case is the use of the **exist()** method on XML columns in the WHERE clause of Transact-SQL.</span></span>  
  
-   <span data-ttu-id="4790a-171">如果您的工作負載使用路徑運算式，從個別的 XML 執行個體中擷取多個值，則在 PROPERTY 索引中將路徑叢集在每個 XML 執行個體中，可能會有所幫助。</span><span class="sxs-lookup"><span data-stu-id="4790a-171">If your workload retrieves multiple values from individual XML instances by using path expressions, clustering paths within each XML instance in the PROPERTY index may be helpful.</span></span> <span data-ttu-id="4790a-172">當物件的屬性被提取，且已知其主索引鍵值時，此案例通常會發生在屬性包案例中。</span><span class="sxs-lookup"><span data-stu-id="4790a-172">This scenario typically occurs in a property bag scenario when properties of an object are fetched and its primary key value is known.</span></span>  
  
-   <span data-ttu-id="4790a-173">如果您的工作負載需要查詢 XML 執行個體中的值，但您不知道含有那些值的元素或屬性名稱，您可能會想要建立 VALUE 索引。</span><span class="sxs-lookup"><span data-stu-id="4790a-173">If your workload involves querying for values within XML instances without knowing the element or attribute names that contain those values, you may want to create the VALUE index.</span></span> <span data-ttu-id="4790a-174">這通常會發生在子系座標軸查閱，例如 //author[last-name="Howard"]，其中 \<author> 元素可出現在階層中的任何層級。</span><span class="sxs-lookup"><span data-stu-id="4790a-174">This typically occurs with descendant axes lookups, such as //author[last-name="Howard"], where \<author> elements can occur at any level of the hierarchy.</span></span> <span data-ttu-id="4790a-175">這也會發生在萬用字元查詢中，例如 /book [@\* = "novel"]，此查詢是要尋找屬性中具有 "novel" 值的 \<book> 元素。</span><span class="sxs-lookup"><span data-stu-id="4790a-175">It also occurs in wildcard queries, such as /book [@\* = "novel"], where the query looks for \<book> elements that have some attribute having the value "novel".</span></span>  
  
### <a name="path-secondary-xml-index"></a><span data-ttu-id="4790a-176">PATH 次要 XML 索引</span><span class="sxs-lookup"><span data-stu-id="4790a-176">PATH Secondary XML Index</span></span>  
 <span data-ttu-id="4790a-177">如果您的查詢通常會在 `xml` 類型資料行上指定路徑運算式，則使用 PATH 次要索引將可使搜尋速度變快。</span><span class="sxs-lookup"><span data-stu-id="4790a-177">If your queries generally specify path expressions on `xml` type columns, a PATH secondary index may be able to speed up the search.</span></span> <span data-ttu-id="4790a-178">如本主題前面所述，當您的查詢在 WHERE 子句中指定 **exist()** 方法時，主索引就非常有用。</span><span class="sxs-lookup"><span data-stu-id="4790a-178">As described earlier in this topic, the primary index is helpful when you have queries that specify **exist()** method in the WHERE clause.</span></span> <span data-ttu-id="4790a-179">如果您加入 PATH 次要索引，也可以改善這類查詢的搜尋效能。</span><span class="sxs-lookup"><span data-stu-id="4790a-179">If you add a PATH secondary index, you may also improve the search performance in such queries.</span></span>  
  
 <span data-ttu-id="4790a-180">雖然主要 XML 索引可避免必須在執行階段切割 XML 二進位大型物件，但是它可能無法為以路徑運算式為基礎的查詢提供最佳的效能。</span><span class="sxs-lookup"><span data-stu-id="4790a-180">Although a primary XML index avoids having to shred the XML binary large objects at run time, it may not provide the best performance for queries based on path expressions.</span></span> <span data-ttu-id="4790a-181">由於會針對大型 XML 執行個體，循序搜尋與 XML 二進位大型物件相對應的主要 XML 索引中的所有資料列，因此循序搜尋可能會很慢。</span><span class="sxs-lookup"><span data-stu-id="4790a-181">Because all rows in the primary XML index corresponding to an XML binary large object are searched sequentially for large XML instances, the sequential search may be slow.</span></span> <span data-ttu-id="4790a-182">在此情況下，將次要索引建立在主要索引的路徑值與節點值上，將可大幅增加索引搜尋的速度。</span><span class="sxs-lookup"><span data-stu-id="4790a-182">In this case, having a secondary index built on the path values and node values in the primary index can significantly speed up the index search.</span></span> <span data-ttu-id="4790a-183">在 PATH 次要索引中，路徑與節點值都是索引鍵資料行，可在搜尋路徑時進行更有效率的搜尋。</span><span class="sxs-lookup"><span data-stu-id="4790a-183">In the PATH secondary index, the path and node values are key columns that allow for more efficient seeks when searching for paths.</span></span> <span data-ttu-id="4790a-184">查詢最佳化工具可以針對如下列所示的運算式使用 PATH 索引：</span><span class="sxs-lookup"><span data-stu-id="4790a-184">The query optimizer may use the PATH index for expressions such as those shown in the following:</span></span>  
  
-   <span data-ttu-id="4790a-185">`/root/Location` 其僅指定路徑</span><span class="sxs-lookup"><span data-stu-id="4790a-185">`/root/Location` which specify only a path</span></span>  
  
 <span data-ttu-id="4790a-186">OR</span><span class="sxs-lookup"><span data-stu-id="4790a-186">OR</span></span>  
  
-   <span data-ttu-id="4790a-187">`/root/Location/@LocationID[.="10"]` 其中同時指定了路徑與節點值。</span><span class="sxs-lookup"><span data-stu-id="4790a-187">`/root/Location/@LocationID[.="10"]` where both the path and the node value are specified.</span></span>  
  
 <span data-ttu-id="4790a-188">下列查詢顯示 PATH 索引非常有用：</span><span class="sxs-lookup"><span data-stu-id="4790a-188">The following query shows where the PATH index is helpful:</span></span>  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS "PD")  
  
SELECT CatalogDescription.query('  
  /PD:ProductDescription/PD:Summary  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist ('/PD:ProductDescription/@ProductModelID[.="19"]') = 1  
```  
  
 <span data-ttu-id="4790a-189">在查詢中， `/PD:ProductDescription/@ProductModelID` 方法中的路徑運算式 `"19"` 與 `exist()` 值會對應至 PATH 索引的索引鍵欄位。</span><span class="sxs-lookup"><span data-stu-id="4790a-189">In the query, the path expression `/PD:ProductDescription/@ProductModelID` and value `"19"` in the `exist()` method correspond to the key fields of the PATH index.</span></span> <span data-ttu-id="4790a-190">這允許在 PATH 索引中進行直接搜尋，並對主索引中的路徑值提供比循序搜尋更佳的搜尋效能。</span><span class="sxs-lookup"><span data-stu-id="4790a-190">This allows for direct seek in the PATH index and provides better search performance than the sequential search for path values in the primary index.</span></span>  
  
### <a name="value-secondary-xml-index"></a><span data-ttu-id="4790a-191">VALUE 次要 XML 索引</span><span class="sxs-lookup"><span data-stu-id="4790a-191">VALUE Secondary XML Index</span></span>  
 <span data-ttu-id="4790a-192">如果查詢是以值為基礎，例如， `/Root/ProductDescription/@*[. = "Mountain Bike"]` 或 `//ProductDescription[@Name = "Mountain Bike"]`，且並未完整指定路徑，或是路徑中包含萬用字元，您可以透過在主要 XML 索引的節點值上建立次要 XML 索引，以獲得更快的結果。</span><span class="sxs-lookup"><span data-stu-id="4790a-192">If queries are value based, for example, `/Root/ProductDescription/@*[. = "Mountain Bike"]` or `//ProductDescription[@Name = "Mountain Bike"]`, and the path is not fully specified or it includes a wildcard, you might obtain faster results by building a secondary XML index that is built on node values in the primary XML index.</span></span>  
  
 <span data-ttu-id="4790a-193">VALUE 索引的索引鍵資料行是主要 XML 索引的節點值與路徑。</span><span class="sxs-lookup"><span data-stu-id="4790a-193">The key columns of the VALUE index are (node value and path) of the primary XML index.</span></span> <span data-ttu-id="4790a-194">如果您的工作負載需要在不知道包含值的元素或屬性名稱的情況下，從 XML 執行個體查詢值，VALUE 索引將會非常有用。</span><span class="sxs-lookup"><span data-stu-id="4790a-194">If your workload involves querying for values from XML instances without knowing the element or attribute names that contain the values, a VALUE index may be useful.</span></span> <span data-ttu-id="4790a-195">例如，下列運算式將可從擁有 VALUE 索引而獲益：</span><span class="sxs-lookup"><span data-stu-id="4790a-195">For example, the following expression will benefit from having a VALUE index:</span></span>  
  
-   <span data-ttu-id="4790a-196">`//author[LastName="someName"]`，其中您知道 <`LastName`> 元素的值，但是 <`author`> 父系可存在於任何位置。</span><span class="sxs-lookup"><span data-stu-id="4790a-196">`//author[LastName="someName"]` where you know the value of the <`LastName`> element, but the <`author`> parent can occur anywhere.</span></span>  
  
-   <span data-ttu-id="4790a-197">在 `/book[@* = "someValue"]` 中，查詢會尋找某些屬性中包含值 `"someValue"` 的 <`book`> 元素。</span><span class="sxs-lookup"><span data-stu-id="4790a-197">`/book[@* = "someValue"]` where the query looks for the <`book`> element that has some attribute having the value `"someValue"`.</span></span>  
  
 <span data-ttu-id="4790a-198">下列查詢會從 `ContactID` 資料表傳回 `Contact` 。</span><span class="sxs-lookup"><span data-stu-id="4790a-198">The following query returns `ContactID` from the `Contact` table.</span></span> <span data-ttu-id="4790a-199">`WHERE`子句會指定一個篩選準則，以尋找類型資料行中的值 `AdditionalContactInfo``xml` 。</span><span class="sxs-lookup"><span data-stu-id="4790a-199">The `WHERE` clause specifies a filter that looks for values in the `AdditionalContactInfo``xml` type column.</span></span> <span data-ttu-id="4790a-200">如果對應的其他連絡資訊 XML 二進位大型物件包含特定的電話號碼，就會傳回連絡識別碼。</span><span class="sxs-lookup"><span data-stu-id="4790a-200">The contact IDs are returned only if the corresponding additional contact information XML binary large object includes a specific telephone number.</span></span> <span data-ttu-id="4790a-201">因為 <`telephoneNumber`> 元素有可能出現在 XML 的任何位置，所以路徑運算式會指定 descendent-or-self 軸。</span><span class="sxs-lookup"><span data-stu-id="4790a-201">Because the <`telephoneNumber`> element may appear anywhere in the XML, the path expression specifies the descendent-or-self axis.</span></span>  
  
```  
WITH XMLNAMESPACES (  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS CI,  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS ACT)  
  
SELECT ContactID   
FROM   Person.Contact  
WHERE  AdditionalContactInfo.exist('//ACT:telephoneNumber/ACT:number[.="111-111-1111"]') = 1  
```  
  
 <span data-ttu-id="4790a-202">在此情況下，雖然已得知 <`number`> 的搜尋值，但它有可能以 <`telephoneNumber`> 元素的子系出現在 XML 執行個體中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="4790a-202">In this situation, the search value for <`number`> is known, but it can appear anywhere in the XML instance as a child of the <`telephoneNumber`> element.</span></span> <span data-ttu-id="4790a-203">此類的查詢可從以特定值為基礎的索引查閱獲益。</span><span class="sxs-lookup"><span data-stu-id="4790a-203">This kind of query might benefit from an index lookup based on a specific value.</span></span>  
  
### <a name="property-secondary-index"></a><span data-ttu-id="4790a-204">PROPERTY 次要索引</span><span class="sxs-lookup"><span data-stu-id="4790a-204">PROPERTY Secondary Index</span></span>  
 <span data-ttu-id="4790a-205">從個別 XML 執行個體擷取一或多個值的查詢可從 PROPERTY 索引獲益。</span><span class="sxs-lookup"><span data-stu-id="4790a-205">Queries that retrieve one or more values from individual XML instances might benefit from a PROPERTY index.</span></span> <span data-ttu-id="4790a-206">當您使用類型\*\* ( # B1\*\*方法的值來抓取物件屬性 `xml` ，以及已知物件的主鍵值時，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="4790a-206">This scenario occurs when you retrieve object properties by using the **value()** method of the `xml` type and when the primary key value of the object is known.</span></span>  
  
 <span data-ttu-id="4790a-207">PROPERTY 索引是建立在主要 XML 索引的資料行 (PK、Path 以及節點值) 上，在主要 XML 索引中 PK 是基底資料表的主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="4790a-207">The PROPERTY index is built on columns (PK, Path and node value) of the primary XML index where PK is the primary key of the base table.</span></span>  
  
 <span data-ttu-id="4790a-208">例如，若為產品型號 `19`，下列查詢就會使用 `ProductModelID` 方法來擷取 `ProductModelName` 和 `value()` 屬性值。</span><span class="sxs-lookup"><span data-stu-id="4790a-208">For example, for product model `19`, the following query retrieves the `ProductModelID` and `ProductModelName` attribute values using the `value()` method.</span></span> <span data-ttu-id="4790a-209">PROPERTY 索引可提供比使用主要 XML 索引或其他次要 XML 索引更快的執行。</span><span class="sxs-lookup"><span data-stu-id="4790a-209">Instead of using the primary XML index or the other secondary XML indexes, the PROPERTY index may provide faster execution.</span></span>  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS "PD")  
  
SELECT CatalogDescription.value('(/PD:ProductDescription/@ProductModelID)[1]', 'int') as ModelID,  
       CatalogDescription.value('(/PD:ProductDescription/@ProductModelName)[1]', 'varchar(30)') as ModelName          
FROM Production.ProductModel     
WHERE ProductModelID = 19  
```  
  
 <span data-ttu-id="4790a-210">除了本主題稍後所述的差異之外，在類型資料行上建立 XML 索引 `xml` 與在非類型資料行上建立索引類似 `xml` 。</span><span class="sxs-lookup"><span data-stu-id="4790a-210">Except for the differences described later in this topic, creating an XML index on an`xml` type column is similar to creating an index on a non-`xml` type column.</span></span> <span data-ttu-id="4790a-211">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] DDL 陳述式可用以建立及管理 XML 索引：</span><span class="sxs-lookup"><span data-stu-id="4790a-211">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] DDL statements can be used to create and manage XML indexes:</span></span>  
  
-   [<span data-ttu-id="4790a-212">CREATE INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4790a-212">CREATE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
-   [<span data-ttu-id="4790a-213">ALTER INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4790a-213">ALTER INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-index-transact-sql)  
  
-   [<span data-ttu-id="4790a-214">DROP INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4790a-214">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
## <a name="getting-information-about-xml-indexes"></a><span data-ttu-id="4790a-215">取得有關 XML 索引的資訊</span><span class="sxs-lookup"><span data-stu-id="4790a-215">Getting Information about XML Indexes</span></span>  
 <span data-ttu-id="4790a-216">XML 索引項目會出現在目錄檢視 sys.indexes 中，且具有索引 "type" 3。</span><span class="sxs-lookup"><span data-stu-id="4790a-216">XML index entries appear in the catalog view, sys.indexes, with the index "type" 3.</span></span> <span data-ttu-id="4790a-217">名稱資料行包含此 XML 索引的名稱。</span><span class="sxs-lookup"><span data-stu-id="4790a-217">The name column contains the name of the XML index.</span></span>  
  
 <span data-ttu-id="4790a-218">XML 索引也會記錄在目錄檢視 sys.xml_indexes 中。</span><span class="sxs-lookup"><span data-stu-id="4790a-218">XML indexes are also recorded in the catalog view, sys.xml_indexes.</span></span> <span data-ttu-id="4790a-219">其中包含 sys.indexes 的所有資料行，以及對 XML 索引有助益的一些特定資料行。</span><span class="sxs-lookup"><span data-stu-id="4790a-219">This contains all the columns of sys.indexes and some specific ones that are useful for XML indexes.</span></span> <span data-ttu-id="4790a-220">資料行 secondary_type 中的 NULL 值是指主要 XML 索引；'P'、'R' 和 'V' 這三個值分別代表 PATH、PROPERTY 和 VALUE 次要 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="4790a-220">The value NULL in the column, secondary_type, indicates a primary XML index; the values 'P', 'R' and 'V' stand for PATH, PROPERTY, and VALUE secondary XML indexes, respectively.</span></span>  
  
 <span data-ttu-id="4790a-221">XML 索引使用的空間可以在資料表值函式 [sys.dm_db_index_physical_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql)中找到。</span><span class="sxs-lookup"><span data-stu-id="4790a-221">The space use of XML indexes can be found in the table-valued function [sys.dm_db_index_physical_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql).</span></span> <span data-ttu-id="4790a-222">其提供所有索引類型的資訊，例如：所佔用的磁碟分頁數量、平均資料列大小 (位元組)，以及記錄的數量。</span><span class="sxs-lookup"><span data-stu-id="4790a-222">It provides information, such as the number of disk pages occupied, average row size in bytes, and number of records, for all index types..</span></span> <span data-ttu-id="4790a-223">另外還包含 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="4790a-223">This also includes XML indexes.</span></span> <span data-ttu-id="4790a-224">每個資料庫分割區都有此資訊。</span><span class="sxs-lookup"><span data-stu-id="4790a-224">This information is available for each database partition.</span></span> <span data-ttu-id="4790a-225">XML 索引使用相同的基底資料表分割區配置及分割區功能。</span><span class="sxs-lookup"><span data-stu-id="4790a-225">XML indexes use the same partitioning scheme and partitioning function of the base table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4790a-226">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4790a-226">See Also</span></span>  
 <span data-ttu-id="4790a-227">[sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4790a-227">[sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql) </span></span>  
 [<span data-ttu-id="4790a-228">XML 資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4790a-228">XML Data &#40;SQL Server&#41;</span></span>](../xml/xml-data-sql-server.md)  
  
  
