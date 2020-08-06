---
title: 將次要資料庫從可用性群組移除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.unjoindb.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], databases
ms.assetid: 4e51a570-58d7-4f01-9390-4198f3602576
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1c3de0afd73b46ae5594d26d1763f5bd78483efd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593605"
---
# <a name="remove-a-secondary-database-from-an-availability-group-sql-server"></a><span data-ttu-id="ca42b-102">將次要資料庫從可用性群組移除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ca42b-102">Remove a Secondary Database from an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="ca42b-103">此主題描述如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]或 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中的 PowerShell，將次要資料庫從 AlwaysOn 可用性群組中移除。</span><span class="sxs-lookup"><span data-stu-id="ca42b-103">This topic describes how to remove a secondary database from an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="ca42b-104">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="ca42b-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ca42b-105">先決條件</span><span class="sxs-lookup"><span data-stu-id="ca42b-105">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="ca42b-106">安全性</span><span class="sxs-lookup"><span data-stu-id="ca42b-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ca42b-107">**若要使用下列項目移除次要資料庫：**</span><span class="sxs-lookup"><span data-stu-id="ca42b-107">**To remove a secondary database, using:**</span></span>  
  
     [<span data-ttu-id="ca42b-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ca42b-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ca42b-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ca42b-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="ca42b-110">PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca42b-110">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="ca42b-111">**待處理：**  [從可用性群組中移除次要資料庫之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="ca42b-111">**Follow Up:**  [After Removing a Secondary Database from an Availability Group](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ca42b-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="ca42b-112">Before You Begin</span></span>  
  
###  <a name="Restrictions"></a>   
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="ca42b-113">必要條件和限制</span><span class="sxs-lookup"><span data-stu-id="ca42b-113">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="ca42b-114">只有在次要複本上才支援這個工作。</span><span class="sxs-lookup"><span data-stu-id="ca42b-114">This task is supported only on secondary replicas.</span></span> <span data-ttu-id="ca42b-115">您必須連接到裝載要從中移除資料庫之次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="ca42b-115">You must be connected to the server instance that hosts the secondary replica from which the database is to be removed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ca42b-116">Security</span><span class="sxs-lookup"><span data-stu-id="ca42b-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ca42b-117">權限</span><span class="sxs-lookup"><span data-stu-id="ca42b-117">Permissions</span></span>  
 <span data-ttu-id="ca42b-118">需要資料庫的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="ca42b-118">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ca42b-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ca42b-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="ca42b-120">**若要從可用性群組中移除次要資料庫**</span><span class="sxs-lookup"><span data-stu-id="ca42b-120">**To remove a secondary database from an availability group**</span></span>  
  
1.  <span data-ttu-id="ca42b-121">在 [物件總管] 中，連接到裝載您要從中移除一個或多個次要資料庫之次要複本的伺服器執行個體，然後展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="ca42b-121">In Object Explorer, connect to the server instance that hosts the secondary replica from which you want to remove one or more secondary databases, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="ca42b-122">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="ca42b-122">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="ca42b-123">選取可用性群組，然後展開 **[可用性資料庫]** 節點。</span><span class="sxs-lookup"><span data-stu-id="ca42b-123">Select the availability group, and expand the **Availability Databases** node.</span></span>  
  
4.  <span data-ttu-id="ca42b-124">此步驟取決於您要移除多個資料庫群組或只要移除一個資料庫，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ca42b-124">This step depends on whether you want to remove multiple databases groups or only one database, as follows:</span></span>  
  
    -   <span data-ttu-id="ca42b-125">若要移除多個資料庫，請使用 **[物件總管詳細資料]** 窗格檢視及選取您要移除的所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="ca42b-125">To remove multiple databases, use the **Object Explorer Details** pane to view and select all the databases that you want to remove.</span></span> <span data-ttu-id="ca42b-126">如需詳細資訊，請參閱[使用物件總管詳細資料監視可用性群組 &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="ca42b-126">For more information, see [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md).</span></span>  
  
    -   <span data-ttu-id="ca42b-127">若要移除單一資料庫，請在 **[物件總管]** 窗格或 **[物件總管詳細資料]** 窗格中選取它。</span><span class="sxs-lookup"><span data-stu-id="ca42b-127">To remove a single database, select it in either the **Object Explorer** pane or the **Object Explorer Details** pane.</span></span>  
  
5.  <span data-ttu-id="ca42b-128">以滑鼠右鍵按一下選取的一或多個資料庫，然後在命令功能表中選取 [移除次要資料庫]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ca42b-128">Right-click the selected database or databases, and select **Remove Secondary Database** in the command menu.</span></span>  
  
6.  <span data-ttu-id="ca42b-129">在 **[從可用性群組移除資料庫]** 對話方塊中，若要移除所有列出的可用性資料庫，請按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="ca42b-129">In the **Remove Database from Availability Group** dialog box, to remove all the listed databases, click **OK**.</span></span> <span data-ttu-id="ca42b-130">如果您不要移除所有列出的資料庫，請按一下 **[取消]**。</span><span class="sxs-lookup"><span data-stu-id="ca42b-130">If you do not want to remove all the listed databases, click **Cancel**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ca42b-131">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ca42b-131">Using Transact-SQL</span></span>  
 <span data-ttu-id="ca42b-132">**若要從可用性群組中移除次要資料庫**</span><span class="sxs-lookup"><span data-stu-id="ca42b-132">**To remove a secondary database from an availability group**</span></span>  
  
1.  <span data-ttu-id="ca42b-133">連接到裝載次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="ca42b-133">Connect to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="ca42b-134">使用 [ALTER DATABASE 陳述式的 SET HADR 子句](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) ，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ca42b-134">Use the [SET HADR clause of the ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) statement, as follows:</span></span>  
  
     <span data-ttu-id="ca42b-135">ALTER DATABASE *database_name* SET HADR OFF</span><span class="sxs-lookup"><span data-stu-id="ca42b-135">ALTER DATABASE *database_name* SET HADR OFF</span></span>  
  
     <span data-ttu-id="ca42b-136">其中 *database_name* 是次要資料庫的名稱，您要從其所屬的可用性群組移除此資料庫。</span><span class="sxs-lookup"><span data-stu-id="ca42b-136">where *database_name* is the name of a secondary database to be removed from the availability group to which it belongs.</span></span>  
  
     <span data-ttu-id="ca42b-137">下列範例會將本機次要資料庫 *MyDb2* 從其可用性群組中移除。</span><span class="sxs-lookup"><span data-stu-id="ca42b-137">The following example removes the local secondary database *MyDb2* from its availability group.</span></span>  
  
    ```sql
    ALTER DATABASE MyDb2 SET HADR OFF;  
    GO  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="ca42b-138">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca42b-138">Using PowerShell</span></span>  
 <span data-ttu-id="ca42b-139">**若要從可用性群組中移除次要資料庫**</span><span class="sxs-lookup"><span data-stu-id="ca42b-139">**To remove a secondary database from an availability group**</span></span>  
  
1.  <span data-ttu-id="ca42b-140">將目錄切換到 (`cd`) 裝載次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="ca42b-140">Change directory (`cd`) to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="ca42b-141">使用 **Remove-SqlAvailabilityDatabase** 指令程式，指定要從可用性群組移除的可用性資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="ca42b-141">Use the **Remove-SqlAvailabilityDatabase** cmdlet, specifying the name of the availability database to be removed from the availability group.</span></span> <span data-ttu-id="ca42b-142">連接到裝載次要複本的伺服器執行個體時，只會從可用性群組移除本機次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="ca42b-142">When you are connected to a server instance that hosts a secondary replica, only the local secondary database is removed from the availability group.</span></span>  
  
     <span data-ttu-id="ca42b-143">例如，下列命令會從伺服器執行個體 `MyDb8` 所裝載的次要複本中移除次要資料庫 `SecondaryComputer\Instance`。</span><span class="sxs-lookup"><span data-stu-id="ca42b-143">For example, the following command removes the secondary database `MyDb8` from the secondary replica hosted by the server instance named `SecondaryComputer\Instance`.</span></span> <span data-ttu-id="ca42b-144">已移除之次要資料庫的資料同步處理會停止。</span><span class="sxs-lookup"><span data-stu-id="ca42b-144">Data synchronization to the removed secondary databases ceases.</span></span> <span data-ttu-id="ca42b-145">此命令不會影響主要資料庫或任何其他次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="ca42b-145">This command does not affect the primary database or any other secondary databases.</span></span>  
  
    ```powershell
    Remove-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\SecondaryComputer\InstanceName\AvailabilityGroups\MyAg\Databases\MyDb8  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="ca42b-146">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="ca42b-146">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="ca42b-147">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="ca42b-147">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="ca42b-148">**若要設定和使用 SQL Server PowerShell 提供者**</span><span class="sxs-lookup"><span data-stu-id="ca42b-148">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="ca42b-149">SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="ca42b-149">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-removing-a-secondary-database-from-an-availability-group"></a><a name="FollowUp"></a><span data-ttu-id="ca42b-150">後續操作：從可用性群組中移除次要資料庫之後</span><span class="sxs-lookup"><span data-stu-id="ca42b-150">Follow Up: After Removing a Secondary Database from an Availability Group</span></span>  
 <span data-ttu-id="ca42b-151">次要資料庫已移除時，它不再聯結至可用性群組，而且可用性群組會將移除之次要資料庫的所有相關資訊捨棄。</span><span class="sxs-lookup"><span data-stu-id="ca42b-151">When a secondary database is removed, it is no longer joined to the availability group and all information about the removed secondary database is discarded by the availability group.</span></span> <span data-ttu-id="ca42b-152">移除的次要資料庫處於 RESTORING 狀態。</span><span class="sxs-lookup"><span data-stu-id="ca42b-152">The removed secondary database is placed in the RESTORING state.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="ca42b-153">在移除次要資料庫後的短暫時間內，您可能可以透過將次要資料庫重新聯結至可用性群組，在資料庫上重新啟動 AlwaysOn 資料同步處理。</span><span class="sxs-lookup"><span data-stu-id="ca42b-153">For a short time after removing a secondary database, you might be able to restart AlwaysOn data synchronization on the database by re-joining it to the availability group.</span></span> <span data-ttu-id="ca42b-154">如需詳細資訊，請參閱 [將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ca42b-154">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
 <span data-ttu-id="ca42b-155">此時有替代方法可處理移除的次要資料庫：</span><span class="sxs-lookup"><span data-stu-id="ca42b-155">At this point there are alternative ways of dealing with a removed secondary database:</span></span>  
  
-   <span data-ttu-id="ca42b-156">如果您不再需要此次要資料庫，可將它卸除。</span><span class="sxs-lookup"><span data-stu-id="ca42b-156">If you no longer need the secondary database, you can drop it.</span></span>  
  
     <span data-ttu-id="ca42b-157">如需詳細資訊，請參閱 [DROP DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) 或[刪除資料庫](../../../relational-databases/databases/delete-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="ca42b-157">For more information, see [DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) or [Delete a Database](../../../relational-databases/databases/delete-a-database.md).</span></span>  
  
-   <span data-ttu-id="ca42b-158">從可用性群組中移除次要資料庫之後，若要存取移除的次要資料庫，可以復原資料庫。</span><span class="sxs-lookup"><span data-stu-id="ca42b-158">If you want to access a removed secondary database after it has been removed from the availability group, you can recover the database.</span></span> <span data-ttu-id="ca42b-159">不過，如果復原移除的次要資料庫，線上將會有兩個名稱相同但內容不同的獨立資料庫。</span><span class="sxs-lookup"><span data-stu-id="ca42b-159">However, if you recover a removed secondary database, two divergent, independent databases that have the same name are online.</span></span> <span data-ttu-id="ca42b-160">您必須確認用戶端只可以存取目前的主要資料庫。</span><span class="sxs-lookup"><span data-stu-id="ca42b-160">You must make sure that clients can access only the current primary database.</span></span>  
  
     <span data-ttu-id="ca42b-161">如需詳細資訊，請參閱[復原資料庫而不還原資料 &#40;Transact-SQL&#41;](../../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="ca42b-161">For more information, see [Recover a Database Without Restoring Data &#40;Transact-SQL&#41;](../../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca42b-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca42b-162">See Also</span></span>  
 <span data-ttu-id="ca42b-163">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ca42b-163">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="ca42b-164">將主要資料庫從可用性群組移除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ca42b-164">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
