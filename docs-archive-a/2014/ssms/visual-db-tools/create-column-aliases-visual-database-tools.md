---
title: 建立資料行別名 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], aliases
- aliases [SQL Server], columns
ms.assetid: e2e1c166-8ea7-47a2-b6a7-e419bf0fa3bb
author: stevestein
ms.author: sstein
ms.openlocfilehash: febe7ed27ed10a283cab549bc65299577d69761c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593752"
---
# <a name="create-column-aliases-visual-database-tools"></a><span data-ttu-id="e8ae7-102">建立資料行別名 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e8ae7-102">Create Column Aliases (Visual Database Tools)</span></span>
  <span data-ttu-id="e8ae7-103">您可以建立資料行名稱的別名，來更輕鬆地使用資料行名稱、計算和彙總值。</span><span class="sxs-lookup"><span data-stu-id="e8ae7-103">You can create aliases for column names to make it easier to work with column names, calculations, and summary values.</span></span> <span data-ttu-id="e8ae7-104">例如，您可以建立資料行別名來：</span><span class="sxs-lookup"><span data-stu-id="e8ae7-104">For example, you can create a column alias to:</span></span>  
  
-   <span data-ttu-id="e8ae7-105">針對諸如 `(quantity * unit_price)` 的運算式或彙總函式，建立一個如 Total Amount (總數量) 的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="e8ae7-105">Create a column name, such as "Total Amount," for an expression such as `(quantity * unit_price)` or for an aggregate function.</span></span>  
  
-   <span data-ttu-id="e8ae7-106">建立資料行名稱的縮短形式，例如， `"d_id"` 代表 `"discounts.stor_id."`</span><span class="sxs-lookup"><span data-stu-id="e8ae7-106">Create a shortened form of a column name, such as `"d_id"` for `"discounts.stor_id."`</span></span>  
  
 <span data-ttu-id="e8ae7-107">在定義資料行別名後，您可以在選取查詢中使用別名，來指定查詢的輸出項目。</span><span class="sxs-lookup"><span data-stu-id="e8ae7-107">After you have defined a column alias, you can use the alias in a Select query to specify query output.</span></span>  
  
### <a name="to-create-a-column-alias"></a><span data-ttu-id="e8ae7-108">若要建立資料行別名</span><span class="sxs-lookup"><span data-stu-id="e8ae7-108">To create a column alias</span></span>  
  
1.  <span data-ttu-id="e8ae7-109">在 [準則窗格]  中，找出包含您想要建立別名之資料行的資料列，並且視輸出需要標示該資料列。</span><span class="sxs-lookup"><span data-stu-id="e8ae7-109">In the **Criteria Pane**, locate the row containing the data column for which you want to create an alias, and if necessary, mark it for output.</span></span> <span data-ttu-id="e8ae7-110">如果資料行不在方格中，將其加入。</span><span class="sxs-lookup"><span data-stu-id="e8ae7-110">If the data column is not already in the grid, add it.</span></span>  
  
2.  <span data-ttu-id="e8ae7-111">在該資料列的 [別名]  資料行中，輸入別名。</span><span class="sxs-lookup"><span data-stu-id="e8ae7-111">In the **Alias** column for that row, enter the alias.</span></span> <span data-ttu-id="e8ae7-112">別名必須遵循所有 SQL 的命名慣例。</span><span class="sxs-lookup"><span data-stu-id="e8ae7-112">The alias must follow all naming conventions for SQL.</span></span> <span data-ttu-id="e8ae7-113">如果所輸入的別名包含空白字元，[查詢和檢視設計師] 會自動在別名前後加入分隔符號。</span><span class="sxs-lookup"><span data-stu-id="e8ae7-113">If the alias name you enter contains spaces, the Query and View Designer automatically puts delimiters around it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ae7-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8ae7-114">See Also</span></span>  
 <span data-ttu-id="e8ae7-115">[將資料行加入至查詢 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="e8ae7-115">[Add Columns to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="e8ae7-116">[排序和分組查詢結果 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="e8ae7-116">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="e8ae7-117">[&#40;Visual Database Tools&#41;匯總查詢結果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="e8ae7-117">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="e8ae7-118">使用查詢執行基本作業 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="e8ae7-118">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
