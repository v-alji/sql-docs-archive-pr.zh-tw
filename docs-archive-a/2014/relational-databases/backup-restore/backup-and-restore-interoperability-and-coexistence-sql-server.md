---
title: 備份與還原：互通性與共存性 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- file restores [SQL Server], related features
- restoring [SQL Server], files
- restoring files [SQL Server], related features
- backups [SQL Server], files or filegroups
- file backups [SQL Server], related features
ms.assetid: 69f212b8-edcd-4c5d-8a8a-679ced33c128
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cd78e5f1e85510ec7a14548280a616a9b32aec55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584599"
---
# <a name="backup-and-restore-interoperability-and-coexistence-sql-server"></a><span data-ttu-id="07b11-102">備份與還原：互通性與共存性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="07b11-102">Backup and Restore: Interoperability and Coexistence (SQL Server)</span></span>
  <span data-ttu-id="07b11-103">本主題描述 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中數個功能的備份和還原考量。</span><span class="sxs-lookup"><span data-stu-id="07b11-103">This topic describes backup-and-restore considerations for several features in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="07b11-104">這些功能包括：檔案還原和資料庫啟動、線上還原和停用的索引、資料庫鏡像，以及分次還原和全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="07b11-104">These features include: file restore and database startup, online restore and disabled indexes, database mirroring, and piecemeal restore and full-text indexes.</span></span>  
  
 <span data-ttu-id="07b11-105">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="07b11-105">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="07b11-106">檔案還原與資料庫啟動</span><span class="sxs-lookup"><span data-stu-id="07b11-106">File Restore and Database Startup</span></span>](#FileRestoreAndDbStartup)  
  
-   [<span data-ttu-id="07b11-107">線上還原和停用的索引</span><span class="sxs-lookup"><span data-stu-id="07b11-107">Online Restore and Disabled Indexes</span></span>](#OnlineRestoreAndDisabledIndexes)  
  
-   [<span data-ttu-id="07b11-108">資料庫鏡像與備份和還原</span><span class="sxs-lookup"><span data-stu-id="07b11-108">Database Mirroring and Backup and Restore</span></span>](#DbMandBnR)  
  
-   [<span data-ttu-id="07b11-109">分次還原和全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="07b11-109">Piecemeal Restore and Full-Text Indexes</span></span>](#PiecemealAndFTIndexes)  
  
-   [<span data-ttu-id="07b11-110">檔案備份以及還原與壓縮</span><span class="sxs-lookup"><span data-stu-id="07b11-110">File Backup and Restore and Compression</span></span>](#FileBnRandCompression)  
  
-   [<span data-ttu-id="07b11-111">相關工作</span><span class="sxs-lookup"><span data-stu-id="07b11-111">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="file-restore-and-database-startup"></a><a name="FileRestoreAndDbStartup"></a> <span data-ttu-id="07b11-112">檔案還原與資料庫啟動</span><span class="sxs-lookup"><span data-stu-id="07b11-112">File Restore and Database Startup</span></span>  
 <span data-ttu-id="07b11-113">本節僅與包含多個檔案群組的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫有關。</span><span class="sxs-lookup"><span data-stu-id="07b11-113">This section is relevant only for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that have multiple filegroups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07b11-114">當資料庫啟動時，只有在資料庫關閉時其檔案仍在線上的檔案群組才會復原並回到線上。</span><span class="sxs-lookup"><span data-stu-id="07b11-114">When a database is started, only filegroups whose files were online when the database was closed are recovered and brought online.</span></span>  
  
 <span data-ttu-id="07b11-115">如果在資料庫啟動期間發生問題，復原會失敗，且會將資料庫標示為 SUSPECT。</span><span class="sxs-lookup"><span data-stu-id="07b11-115">If a problem is encountered during database startup, recovery fails, and the database is marked as SUSPECT.</span></span> <span data-ttu-id="07b11-116">如果將問題隔離到檔案，資料庫管理員就可以使檔案離線，並嘗試重新啟動資料庫。</span><span class="sxs-lookup"><span data-stu-id="07b11-116">If the problem can be isolated to a file or files, the database administrator can take the files offline and try to restart the database.</span></span> <span data-ttu-id="07b11-117">若要使檔案離線，您可以使用下列 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) 陳述式：</span><span class="sxs-lookup"><span data-stu-id="07b11-117">To take a file offline, you can use the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement:</span></span>  
  
 <span data-ttu-id="07b11-118">ALTER database *database_name*修改檔案 (名稱 **= ' *`filename`* '**，離線) </span><span class="sxs-lookup"><span data-stu-id="07b11-118">ALTER DATABASE *database_name* MODIFY FILE (NAME **='*`filename`*'**, OFFLINE)</span></span>  
  
 <span data-ttu-id="07b11-119">如果啟動成功，任何包含離線檔案的檔案群組都會保持離線。</span><span class="sxs-lookup"><span data-stu-id="07b11-119">If startup succeeds, any filegroup that contains an offline file remains offline.</span></span>  
  
##  <a name="online-restore-and-disabled-indexes"></a><a name="OnlineRestoreAndDisabledIndexes"></a> <span data-ttu-id="07b11-120">線上還原和停用的索引</span><span class="sxs-lookup"><span data-stu-id="07b11-120">Online Restore and Disabled Indexes</span></span>  
 <span data-ttu-id="07b11-121">本節僅與包含多個檔案群組 (在簡單復原模式下，至少有一個唯讀檔案群組) 的資料庫有關。</span><span class="sxs-lookup"><span data-stu-id="07b11-121">This section is relevant only for databases that have multiple filegroups and, for the simple recovery model, at least one read-only filegroup.</span></span>  
  
 <span data-ttu-id="07b11-122">在這些案例中，如果資料庫在線上，則只有在保有索引任一部分的所有檔案群組都在線上時，才可以建立、卸除、啟用或停用索引。</span><span class="sxs-lookup"><span data-stu-id="07b11-122">In these cases, when a database is online, the index can be created, dropped, enabled or disabled only if all filegroups holding any part of the index are online.</span></span>  
  
 <span data-ttu-id="07b11-123">如需還原離線檔案群組的相關資訊，請參閱[線上還原 &#40;SQL Server&#41;](online-restore-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="07b11-123">For information about restoring offline filegroups, see [Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md).</span></span>  
  
##  <a name="database-mirroring-and-backup-and-restore"></a><a name="DbMandBnR"></a> <span data-ttu-id="07b11-124">資料庫鏡像與備份和還原</span><span class="sxs-lookup"><span data-stu-id="07b11-124">Database Mirroring and Backup and Restore</span></span>  
 <span data-ttu-id="07b11-125">本節僅與包含多個檔案群組的完整模式資料庫有關。</span><span class="sxs-lookup"><span data-stu-id="07b11-125">This section is relevant only for full-model databases that have multiple filegroups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07b11-126">未來的 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本將移除資料庫鏡像功能。</span><span class="sxs-lookup"><span data-stu-id="07b11-126">The database mirroring feature will be removed in a future version of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="07b11-127">請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="07b11-127">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span> <span data-ttu-id="07b11-128">請改用 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="07b11-128">Use [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] instead.</span></span>  
  
 <span data-ttu-id="07b11-129">資料庫鏡像是增加資料庫可用性的軟體方案。</span><span class="sxs-lookup"><span data-stu-id="07b11-129">Database mirroring is a solution for increasing database availability.</span></span> <span data-ttu-id="07b11-130">鏡像是以每個資料庫為基準實作，只適用於使用完整復原模式的資料庫。</span><span class="sxs-lookup"><span data-stu-id="07b11-130">Mirroring is implemented on a per-database basis and works only with databases that use the full recovery model.</span></span> <span data-ttu-id="07b11-131">如需詳細資訊，請參閱[資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="07b11-131">For more information, see [Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07b11-132">若要散發資料庫中檔案群組子集的副本，請使用複寫：請只複寫檔案群組中您要複製到其他伺服器的物件。</span><span class="sxs-lookup"><span data-stu-id="07b11-132">To distribute copies of a subset of the filegroups in a database, use replication: replicate only those objects in the filegroups you want to copy to other servers.</span></span> <span data-ttu-id="07b11-133">如需複寫的詳細資訊，請參閱 [SQL Server 複寫](../../relational-databases/replication/sql-server-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="07b11-133">For more information about replication, see [SQL Server Replication](../../relational-databases/replication/sql-server-replication.md).</span></span>  
  
### <a name="creating-the-mirror-database"></a><span data-ttu-id="07b11-134">建立鏡像資料庫</span><span class="sxs-lookup"><span data-stu-id="07b11-134">Creating the Mirror Database</span></span>  
 <span data-ttu-id="07b11-135">鏡像資料庫是透過在鏡像伺服器上還原 (但不復原) 主體資料庫備份的方式所建立。</span><span class="sxs-lookup"><span data-stu-id="07b11-135">The mirror database is created by restoring, WITH NORECOVERY, backups of the principal database on the mirror server.</span></span> <span data-ttu-id="07b11-136">還原必須保留相同的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="07b11-136">The restore must keep the same database name.</span></span> <span data-ttu-id="07b11-137">如需詳細資訊，請參閱 [準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="07b11-137">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
 <span data-ttu-id="07b11-138">您可以使用分次還原順序來建立鏡像資料庫 (只要有支援)。</span><span class="sxs-lookup"><span data-stu-id="07b11-138">You can create the mirror database by using use a piecemeal restore sequence, where supported.</span></span> <span data-ttu-id="07b11-139">不過，要等到還原了所有檔案群組，而且通常還要在時間點上將記錄備份還原到夠接近主體資料庫的時間點之後，才能開始進行鏡像。</span><span class="sxs-lookup"><span data-stu-id="07b11-139">However, you cannot start mirroring until you have restored all the filegroups and, typically, restored log backups to get the mirror database close enough in time with the principal database.</span></span> <span data-ttu-id="07b11-140">如需詳細資訊，請參閱[分次還原 &#40;SQL Server&#41;](piecemeal-restores-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="07b11-140">For more information, see [Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md).</span></span>  
  
### <a name="restrictions-on-backup-and-restore-during-mirroring"></a><span data-ttu-id="07b11-141">鏡像期間備份和還原的限制</span><span class="sxs-lookup"><span data-stu-id="07b11-141">Restrictions on Backup and Restore During Mirroring</span></span>  
 <span data-ttu-id="07b11-142">資料庫鏡像工作階段使用中時，將套用下列限制：</span><span class="sxs-lookup"><span data-stu-id="07b11-142">While a database mirroring session is active, the following restrictions apply:</span></span>  
  
-   <span data-ttu-id="07b11-143">不允許備份和還原鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="07b11-143">Backup and restore of the mirror database are not allowed.</span></span>  
  
-   <span data-ttu-id="07b11-144">允許備份主體資料庫，但不允許 BACKUP LOG WITH NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="07b11-144">Backup of the principal database is allowed, but BACKUP LOG WITH NORECOVERY is not allowed.</span></span>  
  
-   <span data-ttu-id="07b11-145">不允許還原主體資料庫。</span><span class="sxs-lookup"><span data-stu-id="07b11-145">Restoring the principal database is not allowed.</span></span>  
  
##  <a name="piecemeal-restore-and-full-text-indexes"></a><a name="PiecemealAndFTIndexes"></a> <span data-ttu-id="07b11-146">分次還原和全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="07b11-146">Piecemeal Restore and Full-Text Indexes</span></span>  
 <span data-ttu-id="07b11-147">本節只與包含多個檔案群組的資料庫有關，而在簡單模式資料庫中僅與唯讀檔案群組相關。</span><span class="sxs-lookup"><span data-stu-id="07b11-147">This section is relevant only for databases that contain multiple filegroups and, for the simple-model databases, only for read-only filegroups.</span></span>  
  
 <span data-ttu-id="07b11-148">全文檢索索引會儲存在資料庫檔案群組中，而且可能會受到分次還原的影響。</span><span class="sxs-lookup"><span data-stu-id="07b11-148">Full-text indexes are stored in database filegroups and can be affected by a piecemeal restore.</span></span> <span data-ttu-id="07b11-149">如果全文檢索索引與任何相關聯的資料表資料位於相同的檔案群組中，分次還原就會依照預期方式運作。</span><span class="sxs-lookup"><span data-stu-id="07b11-149">If the full-text index resides in the same filegroup as any of the associated table data, piecemeal restore works as expected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07b11-150">若要檢視包含全文檢索索引之檔案群組的檔案群組識別碼，請選取 [sys.fulltext_indexes](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql)的 data_space_id 資料行。</span><span class="sxs-lookup"><span data-stu-id="07b11-150">To view the filegroup ID of the filegroup that contains a full-text index, select the data_space_id column of [sys.fulltext_indexes](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql).</span></span>  
  
### <a name="full-text-indexes-and-tables-in-separate-filegroups"></a><span data-ttu-id="07b11-151">個別檔案群組中的全文檢索索引和資料表</span><span class="sxs-lookup"><span data-stu-id="07b11-151">Full-Text Indexes and Tables in Separate Filegroups</span></span>  
 <span data-ttu-id="07b11-152">如果全文檢索索引與所有相關聯的資料表資料位於不同的檔案群組中，則分次還原的行為會取決於第一個還原且上線的檔案群組而定：</span><span class="sxs-lookup"><span data-stu-id="07b11-152">If a full-text index resides in a separate filegroup from all of the associated table data, the behavior of piecemeal restore depends on which of the filegroups is restored and brought online first:</span></span>  
  
-   <span data-ttu-id="07b11-153">如果包含全文檢索索引的檔案群組在包含相關聯資料表資料的檔案群組之前還原並上線，一旦全文檢索索引上線時，全文檢索搜尋就會依照預期方式運作。</span><span class="sxs-lookup"><span data-stu-id="07b11-153">If the filegroup that contains the full-text index is restored and brought online before the filegroups that contain the associated table data, full-text search works as expected as soon as the full-text index is online.</span></span>  
  
-   <span data-ttu-id="07b11-154">如果包含資料表資料的檔案群組在包含全文檢索索引的檔案群組之前還原並上線，則全文檢索行為可能會受到影響。</span><span class="sxs-lookup"><span data-stu-id="07b11-154">If the filegroup that contains the table data is restored and brought online before the filegroup that contains the full-text index, full-text behavior might be affected.</span></span> <span data-ttu-id="07b11-155">這是因為在索引上線之前，觸發母體擴展、重建目錄或重新組織目錄的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式都會失敗。</span><span class="sxs-lookup"><span data-stu-id="07b11-155">This is because [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that trigger a population, rebuild the catalog, or reorganize the catalog fail until the index is brought online.</span></span> <span data-ttu-id="07b11-156">這些陳述式包括 CREATE FULLTEXT INDEX、ALTER FULLTEXT INDEX、DROP FULLTEXT INDEX 和 ALTER FULLTEXT CATALOG。</span><span class="sxs-lookup"><span data-stu-id="07b11-156">These statements include CREATE FULLTEXT INDEX, ALTER FULLTEXT INDEX, DROP FULLTEXT INDEX, and ALTER FULLTEXT CATALOG.</span></span>  
  
     <span data-ttu-id="07b11-157">在此情況下，下列因素就很重要：</span><span class="sxs-lookup"><span data-stu-id="07b11-157">In this case, the following factors are significant:</span></span>  
  
    -   <span data-ttu-id="07b11-158">如果全文檢索索引具有變更追蹤，在索引檔案群組上線之前，使用者 DML 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="07b11-158">If the full-text index has change tracking, user DML will fail until the index filegroup is brought online.</span></span> <span data-ttu-id="07b11-159">此外，在索引檔案群組上線之前，刪除作業也會失敗。</span><span class="sxs-lookup"><span data-stu-id="07b11-159">Delete operation will also fail until the index filegroup is online.</span></span>  
  
    -   <span data-ttu-id="07b11-160">無論變更追蹤與否，全文檢索查詢都會失敗，因為無法使用索引。</span><span class="sxs-lookup"><span data-stu-id="07b11-160">Regardless of change tracking, full-text queries fail because the index is not available.</span></span> <span data-ttu-id="07b11-161">如果在包含全文檢索索引的檔案群組離線時，嘗試全文檢索查詢，將會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="07b11-161">If a full-text query is tried when the filegroup that contains the full-text index is offline, an error is returned.</span></span>  
  
    -   <span data-ttu-id="07b11-162">只有當狀態函數 (例如 FULLTEXTCATALOGPROPERTY) 不需要存取全文檢索索引時，這些函數才會成功。</span><span class="sxs-lookup"><span data-stu-id="07b11-162">Status functions (such as FULLTEXTCATALOGPROPERTY) succeed only when they do not have to access full-text index.</span></span> <span data-ttu-id="07b11-163">例如，存取任何線上全文檢索中繼資料都會成功，但是 **uniquekeycount、itemcount** 卻會失敗。</span><span class="sxs-lookup"><span data-stu-id="07b11-163">For example, access to any online full-text metadata would succeed, but **uniquekeycount, itemcount** would fail.</span></span>  
  
     <span data-ttu-id="07b11-164">在全文檢索索引檔案群組還原並上線之後，索引資料與資料表資料就會一致。</span><span class="sxs-lookup"><span data-stu-id="07b11-164">After the full-text index filegroup is restored and brought online, the index data and table data are consistent.</span></span>  
  
 <span data-ttu-id="07b11-165">一旦資料表檔案群組和群組檢索索引檔案群組都上線時，任何暫停的全文檢索母體擴展就會繼續進行。</span><span class="sxs-lookup"><span data-stu-id="07b11-165">As soon as both the base table filegroup and the full-text index filegroup are online, any paused full-text population is resumed.</span></span>  
  
##  <a name="file-backup-and-restore-and-compression"></a><a name="FileBnRandCompression"></a> <span data-ttu-id="07b11-166">檔案備份以及還原與壓縮</span><span class="sxs-lookup"><span data-stu-id="07b11-166">File Backup and Restore and Compression</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="07b11-167">支援唯讀檔案群組及唯讀資料庫的 NTFS 檔案系統資料壓縮。</span><span class="sxs-lookup"><span data-stu-id="07b11-167">supports NTFS file system data compression of read-only filegroups and read-only databases.</span></span>  
  
 <span data-ttu-id="07b11-168">壓縮的 NTFS 檔案支援唯讀檔案群組中的檔案還原。</span><span class="sxs-lookup"><span data-stu-id="07b11-168">Restoring files in a read-only filegroup is supported on compressed NTFS files.</span></span> <span data-ttu-id="07b11-169">這些檔案群組的備份與還原，本質上與任何唯讀檔案群組相同，但有下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="07b11-169">Backup and restore of these filegroups works essentially as it would for any read-only filegroup, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="07b11-170">將讀寫檔案 (包括讀寫資料庫的主要檔案或記錄檔) 還原至壓縮磁碟區會失敗，並顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="07b11-170">Restoring a read-write file (including the primary or log files of a read-write database) to a compressed volume fails and displays an error.</span></span>  
  
-   <span data-ttu-id="07b11-171">允許將唯讀資料庫還原至壓縮磁碟區。</span><span class="sxs-lookup"><span data-stu-id="07b11-171">Restoring a read-only database to a compressed volume is allowed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07b11-172">讀取/寫入資料庫的記錄檔絕不可放在壓縮檔案系統上。</span><span class="sxs-lookup"><span data-stu-id="07b11-172">Log files of read/write databases should never be placed on compressed file systems.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="07b11-173">相關工作</span><span class="sxs-lookup"><span data-stu-id="07b11-173">Related Tasks</span></span>  
  
-   [<span data-ttu-id="07b11-174">準備鏡像資料庫以進行鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="07b11-174">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
-   [<span data-ttu-id="07b11-175">備份並還原全文檢索目錄與索引</span><span class="sxs-lookup"><span data-stu-id="07b11-175">Back Up and Restore Full-Text Catalogs and Indexes</span></span>](../search/back-up-and-restore-full-text-catalogs-and-indexes.md)  
  
## <a name="see-also"></a><span data-ttu-id="07b11-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07b11-176">See Also</span></span>  
 <span data-ttu-id="07b11-177">[SQL Server 資料庫的備份與還原](back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="07b11-177">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="07b11-178">[備份及還原複寫的資料庫](../replication/administration/back-up-and-restore-replicated-databases.md) </span><span class="sxs-lookup"><span data-stu-id="07b11-178">[Back Up and Restore Replicated Databases](../replication/administration/back-up-and-restore-replicated-databases.md) </span></span>  
 [<span data-ttu-id="07b11-179">作用中次要資料庫：次要複本上的備份 &#40;AlwaysOn 可用性群組&#41;</span><span class="sxs-lookup"><span data-stu-id="07b11-179">Active Secondaries: Backup on Secondary Replicas &#40;AlwaysOn Availability Groups&#41;</span></span>](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)  
  
  
