---
title: 範例：離線還原主要和另一個檔案群組 (完整復原模式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- offline restores [SQL Server]
- restore sequences [SQL Server], offline
ms.assetid: 7d6c50eb-dc84-4d66-855a-0b5f1bd89737
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6f845927fdd74fba476139fccbf9a5fa112d434e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599522"
---
# <a name="example-offline-restore-of-primary-and-one-other-filegroup-full-recovery-model"></a><span data-ttu-id="7e3a2-102">範例：離線還原主要檔案群組與另一個檔案群組 (完整復原模式)</span><span class="sxs-lookup"><span data-stu-id="7e3a2-102">Example: Offline Restore of Primary and One Other Filegroup (Full Recovery Model)</span></span>
  <span data-ttu-id="7e3a2-103">本主題僅與在完整復原模式下，包含多個檔案群組的資料庫有關。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-103">This topic is relevant only for databases under the full recovery model that contain multiple filegroups.</span></span>  
  
 <span data-ttu-id="7e3a2-104">在此範例中，名為 `adb` 的資料庫包含三個檔案群組。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-104">In this example, a database named `adb` contains three filegroups.</span></span> <span data-ttu-id="7e3a2-105">檔案群組 `A` 和 `C` 可讀取/寫入，而檔案群組 `B` 則是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-105">Filegroups `A` and `C` are read/write, and filegroup `B` is read-only.</span></span> <span data-ttu-id="7e3a2-106">主要檔案群組和檔案群組 `B` 損毀，但檔案群組 `A` 和 `C` 完整無缺。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-106">The primary filegroup and filegroup `B` are damaged, but filegroups `A` and `C` are intact.</span></span> <span data-ttu-id="7e3a2-107">在損毀之前，所有檔案群組都在線上。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-107">Before the disaster, all the filegroups were online.</span></span>  
  
 <span data-ttu-id="7e3a2-108">資料庫管理員決定還原並復原主要檔案群組和檔案群組 `B`。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-108">The database administrator decides to restore and recover the primary filegroup and filegroup `B`.</span></span> <span data-ttu-id="7e3a2-109">資料庫使用完整復原模式，因此開始還原之前，必須對資料庫進行結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-109">The database is using the full recovery model; therefore, before the restore starts, a tail-log backup must be taken of the database.</span></span> <span data-ttu-id="7e3a2-110">當資料庫上線時，檔案群組 `A` 和 `C` 會自動回到線上。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-110">When the database comes on line, Filegroups `A` and `C` are automatically brought online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7e3a2-111">離線還原順序的步驟比唯讀檔案的線上還原步驟少。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-111">The offline restore sequence has fewer steps than an online restore of a read-only file.</span></span> <span data-ttu-id="7e3a2-112">如需範例，請參閱[範例：線上還原唯讀檔案 &#40;完整復原模式&#41;](example-online-restore-of-a-read-only-file-full-recovery-model.md)。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-112">For an example, see [Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;](example-online-restore-of-a-read-only-file-full-recovery-model.md).</span></span> <span data-ttu-id="7e3a2-113">但是在還原順序期間，整個資料庫都會離線。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-113">However, the whole database is offline for the duration of the sequence.</span></span>  
  
## <a name="tail-log-backup"></a><span data-ttu-id="7e3a2-114">結尾記錄備份</span><span class="sxs-lookup"><span data-stu-id="7e3a2-114">Tail-Log Backup</span></span>  
 <span data-ttu-id="7e3a2-115">還原資料庫之前，資料庫管理員必須備份記錄的結尾。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-115">Before restoring the database, the database administrator must back up the tail of the log.</span></span> <span data-ttu-id="7e3a2-116">因為資料庫已損毀，必須使用 NO_TRUNCATE 選項來建立結尾記錄備份：</span><span class="sxs-lookup"><span data-stu-id="7e3a2-116">Because the database is damaged, creating the tail-log backup requires using the NO_TRUNCATE option:</span></span>  
  
```  
BACKUP LOG adb TO tailLogBackup   
   WITH NORECOVERY, NO_TRUNCATE  
```  
  
 <span data-ttu-id="7e3a2-117">結尾記錄備份是下列還原順序中套用的最後一個備份。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-117">The tail-log backup is the last backup that is applied in the following restore sequences.</span></span>  
  
## <a name="restore-sequence"></a><span data-ttu-id="7e3a2-118">還原順序</span><span class="sxs-lookup"><span data-stu-id="7e3a2-118">Restore Sequence</span></span>  
 <span data-ttu-id="7e3a2-119">為了還原主要檔案群組和檔案群組 `B`，資料庫管理員會使用不含 PARTIAL 選項的還原順序，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7e3a2-119">To restore the primary filegroup and filegroup `B`, the database administrator uses a restore sequence without the PARTIAL option, as follows:</span></span>  
  
```  
RESTORE DATABASE adb FILEGROUP='Primary' FROM backup1   
WITH NORECOVERY  
RESTORE DATABASE adb FILEGROUP='B' FROM backup2   
WITH NORECOVERY  
RESTORE LOG adb FROM backup3 WITH NORECOVERY  
RESTORE LOG adb FROM backup4 WITH NORECOVERY  
RESTORE LOG adb FROM backup5 WITH NORECOVERY  
RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
```  
  
 <span data-ttu-id="7e3a2-120">未還原的檔案會自動回到線上。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-120">The files that are not restored are automatically brought online.</span></span> <span data-ttu-id="7e3a2-121">接著，所有檔案群組都會回到線上狀態。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-121">All the filegroups are now online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e3a2-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e3a2-122">See Also</span></span>  
 <span data-ttu-id="7e3a2-123">[線上還原 &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7e3a2-123">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="7e3a2-124">[分次還原 &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7e3a2-124">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 <span data-ttu-id="7e3a2-125">[檔案還原 &#40;完整復原模式&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="7e3a2-125">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="7e3a2-126">[套用交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7e3a2-126">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="7e3a2-127">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7e3a2-127">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
