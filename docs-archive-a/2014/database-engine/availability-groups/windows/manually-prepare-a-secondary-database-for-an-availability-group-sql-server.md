---
title: 針對可用性群組手動準備次要資料庫 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.configsecondarydbs.f1
- sql12.swb.availabilitygroup.preparedbs.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- secondary databases [SQL Server]
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: 9f2feb3c-ea9b-4992-8202-2aeed4f9a6dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3da3f7332bdabce65785b2844157dd4639389254
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594190"
---
# <a name="manually-prepare-a-secondary-database-for-an-availability-group-sql-server"></a><span data-ttu-id="fc419-102">針對可用性群組手動準備次要資料庫 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="fc419-102">Manually Prepare a Secondary Database for an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="fc419-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或 PowerShell，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中準備 AlwaysOn 可用性群組的次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="fc419-103">This topic describes how to prepare a secondary database for an AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell.</span></span> <span data-ttu-id="fc419-104">準備次要資料庫需要進行兩個步驟：(1) 使用 RESTORE WITH NORECOVERY，將主要資料庫的最新資料庫備份和後續記錄備份還原至裝載次要複本的每個伺服器執行個體，以及 (2) 將還原的資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="fc419-104">Preparing a secondary database requires two steps: (1) restoring a recent database backup of the primary database and subsequent log backups onto each server instance that hosts the secondary replica, using RESTORE WITH NORECOVERY, and (2) joining the restored database to the availability group.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="fc419-105">如果您有現有的記錄傳送組態，您可能可以將記錄傳送主要資料庫連同其一個或多個次要資料庫，一併轉換成 AlwaysOn 主要資料庫和一個或多個 AlwaysOn 次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="fc419-105">If you have an existing log shipping configuration, you might be able to convert the log shipping primary database along with one or more of its secondary databases to an AlwaysOn primary database and one or more AlwaysOn secondary databases.</span></span> <span data-ttu-id="fc419-106">如需詳細資訊，請參閱[從記錄傳送遷移至 AlwaysOn 可用性群組 &#40;SQL Server&#41;的必要條件](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="fc419-106">For more information, see [Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md).</span></span>  
  
-   <span data-ttu-id="fc419-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="fc419-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fc419-108">必要條件和限制</span><span class="sxs-lookup"><span data-stu-id="fc419-108">Prerequisites and Restrictions</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="fc419-109">建議</span><span class="sxs-lookup"><span data-stu-id="fc419-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="fc419-110">安全性</span><span class="sxs-lookup"><span data-stu-id="fc419-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fc419-111">**若要使用下列項目來準備次要資料庫：**</span><span class="sxs-lookup"><span data-stu-id="fc419-111">**To prepare a secondary database, using:**</span></span>  
  
     [<span data-ttu-id="fc419-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fc419-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="fc419-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fc419-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="fc419-114">PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc419-114">PowerShell</span></span>](#PowerShellProcedure)  
  
-   [<span data-ttu-id="fc419-115">相關備份和還原工作</span><span class="sxs-lookup"><span data-stu-id="fc419-115">Related Backup and Restore Tasks</span></span>](#RelatedTasks)  
  
-   <span data-ttu-id="fc419-116">**後續操作** [準備次要資料庫之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="fc419-116">**Follow Up:** [After Preparing a Secondary Database](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fc419-117">開始之前</span><span class="sxs-lookup"><span data-stu-id="fc419-117">Before You Begin</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="fc419-118">必要條件和限制</span><span class="sxs-lookup"><span data-stu-id="fc419-118">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="fc419-119">請確定您規劃放置資料庫的系統已配備具有足夠空間來保存次要資料庫的磁碟機。</span><span class="sxs-lookup"><span data-stu-id="fc419-119">Make sure that the system where you plan to place database possesses a disk drive with sufficient space for the secondary databases.</span></span>  
  
-   <span data-ttu-id="fc419-120">次要資料庫的名稱必須與主要資料庫的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="fc419-120">The name of the secondary database must be the same as the name of the primary database.</span></span>  
  
-   <span data-ttu-id="fc419-121">針對每個還原作業使用 RESTORE WITH NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="fc419-121">Use RESTORE WITH NORECOVERY for every restore operation.</span></span>  
  
-   <span data-ttu-id="fc419-122">如果次要資料庫與主要資料庫必須位於不同的檔案路徑 (包括磁碟機代號)，還原命令也必須針對每個資料庫檔案使用 WITH MOVE 選項，以便將它們指定為次要資料庫的路徑。</span><span class="sxs-lookup"><span data-stu-id="fc419-122">If the secondary database needs to reside on a different file path (including the drive letter) than the primary database, the restore command must also use the WITH MOVE option for each of the database files to specify them to the path of the secondary database.</span></span>  
  
-   <span data-ttu-id="fc419-123">如果您是按檔案群組逐一還原資料庫，請務必還原整個資料庫。</span><span class="sxs-lookup"><span data-stu-id="fc419-123">If you restore the database filegroup by filegroup, be sure to restore the whole database.</span></span>  
  
-   <span data-ttu-id="fc419-124">還原資料庫之後，您必須還原 (WITH NORECOVERY) 自從上次還原資料備份以來所建立的每個記錄備份。</span><span class="sxs-lookup"><span data-stu-id="fc419-124">After restoring the database, you must restore (WITH NORECOVERY) every log backup created since the last restored data backup.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="fc419-125">建議</span><span class="sxs-lookup"><span data-stu-id="fc419-125">Recommendations</span></span>  
  
-   <span data-ttu-id="fc419-126">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的獨立執行個體上，我們建議，給定次要資料庫的檔案路徑 (包括磁碟機代號) 盡可能與對應主要資料庫的路徑完全相同。</span><span class="sxs-lookup"><span data-stu-id="fc419-126">On stand-alone instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], we recommend that, if possible, the file path (including the drive letter) of a given secondary database be identical to the path of the corresponding primary database.</span></span> <span data-ttu-id="fc419-127">這是因為，如果您在建立次要資料庫時移動資料庫檔案，之後在次要資料庫上加入檔案的作業可能會失敗，而且導致次要資料庫暫停。</span><span class="sxs-lookup"><span data-stu-id="fc419-127">This is because if you move the database files when creating a secondary database, a later add-file operation might fail on the secondary database and cause the secondary database to be suspended.</span></span>  
  
-   <span data-ttu-id="fc419-128">準備次要資料庫之前，我們強烈建議您針對可用性群組中的資料庫暫停排程的記錄備份，直到次要複本的初始化完成為止。</span><span class="sxs-lookup"><span data-stu-id="fc419-128">Before preparing your secondary databases, we strongly recommend that you suspend scheduled log backups on the databases in the availability group until the initialization of secondary replicas has completed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fc419-129">Security</span><span class="sxs-lookup"><span data-stu-id="fc419-129">Security</span></span>  
 <span data-ttu-id="fc419-130">備份資料庫時，[可信任的[資料庫] 屬性](../../../relational-databases/security/trustworthy-database-property.md)會設定為 [關閉]。</span><span class="sxs-lookup"><span data-stu-id="fc419-130">When a database is backed up, the [TRUSTWORTHY database property](../../../relational-databases/security/trustworthy-database-property.md) is set to OFF.</span></span> <span data-ttu-id="fc419-131">因此，新還原資料庫上的 TRUSTWORTHY 一律為 OFF。</span><span class="sxs-lookup"><span data-stu-id="fc419-131">Therefore, TRUSTWORTHY is always OFF on a newly restored database.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fc419-132">權限</span><span class="sxs-lookup"><span data-stu-id="fc419-132">Permissions</span></span>  
 <span data-ttu-id="fc419-133">BACKUP DATABASE 和 BACKUP LOG 權限預設為 **sysadmin** 固定伺服器角色以及 **db_owner** 和 **db_backupoperator** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="fc419-133">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span> <span data-ttu-id="fc419-134">如需詳細資訊，請參閱 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="fc419-134">For more information, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
 <span data-ttu-id="fc419-135">當還原的資料庫不存在伺服器執行個體上時，RESTORE 陳述式就需要 CREATE DATABASE 權限。</span><span class="sxs-lookup"><span data-stu-id="fc419-135">When the database being restored does not exist on the server instance, the RESTORE statement requires CREATE DATABASE permissions.</span></span> <span data-ttu-id="fc419-136">如需詳細資訊，請參閱 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)備份。</span><span class="sxs-lookup"><span data-stu-id="fc419-136">For more information, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fc419-137">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fc419-137">Using SQL Server Management Studio</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fc419-138"> 如果主控主要複本的伺服器執行個體和主控次要複本的每個執行個體之間的備份和還原檔案路徑相同，則您應該可以使用 [新增可用性群組精靈](use-the-availability-group-wizard-sql-server-management-studio.md)、 [將複本加入至可用性群組精靈](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)或 [將資料庫加入至可用性群組精靈](availability-group-add-database-to-group-wizard.md)建立次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="fc419-138">If the backup and restore file paths are identical between the server instance that hosts the primary replica and every instance that hosts a secondary replica, you should be able create secondary databases by using [New Availability Group Wizard](use-the-availability-group-wizard-sql-server-management-studio.md), [Add Replica to Availability Group Wizard](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md), or [Add Database to Availability Group Wizard](availability-group-add-database-to-group-wizard.md).</span></span>  
  
 <span data-ttu-id="fc419-139">**若要準備次要資料庫**</span><span class="sxs-lookup"><span data-stu-id="fc419-139">**To prepare a secondary database**</span></span>  
  
1.  <span data-ttu-id="fc419-140">除非您已經擁有主要資料庫的最新資料庫備份，否則請建立新的完整或差異資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="fc419-140">Unless you already have a recent database backup of the primary database, create a new full or differential database backup.</span></span> <span data-ttu-id="fc419-141">最佳作法是將這個備份和任何後續記錄備份放置於建議的網路共用。</span><span class="sxs-lookup"><span data-stu-id="fc419-141">As a best practice, place this backup and any subsequent log backups onto the recommended network share.</span></span>  
  
2.  <span data-ttu-id="fc419-142">至少建立主要資料庫的一個新記錄備份。</span><span class="sxs-lookup"><span data-stu-id="fc419-142">Create at least one new log backup of the primary database.</span></span>  
  
3.  <span data-ttu-id="fc419-143">在裝載次要複本的伺服器執行個體上，還原主要資料庫的完整資料庫備份 (並選擇性地還原差異備份)，接著還原任何後續記錄備份。</span><span class="sxs-lookup"><span data-stu-id="fc419-143">On the server instance that hosts the secondary replica, restore the full database backup of the primary database (and optionally a differential backup) followed by any subsequent log backups.</span></span>  
  
     <span data-ttu-id="fc419-144">在 [**還原 DATABASEOptions** ] 頁面上，選取 [\*\*讓資料庫保持不運作，且不回復未認可的交易]。可以還原其他交易記錄。 (RESTORE WITH NORECOVERY) \*\*。</span><span class="sxs-lookup"><span data-stu-id="fc419-144">On the **RESTORE DATABASEOptions** page, select **Leave the database non-operational, and do not roll back the uncommitted transactions. Additional transaction logs can be restored. (RESTORE WITH NORECOVERY)**.</span></span>  
  
     <span data-ttu-id="fc419-145">如果主要資料庫與次要資料庫的檔案路徑不同 (例如，主要資料庫位於磁碟機 'F:' 而裝載次要複本的伺服器執行個體缺少 F: 磁碟機)，請在您的 WITH 子句中加入 MOVE 選項。</span><span class="sxs-lookup"><span data-stu-id="fc419-145">If the file paths of the primary database and the secondary database differ, for example, if the primary database is on drive 'F:' but the server instance that hosts the secondary replica lacks an F: drive, include the MOVE option in your WITH clause.</span></span>  
  
4.  <span data-ttu-id="fc419-146">若要完成次要資料庫的組態設定，您必須將次要資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="fc419-146">To complete configuration of the secondary database, you need to join the secondary database to the availability group.</span></span> <span data-ttu-id="fc419-147">如需詳細資訊，請參閱[將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="fc419-147">For more information, [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fc419-148"> 如需有關如何執行這些備份和還原作業的詳細資訊，請參閱本節稍後的＜ [相關備份和還原工作](#RelatedTasks)＞。</span><span class="sxs-lookup"><span data-stu-id="fc419-148">For information about how to perform these backup and restore operations, see [Related Backup and Restore Tasks](#RelatedTasks), later in this section.</span></span>  
  
###  <a name="related-backup-and-restore-tasks"></a><a name="RelatedTasks"></a><span data-ttu-id="fc419-149">相關備份和還原工作</span><span class="sxs-lookup"><span data-stu-id="fc419-149">Related Backup and Restore Tasks</span></span>  
 <span data-ttu-id="fc419-150">**若要建立資料庫備份**</span><span class="sxs-lookup"><span data-stu-id="fc419-150">**To create a database backup**</span></span>  
  
-   [<span data-ttu-id="fc419-151">建立完整資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fc419-151">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="fc419-152">建立差異資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fc419-152">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)  
  
 <span data-ttu-id="fc419-153">**若要建立記錄備份**</span><span class="sxs-lookup"><span data-stu-id="fc419-153">**To create a log backup**</span></span>  
  
-   [<span data-ttu-id="fc419-154">備份交易記錄 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fc419-154">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
 <span data-ttu-id="fc419-155">**若要還原備份**</span><span class="sxs-lookup"><span data-stu-id="fc419-155">**To restore backups**</span></span>  
  
-   [<span data-ttu-id="fc419-156">還原資料庫備份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="fc419-156">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](../../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="fc419-157">還原差異資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fc419-157">Restore a Differential Database Backup &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/restore-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="fc419-158">還原交易記錄備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fc419-158">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
-   [<span data-ttu-id="fc419-159">將資料庫還原到新位置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fc419-159">Restore a Database to a New Location &#40;SQL Server&#41;</span></span>](../../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fc419-160">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fc419-160">Using Transact-SQL</span></span>  
 <span data-ttu-id="fc419-161">**若要準備次要資料庫**</span><span class="sxs-lookup"><span data-stu-id="fc419-161">**To prepare a secondary database**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fc419-162">如需這個程序的範例，請參閱本主題前面的 [範例 (Transact-SQL)](#ExampleTsql)。</span><span class="sxs-lookup"><span data-stu-id="fc419-162">For an example of this procedure, see [Example (Transact-SQL)](#ExampleTsql), earlier in this topic.</span></span>  
  
1.  <span data-ttu-id="fc419-163">除非您擁有主要資料庫的最新完整備份，否則請連接到裝載主要複本的伺服器執行個體，並且建立完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="fc419-163">Unless you have a recent full backup of the primary database, connect to the server instance that hosts the primary replica and create a full database backup.</span></span> <span data-ttu-id="fc419-164">最佳作法是將這個備份和任何後續記錄備份放置於建議的網路共用。</span><span class="sxs-lookup"><span data-stu-id="fc419-164">As a best practice, place this backup and any subsequent log backups onto the recommended network share.</span></span>  
  
2.  <span data-ttu-id="fc419-165">在裝載次要複本的伺服器執行個體上，還原主要資料庫的完整資料庫備份 (並選擇性地還原差異備份)，接著還原所有後續記錄備份。</span><span class="sxs-lookup"><span data-stu-id="fc419-165">On the server instance that hosts the secondary replica, restore the full database backup of the primary database (and optionally a differential backup) followed by all subsequent log backups.</span></span> <span data-ttu-id="fc419-166">針對每個還原作業使用 WITH NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="fc419-166">Use WITH NORECOVERY for every restore operation.</span></span>  
  
     <span data-ttu-id="fc419-167">如果主要資料庫與次要資料庫的檔案路徑不同 (例如，主要資料庫位於磁碟機 'F:' 而裝載次要複本的伺服器執行個體缺少 F: 磁碟機)，請在您的 WITH 子句中加入 MOVE 選項。</span><span class="sxs-lookup"><span data-stu-id="fc419-167">If the file paths of the primary database and the secondary database differ, for example, if the primary database is on drive 'F:' but the server instance that hosts the secondary replica lacks an F: drive, include the MOVE option in your WITH clause.</span></span>  
  
3.  <span data-ttu-id="fc419-168">如果自從必要的記錄備份以來，在主要資料庫上建立過任何記錄備份，您也必須將這些備份複製到裝載次要複本的伺服器執行個體，並且一律使用 RESTORE WITH NORECOVERY，從最早的記錄開始，將每個記錄備份套用至次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="fc419-168">If any log backups have been taken on the primary database since the required log backup, you must also copy these to the server instance that hosts the secondary replica and apply each of those log backups to the secondary database, starting with the earliest and always using RESTORE WITH NORECOVERY.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fc419-169">如果主要資料庫剛剛建立，而且尚未建立任何記錄備份，或者復原模式剛剛從簡單變更為完整，記錄備份就不存在。</span><span class="sxs-lookup"><span data-stu-id="fc419-169">A log backup would not exist if the primary database has just been created and no log backup has been taken yet or if the recovery model has just been changed from simple to full.</span></span>  
  
4.  <span data-ttu-id="fc419-170">若要完成次要資料庫的組態設定，您必須將次要資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="fc419-170">To complete configuration of the secondary database, you need to join the secondary database to the availability group.</span></span> <span data-ttu-id="fc419-171">如需詳細資訊，請參閱[將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="fc419-171">For more information, [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fc419-172"> 如需有關如何執行這些備份和還原作業的詳細資訊，請參閱本主題稍後的＜ [相關備份和還原工作](#RelatedTasks)＞。</span><span class="sxs-lookup"><span data-stu-id="fc419-172">For information about how to perform these backup and restore operations, see [Related Backup and Restore Tasks](#RelatedTasks), later in this topic.</span></span>  
  
###  <a name="transact-sql-example"></a><a name="ExampleTsql"></a><span data-ttu-id="fc419-173">Transact-sql 範例</span><span class="sxs-lookup"><span data-stu-id="fc419-173">Transact-SQL Example</span></span>  
 <span data-ttu-id="fc419-174">下列範例會準備次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="fc419-174">The following example prepares a secondary database.</span></span> <span data-ttu-id="fc419-175">此範例使用 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 範例資料庫，依預設採用簡單復原模式。</span><span class="sxs-lookup"><span data-stu-id="fc419-175">This example uses the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] sample database, which uses the simple recovery model by default.</span></span>  
  
1.  <span data-ttu-id="fc419-176">若要使用 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 資料庫，請將它修改為使用完整復原模式：</span><span class="sxs-lookup"><span data-stu-id="fc419-176">To use the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database, modify it to use the full recovery model:</span></span>  
  
    ```sql
    USE master;  
    GO  
    ALTER DATABASE MyDB1   
    SET RECOVERY FULL;  
    GO  
    ```  
  
2.  <span data-ttu-id="fc419-177">將資料庫的復原模式從 SIMPLE 修改為 FULL 之後，請建立完整備份，以便用於建立次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="fc419-177">After modifying the recovery model of the database from SIMPLE to FULL, create a full backup, which can be used to create the secondary database.</span></span> <span data-ttu-id="fc419-178">因為剛剛才變更復原模式，所以指定了 WITH FORMAT 選項以建立新的媒體集。</span><span class="sxs-lookup"><span data-stu-id="fc419-178">Because the recovery model has just been changed, the WITH FORMAT option is specified to create a new media set.</span></span> <span data-ttu-id="fc419-179">要區分在完整復原模式與簡單復原模式建立的備份時，此方式非常有協助。</span><span class="sxs-lookup"><span data-stu-id="fc419-179">This is useful to separate the backups under the full recovery model from any previous backups made under the simple recovery model.</span></span> <span data-ttu-id="fc419-180">為了完成此範例的目的，我們會在資料庫所在的相同磁碟機上建立備份檔 (C:\\[!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)].bak)。</span><span class="sxs-lookup"><span data-stu-id="fc419-180">For the purpose of this example, the backup file (C:\\[!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)].bak) is created on the same drive as the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fc419-181">對於實際執行的資料庫，您必須備份至其他裝置。</span><span class="sxs-lookup"><span data-stu-id="fc419-181">For a production database, you should always back up to a separate device.</span></span>  
  
     <span data-ttu-id="fc419-182">在裝載主要複本的伺服器執行個體 (`INSTANCE01`) 上，依照下列方式建立主要資料庫的完整備份：</span><span class="sxs-lookup"><span data-stu-id="fc419-182">On the server instance that hosts the primary replica (`INSTANCE01`), create a full backup of the primary database as follows:</span></span>  
  
    ```sql
    BACKUP DATABASE MyDB1   
        TO DISK = 'C:\MyDB1.bak'   
        WITH FORMAT  
    GO  
    ```  
  
3.  <span data-ttu-id="fc419-183">將完整備份複製到裝載次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="fc419-183">Copy the full backup to the server instance that hosts the secondary replica.</span></span>  
  
4.  <span data-ttu-id="fc419-184">使用 RESTORE WITH NORECOVERY，將完整備份還原至裝載次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="fc419-184">Restore the full backup, using RESTORE WITH NORECOVERY, onto the server instance that hosts the secondary replica.</span></span> <span data-ttu-id="fc419-185">還原命令需視主要與次要資料庫的路徑是否相同而定。</span><span class="sxs-lookup"><span data-stu-id="fc419-185">The restore command depends on whether the paths of primary and secondary databases are identical.</span></span>  
  
    -   <span data-ttu-id="fc419-186">**若路徑相同：**</span><span class="sxs-lookup"><span data-stu-id="fc419-186">**If the paths are identical:**</span></span>  
  
         <span data-ttu-id="fc419-187">在裝載次要複本的電腦上，依照下列方式還原完整備份：</span><span class="sxs-lookup"><span data-stu-id="fc419-187">On the computer that hosts the secondary replica, restore the full backup as follows:</span></span>  
  
        ```sql
        RESTORE DATABASE MyDB1   
            FROM DISK = 'C:\MyDB1.bak'   
            WITH NORECOVERY  
        GO  
        ```  
  
    -   <span data-ttu-id="fc419-188">**若路徑不同：**</span><span class="sxs-lookup"><span data-stu-id="fc419-188">**If the paths differ:**</span></span>  
  
         <span data-ttu-id="fc419-189">如果次要資料庫的路徑與主要資料庫的路徑不同 (例如，磁碟機代號不同)，則建立次要資料庫時，還原作業中必須包含 MOVE 子句。</span><span class="sxs-lookup"><span data-stu-id="fc419-189">If the path of the secondary database differs from the path of the primary database (for instance, their drive letters differ), creating the secondary database requires that the restore operation include a MOVE clause.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="fc419-190">如果主要與次要資料庫的路徑名稱不同，您將無法加入檔案。</span><span class="sxs-lookup"><span data-stu-id="fc419-190">If the path names of the primary and secondary databases differ, you cannot add a file.</span></span> <span data-ttu-id="fc419-191">這是因為接收加入檔案作業的記錄時，次要複本的伺服器執行個體會嘗試將新檔案放在主要資料庫所使用的相同路徑中。</span><span class="sxs-lookup"><span data-stu-id="fc419-191">This is because on receiving the log for the add file operation, the server instance of the secondary replica attempts to place the new file in the same path as used by the primary database.</span></span>  
  
         <span data-ttu-id="fc419-192">例如，下列命令會還原位於 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]預設執行個體資料目錄 (C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA) 中之主要資料庫的備份。</span><span class="sxs-lookup"><span data-stu-id="fc419-192">For example, the following command restores a backup of a primary database that resides in the data directory of the default instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA.</span></span> <span data-ttu-id="fc419-193">「還原資料庫」作業必須將資料庫移至 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 名為 (*AlwaysOn1*) 之遠端實例的資料目錄，它會在另一個叢集節點上裝載次要複本。</span><span class="sxs-lookup"><span data-stu-id="fc419-193">The restore database operation must move the database to the data directory of a remote instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] named  (*AlwaysOn1*), which hosts the secondary replica on another cluster node.</span></span> <span data-ttu-id="fc419-194">其中，資料和記錄檔會還原至*C:\Program FILES\MICROSOFT SQL Server\MSSQL12。ALWAYSON1\MSSQL\DATA*目錄。</span><span class="sxs-lookup"><span data-stu-id="fc419-194">There, the data and log files are restored to the *C:\Program Files\Microsoft SQL Server\MSSQL12.ALWAYSON1\MSSQL\DATA* directory .</span></span> <span data-ttu-id="fc419-195">此還原作業會使用 WITH NORECOVERY，將次要資料庫保留在還原資料庫中。</span><span class="sxs-lookup"><span data-stu-id="fc419-195">The restore operation uses WITH NORECOVERY, to leave the secondary database in the restoring database.</span></span>  
  
        ```sql
        RESTORE DATABASE MyDB1  
          FROM DISK='C:\MyDB1.bak'  
         WITH NORECOVERY,   
            MOVE 'MyDB1_Data' TO   
             'C:\Program Files\Microsoft SQL Server\MSSQL12.ALWAYSON1\MSSQL\DATA\MyDB1_Data.mdf',   
            MOVE 'MyDB1_Log' TO  
             'C:\Program Files\Microsoft SQL Server\MSSQL12.ALWAYSON1\MSSQL\DATA\MyDB1_Data.ldf';  
        GO  
        ```  
  
5.  <span data-ttu-id="fc419-196">還原完整備份之後，您必須在主要資料庫上建立記錄備份。</span><span class="sxs-lookup"><span data-stu-id="fc419-196">After you restore the full backup, you must create a log backup on the primary database.</span></span> <span data-ttu-id="fc419-197">例如，下列 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式會將記錄備份至名為 *E:\MyDB1_log.bak*的備份檔：</span><span class="sxs-lookup"><span data-stu-id="fc419-197">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement backs up the log to the a backup file named *E:\MyDB1_log.bak*:</span></span>  
  
    ```sql
    BACKUP LOG MyDB1   
      TO DISK = 'E:\MyDB1_log.bak'   
    GO  
    ```  
  
6.  <span data-ttu-id="fc419-198">您必須先套用必要的記錄備份 (以及任何後續記錄備份)，然後才能將資料庫聯結至次要複本。</span><span class="sxs-lookup"><span data-stu-id="fc419-198">Before you can join the database to the secondary replica, you must apply the required log backup (and any subsequent log backups).</span></span>  
  
     <span data-ttu-id="fc419-199">例如，下列 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式會從 *C:\MyDB1.bak*還原第一筆記錄：</span><span class="sxs-lookup"><span data-stu-id="fc419-199">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement restores the first log from *C:\MyDB1.bak*:</span></span>  
  
    ```sql
    RESTORE LOG MyDB1   
      FROM DISK = 'E:\MyDB1_log.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
7.  <span data-ttu-id="fc419-200">如果資料庫聯結次要複本之前執行了任何額外的記錄備份，您也必須使用 RESTORE WITH NORECOVERY，依序將這些記錄備份全部還原至裝載次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="fc419-200">If any additional log backups occur before the database joins the secondary replica, you must also restore all of those log backups, in sequence, to the server instance that hosts the secondary replica using RESTORE WITH NORECOVERY.</span></span>  
  
     <span data-ttu-id="fc419-201">例如，下列 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式會從 *E:\MyDB1_log.bak*還原兩個額外的記錄：</span><span class="sxs-lookup"><span data-stu-id="fc419-201">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement restores two additional logs from *E:\MyDB1_log.bak*:</span></span>  
  
    ```sql
    RESTORE LOG MyDB1   
      FROM DISK = 'E:\MyDB1_log.bak'   
        WITH FILE=2, NORECOVERY  
    GO  
    RESTORE LOG MyDB1   
      FROM DISK = 'E:\MyDB1_log.bak'   
        WITH FILE=3, NORECOVERY  
    GO  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="fc419-202">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc419-202">Using PowerShell</span></span>  
 <span data-ttu-id="fc419-203">**若要準備次要資料庫**</span><span class="sxs-lookup"><span data-stu-id="fc419-203">**To prepare a secondary database**</span></span>  
  
1.  <span data-ttu-id="fc419-204">如果您需要建立主要資料庫的最新備份，請變更目錄 (`cd`) 為裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="fc419-204">If you need to create a recent backup of the primary database, change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="fc419-205">使用 `Backup-SqlDatabase` 指令程式來建立每個備份。</span><span class="sxs-lookup"><span data-stu-id="fc419-205">Use the `Backup-SqlDatabase` cmdlet to create each of the backups.</span></span>  
  
3.  <span data-ttu-id="fc419-206">將目錄切換到 (`cd`) 裝載次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="fc419-206">Change directory (`cd`) to the server instance that hosts the secondary replica.</span></span>  
  
4.  <span data-ttu-id="fc419-207">若要還原每個主要資料庫的資料庫和記錄備份，請使用 `restore-SqlDatabase` 指令程式，並指定 `NoRecovery` 還原參數。</span><span class="sxs-lookup"><span data-stu-id="fc419-207">To restore the database and log backups of each primary database, use the `restore-SqlDatabase` cmdlet, specifying the `NoRecovery` restore parameter.</span></span> <span data-ttu-id="fc419-208">如果在裝載主要複本的電腦和裝載目標次要複本的電腦之間有檔案路徑差異，也要使用 `RelocateFile` 還原參數。</span><span class="sxs-lookup"><span data-stu-id="fc419-208">If the file paths differ between the computers that host the primary replica and the target secondary replica, also use the `RelocateFile` restore parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fc419-209">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="fc419-209">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="fc419-210">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="fc419-210">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
5.  <span data-ttu-id="fc419-211">若要完成次要資料庫的組態設定，您必須將它聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="fc419-211">To complete configuration of the secondary database, you need to join it to the availability group.</span></span> <span data-ttu-id="fc419-212">如需詳細資訊，請參閱[將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="fc419-212">For more information, [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
 <span data-ttu-id="fc419-213">**若要設定和使用 SQL Server PowerShell 提供者**</span><span class="sxs-lookup"><span data-stu-id="fc419-213">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="fc419-214">SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="fc419-214">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
###  <a name="sample-backup-and-restore-script-and-command"></a><a name="ExamplePSscript"></a><span data-ttu-id="fc419-215">範例備份與還原腳本和命令</span><span class="sxs-lookup"><span data-stu-id="fc419-215">Sample Backup and Restore Script and Command</span></span>  
 <span data-ttu-id="fc419-216">下列 PowerShell 命令會將完整資料庫備份和交易記錄備份至網路共用，並且從該共用還原這些備份。</span><span class="sxs-lookup"><span data-stu-id="fc419-216">The following PowerShell commands back up a full database backup and transaction log to a network share and restore those backups from that share.</span></span> <span data-ttu-id="fc419-217">此範例會假設還原資料庫的目標檔案路徑與備份資料庫的檔案路徑相同。</span><span class="sxs-lookup"><span data-stu-id="fc419-217">This example assumes that the file path to which the database is restored is the same as the file path on which the database was backed up.</span></span>  
  
```powershell
# Create database backup  
Backup-SqlDatabase -Database "MyDB1" -BackupFile "\\share\backups\MyDB1.bak" -ServerInstance "SourceMachine\Instance"  
# Create log backup  
Backup-SqlDatabase -Database "MyDB1" -BackupAction "Log" -BackupFile "\\share\backups\MyDB1.trn" -ServerInstance "SourceMachine\Instance"  
# Restore database backup
Restore-SqlDatabase -Database "MyDB1" -BackupFile "\\share\backups\MyDB1.bak" -NoRecovery -ServerInstance "DestinationMachine\Instance"  
# Restore log backup
Restore-SqlDatabase -Database "MyDB1" -BackupFile "\\share\backups\MyDB1.trn" -RestoreAction "Log" -NoRecovery -ServerInstance "DestinationMachine\Instance"
```  
  
##  <a name="follow-up-after-preparing-a-secondary-database"></a><a name="FollowUp"></a><span data-ttu-id="fc419-218">後續操作：準備次要資料庫之後</span><span class="sxs-lookup"><span data-stu-id="fc419-218">Follow Up: After Preparing a Secondary Database</span></span>  
 <span data-ttu-id="fc419-219">若要完成次要資料庫的組態設定，您必須將新還原的資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="fc419-219">To complete configuration of the secondary database, join the newly restored database to the availability group.</span></span> <span data-ttu-id="fc419-220">如需詳細資訊，請參閱 [將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="fc419-220">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc419-221">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc419-221">See Also</span></span>  
 <span data-ttu-id="fc419-222">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fc419-222">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="fc419-223">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fc419-223">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="fc419-224">[RESTORE 引數 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fc419-224">[RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span></span>  
 <span data-ttu-id="fc419-225">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fc419-225">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="fc419-226">針對失敗的新增檔案作業進行疑難排解 &#40;AlwaysOn 可用性群組&#41;</span><span class="sxs-lookup"><span data-stu-id="fc419-226">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
