---
title: 部分備份 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full backups [SQL Server]
- partial backups [SQL Server]
- READ_WRITE_FILEGROUPS option
- database backups [SQL Server], about backing up databases
ms.assetid: fe6b6bb1-38d0-46c4-bab8-31df14e8999c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0c03cf2fb4d3af6fe87459e881e26c48cfacc232
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598480"
---
# <a name="partial-backups-sql-server"></a><span data-ttu-id="dad91-102">部分備份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="dad91-102">Partial Backups (SQL Server)</span></span>
  <span data-ttu-id="dad91-103">所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 復原模式皆支援部分備份，因此本主題與所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫都有關。</span><span class="sxs-lookup"><span data-stu-id="dad91-103">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recovery models support partial backups, so this topic is relevant for all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span> <span data-ttu-id="dad91-104">但是，部分備份設計為在簡單復原模式下用以改善備份超大型資料庫 (其中包含一個或多個唯讀檔案群組) 時的彈性。</span><span class="sxs-lookup"><span data-stu-id="dad91-104">However, partial backups are designed for use under the simple recovery model to improve flexibility for backing up very large databases that contain one or more read-only filegroups.</span></span>  
  
 <span data-ttu-id="dad91-105">每當您想要排除唯讀檔案群組時，部分備份就十分有用。</span><span class="sxs-lookup"><span data-stu-id="dad91-105">Partial backups are useful whenever you want to exclude read-only filegroups.</span></span> <span data-ttu-id="dad91-106">*「部分備份」* (Partial backup) 與完整資料庫備份類似，但部分備份不包含所有檔案群組。</span><span class="sxs-lookup"><span data-stu-id="dad91-106">A *partial backup* resembles a full database backup, but a partial backup does not contain all the filegroups.</span></span> <span data-ttu-id="dad91-107">然而，若為讀寫資料庫，則部分備份包含主要檔案群組、每個讀寫檔案群組，以及 (選擇性地) 一個或多個唯讀檔案中的資料。</span><span class="sxs-lookup"><span data-stu-id="dad91-107">Instead, for a read-write database, a partial backup contains the data in the primary filegroup, every read-write filegroup, and, optionally, one or more read-only files.</span></span> <span data-ttu-id="dad91-108">唯讀資料庫的部分備份只包含主要檔案群組。</span><span class="sxs-lookup"><span data-stu-id="dad91-108">A partial backup of a read-only database contains only the primary filegroup.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dad91-109">如果唯讀資料庫在部分備份之後變成可讀寫，可能有不在部分備份中的可讀寫次要檔案群組。</span><span class="sxs-lookup"><span data-stu-id="dad91-109">If a read-only database is changed to read/write after a partial backup, there might be read/write secondary filegroups that are not in the partial backup.</span></span> <span data-ttu-id="dad91-110">在此情況下，當您試圖進行差異部分備份時，備份會失敗。</span><span class="sxs-lookup"><span data-stu-id="dad91-110">In this case, if you try to take a differential partial backup, the backup fails.</span></span> <span data-ttu-id="dad91-111">您必須先進行另一個部分備份，才可以進行資料庫的差異部分備份。</span><span class="sxs-lookup"><span data-stu-id="dad91-111">Before you can take a differential partial backup of the database, you must take another partial backup.</span></span> <span data-ttu-id="dad91-112">新的部分備份會包含每個讀取/寫入次要檔案群組，並且可作為差異部分備份的基底。</span><span class="sxs-lookup"><span data-stu-id="dad91-112">The new partial backup contains every read/write secondary filegroup and can serve as the base for differential partial backups.</span></span>  
  
 <span data-ttu-id="dad91-113">唯讀檔案群組的檔案備份可以結合部分備份。</span><span class="sxs-lookup"><span data-stu-id="dad91-113">File backups of read-only filegroups can be combined with partial backups.</span></span> <span data-ttu-id="dad91-114">如需檔案備份的相關資訊，請參閱[完整檔案備份 &#40;SQL Server&#41;](full-file-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="dad91-114">For information about file backups, see [Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="dad91-115">部分備份可以當成差異部分備份的 *「差異基底」* (Differential base)。</span><span class="sxs-lookup"><span data-stu-id="dad91-115">A partial backup can serve as the *differential base* for differential partial backups.</span></span> <span data-ttu-id="dad91-116">如需詳細資訊，請參閱 [差異備份 &#40;SQL Server&#41;](differential-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="dad91-116">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="dad91-117">相關工作</span><span class="sxs-lookup"><span data-stu-id="dad91-117">Related Tasks</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dad91-118">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [維護計畫精靈] 不支援部分備份。</span><span class="sxs-lookup"><span data-stu-id="dad91-118">Partial backups are not supported by [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or the Maintenance Plan Wizard.</span></span>  
  
 <span data-ttu-id="dad91-119">**建立部分備份**</span><span class="sxs-lookup"><span data-stu-id="dad91-119">**To create a partial backup**</span></span>  
  
-   <span data-ttu-id="dad91-120">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (READ_WRITE_FILEGROUPS; FILEGROUP 選項，如有需要)</span><span class="sxs-lookup"><span data-stu-id="dad91-120">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (READ_WRITE_FILEGROUPS; FILEGROUP option, if needed)</span></span>  
  
 <span data-ttu-id="dad91-121">**在還原順序中使用部分備份**</span><span class="sxs-lookup"><span data-stu-id="dad91-121">**To use a partial backup in a restore sequence**</span></span>  
  
-   [<span data-ttu-id="dad91-122">範例：分次還原資料庫 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="dad91-122">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="dad91-123">範例：僅限於部分檔案群組的分次還原 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="dad91-123">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="dad91-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dad91-124">See Also</span></span>  
 <span data-ttu-id="dad91-125">[備份概觀 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="dad91-125">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="dad91-126">[檔案還原 &#40;簡單復原模式&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="dad91-126">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 [<span data-ttu-id="dad91-127">分次還原 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="dad91-127">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
