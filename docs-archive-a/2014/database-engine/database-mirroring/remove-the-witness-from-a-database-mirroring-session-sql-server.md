---
title: 從資料庫鏡像工作階段移除見證 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- witness [SQL Server], turning off
- witness [SQL Server], removing
- database mirroring [SQL Server], witness
ms.assetid: f3ce7afc-8936-4d35-80ce-d0f8fbc318d3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d5ede54aca3588a6fcd7cee8759112b606eac752
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701797"
---
# <a name="remove-the-witness-from-a-database-mirroring-session-sql-server"></a><span data-ttu-id="d2def-102">從資料庫鏡像工作階段移除見證 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d2def-102">Remove the Witness from a Database Mirroring Session (SQL Server)</span></span>
  <span data-ttu-id="d2def-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中移除資料庫鏡像工作階段內的見證。</span><span class="sxs-lookup"><span data-stu-id="d2def-103">This topic describes how to remove a witness from a database mirroring session in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d2def-104">在資料庫鏡像工作階段期間，資料庫擁有者隨時可以關閉資料庫鏡像工作階段的見證。</span><span class="sxs-lookup"><span data-stu-id="d2def-104">At any time during a database mirroring session, the database owner can turn off the witness for a database mirroring session.</span></span>  
  
 <span data-ttu-id="d2def-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="d2def-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d2def-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="d2def-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d2def-107">安全性</span><span class="sxs-lookup"><span data-stu-id="d2def-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d2def-108">**若要取代移除見證，請使用：**</span><span class="sxs-lookup"><span data-stu-id="d2def-108">**To Replace remove the witness, using:**</span></span>  
  
     [<span data-ttu-id="d2def-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d2def-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d2def-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d2def-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="d2def-111">**後續操作：**  [移除見證之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="d2def-111">**Follow Up:**  [After Removing the Witness](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d2def-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="d2def-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d2def-113">Security</span><span class="sxs-lookup"><span data-stu-id="d2def-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d2def-114">權限</span><span class="sxs-lookup"><span data-stu-id="d2def-114">Permissions</span></span>  
 <span data-ttu-id="d2def-115">需要資料庫的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="d2def-115">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d2def-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d2def-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-the-witness"></a><span data-ttu-id="d2def-117">移除見證</span><span class="sxs-lookup"><span data-stu-id="d2def-117">To remove the witness</span></span>  
  
1.  <span data-ttu-id="d2def-118">連接到主體伺服器執行個體，在 **[物件總管]** 窗格中按一下伺服器名稱，以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="d2def-118">Connect to the principal server instance and, in the **Object Explorer** pane, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="d2def-119">展開 **[資料庫]**，然後選取要移除見證的資料庫。</span><span class="sxs-lookup"><span data-stu-id="d2def-119">Expand **Databases**, and select the database whose witness you want to remove.</span></span>  
  
3.  <span data-ttu-id="d2def-120">以滑鼠右鍵按一下資料庫，選取 [工作]，然後按一下 [鏡像]。</span><span class="sxs-lookup"><span data-stu-id="d2def-120">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="d2def-121">這將會開啟在 **[資料庫屬性]** 對話方塊中的 **[鏡像]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="d2def-121">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="d2def-122">若要移除見證，請從 **[見證]** 欄位刪除其伺服器網路位址。</span><span class="sxs-lookup"><span data-stu-id="d2def-122">To remove the witness, delete its server network address from the **Witness** field.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d2def-123">如果從具有自動容錯移轉的高安全性模式切換到高效能模式，則會自動清除 [見證] 欄位。</span><span class="sxs-lookup"><span data-stu-id="d2def-123">If you switch from high-safety mode with automatic failover to high-performance mode, the **Witness** field is automatically cleared.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d2def-124">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d2def-124">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-the-witness"></a><span data-ttu-id="d2def-125">移除見證</span><span class="sxs-lookup"><span data-stu-id="d2def-125">To remove the witness</span></span>  
  
1.  <span data-ttu-id="d2def-126">連接到任一夥伴伺服器執行個體上的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d2def-126">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on either partner server instance.</span></span>  
  
2.  <span data-ttu-id="d2def-127">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="d2def-127">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d2def-128">發出下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="d2def-128">Issue the following statement:</span></span>  
  
     <span data-ttu-id="d2def-129">[ALTER DATABASE 資料庫名稱](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) \*\* SET WITNESS OFF</span><span class="sxs-lookup"><span data-stu-id="d2def-129">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) *database_name* SET WITNESS OFF</span></span>  
  
     <span data-ttu-id="d2def-130">其中 *database_name* 是鏡像資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="d2def-130">where *database_name* is the name of the mirrored database.</span></span>  
  
     <span data-ttu-id="d2def-131">下列範例會從 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫中移除見證。</span><span class="sxs-lookup"><span data-stu-id="d2def-131">The following example removes the witness from the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET WITNESS OFF ;  
    ```  
  
##  <a name="follow-up-after-removing-the-witness"></a><a name="FollowUp"></a><span data-ttu-id="d2def-132">後續操作：移除見證之後</span><span class="sxs-lookup"><span data-stu-id="d2def-132">Follow Up: After Removing the Witness</span></span>  
 <span data-ttu-id="d2def-133">關閉見證會根據交易安全性設定來變更 [作業模式](database-mirroring-operating-modes.md)：</span><span class="sxs-lookup"><span data-stu-id="d2def-133">Turning off the witness changes the [operating mode](database-mirroring-operating-modes.md)in accordance with the transaction-safety setting:</span></span>  
  
-   <span data-ttu-id="d2def-134">如果交易安全性設定為 FULL (預設值)，則工作階段會使用高安全性的同步模式，而且不包含自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="d2def-134">If transaction safety is set to FULL (the default), the session uses high-safety, synchronous mode without automatic failover.</span></span>  
  
-   <span data-ttu-id="d2def-135">如果交易安全性設定為 OFF，則工作階段會以非同步方式作業 (以高效能模式)，而且不需要仲裁。</span><span class="sxs-lookup"><span data-stu-id="d2def-135">If transaction safety is set to OFF, the session operates asynchronously (in high-performance mode) without requiring quorum.</span></span> <span data-ttu-id="d2def-136">每當交易安全性關閉時，我們也強烈建議您關閉見證。</span><span class="sxs-lookup"><span data-stu-id="d2def-136">Whenever transaction safety is turned off, we strongly recommend also turning the witness off.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="d2def-137">資料庫的交易安全性設定會記錄在每個夥伴之 **mirroring_safety_level** 和 **mirroring_safety_level_desc** 資料行的 [sys.database_mirroring](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql) 目錄檢視中。</span><span class="sxs-lookup"><span data-stu-id="d2def-137">The transaction safety setting of the database is recorded on each partner in the [sys.database_mirroring](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql) catalog view in the **mirroring_safety_level** and **mirroring_safety_level_desc** columns.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="d2def-138">相關工作</span><span class="sxs-lookup"><span data-stu-id="d2def-138">Related Tasks</span></span>  
  
-   [<span data-ttu-id="d2def-139">使用 Windows 驗證新增資料庫鏡像見證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d2def-139">Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="d2def-140">新增或取代資料庫鏡像見證 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="d2def-140">Add or Replace a Database Mirroring Witness &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="d2def-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2def-141">See Also</span></span>  
 <span data-ttu-id="d2def-142">[ALTER DATABASE 資料庫鏡像 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="d2def-142">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="d2def-143">[變更資料庫鏡像會話中的交易安全性 &#40;Transact-sql&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="d2def-143">[Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md) </span></span>  
 <span data-ttu-id="d2def-144">[使用 Windows 驗證加入資料庫鏡像見證 &#40;Transact-sql&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="d2def-144">[Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md) </span></span>  
 [<span data-ttu-id="d2def-145">資料庫鏡像見證</span><span class="sxs-lookup"><span data-stu-id="d2def-145">Database Mirroring Witness</span></span>](database-mirroring-witness.md)  
  
  
