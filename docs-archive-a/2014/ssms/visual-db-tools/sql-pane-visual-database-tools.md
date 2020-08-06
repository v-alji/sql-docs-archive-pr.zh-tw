---
title: SQL 窗格 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Query Designer [SQL Server], SQL pane
- View Designer, SQL pane
- SQL pane [Visual Database Tools]
ms.assetid: dbabab18-0614-415b-a2ef-9bcd0d320d5c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3a87ec1d5517852fefb152e0ec7b3165fa32988b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686665"
---
# <a name="sql-pane-visual-database-tools"></a><span data-ttu-id="6f4bb-102">SQL 窗格 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="6f4bb-102">SQL Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="6f4bb-103">您可以使用 [SQL] 窗格建立您自己的 SQL 陳述式，也可以使用 [準則] 窗格和 [圖表] 窗格建立陳述式。在這個情況中，SQL 陳述式會在 [SQL] 窗格中建立。</span><span class="sxs-lookup"><span data-stu-id="6f4bb-103">You can use the SQL pane to create your own SQL statement, or you can use the Criteria pane and Diagram pane to create the statement, in which case the SQL statements will be created in the SQL pane.</span></span> <span data-ttu-id="6f4bb-104">當您建置查詢時，[SQL 窗格] 會自動進行簡單的可讀性更新及重新格式化。</span><span class="sxs-lookup"><span data-stu-id="6f4bb-104">As you build your query, the SQL pane automatically updates and reformats for easy readability.</span></span>  
  
 <span data-ttu-id="6f4bb-105">若要開啟 [SQL 窗格]，請先開啟查詢和檢視設計工具 (按一下 [資料庫]  功能表中的 [新增查詢]  ，以在伺服器總管中選取資料庫物件)。</span><span class="sxs-lookup"><span data-stu-id="6f4bb-105">To open the SQL pane, first open Query and View Designer (with a database object selected in Server Explorer, from the **Database** menu, click **New Query**).</span></span> <span data-ttu-id="6f4bb-106">接著在 [查詢設計工具]  功能表中指向 [窗格]  按一下 [SQL]  。</span><span class="sxs-lookup"><span data-stu-id="6f4bb-106">Then from the **Query Designer** menu point to **Pane** and click **SQL**.</span></span>  
  
 <span data-ttu-id="6f4bb-107">您可以在 [SQL 窗格] 中：</span><span class="sxs-lookup"><span data-stu-id="6f4bb-107">In the SQL pane you can:</span></span>  
  
-   <span data-ttu-id="6f4bb-108">輸入 SQL 陳述式以建立新的查詢。</span><span class="sxs-lookup"><span data-stu-id="6f4bb-108">Create new queries by entering SQL statements.</span></span>  
  
-   <span data-ttu-id="6f4bb-109">根據您在 [圖表窗格] 和 [準則窗格] 所做的設定，修改由查詢和檢視設計工具所建立的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6f4bb-109">Modify the SQL statement created by the Query and View Designer based on settings you make in the Diagram and Criteria panes.</span></span>  
  
-   <span data-ttu-id="6f4bb-110">輸入使用資料庫 (您目前所使用的資料庫) 特定功能的陳述式。</span><span class="sxs-lookup"><span data-stu-id="6f4bb-110">Enter statements that take advantage of features specific to the database you are using.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f4bb-111">請確定您完全暸解所使用資料庫的資料庫物件識別規則。</span><span class="sxs-lookup"><span data-stu-id="6f4bb-111">Be sure you know the rules for identifying database objects in the database you are using.</span></span> <span data-ttu-id="6f4bb-112">如需詳細資料，請參閱資料庫管理系統中的文件集。</span><span class="sxs-lookup"><span data-stu-id="6f4bb-112">For details, see the documentation for your database management system.</span></span>  
  
## <a name="statements-in-the-sql-pane"></a><span data-ttu-id="6f4bb-113">SQL 窗格中的陳述式</span><span class="sxs-lookup"><span data-stu-id="6f4bb-113">Statements in the SQL Pane</span></span>  
 <span data-ttu-id="6f4bb-114">您可以直接在 [SQL 窗格] 中編輯目前查詢。</span><span class="sxs-lookup"><span data-stu-id="6f4bb-114">You can edit the current query directly in the SQL pane.</span></span> <span data-ttu-id="6f4bb-115">當移至其他窗格時，查詢和檢視設計工具將自動格式化陳述式，然後變更 [圖表窗格] 和 [準則窗格] 以符合陳述式。</span><span class="sxs-lookup"><span data-stu-id="6f4bb-115">When you move to another pane, the Query and View Designer automatically formats your statement, and then changes the Diagram and Criteria panes to match your statement.</span></span>  
  
 <span data-ttu-id="6f4bb-116">如果陳述式無法在 [圖表窗格] 和 [準則窗格] 中顯示，而這些窗格是可見的，查詢和檢視設計工具將顯示錯誤訊息，然後提供兩個選項：</span><span class="sxs-lookup"><span data-stu-id="6f4bb-116">If your statement cannot be represented in the Diagram and Criteria panes, and if those panes are visible, Query and View Designer displays an error and then offers you two choices:</span></span>  
  
-   <span data-ttu-id="6f4bb-117">忽略陳述式無法在 [圖表窗格] 及 [準則窗格] 中表示。</span><span class="sxs-lookup"><span data-stu-id="6f4bb-117">Ignore that the statement can not be represented in the Diagram and Criteria panes.</span></span>  
  
-   <span data-ttu-id="6f4bb-118">恢復無法顯示的變更，並還原成最新版本的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6f4bb-118">Undo the change that can not be represented and revert to the most recent version of the SQL statement.</span></span>  
  
 <span data-ttu-id="6f4bb-119">如果您選擇忽略陳述是無法在 [圖表窗格] 及 [準則窗格] 中表示，則查詢和檢視設計工具會將其他窗格變為暗灰色，表示這些窗格不再反映 [SQL 窗格] 的內容。</span><span class="sxs-lookup"><span data-stu-id="6f4bb-119">If you choose to ignore that the statement can not be represented in the Diagram and Criteria panes, the Query and View Designer dims the other panes to indicate that they no longer reflect the contents of the SQL pane.</span></span>  
  
 <span data-ttu-id="6f4bb-120">和其他 SQL 陳述式一樣，您可以繼續編輯和執行該陳述式。</span><span class="sxs-lookup"><span data-stu-id="6f4bb-120">You can continue to edit the statement and execute it as you would any SQL statement.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f4bb-121">如果您輸入 SQL 陳述式，然後又變更 [圖表窗格] 和 [準則窗格] 來進一步變更查詢，查詢和檢視設計工具將重新建立並重新顯示 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6f4bb-121">If you enter an SQL statement, but then make further changes to the query by changing the Diagram and Criteria panes, the Query and View Designer rebuilds and redisplays the SQL statement.</span></span> <span data-ttu-id="6f4bb-122">有時候，這個動作產生的 SQL 陳述式會不同於您原本輸入的陳述式 (雖然其結果相同)。</span><span class="sxs-lookup"><span data-stu-id="6f4bb-122">In some cases, this action results in an SQL statement that is constructed differently from the one you originally entered (though it will always yield the same results).</span></span> <span data-ttu-id="6f4bb-123">當您使用的搜尋條件牽涉到與 AND 和 OR 連結的幾個子句時，其不同之處最為明顯。</span><span class="sxs-lookup"><span data-stu-id="6f4bb-123">This difference is particularly likely when you are working with search conditions that involve several clauses linked with AND and OR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f4bb-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f4bb-124">See Also</span></span>  
 <span data-ttu-id="6f4bb-125">[&#40;Visual Database Tools 建立查詢&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6f4bb-125">[Create Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="6f4bb-126">[&#40;Visual Database Tools 執行查詢&#41;](run-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6f4bb-126">[Run Queries &#40;Visual Database Tools&#41;](run-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="6f4bb-127">[設計查詢和觀看 how to 主題 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6f4bb-127">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="6f4bb-128">[&#40;Visual Database Tools&#41;的圖表窗格](diagram-pane-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6f4bb-128">[Diagram Pane &#40;Visual Database Tools&#41;](diagram-pane-visual-database-tools.md) </span></span>  
 <span data-ttu-id="6f4bb-129">[&#40;Visual Database Tools&#41;的 [準則窗格]](criteria-pane-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="6f4bb-129">[Criteria Pane &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="6f4bb-130">結果窗格 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="6f4bb-130">Results Pane &#40;Visual Database Tools&#41;</span></span>](results-pane-visual-database-tools.md)  
  
  
