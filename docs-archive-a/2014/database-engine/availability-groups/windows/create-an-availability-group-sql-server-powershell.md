---
title: 建立可用性群組 (SQL Server PowerShell) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: bc69a7df-20fa-41e1-9301-11317c5270d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3af9bf896b954e6849c0d491f9ed267655369ccb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710818"
---
# <a name="create-an-availability-group-sql-server-powershell"></a><span data-ttu-id="1d48d-102">建立可用性群組 (SQL Server PowerShell)</span><span class="sxs-lookup"><span data-stu-id="1d48d-102">Create an Availability Group (SQL Server PowerShell)</span></span>
  <span data-ttu-id="1d48d-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中的 PowerShell，透過 PowerShell 指令程式建立及設定 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="1d48d-103">This topic describes how to use PowerShell cmdlets to create and configure an AlwaysOn availability group by using PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="1d48d-104">*「可用性群組」* (Availability Group) 會定義當做單一單位容錯移轉的一組使用者資料庫，以及支援容錯移轉的一組容錯移轉夥伴 (也稱為 *「可用性複本」*(Availability Replica))。</span><span class="sxs-lookup"><span data-stu-id="1d48d-104">An *availability group* defines a set of user databases that will fail over as a single unit and a set of failover partners, known as *availability replicas*, which support failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1d48d-105">如需可用性群組的簡介，請參閱 [AlwaysOn 可用性群組概觀 &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1d48d-105">For an introduction to availability groups, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  

> [!NOTE]  
>  <span data-ttu-id="1d48d-106">若不使用 PowerShell 指令程式，您可以使用 [建立可用性群組精靈] 或 [!INCLUDE[tsql](../../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1d48d-106">As an alternative to using PowerShell cmdlets, you can use the Create Availability Group wizard or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="1d48d-107">如需詳細資訊，請參閱 [使用新增可用性群組對話方塊 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) 或 [建立可用性群組 &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)中的 PowerShell，透過 PowerShell Cmdlet 建立及設定 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="1d48d-107">For more information, see [Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) or [Create an Availability Group &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1d48d-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="1d48d-108">Before You Begin</span></span>  
 <span data-ttu-id="1d48d-109">我們強烈建議您先閱讀本節內容，然後再嘗試建立您的第一個可用性群組。</span><span class="sxs-lookup"><span data-stu-id="1d48d-109">We strongly recommend that you read this section before attempting to create your first availability group.</span></span>  
  
###  <a name="prerequisites-restrictions-and-recommendations"></a><a name="PrerequisitesRestrictions"></a> <span data-ttu-id="1d48d-110">必要條件、限制及建議</span><span class="sxs-lookup"><span data-stu-id="1d48d-110">Prerequisites, Restrictions, and Recommendations</span></span>  
  
-   <span data-ttu-id="1d48d-111">建立可用性群組之前，請確認 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 主機執行個體分別位於 Windows Server 容錯移轉叢集 (WSFC) 容錯移轉叢集的不同 WSFC 節點上。</span><span class="sxs-lookup"><span data-stu-id="1d48d-111">Before creating an availability group, verify that the host instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] each resides on a different Windows Server Failover Clustering (WSFC) node of a single WSFC failover cluster.</span></span> <span data-ttu-id="1d48d-112">此外，請確認您的伺服器執行個體符合其他伺服器執行個體必要條件和所有其他 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 需求，而且您了解建議事項。</span><span class="sxs-lookup"><span data-stu-id="1d48d-112">Also, verify that your server instances met the other server-instance prerequisites and that all of the other [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] requirements are meet and that you are aware of the recommendations.</span></span> <span data-ttu-id="1d48d-113">如需詳細資訊，強烈建議您閱讀 [AlwaysOn 可用性群組的必要條件、限制和建議 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="1d48d-113">For more information, we strongly recommend that you read [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1d48d-114">Security</span><span class="sxs-lookup"><span data-stu-id="1d48d-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1d48d-115">權限</span><span class="sxs-lookup"><span data-stu-id="1d48d-115">Permissions</span></span>  
 <span data-ttu-id="1d48d-116">需要 **系統管理員 (sysadmin)** 固定伺服器角色的成員資格，以及 CREATE AVAILABILITY GROUP 伺服器權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="1d48d-116">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
###  <a name="summary-of-tasks-and-corresponding-powershell-cmdlets"></a><a name="SummaryPSStatements"></a><span data-ttu-id="1d48d-117">工作和對應的 PowerShell Cmdlet 的摘要</span><span class="sxs-lookup"><span data-stu-id="1d48d-117">Summary of Tasks and Corresponding PowerShell Cmdlets</span></span>  
 <span data-ttu-id="1d48d-118">下表列出與設定可用性群組有關的基本工作，並指出 PowerShell 指令程式支援哪些工作。</span><span class="sxs-lookup"><span data-stu-id="1d48d-118">The following table lists the basic tasks involved in configuring an availability group and indicates those that are supported by PowerShell cmdlets.</span></span> <span data-ttu-id="1d48d-119">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 工作必須依照其出現在表格中的順序來執行。</span><span class="sxs-lookup"><span data-stu-id="1d48d-119">The [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] tasks must be performed in the sequence in which they are presented in the table.</span></span>  
  
|<span data-ttu-id="1d48d-120">Task</span><span class="sxs-lookup"><span data-stu-id="1d48d-120">Task</span></span>|<span data-ttu-id="1d48d-121">PowerShell 指令程式 (如果可用) 或 Transact-SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="1d48d-121">PowerShell Cmdlets (if Available) or Transact-SQL Statement</span></span>|<span data-ttu-id="1d48d-122">執行工作的位置**<sup>\*</sup>**</span><span class="sxs-lookup"><span data-stu-id="1d48d-122">Where to Perform Task**<sup>\*</sup>**</span></span>|  
|----------|--------------------------------------------------------------------|-------------------------------------------|  
|<span data-ttu-id="1d48d-123">建立資料庫鏡像端點 (每個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體一次)</span><span class="sxs-lookup"><span data-stu-id="1d48d-123">Create database mirroring endpoint (once per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance)</span></span>|`New-SqlHadrEndPoint`|<span data-ttu-id="1d48d-124">在缺少資料庫鏡像端點的每一個伺服器執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="1d48d-124">Execute on each server instance that lacks database mirroring endpoint.</span></span><br /><br /> <span data-ttu-id="1d48d-125">注意：若要變更現有資料庫鏡像端點，請使用 `Set-SqlHadrEndpoint`。</span><span class="sxs-lookup"><span data-stu-id="1d48d-125">Note: To alter an existing database mirroring endpoint, use `Set-SqlHadrEndpoint`.</span></span>|  
|<span data-ttu-id="1d48d-126">建立可用性群組</span><span class="sxs-lookup"><span data-stu-id="1d48d-126">Create availability group</span></span>|<span data-ttu-id="1d48d-127">首先，使用 `New-SqlAvailabilityReplica` 指令程式搭配 `-AsTemplate` 參數，針對您打算包含在可用性群組內之兩個可用性複本的每一個來建立記憶體內的可用性複本物件。</span><span class="sxs-lookup"><span data-stu-id="1d48d-127">First, use the `New-SqlAvailabilityReplica` cmdlet with the `-AsTemplate` parameter to create an in-memory availability-replica object for each of the two availability replicas that you plan to include in the availability group.</span></span><br /><br /> <span data-ttu-id="1d48d-128">然後，使用 `New-SqlAvailabilityGroup` 指令程式及參考可用性複本物件來建立可用性群組。</span><span class="sxs-lookup"><span data-stu-id="1d48d-128">Then, create the availability group by using the `New-SqlAvailabilityGroup` cmdlet and referencing your availability-replica objects.</span></span>|<span data-ttu-id="1d48d-129">於裝載初始主要複本的伺服器執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="1d48d-129">Execute on the server instance that is to host the initial primary replica.</span></span>|  
|<span data-ttu-id="1d48d-130">將次要複本加入可用性群組</span><span class="sxs-lookup"><span data-stu-id="1d48d-130">Join secondary replica to availability group</span></span>|`Join-SqlAvailabilityGroup`|<span data-ttu-id="1d48d-131">在裝載次要複本的每一個伺服器執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="1d48d-131">Execute on each server instance that is hosts a secondary replica.</span></span>|  
|<span data-ttu-id="1d48d-132">準備次要資料庫</span><span class="sxs-lookup"><span data-stu-id="1d48d-132">Prepare the secondary database</span></span>|<span data-ttu-id="1d48d-133">`Backup-SqlDatabase` 和 `Restore-SqlDatabase`</span><span class="sxs-lookup"><span data-stu-id="1d48d-133">`Backup-SqlDatabase` and `Restore-SqlDatabase`</span></span>|<span data-ttu-id="1d48d-134">在裝載主要複本的伺服器執行個體上建立備份。</span><span class="sxs-lookup"><span data-stu-id="1d48d-134">Create backups on the server instance that hosts the primary replica.</span></span><br /><br /> <span data-ttu-id="1d48d-135">使用 `NoRecovery` 還原參數，還原裝載次要複本之每個伺服器執行個體上的備份。</span><span class="sxs-lookup"><span data-stu-id="1d48d-135">Restore backups on each server instance that hosts a secondary replica, using the `NoRecovery` restore parameter.</span></span> <span data-ttu-id="1d48d-136">如果在裝載主要複本的電腦和裝載目標次要複本的電腦之間有檔案路徑差異，也要使用 `RelocateFile` 還原參數。</span><span class="sxs-lookup"><span data-stu-id="1d48d-136">If the file paths differ between the computers that host the primary replica and the target secondary replica, also use the `RelocateFile` restore parameter.</span></span>|  
|<span data-ttu-id="1d48d-137">將每一個次要資料庫加入可用性群組來啟動資料同步處理。</span><span class="sxs-lookup"><span data-stu-id="1d48d-137">Start data synchronization by joining each secondary database to availability group</span></span>|`Add-SqlAvailabilityDatabase`|<span data-ttu-id="1d48d-138">在裝載次要複本的每一個伺服器執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="1d48d-138">Execute on each server instance that hosts a secondary replica.</span></span>|  
  
 <span data-ttu-id="1d48d-139">**<sup>\*</sup>** 若要執行指定的工作，請將目錄 (`cd`) 變更為指定的伺服器實例。</span><span class="sxs-lookup"><span data-stu-id="1d48d-139">**<sup>\*</sup>**  To perform a given task, change directory (`cd`) to the indicated server instance or instances.</span></span>  
  
###  <a name="to-set-up-and-use-the-sql-server-powershell-provider"></a><a name="PsProviderLinks"></a><span data-ttu-id="1d48d-140">若要設定及使用 SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="1d48d-140">To Set Up and Use the SQL Server PowerShell Provider</span></span>  
  
-   [<span data-ttu-id="1d48d-141">SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="1d48d-141">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
-   [<span data-ttu-id="1d48d-142">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="1d48d-142">Get Help SQL Server PowerShell</span></span>](../../../powershell/sql-server-powershell.md)  
  
##  <a name="using-powershell-to-create-and-configure-an-availability-group"></a><a name="PowerShellProcedure"></a><span data-ttu-id="1d48d-143">使用 PowerShell 建立和設定可用性群組</span><span class="sxs-lookup"><span data-stu-id="1d48d-143">Using PowerShell to Create and Configure an Availability Group</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1d48d-144">若要檢視給定指令程式的語法和範例，請使用 `Get-Help` PowerShell 環境中的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="1d48d-144">To view the syntax and an example of a given cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="1d48d-145">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="1d48d-145">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
1.  <span data-ttu-id="1d48d-146">將目錄 (`cd`) 變更為要裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="1d48d-146">Change directory (`cd`) to the server instance that is to host the primary replica.</span></span>  
  
2.  <span data-ttu-id="1d48d-147">針對主要複本建立記憶體中的可用性複本物件。</span><span class="sxs-lookup"><span data-stu-id="1d48d-147">Create an in-memory availability-replica object for the primary replica.</span></span>  
  
3.  <span data-ttu-id="1d48d-148">針對每一個次要複本建立記憶體中的可用性複本物件。</span><span class="sxs-lookup"><span data-stu-id="1d48d-148">Create an in-memory availability-replica object for each of the secondary replicas.</span></span>  
  
4.  <span data-ttu-id="1d48d-149">建立可用性群組。</span><span class="sxs-lookup"><span data-stu-id="1d48d-149">Create the availability group.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1d48d-150">可用性群組名稱的最大長度為 128 個字元。</span><span class="sxs-lookup"><span data-stu-id="1d48d-150">The maximum length for an availability group name is 128 characters.</span></span>  
  
5.  <span data-ttu-id="1d48d-151">將新的次要複本加入可用性群組。</span><span class="sxs-lookup"><span data-stu-id="1d48d-151">Join the new secondary replica to the availability group.</span></span> <span data-ttu-id="1d48d-152">如需詳細資訊，請參閱 [將次要複本聯結至可用性群組 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1d48d-152">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
6.  <span data-ttu-id="1d48d-153">如果是可用性群組中的每個資料庫，請使用 RESTORE WITH NORECOVERY 還原主要資料庫的最近備份來建立次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="1d48d-153">For each database in the availability group, create a secondary database by restoring recent backups of the primary database, using RESTORE WITH NORECOVERY.</span></span>  
  
7.  <span data-ttu-id="1d48d-154">將每一個新的次要資料庫加入可用性群組。</span><span class="sxs-lookup"><span data-stu-id="1d48d-154">Join every new secondary database to the availability group.</span></span> <span data-ttu-id="1d48d-155">如需詳細資訊，請參閱 [將次要複本聯結至可用性群組 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1d48d-155">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
8.  <span data-ttu-id="1d48d-156">您可以選擇使用 Windows `dir` 命令來確認新的可用性群組的內容。</span><span class="sxs-lookup"><span data-stu-id="1d48d-156">Optionally, use the Windows `dir` command to verify the contents of the new availability group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1d48d-157">如果伺服器執行個體的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務帳戶在不同的網域使用者帳戶下執行，請在每一個伺服器執行個體上建立其他伺服器執行個體的登入，並將此登入 CONNECT 權限授與本機資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="1d48d-157">If the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service accounts of the server instances run under different domain user accounts, on each server instance, create a login for the other server instance and grant this login CONNECT permission to the local database mirroring endpoint.</span></span>  
  
##  <a name="example-using-powershell-to-create-an-availability-group"></a><a name="ExampleConfigureGroup"></a><span data-ttu-id="1d48d-158">範例：使用 PowerShell 建立可用性群組</span><span class="sxs-lookup"><span data-stu-id="1d48d-158">Example: Using PowerShell to Create an Availability Group</span></span>  
 <span data-ttu-id="1d48d-159">下列 PowerShell 範例會建立及設定一個名為 `MyAG` 的簡單可用性群組，其包含兩個可用性複本和一個可用性資料庫。</span><span class="sxs-lookup"><span data-stu-id="1d48d-159">The following PowerShell example creates and configures a simple availability group named `MyAG` with two availability replicas and one availability database.</span></span> <span data-ttu-id="1d48d-160">範例：</span><span class="sxs-lookup"><span data-stu-id="1d48d-160">The example:</span></span>  
  
1.  <span data-ttu-id="1d48d-161">備份 `MyDatabase` 及其交易記錄。</span><span class="sxs-lookup"><span data-stu-id="1d48d-161">Backs up `MyDatabase` and its transaction log.</span></span>  
  
2.  <span data-ttu-id="1d48d-162">使用 `MyDatabase` 選項還原 `-NoRecovery` 和其交易記錄。</span><span class="sxs-lookup"><span data-stu-id="1d48d-162">Restores `MyDatabase` and its transaction log, using the `-NoRecovery` option.</span></span>  
  
3.  <span data-ttu-id="1d48d-163">建立主要複本的記憶體內表示法，此主要複本將由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 本機執行個體 (名為 `PrimaryComputer\Instance`) 所裝載。</span><span class="sxs-lookup"><span data-stu-id="1d48d-163">Creates an in-memory representation of the primary replica, which will be hosted by the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (named `PrimaryComputer\Instance`).</span></span>  
  
4.  <span data-ttu-id="1d48d-164">建立次要複本的記憶體內表示法，此次要複本將由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體 (名為 `SecondaryComputer\Instance`) 所裝載。</span><span class="sxs-lookup"><span data-stu-id="1d48d-164">Creates an in-memory representation of the secondary replica, which will be hosted by an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (named `SecondaryComputer\Instance`).</span></span>  
  
5.  <span data-ttu-id="1d48d-165">建立名為 `MyAG`的可用性群組。</span><span class="sxs-lookup"><span data-stu-id="1d48d-165">Creates an availability group named `MyAG`.</span></span>  
  
6.  <span data-ttu-id="1d48d-166">將次要複本聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="1d48d-166">Joins the secondary replica to the availability group.</span></span>  
  
7.  <span data-ttu-id="1d48d-167">將次要資料庫加入可用性群組。</span><span class="sxs-lookup"><span data-stu-id="1d48d-167">Joins the secondary database to the availability group.</span></span>  
  
```powershell
# Backup my database and its log on the primary  
Backup-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.bak" `  
    -ServerInstance "PrimaryComputer\Instance"  
  
Backup-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.log" `  
    -ServerInstance "PrimaryComputer\Instance" `  
    -BackupAction Log   
  
# Restore the database and log on the secondary (using NO RECOVERY)  
Restore-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.bak" `  
    -ServerInstance "SecondaryComputer\Instance" `  
    -NoRecovery  
  
Restore-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.log" `  
    -ServerInstance "SecondaryComputer\Instance" `  
    -RestoreAction Log `  
    -NoRecovery  
  
# Create an in-memory representation of the primary replica.  
$primaryReplica = New-SqlAvailabilityReplica `  
    -Name "PrimaryComputer\Instance" `  
    -EndpointURL "TCP://PrimaryComputer.domain.com:5022" `  
    -AvailabilityMode "SynchronousCommit" `  
    -FailoverMode "Automatic" `  
    -Version 12 `  
    -AsTemplate  
  
# Create an in-memory representation of the secondary replica.  
$secondaryReplica = New-SqlAvailabilityReplica `  
    -Name "SecondaryComputer\Instance" `  
    -EndpointURL "TCP://SecondaryComputer.domain.com:5022" `  
    -AvailabilityMode "SynchronousCommit" `  
    -FailoverMode "Automatic" `  
    -Version 12 `  
    -AsTemplate  
  
# Create the availability group  
New-SqlAvailabilityGroup `  
    -Name "MyAG" `  
    -Path "SQLSERVER:\SQL\PrimaryComputer\Instance" `  
    -AvailabilityReplica @($primaryReplica,$secondaryReplica) `  
    -Database "MyDatabase"  
  
# Join the secondary replica to the availability group.  
Join-SqlAvailabilityGroup -Path "SQLSERVER:\SQL\SecondaryComputer\Instance" -Name "MyAG"  
  
# Join the secondary database to the availability group.  
Add-SqlAvailabilityDatabase -Path "SQLSERVER:\SQL\SecondaryComputer\Instance\AvailabilityGroups\MyAG" -Database "MyDatabase"  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="1d48d-168">相關工作</span><span class="sxs-lookup"><span data-stu-id="1d48d-168">Related Tasks</span></span>  
 <span data-ttu-id="1d48d-169">**若要設定 AlwaysOn 可用性群組的伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="1d48d-169">**To configure a server instance for AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="1d48d-170">啟用和停用 AlwaysOn 可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1d48d-170">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="1d48d-171">建立 AlwaysOn 可用性群組 &#40;SQL Server PowerShell 的資料庫鏡像端點&#41;</span><span class="sxs-lookup"><span data-stu-id="1d48d-171">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
 <span data-ttu-id="1d48d-172">**若要設定可用性群組和複本屬性**</span><span class="sxs-lookup"><span data-stu-id="1d48d-172">**To configure availability group and replica properties**</span></span>  
  
-   [<span data-ttu-id="1d48d-173">變更可用性複本的可用性模式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1d48d-173">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="1d48d-174">變更可用性複本的容錯移轉模式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1d48d-174">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="1d48d-175">建立或設定可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1d48d-175">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="1d48d-176">設定彈性容錯移轉原則以控制自動容錯移轉的條件 (AlwaysOn 可用性群組)</span><span class="sxs-lookup"><span data-stu-id="1d48d-176">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (AlwaysOn Availability Groups)</span></span>](configure-flexible-automatic-failover-policy.md)  
  
-   [<span data-ttu-id="1d48d-177">在新增或修改可用性複本時指定端點 URL &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1d48d-177">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="1d48d-178">設定可用性複本的備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1d48d-178">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="1d48d-179">設定可用性複本的唯讀存取 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1d48d-179">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="1d48d-180">設定可用性群組的唯讀路由 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1d48d-180">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="1d48d-181">變更可用性複本的工作階段逾時期限 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1d48d-181">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 <span data-ttu-id="1d48d-182">**若要完成可用性群組組態**</span><span class="sxs-lookup"><span data-stu-id="1d48d-182">**To complete availability group configuration**</span></span>  
  
-   [<span data-ttu-id="1d48d-183">將次要複本聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1d48d-183">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="1d48d-184">針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1d48d-184">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="1d48d-185">將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1d48d-185">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="1d48d-186">建立或設定可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1d48d-186">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 <span data-ttu-id="1d48d-187">**建立可用性群組的其他方法**</span><span class="sxs-lookup"><span data-stu-id="1d48d-187">**Alternative ways to create an availability group**</span></span>  
  
-   [<span data-ttu-id="1d48d-188">使用可用性群組精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="1d48d-188">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="1d48d-189">使用新增可用性群組對話方塊 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="1d48d-189">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="1d48d-190">建立可用性群組 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1d48d-190">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
 <span data-ttu-id="1d48d-191">**若要疑難排解 AlwaysOn 可用性群組組態**</span><span class="sxs-lookup"><span data-stu-id="1d48d-191">**To troubleshoot AlwaysOn Availability Groups configuration**</span></span>  
  
-   [<span data-ttu-id="1d48d-192">針對 AlwaysOn 可用性群組 Configuration (SQL Server) 已刪除進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="1d48d-192">Troubleshoot AlwaysOn Availability Groups Configuration (SQL Server)deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [<span data-ttu-id="1d48d-193">針對失敗的新增檔案作業進行疑難排解 &#40;AlwaysOn 可用性群組&#41;</span><span class="sxs-lookup"><span data-stu-id="1d48d-193">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="1d48d-194">相關內容</span><span class="sxs-lookup"><span data-stu-id="1d48d-194">Related Content</span></span>  
  
-   <span data-ttu-id="1d48d-195">**部落格：**</span><span class="sxs-lookup"><span data-stu-id="1d48d-195">**Blogs:**</span></span>  
  
     [<span data-ttu-id="1d48d-196">AlwaysON - HADRON 學習系列：具備 HADRON 功能之資料庫的工作者集區使用方式</span><span class="sxs-lookup"><span data-stu-id="1d48d-196">AlwaysON - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases</span></span>](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [<span data-ttu-id="1d48d-197">使用 SQL Server PowerShell 設定 AlwaysOn</span><span class="sxs-lookup"><span data-stu-id="1d48d-197">Configuring AlwaysOn with SQL Server PowerShell</span></span>](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/configuring-alwayson-with-sql-server-powershell.aspx)  
  
     [<span data-ttu-id="1d48d-198">SQL Server AlwaysOn 團隊部落格：官方 SQL Server AlwaysOn 團隊部落格</span><span class="sxs-lookup"><span data-stu-id="1d48d-198">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="1d48d-199">CSS SQL Server 工程師部落格</span><span class="sxs-lookup"><span data-stu-id="1d48d-199">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="1d48d-200">**影片：**</span><span class="sxs-lookup"><span data-stu-id="1d48d-200">**Videos:**</span></span>  
  
     [<span data-ttu-id="1d48d-201">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第 1 部：新一代高可用性解決方案簡介</span><span class="sxs-lookup"><span data-stu-id="1d48d-201">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="1d48d-202">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第 2 部：使用 AlwaysOn 建立關鍵任務的高可用性方案</span><span class="sxs-lookup"><span data-stu-id="1d48d-202">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="1d48d-203">**白皮書：**</span><span class="sxs-lookup"><span data-stu-id="1d48d-203">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="1d48d-204">Microsoft SQL Server AlwaysOn 高可用性和災害復原方案指南</span><span class="sxs-lookup"><span data-stu-id="1d48d-204">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="1d48d-205">Microsoft 的 SQL Server 2012 白皮書</span><span class="sxs-lookup"><span data-stu-id="1d48d-205">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="1d48d-206">SQL Server 客戶諮詢團隊白皮書</span><span class="sxs-lookup"><span data-stu-id="1d48d-206">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="1d48d-207">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d48d-207">See Also</span></span>  
 [<span data-ttu-id="1d48d-208">資料庫鏡像端點 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1d48d-208">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
