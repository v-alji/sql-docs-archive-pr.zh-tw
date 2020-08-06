---
title: 範例：線上還原唯讀檔案 (簡單復原模式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restore sequences [SQL Server], online
- online restores [SQL Server], simple recovery model
- simple recovery model [SQL Server], RESTORE examples
ms.assetid: 0c691fc6-9865-46a7-b055-8097424492d6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d84c920a2cb40866ba106b4d30d8e24c4caea611
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709685"
---
# <a name="example-online-restore-of-a-read-only-file-simple-recovery-model"></a><span data-ttu-id="36f26-102">範例：線上還原讀取/寫入檔案 (簡單復原模式)</span><span class="sxs-lookup"><span data-stu-id="36f26-102">Example: Online Restore of a Read-Only File (Simple Recovery Model)</span></span>
  <span data-ttu-id="36f26-103">本主題是關於在簡單復原模式下，包含唯讀檔案群組的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="36f26-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases under the simple recovery model that contain a read-only filegroup.</span></span> <span data-ttu-id="36f26-104">在簡單復原模式下，如果有檔案成為唯讀後保留的備份檔案，就可以線上還原唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="36f26-104">Under the simple recovery model, a read-only file can be restored online if a file backup exists that was taken since the file became read-only for the last time.</span></span>  
  
 <span data-ttu-id="36f26-105">在此範例中，名為 `adb` 的資料庫包含三個檔案群組。</span><span class="sxs-lookup"><span data-stu-id="36f26-105">In this example, a database named `adb` contains three filegroups.</span></span> <span data-ttu-id="36f26-106">檔案群組 `A` 可讀取/寫入，而檔案群組 `B` 和 `C` 則是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="36f26-106">Filegroup `A` is read/write, and filegroups `B` and `C` are read-only.</span></span> <span data-ttu-id="36f26-107">所有的檔案群組一開始都是在線上。</span><span class="sxs-lookup"><span data-stu-id="36f26-107">Initially, all of the filegroups are online.</span></span> <span data-ttu-id="36f26-108">在檔案群組 `B`中，必須還原的是唯讀檔案 `b1`。</span><span class="sxs-lookup"><span data-stu-id="36f26-108">A read-only file in filegroup `B`, `b1`, has to be restored.</span></span> <span data-ttu-id="36f26-109">資料庫管理員可以使用在檔案成為唯讀後保留的備份進行還原。</span><span class="sxs-lookup"><span data-stu-id="36f26-109">The database administrator can restore it by using a backup that was taken after the file became read-only.</span></span> <span data-ttu-id="36f26-110">檔案群組 `B` 在還原期間會處於離線，但資料庫的其他檔案群組仍會維持線上工作。</span><span class="sxs-lookup"><span data-stu-id="36f26-110">For the duration of the restore, filegroup `B` will be offline, but the remainder of the database will remain online.</span></span>  
  
## <a name="restore-sequence"></a><span data-ttu-id="36f26-111">還原順序</span><span class="sxs-lookup"><span data-stu-id="36f26-111">Restore Sequence</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="36f26-112">線上還原順序的語法和離線還原順序的語法相同。</span><span class="sxs-lookup"><span data-stu-id="36f26-112">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
 <span data-ttu-id="36f26-113">為還原檔案，資料庫管理員會使用下列還原順序：</span><span class="sxs-lookup"><span data-stu-id="36f26-113">To restore the file, the database administrator uses the following restore sequence:</span></span>  
  
```  
RESTORE DATABASE adb FILE='b1' FROM filegroup_B_backup   
WITH RECOVERY  
```  
  
 <span data-ttu-id="36f26-114">檔案現在已經在線上。</span><span class="sxs-lookup"><span data-stu-id="36f26-114">The file is now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="36f26-115">其他範例</span><span class="sxs-lookup"><span data-stu-id="36f26-115">Additional Examples</span></span>  
  
-   [<span data-ttu-id="36f26-116">範例：分次還原資料庫 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="36f26-116">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="36f26-117">範例：僅限於部分檔案群組的分次還原 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="36f26-117">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="36f26-118">範例：分次還原資料庫 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="36f26-118">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="36f26-119">範例：僅限於部分檔案群組的分次還原 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="36f26-119">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="36f26-120">範例：線上還原讀取/寫入檔案 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="36f26-120">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="36f26-121">範例：線上還原唯讀檔案 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="36f26-121">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="36f26-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36f26-122">See Also</span></span>  
 <span data-ttu-id="36f26-123">[線上還原 &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="36f26-123">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="36f26-124">[分次還原 &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="36f26-124">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 <span data-ttu-id="36f26-125">[檔案還原 &#40;簡單復原模式&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="36f26-125">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="36f26-126">[還原和復原概觀 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="36f26-126">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="36f26-127">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="36f26-127">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
