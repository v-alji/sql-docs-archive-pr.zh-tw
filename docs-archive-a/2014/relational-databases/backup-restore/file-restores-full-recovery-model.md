---
title: 檔案還原 (完整復原模式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- file restores [SQL Server]
- full recovery model [SQL Server], performing restores
- restoring files [SQL Server], Transact-SQL restore sequence
- restoring files [SQL Server]
- file restores [SQL Server], full recovery model
- restoring files [SQL Server], full recovery model
- Transact-SQL restore sequence
- file restores [SQL Server], Transact-SQL restore sequence
ms.assetid: d2236a2a-4cf1-4c3f-b542-f73f6096e15c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 488515ec900867f13d33580402e36a3f98747bb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699832"
---
# <a name="file-restores-full-recovery-model"></a><span data-ttu-id="75ba3-102">檔案還原 (完整復原模式)</span><span class="sxs-lookup"><span data-stu-id="75ba3-102">File Restores (Full Recovery Model)</span></span>
  <span data-ttu-id="75ba3-103">這個主題僅與在完整或大量載入復原模式下，包含多個檔案或檔案群組的資料庫有關。</span><span class="sxs-lookup"><span data-stu-id="75ba3-103">This topic is relevant only for databases that contain multiple files or filegroups under the full or bulk-load recovery model.</span></span>  
  
 <span data-ttu-id="75ba3-104">檔案還原的目的是還原一個或多個損毀的檔案，而不還原整個資料庫。</span><span class="sxs-lookup"><span data-stu-id="75ba3-104">In a file restore, the goal is to restore one or more damaged files without restoring the whole database.</span></span> <span data-ttu-id="75ba3-105">檔案還原實例包含複製、向前復原及復原適當資料的單一還原順序。</span><span class="sxs-lookup"><span data-stu-id="75ba3-105">A file restore scenario consists of a single restore sequence that copies, rolls forward, and recovers the appropriate data</span></span>  
  
 <span data-ttu-id="75ba3-106">如果正在還原的檔案群組為可讀寫，則必須在還原最後一個資料或差異備份之後，套用無間斷的記錄備份鏈結。</span><span class="sxs-lookup"><span data-stu-id="75ba3-106">If the filegroup that is being restored is read/write, an unbroken chain of log backups must be applied after the last data or differential backup is restored.</span></span> <span data-ttu-id="75ba3-107">這會將檔案群組向前復原到位於記錄檔內目前使用中記錄檔記錄上的記錄檔記錄。</span><span class="sxs-lookup"><span data-stu-id="75ba3-107">This brings the filegroup forward to the log records in the current active log records in the log file.</span></span> <span data-ttu-id="75ba3-108">復原點通常接近記錄的結尾，但不一定如此。</span><span class="sxs-lookup"><span data-stu-id="75ba3-108">The recovery point is typically near the end of log, but not necessarily.</span></span>  
  
 <span data-ttu-id="75ba3-109">如果正在還原的檔案群組為唯讀，通常沒有必要套用記錄備份，所以會略過。</span><span class="sxs-lookup"><span data-stu-id="75ba3-109">If the filegroup that is being restored is read-only, usually applying log backups is unnecessary and is skipped.</span></span> <span data-ttu-id="75ba3-110">如果是在檔案變成唯讀之後進行的備份，此備份就是要還原的最後一個備份。</span><span class="sxs-lookup"><span data-stu-id="75ba3-110">If the backup was taken after the file became read-only, that is the last backup to restore.</span></span> <span data-ttu-id="75ba3-111">向前復原會在目標點停止。</span><span class="sxs-lookup"><span data-stu-id="75ba3-111">Roll forward stops at the target point.</span></span>  
  
 <span data-ttu-id="75ba3-112">這些檔案還原實例如下：</span><span class="sxs-lookup"><span data-stu-id="75ba3-112">The file-restore scenarios are as follows:</span></span>  
  
-   <span data-ttu-id="75ba3-113">離線檔案還原</span><span class="sxs-lookup"><span data-stu-id="75ba3-113">Offline file restore</span></span>  
  
     <span data-ttu-id="75ba3-114">在 *「離線檔案還原」* (Offline File Restore) 中，還原損毀的檔案或檔案群組時，資料庫處於離線狀態。</span><span class="sxs-lookup"><span data-stu-id="75ba3-114">In an *offline file restore*, the database is offline while damaged files or filegroups are restored.</span></span> <span data-ttu-id="75ba3-115">在還原順序結束後，資料庫會恢復上線。</span><span class="sxs-lookup"><span data-stu-id="75ba3-115">At the end of the restore sequence, the database comes online.</span></span>  
  
     <span data-ttu-id="75ba3-116">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的所有版本都支援離線檔案還原。</span><span class="sxs-lookup"><span data-stu-id="75ba3-116">All editions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] support offline file restore.</span></span>  
  
-   <span data-ttu-id="75ba3-117">線上檔案還原</span><span class="sxs-lookup"><span data-stu-id="75ba3-117">Online file restore</span></span>  
  
     <span data-ttu-id="75ba3-118">在 *「線上檔案還原」* (Online File Restore) 中，如果資料庫在還原期間處於線上，則在檔案還原期間也會處於線上。</span><span class="sxs-lookup"><span data-stu-id="75ba3-118">In an *online file restore*, if database is online at restore time, it remains online during the file restore.</span></span> <span data-ttu-id="75ba3-119">不過，在還原作業期間，包含正在還原之檔案的每個檔案群組都會離線。</span><span class="sxs-lookup"><span data-stu-id="75ba3-119">However, each filegroup in which a file is being restored is offline during the restore operation.</span></span> <span data-ttu-id="75ba3-120">離線檔案群組中的所有檔案都復原後，檔案群組就會自動回到線上。</span><span class="sxs-lookup"><span data-stu-id="75ba3-120">After all the files in an offline filegroup are recovered, the filegroup is automatically brought online.</span></span>  
  
     <span data-ttu-id="75ba3-121">如需線上頁面和檔案還原支援的相關資訊，請參閱 [SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="75ba3-121">For information about support for online page and file restore, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="75ba3-122">如需線上還原的詳細資訊，請參閱[線上還原 &#40;SQL Server&#41;](online-restore-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="75ba3-122">For more information about online restores, see [Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md).</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="75ba3-123">如果您想要讓資料庫離線以進行檔案還原，請在啟動還原順序之前，先執行下列 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) 陳述式來使資料庫離線：ALTER DATABASE *database_name* SET OFFLINE。</span><span class="sxs-lookup"><span data-stu-id="75ba3-123">If you want the database to be offline for a file restore, take the database offline before you start the restore sequence by executing the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) statement: ALTER DATABASE *database_name* SET OFFLINE.</span></span>  
  
  
  
##  <a name="restoring-damaged-files-from-file-backups"></a><a name="Overview"></a> <span data-ttu-id="75ba3-124">從檔案備份還原損壞的檔案</span><span class="sxs-lookup"><span data-stu-id="75ba3-124">Restoring Damaged Files from File Backups</span></span>  
  
1.  <span data-ttu-id="75ba3-125">在還原一個或多個損壞的檔案之前，請嘗試建立 [結尾記錄備份](tail-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="75ba3-125">Before restoring one or more damaged files, attempt to create a [tail-log backup](tail-log-backups-sql-server.md).</span></span>  
  
     <span data-ttu-id="75ba3-126">如果記錄已經損壞，就無法建立結尾記錄備份，而且您必須還原整個資料庫。</span><span class="sxs-lookup"><span data-stu-id="75ba3-126">If the log has been damaged, a tail-log backup cannot be created, and you must restore the whole database.</span></span>  
  
     <span data-ttu-id="75ba3-127">如需如何備份交易記錄的相關資訊，請參閱[交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="75ba3-127">For information about how to back up a transaction log, see [Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="75ba3-128">如果是離線檔案還原，一定要在檔案還原之前進行結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="75ba3-128">For an offline file restore, you must always take a tail-log backup before the file restore.</span></span> <span data-ttu-id="75ba3-129">如果是線上檔案還原，一定要在檔案還原之後進行記錄備份。</span><span class="sxs-lookup"><span data-stu-id="75ba3-129">For an online file restore, you must always take the log backup after the file restore.</span></span> <span data-ttu-id="75ba3-130">為了讓檔案可以復原到與資料庫其餘部分一致的狀態，進行這個記錄備份有其必要。</span><span class="sxs-lookup"><span data-stu-id="75ba3-130">This log backup is necessary to allow for the file to be recovered to a state consistent with the rest of the database.</span></span>  
  
2.  <span data-ttu-id="75ba3-131">從每個損毀檔案的最近一次檔案備份還原該檔案。</span><span class="sxs-lookup"><span data-stu-id="75ba3-131">Restore each damaged file from the most recent file backup of that file.</span></span>  
  
3.  <span data-ttu-id="75ba3-132">還原每個已還原檔案的最新差異檔案備份 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="75ba3-132">Restore the most recent differential file backup, if any, for each restored file.</span></span>  
  
4.  <span data-ttu-id="75ba3-133">依序還原交易記錄備份，從包含最舊還原檔案的備份開始，到步驟 1 所建立的結尾記錄備份結束。</span><span class="sxs-lookup"><span data-stu-id="75ba3-133">Restore transaction log backups in sequence, starting with the backup that covers the oldest of the restored files and ending with the tail-log backup created in step 1.</span></span>  
  
     <span data-ttu-id="75ba3-134">您必須還原在檔案備份之後建立的交易記錄備份，才能讓資料庫恢復一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="75ba3-134">You must restore the transaction log backups that were created after the file backups to bring the database to a consistent state.</span></span> <span data-ttu-id="75ba3-135">交易記錄備份可以快速地向前復原，因為只需套用適用於還原檔案的變更。</span><span class="sxs-lookup"><span data-stu-id="75ba3-135">The transaction log backups can be rolled forward quickly, because only the changes that apply to the restored files are applied.</span></span> <span data-ttu-id="75ba3-136">還原個別檔案比還原整個資料庫更為理想，因為不需複製未受損的檔案，便可接著向前復原。</span><span class="sxs-lookup"><span data-stu-id="75ba3-136">Restoring individual files can be better than restoring the whole database, because undamaged files are not copied and then rolled forward.</span></span> <span data-ttu-id="75ba3-137">不過，仍然需要讀取記錄備份的整個鏈結。</span><span class="sxs-lookup"><span data-stu-id="75ba3-137">However, the whole chain of log backups still has to be read.</span></span>  
  
5.  <span data-ttu-id="75ba3-138">復原資料庫。</span><span class="sxs-lookup"><span data-stu-id="75ba3-138">Recover the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75ba3-139">檔案備份可以用來將資料庫還原至較早的時間點。</span><span class="sxs-lookup"><span data-stu-id="75ba3-139">File backups can be used to restore the database to an earlier point in time.</span></span> <span data-ttu-id="75ba3-140">若要這樣做，您必須還原整個檔案備份組，然後依序還原交易記錄備份，以回到上一次還原的檔案備份結尾之後的目標時間點。</span><span class="sxs-lookup"><span data-stu-id="75ba3-140">To do this, you must restore a complete set of file backups, and then restore transaction log backups in sequence to reach a target point that is after the end of the most recent restored file backup.</span></span> <span data-ttu-id="75ba3-141">如需時間點還原的詳細資訊，請參閱[將 SQL Server 資料庫還原至某個時間點 &#40;完整復原模式&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)。</span><span class="sxs-lookup"><span data-stu-id="75ba3-141">For more information about point-in-time recovery, see [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
## <a name="transact-sql-restore-sequence-for-an-offline-file-restore-full-recovery-model"></a><span data-ttu-id="75ba3-142">離線檔案還原的 Transact-SQL 還原順序 (完整復原模式)</span><span class="sxs-lookup"><span data-stu-id="75ba3-142">Transact-SQL Restore Sequence for an Offline File Restore (Full Recovery Model)</span></span>  
 <span data-ttu-id="75ba3-143">檔案還原實例包含複製、向前復原及復原適當資料的單一還原順序。</span><span class="sxs-lookup"><span data-stu-id="75ba3-143">A file restore scenario consists of a single restore sequence that copies, rolls forward, and recovers the appropriate data.</span></span>  
  
 <span data-ttu-id="75ba3-144">本節說明檔案還原順序的基本 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 選項。</span><span class="sxs-lookup"><span data-stu-id="75ba3-144">This section shows the essential [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) options for a file-restore sequence.</span></span> <span data-ttu-id="75ba3-145">會省略與這個檔案還原無關的語法和詳細資料。</span><span class="sxs-lookup"><span data-stu-id="75ba3-145">Syntax and details that are not relevant to this purpose are omitted.</span></span>  
  
 <span data-ttu-id="75ba3-146">下列範例還原順序顯示如何使用 WITH NORECOVERY 來離線還原兩個次要檔案 ( `A` 和 `B`)。</span><span class="sxs-lookup"><span data-stu-id="75ba3-146">The following sample restore sequence shows an offline restore of two secondary files, `A` and `B`, using WITH NORECOVERY.</span></span> <span data-ttu-id="75ba3-147">接下來，此範例會以 NORECOVERY 套用這兩個記錄備份，然後再使用 WITH RECOVERY 套用結尾記錄備份以進行還原。</span><span class="sxs-lookup"><span data-stu-id="75ba3-147">Next, two log backups are applied with NORECOVERY, followed with the tail-log backup, and this is restored using WITH RECOVERY.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75ba3-148">下列範例還原順序是透過讓檔案離線來啟動，然後建立結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="75ba3-148">The following sample restore sequence starts by taking the file offline and then creates a tail-log backup.</span></span>  
  
```  
--Take the file offline.  
ALTER DATABASE database_name MODIFY FILE SET OFFLINE;  
-- Back up the currently active transaction log.  
BACKUP LOG database_name  
   TO <tail_log_backup>  
   WITH NORECOVERY;  
GO   
-- Restore the files.  
RESTORE DATABASE database_name FILE=name   
   FROM <file_backup_of_file_A>   
   WITH NORECOVERY;  
RESTORE DATABASE database_name FILE=<name> ......  
   FROM <file_backup_of_file_B>   
   WITH NORECOVERY;  
-- Restore the log backups.  
RESTORE LOG database_name FROM <log_backup>   
   WITH NORECOVERY;  
RESTORE LOG database_name FROM <log_backup>   
   WITH NORECOVERY;  
RESTORE LOG database_name FROM <tail_log_backup>   
   WITH RECOVERY;  
```  
  
## <a name="examples"></a><span data-ttu-id="75ba3-149">範例</span><span class="sxs-lookup"><span data-stu-id="75ba3-149">Examples</span></span>  
  
-   [<span data-ttu-id="75ba3-150">範例：線上還原讀取/寫入檔案 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="75ba3-150">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="75ba3-151">範例：線上還原唯讀檔案 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="75ba3-151">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="75ba3-152">範例：離線還原主要檔案群組與另一個檔案群組 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="75ba3-152">Example: Offline Restore of Primary and One Other Filegroup &#40;Full Recovery Model&#41;</span></span>](example-offline-restore-of-primary-and-one-other-filegroup-full-recovery-model.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="75ba3-153">相關工作</span><span class="sxs-lookup"><span data-stu-id="75ba3-153">Related Tasks</span></span>  
 <span data-ttu-id="75ba3-154">**還原檔案和檔案群組**</span><span class="sxs-lookup"><span data-stu-id="75ba3-154">**To restore files and filegroups**</span></span>  
  
-   [<span data-ttu-id="75ba3-155">將檔案還原到新位置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="75ba3-155">Restore Files to a New Location &#40;SQL Server&#41;</span></span>](restore-files-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="75ba3-156">還原檔案和檔案群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="75ba3-156">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
-   <span data-ttu-id="75ba3-157"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="75ba3-157"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="75ba3-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75ba3-158">See Also</span></span>  
 <span data-ttu-id="75ba3-159">[備份與還原：互通性與共存性 &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="75ba3-159">[Backup and Restore: Interoperability and Coexistence &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span></span>  
 <span data-ttu-id="75ba3-160">[差異備份 &#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="75ba3-160">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="75ba3-161">[完整檔案備份 &#40;SQL Server&#41;](full-file-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="75ba3-161">[Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md) </span></span>  
 <span data-ttu-id="75ba3-162">[備份概觀 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="75ba3-162">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="75ba3-163">[還原和復原概觀 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="75ba3-163">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="75ba3-164">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="75ba3-164">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="75ba3-165">[完整資料庫還原 &#40;簡單復原模式&#41;](complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="75ba3-165">[Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) </span></span>  
 [<span data-ttu-id="75ba3-166">分次還原 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="75ba3-166">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
