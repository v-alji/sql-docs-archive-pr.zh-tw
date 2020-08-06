---
title: 備份含有記憶體最佳化資料表的資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 83d47694-e56d-4dae-b54e-14945bf8ba31
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 176448aa9d4bab4101ab2db12ffc9a8a7fd1a5b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592006"
---
# <a name="backing-up-a-database-with-memory-optimized-tables"></a><span data-ttu-id="98f87-102">備份含有記憶體最佳化資料表的資料庫</span><span class="sxs-lookup"><span data-stu-id="98f87-102">Backing Up a Database with Memory-Optimized Tables</span></span>
  <span data-ttu-id="98f87-103">記憶體最佳化資料表會當做正常資料庫備份的一部分進行備份。</span><span class="sxs-lookup"><span data-stu-id="98f87-103">Memory-optimized tables are backed up as part of regular database backups.</span></span> <span data-ttu-id="98f87-104">如果是磁碟資料表，資料庫備份作業會驗證資料的 CHECKSUM 和差異檔案組，以便偵測是否有儲存體損毀。</span><span class="sxs-lookup"><span data-stu-id="98f87-104">As for disk-based tables, the CHECKSUM of data and delta file pairs is validated as part of the database backup to detect storage corruption.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="98f87-105">在備份期間，若您偵測到記憶體最佳化的檔案群組中，有一個或多個檔案有 CHECKSUM 錯誤，就無法還原及重新啟動資料庫。</span><span class="sxs-lookup"><span data-stu-id="98f87-105">During a backup, if you detect a CHECKSUM error in one or more files in a memory-optimized filegroup, you will not be able to restore and restart the database.</span></span> <span data-ttu-id="98f87-106">在此情況下，您必須使用最後的已知良好備份還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="98f87-106">In that situation, you must, restore your database with the last known good backup.</span></span> <span data-ttu-id="98f87-107">若您沒有備份，可以從記憶體最佳化的資料表和磁碟基礎的資料表匯出資料，並在卸除及重新建立資料庫之後重新載入。</span><span class="sxs-lookup"><span data-stu-id="98f87-107">If you don't have a backup, you can export the data from memory-optimized tables and disk-based tables and reload after you drop and recreate the database.</span></span>  
  
 <span data-ttu-id="98f87-108">包含一個或多個記憶體最佳化資料表之資料庫的完整備份是由以下項目所組成：為磁碟資料表配置的儲存體 (如果有的話)、使用中的交易記錄，以及記憶體最佳化資料表的資料和差異檔案組 (又稱為檢查點檔案組)。</span><span class="sxs-lookup"><span data-stu-id="98f87-108">A full backup of a database with one or more memory-optimized tables consists of the allocated storage for disk-based tables (if any), the active transaction log, and the data and delta file pairs (also known as checkpoint file pairs) for memory-optimized tables.</span></span> <span data-ttu-id="98f87-109">不過，如 [記憶體最佳化資料表的持久性](memory-optimized-tables.md)中所述，記憶體最佳化資料表所使用的儲存空間可能會遠超過它在記憶體中的大小，而且會影響資料庫備份的大小。</span><span class="sxs-lookup"><span data-stu-id="98f87-109">However, as described in [Durability for Memory-Optimized Tables](memory-optimized-tables.md), the storage used by memory-optimized tables can be much larger than its size in memory, and it affects the size of the database backup.</span></span>  
  
## <a name="full-database-backup"></a><span data-ttu-id="98f87-110">完整資料庫備份</span><span class="sxs-lookup"><span data-stu-id="98f87-110">Full Database Backup</span></span>  
 <span data-ttu-id="98f87-111">這裡的討論內容著重於只包含持久性記憶體最佳化資料表之資料庫的資料庫備份，因為磁碟資料表的備份是相同的。</span><span class="sxs-lookup"><span data-stu-id="98f87-111">This discussion will focus on database backups for databases with just durable memory-optimized tables, because the backup for disk-based tables is the same.</span></span> <span data-ttu-id="98f87-112">記憶體最佳化檔案群組中的檢查點檔案組可能處於各種不同狀態。</span><span class="sxs-lookup"><span data-stu-id="98f87-112">The checkpoint file pairs in the memory-optimized filegroup could be in various states.</span></span> <span data-ttu-id="98f87-113">下表描述備份檔案的哪個部分。</span><span class="sxs-lookup"><span data-stu-id="98f87-113">The table below describes what part of the files is backed.</span></span>  
  
|<span data-ttu-id="98f87-114">檢查點檔案組狀態</span><span class="sxs-lookup"><span data-stu-id="98f87-114">Checkpoint File Pair State</span></span>|<span data-ttu-id="98f87-115">Backup</span><span class="sxs-lookup"><span data-stu-id="98f87-115">Backup</span></span>|  
|--------------------------------|------------|  
|<span data-ttu-id="98f87-116">已預先建立</span><span class="sxs-lookup"><span data-stu-id="98f87-116">PRECREATED</span></span>|<span data-ttu-id="98f87-117">僅限檔案中繼資料</span><span class="sxs-lookup"><span data-stu-id="98f87-117">File metadata only</span></span>|  
|<span data-ttu-id="98f87-118">建構中</span><span class="sxs-lookup"><span data-stu-id="98f87-118">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="98f87-119">僅限檔案中繼資料</span><span class="sxs-lookup"><span data-stu-id="98f87-119">File metadata only</span></span>|  
|<span data-ttu-id="98f87-120">使用中</span><span class="sxs-lookup"><span data-stu-id="98f87-120">Active</span></span>|<span data-ttu-id="98f87-121">檔案中繼資料加上使用的位元組</span><span class="sxs-lookup"><span data-stu-id="98f87-121">File metadata plus used bytes</span></span>|  
|<span data-ttu-id="98f87-122">合併來源</span><span class="sxs-lookup"><span data-stu-id="98f87-122">Merge source</span></span>|<span data-ttu-id="98f87-123">檔案中繼資料加上使用的位元組</span><span class="sxs-lookup"><span data-stu-id="98f87-123">File metadata plus used bytes</span></span>|  
|<span data-ttu-id="98f87-124">合併目標</span><span class="sxs-lookup"><span data-stu-id="98f87-124">Merge target</span></span>|<span data-ttu-id="98f87-125">僅限檔案中繼資料</span><span class="sxs-lookup"><span data-stu-id="98f87-125">File metadata only</span></span>|  
|<span data-ttu-id="98f87-126">備份/高可用性所需</span><span class="sxs-lookup"><span data-stu-id="98f87-126">REQUIRED FOR BACKUP/HA</span></span>|<span data-ttu-id="98f87-127">檔案中繼資料加上使用的位元組</span><span class="sxs-lookup"><span data-stu-id="98f87-127">File metadata plus used bytes</span></span>|  
|<span data-ttu-id="98f87-128">正在轉換為標記</span><span class="sxs-lookup"><span data-stu-id="98f87-128">IN TRANSITION TO TOMBSTONE</span></span>|<span data-ttu-id="98f87-129">僅限檔案中繼資料</span><span class="sxs-lookup"><span data-stu-id="98f87-129">File metadata only</span></span>|  
|<span data-ttu-id="98f87-130">標記</span><span class="sxs-lookup"><span data-stu-id="98f87-130">TOMBSTONE</span></span>|<span data-ttu-id="98f87-131">僅限檔案中繼資料</span><span class="sxs-lookup"><span data-stu-id="98f87-131">File metadata only</span></span>|  
  
 <span data-ttu-id="98f87-132">包含一個或多個記憶體最佳化資料表之資料庫備份的大小通常超過它在記憶體中的大小，但是小於磁碟儲存空間。</span><span class="sxs-lookup"><span data-stu-id="98f87-132">The size of database backups with one or more memory-optimized tables is typically larger than its size in memory but smaller than the on-disk storage.</span></span> <span data-ttu-id="98f87-133">額外的大小將取決於已刪除的資料列數目以及處於「合併來源」和「備份/高可用性所需」狀態之檢查點檔案組的數目 (間接取決於工作負載)。</span><span class="sxs-lookup"><span data-stu-id="98f87-133">The extra size will depend upon the number of deleted rows and the number of checkpoint file pairs in the states Merge source and REQUIRED FOR BACKUP/HA which indirectly depends upon the workload.</span></span> <span data-ttu-id="98f87-134">如需成對檢查點檔案的狀態原因，請參閱[dm_db_xtp_checkpoint_files &#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="98f87-134">For descriptions of the states for checkpoint file pairs, see [sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql).</span></span>  
  
### <a name="estimating-size-of-full-database-backup"></a><span data-ttu-id="98f87-135">估計完整資料庫備份的大小</span><span class="sxs-lookup"><span data-stu-id="98f87-135">Estimating Size of Full Database Backup</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="98f87-136">建議您不要使用 BackupSizeInBytes 值來估計記憶體內部 OLTP 的備份大小。</span><span class="sxs-lookup"><span data-stu-id="98f87-136">It's recommended that you not use the BackupSizeInBytes value to estimate the backup size for In-Memory OLTP.</span></span>  
  
 <span data-ttu-id="98f87-137">第一個工作負載案例主要是為了插入。</span><span class="sxs-lookup"><span data-stu-id="98f87-137">The first workload scenario is for (mostly) insert.</span></span> <span data-ttu-id="98f87-138">在此案例中，大部分的資料檔案都處於作用中狀態，並且已完全載入，而且已刪除的資料列很少。</span><span class="sxs-lookup"><span data-stu-id="98f87-138">In this scenario, most data files will be in the Active state, fully loaded, and with very few deleted rows.</span></span> <span data-ttu-id="98f87-139">資料庫備份的大小將會與記憶體中的資料大小十分接近。</span><span class="sxs-lookup"><span data-stu-id="98f87-139">The size of database backup up will be close to the size of data in memory.</span></span>  
  
 <span data-ttu-id="98f87-140">第二個工作負載案例是頻繁的插入、刪除和更新作業：在最糟榚的情況下，在考量已刪除的資料列之後，每一個檢查點檔案組的載入程度為 50%。</span><span class="sxs-lookup"><span data-stu-id="98f87-140">The second workload scenario is for frequent insert, delete, and update operations: In the worst case, each of the checkpoint file pairs are 50% loaded, after accounting for the deleted rows.</span></span> <span data-ttu-id="98f87-141">因此，資料庫備份的大小至少為記憶體中資料大小的兩倍。</span><span class="sxs-lookup"><span data-stu-id="98f87-141">So the size of the database backup will at least be 2 times the size of data in memory.</span></span> <span data-ttu-id="98f87-142">另外，處於「合併來源」和「備份/高可用性所需」狀態而且會讓資料庫備份大小增加的檢查點檔案組也很少。</span><span class="sxs-lookup"><span data-stu-id="98f87-142">Additionally, there will few checkpoint file pairs in states Merge source and Required for backup/high availability that will add to the size of database backup.</span></span>  
  
## <a name="differential-backups-of-databases-with-memory-optimized-tables"></a><span data-ttu-id="98f87-143">使用記憶體最佳化資料表的資料庫差異備份</span><span class="sxs-lookup"><span data-stu-id="98f87-143">Differential Backups of Databases with Memory-Optimized Tables</span></span>  
 <span data-ttu-id="98f87-144">記憶體最佳化資料表的儲存體包含資料和差異檔案，如 [記憶體最佳化資料表的持久性](memory-optimized-tables.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="98f87-144">The storage for memory-optimized tables consists of data and delta files as described in [Durability for Memory-Optimized Tables](memory-optimized-tables.md).</span></span> <span data-ttu-id="98f87-145">具有記憶體最佳化資料表之資料庫的差異備份會包含下列資料：</span><span class="sxs-lookup"><span data-stu-id="98f87-145">The differential backup of a database with memory-optimized tables contains the following data:</span></span>  
  
-   <span data-ttu-id="98f87-146">記憶體最佳化資料表的存在並不會影響儲存磁碟資料表之檔案群組的差異備份。</span><span class="sxs-lookup"><span data-stu-id="98f87-146">Differential backup for filegroups storing disk-based tables is not affected by the presence of memory-optimized tables.</span></span>  
  
-   <span data-ttu-id="98f87-147">使用中交易記錄與完整資料庫備份中相同。</span><span class="sxs-lookup"><span data-stu-id="98f87-147">The active transaction log is the same as in a full database backup.</span></span>  
  
-   <span data-ttu-id="98f87-148">對於記憶體最佳化資料檔案群組而言，差異備份會使用與完整資料庫備份相同的演算法來識別資料和差異檔案以進行備份，但是它會接著篩選出檔案的子集，如下所述：</span><span class="sxs-lookup"><span data-stu-id="98f87-148">For a memory-optimized data filegroup, the differential backup uses the same algorithm as full database backup to identify the data and delta files for backup but it then filters out the subset of files as follows:</span></span>  
  
    -   <span data-ttu-id="98f87-149">資料檔案包含新插入的資料列，而該檔案已滿時，就會關閉並標示為唯讀。</span><span class="sxs-lookup"><span data-stu-id="98f87-149">A data file contains newly inserted rows and when it is full, it is closed and marked read-only.</span></span> <span data-ttu-id="98f87-150">資料檔案只有在上一次完整資料庫備份之後關閉時，才會進行備份。</span><span class="sxs-lookup"><span data-stu-id="98f87-150">A data file is backed up only if it was closed after the last full database backup.</span></span> <span data-ttu-id="98f87-151">差異備份只會備份包含上一次完整資料庫備份之後插入之資料列的資料檔案，但不包括更新和刪除的情況，因為在這類情況下，部分插入的資料列可能已標示為記憶體回收，或是已進行過記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="98f87-151">The differential backup only backups up data files containing the inserted rows since the last full database backup with the exception of an update and delete scenario where it is possible that some of the inserted rows may have already been either marked for garbage collection or already garbage collected.</span></span>  
  
    -   <span data-ttu-id="98f87-152">差異檔案會儲存已刪除資料列的參考。</span><span class="sxs-lookup"><span data-stu-id="98f87-152">A delta file stores references to the deleted data rows.</span></span> <span data-ttu-id="98f87-153">由於所有後續交易都可以刪除資料列，因此差異檔案可以在其存留期內隨時修改，而且永遠不會關閉。</span><span class="sxs-lookup"><span data-stu-id="98f87-153">Since any future transaction can delete a row, a delta file can be modified anytime in its life time, it is never closed.</span></span> <span data-ttu-id="98f87-154">差異檔案一律會備份。</span><span class="sxs-lookup"><span data-stu-id="98f87-154">A delta file is always backed up.</span></span> <span data-ttu-id="98f87-155">差異檔案通常使用不到 10% 的儲存空間，因此差異檔案對於差異備份大小的影響非常小。</span><span class="sxs-lookup"><span data-stu-id="98f87-155">Delta files typically use less than 10% of the storage, so delta files have a minimal impact on the size of differential backup.</span></span>  
  
 <span data-ttu-id="98f87-156">如果記憶體最佳化資料表是您資料庫大小的重要部分，則差異備份能夠大幅減少資料庫備份的大小。</span><span class="sxs-lookup"><span data-stu-id="98f87-156">If memory-optimized tables are a significant portion of your database size, the differential backup can significantly reduce the size of your database backup.</span></span>  
  
 <span data-ttu-id="98f87-157">如果是一般 OLTP 工作負載，差異備份將會遠小於完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="98f87-157">For typical OLTP workloads, the differential backups will be considerably smaller than the full database backups.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98f87-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98f87-158">See Also</span></span>  
 [<span data-ttu-id="98f87-159">備份、還原及復原記憶體最佳化資料表</span><span class="sxs-lookup"><span data-stu-id="98f87-159">Backup, Restore, and Recovery of Memory-Optimized Tables</span></span>](restore-and-recovery-of-memory-optimized-tables.md)  
  
  
