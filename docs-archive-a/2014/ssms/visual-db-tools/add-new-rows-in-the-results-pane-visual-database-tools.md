---
title: 在結果窗格中加入新的資料列 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- inserting rows
- Query Designer [SQL Server], Results pane
- Results pane
- adding rows
- row additions [SQL Server], Results pane
ms.assetid: 59891c84-3f54-4ab9-8b86-72c59627b480
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3137da106279e09305261c6c7cb7fd06d254b4fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593765"
---
# <a name="add-new-rows-in-the-results-pane-visual-database-tools"></a><span data-ttu-id="c0205-102">在結果窗格中加入新的資料列 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c0205-102">Add New Rows in the Results Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="c0205-103">您可以利用輸入或是從其他諸如「記事本」或 Excel 程式貼上的方式，加入新的資料。</span><span class="sxs-lookup"><span data-stu-id="c0205-103">You can add new data either by typing it in or by pasting it from another program such as Notepad or Excel.</span></span> <span data-ttu-id="c0205-104">要貼上資料列必須要有與貼入的資料表完全相同的資料行數目和類型。</span><span class="sxs-lookup"><span data-stu-id="c0205-104">A row to be pasted must have exactly the same number and types of columns as the table into which you are pasting.</span></span> <span data-ttu-id="c0205-105">多重資料列可一併貼上至 [結果] 窗格。</span><span class="sxs-lookup"><span data-stu-id="c0205-105">You can paste multiple rows into the Results pane at once.</span></span>  
  
 <span data-ttu-id="c0205-106">如需如何輸入資料的資訊，請參閱 [更新結果的規則 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="c0205-106">For information about how to enter data see [Rules for Updating Results &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
### <a name="to-add-a-new-data-row"></a><span data-ttu-id="c0205-107">若要加入新資料列</span><span class="sxs-lookup"><span data-stu-id="c0205-107">To add a new data row</span></span>  
  
1.  <span data-ttu-id="c0205-108">導覽至 [結果] 窗格下方，有空白資料列可加入新的資料列之處。</span><span class="sxs-lookup"><span data-stu-id="c0205-108">Navigate to the bottom of the Results pane, where a blank row is available for adding a new data row.</span></span>  
  
     <span data-ttu-id="c0205-109">所有資料行的初始值皆為 *NULL*。</span><span class="sxs-lookup"><span data-stu-id="c0205-109">The initial values for all columns will be *NULL*.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="c0205-110">若要直接移至第一個空白資料列，請使用位於 [結果] 窗格底部的導覽列。</span><span class="sxs-lookup"><span data-stu-id="c0205-110">To go directly to the first empty row use the navigation bar at the bottom of the Results pane.</span></span>  
  
2.  <span data-ttu-id="c0205-111">若要把剪貼簿中的資料列貼上，按一下新資料列左邊的按鈕，加以選取。</span><span class="sxs-lookup"><span data-stu-id="c0205-111">If you are pasting rows from the Clipboard, select the new row by clicking the button to its left.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c0205-112">如果所貼上的一或多個資料列無法為資料庫認可，您將會收到通知哪些資料列不被認可的訊息。</span><span class="sxs-lookup"><span data-stu-id="c0205-112">If one or more of the rows you're pasting can't be committed to the database you will receive a message telling you which row(s) couldn't be committed.</span></span>  
  
3.  <span data-ttu-id="c0205-113">輸入新資料列的資料。</span><span class="sxs-lookup"><span data-stu-id="c0205-113">Enter the data for the new row.</span></span> <span data-ttu-id="c0205-114">若要貼上，請從 [編輯] 功能表選擇 [貼上]。</span><span class="sxs-lookup"><span data-stu-id="c0205-114">If you are pasting, choose **Paste** from the **Edit** menu.</span></span>  
  
4.  <span data-ttu-id="c0205-115">離開該資料列，讓資料庫對其進行認可。</span><span class="sxs-lookup"><span data-stu-id="c0205-115">Leave that row to commit it to the database.</span></span>  
  
 <span data-ttu-id="c0205-116">儲存資料列時如果發生錯誤，查詢和檢視設計工具會顯示訊息，然後讓您返回先前所編輯的資料列。</span><span class="sxs-lookup"><span data-stu-id="c0205-116">If an error occurs when you save the row the Query and View Designer displays a message and then returns you to the row you were editing.</span></span> <span data-ttu-id="c0205-117">您可以：</span><span class="sxs-lookup"><span data-stu-id="c0205-117">You can then:</span></span>  
  
-   <span data-ttu-id="c0205-118">進一步編輯資料列來解決錯誤。</span><span class="sxs-lookup"><span data-stu-id="c0205-118">Resolve the error by making further edits in the row.</span></span>  
  
-   <span data-ttu-id="c0205-119">按一下 ESC 鍵來取消編輯。</span><span class="sxs-lookup"><span data-stu-id="c0205-119">Cancel the edit by pressing ESC.</span></span> <span data-ttu-id="c0205-120">如果是在變更過的資料格中按 ESC 鍵，那麼該資料格中的變更會取消。</span><span class="sxs-lookup"><span data-stu-id="c0205-120">If you press ESC while in a cell that you changed, the changes for that cell are canceled.</span></span> <span data-ttu-id="c0205-121">如果在沒有變更的資料格中按 ESC 鍵，整個資料列的變更都會取消。</span><span class="sxs-lookup"><span data-stu-id="c0205-121">If you press ESC while in a cell you have not changed, the changes for the entire row are canceled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0205-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0205-122">See Also</span></span>  
 <span data-ttu-id="c0205-123">[使用 [結果] 窗格中的資料 &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="c0205-123">[Work with Data in the Results Pane &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="c0205-124">使用查詢執行基本作業 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="c0205-124">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
