---
title: 將資料庫新增至可用性群組 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: 2a54eef8-9e8e-4e04-909c-6970112d55cc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0907cf711cac65ad77a8948841d92705fdc1eac9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585625"
---
# <a name="add-a-database-to-an-availability-group-sql-server"></a><span data-ttu-id="1f6c1-102">將資料庫加入至可用性群組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1f6c1-102">Add a Database to an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="1f6c1-103">本主題描述如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]或 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中的 PowerShell，將資料庫加入至 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-103">This topic describes how to add a database to an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="1f6c1-104">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="1f6c1-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1f6c1-105">必要條件和限制</span><span class="sxs-lookup"><span data-stu-id="1f6c1-105">Prerequisites and Restrictions</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="1f6c1-106">權限</span><span class="sxs-lookup"><span data-stu-id="1f6c1-106">Permissions</span></span>](#Permissions)  
  
-   <span data-ttu-id="1f6c1-107">**若要使用下列項目，將資料庫加入至可用性群組：**</span><span class="sxs-lookup"><span data-stu-id="1f6c1-107">**To add a database to an availability group, using:**</span></span>  
  
     [<span data-ttu-id="1f6c1-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1f6c1-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1f6c1-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1f6c1-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="1f6c1-110">PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f6c1-110">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1f6c1-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="1f6c1-111">Before You Begin</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="1f6c1-112">必要條件和限制</span><span class="sxs-lookup"><span data-stu-id="1f6c1-112">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="1f6c1-113">您必須連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-113">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
-   <span data-ttu-id="1f6c1-114">資料庫必須位於裝載主要複本的伺服器執行個體上，且符合可用性資料庫的必要條件和限制。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-114">The database must reside on the server instance that hosts the primary replica and comply with the prerequisites and restrictions for availability databases.</span></span> <span data-ttu-id="1f6c1-115">如需詳細資訊，請參閱 [AlwaysOn 可用性群組的必要條件、限制和建議 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-115">For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1f6c1-116">Security</span><span class="sxs-lookup"><span data-stu-id="1f6c1-116">Security</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1f6c1-117">權限</span><span class="sxs-lookup"><span data-stu-id="1f6c1-117">Permissions</span></span>  
 <span data-ttu-id="1f6c1-118">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-118">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1f6c1-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1f6c1-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="1f6c1-120">**若要將資料庫加入至可用性群組**</span><span class="sxs-lookup"><span data-stu-id="1f6c1-120">**To add a database to an availability group**</span></span>  
  
1.  <span data-ttu-id="1f6c1-121">在 [物件總管] 中，連接到裝載主要複本的伺服器執行個體，然後展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-121">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="1f6c1-122">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-122">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="1f6c1-123">以滑鼠右鍵按一下可用性群組，然後選取下列其中一個命令：</span><span class="sxs-lookup"><span data-stu-id="1f6c1-123">Right-click the availability group, and select one of the following commands:</span></span>  
  
    -   <span data-ttu-id="1f6c1-124">若要啟動「將資料庫加入至可用性群組精靈」，選取 **[加入資料庫]** 命令。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-124">To launch the Add Database to Availability Group Wizard, select the **Add Database** command.</span></span> <span data-ttu-id="1f6c1-125">如需詳細資訊，請參閱[使用 [將資料庫加入至可用性群組精靈] &#40;SQL Server Management Studio&#41;](availability-group-add-database-to-group-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-125">For more information, see [Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;](availability-group-add-database-to-group-wizard.md).</span></span>  
  
    -   <span data-ttu-id="1f6c1-126">若要在 **[可用性群組屬性]** 對話方塊中指定一個或多個資料庫來加入這些資料庫，選取 **[屬性]** 命令。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-126">To add one or more databases by specifying them in the **Availability Group Properties** dialog box, select the **Properties** command.</span></span> <span data-ttu-id="1f6c1-127">加入資料庫的步驟如下所示：</span><span class="sxs-lookup"><span data-stu-id="1f6c1-127">The steps for adding a database are as follows:</span></span>  
  
        1.  <span data-ttu-id="1f6c1-128">在 **[可用性資料庫]** 窗格中，按一下 **[加入]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-128">In the **Availability Databases** pane, click the **Add** button.</span></span> <span data-ttu-id="1f6c1-129">這樣會建立並選取一個空白資料庫欄位。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-129">This creates and selects a blank database field.</span></span>  
  
        2.  <span data-ttu-id="1f6c1-130">輸入符合可用性資料庫必要條件之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-130">Enter the name of a database that meets the availability-databases prerequisites.</span></span>  
  
         <span data-ttu-id="1f6c1-131">若要加入另一個資料庫，請重複上述步驟。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-131">To add another database, repeat the preceding steps.</span></span> <span data-ttu-id="1f6c1-132">當您指定好資料庫時，按一下 **[確定]** 以完成該作業。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-132">When you are done specifying databases, click **OK** to complete the operation.</span></span>  
  
         <span data-ttu-id="1f6c1-133">使用 **[可用性群組屬性]** 對話方塊將資料庫加入至可用性群組之後，您需要在裝載次要複本的每個伺服器執行個體上設定對應的次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-133">After you use the **Availability Group Properties** dialog box to add a database to an availability group, you need to configure the corresponding secondary database on each server instance that hosts a secondary replica.</span></span> <span data-ttu-id="1f6c1-134">如需詳細資訊，請參閱[於 AlwaysOn 次要資料庫啟動資料移動 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-134">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1f6c1-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1f6c1-135">Using Transact-SQL</span></span>  
 <span data-ttu-id="1f6c1-136">**若要將資料庫加入至可用性群組**</span><span class="sxs-lookup"><span data-stu-id="1f6c1-136">**To add a database to an availability group**</span></span>  
  
1.  <span data-ttu-id="1f6c1-137">連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-137">Connect to the server instance that hosts the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="1f6c1-138">使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 陳述式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1f6c1-138">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="1f6c1-139">ALTER AVAILABILITY GROUP *group_name* ADD DATABASE *database_name* [,...*n*]</span><span class="sxs-lookup"><span data-stu-id="1f6c1-139">ALTER AVAILABILITY GROUP *group_name* ADD DATABASE *database_name* [,...*n*]</span></span>  
  
     <span data-ttu-id="1f6c1-140">其中 *group_name* 是可用性群組的名稱，而 *database_name* 是要加入群組中之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-140">where *group_name* is the name of the availability group and *database_name* is the name of a database to be added to the group.</span></span>  
  
     <span data-ttu-id="1f6c1-141">下列範例會將 *MyDb3* 資料庫加入 *MyAG* 可用性群組中。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-141">The following example adds the *MyDb3* database to the *MyAG* availability group.</span></span>  
  
    ```  
    -- Connect to the server instance that hosts the primary replica.  
    -- Add an existing database to the availability group.  
    ALTER AVAILABILITY GROUP MyAG ADD DATABASE MyDb3;  
    GO  
    ```  
  
3.  <span data-ttu-id="1f6c1-142">將資料庫加入至可用性群組之後，您需要在裝載次要複本的每個伺服器執行個體上設定對應的次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-142">After you add a database to an availability group, you need to configure the corresponding secondary database on each server instance that hosts a secondary replica.</span></span> <span data-ttu-id="1f6c1-143">如需詳細資訊，請參閱[於 AlwaysOn 次要資料庫啟動資料移動 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-143">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="1f6c1-144">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f6c1-144">Using PowerShell</span></span>  
 <span data-ttu-id="1f6c1-145">**若要將資料庫加入至可用性群組**</span><span class="sxs-lookup"><span data-stu-id="1f6c1-145">**To add a database to an availability group**</span></span>  
  
1.  <span data-ttu-id="1f6c1-146">變更目錄 (`cd`) 為裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-146">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="1f6c1-147">使用 `Add-SqlAvailabilityDatabase` 指令程式。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-147">Use the `Add-SqlAvailabilityDatabase` cmdlet.</span></span>  
  
     <span data-ttu-id="1f6c1-148">例如，下列命令會將次要資料庫 `MyDd` 加入 `MyAG` 可用性群組中，而其主要複本是由 `PrimaryServer\InstanceName`裝載。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-148">For example, the following command adds the secondary database `MyDd` to the `MyAG` availability group, whose primary replica is hosted by `PrimaryServer\InstanceName`.</span></span>  
  
    ```powershell
    Add-SqlAvailabilityDatabase `   
     -Path SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAG `   
     -Database "MyDb"  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="1f6c1-149">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-149">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="1f6c1-150">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-150">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
3.  <span data-ttu-id="1f6c1-151">將資料庫加入至可用性群組之後，您需要在裝載次要複本的每個伺服器執行個體上設定對應的次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-151">After you add a database to an availability group, you need to configure the corresponding secondary database on each server instance that hosts a secondary replica.</span></span> <span data-ttu-id="1f6c1-152">如需詳細資訊，請參閱[於 AlwaysOn 次要資料庫啟動資料移動 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-152">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
 <span data-ttu-id="1f6c1-153">若要設定及使用 SQL Server PowerShell 提供者，請參閱[SQL Server PowerShell 提供者](../../../powershell/sql-server-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-153">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>

 <span data-ttu-id="1f6c1-154">下列範例示範此完整程序：根據裝載可用性群組之主要複本的伺服器執行個體上的資料庫準備次要資料庫、將資料庫加入至可用性群組 (做為主要資料庫)，然後將次要資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-154">The following example shows the full process for preparing a secondary database from a database on the server instance that hosts the primary replica of an availability group, adding the database to an availability group (as a primary database), and then joining the secondary database to the availability group.</span></span> <span data-ttu-id="1f6c1-155">首先，此範例會備份資料庫及其交易記錄。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-155">First, the example backs up the database and its transaction log.</span></span> <span data-ttu-id="1f6c1-156">然後，此範例會將資料庫和記錄備份還原至裝載次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-156">Then the example restores the database and log backups to the server instances that host a secondary replica.</span></span>  
  
 <span data-ttu-id="1f6c1-157">此範例會呼叫 `Add-SqlAvailabilityDatabase` 兩次：第一次是針對主要複本呼叫，以便將資料庫加入至可用性群組，然後再針對次要複本呼叫，以便將該複本的次要資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-157">The example calls `Add-SqlAvailabilityDatabase` twice: first on the primary replica to add the database to the availability group, and then on the secondary replica to join the secondary database on that replica to the availability group.</span></span> <span data-ttu-id="1f6c1-158">如果您有多個次要複本，請還原並聯結每個次要複本的次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="1f6c1-158">If you have more than one secondary replica, restore and join the secondary database on each of them.</span></span>  
  
```powershell
$DatabaseBackupFile = "\\share\backups\MyDatabase.bak"  
$LogBackupFile = "\\share\backups\MyDatabase.trn"  
$MyAgPrimaryPath = "SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAg"  
$MyAgSecondaryPath = "SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MyAg"  
  
Backup-SqlDatabase -Database "MyDatabase" -BackupFile $DatabaseBackupFile -ServerInstance "PrimaryServer\InstanceName"  
Backup-SqlDatabase -Database "MyDatabase" -BackupFile $LogBackupFile -ServerInstance "PrimaryServer\InstanceName" -BackupAction 'Log'  
  
Restore-SqlDatabase -Database "MyDatabase" -BackupFile $DatabaseBackupFile -ServerInstance "SecondaryServer\InstanceName" -NoRecovery  
Restore-SqlDatabase -Database "MyDatabase" -BackupFile $LogBackupFile -ServerInstance "SecondaryServer\InstanceName" -RestoreAction 'Log' -NoRecovery  
  
Add-SqlAvailabilityDatabase -Path $MyAgPrimaryPath -Database "MyDatabase"  
Add-SqlAvailabilityDatabase -Path $MyAgSecondaryPath -Database "MyDatabase"
```  
  
## <a name="see-also"></a><span data-ttu-id="1f6c1-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f6c1-159">See Also</span></span>  
 <span data-ttu-id="1f6c1-160">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1f6c1-160">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="1f6c1-161">[建立及設定可用性群組 &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1f6c1-161">[Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="1f6c1-162">[使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="1f6c1-162">[Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="1f6c1-163">監視可用性群組 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1f6c1-163">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
