---
title: 將 SQL Server 資料庫還原至某個時間點 (完整復原模式) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- STOPAT clause [RESTORE LOG statement]
- point in time recovery [SQL Server]
- restoring databases [SQL Server], point in time
ms.assetid: 3a5daefd-08a8-4565-b54f-28ad01a47d32
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0c71ff6e75cbbf27042c1eac70b1f97076290865
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598465"
---
# <a name="restore-a-sql-server-database-to-a-point-in-time-full-recovery-model"></a><span data-ttu-id="4d2d4-102">將 SQL Server 資料庫還原至某個時間點 (完整復原模式)</span><span class="sxs-lookup"><span data-stu-id="4d2d4-102">Restore a SQL Server Database to a Point in Time (Full Recovery Model)</span></span>
  <span data-ttu-id="4d2d4-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中將資料庫還原至時間點。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-103">This topic describes how to restore a database to a point in time in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="4d2d4-104">本主題僅與使用完整或大量記錄復原模式的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫相關。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-104">This topic is relevant only for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that use the full or bulk-logged recovery models.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4d2d4-105">在大量記錄復原模式下，如果記錄備份包含大量記錄的變更，則時間點復原不可能復原至該備份內的時間點。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-105">Under the bulk-logged recovery model, if a log backup contains bulk-logged changes, point-in-time recovery is not possible to a point within that backup.</span></span> <span data-ttu-id="4d2d4-106">資料庫必須復原至交易記錄備份的結尾。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-106">The database must be recovered to the end of the transaction log backup.</span></span>  
  
-   <span data-ttu-id="4d2d4-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="4d2d4-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4d2d4-108">建議</span><span class="sxs-lookup"><span data-stu-id="4d2d4-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="4d2d4-109">安全性</span><span class="sxs-lookup"><span data-stu-id="4d2d4-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4d2d4-110">**若要將 SQL Server 資料庫還原到某個時間點，請使用：**</span><span class="sxs-lookup"><span data-stu-id="4d2d4-110">**To restore a SQL Server database to a point in time, using:**</span></span>  
  
     [<span data-ttu-id="4d2d4-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4d2d4-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4d2d4-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4d2d4-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4d2d4-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="4d2d4-113">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="4d2d4-114">建議</span><span class="sxs-lookup"><span data-stu-id="4d2d4-114">Recommendations</span></span>  
  
-   <span data-ttu-id="4d2d4-115">您可以使用 STANDBY 尋找未知時間點。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-115">Use STANDBY to find unknown point in time.</span></span>  
  
-   <span data-ttu-id="4d2d4-116">指定還原順序中較早的時間點</span><span class="sxs-lookup"><span data-stu-id="4d2d4-116">Specify the point in time early in a restore sequence</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4d2d4-117">Security</span><span class="sxs-lookup"><span data-stu-id="4d2d4-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4d2d4-118">權限</span><span class="sxs-lookup"><span data-stu-id="4d2d4-118">Permissions</span></span>  
 <span data-ttu-id="4d2d4-119">如果還原的資料庫不存在，使用者必須有 CREATE DATABASE 權限，才能執行 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-119">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="4d2d4-120">如果資料庫存在，RESTORE 權限預設為 **系統管理員 (sysadmin)** 和 **資料庫建立者 (dbcreator)** 固定伺服器角色的成員以及資料庫的擁有者 (**dbo**) (對 FROM DATABASE_SNAPSHOT 選項而言，資料庫一律存在)。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-120">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="4d2d4-121">RESTORE 權限提供給伺服器隨時可以取得其成員資格資訊的角色。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-121">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="4d2d4-122">由於資料庫必須是可存取且未損毀，才能夠檢查固定資料庫角色成員資格，但執行 RESTORE 時未必如此；因此， **db_owner** 固定資料庫角色的成員並沒有 RESTORE 權限。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-122">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4d2d4-123">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4d2d4-123">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="4d2d4-124">**將資料庫還原至某個時間點**</span><span class="sxs-lookup"><span data-stu-id="4d2d4-124">**To restore a database to a point in time**</span></span>  
  
1.  <span data-ttu-id="4d2d4-125">在 [物件總管] 中，連接至適當的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體，並展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-125">In Object Explorer, connect to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="4d2d4-126">展開 **[資料庫]** 。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-126">Expand **Databases**.</span></span> <span data-ttu-id="4d2d4-127">視資料庫而定，選取使用者資料庫，或者展開 [系統資料庫]  ，再選取系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-127">Depending on the database, either select a user database or expand **System Databases**, and then select a system database.</span></span>  
  
3.  <span data-ttu-id="4d2d4-128">以滑鼠右鍵按一下資料庫，依序指向 [工作]  及 [還原]  ，然後按一下 [資料庫]  。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-128">Right-click the database, point to **Tasks**, point to **Restore**, and then click **Database**.</span></span>  
  
4.  <span data-ttu-id="4d2d4-129">在 **[一般]** 頁面上，使用 **[來源]** 區段指定要還原之備份組的來源和位置。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-129">On the **General** page, use the **Source** section to specify the source and location of the backup sets to restore.</span></span> <span data-ttu-id="4d2d4-130">選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="4d2d4-130">Select one of the following options:</span></span>  
  
    -   <span data-ttu-id="4d2d4-131">**Database**</span><span class="sxs-lookup"><span data-stu-id="4d2d4-131">**Database**</span></span>  
  
         <span data-ttu-id="4d2d4-132">從下拉式清單中選取要還原的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-132">Select the database to restore from the drop-down list.</span></span> <span data-ttu-id="4d2d4-133">此清單僅包含已根據 **msdb** 備份記錄而備份的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-133">The list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4d2d4-134">如果備份是根據不同的伺服器建立的，目的地伺服器就沒有指定之資料庫的備份記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-134">If the backup is taken from a different server, the destination server will not have the backup history information for the specified database.</span></span> <span data-ttu-id="4d2d4-135">在此情況下，請選取 **[裝置]** ，以便手動指定要還原的檔案或裝置。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-135">In this case, select **Device** to manually specify the file or device to restore.</span></span>  
  
    -   <span data-ttu-id="4d2d4-136">**裝置**</span><span class="sxs-lookup"><span data-stu-id="4d2d4-136">**Device**</span></span>  
  
         <span data-ttu-id="4d2d4-137">按一下瀏覽 ( **...** ) 按鈕，開啟 [選取備份裝置]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-137">Click the browse (**...**) button to open the **Select backup devices** dialog box.</span></span> <span data-ttu-id="4d2d4-138">在 **[備份媒體類型]** 方塊中，選取列出的其中一種裝置類型。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-138">In the **Backup media type** box, select one of the listed device types.</span></span> <span data-ttu-id="4d2d4-139">若要選取 **[備份媒體]** 方塊中的一個或多個裝置，請按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-139">To select one or more devices for the **Backup media** box, click **Add**.</span></span>  
  
         <span data-ttu-id="4d2d4-140">將您要的裝置加入 **[備份媒體]** 清單方塊後，按一下 **[確定]** 即可回到 **[一般]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-140">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
         <span data-ttu-id="4d2d4-141">在 **[來源: 裝置: 資料庫]** 清單方塊中，選取應該還原的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-141">In the **Source: Device: Database** list box, select the name of the database which should be restored.</span></span>  
  
         <span data-ttu-id="4d2d4-142">**注意** ：這份清單只能在選取 **[裝置]** 時使用。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-142">**Note** This list is only available when **Device** is selected.</span></span> <span data-ttu-id="4d2d4-143">只有在所選取裝置上有備份的資料庫才可供使用。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-143">Only databases that have backups on the selected device will be available.</span></span>  
  
5.  <span data-ttu-id="4d2d4-144">在 **[目的地]** 區段中，會將要還原之資料庫的名稱自動填入 **[資料庫]** 方塊。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-144">In the **Destination** section, the **Database** box is automatically populated with the name of the database to be restored.</span></span> <span data-ttu-id="4d2d4-145">若要變更資料庫的名稱，請在 **[資料庫]** 方塊中輸入新名稱。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-145">To change the name of the database, enter the new name in the **Database** box.</span></span>  
  
6.  <span data-ttu-id="4d2d4-146">按一下 **[時間表]** ，存取 **[備份時間表]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-146">Click **Timeline** to access the **Backup Timeline** dialog box.</span></span>  
  
7.  <span data-ttu-id="4d2d4-147">在 **[還原至]** 區段中，按一下 **[特定的日期與時間]** 。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-147">In the **Restore to** section, click **Specific date and time**.</span></span>  
  
8.  <span data-ttu-id="4d2d4-148">使用 **[日期]** 及 **[時間]** 方塊或滑動軸，指定應該停止還原的特定日期與時間。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-148">Use either the **Date** and **Time** boxes or the slider bar to specify a specific date and time to where the restore should stop.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="4d2d4-149">您可以使用 [時間表間隔]  方塊變更時間表上顯示的時間量。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-149">Use the **Timeline Interval** box to change the amount of time displayed on the timeline.</span></span>  
  
9. <span data-ttu-id="4d2d4-150">當您指定了特定的時間點之後，Database Recovery Advisor 便會在 **[要還原的備份組]** 方格的 **[還原]** 資料行中確定只選取要還原到該時間點所需的備份。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-150">After you have specified a specific point in time, the Database Recovery Advisor ensures that only backups that are required for restoring to that point in time are selected in the **Restore** column of the **Backup sets to restore** grid.</span></span> <span data-ttu-id="4d2d4-151">這些選取的備份為您的時間點還原構成了建議的還原計畫。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-151">These selected backups make up the recommended restore plan for your point-in-time restore.</span></span> <span data-ttu-id="4d2d4-152">您應該只使用選取的備份來進行時間點還原作業。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-152">You should use only the selected backups for your point-in-time restore operation.</span></span>  
  
     <span data-ttu-id="4d2d4-153">如需 [要還原的備份組]  方格中各資料行的相關資訊，請參閱[還原資料庫 &#40;一般頁面&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-153">For information about the columns in the **Backup sets to restore** grid, see [Restore Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span> <span data-ttu-id="4d2d4-154">如需資料庫復原建議程式的相關資訊，請參閱[還原和復原概觀 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-154">For information about the Database Recovery Advisor, see [Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md).</span></span>  
  
10. <span data-ttu-id="4d2d4-155">在 **[選項]** 頁面的 **[還原選項]** 面板中，您可以選取下列任何選項 (如果情況適用)：</span><span class="sxs-lookup"><span data-stu-id="4d2d4-155">On the **Options** page, in the **Restore options** panel, you can select any of the following options, if appropriate for your situation:</span></span>  
  
    -   <span data-ttu-id="4d2d4-156">**覆寫現有的資料庫 (WITH REPLACE)**</span><span class="sxs-lookup"><span data-stu-id="4d2d4-156">**Overwrite the existing database (WITH REPLACE)**</span></span>  
  
    -   <span data-ttu-id="4d2d4-157">**保留複寫設定 (WITH KEEP_REPLICATION)**</span><span class="sxs-lookup"><span data-stu-id="4d2d4-157">**Preserve the replication settings (WITH KEEP_REPLICATION)**</span></span>  
  
    -   <span data-ttu-id="4d2d4-158">**限制對還原資料庫的存取 (WITH RESTRICTED_USER)**</span><span class="sxs-lookup"><span data-stu-id="4d2d4-158">**Restrict access to the restored database (WITH RESTRICTED_USER)**</span></span>  
  
     <span data-ttu-id="4d2d4-159">如需這些選項的詳細資訊，請參閱[還原資料庫 &#40;選項頁面&#41;](restore-database-options-page.md)。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-159">For more information about these options, see [Restore Database &#40;Options Page&#41;](restore-database-options-page.md).</span></span>  
  
11. <span data-ttu-id="4d2d4-160">針對 **[還原狀態]** 方塊，選取選項。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-160">Select an option for the **Recovery state** box.</span></span> <span data-ttu-id="4d2d4-161">此方塊決定資料庫在還原作業之後的狀態。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-161">This box determines the state of the database after the restore operation.</span></span>  
  
    -   <span data-ttu-id="4d2d4-162">**RESTORE WITH RECOVERY** 是預設行為，透過回復未認可的交易，讓資料庫保持備妥可用。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-162">**RESTORE WITH RECOVERY** is the default behavior which leaves the database ready for use by rolling back the uncommitted transactions.</span></span> <span data-ttu-id="4d2d4-163">無法還原其他交易記錄。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-163">Additional transaction logs cannot be restored.</span></span> <span data-ttu-id="4d2d4-164">若您要立即還原所有必要的備份，請選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-164">Select this option if you are restoring all of the necessary backups now.</span></span>  
  
    -   <span data-ttu-id="4d2d4-165">**RESTORE WITH NORECOVERY** ，讓資料庫保持不運作，且不回復未認可的交易。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-165">**RESTORE WITH NORECOVERY** which leaves the database non-operational, and does not roll back the uncommitted transactions.</span></span> <span data-ttu-id="4d2d4-166">可以還原其他交易記錄。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-166">Additional transaction logs can be restored.</span></span> <span data-ttu-id="4d2d4-167">資料庫在復原之前都無法使用。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-167">The database cannot be used until it is recovered.</span></span>  
  
    -   <span data-ttu-id="4d2d4-168">**RESTORE WITH STANDBY** ，讓資料庫處於唯讀模式。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-168">**RESTORE WITH STANDBY** which leaves the database in read-only mode.</span></span> <span data-ttu-id="4d2d4-169">它會復原未認可的交易，但會將復原動作儲存在待命資料庫檔案中，以還原復原影響。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-169">It undoes uncommitted transactions, but saves the undo actions in a standby file so that recovery effects can be reverted.</span></span>  
  
     <span data-ttu-id="4d2d4-170">如需這些選項的描述，請參閱[還原資料庫 &#40;選項頁面&#41;](restore-database-options-page.md)。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-170">For descriptions of the options, see [Restore Database &#40;Options Page&#41;](restore-database-options-page.md).</span></span>  
  
12. <span data-ttu-id="4d2d4-171">如果選取的時間點需要 [還原前先進行結尾記錄備份]  ，則會予以選取。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-171">**Take tail-log backup before restore** will be selected if it is necessary for the point in time that you have selected.</span></span> <span data-ttu-id="4d2d4-172">您不需要修改這個設定，但是即使不需要，還是可以選擇備份記錄結尾。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-172">You do not need to modify this setting, but you can choose to backup the tail of the log even if it is not required.</span></span>  
  
13. <span data-ttu-id="4d2d4-173">若資料庫有使用中的連接，還原作業可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-173">Restore operations may fail if there are active connections to the database.</span></span> <span data-ttu-id="4d2d4-174">核取 **[關閉現有的連接選項]** ，確定已關閉 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 與資料庫之間的所有使用中連接。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-174">Check the **Close existing connections option** to ensure that all active connections between [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and the database are closed.</span></span> <span data-ttu-id="4d2d4-175">這個核取方塊會在執行還原作業之前將資料庫設定為單一使用者模式，並在完成後將資料庫設定為多使用者模式。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-175">This check box sets the database to single user mode before performing the restore operations, and sets the database to multi-user mode when complete.</span></span>  
  
14. <span data-ttu-id="4d2d4-176">如果想要系統在每個還原作業之間提示您，請選取 **[還原每個備份之前先提示]** 。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-176">Select **Prompt before restoring each backup** if you wish to be prompted between each restore operation.</span></span> <span data-ttu-id="4d2d4-177">除非資料庫夠大，而且您想要監視還原作業的狀態，否則這通常不需要。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-177">This is not usually necessary unless the database is large and you wish to monitor the status of the restore operation.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4d2d4-178">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4d2d4-178">Using Transact-SQL</span></span>  
 <span data-ttu-id="4d2d4-179">**開始之前**</span><span class="sxs-lookup"><span data-stu-id="4d2d4-179">**Before you begin**</span></span>  
  
 <span data-ttu-id="4d2d4-180">指定的時間一律是從記錄備份中還原。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-180">A specified time is always restored from a log backup.</span></span> <span data-ttu-id="4d2d4-181">在還原順序的每個 RESTORE LOG 陳述式中，您必須在相同的 STOPAT 子句中指定目標時間或交易。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-181">In every RESTORE LOG statement of the restore sequence, you must specify your target time or transaction in an identical STOPAT clause.</span></span> <span data-ttu-id="4d2d4-182">您必須先還原其端點早於目標還原時間的完整資料庫備份，當做時間點還原的必要條件。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-182">As a prerequisite to a point-in-time restore, you must first restore a full database backup whose end point is earlier than your target restore time.</span></span> <span data-ttu-id="4d2d4-183">該完整資料庫備份可以晚於最近的完整資料庫備份，只要您之後還原每個後續的記錄備份即可，最多並包括含有目標時間點的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-183">That full database backup can be older than the most recent full database backup as long as you then restore every subsequent log backup, up to and including the log backup that contains your target point in time.</span></span>  
  
 <span data-ttu-id="4d2d4-184">若要協助您識別要還原哪個資料庫備份，可以選擇性地在 RESTORE DATABASE 陳述式中指定 WITH STOPAT 子句，以便在資料庫備份太接近指定的目標時間時引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-184">To help you identify which database backup to restore, you can optionally specify your WITH STOPAT clause in your RESTORE DATABASE statement to raise an error if a data backup is too recent for the specified target time.</span></span> <span data-ttu-id="4d2d4-185">此時，系統一定會還原完整的資料備份，即使它包含目標時間也一樣。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-185">The complete data backup is always restored, even if it contains the target time.</span></span>  
  
 <span data-ttu-id="4d2d4-186">**基本 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語法**</span><span class="sxs-lookup"><span data-stu-id="4d2d4-186">**Basic [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax**</span></span>  
  
 <span data-ttu-id="4d2d4-187">RESTORE LOG *database_name* FROM <backup_device> WITH STOPAT \*\* = *`time`* ，\*\* RECOVERY .。。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-187">RESTORE LOG *database_name* FROM <backup_device> WITH STOPAT **=*`time`*,** RECOVERY...</span></span>  
  
 <span data-ttu-id="4d2d4-188">復原點是在 `datetime` 由*時間*指定的值之前或之前發生的最新交易認可。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-188">The recovery point is the latest transaction commit that occurred at or before the `datetime` value that is specified by *time*.</span></span>  
  
 <span data-ttu-id="4d2d4-189">若只要還原特定時間點之前進行的修改，請為您要還原的每個備份指定 WITH STOPAT **=** *time*。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-189">To restore only the modifications that were made before a specific point in time, specify WITH STOPAT **=** *time* for each backup you restore.</span></span> <span data-ttu-id="4d2d4-190">這樣可確保您不會還原到超過目標時間。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-190">This makes sure that you do not go past the target time.</span></span>  
  
 <span data-ttu-id="4d2d4-191">**將資料庫還原至某個時間點**</span><span class="sxs-lookup"><span data-stu-id="4d2d4-191">**To restore a database to a point in time**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d2d4-192">如需這個程序的範例，請參閱本節稍後的 [範例 &#40;Transact-SQL&#41;](#TsqlExample)。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-192">For an example of this procedure, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="4d2d4-193">連接至想要在其上還原資料庫的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-193">Connect to server instance on which you want to restore the database.</span></span>  
  
2.  <span data-ttu-id="4d2d4-194">使用 NORECOVERY 選項執行 RESTORE DATABASE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-194">Execute the RESTORE DATABASE statement using the NORECOVERY option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4d2d4-195">如果部分還原順序排除任何 [FILESTREAM](../blob/filestream-sql-server.md) 檔案群組，則不支援時間點還原。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-195">If a partial restore sequence excludes any [FILESTREAM](../blob/filestream-sql-server.md) filegroup, point-in-time restore is not supported.</span></span> <span data-ttu-id="4d2d4-196">您可以強制還原順序，以繼續進行。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-196">You can force the restore sequence to continue.</span></span> <span data-ttu-id="4d2d4-197">但是，絕對無法還原 RESTORE 陳述式中省略的 FILESTREAM 檔案群組。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-197">However the FILESTREAM filegroups that are omitted from your RESTORE statement can never be restored.</span></span> <span data-ttu-id="4d2d4-198">若要強制時間點還原，請指定 CONTINUE_AFTER_ERROR 選項，連同 STOPAT、STOPATMARK 或 STOPBEFOREMARK 選項，而且您也必須在後續的 RESTORE LOG 陳述式中指定這些項目。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-198">To force a point-in-time restore, specify the CONTINUE_AFTER_ERROR option together with the STOPAT, STOPATMARK, or STOPBEFOREMARK option, which you must also specify in your subsequent RESTORE LOG statements.</span></span> <span data-ttu-id="4d2d4-199">如果您指定 CONTINUE_AFTER_ERROR，則部分還原順序會成功，而 FILESTREAM 檔案群組則會變成無法復原。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-199">If you specify CONTINUE_AFTER_ERROR, the partial restore sequence succeeds and the FILESTREAM filegroup becomes unrecoverable.</span></span>  
  
3.  <span data-ttu-id="4d2d4-200">還原上一次的差異資料庫備份 (如有)，但不復原資料庫 (RESTORE DATABASE *database_name* FROM *backup_device* WITH NORECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-200">Restore the last differential database backup, if any,  without recovering the database (RESTORE DATABASE *database_name* FROM *backup_device* WITH NORECOVERY).</span></span>  
  
4.  <span data-ttu-id="4d2d4-201">依建立的相同順序，套用每個交易記錄備份，並指定您想要停止還原記錄的時間 (RESTORE DATABASE *database_name*從 <backup_device> WITH STOPAT\*\* = *`time`* ，\*\* RECOVERY) 。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-201">Apply each transaction log backup in the same sequence in which they were created, specifying the time at which you intend to stop restoring log (RESTORE DATABASE *database_name* FROM <backup_device> WITH STOPAT**=*`time`*,** RECOVERY).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4d2d4-202">RECOVERY 及 STOPAT 選項。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-202">The RECOVERY and STOPAT options.</span></span> <span data-ttu-id="4d2d4-203">如果交易記錄備份中不含所要求的時間 (例如指定的時間超出交易記錄的結束時間)，則會產生警告訊息，且此資料庫會維持未復原狀態。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-203">If the transaction log backup does not contain the requested time (for example, if the time specified is beyond the end of the time covered by the transaction log), a warning is generated and the database remains unrecovered.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="4d2d4-204">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4d2d4-204">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="4d2d4-205">下列範例會將資料庫還原至 `12:00 AM``April 15, 2020` 時的狀態，並顯示含有多個記錄備份的還原作業。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-205">The following example restores a database to its state as of `12:00 AM` on `April 15, 2020` and shows a restore operation that involves multiple log backups.</span></span> <span data-ttu-id="4d2d4-206">在備份裝置 `AdventureWorksBackups`上，要還原的完整資料庫備份是裝置上的第三個備份組 (`FILE = 3`)，第一個記錄備份是第四個備份組 (`FILE = 4`)，而第二個記錄備份是第五個備份組 (`FILE = 5`)。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-206">On the backup device, `AdventureWorksBackups`, the full database backup to be restored is the third backup set on the device (`FILE = 3`), the first log backup is the fourth backup set (`FILE = 4`), and the second log backup is the fifth backup set (`FILE = 5`).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4d2d4-207">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫使用簡單復原模式。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-207">The [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database uses the simple recovery model.</span></span> <span data-ttu-id="4d2d4-208">若要允許記錄備份，在執行完整資料庫備份之前，已使用 `ALTER DATABASE AdventureWorks SET RECOVERY FULL`將資料庫設定為使用完整復原模式。</span><span class="sxs-lookup"><span data-stu-id="4d2d4-208">To permit log backups, before taking a full database backup, the database was set to use the full recovery model, using `ALTER DATABASE AdventureWorks SET RECOVERY FULL`.</span></span>  
  
```  
RESTORE DATABASE AdventureWorks  
   FROM AdventureWorksBackups  
   WITH FILE=3, NORECOVERY;  
  
RESTORE LOG AdventureWorks  
   FROM AdventureWorksBackups  
   WITH FILE=4, NORECOVERY, STOPAT = 'Apr 15, 2020 12:00 AM';  
  
RESTORE LOG AdventureWorks  
   FROM AdventureWorksBackups  
   WITH FILE=5, NORECOVERY, STOPAT = 'Apr 15, 2020 12:00 AM';  
RESTORE DATABASE AdventureWorks WITH RECOVERY;   
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="4d2d4-209">相關工作</span><span class="sxs-lookup"><span data-stu-id="4d2d4-209">Related Tasks</span></span>  
  
-   [<span data-ttu-id="4d2d4-210">還原資料庫備份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="4d2d4-210">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="4d2d4-211">備份交易記錄 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4d2d4-211">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="4d2d4-212">在完整復原模式下將資料庫還原至失敗點 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4d2d4-212">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="4d2d4-213">還原資料庫至標示的交易 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="4d2d4-213">Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="4d2d4-214">復原到記錄序號 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4d2d4-214">Recover to a Log Sequence Number &#40;SQL Server&#41;</span></span>](recover-to-a-log-sequence-number-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="4d2d4-215">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d2d4-215">See Also</span></span>  
 <span data-ttu-id="4d2d4-216">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4d2d4-216">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="4d2d4-217">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4d2d4-217">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="4d2d4-218">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4d2d4-218">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
  
