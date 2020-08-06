---
title: 備份交易記錄 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- transaction log backups [SQL Server], SQL Server Management Studio
- backups [SQL Server], creating
- backing up transaction logs [SQL Server], SQL Server Management Studio
ms.assetid: 3426b5eb-6327-4c7f-88aa-37030be69fbf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b57ca40b08718cda5095249991e0d424e6593a24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595145"
---
# <a name="back-up-a-transaction-log-sql-server"></a><span data-ttu-id="3052b-102">備份交易記錄 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3052b-102">Back Up a Transaction Log (SQL Server)</span></span>
  <span data-ttu-id="3052b-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 PowerShell，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中備份交易記錄。</span><span class="sxs-lookup"><span data-stu-id="3052b-103">This topic describes how to back up a transaction log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or PowerShell.</span></span>  
  
 <span data-ttu-id="3052b-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="3052b-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3052b-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="3052b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3052b-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="3052b-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="3052b-107">建議</span><span class="sxs-lookup"><span data-stu-id="3052b-107">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="3052b-108">安全性</span><span class="sxs-lookup"><span data-stu-id="3052b-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3052b-109">**若要使用下列項目備份交易記錄：**</span><span class="sxs-lookup"><span data-stu-id="3052b-109">**To back up a transaction log, using:**</span></span>  
  
     [<span data-ttu-id="3052b-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3052b-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3052b-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3052b-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="3052b-112">PowerShell</span><span class="sxs-lookup"><span data-stu-id="3052b-112">PowerShell</span></span>](#PowerShellProcedure)  
  
    > [!NOTE]  
    >  <span data-ttu-id="3052b-113"> 或者，您也可以使用[維護計畫精靈](../maintenance-plans/use-the-maintenance-plan-wizard.md)來建立備份。</span><span class="sxs-lookup"><span data-stu-id="3052b-113">Alternatively, you can use the[Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md)to create backups.</span></span>  
  
-   [<span data-ttu-id="3052b-114">相關工作</span><span class="sxs-lookup"><span data-stu-id="3052b-114">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3052b-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="3052b-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3052b-116">限制事項</span><span class="sxs-lookup"><span data-stu-id="3052b-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="3052b-117">在明確或隱含的交易中，並不允許使用 BACKUP 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3052b-117">The BACKUP statement is not allowed in an explicit or implicit transaction.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="3052b-118">建議</span><span class="sxs-lookup"><span data-stu-id="3052b-118">Recommendations</span></span>  
  
-   <span data-ttu-id="3052b-119">如果資料庫使用完整復原模式或大量記錄復原模式，您必須定期備份交易記錄，使其足以保護您的資料，並讓交易記錄不要被填滿。</span><span class="sxs-lookup"><span data-stu-id="3052b-119">If a database uses either the full or bulk-logged recovery model, you must back up the transaction log regularly enough to protect your data and to keep the transaction log from filling.</span></span> <span data-ttu-id="3052b-120">這會截斷記錄並支援將資料庫還原到特定時間點。</span><span class="sxs-lookup"><span data-stu-id="3052b-120">This truncates the log and supports restoring the database to a specific point in time.</span></span>  
  
-   <span data-ttu-id="3052b-121">根據預設，每項成功的備份作業都會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔與系統事件記錄檔中，加入一個項目。</span><span class="sxs-lookup"><span data-stu-id="3052b-121">By default, every successful backup operation adds an entry in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and in the system event log.</span></span> <span data-ttu-id="3052b-122">如果您經常備份記錄檔，這些成功訊息可能會快速累積，因而產生龐大的錯誤記錄檔，讓您難以尋找其他訊息。</span><span class="sxs-lookup"><span data-stu-id="3052b-122">If back up the log very frequently, these success messages accumulate quickly, resulting in huge error logs that can make finding other messages difficult.</span></span> <span data-ttu-id="3052b-123">在這類情況下，如果沒有任何指令碼相依於這些記錄項目，您就可以使用追蹤旗標 3226 來隱藏這些記錄項目。</span><span class="sxs-lookup"><span data-stu-id="3052b-123">In such cases you can suppress these log entries by using trace flag 3226 if none of your scripts depend on those entries.</span></span> <span data-ttu-id="3052b-124">如需詳細資訊，請參閱[追蹤旗標 &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3052b-124">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3052b-125">Security</span><span class="sxs-lookup"><span data-stu-id="3052b-125">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3052b-126">權限</span><span class="sxs-lookup"><span data-stu-id="3052b-126">Permissions</span></span>  
 <span data-ttu-id="3052b-127">BACKUP DATABASE 和 BACKUP LOG 權限預設為 **sysadmin** 固定伺服器角色以及 **db_owner** 和 **db_backupoperator** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="3052b-127">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="3052b-128">備份裝置實體檔案的擁有權和權限問題可能會干擾備份作業。</span><span class="sxs-lookup"><span data-stu-id="3052b-128">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3052b-129">必須能夠讀取和寫入裝置；執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的帳戶必須具備寫入權限。</span><span class="sxs-lookup"><span data-stu-id="3052b-129">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="3052b-130">不過，在系統資料表中加入備份裝置項目的 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)並不會檢查檔案存取權限。</span><span class="sxs-lookup"><span data-stu-id="3052b-130">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="3052b-131">當您嘗試備份或還原時，存取實體資源之前不一定會出現備份裝置實體檔案的這些問題。</span><span class="sxs-lookup"><span data-stu-id="3052b-131">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3052b-132">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3052b-132">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-back-up-a-transaction-log"></a><span data-ttu-id="3052b-133">備份交易記錄檔</span><span class="sxs-lookup"><span data-stu-id="3052b-133">To back up a transaction log</span></span>  
  
1.  <span data-ttu-id="3052b-134">連接到適當的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體之後，請在 [物件總管] 中按一下伺服器名稱以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="3052b-134">After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="3052b-135">展開 **[資料庫]** ，然後視資料庫而定，選取使用者資料庫，或者展開 **[系統資料庫]** 並選取一個系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="3052b-135">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="3052b-136">以滑鼠右鍵按一下資料庫，指向 **[工作]** ，然後按一下 **[備份]** 。</span><span class="sxs-lookup"><span data-stu-id="3052b-136">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="3052b-137">會出現 **[備份資料庫]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3052b-137">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="3052b-138">在 **[資料庫]** 清單方塊中確認資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="3052b-138">In the **Database** list box, verify the database name.</span></span> <span data-ttu-id="3052b-139">您可以選擇性從清單中選取不同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="3052b-139">You can optionally select a different database from the list.</span></span>  
  
5.  <span data-ttu-id="3052b-140">確認復原模式是否為 **[FULL]** 或 **[BULK_LOGGED]** 。</span><span class="sxs-lookup"><span data-stu-id="3052b-140">Verify that the recovery model is either **FULL** or **BULK_LOGGED**.</span></span>  
  
6.  <span data-ttu-id="3052b-141">在 **[備份類型]** 清單方塊中，選取 **[交易記錄]** 。</span><span class="sxs-lookup"><span data-stu-id="3052b-141">In the **Backup type** list box, select **Transaction Log**.</span></span>  
  
7.  <span data-ttu-id="3052b-142">或者，您也可以選取 **[僅複製備份]** 來建立僅複製備份。</span><span class="sxs-lookup"><span data-stu-id="3052b-142">Optionally, you can select **Copy Only Backup** to create a copy-only backup.</span></span> <span data-ttu-id="3052b-143">「只複製備份」  是與傳統 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份順序無關的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份。</span><span class="sxs-lookup"><span data-stu-id="3052b-143">A *copy-only backup* is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup that is independent of the sequence of conventional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span> <span data-ttu-id="3052b-144">如需詳細資訊，請參閱[只複製備份 &#40;SQL Server&#41;](copy-only-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3052b-144">For more information, see [Copy-Only Backups &#40;SQL Server&#41;](copy-only-backups-sql-server.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3052b-145">選取 **[差異]** 選項時，您無法建立「只複製」備份。</span><span class="sxs-lookup"><span data-stu-id="3052b-145">When the **Differential** option is selected, you cannot create a copy-only backup.</span></span>  
  
8.  <span data-ttu-id="3052b-146">接受 **[名稱]** 文字方塊中建議的預設備份組名稱，或者輸入不同的備份組名稱。</span><span class="sxs-lookup"><span data-stu-id="3052b-146">Either accept the default backup set name suggested in the **Name** text box, or enter a different name for the backup set.</span></span>  
  
9. <span data-ttu-id="3052b-147">(選擇性) 在 **[描述]** 文字方塊中輸入備份組的描述。</span><span class="sxs-lookup"><span data-stu-id="3052b-147">Optionally, in the **Description** text box, enter a description of the backup set.</span></span>  
  
10. <span data-ttu-id="3052b-148">指定備份組會在何時過期：</span><span class="sxs-lookup"><span data-stu-id="3052b-148">Specify when the backup set will expire:</span></span>  
  
    -   <span data-ttu-id="3052b-149">若要讓備份組在特定的天數後過期，請按一下 [之後]  \(預設選項)，然後輸入備份組建立之後將會過期的天數。</span><span class="sxs-lookup"><span data-stu-id="3052b-149">To have the backup set expire after a specific number of days, click **After** (the default option), and enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="3052b-150">這個值可以介於 0 到 99999 日之間；值為 0 日意指備份組永遠不會過期。</span><span class="sxs-lookup"><span data-stu-id="3052b-150">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="3052b-151">預設值會在 **[伺服器屬性]** 對話方塊 ( **[資料庫設定]** 頁面) 的 **[預設備份媒體保留 (以天為單位)]** 選項中設定。</span><span class="sxs-lookup"><span data-stu-id="3052b-151">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (**Database Settings** page).</span></span> <span data-ttu-id="3052b-152">若要存取此對話方塊，請以滑鼠右鍵按一下 [物件總管] 中的伺服器名稱並選取 [屬性]，然後選取 **[資料庫設定]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="3052b-152">To access this dialog box, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="3052b-153">若要讓備份組在特定日期過期，請按一下 **[於]** ，然後輸入備份組將過期的日期。</span><span class="sxs-lookup"><span data-stu-id="3052b-153">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
11. <span data-ttu-id="3052b-154">按一下 **[磁碟]** 、 **[URL]** 或 **[磁帶]** ，以選擇備份目的地的類型。</span><span class="sxs-lookup"><span data-stu-id="3052b-154">Choose the type of backup destination by clicking **Disk**, **URL** or **Tape**.</span></span> <span data-ttu-id="3052b-155">若要選取包含單一媒體集的磁碟或磁帶機 (最多 64 個) 的路徑，請按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="3052b-155">To select the paths of up to 64 disk or tape drives containing a single media set, click **Add**.</span></span> <span data-ttu-id="3052b-156">選取的路徑會在 **[備份至]** 清單方塊中顯示。</span><span class="sxs-lookup"><span data-stu-id="3052b-156">The selected paths are displayed in the **Backup to** list box.</span></span>  
  
     <span data-ttu-id="3052b-157">若要移除備份目的地，請選取目的地，然後按一下 **[移除]** 。</span><span class="sxs-lookup"><span data-stu-id="3052b-157">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="3052b-158">若要檢視備份目的地的內容，請選取目的地，然後按一下 **[內容]** 。</span><span class="sxs-lookup"><span data-stu-id="3052b-158">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
12. <span data-ttu-id="3052b-159">若要檢視或選取進階選項，請按一下 **[選取頁面]** 窗格中的 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="3052b-159">To view or select the advanced options, click **Options** in the **Select a page** pane.</span></span>  
  
13. <span data-ttu-id="3052b-160">按下列項目之一，以選取 **[覆寫媒體]** 選項：</span><span class="sxs-lookup"><span data-stu-id="3052b-160">Select an **Overwrite Media** option, by clicking one of the following:</span></span>  
  
    -   <span data-ttu-id="3052b-161">**備份至現有的媒體集**</span><span class="sxs-lookup"><span data-stu-id="3052b-161">**Back up to the existing media set**</span></span>  
  
         <span data-ttu-id="3052b-162">針對這個選項，按一下 **[附加至現有的備份組]** 或 **[覆寫所有現有的備份組]** 。</span><span class="sxs-lookup"><span data-stu-id="3052b-162">For this option, click either **Append to the existing backup set** or **Overwrite all existing backup sets**.</span></span> <span data-ttu-id="3052b-163">如需詳細資訊，請參閱 [媒體集、媒體家族與備份組 &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3052b-163">For more information, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
         <span data-ttu-id="3052b-164">另外，也可以選取 **[檢查媒體集名稱及備份組是否逾期]** ，以讓備份作業確認媒體集及備份組逾期的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="3052b-164">Optionally, select **Check media set name and backup set expiration** to cause the backup operation to verify the date and time at which the media set and backup set expire.</span></span>  
  
         <span data-ttu-id="3052b-165">另外，也可以在 **[媒體集名稱]** 文字方塊中輸入名稱。</span><span class="sxs-lookup"><span data-stu-id="3052b-165">Optionally, enter a name in the **Media set name** text box.</span></span> <span data-ttu-id="3052b-166">如果未指定名稱，就會建立一個空白名稱的媒體集。</span><span class="sxs-lookup"><span data-stu-id="3052b-166">If no name is specified, a media set with a blank name is created.</span></span> <span data-ttu-id="3052b-167">如果您指定媒體集名稱，就會檢查媒體 (磁帶或磁碟)，以查看實際名稱是否與您在此處輸入的名稱相符。</span><span class="sxs-lookup"><span data-stu-id="3052b-167">If you specify a media set name, the media (tape or disk) is checked to see whether the actual name matches the name you enter here.</span></span>  
  
         <span data-ttu-id="3052b-168">如果您讓媒體名稱保持空白，並核取方塊以針對媒體進行檢查，成功也會使媒體上的媒體名稱保持空白。</span><span class="sxs-lookup"><span data-stu-id="3052b-168">If you leave the media name blank and check the box to check it against the media, success will equal the media name on the media also being blank.</span></span>  
  
    -   <span data-ttu-id="3052b-169">**備份至新的媒體集，並清除所有現有的備份組**</span><span class="sxs-lookup"><span data-stu-id="3052b-169">**Back up to a new media set, and erase all existing backup sets**</span></span>  
  
         <span data-ttu-id="3052b-170">針對這個選項，在 **[新媒體集名稱]** 文字方塊中輸入名稱，然後選擇性在 **[新媒體集描述]** 文字方塊中描述媒體集。</span><span class="sxs-lookup"><span data-stu-id="3052b-170">For this option, enter a name in the **New media set name** text box, and, optionally, describe the media set in the **New media set description** text box.</span></span> <span data-ttu-id="3052b-171">如需詳細資訊，請參閱 [媒體集、媒體家族與備份組 &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3052b-171">For more information, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
14. <span data-ttu-id="3052b-172">(選擇性) 在 **[可靠性]** 區段中選取：</span><span class="sxs-lookup"><span data-stu-id="3052b-172">In the **Reliability** section, optionally, check:</span></span>  
  
    -   <span data-ttu-id="3052b-173">**[完成後驗證備份]** 。</span><span class="sxs-lookup"><span data-stu-id="3052b-173">**Verify backup when finished**.</span></span>  
  
    -   <span data-ttu-id="3052b-174">**[寫入媒體之前執行總和檢查碼]** 及/或 **[發生總和檢查碼錯誤時繼續]** 。</span><span class="sxs-lookup"><span data-stu-id="3052b-174">**Perform checksum before writing to media**, and, optionally, **Continue on checksum error**.</span></span> <span data-ttu-id="3052b-175">如需總和檢查碼的相關資訊，請參閱[在備份和還原期間可能的媒體錯誤 &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3052b-175">For information on checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
15. <span data-ttu-id="3052b-176">在 **[交易記錄]** 區段中：</span><span class="sxs-lookup"><span data-stu-id="3052b-176">In the **Transaction log** section:</span></span>  
  
    -   <span data-ttu-id="3052b-177">對於例行的記錄備份，請保留預設選項 **[移除非使用中的項目以截斷交易記錄]** 。</span><span class="sxs-lookup"><span data-stu-id="3052b-177">For routine log backups, keep the default selection, **Truncate the transaction log by removing inactive entries**.</span></span>  
  
    -   <span data-ttu-id="3052b-178">若要備份記錄的結尾 (亦即，使用中的記錄)，請勾選 **[備份記錄檔的結尾，並讓資料庫保持在還原狀態]**。</span><span class="sxs-lookup"><span data-stu-id="3052b-178">To back up the tail of the log (that is, the active log), check **Back up the tail of the log, and leave database in the restoring state**.</span></span>  
  
         <span data-ttu-id="3052b-179">結尾記錄備份是在發生失敗後進行的，會備份記錄的結尾，以防止遺失工作資料。</span><span class="sxs-lookup"><span data-stu-id="3052b-179">A tail-log backup is taken after a failure to back up the tail of the log in order to prevent work loss.</span></span> <span data-ttu-id="3052b-180">在以下兩種情況時應備份使用中的記錄 (結尾記錄備份)：發生失敗後開始還原資料庫之前，或是容錯移轉到次要資料庫時。</span><span class="sxs-lookup"><span data-stu-id="3052b-180">Back up the active log (a tail-log backup) both after a failure, before beginning to restore the database, or when failing over to a secondary database.</span></span> <span data-ttu-id="3052b-181">選取此選項相當於在 Transact-SQL 的 BACKUP LOG 陳述式中，指定 NORECOVERY 選項。</span><span class="sxs-lookup"><span data-stu-id="3052b-181">Selecting this option is equivalent to specifying the NORECOVERY option in the BACKUP LOG statement of Transact-SQL.</span></span> <span data-ttu-id="3052b-182">如需結尾記錄備份的詳細資訊，請參閱[結尾記錄備份 &#40;SQL Server&#41;](tail-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3052b-182">For more information about tail-log backups, see [Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md).</span></span>  
  
16. <span data-ttu-id="3052b-183">如果是備份至磁帶機 (在 [一般]  頁面的 [目的地]  區段中指定)，[備份後卸載磁帶]  選項會啟用供選擇。</span><span class="sxs-lookup"><span data-stu-id="3052b-183">If you are backing up to a tape drive (as specified in the **Destination** section of the **General** page), the **Unload the tape after backup** option is active.</span></span> <span data-ttu-id="3052b-184">按一下這個選項會啟動 **[卸載之前倒轉磁帶]** 選項。</span><span class="sxs-lookup"><span data-stu-id="3052b-184">Clicking this option activates the **Rewind the tape before unloading** option.</span></span>  
  
17. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="3052b-185">和更新的版本支援 [備份壓縮](backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3052b-185">and later supports [backup compression](backup-compression-sql-server.md).</span></span> <span data-ttu-id="3052b-186">依預設，備份壓縮與否取決於 **備份壓縮預設** 伺服器組態選項的值。</span><span class="sxs-lookup"><span data-stu-id="3052b-186">By default, whether a backup is compressed depends on the value of the **backup-compression default** server configuration option.</span></span> <span data-ttu-id="3052b-187">不過，不論目前的伺服器層級預設值為何，您都可以透過核取 [壓縮備份]  壓縮備份，而且可以透過核取 [不要壓縮備份]  防止壓縮。</span><span class="sxs-lookup"><span data-stu-id="3052b-187">However, regardless of the current server-level default, you can compress a backup by checking **Compress backup**, and you can prevent compression by checking **Do not compress backup**.</span></span>  
  
     <span data-ttu-id="3052b-188">**檢視目前的 backup compression default**</span><span class="sxs-lookup"><span data-stu-id="3052b-188">**To view the current backup compression default**</span></span>  
  
    -   [<span data-ttu-id="3052b-189">檢視或設定 backup compression default 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="3052b-189">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
 <span data-ttu-id="3052b-190">**加密**</span><span class="sxs-lookup"><span data-stu-id="3052b-190">**Encryption**</span></span>  
  
 <span data-ttu-id="3052b-191">若要加密備份檔案，請核取 **[加密備份]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="3052b-191">To encrypt the backup file check the **Encrypt backup** check box.</span></span> <span data-ttu-id="3052b-192">選取要用於加密備份檔案的加密演算法，並提供憑證或非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="3052b-192">Select an encryption algorithm to use for encrypting the backup file and provide a Certificate or Asymmetric key.</span></span> <span data-ttu-id="3052b-193">可用於加密的演算法包括：</span><span class="sxs-lookup"><span data-stu-id="3052b-193">The available algorithms for encryption are:</span></span>  
  
-   <span data-ttu-id="3052b-194">AES 128</span><span class="sxs-lookup"><span data-stu-id="3052b-194">AES 128</span></span>  
  
-   <span data-ttu-id="3052b-195">AES 192</span><span class="sxs-lookup"><span data-stu-id="3052b-195">AES 192</span></span>  
  
-   <span data-ttu-id="3052b-196">AES 256</span><span class="sxs-lookup"><span data-stu-id="3052b-196">AES 256</span></span>  
  
-   <span data-ttu-id="3052b-197">三重 DES</span><span class="sxs-lookup"><span data-stu-id="3052b-197">Triple DES</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3052b-198">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3052b-198">Using Transact-SQL</span></span>  
  
#### <a name="to-back-up-a-transaction-log"></a><span data-ttu-id="3052b-199">備份交易記錄檔</span><span class="sxs-lookup"><span data-stu-id="3052b-199">To back up a transaction log</span></span>  
  
1.  <span data-ttu-id="3052b-200">執行 BACKUP LOG 陳述式以備份交易記錄，並指定下列項目：</span><span class="sxs-lookup"><span data-stu-id="3052b-200">Execute the BACKUP LOG statement to back up the transaction log, specifying the following:</span></span>  
  
    -   <span data-ttu-id="3052b-201">所要備份的交易記錄所屬資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="3052b-201">The name of the database to which the transaction log that you want to back up belongs.</span></span>  
  
    -   <span data-ttu-id="3052b-202">寫入交易記錄備份的備份裝置。</span><span class="sxs-lookup"><span data-stu-id="3052b-202">The backup device where the transaction log backup is written.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="3052b-203">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3052b-203">Example (Transact-SQL)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3052b-204">這個範例使用 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 資料庫，而該資料庫則是使用簡單復原模式。</span><span class="sxs-lookup"><span data-stu-id="3052b-204">This example uses the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database, which uses the simple recovery model.</span></span> <span data-ttu-id="3052b-205">為了允許記錄備份，在執行完整資料庫備份之前，此資料庫已設定為使用完整復原模式。</span><span class="sxs-lookup"><span data-stu-id="3052b-205">To permit log backups, before taking a full database backup, the database was set to use the full recovery model.</span></span> <span data-ttu-id="3052b-206">如需詳細資訊，請參閱[檢視或變更資料庫的復原模式 &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3052b-206">For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md).</span></span>  
  
 <span data-ttu-id="3052b-207">這個範例會在先前所建立的具名備份裝置 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 上建立 `MyAdvWorks_FullRM_log1`資料庫的交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="3052b-207">This example creates a transaction log backup for the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database to the previously created named backup device, `MyAdvWorks_FullRM_log1`.</span></span>  
  
```sql  
BACKUP LOG AdventureWorks2012  
   TO MyAdvWorks_FullRM_log1;  
GO  
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="3052b-208">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3052b-208">Using PowerShell</span></span>  
  
<span data-ttu-id="3052b-209">使用 `Backup-SqlDatabase` 指令程式，並且為 `Log` 參數指定 `-BackupAction` 值。</span><span class="sxs-lookup"><span data-stu-id="3052b-209">Use the `Backup-SqlDatabase` cmdlet and specify `Log` for the value of the `-BackupAction` parameter.</span></span>  
  
<span data-ttu-id="3052b-210">下列範例會在伺服器執行個體 `MyDB` 的預設備份位置，建立 `Computer\Instance`資料庫的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="3052b-210">The following example creates a log backup of the `MyDB` database to the default backup location of the server instance `Computer\Instance`.</span></span>  
  
    ```powershell
    Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Log  
    ```  
  
<span data-ttu-id="3052b-211">若要設定及使用 SQL Server PowerShell 提供者，請參閱[SQL Server PowerShell 提供者](../../powershell/sql-server-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="3052b-211">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../powershell/sql-server-powershell-provider.md).</span></span>
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="3052b-212">相關工作</span><span class="sxs-lookup"><span data-stu-id="3052b-212">Related Tasks</span></span>  
  
-   [<span data-ttu-id="3052b-213">還原交易記錄備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3052b-213">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
-   [<span data-ttu-id="3052b-214">將 SQL Server 資料庫還原至某個時間點 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="3052b-214">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   [<span data-ttu-id="3052b-215">寫滿交易記錄疑難排解 &#40;SQL Server 錯誤 9002&#41;</span><span class="sxs-lookup"><span data-stu-id="3052b-215">Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;</span></span>](../logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
## <a name="see-also"></a><span data-ttu-id="3052b-216">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3052b-216">See Also</span></span>  
 <span data-ttu-id="3052b-217">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3052b-217">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="3052b-218">[套用交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3052b-218">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="3052b-219">[維護計畫](../maintenance-plans/maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="3052b-219">[Maintenance Plans](../maintenance-plans/maintenance-plans.md) </span></span>  
 [<span data-ttu-id="3052b-220">完整檔案備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3052b-220">Full File Backups &#40;SQL Server&#41;</span></span>](full-file-backups-sql-server.md)  
