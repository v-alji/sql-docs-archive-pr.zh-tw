---
title: 將報表伺服器資料庫移至其他電腦 (SSRS 原生模式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 44a9854d-e333-44f6-bdc7-8837b9f34416
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 49fd35f57cf783b262b3c690e3047e5f479ab193
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686763"
---
# <a name="moving-the-report-server-databases-to-another-computer-ssrs-native-mode"></a><span data-ttu-id="65d1a-102">將報表伺服器資料庫移至其他電腦 (SSRS 原生模式)</span><span class="sxs-lookup"><span data-stu-id="65d1a-102">Moving the Report Server Databases to Another Computer (SSRS Native Mode)</span></span>
  <span data-ttu-id="65d1a-103">您可以將安裝中所使用的報表伺服器資料庫，移 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 至不同電腦上的實例。</span><span class="sxs-lookup"><span data-stu-id="65d1a-103">You can move the report server databases that are used in an installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] to an instance that is on a different computer.</span></span> <span data-ttu-id="65d1a-104">但是，您必須一起移動或複製 reportserver 和 reportservertempdb 資料庫。</span><span class="sxs-lookup"><span data-stu-id="65d1a-104">Both the reportserver and reportservertempdb databases must be moved or copied together.</span></span> <span data-ttu-id="65d1a-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝需要這兩個資料庫。reportservertempdb 資料庫的名稱必須與所移動的主要 reportserver 資料庫相關。</span><span class="sxs-lookup"><span data-stu-id="65d1a-105">A [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation requires both databases; the reportservertempdb database must be related by name to the primary reportserver database you are moving.</span></span>  
  
 <span data-ttu-id="65d1a-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]原生模式。</span><span class="sxs-lookup"><span data-stu-id="65d1a-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="65d1a-107">移動資料庫不會影響目前已針對報表伺服器項目所定義的排程作業。</span><span class="sxs-lookup"><span data-stu-id="65d1a-107">Moving a database does not effect scheduled operations that are currently defined for report server items.</span></span>  
  
-   <span data-ttu-id="65d1a-108">當您第一次重新啟動報表伺服器服務時，便會重新建立排程。</span><span class="sxs-lookup"><span data-stu-id="65d1a-108">Schedules will be recreated the first time that you restart the Report Server service.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="65d1a-109">Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="65d1a-109">Agent jobs that are used to trigger a schedule will be recreated on the new database instance.</span></span> <span data-ttu-id="65d1a-110">雖然您不需要將這些作業移至新的電腦，但是可能會想要刪除電腦上不再使用的作業。</span><span class="sxs-lookup"><span data-stu-id="65d1a-110">You do not have to move the jobs to the new computer, but you might want to delete jobs on the computer that will no longer be used.</span></span>  
  
-   <span data-ttu-id="65d1a-111">移動的資料庫會保留訂閱、快取報表以及快照集。</span><span class="sxs-lookup"><span data-stu-id="65d1a-111">Subscriptions, cached reports, and snapshots are preserved in the moved database.</span></span> <span data-ttu-id="65d1a-112">如果快照集並未在移動資料庫之後收取重新整理過的資料，請在報表管理員中清除快照集選項，然後按一下 [套用]\*\*\*\* 儲存變更、重新建立排程，再按一下 [套用]\*\*\*\* 儲存變更。</span><span class="sxs-lookup"><span data-stu-id="65d1a-112">If a snapshot is not picking up refreshed data after the database is moved, clear the snapshot options in Report Manager, click **Apply** to save your changes, re-create the schedule, and click **Apply** again to save your changes.</span></span>  
  
-   <span data-ttu-id="65d1a-113">當您移動 reportservertempdb 資料庫時，系統會保留儲存在該資料庫中的暫存報表和使用者工作階段。</span><span class="sxs-lookup"><span data-stu-id="65d1a-113">Temporary report and user session data that is stored in reportservertempdb are persisted when you move that database.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="65d1a-114">提供數種移動資料庫的方法，包括備份與還原、附加與卸離，以及複製。</span><span class="sxs-lookup"><span data-stu-id="65d1a-114">provides several approaches for moving databases, including backup and restore, attach and detach, and copy.</span></span> <span data-ttu-id="65d1a-115">並不是所有方法都適合用來將現有資料庫重新放置到新的伺服器執行個體上，</span><span class="sxs-lookup"><span data-stu-id="65d1a-115">Not all approaches are appropriate for relocating an existing database to a new server instance.</span></span> <span data-ttu-id="65d1a-116">移動報表伺服器資料庫的最佳方法會因您的系統可用性需求而有所差異。</span><span class="sxs-lookup"><span data-stu-id="65d1a-116">The approach that you should use to move the report server database will vary depending on your system availability requirements.</span></span> <span data-ttu-id="65d1a-117">移動報表伺服器資料庫最簡單的方式就是附加與卸離，</span><span class="sxs-lookup"><span data-stu-id="65d1a-117">The easiest way to move the report server databases is to attach and detach them.</span></span> <span data-ttu-id="65d1a-118">但是，如果要採用這種方法，您必須在卸離資料庫時將報表伺服器設定為離線狀態。</span><span class="sxs-lookup"><span data-stu-id="65d1a-118">However, this approach requires that you take the report server offline while you detach the database.</span></span> <span data-ttu-id="65d1a-119">如果您希望能將服務中斷的情況降到最少，備份與還原就是比較好的選擇，但是您必須執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令來執行這些作業。</span><span class="sxs-lookup"><span data-stu-id="65d1a-119">Backup and restore is a better choice if you want to minimize service disruptions, but you must run [!INCLUDE[tsql](../../includes/tsql-md.md)] commands to perform the operations.</span></span> <span data-ttu-id="65d1a-120">我們不建議利用複製資料庫來移動報表伺服器 (特別是使用「複製資料庫精靈」)，因為複製資料庫不會保留資料庫中的權限設定。</span><span class="sxs-lookup"><span data-stu-id="65d1a-120">Copying the database is not recommended (specifically, by using the Copy Database Wizard); it does not preserve permission settings in the database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="65d1a-121">如果您對現有安裝所做的唯一變更是重新放置報表伺服器資料庫，就適用本主題中所提供的這些步驟。</span><span class="sxs-lookup"><span data-stu-id="65d1a-121">The steps provided in this topic are recommended when relocating the report server database is the only change you are making to the existing installation.</span></span> <span data-ttu-id="65d1a-122">移轉整個 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝 (亦即，移動資料庫，並變更使用資料庫之報表伺服器 Windows 服務的識別) 需要重新設定連接和重設加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="65d1a-122">Migrating an entire [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation (that is, moving the database and changing the identity of the Report Server Windows service that uses the database) requires connection reconfiguration and an encryption key reset.</span></span>  
  
## <a name="detaching-and-attaching-the-report-server-databases"></a><span data-ttu-id="65d1a-123">卸離及附加報表伺服器資料庫</span><span class="sxs-lookup"><span data-stu-id="65d1a-123">Detaching and Attaching the Report Server Databases</span></span>  
 <span data-ttu-id="65d1a-124">如果您可以將報表伺服器設定為離線狀態，就可以卸離資料庫，並將資料庫移動到您要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="65d1a-124">If you can take the report server offline, you can detach the databases to move them to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you want to use.</span></span> <span data-ttu-id="65d1a-125">這種方式可以保留資料庫中的權限。</span><span class="sxs-lookup"><span data-stu-id="65d1a-125">This approach preserves permissions in the databases.</span></span> <span data-ttu-id="65d1a-126">如果您要使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 資料庫，就必須將它移至另一個 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="65d1a-126">If you are using a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] database, you must move it to another [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] instance.</span></span> <span data-ttu-id="65d1a-127">移動資料庫之後，您必須重新設定報表伺服器與報表伺服器資料庫間的連接。</span><span class="sxs-lookup"><span data-stu-id="65d1a-127">After you move the databases, you must reconfigure the report server connection to the report server database.</span></span> <span data-ttu-id="65d1a-128">如果執行的是向外延伸部署，您必須重新設定部署中每個報表伺服器的報表伺服器資料庫連接。</span><span class="sxs-lookup"><span data-stu-id="65d1a-128">If you are running a scale-out deployment, you must reconfigure the report server database connection for each report server in the deployment.</span></span>  
  
 <span data-ttu-id="65d1a-129">請使用下列步驟來移動資料庫：</span><span class="sxs-lookup"><span data-stu-id="65d1a-129">Use the following steps to move the databases:</span></span>  
  
1.  <span data-ttu-id="65d1a-130">備份您想要移動之報表伺服器資料庫的加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="65d1a-130">Backup the encryption keys for the report server database you want to move.</span></span> <span data-ttu-id="65d1a-131">您可以使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具來備份這些金鑰。</span><span class="sxs-lookup"><span data-stu-id="65d1a-131">You can use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool backup the keys.</span></span>  
  
2.  <span data-ttu-id="65d1a-132">停止報表伺服器服務。</span><span class="sxs-lookup"><span data-stu-id="65d1a-132">Stop the Report Server service.</span></span> <span data-ttu-id="65d1a-133">您可以使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具來停止這項服務。</span><span class="sxs-lookup"><span data-stu-id="65d1a-133">You can use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to stop the service.</span></span>  
  
3.  <span data-ttu-id="65d1a-134">啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 並開啟 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 主控報表伺服器資料庫之實例的連接。</span><span class="sxs-lookup"><span data-stu-id="65d1a-134">Start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and open a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that hosts the report server databases.</span></span>  
  
4.  <span data-ttu-id="65d1a-135">以滑鼠右鍵按一下報表伺服器資料庫，指向 [工作]，並按一下 [卸離]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65d1a-135">Right-click the report server database, point to Tasks, and click **Detach**.</span></span> <span data-ttu-id="65d1a-136">針對報表伺服器暫存資料庫重複此步驟。</span><span class="sxs-lookup"><span data-stu-id="65d1a-136">Repeat this step for the report server temporary database.</span></span>  
  
5.  <span data-ttu-id="65d1a-137">複製或移動 .mdf 和 .ldf 檔案到您要使用之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的 Data 資料夾。</span><span class="sxs-lookup"><span data-stu-id="65d1a-137">Copy or move the .mdf and .ldf files to the Data folder of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you want to use.</span></span> <span data-ttu-id="65d1a-138">因為移動的資料庫共有兩個，因此請確定您總共移動或複製四個檔案。</span><span class="sxs-lookup"><span data-stu-id="65d1a-138">Because you are moving two databases, make sure that you move or copy all four files.</span></span>  
  
6.  <span data-ttu-id="65d1a-139">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中，開啟即將主控報表伺服器資料庫之新 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的連接。</span><span class="sxs-lookup"><span data-stu-id="65d1a-139">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], open a connection to the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that will host the report server databases.</span></span>  
  
7.  <span data-ttu-id="65d1a-140">以滑鼠右鍵按一下 [資料庫] 節點，然後按一下 [附加]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65d1a-140">Right-click the Databases node, and then click **Attach**.</span></span>  
  
8.  <span data-ttu-id="65d1a-141">按一下 **[加入]** ，選取您要附加之報表伺服器資料庫的 .mdf 和 .ldf 檔案。</span><span class="sxs-lookup"><span data-stu-id="65d1a-141">Click **Add** to select the report server database .mdf and .ldf files that you want to attach.</span></span> <span data-ttu-id="65d1a-142">針對報表伺服器暫存資料庫重複此步驟。</span><span class="sxs-lookup"><span data-stu-id="65d1a-142">Repeat this step for the report server temporary database.</span></span>  
  
9. <span data-ttu-id="65d1a-143">附加資料庫之後，請確認 `RSExecRole` 是報表伺服器資料庫和暫存資料庫中的資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="65d1a-143">After the databases are attached, verify that the `RSExecRole` is a database role in the report server database and temporary database.</span></span> <span data-ttu-id="65d1a-144">`RSExecRole`必須具有報表伺服器資料庫資料表的 select、insert、update、delete 和 reference 許可權，以及預存程式的 execute 許可權。</span><span class="sxs-lookup"><span data-stu-id="65d1a-144">`RSExecRole` must have select, insert, update, delete, and reference permissions on the report server database tables, and execute permissions on the stored procedures.</span></span> <span data-ttu-id="65d1a-145">如需詳細資訊，請參閱 [建立 RSExecRole](../security/create-the-rsexecrole.md)。</span><span class="sxs-lookup"><span data-stu-id="65d1a-145">For more information, see [Create the RSExecRole](../security/create-the-rsexecrole.md).</span></span>  
  
10. <span data-ttu-id="65d1a-146">啟動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具，並開啟報表伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="65d1a-146">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and open a connection to the report server.</span></span>  
  
11. <span data-ttu-id="65d1a-147">在 [資料庫] 頁面上，選取新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，然後按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="65d1a-147">On the Database page, select the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, and then click **Connect**.</span></span>  
  
12. <span data-ttu-id="65d1a-148">選取您剛才移動的報表伺服器資料庫，然後按一下 **[套用]**。</span><span class="sxs-lookup"><span data-stu-id="65d1a-148">Select the report server database that you just moved, and then click **Apply**.</span></span>  
  
13. <span data-ttu-id="65d1a-149">在 [加密金鑰] 頁面上，按一下 [還原]。</span><span class="sxs-lookup"><span data-stu-id="65d1a-149">On the Encryption Keys page, click Restore.</span></span> <span data-ttu-id="65d1a-150">指定包含金鑰備份副本的檔案以及解除鎖定此檔案的密碼。</span><span class="sxs-lookup"><span data-stu-id="65d1a-150">Specify the file that contains the backup copy of the keys and the password to unlock the file.</span></span>  
  
14. <span data-ttu-id="65d1a-151">重新啟動報表伺服器服務。</span><span class="sxs-lookup"><span data-stu-id="65d1a-151">Restart the Report Server service.</span></span>  
  
## <a name="backing-up-and-restoring-the-report-server-databases"></a><span data-ttu-id="65d1a-152">備份及還原報表伺服器資料庫</span><span class="sxs-lookup"><span data-stu-id="65d1a-152">Backing Up and Restoring the Report Server Databases</span></span>  
 <span data-ttu-id="65d1a-153">如果無法將報表伺服器設定為離線狀態，您可以使用備份和還原來重新放置報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="65d1a-153">If you cannot take the report server offline, you can use backup and restore to relocate the report server databases.</span></span> <span data-ttu-id="65d1a-154">您必須使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式來進行備份和還原。</span><span class="sxs-lookup"><span data-stu-id="65d1a-154">You must use [!INCLUDE[tsql](../../includes/tsql-md.md)] statements to do the backup and restore.</span></span> <span data-ttu-id="65d1a-155">還原資料庫之後，您必須將報表伺服器設定為使用新伺服器執行個體上的資料庫。</span><span class="sxs-lookup"><span data-stu-id="65d1a-155">After you restore the databases, you must configure the report server to use the database on the new server instance.</span></span> <span data-ttu-id="65d1a-156">如需詳細資訊，請參閱此主題結尾的指示。</span><span class="sxs-lookup"><span data-stu-id="65d1a-156">For more information, see the instructions at the end of this topic.</span></span>  
  
### <a name="using-backup-and-copy_only-to-backup-the-report-server-databases"></a><span data-ttu-id="65d1a-157">使用 BACKUP 和 COPY_ONLY 備份報表伺服器資料庫</span><span class="sxs-lookup"><span data-stu-id="65d1a-157">Using BACKUP and COPY_ONLY to Backup the Report Server Databases</span></span>  
 <span data-ttu-id="65d1a-158">備份資料庫時，請設定 COPY_ONLY 引數。</span><span class="sxs-lookup"><span data-stu-id="65d1a-158">When backing up the databases, set the COPY_ONLY argument.</span></span> <span data-ttu-id="65d1a-159">請務必同時備份資料庫以及記錄檔。</span><span class="sxs-lookup"><span data-stu-id="65d1a-159">Be sure to back up both of the databases and log files.</span></span>  
  
```  
-- To permit log backups, before the full database backup, alter the database   
-- to use the full recovery model.  
USE master;  
GO  
ALTER DATABASE ReportServer  
   SET RECOVERY FULL  
  
-- If the ReportServerData device does not exist yet, create it.   
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerData',   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\BACKUP\ReportServerData.bak'  
  
-- Create a logical backup device, ReportServerLog.  
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerLog',   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\BACKUP\ReportServerLog.bak'  
  
-- Back up the full ReportServer database.  
BACKUP DATABASE ReportServer  
   TO ReportServerData  
   WITH COPY_ONLY  
  
-- Back up the ReportServer log.  
BACKUP LOG ReportServer  
   TO ReportServerLog  
   WITH COPY_ONLY  
  
-- To permit log backups, before the full database backup, alter the database   
-- to use the full recovery model.  
USE master;  
GO  
ALTER DATABASE ReportServerTempdb  
   SET RECOVERY FULL  
  
-- If the ReportServerTempDBData device does not exist yet, create it.   
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerTempDBData',   
'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\BACKUP\ReportServerTempDBData.bak'  
  
-- Create a logical backup device, ReportServerTempDBLog.  
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerTempDBLog',   
'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\BACKUP\ReportServerTempDBLog.bak'  
  
-- Back up the full ReportServerTempDB database.  
BACKUP DATABASE ReportServerTempDB  
   TO ReportServerTempDBData  
   WITH COPY_ONLY  
  
-- Back up the ReportServerTempDB log.  
BACKUP LOG ReportServerTempDB  
   TO ReportServerTempDBLog  
   WITH COPY_ONLY  
```  
  
### <a name="using-restore-and-move-to-relocate-the-report-server-databases"></a><span data-ttu-id="65d1a-160">使用 RESTORE 和 MOVE 重新放置報表伺服器資料庫</span><span class="sxs-lookup"><span data-stu-id="65d1a-160">Using RESTORE and MOVE to Relocate the Report Server Databases</span></span>  
 <span data-ttu-id="65d1a-161">還原資料庫時，請務必包含 MOVE 引數，如此才能指定路徑。</span><span class="sxs-lookup"><span data-stu-id="65d1a-161">When restoring the databases, be sure to include the MOVE argument so that you can specify a path.</span></span> <span data-ttu-id="65d1a-162">使用 NORECOVERY 引數來執行初始還原；這樣子資料庫可以保持在還原狀態，讓您有時間可以預覽記錄備份，判斷要還原哪一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="65d1a-162">Use the NORECOVERY argument to perform the initial restore; this keeps the database in a RESTORING state, giving you time to review log backups to determine which one to restore.</span></span> <span data-ttu-id="65d1a-163">最後一個步驟會使用 RECOVERY 引數重複執行 RESTORE 作業。</span><span class="sxs-lookup"><span data-stu-id="65d1a-163">The final step repeats the RESTORE operation with the RECOVERY argument.</span></span>  
  
 <span data-ttu-id="65d1a-164">MOVE 引數會使用資料檔案的邏輯名稱。</span><span class="sxs-lookup"><span data-stu-id="65d1a-164">The MOVE argument uses the logical name of the data file.</span></span> <span data-ttu-id="65d1a-165">若要找出該邏輯名稱，請執行下列陳述式： `RESTORE FILELISTONLY FROM DISK='C:\ReportServerData.bak';`</span><span class="sxs-lookup"><span data-stu-id="65d1a-165">To find the logical name, execute the following statement: `RESTORE FILELISTONLY FROM DISK='C:\ReportServerData.bak';`</span></span>  
  
 <span data-ttu-id="65d1a-166">下列範例中包含 FILE 引數，因此您可以指定要還原之記錄檔的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="65d1a-166">The following examples include the FILE argument so that you can specify the file position of the log file to restore.</span></span> <span data-ttu-id="65d1a-167">若要找出該檔案的位置，請執行下列陳述式： `RESTORE HEADERONLY FROM DISK='C:\ReportServerData.bak';`</span><span class="sxs-lookup"><span data-stu-id="65d1a-167">To find the file position, execute the following statement: `RESTORE HEADERONLY FROM DISK='C:\ReportServerData.bak';`</span></span>  
  
 <span data-ttu-id="65d1a-168">還原資料庫和記錄檔時，您應該個別執行每個 RESTORE 作業。</span><span class="sxs-lookup"><span data-stu-id="65d1a-168">When restoring the database and log files, you should run each RESTORE operation separately.</span></span>  
  
```  
-- Restore the report server database and move to new instance folder   
RESTORE DATABASE ReportServer  
   FROM DISK='C:\ReportServerData.bak'  
   WITH NORECOVERY,   
      MOVE 'ReportServer' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer.mdf',   
      MOVE 'ReportServer_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer_Log.ldf';  
GO  
  
-- Restore the report server log file to new instance folder   
RESTORE LOG ReportServer  
   FROM DISK='C:\ReportServerData.bak'  
   WITH NORECOVERY, FILE=2  
      MOVE 'ReportServer' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer.mdf',   
      MOVE 'ReportServer_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer_Log.ldf';  
GO  
  
-- Restore and move the report server temporary database  
RESTORE DATABASE ReportServerTempdb  
   FROM DISK='C:\ReportServerTempDBData.bak'  
   WITH NORECOVERY,   
      MOVE 'ReportServerTempDB' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServerTempDB.mdf',   
      MOVE 'ReportServerTempDB_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\REportServerTempDB_Log.ldf';  
GO  
  
-- Restore the temporary database log file to new instance folder   
RESTORE LOG ReportServerTempdb  
   FROM DISK='C:\ReportServerTempDBData.bak'  
   WITH NORECOVERY, FILE=2  
      MOVE 'ReportServerTempDB' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServerTempDB.mdf',   
      MOVE 'ReportServerTempDB_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\REportServerTempDB_Log.ldf';  
GO  
  
-- Perform final restore  
RESTORE DATABASE ReportServer  
   WITH RECOVERY  
GO  
  
-- Perform final restore  
RESTORE DATABASE ReportServerTempDB  
   WITH RECOVERY  
GO  
```  
  
### <a name="how-to-configure-the-report-server-database-connection"></a><span data-ttu-id="65d1a-169">如何設定報表伺服器資料庫連接</span><span class="sxs-lookup"><span data-stu-id="65d1a-169">How to Configure the Report Server Database Connection</span></span>  
  
1.  <span data-ttu-id="65d1a-170">啟動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員，並開啟報表伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="65d1a-170">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and open a connection to the report server.</span></span>  
  
2.  <span data-ttu-id="65d1a-171">在 [資料庫] 頁面上，按一下 **[變更資料庫]**。</span><span class="sxs-lookup"><span data-stu-id="65d1a-171">On the Database page, click **Change Database**.</span></span> <span data-ttu-id="65d1a-172">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="65d1a-172">Click **Next**.</span></span>  
  
3.  <span data-ttu-id="65d1a-173">按一下 **[選擇現有報表伺服器資料庫]**。</span><span class="sxs-lookup"><span data-stu-id="65d1a-173">Click **Choose an existing report server database**.</span></span> <span data-ttu-id="65d1a-174">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="65d1a-174">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="65d1a-175">選取現在主控報表伺服器資料庫的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，然後按一下 **[測試連接]**。</span><span class="sxs-lookup"><span data-stu-id="65d1a-175">Select the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that now hosts the report server database and click **Test Connection**.</span></span> <span data-ttu-id="65d1a-176">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="65d1a-176">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="65d1a-177">在 [資料庫名稱] 中，選取您想要使用的報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="65d1a-177">In Database Name, select the report server database that you want to use.</span></span> <span data-ttu-id="65d1a-178">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="65d1a-178">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="65d1a-179">在 [認證] 中，指定報表伺服器將用來連接至報表伺服器資料庫的認證。</span><span class="sxs-lookup"><span data-stu-id="65d1a-179">In Credentials, specify the credentials that the report server will use to connect to the report server database.</span></span> <span data-ttu-id="65d1a-180">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="65d1a-180">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="65d1a-181">按 **[下一步]** ，然後按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="65d1a-181">Click **Next** and then **Finish**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="65d1a-182">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝會要求 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體必須包含 `RSExecRole` 角色。</span><span class="sxs-lookup"><span data-stu-id="65d1a-182">A [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation requires that the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] instance include the `RSExecRole` role.</span></span> <span data-ttu-id="65d1a-183">當您透過 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具設定報表伺服器資料庫連接時，會產生角色建立、登入註冊以及角色指派等動作。</span><span class="sxs-lookup"><span data-stu-id="65d1a-183">Role creation, login registration, and role assignments occur when you set the report server database connection through the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span> <span data-ttu-id="65d1a-184">如果您使用其他方法 (尤其是使用 rsconfig.exe 命令提示字元公用程式) 來設定連接，報表伺服器將不會處於工作狀態。</span><span class="sxs-lookup"><span data-stu-id="65d1a-184">If you use alternate approaches (specifically, if you use the rsconfig.exe command prompt utility) to configure the connection, the report server will not be in a working state.</span></span> <span data-ttu-id="65d1a-185">您可能必須撰寫 WMI 程式碼，才能讓報表伺服器可供使用。</span><span class="sxs-lookup"><span data-stu-id="65d1a-185">You might have to write WMI code to make the report server available.</span></span> <span data-ttu-id="65d1a-186">如需詳細資訊，請參閱 [存取 Reporting Services WMI 提供者](../tools/access-the-reporting-services-wmi-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="65d1a-186">For more information, see [Access the Reporting Services WMI Provider](../tools/access-the-reporting-services-wmi-provider.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d1a-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65d1a-187">See Also</span></span>  
 <span data-ttu-id="65d1a-188">[建立 RSExecRole](../security/create-the-rsexecrole.md) </span><span class="sxs-lookup"><span data-stu-id="65d1a-188">[Create the RSExecRole](../security/create-the-rsexecrole.md) </span></span>  
 <span data-ttu-id="65d1a-189">[啟動與停止 Report Server 服務](start-and-stop-the-report-server-service.md) </span><span class="sxs-lookup"><span data-stu-id="65d1a-189">[Start and Stop the Report Server Service](start-and-stop-the-report-server-service.md) </span></span>  
 <span data-ttu-id="65d1a-190">[&#40;SSRS Configuration Manager 設定報表伺服器資料庫連接&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="65d1a-190">[Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="65d1a-191">[&#40;SSRS Configuration Manager 設定自動執行帳戶&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="65d1a-191">[Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="65d1a-192">[Reporting Services 組態管理員 &#40;原生模式&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="65d1a-192">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 <span data-ttu-id="65d1a-193">[&#40;SSRS&#41;的 rsconfig 公用程式](../tools/rsconfig-utility-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="65d1a-193">[rsconfig Utility &#40;SSRS&#41;](../tools/rsconfig-utility-ssrs.md) </span></span>  
 <span data-ttu-id="65d1a-194">[設定和管理 &#40;SSRS Configuration Manager 的加密金鑰&#41;](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="65d1a-194">[Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md) </span></span>  
 [<span data-ttu-id="65d1a-195">報表伺服器資料庫 &#40;SSRS 原生模式&#41;</span><span class="sxs-lookup"><span data-stu-id="65d1a-195">Report Server Database &#40;SSRS Native Mode&#41;</span></span>](report-server-database-ssrs-native-mode.md)  
  
  
