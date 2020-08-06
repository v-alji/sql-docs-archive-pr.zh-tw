---
title: 線上還原 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- online restores [SQL Server]
- online restores [SQL Server], about online restores
ms.assetid: 7982a687-980a-4eb8-8e9f-6894148e7d8c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4db4d5b5ce08c50646857099d82964bb944bc8af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598483"
---
# <a name="online-restore-sql-server"></a><span data-ttu-id="adde7-102">線上還原 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="adde7-102">Online Restore (SQL Server)</span></span>
  <span data-ttu-id="adde7-103">只有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Edition 才支援線上還原。</span><span class="sxs-lookup"><span data-stu-id="adde7-103">Online restore is supported only on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise edition.</span></span> <span data-ttu-id="adde7-104">在此版本中，檔案、分頁或分次還原預設都是在線上進行。</span><span class="sxs-lookup"><span data-stu-id="adde7-104">In this edition, a file, page, or piecemeal restore is online by default.</span></span> <span data-ttu-id="adde7-105">本主題僅與包含多個檔案或檔案群組 (若是簡單復原模式，則只有唯讀檔案群組) 的資料庫有關。</span><span class="sxs-lookup"><span data-stu-id="adde7-105">This topic is relevant for databases that contain multiple files or filegroups (and, under the simple recovery model, only for read-only filegroups).</span></span>  
  
 <span data-ttu-id="adde7-106">在資料庫還在線上時還原資料，就稱之為 *「線上還原」* 。</span><span class="sxs-lookup"><span data-stu-id="adde7-106">Restoring data while the database is online is called an *online restore*.</span></span> <span data-ttu-id="adde7-107">即使有一或多個次要檔案群組離線，只要主要檔案群組還在線上，就將資料庫視為在線上。</span><span class="sxs-lookup"><span data-stu-id="adde7-107">A database is considered to be online whenever the primary filegroup is online, even if one or more of its secondary filegroups are offline.</span></span> <span data-ttu-id="adde7-108">當資料庫在線上時，您可以在任何復原模式下還原離線的檔案。</span><span class="sxs-lookup"><span data-stu-id="adde7-108">Under any recovery model, you can restore a file that is offline while the database is online.</span></span> <span data-ttu-id="adde7-109">當資料庫在線上時，您也可以在完整復原模式下還原頁面。</span><span class="sxs-lookup"><span data-stu-id="adde7-109">Under the full recovery model, you can also restore pages while the database is online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="adde7-110">線上還原會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise 版中自動發生，不需要任何使用者動作。</span><span class="sxs-lookup"><span data-stu-id="adde7-110">Online restore occurs automatically on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise and requires no user action.</span></span> <span data-ttu-id="adde7-111">如果您不想要使用線上還原，則可以先使資料庫離線，再啟動還原。</span><span class="sxs-lookup"><span data-stu-id="adde7-111">If you do not want to use online restore, you can take a database offline before you start a restore.</span></span> <span data-ttu-id="adde7-112">如需詳細資訊，請參閱本主題稍後的「 [使資料庫或檔案離線](#taking_db_or_file_offline)」。</span><span class="sxs-lookup"><span data-stu-id="adde7-112">For more information, see [Taking a Database or File Offline](#taking_db_or_file_offline), later in this topic.</span></span>  
  
 <span data-ttu-id="adde7-113">在線上檔案還原期間，任何即將還原的檔案及其檔案群組都會離線。</span><span class="sxs-lookup"><span data-stu-id="adde7-113">During an online file restore, any file being restored and its filegroup are offline.</span></span> <span data-ttu-id="adde7-114">當線上還原啟動時，如果這其中還有任何檔案在線上，第一個還原陳述式就會讓檔案的檔案群組離線。</span><span class="sxs-lookup"><span data-stu-id="adde7-114">If any of these files is online when an online restore starts, the first restore statement takes the filegroup of the file offline.</span></span> <span data-ttu-id="adde7-115">相反地，在線上分頁還原期間，只有頁面會離線。</span><span class="sxs-lookup"><span data-stu-id="adde7-115">In contrast, during an online page restore, only the page is offline.</span></span>  
  
 <span data-ttu-id="adde7-116">每個線上還原實例都包括下列基本步驟：</span><span class="sxs-lookup"><span data-stu-id="adde7-116">Every online restore scenario involves the following basic steps:</span></span>  
  
1.  <span data-ttu-id="adde7-117">還原資料。</span><span class="sxs-lookup"><span data-stu-id="adde7-117">Restore the data.</span></span>  
  
2.  <span data-ttu-id="adde7-118">針對最後一次記錄還原，使用 WITH RECOVERY 來還原記錄。</span><span class="sxs-lookup"><span data-stu-id="adde7-118">Restore the log by using WITH RECOVERY for the last log restore.</span></span> <span data-ttu-id="adde7-119">這會使還原的資料上線。</span><span class="sxs-lookup"><span data-stu-id="adde7-119">This brings the restored data online.</span></span>  
  
 <span data-ttu-id="adde7-120">有時候會因為回復所需的資料在啟動期間離線，而無法回復未認可的交易。</span><span class="sxs-lookup"><span data-stu-id="adde7-120">Occasionally, an uncommitted transaction cannot be rolled back because the data that is required by rollback is offline during startup.</span></span> <span data-ttu-id="adde7-121">在此情況下，將會延遲交易。</span><span class="sxs-lookup"><span data-stu-id="adde7-121">In this case, the transaction is deferred.</span></span> <span data-ttu-id="adde7-122">如需詳細資訊，請參閱 [延遲交易 &#40;SQL Server&#41;](deferred-transactions-sql-server.md)中無用的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="adde7-122">For more information, see [Deferred Transactions &#40;SQL Server&#41;](deferred-transactions-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="adde7-123">如果資料庫目前正在使用大量記錄復原模式，建議您先切換到完整復原模式，再啟動線上還原。</span><span class="sxs-lookup"><span data-stu-id="adde7-123">If the database is currently using the bulk-logged recovery model, we recommend that you switch to the full recovery model before you start an online restore.</span></span> <span data-ttu-id="adde7-124">如需詳細資訊，請參閱[檢視或變更資料庫的復原模式 &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="adde7-124">For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="adde7-125">如果備份是在附加至伺服器的多個裝置上進行，則在執行線上還原時，必須有相同數目的裝置可用。</span><span class="sxs-lookup"><span data-stu-id="adde7-125">If the backups were taken with multiple devices that were attached to the server, the same number of devices must be available during an online restore.</span></span>  
  
## <a name="log-backups-for-online-restore"></a><span data-ttu-id="adde7-126">線上還原的記錄備份</span><span class="sxs-lookup"><span data-stu-id="adde7-126">Log Backups for Online Restore</span></span>  
 <span data-ttu-id="adde7-127">在線上還原中，復原點就是還原的資料變成離線或最後一次設為唯讀的時間點。</span><span class="sxs-lookup"><span data-stu-id="adde7-127">In an online restore, the recovery point is the point when the data being restored was taken offline or made read-only for the last time.</span></span> <span data-ttu-id="adde7-128">能夠重建及包含此復原點的交易記錄備份，必須完整備妥。</span><span class="sxs-lookup"><span data-stu-id="adde7-128">The transaction log backups leading up to and including this recovery point must all be available.</span></span> <span data-ttu-id="adde7-129">一般而言，在該時間點後必須有記錄備份，才能涵蓋檔案的復原點。</span><span class="sxs-lookup"><span data-stu-id="adde7-129">Generally, a log backup is required after that point to cover the recovery point for the file.</span></span> <span data-ttu-id="adde7-130">唯一的例外就是從資料變成唯讀後建立的資料備份中，對唯讀資料所進行的線上還原。</span><span class="sxs-lookup"><span data-stu-id="adde7-130">The only exception is during an online restore of read-only data from a data backup that was taken after the data became read-only.</span></span> <span data-ttu-id="adde7-131">在這種情況下，您不需要有記錄備份。</span><span class="sxs-lookup"><span data-stu-id="adde7-131">In this case, you do not have to have a log backup.</span></span>  
  
 <span data-ttu-id="adde7-132">一般而言，即使在還原順序啟動之後，您還是可以在資料庫仍在線上時進行交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="adde7-132">Generally, you may take transaction log backups while the database is online, even after the start of the restore sequence.</span></span> <span data-ttu-id="adde7-133">最後記錄備份的時間點取決於要還原之檔案的屬性：</span><span class="sxs-lookup"><span data-stu-id="adde7-133">The timing of the last log backup depends on the properties of the file being restored:</span></span>  
  
-   <span data-ttu-id="adde7-134">對於線上唯讀檔案，您可以在第一個還原順序之前或當中進行復原所需的最後一次記錄備份。</span><span class="sxs-lookup"><span data-stu-id="adde7-134">For an online read-only file, you can take the last log backup that is required for recovery before or during the first restore sequence.</span></span> <span data-ttu-id="adde7-135">如果是在檔案群組成為唯讀之後進行資料或差異備份，唯讀檔案群組就可以不需要記錄備份。</span><span class="sxs-lookup"><span data-stu-id="adde7-135">A read-only filegroup may not require log backups if a data or differential backup was taken after the filegroup became read-only.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="adde7-136">上述資訊也同樣適用於每個離線檔案。</span><span class="sxs-lookup"><span data-stu-id="adde7-136">The preceding information also applies to every offline file.</span></span>  
  
-   <span data-ttu-id="adde7-137">比較特殊的情況是，在發出第一個還原陳述式時仍在線上，但之後因該還原陳述式而自動離線的讀取/寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="adde7-137">A special case exists for a read/write file that was online when the first restore statement was issued and that was then automatically taken offline by that restore statement.</span></span> <span data-ttu-id="adde7-138">在此情況下，您必須在第一個「還原順序」  (此順序中包含一或多個可還原、向前復原及復原資料的 RESTORE 陳述式) 期間進行記錄備份。</span><span class="sxs-lookup"><span data-stu-id="adde7-138">In this case, you must take a log backup during the first *restore sequence* (the sequence of one or more RESTORE statements that restore, roll forward, and recover data).</span></span> <span data-ttu-id="adde7-139">一般而言，必須在還原所有完整備份之後，而且在復原資料之前進行這個記錄備份。</span><span class="sxs-lookup"><span data-stu-id="adde7-139">Generally, this log backup must occur after you restore all the full backups and before you recover the data.</span></span> <span data-ttu-id="adde7-140">不過，如果特定的檔案群組有多個檔案備份，則記錄備份最晚的時間點是在檔案群組離線之後的時間。</span><span class="sxs-lookup"><span data-stu-id="adde7-140">However, if there are multiple file backups for a specific filegroup, the minimal point of log backup is the time after the filegroup is offline.</span></span> <span data-ttu-id="adde7-141">這個資料還原後的記錄備份會擷取檔案離線時的時間點。</span><span class="sxs-lookup"><span data-stu-id="adde7-141">This post-data-restore log backup captures the point at which the file was taken offline.</span></span> <span data-ttu-id="adde7-142">資料還原後的記錄備份是必要的，因為 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 無法使用線上記錄進行線上還原。</span><span class="sxs-lookup"><span data-stu-id="adde7-142">The post-data-restore log backup is necessary because the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] cannot use online log for an online restore.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="adde7-143">此外，您也可以在還原順序之前手動使檔案離線。</span><span class="sxs-lookup"><span data-stu-id="adde7-143">Alternatively, you can manually take the file offline before the restore sequence.</span></span> <span data-ttu-id="adde7-144">如需詳細資訊，請參閱本主題稍後的「使資料庫或檔案離線」。</span><span class="sxs-lookup"><span data-stu-id="adde7-144">For more information, see "Taking a Database or File Offline" later in this topic.</span></span>  
  
##  <a name="taking-a-database-or-file-offline"></a><a name="taking_db_or_file_offline"></a> <span data-ttu-id="adde7-145">使資料庫或檔案離線</span><span class="sxs-lookup"><span data-stu-id="adde7-145">Taking a Database or File Offline</span></span>  
 <span data-ttu-id="adde7-146">如果您不想要使用線上還原，則可以使用下列其中一個方法先讓資料庫離線，再來啟動還原順序：</span><span class="sxs-lookup"><span data-stu-id="adde7-146">If you do not want to use online restore, you can take the database offline before you start the restore sequence by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="adde7-147">在任何復原模式下，您可以使用下列 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) 陳述式，讓資料庫離線：</span><span class="sxs-lookup"><span data-stu-id="adde7-147">Under any recovery model, you can take the database offline by using the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement:</span></span>  
  
     <span data-ttu-id="adde7-148">ALTER DATABASE *database_name* SET OFFLINE</span><span class="sxs-lookup"><span data-stu-id="adde7-148">ALTER DATABASE *database_name* SET OFFLINE</span></span>  
  
-   <span data-ttu-id="adde7-149">或者，也可以在完整復原模式下強制檔案或分頁還原離線，方法是使用下列 [BACKUP LOG](/sql/t-sql/statements/backup-transact-sql) 陳述式，將資料庫置於正在還原狀態：</span><span class="sxs-lookup"><span data-stu-id="adde7-149">Alternatively, under the full recovery model, you can force a file or page restore to be offline, by using the following [BACKUP LOG](/sql/t-sql/statements/backup-transact-sql) statement put the database in to the restoring state:</span></span>  
  
     <span data-ttu-id="adde7-150">BACKUP LOG *database_name* WITH NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="adde7-150">BACKUP LOG *database_name* WITH NORECOVERY.</span></span>  
  
 <span data-ttu-id="adde7-151">只要資料庫仍然離線，所有的還原就都是離線還原。</span><span class="sxs-lookup"><span data-stu-id="adde7-151">As long as a database remains offline, all restores are offline restores.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="adde7-152">範例</span><span class="sxs-lookup"><span data-stu-id="adde7-152">Examples</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="adde7-153">線上還原順序的語法和離線還原順序的語法相同。</span><span class="sxs-lookup"><span data-stu-id="adde7-153">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
-   [<span data-ttu-id="adde7-154">範例：分次還原資料庫 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="adde7-154">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="adde7-155">範例：僅限於部分檔案群組的分次還原 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="adde7-155">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="adde7-156">範例：線上還原唯讀檔案 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="adde7-156">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="adde7-157">範例：分次還原資料庫 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="adde7-157">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="adde7-158">範例：僅限於部分檔案群組的分次還原 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="adde7-158">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="adde7-159">範例：線上還原讀取/寫入檔案 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="adde7-159">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="adde7-160">範例：線上還原唯讀檔案 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="adde7-160">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="adde7-161">相關工作</span><span class="sxs-lookup"><span data-stu-id="adde7-161">Related Tasks</span></span>  
  
-   [<span data-ttu-id="adde7-162">還原檔案和檔案群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="adde7-162">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="adde7-163">還原頁面 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="adde7-163">Restore Pages &#40;SQL Server&#41;</span></span>](restore-pages-sql-server.md)  
  
-   [<span data-ttu-id="adde7-164">管理 suspect_pages 資料表 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="adde7-164">Manage the suspect_pages Table &#40;SQL Server&#41;</span></span>](manage-the-suspect-pages-table-sql-server.md)  
  
-   [<span data-ttu-id="adde7-165">在不還原資料的情況下復原資料庫 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="adde7-165">Recover a Database Without Restoring Data &#40;Transact-SQL&#41;</span></span>](recover-a-database-without-restoring-data-transact-sql.md)  
  
-   [<span data-ttu-id="adde7-166">移除無用的檔案群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="adde7-166">Remove Defunct Filegroups &#40;SQL Server&#41;</span></span>](remove-defunct-filegroups-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="adde7-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adde7-167">See Also</span></span>  
 <span data-ttu-id="adde7-168">[檔案還原 &#40;完整復原模式&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="adde7-168">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="adde7-169">[檔案還原 &#40;簡單復原模式&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="adde7-169">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="adde7-170">[還原頁面 &#40;SQL Server&#41;](restore-pages-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="adde7-170">[Restore Pages &#40;SQL Server&#41;](restore-pages-sql-server.md) </span></span>  
 <span data-ttu-id="adde7-171">[分次還原 &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="adde7-171">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 [<span data-ttu-id="adde7-172">還原和復原概觀 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="adde7-172">Restore and Recovery Overview &#40;SQL Server&#41;</span></span>](restore-and-recovery-overview-sql-server.md)  
  
  
