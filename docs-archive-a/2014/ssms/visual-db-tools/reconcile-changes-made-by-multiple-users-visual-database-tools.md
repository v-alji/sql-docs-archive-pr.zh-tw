---
title: 協調多位使用者所做的變更 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- table modifications [SQL Server], multiple users
- reconciling changes made by multiple users
- modifications made by multiple users
ms.assetid: fc7ed4f2-ad3d-47fc-a3ef-51e5bb069ef0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 337d505fce474a33301c18313fe6137f6bc0ec1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688374"
---
# <a name="reconcile-changes-made-by-multiple-users-visual-database-tools"></a><span data-ttu-id="18dc5-102">協調多位使用者所做的變更 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="18dc5-102">Reconcile Changes Made by Multiple Users (Visual Database Tools)</span></span>
  <span data-ttu-id="18dc5-103">在多位使用者環境中，可以同時讓多位使用者修改相同的物件。</span><span class="sxs-lookup"><span data-stu-id="18dc5-103">In a multiuser environment, changes can be made on the same object by multiple users at once.</span></span> <span data-ttu-id="18dc5-104">這樣的情況會發生在當您使用資料表或資料庫圖表設計工具設計物件的結構時，或是發生在 [查詢和檢視設計師] 的 [結果] 窗格中的值。</span><span class="sxs-lookup"><span data-stu-id="18dc5-104">This can happen when you're working on the structure of the object in the Table or Database Diagram designers or it can happen to values in the results returned in the Query and View designer's Results pane.</span></span> <span data-ttu-id="18dc5-105">這樣會產生您需要解決的衝突。</span><span class="sxs-lookup"><span data-stu-id="18dc5-105">This can cause conflicts that you'll want to resolve.</span></span>  
  
## <a name="conflicts-in-the-table-or-database-diagram-designers"></a><span data-ttu-id="18dc5-106">在資料表或資料庫圖表設計工具中的衝突</span><span class="sxs-lookup"><span data-stu-id="18dc5-106">Conflicts in the Table or Database Diagram Designers</span></span>  
 <span data-ttu-id="18dc5-107">例如，另外一位使用者可能會刪除或重新命名您正在 [資料表設計工具] 中使用的相同或相關資料表。</span><span class="sxs-lookup"><span data-stu-id="18dc5-107">For example, another user might delete or rename a table while you are working with the same or a related table in Table Designer.</span></span> <span data-ttu-id="18dc5-108">當您嘗試儲存資料表時， [偵測到資料庫變更對話方塊 &#40;Visual Database Tools&#41;](visual-database-tools.md) 會通知您資料庫已經在您開啟資料表之後經過更新。</span><span class="sxs-lookup"><span data-stu-id="18dc5-108">When you attempt to save your table, the [Database Changes Detected Dialog Box &#40;Visual Database Tools&#41;](visual-database-tools.md) notifies you that the database has been updated since you opened the table.</span></span>  
  
 <span data-ttu-id="18dc5-109">這個對話方塊將同時顯示資料庫物件清單，其中包含儲存資料表時將會受到影響的所有物件。</span><span class="sxs-lookup"><span data-stu-id="18dc5-109">This dialog box also displays a list of database objects that will be affected as a result of saving your table.</span></span> <span data-ttu-id="18dc5-110">這個時候您可以採取下列行動：</span><span class="sxs-lookup"><span data-stu-id="18dc5-110">At this point, you can take one of these actions:</span></span>  
  
-   <span data-ttu-id="18dc5-111">選擇 [是]  可儲存資料表，並且可使用清單中的所有變更更新資料庫。</span><span class="sxs-lookup"><span data-stu-id="18dc5-111">Choose **Yes** to save your table and update the database with all the changes in the list.</span></span>  
  
     <span data-ttu-id="18dc5-112">這個動作會影響共用相同資料庫物件的資料表。</span><span class="sxs-lookup"><span data-stu-id="18dc5-112">This action could affect tables that share the same database objects.</span></span> <span data-ttu-id="18dc5-113">例如，假設您編輯 `au`資料表`id` _ `titleauthors` 資料行，而另一位使用者正在使用與 `authors` 資料表 `titleauthors` 資料行相關的 `au`\_`id` 資料表。</span><span class="sxs-lookup"><span data-stu-id="18dc5-113">For example, suppose you edit the `au`_`id` column in the `titleauthors` table while another user is working on the `authors` table which is related to the `titleauthors` table by the `au`\_`id` column.</span></span> <span data-ttu-id="18dc5-114">如果您儲存您的資料表將會影響其他使用者的資料表。</span><span class="sxs-lookup"><span data-stu-id="18dc5-114">Saving your table will affect the other user's table.</span></span> <span data-ttu-id="18dc5-115">同樣的，假設其他使用者在 `qty` 資料表中定義了一個 `sales` 資料行的檢查條件約束。</span><span class="sxs-lookup"><span data-stu-id="18dc5-115">Similarly, suppose that another user defined a check constraint for the `qty` column in the `sales` table.</span></span> <span data-ttu-id="18dc5-116">如果您刪除 `qty` 資料行並儲存 `sales` 資料表，則會影響其他使用者的檢查條件約束。</span><span class="sxs-lookup"><span data-stu-id="18dc5-116">If you delete the `qty` column and save the `sales` table, the other user's check constraint will be affected.</span></span>  
  
-   <span data-ttu-id="18dc5-117">選擇 [否]  會取消儲存動作。</span><span class="sxs-lookup"><span data-stu-id="18dc5-117">Choose **No** to cancel the save action.</span></span>  
  
     <span data-ttu-id="18dc5-118">您可關閉資料表而不加以儲存。</span><span class="sxs-lookup"><span data-stu-id="18dc5-118">You can then close the table without saving it.</span></span> <span data-ttu-id="18dc5-119">當您重新開啟資料表，會與在資料庫中的相符。</span><span class="sxs-lookup"><span data-stu-id="18dc5-119">When you reopen the table it will match what is in the database.</span></span>  
  
-   <span data-ttu-id="18dc5-120">選擇 [儲存為文字檔]  可儲存變更清單。</span><span class="sxs-lookup"><span data-stu-id="18dc5-120">Choose **Save Text File** to save a list of the changes.</span></span>  
  
     <span data-ttu-id="18dc5-121">您可以將 [偵測到資料庫變更]  對話方塊中所示的資料庫變更清單儲存為文字檔，以便您了解其他使用者變更的原因。</span><span class="sxs-lookup"><span data-stu-id="18dc5-121">You can save the list of database changes shown in the **Database Changes Detected** dialog box to a text file so that you can investigate the cause of other users' changes.</span></span> <span data-ttu-id="18dc5-122">例如，如果其他使用者編輯您標示為刪除的資料表，您可能想要研究是否應在更新資料庫之前刪除該資料表。</span><span class="sxs-lookup"><span data-stu-id="18dc5-122">For example, if another user edited a table that you marked for deletion, you may want to research whether the table should be deleted before updating the database.</span></span>  
  
## <a name="conflicts-in-the-query-and-view-designer"></a><span data-ttu-id="18dc5-123">在 [查詢和檢視設計師] 中的衝突</span><span class="sxs-lookup"><span data-stu-id="18dc5-123">Conflicts in the Query and View Designer</span></span>  
 <span data-ttu-id="18dc5-124">如果您執行查詢或傳回檢視的結果，資料會顯示在 [結果窗格](results-pane-visual-database-tools.md)中。</span><span class="sxs-lookup"><span data-stu-id="18dc5-124">If you run a query or return the results of a view, the data is shown in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="18dc5-125">多位使用者可以在同時使用相同的資料集，但這樣可能會產生衝突。</span><span class="sxs-lookup"><span data-stu-id="18dc5-125">Multiple users can work on the same set of data at the same time, which can cause conflicts.</span></span>  
  
 <span data-ttu-id="18dc5-126">例如，假設您和您的同事分別執行一個查詢，以顯示 `titleauthors` 資料表的所有資料。</span><span class="sxs-lookup"><span data-stu-id="18dc5-126">For example, lets say you and a colleague each run a query to show all the data in the `titleauthors` table.</span></span> <span data-ttu-id="18dc5-127">您的同事將所回傳的第一筆記錄中的名字 Barb 變更為 Barbara。</span><span class="sxs-lookup"><span data-stu-id="18dc5-127">Your colleague changes the first name in the first record returned from Barb to Barbara.</span></span> <span data-ttu-id="18dc5-128">在這個時候資料庫中這個資料欄位已經是 Barbara，但您的結果集還是顯示 Barb。</span><span class="sxs-lookup"><span data-stu-id="18dc5-128">At this point the database has Barbara in that field, while your result set still shows Barb.</span></span> <span data-ttu-id="18dc5-129">現在您輸入 Barbara 然後按下該資料列。</span><span class="sxs-lookup"><span data-stu-id="18dc5-129">Now you type in Barbara and click off of the row.</span></span> <span data-ttu-id="18dc5-130">您會收到詢問您要如何解決衝突的訊息。</span><span class="sxs-lookup"><span data-stu-id="18dc5-130">You will receive a message asking you how you want to resolve the conflict.</span></span>  
  
-   <span data-ttu-id="18dc5-131">按一下 [是]  可使用您的變更更新資料庫。</span><span class="sxs-lookup"><span data-stu-id="18dc5-131">Click **Yes** to update the database with your changes.</span></span>  
  
     <span data-ttu-id="18dc5-132">這會覆寫您同事的變更。</span><span class="sxs-lookup"><span data-stu-id="18dc5-132">This will override your colleague's changes.</span></span>  
  
-   <span data-ttu-id="18dc5-133">按一下 [否]  可以將您的結果集更新為資料庫中目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="18dc5-133">Click **No** to have your result set updated to what's currently in the database.</span></span>  
  
     <span data-ttu-id="18dc5-134">這會使用您同事的變更覆寫您的變更。</span><span class="sxs-lookup"><span data-stu-id="18dc5-134">This will override your changes with those of your colleague's.</span></span>  
  
-   <span data-ttu-id="18dc5-135">按一下 [取消]  可繼續編輯，而不會解決衝突。</span><span class="sxs-lookup"><span data-stu-id="18dc5-135">Click **Cancel** to continue to edit without resolving the conflict.</span></span>  
  
     <span data-ttu-id="18dc5-136">在這種狀況下，您無法變更資料庫。</span><span class="sxs-lookup"><span data-stu-id="18dc5-136">In this case you will not be able to commit your changes to the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18dc5-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18dc5-137">See Also</span></span>  
 [<span data-ttu-id="18dc5-138">偵測到資料庫變更對話方塊 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="18dc5-138">Database Changes Detected Dialog Box &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
