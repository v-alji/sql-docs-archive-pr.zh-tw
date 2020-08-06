---
title: 查看和解決合併式發行集的資料衝突 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], viewing conflicts
- viewing conflict information
- conflict resolution [SQL Server replication], merge replication
ms.assetid: aeee9546-4480-49f9-8b1e-c71da1f056c7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 77aa9ece0073149c017f6eca35a756b22751a74b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594475"
---
# <a name="view-and-resolve-data-conflicts-for-merge-publications-sql-server-management-studio"></a><span data-ttu-id="64452-102">檢視並解決合併式發行集的資料衝突 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="64452-102">View and Resolve Data Conflicts for Merge Publications (SQL Server Management Studio)</span></span>
  <span data-ttu-id="64452-103">合併式複寫中的衝突根據為每個發行項指定的解決器進行解決。</span><span class="sxs-lookup"><span data-stu-id="64452-103">Conflicts in merge replication are resolved based on the resolver specified for each article.</span></span> <span data-ttu-id="64452-104">依預設，衝突的解決不需要使用者的介入。</span><span class="sxs-lookup"><span data-stu-id="64452-104">By default, conflicts are resolved without the need for user intervention.</span></span> <span data-ttu-id="64452-105">但是可以在「 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 複寫衝突檢視器」(Replication Conflict Viewer) 中檢視衝突並變更解決的結果。</span><span class="sxs-lookup"><span data-stu-id="64452-105">But conflicts can be viewed, and the outcome of the resolution can be changed, in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Replication Conflict Viewer.</span></span>  
  
 <span data-ttu-id="64452-106">複寫衝突檢視器可以在衝突保留期限指定的時間內使用衝突資料 (預設為 14 天)。</span><span class="sxs-lookup"><span data-stu-id="64452-106">Conflict data is available in the Replication Conflict Viewer for the amount of time specified for the conflict retention period (with a default of 14 days).</span></span> <span data-ttu-id="64452-107">若要設定衝突保留期限，可以：</span><span class="sxs-lookup"><span data-stu-id="64452-107">To set the conflict retention period, either:</span></span>  
  
-   <span data-ttu-id="64452-108">為 **@conflict_retention** [Sp_addmergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)的參數指定保留值。</span><span class="sxs-lookup"><span data-stu-id="64452-108">Specify a retention value for the **@conflict_retention** parameter of [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span>  
  
-   <span data-ttu-id="64452-109">為參數指定**conflict_retention**的值 **@property** ，並為 **@value** [sp_changemergepublication &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)指定保留值。</span><span class="sxs-lookup"><span data-stu-id="64452-109">Specify a value of **conflict_retention** for the **@property** parameter and a retention value for the **@value** parameter of [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span>  
  
 <span data-ttu-id="64452-110">依預設，會儲存衝突資訊：</span><span class="sxs-lookup"><span data-stu-id="64452-110">By default, conflict information is stored:</span></span>  
  
-   <span data-ttu-id="64452-111">如果發行集相容性層級為 90RTM 或更高，則是在「發行者」與「訂閱者」端。</span><span class="sxs-lookup"><span data-stu-id="64452-111">At the Publisher and Subscriber if the publication compatibility level is 90RTM or higher.</span></span>  
  
-   <span data-ttu-id="64452-112">如果發行集相容性層級低於 80RTM，則是在發行者端。</span><span class="sxs-lookup"><span data-stu-id="64452-112">At the Publisher if the publication compatibility level is lower than 80RTM.</span></span>  
  
-   <span data-ttu-id="64452-113">如果「訂閱者」執行 [!INCLUDE[ssEW](../../includes/ssew-md.md)]，則會儲存在「發行者」端。</span><span class="sxs-lookup"><span data-stu-id="64452-113">At the Publisher if Subscribers are running [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> <span data-ttu-id="64452-114">衝突資料無法儲存在 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 訂閱者上。</span><span class="sxs-lookup"><span data-stu-id="64452-114">Conflict data cannot be stored on [!INCLUDE[ssEW](../../includes/ssew-md.md)] Subscribers.</span></span>  
  
 <span data-ttu-id="64452-115">衝突資訊的儲存由 **conflict_logging** 發行集屬性控制。</span><span class="sxs-lookup"><span data-stu-id="64452-115">Storage of conflict information is controlled by the **conflict_logging** publication property.</span></span> <span data-ttu-id="64452-116">如需詳細資訊，請參閱 [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql) 和 [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="64452-116">For more information, see [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql) and [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span>  
  
 <span data-ttu-id="64452-117">衝突也可以使用「 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 互動式解決器」在同步處理期間以互動的方式解決。</span><span class="sxs-lookup"><span data-stu-id="64452-117">Conflicts can also be resolved interactively during synchronization using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Interactive Resolver.</span></span> <span data-ttu-id="64452-118">互動解決器可以從 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Synchronization Manager 使用。</span><span class="sxs-lookup"><span data-stu-id="64452-118">The Interactive Resolver is available through the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Synchronization Manager.</span></span> <span data-ttu-id="64452-119">如需詳細資訊，請參閱[使用 Windows Synchronization Manager 同步處理訂閱 &#40;Windows Synchronization Manager&#41;](synchronize-a-subscription-using-windows-synchronization-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="64452-119">For more information, see [Synchronize a Subscription Using Windows Synchronization Manager &#40;Windows Synchronization Manager&#41;](synchronize-a-subscription-using-windows-synchronization-manager.md).</span></span>  
  
### <a name="to-view-and-resolve-conflicts-for-merge-publications"></a><span data-ttu-id="64452-120">若要檢視並解決合併式發行集衝突</span><span class="sxs-lookup"><span data-stu-id="64452-120">To view and resolve conflicts for merge publications</span></span>  
  
1.  <span data-ttu-id="64452-121">如果中有適當的) ，請連接到發行者 (或訂閱者 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="64452-121">Connect to the Publisher (or Subscriber if appropriate) in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="64452-122">展開 **[複寫]** 資料夾，然後展開 **[本機發行集]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="64452-122">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="64452-123">以滑鼠右鍵按一下您要檢視衝突的發行集，然後按一下 **[檢視衝突]** 。</span><span class="sxs-lookup"><span data-stu-id="64452-123">Right-click the publication for which you want to view conflicts, and then click **View Conflicts**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="64452-124">如果將 **conflict_logging** 屬性的值指定為 **'subscriber'** ，就無法使用 **[檢視衝突]** 功能表選項。</span><span class="sxs-lookup"><span data-stu-id="64452-124">If you specified a value of **'subscriber'** for the **conflict_logging** property, the **View Conflicts** menu option is not available.</span></span> <span data-ttu-id="64452-125">若要檢視衝突，請從命令提示字元啟動 ConflictViewer.exe。</span><span class="sxs-lookup"><span data-stu-id="64452-125">To view conflicts, start ConflictViewer.exe from the command prompt.</span></span> <span data-ttu-id="64452-126">依預設，ConflictViewer.exe 位於下列目錄：Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE。</span><span class="sxs-lookup"><span data-stu-id="64452-126">By default, ConflictViewer.exe is located in the following directory: Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE.</span></span> <span data-ttu-id="64452-127">如需有效的啟動參數清單，請執行 ConflictViewer.exe -?。</span><span class="sxs-lookup"><span data-stu-id="64452-127">For a list of valid startup parameters, run ConflictViewer.exe -?.</span></span>  
  
4.  <span data-ttu-id="64452-128">在 **[選取衝突資料表]** 對話方塊中，選取要檢視衝突的資料庫、發行集和資料表。</span><span class="sxs-lookup"><span data-stu-id="64452-128">In the **Select Conflict Table** dialog box, select a database, publication, and table for which to view conflicts.</span></span>  
  
5.  <span data-ttu-id="64452-129">在複寫衝突檢視器中，您可以：</span><span class="sxs-lookup"><span data-stu-id="64452-129">In the Replication Conflict Viewer, you can:</span></span>  
  
    -   <span data-ttu-id="64452-130">使用上方格右側按鈕篩選資料列。</span><span class="sxs-lookup"><span data-stu-id="64452-130">Filter rows with the buttons to the right of the upper grid.</span></span>  
  
    -   <span data-ttu-id="64452-131">在上方格內選取資料列，以便於下方格的該資料列顯示資訊。</span><span class="sxs-lookup"><span data-stu-id="64452-131">Select a row in the upper grid to display information on that row in the lower grid.</span></span>  
  
    -   <span data-ttu-id="64452-132">在上方方格中選取一個或多個資料列，然後按一下 **[移除]**，這相當於按一下 **[提交成功者]** 按鈕 (不會對資料進行任何變更)。</span><span class="sxs-lookup"><span data-stu-id="64452-132">Select one or more rows in the upper grid, and then click **Remove**, which is equivalent to clicking the **Submit Winner** button (without making any changes to the data).</span></span>  
  
    -   <span data-ttu-id="64452-133">按一下 [屬性] 按鈕 (**...** ]) 以查看涉及衝突之資料行的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="64452-133">Click the properties button (**...**) to view more information on a column involved in a conflict.</span></span>  
  
    -   <span data-ttu-id="64452-134">在提交資料之前，編輯 **[衝突成功者]** 或 **[衝突失敗者]** 資料行中的資料 (灰色資料行表示資料為唯讀)。</span><span class="sxs-lookup"><span data-stu-id="64452-134">Edit data in the **Conflict winner** or **Conflict loser** column before submitting the data (data is read-only if the column is gray).</span></span>  
  
    -   <span data-ttu-id="64452-135">按一下 **[提交成功者]** 以接受指定為衝突成功者的資料列。</span><span class="sxs-lookup"><span data-stu-id="64452-135">Click **Submit Winner** to accept the row designated as the winner of the conflict.</span></span>  
  
    -   <span data-ttu-id="64452-136">按一下 **[提交失敗者]** ，以覆寫解決並將指定為衝突失敗者的值傳播到拓撲中的所有節點。</span><span class="sxs-lookup"><span data-stu-id="64452-136">Click **Submit Loser** to override the resolution and to propagate the value designated as the loser of the conflict to all nodes in the topology.</span></span>  
  
    -   <span data-ttu-id="64452-137">選取 **[記錄此衝突的詳細資料]** 即可將衝突資料記錄到檔案中。</span><span class="sxs-lookup"><span data-stu-id="64452-137">Select **Log the details of this conflict** to log conflict data to a file.</span></span> <span data-ttu-id="64452-138">若要指定檔案的位置，請指向 **[檢視]** 功能表，然後按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="64452-138">To specify a location for the file, point to the **View** menu, and then click **Options**.</span></span> <span data-ttu-id="64452-139">輸入值，或按一下瀏覽按鈕 ( **[...]** )，然後導覽至適當的檔案。</span><span class="sxs-lookup"><span data-stu-id="64452-139">Enter a value, or click the browse button (**...**), and then navigate to the appropriate file.</span></span> <span data-ttu-id="64452-140">按一下 **[確定]** 即可結束 **[選項]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="64452-140">Click **OK** to exit the **Options** dialog box.</span></span>  
  
6.  <span data-ttu-id="64452-141">關閉複寫衝突檢視器。</span><span class="sxs-lookup"><span data-stu-id="64452-141">Close the Replication Conflict Viewer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64452-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64452-142">See Also</span></span>  
 <span data-ttu-id="64452-143">[進階合併式複寫衝突偵測與解決](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="64452-143">[Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="64452-144">指定合併發行項解析程式</span><span class="sxs-lookup"><span data-stu-id="64452-144">Specify a Merge Article Resolver</span></span>](publish/specify-a-merge-article-resolver.md)  
  
  
