---
title: 將衍生資料表加入查詢 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [Visual Database Tools]
- joins [SQL Server], derived tables
- table joins [SQL Server]
- derived tables
ms.assetid: 05f1ba1d-465f-4e36-84bb-21b963c9b8f9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 72169654b878f404950788b468bb6603035fd540
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593766"
---
# <a name="add-derived-tables-to-queries-visual-database-tools"></a><span data-ttu-id="6cbbe-102">將衍生資料表加入查詢 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6cbbe-102">Add Derived Tables to Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="6cbbe-103">衍生資料表是用作查詢中資料表來源的結果集。</span><span class="sxs-lookup"><span data-stu-id="6cbbe-103">Derived tables are result sets used as table sources in a query.</span></span> <span data-ttu-id="6cbbe-104">您可以加入衍生資料表至 [圖表窗格]  中的查詢。</span><span class="sxs-lookup"><span data-stu-id="6cbbe-104">You can add a derived table to a query in the **Diagram Pane**.</span></span>  
  
### <a name="to-add-a-derived-table-to-a-query"></a><span data-ttu-id="6cbbe-105">將衍生資料表加入查詢</span><span class="sxs-lookup"><span data-stu-id="6cbbe-105">To add a derived table to a query</span></span>  
  
1.  <span data-ttu-id="6cbbe-106">開啟現有查詢或建立新查詢。</span><span class="sxs-lookup"><span data-stu-id="6cbbe-106">Open an existing query or create a new query.</span></span>  
  
2.  <span data-ttu-id="6cbbe-107">以滑鼠右鍵按一下 [圖表窗格]  ，然後選擇 [新增衍生資料表]  。</span><span class="sxs-lookup"><span data-stu-id="6cbbe-107">Right-click the **Diagram Pane** and choose **Add New Derived Table**.</span></span>  
  
     <span data-ttu-id="6cbbe-108">隨即加入名稱為 derivedtbl_*N* 的新資料表，衍生資料表的 SELECT 陳述式也加入查詢的 FROM 子句中。</span><span class="sxs-lookup"><span data-stu-id="6cbbe-108">A new table with the name derivedtbl_*N* is added, and the derived table's SELECT statement is added to the query's FROM clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cbbe-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cbbe-109">See Also</span></span>  
 <span data-ttu-id="6cbbe-110">[使用 &#40;Visual Database Tools 的查詢來執行基本作業&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6cbbe-110">[Perform Basic Operations with Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="6cbbe-111">[&#40;Visual Database Tools 建立查詢&#41;](create-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6cbbe-111">[Create Queries &#40;Visual Database Tools&#41;](create-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="6cbbe-112">[&#40;Visual Database Tools 開啟查詢&#41;](open-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6cbbe-112">[Open Queries &#40;Visual Database Tools&#41;](open-queries-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="6cbbe-113">SELECT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6cbbe-113">SELECT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/select-transact-sql)  
  
  
