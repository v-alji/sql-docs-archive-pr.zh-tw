---
title: 將主要資料庫從可用性群組移除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.removeprimarydb.f1
helpviewer_keywords:
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: 6d4ca31e-ddf0-44bf-be5e-a5da060bf096
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b6fafaf6464431d68f8cfdf9dc9d8fa844a42a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593607"
---
# <a name="remove-a-primary-database-from-an-availability-group-sql-server"></a><span data-ttu-id="9586a-102">將主要資料庫從可用性群組移除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9586a-102">Remove a Primary Database from an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="9586a-103">此主題描述如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 中的 PowerShell，將主要資料庫和對應的次要資料庫從 AlwaysOn 可用性群組中移除。</span><span class="sxs-lookup"><span data-stu-id="9586a-103">This topic describes how to remove both the primary database and the corresponding secondary database(s) from an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="9586a-104">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="9586a-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9586a-105">必要條件和限制</span><span class="sxs-lookup"><span data-stu-id="9586a-105">Prerequisites and Restrictions</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="9586a-106">安全性</span><span class="sxs-lookup"><span data-stu-id="9586a-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9586a-107">**若要使用下列項目移除可用性資料庫：**</span><span class="sxs-lookup"><span data-stu-id="9586a-107">**To remove an availability database, using:**</span></span>  
  
     [<span data-ttu-id="9586a-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9586a-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9586a-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9586a-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="9586a-110">PowerShell</span><span class="sxs-lookup"><span data-stu-id="9586a-110">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="9586a-111">**待處理：**  [從可用性群組中移除可用性資料庫之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="9586a-111">**Follow Up:**  [After Removing an Availability Database from an Availability Group](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9586a-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="9586a-112">Before You Begin</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="9586a-113">必要條件和限制</span><span class="sxs-lookup"><span data-stu-id="9586a-113">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="9586a-114">只有在主要複本上才支援這個工作。</span><span class="sxs-lookup"><span data-stu-id="9586a-114">This task is supported only on primary replicas.</span></span> <span data-ttu-id="9586a-115">您必須連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="9586a-115">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9586a-116">Security</span><span class="sxs-lookup"><span data-stu-id="9586a-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9586a-117">權限</span><span class="sxs-lookup"><span data-stu-id="9586a-117">Permissions</span></span>  
 <span data-ttu-id="9586a-118">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="9586a-118">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9586a-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9586a-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="9586a-120">**若要移除可用性資料庫**</span><span class="sxs-lookup"><span data-stu-id="9586a-120">**To remove an availability database**</span></span>  
  
1.  <span data-ttu-id="9586a-121">在 [物件總管] 中，連接到裝載要移除資料庫之主要複本的伺服器執行個體，然後展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="9586a-121">In Object Explorer, connect to the server instance that hosts the primary replica of the database or databases to be removed, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="9586a-122">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="9586a-122">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="9586a-123">選取可用性群組，然後展開 **[可用性資料庫]** 節點。</span><span class="sxs-lookup"><span data-stu-id="9586a-123">Select the availability group, and expand the **Availability Databases** node.</span></span>  
  
4.  <span data-ttu-id="9586a-124">此步驟取決於您要移除多個資料庫群組或只要移除一個資料庫，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9586a-124">This step depends on whether you want to remove multiple databases groups or only one database, as follows:</span></span>  
  
    -   <span data-ttu-id="9586a-125">若要移除多個資料庫，請使用 **[物件總管詳細資料]** 窗格檢視及選取您要移除的所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="9586a-125">To remove multiple databases, use the **Object Explorer Details** pane to view and select all the databases that you want to remove.</span></span> <span data-ttu-id="9586a-126">如需詳細資訊，請參閱[使用物件總管詳細資料監視可用性群組 &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="9586a-126">For more information, see [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md).</span></span>  
  
    -   <span data-ttu-id="9586a-127">若要移除單一資料庫，請在 **[物件總管]** 窗格或 **[物件總管詳細資料]** 窗格中選取它。</span><span class="sxs-lookup"><span data-stu-id="9586a-127">To remove a single database, select it in either the **Object Explorer** pane or the **Object Explorer Details** pane.</span></span>  
  
5.  <span data-ttu-id="9586a-128">以滑鼠右鍵按一下選取的一或多個資料庫，然後在命令功能表中選取 [從可用性群組移除資料庫]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9586a-128">Right-click the selected database or databases, and select **Remove Database from Availability Group** in the command menu.</span></span>  
  
6.  <span data-ttu-id="9586a-129">在 **[從可用性群組移除資料庫]** 對話方塊中，若要移除所有列出的資料庫，請按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="9586a-129">In the **Remove Databases from Availability Group** dialog box, to remove all the listed databases, click **OK**.</span></span> <span data-ttu-id="9586a-130">如果您不要移除所有列出的資料庫，請按一下 **[取消]**。</span><span class="sxs-lookup"><span data-stu-id="9586a-130">If you do not want to remove all them, click **Cancel**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9586a-131">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9586a-131">Using Transact-SQL</span></span>  
 <span data-ttu-id="9586a-132">**若要移除可用性資料庫**</span><span class="sxs-lookup"><span data-stu-id="9586a-132">**To remove an availability database**</span></span>  
  
1.  <span data-ttu-id="9586a-133">連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="9586a-133">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="9586a-134">使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 陳述式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9586a-134">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="9586a-135">ALTER AVAILABILITY GROUP *group_name* REMOVE DATABASE *availability_database_name*</span><span class="sxs-lookup"><span data-stu-id="9586a-135">ALTER AVAILABILITY GROUP *group_name* REMOVE DATABASE *availability_database_name*</span></span>  
  
     <span data-ttu-id="9586a-136">*group_name* 是可用性群組的名稱，而 *database_name* 是要移除的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="9586a-136">where *group_name* is the name of the availability group and *database_name* is the name of the database to be removed.</span></span>  
  
     <span data-ttu-id="9586a-137">下列範例會從 `Db6` 可用性群組中移除名稱為 `MyAG` 的資料庫。</span><span class="sxs-lookup"><span data-stu-id="9586a-137">The following example removes a databases named `Db6` from the `MyAG` availability group.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAG REMOVE DATABASE Db6;  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="9586a-138">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9586a-138">Using PowerShell</span></span>  
 <span data-ttu-id="9586a-139">**若要移除可用性資料庫**</span><span class="sxs-lookup"><span data-stu-id="9586a-139">**To remove an availability database**</span></span>  
  
1.  <span data-ttu-id="9586a-140">變更目錄 (`cd`) 為裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="9586a-140">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="9586a-141">使用 `Remove-SqlAvailabilityDatabase` 指令程式，指定要從可用性群組移除的可用性資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="9586a-141">Use the `Remove-SqlAvailabilityDatabase` cmdlet, specifying the name of the availability database to be removed from the availability group.</span></span> <span data-ttu-id="9586a-142">連接到裝載主要複本的伺服器執行個體時，主要資料庫及其對應的次要資料庫都會從可用性群組中移除。</span><span class="sxs-lookup"><span data-stu-id="9586a-142">When you are connected to the server instance that hosts the primary replica, the primary database and its corresponding secondary databases are all removed from the availability group.</span></span>  
  
     <span data-ttu-id="9586a-143">例如，下列命令會將 `MyDb9` 可用性資料庫從名為 `MyAg`的可用性群組中移除。</span><span class="sxs-lookup"><span data-stu-id="9586a-143">For example, the following command removes the availability database `MyDb9` from the availability group named `MyAg`.</span></span> <span data-ttu-id="9586a-144">因為此命令是在裝載主要複本的伺服器執行個體上執行，所以系統會從可用性群組中移除主要資料庫及其所有對應的次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="9586a-144">Because the command is executed on the server instance that hosts the primary replica, the primary database and all its corresponding secondary databases are removed from the availability group.</span></span> <span data-ttu-id="9586a-145">系統將不再針對任何次要複本的這個資料庫進行資料同步處理。</span><span class="sxs-lookup"><span data-stu-id="9586a-145">Data synchronization will no longer occur for this database on any secondary replica.</span></span>  
  
    ```powershell
    Remove-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\PrimaryComputer\InstanceName\AvailabilityGroups\MyAg\Databases\MyDb9  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="9586a-146">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="9586a-146">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell environment.</span></span> <span data-ttu-id="9586a-147">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="9586a-147">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="9586a-148">**若要設定和使用 SQL Server PowerShell 提供者**</span><span class="sxs-lookup"><span data-stu-id="9586a-148">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="9586a-149">SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="9586a-149">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-removing-an-availability-database-from-an-availability-group"></a><a name="FollowUp"></a> <span data-ttu-id="9586a-150">待處理：從可用性群組中移除可用性資料庫之後</span><span class="sxs-lookup"><span data-stu-id="9586a-150">Follow Up: After Removing an Availability Database from an Availability Group</span></span>  
 <span data-ttu-id="9586a-151">從可用性群組中移除可用性資料庫，會結束先前主要資料庫和對應的次要資料庫之間的資料同步處理。</span><span class="sxs-lookup"><span data-stu-id="9586a-151">Removing an availability database from its availability group ends data synchronization between the former primary database and the corresponding secondary databases.</span></span> <span data-ttu-id="9586a-152">先前主要資料庫會保持上線狀態。</span><span class="sxs-lookup"><span data-stu-id="9586a-152">The former primary database remains online.</span></span> <span data-ttu-id="9586a-153">每個對應的次要資料庫處於 RESTORING 狀態。</span><span class="sxs-lookup"><span data-stu-id="9586a-153">Every corresponding secondary database is placed in the RESTORING state.</span></span>  
  
 <span data-ttu-id="9586a-154">此時有替代方法可處理移除的次要資料庫：</span><span class="sxs-lookup"><span data-stu-id="9586a-154">At this point there are alternative ways of dealing with a removed secondary database:</span></span>  
  
-   <span data-ttu-id="9586a-155">如果您不再需要給定的次要資料庫，可將它卸除。</span><span class="sxs-lookup"><span data-stu-id="9586a-155">If you no longer need a given secondary database, you can drop it.</span></span>  
  
     <span data-ttu-id="9586a-156">如需詳細資訊，請參閱 [刪除資料庫](../../../relational-databases/databases/delete-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="9586a-156">For more information, see [Delete a Database](../../../relational-databases/databases/delete-a-database.md).</span></span>  
  
-   <span data-ttu-id="9586a-157">從可用性群組中移除次要資料庫之後，若要存取移除的次要資料庫，可以復原資料庫。</span><span class="sxs-lookup"><span data-stu-id="9586a-157">If you want to access a removed secondary database after it has been removed from the availability group, you can recover the database.</span></span> <span data-ttu-id="9586a-158">不過，如果復原移除的次要資料庫，線上將會有兩個名稱相同但內容不同的獨立資料庫。</span><span class="sxs-lookup"><span data-stu-id="9586a-158">However, if you recover a removed secondary database, two divergent, independent databases that have the same name are online.</span></span> <span data-ttu-id="9586a-159">您必須確定用戶端只能存取其中一個資料庫 (通常是最新的主要資料庫)。</span><span class="sxs-lookup"><span data-stu-id="9586a-159">You must make sure that clients can access only one of them, typically the most recent primary database.</span></span>  
  
     <span data-ttu-id="9586a-160">如需詳細資訊，請參閱[復原資料庫而不還原資料 &#40;Transact-SQL&#41;](../../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="9586a-160">For more information, see [Recover a Database Without Restoring Data &#40;Transact-SQL&#41;](../../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9586a-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9586a-161">See Also</span></span>  
 <span data-ttu-id="9586a-162">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9586a-162">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="9586a-163">將次要資料庫從可用性群組移除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9586a-163">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
