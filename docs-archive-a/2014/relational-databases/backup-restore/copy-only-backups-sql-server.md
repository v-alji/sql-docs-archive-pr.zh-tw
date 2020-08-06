---
title: 只複製備份 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- copy-only backups [SQL Server]
- COPY_ONLY option [BACKUP statement]
- backups [SQL Server], copy-only backups
ms.assetid: f82d6918-a5a7-4af8-868e-4247f5b00c52
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fc74d7b1bba2a0163ac9edefb5d465c54ef6296c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606914"
---
# <a name="copy-only-backups-sql-server"></a><span data-ttu-id="95e4d-102">只複製備份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="95e4d-102">Copy-Only Backups (SQL Server)</span></span>
  <span data-ttu-id="95e4d-103">「只複製備份」  是與傳統 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份順序無關的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份。</span><span class="sxs-lookup"><span data-stu-id="95e4d-103">A *copy-only backup* is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup that is independent of the sequence of conventional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span> <span data-ttu-id="95e4d-104">通常，進行備份會變更資料庫，而且會影響往後其他備份的還原方式。</span><span class="sxs-lookup"><span data-stu-id="95e4d-104">Usually, taking a backup changes the database and affects how later backups are restored.</span></span> <span data-ttu-id="95e4d-105">不過，偶爾為了特殊目的在不影響資料庫整體備份及還原程序的情況下進行備份，相當有用。</span><span class="sxs-lookup"><span data-stu-id="95e4d-105">However, occasionally, it is useful to take a backup for a special purpose without affecting the overall backup and restore procedures for the database.</span></span> <span data-ttu-id="95e4d-106">只複製備份即是供此目的之用。</span><span class="sxs-lookup"><span data-stu-id="95e4d-106">Copy-only backups serve this purpose.</span></span>  
  
 <span data-ttu-id="95e4d-107">只複製備份的類型如下所示：</span><span class="sxs-lookup"><span data-stu-id="95e4d-107">The types of copy-only backups are as follows:</span></span>  
  
-   <span data-ttu-id="95e4d-108">只複製完整備份 (所有復原模式)</span><span class="sxs-lookup"><span data-stu-id="95e4d-108">Copy-only full backups (all recovery models)</span></span>  
  
     <span data-ttu-id="95e4d-109">只複製備份不能當做差異基底或差異備份，因此不會影響差異基底。</span><span class="sxs-lookup"><span data-stu-id="95e4d-109">A copy-only backup cannot serve as a differential base or differential backup and does not affect the differential base.</span></span>  
  
     <span data-ttu-id="95e4d-110">還原只複製完整備份與還原任何其他完整備份相同。</span><span class="sxs-lookup"><span data-stu-id="95e4d-110">Restoring a copy-only full backup is the same as restoring any other full backup.</span></span>  
  
-   <span data-ttu-id="95e4d-111">只複製記錄備份 (僅完整復原模式和大量記錄復原模式)</span><span class="sxs-lookup"><span data-stu-id="95e4d-111">Copy-only log backups (full recovery model and bulk-logged recovery model only)</span></span>  
  
     <span data-ttu-id="95e4d-112">只複製記錄備份會保留現有的記錄封存點，因此不會影響一般記錄備份的順序。</span><span class="sxs-lookup"><span data-stu-id="95e4d-112">A copy-only log backup preserves the existing log archive point and, therefore, does not affect the sequencing of regular log backups.</span></span> <span data-ttu-id="95e4d-113">只複製記錄備份通常是沒有必要的。</span><span class="sxs-lookup"><span data-stu-id="95e4d-113">Copy-only log backups are typically unnecessary.</span></span> <span data-ttu-id="95e4d-114">您反倒可以建立新的例行記錄備份 (使用 WITH NORECOVERY)，且一併使用此備份與還原順序所需之任何先前的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="95e4d-114">Instead, you can create a new routine log backup (using WITH NORECOVERY) and use that backup together with any previous log backups that are required for the restore sequence.</span></span> <span data-ttu-id="95e4d-115">但是，只複製記錄備份有時相當利於進行線上還原。</span><span class="sxs-lookup"><span data-stu-id="95e4d-115">However, a copy-only log backup can sometimes be useful for performing an online restore.</span></span> <span data-ttu-id="95e4d-116">如需這類範例，請參閱[範例：線上還原讀取/寫入檔案 &#40;完整復原模式&#41;](example-online-restore-of-a-read-write-file-full-recovery-model.md)。</span><span class="sxs-lookup"><span data-stu-id="95e4d-116">For an example of this, see [Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;](example-online-restore-of-a-read-write-file-full-recovery-model.md).</span></span>  
  
     <span data-ttu-id="95e4d-117">交易記錄永遠不會在只複製備份之後截斷。</span><span class="sxs-lookup"><span data-stu-id="95e4d-117">The transaction log is never truncated after a copy-only backup.</span></span>  
  
 <span data-ttu-id="95e4d-118">只複製備份會記錄在 **backupset** 資料表的 [is_copy_only](/sql/relational-databases/system-tables/backupset-transact-sql) 資料行中。</span><span class="sxs-lookup"><span data-stu-id="95e4d-118">Copy-only backups are recorded in the **is_copy_only** column of the [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) table.</span></span>  
  
## <a name="to-create-a-copy-only-backup"></a><span data-ttu-id="95e4d-119">若要建立只複製備份</span><span class="sxs-lookup"><span data-stu-id="95e4d-119">To Create a Copy-Only Backup</span></span>  
 <span data-ttu-id="95e4d-120">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]或 PowerShell 建立只複製備份。</span><span class="sxs-lookup"><span data-stu-id="95e4d-120">You can create a copy-only backup by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell.</span></span>  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="95e4d-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="95e4d-121">Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="95e4d-122">在 [備份資料庫]\*\*\*\* 對話方塊的 [一般]\*\*\*\* 頁面上，選取 [只複製備份]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="95e4d-122">On the **General** page of the **Back Up Database** dialog box, select the **Copy Only Backup** option.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="95e4d-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="95e4d-123">Using Transact-SQL</span></span>  
 <span data-ttu-id="95e4d-124">基本的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 語法如下：</span><span class="sxs-lookup"><span data-stu-id="95e4d-124">The essential [!INCLUDE[tsql](../../../includes/tsql-md.md)] syntax is as follows:</span></span>  
  
-   <span data-ttu-id="95e4d-125">用於只複製完整備份：</span><span class="sxs-lookup"><span data-stu-id="95e4d-125">For a copy-only full backup:</span></span>  
  
     <span data-ttu-id="95e4d-126">備份資料庫*database_name*到 \<backup_device*> \* .。。使用 COPY_ONLY .。。</span><span class="sxs-lookup"><span data-stu-id="95e4d-126">BACKUP DATABASE *database_name* TO \<backup_device*>\* ... WITH COPY_ONLY ...</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="95e4d-127">指定 DIFFERENTIAL 選項時，COPY_ONLY 沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="95e4d-127">COPY_ONLY has no effect when specified with the DIFFERENTIAL option.</span></span>  
  
-   <span data-ttu-id="95e4d-128">用於只複製記錄備份：</span><span class="sxs-lookup"><span data-stu-id="95e4d-128">For a copy-only log backup:</span></span>  
  
     <span data-ttu-id="95e4d-129">備份記錄*database_name*至 *\<*backup_device*>* .。。使用 COPY_ONLY .。。</span><span class="sxs-lookup"><span data-stu-id="95e4d-129">BACKUP LOG *database_name* TO *\<*backup_device*>* ... WITH COPY_ONLY ...</span></span>  
  
###  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="95e4d-130">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="95e4d-130">Using PowerShell</span></span>  
  
<span data-ttu-id="95e4d-131">使用 `Backup-SqlDatabase` 指令程式搭配 `-CopyOnly` 參數。</span><span class="sxs-lookup"><span data-stu-id="95e4d-131">Use the `Backup-SqlDatabase` cmdlet with the `-CopyOnly` parameter.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="95e4d-132">相關工作</span><span class="sxs-lookup"><span data-stu-id="95e4d-132">Related Tasks</span></span>  

### <a name="to-create-a-full-or-log-backup"></a><span data-ttu-id="95e4d-133">若要建立完整備份或記錄備份</span><span class="sxs-lookup"><span data-stu-id="95e4d-133">To create a full or log backup</span></span>
  
-   [<span data-ttu-id="95e4d-134">建立完整資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="95e4d-134">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="95e4d-135">備份交易記錄 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="95e4d-135">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
### <a name="to-view-copy-only-backups"></a><span data-ttu-id="95e4d-136">檢視只複製備份</span><span class="sxs-lookup"><span data-stu-id="95e4d-136">To view copy-only backups</span></span>
  
-   [<span data-ttu-id="95e4d-137">backupset &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="95e4d-137">backupset &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/backupset-transact-sql)  
  
### <a name="to-set-up-and-use-the-sql-server-powershell-provider"></a><span data-ttu-id="95e4d-138">若要設定和使用 SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="95e4d-138">To set up and use the SQL Server PowerShell provider</span></span>
  
-   [<span data-ttu-id="95e4d-139">SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="95e4d-139">SQL Server PowerShell Provider</span></span>](../../powershell/sql-server-powershell-provider.md)  

## <a name="see-also"></a><span data-ttu-id="95e4d-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95e4d-140">See Also</span></span>  
 <span data-ttu-id="95e4d-141">[備份概觀 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="95e4d-141">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="95e4d-142">[復原模式 &#40;SQL Server&#41;](recovery-models-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="95e4d-142">[Recovery Models &#40;SQL Server&#41;](recovery-models-sql-server.md) </span></span>  
 <span data-ttu-id="95e4d-143">[使用備份與還原複製資料庫](../databases/copy-databases-with-backup-and-restore.md) </span><span class="sxs-lookup"><span data-stu-id="95e4d-143">[Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md) </span></span>  
 [<span data-ttu-id="95e4d-144">還原和復原概觀 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="95e4d-144">Restore and Recovery Overview &#40;SQL Server&#41;</span></span>](restore-and-recovery-overview-sql-server.md)  
