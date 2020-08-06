---
title: 完整資料庫備份 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full backups [SQL Server]
- backups [SQL Server], database
- backing up databases [SQL Server], full backups
- estimating database backup size
- backing up [SQL Server], size of backup
- database backups [SQL Server], full backups
- size [SQL Server], backups
- database backups [SQL Server], about backing up databases
ms.assetid: 4d933d19-8d21-4aa1-8153-d230cb3a3f99
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ee871b6cabbe6c2b2cb4f444fd1e2d42d711dfbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699826"
---
# <a name="full-database-backups-sql-server"></a><span data-ttu-id="dea26-102">完整資料庫備份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="dea26-102">Full Database Backups (SQL Server)</span></span>
  <span data-ttu-id="dea26-103">完整資料庫備份會備份整個資料庫。</span><span class="sxs-lookup"><span data-stu-id="dea26-103">A full database backup backs up the whole database.</span></span> <span data-ttu-id="dea26-104">這包括交易記錄的部分，讓完整資料庫得以在還原完整資料庫備份之後復原。</span><span class="sxs-lookup"><span data-stu-id="dea26-104">This includes part of the transaction log so that the full database can be recovered after a full database backup is restored.</span></span> <span data-ttu-id="dea26-105">完整資料庫備份代表備份完成時的資料庫。</span><span class="sxs-lookup"><span data-stu-id="dea26-105">Full database backups represent the database at the time the backup finished.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="dea26-106">資料庫的大小增加時，完整資料庫備份就需要更多的時間才能完成，同時也需要更多的儲存空間。</span><span class="sxs-lookup"><span data-stu-id="dea26-106">As a database increases in size full database backups take more time to finish and require more storage space.</span></span> <span data-ttu-id="dea26-107">因此，若為大型資料庫，您可能會想透過一系列的 *「差異資料庫備份」* (Differential database backups) 補充完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="dea26-107">Therefore, for a large database, you might want to supplement a full database backup with a series of *differential database backups*.</span></span> <span data-ttu-id="dea26-108">如需詳細資訊，請參閱 [差異備份 &#40;SQL Server&#41;](differential-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="dea26-108">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dea26-109">資料庫備份上的 TRUSTWORTHY 是設為 OFF。</span><span class="sxs-lookup"><span data-stu-id="dea26-109">TRUSTWORTHY is set to OFF on a database backup.</span></span> <span data-ttu-id="dea26-110">如需如何將 TRUSTWORTHY 設成 ON 的資訊，請參閱 [ALTER DATABASE SET 選項 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)。</span><span class="sxs-lookup"><span data-stu-id="dea26-110">For information about how to set TRUSTWORTHY to ON, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
 <span data-ttu-id="dea26-111">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="dea26-111">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="dea26-112">簡單復原模式下的資料庫備份</span><span class="sxs-lookup"><span data-stu-id="dea26-112">Database Backups Under the Simple Recovery Model</span></span>](#DbBuRMs)  
  
-   [<span data-ttu-id="dea26-113">完整復原模式下的資料庫備份</span><span class="sxs-lookup"><span data-stu-id="dea26-113">Database Backups Under the Full Recovery Model</span></span>](#DbBuRMf)  
  
-   [<span data-ttu-id="dea26-114">使用完整資料庫備份來還原資料庫</span><span class="sxs-lookup"><span data-stu-id="dea26-114">Use a Full Database Backup to Restore the Database</span></span>](#RestoreDbBu)  
  
-   [<span data-ttu-id="dea26-115">相關工作</span><span class="sxs-lookup"><span data-stu-id="dea26-115">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="database-backups-under-the-simple-recovery-model"></a><a name="DbBuRMs"></a> <span data-ttu-id="dea26-116">簡單復原模式下的資料庫備份</span><span class="sxs-lookup"><span data-stu-id="dea26-116">Database Backups Under the Simple Recovery Model</span></span>  
 <span data-ttu-id="dea26-117">在簡單復原模式下，每次備份之後，如果會發生損毀，資料庫都將承受可能遺失工作的風險。</span><span class="sxs-lookup"><span data-stu-id="dea26-117">Under the simple recovery model, after each backup, the database is exposed to potential work loss if a disaster were to occur.</span></span> <span data-ttu-id="dea26-118">工作遺失風險隨著每一次更新而增加，直到下次備份為止；此時工作遺失風險便會歸零，但是又會重新開始另一循環的工作遺失風險。</span><span class="sxs-lookup"><span data-stu-id="dea26-118">The work-loss exposure increases with each update until the next backup, when the work-loss exposure returns to zero and a new cycle of work-loss exposure starts.</span></span> <span data-ttu-id="dea26-119">一段時間之後，備份之間的工作遺失風險會增加。</span><span class="sxs-lookup"><span data-stu-id="dea26-119">Work-loss exposure increases over time between backups.</span></span> <span data-ttu-id="dea26-120">下圖顯示只使用完整資料庫備份之備份策略的工作遺失風險。</span><span class="sxs-lookup"><span data-stu-id="dea26-120">The following illustration shows the work-loss exposure for a backup strategy that uses only full database backups.</span></span>  
  
 <span data-ttu-id="dea26-121">![顯示資料庫備份之間的工作遺失風險](../../database-engine/media/bnr-rmsimple-1-fulldb-backups.gif "顯示資料庫備份之間的工作遺失風險")</span><span class="sxs-lookup"><span data-stu-id="dea26-121">![Shows work-loss exposure between database backups](../../database-engine/media/bnr-rmsimple-1-fulldb-backups.gif "Shows work-loss exposure between database backups")</span></span>  
  
### <a name="example--tsql"></a><span data-ttu-id="dea26-122">範例 ([!INCLUDE[tsql](../../../includes/tsql-md.md)])</span><span class="sxs-lookup"><span data-stu-id="dea26-122">Example ( [!INCLUDE[tsql](../../../includes/tsql-md.md)])</span></span>  
 <span data-ttu-id="dea26-123">下列範例顯示如何使用 WITH FORMAT 來覆寫任何現有備份並建立新的媒體集，以建立完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="dea26-123">The following example shows how to create a full database backup by using WITH FORMAT to overwrite any existing backups and create a new media set.</span></span>  
  
```  
-- Back up the AdventureWorks2012 database to new media set.  
BACKUP DATABASE AdventureWorks2012  
    TO DISK = 'Z:\SQLServerBackups\AdventureWorksSimpleRM.bak'   
    WITH FORMAT;  
GO  
```  
  
##  <a name="database-backups-under-the-full-recovery-model"></a><a name="DbBuRMf"></a> <span data-ttu-id="dea26-124">完整復原模式下的資料庫備份</span><span class="sxs-lookup"><span data-stu-id="dea26-124">Database Backups Under the Full Recovery Model</span></span>  
 <span data-ttu-id="dea26-125">若為使用完整和大量記錄復原的資料庫，資料庫備份是必要的，但還是不足夠。</span><span class="sxs-lookup"><span data-stu-id="dea26-125">For databases that use full and bulk-logged recovery, database backups are necessary but not sufficient.</span></span> <span data-ttu-id="dea26-126">交易記錄備份也是必要的。</span><span class="sxs-lookup"><span data-stu-id="dea26-126">Transaction log backups are also required.</span></span> <span data-ttu-id="dea26-127">下圖顯示完整復原模式下可行的最不複雜的備份策略。</span><span class="sxs-lookup"><span data-stu-id="dea26-127">The following illustration shows the least complex backup strategy that is possible under the full recovery model.</span></span>  
  
 <span data-ttu-id="dea26-128">![完整資料庫備份和記錄備份系列](../../database-engine/media/bnr-rmfull-1-fulldb-log-backups.gif "完整資料庫備份和記錄備份系列")</span><span class="sxs-lookup"><span data-stu-id="dea26-128">![Series of full database backups and log backups](../../database-engine/media/bnr-rmfull-1-fulldb-log-backups.gif "Series of full database backups and log backups")</span></span>  
  
 <span data-ttu-id="dea26-129">如需如何建立記錄備份的相關資訊，請參閱[交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="dea26-129">For information about how to create log backups, see [Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
### <a name="example--tsql"></a><span data-ttu-id="dea26-130">範例 ([!INCLUDE[tsql](../../../includes/tsql-md.md)])</span><span class="sxs-lookup"><span data-stu-id="dea26-130">Example ( [!INCLUDE[tsql](../../../includes/tsql-md.md)])</span></span>  
 <span data-ttu-id="dea26-131">下列範例顯示如何使用 WITH FORMAT 來覆寫任何現有備份並建立新的媒體集，以建立完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="dea26-131">The following example shows how to create a full database backup by using WITH FORMAT to overwrite any existing backups and create a new media set.</span></span> <span data-ttu-id="dea26-132">然後，此範例會接著備份交易記錄。</span><span class="sxs-lookup"><span data-stu-id="dea26-132">Then, the example backs up the transaction log.</span></span> <span data-ttu-id="dea26-133">在實際的情況下，您必須執行一連串的定期記錄備份。</span><span class="sxs-lookup"><span data-stu-id="dea26-133">In a real-life situation, you would have to perform a series of regular log backups.</span></span> <span data-ttu-id="dea26-134">就此範例而言， [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例資料庫會設定為使用完整復原模式。</span><span class="sxs-lookup"><span data-stu-id="dea26-134">For this example, the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database is set to use the full recovery model.</span></span>  
  
```  
USE master;  
ALTER DATABASE AdventureWorks2012 SET RECOVERY FULL;  
GO  
-- Back up the AdventureWorks2012 database to new media set (backup set 1).  
BACKUP DATABASE AdventureWorks2012  
  TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012FullRM.bak'   
  WITH FORMAT;  
GO  
--Create a routine log backup (backup set 2).  
BACKUP LOG AdventureWorks2012 TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012FullRM.bak';  
GO  
```  
  
##  <a name="use-a-full-database-backup-to-restore-the-database"></a><a name="RestoreDbBu"></a> <span data-ttu-id="dea26-135">使用完整資料庫備份來還原資料庫</span><span class="sxs-lookup"><span data-stu-id="dea26-135">Use a Full Database Backup to Restore the Database</span></span>  
 <span data-ttu-id="dea26-136">您可以將資料庫從完整資料庫備份還原到任何位置，在一個步驟中重新建立整個資料庫。</span><span class="sxs-lookup"><span data-stu-id="dea26-136">You can re-create a whole database in one step by restoring the database from a full database backup to any location.</span></span> <span data-ttu-id="dea26-137">在備份中包含足夠的交易記錄，以讓您將資料庫復原至在備份完成時的時間點。</span><span class="sxs-lookup"><span data-stu-id="dea26-137">Enough of the transaction log is included in the backup to let you recover the database to the time when the backup finished.</span></span> <span data-ttu-id="dea26-138">還原的資料庫會符合資料庫備份完成時的原本狀態，再扣除掉任何未認可的交易。</span><span class="sxs-lookup"><span data-stu-id="dea26-138">The restored database matches the state of the original database when the database backup finished, minus any uncommitted transactions.</span></span> <span data-ttu-id="dea26-139">在完整復原模式之下，應該接著還原所有後續的交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="dea26-139">Under the full recovery model, you should then restore all subsequent transaction log backups.</span></span> <span data-ttu-id="dea26-140">在資料庫復原之後，會回復未認可的交易。</span><span class="sxs-lookup"><span data-stu-id="dea26-140">When the database is recovered, uncommitted transactions are rolled back.</span></span>  
  
 <span data-ttu-id="dea26-141">如需詳細資訊，請參閱[完整資料庫還原 &#40;簡單復原模式&#41;](complete-database-restores-simple-recovery-model.md) 或[完整資料庫還原 &#40;完整復原模式&#41;](complete-database-restores-full-recovery-model.md)。</span><span class="sxs-lookup"><span data-stu-id="dea26-141">For more information, see [Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) or [Complete Database Restores &#40;Full Recovery Model&#41;](complete-database-restores-full-recovery-model.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="dea26-142">相關工作</span><span class="sxs-lookup"><span data-stu-id="dea26-142">Related Tasks</span></span>  
 <span data-ttu-id="dea26-143">**建立完整資料庫備份**</span><span class="sxs-lookup"><span data-stu-id="dea26-143">**To create a full database backup**</span></span>  
  
-   [<span data-ttu-id="dea26-144">建立完整資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="dea26-144">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   <span data-ttu-id="dea26-145"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="dea26-145"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span></span>  
  
 <span data-ttu-id="dea26-146">**排程備份作業**</span><span class="sxs-lookup"><span data-stu-id="dea26-146">**To schedule backup jobs**</span></span>  
  
 [<span data-ttu-id="dea26-147">使用維護計畫精靈</span><span class="sxs-lookup"><span data-stu-id="dea26-147">Use the Maintenance Plan Wizard</span></span>](../maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="dea26-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dea26-148">See Also</span></span>  
 <span data-ttu-id="dea26-149">[SQL Server 資料庫的備份與還原](back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="dea26-149">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="dea26-150">[備份概觀 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="dea26-150">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="dea26-151">備份與還原 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="dea26-151">Backup and Restore of Analysis Services Databases</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases)  
  
  
