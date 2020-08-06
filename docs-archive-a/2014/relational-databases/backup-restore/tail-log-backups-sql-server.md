---
title: 結尾記錄備份 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up [SQL Server], tail of log
- transaction log backups [SQL Server], tail-log backups
- NO_TRUNCATE clause
- backups [SQL Server], log backups
- tail-log backups
- backups [SQL Server], tail-log backups
ms.assetid: 313ddaf6-ec54-4a81-a104-7ffa9533ca58
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cd7c505701a4edb1f66ca516d06179b2eb1a222d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592071"
---
# <a name="tail-log-backups-sql-server"></a><span data-ttu-id="5db7f-102">結尾記錄備份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5db7f-102">Tail-Log Backups (SQL Server)</span></span>
  <span data-ttu-id="5db7f-103">本主題僅與使用完整或大量記錄復原模式備份和還原 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫有關。</span><span class="sxs-lookup"><span data-stu-id="5db7f-103">This topic is relevant only for backup and restore of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that are using the full or bulk-logged recovery models.</span></span>  
  
 <span data-ttu-id="5db7f-104">「結尾記錄備份」  (tail-log backup) 可擷取任何尚未備份的記錄檔記錄 (「記錄結尾」  (tail of the log))，來防止工作遺失，並保持記錄鏈結完整。</span><span class="sxs-lookup"><span data-stu-id="5db7f-104">A *tail-log backup* captures any log records that have not yet been backed up (the *tail of the log*) to prevent work loss and to keep the log chain intact.</span></span> <span data-ttu-id="5db7f-105">將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫復原到最新時間點之前，必須備份其交易記錄的結尾。</span><span class="sxs-lookup"><span data-stu-id="5db7f-105">Before you can recover a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database to its latest point in time, you must back up the tail of its transaction log.</span></span> <span data-ttu-id="5db7f-106">結尾記錄備份會是資料庫之復原計畫中感興趣的最後一個備份。</span><span class="sxs-lookup"><span data-stu-id="5db7f-106">The tail-log backup will be the last backup of interest in the recovery plan for the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5db7f-107">並不是所有的還原實例都需要結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="5db7f-107">Not all restore scenarios require a tail-log backup.</span></span> <span data-ttu-id="5db7f-108">如果復原點是包含在較早的記錄備份中，則不需要結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="5db7f-108">You do not need a tail-log backup if the recovery point is contained in an earlier log backup.</span></span> <span data-ttu-id="5db7f-109">而且，如果您要移動或取代 (覆寫) 資料庫，而且不需要將它還原至最近備份之後的某個時間點，就不需要有結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="5db7f-109">Also, a tail-log backup is unnecessary if you are moving or replacing (overwriting) a database and do not need to restore it to a point of time after its most recent backup.</span></span>  
  
 
  
##  <a name="scenarios-that-require-a-tail-log-backup"></a><a name="TailLogScenarios"></a> <span data-ttu-id="5db7f-110">需要結尾記錄備份的實例</span><span class="sxs-lookup"><span data-stu-id="5db7f-110">Scenarios That Require a Tail-Log Backup</span></span>  
 <span data-ttu-id="5db7f-111">建議您在下列實例中進行結尾記錄備份：</span><span class="sxs-lookup"><span data-stu-id="5db7f-111">We recommend that you take a tail-log backup in the following scenarios:</span></span>  
  
-   <span data-ttu-id="5db7f-112">如果資料庫在線上，而且您打算執行資料庫的還原作業，請從備份記錄結尾開始。</span><span class="sxs-lookup"><span data-stu-id="5db7f-112">If the database is online and you plan to perform a restore operation on the database, begin by backing up the tail of the log.</span></span> <span data-ttu-id="5db7f-113">若要避免線上資料庫發生錯誤，您必須使用 .。。WITH [BACKUP](/sql/t-sql/statements/backup-transact-sql)語句的 NORECOVERY 選項 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5db7f-113">To avoid an error for an online database, you must use the ... WITH NORECOVERY option of the [BACKUP](/sql/t-sql/statements/backup-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
-   <span data-ttu-id="5db7f-114">如果資料庫離線且無法啟動，並且需要還原資料庫，請先備份記錄結尾。</span><span class="sxs-lookup"><span data-stu-id="5db7f-114">If a database is offline and fails to start and you need to restore the database, first back up the tail of the log.</span></span> <span data-ttu-id="5db7f-115">因為這段時間不會發生交易，所以使用 WITH NORECOVERY 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="5db7f-115">Because no transactions can occur at this time, using the WITH NORECOVERY is optional.</span></span>  
  
-   <span data-ttu-id="5db7f-116">如果資料庫損毀，請嘗試使用 BACKUP 陳述式的 WITH CONTINUE_AFTER_ERROR 選項來進行結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="5db7f-116">If a database is damaged, try to take a tail-log backup by using the WITH CONTINUE_AFTER_ERROR option of the BACKUP statement.</span></span>  
  
     <span data-ttu-id="5db7f-117">在損毀的資料庫上，只有在記錄檔未損壞、資料庫處於支援結尾記錄備份的狀態，以及資料庫未包含任何大量記錄的變更時，記錄結尾的備份才會成功。</span><span class="sxs-lookup"><span data-stu-id="5db7f-117">On a damaged database backing up the tail of the log can succeed only if the log files are undamaged, the database is in a state that supports tail-log backups, and the database does not contain any bulk-logged changes.</span></span> <span data-ttu-id="5db7f-118">如果無法建立結尾記錄備份，則會遺失在最新記錄備份之後確定的任何交易。</span><span class="sxs-lookup"><span data-stu-id="5db7f-118">If a tail-log backup cannot be created, any transactions committed after the latest log backup are lost.</span></span>  
  
 <span data-ttu-id="5db7f-119">下表摘要說明 BACKUP NORECOVERY 和 CONTINUE_AFTER_ERROR 選項。</span><span class="sxs-lookup"><span data-stu-id="5db7f-119">The following table summarizes the BACKUP NORECOVERY and CONTINUE_AFTER_ERROR options.</span></span>  
  
|<span data-ttu-id="5db7f-120">BACKUP LOG 選項</span><span class="sxs-lookup"><span data-stu-id="5db7f-120">BACKUP LOG option</span></span>|<span data-ttu-id="5db7f-121">註解</span><span class="sxs-lookup"><span data-stu-id="5db7f-121">Comments</span></span>|  
|-----------------------|--------------|  
|<span data-ttu-id="5db7f-122">NORECOVERY</span><span class="sxs-lookup"><span data-stu-id="5db7f-122">NORECOVERY</span></span>|<span data-ttu-id="5db7f-123">每當您打算在資料庫上繼續還原作業時，請使用 NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="5db7f-123">Use NORECOVERY whenever you intend to continue with a restore operation on the database.</span></span> <span data-ttu-id="5db7f-124">NORECOVERY 會讓資料庫進入還原狀態。</span><span class="sxs-lookup"><span data-stu-id="5db7f-124">NORECOVERY takes the database into the restoring state.</span></span> <span data-ttu-id="5db7f-125">這樣可以保證資料庫不會在結尾記錄備份之後變更。</span><span class="sxs-lookup"><span data-stu-id="5db7f-125">This guarantees that the database does not change after the tail-log backup.</span></span>  <span data-ttu-id="5db7f-126">除非也指定了 NO_TRUNCATE 選項或 COPY_ONLY 選項，否則會截斷記錄。</span><span class="sxs-lookup"><span data-stu-id="5db7f-126">The log is truncated unless the NO_TRUNCATE option or COPY_ONLY option is also specified.</span></span><br /><br /> <span data-ttu-id="5db7f-127">\*\* \* \* 重要 \* 事項 \* \*\* ：我們建議您避免使用 NO_TRUNCATE，除非資料庫損毀。</span><span class="sxs-lookup"><span data-stu-id="5db7f-127">**\*\* Important \*\*** We recommend that you avoid using NO_TRUNCATE, except when the database is damaged.</span></span>|  
|<span data-ttu-id="5db7f-128">CONTINUE_AFTER_ERROR</span><span class="sxs-lookup"><span data-stu-id="5db7f-128">CONTINUE_AFTER_ERROR</span></span>|<span data-ttu-id="5db7f-129">只有在您要備份受損資料庫的結尾時，才使用 CONTINUE_AFTER_ERROR。</span><span class="sxs-lookup"><span data-stu-id="5db7f-129">Use CONTINUE_AFTER_ERROR only if you are backing up the tail of a damaged database.</span></span><br /><br /> <span data-ttu-id="5db7f-130">注意：當您在損毀的資料庫上使用備份記錄的結尾時，某些通常會在記錄備份中捕捉到的中繼資料可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="5db7f-130">Note: When you use back up the tail of the log on a damaged database, some of the metadata ordinarily captured in log backups might be unavailable.</span></span> <span data-ttu-id="5db7f-131">如需詳細資訊，請參閱本節稍後的[具有不完整備份中繼資料的結尾記錄備份](#IncompleteMetadata)。</span><span class="sxs-lookup"><span data-stu-id="5db7f-131">For more information, see [Tail-Log Backups That Have Incomplete Backup Metadata](#IncompleteMetadata), later in this topic.</span></span>|  
  
##  <a name="tail-log-backups-that-have-incomplete-backup-metadata"></a><a name="IncompleteMetadata"></a><span data-ttu-id="5db7f-132">具有不完整備份中繼資料的尾記錄備份</span><span class="sxs-lookup"><span data-stu-id="5db7f-132">Tail-Log Backups That Have Incomplete Backup Metadata</span></span>  
 <span data-ttu-id="5db7f-133">即使資料庫離線、損毀或遺漏資料檔案，結尾記錄備份還是會擷取記錄檔的結尾。</span><span class="sxs-lookup"><span data-stu-id="5db7f-133">Tail log backups capture the tail of the log even if the database is offline, damaged, or missing data files.</span></span> <span data-ttu-id="5db7f-134">這可能會導致還原資訊命令和 **msdb**產生不完整的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5db7f-134">This might cause incomplete metadata from the restore information commands and **msdb**.</span></span> <span data-ttu-id="5db7f-135">不過，只有中繼資料不完整，所擷取的記錄仍然完整可用。</span><span class="sxs-lookup"><span data-stu-id="5db7f-135">However, only the metadata is incomplete; the captured log is complete and usable.</span></span>  
  
 <span data-ttu-id="5db7f-136">如果結尾記錄備份具有不完整的中繼資料， [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) 資料表中的 **has_incomplete_metadata** 會設為 **1**。</span><span class="sxs-lookup"><span data-stu-id="5db7f-136">If a tail-log backup has incomplete metadata, in the [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) table, **has_incomplete_metadata** is set to **1**.</span></span> <span data-ttu-id="5db7f-137">此外，在 [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)的輸出中， **HasIncompleteMetadata** 也會設為 **1**。</span><span class="sxs-lookup"><span data-stu-id="5db7f-137">Also, in the output of [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql), **HasIncompleteMetadata** is set to **1**.</span></span>  
  
 <span data-ttu-id="5db7f-138">如果結尾記錄備份的中繼資料不完整， [backupfilegroup](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) 資料表將會遺失有關檔案群組在結尾記錄備份期間的大部分資訊。</span><span class="sxs-lookup"><span data-stu-id="5db7f-138">If the metadata in a tail-log backup is incomplete, the [backupfilegroup](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) table will be missing most of the information about filegroups at the time of the tail-log backup.</span></span> <span data-ttu-id="5db7f-139">大部分 **backupfilegroup** 資料表資料行為 NULL，只有下列資料行具有意義：</span><span class="sxs-lookup"><span data-stu-id="5db7f-139">Most of the **backupfilegroup** table columns are NULL; the only meaningful columns are as follows:</span></span>  
  
-   <span data-ttu-id="5db7f-140">**backup_set_id**</span><span class="sxs-lookup"><span data-stu-id="5db7f-140">**backup_set_id**</span></span>  
  
-   <span data-ttu-id="5db7f-141">**filegroup_id**</span><span class="sxs-lookup"><span data-stu-id="5db7f-141">**filegroup_id**</span></span>  
  
-   <span data-ttu-id="5db7f-142">**type**</span><span class="sxs-lookup"><span data-stu-id="5db7f-142">**type**</span></span>  
  
-   <span data-ttu-id="5db7f-143">**type_desc**</span><span class="sxs-lookup"><span data-stu-id="5db7f-143">**type_desc**</span></span>  
  
-   <span data-ttu-id="5db7f-144">**is_readonly**</span><span class="sxs-lookup"><span data-stu-id="5db7f-144">**is_readonly**</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="5db7f-145">相關工作</span><span class="sxs-lookup"><span data-stu-id="5db7f-145">Related Tasks</span></span>  
 <span data-ttu-id="5db7f-146">若要建立結尾記錄備份，請參閱[資料庫損毀時備份交易記錄 &#40;SQL Server&#41;](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5db7f-146">To create a tail-log backup, see [Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md).</span></span>  
  
 <span data-ttu-id="5db7f-147">若要還原交易記錄備份，請參閱[還原交易記錄備份 &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5db7f-147">To restore a transaction log backup, see [Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5db7f-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5db7f-148">See Also</span></span>  
 <span data-ttu-id="5db7f-149">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5db7f-149">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="5db7f-150">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5db7f-150">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="5db7f-151">[SQL Server 資料庫的備份與還原](back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="5db7f-151">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="5db7f-152">[只複製備份 &#40;SQL Server&#41;](copy-only-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5db7f-152">[Copy-Only Backups &#40;SQL Server&#41;](copy-only-backups-sql-server.md) </span></span>  
 <span data-ttu-id="5db7f-153">[交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5db7f-153">[Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="5db7f-154">套用交易記錄備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5db7f-154">Apply Transaction Log Backups &#40;SQL Server&#41;</span></span>](apply-transaction-log-backups-sql-server.md)  
  
  
