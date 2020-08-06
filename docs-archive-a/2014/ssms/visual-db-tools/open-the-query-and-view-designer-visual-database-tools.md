---
title: 開啟查詢和檢視表設計工具 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- opening View Designer
- View Designer, opening
- Query Designer [SQL Server], opening
- opening Query Designer
ms.assetid: b473f258-d53c-41c0-9ad9-528a2ff141f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3a36a0a9f014759269517a5774167f84c19b0b18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596422"
---
# <a name="open-the-query-and-view-designer-visual-database-tools"></a><span data-ttu-id="97d36-102">開啟查詢和檢視表設計工具 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="97d36-102">Open the Query and View Designer (Visual Database Tools)</span></span>
  <span data-ttu-id="97d36-103">在開啟檢視的定義、顯示查詢或檢視的結果，或者建立或開啟查詢時，[查詢和檢視設計師] 會開啟。</span><span class="sxs-lookup"><span data-stu-id="97d36-103">The Query and View Designer opens when you open the definition of a view, show the results for a query or view, or create or open a query.</span></span> <span data-ttu-id="97d36-104">這包含四個個別的窗格：</span><span class="sxs-lookup"><span data-stu-id="97d36-104">It consists of four separate panes:</span></span>  
  
-   <span data-ttu-id="97d36-105">[圖表] 窗格會以圖形顯示您從資料連接所選取的資料表或資料表值物件。</span><span class="sxs-lookup"><span data-stu-id="97d36-105">The Diagram pane presents a graphic display of the tables or table-valued objects you have selected from the data connection.</span></span> <span data-ttu-id="97d36-106">同時還會顯示資料表或物件之間的任何聯結關聯性。</span><span class="sxs-lookup"><span data-stu-id="97d36-106">It also shows any join relationships among them.</span></span>  
  
-   <span data-ttu-id="97d36-107">只要將您的選擇輸入於類似方格的試算表，[準則] 窗格便可以讓您指定查詢選項 (例如，要顯示的資料行、如何排序結果，以及要選取的資料列)。</span><span class="sxs-lookup"><span data-stu-id="97d36-107">The Criteria pane allows you to specify query options - such as which data columns to display, how to order the results, and what rows to select - by entering your choices into a spreadsheet-like grid.</span></span>  
  
-   <span data-ttu-id="97d36-108">您可以使用 [SQL] 窗格建立您自己的 SQL 陳述式，也可以使用 [準則] 窗格和 [圖表] 窗格建立陳述式。在這個情況中，SQL 陳述式會在 [SQL] 窗格中建立。</span><span class="sxs-lookup"><span data-stu-id="97d36-108">You can use the SQL pane to create your own SQL statement, or you can use the Criteria pane and Diagram pane to create the statement, in which case the SQL statements will be created in the SQL pane.</span></span> <span data-ttu-id="97d36-109">建立查詢時，[SQL] 窗格將自動更新並重新格式化以方便您讀取。</span><span class="sxs-lookup"><span data-stu-id="97d36-109">As you build your query, the SQL pane automatically updates and reformats to be easily read.</span></span>  
  
-   <span data-ttu-id="97d36-110">[結果] 窗格顯示的是最近執行選取查詢的結果</span><span class="sxs-lookup"><span data-stu-id="97d36-110">The Results pane shows the results of the most recently executed Select query.</span></span> <span data-ttu-id="97d36-111">(其他查詢類型的結果則顯示在訊息方塊中)。</span><span class="sxs-lookup"><span data-stu-id="97d36-111">(The results of other query types are displayed in message boxes.)</span></span>  
  
-   <span data-ttu-id="97d36-112">這些窗格可以用來使用查詢和檢視。</span><span class="sxs-lookup"><span data-stu-id="97d36-112">These panes are useful for working with both queries and views.</span></span>  
  
-   <span data-ttu-id="97d36-113">開啟檢視或查詢時，某些窗格或所有窗格會一併開啟。</span><span class="sxs-lookup"><span data-stu-id="97d36-113">When you open a view or query some or all of the panes open with it.</span></span> <span data-ttu-id="97d36-114">哪些窗格會開啟，會根據 [選項]  對話方塊中的設定以及所連接的資料庫管理系統而定。</span><span class="sxs-lookup"><span data-stu-id="97d36-114">Which ones open depend on the settings in the **Options** dialog box and what database management system you're connected to.</span></span> <span data-ttu-id="97d36-115">預設值是四個窗格全部開啟。</span><span class="sxs-lookup"><span data-stu-id="97d36-115">The default is that all four open.</span></span>  
  
### <a name="to-open-the-query-and-view-designer-for-a-view"></a><span data-ttu-id="97d36-116">開啟檢視的查詢和檢視設計師</span><span class="sxs-lookup"><span data-stu-id="97d36-116">To open the Query and View Designer for a view</span></span>  
  
1.  <span data-ttu-id="97d36-117">在物件總管中，以滑鼠右鍵按一下您要開啟的檢視，然後按一下 [設計]  或 [開啟檢視]  。</span><span class="sxs-lookup"><span data-stu-id="97d36-117">In Object Explorer, right-click the view you want to open and click **Design** or **Open View**.</span></span>  
  
     <span data-ttu-id="97d36-118">如果您選擇 [設計]  ，查詢和檢視表設計工具窗格即會依照 [選項]  對話方塊中選取的選項開啟。</span><span class="sxs-lookup"><span data-stu-id="97d36-118">If you chose **Design**, the Query and View Designer panes open as dictated by the options selected in the **Options** dialog box.</span></span> <span data-ttu-id="97d36-119">如果您選擇 [開啟檢視]  ，只有 [結果] 窗格預設會開啟。</span><span class="sxs-lookup"><span data-stu-id="97d36-119">If you chose **Open View**, only the Results pane opens by default.</span></span>  
  
### <a name="to-open-the-query-and-view-designer-for-an-existing-query"></a><span data-ttu-id="97d36-120">若要開啟現有查詢的查詢和檢視設計師</span><span class="sxs-lookup"><span data-stu-id="97d36-120">To open the Query and View Designer for an existing query</span></span>  
  
1.  <span data-ttu-id="97d36-121">在方案總管中，展開 [查詢]  資料夾。</span><span class="sxs-lookup"><span data-stu-id="97d36-121">In Solution Explorer, expand the **Queries** folder.</span></span>  
  
2.  <span data-ttu-id="97d36-122">按兩下要開啟的查詢。</span><span class="sxs-lookup"><span data-stu-id="97d36-122">Double-click the query you want to open.</span></span>  
  
3.  <span data-ttu-id="97d36-123">反白顯示查詢陳述式，在反白顯示區域上按一下滑鼠右鍵，然後按一下 [在編輯器中設計查詢]  。</span><span class="sxs-lookup"><span data-stu-id="97d36-123">Highlight the query statement(s), right-click the highlighted area and click **Design Query in Editor**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d36-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97d36-124">See Also</span></span>  
 <span data-ttu-id="97d36-125">[設計查詢和觀看 how to 主題 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="97d36-125">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="97d36-126">查詢和檢視表設計工具 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="97d36-126">Query and View Designer Tools &#40;Visual Database Tools&#41;</span></span>](query-and-view-designer-tools-visual-database-tools.md)  
  
  
