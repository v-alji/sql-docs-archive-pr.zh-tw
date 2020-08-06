---
title: 備份資料庫工作 (維護計畫) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.backup.f1
- sql12.swb.maint.maintplanproperties.logbackup.f1
helpviewer_keywords:
- Back Up Database Task dialog box
ms.assetid: ed1ef012-fa14-4ba5-bafe-d1527ba065b3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 952730f09deeede360dff5e2bd83f8cdc8a20a67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594524"
---
# <a name="back-up-database-task-maintenance-plan"></a><span data-ttu-id="c1d40-102">備份資料庫工作 (維護計畫)</span><span class="sxs-lookup"><span data-stu-id="c1d40-102">Back Up Database Task (Maintenance Plan)</span></span>
  <span data-ttu-id="c1d40-103">使用 [備份資料庫工作] 對話方塊，即可將備份工作加入維護計畫中。</span><span class="sxs-lookup"><span data-stu-id="c1d40-103">Use the **Back Up Database Task** dialog to add a backup task to the maintenance plan.</span></span> <span data-ttu-id="c1d40-104">萬一因為發生系統或硬體失敗 (或使用者錯誤) 而導致資料庫在某方面發生損毀，因此需要還原已備份副本時，備份資料庫就相當重要。</span><span class="sxs-lookup"><span data-stu-id="c1d40-104">Backing up the database is important in case of system or hardware failure (or user errors) that cause the database to be damaged in some way, thus requiring a backed-up copy to be restored.</span></span> <span data-ttu-id="c1d40-105">此工作讓您能夠執行完整、差異、檔案和檔案群組，以及交易記錄的備份。</span><span class="sxs-lookup"><span data-stu-id="c1d40-105">This task allows you to perform full, differential, files and filegroups, and transaction log backups.</span></span>  
  
 <span data-ttu-id="c1d40-106">**建立備份資料庫工作**</span><span class="sxs-lookup"><span data-stu-id="c1d40-106">**To create a backup database task**</span></span>  
  
-   [<span data-ttu-id="c1d40-107">建立維護計畫</span><span class="sxs-lookup"><span data-stu-id="c1d40-107">Create a Maintenance Plan</span></span>](create-a-maintenance-plan.md)  
  
## <a name="options"></a><span data-ttu-id="c1d40-108">選項。</span><span class="sxs-lookup"><span data-stu-id="c1d40-108">Options</span></span>  
 <span data-ttu-id="c1d40-109">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="c1d40-109">**Connection**</span></span>  
 <span data-ttu-id="c1d40-110">選取執行此工作時要使用的伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="c1d40-110">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="c1d40-111">**新增**</span><span class="sxs-lookup"><span data-stu-id="c1d40-111">**New**</span></span>  
 <span data-ttu-id="c1d40-112">建立新的伺服器連接，以便執行此工作時使用。</span><span class="sxs-lookup"><span data-stu-id="c1d40-112">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="c1d40-113">下面會描述 **[新增連接]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c1d40-113">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="c1d40-114">**資料庫**</span><span class="sxs-lookup"><span data-stu-id="c1d40-114">**Databases**</span></span>  
 <span data-ttu-id="c1d40-115">指定受此工作影響的資料庫。</span><span class="sxs-lookup"><span data-stu-id="c1d40-115">Specify the databases affected by this task.</span></span> <span data-ttu-id="c1d40-116">選取後，下拉式清單就會提供下列選項：[所有資料庫]、[所有系統資料庫]、[所有使用者資料庫] 和 [這些特定資料庫]。</span><span class="sxs-lookup"><span data-stu-id="c1d40-116">When selected, the drop down list provides the following options: **All databases**, **All system databases**, **All user databases**, **These specific databases**.</span></span>  
  
 <span data-ttu-id="c1d40-117">**所有資料庫**</span><span class="sxs-lookup"><span data-stu-id="c1d40-117">**All databases**</span></span>  
 <span data-ttu-id="c1d40-118">產生維護計畫，以便針對所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="c1d40-118">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="c1d40-119">**所有系統資料庫 (master、msdb、model)**</span><span class="sxs-lookup"><span data-stu-id="c1d40-119">**All system databases (master, msdb, model)**</span></span>  
 <span data-ttu-id="c1d40-120">產生維護計畫，針對每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統資料庫執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="c1d40-120">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span> <span data-ttu-id="c1d40-121">不會針對使用者建立的資料庫執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="c1d40-121">No maintenance tasks are run against user-created databases.</span></span>  
  
 <span data-ttu-id="c1d40-122">**所有使用者資料庫 (不包括 master、model、msdb、tempdb)**</span><span class="sxs-lookup"><span data-stu-id="c1d40-122">**All user databases (excluding master, model, msdb, tempdb)**</span></span>  
 <span data-ttu-id="c1d40-123">產生維護計畫，針對所有使用者建立的資料庫執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="c1d40-123">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="c1d40-124">不會對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統資料庫執行任何維護工作。</span><span class="sxs-lookup"><span data-stu-id="c1d40-124">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
 <span data-ttu-id="c1d40-125">**下列資料庫**</span><span class="sxs-lookup"><span data-stu-id="c1d40-125">**These databases**</span></span>  
 <span data-ttu-id="c1d40-126">產生維護計畫，只針對選取的資料庫執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="c1d40-126">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="c1d40-127">如果選擇此選項，則必須在清單中至少選取一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="c1d40-127">At least one database in the list must be selected if this option is chosen.</span></span>  
  
 <span data-ttu-id="c1d40-128">**備份類型**</span><span class="sxs-lookup"><span data-stu-id="c1d40-128">**Backup type**</span></span>  
 <span data-ttu-id="c1d40-129">顯示要執行的備份類型。</span><span class="sxs-lookup"><span data-stu-id="c1d40-129">Shows the type of backup to be performed.</span></span>  
  
 <span data-ttu-id="c1d40-130">**備份元件**</span><span class="sxs-lookup"><span data-stu-id="c1d40-130">**Backup component**</span></span>  
 <span data-ttu-id="c1d40-131">選取 [資料庫]，即可備份整個資料庫。</span><span class="sxs-lookup"><span data-stu-id="c1d40-131">Select **Database** to back up the entire database.</span></span> <span data-ttu-id="c1d40-132">選取 **[檔案與檔案群組]** ，即可僅備份資料庫的一部分。</span><span class="sxs-lookup"><span data-stu-id="c1d40-132">Select **File and filegroups** to back up only a portion of the database.</span></span> <span data-ttu-id="c1d40-133">如果已選取，請提供檔案或檔案群組名稱。</span><span class="sxs-lookup"><span data-stu-id="c1d40-133">If selected, provide the file or filegroup name.</span></span> <span data-ttu-id="c1d40-134">在 **[資料庫]** 方塊中選取多個資料庫時，僅能指定 **[備份元件]** 的 **[資料庫]** 。</span><span class="sxs-lookup"><span data-stu-id="c1d40-134">When multiple databases are selected in the **Databases** box, only specify **Databases** for the **Backup components**.</span></span> <span data-ttu-id="c1d40-135">若要執行檔案或檔案群組備份，請為每個資料庫建立工作。</span><span class="sxs-lookup"><span data-stu-id="c1d40-135">To perform file or filegroup backups, create a task for each database.</span></span>  
  
 <span data-ttu-id="c1d40-136">**備份組逾期時間**</span><span class="sxs-lookup"><span data-stu-id="c1d40-136">**Backup set will expire**</span></span>  
 <span data-ttu-id="c1d40-137">指定備份組何時可由其他備份組覆寫。</span><span class="sxs-lookup"><span data-stu-id="c1d40-137">Specify when the backup set can be overwritten by another backup set.</span></span>  
  
 <span data-ttu-id="c1d40-138">**備份至**</span><span class="sxs-lookup"><span data-stu-id="c1d40-138">**Back up to**</span></span>  
 <span data-ttu-id="c1d40-139">將資料庫備份至檔案或至磁帶。</span><span class="sxs-lookup"><span data-stu-id="c1d40-139">Back up the database to a file or to tape.</span></span> <span data-ttu-id="c1d40-140">唯有安裝在包含資料庫之電腦的磁帶裝置可以使用。</span><span class="sxs-lookup"><span data-stu-id="c1d40-140">Only tape devices attached to the computer containing the database are available.</span></span>  
  
 <span data-ttu-id="c1d40-141">**跨越一或多個檔案的備份資料庫**</span><span class="sxs-lookup"><span data-stu-id="c1d40-141">**Back up databases across one or more files**</span></span>  
 <span data-ttu-id="c1d40-142">按一下 [新增]，即可開啟 [選取備份目的地] 對話方塊，並提供一或多個磁碟位置，或磁帶裝置。</span><span class="sxs-lookup"><span data-stu-id="c1d40-142">Click **Add** to open the **Select Backup Destination** dialog box, and provide one or more a disk location, or tape device.</span></span>  
  
 <span data-ttu-id="c1d40-143">**如果備份檔案存在**</span><span class="sxs-lookup"><span data-stu-id="c1d40-143">**If backup files exist**</span></span>  
 <span data-ttu-id="c1d40-144">選取 [附加] 將此備份加入檔案的結尾。</span><span class="sxs-lookup"><span data-stu-id="c1d40-144">Select **Append** to add this backup to the end of the file.</span></span> <span data-ttu-id="c1d40-145">選取 [覆寫] 即可移除檔案中所有舊的備份，並以此新備份取代。</span><span class="sxs-lookup"><span data-stu-id="c1d40-145">Select **Overwrite**, to remove any old backup in the file and replace them with this new backup.</span></span>  
  
 <span data-ttu-id="c1d40-146">**為每個資料庫建立一個備份檔案**</span><span class="sxs-lookup"><span data-stu-id="c1d40-146">**Create a backup file for every database**</span></span>  
 <span data-ttu-id="c1d40-147">在資料夾方塊裡所指定的位置中，建立備份檔案，</span><span class="sxs-lookup"><span data-stu-id="c1d40-147">Create a backup file in the location specified in the folder box.</span></span> <span data-ttu-id="c1d40-148">會為選取的每個資料庫建立一個檔案。</span><span class="sxs-lookup"><span data-stu-id="c1d40-148">One file will be created for each database selected.</span></span>  
  
 <span data-ttu-id="c1d40-149">**為每個資料庫建立一個子目錄**</span><span class="sxs-lookup"><span data-stu-id="c1d40-149">**Create a sub-directory for each database**</span></span>  
 <span data-ttu-id="c1d40-150">選取即可在子資料夾中放入每個資料庫。</span><span class="sxs-lookup"><span data-stu-id="c1d40-150">Select to place each database in a subfolder.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c1d40-151">雖然維護計畫可以建立子目錄，但是維護工作無法刪除子目錄。</span><span class="sxs-lookup"><span data-stu-id="c1d40-151">Although maintenance plans can create subdirectories, maintenance tasks cannot delete subdirectories.</span></span> <span data-ttu-id="c1d40-152">這項功能可降低利用「維護清除」工作刪除檔案這類惡意攻擊的可能性。</span><span class="sxs-lookup"><span data-stu-id="c1d40-152">This feature reduces the possibility of a malicious attack that uses the Maintenance Cleanup task to delete files.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c1d40-153">子目錄會繼承上層目錄的權限。</span><span class="sxs-lookup"><span data-stu-id="c1d40-153">The subdirectory inherits permissions from the parent directory.</span></span> <span data-ttu-id="c1d40-154">限制權限以避免未經授權的存取。</span><span class="sxs-lookup"><span data-stu-id="c1d40-154">Restrict permissions to avoid unauthorized access.</span></span>  
  
 <span data-ttu-id="c1d40-155">**資料夾**</span><span class="sxs-lookup"><span data-stu-id="c1d40-155">**Folder**</span></span>  
 <span data-ttu-id="c1d40-156">指定包含自動建立的資料庫檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="c1d40-156">Specify the folder to contain the automatically created database files.</span></span>  
  
 <span data-ttu-id="c1d40-157">**備份副檔名**</span><span class="sxs-lookup"><span data-stu-id="c1d40-157">**Backup file extension**</span></span>  
 <span data-ttu-id="c1d40-158">指定備份檔案所用的副檔名。</span><span class="sxs-lookup"><span data-stu-id="c1d40-158">Specify the extension to use for the backup files.</span></span> <span data-ttu-id="c1d40-159">預設為 **.bak**。</span><span class="sxs-lookup"><span data-stu-id="c1d40-159">The default is **.bak**.</span></span>  
  
 <span data-ttu-id="c1d40-160">**驗證備份完整性**</span><span class="sxs-lookup"><span data-stu-id="c1d40-160">**Verify backup integrity**</span></span>  
 <span data-ttu-id="c1d40-161">確認備份組是完整的，且所有磁碟區都可以讀取。</span><span class="sxs-lookup"><span data-stu-id="c1d40-161">Verify that the backup set is complete and that all volumes are readable.</span></span>  
  
 <span data-ttu-id="c1d40-162">**備份記錄的結尾，並讓資料庫保持在還原狀態**</span><span class="sxs-lookup"><span data-stu-id="c1d40-162">**Back up the tail of the log, and leave the database in the restoring state**</span></span>  
 <span data-ttu-id="c1d40-163">在還原資料庫之前，執行記錄備份做為最後一個步驟。</span><span class="sxs-lookup"><span data-stu-id="c1d40-163">Perform a log backup as the last step before restoring a database.</span></span> <span data-ttu-id="c1d40-164">如需詳細資訊，請參閱[結尾記錄備份 &#40;SQL Server&#41;](../backup-restore/tail-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c1d40-164">For more information, see [Tail-Log Backups &#40;SQL Server&#41;](../backup-restore/tail-log-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="c1d40-165">**設定備份壓縮**</span><span class="sxs-lookup"><span data-stu-id="c1d40-165">**Set backup compression**</span></span>  
 <span data-ttu-id="c1d40-166">在 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (或更新的版本) 中，選取下列其中一個 [備份壓縮](../backup-restore/backup-compression-sql-server.md) 值：</span><span class="sxs-lookup"><span data-stu-id="c1d40-166">In [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (or a later version), select one the following [backup compression](../backup-restore/backup-compression-sql-server.md) values:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c1d40-167">**使用預設伺服器設定**</span><span class="sxs-lookup"><span data-stu-id="c1d40-167">**Use the default server setting**</span></span>|<span data-ttu-id="c1d40-168">按一下即可使用伺服器層級的預設值。</span><span class="sxs-lookup"><span data-stu-id="c1d40-168">Click to use the server-level default.</span></span><br /><br /> <span data-ttu-id="c1d40-169">此預設值是由 [備份壓縮預設] 伺服器組態選項所設定。</span><span class="sxs-lookup"><span data-stu-id="c1d40-169">This default is set by the **backup compression default** server-configuration option.</span></span> <span data-ttu-id="c1d40-170">有關如何檢視這個選項目前之設定的詳細資訊，請參閱 [檢視或設定備份壓縮伺服器組態選項](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="c1d40-170">For information about how to view the current setting of this option,  see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>|  
|<span data-ttu-id="c1d40-171">**壓縮備份**</span><span class="sxs-lookup"><span data-stu-id="c1d40-171">**Compress backup**</span></span>|<span data-ttu-id="c1d40-172">不論目前的伺服器層級預設值為何，按一下即可壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="c1d40-172">Click to compress the backup, regardless of the server-level default.</span></span><br /><br /> <span data-ttu-id="c1d40-173">**\*\* 重要 \*\*** 根據預設，壓縮會大幅增加 CPU 使用量，而且壓縮程序所耗用的額外 CPU 可能會對並行作業造成不良的影響。</span><span class="sxs-lookup"><span data-stu-id="c1d40-173">**\*\* Important \*\*** By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely affect concurrent operations.</span></span> <span data-ttu-id="c1d40-174">因此，您可能會想要在由[資源管理員](../resource-governor/resource-governor.md)所限制之 CPU 使用量的工作階段中建立低優先權的壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="c1d40-174">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by [Resource Governor](../resource-governor/resource-governor.md).</span></span> <span data-ttu-id="c1d40-175">如需詳細資訊，請參閱本主題稍後介紹的＜ [使用資源管理員進行備份壓縮，以限制 CPU 使用率 &#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)限制的工作階段中，建立低優先權的壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="c1d40-175">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>|  
|<span data-ttu-id="c1d40-176">**不要壓縮備份**</span><span class="sxs-lookup"><span data-stu-id="c1d40-176">**Do not compress backup**</span></span>|<span data-ttu-id="c1d40-177">不論目前的伺服器層級預設值為何，按一下即可建立未壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="c1d40-177">Click to create an uncompressed backup, regardless of the server-level default.</span></span>|  
  
 <span data-ttu-id="c1d40-178">**檢視 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="c1d40-178">**View T-SQL**</span></span>  
 <span data-ttu-id="c1d40-179">根據選取的選項，檢視此工作在伺服器上執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c1d40-179">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c1d40-180">受影響的物件數目較為大量時，會多花一些時間才會顯示。</span><span class="sxs-lookup"><span data-stu-id="c1d40-180">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="c1d40-181">新增連接對話方塊</span><span class="sxs-lookup"><span data-stu-id="c1d40-181">New Connection Dialog Box</span></span>  
 <span data-ttu-id="c1d40-182">**連線名稱**</span><span class="sxs-lookup"><span data-stu-id="c1d40-182">**Connection name**</span></span>  
 <span data-ttu-id="c1d40-183">輸入新連接的名稱。</span><span class="sxs-lookup"><span data-stu-id="c1d40-183">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="c1d40-184">**選取或輸入伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="c1d40-184">**Select or enter a server name**</span></span>  
 <span data-ttu-id="c1d40-185">選取執行此工作時要連接的伺服器。</span><span class="sxs-lookup"><span data-stu-id="c1d40-185">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="c1d40-186">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="c1d40-186">**Refresh**</span></span>  
 <span data-ttu-id="c1d40-187">重新整理可用的伺服器清單。</span><span class="sxs-lookup"><span data-stu-id="c1d40-187">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="c1d40-188">**輸入要登入到伺服器的資訊**</span><span class="sxs-lookup"><span data-stu-id="c1d40-188">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="c1d40-189">指定如何對伺服器進行驗證。</span><span class="sxs-lookup"><span data-stu-id="c1d40-189">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="c1d40-190">**使用 Windows 整合式安全性**</span><span class="sxs-lookup"><span data-stu-id="c1d40-190">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="c1d40-191">使用 Windows 驗證連線到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c1d40-191">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with Windows Authentication.</span></span>  
  
 <span data-ttu-id="c1d40-192">**使用特定的使用者名稱和密碼**</span><span class="sxs-lookup"><span data-stu-id="c1d40-192">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="c1d40-193">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證連線到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c1d40-193">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="c1d40-194">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="c1d40-194">This option is not available.</span></span>  
  
 <span data-ttu-id="c1d40-195">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="c1d40-195">**User name**</span></span>  
 <span data-ttu-id="c1d40-196">提供驗證時要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="c1d40-196">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="c1d40-197">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="c1d40-197">This option is not available.</span></span>  
  
 <span data-ttu-id="c1d40-198">**密碼**</span><span class="sxs-lookup"><span data-stu-id="c1d40-198">**Password**</span></span>  
 <span data-ttu-id="c1d40-199">提供驗證時要使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="c1d40-199">Provide a password to use when authenticating.</span></span> <span data-ttu-id="c1d40-200">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="c1d40-200">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1d40-201">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1d40-201">See Also</span></span>  
 [<span data-ttu-id="c1d40-202">BACKUP &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c1d40-202">BACKUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/backup-transact-sql)  
  
  
