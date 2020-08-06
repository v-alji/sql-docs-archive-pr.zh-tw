---
title: 資料庫損毀時備份交易記錄 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], damaged
- backing up [SQL Server]. damaged database
- transaction log backups [SQL Server], damaged databases
ms.assetid: 9b8873cc-df54-4336-ab9b-8f525132c2b0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea712e6bc4e73119a4f07a7775f9f25e212f8534
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584598"
---
# <a name="back-up-the-transaction-log-when-the-database-is-damaged-sql-server"></a><span data-ttu-id="6430f-102">資料庫損毀時備份交易記錄 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6430f-102">Back Up the Transaction Log When the Database Is Damaged (SQL Server)</span></span>
  <span data-ttu-id="6430f-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中於資料庫損毀時備份交易記錄。</span><span class="sxs-lookup"><span data-stu-id="6430f-103">This topic describes how to back up a transaction log when the database is damaged in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="6430f-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="6430f-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6430f-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="6430f-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6430f-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="6430f-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="6430f-107">建議</span><span class="sxs-lookup"><span data-stu-id="6430f-107">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="6430f-108">安全性</span><span class="sxs-lookup"><span data-stu-id="6430f-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6430f-109">**若要使用下列項目，在資料庫損毀時備份交易記錄**</span><span class="sxs-lookup"><span data-stu-id="6430f-109">**To back up the transaction log when the database is damaged, using:**</span></span>  
  
     [<span data-ttu-id="6430f-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6430f-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6430f-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6430f-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6430f-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="6430f-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="6430f-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="6430f-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="6430f-114">在明確或隱含的交易中，並不允許使用 BACKUP 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6430f-114">The BACKUP statement is not allowed in an explicit or implicit transaction.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="6430f-115">建議</span><span class="sxs-lookup"><span data-stu-id="6430f-115">Recommendations</span></span>  
  
-   <span data-ttu-id="6430f-116">如果是使用完整復原模式或大量記錄復原模式的資料庫，則在開始還原資料庫之前，您通常需要先備份記錄結尾。</span><span class="sxs-lookup"><span data-stu-id="6430f-116">For a database that uses either the full or bulk-logged recovery model, you generally need to back up the tail of the log before beginning to restore the database.</span></span> <span data-ttu-id="6430f-117">在容錯移轉記錄傳送組態之前，您也應該先備份主要資料庫的記錄結尾。</span><span class="sxs-lookup"><span data-stu-id="6430f-117">You also should back up the tail of the log of the primary database before failing over a log shipping configuration.</span></span> <span data-ttu-id="6430f-118">在復原資料庫之前將結尾記錄備份還原為最終的記錄備份可在失敗之後避免工作遺失的狀況。</span><span class="sxs-lookup"><span data-stu-id="6430f-118">Restoring the tail-log backup as the final log backup before recovering the database avoids work loss after a failure.</span></span> <span data-ttu-id="6430f-119">如需結尾記錄備份的詳細資訊，請參閱[結尾記錄備份 &#40;SQL Server&#41;](tail-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="6430f-119">For more information about tail-log backups, see [Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6430f-120">Security</span><span class="sxs-lookup"><span data-stu-id="6430f-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6430f-121">權限</span><span class="sxs-lookup"><span data-stu-id="6430f-121">Permissions</span></span>  
 <span data-ttu-id="6430f-122">BACKUP DATABASE 和 BACKUP LOG 權限預設為 **sysadmin** 固定伺服器角色以及 **db_owner** 和 **db_backupoperator** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="6430f-122">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="6430f-123">備份裝置實體檔案的擁有權和權限問題可能會干擾備份作業。</span><span class="sxs-lookup"><span data-stu-id="6430f-123">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6430f-124">必須能夠讀取和寫入裝置；執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的帳戶必須具備寫入權限。</span><span class="sxs-lookup"><span data-stu-id="6430f-124">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="6430f-125">不過，在系統資料表中加入備份裝置項目的 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)並不會檢查檔案存取權限。</span><span class="sxs-lookup"><span data-stu-id="6430f-125">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="6430f-126">當您嘗試備份或還原時，存取實體資源之前不一定會出現備份裝置實體檔案的這些問題。</span><span class="sxs-lookup"><span data-stu-id="6430f-126">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6430f-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6430f-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-back-up-the-tail-of-the-transaction-log"></a><span data-ttu-id="6430f-128">若要備份交易記錄的結尾</span><span class="sxs-lookup"><span data-stu-id="6430f-128">To back up the tail of the transaction log</span></span>  
  
1.  <span data-ttu-id="6430f-129">連線至適當的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體之後，在 [物件總管] 中按一下伺服器名稱，以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="6430f-129">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="6430f-130">展開 **[資料庫]** ，然後視資料庫而定，選取使用者資料庫，或者展開 **[系統資料庫]** 並選取一個系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="6430f-130">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="6430f-131">以滑鼠右鍵按一下資料庫，指向 **[工作]** ，然後按一下 **[備份]** 。</span><span class="sxs-lookup"><span data-stu-id="6430f-131">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="6430f-132">會出現 **[備份資料庫]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6430f-132">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="6430f-133">在 **[資料庫]** 清單方塊中確認資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="6430f-133">In the **Database** list box, verify the database name.</span></span> <span data-ttu-id="6430f-134">您可以選擇性從清單中選取不同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="6430f-134">You can optionally select a different database from the list.</span></span>  
  
5.  <span data-ttu-id="6430f-135">確認復原模式是否為 **[FULL]** 或 **[BULK_LOGGED]** 。</span><span class="sxs-lookup"><span data-stu-id="6430f-135">Verify that the recovery model is either **FULL** or **BULK_LOGGED**.</span></span>  
  
6.  <span data-ttu-id="6430f-136">在 **[備份類型]** 清單方塊中，選取 **[交易記錄]** 。</span><span class="sxs-lookup"><span data-stu-id="6430f-136">In the **Backup type** list box, select **Transaction Log**.</span></span>  
  
7.  <span data-ttu-id="6430f-137">保留 **[只複製備份]** 的未選取狀態。</span><span class="sxs-lookup"><span data-stu-id="6430f-137">Leave **Copy Only Backup** deselected.</span></span>  
  
8.  <span data-ttu-id="6430f-138">在 **[備份組]** 區域，接受 **[名稱]** 文字方塊中建議的預設備份組名稱，或者輸入不同的備份組名稱。</span><span class="sxs-lookup"><span data-stu-id="6430f-138">In the **Backup set** area, either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.</span></span>  
  
9. <span data-ttu-id="6430f-139">在 [描述]  文字方塊中，輸入結尾記錄備份的描述。</span><span class="sxs-lookup"><span data-stu-id="6430f-139">In the **Description** text box, enter a description for the tail-log backup.</span></span>  
  
10. <span data-ttu-id="6430f-140">指定備份組會在何時過期：</span><span class="sxs-lookup"><span data-stu-id="6430f-140">Specify when the backup set will expire:</span></span>  
  
    -   <span data-ttu-id="6430f-141">若要讓備份組在特定的天數後過期，請按一下 [之後]  \(預設選項)，然後輸入備份組建立之後將會過期的天數。</span><span class="sxs-lookup"><span data-stu-id="6430f-141">To have the backup set expire after a specific number of days, click **After** (the default option), and enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="6430f-142">這個值可以介於 0 到 99999 日之間；值為 0 日意指備份組永遠不會過期。</span><span class="sxs-lookup"><span data-stu-id="6430f-142">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="6430f-143">預設值會在 **[伺服器屬性]** 對話方塊 ( **[資料庫設定]** 頁面) 的 **[預設備份媒體保留 (以天為單位)]** 選項中設定。</span><span class="sxs-lookup"><span data-stu-id="6430f-143">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (**Database Settings** page).</span></span> <span data-ttu-id="6430f-144">若要存取此對話方塊，請以滑鼠右鍵按一下 [物件總管] 中的伺服器名稱並選取 [屬性]，然後選取 **[資料庫設定]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="6430f-144">To access this dialog box, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="6430f-145">若要讓備份組在特定日期過期，請按一下 **[於]** ，然後輸入備份組將過期的日期。</span><span class="sxs-lookup"><span data-stu-id="6430f-145">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
11. <span data-ttu-id="6430f-146">按一下 **[磁碟]** 或 **[磁帶]** ，以選擇備份目的地的類型。</span><span class="sxs-lookup"><span data-stu-id="6430f-146">Choose the type of backup destination by clicking **Disk** or **Tape**.</span></span> <span data-ttu-id="6430f-147">若要選取包含單一媒體集的磁碟或磁帶機 (最多 64 個) 的路徑，請按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="6430f-147">To select the paths of up to 64 disk or tape drives containing a single media set, click **Add**.</span></span> <span data-ttu-id="6430f-148">選取的路徑會在 **[備份至]** 清單方塊中顯示。</span><span class="sxs-lookup"><span data-stu-id="6430f-148">The selected paths are displayed in the **Backup to** list box.</span></span>  
  
     <span data-ttu-id="6430f-149">若要移除備份目的地，請選取目的地，然後按一下 **[移除]** 。</span><span class="sxs-lookup"><span data-stu-id="6430f-149">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="6430f-150">若要檢視備份目的地的內容，請選取目的地，然後按一下 **[內容]** 。</span><span class="sxs-lookup"><span data-stu-id="6430f-150">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
12. <span data-ttu-id="6430f-151">在 **[選項]** 頁面上，按一下下列其中一個項目，選取 **[覆寫媒體]** 選項：</span><span class="sxs-lookup"><span data-stu-id="6430f-151">On the **Options** page, select an **Overwrite Media** option, by clicking one of the following:</span></span>  
  
    -   <span data-ttu-id="6430f-152">**備份至現有的媒體集**</span><span class="sxs-lookup"><span data-stu-id="6430f-152">**Back up to the existing media set**</span></span>  
  
         <span data-ttu-id="6430f-153">針對這個選項，按一下 **[附加至現有的備份組]** 或 **[覆寫所有現有的備份組]** 。</span><span class="sxs-lookup"><span data-stu-id="6430f-153">For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.</span></span>  
  
         <span data-ttu-id="6430f-154">另外，也可以選取 **[檢查媒體集名稱及備份組是否逾期]** ，以讓備份作業確認媒體集及備份組逾期的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="6430f-154">Optionally, select **Check media set name and backup set expiration** to cause the backup operation to verify the date and time at which the media set and backup set expire.</span></span>  
  
         <span data-ttu-id="6430f-155">另外，也可以在 **[媒體集名稱]** 文字方塊中輸入名稱。</span><span class="sxs-lookup"><span data-stu-id="6430f-155">Optionally, enter a name in the **Media set name** text box.</span></span> <span data-ttu-id="6430f-156">如果未指定名稱，就會建立一個空白名稱的媒體集。</span><span class="sxs-lookup"><span data-stu-id="6430f-156">If no name is specified, a media set with a blank name is created.</span></span> <span data-ttu-id="6430f-157">如果您指定媒體集名稱，就會檢查媒體 (磁帶或磁碟)，以查看實際名稱是否與您在此處輸入的名稱相符。</span><span class="sxs-lookup"><span data-stu-id="6430f-157">If you specify a media set name, the media (tape or disk) is checked to see whether the actual name matches the name you enter here.</span></span>  
  
         <span data-ttu-id="6430f-158">如果您讓媒體名稱保持空白，並核取方塊以針對媒體進行檢查，成功也會使媒體上的媒體名稱保持空白。</span><span class="sxs-lookup"><span data-stu-id="6430f-158">If you leave the media name blank and check the box to check it against the media, success will equal the media name on the media also being blank.</span></span>  
  
    -   <span data-ttu-id="6430f-159">**備份至新的媒體集，並清除所有現有的備份組**</span><span class="sxs-lookup"><span data-stu-id="6430f-159">**Back up to a new media set, and erase all existing backup sets**</span></span>  
  
         <span data-ttu-id="6430f-160">針對這個選項，在 **[新媒體集名稱]** 文字方塊中輸入名稱，然後選擇性在 **[新媒體集描述]** 文字方塊中描述媒體集。</span><span class="sxs-lookup"><span data-stu-id="6430f-160">For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.</span></span>  
  
     <span data-ttu-id="6430f-161">如需媒體集選項的詳細資訊，請參閱[媒體集、媒體家族與備份組 &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="6430f-161">For more information about media set options, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
13. <span data-ttu-id="6430f-162">(選擇性) 在 **[可靠性]** 區段中選取：</span><span class="sxs-lookup"><span data-stu-id="6430f-162">In the **Reliability** section, optionally, check:</span></span>  
  
    -   <span data-ttu-id="6430f-163">**[完成後驗證備份]** 。</span><span class="sxs-lookup"><span data-stu-id="6430f-163">**Verify backup when finished**.</span></span>  
  
    -   <span data-ttu-id="6430f-164">**寫入媒體之前執行總和檢查碼**。</span><span class="sxs-lookup"><span data-stu-id="6430f-164">**Perform checksum before writing to media**.</span></span>  
  
    -   <span data-ttu-id="6430f-165">**發生總和檢查碼錯誤時繼續**</span><span class="sxs-lookup"><span data-stu-id="6430f-165">**Continue on checksum error**</span></span>  
  
     <span data-ttu-id="6430f-166">如需總和檢查碼的相關資訊，請參閱[在備份和還原期間可能的媒體錯誤 &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="6430f-166">For information on checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
14. <span data-ttu-id="6430f-167">在 **[交易記錄]** 區段中，按一下 **[備份記錄的結尾，並讓資料庫保持在還原狀態]** 。</span><span class="sxs-lookup"><span data-stu-id="6430f-167">In the **Transaction log** section, check **Back up the tail of the log, and leave database in the restoring state**.</span></span>  
  
     <span data-ttu-id="6430f-168">這相當於指定以下 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 陳述式：</span><span class="sxs-lookup"><span data-stu-id="6430f-168">This is equivalent to specifying the following [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement:</span></span>  
  
     `BACKUP LOG <database_name> TO <backup_device> WITH NORECOVERY`  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="6430f-169">在還原時，[還原資料庫] 對話方塊會將結尾記錄備份的類型顯示為 [交易記錄 (只複製)]  。</span><span class="sxs-lookup"><span data-stu-id="6430f-169">At restore time, the Restore Database dialog box displays the type of a tail-log backup as **Transaction Log (Copy Only)**.</span></span>  
  
15. <span data-ttu-id="6430f-170">如果是備份至磁帶機 (在 [一般]  頁面的 [目的地]  區段中指定)，[備份後卸載磁帶]  選項會啟用供選擇。</span><span class="sxs-lookup"><span data-stu-id="6430f-170">If you are backing up to a tape drive (as specified in the **Destination** section of the **General** page), the **Unload the tape after backup** option is active.</span></span> <span data-ttu-id="6430f-171">按一下這個選項會啟動 **[卸載之前倒轉磁帶]** 選項。</span><span class="sxs-lookup"><span data-stu-id="6430f-171">Clicking this option activates the **Rewind the tape before unloading** option.</span></span>  
  
16. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="6430f-172">和更新的版本支援 [備份壓縮](backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="6430f-172">and later supports [backup compression](backup-compression-sql-server.md).</span></span> <span data-ttu-id="6430f-173">依預設，備份壓縮與否取決於 **備份壓縮預設** 伺服器組態選項的值。</span><span class="sxs-lookup"><span data-stu-id="6430f-173">By default, whether a backup is compressed depends on the value of the **backup-compression default** server configuration option.</span></span> <span data-ttu-id="6430f-174">不過，不論目前的伺服器層級預設值為何，您都可以透過核取 [壓縮備份]  壓縮備份，而且可以透過核取 [不要壓縮備份]  防止壓縮。</span><span class="sxs-lookup"><span data-stu-id="6430f-174">However, regardless of the current server-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.</span></span>  
  
     <span data-ttu-id="6430f-175">**檢視目前的 backup compression default**</span><span class="sxs-lookup"><span data-stu-id="6430f-175">**To view the current backup compression default**</span></span>  
  
    -   [<span data-ttu-id="6430f-176">檢視或設定 backup compression default 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="6430f-176">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6430f-177">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6430f-177">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-backup-of-the-currently-active-transaction-log"></a><span data-ttu-id="6430f-178">若要為目前使用中的交易記錄建立備份</span><span class="sxs-lookup"><span data-stu-id="6430f-178">To create a backup of the currently active transaction log</span></span>  
  
1.  <span data-ttu-id="6430f-179">執行 BACKUP LOG 陳述式，備份目前使用中的交易記錄，方法為指定：</span><span class="sxs-lookup"><span data-stu-id="6430f-179">Execute the BACKUP LOG statement to back up the currently active transaction log, specifying:</span></span>  
  
    -   <span data-ttu-id="6430f-180">欲備份之交易記錄所屬的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="6430f-180">The name of the database to which the transaction log to back up belongs.</span></span>  
  
    -   <span data-ttu-id="6430f-181">將寫入交易記錄備份的備份裝置。</span><span class="sxs-lookup"><span data-stu-id="6430f-181">The backup device where the transaction log backup will be written.</span></span>  
  
    -   <span data-ttu-id="6430f-182">NO_TRUNCATE 子句。</span><span class="sxs-lookup"><span data-stu-id="6430f-182">The NO_TRUNCATE clause.</span></span>  
  
         <span data-ttu-id="6430f-183">這個子句允許交易記錄作用中的部份也進行備份，即使資料庫無法存取，只要交易記錄可以存取而且沒有損毀即可。</span><span class="sxs-lookup"><span data-stu-id="6430f-183">This clause allows the active part of the transaction log to be backed up even if the database is inaccessible, provided that the transaction log file is accessible and undamaged.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="6430f-184">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6430f-184">Example (Transact-SQL)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6430f-185">這個範例使用 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]，而這個資料庫使用簡單復原模式。</span><span class="sxs-lookup"><span data-stu-id="6430f-185">This example uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], which uses the simple recovery model.</span></span> <span data-ttu-id="6430f-186">為了允許記錄備份，在執行完整資料庫備份之前，此資料庫已設定為使用完整復原模式。</span><span class="sxs-lookup"><span data-stu-id="6430f-186">To permit log backups, before taking a full database backup, the database was set to use the full recovery model.</span></span> <span data-ttu-id="6430f-187">如需詳細資訊，請參閱[檢視或變更資料庫的復原模式 &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="6430f-187">For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md).</span></span>  
  
 <span data-ttu-id="6430f-188">在資料庫已損毀且無法存取時，只要交易記錄沒有損毀且可存取，這個範例就會備份目前使用中的交易記錄。</span><span class="sxs-lookup"><span data-stu-id="6430f-188">This example backs up the currently active transaction log when a database is damaged and inaccessible, if the transaction log is undamaged and accessible.</span></span>  
  
```scr  
BACKUP LOG AdventureWorks2012  
   TO MyAdvWorks_FullRM_log1  
   WITH NO_TRUNCATE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="6430f-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6430f-189">See Also</span></span>  
 <span data-ttu-id="6430f-190">[還原交易記錄備份 &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6430f-190">[Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span></span>  
 <span data-ttu-id="6430f-191">[將 SQL Server 資料庫還原至某個時間點 &#40;完整復原模式&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="6430f-191">[Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span></span>  
 <span data-ttu-id="6430f-192">[備份資料庫 &#40;備份選項頁面&#41;](back-up-database-backup-options-page.md) </span><span class="sxs-lookup"><span data-stu-id="6430f-192">[Back Up Database &#40;Backup Options Page&#41;](back-up-database-backup-options-page.md) </span></span>  
 <span data-ttu-id="6430f-193">[備份資料庫 &#40;一般頁面&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="6430f-193">[Back Up Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="6430f-194">[套用交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6430f-194">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="6430f-195">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6430f-195">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="6430f-196">[檔案還原 &#40;簡單復原模式&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="6430f-196">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 [<span data-ttu-id="6430f-197">檔案還原 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="6430f-197">File Restores &#40;Full Recovery Model&#41;</span></span>](file-restores-full-recovery-model.md)  
  
  
