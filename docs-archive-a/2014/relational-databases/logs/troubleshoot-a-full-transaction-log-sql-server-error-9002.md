---
title: 寫滿交易記錄疑難排解 (SQL Server 錯誤 9002) | Microsoft 文件
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], full
- troubleshooting [SQL Server], full transaction log
- 9002 (Database Engine error)
- transaction logs [SQL Server], truncation
- backing up transaction logs [SQL Server], full logs
- transaction logs [SQL Server], full log
- full transaction logs [SQL Server]
ms.assetid: 0f23aa84-475d-40df-bed3-c923f8c1b520
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d03e259bd0aff8fce02558dbe08efb56748493c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585381"
---
# <a name="troubleshoot-a-full-transaction-log-sql-server-error-9002"></a><span data-ttu-id="2b724-102">寫滿交易記錄疑難排解 (SQL Server 錯誤 9002)</span><span class="sxs-lookup"><span data-stu-id="2b724-102">Troubleshoot a Full Transaction Log (SQL Server Error 9002)</span></span>
  <span data-ttu-id="2b724-103">本主題將討論對於寫滿交易記錄的可能回應，並建議將來可採用的避免方法。</span><span class="sxs-lookup"><span data-stu-id="2b724-103">This topic discusses possible responses to a full transaction log and suggests how to avoid it in the future.</span></span> <span data-ttu-id="2b724-104">當交易記錄寫滿時， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 就會發出 9002 錯誤。</span><span class="sxs-lookup"><span data-stu-id="2b724-104">When the transaction log becomes full, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] issues a 9002 error.</span></span> <span data-ttu-id="2b724-105">此記錄可能會在資料庫處於線上或復原狀態時填滿。</span><span class="sxs-lookup"><span data-stu-id="2b724-105">The log can fill when the database is online or in recovery.</span></span> <span data-ttu-id="2b724-106">如果記錄已滿時，資料庫正在線上，則資料庫仍會保持在線上，但只能讀取並無法更新。</span><span class="sxs-lookup"><span data-stu-id="2b724-106">If the log fills while the database is online, the database remains online but can only be read, not updated.</span></span> <span data-ttu-id="2b724-107">如果此記錄是在復原期間填滿，則 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會將資料庫標示為 RESOURCE PENDING。</span><span class="sxs-lookup"><span data-stu-id="2b724-107">If the log fills during recovery, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] marks the database as RESOURCE PENDING.</span></span> <span data-ttu-id="2b724-108">不論是哪一種情況，使用者都必須採取動作，以便提供足夠的記錄空間。</span><span class="sxs-lookup"><span data-stu-id="2b724-108">In either case, user action is required to make log space available.</span></span>  
  
## <a name="responding-to-a-full-transaction-log"></a><span data-ttu-id="2b724-109">寫滿交易記錄的回應</span><span class="sxs-lookup"><span data-stu-id="2b724-109">Responding to a Full Transaction Log</span></span>  
 <span data-ttu-id="2b724-110">寫滿交易記錄的適當回應會部分根據導致記錄填滿的條件而定。</span><span class="sxs-lookup"><span data-stu-id="2b724-110">The appropriate response to a full transaction log depends partly on what condition or conditions caused the log to fill.</span></span> <span data-ttu-id="2b724-111">若要探索指定情況下無法進行記錄截斷的原因，請使用 **sys.database** 目錄檢視的 **log_reuse_wait** 和 **log_reuse_wait_desc** 資料行。</span><span class="sxs-lookup"><span data-stu-id="2b724-111">To discover what is preventing log truncation in a given case, use the **log_reuse_wait** and **log_reuse_wait_desc** columns of the **sys.database** catalog view.</span></span> <span data-ttu-id="2b724-112">如需詳細資訊，請參閱 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2b724-112">For more information, see [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql).</span></span> <span data-ttu-id="2b724-113">如需可能延遲記錄截斷之其他因素的描述，請參閱[交易記錄 &#40;SQL Server&#41;](the-transaction-log-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2b724-113">For descriptions of factors that can delay log truncation, see [The Transaction Log &#40;SQL Server&#41;](the-transaction-log-sql-server.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2b724-114">如果發生 9002 錯誤時資料庫處於復原狀態，請在解決問題後，使用 ALTER DATABASE *資料庫名稱* SET ONLINE 來復原資料庫。</span><span class="sxs-lookup"><span data-stu-id="2b724-114">If the database was in recovery when the 9002 error occurred, after resolving the problem, recover the database by using ALTER DATABASE *database_name* SET ONLINE.</span></span>  
  
 <span data-ttu-id="2b724-115">寫滿交易記錄的替代回應方式包括：</span><span class="sxs-lookup"><span data-stu-id="2b724-115">Alternatives for responding to a full transaction log include:</span></span>  
  
-   <span data-ttu-id="2b724-116">備份記錄。</span><span class="sxs-lookup"><span data-stu-id="2b724-116">Backing up the log.</span></span>  
  
-   <span data-ttu-id="2b724-117">釋出磁碟空間，使記錄可以自動成長。</span><span class="sxs-lookup"><span data-stu-id="2b724-117">Freeing disk space so that the log can automatically grow.</span></span>  
  
-   <span data-ttu-id="2b724-118">將記錄檔移動到空間足夠的磁碟機。</span><span class="sxs-lookup"><span data-stu-id="2b724-118">Moving the log file to a disk drive with sufficient space.</span></span>  
  
-   <span data-ttu-id="2b724-119">增加記錄檔的大小。</span><span class="sxs-lookup"><span data-stu-id="2b724-119">Increasing the size of a log file.</span></span>  
  
-   <span data-ttu-id="2b724-120">在不同的磁碟上加入記錄檔。</span><span class="sxs-lookup"><span data-stu-id="2b724-120">Adding a log file on a different disk.</span></span>  
  
-   <span data-ttu-id="2b724-121">完成或刪除長時間執行的交易。</span><span class="sxs-lookup"><span data-stu-id="2b724-121">Completing or killing a long-running transaction.</span></span>  
  
 <span data-ttu-id="2b724-122">這些替代方式將於下列各節中討論。</span><span class="sxs-lookup"><span data-stu-id="2b724-122">These alternatives are discussed in the following sections.</span></span> <span data-ttu-id="2b724-123">請選擇最適合您情況的回應。</span><span class="sxs-lookup"><span data-stu-id="2b724-123">Choose a response that fits your situation best.</span></span>  
  
### <a name="backing-up-the-log"></a><span data-ttu-id="2b724-124">備份記錄</span><span class="sxs-lookup"><span data-stu-id="2b724-124">Backing up the Log</span></span>  
 <span data-ttu-id="2b724-125">在完整復原模式或大量記錄復原模式下，如果最近尚未備份交易記錄，備份可能就是阻止記錄截斷的主因。</span><span class="sxs-lookup"><span data-stu-id="2b724-125">Under the full recovery model or bulk-logged recovery model, if the transaction log has not been backed up recently, backup might be what is preventing log truncation.</span></span> <span data-ttu-id="2b724-126">如果記錄從未備份過，您就必須建立兩個記錄備份，以便讓 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 將記錄截斷至上次備份的時間點。</span><span class="sxs-lookup"><span data-stu-id="2b724-126">If the log has never been backed up, you must create two log backups to permit the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to truncate the log to the point of the last backup.</span></span> <span data-ttu-id="2b724-127">截斷記錄可針對新記錄檔的記錄釋出空間。</span><span class="sxs-lookup"><span data-stu-id="2b724-127">Truncating the log frees space for new log records.</span></span> <span data-ttu-id="2b724-128">若要防止記錄檔再度被填滿，請經常備份記錄檔。</span><span class="sxs-lookup"><span data-stu-id="2b724-128">To keep the log from filling up again, take log backups frequently.</span></span>  
  
 <span data-ttu-id="2b724-129">**若要建立交易記錄備份**</span><span class="sxs-lookup"><span data-stu-id="2b724-129">**To create a transaction log backup**</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2b724-130">如果資料庫已損毀，請參閱[結尾記錄備份 &#40;SQL Server&#41;](../backup-restore/tail-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2b724-130">If the database is damaged, see [Tail-Log Backups &#40;SQL Server&#41;](../backup-restore/tail-log-backups-sql-server.md).</span></span>  
  
-   [<span data-ttu-id="2b724-131">備份交易記錄 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2b724-131">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](../backup-restore/back-up-a-transaction-log-sql-server.md)  
  
-   <span data-ttu-id="2b724-132"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="2b724-132"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span></span>  
  
### <a name="freeing-disk-space"></a><span data-ttu-id="2b724-133">釋出磁碟空間</span><span class="sxs-lookup"><span data-stu-id="2b724-133">Freeing Disk Space</span></span>  
 <span data-ttu-id="2b724-134">您可以透過刪除或移動其他檔案，在包含資料庫交易記錄檔的磁碟機上釋出磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="2b724-134">You might be able to free disk space on the disk drive that contains the transaction log file for the database by deleting or moving other files.</span></span> <span data-ttu-id="2b724-135">釋出的磁碟空間會讓復原系統自動加大記錄檔。</span><span class="sxs-lookup"><span data-stu-id="2b724-135">The freed disk space allows the recovery system to enlarge the log file automatically.</span></span>  
  
### <a name="moving-the-log-file-to-a-different-disk"></a><span data-ttu-id="2b724-136">將記錄檔移至不同的磁碟</span><span class="sxs-lookup"><span data-stu-id="2b724-136">Moving the Log File to a Different Disk</span></span>  
 <span data-ttu-id="2b724-137">如果無法在目前包含記錄檔的磁碟機上，釋出足夠的磁碟空間，請考慮將檔案移動到有足夠空間的其他磁碟機。</span><span class="sxs-lookup"><span data-stu-id="2b724-137">If you cannot free enough disk space on the drive that currently contains the log file, consider moving the file to another drive with sufficient space.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2b724-138">記錄檔絕不可放在壓縮檔案系統上。</span><span class="sxs-lookup"><span data-stu-id="2b724-138">Log files should never be placed on compressed file systems.</span></span>  
  
 <span data-ttu-id="2b724-139">**移動記錄檔**</span><span class="sxs-lookup"><span data-stu-id="2b724-139">**To move a log file**</span></span>  
  
-   [<span data-ttu-id="2b724-140">移動資料庫檔案</span><span class="sxs-lookup"><span data-stu-id="2b724-140">Move Database Files</span></span>](../databases/move-database-files.md)  
  
### <a name="increasing-the-size-of-a-log-file"></a><span data-ttu-id="2b724-141">增加記錄檔的大小</span><span class="sxs-lookup"><span data-stu-id="2b724-141">Increasing the Size of a Log File</span></span>  
 <span data-ttu-id="2b724-142">如果記錄磁碟上還有可用空間，您就可以增加記錄檔的大小。</span><span class="sxs-lookup"><span data-stu-id="2b724-142">If space is available on the log disk, you can increase the size of the log file.</span></span> <span data-ttu-id="2b724-143">記錄檔大小的最大值是每個記錄檔 2 TB。</span><span class="sxs-lookup"><span data-stu-id="2b724-143">The maximum size for log files is two terabytes (TB) per log file.</span></span>  
  
 <span data-ttu-id="2b724-144">**若要增加檔案大小**</span><span class="sxs-lookup"><span data-stu-id="2b724-144">**To increase the file size**</span></span>  
  
 <span data-ttu-id="2b724-145">如果已停用自動成長、資料庫在線上，而且磁碟上有足夠的可用空間，請執行下列其中一項動作：</span><span class="sxs-lookup"><span data-stu-id="2b724-145">If autogrow is disabled, the database is online, and sufficient space is available on the disk, either:</span></span>  
  
-   <span data-ttu-id="2b724-146">手動增加檔案大小以產生單一成長遞增。</span><span class="sxs-lookup"><span data-stu-id="2b724-146">Manually increase the file size to produce a single growth increment.</span></span>  
  
-   <span data-ttu-id="2b724-147">使用 ALTER DATABASE 陳述式，設定 FILEGROWTH 選項的非零成長遞增，藉以開啟自動成長。</span><span class="sxs-lookup"><span data-stu-id="2b724-147">Turn on autogrow by using the ALTER DATABASE statement to set a non-zero growth increment for the FILEGROWTH option.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2b724-148">無論是哪一種情況，如果已達到目前的大小限制，都需增加 MAXSIZE 值。</span><span class="sxs-lookup"><span data-stu-id="2b724-148">In either case, if the current size limit has been reached, increase the MAXSIZE value.</span></span>  
  
### <a name="adding-a-log-file-on-a-different-disk"></a><span data-ttu-id="2b724-149">在不同的磁碟上加入記錄檔</span><span class="sxs-lookup"><span data-stu-id="2b724-149">Adding a Log File on a Different Disk</span></span>  
 <span data-ttu-id="2b724-150">使用 ALTER DATABASE <database_name> ADD LOG FILE，在含有足夠空間的不同磁碟上加入資料庫的新記錄檔。</span><span class="sxs-lookup"><span data-stu-id="2b724-150">Add a new log file to the database on a different disk that has sufficient space by using ALTER DATABASE <database_name> ADD LOG FILE.</span></span>  
  
 <span data-ttu-id="2b724-151">**加入記錄檔**</span><span class="sxs-lookup"><span data-stu-id="2b724-151">**To add a log file**</span></span>  
  
-   [<span data-ttu-id="2b724-152">將資料或記錄檔加入資料庫</span><span class="sxs-lookup"><span data-stu-id="2b724-152">Add Data or Log Files to a Database</span></span>](../databases/add-data-or-log-files-to-a-database.md)  
  
## <a name="see-also"></a><span data-ttu-id="2b724-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b724-153">See Also</span></span>  
 <span data-ttu-id="2b724-154">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2b724-154">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="2b724-155">[管理交易記錄檔的大小](manage-the-size-of-the-transaction-log-file.md) </span><span class="sxs-lookup"><span data-stu-id="2b724-155">[Manage the Size of the Transaction Log File](manage-the-size-of-the-transaction-log-file.md) </span></span>  
 <span data-ttu-id="2b724-156">[交易記錄備份 &#40;SQL Server&#41;](../backup-restore/transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2b724-156">[Transaction Log Backups &#40;SQL Server&#41;](../backup-restore/transaction-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="2b724-157">sp_add_log_file_recover_suspect_db &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2b724-157">sp_add_log_file_recover_suspect_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-log-file-recover-suspect-db-transact-sql)  
  
  
