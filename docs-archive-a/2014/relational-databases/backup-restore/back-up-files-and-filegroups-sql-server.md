---
title: 備份檔案和檔案群組 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up filegroups [SQL Server]
- file backups [SQL Server], how-to topics
- backing up files [SQL Server]
- backups [SQL Server], creating
- filegroups [SQL Server], backing up
ms.assetid: a0d3a567-7d8b-4cfe-a505-d197b9a51f70
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7affc90b064febaa70e0a67108074f412b4bbf00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585495"
---
# <a name="back-up-files-and-filegroups-sql-server"></a><span data-ttu-id="ab7e8-102">備份檔案和檔案群組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab7e8-102">Back Up Files and Filegroups (SQL Server)</span></span>
  <span data-ttu-id="ab7e8-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 PowerShell，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中備份檔案與檔案群組。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-103">This topic describes how to back up files and filegroups in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or PowerShell.</span></span> <span data-ttu-id="ab7e8-104">當完整的資料庫備份因資料庫大小和效能需求而變得不可行時，您可以建立檔案備份來代替。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-104">When the database size and performance requirements make a full database backup impractical, you can create a file backup instead.</span></span> <span data-ttu-id="ab7e8-105">*「檔案備份」* (File Backup) 包含一或多個檔案 (或檔案群組) 中的所有資料。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-105">A *file backup* contains all the data in one or more files (or filegroups).</span></span> <span data-ttu-id="ab7e8-106">如需詳細資訊，請參閱 [完整檔案備份 &#40;SQL Server&#41;](full-file-backups-sql-server.md) 和 [差異備份 &#40;SQL Server&#41;](differential-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-106">For more information about file backups, see [Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md) and [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="ab7e8-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="ab7e8-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ab7e8-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="ab7e8-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ab7e8-109">限制事項</span><span class="sxs-lookup"><span data-stu-id="ab7e8-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ab7e8-110">建議</span><span class="sxs-lookup"><span data-stu-id="ab7e8-110">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="ab7e8-111">安全性</span><span class="sxs-lookup"><span data-stu-id="ab7e8-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ab7e8-112">**若要使用下列項目備份檔案與檔案群組：**</span><span class="sxs-lookup"><span data-stu-id="ab7e8-112">**To back up files and filegroups, using:**</span></span>  
  
     [<span data-ttu-id="ab7e8-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ab7e8-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ab7e8-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ab7e8-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="ab7e8-115">PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab7e8-115">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ab7e8-116">開始之前</span><span class="sxs-lookup"><span data-stu-id="ab7e8-116">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ab7e8-117">限制事項</span><span class="sxs-lookup"><span data-stu-id="ab7e8-117">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="ab7e8-118">在明確或隱含的交易中，並不允許使用 BACKUP 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-118">The BACKUP statement is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="ab7e8-119">在簡單復原模式下，必須將所有的讀取/寫入檔案備份在一起。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-119">Under the simple recovery model, read/write files must all be backed up together.</span></span> <span data-ttu-id="ab7e8-120">這有助於確保資料庫還原到一致的時間點。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-120">This helps make sure that the database can be restored to a consistent point in time.</span></span> <span data-ttu-id="ab7e8-121">不要個別指定每一個讀取/寫入檔案或檔案群組，請改用 READ_WRITE_FILEGROUPS 選項。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-121">Instead of individually specifying each read/write file or filegroup, use the READ_WRITE_FILEGROUPS option.</span></span> <span data-ttu-id="ab7e8-122">這個選項會備份資料庫中的所有讀取/寫入檔案群組。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-122">This option backs up all the read/write filegroups in the database.</span></span> <span data-ttu-id="ab7e8-123">藉由指定 READ_WRITE_FILEGROUPS 所建立的備份即稱為「*部份備份*」。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-123">A backup that is created by specifying READ_WRITE_FILEGROUPS is known as a *partial backup*.</span></span> <span data-ttu-id="ab7e8-124">如需詳細資訊，請參閱[部分備份 &#40;SQL Server&#41;](partial-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-124">For more information, see [Partial Backups &#40;SQL Server&#41;](partial-backups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="ab7e8-125">如需基本備份概念的詳細資訊，請參閱 [備份概觀 &#40;SQL Server&#41;](backup-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-125">For more information about limitations and restrictions, see [Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="ab7e8-126">建議</span><span class="sxs-lookup"><span data-stu-id="ab7e8-126">Recommendations</span></span>  
  
-   <span data-ttu-id="ab7e8-127">根據預設，每項成功的備份作業都會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔與系統事件記錄檔中，加入一個項目。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-127">By default, every successful backup operation adds an entry in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and in the system event log.</span></span> <span data-ttu-id="ab7e8-128">如果您經常備份記錄檔，這些成功訊息可能會快速累積，因而產生龐大的錯誤記錄檔，讓您難以尋找其他訊息。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-128">If you back up the log very frequently, these success messages accumulate quickly, resulting in huge error logs that can make finding other messages difficult.</span></span> <span data-ttu-id="ab7e8-129">在這類情況下，如果沒有任何指令碼相依於這些記錄項目，您就可以使用追蹤旗標 3226 來隱藏這些記錄項目。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-129">In such cases you can suppress these log entries by using trace flag 3226 if none of your scripts depend on those entries.</span></span> <span data-ttu-id="ab7e8-130">如需詳細資訊，請參閱[追蹤旗標 &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-130">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ab7e8-131">Security</span><span class="sxs-lookup"><span data-stu-id="ab7e8-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ab7e8-132">權限</span><span class="sxs-lookup"><span data-stu-id="ab7e8-132">Permissions</span></span>  
 <span data-ttu-id="ab7e8-133">BACKUP DATABASE 和 BACKUP LOG 權限預設為 **sysadmin** 固定伺服器角色以及 **db_owner** 和 **db_backupoperator** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-133">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="ab7e8-134">備份裝置實體檔案的擁有權和權限問題可能會干擾備份作業。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-134">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ab7e8-135">必須能夠讀取和寫入裝置；執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的帳戶必須具備寫入權限。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-135">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="ab7e8-136">不過，在系統資料表中加入備份裝置項目的 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)並不會檢查檔案存取權限。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-136">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="ab7e8-137">當您嘗試備份或還原時，存取實體資源之前不一定會出現備份裝置實體檔案的這些問題。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-137">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ab7e8-138">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ab7e8-138">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-back-up-database-files-and-filegroups"></a><span data-ttu-id="ab7e8-139">備份資料庫檔案與檔案群組</span><span class="sxs-lookup"><span data-stu-id="ab7e8-139">To back up database files and filegroups</span></span>  
  
1.  <span data-ttu-id="ab7e8-140">連接到適當的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體之後，請在 [物件總管] 中按一下伺服器名稱以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-140">After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="ab7e8-141">展開 **[資料庫]** ，然後視資料庫而定，選取使用者資料庫，或者展開 **[系統資料庫]** 並選取一個系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-141">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="ab7e8-142">以滑鼠右鍵按一下資料庫，指向 **[工作]** ，然後按一下 **[備份]** 。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-142">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="ab7e8-143">會出現 **[備份資料庫]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-143">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="ab7e8-144">在 **[資料庫]** 清單中，確認資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-144">In the **Database** list, verify the database name.</span></span> <span data-ttu-id="ab7e8-145">您可以選擇性從清單中選取不同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-145">You can optionally select a different database from the list.</span></span>  
  
5.  <span data-ttu-id="ab7e8-146">在 **[備份類型]** 清單中，選取 **[完整]** 或 **[差異]** 。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-146">In the **Backup type** list, select **Full** or **Differential**.</span></span>  
  
6.  <span data-ttu-id="ab7e8-147">若是 **[備份元件]** 選項，請按一下 **[檔案與檔案群組]** 。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-147">For the **Backup component** option, click **File and Filegroups**.</span></span>  
  
7.  <span data-ttu-id="ab7e8-148">在 **[選取檔案與檔案群組]** 對話方塊中，選取您要備份的檔案及檔案群組。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-148">In the **Select Files and Filegroups** dialog box, select the files and filegroups you want to back up.</span></span> <span data-ttu-id="ab7e8-149">您可以選取一或多個個別檔案，或選取檔案群組的方塊，以便自動選取該檔案群組中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-149">You can select one or more individual files or check the box for a filegroup to automatically select all the files in that filegroup.</span></span>  
  
8.  <span data-ttu-id="ab7e8-150">接受 **[名稱]** 文字方塊中建議的預設備份組名稱，或者輸入不同的備份組名稱。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-150">Either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.</span></span>  
  
9. <span data-ttu-id="ab7e8-151">(選擇性) 在 **[描述]** 文字方塊中輸入備份組的描述。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-151">Optionally, in the **Description** text box, enter a description of the backup set.</span></span>  
  
10. <span data-ttu-id="ab7e8-152">指定備份組會在何時過期：</span><span class="sxs-lookup"><span data-stu-id="ab7e8-152">Specify when the backup set will expire:</span></span>  
  
    -   <span data-ttu-id="ab7e8-153">若要讓備份組在特定天數後過期，請按一下 [於指定天數之後]\*\*\*\* (預設選項)。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-153">To have the backup set expire after a specific number of days, click **After** (the default option).</span></span> <span data-ttu-id="ab7e8-154">然後，輸入此備份組在建立之後將會到期的天數。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-154">Then, enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="ab7e8-155">這個值可以介於 0 到 99999 日之間；值為 0 日意指備份組永遠不會過期。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-155">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="ab7e8-156">預設值會在 **[伺服器屬性]** 對話方塊 ( **[資料庫設定]** 頁面) 的 **[預設備份媒體保留 (以天為單位)]** 選項中設定。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-156">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (**Database Settings** page).</span></span> <span data-ttu-id="ab7e8-157">若要存取此選項，請以滑鼠右鍵按一下物件總管中的伺服器名稱，然後選取 [資料庫設定]  頁面。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-157">To access this option, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="ab7e8-158">若要讓備份組在特定日期過期，請按一下 **[於]** ，然後輸入備份組將過期的日期。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-158">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
11. <span data-ttu-id="ab7e8-159">按一下 **[磁碟]** 或 **[磁帶]** ，以選擇備份目的地的類型。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-159">Choose the type of backup destination by clicking **Disk** or **Tape**.</span></span> <span data-ttu-id="ab7e8-160">若要選取包含單一媒體集的磁碟或磁帶機 (最多 64 個) 的路徑，請按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-160">To select the paths of up to 64 disk or tape drives that contain a single media set, click **Add**.</span></span> <span data-ttu-id="ab7e8-161">選取的路徑會在 **[備份至]** 清單中顯示。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-161">The selected paths are displayed in the **Backup to** list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ab7e8-162">若要移除備份目的地，請選取目的地，然後按一下 **[移除]** 。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-162">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="ab7e8-163">若要檢視備份目的地的內容，請選取目的地，然後按一下 **[內容]** 。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-163">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
12. <span data-ttu-id="ab7e8-164">若要檢視或選取進階選項，請按一下 **[選取頁面]** 窗格中的 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-164">To view or select the advanced options, click **Options** in the **Select a page** pane.</span></span>  
  
13. <span data-ttu-id="ab7e8-165">按下列項目之一，以選取 **[覆寫媒體]** 選項：</span><span class="sxs-lookup"><span data-stu-id="ab7e8-165">Select an **Overwrite Media** option, by clicking one of the following:</span></span>  
  
    -   <span data-ttu-id="ab7e8-166">**備份至現有的媒體集**</span><span class="sxs-lookup"><span data-stu-id="ab7e8-166">**Back up to the existing media set**</span></span>  
  
         <span data-ttu-id="ab7e8-167">針對這個選項，按一下 **[附加至現有的備份組]** 或 **[覆寫所有現有的備份組]** 。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-167">For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.</span></span> <span data-ttu-id="ab7e8-168">如需備份至現有媒體集的相關資訊，請參閱[媒體集、媒體家族與備份組 &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-168">For information about backing up to an existing media set, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
         <span data-ttu-id="ab7e8-169">另外，也可以選取 **[檢查媒體集名稱及備份組是否逾期]** ，以讓備份作業確認媒體集及備份組逾期的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-169">Optionally, select **Check media set name and backup set expiration** to cause the backup operation to verify the date and time at which the media set and backup set expire.</span></span>  
  
         <span data-ttu-id="ab7e8-170">另外，也可以在 **[媒體集名稱]** 文字方塊中輸入名稱。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-170">Optionally, enter a name in the **Media set name** text box.</span></span> <span data-ttu-id="ab7e8-171">如果未指定名稱，就會建立一個空白名稱的媒體集。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-171">If no name is specified, a media set with a blank name is created.</span></span> <span data-ttu-id="ab7e8-172">如果您指定媒體集名稱，就會檢查媒體 (磁帶或磁碟)，以查看實際名稱是否與您在此處輸入的名稱相符。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-172">If you specify a media set name, the media (tape or disk) is checked to see whether the actual name matches the name that you enter here.</span></span>  
  
         <span data-ttu-id="ab7e8-173">如果您讓媒體名稱保持空白，並核取方塊以針對媒體進行檢查，成功也會使媒體上的媒體名稱保持空白。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-173">If you leave the media name blank and check the box to check it against the media, success will equal the media name on the media also being blank.</span></span>  
  
    -   <span data-ttu-id="ab7e8-174">**備份至新的媒體集，並清除所有現有的備份組**</span><span class="sxs-lookup"><span data-stu-id="ab7e8-174">**Back up to a new media set, and erase all existing backup sets**</span></span>  
  
         <span data-ttu-id="ab7e8-175">針對這個選項，在 **[新媒體集名稱]** 文字方塊中輸入名稱，然後選擇性在 **[新媒體集描述]** 文字方塊中描述媒體集。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-175">For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.</span></span> <span data-ttu-id="ab7e8-176">如需建立新媒體集的詳細資訊，請參閱[媒體集、媒體家族與備份組 &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-176">For more information about creating a new media set, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
14. <span data-ttu-id="ab7e8-177">在 [**可靠性**] 區段中，選擇性地檢查：</span><span class="sxs-lookup"><span data-stu-id="ab7e8-177">In the **Reliability** section, optionally check:</span></span>  
  
    -   <span data-ttu-id="ab7e8-178">**[完成後驗證備份]** 。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-178">**Verify backup when finished**.</span></span>  
  
    -   <span data-ttu-id="ab7e8-179">**[寫入媒體之前執行總和檢查碼]** 及/或 **[發生總和檢查碼錯誤時繼續]** 。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-179">**Perform checksum before writing to media**, and, optionally, **Continue on checksum error**.</span></span> <span data-ttu-id="ab7e8-180">如需總和檢查碼的詳細資訊，請參閱[在備份和還原期間可能的媒體錯誤 &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-180">For more information about checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
15. <span data-ttu-id="ab7e8-181">如果是備份至磁帶機 (在 [一般]  頁面的 [目的地]  區段中指定)，[備份後卸載磁帶]  選項會啟用供選擇。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-181">If you are backing up to a tape drive (as specified in the **Destination** section of the **General** page), the **Unload the tape after backup** option is active.</span></span> <span data-ttu-id="ab7e8-182">按一下這個選項會啟用 **[卸載之前倒轉磁帶]** 選項。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-182">Clicking this option enables the **Rewind the tape before unloading** option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ab7e8-183">除非您備份的是交易記錄檔 (依 [一般]  頁面的 [備份類型]  區段中的指定)，否則 [交易記錄檔]  區段中的選項為非使用中。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-183">The options in the **Transaction log** section are inactive unless you are backing up a transaction log (as specified in the **Backup type** section of the **General** page).</span></span>  
  
16. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="ab7e8-184">及更新版本支援 [備份壓縮](backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-184">and later versions support [backup compression](backup-compression-sql-server.md).</span></span> <span data-ttu-id="ab7e8-185">依預設，備份壓縮與否取決於 **備份壓縮預設** 伺服器組態選項的值。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-185">By default, whether a backup is compressed depends on the value of the **backup-compression default** server configuration option.</span></span> <span data-ttu-id="ab7e8-186">不過，不論目前的伺服器層級預設值為何，您都可以透過核取 [壓縮備份]  壓縮備份，而且可以透過核取 [不要壓縮備份]  防止壓縮。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-186">However, regardless of the current server-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.</span></span>  
  
     <span data-ttu-id="ab7e8-187">**檢視目前的 backup compression default**</span><span class="sxs-lookup"><span data-stu-id="ab7e8-187">**To view the current backup compression default**</span></span>  
  
    -   [<span data-ttu-id="ab7e8-188">檢視或設定 backup compression default 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="ab7e8-188">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ab7e8-189">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ab7e8-189">Using Transact-SQL</span></span>  
  
#### <a name="to-back-up-files-and-filegroups"></a><span data-ttu-id="ab7e8-190">備份檔案與檔案群組</span><span class="sxs-lookup"><span data-stu-id="ab7e8-190">To back up files and filegroups</span></span>  
  
1.  <span data-ttu-id="ab7e8-191">若要建立檔案或檔案群組備份，請使用 [BACKUP DATABASE <file_or_filegroup>](/sql/t-sql/statements/backup-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-191">To create a file or filegroup backup, use a [BACKUP DATABASE <file_or_filegroup>](/sql/t-sql/statements/backup-transact-sql) statement.</span></span> <span data-ttu-id="ab7e8-192">這個陳述式至少必須指定下列各項：</span><span class="sxs-lookup"><span data-stu-id="ab7e8-192">Minimally, this statement must specify the following:</span></span>  
  
    -   <span data-ttu-id="ab7e8-193">資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-193">The database name.</span></span>  
  
    -   <span data-ttu-id="ab7e8-194">分別為每個檔案或檔案群組指定 FILE 或 FILEGROUP 子句。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-194">A FILE or FILEGROUP clause for each file or filegroup, respectively.</span></span>  
  
    -   <span data-ttu-id="ab7e8-195">完整備份所要寫入的備份裝置。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-195">The backup device on which the full backup will be written.</span></span>  
  
     <span data-ttu-id="ab7e8-196">檔案備份的基本 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語法為：</span><span class="sxs-lookup"><span data-stu-id="ab7e8-196">The basic [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax for a file backup is:</span></span>  
  
     <span data-ttu-id="ab7e8-197">BACKUP DATABASE *database*</span><span class="sxs-lookup"><span data-stu-id="ab7e8-197">BACKUP DATABASE *database*</span></span>  
  
     <span data-ttu-id="ab7e8-198">{ FILE **=** _logical_file_name_ | FILEGROUP **=** _logical_filegroup_name_ } [ **,** ...*f* ]</span><span class="sxs-lookup"><span data-stu-id="ab7e8-198">{ FILE **=**_logical_file_name_ | FILEGROUP **=**_logical_filegroup_name_ } [ **,**...*f* ]</span></span>  
  
     <span data-ttu-id="ab7e8-199">TO *backup_device* [ **,** ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="ab7e8-199">TO *backup_device* [ **,**...*n* ]</span></span>  
  
     <span data-ttu-id="ab7e8-200">[ WITH *with_options* [ **,** ...*o* ] ] ;</span><span class="sxs-lookup"><span data-stu-id="ab7e8-200">[ WITH *with_options* [ **,**...*o* ] ] ;</span></span>  
  
    |<span data-ttu-id="ab7e8-201">選項</span><span class="sxs-lookup"><span data-stu-id="ab7e8-201">Option</span></span>|<span data-ttu-id="ab7e8-202">描述</span><span class="sxs-lookup"><span data-stu-id="ab7e8-202">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="ab7e8-203">*database*</span><span class="sxs-lookup"><span data-stu-id="ab7e8-203">*database*</span></span>|<span data-ttu-id="ab7e8-204">這是要備份交易記錄、部分資料庫或完整資料庫的來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-204">Is the database from which the transaction log, partial database, or complete database is backed up.</span></span>|  
    |<span data-ttu-id="ab7e8-205">FILE **=** _logical_file_name_</span><span class="sxs-lookup"><span data-stu-id="ab7e8-205">FILE **=**_logical_file_name_</span></span>|<span data-ttu-id="ab7e8-206">指定要包含在檔案備份中檔案的邏輯名稱。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-206">Specifies the logical name of a file to include in the file backup.</span></span>|  
    |<span data-ttu-id="ab7e8-207">FILEGROUP **=** _logical_filegroup_name_</span><span class="sxs-lookup"><span data-stu-id="ab7e8-207">FILEGROUP **=**_logical_filegroup_name_</span></span>|<span data-ttu-id="ab7e8-208">指定要包含在檔案備份中的檔案群組的邏輯名稱。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-208">Specifies the logical name of a filegroup to include in the file backup.</span></span> <span data-ttu-id="ab7e8-209">在簡單復原模式之下，只允許唯讀檔案群組使用檔案群組備份。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-209">Under the simple recovery model, a filegroup backup is allowed only for a read-only filegroup.</span></span>|  
    |<span data-ttu-id="ab7e8-210">[ **,** ...*f* ]</span><span class="sxs-lookup"><span data-stu-id="ab7e8-210">[ **,**...*f* ]</span></span>|<span data-ttu-id="ab7e8-211">這是一個預留位置，表示可以指定多個檔案和檔案群組。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-211">Is a placeholder that indicates that multiple files and filegroups may be specified.</span></span> <span data-ttu-id="ab7e8-212">檔案或檔案群組的數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-212">The number of files or filegroups is unlimited.</span></span>|  
    |<span data-ttu-id="ab7e8-213">*backup_device* [ **,** ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="ab7e8-213">*backup_device* [ **,**...*n* ]</span></span>|<span data-ttu-id="ab7e8-214">指定一份清單，列出備份作業可使用的 1 到 64 個備份裝置。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-214">Specifies a list of from 1 to 64 backup devices to use for the backup operation.</span></span> <span data-ttu-id="ab7e8-215">您可以指定實體備份裝置，或者指定對應的邏輯備份裝置 (若已經定義)。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-215">You can specify a physical backup device, or you can specify a corresponding logical backup device, if already defined.</span></span> <span data-ttu-id="ab7e8-216">若要指定實體備份裝置，請使用 DISK 或 TAPE 選項：</span><span class="sxs-lookup"><span data-stu-id="ab7e8-216">To specify a physical backup device, use the DISK or TAPE option:</span></span><br /><br /> <span data-ttu-id="ab7e8-217">{ DISK &#124; TAPE } **=** _physical_backup_device_name_</span><span class="sxs-lookup"><span data-stu-id="ab7e8-217">{ DISK &#124; TAPE } **=**_physical_backup_device_name_</span></span><br /><br /> <span data-ttu-id="ab7e8-218">如需詳細資訊，請參閱 [備份裝置 &#40;SQL Server&#41;](backup-devices-sql-server.md)執行個體上建立資料庫備份，就需要這個選項。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-218">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>|  
    |<span data-ttu-id="ab7e8-219">WITH *with_options* [ **,** ...*o* ]</span><span class="sxs-lookup"><span data-stu-id="ab7e8-219">WITH *with_options* [ **,**...*o* ]</span></span>|<span data-ttu-id="ab7e8-220">另外，也可以指定一個或多個其他選項，如 DIFFERENTIAL。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-220">Optionally, specifies one or more additional options, such as DIFFERENTIAL.</span></span><br /><br /> <span data-ttu-id="ab7e8-221">注意：差異檔案備份需要以完整檔案備份作為基底。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-221">Note: A differential file backup requires a full file backup as a base.</span></span> <span data-ttu-id="ab7e8-222">如需詳細資訊，請參閱[建立差異資料庫備份 &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-222">For more information, see [Create a Differential Database Backup &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md).</span></span>|  
  
2.  <span data-ttu-id="ab7e8-223">在完整復原模式下，您還必須備份交易記錄。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-223">Under the full recovery model, you must also back up the transaction log.</span></span> <span data-ttu-id="ab7e8-224">若要使用一組完整的完整檔案備份來還原資料庫，您還必須有足夠的記錄備份，才能從第一個檔案備份開始涵蓋所有的檔案備份。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-224">To use a complete set of full file backups to restore a database, you must also have enough log backups to span all the file backups, from the start of the first file backup.</span></span> <span data-ttu-id="ab7e8-225">如需詳細資訊，請參閱 [備份交易記錄 &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)資料庫還原至新位置，並選擇性地重新命名資料庫。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-225">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="ab7e8-226">範例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ab7e8-226">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="ab7e8-227">下列範例會備份 `Sales` 資料庫次要檔案群組的一或多個檔案。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-227">The following examples back up one or more files of the secondary filegroups of the `Sales` database.</span></span> <span data-ttu-id="ab7e8-228">這個資料庫使用完整復原模式，而且包含下列次要檔案群組：</span><span class="sxs-lookup"><span data-stu-id="ab7e8-228">This database uses the full recovery model and contains the following secondary filegroups:</span></span>  
  
-   <span data-ttu-id="ab7e8-229">名為 `SalesGroup1` 的檔案群組，其中含有檔案 `SGrp1Fi1` 和 `SGrp1Fi2`。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-229">A filegroup named `SalesGroup1` that has the files `SGrp1Fi1` and `SGrp1Fi2`.</span></span>  
  
-   <span data-ttu-id="ab7e8-230">名為 `SalesGroup2` 的檔案群組，其中含有檔案 `SGrp2Fi1` 和 `SGrp2Fi2`。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-230">A filegroup named `SalesGroup2` that has the files `SGrp2Fi1` and `SGrp2Fi2`.</span></span>  
  
#### <a name="a-creating-a-file-backup-of-two-files"></a><span data-ttu-id="ab7e8-231">A.</span><span class="sxs-lookup"><span data-stu-id="ab7e8-231">A.</span></span> <span data-ttu-id="ab7e8-232">建立兩個檔案的檔案備份</span><span class="sxs-lookup"><span data-stu-id="ab7e8-232">Creating a file backup of two files</span></span>  
 <span data-ttu-id="ab7e8-233">下列範例會建立只有 `SGrp1Fi2` 檔案群組之 `SalesGroup1` 檔案及 `SGrp2Fi2` 檔案群組之 `SalesGroup2` 檔案的差異檔案備份。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-233">The following example creates a differential file backup of only the `SGrp1Fi2` file of the `SalesGroup1` and the `SGrp2Fi2` file of the `SalesGroup2` filegroup.</span></span>  
  
```sql  
--Backup the files in the SalesGroup1 secondary filegroup.  
BACKUP DATABASE Sales  
   FILE = 'SGrp1Fi2',   
   FILE = 'SGrp2Fi2'   
   TO DISK = 'G:\SQL Server Backups\Sales\SalesGroup1.bck';  
GO  
```  
  
#### <a name="b-creating-a-full-file-backup-of-the-secondary-filegroups"></a><span data-ttu-id="ab7e8-234">B.</span><span class="sxs-lookup"><span data-stu-id="ab7e8-234">B.</span></span> <span data-ttu-id="ab7e8-235">建立次要檔案群組的完整檔案備份</span><span class="sxs-lookup"><span data-stu-id="ab7e8-235">Creating a full file backup of the secondary filegroups</span></span>  
 <span data-ttu-id="ab7e8-236">下列範例會為兩個次要檔案群組中的每個檔案建立完整檔案備份。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-236">The following example creates a full file backup of every file in both of the secondary filegroups.</span></span>  
  
```sql  
--Back up the files in SalesGroup1.  
BACKUP DATABASE Sales  
   FILEGROUP = 'SalesGroup1',  
   FILEGROUP = 'SalesGroup2'  
   TO DISK = 'C:\MySQLServer\Backups\Sales\SalesFiles.bck';  
GO  
```  
  
#### <a name="c-creating-a-differential-file-backup-of-the-secondary-filegroups"></a><span data-ttu-id="ab7e8-237">C.</span><span class="sxs-lookup"><span data-stu-id="ab7e8-237">C.</span></span> <span data-ttu-id="ab7e8-238">建立次要檔案群組的差異檔案備份</span><span class="sxs-lookup"><span data-stu-id="ab7e8-238">Creating a differential file backup of the secondary filegroups</span></span>  
 <span data-ttu-id="ab7e8-239">下列範例會為兩個次要檔案群組中的每個檔案建立差異檔案備份。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-239">The following example creates a differential file backup of every file in both of the secondary filegroups.</span></span>  
  
```sql  
--Back up the files in SalesGroup1.  
BACKUP DATABASE Sales  
   FILEGROUP = 'SalesGroup1',  
   FILEGROUP = 'SalesGroup2'  
   TO DISK = 'C:\MySQLServer\Backups\Sales\SalesFiles.bck'  
   WITH   
      DIFFERENTIAL;  
GO  
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="ab7e8-240">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab7e8-240">Using PowerShell</span></span>  
  
<span data-ttu-id="ab7e8-241">使用 `Backup-SqlDatabase` 指令程式，並且為 `Files` 參數指定 `-BackupAction` 值。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-241">Use the `Backup-SqlDatabase` cmdlet and specify `Files` for the value of the `-BackupAction` parameter.</span></span> <span data-ttu-id="ab7e8-242">另外再指定下列其中一個參數：</span><span class="sxs-lookup"><span data-stu-id="ab7e8-242">Also, specify one of the following parameters:</span></span>  
  
    -   <span data-ttu-id="ab7e8-243">若要備份特定檔案，請指定 `-DatabaseFile` *字串*參數，其中*string*是要備份的一個或多個資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-243">To back up a specific file, specify the `-DatabaseFile`*String* parameter, where *String* is one or more database files to be backed up.</span></span>  
  
    -   <span data-ttu-id="ab7e8-244">若要備份指定檔案群組中的所有檔案，請指定 `-DatabaseFileGroup` *string*參數，其中*string*是要備份的一個或多個資料庫檔案群組。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-244">To back up all the files in a given filegroup, specify the `-DatabaseFileGroup`*String* parameter, where *String* is one or more database filegroups to be backed up.</span></span>  
  
     <span data-ttu-id="ab7e8-245">以下範例會為 `MyDB` 資料庫內的次要檔案群組 'FileGroup1' 和 'FileGroup2' 建立其中每個檔案的完整檔案備份。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-245">The following example creates a full file backup of every file in the secondary filegroups 'FileGroup1' and 'FileGroup2' in the `MyDB` database.</span></span> <span data-ttu-id="ab7e8-246">備份是建立在伺服器執行個體 `Computer\Instance`的預設備份位置。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-246">The backups are created on the default backup location of the server instance `Computer\Instance`.</span></span>  
  
    ```powershell
    Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Files -DatabaseFileGroup "FileGroup1","FileGroup2"  
    ```  
  
<span data-ttu-id="ab7e8-247">若要設定及使用 SQL Server PowerShell 提供者，請參閱[SQL Server PowerShell 提供者](../../powershell/sql-server-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-247">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../powershell/sql-server-powershell-provider.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ab7e8-248">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab7e8-248">See Also</span></span>  
 <span data-ttu-id="ab7e8-249">[備份概觀 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ab7e8-249">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="ab7e8-250">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab7e8-250">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="ab7e8-251">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab7e8-251">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="ab7e8-252">[備份記錄與標頭資訊 &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ab7e8-252">[Backup History and Header Information &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md) </span></span>  
 <span data-ttu-id="ab7e8-253">[備份資料庫 &#40;一般頁面&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="ab7e8-253">[Back Up Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="ab7e8-254">[備份資料庫 &#40;備份選項頁面&#41;](back-up-database-backup-options-page.md) </span><span class="sxs-lookup"><span data-stu-id="ab7e8-254">[Back Up Database &#40;Backup Options Page&#41;](back-up-database-backup-options-page.md) </span></span>  
 <span data-ttu-id="ab7e8-255">[完整檔案備份 &#40;SQL Server&#41;](full-file-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ab7e8-255">[Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md) </span></span>  
 <span data-ttu-id="ab7e8-256">[差異備份 &#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ab7e8-256">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="ab7e8-257">[檔案還原 &#40;完整復原模式&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="ab7e8-257">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 [<span data-ttu-id="ab7e8-258">檔案還原 &#40;簡單復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="ab7e8-258">File Restores &#40;Simple Recovery Model&#41;</span></span>](file-restores-simple-recovery-model.md)  
  
  
