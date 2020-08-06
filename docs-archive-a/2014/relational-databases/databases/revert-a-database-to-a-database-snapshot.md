---
title: 將資料庫還原成資料庫快照集 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], reverting to
- reverting databases
ms.assetid: 8f74dd31-c9ca-4537-8760-0c7648f0787d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1c78da3d7c559309c0563760e7062f01cf784648
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595094"
---
# <a name="revert-a-database-to-a-database-snapshot"></a><span data-ttu-id="8f140-102">將資料庫還原成資料庫快照集</span><span class="sxs-lookup"><span data-stu-id="8f140-102">Revert a Database to a Database Snapshot</span></span>
  <span data-ttu-id="8f140-103">如果線上資料庫中的資料已經損毀，在某些情況下，將資料庫還原成發生損毀之前的資料庫快照集可能是從備份還原資料庫的正確替代方式。</span><span class="sxs-lookup"><span data-stu-id="8f140-103">If data in an online database becomes damaged, in some cases, reverting the database to a database snapshot that predates the damage might be an appropriate alternative to restoring the database from a backup.</span></span> <span data-ttu-id="8f140-104">例如，還原資料庫可用於反轉最近發生的嚴重使用者錯誤，例如誤將資料表卸除。</span><span class="sxs-lookup"><span data-stu-id="8f140-104">For example, reverting a database might be useful for reverse a recent serious user error, such as a dropped table.</span></span> <span data-ttu-id="8f140-105">不過，在快照集之後進行的所有變更都將遺失。</span><span class="sxs-lookup"><span data-stu-id="8f140-105">However, all changes made after the snapshot was created are lost.</span></span>  
  
-   <span data-ttu-id="8f140-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="8f140-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8f140-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="8f140-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="8f140-108">先決條件</span><span class="sxs-lookup"><span data-stu-id="8f140-108">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="8f140-109">安全性</span><span class="sxs-lookup"><span data-stu-id="8f140-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8f140-110">**若要將資料庫還原成資料庫快照集，請使用下列方式：** [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="8f140-110">**To Revert a Database to a Database Snapshot, using:**  [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8f140-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="8f140-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8f140-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="8f140-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="8f140-113">在下列狀況下，不支援還原：</span><span class="sxs-lookup"><span data-stu-id="8f140-113">Reverting is unsupported under the following conditions:</span></span>  
  
-   <span data-ttu-id="8f140-114">資料庫目前只能有一個資料庫快照集，就是您打算要還原的目標快照集。</span><span class="sxs-lookup"><span data-stu-id="8f140-114">The database must currently have only one database snapshot, to which you plan to revert.</span></span>  
  
-   <span data-ttu-id="8f140-115">任何唯讀或壓縮的檔案群組存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="8f140-115">Any read-only or compressed filegroups exist in the database.</span></span>  
  
-   <span data-ttu-id="8f140-116">建立快照集時原本處於線上狀態的所有檔案，現在都變成離線狀態。</span><span class="sxs-lookup"><span data-stu-id="8f140-116">Any files are now offline but were online when the snapshot was created.</span></span>  
  
 <span data-ttu-id="8f140-117">在還原資料庫之前，請仔細考慮以下限制：</span><span class="sxs-lookup"><span data-stu-id="8f140-117">Before reverting a database, consider the following limitations:</span></span>  
  
-   <span data-ttu-id="8f140-118">還原不適用於媒體復原。</span><span class="sxs-lookup"><span data-stu-id="8f140-118">Reverting is not intended for media recovery.</span></span> <span data-ttu-id="8f140-119">.</span><span class="sxs-lookup"><span data-stu-id="8f140-119">.</span></span> <span data-ttu-id="8f140-120">資料庫快照集是不完整的資料庫檔案複本，因此如果資料庫或資料庫快照集已損毀，很可能無法從快照集還原。</span><span class="sxs-lookup"><span data-stu-id="8f140-120">A database snapshot is an incomplete copy of the database files, so if either the database or the database snapshot is corrupted, reverting from a snapshot is likely to be impossible.</span></span> <span data-ttu-id="8f140-121">此外，即使可以還原，但是在損毀的情況下還原也不太可能會更正問題。</span><span class="sxs-lookup"><span data-stu-id="8f140-121">Furthermore, even when it is possible, reverting in the event of corruption is unlikely to correct the problem.</span></span> <span data-ttu-id="8f140-122">因此，建立定期備份和測試還原計畫是保護資料庫的基本措施。</span><span class="sxs-lookup"><span data-stu-id="8f140-122">Therefore, taking regular backups and testing your restore plan are essential to protect a database.</span></span> <span data-ttu-id="8f140-123">如需詳細資訊，請參閱 [SQL Server 資料庫的備份與還原](../backup-restore/back-up-and-restore-of-sql-server-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="8f140-123">For more information, see [Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8f140-124">如果您必須能夠將來源資料庫還原到您建立資料庫快照集當時的時間點，請使用完整復原模式並實作可讓您執行此作業的備份原則。</span><span class="sxs-lookup"><span data-stu-id="8f140-124">If you need to be able to restore the source database to the point in time at which you created a database snapshot, use the full recovery model and implement a backup policy that enables you to do that.</span></span>  
  
-   <span data-ttu-id="8f140-125">還原的資料庫會覆寫原始的來源資料庫，因此自從建立快照集以來對資料庫進行的任何更新都將遺失。</span><span class="sxs-lookup"><span data-stu-id="8f140-125">The original source database is overwritten by the reverted database, so any updates to the database since the snapshot's creation are lost.</span></span>  
  
-   <span data-ttu-id="8f140-126">還原作業也會覆寫舊的記錄檔並重建記錄檔。</span><span class="sxs-lookup"><span data-stu-id="8f140-126">The revert operation also overwrites the old log file and rebuilds the log.</span></span> <span data-ttu-id="8f140-127">所以，您無法將還原的資料庫向前復原至發生使用者錯誤的時間點。</span><span class="sxs-lookup"><span data-stu-id="8f140-127">Consequently, you cannot roll the reverted database forward to the point of user error.</span></span> <span data-ttu-id="8f140-128">因此，我們建議您先備份記錄檔，然後再還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="8f140-128">Therefore, we recommend that you back up the log before reverting a database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8f140-129">雖然您不能藉由還原原始記錄檔來向前復原資料庫，但原始記錄檔中的資訊對於重建失去的資料還是非常有用。</span><span class="sxs-lookup"><span data-stu-id="8f140-129">Although you cannot restore the original log to roll forward the database, the information in the original log file can be useful for reconstructing lost data.</span></span>  
  
-   <span data-ttu-id="8f140-130">還原會中斷記錄備份鏈結。</span><span class="sxs-lookup"><span data-stu-id="8f140-130">Reverting breaks the log backup chain.</span></span> <span data-ttu-id="8f140-131">因此，您必須先進行完整資料庫備份或檔案備份，然後才能進行已還原資料庫的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="8f140-131">Therefore, before you can take log backups of the reverted database, you must first take a full database backup or file backup.</span></span> <span data-ttu-id="8f140-132">我們建議您進行完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="8f140-132">We recommend a full database backup.</span></span>  
  
-   <span data-ttu-id="8f140-133">在還原作業期間，將無法使用快照集和來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="8f140-133">During a revert operation, both the snapshot and the source database are unavailable.</span></span> <span data-ttu-id="8f140-134">來源資料庫和快照都會標示為「還原中」。</span><span class="sxs-lookup"><span data-stu-id="8f140-134">The source database and snapshot are both marked "In restore."</span></span> <span data-ttu-id="8f140-135">如果還原作業期間發生錯誤，當資料庫重新啟動時，還原作業會嘗試完成還原。</span><span class="sxs-lookup"><span data-stu-id="8f140-135">If an error occurs during the revert operation, when the database starts up again, the revert operation will try to finish reverting.</span></span>  
  
-   <span data-ttu-id="8f140-136">已還原之資料庫的中繼資料，將與建立快照時的中繼資料相同。</span><span class="sxs-lookup"><span data-stu-id="8f140-136">The metadata of a reverted database is the same as the metadata at the time of the snapshot.</span></span>  
  
-   <span data-ttu-id="8f140-137">還原會卸除所有全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="8f140-137">Reverting drops all the full-text catalogs.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="8f140-138">必要條件</span><span class="sxs-lookup"><span data-stu-id="8f140-138">Prerequisites</span></span>  
 <span data-ttu-id="8f140-139">請確定來源資料庫和資料庫快照集符合下列必要條件：</span><span class="sxs-lookup"><span data-stu-id="8f140-139">Ensure that the source database and database snapshot meet the following prerequisites:</span></span>  
  
-   <span data-ttu-id="8f140-140">確認資料庫尚未損毀。</span><span class="sxs-lookup"><span data-stu-id="8f140-140">Verify that the database has not become corrupted.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8f140-141">如果資料庫已損毀，您就必須從備份還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="8f140-141">If the database has been corrupted, you will need to restore it from backups.</span></span> <span data-ttu-id="8f140-142">如需詳細資訊，請參閱[完整資料庫還原 &#40;簡單復原模式&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) 或[完整資料庫還原 &#40;完整復原模式&#41;](../backup-restore/complete-database-restores-full-recovery-model.md)。</span><span class="sxs-lookup"><span data-stu-id="8f140-142">For more information, see [Complete Database Restores &#40;Simple Recovery Model&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) or [Complete Database Restores &#40;Full Recovery Model&#41;](../backup-restore/complete-database-restores-full-recovery-model.md).</span></span>  
  
-   <span data-ttu-id="8f140-143">識別在發生錯誤之前建立的最近快照集。</span><span class="sxs-lookup"><span data-stu-id="8f140-143">Identify a recent snapshot that was created before the error.</span></span> <span data-ttu-id="8f140-144">如需詳細資訊，請參閱 [檢視資料庫快照集 &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md)中之資料庫的快照集。</span><span class="sxs-lookup"><span data-stu-id="8f140-144">For more information, see [View a Database Snapshot &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md).</span></span>  
  
-   <span data-ttu-id="8f140-145">卸除目前存在資料庫上的任何其他快照集。</span><span class="sxs-lookup"><span data-stu-id="8f140-145">Drop any other snapshots that currently exist on the database.</span></span> <span data-ttu-id="8f140-146">如需詳細資訊，請參閱 [卸除資料庫快照集 &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="8f140-146">For more information, see [Drop a Database Snapshot &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8f140-147">Security</span><span class="sxs-lookup"><span data-stu-id="8f140-147">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8f140-148">權限</span><span class="sxs-lookup"><span data-stu-id="8f140-148">Permissions</span></span>  
 <span data-ttu-id="8f140-149">任何擁有來源資料庫之 RESTORE DATABASE 權限的使用者都可以將它還原成建立資料庫快照集時的狀態。</span><span class="sxs-lookup"><span data-stu-id="8f140-149">Any user who has RESTORE DATABASE permissions on the source database can revert it to its state when a database snapshot was created.</span></span>  
  
##  <a name="how-to-revert-a-database-to-a-database-snapshot-using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8f140-150">如何將資料庫還原成資料庫快照集 (使用 Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="8f140-150">How to Revert a Database to a Database Snapshot (Using Transact-SQL)</span></span>  
 <span data-ttu-id="8f140-151">**若要將資料庫還原成資料庫快照集**</span><span class="sxs-lookup"><span data-stu-id="8f140-151">**To revert a database to a database snapshot**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8f140-152">如需此程序的範例，請參閱本節稍後的 [範例 (Transact-SQL)](#TsqlExample)。</span><span class="sxs-lookup"><span data-stu-id="8f140-152">For an example of this procedure, see [Examples (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="8f140-153">識別您要將資料庫還原成哪一個資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="8f140-153">Identify the database snapshot to which you want to revert the database.</span></span> <span data-ttu-id="8f140-154">您可以檢視 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中之資料庫的快照集 (請參閱 [檢視資料庫快照集 &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md))。</span><span class="sxs-lookup"><span data-stu-id="8f140-154">You can view the snapshots on a database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (see [View a Database Snapshot &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md)).</span></span> <span data-ttu-id="8f140-155">此外，您可以從 **sys.databases &amp;#40;Transact-SQL&amp;#41;** 目錄檢視的 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 資料行中，識別某個檢視的來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="8f140-155">Also, you can identify the source database of a view from the **source_database_id** column of the [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view.</span></span>  
  
2.  <span data-ttu-id="8f140-156">卸除任何其他資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="8f140-156">Drop any other database snapshots.</span></span>  
  
     <span data-ttu-id="8f140-157">如需卸除快照集的相關資訊，請參閱 [卸除資料庫快照集 &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="8f140-157">For information on dropping snapshots, see [Drop a Database Snapshot &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span></span> <span data-ttu-id="8f140-158">如果資料庫使用完整復原模式，您應該在還原之前備份記錄。</span><span class="sxs-lookup"><span data-stu-id="8f140-158">If the database uses the full recovery model, before reverting, you should back up the log.</span></span> <span data-ttu-id="8f140-159">如需詳細資訊，請參閱[備份交易記錄 &#40;SQL Server&#41;](../backup-restore/back-up-a-transaction-log-sql-server.md) 或[資料庫損毀時備份交易記錄 &#40;SQL Server&#41;](../backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="8f140-159">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](../backup-restore/back-up-a-transaction-log-sql-server.md) or [Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;](../backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="8f140-160">執行還原作業。</span><span class="sxs-lookup"><span data-stu-id="8f140-160">Perform the revert operation.</span></span>  
  
     <span data-ttu-id="8f140-161">還原作業需要來源資料庫上的 RESTORE DATABASE 權限。</span><span class="sxs-lookup"><span data-stu-id="8f140-161">A revert operation requires RESTORE DATABASE permissions on the source database.</span></span> <span data-ttu-id="8f140-162">若要還原資料庫，請使用下列 Transact-SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="8f140-162">To revert the database, use the following Transact-SQL statement:</span></span>  
  
     <span data-ttu-id="8f140-163">RESTORE DATABASE *資database_name* FROM DATABASE_SNAPSHOT **=** _database_snapshot_name_</span><span class="sxs-lookup"><span data-stu-id="8f140-163">RESTORE DATABASE *database_name* FROM DATABASE_SNAPSHOT **=**_database_snapshot_name_</span></span>  
  
     <span data-ttu-id="8f140-164">其中 *database_name* 是來源資料庫，而 *database_snapshot_name* 是要用來還原資料庫的快照集名稱。</span><span class="sxs-lookup"><span data-stu-id="8f140-164">Where *database_name* is the source database and *database_snapshot_name* is the name of the snapshot to which you want to revert the database.</span></span> <span data-ttu-id="8f140-165">請注意，在此陳述式中，您必須指定快照名稱，而非備份裝置。</span><span class="sxs-lookup"><span data-stu-id="8f140-165">Notice that in this statement, you must specify a snapshot name rather than a backup device.</span></span>  
  
     <span data-ttu-id="8f140-166">如需詳細資訊，請參閱 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)備份。</span><span class="sxs-lookup"><span data-stu-id="8f140-166">For more information, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8f140-167">在還原作業期間，將無法使用快照和來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="8f140-167">During the revert operation, both the snapshot and the source database are unavailable.</span></span> <span data-ttu-id="8f140-168">來源資料庫和快照集都會標示為「還原中」。</span><span class="sxs-lookup"><span data-stu-id="8f140-168">The source database and snapshot are both marked as "In restore."</span></span> <span data-ttu-id="8f140-169">如果還原作業期間發生錯誤，它會在資料庫重新啟動時嘗試完成還原。</span><span class="sxs-lookup"><span data-stu-id="8f140-169">If an error occurs during the revert operation, it will try to finish reverting when the database starts up again.</span></span>  
  
4.  <span data-ttu-id="8f140-170">如果建立資料庫快照集之後，資料庫擁有者有變更過，您可以更新所還原資料庫的資料庫擁有者。</span><span class="sxs-lookup"><span data-stu-id="8f140-170">If the database owner changed since creation of the database snapshot, you may want to update the database owner of the reverted database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8f140-171">還原的資料庫會保留資料庫快照集的權限和組態 (例如，資料庫擁有者和復原模式)。</span><span class="sxs-lookup"><span data-stu-id="8f140-171">The reverted database retains the permissions and configuration (such as database owner and recovery model) of the database snapshot.</span></span>  
  
5.  <span data-ttu-id="8f140-172">啟動資料庫。</span><span class="sxs-lookup"><span data-stu-id="8f140-172">Start the database.</span></span>  
  
6.  <span data-ttu-id="8f140-173">您可以選擇性地備份還原的資料庫，特別是當它使用完整 (或大量記錄) 復原模式時。</span><span class="sxs-lookup"><span data-stu-id="8f140-173">Optionally, back up the reverted database, especially if it uses the full (or bulk-logged) recovery model.</span></span> <span data-ttu-id="8f140-174">若要備份資料庫，請參閱[建立完整資料庫備份 &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="8f140-174">To back up a database, see [Create a Full Database Backup &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="8f140-175">範例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="8f140-175">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="8f140-176">本節包含將資料庫還原成資料庫快照集的下列範例：</span><span class="sxs-lookup"><span data-stu-id="8f140-176">This section contains the following examples of reverting a database to a database snapshot:</span></span>  
  
-   <span data-ttu-id="8f140-177">A.</span><span class="sxs-lookup"><span data-stu-id="8f140-177">A.</span></span> [<span data-ttu-id="8f140-178">還原 AdventureWorks 資料庫上的快照集</span><span class="sxs-lookup"><span data-stu-id="8f140-178">Reverting a snapshot on the AdventureWorks database</span></span>](#Reverting_AW)  
  
-   <span data-ttu-id="8f140-179">B.</span><span class="sxs-lookup"><span data-stu-id="8f140-179">B.</span></span> [<span data-ttu-id="8f140-180">還原 Sales 資料庫上的快照集</span><span class="sxs-lookup"><span data-stu-id="8f140-180">Reverting a snapshot on the Sales database</span></span>](#Reverting_Sales)  
  
####  <a name="a-reverting-a-snapshot-on-the-adventureworks-database"></a><a name="Reverting_AW"></a> <span data-ttu-id="8f140-181">A.</span><span class="sxs-lookup"><span data-stu-id="8f140-181">A.</span></span> <span data-ttu-id="8f140-182">還原 AdventureWorks 資料庫上的快照集</span><span class="sxs-lookup"><span data-stu-id="8f140-182">Reverting a snapshot on the AdventureWorks database</span></span>  
 <span data-ttu-id="8f140-183">此範例假設 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫上目前只有一個快照集。</span><span class="sxs-lookup"><span data-stu-id="8f140-183">This example assumes that only one snapshot currently exists on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="8f140-184">如需建立還原資料庫之快照集的範例，請參閱 [建立資料庫快照集 &#40;Transact-SQL&#41;](create-a-database-snapshot-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="8f140-184">For the example that creates the snapshot to which the database is reverted here, see [Create a Database Snapshot &#40;Transact-SQL&#41;](create-a-database-snapshot-transact-sql.md).</span></span>  
  
```  
USE master;  
-- Reverting AdventureWorks to AdventureWorks_dbss1800  
RESTORE DATABASE AdventureWorks from   
DATABASE_SNAPSHOT = 'AdventureWorks_dbss1800';  
GO  
```  
  
####  <a name="b-reverting-a-snapshot-on-the-sales-database"></a><a name="Reverting_Sales"></a> <span data-ttu-id="8f140-185">B.</span><span class="sxs-lookup"><span data-stu-id="8f140-185">B.</span></span> <span data-ttu-id="8f140-186">還原 Sales 資料庫上的快照集</span><span class="sxs-lookup"><span data-stu-id="8f140-186">Reverting a snapshot on the Sales database</span></span>  
 <span data-ttu-id="8f140-187">此範例假設 **Sales** 資料庫中目前有兩個快照集： **sales_snapshot0600** 和 **sales_snapshot1200**。</span><span class="sxs-lookup"><span data-stu-id="8f140-187">This example assumes that two snapshots currently exist on the **Sales** database: **sales_snapshot0600** and **sales_snapshot1200**.</span></span> <span data-ttu-id="8f140-188">此範例會刪除較舊的快照集，並將資料庫還原到較新的快照集。</span><span class="sxs-lookup"><span data-stu-id="8f140-188">The example deletes the older of the snapshots and reverts the database to the more recent snapshot.</span></span>  
  
 <span data-ttu-id="8f140-189">如需建立範例資料庫與此範例使用之快照的程式碼，請參閱：</span><span class="sxs-lookup"><span data-stu-id="8f140-189">For the code for creating the sample database and snapshots on which this example depends, see:</span></span>  
  
-   <span data-ttu-id="8f140-190">對於 **Sales** 資料庫與 **sales_snapshot0600** 快照集，請參閱 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) 中的＜使用檔案群組建立資料庫＞和＜建立資料庫快照集＞。</span><span class="sxs-lookup"><span data-stu-id="8f140-190">For the **Sales** database and the **sales_snapshot0600** snapshot, see "Creating a database with filegroups" and "Creating a database snapshot" in [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
-   <span data-ttu-id="8f140-191">對於 **sales_snapshot1200** 快照集，請參閱 [建立資料庫快照集 &#40;Transact-SQL&#41;](create-a-database-snapshot-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="8f140-191">For the **sales_snapshot1200** snapshot, see "Creating a snapshot on the Sales database" in [Create a Database Snapshot &#40;Transact-SQL&#41;](create-a-database-snapshot-transact-sql.md).</span></span>  
  
```  
--Test to see if sales_snapshot0600 exists and if it   
-- does, delete it.  
IF EXISTS (SELECT dbid FROM sys.databases  
    WHERE NAME='sales_snapshot0600')  
    DROP DATABASE SalesSnapshot0600;  
GO  
-- Reverting Sales to sales_snapshot1200  
USE master;  
RESTORE DATABASE Sales FROM DATABASE_SNAPSHOT = 'sales_snapshot1200';  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="8f140-192">相關工作</span><span class="sxs-lookup"><span data-stu-id="8f140-192">Related Tasks</span></span>  
  
-   [<span data-ttu-id="8f140-193">建立資料庫快照集 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8f140-193">Create a Database Snapshot &#40;Transact-SQL&#41;</span></span>](create-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="8f140-194">檢視資料庫快照集 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8f140-194">View a Database Snapshot &#40;SQL Server&#41;</span></span>](view-a-database-snapshot-sql-server.md)  
  
-   [<span data-ttu-id="8f140-195">卸除資料庫快照集 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8f140-195">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="8f140-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f140-196">See Also</span></span>  
 <span data-ttu-id="8f140-197">[資料庫快照集 &#40;SQL Server&#41;](database-snapshots-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8f140-197">[Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md) </span></span>  
 <span data-ttu-id="8f140-198">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f140-198">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="8f140-199">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8f140-199">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 [<span data-ttu-id="8f140-200">資料庫鏡像和資料庫快照集 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8f140-200">Database Mirroring and Database Snapshots &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/database-mirroring-and-database-snapshots-sql-server.md)  
  
  
