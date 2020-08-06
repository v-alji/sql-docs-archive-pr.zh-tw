---
title: 範例：分次還原資料庫 (簡單復原模式) | Microsoft Docs
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
ms.assetid: 9834b14a-4e56-4654-b190-c2a38624b6b4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 69de84fa2ff3a853eb9926549ad4859d2f1ae38e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704205"
---
# <a name="example-piecemeal-restore-of-database-simple-recovery-model"></a><span data-ttu-id="5a7ca-102">範例：分次還原資料庫 (簡單復原模式)</span><span class="sxs-lookup"><span data-stu-id="5a7ca-102">Example: Piecemeal Restore of Database (Simple Recovery Model)</span></span>
  <span data-ttu-id="5a7ca-103">分次還原順序會在檔案群組層級，分階段地還原與復原資料庫，先從主要檔案群組開始，然後才是所有的讀取/寫入次要檔案群組。</span><span class="sxs-lookup"><span data-stu-id="5a7ca-103">A piecemeal restore sequence restores and recovers a database in stages at the filegroup level, starting with the primary and all read/write, secondary filegroups.</span></span>  
  
 <span data-ttu-id="5a7ca-104">在此範例中，資料庫 `adb` 是在損毀之後還原至新的電腦。</span><span class="sxs-lookup"><span data-stu-id="5a7ca-104">In this example, database `adb` is restored to a new computer after a disaster.</span></span> <span data-ttu-id="5a7ca-105">此資料庫使用的是簡單復原模式。</span><span class="sxs-lookup"><span data-stu-id="5a7ca-105">The database is using the simple recovery model.</span></span> <span data-ttu-id="5a7ca-106">在損毀之前，所有檔案群組都在線上。</span><span class="sxs-lookup"><span data-stu-id="5a7ca-106">Before the disaster, all the filegroups are online.</span></span> <span data-ttu-id="5a7ca-107">檔案群組 `A` 和 `C` 可讀取/寫入，而檔案群組 `B` 則是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="5a7ca-107">Filegroups `A` and `C` are read/write, and filegroup `B` is read-only.</span></span> <span data-ttu-id="5a7ca-108">檔案群組 `B` 在最近一次部分備份之前變成唯讀，該部分備份包含主要檔案群組以及讀取/寫入次要檔案群組 `A` 和 `C`。</span><span class="sxs-lookup"><span data-stu-id="5a7ca-108">Filegroup `B` became read-only before the most recent partial backup, which contains the primary filegroup and the read/write secondary filegroups, `A` and `C`.</span></span> <span data-ttu-id="5a7ca-109">在檔案群組 `B` 變成唯讀之後，對檔案群組 `B` 進行了個別的檔案備份。</span><span class="sxs-lookup"><span data-stu-id="5a7ca-109">After filegroup `B` became read-only, a separate file backup of filegroup `B` was taken.</span></span>  
  
## <a name="restore-sequences"></a><span data-ttu-id="5a7ca-110">還原順序</span><span class="sxs-lookup"><span data-stu-id="5a7ca-110">Restore Sequences</span></span>  
  
1.  <span data-ttu-id="5a7ca-111">主要檔案群組和檔案群組 `A` 和 `C`的部分還原。</span><span class="sxs-lookup"><span data-stu-id="5a7ca-111">Partial restore of the primary and filegroups `A` and `C`.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='A',FILEGROUP='C'   
       FROM partial_backup   
       WITH PARTIAL, RECOVERY;  
  
    ```  
  
     <span data-ttu-id="5a7ca-112">此時，主要檔案群組和檔案群組 `A` 和 `C` 在線上。</span><span class="sxs-lookup"><span data-stu-id="5a7ca-112">At this point, the primary and filegroups `A` and `C` are online.</span></span> <span data-ttu-id="5a7ca-113">檔案群組 `B` 中的所有檔案皆為復原暫止狀態，且檔案群組已離線。</span><span class="sxs-lookup"><span data-stu-id="5a7ca-113">All files in filegroup `B` are recovery pending, and the filegroup is offline.</span></span>  
  
2.  <span data-ttu-id="5a7ca-114">線上還原檔案群組 `B`。</span><span class="sxs-lookup"><span data-stu-id="5a7ca-114">Online restore of filegroup `B`.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup WITH RECOVERY;  
  
    ```  
  
     <span data-ttu-id="5a7ca-115">所有檔案群組現在都已在線上。</span><span class="sxs-lookup"><span data-stu-id="5a7ca-115">All filegroups are now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="5a7ca-116">其他範例</span><span class="sxs-lookup"><span data-stu-id="5a7ca-116">Additional Examples</span></span>  
  
-   [<span data-ttu-id="5a7ca-117">範例：僅限於部分檔案群組的分次還原 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="5a7ca-117">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="5a7ca-118">範例：線上還原唯讀檔案 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="5a7ca-118">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="5a7ca-119">範例：分次還原資料庫 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="5a7ca-119">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="5a7ca-120">範例：僅限於部分檔案群組的分次還原 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="5a7ca-120">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="5a7ca-121">範例：線上還原讀取/寫入檔案 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="5a7ca-121">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="5a7ca-122">範例：線上還原唯讀檔案 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="5a7ca-122">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="5a7ca-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a7ca-123">See Also</span></span>  
 <span data-ttu-id="5a7ca-124">[線上還原 &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5a7ca-124">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="5a7ca-125">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5a7ca-125">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="5a7ca-126">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5a7ca-126">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="5a7ca-127">分次還原 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5a7ca-127">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
