---
title: 建立查詢 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], creating
ms.assetid: 696a080d-848f-44d3-a918-e29bafaab85a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 52392adff03b27e1c4c19f354bc62c350cccf17a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584945"
---
# <a name="create-queries-visual-database-tools"></a><span data-ttu-id="0fd67-102">建立查詢 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="0fd67-102">Create Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="0fd67-103">查詢可讓您從資料庫的資料表和檢視中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="0fd67-103">Queries allow you to retrieve data from the tables and views in your database.</span></span> <span data-ttu-id="0fd67-104">您可以在查詢和檢視表設計工具  中建立並使用查詢，這包含四個窗格：[[圖表] 窗格](visual-database-tools.md)、[[SQL] 窗格](sql-pane-visual-database-tools.md)、[[準則] 窗格](criteria-pane-visual-database-tools.md)及 [[結果] 窗格](results-pane-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="0fd67-104">You create and work with queries in **Query and View Designer**, which is composed of four panes: the [Diagram Pane](visual-database-tools.md), the [SQL Pane](sql-pane-visual-database-tools.md), the [Criteria Pane](criteria-pane-visual-database-tools.md), and the [Results Pane](results-pane-visual-database-tools.md).</span></span>  
  
### <a name="to-create-a-new-query"></a><span data-ttu-id="0fd67-105">若要建立新的查詢</span><span class="sxs-lookup"><span data-stu-id="0fd67-105">To create a new query</span></span>  
  
1.  <span data-ttu-id="0fd67-106">在物件總管  中，展開您要查詢之資料庫的 [資料表]  節點。</span><span class="sxs-lookup"><span data-stu-id="0fd67-106">In **Object Explorer**, expand the **Tables** node for the database you want to query.</span></span> <span data-ttu-id="0fd67-107">以滑鼠右鍵按一下您要查詢的資料表，然後按一下 [開啟資料表]  。</span><span class="sxs-lookup"><span data-stu-id="0fd67-107">Right-click the table you want to query and click **Open Table**.</span></span>  
  
2.  <span data-ttu-id="0fd67-108">若要將更多的資料表新增至查詢，請在 [查詢設計工具] 功能表上，選取 [新增資料表]  。</span><span class="sxs-lookup"><span data-stu-id="0fd67-108">To add more tables to the query, on the Query Designer menu, select **Add Table**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0fd67-109">如果您未看見 [圖表]  、[SQL]  、[準則]  或 [結果]  窗格，則從 [查詢設計工具] 功能表中，指向 [窗格]  ，再按要開啟的窗格。</span><span class="sxs-lookup"><span data-stu-id="0fd67-109">If you do not see the **Diagram**, **SQL**, **Criteria**, or **Results** panes, from the Query Designer menu, point to **Pane** and click the pane you want to open.</span></span>  
  
3.  <span data-ttu-id="0fd67-110">從 [新增資料表]  對話方塊中，選取要查詢的資料表，然後針對每個資料表按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="0fd67-110">In the **Add Table** dialog box, select the tables you want to query and click **Add** for each one.</span></span>  
  
4.  <span data-ttu-id="0fd67-111">新增所有要查詢的資料表後，按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="0fd67-111">Once you have added all the tables you want to query, click **Close**.</span></span>  
  
     <span data-ttu-id="0fd67-112">若要在稍後新增更多資料表，在 [圖表]  窗格的空白處按一下滑鼠右鍵，然後從快速鍵功能表中按一下 [新增資料表]  。</span><span class="sxs-lookup"><span data-stu-id="0fd67-112">To add more tables later, right-click the open space in the **Diagram** pane and from the shortcut menu click **Add Table**.</span></span>  
  
5.  <span data-ttu-id="0fd67-113">在 [圖表]  窗格中，為要查詢的每個資料行核取資料表值物件中的方塊。</span><span class="sxs-lookup"><span data-stu-id="0fd67-113">In the **Diagram Pane**, check the boxes in the table-valued objects for each column you want to query.</span></span>  
  
6.  <span data-ttu-id="0fd67-114">從 [查詢設計工具] 功能表中，選擇 [執行 SQL]  執行查詢。</span><span class="sxs-lookup"><span data-stu-id="0fd67-114">From the Query Designer menu, choose **Execute SQL** to run your query.</span></span>  
  
 <span data-ttu-id="0fd67-115">若要進一步修改查詢，您可以在 [SQL]  窗格中變更 SQL 程式碼，或者從 [準則]  窗格中選擇排列次序和資料行別名之類的選項。</span><span class="sxs-lookup"><span data-stu-id="0fd67-115">To further refine your query, you can change the SQL code in the **SQL Pane** or choose options such as sort order and column aliases in the **Criteria Pane.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fd67-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fd67-116">See Also</span></span>  
 <span data-ttu-id="0fd67-117">[&#40;Visual Database Tools&#41;儲存查詢](save-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="0fd67-117">[Save Queries &#40;Visual Database Tools&#41;](save-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="0fd67-118">[&#40;Visual Database Tools&#41;的查詢類型](types-of-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="0fd67-118">[Types of Queries &#40;Visual Database Tools&#41;](types-of-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="0fd67-119">[&#40;Visual Database Tools 指定搜尋準則&#41;](specify-search-criteria-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="0fd67-119">[Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md) </span></span>  
 <span data-ttu-id="0fd67-120">[&#40;Visual Database Tools&#41;匯總查詢結果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="0fd67-120">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="0fd67-121">使用查詢執行基本作業 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="0fd67-121">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
