---
title: 查詢和檢視表設計工具 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.querydesigner
- vdt.pane.diagram
- vdt.pane.grid
- vdt.dlgbox.querybuilder
- vdt.pane.sql
- vdt.pane.results
helpviewer_keywords:
- Query Designer [SQL Server], panes
- View Designer, panes
- Query Designer [SQL Server], components
- View Designer, components
ms.assetid: 12e4b5a5-b793-4b6c-a0e5-c450c49bf26f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 29bd3fa9e171551197927aae0d1bc00446df6e7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704662"
---
# <a name="query-and-view-designer-tools-visual-database-tools"></a><span data-ttu-id="038e1-102">查詢和檢視設計工具 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="038e1-102">Query and View Designer Tools (Visual Database Tools)</span></span>
  <span data-ttu-id="038e1-103">設計查詢、檢視、內嵌函數或單一陳述式預存程序時，您所使用的設計工具將由四個窗格組成：[圖表] 窗格、[準則] 窗格、[SQL] 窗格和 [結果] 窗格。</span><span class="sxs-lookup"><span data-stu-id="038e1-103">When you design a query, view, in-line function, or single-statement stored procedure, the designer you use consists of four panes: the Diagram pane, the Criteria pane, the SQL pane, and the Results pane.</span></span>  
  
 <span data-ttu-id="038e1-104">![查詢設計工具](../../database-engine/media//vs-queryviewdsgpanes.gif "查詢設計工具")</span><span class="sxs-lookup"><span data-stu-id="038e1-104">![Query Designer](../../database-engine/media//vs-queryviewdsgpanes.gif "Query Designer")</span></span>  
  
-   <span data-ttu-id="038e1-105">[圖表] 窗格將顯示您進行查詢的資料表和其他資料表值物件。</span><span class="sxs-lookup"><span data-stu-id="038e1-105">The Diagram pane displays the tables and other table-valued objects that you are querying.</span></span> <span data-ttu-id="038e1-106">每一個矩形代表一個資料表或資料表值物件，並顯示可用的資料行。</span><span class="sxs-lookup"><span data-stu-id="038e1-106">Each rectangle represents a table or table-valued object and shows the available data columns.</span></span> <span data-ttu-id="038e1-107">矩形間的行即代表聯結 (Join)。</span><span class="sxs-lookup"><span data-stu-id="038e1-107">Joins are indicated by lines between the rectangles.</span></span> <span data-ttu-id="038e1-108">如需詳細資訊，請參閱[圖表窗格 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="038e1-108">For more information, see [Diagram Pane &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
-   <span data-ttu-id="038e1-109">[準則] 窗格含有類似工作表的方格，您可以在該窗格中指定選項，如要顯示的資料行、要選取的資料列、如何將資料列群組化等等。</span><span class="sxs-lookup"><span data-stu-id="038e1-109">The Criteria pane contains a spreadsheet-like grid in which you specify options, such as which data columns to display, what rows to select, how to group rows, and so on.</span></span> <span data-ttu-id="038e1-110">如需詳細資訊，請參閱[準則窗格 &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="038e1-110">For more information, see [Criteria Pane &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md).</span></span>  
  
-   <span data-ttu-id="038e1-111">[SQL] 窗格顯示查詢或檢視的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="038e1-111">The SQL pane displays the SQL statement for the query or view.</span></span> <span data-ttu-id="038e1-112">您可以編輯設計工具建立的 SQL 陳述式，或輸入您自己的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="038e1-112">You can edit the SQL statement created by the Designer or you can enter your own SQL statement.</span></span> <span data-ttu-id="038e1-113">當您要輸入無法使用 [圖表] 和 [準則] 窗格建立的 SQL 陳述式時 (如聯結查詢)，這項功能便很有用。</span><span class="sxs-lookup"><span data-stu-id="038e1-113">It is particularly useful for entering SQL statements that cannot be created using the Diagram and Criteria panes, such as union queries.</span></span> <span data-ttu-id="038e1-114">如需詳細資訊，請參閱 [SQL 窗格 &#40;Visual Database Tools&#41;](sql-pane-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="038e1-114">For more information, see [SQL Pane &#40;Visual Database Tools&#41;](sql-pane-visual-database-tools.md).</span></span>  
  
-   <span data-ttu-id="038e1-115">[結果] 窗格顯示查詢或檢視擷取的資料格。</span><span class="sxs-lookup"><span data-stu-id="038e1-115">The Results pane shows a grid with data retrieved by the query or view.</span></span> <span data-ttu-id="038e1-116">在 [查詢和檢視設計師] 中，該窗格顯示的是最近執行 SELECT 查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="038e1-116">In the Query and View Designer, the pane shows the results of the most recently executed SELECT query.</span></span> <span data-ttu-id="038e1-117">您可以編輯資料格方格中的值以及加入或刪除資料列來修改資料庫。</span><span class="sxs-lookup"><span data-stu-id="038e1-117">You can modify the database by editing values in the cells of the grid, and you can add or delete rows.</span></span> <span data-ttu-id="038e1-118">如需詳細資訊，請參閱[結果窗格 &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="038e1-118">For more information, see [Results Pane &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="038e1-119">您可以在其中任何一個窗格中建立查詢或檢視：您可以在 [圖表] 窗格中選擇要指定顯示的資料行、將資料行輸入 [準則] 窗格，或使之成為 [SQL] 窗格中 SQL 陳述式的一部份。</span><span class="sxs-lookup"><span data-stu-id="038e1-119">You can create a query or view by working in any of the panes: you can specify a column to display by choosing it in the Diagram pane, entering it into the Criteria pane, or making it part of the SQL statement in the SQL pane.</span></span>  
  
## <a name="displaying-and-hiding-panes"></a><span data-ttu-id="038e1-120">顯示及隱藏窗格</span><span class="sxs-lookup"><span data-stu-id="038e1-120">Displaying and Hiding Panes</span></span>  
 <span data-ttu-id="038e1-121">若要隱藏窗格或顯示看不見的窗格，請以滑鼠右鍵按一下設計介面，指向 [窗格]  ，然後按一下窗格名稱。</span><span class="sxs-lookup"><span data-stu-id="038e1-121">To hide a pane or display a pane that is not visible, right-click the design surface, point to **Pane**, and then click the name of the pane.</span></span> <span data-ttu-id="038e1-122">如果在查詢設計工具模式中開啟 查詢和檢視表設計工具，則無法使用 結果  窗格。</span><span class="sxs-lookup"><span data-stu-id="038e1-122">If the Query and View Designer is opened in Query Designer mode, the **Results** pane is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="038e1-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="038e1-123">See Also</span></span>  
 <span data-ttu-id="038e1-124">[設計查詢和觀看 how to 主題 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="038e1-124">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="038e1-125">[&#40;Visual Database Tools 開啟查詢和 View Designer&#41;](open-the-query-and-view-designer-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="038e1-125">[Open the Query and View Designer &#40;Visual Database Tools&#41;](open-the-query-and-view-designer-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="038e1-126">SQL 編輯器 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="038e1-126">SQL Editor &#40;Visual Database Tools&#41;</span></span>](sql-editor-visual-database-tools.md)  
  
  
