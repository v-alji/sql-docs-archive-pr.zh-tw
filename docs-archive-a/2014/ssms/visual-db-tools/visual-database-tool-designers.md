---
title: Visual Database Tool 設計工具 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- data sources [SQL Server]
- View Designer
- Visual Database Tools [SQL Server]
- Database Diagram Designer
- Query Designer [SQL Server]
- design tools [Visual Database Tools]
- Table Designer
- Visual Database Tools [SQL Server], designers
- Properties window [Visual Database Tools]
ms.assetid: bd0ca68e-6f69-42dd-bcb5-ce511673769c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6a307a0a82aa02e7197189ca6cfc9ba70a3fea33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592425"
---
# <a name="visual-database-tool-designers"></a><span data-ttu-id="fa48c-102">Visual Database Tool 設計工具</span><span class="sxs-lookup"><span data-stu-id="fa48c-102">Visual Database Tool Designers</span></span>
  <span data-ttu-id="fa48c-103">Visual Database Tools 是設計組合工具，可用來使用資料來源。</span><span class="sxs-lookup"><span data-stu-id="fa48c-103">The Visual Database Tools are a combination of design tools you can use to work with a data source.</span></span> <span data-ttu-id="fa48c-104">您可以使用這些工具來建立查詢、設計或修改資料庫結構，或是更新資料。</span><span class="sxs-lookup"><span data-stu-id="fa48c-104">You can use them to create queries, design or modify a database structure, or update data.</span></span> <span data-ttu-id="fa48c-105">這些工具包括資料庫圖表設計工具、資料表設計師以及查詢和檢視設計師。</span><span class="sxs-lookup"><span data-stu-id="fa48c-105">The tools are Database Diagram Designer, Table Designer, and Query and View Designer.</span></span>  
  
## <a name="properties-window"></a><span data-ttu-id="fa48c-106">屬性視窗</span><span class="sxs-lookup"><span data-stu-id="fa48c-106">Properties Window</span></span>  
 <span data-ttu-id="fa48c-107">[屬性] 視窗並非專屬於 Visual Database Tools，但可在其中進行許多修改動作。</span><span class="sxs-lookup"><span data-stu-id="fa48c-107">The properties window is not specific to Visual Database Tools, but it is where many modifications can be made.</span></span> <span data-ttu-id="fa48c-108">其顯示目前所選取項目 (例如，資料表) 的屬性，並可讓您編輯這些屬性 (從屬性名稱到資料行定序的所有屬性)。</span><span class="sxs-lookup"><span data-stu-id="fa48c-108">It shows the properties for the item currently selected (like a table) and allows you to edit those properties (everything from the properties name to the collation of a column).</span></span> <span data-ttu-id="fa48c-109">某些屬性可以在屬性視窗中查看，但必須以不同工具修改。</span><span class="sxs-lookup"><span data-stu-id="fa48c-109">Some properties can be seen in the properties window but must be modified in a different tool.</span></span>  
  
## <a name="database-diagram-designer"></a><span data-ttu-id="fa48c-110">資料庫圖表設計工具</span><span class="sxs-lookup"><span data-stu-id="fa48c-110">Database Diagram Designer</span></span>  
 <span data-ttu-id="fa48c-111">資料庫圖表設計工具提供了讓您其中視覺化地建立、編輯和顯示資料庫中之資料表和關聯性的視窗。</span><span class="sxs-lookup"><span data-stu-id="fa48c-111">Database Diagram Designer provides a window where you can visually create, edit, and show the tables and relationships in a database.</span></span>  
  
 <span data-ttu-id="fa48c-112">若要顯示資料庫圖表設計工具，請開啟現有的圖表或以滑鼠右鍵按一下物件總管中的 [資料庫] 節點，再從下拉式功能表中選擇 [新增資料庫圖表]  。</span><span class="sxs-lookup"><span data-stu-id="fa48c-112">To display Database Diagram Designer, open an existing diagram or right-click the Database node in Object Explorer and choose **New Database Diagram** from the drop-down menu.</span></span>  
  
 <span data-ttu-id="fa48c-113">設計工具開啟後，[資料庫圖表]  功能表會出現在主功能表中。</span><span class="sxs-lookup"><span data-stu-id="fa48c-113">Once the designer is open, the **Database Diagram** menu appears in the main menu.</span></span> <span data-ttu-id="fa48c-114">此功能表可存取設計師的特殊功能。</span><span class="sxs-lookup"><span data-stu-id="fa48c-114">This menu is the access point to the designer's special features.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa48c-115">此設計師使用 Microsoft SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fa48c-115">This designer works with Microsoft SQL Server databases.</span></span>  
>   
>  <span data-ttu-id="fa48c-116">這個版本的 Visual Database Tools 不支援 Microsoft SQL Server 7 (含) 之前版本。</span><span class="sxs-lookup"><span data-stu-id="fa48c-116">This version of Visual Database Tools does not support Microsoft SQL Server version 7 and earlier.</span></span>  
  
## <a name="table-designer"></a><span data-ttu-id="fa48c-117">資料表設計工具</span><span class="sxs-lookup"><span data-stu-id="fa48c-117">Table Designer</span></span>  
 <span data-ttu-id="fa48c-118">資料表設計師是一種視覺化工具，可以讓您設計並以視覺化方式呈現所連接之 Microsoft SQL Server 資料庫中的單一資料表。</span><span class="sxs-lookup"><span data-stu-id="fa48c-118">Table Designer is a visual tool allowing you to design and visualize a single table in a Microsoft SQL Server database to which you are connected.</span></span>  
  
 <span data-ttu-id="fa48c-119">資料表設計師有兩個窗格。</span><span class="sxs-lookup"><span data-stu-id="fa48c-119">Table Designer has two panes.</span></span> <span data-ttu-id="fa48c-120">上方區域顯示方格；方格中的每個資料列各描述一個資料庫資料行。</span><span class="sxs-lookup"><span data-stu-id="fa48c-120">The upper area shows a grid; each row of the grid describes one database column.</span></span> <span data-ttu-id="fa48c-121">方格將顯示每個資料庫資料行的基本屬性：資料行名稱、資料類型和允許 null 值的設定。</span><span class="sxs-lookup"><span data-stu-id="fa48c-121">For each database column, the grid displays its fundamental attributes: column name, data type, and nulls-allowed setting.</span></span>  
  
 <span data-ttu-id="fa48c-122">[資料表設計師] 下方的 [資料行屬性] 索引標籤，顯示在上方區域反白顯示之資料行的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="fa48c-122">The lower area of Table Designer, the Column Properties tab, shows additional attributes for whichever column is highlighted in the upper area.</span></span>  
  
 <span data-ttu-id="fa48c-123">從 [資料表設計師]，您也可以在方格區按一下滑鼠右鍵，存取可用以建立和修改資料表關聯性、條件約束、索引和索引鍵的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="fa48c-123">From Table Designer, you can also right-click in the grid section to access dialog boxes through which you can create and modify relationships, constraints, indexes, and keys for the table.</span></span>  
  
 <span data-ttu-id="fa48c-124">若要顯示資料表設計工具，請開啟現有的資料表或以滑鼠右鍵按一下物件總管中的 [資料表]  節點，再從下拉式功能表中選擇 [新增資料表]  。</span><span class="sxs-lookup"><span data-stu-id="fa48c-124">To display Table Designer, open an existing table, or right-click the **Tables** node in Object Explorer, and choose **Add New Table** from the drop-down menu.</span></span>  
  
 <span data-ttu-id="fa48c-125">設計師一旦開啟，[資料表設計師] 功能表會出現在主功能表中。</span><span class="sxs-lookup"><span data-stu-id="fa48c-125">Once the designer is open, the Table Designer menu appears in the main menu.</span></span> <span data-ttu-id="fa48c-126">此功能表可存取設計師的特殊功能。</span><span class="sxs-lookup"><span data-stu-id="fa48c-126">This menu is the access point to the designer's special features.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa48c-127">此設計師使用 Microsoft SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fa48c-127">This designer works with Microsoft SQL Server databases.</span></span>  
>   
>  <span data-ttu-id="fa48c-128">這個版本的 Visual Database Tools 不支援 Microsoft SQL Server 7 (含) 之前版本。</span><span class="sxs-lookup"><span data-stu-id="fa48c-128">This version of Visual Database Tools does not support Microsoft SQL Server version 7 and earlier.</span></span>  
  
## <a name="query-and-view-designer"></a><span data-ttu-id="fa48c-129">查詢和檢視表設計工具</span><span class="sxs-lookup"><span data-stu-id="fa48c-129">Query and View Designer</span></span>  
 <span data-ttu-id="fa48c-130">[查詢和檢視設計師] 實際上是兩個使用非常相似的方式運作的工具。</span><span class="sxs-lookup"><span data-stu-id="fa48c-130">Query and View designer is actually two tools that work in very similar ways.</span></span> <span data-ttu-id="fa48c-131">某些主要差異在於：</span><span class="sxs-lookup"><span data-stu-id="fa48c-131">Some of the major differences are:</span></span>  
  
-   <span data-ttu-id="fa48c-132">檢視儲存於資料庫，而查詢和 Visual Studio 資料庫專案一起儲存。</span><span class="sxs-lookup"><span data-stu-id="fa48c-132">Views are saved with the database while a query is saved with a Visual Studio database project.</span></span>  
  
-   <span data-ttu-id="fa48c-133">[查詢設計工具] 可使用任何的資料來源，而 [檢視設計工具] 只能使用 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="fa48c-133">Query Designer works with nearly any data source, where View Designer works only with SQL Server.</span></span>  
  
-   <span data-ttu-id="fa48c-134">[查詢設計工具] 可讓您設計 SELECT、INSERT、UPDATE 和 DELETE DML 陳述式，而檢視只能包含 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="fa48c-134">Query Designer allows you to design SELECT, INSERT, UPDATE and DELETE DML statements, while views can only contain SELECT statements.</span></span>  
  
### <a name="view-designer"></a><span data-ttu-id="fa48c-135">檢視設計工具</span><span class="sxs-lookup"><span data-stu-id="fa48c-135">View Designer</span></span>  
 <span data-ttu-id="fa48c-136">[檢視設計師] 可讓您設計和視覺化現有檢視，或是在所連接的 Microsoft SQL Server 資料庫中建立新的檢視。</span><span class="sxs-lookup"><span data-stu-id="fa48c-136">View Designer allows you to design and visualize an existing view or create a new one in a Microsoft SQL Server database to which you are connected.</span></span>  
  
 <span data-ttu-id="fa48c-137">檢視設計師有四個窗格：圖表窗格、準則窗格、SQL 窗格和結果窗格。</span><span class="sxs-lookup"><span data-stu-id="fa48c-137">View Designer has four panes: the Diagram pane, the Criteria pane, the SQL pane, and the Results pane.</span></span> <span data-ttu-id="fa48c-138">如需這些每個窗格的詳細資訊，請參閱[查詢和檢視表設計工具 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="fa48c-138">For more detailed information on each of these panes, see [Query and View Designer Tools &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="fa48c-139">若要顯示檢視表設計工具，請開啟現有的檢視或以滑鼠右鍵按一下物件總管中的 [檢視]  節點，再從下拉式功能表中選擇 [新增檢視]  。</span><span class="sxs-lookup"><span data-stu-id="fa48c-139">To display View Designer, open an existing view or right-click the **View** node in Object Explorer and choose **Add New View** from the drop-down menu.</span></span>  
  
 <span data-ttu-id="fa48c-140">設計工具開啟後，[查詢設計工具]  功能表會出現在主功能表中。</span><span class="sxs-lookup"><span data-stu-id="fa48c-140">Once the designer is open, the **Query Designer** menu appears in the main menu.</span></span> <span data-ttu-id="fa48c-141">此功能表可存取設計師的特殊功能。</span><span class="sxs-lookup"><span data-stu-id="fa48c-141">This menu is the access point to the designer's special features.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa48c-142">此設計師使用 Microsoft SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fa48c-142">This designer works with Microsoft SQL Server databases.</span></span>  
>   
>  <span data-ttu-id="fa48c-143">這個版本的 Visual Database Tools 不支援 Microsoft SQL Server 7 (含) 之前版本。</span><span class="sxs-lookup"><span data-stu-id="fa48c-143">This version of Visual Database Tools does not support Microsoft SQL Server version 7 and earlier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa48c-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa48c-144">See Also</span></span>  
 <span data-ttu-id="fa48c-145">[設計資料庫關係圖 &#40;Visual Database Tools&#41;](design-database-diagrams-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="fa48c-145">[Design Database Diagrams &#40;Visual Database Tools&#41;](design-database-diagrams-visual-database-tools.md) </span></span>  
 <span data-ttu-id="fa48c-146">[設計資料表 &#40;Visual Database Tools&#41;](design-tables-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="fa48c-146">[Design Tables &#40;Visual Database Tools&#41;](design-tables-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="fa48c-147">設計查詢和檢視使用說明主題 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="fa48c-147">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
