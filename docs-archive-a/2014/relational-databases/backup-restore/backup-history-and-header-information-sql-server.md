---
title: 備份記錄與標頭資訊 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup headers [SQL Server]
- history tables [SQL Server]
- file restores [SQL Server], status information
- backup sets [SQL Server], status information
- listing backed up databases
- status information [SQL Server], backups
- backing up [SQL Server], viewing backup sets
- restoring [SQL Server], history tables
- restoring databases [SQL Server], status information
- backups [SQL Server], status information
- headers [SQL Server]
- media headers [SQL Server]
- backup history tables [SQL Server]
- viewing backup information
- restoring files [SQL Server], viewing backup information
- restoring databases [SQL Server], history tables
- displaying backup information
- restoring files [SQL Server], status information
- historical information [SQL Server], backups
- database restores [SQL Server], history tables
- restore history tables [SQL Server]
- listing backed up files
ms.assetid: 799b9934-0ec2-4f43-960b-5c9653f18374
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ff1e75cc88e51de75af32bcd9d48860be52d5861
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710682"
---
# <a name="backup-history-and-header-information-sql-server"></a><span data-ttu-id="eb2a0-102">備份記錄與標頭資訊 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="eb2a0-102">Backup History and Header Information (SQL Server)</span></span>
  <span data-ttu-id="eb2a0-103">在伺服器執行個體上的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份與還原作業的完整記錄都會儲存在 **msdb** 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-103">A complete history of all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore operations on a server instance is stored in the **msdb** database.</span></span> <span data-ttu-id="eb2a0-104">本主題介紹備份與還原記錄資料表，以及用於存取備份記錄的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-104">This topic introduces the backup and restore history tables and also the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that are used to access backup history.</span></span> <span data-ttu-id="eb2a0-105">本主題也會討論何時列出資料庫和交易記錄檔最有用，以及媒體標頭資訊與備份標頭資訊這兩者的使用時機。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-105">The topic also discusses when listing database and transaction log files is useful and when to use media-header information compared to when to use backup-header information.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="eb2a0-106">若要管理遺失備份和還原記錄最近變更的風險，請經常備份 **msdb** 。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-106">To manage the risk of losing recent changes to your backup and restore history, back up **msdb** frequently.</span></span> <span data-ttu-id="eb2a0-107">如需必須備份哪些系統資料庫的相關資訊，請參閱[系統資料庫的備份與還原 &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-107">For information about which of the system databases you must back up, see [Back Up and Restore of System Databases &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md).</span></span>  
  
 <span data-ttu-id="eb2a0-108">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="eb2a0-108">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="eb2a0-109">備份與還原記錄資料表</span><span class="sxs-lookup"><span data-stu-id="eb2a0-109">Backup and Restore History Tables</span></span>](#BnRHistoryTables)  
  
-   [<span data-ttu-id="eb2a0-110">存取備份記錄的 Transact-SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="eb2a0-110">Transact-SQL Statements for Accessing Backup History</span></span>](#TsqlStatementsForBackupHistory)  
  
-   [<span data-ttu-id="eb2a0-111">資料庫和交易記錄檔</span><span class="sxs-lookup"><span data-stu-id="eb2a0-111">Database and Transaction Log Files</span></span>](#ListDbTlogFiles)  
  
-   [<span data-ttu-id="eb2a0-112">媒體標頭資訊</span><span class="sxs-lookup"><span data-stu-id="eb2a0-112">Media-Header Information</span></span>](#MediaHeader)  
  
-   [<span data-ttu-id="eb2a0-113">備份標頭資訊</span><span class="sxs-lookup"><span data-stu-id="eb2a0-113">Backup-Header Information</span></span>](#BackupHeader)  
  
-   [<span data-ttu-id="eb2a0-114">媒體標頭與備份標頭資訊的比較</span><span class="sxs-lookup"><span data-stu-id="eb2a0-114">Comparison of Media-Header and Backup-Header Information</span></span>](#CompareMediaHeaderBackupHeader)  
  
-   [<span data-ttu-id="eb2a0-115">備份驗證</span><span class="sxs-lookup"><span data-stu-id="eb2a0-115">Backup Verification</span></span>](#Verification)  
  
-   [<span data-ttu-id="eb2a0-116">相關工作</span><span class="sxs-lookup"><span data-stu-id="eb2a0-116">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="backup-and-restore-history-tables"></a><a name="BnRHistoryTables"></a> <span data-ttu-id="eb2a0-117">備份與還原記錄資料表</span><span class="sxs-lookup"><span data-stu-id="eb2a0-117">Backup and Restore History Tables</span></span>  
 <span data-ttu-id="eb2a0-118">此章節介紹儲存 **msdb** 系統資料庫中的備份及還原中繼資料的歷史記錄資料表。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-118">This section introduces the history tables that store backup and restore metadata in the **msdb** system database.</span></span>  
  
|<span data-ttu-id="eb2a0-119">記錄資料表</span><span class="sxs-lookup"><span data-stu-id="eb2a0-119">History table</span></span>|<span data-ttu-id="eb2a0-120">描述</span><span class="sxs-lookup"><span data-stu-id="eb2a0-120">Description</span></span>|  
|-------------------|-----------------|  
|[<span data-ttu-id="eb2a0-121">backupfile</span><span class="sxs-lookup"><span data-stu-id="eb2a0-121">backupfile</span></span>](/sql/relational-databases/system-tables/backupfile-transact-sql)|<span data-ttu-id="eb2a0-122">包含備份的每一個資料檔或記錄檔的資料行。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-122">Contains one row for each data or log file that is backed up.</span></span>|  
|[<span data-ttu-id="eb2a0-123">backupfilegroup</span><span class="sxs-lookup"><span data-stu-id="eb2a0-123">backupfilegroup</span></span>](/sql/relational-databases/system-tables/backupfilegroup-transact-sql)|<span data-ttu-id="eb2a0-124">包含備份組中每一個檔案群組的資料列。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-124">Contains a row for each filegroup in a backup set.</span></span>|  
|[<span data-ttu-id="eb2a0-125">backupmediafamily</span><span class="sxs-lookup"><span data-stu-id="eb2a0-125">backupmediafamily</span></span>](/sql/relational-databases/system-tables/backupmediafamily-transact-sql)|<span data-ttu-id="eb2a0-126">針對每個媒體家族，各包含一個資料列。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-126">Contains one row for each media family.</span></span> <span data-ttu-id="eb2a0-127">如果媒體家族位於鏡像媒體集中，則在這個媒體集中，這個家族的每個鏡像都會各有一個個別的資料列。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-127">If a media family resides in a mirrored media set, the family has a separate row for each mirror in the media set.</span></span>|  
|[<span data-ttu-id="eb2a0-128">backupmediaset</span><span class="sxs-lookup"><span data-stu-id="eb2a0-128">backupmediaset</span></span>](/sql/relational-databases/system-tables/backupmediaset-transact-sql)|<span data-ttu-id="eb2a0-129">每個備份組各含一個資料列。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-129">Contains one row for each backup media set.</span></span>|  
|[<span data-ttu-id="eb2a0-130">backupset</span><span class="sxs-lookup"><span data-stu-id="eb2a0-130">backupset</span></span>](/sql/relational-databases/system-tables/backupset-transact-sql)|<span data-ttu-id="eb2a0-131">每個備份組各含一個資料列。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-131">Contains a row for each backup set.</span></span>|  
|[<span data-ttu-id="eb2a0-132">restorefile</span><span class="sxs-lookup"><span data-stu-id="eb2a0-132">restorefile</span></span>](/sql/relational-databases/system-tables/restorefile-transact-sql)|<span data-ttu-id="eb2a0-133">針對每個還原的檔案，各包含一個資料列。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-133">Contains one row for each restored file.</span></span> <span data-ttu-id="eb2a0-134">這包括檔案群組名稱間接還原的檔案。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-134">This includes files restored indirectly by filegroup name.</span></span>|  
|[<span data-ttu-id="eb2a0-135">restorefilegroup</span><span class="sxs-lookup"><span data-stu-id="eb2a0-135">restorefilegroup</span></span>](/sql/relational-databases/system-tables/restorefilegroup-transact-sql)|<span data-ttu-id="eb2a0-136">針對每個還原的檔案群組，各包含一個資料列。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-136">Contains one row for each restored filegroup.</span></span>|  
|[<span data-ttu-id="eb2a0-137">restorehistory</span><span class="sxs-lookup"><span data-stu-id="eb2a0-137">restorehistory</span></span>](/sql/relational-databases/system-tables/restorehistory-transact-sql)|<span data-ttu-id="eb2a0-138">每項還原作業都有一個資料列。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-138">Contains one row for each restore operation.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="eb2a0-139">執行還原時，會修改備份記錄資料表和還原記錄資料表。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-139">When a restore is performed, backup history tables and restore history tables are modified.</span></span>  
  
##  <a name="transact-sql-statements-for-accessing-backup-history"></a><a name="TsqlStatementsForBackupHistory"></a> <span data-ttu-id="eb2a0-140">存取備份記錄的 Transact-SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="eb2a0-140">Transact-SQL Statements for Accessing Backup History</span></span>  
 <span data-ttu-id="eb2a0-141">還原資訊陳述式會與儲存在某些備份記錄資料表中的資訊對應。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-141">The restore information statements correspond with information stored in certain backup history tables.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="eb2a0-142">RESTORE FILELISTONLY、RESTORE HEADERONLY、RESTORE LABELONLY 和 RESTORE VERIFYONLY Transact-SQL 陳述式需要 CREATE DATABASE 權限。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-142">The RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY, and RESTORE VERIFYONLY Transact-SQL statements require CREATE DATABASE permission.</span></span> <span data-ttu-id="eb2a0-143">與舊版相較，這項需求更能完整地保障備份檔案及備份資訊的安全。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-143">This requirement secures your backup files and protects your backup information more fully than in previous versions.</span></span> <span data-ttu-id="eb2a0-144">如需這個權限的相關資訊，請參閱 [GRANT 資料庫權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-144">For information about this permission, see [GRANT Database Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).</span></span>  
  
|<span data-ttu-id="eb2a0-145">資訊陳述式</span><span class="sxs-lookup"><span data-stu-id="eb2a0-145">Information statement</span></span>|<span data-ttu-id="eb2a0-146">備份記錄資料表</span><span class="sxs-lookup"><span data-stu-id="eb2a0-146">Backup history table</span></span>|<span data-ttu-id="eb2a0-147">描述</span><span class="sxs-lookup"><span data-stu-id="eb2a0-147">Description</span></span>|  
|---------------------------|--------------------------|-----------------|  
|[<span data-ttu-id="eb2a0-148">RESTORE FILELISTONLY</span><span class="sxs-lookup"><span data-stu-id="eb2a0-148">RESTORE FILELISTONLY</span></span>](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)|[<span data-ttu-id="eb2a0-149">backupfile</span><span class="sxs-lookup"><span data-stu-id="eb2a0-149">backupfile</span></span>](/sql/relational-databases/system-tables/backupfile-transact-sql)|<span data-ttu-id="eb2a0-150">傳回結果集，其中會有資料庫清單與包含在指定備份組中的記錄。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-150">Returns a result set that has a list of the database and log files that are contained in the specified backup set.</span></span><br /><br /> <span data-ttu-id="eb2a0-151">如需詳細資訊，請參閱本主題稍後的「列出資料庫與交易記錄檔」。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-151">For more information, see "Listing Database and Transaction Log Files," later in this topic.</span></span>|  
|[<span data-ttu-id="eb2a0-152">RESTORE HEADERONLY</span><span class="sxs-lookup"><span data-stu-id="eb2a0-152">RESTORE HEADERONLY</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)|[<span data-ttu-id="eb2a0-153">backupset</span><span class="sxs-lookup"><span data-stu-id="eb2a0-153">backupset</span></span>](/sql/relational-databases/system-tables/backupset-transact-sql)|<span data-ttu-id="eb2a0-154">擷取特定備份裝置上，所有備份組的所有備份前置資料。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-154">Retrieves all the backup header information for all backup sets on a particular backup device.</span></span> <span data-ttu-id="eb2a0-155">執行 RESTORE HEADERONLY 的結果是結果集。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-155">The result from executing RESTORE HEADERONLY is a result set.</span></span><br /><br /> <span data-ttu-id="eb2a0-156">如需詳細資訊，請參閱本主題稍後的「檢視備份標頭資訊」。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-156">For more information, see "Viewing the Backup-Header Information," later in this topic.</span></span>|  
|[<span data-ttu-id="eb2a0-157">RESTORE LABELONLY</span><span class="sxs-lookup"><span data-stu-id="eb2a0-157">RESTORE LABELONLY</span></span>](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)|[<span data-ttu-id="eb2a0-158">backupmediaset</span><span class="sxs-lookup"><span data-stu-id="eb2a0-158">backupmediaset</span></span>](/sql/relational-databases/system-tables/backupmediaset-transact-sql)|<span data-ttu-id="eb2a0-159">傳回結果集，其中會包含指定備份裝置上之備份媒體的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-159">Returns a result set that contains information about the backup media on a specified backup device.</span></span><br /><br /> <span data-ttu-id="eb2a0-160">如需詳細資訊，請參閱本主題稍後的「檢視媒體標頭資訊」。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-160">For more information, see "Viewing the Media-Header Information," later in this topic.</span></span>|  
  
##  <a name="database-and-transaction-log-files"></a><a name="ListDbTlogFiles"></a> <span data-ttu-id="eb2a0-161">資料庫和交易記錄檔</span><span class="sxs-lookup"><span data-stu-id="eb2a0-161">Database and Transaction Log Files</span></span>  
 <span data-ttu-id="eb2a0-162">在列出備份中的資料庫與交易記錄檔時所顯示的資訊包括：邏輯名稱、實體名稱、檔案類型 (資料庫或記錄)、檔案群組成員資格、檔案大小 (以位元組為單位)、允許的檔案大小上限以及預先定義的檔案成長大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-162">Information that is displayed when the database and transaction log files are listed in a backup includes the logical name, physical name, file type (database or log), filegroup membership, file size (in bytes), the maximum allowed file size, and the predefined file growth size (in bytes).</span></span> <span data-ttu-id="eb2a0-163">在下列狀況中，這些資訊有助於在還原資料庫備份前判斷資料庫備份中的檔案名稱：</span><span class="sxs-lookup"><span data-stu-id="eb2a0-163">This information is useful, in the following situations, to determine the names of the files in a database backup before you restore the database backup:</span></span>  
  
-   <span data-ttu-id="eb2a0-164">損失了一部磁碟機，內含某資料庫的一或多個檔案。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-164">You have lost a disk drive that contains one or more of the files for a database.</span></span>  
  
     <span data-ttu-id="eb2a0-165">您可以列出資料庫備份中的檔案，以判斷哪些檔案受到影響，然後在還原整個資料庫時將那些檔案還原到別的磁碟機，或者只是還原那些檔案，另外再套用備份資料庫後所建的任何交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-165">You can list the files in the database backup to determine which files were affected, and then restore those files onto a different drive when you restore the whole database; or restore just those files and apply any transaction log backups created since the database was backed up.</span></span>  
  
-   <span data-ttu-id="eb2a0-166">要將資料庫從一部伺服器還原至別的伺服器，但該伺服器上沒有目錄結構與磁碟機對應。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-166">You are restoring a database from one server onto another server, but the directory structure and drive mapping does not exist on the server.</span></span>  
  
     <span data-ttu-id="eb2a0-167">列出備份中的檔案能讓您判斷哪些檔案受到影響。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-167">Listing the files in the backup let you determine which files are affected.</span></span> <span data-ttu-id="eb2a0-168">例如，備份包含需要還原到磁碟機 E 的檔案，但是目的地伺服器並沒有磁碟機 E。當您還原這個檔案時，就必須將它重新放置到其他位置，如磁碟機 Z。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-168">For example, the backup contains a file that it has to restore to drive E, but the destination server does not have a drive E. The file must be relocated to another location, such as drive Z, when the file is restored.</span></span>  
  
##  <a name="media-header-information"></a><a name="MediaHeader"></a> <span data-ttu-id="eb2a0-169">媒體標頭資訊</span><span class="sxs-lookup"><span data-stu-id="eb2a0-169">Media-Header Information</span></span>  
 <span data-ttu-id="eb2a0-170">檢視媒體標頭會顯示關於媒體本身的資訊，而非媒體上備份的資訊。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-170">Viewing the media header displays information about the media itself, instead of about the backups on the media.</span></span> <span data-ttu-id="eb2a0-171">顯示的媒體標頭資訊包括：媒體名稱、描述、建立媒體標頭的軟體名稱以及寫入媒體標頭的日期。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-171">Media header information that is displayed includes the media name, description, name of the software that created the media header, and the date the media header was written.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eb2a0-172">檢視媒體標頭會很快。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-172">Viewing the media header is quick.</span></span>  
  
 <span data-ttu-id="eb2a0-173">如需詳細資訊，請參閱本主題後面的 [媒體標頭與備份標頭資訊的比較](#CompareMediaHeaderBackupHeader)。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-173">For more information, see [Comparison of Media-Header and Backup-Header Information](#CompareMediaHeaderBackupHeader), later in this topic.</span></span>  
  
##  <a name="backup-header-information"></a><a name="BackupHeader"></a> <span data-ttu-id="eb2a0-174">備份標頭資訊</span><span class="sxs-lookup"><span data-stu-id="eb2a0-174">Backup-Header Information</span></span>  
 <span data-ttu-id="eb2a0-175">檢視備份標頭會顯示有關媒體上所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 與非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份組的資訊。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-175">Viewing the backup header displays information about all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup sets on the media.</span></span> <span data-ttu-id="eb2a0-176">顯示的資訊包括使用的備份裝置類型、備份類型 (例如資料庫、交易、檔案或差異資料庫)，以及備份開始與停止的日期/時間資訊。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-176">Information that is displayed includes the types of backup devices that are used, the types of backup (for example, database, transaction, file, or differential database), and backup start and stop date/time information.</span></span> <span data-ttu-id="eb2a0-177">當您必須決定要還原磁帶上的哪個備份組，或包含在媒體上的備份時，這項資訊會非常有用。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-177">This information is useful when you have to determine which backup set on the tape to restore, or the backups that are contained on the media.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eb2a0-178">對於高容量的磁帶而言，檢視備份標頭資訊可能很花時間，因為必須掃描整個媒體，才能顯示有關媒體上每個備份的資訊。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-178">Viewing backup header information can take a long time for high-capacity tapes, because the whole media must be scanned to display information about each backup on the media.</span></span>  
  
 <span data-ttu-id="eb2a0-179">如需詳細資訊，請參閱本主題後面的 [媒體標頭與備份標頭資訊的比較](#CompareMediaHeaderBackupHeader)。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-179">For more information, see [Comparison of Media-Header and Backup-Header Information](#CompareMediaHeaderBackupHeader), later in this topic.</span></span>  
  
### <a name="which-backup-set-to-restore"></a><span data-ttu-id="eb2a0-180">要還原的備份組</span><span class="sxs-lookup"><span data-stu-id="eb2a0-180">Which Backup Set to Restore</span></span>  
 <span data-ttu-id="eb2a0-181">您可以使用備份標頭中的資訊來識別要還原的備份組。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-181">You can use information in the backup header to identify which backup set to restore.</span></span> <span data-ttu-id="eb2a0-182">Database Engine 會針對備份媒體上的每個備份組編號。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-182">The Database Engine numbers each backup set on the backup media.</span></span> <span data-ttu-id="eb2a0-183">這樣可讓您利用備份組在媒體上的位置，識別您要還原的備份組。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-183">This lets you identify the backup set you want to restore by using its position on the media.</span></span> <span data-ttu-id="eb2a0-184">例如，下列媒體包含三個備份組。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-184">For example, the following media contains three backup sets.</span></span>  
  
 <span data-ttu-id="eb2a0-185">![包含 SQL Server 備份集的備份媒體](../../database-engine/media/bnr-media-backup-sets.gif "包含 SQL Server 備份集的備份媒體")</span><span class="sxs-lookup"><span data-stu-id="eb2a0-185">![Backup media containing SQL Server backup sets](../../database-engine/media/bnr-media-backup-sets.gif "Backup media containing SQL Server backup sets")</span></span>  
  
 <span data-ttu-id="eb2a0-186">若要還原特定的備份組，可指定所要還原的備份組位置編號。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-186">To restore a specific backup set, specify the position number of the backup set you want to restore.</span></span> <span data-ttu-id="eb2a0-187">例如，若要還原第二個備份組，請指定 2 當做要還原的備份組。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-187">For example, to restore the second backup set, specify 2 as the backup set to restore.</span></span>  
  
##  <a name="comparison-of-media-header-and-backup-header-information"></a><a name="CompareMediaHeaderBackupHeader"></a> <span data-ttu-id="eb2a0-188">媒體標頭與備份標頭資訊的比較</span><span class="sxs-lookup"><span data-stu-id="eb2a0-188">Comparison of Media-Header and Backup-Header Information</span></span>  
 <span data-ttu-id="eb2a0-189">下圖提供的範例顯示檢視備份標頭與媒體標頭資訊之間的差異。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-189">The following illustration provides an example of the differences between viewing backup-header and media-header information.</span></span> <span data-ttu-id="eb2a0-190">取得媒體標頭時，只需從磁帶的開頭擷取資訊。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-190">Obtaining the media header requires retrieving information from only the start of the tape.</span></span> <span data-ttu-id="eb2a0-191">取得備份標頭時，則必須掃描整捲磁帶來查看每個備份組的標頭。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-191">Obtaining the backup header requires scanning the whole tape to look at the header of every backup set.</span></span>  
  
 <span data-ttu-id="eb2a0-192">![包含三個 SQL Server 備份集的媒體集](../../database-engine/media/bnr-media-label.gif "包含三個 SQL Server 備份集的媒體集")</span><span class="sxs-lookup"><span data-stu-id="eb2a0-192">![Media set containing three SQL Server backup sets](../../database-engine/media/bnr-media-label.gif "Media set containing three SQL Server backup sets")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eb2a0-193">使用具有多個媒體家族的媒體集時，會將媒體標頭與備份組寫入所有媒體家族。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-193">When you use media sets that have multiple media families, the media header and backup set are written to all media families.</span></span> <span data-ttu-id="eb2a0-194">因此，只需要針對這些報表作業提供單一媒體家族。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-194">Therefore, you only have to provide a single media family for these reporting operations.</span></span>  
  
 <span data-ttu-id="eb2a0-195">如需有關如何檢視媒體標頭的詳細資訊，請參閱本主題前面的「檢視媒體標頭資訊」。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-195">For information about how to view the media-header, see "Viewing the Media-Header Information," earlier in this topic.</span></span>  
  
 <span data-ttu-id="eb2a0-196">如需有關如何檢視備份裝置上所有備份組之備份標頭資訊的詳細資訊，請參閱本主題前面的＜檢視備份標頭資訊＞。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-196">For information about how to view the backup header information for all backup sets on a backup device, see "Viewing the Backup-Header Information," earlier in this topic.</span></span>  
  
##  <a name="backup-verification"></a><a name="Verification"></a> <span data-ttu-id="eb2a0-197">備份驗證</span><span class="sxs-lookup"><span data-stu-id="eb2a0-197">Backup Verification</span></span>  
 <span data-ttu-id="eb2a0-198">驗證備份不是必要的步驟，但仍是很有用的作法。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-198">Although not required, verifying a backup is a useful practice.</span></span> <span data-ttu-id="eb2a0-199">驗證備份會檢查備份實際上是否完整無缺，以確定備份中的所有檔案都可以讀取也可以還原，並確定在您需要時可以還原備份。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-199">Verifying a backup checks that the backup is intact physically, to ensure that all the files in the backup are readable and can be restored, and that you can restore your backup in the event you need to use it.</span></span> <span data-ttu-id="eb2a0-200">您必須了解，驗證備份並不會驗證備份上的資料結構。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-200">It is important to understand that verifying a backup does not verify the structure of the data on the backup.</span></span> <span data-ttu-id="eb2a0-201">不過，如果是使用 WITH CHECKSUMS 所建立的備份，則使用 WITH CHECKSUMS 來驗證備份可提供適當的指示，指出備份中資料的可靠性。</span><span class="sxs-lookup"><span data-stu-id="eb2a0-201">However, if the backup was created using WITH CHECKSUMS, verifying the backup using WITH CHECKSUMS can provide a good indication of the reliability of the data on the backup.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="eb2a0-202">相關工作</span><span class="sxs-lookup"><span data-stu-id="eb2a0-202">Related Tasks</span></span>  
 <span data-ttu-id="eb2a0-203">**從備份與還原記錄資料表中刪除舊的資料列**</span><span class="sxs-lookup"><span data-stu-id="eb2a0-203">**To delete old rows from backup and restore history tables**</span></span>  
  
-   [<span data-ttu-id="eb2a0-204">sp_delete_backuphistory &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-204">sp_delete_backuphistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)  
  
 <span data-ttu-id="eb2a0-205">**從備份與還原記錄資料表中刪除特定資料庫的所有資料列**</span><span class="sxs-lookup"><span data-stu-id="eb2a0-205">**To delete all rows for a specific database from backup and restore history tables**</span></span>  
  
-   [<span data-ttu-id="eb2a0-206">sp_delete_database_backuphistory &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-206">sp_delete_database_backuphistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-database-backuphistory-transact-sql)  
  
 <span data-ttu-id="eb2a0-207">**檢視備份組中的資料與記錄檔**</span><span class="sxs-lookup"><span data-stu-id="eb2a0-207">**To view the data and log files in a backup set**</span></span>  
  
-   [<span data-ttu-id="eb2a0-208">RESTORE FILELISTONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-208">RESTORE FILELISTONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)  
  
-   <span data-ttu-id="eb2a0-209"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadFileList%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="eb2a0-209"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadFileList%2A> (SMO)</span></span>  
  
 <span data-ttu-id="eb2a0-210">**檢視媒體標頭資訊**</span><span class="sxs-lookup"><span data-stu-id="eb2a0-210">**To view media header information**</span></span>  
  
-   [<span data-ttu-id="eb2a0-211">RESTORE LABELONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-211">RESTORE LABELONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)  
  
-   [<span data-ttu-id="eb2a0-212">檢視邏輯備份裝置的屬性和內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-212">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="eb2a0-213">檢視備份磁帶或檔案的內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-213">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   <span data-ttu-id="eb2a0-214"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadMediaHeader%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="eb2a0-214"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadMediaHeader%2A> (SMO)</span></span>  
  
 <span data-ttu-id="eb2a0-215">**檢視備份標頭資訊**</span><span class="sxs-lookup"><span data-stu-id="eb2a0-215">**To view backup header information**</span></span>  
  
-   [<span data-ttu-id="eb2a0-216">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-216">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
-   [<span data-ttu-id="eb2a0-217">檢視備份磁帶或檔案的內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-217">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="eb2a0-218">檢視邏輯備份裝置的屬性和內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-218">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   <span data-ttu-id="eb2a0-219"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadBackupHeader%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="eb2a0-219"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadBackupHeader%2A> (SMO)</span></span>  
  
 <span data-ttu-id="eb2a0-220">**從備份與還原記錄資料表中刪除舊的資料列**</span><span class="sxs-lookup"><span data-stu-id="eb2a0-220">**To delete old rows from backup and restore history tables**</span></span>  
  
-   [<span data-ttu-id="eb2a0-221">sp_delete_backuphistory &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-221">sp_delete_backuphistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)  
  
 <span data-ttu-id="eb2a0-222">**從備份與還原記錄資料表中刪除特定資料庫的所有資料列**</span><span class="sxs-lookup"><span data-stu-id="eb2a0-222">**To delete all rows for a specific database from backup and restore history tables**</span></span>  
  
-   [<span data-ttu-id="eb2a0-223">sp_delete_database_backuphistory &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-223">sp_delete_database_backuphistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-database-backuphistory-transact-sql)  
  
 <span data-ttu-id="eb2a0-224">**檢視媒體標頭資訊**</span><span class="sxs-lookup"><span data-stu-id="eb2a0-224">**To view media header information**</span></span>  
  
-   [<span data-ttu-id="eb2a0-225">RESTORE LABELONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-225">RESTORE LABELONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)  
  
-   [<span data-ttu-id="eb2a0-226">檢視邏輯備份裝置的屬性和內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-226">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="eb2a0-227">檢視備份磁帶或檔案的內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-227">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   <span data-ttu-id="eb2a0-228"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadMediaHeader%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="eb2a0-228"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadMediaHeader%2A> (SMO)</span></span>  
  
 <span data-ttu-id="eb2a0-229">**檢視備份標頭資訊**</span><span class="sxs-lookup"><span data-stu-id="eb2a0-229">**To view backup header information**</span></span>  
  
-   [<span data-ttu-id="eb2a0-230">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-230">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
-   [<span data-ttu-id="eb2a0-231">檢視備份磁帶或檔案的內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-231">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="eb2a0-232">檢視邏輯備份裝置的屬性和內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-232">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   <span data-ttu-id="eb2a0-233"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadBackupHeader%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="eb2a0-233"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadBackupHeader%2A> (SMO)</span></span>  
  
 <span data-ttu-id="eb2a0-234">**若要檢視備份組中的檔案**</span><span class="sxs-lookup"><span data-stu-id="eb2a0-234">**To view the files in a backup set**</span></span>  
  
-   [<span data-ttu-id="eb2a0-235">檢視備份組中的資料和記錄檔 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-235">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [<span data-ttu-id="eb2a0-236">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-236">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
 <span data-ttu-id="eb2a0-237">**驗證備份**</span><span class="sxs-lookup"><span data-stu-id="eb2a0-237">**To verify a backup**</span></span>  
  
-   [<span data-ttu-id="eb2a0-238">RESTORE VERIFYONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-238">RESTORE VERIFYONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)  
  
-   <span data-ttu-id="eb2a0-239"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlVerify%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="eb2a0-239"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlVerify%2A> (SMO)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb2a0-240">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb2a0-240">See Also</span></span>  
 <span data-ttu-id="eb2a0-241">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb2a0-241">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="eb2a0-242">[媒體集、媒體家族與備份組 &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="eb2a0-242">[Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span></span>  
 <span data-ttu-id="eb2a0-243">[備份裝置 &#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="eb2a0-243">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 <span data-ttu-id="eb2a0-244">[鏡像備份媒體集 &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="eb2a0-244">[Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) </span></span>  
 [<span data-ttu-id="eb2a0-245">備份和還原期間可能發生的媒體錯誤 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eb2a0-245">Possible Media Errors During Backup and Restore &#40;SQL Server&#41;</span></span>](possible-media-errors-during-backup-and-restore-sql-server.md)  
  
  
