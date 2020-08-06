---
title: 移除資料庫鏡像 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], removing
- removing database mirroring [SQL Server]
ms.assetid: bbc4d7f7-3bc7-40d6-a822-af195fe7f8c0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19c1d0449fa1c7434aeaf9c51e3b2dc7bc6b68c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701800"
---
# <a name="remove-database-mirroring-sql-server"></a><span data-ttu-id="ea67e-102">移除資料庫鏡像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ea67e-102">Remove Database Mirroring (SQL Server)</span></span>
  <span data-ttu-id="ea67e-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中移除資料庫內的資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="ea67e-103">This topic describes how to remove database mirroring from a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  <span data-ttu-id="ea67e-104">資料庫擁有者可以隨時手動移除資料庫的鏡像，藉以停止資料庫鏡像工作階段。</span><span class="sxs-lookup"><span data-stu-id="ea67e-104">At any time, the database owner can manually stop a database mirroring session by removing mirroring from the database.</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ea67e-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="ea67e-105">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ea67e-106">Security</span><span class="sxs-lookup"><span data-stu-id="ea67e-106">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ea67e-107">權限</span><span class="sxs-lookup"><span data-stu-id="ea67e-107">Permissions</span></span>  
 <span data-ttu-id="ea67e-108">需要資料庫的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="ea67e-108">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ea67e-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ea67e-109">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-database-mirroring"></a><span data-ttu-id="ea67e-110">若要移除資料庫鏡像</span><span class="sxs-lookup"><span data-stu-id="ea67e-110">To remove database mirroring</span></span>  
  
1.  <span data-ttu-id="ea67e-111">在資料庫鏡像工作階段過程中，連接到主體伺服器執行個體，在 [物件總管] 中按一下伺服器名稱，以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="ea67e-111">During a database mirroring session, connect to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="ea67e-112">展開 **[資料庫]** 並選取資料庫。</span><span class="sxs-lookup"><span data-stu-id="ea67e-112">Expand **Databases**, and select the database.</span></span>  
  
3.  <span data-ttu-id="ea67e-113">以滑鼠右鍵按一下資料庫，選取 [工作]，然後按一下 [鏡像]。</span><span class="sxs-lookup"><span data-stu-id="ea67e-113">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="ea67e-114">這將會開啟在 **[資料庫屬性]** 對話方塊中的 **[鏡像]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="ea67e-114">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="ea67e-115">在 **[選取頁面]** 窗格中按一下 **[鏡像]** 。</span><span class="sxs-lookup"><span data-stu-id="ea67e-115">In the **Select a Page** pane, click **Mirroring**.</span></span>  
  
5.  <span data-ttu-id="ea67e-116">若要移除鏡像，請按一下 **[移除鏡像]** 。</span><span class="sxs-lookup"><span data-stu-id="ea67e-116">To remove mirroring, click **Remove Mirroring**.</span></span> <span data-ttu-id="ea67e-117">會出現提示要求確認。</span><span class="sxs-lookup"><span data-stu-id="ea67e-117">A prompt asks for confirmation.</span></span> <span data-ttu-id="ea67e-118">如果按一下 **[是]** ，會停止工作階段，並從資料庫移除鏡像。</span><span class="sxs-lookup"><span data-stu-id="ea67e-118">If you click **Yes**, the session is stopped and mirroring is removed from the database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ea67e-119">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ea67e-119">Using Transact-SQL</span></span>  
 <span data-ttu-id="ea67e-120">若要移除資料庫鏡像，請使用 **[資料庫屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="ea67e-120">To remove database mirroring, use the **Database Properties**.</span></span> <span data-ttu-id="ea67e-121">使用 **[資料庫屬性]** 對話方塊的 **[鏡像]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="ea67e-121">use the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
#### <a name="to-remove-database-mirroring"></a><span data-ttu-id="ea67e-122">若要移除資料庫鏡像</span><span class="sxs-lookup"><span data-stu-id="ea67e-122">To remove database mirroring</span></span>  
  
1.  <span data-ttu-id="ea67e-123">連接到任一個鏡像夥伴的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ea67e-123">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] of either mirroring partner.</span></span>  
  
2.  <span data-ttu-id="ea67e-124">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="ea67e-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ea67e-125">發出下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="ea67e-125">Issue the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    ALTER DATABASE database_name SET PARTNER OFF  
    ```  
  
     <span data-ttu-id="ea67e-126">其中 *資料庫名稱* 是您要移除其工作階段的鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="ea67e-126">where *database_name* is the mirrored database whose session you want to remove.</span></span>  
  
     <span data-ttu-id="ea67e-127">下列範例會從 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例資料庫中移除資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="ea67e-127">The following example removes database mirroring from the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER OFF;  
    ```  
  
##  <a name="follow-up-removing-database-mirroring"></a><a name="FollowUp"></a> <span data-ttu-id="ea67e-128">後續操作：移除資料庫鏡像</span><span class="sxs-lookup"><span data-stu-id="ea67e-128">Follow Up: Removing Database Mirroring</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ea67e-129">如需移除鏡像之影響的資訊，請參閱[移除資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ea67e-129">For information about the impact of removing mirroring, see [Removing Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
-   <span data-ttu-id="ea67e-130">**如果您打算在資料庫上重新啟動鏡像**</span><span class="sxs-lookup"><span data-stu-id="ea67e-130">**If you intend to restart mirroring on the database**</span></span>  
  
     <span data-ttu-id="ea67e-131">在您可以重新啟動鏡像之前，您必須先將鏡像移除之後在主體資料庫上建立的所有記錄備份套用到鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="ea67e-131">Any log backups taken on the principal database after mirroring was removed must all be applied to the mirror database before you can restart mirroring.</span></span>  
  
-   <span data-ttu-id="ea67e-132">**如果您不打算重新啟動鏡像**</span><span class="sxs-lookup"><span data-stu-id="ea67e-132">**If you do not intent to restart mirroring**</span></span>  
  
     <span data-ttu-id="ea67e-133">另外，您也可以選擇復原先前的鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="ea67e-133">Optionally, you can recover the former mirror database.</span></span> <span data-ttu-id="ea67e-134">在原本是鏡像伺服器的伺服器執行個體上，您可以使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="ea67e-134">On the server instance that was the mirror server, you can use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    RESTORE DATABASE database_name WITH RECOVERY;  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="ea67e-135">如果復原這個資料庫，線上將會有兩個名稱相同但內容不同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="ea67e-135">If you recover this database, two divergent databases with the same name are online.</span></span> <span data-ttu-id="ea67e-136">因此，您必須確定用戶端只能存取其中一個資料庫 (通常是最新的主體資料庫)。</span><span class="sxs-lookup"><span data-stu-id="ea67e-136">Therefore, you need to ensure that clients can access only one of them-typically the most recent principal database.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="ea67e-137">相關工作</span><span class="sxs-lookup"><span data-stu-id="ea67e-137">Related Tasks</span></span>  
  
-   [<span data-ttu-id="ea67e-138">暫停或繼續資料庫鏡像工作階段 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ea67e-138">Pause or Resume a Database Mirroring Session &#40;SQL Server&#41;</span></span>](pause-or-resume-a-database-mirroring-session-sql-server.md)  
  
-   [<span data-ttu-id="ea67e-139">從資料庫鏡像工作階段移除見證 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ea67e-139">Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;</span></span>](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
-   [<span data-ttu-id="ea67e-140">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="ea67e-140">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="ea67e-141">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ea67e-141">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
  
-   [<span data-ttu-id="ea67e-142">範例：使用憑證設定資料庫鏡像 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ea67e-142">Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;</span></span>](example-setting-up-database-mirroring-using-certificates-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="ea67e-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea67e-143">See Also</span></span>  
 <span data-ttu-id="ea67e-144">[資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ea67e-144">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="ea67e-145">[設定資料庫鏡像 &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ea67e-145">[Setting Up Database Mirroring &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="ea67e-146">AlwaysOn Availability Groups (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ea67e-146">AlwaysOn Availability Groups (SQL Server)</span></span>](../availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
