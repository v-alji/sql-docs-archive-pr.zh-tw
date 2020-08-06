---
title: 建立、修改和卸除次要選擇性 XML 索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: 45128105-833b-40a9-9cc9-1ae03ac0b52b
author: rothja
ms.author: jroth
ms.openlocfilehash: e6f7296896b6421db5329565403cdcbaf10b26a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688653"
---
# <a name="create-alter-and-drop-secondary-selective-xml-indexes"></a><span data-ttu-id="7bad4-102">建立、修改和卸除次要選擇性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="7bad4-102">Create, Alter, and Drop Secondary Selective XML Indexes</span></span>
  <span data-ttu-id="7bad4-103">描述如何建立新的次要選擇性 XML 索引，或是修改或卸除現有的次要選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="7bad4-103">Describes how to create a new secondary selective XML index, or alter or drop an existing secondary selective XML index.</span></span>  
  
##  <a name="creating-a-secondary-selective-xml-index"></a><a name="create"></a> <span data-ttu-id="7bad4-104">建立次要選擇性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="7bad4-104">Creating a Secondary Selective XML Index</span></span>  
  
### <a name="how-to-create-a-secondary-selective-xml-index"></a><span data-ttu-id="7bad4-105">如何：建立次要選擇性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="7bad4-105">How to: Create a Secondary Selective XML Index</span></span>  
 <span data-ttu-id="7bad4-106">**使用 Transact-SQL 建立次要選擇性 XML 索引**</span><span class="sxs-lookup"><span data-stu-id="7bad4-106">**Create a Secondary Selective XML Index by Using Transact-SQL**</span></span>  
 <span data-ttu-id="7bad4-107">透過呼叫 CREATE XML INDEX 陳述式的方式建立次要選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="7bad4-107">Create a secondary selective XML index by calling the CREATE XML INDEX statement.</span></span> <span data-ttu-id="7bad4-108">如需詳細資訊，請參閱 [建立 XML 索引 &#40;選擇性 XML 索引&#41;] (~/t-sql/statements/create-xml-index-selective-xml-indexes。</span><span class="sxs-lookup"><span data-stu-id="7bad4-108">For more information, see [CREATE XML INDEX &#40;Selective XML Indexes&#41;](~/t-sql/statements/create-xml-index-selective-xml-indexes.</span></span>  
  
 <span data-ttu-id="7bad4-109">**範例**</span><span class="sxs-lookup"><span data-stu-id="7bad4-109">**Example**</span></span>  
  
 <span data-ttu-id="7bad4-110">下列範例會在 `'pathabc'`路徑上建立次要選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="7bad4-110">The following example creates a secondary selective XML index on the path `'pathabc'`.</span></span> <span data-ttu-id="7bad4-111">要索引的路徑是以使用 CREATE SELECTIVE XML INDEX 陳述式建立時提供的名稱識別。</span><span class="sxs-lookup"><span data-stu-id="7bad4-111">The path to index is identified by the name that was given to it when it was created with the CREATE SELECTIVE XML INDEX statement.</span></span> <span data-ttu-id="7bad4-112">如需詳細資訊，請參閱 [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7bad4-112">For more information, see [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).</span></span>  
  
```sql  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
  
##  <a name="altering-a-secondary-selective-xml-index"></a><a name="alter"></a> <span data-ttu-id="7bad4-113">修改次要選擇性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="7bad4-113">Altering a Secondary Selective XML Index</span></span>  
 <span data-ttu-id="7bad4-114">次要選擇性 XML 索引不支援 ALTER 陳述式。</span><span class="sxs-lookup"><span data-stu-id="7bad4-114">The ALTER statement is not supported for secondary selective XML indexes.</span></span> <span data-ttu-id="7bad4-115">若要變更次要選擇性 XML 索引，請卸除現有的索引並重新建立。</span><span class="sxs-lookup"><span data-stu-id="7bad4-115">To change a secondary selective XML index, drop the existing index and recreate it.</span></span>  
  
### <a name="how-to-alter-a-secondary-selective-xml-index"></a><span data-ttu-id="7bad4-116">如何：修改次要選擇性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="7bad4-116">How to: Alter a Secondary Selective XML Index</span></span>  
 <span data-ttu-id="7bad4-117">**使用 Transact-SQL 修改次要選擇性 XML 索引**</span><span class="sxs-lookup"><span data-stu-id="7bad4-117">**Alter a Secondary Selective XML Index by Using Transact-SQL**</span></span>  
 1.  <span data-ttu-id="7bad4-118">透過呼叫 DROP INDEX 陳述式的方式卸除現有的次要選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="7bad4-118">Drop the existing secondary selective XML index by calling the DROP INDEX statement.</span></span> <span data-ttu-id="7bad4-119">如需詳細資訊，請參閱 [DROP INDEX &#40;選擇性 XML 索引&#41;](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="7bad4-119">For more information, see [DROP INDEX &#40;Selective XML Indexes&#41;](../indexes/indexes.md).</span></span>  
  
2.  <span data-ttu-id="7bad4-120">透過呼叫 CREATE XML INDEX 陳述式的方式重新建立具有所需選項的索引。</span><span class="sxs-lookup"><span data-stu-id="7bad4-120">Recreate the index with the desired options by calling the CREATE XML INDEX statement.</span></span> <span data-ttu-id="7bad4-121">如需詳細資訊，請參閱 [建立 XML 索引 &#40;選擇性 XML 索引&#41;] (~/t-sql/statements/create-xml-index-selective-xml-indexes。</span><span class="sxs-lookup"><span data-stu-id="7bad4-121">For more information, see [CREATE XML INDEX &#40;Selective XML Indexes&#41;](~/t-sql/statements/create-xml-index-selective-xml-indexes.</span></span>  
  
 <span data-ttu-id="7bad4-122">**範例**</span><span class="sxs-lookup"><span data-stu-id="7bad4-122">**Example**</span></span>  
  
 <span data-ttu-id="7bad4-123">下列範例會藉由卸除次要選擇性 XML 索引並重新建立的方式進行變更。</span><span class="sxs-lookup"><span data-stu-id="7bad4-123">The following example changes a secondary selective XML index by dropping it and recreating it.</span></span>  
  
```sql  
DROP INDEX filt_sxi_index_c  
  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
  
##  <a name="dropping-a-secondary-selective-xml-index"></a><a name="drop"></a> <span data-ttu-id="7bad4-124">卸除次要選擇性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="7bad4-124">Dropping a Secondary Selective XML Index</span></span>  
  
### <a name="how-to-drop-a-secondary-selective-xml-index"></a><span data-ttu-id="7bad4-125">如何：卸除次要選擇性 XML 索引</span><span class="sxs-lookup"><span data-stu-id="7bad4-125">How to: Drop a Secondary Selective XML Index</span></span>  
 <span data-ttu-id="7bad4-126">**使用 Transact-SQL 卸除次要選擇性 XML 索引**</span><span class="sxs-lookup"><span data-stu-id="7bad4-126">**Drop a Secondary Selective XML Index by Using Transact-SQL**</span></span>  
 <span data-ttu-id="7bad4-127">透過呼叫 DROP INDEX 陳述式的方式卸除次要選擇性 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="7bad4-127">Drop a secondary selective XML index by calling the DROP INDEX statement.</span></span> <span data-ttu-id="7bad4-128">如需詳細資訊，請參閱 [DROP INDEX &#40;選擇性 XML 索引&#41;](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="7bad4-128">For more information, see [DROP INDEX &#40;Selective XML Indexes&#41;](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="7bad4-129">**範例**</span><span class="sxs-lookup"><span data-stu-id="7bad4-129">**Example**</span></span>  
  
 <span data-ttu-id="7bad4-130">下列範例顯示 DROP INDEX 陳述式。</span><span class="sxs-lookup"><span data-stu-id="7bad4-130">The following example shows a DROP INDEX statement.</span></span>  
  
```sql  
DROP INDEX ssxi_index  
ON tbl  
```  
  
  
## <a name="see-also"></a><span data-ttu-id="7bad4-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bad4-131">See Also</span></span>  
 [<span data-ttu-id="7bad4-132">選擇性 XML 索引 &#40;SXI&#41;</span><span class="sxs-lookup"><span data-stu-id="7bad4-132">Selective XML Indexes &#40;SXI&#41;</span></span>](selective-xml-indexes-sxi.md)  
  
  
