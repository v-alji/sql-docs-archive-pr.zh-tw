---
title: 修改 XML 索引 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XML indexes [SQL Server], modifying
- modifying indexes
ms.assetid: 24d50fe1-c6ec-49e6-91a3-9791851ba53d
author: rothja
ms.author: jroth
ms.openlocfilehash: c5c67470fc9aaaeefe49e5ccb1a8602e082c4054
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687557"
---
# <a name="modify-xml-indexes"></a><span data-ttu-id="a21a2-102">修改 XML 索引</span><span class="sxs-lookup"><span data-stu-id="a21a2-102">Modify XML Indexes</span></span>
  <span data-ttu-id="a21a2-103">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL 陳述式可用來修改現有的 XML 和非 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="a21a2-103">The [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL statement can be used to modify existing XML and non-XML indexes.</span></span> <span data-ttu-id="a21a2-104">然而，並非所有的 ALTER INDEX 選項都可供 XML 索引使用。</span><span class="sxs-lookup"><span data-stu-id="a21a2-104">However, not all the ALTER INDEX options are available to XML indexes.</span></span> <span data-ttu-id="a21a2-105">在修改 XML 索引時，下列選項是無效的：</span><span class="sxs-lookup"><span data-stu-id="a21a2-105">The following options are not valid when modifying XML indexes:</span></span>  
  
-   <span data-ttu-id="a21a2-106">重建和設定選項 IGNORE_DUP_KEY 對於 XML 索引是無效的。</span><span class="sxs-lookup"><span data-stu-id="a21a2-106">The rebuild and set option IGNORE_DUP_KEY is not valid for XML indexes.</span></span> <span data-ttu-id="a21a2-107">對於次要 XML 索引，重建選項 ONLINE 必須設定為 OFF。</span><span class="sxs-lookup"><span data-stu-id="a21a2-107">The rebuild option ONLINE must be set to OFF for secondary XML indexes.</span></span> <span data-ttu-id="a21a2-108">在 ALTER INDEX 陳述式中不允許使用 DROP_EXISTING 選項。</span><span class="sxs-lookup"><span data-stu-id="a21a2-108">The option DROP_EXISTING is not permitted in the ALTER INDEX statement.</span></span>  
  
-   <span data-ttu-id="a21a2-109">在使用者資料表中對於主索引鍵條件約束的修改，並不會自動傳播至 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="a21a2-109">The modifications of the primary key constraint in the user table are not automatically propagated to XML indexes.</span></span> <span data-ttu-id="a21a2-110">使用者必須先卸除 XML 索引，再重新建立它們。</span><span class="sxs-lookup"><span data-stu-id="a21a2-110">The user must drop the XML indexes first and then re-create them.</span></span>  
  
-   <span data-ttu-id="a21a2-111">如果指定了 ALTER INDEX ALL，它會同時套用至非 XML 與 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="a21a2-111">If ALTER INDEX ALL is specified, it applies to both non-XML and XML indexes.</span></span> <span data-ttu-id="a21a2-112">索引選項可以指定為對於兩種索引類型都無效。</span><span class="sxs-lookup"><span data-stu-id="a21a2-112">Indexing options may be specified that are not valid for both types of indexes.</span></span> <span data-ttu-id="a21a2-113">在此情況下，整個陳述式都會失敗。</span><span class="sxs-lookup"><span data-stu-id="a21a2-113">In this case, the whole statement fails.</span></span>  
  
## <a name="example-modifying-an-xml-index"></a><span data-ttu-id="a21a2-114">範例：修改 XML 索引</span><span class="sxs-lookup"><span data-stu-id="a21a2-114">Example: Modifying an XML Index</span></span>  
 <span data-ttu-id="a21a2-115">下列範例會建立 XML 索引，然後將 `ALLOW_ROW_LOCKS` 選項設定為 `OFF`來加以修改。</span><span class="sxs-lookup"><span data-stu-id="a21a2-115">In the following example, an XML index is created and then modified by setting the option `ALLOW_ROW_LOCKS` to `OFF`.</span></span> <span data-ttu-id="a21a2-116">當 `ALLOW_ROW_LOCKS` 為 `OFF`時，將不會鎖定資料列，並可使用頁面與資料表層級鎖定來取得指定索引的存取權。</span><span class="sxs-lookup"><span data-stu-id="a21a2-116">When `ALLOW_ROW_LOCKS` is `OFF`, rows are not locked and access to the specified indexes is obtained by using page-and table-level locks.</span></span>  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
-- Create primary XML index.   
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlCol)  
GO  
-- Note the type 3 is index on XML type.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'  
  
-- Modify and set an index option.  
ALTER INDEX PIdx_T_XmlCol on T   
SET (ALLOW_ROW_LOCKS = OFF)  
```  
  
## <a name="example-disabling-and-enabling-an-xml-index"></a><span data-ttu-id="a21a2-117">範例：停用和啟用 XML 索引</span><span class="sxs-lookup"><span data-stu-id="a21a2-117">Example: Disabling and Enabling an XML Index</span></span>  
 <span data-ttu-id="a21a2-118">依預設，XML 索引為已啟用。</span><span class="sxs-lookup"><span data-stu-id="a21a2-118">By default, an XML index is enabled.</span></span> <span data-ttu-id="a21a2-119">如果停用了 XML 索引，針對 XML 資料行執行的查詢將不會使用 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="a21a2-119">If an XML index is disabled, the queries running against the XML column do not use the XML index.</span></span> <span data-ttu-id="a21a2-120">若要啟用 XML 索引，請使用 `ALTER INDEX` 搭配 `REBUILD` 選項。</span><span class="sxs-lookup"><span data-stu-id="a21a2-120">To enable an XML index, use `ALTER INDEX` with the `REBUILD` option.</span></span>  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol ON T(XmlCol)  
GO  
ALTER INDEX PIdx_T_XmlCol on T DISABLE  
Go  
-- Verify index is disabled.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'  
-- Rebuild the index.  
ALTER INDEX PIdx_T_XmlCol on T REBUILD  
Go  
```  
  
## <a name="see-also"></a><span data-ttu-id="a21a2-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a21a2-121">See Also</span></span>  
 [<span data-ttu-id="a21a2-122">XML 索引 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a21a2-122">XML Indexes &#40;SQL Server&#41;</span></span>](xml-indexes-sql-server.md)  
  
  
