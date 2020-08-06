---
title: 查詢定義差異對話方塊 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69639
- vdtsql.chm:69640
- vdt.dlgbox.querydefinitionsdiffer
ms.assetid: 90383473-2922-40e5-9682-3850849aa856
author: stevestein
ms.author: sstein
ms.openlocfilehash: b9a39d5d6b739fa4ab1a96ea95b513ecb7f6682f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704653"
---
# <a name="query-definitions-differ-dialog-box-visual-database-tools"></a><span data-ttu-id="ccb11-102">查詢定義差異對話方塊 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ccb11-102">Query Definitions Differ Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="ccb11-103">這個對話方塊會通知您，無法在 [圖表] 和 [準則] 窗格中以圖形顯示查詢，而且您只能在 [SQL] 窗格中編輯查詢。</span><span class="sxs-lookup"><span data-stu-id="ccb11-103">This dialog box notifies you that your query cannot be represented graphically in the Diagram and Criteria panes, and that you can edit your query only in the SQL pane.</span></span>  
  
 <span data-ttu-id="ccb11-104">當您在 [SQL] 窗格中輸入或編輯 SQL 陳述式，然後移至另一個窗格、驗證查詢或嘗試執行查詢時，如果發生下列情況，此對話方塊便會出現：</span><span class="sxs-lookup"><span data-stu-id="ccb11-104">This dialog box may appear when you enter or edit an SQL statement in the SQL pane; you then move to another pane, verify the query, or attempt to execute the query; and one of the following conditions applies:</span></span>  
  
-   <span data-ttu-id="ccb11-105">SQL 陳述式不完整或是包含一或多個語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="ccb11-105">The SQL statement is incomplete or contains one or more syntax errors.</span></span>  
  
-   <span data-ttu-id="ccb11-106">SQL 陳述式有效，但是圖形窗格並不支援 (例如，聯合查詢)。</span><span class="sxs-lookup"><span data-stu-id="ccb11-106">The SQL statement is valid but is not supported in the graphical panes (for example, a Union query).</span></span>  
  
-   <span data-ttu-id="ccb11-107">SQL 陳述式有效，但包含所使用資料連接的特定語法。</span><span class="sxs-lookup"><span data-stu-id="ccb11-107">The SQL statement is valid but contains syntax specific to the data connection you are using.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="ccb11-108">您可以使用 [查詢]  工具列中的 [驗證 SQL 陳述式]  按鈕，檢查陳述式是否有效。</span><span class="sxs-lookup"><span data-stu-id="ccb11-108">You can check whether a statement is valid using the **Verify SQL Statement** button on the **Query** toolbar.</span></span>  
  
 <span data-ttu-id="ccb11-109">此對話方塊會顯示訊息，說明 SQL 陳述式無法顯示的原因，並詢問該如何繼續進行。</span><span class="sxs-lookup"><span data-stu-id="ccb11-109">The dialog box displays a message with the reason that the SQL statement cannot be represented, and then asks how you want to proceed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ccb11-110">如果您已經隱藏 [圖表] 和 [準則] 窗格，[查詢定義差異]  對話方塊就不會出現。</span><span class="sxs-lookup"><span data-stu-id="ccb11-110">The **Query Definitions Differ** dialog box does not appear if you have hidden the Diagram and Criteria panes.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ccb11-111">選項。</span><span class="sxs-lookup"><span data-stu-id="ccb11-111">Options</span></span>  
 <span data-ttu-id="ccb11-112">**忽略按鈕**</span><span class="sxs-lookup"><span data-stu-id="ccb11-112">**Ignore Button**</span></span>  
 <span data-ttu-id="ccb11-113">選擇此按鈕可指定要接受 SQL 陳述式，以繼續編輯或直接執行。</span><span class="sxs-lookup"><span data-stu-id="ccb11-113">Choose this button to specify that you want to accept the SQL statement, either to edit it further or to execute it.</span></span> <span data-ttu-id="ccb11-114">如果接受陳述式，[圖表] 和 [準則] 窗格將呈現暗灰色的 (Dimmed) 狀態，表示它們不會顯示 [SQL] 窗格中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="ccb11-114">If you accept the statement, the Diagram and Criteria panes appear dimmed to indicate that they do not represent the statement in the SQL pane.</span></span>  
  
 <span data-ttu-id="ccb11-115">**復原按鈕**</span><span class="sxs-lookup"><span data-stu-id="ccb11-115">**Undo Button**</span></span>  
 <span data-ttu-id="ccb11-116">選擇此按鈕可捨棄對 [SQL] 窗格所做的變更。</span><span class="sxs-lookup"><span data-stu-id="ccb11-116">Choose this button to discard your changes to the SQL pane.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ccb11-117">如果陳述式正確無誤，但是 [查詢和檢視設計師] 無法提供圖形方面的支援，這個陳述式還是可以執行，只是無法顯示在 [圖表] 和 [準則] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="ccb11-117">If the statement is correct but not supported graphically by the Query and View Designer, you can execute it even though it cannot be represented in the Diagram and Criteria panes.</span></span> <span data-ttu-id="ccb11-118">例如，如果您輸入聯合查詢 (Union Query)，陳述式可以執行，但不會顯示在其他窗格中。</span><span class="sxs-lookup"><span data-stu-id="ccb11-118">For example, if you enter a Union query, the statement can be executed but not represented in the other panes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb11-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccb11-119">See Also</span></span>  
 [<span data-ttu-id="ccb11-120">查詢和檢視表設計工具 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="ccb11-120">Query and View Designer Tools &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
