---
title: 檔案還原 (簡單復原模式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- file restores [SQL Server]
- simple recovery model [SQL Server]
- restoring files [SQL Server], Transact-SQL restore sequence
- restoring files [SQL Server]
- Transact-SQL restore sequence
- restoring files [SQL Server], simple recovery model
- file restores [SQL Server], simple recovery model
- file restores [SQL Server], Transact-SQL restore sequence
ms.assetid: b6d07386-7c6f-4cc6-be32-93289adbd3d6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2ed48f48f531e727de5d6e1403ef47f5399f874d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699829"
---
# <a name="file-restores-simple-recovery-model"></a><span data-ttu-id="9c84c-102">檔案還原 (簡單復原模式)</span><span class="sxs-lookup"><span data-stu-id="9c84c-102">File Restores (Simple Recovery Model)</span></span>
  <span data-ttu-id="9c84c-103">這個主題僅與至少包含一個唯讀次要檔案群組的簡單模式資料庫有關。</span><span class="sxs-lookup"><span data-stu-id="9c84c-103">This topic is relevant only for simple-model databases that contain at least one read-only secondary filegroup.</span></span>  
  
 <span data-ttu-id="9c84c-104">檔案還原的目的是還原一個或多個損毀的檔案，而不還原整個資料庫。</span><span class="sxs-lookup"><span data-stu-id="9c84c-104">In a file restore, the goal is to restore one or more damaged files without restoring the whole database.</span></span> <span data-ttu-id="9c84c-105">在簡單復原模式下，僅支援唯讀檔案的檔案備份。</span><span class="sxs-lookup"><span data-stu-id="9c84c-105">Under the simple recovery model, file backups are supported only for read-only files.</span></span> <span data-ttu-id="9c84c-106">透過還原資料庫或部分備份，永遠一併還原主要檔案群組和讀取/寫入次要檔案群組。</span><span class="sxs-lookup"><span data-stu-id="9c84c-106">The primary filegroup and read/write secondary filegroups are always restored together, by restoring a database or partial backup.</span></span>  
  
 <span data-ttu-id="9c84c-107">這些檔案還原實例如下：</span><span class="sxs-lookup"><span data-stu-id="9c84c-107">The file-restore scenarios are as follows:</span></span>  
  
-   <span data-ttu-id="9c84c-108">離線檔案還原</span><span class="sxs-lookup"><span data-stu-id="9c84c-108">Offline file restore</span></span>  
  
     <span data-ttu-id="9c84c-109">在 *「離線檔案還原」* (Offline File Restore) 中，還原損毀的檔案或檔案群組時，資料庫處於離線狀態。</span><span class="sxs-lookup"><span data-stu-id="9c84c-109">In an *offline file restore*, the database is offline while damaged files or filegroups are restored.</span></span> <span data-ttu-id="9c84c-110">在還原順序結束後，資料庫會恢復上線。</span><span class="sxs-lookup"><span data-stu-id="9c84c-110">At the end of the restore sequence, the database comes online.</span></span>  
  
     <span data-ttu-id="9c84c-111">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的所有版本都支援離線檔案還原。</span><span class="sxs-lookup"><span data-stu-id="9c84c-111">All editions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] support offline file restore.</span></span>  
  
-   <span data-ttu-id="9c84c-112">線上檔案還原</span><span class="sxs-lookup"><span data-stu-id="9c84c-112">Online file restore</span></span>  
  
     <span data-ttu-id="9c84c-113">在 *「線上檔案還原」* (Online File Restore) 中，如果資料庫在還原期間處於線上，則在檔案還原期間也會處於線上。</span><span class="sxs-lookup"><span data-stu-id="9c84c-113">In an *online file restore*, if database is online at restore time, it remains online during the file restore.</span></span> <span data-ttu-id="9c84c-114">不過，在還原作業期間，包含正在還原之檔案的每個檔案群組都會離線。</span><span class="sxs-lookup"><span data-stu-id="9c84c-114">However, each filegroup in which a file is being restored is offline during the restore operation.</span></span> <span data-ttu-id="9c84c-115">離線檔案群組中的所有檔案都復原後，檔案群組就會自動回到線上。</span><span class="sxs-lookup"><span data-stu-id="9c84c-115">After all the files in an offline filegroup are recovered, the filegroup is automatically brought online.</span></span>  
  
     <span data-ttu-id="9c84c-116">如需線上頁面和檔案還原支援的相關資訊，請參閱 [SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="9c84c-116">For information about support for online page and file restore, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="9c84c-117">如需線上還原的詳細資訊，請參閱[線上還原 &#40;SQL Server&#41;](online-restore-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9c84c-117">For more information about online restores, see [Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md).</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="9c84c-118">如果您想要讓資料庫離線以進行檔案還原，請在啟動還原順序之前，先執行下列 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) 陳述式來使資料庫離線：ALTER DATABASE *database_name* SET OFFLINE。</span><span class="sxs-lookup"><span data-stu-id="9c84c-118">If you want the database to be offline for a file restore, take the database offline before you start the restore sequence by executing the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) statement: ALTER DATABASE *database_name* SET OFFLINE.</span></span>  
  

  
##  <a name="overview-of-file-and-filegroup-restore-under-the-simple-recovery-model"></a><a name="Overview"></a> <span data-ttu-id="9c84c-119">簡單復原模式下的檔案和檔案群組還原概觀</span><span class="sxs-lookup"><span data-stu-id="9c84c-119">Overview of File and Filegroup Restore Under the Simple Recovery Model</span></span>  
 <span data-ttu-id="9c84c-120">檔案還原案例是單一還原順序，涵蓋複製、向前復原及復原適當資料等動作，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9c84c-120">A file restore scenario consists of a single restore sequence that copies, rolls forward, and recovers the appropriate data as follows:</span></span>  
  
1.  <span data-ttu-id="9c84c-121">從最新的檔案備份來還原每一個損毀的檔案。</span><span class="sxs-lookup"><span data-stu-id="9c84c-121">Restore each damaged file from its most recent file backup.</span></span>  
  
2.  <span data-ttu-id="9c84c-122">針對每個已還原的檔案，還原其最新的差異檔案備份，並復原資料庫。</span><span class="sxs-lookup"><span data-stu-id="9c84c-122">Restore the most recent differential file backup for each restored file and recover the database.</span></span>  
  
### <a name="transact-sql-steps-for-file-restore-sequence-simple-recovery-model"></a><span data-ttu-id="9c84c-123">檔案還原順序的 Transact-SQL 步驟 (簡單復原模式)</span><span class="sxs-lookup"><span data-stu-id="9c84c-123">Transact-SQL Steps for File Restore Sequence (Simple Recovery Model)</span></span>  
 <span data-ttu-id="9c84c-124">本節顯示簡單檔案還原順序的基本 [!INCLUDE[tsql](../../../includes/tsql-md.md)][RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 選項。</span><span class="sxs-lookup"><span data-stu-id="9c84c-124">This section shows the essential [!INCLUDE[tsql](../../../includes/tsql-md.md)][RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) options for a simple file-restore sequence.</span></span> <span data-ttu-id="9c84c-125">會省略與這個檔案還原無關的語法和詳細資料。</span><span class="sxs-lookup"><span data-stu-id="9c84c-125">Syntax and details that are not relevant to this purpose are omitted.</span></span>  
  
 <span data-ttu-id="9c84c-126">還原順序只包含兩個 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="9c84c-126">The restore sequence contains only two [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="9c84c-127">第一個陳述式會還原次要檔案 (即 `A`檔案)，而此檔案是使用 WITH NORECOVERY 進行還原。</span><span class="sxs-lookup"><span data-stu-id="9c84c-127">The first statement restores a secondary file, file `A`, which is restored using WITH NORECOVERY.</span></span> <span data-ttu-id="9c84c-128">第二項作業還原其他兩個檔案 ( `B` 和 `C` )，而這些檔案是使用 WITH RECOVERY 從不同的備份裝置進行還原。</span><span class="sxs-lookup"><span data-stu-id="9c84c-128">The second operation restores two other files, `B` and `C` which are restored using WITH RECOVERY from a different backup device:</span></span>  
  
1.  <span data-ttu-id="9c84c-129">RESTORE DATABASE *database* FILE **=** _name_of_file_A_</span><span class="sxs-lookup"><span data-stu-id="9c84c-129">RESTORE DATABASE *database* FILE **=**_name_of_file_A_</span></span>  
  
     <span data-ttu-id="9c84c-130">FROM *file_backup_of_file_A*</span><span class="sxs-lookup"><span data-stu-id="9c84c-130">FROM *file_backup_of_file_A*</span></span>  
  
     <span data-ttu-id="9c84c-131">WITH NORECOVERY **;**</span><span class="sxs-lookup"><span data-stu-id="9c84c-131">WITH NORECOVERY **;**</span></span>  
  
2.  <span data-ttu-id="9c84c-132">RESTORE DATABASE *database* FILE **=** _name_of_file_B_ **,** _name_of_file_C_</span><span class="sxs-lookup"><span data-stu-id="9c84c-132">RESTORE DATABASE *database* FILE **=**_name_of_file_B_**,**_name_of_file_C_</span></span>  
  
     <span data-ttu-id="9c84c-133">FROM *file_backup_of_files_B_and_C*</span><span class="sxs-lookup"><span data-stu-id="9c84c-133">FROM *file_backup_of_files_B_and_C*</span></span>  
  
     <span data-ttu-id="9c84c-134">WITH RECOVERY **;**</span><span class="sxs-lookup"><span data-stu-id="9c84c-134">WITH RECOVERY **;**</span></span>  
  
### <a name="examples"></a><span data-ttu-id="9c84c-135">範例</span><span class="sxs-lookup"><span data-stu-id="9c84c-135">Examples</span></span>  
  
-   [<span data-ttu-id="9c84c-136">範例：線上還原唯讀檔案 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="9c84c-136">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="9c84c-137">範例：離線還原主要檔案群組與另一個檔案群組 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="9c84c-137">Example: Offline Restore of Primary and One Other Filegroup &#40;Full Recovery Model&#41;</span></span>](example-offline-restore-of-primary-and-one-other-filegroup-full-recovery-model.md)  
  
 
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="9c84c-138">相關工作</span><span class="sxs-lookup"><span data-stu-id="9c84c-138">Related Tasks</span></span>  
 <span data-ttu-id="9c84c-139">**還原檔案和檔案群組**</span><span class="sxs-lookup"><span data-stu-id="9c84c-139">**To restore files and filegroups**</span></span>  
  
-   [<span data-ttu-id="9c84c-140">以覆蓋現有檔案的方式還原檔案與檔案群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9c84c-140">Restore Files and Filegroups over Existing Files &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
-   [<span data-ttu-id="9c84c-141">還原檔案和檔案群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9c84c-141">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="9c84c-142">還原檔案和檔案群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9c84c-142">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
-   <span data-ttu-id="9c84c-143"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="9c84c-143"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="9c84c-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c84c-144">See Also</span></span>  
 <span data-ttu-id="9c84c-145">[備份與還原：互通性與共存性 &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9c84c-145">[Backup and Restore: Interoperability and Coexistence &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span></span>  
 <span data-ttu-id="9c84c-146">[差異備份 &#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9c84c-146">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="9c84c-147">[完整檔案備份 &#40;SQL Server&#41;](full-file-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9c84c-147">[Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md) </span></span>  
 <span data-ttu-id="9c84c-148">[備份概觀 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9c84c-148">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="9c84c-149">[還原和復原概觀 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9c84c-149">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="9c84c-150">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9c84c-150">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="9c84c-151">[完整資料庫還原 &#40;簡單復原模式&#41;](complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="9c84c-151">[Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) </span></span>  
 [<span data-ttu-id="9c84c-152">分次還原 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9c84c-152">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
