---
title: 準備鏡像資料庫以進行鏡像 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], preparing for mirroring
- logins [SQL Server], database mirroring
- mirror database [SQL Server]
ms.assetid: 8676f9d8-c451-419b-b934-786997d46c2b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cf46b4f6fd8e7af55e1930ef6063c4754673fa79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701845"
---
# <a name="prepare-a-mirror-database-for-mirroring-sql-server"></a><span data-ttu-id="0ff0c-102">準備鏡像資料庫以進行鏡像 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0ff0c-102">Prepare a Mirror Database for Mirroring (SQL Server)</span></span>
  <span data-ttu-id="0ff0c-103">資料庫擁有者或系統管理員必須確認鏡像資料庫已經建立且做好鏡像的準備，才能啟動資料庫鏡像工作階段。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-103">Before a database mirroring session can start, the database owner or system administrator must make sure that the mirror database has been created and is ready for mirroring.</span></span> <span data-ttu-id="0ff0c-104">建立新的鏡像資料庫時，最少需要建立主體資料庫的完整備份，以及一個後續記錄備份，並使用 WITH NORECOVERY 將這兩者同時還原到鏡像伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-104">Creating a new mirror database minimally requires taking a full backup of the principal database and a subsequent log backup and restoring them both onto the mirror server instance, using WITH NORECOVERY.</span></span>  
  
 <span data-ttu-id="0ff0c-105">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中準備鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-105">This topic describes how to prepare a mirror database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0ff0c-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="0ff0c-106">Before You Begin</span></span>  
  
###  <a name="requirements"></a><a name="Requirements"></a> <span data-ttu-id="0ff0c-107">需求</span><span class="sxs-lookup"><span data-stu-id="0ff0c-107">Requirements</span></span>  
  
-   <span data-ttu-id="0ff0c-108">主體和鏡像伺服器執行個體必須在相同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本上執行。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-108">The principal and mirror server instances must be running on the same version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0ff0c-109">雖然鏡像伺服器有可能擁有較高版本的 SQL Server，但是只有在仔細規劃的升級程序中才建議使用這個組態。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-109">While it is possible for the mirror server to have a higher version of SQL Server, this configuration is only recommended during a carefully planned upgrade process.</span></span> <span data-ttu-id="0ff0c-110">在這種組態中，您會遇到自動容錯移轉的風險，此時資料移動會自動暫停，因為資料無法移到較低版本的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-110">In such a configuration, you run the risk of an automatic failover, in which data movement is automatically suspended because data cannot move to a lower version of SQL Server.</span></span> <span data-ttu-id="0ff0c-111">如需詳細資訊，請參閱 [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](upgrading-mirrored-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-111">For more information, see [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](upgrading-mirrored-instances.md).</span></span>  
  
-   <span data-ttu-id="0ff0c-112">主體和鏡像伺服器執行個體必須在相同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本上執行。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-112">The principal and mirror server instances must be running on the same edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0ff0c-113">如需 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中資料庫鏡像支援的相關資訊，請參閱 [SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-113">For information about support for database mirroring in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="0ff0c-114">資料庫必須使用完整復原模式。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-114">The database must use the full recovery model.</span></span>  
  
     <span data-ttu-id="0ff0c-115">如需詳細資訊，請參閱[檢視或變更資料庫的復原模式 &#40;SQL Server &#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md) 或 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 和 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-115">For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md) or [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) and [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
-   <span data-ttu-id="0ff0c-116">鏡像資料庫的名稱必須和主體資料庫的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-116">The name of the mirror database must be the same as the name of the principal database.</span></span>  
  
-   <span data-ttu-id="0ff0c-117">鏡像資料庫必須處於 RESTORING 狀態，鏡像作業才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-117">The mirror database must be in the RESTORING state for mirroring to work.</span></span> <span data-ttu-id="0ff0c-118">當準備鏡像資料庫時，您必須使用 RESTORE WITH NORECOVERY 來進行每一項還原作業。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-118">When preparing a mirror database, you must use RESTORE WITH NORECOVERY for every restore operation.</span></span> <span data-ttu-id="0ff0c-119">至少需要使用 RESTORE WITH NORECOVERY 還原主體資料庫的完整備份，接著還原所有後續記錄備份。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-119">Minimally, you will need to restore WITH NORECOVERY a full backup of the principal database, followed by all subsequent log backups.</span></span>  
  
-   <span data-ttu-id="0ff0c-120">您打算建立鏡像資料庫的系統必須配備具有足夠空間可以保存鏡像資料庫的磁碟機。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-120">The system where you plan to create the mirror database must possesses a disk drive with sufficient space to hold the mirror database.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0ff0c-121">限制事項</span><span class="sxs-lookup"><span data-stu-id="0ff0c-121">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="0ff0c-122">您無法鏡像 **master**、 **msdb**、 **temp**或 **model** 系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-122">You cannot mirror the **master**, **msdb**, **temp**, or **model** system databases.</span></span>  
  
-   <span data-ttu-id="0ff0c-123">您無法將屬於[AlwaysOn 可用性群組 (SQL Server) ](../availability-groups/windows/always-on-availability-groups-sql-server.md)的資料庫進行鏡像。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-123">You cannot mirror a database that belongs to an [AlwaysOn Availability Groups (SQL Server)](../availability-groups/windows/always-on-availability-groups-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="0ff0c-124">建議</span><span class="sxs-lookup"><span data-stu-id="0ff0c-124">Recommendations</span></span>  
  
-   <span data-ttu-id="0ff0c-125">使用主體資料庫的最近完整資料庫備份或最近差異資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-125">Use a very recent full database backup or a recent differential database backup of the principal database.</span></span>  
  
-   <span data-ttu-id="0ff0c-126">如果主體資料庫上排程執行記錄備份作業的頻率很高，您可能必須停用備份作業，直到鏡像啟動為止。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-126">If a log backup job is scheduled to run very frequently on the principal database, you might have to disable the backup job until mirroring has started.</span></span>  
  
-   <span data-ttu-id="0ff0c-127">如果可行的話，鏡像資料庫的路徑 (包括磁碟機代號) 應該要和主體資料庫的路徑完全相同。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-127">If possible, the path (including the drive letter) of the mirror database should be identical to the path of the principal database.</span></span>  
  
     <span data-ttu-id="0ff0c-128">如果檔案路徑必須不同，例如，如果主體資料庫在磁碟機 'F:'，但鏡像系統沒有 F: 磁碟機，您就必須在 RESTORE 陳述式中包含 MOVE 選項。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-128">If the file paths must differ, for example, if the principal database is on drive 'F:' but the mirror system lacks an F: drive, you must include the MOVE option in the RESTORE STATEMENT.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="0ff0c-129">在鏡像工作階段期間，若要加入檔案但又不影響工作階段，則檔案路徑必須同時存在兩個伺服器上。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-129">Adding a file during a mirroring session without impacting the session requires that the path of the file exists on both servers.</span></span> <span data-ttu-id="0ff0c-130">因此，如果您在建立鏡像資料庫時移動資料庫檔案，之後在鏡像資料庫上加入檔案的作業可能會失敗，而且導致鏡像暫停。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-130">Therefore, if you move the database files when creating the mirror database, a later add-file operation might fail on the mirror database and cause mirroring to be suspended.</span></span> <span data-ttu-id="0ff0c-131">如需處理失敗之建立檔案作業的相關資訊，請參閱[疑難排解資料庫鏡像組態 &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-131">For information about dealing with a failed create-file operation, see [Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md).</span></span>  
  
-   <span data-ttu-id="0ff0c-132">如果主體資料庫有任何全文檢索目錄，建議您參閱[資料庫鏡像和全文檢索目錄 &#40;SQL Server&#41;](database-mirroring-and-full-text-catalogs-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-132">If the principal database has any full-text catalogs, we recommend that you see [Database Mirroring and Full-Text Catalogs &#40;SQL Server&#41;](database-mirroring-and-full-text-catalogs-sql-server.md).</span></span>  
  
-   <span data-ttu-id="0ff0c-133">對於實際執行的資料庫，您一定要備份至其他裝置。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-133">For a production database, always back up to a separate device.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0ff0c-134">Security</span><span class="sxs-lookup"><span data-stu-id="0ff0c-134">Security</span></span>  
 <span data-ttu-id="0ff0c-135">備份資料庫時，TRUSTWORTHY 設為 OFF。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-135">TRUSTWORTHY is set to OFF when a database is backed up.</span></span> <span data-ttu-id="0ff0c-136">因此，新鏡像資料庫上的 TRUSTWORTHY 一律為 OFF。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-136">Therefore, TRUSTWORTHY is always OFF on a new mirror database.</span></span> <span data-ttu-id="0ff0c-137">您必須採取額外的設定步驟，以確保資料庫在容錯移轉之後的可信度。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-137">If the database needs to be trustworthy after a failover, additional setup steps are necessary.</span></span> <span data-ttu-id="0ff0c-138">如需詳細資訊，請參閱 [設定鏡像資料庫以使用 Trustworthy 屬性 &#40;Transact-SQL&#41;](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)中準備鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-138">For more information, see [Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md).</span></span>  
  
 <span data-ttu-id="0ff0c-139">如需啟用鏡像資料庫的資料庫主要金鑰之自動解密的相關資訊，請參閱 [設定加密鏡像資料庫](set-up-an-encrypted-mirror-database.md)。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-139">For information about enabling automatic decryption of the database master key of a mirror database, see [Set Up an Encrypted Mirror Database](set-up-an-encrypted-mirror-database.md).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0ff0c-140">權限</span><span class="sxs-lookup"><span data-stu-id="0ff0c-140">Permissions</span></span>  
 <span data-ttu-id="0ff0c-141">資料庫擁有者或系統管理員。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-141">Database owner or system administrator.</span></span>  
  
##  <a name="to-prepare-an-existing-mirror-database-to-restart-mirroring"></a><a name="PrepareToRestartMirroring"></a> <span data-ttu-id="0ff0c-142">若要準備現有的鏡像資料庫以重新啟動鏡像</span><span class="sxs-lookup"><span data-stu-id="0ff0c-142">To Prepare an Existing Mirror Database to Restart Mirroring</span></span>  
 <span data-ttu-id="0ff0c-143">如果鏡像已經移除，而且鏡像資料庫仍處於 RECOVERING 狀態，您就可以重新啟動鏡像。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-143">If mirroring has been removed and the mirror database is still in the RECOVERING state, you can restart mirroring.</span></span>  
  
1.  <span data-ttu-id="0ff0c-144">至少取得主體資料庫上的一個記錄備份。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-144">Take at least one log backup on the principal database.</span></span> <span data-ttu-id="0ff0c-145">如需詳細資訊，請參閱 [備份交易記錄 &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)資料庫還原至新位置，並選擇性地重新命名資料庫。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-145">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="0ff0c-146">在鏡像資料庫上，使用 RESTORE WITH NORECOVERY 來還原自從移除鏡像之後對主體資料庫進行的所有記錄備份。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-146">On the mirror database, use RESTORE WITH NORECOVERY to restore all log backups taken on the principal database since mirroring was removed.</span></span> <span data-ttu-id="0ff0c-147">如需詳細資訊，請參閱 [還原交易記錄備份 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)中準備鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-147">For more information, see [Restore a Transaction Log Backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md).</span></span>  
  
##  <a name="to-prepare-a-new-mirror-database"></a><a name="CombinedProcedure"></a> <span data-ttu-id="0ff0c-148">若要準備新的鏡像資料庫</span><span class="sxs-lookup"><span data-stu-id="0ff0c-148">To Prepare a New Mirror Database</span></span>  
 <span data-ttu-id="0ff0c-149">**準備鏡像資料庫**</span><span class="sxs-lookup"><span data-stu-id="0ff0c-149">**To prepare a mirror database**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0ff0c-150">如需這個程序的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 範例，請參閱本節稍後的 [範例 (Transact-SQL)](#TsqlExample)。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-150">For a [!INCLUDE[tsql](../../includes/tsql-md.md)] example of this procedure, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="0ff0c-151">連接到主體伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-151">Connect to principal server instance.</span></span>  
  
2.  <span data-ttu-id="0ff0c-152">建立主體資料庫的完整資料庫備份或差異資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-152">Create either a full database backup or a differential database backup of the principal database.</span></span>  
  
    -   [<span data-ttu-id="0ff0c-153">建立完整資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0ff0c-153">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
    -   <span data-ttu-id="0ff0c-154">[建立差異資料庫備份 &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-154">[Create a Differential Database Backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="0ff0c-155">一般來說，您必須至少取得主體資料庫上的一個記錄備份。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-155">Typically, you need to take at least one log backup on the principal database.</span></span> <span data-ttu-id="0ff0c-156">不過，如果資料庫剛剛建立，而且尚未建立任何記錄備份，或是如果復原模式剛剛從 SIMPLE 變更為 FULL，可能就不需要有記錄備份。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-156">However, a log backup might be unnecessary, if the database has just been created and no log backup has been taken yet, or if the recovery model has just been changed from SIMPLE to FULL.</span></span>  
  
    -   [<span data-ttu-id="0ff0c-157">備份交易記錄 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0ff0c-157">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
4.  <span data-ttu-id="0ff0c-158">除非備份位於可從兩個系統存取的網路磁碟機上，否則請將資料庫備份和記錄備份複製到將裝載鏡像伺服器執行個體的系統。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-158">Unless the backups are on a network drive that is accessible from both systems, copy the database and log backups to the system that will host the mirror server instance.</span></span>  
  
5.  <span data-ttu-id="0ff0c-159">連接到鏡像伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-159">Connect to mirror server instance.</span></span>  
  
6.  <span data-ttu-id="0ff0c-160">使用 RESTORE WITH NORECOVERY，藉由還原完整資料庫備份來建立鏡像資料庫，然後可選擇將最近的差異資料庫備份還原到鏡像伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-160">Using RESTORE WITH NORECOVERY, create the mirror database by restoring the full database backup and, optionally, the most recent differential database backup, onto the mirror server instance.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0ff0c-161">如果您是按檔案群組逐一還原資料庫，請務必還原整個資料庫。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-161">If you restore the database filegroup by filegroup, be sure to restore the whole database.</span></span>  
  
    -   [<span data-ttu-id="0ff0c-162">還原資料庫備份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0ff0c-162">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
    -   <span data-ttu-id="0ff0c-163">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) 和 [RESTORE 引數 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)中準備鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-163">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) and [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span>  
  
7.  <span data-ttu-id="0ff0c-164">使用 RESTORE WITH NORECOVERY，將任何未完成的記錄備份套用到鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-164">Using RESTORE WITH NORECOVERY, apply any outstanding log backup or backups to the mirror database.</span></span>  
  
    -   [<span data-ttu-id="0ff0c-165">還原交易記錄備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0ff0c-165">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="0ff0c-166">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0ff0c-166">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="0ff0c-167">開始進行資料鏡像工作階段之前，您必須先建立鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-167">Before you can start a database mirroring session, you must create the mirror database.</span></span> <span data-ttu-id="0ff0c-168">您應該在開始鏡像工作階段之前完成此動作。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-168">You should do this just before starting the mirroring session.</span></span>  
  
 <span data-ttu-id="0ff0c-169">此範例使用 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例資料庫，依預設採用簡單復原模式。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-169">This example uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database, which uses the simple recovery model by default.</span></span>  
  
1.  <span data-ttu-id="0ff0c-170">若要以 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫來使用資料庫鏡像，請將它修改為使用完整復原模式：</span><span class="sxs-lookup"><span data-stu-id="0ff0c-170">To use database mirroring with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, modify it to use the full recovery model:</span></span>  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE AdventureWorks   
    SET RECOVERY FULL;  
    GO  
    ```  
  
2.  <span data-ttu-id="0ff0c-171">將資料庫的復原模式從 SIMPLE 修改為 FULL 之後，請建立完整備份，以便用於建立鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-171">After modifying the recovery model of the database from SIMPLE to FULL, create a full backup, which can be used to create the mirror database.</span></span> <span data-ttu-id="0ff0c-172">因為剛剛才變更復原模式，所以指定了 WITH FORMAT 選項以建立新的媒體集。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-172">Because the recovery model has just been changed, the WITH FORMAT option is specified to create a new media set.</span></span> <span data-ttu-id="0ff0c-173">要區分在完整復原模式與簡單復原模式建立的備份時，此方式非常有協助。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-173">This is useful to separate the backups under the full recovery model from any previous backups made under the simple recovery model.</span></span> <span data-ttu-id="0ff0c-174">為了完成這個範例的目的，我們會在資料庫所在的相同磁碟機上建立備份檔案 (`C:\AdventureWorks.bak`)。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-174">For the purpose of this example, the backup file (`C:\AdventureWorks.bak`) is created on the same drive as the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0ff0c-175">對於實際執行的資料庫，您必須備份至其他裝置。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-175">For a production database, you should always back up to a separate device.</span></span>  
  
     <span data-ttu-id="0ff0c-176">在主體伺服器執行個體 (於 `PARTNERHOST1`) 上，為主體資料庫建立完整備份，陳述式如下：</span><span class="sxs-lookup"><span data-stu-id="0ff0c-176">On the principal server instance (on `PARTNERHOST1`), create a full backup of the principal database as follows:</span></span>  
  
    ```  
    BACKUP DATABASE AdventureWorks   
        TO DISK = 'C:\AdventureWorks.bak'   
        WITH FORMAT  
    GO  
    ```  
  
3.  <span data-ttu-id="0ff0c-177">將完整備份複製到鏡像伺服器。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-177">Copy the full backup to the mirror server.</span></span>  
  
4.  <span data-ttu-id="0ff0c-178">使用 RESTORE WITH NORECOVERY，將完整備份還原到鏡像伺服器執行個體上。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-178">Using RESTORE WITH NORECOVERY, restore the full backup onto the mirror server instance.</span></span> <span data-ttu-id="0ff0c-179">還原命令需視主體與鏡像資料庫的路徑是否相同而定。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-179">The restore command depends on whether the paths of principal and mirror databases are identical.</span></span>  
  
    -   <span data-ttu-id="0ff0c-180">**若路徑相同：**</span><span class="sxs-lookup"><span data-stu-id="0ff0c-180">**If the paths are identical:**</span></span>  
  
         <span data-ttu-id="0ff0c-181">在鏡像伺服器執行個體 (於 `PARTNERHOST5`) 上，還原完整備份，陳述式如下：</span><span class="sxs-lookup"><span data-stu-id="0ff0c-181">On the mirror server instance (on `PARTNERHOST5`), restore the full backup as follows:</span></span>  
  
        ```  
        RESTORE DATABASE AdventureWorks   
            FROM DISK = 'C:\AdventureWorks.bak'   
            WITH NORECOVERY  
        GO  
        ```  
  
    -   <span data-ttu-id="0ff0c-182">**若路徑不同：**</span><span class="sxs-lookup"><span data-stu-id="0ff0c-182">**If the paths differ:**</span></span>  
  
         <span data-ttu-id="0ff0c-183">若鏡像資料庫的路徑與主體資料庫的路徑不同 (例如，磁碟機代號不同)，則建立鏡像資料庫時，還原作業中必須包含 MOVE 子句。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-183">If the path of the mirror database differs from the path of the principal database (for instance, their drive letters differ), creating the mirror database requires that the restore operation include a MOVE clause.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="0ff0c-184">若主體與鏡像資料庫的路徑名稱不同，您將無法新增檔案。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-184">If the path names of the principal and mirror databases differ, you cannot add a file.</span></span> <span data-ttu-id="0ff0c-185">這是因為接收新增檔案的記錄檔時，鏡像伺服器執行個體會嘗試將新檔案放在主體資料庫所使用的位置。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-185">This is because on receiving the log for the add file operation, the mirror server instance attempts to place the new file in the location used by the principal database.</span></span>  
  
         <span data-ttu-id="0ff0c-186">例如，下列命令會將位於 C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\ 之主體資料庫的備份還原到鏡像資料庫所在的不同位置 D:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Dat`a\`。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-186">For example, the following command restores a backup of a principal database residing in C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\ to a different location, D:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Dat`a\`, where the mirror database is to reside.</span></span>  
  
        ```  
        RESTORE DATABASE AdventureWorks  
           FROM DISK='C:\AdventureWorks.bak'  
           WITH NORECOVERY,   
              MOVE 'AdventureWorks_Data' TO   
                 'D:\Program Files\Microsoft SQL Server\MSSQL.n\MSSQL\Data\AdventureWorks_Data.mdf',   
              MOVE 'AdventureWorks_Log' TO  
                 'D:\Program Files\Microsoft SQL Server\MSSQL.n\MSSQL\Data\AdventureWorks_Log.ldf';  
        GO  
        ```  
  
5.  <span data-ttu-id="0ff0c-187">建立完整備份之後，您必須在主體資料庫上建立記錄備份。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-187">After you create the full backup, you must create a log backup on the principal database.</span></span> <span data-ttu-id="0ff0c-188">例如，下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式會將記錄備份至前一次完整備份所使用的相同檔案：</span><span class="sxs-lookup"><span data-stu-id="0ff0c-188">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement backs up the log to the same file used by the preceding full backup:</span></span>  
  
    ```  
    BACKUP LOG AdventureWorks   
        TO DISK = 'C:\AdventureWorks.bak'   
    GO  
    ```  
  
6.  <span data-ttu-id="0ff0c-189">您必須先套用必要的記錄備份 (以及任何後續記錄備份)，才能啟動鏡像。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-189">Before you can start mirroring, you must apply the required log backup (and any subsequent log backups).</span></span>  
  
     <span data-ttu-id="0ff0c-190">例如，下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式會從 `C:\AdventureWorks.bak`還原第一筆記錄：</span><span class="sxs-lookup"><span data-stu-id="0ff0c-190">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement restores the first log from `C:\AdventureWorks.bak`:</span></span>  
  
    ```  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\AdventureWorks.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
7.  <span data-ttu-id="0ff0c-191">如果啟動鏡像之前執行了任何額外的記錄備份，您也必須使用 WITH NORECOVERY，依序將這些記錄備份全部還原到鏡像伺服器。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-191">If any additional log backups occur before you start mirroring, you must also restore all of those log backups, in sequence, to the mirror server using WITH NORECOVERY.</span></span>  
  
     <span data-ttu-id="0ff0c-192">例如，下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式會從 `C:\AdventureWorks.bak`還原兩個額外的記錄：</span><span class="sxs-lookup"><span data-stu-id="0ff0c-192">For example, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement restores two additional logs from `C:\AdventureWorks.bak`:</span></span>  
  
    ```  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\AdventureWorks.bak'   
        WITH FILE=2, NORECOVERY  
    GO  
    RESTORE LOG AdventureWorks   
        FROM DISK = 'C:\AdventureWorks.bak'   
        WITH FILE=3, NORECOVERY  
    GO  
    ```  
  
 <span data-ttu-id="0ff0c-193">如需設定資料庫鏡像、顯示安全性設定、準備鏡像資料庫、設定夥伴及新增見證的完整範例，請參閱 [設定資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md)中準備鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-193">For a complete example of setting up database mirroring, showing security setup, preparing the mirror database, setting up the partners, and adding a witness, see [Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-preparing-a-mirror-database"></a><a name="FollowUp"></a> <span data-ttu-id="0ff0c-194">後續操作：準備鏡像資料庫之後</span><span class="sxs-lookup"><span data-stu-id="0ff0c-194">Follow Up: After Preparing a Mirror Database</span></span>  
  
1.  <span data-ttu-id="0ff0c-195">如果您在最近的 RESTORE LOG 作業之後已經建立任何額外的記錄備份，則必須使用 RESTORE WITH NORECOVERY 手動套用每一份額外的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-195">If any additional log backups have been taken since your most recent RESTORE LOG operation, you must manually apply every additional log backup, using RESTORE WITH NORECOVERY.</span></span>  
  
2.  <span data-ttu-id="0ff0c-196">啟動鏡像工作階段。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-196">Start the mirroring session.</span></span> <span data-ttu-id="0ff0c-197">如需詳細資訊，請參閱 [使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md) ，在 [使用 Windows 驗證建立資料庫鏡像工作階段 &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md)中準備鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-197">For more information, see [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md) or [Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md).</span></span>  
  
3.  <span data-ttu-id="0ff0c-198">如果已停用主體資料庫上的備份作業，請重新啟用這項作業。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-198">If you disabled the backup job on the principal database, reenable the job.</span></span>  
  
4.  <span data-ttu-id="0ff0c-199">您必須在鏡像開始之後執行額外的設定步驟，以確保資料庫在容錯移轉之後的可信度。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-199">If the database needs to be trustworthy after a failover, extra setup steps are necessary after mirroring begins.</span></span> <span data-ttu-id="0ff0c-200">如需詳細資訊，請參閱 [設定鏡像資料庫以使用 Trustworthy 屬性 &#40;Transact-SQL&#41;](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)中準備鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="0ff0c-200">For more information, see [Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="0ff0c-201">相關工作</span><span class="sxs-lookup"><span data-stu-id="0ff0c-201">Related Tasks</span></span>  
  
-   [<span data-ttu-id="0ff0c-202">建立完整資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0ff0c-202">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="0ff0c-203">還原交易記錄備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0ff0c-203">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
-   [<span data-ttu-id="0ff0c-204">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0ff0c-204">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="0ff0c-205">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0ff0c-205">Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring-establish-session-windows-authentication.md)  
  
-   [<span data-ttu-id="0ff0c-206">設定加密鏡像資料庫</span><span class="sxs-lookup"><span data-stu-id="0ff0c-206">Set Up an Encrypted Mirror Database</span></span>](set-up-an-encrypted-mirror-database.md)  
  
-   [<span data-ttu-id="0ff0c-207">設定鏡像資料庫以使用 Trustworthy 屬性 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0ff0c-207">Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;</span></span>](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="0ff0c-208">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ff0c-208">See Also</span></span>  
 <span data-ttu-id="0ff0c-209">[資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0ff0c-209">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="0ff0c-210">[資料庫鏡像和 AlwaysOn 可用性群組的傳輸安全性 &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="0ff0c-210">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="0ff0c-211">[設定資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0ff0c-211">[Setting Up Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="0ff0c-212">[備份並還原全文檢索目錄與索引。](../../relational-databases/indexes/indexes.md) </span><span class="sxs-lookup"><span data-stu-id="0ff0c-212">[Back Up and Restore Full-Text Catalogs and Indexes](../../relational-databases/indexes/indexes.md) </span></span>  
 <span data-ttu-id="0ff0c-213">[資料庫鏡像和全文檢索目錄 &#40;SQL Server&#41;](database-mirroring-and-full-text-catalogs-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0ff0c-213">[Database Mirroring and Full-Text Catalogs &#40;SQL Server&#41;](database-mirroring-and-full-text-catalogs-sql-server.md) </span></span>  
 <span data-ttu-id="0ff0c-214">[資料庫鏡像和複寫 &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0ff0c-214">[Database Mirroring and Replication &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md) </span></span>  
 <span data-ttu-id="0ff0c-215">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0ff0c-215">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="0ff0c-216">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0ff0c-216">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="0ff0c-217">RESTORE 引數 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0ff0c-217">RESTORE Arguments &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-arguments-transact-sql)  
  
  
