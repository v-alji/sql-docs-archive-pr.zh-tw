---
title: 範例：線上還原讀取/寫入檔案 (完整復原模式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- online restores [SQL Server], full recovery model
- restore sequences [SQL Server], online
ms.assetid: 0dbeda81-1464-44ba-9011-914900096368
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5b99a3d97644c2a5f104173457f30fc5b3fd7188
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592073"
---
# <a name="example-online-restore-of-a-read-write-file-full-recovery-model"></a><span data-ttu-id="82558-102">範例：線上還原讀取/寫入檔案 (完整復原模式)</span><span class="sxs-lookup"><span data-stu-id="82558-102">Example: Online Restore of a Read-Write File (Full Recovery Model)</span></span>
  <span data-ttu-id="82558-103">本主題是關於在完整復原模式下，包含多個檔案或檔案群組的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="82558-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases under the full recovery model that contain multiple files or filegroups.</span></span>  
  
 <span data-ttu-id="82558-104">這個範例當中，使用完整復原模式，名為 `adb`的資料庫包含三個檔案群組。</span><span class="sxs-lookup"><span data-stu-id="82558-104">In this example, a database named `adb`, which uses the full recovery model, contains three filegroups.</span></span> <span data-ttu-id="82558-105">檔案群組 `A` 可讀取/寫入，而檔案群組 `B` 和檔案群組 `C` 則是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="82558-105">Filegroup `A` is read/write, and filegroup `B` and filegroup `C` are read-only.</span></span> <span data-ttu-id="82558-106">所有的檔案群組一開始都是在線上。</span><span class="sxs-lookup"><span data-stu-id="82558-106">Initially, all of the filegroups are online.</span></span>  
  
 <span data-ttu-id="82558-107">檔案群組 `a1` 內的 `A` 檔案已經損毀，資料庫管理員決定在資料庫仍然在線上時還原該檔案。</span><span class="sxs-lookup"><span data-stu-id="82558-107">File `a1` in filegroup `A` appears to be damaged, and the database administrator decides to restore it while the database remains online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="82558-108">在簡單復原模式下，不允許線上還原讀取/寫入資料。</span><span class="sxs-lookup"><span data-stu-id="82558-108">Under the simple recovery model, online restore of read/write data is not allowed.</span></span>  
  
## <a name="restore-sequences"></a><span data-ttu-id="82558-109">還原順序</span><span class="sxs-lookup"><span data-stu-id="82558-109">Restore Sequences</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="82558-110">線上還原順序的語法和離線還原順序的語法相同。</span><span class="sxs-lookup"><span data-stu-id="82558-110">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
1.  <span data-ttu-id="82558-111">線上還原檔案 `a1`。</span><span class="sxs-lookup"><span data-stu-id="82558-111">Online restore of file `a1`.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILE='a1' FROM backup   
    WITH NORECOVERY;  
    ```  
  
     <span data-ttu-id="82558-112">此時，檔案 a1 處於 RESTORING 狀態，而檔案群組 A 已離線。</span><span class="sxs-lookup"><span data-stu-id="82558-112">At this point, file a1 is in the RESTORING state, and filegroup A is offline.</span></span>  
  
2.  <span data-ttu-id="82558-113">還原該檔案之後，資料庫管理員會進行新的記錄備份，以確保能擷取到檔案離線的時間點。</span><span class="sxs-lookup"><span data-stu-id="82558-113">After restoring the file, the database administrator takes a new log backup to make sure that the point at which the file went offline is captured.</span></span>  
  
    ```  
    BACKUP LOG adb TO log_backup3;   
    ```  
  
3.  <span data-ttu-id="82558-114">線上還原記錄備份。</span><span class="sxs-lookup"><span data-stu-id="82558-114">Online restore of log backups.</span></span>  
  
     <span data-ttu-id="82558-115">系統管理員會還原已還原之檔案備份後進行的所有記錄備份，並在最新的記錄備份 (步驟 2 所建立的*log_backup3*) 處結束。</span><span class="sxs-lookup"><span data-stu-id="82558-115">The administrator restores all the log backups taken since the restored file backup, ending with the latest log backup (*log_backup3*, taken in step 2).</span></span> <span data-ttu-id="82558-116">還原最後一個備份之後，資料庫就可以復原。</span><span class="sxs-lookup"><span data-stu-id="82558-116">After the last backup is restored, the database is recovered.</span></span>  
  
    ```  
    RESTORE LOG adb FROM log_backup1 WITH NORECOVERY;  
    RESTORE LOG adb FROM log_backup2 WITH NORECOVERY;  
    RESTORE LOG adb FROM log_backup3 WITH NORECOVERY;  
    RESTORE LOG adb WITH RECOVERY;  
    ```  
  
     <span data-ttu-id="82558-117">檔案 `a1` 現在已經在線上。</span><span class="sxs-lookup"><span data-stu-id="82558-117">File `a1` is now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="82558-118">其他範例</span><span class="sxs-lookup"><span data-stu-id="82558-118">Additional Examples</span></span>  
  
-   [<span data-ttu-id="82558-119">範例：分次還原資料庫 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="82558-119">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="82558-120">範例：僅限於部分檔案群組的分次還原 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="82558-120">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="82558-121">範例：線上還原唯讀檔案 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="82558-121">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="82558-122">範例：分次還原資料庫 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="82558-122">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="82558-123">範例：僅限於部分檔案群組的分次還原 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="82558-123">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="82558-124">範例：線上還原唯讀檔案 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="82558-124">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="82558-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82558-125">See Also</span></span>  
 <span data-ttu-id="82558-126">[線上還原 &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="82558-126">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="82558-127">[分次還原 &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="82558-127">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 <span data-ttu-id="82558-128">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="82558-128">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="82558-129">[還原和復原概觀 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="82558-129">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="82558-130">[套用交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="82558-130">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="82558-131">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="82558-131">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
