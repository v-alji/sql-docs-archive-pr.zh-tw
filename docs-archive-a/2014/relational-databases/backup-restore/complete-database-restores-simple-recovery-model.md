---
title: 完整的資料庫還原 (簡單復原模式) | Microsoft Docs
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
- simple recovery model [SQL Server]
- restoring [SQL Server], database
ms.assetid: 49828927-1727-4d1d-9ef5-3de43f68c026
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67eee8d7d6f44c9ff83795bf2a8bd612309bf0a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606924"
---
# <a name="complete-database-restores-simple-recovery-model"></a><span data-ttu-id="26bdc-102">完整資料庫還原 (簡單復原模式)</span><span class="sxs-lookup"><span data-stu-id="26bdc-102">Complete Database Restores (Simple Recovery Model)</span></span>
  <span data-ttu-id="26bdc-103">在完整資料庫還原中，目標是還原整個資料庫。</span><span class="sxs-lookup"><span data-stu-id="26bdc-103">In a complete database restore, the goal is to restore the whole database.</span></span> <span data-ttu-id="26bdc-104">在還原期間，整個資料庫為離線狀態。</span><span class="sxs-lookup"><span data-stu-id="26bdc-104">The whole database is offline for the duration of the restore.</span></span> <span data-ttu-id="26bdc-105">在讓資料庫的任何部分上線之前，所有的資料都必須復原到一致的位置；此時資料庫的所有部分都會回到相同的時間點，而且沒有未認可的交易存在。</span><span class="sxs-lookup"><span data-stu-id="26bdc-105">Before any part of the database can come online, all data is recovered to a consistent point in which all parts of the database are at the same point in time and no uncommitted transactions exist.</span></span>  
  
 <span data-ttu-id="26bdc-106">在簡單復原模式下，無法將資料庫還原到特定備份中的特定時間點。</span><span class="sxs-lookup"><span data-stu-id="26bdc-106">Under the simple recovery model, the database cannot be restored to a specific point in time within a specific backup.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="26bdc-107">建議您不要附加或還原來源不明或來源不受信任的資料庫。</span><span class="sxs-lookup"><span data-stu-id="26bdc-107">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="26bdc-108">這些資料庫可能包含惡意程式碼，因此可能執行非預期的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 程式碼，或是修改結構描述或實體資料庫結構而造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="26bdc-108">These databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="26bdc-109">使用來源不明或來源不受信任的資料庫之前，請先在非實際執行伺服器的資料庫上執行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) ，同時檢查資料庫中的程式碼，例如預存程序或其他使用者定義程式碼。</span><span class="sxs-lookup"><span data-stu-id="26bdc-109">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  

  
> [!NOTE]  
>  <span data-ttu-id="26bdc-110">如需舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之備份支援的相關資訊，請參閱 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)的＜相容性支援＞一節。</span><span class="sxs-lookup"><span data-stu-id="26bdc-110">For information about support for backups from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see the "Compatibility Support" section of [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
##  <a name="overview-of-database-restore-under-the-simple-recovery-model"></a><a name="Overview"></a> <span data-ttu-id="26bdc-111">簡單復原模式下的資料庫備份概觀</span><span class="sxs-lookup"><span data-stu-id="26bdc-111">Overview of Database Restore Under the Simple Recovery Model</span></span>  
 <span data-ttu-id="26bdc-112">在簡單復原模式下進行完整資料庫還原只需要一個或兩個 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 陳述式，視是否想要還原差異資料庫備份而定。</span><span class="sxs-lookup"><span data-stu-id="26bdc-112">A full database restore under the simple recovery model involves one or two [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statements, depending on whether you want to restore a differential database backup.</span></span> <span data-ttu-id="26bdc-113">如果您只使用完整資料庫備份，則只需要還原最近的備份，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="26bdc-113">If you are using only a full database backup, just restore the most recent backup, as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="26bdc-114">![只還原完整資料庫備份](../../database-engine/media/bnrr-rmsimple1-fulldbbu.gif "只還原完整資料庫備份")</span><span class="sxs-lookup"><span data-stu-id="26bdc-114">![Restoring only a full database backup](../../database-engine/media/bnrr-rmsimple1-fulldbbu.gif "Restoring only a full database backup")</span></span>  
  
 <span data-ttu-id="26bdc-115">如果也要使用差異資料庫備份，請還原最近一次完整資料庫備份，但不要復原資料庫，然後才還原最近一次差異資料庫備份，並復原資料庫。</span><span class="sxs-lookup"><span data-stu-id="26bdc-115">If you are also using a differential database backup, restore the most recent full database backup without recovering the database, and then restore the most recent differential database backup and recover the database.</span></span> <span data-ttu-id="26bdc-116">下圖顯示這項程序。</span><span class="sxs-lookup"><span data-stu-id="26bdc-116">The following illustration shows this process.</span></span>  
  
 <span data-ttu-id="26bdc-117">![還原完整和差異資料庫備份](../../database-engine/media/bnrr-rmsimple2-diffdbbu.gif "還原完整和差異資料庫備份")</span><span class="sxs-lookup"><span data-stu-id="26bdc-117">![Restoring full and differential database backups](../../database-engine/media/bnrr-rmsimple2-diffdbbu.gif "Restoring full and differential database backups")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="26bdc-118">若您想將資料庫備份還原至不同的伺服器執行個體，請參閱 [使用備份與還原複製資料庫](../databases/copy-databases-with-backup-and-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="26bdc-118">If you plan to restore a database backup onto a different server instance, see [Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md).</span></span>  
  
###  <a name="basic-transact-sql-restore-syntax"></a><a name="TsqlSyntax"></a> <span data-ttu-id="26bdc-119">基本 Transact-SQL RESTORE 語法</span><span class="sxs-lookup"><span data-stu-id="26bdc-119">Basic Transact-SQL RESTORE Syntax</span></span>  
 <span data-ttu-id="26bdc-120">用於還原完整資料庫備份的基本 [!INCLUDE[tsql](../../../includes/tsql-md.md)][RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 語法為：</span><span class="sxs-lookup"><span data-stu-id="26bdc-120">The basic [!INCLUDE[tsql](../../../includes/tsql-md.md)][RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) syntax for restoring a full database backup is:</span></span>  
  
 <span data-ttu-id="26bdc-121">RESTORE DATABASE *database_name* FROM *backup_device* [ WITH NORECOVERY ]</span><span class="sxs-lookup"><span data-stu-id="26bdc-121">RESTORE DATABASE *database_name* FROM *backup_device* [ WITH NORECOVERY ]</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="26bdc-122">若您也想還原差異資料庫備份，請使用 WITH NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="26bdc-122">Use WITH NORECOVERY if you plan to also restore a differential database backup.</span></span>  
  
 <span data-ttu-id="26bdc-123">用於還原資料庫備份的基本 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 語法為：</span><span class="sxs-lookup"><span data-stu-id="26bdc-123">The basic [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) syntax for restoring a database backup is:</span></span>  
  
 <span data-ttu-id="26bdc-124">RESTORE DATABASE *database_name* FROM *backup_device* WITH RECOVERY</span><span class="sxs-lookup"><span data-stu-id="26bdc-124">RESTORE DATABASE *database_name* FROM *backup_device* WITH RECOVERY</span></span>  
  
###  <a name="example-transact-sql"></a><a name="Example"></a> <span data-ttu-id="26bdc-125">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26bdc-125">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="26bdc-126">下列範例首先顯示如何使用 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 陳述式來建立 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫的完整資料庫備份及差異資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="26bdc-126">The following example first shows how to use the [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement to create a full database backup and a differential database backup of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="26bdc-127">此範例接著依序還原這些備份。</span><span class="sxs-lookup"><span data-stu-id="26bdc-127">The example then restores these backups in sequence.</span></span> <span data-ttu-id="26bdc-128">資料庫會還原到差異資料庫備份完成時的狀態。</span><span class="sxs-lookup"><span data-stu-id="26bdc-128">The database is restored to its state as of the time that the differential database backup finished.</span></span>  
  
 <span data-ttu-id="26bdc-129">這個範例顯示在完整資料庫還原實例中，還原順序的一些關鍵選項。</span><span class="sxs-lookup"><span data-stu-id="26bdc-129">The example shows the critical options in a restore sequence for the complete database restore scenario.</span></span> <span data-ttu-id="26bdc-130">*「還原順序」* (Restore sequence) 包含一個或多個還原作業，會在一個或多個還原階段中移動資料。</span><span class="sxs-lookup"><span data-stu-id="26bdc-130">A *restore sequence* consists of one or more restore operations that move data through one or more of the phases of restore.</span></span> <span data-ttu-id="26bdc-131">會省略與這個檔案還原無關的語法和詳細資料。</span><span class="sxs-lookup"><span data-stu-id="26bdc-131">Syntax and details that are not relevant to this purpose are omitted.</span></span> <span data-ttu-id="26bdc-132">為了清楚起見，建議您在復原資料庫時明確指定 RECOVERY 選項，即使它是預設的。</span><span class="sxs-lookup"><span data-stu-id="26bdc-132">When you recover a database, we recommend explicitly specifying the RECOVERY option for clarity, even though it is the default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="26bdc-133">此範例會從設定復原模式為 [的](/sql/t-sql/statements/alter-database-transact-sql) ALTER DATABASE `SIMPLE`陳述式開始進行。</span><span class="sxs-lookup"><span data-stu-id="26bdc-133">The example starts with an [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement that sets the recovery model to `SIMPLE`.</span></span>  
  
```  
USE master;  
--Make sure the database is using the simple recovery model.  
ALTER DATABASE AdventureWorks2012 SET RECOVERY SIMPLE;  
GO  
-- Back up the full AdventureWorks2012 database.  
BACKUP DATABASE AdventureWorks2012   
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'   
  WITH FORMAT;  
GO  
--Create a differential database backup.  
BACKUP DATABASE AdventureWorks2012   
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'  
   WITH DIFFERENTIAL;  
GO  
--Restore the full database backup (from backup set 1).  
RESTORE DATABASE AdventureWorks2012   
FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'   
   WITH FILE=1, NORECOVERY;  
--Restore the differential backup (from backup set 2).  
RESTORE DATABASE AdventureWorks2012   
FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'   
   WITH FILE=2, RECOVERY;  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="26bdc-134">相關工作</span><span class="sxs-lookup"><span data-stu-id="26bdc-134">Related Tasks</span></span>  
 <span data-ttu-id="26bdc-135">**還原完整資料庫備份**</span><span class="sxs-lookup"><span data-stu-id="26bdc-135">**To restore a full database backup**</span></span>  
  
-   [<span data-ttu-id="26bdc-136">在簡單復原模式下還原資料庫備份 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26bdc-136">Restore a Database Backup Under the Simple Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)  
  
-   [<span data-ttu-id="26bdc-137">還原資料庫備份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="26bdc-137">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="26bdc-138">將資料庫還原到新位置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="26bdc-138">Restore a Database to a New Location &#40;SQL Server&#41;</span></span>](restore-a-database-to-a-new-location-sql-server.md)  
  
 <span data-ttu-id="26bdc-139">**還原差異資料庫備份**</span><span class="sxs-lookup"><span data-stu-id="26bdc-139">**To restore a differential database backup**</span></span>  
  
-   [<span data-ttu-id="26bdc-140">還原差異資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="26bdc-140">Restore a Differential Database Backup &#40;SQL Server&#41;</span></span>](restore-a-differential-database-backup-sql-server.md)  
  
 <span data-ttu-id="26bdc-141">**使用 SQL Server 管理物件 (SMO) 還原備份**</span><span class="sxs-lookup"><span data-stu-id="26bdc-141">**To restore a backup by using SQL Server Management Objects (SMO)**</span></span>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A>  
  

  
## <a name="see-also"></a><span data-ttu-id="26bdc-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26bdc-142">See Also</span></span>  
 <span data-ttu-id="26bdc-143">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="26bdc-143">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="26bdc-144">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="26bdc-144">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="26bdc-145">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="26bdc-145">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 <span data-ttu-id="26bdc-146">[完整資料庫備份 &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="26bdc-146">[Full Database Backups &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span></span>  
 <span data-ttu-id="26bdc-147">[差異備份 &#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="26bdc-147">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="26bdc-148">[備份概觀 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="26bdc-148">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="26bdc-149">還原和復原概觀 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="26bdc-149">Restore and Recovery Overview &#40;SQL Server&#41;</span></span>](restore-and-recovery-overview-sql-server.md)  
  
  
