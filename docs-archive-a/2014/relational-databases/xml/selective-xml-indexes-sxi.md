---
title: 選擇性 XML 索引 (SXI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: 598ecdcd-084b-4032-81b2-eed6ae9f5d44
author: rothja
ms.author: jroth
ms.openlocfilehash: 37dd72c5de2892672dc9f63066075ab5e770d758
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606656"
---
# <a name="selective-xml-indexes-sxi"></a><span data-ttu-id="e83e9-102">選擇性 XML 索引 (SXI)</span><span class="sxs-lookup"><span data-stu-id="e83e9-102">Selective XML Indexes (SXI)</span></span>
  <span data-ttu-id="e83e9-103">選擇性 XML 索引是除了一般 XML 索引之外，另一種可供您使用 XML 索引類型。</span><span class="sxs-lookup"><span data-stu-id="e83e9-103">Selective XML indexes are another type of XML index that is available to you in addition to ordinary XML indexes.</span></span> <span data-ttu-id="e83e9-104">選擇性 XML 索引功能的目標如下：</span><span class="sxs-lookup"><span data-stu-id="e83e9-104">The goals of the selective XML index feature are the following:</span></span>  
  
-   <span data-ttu-id="e83e9-105">改善 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中所儲存 XML 資料的查詢效能。</span><span class="sxs-lookup"><span data-stu-id="e83e9-105">To improve the performance of queries over XML data stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="e83e9-106">支援更快索引大型 XML 資料工作負載。</span><span class="sxs-lookup"><span data-stu-id="e83e9-106">To support faster indexing of large XML data workloads.</span></span>  
  
-   <span data-ttu-id="e83e9-107">透過減少 XML 索引的儲存成本提升可調適性。</span><span class="sxs-lookup"><span data-stu-id="e83e9-107">To improve scalability by reducing the storage costs of XML indexes.</span></span>  
  
 <span data-ttu-id="e83e9-108">一般 XML 索引的主要限制在於會索引整份 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="e83e9-108">The main limitation with ordinary XML indexes is that they index the entire XML document.</span></span> <span data-ttu-id="e83e9-109">這樣會導致幾項重大錯誤，例如，查詢效能降低與索引維護成本增加，這些大部分與索引的儲存成本相關。</span><span class="sxs-lookup"><span data-stu-id="e83e9-109">This leads to several significant drawbacks, such as decreased query performance and increased index maintenance cost, mostly related to the storage costs of the index.</span></span>  
  
 <span data-ttu-id="e83e9-110">選擇性 XML 索引功能可讓您僅從 XML 文件升級要索引的特定路徑。</span><span class="sxs-lookup"><span data-stu-id="e83e9-110">The selective XML index feature lets you promote only certain paths from the XML documents to index.</span></span> <span data-ttu-id="e83e9-111">在建立索引時，這些路徑會經過評估，而這些路徑指向的節點會經過切割，並且儲存到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中的關聯式資料表內。</span><span class="sxs-lookup"><span data-stu-id="e83e9-111">At index creation time, these paths are evaluated, and the nodes that they point to are shredded and stored inside a relational table in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e83e9-112">此功能使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Research 與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 產品小組共同開發的高效率對應演算法。</span><span class="sxs-lookup"><span data-stu-id="e83e9-112">This feature uses an efficient mapping algorithm developed by [!INCLUDE[msCoName](../../includes/msconame-md.md)] Research in collaboration with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] product team.</span></span> <span data-ttu-id="e83e9-113">此演算法會將 XML 節點對應到單一關聯式資料表並達到絕佳的效能，同時只需要適度的儲存空間。</span><span class="sxs-lookup"><span data-stu-id="e83e9-113">This algorithm maps the XML nodes to a single relational table, and achieves exceptional performance while requiring only modest storage space.</span></span>  
  
 <span data-ttu-id="e83e9-114">選擇性 XML 索引功能也支援在已由選擇性 XML 索引進行索引之節點上的次要選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="e83e9-114">The selective XML index feature also supports secondary selective XML indexes over nodes that have been indexed by a selective XML index.</span></span> <span data-ttu-id="e83e9-115">這些次要選擇性索引不但有效率，還能進一步提升查詢效能。</span><span class="sxs-lookup"><span data-stu-id="e83e9-115">These secondary selective indexes are efficient and further improve the performance of queries.</span></span>  
  
##  <a name="benefits-of-selective-xml-indexes"></a><a name="benefits"></a> <span data-ttu-id="e83e9-116">選擇性 XML 索引的優點</span><span class="sxs-lookup"><span data-stu-id="e83e9-116">Benefits of Selective XML Indexes</span></span>  
 <span data-ttu-id="e83e9-117">選擇性 XML 索引提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="e83e9-117">Selective XML indexes provide the following benefits:</span></span>  
  
1.  <span data-ttu-id="e83e9-118">大幅提升對一般查詢負載之 XML 資料類型的查詢效能。</span><span class="sxs-lookup"><span data-stu-id="e83e9-118">Greatly improved query performance over the XML data type for typical query loads.</span></span>  
  
2.  <span data-ttu-id="e83e9-119">與一般 XML 索引相較之下，儲存需求更低。</span><span class="sxs-lookup"><span data-stu-id="e83e9-119">Reduced storage requirements compared to ordinary XML indexes.</span></span>  
  
3.  <span data-ttu-id="e83e9-120">與一般 XML 索引相較之下，索引維護成本減少。</span><span class="sxs-lookup"><span data-stu-id="e83e9-120">Reduced index maintenance costs compared to ordinary XML indexes.</span></span>  
  
4.  <span data-ttu-id="e83e9-121">不需要更新應用程式就能受益於選擇性 XML 索引的優點。</span><span class="sxs-lookup"><span data-stu-id="e83e9-121">No need to update applications to benefit from selective XML indexes.</span></span>  
  

  
##  <a name="selective-xml-indexes-and-primary-xml-indexes"></a><a name="compare"></a> <span data-ttu-id="e83e9-122">選擇性 XML 索引和主要 XML 索引</span><span class="sxs-lookup"><span data-stu-id="e83e9-122">Selective XML Indexes and Primary XML Indexes</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e83e9-123">在大部分情況下，建立選擇性 XML 索引會比一般 XML 索引獲得更佳的效能和更有效率的儲存。</span><span class="sxs-lookup"><span data-stu-id="e83e9-123">Create a selective XML index instead of an ordinary XML index in most cases for better performance and more efficient storage.</span></span>  
  
 <span data-ttu-id="e83e9-124">但是，下列任一情況為 true 時，不建議使用選擇性 XML 索引：</span><span class="sxs-lookup"><span data-stu-id="e83e9-124">However, a selective XML index is not recommended when either of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="e83e9-125">對應大量節點路徑。</span><span class="sxs-lookup"><span data-stu-id="e83e9-125">You map a large number of node paths.</span></span>  
  
-   <span data-ttu-id="e83e9-126">在文件結構中支援未知元素或未知位置中元素的查詢。</span><span class="sxs-lookup"><span data-stu-id="e83e9-126">You support queries for unknown elements or elements in an unknown location in the document structure.</span></span>  
  

  
##  <a name="simple-example-of-a-selective-xml-index"></a><a name="example"></a> <span data-ttu-id="e83e9-127">簡單的選擇性 XML 索引範例</span><span class="sxs-lookup"><span data-stu-id="e83e9-127">Simple Example of a Selective XML Index</span></span>  
 <span data-ttu-id="e83e9-128">在大約有 500,000 個資料列的資料表中將下列 XML 片段視為 XML 文件：</span><span class="sxs-lookup"><span data-stu-id="e83e9-128">Consider the following XML fragment as an XML document in a table of approximately 500,000 rows:</span></span>  
  
```xml  
<book>  
    <created>2004-03-01</created>   
    <authors>Various</authors>  
    <subjects>  
        <subject>English wit and humor -- Periodicals</subject>  
        <subject>AP</subject>   
    </subjects>  
    <title>Punch, or the London Charivari, Volume 156, April 2, 1919</title>  
    <id>etext11617</id>  
</book>  
```  
  
 <span data-ttu-id="e83e9-129">在這個簡單的結構描述中那麼多個資料列上建立主要 XML 索引，需要花很長的時間。</span><span class="sxs-lookup"><span data-stu-id="e83e9-129">Creating a primary XML index over so many rows of this simple schema takes a long time.</span></span> <span data-ttu-id="e83e9-130">查詢此資料也會因為主要 XML 索引不支援選擇性索引而受到影響。</span><span class="sxs-lookup"><span data-stu-id="e83e9-130">Querying this data also suffers from the fact that a primary XML index does not support selective indexing.</span></span>  
  
 <span data-ttu-id="e83e9-131">如果您只需要在 `/book/title` 路徑和 `/book/subjects` 路徑上查詢此資料，可以建立下列選擇性 XML 索引：</span><span class="sxs-lookup"><span data-stu-id="e83e9-131">If you only need to query this data over the `/book/title` path and the `/book/subjects` path, you can create the following selective XML index:</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX SXI_index  
ON Tbl(xmlcol)  
FOR   
(  
    pathTitle = '/book/title/text()' AS XQUERY 'xs:string',   
    pathAuthors = '/book/authors' AS XQUERY 'node()',  
    pathId = '/book/id' AS SQL NVARCHAR(100)  
)  
```  
  
 <span data-ttu-id="e83e9-132">上述陳述式是 CREATE 語法的很好範例，您可在建立選擇性 XML 索引時使用。</span><span class="sxs-lookup"><span data-stu-id="e83e9-132">The preceding statement is a good example of the CREATE syntax that you use when you create a selective XML index.</span></span> <span data-ttu-id="e83e9-133">在 CREATE 陳述式中，首先提供索引的名稱，並且識別要索引的資料表和 XML 資料行。</span><span class="sxs-lookup"><span data-stu-id="e83e9-133">In the CREATE statement, first you provide a name for the index and identify the table and the XML column to index.</span></span> <span data-ttu-id="e83e9-134">然後提供要索引的路徑。</span><span class="sxs-lookup"><span data-stu-id="e83e9-134">Then you provide the paths to index.</span></span> <span data-ttu-id="e83e9-135">路徑有三個部分：</span><span class="sxs-lookup"><span data-stu-id="e83e9-135">A path has three parts:</span></span>  
  
1.  <span data-ttu-id="e83e9-136">可唯一識別路徑的名稱。</span><span class="sxs-lookup"><span data-stu-id="e83e9-136">A name that uniquely identifies the path.</span></span>  
  
2.  <span data-ttu-id="e83e9-137">描述路徑的 XQuery 運算式。</span><span class="sxs-lookup"><span data-stu-id="e83e9-137">An XQuery expression that describes the path.</span></span>  
  
3.  <span data-ttu-id="e83e9-138">選用的最佳化提示。</span><span class="sxs-lookup"><span data-stu-id="e83e9-138">Optional optimization hints.</span></span>  
  
 <span data-ttu-id="e83e9-139">如需有關這些元素的詳細資訊，請參閱 [相關工作](#reltasks)。</span><span class="sxs-lookup"><span data-stu-id="e83e9-139">For more information about these elements, see [Related Tasks](#reltasks).</span></span>  
  

  
## <a name="supported-features-prerequisites-and-limitations"></a><span data-ttu-id="e83e9-140">支援的功能、必要條件和限制</span><span class="sxs-lookup"><span data-stu-id="e83e9-140">Supported Features, Prerequisites, and Limitations</span></span>  
  
###  <a name="supported-xml-features"></a><a name="features"></a> <span data-ttu-id="e83e9-141">支援的 XML 功能</span><span class="sxs-lookup"><span data-stu-id="e83e9-141">Supported XML Features</span></span>  
 <span data-ttu-id="e83e9-142">選擇性 XML 索引在 exist()、value() 和 nodes() 方法內支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所支援的 XQuery。</span><span class="sxs-lookup"><span data-stu-id="e83e9-142">Selective XML indexes support the XQuery supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inside the exist(), value() and nodes() methods.</span></span>  
  
-   <span data-ttu-id="e83e9-143">對於 exist()、value() 和 nodes() 方法，選擇性 XML 索引包含足夠的資訊可轉換整個運算式。</span><span class="sxs-lookup"><span data-stu-id="e83e9-143">For the exist(), value() and nodes() methods, selective XML indexes contain enough information to transform the entire expression.</span></span>  
  
-   <span data-ttu-id="e83e9-144">對於 query() 和 modify() 方法，選擇性 XML 索引可能只用於節點篩選。</span><span class="sxs-lookup"><span data-stu-id="e83e9-144">For the query() and modify() methods, selective XML indexes may be used for node filtering only.</span></span>  
  
-   <span data-ttu-id="e83e9-145">對於 query() 方法，選擇性 XML 索引不會用來擷取結果。</span><span class="sxs-lookup"><span data-stu-id="e83e9-145">For the query() method, selective XML indexes are not used to retrieve results.</span></span>  
  
-   <span data-ttu-id="e83e9-146">對於 modify() 方法，選擇性 XML 索引不會用來更新 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="e83e9-146">For the modify() method, selective XML indexes are not used to update XML documents.</span></span>  
  

  
###  <a name="unsupported-xml-features"></a><a name="unsupported"></a> <span data-ttu-id="e83e9-147">不支援的 XML 功能</span><span class="sxs-lookup"><span data-stu-id="e83e9-147">Unsupported XML Features</span></span>  
 <span data-ttu-id="e83e9-148">選擇性 XML 索引不支援 XML 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 實作中支援的下列功能：</span><span class="sxs-lookup"><span data-stu-id="e83e9-148">Selective XML indexes do not support the following features that are supported in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implementation of XML:</span></span>  
  
-   <span data-ttu-id="e83e9-149">索引包含複雜 XS 類型的節點：聯集類型、序列類型和清單類型。</span><span class="sxs-lookup"><span data-stu-id="e83e9-149">Indexing of nodes with complex XS types: union types, sequence types, and list types.</span></span>  
  
-   <span data-ttu-id="e83e9-150">索引包含二進位 XS 類型的節點：例如 base64Binary 和 hexBinary。</span><span class="sxs-lookup"><span data-stu-id="e83e9-150">Indexing of nodes with binary XS types: for example, base64Binary and hexBinary.</span></span>  
  
-   <span data-ttu-id="e83e9-151">使用結尾包含萬用字元 `*` 的 XPath 運算式指定要編製索引的節點：例如 `/a/b/c/*`、`/a//b/*` 或 `/a/b/*:c`。</span><span class="sxs-lookup"><span data-stu-id="e83e9-151">Specifying the nodes to index with XPath expressions that contain the wildcard character `*` at the end: For example,  `/a/b/c/*`, `/a//b/*`, or `/a/b/*:c`.</span></span>  
  
-   <span data-ttu-id="e83e9-152">索引子系、屬性或下階以外的任何座標軸。</span><span class="sxs-lookup"><span data-stu-id="e83e9-152">Indexing any axis other than child, attribute, or descendant.</span></span> <span data-ttu-id="e83e9-153">`//<step>` 案例可做為特殊案例。</span><span class="sxs-lookup"><span data-stu-id="e83e9-153">The `//<step>` case is allowed as a special case.</span></span>  
  
-   <span data-ttu-id="e83e9-154">索引 XML 處理指示和註解。</span><span class="sxs-lookup"><span data-stu-id="e83e9-154">Indexing of XML processing instructions and comments.</span></span>  
  
-   <span data-ttu-id="e83e9-155">使用 id() 函數指定及擷取節點識別碼。</span><span class="sxs-lookup"><span data-stu-id="e83e9-155">Specifying and retrieving the identifier for a node by using the id() function.</span></span>  
  

  
###  <a name="prerequisites"></a><a name="prereq"></a> <span data-ttu-id="e83e9-156">必要條件</span><span class="sxs-lookup"><span data-stu-id="e83e9-156">Prerequisites</span></span>  
 <span data-ttu-id="e83e9-157">下列必要條件必須存在，您才能在使用者資料表中的 XML 資料行上建立選擇性 XML 索引：</span><span class="sxs-lookup"><span data-stu-id="e83e9-157">The following prerequisites must exist before you can create a selective XML index over an XML column in a user table:</span></span>  
  
-   <span data-ttu-id="e83e9-158">叢集索引必須存在於使用者資料表的主索引鍵上。</span><span class="sxs-lookup"><span data-stu-id="e83e9-158">A clustered index must exist on the primary key of the user table.</span></span>  
  
-   <span data-ttu-id="e83e9-159">搭配選擇性 XML 索引使用時，使用者資料表的主索引鍵大小限制為 128 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e83e9-159">The primary key of the user table is limited to a size of 128 bytes when used with selective XML indexes.</span></span>  
  
-   <span data-ttu-id="e83e9-160">搭配選擇性 XML 索引使用時，使用者資料表的叢集索引鍵限制為 15 個資料行。</span><span class="sxs-lookup"><span data-stu-id="e83e9-160">The clustering key of the user table is limited to 15 columns when used with selective XML indexes.</span></span>  
  

  
###  <a name="limitations"></a><a name="limits"></a> <span data-ttu-id="e83e9-161">限制</span><span class="sxs-lookup"><span data-stu-id="e83e9-161">Limitations</span></span>  
 <span data-ttu-id="e83e9-162">**一般需求與限制**</span><span class="sxs-lookup"><span data-stu-id="e83e9-162">**General requirements and limitations**</span></span>  
  
-   <span data-ttu-id="e83e9-163">每一個選擇性 XML 索引只能在單一 XML 資料行上建立。</span><span class="sxs-lookup"><span data-stu-id="e83e9-163">Each selective XML index can only be created on a single XML column.</span></span>  
  
-   <span data-ttu-id="e83e9-164">您無法在非 XML 資料行上建立選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="e83e9-164">You cannot create a selective XML index on a non-XML column.</span></span>  
  
-   <span data-ttu-id="e83e9-165">資料表中的每個 XML 資料行只能包含一個選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="e83e9-165">Each XML column in a table can have only one selective XML index.</span></span>  
  
-   <span data-ttu-id="e83e9-166">每一個資料表最多可以有 249 個選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="e83e9-166">Each table can have up to 249 selective XML indexes.</span></span>  
  
 <span data-ttu-id="e83e9-167">**所支援物件的限制**</span><span class="sxs-lookup"><span data-stu-id="e83e9-167">**Limitations on supported objects**</span></span>  
  
 <span data-ttu-id="e83e9-168">您無法在下列物件上建立選擇性 XML 索引：</span><span class="sxs-lookup"><span data-stu-id="e83e9-168">You cannot create selective XML indexes on the following objects:</span></span>  
  
1.  <span data-ttu-id="e83e9-169">檢視中的 XML 資料行。</span><span class="sxs-lookup"><span data-stu-id="e83e9-169">XML columns in a view.</span></span>  
  
2.  <span data-ttu-id="e83e9-170">XML 資料行的資料表值變數。</span><span class="sxs-lookup"><span data-stu-id="e83e9-170">Table-valued variable with XML columns.</span></span>  
  
3.  <span data-ttu-id="e83e9-171">XML 類型變數。</span><span class="sxs-lookup"><span data-stu-id="e83e9-171">XML type variables.</span></span>  
  
4.  <span data-ttu-id="e83e9-172">計算 XML 資料行。</span><span class="sxs-lookup"><span data-stu-id="e83e9-172">Computed XML columns.</span></span>  
  
5.  <span data-ttu-id="e83e9-173">深度超過 128 個巢狀節點的 XML 資料行。</span><span class="sxs-lookup"><span data-stu-id="e83e9-173">XML columns with a depth of more than 128 nested nodes.</span></span>  
  
 <span data-ttu-id="e83e9-174">**有關儲存的限制**</span><span class="sxs-lookup"><span data-stu-id="e83e9-174">**Limitations related to storage**</span></span>  
  
 <span data-ttu-id="e83e9-175">對於 XML 文件中可加入至索引的節點數目會有某一限度的限制。</span><span class="sxs-lookup"><span data-stu-id="e83e9-175">There is a finite limit on the number of nodes from the XML document that can be added to the index.</span></span> <span data-ttu-id="e83e9-176">選擇性 XML 索引會將 XML 文件對應到單一關聯式資料表。</span><span class="sxs-lookup"><span data-stu-id="e83e9-176">A selective XML index maps XML documents to a single relational table.</span></span> <span data-ttu-id="e83e9-177">因此，它不能在資料表的任一資料列中擁有超過 1024 個非 null 資料行。</span><span class="sxs-lookup"><span data-stu-id="e83e9-177">Therefore it cannot have more than 1024 non-null columns in any given row of the table.</span></span> <span data-ttu-id="e83e9-178">此外，疏鬆資料行的許多限制也會套用至選擇性 XML 索引，因為索引會使用疏鬆資料行進行儲存。</span><span class="sxs-lookup"><span data-stu-id="e83e9-178">Furthermore, many of the limitations of sparse columns also apply to selective XML indexes, because the indexes use sparse columns for storage.</span></span>  
  
 <span data-ttu-id="e83e9-179">任一資料列中支援的非 null 資料行數目上限取決於資料行中資料的大小：</span><span class="sxs-lookup"><span data-stu-id="e83e9-179">The maximum number of non-null columns supported in any given row depends on the size of the data in the columns:</span></span>  
  
-   <span data-ttu-id="e83e9-180">在最好的情況下，如果所有資料行都是 **bit**類型，則可支援 1024 個非 null 資料行。</span><span class="sxs-lookup"><span data-stu-id="e83e9-180">In the best case, 1024 non-null columns are supported when all columns are of type **bit**.</span></span>  
  
-   <span data-ttu-id="e83e9-181">在最差的情況下，如果所有資料行都是 **varchar**類型的大型物件，則只能支援 236 個非 null 資料行。</span><span class="sxs-lookup"><span data-stu-id="e83e9-181">In the worst case, only 236 non-null columns are supported when all columns are large objects of type **varchar**.</span></span>  
  
 <span data-ttu-id="e83e9-182">選擇性 XML 索引會在內部針對每一個索引的節點路徑使用一到四個資料行。</span><span class="sxs-lookup"><span data-stu-id="e83e9-182">Selective XML indexes use from one to four columns internally for every node path that is indexed.</span></span> <span data-ttu-id="e83e9-183">依據索引路徑中實際的資料大小而定，可進行索引的節點總數範圍可從 60 個到數百個節點。</span><span class="sxs-lookup"><span data-stu-id="e83e9-183">The total number of nodes that can be indexed ranges from 60 to several hundred nodes, depending on the actual size of the data in the indexed paths.</span></span>  
  
-   <span data-ttu-id="e83e9-184">在最差的情況下，如果節點路徑定義中的部分或全部節點是使用 `//` 對應，則索引節點的最大數目為 60。</span><span class="sxs-lookup"><span data-stu-id="e83e9-184">In the worst case, when some or all nodes are mapped using `//` in the node path definition, the maximum number of indexed nodes is 60.</span></span>  
  
-   <span data-ttu-id="e83e9-185">在最好的情況下，如果節點路徑定義中的節點都不是使用 `//` 對應，則索引節點的最大數目為 200。</span><span class="sxs-lookup"><span data-stu-id="e83e9-185">In the best case, when nodes are mapped without using `//` in the node path definition, the maximum number of indexed nodes is 200.</span></span>  
  
 <span data-ttu-id="e83e9-186">**選擇性 XML 索引會在您 CREATE 或 ALTER 索引時重建。**</span><span class="sxs-lookup"><span data-stu-id="e83e9-186">**Selective XML indexes are rebuilt when you CREATE or ALTER the index.**</span></span>  
  
 <span data-ttu-id="e83e9-187">當您 CREATE 或 ALTER 選擇性 XML 索引時，它會在單一執行緒的離線模式中重建。</span><span class="sxs-lookup"><span data-stu-id="e83e9-187">When you CREATE or ALTER a selective XML index, it is rebuilt in a single-threaded, offline mode.</span></span> <span data-ttu-id="e83e9-188">太多 ALTER 陳述式會對索引之 XML 文件上的查詢效能產生負面影響。</span><span class="sxs-lookup"><span data-stu-id="e83e9-188">Frequently ALTER statements negatively affect the performance of queries over the indexed XML documents.</span></span>  
  
 <span data-ttu-id="e83e9-189">**其他限制**</span><span class="sxs-lookup"><span data-stu-id="e83e9-189">**Other limitations**</span></span>  
  
-   <span data-ttu-id="e83e9-190">查詢提示中不支援選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="e83e9-190">Selective XML indexes are not supported in query hints.</span></span>  
  
-   <span data-ttu-id="e83e9-191">Database Tuning Advisor 中不支援選擇性 XML 索引和次要選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="e83e9-191">Selective XML indexes and secondary selective XML indexes are not supported in Database Tuning Advisor.</span></span>  
  

  
##  <a name="related-tasks"></a><a name="reltasks"></a> <span data-ttu-id="e83e9-192">相關工作</span><span class="sxs-lookup"><span data-stu-id="e83e9-192">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e83e9-193">**Task**</span><span class="sxs-lookup"><span data-stu-id="e83e9-193">**Task**</span></span>|<span data-ttu-id="e83e9-194">**主題**</span><span class="sxs-lookup"><span data-stu-id="e83e9-194">**Topic**</span></span>|  
|<span data-ttu-id="e83e9-195">當您建立或修改選擇性 XML 索引時，指定您要建立索引的節點路徑，以及選用的最佳化提示。</span><span class="sxs-lookup"><span data-stu-id="e83e9-195">Specify the node paths that you want to index and optional optimization hints when you create or alter a selective XML index.</span></span>|[<span data-ttu-id="e83e9-196">指定選擇性 XML 索引的路徑和最佳化提示</span><span class="sxs-lookup"><span data-stu-id="e83e9-196">Specify Paths and Optimization Hints for Selective XML Indexes</span></span>](specify-paths-and-optimization-hints-for-selective-xml-indexes.md)|  
|<span data-ttu-id="e83e9-197">建立、修改或卸除選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="e83e9-197">Create, alter, or drop a selective XML index.</span></span>|[<span data-ttu-id="e83e9-198">建立、修改和卸除選擇性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="e83e9-198">Create, Alter, and Drop Selective XML Indexes</span></span>](create-alter-and-drop-selective-xml-indexes.md)|  
|<span data-ttu-id="e83e9-199">建立、修改或卸除次要選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="e83e9-199">Create, alter, or drop a secondary selective XML index.</span></span>|[<span data-ttu-id="e83e9-200">建立、修改和卸除次要選擇性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="e83e9-200">Create, Alter, and Drop Secondary Selective XML Indexes</span></span>](create-alter-and-drop-secondary-selective-xml-indexes.md)|  
  

  
  
