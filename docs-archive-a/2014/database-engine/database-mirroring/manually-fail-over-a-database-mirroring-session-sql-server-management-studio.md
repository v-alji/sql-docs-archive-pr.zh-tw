---
title: 手動容錯移轉資料庫鏡像工作階段 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover [SQL Server], database mirroring
- manual failover [SQL Server]
- database mirroring [SQL Server], failover
ms.assetid: 4ecf9c63-b3a4-4c54-b553-5bc37973232b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7f7f4547058b2dfd4229142dca73a7d9b4bdb239
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709917"
---
# <a name="manually-fail-over-a-database-mirroring-session-sql-server-management-studio"></a><span data-ttu-id="ee34d-102">手動容錯移轉資料庫鏡像工作階段 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="ee34d-102">Manually Fail Over a Database Mirroring Session (SQL Server Management Studio)</span></span>
  <span data-ttu-id="ee34d-103">鏡像資料庫已同步處理時 (亦即，資料庫為 SYNCHRONIZED 狀態時)，資料庫擁有者可以初始化至鏡像伺服器的手動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="ee34d-103">When the mirrored database is synchronized (that is, when the database is in the SYNCHRONIZED state), the database owner can initiate manual failover to the mirror server.</span></span>  
  
 <span data-ttu-id="ee34d-104">在手動容錯移轉期間，會針對發生容錯移轉的資料庫互換主體伺服器和鏡像伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="ee34d-104">During a manual failover, the principal and mirror server roles are swapped for the database on which the failover occurs.</span></span> <span data-ttu-id="ee34d-105">鏡像資料庫變成主體資料庫，而主體資料庫變成鏡像。</span><span class="sxs-lookup"><span data-stu-id="ee34d-105">The mirror database becomes the principal database and the principal database becomes the mirror.</span></span> <span data-ttu-id="ee34d-106">例如，下表顯示手動容錯移轉如何互換這兩個鏡像夥伴 ( `SQLDBENGINE0_1` 和 `SQLDBENGINE0_2`) 的角色。</span><span class="sxs-lookup"><span data-stu-id="ee34d-106">For example, the following table shows the how a manual failover swaps the roles of two mirroring partners: `SQLDBENGINE0_1` and `SQLDBENGINE0_2`.</span></span>  
  
|<span data-ttu-id="ee34d-107">伺服器</span><span class="sxs-lookup"><span data-stu-id="ee34d-107">Server</span></span>|<span data-ttu-id="ee34d-108">容錯移轉前</span><span class="sxs-lookup"><span data-stu-id="ee34d-108">Before failover</span></span>|<span data-ttu-id="ee34d-109">容錯移轉後</span><span class="sxs-lookup"><span data-stu-id="ee34d-109">After failover</span></span>|  
|------------|---------------------|--------------------|  
|`SQLDBENGINE0_1`|<span data-ttu-id="ee34d-110">PRINCIPAL</span><span class="sxs-lookup"><span data-stu-id="ee34d-110">PRINCIPAL</span></span>|<span data-ttu-id="ee34d-111">MIRROR</span><span class="sxs-lookup"><span data-stu-id="ee34d-111">MIRROR</span></span>|  
|`SQLDBENGINE0_2`|<span data-ttu-id="ee34d-112">MIRROR</span><span class="sxs-lookup"><span data-stu-id="ee34d-112">MIRROR</span></span>|<span data-ttu-id="ee34d-113">PRINCIPAL</span><span class="sxs-lookup"><span data-stu-id="ee34d-113">PRINCIPAL</span></span>|  
  
 <span data-ttu-id="ee34d-114">請注意，其他資料庫鏡像工作階段的伺服器角色不受影響。</span><span class="sxs-lookup"><span data-stu-id="ee34d-114">Note that the server roles for other database mirroring sessions are not affected.</span></span> <span data-ttu-id="ee34d-115">如需詳細資訊，請參閱 [資料庫鏡像工作階段期間的角色切換 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)版本都可使用見證伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="ee34d-115">For more information, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  
### <a name="to-manually-fail-over-database-mirroring"></a><span data-ttu-id="ee34d-116">若要手動容錯移轉資料庫鏡像</span><span class="sxs-lookup"><span data-stu-id="ee34d-116">To manually fail over database mirroring</span></span>  
  
1.  <span data-ttu-id="ee34d-117">連接到主體伺服器執行個體，在 **[物件總管]** 窗格中按一下伺服器名稱，以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="ee34d-117">Connect to the principal server instance and, in the **Object Explorer** pane, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="ee34d-118">展開 [資料庫]，然後選取要容錯移轉的資料庫。</span><span class="sxs-lookup"><span data-stu-id="ee34d-118">Expand **Databases**, and select the database to be failed over.</span></span>  
  
3.  <span data-ttu-id="ee34d-119">以滑鼠右鍵按一下資料庫，選取 [工作]，然後按一下 [鏡像]。</span><span class="sxs-lookup"><span data-stu-id="ee34d-119">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="ee34d-120">這將會開啟在 **[資料庫屬性]** 對話方塊中的 **[鏡像]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="ee34d-120">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="ee34d-121">按一下 [容錯移轉]。</span><span class="sxs-lookup"><span data-stu-id="ee34d-121">Click **Failover**.</span></span>  
  
     <span data-ttu-id="ee34d-122">確認方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="ee34d-122">A confirmation box appears.</span></span>  <span data-ttu-id="ee34d-123">主體伺服器一開始會使用 Windows 驗證來嘗試連接至鏡像伺服器。</span><span class="sxs-lookup"><span data-stu-id="ee34d-123">The principal server begins by trying to connect to the mirror server by using Windows Authentication.</span></span> <span data-ttu-id="ee34d-124">如果 Windows 驗證沒有用，主體伺服器就會顯示 [連接到伺服器] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ee34d-124">If Windows Authentication does not work, the principal server displays the **Connect to Server** dialog box.</span></span> <span data-ttu-id="ee34d-125">如果鏡像伺服器使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證，請在 [驗證] 方塊中選取 [SQL Server 驗證]。</span><span class="sxs-lookup"><span data-stu-id="ee34d-125">If the mirror server uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, select **SQL Server Authentication** in the **Authentication** box.</span></span> <span data-ttu-id="ee34d-126">在 [登入] 文字方塊中，指定要用來連接至鏡像伺服器的登入帳戶，然後在 [密碼] 文字方塊中，指定該帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="ee34d-126">In the **Login** text box, specify the login account to connect with on the mirror server, and in the **Password** text box, specify the password for that account.</span></span>  
  
     <span data-ttu-id="ee34d-127">如果容錯移轉成功，[資料庫屬性] 對話方塊就會關閉。</span><span class="sxs-lookup"><span data-stu-id="ee34d-127">If failover succeeds, the **Database Properties** dialog box closes.</span></span> <span data-ttu-id="ee34d-128">鏡像資料庫變成主體資料庫，而主體資料庫變成鏡像。</span><span class="sxs-lookup"><span data-stu-id="ee34d-128">The mirror database becomes the principal database and the principal database becomes the mirror.</span></span>  
  
     <span data-ttu-id="ee34d-129">如果容錯移轉失敗，則會顯示錯誤訊息，而且對話方塊會保持開啟狀態。</span><span class="sxs-lookup"><span data-stu-id="ee34d-129">If failover fails, an error message is displayed and the dialog box remains open.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="ee34d-130">如果您在開啟 [鏡像] 頁面後修改了任何屬性，將不會儲存那些變更。</span><span class="sxs-lookup"><span data-stu-id="ee34d-130">If you have modified any properties since opening the **Mirroring** page, those changes will not be saved.</span></span>  
  
     <span data-ttu-id="ee34d-131">對話方塊會自動關閉。</span><span class="sxs-lookup"><span data-stu-id="ee34d-131">The dialog box closes automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee34d-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee34d-132">See Also</span></span>  
 <span data-ttu-id="ee34d-133">[資料庫屬性 &#40;鏡像頁面&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="ee34d-133">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="ee34d-134">[資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ee34d-134">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="ee34d-135">[手動容錯移轉資料庫鏡像工作階段 &#40;Transact-SQL&#41;](manually-fail-over-a-database-mirroring-session-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="ee34d-135">[Manually Fail Over a Database Mirroring Session &#40;Transact-SQL&#41;](manually-fail-over-a-database-mirroring-session-transact-sql.md) </span></span>  
 <span data-ttu-id="ee34d-136">[暫停或繼續資料庫鏡像工作階段 &#40;SQL Server&#41;](pause-or-resume-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ee34d-136">[Pause or Resume a Database Mirroring Session &#40;SQL Server&#41;](pause-or-resume-a-database-mirroring-session-sql-server.md) </span></span>  
 [<span data-ttu-id="ee34d-137">移除資料庫鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ee34d-137">Remove Database Mirroring &#40;SQL Server&#41;</span></span>](remove-database-mirroring-sql-server.md)  
  
  
