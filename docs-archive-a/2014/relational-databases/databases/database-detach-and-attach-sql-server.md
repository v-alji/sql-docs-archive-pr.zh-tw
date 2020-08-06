---
title: 資料庫卸離與附加 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- upgrading databases
- databases [SQL Server], detaching
- detach database [SQL Server]
- databases [SQL Server], attaching
- removing databases
- transaction logs [SQL Server], detaching
- databases [SQL Server], removing
- restoring [SQL Server], attached databases
- transaction logs [SQL Server], attaching
- differential backups, after detaching
- moving databases
- attach database [SQL Server]
- detaching databases [SQL Server]
- differential base [SQL Server]
- attaching databases [SQL Server]
- databases [SQL Server], moving
ms.assetid: d0de0639-bc54-464e-98b1-6af22a27eb86
author: stevestein
ms.author: sstein
ms.openlocfilehash: 54eeeec995e390b71ce8871b680c26138fc88783
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595118"
---
# <a name="database-detach-and-attach-sql-server"></a><span data-ttu-id="7af09-102">資料庫卸離與附加 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7af09-102">Database Detach and Attach (SQL Server)</span></span>
  <span data-ttu-id="7af09-103">您可以將資料庫的資料和交易記錄檔卸離，然後再重新附加至相同或不同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="7af09-103">The data and transaction log files of a database can be detached and then reattached to the same or another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7af09-104">若要將資料庫變更至同一台電腦上的不同 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，或要移動資料庫，卸離和附加資料庫相當有用。</span><span class="sxs-lookup"><span data-stu-id="7af09-104">Detaching and attaching a database is useful if you want to change the database to a different instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the same computer or to move the database.</span></span>  
  
 <span data-ttu-id="7af09-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 磁碟儲存格式在 64 位元與 32 位元環境下都相同。</span><span class="sxs-lookup"><span data-stu-id="7af09-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on-disk storage format is the same in the 64-bit and 32-bit environments.</span></span> <span data-ttu-id="7af09-106">因此，附加作業可以跨 32 位元和 64 位元環境執行。</span><span class="sxs-lookup"><span data-stu-id="7af09-106">Therefore, attach works across 32-bit and 64-bit environments.</span></span>  <span data-ttu-id="7af09-107">從在其中一種環境執行的伺服器執行個體卸離資料庫，可以附加到在另一種環境執行的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="7af09-107">A database detached from a server instance running in one environment can be attached on a server instance that runs in another environment.</span></span>  
  
  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7af09-108">Security</span><span class="sxs-lookup"><span data-stu-id="7af09-108">Security</span></span>  
 <span data-ttu-id="7af09-109">檔案存取權限是在數個資料庫作業期間設定，包括卸離或附加資料庫。</span><span class="sxs-lookup"><span data-stu-id="7af09-109">File access permissions are set during a number of database operations, including detaching or attaching a database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7af09-110">建議您不要附加或還原來源不明或來源不受信任的資料庫。</span><span class="sxs-lookup"><span data-stu-id="7af09-110">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="7af09-111">這種資料庫可能包含惡意程式碼，因此可能執行非預期的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼，或是修改結構描述或實體資料庫結構而造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="7af09-111">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="7af09-112">使用來源不明或來源不受信任的資料庫之前，請先在非實際執行伺服器的資料庫上執行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) ，同時檢查資料庫中的程式碼，例如預存程序或其他使用者定義程式碼。</span><span class="sxs-lookup"><span data-stu-id="7af09-112">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
##  <a name="detaching-a-database"></a><a name="DetachDb"></a> <span data-ttu-id="7af09-113">卸離資料庫</span><span class="sxs-lookup"><span data-stu-id="7af09-113">Detaching a Database</span></span>  
 <span data-ttu-id="7af09-114">卸離資料庫時會從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體移除該資料庫，但會保留資料庫中的資料檔和交易記錄檔。</span><span class="sxs-lookup"><span data-stu-id="7af09-114">Detaching a database removes it from the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] but leaves the database intact within its data files and transaction log files.</span></span> <span data-ttu-id="7af09-115">您可使用這些檔案將資料庫附加到任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體，包括已卸離該資料庫的伺服器。</span><span class="sxs-lookup"><span data-stu-id="7af09-115">These files can then be used to attach the database to any instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], including the server from which the database was detached.</span></span>  
  
 <span data-ttu-id="7af09-116">如果下列任一情況為真，則您不能卸離資料庫：</span><span class="sxs-lookup"><span data-stu-id="7af09-116">You cannot detach a database if any of the following are true:</span></span>  
  
-   <span data-ttu-id="7af09-117">資料庫已複寫和發行。</span><span class="sxs-lookup"><span data-stu-id="7af09-117">The database is replicated and published.</span></span> <span data-ttu-id="7af09-118">如果複寫的話，必須取消發行資料庫。</span><span class="sxs-lookup"><span data-stu-id="7af09-118">If replicated, the database must be unpublished.</span></span> <span data-ttu-id="7af09-119">在卸離資料庫之前，您必須先執行 [sp_replicationdboption](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)以停用發行。</span><span class="sxs-lookup"><span data-stu-id="7af09-119">Before you can detach it, you must disable publishing by running [sp_replicationdboption](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7af09-120">如果您無法使用 **sp_replicationdboption**，可執行 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)來移除複寫。</span><span class="sxs-lookup"><span data-stu-id="7af09-120">If you cannot use **sp_replicationdboption**, you can remove replication by running [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql).</span></span>  
  
-   <span data-ttu-id="7af09-121">資料庫有資料庫快照集存在。</span><span class="sxs-lookup"><span data-stu-id="7af09-121">A database snapshot exists on the database.</span></span>  
  
     <span data-ttu-id="7af09-122">在卸離資料庫之前，您必須先卸除它的所有快照集。</span><span class="sxs-lookup"><span data-stu-id="7af09-122">Before you can detach the database, you must drop all of its snapshots.</span></span> <span data-ttu-id="7af09-123">如需詳細資訊，請參閱 [卸除資料庫快照集 &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="7af09-123">For more information, see [Drop a Database Snapshot &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7af09-124">無法卸離或附加資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="7af09-124">A database snapshot cannot be detached or attached.</span></span>  
  
-   <span data-ttu-id="7af09-125">資料庫正在資料庫鏡像工作階段中進行鏡像。</span><span class="sxs-lookup"><span data-stu-id="7af09-125">The database is being mirrored in a database mirroring session.</span></span>  
  
     <span data-ttu-id="7af09-126">除非工作階段結束，否則，您無法卸離資料庫。</span><span class="sxs-lookup"><span data-stu-id="7af09-126">The database cannot be detached unless the session is terminated.</span></span> <span data-ttu-id="7af09-127">如需詳細資訊，請參閱 [移除資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="7af09-127">For more information, see [Removing Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
-   <span data-ttu-id="7af09-128">資料庫受質疑。</span><span class="sxs-lookup"><span data-stu-id="7af09-128">The database is suspect.</span></span> <span data-ttu-id="7af09-129">您無法卸離受質疑的資料庫，而必須先將受質疑的資料庫設定為緊急模式，才能將其卸離。</span><span class="sxs-lookup"><span data-stu-id="7af09-129">A suspect database cannot be detached; before you can detach it, you must put it into emergency mode.</span></span> <span data-ttu-id="7af09-130">如需有關如何使資料庫進入緊急模式的詳細資訊，請參閱 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7af09-130">For more information about how to put a database into emergency mode, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
-   <span data-ttu-id="7af09-131">此資料庫是系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="7af09-131">The database is a system database.</span></span>  
  
### <a name="backup-and-restore-and-detach"></a><span data-ttu-id="7af09-132">備份和還原與卸離</span><span class="sxs-lookup"><span data-stu-id="7af09-132">Backup and Restore and Detach</span></span>  
 <span data-ttu-id="7af09-133">卸離唯讀資料庫會失去有關差異備份之差異基底的資訊。</span><span class="sxs-lookup"><span data-stu-id="7af09-133">Detaching a read-only database loses information about the differential bases of differential backups.</span></span> <span data-ttu-id="7af09-134">如需詳細資訊，請參閱 [差異備份 &#40;SQL Server&#41;](../backup-restore/differential-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7af09-134">For more information, see [Differential Backups &#40;SQL Server&#41;](../backup-restore/differential-backups-sql-server.md).</span></span>  
  
### <a name="responding-to-detach-errors"></a><span data-ttu-id="7af09-135">回應卸離錯誤</span><span class="sxs-lookup"><span data-stu-id="7af09-135">Responding to Detach Errors</span></span>  
 <span data-ttu-id="7af09-136">若在卸離資料庫時發生錯誤，資料庫將無法完全關閉，也無法重建交易記錄檔。</span><span class="sxs-lookup"><span data-stu-id="7af09-136">Errors produced while detaching a database can prevent the database from closing cleanly and the transaction log from being rebuilt.</span></span> <span data-ttu-id="7af09-137">若您收到錯誤訊息，請執行下列訂正動作：</span><span class="sxs-lookup"><span data-stu-id="7af09-137">If you receive an error message, perform the following corrective actions:</span></span>  
  
1.  <span data-ttu-id="7af09-138">重新附加所有與資料庫關聯的檔案，而非只有主要檔案。</span><span class="sxs-lookup"><span data-stu-id="7af09-138">Reattach all files associated with the database, not just the primary file.</span></span>  
  
2.  <span data-ttu-id="7af09-139">解決造成錯誤訊息的問題。</span><span class="sxs-lookup"><span data-stu-id="7af09-139">Resolve the problem that caused the error message.</span></span>  
  
3.  <span data-ttu-id="7af09-140">再次卸離資料庫。</span><span class="sxs-lookup"><span data-stu-id="7af09-140">Detach the database again.</span></span>  
  
##  <a name="attaching-a-database"></a><a name="AttachDb"></a> <span data-ttu-id="7af09-141">附加資料庫</span><span class="sxs-lookup"><span data-stu-id="7af09-141">Attaching a Database</span></span>  
 <span data-ttu-id="7af09-142">您可以附加複製的或卸離的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="7af09-142">You can attach a copied or detached [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="7af09-143">當您附加 [!INCLUDE[ssVersion2005](../../includes/sscurrent-md.md)] 伺服器實例時，會從先前的位置附加這些目錄檔案以及其他資料庫檔案，這與中的相同 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7af09-143">When you attach a [!INCLUDE[ssVersion2005](../../includes/sscurrent-md.md)] server instance, the catalog files are attached from their previous location along with the other database files, the same as in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="7af09-144">如需詳細資訊，請參閱 [升級全文檢索搜尋](../search/upgrade-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="7af09-144">For more information, see [Upgrade Full-Text Search](../search/upgrade-full-text-search.md).</span></span>  
  
 <span data-ttu-id="7af09-145">當您附加資料庫時，所有的資料檔 (MDF 和 NDF 檔案) 都必須可供使用。</span><span class="sxs-lookup"><span data-stu-id="7af09-145">When you attach a database, all data files (MDF and NDF files) must be available.</span></span> <span data-ttu-id="7af09-146">如果資料檔案的路徑與資料庫第一次建立或最後一次附加時的路徑不同，您必須指定檔案的目前路徑。</span><span class="sxs-lookup"><span data-stu-id="7af09-146">If any data file has a different path from when the database was first created or last attached, you must specify the current path of the file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7af09-147">如果附加的主要資料檔是唯讀的，則 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會假設該資料庫也是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="7af09-147">If the primary data file being attached is read-only, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] assumes that the database is read-only.</span></span>  
  
 <span data-ttu-id="7af09-148">第一次將加密的資料庫附加到實例時 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，資料庫擁有者必須藉由執行下列語句來開啟資料庫的主要金鑰：依密碼的開啟主要金鑰解密 = **' *`password`* '**。</span><span class="sxs-lookup"><span data-stu-id="7af09-148">When an encrypted database is first attached to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the database owner must open the master key of the database by executing the following statement: OPEN MASTER KEY DECRYPTION BY PASSWORD = **'*`password`*'**.</span></span> <span data-ttu-id="7af09-149">建議您執行下列陳述式來啟用主要金鑰的自動解密：ALTER MASTER KEY ADD ENCRYPTION BY SERVICE MASTER KEY。</span><span class="sxs-lookup"><span data-stu-id="7af09-149">We recommend that you enable automatic decryption of the master key by executing the following statement: ALTER MASTER KEY ADD ENCRYPTION BY SERVICE MASTER KEY.</span></span> <span data-ttu-id="7af09-150">如需詳細資訊，請參閱 [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) 和 [ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7af09-150">For more information, see [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) and [ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql).</span></span>  
  
 <span data-ttu-id="7af09-151">要不要附加記錄檔，其需求有一部分視資料庫是可讀寫或唯讀而定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7af09-151">The requirement for attaching log files depends partly on whether the database is read-write or read-only, as follows:</span></span>  
  
-   <span data-ttu-id="7af09-152">如果是讀寫資料庫，您通常可以在新位置附加記錄檔。</span><span class="sxs-lookup"><span data-stu-id="7af09-152">For a read-write database, you can usually attach a log file in a new location.</span></span> <span data-ttu-id="7af09-153">不過，某些情況下，重新附加資料庫需要其現有的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="7af09-153">However, in some cases, reattaching a database requires its existing log files.</span></span> <span data-ttu-id="7af09-154">因此，請務必保留所有卸離的記錄檔，直到資料庫在沒有這些檔案的情形下成功附加為止。</span><span class="sxs-lookup"><span data-stu-id="7af09-154">Therefore, it is important to always keep all the detached log files until the database has been successfully attached without them.</span></span>  
  
     <span data-ttu-id="7af09-155">如果讀寫資料庫具有單一記錄檔，而您未指定新位置給該記錄檔，附加作業就會在舊位置尋找該檔案。</span><span class="sxs-lookup"><span data-stu-id="7af09-155">If a read-write database has a single log file and you do not specify a new location for the log file, the attach operation looks in the old location for the file.</span></span> <span data-ttu-id="7af09-156">如果找到，就會使用舊的記錄檔，不論資料庫是否完全關閉。</span><span class="sxs-lookup"><span data-stu-id="7af09-156">If it is found, the old log file is used, regardless of whether the database was shut down cleanly.</span></span> <span data-ttu-id="7af09-157">不過，如果找不到舊記錄檔，且資料庫已完全關閉而無使用中的記錄鏈結，附加作業便會嘗試為該資料庫建立新的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="7af09-157">However, if the old log file is not found and if the database was shut down cleanly and has no active log chain, the attach operation attempts to build a new log file for the database.</span></span>  
  
-   <span data-ttu-id="7af09-158">如果附加的主要資料檔案是唯讀的，則 [!INCLUDE[ssDE](../../includes/ssnoversion-md.md)] 無法更新儲存在主要檔案中的記錄檔位置。</span><span class="sxs-lookup"><span data-stu-id="7af09-158">If the primary data file being attached is read-only, the [!INCLUDE[ssDE](../../includes/ssnoversion-md.md)] cannot update the log location stored in the primary file.</span></span>  
  
  
  
###  <a name="metadata-changes-on-attaching-a-database"></a><a name="Metadata"></a> <span data-ttu-id="7af09-159">附加資料庫時的中繼資料變更</span><span class="sxs-lookup"><span data-stu-id="7af09-159">Metadata Changes on Attaching a Database</span></span>  
 <span data-ttu-id="7af09-160">卸離後再重新附加唯讀資料庫時，會遺失目前差異基底的備份資訊。</span><span class="sxs-lookup"><span data-stu-id="7af09-160">When a read-only database is detached and then reattached, the backup information about the current differential base is lost.</span></span> <span data-ttu-id="7af09-161">*「差異基底」* (Differential Base) 是資料庫或資料庫之檔案或檔案群組子集中所有資料的最新完整備份。</span><span class="sxs-lookup"><span data-stu-id="7af09-161">The *differential base* is the most recent full backup of all the data in the database or in a subset of the files or filegroups of the database.</span></span> <span data-ttu-id="7af09-162">如果沒有基底備份資訊， **master** 資料庫就會變成無法與唯讀資料庫同步處理，而之後所採用的差異備份可能會提供非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="7af09-162">Without the base-backup information, the **master** database becomes unsynchronized with the read-only database, so differential backups taken thereafter may provide unexpected results.</span></span> <span data-ttu-id="7af09-163">因此，如果搭配唯讀資料庫使用差異備份，重新附加資料庫後，應該利用完整備份來建立新的差異基底。</span><span class="sxs-lookup"><span data-stu-id="7af09-163">Therefore, if you are using differential backups with a read-only database, you should establish a new differential base by taking a full backup after you reattach the database.</span></span> <span data-ttu-id="7af09-164">如需差異備份的相關資訊，請參閱[差異備份 &#40;SQL Server&#41;](../backup-restore/differential-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7af09-164">For information about differential backups, see [Differential Backups &#40;SQL Server&#41;](../backup-restore/differential-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="7af09-165">附加時會啟動資料庫。</span><span class="sxs-lookup"><span data-stu-id="7af09-165">On attach, database startup occurs.</span></span> <span data-ttu-id="7af09-166">一般來說，附加資料庫時，會將資料庫設定為先前卸離或複製時的相同狀態。</span><span class="sxs-lookup"><span data-stu-id="7af09-166">Generally, attaching a database places it in the same state that it was in when it was detached or copied.</span></span> <span data-ttu-id="7af09-167">不過，附加與卸離作業會停用資料庫的跨資料庫擁有權鏈結。</span><span class="sxs-lookup"><span data-stu-id="7af09-167">However, attach-and-detach operations both disable cross-database ownership chaining for the database.</span></span> <span data-ttu-id="7af09-168">如需如何啟用鏈結的相關資訊，請參閱 [跨資料庫擁有權鏈結伺服器組態選項](../../database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="7af09-168">For information about how to enable chaining, see [cross db ownership chaining Server Configuration Option](../../database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option.md).</span></span> <span data-ttu-id="7af09-169">同時，每當附加資料庫時，TRUSTWORTHY 都會設為 OFF。</span><span class="sxs-lookup"><span data-stu-id="7af09-169">Also, TRUSTWORTHY is set to OFF whenever the database is attached.</span></span> <span data-ttu-id="7af09-170">如需如何將 TRUSTWORTHY 設成 ON 的資訊，請參閱 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7af09-170">For information about how to set TRUSTWORTHY to ON, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
### <a name="backup-and-restore-and-attach"></a><span data-ttu-id="7af09-171">備份和還原與附加</span><span class="sxs-lookup"><span data-stu-id="7af09-171">Backup and Restore and Attach</span></span>  
 <span data-ttu-id="7af09-172">就像任何完全或部分離線的資料庫一樣，內含還原中檔案的資料庫是無法附加的。</span><span class="sxs-lookup"><span data-stu-id="7af09-172">Like any database that is fully or partially offline, a database with restoring files cannot be attached.</span></span> <span data-ttu-id="7af09-173">如果停止還原順序，則可以附加資料庫。</span><span class="sxs-lookup"><span data-stu-id="7af09-173">If you stop the restore sequence, you can attach the database.</span></span> <span data-ttu-id="7af09-174">然後，還是可以重新啟動還原順序。</span><span class="sxs-lookup"><span data-stu-id="7af09-174">Then, you can restart the restore sequence.</span></span>  
  
###  <a name="attaching-a-database-to-another-server-instance"></a><a name="OtherServerInstance"></a> <span data-ttu-id="7af09-175">將資料庫附加至另一個伺服器執行個體</span><span class="sxs-lookup"><span data-stu-id="7af09-175">Attaching a Database to Another Server Instance</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7af09-176">由較新版本 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所建立的資料庫無法附加在舊版本中。</span><span class="sxs-lookup"><span data-stu-id="7af09-176">A database created by a more recent version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be attached in earlier versions.</span></span>  
  
 <span data-ttu-id="7af09-177">將資料庫附加至另一個伺服器執行個體時，為了提供一致的經驗給使用者和應用程式，您可能會需要在其他伺服器執行個體上為資料庫重新建立部分或所有中繼資料，例如登入和作業。</span><span class="sxs-lookup"><span data-stu-id="7af09-177">When you attach a database onto another server instance, to provide a consistent experience to users and applications, you might have to re-create some or all of the metadata for the database, such as logins and jobs, on the other server instance.</span></span> <span data-ttu-id="7af09-178">如需詳細資訊，請參閱 [在另一個伺服器執行個體上提供可用的資料庫時，管理中繼資料 &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7af09-178">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="7af09-179">相關工作</span><span class="sxs-lookup"><span data-stu-id="7af09-179">Related Tasks</span></span>  
 <span data-ttu-id="7af09-180">**若要卸離資料庫**</span><span class="sxs-lookup"><span data-stu-id="7af09-180">**To detach a database**</span></span>  
  
-   [<span data-ttu-id="7af09-181">sp_detach_db &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7af09-181">sp_detach_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)  
  
-   [<span data-ttu-id="7af09-182">卸離資料庫</span><span class="sxs-lookup"><span data-stu-id="7af09-182">Detach a Database</span></span>](detach-a-database.md)  
  
 <span data-ttu-id="7af09-183">**若要附加資料庫**</span><span class="sxs-lookup"><span data-stu-id="7af09-183">**To attach a database**</span></span>  
  
-   [<span data-ttu-id="7af09-184">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7af09-184">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
-   [<span data-ttu-id="7af09-185">附加資料庫</span><span class="sxs-lookup"><span data-stu-id="7af09-185">Attach a Database</span></span>](attach-a-database.md)  
  
-   [<span data-ttu-id="7af09-186">sp_attach_db &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7af09-186">sp_attach_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-db-transact-sql)  
  
-   [<span data-ttu-id="7af09-187">sp_attach_single_file_db &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7af09-187">sp_attach_single_file_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql)  
  
 <span data-ttu-id="7af09-188">**使用卸離和附加作業來升級資料庫**</span><span class="sxs-lookup"><span data-stu-id="7af09-188">**To upgrade a database using detach and attach operations**</span></span>  
  
-   [<span data-ttu-id="7af09-189">使用卸離與附加來升級資料庫 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7af09-189">Upgrade a Database Using Detach and Attach &#40;Transact-SQL&#41;</span></span>](upgrade-a-database-using-detach-and-attach-transact-sql.md)  
  
 <span data-ttu-id="7af09-190">**使用卸離和附加作業來移動資料庫**</span><span class="sxs-lookup"><span data-stu-id="7af09-190">**To move a database using detach and attach operations**</span></span>  
  
-   [<span data-ttu-id="7af09-191">使用卸離與附加來移動資料庫 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7af09-191">Move a Database Using Detach and Attach &#40;Transact-SQL&#41;</span></span>](move-a-database-using-detach-and-attach-transact-sql.md)  
  
 <span data-ttu-id="7af09-192">**若要刪除資料庫快照集**</span><span class="sxs-lookup"><span data-stu-id="7af09-192">**To delete a database snapshot**</span></span>  
  
-   [<span data-ttu-id="7af09-193">卸除資料庫快照集 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7af09-193">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="7af09-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7af09-194">See Also</span></span>  
 [<span data-ttu-id="7af09-195">資料庫檔案與檔案群組</span><span class="sxs-lookup"><span data-stu-id="7af09-195">Database Files and Filegroups</span></span>](database-files-and-filegroups.md)  
  
  
