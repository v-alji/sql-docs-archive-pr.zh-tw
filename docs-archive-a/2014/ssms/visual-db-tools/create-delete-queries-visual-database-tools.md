---
title: 建立刪除查詢 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- row removal [SQL Server], Delete query
- Delete query
- queries [SQL Server], types
- removing rows
- removing data
- data deletions [SQL Server]
- deleting rows
- deleting data
ms.assetid: 0db3af43-1ec4-48c8-b769-2bb9c76d3434
author: stevestein
ms.author: sstein
ms.openlocfilehash: a76c3aaef623365e419f40f3058308f6217d75d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606530"
---
# <a name="create-delete-queries-visual-database-tools"></a><span data-ttu-id="d6eba-102">建立刪除查詢 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d6eba-102">Create Delete Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="d6eba-103">您可以使用刪除查詢 (Delete Query) 刪除資料表中的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="d6eba-103">You can delete all rows in a table by using a Delete query.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d6eba-104">從資料表中刪除所有資料列可清除資料表中的資料，但不會刪除資料表本身。</span><span class="sxs-lookup"><span data-stu-id="d6eba-104">Deleting all rows from a table clears the data in the table but does not delete the table itself.</span></span> <span data-ttu-id="d6eba-105">若要將資料表從資料庫中刪除，請在物件總管的資料表上按一下滑鼠右鍵，並且按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="d6eba-105">To delete a table from a database, right-click the table in Object Explorer and click **Delete**.</span></span>  
  
 <span data-ttu-id="d6eba-106">建立刪除查詢時，[準則] 窗格將會變更，以反映可以用來刪除資料列的選項。</span><span class="sxs-lookup"><span data-stu-id="d6eba-106">When you create a Delete query, the Criteria pane changes to reflect the options available for deleting rows.</span></span> <span data-ttu-id="d6eba-107">由於您不會在刪除查詢中顯示資料，因此 [輸出]、[排序依據] 和 [排序次序] 等資料行都會移除。</span><span class="sxs-lookup"><span data-stu-id="d6eba-107">Because you do not display data in a Delete query, the Output, Sort By, and Sort Order columns are removed.</span></span> <span data-ttu-id="d6eba-108">此外，在表示資料表或資料表值物件的矩形中，資料行名稱旁邊的核取方塊也會移除，因為您無法個別指定要刪除的資料行。</span><span class="sxs-lookup"><span data-stu-id="d6eba-108">In addition, the check boxes next to the column names in the rectangle representing the table or table-valued object are removed because you cannot specify individual columns to delete.</span></span>  
  
 <span data-ttu-id="d6eba-109">如果 [查詢和檢視設計師] 無法刪除一個或多個資料列，它便不會刪除任何資料列，您會收到訊息說明哪些資料列包含無法從資料庫刪除的資訊。</span><span class="sxs-lookup"><span data-stu-id="d6eba-109">If the Query and View Designer can't delete one or more of the rows none of them will be deleted and you will receive a message telling you which row(s) contain information that can't be deleted from the database.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="d6eba-110">您無法恢復執行刪除查詢的動作。</span><span class="sxs-lookup"><span data-stu-id="d6eba-110">You cannot undo the action of executing a Delete query.</span></span> <span data-ttu-id="d6eba-111">為求安全起見，在執行刪除查詢之前，請先備份資料。</span><span class="sxs-lookup"><span data-stu-id="d6eba-111">As a precaution, back up your data before executing a Delete query.</span></span>  
  
### <a name="to-create-a-delete-query"></a><span data-ttu-id="d6eba-112">若要建立刪除查詢</span><span class="sxs-lookup"><span data-stu-id="d6eba-112">To create a Delete query</span></span>  
  
1.  <span data-ttu-id="d6eba-113">將要刪除資料列的來源資料表加入至 [圖表] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="d6eba-113">Add the table to delete rows from to the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="d6eba-114">從 [查詢設計工具]  功能表中，指向 [變更類型]  ，然後按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="d6eba-114">From the **Query Designer** menu, point to **Change Type**, and then click **Delete**.</span></span> <span data-ttu-id="d6eba-115">**注意**：在啟動刪除查詢時，如果 [圖表] 窗格中顯示一個以上的資料表，查詢和檢視設計師就會顯示[刪除資料表對話方塊](visual-database-tools.md)，提示您輸入要刪除資料列的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="d6eba-115">**Note** If more than one table is displayed in the Diagram pane when you start the Delete query, the Query and View Designer displays the [Delete Table Dialog Box](visual-database-tools.md) to prompt you for the name of the table to delete rows from.</span></span>  
  
 <span data-ttu-id="d6eba-116">執行刪除查詢時， [結果窗格](results-pane-visual-database-tools.md)不會報告任何結果。</span><span class="sxs-lookup"><span data-stu-id="d6eba-116">When you execute the Delete query, no results are reported in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="d6eba-117">但是畫面會出現訊息，指出已經刪除的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="d6eba-117">Instead, a message appears indicating how many rows were deleted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6eba-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6eba-118">See Also</span></span>  
 <span data-ttu-id="d6eba-119">[支援的查詢類型 &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d6eba-119">[Supported Query Types &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="d6eba-120">設計查詢和檢視使用說明主題 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="d6eba-120">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
