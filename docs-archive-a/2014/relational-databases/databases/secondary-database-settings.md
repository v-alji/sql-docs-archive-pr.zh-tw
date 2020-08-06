---
title: 次要資料庫設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.settings.dest.f1
ms.assetid: f992ffc9-ee42-43fe-acec-512032f0ded1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 265d6beda830e2090392918ae14d10c8b7752d02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595085"
---
# <a name="secondary-database-settings"></a><span data-ttu-id="816fd-102">次要資料庫設定</span><span class="sxs-lookup"><span data-stu-id="816fd-102">Secondary Database Settings</span></span>
  <span data-ttu-id="816fd-103">您可以使用此對話方塊，來設定和修改記錄傳送組態中，次要資料庫的屬性。</span><span class="sxs-lookup"><span data-stu-id="816fd-103">Use this dialog box to configure and to modify the properties of a secondary database in the log shipping configuration.</span></span>  
  
 <span data-ttu-id="816fd-104">如需記錄傳送概念的說明，請參閱 [關於記錄傳送 &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="816fd-104">For an explanation of log shipping concepts, see [About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="816fd-105">選項。</span><span class="sxs-lookup"><span data-stu-id="816fd-105">Options</span></span>  
 <span data-ttu-id="816fd-106">**次要伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="816fd-106">**Secondary server instance**</span></span>  
 <span data-ttu-id="816fd-107">顯示目前在記錄傳送組態中設定為次要伺服器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="816fd-107">Displays the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] currently configured to be a secondary server in the log shipping configuration.</span></span>  
  
 <span data-ttu-id="816fd-108">**次要資料庫**</span><span class="sxs-lookup"><span data-stu-id="816fd-108">**Secondary database**</span></span>  
 <span data-ttu-id="816fd-109">顯示記錄傳送組態中，次要資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="816fd-109">Displays the name of the secondary database for the log shipping configuration.</span></span> <span data-ttu-id="816fd-110">將新的次要資料庫加入記錄傳送組態時，您可以從清單中選擇資料庫，或在方塊中輸入新資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="816fd-110">When adding a new secondary database to a log shipping configuration, you can choose a database from the list or type the name of a new of the database into the box.</span></span> <span data-ttu-id="816fd-111">如果您輸入新資料庫的名稱，就必須選取 **[初始化]** 索引標籤上的選項，將主要資料庫的完整資料庫備份還原至次要資料庫中。</span><span class="sxs-lookup"><span data-stu-id="816fd-111">If you enter the name of a new database, you must select an option on the **Initialization** tab that restores a full database backup of the primary database into the secondary database.</span></span> <span data-ttu-id="816fd-112">進行還原作業時，會建立新的資料庫。</span><span class="sxs-lookup"><span data-stu-id="816fd-112">The new database is created as part of the restore operation.</span></span>  
  
 <span data-ttu-id="816fd-113">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="816fd-113">**Connect**</span></span>  
 <span data-ttu-id="816fd-114">連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，在記錄傳送組態中做為次要伺服器使用。</span><span class="sxs-lookup"><span data-stu-id="816fd-114">Connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for use as a secondary server in the log shipping configuration.</span></span> <span data-ttu-id="816fd-115">用來連接的帳戶必須是次要伺服器執行個體上的系統管理員 (sysadmin) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="816fd-115">The account used to connect must be a member of the sysadmin fixed server role on the secondary server instance.</span></span>  
  
 <span data-ttu-id="816fd-116">**初始化索引標籤**</span><span class="sxs-lookup"><span data-stu-id="816fd-116">**Initialize tab**</span></span>  
 <span data-ttu-id="816fd-117">選項如下：</span><span class="sxs-lookup"><span data-stu-id="816fd-117">The options are as follows:</span></span>  
  
 <span data-ttu-id="816fd-118">**是，產生主要資料庫的完整備份，並將其還原到次要資料庫**</span><span class="sxs-lookup"><span data-stu-id="816fd-118">**Yes, generate a full backup of the primary database and restore it to the secondary database**</span></span>  
 <span data-ttu-id="816fd-119">透過備份主要資料庫並將它還原至次要伺服器，即可讓 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 設定您的次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="816fd-119">Have [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] configure your secondary database by backing up the primary database and restoring it on the secondary server.</span></span> <span data-ttu-id="816fd-120">如果您在 **[次要資料庫]** 方塊中輸入新的資料庫名稱，進行還原作業時就會建立此資料庫。</span><span class="sxs-lookup"><span data-stu-id="816fd-120">If you entered a new database name in the **Secondary database** box, the database will be created as part of the restore operation.</span></span>  
  
 <span data-ttu-id="816fd-121">**還原選項**</span><span class="sxs-lookup"><span data-stu-id="816fd-121">**Restore Options**</span></span>  
 <span data-ttu-id="816fd-122">如果您要將次要資料庫的資料與記錄檔，還原至次要伺服器的非預設位置，請按一下此選項。</span><span class="sxs-lookup"><span data-stu-id="816fd-122">Click if you want to restore the data and log files for the secondary database into nondefault locations on the secondary server.</span></span>  
  
 <span data-ttu-id="816fd-123">此按鈕會開啟 **[還原選項]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="816fd-123">This button opens the **Restore Options** dialog box.</span></span> <span data-ttu-id="816fd-124">因此，您可以指定非預設資料夾的路徑，以存放次要資料庫及其記錄。</span><span class="sxs-lookup"><span data-stu-id="816fd-124">There, you can specify paths to nondefault folders where you want the secondary database and its log to reside.</span></span> <span data-ttu-id="816fd-125">如果您指定其中一個資料夾，就必須同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="816fd-125">If you specify either folder, you must specify both.</span></span>  
  
 <span data-ttu-id="816fd-126">這些路徑必須參考到次要伺服器的本機磁碟機。</span><span class="sxs-lookup"><span data-stu-id="816fd-126">The paths must refer to drives that are local to the secondary server.</span></span> <span data-ttu-id="816fd-127">而且這些路徑必須有本機磁碟機代號和冒號 (例如 `C:`)。</span><span class="sxs-lookup"><span data-stu-id="816fd-127">Also, the paths must begin with a local drive letter and colon (for example, `C:`).</span></span> <span data-ttu-id="816fd-128">對應的磁碟機代號或網路路徑無效。</span><span class="sxs-lookup"><span data-stu-id="816fd-128">Mapped drive letters or network paths are invalid.</span></span>  
  
 <span data-ttu-id="816fd-129">如果您按一下 **[還原選項]** 按鈕，然後決定要使用預設資料夾，我們建議您取消 **[還原選項]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="816fd-129">If you click the **Restore Options** button and then decide that you want to use the default folders, we recommend that you cancel the **Restore Options** dialog box.</span></span> <span data-ttu-id="816fd-130">若您已經指定非預設位置，而想要改用預設位置，請再按一下 **[還原選項]** ，並清除文字方塊，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="816fd-130">If you have already specified nondefault locations and now want to use the default locations instead, click **Restore Options** again, clear the text boxes, and click OK.</span></span>  
  
 <span data-ttu-id="816fd-131">**是，將主要資料庫的現有備份還原到次要資料庫**</span><span class="sxs-lookup"><span data-stu-id="816fd-131">**Yes, restore an existing backup of the primary database to the secondary database**</span></span>  
 <span data-ttu-id="816fd-132">讓 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 使用主要資料庫的現有備份，以初始化次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="816fd-132">Have [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] use an existing backup of your primary database to initialize the secondary database.</span></span> <span data-ttu-id="816fd-133">在 **[備份檔案]** 方塊中輸入該備份的位置。</span><span class="sxs-lookup"><span data-stu-id="816fd-133">Type the location of that backup in the **Backup file** box.</span></span> <span data-ttu-id="816fd-134">如果您在 [次要資料庫] 方塊中輸入新的資料庫名稱，進行還原作業時就會建立此資料庫。</span><span class="sxs-lookup"><span data-stu-id="816fd-134">If you entered a new database name in the Secondary database box, the database will be created as part of the restore operation.</span></span>  
  
 <span data-ttu-id="816fd-135">**[備份檔案]**</span><span class="sxs-lookup"><span data-stu-id="816fd-135">**Backup file**</span></span>  
 <span data-ttu-id="816fd-136">如果您選擇 [是，將主要資料庫的現有備份還原到次要資料庫]  選項，請輸入要用來初始化次要資料庫之完整資料庫備份的路徑與檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="816fd-136">Type the path and filename of the full database backup you want to use to initialize the secondary database if you chose the **Yes, restore and existing backup of the primary database to the secondary database option**.</span></span>  
  
 <span data-ttu-id="816fd-137">**還原選項**</span><span class="sxs-lookup"><span data-stu-id="816fd-137">**Restore Options**</span></span>  
 <span data-ttu-id="816fd-138">請參閱本主題稍早有關此按鈕的描述。</span><span class="sxs-lookup"><span data-stu-id="816fd-138">See the description of this button earlier in this topic.</span></span>  
  
 <span data-ttu-id="816fd-139">**否，次要資料庫已初始化**</span><span class="sxs-lookup"><span data-stu-id="816fd-139">**No, the secondary database is initialized**</span></span>  
 <span data-ttu-id="816fd-140">指定次要資料庫已經初始化，且已備妥要從主要資料庫接受交易記錄的備份。</span><span class="sxs-lookup"><span data-stu-id="816fd-140">Specify that the secondary database is already initialized and ready to accept transaction log backups from the primary database.</span></span> <span data-ttu-id="816fd-141">如果您在 **[次要資料庫]** 方塊中輸入新的資料庫名稱，就無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="816fd-141">This option is not available if you typed a new database name in the **Secondary database** box.</span></span>  
  
 <span data-ttu-id="816fd-142">**複製檔案索引標籤**</span><span class="sxs-lookup"><span data-stu-id="816fd-142">**Copy Files tab**</span></span>  
 <span data-ttu-id="816fd-143">選項如下：</span><span class="sxs-lookup"><span data-stu-id="816fd-143">The options are as follows:</span></span>  
  
 <span data-ttu-id="816fd-144">**複製之檔案的目的資料夾**</span><span class="sxs-lookup"><span data-stu-id="816fd-144">**Destination folder for copied files**</span></span>  
 <span data-ttu-id="816fd-145">輸入還原至次要資料庫時，應該用來複製交易記錄備份的路徑。</span><span class="sxs-lookup"><span data-stu-id="816fd-145">Type the path to which transaction log backups should be copied for restoration to the secondary database.</span></span> <span data-ttu-id="816fd-146">通常它是次要伺服器上之資料夾的本機路徑。</span><span class="sxs-lookup"><span data-stu-id="816fd-146">This is usually a local path to a folder located on the secondary server.</span></span> <span data-ttu-id="816fd-147">不過，如果此資料夾位於另一個伺服器上，您就必須指定此資料夾的 UNC 路徑。</span><span class="sxs-lookup"><span data-stu-id="816fd-147">If the folder is located on another server, however, you must specify a UNC path to the folder.</span></span> <span data-ttu-id="816fd-148">次要伺服器執行個體的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶，必須擁有此資料夾的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="816fd-148">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account of the secondary server instance must have Read permissions on this folder.</span></span> <span data-ttu-id="816fd-149">您也必須授與此網路共用的讀取與寫入權限給 Proxy 帳戶，Proxy 帳戶才能在次要伺服器執行個體上執行複製與還原作業。</span><span class="sxs-lookup"><span data-stu-id="816fd-149">You must also grant read and write permissions on this network share to the proxy accounts under which the copy and restore jobs will run at the secondary server instances.</span></span> <span data-ttu-id="816fd-150">根據預設，這是次要伺服器執行個體的 SQL Server Agent 服務帳戶，但是系統管理員 (sysadmin) 可以為此作業選擇其他 Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="816fd-150">By default, this is the SQL Server Agent service account of the secondary server instance, but a sysadmin can choose other proxy accounts for the jobs.</span></span>  
  
 <span data-ttu-id="816fd-151">**在此時間後刪除複製的檔案**</span><span class="sxs-lookup"><span data-stu-id="816fd-151">**Delete copied files after**</span></span>  
 <span data-ttu-id="816fd-152">選擇所複製的交易記錄備份在被刪除之前，要在目的資料夾中存在多久。</span><span class="sxs-lookup"><span data-stu-id="816fd-152">Choose the length of time you want the copied transaction log backup files to remain in the destination folder before being deleted.</span></span>  
  
 <span data-ttu-id="816fd-153">**作業名稱**</span><span class="sxs-lookup"><span data-stu-id="816fd-153">**Job name**</span></span>  
 <span data-ttu-id="816fd-154">顯示用以將交易記錄備份檔案，從主要伺服器複製至次要伺服器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業名稱。</span><span class="sxs-lookup"><span data-stu-id="816fd-154">Displays the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job used to copy transaction log backup files from the primary server to the secondary server.</span></span> <span data-ttu-id="816fd-155">第一次建立此作業時，您可以在方塊中輸入新的名稱。</span><span class="sxs-lookup"><span data-stu-id="816fd-155">When first creating this job, you can change the name by typing in the box.</span></span>  
  
 <span data-ttu-id="816fd-156">**[排程]**</span><span class="sxs-lookup"><span data-stu-id="816fd-156">**Schedule**</span></span>  
 <span data-ttu-id="816fd-157">顯示用來從主要伺服器複製交易記錄備份至次要伺服器的 SQL Server Agent 複製作業的目前排程。</span><span class="sxs-lookup"><span data-stu-id="816fd-157">Displays the current schedule for the SQL Server Agent copy job to copy transaction log backups from the primary server to the secondary server.</span></span> <span data-ttu-id="816fd-158">按一下 **[排程...]** ，即可修改此排程。</span><span class="sxs-lookup"><span data-stu-id="816fd-158">You can modify this schedule by clicking **Schedule...**.</span></span>  
  
 <span data-ttu-id="816fd-159">**[排程...]**</span><span class="sxs-lookup"><span data-stu-id="816fd-159">**Schedule...**</span></span>  
 <span data-ttu-id="816fd-160">修改用來從主要伺服器複製交易記錄備份至次要伺服器的 SQL Server Agent 作業的參數。</span><span class="sxs-lookup"><span data-stu-id="816fd-160">Modify the parameters of the SQL Server Agent job that copies transaction log backups from the primary server to the secondary server.</span></span>  
  
 <span data-ttu-id="816fd-161">**停用此作業**</span><span class="sxs-lookup"><span data-stu-id="816fd-161">**Disable this job**</span></span>  
 <span data-ttu-id="816fd-162">暫停 SQL Server Agent 複製作業。</span><span class="sxs-lookup"><span data-stu-id="816fd-162">Suspend the SQL Server Agent copy job.</span></span>  
  
 <span data-ttu-id="816fd-163">**還原交易記錄索引標籤**</span><span class="sxs-lookup"><span data-stu-id="816fd-163">**Restore Transaction Log tab**</span></span>  
 <span data-ttu-id="816fd-164">選項如下：</span><span class="sxs-lookup"><span data-stu-id="816fd-164">The options are as follows:</span></span>  
  
 <span data-ttu-id="816fd-165">**還原備份時，中斷連接資料庫中的使用者**</span><span class="sxs-lookup"><span data-stu-id="816fd-165">**Disconnect users in the database when restoring backups**</span></span>  
 <span data-ttu-id="816fd-166">正在還原交易記錄備份時，自動中斷連接次要資料庫的使用者。</span><span class="sxs-lookup"><span data-stu-id="816fd-166">Automatically disconnect users from the secondary database while transaction log backups are being restored.</span></span>  
  
 <span data-ttu-id="816fd-167">**不復原模式**</span><span class="sxs-lookup"><span data-stu-id="816fd-167">**No recovery mode**</span></span>  
 <span data-ttu-id="816fd-168">讓次要資料庫維持 NORECOVERY 模式。</span><span class="sxs-lookup"><span data-stu-id="816fd-168">Leave the secondary database in NORECOVERY mode.</span></span>  
  
 <span data-ttu-id="816fd-169">**待命模式**</span><span class="sxs-lookup"><span data-stu-id="816fd-169">**Standby mode**</span></span>  
 <span data-ttu-id="816fd-170">讓次要資料庫維持 STANDBY 模式。</span><span class="sxs-lookup"><span data-stu-id="816fd-170">Leave the secondary database in STANDBY mode.</span></span> <span data-ttu-id="816fd-171">此模式僅允許針對資料庫執行唯讀作業。</span><span class="sxs-lookup"><span data-stu-id="816fd-171">This mode will allow read-only operations to be performed on the database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="816fd-172">例如，如果將現有的次要資料庫的復原模式從 [不復原模式]  變更為 [待命模式]  ，則該變更只有在下次記錄備份還原到資料庫之後才會生效。</span><span class="sxs-lookup"><span data-stu-id="816fd-172">If you change the recovery mode of an existing secondary database, for example, from **No recovery mode** to **Standby mode**, the change takes effect only after the next log backup is restored to the database.</span></span>  
  
 <span data-ttu-id="816fd-173">**延遲還原備份至少**</span><span class="sxs-lookup"><span data-stu-id="816fd-173">**Delay restoring backups at least**</span></span>  
 <span data-ttu-id="816fd-174">選擇還原交易記錄備份至次要資料庫的延遲 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="816fd-174">Choose the delay before transaction log backups are restored to the secondary database, if any.</span></span>  
  
 <span data-ttu-id="816fd-175">**如果未在此時間內進行還原，則發出警示**</span><span class="sxs-lookup"><span data-stu-id="816fd-175">**Alert if no restore occurs within**</span></span>  
 <span data-ttu-id="816fd-176">選擇在發出未發生交易記錄還原的警示之前，記錄傳送等候的時間量。</span><span class="sxs-lookup"><span data-stu-id="816fd-176">Choose the amount of time you want log shipping to wait before raising an alert that no transaction log restores have occurred.</span></span>  
  
 <span data-ttu-id="816fd-177">**作業名稱**</span><span class="sxs-lookup"><span data-stu-id="816fd-177">**Job name**</span></span>  
 <span data-ttu-id="816fd-178">顯示用來還原交易記錄備份至次要資料庫的 SQL Server Agent 作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="816fd-178">Displays the name of the SQL Server Agent job used to restore transaction log backups to the secondary database.</span></span> <span data-ttu-id="816fd-179">第一次建立此作業時，您可以在方塊中輸入新的名稱。</span><span class="sxs-lookup"><span data-stu-id="816fd-179">When first creating this job, you can change the name by typing in the box.</span></span>  
  
 <span data-ttu-id="816fd-180">**[排程]**</span><span class="sxs-lookup"><span data-stu-id="816fd-180">**Schedule**</span></span>  
 <span data-ttu-id="816fd-181">顯示用來還原交易記錄備份至次要資料庫的 SQL Server Agent 作業的目前排程。</span><span class="sxs-lookup"><span data-stu-id="816fd-181">Displays the current schedule for the SQL Server Agent job used for restoring transaction log backups to the secondary database.</span></span> <span data-ttu-id="816fd-182">按一下 **[排程...]** ，即可修改此選項。</span><span class="sxs-lookup"><span data-stu-id="816fd-182">You can modify this option by clicking **Schedule...**.</span></span>  
  
 <span data-ttu-id="816fd-183">**[排程...]**</span><span class="sxs-lookup"><span data-stu-id="816fd-183">**Schedule...**</span></span>  
 <span data-ttu-id="816fd-184">修改與 SQL Server Agent 還原作業相關的參數。</span><span class="sxs-lookup"><span data-stu-id="816fd-184">Modify the parameters associate with the SQL Server Agent restore job.</span></span>  
  
 <span data-ttu-id="816fd-185">**停用此作業**</span><span class="sxs-lookup"><span data-stu-id="816fd-185">**Disable this job**</span></span>  
 <span data-ttu-id="816fd-186">暫停次要資料庫的還原作業。</span><span class="sxs-lookup"><span data-stu-id="816fd-186">Suspend restore operations to the secondary database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="816fd-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="816fd-187">See Also</span></span>  
 <span data-ttu-id="816fd-188">[SQL Server 資料庫的備份與還原](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="816fd-188">[Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 [<span data-ttu-id="816fd-189">關於記錄傳送 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="816fd-189">About Log Shipping &#40;SQL Server&#41;</span></span>](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
