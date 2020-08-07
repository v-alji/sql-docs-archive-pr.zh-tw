---
title: 還原差異資料庫備份 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full differential backups [SQL Server]
- restoring databases [SQL Server], full differential backups
- database backups [SQL Server], full differential backups
- database restores [SQL Server], full differential backups
- backing up databases [SQL Server], full differential backups
ms.assetid: 0dd971a4-ee38-4dd3-9f30-ef77fc58dd11
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a8eab18d84efc1a990715e0d5488085252f93a7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598466"
---
# <a name="restore-a-differential-database-backup-sql-server"></a><span data-ttu-id="1a333-102">還原差異資料庫備份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1a333-102">Restore a Differential Database Backup (SQL Server)</span></span>
  <span data-ttu-id="1a333-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中還原差異資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="1a333-103">This topic describes how to restore a differential database backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1a333-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="1a333-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1a333-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="1a333-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1a333-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="1a333-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1a333-107">先決條件</span><span class="sxs-lookup"><span data-stu-id="1a333-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="1a333-108">安全性</span><span class="sxs-lookup"><span data-stu-id="1a333-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1a333-109">**若要使用下列項目還原差異資料庫備份：**</span><span class="sxs-lookup"><span data-stu-id="1a333-109">**To restore a differential database backup, using:**</span></span>  
  
     [<span data-ttu-id="1a333-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1a333-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1a333-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1a333-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="1a333-112">相關工作</span><span class="sxs-lookup"><span data-stu-id="1a333-112">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1a333-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="1a333-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1a333-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="1a333-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="1a333-115">在明確或隱含的交易中，不允許使用 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="1a333-115">RESTORE is not allowed in an explicit or implicit transaction.</span></span>  
  
-   <span data-ttu-id="1a333-116">在舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，無法還原較新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本所建立的備份。</span><span class="sxs-lookup"><span data-stu-id="1a333-116">Backups that are created by more recent version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be restored in earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="1a333-117">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，您可以從使用 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更新版本所建立的資料庫備份還原使用者資料庫。</span><span class="sxs-lookup"><span data-stu-id="1a333-117">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can restore a user database from a database backup that was created by using [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or a later version.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="1a333-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="1a333-118">Prerequisites</span></span>  
  
-   <span data-ttu-id="1a333-119">在完整或大量記錄還原模式下，您必須先備份使用中的交易記錄檔 (也稱為記錄檔的結尾)，才能還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="1a333-119">Under the full or bulk-logged recovery model, before you can restore a database, you must back up the active transaction log (known as the tail of the log).</span></span> <span data-ttu-id="1a333-120">如需詳細資訊，請參閱 [備份交易記錄 &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)資料庫還原至新位置，並選擇性地重新命名資料庫。</span><span class="sxs-lookup"><span data-stu-id="1a333-120">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1a333-121">Security</span><span class="sxs-lookup"><span data-stu-id="1a333-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1a333-122">權限</span><span class="sxs-lookup"><span data-stu-id="1a333-122">Permissions</span></span>  
 <span data-ttu-id="1a333-123">如果還原的資料庫不存在，使用者必須有 CREATE DATABASE 權限，才能執行 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="1a333-123">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="1a333-124">如果資料庫存在，RESTORE 權限預設為 **系統管理員 (sysadmin)** 和 **資料庫建立者 (dbcreator)** 固定伺服器角色的成員以及資料庫的擁有者 (**dbo**) (對 FROM DATABASE_SNAPSHOT 選項而言，資料庫一律存在)。</span><span class="sxs-lookup"><span data-stu-id="1a333-124">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="1a333-125">RESTORE 權限提供給伺服器隨時可以取得其成員資格資訊的角色。</span><span class="sxs-lookup"><span data-stu-id="1a333-125">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="1a333-126">由於資料庫必須是可存取且未損毀，才能夠檢查固定資料庫角色成員資格，但執行 RESTORE 時未必如此；因此， **db_owner** 固定資料庫角色的成員並沒有 RESTORE 權限。</span><span class="sxs-lookup"><span data-stu-id="1a333-126">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1a333-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1a333-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-a-differential-database-backup"></a><span data-ttu-id="1a333-128">還原差異資料庫備份</span><span class="sxs-lookup"><span data-stu-id="1a333-128">To restore a differential database backup</span></span>  
  
1.  <span data-ttu-id="1a333-129">連線到適當的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體之後，請在 [物件總管] 中按一下伺服器名稱以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="1a333-129">After you connect to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="1a333-130">展開 **[資料庫]** 。</span><span class="sxs-lookup"><span data-stu-id="1a333-130">Expand **Databases**.</span></span> <span data-ttu-id="1a333-131">視資料庫而定，選取使用者資料庫，或者展開 [系統資料庫]  ，再選取系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="1a333-131">Depending on the database, either select a user database or expand **System Databases**, and then select a system database.</span></span>  
  
3.  <span data-ttu-id="1a333-132">以滑鼠右鍵按一下資料庫，依序指向 [工作]  及 [還原]  ，然後按一下 [資料庫]  。</span><span class="sxs-lookup"><span data-stu-id="1a333-132">Right-click the database, point to **Tasks**, point to **Restore**, and then click **Database**.</span></span>  
  
4.  <span data-ttu-id="1a333-133">在 **[一般]** 頁面上，使用 **[來源]** 區段指定要還原之備份組的來源和位置。</span><span class="sxs-lookup"><span data-stu-id="1a333-133">On the **General** page, use the **Source** section to specify the source and location of the backup sets to restore.</span></span> <span data-ttu-id="1a333-134">選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="1a333-134">Select one of the following options:</span></span>  
  
    -   <span data-ttu-id="1a333-135">**Database**</span><span class="sxs-lookup"><span data-stu-id="1a333-135">**Database**</span></span>  
  
         <span data-ttu-id="1a333-136">從下拉式清單中選取要還原的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1a333-136">Select the database to restore from the drop-down list.</span></span> <span data-ttu-id="1a333-137">此清單僅包含已根據 **msdb** 備份記錄而備份的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1a333-137">The list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1a333-138">如果備份是根據不同的伺服器建立的，目的地伺服器就沒有指定之資料庫的備份記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="1a333-138">If the backup is taken from a different server, the destination server will not have the backup history information for the specified database.</span></span> <span data-ttu-id="1a333-139">在此情況下，請選取 **[裝置]** ，以便手動指定要還原的檔案或裝置。</span><span class="sxs-lookup"><span data-stu-id="1a333-139">In this case, select **Device** to manually specify the file or device to restore.</span></span>  
  
    -   <span data-ttu-id="1a333-140">**裝置**</span><span class="sxs-lookup"><span data-stu-id="1a333-140">**Device**</span></span>  
  
         <span data-ttu-id="1a333-141">按一下瀏覽 ( **...** ) 按鈕，開啟 [選取備份裝置]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1a333-141">Click the browse (**...**) button to open the **Select backup devices** dialog box.</span></span> <span data-ttu-id="1a333-142">在 **[備份媒體類型]** 方塊中，選取列出的其中一種裝置類型。</span><span class="sxs-lookup"><span data-stu-id="1a333-142">In the **Backup media type** box, select one of the listed device types.</span></span> <span data-ttu-id="1a333-143">若要選取 **[備份媒體]** 方塊中的一個或多個裝置，請按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="1a333-143">To select one or more devices for the **Backup media** box, click **Add**.</span></span>  
  
         <span data-ttu-id="1a333-144">將您要的裝置加入 **[備份媒體]** 清單方塊後，按一下 **[確定]** 即可回到 **[一般]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="1a333-144">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
         <span data-ttu-id="1a333-145">在 **[來源：裝置：資料庫]** 清單方塊中，選取應該還原的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="1a333-145">In the **Source: Device: Database** list box, select the name of the database which should be restored.</span></span>  
  
         <span data-ttu-id="1a333-146">**注意** ：這份清單只能在選取 **[裝置]** 時使用。</span><span class="sxs-lookup"><span data-stu-id="1a333-146">**Note** This list is only available when **Device** is selected.</span></span> <span data-ttu-id="1a333-147">只有在所選取裝置上有備份的資料庫才可供使用。</span><span class="sxs-lookup"><span data-stu-id="1a333-147">Only databases that have backups on the selected device will be available.</span></span>  
  
5.  <span data-ttu-id="1a333-148">在 **[目的地]** 區段中，會將要還原之資料庫的名稱自動填入 **[資料庫]** 方塊。</span><span class="sxs-lookup"><span data-stu-id="1a333-148">In the **Destination** section, the **Database** box is automatically populated with the name of the database to be restored.</span></span> <span data-ttu-id="1a333-149">若要變更資料庫的名稱，請在 **[資料庫]** 方塊中輸入新名稱。</span><span class="sxs-lookup"><span data-stu-id="1a333-149">To change the name of the database, enter the new name in the **Database** box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1a333-150">若要在特定時間點停止還原，請按一下 **[時間表]** 存取 **[備份時間表]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1a333-150">To stop the restore at a specific point in time, click **Timeline** to access the **Backup Timeline** dialog box.</span></span> <span data-ttu-id="1a333-151">如需在特定時間點停止資料庫還原的說明，請參閱[將 SQL Server 資料庫還原至某個時間點 &#40;完整復原模式&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)。</span><span class="sxs-lookup"><span data-stu-id="1a333-151">For help with stopping a database restore at a specific point in time, see [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
6.  <span data-ttu-id="1a333-152">在 **[要還原的備份組]** 方格中，透過您想要還原的差異備份選取備份。</span><span class="sxs-lookup"><span data-stu-id="1a333-152">In the **Backup sets to restore** grid, select the backups through the differential backup that you wish to restore.</span></span>  
  
     <span data-ttu-id="1a333-153">如需 [要還原的備份組]  方格中各資料行的相關資訊，請參閱[還原資料庫 &#40;一般頁面&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="1a333-153">For information about the columns in the **Backup sets to restore** grid, see [Restore Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
7.  <span data-ttu-id="1a333-154">在 **[選項]** 頁面的 **[還原選項]** 面板中，您可以選取下列任何選項 (如果情況適用)：</span><span class="sxs-lookup"><span data-stu-id="1a333-154">On the **Options** page, in the **Restore options** panel, you can select any of the following options, if appropriate for your situation:</span></span>  
  
    -   <span data-ttu-id="1a333-155">**覆寫現有的資料庫 (WITH REPLACE)**</span><span class="sxs-lookup"><span data-stu-id="1a333-155">**Overwrite the existing database (WITH REPLACE)**</span></span>  
  
    -   <span data-ttu-id="1a333-156">**保留複寫設定 (WITH KEEP_REPLICATION)**</span><span class="sxs-lookup"><span data-stu-id="1a333-156">**Preserve the replication settings (WITH KEEP_REPLICATION)**</span></span>  
  
    -   <span data-ttu-id="1a333-157">**還原每個備份之前先提示**</span><span class="sxs-lookup"><span data-stu-id="1a333-157">**Prompt before restoring each backup**</span></span>  
  
    -   <span data-ttu-id="1a333-158">**限制對還原資料庫的存取 (WITH RESTRICTED_USER)**</span><span class="sxs-lookup"><span data-stu-id="1a333-158">**Restrict access to the restored database (WITH RESTRICTED_USER)**</span></span>  
  
     <span data-ttu-id="1a333-159">如需這些選項的詳細資訊，請參閱[還原資料庫 &#40;選項頁面&#41;](restore-database-options-page.md)。</span><span class="sxs-lookup"><span data-stu-id="1a333-159">For more information about these options, see [Restore Database &#40;Options Page&#41;](restore-database-options-page.md).</span></span>  
  
8.  <span data-ttu-id="1a333-160">針對 **[還原狀態]** 方塊，選取選項。</span><span class="sxs-lookup"><span data-stu-id="1a333-160">Select an option for the **Recovery state** box.</span></span> <span data-ttu-id="1a333-161">此方塊決定資料庫在還原作業之後的狀態。</span><span class="sxs-lookup"><span data-stu-id="1a333-161">This box determines the state of the database after the restore operation.</span></span>  
  
    -   <span data-ttu-id="1a333-162">**RESTORE WITH RECOVERY** 是預設行為，透過回復未認可的交易，讓資料庫保持備妥可用。</span><span class="sxs-lookup"><span data-stu-id="1a333-162">**RESTORE WITH RECOVERY** is the default behavior which leaves the database ready for use by rolling back the uncommitted transactions.</span></span> <span data-ttu-id="1a333-163">無法還原其他交易記錄。</span><span class="sxs-lookup"><span data-stu-id="1a333-163">Additional transaction logs cannot be restored.</span></span> <span data-ttu-id="1a333-164">若您要立即還原所有必要的備份，請選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="1a333-164">Select this option if you are restoring all of the necessary backups now.</span></span>  
  
    -   <span data-ttu-id="1a333-165">**RESTORE WITH NORECOVERY** ，讓資料庫保持不運作，且不回復未認可的交易。</span><span class="sxs-lookup"><span data-stu-id="1a333-165">**RESTORE WITH NORECOVERY** which leaves the database non-operational, and does not roll back the uncommitted transactions.</span></span> <span data-ttu-id="1a333-166">可以還原其他交易記錄。</span><span class="sxs-lookup"><span data-stu-id="1a333-166">Additional transaction logs can be restored.</span></span> <span data-ttu-id="1a333-167">資料庫在復原之前都無法使用。</span><span class="sxs-lookup"><span data-stu-id="1a333-167">The database cannot be used until it is recovered.</span></span>  
  
    -   <span data-ttu-id="1a333-168">**RESTORE WITH STANDBY** ，讓資料庫處於唯讀模式。</span><span class="sxs-lookup"><span data-stu-id="1a333-168">**RESTORE WITH STANDBY** which leaves the database in read-only mode.</span></span> <span data-ttu-id="1a333-169">它會復原未認可的交易，但會將復原動作儲存在待命資料庫檔案中，以還原復原影響。</span><span class="sxs-lookup"><span data-stu-id="1a333-169">It undoes uncommitted transactions, but saves the undo actions in a standby file so that recovery effects can be reverted.</span></span>  
  
     <span data-ttu-id="1a333-170">如需這些選項的描述，請參閱[還原資料庫 &#40;選項頁面&#41;](restore-database-options-page.md)。</span><span class="sxs-lookup"><span data-stu-id="1a333-170">For descriptions of the options, see [Restore Database &#40;Options Page&#41;](restore-database-options-page.md).</span></span>  
  
9. <span data-ttu-id="1a333-171">若資料庫有使用中的連接，還原作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="1a333-171">Restore operations will fail if there are active connections to the database.</span></span> <span data-ttu-id="1a333-172">核取 **[關閉現有的連接選項]** ，確定已關閉 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 與資料庫之間的所有使用中連接。</span><span class="sxs-lookup"><span data-stu-id="1a333-172">Check the **Close existing connections option** to ensure that all active connections between [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and the database are closed.</span></span>  
  
10. <span data-ttu-id="1a333-173">如果想要系統在每個還原作業之間提示您，請選取 **[還原每個備份之前先提示]** 。</span><span class="sxs-lookup"><span data-stu-id="1a333-173">Select **Prompt before restoring each backup** if you wish to be prompted between each restore operation.</span></span> <span data-ttu-id="1a333-174">除非資料庫夠大，而且您想要監視還原作業的狀態，否則這通常不需要。</span><span class="sxs-lookup"><span data-stu-id="1a333-174">This is not usually necessary unless the database is large and you wish to monitor the status of the restore operation.</span></span>  
  
11. <span data-ttu-id="1a333-175">或者，使用 **[檔案]** 頁面將資料庫還原到新位置。</span><span class="sxs-lookup"><span data-stu-id="1a333-175">Optionally, use the **Files** page to restore the database to a new location.</span></span> <span data-ttu-id="1a333-176">如需移動資料庫的說明，請參閱[將資料庫還原到新位置 &#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1a333-176">For help with moving a database, see [Restore a Database to a New Location &#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md).</span></span>  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1a333-177">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1a333-177">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-a-differential-database-backup"></a><span data-ttu-id="1a333-178">還原差異資料庫備份</span><span class="sxs-lookup"><span data-stu-id="1a333-178">To restore a differential database backup</span></span>  
  
1.  <span data-ttu-id="1a333-179">執行 RESTORE DATABASE 陳述式並指定 NORECOVERY 子句，以還原在差異資料庫備份之前的完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="1a333-179">Execute the RESTORE DATABASE statement, specifying the NORECOVERY clause, to restore the full database backup that comes before the differential database backup.</span></span> <span data-ttu-id="1a333-180">如需詳細資訊，請參閱[如何：還原完整備份](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="1a333-180">For more information, see [How to: Restore a Full Backup](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md).</span></span>  
  
2.  <span data-ttu-id="1a333-181">執行 RESTORE DATABASE 陳述式以還原差異資料庫備份，請指定：</span><span class="sxs-lookup"><span data-stu-id="1a333-181">Execute the RESTORE DATABASE statement to restore the differential database backup, specifying:</span></span>  
  
    -   <span data-ttu-id="1a333-182">將套用差異資料庫備份的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="1a333-182">The name of the database to which the differential database backup is applied.</span></span>  
  
    -   <span data-ttu-id="1a333-183">將要還原差異資料庫備份的備份裝置。</span><span class="sxs-lookup"><span data-stu-id="1a333-183">The backup device where the differential database backup is restored from.</span></span>  
  
    -   <span data-ttu-id="1a333-184">如果在還原差異資料庫備份之後，您有交易記錄備份可以套用，則指定 NORECOVERY 子句。</span><span class="sxs-lookup"><span data-stu-id="1a333-184">The NORECOVERY clause if you have transaction log backups to apply after the differential database backup is restored.</span></span> <span data-ttu-id="1a333-185">否則，指定 RECOVERY 子句。</span><span class="sxs-lookup"><span data-stu-id="1a333-185">Otherwise, specify the RECOVERY clause.</span></span>  
  
3.  <span data-ttu-id="1a333-186">使用完整或大量記錄復原模式，還原差異資料庫備份可將資料庫還原到完成差異資料庫備份的時間點。</span><span class="sxs-lookup"><span data-stu-id="1a333-186">With the full or bulk-logged recovery model, restoring a differential database backup restores the database to the point at which the differential database backup was completed.</span></span> <span data-ttu-id="1a333-187">若要復原到失敗點，您必須套用上次建立差異資料庫備份後所建立的所有交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="1a333-187">To recover to the point of failure, you must apply all transaction log backups created after the last differential database backup was created.</span></span> <span data-ttu-id="1a333-188">如需詳細資訊，請參閱[套用交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1a333-188">For more information, see [Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="1a333-189">範例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1a333-189">Examples (Transact-SQL)</span></span>  
  
#### <a name="a-restoring-a-differential-database-backup"></a><span data-ttu-id="1a333-190">A.</span><span class="sxs-lookup"><span data-stu-id="1a333-190">A.</span></span> <span data-ttu-id="1a333-191">還原差異資料庫備份</span><span class="sxs-lookup"><span data-stu-id="1a333-191">Restoring a differential database backup</span></span>  
 <span data-ttu-id="1a333-192">這個範例還原 `MyAdvWorks` 資料庫與差異資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="1a333-192">This example restores a database and differential database backup of the `MyAdvWorks` database.</span></span>  
  
```sql  
-- Assume the database is lost, and restore full database,   
-- specifying the original full database backup and NORECOVERY,   
-- which allows subsequent restore operations to proceed.  
RESTORE DATABASE MyAdvWorks  
   FROM MyAdvWorks_1  
   WITH NORECOVERY;  
GO  
-- Now restore the differential database backup, the second backup on   
-- the MyAdvWorks_1 backup device.  
RESTORE DATABASE MyAdvWorks  
   FROM MyAdvWorks_1  
   WITH FILE = 2,  
   RECOVERY;  
GO  
```  
  
#### <a name="b-restoring-a-database-differential-database-and-transaction-log-backup"></a><span data-ttu-id="1a333-193">B.</span><span class="sxs-lookup"><span data-stu-id="1a333-193">B.</span></span> <span data-ttu-id="1a333-194">還原資料庫、差異資料庫及交易記錄備份</span><span class="sxs-lookup"><span data-stu-id="1a333-194">Restoring a database, differential database, and transaction log backup</span></span>  
 <span data-ttu-id="1a333-195">這個範例還原 `MyAdvWorks` 資料庫、差異資料庫及其交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="1a333-195">This example restores a database, differential database, and transaction log backup of the `MyAdvWorks` database.</span></span>  
  
```sql  
-- Assume the database is lost at this point. Now restore the full   
-- database. Specify the original full database backup and NORECOVERY.  
-- NORECOVERY allows subsequent restore operations to proceed.  
RESTORE DATABASE MyAdvWorks  
   FROM MyAdvWorks_1  
   WITH NORECOVERY;  
GO  
-- Now restore the differential database backup, the second backup on   
-- the MyAdvWorks_1 backup device.  
RESTORE DATABASE MyAdvWorks  
   FROM MyAdvWorks_1  
   WITH FILE = 2,  
   NORECOVERY;  
GO  
-- Now restore each transaction log backup created after  
-- the differential database backup.  
RESTORE LOG MyAdvWorks  
   FROM MyAdvWorks_log1  
   WITH NORECOVERY;  
GO  
RESTORE LOG MyAdvWorks  
   FROM MyAdvWorks_log2  
   WITH RECOVERY;  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="1a333-196">相關工作</span><span class="sxs-lookup"><span data-stu-id="1a333-196">Related Tasks</span></span>  
  
-   [<span data-ttu-id="1a333-197">建立差異資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1a333-197">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="1a333-198">還原交易記錄備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1a333-198">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="1a333-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a333-199">See Also</span></span>  
 <span data-ttu-id="1a333-200">[差異備份 &#40;SQL Server&#41;](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1a333-200">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="1a333-201">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1a333-201">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
