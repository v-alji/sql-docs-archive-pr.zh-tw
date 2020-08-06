---
title: 完整的資料庫還原 (完整復原模式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- complete database restores
- database restores [SQL Server], complete database
- restoring databases [SQL Server], complete database
- restoring [SQL Server], database
- full recovery model [SQL Server], performing restores
- log backups [SQL Server[
ms.assetid: 5b4c471c-b972-498e-aba9-92cf7a0ea881
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea6ec9f196acd0a64a0b785024bd6426cd6a5381
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606927"
---
# <a name="complete-database-restores-full-recovery-model"></a><span data-ttu-id="d053b-102">完整的資料庫還原 (完整復原模式)</span><span class="sxs-lookup"><span data-stu-id="d053b-102">Complete Database Restores (Full Recovery Model)</span></span>
  <span data-ttu-id="d053b-103">在完整資料庫還原中，目標是還原整個資料庫。</span><span class="sxs-lookup"><span data-stu-id="d053b-103">In a complete database restore, the goal is to restore the whole database.</span></span> <span data-ttu-id="d053b-104">在還原期間，整個資料庫為離線狀態。</span><span class="sxs-lookup"><span data-stu-id="d053b-104">The whole database is offline for the duration of the restore.</span></span> <span data-ttu-id="d053b-105">在讓資料庫的任何部分上線之前，所有的資料都必須復原到一致的位置；此時資料庫的所有部分都會回到相同的時間點，而且沒有未認可的交易存在。</span><span class="sxs-lookup"><span data-stu-id="d053b-105">Before any part of the database can come online, all data is recovered to a consistent point in which all parts of the database are at the same point in time and no uncommitted transactions exist.</span></span>  
  
 <span data-ttu-id="d053b-106">在完整復原模式下，還原一個或多個資料備份之後，您必須先還原所有後續的交易記錄備份，然後再復原資料庫。</span><span class="sxs-lookup"><span data-stu-id="d053b-106">Under the full recovery model, after you restore your data backup or backups, you must restore all subsequent transaction log backups and then recover the database.</span></span> <span data-ttu-id="d053b-107">您可以將資料庫還原到其中一個記錄備份內的特定 *「復原點」* (Recovery point)。</span><span class="sxs-lookup"><span data-stu-id="d053b-107">You can restore a database to a specific *recovery point* within one of these log backups.</span></span> <span data-ttu-id="d053b-108">復原點可以是特定日期和時間、標示的交易或記錄序號 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="d053b-108">The recovery point can be a specific date and time, a marked transaction, or a log sequence number (LSN).</span></span>  
  
 <span data-ttu-id="d053b-109">還原資料庫時 (特別是在完整復原模式或大量記錄復原模式下)，應該使用單一還原順序。</span><span class="sxs-lookup"><span data-stu-id="d053b-109">When restoring a database, particularly under the full recovery model or bulk-logged recovery model, you should use a single restore sequence.</span></span> <span data-ttu-id="d053b-110">*「還原順序」* (Restore sequence) 包含一個或多個還原作業，會在一個或多個還原階段中移動資料。</span><span class="sxs-lookup"><span data-stu-id="d053b-110">A *restore sequence* consists of one or more restore operations that move data through one or more of the phases of restore.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d053b-111">建議您不要附加或還原來源不明或來源不受信任的資料庫。</span><span class="sxs-lookup"><span data-stu-id="d053b-111">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="d053b-112">這些資料庫可能包含惡意程式碼，因此可能執行非預期的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼，或是修改結構描述或實體資料庫結構而造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="d053b-112">These databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="d053b-113">使用來源不明或來源不受信任的資料庫之前，請先在非實際執行伺服器的資料庫上執行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) ，同時檢查資料庫中的程式碼，例如預存程序或其他使用者定義程式碼。</span><span class="sxs-lookup"><span data-stu-id="d053b-113">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
 <span data-ttu-id="d053b-114">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="d053b-114">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="d053b-115">將資料庫還原到失敗點</span><span class="sxs-lookup"><span data-stu-id="d053b-115">Restoring a Database to the Point of Failure</span></span>](#PointOfFailure)  
  
-   [<span data-ttu-id="d053b-116">將資料庫還原到記錄備份內的時間點</span><span class="sxs-lookup"><span data-stu-id="d053b-116">Restoring a Database to a Point Within a Log Backup</span></span>](#PointWithinBackup)  
  
-   [<span data-ttu-id="d053b-117">相關工作</span><span class="sxs-lookup"><span data-stu-id="d053b-117">Related Tasks</span></span>](#RelatedTasks)  
  
> [!NOTE]  
>  <span data-ttu-id="d053b-118">如需舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之備份支援的相關資訊，請參閱 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)的＜相容性支援＞一節。</span><span class="sxs-lookup"><span data-stu-id="d053b-118">For information about support for backups from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see the "Compatibility Support" section of [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
##  <a name="restoring-a-database-to-the-point-of-failure"></a><a name="PointOfFailure"></a> <span data-ttu-id="d053b-119">將資料庫還原到失敗點</span><span class="sxs-lookup"><span data-stu-id="d053b-119">Restoring a Database to the Point of Failure</span></span>  
 <span data-ttu-id="d053b-120">一般而言，將資料庫復原至失敗點的作業，包含下列基本步驟：</span><span class="sxs-lookup"><span data-stu-id="d053b-120">Typically, recovering a database to the point of failure involves the following basic steps:</span></span>  
  
1.  <span data-ttu-id="d053b-121">備份使用中的交易記錄檔 (即所謂的記錄檔結尾)。</span><span class="sxs-lookup"><span data-stu-id="d053b-121">Back up the active transaction log (known as the tail of the log).</span></span> <span data-ttu-id="d053b-122">這會建立結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="d053b-122">This creates a tail-log backup.</span></span> <span data-ttu-id="d053b-123">如果沒有使用中的交易記錄，就會遺失該部分記錄中的所有交易。</span><span class="sxs-lookup"><span data-stu-id="d053b-123">If the active transaction log is unavailable, all transactions in that part of the log are lost.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d053b-124">在大量記錄復原模式下，備份包含大量記錄作業的記錄時，需要存取資料庫中的所有資料檔案。</span><span class="sxs-lookup"><span data-stu-id="d053b-124">Under the bulk-logged recovery model, backing up any log that contains bulk-logged operations requires access to all data files in the database.</span></span> <span data-ttu-id="d053b-125">如果無法存取資料檔案，就無法備份交易記錄。</span><span class="sxs-lookup"><span data-stu-id="d053b-125">If the data files cannot be accessed, the transaction log cannot be backed up.</span></span> <span data-ttu-id="d053b-126">在這種情況下，您必須手動重做最近一次備份記錄之後進行的所有變更。</span><span class="sxs-lookup"><span data-stu-id="d053b-126">In that case, you have to manually redo all changes that were made since the most recent log backup.</span></span>  
  
     <span data-ttu-id="d053b-127">如需詳細資訊，請參閱[結尾記錄備份 &#40;SQL Server&#41;](tail-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d053b-127">For more information, see [Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="d053b-128">還原最新的完整資料庫備份，但不復原資料庫 (RESTORE DATABASE *database_name* FROM *backup_device* WITH NORECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="d053b-128">Restore the most recent full database backup without recovering the database (RESTORE DATABASE *database_name* FROM *backup_device* WITH NORECOVERY).</span></span>  
  
3.  <span data-ttu-id="d053b-129">如果有差異備份存在，請還原最新的備份，但是不要復原資料庫 (RESTORE DATABASE *database_name* FROM *differential_backup_device* WITH NORECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="d053b-129">If differential backups exist, restore the most recent one without recovering the database (RESTORE DATABASE *database_name* FROM *differential_backup_device* WITH NORECOVERY).</span></span>  
  
     <span data-ttu-id="d053b-130">還原最近一次的差異備份，可減少必須還原的記錄備份數目。</span><span class="sxs-lookup"><span data-stu-id="d053b-130">Restoring the most recent differential backup reduces the number of log backups that must be restored.</span></span>  
  
4.  <span data-ttu-id="d053b-131">從剛才還原的備份之後所建立的第一個交易記錄備份開始，依順序以 NORECOVERY 還原記錄。</span><span class="sxs-lookup"><span data-stu-id="d053b-131">Starting with the first transaction log backup that was created after the backup you just restored, restore the logs in sequence with NORECOVERY.</span></span>  
  
5.  <span data-ttu-id="d053b-132">復原資料庫 (RESTORE DATABASE *database_name* WITH RECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="d053b-132">Recover the database (RESTORE DATABASE *database_name* WITH RECOVERY).</span></span> <span data-ttu-id="d053b-133">或者，這個步驟也可以合併在還原最後的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="d053b-133">Alternatively, this step can be combined with restoring the last log backup.</span></span>  
  
 <span data-ttu-id="d053b-134">下圖顯示此還原順序。</span><span class="sxs-lookup"><span data-stu-id="d053b-134">The following illustration shows this restore sequence.</span></span> <span data-ttu-id="d053b-135">在失敗發生之後 (1)，會建立結尾記錄備份 (2)。</span><span class="sxs-lookup"><span data-stu-id="d053b-135">After a failure occurs (1), a tail-log backup is created (2).</span></span> <span data-ttu-id="d053b-136">接下來，資料庫會還原至失敗點。</span><span class="sxs-lookup"><span data-stu-id="d053b-136">Next, the database is restored to the point of the failure.</span></span> <span data-ttu-id="d053b-137">這個程序牽涉到還原資料庫備份、後續的差異備份，以及在差異備份之後所進行的每一個記錄備份，包括結尾記錄備份在內。</span><span class="sxs-lookup"><span data-stu-id="d053b-137">This involves restoring a database backup, a subsequent differential backup, and every log backup taken after the differential backup, including the tail-log backup.</span></span>  
  
 <span data-ttu-id="d053b-138">![完成資料庫還原至失敗的時間](../../database-engine/media/bnrr-rmfull1-db-failure-pt.gif "完成資料庫還原至失敗的時間")</span><span class="sxs-lookup"><span data-stu-id="d053b-138">![Complete database restore to the time of a failure](../../database-engine/media/bnrr-rmfull1-db-failure-pt.gif "Complete database restore to the time of a failure")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d053b-139">當您將資料庫備份還原至不同的伺服器執行個體時，請參閱 [使用備份與還原複製資料庫](../databases/copy-databases-with-backup-and-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="d053b-139">When you restore a database backup onto a different server instance, see [Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md).</span></span>  
  
###  <a name="basic-transact-sql-restore-syntax"></a><a name="TsqlSyntax"></a> <span data-ttu-id="d053b-140">基本 Transact-SQL RESTORE 語法</span><span class="sxs-lookup"><span data-stu-id="d053b-140">Basic Transact-SQL RESTORE Syntax</span></span>  
 <span data-ttu-id="d053b-141">上圖中還原順序的基本 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] 語法如下：</span><span class="sxs-lookup"><span data-stu-id="d053b-141">The basic [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] syntax for the restore sequence in the preceding illustration is as follows:</span></span>  
  
1.  <span data-ttu-id="d053b-142">RESTORE DATABASE *&lt;database&gt;* FROM *full database backup* WITH NORECOVERY;</span><span class="sxs-lookup"><span data-stu-id="d053b-142">RESTORE DATABASE *database* FROM *full database backup* WITH NORECOVERY;</span></span>  
  
2.  <span data-ttu-id="d053b-143">RESTORE DATABASE *database* FROM *full_differential_backup* WITH NORECOVERY;</span><span class="sxs-lookup"><span data-stu-id="d053b-143">RESTORE DATABASE *database* FROM *full_differential_backup* WITH NORECOVERY;</span></span>  
  
3.  <span data-ttu-id="d053b-144">RESTORE LOG *database* FROM *log_backup* WITH NORECOVERY;</span><span class="sxs-lookup"><span data-stu-id="d053b-144">RESTORE LOG *database* FROM *log_backup* WITH NORECOVERY;</span></span>  
  
     <span data-ttu-id="d053b-145">針對其他每個記錄備份重複此還原記錄步驟。</span><span class="sxs-lookup"><span data-stu-id="d053b-145">Repeat this restore-log step for each additional log backup.</span></span>  
  
4.  <span data-ttu-id="d053b-146">RESTORE DATABASE *&lt;database&gt;* WITH RECOVERY;</span><span class="sxs-lookup"><span data-stu-id="d053b-146">RESTORE DATABASE *database* WITH RECOVERY;</span></span>  
  
###  <a name="example-recovering-to-the-point-of-failure-transact-sql"></a><a name="ExampleToPoFTsql"></a> <span data-ttu-id="d053b-147">範例：復原到失敗點 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d053b-147">Example: Recovering to the Point of Failure (Transact-SQL)</span></span>  
 <span data-ttu-id="d053b-148">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 範例顯示將資料庫還原到失敗點之還原順序中的基本選項。</span><span class="sxs-lookup"><span data-stu-id="d053b-148">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] example shows the essential options in a restore sequence that restores the database to the point of failure.</span></span> <span data-ttu-id="d053b-149">此範例會建立資料庫的結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="d053b-149">The example creates a tail-log backup of the database.</span></span> <span data-ttu-id="d053b-150">接下來，此範例會還原完整的資料庫備份和記錄備份，然後還原結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="d053b-150">Next, the example restores a full database backup and log backup and then restores the tail-log backup.</span></span> <span data-ttu-id="d053b-151">此範例會在一個不同的最後步驟中復原資料庫。</span><span class="sxs-lookup"><span data-stu-id="d053b-151">The example recovers the database in a separate, final step.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d053b-152">此範例使用 [完整資料庫備份 &#40;SQL Server&#41;](full-database-backups-sql-server.md)的＜相容性支援＞一節。</span><span class="sxs-lookup"><span data-stu-id="d053b-152">This example uses a database backup and log backup that is created in the "Using Database Backups Under the Full Recovery Model" section in [Full Database Backups &#40;SQL Server&#41;](full-database-backups-sql-server.md).</span></span> <span data-ttu-id="d053b-153">在資料庫備份之前， [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例資料庫會設定為使用完整復原模式。</span><span class="sxs-lookup"><span data-stu-id="d053b-153">Before the database backup, the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database was set to use the full recovery model.</span></span>  
  
```  
USE master;  
--Create tail-log backup.  
BACKUP LOG AdventureWorks2012   
TO DISK = 'Z:\SQLServerBackups\AdventureWorksFullRM.bak'    
   WITH NORECOVERY;   
GO  
--Restore the full database backup (from backup set 1).  
RESTORE DATABASE AdventureWorks2012   
  FROM DISK = 'Z:\SQLServerBackups\AdventureWorksFullRM.bak'   
  WITH FILE=1,   
    NORECOVERY;  
  
--Restore the regular log backup (from backup set 2).  
RESTORE LOG AdventureWorks2012   
  FROM DISK = 'Z:\SQLServerBackups\AdventureWorksFullRM.bak'   
  WITH FILE=2,   
    NORECOVERY;  
  
--Restore the tail-log backup (from backup set 3).  
RESTORE LOG AdventureWorks2012   
  FROM DISK = 'Z:\SQLServerBackups\AdventureWorksFullRM.bak'  
  WITH FILE=3,   
    NORECOVERY;  
GO  
--recover the database:  
RESTORE DATABASE AdventureWorks2012 WITH RECOVERY;  
GO  
```  
  
##  <a name="restoring-a-database-to-a-point-within-a-log-backup"></a><a name="PointWithinBackup"></a> <span data-ttu-id="d053b-154">將資料庫還原到記錄備份內的時間點</span><span class="sxs-lookup"><span data-stu-id="d053b-154">Restoring a Database to a Point Within a Log Backup</span></span>  
 <span data-ttu-id="d053b-155">在完整復原模式下，完整資料庫還原通常可以復原到某個時間點、標示的交易或記錄備份內的 LSN。</span><span class="sxs-lookup"><span data-stu-id="d053b-155">Under the full recovery model, a complete database restore can usually be recovered to a point of time, a marked transaction, or an LSN within a log backup.</span></span> <span data-ttu-id="d053b-156">然而，在大量記錄復原模式下，如果記錄備份包含大量記錄的變更，則無法進行時間點復原。</span><span class="sxs-lookup"><span data-stu-id="d053b-156">However, under the bulk-logged recovery model, if the log backup contains bulk-logged changes, point-in-time recovery is not possible.</span></span>  
  
### <a name="sample-point-in-time-restore-scenarios"></a><span data-ttu-id="d053b-157">範例時間點還原案例</span><span class="sxs-lookup"><span data-stu-id="d053b-157">Sample Point-in-Time Restore Scenarios</span></span>  
 <span data-ttu-id="d053b-158">下列範例假設有一個關鍵任務的資料庫系統，每天午夜時會建立一次完整資料庫備份，從星期一到星期六每小時整點時會建立一次差異資料庫備份，而全天每隔 10 分鐘會建立一次交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="d053b-158">The following example assumes a mission-critical database system for which a full database backup is created daily at midnight, a differential database backup is created on the hour, Monday through Saturday, and transaction log backups are created every 10 minutes throughout the day.</span></span> <span data-ttu-id="d053b-159">若要將資料庫還原至星期三 5:19 A.M. 時的狀態，</span><span class="sxs-lookup"><span data-stu-id="d053b-159">To restore the database to the state is was in at 5:19 A.M.</span></span> <span data-ttu-id="d053b-160">請執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d053b-160">Wednesday, do the following:</span></span>  
  
1.  <span data-ttu-id="d053b-161">還原星期二午夜建立的完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="d053b-161">Restore the full database backup that was created Tuesday at midnight.</span></span>  
  
2.  <span data-ttu-id="d053b-162">還原星期三上午 5:00 建立的差異資料庫備份</span><span class="sxs-lookup"><span data-stu-id="d053b-162">Restore the differential database backup that was created at 5:00 A.M.</span></span> <span data-ttu-id="d053b-163">。</span><span class="sxs-lookup"><span data-stu-id="d053b-163">on Wednesday.</span></span>  
  
3.  <span data-ttu-id="d053b-164">套用星期三上午 5:10 建立的交易記錄備份，</span><span class="sxs-lookup"><span data-stu-id="d053b-164">Apply the transaction log backup that was created at 5:10 A.M.</span></span> <span data-ttu-id="d053b-165">。</span><span class="sxs-lookup"><span data-stu-id="d053b-165">on Wednesday.</span></span>  
  
4.  <span data-ttu-id="d053b-166">套用星期三上午 5:20 建立的交易記錄備份，</span><span class="sxs-lookup"><span data-stu-id="d053b-166">Apply the transaction log backup that was created 5:20 A.M.</span></span> <span data-ttu-id="d053b-167">並指定復原程序僅適用於上午 5:19 之前發生的交易。</span><span class="sxs-lookup"><span data-stu-id="d053b-167">on Wednesday, specifying that the recovery process applies only to transactions that occurred before 5:19 A.M.</span></span>  
  
 <span data-ttu-id="d053b-168">或者，如果需要將資料庫還原至星期四 3:04 A.M. 時的狀態，</span><span class="sxs-lookup"><span data-stu-id="d053b-168">Alternatively, if the database needs to be restored to its state at 3:04 A.M.</span></span> <span data-ttu-id="d053b-169">但是無法使用星期四 3:00 A.M. 時建立的差異資料庫備份，</span><span class="sxs-lookup"><span data-stu-id="d053b-169">Thursday, but the differential database backup that was created at 3:00 A.M.</span></span> <span data-ttu-id="d053b-170">則執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="d053b-170">Thursday is unavailable, do the following:</span></span>  
  
1.  <span data-ttu-id="d053b-171">還原星期三午夜建立的資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="d053b-171">Restore the database backup that was created Wednesday at midnight.</span></span>  
  
2.  <span data-ttu-id="d053b-172">還原星期四上午 2:00 建立的差異資料庫備份</span><span class="sxs-lookup"><span data-stu-id="d053b-172">Restore the differential database backup that was created at 2:00 A.M.</span></span> <span data-ttu-id="d053b-173">建立的交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="d053b-173">on Thursday.</span></span>  
  
3.  <span data-ttu-id="d053b-174">套用星期四上午 2:10 到</span><span class="sxs-lookup"><span data-stu-id="d053b-174">Apply all the transaction log backups created from 2:10 A.M.</span></span> <span data-ttu-id="d053b-175">變成上午 3:00。</span><span class="sxs-lookup"><span data-stu-id="d053b-175">to 3:00 A.M.</span></span> <span data-ttu-id="d053b-176">建立的交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="d053b-176">on Thursday.</span></span>  
  
4.  <span data-ttu-id="d053b-177">套用星期四上午 3:10 建立的交易記錄備份，</span><span class="sxs-lookup"><span data-stu-id="d053b-177">Apply the transaction log backup that was created at 3:10 A.M.</span></span> <span data-ttu-id="d053b-178">並在上午 3:04 停止復原程序。</span><span class="sxs-lookup"><span data-stu-id="d053b-178">on Thursday, stopping the recovery process at 3:04 A.M.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d053b-179">如需特定時間點還原的範例，請參閱 [將 SQL Server 資料庫還原至某個時間點 &#40;完整復原模式&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)的＜相容性支援＞一節。</span><span class="sxs-lookup"><span data-stu-id="d053b-179">For an example of a point-in-time restore, see [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="d053b-180">相關工作</span><span class="sxs-lookup"><span data-stu-id="d053b-180">Related Tasks</span></span>  
 <span data-ttu-id="d053b-181">**還原完整資料庫備份**</span><span class="sxs-lookup"><span data-stu-id="d053b-181">**To restore a full database backup**</span></span>  
  
-   [<span data-ttu-id="d053b-182">還原資料庫備份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="d053b-182">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="d053b-183">將資料庫還原到新位置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d053b-183">Restore a Database to a New Location &#40;SQL Server&#41;</span></span>](restore-a-database-to-a-new-location-sql-server.md)  
  
 <span data-ttu-id="d053b-184">**還原差異資料庫備份**</span><span class="sxs-lookup"><span data-stu-id="d053b-184">**To restore a differential database backup**</span></span>  
  
-   [<span data-ttu-id="d053b-185">還原差異資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d053b-185">Restore a Differential Database Backup &#40;SQL Server&#41;</span></span>](restore-a-differential-database-backup-sql-server.md)  
  
 <span data-ttu-id="d053b-186">**還原交易記錄備份**</span><span class="sxs-lookup"><span data-stu-id="d053b-186">**To restore a transaction log backup**</span></span>  
  
-   [<span data-ttu-id="d053b-187">還原交易記錄備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d053b-187">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
 <span data-ttu-id="d053b-188">**使用 SQL Server 管理物件 (SMO) 還原備份**</span><span class="sxs-lookup"><span data-stu-id="d053b-188">**To restore a backup by using SQL Server Management Objects (SMO)**</span></span>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A>  
  
 <span data-ttu-id="d053b-189">**將資料庫還原到記錄備份內的時間點**</span><span class="sxs-lookup"><span data-stu-id="d053b-189">**To restore a database to a point within a log backup**</span></span>  
  
-   [<span data-ttu-id="d053b-190">將 SQL Server 資料庫還原至某個時間點 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="d053b-190">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   [<span data-ttu-id="d053b-191">復原包含標示之交易的相關資料庫</span><span class="sxs-lookup"><span data-stu-id="d053b-191">Recovery of Related  Databases That Contain Marked Transaction</span></span>](recovery-of-related-databases-that-contain-marked-transaction.md)  
  
-   [<span data-ttu-id="d053b-192">復原到記錄序號 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d053b-192">Recover to a Log Sequence Number &#40;SQL Server&#41;</span></span>](recover-to-a-log-sequence-number-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="d053b-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d053b-193">See Also</span></span>  
 <span data-ttu-id="d053b-194">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d053b-194">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="d053b-195">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d053b-195">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="d053b-196">[套用交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d053b-196">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="d053b-197">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d053b-197">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 <span data-ttu-id="d053b-198">[完整資料庫備份 &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d053b-198">[Full Database Backups &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span></span>  
 <span data-ttu-id="d053b-199">[差異備份 &#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d053b-199">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="d053b-200">[備份概觀 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d053b-200">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="d053b-201">還原和復原概觀 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d053b-201">Restore and Recovery Overview &#40;SQL Server&#41;</span></span>](restore-and-recovery-overview-sql-server.md)  
  
  
