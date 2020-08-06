---
title: 將資料表加入查詢 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting tables
- adding tables
- queries [SQL Server], tables
ms.assetid: 6551aa7e-31a1-4636-852a-819bc53d658b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 572002bc913cc9916a75ce2b16c12064452d250f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596435"
---
# <a name="add-tables-to-queries-visual-database-tools"></a><span data-ttu-id="9be7a-102">將資料表加入查詢 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9be7a-102">Add Tables to Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="9be7a-103">建立查詢時，您會從資料表或結構與資料表類似的其他物件 (檢視和某些使用者定義函式) 擷取資料。</span><span class="sxs-lookup"><span data-stu-id="9be7a-103">When you create a query, you are retrieving data from a table or other objects structured like tables - views and certain user-defined functions.</span></span> <span data-ttu-id="9be7a-104">若要在查詢中使用上述物件，請將這些物件新增到 [圖表窗格]  。</span><span class="sxs-lookup"><span data-stu-id="9be7a-104">To work with any of these objects in your query, you add them to the **Diagram Pane**.</span></span>  
  
### <a name="to-add-a-table-or-table-valued-object-to-a-query"></a><span data-ttu-id="9be7a-105">若要將資料表或資料表值物件加入至查詢</span><span class="sxs-lookup"><span data-stu-id="9be7a-105">To add a table or table-valued object to a query</span></span>  
  
1.  <span data-ttu-id="9be7a-106">在查詢和檢視表設計工具之 [圖表窗格]  的背景上按一下滑鼠右鍵，再從捷徑功能表中選擇 [加入資料表]  。</span><span class="sxs-lookup"><span data-stu-id="9be7a-106">In the **Diagram pane** of the Query and View Designer, right-click the background and choose **Add Table** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="9be7a-107">在 [加入資料表]  對話方塊中，選取您要新增到查詢中之物件類型所屬的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9be7a-107">In the **Add Table** dialog box, select the tab for the type of object you want to add to the query.</span></span>  
  
3.  <span data-ttu-id="9be7a-108">在項目清單中，按兩下您要加入的每個項目。</span><span class="sxs-lookup"><span data-stu-id="9be7a-108">In the list of items, double-click each item you want to add.</span></span>  
  
4.  <span data-ttu-id="9be7a-109">當您完成新增項目時，請按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="9be7a-109">When you finish adding items, click **Close**.</span></span>  
  
     <span data-ttu-id="9be7a-110">查詢和檢視表設計工具會據此更新 [圖表窗格]  、[準則窗格]  及 [SQL 窗格]  。</span><span class="sxs-lookup"><span data-stu-id="9be7a-110">The Query and View Designer updates the **Diagram Pane**, **Criteria Pane**, and **SQL Pane** accordingly.</span></span>  
  
 <span data-ttu-id="9be7a-111">當您在 [SQL] 窗格的陳述式中參考資料表和檢視時，這些資料表和檢視會自動加入至查詢中。</span><span class="sxs-lookup"><span data-stu-id="9be7a-111">Tables and views are automatically added to the query when you reference them in the statement in the SQL pane.</span></span>  
  
 <span data-ttu-id="9be7a-112">如果您沒有足夠的存取權限，或如果提供者無法傳回相關資訊，查詢和檢視設計工具將不會顯示資料表或表格化物件 (Table-Structured Object) 的資料行。</span><span class="sxs-lookup"><span data-stu-id="9be7a-112">The Query and View Designer will not display data columns for a table or table-structured object if you do not have sufficient access rights to it or if the provider cannot return information about it.</span></span> <span data-ttu-id="9be7a-113">在這個情況中，資料表或表格化物件只會顯示標題列和 [\* (所有資料行)] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="9be7a-113">In such cases, only a title bar and the \* (All Columns) check box are displayed for the table or table-valued object.</span></span>  
  
### <a name="to-add-an-existing-query-to-a-new-query"></a><span data-ttu-id="9be7a-114">若要將現有查詢加入至新查詢</span><span class="sxs-lookup"><span data-stu-id="9be7a-114">To add an existing query to a new query</span></span>  
  
1.  <span data-ttu-id="9be7a-115">請確定您建立的新查詢中顯示有 [SQL 窗格]  。</span><span class="sxs-lookup"><span data-stu-id="9be7a-115">Make sure the **SQL Pane** is displayed in the new query you are creating.</span></span>  
  
2.  <span data-ttu-id="9be7a-116">在 [SQL 窗格]  中，於 FROM 一字之後輸入左、右括號 ()。</span><span class="sxs-lookup"><span data-stu-id="9be7a-116">In the **SQL Pane**, type a right and left parentheses () after the word FROM.</span></span>  
  
3.  <span data-ttu-id="9be7a-117">開啟現有查詢的 [查詢設計工具]</span><span class="sxs-lookup"><span data-stu-id="9be7a-117">Open the Query Designer for the existing query.</span></span> <span data-ttu-id="9be7a-118">\(您現在已開啟兩個 [查詢設計工具])。</span><span class="sxs-lookup"><span data-stu-id="9be7a-118">(You now have two Query Designers open.)</span></span>  
  
4.  <span data-ttu-id="9be7a-119">顯示內部查詢 (即您要加入所新增外部查詢之現有查詢) 的 [SQL 窗格]  。</span><span class="sxs-lookup"><span data-stu-id="9be7a-119">Display the **SQL Pane** for the inner query - the existing query you are including in the new, outer query.</span></span>  
  
5.  <span data-ttu-id="9be7a-120">選取 [SQL 窗格]  中的所有文字，再將其複製到剪貼簿中。</span><span class="sxs-lookup"><span data-stu-id="9be7a-120">Select all the text in the **SQL Pane**, and copy it to the Clipboard.</span></span>  
  
6.  <span data-ttu-id="9be7a-121">按一下新查詢中的 [SQL 窗格]  ，並將游標置於先前新增的括號之中，然後貼上剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="9be7a-121">Click in the **SQL Pane** of the new query, situate the cursor between the parentheses you added, and paste the contents of the Clipboard.</span></span>  
  
7.  <span data-ttu-id="9be7a-122">在 [SQL 窗格]  中，於右括號之後新增別名。</span><span class="sxs-lookup"><span data-stu-id="9be7a-122">Still in the **SQL Pane**, add an alias after the right parenthesis.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9be7a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9be7a-123">See Also</span></span>  
 <span data-ttu-id="9be7a-124">[&#40;Visual Database Tools 建立資料表別名&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9be7a-124">[Create Table Aliases &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="9be7a-125">[從查詢中移除資料表 &#40;Visual Database Tools&#41;](remove-tables-from-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9be7a-125">[Remove Tables from Queries &#40;Visual Database Tools&#41;](remove-tables-from-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="9be7a-126">[&#40;Visual Database Tools 指定搜尋準則&#41;](specify-search-criteria-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9be7a-126">[Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md) </span></span>  
 <span data-ttu-id="9be7a-127">[&#40;Visual Database Tools&#41;匯總查詢結果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9be7a-127">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="9be7a-128">使用查詢執行基本作業 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="9be7a-128">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
