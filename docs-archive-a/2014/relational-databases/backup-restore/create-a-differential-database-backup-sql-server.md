---
title: 建立差異資料庫備份 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full differential backups [SQL Server]
- database backups [SQL Server], full differential backups
- backing up databases [SQL Server], full differential backups
- backups [SQL Server], creating
ms.assetid: 70f49794-b217-4519-9f2a-76ed61fa9f99
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2c3fb53d90ce633498bc518282d1ff03ce0b926e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606913"
---
# <a name="create-a-differential-database-backup-sql-server"></a><span data-ttu-id="186e7-102">建立差異資料庫備份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="186e7-102">Create a Differential Database Backup (SQL Server)</span></span>
  <span data-ttu-id="186e7-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中建立差異資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="186e7-103">This topic describes how to create a differential database backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="186e7-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="186e7-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="186e7-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="186e7-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="186e7-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="186e7-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="186e7-107">先決條件</span><span class="sxs-lookup"><span data-stu-id="186e7-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="186e7-108">建議</span><span class="sxs-lookup"><span data-stu-id="186e7-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="186e7-109">安全性</span><span class="sxs-lookup"><span data-stu-id="186e7-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="186e7-110">**若要使用下列項目建立差異資料庫備份：**</span><span class="sxs-lookup"><span data-stu-id="186e7-110">**To create a differential database backup, using:**</span></span>  
  
     [<span data-ttu-id="186e7-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="186e7-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="186e7-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="186e7-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="186e7-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="186e7-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="186e7-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="186e7-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="186e7-115">在明確或隱含的交易中，並不允許使用 BACKUP 陳述式。</span><span class="sxs-lookup"><span data-stu-id="186e7-115">The BACKUP statement is not allowed in an explicit or implicit transaction.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="186e7-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="186e7-116">Prerequisites</span></span>  
  
-   <span data-ttu-id="186e7-117">建立差異資料庫備份時，需要有先前的完整資料庫備份存在。</span><span class="sxs-lookup"><span data-stu-id="186e7-117">Creating a differential database backup requires that a previous full database backup exist.</span></span> <span data-ttu-id="186e7-118">如果從未備份過所選取的資料庫，在建立任何差異備份之前，請先執行完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="186e7-118">If the selected database has never been backed up, run a full database backup before creating any differential backups.</span></span> <span data-ttu-id="186e7-119">如需詳細資訊，請參閱 [建立完整資料庫備份 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)中建立差異資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="186e7-119">For more information, see [Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="186e7-120">建議</span><span class="sxs-lookup"><span data-stu-id="186e7-120">Recommendations</span></span>  
  
-   <span data-ttu-id="186e7-121">隨著差異備份大小增加，還原差異備份會大幅增加還原資料庫所需的時間。</span><span class="sxs-lookup"><span data-stu-id="186e7-121">As the differential backups increase in size, restoring a differential backup can significantly increase the time that is required to restore a database.</span></span> <span data-ttu-id="186e7-122">因此，建議您定期進行新的完整備份，為資料建立新的差異基底。</span><span class="sxs-lookup"><span data-stu-id="186e7-122">Therefore, we recommend that you take a new full backup at set intervals to establish a new differential base for the data.</span></span> <span data-ttu-id="186e7-123">例如，您可能每週進行整個資料庫的完整備份 (亦即，完整資料庫備份)，然後在該週定期進行一連串的差異資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="186e7-123">For example, you might take a weekly full backup of the whole database (that is, a full database backup) followed by a regular series of differential database backups during the week.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="186e7-124">Security</span><span class="sxs-lookup"><span data-stu-id="186e7-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="186e7-125">權限</span><span class="sxs-lookup"><span data-stu-id="186e7-125">Permissions</span></span>  
 <span data-ttu-id="186e7-126">BACKUP DATABASE 和 BACKUP LOG 權限預設為 **sysadmin** 固定伺服器角色以及 **db_owner** 和 **db_backupoperator** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="186e7-126">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="186e7-127">備份裝置實體檔案的擁有權和權限問題可能會干擾備份作業。</span><span class="sxs-lookup"><span data-stu-id="186e7-127">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="186e7-128">必須能夠讀取和寫入裝置；執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的帳戶必須具備寫入權限。</span><span class="sxs-lookup"><span data-stu-id="186e7-128">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="186e7-129">不過，在系統資料表中加入備份裝置項目的 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)並不會檢查檔案存取權限。</span><span class="sxs-lookup"><span data-stu-id="186e7-129">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="186e7-130">當您嘗試備份或還原時，存取實體資源之前不一定會出現備份裝置實體檔案的這些問題。</span><span class="sxs-lookup"><span data-stu-id="186e7-130">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="186e7-131">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="186e7-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-differential-database-backup"></a><span data-ttu-id="186e7-132">建立差異資料庫備份</span><span class="sxs-lookup"><span data-stu-id="186e7-132">To create a differential database backup</span></span>  
  
1.  <span data-ttu-id="186e7-133">連線至適當的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體之後，在 [物件總管] 中按一下伺服器名稱，以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="186e7-133">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="186e7-134">展開 **[資料庫]** ，根據資料庫選取使用者資料庫或展開 **[系統資料庫]** ，然後選取一個系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="186e7-134">Expand **Databases**, and depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="186e7-135">以滑鼠右鍵按一下資料庫，指向 **[工作]** ，然後按一下 **[備份]** 。</span><span class="sxs-lookup"><span data-stu-id="186e7-135">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="186e7-136">會出現 **[備份資料庫]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="186e7-136">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="186e7-137">在 **[資料庫]** 清單方塊中確認資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="186e7-137">In the **Database** list box, verify the database name.</span></span> <span data-ttu-id="186e7-138">您可以選擇性從清單中選取不同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="186e7-138">You can optionally select a different database from the list.</span></span>  
  
     <span data-ttu-id="186e7-139">您可以為任何復原模式 (完整、大量記錄或簡單) 執行差異備份。</span><span class="sxs-lookup"><span data-stu-id="186e7-139">You can perform a differential backup for any recovery model (full, bulk-logged, or simple).</span></span>  
  
5.  <span data-ttu-id="186e7-140">在 **[備份類型]** 清單方塊中，選取 **[差異]** 。</span><span class="sxs-lookup"><span data-stu-id="186e7-140">In the **Backup type** list box, select **Differential**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="186e7-141"> 選取 **[差異]** 時，請確認已清除 **[僅複製備份]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="186e7-141">When **Differential** is selected, verify that the **Copy Only Backup** check box is cleared.</span></span>  
  
6.  <span data-ttu-id="186e7-142">針對 **[備份元件]** ，按一下 **[資料庫]** 。</span><span class="sxs-lookup"><span data-stu-id="186e7-142">For **Backup component**, click **Database**.</span></span>  
  
7.  <span data-ttu-id="186e7-143">接受 **[名稱]** 文字方塊中建議的預設備份組名稱，或者輸入不同的備份組名稱。</span><span class="sxs-lookup"><span data-stu-id="186e7-143">Either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.</span></span>  
  
8.  <span data-ttu-id="186e7-144">(選擇性) 在 **[描述]** 文字方塊中輸入備份組的描述。</span><span class="sxs-lookup"><span data-stu-id="186e7-144">Optionally, in the **Description** text box, enter a description of the backup set.</span></span>  
  
9. <span data-ttu-id="186e7-145">指定備份組會在何時過期：</span><span class="sxs-lookup"><span data-stu-id="186e7-145">Specify when the backup set will expire:</span></span>  
  
    -   <span data-ttu-id="186e7-146">若要讓備份組在特定的天數後過期，請按一下 [之後]  \(預設選項)，然後輸入備份組建立之後將會過期的天數。</span><span class="sxs-lookup"><span data-stu-id="186e7-146">To have the backup set expire after a specific number of days, click **After** (the default option), and enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="186e7-147">這個值可以介於 0 到 99999 日之間；值為 0 日意指備份組永遠不會過期。</span><span class="sxs-lookup"><span data-stu-id="186e7-147">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="186e7-148">預設值會在 **[伺服器屬性]** 對話方塊 ( **[資料庫設定]** 頁面) 的 **[預設備份媒體保留 (以天為單位)]** 選項中設定。</span><span class="sxs-lookup"><span data-stu-id="186e7-148">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (**Database Settings** page).</span></span> <span data-ttu-id="186e7-149">若要存取，請以滑鼠右鍵按一下物件總管中的伺服器名稱並選取 [屬性]，然後選取 [資料庫設定]  頁面。</span><span class="sxs-lookup"><span data-stu-id="186e7-149">To access this, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="186e7-150">若要讓備份組在特定日期過期，請按一下 **[於]** ，然後輸入備份組將過期的日期。</span><span class="sxs-lookup"><span data-stu-id="186e7-150">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
10. <span data-ttu-id="186e7-151">按一下 **[磁碟]** 或 **[磁帶]** ，以選擇備份目的地的類型。</span><span class="sxs-lookup"><span data-stu-id="186e7-151">Choose the type of backup destination by clicking **Disk** or **Tape**.</span></span> <span data-ttu-id="186e7-152">若要選取包含單一媒體集的磁碟或磁帶機 (最多 64 個) 的路徑，請按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="186e7-152">To select the path of up to 64 disk or tape drives containing a single media set, click **Add**.</span></span> <span data-ttu-id="186e7-153">選取的路徑會在 **[備份至]** 清單方塊中顯示。</span><span class="sxs-lookup"><span data-stu-id="186e7-153">The selected paths are displayed in the **Backup to** list box.</span></span>  
  
     <span data-ttu-id="186e7-154">若要移除備份目的地，請選取目的地，然後按一下 **[移除]** 。</span><span class="sxs-lookup"><span data-stu-id="186e7-154">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="186e7-155">若要檢視備份目的地的內容，請選取目的地，然後按一下 **[內容]** 。</span><span class="sxs-lookup"><span data-stu-id="186e7-155">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
11. <span data-ttu-id="186e7-156">若要檢視或選取進階選項，請按一下 **[選取頁面]** 窗格中的 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="186e7-156">To view or select the advanced options, click **Options** in the **Select a page** pane.</span></span>  
  
12. <span data-ttu-id="186e7-157">按下列項目之一，以選取 **[覆寫媒體]** 選項：</span><span class="sxs-lookup"><span data-stu-id="186e7-157">Select an **Overwrite Media** option, by clicking one of the following:</span></span>  
  
    -   <span data-ttu-id="186e7-158">**備份至現有的媒體集**</span><span class="sxs-lookup"><span data-stu-id="186e7-158">**Back up to the existing media set**</span></span>  
  
         <span data-ttu-id="186e7-159">針對這個選項，按一下 **[附加至現有的備份組]** 或 **[覆寫所有現有的備份組]** 。</span><span class="sxs-lookup"><span data-stu-id="186e7-159">For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.</span></span> <span data-ttu-id="186e7-160">(選擇性) 選取 **[檢查媒體集名稱及備份組是否逾期]** 核取方塊，然後在 **[媒體集名稱]** 文字方塊中輸入名稱。</span><span class="sxs-lookup"><span data-stu-id="186e7-160">Optionally, check the **Check media set name and backup set expiration** check box and, optionally, enter a name in the **Media set name** text box.</span></span> <span data-ttu-id="186e7-161">如果未指定名稱，就會建立一個空白名稱的媒體集。</span><span class="sxs-lookup"><span data-stu-id="186e7-161">If no name is specified, a media set with a blank name is created.</span></span> <span data-ttu-id="186e7-162">如果您指定媒體集名稱，就會檢查媒體 (磁帶或磁碟)，以查看實際名稱是否與您在此處輸入的名稱相符。</span><span class="sxs-lookup"><span data-stu-id="186e7-162">If you specify a media set name, the media (tape or disk) is checked to see if the actual name matches the name you enter here.</span></span>  
  
         <span data-ttu-id="186e7-163">如果您讓媒體名稱保持空白，並核取方塊以針對媒體進行檢查，成功也會使媒體上的媒體名稱保持空白。</span><span class="sxs-lookup"><span data-stu-id="186e7-163">If you leave the media name blank and check the box to check it against the media, success will equal the media name on the media also being blank.</span></span>  
  
    -   <span data-ttu-id="186e7-164">**備份至新的媒體集，並清除所有現有的備份組**</span><span class="sxs-lookup"><span data-stu-id="186e7-164">**Back up to a new media set, and erase all existing backup sets**</span></span>  
  
         <span data-ttu-id="186e7-165">針對這個選項，在 **[新媒體集名稱]** 文字方塊中輸入名稱，然後選擇性在 **[新媒體集描述]** 文字方塊中描述媒體集。</span><span class="sxs-lookup"><span data-stu-id="186e7-165">For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.</span></span>  
  
13. <span data-ttu-id="186e7-166">(選擇性) 在 **[可靠性]** 區段中選取：</span><span class="sxs-lookup"><span data-stu-id="186e7-166">In the **Reliability** section, optionally, check:</span></span>  
  
    -   <span data-ttu-id="186e7-167">**[完成後驗證備份]** 。</span><span class="sxs-lookup"><span data-stu-id="186e7-167">**Verify backup when finished**.</span></span>  
  
    -   <span data-ttu-id="186e7-168">**[寫入媒體之前執行總和檢查碼]** 及/或 **[發生總和檢查碼錯誤時繼續]** 。</span><span class="sxs-lookup"><span data-stu-id="186e7-168">**Perform checksum before writing to media**, and, optionally, **Continue on checksum error**.</span></span> <span data-ttu-id="186e7-169">如需總和檢查碼的詳細資訊，請參閱[在備份和還原期間可能的媒體錯誤 &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="186e7-169">For information about checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
14. <span data-ttu-id="186e7-170">如果是備份至磁帶機 (在 [一般]  頁面的 [目的地]  區段中指定)，[備份後卸載磁帶]  選項會啟用供選擇。</span><span class="sxs-lookup"><span data-stu-id="186e7-170">If you are backing up to a tape drive (as specified in the **Destination** section of the **General** page), the **Unload the tape after backup** option is active.</span></span> <span data-ttu-id="186e7-171">按一下這個選項會啟動 **[卸載之前倒轉磁帶]** 選項。</span><span class="sxs-lookup"><span data-stu-id="186e7-171">Clicking this option activates the **Rewind the tape before unloading** option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="186e7-172">除非您備份的是交易記錄檔 (依 [一般]  頁面的 [備份類型]  區段中的指定)，否則 [交易記錄檔]  區段中的選項為非使用中。</span><span class="sxs-lookup"><span data-stu-id="186e7-172">The options in the **Transaction log** section are inactive unless you are backing up a transaction log (as specified in the **Backup type** section of the **General** page).</span></span>  
  
15. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="186e7-173">和更新的版本支援 [備份壓縮](backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="186e7-173">and later supports [backup compression](backup-compression-sql-server.md).</span></span> <span data-ttu-id="186e7-174">依預設，備份壓縮與否取決於 **備份壓縮預設** 伺服器組態選項的值。</span><span class="sxs-lookup"><span data-stu-id="186e7-174">By default, whether a backup is compressed depends on the value of the **backup-compression default** server configuration option.</span></span> <span data-ttu-id="186e7-175">不過，不論目前的伺服器層級預設值為何，您都可以透過核取 [壓縮備份]  壓縮備份，而且可以透過核取 [不要壓縮備份]  防止壓縮。</span><span class="sxs-lookup"><span data-stu-id="186e7-175">However, regardless of the current server-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.</span></span>  
  
     <span data-ttu-id="186e7-176">**檢視目前的 backup compression default**</span><span class="sxs-lookup"><span data-stu-id="186e7-176">**To view the current backup compression default**</span></span>  
  
    -   [<span data-ttu-id="186e7-177">檢視或設定 backup compression default 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="186e7-177">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
    > [!NOTE]  
    >  <span data-ttu-id="186e7-178">或者，您可以使用「維護計畫精靈」來建立差異資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="186e7-178">Alternatively, you can use the Maintenance Plan Wizard to create differential database backups.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="186e7-179">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="186e7-179">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-differential-database-backup"></a><span data-ttu-id="186e7-180">建立差異資料庫備份</span><span class="sxs-lookup"><span data-stu-id="186e7-180">To create a differential database backup</span></span>  
  
1.  <span data-ttu-id="186e7-181">執行 BACKUP DATABASE 陳述式以建立差異資料庫備份，請指定：</span><span class="sxs-lookup"><span data-stu-id="186e7-181">Execute the BACKUP DATABASE statement to create the differential database backup, specifying:</span></span>  
  
    -   <span data-ttu-id="186e7-182">欲備份的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="186e7-182">The name of the database to back up.</span></span>  
  
    -   <span data-ttu-id="186e7-183">寫入完整資料庫備份的備份裝置。</span><span class="sxs-lookup"><span data-stu-id="186e7-183">The backup device where the full database backup is written.</span></span>  
  
    -   <span data-ttu-id="186e7-184">DIFFERENTIAL 子句，指定只備份資料庫自上次進行完整資料庫備份後的變更部分。</span><span class="sxs-lookup"><span data-stu-id="186e7-184">The DIFFERENTIAL clause, to specify that only the parts of the database that have changed after the last full database backup was created are backed up.</span></span>  
  
     <span data-ttu-id="186e7-185">必要的語法如下：</span><span class="sxs-lookup"><span data-stu-id="186e7-185">The required syntax is:</span></span>  
  
     <span data-ttu-id="186e7-186">BACKUP DATABASE <資料庫名稱>  TO <備份裝置> WITH DIFFERENTIAL</span><span class="sxs-lookup"><span data-stu-id="186e7-186">BACKUP DATABASE *database_name* TO <backup_device> WITH DIFFERENTIAL</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="186e7-187">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="186e7-187">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="186e7-188">這個範例會建立 `MyAdvWorks` 資料庫的完整和差異資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="186e7-188">This example creates a full and a differential database backup for the `MyAdvWorks` database.</span></span>  
  
```sql  
-- Create a full database backup first.  
BACKUP DATABASE MyAdvWorks   
   TO MyAdvWorks_1   
   WITH INIT;  
GO  
-- Time elapses.  
-- Create a differential database backup, appending the backup  
-- to the backup device containing the full database backup.  
BACKUP DATABASE MyAdvWorks  
   TO MyAdvWorks_1  
   WITH DIFFERENTIAL;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="186e7-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="186e7-189">See Also</span></span>  
 <span data-ttu-id="186e7-190">[差異備份 &#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="186e7-190">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="186e7-191">[建立完整資料庫備份 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="186e7-191">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span></span>  
 <span data-ttu-id="186e7-192">[備份檔案和檔案群組 &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="186e7-192">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="186e7-193">[還原差異資料庫備份 &#40;SQL Server&#41;](restore-a-differential-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="186e7-193">[Restore a Differential Database Backup &#40;SQL Server&#41;](restore-a-differential-database-backup-sql-server.md) </span></span>  
 <span data-ttu-id="186e7-194">[還原交易記錄備份 &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="186e7-194">[Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span></span>  
 <span data-ttu-id="186e7-195">[維護計畫](../maintenance-plans/maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="186e7-195">[Maintenance Plans](../maintenance-plans/maintenance-plans.md) </span></span>  
 [<span data-ttu-id="186e7-196">完整檔案備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="186e7-196">Full File Backups &#40;SQL Server&#41;</span></span>](full-file-backups-sql-server.md)  
  
  
