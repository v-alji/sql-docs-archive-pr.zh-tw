---
title: 分次還原具有記憶體最佳化資料表的資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 732c9721-8dd4-481d-8ff9-1feaaa63f84f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ed23f08d40e23b1d43c1b642f4089fe77646b675
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706493"
---
# <a name="piecemeal-restore-of-databases-with-memory-optimized-tables"></a><span data-ttu-id="19d72-102">分次還原具有記憶體最佳化資料表的資料庫</span><span class="sxs-lookup"><span data-stu-id="19d72-102">Piecemeal Restore of Databases With Memory-Optimized Tables</span></span>
  <span data-ttu-id="19d72-103">具有記憶體最佳化資料表的資料庫支援分次還原，但受到下列一項限制。</span><span class="sxs-lookup"><span data-stu-id="19d72-103">Piecemeal restore is supported on databases with memory-optimized tables except for one restriction described below.</span></span> <span data-ttu-id="19d72-104">如需分次備份和還原的詳細資訊，請參閱 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) 和[分次還原 &#40;SQL Server&#41;](../backup-restore/piecemeal-restores-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="19d72-104">For more information about piecemeal backup and restore, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) and [Piecemeal Restores &#40;SQL Server&#41;](../backup-restore/piecemeal-restores-sql-server.md).</span></span>  
  
 <span data-ttu-id="19d72-105">記憶體最佳化的檔案群組必須與主要檔案群組同時備份和還原：</span><span class="sxs-lookup"><span data-stu-id="19d72-105">A memory-optimized filegroup must be backed up and restored together with the primary filegroup:</span></span>  
  
-   <span data-ttu-id="19d72-106">如果您備份 (或還原) 主要檔案群組，您必須指定記憶體最佳化的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="19d72-106">If you back up (or restore) the primary filegroup you must specify the memory-optimized filegroup.</span></span>  
  
-   <span data-ttu-id="19d72-107">如果您備份 (或還原) 記憶體最佳化的檔案群組，您必須指定主要檔案群組。</span><span class="sxs-lookup"><span data-stu-id="19d72-107">If you backup (or restore) the memory-optimized filegroup you must specify the primary filegroup.</span></span>  
  
 <span data-ttu-id="19d72-108">分次備份和還原的主要狀況包括：</span><span class="sxs-lookup"><span data-stu-id="19d72-108">Key scenarios for piecemeal backup and restore are,</span></span>  
  
-   <span data-ttu-id="19d72-109">分次備份可縮小備份大小。</span><span class="sxs-lookup"><span data-stu-id="19d72-109">Piecemeal backup allows you to reduce the size of backup.</span></span> <span data-ttu-id="19d72-110">以下是一些範例：</span><span class="sxs-lookup"><span data-stu-id="19d72-110">Some examples:</span></span>  
  
    -   <span data-ttu-id="19d72-111">設定在不同的時間或日期進行資料庫備份，可降低對工作負載的影響。</span><span class="sxs-lookup"><span data-stu-id="19d72-111">Configure the database backup to occur at different times or days to minimize the impact on the workload.</span></span> <span data-ttu-id="19d72-112">例如，非常大型的資料庫 (大於 1 TB) 無法在配置給資料庫維護的時間內完成完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="19d72-112">One example is a very large database (greater than 1 TB) where a full database backup cannot complete in the time allocated for database maintenance.</span></span> <span data-ttu-id="19d72-113">在此情況下，您可以使用分次備份將整個資料庫分成多次備份。</span><span class="sxs-lookup"><span data-stu-id="19d72-113">In that situation, you can use piecemeal backup to backup the full database in multiple piecemeal backups.</span></span>  
  
    -   <span data-ttu-id="19d72-114">如果檔案群組標示為唯讀，在標示為唯讀之後，便不需要交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="19d72-114">If a filegroup is marked read-only, it does not require a transaction log backup after it was marked read-only.</span></span> <span data-ttu-id="19d72-115">您可以選擇在標示為唯讀之後只備份檔案群組一次。</span><span class="sxs-lookup"><span data-stu-id="19d72-115">You can choose to back up the filegroup only once after marking it read-only.</span></span>  
  
-   <span data-ttu-id="19d72-116">分次還原。</span><span class="sxs-lookup"><span data-stu-id="19d72-116">Piecemeal restore.</span></span>  
  
    -   <span data-ttu-id="19d72-117">分次還原的目標是要讓資料庫的重要部分恢復連線狀態，而不需要等候所有資料。</span><span class="sxs-lookup"><span data-stu-id="19d72-117">The goal of a piecemeal restore is to bring the critical parts of database online without waiting for all the data.</span></span> <span data-ttu-id="19d72-118">例如，如果資料庫具有分割資料，會很少使用這類舊的分割區。</span><span class="sxs-lookup"><span data-stu-id="19d72-118">One example is if a database has partitioned data, such that older partitions are only used rarely.</span></span> <span data-ttu-id="19d72-119">您可以僅在必要時才進行還原。</span><span class="sxs-lookup"><span data-stu-id="19d72-119">You can restore them only on an as-needed basis.</span></span> <span data-ttu-id="19d72-120">類似的範例為包含歷程記錄資料的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="19d72-120">Similar for filegroups that contain, for example, historical data.</span></span>  
  
    -   <span data-ttu-id="19d72-121">透過頁面修復，您可以還原特定頁面來修正損毀的頁面。</span><span class="sxs-lookup"><span data-stu-id="19d72-121">Using page repair, you can fix page corruption by specifically restoring the page.</span></span> <span data-ttu-id="19d72-122">如需詳細資訊，請參閱[還原頁面 &#40;SQL Server&#41;](../backup-restore/restore-pages-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="19d72-122">For more information, see [Restore Pages &#40;SQL Server&#41;](../backup-restore/restore-pages-sql-server.md).</span></span>  
  
## <a name="samples"></a><span data-ttu-id="19d72-123">範例</span><span class="sxs-lookup"><span data-stu-id="19d72-123">Samples</span></span>  
 <span data-ttu-id="19d72-124">這些範例使用下列結構描述：</span><span class="sxs-lookup"><span data-stu-id="19d72-124">The examples use the following schema:</span></span>  
  
```  
CREATE DATABASE imoltp  
ON PRIMARY (name = imoltp_primary1, filename = 'c:\data\imoltp_data1.mdf')  
LOG ON (name = imoltp_log, filename = 'c:\data\imoltp_log.ldf')  
GO  
  
ALTER DATABASE imoltp ADD FILE (name = imoltp_primary2, filename = 'c:\data\imoltp_data2.ndf')  
GO  
  
ALTER DATABASE imoltp ADD FILEGROUP imoltp_secondary  
ALTER DATABASE imoltp ADD FILE (name = imoltp_secondary, filename = 'c:\data\imoltp_secondary.ndf') TO FILEGROUP imoltp_secondary  
GO  
  
ALTER DATABASE imoltp ADD FILEGROUP imoltp_mod CONTAINS MEMORY_OPTIMIZED_DATA   
ALTER DATABASE imoltp ADD FILE (name='imoltp_mod1', filename='c:\data\imoltp_mod1') TO FILEGROUP imoltp_mod   
ALTER DATABASE imoltp ADD FILE (name='imoltp_mod2', filename='c:\data\imoltp_mod2') TO FILEGROUP imoltp_mod   
GO  
```  
  
### <a name="backup"></a><span data-ttu-id="19d72-125">Backup</span><span class="sxs-lookup"><span data-stu-id="19d72-125">Backup</span></span>  
 <span data-ttu-id="19d72-126">此範例顯示如何備份主要檔案群組和記憶體最佳化的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="19d72-126">This sample shows how to backup the primary filegroup and the memory-optimized filegroup.</span></span> <span data-ttu-id="19d72-127">您必須同時指定主要檔案群組和記憶體最佳化的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="19d72-127">You must specify both primary and memory-optimized filegroup together.</span></span>  
  
```  
backup database imoltp filegroup='primary', filegroup='imoltp_mod' to disk='c:\data\imoltp.dmp' with init  
```  
  
 <span data-ttu-id="19d72-128">下列範例顯示備份主要檔案群組和記憶體最佳化的檔案群組之外的檔案群組，類似於備份不具有記憶體最佳化資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="19d72-128">The following sample shows that a back up of filegroup(s) other than primary and memory-optimized filegroup works similar to the databases without memory-optimized tables.</span></span> <span data-ttu-id="19d72-129">下列命令備份次要檔案群組</span><span class="sxs-lookup"><span data-stu-id="19d72-129">The following command backups up the secondary filegroup</span></span>  
  
```  
backup database imoltp filegroup='imoltp_secondary' to disk='c:\data\imoltp_secondary.dmp' with init  
```  
  
### <a name="restore"></a><span data-ttu-id="19d72-130">還原</span><span class="sxs-lookup"><span data-stu-id="19d72-130">Restore</span></span>  
 <span data-ttu-id="19d72-131">下列範例顯示如何同時還原主要檔案群組和記憶體最佳化的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="19d72-131">The following sample shows how to restore the primary filegroup and memory-optimized filegroup together.</span></span>  
  
```  
restore database imoltp filegroup = 'primary', filegroup = 'imoltp_mod'   
from disk='c:\data\imoltp.dmp' with partial, norecovery  
  
--restore the transaction log  
 RESTORE LOG [imoltp] FROM DISK = N'c:\data\imoltp_log.dmp' WITH  FILE = 1,  NOUNLOAD,  STATS = 10  
GO  
```  
  
 <span data-ttu-id="19d72-132">下一個範例顯示還原主要檔案群組和記憶體最佳化的檔案群組之外的檔案群組，類似於還原不具有記憶體最佳化資料表的資料庫</span><span class="sxs-lookup"><span data-stu-id="19d72-132">The next sample shows that restoring filegroup(s) other than the primary and memory-optimized filegroup works similar to the databases without memory-optimized tables</span></span>  
  
```  
RESTORE DATABASE [imoltp] FILE = N'imoltp_secondary'   
FROM  DISK = N'c:\data\imoltp_secondary.dmp' WITH  FILE = 1,  RECOVERY,  NOUNLOAD,  STATS = 10  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="19d72-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19d72-133">See Also</span></span>  
 [<span data-ttu-id="19d72-134">備份、還原及復原記憶體最佳化資料表</span><span class="sxs-lookup"><span data-stu-id="19d72-134">Backup, Restore, and Recovery of Memory-Optimized Tables</span></span>](../../database-engine/backup-restore-and-recovery-of-memory-optimized-tables.md)  
  
  
