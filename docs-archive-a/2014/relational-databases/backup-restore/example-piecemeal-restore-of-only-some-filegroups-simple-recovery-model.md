---
title: 範例：僅限於某些檔案群組的分次還原 (簡單復原模式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- piecemeal restores [SQL Server], simple recovery model
- restore sequences [SQL Server], piecemeal
- simple recovery model [SQL Server], RESTORE examples
ms.assetid: d7ad026c-5355-4308-9560-0dc843940d4f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8254ac96a269b6fb433759e5a649bf9df1b7feac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709677"
---
# <a name="example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model"></a><span data-ttu-id="857b2-102">範例：僅對部分檔案群組分次還原 (簡單復原模式)</span><span class="sxs-lookup"><span data-stu-id="857b2-102">Example: Piecemeal Restore of Only Some Filegroups (Simple Recovery Model)</span></span>
  <span data-ttu-id="857b2-103">本主題是關於在簡單復原模式下，包含唯讀檔案群組的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="857b2-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases under the simple recovery model that contain a read-only filegroup.</span></span>  
  
 <span data-ttu-id="857b2-104">分次還原順序會在檔案群組層級，分階段地還原與復原資料庫，先從主要檔案群組開始，然後才是所有的讀取/寫入次要檔案群組。</span><span class="sxs-lookup"><span data-stu-id="857b2-104">A piecemeal restore sequence restores and recovers a database in stages at the filegroup level, beginning with the primary and all read/write, secondary filegroups.</span></span>  
  
 <span data-ttu-id="857b2-105">這個範例當中，使用簡單復原模式，名為 `adb`的資料庫包含三個檔案群組。</span><span class="sxs-lookup"><span data-stu-id="857b2-105">In this example, a database named `adb`, which uses the simple recovery model, contains three filegroups.</span></span> <span data-ttu-id="857b2-106">檔案群組 `A` 可讀取/寫入，而檔案群組 `B` 和檔案群組 `C` 則是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="857b2-106">Filegroup `A` is read/write, and filegroup `B` and filegroup `C` are read-only.</span></span> <span data-ttu-id="857b2-107">所有的檔案群組一開始都是在線上。</span><span class="sxs-lookup"><span data-stu-id="857b2-107">Initially, all of the filegroups are online.</span></span>  
  
 <span data-ttu-id="857b2-108">資料庫 `B` 的主要和檔案群組 `adb` 似乎已損毀，所以資料庫管理員決定使用分次還原順序來進行還原。</span><span class="sxs-lookup"><span data-stu-id="857b2-108">The primary and filegroup `B` of database `adb` appear to be damaged; therefore, the database administrator decides to restore them by using a piecemeal restore sequence.</span></span> <span data-ttu-id="857b2-109">在簡單復原模式下，必須從相同的部分備份中還原所有的讀取/寫入檔案群組。</span><span class="sxs-lookup"><span data-stu-id="857b2-109">Under the simple recovery model, all read/write filegroups must be restored from the same partial backup.</span></span> <span data-ttu-id="857b2-110">雖然檔案群組 `A` 完整無缺，但還是必須隨主要檔案群組一起還原，才能確定它們是一致的 (資料庫將會還原到最後一個部分備份結尾所定義的時間點)。</span><span class="sxs-lookup"><span data-stu-id="857b2-110">Although filegroup `A` is intact, it must be restored with the primary filegroup to make sure that they are consistent (the database will be restored to the point in time defined by the end of the last partial backup).</span></span> <span data-ttu-id="857b2-111">檔案群組 `C` 完整未受損，但仍然必須加以復原，才能回到線上。</span><span class="sxs-lookup"><span data-stu-id="857b2-111">Filegroup `C` is intact, but it must be recovered to bring it online.</span></span> <span data-ttu-id="857b2-112">檔案群組 `B`雖然受損，但是包含的資料不比檔案群組 `C`的資料來得重要，因此會在最後才還原 `B` 。</span><span class="sxs-lookup"><span data-stu-id="857b2-112">Filegroup `B`, although damaged, contains less critical data than Filegroup `C`; therefore, `B` will be restored last.</span></span>  
  
## <a name="restore-sequences"></a><span data-ttu-id="857b2-113">還原順序</span><span class="sxs-lookup"><span data-stu-id="857b2-113">Restore Sequences</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="857b2-114">線上還原順序的語法和離線還原順序的語法相同。</span><span class="sxs-lookup"><span data-stu-id="857b2-114">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
1.  <span data-ttu-id="857b2-115">從部分備份中部分還原主要檔案群組和檔案群組 `A` 。</span><span class="sxs-lookup"><span data-stu-id="857b2-115">Partial restore of the primary and filegroup `A` from a partial backup.</span></span>  
  
    ```  
    RESTORE DATABASE adb READ_WRITE_FILEGROUPS FROM partial_backup   
    WITH PARTIAL, RECOVERY  
    ```  
  
     <span data-ttu-id="857b2-116">此時，主要檔案群組和檔案群組 `A` 是在線上。</span><span class="sxs-lookup"><span data-stu-id="857b2-116">At this point the primary filegroup and filegroup `A` are online.</span></span> <span data-ttu-id="857b2-117">檔案群組 `B` 和 `C` 中的檔案皆為復原暫止狀態，且檔案群組已離線。</span><span class="sxs-lookup"><span data-stu-id="857b2-117">Files in filegroups `B` and `C` are recovery pending, and the filegroups are offline.</span></span>  
  
2.  <span data-ttu-id="857b2-118">線上復原檔案群組 `C`。</span><span class="sxs-lookup"><span data-stu-id="857b2-118">Online recovery of filegroup `C`.</span></span>  
  
     <span data-ttu-id="857b2-119">檔案群組 `C` 會是一致的，因為以上所還原的部分備份是在檔案群 `C` 變成唯讀之後才建立的，即使資料庫被還原到了過去的時間點。</span><span class="sxs-lookup"><span data-stu-id="857b2-119">Filegroup `C` is consistent because the partial backup that was restored above was taken after filegroup `C` became read-only, although the database was taken back in time by the restore.</span></span> <span data-ttu-id="857b2-120">資料庫管理員只是復原檔案群組 `C`使其回到線上，並未加以還原。</span><span class="sxs-lookup"><span data-stu-id="857b2-120">The database administrator recovers the filegroup `C`, without restoring it, to bring it online.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='C' WITH RECOVERY  
    ```  
  
     <span data-ttu-id="857b2-121">此時，主要與次要檔案群組 `A` 和 `C` 會在線上。</span><span class="sxs-lookup"><span data-stu-id="857b2-121">At this point the primary and filegroups `A` and `C` are online.</span></span> <span data-ttu-id="857b2-122">FilegroupB 裡的檔案會保持復原暫止，而檔案群組為離線。</span><span class="sxs-lookup"><span data-stu-id="857b2-122">Files in filegroupB remain recovery pending, with the filegroup offline.</span></span>  
  
3.  <span data-ttu-id="857b2-123">線上還原檔案群組。 `B.`</span><span class="sxs-lookup"><span data-stu-id="857b2-123">Online restore of filegroup `B.`</span></span>  
  
     <span data-ttu-id="857b2-124">檔案群組 `B` 中的檔案必須加以還原。</span><span class="sxs-lookup"><span data-stu-id="857b2-124">Files in filegroup `B` must be restored.</span></span> <span data-ttu-id="857b2-125">資料庫管理員所還原的檔案群組 `B` 備份，是在檔案群組 `B` 變成唯讀之後及部分備份之前所建立的。</span><span class="sxs-lookup"><span data-stu-id="857b2-125">The database administrator restores the backup of filegroup `B` taken after filegroup `B` became read-only and before the partial backup.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup   
    WITH RECOVERY  
    ```  
  
     <span data-ttu-id="857b2-126">所有檔案群組現在都已在線上。</span><span class="sxs-lookup"><span data-stu-id="857b2-126">All filegroups are now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="857b2-127">其他範例</span><span class="sxs-lookup"><span data-stu-id="857b2-127">Additional Examples</span></span>  
  
-   [<span data-ttu-id="857b2-128">範例：分次還原資料庫 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="857b2-128">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="857b2-129">範例：線上還原唯讀檔案 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="857b2-129">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="857b2-130">範例：分次還原資料庫 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="857b2-130">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="857b2-131">範例：僅限於部分檔案群組的分次還原 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="857b2-131">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="857b2-132">範例：線上還原讀取/寫入檔案 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="857b2-132">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="857b2-133">範例：線上還原唯讀檔案 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="857b2-133">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="857b2-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="857b2-134">See Also</span></span>  
 <span data-ttu-id="857b2-135">[線上還原 &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="857b2-135">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="857b2-136">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="857b2-136">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="857b2-137">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="857b2-137">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="857b2-138">分次還原 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="857b2-138">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
