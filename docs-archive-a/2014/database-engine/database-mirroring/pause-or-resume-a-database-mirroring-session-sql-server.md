---
title: 暫停或繼續資料庫鏡像工作階段 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- resuming database mirroring
- database mirroring [SQL Server], sessions
- database mirroring [SQL Server], pausing
- database mirroring [SQL Server], resuming
- pausing database mirroring
ms.assetid: 05ede3b4-6abe-4442-abb7-9f5aee1d6bc0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b8a9e30bed3ff268fcfdc6e352ad15ebedfe4e8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701860"
---
# <a name="pause-or-resume-a-database-mirroring-session-sql-server"></a><span data-ttu-id="516e5-102">暫停或繼續資料庫鏡像工作階段 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="516e5-102">Pause or Resume a Database Mirroring Session (SQL Server)</span></span>
  <span data-ttu-id="516e5-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中暫停或繼續資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="516e5-103">This topic describes how to pause or resume database mirroring in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="516e5-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="516e5-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="516e5-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="516e5-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="516e5-106">安全性</span><span class="sxs-lookup"><span data-stu-id="516e5-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="516e5-107">**使用下列方法來執行 ReplaceThisText：**</span><span class="sxs-lookup"><span data-stu-id="516e5-107">**To ReplaceThisText, using:**</span></span>  
  
     [<span data-ttu-id="516e5-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="516e5-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="516e5-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="516e5-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="516e5-110">**後續操作：**  [暫停或繼續資料庫鏡像之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="516e5-110">**Follow Up:**  [After Pausing or Resuming Database Mirroring](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="516e5-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="516e5-111">Before You Begin</span></span>  
 <span data-ttu-id="516e5-112">您可以在任何時候暫停資料庫鏡像工作階段，此工作階段可能會在發生瓶頸時提高效能，而且您可以隨時繼續暫停的工作階段。</span><span class="sxs-lookup"><span data-stu-id="516e5-112">At any time, you can suspend a database mirroring session, which might improve performance during bottlenecks, and you can resume a suspended session at any time.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="516e5-113">在強制服務之後，當原始主體伺服器重新連接時，便會暫停鏡像。</span><span class="sxs-lookup"><span data-stu-id="516e5-113">After a forced service, when the original principal server reconnects, mirroring is suspended.</span></span> <span data-ttu-id="516e5-114">在這種情況下繼續執行鏡像，很可能會造成原始主體伺服器上的資料遺失。</span><span class="sxs-lookup"><span data-stu-id="516e5-114">Resuming mirroring in this situation could possibly cause data loss on the original principal server.</span></span> <span data-ttu-id="516e5-115">如需管理潛在資料遺失的資訊，請參閱[資料庫鏡像工作階段期間的角色切換 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="516e5-115">For information about managing the potential data loss, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="516e5-116">Security</span><span class="sxs-lookup"><span data-stu-id="516e5-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="516e5-117">權限</span><span class="sxs-lookup"><span data-stu-id="516e5-117">Permissions</span></span>  
 <span data-ttu-id="516e5-118">需要資料庫的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="516e5-118">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="516e5-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="516e5-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="516e5-120">若要暫停或繼續資料庫鏡像工作階段，請使用 **[資料庫屬性鏡像]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="516e5-120">To pause or resume a database mirroring session use the **Database Properties Mirroring** page.</span></span>  
  
#### <a name="to-pause-or-resume-database-mirroring"></a><span data-ttu-id="516e5-121">若要暫停或繼續資料庫鏡像</span><span class="sxs-lookup"><span data-stu-id="516e5-121">To pause or resume database mirroring</span></span>  
  
1.  <span data-ttu-id="516e5-122">在資料庫鏡像工作階段過程中，連接到主體伺服器執行個體，在 [物件總管] 中按一下伺服器名稱，以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="516e5-122">During a database mirroring session, connect to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="516e5-123">展開 **[資料庫]** 並選取資料庫。</span><span class="sxs-lookup"><span data-stu-id="516e5-123">Expand **Databases**, and select the database.</span></span>  
  
3.  <span data-ttu-id="516e5-124">以滑鼠右鍵按一下資料庫，選取 [工作]，然後按一下 [鏡像]。</span><span class="sxs-lookup"><span data-stu-id="516e5-124">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="516e5-125">這將會開啟在 **[資料庫屬性]** 對話方塊中的 **[鏡像]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="516e5-125">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="516e5-126">若要暫停工作階段，請按一下 **[暫停]**。</span><span class="sxs-lookup"><span data-stu-id="516e5-126">To pause the session, click **Pause**.</span></span>  
  
     <span data-ttu-id="516e5-127">會出現提示字元要求確認；如果您按一下 **[是]** ，工作階段將暫停，然後按鈕將變更為 **[繼續]** 。</span><span class="sxs-lookup"><span data-stu-id="516e5-127">A prompt asks for confirmation; if you click **Yes**, the session is paused, and the button changes to **Resume**.</span></span>  
  
     <span data-ttu-id="516e5-128">如需暫停工作階段之影響的詳細資訊，請參閱[暫停與繼續資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="516e5-128">For more information about the impact of pausing a session, see [Pausing and Resuming Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
5.  <span data-ttu-id="516e5-129">若要繼續工作階段，請按一下 **[繼續]** 。</span><span class="sxs-lookup"><span data-stu-id="516e5-129">To resume the session, click **Resume**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="516e5-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="516e5-130">Using Transact-SQL</span></span>  
  
#### <a name="to-pause-database-mirroring"></a><span data-ttu-id="516e5-131">若要暫停資料庫鏡像</span><span class="sxs-lookup"><span data-stu-id="516e5-131">To pause database mirroring</span></span>  
  
1.  <span data-ttu-id="516e5-132">連接到任一個夥伴的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="516e5-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] for either partner.</span></span>  
  
2.  <span data-ttu-id="516e5-133">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="516e5-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="516e5-134">發出下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="516e5-134">Issue the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
     <span data-ttu-id="516e5-135">ALTER DATABASE *database_name* SET PARTNER SUSPEND</span><span class="sxs-lookup"><span data-stu-id="516e5-135">ALTER DATABASE *database_name* SET PARTNER SUSPEND</span></span>  
  
     <span data-ttu-id="516e5-136">其中 *database_name* 是您要暫停其工作階段的鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="516e5-136">where *database_name* is the mirrored database whose session you want to you want to suspend.</span></span>  
  
     <span data-ttu-id="516e5-137">下列範例會暫停 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="516e5-137">The following example pauses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER SUSPEND;  
    ```  
  
##### <a name="to-resume-database-mirroring"></a><span data-ttu-id="516e5-138">若要繼續資料庫鏡像</span><span class="sxs-lookup"><span data-stu-id="516e5-138">To resume database mirroring</span></span>  
  
1.  <span data-ttu-id="516e5-139">連接到任一個夥伴的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="516e5-139">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] for either partner.</span></span>  
  
2.  <span data-ttu-id="516e5-140">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="516e5-140">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="516e5-141">發出下列 Transact-SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="516e5-141">Issue the following Transact-SQL statement:</span></span>  
  
     <span data-ttu-id="516e5-142">ALTER DATABASE *database_name* SET PARTNER RESUME</span><span class="sxs-lookup"><span data-stu-id="516e5-142">ALTER DATABASE *database_name* SET PARTNER RESUME</span></span>  
  
     <span data-ttu-id="516e5-143">其中 *database_name* 是您要繼續其工作階段的鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="516e5-143">where *database_name* is the mirrored database whose session you want to resume.</span></span>  
  
     <span data-ttu-id="516e5-144">下列範例會暫停 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="516e5-144">The following example pauses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER RESUME;  
    ```  
  
##  <a name="follow-up-after-pausing-or-resuming-database-mirroring"></a><a name="FollowUp"></a><span data-ttu-id="516e5-145">後續操作：暫停或繼續資料庫鏡像之後</span><span class="sxs-lookup"><span data-stu-id="516e5-145">Follow Up: After Pausing or Resuming Database Mirroring</span></span>  
  
-   <span data-ttu-id="516e5-146">**暫停資料庫鏡像之後**</span><span class="sxs-lookup"><span data-stu-id="516e5-146">**After pausing database mirroring**</span></span>  
  
     <span data-ttu-id="516e5-147">在主要資料庫上，採取預防措施來避免交易記錄變滿。</span><span class="sxs-lookup"><span data-stu-id="516e5-147">On the primary database, take precautions to avoid a full transaction log.</span></span> <span data-ttu-id="516e5-148">如需詳細資訊，請參閱 [交易記錄 &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="516e5-148">For more information, see [The Transaction Log &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md).</span></span>  
  
-   <span data-ttu-id="516e5-149">**繼續資料庫鏡像之後**</span><span class="sxs-lookup"><span data-stu-id="516e5-149">**After resuming database mirroring**</span></span>  
  
     <span data-ttu-id="516e5-150">繼續資料庫鏡像會使鏡像資料庫處於 SYNCHRONIZING 狀態。</span><span class="sxs-lookup"><span data-stu-id="516e5-150">Resuming database mirroring places the mirror database in the SYNCHRONIZING state.</span></span> <span data-ttu-id="516e5-151">若安全性層級為 FULL，則鏡像會追趕上主體，且鏡像資料庫會進入 SYNCHRONIZED 狀態。</span><span class="sxs-lookup"><span data-stu-id="516e5-151">If the safety level is FULL, the mirror catches up with the principal and the mirror database enters the SYNCHRONIZED state.</span></span> <span data-ttu-id="516e5-152">此時即有可能發生容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="516e5-152">At this point, failover becomes possible.</span></span> <span data-ttu-id="516e5-153">若見證存在並處於 ON 的狀態，就有可能發生自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="516e5-153">If the witness is present and ON, automatic failover is possible.</span></span> <span data-ttu-id="516e5-154">若見證不存在，則有可能發生手動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="516e5-154">In the absence of a witness, manual failover is possible.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="516e5-155">相關工作</span><span class="sxs-lookup"><span data-stu-id="516e5-155">Related Tasks</span></span>  
  
-   [<span data-ttu-id="516e5-156">移除資料庫鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="516e5-156">Remove Database Mirroring &#40;SQL Server&#41;</span></span>](remove-database-mirroring-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="516e5-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="516e5-157">See Also</span></span>  
 [<span data-ttu-id="516e5-158">資料庫鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="516e5-158">Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
