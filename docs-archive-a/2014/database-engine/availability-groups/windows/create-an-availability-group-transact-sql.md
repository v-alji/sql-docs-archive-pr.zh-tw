---
title: 建立可用性群組 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: 8b0a6301-8b79-4415-b608-b40876f30066
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 57a494af168a8f5572bafe93f8fb47b22a954a19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710813"
---
# <a name="create-an-availability-group-transact-sql"></a><span data-ttu-id="a8783-102">建立可用性群組 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a8783-102">Create an Availability Group (Transact-SQL)</span></span>
  <span data-ttu-id="a8783-103">此主題描述如何使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 執行個體上建立和設定已啟用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 功能的可用性群組。</span><span class="sxs-lookup"><span data-stu-id="a8783-103">This topic describes how to use [!INCLUDE[tsql](../../../includes/tsql-md.md)] to create and configure an availability group on instances of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] on which the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature is enabled.</span></span> <span data-ttu-id="a8783-104">*「可用性群組」* (Availability Group) 會定義當做單一單位容錯移轉的一組使用者資料庫，以及支援容錯移轉的一組容錯移轉夥伴 (也稱為 *「可用性複本」* (Availability Replica))。</span><span class="sxs-lookup"><span data-stu-id="a8783-104">An *availability group* defines a set of user databases that will fail over as a single unit and a set of failover partners, known as *availability replicas*, that support failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8783-105">如需可用性群組的簡介，請參閱 [AlwaysOn 可用性群組概觀 &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a8783-105">For an introduction to availability groups, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  

> [!NOTE]  
>  <span data-ttu-id="a8783-106">[!INCLUDE[tsql](../../../includes/tsql-md.md)]以外的替代方案是，使用 [建立可用性群組精靈] 或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 指令程式。</span><span class="sxs-lookup"><span data-stu-id="a8783-106">As an alternative to using [!INCLUDE[tsql](../../../includes/tsql-md.md)], you can use the Create Availability Group wizard or [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell cmdlets.</span></span> <span data-ttu-id="a8783-107">如需詳細資訊，請參閱 [使用可用性群組精靈 &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)、 [使用新增可用性群組對話方塊 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)或 [建立可用性群組 &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="a8783-107">For more information, see [Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md), [Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md), or [Create an Availability Group &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a8783-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="a8783-108">Before You Begin</span></span>  
 <span data-ttu-id="a8783-109">我們強烈建議您先閱讀本節內容，然後再嘗試建立您的第一個可用性群組。</span><span class="sxs-lookup"><span data-stu-id="a8783-109">We strongly recommend that you read this section before attempting to create your first availability group.</span></span>  
  
###  <a name="prerequisites-restrictions-and-recommendations"></a><a name="PrerequisitesRestrictions"></a><span data-ttu-id="a8783-110">必要條件、限制和建議</span><span class="sxs-lookup"><span data-stu-id="a8783-110">Prerequisites, Restrictions, and Recommendations</span></span>  
  
-   <span data-ttu-id="a8783-111">建立可用性群組之前，請確認裝載可用性複本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體位於相同 Windows Server 容錯移轉叢集 (WSFC) 容錯移轉叢集的不同 WSFC 節點上。</span><span class="sxs-lookup"><span data-stu-id="a8783-111">Before creating an availability group, verify that the instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that host availability replicas reside on different Windows Server Failover Clustering (WSFC) node within the same WSFC failover cluster.</span></span> <span data-ttu-id="a8783-112">此外，請確認每個伺服器執行個體都符合所有其他 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 必要條件。</span><span class="sxs-lookup"><span data-stu-id="a8783-112">Also, verify that each of the server instance meets all other [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prerequisites.</span></span> <span data-ttu-id="a8783-113">如需詳細資訊，強烈建議您閱讀 [AlwaysOn 可用性群組的必要條件、限制和建議 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="a8783-113">For more information, we strongly recommend that you read [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a8783-114">Security</span><span class="sxs-lookup"><span data-stu-id="a8783-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a8783-115">權限</span><span class="sxs-lookup"><span data-stu-id="a8783-115">Permissions</span></span>  
 <span data-ttu-id="a8783-116">需要 **系統管理員 (sysadmin)** 固定伺服器角色的成員資格，以及 CREATE AVAILABILITY GROUP 伺服器權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="a8783-116">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
###  <a name="summary-of-tasks-and-corresponding-transact-sql-statements"></a><a name="SummaryTsqlStatements"></a> <span data-ttu-id="a8783-117">工作和對應 Transact-SQL 陳述式的摘要</span><span class="sxs-lookup"><span data-stu-id="a8783-117">Summary of Tasks and Corresponding Transact-SQL Statements</span></span>  
 <span data-ttu-id="a8783-118">下表列出與建立和設定可用性群組有關的基本工作，並指出哪些 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式要用於這些工作。</span><span class="sxs-lookup"><span data-stu-id="a8783-118">The following table lists the basic tasks involved in creating and configuring an availability group and indicates which [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements to use for these tasks.</span></span> <span data-ttu-id="a8783-119">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 工作必須依照其出現在表格中的順序來執行。</span><span class="sxs-lookup"><span data-stu-id="a8783-119">The [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] tasks must be performed in the sequence in which they are presented in the table.</span></span>  
  
|<span data-ttu-id="a8783-120">Task</span><span class="sxs-lookup"><span data-stu-id="a8783-120">Task</span></span>|<span data-ttu-id="a8783-121">Transact-SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="a8783-121">Transact-SQL Statement(s)</span></span>|<span data-ttu-id="a8783-122">執行工作的位置**<sup>\*</sup>**</span><span class="sxs-lookup"><span data-stu-id="a8783-122">Where to Perform Task**<sup>\*</sup>**</span></span>|  
|----------|----------------------------------|-------------------------------------------|  
|<span data-ttu-id="a8783-123">建立資料庫鏡像端點 (每個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體一次)</span><span class="sxs-lookup"><span data-stu-id="a8783-123">Create database mirroring endpoint (once per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance)</span></span>|<span data-ttu-id="a8783-124">[建立端點終結點](/sql/t-sql/statements/create-endpoint-transact-sql) *...* 針對 DATABASE_MIRRORING</span><span class="sxs-lookup"><span data-stu-id="a8783-124">[CREATE ENDPOINT](/sql/t-sql/statements/create-endpoint-transact-sql) *endpointName* ... FOR DATABASE_MIRRORING</span></span>|<span data-ttu-id="a8783-125">在缺少資料庫鏡像端點的每一個伺服器執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="a8783-125">Execute on each server instance that lacks database mirroring endpoint.</span></span>|  
|<span data-ttu-id="a8783-126">建立可用性群組</span><span class="sxs-lookup"><span data-stu-id="a8783-126">Create availability group</span></span>|[<span data-ttu-id="a8783-127">CREATE AVAILABILITY GROUP</span><span class="sxs-lookup"><span data-stu-id="a8783-127">CREATE AVAILABILITY GROUP</span></span>](/sql/t-sql/statements/create-availability-group-transact-sql)|<span data-ttu-id="a8783-128">於裝載初始主要複本的伺服器執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="a8783-128">Execute on the server instance that is to host the initial primary replica.</span></span>|  
|<span data-ttu-id="a8783-129">將次要複本加入可用性群組</span><span class="sxs-lookup"><span data-stu-id="a8783-129">Join secondary replica to availability group</span></span>|<span data-ttu-id="a8783-130">[ALTER AVAILABILITY GROUP 群組名稱](join-a-secondary-replica-to-an-availability-group-sql-server.md) \*\* JOIN</span><span class="sxs-lookup"><span data-stu-id="a8783-130">[ALTER AVAILABILITY GROUP](join-a-secondary-replica-to-an-availability-group-sql-server.md) *group_name* JOIN</span></span>|<span data-ttu-id="a8783-131">在裝載次要複本的每一個伺服器執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="a8783-131">Execute on each server instance that hosts a secondary replica.</span></span>|  
|<span data-ttu-id="a8783-132">準備次要資料庫</span><span class="sxs-lookup"><span data-stu-id="a8783-132">Prepare the secondary database</span></span>|<span data-ttu-id="a8783-133">[備份](/sql/t-sql/statements/backup-transact-sql)與[還原](/sql/t-sql/statements/restore-statements-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a8783-133">[BACKUP](/sql/t-sql/statements/backup-transact-sql) and [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>|<span data-ttu-id="a8783-134">在裝載主要複本的伺服器執行個體上建立備份。</span><span class="sxs-lookup"><span data-stu-id="a8783-134">Create backups on the server instance that hosts the primary replica.</span></span><br /><br /> <span data-ttu-id="a8783-135">使用 RESTORE WITH NORECOVERY，還原裝載次要複本之每個伺服器執行個體上的備份。</span><span class="sxs-lookup"><span data-stu-id="a8783-135">Restore backups on each server instance that hosts a secondary replica, using RESTORE WITH NORECOVERY.</span></span>|  
|<span data-ttu-id="a8783-136">將每一個次要資料庫加入可用性群組來啟動資料同步處理。</span><span class="sxs-lookup"><span data-stu-id="a8783-136">Start data synchronization by joining each secondary database to availability group</span></span>|<span data-ttu-id="a8783-137">[ALTER DATABASE 資料庫名稱](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) \*\* SET HADR AVAILABILITY GROUP = 群組名稱\*\*</span><span class="sxs-lookup"><span data-stu-id="a8783-137">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) *database_name* SET HADR AVAILABILITY GROUP = *group_name*</span></span>|<span data-ttu-id="a8783-138">在裝載次要複本的每一個伺服器執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="a8783-138">Execute on each server instance that hosts a secondary replica.</span></span>|  
  
 <span data-ttu-id="a8783-139">**<sup>\*</sup>** 若要執行指定的工作，請連接到指定的伺服器實例。</span><span class="sxs-lookup"><span data-stu-id="a8783-139">**<sup>\*</sup>**  To perform a given task, connect to the indicated server instance or instances.</span></span>  
  
##  <a name="using-transact-sql-to-create-and-configure-an-availability-group"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a8783-140">使用 Transact-SQL 建立和設定可用性群組</span><span class="sxs-lookup"><span data-stu-id="a8783-140">Using Transact-SQL to Create and Configure an Availability Group</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8783-141"> 如需包含每一個這類 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式之程式碼範例的範例組態程序，請參閱 [範例：設定使用 Windows 驗證的可用性群組](#ExampleConfigAGWinAuth)。</span><span class="sxs-lookup"><span data-stu-id="a8783-141">For a sample configuration procedure containing code examples of each these [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements, see [Example: Configuring an Availability Group that Uses Windows Authentication](#ExampleConfigAGWinAuth).</span></span>  
  
1.  <span data-ttu-id="a8783-142">連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="a8783-142">Connect to the server instance that is to host the primary replica.</span></span>  
  
2.  <span data-ttu-id="a8783-143">使用[CREATE AVAILABILITY group](/sql/t-sql/statements/create-availability-group-transact-sql)語句建立可用性群組 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a8783-143">Create the availability group by using the [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span>  
  
3.  <span data-ttu-id="a8783-144">將新的次要複本加入可用性群組。</span><span class="sxs-lookup"><span data-stu-id="a8783-144">Join the new secondary replica to the availability group.</span></span> <span data-ttu-id="a8783-145">如需詳細資訊，請參閱 [將次要複本聯結至可用性群組 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a8783-145">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
4.  <span data-ttu-id="a8783-146">如果是可用性群組中的每個資料庫，請使用 RESTORE WITH NORECOVERY 還原主要資料庫的最近備份來建立次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="a8783-146">For each database in the availability group, create a secondary database by restoring recent backups of the primary database, using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="a8783-147">如需詳細資訊，請參閱 [範例︰設定使用 Windows 驗證的可用性群組 (TRANSACT-SQL)](create-an-availability-group-transact-sql.md)，從還原資料庫備份的步驟開始。</span><span class="sxs-lookup"><span data-stu-id="a8783-147">For more information, see [Example: Setting Up an Availability Group Using Windows Authentication (Transact-SQL)](create-an-availability-group-transact-sql.md), starting with the step that restores the database backup.</span></span>  
  
5.  <span data-ttu-id="a8783-148">將每一個新的次要資料庫加入可用性群組。</span><span class="sxs-lookup"><span data-stu-id="a8783-148">Join every new secondary database to the availability group.</span></span> <span data-ttu-id="a8783-149">如需詳細資訊，請參閱 [將次要複本聯結至可用性群組 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a8783-149">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
##  <a name="example-configuring-an-availability-group-that-uses-windows-authentication"></a><a name="ExampleConfigAGWinAuth"></a> <span data-ttu-id="a8783-150">範例：設定使用 Windows 驗證的可用性群組</span><span class="sxs-lookup"><span data-stu-id="a8783-150">Example: Configuring an Availability Group that Uses Windows Authentication</span></span>  
 <span data-ttu-id="a8783-151">這個範例會建立範例 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 組態程序，此程序會使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 來設定使用 Windows 驗證的資料庫鏡像端點，並建立及設定可用性群組以及其次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="a8783-151">This example creates a sample [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] configuration procedure that uses [!INCLUDE[tsql](../../../includes/tsql-md.md)] to set up database mirroring endpoints that use Windows Authentication and to create and configure an availability group and its secondary databases.</span></span>  
  
 <span data-ttu-id="a8783-152">此範例包含下列章節：</span><span class="sxs-lookup"><span data-stu-id="a8783-152">This example contains the following sections:</span></span>  
  
-   [<span data-ttu-id="a8783-153">使用範例設定程式的必要條件</span><span class="sxs-lookup"><span data-stu-id="a8783-153">Prerequisites for Using the Sample Configuration Procedure</span></span>](#PrerequisitesForExample)  
  
-   [<span data-ttu-id="a8783-154">範例組態程序</span><span class="sxs-lookup"><span data-stu-id="a8783-154">Sample Configuration Procedure</span></span>](#SampleProcedure)  
  
-   [<span data-ttu-id="a8783-155">範例組態程序的完整程式碼範例</span><span class="sxs-lookup"><span data-stu-id="a8783-155">Complete Code Example for Sample Configuration Procedure</span></span>](#CompleteCodeExample)  
  
###  <a name="prerequisites-for-using-the-sample-configuration-procedure"></a><a name="PrerequisitesForExample"></a> <span data-ttu-id="a8783-156">使用範例組態程序的必要條件</span><span class="sxs-lookup"><span data-stu-id="a8783-156">Prerequisites for Using the Sample Configuration Procedure</span></span>  
 <span data-ttu-id="a8783-157">此範例程序有下列需求：</span><span class="sxs-lookup"><span data-stu-id="a8783-157">This sample procedure has the following requirements:</span></span>  
  
-   <span data-ttu-id="a8783-158">伺服器執行個體必須支援 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a8783-158">The server instances must support [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="a8783-159">如需詳細資訊，請參閱 [AlwaysOn 可用性群組的必要條件、限制和建議 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="a8783-159">For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
-   <span data-ttu-id="a8783-160">*MyDb1* 與 *MyDb2*這兩個範例資料庫必須存在於將裝載主要複本的伺服器執行個體上。</span><span class="sxs-lookup"><span data-stu-id="a8783-160">Two sample databases, *MyDb1* and *MyDb2*, must exist on the server instance that will host the primary replica.</span></span> <span data-ttu-id="a8783-161">下列程式碼範例會建立及設定這兩個資料庫，並建立每一個資料庫的完整備份。</span><span class="sxs-lookup"><span data-stu-id="a8783-161">The following code examples create and configure these two databases and create a full backup of each.</span></span> <span data-ttu-id="a8783-162">在您打算建立範例可用性群組的伺服器執行個體上，執行這些程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="a8783-162">Execute these code examples on the server instance on which you intend to create the sample availability group.</span></span> <span data-ttu-id="a8783-163">此伺服器執行個體將會裝載範例可用性群組的初始主要複本。</span><span class="sxs-lookup"><span data-stu-id="a8783-163">This server instance will host the initial primary replica of the sample availability group.</span></span>  
  
    1.  <span data-ttu-id="a8783-164">下列 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 範例會建立這些資料庫，並加以更改為使用完整復原模式：</span><span class="sxs-lookup"><span data-stu-id="a8783-164">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] example creates these databases and alters them to use the full recovery model:</span></span>  
  
        ```sql
        -- Create sample databases:  
        CREATE DATABASE MyDb1;  
        GO  
        ALTER DATABASE MyDb1 SET RECOVERY FULL;  
        GO  
  
        CREATE DATABASE MyDb2;  
        GO  
        ALTER DATABASE MyDb2 SET RECOVERY FULL;  
        GO  
        ```  
  
    2.  <span data-ttu-id="a8783-165">下列程式碼範例會建立 *MyDb1* 與 *MyDb2*的完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="a8783-165">The following code example creates a full database backup of *MyDb1* and *MyDb2*.</span></span> <span data-ttu-id="a8783-166">此程式碼範例會使用虛構的備份共用（檔案伺服器 \\ \\ *FILESERVER* \\ *SQLbackups*）。</span><span class="sxs-lookup"><span data-stu-id="a8783-166">This code example uses a fictional backup share, \\\\*FILESERVER*\\*SQLbackups*.</span></span>  
  
        ```sql
        -- Backup sample databases:  
        BACKUP DATABASE MyDb1   
        TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
            WITH FORMAT  
        GO  
  
        BACKUP DATABASE MyDb2   
        TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
            WITH FORMAT  
        GO
        ```  
  
###  <a name="sample-configuration-procedure"></a><a name="SampleProcedure"></a> <span data-ttu-id="a8783-167">範例組態程序</span><span class="sxs-lookup"><span data-stu-id="a8783-167">Sample Configuration Procedure</span></span>  
 <span data-ttu-id="a8783-168">在此範例組態中，將會於不同但受信任網域 (`DOMAIN1` 和 `DOMAIN2`) 底下執行其服務帳戶的兩個獨立伺服器執行個體上建立可用性複本。</span><span class="sxs-lookup"><span data-stu-id="a8783-168">In this sample configuration, the availability replica will be created on two stand-alone server instances whose service accounts run under different, but trusted, domains (`DOMAIN1` and `DOMAIN2`).</span></span>  
  
 <span data-ttu-id="a8783-169">下表摘要說明此範例組態中所使用的值。</span><span class="sxs-lookup"><span data-stu-id="a8783-169">The following table summarizes the values used in this sample configuration.</span></span>  
  
|<span data-ttu-id="a8783-170">初始角色</span><span class="sxs-lookup"><span data-stu-id="a8783-170">Initial role</span></span>|<span data-ttu-id="a8783-171">系統</span><span class="sxs-lookup"><span data-stu-id="a8783-171">System</span></span>|<span data-ttu-id="a8783-172">主機 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體</span><span class="sxs-lookup"><span data-stu-id="a8783-172">Host [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instance</span></span>|  
|------------------|------------|---------------------------------------------|  
|<span data-ttu-id="a8783-173">Primary</span><span class="sxs-lookup"><span data-stu-id="a8783-173">Primary</span></span>|`COMPUTER01`|`AgHostInstance`|  
|<span data-ttu-id="a8783-174">次要</span><span class="sxs-lookup"><span data-stu-id="a8783-174">Secondary</span></span>|`COMPUTER02`|<span data-ttu-id="a8783-175">預設執行個體</span><span class="sxs-lookup"><span data-stu-id="a8783-175">Default instance.</span></span>|  
  
1.  <span data-ttu-id="a8783-176">在您打算建立可用性群組的伺服器執行個體上 (這是 *上名為* 的執行個體)，建立名為 `AgHostInstance` dbm_endpoint `COMPUTER01`的資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="a8783-176">Create a database mirroring endpoint named *dbm_endpoint* on the server instance on which you plan to create the availability group (this is an instance named `AgHostInstance` on `COMPUTER01`).</span></span> <span data-ttu-id="a8783-177">此端點使用通訊埠 7022。</span><span class="sxs-lookup"><span data-stu-id="a8783-177">This endpoint uses port 7022.</span></span> <span data-ttu-id="a8783-178">請注意，可用性群組建立所在的伺服器執行個體將會裝載主要複本。</span><span class="sxs-lookup"><span data-stu-id="a8783-178">Note that the server instance on which you create the availability group will host the primary replica.</span></span>  
  
    ```sql
    -- Create endpoint on server instance that hosts the primary replica:  
    CREATE ENDPOINT dbm_endpoint  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO
    ```  
  
2.  <span data-ttu-id="a8783-179">在要裝載次要複本的伺服器執行個體上 (這是 *上的預設伺服器執行個體)，建立端點* dbm_endpoint `COMPUTER02`。</span><span class="sxs-lookup"><span data-stu-id="a8783-179">Create an endpoint *dbm_endpoint* on the server instance that will host the secondary replica (this is the default server instance on `COMPUTER02`).</span></span> <span data-ttu-id="a8783-180">此端點使用通訊埠 5022。</span><span class="sxs-lookup"><span data-stu-id="a8783-180">This endpoint uses port 5022.</span></span>  
  
    ```sql
    -- Create endpoint on server instance that hosts the secondary replica:   
    CREATE ENDPOINT dbm_endpoint  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=5022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO
    ```  
  
3.  > [!NOTE]  
    >  <span data-ttu-id="a8783-181">如果要裝載可用性複本之伺服器執行個體的服務帳戶在相同的網域帳戶下執行，則不需要此步驟。</span><span class="sxs-lookup"><span data-stu-id="a8783-181">If the service accounts of the server instances that are to host your availability replicas run under the same domain account this step is unnecessary.</span></span> <span data-ttu-id="a8783-182">略過它，直接進入下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="a8783-182">Skip it and go directly to the next step.</span></span>  
  
     <span data-ttu-id="a8783-183">如果伺服器執行個體的服務帳戶在不同的網域使用者之下執行，請在每一個伺服器執行個體上建立其他伺服器執行個體的登入，並授與此登入存取本機資料庫鏡像端點的權限。</span><span class="sxs-lookup"><span data-stu-id="a8783-183">If the service accounts of the server instances run under different domain users, on each server instance, create a login for the other server instance and grant this login permission to access the local database mirroring endpoint.</span></span>  
  
     <span data-ttu-id="a8783-184">下列程式碼範例將示範用來建立登入，並在端點上授與其權限的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a8783-184">The following code example shows the [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements for creating a login and granting it permission on an endpoint.</span></span> <span data-ttu-id="a8783-185">遠端伺服器執行個體的網域帳戶在這裡會以 *domain_name*\\*user_name*來表示。</span><span class="sxs-lookup"><span data-stu-id="a8783-185">The domain account of the remote server instance is represented here as *domain_name*\\*user_name*.</span></span>  
  
    ```sql
    -- If necessary, create a login for the service account, domain_name\user_name  
    -- of the server instance that will host the other replica:  
    USE master;  
    GO  
    CREATE LOGIN [domain_name\user_name] FROM WINDOWS;  
    GO  
    -- And Grant this login connect permissions on the endpoint:  
    GRANT CONNECT ON ENDPOINT::dbm_endpoint   
       TO [domain_name\user_name];  
    GO  
    ```  
  
4.  <span data-ttu-id="a8783-186">在使用者資料庫所在的伺服器執行個體上，建立可用性群組。</span><span class="sxs-lookup"><span data-stu-id="a8783-186">On the server instance where the user databases reside, create the availability group.</span></span>  
  
     <span data-ttu-id="a8783-187">下列程式碼範例會在建立 *MyDb1* 與 *MyDb2* 範例資料庫的伺服器執行個體上建立名為 *MyAG*的可用性群組。</span><span class="sxs-lookup"><span data-stu-id="a8783-187">The following code example creates an availability group named *MyAG* on the server instance on which the sample databases, *MyDb1* and *MyDb2*, were created.</span></span> <span data-ttu-id="a8783-188">先指定本機伺服器執行個體，即 `AgHostInstance`COMPUTER01 *上的* 。</span><span class="sxs-lookup"><span data-stu-id="a8783-188">The local server instance, `AgHostInstance`, on *COMPUTER01* is specified first.</span></span> <span data-ttu-id="a8783-189">這個執行個體將會裝載初始主要複本。</span><span class="sxs-lookup"><span data-stu-id="a8783-189">This instance will host the initial primary replica.</span></span> <span data-ttu-id="a8783-190">接著指定遠端伺服器執行個體，即 *COMPUTER02*上的預設伺服器執行個體，以裝載次要複本。</span><span class="sxs-lookup"><span data-stu-id="a8783-190">A remote server instance, the default server instance on *COMPUTER02*, is specified to host a secondary replica.</span></span> <span data-ttu-id="a8783-191">這兩個可用性複本都是設定為具有手動容錯移轉的非同步認可模式 (對於非同步認可複本，手動容錯移轉表示在可能遺失資料的情況下強制容錯移轉)。</span><span class="sxs-lookup"><span data-stu-id="a8783-191">Both availability replica are configured to use asynchronous-commit mode with manual failover (for asynchronous-commit replicas manual failover means  forced failover with possible data loss).</span></span>  
  
    ```sql
    -- Create the availability group, MyAG:   
    CREATE AVAILABILITY GROUP MyAG   
       FOR   
          DATABASE MyDB1, MyDB2   
       REPLICA ON   
          'COMPUTER01\AgHostInstance' WITH   
             (  
             ENDPOINT_URL = 'TCP://COMPUTER01.Adventure-Works.com:7022',   
             AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
             FAILOVER_MODE = MANUAL  
             ),  
          'COMPUTER02' WITH   
             (  
             ENDPOINT_URL = 'TCP://COMPUTER02.Adventure-Works.com:5022',  
             AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
             FAILOVER_MODE = MANUAL  
             );   
    GO  
    ```  
  
     <span data-ttu-id="a8783-192">如需建立可用性群組的其他 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 程式碼範例，請參閱 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a8783-192">For additional [!INCLUDE[tsql](../../../includes/tsql-md.md)] code examples of creating an availability group, see [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql).</span></span>  
  
5.  <span data-ttu-id="a8783-193">在裝載次要複本的伺服器執行個體上，將次要複本加入至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="a8783-193">On the server instance that hosts the secondary replica, join the secondary replica to the availability group.</span></span>  
  
     <span data-ttu-id="a8783-194">下列程式碼範例會將 `COMPUTER02` 上的第二個複本加入到 `MyAG` 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="a8783-194">The following code example joins the secondary replica on `COMPUTER02` to the `MyAG` availability group.</span></span>  
  
    ```sql
    -- On the server instance that hosts the secondary replica,   
    -- join the secondary replica to the availability group:  
    ALTER AVAILABILITY GROUP MyAG JOIN;  
    GO  
    ```  
  
6.  <span data-ttu-id="a8783-195">在裝載次要複本的伺服器執行個體上，建立次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="a8783-195">On the server instance that hosts the secondary replica, create the secondary databases.</span></span>  
  
     <span data-ttu-id="a8783-196">下列程式碼範例會使用 RESTORE WITH NORECOVERY 來還原資料庫備份，以建立 *MyDb1* 與 *MyDb2* 次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="a8783-196">The following code example creates the *MyDb1* and *MyDb2* secondary databases by restoring database backups using RESTORE WITH NORECOVERY.</span></span>  
  
    ```sql
    -- On the server instance that hosts the secondary replica,   
    -- Restore database backups using the WITH NORECOVERY option:  
    RESTORE DATABASE MyDb1   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
        WITH NORECOVERY  
    GO  
  
    RESTORE DATABASE MyDb2   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
        WITH NORECOVERY  
    GO
    ```  
  
7.  <span data-ttu-id="a8783-197">在裝載主要複本的伺服器執行個體上，於每一個主要資料庫上備份交易記錄。</span><span class="sxs-lookup"><span data-stu-id="a8783-197">On the server instance that hosts the primary replica, back up the transaction log on each of the primary databases.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a8783-198">當您設定真正的可用性群組時，我們建議您在取得此記錄備份之前，先暫停主要資料庫的記錄備份工作，直到您將對應的次要資料庫加入可用性群組為止。</span><span class="sxs-lookup"><span data-stu-id="a8783-198">When you are configuring a real availability group, we recommend that, before taking this log backup, you suspend log backup tasks for your primary databases until you have joined the corresponding secondary databases to the availability group.</span></span>  
  
     <span data-ttu-id="a8783-199">下列程式碼範例會在 MyDb1 和 MyDb2 上建立交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="a8783-199">The following code example creates a transaction log backup on MyDb1 and on MyDb2.</span></span>  
  
    ```sql
    -- On the server instance that hosts the primary replica,   
    -- Backup the transaction log on each primary database:  
    BACKUP LOG MyDb1   
    TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
        WITH NOFORMAT  
    GO  
  
    BACKUP LOG MyDb2   
    TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
        WITHNOFORMAT  
    GO
    ```  
  
    > [!TIP]  
    >  <span data-ttu-id="a8783-200">一般而言，您必須在每一個主要資料庫上進行記錄備份，然後在對應的次要資料庫上還原 (使用 WITH NORECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="a8783-200">Typically, a log backup must be taken on each primary database and then restored on the corresponding secondary database (using WITH NORECOVERY).</span></span> <span data-ttu-id="a8783-201">不過，如果資料庫剛剛建立，而且尚未建立任何記錄備份，或是如果復原模式剛剛從 SIMPLE 變更為 FULL，可能就不需要此記錄備份。</span><span class="sxs-lookup"><span data-stu-id="a8783-201">However, this log backup might be unnecessary if the database has just been created and no log backup has been taken yet or the recovery model has just been changed from SIMPLE to FULL.</span></span>  
  
8.  <span data-ttu-id="a8783-202">在裝載次要複本的伺服器執行個體上，將記錄備份套用到次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="a8783-202">On the server instance that hosts the secondary replica, apply log backups to the secondary databases.</span></span>  
  
     <span data-ttu-id="a8783-203">下列程式碼範例會使用 RESTORE WITH NORECOVERY 來還原資料庫備份，以將備份套用至 *MyDb1* 與 *MyDb2* 次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="a8783-203">The following code example applies backups to *MyDb1* and *MyDb2* secondary databases by restoring database backups using RESTORE WITH NORECOVERY.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a8783-204">當您準備真正的次要資料庫時，您必須套用您從建立次要資料庫的資料庫備份開始所取得的每一個記錄備份 (從最早的開始)，而且一定要使用 RESTORE WITH NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="a8783-204">When you are preparing a real secondary database, you need to apply every log backup taken since the database backup from which you created the secondary database, starting with the earliest and always using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="a8783-205">當您同時還原完整和差異資料庫備份時，您只需要套用差異備份之後所做的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="a8783-205">Of course, if you restore both full and differential database backups, you would only need to apply the log backups taken after the differential backup.</span></span>  
  
    ```sql
    -- Restore the transaction log on each secondary database,  
    -- using the WITH NORECOVERY option:  
    RESTORE LOG MyDb1   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    RESTORE LOG MyDb2   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
9. <span data-ttu-id="a8783-206">在裝載次要複本的伺服器執行個體上，將新的次要資料庫加入至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="a8783-206">On the server instance that hosts the secondary replica, join the new secondary databases to the availability group.</span></span>  
  
     <span data-ttu-id="a8783-207">下列程式碼範例會依序將 *MyDb1* 次要資料庫與 *MyDb2* 次要資料庫聯結至 *MyAG* 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="a8783-207">The following code example, joins the *MyDb1* secondary database and then the *MyDb2* secondary databases to the *MyAG* availability group.</span></span>  
  
    ```sql
    -- On the server instance that hosts the secondary replica,   
    -- join each secondary database to the availability group:  
    ALTER DATABASE MyDb1 SET HADR AVAILABILITY GROUP = MyAG;  
    GO  
  
    ALTER DATABASE MyDb2 SET HADR AVAILABILITY GROUP = MyAG;  
    GO
    ```  
  
###  <a name="complete-code-example-for-sample-configuration-procedure"></a><a name="CompleteCodeExample"></a> <span data-ttu-id="a8783-208">範例組態程序的完整程式碼範例</span><span class="sxs-lookup"><span data-stu-id="a8783-208">Complete Code Example for Sample Configuration Procedure</span></span>  
 <span data-ttu-id="a8783-209">下列範例會合併範例組態程序之所有步驟的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="a8783-209">The following example merges the code examples from all the steps of the sample configuration procedure.</span></span> <span data-ttu-id="a8783-210">下表摘要說明此程式碼範例中所使用的預留位置值。</span><span class="sxs-lookup"><span data-stu-id="a8783-210">The following table summarized the placeholder values used in this code example.</span></span> <span data-ttu-id="a8783-211">如需有關此程式碼範例中步驟的詳細資訊，請參閱本主題稍早的 [使用範例組態程序的必要條件](#PrerequisitesForExample) 和 [範例組態程序](#SampleProcedure)。</span><span class="sxs-lookup"><span data-stu-id="a8783-211">For more information about the steps in this code example, see [Prerequisites for Using the Sample Configuration Procedure](#PrerequisitesForExample) and [Sample Configuration Procedure](#SampleProcedure), earlier in this topic.</span></span>  
  
|<span data-ttu-id="a8783-212">預留位置</span><span class="sxs-lookup"><span data-stu-id="a8783-212">Placeholder</span></span>|<span data-ttu-id="a8783-213">描述</span><span class="sxs-lookup"><span data-stu-id="a8783-213">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a8783-214">\\\\*FILESERVER*\\*SQLbackups*</span><span class="sxs-lookup"><span data-stu-id="a8783-214">\\\\*FILESERVER*\\*SQLbackups*</span></span>|<span data-ttu-id="a8783-215">虛構的備份共用。</span><span class="sxs-lookup"><span data-stu-id="a8783-215">Fictional backup share.</span></span>|  
|<span data-ttu-id="a8783-216">\\\\*FILESERVER*\\*SQLbackups\MyDb1.bak*</span><span class="sxs-lookup"><span data-stu-id="a8783-216">\\\\*FILESERVER*\\*SQLbackups\MyDb1.bak*</span></span>|<span data-ttu-id="a8783-217">MyDb1 的備份檔案。</span><span class="sxs-lookup"><span data-stu-id="a8783-217">Backup file for MyDb1.</span></span>|  
|<span data-ttu-id="a8783-218">\\\\*FILESERVER*\\*SQLbackups\MyDb2.bak*</span><span class="sxs-lookup"><span data-stu-id="a8783-218">\\\\*FILESERVER*\\*SQLbackups\MyDb2.bak*</span></span>|<span data-ttu-id="a8783-219">MyDb2 的備份檔案。</span><span class="sxs-lookup"><span data-stu-id="a8783-219">Backup file for MyDb2.</span></span>|  
|<span data-ttu-id="a8783-220">*7022*</span><span class="sxs-lookup"><span data-stu-id="a8783-220">*7022*</span></span>|<span data-ttu-id="a8783-221">指派給每一個資料庫鏡像端點的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="a8783-221">Port number assigned to each database mirroring endpoint.</span></span>|  
|<span data-ttu-id="a8783-222">*COMPUTER01\AgHostInstance*</span><span class="sxs-lookup"><span data-stu-id="a8783-222">*COMPUTER01\AgHostInstance*</span></span>|<span data-ttu-id="a8783-223">裝載初始主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="a8783-223">Server instance that hosts the initial primary replica.</span></span>|  
|<span data-ttu-id="a8783-224">*COMPUTER02*</span><span class="sxs-lookup"><span data-stu-id="a8783-224">*COMPUTER02*</span></span>|<span data-ttu-id="a8783-225">裝載初始次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="a8783-225">Server instance that hosts the initial secondary replica.</span></span> <span data-ttu-id="a8783-226">這是 `COMPUTER02`上的預設伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="a8783-226">This is the default server instance on `COMPUTER02`.</span></span>|  
|<span data-ttu-id="a8783-227">*上名為*</span><span class="sxs-lookup"><span data-stu-id="a8783-227">*dbm_endpoint*</span></span>|<span data-ttu-id="a8783-228">為每個資料庫鏡像端點指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="a8783-228">Name specified for each database mirroring endpoint.</span></span>|  
|<span data-ttu-id="a8783-229">*MyDb1*</span><span class="sxs-lookup"><span data-stu-id="a8783-229">*MyAG*</span></span>|<span data-ttu-id="a8783-230">範例可用性群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="a8783-230">Name of sample availability group.</span></span>|  
|<span data-ttu-id="a8783-231">*MyDb1*</span><span class="sxs-lookup"><span data-stu-id="a8783-231">*MyDb1*</span></span>|<span data-ttu-id="a8783-232">第一個範例資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="a8783-232">Name of first sample database.</span></span>|  
|<span data-ttu-id="a8783-233">*MyDb2*</span><span class="sxs-lookup"><span data-stu-id="a8783-233">*MyDb2*</span></span>|<span data-ttu-id="a8783-234">第二個範例資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="a8783-234">Name of second sample database.</span></span>|  
|<span data-ttu-id="a8783-235">*DOMAIN1\user1*</span><span class="sxs-lookup"><span data-stu-id="a8783-235">*DOMAIN1\user1*</span></span>|<span data-ttu-id="a8783-236">要裝載初始主要複本之伺服器執行個體的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="a8783-236">Service account of the server instance that is to host the initial primary replica.</span></span>|  
|<span data-ttu-id="a8783-237">*DOMAIN2\user2*</span><span class="sxs-lookup"><span data-stu-id="a8783-237">*DOMAIN2\user2*</span></span>|<span data-ttu-id="a8783-238">要裝載初始次要複本之伺服器執行個體的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="a8783-238">Service account of the server instance that is to host the initial secondary replica.</span></span>|  
|<span data-ttu-id="a8783-239">TCP://*COMPUTER01.Adventure-Works.com*:*7022*</span><span class="sxs-lookup"><span data-stu-id="a8783-239">TCP://*COMPUTER01.Adventure-Works.com*:*7022*</span></span>|<span data-ttu-id="a8783-240">COMPUTER01 上 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 之 AgHostInstance 執行個體的端點 URL。</span><span class="sxs-lookup"><span data-stu-id="a8783-240">Endpoint URL of the AgHostInstance instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on COMPUTER01.</span></span>|  
|<span data-ttu-id="a8783-241">TCP://*COMPUTER02.Adventure-Works.com*:*5022*</span><span class="sxs-lookup"><span data-stu-id="a8783-241">TCP://*COMPUTER02.Adventure-Works.com*:*5022*</span></span>|<span data-ttu-id="a8783-242">COMPUTER02 上 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 之預設執行個體的端點 URL。</span><span class="sxs-lookup"><span data-stu-id="a8783-242">Endpoint URL of the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on COMPUTER02.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="a8783-243">如需建立可用性群組的其他 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 程式碼範例，請參閱 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a8783-243">For additional [!INCLUDE[tsql](../../../includes/tsql-md.md)] code examples of creating an availability group, see [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql).</span></span>  
  
```sql
-- on the server instance that will host the primary replica,   
-- create sample databases:  
CREATE DATABASE MyDb1;  
GO  
ALTER DATABASE MyDb1 SET RECOVERY FULL;  
GO  
  
CREATE DATABASE MyDb2;  
GO  
ALTER DATABASE MyDb2 SET RECOVERY FULL;  
GO  
  
-- Backup sample databases:  
BACKUP DATABASE MyDb1   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH FORMAT  
GO  
  
BACKUP DATABASE MyDb2   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITH FORMAT  
GO  
  
-- Create the endpoint on the server instance that will host the primary replica:  
CREATE ENDPOINT dbm_endpoint  
    STATE=STARTED   
    AS TCP (LISTENER_PORT=7022)   
    FOR DATABASE_MIRRORING (ROLE=ALL)  
GO  
  
-- Create the endpoint on the server instance that will host the secondary replica:   
CREATE ENDPOINT dbm_endpoint  
    STATE=STARTED   
    AS TCP (LISTENER_PORT=7022)   
    FOR DATABASE_MIRRORING (ROLE=ALL)  
GO  
  
-- If both service accounts run under the same domain account, skip this step. Otherwise,   
-- On the server instance that will host the primary replica,   
-- create a login for the service account   
-- of the server instance that will host the secondary replica, DOMAIN2\user2,   
-- and grant this login connect permissions on the endpoint:  
USE master;  
GO  
CREATE LOGIN [DOMAIN2\user2] FROM WINDOWS;  
GO  
GRANT CONNECT ON ENDPOINT::dbm_endpoint   
   TO [DOMAIN2\user2];  
GO  
  
-- If both service accounts run under the same domain account, skip this step. Otherwise,   
-- On the server instance that will host the secondary replica,  
-- create a login for the service account   
-- of the server instance that will host the primary replica, DOMAIN1\user1,   
-- and grant this login connect permissions on the endpoint:  
USE master;  
GO  
  
CREATE LOGIN [DOMAIN1\user1] FROM WINDOWS;  
GO  
GRANT CONNECT ON ENDPOINT::dbm_endpoint   
   TO [DOMAIN1\user1];  
GO  
  
-- On the server instance that will host the primary replica,   
-- create the availability group, MyAG:  
CREATE AVAILABILITY GROUP MyAG   
   FOR   
      DATABASE MyDB1, MyDB2   
   REPLICA ON   
      'COMPUTER01\AgHostInstance' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER01.Adventure-Works.com:7022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = AUTOMATIC  
         ),  
      'COMPUTER02' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER02.Adventure-Works.com:7022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = AUTOMATIC  
         );   
GO  
  
-- On the server instance that hosts the secondary replica,   
-- join the secondary replica to the availability group:  
ALTER AVAILABILITY GROUP MyAG JOIN;  
GO  
  
-- Restore database backups onto this server instance, using RESTORE WITH NORECOVERY:  
RESTORE DATABASE MyDb1   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH NORECOVERY  
GO  
  
RESTORE DATABASE MyDb2   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITH NORECOVERY  
GO  
  
-- Back up the transaction log on each primary database:  
BACKUP LOG MyDb1   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH NOFORMAT  
GO  
  
BACKUP LOG MyDb2   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITHNOFORMAT  
GO  
  
-- Restore the transaction log on each secondary database,  
-- using the WITH NORECOVERY option:  
RESTORE LOG MyDb1   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH FILE=1, NORECOVERY  
GO  
RESTORE LOG MyDb2   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITH FILE=1, NORECOVERY  
GO  
  
-- On the server instance that hosts the secondary replica,   
-- join each secondary database to the availability group:  
ALTER DATABASE MyDb1 SET HADR AVAILABILITY GROUP = MyAG;  
GO  
  
ALTER DATABASE MyDb2 SET HADR AVAILABILITY GROUP = MyAG;  
GO
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a8783-244">相關工作</span><span class="sxs-lookup"><span data-stu-id="a8783-244">Related Tasks</span></span>  
 <span data-ttu-id="a8783-245">**若要設定可用性群組和複本屬性**</span><span class="sxs-lookup"><span data-stu-id="a8783-245">**To configure availability group and replica properties**</span></span>  
  
-   [<span data-ttu-id="a8783-246">變更可用性複本的可用性模式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-246">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="a8783-247">變更可用性複本的容錯移轉模式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-247">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="a8783-248">建立或設定可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-248">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="a8783-249">設定彈性容錯移轉原則以控制自動容錯移轉的條件 (AlwaysOn 可用性群組)</span><span class="sxs-lookup"><span data-stu-id="a8783-249">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (AlwaysOn Availability Groups)</span></span>](configure-flexible-automatic-failover-policy.md)  
  
-   [<span data-ttu-id="a8783-250">在新增或修改可用性複本時指定端點 URL &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-250">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="a8783-251">設定可用性複本的備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-251">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="a8783-252">設定可用性複本的唯讀存取 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-252">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="a8783-253">設定可用性群組的唯讀路由 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-253">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="a8783-254">變更可用性複本的工作階段逾時期限 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-254">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 <span data-ttu-id="a8783-255">**若要完成可用性群組組態**</span><span class="sxs-lookup"><span data-stu-id="a8783-255">**To complete availability group configuration**</span></span>  
  
-   [<span data-ttu-id="a8783-256">將次要複本聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-256">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="a8783-257">針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-257">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="a8783-258">將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-258">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="a8783-259">建立或設定可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-259">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 <span data-ttu-id="a8783-260">**建立可用性群組的其他方法**</span><span class="sxs-lookup"><span data-stu-id="a8783-260">**Alternative ways to create an availability group**</span></span>  
  
-   [<span data-ttu-id="a8783-261">使用可用性群組精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-261">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="a8783-262">使用新增可用性群組對話方塊 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-262">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="a8783-263">建立可用性群組 &#40;SQL Server PowerShell&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-263">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
 <span data-ttu-id="a8783-264">**若要啟用 AlwaysOn 可用性群組**</span><span class="sxs-lookup"><span data-stu-id="a8783-264">**To enable AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="a8783-265">啟用和停用 AlwaysOn 可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-265">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 <span data-ttu-id="a8783-266">**若要設定資料庫鏡像端點**</span><span class="sxs-lookup"><span data-stu-id="a8783-266">**To configure a database mirroring endpoint**</span></span>  
  
-   [<span data-ttu-id="a8783-267">建立 AlwaysOn 可用性群組 &#40;SQL Server PowerShell 的資料庫鏡像端點&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-267">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="a8783-268">建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-268">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="a8783-269">使用資料庫鏡像端點憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-269">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [<span data-ttu-id="a8783-270">在新增或修改可用性複本時指定端點 URL &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-270">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 <span data-ttu-id="a8783-271">**若要疑難排解 AlwaysOn 可用性群組組態**</span><span class="sxs-lookup"><span data-stu-id="a8783-271">**To troubleshoot AlwaysOn Availability Groups configuration**</span></span>  
  
-   [<span data-ttu-id="a8783-272">針對 AlwaysOn 可用性群組 Configuration (SQL Server) 已刪除進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="a8783-272">Troubleshoot AlwaysOn Availability Groups Configuration (SQL Server)deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [<span data-ttu-id="a8783-273">針對失敗的新增檔案作業進行疑難排解 &#40;AlwaysOn 可用性群組&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-273">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="a8783-274">相關內容</span><span class="sxs-lookup"><span data-stu-id="a8783-274">Related Content</span></span>  
  
-   <span data-ttu-id="a8783-275">**部落格：**</span><span class="sxs-lookup"><span data-stu-id="a8783-275">**Blogs:**</span></span>  
  
     [<span data-ttu-id="a8783-276">AlwaysON - HADRON 學習系列：具備 HADRON 功能之資料庫的工作者集區使用方式</span><span class="sxs-lookup"><span data-stu-id="a8783-276">AlwaysON - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases</span></span>](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [<span data-ttu-id="a8783-277">SQL Server AlwaysOn 團隊部落格：官方 SQL Server AlwaysOn 團隊部落格</span><span class="sxs-lookup"><span data-stu-id="a8783-277">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="a8783-278">CSS SQL Server 工程師部落格</span><span class="sxs-lookup"><span data-stu-id="a8783-278">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="a8783-279">**影片：**</span><span class="sxs-lookup"><span data-stu-id="a8783-279">**Videos:**</span></span>  
  
     [<span data-ttu-id="a8783-280">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第 1 部：新一代高可用性解決方案簡介</span><span class="sxs-lookup"><span data-stu-id="a8783-280">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="a8783-281">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第 2 部：使用 AlwaysOn 建立關鍵任務的高可用性方案</span><span class="sxs-lookup"><span data-stu-id="a8783-281">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="a8783-282">**白皮書：**</span><span class="sxs-lookup"><span data-stu-id="a8783-282">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="a8783-283">Microsoft SQL Server AlwaysOn 高可用性和災害復原方案指南</span><span class="sxs-lookup"><span data-stu-id="a8783-283">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="a8783-284">Microsoft 的 SQL Server 2012 白皮書</span><span class="sxs-lookup"><span data-stu-id="a8783-284">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="a8783-285">SQL Server 客戶諮詢團隊白皮書</span><span class="sxs-lookup"><span data-stu-id="a8783-285">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="a8783-286">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8783-286">See Also</span></span>  
 <span data-ttu-id="a8783-287">[資料庫鏡像端點 &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a8783-287">[The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="a8783-288">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a8783-288">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="a8783-289">可用性群組接聽程式、用戶端連線及應用程式容錯移轉 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a8783-289">Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;</span></span>](../../listeners-client-connectivity-application-failover.md)   
