---
title: 階層式資料 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [SQL Server], tables to support
- hierarchyid [Database Engine], concepts
- hierarchical tables [Database Engine]
- SqlHierarchyId
- hierarchyid [Database Engine]
- hierarchical queries [SQL Server], using hierarchyid data type
ms.assetid: 19aefa9a-fbc2-4b22-92cf-67b8bb01671c
author: rothja
ms.author: jroth
ms.openlocfilehash: 351a5a4aa6bc1655b8da5fced3e51385dd498bdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595001"
---
# <a name="hierarchical-data-sql-server"></a><span data-ttu-id="0add2-102">階層式資料 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0add2-102">Hierarchical Data (SQL Server)</span></span>
  <span data-ttu-id="0add2-103">內建的 `hierarchyid` 資料類型可讓您更輕鬆地儲存及查詢階層式資料。</span><span class="sxs-lookup"><span data-stu-id="0add2-103">The built-in `hierarchyid` data type makes it easier to store and query hierarchical data.</span></span> <span data-ttu-id="0add2-104">`hierarchyid`已針對表示樹狀結構（這是最常見的階層式資料類型）進行優化。</span><span class="sxs-lookup"><span data-stu-id="0add2-104">`hierarchyid` is optimized for representing trees, which are the most common type of hierarchical data.</span></span>  
  
 <span data-ttu-id="0add2-105">階層式資料的定義為一組資料項目，這些資料項目會依據階層式關聯性，彼此相關。</span><span class="sxs-lookup"><span data-stu-id="0add2-105">Hierarchical data is defined as a set of data items that are related to each other by hierarchical relationships.</span></span> <span data-ttu-id="0add2-106">階層式關聯性表示資料的一個項目是另一個項目的父代。</span><span class="sxs-lookup"><span data-stu-id="0add2-106">Hierarchical relationships exist where one item of data is the parent of another item.</span></span> <span data-ttu-id="0add2-107">通常儲存在資料庫的階層式資料範例包含下列：</span><span class="sxs-lookup"><span data-stu-id="0add2-107">Examples of the hierarchical data that is commonly stored in databases include the following:</span></span>  
  
-   <span data-ttu-id="0add2-108">組織結構</span><span class="sxs-lookup"><span data-stu-id="0add2-108">An organizational structure</span></span>  
  
-   <span data-ttu-id="0add2-109">檔案系統</span><span class="sxs-lookup"><span data-stu-id="0add2-109">A file system</span></span>  
  
-   <span data-ttu-id="0add2-110">專案中的一組工作</span><span class="sxs-lookup"><span data-stu-id="0add2-110">A set of tasks in a project</span></span>  
  
-   <span data-ttu-id="0add2-111">語言詞彙的分類表</span><span class="sxs-lookup"><span data-stu-id="0add2-111">A taxonomy of language terms</span></span>  
  
-   <span data-ttu-id="0add2-112">網頁之間的連結圖形</span><span class="sxs-lookup"><span data-stu-id="0add2-112">A graph of links between Web pages</span></span>  
  
 <span data-ttu-id="0add2-113">使用 [hierarchyid](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) 做為資料類型來建立具有階層式結構的資料表，或描述儲存在另一個位置的階層式資料結構。</span><span class="sxs-lookup"><span data-stu-id="0add2-113">Use [hierarchyid](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) as a data type to create tables with a hierarchical structure, or to describe the hierarchical structure of data that is stored in another location.</span></span> <span data-ttu-id="0add2-114">使用 [中的](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) hierarchyid 函數 [!INCLUDE[tsql](../includes/tsql-md.md)] 來查詢及管理階層式資料。</span><span class="sxs-lookup"><span data-stu-id="0add2-114">Use the [hierarchyid functions](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) in [!INCLUDE[tsql](../includes/tsql-md.md)] to query and manage hierarchical data.</span></span>  
  
##  <a name="key-properties-of-hierarchyid"></a><a name="keyprops"></a> <span data-ttu-id="0add2-115">hierarchyid 的主要屬性</span><span class="sxs-lookup"><span data-stu-id="0add2-115">Key Properties of hierarchyid</span></span>  
 <span data-ttu-id="0add2-116">`hierarchyid` 資料類型的值代表樹狀目錄階層中的位置。</span><span class="sxs-lookup"><span data-stu-id="0add2-116">A value of the `hierarchyid` data type represents a position in a tree hierarchy.</span></span> <span data-ttu-id="0add2-117">`hierarchyid` 的值具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="0add2-117">Values for `hierarchyid` have the following properties:</span></span>  
  
-   <span data-ttu-id="0add2-118">極度壓縮</span><span class="sxs-lookup"><span data-stu-id="0add2-118">Extremely compact</span></span>  
  
     <span data-ttu-id="0add2-119">代表樹狀目錄 (含有 *n* 個節點) 中之節點所需的平均位元數目會因平均扇出 (節點子系的平均數目) 而不同。</span><span class="sxs-lookup"><span data-stu-id="0add2-119">The average number of bits that are required to represent a node in a tree with *n* nodes depends on the average fanout (the average number of children of a node).</span></span> <span data-ttu-id="0add2-120">若為小型扇出 (0-7)，其大小大約是 6\*logA*n* 個位元，其中 A 是平均扇出。</span><span class="sxs-lookup"><span data-stu-id="0add2-120">For small fanouts, (0-7) the size is about 6\*logA*n* bits, where A is the average fanout.</span></span> <span data-ttu-id="0add2-121">在平均 fanout 為 6 個階層之 100,000 人員的組織階層中，節點會佔用大約 38 位元。</span><span class="sxs-lookup"><span data-stu-id="0add2-121">A node in an organizational hierarchy of 100,000 people with an average fanout of 6 levels takes about 38 bits.</span></span> <span data-ttu-id="0add2-122">然後，這會四捨五入成 40 位元 (或 5 個位元組)，以便進行儲存。</span><span class="sxs-lookup"><span data-stu-id="0add2-122">This is rounded up to 40 bits, or 5 bytes, for storage.</span></span>  
  
-   <span data-ttu-id="0add2-123">比較是按照深度優先順序</span><span class="sxs-lookup"><span data-stu-id="0add2-123">Comparison is in depth-first order</span></span>  
  
     <span data-ttu-id="0add2-124">假設有兩個 `hierarchyid` 值**a**和**b**， **<b**表示在樹狀目錄的深度優先的遍歷中，b 之前。</span><span class="sxs-lookup"><span data-stu-id="0add2-124">Given two `hierarchyid` values **a** and **b**, **a<b** means a comes before b in a depth-first traversal of the tree.</span></span> <span data-ttu-id="0add2-125">`hierarchyid` 資料類型的索引採用深度優先順序，而且在深度優先周遊中彼此接近的節點會以彼此接近的方式儲存。</span><span class="sxs-lookup"><span data-stu-id="0add2-125">Indexes on `hierarchyid` data types are in depth-first order, and nodes close to each other in a depth-first traversal are stored near each other.</span></span> <span data-ttu-id="0add2-126">例如，某筆記錄的子系會儲存在該記錄旁。</span><span class="sxs-lookup"><span data-stu-id="0add2-126">For example, the children of a record are stored adjacent to that record.</span></span>  
  
-   <span data-ttu-id="0add2-127">支援任意插入和刪除</span><span class="sxs-lookup"><span data-stu-id="0add2-127">Support for arbitrary insertions and deletions</span></span>  
  
     <span data-ttu-id="0add2-128">透過使用 [GetDescendant](/sql/t-sql/data-types/getdescendant-database-engine) 方法，您就一定能夠在任何指定節點的右側、任何指定節點的左側，或任何兩個同層級之間產生同層級。</span><span class="sxs-lookup"><span data-stu-id="0add2-128">By using the [GetDescendant](/sql/t-sql/data-types/getdescendant-database-engine) method, it is always possible to generate a sibling to the right of any given node, to the left of any given node, or between any two siblings.</span></span> <span data-ttu-id="0add2-129">在階層中插入或刪除任意的節點數目時，比較屬性會保留下來。</span><span class="sxs-lookup"><span data-stu-id="0add2-129">The comparison property is maintained when an arbitrary number of nodes is inserted or deleted from the hierarchy.</span></span> <span data-ttu-id="0add2-130">大部分的插入和刪除項目都會保留壓縮度屬性。</span><span class="sxs-lookup"><span data-stu-id="0add2-130">Most insertions and deletions preserve the compactness property.</span></span> <span data-ttu-id="0add2-131">不過，兩個節點之間的插入項目則會以稍微少的壓縮表示來產生 hierarchyid 值。</span><span class="sxs-lookup"><span data-stu-id="0add2-131">However, insertions between two nodes will produce hierarchyid values with a slightly less compact representation.</span></span>  
  
  
##  <a name="limitations-of-hierarchyid"></a><a name="limits"></a> <span data-ttu-id="0add2-132">hierarchyid 的限制</span><span class="sxs-lookup"><span data-stu-id="0add2-132">Limitations of hierarchyid</span></span>  
 <span data-ttu-id="0add2-133">`hierarchyid`資料類型具有下列限制：</span><span class="sxs-lookup"><span data-stu-id="0add2-133">The `hierarchyid` data type has the following limitations:</span></span>  
  
-   <span data-ttu-id="0add2-134">`hierarchyid` 類型的資料行不會自動代表樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="0add2-134">A column of type `hierarchyid` does not automatically represent a tree.</span></span> <span data-ttu-id="0add2-135">應用程式負責決定是否要產生並指派 `hierarchyid` 值，以便讓資料列之間所需的關聯性反映在值中。</span><span class="sxs-lookup"><span data-stu-id="0add2-135">It is up to the application to generate and assign `hierarchyid` values in such a way that the desired relationship between rows is reflected in the values.</span></span> <span data-ttu-id="0add2-136">有些應用程式可能有 `hierarchyid` 類型的資料行，表示在另一個資料表中定義之階層的位置。</span><span class="sxs-lookup"><span data-stu-id="0add2-136">Some applications might have a column of type `hierarchyid` that indicates the location in a hierarchy defined in another table.</span></span>  
  
-   <span data-ttu-id="0add2-137">應用程式負責管理產生與指派 `hierarchyid` 值的並行。</span><span class="sxs-lookup"><span data-stu-id="0add2-137">It is up to the application to manage concurrency in generating and assigning `hierarchyid` values.</span></span> <span data-ttu-id="0add2-138">除非應用程式使用唯一索引鍵條件約束或透過自己的邏輯強制本身的唯一性，否則，不保證資料行中的 `hierarchyid` 值是唯一的。</span><span class="sxs-lookup"><span data-stu-id="0add2-138">There is no guarantee that `hierarchyid` values in a column are unique unless the application uses a unique key constraint or enforces uniqueness itself through its own logic.</span></span>  
  
-   <span data-ttu-id="0add2-139">由 `hierarchyid` 值代表的階層式關聯性不會像外部索引鍵關聯性般強制執行。</span><span class="sxs-lookup"><span data-stu-id="0add2-139">Hierarchical relationships represented by `hierarchyid` values are not enforced like a foreign key relationship.</span></span> <span data-ttu-id="0add2-140">如果 A 擁有子系 B，然後刪除 A 留下 B，讓關聯性變成不存在的記錄，這種階層式關聯性是可能發生而且有時候是恰當的。</span><span class="sxs-lookup"><span data-stu-id="0add2-140">It is possible and sometimes appropriate to have a hierarchical relationship where A has a child B, and then A is deleted leaving B with a relationship to a nonexistent record.</span></span> <span data-ttu-id="0add2-141">如果無法接受這種行為，應用程式必須在刪除父系前，查詢下階。</span><span class="sxs-lookup"><span data-stu-id="0add2-141">If this behavior is unacceptable, the application must query for descendants before deleting parents.</span></span>  
  
  
##  <a name="when-to-use-alternatives-to-hierarchyid"></a><a name="alternatives"></a> <span data-ttu-id="0add2-142">使用 hierarchyid 替代選項的時機</span><span class="sxs-lookup"><span data-stu-id="0add2-142">When to Use Alternatives to hierarchyid</span></span>  
 <span data-ttu-id="0add2-143">代表階層式資料的兩個 `hierarchyid` 替代選項為：</span><span class="sxs-lookup"><span data-stu-id="0add2-143">Two alternatives to `hierarchyid` for representing hierarchical data are:</span></span>  
  
-   <span data-ttu-id="0add2-144">父子式</span><span class="sxs-lookup"><span data-stu-id="0add2-144">Parent/Child</span></span>  
  
-   <span data-ttu-id="0add2-145">XML</span><span class="sxs-lookup"><span data-stu-id="0add2-145">XML</span></span>  
  
 <span data-ttu-id="0add2-146">`hierarchyid` 通常優先於這些替代選項。</span><span class="sxs-lookup"><span data-stu-id="0add2-146">`hierarchyid` is generally superior to these alternatives.</span></span> <span data-ttu-id="0add2-147">但是，以下詳述替代選項可能優先於 hierarchyid 的特定情況。</span><span class="sxs-lookup"><span data-stu-id="0add2-147">However, there are specific situations detailed below where the alternatives are likely superior.</span></span>  
  
### <a name="parentchild"></a><span data-ttu-id="0add2-148">父子式</span><span class="sxs-lookup"><span data-stu-id="0add2-148">Parent/Child</span></span>  
 <span data-ttu-id="0add2-149">使用父子式方式時，每個資料列都包含一個父系的參考。</span><span class="sxs-lookup"><span data-stu-id="0add2-149">When using the Parent/Child approach, each row contains a reference to the parent.</span></span> <span data-ttu-id="0add2-150">下表定義在父子關聯性中包含父系和子系資料列時所使用的一般資料表：</span><span class="sxs-lookup"><span data-stu-id="0add2-150">The following table defines a typical table used to contain the parent and the child rows in a Parent/Child relationship:</span></span>  
  
```  
USE AdventureWorks2012 ;  
GO  
  
CREATE TABLE ParentChildOrg  
   (  
    BusinessEntityID int PRIMARY KEY,  
    ManagerId int REFERENCES ParentChildOrg(BusinessEntityID),  
    EmployeeName nvarchar(50)   
   ) ;  
GO  
```  
  
 <span data-ttu-id="0add2-151">比較父子式和 `hierarchyid` 的一般作業</span><span class="sxs-lookup"><span data-stu-id="0add2-151">Comparing Parent/Child and `hierarchyid` for Common Operations</span></span>  
  
-   <span data-ttu-id="0add2-152">使用 `hierarchyid` 進行子樹查詢時，速度明顯加快。</span><span class="sxs-lookup"><span data-stu-id="0add2-152">Subtree queries are significantly faster with `hierarchyid`.</span></span>  
  
-   <span data-ttu-id="0add2-153">而使用 `hierarchyid` 進行直接下階查詢時，速度則稍慢。</span><span class="sxs-lookup"><span data-stu-id="0add2-153">Direct descendant queries are slightly slower with `hierarchyid`.</span></span>  
  
-   <span data-ttu-id="0add2-154">使用 `hierarchyid` 移動非分葉節點時，速度比較慢。</span><span class="sxs-lookup"><span data-stu-id="0add2-154">Moving non-leaf nodes is slower with `hierarchyid`.</span></span>  
  
-   <span data-ttu-id="0add2-155">使用 `hierarchyid` 插入非分葉節點與插入或移動分葉節點時，其複雜程度相同。</span><span class="sxs-lookup"><span data-stu-id="0add2-155">Inserting non-leaf nodes and inserting or moving leaf nodes has the same complexity with `hierarchyid`.</span></span>  
  
 <span data-ttu-id="0add2-156">下列狀況存在時，最好使用父子式：</span><span class="sxs-lookup"><span data-stu-id="0add2-156">Parent/Child might be superior when the following conditions exist:</span></span>  
  
-   <span data-ttu-id="0add2-157">索引鍵的大小很重要。</span><span class="sxs-lookup"><span data-stu-id="0add2-157">The size of the key is critical.</span></span> <span data-ttu-id="0add2-158">如果節點數目相同，`hierarchyid` 值會等於或大於整數系列 (`smallint`、`int`、`bigint`) 值。</span><span class="sxs-lookup"><span data-stu-id="0add2-158">For the same number of nodes, a `hierarchyid` value is equal to or larger than an integer-family (`smallint`, `int`, `bigint`) value.</span></span> <span data-ttu-id="0add2-159">在極少的情況下，這是使用 [父子式] 的唯一原因，因為比起使用 [父子式] 結構時所需要的通用資料表運算式，`hierarchyid` 的 I/O 位置明顯較好，而且 CPU 的複雜性較高。</span><span class="sxs-lookup"><span data-stu-id="0add2-159">This is only a reason to use Parent/Child in rare cases, because `hierarchyid` has significantly better locality of I/O and CPU complexity than the common table expressions required when you are using a Parent/Child structure.</span></span>  
  
-   <span data-ttu-id="0add2-160">查詢很少會查詢整個階層的區段。</span><span class="sxs-lookup"><span data-stu-id="0add2-160">Queries rarely query across sections of the hierarchy.</span></span> <span data-ttu-id="0add2-161">換句話說，查詢通常只處理階層中的單一點。</span><span class="sxs-lookup"><span data-stu-id="0add2-161">In other words, queries usually address only a single point in the hierarchy.</span></span> <span data-ttu-id="0add2-162">在這些情況下，共同位置就不重要。</span><span class="sxs-lookup"><span data-stu-id="0add2-162">In these cases co-location is not important.</span></span> <span data-ttu-id="0add2-163">例如，如果組織資料表僅用於處理個別員工的薪資，最好使用 [父子式]。</span><span class="sxs-lookup"><span data-stu-id="0add2-163">For example, Parent/Child is superior when the organization table is only used to process payroll for individual employees.</span></span>  
  
-   <span data-ttu-id="0add2-164">非分葉的子樹會經常移動，因此效能非常重要。</span><span class="sxs-lookup"><span data-stu-id="0add2-164">Non-leaf subtrees move frequently and performance is very important.</span></span> <span data-ttu-id="0add2-165">在父子式表示中，變更資料列在階層中的位置會影響單一資料列。</span><span class="sxs-lookup"><span data-stu-id="0add2-165">In a parent/child representation changing the location of a row in a hierarchy affects a single row.</span></span> <span data-ttu-id="0add2-166">變更使用方式中資料列的位置 `hierarchyid` 會影響*n*個數據列，其中*n*是要移動之子樹中的節點數目。</span><span class="sxs-lookup"><span data-stu-id="0add2-166">Changing the location of a row in a `hierarchyid` usage affects *n* rows, where *n* is number of nodes in the sub-tree being moved.</span></span>  
  
     <span data-ttu-id="0add2-167">如果非分葉子樹經常移動且效能非常重要，但是大部分的移動都是在定義良好的階層層級進行時，請考慮將較高和較低的層級分割為兩個階層。</span><span class="sxs-lookup"><span data-stu-id="0add2-167">If the non-leaf subtrees move frequently and performance is important, but most of the moves are at a well-defined level of the hierarchy, consider splitting the higher and lower levels into two hierarchies.</span></span> <span data-ttu-id="0add2-168">這樣會全部移到較高階層的分葉層級中。</span><span class="sxs-lookup"><span data-stu-id="0add2-168">This makes all moves into leaf-levels of the higher hierarchy.</span></span> <span data-ttu-id="0add2-169">例如，請考慮由服務主控之網站的階層。</span><span class="sxs-lookup"><span data-stu-id="0add2-169">For instance, consider a hierarchy of Web sites hosted by a service.</span></span> <span data-ttu-id="0add2-170">網站包含許多以階層方式排列的頁面。</span><span class="sxs-lookup"><span data-stu-id="0add2-170">Sites contain many pages arranged in a hierarchical manner.</span></span> <span data-ttu-id="0add2-171">主控的網站可能會移到網站階層的其他位置，但是從屬的頁面很少會重新排列。</span><span class="sxs-lookup"><span data-stu-id="0add2-171">Hosted sites might be moved to other locations in the site hierarchy, but the subordinate pages are rarely re-arranged.</span></span> <span data-ttu-id="0add2-172">這可能會透過下列方式表示：</span><span class="sxs-lookup"><span data-stu-id="0add2-172">This could be represented via:</span></span>  
  
    ```  
    CREATE TABLE HostedSites   
       (  
        SiteId hierarchyid, PageId hierarchyid  
       ) ;  
    GO  
    ```  
  
  
### <a name="xml"></a><span data-ttu-id="0add2-173">XML</span><span class="sxs-lookup"><span data-stu-id="0add2-173">XML</span></span>  
 <span data-ttu-id="0add2-174">XML 文件是一個樹狀結構，因此，單一的 XML 資料類型執行個體可以代表一個完整的階層。</span><span class="sxs-lookup"><span data-stu-id="0add2-174">An XML document is a tree, and therefore a single XML data type instance can represent a complete hierarchy.</span></span> <span data-ttu-id="0add2-175">在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 建立 XML 索引時，會在 `hierarchyid` 內部使用值來代表階層中的位置。</span><span class="sxs-lookup"><span data-stu-id="0add2-175">In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] when an XML index is created, `hierarchyid` values are used internally to represent the position in the hierarchy.</span></span>  
  
 <span data-ttu-id="0add2-176">如果以下所有狀況成立，使用 XML 資料類型可能比較好：</span><span class="sxs-lookup"><span data-stu-id="0add2-176">Using XML data type can be superior when all the following are true:</span></span>  
  
-   <span data-ttu-id="0add2-177">永遠會儲存與擷取完整的階層。</span><span class="sxs-lookup"><span data-stu-id="0add2-177">The complete hierarchy is always stored and retrieved.</span></span>  
  
-   <span data-ttu-id="0add2-178">應用程式使用的資料為 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="0add2-178">The data is consumed in XML format by the application.</span></span>  
  
-   <span data-ttu-id="0add2-179">述詞搜尋會受到相當的限制，而且效能並不重要。</span><span class="sxs-lookup"><span data-stu-id="0add2-179">Predicate searches are extremely limited and not performance critical.</span></span>  
  
 <span data-ttu-id="0add2-180">例如，如果應用程式追蹤多個組織，務必儲存與擷取完整的組織階層，而且不要在單一組織中查詢，下列表單的資料表才可能有意義：</span><span class="sxs-lookup"><span data-stu-id="0add2-180">For example, if an application tracks multiple organizations, always stores and retrieves the complete organizational hierarchy, and does not query into a single organization, a table of the following form might make sense:</span></span>  
  
```  
CREATE TABLE XMLOrg   
    (  
    Orgid int,  
    Orgdata xml  
    ) ;  
GO  
```  
  
  
##  <a name="indexing-strategies-for-hierarchical-data"></a><a name="indexing"></a> <span data-ttu-id="0add2-181">階層式資料的索引策略</span><span class="sxs-lookup"><span data-stu-id="0add2-181">Indexing Strategies for Hierarchical Data</span></span>  
 <span data-ttu-id="0add2-182">編製階層式資料索引有兩種策略：</span><span class="sxs-lookup"><span data-stu-id="0add2-182">There are two strategies for indexing hierarchical data:</span></span>  
  
-   <span data-ttu-id="0add2-183">**深度優先**</span><span class="sxs-lookup"><span data-stu-id="0add2-183">**Depth-first**</span></span>  
  
     <span data-ttu-id="0add2-184">如果是深度優先的索引，會將子樹中的資料列儲存在彼此的附近。</span><span class="sxs-lookup"><span data-stu-id="0add2-184">A depth-first index stores the rows in a subtree near each other.</span></span> <span data-ttu-id="0add2-185">例如，透過某位經理管理的所有員工都會儲存在經理記錄的附近。</span><span class="sxs-lookup"><span data-stu-id="0add2-185">For example, all employees that report through a manager are stored near their managers' record.</span></span>  
  
     <span data-ttu-id="0add2-186">在深度優先的索引中，節點子樹的所有節點都會位於相同位置。</span><span class="sxs-lookup"><span data-stu-id="0add2-186">In a depth-first index, all nodes in the subtree of a node are co-located.</span></span> <span data-ttu-id="0add2-187">因此，深度優先的索引在回應關於子樹的查詢 (例如，「尋找此資料夾及其子資料夾中的所有檔案」) 時很有效率。</span><span class="sxs-lookup"><span data-stu-id="0add2-187">Depth-first indexes are therefore efficient for answering queries about subtrees, such as "Find all files in this folder and its subfolders".</span></span>  
  
-   <span data-ttu-id="0add2-188">**廣度優先**</span><span class="sxs-lookup"><span data-stu-id="0add2-188">**Breadth-first**</span></span>  
  
     <span data-ttu-id="0add2-189">如果是廣度優先，會將資料列與階層的每個層級儲存在一起。</span><span class="sxs-lookup"><span data-stu-id="0add2-189">A breadth-first stores the rows each level of the hierarchy together.</span></span> <span data-ttu-id="0add2-190">例如，直接由相同經理管理之員工的記錄會儲存在彼此的附近。</span><span class="sxs-lookup"><span data-stu-id="0add2-190">For example, the records of employees who directly report to the same manager are stored near each other.</span></span>  
  
     <span data-ttu-id="0add2-191">在廣度優先的索引中，節點的所有直接子系都會位於相同位置。</span><span class="sxs-lookup"><span data-stu-id="0add2-191">In a breadth-first index all direct children of a node are co-located.</span></span> <span data-ttu-id="0add2-192">因此，廣度優先的索引在回應關於下層子系的查詢 (例如，「尋找直接回報給此經理的所有員工」) 時很有效率。</span><span class="sxs-lookup"><span data-stu-id="0add2-192">Breadth-first indexes are therefore efficient for answering queries about immediate children, such as "Find all employees who report directly to this manager".</span></span>  
  
 <span data-ttu-id="0add2-193">不論是讓深度優先、廣度優先，或是兩者，還是那個要產生叢集索引鍵 (如果有的話)，都取決於上述查詢類型的相對重要性，以及 SELECT 和DML 作業的相對重要性。</span><span class="sxs-lookup"><span data-stu-id="0add2-193">Whether to have depth-first, breadth-first, or both, and which to make the clustering key (if any), depends on the relative importance of the above types of queries, and the relative importance of SELECT vs. DML operations.</span></span> <span data-ttu-id="0add2-194">如需索引策略的詳細範例，請參閱＜ [Tutorial: Using the hierarchyid Data Type](../relational-databases/tables/tutorial-using-the-hierarchyid-data-type.md)＞。</span><span class="sxs-lookup"><span data-stu-id="0add2-194">For a detailed example of indexing strategies, see [Tutorial: Using the hierarchyid Data Type](../relational-databases/tables/tutorial-using-the-hierarchyid-data-type.md).</span></span>  
  
  
### <a name="creating-indexes"></a><span data-ttu-id="0add2-195">建立索引</span><span class="sxs-lookup"><span data-stu-id="0add2-195">Creating Indexes</span></span>  
 <span data-ttu-id="0add2-196">GetLevel() 方法可以用來建立廣度優先排序。</span><span class="sxs-lookup"><span data-stu-id="0add2-196">The GetLevel() method can be used to create a breadth first ordering.</span></span> <span data-ttu-id="0add2-197">在下列範例中，會同時建立廣度優先和深度優先的索引：</span><span class="sxs-lookup"><span data-stu-id="0add2-197">In the following example, both breadth-first and depth-first indexes are created:</span></span>  
  
```wmimof  
USE AdventureWorks2012 ;   
GO  
  
CREATE TABLE Organization  
   (  
    BusinessEntityID hierarchyid,  
    OrgLevel as BusinessEntityID.GetLevel(),   
    EmployeeName nvarchar(50) NOT NULL  
   ) ;  
GO  
  
CREATE CLUSTERED INDEX Org_Breadth_First   
ON Organization(OrgLevel,BusinessEntityID) ;  
GO  
  
CREATE UNIQUE INDEX Org_Depth_First   
ON Organization(BusinessEntityID) ;  
GO  
```  
  
  
## <a name="examples"></a><span data-ttu-id="0add2-198">範例</span><span class="sxs-lookup"><span data-stu-id="0add2-198">Examples</span></span>  
  
### <a name="simple-example"></a><span data-ttu-id="0add2-199">簡單範例</span><span class="sxs-lookup"><span data-stu-id="0add2-199">Simple Example</span></span>  
 <span data-ttu-id="0add2-200">下列範例有意經過簡化以協助您開始使用。</span><span class="sxs-lookup"><span data-stu-id="0add2-200">The following example is intentionally simplistic to help you get started.</span></span> <span data-ttu-id="0add2-201">首先，建立資料表以保留一些地理資料。</span><span class="sxs-lookup"><span data-stu-id="0add2-201">First create a table to hold some geography data.</span></span>  
  
```  
CREATE TABLE SimpleDemo  
(Level hierarchyid NOT NULL,  
Location nvarchar(30) NOT NULL,  
LocationType nvarchar(9) NULL);  
```  
  
 <span data-ttu-id="0add2-202">現在，插入一些大陸、國家/地區、州和城市的資料。</span><span class="sxs-lookup"><span data-stu-id="0add2-202">Now insert data for some continents, countries, states, and cities.</span></span>  
  
```  
INSERT SimpleDemo  
VALUES   
('/1/', 'Europe', 'Continent'),  
('/2/', 'South America', 'Continent'),  
('/1/1/', 'France', 'Country'),  
('/1/1/1/', 'Paris', 'City'),  
('/1/2/1/', 'Madrid', 'City'),  
('/1/2/', 'Spain', 'Country'),  
('/3/', 'Antarctica', 'Continent'),  
('/2/1/', 'Brazil', 'Country'),  
('/2/1/1/', 'Brasilia', 'City'),  
('/2/1/2/', 'Bahia', 'State'),  
('/2/1/2/1/', 'Salvador', 'City'),  
('/3/1/', 'McMurdo Station', 'City');  
```  
  
 <span data-ttu-id="0add2-203">選取資料，並加入資料行以將層級資料轉換為容易了解的文字值。</span><span class="sxs-lookup"><span data-stu-id="0add2-203">Select the data, adding a column that converts the Level data into a text value that is easy to understand.</span></span> <span data-ttu-id="0add2-204">此查詢也會依 `hierarchyid` 資料類型來排序結果。</span><span class="sxs-lookup"><span data-stu-id="0add2-204">This query also orders the result by the `hierarchyid` data type.</span></span>  
  
```  
SELECT CAST(Level AS nvarchar(100)) AS [Converted Level], *   
FROM SimpleDemo ORDER BY Level;  
```  
  
 [!INCLUDE[ssResult](../includes/ssresult-md.md)]  
  
```  
Converted Level  Level     Location         LocationType  
/1/              0x58      Europe           Continent  
/1/1/            0x5AC0    France           Country  
/1/1/1/          0x5AD6    Paris            City  
/1/2/            0x5B40    Spain            Country  
/1/2/1/          0x5B56    Madrid           City  
/2/              0x68      South America    Continent  
/2/1/            0x6AC0    Brazil           Country  
/2/1/1/          0x6AD6    Brasilia         City  
/2/1/2/          0x6ADA    Bahia            State  
/2/1/2/1/        0x6ADAB0  Salvador         City  
/3/              0x78      Antarctica       Continent  
/3/1/            0x7AC0    McMurdo Station  City  
```  
  
 <span data-ttu-id="0add2-205">請注意，即使階層內部不一致，仍具有有效的結構。</span><span class="sxs-lookup"><span data-stu-id="0add2-205">Notice that the hierarchy is has a valid structure, even though it is not internally consistent.</span></span> <span data-ttu-id="0add2-206">Bahia 是唯一的州。</span><span class="sxs-lookup"><span data-stu-id="0add2-206">Bahia is the only state.</span></span> <span data-ttu-id="0add2-207">它會在階層中以 Brasilia 城市的同層級顯示。</span><span class="sxs-lookup"><span data-stu-id="0add2-207">It appears in the hierarchy as a peer of the city Brasilia.</span></span> <span data-ttu-id="0add2-208">同樣地，McMurdo Station 沒有父國家/地區。</span><span class="sxs-lookup"><span data-stu-id="0add2-208">Similarly, McMurdo Station does not have a parent country.</span></span> <span data-ttu-id="0add2-209">使用者必須決定此階層類型是否適用。</span><span class="sxs-lookup"><span data-stu-id="0add2-209">Users must decide if this type of hierarchy is appropriate for their use.</span></span>  
  
 <span data-ttu-id="0add2-210">加入另一個資料列並選取結果。</span><span class="sxs-lookup"><span data-stu-id="0add2-210">Add another row and select the results.</span></span>  
  
```  
INSERT SimpleDemo  
VALUES ('/1/3/1/', 'Kyoto', 'City'), ('/1/3/1/', 'London', 'City');  
SELECT CAST(Level AS nvarchar(100)) AS [Converted Level], * FROM SimpleDemo ORDER BY Level;  
```  
  
 <span data-ttu-id="0add2-211">這會顯示更多可能的問題。</span><span class="sxs-lookup"><span data-stu-id="0add2-211">This demonstrates more possible problems.</span></span> <span data-ttu-id="0add2-212">Kyoto 可插入為層級 `/1/3/1/` ，但卻沒有父層級 `/1/3/`。</span><span class="sxs-lookup"><span data-stu-id="0add2-212">Kyoto can be inserted as level `/1/3/1/` even though there is no parent level `/1/3/`.</span></span> <span data-ttu-id="0add2-213">而 London 和 Kyoto 的 `hierarchyid` 值相同。</span><span class="sxs-lookup"><span data-stu-id="0add2-213">And both London and Kyoto have the same value for the `hierarchyid`.</span></span> <span data-ttu-id="0add2-214">同樣地，使用者必須決定此階層類型是否適用，並封鎖不適用的值。</span><span class="sxs-lookup"><span data-stu-id="0add2-214">Again, users must decide if this type of hierarchy is appropriate for their use, and block values that are invalid for their usage.</span></span>  
  
 <span data-ttu-id="0add2-215">此外，此資料表未使用階層 `'/'`的頂端。</span><span class="sxs-lookup"><span data-stu-id="0add2-215">Also, this table did not use the top of the hierarchy `'/'`.</span></span> <span data-ttu-id="0add2-216">由於所有大陸沒有共同的父系，因此已省略。</span><span class="sxs-lookup"><span data-stu-id="0add2-216">It was omitted because there is no common parent of all the continents.</span></span> <span data-ttu-id="0add2-217">您可以加入整個地球，以加入一個父系。</span><span class="sxs-lookup"><span data-stu-id="0add2-217">You can add one by adding the whole planet.</span></span>  
  
```  
INSERT SimpleDemo  
VALUES ('/', 'Earth', 'Planet');  
```  
  
##  <a name="related-tasks"></a><a name="tasks"></a> <span data-ttu-id="0add2-218">相關工作</span><span class="sxs-lookup"><span data-stu-id="0add2-218">Related Tasks</span></span>  
  
###  <a name="migrating-from-parentchild-to-hierarchyid"></a><a name="migrating"></a> <span data-ttu-id="0add2-219">從父子式移轉到 hierarchyid</span><span class="sxs-lookup"><span data-stu-id="0add2-219">Migrating from Parent/Child to hierarchyid</span></span>  
 <span data-ttu-id="0add2-220">大部分的樹狀目錄都是使用 [父子式] 代表。</span><span class="sxs-lookup"><span data-stu-id="0add2-220">Most trees are represented using Parent/Child.</span></span> <span data-ttu-id="0add2-221">從 [父子式] 結構移轉到使用 `hierarchyid` 的資料表最簡單的方式，就是使用暫存資料行或暫存資料表來追蹤每個階層層級的節點數。</span><span class="sxs-lookup"><span data-stu-id="0add2-221">The easiest way to migrate from a Parent/Child structure to a table using `hierarchyid` is to use a temporary column or a temporary table to keep track of the number of nodes at each level of the hierarchy.</span></span> <span data-ttu-id="0add2-222">如需遷移 [父子式] 資料表的範例，請參閱 [教學課程：使用 hierarchyid 資料類型](../relational-databases/tables/tutorial-using-the-hierarchyid-data-type.md)的第 1 課。</span><span class="sxs-lookup"><span data-stu-id="0add2-222">For an example of migrating a Parent/Child table, see lesson 1 of [Tutorial: Using the hierarchyid Data Type](../relational-databases/tables/tutorial-using-the-hierarchyid-data-type.md).</span></span>  
  
  
###  <a name="managing-a-tree-using-hierarchyid"></a><a name="BKMK_ManagingTrees"></a> <span data-ttu-id="0add2-223">使用 hierarchyid 管理樹狀結構</span><span class="sxs-lookup"><span data-stu-id="0add2-223">Managing a Tree Using hierarchyid</span></span>  
 <span data-ttu-id="0add2-224">雖然 `hierarchyid` 資料行不需要代表樹狀結構，但是應用程式可以輕易地確認這就是樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="0add2-224">Although a `hierarchyid` column does not necessarily represent a tree, an application can easily ensure that it does.</span></span>  
  
-   <span data-ttu-id="0add2-225">產生新值時，請執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="0add2-225">When generating new values, do one of the following:</span></span>  
  
    -   <span data-ttu-id="0add2-226">追蹤父資料列中的最後一個子系號碼。</span><span class="sxs-lookup"><span data-stu-id="0add2-226">Keep track of the last child number in the parent row.</span></span>  
  
    -   <span data-ttu-id="0add2-227">計算最後一個子系。</span><span class="sxs-lookup"><span data-stu-id="0add2-227">Compute the last child.</span></span> <span data-ttu-id="0add2-228">若要有效率地執行這個動作，需要使用廣度優先索引。</span><span class="sxs-lookup"><span data-stu-id="0add2-228">Doing this efficiently requires a breadth-first index.</span></span>  
  
-   <span data-ttu-id="0add2-229">在資料行上建立唯一的索引 (也許是叢集索引鍵的一部份) 以強制執行唯一性。</span><span class="sxs-lookup"><span data-stu-id="0add2-229">Enforce uniqueness by creating a unique index on the column, perhaps as part of a clustering key.</span></span> <span data-ttu-id="0add2-230">若要確保插入唯一的值，請執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="0add2-230">To ensure that unique values are inserted, do one of the following:</span></span>  
  
    -   <span data-ttu-id="0add2-231">偵測唯一的索引鍵違規失敗，然後重試。</span><span class="sxs-lookup"><span data-stu-id="0add2-231">Detect unique key violation failures and retry.</span></span>  
  
    -   <span data-ttu-id="0add2-232">判斷每個新子節點的唯一性，然後插入該子節點做為可序列化交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="0add2-232">Determine the uniqueness of each new child node, and insert it as part of a serializable transaction.</span></span>  
  
  
#### <a name="example-using-error-detection"></a><span data-ttu-id="0add2-233">使用錯誤偵測的範例</span><span class="sxs-lookup"><span data-stu-id="0add2-233">Example Using Error Detection</span></span>  
 <span data-ttu-id="0add2-234">在下列範例中，範例程式碼會計算新子系的 **EmployeeId** 值，然後偵測任何索引鍵違規，並傳回 **INS_EMP** 標記，以便為新的資料列重新計算 **EmployeeId** 值：</span><span class="sxs-lookup"><span data-stu-id="0add2-234">In the following example, the sample code computes the new child **EmployeeId** value, and then detects any key violation and returns to **INS_EMP** marker to recompute the **EmployeeId** value for the new row:</span></span>  
  
```  
USE AdventureWorks ;  
GO  
  
CREATE TABLE Org_T1  
   (  
    EmployeeId hierarchyid PRIMARY KEY,  
    OrgLevel AS EmployeeId.GetLevel(),  
    EmployeeName nvarchar(50)   
   ) ;  
GO  
  
CREATE INDEX Org_BreadthFirst ON Org_T1(OrgLevel, EmployeeId)  
GO  
  
CREATE PROCEDURE AddEmp(@mgrid hierarchyid, @EmpName nvarchar(50) )   
AS  
BEGIN  
    DECLARE @last_child hierarchyid  
INS_EMP:   
    SELECT @last_child = MAX(EmployeeId) FROM Org_T1   
    WHERE EmployeeId.GetAncestor(1) = @mgrid  
INSERT Org_T1 (EmployeeId, EmployeeName)  
SELECT @mgrid.GetDescendant(@last_child, NULL), @EmpName   
-- On error, return to INS_EMP to recompute @last_child  
IF @@error <> 0 GOTO INS_EMP   
END ;  
GO  
```  
  
  
#### <a name="example-using-a-serializable-transaction"></a><span data-ttu-id="0add2-235">使用序列化交易的範例</span><span class="sxs-lookup"><span data-stu-id="0add2-235">Example Using a Serializable Transaction</span></span>  
 <span data-ttu-id="0add2-236">**Org_BreadthFirst** 索引可確定判斷 **@last_child** 會使用範圍搜尋。</span><span class="sxs-lookup"><span data-stu-id="0add2-236">The **Org_BreadthFirst** index ensures that determining **@last_child** uses a range seek.</span></span> <span data-ttu-id="0add2-237">除了應用程式可能想要檢查的其他錯誤情況之外，插入後的重複索引鍵違規會指出嘗試加入具有相同識別碼的多個員工，因此 **@last_child** 必須重新計算。</span><span class="sxs-lookup"><span data-stu-id="0add2-237">In addition to other error cases an application might want to check, a duplicate key violation after the insert indicates an attempt to add multiple employees with the same id, and therefore **@last_child** must be recomputed.</span></span> <span data-ttu-id="0add2-238">下列程式碼使用序列化交易與廣度優先索引來計算新的節點值：</span><span class="sxs-lookup"><span data-stu-id="0add2-238">The following code uses a serializable transaction and a breadth-first index to compute the new node value:</span></span>  
  
```  
CREATE TABLE Org_T2  
    (  
    EmployeeId hierarchyid PRIMARY KEY,  
    LastChild hierarchyid,   
    EmployeeName nvarchar(50)   
    ) ;  
GO  
  
CREATE PROCEDURE AddEmp(@mgrid hierarchyid, @EmpName nvarchar(50))   
AS  
BEGIN  
DECLARE @last_child hierarchyid  
SET TRANSACTION ISOLATION LEVEL SERIALIZABLE  
BEGIN TRANSACTION   
  
UPDATE Org_T2   
SET @last_child = LastChild = EmployeeId.GetDescendant(LastChild,NULL)  
WHERE EmployeeId = @mgrid  
INSERT Org_T2 (EmployeeId, EmployeeName)   
    VALUES(@last_child, @EmpName)  
COMMIT  
END ;  
```  
  
 <span data-ttu-id="0add2-239">下列程式碼會使用三個資料列擴展資料表，然後傳回結果：</span><span class="sxs-lookup"><span data-stu-id="0add2-239">The following code populates the table with three rows and returns the results:</span></span>  
  
```  
INSERT Org_T2 (EmployeeId, EmployeeName)   
    VALUES(hierarchyid::GetRoot(), 'David') ;  
GO  
AddEmp 0x , 'Sariya'  
GO  
AddEmp 0x58 , 'Mary'  
GO  
SELECT * FROM Org_T2  
```  
  
 [!INCLUDE[ssResult](../includes/ssresult-md.md)]  
  
```  
EmployeeId LastChild EmployeeName  
---------- --------- ------------  
0x        0x58       David  
0x58      0x5AC0     Sariya  
0x5AC0    NULL       Mary  
```  
  
  
###  <a name="enforcing-a-tree"></a><a name="BKMK_EnforcingTrees"></a> <span data-ttu-id="0add2-240">強制執行樹狀結構</span><span class="sxs-lookup"><span data-stu-id="0add2-240">Enforcing a tree</span></span>  
 <span data-ttu-id="0add2-241">以上的範例說明應用程式可以如何確保樹狀結構的維護。</span><span class="sxs-lookup"><span data-stu-id="0add2-241">The above examples illustrate how an application can ensure that a tree is maintained.</span></span> <span data-ttu-id="0add2-242">若要透過條件約束強制執行樹狀結構，定義每個節點之父系的計算資料行可以使用傳回主要索引鍵識別碼的外部索引鍵條件約束建立。</span><span class="sxs-lookup"><span data-stu-id="0add2-242">To enforce a tree by using constraints, a computed column that defines the parent of each node can be created with a foreign key constraint back to the primary key id.</span></span>  
  
```  
CREATE TABLE Org_T3  
(  
   EmployeeId hierarchyid PRIMARY KEY,  
   ParentId AS EmployeeId.GetAncestor(1) PERSISTED    
      REFERENCES Org_T3(EmployeeId),  
   LastChild hierarchyid,   
   EmployeeName nvarchar(50)  
)  
GO  
```  
  
 <span data-ttu-id="0add2-243">不信任可以維護階層式樹狀結構的程式碼具有資料表的 DML 直接存取權時，最好使用這個方法強制關聯性。</span><span class="sxs-lookup"><span data-stu-id="0add2-243">This method of enforcing a relationship is preferred when code that is not trusted to maintain the hierarchical tree has direct DML access to the table.</span></span> <span data-ttu-id="0add2-244">不過，由於必須針對每個 DML 作業檢查條件約束，這個方法可能會降低效能。</span><span class="sxs-lookup"><span data-stu-id="0add2-244">However this method might reduce performance because the constraint must be checked on every DML operation.</span></span>  
  
  
###  <a name="finding-ancestors-by-using-the-clr"></a><a name="findclr"></a> <span data-ttu-id="0add2-245">透過使用 CLR 尋找上階</span><span class="sxs-lookup"><span data-stu-id="0add2-245">Finding Ancestors by Using the CLR</span></span>  
 <span data-ttu-id="0add2-246">與階層中兩個節點相關的常見作業就是尋找最低通用上階。</span><span class="sxs-lookup"><span data-stu-id="0add2-246">A common operation involving two nodes in a hierarchy is to find the lowest common ancestor.</span></span> <span data-ttu-id="0add2-247">這可以寫入 [!INCLUDE[tsql](../includes/tsql-md.md)] 或 CLR，因為 `hierarchyid` 這兩種類型都有提供。</span><span class="sxs-lookup"><span data-stu-id="0add2-247">This can be written in either [!INCLUDE[tsql](../includes/tsql-md.md)] or CLR, because the `hierarchyid` type is available in both.</span></span> <span data-ttu-id="0add2-248">因為效能將會更快，因此建議使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="0add2-248">CLR is recommended because performance will be faster.</span></span>  
  
 <span data-ttu-id="0add2-249">使用下列的 CLR 程式碼，列出上階並尋找最低通用上階：</span><span class="sxs-lookup"><span data-stu-id="0add2-249">Use the following CLR code to list ancestors and to find the lowest common ancestor:</span></span>  
  
```  
using System;  
using System.Collections;  
using System.Text;  
using Microsoft.SqlServer.Server;  
using Microsoft.SqlServer.Types;  
  
public partial class HierarchyId_Operations  
{  
    [SqlFunction(FillRowMethodName = "FillRow_ListAncestors")]  
    public static IEnumerable ListAncestors(SqlHierarchyId h)  
    {  
        while (!h.IsNull)  
        {  
            yield return (h);  
            h = h.GetAncestor(1);  
        }  
    }  
    public static void FillRow_ListAncestors(Object obj, out SqlHierarchyId ancestor)  
    {  
        ancestor = (SqlHierarchyId)obj;  
    }  
  
    public static HierarchyId CommonAncestor(SqlHierarchyId h1, HierarchyId h2)  
    {  
        while (!h1.IsDescendant(h2))  
            h1 = h1.GetAncestor(1);  
  
        return h1;  
    }  
}  
```  
  
 <span data-ttu-id="0add2-250">若要在下列 **範例中使用** ListAncestor **和** CommonAncestor [!INCLUDE[tsql](../includes/tsql-md.md)] 方法執行類似如下的程式碼，請在 **中建置 DLL 並建立** HierarchyId_Operations [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 組件：</span><span class="sxs-lookup"><span data-stu-id="0add2-250">To use the **ListAncestor** and **CommonAncestor** methods in the following [!INCLUDE[tsql](../includes/tsql-md.md)] examples, build the DLL and create the **HierarchyId_Operations** assembly in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by executing code similar to the following:</span></span>  
  
```  
CREATE ASSEMBLY HierarchyId_Operations   
FROM '<path to DLL>\ListAncestors.dll'  
GO  
```  
  
  
###  <a name="listing-ancestors"></a><a name="ancestors"></a> <span data-ttu-id="0add2-251">列出上階</span><span class="sxs-lookup"><span data-stu-id="0add2-251">Listing Ancestors</span></span>  
 <span data-ttu-id="0add2-252">建立節點上階清單是一個常見的作業，例如，在組織中顯示位置。</span><span class="sxs-lookup"><span data-stu-id="0add2-252">Creating a list of ancestors of a node is a common operation, for instance to show position in an organization.</span></span> <span data-ttu-id="0add2-253">其中一個方法是，利用以上定義的 **HierarchyId_Operations** 類別，使用資料表值函數：</span><span class="sxs-lookup"><span data-stu-id="0add2-253">One way of doing this is by using a table-valued-function using the **HierarchyId_Operations** class defined above:</span></span>  
  
 <span data-ttu-id="0add2-254">使用 [!INCLUDE[tsql](../includes/tsql-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="0add2-254">Using [!INCLUDE[tsql](../includes/tsql-md.md)]:</span></span>  
  
```  
CREATE FUNCTION ListAncestors (@node hierarchyid)  
RETURNS TABLE (node hierarchyid)  
AS  
EXTERNAL NAME HierarchyId_Operations.HierarchyId_Operations.ListAncestors  
GO  
```  
  
 <span data-ttu-id="0add2-255">使用範例：</span><span class="sxs-lookup"><span data-stu-id="0add2-255">Example of usage:</span></span>  
  
```  
DECLARE @h hierarchyid  
SELECT @h = OrgNode   
FROM HumanResources.EmployeeDemo    
WHERE LoginID = 'adventure-works\janice0' -- /1/1/5/2/  
  
SELECT LoginID, OrgNode.ToString() AS LogicalNode  
FROM HumanResources.EmployeeDemo AS ED  
JOIN ListAncestors(@h) AS A   
   ON ED.OrgNode = A.Node  
GO  
```  
  
  
###  <a name="finding-the-lowest-common-ancestor"></a><a name="lowestcommon"></a> <span data-ttu-id="0add2-256">尋找最低通用上階</span><span class="sxs-lookup"><span data-stu-id="0add2-256">Finding the Lowest Common Ancestor</span></span>  
 <span data-ttu-id="0add2-257">使用以上定義的 **HierarchyId_Operations** 類別建立下列的 [!INCLUDE[tsql](../includes/tsql-md.md)] 函數，尋找與階層中兩個節點相關的最低通用上階：</span><span class="sxs-lookup"><span data-stu-id="0add2-257">Using the **HierarchyId_Operations** class defined above, create the following [!INCLUDE[tsql](../includes/tsql-md.md)] function to find the lowest common ancestor involving two nodes in a hierarchy:</span></span>  
  
```  
CREATE FUNCTION CommonAncestor (@node1 hierarchyid, @node2 hierarchyid)  
RETURNS hierarchyid  
AS  
EXTERNAL NAME HierarchyId_Operations.HierarchyId_Operations.CommonAncestor  
GO  
```  
  
 <span data-ttu-id="0add2-258">使用範例：</span><span class="sxs-lookup"><span data-stu-id="0add2-258">Example of usage:</span></span>  
  
```  
DECLARE @h1 hierarchyid, @h2 hierarchyid  
  
SELECT @h1 = OrgNode   
FROM  HumanResources.EmployeeDemo   
WHERE LoginID = 'adventure-works\jossef0' -- Node is /1/1/3/  
  
SELECT @h2 = OrgNode   
FROM HumanResources.EmployeeDemo    
WHERE LoginID = 'adventure-works\janice0' -- Node is /1/1/5/2/  
  
SELECT OrgNode.ToString() AS LogicalNode, LoginID   
FROM HumanResources.EmployeeDemo    
WHERE OrgNode = dbo.CommonAncestor(@h1, @h2) ;  
```  
  
 <span data-ttu-id="0add2-259">產生的節點是 /1/1/</span><span class="sxs-lookup"><span data-stu-id="0add2-259">The resultant node is /1/1/</span></span>  
  
  
###  <a name="moving-subtrees"></a><a name="BKMK_MovingSubtrees"></a> <span data-ttu-id="0add2-260">移動子樹</span><span class="sxs-lookup"><span data-stu-id="0add2-260">Moving Subtrees</span></span>  
 <span data-ttu-id="0add2-261">另一個常見的作業是移動子樹。</span><span class="sxs-lookup"><span data-stu-id="0add2-261">Another common operation is moving subtrees.</span></span> <span data-ttu-id="0add2-262">下列程式會採用的子樹 **@oldMgr** ，使其 (包括 **@oldMgr**) 的子樹 **@newMgr** 。</span><span class="sxs-lookup"><span data-stu-id="0add2-262">The procedure below takes the subtree of **@oldMgr** and makes it (including **@oldMgr**) a subtree of **@newMgr**.</span></span>  
  
```  
CREATE PROCEDURE MoveOrg(@oldMgr nvarchar(256), @newMgr nvarchar(256) )  
AS  
BEGIN  
DECLARE @nold hierarchyid, @nnew hierarchyid  
SELECT @nold = OrgNode FROM HumanResources.EmployeeDemo WHERE LoginID = @oldMgr ;  
  
SET TRANSACTION ISOLATION LEVEL SERIALIZABLE  
BEGIN TRANSACTION  
SELECT @nnew = OrgNode FROM HumanResources.EmployeeDemo WHERE LoginID = @newMgr ;  
  
SELECT @nnew = @nnew.GetDescendant(max(OrgNode), NULL)   
FROM HumanResources.EmployeeDemo WHERE OrgNode.GetAncestor(1)=@nnew ;  
  
UPDATE HumanResources.EmployeeDemo    
SET OrgNode = OrgNode.GetReparentedValue(@nold, @nnew)  
WHERE OrgNode.IsDescendantOf(@nold) = 1 ;  
  
COMMIT TRANSACTION  
END ;  
GO  
```  
  
  
## <a name="see-also"></a><span data-ttu-id="0add2-263">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0add2-263">See Also</span></span>  
 <span data-ttu-id="0add2-264">[Hierarchyid 資料類型方法參考](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) </span><span class="sxs-lookup"><span data-stu-id="0add2-264">[hierarchyid Data Type Method Reference](/sql/t-sql/data-types/hierarchyid-data-type-method-reference) </span></span>  
 <span data-ttu-id="0add2-265">[Tutorial: Using the hierarchyid Data Type](../relational-databases/tables/tutorial-using-the-hierarchyid-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="0add2-265">[Tutorial: Using the hierarchyid Data Type](../relational-databases/tables/tutorial-using-the-hierarchyid-data-type.md) </span></span>  
 [<span data-ttu-id="0add2-266">hierarchyid &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0add2-266">hierarchyid &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/hierarchyid-data-type-method-reference)  
  
  
