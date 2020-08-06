---
title: 範例：線上還原唯讀檔案 (完整復原模式) | Microsoft Docs
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
ms.assetid: 7ea2d2af-086f-48dc-9636-38dc194c7090
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f493c88d64e6ed22e44f33f1442ae581daa8ed4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709686"
---
# <a name="example-online-restore-of-a-read-only-file-full-recovery-model"></a><span data-ttu-id="2de54-102">範例：線上還原讀取/寫入檔案 (完整復原模式)</span><span class="sxs-lookup"><span data-stu-id="2de54-102">Example: Online Restore of a Read-Only File (Full Recovery Model)</span></span>
  <span data-ttu-id="2de54-103">本主題是關於在完整復原模式下，包含多個檔案或檔案群組的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="2de54-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases under the full recovery model that contain multiple files or filegroups.</span></span>  
  
 <span data-ttu-id="2de54-104">這個範例當中，使用完整復原模式，名為 `adb`的資料庫包含三個檔案群組。</span><span class="sxs-lookup"><span data-stu-id="2de54-104">In this example, a database named `adb`, which uses the full recovery model, contains three filegroups.</span></span> <span data-ttu-id="2de54-105">檔案群組 `A` 可讀取/寫入，而檔案群組 `B` 和檔案群組 `C` 則是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="2de54-105">Filegroup `A` is read/write, and filegroup `B` and filegroup `C` are read-only.</span></span> <span data-ttu-id="2de54-106">所有的檔案群組一開始都是在線上。</span><span class="sxs-lookup"><span data-stu-id="2de54-106">Initially, all of the filegroups are online.</span></span>  
  
 <span data-ttu-id="2de54-107">在資料庫 `b1`的檔案群組 `B` 中，需要還原唯讀檔案 `adb` 。</span><span class="sxs-lookup"><span data-stu-id="2de54-107">A read-only file, `b1`, in filegroup `B` of database `adb` has to be restored.</span></span> <span data-ttu-id="2de54-108">自從檔案變成唯讀之後已經進行過備份，因此不需要記錄備份。</span><span class="sxs-lookup"><span data-stu-id="2de54-108">A backup was taken since the file became read-only; therefore, log backups are not required.</span></span> <span data-ttu-id="2de54-109">在還原期間，檔案群組 `B` 會離線，但資料庫的其餘部分仍在線上。</span><span class="sxs-lookup"><span data-stu-id="2de54-109">Filegroup `B` is offline for the duration of the restore, but the remainder of the database remains online.</span></span>  
  
## <a name="restore-sequence"></a><span data-ttu-id="2de54-110">還原順序</span><span class="sxs-lookup"><span data-stu-id="2de54-110">Restore Sequence</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2de54-111">線上還原順序的語法和離線還原順序的語法相同。</span><span class="sxs-lookup"><span data-stu-id="2de54-111">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
 <span data-ttu-id="2de54-112">為還原檔案，資料庫管理員會使用下列還原順序：</span><span class="sxs-lookup"><span data-stu-id="2de54-112">To restore the file, the database administrator uses the following restore sequence:</span></span>  
  
```  
RESTORE DATABASE adb FILE='b1' FROM filegroup_B_backup  
WITH RECOVERY   
```  
  
 <span data-ttu-id="2de54-113">檔案群組 B 現在已經在線上。</span><span class="sxs-lookup"><span data-stu-id="2de54-113">Filegroup B is now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="2de54-114">其他範例</span><span class="sxs-lookup"><span data-stu-id="2de54-114">Additional Examples</span></span>  
  
-   [<span data-ttu-id="2de54-115">範例：分次還原資料庫 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="2de54-115">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="2de54-116">範例：僅限於部分檔案群組的分次還原 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="2de54-116">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="2de54-117">範例：線上還原唯讀檔案 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="2de54-117">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="2de54-118">範例：分次還原資料庫 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="2de54-118">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="2de54-119">範例：僅限於部分檔案群組的分次還原 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="2de54-119">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="2de54-120">範例：線上還原讀取/寫入檔案 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="2de54-120">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="2de54-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2de54-121">See Also</span></span>  
 <span data-ttu-id="2de54-122">[線上還原 &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2de54-122">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="2de54-123">[還原和復原概觀 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2de54-123">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="2de54-124">[檔案還原 &#40;完整復原模式&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="2de54-124">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 [<span data-ttu-id="2de54-125">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2de54-125">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
