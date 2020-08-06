---
title: 備份資料庫 (媒體選項頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- swb.backupdatabase.mediaoptions.f1
- sql12.swb.backupdatabase.mediaoptions.f1
ms.assetid: eff36228-710c-4ed5-9af5-95859575dc0f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cd09eb091a7f488f891bc2e69d19ad039b65e065
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704213"
---
# <a name="back-up-database-media-options-page"></a><span data-ttu-id="d55f9-102">備份資料庫 (媒體選項頁面)</span><span class="sxs-lookup"><span data-stu-id="d55f9-102">Back Up Database (Media Options Page)</span></span>
  <span data-ttu-id="d55f9-103">使用 [備份資料庫]  對話方塊的 [媒體選項]  頁面以簡式或修改資料庫媒體選項。</span><span class="sxs-lookup"><span data-stu-id="d55f9-103">Use the  **Media Options** page of the **Back Up Database** dialog box to view or modify database media options.</span></span>  
  
 <span data-ttu-id="d55f9-104">**若要使用 SQL Server Management Studio 建立備份**</span><span class="sxs-lookup"><span data-stu-id="d55f9-104">**To create a backup by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="d55f9-105">建立完整資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d55f9-105">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="d55f9-106">建立差異資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d55f9-106">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d55f9-107">您可以定義資料庫維護計畫來建立資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="d55f9-107">You can define a database maintenance plan to create database backups.</span></span> <span data-ttu-id="d55f9-108">如需詳細資訊，請參閱[維護計劃](../maintenance-plans/maintenance-plans.md)和[使用維護計畫精靈](../maintenance-plans/use-the-maintenance-plan-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="d55f9-108">For more information, see [Maintenance Plans](../maintenance-plans/maintenance-plans.md) and [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d55f9-109">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 指定備份工作時，您可以按下 [指令碼]  按鈕，然後選取指令碼的目的地，以產生相對應的 [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) 指令碼。</span><span class="sxs-lookup"><span data-stu-id="d55f9-109">When you specify a backup task by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can generate the corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) script by clicking the **Script** button and then selecting a destination for the script.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d55f9-110">選項。</span><span class="sxs-lookup"><span data-stu-id="d55f9-110">Options</span></span>  
  
### <a name="overwrite-media"></a><span data-ttu-id="d55f9-111">覆寫媒體</span><span class="sxs-lookup"><span data-stu-id="d55f9-111">Overwrite media</span></span>  
 <span data-ttu-id="d55f9-112">[覆寫媒體]  面板的選項會控制備份寫入媒體的方式。</span><span class="sxs-lookup"><span data-stu-id="d55f9-112">The options of the **Overwrite media** panel control how the backup is written to the media.</span></span> <span data-ttu-id="d55f9-113">如果在 [備份資料庫] 對話方塊的 [一般] 頁面中選取 URL (Azure 儲存體) 作為備份目的地，系統會停用 [覆寫媒體] 區段下方的選項。</span><span class="sxs-lookup"><span data-stu-id="d55f9-113">IF you selected URL (Azure Storage) as the backup destination on the General page of the Back Up Database dialog box, the options under the Overwrite media section are disabled.</span></span> <span data-ttu-id="d55f9-114">您可以使用 `BACKUP TO URL.. WITH FORMAT` Transact-SQL 陳述式覆寫備份。</span><span class="sxs-lookup"><span data-stu-id="d55f9-114">You can overwrite a backup using the `BACKUP TO URL.. WITH FORMAT` Transact-SQL statement.</span></span> <span data-ttu-id="d55f9-115">如需詳細資訊，請參閱 [SQL Server Backup to URL](sql-server-backup-to-url.md)。</span><span class="sxs-lookup"><span data-stu-id="d55f9-115">For more information, see [SQL Server Backup to URL](sql-server-backup-to-url.md).</span></span>  
  
 <span data-ttu-id="d55f9-116">只有 [Backup to a new media, and erase all existing backup sets (備份至新的媒體，並清除所有現有的備份組)]  選項支援加密選項。</span><span class="sxs-lookup"><span data-stu-id="d55f9-116">Only the option, **Backup to a new media, and erase all existing backup sets** is supported with encryption options.</span></span> <span data-ttu-id="d55f9-117">如果您選取 [Back up to existing media (備份至現有媒體)]  區段下的選項，[備份選項]  頁面上的加密選項會停用。</span><span class="sxs-lookup"><span data-stu-id="d55f9-117">If you select the options under the **Back up to existing media** section, the encryptions options on the **Backup Options** page will be disabled.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d55f9-118">如需媒體集的一般資訊，請參閱 [媒體集、媒體家族與備份組 &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)之執行個體的電腦上時，此選項才可以使用。</span><span class="sxs-lookup"><span data-stu-id="d55f9-118">For information about media sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
 <span data-ttu-id="d55f9-119">**備份至現有的媒體集**</span><span class="sxs-lookup"><span data-stu-id="d55f9-119">**Back up to the existing media set**</span></span>  
 <span data-ttu-id="d55f9-120">將資料庫備份至現有的媒體集。</span><span class="sxs-lookup"><span data-stu-id="d55f9-120">Back up a database to an existing media set.</span></span> <span data-ttu-id="d55f9-121">選取此選項按鈕來啟動三個選項。</span><span class="sxs-lookup"><span data-stu-id="d55f9-121">Selecting this option button activates three options.</span></span>  
  
 <span data-ttu-id="d55f9-122">選擇下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="d55f9-122">Choose one of the following options:</span></span>  
  
 <span data-ttu-id="d55f9-123">**附加至現有的備份組**</span><span class="sxs-lookup"><span data-stu-id="d55f9-123">**Append to the existing backup set**</span></span>  
 <span data-ttu-id="d55f9-124">將備份組附加至現有的媒體集，會保留任何先前的備份。</span><span class="sxs-lookup"><span data-stu-id="d55f9-124">Append the backup set to the existing media set, preserving any prior backups.</span></span>  
  
 <span data-ttu-id="d55f9-125">**覆寫所有現有的備份組**</span><span class="sxs-lookup"><span data-stu-id="d55f9-125">**Overwrite all existing backup sets**</span></span>  
 <span data-ttu-id="d55f9-126">以目前的備份來取代現有媒體集上之任何先前的備份。</span><span class="sxs-lookup"><span data-stu-id="d55f9-126">Replace any prior backups on the existing media set with the current backup.</span></span>  
  
 <span data-ttu-id="d55f9-127">**檢查媒體集名稱及備份組是否逾期**</span><span class="sxs-lookup"><span data-stu-id="d55f9-127">**Check media set name and backup set expiration**</span></span>  
 <span data-ttu-id="d55f9-128">如果選擇性地備份到現有的媒體集，則備份作業必須確認媒體集的名稱以及備份組的到期日。</span><span class="sxs-lookup"><span data-stu-id="d55f9-128">Optionally, if backing up to an existing media set, require the backup operation to verify the name and the expiration date of the backup sets.</span></span>  
  
 <span data-ttu-id="d55f9-129">**媒體集名稱**</span><span class="sxs-lookup"><span data-stu-id="d55f9-129">**Media set name**</span></span>  
 <span data-ttu-id="d55f9-130">如果選擇性地選取了 [檢查媒體集名稱及備份組是否逾期]\*\*\*\*，請指定要用於此項備份作業的媒體集名稱。</span><span class="sxs-lookup"><span data-stu-id="d55f9-130">If **Check media set name and backup set expiration** is selected, optionally, specify the name of the media set to be used for this backup operation.</span></span>  
  
 <span data-ttu-id="d55f9-131">**備份至新的媒體集，並清除所有現有的備份組**</span><span class="sxs-lookup"><span data-stu-id="d55f9-131">**Back up to a new media set, and erase all existing backup sets**</span></span>  
 <span data-ttu-id="d55f9-132">使用新的媒體集，清除先前的備份組。</span><span class="sxs-lookup"><span data-stu-id="d55f9-132">Use a new media set, erasing the previous backup sets.</span></span>  
  
 <span data-ttu-id="d55f9-133">按一下此選項會啟動下列選項：</span><span class="sxs-lookup"><span data-stu-id="d55f9-133">Clicking this option activates the following options:</span></span>  
  
 <span data-ttu-id="d55f9-134">**新媒體集名稱**</span><span class="sxs-lookup"><span data-stu-id="d55f9-134">**New media set name**</span></span>  
 <span data-ttu-id="d55f9-135">選擇性地輸入媒體集的新名稱。</span><span class="sxs-lookup"><span data-stu-id="d55f9-135">Optionally, enter a new name for the media set.</span></span>  
  
 <span data-ttu-id="d55f9-136">**新媒體集描述**</span><span class="sxs-lookup"><span data-stu-id="d55f9-136">**New media set description**</span></span>  
 <span data-ttu-id="d55f9-137">選擇性地輸入新媒體集具有意義的描述。</span><span class="sxs-lookup"><span data-stu-id="d55f9-137">Optionally, enter a meaningful description of the new media set.</span></span> <span data-ttu-id="d55f9-138">此項描述應該足夠詳實，才能精確地表示內容。</span><span class="sxs-lookup"><span data-stu-id="d55f9-138">This description should be specific enough to communicate the contents accurately.</span></span>  
  
### <a name="reliability"></a><span data-ttu-id="d55f9-139">可靠性</span><span class="sxs-lookup"><span data-stu-id="d55f9-139">Reliability</span></span>  
 <span data-ttu-id="d55f9-140">[交易記錄]  面板的選項控制備份作業的錯誤管理。</span><span class="sxs-lookup"><span data-stu-id="d55f9-140">The options of the **Transaction log** panel control error management by the backup operation.</span></span>  
  
 <span data-ttu-id="d55f9-141">**完成後驗證備份**</span><span class="sxs-lookup"><span data-stu-id="d55f9-141">**Verify backup when finished**</span></span>  
 <span data-ttu-id="d55f9-142">確認備份組是完整的，且所有磁碟區都可以讀取。</span><span class="sxs-lookup"><span data-stu-id="d55f9-142">Verify that the backup set is complete and that all volumes are readable.</span></span>  
  
 <span data-ttu-id="d55f9-143">**寫入媒體之前執行總和檢查碼**</span><span class="sxs-lookup"><span data-stu-id="d55f9-143">**Perform checksum before writing to media**</span></span>  
 <span data-ttu-id="d55f9-144">寫入備份媒體之前確認總和檢查碼是否正確。</span><span class="sxs-lookup"><span data-stu-id="d55f9-144">Verify the checksums before writing to the backup media.</span></span> <span data-ttu-id="d55f9-145">選取此選項相當於在 [!INCLUDE[tsql](../../includes/tsql-md.md)]的 BACKUP 陳述式中指定 CHECKSUM 選項。</span><span class="sxs-lookup"><span data-stu-id="d55f9-145">Selecting this option is equivalent to specifying the CHECKSUM option in the BACKUP statement of [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d55f9-146">選取此選項可能會增加工作負載，並減少備份作業的備份輸送量。</span><span class="sxs-lookup"><span data-stu-id="d55f9-146">Selecting this option may increase the workload, and decrease the backup throughput of the backup operation.</span></span> <span data-ttu-id="d55f9-147">如需有關備份總和檢查碼的資訊，請參閱[在備份和還原期間可能的媒體錯誤 &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d55f9-147">For information about backup checksums, see [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).</span></span>  
  
 <span data-ttu-id="d55f9-148">**發生錯誤時繼續**</span><span class="sxs-lookup"><span data-stu-id="d55f9-148">**Continue on error**</span></span>  
 <span data-ttu-id="d55f9-149">即使發生一或多個錯誤，備份作業也會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="d55f9-149">The backup operation is to continue even after encountering one or more errors.</span></span>  
  
### <a name="transaction-log"></a><span data-ttu-id="d55f9-150">交易記錄</span><span class="sxs-lookup"><span data-stu-id="d55f9-150">Transaction log</span></span>  
 <span data-ttu-id="d55f9-151">[交易記錄]  面板的選項控制交易記錄備份的行為。</span><span class="sxs-lookup"><span data-stu-id="d55f9-151">The options of the **Transaction log** panel control the behavior of a transaction log backup.</span></span> <span data-ttu-id="d55f9-152">只有在完整復原模式或大量記錄復原模式之下，這些選項才具有相關性。</span><span class="sxs-lookup"><span data-stu-id="d55f9-152">These options are relevant only under the full recovery model or bulk-logged recovery model.</span></span> <span data-ttu-id="d55f9-153">只有在 [備份資料庫] 對話方塊的 [[一般](../../integration-services/general-page-of-integration-services-designers-options.md)] 頁面中的 [備份類型] 欄位中，選取 [交易記錄] 後，才會啟動這些選項。   </span><span class="sxs-lookup"><span data-stu-id="d55f9-153">They are activated only if **Transaction log** has been selected in the **Backup type** field on the [General](../../integration-services/general-page-of-integration-services-designers-options.md) page of the **Back Up Database** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d55f9-154">如需交易記錄備份的相關資訊，請參閱[交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d55f9-154">For information about transaction log backups, see [Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="d55f9-155">**截斷交易記錄**</span><span class="sxs-lookup"><span data-stu-id="d55f9-155">**Truncate the transaction log**</span></span>  
 <span data-ttu-id="d55f9-156">備份交易記錄並截斷，以釋放記錄空間。</span><span class="sxs-lookup"><span data-stu-id="d55f9-156">Back up the transaction log and truncate it to free log space.</span></span> <span data-ttu-id="d55f9-157">資料庫仍維持在線上。</span><span class="sxs-lookup"><span data-stu-id="d55f9-157">The database remains online.</span></span> <span data-ttu-id="d55f9-158">這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="d55f9-158">This is the default option.</span></span>  
  
 <span data-ttu-id="d55f9-159">**備份記錄的結尾，並讓資料庫保持在還原狀態**</span><span class="sxs-lookup"><span data-stu-id="d55f9-159">**Back up the tail of the log, and leave the database in the restoring state**</span></span>  
 <span data-ttu-id="d55f9-160">備份記錄的結尾，並讓資料庫保持在還原狀態。</span><span class="sxs-lookup"><span data-stu-id="d55f9-160">Back up the tail of the log and leave the database in a restoring state.</span></span> <span data-ttu-id="d55f9-161">此選項會建立「結尾記錄備份」，其會為尚未備份的記錄 (使用中的記錄) 進行備份，一般而言，是為還原資料庫做準備。 </span><span class="sxs-lookup"><span data-stu-id="d55f9-161">This option creates a *tail-log backup*, which backs up logs that have not yet been backed up (the active log), typically, in preparation for restoring a database.</span></span> <span data-ttu-id="d55f9-162">資料庫完全還原之前，使用者無法使用資料庫。</span><span class="sxs-lookup"><span data-stu-id="d55f9-162">The database will be unavailable to users until it is completely restored.</span></span>  
  
 <span data-ttu-id="d55f9-163">選取此選項相當於在 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 陳述式 ([!INCLUDE[tsql](../../includes/tsql-md.md)]) 中指定 WITH NO_TRUNCATE, NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="d55f9-163">Selecting this option is equivalent to specifying WITH NO_TRUNCATE, NORECOVERY in a [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement ([!INCLUDE[tsql](../../includes/tsql-md.md)]).</span></span> <span data-ttu-id="d55f9-164">如需詳細資訊，請參閱[結尾記錄備份 &#40;SQL Server&#41;](tail-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d55f9-164">For more information, see [Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md).</span></span>  
  
### <a name="tape-drive"></a><span data-ttu-id="d55f9-165">磁帶機</span><span class="sxs-lookup"><span data-stu-id="d55f9-165">Tape drive</span></span>  
 <span data-ttu-id="d55f9-166">[磁帶機]  面板的選項控制備份作業的磁帶管理。</span><span class="sxs-lookup"><span data-stu-id="d55f9-166">The options of the **Tape drive** panel control tape management during the backup operation.</span></span> <span data-ttu-id="d55f9-167">只有在 [備份資料庫] 對話方塊的 [[一般](../../integration-services/general-page-of-integration-services-designers-options.md)] 頁面中的 [目的地] 面板中，選取 [磁帶] 後，才會啟動這些選項。   </span><span class="sxs-lookup"><span data-stu-id="d55f9-167">These options are activated only if **Tape** has been selected in the **Destination** panel on the [General](../../integration-services/general-page-of-integration-services-designers-options.md) page of the **Back Up Database** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d55f9-168">如需有關如何使用磁帶裝置的資訊，請參閱[備份裝置 &#40;SQL Server&#41;](backup-devices-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d55f9-168">For information about how to use tape devices, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>  
  
 <span data-ttu-id="d55f9-169">**備份後卸載磁帶**</span><span class="sxs-lookup"><span data-stu-id="d55f9-169">**Unload the tape after backup**</span></span>  
 <span data-ttu-id="d55f9-170">備份完成之後再卸載磁帶。</span><span class="sxs-lookup"><span data-stu-id="d55f9-170">After the backup is complete, unload the tape.</span></span>  
  
 <span data-ttu-id="d55f9-171">**卸載之前倒轉磁帶**</span><span class="sxs-lookup"><span data-stu-id="d55f9-171">**Rewind the tape before unloading**</span></span>  
 <span data-ttu-id="d55f9-172">卸載磁帶之前先將其釋放及倒轉。</span><span class="sxs-lookup"><span data-stu-id="d55f9-172">Before unloading the tape, release and rewind it.</span></span> <span data-ttu-id="d55f9-173">只有在選取 [備份後卸除磁帶]  時才會啟用這個選項。</span><span class="sxs-lookup"><span data-stu-id="d55f9-173">This is enabled only if **Unload the tape after backup** is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d55f9-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d55f9-174">See Also</span></span>  
 <span data-ttu-id="d55f9-175">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d55f9-175">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="d55f9-176">[備份交易記錄 &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d55f9-176">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="d55f9-177">[備份檔案和檔案群組 &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d55f9-177">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 [<span data-ttu-id="d55f9-178">資料庫損毀時備份交易記錄 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d55f9-178">Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;</span></span>](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
  
