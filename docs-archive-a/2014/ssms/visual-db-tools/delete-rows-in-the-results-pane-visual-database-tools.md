---
title: 刪除結果窗格中的資料列 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- removing rows
- row removal [SQL Server], Visual Database Tools Results pane
- row deletions [SQL Server], Visual Database Tools Results pane
- Query Designer [SQL Server], Results pane
- deleting rows
- Results pane
ms.assetid: a1147905-fe4a-4fac-b576-a17622477e66
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1a82a7232559cd8761ae3af66a9accc0bc307552
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593753"
---
# <a name="delete-rows-in-the-results-pane-visual-database-tools"></a><span data-ttu-id="71d4d-102">刪除結果窗格中的資料列 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="71d4d-102">Delete Rows in the Results Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="71d4d-103">若要刪除資料庫中的資料錄，請刪除 [結果] 窗格中的資料列。</span><span class="sxs-lookup"><span data-stu-id="71d4d-103">Delete rows in the Results pane if you want to delete records in the database.</span></span> <span data-ttu-id="71d4d-104">若要刪除所有的資料列，請使用刪除查詢。</span><span class="sxs-lookup"><span data-stu-id="71d4d-104">If you want to delete all of the rows you can use a Delete query.</span></span> <span data-ttu-id="71d4d-105">如需詳細資訊，請參閱 [建立製成資料表查詢 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="71d4d-105">For more information see [Create Delete Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span> <span data-ttu-id="71d4d-106">如果只是要從 [結果] 窗格移除資料列，請變更查詢的準則。</span><span class="sxs-lookup"><span data-stu-id="71d4d-106">If you only want to remove rows from the Results pane, change the criteria for the query.</span></span> <span data-ttu-id="71d4d-107">如需詳細資訊，請參閱 [指定搜尋準則 &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="71d4d-107">For more information see [Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md).</span></span>  
  
### <a name="to-delete-a-row-or-rows"></a><span data-ttu-id="71d4d-108">若要刪除資料列</span><span class="sxs-lookup"><span data-stu-id="71d4d-108">To delete a row or rows</span></span>  
  
1.  <span data-ttu-id="71d4d-109">在 [結果] 窗格中，選取要刪除的資料列左邊的方塊。</span><span class="sxs-lookup"><span data-stu-id="71d4d-109">Select the box to the left of the row or rows you want to delete in the Results pane.</span></span>  
  
2.  <span data-ttu-id="71d4d-110">按下 DELETE 鍵。</span><span class="sxs-lookup"><span data-stu-id="71d4d-110">Press DELETE.</span></span>  
  
3.  <span data-ttu-id="71d4d-111">在詢問確認的訊息方塊中，按一下 [是]  。</span><span class="sxs-lookup"><span data-stu-id="71d4d-111">In the message box asking for confirmation, click **Yes**.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="71d4d-112">用這種方式刪除的資料列，會永久自資料庫移除，無法重新叫用。</span><span class="sxs-lookup"><span data-stu-id="71d4d-112">Rows you delete in this way are permanently removed from the database and cannot be recalled.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71d4d-113">如果選取的資料列中有任何一個無法從資料庫刪除，所有的資料列將都不會刪除，而且您會接收到通知哪個資料列無法刪除的訊息。</span><span class="sxs-lookup"><span data-stu-id="71d4d-113">If any of the selected rows can't be deleted from the database, none of them will be deleted and you will receive a message telling you which rows can't be deleted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71d4d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71d4d-114">See Also</span></span>  
 <span data-ttu-id="71d4d-115">[&#40;Visual Database Tools 建立刪除查詢&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="71d4d-115">[Create Delete Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="71d4d-116">指定搜尋準則 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="71d4d-116">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
