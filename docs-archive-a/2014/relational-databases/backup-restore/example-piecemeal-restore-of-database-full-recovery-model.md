---
title: 範例：分次還原資料庫 (完整復原模式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- piecemeal restores [SQL Server], full recovery model
- restore sequences [SQL Server], piecemeal
ms.assetid: 0a84892d-2f7a-4e77-b2d0-d68b95595210
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5cfccccdbdc0c4fb3b189ee0a9fa3aeaf426578b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704206"
---
# <a name="example-piecemeal-restore-of-database-full-recovery-model"></a><span data-ttu-id="c20a6-102">範例：分次還原資料庫 (完整復原模式)</span><span class="sxs-lookup"><span data-stu-id="c20a6-102">Example: Piecemeal Restore of Database (Full Recovery Model)</span></span>
  <span data-ttu-id="c20a6-103">分次還原順序會在檔案群組層級，分階段地還原與復原資料庫，從主要檔案群組開始，然後才是所有可讀寫的次要檔案群組。</span><span class="sxs-lookup"><span data-stu-id="c20a6-103">A piecemeal restore sequence restores and recovers a database in stages at the filegroup level, beginning with the primary and all read-write, secondary filegroups.</span></span>  
  
 <span data-ttu-id="c20a6-104">在此範例中，資料庫 `adb` 是在損毀之後還原至新的電腦。</span><span class="sxs-lookup"><span data-stu-id="c20a6-104">In this example, database `adb` is restored to a new computer after a disaster.</span></span> <span data-ttu-id="c20a6-105">資料庫使用完整復原模式，因此開始還原之前，必須對資料庫進行結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="c20a6-105">The database is using the full recovery model; therefore, before the restore starts, a tail-log backup must be taken of the database.</span></span> <span data-ttu-id="c20a6-106">在損毀之前，所有檔案群組都在線上。</span><span class="sxs-lookup"><span data-stu-id="c20a6-106">Before the disaster, all the filegroups are online.</span></span> <span data-ttu-id="c20a6-107">檔案群組 `B` 是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="c20a6-107">Filegroup `B` is read-only.</span></span> <span data-ttu-id="c20a6-108">所有的次要檔案群組都必須還原，但是會依照重要性的高低順序來進行： `A` (最高)、 `C`，最後是 `B`。</span><span class="sxs-lookup"><span data-stu-id="c20a6-108">All of the secondary filegroups must be restored, but they are restored in order of importance: `A` (highest), `C`, and lastly `B`.</span></span> <span data-ttu-id="c20a6-109">這個範例有四個記錄備份，包括結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="c20a6-109">In this example, there are four log backups, including the tail-log backup.</span></span>  
  
## <a name="tail-log-backup"></a><span data-ttu-id="c20a6-110">結尾記錄備份</span><span class="sxs-lookup"><span data-stu-id="c20a6-110">Tail-Log Backup</span></span>  
 <span data-ttu-id="c20a6-111">還原資料庫之前，資料庫管理員必須備份記錄的結尾。</span><span class="sxs-lookup"><span data-stu-id="c20a6-111">Before restoring the database, the database administrator must back up the tail of the log.</span></span> <span data-ttu-id="c20a6-112">因為資料庫已損毀，必須使用 NO_TRUNCATE 選項來建立結尾記錄備份：</span><span class="sxs-lookup"><span data-stu-id="c20a6-112">Because the database is damaged, creating the tail-log backup requires using the NO_TRUNCATE option:</span></span>  
  
```  
BACKUP LOG adb TO tailLogBackup WITH NORECOVERY, NO_TRUNCATE  
```  
  
 <span data-ttu-id="c20a6-113">結尾記錄備份是下列還原順序中套用的最後一個備份。</span><span class="sxs-lookup"><span data-stu-id="c20a6-113">The tail-log backup is the last backup that is applied in the following restore sequences.</span></span>  
  
## <a name="restore-sequences"></a><span data-ttu-id="c20a6-114">還原順序</span><span class="sxs-lookup"><span data-stu-id="c20a6-114">Restore Sequences</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c20a6-115">線上還原順序的語法和離線還原順序的語法相同。</span><span class="sxs-lookup"><span data-stu-id="c20a6-115">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
1.  <span data-ttu-id="c20a6-116">部分還原主要與次要檔案群組 `A`。</span><span class="sxs-lookup"><span data-stu-id="c20a6-116">Partial restore of the primary and secondary filegroup `A`.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='Primary' FROM backup1   
       WITH PARTIAL, NORECOVERY  
    RESTORE DATABASE adb FILEGROUP='A' FROM backup2   
       WITH NORECOVERY  
    RESTORE LOG adb FROM backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM backup4 WITH NORECOVERY  
    RESTORE LOG adb FROM backup5 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
2.  <span data-ttu-id="c20a6-117">線上還原檔案群組 `C`。</span><span class="sxs-lookup"><span data-stu-id="c20a6-117">Online restore of filegroup `C`.</span></span>  
  
     <span data-ttu-id="c20a6-118">此時，主要檔案群組和次要檔案群組 `A` 在線上。</span><span class="sxs-lookup"><span data-stu-id="c20a6-118">At this point, the primary filegroup and secondary filegroup `A` are online.</span></span> <span data-ttu-id="c20a6-119">檔案群組 `B` 與 `C` 的所有檔案已暫止復原，且檔案群組處於離線。</span><span class="sxs-lookup"><span data-stu-id="c20a6-119">All the files in filegroups `B` and `C` are recovery pending, and the filegroups are offline.</span></span>  
  
     <span data-ttu-id="c20a6-120">步驟 1 中最後一個 `RESTORE LOG` 陳述式的訊息指出因為無法使用檔案群組 `C` ，所以會延遲回復此檔案群組的交易。</span><span class="sxs-lookup"><span data-stu-id="c20a6-120">Messages from the last `RESTORE LOG` statement in step 1 indicate that rollback of transactions that involve filegroup `C` was deferred, because this filegroup is not available.</span></span> <span data-ttu-id="c20a6-121">一般作業可繼續進行，但在回復作業完成之前，這些交易會維持鎖定，且不會截斷記錄。</span><span class="sxs-lookup"><span data-stu-id="c20a6-121">Regular operations can continue, but locks are held by these transactions and log truncation will not occur until the rollback can complete.</span></span>  
  
     <span data-ttu-id="c20a6-122">在第二個還原順序中，資料庫管理員會還原檔案群組 `C`：</span><span class="sxs-lookup"><span data-stu-id="c20a6-122">In the second restore sequence, the database administrator restores filegroup `C`:</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='C' FROM backup2a WITH NORECOVERY  
    RESTORE LOG adb FROM backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM backup4 WITH NORECOVERY  
    RESTORE LOG adb FROM backup5 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
     <span data-ttu-id="c20a6-123">此時，主要與次要檔案群組 `A` 和 `C` 會在線上。</span><span class="sxs-lookup"><span data-stu-id="c20a6-123">At this point the primary and filegroups `A` and `C` are online.</span></span> <span data-ttu-id="c20a6-124">檔案群組 `B` 裡的檔案會保持復原暫止，而檔案群組為離線。</span><span class="sxs-lookup"><span data-stu-id="c20a6-124">Files in filegroup `B` remain recovery pending, with the filegroup offline.</span></span> <span data-ttu-id="c20a6-125">已解決延遲的交易，而且可以截斷記錄。</span><span class="sxs-lookup"><span data-stu-id="c20a6-125">Deferred transactions have been resolved, and log truncation occurs.</span></span>  
  
3.  <span data-ttu-id="c20a6-126">線上還原檔案群組 `B`。</span><span class="sxs-lookup"><span data-stu-id="c20a6-126">Online restore of filegroup `B`.</span></span>  
  
     <span data-ttu-id="c20a6-127">在第三個還原順序中，資料庫管理員會還原檔案群組 `B`。</span><span class="sxs-lookup"><span data-stu-id="c20a6-127">In the third restore sequence, the database administrator restores filegroup `B`.</span></span> <span data-ttu-id="c20a6-128">在檔案群組變成唯讀之後會進行檔案群組 `B` 的備份，因此不需要在復原期間將它向前復原。</span><span class="sxs-lookup"><span data-stu-id="c20a6-128">The backup of filegroup `B` was taken after the filegroup became read-only; therefore, it does not have to be rolled forward during recovery.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup2b WITH RECOVERY  
    ```  
  
     <span data-ttu-id="c20a6-129">所有檔案群組現在都已在線上。</span><span class="sxs-lookup"><span data-stu-id="c20a6-129">All filegroups are now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="c20a6-130">其他範例</span><span class="sxs-lookup"><span data-stu-id="c20a6-130">Additional Examples</span></span>  
  
-   [<span data-ttu-id="c20a6-131">範例：分次還原資料庫 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="c20a6-131">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="c20a6-132">範例：僅限於部分檔案群組的分次還原 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="c20a6-132">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="c20a6-133">範例：線上還原唯讀檔案 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="c20a6-133">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="c20a6-134">範例：僅限於部分檔案群組的分次還原 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="c20a6-134">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="c20a6-135">範例：線上還原讀取/寫入檔案 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="c20a6-135">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="c20a6-136">範例：線上還原唯讀檔案 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="c20a6-136">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="c20a6-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c20a6-137">See Also</span></span>  
 <span data-ttu-id="c20a6-138">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c20a6-138">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="c20a6-139">[線上還原 &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c20a6-139">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="c20a6-140">[套用交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c20a6-140">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="c20a6-141">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c20a6-141">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="c20a6-142">分次還原 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c20a6-142">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
