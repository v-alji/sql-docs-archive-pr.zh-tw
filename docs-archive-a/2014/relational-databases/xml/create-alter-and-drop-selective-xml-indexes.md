---
title: 建立、修改和卸除選擇性 XML 索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: c398f396-f630-4a2d-a264-f243c5346de1
author: rothja
ms.author: jroth
ms.openlocfilehash: bf4123a46cc13359c936e6f9cfc0db3dcfdaa175
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688650"
---
# <a name="create-alter-and-drop-selective-xml-indexes"></a><span data-ttu-id="3cda0-102">建立、修改和卸除選擇性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="3cda0-102">Create, Alter, and Drop Selective XML Indexes</span></span>
  <span data-ttu-id="3cda0-103">描述如何建立新的選擇性 XML 索引，或是修改或卸除現有的選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="3cda0-103">Describes how to create a new selective XML index, or alter or drop an existing selective XML index.</span></span>  
  
 <span data-ttu-id="3cda0-104">如需選擇性 XML 索引的詳細資訊，請參閱 [選擇性 XML 索引 &#40;SXI&#41;](selective-xml-indexes-sxi.md)。</span><span class="sxs-lookup"><span data-stu-id="3cda0-104">For more information about selective XML indexes, see [Selective XML Indexes &#40;SXI&#41;](selective-xml-indexes-sxi.md).</span></span>  
  
##  <a name="creating-a-selective-xml-index"></a><a name="create"></a> <span data-ttu-id="3cda0-105">建立選擇性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="3cda0-105">Creating a Selective XML Index</span></span>  
  
### <a name="how-to-create-a-selective-xml-index"></a><span data-ttu-id="3cda0-106">如何：建立選擇性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="3cda0-106">How to: Create a Selective XML Index</span></span>  
 <span data-ttu-id="3cda0-107">**使用 Transact-SQL 建立選擇性 XML 索引**</span><span class="sxs-lookup"><span data-stu-id="3cda0-107">**Create a Selective XML Index by Using Transact-SQL**</span></span>  
 <span data-ttu-id="3cda0-108">透過呼叫 CREATE SELECTIVE XML INDEX 陳述式的方式建立選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="3cda0-108">Create a selective XML index by calling the CREATE SELECTIVE XML INDEX statement.</span></span> <span data-ttu-id="3cda0-109">如需詳細資訊，請參閱 [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3cda0-109">For more information, see [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).</span></span>  
  
 <span data-ttu-id="3cda0-110">**範例**</span><span class="sxs-lookup"><span data-stu-id="3cda0-110">**Example**</span></span>  
  
 <span data-ttu-id="3cda0-111">下列範例會顯示建立選擇性 XML 索引的語法。</span><span class="sxs-lookup"><span data-stu-id="3cda0-111">The following example shows the syntax for creating a selective XML index.</span></span> <span data-ttu-id="3cda0-112">另外還會顯示描述要索引之路徑的多種語法變化，包含選用的最佳化提示。</span><span class="sxs-lookup"><span data-stu-id="3cda0-112">It also shows several variations of the syntax for describing the paths to be indexed, with optional optimization hints.</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX sxi_index  
ON Tbl(xmlcol)  
  
FOR(  
    pathab   = '/a/b' as XQUERY 'node()'  
    pathabc  = '/a/b/c' as XQUERY 'xs:double',   
    pathdtext = '/a/b/d/text()' as XQUERY 'xs:string' MAXLENGTH(200) SINGLETON  
    pathabe = '/a/b/e' as SQL NVARCHAR(100)  
)  
```  
  
  
  
##  <a name="altering-a-selective-xml-index"></a><a name="alter"></a> <span data-ttu-id="3cda0-113">修改選擇性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="3cda0-113">Altering a Selective XML Index</span></span>  
  
### <a name="how-to-alter-a-selective-xml-index"></a><span data-ttu-id="3cda0-114">如何：修改選擇性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="3cda0-114">How to: Alter a Selective XML Index</span></span>  
 <span data-ttu-id="3cda0-115">**使用 Transact-SQL 修改選擇性 XML 索引**</span><span class="sxs-lookup"><span data-stu-id="3cda0-115">**Alter a Selective XML Index by Using Transact-SQL**</span></span>  
 <span data-ttu-id="3cda0-116">透過呼叫 ALTER INDEX 陳述式的方式修改現有的選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="3cda0-116">Alter an existing selective XML index by calling the ALTER INDEX statement.</span></span> <span data-ttu-id="3cda0-117">如需詳細資訊，請參閱 [ALTER INDEX &#40;選擇性 XML 索引&#41;](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="3cda0-117">For more information, see [ALTER INDEX &#40;Selective XML Indexes&#41;](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="3cda0-118">**範例**</span><span class="sxs-lookup"><span data-stu-id="3cda0-118">**Example**</span></span>  
  
 <span data-ttu-id="3cda0-119">下列範例顯示 ALTER INDEX 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3cda0-119">The following example shows an ALTER INDEX statement.</span></span> <span data-ttu-id="3cda0-120">此陳述式會將路徑 `'/a/b/m'` 加入索引的 XQuery 部分，並且從 [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql) 主題的範例中所建立索引的 SQL 部分刪除路徑 `'/a/b/e'`。</span><span class="sxs-lookup"><span data-stu-id="3cda0-120">This statement adds the path `'/a/b/m'` to the XQuery part of the index and deletes the path `'/a/b/e'` from the SQL part of the index created in the example in the topic [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).</span></span> <span data-ttu-id="3cda0-121">要刪除的路徑是以建立時提供的名稱識別。</span><span class="sxs-lookup"><span data-stu-id="3cda0-121">The path to delete is identified by the name that was given to it when it was created.</span></span>  
  
```sql  
ALTER INDEX sxi_index  
ON Tbl  
FOR   
(  
    ADD pathm = '/a/b/m' as XQUERY 'node()' ,  
    REMOVE pathabe  
)  
```  
  
  
  
##  <a name="dropping-a-selective-xml-index"></a><a name="drop"></a> <span data-ttu-id="3cda0-122">卸除選擇性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="3cda0-122">Dropping a Selective XML Index</span></span>  
  
### <a name="how-to-drop-a-selective-xml-index"></a><span data-ttu-id="3cda0-123">如何：卸除選擇性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="3cda0-123">How to: Drop a Selective XML Index</span></span>  
 <span data-ttu-id="3cda0-124">**使用 Transact-SQL 卸除選擇性 XML 索引**</span><span class="sxs-lookup"><span data-stu-id="3cda0-124">**Drop a Selective XML Index by Using Transact-SQL**</span></span>  
 <span data-ttu-id="3cda0-125">透過呼叫 DROP INDEX 陳述式的方式卸除選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="3cda0-125">Drop a selective XML index by calling the DROP INDEX statement.</span></span> <span data-ttu-id="3cda0-126">如需詳細資訊，請參閱 [DROP INDEX &#40;選擇性 XML 索引&#41;](/sql/t-sql/statements/drop-index-selective-xml-indexes)。</span><span class="sxs-lookup"><span data-stu-id="3cda0-126">For more information, see [DROP INDEX &#40;Selective XML Indexes&#41;](/sql/t-sql/statements/drop-index-selective-xml-indexes).</span></span>  
  
 <span data-ttu-id="3cda0-127">**範例**</span><span class="sxs-lookup"><span data-stu-id="3cda0-127">**Example**</span></span>  
  
 <span data-ttu-id="3cda0-128">下列範例顯示 DROP INDEX 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3cda0-128">The following example shows a DROP INDEX statement.</span></span>  
  
```sql  
DROP INDEX sxi_index ON tbl  
```  
  
 
  
  
