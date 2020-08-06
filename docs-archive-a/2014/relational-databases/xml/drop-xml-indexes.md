---
title: 卸除 XML 索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- removing indexes
- dropping indexes
- XML indexes [SQL Server], dropping
ms.assetid: 7591ebea-34af-4925-8553-b2adb5b487c2
author: rothja
ms.author: jroth
ms.openlocfilehash: b7d4621cf2182b4587b12665a1cfe10ddbe0db3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585178"
---
# <a name="drop-xml-indexes"></a><span data-ttu-id="6022e-102">卸除 XML 索引</span><span class="sxs-lookup"><span data-stu-id="6022e-102">Drop XML Indexes</span></span>
  <span data-ttu-id="6022e-103">[DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式可用以卸除現有的主要或次要 XML 及非 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="6022e-103">The [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] statement can be used to drop existing primary or secondary XML and non-XML indexes.</span></span> <span data-ttu-id="6022e-104">不過，DROP INDEX 沒有任何選項會套用至 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="6022e-104">However, no options of DROP INDEX apply to XML indexes.</span></span> <span data-ttu-id="6022e-105">如果您卸除主要 XML 索引，也會刪除任何存在的次要索引。</span><span class="sxs-lookup"><span data-stu-id="6022e-105">If you drop the primary XML index, any secondary indexes that are present are also deleted.</span></span>  
  
 <span data-ttu-id="6022e-106">具有 *TableName.IndexName* 的 DROP 語法已捨棄不用，XML 索引也不支援它。</span><span class="sxs-lookup"><span data-stu-id="6022e-106">The DROP syntax with *TableName.IndexName* is being phased out and is not supported for XML indexes.</span></span>  
  
## <a name="example-creating-and-dropping-a-primary-xml-index"></a><span data-ttu-id="6022e-107">範例：建立和卸除主要 XML 索引</span><span class="sxs-lookup"><span data-stu-id="6022e-107">Example: Creating and Dropping a Primary XML Index</span></span>  
 <span data-ttu-id="6022e-108">在下列範例中，會在 `xml` 類型資料行上建立 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="6022e-108">In the following example, an XML index is created on an `xml` type column.</span></span>  
  
```  
DROP TABLE T  
GO  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
-- Create Primary XML index   
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlCol)  
GO  
-- Verify the index creation.   
-- Note index type is 3 for xml indexes.  
-- Note the type 3 is index on XML type.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'   
-- Drop the index.  
DROP INDEX PIdx_T_XmlCol ON T  
```  
  
 <span data-ttu-id="6022e-109">當卸除資料表時，也會自動卸除在該資料表上的所有 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="6022e-109">When a table is dropped, all the XML indexes on it are also automatically dropped.</span></span> <span data-ttu-id="6022e-110">不過，如果在資料行上有 XML 索引，將無法從資料表卸除 XML 資料行。</span><span class="sxs-lookup"><span data-stu-id="6022e-110">However, an XML column cannot be dropped from a table if an XML index exists on the column.</span></span>  
  
 <span data-ttu-id="6022e-111">在下列範例中，會在 `xml` 類型資料行上建立 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="6022e-111">In the following example, an XML index is created on an `xml` type column.</span></span> <span data-ttu-id="6022e-112">如需詳細資訊，請參閱 [比較具類型的 XML 與不具類型的 XML](../xml/compare-typed-xml-to-untyped-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="6022e-112">For more information, see [Compare Typed XML to Untyped XML](../xml/compare-typed-xml-to-untyped-xml.md).</span></span>  
  
```  
CREATE TABLE TestTable(  
 Col1 int primary key,   
 Col2 xml (Production.ProductDescriptionSchemaCollection))   
GO  
```  
  
 <span data-ttu-id="6022e-113">現在，您可以在 `Co12`上建立主要 XML索引。</span><span class="sxs-lookup"><span data-stu-id="6022e-113">Now, you can create a primary XML index on `Co12`.</span></span>  
  
```  
CREATE PRIMARY XML INDEX PIdx_TestTable_Col2   
ON TestTable(Col2)  
GO  
```  
  
## <a name="example-creating-an-xml-index-by-using-the-drop_existing-index-option"></a><span data-ttu-id="6022e-114">範例：使用 DROP_EXISTING 索引選項建立 XML 索引</span><span class="sxs-lookup"><span data-stu-id="6022e-114">Example: Creating an XML Index by Using the DROP_EXISTING Index Option</span></span>  
 <span data-ttu-id="6022e-115">在下列範例中，會在資料行 (`XmlColx`) 上建立 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="6022e-115">In the following example, an XML index is created on a column (`XmlColx`).</span></span> <span data-ttu-id="6022e-116">接著，會在不同資料行 (`XmlColy`) 上建立另一個具有相同名稱的 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="6022e-116">Then, another XML index with the same name is created on a different column, (`XmlColy`).</span></span> <span data-ttu-id="6022e-117">因為指定了 `DROP_EXISTING` 選項，所以會卸除 (`XmlColx)` 上的現有 XML 索引，並在 (`XmlColy`) 上建立新 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="6022e-117">Because the `DROP_EXISTING` option is specified, the existing XML index on (`XmlColx)` is dropped and a new XML index on (`XmlColy`) is created.</span></span>  
  
```  
DROP TABLE T  
GO  
CREATE TABLE T(Col1 int primary key, XmlColx xml, XmlColy xml)  
GO  
-- Create XML index on XmlColx.  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlColx)  
GO  
-- Create same name XML index on XmlColy.  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlColy)   
WITH (DROP_EXISTING = ON)  
-- Verify the index is created on XmlColy.d.  
SELECT sc.name   
FROM   sys.xml_indexes si inner join sys.index_columns sic   
ON     sic.object_id=si.object_id and sic.index_id=si.index_id  
INNER  join sys.columns sc on sc.object_id=sic.object_id   
AND    sc.column_id=sic.column_id  
WHERE  si.name='PIdx_T_XmlCol'   
AND    si.object_id=object_id('T')  
```  
  
 <span data-ttu-id="6022e-118">此查詢會傳回已建立的指定 XML 索引的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="6022e-118">This query returns the column name on which the specified XML index is created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6022e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6022e-119">See Also</span></span>  
 [<span data-ttu-id="6022e-120">XML 索引 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6022e-120">XML Indexes &#40;SQL Server&#41;</span></span>](xml-indexes-sql-server.md)  
  
  
