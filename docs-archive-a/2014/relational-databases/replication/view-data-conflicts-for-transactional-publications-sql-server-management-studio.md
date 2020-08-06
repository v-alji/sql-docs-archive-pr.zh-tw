---
title: 查看交易式發行集 (SQL Server Management Studio) 的資料衝突 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- conflict resolution [SQL Server replication], queued updating subscriptions
- queued updating subscriptions [SQL Server replication]
- viewing conflict information
ms.assetid: 9977dd75-b0de-4376-9c13-86d80567d8aa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 228753c113bcf43ed276d989a3996e9bf23bfc16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598812"
---
# <a name="view-data-conflicts-for-transactional-publications-sql-server-management-studio"></a><span data-ttu-id="979f7-102">檢視交易式發行集的資料衝突 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="979f7-102">View Data Conflicts for Transactional Publications (SQL Server Management Studio)</span></span>
  <span data-ttu-id="979f7-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 複寫衝突檢視器可讓您檢視點對點異動複寫和具有佇列更新訂閱之異動複寫的衝突。</span><span class="sxs-lookup"><span data-stu-id="979f7-103">You can view conflicts for peer-to-peer transactional replication and transactional replication with queued updating subscriptions in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Replication Conflict Viewer.</span></span> <span data-ttu-id="979f7-104">如需如何偵測和解決衝突的資訊，請參閱[點對點複寫中的衝突偵測](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)和[設定佇列更新衝突解決選項 &#40;SQL Server Management Studio&#41;](publish/create-an-updatable-subscription-to-a-transactional-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="979f7-104">For information about how conflicts are detected and resolved, see [Conflict Detection in Peer-to-Peer Replication](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md) and [Set Queued Updating Conflict Resolution Options &#40;SQL Server Management Studio&#41;](publish/create-an-updatable-subscription-to-a-transactional-publication.md).</span></span>  
  
 <span data-ttu-id="979f7-105">衝突資料的可用性會取決於複寫的類型和衝突保留期限而定：</span><span class="sxs-lookup"><span data-stu-id="979f7-105">The availability of conflict data depends on the type of replication and the conflict retention period:</span></span>  
  
-   <span data-ttu-id="979f7-106">如果是點對點複寫，則在預設情況下，當散發代理程式偵測到衝突時，就會發生失敗。</span><span class="sxs-lookup"><span data-stu-id="979f7-106">For peer-to-peer replication, by default, the Distribution Agent fails when it detects a conflict.</span></span> <span data-ttu-id="979f7-107">衝突錯誤會記錄到錯誤記錄檔中，但是不會將任何衝突資料記錄到衝突資料表中；因此，此資料表無法供人檢視。</span><span class="sxs-lookup"><span data-stu-id="979f7-107">A conflict error is logged into the error log, but no conflict data is logged into the conflict table; therefore it is not available for viewing.</span></span> <span data-ttu-id="979f7-108">如果允許散發代理程式繼續進行，會將衝突記錄在本機中偵測到衝突的每一個節點上。</span><span class="sxs-lookup"><span data-stu-id="979f7-108">If the Distribution Agent is allowed to continue, a conflict is logged locally on each node where it was detected.</span></span> <span data-ttu-id="979f7-109">如需詳細資訊，請參閱＜ [Conflict Detection in Peer-to-Peer Replication](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)＞中的「處理衝突」。</span><span class="sxs-lookup"><span data-stu-id="979f7-109">For more information, see "Handling Conflicts" in [Conflict Detection in Peer-to-Peer Replication](transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).</span></span>  
  
-   <span data-ttu-id="979f7-110">如果是佇列更新訂閱，則會針對每一個衝突提供資料。</span><span class="sxs-lookup"><span data-stu-id="979f7-110">For queued updating subscriptions, data is available for every conflict.</span></span> <span data-ttu-id="979f7-111">複寫衝突檢視器可以在衝突保留期限指定的時間內使用衝突資料 (預設為 14 天)。</span><span class="sxs-lookup"><span data-stu-id="979f7-111">Conflict data is available in the Replication Conflict Viewer for the amount of time specified for the conflict retention period, with a default of 14 days.</span></span> <span data-ttu-id="979f7-112">若要設定衝突保留期限，您可以執行以下其中一項作業：</span><span class="sxs-lookup"><span data-stu-id="979f7-112">To set the conflict retention period, perform either of the following:</span></span>  
  
    -   <span data-ttu-id="979f7-113">針對 [**sp_addpublication**](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) 的 `@conflict_retention` 參數指定保留值。</span><span class="sxs-lookup"><span data-stu-id="979f7-113">Specify a retention value for the @conflict_retention parameter of [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql).</span></span>  
  
    -   <span data-ttu-id="979f7-114">針對參數指定的值 `'conflict_retention'` @property ，並為 sp_changepublication 的參數指定保留值 @value 。 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="979f7-114">Specify a value of `'conflict_retention'` for the @property parameter and a retention value for the @value parameter of [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql).</span></span>  
  
### <a name="to-view-conflicts"></a><span data-ttu-id="979f7-115">若要檢視衝突</span><span class="sxs-lookup"><span data-stu-id="979f7-115">To view conflicts</span></span>  
  
1.  <span data-ttu-id="979f7-116">連接到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的適當伺服器，然後展開伺服器節點：</span><span class="sxs-lookup"><span data-stu-id="979f7-116">Connect to the appropriate server in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node:</span></span>  
  
    -   <span data-ttu-id="979f7-117">如果是點對點複寫，這會是發生衝突的節點。</span><span class="sxs-lookup"><span data-stu-id="979f7-117">For peer-to-peer replication, this is the node at which the conflict occurred.</span></span>  
  
    -   <span data-ttu-id="979f7-118">如果是佇列更新訂閱，這會是發行者。</span><span class="sxs-lookup"><span data-stu-id="979f7-118">For queued updating subscriptions, this is the Publisher.</span></span>  
  
2.  <span data-ttu-id="979f7-119">展開 **[複寫]** 資料夾，然後展開 **[本機發行集]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="979f7-119">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="979f7-120">以滑鼠右鍵按一下您要檢視衝突的發行集，然後按一下 **[檢視衝突]** 。</span><span class="sxs-lookup"><span data-stu-id="979f7-120">Right-click the publication for which you want to view conflicts, and then click **View Conflicts**.</span></span>  
  
4.  <span data-ttu-id="979f7-121">在 **[選取衝突資料表]** 對話方塊中，選取要檢視衝突的資料庫、發行集和資料表。</span><span class="sxs-lookup"><span data-stu-id="979f7-121">In the **Select Conflict Table** dialog box, select a database, publication, and table for which to view conflicts.</span></span>  
  
5.  <span data-ttu-id="979f7-122">在複寫衝突檢視器中，您可以：</span><span class="sxs-lookup"><span data-stu-id="979f7-122">In the Replication Conflict Viewer, you can:</span></span>  
  
    -   <span data-ttu-id="979f7-123">使用上方格右側按鈕篩選資料列。</span><span class="sxs-lookup"><span data-stu-id="979f7-123">Filter rows with the buttons to the right of the upper grid.</span></span>  
  
    -   <span data-ttu-id="979f7-124">在上方格內選取資料列，以便於下方格的該資料列顯示資訊。</span><span class="sxs-lookup"><span data-stu-id="979f7-124">Select a row in the upper grid to display information on that row in the lower grid.</span></span>  
  
    -   <span data-ttu-id="979f7-125">在上方格中選取一個或多個資料列，然後按一下 **[移除]** ，會從衝突中繼資料表中移除資料列。</span><span class="sxs-lookup"><span data-stu-id="979f7-125">Select one or more rows in the upper grid, and then click **Remove**, which removes the row from the conflicts metadata table.</span></span>  
  
    -   <span data-ttu-id="979f7-126">按一下 [屬性] 按鈕 (**...** ]) 以查看涉及衝突之資料行的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="979f7-126">Click the properties button (**...**) to view more information on a column involved in a conflict.</span></span>  
  
    -   <span data-ttu-id="979f7-127">選取 **[記錄此衝突的詳細資料]** 即可將衝突資料記錄到檔案中。</span><span class="sxs-lookup"><span data-stu-id="979f7-127">Select **Log the details of this conflict** to log conflict data to a file.</span></span> <span data-ttu-id="979f7-128">若要指定檔案的位置，請指向 **[檢視]** 功能表，然後按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="979f7-128">To specify a location for the file, point to the **View** menu, and then click **Options**.</span></span> <span data-ttu-id="979f7-129">輸入值，或按一下瀏覽按鈕 ( **[...]** )，然後導覽至適當的檔案。</span><span class="sxs-lookup"><span data-stu-id="979f7-129">Enter a value, or click the browse button (**...**), and then navigate to the appropriate file.</span></span> <span data-ttu-id="979f7-130">按一下 **[確定]** 關閉 **[選項]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="979f7-130">Click **OK** to close the **Options** dialog box.</span></span>  
  
6.  <span data-ttu-id="979f7-131">關閉複寫衝突檢視器。</span><span class="sxs-lookup"><span data-stu-id="979f7-131">Close the Replication Conflict Viewer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="979f7-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="979f7-132">See Also</span></span>  
 <span data-ttu-id="979f7-133">[Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md) </span><span class="sxs-lookup"><span data-stu-id="979f7-133">[Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md) </span></span>  
 [<span data-ttu-id="979f7-134">Queued Updating Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="979f7-134">Queued Updating Conflict Detection and Resolution</span></span>](transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)  
  
  
