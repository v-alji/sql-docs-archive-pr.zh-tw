---
title: 套用異動記錄備份 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring [SQL Server], log backups
- transaction log backups [SQL Server], applying backups
- online restores [SQL Server], log backups
- transaction log backups [SQL Server], quantity needed for restore sequence
- backups [SQL Server], log backups
ms.assetid: 9b12be51-5469-46f9-8e86-e938e10aa3a1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 54c91106f8ca6f15539b4103220860143882c3ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595143"
---
# <a name="apply-transaction-log-backups-sql-server"></a><span data-ttu-id="10fdc-102">套用異動記錄備份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="10fdc-102">Apply Transaction Log Backups (SQL Server)</span></span>
  <span data-ttu-id="10fdc-103">本主題僅與完整復原模式和大量記錄復原模式有關。</span><span class="sxs-lookup"><span data-stu-id="10fdc-103">The topic is relevant only for the full recovery model or bulk-logged recovery model.</span></span>  
  
 <span data-ttu-id="10fdc-104">此主題描述如何在還原 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的過程中套用交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="10fdc-104">This topic describes applying transaction log backups as part of restoring a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="10fdc-105">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="10fdc-105">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="10fdc-106">還原交易記錄備份的需求</span><span class="sxs-lookup"><span data-stu-id="10fdc-106">Requirements for Restoring Transaction Log Backups</span></span>](#Requirements)  
  
-   [<span data-ttu-id="10fdc-107">復原與交易記錄</span><span class="sxs-lookup"><span data-stu-id="10fdc-107">Recovery and Transaction Logs</span></span>](#RecoveryAndTlogs)  
  
-   [<span data-ttu-id="10fdc-108">使用記錄備份還原到失敗點</span><span class="sxs-lookup"><span data-stu-id="10fdc-108">Using Log Backups to Restore to the Point of Failure</span></span>](#PITrestore)  
  
-   [<span data-ttu-id="10fdc-109">相關工作</span><span class="sxs-lookup"><span data-stu-id="10fdc-109">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="requirements-for-restoring-transaction-log-backups"></a><a name="Requirements"></a><span data-ttu-id="10fdc-110">還原交易記錄備份的需求</span><span class="sxs-lookup"><span data-stu-id="10fdc-110">Requirements for Restoring Transaction Log Backups</span></span>  
 <span data-ttu-id="10fdc-111">若要套用交易記錄備份，必須符合下列需求：</span><span class="sxs-lookup"><span data-stu-id="10fdc-111">To apply a transaction log backup, the following requirements must be met:</span></span>  
  
-   <span data-ttu-id="10fdc-112">**有足夠的記錄備份供還原順序使用：** 您必須備份了足夠的記錄，才能完成還原順序。</span><span class="sxs-lookup"><span data-stu-id="10fdc-112">**Enough Log Backups for a Restore Sequence :** You must have enough log records backed up to complete a restore sequence.</span></span> <span data-ttu-id="10fdc-113">您必須先備妥必要的記錄備份，包括所需的 [結尾記錄備份](tail-log-backups-sql-server.md) ，才開始還原順序。</span><span class="sxs-lookup"><span data-stu-id="10fdc-113">The necessary log backups, including the [tail-log backup](tail-log-backups-sql-server.md) where required, must be available before the start of the restore sequence.</span></span>  
  
-   <span data-ttu-id="10fdc-114">**正確的還原順序：** 首先必須還原最新的完整資料庫備份或差異資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="10fdc-114">**Correct restore order:**  The immediately previous full database backup or differential database backup must be restored first.</span></span> <span data-ttu-id="10fdc-115">接著，必須依時間先後順序，還原在該完整或差異資料庫備份之後建立的所有交易記錄。</span><span class="sxs-lookup"><span data-stu-id="10fdc-115">Then, all transaction logs that are created after that full or differential database backup must be restored in chronological order.</span></span> <span data-ttu-id="10fdc-116">如果這個記錄鏈結中的某個交易記錄備份遺失或損毀，您只能還原該遺漏的交易記錄之前的交易記錄。</span><span class="sxs-lookup"><span data-stu-id="10fdc-116">If a transaction log backup in this log chain is lost or damaged, you can restore only transaction logs before the missing transaction log.</span></span>  
  
-   <span data-ttu-id="10fdc-117">**資料庫尚未復原：** 直到套用了最後一個交易記錄之後，才能復原資料庫。</span><span class="sxs-lookup"><span data-stu-id="10fdc-117">**Database not yet recovered:**  The database cannot be recovered until after the final transaction log has been applied.</span></span> <span data-ttu-id="10fdc-118">如果您只還原了其中一個中繼交易記錄備份 (尚未到達記錄鏈結的尾端) 之後便復原資料庫，則您無法還原該時間點之後的資料庫，除非您以完整資料庫備份開始重新啟動整個還原順序。</span><span class="sxs-lookup"><span data-stu-id="10fdc-118">If you recover the database after restoring one of the intermediate transaction log backups, that before the end of the log chain, you cannot restore the database past that point without restarting the complete restore sequence, starting with the full database backup.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="10fdc-119">最佳做法就是還原所有的記錄備份 (RESTORE LOG *資料庫名稱* WITH NORECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="10fdc-119">A best practice is to restore all the log backups (RESTORE LOG *database_name* WITH NORECOVERY).</span></span> <span data-ttu-id="10fdc-120">然後，在還原最後一個記錄備份之後，以個別的作業來復原資料庫 (RESTORE DATABASE *資料庫名稱* WITH RECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="10fdc-120">Then, after restoring the last log backup, recover the database in a separate operation (RESTORE DATABASE *database_name* WITH RECOVERY).</span></span>  
  
##  <a name="recovery-and-transaction-logs"></a><a name="RecoveryAndTlogs"></a><span data-ttu-id="10fdc-121">復原與交易記錄</span><span class="sxs-lookup"><span data-stu-id="10fdc-121">Recovery and Transaction Logs</span></span>  
 <span data-ttu-id="10fdc-122">當您完成還原作業並復原資料庫時，復原作業會回復所有未完成的交易。</span><span class="sxs-lookup"><span data-stu-id="10fdc-122">When you finish the restore operation and recover the database, recovery rolls back all incomplete transactions.</span></span> <span data-ttu-id="10fdc-123">此即稱為 *「恢復階段」*。</span><span class="sxs-lookup"><span data-stu-id="10fdc-123">This is known as the *undo phase*.</span></span> <span data-ttu-id="10fdc-124">需要進行回復，才能還原資料庫的完整性。</span><span class="sxs-lookup"><span data-stu-id="10fdc-124">Rolling back is required to restore the integrity of the database.</span></span> <span data-ttu-id="10fdc-125">回復之後，資料庫會上線，而且不再有交易記錄備份可以套用到資料庫。</span><span class="sxs-lookup"><span data-stu-id="10fdc-125">After rollback, the database goes online, and no more transaction log backups can be applied to the database.</span></span>  
  
 <span data-ttu-id="10fdc-126">例如，一系列交易記錄備份中包含長時間執行的交易。</span><span class="sxs-lookup"><span data-stu-id="10fdc-126">For example, a series of transaction log backups contain a long-running transaction.</span></span> <span data-ttu-id="10fdc-127">該交易的開頭記錄在第一個交易記錄備份，但是交易的結尾記錄在第二個交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="10fdc-127">The start of the transaction is recorded in the first transaction log backup, but the end of the transaction is recorded in the second transaction log backup.</span></span> <span data-ttu-id="10fdc-128">那麼一個交易記錄備份中將沒有認可或回復作業的記錄。</span><span class="sxs-lookup"><span data-stu-id="10fdc-128">There is no record of a commit or rollback operation in the first transaction log backup.</span></span> <span data-ttu-id="10fdc-129">如果在套用第一個交易記錄備份時執行復原作業，則會將長時間執行的交易視為未完成，並且回復在交易的第一個交易記錄備份中記錄的資料修改。</span><span class="sxs-lookup"><span data-stu-id="10fdc-129">If a recovery operation runs when the first transaction log backup is applied, the long-running transaction is treated as incomplete, and data modifications recorded in the first transaction log backup for the transaction are rolled back.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="10fdc-130">不允許在此時間點之後套用第二個交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="10fdc-130">does not allow for the second transaction log backup to be applied after this point.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="10fdc-131">在某些狀況下，您可以在記錄還原期間明確加入檔案。</span><span class="sxs-lookup"><span data-stu-id="10fdc-131">In some circumstances, you can explicitly add a file during log restore.</span></span>  
  
##  <a name="using-log-backups-to-restore-to-the-point-of-failure"></a><a name="PITrestore"></a><span data-ttu-id="10fdc-132">使用記錄備份來還原到失敗點</span><span class="sxs-lookup"><span data-stu-id="10fdc-132">Using Log Backups to Restore to the Point of Failure</span></span>  
 <span data-ttu-id="10fdc-133">假設發生下列事件順序。</span><span class="sxs-lookup"><span data-stu-id="10fdc-133">Assume the following sequence of events.</span></span>  
  
|<span data-ttu-id="10fdc-134">Time</span><span class="sxs-lookup"><span data-stu-id="10fdc-134">Time</span></span>|<span data-ttu-id="10fdc-135">事件</span><span class="sxs-lookup"><span data-stu-id="10fdc-135">Event</span></span>|  
|----------|-----------|  
|<span data-ttu-id="10fdc-136">上午 8:00</span><span class="sxs-lookup"><span data-stu-id="10fdc-136">8:00 A.M.</span></span>|<span data-ttu-id="10fdc-137">備份資料庫以建立完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="10fdc-137">Back up database to create a full database backup.</span></span>|  
|<span data-ttu-id="10fdc-138">中午</span><span class="sxs-lookup"><span data-stu-id="10fdc-138">Noon</span></span>|<span data-ttu-id="10fdc-139">備份交易記錄。</span><span class="sxs-lookup"><span data-stu-id="10fdc-139">Back up transaction log.</span></span>|  
|<span data-ttu-id="10fdc-140">下午 4:00</span><span class="sxs-lookup"><span data-stu-id="10fdc-140">4:00 P.M.</span></span>|<span data-ttu-id="10fdc-141">備份交易記錄。</span><span class="sxs-lookup"><span data-stu-id="10fdc-141">Back up transaction log.</span></span>|  
|<span data-ttu-id="10fdc-142">下午 6:00</span><span class="sxs-lookup"><span data-stu-id="10fdc-142">6:00 P.M.</span></span>|<span data-ttu-id="10fdc-143">備份資料庫以建立完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="10fdc-143">Back up database to create a full database backup.</span></span>|  
|<span data-ttu-id="10fdc-144">下午 8:00</span><span class="sxs-lookup"><span data-stu-id="10fdc-144">8:00 P.M.</span></span>|<span data-ttu-id="10fdc-145">備份交易記錄。</span><span class="sxs-lookup"><span data-stu-id="10fdc-145">Back up transaction log.</span></span>|  
|<span data-ttu-id="10fdc-146">下午 9:45</span><span class="sxs-lookup"><span data-stu-id="10fdc-146">9:45 P.M.</span></span>|<span data-ttu-id="10fdc-147">發生故障。</span><span class="sxs-lookup"><span data-stu-id="10fdc-147">Failure occurs.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="10fdc-148">如需這個備份順序範例的說明，請參閱[交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="10fdc-148">For an explanation of this example sequence of backups, see [Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="10fdc-149">若要將資料庫還原至下午 9:45 的狀態</span><span class="sxs-lookup"><span data-stu-id="10fdc-149">To restore the database to its state at 9:45 P.M.</span></span> <span data-ttu-id="10fdc-150">(失敗點)，您可以使用下列任何一個替代程序：</span><span class="sxs-lookup"><span data-stu-id="10fdc-150">(the point of failure), either of the following alternative procedures can be used:</span></span>  
  
 <span data-ttu-id="10fdc-151">**替代程序 1：使用最新的完整資料庫備份來還原資料庫**</span><span class="sxs-lookup"><span data-stu-id="10fdc-151">**Alternative 1: Restore the database by using the most recent full database backup**</span></span>  
  
1.  <span data-ttu-id="10fdc-152">將目前使用者中交易記錄的結尾記錄備份建立為失敗點。</span><span class="sxs-lookup"><span data-stu-id="10fdc-152">Create a tail-log backup of the currently active transaction log as of the point of failure.</span></span>  
  
2.  <span data-ttu-id="10fdc-153">不要還原上午 8:00 的</span><span class="sxs-lookup"><span data-stu-id="10fdc-153">Do not restore the 8:00 A.M.</span></span> <span data-ttu-id="10fdc-154">完整資料庫備份進行還原，這個程序需要更多的時間。</span><span class="sxs-lookup"><span data-stu-id="10fdc-154">full database backup.</span></span> <span data-ttu-id="10fdc-155">而是還原下午 6:00 的最新</span><span class="sxs-lookup"><span data-stu-id="10fdc-155">Instead, restore the more recent 6:00 P.M.</span></span> <span data-ttu-id="10fdc-156">完整資料庫備份，然後套用下午 8:00 的</span><span class="sxs-lookup"><span data-stu-id="10fdc-156">full database backup, and then apply the 8:00 P.M.</span></span> <span data-ttu-id="10fdc-157">記錄備份及結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="10fdc-157">log backup and the tail-log backup.</span></span>  
  
 <span data-ttu-id="10fdc-158">**替代程序 2：使用較早的完整資料庫備份來還原資料庫**</span><span class="sxs-lookup"><span data-stu-id="10fdc-158">**Alternative 2: Restore the database by using an earlier full database backup**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="10fdc-159">如果發生問題，讓您無法使用下午 6:00 的</span><span class="sxs-lookup"><span data-stu-id="10fdc-159">This alternative process is useful if a problem prevents you from using the 6:00 P.M.</span></span> <span data-ttu-id="10fdc-160">完整資料庫備份進行還原，這個程序需要更多的時間。</span><span class="sxs-lookup"><span data-stu-id="10fdc-160">full database backup.</span></span> <span data-ttu-id="10fdc-161">比起從下午 6:00 的</span><span class="sxs-lookup"><span data-stu-id="10fdc-161">This process takes longer than restoring from the 6:00 P.M.</span></span> <span data-ttu-id="10fdc-162">完整資料庫備份進行還原，這個程序需要更多的時間。</span><span class="sxs-lookup"><span data-stu-id="10fdc-162">full database backup.</span></span>  
  
1.  <span data-ttu-id="10fdc-163">將目前使用者中交易記錄的結尾記錄備份建立為失敗點。</span><span class="sxs-lookup"><span data-stu-id="10fdc-163">Create a tail-log backup of the currently active transaction log as of the point of failure.</span></span>  
  
2.  <span data-ttu-id="10fdc-164">還原上午 8:00 的</span><span class="sxs-lookup"><span data-stu-id="10fdc-164">Restore the 8:00 A.M.</span></span> <span data-ttu-id="10fdc-165">完整資料庫備份，然後依序還原全部四個交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="10fdc-165">full database backup, and then restore all four transaction log backups in sequence.</span></span> <span data-ttu-id="10fdc-166">如此即可將下午 9:45 前完成的所有交易都向前復原。</span><span class="sxs-lookup"><span data-stu-id="10fdc-166">This rolls forward all completed transactions up to 9:45 P.M.</span></span>  
  
     <span data-ttu-id="10fdc-167">這個替代程序指出維護一系列完整資料庫備份的交易記錄備份鏈結可以提供的額外安全性。</span><span class="sxs-lookup"><span data-stu-id="10fdc-167">This alternative points out the redundant security offered by maintaining a chain of transaction log backups across a series of full database backups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="10fdc-168">在某些情況下，您也可以使用交易記錄，將資料庫還原到特定時間點。</span><span class="sxs-lookup"><span data-stu-id="10fdc-168">In some cases, you can also use transaction logs to restore a database to a specific point in time.</span></span> <span data-ttu-id="10fdc-169">如需詳細資訊，請參閱 [將 SQL Server 資料庫還原至某個時間點 &#40;完整復原模式&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)。</span><span class="sxs-lookup"><span data-stu-id="10fdc-169">For more information, [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="10fdc-170">相關工作</span><span class="sxs-lookup"><span data-stu-id="10fdc-170">Related Tasks</span></span>  
 <span data-ttu-id="10fdc-171">**套用交易記錄備份**</span><span class="sxs-lookup"><span data-stu-id="10fdc-171">**To apply a transaction log backup**</span></span>  
  
-   [<span data-ttu-id="10fdc-172">還原交易記錄備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="10fdc-172">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
 <span data-ttu-id="10fdc-173">**還原到您的復原點**</span><span class="sxs-lookup"><span data-stu-id="10fdc-173">**To restore to your recovery point**</span></span>  
  
-   [<span data-ttu-id="10fdc-174">在完整復原模式下將資料庫還原至失敗點 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="10fdc-174">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="10fdc-175">將 SQL Server 資料庫還原至某個時間點 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="10fdc-175">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   <span data-ttu-id="10fdc-176"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="10fdc-176"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span></span>  
  
-   [<span data-ttu-id="10fdc-177">復原包含標示之交易的相關資料庫</span><span class="sxs-lookup"><span data-stu-id="10fdc-177">Recovery of Related  Databases That Contain Marked Transaction</span></span>](recovery-of-related-databases-that-contain-marked-transaction.md)  
  
-   [<span data-ttu-id="10fdc-178">復原到記錄序號 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="10fdc-178">Recover to a Log Sequence Number &#40;SQL Server&#41;</span></span>](recover-to-a-log-sequence-number-sql-server.md)  
  
 <span data-ttu-id="10fdc-179">**若要使用 WITH NORECOVERY，在還原備份之後復原資料庫**</span><span class="sxs-lookup"><span data-stu-id="10fdc-179">**To recover a database after restoring backups using WITH NORECOVERY**</span></span>  
  
-   [<span data-ttu-id="10fdc-180">在不還原資料的情況下復原資料庫 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="10fdc-180">Recover a Database Without Restoring Data &#40;Transact-SQL&#41;</span></span>](recover-a-database-without-restoring-data-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="10fdc-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10fdc-181">See Also</span></span>  
 [<span data-ttu-id="10fdc-182">交易記錄 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="10fdc-182">The Transaction Log &#40;SQL Server&#41;</span></span>](../logs/the-transaction-log-sql-server.md)  
  
  
