---
title: 建立 UNION 查詢 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], types
- UNION queries
- Select query
- combining query results
- merged SELECT query [SQL Server]
ms.assetid: b5aafb1d-e4ed-4922-b790-56abc5ec551a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3c10f39c3e44844c4ec8a6a2328c41ea2de350d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596992"
---
# <a name="create-union-queries-visual-database-tools"></a><span data-ttu-id="95a2a-102">建立 UNION 查詢 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="95a2a-102">Create UNION Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="95a2a-103">UNION 關鍵字讓您可以在所產生的單一資料表中，包含 2 個 SELECT 陳述式的結果。</span><span class="sxs-lookup"><span data-stu-id="95a2a-103">The UNION keyword enables you to include the results of two SELECT statements in one resulting table.</span></span> <span data-ttu-id="95a2a-104">由任一 SELECT 陳述式所傳回的所有資料列，會被結合為 UNION 運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="95a2a-104">All rows returned from either SELECT statement are combined into the result of the UNION expression.</span></span> <span data-ttu-id="95a2a-105">如需範例，請參閱[&#40;transact-sql&#41;的 [選取範例](/sql/t-sql/queries/select-examples-transact-sql)]。</span><span class="sxs-lookup"><span data-stu-id="95a2a-105">For examples, see [SELECT Examples &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-examples-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95a2a-106">圖表窗格只能顯示單一 SELECT 子句。</span><span class="sxs-lookup"><span data-stu-id="95a2a-106">The Diagram pane can only display one SELECT clause.</span></span> <span data-ttu-id="95a2a-107">因此，當您使用 UNION 查詢時，查詢設計工具會隱藏資料表運算窗格。</span><span class="sxs-lookup"><span data-stu-id="95a2a-107">Therefore, when you are working with a UNION query, Query Designer hides the Table Operations pane.</span></span>  
  
### <a name="to-create-a-merged-select-query"></a><span data-ttu-id="95a2a-108">建立合併的 SELECT 查詢</span><span class="sxs-lookup"><span data-stu-id="95a2a-108">To create a Merged SELECT query</span></span>  
  
1.  <span data-ttu-id="95a2a-109">開啟查詢或建立新查詢。</span><span class="sxs-lookup"><span data-stu-id="95a2a-109">Open a query or create a new one.</span></span>  
  
2.  <span data-ttu-id="95a2a-110">在 SQL 窗格中，輸入有效的 UNION 運算式。</span><span class="sxs-lookup"><span data-stu-id="95a2a-110">In the SQL pane, type a valid UNION expression.</span></span>  
  
     <span data-ttu-id="95a2a-111">下列範例是有效的 UNION 運算式。</span><span class="sxs-lookup"><span data-stu-id="95a2a-111">The following example is a valid UNION expression.</span></span>  
  
    ```  
    SELECT ProductModelID, Name  
    FROM Production.ProductModel  
    UNION  
    SELECT ProductModelID, Name   
    FROM dbo.Gloves;  
    ```  
  
3.  <span data-ttu-id="95a2a-112">在 [查詢設計工具]  功能表中，按一下 [執行 SQL]  來執行查詢。</span><span class="sxs-lookup"><span data-stu-id="95a2a-112">On the **Query Designer** menu, click **Execute SQL** to run the query.</span></span>  
  
     <span data-ttu-id="95a2a-113">查詢設計工具目前已格式化您的 UNION 查詢。</span><span class="sxs-lookup"><span data-stu-id="95a2a-113">Your UNION query is now formatted by Query Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a2a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95a2a-114">See Also</span></span>  
 <span data-ttu-id="95a2a-115">[支援的查詢類型 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="95a2a-115">[Supported Query Types &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="95a2a-116">[設計查詢和觀看 how to 主題 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="95a2a-116">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="95a2a-117">[使用 &#40;Visual Database Tools 的查詢來執行基本作業&#41;](perform-basic-operations-with-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="95a2a-117">[Perform Basic Operations with Queries &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="95a2a-118">UNION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="95a2a-118">UNION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/set-operators-union-transact-sql)  
  
  
