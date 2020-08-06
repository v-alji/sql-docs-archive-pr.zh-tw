---
title: 建立全文檢索搜尋查詢 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CONTAINS predicate (Transact-SQL)
- queries [full-text search], creating
- full-text queries [SQL Server], creating
ms.assetid: 537fa556-390e-4c88-9b8e-679848d94abc
author: stevestein
ms.author: sstein
ms.openlocfilehash: f84ab465da0a1b7ac1da1211de1d5199fd28ee95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699121"
---
# <a name="create-full-text-search-queries-visual-database-tools"></a><span data-ttu-id="f0da4-102">建立全文檢索搜尋查詢 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f0da4-102">Create Full-Text Search Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="f0da4-103">全文檢索搜尋會使用 CONTAINS 述詞 (Predicate)，找出在指定資料行中具有指定文字的資料列。</span><span class="sxs-lookup"><span data-stu-id="f0da4-103">Full-text searches use the CONTAINS predicate to locate rows that have specified text in a given column.</span></span> <span data-ttu-id="f0da4-104">全文檢索搜尋只適用於具有現用全文檢索索引的資料行。</span><span class="sxs-lookup"><span data-stu-id="f0da4-104">Full-Text searches are only possible on columns that have active full-text indexes.</span></span> <span data-ttu-id="f0da4-105">如果您嘗試在未具有目前現用全文檢索索引的資料行上使用 CONTAINS 子句，您會收到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f0da4-105">If you attempt to use the CONTAINS clause on a column that does not have a currently active full-text index, you will receive an error.</span></span> <span data-ttu-id="f0da4-106">如需全文檢索索引和 CONTAINS 子句的詳細資訊，請參閱[全文檢索搜尋](../../relational-databases/search/full-text-search.md)和[包含 &#40;transact-sql&#41;](/sql/t-sql/queries/contains-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f0da4-106">For more information on full-text indexes and the CONTAINS clause, see [Full-Text Search](../../relational-databases/search/full-text-search.md) and [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql).</span></span>  
  
### <a name="to-create-a-full-text-search-query"></a><span data-ttu-id="f0da4-107">建立全文檢索搜尋查詢</span><span class="sxs-lookup"><span data-stu-id="f0da4-107">To create a full-text search query</span></span>  
  
1.  <span data-ttu-id="f0da4-108">在 [方案總管] 中開啟查詢或建立新查詢。</span><span class="sxs-lookup"><span data-stu-id="f0da4-108">Open a query from Solution Explorer or create a new one.</span></span>  
  
2.  <span data-ttu-id="f0da4-109">在查詢的 WHERE 子句中，使用 CONTAINS 函數來搜尋全文檢索資料行。</span><span class="sxs-lookup"><span data-stu-id="f0da4-109">In the WHERE clause of your query, use the CONTAINS function to search a full-text column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0da4-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0da4-110">See Also</span></span>  
 <span data-ttu-id="f0da4-111">[支援的查詢類型 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="f0da4-111">[Supported Query Types &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="f0da4-112">[設計查詢和觀看 how to 主題 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="f0da4-112">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="f0da4-113">使用查詢執行基本作業 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="f0da4-113">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
