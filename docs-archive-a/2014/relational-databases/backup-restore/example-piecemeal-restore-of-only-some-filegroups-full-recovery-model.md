---
title: 範例：僅限於部分檔案群組的分次還原 (完整復原模式) | Microsoft Docs
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
ms.assetid: bced4b54-e819-472b-b784-c72e14e72a0b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b3cb1a5ea33a5016c99fdf1f5a7f4e892c045b59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709678"
---
# <a name="example-piecemeal-restore-of-only-some-filegroups-full-recovery-model"></a><span data-ttu-id="5b41d-102">範例：僅對部分檔案群組分次還原 (完整復原模式)</span><span class="sxs-lookup"><span data-stu-id="5b41d-102">Example: Piecemeal Restore of Only Some Filegroups (Full Recovery Model)</span></span>
  <span data-ttu-id="5b41d-103">本主題是關於在完整復原模式下，包含多個檔案或檔案群組的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="5b41d-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases under the full recovery model that contain multiple files or filegroups.</span></span>  
  
 <span data-ttu-id="5b41d-104">分次還原順序會在檔案群組層級，分階段地還原與復原資料庫，先從主要檔案群組開始，然後才是所有的讀取/寫入次要檔案群組。</span><span class="sxs-lookup"><span data-stu-id="5b41d-104">A piecemeal restore sequence restores and recovers a database in stages at the filegroup level, starting with the primary and all read/write, secondary filegroups.</span></span>  
  
 <span data-ttu-id="5b41d-105">這個範例當中，使用完整復原模式，名為 `adb`的資料庫包含三個檔案群組。</span><span class="sxs-lookup"><span data-stu-id="5b41d-105">In this example, a database named `adb`, which uses the full recovery model, contains three filegroups.</span></span> <span data-ttu-id="5b41d-106">檔案群組 `A` 可讀取/寫入，而檔案群組 `B` 和檔案群組 `C` 則是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="5b41d-106">Filegroup `A` is read/write, and filegroup `B` and filegroup `C` are read-only.</span></span> <span data-ttu-id="5b41d-107">所有的檔案群組一開始都是在線上。</span><span class="sxs-lookup"><span data-stu-id="5b41d-107">Initially, all of the filegroups are online.</span></span>  
  
 <span data-ttu-id="5b41d-108">資料庫 `B` 的主要檔案群組與檔案群組 `adb` 似乎已損毀。</span><span class="sxs-lookup"><span data-stu-id="5b41d-108">The primary and filegroup `B` of database `adb` appear to be damaged.</span></span> <span data-ttu-id="5b41d-109">主要檔案群組並不大，很快就可還原。</span><span class="sxs-lookup"><span data-stu-id="5b41d-109">The primary filegroup is fairly small and can be restored quickly.</span></span> <span data-ttu-id="5b41d-110">資料庫管理員決定使用分次還原順序來加以還原。</span><span class="sxs-lookup"><span data-stu-id="5b41d-110">The database administrator decides to restore them by using a piecemeal restore sequence.</span></span> <span data-ttu-id="5b41d-111">首先，還原主要檔案群組及後續的交易記錄檔，並復原資料庫。</span><span class="sxs-lookup"><span data-stu-id="5b41d-111">First, the primary filegroup and the subsequent transaction logs are restored the database is recovered.</span></span>  
  
 <span data-ttu-id="5b41d-112">完整未受損的檔案群組 `A` 和 `C` 中含有重要資料。</span><span class="sxs-lookup"><span data-stu-id="5b41d-112">The intact filegroups `A` and `C` contain critical data.</span></span> <span data-ttu-id="5b41d-113">因此，下一步便是復原這兩個檔案群組，讓它們儘快恢復上線。</span><span class="sxs-lookup"><span data-stu-id="5b41d-113">Therefore, they will be recovered next to bring them online as quickly as possible.</span></span> <span data-ttu-id="5b41d-114">最後則是還原並復原已損毀的次要檔案群組 `B`。</span><span class="sxs-lookup"><span data-stu-id="5b41d-114">Finally, the damaged secondary filegroup, `B`, is restored and recovered.</span></span>  
  
## <a name="restore-sequences"></a><span data-ttu-id="5b41d-115">還原順序：</span><span class="sxs-lookup"><span data-stu-id="5b41d-115">Restore Sequences:</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5b41d-116">線上還原順序的語法和離線還原順序的語法相同。</span><span class="sxs-lookup"><span data-stu-id="5b41d-116">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
1.  <span data-ttu-id="5b41d-117">為資料庫 `adb`建立結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="5b41d-117">Create a tail log backup of database `adb`.</span></span> <span data-ttu-id="5b41d-118">您必須執行此步驟，才能讓完整的檔案群組 `A` 和 `C` 利用資料庫還原點保持在最新狀態。</span><span class="sxs-lookup"><span data-stu-id="5b41d-118">This step is essential to make the intact filegroups `A` and `C` current with the recovery point of the database.</span></span>  
  
    ```  
    BACKUP LOG adb TO tailLogBackup WITH NORECOVERY  
    ```  
  
2.  <span data-ttu-id="5b41d-119">主要檔案群組的部分還原。</span><span class="sxs-lookup"><span data-stu-id="5b41d-119">Partial restore of the primary filegroup.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='Primary' FROM backup   
    WITH PARTIAL, NORECOVERY  
    RESTORE LOG adb FROM backup1 WITH NORECOVERY  
    RESTORE LOG adb FROM backup2 WITH NORECOVERY  
    RESTORE LOG adb FROM backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
     <span data-ttu-id="5b41d-120">此時，主要檔案群組為線上狀態。</span><span class="sxs-lookup"><span data-stu-id="5b41d-120">At this point the primary is online.</span></span> <span data-ttu-id="5b41d-121">檔案群組 `A`、 `B`和 `C` 中的所有檔案皆為復原暫止狀態，且檔案群組已離線。</span><span class="sxs-lookup"><span data-stu-id="5b41d-121">Files in filegroups `A`, `B`, and `C` are recovery pending, and the filegroups are offline.</span></span>  
  
3.  <span data-ttu-id="5b41d-122">線上還原檔案群組 `A` 和 `C`。</span><span class="sxs-lookup"><span data-stu-id="5b41d-122">Online restore of filegroups `A` and `C`.</span></span>  
  
     <span data-ttu-id="5b41d-123">由於這些檔案群組的資料並未損毀，因此它們不需要從備份還原，但必須進行復原才能回到線上。</span><span class="sxs-lookup"><span data-stu-id="5b41d-123">Because their data is undamaged, these filegroups do not have to be restored from a backup, but they do have to be recovered to bring them online.</span></span>  
  
     <span data-ttu-id="5b41d-124">資料庫管理員立即復原 `A` 和 `C` 。</span><span class="sxs-lookup"><span data-stu-id="5b41d-124">The database administrator recovers `A` and `C` immediately.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='A', FILEGROUP='C' WITH RECOVERY  
    ```  
  
     <span data-ttu-id="5b41d-125">此時，主要與次要檔案群組 `A` 和 `C` 會在線上。</span><span class="sxs-lookup"><span data-stu-id="5b41d-125">At this point the primary and filegroups `A` and `C` are online.</span></span> <span data-ttu-id="5b41d-126">檔案群組 `B` 裡的檔案會保持復原暫止，而檔案群組為離線。</span><span class="sxs-lookup"><span data-stu-id="5b41d-126">Files in filegroup `B` remain recovery pending, with the filegroup offline.</span></span>  
  
4.  <span data-ttu-id="5b41d-127">線上還原檔案群組 `B`。</span><span class="sxs-lookup"><span data-stu-id="5b41d-127">Online restore of filegroup `B`.</span></span>  
  
     <span data-ttu-id="5b41d-128">檔案群組 `B` 中的檔案，可在此後的任何時間進行還原。</span><span class="sxs-lookup"><span data-stu-id="5b41d-128">Files in filegroup `B` are restored any time thereafter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5b41d-129">檔案群組 `B` 的備份是在檔案群組變成唯讀之後進行的，因此這些檔案不需向前復原。</span><span class="sxs-lookup"><span data-stu-id="5b41d-129">The backup of filegroup `B` was taken after the filegroup became read-only; therefore, these files do not have to be rolled forward.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup WITH RECOVERY  
    ```  
  
     <span data-ttu-id="5b41d-130">所有檔案群組現在都已在線上。</span><span class="sxs-lookup"><span data-stu-id="5b41d-130">All filegroups are now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="5b41d-131">其他範例</span><span class="sxs-lookup"><span data-stu-id="5b41d-131">Additional Examples</span></span>  
  
-   [<span data-ttu-id="5b41d-132">範例：分次還原資料庫 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="5b41d-132">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="5b41d-133">範例：僅限於部分檔案群組的分次還原 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="5b41d-133">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="5b41d-134">範例：線上還原唯讀檔案 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="5b41d-134">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="5b41d-135">範例：分次還原資料庫 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="5b41d-135">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="5b41d-136">範例：線上還原讀取/寫入檔案 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="5b41d-136">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="5b41d-137">範例：線上還原唯讀檔案 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="5b41d-137">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="5b41d-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b41d-138">See Also</span></span>  
 <span data-ttu-id="5b41d-139">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5b41d-139">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="5b41d-140">[線上還原 &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5b41d-140">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="5b41d-141">[套用交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5b41d-141">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="5b41d-142">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5b41d-142">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="5b41d-143">分次還原 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5b41d-143">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
