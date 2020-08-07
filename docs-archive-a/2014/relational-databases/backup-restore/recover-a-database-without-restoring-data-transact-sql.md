---
title: 在不還原資料的情況下復原資料庫 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring [SQL Server], recovery-only
- recovery-only scenario [SQL Server]
- restoring databases [SQL Server], recovery-only
- recovery [SQL Server], recovery-only
- database recovery [SQL Server]
- database restores [SQL Server], recovery-only
- recovery [SQL Server], without restoring data
ms.assetid: 7e8fa620-315d-4e10-a718-23fa5171c09e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 04e4f78e51adb803bb65530c0b3b903aa7f76419
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598478"
---
# <a name="recover-a-database-without-restoring-data-transact-sql"></a><span data-ttu-id="d3fbd-102">在不還原資料的情況下復原資料庫 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d3fbd-102">Recover a Database Without Restoring Data (Transact-SQL)</span></span>
  <span data-ttu-id="d3fbd-103">通常會先還原 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中的所有資料，再復原資料庫。</span><span class="sxs-lookup"><span data-stu-id="d3fbd-103">Usually, all of the data in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database is restored before the database is recovered.</span></span> <span data-ttu-id="d3fbd-104">不過，還原作業可以復原資料庫，而不實際還原備份；例如，復原與資料庫一致的唯讀檔案時即是如此。</span><span class="sxs-lookup"><span data-stu-id="d3fbd-104">However, a restore operation can recover a database without actually restoring a backup; for example, when recovering a read-only file that is consistent with the database.</span></span> <span data-ttu-id="d3fbd-105">這稱為「僅復原的還原」。</span><span class="sxs-lookup"><span data-stu-id="d3fbd-105">This is referred to as a *recovery-only restore*.</span></span> <span data-ttu-id="d3fbd-106">如果離線資料已與資料庫一致，而且只需要回復為可用狀態，僅復原的還原作業就會完成資料庫的復原，並讓資料回到線上。</span><span class="sxs-lookup"><span data-stu-id="d3fbd-106">When offline data is already consistent with the database and needs only to be made available, a recovery-only restore operation completes the recovery of the database and bring the data online.</span></span>  
  
 <span data-ttu-id="d3fbd-107">整個資料庫或一個或多個檔案或檔案群組，都可能發生僅復原的還原。</span><span class="sxs-lookup"><span data-stu-id="d3fbd-107">A recovery-only restore can occur for a whole database or for one or more a files or filegroups.</span></span>  
  
## <a name="recovery-only-database-restore"></a><span data-ttu-id="d3fbd-108">僅復原的資料庫還原</span><span class="sxs-lookup"><span data-stu-id="d3fbd-108">Recovery-Only Database Restore</span></span>  
 <span data-ttu-id="d3fbd-109">僅復原的資料庫還原在下列情況中會很有用：</span><span class="sxs-lookup"><span data-stu-id="d3fbd-109">A recovery-only database restore can be useful in the following situations:</span></span>  
  
-   <span data-ttu-id="d3fbd-110">還原還原順序中最後一個備份時，您未復原資料庫，但是現在想要復原資料庫以使其回到線上。</span><span class="sxs-lookup"><span data-stu-id="d3fbd-110">You did not recover the database when restoring the last backup in a restore sequence, and you now want to recover the database to bring it online.</span></span>  
  
-   <span data-ttu-id="d3fbd-111">資料庫處於待命模式，而您想在不套用其他記錄備份的情況下使資料庫成為可更新的。</span><span class="sxs-lookup"><span data-stu-id="d3fbd-111">The database is in standby mode, and you want to make the database updatable without applying another log backup.</span></span>  
  
 <span data-ttu-id="d3fbd-112">用於僅復原的資料庫還原的 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 語法如下：</span><span class="sxs-lookup"><span data-stu-id="d3fbd-112">The [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) syntax for a recovery-only database restore is as follows:</span></span>  
  
 <span data-ttu-id="d3fbd-113">RESTORE DATABASE *database_name* WITH RECOVERY</span><span class="sxs-lookup"><span data-stu-id="d3fbd-113">RESTORE DATABASE *database_name* WITH RECOVERY</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3fbd-114">FROM **=** \<*backup_device>\* 子句未使用於僅復原的還原，這是因為沒有備份的必要。</span><span class="sxs-lookup"><span data-stu-id="d3fbd-114">The FROM **=** \<*backup_device>\* clause is not used for recovery-only restores because no backup is necessary.</span></span>  
  
 <span data-ttu-id="d3fbd-115">**範例**</span><span class="sxs-lookup"><span data-stu-id="d3fbd-115">**Example**</span></span>  
  
 <span data-ttu-id="d3fbd-116">下列範例會在還原作業中復原 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例資料庫，而不還原資料。</span><span class="sxs-lookup"><span data-stu-id="d3fbd-116">The following example recovers the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database in a restore operation without restoring data.</span></span>  
  
```  
-- Restore database using WITH RECOVERY.  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY  
```  
  
## <a name="recovery-only-file-restore"></a><span data-ttu-id="d3fbd-117">僅復原的檔案還原</span><span class="sxs-lookup"><span data-stu-id="d3fbd-117">Recovery-Only File Restore</span></span>  
 <span data-ttu-id="d3fbd-118">僅復原的檔案還原在下列情況中會很有用：</span><span class="sxs-lookup"><span data-stu-id="d3fbd-118">A recovery-only file restore can be useful in the following situation:</span></span>  
  
 <span data-ttu-id="d3fbd-119">分次還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="d3fbd-119">A database is restored piecemeal.</span></span> <span data-ttu-id="d3fbd-120">主要檔案群組的還原完成之後，未還原的檔案中有一或多個檔案與新的資料庫狀態一致，或許是因為它已經有好一段時間是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="d3fbd-120">After restore of the primary filegroup is complete, one or more of the unrestored files are consistent with the new database state, perhaps because it has been read-only for some time.</span></span> <span data-ttu-id="d3fbd-121">這些檔案只需復原即可；不需要資料複製。</span><span class="sxs-lookup"><span data-stu-id="d3fbd-121">These files only have to be recovered; data copying is unnecessary.</span></span>  
  
 <span data-ttu-id="d3fbd-122">僅復原的還原作業會讓離線檔案群組中的資料回到線上；不會產生資料複製、重做或恢復階段。</span><span class="sxs-lookup"><span data-stu-id="d3fbd-122">A recovery-only restore operation brings the data in the offline filegroup online; no data-copy, redo, or undo phase occurs.</span></span> <span data-ttu-id="d3fbd-123">如需還原階段的相關資訊，請參閱[還原和復原概觀 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d3fbd-123">For information about the phases of restore, see [Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md).</span></span>  
  
 <span data-ttu-id="d3fbd-124">用於僅復原之檔案還原的 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 語法為：</span><span class="sxs-lookup"><span data-stu-id="d3fbd-124">The [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) syntax for a recovery-only file restore is:</span></span>  
  
 <span data-ttu-id="d3fbd-125">還原資料庫*database_name* {FILE **=** _logical_file_name_ |FILEGROUP **=** _logical_filegroup_name_ } [ **，**.。。*n* ] WITH RECOVERY</span><span class="sxs-lookup"><span data-stu-id="d3fbd-125">RESTORE DATABASE *database_name* { FILE **=**_logical_file_name_ | FILEGROUP **=**_logical_filegroup_name_ }[ **,**...*n* ] WITH RECOVERY</span></span>  
  
 <span data-ttu-id="d3fbd-126">**範例**</span><span class="sxs-lookup"><span data-stu-id="d3fbd-126">**Example**</span></span>  
  
 <span data-ttu-id="d3fbd-127">下列範例說明如何針對 `SalesGroup2`資料庫中次要檔案群組 `Sales` 的檔案進行僅復原的檔案還原。</span><span class="sxs-lookup"><span data-stu-id="d3fbd-127">The following example illustrates a recovery-only file restore of the files in a secondary filegroup, `SalesGroup2`, in the `Sales` database.</span></span> <span data-ttu-id="d3fbd-128">主要檔案群組已經在分次還原的初始步驟中還原，而且 `SalesGroup2` 與還原的主要檔案群組一致。</span><span class="sxs-lookup"><span data-stu-id="d3fbd-128">The primary filegroup has already been restored as the initial step of a piecemeal restore, and `SalesGroup2` is consistent with the restored primary filegroup.</span></span> <span data-ttu-id="d3fbd-129">將此檔案群組復原並使其上線，只需要一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="d3fbd-129">Recovering this filegroup and bringing it online requires only a single statement.</span></span>  
  
```  
RESTORE DATABASE Sales FILEGROUP=SalesGroup2 WITH RECOVERY;  
```  
  
## <a name="examples-of-completing-a-piecemeal-restore-scenario-with-a-recovery-only-restore"></a><span data-ttu-id="d3fbd-130">透過僅復原的還原完成分次還原狀況的範例</span><span class="sxs-lookup"><span data-stu-id="d3fbd-130">Examples of Completing a Piecemeal Restore Scenario with a Recovery-Only Restore</span></span>  
 <span data-ttu-id="d3fbd-131">**簡單復原模式**</span><span class="sxs-lookup"><span data-stu-id="d3fbd-131">**Simple recovery model**</span></span>  
  
-   [<span data-ttu-id="d3fbd-132">範例：分次還原資料庫 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="d3fbd-132">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="d3fbd-133">範例：僅限於部分檔案群組的分次還原 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="d3fbd-133">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
 <span data-ttu-id="d3fbd-134">**完整復原模式**</span><span class="sxs-lookup"><span data-stu-id="d3fbd-134">**Full recovery model**</span></span>  
  
-   [<span data-ttu-id="d3fbd-135">範例：分次還原資料庫 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="d3fbd-135">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="d3fbd-136">範例：僅限於部分檔案群組的分次還原 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="d3fbd-136">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A>  
  
## <a name="see-also"></a><span data-ttu-id="d3fbd-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3fbd-137">See Also</span></span>  
 <span data-ttu-id="d3fbd-138">[線上還原 &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d3fbd-138">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="d3fbd-139">[分次還原 &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d3fbd-139">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 <span data-ttu-id="d3fbd-140">[檔案還原 &#40;簡單復原模式&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="d3fbd-140">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="d3fbd-141">[檔案還原 &#40;完整復原模式&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="d3fbd-141">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 [<span data-ttu-id="d3fbd-142">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d3fbd-142">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
