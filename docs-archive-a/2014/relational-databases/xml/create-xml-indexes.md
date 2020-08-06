---
title: 建立 XML 索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- indexes [XML in SQL Server]
- XML indexes [SQL Server], creating
ms.assetid: 6ecac598-355d-4408-baf7-1b2e8d4cf7c1
author: rothja
ms.author: jroth
ms.openlocfilehash: 9e7800193222b8c9060fee1b247cc5585654cde4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706282"
---
# <a name="create-xml-indexes"></a><span data-ttu-id="cd6a4-102">建立 XML 索引</span><span class="sxs-lookup"><span data-stu-id="cd6a4-102">Create XML Indexes</span></span>
  <span data-ttu-id="cd6a4-103">此主題描述如何建立主要和次要 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-103">This topic describes how to create primary and secondary XML indexes.</span></span>  
  
## <a name="creating-a-primary-xml-index"></a><span data-ttu-id="cd6a4-104">建立主要 XML 索引</span><span class="sxs-lookup"><span data-stu-id="cd6a4-104">Creating a Primary XML Index</span></span>  
 <span data-ttu-id="cd6a4-105">若要建立主要 XML 索引，請使用 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-105">To create a primary XML index, use the [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL statement.</span></span> <span data-ttu-id="cd6a4-106">並非所有供 XML 索引使用的選項都有在 XML 索引中受到支援。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-106">Not all options available for non-XML indexes are supported on XML indexes.</span></span>  
  
 <span data-ttu-id="cd6a4-107">在建立 XML 索引時請注意下列項目：</span><span class="sxs-lookup"><span data-stu-id="cd6a4-107">Note the following when you are creating an XML index:</span></span>  
  
-   <span data-ttu-id="cd6a4-108">若要建立主要 XML 索引，包含要索引的 XML 資料行之資料表 (稱為基底資料表)，必須在主索引鍵上有叢集索引。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-108">To create a primary XML index, the table that contains the XML column being indexed, called the base table, must have a clustered index on the primary key.</span></span> <span data-ttu-id="cd6a4-109">這將可確保如果基底資料表已分割，可使用相同的資料分割結構描述與資料分割函數來分割主要 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-109">This makes sure that if the base table is partitioned, the primary XML index can be partitioned by using the same partitioning scheme and partitioning function.</span></span>  
  
-   <span data-ttu-id="cd6a4-110">如果 XML 索引存在，將無法修改資料表的叢集索引鍵、主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-110">If an XML index exists, the clustered, primary key of the table cannot be modified.</span></span> <span data-ttu-id="cd6a4-111">您必須在修改主索引鍵前，先卸除資料表上的所有 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-111">You will have to drop all XML indexes on the table before modifying the primary key.</span></span>  
  
-   <span data-ttu-id="cd6a4-112">在單一 `xml` 類型資料行上可建立主要 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-112">A primary XML index can be created on a single `xml` type column.</span></span> <span data-ttu-id="cd6a4-113">您無法以作為索引鍵資料行的 XML 類型資料行，建立任何其他類型的索引。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-113">You cannot create any other type of index with the XML type column as a key column.</span></span> <span data-ttu-id="cd6a4-114">不過，您可以在非 XML 索引中包含 `xml` L 類型資料行。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-114">However, you can include the `xml` L type column in a non-XML index.</span></span> <span data-ttu-id="cd6a4-115">在資料表中的每個 `xml` 類型資料行都有其自己的主要 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-115">Each `xml` type column in a table can have its own primary XML index.</span></span> <span data-ttu-id="cd6a4-116">不過，每個 `xml` 類型資料行只允許一個主要 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-116">However, only one primary XML index per `xml` type column is permitted.</span></span>  
  
-   <span data-ttu-id="cd6a4-117">XML 索引是存在於與非 XML 索引相同的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-117">XML indexes exist in the same namespace as non-XML indexes.</span></span> <span data-ttu-id="cd6a4-118">因此，在相同名稱的相同資料表上將無法同時擁有 XML 索引與非 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-118">Therefore, you cannot have an XML index and a non-XML index on the same table with the same name.</span></span>  
  
-   <span data-ttu-id="cd6a4-119">IGNORE_DUP_KEY 與 ONLINE 選項永遠為 XML 索引設定為 OFF。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-119">IGNORE_DUP_KEY and ONLINE options of are always set to OFF for XML indexes.</span></span> <span data-ttu-id="cd6a4-120">您可用 OFF 的值指定這些選項。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-120">You can specify these options with a value of OFF.</span></span>  
  
-   <span data-ttu-id="cd6a4-121">使用者資料表的檔案群組或資料分割資訊可套用於 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-121">The filegroup or partitioning information of the user table is applied to the XML index.</span></span> <span data-ttu-id="cd6a4-122">使用者無法在 XML 索引上分開指定這些選項。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-122">Users cannot specify these separately on an XML index.</span></span>  
  
-   <span data-ttu-id="cd6a4-123">DROP_EXISTING 索引選項可卸除主要 XML 索引並建立新的主要 XML 索引，或是卸除次要 XML 索引並建立新的次要 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-123">The DROP_EXISTING index option can drop a primary XML index and create a new primary XML index, or drop a secondary XML index and create a new secondary XML index.</span></span> <span data-ttu-id="cd6a4-124">不過，這個選項無法卸除次要 XML 索引以建立新主要 XML 索引，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-124">However, this option cannot drop a secondary XML index to create a new primary XML index or vice versa.</span></span>  
  
-   <span data-ttu-id="cd6a4-125">主要 XML 索引名稱的限制與檢視名稱的限制相同。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-125">Primary XML index names have the same restrictions as view names.</span></span>  
  
 <span data-ttu-id="cd6a4-126">您無法在 `xml` view 的類型資料行、具有類型資料行的**資料表**值變數 `xml` 或類型變數上建立 XML 索引 `xml` 。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-126">You cannot create an XML index on an `xml` type column in a view, on a **table** valued variable with `xml` type columns, or `xml` type variables.</span></span>  
  
-   <span data-ttu-id="cd6a4-127">若要使用 ALTER TABLE ALTER COLUMN 選項，將 `xml` 類型資料行從不具類型變更為具類型的 XML (反之亦然)，則在資料行上就不應存在任何 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-127">To change an `xml` type column from untyped to typed XML, or vice versa, by using the ALTER TABLE ALTER COLUMN option, no XML index on the column should exist.</span></span> <span data-ttu-id="cd6a4-128">如果 XML 索引確實存在，必須在嘗試變更資料行類型前先卸除它。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-128">If one does exist, it must be dropped before the column type change is tried.</span></span>  
  
-   <span data-ttu-id="cd6a4-129">在建立 XML 索引時，必須將 ARITHABORT 選項設定為 ON。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-129">The option ARITHABORT must be set to ON when an XML index is created.</span></span> <span data-ttu-id="cd6a4-130">若要使用 XML 資料類型方法查詢、插入、刪除或更新 XML 資料行中的值，必須在連接上設定相同的選項。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-130">To query, insert, delete, or update values in the XML column using XML data type methods, the same option must be set on the connection.</span></span> <span data-ttu-id="cd6a4-131">若未設定，XML 資料類型方法將會失敗。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-131">If it is not, the XML data type methods will fail.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cd6a4-132">在目錄檢視中可以找到關於 XML 索引的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-132">Information about an XML index can be found in catalog views.</span></span> <span data-ttu-id="cd6a4-133">不過，並不支援 **sp_helpindex** 。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-133">However, **sp_helpindex** is not supported.</span></span> <span data-ttu-id="cd6a4-134">在本主題後面所提供的範例將示範如何查詢目錄檢視，以尋找 XML 索引資訊。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-134">Examples provided later in this topic show how to query the catalog views to find XML index information.</span></span>  
  
 <span data-ttu-id="cd6a4-135">在包含 XML 結構描述類型 **xs:date** 或 **xs:dateTime** (或是這些類型的任何子類型) 值 (該值的年份小於 1) 的 XML 資料類型資料行上建立或重新建立主要 XML 索引時， [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 和更新版本中的索引建立會失敗。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-135">When creating or recreating a primary XML index on an XML data type column that contains values of the XML Schema types **xs:date** or **xs:dateTime** (or any subtypes of these types) that have a year of less than 1, the index creation will fail in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions.</span></span> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="cd6a4-136">允許這些值，所以在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]中產生之資料庫內建立索引時，可能會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-136">allowed these values, so this problem can occur when creating indexes in a database generated in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="cd6a4-137">如需詳細資訊，請參閱 [比較具類型的 XML 與不具類型的 XML](../xml/compare-typed-xml-to-untyped-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-137">For more information, see [Compare Typed XML to Untyped XML](../xml/compare-typed-xml-to-untyped-xml.md).</span></span>  
  
### <a name="example-creating-a-primary-xml-index"></a><span data-ttu-id="cd6a4-138">範例：建立主要 XML 索引</span><span class="sxs-lookup"><span data-stu-id="cd6a4-138">Example: Creating a Primary XML Index</span></span>  
 <span data-ttu-id="cd6a4-139">在大部分的範例中，都是使用資料表 T (pk INT PRIMARY KEY, xCol XML) 和不具類型的 XML 資料行。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-139">Table T (pk INT PRIMARY KEY, xCol XML) with an untyped XML column is used in most of the examples.</span></span> <span data-ttu-id="cd6a4-140">這些都可以用一種直接的方法來擴充成具類型的 XML。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-140">These can be extended to typed XML in a straightforward way.</span></span> <span data-ttu-id="cd6a4-141">為求簡單明瞭，我們針對 XML 資料執行個體來說明查詢，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cd6a4-141">For simplicity, queries are described for XML data instances as shown in the following:</span></span>  
  
```  
<book genre="security" publicationdate="2002" ISBN="0-7356-1588-2">  
   <title>Writing Secure Code</title>  
   <author>  
      <first-name>Michael</first-name>  
      <last-name>Howard</last-name>  
   </author>  
   <author>  
      <first-name>David</first-name>  
      <last-name>LeBlanc</last-name>  
   </author>  
   <price>39.99</price>  
</book>  
```  
  
 <span data-ttu-id="cd6a4-142">下列陳述式會在資料表 T 的 XML 資料行 xCol 上建立一個名為 idx_xCol 的 XML 索引：</span><span class="sxs-lookup"><span data-stu-id="cd6a4-142">The following statement creates an XML index, called idx_xCol, on the XML column xCol of table T:</span></span>  
  
```  
CREATE PRIMARY XML INDEX idx_xCol on T (xCol)  
```  
  
## <a name="creating-a-secondary-xml-index"></a><span data-ttu-id="cd6a4-143">建立次要 XML 索引</span><span class="sxs-lookup"><span data-stu-id="cd6a4-143">Creating a Secondary XML Index</span></span>  
 <span data-ttu-id="cd6a4-144">您可以使用 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL 陳述式來建立次要 XML 索引，並指定您所需的次要 XML 索引類型。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-144">Use the [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL statement to create secondary XML indexes and specify the type of the secondary XML index that you want.</span></span>  
  
 <span data-ttu-id="cd6a4-145">在建立次要 XML 索引時請注意下列項目：</span><span class="sxs-lookup"><span data-stu-id="cd6a4-145">Note the following when you are creating secondary XML indexes:</span></span>  
  
-   <span data-ttu-id="cd6a4-146">除了 IGNORE_DUP_KEY 與 ONLINE 之外，所有套用至非叢集索引的索引選項都可在次要 XML 索引上使用。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-146">All indexing options that apply to a nonclustered index, except IGNORE_DUP_KEY and ONLINE, are permitted on secondary XML indexes.</span></span> <span data-ttu-id="cd6a4-147">對於次要 XML 索引，有兩個選項必須永遠設定為 OFF。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-147">The two options must always be set to OFF for secondary XML indexes.</span></span>  
  
-   <span data-ttu-id="cd6a4-148">次要索引會像主要 XML 索引一樣進行分割。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-148">The secondary indexes are partitioned just like the primary XML index.</span></span>  
  
-   <span data-ttu-id="cd6a4-149">DROP_EXISTING 可以卸除使用者資料表上的次要索引，並在使用者資料表上建立其他次要索引。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-149">DROP_EXISTING can drop a secondary index on the user table and create another secondary index on the user table.</span></span>  
  
 <span data-ttu-id="cd6a4-150">您可以查詢 **sys.xml_indexes** 目錄檢視，以便擷取 XML 索引資訊。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-150">You can query the **sys.xml_indexes** catalog view to retrieve XML index information.</span></span> <span data-ttu-id="cd6a4-151">請注意，在 **sys.xml_indexes** 目錄檢視中的 **secondary_type_desc** 資料行會提供次要索引的類型：</span><span class="sxs-lookup"><span data-stu-id="cd6a4-151">Note that the **secondary_type_desc** column in the **sys.xml_indexes** catalog view provides the type of secondary index:</span></span>  
  
```  
SELECT  *   
FROM    sys.xml_indexes;  
```  
  
 <span data-ttu-id="cd6a4-152">在 **secondary_type_desc** 資料行中傳回的值可以是 NULL、PATH、VALUE 或 PROPERTY。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-152">The values returned in the **secondary_type_desc** column can be NULL, PATH, VALUE, or PROPERTY.</span></span> <span data-ttu-id="cd6a4-153">對於主要 XML 索引而言，傳回的值是 NULL。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-153">For the primary XML index, the value returned is NULL.</span></span>  
  
### <a name="example-creating-secondary-xml-indexes"></a><span data-ttu-id="cd6a4-154">範例：建立次要 XML 索引</span><span class="sxs-lookup"><span data-stu-id="cd6a4-154">Example: Creating Secondary XML Indexes</span></span>  
 <span data-ttu-id="cd6a4-155">下列範例說明如何建立次要 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-155">The following example illustrates how secondary XML indexes are created.</span></span> <span data-ttu-id="cd6a4-156">此範例也會顯示您已建立之 XML 索引的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-156">The example also shows information about the XML indexes that you created.</span></span>  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML);  
GO  
-- Create primary index.  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlCol);  
GO  
-- Create secondary indexes (PATH, VALUE, PROPERTY).  
CREATE XML INDEX PIdx_T_XmlCol_PATH ON T(XmlCol)  
USING XML INDEX PIdx_T_XmlCol  
FOR PATH;  
GO  
CREATE XML INDEX PIdx_T_XmlCol_VALUE ON T(XmlCol)  
USING XML INDEX PIdx_T_XmlCol  
FOR VALUE;  
GO  
CREATE XML INDEX PIdx_T_XmlCol_PROPERTY ON T(XmlCol)  
USING XML INDEX PIdx_T_XmlCol  
FOR PROPERTY;  
GO  
```  
  
 <span data-ttu-id="cd6a4-157">您可以查詢 `sys.xml_indexes` 來擷取 XML 索引資訊。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-157">You can query the `sys.xml_indexes` to retrieve XML indexes information.</span></span> <span data-ttu-id="cd6a4-158">`secondary_type_desc` 資料行會提供次要索引類型。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-158">The `secondary_type_desc` column provides the secondary index type.</span></span>  
  
```  
SELECT  *   
FROM    sys.xml_indexes;  
```  
  
 <span data-ttu-id="cd6a4-159">您也可以查詢目錄檢視以便取得索引資訊。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-159">You can also query the catalog view for index information.</span></span>  
  
```  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T');  
```  
  
 <span data-ttu-id="cd6a4-160">您可以加入範例資料，然後檢閱 XML 索引資訊。</span><span class="sxs-lookup"><span data-stu-id="cd6a4-160">You can add sample data and then review the XML index information.</span></span>  
  
```  
INSERT INTO T VALUES (1,  
'<doc id="123">  
<sections>  
<section num="2">  
<heading>Background</heading>  
</section>  
<section num="3">  
<heading>Sort</heading>  
</section>  
<section num="4">  
<heading>Search</heading>  
</section>  
</sections>  
</doc>');  
GO  
-- Check XML index information.  
SELECT *  
FROM   sys.dm_db_index_physical_stats (db_id(), object_id('T'), NULL, NULL, 'DETAILED');  
GO  
-- Space usage of primary XML index  
DECLARE @index_id int;  
SELECT  @index_id = i.index_id  
FROM    sys.xml_indexes i   
WHERE   i.name = 'PIdx_T_XmlCol' and object_name(i.object_id) = 'T';  
  
SELECT *  
FROM sys.dm_db_index_physical_stats (db_id(), object_id('T') , @index_id, DEFAULT, 'DETAILED');  
go  
--- Space usage of secondary XML index (for example PATH secondary index)  PIdx_T_XmlCol_PATH  
DECLARE @index_id int;  
SELECT  @index_id = i.index_id   
FROM    sys.xml_indexes i   
WHERE  i.name = 'PIdx_T_XmlCol_PATH' and object_name(i.object_id) = 'T';  
  
SELECT *  
FROM sys.dm_db_index_physical_stats (db_id(), object_id('T') , @index_id, DEFAULT, 'DETAILED');  
go  
  
-- Space usage of all secondary XML indexes for a particular table  
SELECT i.name, object_name(i.object_id), stats.*   
FROM   sys.dm_db_index_physical_stats (db_id(), object_id('T'), NULL, DEFAULT, 'DETAILED') stats  
JOIN sys.xml_indexes i ON (stats.object_id = i.object_id and stats.index_id = i.index_id)  
WHERE secondary_type is not null;  
-- Drop secondary indexes.  
DROP INDEX PIdx_T_XmlCol_PATH ON T;  
GO  
DROP INDEX PIdx_T_XmlCol_VALUE ON T;  
GO  
DROP INDEX PIdx_T_XmlCol_PROPERTY ON T;  
GO  
-- Drop primary index.  
DROP INDEX PIdx_T_XmlCol ON T;  
-- Drop table T.  
DROP TABLE T;  
Go  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd6a4-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd6a4-161">See Also</span></span>  
 <span data-ttu-id="cd6a4-162">[XML 索引 &#40;SQL Server&#41;](xml-indexes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cd6a4-162">[XML Indexes &#40;SQL Server&#41;](xml-indexes-sql-server.md) </span></span>  
 [<span data-ttu-id="cd6a4-163">XML 資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cd6a4-163">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
