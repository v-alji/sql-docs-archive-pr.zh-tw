---
title: 完整檔案備份 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full backups [SQL Server]
- backing up [SQL Server], files or filegroups
- backups [SQL Server], files or filegroups
- full recovery model [SQL Server], full file backups
- file backups [SQL Server], full
- files [SQL Server], backing up
- filegroups [SQL Server], backing up
- file backups [SQL Server]
ms.assetid: a716bf8d-0c5a-490d-aadd-597b3b0fac0c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e2e45dc68afa4d464aa3931075a1c1b3be792e6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598488"
---
# <a name="full-file-backups-sql-server"></a><span data-ttu-id="d3391-102">完整檔案備份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d3391-102">Full File Backups (SQL Server)</span></span>
  <span data-ttu-id="d3391-103">本主題僅與包含多個檔案或檔案群組的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫有關。</span><span class="sxs-lookup"><span data-stu-id="d3391-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases that contain multiple files or filegroups.</span></span>  
  
 <span data-ttu-id="d3391-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫中的檔案可個別進行備份和還原。</span><span class="sxs-lookup"><span data-stu-id="d3391-104">The files in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database can be backed up and restored individually.</span></span> <span data-ttu-id="d3391-105">而且，您可以指定整個檔案群組，而不是個別指定每個構成的檔案。</span><span class="sxs-lookup"><span data-stu-id="d3391-105">Also, you can specify a whole filegroup instead of specifying each constituent file individually.</span></span> <span data-ttu-id="d3391-106">請注意，如果檔案群組的任何檔案離線 (例如因為檔案正在還原中)，整個檔案群組就會離線，並且無法進行備份。</span><span class="sxs-lookup"><span data-stu-id="d3391-106">Note that if any file in a filegroup is offline (for example, because the file is being restored), the whole filegroup is offline and cannot be backed up.</span></span>  
  
 <span data-ttu-id="d3391-107">唯讀檔案群組的檔案備份可以結合部分備份。</span><span class="sxs-lookup"><span data-stu-id="d3391-107">File backups of read-only filegroups can be combined with partial backups.</span></span> <span data-ttu-id="d3391-108">部分備份包含所有讀取/寫入檔案群組，以及一個或多個唯讀檔案群組 (選用)。</span><span class="sxs-lookup"><span data-stu-id="d3391-108">Partial backups include all the read/write filegroups and, optionally, one or more read-only filegroups.</span></span> <span data-ttu-id="d3391-109">如需詳細資訊，請參閱[部分備份 &#40;SQL Server&#41;](partial-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d3391-109">For more information, see [Partial Backups &#40;SQL Server&#41;](partial-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="d3391-110">檔案備份可以當成差異檔案備份的 *「差異基底」* (Differential base)。</span><span class="sxs-lookup"><span data-stu-id="d3391-110">A file backup can serve as the *differential base* for differential file backups.</span></span> <span data-ttu-id="d3391-111">如需詳細資訊，請參閱 [差異備份 &#40;SQL Server&#41;](differential-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d3391-111">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3391-112">完整檔案備份通常稱為「檔案備份」  ，但與「差異檔案備份」  明確對照時除外。</span><span class="sxs-lookup"><span data-stu-id="d3391-112">Full file backups are typically called *file backups*, except when they are being explicitly compared with *differential file backups*.</span></span>  
  
 <span data-ttu-id="d3391-113">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="d3391-113">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="d3391-114">檔案備份的優點</span><span class="sxs-lookup"><span data-stu-id="d3391-114">Benefits of File Backups</span></span>](#Benefits)  
  
-   [<span data-ttu-id="d3391-115">檔案備份的缺點</span><span class="sxs-lookup"><span data-stu-id="d3391-115">Disadvantages of File Backups</span></span>](#Disadvantages)  
  
-   [<span data-ttu-id="d3391-116">檔案備份概觀</span><span class="sxs-lookup"><span data-stu-id="d3391-116">Overview of File Backups</span></span>](#Overview)  
  
-   [<span data-ttu-id="d3391-117">相關工作</span><span class="sxs-lookup"><span data-stu-id="d3391-117">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="benefits-of-file-backups"></a><a name="Benefits"></a> <span data-ttu-id="d3391-118">檔案備份的優點</span><span class="sxs-lookup"><span data-stu-id="d3391-118">Benefits of File Backups</span></span>  
 <span data-ttu-id="d3391-119">檔案備份提供下列優於資料庫備份的優點：</span><span class="sxs-lookup"><span data-stu-id="d3391-119">File backups offer the following advantages over database backups:</span></span>  
  
-   <span data-ttu-id="d3391-120">使用檔案備份可以增加復原的速度，因為這樣可以讓您只還原受損的檔案，而不需要還原資料庫的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="d3391-120">Using file backups can increase the speed of recovery by letting you restore only damaged files, without restoring the rest of the database.</span></span>  
  
     <span data-ttu-id="d3391-121">例如，如果資料庫由數個檔案組成，這些檔案分別位在不同磁碟上，現在有一個磁碟故障了，就只需還原故障磁碟上的檔案。</span><span class="sxs-lookup"><span data-stu-id="d3391-121">For example, if a database consists of several files that are located on different disks and one disk fails, only the file on the failed disk has to be restored.</span></span> <span data-ttu-id="d3391-122">損毀的檔案可以快速予以還原，而且其復原速度也比復原整個資料庫還要快。</span><span class="sxs-lookup"><span data-stu-id="d3391-122">The damaged file can be quickly restored, and recovery is faster than it would be for an entire database.</span></span>  
  
-   <span data-ttu-id="d3391-123">比起完整資料庫備份，檔案備份在排程與媒體處理上彈性更大，因為對於大型資料庫，完整資料庫備份會變得難以管理。</span><span class="sxs-lookup"><span data-stu-id="d3391-123">File backups increase flexibility in scheduling and media handling over full database backups, which for very large databases can become unmanageable.</span></span> <span data-ttu-id="d3391-124">對於含有各種更新特性資料的大型資料庫來說，檔案或檔案群組備份的增強彈性也很有用處。</span><span class="sxs-lookup"><span data-stu-id="d3391-124">The increased flexibility of file or filegroup backups is also useful for large databases that contain data that has varying update characteristics.</span></span>  
  
##  <a name="disadvantages-of-file-backups"></a><a name="Disadvantages"></a> <span data-ttu-id="d3391-125">檔案備份的缺點</span><span class="sxs-lookup"><span data-stu-id="d3391-125">Disadvantages of File Backups</span></span>  
  
-   <span data-ttu-id="d3391-126">相較於完整資料庫備份，檔案備份的主要缺點在於增加管理上的複雜性。</span><span class="sxs-lookup"><span data-stu-id="d3391-126">The primary disadvantage of file backups compared to full database backups is the additional administrative complexity.</span></span> <span data-ttu-id="d3391-127">維護和持續追蹤完整的備份組是相當耗時的工作，其耗費成本甚至可能會超過完整資料庫備份的空間需求。</span><span class="sxs-lookup"><span data-stu-id="d3391-127">Maintaining and keeping track of a complete set of these backups can be a time-consuming task that might outweigh the space requirements of full database backups.</span></span>  
  
-   <span data-ttu-id="d3391-128">如果損毀的檔案沒有備份，媒體故障將可能造成整個資料庫無法復原。</span><span class="sxs-lookup"><span data-stu-id="d3391-128">A media failure can make a complete database unrecoverable if a damaged file lacks a backup.</span></span> <span data-ttu-id="d3391-129">因此，必須維護一組完整的檔案備份，而在完整/大量記錄復原模式下，則還要備份一個或多個記錄備份，至少涵蓋第一次完整檔案備份和最後一次完整檔案備份之間的間隔。</span><span class="sxs-lookup"><span data-stu-id="d3391-129">You must therefore maintain a complete set of file backups, and, for the full/bulk-logged recovery model, one or more log backups covering minimally the interval between the first full file backup and last full file backup.</span></span>  
  
##  <a name="overview-of-file-backups"></a><a name="Overview"></a> <span data-ttu-id="d3391-130">檔案備份概觀</span><span class="sxs-lookup"><span data-stu-id="d3391-130">Overview of File Backups</span></span>  
 <span data-ttu-id="d3391-131">完整檔案備份會備份一個或多個檔案或檔案群組中的所有資料。</span><span class="sxs-lookup"><span data-stu-id="d3391-131">A full file backup backs up all the data in one or more files or filegroups.</span></span> <span data-ttu-id="d3391-132">根據預設，檔案備份會包含足以將檔案向前復原到備份作業結束的記錄檔記錄。</span><span class="sxs-lookup"><span data-stu-id="d3391-132">By default, file backups contain enough log records to roll forward the file to the end of the backup operation.</span></span>  
  
 <span data-ttu-id="d3391-133">對於每一個復原模式來說，備份唯讀檔案或檔案群組都是相同的。</span><span class="sxs-lookup"><span data-stu-id="d3391-133">Backing up a read-only file or filegroup is the same for every recovery model.</span></span> <span data-ttu-id="d3391-134">在完整復原模式下，一組完整的完整檔案備份連同足以涵蓋所有檔案備份的記錄備份，就相當於一個完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="d3391-134">Under the full recovery model, a complete set of full file backups, together with enough log backups to span all the file backups, is the equivalent of a full database backup.</span></span>  
  
 <span data-ttu-id="d3391-135">同一時間只能進行一個檔案備份作業。</span><span class="sxs-lookup"><span data-stu-id="d3391-135">Only one file backup operation can occur at a time.</span></span> <span data-ttu-id="d3391-136">您可以在一個作業中備份多個檔案，但是如果您只需要還原單一檔案，這樣可能延長復原的時間。</span><span class="sxs-lookup"><span data-stu-id="d3391-136">You can back up multiple files in one operation, but this might extend the recovery time if you only have to restore a single file.</span></span> <span data-ttu-id="d3391-137">這是因為若要找到這個檔案，就要讀取整個備份。</span><span class="sxs-lookup"><span data-stu-id="d3391-137">This is because to locate that file, the whole backup is read.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3391-138">您可以從資料庫備份還原個別檔案；不過，若要尋找並還原一個檔案，從資料庫備份著手會比從檔案備份來得更久。</span><span class="sxs-lookup"><span data-stu-id="d3391-138">Individual files can be restored from a database backup; however, locating and restoring a file takes longer from a database backup than from a file backup.</span></span>  
  
### <a name="file-backups-and-the-simple-recovery-model"></a><span data-ttu-id="d3391-139">檔案備份和簡單復原模式</span><span class="sxs-lookup"><span data-stu-id="d3391-139">File Backups and the Simple Recovery Model</span></span>  
 <span data-ttu-id="d3391-140">在簡單復原模式下，必須將所有的讀取/寫入檔案備份在一起。</span><span class="sxs-lookup"><span data-stu-id="d3391-140">Under the simple recovery model, read/write files must all be backed up together.</span></span> <span data-ttu-id="d3391-141">這樣可以確保將資料庫還原到一致的時間點。</span><span class="sxs-lookup"><span data-stu-id="d3391-141">This makes sure that the database can be restored to a consistent point in time.</span></span> <span data-ttu-id="d3391-142">不要個別指定每一個讀取/寫入檔案或檔案群組，請改用 READ_WRITE_FILEGROUPS 選項。</span><span class="sxs-lookup"><span data-stu-id="d3391-142">Instead of individually specifying each read/write file or filegroup, use the READ_WRITE_FILEGROUPS option.</span></span> <span data-ttu-id="d3391-143">這個選項會備份資料庫中的所有讀取/寫入檔案群組。</span><span class="sxs-lookup"><span data-stu-id="d3391-143">This option backs up all the read/write filegroups in the database.</span></span> <span data-ttu-id="d3391-144">指定 READ_WRITE_FILEGROUPS 所建立的備份即稱為「部分備份」。</span><span class="sxs-lookup"><span data-stu-id="d3391-144">A backup that is created by specifying READ_WRITE_FILEGROUPS is known as a partial backup.</span></span> <span data-ttu-id="d3391-145">如需詳細資訊，請參閱[部分備份 &#40;SQL Server&#41;](partial-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d3391-145">For more information, see [Partial Backups &#40;SQL Server&#41;](partial-backups-sql-server.md).</span></span>  
  
### <a name="file-backups-and-the-full-recovery-model"></a><span data-ttu-id="d3391-146">檔案備份和完整復原模式</span><span class="sxs-lookup"><span data-stu-id="d3391-146">File Backups and the Full Recovery Model</span></span>  
 <span data-ttu-id="d3391-147">在完整復原模式下，不論備份策略的其餘部分為何，您都必須備份交易記錄。</span><span class="sxs-lookup"><span data-stu-id="d3391-147">Under the full recovery model, you must back up the transaction log, regardless of the rest of your backup strategy.</span></span> <span data-ttu-id="d3391-148">一組完整的完整檔案備份，連同足以從第一個檔案備份開始涵蓋所有檔案備份的記錄備份，就相當於一個完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="d3391-148">A complete set of full file backups, together with enough log backups to span all the file backups from the start of the first file backup, is the equivalent of a full database backup.</span></span>  
  
 <span data-ttu-id="d3391-149">只使用檔案和記錄備份來還原資料庫可能會很複雜。</span><span class="sxs-lookup"><span data-stu-id="d3391-149">Restoring a database using just file and log backups can be complex.</span></span> <span data-ttu-id="d3391-150">因此，最好是盡可能執行完整資料庫備份，然後在第一次檔案備份之前啟動記錄備份。</span><span class="sxs-lookup"><span data-stu-id="d3391-150">Therefore, if it is possible, it is a best practice to perform a full database backup and start the log backups before the first file backup.</span></span> <span data-ttu-id="d3391-151">下圖顯示在建立資料庫 (時間 t0) 之後不久即建立完整資料庫備份 (時間 t1) 的策略。</span><span class="sxs-lookup"><span data-stu-id="d3391-151">The following illustration shows a strategy in which a full database backup is taken (at time t1) soon after the database is created (at time t0).</span></span> <span data-ttu-id="d3391-152">第一個資料庫備份可讓交易記錄備份啟動。</span><span class="sxs-lookup"><span data-stu-id="d3391-152">This first database backup enables transaction log backups to start.</span></span> <span data-ttu-id="d3391-153">交易記錄備份已排程為依設定的間隔進行。</span><span class="sxs-lookup"><span data-stu-id="d3391-153">Transaction log backups are scheduled to occur at set intervals.</span></span> <span data-ttu-id="d3391-154">當間隔最符合資料庫的商務需求時，就會進行檔案備份。</span><span class="sxs-lookup"><span data-stu-id="d3391-154">File backups occur at whatever interval best meets the business requirements for the database.</span></span> <span data-ttu-id="d3391-155">本圖顯示逐一備份的四個檔案群組。</span><span class="sxs-lookup"><span data-stu-id="d3391-155">This illustration shows each of the four filegroups being backed up one at a time.</span></span> <span data-ttu-id="d3391-156">這些檔案群組的備份順序 (A、C、B、A) 反映了資料庫的商務需求。</span><span class="sxs-lookup"><span data-stu-id="d3391-156">The order in which they are backed up (A, C, B, A) reflects the business requirements of the database.</span></span>  
  
 <span data-ttu-id="d3391-157">![結合資料庫、檔案和記錄備份的策略](../../database-engine/media/bnr-rmfull-3-fulldb-filegrps-log-backups.gif "結合資料庫、檔案和記錄備份的策略")</span><span class="sxs-lookup"><span data-stu-id="d3391-157">![Strategy combining database, file, and log backups](../../database-engine/media/bnr-rmfull-3-fulldb-filegrps-log-backups.gif "Strategy combining database, file, and log backups")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3391-158">在完整復原模式下，還原讀取/寫入檔案備份時必須向前復原交易記錄，以確保檔案與資料庫其餘部分的一致性。</span><span class="sxs-lookup"><span data-stu-id="d3391-158">Under the full recovery model, you must roll forward the transaction log when restoring a read/write file backup to make sure that the file is consistent with the rest of the database.</span></span> <span data-ttu-id="d3391-159">為了避免向前復原過多的交易記錄備份，請考慮使用差異檔案備份。</span><span class="sxs-lookup"><span data-stu-id="d3391-159">To avoid rolling forward a lot of transaction log backups, consider using differential file backups.</span></span> <span data-ttu-id="d3391-160">如需詳細資訊，請參閱 [差異備份 &#40;SQL Server&#41;](differential-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d3391-160">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="d3391-161">相關工作</span><span class="sxs-lookup"><span data-stu-id="d3391-161">Related Tasks</span></span>  
 <span data-ttu-id="d3391-162">**建立檔案或檔案群組備份**</span><span class="sxs-lookup"><span data-stu-id="d3391-162">**To create a file or filegroup backup**</span></span>  
  
-   [<span data-ttu-id="d3391-163">備份檔案和檔案群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d3391-163">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](back-up-files-and-filegroups-sql-server.md)  
  
-   <span data-ttu-id="d3391-164"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="d3391-164"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3391-165">「維護計畫精靈」不支援檔案備份。</span><span class="sxs-lookup"><span data-stu-id="d3391-165">File backups are not supported by the Maintenance Plan Wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3391-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3391-166">See Also</span></span>  
 <span data-ttu-id="d3391-167">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d3391-167">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="d3391-168">[備份概觀 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d3391-168">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="d3391-169">[備份與還原：互通性與共存性 &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d3391-169">[Backup and Restore: Interoperability and Coexistence &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span></span>  
 <span data-ttu-id="d3391-170">[差異備份 &#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d3391-170">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="d3391-171">[檔案還原 &#40;簡單復原模式&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="d3391-171">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="d3391-172">[檔案還原 &#40;完整復原模式&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="d3391-172">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="d3391-173">[線上還原 &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d3391-173">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 [<span data-ttu-id="d3391-174">分次還原 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d3391-174">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
