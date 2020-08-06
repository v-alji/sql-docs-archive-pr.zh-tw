---
title: 建立完整資料庫備份 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [SQL Server], full backups
- backing up databases [SQL Server], SQL Server Management Studio
- backups [SQL Server], creating
- database backups [SQL Server], SQL Server Management Studio
ms.assetid: 586561fc-dfbb-4842-84f8-204a9100a534
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f406464680a1669133dc87bdfb231c644d33fbdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708457"
---
# <a name="create-a-full-database-backup-sql-server"></a><span data-ttu-id="38a66-102">建立完整資料庫備份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="38a66-102">Create a Full Database Backup (SQL Server)</span></span>
  <span data-ttu-id="38a66-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 PowerShell，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中建立完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="38a66-103">This topic describes how to create a full database backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or PowerShell.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="38a66-104">如需 SQL Server 備份至 Azure Blob 儲存體服務的相關資訊，請參閱[SQL Server 使用 Azure Blob 儲存體服務的備份與還原](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="38a66-104">For information on SQL Server backup to the Azure Blob storage service, see, [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
 <span data-ttu-id="38a66-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="38a66-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="38a66-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="38a66-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="38a66-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="38a66-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="38a66-108">建議</span><span class="sxs-lookup"><span data-stu-id="38a66-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="38a66-109">安全性</span><span class="sxs-lookup"><span data-stu-id="38a66-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="38a66-110">**若要使用下列項目建立完整資料庫備份：**</span><span class="sxs-lookup"><span data-stu-id="38a66-110">**To create a full database backup, using:**</span></span>  
  
     [<span data-ttu-id="38a66-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="38a66-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="38a66-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="38a66-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="38a66-113">PowerShell</span><span class="sxs-lookup"><span data-stu-id="38a66-113">PowerShell</span></span>](#PowerShellProcedure)  
  
-   [<span data-ttu-id="38a66-114">相關工作</span><span class="sxs-lookup"><span data-stu-id="38a66-114">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="38a66-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="38a66-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="38a66-116">限制事項</span><span class="sxs-lookup"><span data-stu-id="38a66-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="38a66-117">在明確或隱含的交易中，並不允許使用 BACKUP 陳述式。</span><span class="sxs-lookup"><span data-stu-id="38a66-117">The BACKUP statement is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="38a66-118">在舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，無法還原較新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本所建立的備份。</span><span class="sxs-lookup"><span data-stu-id="38a66-118">Backups that are created by more recent version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be restored in earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="38a66-119">如需詳細資訊，請參閱 [備份概觀 &#40;SQL Server&#41;](backup-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="38a66-119">For more information, see [Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="38a66-120">建議</span><span class="sxs-lookup"><span data-stu-id="38a66-120">Recommendations</span></span>  
  
-   <span data-ttu-id="38a66-121">資料庫的大小增加時，完整資料庫備份就需要更多的時間才能完成，同時也需要更多的儲存空間。</span><span class="sxs-lookup"><span data-stu-id="38a66-121">As a database increases in size full database backups take more time to finish and require more storage space.</span></span> <span data-ttu-id="38a66-122">因此，若為大型資料庫，您可能會想透過一系列的 *「差異資料庫備份」* (Differential database backups) 補充完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="38a66-122">Therefore, for a large database, you might want to supplement a full database backup with a series of *differential database backups*.</span></span> <span data-ttu-id="38a66-123">如需詳細資訊，請參閱 [差異備份 &#40;SQL Server&#41;](differential-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="38a66-123">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="38a66-124">您可以使用 [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) 系統預存程序來估計完整資料庫備份的大小。</span><span class="sxs-lookup"><span data-stu-id="38a66-124">You can estimate the size of a full database backup by using the [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) system stored procedure.</span></span>  
  
-   <span data-ttu-id="38a66-125">根據預設，每項成功的備份作業都會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔與系統事件記錄檔中，加入一個項目。</span><span class="sxs-lookup"><span data-stu-id="38a66-125">By default, every successful backup operation adds an entry in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and in the system event log.</span></span> <span data-ttu-id="38a66-126">如果您經常備份記錄檔，這些成功訊息可能會快速累積，因而產生龐大的錯誤記錄檔，讓您難以尋找其他訊息。</span><span class="sxs-lookup"><span data-stu-id="38a66-126">If back up the log very frequently, these success messages accumulate quickly, resulting in huge error logs that can make finding other messages difficult.</span></span> <span data-ttu-id="38a66-127">在這類情況下，如果沒有任何指令碼相依於這些記錄項目，您就可以使用追蹤旗標 3226 來隱藏這些記錄項目。</span><span class="sxs-lookup"><span data-stu-id="38a66-127">In such cases you can suppress these log entries by using trace flag 3226 if none of your scripts depend on those entries.</span></span> <span data-ttu-id="38a66-128">如需詳細資訊，請參閱[追蹤旗標 &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="38a66-128">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="38a66-129">Security</span><span class="sxs-lookup"><span data-stu-id="38a66-129">Security</span></span>  
 <span data-ttu-id="38a66-130">資料庫備份上的 TRUSTWORTHY 是設為 OFF。</span><span class="sxs-lookup"><span data-stu-id="38a66-130">TRUSTWORTHY is set to OFF on a database backup.</span></span> <span data-ttu-id="38a66-131">如需如何將 TRUSTWORTHY 設成 ON 的資訊，請參閱 [ALTER DATABASE SET 選項 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)。</span><span class="sxs-lookup"><span data-stu-id="38a66-131">For information about how to set TRUSTWORTHY to ON, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
 <span data-ttu-id="38a66-132">從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 開始，建立備份的 `PASSWORD` 和 `MEDIAPASSWORD` 選項已遭到停用。</span><span class="sxs-lookup"><span data-stu-id="38a66-132">Beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] the `PASSWORD` and `MEDIAPASSWORD` options are discontinued for creating backups.</span></span> <span data-ttu-id="38a66-133">您仍然可以還原以密碼建立的備份。</span><span class="sxs-lookup"><span data-stu-id="38a66-133">You can still restore backups created with passwords.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="38a66-134">權限</span><span class="sxs-lookup"><span data-stu-id="38a66-134">Permissions</span></span>  
 <span data-ttu-id="38a66-135">BACKUP DATABASE 和 BACKUP LOG 權限預設為 **sysadmin** 固定伺服器角色以及 **db_owner** 和 **db_backupoperator** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="38a66-135">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="38a66-136">備份裝置實體檔案的擁有權和權限問題可能會干擾備份作業。</span><span class="sxs-lookup"><span data-stu-id="38a66-136">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="38a66-137">必須能夠讀取和寫入裝置；執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的帳戶必須具備寫入權限。</span><span class="sxs-lookup"><span data-stu-id="38a66-137">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="38a66-138">不過，在系統資料表中加入備份裝置項目的 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)並不會檢查檔案存取權限。</span><span class="sxs-lookup"><span data-stu-id="38a66-138">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="38a66-139">當您嘗試備份或還原時，存取實體資源之前不一定會出現備份裝置實體檔案的這些問題。</span><span class="sxs-lookup"><span data-stu-id="38a66-139">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="38a66-140">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="38a66-140">Using SQL Server Management Studio</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="38a66-141">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 指定備份工作時，您按一下 [指令碼]\*\*\*\* 按鈕，再選取指令碼目的地，即可產生對應的 [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql) 指令碼。</span><span class="sxs-lookup"><span data-stu-id="38a66-141">When you specify a back up task by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can generate the corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql) script by clicking the **Script** button and selecting a script destination.</span></span>  
  
#### <a name="to-back-up-a-database"></a><span data-ttu-id="38a66-142">備份資料庫</span><span class="sxs-lookup"><span data-stu-id="38a66-142">To back up a database</span></span>  
  
1.  <span data-ttu-id="38a66-143">連線至適當的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體之後，在 [物件總管] 中按一下伺服器名稱，以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="38a66-143">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="38a66-144">展開 **[資料庫]** ，根據資料庫選取使用者資料庫或展開 **[系統資料庫]** ，然後選取一個系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="38a66-144">Expand **Databases**, and depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="38a66-145">以滑鼠右鍵按一下資料庫，指向 **[工作]** ，然後按一下 **[備份]** 。</span><span class="sxs-lookup"><span data-stu-id="38a66-145">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="38a66-146">會出現 **[備份資料庫]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="38a66-146">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="38a66-147">在 `Database` 清單方塊中，確認資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="38a66-147">In the `Database` list box, verify the database name.</span></span> <span data-ttu-id="38a66-148">您可以選擇性從清單中選取不同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="38a66-148">You can optionally select a different database from the list.</span></span>  
  
5.  <span data-ttu-id="38a66-149">您可以針對任何復原模式 (**完整**、**大量記錄**或**簡單**) 執行資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="38a66-149">You can perform a database backup for any recovery model (**FULL**, **BULK_LOGGED**, or **SIMPLE**).</span></span>  
  
6.  <span data-ttu-id="38a66-150">請在 **[備份類型]** 清單方塊中，選取 **[完整]**。</span><span class="sxs-lookup"><span data-stu-id="38a66-150">In the **Backup type** list box, select **Full**.</span></span>  
  
     <span data-ttu-id="38a66-151">請注意，您可在建立完整資料庫備份之後，建立差異資料庫備份。如需詳細資訊，請參閱[建立差異資料庫備份 &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="38a66-151">Note that after creating a full database backup, you can create a differential database backup; for more information, see [Create a Differential Database Backup &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md).</span></span>  
  
7.  <span data-ttu-id="38a66-152">或者，您也可以選取 **[僅複製備份]** 來建立僅複製備份。</span><span class="sxs-lookup"><span data-stu-id="38a66-152">Optionally, you can select **Copy Only Backup** to create a copy-only backup.</span></span> <span data-ttu-id="38a66-153">「只複製備份」  是與傳統 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份順序無關的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份。</span><span class="sxs-lookup"><span data-stu-id="38a66-153">A *copy-only backup* is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup that is independent of the sequence of conventional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span> <span data-ttu-id="38a66-154">如需詳細資訊，請參閱[只複製備份 &#40;SQL Server&#41;](copy-only-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="38a66-154">For more information, see [Copy-Only Backups &#40;SQL Server&#41;](copy-only-backups-sql-server.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="38a66-155">選取 **[差異]** 選項時，您無法建立「只複製」備份。</span><span class="sxs-lookup"><span data-stu-id="38a66-155">When the **Differential** option is selected, you cannot create a copy-only backup.</span></span>  
  
8.  <span data-ttu-id="38a66-156">針對 [**備份元件**]，按一下 `Database` 。</span><span class="sxs-lookup"><span data-stu-id="38a66-156">For **Backup component**, click `Database`.</span></span>  
  
9. <span data-ttu-id="38a66-157">接受 **[名稱]** 文字方塊中建議的預設備份組名稱，或者輸入不同的備份組名稱。</span><span class="sxs-lookup"><span data-stu-id="38a66-157">Either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.</span></span>  
  
10. <span data-ttu-id="38a66-158">(選擇性) 在 **[描述]** 文字方塊中輸入備份組的描述。</span><span class="sxs-lookup"><span data-stu-id="38a66-158">Optionally, in the **Description** text box, enter a description of the backup set.</span></span>  
  
11. <span data-ttu-id="38a66-159">按一下 **[磁碟]**、 **[磁帶]** 或 **[URL]** 來選擇備份目的地的類型。</span><span class="sxs-lookup"><span data-stu-id="38a66-159">Choose the type of backup destination by clicking **Disk**, **Tape** or **URL**.</span></span> <span data-ttu-id="38a66-160">若要選取包含單一媒體集的磁碟或磁帶機 (最多 64 個) 的路徑，請按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="38a66-160">To select the paths of up to 64 disk or tape drives containing a single media set, click **Add**.</span></span> <span data-ttu-id="38a66-161">選取的路徑會在 **[備份至]** 清單方塊中顯示。</span><span class="sxs-lookup"><span data-stu-id="38a66-161">The selected paths are displayed in the **Backup to** list box.</span></span>  
  
     <span data-ttu-id="38a66-162">若要移除備份目的地，請選取目的地，然後按一下 **[移除]** 。</span><span class="sxs-lookup"><span data-stu-id="38a66-162">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="38a66-163">若要檢視備份目的地的內容，請選取目的地，然後按一下 **[內容]** 。</span><span class="sxs-lookup"><span data-stu-id="38a66-163">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
12. <span data-ttu-id="38a66-164">若要檢視或選取媒體選項，請按一下 **[選取頁面]** 窗格中的 **[媒體選項]** 。</span><span class="sxs-lookup"><span data-stu-id="38a66-164">To view or select the media options, click **Media Options** in the **Select a page** pane.</span></span>  
  
13. <span data-ttu-id="38a66-165">按下列項目之一，以選取 **[覆寫媒體]** 選項：</span><span class="sxs-lookup"><span data-stu-id="38a66-165">Select an **Overwrite Media** option, by clicking one of the following:</span></span>  
  
    -   <span data-ttu-id="38a66-166">**備份至現有的媒體集**</span><span class="sxs-lookup"><span data-stu-id="38a66-166">**Back up to the existing media set**</span></span>  
  
         <span data-ttu-id="38a66-167">針對這個選項，按一下 **[附加至現有的備份組]** 或 **[覆寫所有現有的備份組]** 。</span><span class="sxs-lookup"><span data-stu-id="38a66-167">For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.</span></span> <span data-ttu-id="38a66-168">如需詳細資訊，請參閱 [媒體集、媒體家族與備份組 &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="38a66-168">For more information, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
         <span data-ttu-id="38a66-169">另外，也可以選取 **[檢查媒體集名稱及備份組是否逾期]** ，以讓備份作業確認媒體集及備份組逾期的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="38a66-169">Optionally, select **Check media set name and backup set expiration** to cause the backup operation to verify the date and time at which the media set and backup set expire.</span></span>  
  
         <span data-ttu-id="38a66-170">另外，也可以在 **[媒體集名稱]** 文字方塊中輸入名稱。</span><span class="sxs-lookup"><span data-stu-id="38a66-170">Optionally, enter a name in the **Media set name** text box.</span></span> <span data-ttu-id="38a66-171">如果未指定名稱，就會建立一個空白名稱的媒體集。</span><span class="sxs-lookup"><span data-stu-id="38a66-171">If no name is specified, a media set with a blank name is created.</span></span> <span data-ttu-id="38a66-172">如果您指定媒體集名稱，就會檢查媒體 (磁帶或磁碟)，以查看實際名稱是否與您在此處輸入的名稱相符。</span><span class="sxs-lookup"><span data-stu-id="38a66-172">If you specify a media set name, the media (tape or disk) is checked to see whether the actual name matches the name you enter here.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="38a66-173">如果在 **[一般]** 頁面中選取 **[URL]** 做為備份目的地，則會停用這個選項。</span><span class="sxs-lookup"><span data-stu-id="38a66-173">This option is disabled if you selected **URL** as the backup destination in the **General** page.</span></span> <span data-ttu-id="38a66-174">如需詳細資訊，請參閱[備份資料庫 &#40;媒體選項頁面&#41;](back-up-database-media-options-page.md)</span><span class="sxs-lookup"><span data-stu-id="38a66-174">For more information, see [Back Up Database &#40;Media Options Page&#41;](back-up-database-media-options-page.md)</span></span>  
        >   
        >  <span data-ttu-id="38a66-175">如果您打算使用加密，請不要選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="38a66-175">If you plan to use encryption, do not select this option.</span></span> <span data-ttu-id="38a66-176">如果您選取這個選項， **[備份選項]** 頁面中的加密選項將會停用。</span><span class="sxs-lookup"><span data-stu-id="38a66-176">If you select this option, the encryption options in the **Backup Options** page will be disabled.</span></span> <span data-ttu-id="38a66-177">當附加至現有的備份組時，不支援加密。</span><span class="sxs-lookup"><span data-stu-id="38a66-177">Encryption is not supported when appending to the existing backup set.</span></span>  
  
    -   <span data-ttu-id="38a66-178">**備份至新的媒體集，並清除所有現有的備份組**</span><span class="sxs-lookup"><span data-stu-id="38a66-178">**Back up to a new media set, and erase all existing backup sets**</span></span>  
  
         <span data-ttu-id="38a66-179">針對這個選項，在 **[新媒體集名稱]** 文字方塊中輸入名稱，然後選擇性在 **[新媒體集描述]** 文字方塊中描述媒體集。</span><span class="sxs-lookup"><span data-stu-id="38a66-179">For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="38a66-180">如果在 **[一般]** 頁面中選取 **[URL]** ，則會停用這個選項。</span><span class="sxs-lookup"><span data-stu-id="38a66-180">This option is disabled if you selected **URL** in the **General** page.</span></span> <span data-ttu-id="38a66-181">備份至 Azure 儲存體時，不支援這些動作。</span><span class="sxs-lookup"><span data-stu-id="38a66-181">These actions are not supported when backing up to Azure storage.</span></span>  
  
14. <span data-ttu-id="38a66-182">在 [**可靠性**] 區段中，選擇性地檢查：</span><span class="sxs-lookup"><span data-stu-id="38a66-182">In the **Reliability** section, optionally check:</span></span>  
  
    -   <span data-ttu-id="38a66-183">**[完成後驗證備份]** 。</span><span class="sxs-lookup"><span data-stu-id="38a66-183">**Verify backup when finished**.</span></span>  
  
    -   <span data-ttu-id="38a66-184">**[寫入媒體之前執行總和檢查碼]** 及/或 **[發生總和檢查碼錯誤時繼續]** 。</span><span class="sxs-lookup"><span data-stu-id="38a66-184">**Perform checksum before writing to media**, and, optionally, **Continue on checksum error**.</span></span> <span data-ttu-id="38a66-185">如需總和檢查碼的相關資訊，請參閱[在備份和還原期間可能的媒體錯誤 &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="38a66-185">For information on checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
15. <span data-ttu-id="38a66-186">如果是備份至磁帶機 (在 [一般]  頁面的 [目的地]  區段中指定)，[備份後卸載磁帶]  選項會啟用供選擇。</span><span class="sxs-lookup"><span data-stu-id="38a66-186">If you are backing up to a tape drive (as specified in the **Destination** section of the **General** page), the **Unload the tape after backup** option is active.</span></span> <span data-ttu-id="38a66-187">按一下這個選項會啟動 **[卸載之前倒轉磁帶]** 選項。</span><span class="sxs-lookup"><span data-stu-id="38a66-187">Clicking this option activates the **Rewind the tape before unloading** option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="38a66-188">除非您備份的是交易記錄檔 (依 [一般]  頁面的 [備份類型]  區段中的指定)，否則 [交易記錄檔]  區段中的選項為非使用中。</span><span class="sxs-lookup"><span data-stu-id="38a66-188">The options in the **Transaction log** section are inactive unless you are backing up a transaction log (as specified in the **Backup type** section of the **General** page).</span></span>  
  
16. <span data-ttu-id="38a66-189">若要檢視或選取備份選項，請按一下 **[選取頁面]** 窗格中的 **[備份選項]** 。</span><span class="sxs-lookup"><span data-stu-id="38a66-189">To view or select the backup options, click **Backup Options** in the **Select a page** pane.</span></span>  
  
17. <span data-ttu-id="38a66-190">指定備份組逾期的時間，和不需明確略過逾期資料的驗證即可覆寫的時間：</span><span class="sxs-lookup"><span data-stu-id="38a66-190">Specify when the backup set will expire and can be overwritten without explicitly skipping verification of the expiration data:</span></span>  
  
    -   <span data-ttu-id="38a66-191">若要讓備份組在特定的天數後過期，請按一下 [之後]  \(預設選項)，然後輸入備份組建立之後將會過期的天數。</span><span class="sxs-lookup"><span data-stu-id="38a66-191">To have the backup set expire after a specific number of days, click **After** (the default option), and enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="38a66-192">這個值可以介於 0 到 99999 日之間；值為 0 日意指備份組永遠不會過期。</span><span class="sxs-lookup"><span data-stu-id="38a66-192">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="38a66-193">預設值設定于 [**伺服器屬性**] 對話方塊的 [**預設備份媒體保留 (（以天**為單位）) ] 選項 ([資料庫設定] 頁面) 。</span><span class="sxs-lookup"><span data-stu-id="38a66-193">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (Database Settings Page).</span></span> <span data-ttu-id="38a66-194">若要存取，請以滑鼠右鍵按一下物件總管中的伺服器名稱並選取 [屬性]，然後選取 [資料庫設定]  頁面。</span><span class="sxs-lookup"><span data-stu-id="38a66-194">To access this, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="38a66-195">若要讓備份組在特定日期過期，請按一下 **[於]** ，然後輸入備份組將過期的日期。</span><span class="sxs-lookup"><span data-stu-id="38a66-195">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
         <span data-ttu-id="38a66-196">如需備份到期日的詳細資訊，請參閱 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="38a66-196">For more information about backup expiration dates, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
18. [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="38a66-197">和更新的版本支援 [備份壓縮](backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="38a66-197">and later supports [backup compression](backup-compression-sql-server.md).</span></span> <span data-ttu-id="38a66-198">依預設，備份壓縮與否取決於 **備份壓縮預設** 伺服器組態選項的值。</span><span class="sxs-lookup"><span data-stu-id="38a66-198">By default, whether a backup is compressed depends on the value of the **backup-compression default** server configuration option.</span></span> <span data-ttu-id="38a66-199">不過，不論目前的伺服器層級預設值為何，您都可以透過核取 [壓縮備份]  壓縮備份，而且可以透過核取 [不要壓縮備份]  防止壓縮。</span><span class="sxs-lookup"><span data-stu-id="38a66-199">However, regardless of the current server-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.</span></span>  
  
     <span data-ttu-id="38a66-200">**若要檢視或變更目前的備份壓縮預設值**</span><span class="sxs-lookup"><span data-stu-id="38a66-200">**To view or change the current backup compression default**</span></span>  
  
    -   [<span data-ttu-id="38a66-201">檢視或設定 backup compression default 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="38a66-201">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
19. <span data-ttu-id="38a66-202">指定是否要對備份使用加密。</span><span class="sxs-lookup"><span data-stu-id="38a66-202">Specify whether to use encryption for the backup.</span></span> <span data-ttu-id="38a66-203">選取要加密步驟所要使用的加密演算法，並提供現有憑證或非對稱金鑰清單中的憑證或非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="38a66-203">Select an encryption algorithm to use for the encryption step, and provide a Certificate or Asymmetric key from a list of existing certificates or asymmetric keys.</span></span> <span data-ttu-id="38a66-204">SQL Server 2014 或更新版本支援加密。</span><span class="sxs-lookup"><span data-stu-id="38a66-204">Encryption is supported in SQL Server 2014 or later.</span></span> <span data-ttu-id="38a66-205">如需加密選項的詳細資訊，請參閱 [備份資料庫 &#40;備份選項頁面&#41;](back-up-database-backup-options-page.md)。</span><span class="sxs-lookup"><span data-stu-id="38a66-205">For more details on the Encryption options, see [Back Up Database &#40;Backup Options Page&#41;](back-up-database-backup-options-page.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="38a66-206">或者，您可以使用「維護計畫精靈」來建立資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="38a66-206">Alternatively, you can use the Maintenance Plan Wizard to create database backups.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="38a66-207">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="38a66-207">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-full-database-backup"></a><span data-ttu-id="38a66-208">建立完整資料庫備份</span><span class="sxs-lookup"><span data-stu-id="38a66-208">To create a full database backup</span></span>  
  
1.  <span data-ttu-id="38a66-209">執行 BACKUP DATABASE 陳述式以建立完整資料庫備份，請指定：</span><span class="sxs-lookup"><span data-stu-id="38a66-209">Execute the BACKUP DATABASE statement to create the full database backup, specifying:</span></span>  
  
    -   <span data-ttu-id="38a66-210">欲備份的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="38a66-210">The name of the database to back up.</span></span>  
  
    -   <span data-ttu-id="38a66-211">寫入完整資料庫備份的備份裝置。</span><span class="sxs-lookup"><span data-stu-id="38a66-211">The backup device where the full database backup is written.</span></span>  
  
     <span data-ttu-id="38a66-212">完整資料庫備份的基本 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語法如下：</span><span class="sxs-lookup"><span data-stu-id="38a66-212">The basic [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax for a full database backup is:</span></span>  
  
     <span data-ttu-id="38a66-213">BACKUP DATABASE *database*</span><span class="sxs-lookup"><span data-stu-id="38a66-213">BACKUP DATABASE *database*</span></span>  
  
     <span data-ttu-id="38a66-214">TO *backup_device* [ **,** ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="38a66-214">TO *backup_device* [ **,**...*n* ]</span></span>  
  
     <span data-ttu-id="38a66-215">[ WITH *with_options* [ **,** ...*o* ] ] ;</span><span class="sxs-lookup"><span data-stu-id="38a66-215">[ WITH *with_options* [ **,**...*o* ] ] ;</span></span>  
  
    |<span data-ttu-id="38a66-216">選項</span><span class="sxs-lookup"><span data-stu-id="38a66-216">Option</span></span>|<span data-ttu-id="38a66-217">描述</span><span class="sxs-lookup"><span data-stu-id="38a66-217">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="38a66-218">*database*</span><span class="sxs-lookup"><span data-stu-id="38a66-218">*database*</span></span>|<span data-ttu-id="38a66-219">為要備份的資料庫。</span><span class="sxs-lookup"><span data-stu-id="38a66-219">Is the database that is to be backed up.</span></span>|  
    |<span data-ttu-id="38a66-220">*backup_device* [ **,** ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="38a66-220">*backup_device* [ **,**...*n* ]</span></span>|<span data-ttu-id="38a66-221">指定一份清單，列出備份作業可使用的 1 到 64 個備份裝置。</span><span class="sxs-lookup"><span data-stu-id="38a66-221">Specifies a list of from 1 to 64 backup devices to use for the backup operation.</span></span> <span data-ttu-id="38a66-222">您可以指定實體備份裝置，或者指定對應的邏輯備份裝置 (若已經定義)。</span><span class="sxs-lookup"><span data-stu-id="38a66-222">You can specify a physical backup device, or you can specify a corresponding logical backup device, if already defined.</span></span> <span data-ttu-id="38a66-223">若要指定實體備份裝置，請使用 DISK 或 TAPE 選項：</span><span class="sxs-lookup"><span data-stu-id="38a66-223">To specify a physical backup device, use the DISK or TAPE option:</span></span><br /><br /> <span data-ttu-id="38a66-224">{ DISK &#124; TAPE } **=** _physical_backup_device_name_</span><span class="sxs-lookup"><span data-stu-id="38a66-224">{ DISK &#124; TAPE } **=**_physical_backup_device_name_</span></span><br /><br /> <span data-ttu-id="38a66-225">如需詳細資訊，請參閱 [備份裝置 &#40;SQL Server&#41;](backup-devices-sql-server.md)執行個體上建立資料庫備份，就需要這個選項。</span><span class="sxs-lookup"><span data-stu-id="38a66-225">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>|  
    |<span data-ttu-id="38a66-226">WITH *with_options* [ **,** ...*o* ]</span><span class="sxs-lookup"><span data-stu-id="38a66-226">WITH *with_options* [ **,**...*o* ]</span></span>|<span data-ttu-id="38a66-227">或者，也可以指定一個或多個其他選項 *o*。</span><span class="sxs-lookup"><span data-stu-id="38a66-227">Optionally, specifies one or more additional options, *o*.</span></span> <span data-ttu-id="38a66-228">如需有關選項基本概念的詳細資訊，請參閱步驟 2。</span><span class="sxs-lookup"><span data-stu-id="38a66-228">For information about some of the basic with options, see step 2.</span></span>|  
  
2.  <span data-ttu-id="38a66-229">選擇性地指定一或多個 WITH 選項。</span><span class="sxs-lookup"><span data-stu-id="38a66-229">Optionally, specify one or more WITH options.</span></span> <span data-ttu-id="38a66-230">這裡描述的是一些基本的 WITH 選項。</span><span class="sxs-lookup"><span data-stu-id="38a66-230">A few basic WITH options are described here.</span></span> <span data-ttu-id="38a66-231">如需所有 WITH 選項的資訊，請參閱 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="38a66-231">For information about all the WITH options, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  
  
    -   <span data-ttu-id="38a66-232">基本備份組 WITH 選項：</span><span class="sxs-lookup"><span data-stu-id="38a66-232">Basic backup set WITH options:</span></span>  
  
         <span data-ttu-id="38a66-233">{ COMPRESSION | NO_COMPRESSION }</span><span class="sxs-lookup"><span data-stu-id="38a66-233">{ COMPRESSION | NO_COMPRESSION }</span></span>  
         <span data-ttu-id="38a66-234">只有在 [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] 及更新的版本中，才會指定是否要在此備份上執行 [備份壓縮](backup-compression-sql-server.md) ，以覆寫伺服器層級的預設值。</span><span class="sxs-lookup"><span data-stu-id="38a66-234">In [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] and later only, specifies whether [backup compression](backup-compression-sql-server.md) is performed on this backup, overriding the server-level default.</span></span>  
  
         <span data-ttu-id="38a66-235">ENCRYPTION (ALGORITHM,  SERVER CERTIFICATE |ASYMMETRIC KEY)</span><span class="sxs-lookup"><span data-stu-id="38a66-235">ENCRYPTION (ALGORITHM,  SERVER CERTIFICATE |ASYMMETRIC KEY)</span></span>  
         <span data-ttu-id="38a66-236">只有在 SQL Server 2014 或更新的版本中，才能指定要使用的加密演算法以及憑證或非對稱金鑰來維護加密的安全。</span><span class="sxs-lookup"><span data-stu-id="38a66-236">In SQL Server 2014 or later only, specify the encryption algorithm to use, and the Certificate or Asymmetric key to use to secure the encryption.</span></span>  
  
         <span data-ttu-id="38a66-237">描述 **=** { **' *`text`* '**  |  **@** _text_variable_ }</span><span class="sxs-lookup"><span data-stu-id="38a66-237">DESCRIPTION **=** { **'*`text`*'** | **@**_text_variable_ }</span></span>  
         <span data-ttu-id="38a66-238">指定描述備份組的自由形式文字。</span><span class="sxs-lookup"><span data-stu-id="38a66-238">Specifies the free-form text that describes the backup set.</span></span> <span data-ttu-id="38a66-239">這個字串最多可有 255 個字元。</span><span class="sxs-lookup"><span data-stu-id="38a66-239">The string can have a maximum of 255 characters.</span></span>  
  
         <span data-ttu-id="38a66-240">名稱 **=** { *backup_set_name*  |  **@** _backup_set_name_var_ }</span><span class="sxs-lookup"><span data-stu-id="38a66-240">NAME **=** { *backup_set_name* | **@**_backup_set_name_var_ }</span></span>  
         <span data-ttu-id="38a66-241">指定備份組的名稱。</span><span class="sxs-lookup"><span data-stu-id="38a66-241">Specifies the name of the backup set.</span></span> <span data-ttu-id="38a66-242">名稱最多可有 128 個字元。</span><span class="sxs-lookup"><span data-stu-id="38a66-242">Names can have a maximum of 128 characters.</span></span> <span data-ttu-id="38a66-243">如果未指定 NAME，它就是空白。</span><span class="sxs-lookup"><span data-stu-id="38a66-243">If NAME is not specified, it is blank.</span></span>  
  
    -   <span data-ttu-id="38a66-244">基本備份組 WITH 選項：</span><span class="sxs-lookup"><span data-stu-id="38a66-244">Basic backup set WITH options:</span></span>  
  
         <span data-ttu-id="38a66-245">根據預設，BACKUP 會將備份附加到現有的媒體集，以保留現有的備份組。</span><span class="sxs-lookup"><span data-stu-id="38a66-245">By default, BACKUP appends the backup to an existing media set, preserving existing backup sets.</span></span> <span data-ttu-id="38a66-246">若要明確指定這項，請使用 NOINIT 選項。</span><span class="sxs-lookup"><span data-stu-id="38a66-246">To explicitly specify this, use the NOINIT option.</span></span> <span data-ttu-id="38a66-247">如需附加至現有備份組的資訊，請參閱 [媒體集、媒體家族與備份組 &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="38a66-247">For information about appending to existing backup sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
         <span data-ttu-id="38a66-248">另外，若要格式化備份媒體，請使用 FORMAT 選項：</span><span class="sxs-lookup"><span data-stu-id="38a66-248">Alternatively, to format the backup media, use the FORMAT option:</span></span>  
  
         <span data-ttu-id="38a66-249">FORMAT [ **，** MEDIANAME **=** { *media_name*  |  **@** _media_name_variable_ }] [ **，** MEDIADESCRIPTION **=** { *text*  |  **@** _text_variable_ }]</span><span class="sxs-lookup"><span data-stu-id="38a66-249">FORMAT [ **,** MEDIANAME**=** { *media_name* | **@**_media_name_variable_ } ] [ **,** MEDIADESCRIPTION **=** { *text* | **@**_text_variable_ } ]</span></span>  
         <span data-ttu-id="38a66-250">當您第一次使用媒體或是想要覆寫所有現有的資料時，請使用 FORMAT 子句。</span><span class="sxs-lookup"><span data-stu-id="38a66-250">Use the FORMAT clause when you are using media for the first time or you want to overwrite all existing data.</span></span> <span data-ttu-id="38a66-251">選擇性地為新的媒體指派媒體名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="38a66-251">Optionally, assign the new media a media name and description.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="38a66-252">當您使用 BACKUP 陳述式的 FORMAT 子句時要非常小心，因為它會破壞備份媒體先前所儲存的任何備份。</span><span class="sxs-lookup"><span data-stu-id="38a66-252">Use extreme caution when you are using the FORMAT clause of the BACKUP statement because this destroys any backups that were previously stored on the backup media.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="38a66-253">範例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="38a66-253">Examples (Transact-SQL)</span></span>  
  
#### <a name="a-backing-up-to-a-disk-device"></a><span data-ttu-id="38a66-254">A.</span><span class="sxs-lookup"><span data-stu-id="38a66-254">A.</span></span> <span data-ttu-id="38a66-255">備份到磁碟裝置</span><span class="sxs-lookup"><span data-stu-id="38a66-255">Backing up to a disk device</span></span>  
 <span data-ttu-id="38a66-256">下列範例使用 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 建立新的媒體集，以將整個 `FORMAT` 資料庫備份至磁碟。</span><span class="sxs-lookup"><span data-stu-id="38a66-256">The following example backs up the complete [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to disk, by using `FORMAT` to create a new media set.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.Bak'  
   WITH FORMAT,  
      MEDIANAME = 'Z_SQLServerBackups',  
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
#### <a name="b-backing-up-to-a-tape-device"></a><span data-ttu-id="38a66-257">B.</span><span class="sxs-lookup"><span data-stu-id="38a66-257">B.</span></span> <span data-ttu-id="38a66-258">備份到磁帶裝置</span><span class="sxs-lookup"><span data-stu-id="38a66-258">Backing up to a tape device</span></span>  
 <span data-ttu-id="38a66-259">下列範例會將完整的 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]資料庫備份到磁帶上，並將備份附加到先前的備份中。</span><span class="sxs-lookup"><span data-stu-id="38a66-259">The following example backs up the complete [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]database to tape, appending the backup to the previous backups.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
   TO TAPE = '\\.\Tape0'  
   WITH NOINIT,  
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
#### <a name="c-backing-up-to-a-logical-tape-device"></a><span data-ttu-id="38a66-260">C.</span><span class="sxs-lookup"><span data-stu-id="38a66-260">C.</span></span> <span data-ttu-id="38a66-261">備份到邏輯磁帶裝置</span><span class="sxs-lookup"><span data-stu-id="38a66-261">Backing up to a logical tape device</span></span>  
 <span data-ttu-id="38a66-262">下列範例會為磁帶機建立邏輯備份裝置。</span><span class="sxs-lookup"><span data-stu-id="38a66-262">The following example creates a logical backup device for a tape drive.</span></span> <span data-ttu-id="38a66-263">這個範例會將完整的 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫備份至該裝置。</span><span class="sxs-lookup"><span data-stu-id="38a66-263">The example then backs up the complete [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to that device.</span></span>  
  
```sql  
-- Create a logical backup device,   
-- AdventureWorks2012_Bak_Tape, for tape device \\.\tape0.  
USE master;  
GO  
EXEC sp_addumpdevice 'tape', 'AdventureWorks2012_Bak_Tape', '\\.\tape0'; USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
   TO AdventureWorks2012_Bak_Tape  
   WITH FORMAT,  
      MEDIANAME = 'AdventureWorks2012_Bak_Tape',  
      MEDIADESCRIPTION = '\\.\tape0',   
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="38a66-264">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="38a66-264">Using PowerShell</span></span>  
  
1.  <span data-ttu-id="38a66-265">使用 `Backup-SqlDatabase` 指令程式。</span><span class="sxs-lookup"><span data-stu-id="38a66-265">Use the `Backup-SqlDatabase` cmdlet.</span></span> <span data-ttu-id="38a66-266">若要明確指出這是完整資料庫備份，請指定 **-BackupAction**參數及其預設值 `Database` 。</span><span class="sxs-lookup"><span data-stu-id="38a66-266">To explicitly indicate that this is a full database backup, specify the **-BackupAction**  parameter with its default value, `Database`.</span></span> <span data-ttu-id="38a66-267">此參數在完整資料庫備份下是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="38a66-267">This parameter is optional for full database backups.</span></span>  
  
     <span data-ttu-id="38a66-268">下列範例會在伺服器執行個體 `MyDB` 的預設備份位置，建立 `Computer\Instance`資料庫的完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="38a66-268">The following example creates a full database backup of the `MyDB` database to the default backup location of the server instance `Computer\Instance`.</span></span> <span data-ttu-id="38a66-269">這個範例指定了選擇性的 `-BackupAction Database`。</span><span class="sxs-lookup"><span data-stu-id="38a66-269">Optionally, this example specifies `-BackupAction Database`.</span></span>  
  
    ```powershell
    Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Database  
    ```  
  
 <span data-ttu-id="38a66-270">**若要設定和使用 SQL Server PowerShell 提供者**</span><span class="sxs-lookup"><span data-stu-id="38a66-270">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="38a66-271">SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="38a66-271">SQL Server PowerShell Provider</span></span>](../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="38a66-272">相關工作</span><span class="sxs-lookup"><span data-stu-id="38a66-272">Related Tasks</span></span>  
  
-   [<span data-ttu-id="38a66-273">備份資料庫 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="38a66-273">Back Up a Database (SQL Server)</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="38a66-274">建立差異資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="38a66-274">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="38a66-275">還原資料庫備份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="38a66-275">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="38a66-276">在簡單復原模式下還原資料庫備份 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="38a66-276">Restore a Database Backup Under the Simple Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)  
  
-   [<span data-ttu-id="38a66-277">在完整復原模式下將資料庫還原至失敗點 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="38a66-277">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="38a66-278">將資料庫還原到新位置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="38a66-278">Restore a Database to a New Location &#40;SQL Server&#41;</span></span>](restore-a-database-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="38a66-279">使用維護計畫精靈</span><span class="sxs-lookup"><span data-stu-id="38a66-279">Use the Maintenance Plan Wizard</span></span>](../maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="38a66-280">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38a66-280">See Also</span></span>  
 <span data-ttu-id="38a66-281">[備份概觀 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="38a66-281">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="38a66-282">[交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="38a66-282">[Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="38a66-283">[媒體集、媒體家族與備份組 &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="38a66-283">[Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span></span>  
 <span data-ttu-id="38a66-284">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="38a66-284">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 <span data-ttu-id="38a66-285">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="38a66-285">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="38a66-286">[備份資料庫 &#40;一般頁面&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="38a66-286">[Back Up Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="38a66-287">[備份資料庫 &#40;備份選項頁面&#41;](back-up-database-backup-options-page.md) </span><span class="sxs-lookup"><span data-stu-id="38a66-287">[Back Up Database &#40;Backup Options Page&#41;](back-up-database-backup-options-page.md) </span></span>  
 <span data-ttu-id="38a66-288">[差異備份 &#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="38a66-288">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="38a66-289">完整資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="38a66-289">Full Database Backups &#40;SQL Server&#41;</span></span>](full-database-backups-sql-server.md)  
