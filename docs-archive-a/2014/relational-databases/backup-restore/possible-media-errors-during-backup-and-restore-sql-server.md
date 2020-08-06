---
title: 在備份和還原期間可能的媒體錯誤 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- media errors [SQL Server]
- CONTINUE_AFTER_ERROR option
- errors [SQL Server], backups
- backups [SQL Server], errors
- RESTORE VERIFYONLY statement
- backup media [SQL Server], error management
- page checksums [SQL Server]
- backup checksums [SQL Server]
- backing up [SQL Server], media errors
- RESTORE statement, media errors
- NO_CHECKSUM option
- checksums [SQL Server]
ms.assetid: 83a27b29-1191-4f8d-9648-6e6be73a9b7c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 15691c513aad6027be1063ef566ebdf245ebcc8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705205"
---
# <a name="possible-media-errors-during-backup-and-restore-sql-server"></a><span data-ttu-id="783fd-102">在備份和還原期間可能的媒體錯誤 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="783fd-102">Possible Media Errors During Backup and Restore (SQL Server)</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="783fd-103">可讓您選擇復原資料庫，而不理會偵測到的錯誤。</span><span class="sxs-lookup"><span data-stu-id="783fd-103">gives you the option of recovering a database despite detected errors.</span></span> <span data-ttu-id="783fd-104">有一項重要的新錯誤偵測機制，就是可以選擇建立備份總和檢查碼，這是由備份作業所建立，並可使用還原作業來加以驗證。</span><span class="sxs-lookup"><span data-stu-id="783fd-104">An important new error-detection mechanism is the optional creation of a backup checksum that can be created by a backup operation and validated by a restore operation.</span></span> <span data-ttu-id="783fd-105">您可以控制作業是否要檢查錯誤，以及在發生錯誤時，是要停止作業，還是要繼續進行。</span><span class="sxs-lookup"><span data-stu-id="783fd-105">You can control whether an operation checks for errors and whether the operation stops or continues on encountering an error.</span></span> <span data-ttu-id="783fd-106">如果備份包含備份總和檢查碼，RESTORE 和 RESTORE VERIFYONLY 陳述式就可以檢查錯誤。</span><span class="sxs-lookup"><span data-stu-id="783fd-106">If a backup contains a backup checksum, RESTORE and RESTORE VERIFYONLY statements can check for errors.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="783fd-107">鏡像備份提供高達四個媒體集複本 (鏡像)，可在因為媒體損壞而導致錯誤時，提供其他的複本來復原。</span><span class="sxs-lookup"><span data-stu-id="783fd-107">Mirrored backups provide up to four copies (mirrors) of a media set, providing alternative copies for recovering from errors caused by damaged media.</span></span> <span data-ttu-id="783fd-108">如需詳細資訊，請參閱本主題稍後的 [鏡像備份媒體集 &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md)的使用者閱讀。</span><span class="sxs-lookup"><span data-stu-id="783fd-108">For more information, see [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).</span></span>  
  
  
  
##  <a name="backup-checksums"></a><a name="BckChecksums"></a> <span data-ttu-id="783fd-109">備份總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="783fd-109">Backup Checksums</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="783fd-110">支援三種類型的總和檢查碼：分頁上的總和檢查碼、記錄區塊中的總和檢查碼，以及備份總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="783fd-110">supports three types of checksums: a checksum on pages, a checksum in log blocks, and a backup checksum.</span></span> <span data-ttu-id="783fd-111">產生備份總和檢查碼時，BACKUP (備份) 會驗證從資料庫讀取的資料，是否與資料庫中的任何總和檢查碼或損毀頁指示一致。</span><span class="sxs-lookup"><span data-stu-id="783fd-111">When generating a backup checksum, BACKUP verifies that the data read from the database is consistent with any checksum or torn-page indication that is present in the database.</span></span>  
  
 <span data-ttu-id="783fd-112">BACKUP 陳述式可選擇性地計算備份資料流的備份總和檢查碼；如果分頁總和檢查碼或損毀頁資訊顯示在特定的分頁上，備份該分頁時，BACKUP 也會驗證該分頁的總和檢查碼、損毀頁狀態及分頁識別碼。</span><span class="sxs-lookup"><span data-stu-id="783fd-112">The BACKUP statement optionally computes a backup checksum on the backup stream; if page-checksum or torn-page information is present on a given page, when backing up the page, BACKUP also verifies the checksum and torn-page status and the page ID, of the page.</span></span> <span data-ttu-id="783fd-113">建立備份總和檢查碼時，備份作業不會新增任何總和檢查碼至分頁。</span><span class="sxs-lookup"><span data-stu-id="783fd-113">When creating a backup checksum, a backup operation does not add any checksums to pages.</span></span> <span data-ttu-id="783fd-114">分頁會依照其存在於資料庫中的樣子來備份，而且備份不會修改分頁。</span><span class="sxs-lookup"><span data-stu-id="783fd-114">Pages are backed up as they exist in the database, and the pages are unmodified by backup.</span></span>  
  
 <span data-ttu-id="783fd-115">因為驗證及產生備份總和檢查碼會造成額外負擔，使用備份總和檢查碼可能會影響效能。</span><span class="sxs-lookup"><span data-stu-id="783fd-115">Due to the overhead verifying and generating backup checksums, using backup checksums poses a potential performance impact.</span></span> <span data-ttu-id="783fd-116">工作負載及備份的輸送量可能都會受到影響。</span><span class="sxs-lookup"><span data-stu-id="783fd-116">Both the workload and the backup throughput may be affected.</span></span> <span data-ttu-id="783fd-117">因此，您可以選擇是否要使用備份總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="783fd-117">Therefore, using backup checksums is optional.</span></span> <span data-ttu-id="783fd-118">決定要在備份期間產生總和檢查碼時，請小心監視對 CPU 造成的額外負擔，以及對系統上任何並行工作負載所造成的影響。</span><span class="sxs-lookup"><span data-stu-id="783fd-118">When deciding to generate checksums during a backup, carefully monitor the CPU overhead incurred as well as the impact on any concurrent workload on the system.</span></span>  
  
 <span data-ttu-id="783fd-119">BACKUP 絕不會修改磁碟上的來源分頁或是分頁的內容。</span><span class="sxs-lookup"><span data-stu-id="783fd-119">BACKUP never modifies the source page on disk nor the contents of a page.</span></span>  
  
 <span data-ttu-id="783fd-120">已啟用備份總和檢查碼時，備份作業會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="783fd-120">When backup checksums are enabled, a backup operation performs the following steps:</span></span>  
  
1.  <span data-ttu-id="783fd-121">在將分頁寫入備份媒體之前，備份作業會先驗證分頁層級的資訊 (分頁總和檢查碼或損毀頁偵測，若其中一項存在的話)。</span><span class="sxs-lookup"><span data-stu-id="783fd-121">Before writing a page to the backup media, the backup operation verifies the page-level information (page checksum or torn page detection), if either exists.</span></span> <span data-ttu-id="783fd-122">如果兩者都不存在，則備份無法驗證分頁。</span><span class="sxs-lookup"><span data-stu-id="783fd-122">If neither exists, backup cannot verify the page.</span></span> <span data-ttu-id="783fd-123">而是直接包含未驗證的分頁，並且將其內容加入整體的備份總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="783fd-123">Unverified the pages are included as is, and their contents are added to the overall backup checksum.</span></span>  
  
     <span data-ttu-id="783fd-124">如果備份作業在驗證期間發生分頁錯誤，則備份失敗。</span><span class="sxs-lookup"><span data-stu-id="783fd-124">If the backup operation encounters a page error during verification, the backup fails.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="783fd-125">如需分頁總和檢查碼及損毀頁偵測的詳細資訊，請參閱 ALTER DATABASE 陳述式的 PAGE_VERIFY 選項。</span><span class="sxs-lookup"><span data-stu-id="783fd-125">For more information about page checksums and torn page detection, see the PAGE_VERIFY option of the ALTER DATABASE statement.</span></span> <span data-ttu-id="783fd-126">如需詳細資訊，請參閱 [ALTER DATABASE SET 選項 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)。</span><span class="sxs-lookup"><span data-stu-id="783fd-126">For more information, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
2.  <span data-ttu-id="783fd-127">不論頁面總和檢查碼是否存在，BACKUP 都會產生備份資料流的個別備份總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="783fd-127">Regardless of whether page checksums are present, BACKUP generates a separate backup checksum for the backup streams.</span></span> <span data-ttu-id="783fd-128">還原作業可以選擇性地利用備份總和檢查碼來驗證備份是否損毀。</span><span class="sxs-lookup"><span data-stu-id="783fd-128">Restore operations can optionally use the backup checksum to validate that the backup is not corrupted.</span></span> <span data-ttu-id="783fd-129">備份總和檢查碼儲存在備份媒體中，而不是儲存在資料庫頁面中。</span><span class="sxs-lookup"><span data-stu-id="783fd-129">The backup checksum is stored on the backup media, not on the database pages.</span></span> <span data-ttu-id="783fd-130">在還原時，您可以選擇性地使用備份總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="783fd-130">The backup checksum can optionally be used at restore time.</span></span>  
  
3.  <span data-ttu-id="783fd-131">備份組會以旗標標示為包含備份總和檢查碼 (在 **msdb..backupset** 的 **has_backup_checksums**資料行中)。</span><span class="sxs-lookup"><span data-stu-id="783fd-131">The backup set is flagged as containing backup checksums (in the **has_backup_checksums** column of **msdb..backupset)**.</span></span> <span data-ttu-id="783fd-132">如需詳細資訊，請參閱 [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="783fd-132">For more information, see [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql).</span></span>  
  
 <span data-ttu-id="783fd-133">在還原作業期間，如果備份媒體上有備份總和檢查碼，依預設 RESTORE 和 RESTORE VERIFYONLY 陳述式都會驗證備份總和檢查碼及分頁總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="783fd-133">During a restore operation, if backup checksums are present on the backup media, by default, both the RESTORE and RESTORE VERIFYONLY statements verify the backup checksums and page checksums.</span></span> <span data-ttu-id="783fd-134">如果沒有備份總和檢查碼，這二種還原作業仍會繼續進行，但不會執行任何驗證；這是因為沒有備份總和檢查碼，還原作業就不能確實地驗證分頁總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="783fd-134">If there is no backup checksum, either restore operation proceeds without any verification; this is because without a backup checksum, restore cannot reliably verify page checksums.</span></span>  
  
## <a name="response-to-page-checksum-errors-during-a-backup-or-restore-operation"></a><span data-ttu-id="783fd-135">在備份或還原作業期間對分頁總和檢查碼錯誤的回應</span><span class="sxs-lookup"><span data-stu-id="783fd-135">Response to Page Checksum Errors During a Backup or Restore Operation</span></span>  
 <span data-ttu-id="783fd-136">根據預設，在發生分頁總和檢查碼錯誤之後，BACKUP 或 RESTORE 作業會失敗，而 RESTORE VERIFYONLY 作業會繼續。</span><span class="sxs-lookup"><span data-stu-id="783fd-136">By default, after encountering a page checksum error, a BACKUP or RESTORE operation fails and a RESTORE VERIFYONLY operation continues.</span></span> <span data-ttu-id="783fd-137">但是，您可以控制給定的作業在發生錯誤時是失敗還是盡其所能地繼續。</span><span class="sxs-lookup"><span data-stu-id="783fd-137">However, you can control whether a given operation fails on encountering an error or continues as best it can.</span></span>  
  
 <span data-ttu-id="783fd-138">如果 BACKUP 作業在發生錯誤後繼續，該作業會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="783fd-138">If a BACKUP operation continues after encountering errors, the operation performs the following steps:</span></span>  
  
1.  <span data-ttu-id="783fd-139">將備份媒體上的備份組標註為包含錯誤，並且在 **msdb** 資料庫的 **suspect_pages** 資料表中追蹤該分頁。</span><span class="sxs-lookup"><span data-stu-id="783fd-139">Flags the backup set on the backup media as containing errors and tracks the page in the **suspect_pages** table in the **msdb** database.</span></span> <span data-ttu-id="783fd-140">如需詳細資訊，請參閱 [suspect_pages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/suspect-pages-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="783fd-140">For more information, see [suspect_pages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/suspect-pages-transact-sql).</span></span>  
  
2.  <span data-ttu-id="783fd-141">將錯誤記錄在 SQL Server 錯誤記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="783fd-141">Logs the error in the SQL Server error log.</span></span>  
  
3.  <span data-ttu-id="783fd-142">將備份組標示為包含該類型的錯誤 (在 **msdb.backupset** 的 **is_damaged**資料行中)。</span><span class="sxs-lookup"><span data-stu-id="783fd-142">Marks the backup set as containing this type of error (in the **is_damaged** column of **msdb.backupset)**.</span></span> <span data-ttu-id="783fd-143">如需詳細資訊，請參閱 [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="783fd-143">For more information, see [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql).</span></span>  
  
4.  <span data-ttu-id="783fd-144">發出訊息指出已順利產生備份，但包含分頁錯誤。</span><span class="sxs-lookup"><span data-stu-id="783fd-144">Issues a message that the backup was successfully generated, but contains page errors.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="783fd-145">相關工作</span><span class="sxs-lookup"><span data-stu-id="783fd-145">Related Tasks</span></span>  
 <span data-ttu-id="783fd-146">**若要啟用或停用備份總和檢查碼**</span><span class="sxs-lookup"><span data-stu-id="783fd-146">**To enable or disable backup checksums**</span></span>  
  
-   [<span data-ttu-id="783fd-147">在備份或還原期間啟用或停用備份總和檢查碼 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="783fd-147">Enable or Disable Backup Checksums During Backup or Restore &#40;SQL Server&#41;</span></span>](enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
 <span data-ttu-id="783fd-148">**若要在備份作業期間控制錯誤的回應方式**</span><span class="sxs-lookup"><span data-stu-id="783fd-148">**To control the response to a error during a backup operation**</span></span>  
  
-   [<span data-ttu-id="783fd-149">指定在發生錯誤後備份或還原作業應該繼續還是停止 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="783fd-149">Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error &#40;SQL Server&#41;</span></span>](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  
## <a name="see-also"></a><span data-ttu-id="783fd-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="783fd-150">See Also</span></span>  
 <span data-ttu-id="783fd-151">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="783fd-151">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="783fd-152">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="783fd-152">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="783fd-153">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="783fd-153">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="783fd-154">[鏡像備份媒體集 &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="783fd-154">[Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) </span></span>  
 <span data-ttu-id="783fd-155">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="783fd-155">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="783fd-156">RESTORE VERIFYONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="783fd-156">RESTORE VERIFYONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)  
  
  
